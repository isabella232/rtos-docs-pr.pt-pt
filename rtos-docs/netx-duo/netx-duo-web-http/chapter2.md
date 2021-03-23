---
title: Capítulo 2 - Instalação e utilização de HTTP e HTTPS
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente NetX Web HTTP.
author: philmea
ms.author: philmea
ms.date: 07/24/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 99e649781588b56e72b509c2aa077c38423379d1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825705"
---
# <a name="chapter-2---installation-and-use-of-http-and-https"></a><span data-ttu-id="2e295-103">Capítulo 2 - Instalação e utilização de HTTP e HTTPS</span><span class="sxs-lookup"><span data-stu-id="2e295-103">Chapter 2 - Installation and use of HTTP and HTTPS</span></span>

<span data-ttu-id="2e295-104">Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente NetX Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="2e295-104">This chapter contains a description of various issues related to installation, setup, and usage of the NetX Web HTTP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="2e295-105">Distribuição de Produtos</span><span class="sxs-lookup"><span data-stu-id="2e295-105">Product Distribution</span></span>

<span data-ttu-id="2e295-106">HTTP para NetX está disponível em [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) .</span><span class="sxs-lookup"><span data-stu-id="2e295-106">HTTP for NetX is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="2e295-107">O pacote inclui três ficheiros de origem, dois ficheiros, e um ficheiro que contém este documento, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="2e295-107">The package includes three source files, two include files, and a file that contains this document, as follows:</span></span>

- <span data-ttu-id="2e295-108">**nx_web_http_common.h** Arquivo comum de cabeçalho para NetX Web HTTP</span><span class="sxs-lookup"><span data-stu-id="2e295-108">**nx_web_http_common.h** Common header file for NetX Web HTTP</span></span>
- <span data-ttu-id="2e295-109">**nx_web_http_client.h** Ficheiro de cabeçalho para cliente HTTP para NetX Web</span><span class="sxs-lookup"><span data-stu-id="2e295-109">**nx_web_http_client.h** Header file for HTTP Client for NetX Web</span></span>
- <span data-ttu-id="2e295-110">**nx_web_http_server.h** Ficheiro de cabeçalho para SERVIDOR HTTP para NetX Web</span><span class="sxs-lookup"><span data-stu-id="2e295-110">**nx_web_http_server.h** Header file for HTTP Server for NetX Web</span></span>
- <span data-ttu-id="2e295-111">**nx_web_http_client.c** C Ficheiro de origem para cliente HTTP para NetX Web</span><span class="sxs-lookup"><span data-stu-id="2e295-111">**nx_web_http_client.c** C Source file for HTTP Client for NetX Web</span></span>
- <span data-ttu-id="2e295-112">**nx_web_http_server.c** C Ficheiro de origem para servidor HTTP para NetX Web</span><span class="sxs-lookup"><span data-stu-id="2e295-112">**nx_web_http_server.c** C Source file for HTTP Server for NetX Web</span></span>
- <span data-ttu-id="2e295-113">**nx_tcpserver.c** Ficheiro de origem C para várias tomadas TCP</span><span class="sxs-lookup"><span data-stu-id="2e295-113">**nx_tcpserver.c** C Source file for multiple TCP sockets</span></span>
- <span data-ttu-id="2e295-114">**nx_tcpserver.h** Ficheiro de cabeçalho para definir símbolos do servidor HTTPS</span><span class="sxs-lookup"><span data-stu-id="2e295-114">**nx_tcpserver.h** Header file for defining HTTPS Server symbols</span></span>
- <span data-ttu-id="2e295-115">**nx_md5.c** Algoritmos de digestão MD5</span><span class="sxs-lookup"><span data-stu-id="2e295-115">**nx_md5.c** MD5 digest algorithms</span></span>
- <span data-ttu-id="2e295-116">**filex_stub.h** Ficheiro de stub se o FileX não estiver presente</span><span class="sxs-lookup"><span data-stu-id="2e295-116">**filex_stub.h** Stub file if FileX is not present</span></span>
- <span data-ttu-id="2e295-117">**nx_web_http.pdf** Descrição de HTTP para NetX Web</span><span class="sxs-lookup"><span data-stu-id="2e295-117">**nx_web_http.pdf** Description of HTTP for NetX Web</span></span>
- <span data-ttu-id="2e295-118">**demo_netx_web_http.c** Demonstração de NetX Web HTTP</span><span class="sxs-lookup"><span data-stu-id="2e295-118">**demo_netx_web_http.c** NetX Web HTTP demonstration</span></span>

## <a name="http-installation"></a><span data-ttu-id="2e295-119">Instalação HTTP</span><span class="sxs-lookup"><span data-stu-id="2e295-119">HTTP Installation</span></span>

<span data-ttu-id="2e295-120">Para utilizar o NetX Web HTTP, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX Duo está instalado.</span><span class="sxs-lookup"><span data-stu-id="2e295-120">In order to use NetX Web HTTP, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="2e295-121">Por exemplo, se o NetX Duo for instalado no diretório "*\threadx\arm7\green*" então o *nx_web_http_client.h* e *nx_web_http_client.c para aplicações do Cliente NetX Web HTTP, e nx_web_http_server.h,* *nx_web_http_server.c, nx_tcpserver.c e nx_tcpserver.h para aplicações netX Web HTTP Server. Para aplicações de cliente e servidor, nx_web_http_common.h também deve estar neste diretório. nx_md5.c* também devem ser copiados para este diretório se estiver a ser utilizada a autenticação digestiva.</span><span class="sxs-lookup"><span data-stu-id="2e295-121">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nx_web_http_client.h* and *nx_web_http_client.c for NetX Web HTTP Client applications, and nx_web_http_server.h*, *nx_web_http_server.c, nx_tcpserver.c and nx_tcpserver.h for NetX Web HTTP Server applications. For both client and server applications, nx_web_http_common.h must be in this directory as well. nx_md5.c* should also be copied into this directory if digest authentication is being used.</span></span> <span data-ttu-id="2e295-122">Para a aplicação de demonstração 'ram driver' os ficheiros HTTP Cliente e Servidor devem ser copiados para o mesmo diretório.</span><span class="sxs-lookup"><span data-stu-id="2e295-122">For the demo ‘ram driver’ application HTTP Client and Server files should be copied into the same directory.</span></span>

<span data-ttu-id="2e295-123">Se utilizar o TLS, deverá ter um diretório NetX Secure separado contendo os ficheiros de origem TLS.</span><span class="sxs-lookup"><span data-stu-id="2e295-123">If using TLS, you should have a separate NetX Secure directory containing the TLS source files.</span></span>

## <a name="using-http"></a><span data-ttu-id="2e295-124">Utilizar HTTP</span><span class="sxs-lookup"><span data-stu-id="2e295-124">Using HTTP</span></span>

<span data-ttu-id="2e295-125">A utilização da NetX Web HTTP é fácil.</span><span class="sxs-lookup"><span data-stu-id="2e295-125">Using NetX Web HTTP is easy.</span></span> <span data-ttu-id="2e295-126">Basicamente, o código de aplicação deve incluir *nx_web_http_client.h* e/ou *nx_web_http_server.h* depois de incluir *tx_api.h, fx_api.h e* *nx_api.h* *(nx_web_http_common.h* está automaticamente incluído).</span><span class="sxs-lookup"><span data-stu-id="2e295-126">Basically, the application code must include *nx_web_http_client.h* and/or *nx_web_http_server.h* after it includes *tx_api.h, fx_api.h,* and *nx_api.h* (*nx_web_http_common.h* is automatically included).</span></span> <span data-ttu-id="2e295-127">Estes cabeçalhos permitem que a aplicação utilize ThreadX, FileX e NetX Duo, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="2e295-127">Those headers enable the application to use ThreadX, FileX, and NetX Duo, respectively.</span></span> <span data-ttu-id="2e295-128">Para o suporte HTTPS, os cabeçalhos devem ser incluídos após a inclusão do ficheiro *nx_secure_tls.h* para obter suporte TLS.</span><span class="sxs-lookup"><span data-stu-id="2e295-128">For HTTPS support, the headers must be included after the *nx_secure_tls.h* file is included to bring in TLS support.</span></span>

<span data-ttu-id="2e295-129">Uma vez incluídos os ficheiros do cabeçalho HTTP, o código de aplicação pode então então fazer as chamadas de função HTTP especificadas posteriormente neste guia.</span><span class="sxs-lookup"><span data-stu-id="2e295-129">Once the HTTP header files are included, the application code is then able to make the HTTP function calls specified later in this guide.</span></span> <span data-ttu-id="2e295-130">A aplicação também deve *ligar-se a nx_web_http_client.c para clientes HTTP(S),* *nx_web_http_server.c e nx_tcpserver.c para servidores HTTP(S)* e *nx_md5.c (para autenticação digestiva)* no processo de construção.</span><span class="sxs-lookup"><span data-stu-id="2e295-130">The application must also link with *nx_web_http_client.c for HTTP(S) clients*, *nx_web_http_server.c and nx_tcpserver.c for HTTP(S) servers*, and *nx_md5.c (for digest authentication)* in the build process.</span></span> <span data-ttu-id="2e295-131">Estes ficheiros devem ser compilados da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação.</span><span class="sxs-lookup"><span data-stu-id="2e295-131">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="2e295-132">Isto é tudo o que é necessário para usar o NetX Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="2e295-132">This is all that is required to use NetX Web HTTP.</span></span>

> [!NOTE]
> <span data-ttu-id="2e295-133">Se NX_WEB_HTTP_DIGEST_ENABLE não for especificado no processo de construção, o ficheiro *.c md5 não* precisa de ser adicionado ao pedido.</span><span class="sxs-lookup"><span data-stu-id="2e295-133">If NX_WEB_HTTP_DIGEST_ENABLE is not specified in the build process, the *md5.c* file does not need to be added to the application.</span></span> <span data-ttu-id="2e295-134">Da mesma forma, se não forem necessárias capacidades do Cliente HTTP, o ficheiro *nx_web_http_client.c* poderá ser omitido e, se não forem necessárias capacidades do Servidor HTTP, poderá ser omitida *nx_web_http_server.c.*</span><span class="sxs-lookup"><span data-stu-id="2e295-134">Similarly, if no HTTP Client capabilities are required, the *nx_web_http_client.c* file may be omitted and if no HTTP Server capabilities are required, *nx_web_http_server.c* may be omitted.</span></span>
>
> <span data-ttu-id="2e295-135">A menos NX_WEB_HTTPS_ENABLE seja definida para ativar HTTPS (em vez de utilizar apenas texto simples HTTP) então o NetX Secure TLS não precisa de estar na construção.</span><span class="sxs-lookup"><span data-stu-id="2e295-135">Unless NX_WEB_HTTPS_ENABLE is defined in order to enable HTTPS (instead of using only plaintext HTTP) then NetX Secure TLS does not need to be in the build.</span></span>
>
> <span data-ttu-id="2e295-136">Uma vez que http utiliza os serviços NetX TCP, o TCP deve ser ativado com a chamada *nx_tcp_enable()* antes de utilizar HTTP.</span><span class="sxs-lookup"><span data-stu-id="2e295-136">Since HTTP utilizes NetX TCP services, TCP must be enabled with the *nx_tcp_enable()* call prior to using HTTP.</span></span>
>
> <span data-ttu-id="2e295-137">Ao utilizar HTTPS com NetX Secure TLS, o TLS deve ser rubricado com *nx_secure_tls_initialize()* antes de ligar para as rotinas HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2e295-137">When using HTTPS with NetX Secure TLS, TLS must be initialized with *nx_secure_tls_initialize()* prior to calling HTTPS routines.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="2e295-138">Sistema de Pequenos Exemplos</span><span class="sxs-lookup"><span data-stu-id="2e295-138">Small Example System</span></span>

<span data-ttu-id="2e295-139">Um exemplo de como utilizar o NetX Web HTTP é descrito na Figura 1.1 abaixo.</span><span class="sxs-lookup"><span data-stu-id="2e295-139">An example of how to use NetX Web HTTP is described in Figure 1.1 below.</span></span>

> [!CAUTION]
> <span data-ttu-id="2e295-140">Isto está previsto apenas para fins de demonstração e não é garantido que compile e corra como está.</span><span class="sxs-lookup"><span data-stu-id="2e295-140">This is provided for demonstration purposes only and is not guaranteed to compile and run as is.</span></span>
>
> <span data-ttu-id="2e295-141">Consulte a distribuição de código de lançamento do NetX Duo HTTPS para ficheiros de código de demonstração que serão devidamente construídos no ambiente express logic nativo.</span><span class="sxs-lookup"><span data-stu-id="2e295-141">Please refer to the NetX Duo HTTPS release code distribution for  demo source code file(s) that will properly build in the native Express Logic environment.</span></span>  <span data-ttu-id="2e295-142">Saiba também que estas demos são mantidas intencionalmente muito simples, uma vez que se destinam a introduzir a aplicação HTTPS e/ou NetX Duo HTTPS para novos utilizadores.</span><span class="sxs-lookup"><span data-stu-id="2e295-142">Also be aware that these demos are intentionally kept very simple as they are intended to introduce HTTPS and/or NetX Duo HTTPS application to new users.</span></span>

<span data-ttu-id="2e295-143">Neste exemplo, o HTTP inclui o ficheiro *nx_web_http_client.h e nx_web_http_server.h são trazidos* *(netx_web_http_common.h* é incluído automaticamente).</span><span class="sxs-lookup"><span data-stu-id="2e295-143">In this example, the HTTP include file *nx_web_http_client.h and nx_web_http_server.h are* brought in (*netx_web_http_common.h* is included automatically).</span></span> <span data-ttu-id="2e295-144">Em seguida, o servidor HTTP é criado em "*tx_application_define*".</span><span class="sxs-lookup"><span data-stu-id="2e295-144">Next, the HTTP Server is created in “*tx_application_define*”.</span></span> <span data-ttu-id="2e295-145">Note que o bloco de controlo do servidor HTTP "*Servidor*" foi definido como uma variável global anteriormente.</span><span class="sxs-lookup"><span data-stu-id="2e295-145">Note that the HTTP Server control block “*Server*” was defined as a global variable previously.</span></span> <span data-ttu-id="2e295-146">Após a criação bem sucedida, o SERVIDOR HTTPS é iniciado.</span><span class="sxs-lookup"><span data-stu-id="2e295-146">After successful creation, the HTTPS Server is started.</span></span> <span data-ttu-id="2e295-147">O Cliente HTTPS é então criado.</span><span class="sxs-lookup"><span data-stu-id="2e295-147">The HTTPS Client is then created.</span></span> <span data-ttu-id="2e295-148">Escreve o ficheiro e lê o ficheiro de volta.</span><span class="sxs-lookup"><span data-stu-id="2e295-148">It writes the file and reads the file back.</span></span>

> [!NOTE]
> <span data-ttu-id="2e295-149">NX_WEB_HTTPS_ENABLE é definido neste sistema.</span><span class="sxs-lookup"><span data-stu-id="2e295-149">NX_WEB_HTTPS_ENABLE is defined on this system.</span></span>

```c
/* This is a small demo of HTTPS on the high-performance NetX Duo TCP/IP stack.
   This demo relies on ThreadX, NetX Duo, and FileX to show an HTML
   transfer from the client and then back from the server.  */

#include  "tx_api.h"
#include  "fx_api.h"
#include  "nx_api.h"
#include  “nx_crypto.h”
#include  “nx_secure_tls_api.h”
#include  “nx_secure_x509.h”
#include  "nx_web_http_client.h"
#include  "nx_web_http_server.h"
#define    DEMO_STACK_SIZE         4096


/* Define the ThreadX and NetX object control blocks...  */

TX_THREAD               thread_0;
TX_THREAD               thread_1;
NX_PACKET_POOL          pool_0;
NX_PACKET_POOL          pool_1;
NX_IP                   ip_0;
NX_IP                   ip_1;
FX_MEDIA                ram_disk;

/* Define HTTP objects.  */

NX_WEB_HTTP_SERVER      my_server;
NX_WEB_HTTP_CLIENT      my_client;

/* Define the counters used in the demo application...  */

ULONG                   error_counter;


/* Define the RAM disk memory.  */

UCHAR                   ram_disk_memory[32000];

/* Include cryptographic routines for TLS. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;

/* Define TLS data for HTTPS. */
CHAR crypto_metadata[8928 * NX_WEB_HTTP_SESSION_MAX];
UCHAR tls_packet_buffer[16500];

/* NX_WEB_HTTP_SERVER_SESSION_MAX defaults to 2 in nx_web_http_server.h */
UCHAR server_tls_packet_buffer[16500 * NX_WEB_HTTP_SERVER_SESSION_MAX];

/* Define certificate containers. The server certificate is used to identify the NetX
   Web HTTPS server and the trusted certificate is used by the client to verify the
   server’s identity certificate.  */
NX_SECURE_X509_CERT server_certificate;
NX_SECURE_X509_CERT trusted_certificate;

/* Remote certificates need both an NX_SECURE_X509_CERT container and an associated
   buffer. The number of certificates depends on the remote host, but usually at least
   two certificates will be sent – the identity certificate for the host and the
   certificate that issued the identity certificate. */
NX_SECURE_X509_CERT remote_certificate, remote_issuer;

UCHAR remote_cert_buffer[2000];
UCHAR remote_issuer_buffer[2000];

/* Certificate information for server and client (see NetX Secure TLS reference on X.509
    certificates for more information). Arrays are populated with binary versions Of
    certificates and keys and the corresponding “len” variables are assigned the lengths
    of that data. Trusted certificates do not need a private key. */
const UCHAR server_cert_der[] = { … };
const UINT  server_cert_derlen = … ;
const UCHAR server_cert_key_der[] = { … };
const UINT  server_cert_key_derlen = … ;

const UCHAR trusted_cert_der[] = { … };
const UINT  trusted_cert_derlen = … ;


/* Define function prototypes.  */

void    thread_0_entry(ULONG thread_input);
VOID    _fx_ram_driver(FX_MEDIA *media_ptr) ;
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
UINT    authentication_check(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
             CHAR *resource, CHAR **name, CHAR **password, CHAR **realm);
UINT tls_setup_callback(NX_WEB_HTTP_CLIENT *client_ptr,
   NX_SECURE_TLS_SESSION *tls_session);

/* Define the application's authentication check.  This is called by
   the HTTP server whenever a new request is received.  */
UINT  authentication_check(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
            CHAR *resource, CHAR **name, CHAR **password, CHAR **realm)
{
    /* Just use a simple name, password, and realm for all
       requests and resources.  */
    *name =     "name";
    *password = "password";
    *realm =    "NetX Web HTTP demo";

    /* Request basic authentication.  */
    return(NX_WEB_HTTP_BASIC_AUTHENTICATE);
}

/* Define the TLS setup callback for HTTPS Client. This function is invoked when the
   HTTPS client is started – all TLS per-session initialization should go in here. */
UINT tls_setup_callback(NX_WEB_HTTP_CLIENT *client_ptr,
  NX_SECURE_TLS_SESSION *tls_session)
{
    UINT status;

    /* Initialize and create TLS session. */
    nx_secure_tls_session_create(tls_session, &nx_crypto_tls_ciphers,
        crypto_metadata, sizeof(crypto_metadata));

    /* Allocate space for packet reassembly. */
    nx_secure_tls_session_packet_buffer_set(tls_session, tls_packet_buffer,
        sizeof(tls_packet_buffer));


    /* Add a CA Certificate to our trusted store for verifying incoming server
        certificates. */
    nx_secure_x509_certificate_initialize(&trusted_certificate, trusted_cert_der,
        trusted_cert_der_len, NX_NULL, 0, NULL, 0,
        NX_SECURE_X509_KEY_TYPE_NONE);
    nx_secure_tls_trusted_certificate_add(tls_session, &trusted_certificate);

    /* Need to allocate space for the certificate coming in from the remote host. */
    nx_secure_tls_remote_certificate_allocate(tls_session, &remote_certificate,
        remote_cert_buffer, sizeof(remote_cert_buffer));
    nx_secure_tls_remote_certificate_allocate(tls_session,
        &remote_issuer, remote_issuer_buffer,
        sizeof(remote_issuer_buffer));

    return(NX_SUCCESS);
 }

/* Define main entry point.  */

 int main()
 {
     /* Enter the ThreadX kernel.  */
     tx_kernel_enter();
 }

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

    CHAR    *pointer;

    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the main thread.  */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system.  */
    nx_system_initialize();

    /* Create packet pool.  */
    nx_packet_pool_create(&pool_0, "NetX Packet Pool 0",
        600, pointer, 8192);
    pointer = pointer + 8192;

    /* Create an IP instance.  */
    nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(1, 2, 3, 4),
        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
        pointer, 4096, 1);
    pointer =  pointer + 4096;

    /* Create another packet pool. */
    nx_packet_pool_create(&pool_1, "NetX Packet Pool 1", 600, pointer, 8192);
    pointer = pointer + 8192;

    /* Create another IP instance.  */
    nx_ip_create(&ip_1, "NetX IP Instance 1", IP_ADDRESS(1, 2, 3, 5),
        0xFFFFFF00UL, &pool_1, _nx_ram_network_driver,
        pointer, 4096, 1);
    pointer = pointer + 4096;

    /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
    nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable ARP and supply ARP cache memory for IP Instance 1.  */
    nx_arp_enable(&ip_1, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable TCP processing for both IP instances.  */
    nx_tcp_enable(&ip_0);
    nx_tcp_enable(&ip_1);

    /* Open the RAM disk.  */
    fx_media_open(&ram_disk, "RAM DISK",
        _fx_ram_driver, ram_disk_memory, pointer, 4096);
    pointer += 4096;

    /* Create the NetX Web HTTP Server.  */
    nx_web_http_server_create(&my_server, "My HTTP Server", &ip_1,
        NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
        pointer, 4096, &pool_1, authentication_check, NX_NULL);
    pointer = pointer + 4096;

    /* The TLS server needs an identity certificate which is imported as a binary DER-
        encoded X.509 certificate and its associated private key (e.g. DER-encoded PKCS#1
        RSA private key). */
    nx_secure_x509_certificate_initialize(&server_certificate, server_cert_der,
        server_cert_der_len, NX_NULL, 0,
        server_cert_key_der, server_cert_key_der_len,
        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Setup TLS session data for the TCP server.
        This enables TLS and HTTPS for the server.  */
    nx_web_http_server_secure_configure(&my_server, &nx_crypto_tls_ciphers,
        crypto_metadata, sizeof(crypto_metadata), server_tls_packet_buffer,
        sizeof(server_tls_packet_buffer), &server_certificate, NX_NULL, 0,
        NX_NULL, 0, NX_NULL, 0);

    /* Start the HTTP Server.  */
    nx_web_http_server_start(&my_server);
}

/* Define the test thread.  */
void    thread_0_entry(ULONG thread_input)
{
    NX_PACKET   *my_packet;
    UINT        status;

    /* Create an HTTP client instance.  */
    status = nx_web_http_client_create(&my_client, "My Client", &ip_0, &pool_0, 600);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Prepare to send the simple 103-byte HTML file to the Server over HTTPS.  */
    status = nx_web_http_client_put_secure_start(&my_client, IP_ADDRESS(1,2,3,5),
        NX_WEB_HTTPS_SERVER_PORT, "/test.htm", "name", "password", 103, tls_setup_callback, 50);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Allocate a packet.  */
     tatus = nx_web_http_client_request_packet_allocate(&pool_0, &my_packet,
        NX_TCP_PACKET, NX_WAIT_FOREVER);

    /* Check status.  */
    if (status != NX_SUCCESS)
        return;

    /* Build a simple 103-byte HTML page.  */
    nx_packet_data_append(my_packet, "<HTML>\r\n", 8,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet,
        "<HEAD><TITLE>NetX HTTP Test</TITLE></HEAD>\r\n", 44,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "<BODY>\r\n", 8,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "<H1>NetX Test Page</H1>\r\n", 25,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "</BODY>\r\n", 9,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "</HTML>\r\n", 9,
        &pool_0, NX_WAIT_FOREVER);

    /* Complete the PUT by writing the total length.  */
    status =  nx_web_http_client_put_packet(&my_client, my_packet, 50);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Now GET the file back!  */
    status =  nx_web_http_client_get_secure_start(&my_client, IP_ADDRESS(1,2,3,5),
        NX_WEB_HTTPS_SERVER_PORT, "/test.htm",
        "name", "password", tls_setup_callback, 50);
 
    /* Check status.  */
    if (status)
        error_counter++;

    /* Get a packet.  */
    status =  nx_web_http_client_response_body_get(&my_client, &my_packet, 20);

    /* Check for an error.  */
    if ((status) || (my_packet -> nx_packet_length != 103))
        error_counter++;

    /* Check to see if we have a packet.  */
    if (status == NX_SUCCESS)
    {

        /* Yes, release it!  */
        nx_packet_release(my_packet);
    }

    /* Make sure TLS shuts down properly. */
    nx_web_http_client_delete(&my_client);

    /* Flush the media.  */
    fx_media_flush(&ram_disk);
}
```

<span data-ttu-id="2e295-150">**Figura 1.1 Exemplo de utilização https com NetX e NetX Secure TLS**</span><span class="sxs-lookup"><span data-stu-id="2e295-150">**Figure 1.1 Example of HTTPS use with NetX and NetX Secure TLS**</span></span>

## <a name="configuration-options"></a><span data-ttu-id="2e295-151">Opções de configuração</span><span class="sxs-lookup"><span data-stu-id="2e295-151">Configuration Options</span></span>

<span data-ttu-id="2e295-152">Existem várias opções de configuração para a construção HTTP para NetX.</span><span class="sxs-lookup"><span data-stu-id="2e295-152">There are several configuration options for building HTTP for NetX.</span></span> <span data-ttu-id="2e295-153">Segue-se uma lista de todas as opções, onde cada uma é descrita em detalhe.</span><span class="sxs-lookup"><span data-stu-id="2e295-153">Following is a list of all options, where each is described in detail.</span></span> <span data-ttu-id="2e295-154">Os valores predefinidos são listados, mas podem ser redefinidos antes da inclusão de *nx_web_http_client.h e nx_web_http_server.h:*</span><span class="sxs-lookup"><span data-stu-id="2e295-154">The default values are listed but can be redefined prior to inclusion of *nx_web_http_client.h and nx_web_http_server.h*:</span></span>

- <span data-ttu-id="2e295-155">**NX_DISABLE_ERROR_CHECKING** Definida, esta opção remove a verificação básica de erros HTTP.</span><span class="sxs-lookup"><span data-stu-id="2e295-155">**NX_DISABLE_ERROR_CHECKING** Defined, this option removes the basic HTTP error checking.</span></span> <span data-ttu-id="2e295-156">É normalmente usado após a depurada aplicação.</span><span class="sxs-lookup"><span data-stu-id="2e295-156">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="2e295-157">**NX_WEB_HTTP_DIGEST_ENABLE** Se definido, a autenticação utilizando a digestão MD5 está ativada no servidor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2e295-157">**NX_WEB_HTTP_DIGEST_ENABLE** If defined, authentication using the MD5 digest is enabled on the HTTPS Server.</span></span> <span data-ttu-id="2e295-158">Por defeito não está definido.</span><span class="sxs-lookup"><span data-stu-id="2e295-158">By default it is not defined.</span></span>
- <span data-ttu-id="2e295-159">**NX_WEB_HTTP_SERVER_PRIORITY** A prioridade da linha do servidor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2e295-159">**NX_WEB_HTTP_SERVER_PRIORITY** The priority of the HTTPS Server thread.</span></span> <span data-ttu-id="2e295-160">Por predefinição, este valor é definido como 16 para especificar a prioridade 16.</span><span class="sxs-lookup"><span data-stu-id="2e295-160">By default, this value is defined as 16 to specify priority 16.</span></span>
- <span data-ttu-id="2e295-161">**NX_WEB_HTTP_NO_FILEX** Definida, esta opção fornece um canhoto para dependências de FileX.</span><span class="sxs-lookup"><span data-stu-id="2e295-161">**NX_WEB_HTTP_NO_FILEX** Defined, this option provides a stub for FileX dependencies.</span></span> <span data-ttu-id="2e295-162">O Cliente HTTPS funcionará sem qualquer alteração se esta opção for definida.</span><span class="sxs-lookup"><span data-stu-id="2e295-162">The HTTPS Client will function without any change if this option is defined.</span></span> <span data-ttu-id="2e295-163">O SERVIDOR HTTPS terá de ser modificado ou o utilizador terá de criar um punhado de serviços FileX para funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="2e295-163">The HTTPS Server will need to either be modified or the user will have to create a handful of FileX services in order to function properly.</span></span>
- <span data-ttu-id="2e295-164">**NX_WEB_HTTP_TYPE_OF_SERVICE** Tipo de serviço necessário para os pedidos HTTPS TCP.</span><span class="sxs-lookup"><span data-stu-id="2e295-164">**NX_WEB_HTTP_TYPE_OF_SERVICE** Type of service required for the HTTPS TCP requests.</span></span> <span data-ttu-id="2e295-165">Por predefinição, este valor é definido como NX_IP_NORMAL para indicar o serviço normal de pacotes IP.</span><span class="sxs-lookup"><span data-stu-id="2e295-165">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="2e295-166">**NX_WEB_HTTP_SERVER_THREAD_TIME_SLICE** O número de marcações de temporizador que o fio do Servidor é permitido funcionar antes de ceder a fios da mesma prioridade.</span><span class="sxs-lookup"><span data-stu-id="2e295-166">**NX_WEB_HTTP_SERVER_THREAD_TIME_SLICE** The number of timer ticks the Server thread is allowed to run before yielding to threads of the same priority.</span></span> <span data-ttu-id="2e295-167">O valor predefinido é 2.</span><span class="sxs-lookup"><span data-stu-id="2e295-167">The default value is 2.</span></span> <span data-ttu-id="2e295-168">Note que esta opção está depreciada.</span><span class="sxs-lookup"><span data-stu-id="2e295-168">Note this option is deprecated.</span></span>
- <span data-ttu-id="2e295-169">**NX_WEB_HTTP_FRAGMENT_OPTION** Fragmento ativar pedidos HTTP TCP.</span><span class="sxs-lookup"><span data-stu-id="2e295-169">**NX_WEB_HTTP_FRAGMENT_OPTION** Fragment enable for HTTP TCP requests.</span></span> <span data-ttu-id="2e295-170">Por predefinição, este valor é NX_DONT_FRAGMENT para desativar a fragmentação HTTP TCP.</span><span class="sxs-lookup"><span data-stu-id="2e295-170">By default, this value is NX_DONT_FRAGMENT to disable HTTP TCP fragmenting.</span></span>
- <span data-ttu-id="2e295-171">**NX_WEB_HTTP_SERVER_WINDOW_SIZE** Tamanho da janela da tomada do servidor.</span><span class="sxs-lookup"><span data-stu-id="2e295-171">**NX_WEB_HTTP_SERVER_WINDOW_SIZE** Server socket window size.</span></span> <span data-ttu-id="2e295-172">Por padrão, este valor é 2048 bytes.</span><span class="sxs-lookup"><span data-stu-id="2e295-172">By default, this value is 2048 bytes.</span></span>
- <span data-ttu-id="2e295-173">**NX_WEB_HTTP_TIME_TO_LIVE** Especifica o número de routers que este pacote pode passar antes de ser descartado.</span><span class="sxs-lookup"><span data-stu-id="2e295-173">**NX_WEB_HTTP_TIME_TO_LIVE** Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="2e295-174">O valor predefinido é definido para 0x80.</span><span class="sxs-lookup"><span data-stu-id="2e295-174">The default value is set to 0x80.</span></span>
- <span data-ttu-id="2e295-175">**NX_WEB_HTTP_SERVER_TIMEOUT** Especifica o número de carraças ThreadX que os serviços internos vão suspender.</span><span class="sxs-lookup"><span data-stu-id="2e295-175">**NX_WEB_HTTP_SERVER_TIMEOUT** Specifies the number of ThreadX ticks that internal services will suspend for.</span></span> <span data-ttu-id="2e295-176">O valor predefinido é definido para 10 segundos (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="2e295-176">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="2e295-177">**NX_WEB_HTTP_SERVER_TIMEOUT_ACCEPT** Especifica o número de carraças threadX que os serviços internos suspenderão em chamadas internas *nx_tcp_server_socket_accept().*</span><span class="sxs-lookup"><span data-stu-id="2e295-177">**NX_WEB_HTTP_SERVER_TIMEOUT_ACCEPT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_server_socket_accept()* calls.</span></span> <span data-ttu-id="2e295-178">O valor predefinido é definido para (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="2e295-178">The default value is set to (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="2e295-179">**NX_WEB_HTTP_SERVER_TIMEOUT_DISCONNECT** Especifica o número de carraças threadX que os serviços internos suspenderão em chamadas internas *nx_tcp_socket_disconnect().*</span><span class="sxs-lookup"><span data-stu-id="2e295-179">**NX_WEB_HTTP_SERVER_TIMEOUT_DISCONNECT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_disconnect()* calls.</span></span> <span data-ttu-id="2e295-180">O valor predefinido é definido para 10 segundos (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="2e295-180">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="2e295-181">**NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE** Especifica o número de carraças threadX que os serviços internos suspenderão em chamadas internas *nx_tcp_socket_receive().*</span><span class="sxs-lookup"><span data-stu-id="2e295-181">**NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_receive()* calls.</span></span> <span data-ttu-id="2e295-182">O valor predefinido é definido para 10 segundos (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="2e295-182">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="2e295-183">**NX_WEB_HTTP_SERVER_TIMEOUT_SEND** Especifica o número de carraças threadX que os serviços internos suspenderão em chamadas internas *nx_tcp_socket_send().*</span><span class="sxs-lookup"><span data-stu-id="2e295-183">**NX_WEB_HTTP_SERVER_TIMEOUT_SEND** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_send()* calls.</span></span> <span data-ttu-id="2e295-184">O valor predefinido é definido para 10 segundos (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="2e295-184">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="2e295-185">**NX_WEB_HTTP_MAX_HEADER_FIELD** **Especifica o tamanho máximo do campo de cabeçalho HTTP. O valor predefinido é de 256.**</span><span class="sxs-lookup"><span data-stu-id="2e295-185">**NX_WEB_HTTP_MAX_HEADER_FIELD** **Specifies the maximum size of the HTTP header field. The default value is 256.**</span></span>
- <span data-ttu-id="2e295-186">\*\*NX_WEB_HTTP_MULTIPART_ENABLE \*\* \*\*Se definido, permite que o SERVIDOR HTTPS suporte pedidos HTTP multipart.</span><span class="sxs-lookup"><span data-stu-id="2e295-186">\*\*NX_WEB_HTTP_MULTIPART_ENABLE \*\* \*\*If defined, enables HTTPS Server to support multipart HTTP requests.</span></span> **
- <span data-ttu-id="2e295-187">**NX_WEB_HTTP_SERVER_MAX_PENDING** Especifica o número de ligações que podem ser em fila para o servidor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2e295-187">**NX_WEB_HTTP_SERVER_MAX_PENDING** Specifies the number of connections that can be queued for the HTTPS Server.</span></span> <span data-ttu-id="2e295-188">O valor predefinido é definido para o dobro do número máximo de sessões de servidor.</span><span class="sxs-lookup"><span data-stu-id="2e295-188">The default value is set to twice the maximum number of server sessions.</span></span>
- <span data-ttu-id="2e295-189">**NX_WEB_HTTP_MAX_RESOURCE** Especifica o número de bytes permitidos num *nome de recurso* fornecido pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="2e295-189">**NX_WEB_HTTP_MAX_RESOURCE** Specifies the number of bytes allowed in a client supplied *resource name*.</span></span> <span data-ttu-id="2e295-190">O valor predefinido é definido para 40.</span><span class="sxs-lookup"><span data-stu-id="2e295-190">The default value is set to 40.</span></span>
- <span data-ttu-id="2e295-191">**NX_WEB_HTTP_MAX_NAME** Especifica o número de bytes permitidos num nome *de utilizador* fornecido pelo cliente .</span><span class="sxs-lookup"><span data-stu-id="2e295-191">**NX_WEB_HTTP_MAX_NAME** Specifies the number of bytes allowed in a client supplied *username*.</span></span> <span data-ttu-id="2e295-192">O valor predefinido é definido para 20.</span><span class="sxs-lookup"><span data-stu-id="2e295-192">The default value is set to 20.</span></span>
- <span data-ttu-id="2e295-193">**NX_WEB_HTTP_MAX_PASSWORD** Especifica o número de bytes permitidos numa *senha* fornecida pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="2e295-193">**NX_WEB_HTTP_MAX_PASSWORD** Specifies the number of bytes allowed in a client supplied *password*.</span></span> <span data-ttu-id="2e295-194">O valor predefinido é definido para 20.</span><span class="sxs-lookup"><span data-stu-id="2e295-194">The default value is set to 20.</span></span>
- <span data-ttu-id="2e295-195">**NX_WEB_HTTP_SERVER_SESSION_MAX** Especifica o número de sessões simultâneas para um servidor HTTP ou HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2e295-195">**NX_WEB_HTTP_SERVER_SESSION_MAX** Specifies the number of simultaneous sessions for an HTTP or HTTPS Server.</span></span> <span data-ttu-id="2e295-196">Para cada sessão é atribuída uma tomada TCP e uma sessão TLS (se HTTPS estiver ativado).</span><span class="sxs-lookup"><span data-stu-id="2e295-196">A TCP socket and a TLS session (if HTTPS is enabled) are allocated for each session.</span></span> <span data-ttu-id="2e295-197">O valor predefinido é definido para 2.</span><span class="sxs-lookup"><span data-stu-id="2e295-197">The default value is set to 2.</span></span>
- <span data-ttu-id="2e295-198">**NX_WEB_HTTPS_ENABLE** Se definido, este macro permite TLS e HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2e295-198">**NX_WEB_HTTPS_ENABLE** If defined, this macro enables TLS and HTTPS.</span></span> <span data-ttu-id="2e295-199">Deixe indefinidos para libertar recursos se apenas o texto simples HTTP for desejado.</span><span class="sxs-lookup"><span data-stu-id="2e295-199">Leave undefined to free up resources if only plaintext HTTP is desired.</span></span> <span data-ttu-id="2e295-200">Por padrão, esta macro não está definida.</span><span class="sxs-lookup"><span data-stu-id="2e295-200">By default, this macro is not defined.</span></span>
- <span data-ttu-id="2e295-201">**NX_WEB_HTTPS_KEEPALIVE_DISABLE** Se definido, esta macro desativa a funcionalidade HTTP Keep-alive.</span><span class="sxs-lookup"><span data-stu-id="2e295-201">**NX_WEB_HTTPS_KEEPALIVE_DISABLE** If defined, this macro disables HTTP keep-alive feature.</span></span> <span data-ttu-id="2e295-202">Por padrão, esta macro não está definida.</span><span class="sxs-lookup"><span data-stu-id="2e295-202">By default, this macro is not defined.</span></span>
- <span data-ttu-id="2e295-203">**NX_WEB_HTTP_SERVER_MIN_PACKET_SIZE** Especifica o tamanho mínimo dos pacotes na piscina especificado na criação do servidor.</span><span class="sxs-lookup"><span data-stu-id="2e295-203">**NX_WEB_HTTP_SERVER_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at server creation.</span></span> <span data-ttu-id="2e295-204">O tamanho mínimo é necessário para garantir que o cabeçalho HTTP completo pode ser contido num pacote.</span><span class="sxs-lookup"><span data-stu-id="2e295-204">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="2e295-205">O valor predefinido é definido para 600.</span><span class="sxs-lookup"><span data-stu-id="2e295-205">The default value is set to 600.</span></span>
- <span data-ttu-id="2e295-206">**NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE** Especifica o tamanho mínimo dos pacotes na piscina especificado na criação do Cliente.</span><span class="sxs-lookup"><span data-stu-id="2e295-206">**NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at Client creation.</span></span> <span data-ttu-id="2e295-207">O tamanho mínimo é necessário para garantir que o cabeçalho HTTP completo pode ser contido num pacote.</span><span class="sxs-lookup"><span data-stu-id="2e295-207">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="2e295-208">O valor predefinido é definido para 600.</span><span class="sxs-lookup"><span data-stu-id="2e295-208">The default value is set to 600.</span></span>
- <span data-ttu-id="2e295-209">**NX_WEB_HTTP_SERVER_RETRY_SECONDS** Desajuste o tempo limite de retransmissão da tomada do servidor em segundos.</span><span class="sxs-lookup"><span data-stu-id="2e295-209">**NX_WEB_HTTP_SERVER_RETRY_SECONDS** Set the Server socket retransmission timeout in seconds.</span></span> <span data-ttu-id="2e295-210">O valor predefinido é definido para 2.</span><span class="sxs-lookup"><span data-stu-id="2e295-210">The default value is set to 2.</span></span>
- <span data-ttu-id="2e295-211">**NX_WEB_HTTP_ SERVER_RETRY_MAX** Isto define o número máximo de retransmissão na tomada do Servidor.</span><span class="sxs-lookup"><span data-stu-id="2e295-211">**NX_WEB_HTTP_ SERVER_RETRY_MAX** This sets the maximum number of retransmissions on Server socket.</span></span> <span data-ttu-id="2e295-212">O valor predefinido é definido para 10.</span><span class="sxs-lookup"><span data-stu-id="2e295-212">The default value is set to 10.</span></span>
- <span data-ttu-id="2e295-213">**NX_WEB_HTTP_ SERVER_RETRY_SHIFT** Este valor é utilizado para definir o próximo tempo limite de retransmissão.</span><span class="sxs-lookup"><span data-stu-id="2e295-213">**NX_WEB_HTTP_ SERVER_RETRY_SHIFT** This value is used to set the next retransmission timeout.</span></span> <span data-ttu-id="2e295-214">O tempo limite atual é multiplicado pelo número de retransmissão até agora, alterado pelo valor do intervalo de tempo da tomada.</span><span class="sxs-lookup"><span data-stu-id="2e295-214">The current timeout is multiplied by the number of retransmissions thus far, shifted by the value of the socket timeout shift.</span></span> <span data-ttu-id="2e295-215">O valor predefinido é definido para 1 para duplicar o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="2e295-215">The default value is set to 1 for doubling the timeout.</span></span>
- <span data-ttu-id="2e295-216">**NX_WEB_HTTP_SERVER_RETRY_TRANSMIT_QUEUE_DEPTH** Isto especifica o número máximo de pacotes que podem ser encadeados na fila de retransmissão da tomada do Servidor.</span><span class="sxs-lookup"><span data-stu-id="2e295-216">**NX_WEB_HTTP_SERVER_RETRY_TRANSMIT_QUEUE_DEPTH** This specifies the maximum number of packets that can be enqueued on the Server socket retransmission queue.</span></span> <span data-ttu-id="2e295-217">Se o número de pacotes encadeados chegar a este número, não podem ser enviados mais pacotes até que um ou mais pacotes enqueados sejam libertados.</span><span class="sxs-lookup"><span data-stu-id="2e295-217">If the number of packets enqueued reaches this number, no more packets can be sent until one or more enqueued packets are released.</span></span> <span data-ttu-id="2e295-218">O valor predefinido é definido para 20.</span><span class="sxs-lookup"><span data-stu-id="2e295-218">The default value is set to 20.</span></span>
