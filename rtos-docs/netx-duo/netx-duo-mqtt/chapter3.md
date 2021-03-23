---
title: Capítulo 3 - Descrição dos Serviços de Clientes Azure RTOS NetX Duo MQTT
description: Este capítulo contém uma descrição de todos os serviços do Cliente NetX Duo MQTT (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9cbb65946c45bfbc476091f7c604346e839a42fc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825897"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-mqtt-client-services"></a>Capítulo 3 - Descrição dos serviços de clientes Azure RTOS NetX Duo MQTT

Este capítulo contém uma descrição de todos os serviços de clientes Azure RTOS NetX Duo MQTT (listados abaixo) por ordem alfabética.

Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

- **nxd_mqtt_client_create Criar** *caso de cliente MQTT*
- **nxd_mqtt_client_will_message_set** *Definir a mensagem de testamento*
- **nxd_mqtt_client_client_login_set** *Definir nome de utilizador e palavra-passe do cliente MQTT*
- **nxd_mqtt_client_connect** *Ligue o Cliente MQTT ao corretor*
- **nxd_mqtt_client_secure_connect** *Ligue o cliente MQTT ao corretor com segurança TLS*
- **nxd_mqtt_client_publish** *publicar uma mensagem através do corretor.*
- **nxd_mqtt_client_subscribe** *Subscreva um tópico*
- **nxd_mqtt_client_unsubscribe** *Desubscreva-se de um tópico*
- **nxd_mqtt_client_receive_notify_set** *Definir mensagem MQTT receber notificar função de retorno*
- **nxd_mqtt_client_message_get** *Recuperar uma mensagem do corretor*
- nxd_mqtt_client_disconnect_notify_set *Definir desconexão de mensagens MQTT notificam a função de retorno* 
- **nxd_mqtt_client_disconnect** *Desligue o cliente MQTT do corretor*
- **nxd_mqtt_client_delete** *Eliminar a instância do cliente MQTT*

## <a name="nxd_mqtt_client_create"></a>nxd_mqtt_client_create

Criar caso de cliente MQTT

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_create(NXD_MQTT_CLIENT *client_ptr,
    CHAR *client_name, CHAR *client_id,
    UINT client_id_length, NX_IP *ip_ptr, NX_PACKET_POOL
    *pool_ptr, VOID *stack_ptr, ULONG stack_size, UINT
    mqtt_thread_priority,
    VOID *memory_ptr, ULONG memory_size);
```

### <a name="description"></a>Descrição

Este serviço cria uma instância do Cliente MQTT na instância IP especificada. A cadeia *client_id* é transmitida para o servidor durante a fase de ligação MQTT como o Identificador de *Cliente (ClientId)*. Também cria os recursos necessários da ThreadX (linha de tarefa do Cliente MQTT, mutex, grupo de bandeira de evento e tomada TCP).

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.
- **client_name** Cadeia de nome de cliente.
- **client_id** Cadeia de identificação do cliente utilizada durante a fase de ligação. O corretor MQTT utiliza este client_id para identificar exclusivamente um cliente.
- **client_id_length** Comprimento da cadeia de identificação do cliente, em bytes.
- **ip_ptr** Ponteiro para a instância IP.
- **pool_ptr** Ponteiro para uma piscina de pacotes que o cliente MQTT usa para o seu funcionamento.
- **stack_ptr** Área de pilha para o fio do cliente MQTT.
- **stack_size** Tamanho da área da pilha, em bytes.
- **mqtt_thread_priority** A prioridade da Linha MQTT.
- **memory_ptr** Precotado. Já não é usado.
- **memory_size** Precotado. Já não é usado.

### <a name="return-values"></a>Valores de devolução

- **NXD_MQTT_SUCCESS** (0x00) criou com sucesso o cliente MQTT.
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Erro lógico interno
- NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido, ip_ptr ou ponteiro da piscina de pacotes.
- NXD_MQTT_INVALID_PARAMETER (0x10009) Inválido irá tópicos de cadeia, will_retrain_flag ou valor will_QoS.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
#define CLIENT_ID_STRING "My Test Client"

#define MQTT_THREAD_PRIORITY 2

NXD_MQTT_CLIENT my_client;
NX_IP ip_0; /* Assume ip_0 is created prior to MQTT client creation. */
NX_PACKET_POOL pool_0;/* Assume pool_0 is created prior to MQTT client creation. */
UCHAR mqtt_thread_stack[STACK_SIZE];

/* Create the MQTT Client instance on "ip_0". */
status = **nxd_mqtt_client_create**(&my_client, "my client",
    CLIENT_ID_STRING, stlren(CLIENT_ID_STRING),
    &ip_0, &pool_0, (VOID*)mqtt_thread_stack, STACK_SIZE,
    MQTT_THREAD_PRIORITY, NX_NULL, 0);

/* If status is NXD_MQTT_SUCCESS an MQTT Client instance was successfully created. */
```

## <a name="nxd_mqtt_client_will_message_set"></a>nxd_mqtt_client_will_message_set

Define a mensagem 'Testamento'

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_will_message_set(NXD_MQTT_CLIENT
    *client_ptr,
    Const UCHAR *will_topic,
    UINT will_topic_length
    Const UCHAR *will_message,
    UINT will_message_length,
    UINT will_retain_flag,
    UINT will_QoS);
```

### <a name="description"></a>Descrição

Este serviço define o tópico de testamento opcional e enviará mensagem antes que o cliente se conecte ao servidor. O tópico deve ser a cadeia codificada UTF-8.

A mensagem do testamento, se definida, é transmitida ao corretor como parte da mensagem CONNECT. Por isso, a aplicação que deseje utilizar a mensagem deve utilizar este serviço antes da ligação MQTT ser esclareça.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.
- **will_topic** UTF-8 codificado irá tópico cadeia. O tópico deve estar presente. O chamador deve manter a will_topic corda válida até que a *chamada nx_mqtt_client_connect* seja feita.
- **will_topic_length** Número de bytes na cadeia de tópicos de vontade
- **will_message** Aplicação definida irá enviar mensagem. Se a mensagem de testamento não for necessária, a aplicação pode definir este campo para *NX_NULL.*
- **will_message_length** Número de bytes na cadeia de mensagens de testamento. Se will_message estiver definido para NU, will_message_length deve ser definido para 0.
- **will_retain_flag** Se o servidor publica a mensagem do testamento como uma mensagem retida. Os valores válidos são *NX_TRUE* ou *NX_FALSE.*
- **will_QoS** Valor QoS utilizado pelo servidor ao enviar mensagem de mensagem. Os valores válidos são 0 ou 1.  

### <a name="return-values"></a>Valores de devolução

- **NXD_MQTT_SUCCESS** (0x00) define com sucesso a mensagem de testamento.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) as mensagens QoS de nível 2 não são suportadas.
- NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido.
- NXD_MQTT_INVALID_PARAMETER (0x10009) Inválido irá tópicos de cadeia, will_retrain_flag ou valor will_QoS.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
#define WILL_TOPIC "my_will_topic"

#define WILL_MESSAGE "my will message"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_will_message_set(&my_client,
    WILL_TOPIC, STRLEN(WILL_TOPIC),
    WILL_MESSAGE, STRLEN(WILL_MESSAGE),
    NX_TRUE, 0);

/* If status is NXD_MQTT_SUCCESS the will message is properly
configured for the session. It will be transmitted to the server
during MQTT connection. */
```

## <a name="nxd_mqtt_client_login_set"></a>nxd_mqtt_client_login_set

Define o nome de utilizador e a palavra-passe do cliente MQTT

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_login_set(NXD_MQTT_CLIENT *client_ptr,
    Const UCHAR *username,
    UINT username_length
    Const UCHAR *password,
    UINT password_length);
```

### <a name="description"></a>Descrição

Este serviço define o nome de utilizador e a palavra-passe, que é utilizado durante a fase de ligação MQTT para iniciar sessão com efeitos de autenticação.

O login do cliente MQTT com nome de utilizador e senha é opcional. Nas situações em que o servidor necessita de um nome de utilizador e palavra-passe, o nome de utilizador e a palavra-passe devem ser definidos antes da ligação ser estabelecida.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.
- **nome de utilizador** Cadeia de nome de utilizador codificada UTF-8. O chamador deve manter o nome de utilizador válido até que a *chamada nx_mqtt_client_connect* seja feita.
- **username_length** Número de bytes na cadeia de nome de utilizador
- **senha** Corda de senha. Se a palavra-passe não for necessária, este campo pode ser definido para NX_NULL.

### <a name="return-values"></a>Valores de devolução

- **NXD_MQTT_SUCCESS** (0x00) define com sucesso a mensagem de testamento.
- NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido.
- NXD_MQTT_INVALID_PARAMETER (0x10009) Cadeia de nome de utilizador inválida ou a cadeia de senha.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
#define USERNAME "MY_NAME"

#define PASSWORD "MY_LOGIN_SECRET"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_login_set(&my_client,
    USERNAME, STRLEN(USERNAME),
    PASSWORD, STRLEN(PASSWORD));

/* If status is NXD_MQTT_SUCCESS the username and the password 
are set for the session. This information will be 
transmitted to the server during MQTT connection. */
```

## <a name="nxd_mqtt_client_connect"></a>nxd_mqtt_client_connect

Ligue o Cliente MQTT ao corretor

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_connect(NXD_MQTT_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT keepalive, UINT clean_session, ULONG wait_option));
```

### <a name="description"></a>Descrição

Este serviço inicia uma ligação com o corretor. Primeiro liga uma tomada TCP e depois faz uma ligação TCP. Assumindo que é bem sucedido, cria um temporizador se a funcionalidade MQTT manter viva estiver ativada. Em seguida, conecta-se com o servidor MQTT (corretor).

Note que este serviço cria uma ligação MQTT sem proteção TLS. Para criar uma ligação MQTT segura, o pedido utilizará o ***serviço nxd_mqtt_client_secure_connect().***

Após a ligação, se o cliente definir o *clean_session* para NX_FALSE, o cliente retransmite quaisquer mensagens armazenadas que ainda não tenham sido reconhecidas.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.
- **server_ip** Endereço IP corretor.
- **server_port** Número da porta do corretor. A porta predefinida para MQTT é definida como **_NXD_MQTT_PORT_** (1883).
- **keep_alive** O valor "manter vivo", em segundos, deve ser utilizado durante a sessão. O valor indica o tempo máximo entre duas mensagens de controlo MQTT enviadas ao corretor antes que o corretor o registe este cliente. O valor 0 desliga a funcionalidade de manter-se viva.
- **clean_session** Se o servidor deve iniciar esta sessão limpa. As opções válidas são **_NX_TRUE_*_ ou _*_NX_FALSE._**
- **wait_option** Tempo de espera de ligação.

### <a name="return-values"></a>Valores de devolução

- **NXD_MQTT_SUCCESS** (0x00) Ligação MQTT bem sucedida
- **NXD_MQTT_ALREADY_CONNECTED** (0x10001) O cliente já está ligado ao corretor.
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) Não conseguiu obter o mutex MQTT 
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Erro lógico interno
- **NXD_MQTT_CONNECT_FAILURE** (0x10005) não conseguiu ligar-se ao corretor.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Incapaz de enviar mensagens ao corretor.
- **NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) Servidor respondeu com erro
- **NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Código de resposta do servidor
- **NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Código de resposta do servidor
- **NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Código de resposta do servidor
- **NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Código de resposta do servidor
- **NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Código de resposta do servidor
- NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido, ip_ptr ou ponteiro de piscina de pacotes

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_connect(&my_client, &broker_address,
    NXD_MQTT_PORT,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session flag set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS a connection to the broker is successfully established. */
```

## <a name="nxd_mqtt_client_secure_connect"></a>nxd_mqtt_client_secure_connect

Ligue o cliente MQTT ao corretor com a segurança TLS

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_secure_connect(NXD_MQTT_CLIENT
    *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NXD_MQTT_CLIENT *,
        NX_SECURE_TLS_SESISON *,
        NX_SECURE_TLS_CERTIFICATE *,
        NX_SECURE_TLS_CERTIFICATE *),
    UINT keepalive, UINT connection_flag,
    UINT clean_session, ULONG wait_option));
```

### <a name="description"></a>Descrição

Este serviço é idêntico ao ***nxd_mqtt_client_connect*** exceto que a ligação passa pela camada TLS em vez de TCP. Portanto, a comunicação entre o cliente e o corretor está assegurada.

O *tls_setup* definido pelo utilizador é uma função de retorno que o cliente MQTT utiliza antes de fazer uma ligação ao cliente MQTT. O pedido deve rubricar o NetX Secure TLS, configurar parâmetros de segurança e carregar certificados relevantes para serem utilizados durante o aperto de mão TLS. O aperto de mão TLS real ocorre após a criação de uma ligação TCP na porta MQTT TLS do corretor (porta TCP padrão 8883). Uma vez que o aperto de mão TLS seja bem sucedido, o pacote de controlo MQTT CONNECT é enviado via TLS.

Para estabelecer ligações seguras, a biblioteca NetX Secure TLS deve estar disponível e o cliente MQTT NetX Duo deve ser construído com ***NX_SECURE_ENABLE*** definido.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.
- **server_ip** Endereço IP corretor.
- **server_port** Número da porta do corretor. A porta predefinida para MQTT é indefinida como **_NXD_MQTT_TLS_PORT_** (8883).
- **tls_setup** Função de retorno de configuração TLS fornecida pelo utilizador. Esta função de retorno é invocada para configurar parâmetros de ligação ao cliente TLS.
- **keep_alive** O valor de manter vivo a ser usado durante a sessão. O valor 0 desliga a funcionalidade de manter-se viva.
- **clean_session** Se o servidor deve ou não iniciar esta sessão limpa. As opções válidas são **_NX_TRUE_*_ ou _*_NX_FALSE._**
- **wait_option** Tempo de espera de ligação.

### <a name="return-values"></a>Valores de devolução

- **NXD_MQTT_SUCCESS** (0x00) Conexão de cliente MQTT bem sucedida estabelecida via TLS.
- **NXD_MQTT_ALREADY_CONNECTED** (0x10001) O cliente já está ligado ao corretor.
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) Não conseguiu obter o mutex MQTT 
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Erro lógico interno
- **NXD_MQTT_CONNECT_FAILURE** (0x10005) não conseguiu ligar-se ao corretor.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Incapaz de enviar mensagens ao corretor.
- **NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) O servidor respondeu com mensagem de erro.
- **NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Código de resposta do servidor
- **NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Código de resposta do servidor
- **NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Código de resposta do servidor
- **NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Código de resposta do servidor
- **NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Código de resposta do servidor
- NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido ou estrutura de endereço de corte.
- NX_INVALID_PORT (0x46) A porta do servidor não pode ser 0.
- NXD_MQTT_INVALID_PARAMETER (0x10009) Erro do parâmetro de entrada
- NXD_MQTT_CLIENT_NOT_RUNNING (0x1000E) MQTT Thread ainda não começou a funcionar.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* TLS setup routine. This function is responsible for setting up TLS parameters.*/
UINT tls_setup_callback(NXD_MQTT_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certificate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_certificate,
    UINT timeout)
{
/* Note this routine is simplified to highlight the
necessary steps to setup a TLS session. Each
application may employ different procedures suitable for
its TLS settings, such as cipher suite, certificates. */

/* Create a TLS session for the MQTT connection, and pass
in various crypto methods this session can use for the
initial TLS handshake. */

/* Load appropriate certificates, or set up session key for Pre-share key operation. */

/* Start the TLS session */

/* Return NX_SUCCESS if the TLS session is established. */
    return(NX_SUCCESS);
}

NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_secure_connect(&my_client,
    &server_address, NXD_MQTT_TLS_PORT, tls_setup_callback,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the MQTT Client was successfully connected to the broker via TLS. */
```

## <a name="nxd_mqtt_client_publish"></a>nxd_mqtt_client_publish

Publique uma mensagem através do corretor

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_publish(NXD_MQTT_CLIENT *client_ptr,
    CHAR *topic_name, UINT topic_name_length, CHAR *message, UINT
    message_length,
    UINT retain, UINT QoS, ULONG timeout);
```

### <a name="description"></a>Descrição

Este serviço publica uma mensagem através do corretor. A publicação de mensagens QoS de nível 2 ainda não é suportada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.
- **topic_name** Tópico para publicar.
- **topic_name_length** Comprimento do tópico, em bytes.
- **mensagem** Ponteiro para o tampão de mensagem.
- **message_length** Tamanho da mensagem, em bytes
- **reter** Determina se o corretor deve reter a mensagem.
- **QoS** O valor QoS desejado: 0 ou 1.
- **tempo limite** Valor de tempo limite

### <a name="return-values"></a>Valores de devolução

- **NXD_MQTT_SUCCESS** (0x00) Cliente MQTT bem sucedido criar
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Erro lógico interno.
- **NXD_MQTT_PACKET_POOL_FAILURE** (0x10006) Não conseguiu obter o pacote da piscina de pacotes.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) não comunicaram com o corretor.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) as mensagens QoS de nível 2 não são suportadas.
- NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido, ip_ptr ou ponteiro de piscina de pacotes
- NXD_MQTT_INVALID_PARAMETER (0x10009) Erro do parâmetro de entrada

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
CHAR *topic = "temperature";
CHAR *message = "100";

/* Publish the temperature value. */
status = nxd_mqtt_client_publish(&my_client,
    topic, STRLEN(topic),
    message, STRLEN(message),
    NX_TRUE, /* Server retains message. */);
    0, /* QOS */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the message has been 
successfully sent to the broker. */
```

## <a name="nxd_mqtt_client_subscribe"></a>nxd_mqtt_client_subscribe

Subscrever um tópico

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_subscribe(NXD_MQTT_CLIENT
    *mqtt_client_ptr, CHAR *topic_name,
    UINT topic_name_length, UINT QoS);
```

### <a name="description"></a>Descrição

Este serviço subscreve um tópico específico. A subscrição de mensagens QoS de nível 2 ainda não está suportada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.
- **topic_name** Tópico para publicar.
- **topic_name_length** Comprimento do tópico, em bytes.
- **QoS O nível QoS desejado:** 0 ou 1.

### <a name="return-values"></a>Valores de devolução

- **NXD_MQTT_SUCCESS** (0x00) subscreveu com sucesso o tema.
- **NXD_MQTT_NOT_CONNECTED** (0x10002) O cliente não está ligado ao corretor.
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) Não conseguiu obter o mutex MQTT
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Erro lógico interno
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Incapaz de enviar mensagens ao corretor.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS nível 2messages não são suportados.
- NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido, ip_ptr ou ponteiro de piscina de pacotes
- NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name não está definido, ou topic_name_length é zero, ou QoS é valor é inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_subscribe(&my_client, topic,
    STRLEN(topic), 0);

/* If status is NXD_MQTT_SUCCESS, the client successfully
subscribes to the topic "temperate". At this point the client
is ready for receiving messages from the broker. */
```

## <a name="nxd_mqtt_client_unsubscribe"></a>nxd_mqtt_client_unsubscribe

Cancelar a subscrição de um tópico

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_unsubscribe(NXD_MQTT_CLIENT
    *mqtt_client_pr,
    CHAR *topic_name,
    UINT topic_name_length);
```

### <a name="description"></a>Descrição

Este serviço não se subscreve de um tópico.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.
- **topic_name** Tópico para cancelar a subscrição de.
- **topic_name_length** Comprimento do tópico, em bytes.

### <a name="return-values"></a>Valores de devolução

- **NXD_MQTT_SUCCESS** (0x00) Com sucesso não subscrito do tópico.
- **NXD_MQTT_NOT_CONNECTED** (0x10002) O cliente não está ligado ao corretor.
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) Não conseguiu obter o mutex MQTT.
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Erro lógico interno
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Incapaz de enviar mensagens ao corretor.
- NX_PTR_ERROR (0x07) Ponteiro do bloco de controlo MQTT inválido
- NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name não está definido, ou topic_name_length é zero.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_unsubscribe(&my_client, topic,
    STRLEN(topic));

/* If status is NXD_MQTT_SUCCESS, the client successfully
unsubscribes the topic "temperate". */
```

## <a name="nxd_mqtt_client_receive_notify_set"></a>nxd_mqtt_client_receive_notify_set

Definir mensagem MQTT receber notificar função de retorno

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_receive_notify_set(NXD_MQTT_CLIENT
    *client_ptr,
    VOID(*receive_notify)(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count));
```

### <a name="description"></a>Descrição

Este serviço regista uma função de retorno com o cliente MQTT. Ao receber uma mensagem publicada pelo corretor, o cliente MQTT armazena a mensagem na fila de receção. Se a função de retorno estiver definida, a função de retorno é invocada para notificar a aplicação de que uma mensagem está pronta para ser recuperada. A função de notificação de receção leva um ponteiro para o bloco de controlo do cliente MQTT, e uma *message_count* indicando o número de mensagens disponíveis na fila de receção. Note que o número pode alterar-se entre a notificação recebida e quando a aplicação recupera estas mensagens, uma vez que novas mensagens podem ter chegado no intervalo.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.
- **receive_notify** A função de retorno fornecida pelo utilizador deve ser invocada ao receber uma mensagem.

### <a name="return-values"></a>Valores de devolução

- **NXD_MQTT_SUCCESS** (0x00) definir com sucesso a função de notificação de receção.
- NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Sample MQTT receive notify function. */

VOID my_notify_func(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count)
{

/* On receiving a message, set an event flag to wake up the
application thread. The message will be received and
processed in the application thread. */
tx_event_flags_set(&mqtt_app_flag,
    MESSAGE_RECEIVED_EVENT, TX_OR);

/* All done. Return to the caller. */
    return;
}

/* Set the receive callback function. */
status = **nxd_mqtt_client_receive_notify_set**(&my_client,
    my_notify_func);

/* If status is NXD_MQTT_SUCCESS the notify function is properly set. */
```

## <a name="nxd_mqtt_client_message_get"></a>nxd_mqtt_client_message_get

Recupere uma mensagem do corretor

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_message_get(NXD_MQTT_CLIENT
    *client_ptr,
    UCHAR *topic_buffer, UINT topic_buffer_size,
    UINT *actual_topic_length, UCHAR *message_buffer,
    UINT message_buffer_size, UINT *actual_message_length);
```

### <a name="description"></a>Descrição

Este serviço recupera uma mensagem publicada pelo corretor. Todas as mensagens recebidas são armazenadas na fila de receção. A aplicação utiliza este serviço para recuperar estas mensagens. Esta chamada não está a bloquear. Se a fila de receção estiver vazia, este serviço retorna ***NXD_MQTT_NO_MESSAGE** _. Uma aplicação que deseje ser notificada da mensagem recebida pode ligar para o serviço _ *_nxd_mqtt_client_receive_notify_set_** para registar uma função de retorno de receção.

O chamador precisa fornecer espaço de memória para a cadeia de tópicos e o corpo da mensagem. Os tamanhos destes dois tampão são passados usando *topic_buffer_size* e *message_buffer_size*. O número real de bytes na cadeia de tópicos e o corpo da mensagem são devolvidos em *atual_topic_length* e *atual_message_length*. Se o comprimento do tópico ou o comprimento da massagem for maior do que o espaço do tampão fornecido, este serviço devolve o código de erro *NXD_MQTT_INSUFFICIENT_BUFFER_SIZE*.

O pedido atribuirá um amortecedor maior e tentará novamente.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.
- **topic_buffer** Ponteiro para o local da memória onde a cadeia de tópicos é copiada.
- **topic_buffer_size** Tamanho do tampão tópico.
- **atual_topic_length** Ponteiro para o local da memória onde o comprimento do tópico real é devolvido.
- **message_buffer** Ponteiro para o local da memória onde a cadeia de mensagens é copiada.
- **message_buffer_size** Tamanho do tampão de mensagem.
- **atual_message_length** Ponteiro para o local da memória onde o comprimento da mensagem é devolvido.

### <a name="return-values"></a>Valores de devolução

- **NXD_MQTT_SUCCESS** (0x00) mensagem recuperada com sucesso.
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Erro lógico interno
- **NXD_MQTT_NO_MESSAGE** (0x1000A) A fila de receção está vazia.
- **NXD_MQTT_INSUFFICIENT_BUFFER_SIZE** (0x1000D) Tampão de tópico ou tampão de mensagem é demasiado pequeno para o tópico ou para a mensagem.
- NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido, ip_ptr ou ponteiro de piscina de pacotes
- NXD_MQTT_INVALID_PARAMETER (0x10009) message_buffer ou ponteiro topic_buffer é NULO

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
UCHAR topic[MAX_TOPIC_SIZE];
UCHAR message[MAX_TOPIC_SIZE];
UINT topic_length;
UINT message_length;

/* Retrieve a message from MQTT client receive queue. */
status = nxd_mqtt_client_message_get(&my_client, topic,
    sizeof(topic), &topic_length, message, sizeof(message),
    &message_length);

/* Check the return value. */
if(status == NXD_MQTT_SUCCESS)
{
/* A message is received. All done. */
}
else if (status == NXD_MQTT_NO_MESSAGE)
{
/* No more messages in the receive queue. All done. */
}
else
{
/* Receive error. */
}
```

## <a name="nxd_mqtt_client_disconnect_notify_set"></a>nxd_mqtt_client_disconnect_notify_set

Definir desconexão de mensagens MQTT notificar função de retorno

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_disconnect_notify_set(
    NXD_MQTT_CLIENT *client_ptr,
    VOID(*disconnect_notify)(NXD_MQTT_CLIENT* client_ptr));
```

### <a name="description"></a>Descrição

Este serviço regista uma função de retorno com o cliente MQTT. Quando o MQTT deteta a ligação ao corretor, chama esta função de notificação para alertar a aplicação. Portanto, a aplicação pode usar esta função de retorno para detetar uma ligação perdida, e para ser capaz de restabelecer a ligação com o corretor.

```c
VOID callback_func(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.
- **disconnect_notify** A função de retorno fornecida pelo utilizador deve ser invocada quando a MQTT detetar a ligação ao corretor se perder.

### <a name="return-values"></a>Valores de devolução

- **NXD_MQTT_SUCCESS** (0x00) definir com sucesso a função de notificação de desconexão.
- NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
VOID disconnect_notify(NXD_MQTT_CLIENT *client_ptr)
{
/* MQTT client is disconnected from the broker. Notify the application so it can re-connect to the broker. */
}

status = nxd_mqtt_client_disconnect_notify_set(client_ptr,
    disconnect_notify);
```

## <a name="nxd_mqtt_client_disconnect"></a>nxd_mqtt_client_disconnect

Desconecte o cliente MQTT do corretor

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_disconnect(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a>Descrição

Este serviço desliga o cliente do corretor. Note que as mensagens na fila de receção são libertadas. As mensagens com QoS 1 na fila de transmissão não são divulgadas. Após a reconectação do cliente ao servidor, as mensagens QoS 1 podem ser processadas, a menos que o cliente se conecte ao servidor com *clean_session* bandeira definida para ***NX_TRUE***.

Se a ligação tiver sido feita com proteção de segurança TLS, este serviço fechará a sessão TLS antes de desligar a ligação TCP.

A chamada de desconexão da tomada TCP tem uma opção de espera definida por NXD_MQTT_SOCKET_TIMEOUT (carraças do temporizador). O valor predefinido é NX_WAIT_FOREVER. Para evitar uma suspensão indefinida no caso de a ligação de rede se perder ou o servidor não responder, defina esta opção para um valor finito.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.

### <a name="return-values"></a>Valores de devolução

- **NXD_MQTT_SUCCESS** (0x00) desligado com sucesso do corretor
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) Não conseguiu obter o mutex MQTT.
- NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Disconnect from the broker. */
status = nxd_mqtt_client_disconnect(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
disconnected from the broker. */
```

## <a name="nxd_mqtt_client_delete"></a>nxd_mqtt_client_delete

Eliminar a instância do cliente MQTT

### <a name="prototype"></a>Prototype

```c
UINT nxd_mqtt_client_delete(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a>Descrição

Este serviço elimina a instância do cliente MQTT e liberta recursos internos. Este serviço desliga automaticamente o cliente do corretor se ainda estiver ligado. As mensagens ainda não transmitidas ou não foram reconhecidas são libertadas. As mensagens recebidas mas não recuperadas pela aplicação também são divulgadas.

Se a ligação foi feita com proteção de segurança TLS, este serviço fecha a sessão TLS antes de desligar a ligação TCP.

Após a execlarção do cliente, uma aplicação que deseje utilizar o serviço MQTT precisa de criar uma nova instância.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.

### <a name="return-values"></a>Valores de devolução

- **NXD_MQTT_SUCCESS** (0x00) eliminou com sucesso o cliente MQTT.
- NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Delete the MQTT client instance. */
status = nxd_mqtt_client_delete(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
deleted from the system. */
```
