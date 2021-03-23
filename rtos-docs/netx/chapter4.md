---
title: Capítulo 4 - Descrição dos Serviços Azure RTOS NetX
description: Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 720e573b53070a754618830134f63a8421b9fd29
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825640"
---
# <a name="chapter-4---description-of-azure-rtos-netx-services"></a>Capítulo 4 - Descrição dos Serviços Azure RTOS NetX

Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX por ordem alfabética. Os nomes de serviço são projetados para que todos os serviços similares sejam agrupados. Por exemplo, todos os serviços ARP são encontrados no início deste capítulo.

> [!NOTE]
> *Note que uma API de tomada de BSD-Compatible está disponível para código de aplicação legado que não pode tirar o máximo partido da API NetX de alto desempenho. Consulte o Apêndice D para obter mais informações sobre a API da tomada de BSD-Compatible.*

Na secção "Valores de Retorno" de cada descrição, os valores em **BOLD** não são afetados pela opção NX_DISABLE_ERROR_CHECKING utilizada para desativar a verificação de erros da API, enquanto os valores em não-negrito são completamente desativados. As secções "Allowed From" indicam a partir da qual cada serviço NetX pode ser chamado.

## <a name="nx_arp_dynamic_entries_invalidate"></a>nx_arp_dynamic_entries_invalidate

Invalidar todas as entradas dinâmicas na cache ARP

### <a name="prototype"></a>Prototype

```C
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
/* If status is NX_SUCCESS the dynamic ARP entries were successfully invalidated. */
```

### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entry_set, nx_arp_enable, nx_arp_gratuitous_send.
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_dynamic_entry_set"></a>nx_arp_dynamic_entry_set

Definir entrada dinâmica ARP

### <a name="prototype"></a>Prototype

```C
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

```C
/* Setup a dynamic ARP entry on the previously created IP Instance 0. */
status = nx_arp_dynamic_entry_set(&ip_0, IP_ADDRESS(1,2,3,4),
    0x1022, 0x1234);
/* If status is NX_SUCCESS, there is now a dynamic mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    10:22:00:00:12:34. */
```

### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entries_invalidate, nx_arp_enable,
- nx_arp_gratuitous_send, nx_arp_hardware_address_find,
- nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete.
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_enable"></a>nx_arp_enable

Ativa o Protocolo de Resolução de Endereços (ARP).

### <a name="prototype"></a>Prototype

```C
UINT nx_arp_enable(
    NX_IP *ip_ptr, 
    VOID *arp_cache_memory, 
    ULONG arp_cache_size);
```

### <a name="description"></a>Descrição

Este serviço inicializa o componente ARP do NetX para a instância IP específica. A inicialização do ARP inclui a configuração da cache ARP e várias rotinas de processamento ARP necessárias para o envio e receção de mensagens ARP.

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

```C
/* Enable ARP and supply 1024 bytes of ARP cache memory for
    previously created IP Instance ip_0. */
status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
/* If status is NX_SUCCESS, ARP was successfully enabled for this IP instance.*/
```

### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_gratuitous_send, nx_arp_hardware_address_find,
- nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete.
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_gratuitous_send"></a>nx_arp_gratuitous_send

Envie um pedido gratuito de ARP

### <a name="prototype"></a>Prototype

```C
UINT nx_arp_gratuitous_send(
    NX_IP *ip_ptr,
    VOID (*response_handler) (NX_IP *ip_ptr, NX_PACKET *packet_ptr));
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

```C
/* Send gratuitous ARP without any response handler. */
status = nx_arp_gratuitous_send(&ip_0, NX_NULL);

/* If status is NX_SUCCESS the gratuitous ARP was successfully sent. */
```

### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_hardware_address_find, nx_arp_info_get.
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_hardware_address_find"></a>nx_arp_hardware_address_find

Localizar endereço de hardware físico dado um endereço IP

### <a name="prototype"></a>Prototype

```C
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

```C
/* Search for the hardware address associated with the IP address of
    1.2.3.4 in the ARP cache of the previously created IP
    Instance 0. */
status = nx_arp_hardware_address_find(
    &ip_0, 
    IP_ADDRESS(1,2,3,4),
    &physical_msw, 
    &physical_lsw);

/* If status is NX_SUCCESS, the variables physical_msw and
    physical_lsw contain the hardware address.*/
```

### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send, nx_arp_info_get.
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_info_get"></a>nx_arp_info_get

Recuperar informações sobre atividades de ARP

### <a name="prototype"></a>Prototype

```C
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

*Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao autor da chamada.*

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

```C
/* Pickup ARP information for ip_0. */
status = nx_arp_info_get(
    &ip_0, 
    &arp_requests_sent,
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

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_ip_address_find,
- nx_arp_static_entries_delete, nx_arp_static_entry_create,
- nx_arp_static_entry_delete

## <a name="nx_arp_ip_address_find"></a>nx_arp_ip_address_find

Localizar endereço IP dado um endereço físico

### <a name="prototype"></a>Prototype

```C
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

```C
/* Search for the IP address associated with the hardware address of
    0x0:0x01234 in the ARP cache of the previously created IP
    Instance ip_0. */
status = nx_arp_ip_address_find(&ip_0, &ip_address, 0x0, 0x1234);

/* If status is NX_SUCCESS, the variables ip_address contains the
    associated IP address.*/
```

### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_static_entries_delete,nx_arp_static_entry_create
- nx_arp_static_entry_delete

## <a name="nx_arp_static_entries_delete"></a>nx_arp_static_entries_delete

Eliminar todas as entradas estáticas de ARP

### <a name="prototype"></a>Prototype

```C
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

```C
/* Delete all the static ARP entries for IP Instance 0, assuming
    "ip_0" is the NX_IP structure for IP Instance 0. */

status = nx_arp_static_entries_delete(&ip_0);

/* If status is NX_SUCCESS all static ARP entries in the ARP cache
have been deleted. */
```

### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entry_create,
- nx_arp_static_entry_delete

## <a name="nx_arp_static_entry_create"></a>nx_arp_static_entry_create

Criar IP estático para mapeamento de hardware em cache ARP

### <a name="prototype"></a>Prototype

```C
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

```C
/* Create a static ARP entry on the previously created IP
    Instance 0. */

status = nx_arp_static_entry_create(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);

/* If status is NX_SUCCESS, there is now a static mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    00:00:00:00:12:34. */
```

### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_delete

## <a name="nx_arp_static_entry_delete"></a>nx_arp_static_entry_delete

Elimine IP estático para mapeamento de hardware em cache ARP


### <a name="prototype"></a>Prototype

```C
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
- **physical_msw** Top 16 bits (47 - 32) do endereço físico que foi mapeado estáticamente.
- **physical_lsw** Inferior 32 bits (31 - 0) do endereço físico que foi mapeado estáticamente.

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

```C
/* Delete a static ARP entry on the previously created IP
    instance ip_0. */
status = nx_arp_static_entry_delete(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);
/* If status is NX_SUCCESS, the previously created static ARP entry
    was successfully deleted. */
```

### <a name="see-also"></a>Consulte também

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create

## <a name="nx_icmp_enable"></a>nx_icmp_enable

Ativar o Protocolo de Mensagens de Controlo de Internet (ICMP)

### <a name="prototype"></a>Prototype

```C
UINT nx_icmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descrição

Este serviço permite o componente ICMP para a instância IP especificada.
O componente ICMP é responsável pelo tratamento de mensagens de erro da Internet e pedidos e respostas de ping.

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

```C
/* Enable ICMP on the previously created IP Instance ip_0. */
status = nx_icmp_enable(&ip_0);

/* If status is NX_SUCCESS, ICMP is enabled. */
```

### <a name="see-also"></a>Consulte também

- nx_icmp_info_get, nx_icmp_ping

## <a name="nx_icmp_info_get"></a>nx_icmp_info_get

Recuperar informações sobre atividades do ICMP

### <a name="prototype"></a>Prototype

```C
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

*Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao autor da chamada.*

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **pings_sent** Ponteiro para o destino para o número total de pings enviados.
- **ping_timeouts** Ponteiro para o destino para o número total de intervalos de ping.
- **ping_threads_suspended** Ponteiro para o destino do número total de fios suspensos em pedidos de ping.
- **ping_responses_received** Ponteiro para a estinação do número total de respostas de ping recebidas.
- **icmp_checksum_errors** Ponteiro para o destino do número total de erros de verificação ICMP.
- **icmp_unhandled_messages** Ponteiro para a estinação do número total de mensagens ICMP não manuseadas.

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

```C
/* Retrieve ICMP information from previously created IP
    instance ip_0. */
status = nx_icmp_info_get(
    &ip_0, 
    &pings_sent, 
    &ping_timeouts,
    &ping_threads_suspended,
    &ping_responses_received,
    &icmp_checksum_errors,
    &icmp_unhandled_messages);

/* If status is NX_SUCCESS, ICMP information was retrieved. */
```

### <a name="see-also"></a>Consulte também

- nx_icmp_enable, nx_icmp_ping

## <a name="nx_icmp_ping"></a>nx_icmp_ping

Enviar pedido de ping para endereço IP especificado

### <a name="prototype"></a>Prototype

```C
UINT nx_icmp_ping(
    NX_IP *ip_ptr,
    ULONG ip_address,
    CHAR *data, ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Descrição

Este serviço envia um pedido de ping para o endereço IP especificado e aguarda o tempo especificado para uma mensagem de resposta a ping. Se não for recebida qualquer resposta, um erro é devolvido. Caso contrário, toda a mensagem de resposta é devolvida na variável apontada por response_ptr.

*Se NX_SUCCESS for devolvido, o pedido é responsável pela libertação do pacote recebido depois de já não ser necessário.*

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **ip_address** Endereço IP, em ordem de anfitrião byte, para ping. Ponteiro de dados para a área de dados para mensagem de ping.
- **data_size** Número de bytes nos dados do ping
- **response_ptr** Ponteiro para o ponteiro do pacote para devolver a mensagem de resposta do ping dentro
- **wait_option** Define quanto tempo esperar por uma resposta de ping. as opções de espera são definidas da seguinte forma:

  - NX_NO_WAIT (0x00000000)
  - NX_WAIT_FOREVER (0xFFFFFFFF)
  - valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)

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

```C
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

- nx_icmp_enable, nx_icmp_info_get

## <a name="nx_igmp_enable"></a>nx_igmp_enable

Ativar o Protocolo de Gestão do Grupo de Internet (IGMP)

### <a name="prototype"></a>Prototype

```C
UINT nx_igmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descrição

Este serviço permite o componente IGMP na instância IP especificada.
A componente IGMP é responsável por fornecer suporte para operações de gestão de grupos multicast IP.

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

```C
/* Enable IGMP on the previously created IP Instance ip_0. */
status = nx_igmp_enable(&ip_0);

/* If status is NX_SUCCESS, IGMP is enabled. */
```

### <a name="see-also"></a>Consulte também

- nx_igmp_info_get,nx_igmp_loopback_disable
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join.
- nx_igmp_multicast_join, nx_igmp_multicast_leave

## <a name="nx_igmp_info_get"></a>nx_igmp_info_get

Recuperar informações sobre atividades do IGMP

### <a name="prototype"></a>Prototype

```C
UINT nx_igmp_info_get(
    NX_IP *ip_ptr,
    ULONG *igmp_reports_sent,
    ULONG *igmp_queries_received,
    ULONG *igmp_checksum_errors,
    ULONG *current_groups_joined);
```

### <a name="description"></a>Descrição

Este serviço obtém informações sobre as atividades do IGMP para a instância IP especificada.

*Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao autor da chamada.*

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

```C
/* Retrieve IGMP information
    from previously created IP Instance ip_0. */
status = nx_igmp_info_get(
    &ip_0, 
    &igmp_reports_sent,
    &igmp_queries_received,
    &igmp_checksum_errors,
    &current_groups_joined);
/* If status is NX_SUCCESS, IGMP information was retrieved. */
```

### <a name="see-also"></a>Consulte também

- nx_igmp_enable, nx_igmp_loopback_disable,
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join.
- nx_igmp_multicast_join, nx_igmp_multicast_leave

## <a name="nx_igmp_loopback_disable"></a>nx_igmp_loopback_disable

Desativar o loopback IGMP

### <a name="prototype"></a>Prototype

```C
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

```C
/* Disable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_disable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is disabled. */
```

### <a name="see-also"></a>Consulte também

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_enable.
- nx_igmp_multicast_interface_join, nx_igmp_multicast_join.
- nx_igmp_multicast_leave

## <a name="nx_igmp_loopback_enable"></a>nx_igmp_loopback_enable

Ativar o loopback IGMP

### <a name="prototype"></a>Prototype

```C
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

```C
/* Enable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_enable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is enabled. */
```

### <a name="see-also"></a>Consulte também

- nx_igmp_enable, nx_igmp_info_get nx_igmp_loopback_disable
- nx_igmp_multicast_interface_join, nx_igmp_multicast_join.
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_interface_join"></a>nx_igmp_multicast_interface_join

Junte a instância IP a grupo multicast especificado através de uma interface

### <a name="prototype"></a>Prototype

```C
UINT nx_igmp_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```

### <a name="description"></a>Descrição

Este serviço junta-se a uma instância IP ao grupo multicast especificado através de uma interface de rede especificada. Mantém-se um contador interno para acompanhar o número de vezes que o mesmo grupo foi acompanhado. Depois de se juntar ao grupo multicast, o componente IGMP permitirá a receção de pacotes IP com este endereço de grupo através da interface de rede especificada e também reportará aos routers que este IP é membro deste grupo multicast. A adesão ao IGMP junta-se, reporta e deixa as mensagens também são enviadas através da interface de rede especificada.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **group_address** Endereço de grupo multicast classe D IP para se juntar na ordem byte de anfitrião.
- **interface_index** Índice da Interface ligado à instância NetX.

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

```C
/* Previously created IP Instance joins the multicast group
    244.0.0.200, via the interface at index 1 in the IP interface list. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_join
    (&ip, IP_ADDRESS(244,0,0,200),
    INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
    the multicast group. */
```

### <a name="see-also"></a>Consulte também

- nx_igmp_enable, nx_igmp_info_get nx_igmp_loopback_disable
- nx_igmp_loopback_enable, nx_igmp_multicast_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_join"></a>nx_igmp_multicast_join

Junte-se à instância IP para grupo multicast especificado

### <a name="prototype"></a>Prototype

```C
UINT nx_igmp_multicast_join(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a>Descrição

Este serviço junta-se a uma instância IP ao grupo multicast especificado. Mantém-se um contador interno para acompanhar o número de vezes que o mesmo grupo foi acompanhado. O condutor é ordenado a enviar um relatório IGMP se este for o primeiro pedido de junção na rede indicando a intenção do anfitrião de se juntar ao grupo. Após a adesão, o componente IGMP permitirá a receção de pacotes IP com este endereço de grupo e informará aos routers que este IP é membro deste grupo multicast.

> [!NOTE]
> *Para se juntar a um grupo multicast num dispositivo não primário, utilize o **serviço nx_igmp_multicast_interface_join.***

- **Parâmetros**

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

```C
/* Previously created IP Instance ip_0 joins the multicast group
    224.0.0.200. */
status = nx_igmp_multicast_join(&ip_0, IP_ADDRESS(224,0,0,200));

/* If status is NX_SUCCESS, this IP instance has successfully
    joined the multicast group 224.0.0.200. */
```

### <a name="see-also"></a>Consulte também

- nx_igmp_enable, nx_igmp_info_get nx_igmp_loopback_disable
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join.
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_leave"></a>nx_igmp_multicast_leave

Fazer com que a instância IP deixe o grupo multicast especificado

### <a name="prototype"></a>Prototype

```C
UINT nx_igmp_multicast_leave(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a>Descrição

Este serviço faz com que uma instância IP saia do grupo multicast especificado, se o número de pedidos de licença corresponder ao número de pedidos de associação. Caso contrário, a contagem interna de juntas é simplesmente decrementeda.

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

```C
/* Cause IP instance to leave the multicast group 224.0.0.200. */
status = nx_igmp_multicast_leave(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully left
    the multicast group 224.0.0.200. */
```
### <a name="see-also"></a>Consulte também

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable.
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join.
- nx_igmp_multicast_join

## <a name="nx_ip_address_change_notifiy"></a>nx_ip_address_change_notifiy

Notifique a aplicação se o endereço IP mudar


### <a name="prototype"></a>Prototype

```C
UINT nx_ip_address_change_notify(
    NX_IP *ip_ptr,
    VOID(*change_notify)(NX_IP *,VOID *),
    VOID *additional_info);
```

### <a name="description"></a>Descrição

Este serviço regista uma função de notificação de aplicação que é chamada sempre que o endereço IP é alterado.

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

```C
/* Register the function "my_ip_changed" to be called whenever
the IP address is changed. */
status = nx_ip_address_change_notify(&ip_0, my_ip_changed, NX_NULL);

/* If status is NX_SUCCESS, the "my_ip_changed" function will be
    called whenever the IP address changes. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_address_get, nx_ip_address_set, nx_ip_create, nx_ip_delete.
- nx_ip_driver_direct_command, nx_ip_driver_interface_direct_command,
- nx_ip_forwarding_disable, nx_ip_forwarding_enable.
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get.
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_address_get"></a>nx_ip_address_get

Recuperar endereço IP e máscara de rede

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_address_get(
    NX_IP *ip_ptr,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a>Descrição

Este serviço recupera o endereço IP e a sua máscara de sub-rede da interface de rede primária.

*Para obter informações sobre o dispositivo secundário, utilize o serviço
- **nx_ip_interface_address_get**.*

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

```C
/* Get the IP address and network mask from the previously created
    IP Instance ip_0. */
status = nx_ip_address_get(&ip_0,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS, the variables ip_address and
    network_mask contain the IP and network mask respectively. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_address_change_notify, nx_ip_address_set, nx_ip_create.
- nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check.
- nx_system_initialize

## <a name="nx_ip_address_set"></a>nx_ip_address_set

Definir endereço IP e máscara de rede

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_address_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a>Descrição

Este serviço define endereço IP e máscara de rede para a interface de rede primária.

*Para definir o endereço IP e a máscara de rede para o dispositivo secundário, utilize o **nx_ip_interface_address_set** de serviço .*

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

```C
/* Set the IP address and network mask to 1.2.3.4 and 0xFFFFFF00
    for the previously created IP Instance ip_0. */
status = nx_ip_address_set(&ip_0, IP_ADDRESS(1,2,3,4), 0xFFFFFF00UL);

/* If status is NX_SUCCESS, the IP instance now has an IP address
    of 1.2.3.4 and a network mask of 0xFFFFFF00. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_create.
- nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check.
- nx_system_initialize

## <a name="nx_ip_create"></a>nx_ip_create

Criar uma instância IP

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_create(
    NX_IP *ip_ptr, 
    CHAR *name, 
    ULONG ip_address,
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
- **default_pool** Ponteiro para o bloco de controlo da piscina de pacotes NetX previamente criado.
- **ip_network_driver** Controlador de rede fornecido pelo utilizador utilizado para enviar e receber pacotes IP.
- **memory_ptr** Ponteiro para a área de memória para a área de pilha do ajudante IP.
- **memory_size** Número de bytes na área de memória para a pilha do fio do ajudante IP.
- **prioridade** Prioridade do fio do ajudante ip.

### <a name="return-values"></a>Valores de devolução
- **NX_SUCCESS** (0x00) criação de instância IP bem sucedida.
- **NX_NOT_IMPLEMENTED** (0x4A) a biblioteca NetX está configurada incorretamente.
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

```C
/* Create an IP instance with an IP address of 1.2.3.4 and a network
    mask of 0xFFFFFF00UL. The "ethernet_driver" specifies the entry
    point of the application specific network driver and the
    "stack_memory_ptr" specifies the start of a 1024 byte memory
    area that is used for this IP instance’s helper thread.  */
status = nx_ip_create(
    &ip_0, 
    "NetX IP Instance ip_0",
    IP_ADDRESS(1, 2, 3, 4),
    0xFFFFFF00UL, &pool_0, 
    ethernet_driver,
    stack_memory_ptr, 
    1024, 
    1);

/* If status is NX_SUCCESS, the IP instance has been created. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set.
- nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check.
- nx_system_initialize

## <a name="nx_ip_delete"></a>nx_ip_delete

Eliminar instância IP previamente criada


### <a name="prototype"></a>Prototype

```C
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

```C
/* Delete a previously created IP instance. */
status = nx_ip_delete(&ip_0);

/* If status is NX_SUCCESS, the IP instance has been deleted. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set.
- nx_ip_create, nx_ip_driver_direct_command.
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check.
- nx_system_initialize

## <a name="nx_ip_driver_direct_command"></a>nx_ip_driver_direct_command

Emitir comando ao controlador de rede

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_driver_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    ULONG *return_value_ptr);
```

### <a name="description"></a>Descrição

Este serviço fornece uma interface direta ao controlador de interface de rede primária da aplicação especificado durante a ***chamada nx_ip_create.***

Os comandos específicos da aplicação podem ser utilizados desde que o seu valor numérico seja superior ou igual a NX_LINK_USER_COMMAND.

*Para emitir comando para o dispositivo secundário, utilize o serviço **nx_ip_driver_interface_direct_command.***

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

- **Preempção Possível**

No

### <a name="example"></a>Exemplo

```C
/* Make a direct call to the application-specific network driver
    for the previously created IP instance. For this example, the
    network driver is interrogated for the link status. */
status = nx_ip_driver_direct_command(
    &ip_0, NX_LINK_GET_STATUS,
    &link_status);

/* If status is NX_SUCCESS, the link_status variable contains a
    NX_TRUE or NX_FALSE value representing the status of the
    physical link. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set.
- nx_ip_create, nx_ip_delete, nx_ip_driver_interface_direct_command.
- nx_ip_forwarding_disable, nx_ip_forwarding_enable.
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get.
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_driver_interface_direct_command"></a>nx_ip_driver_interface_direct_command

Emitir comando ao controlador de rede

### <a name="prototype"></a>Prototype

```C
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

```C
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

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set.
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command.
- nx_ip_forwarding_disable, nx_ip_forwarding_enable.
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get.
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_forwarding_disable"></a>nx_ip_forwarding_disable

Desativar o encaminhamento do pacote IP

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_forwarding_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descrição

Este serviço desativa o encaminhamento de pacotes IP dentro do componente IP NetX. Na criação da tarefa IP, este serviço é automaticamente desativado.

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

```C
/* Disable IP forwarding on this IP instance. */
status = nx_ip_forwarding_disable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been disabled on the
    previously created IP instance. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set.
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command.
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get.
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_forwarding_enable"></a>nx_ip_forwarding_enable

Ativar o encaminhamento de pacotes IP

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_forwarding_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descrição

Este serviço permite reencaminhar pacotes IP dentro do componente NetX IP. Na criação da tarefa IP, este serviço é automaticamente desativado.

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

```C
/* Enable IP forwarding on this IP instance. */
status = nx_ip_forwarding_enable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set.
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command.
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get.
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_fragment_disable"></a>nx_ip_fragment_disable

Desativar a fragmentação do pacote IP

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_fragment_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descrição

Este serviço desativa a fragmentação e a montagem do pacote IP. Para pacotes à espera de serem remontados, este serviço liberta estes pacotes. Na criação da tarefa IP, este serviço é automaticamente desativado.

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

```C
/* Disable IP fragmenting on this IP instance. */
status = nx_ip_fragment_disable(&ip_0);

/* If status is NX_SUCCESS, disables IP fragmenting on the
    previously created IP instance. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set.
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command.
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_enable, nx_ip_info_get.
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_fragment_enable"></a>nx_ip_fragment_enable

Ativar a fragmentação do pacote IP

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_fragment_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descrição

Este serviço permite a fragmentação e remontagem da funcionalidade do pacote IP. Na criação da tarefa IP, este serviço é automaticamente desativado.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Ativar o fragmento IP bem sucedido.
- **NX_PTR_ERROR** (0x07) Ponteiro IP inválido.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) As características de fragmentação IP não são compiladas no NetX.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```C
/* Enable IP fragmenting on this IP instance. */
status = nx_ip_fragment_enable(&ip_0);

/* If status is NX_SUCCESS, IP fragmenting has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set.
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command.
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable, nx_ip_info_get.
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_gateway_address_set"></a>nx_ip_gateway_address_set

Definir endereço IP gateway

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_gateway_address_set(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```

### <a name="description"></a>Descrição

Este serviço define o endereço IP gateway IP. Todo o tráfego fora da rede é encaminhado para este portal de transmissão. O gateway deve estar diretamente acessível através de uma das interfaces de rede.

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

```C
/* Setup the Gateway address for previously created IP
    Instance ip_0. */
status = nx_ip_gateway_address_set(&ip_0, IP_ADDRESS(1,2,3,99));

/* If status is NX_SUCCESS, all out-of-network send requests are
    routed to 1.2.3.99. */
```
### <a name="see-also"></a>Consulte também

- nx_ip_info_get, nx_ip_static_route_add, nx_ip_static_route_delete

## <a name="nx_ip_info_get"></a>nx_ip_info_get

Recuperar informações sobre atividades ip

### <a name="prototype"></a>Prototype

```C
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

*Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao autor da chamada.*

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

```C
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

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set.
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command.
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_interface_address_get"></a>nx_ip_interface_address_get

Recuperar endereço IP de interface

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_interface_address_get (
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a>Descrição

Este serviço recupera o endereço IP de uma interface de rede especificada.

*O dispositivo especificado, se não o dispositivo primário, deve ser previamente ligado à instância IP.*

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

```C
#define INTERFACE_INDEX 1
/* Get device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_get(ip_ptr,INTERFACE_INDEX,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS the interface address was successfully
    retrieved. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_interface_address_set, nx_ip_interface_attach,
- nx_ip_interface_info_get, nx_ip_interface_status_check,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_address_set"></a>nx_ip_interface_address_set

Definir interface endereço IP e máscara de rede

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a>Descrição

Este serviço define o endereço IP e a máscara de rede para a interface IP especificada.

*A interface especificada deve ser previamente anexada à instância IP.*

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **interface_index** Índice da interface anexa à instância NetX.
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

```C
#define INTERFACE_INDEX 1
/* Set device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_set(ip_ptr, INTERFACE_INDEX,
    ip_address, network_mask);

/* If status is NX_SUCCESS the interface IP address and mask was
successfully set. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_interface_address_get, nx_ip_interface_attach,
- nx_ip_interface_info_get, nx_ip_interface_status_check,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_attach"></a>nx_ip_interface_attach

Anexar interface de rede à instância IP

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_interface_attach(
    NX_IP *ip_ptr, 
    CHAR *interface_name,
    ULONG ip_address,
    ULONG network_mask,
    VOID(*ip_link_driver)
    (struct NX_IP_DRIVER_STRUCT *));
```

### <a name="description"></a>Descrição

Este serviço adiciona uma interface de rede física à interface IP. Note que a instância IP é criada com a interface primária para que cada interface adicional seja secundária à interface primária. O número total de interfaces de rede anexas à instância IP (incluindo a interface primária) não pode exceder **NX_MAX_PHYSICAL_INTERFACES**.

Se o fio IP ainda não estiver em funcionamento, as interfaces secundárias serão inicializadas como parte do processo de arranque do fio IP que inicializa todas as interfaces físicas.

Se a linha IP ainda não estiver em funcionamento, a interface secundária é inicializada como parte do serviço ***nx_ip_interface_attach.***

*ip_ptr deve apontar para uma estrutura DE IP NetX válida.*

- ***NX_MAX_PHYSICAL_INTERFACES** devem ser configurados para o número de interfaces de rede para a instância IP. O valor predefinido é um.*

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **interface_name** Ponteiro para interface linha nome.
- **ip_address** Endereço IP do dispositivo na ordem byte anfitrião.
- **network_mask** Máscara de rede do dispositivo na ordem byte hospedeiro.
- **ip_link_driver** Controlador Ethernet para a interface.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) A entrada é adicionada à mesa de encaminhamento estática.
- **NX_NO_MORE_ENTRIES** (0x17) Número máximo de interfaces.
- **NX_MAX_PHYSICAL_INTERFACES** é excedido.
- **NX_DUPLICATED_ENTRY** (0x52) O endereço IP fornecido já é utilizado neste caso IP.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro.
- **NX_IP_ADDRESS_ERROR** (0x21) Entrada de endereço IP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```C
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

- nx_ip_interface_address_get, nx_ip_interface_address_set,
- nx_ip_interface_info_get, nx_ip_interface_status_check,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_info_get"></a>nx_ip_interface_info_get

Recuperar parâmetros de interface de rede


### <a name="prototype"></a>Prototype

```C
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

*ip_ptr deve apontar para uma estrutura DE IP NetX válida. A interface especificada, se não a interface primária, deve ser previamente anexada à instância IP.*

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

```C
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

- nx_ip_interface_address_get, nx_ip_interface_address_set,
- nx_ip_interface_attach, nx_ip_interface_status_check.
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_status_check"></a>nx_ip_interface_status_check

Verificar o estado de verificação de uma instância IP


### <a name="prototype"></a>Prototype

```C
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
- **interface_index** Número do índice de interface
- **needed_status** Estado ip solicitado, definido no formulário bit-mape da seguinte forma:
    - NX_IP_INITIALIZE_DONE (0x0001)
    - NX_IP_ADDRESS_RESOLVED (0x0002)
    - NX_IP_LINK_ENABLED (0x0004)
    - NX_IP_ARP_ENABLED (0x0008)
    - NX_IP_UDP_ENABLED (0x0010)
    - NX_IP_TCP_ENABLED (0x0020)
    - NX_IP_IGMP_ENABLED (0x0040)
    - NX_IP_RARP_COMPLETE (0x0080)
    - NX_IP_INTERFACE_LINK_ENABLED (0x0100)
- **atual_status** Ponteiro para o destino de bits reais definido.
- **wait_option** Define como o serviço se comporta se as bits de estado solicitados não estiverem disponíveis. As opções de espera são definidas da seguinte forma:
    - NX_NO_WAIT (0x00000000)
    - NX_WAIT_FOREVER (0xFFFFFFFF)
    - valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)

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

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the secondary link for the specified IP
    instance is up. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_interface_address_get, nx_ip_interface_address_set,
- nx_ip_interface_attach, nx_ip_interface_info_get,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_link_status_change_notify_set"></a>nx_ip_link_status_change_notify_set

Desa um conjunto de alterações de estado de ligação notifique a função de retorno de chamadas

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_link_status_change_notify_set(
    NX_IP *ip_ptr,
    VOID (*link_status_change_notify)(NX_IP *ip_ptr, UINT interface_index, UINT link_up));
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

```C
/* Configure a callback function to be used when the physical
    interface status is changed. */
status = nx_ip_link_status_change_notify_set(&ip_0, my_change_cb);

/* If status == NX_SUCCESS, the link status change notify function
    is set. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_interface_address_get, nx_ip_interface_address_set,
- nx_ip_interface_attach, nx_ip_interface_info_get,
- nx_ip_interface_status_check

## <a name="nx_ip_raw_packet_disable"></a>nx_ip_raw_packet_disable

Desativar o envio/receção de pacotes brutos


### <a name="prototype"></a>Prototype

```C
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

```C
/* Disable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_disable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been disabled for the previously created IP instance. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_raw_packet_enable, nx_ip_raw_packet_receive,
- nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send

## <a name="nx_ip_raw_packet_enable"></a>nx_ip_raw_packet_enable

Permitir o processamento de pacotes crus


### <a name="prototype"></a>Prototype

```C
UINT nx_ip_raw_packet_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descrição

Este serviço permite a transmissão e receção de pacotes IP crus para este caso IP. Os pacotes de TCP, UDP, ICMP e IGMP ainda são processados pela NetX. Pacotes com tipos de protocolo de camada superior desconhecida são processados pela rotina de receção de pacotes crus.

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

```C
/* Enable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_enable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been enabled for the previously created IP instance. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_raw_packet_disable, nx_ip_raw_packet_receive,
- nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send

## <a name="nx_ip_raw_packet_interface_send"></a>nx_ip_raw_packet_interface_send

Enviar pacote IP cru através de interface de rede especificada

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_raw_packet_interface_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    UINT address_index,
    ULONG type_of_service);
```

### <a name="description"></a>Descrição

Este serviço envia um pacote IP bruto para o endereço IP de destino usando o endereço IP local especificado como endereço de origem, e através da interface de rede associada. Note que esta rotina retorna imediatamente, e não é, portanto, conhecido se o pacote IP foi realmente enviado. O controlador de rede será responsável pela libertação do pacote quando a transmissão estiver completa. Este serviço difere de outros serviços na medida em que não há forma de saber se o pacote foi realmente enviado. Pode perder-se na Internet.

*Note que o processamento de IP bruto deve ser ativado.*

*Este serviço é semelhante ao **nx_ip_raw_packet_send,** exceto que este serviço permite que uma aplicação envie pacote IP cru a partir de interfaces físicas especificadas.*

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

```C
#define ADDRESS_IDNEX 1
/* Send packet out on interface 1 with normal type of service. */
status = nx_ip_raw_packet_interface_send(ip_ptr, packet_ptr,
    destination_ip,
    ADDRESS_INDEX,
    NX_IP_NORMAL);
/* If status is NX_SUCCESS the packet was successfully transmitted. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,
- nx_ip_raw_packet_receive, nx_ip_raw_packet_send

## <a name="nx_ip_raw_packet_receive"></a>nx_ip_raw_packet_receive

Receba pacote IP cru

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_raw_packet_receive(
    NX_IP *ip_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Descrição

Este serviço recebe um pacote IP cru a partir da instância IP especificada. Se houver pacotes IP na fila de receção de pacotes brutos, o primeiro pacote (mais antigo) é devolvido ao chamador. Caso contrário, se não houver pacotes disponíveis, o chamador pode suspender conforme especificado pela opção de espera.

*Se NX_SUCCESS, for devolvido, o pedido é responsável pela libertação do pacote recebido quando já não for necessário.*

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **packet_ptr** Ponteiro para o ponteiro para colocar o pacote IP bruto recebido dentro
- **wait_option** Define como o serviço se comporta se não houver pacotes IP crus disponíveis. As opções de espera são definidas da seguinte forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)

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

```C
/* Receive a raw IP packet for this IP instance, wait for a maximum
    of 4 timer ticks. */
status = nx_ip_raw_packet_receive(&ip_0, &packet_ptr, 4);

/* If status is NX_SUCCESS, the raw IP packet pointer is in the
    variable packet_ptr. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,
- nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send

## <a name="nx_ip_raw_packet_send"></a>nx_ip_raw_packet_send

Enviar pacote IP cru

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_raw_packet_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    ULONG type_of_service);
```

### <a name="description"></a>Descrição

Este serviço envia um pacote IP cru para o endereço IP destino. Note que esta rotina retorna imediatamente, pelo que não se sabe se o pacote IP foi efetivamente enviado. O controlador de rede será responsável pela libertação do pacote quando a transmissão estiver completa.

Para um sistema multihome, o NetX utiliza o endereço IP de destino para encontrar uma interface de rede apropriada e utiliza o endereço IP da interface como endereço de origem. Se o endereço IP de destino for transmitido ou multicast, a primeira interface válida é utilizada. As aplicações utilizam o ***nx_ip_raw_packet_interface_send*** neste caso.

*A menos que um erro seja devolvido, o pedido não deve libertar o pacote após esta chamada. Ao fazê-lo, o controlador da rede libertará o pacote após a transmissão.*

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **packet_ptr** Ponteiro para o pacote IP cru para enviar.
- **destination_ip** Endereço IP de destino, que pode ser um endereço IP de anfitrião específico, uma transmissão de rede, um loop-back interno ou um endereço multicast.
- **type_of_service** Define o tipo de serviço para a transmissão, os valores legais são os seguintes:
- NX_IP_NORMAL (0x00000000)
- NX_IP_MIN_DELAY (0x00100000)
- NX_IP_MAX_DATA (0x00080000)
- NX_IP_MAX_RELIABLE (0x00040000)
- NX_IP_MIN_COST (0x00020000)


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

```C
/* Send a raw IP packet to IP address 1.2.3.5. */
status = nx_ip_raw_packet_send(&ip_0, packet_ptr,
    IP_ADDRESS(1,2,3,5),
    NX_IP_NORMAL);

/* If status is NX_SUCCESS, the raw IP packet pointed to by
    packet_ptr has been sent. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,
- nx_ip_raw_packet_receive, nx_ip_raw_packet_send,
- nx_ip_raw_packet_interface_send

## <a name="nx_ip_static_route_add"></a>nx_ip_static_route_add

Adicione rota estática à mesa de encaminhamento

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_static_route_add(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask,
    ULONG next_hop);
```

### <a name="description"></a>Descrição

Este serviço adiciona uma entrada na tabela de encaminhamento estático. Note que o endereço *next_hop* deve estar diretamente acessível a partir de um dos dispositivos de rede locais.

*Note que ip_ptr deve apontar para uma estrutura CÓP NetX válida e a biblioteca NetX deve ser construída com NX_ENABLE_IP_STATIC_ROUTING definida para utilizar este serviço. Por padrão, o NetX é construído sem NX_ENABLE_IP_STATIC_ROUTING definido.*

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

```C
/* Specify the next hop for the 192.168.10.0 through the gateway
    192.168.1.1. */
status = nx_ip_static_route_add(ip_ptr, IP_ADDRESS(192,168,10,0),
    0xFFFFFF00UL,
    IP_ADDRESS(192,168,1,1));

/* If status is NX_SUCCESS the route was successfully added to the
    static routing table. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_delete

## <a name="nx_ip_static_route_delete"></a>nx_ip_static_route_delete

Eliminar rota estática da mesa de encaminhamento

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_static_route_delete(
    NX_IP *ip_ptr,
    ULONG network_address, 
    ULONG net_mask);
```

### <a name="description"></a>Descrição

Este serviço elimina uma entrada da tabela de encaminhamento estático.

*Note que ip_ptr deve apontar para uma estrutura CÓP NetX válida e a biblioteca NetX deve ser construída com NX_ENABLE_IP_STATIC_ROUTING definida para utilizar este serviço. Por padrão, o NetX é construído sem NX_ENABLE_IP_STATIC_ROUTING definido.*

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **network_address** Endereço de rede de destino, em ordem byte anfitrião.
- **net_mask** Máscara de rede de alvo, em ordem byte de anfitrião.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```C
/* Remove the static route for 192.168.10.0 from the routing table.*/
status = nx_ip_static_route_delete(ip_ptr,
    IP_ADDRESS(192,168,10,0), 0xFFFFFF00UL,);

/* If status is NX_SUCCESS the route was successfully removed from
    the static routing table. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_add

## <a name="nx_ip_status_check"></a>nx_ip_status_check

Verificar o estado de verificação de uma instância IP

### <a name="prototype"></a>Prototype

```C
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
- NX_IP_INITIALIZE_DONE (0x0001)
- NX_IP_ADDRESS_RESOLVED (0x0002)
- NX_IP_LINK_ENABLED (0x0004)
- NX_IP_ARP_ENABLED (0x0008)
- NX_IP_UDP_ENABLED (0x0010)
- NX_IP_TCP_ENABLED (0x0020)
- NX_IP_IGMP_ENABLED (0x0040)
- NX_IP_RARP_COMPLETE (0x0080)
- NX_IP_INTERFACE_LINK_ENABLED (0x0100)
- **atual_status** Ponteiro para o destino de bits reais definido.
- **wait_option** Define como o serviço se comporta se as bits de estado solicitados não estiverem disponíveis. As opções de espera são definidas da seguinte forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)

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

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_status_check(&ip_0, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the link for the specified IP instance
    is up. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set.
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command.
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_system_initialize

## <a name="nx_packet_allocate"></a>nx_packet_allocate

Alocar pacote a partir de piscina especificada

### <a name="prototype"></a>Prototype

```C
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
- **packet_type** Define o tipo de pacote solicitado. Consulte "Packet Pools" na página 49 do Capítulo 3 para obter uma lista de tipos de pacotes suportados.
- **wait_option** Define o tempo de espera em carrapatos se não houver pacotes disponíveis na piscina de pacotes. As opções de espera são definidas da seguinte forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Atribuição de pacotes bem sucedidos.
- **NX_NO_PACKET** (0x01) Nenhum pacote disponível.
- **NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.
- **NX_INVALID_PARAMETERS** (0x4D) O tamanho do pacote não pode suportar o protocolo.
- **NX_OPTION_ERROR** (0x0A) Tipo de pacote inválido.
- **NX_PTR_ERROR** (0x07) Ponteiro de retorno de piscina ou pacote.
- **NX_CALLER_ERROR** (0x11) Opção de espera inválida de não-leitura.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs (controladores de rede de aplicações). A opção de espera deve ser NX_NO_WAIT quando utilizada no contexto ISR ou no temporizador.

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```C
/* Allocate a new UDP packet from the previously created packet pool
    and suspend for a maximum of 5 timer ticks if the pool is
    empty. */
status = nx_packet_allocate(&pool_0, &packet_ptr, NX_UDP_PACKET, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is
    found in the variable packet_ptr. */
```

### <a name="see-also"></a>Consulte também

- nx_packet_copy, nx_packet_data_append.
- nx_packet_data_extract_offset, nx_packet_data_retrieve.
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete.
- nx_packet_pool_info_get, nx_packet_release.
- nx_packet_transmit_release

## <a name="nx_packet_copy"></a>nx_packet_copy

Pacote de cópia

### <a name="prototype"></a>Prototype

```C
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
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)

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

```C
NX_PACKET *new_copy_ptr;

/* Copy packet pointed to by "old_packet_ptr" using packets from
    previously created packet pool_0. */
status = nx_packet_copy(old_packet, &new_copy_ptr, &pool_0, 20);

/* If status is NX_SUCCESS, new_copy_ptr points to the packet copy. */
```

### <a name="see-also"></a>Consulte também

- nx_packet_allocate, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve.
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete.
- nx_packet_pool_info_get, nx_packet_release.
- nx_packet_transmit_release

## <a name="nx_packet_data_append"></a>nx_packet_data_append

Dados do apêndice ao fim do pacote

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_data_append(
    NX_PACKET *packet_ptr,
    VOID *data_start, 
    ULONG data_size,
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
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Pacote de sucesso.
- **NX_NO_PACKET** (0x01) Nenhum pacote disponível.
- **NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para *tx_thread_wait_abort*.
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

```C
/* Append "abcd" to the specified packet. */
status = nx_packet_data_append(packet_ptr, "abcd", 4, &pool_0, 5);

/* If status is NX_SUCCESS, the additional four bytes "abcd" have
    been appended to the packet. */
```


### <a name="see-also"></a>Consulte também

- nx_packet_allocate, nx_packet_copy, nx_packet_data_extract_offset.
- nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create.
- nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release.
- nx_packet_transmit_release

## <a name="nx_packet_data_extract_offset"></a>nx_packet_data_extract_offset

Extrair dados do pacote através de uma compensação

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_data_extract_offset(
    NX_PACKET *packet_ptr,
    ULONG offset,
    VOID *buffer_start,
    ULONG buffer_length,
    ULONG *bytes_copied);
```

### <a name="description"></a>Descrição

Este serviço copia dados de um pacote NetX (ou cadeia de pacotes) a partir da compensação especificada do ponteiro pré-conjunto do pacote do tamanho especificado em bytes no tampão especificado. O número de bytes copiados é devolvido em *bytes_copied.* Este serviço não remove dados do pacote, nem ajusta o ponteiro pré-conjunto ou outras informações internas do estado.

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

### <a name="example"></a>Exemplo

```C
/* Extract 10 bytes from the start of the received packet buffer
    into the specified memory area. */
status = nx_packet_data_extract_offset(my_packet, 0, &data[0], 10,
    &bytes_copied);

/* If status is NX_SUCCESS, 10 bytes were successfully copied into
    the data buffer. */
```

### <a name="see-also"></a>Consulte também

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append.
- nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create.
- nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release.
- nx_packet_transmit_release

## <a name="nx_packet_data_retrieve"></a>nx_packet_data_retrieve

Recuperar dados do pacote

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_data_retrieve(
    NX_PACKET *packet_ptr,
    VOID *buffer_start, 
    ULONG *bytes_copied);
```

### <a name="description"></a>Descrição

Este serviço copia os dados do pacote fornecido no tampão fornecido. O número real de bytes copiados é devolvido no destino apontado por **bytes_copied**.

Note que este serviço não altera o estado interno do pacote. Os dados que estão a ser recuperados ainda estão disponíveis no pacote.

*O tampão de destino deve ser grande o suficiente para manter o conteúdo do pacote. Caso contrário, a memória será corrompida causando resultados imprevisíveis.*

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

```C
UCHAR buffer[512];
ULONG bytes_copied;

/* Retrieve data from packet pointed to by "packet_ptr". */
status = nx_packet_data_retrieve(packet_ptr, buffer, &bytes_copied);

/* If status is NX_SUCCESS, buffer contains the contents of the
    packet, the size of which is contained in "bytes_copied." */
```

### <a name="see-also"></a>Consulte também

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append.
- nx_packet_data_extract_offset, nx_packet_length_get,
- nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release.
- nx_packet_transmit_release

## <a name="nx_packet_length_get"></a>nx_packet_length_get

Obtenha o comprimento dos dados do pacote

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_length_get(
    NX_PACKET *packet_ptr, 
    ULONG *length);
```

### <a name="description"></a>Descrição

Este serviço obtém o comprimento dos dados no pacote especificado.

### <a name="parameters"></a>Parâmetros

- **packet_ptr** Ponteiro para o pacote.
- **comprimento** Destino para o comprimento do pacote.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```C
/* Get the length of the data in "my_packet." */
status = nx_packet_length_get(my_packet, &my_length);

/* If status is NX_SUCCESS, data length is in "my_length". */
```

### <a name="see-also"></a>Consulte também

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append.
- nx_packet_data_extract_offset, nx_packet_data_retrieve.
- nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release.
- nx_packet_transmit_release

## <a name="nx_packet_pool_create"></a>nx_packet_pool_create

Criar piscina de pacotes na área de memória especificada

### <a name="prototype"></a>Prototype

```C
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

```C
/* Create a packet pool of 32000 bytes starting at physical
    address 0x10000000. */
status = nx_packet_pool_create(&pool_0, "Default Pool", 128,
    (void *) 0x10000000, 32000);

/* If status is NX_SUCCESS, the packet pool has been successfully
    created. */
```

### <a name="see-also"></a>Consulte também

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append.
- nx_packet_data_extract_offset, nx_packet_data_retrieve.
- nx_packet_length_get, nx_packet_pool_delete, nx_packet_pool_info_get.
- nx_packet_release, nx_packet_transmit_release

## <a name="nx_packet_pool_delete"></a>nx_packet_pool_delete

Eliminar piscina de pacotes previamente criada

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_pool_delete(NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Descrição

Este serviço elimina uma piscina de pacotes previamente criada. NetX verifica quaisquer fios atualmente suspensos em pacotes na piscina de pacotes e limpa a suspensão.

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

```C
/* Delete a previously created packet pool. */
status = nx_packet_pool_delete(&pool_0);

/* If status is NX_SUCCESS, the packet pool has been successfully
    deleted. */
```

### <a name="see-also"></a>Consulte também

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append.
- nx_packet_data_extract_offset, nx_packet_data_retrieve.
- nx_packet_length_get, nx_packet_pool_create.
- nx_packet_pool_info_get, nx_packet_release.
- nx_packet_transmit_release

## <a name="nx_packet_pool_info_get"></a>nx_packet_pool_info_get

Recuperar informações sobre uma piscina de pacotes

### <a name="prototype"></a>Prototype

```C
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

*Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao autor da chamada.*

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

```C
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

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append.
- nx_packet_data_extract_offset, nx_packet_data_retrieve.
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete
- nx_packet_release, nx_packet_transmit_release

## <a name="nx_packet_release"></a>nx_packet_release

Liberação pacote previamente atribuído

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a>Descrição

Este serviço liberta um pacote, incluindo quaisquer pacotes adicionais acorrentados ao pacote especificado. Se outro fio for bloqueado na atribuição do pacote, é dado o pacote e retomado.

*O pedido deve impedir a libertação de um pacote mais de uma vez, porque fazê-lo irá causar resultados imprevisíveis.*

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

```C
/* Release a previously allocated packet. */
status = nx_packet_release(packet_ptr);

/* If status is NX_SUCCESS, the packet has been returned to the
    packet pool it was allocated from. */
```

### <a name="see-also"></a>Consulte também

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append.
- nx_packet_data_extract_offset, nx_packet_data_retrieve.
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete.
- nx_packet_pool_info_get, nx_packet_transmit_release

## <a name="nx_packet_transmit_release"></a>nx_packet_transmit_release

Liberte um pacote transmitido

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_transmit_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a>Descrição

Para pacotes não TCP, este serviço liberta um pacote transmitido, incluindo quaisquer pacotes adicionais acorrentados ao pacote especificado. Se outro fio for bloqueado na atribuição do pacote, é dado o pacote e retomado. Para um pacote TCP transmitido, o pacote é marcado como sendo transmitido, mas não libertado até que o pacote seja reconhecido. Este serviço é normalmente chamado do controlador de rede da aplicação após a transmissão de um pacote.

*O controlador de rede deve remover o cabeçalho dos meios de comunicação físicos e ajustar o comprimento do pacote antes de ligar para este serviço.*

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

```C
/* Release a previously allocated packet that was just transmitted
    from the application network driver. */
status = nx_packet_transmit_release(packet_ptr);

/* If status is NX_SUCCESS, the transmitted packet has been
    returned to the packet pool it was allocated from. */
```

### <a name="see-also"></a>Consulte também

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append.
- nx_packet_data_extract_offset, nx_packet_data_retrieve.
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete.
- nx_packet_pool_info_get, nx_packet_release

## <a name="nx_rarp_disable"></a>nx_rarp_disable

Desativar o Protocolo de Resolução de Endereços Reversos (RARP)

### <a name="prototype"></a>Prototype

```C
UINT nx_rarp_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descrição

Este serviço desativa o componente RARP do NetX para a instância IP específica. Para um sistema multihome, este serviço desativa o RARP em todas as interfaces.

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

```C
/* Disable RARP on the previously created IP instance. */
status = nx_rarp_disable(&ip_0);

/* If status is NX_SUCCESS, RARP is disabled. */
```

### <a name="see-also"></a>Consulte também

- nx_rarp_enable, nx_rarp_info_get

## <a name="nx_rarp_enable"></a>nx_rarp_enable

Ativar o Protocolo de Resolução de Endereços Reversos (RARP)

### <a name="prototype"></a>Prototype

```C
UINT nx_rarp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descrição

Este serviço permite o componente RARP do NetX para a instância IP específica. Os componentes RARP procuram através de todas as interfaces de rede anexas para um endereço IP zero. Um endereço IP zero indica que a interface ainda não tem a atribuição de endereço IP. A RARP tenta resolver o endereço IP, permitindo o processo RARP nessa interface.

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

```C
/* Enable RARP on the previously created IP instance. */
status = nx_rarp_enable(&ip_0);

/* If status is NX_SUCCESS, RARP is enabled and is attempting to
    resolve this IP instance’s address by querying the network. */
```

### <a name="see-also"></a>Consulte também

- nx_rarp_disable, nx_rarp_info_get

## <a name="nx_rarp_info_get"></a>nx_rarp_info_get

Recuperar informações sobre as atividades da RARP

### <a name="prototype"></a>Prototype

```C
UINT nx_rarp_info_get(
    NX_IP *ip_ptr,
    ULONG *rarp_requests_sent,
    ULONG *rarp_responses_received,
    ULONG *rarp_invalid_messages);
```

### <a name="description"></a>Descrição

Este serviço obtém informações sobre as atividades da RARP para a instância IP especificada.

*Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao autor da chamada.*

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

```C
/* Retrieve RARP information from previously created IP
    Instance 0. */
status = nx_rarp_info_get(&ip_0,
    &rarp_requests_sent,
    &rarp_responses_received,
    &rarp_invalid_messages);

/* If status is NX_SUCCESS, RARP information was retrieved. */
```

### <a name="see-also"></a>Consulte também

- nx_rarp_disable, nx_rarp_enable

## <a name="nx_system_initialize"></a>nx_system_initialize

Inicializar o Sistema NetX

### <a name="prototype"></a>Prototype

```C
VOID nx_system_initialize(VOID);
```

### <a name="description"></a>Descrição

Este serviço inicializa os recursos básicos do sistema NetX em preparação para utilização. Deve ser chamado pela aplicação durante a inicialização e antes de qualquer outra chamada NetX ser feita.

### <a name="parameters"></a>Parâmetros

Nenhum

### <a name="return-values"></a>Valores de devolução

Nenhum

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores, ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```C
/* Initialize NetX for operation. */
nx_system_initialize();

/* At this point, NetX is ready for IP creation and all subsequent
    network operations. */
```

### <a name="see-also"></a>Consulte também

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set.
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command.
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check

## <a name="nx_tcp_client_socket_bind"></a>nx_tcp_client_socket_bind

Ligação da tomada TCP do cliente à porta TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_client_socket_bind(
    NX_TCP_SOCKET *socket_ptr,
    UINT port, ULONG wait_option);
```

### <a name="description"></a>Descrição

Este serviço liga a tomada do cliente TCP previamente criada à porta TCP especificada. As tomadas TCP válidas variam de 0 a 0xFFFF. Se a porta TCP especificada não estiver disponível, o serviço suspende de acordo com a opção de espera fornecida.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada TCP previamente criada.
- **porto** Número da porta para ligar (1 a 0xFFFF). Se o número da porta for NX_ANY_PORT (0x0000), a instância IP procurará a próxima porta livre e usará-a para a encadernação.
- **wait_option** Define como o serviço se comporta se a porta já está ligada a outra tomada. As opções de espera são definidas da seguinte forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Ligação de tomada bem sucedida.
- **NX_ALREADY_BOUND** (0x22) Esta tomada já está ligada a outra porta TCP.
- **NX_PORT_UNAVAILABLE** (0x23) O porto já está ligado a uma tomada diferente.
- **NX_NO_FREE_PORTS** (0x45) Não há porta livre.
- **NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para *tx_thread_wait_abort*.
- **porta NX_INVALID_PORT** (0x46) Inválida.
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```C
/* Bind a previously created client socket to port 12 and wait for 7
    timer ticks for the bind to complete. */
status = nx_tcp_client_socket_bind(&client_socket, 12, 7);

/* If status is NX_SUCCESS, the previously created client_socket is
    bound to port 12 on the associated IP instance. */
```

### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_connect, nx_tcp_client_socket_port_get,
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten.
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect.
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_connect"></a>nx_tcp_client_socket_connect

Ligue a tomada TCP do cliente

### <a name="prototype"></a>Prototype

```C
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
- **server_port** Número da porta do servidor para ligar (1 a 0xFFFF).
- **wait_option** Define como o serviço se comporta enquanto a ligação está sendo estabelecida. As opções de espera são definidas da seguinte forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)

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

```C
/* Initiate a TCP connection from a previously created and bound
    client socket. The connection requested in this example is to
    port 12 on the server with the IP address of 1.2.3.5. This
    service will wait 300 timer ticks for the connection to take
    place before giving up. */
status = nx_tcp_client_socket_connect(&client_socket,
    IP_ADDRESS(1,2,3,5), 12, 300);

/* If status is NX_SUCCESS, the previously created and bound
    client_socket is connected to port 12 on IP 1.2.3.5. */
```

### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind, nx_tcp_client_socket_port_get,
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten.
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect.
- nx_tcp_socket_info_get, nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_port_get"></a>nx_tcp_client_socket_port_get

Obtenha o número da porta vinculado à tomada TCP do cliente

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_client_socket_port_get(
    NX_TCP_SOCKET *socket_ptr,
    UINT *port_ptr);
```

### <a name="description"></a>Descrição

Este serviço recupera o número de porta associado à tomada, o que é útil para encontrar a porta atribuída pela NetX em situações em que o NX_ANY_PORT foi especificado no momento em que a tomada foi ligada.

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

```C
/* Get the port number of previously created and bound client
    socket. */
status = nx_tcp_client_socket_port_get(&client_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten.
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect.
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_unbind"></a>nx_tcp_client_socket_unbind

Tomada de cliente unbind TCP da porta TCP

### <a name="prototype"></a>Prototype

```C
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

```C
/* Unbind a previously created and bound client TCP socket. */
status = nx_tcp_client_socket_unbind(&client_socket);

/* If status is NX_SUCCESS, the client socket is no longer
    bound. */
```

### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.
- nx_tcp_client_socket_port_get, nx_tcp_enable, nx_tcp_free_port_find.
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten.
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect.
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.
- nx_tcp_socket_state_wait

## <a name="nx_tcp_enable"></a>nx_tcp_enable

Ativar o componente TCP do NetX

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descrição

Este serviço permite o componente do Protocolo de Controlo de Transmissão (TCP) do NetX. Após ativação, as ligações TCP podem ser estabelecidas pelo pedido.

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

```C
/* Enable TCP on a previously created IP instance ip_0. */
status = nx_tcp_enable(&ip_0);

/* If status is NX_SUCCESS, TCP is enabled on the IP instance. */
```

### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept.
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten.
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect.
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.
- nx_tcp_socket_state_wait

## <a name="nx_tcp_free_port_find"></a>nx_tcp_free_port_find

Encontre a próxima porta TCP disponível

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_free_port_find(
    NX_IP *ip_ptr,
    UINT port, UINT *free_port_ptr);
```

### <a name="description"></a>Descrição

Este serviço tenta localizar uma porta TCP gratuita (desvinculada) a partir da porta fornecida pela aplicação. A lógica de pesquisa irá envolver-se se a pesquisa atingir o valor máximo da porta de 0xFFFF. Se a pesquisa for bem sucedida, a porta livre é devolvida na variável apontada por *free_port_ptr*.

*Este serviço pode ser chamado de outro fio e ter a mesma porta devolvida. Para evitar esta condição de regata, a aplicação pode pretender colocar este serviço e a tomada do cliente em si liga-se sob a proteção de um mutex.*

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

```C
/* Locate a free TCP port, starting at port 12, on a previously
    created IP instance. */
status = nx_tcp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS, "free_port" contains the next free port
    on the IP instance. */
```

### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_info_get, nx_tcp_server_socket_accept.
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten.
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect.
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.
- nx_tcp_socket_state_wait

## <a name="nx_tcp_info_get"></a>nx_tcp_info_get

Recuperar informações sobre atividades da TCP

### <a name="prototype"></a>Prototype

```C
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

*Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao autor da chamada.*

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

```C
/* Retrieve TCP information from previously created IP Instance ip_0. */
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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_server_socket_accept.
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten.
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect.
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_accept"></a>nx_tcp_server_socket_accept

Aceitar ligação TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_server_socket_accept(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Descrição

Este serviço aceita (ou prepara-se para aceitar) um pedido de ligação ao cliente TCP para uma porta previamente configurada para escuta. Este serviço pode ser chamado imediatamente após a aplicação chamar o serviço de escuta ou de re-escuta, ou depois de a rotina de chamada de escuta ser chamada quando a ligação do cliente estiver realmente presente. Se uma ligação não puder ser estabelecida imediatamente, o serviço suspende de acordo com a opção de espera fornecida.

*A aplicação deve ligar **nx_tcp_server_socket_unaccept** depois de a ligação já não ser necessária para remover a ligação da tomada do servidor à porta do servidor.*

*As rotinas de chamada de aplicação são chamadas de dentro do fio de ajuda do IP.*

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para o bloco de controlo da tomada do servidor TCP.
- **wait_option** Define como o serviço se comporta enquanto a ligação está sendo estabelecida. As opções de espera são definidas da seguinte forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)


### <a name="return-values"></a>Valores de devolução
- **NX_SUCCESS** (0x00) A tomada do servidor TCP bem sucedida aceita (ligação passiva).
- **NX_NOT_LISTEN_STATE** (0x36) A tomada do servidor fornecida não está num estado de escuta.
- **NX_IN_PROGRESS** (0x37) Não foi especificada qualquer espera, a tentativa de ligação está em curso.
- **NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para *tx_thread_wait_abort*.
- **NX_PTR_ERROR** (0x07) Erro do ponteiro da tomada.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) Este componente não foi ativado.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```C
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
        created */

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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten.
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect.
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_listen"></a>nx_tcp_server_socket_listen

Ativar a escuta da ligação do cliente na porta TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_server_socket_listen(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr,
    UINT listen_queue_size,
    VOID (*listen_callback)(NX_TCP_SOCKET *socket_ptr, UINT port));
```

### <a name="description"></a>Descrição

Este serviço permite ouvir um pedido de ligação ao cliente na porta TCP especificada. Quando um pedido de ligação ao cliente é recebido, a tomada do servidor fornecida fica ligada à porta especificada e a função de chamada de chamada de chamada de ouvido fornecida é chamada.

O processamento da rotina de chamada de escuta está completamente à altura da aplicação. Pode conter lógica para acordar um fio de aplicação que posteriormente executa uma operação de aceitação. Se a aplicação já tiver um fio suspenso no processamento de aceitação para esta tomada, a rotina de chamada de escuta pode não ser necessária.

Se a aplicação pretender manusear ligações adicionais ao cliente na mesma porta, o ***nx_tcp_server_socket_relisten*** deve ser chamado com uma tomada disponível (uma tomada no estado FECHADO) para a próxima ligação. Até que o serviço de re-ouvir seja chamado, as ligações adicionais do cliente são em fila. Quando a profundidade máxima da fila é excedida, o pedido de ligação mais antigo é retirado a favor da fila do novo pedido de ligação. A profundidade máxima da fila é especificada por este serviço.

*As rotinas de chamada de aplicação são chamadas a partir do fio interno do ajudante IP.*

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **porto** Número da porta para ouvir (1 a 0xFFFF).
- **socket_ptr** Ponteiro para tomada a utilizar para a ligação.
- **listen_queue_size** Número de pedidos de ligação ao cliente que podem ser na fila.
- **listen_callback** Função de aplicação para ligar quando a ligação é recebida. Se for especificado um NU, a função de chamada de escuta é desativada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Porta TCP bem sucedida ouvir.
- **NX_MAX_LISTEN** (0x33) Não há mais estruturas de pedido de escuta disponíveis. A NX_MAX_LISTEN_REQUESTS constante em nx_api.h define quantos pedidos de escuta ativa são possíveis.
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

```C
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
```

### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.
- nx_tcp_server_socket_accept, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten.
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect.
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_relisten"></a>nx_tcp_server_socket_relisten

Re-ouvir a ligação do cliente na porta TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_server_socket_relisten(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Descrição

Este serviço é chamado depois de ter sido recebida uma ligação numa porta que foi configurada anteriormente para escuta. O principal objetivo deste serviço é fornecer uma nova tomada de servidor para a próxima ligação ao cliente. Se um pedido de ligação for feito em fila, a ligação será processada imediatamente durante esta chamada de serviço.

*A mesma rotina de chamada especificada pelo pedido de escuta original também é chamada quando existe uma ligação para esta nova tomada do servidor.*

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

```C
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
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL,
        port_12_disconnect_request);

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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten.
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect.
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_unaccept"></a>nx_tcp_server_socket_unaccept

Remova a associação da tomada com a porta de escuta

### <a name="prototype"></a>Prototype

```C
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

```C
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
    /* The client has initiated a disconnect on this socket. This example
    doesn't use this callback. */
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
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,NX_NULL,
        port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye"
        to each client and then disconnecting. */
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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind, nx_tcp_enable.
- nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept.
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available.
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect.
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_unlisten"></a>nx_tcp_server_socket_unlisten

Desativar a escuta da ligação ao cliente na porta TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_server_socket_unlisten(NX_IP *ip_ptr, UINT port);
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

```C
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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept.
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect.
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_bytes_available"></a>nx_tcp_socket_bytes_available

Recupera o número de bytes disponíveis para recuperação

### <a name="prototype"></a>Prototype

```C
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

```C
/* Get the bytes available for retrieval on the specified socket. */
status = nx_tcp_socket_bytes_available(&my_socket,
    &bytes_available);

/* Is status = NX_SUCCESS, the available bytes is returned in
    bytes_available. */
```

### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept.
- nx_tcp_server_socket_unlisten, nx_tcp_socket_create.
- nx_tcp_socket_delete, nx_tcp_socket_disconnect.
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_create"></a>nx_tcp_socket_create

Criar tomada de cliente TCP ou servidor

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_create(
    NX_IP *ip_ptr, 
    NX_TCP_SOCKET *socket_ptr,
    CHAR *name, ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG window_size,
    VOID (*urgent_data_callback)(NX_TCP_SOCKET *socket_ptr),
    VOID (*disconnect_callback)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Descrição

Este serviço cria um cliente TCP ou tomada de servidor para a instância IP especificada.

*As rotinas de chamada de aplicação são chamadas a partir do fio associado a esta instância IP.*

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **socket_ptr** Ponteiro para o novo bloco de controlo da tomada TCP.
- **nome** Nome da aplicação para esta tomada TCP.
- **type_of_service** Define o tipo de serviço para a transmissão, os valores legais são os seguintes:

- NX_IP_NORMAL (0x00000000)
- NX_IP_MIN_DELAY (0x00100000)
- NX_IP_MAX_DATA (0x00080000)
- NX_IP_MAX_RELIABLE (0x00040000)
- NX_IP_MIN_COST (0x00020000)

- **fragmento**  Especifica se é permitida a fragmentação ip. Se NX_FRAGMENT_OKAY (0x0) for especificado, é permitida a fragmentação ip. Se NX_DONT_FRAGMENT (0x4000) for especificado, a fragmentação ip está desativada.
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

```C
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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept.
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available.
- nx_tcp_socket_delete, nx_tcp_socket_disconnect.
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_delete"></a>nx_tcp_socket_delete

Eliminar tomada TCP

### <a name="prototype"></a>Prototype

```C
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

```C
/* Delete a previously created TCP client socket. */
status = nx_tcp_socket_delete(&client_socket);

/* If status is NX_SUCCESS, the client socket is deleted. */
```

### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept.
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available.
- nx_tcp_socket_create, nx_tcp_socket_disconnect.
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_disconnect"></a>nx_tcp_socket_disconnect

Desligue as ligações de tomada de cliente e servidor

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_disconnect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Descrição

Este serviço desliga uma ligação estabelecida de tomada de cliente ou servidor. Uma desconexão de uma tomada do servidor deve ser seguida por um pedido não aceite, enquanto uma tomada de cliente desligada é deixada num estado pronto para outro pedido de ligação. Se o processo de desconexão não puder terminar imediatamente, o serviço suspende de acordo com a opção de espera fornecida.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada de cliente ou servidor previamente ligada.
- **wait_option** Define como o serviço se comporta enquanto a desconexão está em curso. As opções de espera são definidas da seguinte forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)

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

```C
/* Disconnect from a previously established connection and wait a
    maximum of 400 timer ticks. */
status = nx_tcp_socket_disconnect(&client_socket, 400);

/* If status is NX_SUCCESS, the previously connected socket (either
    as a result of the client socket connect or the server accept) is
    disconnected. */
```

### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept.
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available.
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_info_get.
- nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,
- nx_tcp_socket_send, nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_disconnect_complete_notify"></a>nx_tcp_socket_disconnect_complete_notify

Instalar a desconexão TCP completa notificar a função de retorno

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_disconnect_complete_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_disconnect_complete_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Descrição

Este serviço regista uma função de retorno que é invocada após a conclusão de uma operação de desconexão da tomada. A função de chamada completa da tomada TCP está disponível se o NetX for construído com a opção

- ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** definido.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada de cliente ou servidor previamente ligada.
- **tcp_disconnect_complete_notify** A função de retorno a instalar.

### <a name="return-values"></a>Valores de devolução
- **NX_SUCCESS** (0x00) registou com sucesso a função de retorno.
- **NX_NOT_SUPPORTED** (0x4B) A funcionalidade de notificação alargada não está incorporada na biblioteca NetX
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) funcionalidade TCP não está ativada.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```C
/* Install the disconnect complete notify callback function. */
status = nx_tcp_socket_disconnect_complete_notify(&client_socket,
    callback);
```

### <a name="see-also"></a>Consulte também

- nx_tcp_enable, nx_tcp_socket_create, nx_tcp_socket_establish_notify.
- nx_tcp_socket_mss_get, nx_tcp_socket_mss_peer_get,
- nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_establish_notify"></a>nx_tcp_socket_establish_notify

Definir TCP estabelecer notificação função de retorno

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_establish_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_establish_notify)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Descrição

Este serviço regista uma função de retorno, que é chamada depois de uma tomada TCP fazer uma ligação. A tomada TCP estabelece a função de retorno de chamada se o NetX for construído com a opção ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** definida.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada de cliente ou servidor previamente ligada.
- **tcp_establish_notify** Função de retorno invocada após a criação de uma ligação TCP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) define com sucesso a função de notificação.
- **NX_NOT_SUPPORTED** (0x4B) A funcionalidade de notificação alargada não está incorporada na biblioteca NetX
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) TCP não foi habilitado pelo pedido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```C
/* Set the function pointer "callback" as the notify function NetX
will call when the connection is in the established state. */
status = nx_tcp_socket_establish_notify(&client_socket, callback);
```

### <a name="see-also"></a>Consulte também

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set.
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify.
- nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure.
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_info_get"></a>nx_tcp_socket_info_get

Recuperar informações sobre as atividades da tomada de TCP

### <a name="prototype"></a>Prototype

```C
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

*Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao autor da chamada.*

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

### <a name="return-values"></a>Valores de devolução

```C
/* Retrieve TCP socket information from previously created socket_0.*/
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

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```C
/* Retrieve TCP socket information from previously created socket_0.*/
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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept.
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available.
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect.
- nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,
- nx_tcp_socket_send, nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_mss_get"></a>nx_tcp_socket_mss_get

Obtenha MSS de tomada

### <a name="prototype"></a>Prototype

```C
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

```C
/* Get the MSS for the socket "my_socket". */
status = nx_tcp_socket_mss_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket's current MSS value. */
```

### <a name="see-also"></a>Consulte também

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_peer_get.
- nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_peer_get"></a>nx_tcp_socket_mss_peer_get

Obtenha MSS da tomada TCP par

### <a name="prototype"></a>Prototype

```C
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

```C
/* Get the MSS of the connected peer to the socket "my_socket". */
status = nx_tcp_socket_mss_peer_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket peer’s advertised MSS value. */
```

### <a name="see-also"></a>Consulte também

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_set"></a>nx_tcp_socket_mss_set

Definir MSS de tomada

### <a name="prototype"></a>Prototype

```C
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

```C
/* Set the MSS of the socket "my_socket" to 1000 bytes. */
status = nx_tcp_socket_mss_set(&my_socket, 1000);

/* If status is NX_SUCCESS, the MSS of "my_socket" is 1000 bytes. */
```

### <a name="see-also"></a>Consulte também

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_peer_info_get"></a>nx_tcp_socket_peer_info_get

Recuperar informações sobre a tomada de TCP do par

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_peer_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *peer_ip_address, 
    ULONG *peer_port);
```

### <a name="description"></a>Descrição

Este serviço recupera o endereço IP e informações de porta para a tomada TCP conectada sobre a rede IP.

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

```C
/* Obtain peer IP address and port on the specified TCP socket. */
status = nx_tcp_socket_peer_info_get(&my_socket, &peer_ip_address,
    &peer_port);

/* If status = NX_SUCCESS, the data was successfully obtained. */
```

### <a name="see-also"></a>Consulte também

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set.
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_receive"></a>nx_tcp_socket_receive

Receber dados da tomada TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_receive(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Descrição

Este serviço recebe dados de TCP da tomada especificada. Se não forem dados na tomada especificada, o chamador suspende com base na opção de espera fornecida.

*Se NX_SUCCESS for devolvido, o pedido é responsável pela libertação do pacote recebido quando já não for necessário.*

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada TCP previamente criada.
- **packet_ptr** Ponteiro para ponteiro de pacoteS TCP.
- **wait_option** Define como o serviço se comporta se não houver dados atualmente em fila nesta tomada. As opções de espera são definidas da seguinte forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)

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

/* Receba um pacote da tomada do cliente TCP previamente criada e conectada. Se não houver pacote disponível, aguarde 200 carraças de temporizador antes de desistir. */ status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);

/* Se o estado for NX_SUCCESS, o pacote recebido é apontado por "packet_ptr". */

### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept.
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available.
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect.
- nx_tcp_socket_info_get, nx_tcp_socket_receive_queue_max_set,
- nx_tcp_socket_send, nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_receive_notify"></a>nx_tcp_socket_receive_notify

Notificar a aplicação dos pacotes recebidos


### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_receive_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_receive_notify) (NX_TCP_SOCKET *socket_ptr));
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

```C
/* Setup a receive packet callback function for the "client_socket"
socket. */
status = nx_tcp_socket_receive_notify(&client_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever one or more packets are received for
    "client_socket". */
```

### <a name="see-also"></a>Consulte também

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set.
- nx_tcp_socket_peer_info_get, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_send"></a>nx_tcp_socket_send

Enviar dados através de uma tomada TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_send(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Descrição

Este serviço envia dados de TCP através de uma tomada TCP previamente ligada. Se o último tamanho da janela anunciado pelo recetor for inferior a este pedido, o serviço suspende opcionalmente com base na opção de espera especificada. Este serviço garante que nenhum dado de pacote maior do que o MSS é enviado para a camada IP.

*A menos que um erro seja devolvido, o pedido não deve libertar o pacote após esta chamada. Ao fazê-lo, o controlador da rede também tentará libertar o pacote após a transmissão.*

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada TCP previamente ligada.
- **packet_ptr** Ponteiro do pacote de dados da TCP.
- **wait_option** Define como o serviço se comporta se o pedido for maior do que o tamanho da janela do recetor. As opções de espera são definidas da seguinte forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)

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

```C
/* Send a packet out on the previously created and connected TCP
    socket. If the receive window on the other side of the connection
    is less than the packet size, wait 200 timer ticks before giving up. */
status = nx_tcp_socket_send(&client_socket, packet_ptr, 200);

/* If status is NX_SUCCESS, the packet has been sent! */
```

### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept.
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available.
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect.
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_state_wait

### <a name="nx_tcp_socket_state_wait"></a>nx_tcp_socket_state_wait

Aguarde que a tomada TCP entre em estado específico

### <a name="prototype"></a>Prototype

```C
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
- NX_TCP_CLOSED (0x01)
- NX_TCP_LISTEN_STATE (0x02)
- NX_TCP_SYN_SENT (0x03)
- NX_TCP_SYN_RECEIVED (0x04)
- NX_TCP_ESTABLISHED (0x05)
- NX_TCP_CLOSE_WAIT (0x06)
- NX_TCP_FIN_WAIT_1 (0x07)
- NX_TCP_FIN_WAIT_2 (0x08)
- NX_TCP_CLOSING (0x09)
- NX_TCP_TIMED_WAIT (0x0A)
- NX_TCP_LAST_ACK (0x0B)
- **wait_option** Define como o serviço se comporta se o estado solicitado não estiver presente. As opções de espera são definidas da seguinte forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)

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

```C
/* Wait 300 timer ticks for the previously created socket to enter
    the established state in the TCP state machine. */
status = nx_tcp_socket_state_wait(&client_socket,
    NX_TCP_ESTABLISHED, 300);

/* If status is NX_SUCCESS, the socket is now in the established
    state! */
```

### <a name="see-also"></a>Consulte também

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept.
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available.
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect.
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send

## <a name="nx_tcp_socket_timed_wait_callback"></a>nx_tcp_socket_timed_wait_callback

Instale o callback para o estado de espera cronometrado

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_timed_wait_callback(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_timed_wait_callback) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Descrição

Este serviço regista uma função de retorno que é invocada quando a tomada TCP está em estado de espera cronometrado. Para utilizar este serviço, a biblioteca NetX deve ser construída com a opção ***NX_ENABLE_EXTENDED_NOTIFY*** definida.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada de cliente ou servidor previamente ligada.
- **tcp_timed_wait_callback** A função de retorno de espera cronometrado

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) regista com sucesso a tomada de função de retorno
- **NX_NOT_SUPPORTED** (0x4B) a biblioteca NetX é construída sem a funcionalidade de notificação estendida ativada.
- **NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.
- **NX_NOT_ENABLED** (0x14) funcionalidade TCP não está ativada.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```C
/* Install the timed wait callback function */
nx_tcp_socket_timed_wait_callback(&client_socket, callback);
```

### <a name="see-also"></a>Consulte também

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set.
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify.
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_transmit_configure"></a>nx_tcp_socket_transmit_configure

Configurar os parâmetros de transmissão da tomada

### <a name="prototype"></a>Prototype

```C
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

```C
/* Configure the "client_socket" for a maximum transmit queue depth
    of 12, 100 tick timeouts, a maximum of 20 retries, and a timeout
    double on each successive retry. */
status = nx_tcp_socket_transmit_configure(&client_socket,
    12,100,20, 1);

/* If status is NX_SUCCESS, the socket’s transmit retry has been
    configured. */
```

### <a name="see-also"></a>Consulte também

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set.
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify.
- nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_window_update_notify_set"></a>nx_tcp_socket_window_update_notify_set

Notifique a aplicação de atualizações do tamanho da janela

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_window_update_notify_set(
    NX_TCP_SOCKET
    *socket_ptr,
    VOID (*tcp_window_update_notify)
    (NX_TCP_SOCKET *socket_ptr));
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

```C
/* Set the function pointer to the windows update callback after creating the
socket. */
status = nx_tcp_socket_window_update_notify_set(&data_socket,
    my_windows_update_callback);

/* Define the window callback function in the host application. */
void my_windows_update_callback(NX_TCP_SCOCKET *data_socket)
{
    /* Process update on increase TCP transmit socket window size. */
    return;
}
```

### <a name="see-also"></a>Consulte também

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set.
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify.
- nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure

## <a name="nx_udp_enable"></a>nx_udp_enable

Ativar o componente UDP do NetX

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descrição

Este serviço permite o componente do Protocolo de Datagram do Utilizador (UDP) do NetX. Após ativação, os datagramas da UDP podem ser enviados e recebidos pelo pedido.

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

```C
/* Enable UDP on the previously created IP instance. */
status = nx_udp_enable(&ip_0);

/* If status is NX_SUCCESS, UDP is now enabled on the specified IP
    instance. */
```

### <a name="see-also"></a>Consulte também

- nx_udp_free_port_find, nx_udp_info_get, nx_udp_packet_info_extract.
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable.
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get.
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind.
- nx_udp_source_extract

## <a name="nx_udp_free_port_find"></a>nx_udp_free_port_find

Encontre a próxima porta UDP disponível

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_free_port_find(
    NX_IP *ip_ptr, 
    UINT port,
    UINT *free_port_ptr);
```

### <a name="description"></a>Descrição

Este serviço procura uma porta UDP gratuita (não ligada) a partir do número de porta fornecido pela aplicação. A lógica de pesquisa irá envolver-se se a pesquisa atingir o valor máximo da porta de 0xFFFF. Se a pesquisa for bem sucedida, a porta livre é devolvida na variável apontada por *free_port_ptr*.

*Este serviço pode ser chamado de outro fio e pode ter a mesma porta devolvida. Para evitar esta condição de regata, a aplicação pode pretender colocar este serviço e a tomada efetiva se ligam sob a proteção de um mutex.*

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

```C
/* Locate a free UDP port, starting at port 12, on a previously
    created IP instance. */
status = nx_udp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS pointer, "free_port" identifies the next
    free UDP port on the IP instance. */
```

### <a name="see-also"></a>Consulte também

- nx_udp_enable, nx_udp_info_get, nx_udp_packet_info_extract.
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable.
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get.
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind.
- nx_udp_source_extract

## <a name="nx_udp_info_get"></a>nx_udp_info_get

Recuperar informações sobre atividades da UDP

### <a name="prototype"></a>Prototype

```C
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

*Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao autor da chamada.*

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

```C
/* Retrieve UDP information from previously created IP Instance ip_0. */
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

- nx_udp_enable, nx_udp_free_port_find, nx_udp_packet_info_extract.
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable.
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get.
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind.
- nx_udp_source_extract

## <a name="nx_udp_packet_info_extract"></a>nx_udp_packet_info_extract

Extrair parâmetros de rede do pacote UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```

### <a name="description"></a>Descrição

Este serviço extrai parâmetros de rede, tais como endereço IP, número de porta de pares, tipo de protocolo (este serviço devolve sempre o tipo UDP) de um pacote recebido numa interface de entrada.

### <a name="parameters"></a>Parâmetros

- **packet_ptr** Ponteiro para pacote.
- **ip_address** Ponteiro para o endereço IP remetente.
- **protocolo** Ponteiro para o protocolo (UDP).
- **porto** Ponteiro para o número da porta do remetente.
- **interface_index** Ponteiro para receber índice de interface.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) dados de interface de pacote extraídos com sucesso.
- **NX_INVALID_PACKET** (0x12) O pacote não contém quadro IP.
- **NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro
- **NX_CALLER_ERROR** (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```C
/* Extract network data from UDP packet interface.*/
status = nx_udp_packet_info_extract( packet_ptr, &ip_address,
    &protocol, &port,
    &interface_index);

/* If status is NX_SUCCESS packet data was successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable.
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get.
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind.
- nx_udp_source_extract

## <a name="nx_udp_socket_bind"></a>nx_udp_socket_bind

Ligue a tomada UDP à porta UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_bind(
    NX_UDP_SOCKET *socket_ptr, 
    UINT port,
    ULONG wait_option);
```

### <a name="description"></a>Descrição

Este serviço liga a tomada UDP previamente criada à porta UDP especificada. As tomadas UDP válidas variam de 0 a 0xFFFF. Se o número de porta solicitado estiver ligado a outra tomada, este serviço aguarda por um período de tempo especificado para que a tomada se desvincula do número da porta.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada UDP previamente criada.
- **porto** Número da porta para ligar (1 a 0xFFFF). Se o número da porta for NX_ANY_PORT (0x0000), a instância IP procurará a próxima porta livre e usará-a para a encadernação.
- **wait_option** Define como o serviço se comporta se a porta já está ligada a outra tomada. As opções de espera são definidas da seguinte forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)

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

```C
/* Bind the previously created UDP socket to port 12 on the
    previously created IP instance. If the port is already bound,
    wait for 300 timer ticks before giving up. */
status = nx_udp_socket_bind(&udp_socket, 12, 300);

/* If status is NX_SUCCESS, the UDP socket is now bound to
    port 12.*/
```

### <a name="see-also"></a>Consulte também

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.
- nx_udp_packet_info_extract, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable.
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get.
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind.
- nx_udp_source_extract

## <a name="nx_udp_socket_bytes_available"></a>nx_udp_socket_bytes_available

Recupera o número de bytes disponíveis para recuperação

### <a name="prototype"></a>Prototype

```C
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

```C
/* Get the bytes available for retrieval from the UDP socket. */
status = nx_udp_socket_bytes_available(&my_socket, &bytes_available);

/* If status == NX_SUCCESS, the number of bytes was successfully
    retrieved.*/
```

### <a name="see-also"></a>Consulte também

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.
- nx_udp_packet_info_extract, nx_udp_socket_bind.
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable.
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get.
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind.
- nx_udp_source_extract

## <a name="nx_udp_socket_checksum_disable"></a>nx_udp_socket_checksum_disable

Desativar a parte de verificação da tomada UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_checksum_disable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Descrição

Este serviço desativa a lógica de checkum para o envio e receção de pacotes na tomada UDP especificada. Quando a lógica de checkum é desativada, um valor de zero é carregado no campo de verificação do cabeçalho UDP para todos os pacotes enviados através desta tomada. Um valor de dados de valor zero no cabeçalho UDP indica ao recetor que a parte de verificação não é calculada para este pacote.

Note também que isto não tem efeito se ***NX_DISABLE_UDP_RX_CHECKSUM** _ e _ *_NX_DISABLE_UDP_TX_CHECKSUM_** são definidos ao receber e enviar pacotes UDP respectivamente.

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

```C
/* Disable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_disable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will not have a checksum
    calculated. */
```

### <a name="see-also"></a>Consulte também

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.
- nx_udp_packet_info_extract, nx_udp_socket_bind.
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get.
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind.
- nx_udp_source_extract

## <a name="nx_udp_socket_checksum_enable"></a>nx_udp_socket_checksum_enable

Ativar a parte de verificação da tomada UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_checksum_enable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Descrição

Este serviço permite a lógica de checkum para o envio e receção de pacotes na tomada UDP especificada. A função de verificação abrange toda a área de dados da UDP, bem como um cabeçalho pseudo-IP.

Note também que isso não tem qualquer efeito se **NX_DISABLE_UDP_RX_CHECKSUM** e **NX_DISABLE_UDP_TX_CHECKSUM** forem definidos ao receber e enviar pacotes UDP respectivamente.

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

```C
/* Enable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_enable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will have a checksum
    calculated. */
```

### <a name="see-also"></a>Consulte também

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.
- nx_udp_packet_info_extract, nx_udp_socket_bind.
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get.
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind.
- nx_udp_source_extract

## <a name="nx_udp_socket_create"></a>nx_udp_socket_create

Criar tomada UDP.

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_create(
    NX_IP *ip_ptr,
    NX_UDP_SOCKET *socket_ptr, CHAR *name,
    ULONG type_of_service, ULONG fragment,
    UINT time_to_live, ULONG queue_maximum);
```

### <a name="description"></a>Descrição

Este serviço cria uma tomada UDP para a instância IP especificada.

### <a name="parameters"></a>Parâmetros

- **ip_ptr** Ponteiro para instância IP previamente criada.
- **socket_ptr** Ponteiro para o novo bloco de controlo de tomadas UDP.
- **nome** Nome da aplicação para esta tomada UDP.
- **type_of_service** Define o tipo de serviço para a transmissão, os valores legais são os seguintes:
    - NX_IP_NORMAL (0x00000000)
    - NX_IP_MIN_DELAY (0x00100000)
    - NX_IP_MAX_DATA (0x00080000)
    - NX_IP_MAX_RELIABLE (0x00040000)
    - NX_IP_MIN_COST (0x00020000)
- **fragmento** Especifica se é permitida a fragmentação ip. Se NX_FRAGMENT_OKAY (0x0) for especificado, é permitida a fragmentação ip. Se NX_DONT_FRAGMENT (0x4000) for especificado, a fragmentação ip está desativada.
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

```C
/* Create a UDP socket with a maximum receive queue of 30 packets.*/
status = nx_udp_socket_create(&ip_0, &udp_socket, "Sample UDP Socket",
    NX_IP_NORMAL, NX_FRAGMENT_OKAY, 0x80, 30);

/* If status is NX_SUCCESS, the new UDP socket has been created and
    is ready for binding. */
```

### <a name="see-also"></a>Consulte também

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.
- nx_udp_packet_info_extract, nx_udp_socket_bind.
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_delete,
- nx_udp_socket_info_get, nx_udp_socket_port_get,
- nx_udp_socket_receive, nx_udp_socket_receive_notify.
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_delete"></a>nx_udp_socket_delete

Eliminar tomada UDP

### <a name="prototype"></a>Prototype

```C
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

```C
/* Delete a previously created UDP socket. */
status = nx_udp_socket_delete(&udp_socket);

/* If status is NX_SUCCESS, the previously created UDP socket has
    been deleted. */
```

### <a name="see-also"></a>Consulte também

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.
- nx_udp_packet_info_extract, nx_udp_socket_bind.
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_info_get, nx_udp_socket_port_get,
- nx_udp_socket_receive, nx_udp_socket_receive_notify.
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_info_get"></a>nx_udp_socket_info_get

Recuperar informações sobre as atividades da tomada da UDP

### <a name="prototype"></a>Prototype

```C
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

*Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao autor da chamada.*

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

```C
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

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.
- nx_udp_packet_info_extract, nx_udp_socket_bind.
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_port_get,
- nx_udp_socket_receive, nx_udp_socket_receive_notify.
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_port_get"></a>nx_udp_socket_port_get

Recolha o número da porta vinculado à tomada UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_port_get(NX_UDP_SOCKET *socket_ptr, UINT *port_ptr);
```

### <a name="description"></a>Descrição

Este serviço recupera o número de porta associado à tomada, o que é útil para encontrar a porta atribuída pela NetX em situações em que o NX_ANY_PORT foi especificado no momento em que a tomada foi ligada.

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

```C
/* Get the port number of created and bound UDP socket. */
status = nx_udp_socket_port_get(&udp_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a>Consulte também

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.
- nx_udp_packet_info_extract, nx_udp_socket_bind.
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_receive, nx_udp_socket_receive_notify.
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_receive"></a>nx_udp_socket_receive

Receber datagrama da tomada UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_receive(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Descrição

Este serviço recebe um datagrama de UDP a partir da tomada especificada. Se não houver um datagrama na tomada especificada, o chamador suspende com base na opção de espera fornecida.

*Se NX_SUCCESS for devolvido, o pedido é responsável pela libertação do pacote recebido quando já não for necessário.*

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada UDP previamente criada.
- **packet_ptr** Ponteiro para o ponteiro do pacote de dados da UDP.
- **wait_option** Define como o serviço se comporta se um datagram não estiver atualmente em fila nesta tomada. As opções de espera são definidas da seguinte forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```C
/* Receive a packet from a previously created and bound UDP socket.
    If no packets are currently available, wait for 500 timer ticks
    before giving up. */
status = nx_udp_socket_receive(&udp_socket, &packet_ptr, 500);

/* If status is NX_SUCCESS, the received UDP packet is pointed to by
    packet_ptr. */
```

### <a name="see-also"></a>Consulte também

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.
- nx_udp_packet_info_extract, nx_udp_socket_bind.
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_receive_notify"></a>nx_udp_socket_receive_notify

Notifique a aplicação de cada pacote recebido

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_receive_notify(
    NX_UDP_SOCKET *socket_ptr,
    VOID (*udp_receive_notify)
    (NX_UDP_SOCKET *socket_ptr));
```

### <a name="description"></a>Descrição

Este serviço define o ponteiro de função de notificação de receção à função de retorno especificado pela aplicação. Esta função de retorno é então chamada sempre que um pacote é recebido na tomada. Se for fornecido um ponteiro NX_NULL, a função de notificação de receção é desativada.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a tomada UDP.
- **udp_receive_notify** Ponteiro da função de retorno da aplicação que é chamado quando um pacote é recebido na tomada.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```C
/* Setup a receive packet callback function for the "udp_socket"
socket. */
status = nx_udp_socket_receive_notify(&udp_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever a packet is received for
    "udp_socket". */
```

### <a name="see-also"></a>Consulte também

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.
- nx_udp_packet_info_extract, nx_udp_socket_bind.
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive, nx_udp_socket_send.
- nx_udp_socket_interface_send, nx_udp_socket_unbind.
- nx_udp_source_extract

## <a name="nx_udp_socket_send"></a>nx_udp_socket_send

Enviar um UDP Datagram

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port);
```

### <a name="description"></a>Descrição

Este serviço envia um datagrama de UDP através de uma tomada UDP previamente criada e ligada. O NetX encontra um endereço IP local adequado como endereço de origem baseado no endereço IP de destino. Para especificar uma interface específica e endereço IP de origem, a aplicação deve utilizar o serviço **nx_udp_socket_interface_send.**

Note que este serviço retorna imediatamente independentemente de o datagrama da UDP ter sido enviado com sucesso.

A tomada deve estar ligada a um porto local.

### <a name="parameters"></a>Parâmetros

- **socket_ptr** Ponteiro para a instância de tomada UDP previamente criada
- **packet_ptr** Ponteiro do pacote de datagrama da UDP
- **ip_address** Endereço IP de destino
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

```C
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

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.
- nx_udp_packet_info_extract, nx_udp_socket_bind.
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_interface_send"></a>nx_udp_socket_interface_send

Envie datagrama através da tomada UDP.

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_interface_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port,
    UINT address_index);
```

### <a name="description"></a>Descrição

Este serviço envia um datagrama de UDP através de uma tomada UDP previamente criada e ligada através da interface de rede com o endereço IP especificado como endereço de origem. Note que o serviço regressa imediatamente, independentemente de o datagrama da UDP ter sido enviado com sucesso.

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

```C
#define ADDRESS_INDEX 1

/* Send packet out on port 80 to the specified destination IP on the
interface at index 1 in the IP task interface list. */
status = nx_udp_packet_interface_send(socket_ptr, packet_ptr,
    destination_ip, 80,
    ADDRESS_INDEX);

/* If status is NX_SUCCESS packet was successfully transmitted. */
```

### <a name="see-also"></a>Consulte também

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.
- nx_udp_packet_info_extract, nx_udp_socket_bind.
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_unbind

## <a name="nx_udp_socket_unbind"></a>nx_udp_socket_unbind

Tomada UDP desaderada da porta UDP.

### <a name="prototype"></a>Prototype

```C
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

```C
/* Unbind the previously bound UDP socket. */
status = nx_udp_socket_unbind(&udp_socket);

/* If status is NX_SUCCESS, the previously bound socket is now
    unbound. */
```

### <a name="see-also"></a>Consulte também

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.
- nx_udp_packet_info_extract, nx_udp_socket_bind.
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_source_extract

## <a name="nx_udp_source_extract"></a>nx_udp_source_extract

Extrair IP e enviar porta a partir do datagrama da UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_source_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address, UINT *port);
```

### <a name="description"></a>Descrição

Este serviço extrai o número de IP e porta do remetente dos cabeçalhos IP e UDP do programa de dados da UDP fornecido.

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

```C
/* Extract the IP and port information from the sender of the UPD
    packet. */
status = nx_udp_source_extract(packet_ptr, &sender_ip_address,
    &sender_port);

/* If status is NX_SUCCESS, the sender IP and port information has
    been stored in sender_ip_address and sender_port respectively.*/
```

### <a name="see-also"></a>Consulte também

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.
- nx_udp_packet_info_extract, nx_udp_socket_bind.
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind