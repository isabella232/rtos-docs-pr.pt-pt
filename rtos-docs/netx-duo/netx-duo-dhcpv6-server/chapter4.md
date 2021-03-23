---
title: Capítulo 4 - Serviços de servidores Azure RTOS NetX Duo DHCPv6
description: Este capítulo contém uma descrição de todos os serviços NetX Duo DHCPv6Server
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1d45139031b5a687baacf86c7a2e0a53c90533be
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826029"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-server-services"></a>Capítulo 4 - Serviços de servidores Azure RTOS NetX Duo DHCPv6

Este capítulo contém uma descrição de todos os serviços NetX Duo DHCPv6Server (listados abaixo).

Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

- nx_dhcpv6_server_create Criar *uma insísição de servidor DHCPv6*
- nx_dhcpv6_server_delete Eliminar *uma insísição do servidor DHCPv6*
- nx_dhcpv6_server_start Iniciar *a tarefa do servidor DHCPv6*
- nx_dhcpv6_server_suspend suspender *a tarefa do servidor DHCPv6*
- nx_dhcpv6_server_resume retomar *o processamento do cliente DHCPv6*
- nx_dhcpv6_server_suspend suspender *o processamento do cliente DHCPv6*
- nx_dhcpv6_create_dns_address Definir *o servidor DNS para pedidos de opção*
- nx_dhcpv6_create_ip_address_range Criar *a gama de endereços IP para arrendar*
- nx_dhcpv6_reserve_ip_address_range *Gama de endereços IP de reserva na lista de servidores*
- nx_dhcpv6_set_server_duid *Definir o Servidor DUID para pacotes DHCPv6*
- nx_dhcpv6_add_ip_address_lease Adicionar *um registo de locação à tabela de servidores DHCPv6*
- Nx_dhcpv6_retrieve_ip_address_lease Recuperar *um registo de locação IP da tabela Server*
- nx_dhcpv6_add_client_record Adicionar *um registo de cliente DHCPv6 à tabela do Servidor*
- nx_dhcpv6_retrieve_client_record Recuperar *um registo de cliente da tabela do Servidor*
- nx_dhcpv6_server_interface_set Definir *o índice de interface para os serviços do Servidor DHCPv6*
- nx_dhcpv6_server_option_request_handler_set *Definir o manipulador de pedidos de opção*

## <a name="nx_dhcpv6_create_dns_address"></a>nx_dhcpv6_create_dns_address

### <a name="set-the-network-dns-server"></a>Definir o servidor DNS da rede

**Prototype**

```
UINT nx_dhcpv6_create_dns_address(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *dns_ipv6_address);
```

**Descrição**

Este serviço carrega o Servidor DHCPv6 com o endereço do servidor DNS para a interface de rede Server DHCPv6.

**Parâmetros de Entrada**

- **dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6
- **dns_ipv6_address** Ponteiro para o servidor DNS

**Valores de devolução**

- **NX_SUCCESS** (0x00) DNS Serversaved para a instância do servidor DHCPv6
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) É fornecido um endereço inválido
- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

**Permitido a partir de**

Código de Aplicação

**Exemplo**

```
/* Set the network DNS server with the input address for the Server DHCPv6interface. */
status = nx_dhcpv6_create__dns_address(&dhcp_server_0, &dns_ipv6_address);
/* If this service returns NX_SUCCESS the DNS server data was accepted. */
```

## <a name="nx_dhcpv6_create_ip_address_range"></a>nx_dhcpv6_create_ip_address_range

### <a name="create-the-server-ip-address-list"></a>Criar a lista de endereços IP do Servidor

**Prototype**

```
UINT _nx_dhcpv6_create_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_added)
```

**Descrição**

Este serviço cria a lista de endereços IP especificada pelos endereços de início e fim do intervalo de endereços atribuível do Servidor. Os endereços de início e de fim devem corresponder ao prefixo do endereço de interface do Servidor (deve estar no mesmo link que a interface Server DHCPv6). O número de endereços realmente adicionados é devolvido.

**Parâmetros de Entrada**

- **dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6
- **start_ipv6_address** Início de endereços para adicionar
- **end_ipv6_address** Fim dos endereços para adicionar
- ***addresses_added** Saída de endereços adicionados

**Valores de devolução**

- **NX_SUCCESS** (0x00) lista de endereços IP criada com sucesso
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) É fornecido um endereço inválido
- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

**Permitido a partir de**

Código de Aplicação

**Exemplo**

```
/* Create the Server IP address list for the server DHCPv6 interface. */
status = nx_dhcpv6_create_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);
/* If status is NX_SUCCESS one or more addresses were successfully added. */
```

## <a name="nx_dhcpv6_reserve_ip_address_range"></a>nx_dhcpv6_reserve_ip_address_range

### <a name="reserve-specified-range-of-ip-addresses"></a>Reserva especificada gama de endereços IP

**Prototype**

```
UINT _nx_dhcpv6_reserve_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_reserved)
```

**Descrição**

Este serviço reserva o intervalo de endereços IP especificado pelos endereços de início e fim. Estes endereços devem estar dentro do intervalo de endereços IP do servidor previamente criado. Estes endereços não serão atribuídos a nenhum Cliente pelo Servidor DHCPv6. Os endereços de início e de fim devem corresponder ao prefixo do endereço de interface do Servidor (deve estar no mesmo link que a interface de rede Do Servidor DHCPv6). O número de endereços realmente reservados é devolvido.

**Parâmetros de Entrada**

- **dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6
- **start_ipv6_address** Início de endereços para reservar
- **end_ipv6_address** Fim dos endereços para reservar
- ***addresses_reserved** Número de endereços reservados

**Valores de devolução**

- **NX_SUCCESS** (0x00) Mensagem DE LIBERTAÇÃO criada e processada com sucesso
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) É fornecido um endereço inválido
- **NX_DHCPV6_INVALID_IP_ADDRESS** (0xED1) Endereço inicial não encontrado na lista de endereços do Servidor.
- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

**Permitido a partir de**

Código de Aplicação

**Exemplo**

```
/* Reserve a range of ip addresses in the Server address table for the server DHCPv6 
network interface. */

status = nx_dhcpv6_reserve_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);

/* If status is NX_SUCCESS one or more addresses were successfully reserved. */
```

## <a name="nx_dhcpv6_server_create"></a>nx_dhcpv6_server_create

### <a name="create-the-dhcpv6-server-instance"></a>Criar a instância do Servidor DHCPv6 

**Prototype**

```
UINT nx_dhcpv6_server_create(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
        NX_IP *ip_ptr, CHAR *name_ptr, 
        NX_PACKET_POOL *packet_pool_ptr, 
        VOID *stack_ptr,ULONG stack_size,
    VOID (*dhcpv6_address_declined_handler)(struct 
        NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        NX_DHCPV6_CLIENT *dhcpv6_client_ptr, 
        UINT message),
    VOID (*dhcpv6_option_request_handler)(
        struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        UINT option_request, UCHAR *buffer_ptr, UINT *index));
```

**Descrição**

Este serviço cria a tarefa do Servidor DHCPv6 com a entrada especificada. Os manipuladores de retorno são entradas opcionais. São necessários o ponteiro da pilha, a instância IP e a entrada do pacote. A instância IP e a piscina de pacotes já devem ser criadas.

O utilizador é encorajado a ligar para nx_dhcpv6_server_option_request_handler_set para definir o manipulador de pedidos de opção.

**Parâmetros de Entrada**

- **dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6
- **ip_ptr** Ponteiro para a instância IP
- **name_str** Ponteiro para o nome do servidor
- **packet_pool_ptr** Ponteiro para a piscina de pacotes do Servidor
- **stack_ptr** Ponteiro para memória de pilha de servidor
- **stack_size** Tamanho da memória da pilha do servidor
- **dhcpv6_address_declined_handler** Ponteiro para o cliente declinar ou libertar o manipulador de mensagens
- **dhcpv6_option_request_handler** Ponteiro para opções pedir opção handler

**Valores de devolução**

- **NX_SUCCESS** (0x00) Servidor retomado com sucesso
- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro
- NX_DHCPV6_PARAM_ERROR Entrada inválida sem ponteiro

**Permitido a partir de**

Código de Aplicação

**Exemplo**

```
/* Create the DHCPv6 Server. */
status = nx_dhcpv6_server_create(&dhcp_server_0, &ip_0, "DHCPv6 Server",
         &pool_0, stack_pointer,2048, dhcpv6_decline_handler,
         dhcpv6_get_time_handler);
/* If status is NX_SUCCESS the Server successfully created. */
```

## <a name="nx_dhcpv6_server_delete"></a>nx_dhcpv6_server_delete

### <a name="delete-the-dhcpv6-server"></a>Eliminar o Servidor DHCPv6

**Prototype**

```
UINT _nx_dhcpv6_server_delee(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Descrição**

Este serviço elimina a tarefa do Servidor DHCPv6 e qualquer pedido que o Servidor estava a processar.

**Parâmetros de Entrada**

- **dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6

**Valores de devolução**

- **servidor NX_SUCCESS** (0x00) eliminado com sucesso
- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

**Permitido a partir de**

Fios

**Exemplo**

```
/* Delete the DHCPv6 Serve. */
status = nx_dhcpv6_server_delete(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully deleted. */
```

## <a name="nx_dhcpv6_server_resume"></a>nx_dhcpv6_server_resume

### <a name="resume-dhcpv6-server-task"></a>Retomar a tarefa do servidor DHCPv6 

**Prototype**

```
UINT _nx_dhcpv6_server_resume(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Descrição**

Este serviço retoma a tarefa do Servidor DHCPv6 e qualquer pedido que o Servidor estava a processar.

**Parâmetros de Entrada**

- **dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6

**Valores de devolução**

- **NX_SUCCESS** (0x00) Servidor retomado com sucesso
- **NX_DHCPV6_ALREADY_STARTED** (0xE91) Servidor já está em execução
- **estado** (variável) ThreadX e NetX Duo estado de erro
- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

**Permitido a partir de**

Fios

**Exemplo**

```
/* Resume the DHCPv6 Server task. */
status = nx_dhcpv6_server_resume(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully resumed. */
```

## <a name="nx_dhcpv6_server_suspend"></a>nx_dhcpv6_server_suspend

### <a name="suspend-dhcpv6-server-task"></a>Suspender a tarefa do servidor DHCPv6 

**Prototype**

```
UINT _nx_dhcpv6_server_suspend(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Descrição**

Este serviço suspende a tarefa do Servidor DHCPv6 e qualquer pedido que o Servidor estava a processar.

**Parâmetros de Entrada**

- **dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6

**Valores de devolução**

- **NX_SUCCESS** (0x00) Servidor retomado com sucesso
- **NX_DHCPV6_NOT_STARTED** (0xE92) Servidor ainda não foi iniciado 
- **Estado** (variável) ThreadX e Estado de erro da NetX Duo
- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

**Permitido a partir de**

Fios

**Exemplo**

```
/* Suspend the DHCPv6 Server task. */
status = nx_dhcpv6_server_suspend(&dhcp_server_0);

/* If status is NX_SUCCESS the Server successfully suspended. */
```

## <a name="nx_dhcpv6_server_start"></a>nx_dhcpv6_server_start

### <a name="start-the-dhcpv6-server-task"></a>Inicie a tarefa do Servidor DHCPv6 

**Prototype**

```
UINT _nx_dhcpv6_server_start(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Descrição**

Este serviço inicia a tarefa do Servidor DHCPv6 e lê o Servidor para processar pedidos de aplicação para receber mensagens do Cliente DHCPv6. Verifica que a instância do Servidor tem informações suficientes (Server DUID), cria e liga a tomada UDP para enviar e receber mensagens DHCPv6, e ativa os temporizadores para manter o tempo de sessão e a expiração do aluguer de IP.

>[!NOTE] 
> Antes de o Servidor DHCPv6 poder ser executado, a aplicação do anfitrião é responsável pela criação do intervalo de endereços IP a partir do qual o Servidor pode atribuir endereços IP. É também responsável pela definição da interface Server DUID e DHCPv6 (ver *nx_dhcpv6_server_duid_set* e *nx_dhcpv6_server_interface_set* respectivamente.

**Parâmetros de Entrada**

- **dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6

**Valores de devolução**

- **NX_SUCCESS** (0x00) Servidor com sucesso
- **NX_DHCPV6_ALREADY_STARTED** (0xE91) Servidor já está em execução
- **NX_DHCPV6_NO_ASSIGNABLE_ADDRESSES** (0xEA7) Servidor não tem endereços atribuíveis para arrendar
- **NX_DHCPV6_INVALID_GLOBAL_INDEX** (0xE97) Índice de endereço global não definido
- **NX_DHCPV6_NO_SERVER_DUID** (0xE92) Nenhum servidor DUID criado 
- **estado** (variável) ThreadX e NetX Duo estado de erro
- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

**Permitido a partir de**

Fios

**Exemplo**

```
/* Start the DHCPv6 Server task. */
status = nx_dhcpv6_server_start(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_retrieve_ip_address_lease"></a>nx_dhcpv6_retrieve_ip_address_lease

### <a name="get-an-ip-address-lease-from-the-server-table"></a>Obtenha um arrendamento de endereço IP na tabela Do Servidor

**Prototype**

```
UINT _nx_dhcpv6_retrieve_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, 
     NXD_ADDRESS *lease_IP_address, ULONG *T1, ULONG *T2, 
     ULONG *valid_lifetime, ULONG *preferred_lifetime)
```

**Descrição**

Este serviço recupera um registo de locação de endereço IP da tabela Server na localização do índice de tabela especificado. Isto pode ser feito antes ou depois de recuperar os dados do registo do Cliente.

A capacidade de armazenar e recuperar dados entre o Servidor DHCPv6 e a memória não volátil é um requisito do protocolo DHCPv6. Não faz diferença em que ordem os dados de locação IP e dados de registo do Cliente são guardados para memória nãovolárida.

>[!NOTE] 
> Não é aconselhável copiar dados para ou a partir de tabelas do Servidor sem parar ou suspender primeiro o Servidor DHCPv6.

**Parâmetros de Entrada**

- **dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6
- **table_index** Índice de tabela para armazenar arrendamento em
- **lease_IP_address** Ponteiro para endereço IP alugado ao Cliente
- **T1** Cliente pediu tempo de renovação
- **T2** Cliente solicitou tempo de reencadernação
- **valid_lifetime** Arrendamento de clientes torna-se depreciado
- **preferred_lifetime** Arrendamento de cliente torna-se inválido

**Valores de devolução**

- **NX_SUCCESS** (0x00) Servidor com sucesso
- **NX_DHCPV6_PARAMETER_ERROR** (0xE93) Entrada de dados de locação IP inválida
- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

**Permitido a partir de**

Código de aplicação

**Exemplo**

```
/* Retrieve the DHCPv6 Server lease data. */
For (I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
{
    /* Get the next lease record. */
    status = nx_dhcpv6_server_startdhcpv6_server_ptr, i, &next_ipv6_address, &T1,
             &T2, &preferred_lifetime, &valid_lifetime);
    /* The host application then saves this record to memory.
}
/* If status is NX_SUCCESS the Server data is successfully downloaded. */
```

## <a name="nx_dhcpv6_add_ip_address_lease"></a>nx_dhcpv6_add_ip_address_lease

### <a name="add-an-ip-address-lease-to-the-server-table"></a>Adicione um aluguer de endereço IP à tabela Do Servidor

**Prototype**

```
UINT _nx_dhcpv6_add_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, NXD_ADDRESS *lease_IP_address, ULONG T1, ULONG T2, 
     ULONG valid_lifetime, ULONG preferred_lifetime)
```

**Descrição**

Este serviço carrega dados de locação IP de uma sessão anterior do Servidor DHCPv6 de memória não volátil para a tabela de locação do Servidor. Isto não é necessário se o Servidor estiver em execução pela primeira vez e não tiver dados de locação prévia. Se for esse o caso, a aplicação do anfitrião deve criar um intervalo de endereços IP para a atribuição de endereços IP, utilizando o serviço *nx_dhcpv6_create_ip_address_range.* Os dados são suficientes para reconstruir um registo de arrendamento DHCPv6. O índice de tabela não precisa de ser especificado. Se for definido para 0xFFFFFFFF (infinito) o Servidor DHCPv6 encontrará a próxima ranhura disponível para copiar os dados para.

>[!NOTE] 
> O upload dos dados de locação IP deve ser feito antes de carregar os registos do Cliente; ambos devem ser feitos antes de (re)iniciar o Servidor DHCPv6.

A capacidade de armazenar e recuperar dados entre o Servidor DHCPv6 e a memória não volátil é um requisito do protocolo DHCPv6.

**Parâmetros de Entrada**

- **dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6
- **table_index** Índice de tabela para armazenar arrendamento em
- **lease_IP_address** Ponteiro para endereço IP alugado ao Cliente
- **T1** Cliente pediu tempo de renovação
- **T2** Cliente solicitou tempo de reencadernação
- **valid_lifetime** Arrendamento de clientes torna-se depreciado
- **preferred_lifetime** Arrendamento de cliente torna-se inválido

**Valores de devolução**

- **NX_SUCCESS** (0x00) Servidor com sucesso
- **NX_DHCPV6_TABLE_FULL** (0xEC4) Não há espaço para mais dados de locação**
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) Os dados de locação não parecem estar ligados à interface do Servidor DHCPv6
- **NX_DHCPV6_PARAM_ERROR** (0xE93) Entrada de dados de locação IP inválida
- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

**Permitido a partir de**

Código de aplicação

**Exemplo**

```
/* Copy the IP lease data to the Server address table. Note that the table index
is defaulted to 0xFFFFFFFF meaning the DHCPv6 Server will find an empty slot 
for each lease. */

    For(I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
    {
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr, 0xFFFFFFFF,
                 &next_ipv6_address, &T1, &T2, &preferred_lifetime, &valid_lifetime);
        /* Get the next lease address from memory… */
    }
    
    /* If status is NX_SUCCESS the lease data was successfully uploaded. It is opk
    to add the Client records to the Server table now. */
```

## <a name="nx_dhcpv6_add_client_record"></a>nx_dhcpv6_add_client_record

### <a name="add-a-client-record-to-the-server-table"></a>Adicione um registo de Cliente à tabela do Servidor

**Prototype**

```
UINT _nx_dhcpv6_add_client_record(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG message_xid, 
     NXD_ADDRESS *client_address, UINT client_state, 
     ULONG IP_lease_time_accrued, ULONG valid_lifetime, UINT duid_type, UINTduid_hardware, 
     ULONG physical_address_msw, ULONG physical_address_lsw, ULONG duid_time, 
     ULONG duid_vendor_number, UCHAR *duid_vendor_private, UINT duid_private_length)
```

**Descrição**

Este serviço copia os dados do Cliente de memória não volátil para a tabela do Servidor um registo de cada vez. Isto só é necessário se o Servidor estiver a ser reiniciado e tiver dados do Cliente de uma sessão anterior para restaurar a memória. Se um Servidor não tiver dados anteriores, o Servidor DHCPv6 rubricará a tabela cliente para poder adicionar registos de Clientes.

Não é necessário especificar o índice de tabela. Se estiver definido para 0xFFFFFFFF (infinito) o Servidor DHCPv6 localizará a próxima ranhura disponível. O Servidor DHCPv6 pode reconstruir um registo do Cliente a partir destes dados.

>[!NOTE] 
> A aplicação do anfitrião DEVE carregar os dados de locação IP ANTES dos dados de gravação do Cliente. Isto é de modo que internamente o Servidor DHCPv6 pode cruzar as tabelas de modo que cada registo do Cliente seja acompanhado com o seu registo de locação IP correspondente nas respetivas tabelas. Consulte *nx_dhcpv6_add_ip_address_lease* para obter mais informações sobre o upload de dados de locação IP a partir da memória.

>[!NOTE] 
> Dependendo do tipo DUID, nem todos os dados devem ser fornecidos. Por exemplo, se um Cliente tiver um tipo DUID atribuído ao fornecedor, pode enviar zero para parâmetros DUID Link Layer (endereço MAC, tipo de hardware, tempo DUID).

A capacidade de armazenar e recuperar dados entre o Servidor DHCPv6 e a memória não volátil é um requisito do protocolo DHCPv6.

**Parâmetros de Entrada**

- **dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6

**Valores de devolução**

- **NX_SUCCESS** (0x00) Servidor com sucesso
- **NX_ INVALID_PARAMETERS** (0x4D) Entrada inválida sem ponteiro**
- **NX_DHCPV6_TABLE_FULL** (0xEC4) Não há slots vazios para adicionar outro registo do Cliente
- **NX_DHCPV6_ADDRESS_NOT_FOUND** (0xEA8) Endereço atribuído ao cliente não encontrado na tabela de locação do Servidor.
- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

**Permitido a partir de**

Código de aplicação

**Exemplo**

```
/*Add the IP lease data and Client records back to the server before starting
theServer. */
    /* Copy the 'lease data' to the server table FIRST. */
for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {

        /* Add the next lease record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr,
                 0xFFFFFFFF,,&next_ipv6_address, NX_DHCPV6_DEFAULT_T1_TIME, 
                 NX_DHCPV6_DEFAULT_T2_TIME, NX_DHCPV6_DEFAULT_PREFERRED_TIME, 
                 NX_DHCPV6_DEFAULT_VALID_TIME);
if (status != NX_SUCCESS)
return status;
        /* Get the next IP lease record from memory. */
        …
    }
    /* Copy the client records to the Server table NEXT.
    for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {
        /* Add the next client record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_client_record(dhcpv6_server_ptr, 0xFFFFFFFF,
                 message_xid, &client_ipv6_address, NX_DHCPV6_STATE_BOUND,
                 IP_lifetime_time_accrued, valid_lifetime, duid_type, 
                 duid_hardware, physical_address_msw, physical_address_lsw, 
                 duid_time, 0, NX_NULL, 0);
if (status != NX_SUCCESS)
return status;
        /* Get the next Client record from memory. */
        …
    }

/* If status is NX_SUCCESS the Server data was successfully restored and 
it is ok to start the DHCPv6 server now. */
```

## <a name="nx_dhcpv6_retrieve_client_record"></a>nx_dhcpv6_retrieve_client_record

### <a name="retrieve-a-client-record-from-the-server-table"></a>Recupere um registo de Cliente da tabela do Servidor

**Prototype**

```
UINT _nx_dhcpv6_retrieve_client_record(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG *message_xid, 
     NXD_ADDRESS *client_address, UINT *client_state, 
     ULONG IP_lease_time_accrued, 
     ULONG *valid_lifetime, UINT *duid_type, 
     UINT *duid_hardware, ULONG *physical_address_msw, 
     ULONG *physical_address_lsw, ULONG *duid_time, 
     ULONG *duid_vendor_number, 
     UCHAR *duid_vendor_private, 
     UINT *duid_private_length)
```

**Descrição**

Este serviço copia os dados essenciais da tabela de registos do Cliente do Servidor para armazenamento para memória não volátil. O Servidor pode reconstruir um registo de Cliente adequado a partir desses dados no processo inverso (enviando dados para a tabela Do Servidor). Independentemente do tipo DUID, nenhum dos ponteiros pode ser ponteiros NULO; os dados são inicializados a zero para todos os parâmetros. Por exemplo, se o tipo DUID do Cliente for Link Layer Plus Time, o número do fornecedor é devolvido como zero e o ID privado é uma cadeia vazia.

A capacidade de armazenar e recuperar dados entre o Servidor DHCPv6 e a memória não volátil é um requisito do protocolo DHCPv6. Não faz diferença em que ordem os dados de locação IP e dados de registo do Cliente são guardados para memória nãovolárida.

>[!NOTE] 
> Não é aconselhável copiar dados para ou a partir de tabelas do Servidor sem parar ou suspender primeiro o Servidor DHCPv6.

**Parâmetros de Entrada**

- **dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6
- **table_index** Índice na tabela de clientes do Server
- **message_xid** ID de transação de servidor de cliente
- **client_address** Endereço IPv6 alugado ao Cliente
- **client_state** Estado do Cliente DHCPv6 (por exemplo, ligado)
- **IP_lease_time_accrued** O tempo expirou no arrendamento já **dhcpv6_server_ptr** Pointer para o SERVIDOR DHCPv6
- **dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6

**Valores de devolução**

- **NX_SUCCESS** (0x00) Servidor com sucesso
- **NX_DHCPV6_INVALID_DUID** (0xECC) Dados DUID inválidos ou inconsistentes
- **NX_PTR_ERROR** (0x16) Entrada inválida do ponteiro
- NX_INVALID_PARAMETERS (0x4D) Entrada inválida sem ponteiro

**Permitido a partir de**

Código de aplicação

**Exemplo**

```
/* Retrieve the Client records from the DHCPv6 Server table. */
For (i = 0; i< NX_MAX_DHCPV6_CLIENTS; i++)
{
    status = nx_dhcpv6_retrieve_client_recorddhcpv6_server_ptr, i, &message_xid,
             &client_ipv6_address, &client_state, &IP_lifetime_time_accrued, 
             valid_lifetime, &duid_type, &duid_hardware, &physical_address_msw,
             &physical_address_lsw, &duid_time, &duid_vendor_number, &private_id[0], 
             &length);
    /* The host application can save this data to memory now.
}
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_server_interface_set"></a>nx_dhcpv6_server_interface_set

### <a name="setthe-interface-index-for-server-dhcpv6-interface"></a>Definir o índice de interface para a interface do Servidor DHCPv6

**Prototype**

```
UINT _nx_dhcpv6_server_interface_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT iface_index, UINT ga_address_index)
```

**Descrição**

Este serviço define a interface de rede na qual o Servidor DHCPv6 lida com pedidos do Cliente DHCPv6. Não que para versões do NetX Duo que não suportem multihome, o valor da interface está em incumprimento a zero. O índice global de endereços é necessário para obter o endereço global do Servidor na sua interface DHCPv6. Isto é usado pela lógica DHCPv6 para garantir que endereços de locação e outros dados DHCPv6 estão em ligação com o Servidor DHCPv6.

Isto deve ser chamado antes do início do servidor DHCPv6, mesmo para aplicações em dispositivos únicos domésticos ou sem suporte multihome.

**Parâmetros de Entrada**

- **dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6
- **iface_index** Interface do servidor DHCPv6
- **ga_address_index** Índice de endereço global do Servidor na tabela de endereços ip do servidor

**Valores de devolução**

- **NX_SUCCESS** (0x00) Servidor com sucesso
- **NX_INVALID_INTERFACE** (0x4C) Interface não existe
- NX_NO_INTERFACE_ADDRESS (0x50) O índice global excede os endereços IPv6 máximos de instância IP (NX_MAX_IPV6_ADDRESSES)
- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

**Permitido a partir de**

Código de aplicação

**Exemplo**

```
/* Set the Server DHCPv6 interface to the primary interface. The global IP 
address is at the index 1 in the IP address table. */
status = nx_dhcpv6_server_interface_set(&dhcp_server_0, 0, 1);

/* If status is NX_SUCCESS the Server interface is successfully set. */
```
## <a name="nx_dhcpv6_set_server_duid"></a>nx_dhcpv6_set_server_duid

### <a name="set-the-server-duid-for-dhcpv6-packets"></a>Desaprova o Servidor DUID para pacotes DHCPv6

**Prototype**

```
UINT _nx_dhcpv6_set_server_duid(NX_DHCPV6_SERVER *dhcpv6_server_ptr,
     UINT duid_type, UINT hardware_type, 
     ULONG mac_address_msw, ULONG mac_address_lsw, 
     ULONG time)
```

**Descrição**

Este serviço define o Servidor DUID e deve ser chamado antes da aplicação do anfitrião iniciar o Servidor. Para os tipos DUID de camada de ligação e de ligação, a aplicação do anfitrião deve fornecer os dados de endereços de hardware e MAC. Para os DUIDs de tempo de ligação, o ponteiro de tempo deve apontar para um tempo válido. O número de segundos desde 1 de janeiro de 2000 é um valor típico de sementes. Se o tipo de DuID do Servidor for a empresa, o tipo atribuído pelo fornecedor, o DUID será criado a partir das opções configuráveis do utilizador NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID e NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID, e os valores de tempo e endereço MAC podem ser definidos como NU.

>[!NOTE] 
> É da responsabilidade da aplicação anfitriã guardar os parâmetros DO SERVIDOR DUID para memória nãovolárida de modo a que utilize o mesmo DUID em mensagens para clientes entre reboots. Este é um requisito do protocolo DHCPv6 (RFC 3315).

**Parâmetros de Entrada**

- **dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6
- **duid_type** Tipo DHCPv6 Server DUID
- **hardware_type** Tipo de hardware (por exemplo, Ethernet)
- **mac_address_msw** Ponteiro para o servidor DHCPv6
- **mac_address_lsw** Ponteiro para o servidor DHCPv6
- **tempo** Valor temporal para DUID

**Valores de devolução**

- **servidor NX_SUCCESS** (0x00) suspenso com sucesso
- **NX_DHCPV6_INVALID_SERVER_DUID** (0XE98) Tipo DUID desconhecido ou não suportado
- **NX_INVALID_PARAMETERS** (0x4D) Entrada inválida sem ponteiro
- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

**Permitido a partir de**

Código de aplicação

**Exemplo**

```
/* Set the DHCPv6 ServerDUID as Link layer plus time, over Ethernet hardware. */
duid_time = SECONDS_SINCE_JAN_1_2000_MOD_32 + rand();

status = nx_dhcpv6_set_server_duid(&dhcp_server_0,1, 0x6,
         physical_address_msw,physical_address_lsw,duid_time);

/* If status is NX_SUCCESS the ServerDUID is successfully set. */
```

## <a name="nx_dhcpv6_server_option_request_handler_set"></a>nx_dhcpv6_server_option_request_handler_set

### <a name="set-the-option-request-handler-for-dhcpv6-server-instance"></a>Desajei o manipulador de pedido de opção para a instância do servidor DHCPv6 

**Prototype**

```
UINT nx_dhcpv6_server_option_request_handler_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     VOID (*dhcpv6_option_request_handler_extended)(
          struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
          UINT option_request, UCHAR *buffer_ptr, 
          UINT *index, UINT available_payload));
```

**Descrição**

Este serviço define o controlador de pedido de opção alargado DHCPv6 Server.

**Parâmetros de Entrada**

- **dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6
- **dhcpv6_option_request_handler_extended** Ponteiro para o controlador de pedido de opções alargadas

**Valores de devolução**

- **NX_SUCCESS** (0x00) Servidor retomado com sucesso
- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

**Permitido a partir de**

Código de Aplicação

**Exemplo**

```
/* Set the option request handler for DHCPv6 Server. */
status = nx_dhcpv6_server_option_request_handler_set(&dhcp_server_0,
         dhcpv6_option_request_handler_extended);

/* If status is NX_SUCCESS the extended handler successfully set. */
```