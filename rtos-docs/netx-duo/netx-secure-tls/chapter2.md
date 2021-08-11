---
title: Capítulo 2 - Instalação e utilização do Azure RTOS NetX Secure
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente NetX Secure.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d11e50b2ab74ee147f682567d142768de6108fc18264e9d8bc69bbfc8a32cc0a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801874"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-secure"></a>Capítulo 2 - Instalação e utilização do Azure RTOS NetX Secure

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NetX Secure.

## <a name="product-version-number"></a>Número da versão do produto

O utilizador pode verificar o número da versão do produto encontrando os seguintes símbolos em nx_secure_tls.h:

***NETX_SECURE_MAJOR_VERSION***

***NETX_SECURE_MINOR_VERSION***

As versões do Pacote de Serviço têm o seguinte símbolo definido para indicar o número do pacote de serviço:

***NETX_SECURE_SERVICE_PACK_VERSION***

## <a name="product-distribution"></a>Distribuição de Produtos

NetX Secure está disponível em [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) . O pacote inclui ficheiros de origem, inclui ficheiros e um ficheiro PDF que contém este documento, da seguinte forma:

- **nx_secure_tls_api.h** Arquivo de cabeçalho API público para NetX Secure TLS
- **nx_secure_tls_user.h** Utilizador define ficheiro de cabeçalho para NetX Secure TLS
- **nx_secure_tls_port.h** Definições específicas da plataforma para o NetX Secure
- **nx_secure_tls.h** Ficheiro de cabeçalho para NetX Secure TLS
- **nx_secure_tls&#42;.c/h** Ficheiros de origem C/H para NetX Secure TLS
- **nx_crypto&#42;.c/h** Ficheiros de origem C/H para a criptografia segura netX
- **nx_secure_x509&#42;.c/h** C/H Ficheiros de origem para certificados digitais X.509.
- **demo_netx_secure_tls.c** Ficheiro C Fonte para demo de TLS Despromo De tLS Do NetX
- **NetX_Secure_User_Guide.pdf** Descrição em PDF do produto NetX Secure

> [!NOTE]
> Os ficheiros nx_crypto* são fornecidos para diferentes plataformas de hardware numa subdiretória do diretório principal NetX Secure.

## <a name="netx-secure-installation"></a>Instalação NetX Secure

Para utilizar o NetX Secure, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo nível de diretório onde o NetX está instalado. Por exemplo, se o NetX for instalado no diretório "*\threadx\arm7\NetX*" então o *nx_secure**.* os diretórios devem ser copiados em "*\threadx\arm7\NetXSecure*".

## <a name="using-netx-secure"></a>Usando o NetX Secure

A utilização do NetX Secure TLS é simples. Basicamente, o código de aplicação deve incluir *nx_secure_tls_api.h* depois de incluir *tx_api.h* e *nx_api.h,* para utilizar o ThreadX e o NetX. Uma vez *incluído nx_secure_tls_api.h,* o código de aplicação é então capaz de fazer as chamadas de função NetX Secure especificadas mais tarde neste guia. O pedido deve igualmente importar o *nx_secure**.* ficheiros numa biblioteca NetXSecure e a plataforma específica *nx_crypto**.* ficheiros numa biblioteca NetXCrypto.

## <a name="small-example-system-tls-client"></a>Sistema de pequenos exemplos (cliente TLS)

Um exemplo de como é fácil utilizar o NetX Secure é descrito na Figura 1.1, que aparece abaixo. Isto demonstra um cliente TLS simples, utilizando módulos de cripto de software (não específicos de hardware) para encriptação. Foi concebido para funcionar com o servidor openSSL de eco inverso (abrir s_server -rev).

Note que para executar este exemplo, necessitará de um certificado X.509 CA para autenticar o certificado do seu servidor alvo. Para o exemplo OpenSSL, bastará um PKI simples de 2 níveis (certificado de servidor de > >de certificado CA raiz). Terá de preencher o conjunto "trusted_ca_data" com uma versão binária codificada pelo DER do certificado de CA e atualizar a variável "trusted_ca_length" para refletir o comprimento real do seu certificado.

Também necessitará do controlador de rede para o seu hardware (substitua o parâmetro "nx_driver_xx" na nx_ip_create chamada).

```C
#include "tx_api.h"
#include "nx_api.h"
#include "nx_secure_tls_api.h"
#include "nx_secure_x509.h"

/* Define the size of our application stack. */
#define     DEMO_STACK_SIZE             4096

/* Define the remote server IP address using NetX IP_ADDRESS macro. */
#define     REMOTE_SERVER_IP_ADDRESS    IP_ADDRESS(192, 168, 1, 1)

/* Define the IP address for this device. */
#define     DEVICE_IP_ADDRESS           IP_ADDRESS(192, 168, 1, 2)

/* Define the remote server port. 443 is the HTTPS default. */
#define     REMOTE_SERVER_PORT          443

/* Define the ThreadX and NetX object control blocks...  */

NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Define an HTTP request to be sent to the HTTPS web server not defined here but
  represented by the ellipsis. */
UCHAR http_request[] = { "GET /example.html HTTP/1.1"  };

/* Define the IP thread's stack area.  */
ULONG ip_thread_stack[3 * 1024 / sizeof(ULONG)];

/* Define packet pool for the demonstration.  */
#define NX_PACKET_POOL_SIZE ((1536 + sizeof(NX_PACKET)) * 32)

ULONG packet_pool_area[NX_PACKET_POOL_SIZE/sizeof(ULONG) + 64 / sizeof(ULONG)];

/* Define the ARP cache area.  */
ULONG arp_space_area[512 / sizeof(ULONG)];

/* Define the TLS Client thread.  */
ULONG             tls_client_thread_stack[6 * 1024 / sizeof(ULONG)];
TX_THREAD         tls_client_thread;
void              client_thread_entry(ULONG thread_input);

/* Define the TLS packet reassembly buffer. */
UCHAR tls_packet_buffer[18000];

/* Define the metadata area for TLS cryptography. The actual size needed can be
   Ascertained by calling nx_secure_tls_metadata_size_calculate.
*/
UCHAR tls_crypto_metadata[18000];

/* Pointer to the TLS ciphersuite table that is included in the platform-specific
   cryptography subdirectory. The table maps the cryptographic routines for the
   platform to function pointers usable by the TLS library.
*/
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers_ecc;
extern const USHORT nx_crypto_ecc_supported_groups[];
extern const NX_CRYPTO_METHOD *nx_crypto_ecc_curves[];
extern const UINT nx_crypto_ecc_supported_groups_size;

/* Binary data for the TLS Client X.509 trusted root CA certificate, ASN.1 DER-
   encoded. A trusted certificate must be provided for TLS Client applications
   (unless X.509 authentication is disabled) or TLS will treat all certificates as
   untrusted and the handshake will fail.
*/

/* DER-encoded binary certificate, not defined here but represented by the ellipsis,
   for the sake of brevity. */
const UCHAR trusted_ca_data[] = { … };
const UINT trusted_ca_length = 0x574;

/* Define the application – initialize drivers and TCP/IP setup.
   NOTE: the variable “status” should be checked after every API call. Most error
         checking has been omitted for clarity. */
void    tx_application_define(void *first_unused_memory)
{
UINT  status;

   /* Initialize the NetX system.  */
   nx_system_initialize();

   /* Create a packet pool. Check status for errors. */
   status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1536,
                                   (ULONG*)(((int)packet_pool_area + 64) & ~63) ,
                                   NX_PACKET_POOL_SIZE);

   /* Create an IP instance for the specific target. Check status for errors. This
      call is not completely defined. Please see other demo files for proper usage
      of the nx_ip_create call. */
   status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                         DEVICE_IP_ADDRESS ,
                         0xFFFFFF00UL,
                         &pool_0, nx_driver_xx,
                         (UCHAR*)ip_thread_stack,
                         sizeof(ip_thread_stack),
                         1);

   /* Enable ARP and supply ARP cache memory for IP Instance 0. Check status for
       errors. */
   status =  nx_arp_enable(&ip_0, (void *)arp_space_area, sizeof(arp_space_area));

   /* Enable TCP traffic. Check status for errors. */
   status =  nx_tcp_enable(&ip_0);

   status =  nx_ip_fragment_enable(&ip_0);

   /* Initialize the NetX Secure TLS system.  */
   nx_secure_tls_initialize();

    /* Create the TLS client thread to start handling incoming requests. */
   tx_thread_create(&tls_client_thread, "TLS Client thread", client_thread_entry, 0,
                     tls_client_thread_stack, sizeof(tls_client_thread_stack),
                     16, 16, 4, TX_AUTO_START);
   return;
}

/* Thread to handle the TLS Client instance. */
void client_thread_entry(ULONG thread_input)
{
UINT       status;
ULONG       actual_status;
NX_PACKET *send_packet;
NX_PACKET *receive_packet;
UCHAR receive_buffer[100];
ULONG bytes;
ULONG server_ipv4_address;

    /* We are not using the thread input parameter so suppress compiler warning. */
    NX_PARAMETER_NOT_USED(thread_input);

   /* Ensure the IP instance has been initialized.  */
   status =  nx_ip_status_check(&ip_0, NX_IP_INITIALIZE_DONE, &actual_status,
                                 NX_IP_PERIODIC_RATE);

   /* Create a TCP socket to use for our TLS session.  */
   status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Client Socket",
                                  NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                                  NX_IP_TIME_TO_LIVE, 8192, NX_NULL, NX_NULL);

   /* Create a TLS session for our socket. This sets up the TLS session object for
          later use */
   status =  nx_secure_tls_session_create(&tls_session,
                                          &nx_crypto_tls_ciphers_ecc,
                                          tls_crypto_metadata,
                                          sizeof(tls_crypto_metadata));

   /* Initialize ECC parameters for this session. */
   status = nx_secure_tls_ecc_initialize(&tls_session,
                                             nx_crypto_ecc_supported_groups,
                                             nx_crypto_ecc_supported_groups_size,
                                             nx_crypto_ecc_curves);

   /* Set the packet reassembly buffer for this TLS session. */
   status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                    sizeof(tls_packet_buffer));

   /* Initialize an X.509 certificate with our CA root certificate data. */
   nx_secure_x509_certificate_initialize(&certificate, trusted_ca_data,
                                         trusted_ca_length, NX_NULL, 0, NX_NULL, 0,
                                         NX_SECURE_X509_KEY_TYPE_NONE);

   /* Add the initialized certificate as a trusted root certificate. */
   nx_secure_tls_trusted_certificate_add(&tls_session, &certificate);

   /* Setup this thread to open a connection on the TCP socket to a remote server.
      The IP address can be used directly or it can be obtained via DNS or other
      means.*/
   server_ipv4_address = REMOTE_SERVER_IP_ADDRESS;
   status = nx_tcp_client_socket_connect(&tcp_socket, server_ipv4_address,
                                         REMOTE_SERVER_PORT, NX_WAIT_FOREVER);

   /* Start the TLS Session using the connected TCP socket. This function will
      ascertain from the TCP socket state that this is a TLS Client session. */
   status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                         NX_WAIT_FOREVER);

    /* Allocate a TLS packet to send an HTTP request over TLS (HTTPS). */
    status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                          NX_WAIT_FOREVER);

    /* Populate the packet with our HTTP request. */
    nx_packet_data_append(send_packet, http_request, sizeof(http_request), &pool_0,
                          NX_WAIT_FOREVER);


   /* Send the HTTP request over the TLS Session, turning it into HTTPS. */
   status = nx_secure_tls_session_send(&tls_session, send_packet, NX_WAIT_FOREVER);

   /* If the send fails, you must release the packet.  */
   if (status != NX_SUCCESS)
   {
         /* Release the packet since the packet was not sent.  */
         nx_packet_release(send_packet);
   }

   /* Receive the HTTP response and any data from the server. */
   status = nx_secure_tls_session_receive(&tls_session, &receive_packet,
   NX_WAIT_FOREVER);
   if (status == NX_SUCCESS)
   {
       /* Extract the data we received from the remote server. */
       status = nx_packet_data_extract_offset(receive_packet, 0, receive_buffer,
                                             100,  &bytes);
        /* Display the response data. */
       receive_buffer[bytes] = 0;
       printf("Received data: %s\n", receive_buffer);

        /* Release the packet when done with it. */
       nx_packet_release(receive_packet);
   }

   /* End the TLS session now that we have received our HTTPS/HTML response. */
   status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

   /* Check for errors to make sure the session ended cleanly. */

   /* Disconnect the TCP socket. */
   status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

}
```

**Figura 1.1 Exemplo de utilização do NetX Secure com NetX**

## <a name="small-example-system-tls-web-server"></a>Sistema de pequenos exemplos (servidor web TLS)

Um exemplo de como é fácil utilizar o NetX Secure é descrito na Figura 1.1, que aparece abaixo e demonstra um simples Servidor Web TLS (HTTPS).

Note que para executar este exemplo, você precisará de um certificado X.509 para identificar o seu servidor para clientes TLS. Para a maioria dos browers web, um certificado auto-assinado simples deve ser suficiente. O seu navegador irá queixar-se de não ser capaz de autenticar o servidor e, em alguns casos, poderá não conseguir estabelecer uma ligação TLS/HTTPS ao seu servidor<sup>3</sup>. Terá de preencher o conjunto "certificate_data" com uma versão binária codificada pelo DER do certificado do servidor e atualizar a variável "certificate_length" para refletir o comprimento real do seu certificado. Também precisa de preencher o conjunto "private_key" com uma versão codificada de DER da chave privada do certificado, formatada com recurso a PKCS#1 para a chave RSA e RFC 5915 para chaves ECC. Preencha a variável "private_key_length" com o comprimento real dos seus dados-chave.

> [!IMPORTANT]
> Alguns navegadores (particularmente algumas versões do navegador Chrome) podem rejeitar certificados auto-assinados. Neste caso, pode criar um PKI de 2 níveis com um certificado de CA raiz que é usado para assinar o certificado do servidor. Nesta situação, o certificado de CA raiz é instalado como um certificado de raiz fidedigno no seu navegador. !!! IMPORTANTE – remova o certificado de CA raiz do seu navegador quando estiver pronto e não o utilize para quaisquer aplicações de produção !!!

Também necessitará do controlador de rede para o seu hardware (substitua o parâmetro "nx_driver_xx" na nx_ip_create chamada).

```C
#include "tx_api.h"
#include "nx_api.h"
#include "nx_secure_tls_api.h"
#include "nx_secure_x509.h"

#define     DEMO_STACK_SIZE         4096

/* Define the IP address for this device. */
#define     DEVICE_IP_ADDRESS             IP_ADDRESS(192, 168, 1, 2)

/* Define the ThreadX and NetX object control blocks...  */

NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Define the IP thread's stack area.  */
ULONG ip_thread_stack[3 * 1024 / sizeof(ULONG)];

/* Define packet pool for the demonstration.  */
#define NX_PACKET_POOL_SIZE ((1536 + sizeof(NX_PACKET)) * 32)

ULONG packet_pool_area[NX_PACKET_POOL_SIZE/sizeof(ULONG) + 64 / sizeof(ULONG)];

/* Define the ARP cache area.  */
ULONG arp_space_area[512 / sizeof(ULONG)];


/* Define the TLS Server thread.  */
ULONG             tls_server_thread_stack[6 * 1024 / sizeof(ULONG)];
TX_THREAD         tls_server_thread;
void              server_thread_entry(ULONG thread_input);

/* Define the TLS packet reassembly buffer. */
UCHAR tls_packet_buffer[18000];

/* Define the metadata area for TLS cryptography. The actual size needed can be
   Ascertained by calling nx_secure_tls_metadata_size_calculate.
*/
UCHAR tls_crypto_metadata[18000];

/* Pointer to the TLS ciphersuite table that is included in the platform-specific
   cryptography subdirectory. The table maps the cryptographic routines for the
   platform to function pointers usable by the TLS library.
*/
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers_ecc;
extern const USHORT nx_crypto_ecc_supported_groups[];
extern const NX_CRYPTO_METHOD *nx_crypto_ecc_curves[];
extern const UINT nx_crypto_ecc_supported_groups_size;

/* Binary data for the TLS Server X.509 certificate, ASN.1 DER-encoded. Note that the
   certificate data and private key data is represented by an ellipsis for the sake
   of brevity.
*/
const UCHAR certificate_data[] = { … }; /* DER-encoded binary certificate. */
const UINT certificate_length = 0x574;

/* Binary data for the TLS Server Private Key, from private key
   file generated at the time of the X.509 certificate creation. ASN.1 DER-encoded. */
const UCHAR private_key[] = { … }; /* DER-encoded private key file (PKCS#1 RSA or ECC) */
const UINT private_key_length = 0x40;

/* Define some HTML data (web page) with an HTTPS header to serve to connecting
   clients. */
UCHAR html_data[] = { "HTTP/1.1 200 OK\r\n" \
        "Date: Tue, 19 May 2020 23:59:59 GMT\r\n" \
        "Content-Type: text/html\r\n" \
        "Content-Length: 200\r\n\r\n" \
        "<html>\r\n"\
        "<body>\r\n"\
        "<b>Hello NetX Secure User!</b>\r\n"\
        "This is a simple webpage\r\n"\
        "served up using NetX Secure!\r\n"\
        "</body>\r\n"\
        "</html>\r\n" };

/* Define the application – initialize drivers and TCP/IP setup.  */
void    tx_application_define(void *first_unused_memory)
{
UINT  status;


    /* Initialize the NetX system.  */
    nx_system_initialize();

    /* Create a packet pool. Check status for errors. */
    status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1536,
                                    (ULONG*)(((int)packet_pool_area + 64) & ~63) ,
                                    NX_PACKET_POOL_SIZE);

    /* Create an IP instance for the specific target. Check status for errors. */
    status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                          DEVICE_IP_ADDRESS,
                          0xFFFFFF00UL,
                          &pool_0, nx_driver_xx,
                          (UCHAR*)ip_thread_stack,
                          sizeof(ip_thread_stack),
                          1);

    /* Enable ARP and supply ARP cache memory for IP Instance 0. Check status for
         errors. */
    status =  nx_arp_enable(&ip_0, (void *)arp_space_area, sizeof(arp_space_area));

    /* Enable TCP traffic. Check status for errors. */
    status =  nx_tcp_enable(&ip_0);

    status =  nx_ip_fragment_enable(&ip_0);

    /* Initialize the NetX Secure TLS system.  */
    nx_secure_tls_initialize();

    /* Create the TLS server thread to start handling incoming requests. */
    tx_thread_create(&tls_server_thread, "TLS Server thread", server_thread_entry, 0,
                   tls_server_thread_stack, sizeof(tls_server_thread_stack),
                   16, 16, 4, TX_AUTO_START);
    return;
}

/* Thread to handle the TLS Server instance. */
void server_thread_entry(ULONG thread_input)
{
UINT       status;
ULONG      actual_status;
NX_PACKET *send_packet;
NX_PACKET *receive_packet;
UCHAR receive_buffer[100];
ULONG bytes;

    NX_PARAMETER_NOT_USED(thread_input);

    /* Ensure the IP instance has been initialized.  */
    status =  nx_ip_status_check(&ip_0, NX_IP_INITIALIZE_DONE, &actual_status,
                                 NX_IP_PERIODIC_RATE);

    /* Create a TCP socket to use for our TLS session.  */
    status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Server Socket",
                                   NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                                   NX_IP_TIME_TO_LIVE, 8192, NX_NULL, NX_NULL);

    /* Create a TLS session for our socket.  */
    status =  nx_secure_tls_session_create(&tls_session,
                                        &nx_crypto_tls_ciphers_ecc,
                                        tls_crypto_metadata,
                                        sizeof(tls_crypto_metadata));

    status = nx_secure_tls_ecc_initialize(&tls_session,
                                          nx_crypto_ecc_supported_groups,
                                          nx_crypto_ecc_supported_groups_size,
                                          nx_crypto_ecc_curves);

     /* Set the packet reassembly buffer for this TLS session. */
     status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                      sizeof(tls_packet_buffer));

    /* Initialize an X.509 certificate and private ECC key for our TLS Session. */
    nx_secure_x509_certificate_initialize(&certificate, certificate_data, NX_NULL, 0,
                                          certificate_length, private_key,
                                          private_key_length,
                                          NX_SECURE_X509_KEY_TYPE_EC_DER);

    /* Add the initialized certificate as a local identity certificate. */
    nx_secure_tls_local_certificate_add(&tls_session, &certificate);


    /* Setup this thread to listen on the TCP socket.
       Port 443 is standard for HTTPS. */
    status =  nx_tcp_server_socket_listen(&ip_0, 443, &tcp_socket, 5, NX_NULL);

    while(1)
     {
         /* Accept a client TCP socket connection.  */
         status =  nx_tcp_server_socket_accept(&tcp_socket, NX_WAIT_FOREVER);

         /* Start the TLS Session using the connected TCP socket. */
         status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                              NX_WAIT_FOREVER);

         /* Receive the HTTPS request. */
         status = nx_secure_tls_session_receive(&tls_session, &receive_packet,
                                                NX_WAIT_FOREVER);

if (status == NX_SUCCESS)
      {
         /* Extract the HTTP request information from the HTTPS request. */
            status = nx_packet_data_extract_offset(receive_packet, 0, receive_buffer,
                                                  100, &bytes);
         /* Display the HTTP request data. */
            receive_buffer[bytes] = 0;
            printf("Received data: %s\n", receive_buffer);

         /* Release the packet when done with it */
            nx_packet_release(receive_packet);
      }

         /* Allocate a TLS packet to send HTML data back to client. */
         status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                                NX_WAIT_FOREVER);

         /* Populate the packet with our HTTP response and HTML web page data. */
         nx_packet_data_append(send_packet, html_data, sizeof(html_data), &pool_0,
                               NX_WAIT_FOREVER);

         /* Send the HTTP response over the TLS Session, turning it into HTTPS. */
         status = nx_secure_tls_session_send(&tls_session, send_packet,
                                                 NX_WAIT_FOREVER);

         /* If the send fails, you must release the packet.  */
         if (status != NX_SUCCESS)
         {
              /* Release the packet since it was not sent.  */
              nx_packet_release(send_packet);
         }

         /* End the TLS session now that we have sent our HTTPS/HTML response. */
         status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

         /* Check for errors to make sure the session ended cleanly! */

         /* Disconnect the TCP socket so we can be ready for the next request. */
         status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

         /* Unaccept the server socket.  */
         status =  nx_tcp_server_socket_unaccept(&tcp_socket);

         /* Setup server socket for listening again.  */
         status =  nx_tcp_server_socket_relisten(&ip_0, 443, &tcp_socket);
     }
}
```

**Figura 1.2 Exemplo de utilização do NetX Secure com NetX**

## <a name="a-note-on-tls-session-error-recovery"></a>Uma nota sobre a recuperação de erros de sessão de TLS

Os sistemas de exemplo acima descritos mostram os contornos básicos para um Cliente e Servidor TLS, respectivamente, mas para maior clareza o tratamento de erros é omitido. No entanto, uma parte do sistema de segurança que o TLS fornece depende do manuseamento adequado das condições de erro. Geralmente, os problemas potenciais mais graves serão tratados dentro da própria pilha TLS, mas é importante que a aplicação TLS responda adequadamente e recupere de erros TLS que não são tratados dentro da implementação do TLS.

Para ilustrar a lógica necessária para o manuseamento adequado de erros, a seguinte função demonstra uma recolha típica de serviços API que podem ser utilizados para lidar adequadamente com erros de TLS e repor o estado TLS de forma limpa após a origem de uma condição de erro. Para além da secção em que se nota, a lógica aplica-se tanto às instâncias do TLS Client como do TLS Server.

Note que as chamadas mais importantes da API na função são para os serviços *nx_secure_tls_session_end*, que fecham de forma limpa a sessão TLS ou aperto de mão, e *nx_secure_tls_session_reset*, que limpa o estado da sessão TLS para que a tls_session instância da estrutura de controlo possa ser reutilizada para uma nova sessão de TLS. Note também que *nx_secure_tls_session_reset* não limpa o estado configurado pelo utilizador, como certificados ou buffers atribuídos, permitindo que a sessão seja reutilizada sem voltar a chamar *nx_secure_tls_session_create.* Para limpar completamente todo o estado da sessão TLS, o *serviço nx_secure_tls_session_delete* pode ser usado em vez disso.

```C
/* Define a helper function to clean up a broken TLS session (to be called on any
   error from nx_secure_tls_session_start onwards). Note that the variables
   tls_session, tcp_socket, and ip_0 are global in the above examples. */
VOID tls_session_error_cleanup(VOID)
{
UINT status;
UINT alert_level, alert_value;

      /* If we got an error back from a TLS API call, there may be an alert from the
         remote host. Extract the alert level and value to print out. Note that the TLS
         API will return NX_SECURE_TLS_ALERT_RECEIVED (0x114) if an alert was received.
         For other error codes the alert value and level are not valid. */
      status = nx_secure_tls_session_alert_value_get(&tls_session, &alert_level,
                                                     &alert_value);
      if(status)
      {
         printf("Pointer error in getting alert value.\n");
      }
      else
      {
         printf("Alert recieved. Value: %d, Level: %d\n", alert_value, alert_level);
      }

      /* End the TLS session. This is required to properly shut down the TLS
         connection. */
      status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

      /* If the session did not shut down cleanly, this is a possible security issue. */
      if (status)
      {
         printf("Error in TLS session end: %x\n", status);
      }

      /* Reset the TLS session to re-use the control structure for the next connection.
         This API service resets the TLS session state but does not remove user-
         configured options such as certificates, PSKs, buffers, and cipher routines. */
      nx_secure_tls_session_reset(&tls_session);

      /* Disconnect the TCP socket, closing the connection. */
      status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket close: %x\n", status);
      }

   /* The following code applies only to a TLS server instance. */
   #if NX_SECURE_TLS_SERVER
      /* Unaccept the server socket.  */
      status =  nx_tcp_server_socket_unaccept(&tcp_socket);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket unaccept: %x\n", status);
      }

      /* Setup server socket for listening again.  */
      status =  nx_tcp_server_socket_relisten(&ip_0, DEVICE_SERVER_PORT, &tcp_socket);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket relisten: %x\n", status);
      }
#endif
} /* End function. */
```

## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração para a construção do NetX Secure. Segue-se uma lista de todas as opções, onde cada uma é descrita em detalhe:

| Definir | Significado |
|----------------------|------------------------------------------------|
| **NX_SECURE_DISABLE_ERROR_CHECKING**                | Definida, esta opção remove a verificação básica de erros NetX Secure. É normalmente usado após a depurada aplicação. |
| **NX_CRYPTO_MAX_RSA_MODULUS_SIZE**                  | Definida, esta opção dá o módulo RSA máximo esperado, em bits. O valor predefinido é de 4096 para um módulo de 4096 bits. Outros valores podem ser 3072, 2048 ou 1024 (não recomendado). |
| **NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES**        | Definida, esta opção permite que o TLS aceite certificados auto-assinados de um anfitrião remoto. Por padrão, o TLS rejeitará certificados de servidor auto-assinados como precaução de segurança. Se esta macro for definida, os certificados auto-assinados devem ainda ser adicionados à loja de confiança para serem aceites. |
| **NX_SECURE_ENABLE_CLIENT_CERTIFICATE_VERIFY**      | Definida, esta opção permite a verificação opcional do Certificado de Cliente X.509 para servidores TLS<sup>4</sup>.  |
| **NX_SECURE_ENABLE_PSK_CIPHERSUITES**               | Definida, esta opção permite a funcionalidade de Chave Pré-Partilhada (PSK). Não desativa certificados digitais. |
| **NX_SECURE_TLS_CLIENT_DISABLED**                   | Definida, esta opção remove todo o código de pilha TLS relacionado com o modo TLS Client, reduzindo o código e o uso de dados. |
| **NX_SECURE_TLS_SERVER_DISABLED**                   | Definida, esta opção remove todo o código de pilha TLS relacionado com o modo TLS Server, reduzindo o código e a utilização de dados.  |
| **NX_SECURE_DISABLE_ECC_CIPHERSUITE**               | Definida, esta opção remove toda a lógica TLS para cifrasuites de criptografia da curva elíptica (ECC). Estes cifrasuites são opcionais em TLS 1.2 e mais cedo e desativá-los pode resultar numa redução significativa do código e do tamanho dos dados.|
| **NX_SECURE_TLS_ENABLE_TLS_1_3**                    | Definida, esta opção permite o modo TLSv1.3. TLS 1.3 é a versão mais recente do TLS e é desativada por padrão. |
| **NX_SECURE_TLS_ENABLE_TLS_1_0**                    | Definida, esta opção permite o modo TLSv1.0. O TLSv1.0 é considerado obsoleto, pelo que só deve ser ativado para retrocompatibilidade com aplicações mais antigas. |
| **NX_SECURE_TLS_ENABLE_TLS_1_1**                    | Definida, esta opção permite o modo TLSv1.1. O TLSv1.1 é considerado obsoleto, pelo que só deve ser ativado para retrocompatibilidade com aplicações mais antigas. |
| **NX_SECURE_TLS_DISABLE_TLS_1_1**                   | Definida, esta opção desativa o modo TLSv1.1. É definido por defeito. O TLSv1.1 é desativado a favor da utilização apenas do TLSv1.2<sup>5</sup>mais seguro .  |
| **NX_SECURE_X509_STRICT_NAME_COMPARE**              | Definida, esta opção permite uma estrita comparação de nomes distintos para certificados X.509 para pesquisa e verificação de certificados. O padrão é apenas comparar os campos de Nome Comum dos Nomes Distintos.|
| **NX_SECURE_X509_USE_EXTENDED_DISTINGUISHED_NAMES** | Definida, esta opção permite os campos de Nome Distinto X.509 opcionais, em detrimento do uso extra de memória para certificados X.509. |

4. Note que esta opção apenas permite que o código seja ligado à aplicação. A funcionalidade terá de ser ativada com o serviço API nx_secure_tls_session_client_verify_enable ou configurada utilizando nx_secure_tls_session_x509_client_verify_configure para utilizar a Verificação do Certificado do Cliente.

5. Note que também é possível desativar o TLSv1.2 se utilizar apenas TLS 1.0 ou TLS 1.1. No entanto, isto não é recomendado e não suportado diretamente.
