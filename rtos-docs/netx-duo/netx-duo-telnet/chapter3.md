---
title: Capítulo 3 - Descrição dos serviços Azure RTOS NetX Duo Telnet
description: Este capítulo contém uma descrição de todos os Serviços Telnet Azure RTOS NetX Duo (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 991ec53aaba052b4f42da6e5a541151953121e76
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825712"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-telnet-services"></a>Capítulo 3 - Descrição dos serviços Azure RTOS NetX Duo Telnet

Este capítulo contém uma descrição de todos os Serviços Telnet Azure RTOS NetX Duo (listados abaixo) por ordem alfabética.

Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

- **nx_telnet_client_connect**: *Ligue um cliente Telnet com o endereço IPv4*
- **nxd_telnet_client_connect**: *Ligue um cliente Telnet IPv6 com o endereço IPv6*
- **nx_telnet_client_create**: *Criar um cliente Telnet*
- **nx_telnet_client_delete**: *Eliminar um Cliente Telnet*
- **nx_telnet_client_disconnect**: *Desconecte um Cliente Telnet*
- **nx_telnet_client_packet_receive**: *Receber pacote via Cliente Telnet*
- **nx_telnet_client_packet_send**: *Enviar pacote através do Cliente Telnet*
- **nx_telnet_server_create**: *Criar um servidor Telnet*
- **nx_telnet_server_delete**: *Eliminar um Servidor Telnet*
- **nx_telnet_server_disconnect**: *Desconecte um Cliente Telnet*
- **nx_telnet_server_get_open_connection_count**: *Recuperar o número de ligações abertas*
- **nx_telnet_server_packet_send**: *Enviar pacote através da ligação ao Cliente*
- **nx_telnet_server_packet_pool_set**: *Definir a piscina de pacotes como piscina de pacotes Telnet Server*
- **nx_telnet_server_start**: *Iniciar um Servidor Telnet*
- **nx_telnet_server_stop**: *Parar um Servidor Telnet*

## <a name="nx_telnet_client_connect"></a>nx_telnet_client_connect

Ligue um cliente Telnet com endereço IPv4

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                              ULONG server_ip, UINT server_port, 
                              ULONG wait_option);
```

### <a name="description"></a>Descrição

Este serviço tenta ligar a instância do Cliente Telnet anteriormente criada ao Servidor no IP e na porta especificados utilizando um endereço IPv4 para o Servidor Telnet. Este serviço insere efetivamente o endereço IP do servidor ULONG num NXD_ADDRESS bloco de controlo e define a versão IP para 4 antes de ligar para o serviço *nxd_telnet_client_connect* descrito abaixo.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr**: Ponteiro para o bloco de controlo do cliente Telnet.
- **server_ip**: Endereço IPv4 do Servidor Telnet.
- **server_port**: Porta de Servidor TCP (Telnet Server é a porta 23).
- **wait_option**: Define quanto tempo o serviço vai esperar pela ligação do Cliente Telnet. As opções de espera são definidas da seguinte forma:

    - **Valor de tempo limite**: (0x00000001 a 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do Servidor Telnet.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF)A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor Telnet responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Ligação de cliente bem sucedida.
- **NX_TELNET_NOT_DISCONNECTED**: (0xF4) Cliente já ligado.
- NX_PTR_ERROR: (0x07) Ponteiro do Cliente Inválido.
- NX_IP_ADDRESS_ERROR: (0x21) Endereço IP inválido.
- NX_CALLER_ERROR: (0x11) Inválido de serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IP address 1.2.3.4 and port 23.  */
status =  nx_telnet_client_connect(&my_client, IP_ADDRESS(1,2,3,4), 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nxd_telnet_client_connect"></a>nxd_telnet_client_connect

Ligue um Cliente Telnet com endereço IPv6 ou IPv4

### <a name="prototype"></a>Prototype

```c
UINT nxd_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                               NXD_ADDRESS *server_ip_address, 
                               UINT server_port, 
                               ULONG wait_option);
```

### <a name="description"></a>Descrição

Este serviço tenta ligar a instância do Cliente Telnet anteriormente criada ao Servidor no IP especificado e na porta utilizando o endereço IPv6 do Telnet Server. Este serviço pode ter um endereço IPv4 ou IPv6, mas deve ser contido na NXD_ADDRESS server_ip_address *variável.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr**: Ponteiro para o bloco de controlo do cliente Telnet.
- **server_ip_address**: Endereço IP do Servidor.
- **server_port**: Porta de Servidor TCP (Telnet Server é a porta 23).
- **wait_option**: Define quanto tempo o serviço vai esperar pela ligação do Cliente Telnet. As opções de espera são definidas da seguinte forma:

    - **Valor de tempo limite**: (0x00000001 a 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do Servidor Telnet.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor Telnet responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Ligação de cliente bem sucedida.
- **NX_TELNET_ERROR:**(0xF0) Erro de ligação do cliente.
- **NX_TELNET_NOT_DISCONNECTED**: (0xF4) Cliente já ligado.
- NX_PTR_ERROR: (0x07) Ponteiro do Cliente Inválido.
- NX_CALLER_ERROR: (0x11) Inválido de serviço.
- NX_TELNET_INVALID_PARAMETER: (0xF5) Entrada inválida sem ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IPv6 address 20010db1:0:f101::101 and port 23.  */
status =  nxd_telnet_client_connect(&my_client, &server_ip_address, 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nx_telnet_client_create"></a>nx_telnet_client_create

Criar um Cliente Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_client_create(NX_TELNET_CLIENT *client_ptr, 
                             CHAR *client_name, NX_IP *ip_ptr, 
                             ULONG window_size);
```

### <a name="description"></a>Descrição

Este serviço cria uma instância do Cliente Telnet.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr**: Ponteiro para o bloco de controlo do cliente Telnet.
- **client_name**: Caso do Cliente.
- **ip_ptr**: Indicação para a instância IP.
- **window_size**: Tamanho da TCP receber janela para este Cliente.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) O Cliente bem sucedido cria.
- **NX_TELNET_ERROR:**(0xF0) A tomada cria erro.
- NX_PTR_ERROR: (0x07) Cliente inválido ou ponteiro IP.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Create the Telnet Client instance “my_client” on the IP instance “ip_0”.  */
status =  nx_telnet_client_create(&my_client, “My Telnet Client”, &ip_0, 2048);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   created.  */
```
## <a name="nx_telnet_client_delete"></a>nx_telnet_client_delete

Excluir um Cliente Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_client_delete(NX_TELNET_CLIENT *client_ptr);
```

### <a name="description"></a>Descrição

Este serviço elimina uma instância do Cliente Telnet anteriormente criada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr**: Ponteiro para o bloco de controlo do cliente Telnet.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) O Cliente bem sucedido apaga.
- **NX_TELNET_NOT_DISCONNECTED**: (0xF4) Cliente ainda ligado.
- NX_PTR_ERROR: (0x07) Ponteiro do Cliente Inválido.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Delete the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_delete(&my_client);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   deleted.  */
```

## <a name="nx_telnet_client_disconnect"></a>nx_telnet_client_disconnect

Desligar um Cliente Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_client_disconnect(NX_TELNET_CLIENT *client_ptr, ULONG wait_option);
```

### <a name="description"></a>Descrição

Este serviço desliga uma instância do Cliente Telnet anteriormente ligada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr**: Ponteiro para o bloco de controlo do cliente Telnet.
- **wait_option**: Define quanto tempo o serviço esperará pela desconexão do Cliente Telnet. As opções de espera são definidas da seguinte forma:

    - **Valor de tempo limite**: (0x00000001 a 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do Servidor Telnet.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor Telnet responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Desconexão do Cliente bem sucedido.
- **NX_TELNET_NOT_CONNECTED:**(0xF3) Cliente não ligado.
- NX_PTR_ERROR: (0x07) Ponteiro do Cliente Inválido.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.


### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c

/* Disconnect the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_disconnect(&my_client, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   disconnected.  */
```

## <a name="nx_telnet_client_packet_receive"></a>nx_telnet_client_packet_receive

Receber pacote via Cliente Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_client_packet_receive(NX_TELNET_CLIENT *client_ptr, 
                                     NX_PACKET **packet_ptr, 
                                     ULONG wait_option);
```

### <a name="description"></a>Descrição

Este serviço recebe um pacote da instância do Cliente Telnet anteriormente ligada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr**: Ponteiro para o bloco de controlo do cliente Telnet.
- **packet_ptr**: Ponte para o destino do pacote recebido.
- **wait_option**: Define quanto tempo o serviço esperará pela receção do pacote do Cliente Telnet. As opções de espera são definidas da seguinte forma:
    - **Valor de tempo limite**: (0x00000001 a 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do Servidor Telnet.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor Telnet responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Pacote cliente bem sucedido receber.
- NX_PTR_ERROR: (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR: (0x11) Inválido de serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c

/* Receive a packet from the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 100);

/* If status is NX_SUCCESS the “my_packet” pointer contains data received from
   the Telnet Client connection.  */
```
## <a name="nx_telnet_client_packet_send"></a>nx_telnet_client_packet_send

Enviar pacote através do Cliente Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_client_packet_send(NX_TELNET_CLIENT *client_ptr, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a>Descrição

Este serviço envia um pacote através da instância do Cliente Telnet anteriormente ligada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr**: Ponteiro para o bloco de controlo do cliente Telnet.
- **packet_ptr**: Ponter para o pacote a enviar.
- **wait_option**: Define quanto tempo o serviço esperará pelo envio do pacote do Cliente Telnet. As opções de espera são definidas da seguinte forma:
    - **Valor de tempo limite**: (0x00000001 a 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do Servidor Telnet.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor Telnet responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Pacote de cliente bem sucedido enviar.
- **NX_TELNET_ERROR**: (0xF0) Enviar o pacote falhado – o chamador é responsável pela libertação do pacote.
- NX_PTR_ERROR: (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR: (0x11) Inválido de serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Send a packet via the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_send(&my_client, my_packet, 100);
/* If status is NX_SUCCESS the packet was successfully sent.  */

```

## <a name="nx_telnet_server_create"></a>nx_telnet_server_create

Criar um Servidor Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_server_create(NX_TELNET_SERVER *server_ptr, CHAR *server_name, NX_IP *ip_ptr, 
                             VOID *stack_ptr, ULONG stack_size, 
                             void (*new_connection)(struct NX_TELNET_SERVER_STRUCT*telnet_server_ptr, 
                                                    UINT logical_connection), 
                             void (*receive_data)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                  UINT logical_connection, NX_PACKET *packet_ptr), 
                             void (*connection_end)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                    UINT logical_connection));

```

### <a name="description"></a>Descrição

Este serviço cria uma instância do Telnet Server na instância IP especificada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr**: Ponteiro para o bloco de controlo do Servidor Telnet.
- **server_name**: Nome da instância telnet Server.
- **ip_ptr**: Ponteiro para a instância IP associada.
- **stack_ptr**: Ponteiro para empilhar para o fio interno do Servidor.
- **sack_size:** Tamanho da pilha, bytes.
- **new_connection:** Ponteiro de função de rotina de chamada de aplicação. Esta rotina é chamada sempre que um novo pedido de ligação ao Cliente Telnet é detetado pelo Servidor.
- **receive_data:** Ponteiro de função de rotina de chamada de aplicação. Esta rotina é chamada sempre que um novo dado do Cliente Telnet está presente na ligação. Esta rotina é responsável pela libertação do pacote.
- **end_connection:** Ponteiro de função de rotina de chamada de aplicação. Esta rotina é chamada sempre que uma ligação telnet Cliente é desligada pelo Cliente ou o tempo de ligação do Cliente termina ("tempo de tempo de atividade" expira). O Servidor também pode desligar-se através do serviço *nx_telnet_server_disconnect* descrito abaixo.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Servidor de sucesso criar.
- NX_PTR_ERROR: (0x07) Inválido Servidor, IP, stack ou guiadores de chamadas de aplicação.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Create a Telnet Server instance “my_server”.  */
status =  nx_telnet_server_create(&my_server, "Telnet Server", &ip_0, 
                                   pointer, 2048, telnet_new_connection, 
                                   telnet_receive_data, telnet_connection_end);


/* If status is NX_SUCCESS the Telnet Server was successfully created.  */
```
## <a name="nx_telnet_server_delete"></a>nx_telnet_server_delete

Excluir um Servidor Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_server_delete(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a>Descrição

Este serviço elimina uma instância telnet server previamente criada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr**: Ponteiro para o bloco de controlo do Servidor Telnet.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Servidor de sucesso eliminar.
- NX_PTR_ERROR: (0x07) Ponteiro do Servidor Inválido.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Delete the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_delete(&my_server);

/* If status is NX_SUCCESS the Telnet Server was successfully deleted.  */
```

## <a name="nx_telnet_server_disconnect"></a>nx_telnet_server_disconnect

Desligar um Cliente Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_server_disconnect(NX_TELNET_SERVER *server_ptr, UINT logical_connection);
```

### <a name="description"></a>Descrição

Este serviço desliga um Cliente previamente ligado nesta instância do Telnet Server. Esta rotina é normalmente chamada da função de retorno de dados de receção da aplicação em resposta a uma condição detetada nos dados recebidos.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr**: Ponteiro para o bloco de controlo do Servidor Telnet.
- **logical_connection**: Ligação lógica correspondente à ligação do Cliente neste Servidor. O valor válido varia entre 0 e NX_TELENET_MAX_CLIENTS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Desconexão do servidor de sucesso.
- **NX_TELNET_ERROR:**(0xF0) A desconexão do servidor falhou.
- NX_OPTION_ERROR: (0x0A) Ligação lógica inválida.
- NX_PTR_ERROR: (0x07) Ponteiro do Servidor Inválido.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c

/* Disconnect the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_disconnect(&my_server, 2);

/* If status is NX_SUCCESS the Client on logical connection 2 was 
   disconnected.  */
```

## <a name="nx_telnet_server_get_open_connection_count"></a>nx_telnet_server_get_open_connection_count

Número de devolução de ligações atualmente abertas

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_server_get_open_connection_count(NX_TELNET_SERVER *server_ptr, UINT *connection_count);
```

### <a name="description"></a>Descrição

Este serviço devolve o número de Clientes Telnet atualmente ligados.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr**: Ponteiro para o bloco de controlo do Servidor Telnet.
- **Connection_count**: Ponteiro para a memória para armazenar contagem de ligação

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Conclusão bem sucedida.
- NX_PTR_ERROR: (0x07) Ponteiro do Servidor Inválido.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Get the number of Telnet Clients connected to the Server. */

status =  nx_telnet_server_get_open_connection_count(&my_server, &conn_count);

/* If status is NX_SUCCESS the conn_count holds the number of open connections.  */

```

## <a name="nx_telnet_server_packet_send"></a>nx_telnet_server_packet_send

Enviar pacote através da ligação ao Cliente

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_server_packet_send(NX_TELNET_SERVER *server_ptr, 
                                  UINT logical_connection, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a>Descrição

Este serviço envia um pacote para a ligação ao Cliente nesta instância do Telnet Server. Esta rotina é normalmente chamada da função de retorno de dados de receção da aplicação em resposta a uma condição detetada nos dados recebidos.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr**: Ponteiro para o bloco de controlo do Servidor Telnet.
- **logical_connection**: Ligação lógica correspondente à ligação do Cliente neste Servidor. O valor válido varia entre 0 e NX_TELENET_MAX_CLIENTS.
- **packet_ptr**: Ponteiro para o pacote recebido.
- **wait_option**: Define quanto tempo o serviço irá esperar pelo envio do pacote Do Servidor Telnet. As opções de espera são definidas da seguinte forma:
    - **Valor de tempo limite**: (0x00000001 a 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do Servidor Telnet.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor Telnet responda ao pedido. 

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Envio de pacote bem sucedido.
- **NX_TELNET_FAILED:**(0xF2) A tomada TCP enviada falhou.
- NX_OPTION_ERROR: (0x0A) Ligação lógica inválida.
- NX_PTR_ERROR: (0x07) Ponteiro do Servidor Inválido.
- NX_CALLER_ERROR: (0x11) Inválido de serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Send a packet to the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_packet_send(&my_server, 2, my_packet, 100);

/* If status is NX_SUCCESS the packet was sent to the Client on logical 
   connection 2.  */
```

## <a name="nx_telnet_server_packet_pool_set"></a>nx_telnet_server_packet_pool_set

Conjunto previamente criado pool de pacotes como piscina Telnet Server

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_server_packet_pool_set(NX_TELNET_SERVER *server_ptr, NX_PACKET_POOL *packet_pool_ptr);

```

### <a name="description"></a>Descrição

Este serviço define um conjunto de pacotes previamente criado como o pool de pacotes telnet Server se NX_TELNET_SERVER_USER_CREATE_PACKET_POOL for definida. Também requer que não NX_TELNET_SERVER_OPTION_DISABLE ser definido de modo a que o Telnet Server precise de um pacote de piscina para transmitir opções telnet aos clientes telnet.

Isto permite que as aplicações criem o conjunto de pacotes em memórias diferentes, por exemplo, sem memória de cache, do que a pilha do Servidor Telnet. Note que se esta função não verificar se o conjunto de pacotes do Telnet Server já está definido. Se for chamado a um ponteiro de piscina telnet server não nulo, ele substituirá e substituirá a piscina de pacotes existente por um pacote de piscina apontado pelo ponteiro de entrada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr**: Ponteiro para o bloco de controlo do servidor Telnet
- **packet_pool_ptr**: Ponteiro para piscina de pacotes previamente criada

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Coloque a piscina com sucesso.
- NX_PTR_ERROR: (0x07) Ponteiro do Servidor Inválido.

### <a name="allowed-from"></a>Permitido a partir de

Init, Threads

### <a name="example"></a>Exemplo

```c
status =  nx_packet_pool_create(&telnet_server_packet_pool, 
                                "Telnet Server Packet Pool", 
                                telnet_server_pool_area, 600*10);

/* Set the packet pool as the Telnet Server packet pool.   */
status =  nx_telnet_server_packet_pool_set(&my_server, &telnet_server_packet_pool);

/* If status is NX_SUCCESS the packet pool is set as Telnet Server pool.  */
```
## <a name="nx_telnet_server_start"></a>nx_telnet_server_start

Iniciar um Servidor Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_server_start(NX_TELNET_SERVER *server_ptr);

```

### <a name="description"></a>Descrição

Este serviço inicia uma instância telnet server previamente criada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr**: Ponteiro para o bloco de controlo do Servidor Telnet.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Começou com sucesso.
- **NX_TELNET_NO_PACKET_POOL**: (0xF6) Sem conjunto de piscina de pacotes
- NX_PTR_ERROR: (0x07) Ponteiro do Servidor Inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Start the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_start(&my_server);

/* If status is NX_SUCCESS the Server was started.  */
```

## <a name="nx_telnet_server_stop"></a>nx_telnet_server_stop

Parar um Servidor Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_server_stop(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a>Descrição

Este serviço para uma instância do Telnet Server previamente criada e iniciou.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr**: Ponteiro para o bloco de controlo do Servidor Telnet.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Parou com sucesso
- NX_PTR_ERROR: (0x07) Ponteiro do Servidor Inválido.
- NX_CALLER_ERROR: (0x11) Inválido de serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Stop the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_stop(&my_server);

/* If status is NX_SUCCESS the Server was stopped.  */
```