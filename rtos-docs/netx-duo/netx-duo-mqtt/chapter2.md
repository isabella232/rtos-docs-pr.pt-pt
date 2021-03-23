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
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-mqtt-client"></a><span data-ttu-id="aba35-103">Capítulo 2 - Instalação e utilização do cliente Azure RTOS NetX Duo MQTT</span><span class="sxs-lookup"><span data-stu-id="aba35-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo MQTT client</span></span>

<span data-ttu-id="aba35-104">Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente cliente Azure RTOS NetX Duo MQTT.</span><span class="sxs-lookup"><span data-stu-id="aba35-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo MQTT client component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="aba35-105">Distribuição de Produtos</span><span class="sxs-lookup"><span data-stu-id="aba35-105">Product Distribution</span></span>

<span data-ttu-id="aba35-106">O Cliente MQTT para NetX Duo está disponível em [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) .</span><span class="sxs-lookup"><span data-stu-id="aba35-106">MQTT Client for NetX Duo is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="aba35-107">O pacote inclui dois ficheiros de origem, um incluindo ficheiro, e um ficheiro que contém este documento, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="aba35-107">The package includes two source files, one include file, and a file that contains this document, as follows:</span></span>

- <span data-ttu-id="aba35-108">**nxd_mqtt_client.h** Arquivo de cabeçalho para cliente MQTT para NetX Duo</span><span class="sxs-lookup"><span data-stu-id="aba35-108">**nxd_mqtt_client.h** Header file for MQTT Client for NetX Duo</span></span>
- <span data-ttu-id="aba35-109">**nxd_mqtt_client.c** Arquivo C Fonte para Cliente MQTT para NetX Duo</span><span class="sxs-lookup"><span data-stu-id="aba35-109">**nxd_mqtt_client.c** C Source file for MQTT Client for NetX Duo</span></span>
- <span data-ttu-id="aba35-110">**nxd_mqtt_client.pdf** Descrição do Cliente MQTT para o NetX Duo</span><span class="sxs-lookup"><span data-stu-id="aba35-110">**nxd_mqtt_client.pdf** Description of MQTT Client for NetX Duo</span></span>
- <span data-ttu-id="aba35-111">**demo_mqtt_client.c** Demonstração de MQTT duo NetX</span><span class="sxs-lookup"><span data-stu-id="aba35-111">**demo_mqtt_client.c** NetX Duo MQTT demonstration</span></span>

## <a name="mqtt-client-installation"></a><span data-ttu-id="aba35-112">Instalação do cliente MQTT</span><span class="sxs-lookup"><span data-stu-id="aba35-112">MQTT Client Installation</span></span>

<span data-ttu-id="aba35-113">Para utilizar o Cliente MQTT para o NetX Duo, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX Duo está instalado.</span><span class="sxs-lookup"><span data-stu-id="aba35-113">In order to use MQTT Client for NetX Duo, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="aba35-114">Por exemplo, se o NetX Duo for instalado no diretório "*\threadx\arm7\green*" então o *nxd_mqtt_client.h* e *nxd_mqtt_client.c* para o NetX Duo MQTT Client precisam de ser copiados para este diretório.</span><span class="sxs-lookup"><span data-stu-id="aba35-114">For example, if NetX Duo is installed in the directory "*\threadx\arm7\green*" then the *nxd_mqtt_client.h* and *nxd_mqtt_client.c* for NetX Duo MQTT Client need to be copied into this directory.</span></span>

## <a name="using-mqtt-client"></a><span data-ttu-id="aba35-115">Utilização do Cliente MQTT</span><span class="sxs-lookup"><span data-stu-id="aba35-115">Using MQTT Client</span></span>

<span data-ttu-id="aba35-116">A utilização do Cliente MQTT para o NetX Duo é fácil.</span><span class="sxs-lookup"><span data-stu-id="aba35-116">Using MQTT Client for NetX Duo is easy.</span></span> <span data-ttu-id="aba35-117">Basicamente, o código de aplicação deve incluir *nxd_mqtt_client.h* depois de incluir *tx_api.h* e *nx_api.h,* para utilizar o ThreadX e o NetX Duo, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="aba35-117">Basically, the application code must include *nxd_mqtt_client.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX, and NetX Duo, respectively.</span></span> <span data-ttu-id="aba35-118">Uma vez incluídos os ficheiros de cabeçalho do Cliente MQTT, o código de aplicação pode então utilizar os serviços MQTT descritos mais tarde neste guia.</span><span class="sxs-lookup"><span data-stu-id="aba35-118">Once the MQTT Client header files are included, the application code is then able to use the MQTT services described later in this guide.</span></span> <span data-ttu-id="aba35-119">O pedido também deve incluir *nxd_mqtt_client.c* no processo de construção.</span><span class="sxs-lookup"><span data-stu-id="aba35-119">The application must also include *nxd_mqtt_client.c* in the build process.</span></span> <span data-ttu-id="aba35-120">Estes ficheiros devem ser compilados da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação.</span><span class="sxs-lookup"><span data-stu-id="aba35-120">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="aba35-121">Isto é tudo o que é necessário para usar o NetX Duo MQTT Client.</span><span class="sxs-lookup"><span data-stu-id="aba35-121">This is all that is required to use NetX Duo MQTT Client.</span></span>

## <a name="using-mqtt-client-with-netx-secure-tls"></a><span data-ttu-id="aba35-122">Utilização do Cliente MQTT com NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="aba35-122">Using MQTT Client with NetX Secure TLS</span></span>

<span data-ttu-id="aba35-123">Para utilizar o cliente MQTT com módulo NetX Secure TLS, a aplicação deve ter o módulo NetX Secure TLS instalado, e incluir *nx_secure_tls_api.h* e *nx_crypto.h*.</span><span class="sxs-lookup"><span data-stu-id="aba35-123">To use MQTT client with NetX Secure TLS module, application must have NetX Secure TLS module installed, and include *nx_secure_tls_api.h* and *nx_crypto.h*.</span></span> <span data-ttu-id="aba35-124">A biblioteca MQTT deve ser construída com o símbolo ***NX_SECURE_ENABLE*** definido.</span><span class="sxs-lookup"><span data-stu-id="aba35-124">The MQTT library must be built with the symbol ***NX_SECURE_ENABLE*** defined.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="aba35-125">Opções de configuração</span><span class="sxs-lookup"><span data-stu-id="aba35-125">Configuration Options</span></span>

<span data-ttu-id="aba35-126">Existem várias opções de configuração para a construção do cliente MQTT para o NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="aba35-126">There are several configuration options for building MQTT client for NetX Duo.</span></span> <span data-ttu-id="aba35-127">Segue-se uma lista de todas as opções, onde cada uma é descrita em detalhe.</span><span class="sxs-lookup"><span data-stu-id="aba35-127">Following is a list of all options, where each is described in detail.</span></span> <span data-ttu-id="aba35-128">Os valores predefinidos estão listados, mas podem ser redefinidos antes da inclusão do *nxd_mqtt_client.h.*</span><span class="sxs-lookup"><span data-stu-id="aba35-128">The default values are listed, but can be redefined prior to inclusion of *nxd_mqtt_client.h.*</span></span>

- <span data-ttu-id="aba35-129">**NX_DISABLE_ERROR_CHECKING**: Definida, esta opção remove a verificação básica de erros do cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="aba35-129">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic MQTT client error checking.</span></span> <span data-ttu-id="aba35-130">É normalmente usado após a depurada aplicação.</span><span class="sxs-lookup"><span data-stu-id="aba35-130">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="aba35-131">**NX_SECURE_ENABLE**: Definido, o Cliente MQTT é construído com suporte TLS.</span><span class="sxs-lookup"><span data-stu-id="aba35-131">**NX_SECURE_ENABLE**: Defined, MQTT Client is built with TLS support.</span></span>
<span data-ttu-id="aba35-132">A definição deste símbolo requer a instalação do módulo NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="aba35-132">Defining this symbol requires NetX Secure TLS module to be installed.</span></span>
<span data-ttu-id="aba35-133">*NX_SECURE_ENABLE* não é ativado por defeito.\*\*</span><span class="sxs-lookup"><span data-stu-id="aba35-133">*NX_SECURE_ENABLE* is not enabled by default.\*\*</span></span>
- <span data-ttu-id="aba35-134">**NXD_MQTT_REQUIRE_TLS**: Definida, a aplicação deve utilizar OTS para ligar ao corretor MQTT.</span><span class="sxs-lookup"><span data-stu-id="aba35-134">**NXD_MQTT_REQUIRE_TLS**: Defined, application must use TLS to connect to MQTT broker.</span></span> <span data-ttu-id="aba35-135">Esta funcionalidade requer *NX_SECURE_ENABLE* definidos.</span><span class="sxs-lookup"><span data-stu-id="aba35-135">This feature requires *NX_SECURE_ENABLE* defined.</span></span> <span data-ttu-id="aba35-136">Por padrão, este símbolo não está definido.</span><span class="sxs-lookup"><span data-stu-id="aba35-136">By default, this symbol is not defined.</span></span>
- <span data-ttu-id="aba35-137">**NXD_MQTT_MAX_TOPIC_NAME_LENGTH:** Depreciado.</span><span class="sxs-lookup"><span data-stu-id="aba35-137">**NXD_MQTT_MAX_TOPIC_NAME_LENGTH**: Deprecated.</span></span>
- <span data-ttu-id="aba35-138">**NXD_MQTT_MAX_MESSAGE_LENGTH:** Depreciado.</span><span class="sxs-lookup"><span data-stu-id="aba35-138">**NXD_MQTT_MAX_MESSAGE_LENGTH**: Deprecated.</span></span>
- <span data-ttu-id="aba35-139">**NXD_MQTT_KEEPALIVE_TIMER_RATE**: Define a taxa de temporizador MQTT, em carraças temporais ThreadX.</span><span class="sxs-lookup"><span data-stu-id="aba35-139">**NXD_MQTT_KEEPALIVE_TIMER_RATE**: Defines the MQTT timer rate, in ThreadX timer ticks.</span></span> <span data-ttu-id="aba35-140">Este temporizador é usado para acompanhar o tempo desde que a última mensagem de controlo MQTT foi enviada, e envia uma mensagem MQTT PINGREQ antes que o tempo de vida expire.</span><span class="sxs-lookup"><span data-stu-id="aba35-140">This timer is used to keep track of the time since last MQTT control message was sent, and sends out an MQTT PINGREQ message before the keep-alive time expires.</span></span> <span data-ttu-id="aba35-141">Este temporizador é ativado se o cliente ligar ao corretor com um conjunto de valor do temporizador vivo.</span><span class="sxs-lookup"><span data-stu-id="aba35-141">This timer is activated if the client connects to the broker with a keep-alive timer value set.</span></span> <span data-ttu-id="aba35-142">O valor predefinido é TX_TIMER_TICKS_PER_SECOND, que é um temporizador de um segundo.</span><span class="sxs-lookup"><span data-stu-id="aba35-142">The default value is TX_TIMER_TICKS_PER_SECOND, which is a one-second timer.</span></span>
- <span data-ttu-id="aba35-143">**NXD_MQTT_PING_TIMEOUT_DELAY**: Define o tempo que o cliente MQTT espera pelo PINGRESP do corretor depois de enviar O PINGREQ MQTT.</span><span class="sxs-lookup"><span data-stu-id="aba35-143">**NXD_MQTT_PING_TIMEOUT_DELAY**: Defines the time the MQTT client waits for PINGRESP from the broker after it sends out MQTT PINGREQ.</span></span> <span data-ttu-id="aba35-144">Se não for recebido PINGRESP após este atraso de tempo, o cliente trata o corretor como não-responsivo e desliga-se do corretor.</span><span class="sxs-lookup"><span data-stu-id="aba35-144">If no PINGRESP is received after this timeout delay, the client treats the broker as non-responsive and disconnects itself from the broker.</span></span> <span data-ttu-id="aba35-145">O atraso de tempo de ping predefinido é TX_TIMER_TICKS_PER_SECOND, que é um segundo.</span><span class="sxs-lookup"><span data-stu-id="aba35-145">The default PING timeout delay is TX_TIMER_TICKS_PER_SECOND, which is one second.</span></span>
- <span data-ttu-id="aba35-146">**NXD_MQTT_SOCKET_TIMEOUT**: Define o tempo de desconexão da tomada TCP quando se desliga do servidor MQTT em carraças temporais.</span><span class="sxs-lookup"><span data-stu-id="aba35-146">**NXD_MQTT_SOCKET_TIMEOUT**: Defines the time out in the TCP socket disconnect call when disconnecting from the MQTT server in timer ticks.</span></span> <span data-ttu-id="aba35-147">O valor predefinido é NX_WAIT_FOREVER.</span><span class="sxs-lookup"><span data-stu-id="aba35-147">The default value is NX_WAIT_FOREVER.</span></span>

## <a name="sample-mqtt-program"></a><span data-ttu-id="aba35-148">Programa MQTT de amostra</span><span class="sxs-lookup"><span data-stu-id="aba35-148">Sample MQTT program</span></span>

<span data-ttu-id="aba35-149">O seguinte programa ilustra uma simples aplicação MQTT.</span><span class="sxs-lookup"><span data-stu-id="aba35-149">The following program illustrates a simple MQTT application.</span></span> <span data-ttu-id="aba35-150">Para simplificar, presume-se que os códigos de devolução são bem sucedidos, pelo que não é feita mais verificação de erros.</span><span class="sxs-lookup"><span data-stu-id="aba35-150">For simplicity, the return codes are assumed to be successful, therefore no further error checking is done.</span></span>

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
