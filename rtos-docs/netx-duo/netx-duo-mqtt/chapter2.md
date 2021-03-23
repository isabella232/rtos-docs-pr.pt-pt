---
title: Capítulo 2 - Instalação e utilização do cliente Azure RTOS NetX Duo MQTT
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente NetX Duo MQTT Client.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cde19a0e84f369f1199ea4027fa09e6bd038e837
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825909"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-mqtt-client"></a>Capítulo 2 - Instalação e utilização do cliente Azure RTOS NetX Duo MQTT

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente cliente Azure RTOS NetX Duo MQTT.

## <a name="product-distribution"></a>Distribuição de Produtos

O Cliente MQTT para NetX Duo está disponível em [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . O pacote inclui dois ficheiros de origem, um incluindo ficheiro, e um ficheiro que contém este documento, da seguinte forma:

- **nxd_mqtt_client.h** Arquivo de cabeçalho para cliente MQTT para NetX Duo
- **nxd_mqtt_client.c** Arquivo C Fonte para Cliente MQTT para NetX Duo
- **nxd_mqtt_client.pdf** Descrição do Cliente MQTT para o NetX Duo
- **demo_mqtt_client.c** Demonstração de MQTT duo NetX

## <a name="mqtt-client-installation"></a>Instalação do cliente MQTT

Para utilizar o Cliente MQTT para o NetX Duo, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX Duo está instalado. Por exemplo, se o NetX Duo for instalado no diretório "*\threadx\arm7\green*" então o *nxd_mqtt_client.h* e *nxd_mqtt_client.c* para o NetX Duo MQTT Client precisam de ser copiados para este diretório.

## <a name="using-mqtt-client"></a>Utilização do Cliente MQTT

A utilização do Cliente MQTT para o NetX Duo é fácil. Basicamente, o código de aplicação deve incluir *nxd_mqtt_client.h* depois de incluir *tx_api.h* e *nx_api.h,* para utilizar o ThreadX e o NetX Duo, respectivamente. Uma vez incluídos os ficheiros de cabeçalho do Cliente MQTT, o código de aplicação pode então utilizar os serviços MQTT descritos mais tarde neste guia. O pedido também deve incluir *nxd_mqtt_client.c* no processo de construção. Estes ficheiros devem ser compilados da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação. Isto é tudo o que é necessário para usar o NetX Duo MQTT Client.

## <a name="using-mqtt-client-with-netx-secure-tls"></a>Utilização do Cliente MQTT com NetX Secure TLS

Para utilizar o cliente MQTT com módulo NetX Secure TLS, a aplicação deve ter o módulo NetX Secure TLS instalado, e incluir *nx_secure_tls_api.h* e *nx_crypto.h*. A biblioteca MQTT deve ser construída com o símbolo ***NX_SECURE_ENABLE*** definido.

## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração para a construção do cliente MQTT para o NetX Duo. Segue-se uma lista de todas as opções, onde cada uma é descrita em detalhe. Os valores predefinidos estão listados, mas podem ser redefinidos antes da inclusão do *nxd_mqtt_client.h.*

- **NX_DISABLE_ERROR_CHECKING**: Definida, esta opção remove a verificação básica de erros do cliente MQTT. É normalmente usado após a depurada aplicação.
- **NX_SECURE_ENABLE**: Definido, o Cliente MQTT é construído com suporte TLS.
A definição deste símbolo requer a instalação do módulo NetX Secure TLS.
*NX_SECURE_ENABLE* não é ativado por defeito.**
- **NXD_MQTT_REQUIRE_TLS**: Definida, a aplicação deve utilizar OTS para ligar ao corretor MQTT. Esta funcionalidade requer *NX_SECURE_ENABLE* definidos. Por padrão, este símbolo não está definido.
- **NXD_MQTT_MAX_TOPIC_NAME_LENGTH:** Depreciado.
- **NXD_MQTT_MAX_MESSAGE_LENGTH:** Depreciado.
- **NXD_MQTT_KEEPALIVE_TIMER_RATE**: Define a taxa de temporizador MQTT, em carraças temporais ThreadX. Este temporizador é usado para acompanhar o tempo desde que a última mensagem de controlo MQTT foi enviada, e envia uma mensagem MQTT PINGREQ antes que o tempo de vida expire. Este temporizador é ativado se o cliente ligar ao corretor com um conjunto de valor do temporizador vivo. O valor predefinido é TX_TIMER_TICKS_PER_SECOND, que é um temporizador de um segundo.
- **NXD_MQTT_PING_TIMEOUT_DELAY**: Define o tempo que o cliente MQTT espera pelo PINGRESP do corretor depois de enviar O PINGREQ MQTT. Se não for recebido PINGRESP após este atraso de tempo, o cliente trata o corretor como não-responsivo e desliga-se do corretor. O atraso de tempo de ping predefinido é TX_TIMER_TICKS_PER_SECOND, que é um segundo.
- **NXD_MQTT_SOCKET_TIMEOUT**: Define o tempo de desconexão da tomada TCP quando se desliga do servidor MQTT em carraças temporais. O valor predefinido é NX_WAIT_FOREVER.

## <a name="sample-mqtt-program"></a>Programa MQTT de amostra

O seguinte programa ilustra uma simples aplicação MQTT. Para simplificar, presume-se que os códigos de devolução são bem sucedidos, pelo que não é feita mais verificação de erros.

```c
#define LOCAL_SERVER_ADDRESS (IP_ADDRESS(192, 168, 1, 81))

/*******************************************************/
/* IOT MQTT Client Example                             */
/*******************************************************/
#define DEMO_STACK_SIZE 2048
#define CLIENT_ID_STRING "mytestclient"
#define MQTT_CLIENT_STACK_SIZE 4096
#define STRLEN(p) (sizeof(p) - 1)

/* Declare the MQTT thread stack space. */
static ULONG mqtt_client_stack[MQTT_CLIENT_STACK_SIZE / sizeof(ULONG)];

/* Declare the MQTT client control block. */
static NXD_MQTT_CLIENT mqtt_client;

/* Define the symbol for signaling a received message. */

/* Define the test threads. */

#define TOPIC_NAME "topic"

#define MESSAGE_STRING "This is a message. "

/* Define the priority of the MQTT internal thread. */
#define MQTT_THREAD_PRIORTY 2

/* Define the MQTT keep alive timer for 5 minutes */
#define MQTT_KEEP_ALIVE_TIMER 300
#define QOS0 0
#define QOS1 1

/* Declare event flag, which is used in this demo. */
TX_EVENT_FLAGS_GROUP mqtt_app_flag;
#define DEMO_MESSAGE_EVENT 1
#define DEMO_ALL_EVENTS 3

/* Declare buffers to hold message and topic. */
static UCHAR message_buffer[NXD_MQTT_MAX_MESSAGE_LENGTH];
static UCHAR topic_buffer[NXD_MQTT_MAX_TOPIC_NAME_LENGTH];

/* Declare the disconnect notify function. */
static VOID my_disconnect_func(NXD_MQTT_CLIENT *client_ptr)
{
    printf("client disconnected from server\n");
}

static VOID my_notify_func(NXD_MQTT_CLIENT* client_ptr, UINT number_of_messages)
{
    tx_event_flags_set(&mqtt_app_flag, DEMO_MESSAGE_EVENT, TX_OR);
    return;
}

static ULONG error_counter;
void demo_mqtt_client_local(NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr)
{
    UINT status;
    NXD_ADDRESS server_ip;
    ULONG events;
    UINT topic_length, message_length;

    /* Create MQTT client instance. */
    nxd_mqtt_client_create(&mqtt_client, "my_client",
        CLIENT_ID_STRING, STRLEN(CLIENT_ID_STRING), ip_ptr, pool_ptr,
        (VOID*)mqtt_client_stack, sizeof(mqtt_client_stack),
        MQTT_THREAD_PRIORTY, NX_NULL, 0);

    /* Register the disconnect notification function. */
    nxd_mqtt_client_disconnect_notify_set(&mqtt_client, my_disconnect_func);

    /* Create an event flag for this demo. */
    status = tx_event_flags_create(&mqtt_app_flag, "my app event");
    server_ip.nxd_ip_version = 4;
    server_ip.nxd_ip_address.v4 = LOCAL_SERVER_ADDRESS;

    /* Start the connection to the server. */
    nxd_mqtt_client_connect(&mqtt_client, &server_ip, NXD_MQTT_PORT, 
        MQTT_KEEP_ALIVE_TIMER, 0, NX_WAIT_FOREVER);

    /* Subscribe to the topic with QoS level 0. */
    nxd_mqtt_client_subscribe(&mqtt_client, TOPIC_NAME, STRLEN(TOPIC_NAME),
        QOS0);

    /* Set the receive notify function. */
    nxd_mqtt_client_receive_notify_set(&mqtt_client, my_notify_func);

    /* Publish a message with QoS Level 1. */
    nxd_mqtt_client_publish(&mqtt_client, TOPIC_NAME,
        STRLEN(TOPIC_NAME), (CHAR*)MESSAGE_STRING, 
        STRLEN(MESSAGE_STRING), 0, QOS1, NX_WAIT_FOREVER);

    /* Now wait for the broker to publish the message. */
    tx_event_flags_get(&mqtt_app_flag, DEMO_ALL_EVENTS,
        TX_OR_CLEAR, &events, TX_WAIT_FOREVER);

    if(events & DEMO_MESSAGE_EVENT)
    {
        nxd_mqtt_client_message_get(&mqtt_client, topic_buffer,
            sizeof(topic_buffer), &topic_length, message_buffer,
            sizeof(message_buffer), &message_length);

        topic_buffer[topic_length] = 0;

        message_buffer[message_length] = 0;

        printf("topic = %s, message = %s\n", topic_buffer, message_buffer);
    }

    /* Now unsubscribe the topic. */
    nxd_mqtt_client_unsubscribe(&mqtt_client, TOPIC_NAME,
        STRLEN(TOPIC_NAME));

    /* Disconnect from the broker. */
    nxd_mqtt_client_disconnect(&mqtt_client);

    /* Delete the client instance, release all the resources. */
    nxd_mqtt_client_delete(&mqtt_client);
    return;
}
```
