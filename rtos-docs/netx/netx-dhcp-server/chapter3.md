---
title: Capítulo 3 - Descrição dos serviços do Servidor Azure RTOS NetX DHCP
description: Este capítulo contém uma descrição de todos os serviços do Servidor Azure RTOS NetX DHCP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 702499184b12484fa5862ba83ff3fadb8fccea31089b6bf8b71daf267e8c84a3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799528"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-server-services"></a>Capítulo 3 - Descrição dos serviços do Servidor Azure RTOS NetX DHCP

Este capítulo contém uma descrição de todos os serviços do Servidor NetX DHCP.

Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

- **nx_dhcp_server_create**: *Criar uma instância do servidor DHCP*
- **nx_dhcp_set_interface_network_parameters**: *Definir opções do Servidor DHCP para parâmetros críticos de rede para interface especificada*
- **nx_dhcp_create_server_ip_address_list:** Criar *um conjunto de endereços IP disponíveis para atribuir à interface dos clientes DHCP*
- **nx_dhcp_clear_client_record**: *Remova o registo do Cliente na base de dados do Servidor*
- **nx_dhcp_server_delete**: *Eliminar uma instância DHCPServer*
- **nx_dhcp_server_start**: *Iniciar ou retomar o processamento do Servidor DHCP*
- **nx_dhcp_server_stop**: *Parar o processamento do servidor DHCP*

## <a name="nx_dhcp_server_create"></a>nx_dhcp_server_create

Criar uma instância do Servidor DHCP

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_server_create(NX_DHCP_SERVER *dhcp_ptr, NX_IP *ip_ptr,
                        VOID *stack_ptr, ULONG stack_size,
                        CHAR *input_address_list, CHAR *name_ptr,
                        NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a>Description

Este serviço cria uma instância do Servidor DHCP com uma instância IP previamente criada.

> [!IMPORTANT]
> A aplicação deve certificar-se de que o pacote criado para o serviço ip create tem uma carga útil mínima de byte 548, não incluindo os cabeçalhos UDP, IP e Ethernet.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponter para o bloco de controlo do servidor DHCP.  
- **ip_ptr**: Indicação para a instância IP do servidor DHCP.
- **stack_ptr**: Localização da pilha do servidor do ponteiro DHCP.
- **stack_size**: Tamanho da pilha de servidor DHCP
- **input_address_list**: Ponteiro para a lista de endereços IP do Servidor
- **name_ptr**: Ponteiro para o nome do servidor DHCP
- **packet_pool_ptr**: Ponteiro para a piscina de pacotes do Servidor DHCP

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Servidor DHCP bem sucedido.
- **NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD**: (0xA9) Carga útil do pacote erro demasiado pequeno
- **NX_DHCP_NO_SERVER_OPTION_LIST**: (0x96) A lista de opções do servidor está vazia
- NX_DHCP_PARAMETER_ERROR: (0x92) Entrada inválida sem ponteiro
- NX_CALLER_ERROR: (0x11) Inválido de serviço.
- NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro.

### <a name="allowed-from"></a>Permitido a partir de

Aplicação

### <a name="example"></a>Exemplo

```c
/* Create a DHCP Server instance. */
status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                    DEMO_SERVER_STACK_SIZE, SERVER_IP_ADDRESS_LIST,
                    "DHCP server", &server_pool);

/* If status is NX_SUCCESS a DHCP Server instance was successfully created. */
```

## <a name="nx_dhcp_create_server_ip_address_list"></a>nx_dhcp_create_server_ip_address_list

Criar uma piscina de endereços IP

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_create_server_ip_address_list(NX_DHCP_SERVER *dhcp_ptr,
                            UINT iface_index, ULONG start_ip_address,
                            ULONG end_ip_address, UINT *addresses_added);
```

### <a name="description"></a>Description

Este serviço cria um conjunto específico de endereços IP disponíveis para o servidor DHCP especificado para atribuir. Os endereços IP de início e fim devem corresponder à interface de rede especificada. O número real de endereços IP adicionados pode ser inferior ao total dos endereços se a lista de endereços IP não for suficientemente grande (que é definida no parâmetro *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* configurável do utilizador).

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr** Ponteiro para o bloco de controlo do servidor DHCP.  
- **iface_index**: Índice correspondente à interface de rede
- **start_ip_address**: Primeiro endereço IP disponível
- **end_ip_address**: O último do endereço IP disponível
- **addresses_added**: Número de endereços IP adicionados à lista

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Servidor DHCP bem sucedido.
- **NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) O índice não corresponde a endereços
- **NX_DHCP_INVALID_IP_ADDRESS_LIST:**(0x99) Entrada de endereço inválido
- NX_DHCP_INVALID_IP_ADDRESS: (0x9B) Endereços ilógicos de início/fim
- NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro.

### <a name="allowed-from"></a>Permitido a partir de

Aplicação

### <a name="example"></a>Exemplo

```c
/* Create a pool of available IP addresses to assign. */
status = nx_dhcp_create_server_ip_list (&dhcp_server, iface_index,
                START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

/* If status is NX_SUCCESS aIP address list was successfully created. 
addresses_added indicates how many IP addresses were actually added to the list. */
```

## <a name="nx_dhcp_clear_client_record"></a>nx_dhcp_clear_client_record

Remova o registo do Cliente da base de dados do Servidor

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_clear_client_record (NX_DHCP_SERVER *dhcp_ptr,
                                NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a>Description

Este serviço limpa o registo do Cliente da base de dados do Servidor.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponter para o bloco de controlo do servidor DHCP.  
- **dhcp_client_ptr**: Ponteiro para o cliente DHCP para remover

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Servidor DHCP bem sucedido.
- NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro.
- NX_CALLER_ERROR: (0x11) Não thread caller of service

### <a name="allowed-from"></a>Permitido a partir de

Aplicação

### <a name="example"></a>Exemplo

```c
/* Remove Client record from the server database. */
status = nx_dhcp_clear_client_record (&dhcp_server, &dhcp_client_ptr);

/* If status is NX_SUCCESS the specified Client was removed from the database. */
```

## <a name="nx_dhcp_set_interface_network_parameters"></a>nx_dhcp_set_interface_network_parameters

Definir parâmetros de rede para opções DHCP

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_set_interface_network_parameters(NX_DHCP_SERVER *dhcp_ptr,
                                    UINT iface_index, ULONG subnet_mask,
                                    ULONG default_gateway_address,
                                    ULONG dns_server_address);
```

### <a name="description"></a>Description

Este serviço define valores predefinidos para parâmetros críticos de rede para a interface especificada. O servidor DHCP incluirá estas opções na sua OFERTA e respostas ACK ao Cliente DHCP. Se os parâmetros de interface definidos pelo anfitrião em que um servidor DHCP está em funcionamento, os parâmetros ficarão incumpridos da seguinte forma: o router definido para o gateway de interface principal para o próprio servidor DHCP, o endereço do servidor DNS para o próprio servidor DHCP e a máscara de sub-rede para a mesma que a interface do servidor DHCP está configurada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponter para o bloco de controlo do servidor DHCP.  
- **iface_index**: Índice correspondente à interface de rede
- **subnet_mask**: Máscara de sub-rede para rede cliente
- **default_gateway_address**: Endereço IP do router do cliente
- **dns_server_address**: Servidor DNS para a rede do Cliente

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Servidor DHCP bem sucedido.
- **NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) O índice não corresponde a endereços
- **NX_DHCP_INVALID_NETWORK_PARAMETERS:**(0xA3) Parâmetros de rede inválidos
- NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro.

### <a name="allowed-from"></a>Permitido a partir de

Aplicação

### <a name="example"></a>Exemplo

```c
/* Set network parameters for a specific interface. */
status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                                    NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                                    IP_ADDRESS(10,0,0,1));

/* If status is NX_SUCCESS network parameters were successfully set. */
```

## <a name="nx_dhcp_server_delete"></a>nx_dhcp_server_delete

Excluir uma instância do Servidor DHCP

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_server_delete(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Description

Este serviço elimina uma instância do Servidor DHCP previamente criada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para uma instância do Servidor DHCP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Servidor DHCP bem sucedido.
- NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro.
- NX_DHCP_PARAMETER_ERROR: (0x92) Entrada inválida sem ponteiro
- NX_CALLER_ERROR: (0x11) Inválido de serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Delete a DHCP Server instance. */
status = nx_dhcp_server_delete(&dhcp_server);  
  
/* If status is NX_SUCCESS the DHCP Server instance was successfully deleted. */
```

## <a name="nx_dhcp_server_start"></a>nx_dhcp_server_start

Iniciar o processamento do servidor DHCP

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_server_start(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Description

Este serviço inicia o processamento do Servidor DHCP, que inclui a criação de uma tomada UDP de servidor, ligação da porta DHCP e espera receber os pedidos do Cliente DHCP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Início do Servidor de Sucesso.  
- **NX_DHCP_ALREADY_STARTED**: (0x93) DHCP já começou.
- NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro.
- NX_CALLER_ERROR: (0x11) Inválido de serviço.
- NX_DHCP_PARAMETER_ERROR: (0x92) Entrada inválida sem ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Start the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_start(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

### <a name="see-also"></a>Consulte também

nx_dhcp_create, nx_dhcp_delete, nx_dhcp_release, nx_dhcp_state_change_notify, nx_dhcp_stop, nx_dhcp_user_option_retrieve nx_dhcp_user_option_convert

## <a name="nx_dhcp_server_stop"></a>nx_dhcp_server_stop

Para o processamento do servidor DHCP

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Description

Este serviço impede o processamento do Servidor DHCP, que inclui receber pedidos do Cliente DHCP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Indicação para a instância do servidor DHCP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Paragem DHCP bem sucedida.
- **NX_DHCP_ALREADY_STARTED**: (0x93) DHCP já começou.
- NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro.
- NX_CALLER_ERROR: (0x11) Inválido de serviço.
- NX_DHCP_PARAMETER_ERROR: (0x92) Entrada inválida sem ponte.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Stop the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_stop(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
