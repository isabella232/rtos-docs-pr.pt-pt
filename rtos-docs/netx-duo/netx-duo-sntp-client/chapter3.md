---
title: Capítulo 3 - Descrição dos Serviços de ClienteS SNTP SNTP da Azure RTOS NetX Duo SNTP
description: Este capítulo contém uma descrição de todos os serviços do Cliente NetX Duo SNTP (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 75b2b878cd084ca1c1cdd1eed4333d303fe32ad6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825747"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-sntp-client-services"></a>Capítulo 3 - Descrição dos Serviços de ClienteS SNTP SNTP da Azure RTOS NetX Duo SNTP

Este capítulo contém uma descrição de todos os serviços do Cliente Azure RTOS NetX Duo SNTP (listados abaixo) por ordem alfabética.

Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

- **nx_sntp_client_create**: *Criar o Cliente SNTP*
- **nx_sntp_client_delete**: *Eliminar o Cliente SNTP*
- **nx_sntp_client_get_local_time**: *Obtenha a hora do cliente SNTP local*
- **nx_sntp_client_get_local_time_extended**: *Obtenha a hora do cliente SNTP local*
- **nx_sntp_client_initialize_broadcast**: *Inicialize o cliente para a operação de transmissão IPv4*
- **nxd_sntp_client_initialize_broadcast**: *Inicialize o cliente para a operação de transmissão IPv6 ou IPv4*
- **nx_sntp_client_initialize_unicast**: *Inicialize o cliente para a operação unicast IPv4*
- **nxd_sntp_client_initialize_unicast**: *Inicialize o cliente para a operação unicast IPv4 ou IPv6*
- **nx_sntp_client_receiving_udpates**: *O Cliente está atualmente a receber atualizações válidas da SNTP*
- **nx_sntp_client_request_unicast_time**: *Enviar um pedido unicast diretamente para o Servidor NTP*
- **nx_sntp_client_run_broadcast**: *Executar o Cliente em modo de transmissão*
- **nx_sntp_client_run_unicast**: *Executar o Cliente em modo unicast*
- **nx_sntp_client_set_local_time**: *Definir o cliente SNTP na hora local*
- **nx_sntp_client_set_time_update_notify**: *Desembaraque a chamada de atualização SNTP*
- **nx_sntp_client_stop**: *Pare a linha do cliente SNTP*
- **nx_sntp_client_utility_display_date_and_time**: *Mostrar tempo de NTP em segundos*
- **nx_sntp_client_utility_msecs_to_fraction**: *Converter milissegundos para um componente de fração NTP*
- **nx_sntp_client_utility_usecs_to_fraction**: *Converter microsegundos num componente de fração NTP*
- **nx_sntp_client_utility_fraction_to_usecs**: *Converter um componente de fração NTP em microsegundos*


## <a name="nx_sntp_client_create"></a>nx_sntp_client_create

Criar um Cliente SNTP

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_create(NX_SNTP_CLIENT *client_ptr, NX_IP *ip_ptr,  
                                     UINT iface_index, 
                                     NX_PACKET_POOL *packet_pool_ptr, 
UINT (*leap_second_handler)(NX_SNTP_CLIENT *client_ptr, 
                                        UINT indicator), 
UINT (*kiss_of_death_handler)(NX_SNTP_CLIENT *client_ptr, 
                               NX_SNTP_TIME_MESSAGE *server_time_msg),
VOID (random_number_generator)(struct NX_SNTP_CLIENT_STRUCT 
                                *client_ptr, ULONG *rand));

```

### <a name="description"></a>Descrição

Este serviço cria uma instância do Cliente SNTP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para bloco de controlo do cliente SNTP

- **ip_ptr** Indicação para o cliente ip instância

- **iface_index** Índice para interface de rede SNTP

- **packet_pool_ptr** Ponteiro para piscina de pacotes de cliente

- **leap_second_handler** Chamada para resposta de candidatura ao salto iminente em segundo lugar

- **kiss_of_death_handler** Callback para resposta de aplicação para receber pacote kiss of Death

- **random_number_generator** Chamada para serviço gerador de números aleatórios

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Criação de clientes bem sucedidos

- **NX_SNTP_INSUFFICIENT_PACKET_PAYLOAD** (0xD2A) Entrada inválida sem ponteiro

- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

- interface de rede NX_INVALID_INTERFACE (0x4C) Inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```C
/* Create the SNTP Client on the primary interface. */
UINT iface_index = 0;
status =  nx_sntp_client_create(&demo_client, 
                     iface_index, &client_ip, 
&client_packet_pool, leap_second_handler, 
                    kiss_of_death_handler, 
NULL /* no random_number_generator callback */);

/* If status is NX_SUCCESS an SNTP Client instance was successfully
   created.  */

```

## <a name="nx_sntp_client_delete"></a>nx_sntp_client_delete

Excluir um Cliente SNTP

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_delete(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Descrição

Este serviço elimina uma instância do Cliente SNTP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para bloco de controlo do cliente SNTP

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Criação de clientes bem sucedidos

- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Inválido de serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Delete the SNTP Client. */
status =  nx_sntp_client_delete(&demo_client);

/* If status is NX_SUCCESS an SNTP Client 
   instance was successfully deleted.  */

```

## <a name="nx_sntp_client_get_local_time"></a>nx_sntp_client_get_local_time

Obtenha a hora local do Cliente SNTP

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_get_local_time(NX_SNTP_CLIENT *client_ptr , 
                                                ULONG *seconds, 
                                                ULONG *fraction, 
                                                CHAR *buffer);

```

### <a name="description"></a>Descrição

Este serviço obtém a hora local do Cliente SNTP com uma entrada de chaveiro de opção para receber os dados em formato de mensagem de cadeia.

Este serviço é precotado. Os desenvolvedores são encorajados a migrar para *nx_sntp_client_get_local_time_extended*().

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para bloco de controlo do cliente SNTP

- **segundos** Ponteiro para segundos locais

- **fração** Componente de fração de tempo local

- **tampão** Ponteiro para tampão para escrever dados de tempo

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Criação de clientes bem sucedidos

- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Inválido de serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Get the SNTP Client local time without the 
   string message option. */

ULONG base_seconds;
ULONG base_fraction;

status =  nx_sntp_client_get_local_time(&demo_client, 
                                       &base_seconds, 
                                       &base_fraction, 
                                       NX_NULL);
/* If status is NX_SUCCESS an SNTP Client time was successfully
   retrieved.  */

```

## <a name="nx_sntp_client_get_local_time_extended"></a>nx_sntp_client_get_local_time_extended

Obtenha o horário prolongado do Cliente SNTP local

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_get_local_time_extended(
                 NX_SNTP_CLIENT *client_ptr,
                 ULONG *seconds, 
                 ULONG *fraction, 
                 CHAR *buffer
                 UINT buffer_size);

```

### <a name="description"></a>Descrição

Este serviço obtém o tempo sNTP cliente estendido local com uma entrada de chaveiro de opção para receber os dados em formato de mensagem de cadeia.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para bloco de controlo do cliente SNTP

- **segundos** Ponteiro para segundos locais

- **fração** Ponteiro para componente de fração

- **tampão** Ponteiro para tampão para escrever dados de tempo

- **buffer_size** Comprimento do tampão

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Criação de clientes bem sucedidos

- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Inválido de serviço

- NX_SIZE_ERROR (0x09) Verifique buffer_size falhar

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Get the SNTP Client local time without the 
   string message option. */

#define BUFSIZE 50

ULONG seconds;
ULONG fraction;
CHAR  buffer[BUFSIZE];

status =  nx_sntp_client_get_local_time_extended(&demo_client, 
                                                &seconds, 
                                                &fraction, 
                                                buffer, 
                                                BUFSIZE);

/* If status is NX_SUCCESS an SNTP Client 
   time was successfully retrieved.  */

```

## <a name="nx_sntp_client_initialize_broadcast"></a>nx_sntp_client_initialize_broadcast

Inicializar o Cliente para operação de transmissão

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                                    ULONG multicast_server_address, 
                                    ULONG broadcast_time_servers);


```

### <a name="description"></a>Descrição

Este serviço inicializa o Cliente para a operação de transmissão, definindo o endereço IP do Servidor SNTP e rubricando parâmetros e intervalos de arranque SNTP. Se os endereços multicast e de transmissão não forem nulos, o endereço multicast é selecionado. Se ambos os endereços forem nulos, um erro é devolvido. Note que isto suporta apenas endereços de servidor IPv4.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para bloco de controlo do cliente SNTP

- **multicast_server_address** Endereço multicast SNTP

- **broadcast_time_server** Endereço de transmissão de servidor SNTP

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Criação de Clientes bem sucedidos

- **NX_INVALID_PARAMETERS** (0x4D) Entrada inválida sem ponteiro

- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Inválido de serviço

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```C
/* Initialize the client for broadcast operation.  */
status =  nx_sntp_client_initialize_broadcast(client_ptr,0x0,
                            NX_NULL, IP_ADDRESS(192,2,2,255);

/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nxd_sntp_client_initialize_broadcast"></a>nxd_sntp_client_initialize_broadcast

Inicializar o Cliente para a operação de transmissão IPv4 ou IPv6

### <a name="prototype"></a>Prototype

```C
UINT nxd_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                            NXD_ADDRESS *multicast_server_address, 
                            NXD_ADDRESS *broadcast_server_address);

```

### <a name="description"></a>Descrição

Este serviço inicializa o Cliente para a operação de transmissão, configurando o endereço IP do Servidor SNTP e rubricando parâmetros e intervalos de arranque SNTP. Se os ponteiros de endereços de difusão e multicast não forem nulos, o endereço multicast é selecionado. Se ambos os ponteiros de endereço forem nulos, um erro é devolvido. Isto suporta os tipos de endereços IPv4 e IPv6. Note que o IPv6 não suporta a transmissão, pelo que o ponteiro do endereço de transmissão está definido para IPv6, um erro é devolvido.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para bloco de controlo do cliente SNTP

- **multicast_server_address** Endereço multicast do servidor SNTP

- **broadcast_server_address** Endereço de transmissão de servidor SNTP

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Cliente iniciais com sucesso

- NX_SNTP_PARAM_ERROR (0xD0D) Entrada inválida sem ponteiro

- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Inválido de serviço


### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```C
/* Initialize the client for broadcast operation.  */
NXD_ADDRESS broadcast_server;

Broadcast_server.nxd_ip_address = NX_IP_VERSION_V6;
Broadcast_server.nxd_ip_address.v6[0] = 0x20010db1;
Broadcast_server.nxd_ip_address.v6[1] = 0x0f101;
Broadcast_server.nxd_ip_address.v6[2] = 0x0;
Broadcast_server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_broadcast(client_ptr,0x0,
                                  NX_NULL, &broadcast_server)


/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nx_sntp_client_initialize_unicast"></a>nx_sntp_client_initialize_unicast

Crie o Cliente SNTP para funcionar em unicast

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                        ULONG unicast_time_server);

```
### <a name="description"></a>Descrição

Este serviço inicializa o Cliente para a operação unicast, definindo o endereço IP do Servidor SNTP e rubricando parâmetros e intervalos de arranque SNTP. Note que isto suporta apenas endereços de servidor IPv4.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para bloco de controlo do cliente SNTP

- **unicast_time_server** Endereço IP do servidor SNTP

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Cliente iniciais com sucesso

- NX_INVALID_PARAMETERS (0x4D) Entrada inválida sem ponteiro

- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Inválido de serviço

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```C
/* Initialize the Client for unicast operation.  */
status =  nx_sntp_client_initialize_unicast(&client_ptr, 
                                 IP_ADDRESS(192,2,2,1));


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```


## <a name="nxd_sntp_client_initialize_unicast"></a>nxd_sntp_client_initialize_unicast

Configurar o Cliente SNTP para funcionar em IPv4 ou IPv6 unicast

### <a name="prototype"></a>Prototype

```C
UINT nxd_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                  NXD_ADDRESS *unicast_time_server);

```

### <a name="description"></a>Descrição

Este serviço inicializa o Cliente para a operação unicast, configurando o endereço IP do SNTP Server e rubricando os parâmetros e intervalos de arranque SNTP. Isto suporta os tipos de endereços IPv4 e IPv6.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para bloco de controlo do cliente SNTP

- **unicast_time_server** Endereço IP do servidor SNTP

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Cliente iniciais com sucesso

- NX_INVALID_PARAMETERS (0x4D) Entrada inválida sem ponteiro

- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Inválido de serviço

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```C
/* Initialize the Client for unicast operation.  */
NXD_ADDRESS unicast_server;

unicast _server.nxd_ip_address = NX_IP_VERSION_V6;
unicast _server.nxd_ip_address.v6[0] = 0x20010db1;
unicast _server.nxd_ip_address.v6[1] = 0x0f101;
unicast _server.nxd_ip_address.v6[2] = 0x0;
unicast _server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_unicast(&client_ptr, 
                                        *unicast_server); 


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```

## <a name="nx_sntp_client_receiving_updates"></a>nx_sntp_client_receiving_updates

Indicar se o Cliente está a receber atualizações válidas

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_receiving_updates(NX_SNTP_CLIENT *client_ptr, 
                                           UINT *receive_status);

```

### <a name="description"></a>Descrição

Este serviço indica se o Cliente está a receber atualizações SNTP válidas. Se o lapso de tempo máximo sem uma atualização válida ou limite de atualizações inválidas consecutivas for ultrapassado, o estado de receção é devolvido como falso. Note que o Cliente SNTP ainda está em execução e se a aplicação pretende reiniciar o Cliente SNTP com outro servidor unicast ou de difusão/multicast deve parar o Cliente SNTP utilizando o serviço *nx_sntp_client_stop,* reinitializar o Cliente utilizando um dos serviços de inicialização com outro servidor.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para o bloco de controlo do cliente SNTP.

- **receive_status** Ponteiro para indicador se o Cliente está a receber atualizações válidas.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Cliente recebeu com sucesso o estado de atualização

- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_receiving_updates(client_ptr, 
                                     &receive_status);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is currently receiving valid updates.  */

```

## <a name="nx_sntp_client_request_unicast_time"></a>nx_sntp_client_request_unicast_time

Envie um pedido unicast diretamente para o Servidor NTP


### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_request_unicast_time(NX_SNTP_CLIENT *client_ptr, 
                                                  UINT wait_option);
```

### <a name="description"></a>Descrição

Este serviço permite que a aplicação envie diretamente um pedido unicast para o servidor NTP assíncronamente a partir da tarefa de thread do Cliente SNTP. A opção de espera especifica quanto tempo esperar por uma resposta. Se for bem sucedido, a aplicação pode utilizar outros serviços do Cliente SNTP para obter a última hora. Consulte a secção **SNTP Asynchronous Unicast Requests** para mais detalhes.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para o bloco de controlo do cliente SNTP.

- **Wait_option** Opção de espera para resposta NTP em carraças tempor.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Cliente envia e recebe com sucesso atualização unicast

- **NX_SNTP_CLIENT_NOT_STARTED** (0xD0B) Linha de cliente não começou

- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Inválido de serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_request_unicast_time(client_ptr, 400);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is received a valid response to the unicast request.  */

```

## <a name="nx_sntp_client_run_broadcast"></a>nx_sntp_client_run_broadcast

Executar o Cliente em modo de transmissão

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_run_broadcast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Descrição

Este serviço inicia o Cliente no modo de transmissão onde aguardará para receber transmissões do servidor SNTP. Se for recebida uma mensagem SNTP de transmissão válida, o tempo limite de tempo do cliente SNTP para o lapso máximo sem uma atualização e contagem de mensagens inválidas consecutivas recebidas são reiniciadas. Se um destes limites for ultrapassado, o Cliente SNTP define o estado do servidor para inválido, embora ainda espere receber atualizações. A aplicação pode sondar a tarefa do Cliente SNTP para o estado do servidor, e se inválida parar o Cliente SNTP e reinitilizá-lo com outro endereço de transmissão SNTP. Também pode mudar para um servidor SNTP unicast.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para o bloco de controlo do cliente SNTP.

### <a name="return-values"></a>Valores de devolução

- **estado** -------- Estado de conclusão real

- **cliente NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) já começou

- **NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) Cliente não inicializado

- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Inválido de serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Start Client running in broadcast mode.  */
status =  nx_sntp_client_run_broadcast(client_ptr);

/* If status is NX_SUCCESS, the client is successfully started.  */

```

## <a name="nx_sntp_client_run_unicast"></a>nx_sntp_client_run_unicast

Executar o Cliente em modo unicast

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_run_unicast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Descrição

Este serviço inicia o Cliente no modo unicast onde envia periodicamente um pedido unicast para o seu SNTP Server para uma atualização de tempo. Se for recebida uma mensagem SNTP válida, o tempo limite de tempo do cliente SNTP para o lapso máximo sem atualização, o intervalo inicial de votação e a contagem de mensagens inválidas consecutivas recebidas são reiniciados. Se um destes limites for ultrapassado, o Cliente SNTP define o estado do Servidor para inválido, embora ainda faça sondagem e aguarde para receber atualizações. A aplicação pode sondar a tarefa do Cliente SNTP para o estado do servidor, e se inválida parar o Cliente SNTP e reinitilizá-lo com outro endereço unicast SNTP. Também pode mudar para um servidor SNTP de transmissão.

.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para o bloco de controlo do cliente SNTP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) iniciou com sucesso o Cliente em modo unicast

- **cliente NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) já começou

- **NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) Cliente não inicializado

- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

- NX_CALLER_ERROR (0x11) Inválido de serviço


### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Start the Client in unicast mode. */
status =  nx_sntp_client_run_unicast(client_ptr);

/* If status = NX_SUCCESS, the Client was successfully started.  */

```

## <a name="nx_sntp_client_set_local_time"></a>nx_sntp_client_set_local_time

Desente o cliente SNTP local

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_set_local_time(NX_SNTP_CLIENT *client_ptr , 
                                ULONG seconds, ULONG fraction);

```

### <a name="description"></a>Descrição

Este serviço define o cliente SNTP local com o tempo de entrada, em formato SNTP, por exemplo, segundos e "fração" que é o formato para colocar frações de segundo em formato hexadecimal. Destina-se a atualizar o cliente SNTP local a partir de um cronometreiro independente, por exemplo, um relógio em tempo real. O protocolo SNTP destina-se a atualizações de tempo SNTP para evitar que o tempo do relógio local se "deslove". As atualizações de tempo do servidor SNTP podem ser, mas não se destinam a ser a única entrada para o cliente SNTP local se não houver um time keeper independente no dispositivo de aplicação.

Esta API também pode ser usada para dar ao Cliente SNTP um tempo base antes de iniciar a linha do Cliente SNTP. A hora local do Cliente SNTP é comparada com as atualizações recebidas para dados de tempo válidos. Pela primeira vez atualização recebida, pode haver uma discrepância muito grande. Portanto, existe uma opção para o Cliente SNTP ignorar a discrepância na primeira atualização. Desta forma, o Cliente SNTP pode começar sem uma hora de base. O tempo de entrada pode ser obtido a partir de tempos conhecidos de época (normalmente disponíveis na Internet) e são calculados como o número de segundos desde 1 de janeiro de 1900 (até 2036 quando uma nova 'época' será iniciada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para bloco de controlo do cliente SNTP

- **segundos** Componente de segundos da entrada do tempo

- **fração** Componente de subsegundos no formato de fração SNTP

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) definir com sucesso a hora local

- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Inicialização

### <a name="example"></a>Exemplo

```C
/* Set the SNTP Client local time. */
base_seconds =  0xd2c50b71;
base_fraction = 0xa132db1e;

status =  nx_sntp_client_set_local_time(&demo_client, 
                                        base_seconds, 
                                        base_fraction);

/* If status is NX_SUCCESS an SNTP Client time 
   was successfully set.  */

```

## <a name="nx_sntp_client_set_time_update_notify"></a>nx_sntp_client_set_time_update_notify

Desaveize a chamada de atualização SNTP

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_set_time_update_notify(NX_SNTP_CLIENT *client_ptr, 
                           VOID (time_update_cb)(NX_SNTP_TIME_MESSAGE 
                        *time_update_ptr, NX_SNTP_TIME *local_time)));

```

### <a name="description"></a>Descrição

Este serviço configura a chamada para notificar a aplicação quando o Cliente SNTP recebe uma atualização de tempo válida. Fornece a mensagem SNTP real e a hora local do Cliente SNTP (geralmente a mesma) em formato NTP. A aplicação pode utilizar os dados NTP diretamente ou ligar para o *serviço nx_sntp_client_utility_display_date_time* para converter o tempo em formato legível humano.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para bloco de controlo do cliente SNTP

- **time_update_cb** Função de retorno do ponteiro

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) configurar com sucesso o retorno

- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Inicialização

### <a name="example"></a>Exemplo

```C
/* Set the SNTP Client time update callback. */
VOID client_time_update_notify(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                           NX_SNTP_TIME *local time);

NX_SNTP_CLIENT demo_client;


status = nx_sntp_client_set_time_update_notify(&demo_client, 
                                            time_update_cb);

/* If status is NX_SUCCESS an SNTP Client 
   time update callback was successfully set.  */

```

## <a name="nx_sntp_client_stop"></a>nx_sntp_client_stop

Pare o fio do cliente SNTP

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_stop(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Descrição

Este serviço para a linha do Cliente SNTP. As tarefas de thread do Cliente SNTP, que funciona em loop infinito, fazem uma pausa em cada iteração para libertar o controlo do estado do Cliente SNTP e permitem que as aplicações façam chamadas API no Cliente SNTP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para bloco de controlo do cliente SNTP

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Com sucesso parou a linha do cliente

- **NX_SNTP_CLIENT_NOT_STARTED** (0xDB) linha de cliente SNTP não começou

- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```C
/* Stop the SNTP Client. */
status =  nx_sntp_client_stop(&demo_client);

/* If status is NX_SUCCESS an SNTP 
   Client instance was successfully stopped.  */

```

## <a name="nx_sntp_client_utility_display_date_time"></a>nx_sntp_client_utility_display_date_time

Converter uma linha de tempo NTP para data e tempo

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_utility_display_date_time (NX_SNTP_CLIENT 
                      *client_ptr, CHAR *buffer, UINT length);

```

### <a name="description"></a>Descrição

Este serviço converte o cliente SNTP local para um formato de data de um ano e devolve a data no tampão fornecido. O NX_SNTP_CURRENT_YEAR não precisa de ser o mesmo ano que o tempo atual do Cliente, mas deve ser definido.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **Ponteiro client_ptr para cliente SNTP**

- **tampão** Ponteiro para tampão para a data da loja

- **comprimento** Tamanho do tampão de entrada

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Conversão bem sucedida

- **NX_SNTP_ERROR_CONVERTING_DATETIME** (0xD08) não NX_SNTP_CURRENT_YEAR definido ou não estabelecido tempo de cliente local

- **NX_SNTP_INVALID_DATETIME_BUFFER** (0xD07) Comprimento do tampão insuficiente


### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```C
/* Convert and display the Client’s local time. */

status =  nx_sntp_client_utility_display_date_time(client_ptr , 
                                        buffer, sizeof(buffer));

/* If status is NX_SUCCESS, 
   date was successfully written to buffer.  */

```

## <a name="nx_sntp_client_utility_msecs_to_fraction"></a>nx_sntp_client_utility_msecs_to_fraction

Converter milissegundos para um componente de fração NTP

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_utility_msecs_to_fraction (ULONG milliseconds,   
                                                 ULONG *fraction);

```

### <a name="description"></a>Descrição

Este serviço converte os milissegundos de entrada para o componente da fração NTP. Destina-se a ser utilizado com aplicações que tenham um tempo base inicial para o Cliente SNTP, mas não em formato NTP segundos/fração. O número de milissegundos deve ser inferior a 1000 para fazer uma fração válida.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **milissegundos Milissegundos para converter**

- **fração** Ponteiro para milissegundos convertidos em fração

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Conversão bem sucedida

- **NX_SNTP_OVERFLOW_ERROR** (0xD32) Erro de conversão de tempo para uma data

- NX_SNTP_INVALID_TIME (0xD30) Entrada de dados inválidas da SNTP

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```C
/* Convert the milliseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(milliseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, 
   data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_usecs_to_fraction"></a>nx_sntp_client_utility_usecs_to_fraction

Converter microsegundos num componente de fração NTP

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_utility_usecs_to_fraction (ULONG microseconds,   
                                                 ULONG *fraction);

```
### <a name="description"></a>Descrição

Este serviço converte os microsegundos de entrada para o componente da fração NTP. Destina-se a ser utilizado com aplicações que tenham um tempo base inicial para o Cliente SNTP, mas não em formato NTP segundos/fração. O número de microsegundos deve ser inferior a 1000000 para fazer uma fração válida.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **microsegundos** Microsegundos para converter

- **fração** Ponteiro para microsegundos convertidos em fração

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Conversão bem sucedida

- **NX_SNTP_OVERFLOW_ERROR** (0xD32) Erro de conversão de tempo para uma data

- NX_SNTP_INVALID_TIME (0xD30) Entrada de dados inválidas da SNTP

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```C
/* Convert the microseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(microseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_fraction_to_usecs"></a>nx_sntp_client_utility_fraction_to_usecs

Converter um componente de fração NTP em microsegundos

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_utility_fraction_to_usecs (ULONG fraction,   
                                         ULONG *microseconds);

```

### <a name="description"></a>Descrição

Este serviço converte o componente de fração NTP de entrada em microsegundos.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **fração para converter**

- **microsegundos** Ponteiro para fração convertido em microsegundos

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Conversão bem sucedida

- NX_SNTP_INVALID_TIME (0xD30) Entrada de dados inválidas da SNTP

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```C
/* Convert the fraction to microseconds. */


status =  nx_sntp_client_utility_fraction_to_msecs(fraction, 
                                             &microseconds);

/* If status is NX_SUCCESS, data was successfully converted.  */
```