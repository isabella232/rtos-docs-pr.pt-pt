---
title: Capítulo 3 - Descrição dos Serviços de Clientes Azure RTOS NetX DNS
description: Este capítulo contém uma descrição de todos os serviços DNS Azure RTOS NetX (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 18e059e79f9742eaaafffbf15b55b4b5063363f8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826750"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dns-client-services"></a><span data-ttu-id="c168e-103">Capítulo 3 - Descrição dos Serviços de Clientes Azure RTOS NetX DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-103">Chapter 3 - Description of Azure RTOS NetX DNS Client Services</span></span>

<span data-ttu-id="c168e-104">Este capítulo contém uma descrição de todos os serviços DNS Azure RTOS NetX (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="c168e-104">This chapter contains a description of all Azure RTOS NetX DNS services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="c168e-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="c168e-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="c168e-106">**nx_dns_authority_zone_start_get**: *Procure o início de uma zona de autoridade associada ao nome de hospedeiro especificado*</span><span class="sxs-lookup"><span data-stu-id="c168e-106">**nx_dns_authority_zone_start_get**: *Look up the start of a zone of authority associated with the specified host name*</span></span>
- <span data-ttu-id="c168e-107">**nx_dns_cache_initialize**: *Inicialize uma Cache DNS.*</span><span class="sxs-lookup"><span data-stu-id="c168e-107">**nx_dns_cache_initialize**: *Initialize a DNS Cache.*</span></span>
- <span data-ttu-id="c168e-108">**nx_dns_cache_notify_clear:** *Limpe a função de notificação completa da cache.*</span><span class="sxs-lookup"><span data-stu-id="c168e-108">**nx_dns_cache_notify_clear**: *Clear the cache full notify function.*</span></span>
- <span data-ttu-id="c168e-109">**nx_dns_cache_notify_set:** *Desa estale a função de notificação completa da cache.*</span><span class="sxs-lookup"><span data-stu-id="c168e-109">**nx_dns_cache_notify_set**: *Set the cache full notify function.*</span></span>
- <span data-ttu-id="c168e-110">**nx_dns_cname_get**: *Procure o nome de domínio canónico para o pseudónimo do nome de domínio de entrada*</span><span class="sxs-lookup"><span data-stu-id="c168e-110">**nx_dns_cname_get**: *Look up the canonical domain name for the input domain name alias*</span></span>
- <span data-ttu-id="c168e-111">**nx_dns_create**: *Criar uma instância do cliente DNS*</span><span class="sxs-lookup"><span data-stu-id="c168e-111">**nx_dns_create**: *Create a DNS Client instance*</span></span>
- <span data-ttu-id="c168e-112">**nx_dns_delete**: *Excluir uma instância do cliente DNS*</span><span class="sxs-lookup"><span data-stu-id="c168e-112">**nx_dns_delete**: *Delete a DNS Client instance*</span></span>
- <span data-ttu-id="c168e-113">**nx_dns_domain_name_server_get**: *Procure os servidores de nome autorizados para a zona de domínio de entrada*</span><span class="sxs-lookup"><span data-stu-id="c168e-113">**nx_dns_domain_name_server_get**: *Look up the authoritative name servers for the input domain zone*</span></span>
- <span data-ttu-id="c168e-114">**nx_dns_domain_mail_exchange_get**: *Procure a troca de correio associada ao nome de anfitrião especificado.*</span><span class="sxs-lookup"><span data-stu-id="c168e-114">**nx_dns_domain_mail_exchange_get**: *Look up the mail exchange associated the specified host name.*</span></span>
- <span data-ttu-id="c168e-115">**nx_dns_domain_service_get**: *Procure os serviços associados ao nome de anfitrião especificado*</span><span class="sxs-lookup"><span data-stu-id="c168e-115">**nx_dns_domain_service_get**: *Look up the service(s) associated with the specified host name*</span></span>
- <span data-ttu-id="c168e-116">**nx_dns_get_serverlist_size**: *Devolva o tamanho da lista de servidores do Cliente DNS*</span><span class="sxs-lookup"><span data-stu-id="c168e-116">**nx_dns_get_serverlist_size**: *Return the size of the DNS Client server list*</span></span>
- <span data-ttu-id="c168e-117">**nx_dns_info_by_name_get**: *Endereço IP de devolução, consulta portuária no nome do anfitrião de entrada*</span><span class="sxs-lookup"><span data-stu-id="c168e-117">**nx_dns_info_by_name_get**: *Return IP address, port querying on input host name*</span></span>
- <span data-ttu-id="c168e-118">**nx_dns_ipv4_address_by_name_get**: *Procure o endereço IPv4 a partir do nome de anfitrião especificado*</span><span class="sxs-lookup"><span data-stu-id="c168e-118">**nx_dns_ipv4_address_by_name_get**: *Look up the IPv4 address from the specified host name*</span></span>
- <span data-ttu-id="c168e-119">**nx_dns_host_by_address_get**: *Procure um nome de anfitrião a partir de um endereço IP especificado*</span><span class="sxs-lookup"><span data-stu-id="c168e-119">**nx_dns_host_by_address_get**: *Look up a host name from a specified IP address*</span></span>
- <span data-ttu-id="c168e-120">**nx_dns_host_by_name_get**: *Procure o endereço IPv4 a partir do nome de anfitrião especificado*</span><span class="sxs-lookup"><span data-stu-id="c168e-120">**nx_dns_host_by_name_get**: *Look up the IPv4 address from the specified host name*</span></span>
- <span data-ttu-id="c168e-121">**nx_dns_host_text_get**: *Procure os dados de texto para o nome do domínio de entrada*</span><span class="sxs-lookup"><span data-stu-id="c168e-121">**nx_dns_host_text_get**: *Look up the text data for the input domain name*</span></span>
- <span data-ttu-id="c168e-122">**nx_dns_packet_pool_set**: *Definir a piscina de pacotes do cliente DNS*</span><span class="sxs-lookup"><span data-stu-id="c168e-122">**nx_dns_packet_pool_set**: *Set the DNS Client packet pool*</span></span>
- <span data-ttu-id="c168e-123">**nx_dns_server_add**: *Adicione um Servidor DNS no endereço especificado na lista de clientes*</span><span class="sxs-lookup"><span data-stu-id="c168e-123">**nx_dns_server_add**: *Add a DNS Server at the specified address to the Client list*</span></span>
- <span data-ttu-id="c168e-124">**nx_dns_server_get**: *Devolva o Servidor DNS na lista de clientes*</span><span class="sxs-lookup"><span data-stu-id="c168e-124">**nx_dns_server_get**: *Return the DNS Server in the Client list*</span></span>
- <span data-ttu-id="c168e-125">**nx_dns_server_remove**: *Remova um Servidor DNS da lista de clientes*</span><span class="sxs-lookup"><span data-stu-id="c168e-125">**nx_dns_server_remove**: *Remove a DNS Server from the Client list*</span></span>
- <span data-ttu-id="c168e-126">**nx_dns_server_remove_all**: *Remova todos os Servidores DNS da lista de clientes*</span><span class="sxs-lookup"><span data-stu-id="c168e-126">**nx_dns_server_remove_all**: *Remove all DNS Servers from the Client list*</span></span>

## <a name="nx_dns_authority_zone_start_get"></a><span data-ttu-id="c168e-127">nx_dns_authority_zone_start_get</span><span class="sxs-lookup"><span data-stu-id="c168e-127">nx_dns_authority_zone_start_get</span></span>

<span data-ttu-id="c168e-128">Procure o início da zona de autoridade para o anfitrião de entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-128">Look up the start of the zone of authority for the input host</span></span>

### <a name="prototype"></a><span data-ttu-id="c168e-129">Prototype</span><span class="sxs-lookup"><span data-stu-id="c168e-129">Prototype</span></span>

```c
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);

```

### <a name="description"></a><span data-ttu-id="c168e-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="c168e-130">Description</span></span>

<span data-ttu-id="c168e-131">Se NX_DNS_ENABLE_EXTENDED_RR_TYPES for definido, este serviço envia uma consulta do tipo SOA com o nome de domínio especificado para obter o início da zona de autoridade para o nome de domínio de entrada.</span><span class="sxs-lookup"><span data-stu-id="c168e-131">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SOA with the specified domain name to obtain the start of the zone of authority for the input domain name.</span></span> <span data-ttu-id="c168e-132">O Cliente DNS copia os registos SOA devolvidos na resposta do DNS Server para o local de memória *record_buffer.*</span><span class="sxs-lookup"><span data-stu-id="c168e-132">The DNS Client copies the SOA record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 
>[!NOTE]
> <span data-ttu-id="c168e-133">O *record_buffer* deve estar alinhado em 4 bytes para receber os dados.</span><span class="sxs-lookup"><span data-stu-id="c168e-133">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="c168e-134">No NetX DNS Client, o tipo de registo SOA, NX_DNS_SOA_ENTRY, é guardado como sete parâmetros de byte 4, totalizando 28 bytes:</span><span class="sxs-lookup"><span data-stu-id="c168e-134">In NetX DNS Client, the SOA record type, NX_DNS_SOA_ENTRY, is saved as seven 4 byte parameters, totaling 28 bytes:</span></span>

- <span data-ttu-id="c168e-135">**nx_dns_soa_host_mname_ptr**: Ponteiro para a principal fonte de dados para esta zona</span><span class="sxs-lookup"><span data-stu-id="c168e-135">**nx_dns_soa_host_mname_ptr**: Pointer to primary source of data for this zone</span></span>
- <span data-ttu-id="c168e-136">**nx_dns_soa_host_rname_ptr**: Ponteiro para caixa de correio responsável por esta zona</span><span class="sxs-lookup"><span data-stu-id="c168e-136">**nx_dns_soa_host_rname_ptr**: Pointer to mailbox responsible for this zone</span></span>
- <span data-ttu-id="c168e-137">**nx_dns_soa_serial**: Número da versão da zona</span><span class="sxs-lookup"><span data-stu-id="c168e-137">**nx_dns_soa_serial**: Zone version number</span></span>
- <span data-ttu-id="c168e-138">**nx_dns_soa_refresh**: Intervalo de atualização</span><span class="sxs-lookup"><span data-stu-id="c168e-138">**nx_dns_soa_refresh**: Refresh interval</span></span>
- <span data-ttu-id="c168e-139">**nx_dns_soa_retry**: Intervalo entre as retrírias da consulta SOA</span><span class="sxs-lookup"><span data-stu-id="c168e-139">**nx_dns_soa_retry**: Interval between SOA query retries</span></span>
- <span data-ttu-id="c168e-140">**nx_dns_soa_expire**: Duração do tempo quando o SOA expirar</span><span class="sxs-lookup"><span data-stu-id="c168e-140">**nx_dns_soa_expire**: Time duration when SOA expires</span></span>
- <span data-ttu-id="c168e-141">**nx_dns_soa_minmum**: Campo TTL mínimo em mensagens de resposta DOMS de nome SOA</span><span class="sxs-lookup"><span data-stu-id="c168e-141">**nx_dns_soa_minmum**: Minimum TTL field in SOA hostname DNS reply messages</span></span>

<span data-ttu-id="c168e-142">O armazenamento de dois registos SOA é mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="c168e-142">The storage of a two SOA records is shown below.</span></span> <span data-ttu-id="c168e-143">Os registos SOA que contenham dados de comprimento fixo são introduzidos a partir da parte superior do tampão.</span><span class="sxs-lookup"><span data-stu-id="c168e-143">The SOA records containing fixed length data are entered starting at the top of the buffer.</span></span> <span data-ttu-id="c168e-144">Os ponteiros MNAME e RNAME apontam para os dados de comprimento variável (nomes hospedeiros) que são armazenados na parte inferior do tampão.</span><span class="sxs-lookup"><span data-stu-id="c168e-144">The pointers MNAME and RNAME point to the variable length data (host names) which are stored at the bottom of the buffer.</span></span> <span data-ttu-id="c168e-145">Os registos SOA adicionais são introduzidos após o primeiro registo ("registos SOA adicionais...") e os seus dados de comprimento variável são armazenados acima dos dados variáveis do comprimento da última entrada ("dados adicionais de comprimento variável SOA"):</span><span class="sxs-lookup"><span data-stu-id="c168e-145">Additional SOA records are entered after the first record (“additional SOA records…”) and their variable length data is stored above the last entry’s variable length data (“additional SOA variable length data”):</span></span>

![Diagrama que representa o armazenamento de dois registos S O A](media/image2.png)

<span data-ttu-id="c168e-147">Se a entrada *record_buffer* não conseguir conter todos os dados do SOA na resposta do servidor, o *record_buffer* detém o número de registos que caberão e devolve o número de registos no tampão.</span><span class="sxs-lookup"><span data-stu-id="c168e-147">If the input *record_buffer* cannot hold all the SOA data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="c168e-148">Com o número de registos SOA devolvidos em \**record_count,* a aplicação pode analisar os dados a partir de *record_buffer* e extrair o início das cordas de nome de anfitrião da autoridade da zona.</span><span class="sxs-lookup"><span data-stu-id="c168e-148">With the number of SOA records returned in \**record_count,* the application can parse the data from *record_buffer* and extract the start of zone authority host name strings.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c168e-149">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-149">Input Parameters</span></span>

- <span data-ttu-id="c168e-150">**dns_ptr**: Ponteiro para o Cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-150">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="c168e-151">**host_name**: Ponteiro para o nome de anfitrião para obter dados do SOA</span><span class="sxs-lookup"><span data-stu-id="c168e-151">**host_name**: Pointer to host name to obtain SOA data for</span></span>
- <span data-ttu-id="c168e-152">**record_buffer**: Ponteiro para a localização para extrair dados do SOA em</span><span class="sxs-lookup"><span data-stu-id="c168e-152">**record_buffer**: Pointer to location to extract SOA data into</span></span>
- <span data-ttu-id="c168e-153">**buffer_size**: Tamanho do tampão para reter dados do SOA</span><span class="sxs-lookup"><span data-stu-id="c168e-153">**buffer_size**: Size of buffer to hold SOA data</span></span>
- <span data-ttu-id="c168e-154">**record_count**: Ponteiro para o número de registos SOA recuperados</span><span class="sxs-lookup"><span data-stu-id="c168e-154">**record_count**: Pointer to the number of SOA records retrieved</span></span>
- <span data-ttu-id="c168e-155">**wait_option**: Aguarde a opção para receber a resposta do DNS Server</span><span class="sxs-lookup"><span data-stu-id="c168e-155">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="c168e-156">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c168e-156">Return Values</span></span>

- <span data-ttu-id="c168e-157">**NX_SUCCESS**: (0x00) obteve com sucesso dados do SOA</span><span class="sxs-lookup"><span data-stu-id="c168e-157">**NX_SUCCESS**: (0x00) Successfully obtained SOA data</span></span>
- <span data-ttu-id="c168e-158">**NX_DNS_NO_SERVER**: (0xA1) A lista de servidores de clientes está vazia</span><span class="sxs-lookup"><span data-stu-id="c168e-158">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="c168e-159">**NX_DNS_QUERY_FAILED**: (0xA3) Nenhuma resposta de DNS válida recebida</span><span class="sxs-lookup"><span data-stu-id="c168e-159">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="c168e-160">NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-160">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="c168e-161">NX_CALLER_ERROR: (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="c168e-161">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="c168e-162">NX_DNS_PARAM_ERROR: (0xA8) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="c168e-162">NX_DNS_PARAM_ERROR: (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c168e-163">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c168e-163">Allowed From</span></span>

<span data-ttu-id="c168e-164">Fios</span><span class="sxs-lookup"><span data-stu-id="c168e-164">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c168e-165">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c168e-165">Example</span></span>
```c
UCHAR                  record_buffer[50];
UINT                   record_count;   
NX_DNS_SOA_ENTRY       *nx_dns_soa_entry_ptr;

/* Request the start of authority zone(s) for the specified host.  */
status =  nx_dns_authority_zone_start_get(&client_dns, (UCHAR *)"www.my_example.com",
                                          record _buffer, sizeof(record_buffer), 
                                          &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else 
{
/* If status is NX_SUCCESS a DNS query was successfully completed and SOA data is returned in soa_buffer.  */

/* Set a local pointer to the SOA buffer. */
    nx_dns_soa_entry_ptr = (NX_DNS_SOA_ENTRY *) record_buffer;
    
    printf("------------------------------------------------------\n");
    printf("Test SOA: \n");
    printf("serial = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_serial );
    printf("refresh = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_refresh );
    printf("retry = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_retry );
    printf("expire = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_expire );
    printf("minmum = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_minmum );
    
    if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr)
    {
        printf("host mname = %s\n", 
               nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr);
    }
    else
    {
        printf("host mame is not set\n");
    }
    
    if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr)
    {
        printf("host rname = %s\n", 
               nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr);
    }
    else
    {
     
        printf("host rname is not set\n");
    }
}

```

```Output
Test SOA:
serial = 2012111212
refresh = 7200
retry = 1800
expire = 1209600
minmum = 300
host mname = ns1.www.my_example.com
host rname = dns-admin.www.my_example.com
```


## <a name="nx_dns_cache_initialize"></a><span data-ttu-id="c168e-166">nx_dns_cache_initialize</span><span class="sxs-lookup"><span data-stu-id="c168e-166">nx_dns_cache_initialize</span></span>

<span data-ttu-id="c168e-167">Inicializar a Cache DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-167">Initialize the DNS Cache</span></span>

### <a name="prototype"></a><span data-ttu-id="c168e-168">Prototype</span><span class="sxs-lookup"><span data-stu-id="c168e-168">Prototype</span></span>

```c
UINT nx_dns_cache_initialize(NX_DNS *dns_ptr,
                             VOID *cache_ptr, UINT cache_size);

```
### <a name="description"></a><span data-ttu-id="c168e-169">Descrição</span><span class="sxs-lookup"><span data-stu-id="c168e-169">Description</span></span>

<span data-ttu-id="c168e-170">Este serviço cria e inicializa uma Cache DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-170">This service creates and initializes a DNS Cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c168e-171">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-171">Input Parameters</span></span>

- <span data-ttu-id="c168e-172">**dns_ptr**: Ponteiro para o bloco de controlo DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-172">**dns_ptr**: Pointer to DNS control block.</span></span>
- <span data-ttu-id="c168e-173">**cache_ptr**: Ponteiro para a Cache DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-173">**cache_ptr**: Pointer to DNS Cache.</span></span>
- <span data-ttu-id="c168e-174">**cache_size**: Tamanho da Cache DNS, em bytes.</span><span class="sxs-lookup"><span data-stu-id="c168e-174">**cache_size**: Size of DNS Cache, in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="c168e-175">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c168e-175">Return Values</span></span>

- <span data-ttu-id="c168e-176">**NX_SUCCESS**: (0x00) DNS Cache inicializada com sucesso</span><span class="sxs-lookup"><span data-stu-id="c168e-176">**NX_SUCCESS**: (0x00) DNS Cache successfully initialized</span></span>
- <span data-ttu-id="c168e-177">NX_DNS_ERROR: (0xA0) A cache não está alinhada com 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="c168e-177">NX_DNS_ERROR: (0xA0) Cache is not 4-byte aligned.</span></span>
- <span data-ttu-id="c168e-178">NX_DNS_PARAM_ERROR: (0xA8) ID DNS inválido.</span><span class="sxs-lookup"><span data-stu-id="c168e-178">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="c168e-179">NX_PTR_ERROR: (0x07) Ponteiro DNS inválido.</span><span class="sxs-lookup"><span data-stu-id="c168e-179">NX_PTR_ERROR: (0x07) Invalid DNS pointer.</span></span>
- <span data-ttu-id="c168e-180">NX_CALLER_ERROR: (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="c168e-180">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c168e-181">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c168e-181">Allowed From</span></span>

<span data-ttu-id="c168e-182">Fios</span><span class="sxs-lookup"><span data-stu-id="c168e-182">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c168e-183">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c168e-183">Example</span></span>
```c
UCHAR          dns_cache [2048]; 

/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, dns_cache, 2048);
/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a><span data-ttu-id="c168e-184">nx_dns_cache_notify_clear</span><span class="sxs-lookup"><span data-stu-id="c168e-184">nx_dns_cache_notify_clear</span></span>

<span data-ttu-id="c168e-185">Limpe a função de notificação completa da Cache DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-185">Clear the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="c168e-186">Prototype</span><span class="sxs-lookup"><span data-stu-id="c168e-186">Prototype</span></span>

```c
UINT     nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```
### <a name="description"></a><span data-ttu-id="c168e-187">Descrição</span><span class="sxs-lookup"><span data-stu-id="c168e-187">Description</span></span>

<span data-ttu-id="c168e-188">Este serviço limpa a função de notificação completa da cache.</span><span class="sxs-lookup"><span data-stu-id="c168e-188">This service clears the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c168e-189">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-189">Input Parameters</span></span>

- <span data-ttu-id="c168e-190">**dns_ptr**: Ponteiro para o bloco de controlo DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-190">**dns_ptr**: Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c168e-191">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c168e-191">Return Values</span></span>

- <span data-ttu-id="c168e-192">**NX_SUCCESS**: (0x00) cache DNS notificam com sucesso definido</span><span class="sxs-lookup"><span data-stu-id="c168e-192">**NX_SUCCESS**: (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="c168e-193">NX_DNS_PARAM_ERROR: (0xA8) ID DNS inválido.</span><span class="sxs-lookup"><span data-stu-id="c168e-193">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="c168e-194">NX_PTR_ERROR: (0x07) Ponteiro DNS inválido.</span><span class="sxs-lookup"><span data-stu-id="c168e-194">NX_PTR_ERROR: (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c168e-195">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c168e-195">Allowed From</span></span>

<span data-ttu-id="c168e-196">Fios</span><span class="sxs-lookup"><span data-stu-id="c168e-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c168e-197">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c168e-197">Example</span></span>

```c
/* Clear the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a><span data-ttu-id="c168e-198">nx_dns_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="c168e-198">nx_dns_cache_notify_set</span></span>

<span data-ttu-id="c168e-199">Desa estale a função de notificação completa da Cache DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-199">Set the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="c168e-200">Prototype</span><span class="sxs-lookup"><span data-stu-id="c168e-200">Prototype</span></span>

```c
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr, VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a><span data-ttu-id="c168e-201">Descrição</span><span class="sxs-lookup"><span data-stu-id="c168e-201">Description</span></span>

<span data-ttu-id="c168e-202">Este serviço define a função de notificação completa da cache.</span><span class="sxs-lookup"><span data-stu-id="c168e-202">This service sets the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c168e-203">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-203">Input Parameters</span></span>

- <span data-ttu-id="c168e-204">**dns_ptr**: Ponteiro para o bloco de controlo DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-204">**dns_ptr**: Pointer to DNS control block.</span></span>
- <span data-ttu-id="c168e-205">**cache_full_notify_cb**: A função de retorno a invocar quando a cache ficar cheia.</span><span class="sxs-lookup"><span data-stu-id="c168e-205">**cache_full_notify_cb**: The callback function to be invoked when cache become full.</span></span>

### <a name="return-values"></a><span data-ttu-id="c168e-206">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c168e-206">Return Values</span></span>

- <span data-ttu-id="c168e-207">**NX_SUCCESS**: (0x00) cache DNS notificam com sucesso definido</span><span class="sxs-lookup"><span data-stu-id="c168e-207">**NX_SUCCESS**: (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="c168e-208">NX_DNS_PARAM_ERROR: (0xA8) ID DNS inválido.</span><span class="sxs-lookup"><span data-stu-id="c168e-208">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="c168e-209">NX_PTR_ERROR: (0x07) Ponteiro DNS inválido.</span><span class="sxs-lookup"><span data-stu-id="c168e-209">NX_PTR_ERROR: (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c168e-210">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c168e-210">Allowed From</span></span>

<span data-ttu-id="c168e-211">Fios</span><span class="sxs-lookup"><span data-stu-id="c168e-211">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c168e-212">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c168e-212">Example</span></span>

```c
/* Set the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set.  */
 
```

## <a name="nx_dns_cname_get"></a><span data-ttu-id="c168e-213">nx_dns_cname_get</span><span class="sxs-lookup"><span data-stu-id="c168e-213">nx_dns_cname_get</span></span>

<span data-ttu-id="c168e-214">Procure o nome canónico para o nome de anfitrião de entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-214">Look up the canonical name for the input hostname</span></span>

### <a name="prototype"></a><span data-ttu-id="c168e-215">Prototype</span><span class="sxs-lookup"><span data-stu-id="c168e-215">Prototype</span></span>
```c
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                      UCHAR *record_buffer, UINT buffer_size, 
                      ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c168e-216">Descrição</span><span class="sxs-lookup"><span data-stu-id="c168e-216">Description</span></span>

<span data-ttu-id="c168e-217">Se NX_DNS_ENABLE_EXTENDED_RR_TYPES for definida em *nx_dns.h,* este serviço envia uma consulta do tipo CNAME com o nome de domínio especificado para obter o nome de domínio canónico.</span><span class="sxs-lookup"><span data-stu-id="c168e-217">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined in *nx_dns.h*, this service sends a query of type CNAME with the specified domain name to obtain the canonical domain name.</span></span> <span data-ttu-id="c168e-218">O Cliente DNS copia a cadeia CNAME devolvida na resposta do DNS Server para o local de memória *record_buffer.*</span><span class="sxs-lookup"><span data-stu-id="c168e-218">The DNS Client copies the CNAME string returned in the DNS Server response into the *record_buffer* memory location.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c168e-219">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-219">Input Parameters</span></span>

- <span data-ttu-id="c168e-220">**dns_ptr**: Ponteiro para o Cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-220">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="c168e-221">**host_name**: Ponteiro para o nome de anfitrião para obter dados CNAME para</span><span class="sxs-lookup"><span data-stu-id="c168e-221">**host_name**: Pointer to host name to obtain CNAME data for</span></span>
- <span data-ttu-id="c168e-222">**record_buffer**: Ponteiro para a localização para extrair dados do CNAME</span><span class="sxs-lookup"><span data-stu-id="c168e-222">**record_buffer**: Pointer to location to extract CNAME data into</span></span>
- <span data-ttu-id="c168e-223">**buffer_size**: Tamanho do tampão para conter dados CNAME</span><span class="sxs-lookup"><span data-stu-id="c168e-223">**buffer_size**: Size of buffer to hold CNAME data</span></span>
- <span data-ttu-id="c168e-224">**wait_option**: Aguarde a opção para receber a resposta do DNS Server</span><span class="sxs-lookup"><span data-stu-id="c168e-224">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="c168e-225">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c168e-225">Return Values</span></span>

- <span data-ttu-id="c168e-226">**NX_SUCCESS**: (0x00) obtidos com sucesso dados cname</span><span class="sxs-lookup"><span data-stu-id="c168e-226">**NX_SUCCESS**: (0x00) Successfully obtained CNAME data</span></span>
- <span data-ttu-id="c168e-227">**NX_DNS_NO_SERVER**: (0xA1) A lista de servidores de clientes está vazia</span><span class="sxs-lookup"><span data-stu-id="c168e-227">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="c168e-228">**NX_DNS_QUERY_FAILED**: (0xA3) Nenhuma resposta de DNS válida recebida</span><span class="sxs-lookup"><span data-stu-id="c168e-228">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="c168e-229">NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-229">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="c168e-230">NX_CALLER_ERROR: (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="c168e-230">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="c168e-231">NX_DNS_PARAM_ERROR: (0xA8) Entrada inválida sem ponte</span><span class="sxs-lookup"><span data-stu-id="c168e-231">NX_DNS_PARAM_ERROR: (0xA8) Invalid non-pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c168e-232">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c168e-232">Allowed From</span></span>

<span data-ttu-id="c168e-233">Fios</span><span class="sxs-lookup"><span data-stu-id="c168e-233">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c168e-234">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c168e-234">Example</span></span>

```c
CHAR            record _buffer[50];

/* Request the canonical name for the specified host.  */
status =  nx_dns_cname_get(&client_dns, (UCHAR *)"www.my_example.com ", 
                            record_buffer, sizeof(record_buffer), 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and the canonical host name is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test CNAME: %s\n", record_buffer);
} 
```

```Output
Test CNAME: **my_example**.com
```

## <a name="nx_dns_create"></a><span data-ttu-id="c168e-235">nx_dns_create</span><span class="sxs-lookup"><span data-stu-id="c168e-235">nx_dns_create</span></span>

<span data-ttu-id="c168e-236">Criar uma instância de cliente DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-236">Create a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="c168e-237">Prototype</span><span class="sxs-lookup"><span data-stu-id="c168e-237">Prototype</span></span>

```c
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```

### <a name="description"></a><span data-ttu-id="c168e-238">Descrição</span><span class="sxs-lookup"><span data-stu-id="c168e-238">Description</span></span>

<span data-ttu-id="c168e-239">Este serviço cria uma instância do Cliente DNS para a instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="c168e-239">This service creates a DNS Client instance for the previously created IP instance.</span></span>

>[!NOTE]
><span data-ttu-id="c168e-240">A aplicação deve garantir que a carga útil do pacote do pacote utilizado pelo Cliente DNS seja suficientemente grande para a mensagem máxima de 512 byte DNS, além dos cabeçalhos UDP, IP e Ethernet.</span><span class="sxs-lookup"><span data-stu-id="c168e-240">The application must ensure that the packet payload of the packet pool used by the DNS Client is large enough for the maximum 512 byte DNS message, plus UDP, IP and Ethernet headers.</span></span> <span data-ttu-id="c168e-241">Se o Cliente DNS criar a sua própria piscina de pacotes, isso é definido por NX_DNS_PACKET_POOL_SIZE e NX_DNS_PACKET_PAYLOAD.</span><span class="sxs-lookup"><span data-stu-id="c168e-241">If the DNS Client creates its own packet pool, this is defined by NX_DNS_PACKET_POOL_SIZE and NX_DNS_PACKET_PAYLOAD.</span></span> <span data-ttu-id="c168e-242">Se a aplicação DO CLIENTE DNS preferir fornecer um conjunto de pacotes previamente criado, a carga útil para o IPv4 DNS Cliente deve ser de 512 bytes para o máximo DNS mais 20 bytes para o cabeçalho IP, 8 bytes para o cabeçalho UDP e 14 bytes para o cabeçalho Ethernet.</span><span class="sxs-lookup"><span data-stu-id="c168e-242">If the DNS Client application prefers to supply a previously created packet pool, the payload for IPv4 DNS Client should be 512 bytes for the maximum DNS plus 20 bytes for the IP header, 8 bytes for the UDP header and 14 bytes for the Ethernet header.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c168e-243">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-243">Input Parameters</span></span>

- <span data-ttu-id="c168e-244">**dns_ptr**: Ponteiro para o Cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-244">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="c168e-245">**ip_ptr**: Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="c168e-245">**ip_ptr**: Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="c168e-246">**domain_name**: Ponteiro para o nome de domínio para a instância DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-246">**domain_name**: Pointer to domain name for DNS instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="c168e-247">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c168e-247">Return Values</span></span>

- <span data-ttu-id="c168e-248">**NX_SUCCESS**: (0x00) DNS bem sucedidos criam</span><span class="sxs-lookup"><span data-stu-id="c168e-248">**NX_SUCCESS**: (0x00) Successful DNS create</span></span>
- <span data-ttu-id="c168e-249">**NX_DNS_ERROR**: (0xA0) DNS criam erro</span><span class="sxs-lookup"><span data-stu-id="c168e-249">**NX_DNS_ERROR**: (0xA0) DNS create error</span></span>
- <span data-ttu-id="c168e-250">NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-250">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="c168e-251">NX_CALLER_ERROR: (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="c168e-251">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c168e-252">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c168e-252">Allowed From</span></span>

<span data-ttu-id="c168e-253">Fios</span><span class="sxs-lookup"><span data-stu-id="c168e-253">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c168e-254">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c168e-254">Example</span></span>

```c
/* Create a DNS Client instance.  */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created.  */
```
## <a name="nx_dns_delete"></a><span data-ttu-id="c168e-255">nx_dns_delete</span><span class="sxs-lookup"><span data-stu-id="c168e-255">nx_dns_delete</span></span>

<span data-ttu-id="c168e-256">Excluir uma instância do cliente DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-256">Delete a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="c168e-257">Prototype</span><span class="sxs-lookup"><span data-stu-id="c168e-257">Prototype</span></span>

```c
UINT     nx_dns_delete(NX_DNS *dns_ptr);
```

### <a name="description"></a><span data-ttu-id="c168e-258">Descrição</span><span class="sxs-lookup"><span data-stu-id="c168e-258">Description</span></span>

<span data-ttu-id="c168e-259">Este serviço elimina uma instância do Cliente DNS previamente criada e liberta os seus recursos.</span><span class="sxs-lookup"><span data-stu-id="c168e-259">This service deletes a previously created DNS Client instance and frees up its resources.</span></span> 
>[!NOTE]
> <span data-ttu-id="c168e-260">Se **NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** estiver definido e o Cliente DNS tiver sido atribuído a um pacote de pacotes definido pelo utilizador, cabe à aplicação eliminar o pacote de pacotes DNS Client se já não precisar.</span><span class="sxs-lookup"><span data-stu-id="c168e-260">If **NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** is defined and the DNS Client was assigned a user defined packet pool, it is up to the application to delete the DNS Client packet pool if it no longer needs it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c168e-261">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-261">Input Parameters</span></span>

- <span data-ttu-id="c168e-262">**dns_ptr**: Ponteiro para a instância do **Cliente** DNS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="c168e-262">**dns_ptr**: Pointer to previously created DNS **Client** instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="c168e-263">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c168e-263">Return Values</span></span>

- <span data-ttu-id="c168e-264">**NX_SUCCESS**: (0x00) O Cliente DNS com sucesso apaga.</span><span class="sxs-lookup"><span data-stu-id="c168e-264">**NX_SUCCESS**: (0x00) Successful DNS Client delete.</span></span>
- <span data-ttu-id="c168e-265">NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou dns.</span><span class="sxs-lookup"><span data-stu-id="c168e-265">NX_PTR_ERROR: (0x07) Invalid IP or DNS Client pointer.</span></span>
- <span data-ttu-id="c168e-266">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="c168e-266">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c168e-267">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c168e-267">Allowed From</span></span>

<span data-ttu-id="c168e-268">Fios</span><span class="sxs-lookup"><span data-stu-id="c168e-268">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c168e-269">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c168e-269">Example</span></span>

```c
/* Delete a DNS Client instance.  */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted.  */
```
## <a name="nx_dns_domain_name_server_get"></a><span data-ttu-id="c168e-270">nx_dns_domain_name_server_get</span><span class="sxs-lookup"><span data-stu-id="c168e-270">nx_dns_domain_name_server_get</span></span>

<span data-ttu-id="c168e-271">Procure os servidores de nome autorizados para a zona de domínio de entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-271">Look up the authoritative name servers for the input domain zone</span></span>

### <a name="prototype"></a><span data-ttu-id="c168e-272">Prototype</span><span class="sxs-lookup"><span data-stu-id="c168e-272">Prototype</span></span>

```c
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c168e-273">Descrição</span><span class="sxs-lookup"><span data-stu-id="c168e-273">Description</span></span>

<span data-ttu-id="c168e-274">Se NX_DNS_ENABLE_EXTENDED_RR_TYPES for definido, este serviço envia uma consulta do tipo NS com o nome de domínio especificado para obter os servidores de nome para o nome de domínio de entrada.</span><span class="sxs-lookup"><span data-stu-id="c168e-274">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type NS with the specified domain name to obtain the name servers for the input domain name.</span></span> <span data-ttu-id="c168e-275">O Cliente DNS copia os registos NS devolvidos na resposta do DNS Server para o local de memória *record_buffer.*</span><span class="sxs-lookup"><span data-stu-id="c168e-275">The DNS Client copies the NS record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="c168e-276">O *record_buffer* deve estar alinhado em 4 bytes para receber os dados.</span><span class="sxs-lookup"><span data-stu-id="c168e-276">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="c168e-277">No Cliente NetX DNS o tipo de dados NS, NX_DNS_NS_ENTRY, é guardado como dois parâmetros de 4 byte:</span><span class="sxs-lookup"><span data-stu-id="c168e-277">In NetX DNS Client the NS data type, NX_DNS_NS_ENTRY, is saved as two 4-byte parameters:</span></span>

- <span data-ttu-id="c168e-278">**nx_dns_ns_ipv4_address**: Endereço IPv4 do servidor de nomes</span><span class="sxs-lookup"><span data-stu-id="c168e-278">**nx_dns_ns_ipv4_address**: Name server’s IPv4 address</span></span>
- <span data-ttu-id="c168e-279">**nx_dns_ns_hostname_ptr**: Ponteiro para o nome de anfitrião do servidor de nome</span><span class="sxs-lookup"><span data-stu-id="c168e-279">**nx_dns_ns_hostname_ptr**: Pointer to the name server’s hostname</span></span>

<span data-ttu-id="c168e-280">O tampão mostrado abaixo contém quatro registos NX_DNS_NS_ENTRY.</span><span class="sxs-lookup"><span data-stu-id="c168e-280">The buffer shown below contains four NX_DNS_NS_ENTRY records.</span></span> <span data-ttu-id="c168e-281">O ponteiro para o anfitrião de cadeia de nome em cada ponto de entrada para a cadeia de nome do anfitrião correspondente na metade inferior do tampão:</span><span class="sxs-lookup"><span data-stu-id="c168e-281">The pointer to host name string in each entry points to the corresponding host name string in the bottom half of the buffer:</span></span>

![Diagrama do tampão que contém quatro registos de entrada N X D N S N S.](media/image3.png)

<span data-ttu-id="c168e-283">Se a entrada *record_buffer* não conseguir conter todos os dados NS na resposta do servidor, o *record_buffer* detém o número de registos que caberão e devolve o número de registos no tampão.</span><span class="sxs-lookup"><span data-stu-id="c168e-283">If the input *record_buffer* cannot hold all the NS data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="c168e-284">Com o número de registos NS devolvidos em \**record_count,* a aplicação pode analisar o endereço IP e o nome de anfitrião de cada registo no *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="c168e-284">With the number of NS records returned in \**record_count,* the application can parse the IP address and host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c168e-285">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-285">Input Parameters</span></span>

- <span data-ttu-id="c168e-286">**dns_ptr**: Ponteiro para o Cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-286">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="c168e-287">**host_name**: Ponteiro para o nome de anfitrião para obter dados de NS para</span><span class="sxs-lookup"><span data-stu-id="c168e-287">**host_name**: Pointer to host name to obtain NS data for</span></span>
- <span data-ttu-id="c168e-288">**record_buffer**: Ponteiro para a localização para extrair dados do SNS em</span><span class="sxs-lookup"><span data-stu-id="c168e-288">**record_buffer**: Pointer to location to extract NS data into</span></span>
- <span data-ttu-id="c168e-289">**buffer_size**: Tamanho do tampão para conter dados do NS</span><span class="sxs-lookup"><span data-stu-id="c168e-289">**buffer_size**: Size of buffer to hold NS data</span></span>
- <span data-ttu-id="c168e-290">**record_count**: Ponteiro para o número de registos NS recuperados</span><span class="sxs-lookup"><span data-stu-id="c168e-290">**record_count**: Pointer to the number of NS records retrieved</span></span>
- <span data-ttu-id="c168e-291">**wait_option**: Aguarde a opção para receber a resposta do DNS Server</span><span class="sxs-lookup"><span data-stu-id="c168e-291">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="c168e-292">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c168e-292">Return Values</span></span>

- <span data-ttu-id="c168e-293">**NX_SUCCESS**: (0x00) obteve com sucesso dados de NS</span><span class="sxs-lookup"><span data-stu-id="c168e-293">**NX_SUCCESS**: (0x00) Successfully obtained NS data</span></span>
- <span data-ttu-id="c168e-294">**NX_DNS_NO_SERVER**: (0xA1) A lista de servidores de clientes está vazia</span><span class="sxs-lookup"><span data-stu-id="c168e-294">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="c168e-295">**NX_DNS_QUERY_FAILED**: (0xA3) Nenhuma resposta de DNS válida recebida</span><span class="sxs-lookup"><span data-stu-id="c168e-295">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="c168e-296">NX_DNS_PARAM_ERROR: (0xA8) ID DNS inválido.</span><span class="sxs-lookup"><span data-stu-id="c168e-296">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="c168e-297">NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-297">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="c168e-298">NX_CALLER_ERROR: (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="c168e-298">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c168e-299">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c168e-299">Allowed From</span></span>

<span data-ttu-id="c168e-300">Fios</span><span class="sxs-lookup"><span data-stu-id="c168e-300">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c168e-301">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c168e-301">Example</span></span>
```c
#define RECORD_COUNT        10

ULONG                      record_buffer[50];
UINT                       record_count;          
NX_DNS_NS_ENTRY            *nx_dns_ns_entry_ptr[RECORD_COUNT];

/* Request the name server(s) for the specified host.  */
status =  nx_dns_domain_name_server_get(&client_dns, (UCHAR *)" www.my_example.com ",  
                                        record_buffer, sizeof(record_buffer),  
                                        &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and NS data is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test NS: ");
    printf("record_count = %d \n", record_count);      

    /* Get the name server.  */
    for(i =0; i< record_count; i++)
    {
        nx_dns_ns_entry_ptr[i] = (NX_DNS_NS_ENTRY *)(record_buffer + i * sizeof(NX_DNS_NS_ENTRY)); 

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address  >> 24,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 16 & 0xFF,                   
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 8 & 0xFF,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address & 0xFF);
        if(nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr)
        {
            printf("hostname = %s\n", 
                    nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr);
        }
        else
            printf("hostname is not set\n");
    }
}
```

```Output
Test NS: record_count = 4 
record 0: IP address: 192.2.2.10
hostname = ns2.www.my_example.com
record 1: IP address: 192.2.2.11
hostname = ns1.www.my_example.com
record 2: IP address: 192.2.2.12
hostname = ns3.www.my_example.com
record 3: IP address: 192.2.2.13
hostname = ns4.www.my_example.com
```

## <a name="nx_dns_domain_mail_exchange_get"></a><span data-ttu-id="c168e-302">nx_dns_domain_mail_exchange_get</span><span class="sxs-lookup"><span data-stu-id="c168e-302">nx_dns_domain_mail_exchange_get</span></span>

<span data-ttu-id="c168e-303">Procure a troca de correio para o nome do anfitrião de entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-303">Look up the mail exchange(s) for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="c168e-304">Prototype</span><span class="sxs-lookup"><span data-stu-id="c168e-304">Prototype</span></span>
```c
UINT     nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                        VOID *record_buffer,                                        
                                        UINT buffer_size, 
                                        UINT *record_count, 
                                        ULONG wait_option);

```

### <a name="description"></a><span data-ttu-id="c168e-305">Descrição</span><span class="sxs-lookup"><span data-stu-id="c168e-305">Description</span></span>

<span data-ttu-id="c168e-306">Se NX_DNS_ENABLE_EXTENDED_RR_TYPES for definido, este serviço envia uma consulta do tipo MX com o nome de domínio especificado para obter a troca de correio para o nome de domínio de entrada.</span><span class="sxs-lookup"><span data-stu-id="c168e-306">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type MX with the specified domain name to obtain the mail exchange for the input domain name.</span></span> <span data-ttu-id="c168e-307">O Cliente DNS copia os registos(s) MX devolvidos na resposta do DNS Server para o local de memória *record_buffer.*</span><span class="sxs-lookup"><span data-stu-id="c168e-307">The DNS Client copies the MX record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

>[!NOTE]
><span data-ttu-id="c168e-308">O *record_buffer* deve estar alinhado em 4 bytes para receber os dados.</span><span class="sxs-lookup"><span data-stu-id="c168e-308">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="c168e-309">No Cliente NetX DNS, o tipo de registo de troca de correio, NX_DNS_MAIL_EXCHANGE_ENTRY, é guardado como quatro parâmetros, totalizando 12 bytes:</span><span class="sxs-lookup"><span data-stu-id="c168e-309">In NetX DNS Client, the mail exchange record type, NX_DNS_MAIL_EXCHANGE_ENTRY, is saved as four parameters, totaling 12 bytes:</span></span>

- <span data-ttu-id="c168e-310">**nx_dns_mx_ipv4_address**: Endereço IPv4 de troca de correio 4 bytes</span><span class="sxs-lookup"><span data-stu-id="c168e-310">**nx_dns_mx_ipv4_address**: Mail exchange IPv4 address 4 bytes</span></span>
- <span data-ttu-id="c168e-311">**nx_dns_mx_preference**: Preferência 2 bytes</span><span class="sxs-lookup"><span data-stu-id="c168e-311">**nx_dns_mx_preference**: Preference 2 bytes</span></span>
- <span data-ttu-id="c168e-312">**nx_dns_mx_reserved0**: Reservado 2 bytes</span><span class="sxs-lookup"><span data-stu-id="c168e-312">**nx_dns_mx_reserved0**: Reserved 2 bytes</span></span>
- <span data-ttu-id="c168e-313">**nx_dns_mx_hostname_ptr**: Ponteiro para troca de correio servidor nome de anfitrião 4 bytes</span><span class="sxs-lookup"><span data-stu-id="c168e-313">**nx_dns_mx_hostname_ptr**: Pointer to mail exchange server host name 4 bytes</span></span>

<span data-ttu-id="c168e-314">Um tampão contendo quatro registos MX é mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="c168e-314">A buffer containing four MX records is shown below.</span></span> <span data-ttu-id="c168e-315">Cada registo contém os dados de comprimento fixo da lista acima.</span><span class="sxs-lookup"><span data-stu-id="c168e-315">Each record contains the fixed length data from the list above.</span></span> <span data-ttu-id="c168e-316">O ponteiro para o nome do anfitrião do servidor de troca de correio aponta para o nome de anfitrião correspondente na parte inferior do tampão.</span><span class="sxs-lookup"><span data-stu-id="c168e-316">The pointer to the mail exchange server host name points to the corresponding host name at the bottom of the buffer.</span></span>

![Diagrama que mostra o tampão contendo quatro registos M X.](media/image4.png)

<span data-ttu-id="c168e-318">Se a entrada *record_buffer* não conseguir conter todos os dados MX na resposta do servidor, o *record_buffer* detém o número de registos que caberão e devolve o número de registos no tampão.</span><span class="sxs-lookup"><span data-stu-id="c168e-318">If the input *record_buffer* cannot hold all the MX data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="c168e-319">Com o número de registos MX devolvidos em \**record_count,* a aplicação pode analisar os parâmetros MX, incluindo o nome do anfitrião de cada registo no *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="c168e-319">With the number of MX records returned in \**record_count,* the application can parse the MX parameters, including the mail host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c168e-320">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-320">Input Parameters</span></span>

- <span data-ttu-id="c168e-321">**dns_ptr**: Ponteiro para o Cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-321">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="c168e-322">**host_name**: Ponteiro para o nome de anfitrião para obter dados MX para</span><span class="sxs-lookup"><span data-stu-id="c168e-322">**host_name**: Pointer to host name to obtain MX data for</span></span>
- <span data-ttu-id="c168e-323">**record_buffer**: Ponteiro para a localização para extrair dados de MX em</span><span class="sxs-lookup"><span data-stu-id="c168e-323">**record_buffer**: Pointer to location to extract MX data into</span></span>
- <span data-ttu-id="c168e-324">**buffer_size**: Tamanho do tampão para conter dados MX</span><span class="sxs-lookup"><span data-stu-id="c168e-324">**buffer_size**: Size of buffer to hold MX data</span></span>
- <span data-ttu-id="c168e-325">**record_count**: Ponteiro para o número de registos MX recuperados</span><span class="sxs-lookup"><span data-stu-id="c168e-325">**record_count**: Pointer to the number of MX records retrieved</span></span>
- <span data-ttu-id="c168e-326">**wait_option**: Aguarde a opção para receber a resposta do DNS Server</span><span class="sxs-lookup"><span data-stu-id="c168e-326">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="c168e-327">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c168e-327">Return Values</span></span>

- <span data-ttu-id="c168e-328">**NX_SUCCESS:**(0x00) obteve com sucesso dados de MX</span><span class="sxs-lookup"><span data-stu-id="c168e-328">**NX_SUCCESS**: (0x00) Successfully obtained MX data</span></span>
- <span data-ttu-id="c168e-329">**NX_DNS_NO_SERVER**: (0xA1) A lista de servidores de clientes está vazia</span><span class="sxs-lookup"><span data-stu-id="c168e-329">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="c168e-330">**NX_DNS_QUERY_FAILED**: (0xA3) Nenhuma resposta de DNS válida recebida</span><span class="sxs-lookup"><span data-stu-id="c168e-330">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="c168e-331">NX_DNS_PARAM_ERROR: (0xA8) ID DNS inválido.</span><span class="sxs-lookup"><span data-stu-id="c168e-331">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="c168e-332">NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-332">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="c168e-333">NX_CALLER_ERROR: (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="c168e-333">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c168e-334">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c168e-334">Allowed From</span></span>

<span data-ttu-id="c168e-335">Fios</span><span class="sxs-lookup"><span data-stu-id="c168e-335">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c168e-336">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c168e-336">Example</span></span>
```c
#define           MAX_RECORD_COUNT 10

ULONG             record_buffer[50];
UINT              record_count;  
NX_DNS_MX_ENTRY  *nx_dns_mx_entry_ptr[MAX_RECORD_COUNT];        

/* Request the mail exchange data for the specified host.  */
status =  nx_dns_domain_mail_exchange_get(&client_dns, (UCHAR *)" www.my_example.com ", 
                                          record_buffer, sizeof(record_buffer),   
                                          &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
       
else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and MX data is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test MX: ");
    printf("record_count = %d \n", record_count);      


    /* Get the mail exchange.  */
    for(i =0; i< record_count; i++)
    {
        nx_dns_mx_entry_ptr[i] = (NX_DNS_MX_ENTRY *)(record_buffer + i * sizeof(NX_DNS_MX_ENTRY));   

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 24,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 16 & 0xFF,                   
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 8 & 0xFF,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address & 0xFF);

        printf("preference = %d \n ", nx_dns_mx_entry_ptr[i] -> nx_dns_mx_preference);

        if(nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr)
            printf("hostname = %s\n", nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr);
        else
            printf("hostname is not set\n");
    }
}
```

```Output
Test MX: record_count = 5 
record 0: IP address: 192.2.2.10
preference = 40 
hostname = alt3.aspmx.l.www.my_example.com
record 1: IP address: 192.2.2.11
preference = 50 
hostname = alt4.aspmx.l.www.my_example.com
record 2: IP address: 192.2.2.12
preference = 10 
hostname = aspmx.l.www.my_example.com
record 3: IP address: 192.2.2.13
preference = 20 
hostname = alt1.aspmx.l.www.my_example.com
record 4: IP address: 192.2.2.14
preference = 30 
hostname = alt2.aspmx.l.www.my_example.com
```


## <a name="nx_dns_domain_service_get"></a><span data-ttu-id="c168e-337">nx_dns_domain_service_get</span><span class="sxs-lookup"><span data-stu-id="c168e-337">nx_dns_domain_service_get</span></span>

<span data-ttu-id="c168e-338">Procure o(s) serviço(s) fornecido pelo nome do anfitrião de entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-338">Look up the service(s) provided by the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="c168e-339">Prototype</span><span class="sxs-lookup"><span data-stu-id="c168e-339">Prototype</span></span>

```c
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c168e-340">Descrição</span><span class="sxs-lookup"><span data-stu-id="c168e-340">Description</span></span>

<span data-ttu-id="c168e-341">Se NX_DNS_ENABLE_EXTENDED_RR_TYPES for definido, este serviço envia uma consulta do tipo SRV com o nome de domínio especificado para procurar o(s) serviço(s) e o número de porta associado ao domínio especificado.</span><span class="sxs-lookup"><span data-stu-id="c168e-341">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SRV with the specified domain name to look up the service(s) and their port number associated with the specified domain.</span></span> <span data-ttu-id="c168e-342">O Cliente DNS copia os registos SRV devolvidos na resposta do DNS Server para o local de memória *record_buffer.*</span><span class="sxs-lookup"><span data-stu-id="c168e-342">The DNS Client copies the SRV record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="c168e-343">O *record_buffer* deve estar alinhado em 4 bytes para receber os dados.</span><span class="sxs-lookup"><span data-stu-id="c168e-343">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="c168e-344">No NetX DNS Client, o tipo de registo de serviço, NX_DNS_SRV_ ENTRADA, é guardado como seis parâmetros, totalizando 16 bytes.</span><span class="sxs-lookup"><span data-stu-id="c168e-344">In NetX DNS Client, the service record type, NX_DNS_SRV_ ENTRY, is saved as six parameters, totaling 16 bytes.</span></span> <span data-ttu-id="c168e-345">Isto permite que os dados SRV de comprimento variável sejam armazenados de forma eficiente na memória:</span><span class="sxs-lookup"><span data-stu-id="c168e-345">This enables variable length SRV data to be stored in a memory efficient manner:</span></span>

- <span data-ttu-id="c168e-346">**Endereço IPv4 do servidor**: nx_dns_srv_ipv4_address 4 bytes</span><span class="sxs-lookup"><span data-stu-id="c168e-346">**Server IPv4 address**: nx_dns_srv_ipv4_address 4 bytes</span></span>
- <span data-ttu-id="c168e-347">**Prioridade do servidor**: nx_dns_srv_priority 2 bytes</span><span class="sxs-lookup"><span data-stu-id="c168e-347">**Server priority**: nx_dns_srv_priority 2 bytes</span></span>
- <span data-ttu-id="c168e-348">**Peso do servidor**: nx_dns_srv_weight 2 bytes</span><span class="sxs-lookup"><span data-stu-id="c168e-348">**Server weight**: nx_dns_srv_weight 2 bytes</span></span>
- <span data-ttu-id="c168e-349">**Número da porta de** serviço : nx_dns_srv_port_number 2 bytes</span><span class="sxs-lookup"><span data-stu-id="c168e-349">**Service port number**: nx_dns_srv_port_number 2 bytes</span></span>
- <span data-ttu-id="c168e-350">**Reservado para alinhamento de 4 bytes:** nx_dns_srv_reserved0 2 bytes</span><span class="sxs-lookup"><span data-stu-id="c168e-350">**Reserved for 4-byte alignment**: nx_dns_srv_reserved0 2 bytes</span></span>
- <span data-ttu-id="c168e-351">**Ponteiro para o nome do anfitrião do servidor**: \*nx_dns_srv_hostname_ptr 4 bytes</span><span class="sxs-lookup"><span data-stu-id="c168e-351">**Pointer to server host name**: \*nx_dns_srv_hostname_ptr 4 bytes</span></span>

<span data-ttu-id="c168e-352">Quatro registos SRV são armazenados no tampão fornecido.</span><span class="sxs-lookup"><span data-stu-id="c168e-352">Four SRV records are stored in the supplied buffer.</span></span> <span data-ttu-id="c168e-353">Cada NX_DNS_SRV_ENTRY registo contém um ponteiro, *nx_dns_srv_hostname_ptr,* que aponta para a cadeia de nome do anfitrião correspondente na parte inferior do tampão de gravação:</span><span class="sxs-lookup"><span data-stu-id="c168e-353">Each NX_DNS_SRV_ENTRY record contains a pointer, *nx_dns_srv_hostname_ptr*, that points to the corresponding host name string in the bottom of the record buffer:</span></span>

![Diagrama de quatro registos S R V armazenados no tampão fornecido.](media/image5.png)

<span data-ttu-id="c168e-355">Se a entrada *record_buffer* não conseguir conter todos os dados SRV na resposta do servidor, o *record_buffer* detém o número de registos que caberão e devolve o número de registos no tampão.</span><span class="sxs-lookup"><span data-stu-id="c168e-355">If the input *record_buffer* cannot hold all the SRV data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="c168e-356">Com o número de registos SRV devolvidos em \**record_count,* a aplicação pode analisar os parâmetros SRV, incluindo o nome do anfitrião do servidor de cada registo no *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="c168e-356">With the number of SRV records returned in \**record_count,* the application can parse the SRV parameters, including the server host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c168e-357">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-357">Input Parameters</span></span>

- <span data-ttu-id="c168e-358">**dns_ptr**: Ponteiro para o Cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-358">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="c168e-359">**host_name**: Ponteiro para o nome de anfitrião para obter dados SRV para</span><span class="sxs-lookup"><span data-stu-id="c168e-359">**host_name**: Pointer to host name to obtain SRV data for</span></span>
- <span data-ttu-id="c168e-360">**record_buffer**: Ponteiro para a localização para extrair dados de SRV em</span><span class="sxs-lookup"><span data-stu-id="c168e-360">**record_buffer**: Pointer to location to extract SRV data into</span></span>
- <span data-ttu-id="c168e-361">**buffer_size**: Tamanho do tampão para conter dados SRV</span><span class="sxs-lookup"><span data-stu-id="c168e-361">**buffer_size**: Size of buffer to hold SRV data</span></span>
- <span data-ttu-id="c168e-362">**record_count**: Ponteiro para o número de registos SRV recuperados</span><span class="sxs-lookup"><span data-stu-id="c168e-362">**record_count**: Pointer to the number of SRV records retrieved</span></span>
- <span data-ttu-id="c168e-363">**wait_option**: Aguarde a opção para receber a resposta do DNS Server</span><span class="sxs-lookup"><span data-stu-id="c168e-363">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="c168e-364">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c168e-364">Return Values</span></span>

- <span data-ttu-id="c168e-365">**NX_SUCCESS:**(0x00) Dados SRV obtidos com sucesso</span><span class="sxs-lookup"><span data-stu-id="c168e-365">**NX_SUCCESS**: (0x00) Successfully obtained SRV data</span></span>
- <span data-ttu-id="c168e-366">**NX_DNS_NO_SERVER**: (0xA1) A lista de servidores de clientes está vazia</span><span class="sxs-lookup"><span data-stu-id="c168e-366">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="c168e-367">**NX_DNS_QUERY_FAILED**: (0xA3) Nenhuma resposta de DNS válida recebida</span><span class="sxs-lookup"><span data-stu-id="c168e-367">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="c168e-368">NX_DNS_PARAM_ERROR: (0xA8) ID DNS inválido.</span><span class="sxs-lookup"><span data-stu-id="c168e-368">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="c168e-369">NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-369">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="c168e-370">NX_CALLER_ERROR: (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="c168e-370">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c168e-371">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c168e-371">Allowed From</span></span>

<span data-ttu-id="c168e-372">Fios</span><span class="sxs-lookup"><span data-stu-id="c168e-372">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c168e-373">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c168e-373">Example</span></span>

```c
#define MAX_RECORD_COUNT  10

UCHAR                  record_buffer[50];
UINT                   record_count;
NX_DNS_SRV_ENTRY       *nx_dns_srv_entry_ptr[MAX_RECORD_COUNT];

/* Request the service(s) provided by the specified host.  */
status =  nx_dns_domain_service_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                    record_buffer, sizeof(record_buffer), 
                                    &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and SRV data is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test SRV: ");
    printf("record_count = %d \n", record_count);      

       
    /* Get the location of services.  */
    for(i =0; i< record_count; i++)
    {
        nx_dns_srv_entry_ptr[i] = (NX_DNS_SRV_ENTRY *)(record_buffer + i * sizeof(NX_DNS_SRV_ENTRY)); 

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
        nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 24,
        nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 16 & 0xFF,                   
        nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 8 & 0xFF,
        nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address & 0xFF);

       printf("port number = %d\n", 
               nx_dns_srv_entry_ptr[i] -> nx_dns_srv_port_number );
               printf("priority = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_priority );
       printf("weight = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_weight );

       if(nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr)
       {
            printf("hostname = %s\n", 
            nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr);
        }
       else
            printf("hostname is not set\n");
    }
}
```

```Output
Test SRV: record_count = 3 
record 0: IP address: 192.2.2.10
port number = 5222
priority = 20
weight = 0
hostname = alt4.xmpp.l.www.my_example.com
record 1: IP address: 192.2.2.11
port number = 5222
priority = 5
weight = 0
hostname = xmpp.l.www.my_example.com
record 2: IP address: 192.2.2.12
port number = 5222
priority = 20
weight = 0
hostname = alt1.xmpp.l.www.my_example.com
```

## <a name="nx_dns_get_serverlist_size"></a><span data-ttu-id="c168e-374">nx_dns_get_serverlist_size</span><span class="sxs-lookup"><span data-stu-id="c168e-374">nx_dns_get_serverlist_size</span></span>

<span data-ttu-id="c168e-375">Devolva o tamanho da lista de servidores do cliente DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-375">Return the size of the DNS Client’s Server list</span></span>

### <a name="prototype"></a><span data-ttu-id="c168e-376">Prototype</span><span class="sxs-lookup"><span data-stu-id="c168e-376">Prototype</span></span>

```c
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```

### <a name="description"></a><span data-ttu-id="c168e-377">Descrição</span><span class="sxs-lookup"><span data-stu-id="c168e-377">Description</span></span>

<span data-ttu-id="c168e-378">Este serviço devolve o número de Servidores DNS válidos na lista de Clientes.</span><span class="sxs-lookup"><span data-stu-id="c168e-378">This service returns the number of valid DNS Servers in the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c168e-379">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-379">Input Parameters</span></span>

- <span data-ttu-id="c168e-380">**dns_ptr**: Ponteiro para bloco de controlo DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-380">**dns_ptr**: Pointer to DNS control block</span></span>  
- <span data-ttu-id="c168e-381">**tamanho**: Devolve o número de servidores na lista</span><span class="sxs-lookup"><span data-stu-id="c168e-381">**size**: Returns the number of servers in the list</span></span>

### <a name="return-values"></a><span data-ttu-id="c168e-382">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c168e-382">Return Values</span></span>

- <span data-ttu-id="c168e-383">**NX_SUCCESS**: (0x00) O tamanho da lista do Servidor DNS regressou com sucesso</span><span class="sxs-lookup"><span data-stu-id="c168e-383">**NX_SUCCESS**: (0x00) DNS Server list size successfully returned</span></span>
- <span data-ttu-id="c168e-384">NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-384">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="c168e-385">NX_CALLER_ERROR: (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="c168e-385">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c168e-386">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c168e-386">Allowed From</span></span>

<span data-ttu-id="c168e-387">Fios</span><span class="sxs-lookup"><span data-stu-id="c168e-387">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c168e-388">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c168e-388">Example</span></span>

```c
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list.  */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned.  */
```

## <a name="nx_dns_info_by_name_get"></a><span data-ttu-id="c168e-389">nx_dns_info_by_name_get</span><span class="sxs-lookup"><span data-stu-id="c168e-389">nx_dns_info_by_name_get</span></span>

<span data-ttu-id="c168e-390">Endereço IP de devolução e porta do servidor DNS pelo nome de anfitrião</span><span class="sxs-lookup"><span data-stu-id="c168e-390">Return ip address and port of DNS server by host name</span></span>

### <a name="prototype"></a><span data-ttu-id="c168e-391">Prototype</span><span class="sxs-lookup"><span data-stu-id="c168e-391">Prototype</span></span>

```c
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c168e-392">Descrição</span><span class="sxs-lookup"><span data-stu-id="c168e-392">Description</span></span>

<span data-ttu-id="c168e-393">Este serviço devolve o IP do Servidor e a porta (registo de serviço) com base no nome do anfitrião de entrada por consulta DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-393">This service returns the Server IP and port (service record) based on the input host name by DNS query.</span></span> <span data-ttu-id="c168e-394">Se não for encontrado um registo de serviço, esta rotina devolve um endereço IP zero no ponteiro do endereço de entrada e um estado de erro não zero volta a sinalizar um erro.</span><span class="sxs-lookup"><span data-stu-id="c168e-394">If a service record is not found, this routine returns a zero IP address in the input address pointer and a non-zero error status return to signal an error.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c168e-395">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-395">Input Parameters</span></span>

- <span data-ttu-id="c168e-396">**dns_ptr**: Ponteiro para bloco de controlo DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-396">**dns_ptr**: Pointer to DNS control block</span></span>  
- <span data-ttu-id="c168e-397">**host_name**: Ponteiro para o tampão do nome anfitrião</span><span class="sxs-lookup"><span data-stu-id="c168e-397">**host_name**: Pointer to host name buffer</span></span>
- <span data-ttu-id="c168e-398">**host_address_ptr**: Ponteiro para endereçar para regressar</span><span class="sxs-lookup"><span data-stu-id="c168e-398">**host_address_ptr**: Pointer to address to return</span></span>
- <span data-ttu-id="c168e-399">**host_port_ptr:** Ponteiro para a porta para devolver wait_option Opção de espera para a resposta ao DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-399">**host_port_ptr**: Pointer to port to return wait_option Wait option for the DNS response</span></span>

### <a name="return-values"></a><span data-ttu-id="c168e-400">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c168e-400">Return Values</span></span>

- <span data-ttu-id="c168e-401">**NX_SUCCESS**: (0x00) Registo do DNS Server devolvido com sucesso</span><span class="sxs-lookup"><span data-stu-id="c168e-401">**NX_SUCCESS**: (0x00) DNS Server record successfully returned</span></span>
- <span data-ttu-id="c168e-402">**NX_DNS_NO_SERVER**: (0xA1) Nenhum Servidor DNS registado com o Cliente para enviar consulta no nome anfitrião</span><span class="sxs-lookup"><span data-stu-id="c168e-402">**NX_DNS_NO_SERVER**: (0xA1) No DNS Server registered with Client to send query on hostname</span></span>
- <span data-ttu-id="c168e-403">**NX_DNS_QUERY_FAILED**: (0xA3) A consulta do DNS falhou; não há resposta de nenhum servidor DNS na lista de Clientes ou nenhum registo de serviço está disponível para o nome de anfitrião de entrada.</span><span class="sxs-lookup"><span data-stu-id="c168e-403">**NX_DNS_QUERY_FAILED**: (0xA3) DNS query failed; no response from any DNS servers in Client list or no service record is available for the input hostname.</span></span>
- <span data-ttu-id="c168e-404">NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-404">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="c168e-405">NX_CALLER_ERROR: (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="c168e-405">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c168e-406">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c168e-406">Allowed From</span></span>

<span data-ttu-id="c168e-407">Fios</span><span class="sxs-lookup"><span data-stu-id="c168e-407">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c168e-408">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c168e-408">Example</span></span>
```c
ULONG         ip_address;
USHORT         port;

/* Attempt to resolve the IP address and ports for this host name.  */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned.  */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a><span data-ttu-id="c168e-409">nx_dns_ipv4_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="c168e-409">nx_dns_ipv4_address_by_name_get</span></span>

<span data-ttu-id="c168e-410">Procure o endereço IPv4 para o nome do anfitrião de entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-410">Look up the IPv4 address for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="c168e-411">Prototype</span><span class="sxs-lookup"><span data-stu-id="c168e-411">Prototype</span></span>

```c
UINT nx_dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                       UCHAR *host_name_ptr, VOID *buffer, 
                                       UINT buffer_size, 
                                       UINT *record_count,
                                       ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c168e-412">Descrição</span><span class="sxs-lookup"><span data-stu-id="c168e-412">Description</span></span>

<span data-ttu-id="c168e-413">Este serviço envia uma consulta do tipo A com o nome de anfitrião especificado para obter os endereços IP para o nome do anfitrião de entrada.</span><span class="sxs-lookup"><span data-stu-id="c168e-413">This service sends a query of Type A with the specified host name to obtain the IP addresses for the input host name.</span></span> <span data-ttu-id="c168e-414">O Cliente DNS copia o endereço IPv4 a partir dos registos A devolvidos na resposta do DNS Server para o local de memória *record_buffer.*</span><span class="sxs-lookup"><span data-stu-id="c168e-414">The DNS Client copies the IPv4 address from the A record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="c168e-415">O *record_buffer* deve estar alinhado em 4 bytes para receber os dados.</span><span class="sxs-lookup"><span data-stu-id="c168e-415">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="c168e-416">Vários endereços IPv4 são armazenados no tampão alinhado de 4 byte, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="c168e-416">Multiple IPv4 addresses are stored in the 4-byte aligned buffer as shown below:</span></span>

![Diagrama de vários endereços I P v 4 que são armazenados no tampão alinhado 4 byte.](media/image6.png)

<span data-ttu-id="c168e-418">Se o tampão fornecido não conseguir conter todos os dados do endereço IP, os restantes registos A não são armazenados em *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="c168e-418">If the supplied buffer cannot hold all the IP address data, the remaining A records are not stored in *record_buffer*.</span></span> <span data-ttu-id="c168e-419">Isto permite que a aplicação recupere um, alguns ou todos os dados de endereço IP disponíveis na resposta do servidor.</span><span class="sxs-lookup"><span data-stu-id="c168e-419">This enables the application to retrieve one, some or all of the available IP address data in the server reply.</span></span>

<span data-ttu-id="c168e-420">Com o número de registos A devolvidos \**record_count* a aplicação pode analisar os dados de endereço IPv4 do *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="c168e-420">With the number of A records returned in \**record_count* the application can parse the IPv4 address data from the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c168e-421">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-421">Input Parameters</span></span>

- <span data-ttu-id="c168e-422">**dns_ptr**: Ponteiro para o Cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-422">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="c168e-423">**host_name_ptr**: Ponteiro para o nome de anfitrião para obter o ponteiro do tampão de endereço IPv4 para a localização para extrair dados do IPv4</span><span class="sxs-lookup"><span data-stu-id="c168e-423">**host_name_ptr**: Pointer to host name to obtain IPv4 address buffer Pointer to location to extract IPv4 data into</span></span>
- <span data-ttu-id="c168e-424">**buffer_size**: Tamanho do tampão para conter dados IPv4</span><span class="sxs-lookup"><span data-stu-id="c168e-424">**buffer_size**: Size of buffer to hold IPv4 data</span></span>
- <span data-ttu-id="c168e-425">**wait_option**: Aguarde a opção para receber a resposta do DNS Server</span><span class="sxs-lookup"><span data-stu-id="c168e-425">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="c168e-426">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c168e-426">Return Values</span></span>

- <span data-ttu-id="c168e-427">**NX_SUCCESS:**(0x00) obteve com sucesso dados do IPv4</span><span class="sxs-lookup"><span data-stu-id="c168e-427">**NX_SUCCESS**: (0x00) Successfully obtained IPv4 data</span></span>
- <span data-ttu-id="c168e-428">**NX_DNS_NO_SERVER**: (0xA1) A lista de servidores de clientes está vazia</span><span class="sxs-lookup"><span data-stu-id="c168e-428">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="c168e-429">**NX_DNS_QUERY_FAILED**: (0xA3) Nenhuma resposta de DNS válida recebida</span><span class="sxs-lookup"><span data-stu-id="c168e-429">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="c168e-430">NX_DNS_PARAM_ERROR: (0xA8) Parâmetro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="c168e-430">NX_DNS_PARAM_ERROR: (0xA8) Invalid input parameter.</span></span>
- <span data-ttu-id="c168e-431">NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-431">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="c168e-432">NX_CALLER_ERROR: (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="c168e-432">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c168e-433">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c168e-433">Allowed From</span></span>

<span data-ttu-id="c168e-434">Fios</span><span class="sxs-lookup"><span data-stu-id="c168e-434">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c168e-435">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c168e-435">Example</span></span>

```c
#define MAX_RECORD_COUNT  20

ULONG           record_buffer[50];
UINT            record_count;
ULONG           *ipv4_address_ptr[MAX_RECORD_COUNT];

/* Request the IPv4 address for the specified host.  */
status =  nx_dns_ipv4_address_by_name_get(&client_dns, 
                                          (UCHAR *)"www.my_example.com",  
                                           record_buffer,                  
                                           sizeof(record_buffer),&record_count,                
                                           500);

        /* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
        error_counter++;
}    
else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed the IPv4 address(es) is returned in record_buffer.  */
    printf("------------------------------------------------------\n");
    printf("Test A: ");
    printf("record_count = %d \n", record_count);      


    /* Get the IPv4 addresses of host.  */
    for(i =0; i< record_count; i++)
    {
        ipv4_address_ptr[i] = (ULONG *)(record_buffer + i * sizeof(ULONG)); 
        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                *ipv4_address_ptr[i] >> 24,
                *ipv4_address_ptr[i] >> 16 & 0xFF,                   
                *ipv4_address_ptr[i] >> 8 & 0xFF,
                *ipv4_address_ptr[i] & 0xFF);
    }
}
```

```Output
------------------------------------------------------
Test A: record_count = 5 
record 0: IP address: 192.2.2.10
record 1: IP address: 192.2.2.11
record 2: IP address: 192.2.2.12
record 3: IP address: 192.2.2.13
record 4: IP address: 192.2.2.14
```

## <a name="nx_dns_host_by_address_get"></a><span data-ttu-id="c168e-436">nx_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="c168e-436">nx_dns_host_by_address_get</span></span>

<span data-ttu-id="c168e-437">Procure um nome de anfitrião a partir de um endereço IP</span><span class="sxs-lookup"><span data-stu-id="c168e-437">Look up a host name from an IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="c168e-438">Prototype</span><span class="sxs-lookup"><span data-stu-id="c168e-438">Prototype</span></span>

```c
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c168e-439">Descrição</span><span class="sxs-lookup"><span data-stu-id="c168e-439">Description</span></span>

<span data-ttu-id="c168e-440">Este serviço solicita a resolução de nome do endereço IP fornecido a partir de um ou mais Servidores DNS previamente especificados pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="c168e-440">This service requests name resolution of the supplied IP address from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="c168e-441">Se for bem sucedido, o nome do anfitrião rescindido por NU É devolvido na cadeia especificada por *host_name_ptr*.</span><span class="sxs-lookup"><span data-stu-id="c168e-441">If successful, the NULL-terminated host name is returned in the string specified by *host_name_ptr*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c168e-442">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-442">Input Parameters</span></span>

- <span data-ttu-id="c168e-443">**dns_ptr**: Ponteiro para a instância DNS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="c168e-443">**dns_ptr**: Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="c168e-444">**ip_address**: Endereço IP para resolver em nome</span><span class="sxs-lookup"><span data-stu-id="c168e-444">**ip_address**: IP address to resolve into a name</span></span>
- <span data-ttu-id="c168e-445">**host_name_ptr**: Ponteiro para a área de destino para o nome de anfitrião</span><span class="sxs-lookup"><span data-stu-id="c168e-445">**host_name_ptr**: Pointer to destination area for host name</span></span>
- <span data-ttu-id="c168e-446">**max_host_name_size**: Tamanho da área de destino para o nome de hospedeiro</span><span class="sxs-lookup"><span data-stu-id="c168e-446">**max_host_name_size**: Size of destination area for host name</span></span>
- <span data-ttu-id="c168e-447">**wait_option**: Define quanto tempo o serviço irá esperar nos tiques temporizadores para uma resposta do servidor DNS após cada consulta de DNS e retry de consulta As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="c168e-447">**wait_option**: Defines how long the service will wait in timer ticks for a DNS server response after each DNS query and query retry The wait options are defined as follows:</span></span>
    - <span data-ttu-id="c168e-448">**valor de tempo limite**: (0x00000001-0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resolução do DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-448">**timeout value**: (0x00000001-0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>
    - <span data-ttu-id="c168e-449">**TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que um servidor DNS responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="c168e-449">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="c168e-450">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c168e-450">Return Values</span></span>

- <span data-ttu-id="c168e-451">**NX_SUCCESS**: (0x00) Resolução bem sucedida do DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-451">**NX_SUCCESS**: (0x00) Successful DNS resolution</span></span>  
- <span data-ttu-id="c168e-452">**NX_DNS_TIMEOUT**: (0xA2) Cronometrado na obtenção de mutex DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-452">**NX_DNS_TIMEOUT**: (0xA2) Timed out on obtaining DNS mutex</span></span>
- <span data-ttu-id="c168e-453">**NX_DNS_NO_SERVER**: (0xA1) Não é especificado nenhum endereço DNS Server</span><span class="sxs-lookup"><span data-stu-id="c168e-453">**NX_DNS_NO_SERVER**: (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="c168e-454">**NX_DNS_QUERY_FAILED**: (0xA3) Não recebeu resposta à consulta</span><span class="sxs-lookup"><span data-stu-id="c168e-454">**NX_DNS_QUERY_FAILED**: (0xA3) Received no response to query</span></span>
- <span data-ttu-id="c168e-455">**NX_DNS_BAD_ADDRESS_ERROR:**(0xA4) Endereço de entrada nulo</span><span class="sxs-lookup"><span data-stu-id="c168e-455">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Null input address</span></span>
- <span data-ttu-id="c168e-456">**NX_DNS_INVALID_ADDRESS_TYPE**: (0xB2) O índice aponta para o tipo de endereço inválido (por exemplo, IPv6)</span><span class="sxs-lookup"><span data-stu-id="c168e-456">**NX_DNS_INVALID_ADDRESS_TYPE**: (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="c168e-457">**NX_DNS_PARAM_ERROR:**(0xA8) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="c168e-457">**NX_DNS_PARAM_ERROR**: (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="c168e-458">NX_PTR_ERROR: (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="c168e-458">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="c168e-459">NX_CALLER_ERROR: (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="c168e-459">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c168e-460">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c168e-460">Allowed From</span></span>

<span data-ttu-id="c168e-461">Fios</span><span class="sxs-lookup"><span data-stu-id="c168e-461">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c168e-462">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c168e-462">Example</span></span>

```c
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */

```

## <a name="nx_dns_host_by_name_get"></a><span data-ttu-id="c168e-463">nx_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="c168e-463">nx_dns_host_by_name_get</span></span>

<span data-ttu-id="c168e-464">Procure um endereço IP a partir do nome do anfitrião</span><span class="sxs-lookup"><span data-stu-id="c168e-464">Look up an IP address from the host name</span></span>

### <a name="prototype"></a><span data-ttu-id="c168e-465">Prototype</span><span class="sxs-lookup"><span data-stu-id="c168e-465">Prototype</span></span>

```c
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c168e-466">Descrição</span><span class="sxs-lookup"><span data-stu-id="c168e-466">Description</span></span>

<span data-ttu-id="c168e-467">Este serviço solicita a resolução de nome do nome fornecido, apontado por *host_name*, a partir de um ou mais Servidores DNS previamente especificados pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="c168e-467">This service requests name resolution of the supplied name, pointed to by *host_name*, from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="c168e-468">Se for bem sucedido, o endereço IP associado é devolvido no destino apontado por *host_address_ptr*.</span><span class="sxs-lookup"><span data-stu-id="c168e-468">If successful, the associated IP address is returned in the destination pointed to by *host_address_ptr*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c168e-469">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-469">Input Parameters</span></span>

- <span data-ttu-id="c168e-470">**dns_ptr**: Ponteiro para a instância DNS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="c168e-470">**dns_ptr**: Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="c168e-471">**host_name**: Ponteiro para o nome de anfitrião</span><span class="sxs-lookup"><span data-stu-id="c168e-471">**host_name**: Pointer to host name</span></span>
- <span data-ttu-id="c168e-472">**host_address_ptr**: Ponteiro para o endereço IP do anfitrião DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-472">**host_address_ptr**: Pointer to DNS host IP address</span></span>
- <span data-ttu-id="c168e-473">**wait_option**: Define quanto tempo o serviço aguarda pela resolução do DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-473">**wait_option**: Defines how long the service will wait for the DNS resolution.</span></span> <span data-ttu-id="c168e-474">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="c168e-474">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="c168e-475">**valor de tempo limite**: (0x00000001 a 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resolução do DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-475">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>
    - <span data-ttu-id="c168e-476">**TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que um servidor DNS responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="c168e-476">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="c168e-477">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c168e-477">Return Values</span></span>

- <span data-ttu-id="c168e-478">**NX_SUCCESS:**(0x00) Resolução de DNS bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="c168e-478">**NX_SUCCESS**: (0x00) Successful DNS resolution.</span></span>
- <span data-ttu-id="c168e-479">**NX_DNS_NO_SERVER**: (0xA1) Não é especificado nenhum endereço DNS Server</span><span class="sxs-lookup"><span data-stu-id="c168e-479">**NX_DNS_NO_SERVER**: (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="c168e-480">**NX_DNS_QUERY_FAILED**: (0xA3) Não recebeu resposta à consulta</span><span class="sxs-lookup"><span data-stu-id="c168e-480">**NX_DNS_QUERY_FAILED**: (0xA3) Received no response to query</span></span>
- <span data-ttu-id="c168e-481">NX_DNS_PARAM_ERROR: (0xA8) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="c168e-481">NX_DNS_PARAM_ERROR: (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="c168e-482">NX_PTR_ERROR: (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="c168e-482">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="c168e-483">NX_CALLER_ERROR: (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="c168e-483">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c168e-484">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c168e-484">Allowed From</span></span>

<span data-ttu-id="c168e-485">Fios</span><span class="sxs-lookup"><span data-stu-id="c168e-485">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c168e-486">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c168e-486">Example</span></span>
```c
ULONG ip_address;

    /* Get the IP address for the name “www.my_example.com”.  */
    status =  nx_dns_host_by_name_get(&my_dns, “www.my_example.com”, &ip_address, 4000);

    /* Check for DNS query error.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else     
    {

    /* If status is NX_SUCCESS the IP address for “www.my_example.com” can be found in the “ip_address” variable.  */
        
        printf("------------------------------------------------------\n");
        printf("Test A: \n");
        printf("IP address: %d.%d.%d.%d\n",
                host_ip_address >> 24,
                host_ip_address >> 16 & 0xFF,                   
                host_ip_address >> 8 & 0xFF,
                host_ip_address & 0xFF);
    }
```

```Output
Test A: 
IP address: 192.2.2.10
```

## <a name="nx_dns_host_text_get"></a><span data-ttu-id="c168e-487">nx_dns_host_text_get</span><span class="sxs-lookup"><span data-stu-id="c168e-487">nx_dns_host_text_get</span></span>

<span data-ttu-id="c168e-488">Procure a cadeia de texto para o nome de domínio de entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-488">Look up the text string for the input domain name</span></span>

### <a name="prototype"></a><span data-ttu-id="c168e-489">Prototype</span><span class="sxs-lookup"><span data-stu-id="c168e-489">Prototype</span></span>

```c
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c168e-490">Descrição</span><span class="sxs-lookup"><span data-stu-id="c168e-490">Description</span></span>

<span data-ttu-id="c168e-491">Este serviço envia uma consulta do tipo TXT com o nome de domínio especificado e tampão para obter os dados de cadeia arbitrários.</span><span class="sxs-lookup"><span data-stu-id="c168e-491">This service sends a query of type TXT with the specified domain name and buffer to obtain the arbitrary string data.</span></span>

<span data-ttu-id="c168e-492">O Cliente DNS copia a cadeia de texto no registo TXT na resposta do DNS Server para a *localização da* memória record_buffer.</span><span class="sxs-lookup"><span data-stu-id="c168e-492">The DNS Client copies the text string in the TXT record in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="c168e-493">O *record_buffer* não precisa de estar alinhado com 4 byte para receber os dados.</span><span class="sxs-lookup"><span data-stu-id="c168e-493">The *record_buffer* does not need to be 4-byte aligned to receive the data.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c168e-494">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-494">Input Parameters</span></span>

- <span data-ttu-id="c168e-495">**dns_ptr**: Ponteiro para o Cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-495">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="c168e-496">**host_name**: Ponteiro para o nome do anfitrião para pesquisar</span><span class="sxs-lookup"><span data-stu-id="c168e-496">**host_name**: Pointer to name of host to search on</span></span>
- <span data-ttu-id="c168e-497">**record_buffer**: Ponteiro para a localização para extrair dados TXT em</span><span class="sxs-lookup"><span data-stu-id="c168e-497">**record_buffer**: Pointer to location to extract TXT data into</span></span>
- <span data-ttu-id="c168e-498">**buffer_size**: Tamanho do tampão para conter dados TXT</span><span class="sxs-lookup"><span data-stu-id="c168e-498">**buffer_size**: Size of buffer to hold TXT data</span></span>
- <span data-ttu-id="c168e-499">**wait_option**: Aguarde a opção para receber a resposta do DNS Server</span><span class="sxs-lookup"><span data-stu-id="c168e-499">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="c168e-500">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c168e-500">Return Values</span></span>

- <span data-ttu-id="c168e-501">**NX_SUCCESS**: (0x00) Cadeia TXT obtida com sucesso</span><span class="sxs-lookup"><span data-stu-id="c168e-501">**NX_SUCCESS**: (0x00) Successfully TXT string obtained</span></span>
- <span data-ttu-id="c168e-502">**NX_DNS_NO_SERVER**: (0xA1) A lista de servidores de clientes está vazia</span><span class="sxs-lookup"><span data-stu-id="c168e-502">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="c168e-503">**NX_DNS_QUERY_FAILED**: (0xA3) Nenhuma resposta de DNS válida recebida</span><span class="sxs-lookup"><span data-stu-id="c168e-503">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="c168e-504">NX_PTR_ERROR: (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="c168e-504">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="c168e-505">NX_CALLER_ERROR: (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="c168e-505">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="c168e-506">NX_DNS_PARAM_ERROR: (0xA8) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="c168e-506">NX_DNS_PARAM_ERROR: (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c168e-507">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c168e-507">Allowed From</span></span>

<span data-ttu-id="c168e-508">Fios</span><span class="sxs-lookup"><span data-stu-id="c168e-508">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c168e-509">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c168e-509">Example</span></span>

```c
CHAR            record_buffer[50];

/* Request the text string for the specified host.  */
status =  nx_dns_host_text_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                record_buffer, 
                                sizeof(record_buffer), 500);


/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
     error_counter++;
}
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and the text string is returned in record_buffer.  */
 
     printf("------------------------------------------------------\n");
     printf("Test TXT:\n %s\n", record_buffer);
} 
```

```Output
Test TXT: 
v=spf1 include:_www.my_example.com ip4:192.2.2.10/31 ip4:192.2.2.11/31 ~all
```

## <a name="nx_dns_packet_pool_set"></a><span data-ttu-id="c168e-510">nx_dns_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="c168e-510">nx_dns_packet_pool_set</span></span>

<span data-ttu-id="c168e-511">Desa estaladiço do pacote do cliente DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-511">Set the DNS Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="c168e-512">Prototype</span><span class="sxs-lookup"><span data-stu-id="c168e-512">Prototype</span></span>

```c
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="c168e-513">Descrição</span><span class="sxs-lookup"><span data-stu-id="c168e-513">Description</span></span>

<span data-ttu-id="c168e-514">Este serviço define um pacote de pacotes previamente criado como o pacote de pacotes DNS **Client.**</span><span class="sxs-lookup"><span data-stu-id="c168e-514">This service sets a previously created packet pool as the DNS **Client** packet pool.</span></span> <span data-ttu-id="c168e-515">O Cliente DNS utilizará este pacote para enviar consultas de DNS, pelo que a carga útil do pacote não deve ser inferior a NX_DNS_PACKET_PAYLOAD_UNALIGNED que inclui os cabeçalhos Ethernet, IP e UDP e é definido em *nx_dns.h*.</span><span class="sxs-lookup"><span data-stu-id="c168e-515">The DNS Client will use this packet pool to send DNS queries, so the packet payload should not be less than NX_DNS_PACKET_PAYLOAD_UNALIGNED which includes the Ethernet frame, IP and UDP headers and is defined in *nx_dns.h*.</span></span>
 
>[!NOTE]
><span data-ttu-id="c168e-516">Quando o Cliente DNS é eliminado, o pacote não é apagado com ele e é da responsabilidade da aplicação apagar o pacote quando já não precisa.</span><span class="sxs-lookup"><span data-stu-id="c168e-516">When the DNS Client is deleted, the packet pool is not deleted with it and it is the responsibility of the application to delete the packet pool when it no longer needs it.</span></span>

>[!NOTE]
><span data-ttu-id="c168e-517">Este serviço só está disponível se a opção de configuração NX_DNS_CLIENT_USER_CREATE_PACKET_POOL for definida em *nx_dns.h*</span><span class="sxs-lookup"><span data-stu-id="c168e-517">This service is only available if the configuration option NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined in *nx_dns.h*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c168e-518">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-518">Input Parameters</span></span>

- <span data-ttu-id="c168e-519">**dns_ptr**: Ponteiro para a instância do **Cliente** DNS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="c168e-519">**dns_ptr**: Pointer to previously created DNS **Client** instance.</span></span>
- <span data-ttu-id="c168e-520">**pool_ptr**: Ponteiro para piscina de pacotes previamente criada</span><span class="sxs-lookup"><span data-stu-id="c168e-520">**pool_ptr**: Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="c168e-521">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c168e-521">Return Values</span></span>

- <span data-ttu-id="c168e-522">**NX_SUCCESS:**(0x00) Conclusão bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="c168e-522">**NX_SUCCESS**: (0x00) Successful completion.</span></span>
- <span data-ttu-id="c168e-523">**NX_NOT_ENABLED:**(0x14) Cliente não configurado para esta opção</span><span class="sxs-lookup"><span data-stu-id="c168e-523">**NX_NOT_ENABLED**: (0x14) Client not configured for this option</span></span>
- <span data-ttu-id="c168e-524">NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou **DNS.**</span><span class="sxs-lookup"><span data-stu-id="c168e-524">NX_PTR_ERROR: (0x07) Invalid IP or DNS **Client** pointer.</span></span>
- <span data-ttu-id="c168e-525">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="c168e-525">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c168e-526">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c168e-526">Allowed From</span></span>

<span data-ttu-id="c168e-527">Fios</span><span class="sxs-lookup"><span data-stu-id="c168e-527">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c168e-528">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c168e-528">Example</span></span>
```c
NX_DNS             my_dns;
NX_PACKET_POOL     client_pool;
NX_IP             *ip_ptr;


/* Create the DNS Client.  */
status =  nx_dns_create(&my_dns, ip_ptr, “My DNS Client”);

/* Create a packet pool for the DNS Client.  */
status =  nx_packet_pool_create(&client_pool, "DNS Client Packet Pool", 
                                 NX_DNS_PACKET_PAYLOAD, free_mem_pointer, 
                                 NX_DNS_PACKET_POOL_SIZE);

/* Set the DNS Client packet pool.  */
status =  nx_dns_packet_pool_set(&my_dns, &client_pool);

/* If status is NX_SUCCESS the DNS Client packet pool was successfully set.  */
```

## <a name="nx_dns_server_add"></a><span data-ttu-id="c168e-529">nx_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="c168e-529">nx_dns_server_add</span></span>

<span data-ttu-id="c168e-530">Adicionar endereço IP do servidor DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-530">Add DNS Server IP Address</span></span>

### <a name="prototype"></a><span data-ttu-id="c168e-531">Prototype</span><span class="sxs-lookup"><span data-stu-id="c168e-531">Prototype</span></span>

```c
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="c168e-532">Descrição</span><span class="sxs-lookup"><span data-stu-id="c168e-532">Description</span></span>

<span data-ttu-id="c168e-533">Este serviço adiciona um Servidor DNS IPv4 à lista de servidores.</span><span class="sxs-lookup"><span data-stu-id="c168e-533">This service adds an IPv4 DNS Server to the server list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c168e-534">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-534">Input Parameters</span></span>

- <span data-ttu-id="c168e-535">**dns_ptr**: Ponteiro para o bloco de controlo DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-535">**dns_ptr**: Pointer to DNS control block.</span></span>  
- <span data-ttu-id="c168e-536">**server_address**: Endereço IP do Servidor DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-536">**server_address**: IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="c168e-537">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c168e-537">Return Values</span></span>

- <span data-ttu-id="c168e-538">**NX_SUCCESS**: (0x00) Servidor adicionado com sucesso</span><span class="sxs-lookup"><span data-stu-id="c168e-538">**NX_SUCCESS**: (0x00) Server successfully added</span></span>
- <span data-ttu-id="c168e-539">**NX_DNS_DUPLICATE_ENTRY** ou **NX_NO_MORE_ENTRIES:**(0x17) Não são permitidos mais servidores DNS (a lista está completa)</span><span class="sxs-lookup"><span data-stu-id="c168e-539">**NX_DNS_DUPLICATE_ENTRY** or **NX_NO_MORE_ENTRIES**: (0x17) No more DNS Servers Allowed (list is full)</span></span>
- <span data-ttu-id="c168e-540">**NX_DNS_PARAM_ERROR:**(0xA8) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="c168e-540">**NX_DNS_PARAM_ERROR**: (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="c168e-541">NX_PTR_ERROR: (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="c168e-541">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="c168e-542">NX_CALLER_ERROR: (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="c168e-542">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="c168e-543">NX_DNS_BAD_ADDRESS_ERROR: (0xA4) Entrada de endereço de servidor nulo</span><span class="sxs-lookup"><span data-stu-id="c168e-543">NX_DNS_BAD_ADDRESS_ERROR: (0xA4) Null server address input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c168e-544">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c168e-544">Allowed From</span></span>

<span data-ttu-id="c168e-545">Fios</span><span class="sxs-lookup"><span data-stu-id="c168e-545">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c168e-546">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c168e-546">Example</span></span>

```c
/* Add a DNS Server at IP address 202.2.2.13.  */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added.  */
```

## <a name="nx_dns_server_get"></a><span data-ttu-id="c168e-547">nx_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="c168e-547">nx_dns_server_get</span></span>

<span data-ttu-id="c168e-548">Devolva um Servidor DNS IPv4 da lista de clientes</span><span class="sxs-lookup"><span data-stu-id="c168e-548">Return an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="c168e-549">Prototype</span><span class="sxs-lookup"><span data-stu-id="c168e-549">Prototype</span></span>

```c
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                       ULONG *dns_server_address);
```

### <a name="description"></a><span data-ttu-id="c168e-550">Descrição</span><span class="sxs-lookup"><span data-stu-id="c168e-550">Description</span></span>

<span data-ttu-id="c168e-551">Este serviço devolve o endereço IPv4 DNS Server da lista de servidores no índice especificado.</span><span class="sxs-lookup"><span data-stu-id="c168e-551">This service returns the IPv4 DNS Server address from the server list at the specified index.</span></span> <span data-ttu-id="c168e-552">Note que o índice é baseado em zero.</span><span class="sxs-lookup"><span data-stu-id="c168e-552">Note that the index is zero based.</span></span> <span data-ttu-id="c168e-553">Se o índice de entrada exceder o tamanho da lista de Clientes DNS, é devolvido um erro.</span><span class="sxs-lookup"><span data-stu-id="c168e-553">If the input index exceeds the size of the DNS Client list, an error is returned.</span></span> <span data-ttu-id="c168e-554">O serviço *nx_dns_get_serverlist_size* pode ser chamado primeiro obter o número de servidores DNS na lista de Clientes.</span><span class="sxs-lookup"><span data-stu-id="c168e-554">The *nx_dns_get_serverlist_size* service may be called first obtain the number of DNS servers in the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c168e-555">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-555">Input Parameters</span></span>

- <span data-ttu-id="c168e-556">**dns_ptr**: Ponteiro para bloco de controlo DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-556">**dns_ptr**: Pointer to DNS control block</span></span>  
- <span data-ttu-id="c168e-557">**índice** na lista de servidores do CLIENTE DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-557">**index**: Index into DNS Client’s list of servers</span></span>
- <span data-ttu-id="c168e-558">**dns_server_address**: Ponteiro para endereço IP do Servidor DNS</span><span class="sxs-lookup"><span data-stu-id="c168e-558">**dns_server_address**: Pointer to IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="c168e-559">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c168e-559">Return Values</span></span>

- <span data-ttu-id="c168e-560">**NX_SUCCESS:**(0x00) Servidor de sucesso devolvido</span><span class="sxs-lookup"><span data-stu-id="c168e-560">**NX_SUCCESS**: (0x00) Successful server returned</span></span>
- <span data-ttu-id="c168e-561">**NX_DNS_SERVER_NOT_FOUND**: (0xA9) Índice aponta para slot vazio</span><span class="sxs-lookup"><span data-stu-id="c168e-561">**NX_DNS_SERVER_NOT_FOUND**: (0xA9) Index points to empty slot</span></span>
- <span data-ttu-id="c168e-562">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Índice aponta para endereço nulo</span><span class="sxs-lookup"><span data-stu-id="c168e-562">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Index points to Null address</span></span>
- <span data-ttu-id="c168e-563">**NX_DNS_PARAM_ERROR**: (0xA8) Índice excede o tamanho da lista</span><span class="sxs-lookup"><span data-stu-id="c168e-563">**NX_DNS_PARAM_ERROR**: (0xA8) Index exceeds size of list</span></span>
- <span data-ttu-id="c168e-564">NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-564">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="c168e-565">NX_CALLER_ERROR: (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="c168e-565">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c168e-566">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c168e-566">Allowed From</span></span>

<span data-ttu-id="c168e-567">Fios</span><span class="sxs-lookup"><span data-stu-id="c168e-567">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c168e-568">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c168e-568">Example</span></span>

```c
ULONG     my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list.  */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned.  */
```

## <a name="nx_dns_server_remove"></a><span data-ttu-id="c168e-569">nx_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="c168e-569">nx_dns_server_remove</span></span>

<span data-ttu-id="c168e-570">Remova um Servidor DNS IPv4 da lista de clientes</span><span class="sxs-lookup"><span data-stu-id="c168e-570">Remove an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="c168e-571">Prototype</span><span class="sxs-lookup"><span data-stu-id="c168e-571">Prototype</span></span>

```c
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="c168e-572">Descrição</span><span class="sxs-lookup"><span data-stu-id="c168e-572">Description</span></span>

<span data-ttu-id="c168e-573">Este serviço remove um Servidor DNS IPv4 da lista de Clientes.</span><span class="sxs-lookup"><span data-stu-id="c168e-573">This service removes an IPv4 DNS Server from the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c168e-574">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-574">Input Parameters</span></span>

- <span data-ttu-id="c168e-575">**dns_ptr**: Ponteiro para o bloco de controlo DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-575">**dns_ptr**: Pointer to DNS control block.</span></span>
- <span data-ttu-id="c168e-576">**server_address**: Endereço IP do DNS Server.</span><span class="sxs-lookup"><span data-stu-id="c168e-576">**server_address**: IP address of DNS Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="c168e-577">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c168e-577">Return Values</span></span>

- <span data-ttu-id="c168e-578">**NX_SUCCESS**: (0x00) DNS Server removido com sucesso</span><span class="sxs-lookup"><span data-stu-id="c168e-578">**NX_SUCCESS**: (0x00) DNS Server successfully removed</span></span>
- <span data-ttu-id="c168e-579">**NX_DNS_SERVER_NOT_FOUND**: (0xA9) Servidor não na lista de clientes</span><span class="sxs-lookup"><span data-stu-id="c168e-579">**NX_DNS_SERVER_NOT_FOUND**: (0xA9) Server not in Client list</span></span>
- <span data-ttu-id="c168e-580">**NX_DNS_BAD_ADDRESS_ERROR:**(0xA4) Entrada de endereço de servidor nulo</span><span class="sxs-lookup"><span data-stu-id="c168e-580">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Null server address input</span></span>
- <span data-ttu-id="c168e-581">NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-581">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="c168e-582">NX_CALLER_ERROR: (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="c168e-582">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c168e-583">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c168e-583">Allowed From</span></span>

<span data-ttu-id="c168e-584">Fios</span><span class="sxs-lookup"><span data-stu-id="c168e-584">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c168e-585">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c168e-585">Example</span></span>

```c
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nx_dns_server_remove_all"></a><span data-ttu-id="c168e-586">nx_dns_server_remove_all</span><span class="sxs-lookup"><span data-stu-id="c168e-586">nx_dns_server_remove_all</span></span>

<span data-ttu-id="c168e-587">Remova todos os Servidores DNS da lista de clientes</span><span class="sxs-lookup"><span data-stu-id="c168e-587">Remove all DNS Servers from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="c168e-588">Prototype</span><span class="sxs-lookup"><span data-stu-id="c168e-588">Prototype</span></span>

```c
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```

### <a name="description"></a><span data-ttu-id="c168e-589">Descrição</span><span class="sxs-lookup"><span data-stu-id="c168e-589">Description</span></span>

<span data-ttu-id="c168e-590">Este serviço remove todos os Servidores DNS da lista de Clientes.</span><span class="sxs-lookup"><span data-stu-id="c168e-590">This service removes all DNS Servers from the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c168e-591">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c168e-591">Input Parameters</span></span>

- <span data-ttu-id="c168e-592">**dns_ptr**: Ponteiro para o bloco de controlo DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-592">**dns_ptr**: Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c168e-593">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c168e-593">Return Values</span></span>

- <span data-ttu-id="c168e-594">**NX_SUCCESS**: (0x00) Servidores DNS removidos com sucesso</span><span class="sxs-lookup"><span data-stu-id="c168e-594">**NX_SUCCESS**: (0x00) DNS Servers successfully removed</span></span>
- <span data-ttu-id="c168e-595">**NX_DNS_ERROR**: (0xA0) Incapaz de obter proteção mutex</span><span class="sxs-lookup"><span data-stu-id="c168e-595">**NX_DNS_ERROR**: (0xA0) Unable to obtain protection mutex</span></span>
- <span data-ttu-id="c168e-596">NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS.</span><span class="sxs-lookup"><span data-stu-id="c168e-596">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="c168e-597">NX_CALLER_ERROR: (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="c168e-597">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c168e-598">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c168e-598">Allowed From</span></span>

<span data-ttu-id="c168e-599">Fios</span><span class="sxs-lookup"><span data-stu-id="c168e-599">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c168e-600">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c168e-600">Example</span></span>

```c

/* Remove all DNS Servers from the Client list.  */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed.  */
```