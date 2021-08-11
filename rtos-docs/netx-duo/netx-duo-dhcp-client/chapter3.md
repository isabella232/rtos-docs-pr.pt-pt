---
title: Capítulo 3 - Descrição dos serviços de clientes Azure RTOS NetX Duo DHCP
description: Este capítulo contém uma descrição de todos os serviços de clientes Azure RTOS NetX Duo DHCP (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9c678772b6e6160dba9929af41e76c2580c06fb163bfccfdb6fcc46fa42ade82
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790348"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dhcp-client-services"></a>Capítulo 3 - Descrição dos serviços de clientes Azure RTOS NetX Duo DHCP

Este capítulo contém uma descrição de todos os serviços de clientes Azure RTOS NetX Duo DHCP (listados abaixo) por ordem alfabética.

Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

- **nx_dhcp_create**: *Criar uma instância DHCP*
- **nx_dhcp_clear_broadcast_flag**: *Clara bandeira de transmissão nas mensagens do Cliente*
- **nx_dhcp_delete**: *Eliminar uma instância DHCP*
- **nx_dhcp_force_renew**: *Enviar uma mensagem de renovação de força*
- **nx_dhcp_packet_pool_set**: *Definir a piscina de pacotes do cliente DHCP*
- **nx_dhcp_decline**: Enviar *mensagem de recusa para o servidor*
- **nx_dhcp_release**: Enviar *mensagem de desbloqueio para o servidor*
- **nx_dhcp_reinitialize**: *Claros parâmetros da rede de clientes DHCP*
- **nx_dhcp_request_client_ip**: *Especifique um endereço IP específico*
- **nx_dhcp_send_request**: *Enviar mensagem DHCP para o servidor*
- **nx_dhcp_start**: *Inicie o processamento do cliente DHCP*
- **nx_dhcp_stop**: *Parar o processamento do cliente DHCP*
- **nx_dhcp_set_interface_index**: *Desa cos um pouco de interface para executar o Cliente DHCP*
- **nx_dhcp_server_address_get**: *Obtenha o endereço IP do servidor DHCP*
- **nx_dhcp_state_change_notify**: *Desa esta medida de chamada quando o estado do DHCP mudar*
- **nx_dhcp_user_option_retrieve**: *Recuperar a opção DHCP especificada*
- **nx_dhcp_user_option_convert**: *Converter quatro bytes para ULONG*

Serviços de clientes dHCP específicos da interface:
 
- **nx_dhcp_interface_clear_broadcast_flag**: *Clara bandeira de transmissão nas mensagens do Cliente na interface especificada*
- **nx_dhcp_interface_enable**: *Permitir que a interface execute o DHCP na interface especificada*
- **nx_dhcp_interface_disable**: *Desative a interface para executar o DHCP na interface especificada*
- **nx_dhcp_interface_decline**: *Enviar mensagem de declínio para o servidor na interface especificada*
- **nx_dhcp_interface_force_renew**: *Enviar uma mensagem de renovação de força na interface especificada*
- **nx_dhcp_interface_reinitialize**: *Limpar os parâmetros da rede de clientes DHCP na interface especificada*
- **nx_dhcp_interface_release**: *Enviar mensagem de desbloqueio para o servidor na interface especificada*
- **nx_dhcp_interface_request_client_ip**: *Especifique um endereço IP específico na interface especificada*
- **nx_dhcp_interface_send_request**: *Enviar mensagem DHCP para o servidor na interface especificada*
- **nx_dhcp_interface_server_address_get**: *Obtenha o endereço IP do servidor DHCP na interface especificada*
- **nx_dhcp_interface_start**: *Inicie o processamento do Cliente DHCP na interface especificada*
- **nx_dhcp_interface_stop**: *Parar o processamento do Cliente DHCP na interface especificada*
- **nx_dhcp_interface_state_change_notify**: *Desa esta medida de chamada quando o estado de DHCP mudar na interface especificada*
- **nx_dhcp_interface_user_option_retrieve**: *Recuperar a opção DHCP especificada na interface especificada*

Serviços ao cliente DAHCP se NX_DHCP_CLIENT_RESORE_STATE estiver definido:

- **nx_dhcp_resume**: *Retomar estado de cliente DHCP previamente estabelecido*
- **nx_dhcp_suspend**: *Suspender o processamento do estado do cliente DHCP*
- **nx_dhcp_client_get_record**: *Criar um registo do estado do cliente DHCP*
- **nx_dhcp_client_restore_record**: *Restaurar um registo previamente guardado para o Cliente DHCP*
- **nx_dhcp_client_update_time_remaining**: *Atualizar o tempo que resta no estado atual do DHCP*

Serviços específicos do cliente DHCP de interface se NX_DHCP_CLIENT_RESORE_STATE for definido:

- **nx_dhcp_client_interface_get_record**: *Criar um registo do estado do Cliente DHCP na interface especificada*
- **nx_dhcp_client_interface_restore_record**: *Restaurar um registo previamente guardado para o Cliente DHCP na interface especificada*
- **nx_dhcp_client_interface_update_time_remaining**: *Atualizar o tempo restante no estado dhcp atual na interface especificada*

## <a name="nx_dhcp_create"></a>nx_dhcp_create

Criar uma instância DHCP

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_create(NX_DHCP *dhcp_ptr, NX_IP *ip_ptr, CHAR *name_ptr);
```

### <a name="description"></a>Description

Este serviço cria uma instância DHCP para a instância IP previamente criada. Por predefinição, a interface primária está ativada para executar o DHCP. A entrada de nomes, embora não utilizada na implementação do NetX Duo do Cliente DHCP, deve seguir os critérios RFC 1035 para os nomes dos anfitriões. O comprimento total não deve exceder 255 caracteres, as etiquetas separadas por pontos devem começar com uma letra, e terminar com uma letra ou número, e podem conter hífens, mas nenhum outro carácter não alfanumérico.

Se a aplicação quiser executar a DHCP outra interface registada com a instância IP (utilizando *nx_ip_interface_attach),* a aplicação pode chamar *nx_dhcp_set_interface_index* para executar o DHCP apenas nessa interface, ou *nx_dhcp_interface_enable* para executar DHCP nessa interface também. Consulte a descrição destes serviços para mais detalhes.

>[!NOTE]
> A aplicação deve certificar-se de que a carga útil do pacote do cliente DHCP pode suportar o tamanho mínimo da mensagem DHCP especificado pela Secção 2 (548 bytes de dados de mensagens DHCP mais cabeçalhos de estrutura de UDP, IP e rede física).

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para o bloco de controlo DHCP. 
- **ip_ptr**: Ponteiro para instância IP previamente criada.  
- **name_ptr**: Ponteiro para o nome de anfitrião para a instância DHCP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Cria o DHCP com sucesso
- **NX_DHCP_INVALID_NAME:**(0xA8) Nome de anfitrião inválido
- **NX_DHCP_INVALID_PAYLOAD**: (0x9C) Carga útil demasiado pequena para a mensagem DHCP
- NX_PTR_ERROR: (0x16) Ponteiro IP inválido ou DHCP

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Create a DHCP instance.  */
status =  nx_dhcp_create(&my_dhcp, &my_ip, "My-DHCP");

/* If status is NX_SUCCESS a DHCP instance was successfully created.  */
```

## <a name="nx_dhcp_interface_enable"></a>nx_dhcp_interface_enable

Permitir que a interface especificada execute o DHCP 

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_interface_enable(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>Description

Este serviço permite a interface especificada para a execução do DHCP. Por predefinição, a interface primária está ativada para o Cliente DHCP. Neste momento, o DHCP pode ser iniciado nesta interface, quer chamando *nx_dhcp_interface_start,* quer para iniciar o DHCP em todas as interfaces ativadas *nx_dhcp_start*.

>[!NOTE] 
> A aplicação deve primeiro registar esta interface com a instância IP, utilizando *nx_ip_interface_attach.*

Além disso, deve existir um 'registo' de interface do Cliente DHCP disponível para adicionar esta interface à lista de interfaces ativadas. Por predefinição, NX_DHCP_CLIENT_MAX_RECORDS é definido para 1. Desa esta opção para o número máximo de interfaces que se espera que sejam executadas em simultâneo com o Cliente DHCP. Normalmente, NX_DHCP_CLIENT_MAX_RECORDS será igual a NX_MAX_PHYSICAL_INTERFACES; no entanto, se um dispositivo tiver mais interfaces físicas do que espera executar o Cliente DHCP, pode guardar a memória definindo NX_DHCP_CLIENT_MAX_RECORDS para menos do que esse número. Não há um para um mapeamento de interfaces físicas com registos de interface do Cliente DHCP.

A diferença entre este serviço e *nx_dhcp_set_interface_index* é que este último define apenas uma interface única para executar DHCP, enquanto este serviço simplesmente adiciona a interface especificada à lista de interfaces do Cliente ativadas para DHCP.

Para desativar uma interface para DHCP, a aplicação pode chamar o

*nx_dhcp_interface_disable* serviço.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para o bloco de controlo DHCP.  
- **interface_index**: Índice de interface para permitir a DHCP em

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Ativar o DHCP com sucesso
- **NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) Não há registo disponível para outra Interface a ser ativada para o DHCP
- **NX_DHCP_INTERFACE_ALREADY_ENABLED:** Interface (0xA3) ativada para DHCP
- NX_PTR_ERROR: (0x16) Ponteiro IP inválido ou DHCP
- NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Enable DHCP on a secondary interface. It is already enabled on the primary 
   interface.  NX_DHCP_CLIENT_MAX_RECORDS is set to 2. */

status =  nx_dhcp_interface_enable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface was successfully enabled.  */


status = nx_dhcp_start(&my_dhcp);
/* If status is NX_SUCCESS DHCP is running on interface 0 and 1.  */
```

## <a name="nx_dhcp_interface_disable"></a>nx_dhcp_interface_disable

Desative a interface especificada para executar o DHCP 

### <a name="prototype"></a>Prototype

```c

UINT nx_dhcp_interface_disable(NX_DHCP *dhcp_ptr, 
                               UINT interface_index);
```

### <a name="description"></a>Description

Este serviço desativa a interface especificada para a execução do DHCP. Reinicia o Cliente DHCP nesta interface.

Para reiniciar o Cliente DHCP, a aplicação deve voltar a ativar a interface utilizando *nx_dhcp_interface_enable* e reiniciar o DHCP chamando *nx_dhcp_interface_start*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para o bloco de controlo DHCP.  
- **interface_index**: Índice de interface para desativar o DHCP

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Cria o DHCP com sucesso
- **NX_DHCP_INTERFACE_NOT_ENABLED:** Interface (0xA4) não ativada para DHCP
- NX_PTR_ERROR: (0x16) Ponteiro IP inválido ou DHCP
- NX_CALLER_ERROR: (0x11) Inválido deste serviço
- NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Disable DHCP on a secondary interface. */

status =  nx_dhcp_interface_disable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface is successfully disabled.  */
```
## <a name="nx_dhcp_clear_broadcast_flag"></a>nx_dhcp_clear_broadcast_flag

Definir a bandeira de transmissão DHCP

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_clear_broadcast_flag(NX_DHCP *dhcp_ptr, UINT clear_flag);
```

### <a name="description"></a>Description

Este serviço define ou limpa a bandeira de transmissão o cabeçalho de mensagem DHCP para todas as interfaces ativadas para DHCP. Para algumas mensagens DHCP (por exemplo, DISCOVER) a bandeira de transmissão está definida para ser transmitida porque o Cliente não tem um endereço IP.

clear_flag valores: 

- **NX_TRUE:** a bandeira de radiodifusão é apurada (pedido de resposta unicast)
- **NX_FALSE:** é definida a bandeira de radiodifusão (pedido de resposta transmitida)

Este serviço destina-se a Clientes DHCP que devem passar por um router para chegar ao Servidor DHCP, onde o router rejeita o encaminhamento de mensagens de transmissão.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para bloco de controlo DHCP  
- **clear_flag**: Valor para definir a bandeira de transmissão

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Com sucesso colocar a bandeira
- NX_PTR_ERROR: (0x16) Ponteiro IP inválido ou DHCP

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a  
    unicast response).  */
status =  nx_dhcp_clear_broadcast_flag(&my_dhcp, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated.  */
```

## <a name="nx_dhcp_interface_clear_broadcast_flag"></a>nx_dhcp_interface_clear_broadcast_flag

Desmarcar ou limpar a bandeira de transmissão na interface especificada

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_interface_clear_broadcast_flag(NX_DHCP *dhcp_ptr, 
                                            UINT interface_index, 
                                            UINT clear_flag);
```

### <a name="description"></a>Description

Este serviço permite que a aplicação do anfitrião do cliente DHCP desempecifique ou limpe a bandeira de transmissão nas mensagens do Cliente DHCP para o Servidor DHCP na interface especificada. Para mais detalhes, **consulte nx_dhcp_clear_broadcast_flag.**

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para bloco de controlo DHCP
- **interface_index**: Índice de interface para definir a bandeira de transmissão
- **clear_flag**: Valor para definir a bandeira de transmissão

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Com sucesso colocar a bandeira
- **NX_DHCP_INTERFACE_NOT_ENABLED:** Interface (0xA4) não ativada para DHCP
- NX_PTR_ERROR: (0x16) Ponteiro IP inválido ou DHCP
- NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a 
   unicast response) on a previously attached secondary interface.  */

iface_index = 1;

status =  nx_dhcp_interface_clear_broadcast_flag(&my_dhcp, iface_index, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated.  */
```

## <a name="nx_dhcp_delete"></a>nx_dhcp_delete

Eliminar uma instância DHCP

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_delete(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Description

Este serviço elimina uma instância DHCP previamente criada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Eliminar o DHCP com sucesso.
- NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Delete a DHCP instance.  */
status =  nx_dhcp_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCP instance was successfully deleted.  */
```

## <a name="nx_dhcp_-force_renew"></a>nx_dhcp_ force_renew

Enviar uma mensagem de renovação de força 

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp force_renew(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Description

Este serviço permite que a aplicação do anfitrião envie uma mensagem de renovação de força em todas as interfaces ativadas para DHCP. O Cliente DHCP deve estar num estado vinculado. Esta função define o estado para RENOVAR de modo a que o Cliente DHCP tente renovar antes que o tempo limite T1 expire.

Para enviar uma renovação de força numa interface específica quando várias interfaces estiverem habilitados a DHCP, utilize *nx_dhcp_interface_force_renew*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Enviou com sucesso a renovação da força.
- **NX_DHCP_NOT_BOUND:**(0x94) endereço IP do cliente não vinculado.  
- NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Send a force renew message from the Client.  */
status =  nx_dhcp_force_renew(&my_dhcp);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired.  */
```

## <a name="nx_dhcp_interface_force_renew"></a>nx_dhcp_interface_force_renew

Envie uma mensagem de renovação de força na interface especificada

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_interface_force_renew(NX_DHCP *dhcp_ptr, 
                                   UINT interface_index);
```

### <a name="description"></a>Description

Este serviço permite que a aplicação anfitriã envie uma mensagem de renovação de força na interface de entrada, desde que essa interface tenha sido ativada para DHCP (ver *nx_dhcp_interface_enable).* O Cliente DHCP na interface especificada deve estar num estado VINculado. Esta função define o estado para RENOVAR de modo a que o Cliente DHCP tente renovar antes que o tempo limite T1 expire.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Enviou com sucesso a renovação da força.  
- **NX_DHCP_INTERFACE_NOT_ENABLED:** Interface (0xA4) não ativada para DHCP
- NX_PTR_ERROR: (0x16) Ponteiro IP inválido ou DHCP
- NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Send a force renew message to the server on interface 1.  */
status =  nx_dhcp_interface_force_renew(&my_dhcp, 1);


/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired.  */
```

## <a name="nx_dhcp_packet_pool_set"></a>nx_dhcp_packet_pool_set

Desa estaladiço do cliente DHCP

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_packet_pool_set(NX_DHCP *dhcp_ptr, NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a>Description

Este serviço permite que a aplicação crie o pool de pacotes do Cliente DHCP, passando um ponteiro para um pacote de pacotes previamente criado nesta chamada de serviço. Para utilizar esta funcionalidade, a aplicação do anfitrião deve definir NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL. Quando definido, o serviço *nx_dhcp_create* não criará a piscina de pacotes do Cliente. 

>[!NOTE] 
> A aplicação é recomendada para usar os valores padrão para a carga útil do pacote de cliente DHCP, definida como NX_DHCP_PACKET_PAYLOAD em *nxd_dhcp_client.h* ao criar o pool de pacotes.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para o bloco de controlo DHCP.  
- **packet_pool_ptr**: Ponteiro para piscina de pacotes previamente criada

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) DhCP Pacote de pacotes de clientes está definido
- **NX_NOT_ENABLED**: (0x14) O serviço não está ativado
- NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido
- NX_DHCP_INVALID_PAYLOAD: (0x9C) A carga útil é muito pequena

### <a name="allowed-from"></a>Permitido a partir de

Código de aplicação

### <a name="example"></a>Exemplo

```c
/* Create the packet pool. */
status =  nx_packet_pool_create(&dhcp_pool, "DHCP Client Packet Pool", 
                                 NX_DHCP_PACKET_PAYLOAD, pointer, 
                                 (15 * NX_DHCP_PACKET_PAYLOAD));

/* Create the DHCP Client. */
status =  nx_dhcp_create(&dhcp_0, &ip_0, "janetsdhcp1");

/* Set the DHCP Client packet pool.  */
status =  nx_dhcp_packet_pool_set(&my_dhcp, packet_pool_ptr);
/* If status is NX_SUCCESS packet pool was successfully set.  */

```

## <a name="nx_dhcp_request_client_ip"></a>nx_dhcp_request_client_ip

Definir endereço IP solicitado para instância DHCP

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_request_client_ip(NX_DHCP *dhcp_ptr, 
                               ULONG client_ip_address, 
                               UINT skip_discover_message);
```

### <a name="description"></a>Description

Este serviço define o endereço IP para o Cliente DHCP solicitar a partir do Servidor DHCP na primeira interface ativada para DHCP no registo do Cliente DHCP. Se a bandeira *skip_discover_message* estiver definida, o Cliente DHCP ignora a mensagem Discover e envia uma mensagem De pedido.

Para definir o pedido de um IP específico para mensagens DHCP numa interface específica, utilize o serviço *nx_dhcp_interface_request_client_ip.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para o bloco de controlo DHCP.  
- **client_ip_address**: Endereço IP a pedido do servidor DHCP
- **skip_discover_message:** 
    - Se for verdade, o Cliente DHCP envia mensagem de pedido
    - Se for falso, envia a mensagem Discover.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Está definido o endereço IP solicitado.
- NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido
- NX_DHCP_INVALID_IP_REQUEST: (0x9D) endereço IP NUDO solicitado

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Set the DHCP Client requested IP address and skip the discover message.  */

status =  nx_dhcp_request_client_ip(&my_dhcp, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set.  */

```

## <a name="nx_dhcp_interface_request_client_ip"></a>nx_dhcp_interface_request_client_ip

Definir endereço IP solicitado para instância DHCP em interface especificada

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_interface_request_client_ip(NX_DHCP *dhcp_ptr, UINT  interface_index, 
                                         ULONG client_ip_address, UINT skip_discover_message);
```

### <a name="description"></a>Description

Este serviço define o endereço IP para o Cliente DHCP solicitar a partir do Servidor DHCP na interface especificada, se essa interface estiver ativada para DHCP (ver *nx_dhcp_interface_enable*). Se a bandeira *skip_discover_message* estiver definida, o Cliente DHCP ignora a mensagem Discover e envia uma mensagem De pedido.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para o bloco de controlo DHCP.
- **Interface_index**: Índice de interface para solicitar endereço IP em
- **client_ip_address**: Endereço IP a pedido do servidor DHCP
- **skip_discover_message**: Se for verdade, o Cliente DHCP envia mensagem de pedido; senão envia a mensagem Discover.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Está definido o endereço IP solicitado.
- **NX_DHCP_INTERFACE_NOT_ENABLED:** Interface (0xA4) não ativada para DHCP
- NX_PTR_ERROR: (0x16) Ponteiro IP inválido ou DHCP
- NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Set the DHCP Client requested IP address and skip the discover message on  
   interface 0.  */
status =  nx_dhcp_interface_request_client_ip(&my_dhcp, 0, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set.  */
```

## <a name="nx_dhcp_reinitialize"></a>nx_dhcp_reinitialize

Limpe os parâmetros da rede de clientes DHCP 

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_reinitialize(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Description

Este serviço limpa os parâmetros da rede de aplicações do anfitrião (endereço IP, endereço de rede e máscara de rede) e limpa o estado do Cliente DHCP em todas as interfaces ativadas para DHCP. É utilizado em combinação com *nx_dhcp_stop* e *nx_dhcp_start* para "reiniciar" a máquina estatal DHCP:

```c
nx_dhcp_stop(&my_dhcp);
nx_dhcp_reinitialize(&my_dhcp);
nx_dhcp_start(&my_dhcp);
```

Para reinitializar o Cliente DHCP numa interface específica quando várias interfaces estiverem ativadas para DHCP, utilize o serviço *nx_dhcp_interface_reinitialize.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) DHCP reinibida com sucesso 
- NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Reinitialize the previously started DHCP client.  */
status =  nx_dhcp_reinitialize(&my_dhcp);

/* If status is NX_SUCCESS the host application successfully reinitialized its network parameters and DHCP client state. */
```

## <a name="nx_dhcp_interface_reinitialize"></a>nx_dhcp_interface_reinitialize

Limpe os parâmetros da rede de clientes DHCP na interface especificada 

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_interface_reinitialize(NX_DHCP *dhcp_ptr, 
                                     UINT interface_index);
```

### <a name="description"></a>Description

Este serviço limpa os parâmetros de rede (endereço IP, endereço de rede e máscara de rede) na interface especificada se essa interface estiver ativada para DHCP (ver *nx_dhcp_interface_enable*). Consulte *nx_dhcp_reinitialize* para mais detalhes.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para a instância DHCP previamente criada
- **interface_index**: Índice de interface para reinitializar

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Interface reinicializada com sucesso
- **NX_DHCP_INTERFACE_NOT_ENABLED:** Interface (0xA4) não ativada para DHCP
- NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.
- NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Reinitialize the previously started DHCP client on interface 1.  */
status =  nx_dhcp_interface_reinitialize(&my_dhcp, 1);

/* If status is NX_SUCCESS the host application successfully reinitialized its network parameters and DHCP client state. */
```

## <a name="nx_dhcp_release"></a>nx_dhcp_release

Liberação de endereço IP alugado

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_release(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Description

Este serviço liberta o endereço IP obtido a partir de um servidor DHCP enviando a mensagem RELEASE para esse servidor. Em seguida, reinicia o cliente DHCP. Este serviço é aplicado a todas as interfaces ativadas para DHCP.

A aplicação pode reiniciar o Cliente DHCP chamando *nx_dhcp_start*.

Para libertar um endereço de volta para o servidor DHCP numa interface específica, utilize o serviço *nx_dhcp_interface_release*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Libertação bem sucedida do DHCP.  
- **NX_DHCP_NOT_BOUND**: (0x94) O endereço IP não foi arrendado, pelo que não pode ser lançado.
- NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Release the previously leased IP address.  */
status =  nx_dhcp_release(&my_dhcp);

/* If status is NX_SUCCESS the previous IP lease was successfully released.  */
```

## <a name="nx_dhcp_interface_release"></a>nx_dhcp_interface_release

Liberar endereço IP na interface especificada

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_interface_release(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>Description

Este serviço liberta o endereço IP obtido a partir de um servidor DHCP na interface especificada e reinicia o Cliente DHCP. O Cliente DHCP pode ser reiniciado chamando *nx_dhcp_start*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Libertação bem sucedida do DHCP.
- **NX_DHCP_INTERFACE_NOT_ENABLED:** Interface (0xA4) não ativada para DHCP
- **NX_DHCP_NOT_BOUND**: (0x94) O endereço IP não foi arrendado, pelo que não pode ser lançado.
- NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.
- NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Release the previously leased IP address on interface 1.  */
status =  nx_dhcp_interface_release(&my_dhcp, 1);

/* If status is NX_SUCCESS the previous IP lease was successfully released.  */
```

## <a name="nx_dhcp_decline"></a>nx_dhcp_decline

Recuse o endereço IP do Servidor DHCP

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_decline(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Description

Este serviço declina um endereço IP alugado a partir do servidor DHCP em todas as interfaces ativadas para DHCP. Se NX_DHCP_CLIENT_ SEND_ ARP_PROBE estiver definido, o Cliente DHCP enviará uma mensagem DECLINE se detetar que o endereço IP já está a ser utilizado. Consulte **as sondas ARP** no Capítulo Um para obter mais informações sobre a configuração da sonda ARP no Cliente DHCP da NetX Duo.

A aplicação pode usar este serviço para recusar o seu endereço IP se descobrir que o endereço está a ser utilizado por outros meios.

Este serviço reinicia o Cliente DHCP para que possa ser reiniciado chamando *nx_dhcp_start*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Declínio enviado com sucesso  
- **NX_DHCP_NOT_BOUND:**(0x94) Cliente DHCP não vinculado
- NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido
- NX_CALLER_ERROR: (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c

/* Decline the IP address offered by the DHCP server.  */
status =  nx_dhcp_decline(&my_dhcp);

/* If status is NX_SUCCESS the previous IP address decline message was successfully trasnmitted.  */
```

## <a name="nx_dhcp_interface_decline"></a>nx_dhcp_interface_decline

Recuse o endereço IP do Servidor DHCP na interface especificada

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_interface_decline(NX_DHCP *dhcp_ptr, 
                               UINT interface_index);
```

### <a name="description"></a>Description

Este serviço envia a mensagem DECLINar para o servidor para recusar um endereço IP atribuído pelo servidor DHCP. Também reinicia o Cliente DHCP. Consulte *nx_dhcp_decline* para mais detalhes.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.
- **Interface_index**: Índice de interface para recusar endereço IP

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Mensagem de declínio dhcp enviada  
- **NX_DHCP_NOT_BOUND:**(0x94) Cliente DHCP não vinculado
- **NX_DHCP_INTERFACE_NOT_ENABLED:** Interface (0xA4) não ativada para DHCP
- NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.
- NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Decline the IP address offered by the DHCP server on interface 2.  */
status =  nx_dhcp_interface_decline(&my_dhcp, 2);

/* If status is NX_SUCCESS the previous IP address decline message was successfully trasnmitted.  */
```
## <a name="nx_dhcp_send_request"></a>nx_dhcp_send_request

Enviar mensagem DHCP para o Servidor

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_send_request(NX_DHCP *dhcp_ptr, UINT dhcp_message_type);

```

### <a name="description"></a>Description

Este serviço envia a mensagem DHCP especificada para o servidor DHCP na primeira interface ativada para DHCP encontrada no registo do Cliente DHCP. Para enviar uma mensagem RELEASE ou DECLINar, a aplicação deve utilizar os serviços *nx_dhcp[_interface]_release*() ou *nx_dhcp_interface_decline()* respectivamente.

O Cliente DHCP deve ser iniciado a utilizar este serviço, exceto para enviar o tipo de mensagem INFORM_REQUEST.

>[!NOTE]
> Este serviço não se destina à aplicação de anfitrião para 'conduzir' a máquina estatal dhcp Client.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para o bloco de controlo DHCP.  
- **dhcp_message_type**: Pedido de mensagem (definido em *nxd_dhcp_client.h)*

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Mensagem DHCP enviada  
- **NX_DHCP_NOT_STARTED:**(0x96) Índice de interface inválido
- **NX_DHCP_INVALID_MESSAGE:**(0x9B) Tipo de mensagem inválida para enviar
- NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Send the DHCP INFORM REQUEST message to the server.  */

status =  nx_dhcp_send_request(&my_dhcp, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent.  */
```

## <a name="nx_dhcp_interface_send_request"></a>nx_dhcp_interface_send_request

Envie mensagem DHCP para o Servidor numa interface específica

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_interface_send_request(NX_DHCP *dhcp_ptr, 
                                    UINT interface_index, 
                                    UINT dhcp_message_type);
```

### <a name="description"></a>Description

Este serviço envia uma mensagem para o servidor DHCP na interface especificada se essa interface estiver ativada para DHCP. Para enviar uma mensagem RELEASE ou DECLINar, a aplicação deve utilizar os serviços *nx_dhcp[_interface]_release*() ou *nx_dhcp_interface_decline()* respectivamente.

O Cliente DHCP deve ser iniciado a utilizar este serviço, exceto para o envio do tipo de mensagem DHCP INFORM REQUEST.

Este serviço não se destina à aplicação de anfitrião para 'conduzir' a máquina estatal dhcp Client.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para o bloco de controlo DHCP.
- **Interface_index**: Índice de interface para enviar mensagem
- **dhcp_message_type**: Pedido de mensagem (definido em nxd_dhcp_client.h)

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Mensagem DHCP enviada  
- **NX_DHCP_NOT_STARTED:**(0x96) Índice de interface inválido
- **NX_DHCP_INVALID_MESSAGE:**(0x9B) Tipo de mensagem inválida para enviar
- **NX_DHCP_INTERFACE_NOT_ENABLED:** Interface (0xA4) não ativada para DHCP
- NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.
- NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Send the INFORM REQUEST message to the server on the primary interface.  */

status =  nx_dhcp_interface_send_request(&my_dhcp, 0, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent.  */
```

## <a name="nx_dhcp_server_address_get"></a>nx_dhcp_server_address_get

Obtenha o endereço IP do servidor DHCP do cliente DHCP

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_server_address_get(NX_DHCP *dhcp_ptr, 
                                ULONG server_address);
```

### <a name="description"></a>Description

Este serviço recupera o endereço IP do servidor DHCP do cliente DHCP dhCP na primeira interface ativada para DHCP encontrado no registo do Cliente DHCP. O chamador só pode utilizar este serviço depois de o Cliente DHCP estar ligado a um endereço IP atribuído pelo Servidor DHCP. A aplicação de anfitrião pode usar o serviço *nx_ip_status_check* para verificar se o endereço IP está definido, ou pode usar o *nx _dhcp_state_change_notify* e consultar o estado do Cliente DHCP é NX_DHCP_STATE_BOUND. Consulte *nx_dhcp_state_change_notify* para obter mais detalhes sobre a definição da função de retorno de mudança de estado.

Para encontrar o servidor DHCP numa interface específica quando várias interfaces estiverem ativadas para o Cliente DHCP, utilize o serviço *nx_dhcp_interface_server_address_get*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para o bloco de controlo DHCP.
- **server_address**: Ponteiro para o endereço IP do servidor

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) endereço do servidor DHCP devolvido
- **NX_DHCP_NO_INTERFACES_ENABLED:**(0xA5) Não há interfaces ativadas para o DHCP
- NX_PTR_ERROR: (0x16) Ponteiro de entrada inválido
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Use the state change notify service to determine the Client transition to the bound state and get its DHCP server IP address.*/

void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{
ULONG server_address;
UINT  status;

/* Increment state changes counter.  */
state_changes++;

if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
        {
            status = nx_dhcp_server_address_get(&dhcp_0, &server_address);
        }

}
```

## <a name="nx_dhcp_interface_server_address_get"></a>nx_dhcp_interface_server_address_get

Obtenha o endereço IP do servidor DHCP do cliente DHCP na interface especificada

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_interface_server_address_get(NX_DHCP *dhcp_ptr, 
                                          UINT interface_index,
                                          ULONG server_address);
```

### <a name="description"></a>Description

Este serviço recupera o endereço IP do servidor DHCP do cliente DHCP dhCP na interface especificada se essa interface estiver ativada para DHCP. O Cliente DHCP deve estar no estado de Bound. Depois de iniciar o Cliente DHCP nessa interface, a aplicação anfitriã pode utilizar o serviço *nx_ip_status_check* para verificar se o endereço IP está definido, ou pode usar a chamada de alteração do estado do cliente DHCP e consultar o estado do Cliente DHCP é NX_DHCP_STATE_BOUND. Consulte *nx_dhcp_state_change_notify* para obter mais detalhes sobre a definição da função de retorno de mudança de estado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para o bloco de controlo DHCP.
- **Interface_index**: Índice de interface para obter endereço IP
- **server_address**: Ponteiro para o endereço IP do servidor

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) endereço do servidor DHCP devolvido
- **NX_DHCP_NO_INTERFACES_ENABLED:**(0xA5) Não há interfaces ativadas para o DHCP
- **NX_DHCP_NOT_BOUND:**(0x94) Cliente DHCP não vinculado
- NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.
- NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. */

void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter.  */
state_changes++;

/* Get the DHCP server IP address on interface 1 */
if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
        {
         status = nx_dhcp_interface_server_address_get(&dhcp_0, 1, 
                                                       &server_address);
        }
}
```

## <a name="nx_dhcp_set_interface_index"></a>nx_dhcp_set_interface_index

Definir interface de rede para a instância DHCP

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_set_interface_index(NX_DHCP *dhcp_ptr, UINT index);
```

### <a name="description"></a>Description

Este serviço define a interface de rede para a instância DHCP ligar ao Servidor DHCP quando executa o Cliente DHCP configurado para uma única interface de rede.

Por predefinição, o Cliente DHCP funciona na interface primária. Para executar o DHCP num serviço secundário, utilize este serviço para definir a interface secundária como interface do Cliente DHCP. O pedido deve registar previamente a interface especificada para a instância IP utilizando o serviço *nx_ip_interface_attach.*

>[!NOTE]
> Este serviço destina-se a aplicações que pretendam executar o Cliente DHCP numa única interface. Para executar DHCP em várias interfaces consulte *nx_dhcp_interface_enable* para obter mais detalhes.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para o bloco de controlo DHCP.  
- **índice**: Índice da interface da rede de dispositivos

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) A interface está definida com sucesso.
- **NX_INVALID_INTERFACE:**(0x4C) Interface de rede inválida
- **NX_DHCP_INTERFACE_ALREADY_ENABLED:** Interface (0xA3) ativada para DHCP
- **NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) Não há registo disponível para outro 
- NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Set the DHCP Client interface to the secondary interface (index 1).  */
status =  nx_dhcp_set_interface_index(&my_dhcp, 1);
/* If status is NX_SUCCESS a DHCP interface was successfully set.  */
```

## <a name="nx_dhcp_start"></a>nx_dhcp_start

Iniciar o processamento do DHCP

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_start(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Description

Este serviço inicia o processamento de DHCP em todas as interfaces ativadas para DHCP. Por predefinição, a interface primária é ativada para DHCP quando a aplicação *nx_dhcp_create.*

Para verificar quando a instância IP está ligada a um endereço IP na interface do Cliente DHCP, utilize *nx_ip_status_check* para ver confirmar se o endereço IP é válido.

Se existirem outras interfaces já em execução dhCP, este serviço não irá afetá-los.

Para iniciar o DHCP numa interface específica quando várias interfaces estiverem ativadas, utilize o serviço *nx_dhcp_interface_start.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Início dhcp bem sucedido.  
- **NX_DHCP_ALREADY_STARTED**: (0x93) DHCP já começou.
- NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.
- NX_CALLER_ERROR: (0x11) Inválido de serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Start the DHCP processing for this IP instance.  */
status =  nx_dhcp_start(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully started.  */
```

## <a name="nx_dhcp_interface_start"></a>nx_dhcp_interface_start

Iniciar o processamento do DHCP na interface especificada

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_interface_start(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>Description

Este serviço inicia o processamento de DHCP na interface especificada se essa interface estiver ativada para DHCP. Consulte *nx_dhcp_interface_enable*() para obter mais detalhes sobre como ativar uma interface para DHCP. Por predefinição, a interface primária é ativada para DHCP quando a aplicação *nx_dhcp_create.*

Se não houver outras interfaces a executar o Cliente DHCP este serviço iniciará/retomará a linha do Cliente DHCP e (re)ativar o temporizador do Cliente DHCP.  
  
A aplicação deve utilizar *nx_ip_status_check* para verificar se um endereço IP é obtido.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.
- **Interface_index**: Índice sobre o qual iniciar o Cliente DHCP

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Início dhcp bem sucedido. 
- **NX_DHCP_ALREADY_STARTED**: (0x93) DHCP já começou.
- NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.
- NX_CALLER_ERROR: (0x11) Inválido de serviço.
- NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Start the DHCP processing for this IP instance on interface 1.  */
status =  nx_dhcp_interface_start(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully started.  */
```

## <a name="nx_dhcp_state_change_notify"></a>nx_dhcp_state_change_notify

Definir função de retorno de mudança de estado DHCP

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_state_change_notify(NX_DHCP *dhcp_ptr, 
                                 VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, UCHAR new_state));
```

### <a name="description"></a>Description

Este serviço regista a função de retorno especificado dhcp_state_change_notify para notificar uma aplicação de alterações do estado dhcp. A função de retorno fornece o estado em que o Cliente DHCP se transferiu.

Seguem-se os valores associados aos vários estados da DHCP:

- NX_DHCP_STATE_BOOT: 1
- NX_DHCP_STATE_INIT: 2
- NX_DHCP_STATE_SELECTING: 3
- NX_DHCP_STATE_REQUESTING: 4
- NX_DHCP_STATE_BOUND: 5
- NX_DHCP_STATE_RENEWING: 6
- NX_DHCP_STATE_REBINDING: 7
- NX_DHCP_STATE_FORCERENEW: 8
- NX_DHCP_STATE_ADDRESS_PROBING: 9

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.
- **dhcp_state_change_notify**: Ponteiro da função de retorno de mudança de estado

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Conjunto de chamadas bem-sucedidos.  
- NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.
- NX_CALLER_ERROR: (0x11) Inválido de serviço.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Register the “my_state_change” function to be called on any DHCP state change, assuming DHCP has alreadybeen created.  */
status =  nx_dhcp_state_change_notify(&my_dhcp, my_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered.  */
```

## <a name="nx_dhcp_interface_state_change_notify"></a>nx_dhcp_interface_state_change_notify

Definir função de retorno de alteração de estado DHCP na interface especificada

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_interface_state_change_notify(NX_DHCP *dhcp_ptr, UINT interface_index,
                                           VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                                                            UINT interface_index,
                                                                            UCHAR new_state));
```

### <a name="description"></a>Description

Este serviço regista a função de retorno especificado para notificar uma aplicação de alterações do estado dhcp. Os argumentos de entrada funciton de retorno são o índice de interface e o estado para o quais o Cliente DHCP passou a essa interface.

Para obter mais informações sobre as funções de mudança de estado, consulte *nx_dhcp_state_change_notify*().

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.
- **dhcp_interface_state_change_notify**: Ponteiro da função de chamada de aplicação

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Conjunto de chamadas bem-sucedidos.  
- NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Register the “my_state_change” function to be called on any DHCP state change,   
   assuming DHCP has alreadybeen created.  */

void dhcp_interstate_state_change(NX_DHCP *dhcp_ptr, UINT iface_index, 
                                  UCHAR new_state);


status =  nx_dhcp_interstate_state_change_notify(&my_dhcp,  
                                                 dhcp_interstate_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered.  */
```

## <a name="nx_dhcp_stop"></a>nx_dhcp_stop

Para o processamento do DHCP

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_stop(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Description

Este serviço impede o processamento de DHCP em todas as interfaces que iniciaram o processamento do DHCP. Se não houver interfaces a processar o DHCP, este serviço suspenderá a linha do Cliente DHCP e inativará o temporizador do Cliente DHCP.

Para parar o DHCP numa interface específica se várias interfaces estiverem ativadas para DHCP, utilize o serviço *nx_dhcp_interface_stop.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) paragem bem sucedida do DHCP
- **NX_DHCP_NOT_STARTED**: (0x96) A instância dhcp não começou.
- NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.
- NX_CALLER_ERROR: (0x11) Inválido de serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Stop the DHCP processing for this IP instance.  */
status =  nx_dhcp_stop(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully stopped.  */
```

## <a name="nx_dhcp_interface_stop"></a>nx_dhcp_interface_stop

Parar o processamento do DHCP na interface especificada

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_interface_stop(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>Description

Este serviço impede o processamento de DHCP na interface especificada se o DHCP já estiver iniciado. Se não houver outras interfaces a funcionar dhCP, o fio e o temporizador DHCP estão suspensos.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.
- **Interface_index**: Interface para parar o processamento do DHCP

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) paragem bem sucedida do DHCP
- **NX_DHCP_NOT_STARTED**: (0x96) o DHCP não começou.
- NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.
- NX_CALLER_ERROR: (0x11) Inválido de serviço.
- NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Stop DHCP processing for this IP instance on interface 1.  */
status =  nx_dhcp_interface_stop(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully stopped.  */
```

## <a name="nx_dhcp_user_option_retrieve"></a>nx_dhcp_user_option_retrieve

Recupere uma opção DHCP da última resposta do servidor

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_user_option_retrieve(NX_DHCP *dhcp_ptr, UINT request_option, 
                                  UCHAR *destination_ptr, UINT *destination_size);
```

### <a name="description"></a>Description

Este serviço recupera a opção DHCP especificada a partir do tampão de opções DHCP na primeira interface ativada para DHCP encontrada no registo do Cliente DHCP. Se for bem sucedido, os dados de opção são copiados para o tampão especificado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.  
- **request_option**: Opção DHCP, conforme especificado pelos RFCs. Consulte a opção NX_DHCP_OPTION em *nxd_dhcp_client.h*.
- **destination_ptr**: Ponte para o destino para a cadeia de resposta.  
- **destination_size**: Ponte para o tamanho do destino e no regresso, o destino para colocar o número de bytes devolvidos.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Recuperação de opções bem sucedidas.  
- **NX_DHCP_NOT_BOUND:**(0x94) O Cliente DHCP não está vinculado.
- **NX_DHCP_NO_INTERFACES_ENABLED:**(0xA5) Não há interfaces ativadas para o DHCP
- **NX_DHCP_DEST_TO_SMALL:**(0x95) O destino é demasiado pequeno para manter a resposta.
- **NX_DHCP_PARSE_ERROR**: (0x97) Opção não encontrada na resposta do Servidor.
- NX_PTR_ERROR: (0x16) Ponteiro de entrada inválido.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server.  */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_user_option_retrieve(&my_dhcp, NX_DHCP_OPTION_DNS_SVR,
                                        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string.  */
```

## <a name="nx_dhcp_interface_user_option_retrieve"></a>nx_dhcp_interface_user_option_retrieve

Recupere uma opção DHCP da última resposta do servidor na interface especificada

### <a name="prototype"></a>Prototype

```c
UINT nx_dhcp_interface_user_option_retrieve(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            UINT request_option, UCHAR *destination_ptr,
                                            UINT *destination_size);
```

### <a name="description"></a>Description

Este serviço recupera a opção DHCP especificada a partir do tampão de opções DHCP na interface especificada, se essa interface estiver ativada para DHCP. Se for bem sucedido, os dados de opção são copiados para o tampão especificado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.
- **Interface_index**: Índice para recuperar a opção especificada
- **request_option**: Opção DHCP, conforme especificado pelos RFCs. Consulte a opção NX_DHCP_OPTION: em *nxd_dhcp_client.h*.  
- **destination_ptr**: Ponte para o destino para a cadeia de resposta.  
- **destination_size**: Ponte para o tamanho do destino e no regresso, o destino para colocar o número de bytes devolvidos.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Recuperação de opções bem sucedidas.  
- **NX_DHCP_NOT_BOUND:**(0x94) endereço IP não atribuído
- **NX_DHCP_DEST_TO_SMALL:**(0x95) Tampão é muito pequeno
- **NX_DHCP_PARSE_ERROR**: (0x97) A opção DHCP não encontrada na resposta do Servidor.
- NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.
- NX_CALLER_ERROR: (0x11) Inválido de serviço.
- NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server on the prmary interface.  */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_interface_user_option_retrieve(&my_dhcp, 0, NX_DHCP_OPTION_DNS_SVR,
                                                  dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string.  */
```

## <a name="nx_dhcp_user_option_convert"></a>nx_dhcp_user_option_convert

Converter quatro bytes para ULONG

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_user_option_convert(UCHAR *option_string_ptr);
```

### <a name="description"></a>Description

Este serviço converte os quatro caracteres apontados por "option_string_ptr" num valor longo não assinado. É especialmente útil quando os endereços IP são  
presente.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **option_string_ptr**: Ponteiro para a cadeia de opções previamente recuperada.

### <a name="return-values"></a>Valores de devolução

- **Valor**: Valor dos quatro primeiros bytes.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
UCHAR  dns_ip_string[4];
ULONG  dns_ip;

/* Convert the first four bytes of “dns_ip_string” to an actual IP
address in “dns_ip.”  */
dns_ip=  nx_dhcp_user_option_convert(dns_ip_string);

/* If status is NX_SUCCESS the DNS IP address is in “dns_ip.”  */
```

## <a name="nx_dhcp_user_option_add_callback_set"></a>nx_dhcp_user_option_add_callback_set

Desace a função de retorno definido para adicionar opções fornecidas pelo utilizador

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_user_option_add_callbcak_set(NX_DHCP *dhcp_ptr, 
                                           UINT (*dhcp_user_option_add)(NX_DHCP *dhcp_ptr, 
                                                                        UINT iface_index, 
                                                                        UINT message_type, 
                                                                        UCHAR *user_option_ptr, 
                                                                        UINT *user_option_length));
```

### <a name="description"></a>Description

Este serviço regista a função de retorno especificado para adicionar opções fornecidas pelo utilizador.

Se a função de retorno especificado, as aplicações podem adicionar opções fornecidas pelo utilizador no pacote iface_index e message_type.

>[!NOTE] 
> Na rotina do utilizador. As aplicações devem seguir o formato de opções DHCP quando adicionar opções fornecidas pelo utilizador. O tamanho total das opções do utilizador deve ser menor ou igual a user_option_length e atualizar o user_option_length como comprimento real das opções. Volte NX_TRUE se adicionar opções com sucesso, caso contrário, volte NX_FALSE.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.
- **dhcp_user_option_add**: Função de adicionar a opção do utilizador ao utilizador.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Conjunto de chamadas bem-sucedidos.
- NX_PTR_ERROR: (0x16) Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Register the “my_dhcp_user_option_add” function to be called when add DHCP
options, assuming DHCP has already been created.  */

status =  nx_dhcp_user_option_add_callback_set(&my_dhcp, my_dhcp_user_option_add);

/* If status is NX_SUCCESS the callback function was successfully registered.  */

```

