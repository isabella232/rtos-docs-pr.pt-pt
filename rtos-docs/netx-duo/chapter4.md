---
title: Capítulo 4 - Descrição dos Serviços Azure RTOS NetX Duo
description: Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX Duo por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 85617aadab7f484a4f4e467fd13f815f4d8b5609
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827044"
---
# <a name="chapter-4---description-of-azure-rtos-netx-duo-services"></a>Capítulo 4 - Descrição dos Serviços Azure RTOS NetX Duo

Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX Duo por ordem alfabética. Os nomes de serviço são projetados para que todos os serviços similares sejam agrupados. Por exemplo, todos os serviços ARP são encontrados no início deste capítulo. 

Existem inúmeros novos serviços no NetX Duo introduzidos para apoiar protocolos e operações baseados no IPv6. Os serviços com iPv6 na Net Duo têm o prefixo ***nxd,*** indicando que foram concebidos para o funcionamento de pilha dupla IPv4 e IPv6.

Os serviços existentes na NetX são totalmente suportados no NetX Duo. As aplicações NetX podem ser migradas para o NetX Duo com o mínimo esforço de porting.

> [!NOTE]
> *Note que uma API de tomada de BSD-Compatible está disponível para código de aplicação legado que não pode tirar o máximo partido do NetX Duo API de alto desempenho. Consulte o Apêndice D para obter mais informações sobre a API de tomada de BSD-Compatible*.

Na secção "Valores de Retorno" de cada descrição, os valores em **BOLD** não são afetados pela opção NX_DISABLE_ERROR_CHECKING utilizada para desativar a verificação de erros da API, enquanto os valores em não-negrito são completamente desativados. As secções "Allowed From" indicam a partir da qual cada serviço NetX Duo pode ser chamado.

## <a name="nx_arp_dynamic_entries_invalidate"></a>nx_arp_dynamic_entries_invalidate   
Invalidar todas as entradas dinâmicas na cache ARP

### <a name="prototype"></a>Prototype     

```c
UINT nx_arp_dynamic_entries_invalidate(NX_IP *ip_ptr);
```

### <a name="description"></a>Descrição   
Este serviço invalida todas as entradas dinâmicas de ARP atualmente na cache ARP.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Cache ARP bem sucedido invalida.
- **NX_NOT_ENABLED** (0x14) ARP não está ativado.
- **NX_PTR_ERROR** (0x07) Endereço IP inválido.
- **NX_CALLER_ERROR** (0x11) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de   
Fios

### <a name="preemption-possible"></a>Preempção Possível    
No

### <a name="example"></a>Exemplo

```c
/* Invalidate all dynamic entries in the ARP cache. */
status = nx_arp_dynamic_entries_invalidate(&ip_0);

/* If status is NX_SUCCESS the dynamic ARP entries were
   successfully invalidated. */
```
### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_dynamic_entry_set"></a>nx_arp_dynamic_entry_set  
Definir entrada dinâmica ARP

### <a name="prototype"></a>Prototype  

```c
UINT nx_arp_dynamic_entry_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);  
```

### <a name="description"></a>Descrição    
Este serviço atribui uma entrada dinâmica a partir da cache ARP e configura o IP especificado para o mapeamento de endereço físico. Se for especificado um endereço físico zero, é enviado um pedido real de ARP para a rede, a fim de ter o endereço físico resolvido. Note também que esta entrada será removida se o envelhecimento ARP estiver ativo ou se a cache ARP estiver esgotada e esta é a entrada ARP menos usada recentemente.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **ip_address** Endereço IP para mapa.
- **physical_msw** Top 16 bits (47-32) do endereço físico.
- **physical_lsw** Inferior 32 bits (31-0) do endereço físico.

### <a name="return-values"></a>Valores de devolução    

- **NX_SUCCESS** (0x00) Conjunto de entrada dinâmica ARP bem sucedida.
- **NX_NO_MORE_ENTRIES** (0x17) Não há mais entradas ARP disponíveis na cache ARP.
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IP inválido.
- **NX_PTR_ERROR** (0x07) Ponteiro de instância IP inválido.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de    
Fios

### <a name="preemption-possible"></a>Preempção Possível    
No

### <a name="example"></a>Exemplo

```c
/* Setup a dynamic ARP entry on the previously created IP
   Instance 0. */
status = nx_arp_dynamic_entry_set(&ip_0, IP_ADDRESS(1,2,3,4),
                                  0x1022, 0x1234);

/* If status is NX_SUCCESS, there is now a dynamic mapping between
   the IP address of 1.2.3.4 and the physical hardware address of
   10:22:00:00:12:34. */
```
### <a name="see-also"></a>Consulte também 

- nx_arp_dynamic_entries_invalidate
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_enable"></a>nx_arp_enable  
Ativar o Protocolo de Resolução de Endereços (ARP)

### <a name="prototype"></a>Prototype    

```c
UINT nx_arp_enable(
    NX_IP *ip_ptr, 
    VOID *arp_cache_memory,
    ULONG arp_cache_size);
```

### <a name="description"></a>Descrição

Este serviço inicializa o componente ARP da NetX Duo para a instância IP específica. A inicialização do ARP inclui a configuração da cache ARP e várias rotinas de processamento ARP necessárias para o envio e receção de mensagens ARP.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **arp_cache_memory** Ponteiro para a área de memória para colocar cache ARP.
- **arp_cache_size** Cada entrada ARP é de 52 bytes, o número total de entradas ARP é, portanto, o tamanho dividido por 52.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Ativar ARP com sucesso.
- **NX_PTR_ERROR** (0x07) IP inválido ou ponteiro de memória cache.
- **NX_SIZE_ERROR** (0x09) A memória de cache ARP fornecida pelo utilizador é demasiado pequena.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_ALREADY_ENABLED** (0x15) Este componente já foi ativado.

### <a name="allowed-from"></a>Permitido a partir de   
Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível  
No

### <a name="example"></a>Exemplo

```c
/* Enable ARP and supply 1024 bytes of ARP cache memory for
   previously created IP Instance ip_0. */
status = nx_arp_enable(&ip_0, (void *) pointer, 1024);

/* If status is NX_SUCCESS, ARP was successfully enabled for this IP
instance.*/
```
### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_entry_delete"></a>nx_arp_entry_delete   
Excluir uma entrada ARP

### <a name="prototype"></a>Prototype  

```c
UINT nx_arp_entry_delete(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```
### <a name="description"></a>Descrição

Este serviço remove uma entrada ARP para o endereço IP dado da sua tabela ARP interna IP.

### <a name="parameters"></a>Parâmetros  

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **ip_address** A entrada ARP com o endereço IP especificado deve ser eliminada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Ativar ARP com sucesso.
- **NX_ENTRY_NOT_FOUND** (0x16) Não é possível encontrar nenhuma entrada com o endereço IP especificado.
- **NX_PTR_ERROR** (0x07) IP inválido ou ponteiro de memória cache.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_IP_ADDRESS_ERROR** (0x21) O endereço IP especificado é inválido.

### <a name="allowed-from"></a>Permitido a partir de  
Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível  
No

### <a name="example"></a>Exemplo

```c
/* Delete the ARP entry with the IP address 1.2.3.4. */
status = nx_arp_entry_delete(&ip_0, IP_ADDRESS(1, 2, 3, 4));

/* If status is NX_SUCCESS, ARP entry with the specified IP address
   is deleted.*/
```

### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_gratuitous_send"></a>nx_arp_gratuitous_send   
Envie um pedido gratuito de ARP

### <a name="prototype"></a>Prototype  

```c
UINT nx_arp_gratuitous_send(
    NX_IP *ip_ptr,
    VOID (*response_handler)(NX_IP *ip_ptr, NX_PACKET *packet_ptr));
```                               
### <a name="description"></a>Descrição

Este serviço passa por todas as interfaces físicas para transmitir pedidos ARP gratuitos, desde que o endereço IP da interface seja válido. Se uma resposta ARP for posteriormente recebida, o manipulador de resposta fornecido é chamado para processar a resposta ao ARP gratuito.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **response_handler** Ponteiro para função de manuseamento de resposta. Se NX_NULL for fornecida, as respostas são ignoradas.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Enviado gratuito gratuito.
- **NX_NO_PACKET** (0x01) Nenhum pacote disponível.
- **NX_NOT_ENABLED** (0x14) ARP não está ativado.
- **NX_IP_ADDRESS_ERROR** (0x21) O endereço IP atual é inválido.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```
/* Send gratuitous ARP without any response handler. */
status = nx_arp_gratuitous_send(&ip_0, NX_NULL);

/* If status is NX_SUCCESS the gratuitous ARP was successfully
   sent. */
```

### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_hardware_address_find"></a>nx_arp_hardware_address_find
Localizar endereço de hardware físico dado um endereço IP

### <a name="prototype"></a>Prototype  

```c
UINT nx_arp_hardware_address_find(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG *physical_msw,
    ULONG *physical_lsw);
```
### <a name="description"></a>Descrição

Este serviço tenta encontrar um endereço de hardware físico na cache ARP que esteja associado ao endereço IP fornecido.

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **ip_address** Endereço IP para procurar.
- **physical_msw** Ponteiro para a variável para devolver os 16 bits superiores (47-32) do endereço físico.
- **physical_lsw** Ponteiro para a variável para devolver os 32 bits inferiores (31-0) do endereço físico.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Bem sucedido no endereço de hardware ARP.
- **NX_ENTRY_NOT_FOUND** (0x16) O mapeamento não foi encontrado na cache ARP.
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IP inválido.
- **NX_PTR_ERROR** (0x07) IP inválido ou ponteiro de memória.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Search for the hardware address associated with the IP address of
   1.2.3.4 in the ARP cache of the previously created IP
   Instance 0. */
status = nx_arp_hardware_address_find(&ip_0, IP_ADDRESS(1,2,3,4),
                                      &physical_msw,
                                      &physical_lsw);

/* If status is NX_SUCCESS, the variables physical_msw and
   physical_lsw contain the hardware address.*/
```   
### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_info_get"></a>nx_arp_info_get
Recuperar informações sobre atividades de ARP

### <a name="prototype"></a>Prototype  

```c
UINT nx_arp_info_get(
    NX_IP *ip_ptr,
    ULONG *arp_requests_sent,
    ULONG *arp_requests_received,
    ULONG *arp_responses_sent,
    ULONG *arp_responses_received,
    ULONG *arp_dynamic_entries,
    ULONG *arp_static_entries,
    ULONG *arp_aged_entries,
    ULONG *arp_invalid_messages);
```

### <a name="description"></a>Descrição

Este serviço obtém informações sobre as atividades ARP para a instância IP associada.

> [!NOTE]
> *Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao chamador*.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **arp_requests_sent** Ponteiro para destino para o total de pedidos de ARP enviados a partir desta instância IP.
- **arp_requests_received** Ponteiro para destino para o total de pedidos de ARP recebidos da rede.
- **arp_responses_sent** Ponteiro para destino para o total de respostas ARP enviadas a partir desta instância IP.
- **arp_responses_received** Ponteiro para o destino para o total de respostas ARP recebidas da rede.
- **arp_dynamic_entries** Ponteiro para o destino para o número atual de entradas dinâmicas de ARP.
- **arp_static_entries** Ponteiro para o destino para o número atual de entradas estáticas de ARP.
- **arp_aged_entries** Ponteiro para o destino do número total de entradas ARP que envelheceram e se tornaram inválidas.
- **arp_invalid_messages** Ponteiro para o destino das mensagens ARP inválidas totais recebidas.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Recuperação de informações ARP bem sucedidas.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Pickup ARP information for ip_0. */
status = nx_arp_info_get(&ip_0, &arp_requests_sent,
                         &arp_requests_received,
                         &arp_responses_sent,
                         &arp_responses_received,
                         &arp_dynamic_entries,
                         &arp_static_entries,
                         &arp_aged_entries,
                         &arp_invalid_messages);

/* If status is NX_SUCCESS, the ARP information has been stored in
   the supplied variables. */
```
### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_ip_address_find"></a>nx_arp_ip_address_find
Localizar endereço IP dado um endereço físico

### <a name="prototype"></a>Prototype  

```c
UINT nx_arp_ip_address_find(
    NX_IP *ip_ptr, 
    ULONG *ip_address,
    ULONG physical_msw, 
    ULONG physical_lsw);
```
### <a name="description"></a>Descrição

Este serviço tenta encontrar um endereço IP na cache ARP que esteja associado ao endereço físico fornecido.

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **ip_address** Ponteiro para devolver o endereço IP, se for encontrado um que tenha sido mapeado.
- **physical_msw** Top 16 bits (47-32) do endereço físico para procurar.
- **physical_lsw** Menos 32 bits (31-0) do endereço físico para procurar.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Sucesso do endereço IP 
- **NX_ENTRY_NOT_FOUND** (0x16) O mapeamento não foi encontrado na cache ARP.
- **NX_PTR_ERROR** (0x07) IP inválido ou ponteiro de memória.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.
- **NX_INVALID_PARAMETERS** (0x4D) Physical_msw e physical_lsw são 0.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Search for the IP address associated with the hardware address of
   0x0:0x01234 in the ARP cache of the previously created IP
   Instance ip_0. */
status = nx_arp_ip_address_find(&ip_0, &ip_address, 0x0, 0x1234);

/* If status is NX_SUCCESS, the variables ip_address contains the
   associated IP address. */
```
### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_static_entries_delete"></a>nx_arp_static_entries_delete
Eliminar todas as entradas estáticas de ARP

### <a name="prototype"></a>Prototype  

```c
UINT nx_arp_static_entries_delete(NX_IP *ip_ptr);
```

### <a name="description"></a>Descrição

Este serviço elimina todas as entradas estáticas na cache ARP.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) As entradas estáticas são eliminadas.
- **NX_PTR_ERROR** (0x07) Ponteiro ip_ptr Inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Delete all the static ARP entries for IP Instance 0, assuming
   "ip_0" is the NX_IP structure for IP Instance 0. */
status = nx_arp_static_entries_delete(&ip_0);

/* If status is NX_SUCCESS all static ARP entries in the ARP cache
   have been deleted. */
```
### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_static_entry_create"></a>nx_arp_static_entry_create
Criar IP estático para mapeamento de hardware em cache ARP

### <a name="prototype"></a>Prototype  

```c
UINT nx_arp_static_entry_create(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```
### <a name="description"></a>Descrição

Este serviço cria um mapeamento de endereço ip-físico estático na cache ARP para a instância IP especificada. As entradas ARP estáticas não estão sujeitas a atualizações periódicas ARP.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **ip_address** Endereço IP para mapa.
- **physical_msw** Top 16 bits (47-32) do endereço físico para mapear.
- **physical_lsw** Inferior 32 bits (31-0) do endereço físico para mapear.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Entrada estática bem sucedida da ARP cria.
- **NX_NO_MORE_ENTRIES** (0x17) Não há mais entradas ARP disponíveis na cache ARP.
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IP inválido.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.
- **NX_INVALID_PARAMETERS** (0x4D) Physical_msw e physical_lsw são 0.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Create a static ARP entry on the previously created IP
   Instance 0. */
status = nx_arp_static_entry_create(&ip_0, IP_ADDRESS(1,2,3,4),
                                    0x0, 0x1234);

/* If status is NX_SUCCESS, there is now a static mapping between
   the IP address of 1.2.3.4 and the physical hardware address of
   0x00:0x1234. */
```
### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_static_entry_delete"></a>nx_arp_static_entry_delete 
Elimine IP estático para mapeamento de hardware em cache ARP

### <a name="prototype"></a>Prototype  

```c
UINT nx_arp_static_entry_delete(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```
### <a name="description"></a>Descrição

Este serviço encontra e elimina um mapeamento de endereço ip-físico previamente criado na cache ARP para a instância IP especificada.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **ip_address** Endereço IP que foi mapeado estáticamente.
- **physical_msw** Top 16 bits (47 - **32) do endereço físico que foi mapeado estáticamente.
- **physical_lsw** Inferior 32 bits (31 - **0) do endereço físico que foi mapeado estáticamente.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Entrada estática bem sucedida da ARP.
- **NX_ENTRY_NOT_FOUND** (0x16) A entrada estática ARP não foi encontrada na cache ARP.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IP inválido.
- **NX_INVALID_PARAMETERS** (0x4D) Physical_msw e physical_lsw são 0.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Delete a static ARP entry on the previously created IP
   instance ip_0. */
status = nx_arp_static_entry_delete(&ip_0, IP_ADDRESS(1,2,3,4),
                                    0x0, 0x1234);

/* If status is NX_SUCCESS, the previously created static ARP entry
   was successfully deleted. */
```
### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_icmp_enable"></a>nx_icmp_enable
Ativar o Protocolo de Mensagens de Controlo de Internet (ICMP)

### <a name="prototype"></a>Prototype  

```c
UINT nx_icmp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descrição

Este serviço permite o componente ICMP para a instância IP especificada. O componente ICMP é responsável pelo tratamento de mensagens de erro da Internet e pedidos e respostas de ping. 

> [!IMPORTANT]  
> *Este serviço apenas permite o ICMP para o serviço IPv4. Para permitir tanto o ICMPv4 como o ICMPv6, as aplicações devem utilizar o serviço **nxd_icmp_enable***.

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro para instância IP previamente criada.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) ICMP bem sucedido.
- **NX_ALREADY_ENABLED** (0x15) ICMP já está habilitado.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Enable ICMP on the previously created IP Instance ip_0. */
status = nx_icmp_enable(&ip_0);

/* If status is NX_SUCCESS, ICMP is enabled. */
```
### <a name="see-also"></a>Consulte também

- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nx_icmp_info_get"></a>nx_icmp_info_get
Recuperar informações sobre atividades do ICMP

### <a name="prototype"></a>Prototype  

```c
UINT nx_icmp_info_get(
    NX_IP *ip_ptr,
    ULONG *pings_sent,
    ULONG *ping_timeouts,
    ULONG *ping_threads_suspended,
    ULONG *ping_responses_received,
    ULONG *icmp_checksum_errors,
    ULONG *icmp_unhandled_messages);
```
### <a name="description"></a>Descrição

Este serviço obtém informações sobre as atividades do ICMP para a instância IP especificada.

> [!NOTE]  
> *Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao chamador*.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **pings_sent** Ponteiro para o destino para o número total de pings enviados.
- **ping_timeouts** Ponteiro para o destino para o número total de intervalos de ping.
- **ping_threads_suspended** Ponteiro para o destino do número total de fios suspensos em pedidos de ping.
- **ping_responses_received** Ponteiro para o destino do número total de respostas de ping recebidas.
- **icmp_checksum_errors** Ponteiro para o destino do número total de erros de verificação ICMP.
- **icmp_unhandled_messages** Ponteiro para o destino do número total de mensagens ICMP não manuseadas.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Recuperação de informação bem sucedida do ICMP.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Retrieve ICMP information from previously created IP
   instance ip_0. */
status = nx_icmp_info_get(&ip_0, &pings_sent, &ping_timeouts,
                          &ping_threads_suspended,
                          &ping_responses_received,
                          &icmp_checksum_errors,
                          &icmp_unhandled_messages);
/* If status is NX_SUCCESS, ICMP information was retrieved. */
```
### <a name="see-also"></a>Consulte também

- nx_icmp_enable
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nx_icmp_ping"></a>nx_icmp_ping  
Enviar pedido de ping para endereço IP especificado

### <a name="prototype"></a>Prototype  

```c
UINT nx_icmp_ping(
    NX_IP *ip_ptr,
    ULONG ip_address,
    CHAR *data, ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Descrição

Este serviço envia um pedido de ping para o endereço IP especificado e aguarda o tempo especificado para uma mensagem de resposta a ping. Se não for recebida qualquer resposta, um erro é devolvido. Caso contrário, toda a mensagem de resposta é devolvida na variável apontada por response_ptr. 

Para enviar um pedido de ping para um destino IPv6, as aplicações devem utilizar o serviço ***nxd_icmp_ping** _ ou _ *_nxd_icmp_source_ping_** .

> [!WARNING]  
> *Se NX_SUCCESS for devolvido, o pedido é responsável pela libertação do pacote recebido depois de já não ser necessário*.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **ip_address** Endereço IP, em ordem de anfitrião byte, para ping.
- **dados** Ponteiro para a área de dados para mensagem de ping.
- **data_size** Número de bytes nos dados do ping
- **response_ptr** Ponteiro para o ponteiro do pacote para devolver a mensagem de resposta do ping dentro
- **wait_option** Define o número de carraças do temporizador ThreadX para aguardar uma resposta de ping. As opções de espera são definidas da seguinte forma:

| Opção de Espera            | Valor                           |
| -----------------------|---------------------------------|
| NX_NO_WAIT             | (0x00000000)                    |
| valor de tempo limite em carrapatos | (0x00000001 através de 0xFFFFFFFE) |
| NX_WAIT_FOREVER        | 0xFFFFFFFF                      |

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Ping de sucesso. O ponteiro da mensagem de resposta foi colocado na variável apontada por response_ptr.
- **NX_NO_PACKET** (0x01) Incapaz de atribuir um pacote de pedido de ping.
- **NX_OVERFLOW** (0x03) Área de dados especificada excede o tamanho do pacote padrão para esta instância IP.
- **NX_NO_RESPONSE** (0x29) A IP solicitada não respondeu.
- **NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IP inválido.
- **NX_PTR_ERROR** (0x07) IP inválido ou ponteiro de resposta.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Issue a ping to IP address 1.2.3.5 from the previously created IP
   Instance ip_0. */
status = nx_icmp_ping(&ip_0, IP_ADDRESS(1,2,3,5), "abcd", 4,
                      &response_ptr, 10);

/* If status is NX_SUCCESS, a ping response was received from IP
   address 1.2.3.5 and the response packet is contained in the
   packet pointed to by response_ptr. It should have the same "abcd"
   four bytes of data. */
```
### <a name="see-also"></a>Consulte também

- nx_icmp_enable
- nx_icmp_info_get
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nx_igmp_enable"></a>nx_igmp_enable
Ativar o Protocolo de Gestão do Grupo de Internet (IGMP)

### <a name="prototype"></a>Prototype  

```c
UINT nx_igmp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descrição

Este serviço permite o componente IGMP na instância IP especificada. A componente IGMP é responsável por fornecer suporte para operações de gestão de grupos multicast IP.

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro para instância IP previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) IGMP bem sucedido.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_ALREADY_ENABLED** (0x15) Este componente já foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Enable IGMP on the previously created IP Instance ip_0. */
status = nx_igmp_enable(&ip_0);

/* If status is NX_SUCCESS, IGMP is enabled. */
```
### <a name="see-also"></a>Consulte também

- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_info_get"></a>nx_igmp_info_get
Recuperar informações sobre atividades do IGMP

### <a name="prototype"></a>Prototype  

```c
UINT nx_igmp_info_get(
    NX_IP *ip_ptr,
    ULONG *igmp_reports_sent,
    ULONG *igmp_queries_received,
    ULONG *igmp_checksum_errors,
    ULONG *current_groups_joined);
```
### <a name="description"></a>Descrição

Este serviço obtém informações sobre as atividades do IGMP para a instância IP especificada.

> [!IMPORTANT]  
> *Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao chamador*.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **igmp_reports_sent** Ponteiro para o destino para o número total de relatórios do ICMP enviados.
- **igmp_queries_received** Ponteiro para destino para o número total de consultas recebidas pelo router multicast.
- **igmp_checksum_errors** Ponteiro para o destino do número total de erros de verificação IGMP em pacotes de receção.
- **current_groups_joined** Ponteiro para o destino do número atual de grupos unidos através desta instância IP.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Recuperação de informações bem sucedidas do IGMP.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Retrieve IGMP information from previously created IP Instance ip_0. */
status = nx_igmp_info_get(&ip_0, &igmp_reports_sent,
                          &igmp_queries_received,
                          &igmp_checksum_errors,
                          &current_groups_joined);

/* If status is NX_SUCCESS, IGMP information was retrieved. */
```

### <a name="see-also"></a>Consulte também

- nx_igmp_enable
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_loopback_disable"></a>nx_igmp_loopback_disable
Desativar o loopback IGMP

### <a name="prototype"></a>Prototype  

```c
UINT nx_igmp_loopback_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descrição

Este serviço desativa o loopback IGMP para todos os grupos multicasts subsequentes.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Desativação de loopback IGMP bem sucedida.
- **NX_NOT_ENABLED** (0x14) IGMP não está ativado.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Caller não é um fio ou inicialização.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Disable IGMP loopback for all subsequent multicast groups
   joined. */
status = nx_igmp_loopback_disable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is disabled. */
```
### <a name="see-also"></a>Consulte também

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_loopback_enable"></a>nx_igmp_loopback_enable
Ativar o loopback IGMP

### <a name="prototype"></a>Prototype  

```c
UINT nx_igmp_loopback_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descrição

Este serviço permite o loopback IGMP para todos os grupos multicasts subsequentes.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Desativação de loopback IGMP bem sucedida.
- **NX_NOT_ENABLED** (0x14) IGMP não está ativado.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Caller não é um fio ou inicialização.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Enable IGMP loopback for all subsequent multicast
   groups joined. */
status = nx_igmp_loopback_enable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is enabled. */
```
### <a name="see-also"></a>Consulte também

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_interface_join"></a>nx_igmp_multicast_interface_join
Junte a instância IP a grupo multicast especificado através de uma interface

### <a name="prototype"></a>Prototype  

```c
UINT nx_igmp_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>Descrição

Este serviço junta-se a uma instância IP ao grupo multicast especificado através de uma interface de rede especificada. Mantém-se um contador interno para acompanhar o número de vezes que o mesmo grupo foi acompanhado. Depois de se juntar ao grupo multicast, o componente IGMP permitirá a receção de pacotes IP com este endereço de grupo através da interface de rede especificada e também reportará aos routers que este IP é membro deste grupo multicast. A adesão ao IGMP junta-se, reporta e deixa as mensagens também são enviadas através da interface de rede especificada. Para aderir a um grupo multicast IPv4 sem enviar o relatório de adesão ao grupo IGMP, a aplicação utilizará o serviço ***nx_ipv4_multicast_interface_join***.

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **group_address** Endereço de grupo multicast classe D IP para se juntar na ordem byte de anfitrião.
- **interface_index** Índice da Interface ligado à instância NetX Duo.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Grupo multicast bem sucedido.
- **NX_NO_MORE_ENTRIES** (0x17) Não podem ser acompanhados mais grupos multicast, o máximo excedido.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_INVALID_INTERFACE** (0x4C) Índice de dispositivo aponta para uma interface de rede inválida.
- **NX_IP_ADDRESS_ERROR** endereço de grupo multicast fornecido (0x21) não é um endereço de classe D válido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** suporte multicast IP (0x14) não está ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Previously created IP Instance joins the multicast group
   244.0.0.200, via the interface at index 1 in the IP interface
   list. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_join
                                 (&ip IP_ADDRESS(244,0,0,200),
                                  INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
   the multicast group. */
```   
### <a name="see-also"></a>Consulte também

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_interface_leave"></a>nx_igmp_multicast_interface_leave
Deixe o grupo multicast especificado através de uma interface

### <a name="prototype"></a>Prototype  

```c
UINT nx_igmp_multicast_interface_leave(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>Descrição

Este serviço deixa o grupo multicast especificado através de uma interface de rede especificada. Mantém-se um contador interno para acompanhar o número de vezes que o mesmo grupo tem sido membro. Após deixar o grupo multicast, o componente IGMP enviará o relatório de adesão adequado, e poderá sair do grupo se não houver membros deste nó. Para deixar um grupo multicast IPv4 sem enviar o relatório de adesão ao grupo IGMP, o pedido deve utilizar o serviço ***nx_ipv4_multicast_interface_leave***.

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **group_address** Endereço de grupo multicast ip classe D para sair. O endereço IP está em ordem de acolhimento.
- **interface_index** Índice da Interface ligado à instância NetX Duo.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Grupo multicast bem sucedido.
- **NX_ENTRY_NOT_FOUND** (0x16) O endereço de grupo multicast especificado não pode ser encontrado na tabela multicast local.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_INVALID_INTERFACE** (0x4C) Índice de dispositivo aponta para uma interface de rede inválida.
- **NX_IP_ADDRESS_ERROR** endereço de grupo multicast fornecido (0x21) não é um endereço de classe D válido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** suporte multicast IP (0x14) não está ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Leave the multicast group 244.0.0.200. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_leave
                                (&ip IP_ADDRESS(244,0,0,200),
                                 INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully leaves
   the multicast group 244.0.0.200. */
```
### <a name="see-also"></a>Consulte também

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_join"></a>nx_igmp_multicast_join
Junte-se à instância IP para grupo multicast especificado

### <a name="prototype"></a>Prototype  

```c
UINT nx_igmp_multicast_join(
    NX_IP *ip_ptr, 
    ULONG group_address);
```
### <a name="description"></a>Descrição

Este serviço junta-se a uma instância IP ao grupo multicast especificado. Mantém-se um contador interno para acompanhar o número de vezes que o mesmo grupo foi acompanhado. O condutor é ordenado a enviar um relatório IGMP se este for o primeiro pedido de junção na rede indicando a intenção do anfitrião de se juntar ao grupo. Após a adesão, o componente IGMP permitirá a receção de pacotes IP com este endereço de grupo e informará aos routers que este IP é membro deste grupo multicast. Para aderir a um grupo multicast IPv4 sem enviar o relatório de adesão ao grupo IGMP, a aplicação utilizará o serviço ***nx_ipv4_multicast_interface_join***.

> [!NOTE]  
> *Para se juntar a um grupo multicast num dispositivo não primário, utilize o **serviço nx_igmp_multicast_interface_join.***

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **group_address** Endereço de grupo multicast classe D IP para aderir.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Grupo multicast bem sucedido.
- **NX_NO_MORE_ENTRIES** (0x17) Não podem ser acompanhados mais grupos multicast, o máximo excedido.
- **NX_INVALID_INTERFACE** (0x4C) Índice de dispositivo aponta para uma interface de rede inválida.
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço de grupo IP inválido.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Previously created IP Instance ip_0 joins the multicast group
   224.0.0.200. */
status = nx_igmp_multicast_join(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully
   joined the multicast group 224.0.0.200. */
```
### <a name="see-also"></a>Consulte também

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_leave"></a>nx_igmp_multicast_leave
Fazer com que a instância IP deixe o grupo multicast especificado

### <a name="prototype"></a>Prototype  

```c
UINT nx_igmp_multicast_leave(
    NX_IP *ip_ptr, 
    ULONG group_address);
```
### <a name="description"></a>Descrição

Este serviço faz com que uma instância IP saia do grupo multicast especificado, se o número de equestres de licença corresponder ao número de pedidos de aderi. Caso contrário, a contagem interna de juntas é simplesmente decrementeda. Para deixar um grupo multicast IPv4 sem enviar o relatório de adesão ao grupo IGMP, o pedido deve utilizar o serviço ***nx_ipv4_multicast_interface_leave***.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **group_address** Grupo multicast para sair.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Grupo multicast bem sucedido.
- **NX_ENTRY_NOT_FOUND** (0x16) Não foi encontrado o pedido de aderião anterior.
- **NX_INVALID_INTERFACE** (0x4C) Índice de dispositivo aponta para uma interface de rede inválida.
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço de grupo IP inválido.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Cause IP instance to leave the multicast group 224.0.0.200. */
status = nx_igmp_multicast_leave(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully left
   the multicast group 224.0.0.200. */
```
### <a name="see-also"></a>Consulte também

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_ip_address_change_notifiy"></a>nx_ip_address_change_notifiy
Notifique a aplicação se o endereço IP mudar

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_address_change_notify(
    NX_IP *ip_ptr,
    VOID(*change_notify)(NX_IP *, VOID *),
    VOID *additional_info);
```
### <a name="description"></a>Descrição

Este serviço regista uma função de notificação de aplicação que é chamada sempre que o endereço IPv4 é alterado.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **change_notify** Ponteiro para função de notificação de alteração IP. Se este parâmetro for NX_NULL, a notificação de alteração de endereço IP é desativada.
- **additional_info** Ponteiro para informações adicionais opcionais que também são fornecidas à função de notificação quando o endereço IP é alterado.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Notificação de alteração de endereço IP bem sucedida.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Register the function "my_ip_changed" to be called whenever the
   IP address is changed. */
status = nx_ip_address_change_notify(&ip_0, my_ip_changed,
                                      NX_NULL);

/* If status is NX_SUCCESS, the "my_ip_changed" function will be
   called whenever the IP address changes. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_address_get"></a>nx_ip_address_get
Recuperar endereço IPv4 e máscara de rede

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_address_get(
    NX_IP *ip_ptr,
    ULONG *ip_address,
    ULONG *network_mask);
```
### <a name="description"></a>Descrição

Este serviço recupera o endereço IPv4 e a sua máscara de sub-rede da interface de rede primária.

> [!IMPORTANT]   
> *Para obter informações sobre o dispositivo secundário, utilize o serviço **nx_ip_interface_address_get****.

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **ip_address** Ponteiro para destino para endereço IP.
- **network_mask** Ponteiro para destino para máscara de rede.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) endereço IP bem sucedido obtém.
- **NX_PTR_ERROR** (0x07) IP inválido ou ponteiro variável de retorno.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Get the IP address and network mask from the previously created
   IP Instance ip_0. */
status = nx_ip_address_get(&ip_0, &ip_address, &network_mask);

/* If status is NX_SUCCESS, the variables ip_address and
   network_mask contain the IP and network mask respectively. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_address_set"></a>nx_ip_address_set
Definir endereço IPv4 e máscara de rede

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_address_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG network_mask);
```
### <a name="description"></a>Descrição

Este serviço define o endereço IPv4 e a máscara de rede para a interface de rede primária.

> [!IMPORTANT]  
> *Para definir o endereço IP e a máscara de rede para o dispositivo secundário, utilize o serviço **nx_ip_interface_address_set****.

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **ip_address** Novo endereço IP.
- **network_mask** Nova máscara de rede.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) conjunto de endereços IP bem sucedidos.
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IP inválido.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Set the IP address and network mask to 1.2.3.4 and 0xFFFFFF00 for
   the previously created IP Instance ip_0. */
status = nx_ip_address_set(&ip_0, IP_ADDRESS(1,2,3,4),
                           0xFFFFFF00UL);

/* If status is NX_SUCCESS, the IP instance now has an IP address of
   1.2.3.4 and a network mask of 0xFFFFFF00. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_auxiliary_packet_pool_set"></a>nx_ip_auxiliary_packet_pool_set
Configure uma piscina de pacotes auxiliares

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_auxiliary_packet_pool_set(
    NX_IP *ip_ptr,
    NX_PACKET_POOL *aux_pool);
```
### <a name="description"></a>Descrição

Este serviço configura uma piscina de pacotes auxiliares na instância IP. Para um sistema limitado à memória, o utilizador pode aumentar a eficiência da memória criando o conjunto de pacotes predefinidos com o tamanho do pacote de MTU, e criando uma piscina de pacotes auxiliares com tamanho de pacote menor para o fio IP para transmitir pequenos pacotes com. O tamanho recomendado do pacote para a piscina auxiliar é de 256 bytes, assumindo que o IPv6 e o IPsec estão ambos ativados.

Por predefinição, a instância IP não aceita o conjunto de pacotes auxiliares. Para ativar esta funcionalidade, *NX_DUAL_PACKET_POOL_ENABLE* devem ser definidas ao compilar a biblioteca NetX Duo.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **aux_pool** A piscina de pacotes auxiliares a configurar para a instância IP.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) conjunto de endereços IP bem sucedidos.
- **NX_NOT_SUPPORTED** (0x4B) A função de piscina de pacotes duplos não é compilada na biblioteca.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido ou ponteiro de piscina.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível  

No

### <a name="example"></a>Exemplo

```c
#define SMALL_PAYLOAD_SIZE 256
NX_PACKET small_pool;

nx_packet_pool_create(&small_pool, "small pool", SMALL_PAYLOAD_SIZE,
                       small_pool_memory_ptr, small_pool_size);

/* Add the small packet pool to the IP instance. */
status = nx_ip_auxiliary_packet_pool_set(&ip_0, &small_pool);

/* If status is NX_SUCCESS, the IP instance now is able to use the
   small pool for transmitting small datagram. */
```
### <a name="see-also"></a>Consulte também

- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_ip_create"></a>nx_ip_create
Criar uma instância IP

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_create(
    NX_IP *ip_ptr, 
    CHAR *name, ULONG ip_address,
    ULONG network_mask, 
    NX_PACKET_POOL *default_pool,
    VOID (*ip_network_driver)(NX_IP_DRIVER *),
    VOID *memory_ptr, 
    ULONG memory_size,
    UINT priority);
```
### <a name="description"></a>Descrição

Este serviço cria uma instância IP com o endereço IP fornecido pelo utilizador e o controlador de rede. Além disso, a aplicação deve fornecer um conjunto de pacotes previamente criado para a instância IP para usar para a atribuição interna de pacotes. Note que o controlador de rede de aplicações fornecido não é chamado até que o fio deste IP seja executado.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para bloquear para criar uma nova instância IP.
- **nome** Nome deste novo exemplo de IP.
- **ip_address** Endereço IP para este novo exemplo de IP.
- **network_mask** Máscara para delinear a parte da rede do endereço IP para utilizações de sub-redes e super-redes.
- **default_pool** Ponteiro para o bloco de controlo da piscina de pacotes NetX Duo anteriormente criada.
- **ip_network_driver** Controlador de rede fornecido pelo utilizador utilizado para enviar e receber pacotes IP.
- **memory_ptr** Ponteiro para a área de memória para a área de pilha do ajudante IP.
- **memory_size** Número de bytes na área de memória para a pilha do fio do ajudante IP.
- **prioridade** Prioridade do fio do ajudante ip.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) criação de instância IP bem sucedida.
- **NX_NOT_IMPLEMENTED** (0x4A) a biblioteca NetX Duo está configurada incorretamente.
- **NX_PTR_ERROR** (0x07) IP inválido, ponteiro de função do controlador de rede, piscina de pacotes ou ponteiro de memória.
- **NX_SIZE_ERROR** (0x09) O tamanho da pilha fornecida é demasiado pequeno.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_IP_ADDRESS_ERROR** (0x21) O endereço IP fornecido é inválido.
- **NX_OPTION_ERROR** (0x21) A prioridade fornecida do fio IP é inválida.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Create an IP instance with an IP address of 1.2.3.4 and a network
   mask of 0xFFFFFF00UL. The "ethernet_driver" specifies the entry
   point of the application specific network driver and the
   "stack_memory_ptr" specifies the start of a 1024 byte memory
   area that is used for this IP instance’s helper thread. */
status = nx_ip_create(&ip_0, "NetX IP Instance ip_0",
                      IP_ADDRESS(1, 2, 3, 4),
                      0xFFFFFF00UL, &pool_0, ethernet_driver,
                      stack_memory_ptr, 1024, 1);

/* If status is NX_SUCCESS, the IP instance has been created. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_delete"></a>nx_ip_delete
Eliminar instância IP previamente criada

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_delete(NX_IP *ip_ptr);
```
### <a name="description"></a>Descrição

Este serviço elimina uma instância IP previamente criada e liberta todos os recursos do sistema detidos pela instância IP.

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro para instância IP previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Eliminação IP bem sucedida.
- **NX_SOCKETS_BOUND** (0x28) Este caso IP ainda tem tomadas UDP ou TCP ligadas a ele. Todas as tomadas devem ser desvinculados e eliminadas antes de eliminar a instância IP.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

Sim

### <a name="example"></a>Exemplo

```c
/* Delete a previously created IP instance. */
status = nx_ip_delete(&ip_0);

/* If status is NX_SUCCESS, the IP instance has been deleted. */
```

### <a name="see-also"></a>Consulte também 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_driver_direct_command"></a>nx_ip_driver_direct_command
Emitir comando ao controlador de rede

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_driver_direct_command
    (NX_IP *ip_ptr,
    UINT command,
    ULONG *return_value_ptr);
```
### <a name="description"></a>Descrição

Este serviço fornece uma interface direta ao controlador de interface de rede primária da aplicação especificado durante a ***chamada nx_ip_create.*** Os comandos específicos da aplicação podem ser utilizados desde que o seu valor numérico seja superior ou igual a NX_LINK_USER_COMMAND.

> [!IMPORTANT]  
> *Para emitir comando para o dispositivo secundário, utilize o serviço **nx_ip_driver_interface_direct_command***.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **comando** Código de comando numérico. Os comandos padrão são definidos da seguinte forma:
    - NX_LINK_GET_STATUS (10)
    - NX_LINK_GET_SPEED (11)
    - NX_LINK_GET_DUPLEX_TYPE (12)
    - NX_LINK_GET_ERROR_COUNT (13)
    - NX_LINK_GET_RX_COUNT (14)
    - NX_LINK_GET_TX_COUNT (15)
    - NX_LINK_GET_ALLOC_ERRORS (16)
    - NX_LINK_USER_COMMAND (50)
- **return_value_ptr** Ponteiro para devolver variável no chamador.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Comando direto do controlador de rede bem sucedido.
- **NX_UNHANDLED_COMMAND** (0x44) Comando do controlador de rede não manuseado ou não simplificado.
- **NX_PTR_ERROR** (0x07) IP inválido ou ponteiro de valor de retorno.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_INVALID_INTERFACE** (0x4C) Índice de interface inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Make a direct call to the application-specific network driver
   for the previously created IP instance. For this example, the
   network driver is interrogated for the link status. */
status = nx_ip_driver_direct_command(&ip_0, NX_LINK_GET_STATUS,
                                     &link_status);

/* If status is NX_SUCCESS, the link_status variable contains a
   NX_TRUE or NX_FALSE value representing the status of the
   physical link. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_driver_interface_direct_command"></a>nx_ip_driver_interface_direct_command
Emitir comando ao controlador de rede

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_driver_interface_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    UINT interface_index,
    ULONG *return_value_ptr);
```
### <a name="description"></a>Descrição

Este serviço fornece um comando direto ao controlador de dispositivo de rede da aplicação na instância IP. Os comandos específicos da aplicação podem ser utilizados desde que o seu valor numérico seja superior ou igual a *NX_LINK_USER_COMMAND*.

### <a name="parameters"></a>Parâmetros  

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **comando** Código de comando numérico. Os comandos padrão são definidos da seguinte forma:
    - NX_LINK_GET_STATUS (10)
    - NX_LINK_GET_SPEED (11)
    - NX_LINK_GET_DUPLEX_TYPE (12)
    - NX_LINK_GET_ERROR_COUNT (13)
    - NX_LINK_GET_RX_COUNT (14)
    - NX_LINK_GET_TX_COUNT (15)
    - NX_LINK_GET_ALLOC_ERRORS (16)
    - NX_LINK_USER_COMMAND (50)
- **interface_index** Índice da interface de rede para o que o comando deve ser enviado.
- **return_value_ptr** Ponteiro para devolver variável no chamador.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Comando direto do controlador de rede bem sucedido.
- **NX_UNHANDLED_COMMAND** (0x44) Comando do controlador de rede não manuseado ou não simplificado.
- **NX_INVALID_INTERFACE** (0x4C) Índice de interface inválido
- **NX_PTR_ERROR** (0x07) IP inválido ou ponteiro de valor de retorno.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Make a direct call to the application-specific network driver
   for the previously created IP instance. For this example, the
   network driver is interrogated for the link status. */

/* Set the interface index to the primary device. */
UINT interface_index = 0;

status = nx_ip_driver_interface_direct_command(&ip_0,
                                               NX_LINK_GET_STATUS,
                                               interface_index,
                                               &link_status);

/* If status is NX_SUCCESS, the link_status variable contains a
   NX_TRUE or NX_FALSE value representing the status of the
   physical link. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_forwarding_disable"></a>nx_ip_forwarding_disable  
Desativar o encaminhamento do pacote IP

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_forwarding_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descrição

Este serviço desativa o encaminhamento de pacotes IP dentro do componente IP NetX Duo. Na criação da tarefa IP, este serviço é automaticamente desativado.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Desativação de IP bem sucedida.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores

### <a name="preemption-possible"></a>Preempção Possível  

No

### <a name="example"></a>Exemplo

```c
/* Disable IP forwarding on this IP instance. */
status = nx_ip_forwarding_disable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been disabled on the
   previously created IP instance. */
```
### <a name="see-also"></a>Consulte também  

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_forwarding_enable"></a>nx_ip_forwarding_enable
Ativar o encaminhamento de pacotes IP

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_forwarding_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descrição

Este serviço permite reencaminhar pacotes IP dentro do componente NetX Duo IP. Na criação da tarefa IP, este serviço é automaticamente desativado.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Ativação de encaminhamento IP bem sucedido.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Enable IP forwarding on this IP instance. */
status = nx_ip_forwarding_enable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been enabled on the
   previously created IP instance. */
```
### <a name="see-also"></a>Consulte também 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_fragment_disable"></a>nx_ip_fragment_disable
Desativar a fragmentação do pacote IP

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_fragment_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descrição

Este serviço desativa a fragmentação e a funcionalidade de fragmentação e remontagem do pacote IPv4 e IPv6. Para pacotes à espera de serem remontados, este serviço liberta estes pacotes. Na criação da tarefa IP, este serviço é automaticamente desativado.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Desativação de fragmentos IP bem sucedidos.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) A fragmentação ip não está ativada na instância IP.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Disable IP fragmenting on this IP instance. */
status = nx_ip_fragment_disable(&ip_0);

/* If status is NX_SUCCESS, disables IP fragmenting on the
   previously created IP instance. */
```

### <a name="see-also"></a>Consulte também  

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_fragment_enable"></a>nx_ip_fragment_enable
Ativar a fragmentação do pacote IP

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_fragment_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descrição

Este serviço permite a fragmentação e montagem de pacotes IPv4 e IPv6. Na criação da tarefa IP, este serviço é automaticamente desativado.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Ativar o fragmento IP bem sucedido.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) As características de fragmentação IP não são compiladas no NetX Duo.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Enable IP fragmenting on this IP instance. */
status = nx_ip_fragment_enable(&ip_0);

/* If status is NX_SUCCESS, IP fragmenting has been enabled on the
   previously created IP instance. */
```
### <a name="see-also"></a>Consulte também  

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_gateway_address_clear"></a>nx_ip_gateway_address_clear
Limpe o endereço de gateway IPv4

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_gateway_address_clear(NX_IP *ip_ptr);
```
### <a name="description"></a>Descrição

Este serviço limpa o endereço de gateway IPv4 configurado no caso. Para limpar um IPv6 por defeito fora da instância IP, as aplicações devem utilizar o serviço ***nxd_ipv6_default_router_delete.***

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro do bloco de controlo IP

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) limpou com sucesso o endereço de gateway IP.
- **NX_PTR_ERROR** (0x07) Bloco de controlo IP inválido
- **NX_CALLER_ERROR** (0x11) O serviço não é chamado a partir da inicialização do sistema ou do contexto do fio.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Clear the gateway address of IP instance. */
status = nx_ip_gateway_address_clear(&ip_0);

/* If status == NX_SUCCESS, the gateway address was successfully
   cleared from the IP instance. */
```
### <a name="see-also"></a>Consulte também

-nx_ip_gateway_address_get -nx_ip_gateway_address_set -nx_ip_info_get -nx_ip_static_route_add -nx_ip_static_route_delete -nxd_ipv6_default_router_add -nxd_ipv6_default_router_delete -nxd_ipv6_default_router_entry_get -nxd_ipv6_default_router_get -nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_gateway_address_get"></a>nx_ip_gateway_address_get
Obtenha o endereço de gateway IPv4

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_gateway_address_get(
    NX_IP *ip_ptr, 
    ULONG *ip_address);
```
### <a name="description"></a>Descrição

Este serviço recupera o endereço de gateway IPv4 configurado na instância IP.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro do bloco de controlo IP
- **ip_address** Ponteiro para a memória onde o endereço de gateway está armazenado

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Com sucesso obter 
- **NX_PTR_ERROR** (0x07) Ponteiro do bloco de controlo IP inválido ou ponteiro de endereço IP
- **NX_NOT_FOUND** (0x4E) Endereço gateway não encontrado
- **NX_CALLER_ERROR** (0x11) S ervice não é chamado a partir da inicialização do sistema ou do contexto do fio.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
ULONG ip_address;

/* Get the gateway address of IP instance. */
status = nx_ip_gateway_address_get(&ip_0, &ip_address);

/* If status == NX_SUCCESS, the gateway address was successfully
   got. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_gateway_address_set"></a>nx_ip_gateway_address_set
Definir endereço IP gateway

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_gateway_address_set(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```
### <a name="description"></a>Descrição

Este serviço define o endereço IP do gateway IPv4. Todo o tráfego fora da rede é encaminhado para este portal de transmissão. O gateway deve estar diretamente acessível através de uma das interfaces de rede. Para configurar o endereço de gateway IPv6, utilize o nxd_ipv6_default_router_add de ***serviço.*** 

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **ip_address** Endereço IP do portal.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) conjunto de endereço IP de Gateway bem sucedido.
- **NX_PTR_ERROR** (0x07) Ponteiro de instância IP inválido.
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fio

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Setup the Gateway address for previously created IP
   Instance ip_0. */
status = nx_ip_gateway_address_set(&ip_0, IP_ADDRESS(1,2,3,99);

/* If status is NX_SUCCESS, all out-of-network send requests are
   routed to 1.2.3.99. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_info_get"></a>nx_ip_info_get
Recuperar informações sobre atividades ip

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_info_get(
    NX_IP *ip_ptr,
    ULONG *ip_total_packets_sent,
    ULONG *ip_total_bytes_sent,
    ULONG *ip_total_packets_received,
    ULONG *ip_total_bytes_received,
    ULONG *ip_invalid_packets,
    ULONG *ip_receive_packets_dropped,
    ULONG *ip_receive_checksum_errors,
    ULONG *ip_send_packets_dropped,
    ULONG *ip_total_fragments_sent,
    ULONG *ip_total_fragments_received);
```
### <a name="description"></a>Descrição

Este serviço obtém informações sobre as atividades IP para a instância IP especificada.

> [!NOTE]  
> *Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao chamador*.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **ip_total_packets_sent** Ponteiro para destino para o número total de pacotes IP enviados.
- **ip_total_bytes_sent** Ponteiro para destino para o número total de bytes enviados.
- **ip_total_packets_received** Ponteiro para o destino do número total de pacotes de IP recebem.
- **ip_total_bytes_received** Ponteiro para o destino do número total de bytes IP recebidos.
- **ip_invalid_packets** Ponteiro para o destino do número total de pacotes IP inválidos.
- **ip_receive_packets_dropped** Ponteiro para o destino do número total de pacotes de receção reduzido.
- **ip_receive_checksum_errors** Ponteiro para o destino do número total de erros de checkum nos pacotes de receção.
- **ip_send_packets_dropped** Ponteiro para o destino do número total de pacotes de envio reduzidos.
- **ip_total_fragments_sent** Ponteiro para o destino do número total de fragmentos enviados.
- **ip_total_fragments_received** Ponteiro para o destino do número total de fragmentos recebidos.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Recuperação de informações IP bem sucedidas.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Retrieve IP information from previously created IP
   Instance 0. */
status = nx_ip_info_get(&ip_0,
                        &ip_total_packets_sent,
                        &ip_total_bytes_sent,
                        &ip_total_packets_received,
                        &ip_total_bytes_received,
                        &ip_invalid_packets,
                        &ip_receive_packets_dropped,
                        &ip_receive_checksum_errors,
                        &ip_send_packets_dropped,
                        &ip_total_fragments_sent,
                        &ip_total_fragments_received);

/* If status is NX_SUCCESS, IP information was retrieved. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_interface_address_get"></a>nx_ip_interface_address_get
Recuperar endereço IP de interface

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_interface_address_get (
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *ip_address,
    ULONG *network_mask);
```
### <a name="description"></a>Descrição

Este serviço recupera o endereço IPv4 de uma interface de rede especificada. Para recuperar o endereço IPv6, a aplicação deve utilizar o serviço ***nxd_ipv6_address_get***

> [!CAUTION]  
> *O dispositivo especificado, se não o dispositivo primário, deve ser previamente ligado à instância IP*.

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **interface_index** Índice de interface, o mesmo valor que o índice da interface de rede anexada à instância IP.
- **ip_address** Ponteiro para destino para o endereço IP interface do dispositivo.
- **network_mask** Ponteiro para destino para a máscara de rede de interface do dispositivo.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) endereço IP bem sucedido obtém.
- **NX_INVALID_INTERFACE** (0x4C) A interface de rede especificada é inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
#define INTERFACE_INDEX 1

/* Get device IP address and network mask for the specified
   interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_get(ip_ptr,INTERFACE_INDEX,
                                     &ip_address,
                                     &network_mask);

/* If status is NX_SUCCESS the interface address was successfully
   retrieved. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_address_mapping_configure"></a>nx_ip_interface_address_mapping_configure
Configure se o mapeamento de endereços é necessário

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_interface_address_mapping_configure(
    NX_IP *ip_ptr,
    UINT interface_index,
    UINT mapping_needed);
```
### <a name="description"></a>Descrição

Este serviço configura se o endereço IP para mapeamento de endereço MAC é necessário para a interface de rede especificada. Este serviço é normalmente chamado do controlador do dispositivo de interface para notificar a pilha IP se a interface subjacente requer endereço IP para o mapeamento de endereços de camada dois (MAC).

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro do bloco de controlo IP
- **interface_index** Índice para a interface de rede
- **mapping_needed** NX_TRUE - mapeamento de endereço necessário NX_FALSE - mapeamento de endereço não necessário

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Configuração bem sucedida
- **NX_INVALID_INTERFACE** (0x4C) Índice de dispositivo não é válido
- **NX_PTR_ERROR** (0x07) Ponteiro do bloco de controlo IP inválido
- **NX_CALLER_ERROR** (0x11) O serviço não é chamado a partir da inicialização do sistema ou do contexto do fio.

### <a name="allowed-from"></a>Permitido a partir de

Fio

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
#define PRIMARY_INTERFACE 0
UCHAR mapping_needed = NX_TRUE;

/* Configure address mapping needed specified interface. */
status = nx_ip_interface_address_mapping_configure(&ip_0,
                                             PRIMARY_INTERFACE,
                                             mapping_needed);

/* If status == NX_SUCCESS, the address mapping needed was
   successfully configured. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_interface_address_get
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_address_set"></a>nx_ip_interface_address_set
Definir interface endereço IP e máscara de rede

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG ip_address,
    ULONG network_mask);
```
### <a name="description"></a>Descrição

Este serviço define o endereço IPv4 e a máscara de rede para a interface IP especificada. Para configurar o endereço de interface IPv6, a aplicação deve utilizar o serviço ***nxd_ipv6_address_set***. 
 
> [!WARNING]  
> *A interface especificada deve ser previamente anexada à instância IP*. 

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **interface_index** Índice da interface anexa à instância NetX Duo.
- **ip_address** Novo endereço IP de interface de rede.
- **network_mask** Nova máscara de rede de interface.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) conjunto de endereços IP bem sucedidos.
- **NX_INVALID_INTERFACE** (0x4C) A interface de rede especificada é inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_PTR_ERROR** (0x07) Ponteiros inválidos.
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IP inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
#define INTERFACE_INDEX 1

/* Set device IP address and network mask for the specified
   interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_set(ip_ptr, INTERFACE_INDEX,
                                     ip_address,
                                     network_mask);

/* If status is NX_SUCCESS the interface IP address and mask was
   successfully set. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_attach"></a>nx_ip_interface_attach
Anexar interface de rede à instância IP

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_interface_attach(
    NX_IP *ip_ptr, 
    CHAR *interface_name,
    ULONG ip_address,
    ULONG network_mask,
    VOID(*ip_link_driver)(struct NX_IP_DRIVER_STRUCT *));
```
### <a name="description"></a>Descrição

Este serviço adiciona uma interface de rede física à interface IP. Note que a instância IP é criada com a interface primária para que cada interface adicional seja secundária à interface primária. O número total de interfaces de rede anexas à instância IP (incluindo a interface primária) não pode exceder **NX_MAX_PHYSICAL_INTERFACES**.

Se o fio IP ainda não estiver em funcionamento, as interfaces secundárias serão inicializadas como parte do processo de arranque do fio IP que inicializa todas as interfaces físicas.

Se a linha IP ainda não estiver em funcionamento, a interface secundária é inicializada como parte do serviço ***nx_ip_interface_attach.***

> [!WARNING]  
> *ip_ptr deve apontar para uma estrutura IP NetX Duo válida. **NX_MAX_PHYSICAL_INTERFACES** devem ser configurados para o número de interfaces de rede para a instância IP. O valor predefinido é um*.

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **interface_name** Ponteiro para interface linha nome.
- **ip_address** Endereço IP do dispositivo na ordem byte anfitrião.
- **network_mask** Máscara de rede do dispositivo na ordem byte hospedeiro.
- **ip_link_driver** Controlador Ethernet para a interface.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) A entrada é adicionada à mesa de encaminhamento estática.
- **NX_NO_MORE_ENTRIES** (0x17) Número máximo de interfaces. NX_MAX_PHYSICAL_INTERFACES é excedido. Se o IPv6 estiver ativado, este erro também pode indicar que o controlador pode não ter recursos suficientes para lidar com as operações multicast IPv6.
- **NX_DUPLICATED_ENTRY** (0x52) O endereço IP fornecido já é utilizado neste caso IP.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro.
- **NX_IP_ADDRESS_ERROR** (0x21) Entrada de endereço IP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Attach secondary device for device IP address 192.168.1.68 with
   the specified Ethernet driver. */
status = nx_ip_interface_attach(ip_ptr, “secondary_port”,
                                IP_ADDRESS(192,168,1,68),
                                0xFFFFFF00UL,
                                nx_etherDriver);

/* If status is NX_SUCCESS the interface was successfully added to
   the IP instance interface table. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_capability_get"></a>nx_ip_interface_capability_get
Obtenha a capacidade de hardware de interface

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_interface_capability_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *interface_capability_flag);
```
### <a name="description"></a>Descrição

Este serviço recupera a bandeira de capacidade da interface de rede especificada. Para utilizar este serviço, a biblioteca NetX Duo deve ser construída com a opção ***NX_ENABLE_INTERFACE_CAPABILITY*** ativada.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro do bloco de controlo IP
- **interface_index** Índice da interface de rede
- **interface_capability_flag** Ponteiro para o espaço de memória para a bandeira de capacidade

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) obteve com sucesso informações sobre a capacidade da interface.
- **NX_NOT_SUPPORTED** funcionalidade de capacidade de interface (0x4B) não é suportada nesta construção.
- **NX_INVALID_INTERFACE** (0x4C) O índice de interface não é válido
- **NX_PTR_ERROR** (0x07) Ponteiro do bloco de controlo IP inválido ou ponteiro de bandeira de capacidade inválida
- **NX_CALLER_ERROR** (0x11) O serviço não é chamado a partir da inicialização do sistema ou do contexto do fio.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
#define PRIMARY_INTERFACE 0
ULONG       capability_flag;

/* Get the hardware capability flag of specified interface. */
status = nx_ip_interface_capability_get(&ip_0,
                                        PRIMARY_INTERFACE,
                                        &capability_flag);

/* If status == NX_SUCCESS, the capability flag from the primary
   interface was successfully retrieved. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_capability_set"></a>nx_ip_interface_capability_set
Desa parte da bandeira de capacidade de hardware

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_interface_capability_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG interface_capability_flag);
```                           
### <a name="description"></a>Descrição

Este serviço é utilizado pelo controlador do dispositivo de rede para configurar a bandeira de capacidade para uma interface de rede especificada. Para utilizar este serviço, a biblioteca NetX Duo deve ser compilada com a opção ***NX_ENABLE_INTERFACE_CAPABILITY*** definida.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro do bloco de controlo IP
- **interface_index** Índice de interface de rede
- **interface_capability_flag** Bandeira de capacidade para saída

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) definir com sucesso a bandeira de capacidade de hardware da interface.
- **NX_NOT_SUPPORTED** funcionalidade de capacidade de interface (0x4B) não é suportada nesta construção.
- **NX_INVALID_INTERFACE** (0x4C) O índice de interface não é válido 
- **NX_PTR_ERROR** (0x07) Ponteiro do bloco de controlo IP inválido 
- **NX_CALLER_ERROR** (0x11) S ervice não é chamado a partir da inicialização do sistema ou do contexto do fio.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
#define PRIMARY_INTERFACE 0
ULONG capability_flag = \
                 NX_INTERFACE_CAPABILITY_IPV4_TX_CHECKSUM |\
                 NX_INTERFACE_CAPABILITY_IPV4_RX_CHECKSUM;
UINT device_index = 0;

/* Set the hardware capability flag of specified interface. */
status = nx_ip_interface_capability_set(&ip_0,
                                        PRIMARY_INTERFACE,
                                        capability_flag);

/* If status == NX_SUCCESS, the hardware capability flag was
   successfully set. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_detach"></a>nx_ip_interface_detach
Retirar a interface especificada da instância IP

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr, 
    UINT index);
```
### <a name="description"></a>Descrição

Este serviço destaca a interface IP especificada da instância IP. Uma vez que uma interface é separada, todas as tomadas TCP conectadas fechadas, e cache ND e entradas ARP para esta interface são removidas das respetivas tabelas. As adesões IGMP para esta interface são removidas.

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **índice** Índice da interface a ser removido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) removeu com sucesso uma interface física.
- **NX_INVALID_INTERFACE** (0x4C) A interface de rede especificada é inválida.
- **NX_PTR_ERROR** (0x07) Ponteiros inválidos.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
#define INTERFACE_INDEX 1

/* Detach interface 1. */
status = nx_ip_interface_detach(&IP_0, INTERFACE_INDEX);

/* If status is NX_SUCCESS the interface is successfully detached
   from the IP instance. */
```

### <a name="see-also"></a>Consulte também  

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_info_get"></a>nx_ip_interface_info_get
Recuperar parâmetros de interface de rede

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_interface_info_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    CHAR **interface_name,
    ULONG *ip_address,
    ULONG *network_mask,
    ULONG *mtu_size,
    ULONG *physical_address_msw,
    ULONG *physical_address_lsw);
```
### <a name="description"></a>Descrição

Este serviço obtém informações sobre os parâmetros de rede para a interface de rede especificada. Todos os dados são recuperados por encomenda de byte de anfitrião. 

> [!WARNING]  
> *ip_ptr deve apontar para uma estrutura IP NetX Duo válida. A interface especificada, se não a interface primária, deve ser previamente anexada à instância IP*.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **interface_index** Índice especificando interface de rede.
- **interface_name** Ponteiro para o tampão que detém o nome da interface de rede.
- **ip_address** Ponteiro para o destino para o endereço IP da interface.
- **network_mask** Ponteiro para destino para máscara de rede.
- **mtu_size** Ponteiro para destino para unidade de transferência máxima para esta interface.
- **physical_address_msw** Ponteiro para o destino para os 16 melhores bits do endereço MAC do dispositivo.
- **physical_address_lsw** Ponteiro para destino para menos 32 bits do endereço MAC do dispositivo.

### <a name="return-values"></a>Valores de devolução   

- **NX_SUCCESS** informações de interface (0x00) foram obtidas.
- **NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro.
- **NX_INVALID_INTERFACE** (0x4C) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) O serviço não é chamado a partir da inicialização do sistema ou do contexto do fio.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Retrieve interface parameters for the specified interface (index
   1 in IP instance list of interfaces). */
#define INTERFACE_INDEX 1
status = nx_ip_interface_info_get(ip_ptr, INTERFACE_INDEX,
                                  &name_ptr, &ip_address,
                                  &network_mask,
                                  &mtu_size,
                                  &physical_address_msw,
                                  &physical_address_lsw);

/* If status is NX_SUCCESS the interface information is
   successfully retrieved. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_mtu_set"></a>nx_ip_interface_mtu_set
Definir o valor MTU de uma interface de rede

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_interface_mtu_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG mtu_size);
```
### <a name="description"></a>Descrição

Este serviço é utilizado pelo controlador do dispositivo para configurar o valor IP MTU para a interface de rede especificada.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro do bloco de controlo IP
- **interface_index** Índice para a interface de rede
- **mtu_size** Tamanho IP MTU

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) definir com sucesso o valor mtu
- **NX_INVALID_INTERFACE** (0x4C) O índice de interface não é válido
- **NX_PTR_ERROR** (0x07) Ponteiro do bloco de controlo IP inválido
- **NX_CALLER_ERROR** (0x11) O serviço não é chamado a partir da inicialização do sistema ou do contexto do fio.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
#define PRIMARY_INTERFACE 0
ULONG       mtu_size = 1500;

/* Set the MTU size of specified interface. */
status = nx_ip_interface_mtu_set(&ip_0,
                                 PRIMARY_INTERFACE, mtu_size);

/* If status == NX_SUCCESS, the MTU size was successfully set. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_physical_address_get"></a>nx_ip_interface_physical_address_get
Obtenha o endereço físico de um dispositivo de rede

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_interface_physical_address_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *physical_msw,
    ULONG *physical_lsw);
```
### <a name="description"></a>Descrição

Este serviço recupera o endereço físico de uma interface de rede a partir da instância IP.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro do bloco de controlo IP
- **interface_index** Índice da interface de rede
- **physical_msw** Ponteiro para destino para os 16 melhores bits do endereço MAC do dispositivo
- **physical_lsw** Ponteiro para destino para menos 32 bits do endereço MAC do dispositivo

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Com sucesso obter
- **NX_INVALID_INTERFACE** (0x4C) O índice de interface não é válido
- **NX_PTR_ERROR** (0x07) Ponteiro do bloco de controlo IP inválido ou ponteiro de endereço físico
- **NX_CALLER_ERROR** (0x11) O serviço não é chamado a partir da inicialização do sistema ou do contexto do fio.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
#define PRIMARY_INTERFACE 0
ULONG   physical_msw;
ULONG   physical_lsw;

/* Get the physical address of specified interface. */
status = nx_ip_interface_physical_address_get(&ip_0,
                                              PRIMARY_INTERFACE,
                                              &physical_msw,
                                              &physical_lsw);

/* If status == NX_SUCCESS, the physical address was successfully
   retrieved. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_physical_address_set"></a>nx_ip_interface_physical_address_set
Definir o endereço físico para uma interface de rede especificada

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_interface_physical_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG physical_msw,
    ULONG physical_lsw,
    UINT update_driver);
```
### <a name="description"></a>Descrição

Este serviço é utilizado pela aplicação ou pelo controlador do dispositivo para configurar o endereço físico do endereço MAC da interface de rede especificada. O novo endereço MAC é aplicado no bloco de controlo da estrutura da interface. Se a bandeira ***update_driver*** estiver definida, é emitido um comando ao nível do condutor para que o controlador do dispositivo possa atualizar o seu endereço MAC programado no controlador Ethernet.

Numa situação típica, este serviço é chamado do controlador do dispositivo de interface durante a fase de inicialização para notificar a pilha IP do seu endereço MAC. Neste caso, a bandeira ***update_driver*** não deve ser colocada.

Esta rotina também pode ser chamada da aplicação do utilizador para reconfigurar o endereço MAC da interface no tempo de execução. Neste caso de utilização, deve ser definida a bandeira ***update_driver,*** para que o novo endereço MAC possa ser aplicado ao controlador do dispositivo.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro do bloco de controlo IP
- **interface_index** Índice para a interface de rede
- **physical_msw** Ponteiro para destino para os 16 melhores bits do endereço MAC do dispositivo
- **physical_lsw** Ponteiro para destino para menos 32 bits do endereço MAC do dispositivo

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Conjunto de sucesso
- **Comando NX_UNHANDLED_COMMAND** (0x4B) não reconhecido pelo motorista
- **NX_INVALID_INTERFACE** (0x4C) O índice de interface não é válido
- **NX_PTR_ERROR** (0x07) Ponteiro do bloco de controlo IP inválido
- **NX_CALLER_ERROR** (0x11) O serviço não é chamado a partir da inicialização do sistema ou do contexto do fio.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
#define PRIMARY_INTERFACE 0
ULONG       physical_msw = 0x00CF;
ULONG       physical_lsw = 0x01020304;

/* Set the physical address of specified device. */
status = nx_ip_interface_physical_address_set(&ip_0,
                                              PRIMARY_INTERFACE,
                                              physical_msw,
                                              physical_lsw,
                                              NX_TRUE);

/* If status == NX_SUCCESS, the physical address was successfully
   set. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_status_check"></a>nx_ip_interface_status_check
Verificar o estado de verificação de uma instância IP

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_interface_status_check(
    NX_IP *ip_ptr,
    UINT interface_index
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```
### <a name="description"></a>Descrição

Este serviço verifica e aguarda opcionalmente o estado especificado da interface de rede de uma instância IP previamente criada.

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **interface_index** Número do índice de interface needed_status estado IP solicitado, definido no formulário bit-mape da seguinte forma:
  - **NX_IP_INITIALIZE_DONE** (0x0001)
  - **NX_IP_ADDRESS_RESOLVED** (0x0002)
  - **NX_IP_LINK_ENABLED** (0x0004)
  - **NX_IP_ARP_ENABLED** (0x0008)
  - **NX_IP_UDP_ENABLED** (0x0010)
  - **NX_IP_TCP_ENABLED** (0x0020)
  - **NX_IP_IGMP_ENABLED** (0x0040)
  - **NX_IP_RARP_COMPLETE** (0x0080)
  - **NX_IP_INTERFACE_LINK_ENABLED** (0x0100)
- **atual_status** Ponteiro para o destino de bits reais definido. wait_option Define como o serviço se comporta se as bits de estado solicitados não estiverem disponíveis. As opções de espera são definidas da seguinte forma:
  - **NX_NO_WAIT** (0x00000000)
  - **valor de tempo limite** (0x00000001 através de 0xFFFFFFFE)
  - **NX_WAIT_FOREVER** 0xFFFFFFFF

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Verificação de estado IP bem sucedida.
- **NX_NOT_SUCCESSFUL** pedido de estado (0x43) não foi satisfeito dentro do prazo especificado.
- **NX_PTR_ERROR** ponteiro IP (0x07) é ou tornou-se inválido, ou o ponteiro de estado real é inválido.
- **NX_OPTION_ERROR** (0x0a) A opção de estado necessária inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **Interface_index NX_INVALID_INTERFACE** (0x4C) está fora de alcance. ou a interface não é válida.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Wait 10 ticks for the link up status on the previously created IP
   instance. */
status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_LINK_ENABLED,
                                      &actual_status, 10);

/* If status is NX_SUCCESS, the secondary link for the specified IP
   instance is up. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_link_status_change_notify_set"></a>nx_ip_link_status_change_notify_set
Desa um conjunto de alterações de estado de ligação notifique a função de retorno de chamadas

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_link_status_change_notify_set(
    NX_IP *ip_ptr,
    VOID(*link_status_change_notify)(NX_IP *ip_ptr, UINT interface_index, UINT link_up));
```
### <a name="description"></a>Descrição

Este serviço configura a alteração do estado de ligação notifica a função de retorno de chamada. A rotina *de link_status_change_notify* fornecida pelo utilizador é invocada quando o estado da interface primária ou secundária é alterado (por exemplo, o endereço IP é alterado.) Se *link_status_change_notify* é NU, a alteração do estado de ligação notifica a função de chamada de chamada.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro do bloco de controlo IP
- **link_status_change_notify** Função de retorno fornecida pelo utilizador a ser chamada a uma alteração da interface física.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Conjunto de sucesso
- **NX_PTR_ERROR** (0x07) Ponteiro do bloco de controlo IP inválido ou novo ponteiro de endereço físico
- **NX_CALLER_ERROR** (0x11) O serviço não é chamado a partir da inicialização do sistema ou do contexto do fio.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Configure a callback function to be used when the physical
   interface status is changed. */
status = nx_ip_link_status_change_notify_set(&ip_0,
                                             my_change_cb);

/* If status == NX_SUCCESS, the link status change notify function
   is set. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check

## <a name="nx_ip_max_payload_size_find"></a>nx_ip_max_payload_size_find
Calcular a carga máxima de dados do pacote

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_max_payload_size_find(
    NX_IP *ip_ptr,
    NXD_ADDRESS *dest_address,
    UINT if_index,
    UINT src_port,
    UINT dest_port,
    ULONG protocol,
    ULONG *start_offset_ptr,
    ULONG *payload_length_ptr);
```
### <a name="description"></a>Descrição

Este serviço encontra o tamanho máximo da carga útil da aplicação que não exigirá a fragmentação ip para chegar ao destino; por exemplo, a carga útil está no tamanho mtu da interface local ou abaixo. (ou o valor do Caminho MTU obtido através da descoberta do IPv6 Path MTU). O cabeçalho IP e o tamanho superior do cabeçalho de aplicação (TCP ou UDP) são subtraídos da carga total. Se a Política de Segurança NetX Duo IPsec se aplicar a este ponto final, os cabeçalhos IPsec (ESP/AH) e as despesas gerais associadas, como o Vetor Inicial, também são subtraídos do MTU. Este serviço é aplicável tanto para os pacotes IPv4 como IPv6.

O parâmetro *if_index* especifica a interface a utilizar para o envio do pacote. Para um sistema multihome, o chamador precisa de especificar o parâmetro *if_index* se o destino for uma transmissão (apenas IPv4), multicast ou endereço iPv6 link-local.

Este serviço devolve dois valores ao chamador:

1) start_offset_ptr: Esta é a localização após os cabeçalhos TCP/UDP/IP/IPsec;
2) payload_length_ptr: a quantidade de pedido de dados pode ser transferida sem exceder a MTU.

Não existe um serviço NetX equivalente.

### <a name="restrictions"></a>Restrições 

A instância IP deve ser previamente criada.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Indicação para a instância IP
- **dest_address** Ponteiro para endereço de destino do pacote
- **if_index** Indica o índice da interface a utilizar
- **src_port** Número da porta de origem
- **dest_port** Número da porta de destino
- **protocolo** Protocolo de camada superior a utilizar
- **start_offset_ptr** Ponteiro para o início dos dados para a carga máxima do pacote
- **payload_length_ptr** Ponteiro para o tamanho da carga útil, excluindo cabeçalhos

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Payload com sucesso calculado
- **NX_INVALID_INTERFACE** (0x4C) O índice de interface é inválido ou a interface não é válida.
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IP inválido.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido ou endereço de destino inválido
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço inválido fornecido 
- **NX_NOT_SUPPORTED** (0x4B) Protocolo inválido (não UDP ou TCP)
- **NX_CALLER_ERROR** (0x11) O serviço não é chamado a partir da inicialização do sistema ou do contexto do fio.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* The following example determines the maximum payload for UDP
   packet to remote host. */
#define PRIMARY_INTERFACE 0
status = nx_ip_max_payload_size_find(&ip_0,
                                     &dest_ipv6_address,
                                     PRIMARY_INTERFACE,
                                     source_port,
                                     dest_port, NX_PROTOCOL_UDP,
                                     &start_offset,
                                     &payload_length);

/* A return value of NX_SUCCESS indicates the packet payload
   payload_length starting at the offset start_offset is
   successfully computed. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_raw_packet_disable"></a>nx_ip_raw_packet_disable
Desativar o envio/receção de pacotes brutos

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_raw_packet_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descrição

Este serviço desativa a transmissão e receção de pacotes IP crus para este caso IP. Se o serviço de pacotes brutos foi previamente ativado, e existem pacotes crus na fila de receção, este serviço libertará quaisquer pacotes crus recebidos.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Pacotes IP crus bem sucedidos desativar.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Disable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_disable(&ip_0);
/* If status is NX_SUCCESS, raw IP packet sending/receiving has
   been disabled for the previously created IP instance. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_enable"></a>nx_ip_raw_packet_enable
Permitir o processamento de pacotes crus

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_raw_packet_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descrição

Este serviço permite a transmissão e receção de pacotes IP crus para este caso IP. Os pacotes de TCP, UDP, ICMP e IGMP ainda são processados pela NetX Duo. Pacotes com tipos de protocolo de camada superior desconhecida são processados pela rotina de receção de pacotes crus.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Pacotes ip crus bem sucedidos.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Enable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_enable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
   been enabled for the previously created IP instance. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_filter_set"></a>nx_ip_raw_packet_filter_set
Definir filtro de pacote IP cru

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_raw_packet_filter_set(
    NX_IP *ip_ptr,
    UINT (*raw_packet_filter)(NX_IP *, ULONG, NX_PACKET *));
```
### <a name="description"></a>Descrição

Este serviço configura o filtro de pacotes crus IP. A função de filtro de pacotes brutos, implementada pela aplicação do utilizador, permite que uma aplicação receba pacotes crus com base em critérios fornecidos pelo utilizador. Note que a camada de invólucro BSD NetX Duo utiliza a função de filtro de pacote cru para manusear a tomada crua na camada BSD. Para utilizar este serviço, a biblioteca NetX Duo deve ser construída com a opção ***NX_ENABLE_IP_RAW_PACKET_FILTER*** definida.

### <a name="parameters"></a>Parâmetros  

- **ip_ptr** Ponteiro do bloco de controlo IP
- **raw_packet_filter** Ponteiro de função do filtro de pacote cru

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) definir com sucesso a rotina do filtro de pacote cru
- **NX_NOT_SUPPORT** (0x4B) Suporte ao pacote bruto não está disponível
- **NX_PTR_ERROR** (0x07) Ponteiro do bloco de controlo IP inválido
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
UINT raw_packet_filter(NX_IP *ip_ptr, ULONG protocol,
                       NX_PACKET *packet_ptr)
{

/* Simply filter protocol. */
if(protocol == NX_IP_RAW)
   return NX_SUCCESS;
else
   return NX_NOT_SUCCESSFUL;
}

void raw_packet_thread_entry(ULONG id)
{

/* Set the raw packet filter of IP instance. */
status = nx_ip_raw_packet_filter_set(&ip_0,
                                     raw_packet_filter);

/* If status == NX_SUCCESS, the raw packet filter of IP instance
   was successfully set. */
}
```
### <a name="see-also"></a>Consulte também

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_receive"></a>nx_ip_raw_packet_receive
Receba pacote IP cru

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_raw_packet_receive(
    NX_IP *ip_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Descrição

Este serviço recebe um pacote IP cru a partir da instância IP especificada. Se houver pacotes IP na fila de receção de pacotes brutos, o primeiro pacote (mais antigo) é devolvido ao chamador. Caso contrário, se não houver pacotes disponíveis, o chamador pode suspender conforme especificado pela opção de espera.

> [!CAUTION]   
> *Se NX_SUCCESS, for devolvido, o pedido é responsável pela libertação do pacote recebido quando já não for necessário*.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **packet_ptr** Ponteiro para o ponteiro para colocar o pacote IP bruto recebido dentro
- **wait_option** Define como o serviço se comporta se os pacotes não estiverem disponíveis. As opções de espera são definidas da seguinte forma:
   - **NX_NO_WAIT** (0x00000000)
   - **NX_WAIT_FOREVER** (0xFFFFFFFF)
   - **valor de tempo limite em carrapatos** (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Pacote IP cru bem sucedido.
- **NX_NO_PACKET** (0x01) Não estava disponível nenhum pacote.
- **NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.
- **NX_PTR_ERROR** (0x07) IP inválido ou ponteiro do pacote de devolução.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Receive a raw IP packet for this IP instance, wait for a maximum
   of 4 timer ticks. */
status = nx_ip_raw_packet_receive(&ip_0, &packet_ptr, 4);

/* If status is NX_SUCCESS, the raw IP packet pointer is in the
   variable packet_ptr. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_send"></a>nx_ip_raw_packet_send
Enviar pacote IP cru

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_raw_packet_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    ULONG type_of_service);
```
### <a name="description"></a>Descrição

Este serviço envia um pacote IPv4 cru para o endereço IP destino. Note que esta rotina retorna imediatamente, pelo que não se sabe se o pacote IP foi efetivamente enviado. O controlador de rede será responsável pela libertação do pacote quando a transmissão estiver completa.

Para um sistema multihome, o NetX Duo utiliza o endereço IP de destino para encontrar uma interface de rede apropriada e utiliza o endereço IP da interface como endereço de origem. Se o endereço IP de destino for transmitido ou multicast, a primeira interface válida é utilizada. As aplicações utilizam o ***nx_ip_raw_packet_source_send*** neste caso.

Para enviar um pacote IPv6 cru, a aplicação deve utilizar o serviço ***nxd_ip_raw_packet_send,** _ ou _ *_nxd_ip_raw_packet_source_send._**

> [!WARNING]  
> *A menos que um erro seja devolvido, o pedido não deve libertar o pacote após esta chamada. Ao fazê-lo, o controlador da rede libertará o pacote após a transmissão*.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **packet_ptr** Ponteiro para o pacote IP cru para enviar.
- **destination_ip** Endereço IP de destino, que pode ser um endereço IP de anfitrião específico, uma transmissão de rede, um loop-back interno ou um endereço multicast.
- **type_of_service** Define o tipo de serviço para a transmissão, os valores legais são os seguintes:
    - **NX_IP_NORMAL** (0x00000000)
    - **NX_IP_MIN_DELAY** (0x00100000)
    - **NX_IP_MAX_DATA** (0x00080000)
    - **NX_IP_MAX_RELIABLE** (0x00040000)
    - **NX_IP_MIN_COST** (0x00020000)

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Pacotes crus IP bem sucedidos enviados.
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IP inválido.
- **NX_NOT_ENABLED** (0x14) A função IP raw não está ativada.
- **NX_OPTION_ERROR** (0x0A) Tipo de serviço inválido.
- **NX_UNDERFLOW** (0x02) Não há espaço suficiente para preparar um cabeçalho IP no pacote.
- **NX_OVERFLOW** (0x03) O ponteiro do apêndice do pacote é inválido.
- **NX_PTR_ERROR** (0x07) IP inválido ou ponteiro do pacote.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Send a raw IP packet to IP address 1.2.3.5. */
status = nx_ip_raw_packet_send(&ip_0, packet_ptr,
                               IP_ADDRESS(1,2,3,5),
                               NX_IP_NORMAL);

/* If status is NX_SUCCESS, the raw IP packet pointed to by
   packet_ptr has been sent. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_source_send"></a>nx_ip_raw_packet_source_send
Enviar pacote IP cru através de interface de rede especificada

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_raw_packet_source_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    UINT address_index,
    ULONG type_of_service);
```
### <a name="description"></a>Descrição

Este serviço envia um pacote IP bruto para o endereço IP de destino usando o endereço IPv4 local especificado como endereço de origem, e através da interface de rede associada. Note que esta rotina retorna imediatamente, e não é, portanto, conhecido se o pacote IP foi realmente enviado. O controlador de rede será responsável pela libertação do pacote quando a transmissão estiver completa. Este serviço difere de outros serviços na medida em que não há forma de saber se o pacote foi realmente enviado. Pode perder-se na Internet.

> [!CAUTION]  
> *Note que o processamento de IP bruto deve ser ativado*.

> [!WARNING]  
> *Este serviço é semelhante ao **nx_ip_raw_packet_send,** exceto que este serviço permite que uma aplicação envie pacotes IPv4 crus a partir de interfaces físicas especificadas.*

### <a name="parameters"></a>Parâmetros  

- **ip_ptr** Ponteiro para tarefa IP previamente criada.
- **packet_ptr** Ponteiro para pacote para transmitir.
- **destination_ip** Endereço IP para enviar pacote.
- **address_index** Índice do endereço da interface para enviar o pacote.
- **type_of_service** Tipo de serviço para pacote.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Pacote transmitido com sucesso.
- **NX_IP_ADDRESS_ERROR** (0x21) Não existe uma interface de saída adequada disponível.
- **NX_NOT_ENABLED** (0x14) processamento de pacotes IP crus não ativados.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro.
- **NX_OPTION_ERROR** (0x0A) Tipo de serviço inválido especificado.
- **NX_OVERFLOW** (0x03) Ponteiro de pré-final de pacote inválido.
- **NX_UNDERFLOW** (0x02) Ponteiro de pré-final de pacote inválido.
- **NX_INVALID_INTERFACE** (0x4C) Índice de interface inválido especificado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
#define ADDRESS_IDNEX 1

/* Send packet out on interface 1 with normal type of service. */
status = nx_ip_raw_packet_source_send(ip_ptr, packet_ptr,
                                      destination_ip,
                                      ADDRESS_INDEX,
                                      NX_IP_NORMAL);

/* If status is NX_SUCCESS the packet was successfully
   transmitted. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_receive_queue_max_set"></a>nx_ip_raw_receive_queue_max_set
Definir o tamanho máximo de fila de receção bruta

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_raw_receive_queue_max_set(
    NX_IP *ip_ptr, 
    ULONG queue_max);
```
### <a name="description"></a>Descrição

Este serviço configura a profundidade máxima da fila de receção de pacotes ip crus. Note que a fila de receção de pacotes ip cru é partilhada com pacotes IPv4 e IPv6. Quando a fila de receção do pacote bruto atinge a profundidade máxima configurada pelo utilizador, os pacotes crus recentemente recebidos são largados. O pacote ip bruto predefinido receber profundidade de fila é de 20.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro do bloco de controlo IP
- **queue_max** Novo valor para o tamanho da fila

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) definidos com sucesso em bruto receber a profundidade máxima da fila
- **NX_PTR_ERROR** (0x07) Ponteiro do bloco de controlo IP inválido
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
ULONG queue_max = 10;

/* Set the maximum size of the IP raw packet receive queue. */
status = nx_ip_raw_receive_queue_max_set (&ip_0,
                                          queue_max);

/* If status == NX_SUCCESS, the maximum size of the IP raw packet
   receive queue was successfully set. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_static_route_add"></a>nx_ip_static_route_add
Adicione rota estática à mesa de encaminhamento

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_static_route_add(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask,
    ULONG next_hop);
```
### <a name="description"></a>Descrição

Este serviço adiciona uma entrada na tabela de encaminhamento estático. Note que o endereço *next_hop* deve estar diretamente acessível a partir de um dos dispositivos de rede locais.

> [!CAUTION]  
> *Note que ip_ptr deve apontar para uma estrutura cómoda netx Duo IP válida e a biblioteca NetX Duo deve ser construída com NX_ENABLE_IP_STATIC_ROUTING definida para usar este serviço. Por padrão, o NetX Duo é construído sem NX_ENABLE_IP_STATIC_ROUTING definido*.

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **network_address** Endereço de rede alvo, em ordem byte de anfitrião 
- **net_mask** Máscara de rede de alvo, em ordem byte hospedeiro
- **next_hop** Próximo endereço de lúpulo para a rede alvo, em ordem byte anfitrião

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) A entrada é adicionada à mesa de encaminhamento estática.
- **NX_OVERFLOW** (0x03) A mesa de encaminhamento está cheia.
- **NX_NOT_SUPPORTED** (0x4B) Esta função não está compilada.
- **NX_IP_ADDRESS_ERROR** (0x21) O próximo lúpulo não é diretamente acessível através de interfaces locais.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_PTR_ERROR** (0x07) Ponteiro ip_ptr Inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Specify the next hop for 192.168.1.68 through the gateway
   192.168.1.1. */
status = nx_ip_static_route_add(ip_ptr, IP_ADDRESS(192,168,1,0),
                                0xFFFFFF00UL,
                                IP_ADDRESS(192,168,1,1));

/* If status is NX_SUCCESS the route was successfully added to the
   static routing table. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_static_route_delete"></a>nx_ip_static_route_delete
Eliminar rota estática da mesa de encaminhamento

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_static_route_delete(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask);
```
### <a name="description"></a>Descrição

Este serviço elimina uma entrada da tabela de encaminhamento estático.

> [!WARNING]  
> *Note que ip_ptr deve apontar para uma estrutura cómoda netx Duo IP válida e a biblioteca NetX Duo deve ser construída com NX_ENABLE_IP_STATIC_ROUTING definida para usar este serviço. Por padrão, o NetX Duo é construído sem NX_ENABLE_IP_STATIC_ROUTING definido*.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **network_address** Endereço de rede de destino, em ordem byte anfitrião.
- **net_mask** Máscara de rede de alvo, em ordem byte de anfitrião.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Supressão bem sucedida da tabela de encaminhamento estático.
- **NX_NOT_SUCCESSFUL** (0x43) A entrada não pode ser encontrada na mesa de encaminhamento.
- **NX_NOT_SUPPORTED** (0x4B) Esta função não está compilada.
- **NX_PTR_ERROR** (0x07) Ponteiro ip_ptr Inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Remove the static route for 192.168.1.68 from the routing
   table.*/
status = nx_ip_static_route_delete(ip_ptr,
                                   IP_ADDRESS(192,168,1,0),
                                   0xFFFFFF00UL,);

/* If status is NX_SUCCESS the route was successfully removed from
   the static routing table. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_status_check"></a>nx_ip_status_check
Verificar o estado de verificação de uma instância IP

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_status_check(
    NX_IP *ip_ptr,
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```
### <a name="description"></a>Descrição

Este serviço verifica e aguarda opcionalmente o estado especificado da interface de rede primária de uma instância IP previamente criada. Para obter o estatuto nas interfaces secundárias, as aplicações utilizarão o ***serviço nx_ip_interface_status_check.***

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **needed_status** Estado ip solicitado, definido no formulário bit-mape da seguinte forma:
  - **NX_IP_INITIALIZE_DONE** (0x0001)
  - **NX_IP_ADDRESS_RESOLVED** (0x0002)
  - **NX_IP_LINK_ENABLED** (0x0004)
  - **NX_IP_ARP_ENABLED** (0x0008)
  - **NX_IP_UDP_ENABLED** (0x0010)
  - **NX_IP_TCP_ENABLED** (0x0020)
  - **NX_IP_IGMP_ENABLED** (0x0040)
  - **NX_IP_RARP_COMPLETE** (0x0080)
  - **NX_IP_INTERFACE_LINK_ENABLED** (0x0100)
- **atual_status** Ponteiro para o destino de bits reais definido.
- **wait_option** Define como o serviço se comporta se as bits de estado solicitados não estiverem disponíveis. As opções de espera são definidas da seguinte forma:
  - **NX_NO_WAIT** 0x00000000)
  - **valor de tempo limite em carrapatos** (0x00000001 a 0xFFFFFFFE)
  - **NX_WAIT_FOREVER** 0xFFFFFFFF

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Verificação de estado IP bem sucedida.
- **NX_NOT_SUCCESSFUL** pedido de estado (0x43) não foi satisfeito dentro do prazo especificado.
- **NX_PTR_ERROR** ponteiro IP (0x07) é ou tornou-se inválido, ou o ponteiro de estado real é inválido.
- **NX_OPTION_ERROR** (0x0a) A opção de estado necessária inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Wait 10 ticks for the link up status on the previously created IP
   instance. */
status = nx_ip_status_check(&ip_0, NX_IP_LINK_ENABLED,
                            &actual_status, 10);

/* If status is NX_SUCCESS, the link for the specified IP instance
   is up. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ipv4_multicast_interface_join"></a>nx_ipv4_multicast_interface_join
Junte a instância IP a grupo multicast especificado através de uma interface

### <a name="prototype"></a>Prototype  

```c
UINT nx_ipv4_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>Descrição

Este serviço junta-se a uma instância IP ao grupo multicast especificado através de uma interface de rede especificada. Uma vez que a instância IP se junta a um grupo multicast, a lógica de receção IP começa a encaminhar pacotes de dados do grupo dar grupo multicast para a camada superior. Note que este serviço se junta a um grupo multicast sem enviar relatórios IGMP.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **group_address** Endereço de grupo multicast classe D IP para se juntar na ordem byte de anfitrião.
- **interface_index** Índice da Interface ligado à instância NetX Duo.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Grupo multicast bem sucedido.
- **NX_NO_MORE_ENTRIES** (0x17) Não podem ser acompanhados mais grupos multicast, o máximo excedido.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido para a instância IP, ou a instância IP é inválida
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_EANABLED** (0x14) IGMP não está habilitado neste caso de IP
- **NX_IP_ADDRESS_ERROR** endereço de grupo multicast fornecido (0x21) não é um endereço de classe D válido.
- **NX_INVALID_INTERFACE** (0x4C) Índice de dispositivo aponta para uma interface de rede inválida.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Previously created IP Instance joins the multicast group
   224.0.0.200, via the interface at index 1 in the IP interface
   list. */
#define INTERFACE_INDEX 1
status = nx_ipv4_multicast_interface_join
                                 (&ip IP_ADDRESS(224,0,0,200),
                                  INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
   the multicast group. */
```
### <a name="see-also"></a>Consulte também

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_ipv4_multicast_interface_leave"></a>nx_ipv4_multicast_interface_leave
Deixe o grupo multicast especificado através de uma interface

### <a name="prototype"></a>Prototype  

```c
UINT nx_ipv4_multicast_interface_leave(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>Descrição

Este serviço deixa o grupo multicast especificado através de uma interface de rede especificada. Depois de sair do grupo, este serviço não desencadeia a geração de mensagens IGMP.

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **group_address** Endereço de grupo multicast ip classe D para sair. O endereço IP está em ordem de acolhimento.
- **interface_index** Índice da Interface ligado à instância NetX Duo.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Grupo multicast bem sucedido.
- **NX_ENTRY_NOT_FOUND** (0x16) O endereço de grupo multicast especificado não pode ser encontrado na tabela multicast local.
- **NX_INVALID_INTERFACE** (0x4C) Índice de dispositivo aponta para uma interface de rede inválida.
- **NX_IP_ADDRESS_ERROR** endereço de grupo multicast fornecido (0x21) não é um endereço de classe D válido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido para a instância IP, ou a instância IP é inválida

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Leave the multicast group 224.0.0.200. */
#define INTERFACE_INDEX 1
status = nx_ipv4_multicast_interface_leave
                                (&ip, IP_ADDRESS(224,0,0,200),
                                 INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully leaves
   the multicast group 244.0.0.200. */
```
### <a name="see-also"></a>Consulte também

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_packet_allocate"></a>nx_packet_allocate
Alocar pacote a partir de piscina especificada

### <a name="prototype"></a>Prototype  

```c
UINT nx_packet_allocate(
    NX_PACKET_POOL *pool_ptr,
    NX_PACKET **packet_ptr,
    ULONG packet_type,
    ULONG wait_option);
```
### <a name="description"></a>Descrição

Este serviço atribui um pacote da piscina especificada e ajusta o ponteiro pré-final no pacote de acordo com o tipo de pacote especificado. Se não houver pacote disponível, o serviço suspende de acordo com a opção de espera fornecida.

### <a name="parameters"></a>Parâmetros

- **pool_ptr** Ponteiro para piscina de pacotes previamente criada.
- **packet_ptr** Ponteiro para o ponteiro do ponteiro do pacote atribuído.
- **packet_type** Define o tipo de pacote solicitado. Consulte "Packet Pools" na página 63 do Capítulo 3 para obter uma lista de tipos de pacotes suportados.
- **wait_option** Define o tempo de espera em carrapatos se não houver pacotes disponíveis na piscina de pacotes. As opções de espera são definidas da seguinte forma:
  - **NX_NO_WAIT** (0x00000000)
  - **NX_WAIT_FOREVER** (0xFFFFFFFF)
  - **valor de tempo limite em carrapatos** (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Atribuição de pacotes bem sucedidos.
- **NX_NO_PACKET** (0x01) Nenhum pacote disponível.
- **NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.
- **NX_INVALID_PARAMETERS** (0x4D) O tamanho do pacote não pode suportar o protocolo.
- **NX_OPTION_ERROR** (0x0A) Tipo de pacote inválido.
- **NX_PTR_ERROR** (0x07) Ponteiro de retorno de piscina ou pacote.
- **NX_CALLER_ERROR** (0x11) Opção de espera inválida de não-leitura.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs (controladores de rede de aplicações). A opção de espera deve ser *NX_NO_WAIT* quando utilizada no contexto ISR ou no temporizador.

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Allocate a new UDP packet from the previously created packet pool
   and suspend for a maximum of 5 timer ticks if the pool is
   empty. */
status = nx_packet_allocate(&pool_0, &packet_ptr,
                            NX_UDP_PACKET, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is
   found in the variable packet_ptr. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_copy"></a>nx_packet_copy
Pacote de cópia

### <a name="prototype"></a>Prototype  

```c
UINT nx_packet_copy(
    NX_PACKET *packet_ptr,
    NX_PACKET **new_packet_ptr,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Descrição

Este serviço copia as informações no pacote fornecido a um ou mais novos pacotes que são atribuídos a partir da piscina de pacotes fornecidos. Se for bem sucedido, o ponteiro para o novo pacote é devolvido no destino apontado por **new_packet_ptr**.

### <a name="parameters"></a>Parâmetros

- **packet_ptr** Ponteiro para o pacote de origem.
- **new_packet_ptr** Ponteiro para o destino de onde devolver o ponteiro à nova cópia do pacote.
- **pool_ptr** Ponteiro para o pacote de pacotes anteriormente criado que é usado para alocar um ou mais pacotes para a cópia.
- **wait_option** Define como o serviço espera se não houver pacotes disponíveis. As opções de espera são definidas da seguinte forma:
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **valor de tempo limite em carrapatos** (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Cópia de pacote bem sucedida.
- **NX_NO_PACKET** (0x01) Pacote não disponível para cópia.
- **NX_INVALID_PACKET** (0x12) O pacote de origem ou cópia vazio falhou.
- **NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.
- **NX_INVALID_PARAMETERS** (0x4D) O tamanho do pacote não pode suportar o protocolo.
- **NX_PTR_ERROR** (0x07) Piscina inválida, pacote ou ponteiro de destino.
- **NX_UNDERFLOW** (0x02) Ponteiro de pré-final de pacote inválido.
- **NX_OVERFLOW** (0x03) Ponteiro de pacote inválido.
- **NX_CALLER_ERROR** (0x11) Foi especificada uma opção de espera na inicialização ou numa ISR.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
NX_PACKET *new_copy_ptr;

/* Copy packet pointed to by "old_packet_ptr" using packets from
   previously created packet pool_0. */
status = nx_packet_copy(old_packet, &new_copy_ptr, &pool_0, 20);

/* If status is NX_SUCCESS, new_copy_ptr points to the packet copy. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_data_append"></a>nx_packet_data_append
Dados do apêndice ao fim do pacote

### <a name="prototype"></a>Prototype  

```c
UINT nx_packet_data_append(
    NX_PACKET *packet_ptr,
    VOID *data_start, ULONG data_size,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Descrição

Este serviço anexa dados ao final do pacote especificado. A área de dados fornecida é copiada para o pacote. Se não houver memória suficiente disponível e a função de pacote acorrentado estiver ativada, um ou mais pacotes serão atribuídos para satisfazer o pedido. Se a função de pacote acorrentado não estiver ativada, *NX_SIZE_ERROR* é devolvida.

### <a name="parameters"></a>Parâmetros

- **packet_ptr** Ponteiro do pacote.
- **data_start** Ponteiro para o início da área de dados do utilizador para anexar ao pacote.
- **data_size** Tamanho da área de dados do utilizador.
- **pool_ptr** Ponteiro para pacote de piscina a partir do qual atribuir outro pacote se não houver espaço suficiente no pacote atual.
- **wait_option** Define como o serviço se comporta se não houver pacotes disponíveis. As opções de espera são definidas da seguinte forma:
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **valor de tempo limite em carrapatos** (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Pacote de sucesso.
- **NX_NO_PACKET** (0x01) Nenhum pacote disponível.
- **NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.
- **NX_INVALID_PARAMETERS** (0x4D) O tamanho do pacote não pode suportar o protocolo.
- **NX_UNDERFLOW** (0x02) O ponteiro prepend é inferior ao arranque da carga útil.
- **NX_OVERFLOW** (0x03) O ponteiro do apêndice é maior do que a extremidade da carga útil.
- **NX_PTR_ERROR** (0x07) Piscina inválida, pacote ou dados Pointer.
- **NX_SIZE_ERROR** (0x09) Tamanho de dados inválidos.
- **NX_CALLER_ERROR** (0x11) Opção de espera inválida de não-leitura.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs (controladores de rede de aplicações)

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Append "abcd" to the specified packet. */
status = nx_packet_data_append(packet_ptr, "abcd", 4, &pool_0, 5);

/* If status is NX_SUCCESS, the additional four bytes "abcd" have
   been appended to the packet. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release


## <a name="nx_packet_data_extract_offset"></a>nx_packet_data_extract_offset
Extrair dados do pacote através de uma compensação

### <a name="prototype"></a>Prototype  

```c
UINT nx_packet_data_extract_offset(
    NX_PACKET *packet_ptr,
    ULONG offset,
    VOID *buffer_start,
    ULONG buffer_length,
    ULONG *bytes_copied);
```
### <a name="description"></a>Descrição

Este serviço copia dados de um pacote NetX Duo (ou cadeia de pacotes) a partir da compensação especificada a partir do ponteiro pré-final do pacote do tamanho especificado em bytes no tampão especificado. O número de bytes copiados é devolvido em *bytes_copied.* Este serviço não remove dados do pacote, nem ajusta o ponteiro pré-conjunto ou outras informações internas do estado.

### <a name="parameters"></a>Parâmetros

- **packet_ptr** Ponteiro para pacote para extrair
- **compensar** Compensado do ponteiro pré-final atual.
- **buffer_start** Ponteiro para o início do tampão de poupança
- **buffer_length** Número de bytes para copiar
- **bytes_copied** Número de bytes realmente copiados

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Cópia de pacote de sucesso
- **NX_PACKET_OFFSET_ERROR** (0x53) Foi fornecido valor de compensação inválido
- **NX_PTR_ERROR** (0x07) Ponteiro de pacote inválido ou ponteiro tampão

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

```c
/* Extract 10 bytes from the start of the received packet buffer
   into the specified memory area. */
status = nx_packet_data_extract_offset(my_packet, 0, &data[0], 10,
                                       &bytes_copied) ;
/* If status is NX_SUCCESS, 10 bytes were successfully copied into
   the data buffer. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_data_retrieve"></a>nx_packet_data_retrieve
Recuperar dados do pacote

### <a name="prototype"></a>Prototype  

```c
UINT nx_packet_data_retrieve(
    NX_PACKET *packet_ptr,
    VOID *buffer_start,
    ULONG *bytes_copied);
```
### <a name="description"></a>Descrição

Este serviço copia os dados do pacote fornecido no tampão fornecido. O número real de bytes copiados é devolvido no destino apontado por **bytes_copied**.

Note que este serviço não altera o estado interno do pacote. Os dados que estão a ser recuperados ainda estão disponíveis no pacote. 

> [!CAUTION]  
> *O tampão de destino deve ser grande o suficiente para manter o conteúdo do pacote. Caso contrário, a memória será corrompida causando resultados imprevisíveis*.

### <a name="parameters"></a>Parâmetros

- **packet_ptr** Ponteiro para o pacote de origem.
- **buffer_start** Ponteiro para o início da área tampão.
- **bytes_copied** Ponteiro para o destino para o número de bytes copiados.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Recuperação de dados de pacotes bem sucedidos.
- **pacote** inválido NX_INVALID_PACKET (0x12).
- **NX_PTR_ERROR** (0x07) Pacote inválido, arranque do tampão ou bytes ponteiros copiados.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
UCHAR                 buffer[512];
ULONG                 bytes_copied;

/* Retrieve data from packet pointed to by "packet_ptr". */
status = nx_packet_data_retrieve(packet_ptr, buffer, &bytes_copied);

/* If status is NX_SUCCESS, buffer contains the contents of the
   packet, the size of which is contained in "bytes_copied." */
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_length_get"></a>nx_packet_length_get
Obtenha o comprimento dos dados do pacote

### <a name="prototype"></a>Prototype  

```c
UINT nx_packet_length_get(
    NX_PACKET *packet_ptr, 
    ULONG *length);
```
### <a name="description"></a>Descrição

Este serviço obtém o comprimento dos dados no pacote especificado.

### <a name="parameters"></a>Parâmetros

- **packet_ptr** Ponteiro para o pacote.
- **comprimento** Destino para o comprimento do pacote.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Comprimento do pacote bem sucedido obter.
- **NX_PTR_ERROR** (0x07) Ponteiro do pacote inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Get the length of the data in "my_packet." */
status = nx_packet_length_get(my_packet, &my_length);

/* If status is NX_SUCCESS, data length is in "my_length". */
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_create"></a>nx_packet_pool_create
Criar piscina de pacotes na área de memória especificada

### <a name="prototype"></a>Prototype  

```c
UINT nx_packet_pool_create(
    NX_PACKET_POOL *pool_ptr,
    CHAR *name,
    ULONG payload_size,
    VOID *memory_ptr,
    ULONG memory_size);
```
### <a name="description"></a>Descrição

Este serviço cria um conjunto de pacotes do tamanho especificado do pacote na área de memória fornecida pelo utilizador.

### <a name="parameters"></a>Parâmetros

- **pool_ptr** Ponteiro para bloco de controlo de piscina de pacote.
- **nome** Ponteiro para o nome da aplicação para a piscina de pacotes.
- **payload_size** Número de bytes em cada pacote na piscina. Este valor deve ser de, pelo menos, 40 bytes e deve ser igualmente divisível por 4.
- **memory_ptr** Ponteiro para a área de memória para colocar a piscina de pacotes dentro O ponteiro deve ser alinhado num limite ULONG.
- **memory_size** Tamanho da área de memória da piscina.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Conjunto de pacotes bem sucedidos criar.
- **NX_PTR_ERROR** (0x07) Piscina inválida ou ponteiro de memória.
- **NX_SIZE_ERROR** (0x09) Bloco inválido ou tamanho da memória.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Create a packet pool of 32000 bytes starting at physical
   address 0x10000000. */
status = nx_packet_pool_create(&pool_0, "Default Pool", 128,
                               (void *) 0x10000000, 32000);

/* If status is NX_SUCCESS, the packet pool has been successfully
   created. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_delete"></a>nx_packet_pool_delete
Eliminar piscina de pacotes previamente criada

### <a name="prototype"></a>Prototype  

```c
UINT  nx_packet_pool_delete(NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a>Descrição

Este serviço elimina um pacote de pacotes previamente criado. NetX Duo verifica quaisquer fios atualmente suspensos em pacotes na piscina de pacotes e limpa a suspensão.

### <a name="parameters"></a>Parâmetros

- **pool_ptr** Ponteiro do bloco de controlo da piscina de pacote.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Pacotes de sucesso eliminar.
- **NX_PTR_ERROR** (0x07) Ponteiro de piscina inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

Sim

### <a name="example"></a>Exemplo

```c
/* Delete a previously created packet pool. */
status = nx_packet_pool_delete(&pool_0);

/* If status is NX_SUCCESS, the packet pool has been successfully
   deleted. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_info_get"></a>nx_packet_pool_info_get
Recuperar informações sobre uma piscina de pacotes

### <a name="prototype"></a>Prototype  

```c
UINT nx_packet_pool_info_get(
    NX_PACKET_POOL *pool_ptr,
    ULONG *total_packets,
    ULONG *free_packets,
    ULONG *empty_pool_requests,
    ULONG *empty_pool_suspensions,
    ULONG *invalid_packet_releases);
```
### <a name="description"></a>Descrição

Este serviço obtém informações sobre a piscina de pacotes especificado.

> [!IMPORTANT]  
> *Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao chamador*.

### <a name="parameters"></a>Parâmetros

- **pool_ptr** Ponteiro para piscina de pacotes previamente criada.
- **total_packets** Ponteiro para destino para o número total de pacotes na piscina.
- **free_packets** Ponteiro para o destino para o número total de pacotes atualmente gratuitos.
- **empty_pool_requests** Ponteiro para o destino do número total de pedidos de atribuição quando a piscina estava vazia.
- **empty_pool_suspensions** Ponteiro para o destino do número total de suspensões de piscina vazias.
- **invalid_packet_releases** Ponteiro para o destino do número total de lançamentos de pacotes inválidos.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Recuperação de informações de piscina de pacotes bem sucedidos.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios e temporizadores

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Retrieve packet pool information. */
status = nx_packet_pool_info_get(&pool_0,
                                 &total_packets,
                                 &free_packets,
                                 &empty_pool_requests,
                                 &empty_pool_suspensions,
                                 &invalid_packet_releases);

/* If status is NX_SUCCESS, packet pool information was
   retrieved. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_low_watermark_set"></a>nx_packet_pool_low_watermark_set
Definir pacote piscina baixa marca de água

### <a name="prototype"></a>Prototype  

```c
UINT nx_packet_pool_low_watermark_set(
    NX_PACKET_POOL *pool_ptr,
    ULONG low_watermark);
```
### <a name="description"></a>Descrição

Este serviço configura a marca de água baixa para a piscina de pacotes especificado. Uma vez definido o baixo valor da marca de água, o TCP ou a UDP não fazem fila dos pacotes recebidos se o número de pacotes disponíveis na piscina for inferior à marca de água baixa da piscina, impedindo que a piscina do pacote seja esfomeada de pacotes. Este serviço está disponível se a biblioteca NetX Duo for construída com a opção ***NX_ENABLE_LOW_WATERMARK*** definida.

### <a name="parameters"></a>Parâmetros

- **pool_ptr** Ponteiro para bloco de controlo de piscina de pacote.
- **low_watermark** Baixo valor de marca de água a configurar

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) definir com sucesso o baixo valor da marca de água.
- **NX_NOT_SUPPORTED** (0x4B) A função de marca de água baixa não está incorporada no NetX Duo.
- **NX_PTR_ERROR** (0x07) Ponteiro de piscina inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Set pool_0 low watermark value to 2. */
status = nx_packet_pool_create(&pool_0, 2);

/* If status is NX_SUCCESS, the low watermark value is set for
   pool_0.*/
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_release"></a>nx_packet_release
Liberação pacote previamente atribuído

### <a name="prototype"></a>Prototype  

```c
UINT nx_packet_release(NX_PACKET *packet_ptr);
```
### <a name="description"></a>Descrição

Este serviço liberta um pacote, incluindo quaisquer pacotes adicionais acorrentados ao pacote especificado. Se outro fio for bloqueado na atribuição do pacote, é dado o pacote e retomado.

> [!NOTE]  
> *O pedido deve evitar a libertação de um pacote mais de uma vez, porque fazê-lo irá causar resultados imprevisíveis*.

### <a name="parameters"></a>Parâmetros

- **packet_ptr** Ponteiro do pacote.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Lançamento de pacote bem sucedido.
- **NX_PTR_ERROR** (0x07) Ponteiro do pacote inválido.
- **NX_UNDERFLOW** (0x02) O ponteiro prepend é inferior ao arranque da carga útil.
- **NX_OVERFLOW** (0x03) O ponteiro do apêndice é maior do que a extremidade da carga útil.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs (controladores de rede de aplicações)

### <a name="preemption-possible"></a>Preempção Possível

Sim

### <a name="example"></a>Exemplo

```c
/* Release a previously allocated packet. */
status = nx_packet_release(packet_ptr);

/* If status is NX_SUCCESS, the packet has been returned to the
   packet pool it was allocated from. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_transmit_release

## <a name="nx_packet_transmit_release"></a>nx_packet_transmit_release
Liberte um pacote transmitido

### <a name="prototype"></a>Prototype  

```c
UINT nx_packet_transmit_release(NX_PACKET *packet_ptr);
```
### <a name="description"></a>Descrição

Para pacotes não TCP, este serviço liberta um pacote transmitido, incluindo quaisquer pacotes adicionais acorrentados ao pacote especificado. Se outro fio for bloqueado na atribuição do pacote, é dado o pacote e retomado. Para um pacote TCP transmitido, o pacote é marcado como sendo transmitido, mas não libertado até que o pacote seja reconhecido. Este serviço é normalmente chamado do controlador de rede da aplicação após a transmissão de um pacote.

> [!WARNING] 
> *O controlador de rede deve remover o cabeçalho dos meios de comunicação físicos e ajustar o comprimento do pacote antes de ligar para este serviço*.

### <a name="parameters"></a>Parâmetros

- **packet_ptr** Ponteiro do pacote.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Libertação bem sucedida do pacote de transmissão.
- **NX_PTR_ERROR** (0x07) Ponteiro do pacote inválido.
- **NX_UNDERFLOW** (0x02) O ponteiro prepend é inferior ao arranque da carga útil.
- **NX_OVERFLOW** (0x03) O ponteiro do apêndice é maior do que a extremidade da carga útil.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores, controladores de rede de aplicações (incluindo ISRs)

### <a name="preemption-possible"></a>Preempção Possível

Sim

### <a name="example"></a>Exemplo

```c
/* Release a previously allocated packet that was just transmitted
   from the application network driver. */
status = nx_packet_transmit_release(packet_ptr);

/* If status is NX_SUCCESS, the transmitted packet has been
   returned to the packet pool it was allocated from. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release

## <a name="nx_rarp_disable"></a>nx_rarp_disable
Desativar o Protocolo de Resolução de Endereços Reversos (RARP)

### <a name="prototype"></a>Prototype  

```c
UINT nx_rarp_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descrição

Este serviço desativa o componente RARP do NetX Duo para a instância IP específica. Para um sistema multihome, este serviço desativa o RARP em todas as interfaces.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) RaRP com sucesso.
- **NX_NOT_ENABLED** (0x14) RARP não estava ativado.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Disable RARP on the previously created IP instance. */
status = nx_rarp_disable(&ip_0);

/* If status is NX_SUCCESS, RARP is disabled. */
```
### <a name="see-also"></a>Consulte também

- nx_rarp_enable
- nx_rarp_info_get

## <a name="nx_rarp_enable"></a>nx_rarp_enable
Ativar o Protocolo de Resolução de Endereços Reversos (RARP)

### <a name="prototype"></a>Prototype  

```c
UINT nx_rarp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descrição

Este serviço permite o componente RARP do NetX Duo para a instância IP específica. Os componentes RARP procuram através de todas as interfaces de rede anexas para um endereço IP zero. Um endereço IP zero indica que a interface ainda não tem a atribuição de endereço IP. A RARP tenta resolver o endereço IP, permitindo o processo RARP nessa interface.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) RARP bem sucedido.
- **NX_IP_ADDRESS_ERROR** endereço IP (0x21) já é válido.
- **NX_ALREADY_ENABLED** (0x15) RARP já estava ativado.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Enable RARP on the previously created IP instance. */
status = nx_rarp_enable(&ip_0);

/* If status is NX_SUCCESS, RARP is enabled and is attempting to
   resolve this IP instance’s address by querying the network. */
```
### <a name="see-also"></a>Consulte também

- nx_rarp_disable
- nx_rarp_info_get

## <a name="nx_rarp_info_get"></a>nx_rarp_info_get
Recuperar informações sobre as atividades da RARP

### <a name="prototype"></a>Prototype  

```c
UINT nx_rarp_info_get(
    NX_IP *ip_ptr,
    ULONG *rarp_requests_sent,
    ULONG *rarp_responses_received,
    ULONG *rarp_invalid_messages);
```
### <a name="description"></a>Descrição

Este serviço obtém informações sobre as atividades da RARP para a instância IP especificada.

> [!IMPORTANT]  
> *Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao chamador*.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **rarp_requests_sent** Ponteiro para destino para o número total de pedidos de RARP enviados.
- **rarp_responses_received** Ponteiro para destino para o número total de respostas RARP recebidas.
- **rarp_invalid_messages** Ponteiro para o destino do número total de mensagens inválidas.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Recuperação de informações rarp bem sucedidas.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Retrieve RARP information from previously created IP
   Instance 0. */
status = nx_rarp_info_get(&ip_0,
                          &rarp_requests_sent,
                          &rarp_responses_received,
                          &rarp_invalid_messages);

/* If status is NX_SUCCESS, RARP information was retrieved. */
```
### <a name="see-also"></a>Consulte também

- nx_rarp_disable
- nx_rarp_enable

## <a name="nx_system_initialize"></a>nx_system_initialize
Inicialize o Sistema NetX Duo

### <a name="prototype"></a>Prototype  

```c
VOID nx_system_initialize(VOID);
```
### <a name="description"></a>Descrição

Este serviço inicializa os recursos básicos do sistema NetX Duo em preparação para utilização. Deve ser chamado pela aplicação durante a inicialização e antes de qualquer outra chamada NetX Duo ser feita.

### <a name="parameters"></a>Parâmetros

Nenhum

### <a name="return-values"></a>Valores de devolução

Nenhum

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores, ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

Gestão de Sistema

### <a name="example"></a>Exemplo

```c
/* Initialize NetX Duo for operation. */
nx_system_initialize();

/* At this point, NetX Duo is ready for IP creation and all
   subsequent network operations. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_tcp_client_socket_bind"></a>nx_tcp_client_socket_bind
Ligação da tomada TCP do cliente à porta TCP

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_client_socket_bind(
    NX_TCP_SOCKET *socket_ptr,
    UINT port,
    ULONG wait_option);
```
### <a name="description"></a>Descrição

Este serviço liga a tomada do cliente TCP previamente criada à porta TCP especificada. As tomadas TCP válidas variam de 0 a 0xFFFF. Se a porta TCP especificada não estiver disponível, o serviço suspende de acordo com a opção de espera fornecida.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada TCP previamente criada.
- **número da porta** para ligar (1 a 0xFFFF). Se o número da porta for NX_ANY_PORT (0x0000), a instância IP procurará a próxima porta livre e usará-a para a encadernação.
- **wait_option** Define como o serviço se comporta se a porta já está ligada a outra tomada. As opções de espera são definidas da seguinte forma:
- **NX_NO_WAIT** (0x00000000)
- **NX_WAIT_FOREVER** (0xFFFFFFFF)
- **valor de tempo limite em carrapatos** (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Ligação de tomada bem sucedida.
- **NX_ALREADY_BOUND** (0x22) Esta tomada já está ligada a outra porta TCP.
- **NX_PORT_UNAVAILABLE** (0x23) O porto já está ligado a uma tomada diferente.
- **NX_NO_FREE_PORTS** (0x45) Não há porta livre.
- **NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.
- **porta NX_INVALID_PORT** (0x46) Inválida.
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Bind a previously created client socket to port 12 and wait for 7
   timer ticks for the bind to complete. */
status = nx_tcp_client_socket_bind(&client_socket, 12, 7);

/* If status is NX_SUCCESS, the previously created client_socket is
   bound to port 12 on the associated IP instance. */
```
### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_client_socket_connect"></a>nx_tcp_client_socket_connect
Ligue a tomada TCP do cliente

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG server_ip,
    UINT server_port,
    ULONG wait_option);
```
### <a name="description"></a>Descrição

Este serviço liga a tomada do cliente TCP previamente criada e ligada à porta do servidor especificado. As portas de servidores TCP válidas variam de 0 a 0xFFFF. Se a ligação não estiver concluída imediatamente, o serviço suspende de acordo com a opção de espera fornecida.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada TCP previamente criada.
- **server_ip** O endereço IP do servidor.
- **server_port** Número da porta do servidor para ligar a** (1 a 0xFFFF).
- **wait_option** Define como o serviço se comporta enquanto a ligação está sendo estabelecida. As opções de espera são definidas da seguinte forma:
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **valor de tempo limite em carrapatos** (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Ligação de tomadas bem sucedidas.
- **NX_NOT_BOUND** (0x24) A tomada não está ligada.
- **NX_NOT_CLOSED** (0x35) A tomada não se encontra fechada.
- **NX_IN_PROGRESS** (0x37) Não foi especificada qualquer espera, a tentativa de ligação está em curso.
- **NX_INVALID_INTERFACE** (0x4C) Interface inválida fornecida.
- **NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IP do servidor inválido.
- **porta NX_INVALID_PORT** (0x46) Inválida.
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Initiate a TCP connection from a previously created and bound
   client socket. The connection requested in this example is to
   port 12 on the server with the IP address of 1.2.3.5. This
   service will wait 300 timer ticks for the connection to take
   place before giving up. */
status = nx_tcp_client_socket_connect(&client_socket,
                                      IP_ADDRESS(1,2,3,5),
                                      12, 300);

/* If status is NX_SUCCESS, the previously created and bound
   client_socket is connected to port 12 on IP 1.2.3.5. */
```
### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_client_socket_port_get"></a>nx_tcp_client_socket_port_get
Obtenha o número da porta vinculado à tomada TCP do cliente

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_client_socket_port_get(
    NX_TCP_SOCKET *socket_ptr,
    UINT *port_ptr);
```
### <a name="description"></a>Descrição

Este serviço recupera o número de porta associado à tomada, o que é útil para encontrar a porta atribuída pela NetX Duo em situações em que o NX_ANY_PORT foi especificado no momento em que a tomada foi ligada.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada TCP previamente criada.
- **port_ptr** Ponteiro para o destino para o número da porta de retorno. Os números de porta válidos são (1 a 0xFFFF).

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Ligação de tomada bem sucedida.
- **NX_NOT_BOUND** (0x24) Esta tomada não está ligada a uma porta.
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida ou ponteiro de retorno da porta.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Get the port number of previously created and bound client
   socket. */
status = nx_tcp_client_socket_port_get(&client_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
   socket is bound to. */
```
### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_client_socket_unbind"></a>nx_tcp_client_socket_unbind
Tomada de cliente unbind TCP da porta TCP

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_client_socket_unbind(NX_TCP_SOCKET *socket_ptr);
```
### <a name="description"></a>Descrição

Este serviço liberta a encadernação entre a tomada do cliente TCP e uma porta TCP. Se houver outros fios à espera de ligar outra tomada ao mesmo número de porta, o primeiro fio suspenso fica ligado a esta porta.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada TCP previamente criada.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Tomada desaderada com sucesso.
- **NX_NOT_BOUND** (0x24) Tomada não estava ligada a nenhuma porta.
- **NX_NOT_CLOSED** (0x35) A tomada não foi desligada.
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

Sim

### <a name="example"></a>Exemplo

```c
/* Unbind a previously created and bound client TCP socket. */
status = nx_tcp_client_socket_unbind(&client_socket);

/* If status is NX_SUCCESS, the client socket is no longer
   bound. */
```
### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_enable"></a>nx_tcp_enable
Ativar o componente TCP do NetX Duo

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descrição

Este serviço permite o componente do Protocolo de Controlo de Transmissão (TCP) da NetX Duo. Após ativação, as ligações TCP podem ser estabelecidas pelo pedido.

### <a name="parameters"></a>Parâmetros  

- **ip_ptr** Ponteiro para instância IP previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) TCP bem sucedido.
- **NX_ALREADY_ENABLED** (0x15) TCP já está ativado.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Enable TCP on a previously created IP instance ip_0. */
status = nx_tcp_enable(&ip_0);

/* If status is NX_SUCCESS, TCP is enabled on the IP instance. */
```
### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_free_port_find"></a>nx_tcp_free_port_find
Encontre a próxima porta TCP disponível

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_free_port_find(
    NX_IP *ip_ptr,
    UINT port,
    UINT *free_port_ptr);
```
### <a name="description"></a>Descrição

Este serviço tenta localizar uma porta TCP gratuita (desvinculada) a partir da porta fornecida pela aplicação. A lógica de pesquisa irá envolver-se se a pesquisa atingir o valor máximo da porta de 0xFFFF. Se a pesquisa for bem sucedida, a porta livre é devolvida na variável apontada por *free_port_ptr*.

> [!WARNING]  
> *Este serviço pode ser chamado de outro fio e ter a mesma porta devolvida. Para evitar esta condição de regata, a aplicação pode pretender colocar este serviço e a tomada do cliente em si liga-se sob a proteção de um mutex*.

### <a name="parameters"></a>Parâmetros  

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **porto** Número da porta para iniciar a pesquisa em (1 a 0xFFFF).
- **free_port_ptr** Ponteiro para o destino valor de retorno de porto livre.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Achado de porta livre com sucesso.
- **NX_NO_FREE_PORTS** (0x45) Não foram encontradas portas livres.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.
- **NX_INVALID_PORT** (0x46) O número de porta especificado é inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Locate a free TCP port, starting at port 12, on a previously
   created IP instance. */
status = nx_tcp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS, "free_port" contains the next free port
   on the IP instance. */
```
### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_info_get"></a>nx_tcp_info_get
Recuperar informações sobre atividades da TCP

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_info_get(
    NX_IP *ip_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_invalid_packets,
    ULONG *tcp_receive_packets_dropped,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_connections,
    ULONG *tcp_disconnections,
    ULONG *tcp_connections_dropped,
    ULONG *tcp_retransmit_packets);
```
### <a name="description"></a>Descrição

Este serviço obtém informações sobre as atividades da TCP para a instância IP especificada.

> [!IMPORTANT]  
> *Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao chamador*.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **tcp_packets_sent** Ponteiro para o destino para o número total de pacotes TCP enviados.
- **tcp_bytes_sent** Ponteiro para o destino para o número total de bytes TCP enviados.
- **tcp_packets_received** Ponteiro para o destino do número total de pacotes TCP recebidos.
- **tcp_bytes_received** Ponteiro para o destino do número total de bytes TCP recebidos.
- **tcp_invalid_packets** Ponteiro para o destino do número total de pacotes TCP inválidos.
- **tcp_receive_packets_dropped** O ponteiro para o destino do número total de pacotes de receção TCP caiu.
- **tcp_checksum_errors** Ponteiro para o destino do número total de pacotes TCP com erros de checkum.
- **tcp_connections** Ponteiro para o destino do número total de ligações TCP.
- **tcp_disconnections** Ponteiro para o destino do número total de desconexões TCP.
- **tcp_connections_dropped** O ponteiro para o destino do número total de ligações TCP diminuiu.
- **tcp_retransmit_packets** Ponteiro para o destino do número total de pacotes TCP retransmiitados.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Recuperação de informação bem sucedida da TCP.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Retrieve TCP information from previously created IP Instance
   ip_0. */
status = nx_tcp_info_get(&ip_0,
                         &tcp_packets_sent,
                         &tcp_bytes_sent,
                         &tcp_packets_received,
                         &tcp_bytes_received,
                         &tcp_invalid_packets,
                         &tcp_receive_packets_dropped,
                         &tcp_checksum_errors,
                         &tcp_connections,
                         &tcp_disconnections
                         &tcp_connections_dropped,
                         &tcp_retransmit_packets);

/* If status is NX_SUCCESS, TCP information was retrieved. */
```
### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_accept"></a>nx_tcp_server_socket_accept
Aceitar ligação TCP

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_server_socket_accept(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Descrição

Este serviço aceita (ou prepara-se para aceitar) um pedido de ligação ao cliente TCP para uma porta previamente configurada para escuta. Este serviço pode ser chamado imediatamente após a aplicação chamar o serviço de escuta ou de re-escuta ou depois de a rotina de chamada de escuta ser chamada quando a ligação do cliente estiver realmente presente. Se uma ligação não puder ser estabelecida imediatamente, o serviço suspende de acordo com a opção de espera fornecida.

> [!WARNING]  
> *A aplicação deve ligar **nx_tcp_server_socket_unaccept** depois de a ligação já não ser necessária para remover a ligação da tomada do servidor à porta do servidor*.

> [!IMPORTANT]  
> *As rotinas de chamada de aplicação são chamadas a partir do fio de ajuda do IP*.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para o bloco de controlo da tomada do servidor TCP.
- **wait_option** Define como o serviço se comporta enquanto a ligação está sendo estabelecida. As opções de espera são definidas da seguinte forma:
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **valor de tempo limite em carrapatos** (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) A tomada do servidor TCP bem sucedida aceita (ligação passiva).
- **NX_NOT_LISTEN_STATE** (0x36) A tomada do servidor fornecida não está num estado de escuta.
- **NX_IN_PROGRESS** (0x37) Não foi especificada qualquer espera, a tentativa de ligação está em curso.
- **NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.
- **NX_PTR_ERROR** (0x07) Erro do ponteiro da tomada.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
       example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
NX_PACKET *my_packet;
UINT status, i;
    /* Assuming that:
       "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created and the
        link is enabled "my_pool" packet pool has already been
        created
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
                         "Port 12 Server Socket",
                          NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                          NX_IP_TIME_TO_LIVE, 100,
                          NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
                                port_12_connect_request);

    /* Loop to process 5 server connections, sending
       "Hello_and_Goodbye" to each client and then disconnecting.*/
    for (i = 0; i < 5; i++)
    {

        /* Get the semaphore that indicates a client connection
        request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
           complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {

            /* Allocate a packet for the "Hello_and_Goodbye"
               message */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                                         NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                                  sizeof("Hello_and_Goodbye"),
                                  &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
               /* Error, release the packet. */
               nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
         }

         /* Unaccept the server socket. Note that unaccept is called
            even if disconnect or accept fails. */
         nx_tcp_server_socket_unaccept(&server_socket);

         /* Setup server socket for listening with this socket
            again. */
         nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
     }

     /* We are now done so unlisten on server port 12. */
     nx_tcp_server_socket_unlisten(&my_ip, 12);

     /* Delete the server socket. */
     nx_tcp_socket_delete(&server_socket);
}
```
### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_listen"></a>nx_tcp_server_socket_listen
Ativar a escuta da ligação do cliente na porta TCP

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_server_socket_listen(
    NX_IP *ip_ptr, UINT port,
    NX_TCP_SOCKET *socket_ptr,
    UINT listen_queue_size,
    VOID (*listen_callback)(NX_TCP_SOCKET *socket_ptr, UINT port));
```
### <a name="description"></a>Descrição

Este serviço permite ouvir um pedido de ligação ao cliente na porta TCP especificada. Quando um pedido de ligação ao cliente é recebido, a tomada do servidor fornecida fica ligada à porta especificada e a função de chamada de chamada de chamada de ouvido fornecida é chamada.

O processamento da rotina de chamada de escuta está completamente à altura da aplicação. Pode conter lógica para acordar um fio de aplicação que posteriormente executa uma operação de aceitação. Se a aplicação já tiver um fio suspenso no processamento de aceitação para esta tomada, a rotina de chamada de escuta pode não ser necessária.

Se a aplicação pretender manusear ligações adicionais ao cliente na mesma porta, o ***nx_tcp_server_socket_relisten*** deve ser chamado com uma tomada disponível (uma tomada no estado FECHADO) para a próxima ligação. Até que o serviço de re-ouvir seja chamado, as ligações adicionais do cliente são em fila. Quando a profundidade máxima da fila é excedida, o pedido de ligação mais antigo é retirado a favor da fila do novo pedido de ligação. A profundidade máxima da fila é especificada por este serviço.

> [!IMPORTANT]  
> *As rotinas de chamada de aplicação são chamadas a partir do fio interno do ajudante IP*.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **porto** Número da porta para ouvir (1 a 0xFFFF).
- **socket_ptr** Ponteiro para tomada a utilizar para a ligação.
- **listen_queue_size** Número de pedidos de ligação ao cliente que podem ser na fila.
- **listen_callback** Função de aplicação para ligar quando a ligação é recebida. Se for especificado um NU, a função de chamada de escuta é desativada.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Porta TCP bem sucedida ouvir.
- **NX_MAX_LISTEN** (0x33) Não há mais estruturas de pedido de escuta disponíveis. A NX_MAX_LISTEN_REQUESTS constante em **_nx_api.h_** define quantos pedidos de escuta ativa são possíveis.
- **NX_NOT_CLOSED** (0x35) A tomada do servidor fornecida não está fechada.
- **NX_ALREADY_BOUND** (0x22) A tomada do servidor fornecida já está ligada a uma porta.
- **NX_DUPLICATE_LISTEN** (0x34) Já existe um pedido de escuta ativo para este porto.
- **NX_INVALID_PORT** (0x46) Porta inválida especificada.
- **NX_PTR_ERROR** (0x07) IP inválido ou ponteiro de tomada.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
   /* Simply set the semaphore to wake up the server thread.*/
   tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
   /* The client has initiated a disconnect on this socket.
   This example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
NX_PACKET *my_packet;
UINT status, i;
   /* Assuming that:
      "port_12_semaphore" has already been created with an
      initial count of 0 "my_ip" has already been created
      and the link is enabled "my_pool" packet pool has already
      been created.
   */

   /* Create the server socket. */
   nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server
                        Socket",
                        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                        NX_IP_TIME_TO_LIVE, 100,
                        NX_NULL, port_12_disconnect_request);

   /* Setup server listening on port 12. */
   nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
                               port_12_connect_request);

   /* Loop to process 5 server connections, sending
      "Hello_and_Goodbye" to
      each client and then disconnecting. */
   for (i = 0; i < 5; i++)
   {

        /* Get the semaphore that indicates a client connection
           request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection
           to complete. */
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
           if (status == NX_SUCCESS)
        {

              /* Allocate a packet for the "Hello_and_Goodbye"
                 message. */
              nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                                 NX_WAIT_FOREVER);

              /* Place "Hello_and_Goodbye" in the packet. */
              nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                                    sizeof("Hello_and_Goodbye"),
                                    &my_pool,
                                    NX_WAIT_FOREVER);

             /* Send "Hello_and_Goodbye" to client. */
             nx_tcp_socket_send(&server_socket, my_packet, 200);

             /* Check for an error. */
             if (status)
             {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
             }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
         }
         /* Unaccept the server socket. Note that unaccept is called
            even if disconnect or accept fails. */
         nx_tcp_server_socket_unaccept(&server_socket);

         /* Setup server socket for listening with this socket
         again. */
         nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
     }
     /* We are now done so unlisten on server port 12. */
     nx_tcp_server_socket_unlisten(&my_ip, 12);
     /* Delete the server socket. */
     nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_relisten"></a>nx_tcp_server_socket_relisten
Re-ouvir a ligação do cliente na porta TCP

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_server_socket_relisten(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr);
```
### <a name="description"></a>Descrição

Este serviço é chamado depois de ter sido recebida uma ligação numa porta que foi configurada anteriormente para escuta. O principal objetivo deste serviço é fornecer uma nova tomada de servidor para a próxima ligação ao cliente. Se um pedido de ligação for feito em fila, a ligação será processada imediatamente durante esta chamada de serviço.

> [!IMPORTANT]  
> *A mesma rotina de chamada especificada pelo pedido de escuta original também é chamada quando existe uma ligação para esta nova tomada do servidor*.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **porto** Número da porta para voltar a ouvir (1 a 0xFFFF).
- **socket_ptr** Tomada para utilizar para a próxima ligação ao cliente.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Porta TCP bem sucedida a ouvir.
- **NX_NOT_CLOSED** (0x35) A tomada do servidor fornecida não está fechada.
- **NX_ALREADY_BOUND** (0x22) A tomada do servidor fornecida já está ligada a uma porta.
- **NX_INVALID_RELISTEN** (0x47) Já existe um ponteiro de tomada válido para esta porta ou a porta especificada não tem um pedido de escuta ativo.
- **NX_CONNECTION_PENDING** (0x48) O mesmo que NX_SUCCESS, exceto que houve um pedido de ligação em fila e foi processado durante esta chamada.
- **NX_INVALID_PORT** (0x46) Porta inválida especificada.
- **NX_PTR_ERROR** (0x07) IP inválido ou ouvir o ponteiro de retorno.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{

   /* Simply set the semaphore to wake up the server thread.*/
   tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
   /* The client has initiated a disconnect on this socket. This
      example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{

NX_PACKET *my_packet;
UINT status, i;

   /* Assuming that:
     "port_12_semaphore" has already been created with an initial
     count of 0.
    "my_ip" has already been created and the link is enabled.
    "my_pool" packet pool has already been created. */

   /* Create the server socket. */
   nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server Socket",
                                 NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                                 NX_IP_TIME_TO_LIVE, 100,
                                 NX_NULL, port_12_disconnect_request);

   /* Setup server listening on port 12. */
   nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
                               port_12_connect_request);

   /* Loop to process 5 server connections, sending
      "Hello_and_Goodbye" to each client then disconnecting. */
   for (i = 0; i < 5; i++)
   {

       /* Get the semaphore that indicates a client connection
          request is present. */
       tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

       /* Wait for 200 ticks for the client socket connection to
          complete. */
       status = nx_tcp_server_socket_accept(&server_socket, 200);

       /* Check for a successful connection. */
          if (status == NX_SUCCESS)
       {

             /* Allocate a packet for the "Hello_and_Goodbye"
                message. */
             nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                                NX_WAIT_FOREVER);

             /* Place "Hello_and_Goodbye" in the packet. */
             nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                                   sizeof("Hello_and_Goodbye"),
                                   &my_pool, NX_WAIT_FOREVER);

             /* Send "Hello_and_Goodbye" to client. */
             nx_tcp_socket_send(&server_socket, my_packet, 200);

             /* Check for an error. */
             if (status)
             {

                /* Error, release the packet. */
                nx_packet_release(my_packet);
             }

             /* Now disconnect the server socket from the client. */
             nx_tcp_socket_disconnect(&server_socket, 200);
         }

         /* Unaccept the server socket. Note that unaccept is
            called even if disconnect or accept fails. */
         nx_tcp_server_socket_unaccept(&server_socket);

         /* Setup server socket for listening with this socket
            again. */
         nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
     }

     /* We are now done so unlisten on server port 12. */
     nx_tcp_server_socket_unlisten(&my_ip, 12);

     /* Delete the server socket. */
     nx_tcp_socket_delete(&server_socket);
}
```
### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_unaccept"></a>nx_tcp_server_socket_unaccept
Remova a associação da tomada com a porta de escuta

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_server_socket_unaccept(NX_TCP_SOCKET *socket_ptr);
```
### <a name="description"></a>Descrição

Este serviço remove a associação entre esta tomada do servidor e a porta do servidor especificada. O pedido deve ligar para este serviço após uma desconexão ou após uma chamada de aceitação infrutífera.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada do servidor previamente configurada.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Tomada de servidor bem sucedida não acepte.
- **NX_NOT_LISTEN_STATE** (0x36) A tomada do servidor encontra-se num estado impróprio e provavelmente não está desligada.
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
NX_PACKET_POOL        my_pool;
NX_IP                 my_ip;
NX_TCP_SOCKET         server_socket;
void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{

   /* Simply set the semaphore to wake up the server thread. */
   tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
   /* The client has initiated a disconnect on this socket. This example
   doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{

NX_PACKET  *my_packet;
UINT       status, i;

   /* Assuming that:
     "port_12_semaphore" has already been created with an initial count
      of 0 "my_ip" has already been created and the link is enabled
     "my_pool" packet pool has already been created
   */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server
                         Socket",NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                         NX_IP_TIME_TO_LIVE, 100,NX_NULL,
                         port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
                                port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye"
       to
       each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {

        /* Get the semaphore that indicates a client connection request
           is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
           complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

       /* Check for a successful connection. */
          if (status == NX_SUCCESS)
       {
             /* Allocate a packet for the "Hello_and_Goodbye" message. */
             nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                                NX_WAIT_FOREVER);

             /* Place "Hello_and_Goodbye" in the packet. */
             nx_packet_data_append(my_packet,
                      "Hello_and_Goodbye",sizeof("Hello_and_Goodbye"),
                      &my_pool, NX_WAIT_FOREVER);

             /* Send "Hello_and_Goodbye" to client. */
             nx_tcp_socket_send(&server_socket, my_packet, 200);

             /* Check for an error. */
             if (status)
             {

                /* Error, release the packet. */
                nx_packet_release(my_packet);
             }

             /* Now disconnect the server socket from the client. */
             nx_tcp_socket_disconnect(&server_socket, 200);
       }

       /* Unaccept the server socket. Note that unaccept is called even
          if disconnect or accept fails. */
       nx_tcp_server_socket_unaccept(&server_socket);

      /* Setup server socket for listening with this socket again. */
      nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }

    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```
### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_unlisten"></a>nx_tcp_server_socket_unlisten
Desativar a escuta da ligação ao cliente na porta TCP

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_server_socket_unlisten(
    NX_IP *ip_ptr, 
    UINT port);
```
### <a name="description"></a>Descrição

Este serviço desativa a audição de um pedido de ligação ao cliente na porta TCP especificada.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **porto** Número de portas para desativar a audição (0 a 0xFFFF).

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) TCP bem sucedido ouvir desativar.
- **NX_ENTRY_NOT_FOUND** (0x16) A audição não estava ativada para a porta especificada.
- **NX_INVALID_PORT** (0x46) Porta inválida especificada.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
NX_PACKET_POOL       my_pool;
NX_IP                my_ip;
NX_TCP_SOCKET        server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{

     /* Simply set the semaphore to wake up the server thread. */
     tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{

     /* The client has initiated a disconnect on this socket. This example
        doesn't use this callback.*/
}

void port_12_server_thread_entry(ULONG id)
{

NX_PACKET *my_packet;
UINT status, i;

     /* Assuming that:
       "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
       "my_pool" packet pool has already been created
     */

     /* Create the server socket. */
     nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server Socket",
                          NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                          NX_IP_TIME_TO_LIVE, 100,
                          NX_NULL, port_12_disconnect_request);

     /* Setup server listening on port 12. */
     nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
                                 port_12_connect_request);

     /* Loop to process 5 server connections, sending "Hello_and_Goodbye" to
        each client and then disconnecting. */
     for (i = 0; i < 5; i++)
     {

         /* Get the semaphore that indicates a client connection request is
            present. */
         tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

         /* Wait for 200 ticks for the client socket connection to complete.*/
         status = nx_tcp_server_socket_accept(&server_socket, 200);

         /* Check for a successful connection. */
         if (status == NX_SUCCESS)
         {

             /* Allocate a packet for the "Hello_and_Goodbye" message. */
             nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                                NX_WAIT_FOREVER);

             /* Place "Hello_and_Goodbye" in the packet. */
             nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                                   sizeof("Hello_and_Goodbye"), &my_pool,
                                   NX_WAIT_FOREVER);

             /* Send "Hello_and_Goodbye" to client. */
             nx_tcp_socket_send(&server_socket, my_packet, 200);

             /* Check for an error. */
             if (status)
             {

                /* Error, release the packet. */
                nx_packet_release(my_packet);
             }

             /* Now disconnect the server socket from the client. */
             nx_tcp_socket_disconnect(&server_socket, 200);
          }

          /* Unaccept the server socket. Note that unaccept is called even if
             disconnect or accept fails. */
          nx_tcp_server_socket_unaccept(&server_socket);

          /* Setup server socket for listening with this socket again. */
          nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
     }
  
     /* We are now done so unlisten on server port 12. */
     nx_tcp_server_socket_unlisten(&my_ip, 12);

     /* Delete the server socket. */
     nx_tcp_socket_delete(&server_socket);
}
```
### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_bytes_available"></a>nx_tcp_socket_bytes_available
Recupera o número de bytes disponíveis para recuperação

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_bytes_available(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```
### <a name="description"></a>Descrição

Este serviço obtém o número de bytes disponíveis para recuperação na tomada TCP especificada. Note que a tomada TCP já deve estar ligada.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para tomada TCP previamente criada e conectada.
- **bytes_available** Ponteiro para destino para bytes disponíveis.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O Serviço executa com sucesso. O número de bytes disponíveis para leitura é devolvido ao chamador.
- **NX_NOT_CONNECTED** (0x38) A tomada não se encontra ligada.
- **NX_PTR_ERROR** (0x07) Ponteiros inválidos.
- **NX_NOT_ENABLED** (0x14) TCP não está ativado.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Get the bytes available for retrieval on the specified socket. */
status = nx_tcp_socket_bytes_available(&my_socket,&bytes_available);

/* Is status = NX_SUCCESS, the available bytes is returned in
   bytes_available. */
```
### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_create"></a>nx_tcp_socket_create
Criar tomada de cliente TCP ou servidor

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_create(
    NX_IP *ip_ptr, 
    NX_TCP_SOCKET *socket_ptr,
    CHAR *name, 
    ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG window_size,
    VOID (*urgent_data_callback)(NX_TCP_SOCKET *socket_ptr),
    VOID (*disconnect_callback)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Descrição

Este serviço cria um cliente TCP ou tomada de servidor para a instância IP especificada.

> [!NOTE]  
> *As rotinas de chamada de aplicação são chamadas a partir do fio associado a esta instância IP*.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **socket_ptr** Ponteiro para o novo bloco de controlo da tomada TCP.
- **nome** Nome da aplicação para esta tomada TCP.
- **type_of_service** Define o tipo de serviço para a transmissão, os valores legais são os seguintes:
    - **NX_IP_NORMAL** (0x00000000)
    - **NX_IP_MIN_DELAY** (0x00100000)
    - **NX_IP_MAX_DATA** (0x00080000)
    - **NX_IP_MAX_RELIABLE** (0x00040000)
    - **NX_IP_MIN_COST** (0x00020000)
- **fragmento** Especifica se é permitida a fragmentação ip. Se for especificado NX_FRAGMENT_OKAY** (0x0), é permitida a fragmentação ip. Se NX_DONT_FRAGMENT (0x4000) for especificado, a fragmentação ip está desativada.
- **time_to_live** Especifica o valor de 8 bits que define quantos routers este pacote pode passar antes de ser jogado fora. O valor predefinido é especificado por NX_IP_TIME_TO_LIVE.
- **window_size** Define o número máximo de bytes permitidos na fila de receção para esta tomada
- **urgent_data_callback** Função de aplicação que é chamada sempre que os dados urgentes são detetados no fluxo de receção. Se este valor for NX_NULL, os dados urgentes são ignorados.
- **disconnect_callback** Função de aplicação que é chamada sempre que uma desconexão é emitida pela tomada na outra extremidade da ligação. Se este valor for NX_NULL, a função de desconexão é desativada.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Tomada de cliente bem sucedida da TCP criar.
- **NX_OPTION_ERROR** (0x0A) Tipo de serviço inválido, fragmento, tamanho da janela inválido ou opção de tempo-tolive.
- **NX_PTR_ERROR** (0x07) IP inválido ou ponteiro de tomada.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e Threads

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Create a TCP client socket on the previously created IP instance,
   with normal delivery, IP fragmentation enabled, 0x80 time to
   live, a 200-byte receive window, no urgent callback routine, and
   the "client_disconnect" routine to handle disconnection initiated
   from the other end of the connection. */
status = nx_tcp_socket_create(&ip_0, &client_socket,
                             "Client Socket",
                             NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                             0x80, 200, NX_NULL
                             client_disconnect);

/* If status is NX_SUCCESS, the client socket is created and ready
   to be bound. */
```
### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_delete"></a>nx_tcp_socket_delete
Eliminar tomada TCP

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_delete(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Descrição

Este serviço elimina uma tomada TCP previamente criada. Se a tomada ainda estiver ligada ou ligada, o serviço devolve um código de erro.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Tomada TCP previamente criada

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Apagar a tomada com sucesso.
- **NX_NOT_CREATED** (0x27) Tomada não foi criada.
- **NX_STILL_BOUND** (0x42) A tomada ainda está ligada.
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Delete a previously created TCP client socket. */
status = nx_tcp_socket_delete(&client_socket);

/* If status is NX_SUCCESS, the client socket is deleted. */
```
### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_disconnect"></a>nx_tcp_socket_disconnect
Desligue as ligações de tomada de cliente e servidor

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_disconnect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Descrição

Este serviço desliga uma ligação estabelecida de tomada de cliente ou servidor. Uma desconexão de uma tomada do servidor deve ser seguida por um pedido não aceite, enquanto uma tomada de cliente desligada é deixada num estado pronto para outro pedido de ligação. Se o processo de desconexão não puder terminar imediatamente, o serviço suspende de acordo com a opção de espera fornecida.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada de cliente ou servidor previamente ligada.
- **wait_option** Define como o serviço se comporta enquanto a desconexão está em curso. As opções de espera são definidas da seguinte forma:
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **valor de tempo limite em carrapatos** (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Desconexão de tomadas com sucesso.
- **NX_NOT_CONNECTED** (0x38) A tomada especificada não está ligada.
- **NX_IN_PROGRESS** (0x37) A desconexão está em curso, não foi especificada qualquer espera.
- **NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

Sim 

### <a name="example"></a>Exemplo 

```c
/* Disconnect from a previously established connection and wait a
   maximum of 400 timer ticks. */
status = nx_tcp_socket_disconnect(&client_socket, 400);

/* If status is NX_SUCCESS, the previously connected socket (either
   as a result of the client socket connect or the server accept) is
   disconnected. */
```
### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_disconnect_complete_notify"></a>nx_tcp_socket_disconnect_complete_notify
Instalar a desconexão TCP completa notificar a função de retorno
 
### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_disconnect_complete_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_disconnect_complete_notify)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Descrição

Este serviço regista uma função de retorno que é invocada após a conclusão de uma operação de desconexão da tomada. A função de chamada completa da tomada TCP está disponível se o NetX Duo for construído com a opção ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** definida.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada de cliente ou servidor previamente ligada.
- **tcp_disconnect_complete_notify** A função de retorno a instalar.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) registou com sucesso a função de retorno.
- **NX_NOT_SUPPORTED** (0x4B) A função de notificação alargada não é incorporada na biblioteca NetX Duo NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) funcionalidade TCP não está ativada.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Install the disconnect complete notify callback function. */
status = nx_tcp_socket_disconnect_complete_notify(&client_socket,
                                                  callback);
```
### <a name="see-also"></a>Consulte também

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_setnx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_establish_notify"></a>nx_tcp_socket_establish_notify
Definir TCP estabelecer notificação função de retorno

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_establish_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_establish_notify)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Descrição

Este serviço regista uma função de retorno, que é chamada depois de uma tomada TCP fazer uma ligação. A tomada TCP estabelece a função de retorno de chamada se o NetX Duo for construído com a opção ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** definida.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada de cliente ou servidor previamente ligada.
- **tcp_establish_notify** Função de retorno invocada após a criação de uma ligação TCP.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) define com sucesso a função de notificação.
- **NX_NOT_SUPPORTED** (0x4B) A funcionalidade de notificação alargada não está integrada na biblioteca NetX Duo 
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) TCP não foi habilitado pelo pedido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Set the function pointer "callback" as the notify function NetX
   Duo will call when the connection is in the established state. */
status = nx_tcp_socket_establish_notify(&client_socket, callback);
```
### <a name="see-also"></a>Consulte também

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_info_get"></a>nx_tcp_socket_info_get
Recuperar informações sobre as atividades da tomada de TCP

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_retransmit_packets,
    ULONG *tcp_packets_queued,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_socket_state,
    ULONG *tcp_transmit_queue_depth,
    ULONG *tcp_transmit_window,
    ULONG *tcp_receive_window);
```
### <a name="description"></a>Descrição

Este serviço obtém informações sobre as atividades da tomada TCP para a instância de tomada TCP especificada.

> [!NOTE]  
> *Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao chamador*.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada TCP previamente criada.
- **tcp_packets_sent** Ponteiro para o destino para o número total de pacotes TCP enviados na tomada.
- **tcp_bytes_sent** Ponteiro para destino para o número total de bytes TCP enviados na tomada.
- **tcp_packets_received** Ponteiro para o destino do número total de pacotes TCP recebidos na tomada.
- **tcp_bytes_received** Ponteiro para o destino do número total de bytes TCP recebidos na tomada.
- **tcp_retransmit_packets** Ponteiro para o destino do número total de retransmissão de pacotes TCP.
- **tcp_packets_queued** Ponteiro para o destino do número total de pacotes TCP em fila na tomada.
- **tcp_checksum_errors** Ponteiro para o destino do número total de pacotes TCP com erros de verificação na tomada.
- **tcp_socket_state** Ponteiro para o destino do estado atual da tomada.
- **tcp_transmit_queue_depth** Ponteiro para o destino do número total de pacotes de transmissão ainda em fila à espera de ACK.
- **tcp_transmit_window** Ponteiro para o destino do tamanho atual da janela de transmissão.
- **tcp_receive_window** Ponteiro para o destino da corrente receber o tamanho da janela.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Recuperação de informações de tomadas TCP bem sucedidas.
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida. 
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Retrieve TCP socket information from previously created
   socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
                                &tcp_packets_sent,
                                &tcp_bytes_sent,
                                &tcp_packets_received,
                                &tcp_bytes_received,
                                &tcp_retransmit_packets,
                                &tcp_packets_queued,
                                &tcp_checksum_errors,
                                &tcp_socket_state,
                                &tcp_transmit_queue_depth,
                                &tcp_transmit_window,
                                &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```
### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_mss_get"></a>nx_tcp_socket_mss_get
Obtenha MSS de tomada

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_mss_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```
### <a name="description"></a>Descrição

Este serviço recupera o tamanho máximo de segmento local (MSS) da tomada especificada.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para tomada previamente criada.
- **mss** Destino para o regresso da MSS.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) MSS bem sucedidos obtêm.
- **NX_PTR_ERROR** (0x07) Tomada inválida ou ponteiro de destino MSS.
- **NX_NOT_ENABLED** (0x14) TCP não está ativado.
- **NX_CALLER_ERROR** (0x11) Caller não é um fio ou inicialização.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Get the MSS for the socket "my_socket". */
status = nx_tcp_socket_mss_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
   socket's current MSS value. */
```
### <a name="see-also"></a>Consulte também

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_peer_get"></a>nx_tcp_socket_mss_peer_get
Obtenha MSS da tomada TCP par

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_mss_peer_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *mss);
```
### <a name="description"></a>Descrição

Este serviço recupera o Tamanho Máximo do Segmento (MSS) anunciado pela tomada de pares.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para tomada previamente criada e conectada.
- **mss** Destino para devolver o MSS.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) MSS de sucesso.
- **NX_PTR_ERROR** (0x07) Tomada inválida ou ponteiro de destino MSS.
- **NX_NOT_ENABLED** (0x14) TCP não está ativado.
- **NX_CALLER_ERROR** (0x11) Caller não é um fio ou inicialização.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Get the MSS of the connected peer to the socket "my_socket". */
status = nx_tcp_socket_mss_peer_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
   socket peer’s advertised MSS value. */
```
### <a name="see-also"></a>Consulte também

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_set"></a>nx_tcp_socket_mss_set
Definir MSS de tomada

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_mss_set(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG mss);
```
### <a name="description"></a>Descrição

Este serviço define o tamanho máximo do segmento da tomada especificada (MSS). Note que o valor MSS deve estar dentro da interface de rede IP MTU, permitindo espaço para cabeçalhos IP e TCP.

Este serviço deve ser utilizado antes de uma tomada TCP iniciar o processo de ligação. Se o serviço for utilizado após a criação de uma ligação TCP, o novo valor não tem qualquer efeito na ligação.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para tomada previamente criada.
- **mss** Valor da MSS para definir.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Conjunto MSS bem sucedido.
- **NX_SIZE_ERROR** (0x09) O valor especificado de MSS é demasiado elevado.
- **NX_NOT_CONNECTED** (0x38) A ligação TCP não foi estabelecida 
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_NOT_ENABLED** (0x14) TCP não está ativado.
- **NX_CALLER_ERROR** (0x11) Caller não é um fio ou inicialização.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Set the MSS of the socket "my_socket" to 1000 bytes. */
status = nx_tcp_socket_mss_set(&my_socket, 1000);

/* If status is NX_SUCCESS, the MSS of "my_socket" is 1000 bytes. */
```

### <a name="see-also"></a>Consulte também

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_peer_info_get"></a>nx_tcp_socket_peer_info_get
Recuperar informações sobre a tomada de TCP do par

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_peer_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *peer_ip_address,
    ULONG *peer_port);
```
### <a name="description"></a>Descrição

Este serviço recupera o endereço IP e informações de porta para a tomada TCP conectada sobre a rede IPv4. O serviço equivalente que também suporta a rede IPv6 é ***nxd_tcp_socket_peer_info_get.***

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para tomada TCP previamente criada.
- **peer_ip_address** Ponteiro para destino para endereço IP peer, em ordem byte anfitrião.
- **peer_port** Ponteiro para destino para número de porta de pares, em ordem byte de anfitrião.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) O Serviço executa com sucesso. O endereço IP peer e o número da porta são devolvidos ao chamador.
- **NX_NOT_CONNECTED** (0x38) A tomada não se encontra ligada.
- **NX_PTR_ERROR** (0x07) Ponteiros inválidos.
- **NX_NOT_ENABLED** (0x14) TCP não está ativado.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Obtain peer IP address and port on the specified TCP socket. */
status = nx_tcp_socket_peer_info_get(&my_socket, &peer_ip_address,
                                     &peer_port);

/* If status = NX_SUCCESS, the data was successfully obtained. */
```
### <a name="see-also"></a>Consulte também

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_queue_depth_notify_set"></a>nx_tcp_socket_queue_depth_notify_set
Definir a função de notificação de fila de transmissão TCP

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_queue_depth_notify_set(
              NX_TCP_SOCKET *socket_ptr,
              VOID(*tcp_socket_queue_depth_notify)(NX_TCP_SOCKET *));
```
### <a name="description"></a>Descrição

Este serviço define a função de notificação de profundidade de fila de transmissão especificada pela aplicação, que é chamada sempre que a tomada especificada determina que libertou pacotes da fila de transmissão de modo a que a profundidade da fila já não exceda o seu limite. Se uma aplicação for bloqueada no transmissor devido à profundidade da fila, a função de retorno serve como uma notificação à aplicação de que pode voltar a transmitir. Este serviço só está disponível se a biblioteca NetX Duo for construída com a opção ***NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY*** definida.

### <a name="parameters"></a>Parâmetros 

- **socket_ptr** Ponteiro para a estrutura da tomada 
- **tcp_socket_queue_depth_notify** A função de notificação a instalar

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) instalou com sucesso a função de notificação
- **NX_NOT_SUPPORTED** (0x4B) A funcionalidade de notificação de profundidade da fila da tomada TCP não está incorporada na biblioteca NetX Duo
- **NX_PTR_ERROR** (0x07) Ponteiro inválido para o bloco de controlo da tomada ou para a função de notificação
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) funcionalidade TCP não está ativada.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
VOID tcp_socket_queue_depth_notify(NX_TCP_SOCKET *socket_ptr)
{
   /* Notify the application to resume sending. */

}
/* Install the TCP transmit queue notify function .*/
status = nxd_tcp_socket_queue_depth_notify_set(&tcp_socket,
                                  tcp_socket_queue_depth_notify);

/* If status == NX_SUCCESS, the callback function is successfully
   installed. */
```

### <a name="see-also"></a>Consulte também

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_receive"></a>nx_tcp_socket_receive
Receber dados da tomada TCP

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_receive(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Descrição

Este serviço recebe dados de TCP da tomada especificada. Se não forem dados na tomada especificada, o chamador suspende com base na opção de espera fornecida.

> [!CAUTION]  
> *Se NX_SUCCESS for devolvido, o pedido é responsável pela libertação do pacote recebido quando já não for necessário*.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada TCP previamente criada.
- **packet_ptr** Ponteiro para ponteiro de pacoteS TCP.
- **wait_option** Define como o serviço se comporta se os dados estão atualmente em fila nesta tomada. As opções de espera são definidas da seguinte forma:
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **valor de tempo limite em carrapatos** (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Os dados de tomadas bem sucedidos recebem.
- **NX_NOT_BOUND** (0x24) A tomada ainda não está ligada.
- **NX_NO_PACKET** (0x01) Nenhum dado recebido.
- **NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.
- **NX_NOT_CONNECTED** (0x38) A tomada já não está ligada.
- **NX_PTR_ERROR** (0x07) Tomada inválida ou ponteiro do pacote de devolução.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Receive a packet from the previously created and connected TCP
   client socket. If no packet is available, wait for 200 timer
   ticks before giving up. */
status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);

/* If status is NX_SUCCESS, the received packet is pointed to by
   "packet_ptr". */
```
### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_receive_notify"></a>nx_tcp_socket_receive_notify
Notificar a aplicação dos pacotes recebidos

### <a name="prototype"></a>Prototype   

```c
UINT nx_tcp_socket_receive_notify(
    NX_TCP_SOCKET *socket_ptr, 
    VOID (*tcp_receive_notify)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Descrição 

Este serviço configura o ponteiro de função de notificação de receção com a função de retorno especificado pela aplicação. Esta função de retorno é então chamada sempre que um ou mais pacotes são recebidos na tomada. Se for fornecido um ponteiro NX_NULL, a função de notificação é desativada.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a tomada TCP.
- **tcp_receive_notify** O ponteiro da função de retorno da aplicação que é chamado quando um ou mais pacotes são recebidos na tomada.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) A tomada de sucesso recebe a notificação.
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) funcionalidade TCP não está ativada.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Setup a receive packet callback function for the "client_socket"
   socket. */
status = nx_tcp_socket_receive_notify(&client_socket,
                                      my_receive_notify);

/* If status is NX_SUCCESS, NetX Duo will call the function named
   "my_receive_notify" whenever one or more packets are received for
   "client_socket". */
```
### <a name="see-also"></a>Consulte também

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_send"></a>nx_tcp_socket_send
Enviar dados através de uma tomada TCP

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_send(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Descrição

Este serviço envia dados de TCP através de uma tomada TCP previamente ligada. Se o último tamanho da janela anunciado pelo recetor for inferior a este pedido, o serviço suspende opcionalmente com base na opção de espera especificada. Este serviço garante que nenhum dado de pacote maior do que o MSS é enviado para a camada IP. 

> [!WARNING]  
> *A menos que um erro seja devolvido, o pedido não deve libertar o pacote após esta chamada. Ao fazê-lo, o condutor da rede também tentará libertar o pacote após a transmissão*.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada TCP previamente ligada.
- **packet_ptr** Ponteiro do pacote de dados da TCP.
- **wait_option** Define como o serviço se comporta se o pedido for maior do que o tamanho da janela do recetor. As opções de espera são definidas da seguinte forma:
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **valor de tempo limite em carrapatos** (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Envio de tomadas bem sucedidas.
- **NX_NOT_BOUND** (0x24) Tomada não estava ligada a nenhuma porta.
- **NX_NO_INTERFACE_ADDRESS** (0x50) Não foi encontrada nenhuma interface de saída adequada.
- **NX_NOT_CONNECTED** (0x38) A tomada já não está ligada.
- **NX_WINDOW_OVERFLOW** (0x39) O pedido é maior do que o tamanho da janela anunciado pelo recetor em bytes.
- **NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.
- **NX_INVALID_PACKET** (0x12) Pacote não é atribuído.
- **NX_TX_QUEUE_DEPTH** (0x49) Foi atingida a profundidade máxima da fila de transmissão.
- **NX_OVERFLOW** (0x03) O ponteiro do apêndice do pacote é inválido.
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.
- **NX_UNDERFLOW** (0x02) O ponteiro de preparação do pacote é inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Send a packet out on the previously created and connected TCP
   socket. If the receive window on the other side of the connection
   is less than the packet size, wait 200 timer ticks before giving
   up. */
status = nx_tcp_socket_send(&client_socket, packet_ptr, 200);

/* If status is NX_SUCCESS, the packet has been sent! */
```
### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_state_wait"></a>nx_tcp_socket_state_wait
Aguarde que a tomada TCP entre em estado específico

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_state_wait(
    NX_TCP_SOCKET *socket_ptr,
    UINT desired_state,
    ULONG wait_option);
```
### <a name="description"></a>Descrição

Este serviço aguarda que a tomada entre no estado pretendido. Se a tomada não estiver no estado pretendido, o serviço suspende de acordo com a opção de espera fornecida.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada TCP previamente ligada.
- **desired_state** Estado de TCP desejado. Os estados de tomada TCP válidos são definidos da seguinte forma:
    - **NX_TCP_CLOSED** (0x01)
    - **NX_TCP_LISTEN_STATE** (0x02)
    - **NX_TCP_SYN_SENT** (0x03)
    - **NX_TCP_SYN_RECEIVED** (0x04)
    - **NX_TCP_ESTABLISHED** (0x05)
    - **NX_TCP_CLOSE_WAIT** (0x06)
    - **NX_TCP_FIN_WAIT_1** (0x07)
    - **NX_TCP_FIN_WAIT_2** (0x08)
    - **NX_TCP_CLOSING** (0x09)
    - **NX_TCP_TIMED_WAIT** (0x0A)
    - **NX_TCP_LAST_ACK** (0x0B)
- **wait_option** Define como o serviço se comporta se o estado solicitado não estiver presente. As opções de espera são definidas da seguinte forma:
    - **NX_NO_WAIT** (0x00000000)
    - **valor de tempo limite em carrapatos** (0x00000001 através de 0xFFFFFFFF)

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Espera de estado bem-sucedido.
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_NOT_SUCCESSFUL** Estado (0x43) não está presente dentro do tempo de espera especificado.
- **NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.
- **NX_OPTION_ERROR** (0x0A) O estado de tomada pretendido é inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Wait 300 timer ticks for the previously created socket to enter
   the established state in the TCP state machine. */
status = nx_tcp_socket_state_wait(&client_socket,
                                  NX_TCP_ESTABLISHED, 300);

/* If status is NX_SUCCESS, the socket is now in the established
   state! */
```
### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_timed_wait_callback"></a>nx_tcp_socket_timed_wait_callback
Instale o callback para o estado de espera cronometrado

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_timed_wait_callback(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_timed_wait_callback)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Descrição

Este serviço regista uma função de retorno que é invocada quando a tomada TCP está em estado de espera cronometrado. Para utilizar este serviço, a biblioteca NetX Duo deve ser construída com a opção ***NX_ENABLE_EXTENDED_NOTIFY*** definida.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada de cliente ou servidor previamente ligada.
- **tcp_timed_wait_callback** A função de retorno de espera cronometrado

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) regista com sucesso a tomada de função de retorno
- **NX_NOT_SUPPORTED** (0x4B) a biblioteca NetX Duo é construída sem a funcionalidade de notificação estendida ativada.
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) funcionalidade TCP não está ativada.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Install the timed wait callback function */
nx_tcp_socket_timed_wait_callback(&client_socket, callback);
```

### <a name="see-also"></a>Consulte também

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_transmit_configure"></a>nx_tcp_socket_transmit_configure
Configurar os parâmetros de transmissão da tomada

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_transmit_configure(
    NX_TCP_SOCKET *socket_ptr,
    ULONG max_queue_depth,
    ULONG timeout,
    ULONG max_retries,
    ULONG timeout_shift);
```
### <a name="description"></a>Descrição

Este serviço configura vários parâmetros de transmissão da tomada TCP especificada.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a tomada TCP.
- **max_queue_depth** Número máximo de pacotes autorizados a ser em fila para transmissão.
- **tempo limite** O número de marcadores ThreadX marca um ACK é esperado antes do pacote ser enviado novamente.
- **max_retries** Número máximo de retró assim que é permitido.
- **timeout_shift** Valor para deslocar o tempo limite para cada relemque subsequente. Um valor de 0, resulta no mesmo intervalo entre as sucessivas retrações. Um valor de 1, duplica o tempo limite entre as retrações.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Configuração de tomada de transmissão bem sucedida.
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_OPTION_ERROR** (0x0a) Opção de profundidade de fila inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) funcionalidade TCP não está ativada.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Configure the "client_socket" for a maximum transmit queue depth of
   12, 100 tick timeouts, a maximum of 20 retries, and a timeout double
   on each successive retry. */
status = nx_tcp_socket_transmit_configure(&client_socket,12,100,20,1);

/* If status is NX_SUCCESS, the socket’s transmit retry has been
   configured. */
```
### <a name="see-also"></a>Consulte também

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_window_update_notify_set"></a>nx_tcp_socket_window_update_notify_set
Notifique a aplicação de atualizações do tamanho da janela

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_window_update_notify_set(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_window_update_notify)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Descrição

Este serviço instala uma rotina de chamada de atualização da janela da tomada. Esta rotina é chamada automaticamente sempre que a tomada especificada recebe um pacote indicando um aumento no tamanho da janela do hospedeiro remoto.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para tomada TCP previamente criada.
- **tcp_window_update_notify** Rotina de chamada a ser chamada quando o tamanho da janela muda. Um valor de NULO desativa a atualização da alteração da janela.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) A rotina de chamada é instalada na tomada.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_PTR_ERROR** (0x07) Ponteiros inválidos.
- **NX_NOT_ENABLED** (0x14) funcionalidade TCP não está ativada.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Set the function pointer to the windows update callback after creating the
   socket. */
status = nx_tcp_socket_window_update_notify_set(&data_socket,
                                                my_windows_update_callback);

/* Define the window callback function in the host application. */
void my_windows_update_callback(&data_socket)
{

/* Process update on increase TCP transmit socket window size. */
   return;
}
```
### <a name="see-also"></a>Consulte também

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure

## <a name="nx_udp_enable"></a>nx_udp_enable
Ativar o componente UDP do NetX Duo

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descrição

Este serviço permite o componente do Protocolo de Datagram do Utilizador (UDP) da NetX Duo. Após ativação, os datagramas da UDP podem ser enviados e recebidos pelo pedido.

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro para instância IP previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) UDP bem sucedido.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_ALREADY_ENABLED** (0x15) Este componente já foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Enable UDP on the previously created IP instance. */
status = nx_udp_enable(&ip_0);

/* If status is NX_SUCCESS, UDP is now enabled on the specified IP
   instance. */
```
### <a name="see-also"></a>Consulte também

- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_free_port_find"></a>nx_udp_free_port_find
Encontre a próxima porta UDP disponível

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_free_port_find(
    NX_IP *ip_ptr, 
    UINT port,
    UINT *free_port_ptr);
```
### <a name="description"></a>Descrição

Este serviço procura uma porta UDP gratuita (não ligada) a partir do número de porta fornecido pela aplicação. A lógica de pesquisa irá envolver-se se a pesquisa atingir o valor máximo da porta de 0xFFFF. Se a pesquisa for bem sucedida, a porta livre é devolvida na variável apontada por free_port_ptr.

> [!WARNING]  
> *Este serviço pode ser chamado de outro fio e pode ter a mesma porta devolvida. Para evitar esta condição de regata, a aplicação pode pretender colocar este serviço e a tomada efetiva ligada sob a proteção de um mutex*.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **porto** Número da porta para iniciar a pesquisa (1 a 0xFFFF).
- **free_port_ptr** Ponteiro para a variável de retorno de porto livre de destino.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Achado de porta livre com sucesso.
- **NX_NO_FREE_PORTS** (0x45) Não foram encontradas portas livres.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.
- **NX_INVALID_PORT** (0x46) O número de porta especificado é inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Locate a free UDP port, starting at port 12, on a previously
   created IP instance. */
status = nx_udp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS pointer, "free_port" identifies the next
   free UDP port on the IP instance. */
```
### <a name="see-also"></a>Consulte também

- nx_udp_enable
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_info_get"></a>nx_udp_info_get
Recuperar informações sobre atividades da UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_info_get(
    NX_IP *ip_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_invalid_packets,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```
### <a name="description"></a>Descrição

Este serviço obtém informações sobre as atividades da UDP para a instância IP especificada.

> [!IMPORTANT]  
> *Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao chamador*.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **udp_packets_sent** Ponteiro para o destino para o número total de pacotes UDP enviados.
- **udp_bytes_sent** Ponteiro para destino para o número total de bytes UDP enviados.
- **udp_packets_received** Ponteiro para o destino do número total de pacotes UDP recebidos.
- **udp_bytes_received** Ponteiro para o destino do número total de bytes UDP recebidos.
- **udp_invalid_packets** Ponteiro para o destino do número total de pacotes UDP inválidos.
- **udp_receive_packets_dropped** O ponteiro para o destino do número total de pacotes de receção UDP caiu.
- **udp_checksum_errors** Ponteiro para o destino do número total de pacotes UDP com erros de checkum.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Recuperação de informações bem sucedidas da UDP.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios e temporizadores

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Retrieve UDP information from previously created IP Instance
   ip_0. */
status = nx_udp_info_get(&ip_0, &udp_packets_sent,
                         &udp_bytes_sent,
                         &udp_packets_received,
                         &udp_bytes_received,
                         &udp_invalid_packets,
                         &udp_receive_packets_dropped,
                         &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP information was retrieved. */
```
### <a name="see-also"></a>Consulte também

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_packet_info_extract"></a>nx_udp_packet_info_extract
Extrair parâmetros de rede do pacote UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```
### <a name="description"></a>Descrição

Este serviço extrai parâmetros de rede, tais como endereço IPv4, número de porta de pares, tipo de protocolo (este serviço devolve sempre o tipo UDP) de um pacote recebido numa interface de entrada. Para obter informações sobre um pacote proveniente da rede IPv4 ou IPv6, a aplicação utilizará o ***serviço nxd_udp_packet_info_extract.***

### <a name="parameters"></a>Parâmetros

- **packet_ptr** Ponteiro para pacote.
- **ip_address** Ponteiro para o endereço IP remetente.
- **protocolo** Ponteiro para o protocolo (UDP).
- **porto** Ponteiro para o número da porta do remetente.
- **interface_index** Ponteiro para receber índice de interface.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) dados de interface de pacote extraídos com sucesso.
- **NX_INVALID_PACKET** (0x12) O pacote não contém quadro IPv4.
- **NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Extract network data from UDP packet interface.*/
status = nx_udp_packet_info_extract(packet_ptr, &ip_address,
                                     &protocol, &port,
                                     &interface_index);

/* If status is NX_SUCCESS packet data was successfully
   retrieved. */
```
### <a name="see-also"></a>Consulte também

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_bind"></a>nx_udp_socket_bind
Ligue a tomada UDP à porta UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_socket_bind(
    NX_UDP_SOCKET *socket_ptr, 
    UINT port,
    ULONG wait_option);
```
### <a name="description"></a>Descrição

Este serviço liga a tomada UDP previamente criada à porta UDP especificada. As tomadas UDP válidas variam de 0 a 0xFFFF. Se o número de porta solicitado estiver ligado a outra tomada, este serviço aguarda por um período de tempo especificado para que a tomada se desvincula do número da porta.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada UDP previamente criada.
- **porto** Número da porta para ligar a** (1 a 0xFFFF). Se o número da porta for NX_ANY_PORT** (0x0000), a instância IP procurará a próxima porta livre e usará-a para a encadernação.
- **wait_option** Define como o serviço se comporta se a porta já está ligada a outra tomada. As opções de espera são definidas da seguinte forma:
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **valor de tempo limite em carrapatos** (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Ligação de tomada bem sucedida.
- **NX_ALREADY_BOUND** (0x22) Esta tomada já está ligada a outra porta.
- **NX_PORT_UNAVAILABLE** (0x23) O porto já está ligado a uma tomada diferente.
- **NX_NO_FREE_PORTS** (0x45) Não há porta livre.
- **NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.
- **NX_INVALID_PORT** (0x46) Porta inválida especificada.
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Bind the previously created UDP socket to port 12 on the
   previously created IP instance. If the port is already bound,
   wait for 300 timer ticks before giving up. */
status = nx_udp_socket_bind(&udp_socket, 12, 300);

/* If status is NX_SUCCESS, the UDP socket is now bound to
   port 12.*/
```
### <a name="see-also"></a>Consulte também

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_bytes_available"></a>nx_udp_socket_bytes_available
Recupera o número de bytes disponíveis para recuperação

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_socket_bytes_available(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```
### <a name="description"></a>Descrição

Este serviço recupera o número de bytes disponíveis para receção na tomada UDP especificada.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para tomada UDP previamente criada.
- **bytes_available** Ponteiro para destino para bytes disponíveis.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Bytes de sucesso disponível.
- **NX_NOT_SUCCESSFUL** (0x43) Tomada não ligada a uma porta.
- **NX_PTR_ERROR** (0x07) Ponteiros inválidos.
- **NX_NOT_ENABLED** funcionalidade UDP (0x14) não está ativada.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Get the bytes available for retrieval from the UDP socket. */
status = nx_udp_socket_bytes_available(&my_socket,
                                       &bytes_available);

/* If status == NX_SUCCESS, the number of bytes was successfully
   retrieved.*/
```
### <a name="see-also"></a>Consulte também

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_checksum_disable"></a>nx_udp_socket_checksum_disable
Desativar a parte de verificação da tomada UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_socket_checksum_disable(NX_UDP_SOCKET *socket_ptr);
```
### <a name="description"></a>Descrição

Este serviço desativa a lógica de checkum para o envio e receção de pacotes na tomada UDP especificada. Quando a lógica de checkum é desativada, um valor de zero é carregado no campo de verificação do cabeçalho UDP para todos os pacotes enviados através desta tomada. Um valor de dados de valor zero no cabeçalho UDP indica ao recetor que a parte de verificação não é calculada para este pacote.

Note também que tal não tem qualquer efeito se **NX_DISABLE_UDP_RX_CHECKSUM** e **NX_DISABLE_UDP_TX_CHECKSUM** forem definidos ao receber e enviar pacotes UDP respectivamente,

Note que este serviço não tem qualquer efeito nos pacotes na rede IPv6, uma vez que a UDP checksum é obrigatória para o IPv6.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada UDP previamente criada.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Desativação de verificação de tomadas bem sucedidas.
- **NX_NOT_BOUND** (0x24) A tomada não está ligada.
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizador

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Disable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_disable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will not have a checksum
   calculated. */
```
### <a name="see-also"></a>Consulte também

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_checksum_enable"></a>nx_udp_socket_checksum_enable
Ativar a parte de verificação da tomada UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_socket_checksum_enable(NX_UDP_SOCKET *socket_ptr);
```
### <a name="description"></a>Descrição

Este serviço permite a lógica de checkum para o envio e receção de pacotes na tomada UDP especificada. A função de verificação abrange toda a área de dados da UDP, bem como um cabeçalho pseudo-IP.

Note também que isso não tem qualquer efeito se **NX_DISABLE_UDP_RX_CHECKSUM** e **NX_DISABLE_UDP_TX_CHECKSUM** forem definidos ao receber e enviar pacotes UDP respectivamente.

Note que este serviço não tem qualquer efeito sobre os pacotes na rede IPv6. A udp checksum é obrigatória no IPv6.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada UDP previamente criada.

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Ativar a tomada de verificação com sucesso.
- **NX_NOT_BOUND** (0x24) A tomada não está ligada.
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizador

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Enable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_enable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will have a checksum
   calculated. */
```
### <a name="see-also"></a>Consulte também

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_create"></a>nx_udp_socket_create
Criar tomada UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_socket_create(
    NX_IP *ip_ptr,
    NX_UDP_SOCKET *socket_ptr, 
    CHAR *name,
    ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG queue_maximum);
```
### <a name="description"></a>Descrição

Este serviço cria uma tomada UDP para a instância IP especificada.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **socket_ptr** Ponteiro para o novo bloco de controlo de tomadas UDP.
- **nome** Nome da aplicação para esta tomada UDP.
- **type_of_service** Define o tipo de serviço para a transmissão, os valores legais são os seguintes:
    - **NX_IP_NORMAL** (0x00000000)
    - **NX_IP_MIN_DELAY** (0x00100000)
    - **NX_IP_MAX_DATA** (0x00080000)
    - **NX_IP_MAX_RELIABLE** (0x00040000)
    - **NX_IP_MIN_COST** (0x00020000)
- **fragmento Especifica** se a fragmentação IP é ou não permitida. Se NX_FRAGMENT_OKAY (0x0) for especificado, é permitida a fragmentação ip. Se NX_DONT_FRAGMENT (0x4000) for especificado, a fragmentação ip está desativada.
- **time_to_live** Especifica o valor de 8 bits que define quantos routers este pacote pode passar antes de ser jogado fora. O valor predefinido é especificado por NX_IP_TIME_TO_LIVE.
- **queue_maximum** Define o número máximo de datagramas da UDP que podem ser pré-visualizados para esta tomada. Após o limite de fila ser atingido, para cada novo pacote recebido o pacote UDP mais antigo é lançado.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Tomada UDP bem sucedida criar.
- **NX_OPTION_ERROR** (0x0A) Opção de serviço, fragmento ou tempo-a-vida inválido.
- **NX_PTR_ERROR** (0x07) IP inválido ou ponteiro de tomada.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e Threads

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Create a UDP socket with a maximum receive queue of 30 packets.*/
status = nx_udp_socket_create(&ip_0, &udp_socket, "Sample UDP Socket",
                              NX_IP_NORMAL, NX_FRAGMENT_OKAY, 0x80,
                              30);

/* If status is NX_SUCCESS, the new UDP socket has been created and
   is ready for binding. */
```
### <a name="see-also"></a>Consulte também

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_delete"></a>nx_udp_socket_delete
Eliminar tomada UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_socket_delete(NX_UDP_SOCKET *socket_ptr);
```
### <a name="description"></a>Descrição

Este serviço elimina uma tomada UDP previamente criada. Se a tomada estava ligada a uma porta, a tomada deve ser desaderada primeiro.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada UDP previamente criada.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Apagar a tomada com sucesso.
- **NX_STILL_BOUND** (0x42) A tomada ainda está ligada.
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Delete a previously created UDP socket. */
status = nx_udp_socket_delete(&udp_socket);

/* If status is NX_SUCCESS, the previously created UDP socket has
   been deleted. */
```
### <a name="see-also"></a>Consulte também

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_info_get"></a>nx_udp_socket_info_get
Recuperar informações sobre as atividades da tomada da UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_socket_info_get(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_packets_queued,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```
### <a name="description"></a>Descrição

Este serviço obtém informações sobre as atividades da tomada UDP para a instância de tomada UDP especificada.

> [!IMPORTANT]  
> *Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao chamador*.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada UDP previamente criada.
- **udp_packets_sent** Ponteiro para o destino para o número total de pacotes UDP enviados na tomada.
- **udp_bytes_sent** Ponteiro para destino para o número total de bytes UDP enviados na tomada.
- **udp_packets_received** Ponteiro para o destino do número total de pacotes UDP recebidos na tomada.
- **udp_bytes_received** Ponteiro para o destino do número total de bytes UDP recebidos na tomada.
- **udp_packets_queued** Ponteiro para o destino do número total de pacotes de UDP em fila na tomada.
- **udp_receive_packets_dropped** O ponteiro para o destino do número total de pacotes de receção UDP caiu para tomada devido ao tamanho da fila ser excedido.
- **udp_checksum_errors** Ponteiro para o destino do número total de pacotes UDP com erros de verificação na tomada.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Recuperação de informações de tomadas UDP bem sucedidas.
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios e temporizadores

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Retrieve UDP socket information from socket 0.*/
status = nx_udp_socket_info_get(&socket_0,
                                &udp_packets_sent,
                                &udp_bytes_sent,
                                &udp_packets_received,
                                &udp_bytes_received,
                                &udp_queued_packets,
                                &udp_receive_packets_dropped,
                                &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP socket information was retrieved.*/
```
### <a name="see-also"></a>Consulte também

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_port_get"></a>nx_udp_socket_port_get
Recolha o número da porta vinculado à tomada UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_socket_port_get(
    NX_UDP_SOCKET *socket_ptr,
    UINT *port_ptr);
```
### <a name="description"></a>Descrição

Este serviço recupera o número de porta associado à tomada, o que é útil para encontrar a porta atribuída pela NetX Duo em situações em que o NX_ANY_PORT foi especificado no momento em que a tomada foi ligada.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada UDP previamente criada.
- **port_ptr** Ponteiro para o destino para o número da porta de retorno. Os números de porta válidos são (1- 0xFFFF).

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Ligação de tomada bem sucedida.
- **NX_NOT_BOUND** (0x24) Esta tomada não está ligada a uma porta.
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida ou ponteiro de retorno da porta.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Get the port number of created and bound UDP socket. */
status = nx_udp_socket_port_get(&udp_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
   socket is bound to. */
```
### <a name="see-also"></a>Consulte também

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_receive"></a>nx_udp_socket_receive
Receber datagrama da tomada UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_socket_receive(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Descrição

Este serviço recebe um datagrama de UDP a partir da tomada especificada. Se não houver um datagrama na tomada especificada, o chamador suspende com base na opção de espera fornecida.

> [!CAUTION]  
> *Se NX_SUCCESS for devolvido, o pedido é responsável pela libertação do pacote recebido quando já não for necessário*.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada UDP previamente criada.
- **packet_ptr** Ponteiro para o ponteiro do pacote de dados da UDP.
- **wait_option** Define como o serviço se comporta se um datagram não estiver atualmente em fila nesta tomada. As opções de espera são definidas da seguinte forma:
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **valor de tempo limite em carrapatos** (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Receber tomadas bem sucedidas.
- **NX_NOT_BOUND** (0x24) Tomada não estava ligada a nenhuma porta.
- **NX_NO_PACKET** (0x01) Não havia nenhum datagrama da UDP para receber.
- **NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.
- **NX_PTR_ERROR** (0x07) Tomada inválida ou ponteiro de retorno do pacote.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Receive a packet from a previously created and bound UDP socket.
   If no packets are currently available, wait for 500 timer ticks
   before giving up. */
status = nx_udp_socket_receive(&udp_socket, &packet_ptr, 500);

/* If status is NX_SUCCESS, the received UDP packet is pointed to by
   packet_ptr. */
```
### <a name="see-also"></a>Consulte também

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_receive_notify"></a>nx_udp_socket_receive_notify
Notifique a aplicação de cada pacote recebido

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_socket_receive_notify(
    NX_UDP_SOCKET *socket_ptr,
    VOID (*udp_receive_notify)(NX_UDP_SOCKET *socket_ptr));
```
### <a name="description"></a>Descrição 

Este serviço define o ponteiro de função de notificação de receção à função de retorno especificado pela aplicação. Esta função de retorno é então chamada sempre que um pacote é recebido na tomada. Se for fornecido um ponteiro NX_NULL, a função de notificação de receção é desativada.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a tomada UDP.
- **udp_receive_notify** Ponteiro da função de retorno da aplicação que é chamado quando um pacote é recebido na tomada.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) A tomada definida com sucesso recebem a função de notificação.
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Setup a receive packet callback function for the "udp_socket"
   socket. */
status = nx_udp_socket_receive_notify(&udp_socket,
                                      my_receive_notify);

/* If status is NX_SUCCESS, NetX Duo will call the function named
   "my_receive_notify" whenever a packet is received for
   "udp_socket". */
```
### <a name="see-also"></a>Consulte também

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_send"></a>nx_udp_socket_send
Enviar um UDP Datagram

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address, 
    UINT port);
```
### <a name="description"></a>Descrição

Este serviço envia um datagrama de UDP através de uma tomada UDP previamente criada e ligada para redes IPv4. NetX Duo encontra um endereço IP local adequado como endereço de origem baseado no endereço IP de destino. Para especificar uma interface específica e endereço IP de origem, a aplicação deve utilizar o serviço **nxd_udp_socket_source_send.**

Note que este serviço retorna imediatamente independentemente de o datagrama da UDP ter sido enviado com sucesso. O serviço equivalente NetX Duo (IPv4/IPv6) é ***nxd_udp_socket_send***.

A tomada deve estar ligada a um porto local.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada UDP previamente criada
- **packet_ptr** Ponteiro do pacote de datagrama da UDP
- **ip_address** Endereço IPv4 de destino
- **porto** Número de porta de destino válido entre 1 e 0xFFFF), em encomenda byte de anfitrião

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Envio de tomada uDP bem sucedida
- **NX_NOT_BOUND** (0x24) Tomada não ligada a nenhuma porta
- **NX_NO_INTERFACE_ADDRESS** (0x50) Não é possível encontrar uma interface de saída adequada.
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IP do servidor inválido
- **NX_UNDERFLOW** (0x02) Não há espaço suficiente para cabeçalho UDP no pacote
- **NX_OVERFLOW** (0x03) O ponteiro do apêndice do pacote é inválido
- **ponteiro de tomada** inválida NX_PTR_ERROR (0x07)
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço
- **NX_NOT_ENABLED** (0x14) UDP não foi habilitado
- **NX_INVALID_PORT** (0x46) Número de porta não está dentro de um alcance válido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
ULONG server_address;

/* Set the UDP Client IP address. */
server_address = IP_ADDRESS(1,2,3,5);

/* Send a packet to the UDP server at server_address on port 12. */
status = nx_udp_socket_send(&client_socket, packet_ptr,
                            server_address, 12);

/* If status == NX_SUCCESS, the application successfully transmitted
   the packet out the UDP socket to its peer. */
```
### <a name="see-also"></a>Consulte também

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_source_send"></a>nx_udp_socket_source_send
Enviar datagrama através da tomada UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_socket_source_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port,
    UINT address_index);
```
### <a name="description"></a>Descrição

Este serviço envia um datagrama de UDP através de uma tomada UDP previamente criada e ligada através da interface de rede com o endereço IP especificado como endereço de origem. Note que o serviço regressa imediatamente, independentemente de o datagrama da UDP ter sido enviado com sucesso. ***nxd_udp_socket_source_send*** funciona tanto para as redes IPv4 como para o IPv6.

### <a name="parameters"></a>Parâmetros 

- **socket_ptr** Tomada para transmitir o pacote.
- **packet_ptr** Ponteiro para pacote para transmitir.
- **ip_address** Endereço IP destino para enviar pacote.
- **porto** Porto de destino.
- **address_index** Índice do endereço associado à interface para enviar o pacote.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Packet enviado com sucesso.
- **NX_NOT_BOUND** (0x24) Tomada não ligada a uma porta.
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IP inválido.
- **NX_NOT_ENABLED** processamento de UDP (0x14) não está ativado.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido.
- **NX_OVERFLOW** (0x03) Ponteiro de pacote inválido.
- **NX_UNDERFLOW** (0x02) Ponteiro de pré-final de pacote inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_INVALID_INTERFACE** (0x4C) Índice de endereços inválidos.
- **NX_INVALID_PORT** (0x46) O número do porto excede o número máximo de porta.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
#define ADDRESS_INDEX 1

/* Send packet out on port 80 to the specified destination IP on the
   interface at index 1 in the IP task interface list. */
status = nx_udp_socket_source_send(socket_ptr, packet_ptr,
                                   destination_ip, 80,
                                   ADDRESS_INDEX);

/* If status is NX_SUCCESS packet was successfully transmitted. */
```

### <a name="see-also"></a>Consulte também

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_unbind"></a>nx_udp_socket_unbind
Tomada UDP desaderada da porta UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_socket_unbind(NX_UDP_SOCKET *socket_ptr);
```
### <a name="description"></a>Descrição

Este serviço liberta a encadernação entre a tomada UDP e uma porta UDP. Quaisquer pacotes recebidos armazenados na fila de receção são libertados como parte da operação un encaderna.

Se houver outros fios à espera de ligar outra tomada à porta desvinculada, o primeiro fio suspenso fica então ligado à porta recém-desvinculada.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada UDP previamente criada.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Tomada desaderada com sucesso.
- **NX_NOT_BOUND** (0x24) Tomada não estava ligada a nenhuma porta.
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

Sim

### <a name="example"></a>Exemplo

```c
/* Unbind the previously bound UDP socket. */
status = nx_udp_socket_unbind(&udp_socket);

/* If status is NX_SUCCESS, the previously bound socket is now
   unbound. */
```
### <a name="see-also"></a>Consulte também

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_source_extract"></a>nx_udp_source_extract
Extrair IP e enviar porta a partir do datagrama da UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_source_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address, 
    UINT *port);
```
### <a name="description"></a>Descrição

Este serviço extrai o número de IP e porta do remetente dos cabeçalhos IP e UDP do programa de dados da UDP fornecido. Note que o ***serviço nxd_udp_source_extract*** funciona com pacotes da rede IPv4 ou IPv6.

### <a name="parameters"></a>Parâmetros

- **packet_ptr** Ponteiro do pacote de datagrama da UDP.
- **ip_address** Ponteiro válido para a variável de endereço IP de retorno.
- **porto** Ponteiro válido para a variável porta de retorno.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Extração IP/porta de origem bem sucedida.
- **NX_INVALID_PACKET** (0x12) O pacote fornecido é inválido.
- **NX_PTR_ERROR** (0x07) Pacote inválido ou IP ou destino portuário.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores, ISR

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Extract the IP and port information from the sender of the UPD packet. */
status = nx_udp_source_extract(packet_ptr, &sender_ip_address, &sender_port);

/* If status is NX_SUCCESS, the sender IP and port information has been stored
   in sender_ip_address and sender_port respectively.*/
```
### <a name="see-also"></a>Consulte também

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nxd_icmp_enable"></a>nxd_icmp_enable
Ativar serviços ICMPv4 e ICMPv6

### <a name="prototype"></a>Prototype  

```c
UINT nxd_icmp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descrição

Este serviço permite tanto os serviços ICMPv4 como ICMPv6 e só pode ser chamado após a criação da instância IP. O serviço pode ser ativado antes ou depois do IPv6 estar ativado (ver *nxd_ipv6_enable).* Os serviços ICMPv4 incluem Pedido de Eco/Resposta. Os serviços ICMPv6 incluem Pedido de Eco/Resposta, Descoberta de Vizinhos, Deteção de Endereços Duplicados, Descoberta do Router e configuração automática de endereços apátridas. O equivalente IPv4 na NetX é *nx_icmp_enable*.

> [!NOTE] 
> *Se o endereço IPv6 estiver configurado manualmente antes de ativar o ICMPv6, o IPv6 configurado manualmente não está sujeito ao processo de deteção de endereços duplicado*.

*nx_icmp_enable* inicia serviços ICMP apenas para operações IPv4. As aplicações que utilizem os serviços ICMPv6 devem utilizar *nxd_icmp_enable* em vez de *nx_icmp_enable*.

Para utilizar a solicitação do router IPv6 e a configuração de endereço automático apátrida IPv6, o ICMPv6 deve ser ativado.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) serviços ICMP estão habilitados com sucesso
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Enable ICMP on the IP instance. */
status = nxd_icmp_enable(&ip_0);

/* A status return of NX_SUCCESS indicates that the IP instance is
   enabled for ICMP services. */
```
### <a name="see-also"></a>Consulte também

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nxd_icmp_ping"></a>nxd_icmp_ping
Executar pedidos de eco ICMPv4 ou ICMPv6

### <a name="prototype"></a>Prototype  

```c
UINT nxd_icmp_ping(
    NX_IP *ip_ptr, 
    NXD_ADDRESS *ip_address,
    CHAR *data_ptr, 
    ULONG data_size,
    NX_PACKET **response_ptr, 
    ULONG wait_option);
```
### <a name="description"></a>Descrição

Este serviço envia um pacote ICMP Echo Request através de uma interface física apropriada e aguarda uma Resposta Echo do anfitrião do destino. A NetX Duo determina a interface adequada, com base no endereço de destino, para enviar a mensagem de ping . As aplicações devem utilizar o ***serviço nxd_icmp_source_ping*** para especificar a interface física e o endereço IP de origem precisa para utilizar para a transmissão de pacotes.

A instância IP deve ter sido criada e os serviços ICMPv4/ICMPv6 devem ser ativados (ver ***nxd_icmp_enable***).

> [!WARNING]  
> Se NX_SUCCESS for devolvido, o pedido é responsável pela libertação do pacote recebido depois de já não ser necessário.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Indicação para a instância IP
- **ip_address** Endereço IP destino para ping, em encomenda byte anfitrião
- **data_ptr** Ponteiro para a área de dados do pacote de ping
- **data_size** Número de bytes de dados de ping
- **response_ptr** Ponteiro para ponteiro do pacote de resposta
- **wait_option** Hora de esperar por uma resposta. As opções de espera são definidas da seguinte forma:
    - **NX_NO_WAIT** (0x00000000)
    - **valor de tempo limite em carrapatos** (0x00000001 através 
    - **NX_WAIT_FOREVER** 0xFFFFFFFE)

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Bem-sucedido enviado e recebido ping
- **NX_NOT_SUPPORTED** (0x4B) IPv6 não está ativado
- **NX_OVERFLOW** (0x03) Os dados do Ping excedem a carga útil do pacote
- **NX_NO_RESPONSE** (0x29) O anfitrião do destino não respondeu
- **NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por tx_thread_wait_abort
- **NX_NO_INTERFACE_ADDRESS** (0x50) Não é possível encontrar uma interface de saída adequada.
- **NX_PTR_ERROR** (0x07) IP inválido ou ponteiro de resposta
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço
- **NX_NOT_ENABLED** (0x14) ip ou componente ICMP não está ativado
- **NX_IP_ADDRESS_ERROR** (0x21) O endereço IP de entrada é inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* The following two examples illustrate how to use this API to send
   ping packets to IPv6 or IPv4 destinations. */

/* The first example: Send a ping packet to an IPv6 host
   2001:1234:5678::1 */
   
/* Declare variable address to hold the destination address. */
NXD_ADDRESS ip_address;

char *buffer = “abcd”;
UINT prefix_length = 10;

/* Set the IPv6 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]    = 0x20011234;
ip_address.nxd_ip_address.v6[1]    = 0x56780000;
ip_address.nxd_ip_address.v6[2]    = 0;
ip_address.nxd_ip_address.v6[3]    = 1;

status = nxd_icmp_ping(&ip_0, &ip_address, buffer,
                       strlen(buffer),&response_ptr,
                       NX_WAIT_FOREVER);

/* A return value of NX_SUCCESS indicates a ping reply has been
   received from IP address 2001:1234:5678::1 and the response
   packet is contained in the packet pointed to by response_ptr.It
   should have the same “abcd” four bytes of data. */

/* The second example: Send a ping packet to an IPv4 host 1.2.3.4 */

/* Program the IPv4 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4[0]    = 0x01020304;

status = nxd_icmp_ping(&ip_0, &ip_address, buffer,
                       strlen(buffer),&response_ptr, 10);

/* A return value of NX_SUCCESS indicates a ping reply was received
   from IP address 1.2.3.4 and the response packet is contained in
   the packet pointed to by response_ptr. It should have the same
   “abcd” four bytes of data. */
```
### <a name="see-also"></a>Consulte também

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nxd_icmp_source_ping"></a>nxd_icmp_source_ping
Executar pedidos de eco ICMPv4 ou ICMPv6

### <a name="prototype"></a>Prototype  

```c
UINT nxd_icmp_source_ping(
    NX_IP *ip_ptr, 
    NXD_ADDRESS *ip_address,
    UINT address_index,
    CHAR *data_ptr, 
    ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Descrição

Este serviço envia um pacote ICMP Echo Request utilizando o índice especificado de um endereço IPv4 ou IPv6, e através da interface de rede o endereço de origem está associado, e aguarda uma Resposta de Eco do anfitrião do destino. Este serviço funciona com endereços IPv4 e IPv6. O parâmetro *address_index* indica o endereço IPv4 ou IPv6 de origem a utilizar. Para o endereço IPv4, o *address_index* é o mesmo índice da interface de rede anexa. Para o IPv6, o *address_index* indica a entrada na tabela de endereços IPv6.

A instância IP deve ter sido criada e os serviços ICMPv4 e ICMPv6 devem ser ativados (ver *nxd_icmp_enable*).

> [!CAUTION] 
> *Se NX_SUCCESS for devolvido, o pedido é responsável pela libertação do pacote recebido depois de já não ser necessário*.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Indicação para a instância IP
- **ip_address** Endereço IP destino para ping, em encomenda byte anfitrião
- **address_index** Indica o endereço IP para usar como endereço de origem
- **data_ptr** Ponteiro para a área de dados do pacote de ping
- **data_size** Número de bytes de dados de ping
- **response_ptr** Ponteiro para ponteiro do pacote de resposta
- **wait_option** Hora de esperar por uma resposta. As opções de espera são definidas da seguinte forma:
    - **NX_NO_WAIT** (0x00000000)
    - **valor de tempo limite em carrapatos** (0x00000001 através de 0xFFFFFFFE
    - **NX_WAIT_FOREVER** 0xFFFFFFFF)

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Bem-sucedido enviado e recebido ping
- **NX_NOT_SUPPORTED** (0x4B) IPv6 não está ativado
- **NX_OVERFLOW** (0x03) Os dados do Ping excedem a carga útil do pacote
- **NX_NO_RESPONSE** (0x29) O anfitrião do destino não respondeu
- **NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por tx_thread_wait_abort
- **NX_NO_INTERFACE_ADDRESS** (0x50) Não é possível encontrar uma interface de saída adequada
- **NX_PTR_ERROR** (0x07) IP inválido ou ponteiro de resposta
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço
- **NX_NOT_ENABLED** (0x14) ip ou componente ICMP não está ativado
- **NX_IP_ADDRESS_ERROR** (0x21) O endereço IP de entrada é inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* The following two examples illustrate how to use this API to send ping
   packets to IPv6 or IPv4 destinations. */

/* The first example: Send a ping packet to an IPv6 host
   FE80::411:7B23:40dc:f181 */

/* Declare variable address to hold the destination address. */

#define PRIMARY_INTERFACE 0
#define GLOBAL_IPv6_ADDRESS 1

NXD_ADDRESS ip_address;
char *buffer = “abcd”;
UINT prefix_length = 10;

/* Set the IPv6 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]    = 0xFE800000;
ip_address.nxd_ip_address.v6[1]    = 0x00000000;
ip_address.nxd_ip_address.v6[2]    = 0x04117B23;
ip_address.nxd_ip_address.v6[3]    = 0x40DCF181;

status = nxd_icmp_source_ping(&ip_0, &ip_address,
                              GLOBAL_IPv6_ADDRESS,
                              buffer,
                              strlen(buffer),
                              &response_ptr,
                              NX_WAIT_FOREVER);

/* A return value of NX_SUCCESS indicates a ping reply has been received
   from IP address FE80::411:7B23:40dc:f181 and the response packet is
   contained in the packet pointed to by response_ptr. It should have the
   same “abcd” four bytes of data. */

/* The second example: Send a ping packet to an IPv4 host 1.2.3.4 */

/* Program the IPv4 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4       = 0x01020304;

status = nxd_icmp_source_ping(&ip_0, &ip_address,
                              PRIMARY_INTERFACE,
                              buffer,
                              strlen(buffer),
                              &response_ptr,
                              NX_WAIT_FOREVER);

/* A return value of NX_SUCCESS indicates a ping reply was received from
   IP address 1.2.3.4 and the response packet is contained in the packet
   pointed to by response_ptr. It should have the same “abcd” four bytes
   of data. */
```

### <a name="see-also"></a>Consulte também

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nxd_icmpv6_ra_flag_callback_set"></a>nxd_icmpv6_ra_flag_callback_set
Desabrar a função de retorno de alteração de bandeira ICMPv6 RA

### <a name="prototype"></a>Prototype  

```c
UINT nxd_icmpv6_ra_flag_callback_set(
    NX_IP *ip_ptr, 
    VOID(*ra_callback)(NX_IP*ip_ptr, UINT ra_flag));
```
### <a name="description"></a>Descrição

Este serviço define a função de retorno de chamada de alteração de bandeira do Router ICMPv6. A função de retorno fornecida pelo utilizador é invocada quando o NetX Duo recebe uma mensagem de anúncio do router.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Indicação para a instância IP
- **ra_callback** Função de retorno fornecida pelo utilizador

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Definir bem-sucedido a função de retorno da bandeira da RA
- **NX_NOT_SUPPORTED** (0x4B) IPv6 não está ativado
- **IP** NX_PTR_ERROR (0x07) Inválido
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
VOID icmpv6_ra_flag_callback(NX_IP *ip_ptr, UINT ra_flag)
{
   /* RA flag has changed. The updated value is passed in via the
      ra_flag parameter. */
}

/* Configure the user-defined ICMPv6 RA flag change callback
   function. */
status = nxd_icmpv6_ra_flag_callback_set(&ip_0,
                                         icmpv6_ra_flag_callback);

/* A status return of NX_SUCCESS indicates the callback function has
   been successfully configured. */
```
### <a name="see-also"></a>Consulte também

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping

## <a name="nxd_ip_raw_packet_send"></a>nxd_ip_raw_packet_send
Enviar pacote IP cru

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ip_raw_packet_send(
    NX_IP *ip_ptr, 
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *destination
    ULONG protocol, 
    UINT ttl, 
    ULONG tos);
```
### <a name="description"></a>Descrição

Este serviço envia um pacote IPv4 ou IPv6 em bruto (sem cabeçalhos de protocolo de camada de transporte). Num sistema multihome, se o sistema não conseguir determinar uma interface adequada (por exemplo, se o endereço IP de destino for transmitido IPv4, multicast ou endereço multicast IPv6), o dispositivo principal é selecionado. O serviço ***nxd_ip_raw_packet_source_send** _ pode ser usado para especificar uma interface de saída. O equivalente NetX é _ *_nx_ip_raw_packet_send_.**

A instância IP deve ser previamente criada e o manuseamento de pacotes IP crus deve ser ativado utilizando o serviço ***nx_ip_raw_packet_enable.***

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para a instância IP previamente criada
- **packet_ptr** Ponteiro para pacote para transmitir
- **destination_ip** Ponteiro para endereço de destino
- **protocolo** Protocolo de pacote armazenado no cabeçalho IP
- **ttl** Valor para TTL ou limite de lúpulo
- **tos** Valor para TOS ou classe de tráfego e etiqueta de fluxo

### <a name="return-value"></a>Devolver Valor 

- **NX_SUCCESS** (0x00) Pacote IP cru enviado com sucesso
- **NX_NO_INTERFACE_ADDRESS** (0x50) Não é possível encontrar uma interface de saída adequada
- **NX_NOT_ENABLED** (0x14) Tratamento IP bruto não habilitado
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IPv4 ou IPv6 inválido
- **NX_UNDERFLOW** (0x02) Não há espaço suficiente para cabeçalho IPv4 ou IPv6 no pacote
- **NX_OVERFLOW** (0x03) O ponteiro do apêndice do pacote é inválido
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido ou ponteiro de pacote
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço
- **NX_INVALID_PARAMETERS** (0x4D) Entrada de endereço IPv6 não válida

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
NXD_ADDRESS dest_address;

/* Set the destination address,in this case an IPv6 address. */
dest_address.nxd_ip_address_version  = NX_IP_VERSION_V6;
dest_address.nxd_ip_address.v6[0]    = 0x20011234;
dest_address.nxd_ip_address.v6[1]    = 0x56780000;
dest_address.nxd_ip_address.v6[2]    = 0;
dest_address.nxd_ip_address.v6[3]    = 1;

UINT ttl, tos;

ttl = 128;

tos = 0;

/* Enable RAW IP handling on the previously created IP instance.*/
status = nx_raw_ip_packet_enable(&ip_0);

/* Allocate a packet pointed to by packet_ptr from the IP packet
   pool. */
/* Then transmit the packet to the destination address. */

status = nxd_ip_raw_packet_send(&ip_0, packet_ptr, dest_address,
                                NX_PROTOCOL_UDP, ttl, tos);

/* A status return of NX_SUCCESS indicates the packet was
   successfully transmitted. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_source_send

## <a name="nxd_ip_raw_packet_source_send"></a>nxd_ip_raw_packet_source_send
Enviar pacotes brutos usando endereço de origem especificado

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ip_raw_packet_source_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *destination_ip,
    UINT address_index,
    ULONG protocol,
    UINT ttl,
    ULONG tos);
```
### <a name="description"></a>Descrição

Este serviço envia um pacote IPv4 ou IPv6 em bruto utilizando o endereço IPv4 ou IPv6 especificado como endereço de origem. Este serviço é normalmente utilizado num sistema multihome, se o sistema não conseguir determinar uma interface adequada (por exemplo, se o endereço IP de destino for transmitido IPv4, multicast ou endereço multicast IPv6). O parâmetro *address_index* permite que a aplicação especifique o endereço de origem a utilizar ao enviar este pacote cru.

A instância IP deve ser previamente criada e o manuseamento de pacotes IP crus deve ser ativado utilizando o serviço ***nx_ip_raw_packet_enable.***

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro de instância IP
- **packet_ptr** Ponteiro para pacote para enviar
- **destination_ip** Endereço IP de destino
- **address_index** Indexar os endereços IPv4 ou IPv6 para usar como endereço de origem.
- **protocolo** Valor para o campo do protocolo
- **ttl** Valor para ttl ou limite de lúpulo
- **tos** Valor para tos ou classe de tráfego e rótulo de fluxo

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Packet é enviado com sucesso
- **NX_UNDERFLOW** (0x02) Não há espaço suficiente para cabeçalho IPv4 ou IPv6 no pacote
- **NX_OVERFLOW** (0x03) O ponteiro do apêndice do pacote é inválido
- **NX_PTR_ERROR** (0x07) Ponteiro inválido para bloco de controlo IP, pacote ou destination_ip
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço
- **NX_NOT_ENABLED** (0x14) Processamento bruto não habilitado
- **NX_IP_ADDRESS_ERROR** (0x21) Erro de endereço
- **NX_INVALID_INTERFACE** (0x4C) Índice de interface inválido
- **NX_INVALID_PARAMETERS** (0x4D) Entrada de endereço IPv6 não válida

### <a name="allowed-from"></a>Permitido a partir de

Fio

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
#define SOURCE_ADDRESS_INDEX 2

/* Send a raw packet from specified interface. */
status = nxd_ip_raw_packet_source_send(&ip_0, packet_ptr,
                                       dest_ip,
                                       SOURCE_ADDRESS_INDEX,
                                       NX_IP_RAW,
                                       NX_IP_TIME_TO_LIVE,
                                       NX_IP_NORMAL);

/* If status == NX_SUCCESS, raw packet has been sent out on the
   specified interface. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send

## <a name="nxd_ipv6_address_change_notify"></a>nxd_ipv6_address_change_notify
Definir alteração de endereço ipv6 notificar

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_address_change_notify(
    NX_IP *ip_ptr,
    VOID (*ip_address_change_notify)(NX_IP *, UINT, UINT, UINT, ULONG *));
```
### <a name="description"></a>Descrição

Este serviço regista uma rotina de chamada de chamada de aplicação que o NetX Duo chama sempre que o Endereço IPv6 é alterado.

Este serviço está disponível se a biblioteca NetX Duo for construída é a opção ***NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY*** definida.

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro do bloco de controlo IP
- **ip_address_change_notify** Função de retorno de aplicação

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Conjunto de sucesso
- **NX_NOT_SUPPORTED** (0x4B) a funcionalidade de notificação de alteração de endereço iPv6 não está incorporada na biblioteca NetX Duo
- **NX_PTR_ERROR** (0x07) Ponteiro do bloco de controlo IP inválido
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço
- **NX_NOT_ENABLED** (0x14) IPv6 notificação de alteração de endereço não é compilada

### <a name="allowed-from"></a>Permitido a partir de

Fio

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
VOID ip_address_change_notify(NX_IP *ip_ptr, UINT status,
                              UINT interface_index,
                              UINT address_index,
                              ULONG *ip_address)
{

   /* Do something when ip address changed. */
}

void ip_address_thread_entry(ULONG id)
{

   /* Set the ip address change notify of IP instance. */
   status = nxd_ipv6_address_change_notify (&ip_0, ip_address_change_notify);

/* If status == NX_SUCCESS, the ip address change notify of IP
   instance was successfully set. */
}
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_address_delete"></a>nxd_ipv6_address_delete
Apagar endereço IPv6

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_address_delete(
    NX_IP *ip_ptr, 
    UINT address_index);
```
### <a name="description"></a>Descrição

Este serviço elimina o endereço IPv6 no índice especificado na tabela de endereços IPv6 da instância IP especificada. Não há equivalente NetX.

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro para a instância IP previamente criada
- **address_index** Tabela de endereços IPv6 de instância IP

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Endereço eliminado com sucesso
- **NX_NOT_SUPPORTED** (0x4B) IPv6 não está integrado na biblioteca NetX Duo
- **NX_NO_INTERFACE_ADDRESS** (0x50) Não é possível encontrar uma interface de saída adequada
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
NXD_ADDRESS ip_address;
UINT        address_index;

/* Delete the IPv6 address at the specified address table index. */
address_index = 1;
status = nxd_ipv6_address_delete(&ip_0, address_index);

/* A status return of NX_SUCCESS indicates that the IP instance
   address is successfully deleted. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_address_get"></a>nxd_ipv6_address_get
Recuperar endereço e prefixo IPv6

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_address_get(
    NX_IP *ip_ptr, 
    UINT address_index, 
    NXD_ADDRESS *ip_address,
    ULONG *prefix_length,
    UINT *interface_index);
```
### <a name="description"></a>Descrição

Este serviço recupera o endereço e prefixo IPv6 no índice especificado na tabela de endereços da instância IP especificada. O índice da interface física com o qual o endereço IPv6 está associado é devolvido no *ponteiro interface_index.* Os serviços equivalentes NetX são ***nx_ip_address_get** _ e _*_nx_ip_interface_address_get_**.

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro para a instância IP previamente criada
- **address_index** Tabela de endereços de instância IP
- **ip_address** Ponteiro para o endereço a definir
- **prefix_length** Comprimento do prefixo do endereço (máscara de sub-rede)
- **interface_index** Ponteiro para o índice da interface

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) IPv6 está habilitado com sucesso
- **NX_NOT_SUPPORTED** (0x4B) funcionalidade IPv6 não está incorporada na biblioteca NetX Duo.
- **NX_NO_INTERFACE_ADDRESS** (0x50) Sem endereço de interface, ou address_index inválidos
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
NXD_ADDRESS ip_address;
UINT        address_index;
ULONG       prefix_length;
UINT        interface_index;

/* Get the IPv6 address at the specified address table index. If
   found, the address network interface is returned in the
   interface_index input, as well as the address prefix in the
   prefix_length input. */

address_index = 1;
status = nxd_ipv6_address_get(&ip_0, address_index, &ip_address,
                              &prefix_length, &interface_index);

/* A status return of NX_SUCCESS indicates that the IP instance
   address is successfully retrieved. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_address_set"></a>nxd_ipv6_address_set
Definir endereço iPv6 e prefixo

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_address_set(
    NX_IP *ip_ptr, 
    UINT interface_index,
    NXD_ADDRESS *ip_address,
    ULONG prefix_length,
    UINT *address_index);
```
### <a name="description"></a>Descrição

Este serviço define o endereço EPv6 fornecido e prefixo para a instância IP especificada. Se o *argumento address_index* não for nulo, o índice na tabela de endereços IPv6 onde o endereço é inserido é devolvido. Os serviços equivalentes NetX são ***nx_ip_address_set** _ e _*_nx_ip_interface_address_set_**.

### <a name="parameters"></a>Parâmetros  

- **ip_ptr** Ponteiro para a instância IP previamente criada
- **interface_index** Índice para a interface o endereço IPv6 está associado
- **ip_address** Ponteiro para o endereço a definir
- **prefix_length** Comprimento do prefixo do endereço (máscara de sub-rede)
- **address_index** Ponteiro para o índice na tabela de endereços onde o endereço é inserido

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) IPv6 está habilitado com sucesso
- **NX_NO_MORE_ENTRIES** (0x15) tabela de endereços IP está cheia
- **NX_NOT_SUPPORTED** (0x4B) funcionalidade IPv6 não está incorporada na biblioteca NetX Duo.
- **NX_DUPLICATED_ENTRY** (0x52) O endereço IP fornecido já é utilizado neste caso IP
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IPv6 inválido
- **NX_INVALID_INTERFACE** (0x4C) Interface aponta para uma interface de rede inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
NXD_ADDRESS ip_address;
UINT        address_index;
UINT        interface_index;

ip_address.nxd_ip_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0] = 0x20010000;
ip_address.nxd_ip_address.v6[1] = 0;
ip_address.nxd_ip_address.v6[2] = 0;
ip_address.nxd_ip_address.v6[3] = 1;

/* First create an IP instance with packet pool, source address, and
   driver.*/
status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                     IP_ADDRESS(1,2,3,4),
                     0xFFFFFF00UL, &pool_0,_nx_ram_network_driver,
                     pointer, 2048, 1);

/* Then enable IPv6 on the IP instance. */
status = nxd_ipv6_enable(&ip_0);

/* Set the IPv6 address (a global address as indicated by the 64 bit
   prefix) using the IPv6 address just created on the primary device
   (index zero). The index into the address table is returned in
   address_index. */
interface_index = 0;
status = nxd_ipv6_address_set(&ip_0, interface_index, &ip_address,
                              64,&address_index);

/* A status return of NX_SUCCESS indicates that the IPv6 address is
   successfully assigned to the primary interface (interface 0). */
```

### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_default_router_add"></a>nxd_ipv6_default_router_add
Adicione um router IPv6 à tabela de router predefinido

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_default_router_add(
    NX_IP *ip_ptr,
    NXD_ADDRESS *router_address,
    ULONG router_lifetime,
    UINT index_index);
```
### <a name="description"></a>Descrição

Este serviço adiciona um router padrão IPv6 na interface física especificada à tabela de router predefinido. O serviço NetX IPv4 equivalente é ***nx_ip_gateway_address_set***.

*router_address* deve apontar para um endereço IPv6 válido, e o router deve estar diretamente acessível a partir da interface física especificada.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada
- **router_address** Ponteiro para o endereço do router predefinido, na ordem byte de anfitrião
- **router_lifetime** Tempo de vida do router padrão, em segundos. Os valores válidos são:
    - **0xFFFF:** Não há tempo para sair.
    - **0-0xFFFE:** Valor de tempo limite, em segundos
- **index_index** Ponteiro para a localização de memória válida para o índice de rede através do qual o router pode ser alcançado

### <a name="return-values"></a>Valores de devolução  

- **router padrão NX_SUCCESS** (0x00) é adicionado com sucesso
- **NX_NO_MORE_ENTRIES** (0x17) Não há mais entradas disponíveis na tabela de router predefinido.
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IPv6 inválido
- **NX_NOT_SUPPORTED** (0x4B) funcionalidade IPv6 não está incorporada na biblioteca NetX Duo.
- **NX_INVALID_PARAMETERS** (0x4D) Entrada de endereço IPv6 não válida
- **NX_PTR_ERROR** (0x07) Instância IP inválida ou espaço de armazenamento
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço
- **NX_INVALID_INTERFACE** (0x4C) Índice de interface de router inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* This example adds a default router for the primary interface at
   fe80::1219:B9FF:FE37:ac to the default router table. */

#define PRIMARY_INTERFACE 0

NXD_ADDRESS router_address;

/* Set the router address version to IPv6 */
router_address.nxd_ip_version   = NX_IP_VERSION_V6;

/* Set the IPv6 address, in host byte order. */
router_address.nxd_ip_address[0] = 0xfe800000;
router_address.nxd_ip_address[1] = 0x0;
router_address.nxd_ip_address[2] = 0x1219B9FF;
router_address.nxd_ip_address[3] = 0xFE3700AC;

/* Set IPv6 default router. */
status = nxd_ipv6_default_router_add(ip_ptr, &router_address,
                                     0xFFFF, PRIMARY_INTERFACE);

/* Unless invalid pointer input is detected by the error checking
   Service, status return is always NX_SUCCESS. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_delete"></a>nxd_ipv6_default_router_delete
Remover O Router IPv6 da tabela de router predefinido

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_default_router_delete (
    NX_IP *ip_ptr,
    NXD_ADDRESS *router_address);
```
### <a name="description"></a>Descrição

Este serviço elimina um router padrão IPv6 da tabela de router predefinido. O serviço NetX IPv4 equivalente é ***nx_ip_gateway_address_clear***.

### <a name="restrictions"></a>Restrições

A instância IP foi criada. *router_address* devemos indicar informações válidas.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para uma instância IP previamente criada
- **router_address** Ponteiro para o endereço de gateway padrão IPv6

### <a name="return-values"></a>Valores de devolução 

- **Router NX_SUCCESS** (0x00) eliminado com sucesso
- **NX_NOT_SUPPORTED** (0x4B) funcionalidade IPv6 não está incorporada na biblioteca NetX Duo.
- **NX_NOT_FOUND** (0x4E) A entrada do router não pode ser encontrada
- **NX_PTR_ERROR** (0x07) Instância IP inválida ou espaço de armazenamento
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço
- **NX_INVALID_PARAMETERS** (0x82) Entrada inválida sem ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/*This example removes a default router:fe80::1219:B9FF:FE37:ac */

NXD_ADDRESS router_address;

/* Set the router_address version to IPv6 */
router_address.nxd_ip_version = NX_IP_VERSION_V6;

/* Program the IPv6 address, in host byte order. */
router_address.nxd_ip_address[0] = 0xfe800000;
router_address.nxd_ip_address[1] = 0x0;
router_address.nxd_ip_address[2] = 0x1219B9FF;
router_address.nxd_ip_address[3] = 0xFE3700AC;

/* Delete the IPv6 default router. */
nxd_ipv6_default_router_delete(ip_ptr, &router_address);
```
### <a name="see-also"></a>Consulte também

- nx_ip_gateway_address_clearnx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_getnx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_entry_get"></a>nxd_ipv6_default_router_entry_get
Obtenha entrada de router predefinido

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_default_router_entry_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    UINT entry_index,
    NXD_ADDRESS *router_addr,
    ULONG *router_lifetime,
    ULONG *prefix_length,
    ULONG *configuration_method);
```
### <a name="description"></a>Descrição

Este serviço recupera uma entrada de router a partir da tabela de encaminhamento padrão IPv6 que está ligada a um dispositivo de rede especificado.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro do bloco de controlo IP
- **interface_index** Índice da interface de rede
- **entry_index** Índice de Entrada
- **router_addr** Endereço IPv6 do Router
- **router_lifetime** Ponteiro para o tempo de vida do router
- **prefix_length** Ponteiro para o comprimento do prefixo
- **configuration_method** Ponteiro para a informação sobre como a entrada foi configurada

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Com sucesso obter
- **NX_NOT_FOUND** (0x4E) entrada do Router não encontrada
- **NX_INVALID_INTERFACE** (0x4C) O índice de interface não é válido
- **NX_PTR_ERROR** (0x07) Ponteiro do bloco de controlo IP inválido
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
#define PRIMARY_INTERFACE 0
NXD_ADDRESS            router_addr;
ULONG                  router_lifetime;
ULONG                  prefix_length;
ULONG                  configuration_method;

/* Get the router entry of specified interface. */
status = nxd_ipv6_default_router_entry_get (&ip_0,
                                            PRIMARY_INTERFACE,
                                            entry_index,
                                            &router_addr,
                                            &router_lifetime,
                                            &prefix_length,
                                            &configuration_method);

/* If status == NX_SUCCESS, the router entry was successfully
   got. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_get"></a>nxd_ipv6_default_router_get
Recupere um Router IPv6 da tabela de router predefinido

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_default_router_get(
    NX_IP *ip_ptr, 
    UINT interface_index
    NXD_ADDRESS *router_address,
    ULONG *router_lifetime,
    ULONG *prefix_length);
```
### <a name="description"></a>Descrição

Este serviço recupera um endereço de router padrão IPv6, duração útil e prefixo na interface física especificada a partir da tabela de router predefinido. O serviço NetX IPv4 equivalente é ***nx_ip_gateway_address_get*.**

*router_address* deve apontar para uma estrutura de NXD_ADDRESS válida, para que este serviço possa preencher o endereço IPv6 do router predefinido.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada
- **interface_index** O índice para a interface de rede que o router é acessível através
- **router_address** Ponteiro para o espaço de armazenamento para o valor de retorno do endereço de router predefinido, na ordem byte de anfitrião.
- **router_lifetime** Ponteiro para a vida útil do router
- **prefix_length** Ponteiro para o comprimento do prefixo do endereço do router

### <a name="return-values"></a>Valores de devolução 

- **router padrão NX_SUCCESS** (0x00) é adicionado com sucesso
- **NX_NOT_SUPPORTED** (0x4B) funcionalidade IPv6 não está incorporada na biblioteca NetX Duo.
- **router padrão NX_NOT_FOUND** (0x4E) não encontrado
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço
- **NX_INVALID_INTERFACE** (0x4C) Índice de interface de router inválido
- **NX_PTR_ERROR** (0x07) Instância IP inválida ou espaço de armazenamento

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* This example retrieves a default router for the primary device
   from the default router table. */

#define PRIMARY_INTERFACE 0

NXD_ADDRESS router_address;
ULONG       router_lifetime;
ULONG       prefix_length;

/* Get IPv6 default router. */
status = nxd_ipv6_default_router_get(ip_ptr, PRIMARY_INTERFACE,
                                     &router_address,
                                     &router_lifetime,
                                     &prefix_length);

/* If status returns NX_SUCCESS, the router address and related
   information is returned successfully. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_number_of_entries_get"></a>nxd_ipv6_default_router_number_of_entries_get
Obtenha o número de routers IPv6 predefinidos

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_default_router_number_of_entries_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    UINT *num_entries);
```
### <a name="description"></a>Descrição

Este serviço recupera o número de routers padrão IPv6 configurados numa determinada interface de rede.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro do bloco de controlo IP
- **interface_index** Índice da interface de rede
- **num_entries** Destino para o número de routers IPv6 num dispositivo de rede especificado

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Com sucesso obter
- **NX_NOT_SUPPORTED** (0x4B) funcionalidade IPv6 não está incorporada na biblioteca NetX Duo.
- **NX_INVALID_INTERFACE** (0x4C) O valor do índice do dispositivo não é válido
- **NX_PTR_ERROR** (0x07) Ponteiro do bloco de controlo IP inválido ou ponteiro num_entries

### <a name="allowed-from"></a>Permitido a partir de

Fio

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
#define PRIMARY_INTERFACE 0
UINT                   num_entries;

/* Get the router entries of specified interface. */
status = nxd_ipv6_default_router_number_of_entries_get(&ip_0,
                                                       PRIMARY_INTERFACE,
                                                       &num_entries);

/* If status == NX_SUCCESS, the router entries was successfully
   retrieved. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get

## <a name="nxd_ipv6_disable"></a>nxd_ipv6_disable
Desative a função IPv6

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descrição

Este serviço desativa o IPv6 para a instância IP especificada. Também limpa a tabela de routers predefinidos, cache ND e tabela de endereços IPv6, deixa todos os grupos multicast e repõe as variáveis de solicitação do router. Este serviço não tem efeito se o IPv6 não estiver ativado.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro de instância IP

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) Desativação bem sucedida
- **NX_NOT_SUPPORTED** (0x4B) funcionalidade IPv6 não está incorporada na biblioteca NetX Duo.
- **NX_PTR_ERROR** (0x07) Ponteiro do bloco de controlo IP inválido
- **NX_NOT_SUPPORT** (0x4B) módulo IPv6 não é compilado
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Disable IPv6 feature on this IP instance. */
status = nxd_ipv6_disable(&ip_0);

/* If status == NX_SUCCESS, disables IPv6 feature on IP instance.*/
```
### <a name="see-also"></a>Consulte também 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_enable"></a>nxd_ipv6_enable
Ativar serviços IPv6

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descrição

Este serviço permite serviços IPv6. Quando os serviços IPv6 estão ativados, a instância IP junta-se ao grupo multicast all-node (FF02::1). Este serviço não define o endereço local de ligação ou endereço global. As aplicações devem utilizar *nxd_ipv6_address_set* para configurar os endereços de rede do dispositivo. Não há equivalente NetX.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para a instância IP previamente criada

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) IPv6 está habilitado com sucesso
- **NX_ALREADY_ENABLED** (0x15) IPv6 já está ativado
- **NX_NOT_SUPPORTED** (0x4B) funcionalidade IPv6 não está incorporada na biblioteca NetX Duo.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* First create an IP instance with packet pool, source address, and
   driver.*/
status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                      IP_ADDRESS(1,2,3,4),
                      0xFFFFFF00UL, &pool_0,_nx_ram_network_driver,
                      pointer, 2048, 1);

/* Then enable IPv6 on the IP instance. */
status = nxd_ipv6_enable(&ip_0);

/* A status return of NX_SUCCESS indicates that the IP instance is
   enabled for IPv6 services. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_multicast_interface_join"></a>nxd_ipv6_multicast_interface_join
Junte-se a um grupo multicast IPv6

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_multicast_interface_join(
    NX_IP *ip_ptr,
    NXD_ADDRESS *group_address,
    UINT interface_index);
```

### <a name="description"></a>Descrição

Este serviço permite que uma aplicação se junte a um endereço multicast IPv6 específico numa interface de rede específica. O controlador de ligação é notificado para adicionar o endereço multicast. Este serviço está disponível se a biblioteca NetX Duo for construída com a opção ***NX_ENABLE_IPV6_MULTICAST*** definida.

### <a name="parameters"></a>Parâmetros  

- **ip_ptr** Ponteiro de instância IP
- **group_address** Endereço multicast IPv6
- **interface_index** O índice da interface de rede associada ao grupo multicast

### <a name="return-values"></a>Valores de devolução  

- **NX_SUCCESS** (0x00) permite receber com sucesso o endereço multicast IPv6
- **NX_NO_MORE_ENTRIES** (0x17) Não há mais inscrições na tabela multicast IPv6.
- **NX_OVERFLOW** (0x03) Não há mais endereços de grupo disponíveis no controlador do dispositivo
- **NX_NOT_SUPPORTED** (0x4B) funcionalidade IPv6 ou recurso multicast IPv6 não é incorporado na biblioteca NetX Duo
- **NX_PTR_ERROR** (0x07) Ponteiro do bloco de controlo IP inválido
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IPv6 inválido
- **NX_INVALID_INTERFACE** (0x4C) O índice de interface não é válido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
#define PRIMARY_INTERFACE 0

/* Join multicast group on this IP instance. */
status = nxd_ipv6_multicast_interface_join(&ip_0,
                                           &group_address,
                                           PRIMARY_INTERFACE);

/* If status == NX_SUCCESS, interface of index on IP instance
   has joined the multicast group. */
```
### <a name="see-also"></a>Consulte também

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_leave

## <a name="nxd_ipv6_multicast_interface_leave"></a>nxd_ipv6_multicast_interface_leave
Deixe um grupo multicast IPv6

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_multicast_interface_leave(
    NX_IP *ip_ptr,
    NXD_ADDRESS *group_address,
    UINT interface_index);
```
### <a name="description"></a>Descrição

Este serviço remove o endereço multicast IPv6 específico do dispositivo de rede específico. O controlador de ligação também é notificado da remoção do endereço multicast IPv6. Este serviço está disponível se a biblioteca NetX Duo for construída com a opção ***NX_ENABLE_IPV6_MULTICAST*** definida.

### <a name="parameters"></a>Parâmetros  

- **ip_ptr** Ponteiro de instância IP
- **group_address** Endereço multicast IPv6
- **interface_index** O índice da interface de rede associado ao grupo

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Licença multicast bem sucedida
- **NX_ENTRY_NOT_FOUND** (0x16) Entrada não encontrada
- **NX_NOT_SUPPORTED** (0x4B) funcionalidade IPv6 ou recurso multicast IPv6 não é incorporado na biblioteca NetX Duo
- **NX_PTR_ERROR** (0x07) Ponteiro do bloco de controlo IP inválido
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IPv6 inválido
- **NX_INVALID_INTERFACE** (0x4C) O índice de interface não é válido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
#define PRIMARY_INTERFACE 0

/* Leave multicast address on this IP instance. */
status = nxd_ipv6_multicast_interface_leave(&ip_0,
                                            &group_address,
                                            primary_interface);

/* If status == NX_SUCCESS, interface of index on IP instance
   has left the multicast group. */
```
### <a name="see-also"></a>Consulte também

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join

## <a name="nxd_ipv6_stateless_address_autoconfig_disable"></a>nxd_ipv6_stateless_address_autoconfig_disable
Desativar o endereço apátrida automaticamente configurar

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_stateless_address_autoconfig_disable(
    NX_IP *ip_ptr,
    UINT interface_index);
```
### <a name="description"></a>Descrição

Este serviço desativa a função de configuração automática de endereço apátrida IPv6 num dispositivo de rede especificado. Não tem efeito se o endereço IPv6 tiver sido configurado.

Este serviço está disponível se a biblioteca NetX Duo for construída com a opção ***NX_IPV6_STATELESS_AUTOCONFIG_CONTROL*** definida.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro de instância IP
- **interface_index** O índice da interface de rede que o endereço apátrida IPv6 deve ser desativado.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) desativa com sucesso a função de configuração automática de endereços apátridas.
- **NX_NOT_SUPPORTED** (0x4B) funcionalidade IPv6 ou função de controlo autoconfig de endereço apátrida IPv6 não está incorporada na biblioteca NetX Duo
- **NX_INVALID_INTERFACE** (0x4C) O índice de interface não é válido
- **NX_PTR_ERROR** (0x07) Ponteiro do bloco de controlo IP inválido
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
#define PRIMARY_INTERFACE 0

/* Disable stateless address auto configuration on this IP instance. */
status = nxd_ipv6_stateless_address_autoconfig_disable(&ip_0,
                                                       PRIMARY_INTERFACE);

/* If status == NX_SUCCESS, disables stateless address auto
   configuration on IP instance. */
```
### <a name="see-also"></a>Consulte também 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_stateless_address_autoconfig_enable"></a>nxd_ipv6_stateless_address_autoconfig_enable
Permitir a autoconfigução de endereço apátrida

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_stateless_address_autoconfig_enable(
    NX_IP *ip_ptr,
    UINT interface_index);
```
### <a name="description"></a>Descrição

Este serviço permite a funcionalidade de configuração automática de endereço apátrida IPv6 num dispositivo de rede especificado.

Este serviço está disponível se a biblioteca NetX Duo for construída com a opção ***NX_IPV6_STATELESS_AUTOCONFIG_CONTROL*** definida.

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro de instância IP
- **interface_index** O índice da interface de rede que o endereço apátrida IPv6 deve ser ativado automaticamente.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Permite com sucesso a função de configuração automática de endereços apátridas.
- **NX_ALREADY_ENABLED** (0x15) Já ativado
- **NX_NOT_SUPPORTED** (0x4B) funcionalidade IPv6 ou função de controlo autoconfig de endereço apátrida IPv6 não está incorporada na biblioteca NetX Duo
- **NX_INVALID_INTERFACE** (0x4C) O índice de interface não é válido
- **NX_PTR_ERROR** (0x07) Ponteiro do bloco de controlo IP inválido
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
#define PRIMARY_INTERFACE

/* Enable stateless address auto configuration on this
   IP instance. */
status = nxd_ipv6_stateless_address_autoconfig_enable(&ip_0,
                                                      PRIMARY_INTERFACE);

/* If status == NX_SUCCESS, enables stateless address auto
   configuration on IP instance. */
```
### <a name="see-also"></a>Consulte também 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable

## <a name="nxd_nd_cache_entry_delete"></a>nxd_nd_cache_entry_delete
Excluir entrada de endereço IPv6 na Cache do Vizinho

### <a name="prototype"></a>Prototype  

```c
UINT nxd_nd_cache_entry_delete(
    NX_IP *ip_ptr, 
    ULONG *ip_address);
```
### <a name="description"></a>Descrição

Este serviço elimina uma entrada de cache de descoberta de vizinho iPv6 para o endereço IP fornecido. A função LíquidaX IPv4 equivalente é ***nx_arp_static_entry_delete***.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada
- **ip_address** Endereço do Ponteiro para iPv6 para apagar, na ordem byte de anfitrião

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) apagou com sucesso o endereço
- **NX_ENTRY_NOT_FOUND** (0x16) Endereço não encontrado na cache do vizinho IPv6
- **NX_NOT_SUPPORTED** (0x4B) IPv6 não está integrado na biblioteca NetX Duo
- **NX_PTR_ERROR** (0x07) Instância IP inválida ou espaço de armazenamento
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* This example deletes an entry from the neighbor cache table. */

NXD_ADDRESS ip_address;

ip_address.nxd_ip_address_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]   = 0x20011234;
ip_address.nxd_ip_address.v6[1]   = 0x56780000;
ip_address.nxd_ip_address.v6[2]   = 0;
ip_address.nxd_ip_address.v6[3]   = 1;

/* Delete an entry in the neighbor cache table with the specified IPv6
   address and hardware address. */
status = nxd_nd_cache_entry_delete(&ip_0,
                                   &ip_address.nxd_ip_address.v6[0]);

/* If status == NX_SUCCESS, the entry was deleted from the neighbor cache
   table. */
```
### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_entry_set"></a>nxd_nd_cache_entry_set
Adicione um endereço IPv6/MAC Mapping à Cache do Vizinho

### <a name="prototype"></a>Prototype  

```c
UINT nxd_nd_cache_entry_set(
    NX_IP *ip_ptr, 
    NXD_ADDRESS *dest_ip,
    UINT interface_index, 
    char *mac);
```

### <a name="description"></a>Descrição

Este serviço adiciona uma entrada na cache de descoberta do vizinho para o endereço IP especificado *ip_address* mapeado para o endereço MAC de hardware no índice de interface de rede especificado (interface_index). O serviço NetX IPv4 equivalente é ***nx_arp_static_entry_create***.

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro para instância IP previamente criada
- **dest_ip** Indicação para o endereço IPv6
- **interface_index** Índice especificando interface de rede física onde o endereço IPv6 de destino pode ser alcançado 
- **mac** Ponteiro para o endereço de hardware.

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) Entrada adicionada com sucesso
- **NX_NOT_SUCCESSFUL** (0x43) Cache inválido ou nenhuma entrada de cache do vizinho disponível
- **NX_NOT_SUPPORTED** (0x4B) IPv6 não está integrado na biblioteca NetX Duo
- **NX_PTR_ERROR** (0x07) Instância IP inválida ou espaço de armazenamento
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço
- **NX_INVALID_INTERFACE** (0x4C) Valor do índice de interface inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* This example adds an entry on the primary network interface to
   the neighbor cache table. */

#define PRIMARY_INTEFACE 0

NXD_ADDRESS ip_address;
UCHAR hw_address[6] = {0x0, 0xcf,0x01,0x02, 0x03, 0x04};
CHAR  *mac;

mac = (CHAR *)&hw_address[0];

ip_address.nxd_ip_address_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]   = 0x20011234;
ip_address.nxd_ip_address.v6[1]   = 0x56780000;
ip_address.nxd_ip_address.v6[2]   = 0;
ip_address.nxd_ip_address.v6[3]   = 1;

/* Create an entry in the neighbor cache table with the specified
   IPv6 address and hardware address. */
status = nxd_nd_cache_entry_set(&ip_0,
                                &ip_address.nxd_ip_address.v6[0],
                                PRIMARY_INTERFACE, mac);

/* If status == NX_SUCCESS, the entry was added to the neighbor
   cache table. */
```
### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_hardware_address_find"></a>nxd_nd_cache_hardware_address_find
Localizar Endereço de Hardware para um endereço IPv6

### <a name="prototype"></a>Prototype  

```c
UINT nxd_nd_cache_hardware_address_find(
    NX_IP *ip_ptr,
    NXD_ADDRESS *ip_address,
    ULONG *physical_msw,
    ULONG *physical_lsw
    UINT *interface_index);
```
### <a name="description"></a>Descrição

Este serviço tenta encontrar um endereço de hardware físico na cache de descoberta do vizinho IPv6 que está associado com o endereço IPv6 fornecido. O índice da interface de rede através do qual o vizinho pode ser alcançado também é devolvido no parâmetro *interface_index.* O serviço NetX IPv4 equivalente é ***nx_arp_hardware_address_find***.

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro para instância IP previamente criada
- **ip_address** Ponteiro para endereço IP para encontrar, encomenda byte anfitrião
- **physical_msw** Ponteiro para os 16 melhores bits (47-32) do endereço físico, em ordem byte anfitrião 
- **physical_lsw** Ponteiro para os 32 bits inferiores (31-0) do endereço físico em ordem byte anfitrião
- **interface_index** Ponteiro para a localização de memória válida para o índice de interface especificando o dispositivo de rede no qual o endereço IPv6 pode ser alcançado.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) encontrou com sucesso o endereço
- **NX_ENTRY_NOT_FOUND** (0x16) Mapeamento não na cache do vizinho
- **NX_NOT_SUPPORTED** (0x4B) IPv6 não está integrado na biblioteca NetX Duo
- **NX_INVALID_PARAMETERS** (0x4D) O endereço IP fornecido não é a versão 6.
- **NX_PTR_ERROR** (0x07) Instância IP inválida ou espaço de armazenamento
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* This example inputs an IP address on the primary network in order
   to obtain the hardware address it is mapped to in the neighbor
   cache able. */

NXD_ADDRESS  ip_address;
ULONG physical_msw, physical_lsw;
UINT  interface_index;

ip_address.nxd_ip_address_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]   = 0x20011234;
ip_address.nxd_ip_address.v6[1]   = 0x56780000;
ip_address.nxd_ip_address.v6[2]   = 0;
ip_address.nxd_ip_address.v6[3]   = 1;

/* Obtain the hardware address mapped to the supplied global IPv6
   address. */
status = nxd_nd_cache_hardware_address_find(&ip_0, &ip_address,
                                            &physical_msw,
                                            &physical_lsw
                                            &interface_index);

/* If status == NX_SUCCESS, a matching entry was found in the
   neighbor cache table and the hardware address returned in
   variables physical_msw and physical_lsw, the index of the network
   interface through which the neighbor can be reached is stored in
   interface_index. */
```
### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_invalidate"></a>nxd_nd_cache_invalidate
Invalidar a Cache de Descoberta do Vizinho

### <a name="prototype"></a>Prototype  

```c
UINT nxd_nd_cache_invalidate(NX_IP *ip_ptr);
```
### <a name="description"></a>Descrição

Este serviço invalida toda a cache de descoberta do vizinho IPv6. Este serviço pode ser invocado antes ou depois de o ICMPv6 ter sido ativado. Este serviço não é aplicável à conectividade IPv4, pelo que não existe um serviço equivalente NetX.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Indicação para a instância IP

### <a name="return-values"></a>Valores de devolução

- **cache NX_SUCCESS** (0x00) invalidada com sucesso
- **NX_NOT_SUPPORTED** (0x4B) IPv6 não está integrado na biblioteca NetX Duo
- **NX_PTR_ERROR** (0x07) Instância IP inválida
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* This example invalidates the host neighbor cache table. */

/* Invalidate the cache table bound to the IP instance. */
status = nxd_nd_cache_invalidate (&ip_0);

/* If status == NX_SUCCESS, all entries in the neighbor cache table
   are invalidated. */
```
### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_ip_address_find"></a>nxd_nd_cache_ip_address_find
Obter endereço IPv6 para um endereço físico

### <a name="prototype"></a>Prototype  

```c
UINT nxd_nd_cache_ip_address_find(
    NX_IP *ip_ptr,
    NXD_ADDRESS *ip_address,
    ULONG physical_msw,
    ULONG physical_lsw,
    UINT *interface_index);
```
### <a name="description"></a>Descrição

Este serviço tenta encontrar um endereço IPv6 na cache de descoberta do vizinho IPv6 que está associado com o endereço físico fornecido. O índice da interface de rede através do qual o vizinho pode ser alcançado também é devolvido. O serviço NetX IPv4 equivalente é ***nx_arp_ip_address_find***.

### <a name="parameters"></a>Parâmetros 

- **ip_ptr** Ponteiro para instância IP previamente criada
- **ip_address** Ponteiro para estrutura NXD_ADDRESS válida
- **physical_msw** Top 16 bits (47-32) do endereço físico para encontrar, ordem byte anfitrião
- **physical_lsw** Inferior 32 bits (31-0) do endereço físico para encontrar, ordem byte anfitrião
- **interface_index** Ponteiro para o índice do dispositivo de rede através do qual o endereço IPv6 pode ser alcançado

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) encontrou com sucesso o endereço
- **NX_ENTRY_NOT_FOUND** (0x16) Endereço físico não encontrado na cache do vizinho
- **NX_NOT_SUPPORTED** (0x4B) IPv6 não está integrado na biblioteca NetX Duo
- **NX_PTR_ERROR** (0x07) Instância IP inválida ou espaço de armazenamento
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço 
- **NX_INVALID_PARAMETERS** endereço MAC (0x4D) é zero.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* This example inputs a hardware address to search on for the
   matching IPv6 global address in the neighbor cache table. */

NXD_ADDRESS ip_address;
ULONG physical_msw = 0xcf;
ULONG physical_lsw = 0x01020304;
UINT  interface_index;

/* Obtain the IPv6 address mapped to the supplied hardware
   Address on the primary device. */
status = nxd_nd_cache_ip_address_find(&ip_0, &ip_address,
                                      physical_msw, physical_lsw,
                                      &interface_index);

/* If status == NX_SUCCESS, a matching entry was found in the
   neighbor cache table and the global IPv6 address returned in
   variable ip_address. */
```
### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate

## <a name="nxd_tcp_client_socket_connect"></a>nxd_tcp_client_socket_connect
Faça uma ligação TCP

### <a name="prototype"></a>Prototype  

```c
UINT nxd_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr
    NXD_ADDRESSS *server_ip,
    UINT server_port,
    ULONG wait_option);
```
### <a name="description"></a>Descrição

Este serviço faz a ligação TCP utilizando uma tomada de cliente TCP previamente criada para a porta do servidor especificado. Este serviço funciona em redes IPv4 ou IPv6. As portas de servidores TCP válidas variam de 0 a 0xFFFF. O NetX Duo determina a interface física adequada com base no endereço IP do servidor. O equivalente NetX IPv4 é ***nx_tcp_client_socket_connect***.

A tomada deve ter sido ligada a um porto local.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para tomada TCP previamente criada
- **server_ip** Ponteiro para endereço de destino IPv4 ou IPv6, em encomenda byte anfitrião
- **server_port** Número da porta do servidor para ligar a (1 a 0xFFFF), em ordem byte de anfitrião
- **wait_option** Opção de espera enquanto a ligação está a ser estabelecida. As opções de espera são definidas da seguinte forma:
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **valor de tempo limite em carrapatos** (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Ligação de tomada bem sucedida
- **NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IPv4 ou IPv6 do servidor inválido ou inválido
- **NX_NOT_BOUND** (0x24) Tomada não está ligada
- **NX_NOT_CLOSED** (0x35) Tomada não está em estado fechado
- **NX_IN_PROGRESS** (0x37) Não foi especificada qualquer espera, tentativa de ligação está em curso
- **NX_INVALID_INTERFACE** (0x4C) Índice de interface inválido.
- **NX_NO_INTERFACE_ADDRESS** (0x50) A interface de rede não tem endereço IPv6 válido
- **TCP NX_NOT_ENABLED** (0x14) não está habilitado
- **porta** inválida NX_INVALID_PORT (0x46)
- **ponteiro de tomada** inválida NX_PTR_ERROR (0x07)
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço
- **NX_NOT_CONNECTED** (0x38) A ligação falha.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
NXD_ADDRESS peer_ip_address;
ULONG       peer_port;

/* Set Peer IPv6 address */
peer_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
peer_ip_address.nxd_ip_address.v6[0] = 0x20010000;
peer_ip_address.nxd_ip_address.v6[1] = 0;
peer_ip_address.nxd_ip_address.v6[2] = 0;
peer_ip_address.nxd_ip_address.v6[3] = 0x101;

/* Set peer port number */
peer_port = 2563;

/* Connect to the peer */
status = nxd_tcp_client_socket_connect(socket_ptr,
                                       &peer_ip_address,
                                       peer_port, NX_WAIT_FOREVER);
```
### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_socket_peer_info_get

## <a name="nxd_tcp_socket_peer_info_get"></a>nxd_tcp_socket_peer_info_get
Recupera endereço IP da tomada peer TCP e número de porta

### <a name="prototype"></a>Prototype  

```c
UINT nxd_tcp_socket_peer_info_get
    (NX_TCP_SOCKET *socket_ptr,
    NXD_ADDRESS *peer_ip_address,
    ULONG *peer_port);
```
### <a name="description"></a>Descrição

Este serviço recupera o endereço IP e informações de porta para a tomada TCP conectada sobre a rede IPv4 ou IPv6. O serviço NetX IPv4 equivalente é ***nx_tcp_socket_peer_info_get***.

Note que *socket_ptr* deve apontar para uma tomada TCP que já se encontra no estado ligado.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para tomada TCP ligado ao hospedeiro de pares
- **peer_ip_address** Ponteiro para endereço de pares IPv4 ou IPv6. O endereço IP devolvido está na ordem de anfitrião byte.
- **peer_port** Ponteiro para o número da porta de pares. O número de porta devolvido está em ordem de adeus.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Informações de tomadas recuperadas com sucesso
- **NX_NOT_CONNECTED** (0x38) Tomada não ligada ao par
- **TCP NX_NOT_ENABLED** (0x14) não está habilitado
- **NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
NXD_ADDRESS  peer_ip_address;
ULONG        peer_port;

/* Get TCP socket information. */
status = nxd_tcp_socket_peer_info_get(socket_ptr, &peer_ip_address,
                                      &peer_port);

/* If status == NX_SUCCESS, the service returns valid peer info: */
if(peer_ip_address.nxd_ip_version == NX_IP_VERSION_V4)
    /* Peer IP address is stored in
       peer_ip_address.nxd_ip_address.v4 */

if(peer_ip_address.nxd_ip_version == NX_IP_VERSION_V6)
    /* Peer IP address is stored in
       peer_ip_address.nxd_ip_address.v6 */
```
### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect

## <a name="nxd_udp_packet_info_extract"></a>nxd_udp_packet_info_extract
Extrair parâmetros de rede do pacote UDP

### <a name="prototype"></a>Prototype  

```c
UINT nxd_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```
### <a name="description"></a>Descrição

Este serviço extrai parâmetros de rede de um pacote recebido nas redes IPv4 ou IPv6 UDP. O serviço equivalente NetX é ***nx_udp_packet_info_extract.***

### <a name="parameters"></a>Parâmetros

- **packet_ptr** Ponteiro para pacote.
- **ip_address** Ponteiro para o endereço IP remetente.
- **protocolo** Ponteiro para o protocolo a ser devolvido.
- **porto** Ponteiro para o número da porta do remetente.
- **interface_index** Ponteiro para o índice da interface de rede a partir do qual este pacote é recebido

### <a name="return-values"></a>Valores de devolução 

- **NX_SUCCESS** (0x00) dados de interface de pacote extraídos com sucesso.
- **NX_INVALID_PACKET** (0x12) Pacote não é nem IPv4 nem IPv6.
- **NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Extract network data from UDP packet interface.*/
status = nxd_udp_packet_info_extract(packet_ptr, &ip_address,
                                    &protocol, &port,
                                    &interface_index);

/* If status is NX_SUCCESS packet data was successfully retrieved.*/
```
### <a name="see-also"></a>Consulte também 

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nxd_udp_socket_send"></a>nxd_udp_socket_send
Enviar um UDP Datagram

### <a name="prototype"></a>Prototype  

```c
UINT nxd_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address,
    UINT port);
```
### <a name="description"></a>Descrição

Este serviço envia um datagrama de UDP através de uma tomada UDP previamente criada e ligada para redes IPv4 ou IPv6. NetX Duo encontra um endereço IP local adequado como endereço de origem baseado no endereço IP de destino. Para especificar uma interface específica e endereço IP de origem, a aplicação deve utilizar o serviço ***nxd_udp_socket_source_send.***

Note que este serviço retorna imediatamente independentemente de o datagrama da UDP ter sido enviado com sucesso. O serviço equivalente NetX (IPv4) é ***nx_udp_socket_send***.

A tomada deve estar ligada a um porto local.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada UDP previamente criada
- **packet_ptr** Ponteiro do pacote de datagrama da UDP
- **ip_address** Endereço IPv4 ou IPv6 de destino
- **porto** Número de porta de destino válido entre 1 e 0xFFFF), em encomenda byte de anfitrião

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Envio de tomada uDP bem sucedida
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IPv4 ou IPv6 do servidor inválido ou inválido
- **NX_NOT_BOUND** (0x24) Tomada não ligada a nenhuma porta
- **NX_NO_INTERFACE_ADDRESS** (0x50) Não é possível encontrar uma interface de saída adequada.
- **NX_UNDERFLOW** (0x02) Não há espaço suficiente para cabeçalho UDP no pacote
- **NX_OVERFLOW** (0x03) O ponteiro do apêndice do pacote é inválido
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida, ponteiro de endereço ou ponteiro do pacote.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço
- **NX_NOT_ENABLED** (0x14) UDP não foi habilitado
- **NX_INVALID_PORT** (0x46) Número de porta não está dentro de um alcance válido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
NXD_ADDRESS ip_address, server_address;

/* Set the UDP Client IPv6 address. */
ip_address.nxd_ip_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0] = 0x20010000;
ip_address.nxd_ip_address.v6[1] = 0;
ip_address.nxd_ip_address.v6[2] = 0;
ip_address.nxd_ip_address.v6[3] = 1;

/* Set the UDP server IPv6 address to send to. */
server_address.nxd_ip_version = NX_IP_VERSION_V6;
server_address.nxd_ip_address.v6[0] = 0x20010000;
server_address.nxd_ip_address.v6[1] = 0;
server_address.nxd_ip_address.v6[2] = 0;
server_address.nxd_ip_address.v6[3] = 2;

/* Set the global address (indicated by the 64 bit prefix) using the
   IPv6 address just created on the primary device (index 0). We
   don’t need the index into the address table, so the last argument
   is set to null. */

interface_index = 0;
status = nxd_ipv6_address_set(&client_ip, interface_index,
                              &ip_address, 64, NX_NULL);

/* Create the UDP socket client_socket with the ip_address and
   allocate a packet pointed to by packet_ptr (not shown). */

/* Send a packet to the UDP server at server_address on port 12. */
status = nxd_udp_socket_send(&client_socket, packet_ptr,
                             &server_address, 12);

/* If status == NX_SUCCESS, the UDP host successfully transmitted
   the packet out the UDP socket to the server. */
```
### <a name="see-also"></a>Consulte também

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nxd_udp_socket_source_send"></a>nxd_udp_socket_source_send
Enviar um UDP Datagram

### <a name="prototype"></a>Prototype  

```c
UINT nxd_udp_socket_source_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address,
    UINT port, 
    UINT address_index);
```
### <a name="description"></a>Descrição

Este serviço envia um datagrama de UDP através de uma tomada UDP previamente criada e ligada para redes IPv4 ou IPv6. O parâmetro *address_index* especifica o endereço IP de origem a utilizar para o pacote de saída. Note que a função retorna imediatamente independentemente de o datagrama da UDP ter sido enviado com sucesso.

A tomada deve estar ligada a um porto local.

O serviço equivalente NetX (IPv4) é ***nx_udp_socket_source_send***.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada UDP previamente criada
- **packet_ptr** Ponteiro do pacote de datagrama da UDP
- **ip_address** Ponteiro para destino IPv4 ou IPv6 endereço porto de destino número de porta de destino válido entre 1 e 0xFFFF), em encomenda byte anfitrião
- **address_index** Índice especificando o endereço de origem para usar para o pacote

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Envio de tomada uDP bem sucedida
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IPv4 ou IPv6 do servidor inválido ou inválido
- **NX_NOT_BOUND** (0x24) Tomada não ligada a nenhuma porta
- **NX_NO_INTERFACE_ADDRESS** (0x50) Não é possível encontrar uma interface de saída adequada.
- **NX_NOT_FOUND** (0x4E) Não é possível encontrar uma interface adequada
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida, endereço ou ponteiro do pacote.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço
- **NX_NOT_ENABLED** (0x14) UDP não foi habilitado
- **NX_INVALID_PORT** (0x46) O número da porta não está ao alcance válido.
- **NX_INVALID_INTERFACE** (0x4C) Interface de rede especificada é válida
- **NX_UNDERFLOW** (0x02) Não há espaço suficiente para cabeçalho UDP no pacote
- **NX_OVERFLOW** (0x03) O ponteiro do apêndice do pacote é inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
NXD_ADDRESS ip_address, server_address;
UINT address_index;

/* Set the UDP Client IPv6 address. */
ip_address.nxd_ip_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0] = 0x20010000;
ip_address.nxd_ip_address.v6[1] = 0;
ip_address.nxd_ip_address.v6[2] = 0;
ip_address.nxd_ip_address.v6[3] = 1;

/* Set the UDP server IPv6 address to send to. */
server_address.nxd_ip_version = NX_IP_VERSION_V6;
server_address.nxd_ip_address.v6[0] = 0x20010000;
server_address.nxd_ip_address.v6[1] = 0;
server_address.nxd_ip_address.v6[2] = 0;
server_address.nxd_ip_address.v6[3] = 2;

/* Set the global address (indicated by the 64 bit prefix) using the IPv6
   address just created on the primary device (index 0). The address index
   is needed for nxd_udp_socket_source_send. */

status = nxd_ipv6_address_set(&client_ip, 0,
                              &ip_address, 64, &address_index);

/* Create the UDP socket client_socket with the ip_address and
   allocate a packet pointed to by packet_ptr (not shown). */

/* Send a packet to the UDP server at server_address on port 12. */
status = nxd_udp_socket_source_send(&client_socket, packet_ptr,
                                    &server_address, 12, address_index);

/* If status == NX_SUCCESS, the UDP host successfully transmitted the
   packet out the UDP socket to the server. */
```
### <a name="see-also"></a>Consulte também

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_source_extract

## <a name="nxd_udp_source_extract"></a>nxd_udp_source_extract
Recuperar informações de origem de pacotes UPD

### <a name="prototype"></a>Prototype  

```c
UINT nxd_udp_source_extract(
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address, 
    UINT *port);
```
### <a name="description"></a>Descrição

Este serviço extrai o endereço IP de origem e o número de porta de um pacote UDP recebido através da tomada UDP hospedeira. O equivalente NetX (IPv4) é ***nx_udp_source_extract***.

### <a name="parameters"></a>Parâmetros

- **packet_ptr** Ponteiro para receber pacote UDP
- **ip_address** Ponteiro para NXD_ADDRESS estrutura para armazenar endereço IP de origem de pacote
- **porto** Número da porta da tomada UDP

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Extrato de origem bem sucedido
- **NX_INVALID_PACKET** (0x12) Pacote não é válido
- **ponteiro de tomada** inválida NX_PTR_ERROR (0x07)
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
NXD_ADDRESS ip_address;
UINT         port;

/* Create the UDP socket client_socket and
   allocate the packet pointed to by packet_ptr (not shown). */

/* Extract the IP address and port of the packet received on the UDP
   socket specified in the packet interface. */
status = nxd_udp_source_extract(&packet_ptr, &ip_address, &port);

/* If status == NX_SUCCESS, the source IP address and port of the
   packet received on the UDP socket was successfully extracted. */
```
### <a name="see-also"></a>Consulte também

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send