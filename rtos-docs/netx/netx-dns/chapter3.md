---
title: Capítulo 3 - Descrição dos Serviços de Clientes Azure RTOS NetX DNS
description: Este capítulo contém uma descrição de todos os serviços DNS Azure RTOS NetX (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 922d41dc374ccd782809404776f18f2aed8f5e3c34b7c9e143075c0ee5567220
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782527"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dns-client-services"></a>Capítulo 3 - Descrição dos Serviços de Clientes Azure RTOS NetX DNS

Este capítulo contém uma descrição de todos os serviços DNS Azure RTOS NetX (listados abaixo) por ordem alfabética.

Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

- **nx_dns_authority_zone_start_get**: *Procure o início de uma zona de autoridade associada ao nome de hospedeiro especificado*
- **nx_dns_cache_initialize**: *Inicialize uma Cache DNS.*
- **nx_dns_cache_notify_clear:** *Limpe a função de notificação completa da cache.*
- **nx_dns_cache_notify_set:** *Desa estale a função de notificação completa da cache.*
- **nx_dns_cname_get**: *Procure o nome de domínio canónico para o pseudónimo do nome de domínio de entrada*
- **nx_dns_create**: *Criar uma instância do cliente DNS*
- **nx_dns_delete**: *Excluir uma instância do cliente DNS*
- **nx_dns_domain_name_server_get**: *Procure os servidores de nome autorizados para a zona de domínio de entrada*
- **nx_dns_domain_mail_exchange_get**: *Procure a troca de correio associada ao nome de anfitrião especificado.*
- **nx_dns_domain_service_get**: *Procure os serviços associados ao nome de anfitrião especificado*
- **nx_dns_get_serverlist_size**: *Devolva o tamanho da lista de servidores do Cliente DNS*
- **nx_dns_info_by_name_get**: *Endereço IP de devolução, consulta portuária no nome do anfitrião de entrada*
- **nx_dns_ipv4_address_by_name_get**: *Procure o endereço IPv4 a partir do nome de anfitrião especificado*
- **nx_dns_host_by_address_get**: *Procure um nome de anfitrião a partir de um endereço IP especificado*
- **nx_dns_host_by_name_get**: *Procure o endereço IPv4 a partir do nome de anfitrião especificado*
- **nx_dns_host_text_get**: *Procure os dados de texto para o nome do domínio de entrada*
- **nx_dns_packet_pool_set**: *Definir a piscina de pacotes do cliente DNS*
- **nx_dns_server_add**: *Adicione um Servidor DNS no endereço especificado na lista de clientes*
- **nx_dns_server_get**: *Devolva o Servidor DNS na lista de clientes*
- **nx_dns_server_remove**: *Remova um Servidor DNS da lista de clientes*
- **nx_dns_server_remove_all**: *Remova todos os Servidores DNS da lista de clientes*

## <a name="nx_dns_authority_zone_start_get"></a>nx_dns_authority_zone_start_get

Procure o início da zona de autoridade para o anfitrião de entrada

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);

```

### <a name="description"></a>Description

Se NX_DNS_ENABLE_EXTENDED_RR_TYPES for definido, este serviço envia uma consulta do tipo SOA com o nome de domínio especificado para obter o início da zona de autoridade para o nome de domínio de entrada. O Cliente DNS copia os registos SOA devolvidos na resposta do DNS Server para o local de memória *record_buffer.* 
>[!NOTE]
> O *record_buffer* deve estar alinhado em 4 bytes para receber os dados.

No NetX DNS Client, o tipo de registo SOA, NX_DNS_SOA_ENTRY, é guardado como sete parâmetros de byte 4, totalizando 28 bytes:

- **nx_dns_soa_host_mname_ptr**: Ponteiro para a principal fonte de dados para esta zona
- **nx_dns_soa_host_rname_ptr**: Ponteiro para caixa de correio responsável por esta zona
- **nx_dns_soa_serial**: Número da versão da zona
- **nx_dns_soa_refresh**: Intervalo de atualização
- **nx_dns_soa_retry**: Intervalo entre as retrírias da consulta SOA
- **nx_dns_soa_expire**: Duração do tempo quando o SOA expirar
- **nx_dns_soa_minmum**: Campo TTL mínimo em mensagens de resposta DOMS de nome SOA

O armazenamento de dois registos SOA é mostrado abaixo. Os registos SOA que contenham dados de comprimento fixo são introduzidos a partir da parte superior do tampão. Os ponteiros MNAME e RNAME apontam para os dados de comprimento variável (nomes hospedeiros) que são armazenados na parte inferior do tampão. Os registos SOA adicionais são introduzidos após o primeiro registo ("registos SOA adicionais...") e os seus dados de comprimento variável são armazenados acima dos dados variáveis do comprimento da última entrada ("dados adicionais de comprimento variável SOA"):

![Diagrama que representa o armazenamento de dois registos S O A](media/image2.png)

Se a entrada *record_buffer* não conseguir conter todos os dados do SOA na resposta do servidor, o *record_buffer* detém o número de registos que caberão e devolve o número de registos no tampão.

Com o número de registos SOA devolvidos em **record_count,* a aplicação pode analisar os dados a partir de *record_buffer* e extrair o início das cordas de nome de anfitrião da autoridade da zona.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dns_ptr**: Ponteiro para o Cliente DNS.  
- **host_name**: Ponteiro para o nome de anfitrião para obter dados do SOA
- **record_buffer**: Ponteiro para a localização para extrair dados do SOA em
- **buffer_size**: Tamanho do tampão para reter dados do SOA
- **record_count**: Ponteiro para o número de registos SOA recuperados
- **wait_option**: Aguarde a opção para receber a resposta do DNS Server

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) obteve com sucesso dados do SOA
- **NX_DNS_NO_SERVER**: (0xA1) A lista de servidores de clientes está vazia
- **NX_DNS_QUERY_FAILED**: (0xA3) Nenhuma resposta de DNS válida recebida
- NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS
- NX_CALLER_ERROR: (0x11) Inválido deste serviço
- NX_DNS_PARAM_ERROR: (0xA8) Entrada inválida sem ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo
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


## <a name="nx_dns_cache_initialize"></a>nx_dns_cache_initialize

Inicializar a Cache DNS

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_cache_initialize(NX_DNS *dns_ptr,
                             VOID *cache_ptr, UINT cache_size);

```
### <a name="description"></a>Description

Este serviço cria e inicializa uma Cache DNS.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dns_ptr**: Ponteiro para o bloco de controlo DNS.
- **cache_ptr**: Ponteiro para a Cache DNS.
- **cache_size**: Tamanho da Cache DNS, em bytes.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) DNS Cache inicializada com sucesso
- NX_DNS_ERROR: (0xA0) A cache não está alinhada com 4 bytes.
- NX_DNS_PARAM_ERROR: (0xA8) ID DNS inválido.
- NX_PTR_ERROR: (0x07) Ponteiro DNS inválido.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo
```c
UCHAR          dns_cache [2048]; 

/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, dns_cache, 2048);
/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a>nx_dns_cache_notify_clear

Limpe a função de notificação completa da Cache DNS

### <a name="prototype"></a>Prototype

```c
UINT     nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```
### <a name="description"></a>Description

Este serviço limpa a função de notificação completa da cache.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dns_ptr**: Ponteiro para o bloco de controlo DNS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) cache DNS notificam com sucesso definido
- NX_DNS_PARAM_ERROR: (0xA8) ID DNS inválido.
- NX_PTR_ERROR: (0x07) Ponteiro DNS inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Clear the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a>nx_dns_cache_notify_set

Desa estale a função de notificação completa da Cache DNS

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr, VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a>Description

Este serviço define a função de notificação completa da cache.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dns_ptr**: Ponteiro para o bloco de controlo DNS.
- **cache_full_notify_cb**: A função de retorno a invocar quando a cache ficar cheia.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) cache DNS notificam com sucesso definido
- NX_DNS_PARAM_ERROR: (0xA8) ID DNS inválido.
- NX_PTR_ERROR: (0x07) Ponteiro DNS inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Set the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set.  */
 
```

## <a name="nx_dns_cname_get"></a>nx_dns_cname_get

Procure o nome canónico para o nome de anfitrião de entrada

### <a name="prototype"></a>Prototype
```c
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                      UCHAR *record_buffer, UINT buffer_size, 
                      ULONG wait_option);
```

### <a name="description"></a>Description

Se NX_DNS_ENABLE_EXTENDED_RR_TYPES for definida em *nx_dns.h,* este serviço envia uma consulta do tipo CNAME com o nome de domínio especificado para obter o nome de domínio canónico. O Cliente DNS copia a cadeia CNAME devolvida na resposta do DNS Server para o local de memória *record_buffer.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dns_ptr**: Ponteiro para o Cliente DNS.  
- **host_name**: Ponteiro para o nome de anfitrião para obter dados CNAME para
- **record_buffer**: Ponteiro para a localização para extrair dados do CNAME
- **buffer_size**: Tamanho do tampão para conter dados CNAME
- **wait_option**: Aguarde a opção para receber a resposta do DNS Server

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) obtidos com sucesso dados cname
- **NX_DNS_NO_SERVER**: (0xA1) A lista de servidores de clientes está vazia
- **NX_DNS_QUERY_FAILED**: (0xA3) Nenhuma resposta de DNS válida recebida
- NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS
- NX_CALLER_ERROR: (0x11) Inválido deste serviço
- NX_DNS_PARAM_ERROR: (0xA8) Entrada inválida sem ponte

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

## <a name="nx_dns_create"></a>nx_dns_create

Criar uma instância de cliente DNS

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```

### <a name="description"></a>Description

Este serviço cria uma instância do Cliente DNS para a instância IP previamente criada.

>[!NOTE]
>A aplicação deve garantir que a carga útil do pacote do pacote utilizado pelo Cliente DNS seja suficientemente grande para a mensagem máxima de 512 byte DNS, além dos cabeçalhos UDP, IP e Ethernet. Se o Cliente DNS criar a sua própria piscina de pacotes, isso é definido por NX_DNS_PACKET_POOL_SIZE e NX_DNS_PACKET_PAYLOAD. Se a aplicação DO CLIENTE DNS preferir fornecer um conjunto de pacotes previamente criado, a carga útil para o IPv4 DNS Cliente deve ser de 512 bytes para o máximo DNS mais 20 bytes para o cabeçalho IP, 8 bytes para o cabeçalho UDP e 14 bytes para o cabeçalho Ethernet.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dns_ptr**: Ponteiro para o Cliente DNS.  
- **ip_ptr**: Ponteiro para instância IP previamente criada.  
- **domain_name**: Ponteiro para o nome de domínio para a instância DNS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) DNS bem sucedidos criam
- **NX_DNS_ERROR**: (0xA0) DNS criam erro
- NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS
- NX_CALLER_ERROR: (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Create a DNS Client instance.  */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created.  */
```
## <a name="nx_dns_delete"></a>nx_dns_delete

Excluir uma instância do cliente DNS

### <a name="prototype"></a>Prototype

```c
UINT     nx_dns_delete(NX_DNS *dns_ptr);
```

### <a name="description"></a>Description

Este serviço elimina uma instância do Cliente DNS previamente criada e liberta os seus recursos. 
>[!NOTE]
> Se **NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** estiver definido e o Cliente DNS tiver sido atribuído a um pacote de pacotes definido pelo utilizador, cabe à aplicação eliminar o pacote de pacotes DNS Client se já não precisar.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dns_ptr**: Ponteiro para a instância do **Cliente** DNS previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) O Cliente DNS com sucesso apaga.
- NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou dns.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Delete a DNS Client instance.  */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted.  */
```
## <a name="nx_dns_domain_name_server_get"></a>nx_dns_domain_name_server_get

Procure os servidores de nome autorizados para a zona de domínio de entrada

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a>Description

Se NX_DNS_ENABLE_EXTENDED_RR_TYPES for definido, este serviço envia uma consulta do tipo NS com o nome de domínio especificado para obter os servidores de nome para o nome de domínio de entrada. O Cliente DNS copia os registos NS devolvidos na resposta do DNS Server para o local de memória *record_buffer.* 

>[!NOTE]
>O *record_buffer* deve estar alinhado em 4 bytes para receber os dados.

No Cliente NetX DNS o tipo de dados NS, NX_DNS_NS_ENTRY, é guardado como dois parâmetros de 4 byte:

- **nx_dns_ns_ipv4_address**: Endereço IPv4 do servidor de nomes
- **nx_dns_ns_hostname_ptr**: Ponteiro para o nome de anfitrião do servidor de nome

O tampão mostrado abaixo contém quatro registos NX_DNS_NS_ENTRY. O ponteiro para o anfitrião de cadeia de nome em cada ponto de entrada para a cadeia de nome do anfitrião correspondente na metade inferior do tampão:

![Diagrama do tampão que contém quatro registos de entrada N X D N S N S.](media/image3.png)

Se a entrada *record_buffer* não conseguir conter todos os dados NS na resposta do servidor, o *record_buffer* detém o número de registos que caberão e devolve o número de registos no tampão.

Com o número de registos NS devolvidos em **record_count,* a aplicação pode analisar o endereço IP e o nome de anfitrião de cada registo no *record_buffer*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dns_ptr**: Ponteiro para o Cliente DNS.  
- **host_name**: Ponteiro para o nome de anfitrião para obter dados de NS para
- **record_buffer**: Ponteiro para a localização para extrair dados do SNS em
- **buffer_size**: Tamanho do tampão para conter dados do NS
- **record_count**: Ponteiro para o número de registos NS recuperados
- **wait_option**: Aguarde a opção para receber a resposta do DNS Server

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) obteve com sucesso dados de NS
- **NX_DNS_NO_SERVER**: (0xA1) A lista de servidores de clientes está vazia
- **NX_DNS_QUERY_FAILED**: (0xA3) Nenhuma resposta de DNS válida recebida
- NX_DNS_PARAM_ERROR: (0xA8) ID DNS inválido.
- NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS
- NX_CALLER_ERROR: (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo
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

## <a name="nx_dns_domain_mail_exchange_get"></a>nx_dns_domain_mail_exchange_get

Procure a troca de correio para o nome do anfitrião de entrada

### <a name="prototype"></a>Prototype
```c
UINT     nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                        VOID *record_buffer,                                        
                                        UINT buffer_size, 
                                        UINT *record_count, 
                                        ULONG wait_option);

```

### <a name="description"></a>Description

Se NX_DNS_ENABLE_EXTENDED_RR_TYPES for definido, este serviço envia uma consulta do tipo MX com o nome de domínio especificado para obter a troca de correio para o nome de domínio de entrada. O Cliente DNS copia os registos(s) MX devolvidos na resposta do DNS Server para o local de memória *record_buffer.*

>[!NOTE]
>O *record_buffer* deve estar alinhado em 4 bytes para receber os dados.

No Cliente NetX DNS, o tipo de registo de troca de correio, NX_DNS_MAIL_EXCHANGE_ENTRY, é guardado como quatro parâmetros, totalizando 12 bytes:

- **nx_dns_mx_ipv4_address**: Endereço IPv4 de troca de correio 4 bytes
- **nx_dns_mx_preference**: Preferência 2 bytes
- **nx_dns_mx_reserved0**: Reservado 2 bytes
- **nx_dns_mx_hostname_ptr**: Ponteiro para troca de correio servidor nome de anfitrião 4 bytes

Um tampão contendo quatro registos MX é mostrado abaixo. Cada registo contém os dados de comprimento fixo da lista acima. O ponteiro para o nome do anfitrião do servidor de troca de correio aponta para o nome de anfitrião correspondente na parte inferior do tampão.

![Diagrama que mostra o tampão contendo quatro registos M X.](media/image4.png)

Se a entrada *record_buffer* não conseguir conter todos os dados MX na resposta do servidor, o *record_buffer* detém o número de registos que caberão e devolve o número de registos no tampão.

Com o número de registos MX devolvidos em **record_count,* a aplicação pode analisar os parâmetros MX, incluindo o nome do anfitrião de cada registo no *record_buffer*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dns_ptr**: Ponteiro para o Cliente DNS.  
- **host_name**: Ponteiro para o nome de anfitrião para obter dados MX para
- **record_buffer**: Ponteiro para a localização para extrair dados de MX em
- **buffer_size**: Tamanho do tampão para conter dados MX
- **record_count**: Ponteiro para o número de registos MX recuperados
- **wait_option**: Aguarde a opção para receber a resposta do DNS Server

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) obteve com sucesso dados de MX
- **NX_DNS_NO_SERVER**: (0xA1) A lista de servidores de clientes está vazia
- **NX_DNS_QUERY_FAILED**: (0xA3) Nenhuma resposta de DNS válida recebida
- NX_DNS_PARAM_ERROR: (0xA8) ID DNS inválido.
- NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS
- NX_CALLER_ERROR: (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo
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


## <a name="nx_dns_domain_service_get"></a>nx_dns_domain_service_get

Procure o(s) serviço(s) fornecido pelo nome do anfitrião de entrada

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a>Description

Se NX_DNS_ENABLE_EXTENDED_RR_TYPES for definido, este serviço envia uma consulta do tipo SRV com o nome de domínio especificado para procurar o(s) serviço(s) e o número de porta associado ao domínio especificado. O Cliente DNS copia os registos SRV devolvidos na resposta do DNS Server para o local de memória *record_buffer.* 

>[!NOTE]
>O *record_buffer* deve estar alinhado em 4 bytes para receber os dados.

No NetX DNS Client, o tipo de registo de serviço, NX_DNS_SRV_ ENTRADA, é guardado como seis parâmetros, totalizando 16 bytes. Isto permite que os dados SRV de comprimento variável sejam armazenados de forma eficiente na memória:

- **Endereço IPv4 do servidor**: nx_dns_srv_ipv4_address 4 bytes
- **Prioridade do servidor**: nx_dns_srv_priority 2 bytes
- **Peso do servidor**: nx_dns_srv_weight 2 bytes
- **Número da porta de** serviço : nx_dns_srv_port_number 2 bytes
- **Reservado para alinhamento de 4 bytes:** nx_dns_srv_reserved0 2 bytes
- **Ponteiro para o nome do anfitrião do servidor**: *nx_dns_srv_hostname_ptr 4 bytes

Quatro registos SRV são armazenados no tampão fornecido. Cada NX_DNS_SRV_ENTRY registo contém um ponteiro, *nx_dns_srv_hostname_ptr,* que aponta para a cadeia de nome do anfitrião correspondente na parte inferior do tampão de gravação:

![Diagrama de quatro registos S R V armazenados no tampão fornecido.](media/image5.png)

Se a entrada *record_buffer* não conseguir conter todos os dados SRV na resposta do servidor, o *record_buffer* detém o número de registos que caberão e devolve o número de registos no tampão.

Com o número de registos SRV devolvidos em **record_count,* a aplicação pode analisar os parâmetros SRV, incluindo o nome do anfitrião do servidor de cada registo no *record_buffer*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dns_ptr**: Ponteiro para o Cliente DNS.  
- **host_name**: Ponteiro para o nome de anfitrião para obter dados SRV para
- **record_buffer**: Ponteiro para a localização para extrair dados de SRV em
- **buffer_size**: Tamanho do tampão para conter dados SRV
- **record_count**: Ponteiro para o número de registos SRV recuperados
- **wait_option**: Aguarde a opção para receber a resposta do DNS Server

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Dados SRV obtidos com sucesso
- **NX_DNS_NO_SERVER**: (0xA1) A lista de servidores de clientes está vazia
- **NX_DNS_QUERY_FAILED**: (0xA3) Nenhuma resposta de DNS válida recebida
- NX_DNS_PARAM_ERROR: (0xA8) ID DNS inválido.
- NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS
- NX_CALLER_ERROR: (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

## <a name="nx_dns_get_serverlist_size"></a>nx_dns_get_serverlist_size

Devolva o tamanho da lista de servidores do cliente DNS

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```

### <a name="description"></a>Description

Este serviço devolve o número de Servidores DNS válidos na lista de Clientes.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dns_ptr**: Ponteiro para bloco de controlo DNS  
- **tamanho**: Devolve o número de servidores na lista

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) O tamanho da lista do Servidor DNS regressou com sucesso
- NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list.  */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned.  */
```

## <a name="nx_dns_info_by_name_get"></a>nx_dns_info_by_name_get

Endereço IP de devolução e porta do servidor DNS pelo nome de anfitrião

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço devolve o IP do Servidor e a porta (registo de serviço) com base no nome do anfitrião de entrada por consulta DNS. Se não for encontrado um registo de serviço, esta rotina devolve um endereço IP zero no ponteiro do endereço de entrada e um estado de erro não zero volta a sinalizar um erro.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dns_ptr**: Ponteiro para bloco de controlo DNS  
- **host_name**: Ponteiro para o tampão do nome anfitrião
- **host_address_ptr**: Ponteiro para endereçar para regressar
- **host_port_ptr:** Ponteiro para a porta para devolver wait_option Opção de espera para a resposta ao DNS

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Registo do DNS Server devolvido com sucesso
- **NX_DNS_NO_SERVER**: (0xA1) Nenhum Servidor DNS registado com o Cliente para enviar consulta no nome anfitrião
- **NX_DNS_QUERY_FAILED**: (0xA3) A consulta do DNS falhou; não há resposta de nenhum servidor DNS na lista de Clientes ou nenhum registo de serviço está disponível para o nome de anfitrião de entrada.
- NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS
- NX_CALLER_ERROR: (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo
```c
ULONG         ip_address;
USHORT         port;

/* Attempt to resolve the IP address and ports for this host name.  */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned.  */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a>nx_dns_ipv4_address_by_name_get

Procure o endereço IPv4 para o nome do anfitrião de entrada

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                       UCHAR *host_name_ptr, VOID *buffer, 
                                       UINT buffer_size, 
                                       UINT *record_count,
                                       ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço envia uma consulta do tipo A com o nome de anfitrião especificado para obter os endereços IP para o nome do anfitrião de entrada. O Cliente DNS copia o endereço IPv4 a partir dos registos A devolvidos na resposta do DNS Server para o local de memória *record_buffer.* 

>[!NOTE]
>O *record_buffer* deve estar alinhado em 4 bytes para receber os dados.

Vários endereços IPv4 são armazenados no tampão alinhado de 4 byte, conforme mostrado abaixo:

![Diagrama de vários endereços I P v 4 que são armazenados no tampão alinhado 4 byte.](media/image6.png)

Se o tampão fornecido não conseguir conter todos os dados do endereço IP, os restantes registos A não são armazenados em *record_buffer*. Isto permite que a aplicação recupere um, alguns ou todos os dados de endereço IP disponíveis na resposta do servidor.

Com o número de registos A devolvidos **record_count* a aplicação pode analisar os dados de endereço IPv4 do *record_buffer*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dns_ptr**: Ponteiro para o Cliente DNS.  
- **host_name_ptr**: Ponteiro para o nome de anfitrião para obter o ponteiro do tampão de endereço IPv4 para a localização para extrair dados do IPv4
- **buffer_size**: Tamanho do tampão para conter dados IPv4
- **wait_option**: Aguarde a opção para receber a resposta do DNS Server

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) obteve com sucesso dados do IPv4
- **NX_DNS_NO_SERVER**: (0xA1) A lista de servidores de clientes está vazia
- **NX_DNS_QUERY_FAILED**: (0xA3) Nenhuma resposta de DNS válida recebida
- NX_DNS_PARAM_ERROR: (0xA8) Parâmetro de entrada inválido.
- NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS
- NX_CALLER_ERROR: (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

## <a name="nx_dns_host_by_address_get"></a>nx_dns_host_by_address_get

Procure um nome de anfitrião a partir de um endereço IP

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço solicita a resolução de nome do endereço IP fornecido a partir de um ou mais Servidores DNS previamente especificados pela aplicação. Se for bem sucedido, o nome do anfitrião rescindido por NU É devolvido na cadeia especificada por *host_name_ptr*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dns_ptr**: Ponteiro para a instância DNS previamente criada.
- **ip_address**: Endereço IP para resolver em nome
- **host_name_ptr**: Ponteiro para a área de destino para o nome de anfitrião
- **max_host_name_size**: Tamanho da área de destino para o nome de hospedeiro
- **wait_option**: Define quanto tempo o serviço irá esperar nos tiques temporizadores para uma resposta do servidor DNS após cada consulta de DNS e retry de consulta As opções de espera são definidas da seguinte forma:
    - **valor de tempo limite**: (0x00000001-0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resolução do DNS.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que um servidor DNS responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Resolução bem sucedida do DNS  
- **NX_DNS_TIMEOUT**: (0xA2) Cronometrado na obtenção de mutex DNS
- **NX_DNS_NO_SERVER**: (0xA1) Não é especificado nenhum endereço DNS Server
- **NX_DNS_QUERY_FAILED**: (0xA3) Não recebeu resposta à consulta
- **NX_DNS_BAD_ADDRESS_ERROR:**(0xA4) Endereço de entrada nulo
- **NX_DNS_INVALID_ADDRESS_TYPE**: (0xB2) O índice aponta para o tipo de endereço inválido (por exemplo, IPv6)
- **NX_DNS_PARAM_ERROR:**(0xA8) Entrada inválida sem ponteiro
- NX_PTR_ERROR: (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR: (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */

```

## <a name="nx_dns_host_by_name_get"></a>nx_dns_host_by_name_get

Procure um endereço IP a partir do nome do anfitrião

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço solicita a resolução de nome do nome fornecido, apontado por *host_name*, a partir de um ou mais Servidores DNS previamente especificados pela aplicação. Se for bem sucedido, o endereço IP associado é devolvido no destino apontado por *host_address_ptr*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dns_ptr**: Ponteiro para a instância DNS previamente criada.
- **host_name**: Ponteiro para o nome de anfitrião
- **host_address_ptr**: Ponteiro para o endereço IP do anfitrião DNS
- **wait_option**: Define quanto tempo o serviço aguarda pela resolução do DNS. As opções de espera são definidas da seguinte forma:
    - **valor de tempo limite**: (0x00000001 a 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resolução do DNS.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que um servidor DNS responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Resolução de DNS bem sucedida.
- **NX_DNS_NO_SERVER**: (0xA1) Não é especificado nenhum endereço DNS Server
- **NX_DNS_QUERY_FAILED**: (0xA3) Não recebeu resposta à consulta
- NX_DNS_PARAM_ERROR: (0xA8) Entrada inválida sem ponteiro
- NX_PTR_ERROR: (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR: (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo
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

## <a name="nx_dns_host_text_get"></a>nx_dns_host_text_get

Procure a cadeia de texto para o nome de domínio de entrada

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço envia uma consulta do tipo TXT com o nome de domínio especificado e tampão para obter os dados de cadeia arbitrários.

O Cliente DNS copia a cadeia de texto no registo TXT na resposta do DNS Server para a *localização da* memória record_buffer. 

>[!NOTE]
>O *record_buffer* não precisa de estar alinhado com 4 byte para receber os dados.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dns_ptr**: Ponteiro para o Cliente DNS.  
- **host_name**: Ponteiro para o nome do anfitrião para pesquisar
- **record_buffer**: Ponteiro para a localização para extrair dados TXT em
- **buffer_size**: Tamanho do tampão para conter dados TXT
- **wait_option**: Aguarde a opção para receber a resposta do DNS Server

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Cadeia TXT obtida com sucesso
- **NX_DNS_NO_SERVER**: (0xA1) A lista de servidores de clientes está vazia
- **NX_DNS_QUERY_FAILED**: (0xA3) Nenhuma resposta de DNS válida recebida
- NX_PTR_ERROR: (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR: (0x11) Inválido deste serviço
- NX_DNS_PARAM_ERROR: (0xA8) Entrada inválida sem ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

## <a name="nx_dns_packet_pool_set"></a>nx_dns_packet_pool_set

Desa estaladiço do pacote do cliente DNS

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a>Description

Este serviço define um pacote de pacotes previamente criado como o pacote de pacotes DNS **Client.** O Cliente DNS utilizará este pacote para enviar consultas de DNS, pelo que a carga útil do pacote não deve ser inferior a NX_DNS_PACKET_PAYLOAD_UNALIGNED que inclui os cabeçalhos Ethernet, IP e UDP e é definido em *nx_dns.h*.
 
>[!NOTE]
>Quando o Cliente DNS é eliminado, o pacote não é apagado com ele e é da responsabilidade da aplicação apagar o pacote quando já não precisa.

>[!NOTE]
>Este serviço só está disponível se a opção de configuração NX_DNS_CLIENT_USER_CREATE_PACKET_POOL for definida em *nx_dns.h*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dns_ptr**: Ponteiro para a instância do **Cliente** DNS previamente criada.
- **pool_ptr**: Ponteiro para piscina de pacotes previamente criada

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Conclusão bem sucedida.
- **NX_NOT_ENABLED:**(0x14) Cliente não configurado para esta opção
- NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou **DNS.**
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo
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

## <a name="nx_dns_server_add"></a>nx_dns_server_add

Adicionar endereço IP do servidor DNS

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a>Description

Este serviço adiciona um Servidor DNS IPv4 à lista de servidores.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dns_ptr**: Ponteiro para o bloco de controlo DNS.  
- **server_address**: Endereço IP do Servidor DNS

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Servidor adicionado com sucesso
- **NX_DNS_DUPLICATE_ENTRY** ou **NX_NO_MORE_ENTRIES:**(0x17) Não são permitidos mais servidores DNS (a lista está completa)
- **NX_DNS_PARAM_ERROR:**(0xA8) Entrada inválida sem ponteiro
- NX_PTR_ERROR: (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR: (0x11) Inválido deste serviço
- NX_DNS_BAD_ADDRESS_ERROR: (0xA4) Entrada de endereço de servidor nulo

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Add a DNS Server at IP address 202.2.2.13.  */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added.  */
```

## <a name="nx_dns_server_get"></a>nx_dns_server_get

Devolva um Servidor DNS IPv4 da lista de clientes

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                       ULONG *dns_server_address);
```

### <a name="description"></a>Description

Este serviço devolve o endereço IPv4 DNS Server da lista de servidores no índice especificado. Note que o índice é baseado em zero. Se o índice de entrada exceder o tamanho da lista de Clientes DNS, é devolvido um erro. O serviço *nx_dns_get_serverlist_size* pode ser chamado primeiro obter o número de servidores DNS na lista de Clientes.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dns_ptr**: Ponteiro para bloco de controlo DNS  
- **índice** na lista de servidores do CLIENTE DNS
- **dns_server_address**: Ponteiro para endereço IP do Servidor DNS

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Servidor de sucesso devolvido
- **NX_DNS_SERVER_NOT_FOUND**: (0xA9) Índice aponta para slot vazio
- **NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Índice aponta para endereço nulo
- **NX_DNS_PARAM_ERROR**: (0xA8) Índice excede o tamanho da lista
- NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
ULONG     my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list.  */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned.  */
```

## <a name="nx_dns_server_remove"></a>nx_dns_server_remove

Remova um Servidor DNS IPv4 da lista de clientes

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a>Description

Este serviço remove um Servidor DNS IPv4 da lista de Clientes.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dns_ptr**: Ponteiro para o bloco de controlo DNS.
- **server_address**: Endereço IP do DNS Server.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) DNS Server removido com sucesso
- **NX_DNS_SERVER_NOT_FOUND**: (0xA9) Servidor não na lista de clientes
- **NX_DNS_BAD_ADDRESS_ERROR:**(0xA4) Entrada de endereço de servidor nulo
- NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nx_dns_server_remove_all"></a>nx_dns_server_remove_all

Remova todos os Servidores DNS da lista de clientes

### <a name="prototype"></a>Prototype

```c
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```

### <a name="description"></a>Description

Este serviço remove todos os Servidores DNS da lista de Clientes.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dns_ptr**: Ponteiro para o bloco de controlo DNS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Servidores DNS removidos com sucesso
- **NX_DNS_ERROR**: (0xA0) Incapaz de obter proteção mutex
- NX_PTR_ERROR: (0x07) Ponteiro IP inválido ou DNS.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c

/* Remove all DNS Servers from the Client list.  */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed.  */
```