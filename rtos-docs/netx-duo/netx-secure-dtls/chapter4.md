---
title: Capítulo 4 - Descrição dos serviços Azure RTOS NetX Secure DTLS
description: Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX Secure DTLS listados por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e795a5fa35a4590e508c7fe2eec53f5494809657
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825688"
---
# <a name="chapter-4-description-of-azure-rtos-netx-secure-dtls-services"></a><span data-ttu-id="41ccc-103">Capítulo 4: Descrição dos serviços Azure RTOS NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="41ccc-103">Chapter 4: Description of Azure RTOS NetX Secure DTLS services</span></span>

<span data-ttu-id="41ccc-104">Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX Secure DTLS (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="41ccc-104">This chapter contains a description of all Azure RTOS NetX Secure DTLS services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="41ccc-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pela macro **NX_SECURE_DISABLE_ERROR_CHECKING** que é utilizada para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="41ccc-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_SECURE_DISABLE_ERROR_CHECKING** macro that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="41ccc-106">nx_secure_dtls_client_session_start</span><span class="sxs-lookup"><span data-stu-id="41ccc-106">nx_secure_dtls_client_session_start</span></span>](#nx_secure_dtls_client_session_start)
- [<span data-ttu-id="41ccc-107">nx_secure_dtls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="41ccc-107">nx_secure_dtls_packet_allocate</span></span>](#nx_secure_dtls_packet_allocate)
- [<span data-ttu-id="41ccc-108">nx_secure_dtls_psk_add</span><span class="sxs-lookup"><span data-stu-id="41ccc-108">nx_secure_dtls_psk_add</span></span>](#nx_secure_dtls_psk_add)
- [<span data-ttu-id="41ccc-109">nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="41ccc-109">nx_secure_dtls_server_create</span></span>](#nx_secure_dtls_server_create)
- [<span data-ttu-id="41ccc-110">nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="41ccc-110">nx_secure_dtls_server_delete</span></span>](#nx_secure_dtls_server_delete)
- [<span data-ttu-id="41ccc-111">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="41ccc-111">nx_secure_dtls_server_local_certificate_add</span></span>](#nx_secure_dtls_server_local_certificate_add)
- [<span data-ttu-id="41ccc-112">nx_secure_dtls_server_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="41ccc-112">nx_secure_dtls_server_local_certificate_remove</span></span>](#nx_secure_dtls_server_local_certificate_remove)
- [<span data-ttu-id="41ccc-113">nx_secure_dtls_server_notify_set</span><span class="sxs-lookup"><span data-stu-id="41ccc-113">nx_secure_dtls_server_notify_set</span></span>](#nx_secure_dtls_server_notify_set)
- [<span data-ttu-id="41ccc-114">nx_secure_dtls_server_psk_add</span><span class="sxs-lookup"><span data-stu-id="41ccc-114">nx_secure_dtls_server_psk_add</span></span>](#nx_secure_dtls_server_psk_add)
- [<span data-ttu-id="41ccc-115">nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="41ccc-115">nx_secure_dtls_server_session_send</span></span>](#nx_secure_dtls_server_session_send)
- [<span data-ttu-id="41ccc-116">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="41ccc-116">nx_secure_dtls_server_session_start</span></span>](#nx_secure_dtls_server_session_start)
- [<span data-ttu-id="41ccc-117">nx_secure_dtls_server_start</span><span class="sxs-lookup"><span data-stu-id="41ccc-117">nx_secure_dtls_server_start</span></span>](#nx_secure_dtls_server_start)
- [<span data-ttu-id="41ccc-118">nx_secure_dtls_server_stop</span><span class="sxs-lookup"><span data-stu-id="41ccc-118">nx_secure_dtls_server_stop</span></span>](#nx_secure_dtls_server_stop)
- [<span data-ttu-id="41ccc-119">nx_secure_dtls_server_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="41ccc-119">nx_secure_dtls_server_trusted_certificate_add</span></span>](#nx_secure_dtls_server_trusted_certificate_add)
- [<span data-ttu-id="41ccc-120">nx_secure_dtls_server_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="41ccc-120">nx_secure_dtls_server_trusted_certificate_remove</span></span>](#nx_secure_dtls_server_trusted_certificate_remove)
- [<span data-ttu-id="41ccc-121">nx_secure_dtls_server_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="41ccc-121">nx_secure_dtls_server_x509_client_verify_configure</span></span>](#nx_secure_dtls_server_x509_client_verify_configure)
- [<span data-ttu-id="41ccc-122">nx_secure_dtls_server_x509_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="41ccc-122">nx_secure_dtls_server_x509_client_verify_disable</span></span>](#nx_secure_dtls_server_x509_client_verify_disable)
- [<span data-ttu-id="41ccc-123">nx_secure_dtls_session_client_info_get</span><span class="sxs-lookup"><span data-stu-id="41ccc-123">nx_secure_dtls_session_client_info_get</span></span>](#nx_secure_dtls_session_client_info_get)
- [<span data-ttu-id="41ccc-124">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="41ccc-124">nx_secure_dtls_session_create</span></span>](#nx_secure_dtls_session_create)
- [<span data-ttu-id="41ccc-125">nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="41ccc-125">nx_secure_dtls_session_delete</span></span>](#nx_secure_dtls_session_delete)
- [<span data-ttu-id="41ccc-126">nx_secure_dtls_session_end</span><span class="sxs-lookup"><span data-stu-id="41ccc-126">nx_secure_dtls_session_end</span></span>](#nx_secure_dtls_session_end)
- [<span data-ttu-id="41ccc-127">nx_secure_dtls_session_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="41ccc-127">nx_secure_dtls_session_local_certificate_add</span></span>](#nx_secure_dtls_session_local_certificate_add)
- [<span data-ttu-id="41ccc-128">nx_secure_dtls_session_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="41ccc-128">nx_secure_dtls_session_local_certificate_remove</span></span>](#nx_secure_dtls_session_local_certificate_remove)
- [<span data-ttu-id="41ccc-129">nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="41ccc-129">nx_secure_dtls_session_receive</span></span>](#nx_secure_dtls_session_receive)
- [<span data-ttu-id="41ccc-130">nx_secure_dtls_session_reset</span><span class="sxs-lookup"><span data-stu-id="41ccc-130">nx_secure_dtls_session_reset</span></span>](#nx_secure_dtls_session_reset)
- [<span data-ttu-id="41ccc-131">nx_secure_dtls_ session_send</span><span class="sxs-lookup"><span data-stu-id="41ccc-131">nx_secure_dtls_ session_send</span></span>](#nx_secure_dtls_-session_send)
- [<span data-ttu-id="41ccc-132">nx_secure_dtls_session_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="41ccc-132">nx_secure_dtls_session_trusted_certificate_add</span></span>](#nx_secure_dtls_session_trusted_certificate_add)
- [<span data-ttu-id="41ccc-133">nx_secure_dtls_session_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="41ccc-133">nx_secure_dtls_session_trusted_certificate_remove</span></span>](#nx_secure_dtls_session_trusted_certificate_remove)


## <a name="nx_secure_dtls_client_session_start"></a><span data-ttu-id="41ccc-134">nx_secure_dtls_client_session_start</span><span class="sxs-lookup"><span data-stu-id="41ccc-134">nx_secure_dtls_client_session_start</span></span>

<span data-ttu-id="41ccc-135">Inicie uma Sessão de Clientes DTLS Segura netX</span><span class="sxs-lookup"><span data-stu-id="41ccc-135">Start a NetX Secure DTLS Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-136">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-136">Prototype</span></span>

```C
UINT nx_secure_dtls_client_session_start(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        NX_UDP_SOCKET *udp_socket,
                        NXD_ADDRESS *ip_address, UINT port,
                        UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="41ccc-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-137">Description</span></span>

<span data-ttu-id="41ccc-138">Este serviço inicia uma sessão de Cliente DTLS, conectando-se ao servidor no endereço IP fornecido e na porta UDP, utilizando a tomada UDP fornecida para comunicações de rede.</span><span class="sxs-lookup"><span data-stu-id="41ccc-138">This service starts a DTLS Client session, connecting to the server at the provided IP address and UDP port, using the provided UDP socket for network communications.</span></span>

<span data-ttu-id="41ccc-139">O bloco de controlo de sessão DTLS deve ser inicializado antes de ligar para este serviço utilizando nx_secure_dtls_session_create.</span><span class="sxs-lookup"><span data-stu-id="41ccc-139">The DTLS session control block must be initialized prior to calling this service using nx_secure_dtls_session_create.</span></span> <span data-ttu-id="41ccc-140">Além disso, o Cliente DTLS exige que pelo menos um certificado de CA fidedigno tenha sido adicionado à sessão usando nx_secure_dtls_session_trusted_certificate_add ou Chaves Pré-Partilhadas estejam ativadas e configuradas.</span><span class="sxs-lookup"><span data-stu-id="41ccc-140">Additionally, the DTLS Client requires that at least one trusted CA certificate has been added to the session using nx_secure_dtls_session_trusted_certificate_add or Pre-Shared Keys are enabled and configured.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-141">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-141">Parameters</span></span>

- <span data-ttu-id="41ccc-142">**dtls_session** Ponteiro para uma estrutura de Sessão DTLS que foi inicializada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="41ccc-142">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>
- <span data-ttu-id="41ccc-143">**udp_socket** Tomada UDP inicializada que será usada para estabelecer comunicações de rede com o servidor DTLS remoto.</span><span class="sxs-lookup"><span data-stu-id="41ccc-143">**udp_socket** Initialized UDP socket that will be used to establish network communications with the remote DTLS server.</span></span>
- <span data-ttu-id="41ccc-144">**ip_address** Ponteiro para a estrutura do endereço IP que contém o endereço do servidor DTLS remoto.</span><span class="sxs-lookup"><span data-stu-id="41ccc-144">**ip_address** Pointer to IP address structure containing the address of the remote DTLS server.</span></span>
- <span data-ttu-id="41ccc-145">**porto** Tomada UDP inicializada que será usada para estabelecer comunicações de rede com o servidor DTLS remoto.</span><span class="sxs-lookup"><span data-stu-id="41ccc-145">**port** Initialized UDP socket that will be used to establish network communications with the remote DTLS server.</span></span>
- <span data-ttu-id="41ccc-146">**wait_option** Opção de suspensão para tentativa de ligação.</span><span class="sxs-lookup"><span data-stu-id="41ccc-146">**wait_option** Suspension option for connection attempt.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-147">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-147">Return Values</span></span>

- <span data-ttu-id="41ccc-148">**NX_SUCCESS** (0x00) Atribuição bem sucedida de certificado à sessão.</span><span class="sxs-lookup"><span data-stu-id="41ccc-148">**NX_SUCCESS** (0x00) Successful assignment of certificate to session.</span></span>
- <span data-ttu-id="41ccc-149">**NX_NOT_CONNECTED** (0x38) O servidor não pode ser alcançado no endereço e na porta dado.</span><span class="sxs-lookup"><span data-stu-id="41ccc-149">**NX_NOT_CONNECTED** (0x38) The server cannot be reached at the given address and port.</span></span>
- <span data-ttu-id="41ccc-150">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) Um tipo de mensagem TLS/DTLS recebido está incorreto.</span><span class="sxs-lookup"><span data-stu-id="41ccc-150">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS/DTLS message type is incorrect.</span></span>
- <span data-ttu-id="41ccc-151">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) Uma cifra fornecida pelo hospedeiro remoto não é suportada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-151">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="41ccc-152">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) O processamento de mensagens durante o aperto de mão TLS falhou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-152">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="41ccc-153">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Uma mensagem recebida falhou numa verificação de HASH MAC.</span><span class="sxs-lookup"><span data-stu-id="41ccc-153">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a hash MAC check.</span></span>
- <span data-ttu-id="41ccc-154">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Um envio de tomada TCP subjacente falhou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-154">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="41ccc-155">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Uma mensagem recebida tinha um campo de comprimento inválido.</span><span class="sxs-lookup"><span data-stu-id="41ccc-155">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="41ccc-156">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) Uma mensagem ChangeCipherSpec recebida estava incorreta.</span><span class="sxs-lookup"><span data-stu-id="41ccc-156">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="41ccc-157">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) Um certificado TLS de entrada é inutilizável para identificar o servidor DTLS remoto.</span><span class="sxs-lookup"><span data-stu-id="41ccc-157">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) An incoming TLS certificate is unusable for identifying the remote DTLS server.</span></span>
- <span data-ttu-id="41ccc-158">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) A cifra de chave pública fornecida pelo hospedeiro remoto não é suportada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-158">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="41ccc-159">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) O anfitrião remoto não indicou cifrasuites que sejam suportadas pela pilha DTLS NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="41ccc-159">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure DTLS stack.</span></span>
- <span data-ttu-id="41ccc-160">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Uma mensagem DTLS recebida tinha uma versão DTLS desconhecida no seu cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="41ccc-160">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received DTLS message had an unknown DTLS version in its header.</span></span>
- <span data-ttu-id="41ccc-161">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Uma mensagem DTLS recebida tinha uma versão DTLS conhecida mas não suportada no seu cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="41ccc-161">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received DTLS message had a known but unsupported DTLS version in its header.</span></span>
- <span data-ttu-id="41ccc-162">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Uma atribuição interna de pacotes TLS falhou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-162">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="41ccc-163">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) O anfitrião remoto forneceu um certificado inválido.</span><span class="sxs-lookup"><span data-stu-id="41ccc-163">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="41ccc-164">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) O anfitrião remoto enviou um alerta indicando um erro e terminando a sessão TLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-164">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="41ccc-165">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) Uma entrada na tabela cifrasumita tinha um ponteiro de função NU.</span><span class="sxs-lookup"><span data-stu-id="41ccc-165">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) An entry in the ciphersuite table had a NULL function pointer.</span></span>
- <span data-ttu-id="41ccc-166">**NX_PTR_ERROR** (0x07) Sessão inválida, tomada ou ponteiro de endereço.</span><span class="sxs-lookup"><span data-stu-id="41ccc-166">**NX_PTR_ERROR** (0x07) Invalid session, socket, or address pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-167">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-167">Allowed From</span></span>

<span data-ttu-id="41ccc-168">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-168">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-169">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-169">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-170">See Also</span></span>

- <span data-ttu-id="41ccc-171">nx_secure_dtls_session_receive, nx_secure_dtls_session_send,</span><span class="sxs-lookup"><span data-stu-id="41ccc-171">nx_secure_dtls_session_receive, nx_secure_dtls_session_send,</span></span>
- <span data-ttu-id="41ccc-172">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="41ccc-172">nx_secure_dtls_session_create</span></span>

## <a name="nx_secure_dtls_packet_allocate"></a><span data-ttu-id="41ccc-173">nx_secure_dtls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="41ccc-173">nx_secure_dtls_packet_allocate</span></span>

<span data-ttu-id="41ccc-174">Aloque um pacote para uma Sessão de DTLS NetX Secure</span><span class="sxs-lookup"><span data-stu-id="41ccc-174">Allocate a packet for a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-175">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-175">Prototype</span></span>

```C
UINT  nx_secure_dtls_packet_allocate(
                              NX_SECURE_DTLS_SESSION *session_ptr,
                         NX_PACKET_POOL *pool_ptr,
                         NX_PACKET **packet_ptr,
                              ULONG wait_option);

```

### <a name="description"></a><span data-ttu-id="41ccc-176">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-176">Description</span></span>

<span data-ttu-id="41ccc-177">Este serviço atribui uma NX_PACKET para a sessão DTLS ativa especificada a partir do NX_PACKET_POOL especificado.</span><span class="sxs-lookup"><span data-stu-id="41ccc-177">This service allocates an NX_PACKET for the specified active DTLS session from the specified NX_PACKET_POOL.</span></span> <span data-ttu-id="41ccc-178">Este serviço deve ser chamado pela aplicação para atribuir pacotes de dados a serem enviados através de uma ligação DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-178">This service should be called by the application to allocate data packets to be sent over a DTLS connection.</span></span> <span data-ttu-id="41ccc-179">A sessão DTLS deve ser inicializada antes de ligar para este serviço.</span><span class="sxs-lookup"><span data-stu-id="41ccc-179">The DTLS session must be initialized before calling this service.</span></span>

<span data-ttu-id="41ccc-180">O pacote atribuído é devidamente inicializado de modo a que os dados do cabeçalho e do rodapé DTLS possam ser adicionados após a população dos dados do pacote.</span><span class="sxs-lookup"><span data-stu-id="41ccc-180">The allocated packet is properly initialized so that DTLS header and footer data may be added after the packet data is populated.</span></span> <span data-ttu-id="41ccc-181">O comportamento é idêntico ao *nx_packet_allocate*.</span><span class="sxs-lookup"><span data-stu-id="41ccc-181">The behavior is otherwise identical to *nx_packet_allocate*.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-182">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-182">Parameters</span></span>

- <span data-ttu-id="41ccc-183">**session_ptr** Ponteiro para uma instância de Sessão DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-183">**session_ptr** Pointer to a DTLS Session instance.</span></span>
- <span data-ttu-id="41ccc-184">**pool_ptr** O ponteiro para um NX_PACKET_POOL a partir do qual atribuir o pacote.</span><span class="sxs-lookup"><span data-stu-id="41ccc-184">**pool_ptr** Pointer to an NX_PACKET_POOL from which to allocate the packet.</span></span>
- <span data-ttu-id="41ccc-185">**packet_ptr** Ponteiro de saída para o pacote recém-atribuído.</span><span class="sxs-lookup"><span data-stu-id="41ccc-185">**packet_ptr** Output pointer to the newly-allocated packet.</span></span>
- <span data-ttu-id="41ccc-186">**wait_option** Opção de suspensão para alocação de pacotes.</span><span class="sxs-lookup"><span data-stu-id="41ccc-186">**wait_option** Suspension option for packet allocation.</span></span>


### <a name="return-values"></a><span data-ttu-id="41ccc-187">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-187">Return Values</span></span>

- <span data-ttu-id="41ccc-188">**NX_SUCCESS** (0x00) Atribuição de pacotes bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="41ccc-188">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="41ccc-189">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) A atribuição de pacotes subjacentes falhou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-189">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>
- <span data-ttu-id="41ccc-190">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) A sessão DTLS fornecida não foi inicializada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-190">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied DTLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-191">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-191">Allowed From</span></span>

<span data-ttu-id="41ccc-192">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-192">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-193">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-193">Example</span></span>

```C
/* Allocate a new DTLS packet from the previously created packet pool and
previously initialized DTLS session.   */

status = nx_secure_dtls_packet_allocate(&dtls_session, &pool_0, &packet_ptr,
                                                              NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in
the variable packet_ptr.  */

```

### <a name="see-also"></a><span data-ttu-id="41ccc-194">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-194">See Also</span></span>

- <span data-ttu-id="41ccc-195">nx_secure_x509_certificate_initialize, nx_secure_dtls_session_create,</span><span class="sxs-lookup"><span data-stu-id="41ccc-195">nx_secure_x509_certificate_initialize, nx_secure_dtls_session_create,</span></span>
- <span data-ttu-id="41ccc-196">nx_secure_dtls_session_trusted_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="41ccc-196">nx_secure_dtls_session_trusted_certificate_add,</span></span>
- <span data-ttu-id="41ccc-197">nx_secure_dtls_session_send, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="41ccc-197">nx_secure_dtls_session_send, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="41ccc-198">nx_secure_dtls_session_end, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="41ccc-198">nx_secure_dtls_session_end, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_psk_add"></a><span data-ttu-id="41ccc-199">nx_secure_dtls_psk_add</span><span class="sxs-lookup"><span data-stu-id="41ccc-199">nx_secure_dtls_psk_add</span></span>

<span data-ttu-id="41ccc-200">Adicione uma chave pré-partilhada a uma Sessão de DTLS Segura netX</span><span class="sxs-lookup"><span data-stu-id="41ccc-200">Add a Pre-Shared Key to a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-201">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-201">Prototype</span></span>

```C
UINT  nx_secure_dtls_psk_add(NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a><span data-ttu-id="41ccc-202">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-202">Description</span></span>

<span data-ttu-id="41ccc-203">Este serviço adiciona uma chave pré-partilhada (PSK), a sua cadeia de identidade e uma dica de identidade para um bloco de controlo DTLS Session.</span><span class="sxs-lookup"><span data-stu-id="41ccc-203">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a DTLS Session control block.</span></span> <span data-ttu-id="41ccc-204">O PSK é utilizado em vez de um certificado digital quando as cifrasuites PSK são ativadas e utilizadas.</span><span class="sxs-lookup"><span data-stu-id="41ccc-204">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-205">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-205">Parameters</span></span>

- <span data-ttu-id="41ccc-206">**session_ptr** Ponteiro para uma instância de Sessão DTLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-206">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="41ccc-207">**pre_shared_key** O valor real do PSK.</span><span class="sxs-lookup"><span data-stu-id="41ccc-207">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="41ccc-208">**psk_length** O comprimento do valor PSK.</span><span class="sxs-lookup"><span data-stu-id="41ccc-208">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="41ccc-209">**psk_identity** Uma corda usada para identificar este valor psk.</span><span class="sxs-lookup"><span data-stu-id="41ccc-209">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="41ccc-210">**identity_length** O comprimento da identidade psk.</span><span class="sxs-lookup"><span data-stu-id="41ccc-210">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="41ccc-211">**dica** Uma cadeia usada para indicar qual grupo de PSKs escolher num servidor TLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-211">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="41ccc-212">**hint_length** O comprimento da corda de sugestão.</span><span class="sxs-lookup"><span data-stu-id="41ccc-212">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-213">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-213">Return Values</span></span>

- <span data-ttu-id="41ccc-214">**NX_SUCCESS** (0x00) Adição bem sucedida de PSK.</span><span class="sxs-lookup"><span data-stu-id="41ccc-214">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="41ccc-215">**NX_PTR_ERROR** (0x07) Ponteiro de sessão DTLS inválido.</span><span class="sxs-lookup"><span data-stu-id="41ccc-215">**NX_PTR_ERROR** (0x07) Invalid DTLS session pointer.</span></span>
- <span data-ttu-id="41ccc-216">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Não pode adicionar outro PSK.</span><span class="sxs-lookup"><span data-stu-id="41ccc-216">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-217">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-217">Allowed From</span></span>

<span data-ttu-id="41ccc-218">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-218">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-219">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-219">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_psk_add(&dtls_session, psk,
                            sizeof(psk), “psk_1”, 4,
                            “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */


```

### <a name="see-also"></a><span data-ttu-id="41ccc-220">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-220">See Also</span></span>

- <span data-ttu-id="41ccc-221">nx_secure_dtls_server_psk_add, nx_secure_dtls_client_session_create</span><span class="sxs-lookup"><span data-stu-id="41ccc-221">nx_secure_dtls_server_psk_add, nx_secure_dtls_client_session_create</span></span>

## <a name="nx_secure_dtls_server_create"></a><span data-ttu-id="41ccc-222">nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="41ccc-222">nx_secure_dtls_server_create</span></span>

<span data-ttu-id="41ccc-223">Criar um Servidor DTLS Seguro NetX</span><span class="sxs-lookup"><span data-stu-id="41ccc-223">Create a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-224">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-224">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="41ccc-225">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-225">Description</span></span>

<span data-ttu-id="41ccc-226">Este serviço cria uma instância de um servidor DTLS para lidar com pedidos DTLS de entrada numa determinada porta UDP.</span><span class="sxs-lookup"><span data-stu-id="41ccc-226">This service creates an instance of a DTLS server to handle incoming DTLS requests on a particular UDP port.</span></span> <span data-ttu-id="41ccc-227">Devido ao facto de a UDP ser apátrida, os pedidos do DTLS de vários clientes podem entrar numa única porta enquanto outras sessões de DTLS estão ativas.</span><span class="sxs-lookup"><span data-stu-id="41ccc-227">Due to the fact that UDP is stateless, DTLS requests from multiple clients can come in on a single port while other DTLS sessions are active.</span></span> <span data-ttu-id="41ccc-228">Assim, o servidor é necessário para manter sessões ativas e encaminhar corretamente as mensagens recebidas para o manipulador adequado.</span><span class="sxs-lookup"><span data-stu-id="41ccc-228">Thus, the server is needed to maintain active sessions and properly route incoming messages to the proper handler.</span></span>

<span data-ttu-id="41ccc-229">O parâmetro ip_ptr aponta para uma NX_IP instância a utilizar para a tomada interna do UDP associada ao Servidor DTLS (e armazenada no bloco de controlo NX_SECURE_DTLS_SERVER).</span><span class="sxs-lookup"><span data-stu-id="41ccc-229">The ip_ptr parameter points to an NX_IP instance to be used for the internal UDP socket associated with the DTLS Server (and stored in the NX_SECURE_DTLS_SERVER control block).</span></span> <span data-ttu-id="41ccc-230">A instância IP e a porta são usadas para definir a interface UDP sobre a qual o servidor é instantâneo com o serviço nx_secure_dtls_server_start.</span><span class="sxs-lookup"><span data-stu-id="41ccc-230">The IP instance and port are used to define the UDP interface upon which the server is instantiated with the nx_secure_dtls_server_start service.</span></span>

<span data-ttu-id="41ccc-231">O parâmetro tampão de sessão é utilizado para manter os blocos de controlo para todas as possíveis sessões de DTLS simultâneas para o servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-231">The session buffer parameter is used to hold the control blocks for all the possible simultaneous DTLS sessions for the DTLS server.</span></span> <span data-ttu-id="41ccc-232">Deve ser atribuído com um tamanho que seja um múltiplo do tamanho da estrutura do bloco de controlo NX_SECURE_DTLS_SESSION.</span><span class="sxs-lookup"><span data-stu-id="41ccc-232">It should be allocated with a size that is an even multiple of the size of the NX_SECURE_DTLS_SESSION control block structure.</span></span>

<span data-ttu-id="41ccc-233">Para calcular o tamanho necessário dos metadados, pode ser utilizado o nx_secure_tls_metadata_size_calculate API.</span><span class="sxs-lookup"><span data-stu-id="41ccc-233">To calculate the necessary metadata size, the API nx_secure_tls_metadata_size_calculate may be used.</span></span>

<span data-ttu-id="41ccc-234">O parâmetro packet_reassembly_buffer é usado pela DTLS para remontar os datagramas de UDP num registo DTLS completo para efeitos de desencriptação e deve ser grande o suficiente para acomodar o maior registo DTLS esperado (16KB é o tamanho máximo de registo do DTLS, mas muitas aplicações não enviam tantos dados num único registo).</span><span class="sxs-lookup"><span data-stu-id="41ccc-234">The packet_reassembly_buffer parameter is used by DTLS to reassemble UDP datagrams into a complete DTLS record for the purposes of decryption and should be large enough to accommodate the largest expected DTLS record (16KB is the DTLS maximum record size but many applications don’t send that much data in a single record).</span></span>

<span data-ttu-id="41ccc-235">A rotina de chamada connect_notify é invocada sempre que um novo cliente DTLS se conecta ao servidor.</span><span class="sxs-lookup"><span data-stu-id="41ccc-235">The connect_notify callback routine is invoked whenever a new DTLS client connects to the server.</span></span> <span data-ttu-id="41ccc-236">Cabe à aplicação iniciar a sessão DTLS utilizando o *serviço nx_secure_dtls_server_session_start*.</span><span class="sxs-lookup"><span data-stu-id="41ccc-236">It is up to the application to then start the DTLS session using the service *nx_secure_dtls_server_session_start*.</span></span> <span data-ttu-id="41ccc-237">Embora a sessão possa ser iniciada na própria chamada, recomenda-se que a chamada apenas seja utilizada para notificar o fio de aplicação (ou fio DTLS dedicado criado pela aplicação) da ligação, uma vez que o retorno é invocado pelo fio IP que é utilizado para processar todo o processamento de rede de nível inferior (por exemplo, UDP).</span><span class="sxs-lookup"><span data-stu-id="41ccc-237">While the session may be started in the callback itself, it is recommended that the callback only be used to notify the application thread (or dedicated DTLS thread created by the application) of the connection as the callback is invoked by the IP thread which is used to process all lower-level network processing (e.g. UDP).</span></span> <span data-ttu-id="41ccc-238">Isto pode ser tão simples como guardar o parâmetro de sessão DTLS (fornecido como parâmetro para a chamada) e invocar nx_secure_dtls_server_session_start no outro fio.</span><span class="sxs-lookup"><span data-stu-id="41ccc-238">This can be as simple as saving the DTLS session parameter (provided as a parameter to the callback) and invoking nx_secure_dtls_server_session_start in the other thread.</span></span> <span data-ttu-id="41ccc-239">A connect_notify chamada deve geralmente voltar NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-239">The connect_notify callback should generally return NX_SUCCESS.</span></span>

<span data-ttu-id="41ccc-240">A rotina de chamada receive_notify é invocada sempre que é recebido um registo DTLS que corresponda a uma sessão DTLS estabelecida existente (o endereço IP e a porta do anfitrião remoto são utilizados para identificar uma sessão existente).</span><span class="sxs-lookup"><span data-stu-id="41ccc-240">The receive_notify callback routine is invoked whenever a DTLS record is received that matches an existing established DTLS session (the remote host IP address and port are used to identify an existing session).</span></span> <span data-ttu-id="41ccc-241">Isto representa os "dados de aplicação" que são encriptados e enviados sobre DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-241">This represents the “application data” that is encrypted and sent over DTLS.</span></span> <span data-ttu-id="41ccc-242">O pedido deve ligar para o *serviço nx_secure_dtls_session_receive* na sessão DTLS fornecida para recuperar os dados recebidos.</span><span class="sxs-lookup"><span data-stu-id="41ccc-242">The application must call the service *nx_secure_dtls_session_receive* on the provided DTLS session to retrieve the received data.</span></span> <span data-ttu-id="41ccc-243">Tal como acontece com a chamada connect_receive, recomenda-se que a sessão seja passada para outro fio para manusear o processamento da mensagem à medida que a chamada é invocada a partir do fio IP.</span><span class="sxs-lookup"><span data-stu-id="41ccc-243">As with the connect_receive callback, it is recommended that the session be passed to another thread to handle the message processing as the callback is invoked from the IP thread.</span></span> <span data-ttu-id="41ccc-244">A receive_notify chamada deve geralmente voltar NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-244">The receive_notify callback should generally return NX_SUCCESS.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-245">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-245">Parameters</span></span>

- <span data-ttu-id="41ccc-246">**server_ptr** Ponteiro para uma instância do Servidor DTLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-246">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="41ccc-247">**ip_ptr** Ponteiro para um bloco de controlo de NX_IP inicializado para usar como interface de rede para o servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-247">**ip_ptr** Pointer to an initialized NX_IP control block to use as the network interface for the DTLS server.</span></span>
- <span data-ttu-id="41ccc-248">**porto** A porta UDP local à qual está ligada a tomada UDP do servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-248">**port** The local UDP port to which the DTLS server UDP socket is bound.</span></span>
- <span data-ttu-id="41ccc-249">**tempo limite** Valor de tempo limite para utilizar para operações de rede.</span><span class="sxs-lookup"><span data-stu-id="41ccc-249">**timeout** Timeout value to use for network operations.</span></span>
- <span data-ttu-id="41ccc-250">**session_buffer** Espaço tampão para conter blocos de controlo para todos os casos de NX_SECURE_DTLS_SESSION atribuídos a esta instância do Servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-250">**session_buffer** Buffer space to contain control blocks for all instances of NX_SECURE_DTLS_SESSION assigned to this DTLS Server instance.</span></span>
- <span data-ttu-id="41ccc-251">**session_buffer_size** Tamanho do tampão da sessão.</span><span class="sxs-lookup"><span data-stu-id="41ccc-251">**session_buffer_size** Size of the session buffer.</span></span> <span data-ttu-id="41ccc-252">Isto determina o número de sessões DTLS atribuídas ao Servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-252">This determines the number of DTLS sessions assigned to the DTLS Server.</span></span>
- <span data-ttu-id="41ccc-253">**crypto_table** Ponteiro para uma estrutura de tabela de encriptação TLS/DTLS utilizada para todas as operações criptográficas.</span><span class="sxs-lookup"><span data-stu-id="41ccc-253">**crypto_table** Pointer to a TLS/DTLS encryption table structure used for all cryptographic operations.</span></span>
- <span data-ttu-id="41ccc-254">**crypto_metadata_buffer** Espaço tampão para cálculos de operação criptográfica e informações do estado.</span><span class="sxs-lookup"><span data-stu-id="41ccc-254">**crypto_metadata_buffer** Buffer space for cryptographic operation calculations and state information.</span></span>
- <span data-ttu-id="41ccc-255">**crypto_metadata_size** Tamanho do tampão de metadados.</span><span class="sxs-lookup"><span data-stu-id="41ccc-255">**crypto_metadata_size** Size of metadata buffer.</span></span>
- <span data-ttu-id="41ccc-256">**packet_reassembly_buffer** Tampão usado pela DTLS para remontar dados de UDP em registos DTLS para desencriptação.</span><span class="sxs-lookup"><span data-stu-id="41ccc-256">**packet_reassembly_buffer** Buffer used by DTLS to reassemble UDP data into DTLS records for decryption.</span></span>
- <span data-ttu-id="41ccc-257">**packet_reassembly_buffer_size** Tamanho do tampão de remontagem.</span><span class="sxs-lookup"><span data-stu-id="41ccc-257">**packet_reassembly_buffer_size** Size of reassembly buffer.</span></span> <span data-ttu-id="41ccc-258">Geralmente deve ser superior a 16KB, mas pode ser menor dependendo da aplicação.</span><span class="sxs-lookup"><span data-stu-id="41ccc-258">Generally should be greater than 16KB but may be smaller depending on application.</span></span>
- <span data-ttu-id="41ccc-259">**connect_notify** Rotina de chamada invocada sempre que um cliente DTLS remoto tenta ligar-se a este servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-259">**connect_notify** Callback routine invoked whenever a remote DTLS Client attempts to connect to this DTLS server.</span></span>
- <span data-ttu-id="41ccc-260">**receive_notify** Callback invocado sempre que os dados da aplicação são recebidos durante uma sessão DTLS existente.</span><span class="sxs-lookup"><span data-stu-id="41ccc-260">**receive_notify** Callback invoked whenever application data is received over an existing DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-261">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-261">Return Values</span></span>

- <span data-ttu-id="41ccc-262">**NX_SUCCESS** (0x00) Criação bem sucedida do servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-262">**NX_SUCCESS** (0x00) Successful creation of DTLS server.</span></span>
- <span data-ttu-id="41ccc-263">**NX_PTR_ERROR** (0x07) Ponteiro inválido passou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-263">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="41ccc-264">**NX_INVALID_PARAMETERS** (0x4D) Não há espaço tampão suficiente para sessões, remontagem de pacotes ou criptografia.</span><span class="sxs-lookup"><span data-stu-id="41ccc-264">**NX_INVALID_PARAMETERS** (0x4D) Not enough buffer space for sessions, packet reassembly, or cryptography.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-265">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-265">Allowed From</span></span>

<span data-ttu-id="41ccc-266">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-266">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-267">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-267">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-268">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-268">See Also</span></span>

- <span data-ttu-id="41ccc-269">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span><span class="sxs-lookup"><span data-stu-id="41ccc-269">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="41ccc-270">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send.</span><span class="sxs-lookup"><span data-stu-id="41ccc-270">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="41ccc-271">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="41ccc-271">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="41ccc-272">nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="41ccc-272">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="41ccc-273">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="41ccc-273">nx_secure_dtls_server_local_certificate_add</span></span>

## <a name="nx_secure_dtls_server_delete"></a><span data-ttu-id="41ccc-274">nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="41ccc-274">nx_secure_dtls_server_delete</span></span>

<span data-ttu-id="41ccc-275">Liberte os recursos utilizados por um Servidor DTLS Seguro NetX</span><span class="sxs-lookup"><span data-stu-id="41ccc-275">Free up resources used by a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-276">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-276">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_delete(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="41ccc-277">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-277">Description</span></span>

<span data-ttu-id="41ccc-278">Este serviço liberta os recursos atribuídos a uma instância do Servidor DTLS, incluindo a tomada interna do UDP utilizada pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="41ccc-278">This service frees up the resources allocated to a DTLS Server instance, including the internal UDP socket used by the server.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-279">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-279">Parameters</span></span>

- <span data-ttu-id="41ccc-280">**server_ptr** Ponteiro para uma instância do Servidor DTLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-280">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-281">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-281">Return Values</span></span>

- <span data-ttu-id="41ccc-282">**NX_SUCCESS** (0x00) Eliminação bem sucedida do servidor.</span><span class="sxs-lookup"><span data-stu-id="41ccc-282">**NX_SUCCESS** (0x00) Successful deletion of server.</span></span>
- <span data-ttu-id="41ccc-283">**NX_PTR_ERROR** (0x07) Ponteiro inválido passou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-283">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="41ccc-284">**NX_STILL_BOUND** (0x42) tomada UDP ainda está ligada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-284">**NX_STILL_BOUND** (0x42) UDP socket is still bound.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-285">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-285">Allowed From</span></span>

<span data-ttu-id="41ccc-286">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-286">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-287">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-287">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-288">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-288">See Also</span></span>

- <span data-ttu-id="41ccc-289">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="41ccc-289">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="41ccc-290">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send.</span><span class="sxs-lookup"><span data-stu-id="41ccc-290">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="41ccc-291">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="41ccc-291">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_server_local_certificate_add"></a><span data-ttu-id="41ccc-292">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="41ccc-292">nx_secure_dtls_server_local_certificate_add</span></span>

<span data-ttu-id="41ccc-293">Adicione um certificado de identidade de servidor local a um Servidor DTLS Seguro NetX</span><span class="sxs-lookup"><span data-stu-id="41ccc-293">Add a local server identity certificate to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-294">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-294">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_local_certificate_add(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                 NX_SECURE_X509_CERT *certificate,
                                 UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="41ccc-295">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-295">Description</span></span>

<span data-ttu-id="41ccc-296">Este serviço adiciona um certificado de identidade do servidor local a uma instância do Servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-296">This service adds a local server identity certificate to a DTLS Server instance.</span></span> <span data-ttu-id="41ccc-297">Pelo menos um certificado de identidade é necessário para que os clientes se conectem a um servidor DTLS a menos que seja utilizado um mecanismo de autenticação alternativo (por exemplo, Chaves Pré-Partilhadas).</span><span class="sxs-lookup"><span data-stu-id="41ccc-297">At least one identity certificate is required for clients to connect to a DTLS server unless an alternate authentication mechanism (e.g. Pre-Shared Keys) is used.</span></span>

<span data-ttu-id="41ccc-298">O parâmetro cert_id é um identificador numérico, sem zero para o certificado.</span><span class="sxs-lookup"><span data-stu-id="41ccc-298">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="41ccc-299">Isto permite que o certificado seja facilmente removido ou encontrado no caso de existirem vários certificados de identidade com o mesmo Nome Comum X.509 presente na loja do servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-299">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS server store.</span></span> <span data-ttu-id="41ccc-300">Consulte o Guia de Utilizador NetX Secure TLS para obter mais informações sobre os certificados de servidor X.509.</span><span class="sxs-lookup"><span data-stu-id="41ccc-300">See the NetX Secure TLS User Guide for more information about X.509 server certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-301">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-301">Parameters</span></span>

- <span data-ttu-id="41ccc-302">**server_ptr** Ponteiro para uma instância do Servidor DTLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-302">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="41ccc-303">**certificado** Ponteiro para uma estrutura de certificado X.509 previamente inicializada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-303">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="41ccc-304">**cert_id** Identificador único numérico não zero para este certificado neste servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-304">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-305">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-305">Return Values</span></span>

- <span data-ttu-id="41ccc-306">**NX_SUCCESS** (0x00) Adição bem sucedida de certificado ao servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-306">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS server.</span></span>
- <span data-ttu-id="41ccc-307">**NX_PTR_ERROR** (0x07) Ponteiro inválido passou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-307">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="41ccc-308">**NX_INVALID_PARAMETERS** (0x4D) Foi aprovado um certificado de identificação de 0.</span><span class="sxs-lookup"><span data-stu-id="41ccc-308">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-309">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-309">Allowed From</span></span>

<span data-ttu-id="41ccc-310">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-310">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-311">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-311">Example</span></span>

<span data-ttu-id="41ccc-312">\*Consulte a referência para *nx_secure_dtls_server_create* para obter um exemplo mais completo.</span><span class="sxs-lookup"><span data-stu-id="41ccc-312">\*See reference for *nx_secure_dtls_server_create* for a more complete example.</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-313">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-313">See Also</span></span>

- <span data-ttu-id="41ccc-314">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="41ccc-314">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="41ccc-315">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send.</span><span class="sxs-lookup"><span data-stu-id="41ccc-315">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="41ccc-316">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="41ccc-316">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="41ccc-317">nx_secure_dtls_server_local_certificate_remove,</span><span class="sxs-lookup"><span data-stu-id="41ccc-317">nx_secure_dtls_server_local_certificate_remove,</span></span>
- <span data-ttu-id="41ccc-318">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="41ccc-318">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_local_certificate_remove"></a><span data-ttu-id="41ccc-319">nx_secure_dtls_server_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="41ccc-319">nx_secure_dtls_server_local_certificate_remove</span></span>

<span data-ttu-id="41ccc-320">Remova um certificado de identidade do servidor local de um Servidor DTLS Seguro NetX</span><span class="sxs-lookup"><span data-stu-id="41ccc-320">Remove a local server identity certificate from a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-321">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-321">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_local_certificate_remove(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                   UCHAR *common_name,
                                   UINT common_name_length,
                                   UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="41ccc-322">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-322">Description</span></span>

<span data-ttu-id="41ccc-323">Este serviço remove um certificado de identidade do servidor local de uma instância do Servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-323">This service removes a local server identity certificate from a DTLS Server instance.</span></span> <span data-ttu-id="41ccc-324">Pelo menos um certificado de identidade é necessário para que os clientes se conectem a um servidor DTLS a menos que seja utilizado um mecanismo de autenticação alternativo (por exemplo, Chaves Pré-Partilhadas).</span><span class="sxs-lookup"><span data-stu-id="41ccc-324">At least one identity certificate is required for clients to connect to a DTLS server unless an alternate authentication mechanism (e.g. Pre-Shared Keys) is used.</span></span>

<span data-ttu-id="41ccc-325">O certificado a retirar pode ser identificado pelo seu Nome Comum X.509 ou pelo cert_id numérico que foi atribuído na chamada para *nx_secure_dtls_server_local_certificate_add*.</span><span class="sxs-lookup"><span data-stu-id="41ccc-325">The certificate to be removed can be identified either by its X.509 Common Name or by the numeric cert_id that was assigned in the call to *nx_secure_dtls_server_local_certificate_add*.</span></span> <span data-ttu-id="41ccc-326">O cert_id é utilizado apenas para identificar o certificado e é mantido pelo pedido.</span><span class="sxs-lookup"><span data-stu-id="41ccc-326">The cert_id is only used to identify the certificate and is maintained by the application.</span></span> <span data-ttu-id="41ccc-327">Se o nome comum for utilizado em vez do identificador de certificado numérico, o parâmetro cert_id deve ser definido para 0.</span><span class="sxs-lookup"><span data-stu-id="41ccc-327">If the Common Name is used instead of the numeric certificate identifier, the cert_id parameter should be set to 0.</span></span>

> [!NOTE]
> <span data-ttu-id="41ccc-328">Remover um certificado enquanto um aperto de mão DTLS está sendo processado resultará em comportamento inesperado.</span><span class="sxs-lookup"><span data-stu-id="41ccc-328">Removing a certificate while a DTLS handshake is being processed will result in unexpected behavior.</span></span> <span data-ttu-id="41ccc-329">O *serviço nx_secure_dtls_server_stop* deve ser chamado antes de retirar os certificados.</span><span class="sxs-lookup"><span data-stu-id="41ccc-329">The service *nx_secure_dtls_server_stop* should be called before removing certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-330">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-330">Parameters</span></span>

- <span data-ttu-id="41ccc-331">**server_ptr** Ponteiro para uma instância do Servidor DTLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-331">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="41ccc-332">**common_name** X.509 CommonName do certificado a remover.</span><span class="sxs-lookup"><span data-stu-id="41ccc-332">**common_name** X.509 CommonName of the certificate to remove.</span></span> <span data-ttu-id="41ccc-333">Se isto for usado, passe cert_id como zero.</span><span class="sxs-lookup"><span data-stu-id="41ccc-333">If this is used, pass cert_id as zero.</span></span>
- <span data-ttu-id="41ccc-334">**common_name_length** Comprimento de common_name cordas em bytes.</span><span class="sxs-lookup"><span data-stu-id="41ccc-334">**common_name_length** Length of common_name string in bytes.</span></span>
- <span data-ttu-id="41ccc-335">**cert_id** Identificador único numérico não zero para este certificado neste servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-335">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span> <span data-ttu-id="41ccc-336">Se isto for utilizado, passe NX_NULL para o parâmetro common_name.</span><span class="sxs-lookup"><span data-stu-id="41ccc-336">If this is used, pass NX_NULL for the common_name parameter.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-337">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-337">Return Values</span></span>

- <span data-ttu-id="41ccc-338">**NX_SUCCESS** (0x00) Remoção bem sucedida do certificado do servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-338">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS server.</span></span>
- <span data-ttu-id="41ccc-339">**NX_PTR_ERROR** (0x07) Ponteiro inválido passou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-339">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="41ccc-340">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Não foi encontrado nenhum certificado correspondente ao cert_id ou common_name no servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-340">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS server.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-341">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-341">Allowed From</span></span>

<span data-ttu-id="41ccc-342">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-342">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-343">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-343">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-344">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-344">See Also</span></span>

- <span data-ttu-id="41ccc-345">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="41ccc-345">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="41ccc-346">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="41ccc-346">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="41ccc-347">nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="41ccc-347">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="41ccc-348">nx_secure_dtls_server_local_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="41ccc-348">nx_secure_dtls_server_local_certificate_add,</span></span>
- <span data-ttu-id="41ccc-349">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="41ccc-349">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_notify_set"></a><span data-ttu-id="41ccc-350">nx_secure_dtls_server_notify_set</span><span class="sxs-lookup"><span data-stu-id="41ccc-350">nx_secure_dtls_server_notify_set</span></span>

<span data-ttu-id="41ccc-351">Atribuir rotinas de chamada de notificação opcional a um Servidor DTLS Seguro NetX</span><span class="sxs-lookup"><span data-stu-id="41ccc-351">Assign optional notification callback routines to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-352">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-352">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_notify_set(
                         NX_SECURE_DTLS_SERVER *server_ptr,
                         UINT (*disconnect_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session),
                         UINT (*error_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session,
                                      UINT error_code));

```

### <a name="description"></a><span data-ttu-id="41ccc-353">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-353">Description</span></span>

<span data-ttu-id="41ccc-354">Este serviço pode ser utilizado para adicionar rotinas de chamada de notificação opcionais a um servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-354">This service can be used to add optional notification callback routines to a DTLS server.</span></span> <span data-ttu-id="41ccc-355">Qualquer um dos parâmetros de retorno pode ser passado como NX_NULL se apenas uma chamada for desejada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-355">Either callback parameter may be passed as NX_NULL if only one callback is desired.</span></span>

<span data-ttu-id="41ccc-356">A disconnect_notify chamada é invocada quando um cliente remoto termina uma sessão de DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-356">The disconnect_notify callback is invoked when a remote client ends a DTLS session.</span></span> <span data-ttu-id="41ccc-357">O parâmetro dtls_session é a instância da sessão que foi encerrada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-357">The dtls_session parameter is the session instance that was closed.</span></span> <span data-ttu-id="41ccc-358">A chamada deve geralmente voltar NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-358">The callback should generally return NX_SUCCESS.</span></span>

<span data-ttu-id="41ccc-359">A chamada error_notify é invocada sempre que ocorre um erro ou tempo limite de DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-359">The error_notify callback is invoked whenever a DTLS error or timeout occurs.</span></span> <span data-ttu-id="41ccc-360">O parâmetro dtls_session é a instância de sessão para a qual ocorreu o erro, e error_code é o código de estado numérico para o erro que causou o problema (ver apêndice A)</span><span class="sxs-lookup"><span data-stu-id="41ccc-360">The dtls_session parameter is the session instance for which the error occurred, and error_code is the numeric status code for the error that caused the issue (see Appendix A)</span></span>

<span data-ttu-id="41ccc-361">NetX Secure Return/Error Codes para uma lista de códigos de erro que podem ser devolvidos).</span><span class="sxs-lookup"><span data-stu-id="41ccc-361">NetX Secure Return/Error Codes for a list of error codes that may be returned).</span></span> <span data-ttu-id="41ccc-362">A chamada deve geralmente voltar NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-362">The callback should generally return NX_SUCCESS.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-363">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-363">Parameters</span></span>

- <span data-ttu-id="41ccc-364">**server_ptr** Ponteiro para uma instância do Servidor DTLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-364">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="41ccc-365">**disconnect_notify** Rotina de chamada invocada sempre que um anfitrião remoto do cliente fecha uma sessão de DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-365">**disconnect_notify** Callback routine invoked whenever a remote client host closes a DTLS session.</span></span>
- <span data-ttu-id="41ccc-366">**error_notify** Rotina de retorno invocada sempre que dTLS encontra um erro ou tempo limite.</span><span class="sxs-lookup"><span data-stu-id="41ccc-366">**error_notify** Callback routine invoked whenever DTLS encounters an error or timeout.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-367">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-367">Return Values</span></span>

- <span data-ttu-id="41ccc-368">**NX_SUCCESS** (0x00) Atribuição bem sucedida de rotinas de retorno.</span><span class="sxs-lookup"><span data-stu-id="41ccc-368">**NX_SUCCESS** (0x00) Successful assignment of callback routines.</span></span>
- <span data-ttu-id="41ccc-369">**NX_PTR_ERROR** (0x07) Ponteiro inválido passou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-369">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-370">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-370">Allowed From</span></span>

<span data-ttu-id="41ccc-371">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-371">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-372">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-372">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-373">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-373">See Also</span></span>

- <span data-ttu-id="41ccc-374">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="41ccc-374">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="41ccc-375">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="41ccc-375">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="41ccc-376">nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="41ccc-376">nx_secure_dtls_server_session_stop</span></span>

## <a name="nx_secure_dtls_server_psk_add"></a><span data-ttu-id="41ccc-377">nx_secure_dtls_server_psk_add</span><span class="sxs-lookup"><span data-stu-id="41ccc-377">nx_secure_dtls_server_psk_add</span></span>

<span data-ttu-id="41ccc-378">Adicione uma chave pré-partilhada a um servidor DTLS Seguro NetX</span><span class="sxs-lookup"><span data-stu-id="41ccc-378">Add a Pre-Shared Key to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-379">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-379">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_psk_add(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *pre_shared_key, UINT psk_length,
                                UCHAR *psk_identity,
                                UINT identity_length, UCHAR *hint,
                                UINT hint_length);

```

### <a name="description"></a><span data-ttu-id="41ccc-380">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-380">Description</span></span>

<span data-ttu-id="41ccc-381">Este serviço adiciona uma chave pré-partilhada (PSK), a sua cadeia de identidade e uma sugestão de identidade para um bloco de controlo do Servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-381">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a DTLS Server control block.</span></span> <span data-ttu-id="41ccc-382">O PSK é utilizado em vez de um certificado digital quando as cifrasuites PSK são ativadas e utilizadas.</span><span class="sxs-lookup"><span data-stu-id="41ccc-382">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

<span data-ttu-id="41ccc-383">O PSK adicionado é replicado em todas as sessões DTLS atribuídas ao Servidor DTLS (através do tampão de sessão dado na chamada para nx_secure_dtls_server_create).</span><span class="sxs-lookup"><span data-stu-id="41ccc-383">The PSK that is added is replicated across all the DTLS sessions assigned to the DTLS Server (via the session buffer given in the call to nx_secure_dtls_server_create).</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-384">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-384">Parameters</span></span>

- <span data-ttu-id="41ccc-385">**server_ptr** Ponteiro para uma instância do Servidor DTLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-385">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="41ccc-386">**pre_shared_key** O valor real do PSK.</span><span class="sxs-lookup"><span data-stu-id="41ccc-386">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="41ccc-387">**psk_length** O comprimento do valor PSK.</span><span class="sxs-lookup"><span data-stu-id="41ccc-387">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="41ccc-388">**psk_identity** Uma corda usada para identificar este valor psk.</span><span class="sxs-lookup"><span data-stu-id="41ccc-388">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="41ccc-389">**identity_length** O comprimento da identidade psk.</span><span class="sxs-lookup"><span data-stu-id="41ccc-389">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="41ccc-390">**dica** Uma cadeia usada para indicar qual grupo de PSKs escolher num servidor TLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-390">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="41ccc-391">**hint_length** O comprimento da corda de sugestão.</span><span class="sxs-lookup"><span data-stu-id="41ccc-391">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-392">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-392">Return Values</span></span>

- <span data-ttu-id="41ccc-393">**NX_SUCCESS** (0x00) Adição bem sucedida de PSK.</span><span class="sxs-lookup"><span data-stu-id="41ccc-393">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="41ccc-394">**NX_PTR_ERROR** (0x07) Ponteiro do servidor DTLS inválido.</span><span class="sxs-lookup"><span data-stu-id="41ccc-394">**NX_PTR_ERROR** (0x07) Invalid DTLS server pointer.</span></span>
- <span data-ttu-id="41ccc-395">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Não pode adicionar outro PSK.</span><span class="sxs-lookup"><span data-stu-id="41ccc-395">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-396">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-396">Allowed From</span></span>

<span data-ttu-id="41ccc-397">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-398">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-398">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_server_psk_add(&dtls_server, psk, sizeof(psk), “psk_1”,
   4, “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */

```

### <a name="see-also"></a><span data-ttu-id="41ccc-399">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-399">See Also</span></span>

- <span data-ttu-id="41ccc-400">nx_secure_dtls_psk_add, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="41ccc-400">nx_secure_dtls_psk_add, nx_secure_dtls_server_create</span></span>

## <a name="nx_secure_dtls_server_session_send"></a><span data-ttu-id="41ccc-401">nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="41ccc-401">nx_secure_dtls_server_session_send</span></span>

<span data-ttu-id="41ccc-402">Envie dados sobre uma sessão de DTLS estabelecida com um Servidor DTLS Seguro NetX</span><span class="sxs-lookup"><span data-stu-id="41ccc-402">Send data over a DTLS session established with a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-403">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-403">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_session_send(
                                NX_SECURE_DTLS_SESSION *session_ptr,
                               NX_PACKET *packet_ptr);

```

### <a name="description"></a><span data-ttu-id="41ccc-404">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-404">Description</span></span>

<span data-ttu-id="41ccc-405">Este serviço envia um pacote de dados sobre uma sessão estabelecida do DTLS Server para um anfitrião remoto do Cliente DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-405">This service sends a packet of data over an established DTLS Server session to a remote DTLS Client host.</span></span> <span data-ttu-id="41ccc-406">A sessão utilizada é obtida na rotina de chamada receive_notify fornecida a nx_secure_dtls_session_create.</span><span class="sxs-lookup"><span data-stu-id="41ccc-406">The session used is obtained in the receive_notify callback routine provided to nx_secure_dtls_session_create.</span></span>

<span data-ttu-id="41ccc-407">Os dados fornecidos no pacote, que devem ser atribuídos utilizando *nx_secure_dtls_packet_allocate,* são encriptados utilizando os parâmetros e rotinas criptográficos da sessão DTLS e depois enviados para o anfitrião remoto através da porta UDP interna do DTLS Server para o endereço IP e porta do cliente anexado (armazenados na Sessão DTLS).</span><span class="sxs-lookup"><span data-stu-id="41ccc-407">The data provided in the packet, which must be allocated using *nx_secure_dtls_packet_allocate*, is encrypted using the DTLS session cryptographic parameters and routines and then sent to the remote host over the DTLS Server internal UDP port to the attached client’s IP address and port (stored in the DTLS Session).</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-408">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-408">Parameters</span></span>

- <span data-ttu-id="41ccc-409">**session_ptr** Ponteiro para uma instância de sessão DTLS obtida a partir da rotina de chamada receive_notify fornecida pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="41ccc-409">**session_ptr** Pointer to a DTLS session instance obtained from the receive_notify callback routine provided by the application.</span></span>
- <span data-ttu-id="41ccc-410">**packet_ptr** Ponteiro para uma NX_PACKET instância atribuída anteriormente e povoada com dados de aplicação.</span><span class="sxs-lookup"><span data-stu-id="41ccc-410">**packet_ptr** Pointer to an NX_PACKET instance allocated previously and populated with application data.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-411">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-411">Return Values</span></span>

- <span data-ttu-id="41ccc-412">**NX_SUCCESS** (0x00) Criação bem sucedida do servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-412">**NX_SUCCESS** (0x00) Successful creation of DTLS server.</span></span>
- <span data-ttu-id="41ccc-413">**NX_PTR_ERROR** (0x07) Ponteiro inválido passou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-413">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="41ccc-414">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Ocorreu um erro na operação de envio da UDP subjacente.</span><span class="sxs-lookup"><span data-stu-id="41ccc-414">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An error occurred in the underlying UDP send operation.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-415">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-415">Allowed From</span></span>

<span data-ttu-id="41ccc-416">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-416">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-417">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-417">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-418">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-418">See Also</span></span>

- <span data-ttu-id="41ccc-419">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span><span class="sxs-lookup"><span data-stu-id="41ccc-419">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="41ccc-420">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_create.</span><span class="sxs-lookup"><span data-stu-id="41ccc-420">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_create,</span></span>
- <span data-ttu-id="41ccc-421">nx_secure_dtls_server_session_start, nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="41ccc-421">nx_secure_dtls_server_session_start, nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="41ccc-422">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="41ccc-422">nx_secure_dtls_server_local_certificate_add</span></span>

## <a name="nx_secure_dtls_server_session_start"></a><span data-ttu-id="41ccc-423">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="41ccc-423">nx_secure_dtls_server_session_start</span></span>

<span data-ttu-id="41ccc-424">Inicie uma Sessão DTLS a partir de um Servidor DTLS Seguro NetX</span><span class="sxs-lookup"><span data-stu-id="41ccc-424">Start a DTLS Session from a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-425">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-425">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_session_start(
                 NX_SECURE_DTLS_SESSION *session_ptr, UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="41ccc-426">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-426">Description</span></span>

<span data-ttu-id="41ccc-427">Este serviço inicia uma sessão do DTLS Server executando o aperto de mão DTLS do lado do servidor quando um Cliente DTLS remoto se ligou ao servidor e solicitou uma ligação DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-427">This service starts a DTLS Server session by performing the server-side DTLS handshake when a remote DTLS Client has connected to the server and requested a DTLS connection.</span></span>

<span data-ttu-id="41ccc-428">A Sessão DTLS é obtida na rotina de chamada connect_notify fornecida a nx_secure_dtls_server_create.</span><span class="sxs-lookup"><span data-stu-id="41ccc-428">The DTLS Session is obtained in the connect_notify callback routine provided to nx_secure_dtls_server_create.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-429">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-429">Parameters</span></span>

- <span data-ttu-id="41ccc-430">**session_ptr** Ponteiro para uma instância de Sessão DTLS obtida a partir de uma chamada de connect_notify do Servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-430">**session_ptr** Pointer to a DTLS Session instance obtained from a DTLS Server connect_notify callback.</span></span>
- <span data-ttu-id="41ccc-431">**wait_option** ThreadX espera valor para usar para operações de rede.</span><span class="sxs-lookup"><span data-stu-id="41ccc-431">**wait_option** ThreadX wait value to use for network operations.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-432">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-432">Return Values</span></span>

- <span data-ttu-id="41ccc-433">**NX_SUCCESS** (0x00) Criação bem sucedida do servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-433">**NX_SUCCESS** (0x00) Successful creation of DTLS server.</span></span>
- <span data-ttu-id="41ccc-434">**NX_PTR_ERROR** (0x07) Ponteiro inválido passou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-434">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="41ccc-435">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Não poderia atribuir um pacote de aperto de mão DTLS (piscina vazia).</span><span class="sxs-lookup"><span data-stu-id="41ccc-435">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate a DTLS handshake packet (packet pool empty).</span></span>
- <span data-ttu-id="41ccc-436">**NX_SECURE_TLS_INVALID_PACKET** (0x104) Dados recevied que não eram um registo DTLS válido.</span><span class="sxs-lookup"><span data-stu-id="41ccc-436">**NX_SECURE_TLS_INVALID_PACKET** (0x104) Recevied data that was not a valid DTLS record.</span></span>
- <span data-ttu-id="41ccc-437">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Um registo DTLS não foi devidamente hashed (erro de encriptação).</span><span class="sxs-lookup"><span data-stu-id="41ccc-437">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A DTLS record failed to be properly hashed (encryption error).</span></span>
- <span data-ttu-id="41ccc-438">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Falha de verificação de encriptação.</span><span class="sxs-lookup"><span data-stu-id="41ccc-438">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Encryption padding check failure.</span></span>
- <span data-ttu-id="41ccc-439">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Recevied um alerta do hospedeiro remoto durante o aperto de mão DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-439">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Recevied an alert from the remote host during the DTLS handshake.</span></span>
- <span data-ttu-id="41ccc-440">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) Recebeu uma mensagem não reconhecida durante o aperto de mão DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-440">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) Received an unrecognized message during the DTLS handshake.</span></span>
- <span data-ttu-id="41ccc-441">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Recevied um registo DTLS com um comprimento inválido.</span><span class="sxs-lookup"><span data-stu-id="41ccc-441">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Recevied a DTLS record with an invalid length.</span></span>
- <span data-ttu-id="41ccc-442">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) Recebeu um ClientHello sem cifrasuites DTLS suportados.</span><span class="sxs-lookup"><span data-stu-id="41ccc-442">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) Received a ClientHello with no supported DTLS ciphersuites.</span></span>
- <span data-ttu-id="41ccc-443">**NX_SECURE_TLS_BAD_COMPRESSION_METHOD** (0x118) Recevied a ClientHello com um método de compressão desconhecido.</span><span class="sxs-lookup"><span data-stu-id="41ccc-443">**NX_SECURE_TLS_BAD_COMPRESSION_METHOD** (0x118) Recevied a ClientHello with a unknown compression method.</span></span>
- <span data-ttu-id="41ccc-444">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Falha do aperto de mão genérico (não especificado), geralmente devido a problemas com o processamento de extensão.</span><span class="sxs-lookup"><span data-stu-id="41ccc-444">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Generic (unspecified) handshake failure, usually due to problems with extension processing.</span></span>
- <span data-ttu-id="41ccc-445">**NX_SECURE_TLS_UNSUPPORTED_FEATURE** (0x130) Uma funcionalidade que ainda não foi suportada foi invocada durante o aperto de mão DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-445">**NX_SECURE_TLS_UNSUPPORTED_FEATURE** (0x130) A feature that is not yet supported was invoked during the DTLS handshake.</span></span>
- <span data-ttu-id="41ccc-446">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Foi encontrada uma cifrasuita desconhecida (indicava erro de criptografia interna).</span><span class="sxs-lookup"><span data-stu-id="41ccc-446">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) An unknown ciphersuite was encountered (indicated internal cryptography error).</span></span>
- <span data-ttu-id="41ccc-447">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) Recevied um registo DTLS com uma versão DTLS desajustada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-447">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) Recevied a DTLS record with a mismatched DTLS version.</span></span>
- <span data-ttu-id="41ccc-448">**NX_SECURE_TLS_FINISHED_HASH_FAILURE** (0x115) Não conseguiu validar o haxixe do aperto de mão DTLS, a sessão é inválida.</span><span class="sxs-lookup"><span data-stu-id="41ccc-448">**NX_SECURE_TLS_FINISHED_HASH_FAILURE** (0x115) Failed to validate the DTLS handshake hash, session is invalid.</span></span>
- <span data-ttu-id="41ccc-449">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Envio interno da UDP falhou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-449">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Internal UDP send failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-450">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-450">Allowed From</span></span>

<span data-ttu-id="41ccc-451">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-451">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-452">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-452">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-453">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-453">See Also</span></span>

- <span data-ttu-id="41ccc-454">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span><span class="sxs-lookup"><span data-stu-id="41ccc-454">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="41ccc-455">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send.</span><span class="sxs-lookup"><span data-stu-id="41ccc-455">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="41ccc-456">nx_secure_dtls_server_session_create, nx_secure_dtls_server_session_stop.</span><span class="sxs-lookup"><span data-stu-id="41ccc-456">nx_secure_dtls_server_session_create, nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="41ccc-457">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="41ccc-457">nx_secure_dtls_server_local_certificate_add</span></span>

## <a name="nx_secure_dtls_server_start"></a><span data-ttu-id="41ccc-458">nx_secure_dtls_server_start</span><span class="sxs-lookup"><span data-stu-id="41ccc-458">nx_secure_dtls_server_start</span></span>

<span data-ttu-id="41ccc-459">Inicie uma instância do Servidor DTLS Segura NetX a ouvir na porta UDP configurada</span><span class="sxs-lookup"><span data-stu-id="41ccc-459">Start a NetX Secure DTLS Server instance listening on the configured UDP port</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-460">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-460">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_start(
                  NX_SECURE_DTLS_SERVER *server_ptr);

```

### <a name="description"></a><span data-ttu-id="41ccc-461">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-461">Description</span></span>

<span data-ttu-id="41ccc-462">Este serviço inicia um Servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-462">This service starts a DTLS Server.</span></span> <span data-ttu-id="41ccc-463">Após a revolução da chamada, o servidor está ativo e começará a processar pedidos de entrada de clientes DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-463">After the call returns, the server is active and will begin processing incoming requests from DTLS clients.</span></span> <span data-ttu-id="41ccc-464">A instância do servidor deve ter sido configurada com o *serviço nx_secure_dtls_server_create*.</span><span class="sxs-lookup"><span data-stu-id="41ccc-464">The server instance must have been configured with the service *nx_secure_dtls_server_create*.</span></span>

> [!NOTE]
> <span data-ttu-id="41ccc-465">Este serviço liga a porta UDP do Servidor DTLS interno à porta local configurada, pelo que a maioria dos problemas encontrados terão a ver com comunicações UDP e configuração de rede.</span><span class="sxs-lookup"><span data-stu-id="41ccc-465">This service binds the internal DTLS Server UDP port to the configured local port so most issues encountered will have to do with UDP communications and network configuration.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-466">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-466">Parameters</span></span>

- <span data-ttu-id="41ccc-467">**server_ptr** Ponteiro para uma instância do Servidor DTLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-467">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-468">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-468">Return Values</span></span>

- <span data-ttu-id="41ccc-469">**NX_SUCCESS** (0x00) Início bem sucedido do servidor.</span><span class="sxs-lookup"><span data-stu-id="41ccc-469">**NX_SUCCESS** (0x00) Successful start of server.</span></span>
- <span data-ttu-id="41ccc-470">**NX_PTR_ERROR** (0x07) Ponteiro inválido passou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-470">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="41ccc-471">**NX_NOT_ENABLED** (0x14) UDP não está ativado.</span><span class="sxs-lookup"><span data-stu-id="41ccc-471">**NX_NOT_ENABLED** (0x14) UDP not enabled.</span></span>
- <span data-ttu-id="41ccc-472">**NX_NO_FREE_PORTS** (0x45) Não há portas UDP disponíveis.</span><span class="sxs-lookup"><span data-stu-id="41ccc-472">**NX_NO_FREE_PORTS** (0x45) No available UDP ports.</span></span>
- <span data-ttu-id="41ccc-473">**NX_INVALID_PORT** (0x46) Porta UDP inválida.</span><span class="sxs-lookup"><span data-stu-id="41ccc-473">**NX_INVALID_PORT** (0x46) Invalid UDP port.</span></span>
- <span data-ttu-id="41ccc-474">**NX_ALREADY_BOUND** (0x22) porta UDP já está vinculada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-474">**NX_ALREADY_BOUND** (0x22) UDP port already bound.</span></span>
- <span data-ttu-id="41ccc-475">**NX_PORT_UNAVAILABLE** (0x23) porta UDP não disponível para utilização.</span><span class="sxs-lookup"><span data-stu-id="41ccc-475">**NX_PORT_UNAVAILABLE** (0x23) UDP port not available for use.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-476">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-476">Allowed From</span></span>

<span data-ttu-id="41ccc-477">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-477">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-478">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-478">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-479">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-479">See Also</span></span>

- <span data-ttu-id="41ccc-480">nx_secure_dtls_server_stop, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="41ccc-480">nx_secure_dtls_server_stop, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="41ccc-481">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="41ccc-481">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="41ccc-482">nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="41ccc-482">nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="41ccc-483">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="41ccc-483">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_server_stop"></a><span data-ttu-id="41ccc-484">nx_secure_dtls_server_stop</span><span class="sxs-lookup"><span data-stu-id="41ccc-484">nx_secure_dtls_server_stop</span></span>

<span data-ttu-id="41ccc-485">Pare uma instância ativa do Servidor DTLS do NetX Secure</span><span class="sxs-lookup"><span data-stu-id="41ccc-485">Stop an active NetX Secure DTLS Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-486">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-486">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_stop(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="41ccc-487">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-487">Description</span></span>

<span data-ttu-id="41ccc-488">Este serviço impede que um Servidor DTLS ouça na porta UDP configurante e reinicie todas as sessões DTLS associadas, interrompendo quaisquer comunicações DTLS em curso.</span><span class="sxs-lookup"><span data-stu-id="41ccc-488">This service stops a DTLS Server from listening on the configure UDP port and resets all the associated DTLS sessions, halting any in-progress DTLS communications.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-489">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-489">Parameters</span></span>

- <span data-ttu-id="41ccc-490">**server_ptr** Ponteiro para uma instância ativa do Servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-490">**server_ptr** Pointer to an active DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-491">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-491">Return Values</span></span>

- <span data-ttu-id="41ccc-492">**NX_SUCCESS** (0x00) Paragem bem sucedida do servidor.</span><span class="sxs-lookup"><span data-stu-id="41ccc-492">**NX_SUCCESS** (0x00) Successful stop of server.</span></span>
- <span data-ttu-id="41ccc-493">**NX_PTR_ERROR** (0x07) Ponteiro inválido passou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-493">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-494">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-494">Allowed From</span></span>

<span data-ttu-id="41ccc-495">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-495">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-496">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-496">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-497">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-497">See Also</span></span>

- <span data-ttu-id="41ccc-498">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="41ccc-498">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="41ccc-499">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="41ccc-499">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="41ccc-500">nx_secure_dtls_server_session_send,</span><span class="sxs-lookup"><span data-stu-id="41ccc-500">nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="41ccc-501">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="41ccc-501">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_server_trusted_certificate_add"></a><span data-ttu-id="41ccc-502">nx_secure_dtls_server_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="41ccc-502">nx_secure_dtls_server_trusted_certificate_add</span></span>

<span data-ttu-id="41ccc-503">Adicione um certificado ca fidedigno a um Servidor DTLS Seguro NetX</span><span class="sxs-lookup"><span data-stu-id="41ccc-503">Add a trusted CA certificate to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-504">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-504">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_trusted_certificate_add(
                                         NX_SECURE_DTLS_SERVER *server_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="41ccc-505">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-505">Description</span></span>

<span data-ttu-id="41ccc-506">Este serviço adiciona um certificado ca ou CA intermédio fidedigno a uma instância do Servidor DTLS e atribuído a todas as sessões internas do servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-506">This service adds a trusted CA or intermediate CA certificate to a DTLS Server instance and assigned to all the internal DTLS server sessions.</span></span> <span data-ttu-id="41ccc-507">Isto só é necessário se a autenticação do certificado do cliente X.509 for ativada utilizando *nx_secure_dtls_server_x509_client_verify_configure*.</span><span class="sxs-lookup"><span data-stu-id="41ccc-507">This is only necessary if X.509 Client certificate authentication is enabled using *nx_secure_dtls_server_x509_client_verify_configure*.</span></span> <span data-ttu-id="41ccc-508">O certificado adicional será usado para verificar os certificados do Cliente X.509.</span><span class="sxs-lookup"><span data-stu-id="41ccc-508">The added certificate will be used to verify incoming Client X.509 certificates.</span></span>

<span data-ttu-id="41ccc-509">O parâmetro cert_id é um identificador numérico, sem zero para o certificado.</span><span class="sxs-lookup"><span data-stu-id="41ccc-509">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="41ccc-510">Isto permite que o certificado seja facilmente removido ou encontrado no caso de existirem vários certificados de identidade com o mesmo Nome Comum X.509 presente na loja do servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-510">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS server store.</span></span> <span data-ttu-id="41ccc-511">Consulte o Guia de Utilizador NetX Secure TLS para obter mais informações sobre os certificados de servidor X.509.</span><span class="sxs-lookup"><span data-stu-id="41ccc-511">See the NetX Secure TLS User Guide for more information about X.509 server certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-512">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-512">Parameters</span></span>

- <span data-ttu-id="41ccc-513">**server_ptr** Ponteiro para uma instância do Servidor DTLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-513">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="41ccc-514">**certificado** Ponteiro para uma estrutura de certificado X.509 previamente inicializada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-514">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="41ccc-515">**cert_id** Identificador único numérico não zero para este certificado neste servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-515">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-516">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-516">Return Values</span></span>

- <span data-ttu-id="41ccc-517">**NX_SUCCESS** (0x00) Adição bem sucedida de certificado ao servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-517">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS server.</span></span>
- <span data-ttu-id="41ccc-518">**NX_PTR_ERROR** (0x07) Ponteiro inválido passou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-518">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="41ccc-519">**NX_INVALID_PARAMETERS** (0x4D) Foi aprovado um certificado de identificação de 0.</span><span class="sxs-lookup"><span data-stu-id="41ccc-519">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-520">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-520">Allowed From</span></span>

<span data-ttu-id="41ccc-521">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-521">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-522">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-522">Example</span></span>

<span data-ttu-id="41ccc-523">\*Consulte a referência para *nx_secure_dtls_server_create* para obter um exemplo mais completo.</span><span class="sxs-lookup"><span data-stu-id="41ccc-523">\*See reference for *nx_secure_dtls_server_create* for a more complete example.</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-524">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-524">See Also</span></span>

- <span data-ttu-id="41ccc-525">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="41ccc-525">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="41ccc-526">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send.</span><span class="sxs-lookup"><span data-stu-id="41ccc-526">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="41ccc-527">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="41ccc-527">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="41ccc-528">nx_secure_dtls_server_local_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="41ccc-528">nx_secure_dtls_server_local_certificate_add,</span></span>
- <span data-ttu-id="41ccc-529">nx_secure_dtls_server_trusted_certificate_remove,</span><span class="sxs-lookup"><span data-stu-id="41ccc-529">nx_secure_dtls_server_trusted_certificate_remove,</span></span>
- <span data-ttu-id="41ccc-530">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="41ccc-530">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_trusted_certificate_remove"></a><span data-ttu-id="41ccc-531">nx_secure_dtls_server_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="41ccc-531">nx_secure_dtls_server_trusted_certificate_remove</span></span>

<span data-ttu-id="41ccc-532">Remova um certificado ca fidedigno de um Servidor DTLS Seguro NetX</span><span class="sxs-lookup"><span data-stu-id="41ccc-532">Remove a trusted CA certificate from a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-533">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-533">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_trusted_certificate_remove(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *common_name,
                                UINT common_name_length,
                                UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="41ccc-534">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-534">Description</span></span>

<span data-ttu-id="41ccc-535">Este serviço remove um certificado de CA fidedigno de uma instância do DTLS Server.</span><span class="sxs-lookup"><span data-stu-id="41ccc-535">This service removes a trusted CA certificate from a DTLS Server instance.</span></span> <span data-ttu-id="41ccc-536">Os certificados de CA fidedignos só são necessários para um Servidor DTLS para o qual a verificação do certificado de cliente X.509 foi ativada através da chamada *nx_secure_dtls_server_x509_client_verify_configure*.</span><span class="sxs-lookup"><span data-stu-id="41ccc-536">Trusted CA certificates are only necessary for a DTLS Server for which X.509 Client certificate verification has been enabled by calling *nx_secure_dtls_server_x509_client_verify_configure*.</span></span>

<span data-ttu-id="41ccc-537">O certificado a retirar pode ser identificado pelo seu Nome Comum X.509 ou pelo cert_id numérico que foi atribuído na chamada a *nx_secure_dtls_server_trusted_certificate_add*.</span><span class="sxs-lookup"><span data-stu-id="41ccc-537">The certificate to be removed can be identified either by its X.509 Common Name or by the numeric cert_id that was assigned in the call to *nx_secure_dtls_server_trusted_certificate_add*.</span></span> <span data-ttu-id="41ccc-538">O cert_id é utilizado apenas para identificar o certificado e é mantido pelo pedido.</span><span class="sxs-lookup"><span data-stu-id="41ccc-538">The cert_id is only used to identify the certificate and is maintained by the application.</span></span> <span data-ttu-id="41ccc-539">Se o nome comum for utilizado em vez do identificador de certificado numérico, o parâmetro cert_id deve ser definido para 0.</span><span class="sxs-lookup"><span data-stu-id="41ccc-539">If the Common Name is used instead of the numeric certificate identifier, the cert_id parameter should be set to 0.</span></span>

> [!NOTE]
> <span data-ttu-id="41ccc-540">Remover um certificado enquanto um aperto de mão DTLS está a ser processado pode resultar em comportamento inesperado.</span><span class="sxs-lookup"><span data-stu-id="41ccc-540">Removing a certificate while a DTLS handshake is being processed may result in unexpected behavior.</span></span> <span data-ttu-id="41ccc-541">O *serviço nx_secure_dtls_server_stop* deve ser chamado antes de retirar os certificados.</span><span class="sxs-lookup"><span data-stu-id="41ccc-541">The service *nx_secure_dtls_server_stop* should be called before removing certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-542">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-542">Parameters</span></span>

- <span data-ttu-id="41ccc-543">**server_ptr** Ponteiro para uma instância do Servidor DTLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-543">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="41ccc-544">**common_name** X.509 CommonName do certificado a remover.</span><span class="sxs-lookup"><span data-stu-id="41ccc-544">**common_name** X.509 CommonName of the certificate to remove.</span></span> <span data-ttu-id="41ccc-545">Se isto for usado, passe cert_id como zero.</span><span class="sxs-lookup"><span data-stu-id="41ccc-545">If this is used, pass cert_id as zero.</span></span>
- <span data-ttu-id="41ccc-546">**common_name_length** Comprimento de common_name cordas em bytes.</span><span class="sxs-lookup"><span data-stu-id="41ccc-546">**common_name_length** Length of common_name string in bytes.</span></span>
- <span data-ttu-id="41ccc-547">**cert_id** Identificador único numérico não zero para este certificado neste servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-547">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span> <span data-ttu-id="41ccc-548">Se isto for utilizado, passe NX_NULL para o parâmetro common_name.</span><span class="sxs-lookup"><span data-stu-id="41ccc-548">If this is used, pass NX_NULL for the common_name parameter.</span></span>


### <a name="return-values"></a><span data-ttu-id="41ccc-549">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-549">Return Values</span></span>

- <span data-ttu-id="41ccc-550">**NX_SUCCESS** (0x00) Remoção bem sucedida do certificado do servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-550">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS server.</span></span>
- <span data-ttu-id="41ccc-551">**NX_PTR_ERROR** (0x07) Ponteiro inválido passou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-551">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="41ccc-552">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Não foi encontrado nenhum certificado correspondente ao cert_id ou common_name no servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-552">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS server.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-553">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-553">Allowed From</span></span>

<span data-ttu-id="41ccc-554">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-554">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-555">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-555">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-556">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-556">See Also</span></span>

- <span data-ttu-id="41ccc-557">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="41ccc-557">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="41ccc-558">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="41ccc-558">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="41ccc-559">nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="41ccc-559">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="41ccc-560">nx_secure_dtls_server_trusted_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="41ccc-560">nx_secure_dtls_server_trusted_certificate_add,</span></span>
- <span data-ttu-id="41ccc-561">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="41ccc-561">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_x509_client_verify_configure"></a><span data-ttu-id="41ccc-562">nx_secure_dtls_server_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="41ccc-562">nx_secure_dtls_server_x509_client_verify_configure</span></span>

<span data-ttu-id="41ccc-563">Configure um Servidor DTLS Seguro NetX para solicitar e verificar certificados de cliente</span><span class="sxs-lookup"><span data-stu-id="41ccc-563">Configure a NetX Secure DTLS Server to request and verify client certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-564">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-564">Prototype</span></span>

```C
UINT nx_secure_dtls_server_x509_client_verify_configure(
                           NX_SECURE_DTLS_SERVER *server_ptr,
                               UINT certs_per_session,
                               UCHAR *certs_buffer, ULONG buffer_size);

```

### <a name="description"></a><span data-ttu-id="41ccc-565">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-565">Description</span></span>

<span data-ttu-id="41ccc-566">Este serviço configura um Servidor DTLS para solicitar e verificar certificados de cliente DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-566">This service configures a DTLS Server to request and verify DTLS Client certificates.</span></span> <span data-ttu-id="41ccc-567">Esta função opcional é utilizada quando são desejados certificados X.509 para a autenticação do cliente em vez de outros mecanismos (por exemplo, uma Chave Pré-Partilhada).</span><span class="sxs-lookup"><span data-stu-id="41ccc-567">This optional feature is used when X.509 certificates are desired for client authentication in place of other mechanisms (e.g. a Pre-Shared Key).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="41ccc-568">*Quando um Servidor DTLS estiver configurado para verificar os certificados de cliente que utilizam este serviço, pelo menos um certificado ca fidedigno deve ser adicionado ao servidor usando nx_secure_dtls_server_trusted_certificate_add ou o servidor rejeitará todas as ligações do cliente que chegam porque não poderá verificar os certificados do cliente contra a loja fidedigna.*</span><span class="sxs-lookup"><span data-stu-id="41ccc-568">*When a DTLS Server is configured to verify client certificates using this service, at least one trusted CA certificate must be added to the server using nx_secure_dtls_server_trusted_certificate_add or the server will reject all incoming client connections because it will be unable to verify client certificates against the trusted store.*</span></span>

<span data-ttu-id="41ccc-569">Ao ligar para este serviço, a instância do DTLS Server irá (uma vez iniciada) solicitar certificados de cliente como parte do aperto de mão DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-569">Upon calling this service, the DTLS Server instance will (once started) request client certificates as part of the DTLS handshake.</span></span> <span data-ttu-id="41ccc-570">Assumindo que o cliente está devidamente configurado com um certificado de identidade (e cadeia de certificados associado quando aplicável), o DTLS Server requer que a memória seja alocado para processar os dados do certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="41ccc-570">Assuming the client is properly configured with an identity certificate (and associated certificate chain when applicable), the DTLS Server requires memory to be allocated to process the client certificate data.</span></span> <span data-ttu-id="41ccc-571">Esta memória é passada como o *parâmetro certs_buffer.*</span><span class="sxs-lookup"><span data-stu-id="41ccc-571">This memory is passed in as the *certs_buffer* parameter.</span></span>

<span data-ttu-id="41ccc-572">O certs_buffer deve ser dimensionado para acomodar a maior cadeia de certificados esperada de um cliente DTLS, *o que vezes o número de sessões de servidores DTLS*.</span><span class="sxs-lookup"><span data-stu-id="41ccc-572">The certs_buffer must be sized to accommodate the largest expected certificate chain from a DTLS client, *times the number of DTLS server sessions*.</span></span> <span data-ttu-id="41ccc-573">O tampão é dividido entre as sessões disponíveis utilizando o parâmetro *certs_per_session* que representa o número máximo esperado de certificados numa cadeia de certificados do Cliente.</span><span class="sxs-lookup"><span data-stu-id="41ccc-573">The buffer is divided amongst the available sessions using the *certs_per_session* parameter which represents the maximum expected number of certificates in a Client certificate chain.</span></span> <span data-ttu-id="41ccc-574">O tampão também precisa de fornecer espaço para a estrutura de dados NX_SECURE_X509_CERT que é usada para analisar os dados do certificado.</span><span class="sxs-lookup"><span data-stu-id="41ccc-574">The buffer also needs to provide space for the NX_SECURE_X509_CERT data structure which is used to parse the certificate data.</span></span>

<span data-ttu-id="41ccc-575">O cálculo do tamanho adequado do tampão pode ser feito com a seguinte fórmula:</span><span class="sxs-lookup"><span data-stu-id="41ccc-575">Calculating the proper buffer size can be done with the following formula:</span></span>

```C
buffer_size = (# of DTLS sessions in server) *
                (certs_per_session) *
                (    maximum expected certificate size +
                      sizeof(NX_SECURE_X509_CERT)    )

```

- <span data-ttu-id="41ccc-576">O número de sessões de DTLS é determinado pelo tamanho do tampão de sessão passado para nx_secure_dtls_server_create.</span><span class="sxs-lookup"><span data-stu-id="41ccc-576">The number of DTLS sessions is determined by the size of the session buffer passed into nx_secure_dtls_server_create.</span></span>
- <span data-ttu-id="41ccc-577">certs_per_session deve ser definido para o número máximo esperado de certificados em qualquer cadeia de certificados de cliente.</span><span class="sxs-lookup"><span data-stu-id="41ccc-577">certs_per_session should be set to the maximum expected number of certificates in any client certificate chain.</span></span>
- <span data-ttu-id="41ccc-578">O tamanho máximo esperado do certificado depende da aplicação, tamanhos-chave e outros fatores, mas 2KB é geralmente suficiente.</span><span class="sxs-lookup"><span data-stu-id="41ccc-578">The maximum expected certificate size is dependent on the application, key sizes, and other factors but 2KB is generally sufficient.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-579">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-579">Parameters</span></span>

- <span data-ttu-id="41ccc-580">**server_ptr** Ponteiro para uma instância do Servidor DTLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-580">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="41ccc-581">**certs_per_session** Número de certificados a atribuir a cada sessão de servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-581">**certs_per_session** Number of certificates to allocate to each DTLS server session.</span></span>
- <span data-ttu-id="41ccc-582">**certs_buffer** Espaço tampão para dados de certificados de entrada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-582">**certs_buffer** Buffer space for incoming certificate data.</span></span>
- <span data-ttu-id="41ccc-583">**buffer_size** Tamanho do tampão de certificado.</span><span class="sxs-lookup"><span data-stu-id="41ccc-583">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-584">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-584">Return Values</span></span>

- <span data-ttu-id="41ccc-585">**NX_SUCCESS** (0x00) Configuração bem sucedida da verificação do cliente X.509.</span><span class="sxs-lookup"><span data-stu-id="41ccc-585">**NX_SUCCESS** (0x00) Successful configuration of X.509 Client verification.</span></span>
- <span data-ttu-id="41ccc-586">**NX_PTR_ERROR** (0x07) Ponteiro inválido passou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-586">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="41ccc-587">**NX_INVALID_PARAMETERS** (0x4D) Loja de certificados inválida (caso DTLSserver não initilizada?).</span><span class="sxs-lookup"><span data-stu-id="41ccc-587">**NX_INVALID_PARAMETERS** (0x4D) Invalid certificate store (DTLSserver instance not initalized?).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-588">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-588">Allowed From</span></span>

<span data-ttu-id="41ccc-589">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-589">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-590">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-590">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-591">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-591">See Also</span></span>

- <span data-ttu-id="41ccc-592">nx_secure_dtls_server_x509_client_verify_disable,</span><span class="sxs-lookup"><span data-stu-id="41ccc-592">nx_secure_dtls_server_x509_client_verify_disable,</span></span>
- <span data-ttu-id="41ccc-593">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="41ccc-593">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="41ccc-594">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="41ccc-594">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="41ccc-595">nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="41ccc-595">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="41ccc-596">nx_secure_dtls_server_trusted_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="41ccc-596">nx_secure_dtls_server_trusted_certificate_add,</span></span>
- <span data-ttu-id="41ccc-597">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="41ccc-597">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_x509_client_verify_disable"></a><span data-ttu-id="41ccc-598">nx_secure_dtls_server_x509_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="41ccc-598">nx_secure_dtls_server_x509_client_verify_disable</span></span>

<span data-ttu-id="41ccc-599">Desativa a verificação do certificado X.509 do cliente para um Servidor DTLS Seguro NetX</span><span class="sxs-lookup"><span data-stu-id="41ccc-599">Disables client X.509 certificate verification for a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-600">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-600">Prototype</span></span>

```C
UINT nx_secure_dtls_server_x509_client_verify_disable(
                           NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="41ccc-601">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-601">Description</span></span>

<span data-ttu-id="41ccc-602">Este serviço desativa a verificação do certificado de cliente X.509 num Servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-602">This service disables X.509 Client certificate verification on a DTLS Server.</span></span> <span data-ttu-id="41ccc-603">O serviço não tem efeito se a verificação do certificado do Cliente X.509 não estiver ativada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-603">The service has no effect if X.509 Client certificate verification is not enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="41ccc-604">A desativação da autenticação do cliente numa instância ativa do DTLS Server pode resultar num comportamento imprevisível.</span><span class="sxs-lookup"><span data-stu-id="41ccc-604">Disabling client authentication on an active DTLS Server instance may result in unpredictable behavior.</span></span> <span data-ttu-id="41ccc-605">O serviço nx_secure_dtls_server_stop deve ser chamado antes de alterar o estado do servidor.</span><span class="sxs-lookup"><span data-stu-id="41ccc-605">The nx_secure_dtls_server_stop service should be called before changing server state.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-606">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-606">Parameters</span></span>

- <span data-ttu-id="41ccc-607">**server_ptr** Ponteiro para uma instância do Servidor DTLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-607">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-608">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-608">Return Values</span></span>

- <span data-ttu-id="41ccc-609">**NX_SUCCESS** (0x00) Desativação bem sucedida da autenticação do cliente X.509.</span><span class="sxs-lookup"><span data-stu-id="41ccc-609">**NX_SUCCESS** (0x00) Successful disabling of X.509 client authentication.</span></span>
- <span data-ttu-id="41ccc-610">**NX_PTR_ERROR** (0x07) Ponteiro inválido passou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-610">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-611">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-611">Allowed From</span></span>

<span data-ttu-id="41ccc-612">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-612">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-613">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-613">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-614">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-614">See Also</span></span>

- <span data-ttu-id="41ccc-615">nx_secure_dtls_server_x509_client_verify_configure,</span><span class="sxs-lookup"><span data-stu-id="41ccc-615">nx_secure_dtls_server_x509_client_verify_configure,</span></span>
- <span data-ttu-id="41ccc-616">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="41ccc-616">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="41ccc-617">nx_secure_dtls_server_session_start,</span><span class="sxs-lookup"><span data-stu-id="41ccc-617">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="41ccc-618">nx_secure_dtls_server_session_stop,</span><span class="sxs-lookup"><span data-stu-id="41ccc-618">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="41ccc-619">nx_secure_dtls_server_trusted_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="41ccc-619">nx_secure_dtls_server_trusted_certificate_add,</span></span>
- <span data-ttu-id="41ccc-620">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="41ccc-620">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_client_info_get"></a><span data-ttu-id="41ccc-621">nx_secure_dtls_session_client_info_get</span><span class="sxs-lookup"><span data-stu-id="41ccc-621">nx_secure_dtls_session_client_info_get</span></span>

<span data-ttu-id="41ccc-622">Obtenha informações remotas do cliente a partir de uma sessão do DTLS Server</span><span class="sxs-lookup"><span data-stu-id="41ccc-622">Get remote client information from a DTLS Server session</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-623">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-623">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_client_info_get(
                                    NX_SECURE_DTLS_SESSION *session_ptr,
                                    NXD_ADDRESS *client_ip_address,
                                    UINT *client_port, UINT *local_port);

```

### <a name="description"></a><span data-ttu-id="41ccc-624">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-624">Description</span></span>

<span data-ttu-id="41ccc-625">Este serviço devolve a informação de rede sobre um Cliente DTLS que está ligado a uma sessão particular do DTLS Server.</span><span class="sxs-lookup"><span data-stu-id="41ccc-625">This service returns the network information about a DTLS Client that is connected to a particular DTLS Server session.</span></span> <span data-ttu-id="41ccc-626">A informação devolvida consiste no endereço IP do cliente remoto e na porta UDP, bem como na porta do servidor local à qual o cliente está ligado.</span><span class="sxs-lookup"><span data-stu-id="41ccc-626">The information returned consists of the remote client’s IP address and UDP port, as well as the local server port to which the client is connected.</span></span>

<span data-ttu-id="41ccc-627">Em geral, a instância da sessão DTLS será a obtida na invocação de uma das rotinas de chamada de notificação DTLS (por exemplo, as chamadas connect_notify ou receive_notify transmitidas para nx_secure_dtls_server_create).</span><span class="sxs-lookup"><span data-stu-id="41ccc-627">In general, the DTLS session instance will be the one obtained in the invocation of one of the DTLS notification callback routines (e.g. the connect_notify or receive_notify callbacks passed into nx_secure_dtls_server_create).</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-628">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-628">Parameters</span></span>

- <span data-ttu-id="41ccc-629">**session_ptr** Ponteiro para uma sessão de sessão de servidor DTLS ativa.</span><span class="sxs-lookup"><span data-stu-id="41ccc-629">**session_ptr** Pointer to an active DTLS server session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-630">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-630">Return Values</span></span>

- <span data-ttu-id="41ccc-631">**NX_SUCCESS** (0x00) Eliminação bem sucedida do servidor.</span><span class="sxs-lookup"><span data-stu-id="41ccc-631">**NX_SUCCESS** (0x00) Successful deletion of server.</span></span>
- <span data-ttu-id="41ccc-632">**NX_PTR_ERROR** (0x07) Ponteiro inválido passou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-632">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="41ccc-633">**NX_INVALID_SOCKET** (0x13) A tomada UDP associada não é válida (sessão não inicializada?).</span><span class="sxs-lookup"><span data-stu-id="41ccc-633">**NX_INVALID_SOCKET** (0x13) The associated UDP socket is not valid (session not initialized?).</span></span>
- <span data-ttu-id="41ccc-634">**NX_NOT_CONNECTED** (0x38) tomada UDP não está ligada – a ligação do cliente caiu ou ainda não foi estabelecida.</span><span class="sxs-lookup"><span data-stu-id="41ccc-634">**NX_NOT_CONNECTED** (0x38) UDP socket is not connected – client connection dropped or not yet established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-635">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-635">Allowed From</span></span>

<span data-ttu-id="41ccc-636">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-636">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-637">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-637">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-638">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-638">See Also</span></span>

- <span data-ttu-id="41ccc-639">nx_secure_dtls_server_start, nx_secure_dtls_server_stop.</span><span class="sxs-lookup"><span data-stu-id="41ccc-639">nx_secure_dtls_server_start, nx_secure_dtls_server_stop,</span></span>
- <span data-ttu-id="41ccc-640">nx_secure_dtls_server_create, nx_secure_dtls_server_delete,</span><span class="sxs-lookup"><span data-stu-id="41ccc-640">nx_secure_dtls_server_create, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="41ccc-641">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send.</span><span class="sxs-lookup"><span data-stu-id="41ccc-641">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="41ccc-642">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="41ccc-642">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_session_create"></a><span data-ttu-id="41ccc-643">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="41ccc-643">nx_secure_dtls_session_create</span></span>

<span data-ttu-id="41ccc-644">Criar e configurar uma Sessão de DTLS Segura NetX</span><span class="sxs-lookup"><span data-stu-id="41ccc-644">Create and configure a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-645">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-645">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="41ccc-646">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-646">Description</span></span>

<span data-ttu-id="41ccc-647">Este serviço cria e configura uma sessão DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-647">This service creates and configures a DTLS session.</span></span> <span data-ttu-id="41ccc-648">Geralmente, isto será usado para criar sessões de Cliente DTLS, uma vez que as sessões do DTLS Server são geridas com o mecanismo DTLS Server (ver *nx_secure_dtls_server_create),* mas pode haver casos em que uma aplicação precisa de criar uma única instância de sessão de Sessão DTLS Server autónoma, caso em que este serviço pode ser utilizado <sup>7</sup>.</span><span class="sxs-lookup"><span data-stu-id="41ccc-648">Generally, this will be used to create DTLS Client sessions as DTLS Server sessions are managed with the DTLS Server mechanism (see *nx_secure_dtls_server_create*), but there may be instances where an application needs to create a single stand-alone DTLS Server session instance in which case this service may be used<sup>7</sup>.</span></span>

<span data-ttu-id="41ccc-649">Os parâmetros configuram a informação e a atribuição de memória necessárias para instantaneaizar uma sessão de DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-649">The parameters configure the information and memory allocation needed to instantiate a DTLS session.</span></span> <span data-ttu-id="41ccc-650">O parâmetro crypto_table é uma tabela TLS que contém todas as rotinas criptográficas necessárias para encriptação e autenticação TLS/DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-650">The crypto_table parameter is a TLS table containing all of the cryptographic routines needed for TLS/DTLS encryption and authentication.</span></span> <span data-ttu-id="41ccc-651">O metadata_buffer é utilizado para caclulações de encriptação (ver nx_secure_tls_metadata_size_calculate no Guia do Utilizador NetX Secure TLS), e o packet_reassembly_buffer é utilizado para remontar os dados do UDP num registo completo de DTLS para desencriptação.</span><span class="sxs-lookup"><span data-stu-id="41ccc-651">The metadata_buffer is used for encryption caclulations (see nx_secure_tls_metadata_size_calculate in the NetX Secure TLS User Guide), and the packet_reassembly_buffer is used to reassemble UDP datagrams into a complete DTLS record for decryption.</span></span>

<span data-ttu-id="41ccc-652">Os certs_number e remote_certificate_buffer são necessários para os Clientes DTLS que precisam de espaço para armazenar e processar a cadeia de certificados DTLS Server.</span><span class="sxs-lookup"><span data-stu-id="41ccc-652">The certs_number and remote_certificate_buffer are required for DTLS Clients which need space to store and process the incoming DTLS Server certificate chain.</span></span> <span data-ttu-id="41ccc-653">O tampão deve ser capaz de acomodar o tamanho máximo esperado da cadeia de certificados para qualquer servidor ao qual se conecte.</span><span class="sxs-lookup"><span data-stu-id="41ccc-653">The buffer must be able to accommodate the maximum expected size of the certificate chain for any server to which it will connect.</span></span> <span data-ttu-id="41ccc-654">O tampão é dividido pelo número de certificados esperados (certs_number parâmetro) e deve também ser suficientemente grande para deter uma estrutura NX_SECURE_X509_CERT por certificado.</span><span class="sxs-lookup"><span data-stu-id="41ccc-654">The buffer is divided up by the number of expected certificates (certs_number parameter) and must also be large enough to hold one NX_SECURE_X509_CERT structure per certificate.</span></span> <span data-ttu-id="41ccc-655">O tamanho do tampão pode ser determinado com a seguinte fórmula:</span><span class="sxs-lookup"><span data-stu-id="41ccc-655">The buffer size can be determined using the following formula:</span></span>

```C
remote_certificate_buffer_size = (certs_number) *
                 (maximum cert size + sizeof(NX_SECURE_X509_CERT))
```

- <span data-ttu-id="41ccc-656">certs_number é o número máximo esperado de certificados na cadeia de certificados do servidor</span><span class="sxs-lookup"><span data-stu-id="41ccc-656">certs_number is the expected maximum number of certificates in the server’s certificate chain</span></span>
- <span data-ttu-id="41ccc-657">O tamanho máximo do certificado depende do tamanho das chaves utilizadas e das informações no certificado, mas 2KB é geralmente suficiente.</span><span class="sxs-lookup"><span data-stu-id="41ccc-657">Maximum certificate size is dependent on the size of keys being used and the information in the certificate, but 2KB is generally sufficient.</span></span>

<span data-ttu-id="41ccc-658">**7** A criação de sessões do DTLS Server com esta rotina não é recomendada e vem com algumas limitações.</span><span class="sxs-lookup"><span data-stu-id="41ccc-658">**7** Creating DTLS Server sessions with this routine is not recommended and comes with some limitations.</span></span> <span data-ttu-id="41ccc-659">A principal questão é que a sessão não tratará graciosamente as ligações adicionais do cliente – uma vez que a UDP não tem ligação, um segundo cliente pode legalmente enviar dados para a porta UDP do servidor quando uma sessão anterior do DTLS ainda estiver ativa, o que faria com que a sessão do servidor terminasse com um erro.</span><span class="sxs-lookup"><span data-stu-id="41ccc-659">The primary issue is that the session will not handle additional client connections gracefully – since UDP is connectionless a second client can legally send data to the server’s UDP port when a previous DTLS session is still active which would cause the server session to end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-660">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-660">Parameters</span></span>

- <span data-ttu-id="41ccc-661">**dtls_session** Ponteiro para uma estrutura de Sessão DTLS não iniializada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-661">**dtls_session** Pointer to an uninitialized DTLS Session structure.</span></span>
- <span data-ttu-id="41ccc-662">**crypto_table** Ponteiro para uma estrutura de tabela de encriptação TLS/DTLS utilizada para todas as operações criptográficas.</span><span class="sxs-lookup"><span data-stu-id="41ccc-662">**crypto_table** Pointer to a TLS/DTLS encryption table structure used for all cryptographic operations.</span></span>
- <span data-ttu-id="41ccc-663">**crypto_metadata_buffer** Espaço tampão para cálculos de operação criptográfica e informações do estado.</span><span class="sxs-lookup"><span data-stu-id="41ccc-663">**crypto_metadata_buffer** Buffer space for cryptographic operation calculations and state information.</span></span>
- <span data-ttu-id="41ccc-664">**crypto_metadata_size** Tamanho do tampão de metadados.</span><span class="sxs-lookup"><span data-stu-id="41ccc-664">**crypto_metadata_size** Size of metadata buffer.</span></span>
- <span data-ttu-id="41ccc-665">**packet_reassembly_buffer** Tampão usado pela DTLS para remontar dados de UDP em registos DTLS para desencriptação.</span><span class="sxs-lookup"><span data-stu-id="41ccc-665">**packet_reassembly_buffer** Buffer used by DTLS to reassemble UDP data into DTLS records for decryption.</span></span>
- <span data-ttu-id="41ccc-666">**packet_reassembly_buffer_size** Tamanho do tampão de remontagem.</span><span class="sxs-lookup"><span data-stu-id="41ccc-666">**packet_reassembly_buffer_size** Size of reassembly buffer.</span></span> <span data-ttu-id="41ccc-667">Geralmente deve ser superior a 16KB, mas pode ser menor dependendo da aplicação.</span><span class="sxs-lookup"><span data-stu-id="41ccc-667">Generally should be greater than 16KB but may be smaller depending on application.</span></span>
- <span data-ttu-id="41ccc-668">**certs_number** Número máximo esperado de certificados na cadeia de certificados do servidor remoto.</span><span class="sxs-lookup"><span data-stu-id="41ccc-668">**certs_number** Maximum expected number of certificates in the remote server’s certificate chain.</span></span>
- <span data-ttu-id="41ccc-669">**remote_certificate_buffer** Espaço tampão para dados de certificados de entrada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-669">**remote_certificate_buffer** Buffer space for incoming certificate data.</span></span>
- <span data-ttu-id="41ccc-670">**remote_certificate_buffer_size** Tamanho do tampão de certificado.</span><span class="sxs-lookup"><span data-stu-id="41ccc-670">**remote_certificate_buffer_size** Size of the certificate buffer.</span></span>


### <a name="return-values"></a><span data-ttu-id="41ccc-671">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-671">Return Values</span></span>

- <span data-ttu-id="41ccc-672">**NX_SUCCESS** (0x00) Criação bem sucedida da sessão.</span><span class="sxs-lookup"><span data-stu-id="41ccc-672">**NX_SUCCESS** (0x00) Successful creation of session.</span></span>
- <span data-ttu-id="41ccc-673">**NX_PTR_ERROR** (0x07) Sessão inválida ou ponteiro tampão.</span><span class="sxs-lookup"><span data-stu-id="41ccc-673">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>
- <span data-ttu-id="41ccc-674">**NX_INVALID_PARAMETERS** (0x4D) Não há espaço tampão suficiente para remontagem de pacotes, certificados ou criptografia.</span><span class="sxs-lookup"><span data-stu-id="41ccc-674">**NX_INVALID_PARAMETERS** (0x4D) Not enough buffer space for packet reassembly, certificates, or cryptography.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-675">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-675">Allowed From</span></span>

<span data-ttu-id="41ccc-676">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-676">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-677">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-677">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-678">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-678">See Also</span></span>

- <span data-ttu-id="41ccc-679">nx_secure_dtls_client_session_start,nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="41ccc-679">nx_secure_dtls_client_session_start,nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="41ccc-680">nx_secure_dtls_session_send</span><span class="sxs-lookup"><span data-stu-id="41ccc-680">nx_secure_dtls_session_send</span></span>

## <a name="nx_secure_dtls_session_delete"></a><span data-ttu-id="41ccc-681">nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="41ccc-681">nx_secure_dtls_session_delete</span></span>

<span data-ttu-id="41ccc-682">Liberte os recursos utilizados por uma Sessão DTLS NetX Secure</span><span class="sxs-lookup"><span data-stu-id="41ccc-682">Free up resources used by a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-683">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-683">Prototype</span></span>

```C
UINT nx_secure_dtls_session_delete(
                        NX_SECURE_DTLS_SESSION *dtls_session);

```

### <a name="description"></a><span data-ttu-id="41ccc-684">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-684">Description</span></span>

<span data-ttu-id="41ccc-685">Este serviço elimina uma sessão DTLS, libertando todos os recursos que foram atribuídos quando foi criado.</span><span class="sxs-lookup"><span data-stu-id="41ccc-685">This service deletes a DTLS session, freeing up any resources that were allocated when it was created.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-686">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-686">Parameters</span></span>

- <span data-ttu-id="41ccc-687">**dtls_session** Ponteiro para uma estrutura de Sessão DTLS que foi inicializada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="41ccc-687">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-688">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-688">Return Values</span></span>

- <span data-ttu-id="41ccc-689">**NX_SUCCESS** (0x00) Supressão bem sucedida da sessão.</span><span class="sxs-lookup"><span data-stu-id="41ccc-689">**NX_SUCCESS** (0x00) Successful deletion of session.</span></span>
- <span data-ttu-id="41ccc-690">**NX_PTR_ERROR** (0x07) Sessão inválida ou ponteiro tampão.</span><span class="sxs-lookup"><span data-stu-id="41ccc-690">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-691">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-691">Allowed From</span></span>

<span data-ttu-id="41ccc-692">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-692">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-693">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-693">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-694">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-694">See Also</span></span>

- <span data-ttu-id="41ccc-695">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="41ccc-695">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="41ccc-696">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="41ccc-696">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_session_end"></a><span data-ttu-id="41ccc-697">nx_secure_dtls_session_end</span><span class="sxs-lookup"><span data-stu-id="41ccc-697">nx_secure_dtls_session_end</span></span>

<span data-ttu-id="41ccc-698">Desligue uma Sessão DTLS segura ativa da NetX</span><span class="sxs-lookup"><span data-stu-id="41ccc-698">Shut down an active NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-699">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-699">Prototype</span></span>

```C
UINT nx_secure_dtls_session_end(NX_SECURE_DTLS_SESSION *dtls_session,
                                UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="41ccc-700">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-700">Description</span></span>

<span data-ttu-id="41ccc-701">Este serviço termina uma sessão DTLS ativa enviando um alerta TLS/DTLS CloseNotify para o anfitrião remoto.</span><span class="sxs-lookup"><span data-stu-id="41ccc-701">This service ends an active DTLS session by sending a TLS/DTLS CloseNotify alert to the remote host.</span></span> <span data-ttu-id="41ccc-702">O endereço IP e a porta utilizados são os utilizados na chamada anterior para nx_secure_dtls_session_send.</span><span class="sxs-lookup"><span data-stu-id="41ccc-702">The IP address and port used are those used in the previous call to nx_secure_dtls_session_send.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-703">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-703">Parameters</span></span>

- <span data-ttu-id="41ccc-704">**dtls_session** Ponteiro para uma estrutura de Sessão DTLS que foi inicializada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="41ccc-704">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>
- <span data-ttu-id="41ccc-705">**wait_option** ThreadX espera valor para usar para operações de rede.</span><span class="sxs-lookup"><span data-stu-id="41ccc-705">**wait_option** ThreadX wait value to use for network operations.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-706">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-706">Return Values</span></span>

- <span data-ttu-id="41ccc-707">**NX_SUCCESS** (0x00) Supressão bem sucedida da sessão.</span><span class="sxs-lookup"><span data-stu-id="41ccc-707">**NX_SUCCESS** (0x00) Successful deletion of session.</span></span>
- <span data-ttu-id="41ccc-708">**NX_PTR_ERROR** (0x07) Sessão inválida ou ponteiro tampão.</span><span class="sxs-lookup"><span data-stu-id="41ccc-708">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>
- <span data-ttu-id="41ccc-709">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Não podia atribuir pacotes para alerta CloseNotify.</span><span class="sxs-lookup"><span data-stu-id="41ccc-709">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate packet(s) for CloseNotify alert.</span></span>
- <span data-ttu-id="41ccc-710">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Erro interno provável – rotina criptográfica não reconhecida.</span><span class="sxs-lookup"><span data-stu-id="41ccc-710">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Likely internal error – cryptographic routine not recognized.</span></span>
- <span data-ttu-id="41ccc-711">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Envio subjacente da UDP falhou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-711">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Underlying UDP send failed.</span></span>
- <span data-ttu-id="41ccc-712">**NX_IP_ADDRESS_ERROR** (0x21) Erro com endereço IP do anfitrião remoto.</span><span class="sxs-lookup"><span data-stu-id="41ccc-712">**NX_IP_ADDRESS_ERROR** (0x21) Error with remote host IP address.</span></span>
- <span data-ttu-id="41ccc-713">**NX_NOT_BOUND** (0x24) Tomada UDP subjacente não está ligada à porta.</span><span class="sxs-lookup"><span data-stu-id="41ccc-713">**NX_NOT_BOUND** (0x24) Underlying UDP socket not bound to port.</span></span>
- <span data-ttu-id="41ccc-714">**NX_INVALID_PORT** (0x46) Porta UDP inválida.</span><span class="sxs-lookup"><span data-stu-id="41ccc-714">**NX_INVALID_PORT** (0x46) Invalid UDP port.</span></span>
- <span data-ttu-id="41ccc-715">**NX_PORT_UNAVAILABLE** (0x23) porta UDP não disponível para utilização.</span><span class="sxs-lookup"><span data-stu-id="41ccc-715">**NX_PORT_UNAVAILABLE** (0x23) UDP port not available for use.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-716">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-716">Allowed From</span></span>

<span data-ttu-id="41ccc-717">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-717">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-718">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-718">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-719">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-719">See Also</span></span>

- <span data-ttu-id="41ccc-720">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="41ccc-720">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="41ccc-721">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="41ccc-721">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_session_local_certificate_add"></a><span data-ttu-id="41ccc-722">nx_secure_dtls_session_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="41ccc-722">nx_secure_dtls_session_local_certificate_add</span></span>

<span data-ttu-id="41ccc-723">Adicione um certificado de identidade local a uma Sessão de DTLS Segura NetX</span><span class="sxs-lookup"><span data-stu-id="41ccc-723">Add a local identity certificate to a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-724">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-724">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_local_certificate_add(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            NX_SECURE_X509_CERT *certificate,
                            UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="41ccc-725">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-725">Description</span></span>

<span data-ttu-id="41ccc-726">Este serviço adiciona um certificado de identidade local a uma instância de Sessão DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-726">This service adds a local identity certificate to a DTLS Session instance.</span></span> <span data-ttu-id="41ccc-727">Em geral, este serviço será utilizado quando uma sessão do Cliente DTLS necessitar de fornecer um certificado de identidade a um servidor remoto.</span><span class="sxs-lookup"><span data-stu-id="41ccc-727">In general, this service will be used when a DTLS Client session needs to provide an identity certificate to a remote server host.</span></span> <span data-ttu-id="41ccc-728">Esta é uma configuração opcional para DTLS, pelo que um certificado não é geralmente necessário para clientes DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-728">This is an optional configuration for DTLS so a certificate is not generally required for DTLS Clients.</span></span> <span data-ttu-id="41ccc-729">Um certificado de identidade requer uma chave privada associada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-729">An identity certificate requires an associated private key.</span></span>

<span data-ttu-id="41ccc-730">O parâmetro cert_id é um identificador numérico, sem zero para o certificado.</span><span class="sxs-lookup"><span data-stu-id="41ccc-730">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="41ccc-731">Isto permite que o certificado seja facilmente removido ou encontrado no caso de existirem vários certificados de identidade com o mesmo Nome Comum X.509 presente na loja de certificados DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-731">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="41ccc-732">Consulte o Guia de Utilizador NetX Secure TLS para obter mais informações sobre os certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="41ccc-732">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-733">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-733">Parameters</span></span>

- <span data-ttu-id="41ccc-734">**session_ptr** Ponteiro para uma instância de Sessão DTLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-734">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="41ccc-735">**certificado** Ponteiro para uma estrutura de certificado X.509 previamente inicializada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-735">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="41ccc-736">**cert_id** Identificador único numérico não zero para este certificado neste servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-736">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-737">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-737">Return Values</span></span>

- <span data-ttu-id="41ccc-738">**NX_SUCCESS** (0x00) Adição bem sucedida de certificado à sessão DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-738">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS session.</span></span>
- <span data-ttu-id="41ccc-739">**NX_PTR_ERROR** (0x07) Ponteiro inválido passou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-739">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="41ccc-740">**NX_INVALID_PARAMETERS** (0x4D) Foi aprovado um certificado de identificação de 0.</span><span class="sxs-lookup"><span data-stu-id="41ccc-740">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-741">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-741">Allowed From</span></span>

<span data-ttu-id="41ccc-742">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-742">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-743">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-743">Example</span></span>

<span data-ttu-id="41ccc-744">\*Consulte a referência para *nx_secure_dtls_session_create* para obter um exemplo mais completo.</span><span class="sxs-lookup"><span data-stu-id="41ccc-744">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-745">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-745">See Also</span></span>

- <span data-ttu-id="41ccc-746">nx_secure_dtls_session_create, nx_secure_dtls_session_receive.</span><span class="sxs-lookup"><span data-stu-id="41ccc-746">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="41ccc-747">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span><span class="sxs-lookup"><span data-stu-id="41ccc-747">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="41ccc-748">nx_secure_dtls_session_local_certificate_remove,</span><span class="sxs-lookup"><span data-stu-id="41ccc-748">nx_secure_dtls_session_local_certificate_remove,</span></span>
- <span data-ttu-id="41ccc-749">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="41ccc-749">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_local_certificate_remove"></a><span data-ttu-id="41ccc-750">nx_secure_dtls_session_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="41ccc-750">nx_secure_dtls_session_local_certificate_remove</span></span>

<span data-ttu-id="41ccc-751">Remova um certificado de identidade local de uma Sessão de DTLS Segura netX</span><span class="sxs-lookup"><span data-stu-id="41ccc-751">Remove a local identity certificate from a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-752">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-752">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_local_certificate_remove(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         UCHAR *common_name,
                                         UINT common_name_length, UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="41ccc-753">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-753">Description</span></span>

<span data-ttu-id="41ccc-754">Este serviço remove um certificado de identidade local de uma instância de Sessão DTLS utilizando um número de identificação de certificado (atribuído quando o certificado foi adicionado com nx_secure_dtls_session_local_certificate_add) ou o campo X.509 CommonName.</span><span class="sxs-lookup"><span data-stu-id="41ccc-754">This service removes a local identity certificate from a DTLS Session instance using either a certificate ID number (assigned when the certificate was added with nx_secure_dtls_session_local_certificate_add) or the X.509 CommonName field.</span></span>

<span data-ttu-id="41ccc-755">Se o common_name for utilizado para corresponder ao certificado, o parâmetro cert_id deve ser definido para 0.</span><span class="sxs-lookup"><span data-stu-id="41ccc-755">If the common_name is used to match the certificate, the cert_id parameter should be set to 0.</span></span> <span data-ttu-id="41ccc-756">Se cert_id for utilizado, common_name deve ser aprovado um valor de NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="41ccc-756">If cert_id is used, common_name should be passed a value of NX_NULL.</span></span>

<span data-ttu-id="41ccc-757">O parâmetro cert_id é um identificador numérico, sem zero para o certificado.</span><span class="sxs-lookup"><span data-stu-id="41ccc-757">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="41ccc-758">Isto permite que o certificado seja facilmente removido ou encontrado no caso de existirem vários certificados de identidade com o mesmo Nome Comum X.509 presente na loja de certificados DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-758">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="41ccc-759">Consulte o Guia de Utilizador NetX Secure TLS para obter mais informações sobre os certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="41ccc-759">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-760">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-760">Parameters</span></span>

- <span data-ttu-id="41ccc-761">**session_ptr** Ponteiro para uma instância de Sessão DTLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-761">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="41ccc-762">**common_name** Ponteiro para a corda CommonName para combinar.</span><span class="sxs-lookup"><span data-stu-id="41ccc-762">**common_name** Pointer to the CommonName string to match.</span></span>
- <span data-ttu-id="41ccc-763">**common_name_length** Comprimento da corda common_name.</span><span class="sxs-lookup"><span data-stu-id="41ccc-763">**common_name_length** Length of the common_name string.</span></span>
- <span data-ttu-id="41ccc-764">**cert_id** Identificador único numérico não zero para este certificado neste servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-764">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-765">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-765">Return Values</span></span>

- <span data-ttu-id="41ccc-766">**NX_SUCCESS** (0x00) Remoção bem sucedida do certificado da sessão DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-766">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS session.</span></span>
- <span data-ttu-id="41ccc-767">**NX_PTR_ERROR** (0x07) Ponteiro inválido passou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-767">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="41ccc-768">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Não foi encontrado nenhum certificado correspondente ao cert_id ou common_name na sessão DTLS dada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-768">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-769">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-769">Allowed From</span></span>

<span data-ttu-id="41ccc-770">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-770">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-771">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-771">Example</span></span>

<span data-ttu-id="41ccc-772">\*Consulte a referência para *nx_secure_dtls_session_create* para obter um exemplo mais completo.</span><span class="sxs-lookup"><span data-stu-id="41ccc-772">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-773">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-773">See Also</span></span>

- <span data-ttu-id="41ccc-774">nx_secure_dtls_session_create, nx_secure_dtls_session_receive.</span><span class="sxs-lookup"><span data-stu-id="41ccc-774">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="41ccc-775">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span><span class="sxs-lookup"><span data-stu-id="41ccc-775">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="41ccc-776">nx_secure_dtls_session_local_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="41ccc-776">nx_secure_dtls_session_local_certificate_add,</span></span>
- <span data-ttu-id="41ccc-777">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="41ccc-777">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_receive"></a><span data-ttu-id="41ccc-778">nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="41ccc-778">nx_secure_dtls_session_receive</span></span>

<span data-ttu-id="41ccc-779">Receba os dados da aplicação sobre uma Sessão de DTLS Segura NetX estabelecida</span><span class="sxs-lookup"><span data-stu-id="41ccc-779">Receive application data over an established NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-780">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-780">Prototype</span></span>

```C
UINT nx_secure_dtls_session_receive(
                                NX_SECURE_DTLS_SESSION *dtls_session,
                                NX_PACKET **packet_ptr_ptr,
                                UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="41ccc-781">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-781">Description</span></span>

<span data-ttu-id="41ccc-782">Este serviço devolve os dados da aplicação recebidos por uma Sessão DTLS ativa.</span><span class="sxs-lookup"><span data-stu-id="41ccc-782">This service returns application data received by an active DTLS Session.</span></span> <span data-ttu-id="41ccc-783">A Sessão DTLS pode ser uma sessão de Servidor DTLS (gerida por uma instância do DTLS Server) ou uma sessão de Cliente DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-783">The DTLS Session may be either a DTLS Server session (managed by a DTLS Server instance) or a DTLS Client session.</span></span> <span data-ttu-id="41ccc-784">O pacote devolvido pode ser processado utilizando qualquer um dos serviços NX_PACKET API (consulte a documentação NetX para obter mais informações).</span><span class="sxs-lookup"><span data-stu-id="41ccc-784">The returned packet may be processed using any of the NX_PACKET API services (see the NetX documentation for more information).</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-785">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-785">Parameters</span></span>

- <span data-ttu-id="41ccc-786">**dtls_session** Ponteiro para uma estrutura de Sessão DTLS que foi inicializada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="41ccc-786">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>
- <span data-ttu-id="41ccc-787">**packet_ptr_ptr** Ponteiro para um ponteiro NX_PACKET para o pacote de devolução.</span><span class="sxs-lookup"><span data-stu-id="41ccc-787">**packet_ptr_ptr** Pointer to an NX_PACKET pointer for the return packet.</span></span>
- <span data-ttu-id="41ccc-788">**wait_option** ThreadX espera valor para usar para operações de rede.</span><span class="sxs-lookup"><span data-stu-id="41ccc-788">**wait_option** ThreadX wait value to use for network operations.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-789">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-789">Return Values</span></span>

- <span data-ttu-id="41ccc-790">**NX_SUCCESS** (0x00) Recebimento bem sucedido do pacote de dados da aplicação.</span><span class="sxs-lookup"><span data-stu-id="41ccc-790">**NX_SUCCESS** (0x00) Successful receipt of application data packet.</span></span>
- <span data-ttu-id="41ccc-791">**NX_PTR_ERROR** (0x07) Sessão inválida ou ponteiro do pacote.</span><span class="sxs-lookup"><span data-stu-id="41ccc-791">**NX_PTR_ERROR** (0x07) Invalid session or packet pointer.</span></span>
- <span data-ttu-id="41ccc-792">**NX_NOT_ENABLED** UDP (0x14) não está ativado.</span><span class="sxs-lookup"><span data-stu-id="41ccc-792">**NX_NOT_ENABLED** (0x14) UDP is not enabled.</span></span>
- <span data-ttu-id="41ccc-793">**NX_NOT_BOUND** (0x24) tomada UDP não está ligada à porta.</span><span class="sxs-lookup"><span data-stu-id="41ccc-793">**NX_NOT_BOUND** (0x24) UDP socket not bound to port.</span></span>
- <span data-ttu-id="41ccc-794">**NX_SECURE_TLS_INVALID_PACKET** (0x104) Dados recevied que não eram um registo DTLS válido.</span><span class="sxs-lookup"><span data-stu-id="41ccc-794">**NX_SECURE_TLS_INVALID_PACKET** (0x104) Recevied data that was not a valid DTLS record.</span></span>
- <span data-ttu-id="41ccc-795">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Um registo DTLS não foi devidamente hashed (erro de encriptação).</span><span class="sxs-lookup"><span data-stu-id="41ccc-795">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A DTLS record failed to be properly hashed (encryption error).</span></span>
- <span data-ttu-id="41ccc-796">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Falha de verificação de encriptação.</span><span class="sxs-lookup"><span data-stu-id="41ccc-796">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Encryption padding check failure.</span></span>
- <span data-ttu-id="41ccc-797">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Recevied um alerta do hospedeiro remoto.</span><span class="sxs-lookup"><span data-stu-id="41ccc-797">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Recevied an alert from the remote host.</span></span>
- <span data-ttu-id="41ccc-798">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE**    (0x102) recebeu uma mensagem não reconhecida.</span><span class="sxs-lookup"><span data-stu-id="41ccc-798">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE**    (0x102) Received an unrecognized message.</span></span>
- <span data-ttu-id="41ccc-799">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Recevied um registo DTLS com um comprimento inválido.</span><span class="sxs-lookup"><span data-stu-id="41ccc-799">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Recevied a DTLS record with an invalid length.</span></span>
- <span data-ttu-id="41ccc-800">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Foi encontrada uma cifrasuita desconhecida (indica erro de criptografia interna).</span><span class="sxs-lookup"><span data-stu-id="41ccc-800">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) An unknown ciphersuite was encountered (indicates internal cryptography error).</span></span>
- <span data-ttu-id="41ccc-801">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) Recevied um registo DTLS com uma versão DTLS desajustada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-801">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) Recevied a DTLS record with a mismatched DTLS version.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-802">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-802">Allowed From</span></span>

<span data-ttu-id="41ccc-803">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-803">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-804">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-804">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-805">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-805">See Also</span></span>

- <span data-ttu-id="41ccc-806">nx_secure_dtls_client_session_start, nx_secure_dtls_session_end,</span><span class="sxs-lookup"><span data-stu-id="41ccc-806">nx_secure_dtls_client_session_start, nx_secure_dtls_session_end,</span></span>
- <span data-ttu-id="41ccc-807">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="41ccc-807">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_session_reset"></a><span data-ttu-id="41ccc-808">nx_secure_dtls_session_reset</span><span class="sxs-lookup"><span data-stu-id="41ccc-808">nx_secure_dtls_session_reset</span></span>

<span data-ttu-id="41ccc-809">Dados claros numa instância de Sessão DTLS Segura netX</span><span class="sxs-lookup"><span data-stu-id="41ccc-809">Clear data in an NetX Secure DTLS Session instance</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-810">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-810">Prototype</span></span>

```C
UINT nx_secure_dtls_session_reset(NX_SECURE_DTLS_SESSION *dtls_session);
```

### <a name="description"></a><span data-ttu-id="41ccc-811">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-811">Description</span></span>

<span data-ttu-id="41ccc-812">Este serviço reinicia uma sessão de DTLS, limpando todos os dados criptográficos efémeros e permitindo que a estrutura seja reutilizada para uma nova sessão.</span><span class="sxs-lookup"><span data-stu-id="41ccc-812">This service resets a DTLS session, clearing all ephemeral cryptographic data and allowing the structure to be re-used for a new session.</span></span> <span data-ttu-id="41ccc-813">Os dados persistentes (por exemplo, lojas de certificados) são mantidos de modo a que nx_secure_dtls_session_create não seja chamado repetidamente.</span><span class="sxs-lookup"><span data-stu-id="41ccc-813">Persistent data (e.g. certificate stores) are maintained so that nx_secure_dtls_session_create need not be called repeatedly.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-814">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-814">Parameters</span></span>

- <span data-ttu-id="41ccc-815">**dtls_session** Ponteiro para uma estrutura de Sessão DTLS que foi inicializada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="41ccc-815">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-816">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-816">Return Values</span></span>

- <span data-ttu-id="41ccc-817">**NX_SUCCESS** (0x00) Reinicie bem a sessão.</span><span class="sxs-lookup"><span data-stu-id="41ccc-817">**NX_SUCCESS** (0x00) Successful reset of session.</span></span>
- <span data-ttu-id="41ccc-818">**NX_PTR_ERROR** (0x07) Sessão inválida ou ponteiro tampão.</span><span class="sxs-lookup"><span data-stu-id="41ccc-818">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-819">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-819">Allowed From</span></span>

<span data-ttu-id="41ccc-820">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-820">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-821">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-821">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-822">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-822">See Also</span></span>

- <span data-ttu-id="41ccc-823">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="41ccc-823">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="41ccc-824">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="41ccc-824">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_-session_send"></a><span data-ttu-id="41ccc-825">nx_secure_dtls_ session_send</span><span class="sxs-lookup"><span data-stu-id="41ccc-825">nx_secure_dtls_ session_send</span></span>

<span data-ttu-id="41ccc-826">Enviar dados sobre uma sessão de DTLS</span><span class="sxs-lookup"><span data-stu-id="41ccc-826">Send data over a DTLS session</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-827">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-827">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_send(NX_SECURE_DTLS_SESSION *session_ptr,
                                          NX_PACKET *packet_ptr,
                                          NXD_ADDRESS *ip_address, UINT port);

```

### <a name="description"></a><span data-ttu-id="41ccc-828">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-828">Description</span></span>

<span data-ttu-id="41ccc-829">Este serviço envia um pacote de dados sobre uma Sessão DTLS estabelecida para um anfitrião DTLS remoto no endereço IP e porta dado.</span><span class="sxs-lookup"><span data-stu-id="41ccc-829">This service sends a packet of data over an established DTLS Session to a remote DTLS host at the given IP address and port.</span></span> <span data-ttu-id="41ccc-830">A sessão utilizada é uma sessão ativa do Cliente DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-830">The session used is an active DTLS Client session.</span></span> <span data-ttu-id="41ccc-831">Note que o endereço IP e a porta são fornecidos devido à natureza apátrida da UDP, mas geralmente devem corresponder ao endereço e porto utilizados para iniciar a sessão em nx_secure_dtls_session_start.</span><span class="sxs-lookup"><span data-stu-id="41ccc-831">Note that the IP address and port are provided due to the stateless nature of UDP but should generally match the address and port used to start the session in nx_secure_dtls_session_start.</span></span>

<span data-ttu-id="41ccc-832">Os dados fornecidos no pacote, que deve ser atribuído com *nx_secure_dtls_packet_allocate,* são encriptados utilizando os parâmetros e rotinas criptográficos da sessão DTLS e depois enviados ao anfitrião remoto através da tomada UDP da Sessão DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-832">The data provided in the packet, which must be allocated using *nx_secure_dtls_packet_allocate*, is encrypted using the DTLS session cryptographic parameters and routines and then sent to the remote host over the DTLS Session’s UDP socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-833">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-833">Parameters</span></span>

- <span data-ttu-id="41ccc-834">**session_ptr** Ponteiro para uma instância de sessão de clientes DTLS ativa.</span><span class="sxs-lookup"><span data-stu-id="41ccc-834">**session_ptr** Pointer to an active DTLS client session instance.</span></span>
- <span data-ttu-id="41ccc-835">**packet_ptr** Ponteiro para uma NX_PACKET instância atribuída anteriormente e povoada com dados de aplicação.</span><span class="sxs-lookup"><span data-stu-id="41ccc-835">**packet_ptr** Pointer to an NX_PACKET instance allocated previously and populated with application data.</span></span>
- <span data-ttu-id="41ccc-836">**ip_address** Ponteiro para uma estrutura NXD_ADDRESS que contém o endereço IP do anfitrião remoto.</span><span class="sxs-lookup"><span data-stu-id="41ccc-836">**ip_address** Pointer to an NXD_ADDRESS structure containing the IP address of the remote host.</span></span>
- <span data-ttu-id="41ccc-837">**porto** Porta UDP no hospedeiro remoto.</span><span class="sxs-lookup"><span data-stu-id="41ccc-837">**port** UDP port on the remote host.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-838">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-838">Return Values</span></span>

- <span data-ttu-id="41ccc-839">**NX_SUCCESS** (0x00) Envio bem sucedido do pacote.</span><span class="sxs-lookup"><span data-stu-id="41ccc-839">**NX_SUCCESS** (0x00) Successful send of packet.</span></span>
- <span data-ttu-id="41ccc-840">**NX_PTR_ERROR** (0x07) Ponteiro inválido passou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-840">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="41ccc-841">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Ocorreu um erro na operação de envio da UDP subjacente.</span><span class="sxs-lookup"><span data-stu-id="41ccc-841">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An error occurred in the underlying UDP send operation.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-842">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-842">Allowed From</span></span>

<span data-ttu-id="41ccc-843">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-843">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-844">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-844">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-845">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-845">See Also</span></span>

- <span data-ttu-id="41ccc-846">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span><span class="sxs-lookup"><span data-stu-id="41ccc-846">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="41ccc-847">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="41ccc-847">nx_secure_dtls_session_create</span></span>

## <a name="nx_secure_dtls_session_trusted_certificate_add"></a><span data-ttu-id="41ccc-848">nx_secure_dtls_session_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="41ccc-848">nx_secure_dtls_session_trusted_certificate_add</span></span>

<span data-ttu-id="41ccc-849">Adicione um certificado ca fidedigno a uma Sessão de DTLS NetX Secure</span><span class="sxs-lookup"><span data-stu-id="41ccc-849">Add a trusted CA certificate to a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-850">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-850">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_trusted_certificate_add(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="41ccc-851">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-851">Description</span></span>

<span data-ttu-id="41ccc-852">Este serviço adiciona um certificado CA ou CA X.509 intermédio fidedigno a uma instância de Sessão DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-852">This service adds a trusted CA or intermediate CA X.509 certificate to a DTLS Session instance.</span></span> <span data-ttu-id="41ccc-853">Um Cliente DTLS requer pelo menos um certificado fidedigno para validar certificados de servidor remoto, a menos que seja utilizado um mecanismo alternativo de autenticação (por exemplo, Chaves Pré-Partilhadas).</span><span class="sxs-lookup"><span data-stu-id="41ccc-853">A DTLS Client requires at least one trusted certificate in order to validate remote server certificates unless an alternative authentication mechanism is used (e.g. Pre-Shared Keys).</span></span> <span data-ttu-id="41ccc-854">Um certificado de confiança não costuma ter uma chave privada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-854">A trusted certificate does not usually have a private key.</span></span>

<span data-ttu-id="41ccc-855">O parâmetro cert_id é um identificador numérico, sem zero para o certificado.</span><span class="sxs-lookup"><span data-stu-id="41ccc-855">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="41ccc-856">Isto permite que o certificado seja facilmente removido ou encontrado no caso de existirem vários certificados de identidade com o mesmo Nome Comum X.509 presente na loja de certificados DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-856">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="41ccc-857">Consulte o Guia de Utilizador NetX Secure TLS para obter mais informações sobre os certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="41ccc-857">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-858">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-858">Parameters</span></span>

- <span data-ttu-id="41ccc-859">**session_ptr** Ponteiro para uma instância de Sessão DTLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-859">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="41ccc-860">**certificado** Ponteiro para uma estrutura de certificado X.509 previamente inicializada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-860">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="41ccc-861">**cert_id** Identificador único numérico não zero para este certificado neste servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-861">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="41ccc-862">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-862">Return Values</span></span>

- <span data-ttu-id="41ccc-863">**NX_SUCCESS** (0x00) Adição bem sucedida de certificado à sessão DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-863">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS session.</span></span>
- <span data-ttu-id="41ccc-864">**NX_PTR_ERROR** (0x07) Ponteiro inválido passou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-864">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="41ccc-865">**NX_INVALID_PARAMETERS** (0x4D) Foi aprovado um certificado de identificação de 0.</span><span class="sxs-lookup"><span data-stu-id="41ccc-865">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-866">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-866">Allowed From</span></span>

<span data-ttu-id="41ccc-867">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-867">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-868">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-868">Example</span></span>

<span data-ttu-id="41ccc-869">\*Consulte a referência para *nx_secure_dtls_session_create* para obter um exemplo mais completo.</span><span class="sxs-lookup"><span data-stu-id="41ccc-869">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-870">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-870">See Also</span></span>

- <span data-ttu-id="41ccc-871">nx_secure_dtls_session_create, nx_secure_dtls_session_receive.</span><span class="sxs-lookup"><span data-stu-id="41ccc-871">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="41ccc-872">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span><span class="sxs-lookup"><span data-stu-id="41ccc-872">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="41ccc-873">nx_secure_dtls_session_trusted_certificate_remove,</span><span class="sxs-lookup"><span data-stu-id="41ccc-873">nx_secure_dtls_session_trusted_certificate_remove,</span></span>
- <span data-ttu-id="41ccc-874">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="41ccc-874">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_trusted_certificate_remove"></a><span data-ttu-id="41ccc-875">nx_secure_dtls_session_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="41ccc-875">nx_secure_dtls_session_trusted_certificate_remove</span></span>

<span data-ttu-id="41ccc-876">Remova um certificado de CA fidedigno de uma Sessão de DTLS NetX Secure</span><span class="sxs-lookup"><span data-stu-id="41ccc-876">Remove a trusted CA certificate from a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="41ccc-877">Prototype</span><span class="sxs-lookup"><span data-stu-id="41ccc-877">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_trusted_certificate_remove(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *common_name,
                            UINT common_name_length, UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="41ccc-878">Descrição</span><span class="sxs-lookup"><span data-stu-id="41ccc-878">Description</span></span>

<span data-ttu-id="41ccc-879">Este serviço remove um certificado de CA fidedigno de uma instância DTLS Session utilizando um número de identificação de certificado (atribuído quando o certificado foi adicionado com nx_secure_dtls_session_trusted_certificate_add) ou o campo X.509 CommonName.</span><span class="sxs-lookup"><span data-stu-id="41ccc-879">This service removes a trusted CA certificate from a DTLS Session instance using either a certificate ID number (assigned when the certificate was added with nx_secure_dtls_session_trusted_certificate_add) or the X.509 CommonName field.</span></span>

<span data-ttu-id="41ccc-880">Se o common_name for utilizado para corresponder ao certificado, o parâmetro cert_id deve ser definido para 0.</span><span class="sxs-lookup"><span data-stu-id="41ccc-880">If the common_name is used to match the certificate, the cert_id parameter should be set to 0.</span></span> <span data-ttu-id="41ccc-881">Se cert_id for utilizado, common_name deve ser aprovado um valor de NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="41ccc-881">If cert_id is used, common_name should be passed a value of NX_NULL.</span></span>

<span data-ttu-id="41ccc-882">O parâmetro cert_id é um identificador numérico, sem zero para o certificado.</span><span class="sxs-lookup"><span data-stu-id="41ccc-882">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="41ccc-883">Isto permite que o certificado seja facilmente removido ou encontrado no caso de existirem vários certificados de identidade com o mesmo Nome Comum X.509 presente na loja de certificados DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-883">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="41ccc-884">Consulte o Guia de Utilizador NetX Secure TLS para obter mais informações sobre os certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="41ccc-884">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="41ccc-885">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41ccc-885">Parameters</span></span>

- <span data-ttu-id="41ccc-886">**session_ptr** Ponteiro para uma instância de Sessão DTLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-886">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="41ccc-887">**common_name** Ponteiro para a corda CommonName para combinar.</span><span class="sxs-lookup"><span data-stu-id="41ccc-887">**common_name** Pointer to the CommonName string to match.</span></span>
- <span data-ttu-id="41ccc-888">**common_name_length** Comprimento da corda common_name.</span><span class="sxs-lookup"><span data-stu-id="41ccc-888">**common_name_length** Length of the common_name string.</span></span>
- <span data-ttu-id="41ccc-889">**cert_id** Identificador único numérico não zero para este certificado neste servidor DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-889">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>


### <a name="return-values"></a><span data-ttu-id="41ccc-890">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="41ccc-890">Return Values</span></span>

- <span data-ttu-id="41ccc-891">**NX_SUCCESS** (0x00) Remoção bem sucedida do certificado da sessão DTLS.</span><span class="sxs-lookup"><span data-stu-id="41ccc-891">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS session.</span></span>
- <span data-ttu-id="41ccc-892">**NX_PTR_ERROR** (0x07) Ponteiro inválido passou.</span><span class="sxs-lookup"><span data-stu-id="41ccc-892">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="41ccc-893">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Não foi encontrado nenhum certificado correspondente ao cert_id ou common_name na sessão DTLS dada.</span><span class="sxs-lookup"><span data-stu-id="41ccc-893">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="41ccc-894">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="41ccc-894">Allowed From</span></span>

<span data-ttu-id="41ccc-895">Fios</span><span class="sxs-lookup"><span data-stu-id="41ccc-895">Threads</span></span>

### <a name="example"></a><span data-ttu-id="41ccc-896">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41ccc-896">Example</span></span>

<span data-ttu-id="41ccc-897">\*Consulte a referência para *nx_secure_dtls_session_create* para obter um exemplo mais completo.</span><span class="sxs-lookup"><span data-stu-id="41ccc-897">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

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

### <a name="see-also"></a><span data-ttu-id="41ccc-898">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41ccc-898">See Also</span></span>

- <span data-ttu-id="41ccc-899">nx_secure_dtls_session_create, nx_secure_dtls_session_receive.</span><span class="sxs-lookup"><span data-stu-id="41ccc-899">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="41ccc-900">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span><span class="sxs-lookup"><span data-stu-id="41ccc-900">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="41ccc-901">nx_secure_dtls_session_trusted_certificate_add,</span><span class="sxs-lookup"><span data-stu-id="41ccc-901">nx_secure_dtls_session_trusted_certificate_add,</span></span>
- <span data-ttu-id="41ccc-902">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="41ccc-902">nx_secure_x509_certificate_initialize</span></span>
