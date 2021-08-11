---
title: Capítulo 4 - Descrição dos serviços Azure RTOS NetX Secure DTLS
description: Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX Secure DTLS listados por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 45966e7c8ea9be18bf294e8a7540e7226e803f29ae4f3ad3faaa29e4939c2ed8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801852"
---
# <a name="chapter-4-description-of-azure-rtos-netx-secure-dtls-services"></a>Capítulo 4: Descrição dos serviços Azure RTOS NetX Secure DTLS

Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX Secure DTLS (listados abaixo) por ordem alfabética.

Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pela macro **NX_SECURE_DISABLE_ERROR_CHECKING** que é utilizada para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

- [nx_secure_dtls_client_session_start](#nx_secure_dtls_client_session_start)
- [nx_secure_dtls_packet_allocate](#nx_secure_dtls_packet_allocate)
- [nx_secure_dtls_psk_add](#nx_secure_dtls_psk_add)
- [nx_secure_dtls_server_create](#nx_secure_dtls_server_create)
- [nx_secure_dtls_server_delete](#nx_secure_dtls_server_delete)
- [nx_secure_dtls_server_local_certificate_add](#nx_secure_dtls_server_local_certificate_add)
- [nx_secure_dtls_server_local_certificate_remove](#nx_secure_dtls_server_local_certificate_remove)
- [nx_secure_dtls_server_notify_set](#nx_secure_dtls_server_notify_set)
- [nx_secure_dtls_server_psk_add](#nx_secure_dtls_server_psk_add)
- [nx_secure_dtls_server_session_send](#nx_secure_dtls_server_session_send)
- [nx_secure_dtls_server_session_start](#nx_secure_dtls_server_session_start)
- [nx_secure_dtls_server_start](#nx_secure_dtls_server_start)
- [nx_secure_dtls_server_stop](#nx_secure_dtls_server_stop)
- [nx_secure_dtls_server_trusted_certificate_add](#nx_secure_dtls_server_trusted_certificate_add)
- [nx_secure_dtls_server_trusted_certificate_remove](#nx_secure_dtls_server_trusted_certificate_remove)
- [nx_secure_dtls_server_x509_client_verify_configure](#nx_secure_dtls_server_x509_client_verify_configure)
- [nx_secure_dtls_server_x509_client_verify_disable](#nx_secure_dtls_server_x509_client_verify_disable)
- [nx_secure_dtls_session_client_info_get](#nx_secure_dtls_session_client_info_get)
- [nx_secure_dtls_session_create](#nx_secure_dtls_session_create)
- [nx_secure_dtls_session_delete](#nx_secure_dtls_session_delete)
- [nx_secure_dtls_session_end](#nx_secure_dtls_session_end)
- [nx_secure_dtls_session_local_certificate_add](#nx_secure_dtls_session_local_certificate_add)
- [nx_secure_dtls_session_local_certificate_remove](#nx_secure_dtls_session_local_certificate_remove)
- [nx_secure_dtls_session_receive](#nx_secure_dtls_session_receive)
- [nx_secure_dtls_session_reset](#nx_secure_dtls_session_reset)
- [nx_secure_dtls_ session_send](#nx_secure_dtls_-session_send)
- [nx_secure_dtls_session_trusted_certificate_add](#nx_secure_dtls_session_trusted_certificate_add)
- [nx_secure_dtls_session_trusted_certificate_remove](#nx_secure_dtls_session_trusted_certificate_remove)


## <a name="nx_secure_dtls_client_session_start"></a>nx_secure_dtls_client_session_start

Inicie uma Sessão de Clientes DTLS Segura netX

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_dtls_client_session_start(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        NX_UDP_SOCKET *udp_socket,
                        NXD_ADDRESS *ip_address, UINT port,
                        UINT wait_option);

```

### <a name="description"></a>Description

Este serviço inicia uma sessão de Cliente DTLS, conectando-se ao servidor no endereço IP fornecido e na porta UDP, utilizando a tomada UDP fornecida para comunicações de rede.

O bloco de controlo de sessão DTLS deve ser inicializado antes de ligar para este serviço utilizando nx_secure_dtls_session_create. Além disso, o Cliente DTLS exige que pelo menos um certificado de CA fidedigno tenha sido adicionado à sessão usando nx_secure_dtls_session_trusted_certificate_add ou Chaves Pré-Partilhadas estejam ativadas e configuradas.

### <a name="parameters"></a>Parâmetros

- **dtls_session** Ponteiro para uma estrutura de Sessão DTLS que foi inicializada anteriormente.
- **udp_socket** Tomada UDP inicializada que será usada para estabelecer comunicações de rede com o servidor DTLS remoto.
- **ip_address** Ponteiro para a estrutura do endereço IP que contém o endereço do servidor DTLS remoto.
- **porto** Tomada UDP inicializada que será usada para estabelecer comunicações de rede com o servidor DTLS remoto.
- **wait_option** Opção de suspensão para tentativa de ligação.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Atribuição bem sucedida de certificado à sessão.
- **NX_NOT_CONNECTED** (0x38) O servidor não pode ser alcançado no endereço e na porta dado.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) Um tipo de mensagem TLS/DTLS recebido está incorreto.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) Uma cifra fornecida pelo hospedeiro remoto não é suportada.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) O processamento de mensagens durante o aperto de mão TLS falhou.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Uma mensagem recebida falhou numa verificação de HASH MAC.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Um envio de tomada TCP subjacente falhou.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Uma mensagem recebida tinha um campo de comprimento inválido.
- **NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) Uma mensagem ChangeCipherSpec recebida estava incorreta.
- **NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) Um certificado TLS de entrada é inutilizável para identificar o servidor DTLS remoto.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) A cifra de chave pública fornecida pelo hospedeiro remoto não é suportada.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) O anfitrião remoto não indicou cifrasuites que sejam suportadas pela pilha DTLS NetX Secure.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Uma mensagem DTLS recebida tinha uma versão DTLS desconhecida no seu cabeçalho.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Uma mensagem DTLS recebida tinha uma versão DTLS conhecida mas não suportada no seu cabeçalho.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Uma atribuição interna de pacotes TLS falhou.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) O anfitrião remoto forneceu um certificado inválido.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) O anfitrião remoto enviou um alerta indicando um erro e terminando a sessão TLS.
- **NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) Uma entrada na tabela cifrasumita tinha um ponteiro de função NU.
- **NX_PTR_ERROR** (0x07) Sessão inválida, tomada ou ponteiro de endereço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                           &nx_crypto_tls_ciphers,
                                           crypto_metadata,
                                           sizeof(crypto_metadata),
                                           packet_buffer,
                                           sizeof(packet_buffer),
                                           REMOTE_CERT_NUMBER,
                                           remote_certs_buffer,
                                           sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
       Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                      trusted_cert_der,
                                      trusted_cert_der_len,
                                      NX_NULL, 0, NX_NULL, 0,
                                      NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                   &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                                  &udp_socket, &server_ip,
                                                  4443,
                                                  NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
      /* Error! */
      return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session, &receive_packet,
                                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session, NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_session_receive, nx_secure_dtls_session_send,
- nx_secure_dtls_session_create

## <a name="nx_secure_dtls_packet_allocate"></a>nx_secure_dtls_packet_allocate

Aloque um pacote para uma Sessão de DTLS NetX Secure

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_packet_allocate(
                              NX_SECURE_DTLS_SESSION *session_ptr,
                         NX_PACKET_POOL *pool_ptr,
                         NX_PACKET **packet_ptr,
                              ULONG wait_option);

```

### <a name="description"></a>Description

Este serviço atribui uma NX_PACKET para a sessão DTLS ativa especificada a partir do NX_PACKET_POOL especificado. Este serviço deve ser chamado pela aplicação para atribuir pacotes de dados a serem enviados através de uma ligação DTLS. A sessão DTLS deve ser inicializada antes de ligar para este serviço.

O pacote atribuído é devidamente inicializado de modo a que os dados do cabeçalho e do rodapé DTLS possam ser adicionados após a população dos dados do pacote. O comportamento é idêntico ao *nx_packet_allocate*.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão DTLS.
- **pool_ptr** O ponteiro para um NX_PACKET_POOL a partir do qual atribuir o pacote.
- **packet_ptr** Ponteiro de saída para o pacote recém-atribuído.
- **wait_option** Opção de suspensão para alocação de pacotes.


### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Atribuição de pacotes bem sucedidos.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) A atribuição de pacotes subjacentes falhou.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) A sessão DTLS fornecida não foi inicializada.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Allocate a new DTLS packet from the previously created packet pool and
previously initialized DTLS session.   */

status = nx_secure_dtls_packet_allocate(&dtls_session, &pool_0, &packet_ptr,
                                                              NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in
the variable packet_ptr.  */

```

### <a name="see-also"></a>Consulte também

- nx_secure_x509_certificate_initialize, nx_secure_dtls_session_create,
- nx_secure_dtls_session_trusted_certificate_add,
- nx_secure_dtls_session_send, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_end, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_psk_add"></a>nx_secure_dtls_psk_add

Adicione uma chave pré-partilhada a uma Sessão de DTLS Segura netX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_psk_add(NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a>Description

Este serviço adiciona uma chave pré-partilhada (PSK), a sua cadeia de identidade e uma dica de identidade para um bloco de controlo DTLS Session. O PSK é utilizado em vez de um certificado digital quando as cifrasuites PSK são ativadas e utilizadas.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão DTLS previamente criada.
- **pre_shared_key** O valor real do PSK.
- **psk_length** O comprimento do valor PSK.
- **psk_identity** Uma corda usada para identificar este valor psk.
- **identity_length** O comprimento da identidade psk.
- **dica** Uma cadeia usada para indicar qual grupo de PSKs escolher num servidor TLS.
- **hint_length** O comprimento da corda de sugestão.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Adição bem sucedida de PSK.
- **NX_PTR_ERROR** (0x07) Ponteiro de sessão DTLS inválido.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Não pode adicionar outro PSK.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_psk_add(&dtls_session, psk,
                            sizeof(psk), “psk_1”, 4,
                            “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */


```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_server_psk_add, nx_secure_dtls_client_session_create

## <a name="nx_secure_dtls_server_create"></a>nx_secure_dtls_server_create

Criar um Servidor DTLS Seguro NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_create(
                NX_SECURE_DTLS_SERVER *server_ptr, NX_IP *ip_ptr,
                UINT port, ULONG timeout, VOID *session_buffer,
                UINT session_buffer_size,
                const NX_SECURE_TLS_CRYPTO *crypto_table,
                VOID *crypto_metadata_buffer, ULONG crypto_metadata_size,
                UCHAR *packet_reassembly_buffer,
                UINT packet_reassembly_buffer_size,
                UINT (*connect_notify)(
                              NX_SECURE_DTLS_SESSION *dtls_session,
                              NXD_ADDRESS *ip_address, UINT port),
                UINT (*receive_notify)(
                              NX_SECURE_DTLS_SESSION *dtls_session)));

```

### <a name="description"></a>Description

Este serviço cria uma instância de um servidor DTLS para lidar com pedidos DTLS de entrada numa determinada porta UDP. Devido ao facto de a UDP ser apátrida, os pedidos do DTLS de vários clientes podem entrar numa única porta enquanto outras sessões de DTLS estão ativas. Assim, o servidor é necessário para manter sessões ativas e encaminhar corretamente as mensagens recebidas para o manipulador adequado.

O parâmetro ip_ptr aponta para uma NX_IP instância a utilizar para a tomada interna do UDP associada ao Servidor DTLS (e armazenada no bloco de controlo NX_SECURE_DTLS_SERVER). A instância IP e a porta são usadas para definir a interface UDP sobre a qual o servidor é instantâneo com o serviço nx_secure_dtls_server_start.

O parâmetro tampão de sessão é utilizado para manter os blocos de controlo para todas as possíveis sessões de DTLS simultâneas para o servidor DTLS. Deve ser atribuído com um tamanho que seja um múltiplo do tamanho da estrutura do bloco de controlo NX_SECURE_DTLS_SESSION.

Para calcular o tamanho necessário dos metadados, pode ser utilizado o nx_secure_tls_metadata_size_calculate API.

O parâmetro packet_reassembly_buffer é usado pela DTLS para remontar os datagramas de UDP num registo DTLS completo para efeitos de desencriptação e deve ser grande o suficiente para acomodar o maior registo DTLS esperado (16KB é o tamanho máximo de registo do DTLS, mas muitas aplicações não enviam tantos dados num único registo).

A rotina de chamada connect_notify é invocada sempre que um novo cliente DTLS se conecta ao servidor. Cabe à aplicação iniciar a sessão DTLS utilizando o *serviço nx_secure_dtls_server_session_start*. Embora a sessão possa ser iniciada na própria chamada, recomenda-se que a chamada apenas seja utilizada para notificar o fio de aplicação (ou fio DTLS dedicado criado pela aplicação) da ligação, uma vez que o retorno é invocado pelo fio IP que é utilizado para processar todo o processamento de rede de nível inferior (por exemplo, UDP). Isto pode ser tão simples como guardar o parâmetro de sessão DTLS (fornecido como parâmetro para a chamada) e invocar nx_secure_dtls_server_session_start no outro fio. A connect_notify chamada deve geralmente voltar NX_SUCCESS.

A rotina de chamada receive_notify é invocada sempre que é recebido um registo DTLS que corresponda a uma sessão DTLS estabelecida existente (o endereço IP e a porta do anfitrião remoto são utilizados para identificar uma sessão existente). Isto representa os "dados de aplicação" que são encriptados e enviados sobre DTLS. O pedido deve ligar para o *serviço nx_secure_dtls_session_receive* na sessão DTLS fornecida para recuperar os dados recebidos. Tal como acontece com a chamada connect_receive, recomenda-se que a sessão seja passada para outro fio para manusear o processamento da mensagem à medida que a chamada é invocada a partir do fio IP. A receive_notify chamada deve geralmente voltar NX_SUCCESS.

### <a name="parameters"></a>Parâmetros

- **server_ptr** Ponteiro para uma instância do Servidor DTLS previamente criada.
- **ip_ptr** Ponteiro para um bloco de controlo de NX_IP inicializado para usar como interface de rede para o servidor DTLS.
- **porto** A porta UDP local à qual está ligada a tomada UDP do servidor DTLS.
- **tempo limite** Valor de tempo limite para utilizar para operações de rede.
- **session_buffer** Espaço tampão para conter blocos de controlo para todos os casos de NX_SECURE_DTLS_SESSION atribuídos a esta instância do Servidor DTLS.
- **session_buffer_size** Tamanho do tampão da sessão. Isto determina o número de sessões DTLS atribuídas ao Servidor DTLS.
- **crypto_table** Ponteiro para uma estrutura de tabela de encriptação TLS/DTLS utilizada para todas as operações criptográficas.
- **crypto_metadata_buffer** Espaço tampão para cálculos de operação criptográfica e informações do estado.
- **crypto_metadata_size** Tamanho do tampão de metadados.
- **packet_reassembly_buffer** Tampão usado pela DTLS para remontar dados de UDP em registos DTLS para desencriptação.
- **packet_reassembly_buffer_size** Tamanho do tampão de remontagem. Geralmente deve ser superior a 16KB, mas pode ser menor dependendo da aplicação.
- **connect_notify** Rotina de chamada invocada sempre que um cliente DTLS remoto tenta ligar-se a este servidor DTLS.
- **receive_notify** Callback invocado sempre que os dados da aplicação são recebidos durante uma sessão DTLS existente.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Criação bem sucedida do servidor DTLS.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido passou.
- **NX_INVALID_PARAMETERS** (0x4D) Não há espaço tampão suficiente para sessões, remontagem de pacotes ou criptografia.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
    *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE, dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                        device_cert_der_len, NX_NULL, 0,
                        device_cert_key_der, device_cert_key_der_len,
                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);

        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                           NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session, &packet_pool,
                                                   &send_packet, NX_IP_PERIODIC_RATE);

        /* Check for errors and prepare response data
        (e.g. nx_packet_data_append). */

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

        }

        /* If not processing connections or received data,
        let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* Server processing is done, stop the server
    instance from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_server_start, nx_secure_dtls_server_delete,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send.
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_delete"></a>nx_secure_dtls_server_delete

Liberte os recursos utilizados por um Servidor DTLS Seguro NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_delete(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Description

Este serviço liberta os recursos atribuídos a uma instância do Servidor DTLS, incluindo a tomada interna do UDP utilizada pelo servidor.

### <a name="parameters"></a>Parâmetros

- **server_ptr** Ponteiro para uma instância do Servidor DTLS previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Eliminação bem sucedida do servidor.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido passou.
- **NX_STILL_BOUND** (0x42) tomada UDP ainda está ligada.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
*ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                            LOCAL_SERVER_PORT,
                                            NX_IP_PERIODIC_RATE,
                                            dtls_server_session_buffer,
                                            sizeof(dtls_server_session_buffer),
                                            &tls_crypto_table,
                                            crypto_metadata_buffer,
                                            sizeof(crypto_metadata_buffer),
                                            packet_buffer, sizeof(packet_buffer),
                                            dtls_server_connect_notify,
                                            dtls_server_receive_notify);


    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                         NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                        &packet_pool,
                                                        &send_packet,
                                                        NX_IP_PERIODIC_RATE);

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send.
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_local_certificate_add"></a>nx_secure_dtls_server_local_certificate_add

Adicione um certificado de identidade de servidor local a um Servidor DTLS Seguro NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_local_certificate_add(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                 NX_SECURE_X509_CERT *certificate,
                                 UINT cert_id);

```

### <a name="description"></a>Description

Este serviço adiciona um certificado de identidade do servidor local a uma instância do Servidor DTLS. Pelo menos um certificado de identidade é necessário para que os clientes se conectem a um servidor DTLS a menos que seja utilizado um mecanismo de autenticação alternativo (por exemplo, Chaves Pré-Partilhadas).

O parâmetro cert_id é um identificador numérico, sem zero para o certificado. Isto permite que o certificado seja facilmente removido ou encontrado no caso de existirem vários certificados de identidade com o mesmo Nome Comum X.509 presente na loja do servidor DTLS. Consulte o Guia de Utilizador NetX Secure TLS para obter mais informações sobre os certificados de servidor X.509.

### <a name="parameters"></a>Parâmetros

- **server_ptr** Ponteiro para uma instância do Servidor DTLS previamente criada.
- **certificado** Ponteiro para uma estrutura de certificado X.509 previamente inicializada.
- **cert_id** Identificador único numérico não zero para este certificado neste servidor DTLS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Adição bem sucedida de certificado ao servidor DTLS.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido passou.
- **NX_INVALID_PARAMETERS** (0x4D) Foi aprovado um certificado de identificação de 0.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

*Consulte a referência para *nx_secure_dtls_server_create* para obter um exemplo mais completo.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                            certificate_der_data,
                            sizeof(certificate_der_data),
                            NX_NULL, 0,
                            certificate_key_der_data,
                            sizeof(certificate_key_der_data),
                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Process incoming requests and data. */
    }

}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send.
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_local_certificate_remove,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_local_certificate_remove"></a>nx_secure_dtls_server_local_certificate_remove

Remova um certificado de identidade do servidor local de um Servidor DTLS Seguro NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_local_certificate_remove(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                   UCHAR *common_name,
                                   UINT common_name_length,
                                   UINT cert_id);

```

### <a name="description"></a>Description

Este serviço remove um certificado de identidade do servidor local de uma instância do Servidor DTLS. Pelo menos um certificado de identidade é necessário para que os clientes se conectem a um servidor DTLS a menos que seja utilizado um mecanismo de autenticação alternativo (por exemplo, Chaves Pré-Partilhadas).

O certificado a retirar pode ser identificado pelo seu Nome Comum X.509 ou pelo cert_id numérico que foi atribuído na chamada para *nx_secure_dtls_server_local_certificate_add*. O cert_id é utilizado apenas para identificar o certificado e é mantido pelo pedido. Se o nome comum for utilizado em vez do identificador de certificado numérico, o parâmetro cert_id deve ser definido para 0.

> [!NOTE]
> Remover um certificado enquanto um aperto de mão DTLS está sendo processado resultará em comportamento inesperado. O *serviço nx_secure_dtls_server_stop* deve ser chamado antes de retirar os certificados.

### <a name="parameters"></a>Parâmetros

- **server_ptr** Ponteiro para uma instância do Servidor DTLS previamente criada.
- **common_name** X.509 CommonName do certificado a remover. Se isto for usado, passe cert_id como zero.
- **common_name_length** Comprimento de common_name cordas em bytes.
- **cert_id** Identificador único numérico não zero para este certificado neste servidor DTLS. Se isto for utilizado, passe NX_NULL para o parâmetro common_name.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Remoção bem sucedida do certificado do servidor DTLS.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido passou.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Não foi encontrado nenhum certificado correspondente ao cert_id ou common_name no servidor DTLS.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT, NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                        certificate_der_data,
                                        sizeof(certificate_der_data),
                                        NX_NULL, 0, certificate_key_der_data,
                                        sizeof(certificate_key_der_data),
                                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                     &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before removing a certificate. */
    Status = nx_secure_dtls_server_stop(&dtls_server);

    /* At some point in the future we decide to remove the certificate we added.
    We can use the certificate identifier we passed into the call to
    nx_secure_dtls_local_certificate_add (value = 1); */
    status = nx_secure_dtls_server_local_certificate_remove(&dtls_server,
                                                          NX_NULL, 0, 1);

}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_local_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_notify_set"></a>nx_secure_dtls_server_notify_set

Atribuir rotinas de chamada de notificação opcional a um Servidor DTLS Seguro NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_notify_set(
                         NX_SECURE_DTLS_SERVER *server_ptr,
                         UINT (*disconnect_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session),
                         UINT (*error_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session,
                                      UINT error_code));

```

### <a name="description"></a>Description

Este serviço pode ser utilizado para adicionar rotinas de chamada de notificação opcionais a um servidor DTLS. Qualquer um dos parâmetros de retorno pode ser passado como NX_NULL se apenas uma chamada for desejada.

A disconnect_notify chamada é invocada quando um cliente remoto termina uma sessão de DTLS. O parâmetro dtls_session é a instância da sessão que foi encerrada. A chamada deve geralmente voltar NX_SUCCESS.

A chamada error_notify é invocada sempre que ocorre um erro ou tempo limite de DTLS. O parâmetro dtls_session é a instância de sessão para a qual ocorreu o erro, e error_code é o código de estado numérico para o erro que causou o problema (ver apêndice A)

NetX Secure Return/Error Codes para uma lista de códigos de erro que podem ser devolvidos). A chamada deve geralmente voltar NX_SUCCESS.

### <a name="parameters"></a>Parâmetros

- **server_ptr** Ponteiro para uma instância do Servidor DTLS previamente criada.
- **disconnect_notify** Rotina de chamada invocada sempre que um anfitrião remoto do cliente fecha uma sessão de DTLS.
- **error_notify** Rotina de retorno invocada sempre que dTLS encontra um erro ou tempo limite.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Atribuição bem sucedida de rotinas de retorno.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido passou.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

UINT disconnect_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
NXD_ADDRESS client_ip_addr;
UINT client_port;
UINT local_port;

    /* We have received a disconnection notice (CloseNotify message) from a
       remote client. Application can use the dtls_session parameter for any
       desired processing. */

    /* See what client disconnected by extracting its IP address and port.
       NOTE: depending on how the session ended, the client information may
             no longer be available. */
    status  = nx_secure_dtls_session_client_info_get(dtls_session,
                                                    &ip_addr,
                                                    &client_port,
                                                    &local_port);

    return(NX_SUCCESS);
}

UINT error_notify(NX_SECURE_DTLS_SESSION *dtls_session, UINT error_code)
{
    /* The DTLS server has encountered an error or timeout condition. We
    can use the error_code parameter to determine the error and we
    can insect the dtls_session for more information. */

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Other setup (e.g. certificates) goes here … */

    status = nx_secure_dtls_server_notify_set(&dtls_server, disconnect_notify,
                                                                 error_notify);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop

## <a name="nx_secure_dtls_server_psk_add"></a>nx_secure_dtls_server_psk_add

Adicione uma chave pré-partilhada a um servidor DTLS Seguro NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_psk_add(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *pre_shared_key, UINT psk_length,
                                UCHAR *psk_identity,
                                UINT identity_length, UCHAR *hint,
                                UINT hint_length);

```

### <a name="description"></a>Description

Este serviço adiciona uma chave pré-partilhada (PSK), a sua cadeia de identidade e uma sugestão de identidade para um bloco de controlo do Servidor DTLS. O PSK é utilizado em vez de um certificado digital quando as cifrasuites PSK são ativadas e utilizadas.

O PSK adicionado é replicado em todas as sessões DTLS atribuídas ao Servidor DTLS (através do tampão de sessão dado na chamada para nx_secure_dtls_server_create).

### <a name="parameters"></a>Parâmetros

- **server_ptr** Ponteiro para uma instância do Servidor DTLS previamente criada.
- **pre_shared_key** O valor real do PSK.
- **psk_length** O comprimento do valor PSK.
- **psk_identity** Uma corda usada para identificar este valor psk.
- **identity_length** O comprimento da identidade psk.
- **dica** Uma cadeia usada para indicar qual grupo de PSKs escolher num servidor TLS.
- **hint_length** O comprimento da corda de sugestão.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Adição bem sucedida de PSK.
- **NX_PTR_ERROR** (0x07) Ponteiro do servidor DTLS inválido.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Não pode adicionar outro PSK.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_server_psk_add(&dtls_server, psk, sizeof(psk), “psk_1”,
   4, “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_psk_add, nx_secure_dtls_server_create

## <a name="nx_secure_dtls_server_session_send"></a>nx_secure_dtls_server_session_send

Envie dados sobre uma sessão de DTLS estabelecida com um Servidor DTLS Seguro NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_session_send(
                                NX_SECURE_DTLS_SESSION *session_ptr,
                               NX_PACKET *packet_ptr);

```

### <a name="description"></a>Description

Este serviço envia um pacote de dados sobre uma sessão estabelecida do DTLS Server para um anfitrião remoto do Cliente DTLS. A sessão utilizada é obtida na rotina de chamada receive_notify fornecida a nx_secure_dtls_session_create.

Os dados fornecidos no pacote, que devem ser atribuídos utilizando *nx_secure_dtls_packet_allocate,* são encriptados utilizando os parâmetros e rotinas criptográficos da sessão DTLS e depois enviados para o anfitrião remoto através da porta UDP interna do DTLS Server para o endereço IP e porta do cliente anexado (armazenados na Sessão DTLS).

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de sessão DTLS obtida a partir da rotina de chamada receive_notify fornecida pela aplicação.
- **packet_ptr** Ponteiro para uma NX_PACKET instância atribuída anteriormente e povoada com dados de aplicação.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Criação bem sucedida do servidor DTLS.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido passou.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Ocorreu um erro na operação de envio da UDP subjacente.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;


/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key
    and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                        device_cert_der,
                                        device_cert_der_len,
                                        NX_NULL,
                                        0, device_cert_key_der,
                                        device_cert_key_der_len,
                                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

        /* Check for errors and prepare response data
        (e.g. nx_packet_data_append). */

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

}

/* If not processing connections or received data, let the thread sleep. */
if(!connect_flag && !receive_flag)
{
    tx_thread_sleep(100);
}
    }

    /* Server processing is done, stop the server instance
    from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_server_start, nx_secure_dtls_server_delete,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_create.
- nx_secure_dtls_server_session_start, nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_session_start"></a>nx_secure_dtls_server_session_start

Inicie uma Sessão DTLS a partir de um Servidor DTLS Seguro NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_session_start(
                 NX_SECURE_DTLS_SESSION *session_ptr, UINT wait_option);

```

### <a name="description"></a>Description

Este serviço inicia uma sessão do DTLS Server executando o aperto de mão DTLS do lado do servidor quando um Cliente DTLS remoto se ligou ao servidor e solicitou uma ligação DTLS.

A Sessão DTLS é obtida na rotina de chamada connect_notify fornecida a nx_secure_dtls_server_create.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão DTLS obtida a partir de uma chamada de connect_notify do Servidor DTLS.
- **wait_option** ThreadX espera valor para usar para operações de rede.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Criação bem sucedida do servidor DTLS.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido passou.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Não poderia atribuir um pacote de aperto de mão DTLS (piscina vazia).
- **NX_SECURE_TLS_INVALID_PACKET** (0x104) Dados recevied que não eram um registo DTLS válido.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Um registo DTLS não foi devidamente hashed (erro de encriptação).
- **NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Falha de verificação de encriptação.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Recevied um alerta do hospedeiro remoto durante o aperto de mão DTLS.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) Recebeu uma mensagem não reconhecida durante o aperto de mão DTLS.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Recevied um registo DTLS com um comprimento inválido.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) Recebeu um ClientHello sem cifrasuites DTLS suportados.
- **NX_SECURE_TLS_BAD_COMPRESSION_METHOD** (0x118) Recevied a ClientHello com um método de compressão desconhecido.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Falha do aperto de mão genérico (não especificado), geralmente devido a problemas com o processamento de extensão.
- **NX_SECURE_TLS_UNSUPPORTED_FEATURE** (0x130) Uma funcionalidade que ainda não foi suportada foi invocada durante o aperto de mão DTLS.
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Foi encontrada uma cifrasuita desconhecida (indicava erro de criptografia interna).
- **NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) Recevied um registo DTLS com uma versão DTLS desajustada.
- **NX_SECURE_TLS_FINISHED_HASH_FAILURE** (0x115) Não conseguiu validar o haxixe do aperto de mão DTLS, a sessão é inválida.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Envio interno da UDP falhou.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
* DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT, NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len, NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                        NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                    &packet_pool, &send_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                                send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* Server processing is done,
    stop the server instance from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_server_start, nx_secure_dtls_server_delete,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send.
- nx_secure_dtls_server_session_create, nx_secure_dtls_server_session_stop.
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_start"></a>nx_secure_dtls_server_start

Inicie uma instância do Servidor DTLS Segura NetX a ouvir na porta UDP configurada

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_start(
                  NX_SECURE_DTLS_SERVER *server_ptr);

```

### <a name="description"></a>Description

Este serviço inicia um Servidor DTLS. Após a revolução da chamada, o servidor está ativo e começará a processar pedidos de entrada de clientes DTLS. A instância do servidor deve ter sido configurada com o *serviço nx_secure_dtls_server_create*.

> [!NOTE]
> Este serviço liga a porta UDP do Servidor DTLS interno à porta local configurada, pelo que a maioria dos problemas encontrados terão a ver com comunicações UDP e configuração de rede.

### <a name="parameters"></a>Parâmetros

- **server_ptr** Ponteiro para uma instância do Servidor DTLS previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Início bem sucedido do servidor.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido passou.
- **NX_NOT_ENABLED** (0x14) UDP não está ativado.
- **NX_NO_FREE_PORTS** (0x45) Não há portas UDP disponíveis.
- **NX_INVALID_PORT** (0x46) Porta UDP inválida.
- **NX_ALREADY_BOUND** (0x22) porta UDP já está vinculada.
- **NX_PORT_UNAVAILABLE** (0x23) porta UDP não disponível para utilização.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                        NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session, &packet_pool,
                &send_packet, NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
                (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);
        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_server_stop, nx_secure_dtls_server_create,
- nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,
- nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_stop"></a>nx_secure_dtls_server_stop

Pare uma instância ativa do Servidor DTLS do NetX Secure

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_stop(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Description

Este serviço impede que um Servidor DTLS ouça na porta UDP configurante e reinicie todas as sessões DTLS associadas, interrompendo quaisquer comunicações DTLS em curso.

### <a name="parameters"></a>Parâmetros

- **server_ptr** Ponteiro para uma instância ativa do Servidor DTLS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Paragem bem sucedida do servidor.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido passou.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* We have exited the processing loop, stop the server. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,
- nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_trusted_certificate_add"></a>nx_secure_dtls_server_trusted_certificate_add

Adicione um certificado ca fidedigno a um Servidor DTLS Seguro NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_trusted_certificate_add(
                                         NX_SECURE_DTLS_SERVER *server_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a>Description

Este serviço adiciona um certificado ca ou CA intermédio fidedigno a uma instância do Servidor DTLS e atribuído a todas as sessões internas do servidor DTLS. Isto só é necessário se a autenticação do certificado do cliente X.509 for ativada utilizando *nx_secure_dtls_server_x509_client_verify_configure*. O certificado adicional será usado para verificar os certificados do Cliente X.509.

O parâmetro cert_id é um identificador numérico, sem zero para o certificado. Isto permite que o certificado seja facilmente removido ou encontrado no caso de existirem vários certificados de identidade com o mesmo Nome Comum X.509 presente na loja do servidor DTLS. Consulte o Guia de Utilizador NetX Secure TLS para obter mais informações sobre os certificados de servidor X.509.

### <a name="parameters"></a>Parâmetros

- **server_ptr** Ponteiro para uma instância do Servidor DTLS previamente criada.
- **certificado** Ponteiro para uma estrutura de certificado X.509 previamente inicializada.
- **cert_id** Identificador único numérico não zero para este certificado neste servidor DTLS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Adição bem sucedida de certificado ao servidor DTLS.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido passou.
- **NX_INVALID_PARAMETERS** (0x4D) Foi aprovado um certificado de identificação de 0.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

*Consulte a referência para *nx_secure_dtls_server_create* para obter um exemplo mais completo.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0, NX_NULL,
                                            0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add trusted CA certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                            &trusted_ca_certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Process incoming requests and data. */
    }

}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send.
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_local_certificate_add,
- nx_secure_dtls_server_trusted_certificate_remove,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_trusted_certificate_remove"></a>nx_secure_dtls_server_trusted_certificate_remove

Remova um certificado ca fidedigno de um Servidor DTLS Seguro NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_server_trusted_certificate_remove(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *common_name,
                                UINT common_name_length,
                                UINT cert_id);

```

### <a name="description"></a>Description

Este serviço remove um certificado de CA fidedigno de uma instância do DTLS Server. Os certificados de CA fidedignos só são necessários para um Servidor DTLS para o qual a verificação do certificado de cliente X.509 foi ativada através da chamada *nx_secure_dtls_server_x509_client_verify_configure*.

O certificado a retirar pode ser identificado pelo seu Nome Comum X.509 ou pelo cert_id numérico que foi atribuído na chamada a *nx_secure_dtls_server_trusted_certificate_add*. O cert_id é utilizado apenas para identificar o certificado e é mantido pelo pedido. Se o nome comum for utilizado em vez do identificador de certificado numérico, o parâmetro cert_id deve ser definido para 0.

> [!NOTE]
> Remover um certificado enquanto um aperto de mão DTLS está a ser processado pode resultar em comportamento inesperado. O *serviço nx_secure_dtls_server_stop* deve ser chamado antes de retirar os certificados.

### <a name="parameters"></a>Parâmetros

- **server_ptr** Ponteiro para uma instância do Servidor DTLS previamente criada.
- **common_name** X.509 CommonName do certificado a remover. Se isto for usado, passe cert_id como zero.
- **common_name_length** Comprimento de common_name cordas em bytes.
- **cert_id** Identificador único numérico não zero para este certificado neste servidor DTLS. Se isto for utilizado, passe NX_NULL para o parâmetro common_name.


### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Remoção bem sucedida do certificado do servidor DTLS.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido passou.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Não foi encontrado nenhum certificado correspondente ao cert_id ou common_name no servidor DTLS.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                                    certificate_der_data,
                                                    sizeof(certificate_der_data),
                                                    NX_NULL, 0, NX_NULL, 0,
                                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                                       &trusted_ca_certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before removing a certificate. */
    Status = nx_secure_dtls_server_stop(&dtls_server);


/* At some point in the future we decide to remove the certificate we added. We can
       use the certificate identifier we passed into the call to
       nx_secure_dtls_trusted_certificate_add (value = 1); */
    status = nx_secure_dtls_server_trusted_certificate_remove(&dtls_server,
                                                          NX_NULL, 0, 1);

}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_trusted_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_x509_client_verify_configure"></a>nx_secure_dtls_server_x509_client_verify_configure

Configure um Servidor DTLS Seguro NetX para solicitar e verificar certificados de cliente

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_dtls_server_x509_client_verify_configure(
                           NX_SECURE_DTLS_SERVER *server_ptr,
                               UINT certs_per_session,
                               UCHAR *certs_buffer, ULONG buffer_size);

```

### <a name="description"></a>Description

Este serviço configura um Servidor DTLS para solicitar e verificar certificados de cliente DTLS. Esta função opcional é utilizada quando são desejados certificados X.509 para a autenticação do cliente em vez de outros mecanismos (por exemplo, uma Chave Pré-Partilhada).

> [!IMPORTANT]
> *Quando um Servidor DTLS estiver configurado para verificar os certificados de cliente que utilizam este serviço, pelo menos um certificado ca fidedigno deve ser adicionado ao servidor usando nx_secure_dtls_server_trusted_certificate_add ou o servidor rejeitará todas as ligações do cliente que chegam porque não poderá verificar os certificados do cliente contra a loja fidedigna.*

Ao ligar para este serviço, a instância do DTLS Server irá (uma vez iniciada) solicitar certificados de cliente como parte do aperto de mão DTLS. Assumindo que o cliente está devidamente configurado com um certificado de identidade (e cadeia de certificados associado quando aplicável), o DTLS Server requer que a memória seja alocado para processar os dados do certificado do cliente. Esta memória é passada como o *parâmetro certs_buffer.*

O certs_buffer deve ser dimensionado para acomodar a maior cadeia de certificados esperada de um cliente DTLS, *o que vezes o número de sessões de servidores DTLS*. O tampão é dividido entre as sessões disponíveis utilizando o parâmetro *certs_per_session* que representa o número máximo esperado de certificados numa cadeia de certificados do Cliente. O tampão também precisa de fornecer espaço para a estrutura de dados NX_SECURE_X509_CERT que é usada para analisar os dados do certificado.

O cálculo do tamanho adequado do tampão pode ser feito com a seguinte fórmula:

```C
buffer_size = (# of DTLS sessions in server) *
                (certs_per_session) *
                (    maximum expected certificate size +
                      sizeof(NX_SECURE_X509_CERT)    )

```

- O número de sessões de DTLS é determinado pelo tamanho do tampão de sessão passado para nx_secure_dtls_server_create.
- certs_per_session deve ser definido para o número máximo esperado de certificados em qualquer cadeia de certificados de cliente.
- O tamanho máximo esperado do certificado depende da aplicação, tamanhos-chave e outros fatores, mas 2KB é geralmente suficiente.

### <a name="parameters"></a>Parâmetros

- **server_ptr** Ponteiro para uma instância do Servidor DTLS previamente criada.
- **certs_per_session** Número de certificados a atribuir a cada sessão de servidor DTLS.
- **certs_buffer** Espaço tampão para dados de certificados de entrada.
- **buffer_size** Tamanho do tampão de certificado.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Configuração bem sucedida da verificação do cliente X.509.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido passou.
- **NX_INVALID_PARAMETERS** (0x4D) Loja de certificados inválida (caso DTLSserver não initilizada?).

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Configure number of sessions per server. */
#define DTLS_SERVER_SESSIONS 3

/* Define parameters for X.509 client verification. */
#define MAX_CERT_SIZE         (2000)       /* 2KB expected maximum certificate size. */
#define CERTS_PER_SESSION (3)            /* Assume maximum chain length of 3 certificates. */
#define CERT_BUFFER_SIZE     (DTLS_SERVER_SESSIONS * CERTS_PER_SESSION * \
 (MAX_CERT_SIZE + sizeof(NX_SECURE_X509_CERT))

/* Define our incoming certificate buffer. */
UCHAR client_certs_buffer[CERT_BUFFER_SIZE];

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                    certificate_der_data,
                                    sizeof(certificate_der_data),
                                    NX_NULL, 0,
                                    NX_NULL, 0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                                &trusted_ca_certificate, 1);

    /* Configure client X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_configure(&dtls_server,
        CERTS_PER_SESSION,
        client_certs_buffer,
        sizeof(client_certs_buffer));

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */
}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_server_x509_client_verify_disable,
- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_trusted_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_x509_client_verify_disable"></a>nx_secure_dtls_server_x509_client_verify_disable

Desativa a verificação do certificado X.509 do cliente para um Servidor DTLS Seguro NetX

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_dtls_server_x509_client_verify_disable(
                           NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Description

Este serviço desativa a verificação do certificado de cliente X.509 num Servidor DTLS. O serviço não tem efeito se a verificação do certificado do Cliente X.509 não estiver ativada.

> [!NOTE]
> A desativação da autenticação do cliente numa instância ativa do DTLS Server pode resultar num comportamento imprevisível. O serviço nx_secure_dtls_server_stop deve ser chamado antes de alterar o estado do servidor.

### <a name="parameters"></a>Parâmetros

- **server_ptr** Ponteiro para uma instância do Servidor DTLS previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Desativação bem sucedida da autenticação do cliente X.509.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido passou.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Configure number of sessions per server. */
#define DTLS_SERVER_SESSIONS 3

/* Define parameters for X.509 client verification. */
#define MAX_CERT_SIZE         (2000)       /* 2KB expected maximum certificate size. */
#define CERTS_PER_SESSION (3)            /* Assume maximum chain length of 3 certificates. */
#define CERT_BUFFER_SIZE     (DTLS_SERVER_SESSIONS * CERTS_PER_SESSION * \
 (MAX_CERT_SIZE + sizeof(NX_SECURE_X509_CERT))

/* Define our incoming certificate buffer. */
UCHAR client_certs_buffer[CERT_BUFFER_SIZE];

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                    certificate_der_data,
                        sizeof(certificate_der_data), NX_NULL, 0,
                        NX_NULL, 0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                            &trusted_ca_certificate, 1);

    /* Configure client X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_configure(&dtls_server,
        CERTS_PER_SESSION,
        client_certs_buffer,
        sizeof(client_certs_buffer));

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before changing state. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* Disable X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_disable(&dtls_server);

}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_server_x509_client_verify_configure,
- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_trusted_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_client_info_get"></a>nx_secure_dtls_session_client_info_get

Obtenha informações remotas do cliente a partir de uma sessão do DTLS Server

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_session_client_info_get(
                                    NX_SECURE_DTLS_SESSION *session_ptr,
                                    NXD_ADDRESS *client_ip_address,
                                    UINT *client_port, UINT *local_port);

```

### <a name="description"></a>Description

Este serviço devolve a informação de rede sobre um Cliente DTLS que está ligado a uma sessão particular do DTLS Server. A informação devolvida consiste no endereço IP do cliente remoto e na porta UDP, bem como na porta do servidor local à qual o cliente está ligado.

Em geral, a instância da sessão DTLS será a obtida na invocação de uma das rotinas de chamada de notificação DTLS (por exemplo, as chamadas connect_notify ou receive_notify transmitidas para nx_secure_dtls_server_create).

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma sessão de sessão de servidor DTLS ativa.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Eliminação bem sucedida do servidor.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido passou.
- **NX_INVALID_SOCKET** (0x13) A tomada UDP associada não é válida (sessão não inicializada?).
- **NX_NOT_CONNECTED** (0x38) tomada UDP não está ligada – a ligação do cliente caiu ou ainda não foi estabelecida.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array
   or list in case a new connection is
   attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
                                                            *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    NXD_ADDRESS client_ip;
    UINT client_port, server_port;

    /* Get DTLS client information which can be used in filtering or associating
       the DTLS session with application data (e.g. a session pointer table). */
    status = nx_secure_dtls_session_client_info_get(dtls_session, &client_ip,
   &client_port, &server_port);

    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                            LOCAL_SERVER_PORT,
                                            NX_IP_PERIODIC_RATE,
                                            dtls_server_session_buffer,
                                            sizeof(dtls_server_session_buffer),
                                            &tls_crypto_table,
                                            crypto_metadata_buffer,
                                            sizeof(crypto_metadata_buffer),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            dtls_server_connect_notify,
                                            dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);
        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_server_start, nx_secure_dtls_server_stop.
- nx_secure_dtls_server_create, nx_secure_dtls_server_delete,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send.
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_session_create"></a>nx_secure_dtls_session_create

Criar e configurar uma Sessão de DTLS Segura NetX

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_dtls_session_create(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        VOID *metadata_buffer, ULONG metadata_size,
                        UCHAR *packet_reassembly_buffer,
                        UINT packet_reassembly_buffer_size,
                        UINT certs_number,
                        UCHAR *remote_certificate_buffer,
                        ULONG remote_certificate_buffer_size));

```

### <a name="description"></a>Description

Este serviço cria e configura uma sessão DTLS. Geralmente, isto será usado para criar sessões de Cliente DTLS, uma vez que as sessões do DTLS Server são geridas com o mecanismo DTLS Server (ver *nx_secure_dtls_server_create),* mas pode haver casos em que uma aplicação precisa de criar uma única instância de sessão de Sessão DTLS Server autónoma, caso em que este serviço pode ser utilizado <sup>7</sup>.

Os parâmetros configuram a informação e a atribuição de memória necessárias para instantaneaizar uma sessão de DTLS. O parâmetro crypto_table é uma tabela TLS que contém todas as rotinas criptográficas necessárias para encriptação e autenticação TLS/DTLS. O metadata_buffer é utilizado para caclulações de encriptação (ver nx_secure_tls_metadata_size_calculate no Guia do Utilizador NetX Secure TLS), e o packet_reassembly_buffer é utilizado para remontar os dados do UDP num registo completo de DTLS para desencriptação.

Os certs_number e remote_certificate_buffer são necessários para os Clientes DTLS que precisam de espaço para armazenar e processar a cadeia de certificados DTLS Server. O tampão deve ser capaz de acomodar o tamanho máximo esperado da cadeia de certificados para qualquer servidor ao qual se conecte. O tampão é dividido pelo número de certificados esperados (certs_number parâmetro) e deve também ser suficientemente grande para deter uma estrutura NX_SECURE_X509_CERT por certificado. O tamanho do tampão pode ser determinado com a seguinte fórmula:

```C
remote_certificate_buffer_size = (certs_number) *
                 (maximum cert size + sizeof(NX_SECURE_X509_CERT))
```

- certs_number é o número máximo esperado de certificados na cadeia de certificados do servidor
- O tamanho máximo do certificado depende do tamanho das chaves utilizadas e das informações no certificado, mas 2KB é geralmente suficiente.

**7** A criação de sessões do DTLS Server com esta rotina não é recomendada e vem com algumas limitações. A principal questão é que a sessão não tratará graciosamente as ligações adicionais do cliente – uma vez que a UDP não tem ligação, um segundo cliente pode legalmente enviar dados para a porta UDP do servidor quando uma sessão anterior do DTLS ainda estiver ativa, o que faria com que a sessão do servidor terminasse com um erro.

### <a name="parameters"></a>Parâmetros

- **dtls_session** Ponteiro para uma estrutura de Sessão DTLS não iniializada.
- **crypto_table** Ponteiro para uma estrutura de tabela de encriptação TLS/DTLS utilizada para todas as operações criptográficas.
- **crypto_metadata_buffer** Espaço tampão para cálculos de operação criptográfica e informações do estado.
- **crypto_metadata_size** Tamanho do tampão de metadados.
- **packet_reassembly_buffer** Tampão usado pela DTLS para remontar dados de UDP em registos DTLS para desencriptação.
- **packet_reassembly_buffer_size** Tamanho do tampão de remontagem. Geralmente deve ser superior a 16KB, mas pode ser menor dependendo da aplicação.
- **certs_number** Número máximo esperado de certificados na cadeia de certificados do servidor remoto.
- **remote_certificate_buffer** Espaço tampão para dados de certificados de entrada.
- **remote_certificate_buffer_size** Tamanho do tampão de certificado.


### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Criação bem sucedida da sessão.
- **NX_PTR_ERROR** (0x07) Sessão inválida ou ponteiro tampão.
- **NX_INVALID_PARAMETERS** (0x4D) Não há espaço tampão suficiente para remontagem de pacotes, certificados ou criptografia.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len,
                                    NX_NULL, 0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
    &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                            &udp_socket, &server_ip,
                                            4443,
                                            NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session,
                                                &send_packet,
                                                &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session,
                                            &receive_packet,
                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_client_session_start,nx_secure_dtls_session_receive
- nx_secure_dtls_session_send

## <a name="nx_secure_dtls_session_delete"></a>nx_secure_dtls_session_delete

Liberte os recursos utilizados por uma Sessão DTLS NetX Secure

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_dtls_session_delete(
                        NX_SECURE_DTLS_SESSION *dtls_session);

```

### <a name="description"></a>Description

Este serviço elimina uma sessão DTLS, libertando todos os recursos que foram atribuídos quando foi criado.

### <a name="parameters"></a>Parâmetros

- **dtls_session** Ponteiro para uma estrutura de Sessão DTLS que foi inicializada anteriormente.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Supressão bem sucedida da sessão.
- **NX_PTR_ERROR** (0x07) Sessão inválida ou ponteiro tampão.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                        trusted_cert_der,
                                        trusted_cert_der_len,
                                        NX_NULL, 0, NX_NULL, 0,
                                        NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                                    &udp_socket,
                                                    &server_ip, 4443,
                                                    NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

        /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                &receive_packet,
                                                NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_end"></a>nx_secure_dtls_session_end

Desligue uma Sessão DTLS segura ativa da NetX

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_dtls_session_end(NX_SECURE_DTLS_SESSION *dtls_session,
                                UINT wait_option);

```

### <a name="description"></a>Description

Este serviço termina uma sessão DTLS ativa enviando um alerta TLS/DTLS CloseNotify para o anfitrião remoto. O endereço IP e a porta utilizados são os utilizados na chamada anterior para nx_secure_dtls_session_send.

### <a name="parameters"></a>Parâmetros

- **dtls_session** Ponteiro para uma estrutura de Sessão DTLS que foi inicializada anteriormente.
- **wait_option** ThreadX espera valor para usar para operações de rede.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Supressão bem sucedida da sessão.
- **NX_PTR_ERROR** (0x07) Sessão inválida ou ponteiro tampão.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Não podia atribuir pacotes para alerta CloseNotify.
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Erro interno provável – rotina criptográfica não reconhecida.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Envio subjacente da UDP falhou.
- **NX_IP_ADDRESS_ERROR** (0x21) Erro com endereço IP do anfitrião remoto.
- **NX_NOT_BOUND** (0x24) Tomada UDP subjacente não está ligada à porta.
- **NX_INVALID_PORT** (0x46) Porta UDP inválida.
- **NX_PORT_UNAVAILABLE** (0x23) porta UDP não disponível para utilização.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session,
                                                &send_packet,
                                                &server_ip, 4443);

    /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session,
                                        NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

    }

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_local_certificate_add"></a>nx_secure_dtls_session_local_certificate_add

Adicione um certificado de identidade local a uma Sessão de DTLS Segura NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_session_local_certificate_add(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            NX_SECURE_X509_CERT *certificate,
                            UINT cert_id);

```

### <a name="description"></a>Description

Este serviço adiciona um certificado de identidade local a uma instância de Sessão DTLS. Em geral, este serviço será utilizado quando uma sessão do Cliente DTLS necessitar de fornecer um certificado de identidade a um servidor remoto. Esta é uma configuração opcional para DTLS, pelo que um certificado não é geralmente necessário para clientes DTLS. Um certificado de identidade requer uma chave privada associada.

O parâmetro cert_id é um identificador numérico, sem zero para o certificado. Isto permite que o certificado seja facilmente removido ou encontrado no caso de existirem vários certificados de identidade com o mesmo Nome Comum X.509 presente na loja de certificados DTLS. Consulte o Guia de Utilizador NetX Secure TLS para obter mais informações sobre os certificados X.509.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão DTLS previamente criada.
- **certificado** Ponteiro para uma estrutura de certificado X.509 previamente inicializada.
- **cert_id** Identificador único numérico não zero para este certificado neste servidor DTLS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Adição bem sucedida de certificado à sessão DTLS.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido passou.
- **NX_INVALID_PARAMETERS** (0x4D) Foi aprovado um certificado de identificação de 0.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

*Consulte a referência para *nx_secure_dtls_session_create* para obter um exemplo mais completo.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data. Identity
certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

/* Create a TLS session for our socket. Ciphers and metadata defined
   elsewhere. See nx_secure_tls_session_create reference for more
   information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
{
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
}

/* Initialize our trusted certificate. See section “Importing X.509
   Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len,
                                    NX_NULL, 0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

/* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                              &certificate, 1);

    /* Initialize local server identity certificate with key and
    add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                        certificate_der_data,
                        sizeof(certificate_der_data),
                        NX_NULL, 0,
                        certificate_key_der_data,
                        sizeof(certificate_key_der_data),
                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                    &certificate, 1);

/* Set up IP address of remote host. */
server_ip.nxd_ip_version = NX_IP_VERSION_V4;
server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


/* Now we can start the DTLS session as normal. */
status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                    &udp_socket, &server_ip, 4443,
                                    NX_IP_PERIODIC_RATE);


    /* Process responses, etc…*/
}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive.
- nx_secure_dtls_session_send, nx_secure_dtls_session_start,
- nx_secure_dtls_session_local_certificate_remove,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_local_certificate_remove"></a>nx_secure_dtls_session_local_certificate_remove

Remova um certificado de identidade local de uma Sessão de DTLS Segura netX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_session_local_certificate_remove(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         UCHAR *common_name,
                                         UINT common_name_length, UINT cert_id);

```

### <a name="description"></a>Description

Este serviço remove um certificado de identidade local de uma instância de Sessão DTLS utilizando um número de identificação de certificado (atribuído quando o certificado foi adicionado com nx_secure_dtls_session_local_certificate_add) ou o campo X.509 CommonName.

Se o common_name for utilizado para corresponder ao certificado, o parâmetro cert_id deve ser definido para 0. Se cert_id for utilizado, common_name deve ser aprovado um valor de NX_NULL.

O parâmetro cert_id é um identificador numérico, sem zero para o certificado. Isto permite que o certificado seja facilmente removido ou encontrado no caso de existirem vários certificados de identidade com o mesmo Nome Comum X.509 presente na loja de certificados DTLS. Consulte o Guia de Utilizador NetX Secure TLS para obter mais informações sobre os certificados X.509.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão DTLS previamente criada.
- **common_name** Ponteiro para a corda CommonName para combinar.
- **common_name_length** Comprimento da corda common_name.
- **cert_id** Identificador único numérico não zero para este certificado neste servidor DTLS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Remoção bem sucedida do certificado da sessão DTLS.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido passou.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Não foi encontrado nenhum certificado correspondente ao cert_id ou common_name na sessão DTLS dada.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

*Consulte a referência para *nx_secure_dtls_session_create* para obter um exemplo mais completo.

```C

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data.
Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
        nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                            &certificate, 1);

        /* Initialize local server identity certificate with key
        and add to server. */
        status = nx_secure_x509_certificate_initialize(&certificate,
                                certificate_der_data,
                                sizeof(certificate_der_data),
                                NX_NULL, 0,
                                certificate_key_der_data,
                                sizeof(certificate_key_der_data),
                                NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

        /* Add local server identity certificate to DTLS server with ID of 1. */
        status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                            &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
        &udp_socket, &server_ip, 4443,
        NX_IP_PERIODIC_RATE);

        /* Process responses, etc…*/

    /* At some point in the future,
    we decide to remove the certificate using the ID of 1
    when it was added to the session. */
        status = nx_secure_dtls_session_local_certificate_remove(&client_dtls_session,
                                                                NX_NULL, 0, 1);
}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive.
- nx_secure_dtls_session_send, nx_secure_dtls_session_start,
- nx_secure_dtls_session_local_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_receive"></a>nx_secure_dtls_session_receive

Receba os dados da aplicação sobre uma Sessão de DTLS Segura NetX estabelecida

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_dtls_session_receive(
                                NX_SECURE_DTLS_SESSION *dtls_session,
                                NX_PACKET **packet_ptr_ptr,
                                UINT wait_option);

```

### <a name="description"></a>Description

Este serviço devolve os dados da aplicação recebidos por uma Sessão DTLS ativa. A Sessão DTLS pode ser uma sessão de Servidor DTLS (gerida por uma instância do DTLS Server) ou uma sessão de Cliente DTLS. O pacote devolvido pode ser processado utilizando qualquer um dos serviços NX_PACKET API (consulte a documentação NetX para obter mais informações).

### <a name="parameters"></a>Parâmetros

- **dtls_session** Ponteiro para uma estrutura de Sessão DTLS que foi inicializada anteriormente.
- **packet_ptr_ptr** Ponteiro para um ponteiro NX_PACKET para o pacote de devolução.
- **wait_option** ThreadX espera valor para usar para operações de rede.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Recebimento bem sucedido do pacote de dados da aplicação.
- **NX_PTR_ERROR** (0x07) Sessão inválida ou ponteiro do pacote.
- **NX_NOT_ENABLED** UDP (0x14) não está ativado.
- **NX_NOT_BOUND** (0x24) tomada UDP não está ligada à porta.
- **NX_SECURE_TLS_INVALID_PACKET** (0x104) Dados recevied que não eram um registo DTLS válido.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Um registo DTLS não foi devidamente hashed (erro de encriptação).
- **NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Falha de verificação de encriptação.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Recevied um alerta do hospedeiro remoto.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE**    (0x102) recebeu uma mensagem não reconhecida.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Recevied um registo DTLS com um comprimento inválido.
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Foi encontrada uma cifrasuita desconhecida (indica erro de criptografia interna).
- **NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) Recevied um registo DTLS com uma versão DTLS desajustada.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session, &receive_packet,
                                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session, NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_end,
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_reset"></a>nx_secure_dtls_session_reset

Dados claros numa instância de Sessão DTLS Segura netX

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_dtls_session_reset(NX_SECURE_DTLS_SESSION *dtls_session);
```

### <a name="description"></a>Description

Este serviço reinicia uma sessão de DTLS, limpando todos os dados criptográficos efémeros e permitindo que a estrutura seja reutilizada para uma nova sessão. Os dados persistentes (por exemplo, lojas de certificados) são mantidos de modo a que nx_secure_dtls_session_create não seja chamado repetidamente.

### <a name="parameters"></a>Parâmetros

- **dtls_session** Ponteiro para uma estrutura de Sessão DTLS que foi inicializada anteriormente.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Reinicie bem a sessão.
- **NX_PTR_ERROR** (0x07) Sessão inválida ou ponteiro tampão.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_reset(&client_dtls_session);

    /* A new session can now be started using the same structure. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,



    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_-session_send"></a>nx_secure_dtls_ session_send

Enviar dados sobre uma sessão de DTLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_session_send(NX_SECURE_DTLS_SESSION *session_ptr,
                                          NX_PACKET *packet_ptr,
                                          NXD_ADDRESS *ip_address, UINT port);

```

### <a name="description"></a>Description

Este serviço envia um pacote de dados sobre uma Sessão DTLS estabelecida para um anfitrião DTLS remoto no endereço IP e porta dado. A sessão utilizada é uma sessão ativa do Cliente DTLS. Note que o endereço IP e a porta são fornecidos devido à natureza apátrida da UDP, mas geralmente devem corresponder ao endereço e porto utilizados para iniciar a sessão em nx_secure_dtls_session_start.

Os dados fornecidos no pacote, que deve ser atribuído com *nx_secure_dtls_packet_allocate,* são encriptados utilizando os parâmetros e rotinas criptográficos da sessão DTLS e depois enviados ao anfitrião remoto através da tomada UDP da Sessão DTLS.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de sessão de clientes DTLS ativa.
- **packet_ptr** Ponteiro para uma NX_PACKET instância atribuída anteriormente e povoada com dados de aplicação.
- **ip_address** Ponteiro para uma estrutura NXD_ADDRESS que contém o endereço IP do anfitrião remoto.
- **porto** Porta UDP no hospedeiro remoto.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Envio bem sucedido do pacote.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido passou.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Ocorreu um erro na operação de envio da UDP subjacente.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
    /* Error! */
    return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

        /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_create

## <a name="nx_secure_dtls_session_trusted_certificate_add"></a>nx_secure_dtls_session_trusted_certificate_add

Adicione um certificado ca fidedigno a uma Sessão de DTLS NetX Secure

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_session_trusted_certificate_add(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a>Description

Este serviço adiciona um certificado CA ou CA X.509 intermédio fidedigno a uma instância de Sessão DTLS. Um Cliente DTLS requer pelo menos um certificado fidedigno para validar certificados de servidor remoto, a menos que seja utilizado um mecanismo alternativo de autenticação (por exemplo, Chaves Pré-Partilhadas). Um certificado de confiança não costuma ter uma chave privada.

O parâmetro cert_id é um identificador numérico, sem zero para o certificado. Isto permite que o certificado seja facilmente removido ou encontrado no caso de existirem vários certificados de identidade com o mesmo Nome Comum X.509 presente na loja de certificados DTLS. Consulte o Guia de Utilizador NetX Secure TLS para obter mais informações sobre os certificados X.509.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão DTLS previamente criada.
- **certificado** Ponteiro para uma estrutura de certificado X.509 previamente inicializada.
- **cert_id** Identificador único numérico não zero para este certificado neste servidor DTLS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Adição bem sucedida de certificado à sessão DTLS.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido passou.
- **NX_INVALID_PARAMETERS** (0x4D) Foi aprovado um certificado de identificação de 0.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

*Consulte a referência para *nx_secure_dtls_session_create* para obter um exemplo mais completo.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data.
Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
   Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                            trusted_cert_der,
                                            trusted_cert_der_len,
                                            NX_NULL, 0, NX_NULL, 0,
                                            NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the trusted store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                      &certificate, 1);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0,
                                            certificate_key_der_data,
                                            sizeof(certificate_key_der_data),
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);

    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
         &udp_socket, &server_ip, 4443,
         NX_IP_PERIODIC_RATE);


    /* Process responses, etc…*/
}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive.
- nx_secure_dtls_session_send, nx_secure_dtls_session_start,
- nx_secure_dtls_session_trusted_certificate_remove,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_trusted_certificate_remove"></a>nx_secure_dtls_session_trusted_certificate_remove

Remova um certificado de CA fidedigno de uma Sessão de DTLS NetX Secure

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_dtls_session_trusted_certificate_remove(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *common_name,
                            UINT common_name_length, UINT cert_id);

```

### <a name="description"></a>Description

Este serviço remove um certificado de CA fidedigno de uma instância DTLS Session utilizando um número de identificação de certificado (atribuído quando o certificado foi adicionado com nx_secure_dtls_session_trusted_certificate_add) ou o campo X.509 CommonName.

Se o common_name for utilizado para corresponder ao certificado, o parâmetro cert_id deve ser definido para 0. Se cert_id for utilizado, common_name deve ser aprovado um valor de NX_NULL.

O parâmetro cert_id é um identificador numérico, sem zero para o certificado. Isto permite que o certificado seja facilmente removido ou encontrado no caso de existirem vários certificados de identidade com o mesmo Nome Comum X.509 presente na loja de certificados DTLS. Consulte o Guia de Utilizador NetX Secure TLS para obter mais informações sobre os certificados X.509.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão DTLS previamente criada.
- **common_name** Ponteiro para a corda CommonName para combinar.
- **common_name_length** Comprimento da corda common_name.
- **cert_id** Identificador único numérico não zero para este certificado neste servidor DTLS.


### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Remoção bem sucedida do certificado da sessão DTLS.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido passou.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Não foi encontrado nenhum certificado correspondente ao cert_id ou common_name na sessão DTLS dada.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

*Consulte a referência para *nx_secure_dtls_session_create* para obter um exemplo mais completo.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data. Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL, 0,
                                    NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
        nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                            &certificate, 1);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0,
                                            certificate_key_der_data,
                                            sizeof(certificate_key_der_data),
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    /* Process responses, etc…*/

    /* At some point in the future,
    we decide to remove the certificate using the ID of 1
    when it was added to the session. */
    status = nx_secure_dtls_session_trusted_certificate_remove(&client_dtls_session,
                                                                    NX_NULL, 0, 1);
}

```

### <a name="see-also"></a>Consulte também

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive.
- nx_secure_dtls_session_send, nx_secure_dtls_session_start,
- nx_secure_dtls_session_trusted_certificate_add,
- nx_secure_x509_certificate_initialize
