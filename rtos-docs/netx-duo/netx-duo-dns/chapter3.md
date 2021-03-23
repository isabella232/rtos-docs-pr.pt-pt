---
title: Capítulo 3 - Descrição dos Serviços de Clientes Azure RTOS NetX Duo DNS
description: Este capítulo contém uma descrição de todos os serviços DNS Azure RTOS NetX Duo (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9634adab3944c29f64d26dd688b5053dc1bd9bcb
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826017"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dns-client-services"></a><span data-ttu-id="f6716-103">Capítulo 3 - Descrição dos Serviços de Clientes Azure RTOS NetX Duo DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-103">Chapter 3 - Description of Azure RTOS NetX Duo DNS Client Services</span></span>

<span data-ttu-id="f6716-104">Este capítulo contém uma descrição de todos os serviços DNS Azure RTOS NetX (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="f6716-104">This chapter contains a description of all Azure RTOS NetX DNS services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="f6716-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="f6716-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="f6716-106">**nx_dns_authority_zone_start_get** *Procure o início de uma zona de autoridade associada ao nome de anfitrião especificado*</span><span class="sxs-lookup"><span data-stu-id="f6716-106">**nx_dns_authority_zone_start_get** *Look up the start of a zone of authority associated with the specified host name*</span></span>

- <span data-ttu-id="f6716-107">**nx_dns_cache_initialize** *Inicialize uma Cache DNS.*</span><span class="sxs-lookup"><span data-stu-id="f6716-107">**nx_dns_cache_initialize** *Initialize a DNS Cache.*</span></span>

- <span data-ttu-id="f6716-108">**nx_dns_cache_notify_clear** *Limpe a função de notificação completa da cache.*</span><span class="sxs-lookup"><span data-stu-id="f6716-108">**nx_dns_cache_notify_clear** *Clear the cache full notify function.*</span></span>

- <span data-ttu-id="f6716-109">**nx_dns_cache_notify_set** *Desemalte a função de notificação completa da cache.*</span><span class="sxs-lookup"><span data-stu-id="f6716-109">**nx_dns_cache_notify_set** *Set the cache full notify function.*</span></span>

- <span data-ttu-id="f6716-110">**nx_dns_cname_get** *Procure o nome de domínio canónico para o pseudónimo do nome de domínio de entrada*</span><span class="sxs-lookup"><span data-stu-id="f6716-110">**nx_dns_cname_get** *Look up the canonical domain name for the input domain name alias*</span></span>

- <span data-ttu-id="f6716-111">**nx_dns_create** *Criar uma instância de cliente DNS*</span><span class="sxs-lookup"><span data-stu-id="f6716-111">**nx_dns_create** *Create a DNS Client instance*</span></span>

- <span data-ttu-id="f6716-112">**nx_dns_delete Excluir** *uma instância do cliente DNS*</span><span class="sxs-lookup"><span data-stu-id="f6716-112">**nx_dns_delete** *Delete a DNS Client instance*</span></span>

- <span data-ttu-id="f6716-113">**nx_dns_domain_name_server_get** *Procure os servidores de nome autorizados para a zona de domínio de entrada*</span><span class="sxs-lookup"><span data-stu-id="f6716-113">**nx_dns_domain_name_server_get** *Look up the authoritative name servers for the input domain zone*</span></span>

- <span data-ttu-id="f6716-114">**nx_dns_domain_mail_exchange_get** *Procure a troca de correio associada ao nome de anfitrião especificado.*</span><span class="sxs-lookup"><span data-stu-id="f6716-114">**nx_dns_domain_mail_exchange_get** *Look up the mail exchange associated the specified host name.*</span></span>

- <span data-ttu-id="f6716-115">**nx_dns_domain_service_get** *Procure os serviços associados ao nome de anfitrião especificado*</span><span class="sxs-lookup"><span data-stu-id="f6716-115">**nx_dns_domain_service_get** *Look up the service(s) associated with the specified host name*</span></span>

- <span data-ttu-id="f6716-116">**nx_dns_get_serverlist_size** *Devolver o tamanho da lista de servidores do Cliente DNS*</span><span class="sxs-lookup"><span data-stu-id="f6716-116">**nx_dns_get_serverlist_size** *Return the size of the DNS Client server list*</span></span>

- <span data-ttu-id="f6716-117">**nx_dns_info_by_name_get** *Endereço IP de retorno, consulta de porta no nome do anfitrião de entrada*</span><span class="sxs-lookup"><span data-stu-id="f6716-117">**nx_dns_info_by_name_get** *Return IP address, port querying on input host name*</span></span>

- <span data-ttu-id="f6716-118">**nx_dns_ipv4_address_by_name_get** *Procure o endereço IPv4 a partir do nome de anfitrião especificado*</span><span class="sxs-lookup"><span data-stu-id="f6716-118">**nx_dns_ipv4_address_by_name_get** *Look up the IPv4 address from the specified host name*</span></span>

- <span data-ttu-id="f6716-119">**nxd_dns_ipv6_address_by_name_get** *Procure o endereço IPv6 a partir do nome de anfitrião especificado*</span><span class="sxs-lookup"><span data-stu-id="f6716-119">**nxd_dns_ipv6_address_by_name_get** *Look up the IPv6 address from the specified host name*</span></span>

- <span data-ttu-id="f6716-120">**nx_dns_host_by_address_get** *função de invólucro para nxd_dns_host_by_address_get procurar um nome de anfitrião a partir de um endereço IP especificado (suporta apenas endereços IPv4)*</span><span class="sxs-lookup"><span data-stu-id="f6716-120">**nx_dns_host_by_address_get** *Wrapper function for nxd_dns_host_by_address_get to look up a host name from a specified IP address (supports only IPv4 addresses)*</span></span>

- <span data-ttu-id="f6716-121">**nxd_dns_host_by_address_get** *Procure um endereço IP a partir do nome do anfitrião de entrada (suporta os endereços IPv4 e IPv6)*</span><span class="sxs-lookup"><span data-stu-id="f6716-121">**nxd_dns_host_by_address_get** *Look up an IP address from the input host name (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="f6716-122">**nx_dns_host_by_name_get** *função de invólucro para nxd_dns_host_by_address_get procurar um nome de anfitrião a partir do endereço especificado (suporta apenas endereços IPv4)*</span><span class="sxs-lookup"><span data-stu-id="f6716-122">**nx_dns_host_by_name_get** *Wrapper function for nxd_dns_host_by_address_get to look up a host name from the specified address (supports only IPv4 addresses)*</span></span>

- <span data-ttu-id="f6716-123">**nxd_dns_host_by_name_get** *Procure um endereço IP a partir do nome do anfitrião de entrada (suporta os endereços IPv4 e IPv6)*</span><span class="sxs-lookup"><span data-stu-id="f6716-123">**nxd_dns_host_by_name_get** *Look up an IP address from the input host name (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="f6716-124">**nx_dns_host_text_get** *Procure os dados de texto para o nome de domínio de entrada*</span><span class="sxs-lookup"><span data-stu-id="f6716-124">**nx_dns_host_text_get** *Look up the text data for the input domain name*</span></span>

- <span data-ttu-id="f6716-125">**nx_dns_packet_pool_set** *Definir a piscina de pacotes do cliente DNS*</span><span class="sxs-lookup"><span data-stu-id="f6716-125">**nx_dns_packet_pool_set** *Set the DNS Client packet pool*</span></span>

- <span data-ttu-id="f6716-126">**nx_dns_server_add** *função de invólucro para* nxd_dns_server_add adicionar um Servidor *DNS no endereço especificado na lista de Clientes (suporta apenas o IPv4)*</span><span class="sxs-lookup"><span data-stu-id="f6716-126">**nx_dns_server_add** *Wrapper function for* nxd_dns_server_add *to add a DNS Server at the specified address to the Client list (supports only IPv4)*</span></span>

- <span data-ttu-id="f6716-127">**nxd_dns_server_add** *Adicionar um Servidor DNS do endereço IP especificado à lista de servidores do Cliente (suporta os endereços IPv4 ou IPv6)*</span><span class="sxs-lookup"><span data-stu-id="f6716-127">**nxd_dns_server_add** *Add a DNS Server of the specified IP address to the Client server list (supports both IPv4 or IPv6 addresses)*</span></span>

- <span data-ttu-id="f6716-128">**nx_dns_server_get** *Devolver o Servidor DNS na lista de Clientes (suporta apenas endereços IPv4)*</span><span class="sxs-lookup"><span data-stu-id="f6716-128">**nx_dns_server_get** *Return the DNS Server in the Client list (supports only IPv4 addresses)*</span></span>

- <span data-ttu-id="f6716-129">**nxd_dns_server_get** *Devolver o Servidor DNS na lista de Clientes (suporta os endereços IPv4 e IPv6)*</span><span class="sxs-lookup"><span data-stu-id="f6716-129">**nxd_dns_server_get** *Return the DNS Server in the Client list (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="f6716-130">**nx_dns_server_remove** *função de invólucro para nxd_dns_server_remove remover um Servidor DNS da lista de clientes*</span><span class="sxs-lookup"><span data-stu-id="f6716-130">**nx_dns_server_remove** *Wrapper function for nxd_dns_server_remove to remove a DNS Server from the Client list*</span></span>

- <span data-ttu-id="f6716-131">**nxd_dns_server_remove** *Remover um Servidor DNS do endereço IP especificado da lista de Clientes (suporta os endereços IPv4 e IPv6)*</span><span class="sxs-lookup"><span data-stu-id="f6716-131">**nxd_dns_server_remove** *Remove a DNS Server of the specified IP address from the Client list (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="f6716-132">**nx_dns_server_remove_all** *Remover todos os Servidores DNS da lista de clientes*</span><span class="sxs-lookup"><span data-stu-id="f6716-132">**nx_dns_server_remove_all** *Remove all DNS Servers from the Client list*</span></span>

## <a name="nx_dns_authority_zone_start_get"></a><span data-ttu-id="f6716-133">nx_dns_authority_zone_start_get</span><span class="sxs-lookup"><span data-stu-id="f6716-133">nx_dns_authority_zone_start_get</span></span>

<span data-ttu-id="f6716-134">Procure o início da zona de autoridade para o anfitrião de entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-134">Look up the start of the zone of authority for the input host</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-135">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-135">Prototype</span></span>
```C
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,                                        
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="f6716-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-136">Description</span></span>

<span data-ttu-id="f6716-137">Se NX_DNS_ENABLE_EXTENDED_RR_TYPES for definido, este serviço envia uma consulta do tipo SOA com o nome de domínio especificado para obter o início da zona de autoridade para o nome de domínio de entrada.</span><span class="sxs-lookup"><span data-stu-id="f6716-137">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SOA with the specified domain name to obtain the start of the zone of authority for the input domain name.</span></span> <span data-ttu-id="f6716-138">O Cliente DNS copia os registos SOA devolvidos na resposta do DNS Server para o local de memória *record_buffer.*</span><span class="sxs-lookup"><span data-stu-id="f6716-138">The DNS Client copies the SOA record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

> [!NOTE]
> <span data-ttu-id="f6716-139">O *record_buffer* deve estar alinhado em 4 bytes para receber os dados.</span><span class="sxs-lookup"><span data-stu-id="f6716-139">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="f6716-140">No NetX Duo DNS Client, o tipo de registo SOA, NX_DNS_SOA_ENTRY, é guardado como sete parâmetros de byte 4, totalizando 28 bytes:</span><span class="sxs-lookup"><span data-stu-id="f6716-140">In NetX Duo DNS Client, the SOA record type, NX_DNS_SOA_ENTRY, is saved as seven 4 byte parameters, totaling 28 bytes:</span></span>

- <span data-ttu-id="f6716-141">**nx_dns_soa_host_mname_ptr** Ponteiro para a fonte primária de dados para esta zona.</span><span class="sxs-lookup"><span data-stu-id="f6716-141">**nx_dns_soa_host_mname_ptr** Pointer to primary source of data for this zone.</span></span>
- <span data-ttu-id="f6716-142">**nx_dns_soa_host_rname_ptr** Ponteiro para caixa de correio responsável por esta zona</span><span class="sxs-lookup"><span data-stu-id="f6716-142">**nx_dns_soa_host_rname_ptr** Pointer to mailbox responsible for this zone</span></span>
- <span data-ttu-id="f6716-143">**nx_dns_soa_serial** Número da versão da zona</span><span class="sxs-lookup"><span data-stu-id="f6716-143">**nx_dns_soa_serial** Zone version number</span></span>
- <span data-ttu-id="f6716-144">**nx_dns_soa_refresh** Intervalo de atualização</span><span class="sxs-lookup"><span data-stu-id="f6716-144">**nx_dns_soa_refresh** Refresh interval</span></span>
- <span data-ttu-id="f6716-145">**nx_dns_soa_retry** Intervalo entre as recaírias da consulta soa</span><span class="sxs-lookup"><span data-stu-id="f6716-145">**nx_dns_soa_retry** Interval between SOA query retries</span></span>
- <span data-ttu-id="f6716-146">**nx_dns_soa_expire** Duração do tempo quando o SOA expirar</span><span class="sxs-lookup"><span data-stu-id="f6716-146">**nx_dns_soa_expire** Time duration when SOA expires</span></span>
- <span data-ttu-id="f6716-147">**nx_dns_soa_minmum** Campo TTL mínimo em palavras de resposta DO ESTADO</span><span class="sxs-lookup"><span data-stu-id="f6716-147">**nx_dns_soa_minmum** Minimum TTL field in SOA hostname DNS reply messages</span></span>

<span data-ttu-id="f6716-148">O armazenamento de dois registos SOA é mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="f6716-148">The storage of a two SOA records is shown below.</span></span> <span data-ttu-id="f6716-149">Os registos SOA que contenham dados de comprimento fixo são introduzidos a partir da parte superior do tampão.</span><span class="sxs-lookup"><span data-stu-id="f6716-149">The SOA records containing fixed length data are entered starting at the top of the buffer.</span></span> <span data-ttu-id="f6716-150">Os ponteiros MNAME e RNAME apontam para os dados de comprimento variável (nomes hospedeiros) que são armazenados na parte inferior do tampão.</span><span class="sxs-lookup"><span data-stu-id="f6716-150">The pointers MNAME and RNAME point to the variable length data (host names) which are stored at the bottom of the buffer.</span></span> <span data-ttu-id="f6716-151">Os registos SOA adicionais são introduzidos após o primeiro registo ("registos SOA adicionais...") e os seus dados de comprimento variável são armazenados acima dos dados variáveis do comprimento da última entrada ("dados adicionais de comprimento variável SOA"):</span><span class="sxs-lookup"><span data-stu-id="f6716-151">Additional SOA records are entered after the first record (“additional SOA records…”) and their variable length data is stored above the last entry’s variable length data (“additional SOA variable length data”):</span></span>

![O armazenamento de dois registos SOA](media/image4.png)

<span data-ttu-id="f6716-153">Se a entrada *record_buffer* não conseguir conter todos os dados do SOA na resposta do servidor, o *record_buffer* detém o número de registos que caberão e devolve o número de registos no tampão.</span><span class="sxs-lookup"><span data-stu-id="f6716-153">If the input *record_buffer* cannot hold all the SOA data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="f6716-154">Com o número de registos SOA devolvidos em \**record_count,* a aplicação pode analisar os dados a partir de *record_buffer* e extrair o início das cordas de nome de anfitrião da autoridade da zona.</span><span class="sxs-lookup"><span data-stu-id="f6716-154">With the number of SOA records returned in \**record_count,* the application can parse the data from *record_buffer* and extract the start of zone authority host name strings.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-155">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-155">Input Parameters</span></span>

- <span data-ttu-id="f6716-156">**dns_ptr** Ponteiro para o Cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-156">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="f6716-157">**host_name** Ponteiro para o nome de anfitrião para obter dados soa para</span><span class="sxs-lookup"><span data-stu-id="f6716-157">**host_name** Pointer to host name to obtain SOA data for</span></span>
- <span data-ttu-id="f6716-158">**record_buffer** Ponteiro para a localização para extrair dados do SOA em</span><span class="sxs-lookup"><span data-stu-id="f6716-158">**record_buffer** Pointer to location to extract SOA data into</span></span>
- <span data-ttu-id="f6716-159">**buffer_size** Tamanho do tampão para reter dados do SOA</span><span class="sxs-lookup"><span data-stu-id="f6716-159">**buffer_size** Size of buffer to hold SOA data</span></span>
- <span data-ttu-id="f6716-160">**record_count** Ponteiro para o número de registos SOA recuperados</span><span class="sxs-lookup"><span data-stu-id="f6716-160">**record_count** Pointer to the number of SOA records retrieved</span></span>
- <span data-ttu-id="f6716-161">**wait_option** Aguarde a opção para receber a resposta do DNS Server</span><span class="sxs-lookup"><span data-stu-id="f6716-161">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-162">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-162">Return Values</span></span>

- <span data-ttu-id="f6716-163">**NX_SUCCESS** (0x00) obteve com sucesso dados do SOA</span><span class="sxs-lookup"><span data-stu-id="f6716-163">**NX_SUCCESS** (0x00) Successfully obtained SOA data</span></span>
- <span data-ttu-id="f6716-164">**NX_DNS_NO_SERVER** (0xA1) Lista de servidores de clientes está vazia</span><span class="sxs-lookup"><span data-stu-id="f6716-164">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="f6716-165">**NX_DNS_QUERY_FAILED** (0xA3) Nenhuma resposta de DNS válida recebida</span><span class="sxs-lookup"><span data-stu-id="f6716-165">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="f6716-166">NX_PTR_ERROR (0x07) Ponteiro IP inválido ou DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-166">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="f6716-167">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="f6716-167">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="f6716-168">NX_DNS_PARAM_ERROR (0xA8) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="f6716-168">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-169">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-169">Allowed From</span></span>

<span data-ttu-id="f6716-170">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-170">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6716-171">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6716-171">Example</span></span>
```C
UCHAR  record_buffer[50];
UINT   record_count;   
NX_DNS_SOA_ENTRY *nx_dns_soa_entry_ptr;

/* Request the start of authority zone(s) for the specified host. */
status =  nx_dns_authority_zone_start_get(&client_dns, (UCHAR *)"www.my_example.com",  
                                          record _buffer, sizeof(record_buffer), 
                                          &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
         error_counter++;
}
else 
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and SOA data 
       is returned in soa_buffer. */

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

[Output]
----------------------------------------------------
Test SOA: 
serial = 2012111212
refresh = 7200
retry = 1800
expire = 1209600
minmum = 300
host mname = ns1.www.my_example.com
host rname = dns-admin.www.my_example.com
```

## <a name="nx_dns_cache_initialize"></a><span data-ttu-id="f6716-172">nx_dns_cache_initialize</span><span class="sxs-lookup"><span data-stu-id="f6716-172">nx_dns_cache_initialize</span></span>

<span data-ttu-id="f6716-173">Inicializar a Cache DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-173">Initialize the DNS Cache</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-174">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-174">Prototype</span></span>
```C
UINT nx_dns_cache_initialize(NX_DNS *dns_ptr,
                            VOID *cache_ptr, UINT cache_size);
```

### <a name="description"></a><span data-ttu-id="f6716-175">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-175">Description</span></span>

<span data-ttu-id="f6716-176">Este serviço cria e inicializa uma Cache DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-176">This service creates and initializes a DNS Cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-177">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-177">Input Parameters</span></span>

- <span data-ttu-id="f6716-178">**dns_ptr** Ponteiro para o bloco de controlo DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-178">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="f6716-179">**cache_ptr** Ponteiro para a Cache DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-179">**cache_ptr** Pointer to DNS Cache.</span></span>
- <span data-ttu-id="f6716-180">**cache_size** Tamanho do DNS Cache, em bytes.</span><span class="sxs-lookup"><span data-stu-id="f6716-180">**cache_size** Size of DNS Cache, in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-181">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-181">Return Values</span></span>

- <span data-ttu-id="f6716-182">**NX_SUCCESS** (0x00) DNS Cache iniciais com sucesso</span><span class="sxs-lookup"><span data-stu-id="f6716-182">**NX_SUCCESS** (0x00) DNS Cache successfully initialized</span></span>
- <span data-ttu-id="f6716-183">NX_DNS_PARAM_ERROR (0xA8) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="f6716-183">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="f6716-184">NX_DNS_CACHE_ERROR (0xB7) Ponteiro cache inválido.</span><span class="sxs-lookup"><span data-stu-id="f6716-184">NX_DNS_CACHE_ERROR (0xB7) Invalid Cache pointer.</span></span>
- <span data-ttu-id="f6716-185">NX_PTR_ERROR (0x07) Ponteiro DNS inválido.</span><span class="sxs-lookup"><span data-stu-id="f6716-185">NX_PTR_ERROR (0x07) Invalid DNS pointer.</span></span> 
- <span data-ttu-id="f6716-186">NX_DNS_ERROR cache (0xA0) não está alinhada com 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="f6716-186">NX_DNS_ERROR (0xA0) Cache is not 4-byte aligned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-187">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-187">Allowed From</span></span>

<span data-ttu-id="f6716-188">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-188">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6716-189">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6716-189">Example</span></span>
```C
/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, &dns_cache, 2048);

/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a><span data-ttu-id="f6716-190">nx_dns_cache_notify_clear</span><span class="sxs-lookup"><span data-stu-id="f6716-190">nx_dns_cache_notify_clear</span></span>

<span data-ttu-id="f6716-191">Limpe a função de notificação completa da Cache DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-191">Clear the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-192">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-192">Prototype</span></span>
```C
UINT nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```

### <a name="description"></a><span data-ttu-id="f6716-193">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-193">Description</span></span>

<span data-ttu-id="f6716-194">Este serviço limpa a função de notificação completa da cache.</span><span class="sxs-lookup"><span data-stu-id="f6716-194">This service clears the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-195">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-195">Input Parameters</span></span>

- <span data-ttu-id="f6716-196">**dns_ptr** Ponteiro para o bloco de controlo DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-196">**dns_ptr** Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-197">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-197">Return Values</span></span>

- <span data-ttu-id="f6716-198">**cache DNS** NX_SUCCESS (0x00) notificam com sucesso</span><span class="sxs-lookup"><span data-stu-id="f6716-198">**NX_SUCCESS** (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="f6716-199">NX_DNS_PARAM_ERROR (0xA8) Entrada inválida sem ponte</span><span class="sxs-lookup"><span data-stu-id="f6716-199">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="f6716-200">NX_PTR_ERROR (0x07) Ponteiro DNS inválido.</span><span class="sxs-lookup"><span data-stu-id="f6716-200">NX_PTR_ERROR (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-201">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-201">Allowed From</span></span>

<span data-ttu-id="f6716-202">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-202">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6716-203">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6716-203">Example</span></span>
```C
/* Clear the DNS Cache full notify function. */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a><span data-ttu-id="f6716-204">nx_dns_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="f6716-204">nx_dns_cache_notify_set</span></span>

<span data-ttu-id="f6716-205">Desa estale a função de notificação completa da Cache DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-205">Set the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-206">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-206">Prototype</span></span>
```C
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr,
                            VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a><span data-ttu-id="f6716-207">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-207">Description</span></span>

<span data-ttu-id="f6716-208">Este serviço define a função de notificação completa da cache.</span><span class="sxs-lookup"><span data-stu-id="f6716-208">This service sets the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-209">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-209">Input Parameters</span></span>

- <span data-ttu-id="f6716-210">**dns_ptr** Ponteiro para o bloco de controlo DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-210">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="f6716-211">**cache_full_notify_cb** A função de retorno a invocar quando a cache ficar cheia.</span><span class="sxs-lookup"><span data-stu-id="f6716-211">**cache_full_notify_cb** The callback function to be invoked when cache become full.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-212">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-212">Return Values</span></span>

- <span data-ttu-id="f6716-213">**cache DNS** NX_SUCCESS (0x00) notificam com sucesso</span><span class="sxs-lookup"><span data-stu-id="f6716-213">**NX_SUCCESS** (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="f6716-214">NX_DNS_PARAM_ERROR (0xA8) Entrada inválida sem ponte</span><span class="sxs-lookup"><span data-stu-id="f6716-214">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="f6716-215">NX_PTR_ERROR (0x07) Ponteiro DNS inválido.</span><span class="sxs-lookup"><span data-stu-id="f6716-215">NX_PTR_ERROR (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-216">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-216">Allowed From</span></span>

<span data-ttu-id="f6716-217">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-217">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6716-218">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6716-218">Example</span></span>
```C
/* Set the DNS Cache full notify function. */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set. */
```

## <a name="nx_dns_cname_get"></a><span data-ttu-id="f6716-219">nx_dns_cname_get</span><span class="sxs-lookup"><span data-stu-id="f6716-219">nx_dns_cname_get</span></span>

<span data-ttu-id="f6716-220">Procure o nome canónico para o nome de anfitrião de entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-220">Look up the canonical name for the input hostname</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-221">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-221">Prototype</span></span>
```C
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                     UCHAR *record_buffer, UINT buffer_size, 
                     ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f6716-222">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-222">Description</span></span>

<span data-ttu-id="f6716-223">Se NX_DNS_ENABLE_EXTENDED_RR_TYPES for definida em *nxd_dns.h,* este serviço envia uma consulta do tipo CNAME com o nome de domínio especificado para obter o nome de domínio canónico.</span><span class="sxs-lookup"><span data-stu-id="f6716-223">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined in *nxd_dns.h*, this service sends a query of type CNAME with the specified domain name to obtain the canonical domain name.</span></span> <span data-ttu-id="f6716-224">O Cliente DNS copia a cadeia CNAME devolvida na resposta do DNS Server para o local de memória *record_buffer.*</span><span class="sxs-lookup"><span data-stu-id="f6716-224">The DNS Client copies the CNAME string returned in the DNS Server response into the *record_buffer* memory location.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-225">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-225">Input Parameters</span></span>

- <span data-ttu-id="f6716-226">**dns_ptr** Ponteiro para o Cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-226">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="f6716-227">**host_name** Ponteiro para o nome de anfitrião para obter dados CNAME para</span><span class="sxs-lookup"><span data-stu-id="f6716-227">**host_name** Pointer to host name to obtain CNAME data for</span></span>
- <span data-ttu-id="f6716-228">**record_buffer** Ponteiro para a localização para extrair dados do CNAME em</span><span class="sxs-lookup"><span data-stu-id="f6716-228">**record_buffer** Pointer to location to extract CNAME data into</span></span>
- <span data-ttu-id="f6716-229">**buffer_size** Tamanho do tampão para conter dados CNAME</span><span class="sxs-lookup"><span data-stu-id="f6716-229">**buffer_size** Size of buffer to hold CNAME data</span></span>
- <span data-ttu-id="f6716-230">**wait_option** Aguarde a opção para receber a resposta do DNS Server</span><span class="sxs-lookup"><span data-stu-id="f6716-230">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-231">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-231">Return Values</span></span>

- <span data-ttu-id="f6716-232">**NX_SUCCESS** (0x00) obteve com sucesso dados do CNAME</span><span class="sxs-lookup"><span data-stu-id="f6716-232">**NX_SUCCESS** (0x00) Successfully obtained CNAME data</span></span>
- <span data-ttu-id="f6716-233">**NX_DNS_NO_SERVER** (0xA1) Lista de servidores de clientes está vazia</span><span class="sxs-lookup"><span data-stu-id="f6716-233">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="f6716-234">**NX_DNS_QUERY_FAILED** (0xA3) Nenhuma resposta de DNS válida recebida</span><span class="sxs-lookup"><span data-stu-id="f6716-234">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="f6716-235">NX_PTR_ERROR (0x07) Ponteiro IP inválido ou DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-235">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="f6716-236">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="f6716-236">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="f6716-237">NX_DNS_PARAM_ERROR (0xA8) Entrada inválida sem ponte</span><span class="sxs-lookup"><span data-stu-id="f6716-237">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-238">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-238">Allowed From</span></span>

<span data-ttu-id="f6716-239">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-239">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6716-240">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6716-240">Example</span></span>
```C
CHAR            record _buffer[50];

/* Request the canonical name for the specified host. */
status =  nx_dns_cname_get(&client_dns, (UCHAR *)"www.my_example.com ", 
                                   record_buffer, sizeof(record_buffer), 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and 
   the canonical host name is returned in record_buffer. */

    printf("------------------------------------------------------\n");
    printf("Test CNAME: %s\n", record_buffer);
} 

[Output]
----------------------------------------------------
Test CNAME: my_example.com
```

##  <a name="nx_dns_create"></a><span data-ttu-id="f6716-241">nx_dns_create</span><span class="sxs-lookup"><span data-stu-id="f6716-241">nx_dns_create</span></span>

<span data-ttu-id="f6716-242">Criar uma instância de cliente DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-242">Create a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-243">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-243">Prototype</span></span>
```C
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```
### <a name="description"></a><span data-ttu-id="f6716-244">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-244">Description</span></span>

<span data-ttu-id="f6716-245">Este serviço cria uma instância do Cliente DNS para a instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="f6716-245">This service creates a DNS Client instance for the previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f6716-246">A aplicação deve garantir que a carga útil do pacote do pacote utilizado pelo Cliente DNS seja suficientemente grande para a mensagem máxima de 512 byte DNS, além dos cabeçalhos UDP, IP e Ethernet.</span><span class="sxs-lookup"><span data-stu-id="f6716-246">The application must ensure that the packet payload of the packet pool used by the DNS Client is large enough for the maximum 512 byte DNS message, plus UDP, IP and Ethernet headers.</span></span> <span data-ttu-id="f6716-247">Se o Cliente DNS criar a sua própria piscina de pacotes, isso é definido por NX_DNS_PACKET_PAYLOAD e NX_DNS_PACKET_POOL_SIZE.</span><span class="sxs-lookup"><span data-stu-id="f6716-247">If the DNS Client creates its own packet pool, this is defined by NX_DNS_PACKET_PAYLOAD and NX_DNS_PACKET_POOL_SIZE.</span></span>

<span data-ttu-id="f6716-248">Se a aplicação DO CLIENTE DNS preferir fornecer um conjunto de pacotes previamente criado, a carga útil para o IPv4 DNS Cliente deve ser de 512 bytes para o máximo DNS mais 20 bytes para o cabeçalho IP, 8 bytes para o cabeçalho UDP e 14 bytes para o cabeçalho Ethernet.</span><span class="sxs-lookup"><span data-stu-id="f6716-248">If the DNS Client application prefers to supply a previously created packet pool, the payload for IPv4 DNS Client should be 512 bytes for the maximum DNS plus 20 bytes for the IP header, 8 bytes for the UDP header and 14 bytes for the Ethernet header.</span></span> <span data-ttu-id="f6716-249">Para o IPv6, a única diferença é que o cabeçalho IP é de 40 bytes, pelo que o pacote precisa acomodar o cabeçalho IPv6 de 40 bytes.</span><span class="sxs-lookup"><span data-stu-id="f6716-249">For IPv6 the only difference is the IP header is 40 bytes, therefore the packet needs to accommodate the IPv6 header of 40 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-250">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-250">Input Parameters</span></span>

- <span data-ttu-id="f6716-251">**dns_ptr** Ponteiro para o Cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-251">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="f6716-252">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="f6716-252">**ip_ptr** Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="f6716-253">**domain_name** Ponteiro para nome de domínio para a instância DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-253">**domain_name** Pointer to domain name for DNS instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-254">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-254">Return Values</span></span>

- <span data-ttu-id="f6716-255">**NX_SUCCESS** (0x00) DNS de sucesso criam</span><span class="sxs-lookup"><span data-stu-id="f6716-255">**NX_SUCCESS** (0x00) Successful DNS create</span></span>
- <span data-ttu-id="f6716-256">**DNS NX_DNS_ERROR** (0xA0) criam erro</span><span class="sxs-lookup"><span data-stu-id="f6716-256">**NX_DNS_ERROR** (0xA0) DNS create error</span></span>
- <span data-ttu-id="f6716-257">NX_PTR_ERROR (0x07) Ponteiro IP inválido ou DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-257">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="f6716-258">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="f6716-258">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-259">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-259">Allowed From</span></span>

<span data-ttu-id="f6716-260">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-260">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6716-261">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6716-261">Example</span></span>
```C
/* Create a DNS Client instance. */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created. */
```

## <a name="nx_dns_delete"></a><span data-ttu-id="f6716-262">nx_dns_delete</span><span class="sxs-lookup"><span data-stu-id="f6716-262">nx_dns_delete</span></span>

<span data-ttu-id="f6716-263">Excluir uma instância do cliente DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-263">Delete a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-264">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-264">Prototype</span></span>
```C
UINT nx_dns_delete(NX_DNS *dns_ptr);
```
### <a name="description"></a><span data-ttu-id="f6716-265">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-265">Description</span></span>

<span data-ttu-id="f6716-266">Este serviço elimina uma instância do Cliente DNS previamente criada e liberta os seus recursos.</span><span class="sxs-lookup"><span data-stu-id="f6716-266">This service deletes a previously created DNS Client instance and frees up its resources.</span></span> 

> [!NOTE]
> <span data-ttu-id="f6716-267">Se NX_DNS_CLIENT_USER_CREATE_PACKET_POOL estiver definido e o Cliente DNS tiver sido atribuído a um pacote de pacotes definido pelo utilizador, cabe à aplicação eliminar o pacote de pacotes DNS Client se já não precisar.</span><span class="sxs-lookup"><span data-stu-id="f6716-267">If NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined and the DNS Client was assigned a user defined packet pool, it is up to the application to delete the DNS Client packet pool if it no longer needs it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-268">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-268">Input Parameters</span></span>

- <span data-ttu-id="f6716-269">**dns_ptr** Ponteiro para a instância do cliente DNS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="f6716-269">**dns_ptr** Pointer to previously created DNS Client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-270">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-270">Return Values</span></span>

- <span data-ttu-id="f6716-271">**NX_SUCCESS** (0x00) Cliente DNS bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="f6716-271">**NX_SUCCESS** (0x00) Successful DNS Client delete.</span></span>
- <span data-ttu-id="f6716-272">NX_PTR_ERROR (0x07) Ponteiro IP inválido ou DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-272">NX_PTR_ERROR (0x07) Invalid IP or DNS Client pointer.</span></span>
- <span data-ttu-id="f6716-273">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="f6716-273">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-274">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-274">Allowed From</span></span>

<span data-ttu-id="f6716-275">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-275">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6716-276">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6716-276">Example</span></span>
```C
/* Delete a DNS Client instance. */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted. */
```

## <a name="nx_dns_domain_name_server_get"></a><span data-ttu-id="f6716-277">nx_dns_domain_name_server_get</span><span class="sxs-lookup"><span data-stu-id="f6716-277">nx_dns_domain_name_server_get</span></span>

<span data-ttu-id="f6716-278">Procure os servidores de nome autorizados para a zona de domínio de entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-278">Look up the authoritative name servers for the input domain zone</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-279">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-279">Prototype</span></span>
```C
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f6716-280">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-280">Description</span></span>

<span data-ttu-id="f6716-281">Se NX_DNS_ENABLE_EXTENDED_RR_TYPES for definido, este serviço envia uma consulta do tipo NS com o nome de domínio especificado para obter os servidores de nome para o nome de domínio de entrada.</span><span class="sxs-lookup"><span data-stu-id="f6716-281">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type NS with the specified domain name to obtain the name servers for the input domain name.</span></span> <span data-ttu-id="f6716-282">O Cliente DNS copia os registos NS devolvidos na resposta do DNS Server para o local de memória *record_buffer.*</span><span class="sxs-lookup"><span data-stu-id="f6716-282">The DNS Client copies the NS record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

> [!NOTE]
> <span data-ttu-id="f6716-283">O *record_buffer* deve estar alinhado em 4 bytes para receber os dados.</span><span class="sxs-lookup"><span data-stu-id="f6716-283">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="f6716-284">No Cliente DNS NetX Duo o tipo de dados NS, NX_DNS_NS_ENTRY, é guardado como dois parâmetros de 4 byte:</span><span class="sxs-lookup"><span data-stu-id="f6716-284">In NetX Duo DNS Client the NS data type, NX_DNS_NS_ENTRY, is saved as two 4-byte parameters:</span></span>

- <span data-ttu-id="f6716-285">**nx_dns_ns_ipv4_address** Endereço IPv4 do servidor de nome</span><span class="sxs-lookup"><span data-stu-id="f6716-285">**nx_dns_ns_ipv4_address** Name server’s IPv4 address</span></span>
- <span data-ttu-id="f6716-286">**nx_dns_ns_hostname_ptr** Ponteiro para o nome de anfitrião do servidor de nome</span><span class="sxs-lookup"><span data-stu-id="f6716-286">**nx_dns_ns_hostname_ptr** Pointer to the name server’s hostname</span></span>

<span data-ttu-id="f6716-287">O tampão mostrado abaixo contém quatro registos NX_DNS_NS_ENTRY.</span><span class="sxs-lookup"><span data-stu-id="f6716-287">The buffer shown below contains four NX_DNS_NS_ENTRY records.</span></span> <span data-ttu-id="f6716-288">O ponteiro para o anfitrião de cadeia de nome em cada ponto de entrada para a cadeia de nome do anfitrião correspondente na metade inferior do tampão:</span><span class="sxs-lookup"><span data-stu-id="f6716-288">The pointer to host name string in each entry points to the corresponding host name string in the bottom half of the buffer:</span></span>

![Contém quatro registos NX_DNS_NS_ENTRY](media/image5.png)

<span data-ttu-id="f6716-290">Se a entrada *record_buffer* não conseguir conter todos os dados NS na resposta do servidor, o *record_buffer* detém o número de registos que caberão e devolve o número de registos no tampão.</span><span class="sxs-lookup"><span data-stu-id="f6716-290">If the input *record_buffer* cannot hold all the NS data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="f6716-291">Com o número de registos NS devolvidos em \**record_count,* a aplicação pode analisar o endereço IP e o nome de anfitrião de cada registo no *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="f6716-291">With the number of NS records returned in \**record_count,* the application can parse the IP address and host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-292">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-292">Input Parameters</span></span>

- <span data-ttu-id="f6716-293">**dns_ptr** Ponteiro para o Cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-293">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="f6716-294">**host_name** Ponteiro para o nome de anfitrião para obter dados de NS para</span><span class="sxs-lookup"><span data-stu-id="f6716-294">**host_name** Pointer to host name to obtain NS data for</span></span>
- <span data-ttu-id="f6716-295">**record_buffer** Ponteiro para a localização para extrair dados do SNS em</span><span class="sxs-lookup"><span data-stu-id="f6716-295">**record_buffer** Pointer to location to extract NS data into</span></span>
- <span data-ttu-id="f6716-296">**buffer_size** Tamanho do tampão para conter dados NS</span><span class="sxs-lookup"><span data-stu-id="f6716-296">**buffer_size** Size of buffer to hold NS data</span></span>
- <span data-ttu-id="f6716-297">**record_count** Ponteiro para o número de registos NS recuperados</span><span class="sxs-lookup"><span data-stu-id="f6716-297">**record_count** Pointer to the number of NS records retrieved</span></span>
- <span data-ttu-id="f6716-298">**wait_option** Aguarde a opção para receber a resposta do DNS Server</span><span class="sxs-lookup"><span data-stu-id="f6716-298">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-299">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-299">Return Values</span></span>

- <span data-ttu-id="f6716-300">**NX_SUCCESS** (0x00) obteve com sucesso dados de NS</span><span class="sxs-lookup"><span data-stu-id="f6716-300">**NX_SUCCESS** (0x00) Successfully obtained NS data</span></span>
- <span data-ttu-id="f6716-301">**NX_DNS_NO_SERVER** (0xA1) Lista de servidores de clientes está vazia</span><span class="sxs-lookup"><span data-stu-id="f6716-301">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="f6716-302">**NX_DNS_QUERY_FAILED** (0xA3) Nenhuma resposta de DNS válida recebida</span><span class="sxs-lookup"><span data-stu-id="f6716-302">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="f6716-303">NX_DNS_PARAM_ERROR (0xA8) Entrada inválida sem ponte</span><span class="sxs-lookup"><span data-stu-id="f6716-303">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="f6716-304">NX_PTR_ERROR (0x07) Ponteiro IP inválido ou DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-304">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="f6716-305">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="f6716-305">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-306">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-306">Allowed From</span></span>

<span data-ttu-id="f6716-307">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-307">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6716-308">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6716-308">Example</span></span>
```C
#define RECORD_COUNT    10

ULONG  record_buffer[50];
UINT   record_count;          
NX_DNS_NS_ENTRY  *nx_dns_ns_entry_ptr[RECORD_COUNT];

/* Request the name server(s) for the specified host. */
status =  nx_dns_domain_name_server_get(&client_dns, (UCHAR *)" www.my_example.com ",  
                                        record_buffer, sizeof(record_buffer),  
                                        &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and NS data
   is returned in record_buffer. */

    printf("------------------------------------------------------\n");
    printf("Test NS: ");
    printf("record_count = %d \n", record_count);      

    /* Get the name server. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_ns_entry_ptr[i] = (NX_DNS_NS_ENTRY *)
                               (record_buffer + i * sizeof(NX_DNS_NS_ENTRY)); 

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

[Output]
------------------------------------------------------
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

## <a name="nx_dns_domain_mail_exchange_get"></a><span data-ttu-id="f6716-309">nx_dns_domain_mail_exchange_get</span><span class="sxs-lookup"><span data-stu-id="f6716-309">nx_dns_domain_mail_exchange_get</span></span>

<span data-ttu-id="f6716-310">Procure a troca de correio para o nome do anfitrião de entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-310">Look up the mail exchange(s) for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-311">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-311">Prototype</span></span>
```C
UINT nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                     VOID *record_buffer,                                        
                                     UINT buffer_size, 
                                     UINT *record_count, 
                                     ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f6716-312">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-312">Description</span></span>

<span data-ttu-id="f6716-313">Se NX_DNS_ENABLE_EXTENDED_RR_TYPES for definido, este serviço envia uma consulta do tipo MX com o nome de domínio especificado para obter a troca de correio para o nome de domínio de entrada.</span><span class="sxs-lookup"><span data-stu-id="f6716-313">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type MX with the specified domain name to obtain the mail exchange for the input domain name.</span></span> <span data-ttu-id="f6716-314">O Cliente DNS copia os registos(s) MX devolvidos na resposta do DNS Server para o local de memória *record_buffer.*</span><span class="sxs-lookup"><span data-stu-id="f6716-314">The DNS Client copies the MX record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="f6716-315">O *record_buffer* deve estar alinhado em 4 bytes para receber os dados.</span><span class="sxs-lookup"><span data-stu-id="f6716-315">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="f6716-316">No NetX Duo DNS Client, o tipo de registo de troca de correio, NX_DNS_MAIL_EXCHANGE_ENTRY, é guardado como quatro parâmetros, totalizando 12 bytes:</span><span class="sxs-lookup"><span data-stu-id="f6716-316">In NetX Duo DNS Client, the mail exchange record type, NX_DNS_MAIL_EXCHANGE_ENTRY, is saved as four parameters, totaling 12 bytes:</span></span>

- <span data-ttu-id="f6716-317">**nx_dns_mx_ipv4_address** Endereço IPv4 de troca de correio 4 bytes</span><span class="sxs-lookup"><span data-stu-id="f6716-317">**nx_dns_mx_ipv4_address** Mail exchange IPv4 address 4 bytes</span></span>
- <span data-ttu-id="f6716-318">**nx_dns_mx_preference** Preferência 2 bytes</span><span class="sxs-lookup"><span data-stu-id="f6716-318">**nx_dns_mx_preference** Preference 2 bytes</span></span>
- <span data-ttu-id="f6716-319">**nx_dns_mx_reserved0** Reservado 2 bytes</span><span class="sxs-lookup"><span data-stu-id="f6716-319">**nx_dns_mx_reserved0** Reserved 2 bytes</span></span>
- <span data-ttu-id="f6716-320">**nx_dns_mx_hostname_ptr** Ponteiro para troca de correio servidor nome de anfitrião 4 bytes</span><span class="sxs-lookup"><span data-stu-id="f6716-320">**nx_dns_mx_hostname_ptr** Pointer to mail exchange server host name 4 bytes</span></span>

<span data-ttu-id="f6716-321">Um tampão contendo quatro registos MX é mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="f6716-321">A buffer containing four MX records is shown below.</span></span> <span data-ttu-id="f6716-322">Cada registo contém os dados de comprimento fixo da lista acima.</span><span class="sxs-lookup"><span data-stu-id="f6716-322">Each record contains the fixed length data from the list above.</span></span> <span data-ttu-id="f6716-323">O ponteiro para o nome do anfitrião do servidor de troca de correio aponta para o nome de anfitrião correspondente na parte inferior do tampão.</span><span class="sxs-lookup"><span data-stu-id="f6716-323">The pointer to the mail exchange server host name points to the corresponding host name at the bottom of the buffer.</span></span>

![Um tampão contendo quatro registos MX](media/image6.png)

<span data-ttu-id="f6716-325">Se a entrada *record_buffer* não conseguir conter todos os dados MX na resposta do servidor, o *record_buffer* detém o número de registos que caberão e devolve o número de registos no tampão.</span><span class="sxs-lookup"><span data-stu-id="f6716-325">If the input *record_buffer* cannot hold all the MX data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="f6716-326">Com o número de registos MX devolvidos em \**record_count,* a aplicação pode analisar os parâmetros MX, incluindo o nome do anfitrião de cada registo no *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="f6716-326">With the number of MX records returned in \**record_count,* the application can parse the MX parameters, including the mail host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-327">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-327">Input Parameters</span></span>

- <span data-ttu-id="f6716-328">**dns_ptr** Ponteiro para o Cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-328">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="f6716-329">**host_name** Ponteiro para o nome de anfitrião para obter dados MX para</span><span class="sxs-lookup"><span data-stu-id="f6716-329">**host_name** Pointer to host name to obtain MX data for</span></span>
- <span data-ttu-id="f6716-330">**record_buffer** Ponteiro para a localização para extrair dados de MX em</span><span class="sxs-lookup"><span data-stu-id="f6716-330">**record_buffer** Pointer to location to extract MX data into</span></span>
- <span data-ttu-id="f6716-331">**buffer_size** Tamanho do tampão para conter dados MX</span><span class="sxs-lookup"><span data-stu-id="f6716-331">**buffer_size** Size of buffer to hold MX data</span></span>
- <span data-ttu-id="f6716-332">**record_count** Ponteiro para o número de registos MX recuperados</span><span class="sxs-lookup"><span data-stu-id="f6716-332">**record_count** Pointer to the number of MX records retrieved</span></span>
- <span data-ttu-id="f6716-333">**wait_option** Aguarde a opção para receber a resposta do DNS Server</span><span class="sxs-lookup"><span data-stu-id="f6716-333">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-334">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-334">Return Values</span></span>

- <span data-ttu-id="f6716-335">**NX_SUCCESS** (0x00) obteve com sucesso dados de MX</span><span class="sxs-lookup"><span data-stu-id="f6716-335">**NX_SUCCESS** (0x00) Successfully obtained MX data</span></span>
- <span data-ttu-id="f6716-336">**NX_DNS_NO_SERVER** (0xA1) Lista de servidores de clientes está vazia</span><span class="sxs-lookup"><span data-stu-id="f6716-336">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="f6716-337">**NX_DNS_QUERY_FAILED** (0xA3) Nenhuma resposta de DNS válida recebida</span><span class="sxs-lookup"><span data-stu-id="f6716-337">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="f6716-338">NX_DNS_PARAM_ERROR (0xA8) Entrada inválida sem ponte</span><span class="sxs-lookup"><span data-stu-id="f6716-338">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="f6716-339">NX_PTR_ERROR (0x07) Ponteiro IP inválido ou DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-339">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="f6716-340">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="f6716-340">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-341">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-341">Allowed From</span></span>

<span data-ttu-id="f6716-342">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-342">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6716-343">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6716-343">Example</span></span>
```C
#define MAX_RECORD_COUNT 10

ULONG  record_buffer[50];
UINT   record_count;  
NX_DNS_MX_ENTRY  *nx_dns_mx_entry_ptr[MAX_RECORD_COUNT];        

/* Request the mail exchange data for the specified host. */
status =  nx_dns_domain_mail_exchange_get(&client_dns, (UCHAR *)" www.my_example.com ", 
                                          record_buffer, sizeof(record_buffer),   
                                          &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}
       
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and MX
   data is returned in record_buffer. */

    printf("------------------------------------------------------\n");
    printf("Test MX: ");
    printf("record_count = %d \n", record_count);      


    /* Get the mail exchange. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_mx_entry_ptr[i] = (NX_DNS_MX_ENTRY *)
               (record_buffer + i * sizeof(NX_DNS_MX_ENTRY));   

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 24,
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 16 & 0xFF,                   
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 8 & 0xFF,
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address & 0xFF);

        printf("preference = %d \n ", 
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_preference);

        if(nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr)
            printf("hostname = %s\n", 
                    nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr);
        else
            printf("hostname is not set\n");
}


[Output]

-----------------------------------------------------
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

## <a name="nx_dns_domain_service_get"></a><span data-ttu-id="f6716-344">nx_dns_domain_service_get</span><span class="sxs-lookup"><span data-stu-id="f6716-344">nx_dns_domain_service_get</span></span>

<span data-ttu-id="f6716-345">Procure o(s) serviço(s) fornecido pelo nome do anfitrião de entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-345">Look up the service(s) provided by the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-346">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-346">Prototype</span></span>
```C
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f6716-347">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-347">Description</span></span>

<span data-ttu-id="f6716-348">Se NX_DNS_ENABLE_EXTENDED_RR_TYPES for definido, este serviço envia uma consulta do tipo SRV com o nome de domínio especificado para procurar o(s) serviço(s) e o número de porta associado ao domínio especificado.</span><span class="sxs-lookup"><span data-stu-id="f6716-348">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SRV with the specified domain name to look up the service(s) and their port number associated with the specified domain.</span></span> <span data-ttu-id="f6716-349">O Cliente DNS copia os registos SRV devolvidos na resposta do DNS Server para o local de memória *record_buffer.*</span><span class="sxs-lookup"><span data-stu-id="f6716-349">The DNS Client copies the SRV record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="f6716-350">O *record_buffer* deve estar alinhado em 4 bytes para receber os dados.</span><span class="sxs-lookup"><span data-stu-id="f6716-350">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="f6716-351">No NetX Duo DNS Client, o tipo de registo de serviço, NX_DNS_SRV_ ENTRADA, é guardado como seis parâmetros, totalizando 16 bytes.</span><span class="sxs-lookup"><span data-stu-id="f6716-351">In NetX Duo DNS Client, the service record type, NX_DNS_SRV_ ENTRY, is saved as six parameters, totaling 16 bytes.</span></span> <span data-ttu-id="f6716-352">Isto permite que os dados SRV de comprimento variável sejam armazenados de forma eficiente na memória:</span><span class="sxs-lookup"><span data-stu-id="f6716-352">This enables variable length SRV data to be stored in a memory efficient manner:</span></span>

- <span data-ttu-id="f6716-353">**Endereço IPv4 do servidor** nx_dns_srv_ipv4_address 4 bytes</span><span class="sxs-lookup"><span data-stu-id="f6716-353">**Server IPv4 address** nx_dns_srv_ipv4_address 4 bytes</span></span>
- <span data-ttu-id="f6716-354">**Prioridade do servidor** nx_dns_srv_priority 2 bytes</span><span class="sxs-lookup"><span data-stu-id="f6716-354">**Server priority** nx_dns_srv_priority 2 bytes</span></span>
- <span data-ttu-id="f6716-355">**Peso do servidor** nx_dns_srv_weight 2 bytes</span><span class="sxs-lookup"><span data-stu-id="f6716-355">**Server weight** nx_dns_srv_weight 2 bytes</span></span>
- <span data-ttu-id="f6716-356">**Número da porta de** serviço nx_dns_srv_port_number 2 bytes</span><span class="sxs-lookup"><span data-stu-id="f6716-356">**Service port number** nx_dns_srv_port_number 2 bytes</span></span>
- <span data-ttu-id="f6716-357">**Reservado para alinhamento de 4 bytes** nx_dns_srv_reserved0 2 bytes</span><span class="sxs-lookup"><span data-stu-id="f6716-357">**Reserved for 4-byte alignment** nx_dns_srv_reserved0 2 bytes</span></span>
- <span data-ttu-id="f6716-358">**Ponteiro para o nome do anfitrião do servidor** \*nx_dns_srv_hostname_ptr 4 bytes</span><span class="sxs-lookup"><span data-stu-id="f6716-358">**Pointer to server host name** \*nx_dns_srv_hostname_ptr 4 bytes</span></span>

<span data-ttu-id="f6716-359">Quatro registos SRV são armazenados no tampão fornecido.</span><span class="sxs-lookup"><span data-stu-id="f6716-359">Four SRV records are stored in the supplied buffer.</span></span> <span data-ttu-id="f6716-360">Cada NX_DNS_SRV_ENTRY registo contém um ponteiro, *nx_dns_srv_hostname_ptr,* que aponta para a cadeia de nome do anfitrião correspondente na parte inferior do tampão de gravação:</span><span class="sxs-lookup"><span data-stu-id="f6716-360">Each NX_DNS_SRV_ENTRY record contains a pointer, *nx_dns_srv_hostname_ptr*, that points to the corresponding host name string in the bottom of the record buffer:</span></span>

![Quatro discos SRV](media/image7.png)

<span data-ttu-id="f6716-362">Se a entrada *record_buffer* não conseguir conter todos os dados SRV na resposta do servidor, o *record_buffer* detém o número de registos que caberão e devolve o número de registos no tampão.</span><span class="sxs-lookup"><span data-stu-id="f6716-362">If the input *record_buffer* cannot hold all the SRV data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="f6716-363">Com o número de registos SRV devolvidos em \**record_count,* a aplicação pode analisar os parâmetros SRV, incluindo o nome do anfitrião do servidor de cada registo no *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="f6716-363">With the number of SRV records returned in \**record_count,* the application can parse the SRV parameters, including the server host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-364">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-364">Input Parameters</span></span>

- <span data-ttu-id="f6716-365">**dns_ptr** Ponteiro para o Cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-365">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="f6716-366">**host_name** Ponteiro para o nome de anfitrião para obter dados SRV para</span><span class="sxs-lookup"><span data-stu-id="f6716-366">**host_name** Pointer to host name to obtain SRV data for</span></span>
- <span data-ttu-id="f6716-367">**record_buffer** Ponteiro para a localização para extrair dados DEV em</span><span class="sxs-lookup"><span data-stu-id="f6716-367">**record_buffer** Pointer to location to extract SRV data into</span></span>
- <span data-ttu-id="f6716-368">**buffer_size** Tamanho do tampão para conter dados SRV</span><span class="sxs-lookup"><span data-stu-id="f6716-368">**buffer_size** Size of buffer to hold SRV data</span></span>
- <span data-ttu-id="f6716-369">**record_count** Ponteiro para o número de registos SRV recuperados</span><span class="sxs-lookup"><span data-stu-id="f6716-369">**record_count** Pointer to the number of SRV records retrieved</span></span>
- <span data-ttu-id="f6716-370">**wait_option** Aguarde a opção para receber a resposta do DNS Server</span><span class="sxs-lookup"><span data-stu-id="f6716-370">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-371">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-371">Return Values</span></span>

- <span data-ttu-id="f6716-372">**NX_SUCCESS** (0x00) obteve com sucesso dados de SRV</span><span class="sxs-lookup"><span data-stu-id="f6716-372">**NX_SUCCESS** (0x00) Successfully obtained SRV data</span></span>
- <span data-ttu-id="f6716-373">**NX_DNS_NO_SERVER** (0xA1) Lista de servidores de clientes está vazia</span><span class="sxs-lookup"><span data-stu-id="f6716-373">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="f6716-374">**NX_DNS_QUERY_FAILED** (0xA3) Nenhuma resposta de DNS válida recebida</span><span class="sxs-lookup"><span data-stu-id="f6716-374">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="f6716-375">NX_DNS_PARAM_ERROR (0xA8) Parâmetro inválido sem ponte.</span><span class="sxs-lookup"><span data-stu-id="f6716-375">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer parameter.</span></span>
- <span data-ttu-id="f6716-376">NX_PTR_ERROR (0x07) Ponteiro IP inválido ou DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-376">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="f6716-377">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="f6716-377">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-378">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-378">Allowed From</span></span>

<span data-ttu-id="f6716-379">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-379">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6716-380">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6716-380">Example</span></span>
```C
#define MAX_RECORD_COUNT  10

UCHAR  record_buffer[50];
UINT   record_count;          
NX_DNS_SRV_ENTRY *nx_dns_srv_entry_ptr[MAX_RECORD_COUNT];

/* Request the service(s) provided by the specified host. */
status =  nx_dns_domain_service_get(&client_dns, (UCHAR *)"www.my_example.com ", 
                                    record_buffer, sizeof(record_buffer), 
                                    &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and SRV data
       is returned in record_buffer. */

        printf("------------------------------------------------------\n");
        printf("Test SRV: ");
        printf("record_count = %d \n", record_count);      

           
        /* Get the location of services. */
        for(i =0; i< record_count; i++)
        {
            nx_dns_srv_entry_ptr[i] = (NX_DNS_SRV_ENTRY *)
                                    (record_buffer + i * sizeof(NX_DNS_SRV_ENTRY)); 

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

[Output]
----------------------------------------------------
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

## <a name="nx_dns_get_serverlist_size"></a><span data-ttu-id="f6716-381">nx_dns_get_serverlist_size</span><span class="sxs-lookup"><span data-stu-id="f6716-381">nx_dns_get_serverlist_size</span></span>

<span data-ttu-id="f6716-382">Devolva o tamanho da lista de servidores do cliente DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-382">Return the size of the DNS Client’s Server list</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-383">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-383">Prototype</span></span>
```C
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```
### <a name="description"></a><span data-ttu-id="f6716-384">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-384">Description</span></span>

<span data-ttu-id="f6716-385">Este serviço devolve o número de Servidores DNS válidos (tanto IPv4 como IPv6) na lista de Clientes.</span><span class="sxs-lookup"><span data-stu-id="f6716-385">This service returns the number of valid DNS Servers (both IPv4 and IPv6) in the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-386">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-386">Input Parameters</span></span>

- <span data-ttu-id="f6716-387">**dns_ptr** Ponteiro para bloco de controlo DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-387">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="f6716-388">**tamanho** Devolve o número de servidores na lista</span><span class="sxs-lookup"><span data-stu-id="f6716-388">**size** Returns the number of servers in the list</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-389">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-389">Return Values</span></span>

- <span data-ttu-id="f6716-390">**NX_SUCCESS** (0x00) DNS Server tamanho da lista de servidor devolvido com sucesso</span><span class="sxs-lookup"><span data-stu-id="f6716-390">**NX_SUCCESS** (0x00) DNS Server list size successfully returned</span></span>
- <span data-ttu-id="f6716-391">NX_PTR_ERROR (0x07) Ponteiro IP inválido ou DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-391">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="f6716-392">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="f6716-392">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-393">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-393">Allowed From</span></span>

<span data-ttu-id="f6716-394">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-394">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6716-395">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6716-395">Example</span></span>
```C
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list. */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned. */
```

## <a name="nx_dns_info_by_name_get"></a><span data-ttu-id="f6716-396">nx_dns_info_by_name_get</span><span class="sxs-lookup"><span data-stu-id="f6716-396">nx_dns_info_by_name_get</span></span>

<span data-ttu-id="f6716-397">Endereço IP de devolução e porta do servidor DNS pelo nome de anfitrião</span><span class="sxs-lookup"><span data-stu-id="f6716-397">Return ip address and port of DNS server by host name</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-398">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-398">Prototype</span></span>
```C
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f6716-399">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-399">Description</span></span>

<span data-ttu-id="f6716-400">Este serviço devolve o IP do Servidor e a porta (registo de serviço) com base no nome do anfitrião de entrada por consulta DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-400">This service returns the Server IP and port (service record) based on the input host name by DNS query.</span></span> <span data-ttu-id="f6716-401">Se não for encontrado um registo de serviço, esta rotina devolve um endereço IP zero no ponteiro do endereço de entrada e um estado de erro não zero volta a sinalizar um erro.</span><span class="sxs-lookup"><span data-stu-id="f6716-401">If a service record is not found, this routine returns a zero IP address in the input address pointer and a non-zero error status return to signal an error.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-402">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-402">Input Parameters</span></span>

- <span data-ttu-id="f6716-403">**dns_ptr** Ponteiro para bloco de controlo DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-403">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="f6716-404">**host_name** Ponteiro para o tampão de nome anfitrião</span><span class="sxs-lookup"><span data-stu-id="f6716-404">**host_name** Pointer to host name buffer</span></span>
- <span data-ttu-id="f6716-405">**host_address_ptr** Ponteiro para endereçar para devolver</span><span class="sxs-lookup"><span data-stu-id="f6716-405">**host_address_ptr** Pointer to address to return</span></span>
- <span data-ttu-id="f6716-406">**host_port_ptr** Ponteiro para o porto para regressar</span><span class="sxs-lookup"><span data-stu-id="f6716-406">**host_port_ptr** Pointer to port to return</span></span>
- <span data-ttu-id="f6716-407">**wait_option** Opção de espera para a resposta dns</span><span class="sxs-lookup"><span data-stu-id="f6716-407">**wait_option** Wait option for the DNS response</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-408">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-408">Return Values</span></span>

- <span data-ttu-id="f6716-409">**NX_SUCCESS** (0x00) Registo do DNS Server devolvido com sucesso</span><span class="sxs-lookup"><span data-stu-id="f6716-409">**NX_SUCCESS** (0x00) DNS Server record successfully returned</span></span>
- <span data-ttu-id="f6716-410">**NX_DNS_NO_SERVER** (0xA1) Nenhum Servidor DNS registado com o Cliente para enviar consulta no nome anfitrião</span><span class="sxs-lookup"><span data-stu-id="f6716-410">**NX_DNS_NO_SERVER** (0xA1) No DNS Server registered with Client to send query on hostname</span></span>
- <span data-ttu-id="f6716-411">**NX_DNS_QUERY_FAILED** (0xA3) consulta de DNS falhou; não há resposta de nenhum servidor DNS na lista de Clientes ou nenhum registo de serviço está disponível para o nome de anfitrião de entrada.</span><span class="sxs-lookup"><span data-stu-id="f6716-411">**NX_DNS_QUERY_FAILED** (0xA3) DNS query failed; no response from any DNS servers in Client list or no service record is available for the input hostname.</span></span>
- <span data-ttu-id="f6716-412">NX_PTR_ERROR (0x07) Ponteiro IP inválido ou DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-412">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="f6716-413">NX_CALLER_ERROR (0x11) Inválido</span><span class="sxs-lookup"><span data-stu-id="f6716-413">NX_CALLER_ERROR (0x11) Invalid caller</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-414">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-414">Allowed From</span></span>

<span data-ttu-id="f6716-415">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-415">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6716-416">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6716-416">Example</span></span>
```C
ULONG ip_address
USHORT port;

/* Attempt to resolve the IP address and ports for this host name. */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned. */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a><span data-ttu-id="f6716-417">nx_dns_ipv4_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="f6716-417">nx_dns_ipv4_address_by_name_get</span></span>

<span data-ttu-id="f6716-418">Procure o endereço IPv4 para o nome do anfitrião de entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-418">Look up the IPv4 address for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-419">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-419">Prototype</span></span>
```C
UINT nx_ dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f6716-420">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-420">Description</span></span>

<span data-ttu-id="f6716-421">Este serviço envia uma consulta do tipo A com o nome de anfitrião especificado para obter os endereços IP para o nome do anfitrião de entrada.</span><span class="sxs-lookup"><span data-stu-id="f6716-421">This service sends a query of Type A with the specified host name to obtain the IP addresses for the input host name.</span></span> <span data-ttu-id="f6716-422">O Cliente DNS copia o endereço IPv4 a partir dos registos A devolvidos na resposta do DNS Server para o local de memória *record_buffer.*</span><span class="sxs-lookup"><span data-stu-id="f6716-422">The DNS Client copies the IPv4 address from the A record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

> [!NOTE]
> <span data-ttu-id="f6716-423">O *record_buffer* deve estar alinhado em 4 bytes para receber os dados.</span><span class="sxs-lookup"><span data-stu-id="f6716-423">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="f6716-424">Vários endereços IPv4 são armazenados no tampão alinhado de 4 byte, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="f6716-424">Multiple IPv4 addresses are stored in the 4-byte aligned buffer as shown below:</span></span>

![tampão alinhado de endereço múltiplo 4-byte](media/image8.png)

<span data-ttu-id="f6716-426">Se o tampão fornecido não conseguir conter todos os dados do endereço IP, os restantes registos A não são armazenados em *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="f6716-426">If the supplied buffer cannot hold all the IP address data, the remaining A records are not stored in *record_buffer*.</span></span> <span data-ttu-id="f6716-427">Isto permite que a aplicação recupere um, alguns ou todos os dados de endereço IP disponíveis na resposta do servidor.</span><span class="sxs-lookup"><span data-stu-id="f6716-427">This enables the application to retrieve one, some or all of the available IP address data in the server reply.</span></span>

<span data-ttu-id="f6716-428">Com o número de registos A devolvidos \**record_count* a aplicação pode analisar os dados de endereço IPv4 do *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="f6716-428">With the number of A records returned in \**record_count* the application can parse the IPv4 address data from the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-429">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-429">Input Parameters</span></span>

- <span data-ttu-id="f6716-430">**dns_ptr** Ponteiro para o Cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-430">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="f6716-431">**host_name_ptr** Ponteiro para o nome de anfitrião para obter endereço IPv4</span><span class="sxs-lookup"><span data-stu-id="f6716-431">**host_name_ptr** Pointer to host name to obtain IPv4 address</span></span>
- <span data-ttu-id="f6716-432">**tampão** Ponteiro para a localização para extrair dados do IPv4 em</span><span class="sxs-lookup"><span data-stu-id="f6716-432">**buffer** Pointer to location to extract IPv4 data into</span></span>
- <span data-ttu-id="f6716-433">**buffer_size** Tamanho do tampão para manter dados IPv4</span><span class="sxs-lookup"><span data-stu-id="f6716-433">**buffer_size** Size of buffer to hold IPv4 data</span></span>
- <span data-ttu-id="f6716-434">**wait_option** Aguarde a opção para receber a resposta do DNS Server</span><span class="sxs-lookup"><span data-stu-id="f6716-434">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-435">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-435">Return Values</span></span>

- <span data-ttu-id="f6716-436">**NX_SUCCESS** (0x00) obteve com sucesso dados do IPv4</span><span class="sxs-lookup"><span data-stu-id="f6716-436">**NX_SUCCESS** (0x00) Successfully obtained IPv4 data</span></span>
- <span data-ttu-id="f6716-437">**NX_DNS_NO_SERVER** (0xA1) Lista de servidores de clientes está vazia</span><span class="sxs-lookup"><span data-stu-id="f6716-437">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="f6716-438">**NX_DNS_QUERY_FAILED** (0xA3) Nenhuma resposta de DNS válida recebida</span><span class="sxs-lookup"><span data-stu-id="f6716-438">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="f6716-439">NX_PTR_ERROR (0x07) Ponteiro IP inválido ou DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-439">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="f6716-440">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="f6716-440">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="f6716-441">NX_DNS_PARAM_ERROR (0xA8) Parâmetro inválido sem ponte.</span><span class="sxs-lookup"><span data-stu-id="f6716-441">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-442">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-442">Allowed From</span></span>

<span data-ttu-id="f6716-443">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-443">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6716-444">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6716-444">Example</span></span>
```C
#define MAX_RECORD_COUNT  20

ULONG           record_buffer[50];
UINT            record_count;
ULONG           *ipv4_address_ptr[MAX_RECORD_COUNT];

/* Request the IPv4 address for the specified host. */
status =  nx_dns_ipv4_address_by_name_get(&client_dns, 
                                          (UCHAR *)"www.my_example.com",  
                                           record_buffer,                  
                                           sizeof(record_buffer),&record_count,                
                                           500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
        error_counter++;
}    
        else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed the IPv4
       address(es) is returned in record_buffer. */

          
            printf("------------------------------------------------------\n");
            printf("Test A: ");
            printf("record_count = %d \n", record_count);      


           /* Get the IPv4 addresses of host. */
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

[Output]

------------------------------------------------------
Test A: record_count = 5 
record 0: IP address: 192.2.2.10
record 1: IP address: 192.2.2.11
record 2: IP address: 192.2.2.12
record 3: IP address: 192.2.2.13
record 4: IP address: 192.2.2.14
```

## <a name="nxd_dns_ipv6_address_by_name_get"></a><span data-ttu-id="f6716-445">nxd_dns_ipv6_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="f6716-445">nxd_dns_ipv6_address_by_name_get</span></span>

<span data-ttu-id="f6716-446">Procure o endereço IPv6 para o nome do anfitrião de entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-446">Look up the IPv6 address for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-447">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-447">Prototype</span></span>
```C
UINT nxd_ dns_ipv6_address_by_name_get(NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f6716-448">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-448">Description</span></span>

<span data-ttu-id="f6716-449">Este serviço envia uma consulta do tipo AAAA com o nome de domínio especificado para obter os endereços IP para o nome de domínio de entrada.</span><span class="sxs-lookup"><span data-stu-id="f6716-449">This service sends a query of type AAAA with the specified domain name to obtain the IP addresses for the input domain name.</span></span> <span data-ttu-id="f6716-450">O Cliente DNS copia o endereço IPv6 a partir dos registos(s) AAAA devolvidos na resposta do DNS Server para o local de memória *record_buffer.*</span><span class="sxs-lookup"><span data-stu-id="f6716-450">The DNS Client copies the IPv6 address from the AAAA record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="f6716-451">O *record_buffer* deve estar alinhado em 4 bytes para receber os dados.</span><span class="sxs-lookup"><span data-stu-id="f6716-451">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="f6716-452">O formato dos endereços IPv6 armazenados no tampão alinhado de 4 byte é mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="f6716-452">The format of IPv6 addresses stored in the 4-byte aligned buffer is shown below:</span></span>

![Tampão alinhado iPv6 4 byte](media/image9.png)

<span data-ttu-id="f6716-454">Se a entrada *record_buffer* não conseguir conter todos os dados AAAA na resposta do servidor, o *record_buffer* detém o número de registos que caberão e devolve o número de registos no tampão.</span><span class="sxs-lookup"><span data-stu-id="f6716-454">If the input *record_buffer* cannot hold all the AAAA data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="f6716-455">Com o número de registos AAAA devolvidos em \**record_count,* a aplicação pode analisar os endereços IPv6 de cada registo no *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="f6716-455">With the number of AAAA records returned in \**record_count,* the application can parse the IPv6 addresses from each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-456">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-456">Input Parameters</span></span>

- <span data-ttu-id="f6716-457">**dns_ptr** Ponteiro para o Cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-457">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="f6716-458">**host_name_ptr** Ponteiro para o nome de anfitrião para obter endereço IPv6</span><span class="sxs-lookup"><span data-stu-id="f6716-458">**host_name_ptr** Pointer to host name to obtain IPv6 address</span></span>
- <span data-ttu-id="f6716-459">**tampão** Ponteiro para a localização para extrair dados do IPv6 em</span><span class="sxs-lookup"><span data-stu-id="f6716-459">**buffer** Pointer to location to extract IPv6 data into</span></span>
- <span data-ttu-id="f6716-460">**buffer_size** Tamanho do tampão para manter dados IPv6</span><span class="sxs-lookup"><span data-stu-id="f6716-460">**buffer_size** Size of buffer to hold IPv6 data</span></span>
- <span data-ttu-id="f6716-461">**wait_option** Aguarde a opção para receber a resposta do DNS Server</span><span class="sxs-lookup"><span data-stu-id="f6716-461">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-462">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-462">Return Values</span></span>

- <span data-ttu-id="f6716-463">**NX_SUCCESS** (0x00) obteve com sucesso dados do IPv6</span><span class="sxs-lookup"><span data-stu-id="f6716-463">**NX_SUCCESS** (0x00) Successfully obtained IPv6 data</span></span>
- <span data-ttu-id="f6716-464">**NX_DNS_NO_SERVER** (0xA1) Lista de servidores de clientes está vazia</span><span class="sxs-lookup"><span data-stu-id="f6716-464">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="f6716-465">**NX_DNS_QUERY_FAILED** (0xA3) Nenhuma resposta de DNS válida recebida</span><span class="sxs-lookup"><span data-stu-id="f6716-465">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="f6716-466">NX_PTR_ERROR (0x07) Ponteiro IP inválido ou DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-466">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="f6716-467">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="f6716-467">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="f6716-468">NX_DNS_PARAM_ERROR (0xA8) Parâmetro inválido sem ponte.</span><span class="sxs-lookup"><span data-stu-id="f6716-468">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-469">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-469">Allowed From</span></span>

<span data-ttu-id="f6716-470">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-470">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6716-471">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6716-471">Example</span></span>
```C
#define      MAX_RECORD_COUNT  20

ULONG           record_buffer[50];
UINT            record_count;
NXD_ADDRESS    *ipv6_address_ptr[MAX_RECORD_COUNT];

/* Request the IPv4 address for the specified host. */
status =  nxd_dns_ipv6_address_by_name_get(&client_dns, 
                                           (UCHAR *)"www.my_example.com", 
                                           record__buffer,                  
                                           sizeof(record_buffer), 
                                           &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
        error_counter++;
}    
        else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed the IPv6 
    address(es) is (are) returned in record_buffer. */
      
    printf("------------------------------------------------------\n");
    printf("Test AAAA: ");
    printf("record_count = %d \n", record_count);      

    /* Get the IPv6 addresses of host. */
    for(i =0; i< record_count; i++)
    {

        ipv6_address_ptr[i] = 
            (NX_DNS_IPV6_ADDRESS *)(record_buffer + i * sizeof(NX_DNS_IPV6_ADDRESS)); 
             
        printf("record %d: IP address: %x:%x:%x:%x:%x:%x:%x:%x\n", i, 
                ipv6_address_ptr[i] -> ipv6_address[0]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[0]  & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[1]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[1]  & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[2]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[2]  & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[3]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[3]  & 0xFFFF);
            }
}


[Output]
------------------------------------------------------
Test AAAA: record_count = 1 
record 0: IP address: 2001:0db8:0000:f101: 0000: 0000: 0000:01003
```

## <a name="nx_dns_host_by_address_get"></a><span data-ttu-id="f6716-472">nx_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="f6716-472">nx_dns_host_by_address_get</span></span>

<span data-ttu-id="f6716-473">Procure um nome de anfitrião a partir de um endereço IP</span><span class="sxs-lookup"><span data-stu-id="f6716-473">Look up a host name from an IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-474">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-474">Prototype</span></span>
```C
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f6716-475">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-475">Description</span></span>

<span data-ttu-id="f6716-476">Este serviço solicita a resolução de nome do endereço IP fornecido a partir de um ou mais Servidores DNS previamente especificados pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="f6716-476">This service requests name resolution of the supplied IP address from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="f6716-477">Se for bem sucedido, o nome do anfitrião rescindido por NU É devolvido na cadeia especificada por *host_name_ptr*.</span><span class="sxs-lookup"><span data-stu-id="f6716-477">If successful, the NULL-terminated host name is returned in the string specified by *host_name_ptr*.</span></span> <span data-ttu-id="f6716-478">Esta é uma função de invólucro para *nxd_dns_host_by_address_get* serviço e não aceita endereços IPv6.</span><span class="sxs-lookup"><span data-stu-id="f6716-478">This is a wrapper function for *nxd_dns_host_by_address_get* service and does not accept IPv6 addresses.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-479">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-479">Input Parameters</span></span>

- <span data-ttu-id="f6716-480">**dns_ptr** Ponteiro para a instância DNS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="f6716-480">**dns_ptr** Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="f6716-481">**ip_address** Endereço IP para resolver em nome</span><span class="sxs-lookup"><span data-stu-id="f6716-481">**ip_address** IP address to resolve into a name</span></span>
- <span data-ttu-id="f6716-482">**host_name_ptr** Ponteiro para a área de destino para o nome de anfitrião</span><span class="sxs-lookup"><span data-stu-id="f6716-482">**host_name_ptr** Pointer to destination area for host name</span></span>
- <span data-ttu-id="f6716-483">**max_host_name_size** Tamanho da área de destino para o nome de hospedeiro</span><span class="sxs-lookup"><span data-stu-id="f6716-483">**max_host_name_size** Size of destination area for host name</span></span>
- <span data-ttu-id="f6716-484">**wait_option** Define quanto tempo o serviço irá esperar no temporizador para uma resposta do servidor DNS após cada consulta de DNS e redandição de consulta.</span><span class="sxs-lookup"><span data-stu-id="f6716-484">**wait_option** Defines how long the service will wait in timer ticks for a DNS server response after each DNS query and query retry.</span></span> <span data-ttu-id="f6716-485">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="f6716-485">The wait options are defined as follows:</span></span>

  <span data-ttu-id="f6716-486">valor de prazo (0x00000001-0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="f6716-486">timeout value (0x00000001-0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>

  <span data-ttu-id="f6716-487">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que um servidor DNS responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="f6716-487">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

  <span data-ttu-id="f6716-488">A seleção de um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resolução do DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-488">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-489">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-489">Return Values</span></span>

- <span data-ttu-id="f6716-490">**NX_SUCCESS** (0x00) Resolução de DNS bem sucedida</span><span class="sxs-lookup"><span data-stu-id="f6716-490">**NX_SUCCESS** (0x00) Successful DNS resolution</span></span>  
- <span data-ttu-id="f6716-491">**NX_DNS_TIMEOUT** (0xA2) cronometrado na obtenção de mutex DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-491">**NX_DNS_TIMEOUT** (0xA2) Timed out on obtaining DNS mutex</span></span>
- <span data-ttu-id="f6716-492">**NX_DNS_NO_SERVER** (0xA1) Nenhum endereço dns server especificado</span><span class="sxs-lookup"><span data-stu-id="f6716-492">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="f6716-493">**NX_DNS_QUERY_FAILED** (0xA3) Não recebeu resposta à consulta</span><span class="sxs-lookup"><span data-stu-id="f6716-493">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="f6716-494">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Endereço de entrada nulo</span><span class="sxs-lookup"><span data-stu-id="f6716-494">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null input address</span></span>
- <span data-ttu-id="f6716-495">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) O índice aponta para o tipo de endereço inválido (por exemplo, IPv6)</span><span class="sxs-lookup"><span data-stu-id="f6716-495">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="f6716-496">**NX_DNS_PARAM_ERROR** (0xA8) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="f6716-496">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="f6716-497">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Não pode processar registo com IPv6 desativado</span><span class="sxs-lookup"><span data-stu-id="f6716-497">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="f6716-498">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="f6716-498">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="f6716-499">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="f6716-499">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-500">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-500">Allowed From</span></span>

<span data-ttu-id="f6716-501">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-501">Threads</span></span>

<span data-ttu-id="f6716-502">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f6716-502">**Example**</span></span>
```C
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */
```

## <a name="nxd_dns_host_by_address_get"></a><span data-ttu-id="f6716-503">nxd_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="f6716-503">nxd_dns_host_by_address_get</span></span>

<span data-ttu-id="f6716-504">Procure um nome de anfitrião a partir do endereço IP</span><span class="sxs-lookup"><span data-stu-id="f6716-504">Look up a host name from the IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-505">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-505">Prototype</span></span>
```C
UINT nxd_dns_host_by_address_get(NX_DNS *dns_ptr, 
                                 NXD_ADDRESS ip_address, 
                                 ULONG *host_name_ptr, 
                                 ULONG max_host_name_size, 
                                 ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f6716-506">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-506">Description</span></span>

<span data-ttu-id="f6716-507">Este serviço solicita a resolução de nome do endereço IPv6 ou IPv4 no *ip_address* argumento de entrada de um ou mais Servidores DNS previamente especificados pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="f6716-507">This service requests name resolution of the IPv6 or IPv4 address in the *ip_address* input argument from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="f6716-508">Se for bem sucedido, o nome do anfitrião rescindido por NU É devolvido na cadeia especificada por *host_name_ptr*.</span><span class="sxs-lookup"><span data-stu-id="f6716-508">If successful, the NULL-terminated host name is returned in the string specified by *host_name_ptr*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-509">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-509">Input Parameters</span></span>

- <span data-ttu-id="f6716-510">**dns_ptr** Ponteiro para a instância DNS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="f6716-510">**dns_ptr** Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="f6716-511">**ip_address** Endereço IP para resolver em nome</span><span class="sxs-lookup"><span data-stu-id="f6716-511">**ip_address** IP address to resolve into a name</span></span>
- <span data-ttu-id="f6716-512">**host_name_ptr** Ponteiro para a área de destino para o nome de anfitrião</span><span class="sxs-lookup"><span data-stu-id="f6716-512">**host_name_ptr** Pointer to destination area for host name</span></span>
- <span data-ttu-id="f6716-513">**max_host_name_size** Tamanho da área de destino para o nome de hospedeiro</span><span class="sxs-lookup"><span data-stu-id="f6716-513">**max_host_name_size** Size of destination area for host name</span></span>
- <span data-ttu-id="f6716-514">**wait_option** Define quanto tempo o serviço irá esperar no temporizador para uma resposta do servidor DNS após cada consulta de DNS e redandição de consulta.</span><span class="sxs-lookup"><span data-stu-id="f6716-514">**wait_option** Defines how long the service will wait in timer ticks for a DNS server response after each DNS query and query retry.</span></span> <span data-ttu-id="f6716-515">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="f6716-515">The wait options are defined as follows:</span></span>

  <span data-ttu-id="f6716-516">valor de tempo limite (0x00000001 a 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="f6716-516">timeout value (0x00000001 through 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>  

  <span data-ttu-id="f6716-517">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que um servidor DNS responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="f6716-517">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

  <span data-ttu-id="f6716-518">A seleção de um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resolução do DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-518">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-519">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-519">Return Values</span></span>

- <span data-ttu-id="f6716-520">**NX_SUCCESS** (0x00) Resolução de DNS bem sucedida</span><span class="sxs-lookup"><span data-stu-id="f6716-520">**NX_SUCCESS** (0x00) Successful DNS resolution</span></span>  
- <span data-ttu-id="f6716-521">**NX_DNS_TIMEOUT** (0xA2) cronometrado na obtenção de mutex DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-521">**NX_DNS_TIMEOUT** (0xA2) Timed out on obtaining DNS mutex</span></span>
- <span data-ttu-id="f6716-522">**NX_DNS_NO_SERVER** (0xA1) Nenhum endereço dns server especificado</span><span class="sxs-lookup"><span data-stu-id="f6716-522">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="f6716-523">**NX_DNS_QUERY_FAILED** (0xA3) Não recebeu resposta à consulta</span><span class="sxs-lookup"><span data-stu-id="f6716-523">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="f6716-524">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Endereço de entrada nulo</span><span class="sxs-lookup"><span data-stu-id="f6716-524">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null input address</span></span>
- <span data-ttu-id="f6716-525">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Não pode processar registo com IPv6 desativado</span><span class="sxs-lookup"><span data-stu-id="f6716-525">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="f6716-526">NX_PTR_ERROR (0x07) Ponteiro IP inválido ou DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-526">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="f6716-527">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="f6716-527">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="f6716-528">NX_DNS_PARAM_ERROR (0xA8) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="f6716-528">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-529">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-529">Allowed From</span></span>

<span data-ttu-id="f6716-530">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-530">Threads</span></span>

<span data-ttu-id="f6716-531">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f6716-531">**Example**</span></span>
```C
UCHAR   resolved_name[200];
NXD_ADDRESS host_address;

host_address.nxd_ip_version = NX_IP_VERISON_V6;
host_address.nxd_ip_address.v6[0] = 0x20010db8;
host_address.nxd_ip_address.v6[1] = 0x0;
host_address.nxd_ip_address.v6[2] = 0xf101;
host_address.nxd_ip-address.v6[3] = 0x108;

/* Get the name associated with theinput host_address. */
status =  nxd_dns_host_by_address_get(&my_dns, &host_address,
                                      resolved_name, sizeof(resolved_name), 4000);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
     error_counter++;
}     
else     
{
     printf("------------------------------------------------------\n");
     printf("Test PTR: %s\n", record_buffer);
}

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable. */


[Output]

 ------------------------------------------------------
 Test PTR: my_example.net
```

## <a name="nx_dns_host_by_name_get"></a><span data-ttu-id="f6716-532">nx_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="f6716-532">nx_dns_host_by_name_get</span></span>

<span data-ttu-id="f6716-533">Procure um endereço IP a partir do nome do anfitrião</span><span class="sxs-lookup"><span data-stu-id="f6716-533">Look up an IP address from the host name</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-534">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-534">Prototype</span></span>
```C
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f6716-535">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-535">Description</span></span>

<span data-ttu-id="f6716-536">Este serviço solicita a resolução de nome do nome fornecido a partir de um ou mais Servidores DNS previamente especificados pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="f6716-536">This service requests name resolution of the supplied name from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="f6716-537">Se for bem sucedido, o endereço IP associado é devolvido no destino apontado por host_address_ptr.</span><span class="sxs-lookup"><span data-stu-id="f6716-537">If successful, the associated IP address is returned in the destination pointed to by host_address_ptr.</span></span> <span data-ttu-id="f6716-538">Esta é uma função de invólucro para o serviço *nxd_dns_host_by_name_get,* e está limitada à entrada de endereço IPv4.</span><span class="sxs-lookup"><span data-stu-id="f6716-538">This is a wrapper function for the *nxd_dns_host_by_name_get* service, and is limited to IPv4 address input.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-539">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-539">Input Parameters</span></span>

- <span data-ttu-id="f6716-540">**dns_ptr** Ponteiro para a instância DNS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="f6716-540">**dns_ptr** Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="f6716-541">**host_name** Ponteiro para o nome de anfitrião</span><span class="sxs-lookup"><span data-stu-id="f6716-541">**host_name** Pointer to host name</span></span>
- <span data-ttu-id="f6716-542">**host_address_ptr** Endereço IP do DNS Server devolvido</span><span class="sxs-lookup"><span data-stu-id="f6716-542">**host_address_ptr** DNS Server IP address returned</span></span>
- <span data-ttu-id="f6716-543">**wait_option** Define quanto tempo o serviço vai esperar pela resolução do DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-543">**wait_option** Defines how long the service will wait for the DNS resolution.</span></span> <span data-ttu-id="f6716-544">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="f6716-544">The wait options are defined as follows:</span></span>

  <span data-ttu-id="f6716-545">valor de tempo limite (0x00000001 a 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="f6716-545">timeout value (0x00000001 through 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>

  <span data-ttu-id="f6716-546">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que um servidor DNS responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="f6716-546">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

  <span data-ttu-id="f6716-547">A seleção de um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resolução do DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-547">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-548">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-548">Return Values</span></span>

- <span data-ttu-id="f6716-549">**NX_SUCCESS** (0x00) Resolução de DNS bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="f6716-549">**NX_SUCCESS** (0x00) Successful DNS resolution.</span></span>
- <span data-ttu-id="f6716-550">**NX_DNS_NO_SERVER** (0xA1) Nenhum endereço dns server especificado</span><span class="sxs-lookup"><span data-stu-id="f6716-550">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="f6716-551">**NX_DNS_QUERY_FAILED** (0xA3) Não recebeu resposta à consulta</span><span class="sxs-lookup"><span data-stu-id="f6716-551">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="f6716-552">NX_DNS_PARAM_ERROR (0xA8) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="f6716-552">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="f6716-553">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="f6716-553">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="f6716-554">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="f6716-554">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-555">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-555">Allowed From</span></span>

<span data-ttu-id="f6716-556">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-556">Threads</span></span>

<span data-ttu-id="f6716-557">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f6716-557">**Example**</span></span>
```C
ULONG host_address;

/* Get the IP address for the name “www.my_example.com”. */
   status =  nx_dns_host_by_name_get(&my_dns, “www.my_example.com”, &host_address, 4000);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{

    /* If status is NX_SUCCESS the IP address for “www.my_example.com” can be found 
        in the “ip_address” variable. */
        
    printf("------------------------------------------------------\n");
    printf("Test A: \n");
    printf("IP address: %d.%d.%d.%d\n",
    host_address >> 24,
    host_address >> 16 & 0xFF,                   
    host_address >> 8 & 0xFF,
    host_address & 0xFF);
}

[Output]
 ------------------------------------------------------
Test A: 
IP address: 192.2.2.10
```

## <a name="nxd_dns_host_by_name_get"></a><span data-ttu-id="f6716-558">nxd_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="f6716-558">nxd_dns_host_by_name_get</span></span>

<span data-ttu-id="f6716-559">Procure um endereço IP a partir do nome do anfitrião</span><span class="sxs-lookup"><span data-stu-id="f6716-559">Lookup an IP address from the host name</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-560">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-560">Prototype</span></span>
```C
UINT nxd_dns_host_by_name_get(NX_DNS *dns_ptr, ULONG *host_name, 
                              NXD_ADDRESS *host_address_ptr, 
                              ULONG wait_option, UINT lookup_type);
```

### <a name="description"></a><span data-ttu-id="f6716-561">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-561">Description</span></span>

<span data-ttu-id="f6716-562">Este serviço solicita a resolução de nome do endereço IP fornecido a partir de um ou mais Servidores DNS previamente especificados pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="f6716-562">This service requests name resolution of the supplied IP address from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="f6716-563">Se for bem sucedido, o endereço IP associado é devolvido num NXD_ADDRESS apontado por *host_address_ptr*.</span><span class="sxs-lookup"><span data-stu-id="f6716-563">If successful, the associated IP address is returned in an NXD_ADDRESS pointed to by *host_address_ptr*.</span></span> <span data-ttu-id="f6716-564">Se o chamador definir especificamente a entrada lookup_type para NX_IP_VERSION_V6, este serviço enviará consulta para um endereço IPv6 anfitrião (registo AAAA).</span><span class="sxs-lookup"><span data-stu-id="f6716-564">If the caller specifically sets the lookup_type input to NX_IP_VERSION_V6, this service will send out query for a host IPv6 address (AAAA record).</span></span> <span data-ttu-id="f6716-565">Se o chamador definir especificamente a entrada lookup_type para NX_IP_VERSION_V4, este serviço enviará consulta para um endereço IPv4 anfitrião (Registo).</span><span class="sxs-lookup"><span data-stu-id="f6716-565">If the caller specifically sets the lookup_type input to NX_IP_VERSION_V4, this service will send out query for a host IPv4 address (A record).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-566">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-566">Input Parameters</span></span>

- <span data-ttu-id="f6716-567">**dns_ptr** Ponteiro para a instância do cliente DNS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="f6716-567">**dns_ptr** Pointer to previously created DNS Client instance.</span></span>
- <span data-ttu-id="f6716-568">**host_name** Ponteiro para o nome de anfitrião para encontrar um endereço IP de</span><span class="sxs-lookup"><span data-stu-id="f6716-568">**host_name** Pointer to host name to find an IP address of</span></span>
- <span data-ttu-id="f6716-569">**host_address_ptr** Ponteiro para destino para NXD_ADDRESS que contenha o endereço IP</span><span class="sxs-lookup"><span data-stu-id="f6716-569">**host_address_ptr** Pointer to destination for NXD_ADDRESS containing the IP address</span></span>
- <span data-ttu-id="f6716-570">**wait_option** Define quanto tempo o serviço irá esperar nos tiques temporizadores para a resposta do DNS Server para cada transmissão e retransmissão de consultas.</span><span class="sxs-lookup"><span data-stu-id="f6716-570">**wait_option** Defines how long the service will wait in timer ticks for the DNS Server response for each query transmission and retransmission.</span></span> <span data-ttu-id="f6716-571">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="f6716-571">The wait options are defined as follows:</span></span>

  <span data-ttu-id="f6716-572">valor de tempo limite (0x00000001 a 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="f6716-572">timeout value (0x00000001 through 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>  

  <span data-ttu-id="f6716-573">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que um Servidor DNS responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="f6716-573">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS Server responds to the request.</span></span>

  <span data-ttu-id="f6716-574">A seleção de um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resolução do DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-574">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

- <span data-ttu-id="f6716-575">**lookup_type** Indicar tipo de procura (A vs AAAA).</span><span class="sxs-lookup"><span data-stu-id="f6716-575">**lookup_type** Indicate type of lookup (A vs AAAA).</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-576">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-576">Return Values</span></span>

- <span data-ttu-id="f6716-577">**NX_SUCCESS** (0x00) Resolução de DNS bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="f6716-577">**NX_SUCCESS** (0x00) Successful DNS resolution.</span></span>
- <span data-ttu-id="f6716-578">**NX_DNS_NO_SERVER** (0xA1) Nenhum endereço dns server especificado</span><span class="sxs-lookup"><span data-stu-id="f6716-578">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="f6716-579">**NX_DNS_QUERY_FAILED** (0xA3) Não recebeu resposta à consulta</span><span class="sxs-lookup"><span data-stu-id="f6716-579">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="f6716-580">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Endereço de entrada nulo</span><span class="sxs-lookup"><span data-stu-id="f6716-580">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null input address</span></span>
- <span data-ttu-id="f6716-581">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Não pode processar registo com IPv6 desativado</span><span class="sxs-lookup"><span data-stu-id="f6716-581">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="f6716-582">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="f6716-582">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="f6716-583">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="f6716-583">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="f6716-584">NX_DNS_PARAM_ERROR (0xA8) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="f6716-584">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-585">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-585">Allowed From</span></span>

<span data-ttu-id="f6716-586">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-586">Threads</span></span>

<span data-ttu-id="f6716-587">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="f6716-587">**Example**</span></span>
```C
NXD_ADDRESS host_ipduo_address;

/* Create an AAAA query to obtain the IPv6 address for the host “www.my_example.com”. */
status =  nxd_dns_host_by_name_get(&my_dns, “www.my_example.com”, 
                                   &host_ipduo_address, 4000, 
                                   NX_IP_VERSION_V6);

if (status != NX_SUCCESS)
{
        error_counter++;
}
else
{
/* If status is NX_SUCCESS the IP address for “www.my_example.com” can be 
   found in the “ip_address” variable. */

    printf("------------------------------------------------------\n");
    printf("Test AAAA: \n");

    printf("IP address: %x:%x:%x:%x:%x:%x:%x:%x\n", 
           host_ipduo_address.nxd_ip_address.v6[0]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[0]  & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[1]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[1]  & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[2]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[2]  & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[3]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[3]  & 0xFFFF);
}

[Output]

------------------------------------------------------
Test AAAA: 
IP address: 2607:f8b0:4007:800:0:0:0:1008
```

<span data-ttu-id="f6716-588">Outro exemplo de utilização deste serviço de tempo, desta vez utilizando endereços IPv4 e tipos de registo A, é mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="f6716-588">Another example of using this time service, this time using IPv4 addresses and A record types, is shown below:</span></span>
```C
/* Create a query to obtain the IPv4 address for the host “www.my_example.com”. */
status =  nxd_dns_host_by_name_get(&my_dns, “www.my_example.com”, &ip_address, 4000, 
                                   NX_IP_VERSION_V4);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else     
{   
/* If status is NX_SUCCESS the IP address for “www.my_example.com” can be 
   found in the “ip_address” variable. */
  
     printf("------------------------------------------------------\n");
     printf("Test A: \n");
     printf("IP address: %d.%d.%d.%d\n",
            host_ipduo_address.nxd_ip_address.v4 >> 24,
            host_ipduo_address.nxd_ip_address.v4 >> 16 & 0xFF,                   
            host_ipduo_address.nxd_ip_address.v4 >> 8 & 0xFF,
            host_ipduo_address.nxd_ip_address.v4 & 0xFF);
 }

[Output]

------------------------------------------------------
Test A: 
IP address: 192.2.2.10
```

## <a name="nx_dns_host_text_get"></a><span data-ttu-id="f6716-589">nx_dns_host_text_get</span><span class="sxs-lookup"><span data-stu-id="f6716-589">nx_dns_host_text_get</span></span>

<span data-ttu-id="f6716-590">Procure a cadeia de texto para o nome de domínio de entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-590">Look up the text string for the input domain name</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-591">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-591">Prototype</span></span>
```C
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f6716-592">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-592">Description</span></span>

<span data-ttu-id="f6716-593">Este serviço envia uma consulta do tipo TXT com o nome de domínio especificado e tampão para obter os dados de cadeia arbitrários.</span><span class="sxs-lookup"><span data-stu-id="f6716-593">This service sends a query of type TXT with the specified domain name and buffer to obtain the arbitrary string data.</span></span>

<span data-ttu-id="f6716-594">O Cliente DNS copia a cadeia de texto no registo TXT na resposta do DNS Server para a *localização da* memória record_buffer.</span><span class="sxs-lookup"><span data-stu-id="f6716-594">The DNS Client copies the text string in the TXT record in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="f6716-595">O record_buffer não precisa de estar alinhado com 4 bytes para receber os dados.</span><span class="sxs-lookup"><span data-stu-id="f6716-595">The record_buffer does not need to be 4-byte aligned to receive the data.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-596">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-596">Input Parameters</span></span>

- <span data-ttu-id="f6716-597">**dns_ptr** Ponteiro para o Cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-597">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="f6716-598">**host_name** Ponteiro para o nome do anfitrião para pesquisar em</span><span class="sxs-lookup"><span data-stu-id="f6716-598">**host_name** Pointer to name of host to search on</span></span>
- <span data-ttu-id="f6716-599">**record_buffer** Ponteiro para a localização para extrair dados TXT em</span><span class="sxs-lookup"><span data-stu-id="f6716-599">**record_buffer** Pointer to location to extract TXT data into</span></span>
- <span data-ttu-id="f6716-600">**buffer_size** Tamanho do tampão para conter dados TXT</span><span class="sxs-lookup"><span data-stu-id="f6716-600">**buffer_size** Size of buffer to hold TXT data</span></span>
- <span data-ttu-id="f6716-601">**wait_option** Aguarde a opção para receber a resposta do DNS Server</span><span class="sxs-lookup"><span data-stu-id="f6716-601">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-602">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-602">Return Values</span></span>

- <span data-ttu-id="f6716-603">**NX_SUCCESS** (0x00) Cadeia TXT obtida com sucesso</span><span class="sxs-lookup"><span data-stu-id="f6716-603">**NX_SUCCESS** (0x00) Successfully TXT string obtained</span></span>
- <span data-ttu-id="f6716-604">**NX_DNS_NO_SERVER** (0xA1) Lista de servidores de clientes está vazia</span><span class="sxs-lookup"><span data-stu-id="f6716-604">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="f6716-605">**NX_DNS_QUERY_FAILED** (0xA3) Nenhuma resposta de DNS válida recebida</span><span class="sxs-lookup"><span data-stu-id="f6716-605">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="f6716-606">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="f6716-606">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="f6716-607">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="f6716-607">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="f6716-608">NX_DNS_PARAM_ERROR (0xA8) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="f6716-608">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-609">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-609">Allowed From</span></span>

<span data-ttu-id="f6716-610">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-610">Threads</span></span>

######   
<span data-ttu-id="f6716-611">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6716-611">Example</span></span>
```C
CHAR            record_buffer[50];

/* Request the text string for the specified host. */
status =  nx_dns_host_text_get(&client_dns, (UCHAR *)"www.my_example.com", 
                               record_buffer, 
                               sizeof(record_buffer), 500);


/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
     error_counter++;
}
else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and the
       text string is returned in record_buffer. */
 
     printf("------------------------------------------------------\n");
     printf("Test TXT:\n %s\n", record_buffer);
} 


[Output]

------------------------------------------------------
Test TXT: 
v=spf1 include:_www.my_example.com ip4:192.2.2.10/31 ip4:192.2.2.11/31 ~all
```

## <a name="nx_dns_packet_pool_set"></a><span data-ttu-id="f6716-612">nx_dns_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="f6716-612">nx_dns_packet_pool_set</span></span>

<span data-ttu-id="f6716-613">Desa estaladiço do pacote do cliente DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-613">Set the DNS Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-614">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-614">Prototype</span></span>
```C
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="f6716-615">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-615">Description</span></span>

<span data-ttu-id="f6716-616">Este serviço define um pacote de pacotes previamente criado como o pacote de pacotes DNS Client.</span><span class="sxs-lookup"><span data-stu-id="f6716-616">This service sets a previously created packet pool as the DNS Client packet pool.</span></span> <span data-ttu-id="f6716-617">O Cliente DNS utilizará este pacote para enviar consultas de DNS, pelo que a carga útil do pacote não deve ser inferior a NX_DNS_PACKET_PAYLOAD que inclui os cabeçalhos Ethernet, IP e UDP e é definido em *nxd_dns.h.*</span><span class="sxs-lookup"><span data-stu-id="f6716-617">The DNS Client will use this packet pool to send DNS queries, so the packet payload should not be less than NX_DNS_PACKET_PAYLOAD which includes the Ethernet, IP and UDP headers and is defined in *nxd_dns.h.*</span></span> 

> [!NOTE]
> <span data-ttu-id="f6716-618">*W* hen o DNS Client é eliminado, o pacote de pacotes não é apagado com ele e é da responsabilidade da aplicação apagar o pacote de pacotes quando já não precisa dele.</span><span class="sxs-lookup"><span data-stu-id="f6716-618">*W* hen the DNS Client is deleted, the packet pool is not deleted with it and it is the responsibility of the application to delete the packet pool when it no longer needs it.</span></span>
>
> <span data-ttu-id="f6716-619">Este serviço só está disponível se a opção de configuração NX_DNS_CLIENT_USER_CREATE_PACKET_POOL for definida em *nxd_dns.h*</span><span class="sxs-lookup"><span data-stu-id="f6716-619">This service is only available if the configuration option NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined in *nxd_dns.h*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-620">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-620">Input Parameters</span></span>

- <span data-ttu-id="f6716-621">**dns_ptr** Ponteiro para a instância do cliente DNS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="f6716-621">**dns_ptr** Pointer to previously created DNS Client instance.</span></span>
- <span data-ttu-id="f6716-622">**pool_ptr** Ponteiro para piscina de pacotes previamente criada</span><span class="sxs-lookup"><span data-stu-id="f6716-622">**pool_ptr** Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-623">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-623">Return Values</span></span>

- <span data-ttu-id="f6716-624">**NX_SUCCESS** (0x00) Conclusão bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="f6716-624">**NX_SUCCESS** (0x00) Successful completion.</span></span>
- <span data-ttu-id="f6716-625">**NX_NOT_ENABLED** (0x14) Cliente não configurado para esta opção</span><span class="sxs-lookup"><span data-stu-id="f6716-625">**NX_NOT_ENABLED** (0x14) Client not configured for this option</span></span>
- <span data-ttu-id="f6716-626">NX_PTR_ERROR (0x07) Ponteiro IP inválido ou DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-626">NX_PTR_ERROR (0x07) Invalid IP or DNS Client pointer.</span></span>
- <span data-ttu-id="f6716-627">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="f6716-627">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-628">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-628">Allowed From</span></span>

<span data-ttu-id="f6716-629">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-629">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6716-630">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6716-630">Example</span></span>
```C
NXD_DNS my_dns;
NX_PACKET_POOL client_pool;
NX_IP *ip_ptr;


/* Create the DNS Client. */
status =  nx_dns_create(&my_dns, ip_ptr, “My DNS Client”);

/* Create a packet pool for the DNS Client. */
status =  nx_packet_pool_create(&client_pool, "DNS Client Packet Pool", 
                                NX_DNS_PACKET_PAYLOAD, free_mem_pointer, 
                                NX_DNS_PACKET_POOL_SIZE);

/* Set the DNS Client packet pool. */
status =  nx_dns_packet_pool_set(&my_dns, &client_pool);

/* If status is NX_SUCCESS the DNS Client packet pool was successfully set. */
```

## <a name="nx_dns_server_add"></a><span data-ttu-id="f6716-631">nx_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="f6716-631">nx_dns_server_add</span></span>

<span data-ttu-id="f6716-632">Adicionar endereço IP do servidor DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-632">Add DNS Server IP Address</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-633">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-633">Prototype</span></span>
```C
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a><span data-ttu-id="f6716-634">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-634">Description</span></span>

<span data-ttu-id="f6716-635">Este serviço adiciona um Servidor DNS IPv4 à lista de servidores.</span><span class="sxs-lookup"><span data-stu-id="f6716-635">This service adds an IPv4 DNS Server to the server list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-636">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-636">Input Parameters</span></span>

- <span data-ttu-id="f6716-637">**dns_ptr** Ponteiro para o bloco de controlo DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-637">**dns_ptr** Pointer to DNS control block.</span></span>  
- <span data-ttu-id="f6716-638">**server_address** Endereço IP do Servidor DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-638">**server_address** IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-639">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-639">Return Values</span></span>

- <span data-ttu-id="f6716-640">**NX_SUCCESS** (0x00) Servidor adicionado com sucesso</span><span class="sxs-lookup"><span data-stu-id="f6716-640">**NX_SUCCESS** (0x00) Server successfully added</span></span>
- <span data-ttu-id="f6716-641">**NX_DNS_DUPLICATE_ENTRY**</span><span class="sxs-lookup"><span data-stu-id="f6716-641">**NX_DNS_DUPLICATE_ENTRY**</span></span>  
<span data-ttu-id="f6716-642">**NX_NO_MORE_ENTRIES** (0x17) Não são permitidos mais servidores DNS (a lista está completa)</span><span class="sxs-lookup"><span data-stu-id="f6716-642">**NX_NO_MORE_ENTRIES** (0x17) No more DNS Servers Allowed (list is full)</span></span>
- <span data-ttu-id="f6716-643">**NX_DNS_PARAM_ERROR** (0xA8) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="f6716-643">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="f6716-644">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Não pode processar registo com IPv6 desativado</span><span class="sxs-lookup"><span data-stu-id="f6716-644">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="f6716-645">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="f6716-645">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="f6716-646">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="f6716-646">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="f6716-647">NX_DNS_BAD_ADDRESS_ERROR (0xA4) Entrada de endereço de servidor nulo</span><span class="sxs-lookup"><span data-stu-id="f6716-647">NX_DNS_BAD_ADDRESS_ERROR (0xA4) Null server address input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-648">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-648">Allowed From</span></span>

<span data-ttu-id="f6716-649">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-649">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6716-650">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6716-650">Example</span></span>
```C
/* Add a DNS Server at IP address 202.2.2.13. */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added. */
```

## <a name="nxd_dns_server_add"></a><span data-ttu-id="f6716-651">nxd_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="f6716-651">nxd_dns_server_add</span></span>

<span data-ttu-id="f6716-652">Adicionar servidor DNS à lista de clientes</span><span class="sxs-lookup"><span data-stu-id="f6716-652">Add DNS Server to the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-653">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-653">Prototype</span></span>
```C
UINT nxd_dns_server_add(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a><span data-ttu-id="f6716-654">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-654">Description</span></span>

<span data-ttu-id="f6716-655">Este serviço adiciona o endereço IP de um servidor DNS à lista de servidores do DNS Client.</span><span class="sxs-lookup"><span data-stu-id="f6716-655">This service adds the IP address of a DNS server to the DNS Client server list.</span></span> <span data-ttu-id="f6716-656">O server_address pode ser um endereço IPv4 ou IPv6.</span><span class="sxs-lookup"><span data-stu-id="f6716-656">The server_address may be either an IPv4 or IPv6 address.</span></span> <span data-ttu-id="f6716-657">Se o Cliente pretender aceder ao mesmo servidor através do seu endereço IPv4 ou do endereço IPv6, deverá adicionar ambos os endereços IP como entradas na lista de servidores.</span><span class="sxs-lookup"><span data-stu-id="f6716-657">If the Client wishes to be able to access the same server by either its IPv4 address or IPv6 address it should add both IP addresses as entries to the server list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-658">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-658">Input Parameters</span></span>

- <span data-ttu-id="f6716-659">**dns_ptr** Ponteiro para o bloco de controlo DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-659">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="f6716-660">**server_address** Ponteiro para o NXD_ADDRESS que contém o endereço IP do servidor DO DNS Server.</span><span class="sxs-lookup"><span data-stu-id="f6716-660">**server_address** Pointer to the NXD_ADDRESS containing the server IP address of DNS Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-661">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-661">Return Values</span></span>

- <span data-ttu-id="f6716-662">**NX_SUCCESS** (0x00) Servidor adicionado com sucesso</span><span class="sxs-lookup"><span data-stu-id="f6716-662">**NX_SUCCESS** (0x00) Server successfully added</span></span>
- <span data-ttu-id="f6716-663">**NX_DNS_DUPLICATE_ENTRY**</span><span class="sxs-lookup"><span data-stu-id="f6716-663">**NX_DNS_DUPLICATE_ENTRY**</span></span>  
<span data-ttu-id="f6716-664">**NX_NO_MORE_ENTRIES** (0x17) Não são permitidos mais Servidores DNS (a lista está completa)</span><span class="sxs-lookup"><span data-stu-id="f6716-664">**NX_NO_MORE_ENTRIES** (0x17) No more DNS Servers allowed (list is full)</span></span> 
- <span data-ttu-id="f6716-665">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Não pode processar registo com IPv6 desativado</span><span class="sxs-lookup"><span data-stu-id="f6716-665">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="f6716-666">**NX_DNS_PARAM_ERROR** (0xA8) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="f6716-666">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="f6716-667">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="f6716-667">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="f6716-668">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="f6716-668">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="f6716-669">NX_DNS_BAD_ADDRESS_ERROR (0xA4) Entrada de endereço de servidor nulo</span><span class="sxs-lookup"><span data-stu-id="f6716-669">NX_DNS_BAD_ADDRESS_ERROR (0xA4) Null server address input</span></span>
- <span data-ttu-id="f6716-670">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) O índice aponta para o tipo de endereço inválido (por exemplo, IPv6)</span><span class="sxs-lookup"><span data-stu-id="f6716-670">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-671">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-671">Allowed From</span></span>

<span data-ttu-id="f6716-672">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-672">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6716-673">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6716-673">Example</span></span>
```C
NXD_ADDRESS server_address;

server_address.nxd_ip_version = NX_IP_VERISON_V6;
server_address.nxd_ip_address.v6[0] = 0x20010db8;
server_address.nxd_ip_address.v6[1] = 0x0;
server_address.nxd_ip_address.v6[2] = 0xf101;
server_address.nxd_ip-address.v6[3] = 0x108;


/* Add a DNS Server with the IP address pointed to by the server_address input. */
status =  nxd_dns_server_add(&my_dns, &server_address);

/* If status is NX_SUCCESS a DNS Server was successfully added. */
```

## <a name="nx_dns_server_get"></a><span data-ttu-id="f6716-674">nx_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="f6716-674">nx_dns_server_get</span></span>

<span data-ttu-id="f6716-675">Devolva um Servidor DNS IPv4 da lista de clientes</span><span class="sxs-lookup"><span data-stu-id="f6716-675">Return an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-676">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-676">Prototype</span></span>
```C
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        ULONG *dns_server_address);
```

### <a name="description"></a><span data-ttu-id="f6716-677">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-677">Description</span></span>

<span data-ttu-id="f6716-678">Este serviço devolve o endereço IPv4 DNS Server da lista de servidores no índice especificado.</span><span class="sxs-lookup"><span data-stu-id="f6716-678">This service returns the IPv4 DNS Server address from the server list at the specified index.</span></span> 

> [!NOTE]
> <span data-ttu-id="f6716-679">O índice é baseado em zero.</span><span class="sxs-lookup"><span data-stu-id="f6716-679">The index is zero based.</span></span> <span data-ttu-id="f6716-680">Se o índice de entrada exceder o tamanho da lista de Clientes DNS, um endereço IPv6 é encontrado nesse índice ou um endereço nulo é encontrado no índice especificado, um erro é devolvido.</span><span class="sxs-lookup"><span data-stu-id="f6716-680">If the input index exceeds the size of the DNS Client list, an IPv6 address is found at that index or a null address is found at the specified index, an error is returned.</span></span> <span data-ttu-id="f6716-681">O serviço *nx_dns_get_serverlist_size* pode ser chamado primeiro obter o número de servidores DNS na lista de Clientes.</span><span class="sxs-lookup"><span data-stu-id="f6716-681">The *nx_dns_get_serverlist_size* service may be called first obtain the number of DNS servers in the Client list.</span></span>

<span data-ttu-id="f6716-682">Este serviço suporta apenas endereços IPv4.</span><span class="sxs-lookup"><span data-stu-id="f6716-682">This service does only supports IPv4 addresses.</span></span> <span data-ttu-id="f6716-683">Chama ao serviço *nxd_dns_server_get* que suporta os endereços IPv4 e IPv6.</span><span class="sxs-lookup"><span data-stu-id="f6716-683">It calls the *nxd_dns_server_get* service which supports both IPv4 and IPv6 addresses.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-684">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-684">Input Parameters</span></span>

- <span data-ttu-id="f6716-685">**dns_ptr** Ponteiro para bloco de controlo DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-685">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="f6716-686">**índice** Índice na lista de servidores do CLIENTE DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-686">**index** Index into DNS Client’s list of servers</span></span>
- <span data-ttu-id="f6716-687">**dns_server_address** Ponteiro para endereço IP do Servidor DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-687">**dns_server_address** Pointer to IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-688">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-688">Return Values</span></span>

- <span data-ttu-id="f6716-689">**NX_SUCCESS** (0x00) Servidor de sucesso devolvido</span><span class="sxs-lookup"><span data-stu-id="f6716-689">**NX_SUCCESS** (0x00) Successful server returned</span></span>
- <span data-ttu-id="f6716-690">**Índice NX_DNS_SERVER_NOT_FOUND** (0xA9) aponta para slot vazio</span><span class="sxs-lookup"><span data-stu-id="f6716-690">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Index points to empty slot</span></span>
- <span data-ttu-id="f6716-691">**índice NX_DNS_BAD_ADDRESS_ERROR** (0xA4) aponta para endereço nulo</span><span class="sxs-lookup"><span data-stu-id="f6716-691">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Index points to Null address</span></span>
- <span data-ttu-id="f6716-692">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) O índice aponta para o tipo de endereço inválido (por exemplo, IPv6)</span><span class="sxs-lookup"><span data-stu-id="f6716-692">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="f6716-693">**NX_DNS_PARAM_ERROR** (0xA8) Entrada inválida sem ponte</span><span class="sxs-lookup"><span data-stu-id="f6716-693">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="f6716-694">NX_PTR_ERROR (0x07) Ponteiro IP inválido ou DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-694">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="f6716-695">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="f6716-695">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-696">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-696">Allowed From</span></span>

<span data-ttu-id="f6716-697">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-697">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6716-698">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6716-698">Example</span></span>
```C
ULONG my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nxd_dns_server_get"></a><span data-ttu-id="f6716-699">nxd_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="f6716-699">nxd_dns_server_get</span></span>

<span data-ttu-id="f6716-700">Devolva um Servidor DNS da lista de clientes</span><span class="sxs-lookup"><span data-stu-id="f6716-700">Return a DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-701">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-701">Prototype</span></span>
```C
UINT nxd_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        NXD_ADDRESS *dns_server_address);
```

### <a name="description"></a><span data-ttu-id="f6716-702">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-702">Description</span></span>

<span data-ttu-id="f6716-703">Este serviço devolve o endereço IP do SERVIDOR DNS da lista de servidores no índice especificado.</span><span class="sxs-lookup"><span data-stu-id="f6716-703">This service returns the DNS Server IP address from the server list at the specified index.</span></span> 

> [!NOTE]
> <span data-ttu-id="f6716-704">O índice é baseado em zero.</span><span class="sxs-lookup"><span data-stu-id="f6716-704">The index is zero based.</span></span> <span data-ttu-id="f6716-705">Se o índice de entrada exceder o tamanho da lista de Clientes DNS, ou se um endereço nulo for encontrado no índice especificado, um erro é devolvido.</span><span class="sxs-lookup"><span data-stu-id="f6716-705">If the input index exceeds the size of the DNS Client list, or a null address is found at the specified index, an error is returned.</span></span> <span data-ttu-id="f6716-706">O serviço *nx_dns_get_serverlist_size* pode ser chamado primeiro para obter o número de servidores DNS na lista de servidores.</span><span class="sxs-lookup"><span data-stu-id="f6716-706">The *nx_dns_get_serverlist_size* service may be called first to obtain the number of DNS servers in the server list.</span></span>

<span data-ttu-id="f6716-707">Este serviço suporta endereços IPv4 e IPv6.</span><span class="sxs-lookup"><span data-stu-id="f6716-707">This service supports IPv4 and IPv6 addresses.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-708">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-708">Input Parameters</span></span>

- <span data-ttu-id="f6716-709">**dns_ptr** Ponteiro para bloco de controlo DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-709">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="f6716-710">**índice** Índice na lista de servidores do CLIENTE DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-710">**index** Index into DNS Client’s list of servers</span></span>
- <span data-ttu-id="f6716-711">**dns_server_address** Ponteiro para endereço IP do Servidor DNS</span><span class="sxs-lookup"><span data-stu-id="f6716-711">**dns_server_address** Pointer to IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-712">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-712">Return Values</span></span>

- <span data-ttu-id="f6716-713">**NX_SUCCESS** (0x00) endereço IP do servidor devolvido com sucesso</span><span class="sxs-lookup"><span data-stu-id="f6716-713">**NX_SUCCESS** (0x00) Successfully returned server IP address</span></span>
- <span data-ttu-id="f6716-714">**Índice NX_DNS_SERVER_NOT_FOUND** (0xA9) aponta para slot vazio</span><span class="sxs-lookup"><span data-stu-id="f6716-714">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Index points to empty slot</span></span>
- <span data-ttu-id="f6716-715">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Índice aponta para endereço de servidor nulo</span><span class="sxs-lookup"><span data-stu-id="f6716-715">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Index points to null server address</span></span>
- <span data-ttu-id="f6716-716">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) O índice aponta para o tipo de endereço inválido (por exemplo, IPv6)</span><span class="sxs-lookup"><span data-stu-id="f6716-716">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="f6716-717">**NX_DNS_PARAM_ERROR** (0xA8) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="f6716-717">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="f6716-718">NX_PTR_ERROR (0x07) Ponteiro IP inválido ou DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-718">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="f6716-719">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="f6716-719">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-720">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-720">Allowed From</span></span>

<span data-ttu-id="f6716-721">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-721">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6716-722">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6716-722">Example</span></span>
```C
NXD_ADDRESS my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nxd_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nx_dns_server_remove"></a><span data-ttu-id="f6716-723">nx_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="f6716-723">nx_dns_server_remove</span></span>

<span data-ttu-id="f6716-724">Remova um Servidor DNS IPv4 da lista de clientes</span><span class="sxs-lookup"><span data-stu-id="f6716-724">Remove an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-725">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-725">Prototype</span></span>
```C
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a><span data-ttu-id="f6716-726">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-726">Description</span></span>

<span data-ttu-id="f6716-727">Este serviço remove um Servidor DNS IPv4 da lista de Clientes.</span><span class="sxs-lookup"><span data-stu-id="f6716-727">This service removes an IPv4 DNS Server from the Client list.</span></span> <span data-ttu-id="f6716-728">É uma função de invólucro para *nxd_dns_server_remove*.</span><span class="sxs-lookup"><span data-stu-id="f6716-728">It is a wrapper function for *nxd_dns_server_remove*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-729">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-729">Input Parameters</span></span>

- <span data-ttu-id="f6716-730">**dns_ptr** Ponteiro para o bloco de controlo DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-730">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="f6716-731">**server_address** Endereço IP do DNS Server.</span><span class="sxs-lookup"><span data-stu-id="f6716-731">**server_address** IP address of DNS Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-732">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-732">Return Values</span></span>

- <span data-ttu-id="f6716-733">**NX_SUCCESS** (0x00) DNS Server removido com sucesso</span><span class="sxs-lookup"><span data-stu-id="f6716-733">**NX_SUCCESS** (0x00) DNS Server successfully removed</span></span>
- <span data-ttu-id="f6716-734">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Servidor não na lista de clientes</span><span class="sxs-lookup"><span data-stu-id="f6716-734">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Server not in Client list</span></span>
- <span data-ttu-id="f6716-735">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Entrada de endereço de servidor nulo</span><span class="sxs-lookup"><span data-stu-id="f6716-735">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null server address input</span></span>
- <span data-ttu-id="f6716-736">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Não pode processar registo com IPv6 desativado</span><span class="sxs-lookup"><span data-stu-id="f6716-736">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="f6716-737">NX_PTR_ERROR (0x07) Ponteiro IP inválido ou DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-737">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="f6716-738">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="f6716-738">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-739">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-739">Allowed From</span></span>

<span data-ttu-id="f6716-740">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-740">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6716-741">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6716-741">Example</span></span>
```C
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nxd_dns_server_remove"></a><span data-ttu-id="f6716-742">nxd_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="f6716-742">nxd_dns_server_remove</span></span>

<span data-ttu-id="f6716-743">Remova um Servidor DNS da lista de clientes</span><span class="sxs-lookup"><span data-stu-id="f6716-743">Remove a DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-744">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-744">Prototype</span></span>
```C
UINT nxd_dns_server_remove(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a><span data-ttu-id="f6716-745">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-745">Description</span></span>

<span data-ttu-id="f6716-746">Este serviço remove um Servidor DNS do endereço IP especificado da lista de Clientes.</span><span class="sxs-lookup"><span data-stu-id="f6716-746">This service removes a DNS Server of the specified IP address from the Client list.</span></span> <span data-ttu-id="f6716-747">O endereço IP de entrada aceita endereços IPv4 e IPv6.</span><span class="sxs-lookup"><span data-stu-id="f6716-747">The input IP address accepts both IPv4 and IPv6 addresses.</span></span> <span data-ttu-id="f6716-748">Após a remoção do servidor, os restantes servidores descem um índice da lista para preencher a ranhura desocupada.</span><span class="sxs-lookup"><span data-stu-id="f6716-748">After the server is removed, the remaining servers move down one index in the list to fill the vacated slot.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-749">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-749">Input Parameters</span></span>

- <span data-ttu-id="f6716-750">**dns_ptr** Ponteiro para o bloco de controlo DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-750">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="f6716-751">**server_address** O ponteiro para o SERVIDOR DNS NXD_ADDRESS dados que contenham o endereço IP do servidor.</span><span class="sxs-lookup"><span data-stu-id="f6716-751">**server_address** Pointer to DNS Server NXD_ADDRESS data containing server IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-752">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-752">Return Values</span></span>

- <span data-ttu-id="f6716-753">**NX_SUCCESS** (0x00) DNS Server removido com sucesso</span><span class="sxs-lookup"><span data-stu-id="f6716-753">**NX_SUCCESS** (0x00) DNS Server successfully removed</span></span>
- <span data-ttu-id="f6716-754">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Servidor não na lista de clientes</span><span class="sxs-lookup"><span data-stu-id="f6716-754">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Server not in Client list</span></span>
- <span data-ttu-id="f6716-755">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Entrada de endereço de servidor nulo</span><span class="sxs-lookup"><span data-stu-id="f6716-755">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null server address input</span></span>
- <span data-ttu-id="f6716-756">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Não pode processar registo com IPv6 desativado</span><span class="sxs-lookup"><span data-stu-id="f6716-756">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="f6716-757">NX_PTR_ERROR (0x07) Ponteiro IP inválido ou DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-757">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="f6716-758">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="f6716-758">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="f6716-759">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) O índice aponta para o tipo de endereço inválido (por exemplo, IPv6)</span><span class="sxs-lookup"><span data-stu-id="f6716-759">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-760">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-760">Allowed From</span></span>

<span data-ttu-id="f6716-761">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-761">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6716-762">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6716-762">Example</span></span>
```C
NXD_ADDRESS server_address;

server_address.nxd_ip_version = NX_IP_VERISON_V6;
server_address.nxd_ip_address.v6[0] = 0x20010db8;
server_address.nxd_ip_address.v6[1] = 0x0;
server_address.nxd_ip_address.v6[2] = 0xf101;
server_address.nxd_ip-address.v6[3] = 0x108;


/* Remove the DNS Server at the specified IP address from the Client list. */
status =  nxd_dns_server_remove(&my_dns,&server_ADDRESS);

/* If status is NX_SUCCESS a DNS Server was successfully removed. */
```

## <a name="nx_dns_server_remove_all"></a><span data-ttu-id="f6716-763">nx_dns_server_remove_all</span><span class="sxs-lookup"><span data-stu-id="f6716-763">nx_dns_server_remove_all</span></span>

<span data-ttu-id="f6716-764">Remova todos os Servidores DNS da lista de clientes</span><span class="sxs-lookup"><span data-stu-id="f6716-764">Remove all DNS Servers from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="f6716-765">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6716-765">Prototype</span></span>
```C
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```
### <a name="description"></a><span data-ttu-id="f6716-766">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6716-766">Description</span></span>

<span data-ttu-id="f6716-767">Este serviço remove todos os Servidores DNS da lista de Clientes.</span><span class="sxs-lookup"><span data-stu-id="f6716-767">This service removes all DNS Servers from the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f6716-768">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="f6716-768">Input Parameters</span></span>

- <span data-ttu-id="f6716-769">**dns_ptr** Ponteiro para o bloco de controlo DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-769">**dns_ptr** Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6716-770">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f6716-770">Return Values</span></span>

- <span data-ttu-id="f6716-771">**NX_SUCCESS** (0x00) SERVIDORes DNS removidos com sucesso</span><span class="sxs-lookup"><span data-stu-id="f6716-771">**NX_SUCCESS** (0x00) DNS Servers successfully removed</span></span>
- <span data-ttu-id="f6716-772">**NX_DNS_ERROR** (0xA0) Incapaz de obter proteção mutex</span><span class="sxs-lookup"><span data-stu-id="f6716-772">**NX_DNS_ERROR** (0xA0) Unable to obtain protection mutex</span></span>
- <span data-ttu-id="f6716-773">NX_PTR_ERROR (0x07) Ponteiro IP inválido ou DNS.</span><span class="sxs-lookup"><span data-stu-id="f6716-773">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="f6716-774">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="f6716-774">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6716-775">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="f6716-775">Allowed From</span></span>

<span data-ttu-id="f6716-776">Fios</span><span class="sxs-lookup"><span data-stu-id="f6716-776">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f6716-777">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6716-777">Example</span></span>
```C
/* Remove all DNS Servers from the Client list. */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed. */
```