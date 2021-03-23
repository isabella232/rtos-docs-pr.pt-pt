---
title: Capítulo 1 - Introdução ao Azure RTOS NetX Duo MQTT
description: O pacote de clientes NetX Duo MQTT requer que o NetX Duo (versão 5.10 ou posterior) seja instalado, devidamente configurado, e a instância IP foi criada.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2e13b997f987e2fd82569bcb1904218908313d70
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825910"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mqtt"></a>Capítulo 1 - Introdução ao Azure RTOS NetX Duo MQTT

## <a name="netx-duo-mqtt-requirements"></a>Requisitos de MQTT duo NetX

O pacote de clientes Azure RTOS NetX Duo MQTT exige que o NetX Duo (versão 5.10 ou posterior) seja instalado, devidamente configurado, e a instância IP tenha sido criada. O módulo TCP deve ser ativado no sistema. Além disso, se for necessária a segurança TLS, o módulo NetX Secure TLS tem de ser configurado de acordo com o parâmetro de segurança exigido pelo corretor.

## <a name="netx-duo-mqtt-specification"></a>Especificação MQTT duo netx

O implementação do cliente NetX Duo MQTT está em conformidade com a versão OASIS MQTT 3.1.1 out<sup>29 th</sup> 2014. A especificação pode ser encontrada em:

- [http://mqtt.org/](http://mqtt.org/)

## <a name="netx-duo-mqtt-basic-operation"></a>Operação Básica NetX Duo MQTT

O MQTT (Message Queue Telemetry Transport) baseia-se no modelo de assinante-editor. Um cliente pode publicar informações a outros clientes através de um corretor. Um cliente, se estiver interessado num tópico, pode subscrever o tópico através do corretor. Um corretor é responsável pela entrega de mensagens publicadas aos seus clientes que subscrevem o tema. Neste modelo de assinante-editor, vários clientes podem publicar dados com o mesmo tópico. Um cliente receberá uma mensagem que publica se o cliente subscrever o mesmo tópico.

Dependendo do caso de utilização, um cliente pode escolher um dos 3 níveis QoS ao publicar uma mensagem:

- **QoS 0**: A mensagem é entregue no máximo uma vez. As mensagens enviadas com o QoS 0 podem perder-se.
- **QoS 1**: A mensagem é entregue pelo menos uma vez. As mensagens enviadas com o QoS 1 podem ser entregues mais de uma vez.
- **QoS 2**: A mensagem é entregue exatamente uma vez. As mensagens enviadas com o QoS 2 estão garantidamente entregues, sem duplicação.

> [!NOTE]
> Esta implementação do cliente MQTT não suporta mensagens QoS de nível 2.

Uma vez que o QoS 1 e o QoS 2 estão garantidos para serem entregues, o corretor mantém o estado das mensagens QoS 1 e QoS 2 enviadas a cada cliente. Isto é particularmente importante para os clientes que esperam mensagens QoS1 ou QoS 2. O cliente pode ser desligado do corretor (por exemplo, quando o cliente reinicia ou o link de comunicação é temporariamente perdido). O corretor deve armazenar mensagens QoS 1 e QoS 2 para que as mensagens possam ser entregues mais tarde assim que o cliente estiver novamente ligado ao corretor. No entanto, o cliente pode optar por não receber nenhuma mensagem velha do corretor após a reconexão. O cliente pode fazê-lo iniciando a ligação com a bandeira *clean_session* definida para ***NX_TRUE** _. Neste caso, ao receber a mensagem MQTT CONNECT, o corretor descartará qualquer informação de sessão associada a este cliente, incluindo mensagens QoS 1 ou QoS 2 não entregues ou não confirmadas. Se a _bandeira clean_session* for para ***NX_FALSE,**_ o servidor reensificará as mensagens QoS 1 e QoS 2. O Cliente MQTT também reencamende quaisquer mensagens não reconhecidas se _clean_session* estiver definido para ***NX_TRUE*.** Este reconhecimento é diferente da camada TCP ACK, embora isso também aconteça. O cliente MQTT envia um reconhecimento ao corretor.

Uma aplicação cria uma instância de cliente MQTT ligando ***nxd_mqtt_client_create()** _. Uma vez criado o cliente, a aplicação pode ligar-se ao corretor chamando _*_nxd_mqtt_client_connect()_*_. Depois de ligar ao corretor, o cliente pode subscrever um tópico chamando _*_nxd_mqtt_client_subscribe()_*_, ou publicar um tópico chamando _*_nxd_mqtt_client_publish()_**.

As mensagens MQTT recebidas são armazenadas na fila de receção na instância do cliente MQTT. A aplicação recupera esta mensagem chamando ***nxd_mqtt_client_message_get()***. Se houver mensagens na fila de receção, a primeira mensagem (por exemplo, a mais antiga) da fila é devolvida ao chamador. O tópico da mensagem também é devolvido.

> [!NOTE]
> A função ***nxd_mqtt_client_message_get()** _ não bloqueia se a fila de receção do cliente MQTT estiver vazia. A função retorna imediatamente com o código de devolução _*_NXD_MQTT_NO_MESSAGE_**. O pedido deve tratar este valor de devolução como uma indicação de que a fila de receção está vazia, não um erro.

Para evitar a sondagem da fila de receção de mensagens recebidas, a aplicação pode registar uma função de retorno com o cliente MQTT chamando ***nxd_mqtt_client_recieve_notify_set()***. A função de retorno é declarada como:

```c
VOID (*receive_notify_callback)(NXD_MQTT_CLIENT *client_ptr, 
    UINT message_count);
```

Como o cliente MQTT recebe mensagens do corretor, invoca a função de retorno se a função estiver definida. A função de retorno passa o ponteiro para o bloco de controlo do cliente e um valor de contagem de mensagens. O valor da contagem de mensagens indica o número de mensagens MQTT na fila de receção. Note que esta função de retorno executa no contexto do fio do cliente MQTT. Portanto, a função de retorno não deve executar quaisquer procedimentos que possam bloquear o fio do cliente MQTT. A função de retorno deve acionar o fio de aplicação para chamar ***nxd_mqtt_client_message_get para*** recuperar as mensagens.

Para desligar e encerrar o serviço de cliente MQTT, o pedido utilizará o serviço ***nxd_mqtt_client_disconnect()** e _*_nxd_mqtt_client_delete()._*_ Chamar _*_nxd_mqtt_client_disconnect simplesmente_*_ desliga a ligação TCP ao corretor. Lança mensagens já recebidas e armazenadas na fila de receção. No entanto, não liberta mensagens QoS de nível 1 na fila de transmissão. As mensagens qoS nível 1 são retransmitidas após a ligação, assumindo que a bandeira _*_clean_session_*_ está definida para _ *_NX_FALSE._**

O corretor também pode desligar-se do cliente. Quando a ligação TCP entre o cliente e o corretor é encerrada, o pedido pode ser notificado pela função de notificação de desconexão. Para utilizar o mecanismo de notificação, a aplicação instala a função de notificação de desconexão chamando ***nxd_mqtt_client_disconnect_notify_set*.** Uma vez observada uma desconexão TCP e a sessão MQTT foi criada, a função de notificação é invocada.

Chamar ***nxd_mqtt_client_delete()*** liberta todos os blocos de mensagens na fila de transmissão e na fila de receção. As mensagens QoS de nível 1 não reconhecidas também são eliminadas.

## <a name="secure-mqtt-connection"></a>Ligação MQTT segura

O cliente MQTT faz uma ligação segura ao corretor utilizando o módulo NetX Secure TLS. O número de porta padrão para MQTT com segurança TLS é 8883, definido em ***NXD_MQTT_TLS_PORT***.

Para criar uma ligação MQTT segura ao corretor, uma sessão TLS precisa de ser negociada após a criação de uma ligação TCP, antes de as mensagens MQTT CONNECT poderem ser enviadas para o corretor. A sessão TLS configurada é realizada chamando ***nxd_mqtt_client_secure_connect()*** e passando numa função de chamada de configuração TLS definida pelo utilizador. Durante a fase de ligação MQTT, uma vez estabelecida a ligação TCP, o cliente invoca a função de chamada de configuração TLS para iniciar um processo de aperto de mão TLS adequado. Após a sessão TLS ser estabelecida, o cliente continua a mensagem MQTT CONNECT sobre o canal seguro.

A função de retorno definido pelo utilizador tem cinco valores de entrada e é declarada como:

```c
UINT tls_Setup_callback(NXD_MQTT_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certificate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_cerfiticate);
```

Abaixo está uma descrição dos parâmetros de entrada:

- **client_ptr**: Ponter para o bloco de controlo do cliente MQTT.
- **session_ptr**: Ponteiro para o bloco de controlo de sessão TLS.
- **certificate_ptr**: Ponteiro para o bloco de controlo do certificado. A função de configuração configura este certificado antes de enviá-lo para o corretor.
- **trusted_certificate_ptr**: Ponter para o certificado de confiança. A função de configuração TLS configura o certificado fidedigno para autenticar o servidor.

Na função de configuração TLS, a aplicação é responsável pela criação de uma sessão TLS e configurar a sessão com um certificado adequado. O seguinte código pseudo descreve um procedimento típico de arranque de sessão TLS. O leitor é encaminhado para o Guia de Utilizador NetX Secure TLS para obter detalhes sobre a utilização de APIs TLS.

Abaixo está um exemplo de chamada de configuração TLS:

```c
UINT tls_setup_callback(NXD_MQTT_CLIENT *client_pt
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certrifcate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_certificate_ptr)
{
    /* Initialize TLS module */
    nx_secure_tls_initialize();

    /* Create a TLS session */
    nx_secure_tls_session_create(session_ptr, …);

    /* Need to allocate space for the certificate coming in from the broker. */
    memset(certificate_ptr), 0, sizeof(NX_SECURE_TLS_CERTIFICATE));

    nx_secure_tls_remote_certificate_allocate(session_ptr, certificate_ptr);

    /* Add a CA Certificate to our trusted store for verifying incomingserver certificates. */
    nx_secure_tls_certificate_initialize(
        trusted_certificate_ptr,
        ca_cert_der,
        ca_cert_der_len, NULL, 0);
    nx_secure_tls_trusted_certificate_add(session_ptr,
        trusted_certificate));
}
```

## <a name="known-limitations-of-the-netx-duo-mqtt-client"></a>Limitações conhecidas do Cliente MQTT Duo NetX

- NetX Duo MQTT não suporta o envio ou receção de mensagens QoS de nível 2.
- NetX Duo MQTT não suporta pacotes acorrentados.
