---
title: Capítulo 2 - Instalação e utilização do Azure RTOS NetX Secure
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente NetX Secure.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b3ef82bd113518b35105fb2eefe23bd3e755ca06
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826953"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-secure"></a><span data-ttu-id="074fd-103">Capítulo 2 - Instalação e utilização do Azure RTOS NetX Secure</span><span class="sxs-lookup"><span data-stu-id="074fd-103">Chapter 2 - Installation and use of Azure RTOS NetX Secure</span></span>

<span data-ttu-id="074fd-104">Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="074fd-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Secure component.</span></span>

## <a name="product-version-number"></a><span data-ttu-id="074fd-105">Número da versão do produto</span><span class="sxs-lookup"><span data-stu-id="074fd-105">Product Version Number</span></span>

<span data-ttu-id="074fd-106">O utilizador pode verificar o número da versão do produto encontrando os seguintes símbolos em nx_secure_tls.h:</span><span class="sxs-lookup"><span data-stu-id="074fd-106">User may verify the product version number by finding the following symbols in nx_secure_tls.h:</span></span>

<span data-ttu-id="074fd-107">***NETX_SECURE_MAJOR_VERSION***</span><span class="sxs-lookup"><span data-stu-id="074fd-107">***NETX_SECURE_MAJOR_VERSION***</span></span>

<span data-ttu-id="074fd-108">***NETX_SECURE_MINOR_VERSION***</span><span class="sxs-lookup"><span data-stu-id="074fd-108">***NETX_SECURE_MINOR_VERSION***</span></span>

<span data-ttu-id="074fd-109">As versões do Pacote de Serviço têm o seguinte símbolo definido para indicar o número do pacote de serviço:</span><span class="sxs-lookup"><span data-stu-id="074fd-109">Service Pack releases has the following symbol defined to indicate the service pack number:</span></span>

<span data-ttu-id="074fd-110">***NETX_SECURE_SERVICE_PACK_VERSION***</span><span class="sxs-lookup"><span data-stu-id="074fd-110">***NETX_SECURE_SERVICE_PACK_VERSION***</span></span>

## <a name="product-distribution"></a><span data-ttu-id="074fd-111">Distribuição de Produtos</span><span class="sxs-lookup"><span data-stu-id="074fd-111">Product Distribution</span></span>

<span data-ttu-id="074fd-112">NetX Secure está disponível em [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) .</span><span class="sxs-lookup"><span data-stu-id="074fd-112">NetX Secure is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="074fd-113">O pacote inclui ficheiros de origem, inclui ficheiros e um ficheiro PDF que contém este documento, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="074fd-113">The package includes source files, include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="074fd-114">**nx_secure_tls_api.h** Arquivo de cabeçalho API público para NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="074fd-114">**nx_secure_tls_api.h** Public API header file for NetX Secure TLS</span></span>
- <span data-ttu-id="074fd-115">**nx_secure_tls_user.h** Utilizador define ficheiro de cabeçalho para NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="074fd-115">**nx_secure_tls_user.h** User defines header file for NetX Secure TLS</span></span>
- <span data-ttu-id="074fd-116">**nx_secure_tls_port.h** Definições específicas da plataforma para o NetX Secure</span><span class="sxs-lookup"><span data-stu-id="074fd-116">**nx_secure_tls_port.h** Platform-specific definitions for NetX Secure</span></span>
- <span data-ttu-id="074fd-117">**nx_secure_tls.h** Ficheiro de cabeçalho para NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="074fd-117">**nx_secure_tls.h** Header file for NetX Secure TLS</span></span>
- <span data-ttu-id="074fd-118">**nx_secure_tls&#42;.c/h** Ficheiros de origem C/H para NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="074fd-118">**nx_secure_tls&#42;.c/h** C/H Source files for NetX Secure TLS</span></span>
- <span data-ttu-id="074fd-119">**nx_crypto&#42;.c/h** Ficheiros de origem C/H para a criptografia segura netX</span><span class="sxs-lookup"><span data-stu-id="074fd-119">**nx_crypto&#42;.c/h** C/H Source files for NetX Secure Cryptography</span></span>
- <span data-ttu-id="074fd-120">**nx_secure_x509&#42;.c/h** C/H Ficheiros de origem para certificados digitais X.509.</span><span class="sxs-lookup"><span data-stu-id="074fd-120">**nx_secure_x509&#42;.c/h** C/H Source files for X.509 digital certificates.</span></span>
- <span data-ttu-id="074fd-121">**demo_netx_secure_tls.c** Ficheiro C Fonte para demo de TLS Despromo De tLS Do NetX</span><span class="sxs-lookup"><span data-stu-id="074fd-121">**demo_netx_secure_tls.c** C Source file for NetX Secure TLS Demo</span></span>
- <span data-ttu-id="074fd-122">**NetX_Secure_User_Guide.pdf** Descrição em PDF do produto NetX Secure</span><span class="sxs-lookup"><span data-stu-id="074fd-122">**NetX_Secure_User_Guide.pdf** PDF description of NetX Secure product</span></span>

> [!NOTE]
> <span data-ttu-id="074fd-123">Os ficheiros nx_crypto\* são fornecidos para diferentes plataformas de hardware numa subdiretória do diretório principal NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="074fd-123">The nx_crypto\* files are provided for different hardware platforms in a subdirectory of the NetX Secure parent directory.</span></span>

## <a name="netx-secure-installation"></a><span data-ttu-id="074fd-124">Instalação NetX Secure</span><span class="sxs-lookup"><span data-stu-id="074fd-124">NetX Secure Installation</span></span>

<span data-ttu-id="074fd-125">Para utilizar o NetX Secure, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo nível de diretório onde o NetX está instalado.</span><span class="sxs-lookup"><span data-stu-id="074fd-125">In order to use NetX Secure, the entire distribution mentioned previously should be copied to the same directory level where NetX is installed.</span></span> <span data-ttu-id="074fd-126">Por exemplo, se o NetX for instalado no diretório "*\threadx\arm7\NetX*" então o *nx_secure\*\*.*</span><span class="sxs-lookup"><span data-stu-id="074fd-126">For example, if NetX is installed in the directory "*\threadx\arm7\NetX*" then the *nx_secure\*\*.*</span></span> <span data-ttu-id="074fd-127">os diretórios devem ser copiados em "*\threadx\arm7\NetXSecure*".</span><span class="sxs-lookup"><span data-stu-id="074fd-127">directories should be copied into "*\threadx\arm7\NetXSecure*".</span></span>

## <a name="using-netx-secure"></a><span data-ttu-id="074fd-128">Usando o NetX Secure</span><span class="sxs-lookup"><span data-stu-id="074fd-128">Using NetX Secure</span></span>

<span data-ttu-id="074fd-129">A utilização do NetX Secure TLS é simples.</span><span class="sxs-lookup"><span data-stu-id="074fd-129">Using NetX Secure TLS is straightforward.</span></span> <span data-ttu-id="074fd-130">Basicamente, o código de aplicação deve incluir *nx_secure_tls_api.h* depois de incluir *tx_api.h* e *nx_api.h,* para utilizar o ThreadX e o NetX.</span><span class="sxs-lookup"><span data-stu-id="074fd-130">Basically, the application code must include *nx_secure_tls_api.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span> <span data-ttu-id="074fd-131">Uma vez *incluído nx_secure_tls_api.h,* o código de aplicação é então capaz de fazer as chamadas de função NetX Secure especificadas mais tarde neste guia.</span><span class="sxs-lookup"><span data-stu-id="074fd-131">Once *nx_secure_tls_api.h* is included, the application code is then able to make the NetX Secure function calls specified later in this guide.</span></span> <span data-ttu-id="074fd-132">O pedido deve igualmente importar o *nx_secure\*\*.*</span><span class="sxs-lookup"><span data-stu-id="074fd-132">The application must also import the *nx_secure\*\*.*</span></span> <span data-ttu-id="074fd-133">ficheiros numa biblioteca NetXSecure e a plataforma específica *nx_crypto\*\*.*</span><span class="sxs-lookup"><span data-stu-id="074fd-133">files into a NetXSecure library, and the platform-specific *nx_crypto\*\*.*</span></span> <span data-ttu-id="074fd-134">ficheiros numa biblioteca NetXCrypto.</span><span class="sxs-lookup"><span data-stu-id="074fd-134">files into a NetXCrypto library.</span></span>

## <a name="small-example-system-tls-client"></a><span data-ttu-id="074fd-135">Sistema de pequenos exemplos (cliente TLS)</span><span class="sxs-lookup"><span data-stu-id="074fd-135">Small Example System (TLS Client)</span></span>

<span data-ttu-id="074fd-136">Um exemplo de como é fácil utilizar o NetX Secure é descrito na Figura 1.1, que aparece abaixo.</span><span class="sxs-lookup"><span data-stu-id="074fd-136">An example of how easy it is to use NetX Secure is described in Figure 1.1, which appears below.</span></span> <span data-ttu-id="074fd-137">Isto demonstra um cliente TLS simples, utilizando módulos de cripto de software (não específicos de hardware) para encriptação.</span><span class="sxs-lookup"><span data-stu-id="074fd-137">This demonstrates a simple TLS Client, using software crypto modules (not hardware specific) for encryption.</span></span> <span data-ttu-id="074fd-138">Foi concebido para funcionar com o servidor openSSL de eco inverso (abrir s_server -rev).</span><span class="sxs-lookup"><span data-stu-id="074fd-138">It is designed to work with the OpenSSL reverse-echo server (openssl s_server -rev).</span></span>

<span data-ttu-id="074fd-139">Note que para executar este exemplo, necessitará de um certificado X.509 CA para autenticar o certificado do seu servidor alvo.</span><span class="sxs-lookup"><span data-stu-id="074fd-139">Note that in order to run this example, you will need an X.509 CA certificate to authenticate your target server's certificate.</span></span> <span data-ttu-id="074fd-140">Para o exemplo OpenSSL, bastará um PKI simples de 2 níveis (certificado de servidor de > >de certificado CA raiz).</span><span class="sxs-lookup"><span data-stu-id="074fd-140">For the OpenSSL example, a simple 2-level PKI (root CA certificate-> >server certificate) will suffice.</span></span> <span data-ttu-id="074fd-141">Terá de preencher o conjunto "trusted_ca_data" com uma versão binária codificada pelo DER do certificado de CA e atualizar a variável "trusted_ca_length" para refletir o comprimento real do seu certificado.</span><span class="sxs-lookup"><span data-stu-id="074fd-141">You will need to fill in the "trusted_ca_data" array with a DER-encoded binary version of your CA certificate and update the "trusted_ca_length" variable to reflect your certificate's actual length.</span></span>

<span data-ttu-id="074fd-142">Também necessitará do controlador de rede para o seu hardware (substitua o parâmetro "nx_driver_xx" na nx_ip_create chamada).</span><span class="sxs-lookup"><span data-stu-id="074fd-142">You will also need the network driver for your hardware (replace "nx_driver_xx" parameter in nx_ip_create call).</span></span>

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

<span data-ttu-id="074fd-143">**Figura 1.1 Exemplo de utilização do NetX Secure com NetX**</span><span class="sxs-lookup"><span data-stu-id="074fd-143">**Figure 1.1 Example of NetX Secure use with NetX**</span></span>

## <a name="small-example-system-tls-web-server"></a><span data-ttu-id="074fd-144">Sistema de pequenos exemplos (servidor web TLS)</span><span class="sxs-lookup"><span data-stu-id="074fd-144">Small Example System (TLS Web Server)</span></span>

<span data-ttu-id="074fd-145">Um exemplo de como é fácil utilizar o NetX Secure é descrito na Figura 1.1, que aparece abaixo e demonstra um simples Servidor Web TLS (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="074fd-145">An example of how easy it is to use NetX Secure is described in Figure 1.1, which appears below and demonstrates a simple TLS Web Server (HTTPS).</span></span>

<span data-ttu-id="074fd-146">Note que para executar este exemplo, você precisará de um certificado X.509 para identificar o seu servidor para clientes TLS.</span><span class="sxs-lookup"><span data-stu-id="074fd-146">Note that in order to run this example, you will need an X.509 certificate to identify your server to TLS clients.</span></span> <span data-ttu-id="074fd-147">Para a maioria dos browers web, um certificado auto-assinado simples deve ser suficiente.</span><span class="sxs-lookup"><span data-stu-id="074fd-147">For most web browers a simple self-signed certificate should be sufficient.</span></span> <span data-ttu-id="074fd-148">O seu navegador irá queixar-se de não ser capaz de autenticar o servidor e, em alguns casos, poderá não conseguir estabelecer uma ligação TLS/HTTPS ao seu servidor<sup>3</sup>.</span><span class="sxs-lookup"><span data-stu-id="074fd-148">Your browser will complain about not being able to authenticate the server and in some cases may be unable to establish a TLS/HTTPS connection to your server<sup>3</sup>.</span></span> <span data-ttu-id="074fd-149">Terá de preencher o conjunto "certificate_data" com uma versão binária codificada pelo DER do certificado do servidor e atualizar a variável "certificate_length" para refletir o comprimento real do seu certificado.</span><span class="sxs-lookup"><span data-stu-id="074fd-149">You will need to fill in the "certificate_data" array with a DER-encoded binary version of your server certificate and update the "certificate_length" variable to reflect your certificate's actual length.</span></span> <span data-ttu-id="074fd-150">Também precisa de preencher o conjunto "private_key" com uma versão codificada de DER da chave privada do certificado, formatada com recurso a PKCS#1 para a chave RSA e RFC 5915 para chaves ECC.</span><span class="sxs-lookup"><span data-stu-id="074fd-150">You also need to fill in the "private_key" array with a DER-encoded version of your certificate's private key, formatted using PKCS#1 for RSA key and RFC 5915 for ECC keys.</span></span> <span data-ttu-id="074fd-151">Preencha a variável "private_key_length" com o comprimento real dos seus dados-chave.</span><span class="sxs-lookup"><span data-stu-id="074fd-151">Fill in the "private_key_length" variable with the actual length of your key data.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="074fd-152">Alguns navegadores (particularmente algumas versões do navegador Chrome) podem rejeitar certificados auto-assinados.</span><span class="sxs-lookup"><span data-stu-id="074fd-152">Some browsers (particularly some versions of the Chrome browser) may reject self-signed certificates.</span></span> <span data-ttu-id="074fd-153">Neste caso, pode criar um PKI de 2 níveis com um certificado de CA raiz que é usado para assinar o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="074fd-153">In this case you can create a 2-level PKI with a root CA certificate that is used to sign your server certificate.</span></span> <span data-ttu-id="074fd-154">Nesta situação, o certificado de CA raiz é instalado como um certificado de raiz fidedigno no seu navegador.</span><span class="sxs-lookup"><span data-stu-id="074fd-154">In this situation, the root CA certificate is installed as a trusted root certificate in your browser.</span></span> <span data-ttu-id="074fd-155">!!!</span><span class="sxs-lookup"><span data-stu-id="074fd-155">!!!</span></span> <span data-ttu-id="074fd-156">IMPORTANTE – remova o certificado de CA raiz do seu navegador quando estiver pronto e não o utilize para quaisquer aplicações de produção !!!</span><span class="sxs-lookup"><span data-stu-id="074fd-156">IMPORTANT – remove your root CA certificate from your browser when done and do not use it for any production applications !!!</span></span>

<span data-ttu-id="074fd-157">Também necessitará do controlador de rede para o seu hardware (substitua o parâmetro "nx_driver_xx" na nx_ip_create chamada).</span><span class="sxs-lookup"><span data-stu-id="074fd-157">You will also need the network driver for your hardware (replace "nx_driver_xx" parameter in nx_ip_create call).</span></span>

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

<span data-ttu-id="074fd-158">**Figura 1.2 Exemplo de utilização do NetX Secure com NetX**</span><span class="sxs-lookup"><span data-stu-id="074fd-158">**Figure 1.2 Example of NetX Secure use with NetX**</span></span>

## <a name="a-note-on-tls-session-error-recovery"></a><span data-ttu-id="074fd-159">Uma nota sobre a recuperação de erros de sessão de TLS</span><span class="sxs-lookup"><span data-stu-id="074fd-159">A Note on TLS Session Error Recovery</span></span>

<span data-ttu-id="074fd-160">Os sistemas de exemplo acima descritos mostram os contornos básicos para um Cliente e Servidor TLS, respectivamente, mas para maior clareza o tratamento de erros é omitido.</span><span class="sxs-lookup"><span data-stu-id="074fd-160">The example systems described above show the basic outlines for a TLS Client and Server, respectively, but for clarity the error handling is omitted.</span></span> <span data-ttu-id="074fd-161">No entanto, uma parte do sistema de segurança que o TLS fornece depende do manuseamento adequado das condições de erro.</span><span class="sxs-lookup"><span data-stu-id="074fd-161">However, part of the security TLS provides is dependent on the proper handling of error conditions.</span></span> <span data-ttu-id="074fd-162">Geralmente, os problemas potenciais mais graves serão tratados dentro da própria pilha TLS, mas é importante que a aplicação TLS responda adequadamente e recupere de erros TLS que não são tratados dentro da implementação do TLS.</span><span class="sxs-lookup"><span data-stu-id="074fd-162">Generally, the most serious potential problems will be handled within the TLS stack itself, but it is important for the TLS application to properly respond to and recover from TLS errors that are not handled within the TLS implementation.</span></span>

<span data-ttu-id="074fd-163">Para ilustrar a lógica necessária para o manuseamento adequado de erros, a seguinte função demonstra uma recolha típica de serviços API que podem ser utilizados para lidar adequadamente com erros de TLS e repor o estado TLS de forma limpa após a origem de uma condição de erro.</span><span class="sxs-lookup"><span data-stu-id="074fd-163">In order to illustrate the necessary logic for proper error handling, the following function demonstrates a typical collection of API services that can be used to properly handle TLS errors and cleanly reset the TLS state after an error condition is encountered.</span></span> <span data-ttu-id="074fd-164">Para além da secção em que se nota, a lógica aplica-se tanto às instâncias do TLS Client como do TLS Server.</span><span class="sxs-lookup"><span data-stu-id="074fd-164">Other than the section where noted, the logic applies to both TLS Client and TLS Server instances.</span></span>

<span data-ttu-id="074fd-165">Note que as chamadas mais importantes da API na função são para os serviços *nx_secure_tls_session_end*, que fecham de forma limpa a sessão TLS ou aperto de mão, e *nx_secure_tls_session_reset*, que limpa o estado da sessão TLS para que a tls_session instância da estrutura de controlo possa ser reutilizada para uma nova sessão de TLS.</span><span class="sxs-lookup"><span data-stu-id="074fd-165">Note that the most important API calls in the function are to the services *nx_secure_tls_session_end*, which cleanly closes the TLS session or handshake, and *nx_secure_tls_session_reset*, which clears the TLS session state so the tls_session control structure instance can be reused for a new TLS session.</span></span> <span data-ttu-id="074fd-166">Note também que *nx_secure_tls_session_reset* não limpa o estado configurado pelo utilizador, como certificados ou buffers atribuídos, permitindo que a sessão seja reutilizada sem voltar a chamar *nx_secure_tls_session_create.*</span><span class="sxs-lookup"><span data-stu-id="074fd-166">Also note that *nx_secure_tls_session_reset* does not clear the user-configured state such as certificates or assigned buffers, allowing the session to be reused without calling *nx_secure_tls_session_create* again.</span></span> <span data-ttu-id="074fd-167">Para limpar completamente todo o estado da sessão TLS, o *serviço nx_secure_tls_session_delete* pode ser usado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="074fd-167">To completely clear all TLS session state, the service *nx_secure_tls_session_delete* may be used instead.</span></span>

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

## <a name="configuration-options"></a><span data-ttu-id="074fd-168">Opções de configuração</span><span class="sxs-lookup"><span data-stu-id="074fd-168">Configuration Options</span></span>

<span data-ttu-id="074fd-169">Existem várias opções de configuração para a construção do NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="074fd-169">There are several configuration options for building NetX Secure.</span></span> <span data-ttu-id="074fd-170">Segue-se uma lista de todas as opções, onde cada uma é descrita em detalhe:</span><span class="sxs-lookup"><span data-stu-id="074fd-170">Following is a list of all options, where each is described in detail:</span></span>

| <span data-ttu-id="074fd-171">Definir</span><span class="sxs-lookup"><span data-stu-id="074fd-171">Define</span></span> | <span data-ttu-id="074fd-172">Significado</span><span class="sxs-lookup"><span data-stu-id="074fd-172">Meaning</span></span> |
|----------------------|------------------------------------------------|
| <span data-ttu-id="074fd-173">**NX_SECURE_DISABLE_ERROR_CHECKING**</span><span class="sxs-lookup"><span data-stu-id="074fd-173">**NX_SECURE_DISABLE_ERROR_CHECKING**</span></span>                | <span data-ttu-id="074fd-174">Definida, esta opção remove a verificação básica de erros NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="074fd-174">Defined, this option removes the basic NetX Secure error checking.</span></span> <span data-ttu-id="074fd-175">É normalmente usado após a depurada aplicação.</span><span class="sxs-lookup"><span data-stu-id="074fd-175">It is typically used after the application has been debugged.</span></span> |
| <span data-ttu-id="074fd-176">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**</span><span class="sxs-lookup"><span data-stu-id="074fd-176">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**</span></span>                  | <span data-ttu-id="074fd-177">Definida, esta opção dá o módulo RSA máximo esperado, em bits.</span><span class="sxs-lookup"><span data-stu-id="074fd-177">Defined, this option gives the maximum RSA modulus expected, in bits.</span></span> <span data-ttu-id="074fd-178">O valor predefinido é de 4096 para um módulo de 4096 bits.</span><span class="sxs-lookup"><span data-stu-id="074fd-178">The default value is 4096 for a 4096-bit modulus.</span></span> <span data-ttu-id="074fd-179">Outros valores podem ser 3072, 2048 ou 1024 (não recomendado).</span><span class="sxs-lookup"><span data-stu-id="074fd-179">Other values can be 3072, 2048, or 1024 (not recommended).</span></span> |
| <span data-ttu-id="074fd-180">**NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES**</span><span class="sxs-lookup"><span data-stu-id="074fd-180">**NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES**</span></span>        | <span data-ttu-id="074fd-181">Definida, esta opção permite que o TLS aceite certificados auto-assinados de um anfitrião remoto.</span><span class="sxs-lookup"><span data-stu-id="074fd-181">Defined, this option allows TLS to accept self-signed certificates from a remote host.</span></span> <span data-ttu-id="074fd-182">Por padrão, o TLS rejeitará certificados de servidor auto-assinados como precaução de segurança.</span><span class="sxs-lookup"><span data-stu-id="074fd-182">By default, TLS will reject self-signed server certificates as a security precaution.</span></span> <span data-ttu-id="074fd-183">Se esta macro for definida, os certificados auto-assinados devem ainda ser adicionados à loja de confiança para serem aceites.</span><span class="sxs-lookup"><span data-stu-id="074fd-183">If this macro is defined, self-signed certificates must still be added to the trusted store to be accepted.</span></span> |
| <span data-ttu-id="074fd-184">**NX_SECURE_ENABLE_CLIENT_CERTIFICATE_VERIFY**</span><span class="sxs-lookup"><span data-stu-id="074fd-184">**NX_SECURE_ENABLE_CLIENT_CERTIFICATE_VERIFY**</span></span>      | <span data-ttu-id="074fd-185">Definida, esta opção permite a verificação opcional do Certificado de Cliente X.509 para servidores TLS<sup>4</sup>.</span><span class="sxs-lookup"><span data-stu-id="074fd-185">Defined, this option enables the optional X.509 Client Certificate Verification for TLS Servers<sup>4</sup>.</span></span>  |
| <span data-ttu-id="074fd-186">**NX_SECURE_ENABLE_PSK_CIPHERSUITES**</span><span class="sxs-lookup"><span data-stu-id="074fd-186">**NX_SECURE_ENABLE_PSK_CIPHERSUITES**</span></span>               | <span data-ttu-id="074fd-187">Definida, esta opção permite a funcionalidade de Chave Pré-Partilhada (PSK).</span><span class="sxs-lookup"><span data-stu-id="074fd-187">Defined, this option enables Pre-Shared Key (PSK) functionality.</span></span> <span data-ttu-id="074fd-188">Não desativa certificados digitais.</span><span class="sxs-lookup"><span data-stu-id="074fd-188">It does not disable digital certificates.</span></span> |
| <span data-ttu-id="074fd-189">**NX_SECURE_TLS_CLIENT_DISABLED**</span><span class="sxs-lookup"><span data-stu-id="074fd-189">**NX_SECURE_TLS_CLIENT_DISABLED**</span></span>                   | <span data-ttu-id="074fd-190">Definida, esta opção remove todo o código de pilha TLS relacionado com o modo TLS Client, reduzindo o código e o uso de dados.</span><span class="sxs-lookup"><span data-stu-id="074fd-190">Defined, this option removes all TLS stack code related to TLS Client mode, reducing code and data usage.</span></span> |
| <span data-ttu-id="074fd-191">**NX_SECURE_TLS_SERVER_DISABLED**</span><span class="sxs-lookup"><span data-stu-id="074fd-191">**NX_SECURE_TLS_SERVER_DISABLED**</span></span>                   | <span data-ttu-id="074fd-192">Definida, esta opção remove todo o código de pilha TLS relacionado com o modo TLS Server, reduzindo o código e a utilização de dados.</span><span class="sxs-lookup"><span data-stu-id="074fd-192">Defined, this option removes all TLS stack code related to TLS Server mode, reducing code and data usage.</span></span>  |
| <span data-ttu-id="074fd-193">**NX_SECURE_DISABLE_ECC_CIPHERSUITE**</span><span class="sxs-lookup"><span data-stu-id="074fd-193">**NX_SECURE_DISABLE_ECC_CIPHERSUITE**</span></span>               | <span data-ttu-id="074fd-194">Definida, esta opção remove toda a lógica TLS para cifrasuites de criptografia da curva elíptica (ECC).</span><span class="sxs-lookup"><span data-stu-id="074fd-194">Defined, this option removes all TLS logic for Elliptic Curve Cryptography (ECC) ciphersuites.</span></span> <span data-ttu-id="074fd-195">Estes cifrasuites são opcionais em TLS 1.2 e mais cedo e desativá-los pode resultar numa redução significativa do código e do tamanho dos dados.</span><span class="sxs-lookup"><span data-stu-id="074fd-195">These ciphersuites are optional in TLS 1.2 and earlier and disabling them can result in significant code and data size reduction.</span></span>|
| <span data-ttu-id="074fd-196">**NX_SECURE_TLS_ENABLE_TLS_1_3**</span><span class="sxs-lookup"><span data-stu-id="074fd-196">**NX_SECURE_TLS_ENABLE_TLS_1_3**</span></span>                    | <span data-ttu-id="074fd-197">Definida, esta opção permite o modo TLSv1.3.</span><span class="sxs-lookup"><span data-stu-id="074fd-197">Defined, this option enables TLSv1.3 mode.</span></span> <span data-ttu-id="074fd-198">TLS 1.3 é a versão mais recente do TLS e é desativada por padrão.</span><span class="sxs-lookup"><span data-stu-id="074fd-198">TLS 1.3 is the newest version of TLS and is disabled by default.</span></span> |
| <span data-ttu-id="074fd-199">**NX_SECURE_TLS_ENABLE_TLS_1_0**</span><span class="sxs-lookup"><span data-stu-id="074fd-199">**NX_SECURE_TLS_ENABLE_TLS_1_0**</span></span>                    | <span data-ttu-id="074fd-200">Definida, esta opção permite o modo TLSv1.0.</span><span class="sxs-lookup"><span data-stu-id="074fd-200">Defined, this option enables the legacy TLSv1.0 mode.</span></span> <span data-ttu-id="074fd-201">O TLSv1.0 é considerado obsoleto, pelo que só deve ser ativado para retrocompatibilidade com aplicações mais antigas.</span><span class="sxs-lookup"><span data-stu-id="074fd-201">TLSv1.0 is considered obsolete so it should only be enabled for backward-compatibility with older applications.</span></span> |
| <span data-ttu-id="074fd-202">**NX_SECURE_TLS_ENABLE_TLS_1_1**</span><span class="sxs-lookup"><span data-stu-id="074fd-202">**NX_SECURE_TLS_ENABLE_TLS_1_1**</span></span>                    | <span data-ttu-id="074fd-203">Definida, esta opção permite o modo TLSv1.1.</span><span class="sxs-lookup"><span data-stu-id="074fd-203">Defined, this option enables the legacy TLSv1.1 mode.</span></span> <span data-ttu-id="074fd-204">O TLSv1.1 é considerado obsoleto, pelo que só deve ser ativado para retrocompatibilidade com aplicações mais antigas.</span><span class="sxs-lookup"><span data-stu-id="074fd-204">TLSv1.1 is considered obsolete so it should only be enabled for backward-compatibility with older applications.</span></span> |
| <span data-ttu-id="074fd-205">**NX_SECURE_TLS_DISABLE_TLS_1_1**</span><span class="sxs-lookup"><span data-stu-id="074fd-205">**NX_SECURE_TLS_DISABLE_TLS_1_1**</span></span>                   | <span data-ttu-id="074fd-206">Definida, esta opção desativa o modo TLSv1.1.</span><span class="sxs-lookup"><span data-stu-id="074fd-206">Defined, this option disables TLSv1.1 mode.</span></span> <span data-ttu-id="074fd-207">É definido por defeito.</span><span class="sxs-lookup"><span data-stu-id="074fd-207">It is defined by default.</span></span> <span data-ttu-id="074fd-208">O TLSv1.1 é desativado a favor da utilização apenas do TLSv1.2<sup>5</sup>mais seguro .</span><span class="sxs-lookup"><span data-stu-id="074fd-208">TLSv1.1 is disabled in favor of using only the more-secure TLSv1.2<sup>5</sup>.</span></span>  |
| <span data-ttu-id="074fd-209">**NX_SECURE_X509_STRICT_NAME_COMPARE**</span><span class="sxs-lookup"><span data-stu-id="074fd-209">**NX_SECURE_X509_STRICT_NAME_COMPARE**</span></span>              | <span data-ttu-id="074fd-210">Definida, esta opção permite uma estrita comparação de nomes distintos para certificados X.509 para pesquisa e verificação de certificados.</span><span class="sxs-lookup"><span data-stu-id="074fd-210">Defined, this option enables strict distinguished name comparison for X.509 certificates for certificate searching and verification.</span></span> <span data-ttu-id="074fd-211">O padrão é apenas comparar os campos de Nome Comum dos Nomes Distintos.</span><span class="sxs-lookup"><span data-stu-id="074fd-211">The default is to only compare the Common Name fields of the Distinguished Names.</span></span>|
| <span data-ttu-id="074fd-212">**NX_SECURE_X509_USE_EXTENDED_DISTINGUISHED_NAMES**</span><span class="sxs-lookup"><span data-stu-id="074fd-212">**NX_SECURE_X509_USE_EXTENDED_DISTINGUISHED_NAMES**</span></span> | <span data-ttu-id="074fd-213">Definida, esta opção permite os campos de Nome Distinto X.509 opcionais, em detrimento do uso extra de memória para certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="074fd-213">Defined, this option enables the optional X.509 Distinguished Name fields, at the expense of extra memory use for X.509 certificates.</span></span> |

4. <span data-ttu-id="074fd-214">Note que esta opção apenas permite que o código seja ligado à aplicação.</span><span class="sxs-lookup"><span data-stu-id="074fd-214">Note that this option only enables the code to be linked into the application.</span></span> <span data-ttu-id="074fd-215">A funcionalidade terá de ser ativada com o serviço API nx_secure_tls_session_client_verify_enable ou configurada utilizando nx_secure_tls_session_x509_client_verify_configure para utilizar a Verificação do Certificado do Cliente.</span><span class="sxs-lookup"><span data-stu-id="074fd-215">The feature will need to be enabled with the API service nx_secure_tls_session_client_verify_enable or configured using nx_secure_tls_session_x509_client_verify_configure in order to use Client Certificate Verification.</span></span>

5. <span data-ttu-id="074fd-216">Note que também é possível desativar o TLSv1.2 se utilizar apenas TLS 1.0 ou TLS 1.1.</span><span class="sxs-lookup"><span data-stu-id="074fd-216">Note that it is also possible to disable TLSv1.2 if using TLS 1.0 or TLS 1.1 only.</span></span> <span data-ttu-id="074fd-217">No entanto, isto não é recomendado e não suportado diretamente.</span><span class="sxs-lookup"><span data-stu-id="074fd-217">However, this is not recommended and not directly supported.</span></span>
