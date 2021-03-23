---
title: Capítulo 4 - Azure RTOS NetX Duo DHCPv6 Serviços de clientes
description: Este capítulo contém uma descrição de todos os serviços de clientes Azure RTOS NetX Duo DHCPv6 (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 40fbfa7319ca95af65c92b12582d4bbb05005dc0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826072"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-client-services"></a>Capítulo 4 - Azure RTOS NetX Duo DHCPv6 Serviços de clientes

Este capítulo contém uma descrição de todos os serviços de clientes Azure RTOS NetX Duo DHCPv6 (listados abaixo) por ordem alfabética.

Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

- **nx_dhcpv6_client_create:** *Criar uma instância de cliente DHCPv6* 

- **nx_dhcpv6_client_delete:** *Eliminar uma instância de cliente DHCPv6* 

- **nx_dhcpv6_create_ client_duid:** *Criar um DHCPv6 Client DUID* 

- **nx_dhcpv6 _add_client_ia:** *Adicionar um Endereço de Identidade do Cliente DHCPv6 (IA)* 

- **nx_dhcpv6 _create_client_ia:** *(Legacy Add a DHCPv6 Client Identity Address (IA))* 

- **nx_dhcpv6_create_client_iana:** *Criar uma Associação de Identidade de Cliente DHCPv6 para endereços não temporários (IANA)* 

- **nx_dhcpv6_get_client_duid_time_id:** *Obtenha o tempo ID do DHCPv6 Client DUID* 

- **nx_dhcpv6_client_set_interface:** *Definir a interface de rede do Cliente para comunicações com o Servidor DHCPv6* 

- **nx_dhcpv6_get_IP_address:** *Obtenha o endereço IPv6 global atribuído ao cliente DHCPv6* 

- **nx_dhcpv6_get_lease_time_data:** *Obtenha estadias de vida válidas e preferidas para o endereço IPv6 global do Cliente*

- **nx_dhcpv6_get_valid_ip_address_lease_time:** *Obtenha tempos de vida válidos e preferidos para o endereço IPv6 do cliente DHCPv6 por índice de endereço* 

- **nx_dhcpv6_get_iana_lease_time:** *Obter T1 e T2 na Associação de Identidade (IANA) arrendados ao Cliente DHCPv6* 

- **nx_dhcpv6_get_other_option_data:** *Obtenha os dados de opção especificados, por exemplo, nome de domínio ou servidor de fuso horário* 

- **nx_dhcpv6_get_DNS_server_address:** *Obtenha o endereço DNS Server no índice especificado na lista de servidores DNS do cliente DHCPv6* 

- **nx_dhcpv6_get_time_accrued:** *Obtenha o tempo acumulado o arrendamento global de endereços IPv6 foi vinculado ao Cliente DHCPv6* 

- **nx_dhcpv6_get_time_server_address:** *Obtenha o endereço do Servidor de Tempo no índice especificado na lista de servidores do tempo do cliente DHCPv6*

- **nx_dhcpv6_get_valid_ip_address_count:** *Obtenha o número de endereços IPv6 atribuídos ao Cliente DHCPv6* 

- **nx_dhcpv6_reinitialize:** *Reinitializar o DHCPv6 para reiniciar a máquina estatal DHCPv6 e reexecutar o protocolo DHCPv6* 

- **nx_dhcpv6_request_confirm:** *Enviar um pedido CONFIRMA para o Servidor* 

- **nx_dhcpv6_request_inform_request:** S *termine uma mensagem INFORM REQUEST para o Servidor* 

- **nx_dhcpv6_request_release:** *Enviar um pedido de LIBERTAÇÃO para o Servidor* 

- **nx_dhcpv6_request_option_DNS_server:** *Adicionar a opção de servidor DNS à opção de pedido de cliente em mensagens de pedido para o Servidor* 

- **nx_dhcpv6_request_option_FQDN:** *Adicionar a opção FQDN à opção cliente solicitar dados em mensagens de pedido ao Servidor* 

- **nx_dhcpv6_request_option_domain_name:** *Adicionar a opção nome de domínio à opção de pedido de cliente em mensagens de pedido ao Servidor* 

- **nx_dhcpv6_request_option_time_server:** *Adicionar a opção de servidor de tempo à opção cliente solicitar dados em mensagens de pedido ao Servidor* 

- **nx_dhcpv6_request_option_timezone:** *Adicione a opção de fuso horário à opção de pedido de dados do Cliente em mensagens de pedido ao Servidor* 

- **nx_dhcpv6_request_solicit:** *Enviar um pedido DHCPv6 SOLICIT a qualquer Servidor na rede cliente (transmissão)* 

- **nx_dhcpv6_request_solicit_rapid:** *Enviar um pedido DHCPv6 SOLICIT a qualquer Servidor na rede cliente (transmissão) com o conjunto de opções De Compromisso Rápido* 

- **nx_dhcpv6_resume:** *Retomar o processamento do cliente DHCPv6* 

- **nx_dhcpv6_start:** *Inicie a tarefa de thread do cliente DHCPv6. Note que isto não é equivalente a iniciar a máquina estatal DHCPv6 e não envia um pedido SOLICIT* 

- **nx_dhcpv6_stop:** *Parar a tarefa de thread do cliente DHCPv6* 

- **nx_dhcpv6_suspend:** *Suspender a tarefa de thread do cliente DHCPv6* 

- **nx_dhcpv6_set_time_accrued:** *Dedibrar o tempo acumulado no contrato global de locação de endereços IPv6 do Cliente no registo do Cliente.*

## <a name="nx_dhcpv6_client_create"></a>nx_dhcpv6_client_create

Criar uma instância de cliente DHCPv6

### <a name="prototype"></a>Prototype

```C
UINT  nx_dhcpv6_client_create(NX_DHCPV6 *dhcpv6_ptr, 
                        NX_IP *ip_ptr, CHAR *name_ptr, 
                        NX_PACKET_POOL *packet_pool_ptr, 
                        VOID *stack_ptr, ULONG stack_size,
                        VOID (*dhcpv6_state_change_notify)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                  UINT old_state, UINT new_state), 
                        VOID (*dhcpv6_server_error_handler)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                 UINT op_code, UINT status_code, 
                                 UINT message_type));
```

### <a name="description"></a>Descrição

Este serviço cria uma instância de cliente DHCPv6, incluindo funções de retorno.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para bloco de controlo DHCPv6  

- **ip_ptr** Indicação para o cliente ip instância  

- **name_ptr** Ponteiro para nomear para a instância DHCPv6

- **packet_pool_ptr** Ponteiro para piscina de pacotes de cliente

- **stack_ptr** Ponteiro para memória de pilha de cliente

- **stack_size** Tamanho da memória da pilha de cliente

- **dhcpv6_state_change_notify** Função de retorno do ponteiro invocado quando o Cliente inicia um novo pedido de DHCPv6 para o servidor

- **dhcpv6_server_error_handler** Função de retorno do ponteiro invocado quando o Cliente recebe um estado de erro do servidor

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Sucesso cliente criar

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_DHCPV6_PARAM_ERROR (0xE93) Entrada inválida sem ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Create a DHCPv6 client instance without specifying link local or preferred
   global IP address.  */
status =  nx_dhcpv6_client_create(&dhcp_0, &ip_0, "DHCPv6 Client", &pool_0,
                                  NULL, NULL, pointer, 2048,        
                                  dhcpv6_state_change_notify, 
                                  dhcpv6_server_error_handler);

/* If status is NX_SUCCESS a DHCPv6 client instance was successfully
   created.  */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_client_delete

## <a name="nx_dhcpv6_client_delete"></a>nx_dhcpv6_client_delete

Excluir uma instância de cliente DHCPv6

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_client_delete(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descrição

Este serviço elimina uma instância de cliente DHCPv6 previamente criada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Eliminação bem sucedida do DHCPv6

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_DHCPV6_PARAM_ERROR (0xE93) Entrada inválida sem ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Delete a DHCPv6 client instance.  */
status =  nx_dhcpv6_client_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCPv6 client instance was successfully
   deleted.  */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_client_create

## <a name="nx_dhcpv6_client_set_interface"></a>nx_dhcpv6_client_set_interface

Define a Interface de Rede do Cliente para DHCPv6

### <a name="prototype"></a>Prototype

```C
UINT    nx_dhcpv6_client_set_interface(NX_DHCPV6 *dhcpv6_ptr, 
                                       UINT *interface_index);
```

### <a name="description"></a>Descrição

Este serviço define a interface de rede do Cliente para comunicar com o(s) Servidor(s) DHCPv6 ao índice de interface de entrada especificado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

- **interface_index** Índice indicando interface de rede

### <a name="return-values"></a>Valores de devolução

- **interface NX_SUCCESS** (0x00) definida com sucesso

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_INVALID_INTERFACE (0x4C) Entrada do índice de interface inválida

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Set the client interface for DHCPv6 communication with the Server to 
   the secondary interface (1). */

UINT index = 1;
status = nx_dhcpv6_client_set_interface(&dhcp_0, index);

/* If status is NX_SUCCESS, the Client successfully set 
   the DHCPv6 network interface.  */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_client _create
- nx_dhcpv6_start

## <a name="nx_dhcpv6_client_set_destination_address"></a>nx_dhcpv6_client_set_destination_address

Define o endereço de destino onde a mensagem DHCPv6 deve ser enviada para

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_client_set_destination_address(NX_DHCPV6 *dhcpv6_ptr,
                                              NXD_ADDRESS *destination_address);
```

### <a name="description"></a>Descrição

Este serviço define o endereço de destino para onde a mensagem DHCPv6 deve ser enviada. Por predefinição está ALL_DHCP_Relay_Agents_and_Servers(FF02:1:2).

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

- **destination_address** Endereço de destino

### <a name="return-values"></a>Valores de devolução

- **interface NX_SUCCESS** (0x00) definida com sucesso

- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

- NX_DHCPV6_PARAM_ERROR (0xE93) Erro de paramentamento

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Set the destination address where DHCPv6 message should be sent to. */

NXD_ADDRESS dest_address; /* Set the destination address.  */

status = nx_dhcpv6_client_set_destination_address(&dhcp_0, &dest_address);

/* If status is NX_SUCCESS, the Client successfully set the destination address. */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_client _create
- nx_dhcpv6_start

## <a name="nx_dhcpv6_create_client_duid"></a>nx_dhcpv6_create_client_duid

Criar objeto DUID do cliente

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr,
                                  UINT duid_type, UINT hardware_type,
                                  ULONG time);
```

### <a name="description"></a>Descrição

Este serviço cria o DuID do Cliente com os parâmetros de entrada. Se a entrada de tempo não for fornecida e o tipo duid indicar camada de ligação com o tempo, esta função fornecerá um tempo que inclui um fator de aleatoriedade para a singularidade. Os tipos duid atribuídos pelo fornecedor (empresa) não são suportados.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

- **duid_type** Tipo de DUID (hardware, empresa, etc)

- **hardware_type** Hardware de rede, por exemplo, IEEE 802

- **tempo** Valor utilizado na criação de identificador único

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Cliente BEM sucedido DUID criado

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_DHCPV6_PARAM_ERROR (0xE93) Entrada inválida sem ponteiro

- NX_DHCPV6_UNSUPPORTED_DUID_TYPE (0xE98) tipo DUID desconhecido ou não suportado 

- NX_DHCPV6_UNSUPPORTED_DUID_HW_TYPE (0xE99) tipo de hardware DUID desconhecido ou não suportado

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Create the Client DUID from the supplied input.
   The time field is left NULL so the DHCPv6 client will provide one.  */
status = nx_dhcpv6_create_client_duid(&dhcp_0, NX_DHCPV6_DUID_TYPE_LINK_TIME,
                                      NX_DHCPV6_HW_TYPE_IEEE_802, 0)

/* If status is NX_SUCCESS the client DUID was successfully created.  */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_create_client_ia
- nx_dhcpv6_create_client_iana
- nx_dhcpv6_create_server_duid

## <a name="nx_dhcpv6_create_client_ia"></a>nx_dhcpv6_create_client_ia

Adicionar uma Associação de Identidade ao Cliente

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_create_client_ia(NX_DHCPV6 *dhcpv6_ptr,
                                NXD_ADDRESS *ipv6_address,
                                ULONG preferred_lifetime,
                                ULONG valid_lifetime);
```

### <a name="description"></a>Descrição

Este serviço é idêntico ao *serviço nx_dhcpv6_add_client_ia.* Adiciona uma Associação de Identidade de Cliente preenchendo o registo do Cliente com os parâmetros fornecidos. Para solicitar as horas máximas preferenciais e válidas, desa um determinado parâmetro ao infinito. Para adicionar mais de um IA a um Cliente DHCPv6, desempate o NX_DHCPV6_MAX_IA_ADDRESS para um valor superior ao valor padrão de 1.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

- **ipv6_address** Ponteiro para o bloco de endereços IP netx duo

- **preferred_lifetime** Período de tempo antes de o endereço IP ser depreciado

- **valid_lifetime** Período de tempo antes do endereço IP expirar

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Cliente bem sucedido IA adicionado

- **NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Endereço DUPLICADO IA 

- **NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) IA excede o máximo que o Cliente IAs pode armazenar

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) Endereço IA inválido (por exemplo, nulo) endereço ia em IA

- NX_DHCPV6_PARAM_ERROR (0xE93) Entrada inválida sem ponteiro


### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_create_client_ia(&dhcp_0, &ipv6_address, 
NX_DHCPV6_PREFERRED_LIFETIME, NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_add_client_duid
- nx_dhcpv6_create_server_duid
- nx_dhcpv6_create_client_iana

## <a name="nx_dhcpv6_create_client_iana"></a>nx_dhcpv6_create_client_iana

Criar uma Associação de Identidade (Não Temporária) para o Cliente

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT IA_ident, ULONG T1, ULONG T2);
```

### <a name="description"></a>Descrição

Este serviço cria uma Associação de Identidade Não Temporária (IANA) a partir dos parâmetros fornecidos. Para definir as vezes T1 e T2 no máximo (infinito) nos pedidos do Cliente DHCPv6, desajei estes parâmetros a NX_DHCPV6_INFINITE_LEASE. 

> [!NOTE]
> Um cliente tem apenas um IANA.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

- **IA_ident** Identificador único da Associação de Identidade

- **T1** Quando o Cliente deve iniciar a renovação do endereço IPv6

- **T2** Quando o Cliente deve iniciar o reencambido endereço DeVV6

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) criou com sucesso o IANA

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_DHCPV6_PARAM_ERROR (0xE93) Entrada inválida sem ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Create the Client IANA from the supplied input.  */
status = nx_dhcpv6_create_client_iana(&dhcp_0, DHCPV6_IA_ID, DHCPV6_T1,   
                                      DHCPV6_T2);

/* If status is NX_SUCCESS the client IANA was successfully created.  */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_create_client_duid
- nx_dhcpv6_create_server_duid
- nx_dhcpv6_add_client_ia

## <a name="nx_dhcpv6_add_client_ia"></a>nx_dhcpv6_add_client_ia 

Adicionar uma Associação de Identidade ao Cliente

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                             NXD_ADDRESS *ipv6_address, 
                             ULONG preferred_lifetime, 
                             ULONG valid_lifetime);
```

### <a name="description"></a>Descrição

Este serviço adiciona uma Associação de Identidade de Cliente preenchendo o registo do Cliente com os parâmetros fornecidos. Para solicitar as horas máximas preferenciais e válidas, desa um determinado parâmetro ao infinito. Para adicionar mais de um IA a um Cliente DHCPv6, desempate o NX_DHCPV6_MAX_IA_ADDRESS para um valor superior ao valor padrão de 1.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

- **ipv6_address** Ponteiro para o bloco de endereços IP netx duo

- **preferred_lifetime** Período de tempo antes de o endereço IP ser depreciado

- **valid_lifetime** Período de tempo antes do endereço IP expirar 

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Cliente bem sucedido IA adicionado

- **NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Endereço DUPLICADO IA 

- **NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) IA excede o máximo que o Cliente IAs pode armazenar

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) Endereço IA inválido (por exemplo, nulo) endereço ia em IA

- NX_DHCPV6_PARAM_ERROR (0xE93) Entrada inválida sem ponteiro

 
### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_add_client_ia(&dhcp_0, &ipv6_address, 
                                 NX_DHCPV6_PREFERRED_LIFETIME,
                                 NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_create_client_duid
- nx_dhcpv6_create_server_duid
- nx_dhcpv6_create_client_iana

## <a name="nx_dhcpv6_get_client_duid_time_id"></a>nx_dhcpv6_get_client_duid_time_id

Recupera o tempo ID do Cliente DUID

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_get_client_duid_time_id(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_id);
```

### <a name="description"></a>Descrição

Este serviço recupera o campo de identificação de tempo do Cliente DUID. Se a aplicação tiver de ligar primeiro *nx_dhcpv6_create_client_duid,* para preencher o DUID do Cliente na instância do Cliente DHCPv6 ou terá um valor nulo para este campo. A intenção é que a aplicação guarde estes dados e apresente o mesmo DuID do Cliente ao servidor, incluindo o campo de tempo, através de reboots.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

- **time_id** Ponteiro para o campo de tempo DUID do cliente

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) dados de locação IP recuperados com sucesso

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Retrieve the time ID from the Client DUID.  */
status = nx_dhcpv6_get_client_duid_time_id(&dhcp_0, &time_ID);

/* If status is NX_SUCCESS the time ID was retrieved. */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_time_lease_data
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_ip_address"></a>nx_dhcpv6_get_IP_address

Recupera o endereço global do IPv6 do cliente

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_get_IP_address(NX_DHCPV6 *dhcpv6_ptr, 
                              NXD_ADDRESS *ip_address);
```

### <a name="description"></a>Descrição

Este serviço recupera o endereço IPv6 global do Cliente. Se o Cliente não tiver um endereço válido, é devolvido um estado de erro. Se um Cliente tiver mais de um endereço IPv6 global, o endereço IPv6 primário é devolvido.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

- **ip_address** Ponteiro para endereço IPv6

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) endereço IPv6 atribuído com sucesso

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) endereço IPv6 não é válido

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
UINT address_status;
UINT address_index;

/* Retrieve the client’s assigned IP address.  */
status = nx_dhcpv6_get_IP_address(&dhcp_0, &ipv6_address);

/* If status is NX_SUCCESS the client IP address was assigned.
   Now register it with NetX Duo on the primary interface (index zero). 
   The address index is returned in the address_index field*/
status = nxd_ipv6_address_set(&ip_0, 0, &ipv6_address, 64, &address_index);
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_client_duid_time_id
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_lease_time_data"></a>nx_dhcpv6_get_lease_time_data

Recupera os dados do tempo de locação de endereços do cliente

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_get_lease_time_data(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                   ULONG *T2, ULONG *preferred_lifetime, 
                                   ULONG *valid_lifetime);
```

### <a name="description"></a>Descrição

Este serviço recupera os dados globais do tempo de endereço do Cliente. Se o estado do endereço do Cliente IA for inválido, os dados de tempo são definidos para zero e um estado de conclusão bem-sucedido é devolvido. Se um Cliente tiver mais de um endereço IPv6 global, os dados de endereços ii primários são devolvidos.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

- **T1** Ponteiro para IA abordar tempo de renovação

- **T2** Ponteiro para o tempo de reencadernação do endereço ia

- **preferred_lifetime** Ponteiro para o tempo quando o endereço ia é depreciado

- **valid_lifetime** Ponteiro para o momento em que o endereço IA está expirado

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) dados de locação financeira da IA recuperados com sucesso

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Retrieve the client’s assigned IA lease data.  */
status = nx_dhcpv6_get_lease_time_data(&dhcp_0, &T1, &T2, &preferred_lifetime, 
                                       &valid_lifetime);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_client_duid_time_id
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued
- nx_dhcpv6_get_iana_lease_time

## <a name="nx_dhcpv6_get_iana-lease_time"></a>nx_dhcpv6_get_iana lease_time

Recupere os dados do tempo de locação IANA do Cliente

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_get_iana_lease_time(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                    ULONG *T2);
```

### <a name="description"></a>Descrição

Este serviço recupera os dados globais do tempo de locação ia-NA do Cliente (T1 e T2). Se nenhum dos endereços IA-NA do Cliente tiver um estado de endereço válido, os dados de tempo são definidos para zero e um estado de conclusão bem-sucedido é devolvido. Se um Cliente tiver mais de um endereço IPv6 global, os dados de endereços ii primários são devolvidos.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

- **T1** Ponteiro a tempo para iniciar a renovação do arrendamento

- **T2** Ponteiro a tempo para iniciar o reencaimento do arrendamento

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) dados de locação IANA recuperados com sucesso

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Retrieve the client’s assigned IANA lease data.  */
status = nx_dhcpv6_get_iana_lease_time(&dhcp_0, &T1, &T2);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_client_duid_time_id
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued
- nx_dhcpv6_get_lease_time_data

## <a name="nx_dhcpv6_get_valid_ip_address_count"></a>nx_dhcpv6_get_valid_ip_address_count

Recupere uma contagem dos endereços IA válidos do Cliente

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_get_valid_ip_address_count(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT *address_count);
```

### <a name="description"></a>Descrição

Este serviço recupera a contagem dos endereços IPv6 válidos do Cliente. Um endereço IPv6 válido está vinculado (atribuído) ao Cliente e registado na instância IP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

- **address_count** Ponteiro para a contagem de endereços para devolver

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) dados de locação IANA recuperados com sucesso

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
UINT address_count; 

/* Retrieve the count of valid IA-NA addresses.  */
status = nx_dhcpv6_get_valid_ip_address_count(&dhcp_0, &address_count);

/* If status is NX_SUCCESS the client IA address count was retrieved.  */
```

## <a name="nx_dhcpv6_get_valid_ip_address_lease_time"></a>nx_dhcpv6_get_valid_ip_address_lease_time

Recupere os dados do Cliente IA por índice de endereço

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                               UINT address_index,
                                               NXD_ADDRESS *ip_address,
                                               ULONG *preferred_lifetime,
                                               ULONG *valid_lifetime);
```

### <a name="description"></a>Descrição

Este serviço recupera o endereço ia do Cliente e os dados de locação por índice de endereço. Se for fornecido um índice inválido ou o endereço IPv6 nesse índice não for válido, o serviço devolve um estado de erro NX_DHCPV6_IA_ADDRESS_NOT_VALID.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

- **address_index** Índice na tabela DHCPv6 IA

- **ip_address** Ponteiro para endereço IPv6 para recuperar

- **preferred_lifetime** Ponteiro para o tempo quando o endereço ia é depreciado

- **valid_lifetime** Ponteiro para o momento em que o endereço IA está expirado

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) dados da IANA recuperados com sucesso

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) Um índice inválido ou nenhum endereço IPv6 válido no índice fornecido 

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
UINT address_index = 1; 
NXD_ADDRESS *ip_address;

/* Retrieve the IPv6 address, and valid and preferred lifetime for the IA record
   Saved at index 1 in the DHCPv6 table.  */
status = nx_dhcpv6_get_valid_ip_address_lease_time(&dhcp_0, address_index, 
                                                   &ip_address, 
                                                   &preferred_lifetime,  
                                                   &valid_lifetime);

/* If status is NX_SUCCESS the client IA address and lease data were retrieved.  */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_iana_lease_time
- nx_dhcpv6_get_lease_time_data

## <a name="nx_dhcpv6_get_dns_server_address"></a>nx_dhcpv6_get_DNS_server_address

Recupera o endereço do Servidor DNS 

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_get_DNS_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index,
                                      NXD_ADDRESS *server_address);
```

### <a name="description"></a>Descrição

Este serviço recupera os dados de endereços do servidor DNS IPv6 no índice especificado na lista de Clientes. Se a lista não contiver um endereço de servidor no índice, um erro é devolvido. O índice não pode exceder o tamanho da lista do Servidor DNS é especificado pela opção configurável do utilizador NX_DHCPV6_NUM_DNS_SERVERS.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

- **índice** Índice na lista do Servidor DNS

- **server_address** Ponteiro para o tampão de endereço do servidor

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Endereço recuperado com sucesso

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Retrieve the DNS server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


        status = nx_dhcpv6_get_DNS_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the DNS server IP address successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_other_option_data"></a>nx_dhcpv6_get_other_option_data

Recupera dados de opção DHCPv6 

### <a name="prototype"></a>Prototype

```C
UINT  nx_dhcpv6_get_other_option_data(NX_DHCPV6 *dhcpv6_ptr, 
                                      UINT option_code, UCHAR *buffer);
```

### <a name="description"></a>Descrição

Este serviço recupera os dados de opção DHCPv6 a partir de uma mensagem DHCPv6 para o código de opção especificado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

- código **de opção** Código código código para que dados para recuperar

- **tampão** Ponteiro para tampão para copiar dados para 

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Dados de opção recuperados com sucesso

- **NX_DHCPV6_UNKNOWN_OPTION** (0xEAB) Código de opção desconhecido/não suportado

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_DHCPV6_PARAM_ERROR (0xE93) Entrada inválida sem ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Retrieve the option data specified by the input option code. */
status = nx_dhcpv6_get_other_option_data(&dhcp_0, option_code, buffer);

/* If status is NX_SUCCESS the option data was retrieved. */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_time_accrued"></a>nx_dhcpv6_get_time_accrued

Recupera tempo acumulado no contrato de arrendamento de endereços IP do Cliente

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_accrued);
```

### <a name="description"></a>Descrição

Este serviço recupera o tempo acumulado no contrato de arrendamento de endereços IPv6 do Cliente. A função verifica todos os endereços IPv6 atribuídos ao Cliente para o primeiro endereço válido. Se não forem encontrados endereços válidos, é devolvido um valor zero pelo tempo acumulado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

- **time_accrued** Ponteiro para o tempo acumulado no arrendamento IP

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Tempo acumulado recuperado com sucesso

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Retrieve time accrued time on the Client address lease. */
status = nx_dhcpv6_get_time_accrued(&dhcp_0, &time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address 
   lease was retrieved. */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_set_time_accrued

## <a name="nx_dhcpv6_get_time_server_address"></a>nx_dhcpv6_get_time_server_address

Recupera o endereço do servidor de tempo 

### <a name="prototype"></a>Prototype

```C
UINT  nx_dhcpv6_get_time_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index, 
                                        NXD_ADDRESS *server_address);
```

### <a name="description"></a>Descrição

Este serviço recupera os dados de endereços do servidor Time IPv6 no índice especificado na lista de Clientes. Se a lista não contiver um endereço de servidor no índice, um erro é devolvido. O índice não pode exceder o tamanho da lista de Servidor de Tempo é especificado pela opção configurável do utilizador NX_DHCPV6_NUM_TIME_SERVERS.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

- **índice** Índice na lista do Servidor de Tempo

- **server_address** Ponteiro para o tampão de endereço do servidor

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Endereço recuperado com sucesso

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Retrieve the Time server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


      status = nx_dhcpv6_get_time_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the Time server IP address successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued
- nx_dhcpv6_get_DNS_server_address

## <a name="nx_dhcpv6_reinitialize"></a>nx_dhcpv6_reinitialize

Remova o endereço IP do Cliente da tabela IP

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_reinitialize(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descrição

Este serviço reinicia o Cliente para reiniciar a máquina estatal DHCPv6 e re-executar o protocolo DHCPv6. Isto não é necessário se o Cliente não tiver iniciado previamente a máquina estatal DHPCv6 ou tiver sido atribuído qualquer endereço IPv6. Os endereços guardados para o Cliente DHCPv6, bem como registados na instância IP, estão ambos limpos.

> [!NOTE]
> A aplicação deve ainda iniciar o Cliente DHCPv6 utilizando o *serviço de nx_dhcpv6_start* e iniciar o pedido de atribuição de endereços IPv6 ligando para *nx_dhcpv6_request_solicit*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

### <a name="return-values"></a>Valores de devolução

- **endereço NX_SUCCESS** (0x00) removido com sucesso

- **cliente NX_DHCPV6_ALREADY_STARTED** (0xE91) DHCPv6 já está em execução

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Clear the assigned IP address(es) from the Client and the IP instance */
status = nx_dhcpv6_reinitialize(&dhcp_0);

/* If status is NX_SUCCESS the Client IP address was successfully removed. */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_stop
- nx_dhcpv6_start

## <a name="nx_dhcpv6_request_confirm"></a>nx_dhcpv6_request_confirm

Processar o estado confirma do Cliente

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_confirm(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descrição

Este serviço envia um pedido CONFIRMA. Se for recebida uma resposta do Servidor, o Cliente DHCPv6 atualiza os seus parâmetros de locação com os dados recebidos.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) CONFIRMam mensagem enviada e processada com sucesso

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Send a CONFIRM message to the Server. */
status = nx_dhcpv6_request_confirm(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the CONFIRM message. */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_request_inform_request
- nx_dhcpv6_request_release
- nx_dhcpv6_request_solicit


## <a name="nx_dhcpv6_request_inform_request"></a>nx_dhcpv6_request_inform_request

Processar o estado de PEDIDO INFORM do Cliente

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_inform_request(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descrição

Este serviço envia uma mensagem INFORM REQUEST. Se uma resposta for recebida, Quando uma é recebida, a resposta é processada para determinar se é válida e o servidor concedeu o pedido. A instância do Cliente é então atualizada com as informações do servidor, conforme necessário.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) INFORM REQUEST Mensagem criada e processada com sucesso

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Send an INFORM REQUEST message to the server. */
status = nx_dhcpv6_request_inform_request(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the INFORM REQUEST 
   message and processed the reply. */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_request_confirm

## <a name="nx_dhcpv6_request_option_dns_server"></a>nx_dhcpv6_request_option_DNS_server

Adicionar servidor DNS ao pedido de opção DHCPv6

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descrição

Este serviço adiciona a opção de solicitar informações do servidor DNS ao pedido de opção DHCPv6. Se a resposta do Servidor incluir dados do servidor DNS, o Cliente armazenará o servidor DNS se tiver espaço para o fazer. O número de servidores DNS que o Cliente pode armazenar é determinado pela opção configurável NX_DHCPV6_NUM_DNS_SERVERS cujo valor padrão é 2.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) opção de servidor DNS está incluída

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Set the DNS server option in Client requests. */
nx_dhcpv6_request_option_DNS_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_time_server
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_fqdn"></a>nx_dhcpv6_request_option_FQDN

Adicionar opção de nome de domínio totalmente qualificado à lista de pedidos de opção

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_option_FQDN(NX_DHCPV6 *dhcpv6_ptr, UCHAR *domain_name, 
UINT op);
```

### <a name="description"></a>Descrição

Este serviço adiciona a opção de adicionar o Nome de Domínio Totalmente Qualificado ao pedido de opção DHCPv6. Existem três opções para a opção FQDN:

- NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR 0 Atualizar o mapeamento de endereço FQDN-iPv6 para FQDN e endereço(es) utilizado pelo Cliente.

- NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE 1 Atualizar o mapeamento de endereço FQDN-iPv6 para FQDN e endereço(es) utilizado pelo Cliente para o servidor.

- NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE 2 Solicite que o servidor não efetue atualizações DNS em nome do Cliente.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

- **domain_name** Corda segurando o nome de domínio

- **op** Tipo de opção FQDN a aplicar (ver lista acima)

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) A opção FQDN está incluída

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Set the FQDN option in Client DHCPv6 request. */
nx_dhcpv6_request_option_FQDN(&dhcp_0, “DHCPv6_Client”, 
                              NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE);
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_time_server
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_domain_name"></a>nx_dhcpv6_request_option_domain_name

Adicione a opção de nome de domínio ao pedido de opção DHCPv6

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_option_domain_name(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descrição

Este serviço adiciona a opção nome de domínio ao pedido de opção nas mensagens de pedido do Cliente. Se a resposta do Servidor incluir dados de nome de domínio, o Cliente armazenará as informações sobre o nome de domínio se o tamanho do nome de domínio estiver dentro do tamanho do tampão para manter o nome de domínio. Este tamanho tampão é uma opção configurável (NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE) com um valor padrão de 30 bytes.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) conjunto de opção de nome de domínio

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Set the domain name option in Client requests. */
nx_dhcpv6_request_option_domain_name(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_request_option_DNS_server
- nx_dhcpv6_request_option_time_server
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_time_server"></a>nx_dhcpv6_request_option_time_server

Definir dados do servidor de tempo como pedido opcional

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descrição

Este serviço adiciona a opção de informação do servidor de tempo ao pedido de opção de solicitação de mensagens de pedido do Cliente. Se a resposta do Servidor incluir dados do servidor tim, o Cliente armazenará o servidor de tempo se tiver espaço para o fazer. O número de servidores de tempo que o Cliente pode armazenar é determinado pela opção configurável

NX_DHCPV6_NUM_TIME _SERVERS cujo valor padrão é 1.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Opção de servidor de tempo adicionada

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Set the time server option in Client request messages. */
nx_dhcpv6_request_option_time_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_request_option_DNS_server
- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_timezone"></a>nx_dhcpv6_request_option_timezone

Definir dados de fuso horário como pedido opcional

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_option_timezone(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descrição

Este serviço adiciona a opção de solicitar informações de fuso horário ao pedido de opção Cliente. Se a resposta do Servidor incluir dados de fuso horário, o Cliente armazenará a informação do fuso horário se o tamanho do fuso horário estiver dentro do tamanho do tampão para manter o fuso horário. Este tamanho tampão é uma opção configurável (NX_DHCPV6_ TIME_ZONE _BUFFER_SIZE) com um valor padrão de 10 bytes.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) opção de fuso horário adicionada

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Set time zone option in Client request messages. */
nx_dhcpv6_request_option_timezone(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_request_option_DNS_server
- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_time_server

## <a name="nx_dhcpv6_request_release"></a>nx_dhcpv6_request_release

Envie uma mensagem DE LIBERTAÇÃO DHCPv6

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_release(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descrição

Este serviço envia uma mensagem RELEASE na rede Cliente. Se a mensagem for enviada com sucesso, é devolvido um estado de sucesso. Uma conclusão bem sucedida não significa que o Cliente recebeu uma resposta ou foi-lhe ainda concedido um endereço IPv6. A tarefa de thread do cliente DHCPv6 aguarda uma resposta de um Servidor DHCPv6. Se um for recebido, verifica se a resposta é válida e armazena os dados para o registo do Cliente.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Mensagem DE LIBERTAÇÃO enviada com sucesso

- **NX_DHCPV6_NOT_STARTED** (0xE92) DHCPv6 Tarefa de cliente não iniciada

- **endereço NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) não vinculado ao Cliente

- **NX_INVALID_INTERFACE** (0x4C) Não encontrados na tabela de endereços IP

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Send an RELEASE message to the Server. */
status = nx_dhcpv6_request_release(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the RELEASE message. */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_request_confirm
- nx_dhcpv6_request_inform_request
- nx_dhcpv6_request_solicit

## <a name="nx_dhcpv6_request_solicit"></a>nx_dhcpv6_request_solicit

Enviar uma mensagem SOLICIT

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_solicit(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descrição

Este serviço envia uma mensagem SOLICIT na rede. Se a mensagem for enviada com sucesso, é devolvido um estado de sucesso. Uma conclusão bem sucedida não significa que o Cliente recebeu uma resposta ou foi-lhe ainda concedido um endereço IPv6. A tarefa de thread do cliente DHCPv6 aguarda uma resposta (uma mensagem DE ANÚNCIO) de um Servidor DHCPv6. Se um for recebido, verifica se a resposta é válida, armazena os dados para o registo do Cliente e promove o Cliente ao estado REQUEST.

> [!NOTE] 
> Se a opção 'Compromisso Rápido' estiver definida, o Cliente DHCPv6 irá diretamente para o estado de Bound se receber uma mensagem de anúncio do Servidor válido. Consulte a descrição do serviço para *obter mais informações nx_dhcpv6_request_solicit_rapid.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Mensagem SOLICIT enviada com sucesso

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

## <a name="nx_dhcpv6_request_solicit_rapid"></a>nx_dhcpv6_request_solicit_rapid

Envie uma mensagem SOLICIT com a opção Rapid Commit

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_request_solicit_rapid(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descrição

Este serviço envia uma mensagem SOLICIT na rede com o conjunto de opções Rapid Commit. Se a mensagem for enviada com sucesso, é devolvido um estado de sucesso. Uma conclusão bem sucedida não significa que o Cliente recebeu uma resposta ou foi-lhe ainda concedido um endereço IPv6. A tarefa de thread do cliente DHCPv6 aguarda uma resposta (uma mensagem DE ANÚNCIO) de um Servidor DHCPv6. Se um for recebido, verifica se a resposta é válida, armazena os dados para o registo do Cliente e promove o Cliente para o estado BOUND.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Mensagem SOLICIT enviada com sucesso

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit_rapid(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_request_solicit
- nx_dhcpv6_request_confirm
- nx_dhcpv6_request_inform_request
- nx_dhcpv6_request_release

## <a name="nx_dhcpv6_resume"></a>nx_dhcpv6_resume

Retomar a tarefa do cliente DHCPv6 

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_resume(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descrição

Este serviço retoma a tarefa de thread do cliente DHCPv6. O estado atual do cliente DHCPv6 será processado (por exemplo, Ligado, Solicit)

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Cliente retomado com sucesso

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Resume the DHCPv6 Client task. */
status = nx_dhcpv6_resume(&dhcp_0);

/* If status is NX_SUCCESS the Client thread task successfully resumed. */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_start
- nx_dhcpv6_stop
- nx_dhcpv6_suspend

## <a name="nx_dhcpv6_set_-time_accrued"></a>nx_dhcpv6_set_ time_accrued

Define o tempo acumulado no contrato de arrendamento de endereços IP do Cliente

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_set_time_accrued(NX_DHCPV6 *dhcpv6_ptr,
                                ULONG time_accrued);
```

### <a name="description"></a>Descrição

Este serviço define o tempo acumulado no endereço IP global do Cliente desde que foi atribuído pelo servidor. Isto só deve ser utilizado se um Cliente estiver atualmente vinculado a um endereço IPv6 atribuído.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

- **time_accrued** Tempo acumulado no arrendamento IP

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Tempo acumulado com sucesso

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Set time accrued since client’s assigned IP address was assigned. */
status = nx_dhcpv6_set_time_accrued(&dhcp_0, time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address lease was 
   successfully set. */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_start"></a>nx_dhcpv6_start

Inicie a tarefa do Cliente DHCPv6 

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descrição

Este serviço inicia a tarefa do Cliente DHCPv6 e prepara o Cliente para executar o protocolo DHCPv6. Verifica que a instância do Cliente tem informações suficientes (como um Cliente DUID), cria e liga a tomada UDP para enviar e receber mensagens DHCPv6 e ativa os temporizadores para manter o registo do tempo de sessão e quando o atual contrato de arrendamento IPv6 expirar.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Cliente começou com sucesso

- **NX_DHCPV6_MISSING_REQUIRED_OPTIONS** (0xEA9) Cliente em falta de opções necessárias

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Start the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully started. */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_resume
- nx_dhcpv6_suspend
- nx_dhcpv6_stop
- nx_dhcpv6_reinitialize

## <a name="nx_dhcpv6_stop"></a>nx_dhcpv6_stop

Pare a tarefa do Cliente DHCPv6 

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_stop(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descrição

Este serviço interrompe a tarefa do Cliente DHCPv6 e limpa as contagens de retransmissão, intervalos máximos de retransmissão, desativa a sessão e locação dos temporizadores de validade, e desvincula a porta de tomada do Cliente DHCPv6. Para reiniciar o Cliente, é necessário parar primeiro e reinitir opcionalmente o Cliente antes de iniciar outra sessão com qualquer servidor DHCPv6. Consulte a secção Exemplo Pequeno para mais detalhes.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Cliente parou com sucesso

- **NX_DHCPV6_NOT_STARTED** (0xE92) Linha de cliente não começou

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio


### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Stop the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully stopped. */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_resume
- nx_dhcpv6_suspend
- nx_dhcpv6_reinitialize
- nx_dhcpv6_start

## <a name="nx_dhcpv6_suspend"></a>nx_dhcpv6_suspend

Suspender a tarefa do Cliente DHCPv6 

### <a name="prototype"></a>Prototype

```C
UINT nx_dhcpv6_suspend(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descrição

Este serviço suspende a tarefa do cliente DHCPv6 e qualquer pedido que tenha sido no meio do processamento. Os temporizadores são desativados e o estado do Cliente está definido para não funcionar.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6

### <a name="return-values"></a>Valores de devolução

- **cliente NX_SUCCESS** (0x00) suspenso com sucesso

- **NX_DHCPV6_NOT_STARTED** (0XE92) Cliente não em funcionamento por isso não pode ser suspenso

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Deve ser chamado de fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Suspend the DHCPv6 Client task. */
status = nx_dhcpv6_suspend(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully suspended. */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_resume
- nx_dhcpv6_start
- nx_dhcpv6_reinitialize
- nx_dhcpv6_stop
