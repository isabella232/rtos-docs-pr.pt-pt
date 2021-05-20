---
title: Capítulo 4 - Descrição dos serviços Azure RTOS NetX Secure
description: Este capítulo contém uma descrição de todos os serviços NetX Secure (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 80ec22058ab64ed0c6258bb3d9364ec44f9a741b
ms.sourcegitcommit: 4ebe7c51ba850951c6a9d0f15e22d07bb752bc28
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/20/2021
ms.locfileid: "110223397"
---
# <a name="chapter-4---description-of-azure-rtos-netx-secure-services"></a><span data-ttu-id="34a2c-103">Capítulo 4 - Descrição dos serviços Azure RTOS NetX Secure</span><span class="sxs-lookup"><span data-stu-id="34a2c-103">Chapter 4 - Description of Azure RTOS NetX Secure services</span></span>

<span data-ttu-id="34a2c-104">Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX Secure (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="34a2c-104">This chapter contains a description of all Azure RTOS NetX Secure services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="34a2c-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pela macro **NX_SECURE_DISABLE_ERROR_CHECKING** que é utilizada para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="34a2c-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_SECURE_DISABLE_ERROR_CHECKING** macro that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="34a2c-106">nx_secure_crypto_table_self_test</span><span class="sxs-lookup"><span data-stu-id="34a2c-106">nx_secure_crypto_table_self_test</span></span>](#nx_secure_crypto_table_self_test)
  - <span data-ttu-id="34a2c-107">Realize self_test sobre os métodos cripto</span><span class="sxs-lookup"><span data-stu-id="34a2c-107">Perform self_test on the crypto methods</span></span>
- [<span data-ttu-id="34a2c-108">nx_secure_module_hash_compute</span><span class="sxs-lookup"><span data-stu-id="34a2c-108">nx_secure_module_hash_compute</span></span>](#nx_secure_module_hash_compute)
  - <span data-ttu-id="34a2c-109">Valor do haxixe computativo usando user_supplied função de haxixe</span><span class="sxs-lookup"><span data-stu-id="34a2c-109">Computes hash value using user_supplied hash function</span></span>
- [<span data-ttu-id="34a2c-110">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-110">nx_secure_tls_active_certificate_set</span></span>](#nx_secure_tls_active_certificate_set)
  - <span data-ttu-id="34a2c-111">Definir o certificado de identidade ativa para uma Sessão TLS NetX Secure</span><span class="sxs-lookup"><span data-stu-id="34a2c-111">Set the active identity certificate for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="34a2c-112">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-112">nx_secure_tls_client_psk_set</span></span>](#nx_secure_tls_client_psk_set)
  - <span data-ttu-id="34a2c-113">Desagure uma chave de Pre_Shared para uma sessão de clientes NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="34a2c-113">Set a Pre_Shared Key for a NetX Secure TLS Client Session</span></span>
- [<span data-ttu-id="34a2c-114">nx_secure_tls_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-114">nx_secure_tls_initialize</span></span>](#nx_secure_tls_initialize)
  - <span data-ttu-id="34a2c-115">Inicializa o módulo NetX Secure TLS]</span><span class="sxs-lookup"><span data-stu-id="34a2c-115">Initializes the NetX Secure TLS module]</span></span>
- [<span data-ttu-id="34a2c-116">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-116">nx_secure_tls_local_certificate_add</span></span>](#nx_secure_tls_local_certificate_add)
  - <span data-ttu-id="34a2c-117">Adicione um certificado local à Sessão NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="34a2c-117">Add a local certificate to NetX Secure TLS Session</span></span>
- [<span data-ttu-id="34a2c-118">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="34a2c-118">nx_secure_tls_local_certificate_find</span></span>](#nx_secure_tls_local_certificate_find)
  - <span data-ttu-id="34a2c-119">Encontre um certificado local numa Sessão De TLS Segura NetX por Nome Comum</span><span class="sxs-lookup"><span data-stu-id="34a2c-119">Find a local certificate in a NetX Secure TLS Session by Common Name</span></span>
- [<span data-ttu-id="34a2c-120">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="34a2c-120">nx_secure_tls_local_certificate_remove</span></span>](#nx_secure_tls_local_certificate_remove)
  - <span data-ttu-id="34a2c-121">Remover certificado local da Sessão NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="34a2c-121">Remove local certificate from NetX Secure TLS Session</span></span>
- [<span data-ttu-id="34a2c-122">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="34a2c-122">nx_secure_tls_metadata_size_calculate</span></span>](#nx_secure_tls_metadata_size_calculate)
  - <span data-ttu-id="34a2c-123">Calcular o tamanho dos metadados criptográficos para uma Sessão de TLS NetX Secure</span><span class="sxs-lookup"><span data-stu-id="34a2c-123">Calculate size of cryptographic metadata for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="34a2c-124">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-124">nx_secure_tls_packet_allocate</span></span>](#nx_secure_tls_packet_allocate)
  - <span data-ttu-id="34a2c-125">Aloque um pacote para uma Sessão NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="34a2c-125">Allocate a packet for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="34a2c-126">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-126">nx_secure_tls_psk_add</span></span>](#nx_secure_tls_psk_add)
  - <span data-ttu-id="34a2c-127">Adicione uma chave Pre_Shared a uma Sessão De TLS Segura NetX</span><span class="sxs-lookup"><span data-stu-id="34a2c-127">Add a Pre_Shared Key to a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="34a2c-128">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-128">nx_secure_tls_remote_certificate_allocate</span></span>](#nx_secure_tls_remote_certificate_allocate)
  - <span data-ttu-id="34a2c-129">Alocar espaço para o certificado fornecido por um anfitrião remoto TLS</span><span class="sxs-lookup"><span data-stu-id="34a2c-129">Allocate space for the certificate provided by a remote TLS host</span></span>
- [<span data-ttu-id="34a2c-130">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-130">nx_secure_tls_remote_certificate_buffer_allocate</span></span>](#nx_secure_tls_remote_certificate_buffer_allocate)
  - <span data-ttu-id="34a2c-131">Alocar espaço para todos os certificados fornecidos por um anfitrião remoto TLS</span><span class="sxs-lookup"><span data-stu-id="34a2c-131">Allocate space for all certificates provided by a remote TLS host</span></span>
- [<span data-ttu-id="34a2c-132">nx_secure_tls_remote_certificate_free_all</span><span class="sxs-lookup"><span data-stu-id="34a2c-132">nx_secure_tls_remote_certificate_free_all</span></span>](#nx_secure_tls_remote_certificate_free_all)
  - <span data-ttu-id="34a2c-133">Espaço gratuito atribuído para certificados de entrada</span><span class="sxs-lookup"><span data-stu-id="34a2c-133">Free space allocated for incoming certificates</span></span>
- [<span data-ttu-id="34a2c-134">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-134">nx_secure_tls_server_certificate_add</span></span>](#nx_secure_tls_server_certificate_add)
  - <span data-ttu-id="34a2c-135">Adicione um certificado especificamente para servidores TLS usando um identificador numérico</span><span class="sxs-lookup"><span data-stu-id="34a2c-135">Add a certificate specifically for TLS servers using a numeric identifier</span></span>
- [<span data-ttu-id="34a2c-136">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="34a2c-136">nx_secure_tls_server_certificate_find</span></span>](#nx_secure_tls_server_certificate_find)
  - <span data-ttu-id="34a2c-137">Encontre um certificado usando um identificador numérico</span><span class="sxs-lookup"><span data-stu-id="34a2c-137">Find a certificate using a numeric identifier</span></span>
- [<span data-ttu-id="34a2c-138">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="34a2c-138">nx_secure_tls_server_certificate_remove</span></span>](#nx_secure_tls_server_certificate_remove)
  - <span data-ttu-id="34a2c-139">Remova um certificado de servidor local usando um identificador numérico</span><span class="sxs-lookup"><span data-stu-id="34a2c-139">Remove a local server certificate using a numeric identifier</span></span>
- [<span data-ttu-id="34a2c-140">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-140">nx_secure_tls_session_certificate_callback_set</span></span>](#nx_secure_tls_session_certificate_callback_set)
  - <span data-ttu-id="34a2c-141">Configurar uma chamada para o TLS usar para validação adicional de certificados</span><span class="sxs-lookup"><span data-stu-id="34a2c-141">Set up a callback for TLS to use for additional certificate validation</span></span>
- [<span data-ttu-id="34a2c-142">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-142">nx_secure_tls_session_client_callback_set</span></span>](#nx_secure_tls_session_client_callback_set)
  - <span data-ttu-id="34a2c-143">Configurar uma chamada para o TLS invocar no início de um aperto de mão do Cliente TLS</span><span class="sxs-lookup"><span data-stu-id="34a2c-143">Set up a callback for TLS to invoke at the beginning of a TLS Client handshake</span></span>
- [<span data-ttu-id="34a2c-144">nx_secure_tls_session_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="34a2c-144">nx_secure_tls_session_x509_client_verify_configure</span></span>](#nx_secure_tls_session_x509_client_verify_configure)
  - <span data-ttu-id="34a2c-145">Ativar a verificação do cliente X.509 e alocar espaço para certificados de cliente</span><span class="sxs-lookup"><span data-stu-id="34a2c-145">Enable client X.509 verification and allocate space for client certificates</span></span>
- [<span data-ttu-id="34a2c-146">nx_secure_tls_session_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="34a2c-146">nx_secure_tls_session_client_verify_disable</span></span>](#nx_secure_tls_session_client_verify_disable)
  - <span data-ttu-id="34a2c-147">Desativar a autenticação do certificado do cliente para uma Sessão TLS Segura NetX</span><span class="sxs-lookup"><span data-stu-id="34a2c-147">Disable Client Certificate Authentication for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="34a2c-148">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="34a2c-148">nx_secure_tls_session_client_verify_enable</span></span>](#nx_secure_tls_session_client_verify_enable)
  - <span data-ttu-id="34a2c-149">Ativar a autenticação do certificado de cliente para uma Sessão TLS Segura NetX</span><span class="sxs-lookup"><span data-stu-id="34a2c-149">Enable Client Certificate Authentication for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="34a2c-150">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-150">nx_secure_tls_session_create</span></span>](#nx_secure_tls_session_create)
  - <span data-ttu-id="34a2c-151">Criar uma Sessão TLS Segura NetX para comunicações seguras</span><span class="sxs-lookup"><span data-stu-id="34a2c-151">Create a NetX Secure TLS Session for secure communications</span></span>
- [<span data-ttu-id="34a2c-152">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="34a2c-152">nx_secure_tls_session_delete</span></span>](#nx_secure_tls_session_delete)
  - <span data-ttu-id="34a2c-153">Excluir uma Sessão de TLS Segura NetX</span><span class="sxs-lookup"><span data-stu-id="34a2c-153">Delete a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="34a2c-154">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="34a2c-154">nx_secure_tls_session_end</span></span>](#nx_secure_tls_session_end)
  - <span data-ttu-id="34a2c-155">Termine uma sessão ativa de TLS Do NetX Secure</span><span class="sxs-lookup"><span data-stu-id="34a2c-155">End an active NetX Secure TLS Session</span></span>
- [<span data-ttu-id="34a2c-156">nx_secure_tls_session_packet_buffer_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-156">nx_secure_tls_session_packet_buffer_set</span></span>](#nx_secure_tls_session_packet_buffer_set)
  - <span data-ttu-id="34a2c-157">Descreva o tampão de montagem do pacote para uma Sessão TLS NetX Secure</span><span class="sxs-lookup"><span data-stu-id="34a2c-157">Set the packet reassembly buffer for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="34a2c-158">nx_secure_tls_session_protocol_version_override</span><span class="sxs-lookup"><span data-stu-id="34a2c-158">nx_secure_tls_session_protocol_version_override</span></span>](#nx_secure_tls_session_protocol_version_override)
  - <span data-ttu-id="34a2c-159">Anular a versão padrão do protocolo TLS para uma Sessão De TLS Do NetX Secure</span><span class="sxs-lookup"><span data-stu-id="34a2c-159">Override the default TLS protocol version for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="34a2c-160">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="34a2c-160">nx_secure_tls_session_receive</span></span>](#nx_secure_tls_session_receive)
  - <span data-ttu-id="34a2c-161">Receber dados de uma Sessão De TLS Segura NetX</span><span class="sxs-lookup"><span data-stu-id="34a2c-161">Receive data from a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="34a2c-162">nx_secure_tls_session_renegotiate_callback_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-162">nx_secure_tls_session_renegotiate_callback_set</span></span>](#nx_secure_tls_session_renegotiate_callback_set)
  - <span data-ttu-id="34a2c-163">Atribua uma chamada que será invocada no início de uma renegociação da sessão</span><span class="sxs-lookup"><span data-stu-id="34a2c-163">Assign a callback that will be invoked at the beginning of a session renegotiation</span></span>
- [<span data-ttu-id="34a2c-164">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="34a2c-164">nx_secure_tls_session_renegotiate</span></span>](#nx_secure_tls_session_renegotiate)
  - <span data-ttu-id="34a2c-165">Inicie um aperto de mão de renegociação de sessão com o anfitrião remoto</span><span class="sxs-lookup"><span data-stu-id="34a2c-165">Initiate a session renegotiation handshake with the remote host</span></span>
- [<span data-ttu-id="34a2c-166">nx_secure_tls_session_reset</span><span class="sxs-lookup"><span data-stu-id="34a2c-166">nx_secure_tls_session_reset</span></span>](#nx_secure_tls_session_reset)
  - <span data-ttu-id="34a2c-167">Limpe e reponha uma Sessão de TLS De Segurança NetX</span><span class="sxs-lookup"><span data-stu-id="34a2c-167">Clear out and reset a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="34a2c-168">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="34a2c-168">nx_secure_tls_session_send</span></span>](#nx_secure_tls_session_send)
  - <span data-ttu-id="34a2c-169">Enviar dados através de uma Sessão De TLS Segura NetX</span><span class="sxs-lookup"><span data-stu-id="34a2c-169">Send data through a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="34a2c-170">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-170">nx_secure_tls_session_server_callback_set</span></span>](#nx_secure_tls_session_server_callback_set)
  - <span data-ttu-id="34a2c-171">Configurar uma chamada para o TLS invocar no início de um aperto de mão do TLS Server</span><span class="sxs-lookup"><span data-stu-id="34a2c-171">Set up a callback for TLS to invoke at the beginning of a TLS Server handshake</span></span>
- [<span data-ttu-id="34a2c-172">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="34a2c-172">nx_secure_tls_session_sni_extension_parse</span></span>](#nx_secure_tls_session_sni_extension_parse)
  - <span data-ttu-id="34a2c-173">Parse uma extensão de indicação de nome do servidor (SNI) recebida de um cliente TLS</span><span class="sxs-lookup"><span data-stu-id="34a2c-173">Parse a Server Name Indication (SNI) extension received from a TLS Client</span></span>
- [<span data-ttu-id="34a2c-174">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-174">nx_secure_tls_session_sni_extension_set</span></span>](#nx_secure_tls_session_sni_extension_set)
  - <span data-ttu-id="34a2c-175">Desa estade um nome DNS de extensão de extensão de nome do servidor (SNI) para enviar para um servidor remoto</span><span class="sxs-lookup"><span data-stu-id="34a2c-175">Set a Server Name Indication (SNI) extension DNS name to send to a remote Server</span></span>
- [<span data-ttu-id="34a2c-176">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="34a2c-176">nx_secure_tls_session_start</span></span>](#nx_secure_tls_session_start)
  - <span data-ttu-id="34a2c-177">Inicie uma Sessão De TLS Segura NetX</span><span class="sxs-lookup"><span data-stu-id="34a2c-177">Start a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="34a2c-178">nx_secure_tls_session_time_function_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-178">nx_secure_tls_session_time_function_set</span></span>](#nx_secure_tls_session_time_function_set)
  - <span data-ttu-id="34a2c-179">Atribua uma função de marcação de tempo a uma Sessão TLS Segura NetX</span><span class="sxs-lookup"><span data-stu-id="34a2c-179">Assign a timestamp function to a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="34a2c-180">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-180">nx_secure_tls_trusted_certificate_add</span></span>](#nx_secure_tls_trusted_certificate_add)
  - <span data-ttu-id="34a2c-181">Adicionar certificado fidedigno à Sessão TLS Do NetX Secure</span><span class="sxs-lookup"><span data-stu-id="34a2c-181">Add trusted certificate to NetX Secure TLS Session</span></span>
- [<span data-ttu-id="34a2c-182">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="34a2c-182">nx_secure_tls_trusted_certificate_remove</span></span>](#nx_secure_tls_trusted_certificate_remove)
  - <span data-ttu-id="34a2c-183">Remover certificado fidedigno da Sessão TLS Do NetX Secure</span><span class="sxs-lookup"><span data-stu-id="34a2c-183">Remove trusted certificate from NetX Secure TLS Session</span></span>
- [<span data-ttu-id="34a2c-184">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-184">nx_secure_x509_certificate_initialize</span></span>](#nx_secure_x509_certificate_initialize)
  - <span data-ttu-id="34a2c-185">Inicializar o Certificado X.509 para NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="34a2c-185">Initialize X.509 Certificate for NetX Secure TLS</span></span>
- [<span data-ttu-id="34a2c-186">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="34a2c-186">nx_secure_x509_common_name_dns_check</span></span>](#nx_secure_x509_common_name_dns_check)
  - <span data-ttu-id="34a2c-187">Verifique o nome DNS contra o Certificado X.509</span><span class="sxs-lookup"><span data-stu-id="34a2c-187">Check DNS name against X.509 Certificate</span></span>
- [<span data-ttu-id="34a2c-188">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="34a2c-188">nx_secure_x509_crl_revocation_check</span></span>](#nx_secure_x509_crl_revocation_check)
  - <span data-ttu-id="34a2c-189">Verifique o Certificado X.509 com uma Lista de Revogação de Certificados (CRL)]</span><span class="sxs-lookup"><span data-stu-id="34a2c-189">Check X.509 Certificate against a supplied Certificate Revocation List (CRL)]</span></span>
- [<span data-ttu-id="34a2c-190">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-190">nx_secure_x509_dns_name_initialize</span></span>](#nx_secure_x509_dns_name_initialize)
  - <span data-ttu-id="34a2c-191">Inicialize uma estrutura de nomeS DNS X.509</span><span class="sxs-lookup"><span data-stu-id="34a2c-191">Initialize an X.509 DNS name structure</span></span>
- [<span data-ttu-id="34a2c-192">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="34a2c-192">nx_secure_x509_extended_key_usage_extension_parse</span></span>](#nx_secure_x509_extended_key_usage_extension_parse)
  - <span data-ttu-id="34a2c-193">Encontre e analise uma extensão de utilização estendida X.509 num certificado X.509</span><span class="sxs-lookup"><span data-stu-id="34a2c-193">Find and parse an X.509 extended key usage extension in an X.509 certificate</span></span>
- [<span data-ttu-id="34a2c-194">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="34a2c-194">nx_secure_x509_extension_find</span></span>](#nx_secure_x509_extension_find)
  - <span data-ttu-id="34a2c-195">Encontre e devolva uma extensão X.509 num certificado X.509</span><span class="sxs-lookup"><span data-stu-id="34a2c-195">Find and return an X.509 extension in an X.509 certificate</span></span>
- [<span data-ttu-id="34a2c-196">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="34a2c-196">nx_secure_x509_key_usage_extension_parse</span></span>](#nx_secure_x509_key_usage_extension_parse)
  - <span data-ttu-id="34a2c-197">Encontre e analise uma extensão de utilização da chave X.509 num certificado X.509</span><span class="sxs-lookup"><span data-stu-id="34a2c-197">Find and parse an X.509 Key Usage extension in an X.509 certificate</span></span>

## <a name="nx_secure_crypto_table_self_test"></a><span data-ttu-id="34a2c-198">nx_secure_crypto_table_self_test</span><span class="sxs-lookup"><span data-stu-id="34a2c-198">nx_secure_crypto_table_self_test</span></span>

<span data-ttu-id="34a2c-199">Realizar auto-teste nos métodos cripto</span><span class="sxs-lookup"><span data-stu-id="34a2c-199">Perform self-test on the crypto methods</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-200">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-200">Prototype</span></span>

```C
UINT nx_secure_crypto_table_self_test(
                                  const NX_SECURE_TLS_CRYPTO *crypto_table,
                                  VOID *metadata, UINT metadata_size);
```

### <a name="description"></a><span data-ttu-id="34a2c-201">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-201">Description</span></span>

<span data-ttu-id="34a2c-202">Este serviço executa através do método cripto-método auto-testes para validar.</span><span class="sxs-lookup"><span data-stu-id="34a2c-202">This service runs through the crypto method self tests to validate.</span></span> <span data-ttu-id="34a2c-203">O auto-teste só está disponível se a biblioteca NetX Secure for construída com o símbolo NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK definido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-203">The self test is available only if NetX Secure library is built with the symbol NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK defined.</span></span>

<span data-ttu-id="34a2c-204">Para cada método cripto suportado, o auto-teste fornece dados de entrada pré-definidos e verificado que a saída corresponde ao valor esperado pré-definido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-204">For each supported crypto method, the self test provides pre-defined input data, and verified the output matches the pre-defined expected value.</span></span>

<span data-ttu-id="34a2c-205">NetX Secure crypto self test suporta os seguintes algoritmos e tamanhos chave:</span><span class="sxs-lookup"><span data-stu-id="34a2c-205">NetX Secure crypto self test supports the following algorithms and key sizes:</span></span>

- <span data-ttu-id="34a2c-206">DES: encriptação e desencriptação</span><span class="sxs-lookup"><span data-stu-id="34a2c-206">DES: encryption and decryption</span></span>
- <span data-ttu-id="34a2c-207">DES Triplo (3DES): encriptação e desencriptação</span><span class="sxs-lookup"><span data-stu-id="34a2c-207">Triple DES (3DES): encryption and decryption</span></span>
- <span data-ttu-id="34a2c-208">AES: tamanho da chave de 128, 192, 256 bits, encriptação e desencriptação, no modo CBC e no modo de contador.</span><span class="sxs-lookup"><span data-stu-id="34a2c-208">AES: 128-, 192-, 256-bit key size, encryption and decryption, in CBC mode and counter mode.</span></span>
- <span data-ttu-id="34a2c-209">HMAC-MD5: autenticação e computação de haxixe</span><span class="sxs-lookup"><span data-stu-id="34a2c-209">HMAC-MD5: authentication and hash computation</span></span>
- <span data-ttu-id="34a2c-210">HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2-512, autenticação e computação de haxixe</span><span class="sxs-lookup"><span data-stu-id="34a2c-210">HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2- 512, authentication and hash computation</span></span>
- <span data-ttu-id="34a2c-211">MD5: autenticação</span><span class="sxs-lookup"><span data-stu-id="34a2c-211">MD5: authentication</span></span>
- <span data-ttu-id="34a2c-212">Função pseudoaleatória (PRF): PRF_HMAC_SHA1 e PRF_HMAC_SHA2-256</span><span class="sxs-lookup"><span data-stu-id="34a2c-212">Pseudo-random Function (PRF): PRF_HMAC_SHA1 and PRF_HMAC_SHA2-256</span></span>
- <span data-ttu-id="34a2c-213">RSA: operação rsa 1024-, 2048-, 4096-bit RSA power-modulus</span><span class="sxs-lookup"><span data-stu-id="34a2c-213">RSA: 1024-, 2048-, 4096-bit RSA power-modulus operation</span></span>
- <span data-ttu-id="34a2c-214">SHA1 (96- e 160 bits), SHA2 (256bit, 384bit, 512bit) autenticação</span><span class="sxs-lookup"><span data-stu-id="34a2c-214">SHA: SHA1 (96- and 160-bit), SHA2 (256bit, 384bit, 512bit) authentication</span></span>

<span data-ttu-id="34a2c-215">Esta função tem os vetores incorporados para os algoritmos cripto listados acima.</span><span class="sxs-lookup"><span data-stu-id="34a2c-215">This function has the built-in vectors for the crypto algorithms listed above.</span></span> <span data-ttu-id="34a2c-216">No entanto, apenas testa os listados no *cipher_table* passaram para esta função.</span><span class="sxs-lookup"><span data-stu-id="34a2c-216">However it only tests the ones listed in the *cipher_table* passed into this function.</span></span> <span data-ttu-id="34a2c-217">Por exemplo, para uma sessão de TLS utiliza apenas o TLS_RSA_WITH_AES_128_CBC_SHA cifrasuita, esta função realizará auto-teste no RSA (1024-, 2048-, 4096-bit), AES-CBC (128-bit) e SHA1.</span><span class="sxs-lookup"><span data-stu-id="34a2c-217">For example, for a TLS session uses only the ciphersuite TLS_RSA_WITH_AES_128_CBC_SHA, this function will perform self test on the RSA (1024-, 2048-, 4096-bit), AES-CBC (128-bit) and SHA1.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-218">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-218">Parameters</span></span>

- <span data-ttu-id="34a2c-219">**crypto_table** Ponteiro para a tabela cripto que está a ser usada pela sessão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-219">**crypto_table** Pointer to the crypto table being used by the TLS session.</span></span> <span data-ttu-id="34a2c-220">Esta é a mesma crypto_table a ser passada para a **_chamada nx_secure_tls_session_create()._**</span><span class="sxs-lookup"><span data-stu-id="34a2c-220">This is the same crypto_table being passed into the **_nx_secure_tls_session_create()_** call.</span></span>
- <span data-ttu-id="34a2c-221">**metadados** Ponteiro para o espaço para a área de metadados de criptografia.</span><span class="sxs-lookup"><span data-stu-id="34a2c-221">**metadata** Pointer to space for cryptography metadata area.</span></span> <span data-ttu-id="34a2c-222">.</span><span class="sxs-lookup"><span data-stu-id="34a2c-222">.</span></span>
- <span data-ttu-id="34a2c-223">**metadata_size** Tamanho do tampão de metadados.</span><span class="sxs-lookup"><span data-stu-id="34a2c-223">**metadata_size** Size of the metadata buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-224">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-224">Return Values</span></span>

- <span data-ttu-id="34a2c-225">**NX_SECURE_TLS_SUCCESS** (0x00) testaram com sucesso os métodos de cripto fornecidos.</span><span class="sxs-lookup"><span data-stu-id="34a2c-225">**NX_SECURE_TLS_SUCCESS** (0x00) Successfully tested the crypto methods provided.</span></span>
- <span data-ttu-id="34a2c-226">**NX_PTR_ERROR** (0x07) Estrutura do método do cripto inválido</span><span class="sxs-lookup"><span data-stu-id="34a2c-226">**NX_PTR_ERROR** (0x07) Invalid crypto method structure</span></span>
- <span data-ttu-id="34a2c-227">**NX_NOT_SUCCESSFUL** (0x43) O auto-teste crypto falha.</span><span class="sxs-lookup"><span data-stu-id="34a2c-227">**NX_NOT_SUCCESSFUL** (0x43) Crypto self test fails.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-228">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-228">Allowed From</span></span>

<span data-ttu-id="34a2c-229">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="34a2c-229">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-230">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-230">Example</span></span>

```C
/* crypto_tls_ciphers is the cipher table for the TLS session. */
/* metadata_buffer is the memory area used by the cipher functions. */

/* The following function verifies the supplied ciphersuties using the built-in
   self test. */

if (nx_secure_crypto_table_self_test(&crypto_tls_ciphers, metadata_buffer,
    sizeof(metadata_buffer)))
{
    printf("Crypto self test failed!\r\n");
    exit(0);
}
else
{
    printf("Crypto self test succeed!\r\n");
}

/* Now the ciphersuites are successfully test, it can be used in
   nx_secure_tls_session_create() */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-231">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-231">See Also</span></span>

- <span data-ttu-id="34a2c-232">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-232">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_module_hash_compute"></a><span data-ttu-id="34a2c-233">nx_secure_module_hash_compute</span><span class="sxs-lookup"><span data-stu-id="34a2c-233">nx_secure_module_hash_compute</span></span>

<span data-ttu-id="34a2c-234">Valor de haxixe computativo usando a função de haxixe fornecida pelo utilizador</span><span class="sxs-lookup"><span data-stu-id="34a2c-234">Computes hash value using user-supplied hash function</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-235">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-235">Prototype</span></span>

```C
UINT nx_secure_module_hash_compute(
                      NX_CRYPTO_METHOD *hamc_ptr,
                      UINT start_address, UINT end_address,
                      UCHAR *key, UINT key_length,
                      VOID *metadata, UINT metadata_size,
                      UCHAR *output_buffer, UINT output_buffer_size,
                      UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="34a2c-236">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-236">Description</span></span>

<span data-ttu-id="34a2c-237">Esta função calcula o valor do hash do fluxo de dados na área de memória especificada, utilizando o método de cripto HMAC fornecido e a cadeia de chaves.</span><span class="sxs-lookup"><span data-stu-id="34a2c-237">This function computes the hash value of the data stream in the specified memory area, using supplied HMAC crypto method and the key string.</span></span> <span data-ttu-id="34a2c-238">A função de computação de haxixe do módulo só está disponível se a biblioteca NetX Secure for construída com o seguinte símbolo a ser definido: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK</span><span class="sxs-lookup"><span data-stu-id="34a2c-238">The module hash compute function is available only if NetX Secure library is built with the following symbol being defined: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-239">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-239">Parameters</span></span>

- <span data-ttu-id="34a2c-240">**hmac_ptr** Ponteiro para o método de cripto HMAC que está a ser utilizado para a computação de valor de haxixe.</span><span class="sxs-lookup"><span data-stu-id="34a2c-240">**hmac_ptr** Pointer to the HMAC crypto method being used for the hash value computation.</span></span>
- <span data-ttu-id="34a2c-241">**start_address** O endereço inicial do tampão de dados</span><span class="sxs-lookup"><span data-stu-id="34a2c-241">**start_address** The starting address of the data buffer</span></span>
- <span data-ttu-id="34a2c-242">**end_address** O endereço final do tampão de dados.</span><span class="sxs-lookup"><span data-stu-id="34a2c-242">**end_address** The ending address of the data buffer.</span></span> <span data-ttu-id="34a2c-243">Note que o cálculo de haxixe não cobre os dados neste end_address.</span><span class="sxs-lookup"><span data-stu-id="34a2c-243">Note that hash computation does not cover the data at this end_address.</span></span>
- <span data-ttu-id="34a2c-244">**chave** A corda chave que está a ser utilizada na computação HMAC.</span><span class="sxs-lookup"><span data-stu-id="34a2c-244">**key** The key string being used in the HMAC computation.</span></span>
- <span data-ttu-id="34a2c-245">**key_length** O tamanho da corda chave, em bytes</span><span class="sxs-lookup"><span data-stu-id="34a2c-245">**key_length** The size of the key string, in bytes</span></span>
- <span data-ttu-id="34a2c-246">**metadados** Ponteiro para o espaço usado pelo algoritmo HMAC.</span><span class="sxs-lookup"><span data-stu-id="34a2c-246">**metadata** Pointer to space used by the HMAC algorithm.</span></span>
- <span data-ttu-id="34a2c-247">**metadata_size** Tamanho do tampão de metadados.</span><span class="sxs-lookup"><span data-stu-id="34a2c-247">**metadata_size** Size of the metadata buffer.</span></span>
- <span data-ttu-id="34a2c-248">**output_buffer** O local de memória onde a saída de haxixe está a ser armazenada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-248">**output_buffer** The memory location where the hash output is being stored at.</span></span>
- <span data-ttu-id="34a2c-249">**output_buffer_size** O espaço disponível do tampão de saída, em bytes</span><span class="sxs-lookup"><span data-stu-id="34a2c-249">**output_buffer_size** The available space of the output buffer, in bytes</span></span>
- <span data-ttu-id="34a2c-250">**atual_size** Devolvido pela função indicando o número real de bytes que estão a ser escritos no output_buffer.</span><span class="sxs-lookup"><span data-stu-id="34a2c-250">**actual_size** Returned by the function indicating the actual number of bytes being written into the output_buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-251">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-251">Return Values</span></span>

- <span data-ttu-id="34a2c-252">**0** Comumente computação com sucesso o valor do haxixe.</span><span class="sxs-lookup"><span data-stu-id="34a2c-252">**0** Successfully computed the hash value.</span></span>
- <span data-ttu-id="34a2c-253">**1** A computação de haxixe falhou.</span><span class="sxs-lookup"><span data-stu-id="34a2c-253">**1** The hash computation failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-254">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-254">Allowed From</span></span>

<span data-ttu-id="34a2c-255">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="34a2c-255">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-256">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-256">Example</span></span>

```C
/* Define the HMAC SHA256 method */
NX_CRYPTO_METHOD hmac_sha256 =
{
    NX_CRYPTO_AUTHENTICATION_HMAC_SHA2_256,    /* HMAC SHA256 algorithm  */
    0,                                         /* Key size, not used     */
    0,                                         /* IV size, not used      */
    NX_CRYPTO_HMAC_SHA256_ICV_FULL_LEN_IN_BITS,/* Transmitted ICV size   */
    NX_CRYPTO_SHA2_BLOCK_SIZE_IN_BYTES,        /* Block size in bytes    */
    sizeof(NX_CRYPTO_SHA256_HMAC),             /* Metadata size in bytes */
    _nx_crypto_method_hmac_sha256_init,        /* HMAC SHA256 init       */
    _nx_crypto_method_hmac_sha256_cleanup,     /* HMAC SHA256 cleanup    */
    _nx_crypto_method_hmac_sha256_operation    /* HMAC SHA256 operation  */
};

/* Define the hash key being used. */
const CHAR hash_key = “my hash key”;

/* Define starting address. */
UINT starting_address = 0x10000;

/* Define the ending address.
   Note that the hash computation covers the memory location
   before the ending address. */
UINT ending_address = 0x11000;

/* Declare the output buffer. */
#define OUTPUT_BUFFER_SIZE
UCHAR output_buffer[OUTPUT_BUFFER_SIZE];

UINT actual_size;

/* Declare 1K bytes of metadata buffer area. */
UCHAR metadata_buffer[1024];

/* Compute the hash value of the data between 0x10000 – 0x10FFF */
nx_secure_module_hash_compute(&hmac_sha256,
                              starting_address, ending_address,
                              hash_key, strlen(hash_key),
                              metadata_buffer, sizeof(metadata_buffer),
                              output_buffer, OUTPUT_BUFFER_SIZE, &actual_size);

/* If this function returns “0”, the hash value has been computed and is stored
   in output_buffer. */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-257">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-257">See Also</span></span>

- <span data-ttu-id="34a2c-258">nx_secure_crypto_method_self_test</span><span class="sxs-lookup"><span data-stu-id="34a2c-258">nx_secure_crypto_method_self_test</span></span>

## <a name="nx_secure_tls_active_certificate_set"></a><span data-ttu-id="34a2c-259">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-259">nx_secure_tls_active_certificate_set</span></span>

<span data-ttu-id="34a2c-260">Definir o certificado de identidade ativa para uma Sessão TLS NetX Secure</span><span class="sxs-lookup"><span data-stu-id="34a2c-260">Set the active identity certificate for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-261">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-261">Prototype</span></span>

```C
UINT  nx_secure_tls_active_certificate_set(
                   NX_SECURE_TLS_SESSION *tls_session,
                   NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a><span data-ttu-id="34a2c-262">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-262">Description</span></span>

<span data-ttu-id="34a2c-263">Este serviço destina-se a ser chamado a partir de uma chamada de sessão (ver nx_secure_tls_session_client_callback_set e nx_secure_tls_session_server_callback_set).</span><span class="sxs-lookup"><span data-stu-id="34a2c-263">This service is intended to be called from within a session callback (see nx_secure_tls_session_client_callback_set and nx_secure_tls_session_server_callback_set).</span></span> <span data-ttu-id="34a2c-264">Quando chamado com uma estrutura de NX_SECURE_X509_CERT previamente inicializada, esse certificado será utilizado em vez do certificado de identidade padrão.</span><span class="sxs-lookup"><span data-stu-id="34a2c-264">When called with a previously-initialized NX_SECURE_X509_CERT structure, that certificate will be used instead of the default identity certificate.</span></span> <span data-ttu-id="34a2c-265">Na maioria dos casos, o certificado deve ter sido adicionado à loja local (ver nx_secure_tls_local_certificate_add) ou o aperto de mão TLS pode falhar.</span><span class="sxs-lookup"><span data-stu-id="34a2c-265">In most cases, the certificate must have been added to the local store (see nx_secure_tls_local_certificate_add) or the TLS handshake may fail.</span></span>

<span data-ttu-id="34a2c-266">Este serviço destina-se a permitir que a TLS suporte vários certificados de identidade.</span><span class="sxs-lookup"><span data-stu-id="34a2c-266">This service is intended to allow TLS to support multiple identity certificates.</span></span> <span data-ttu-id="34a2c-267">Isto é útil para um servidor TLS que presta serviços múltiplos endereços de rede para que o servidor possa escolher um certificado apropriado para fornecer ao cliente remoto dependendo do ponto de entrada do cliente.</span><span class="sxs-lookup"><span data-stu-id="34a2c-267">This is useful for a TLS server that services multiple network addresses so the server can pick an appropriate certificate to provide to the remote client depending on the client's entrypoint.</span></span> <span data-ttu-id="34a2c-268">Para um cliente TLS, esta rotina pode ser usada para alterar o certificado enviado para um servidor remoto em tempo de execução depois de o servidor se ter identificado no aperto de mão TLS (isto é mais raro do que o caso de utilização do servidor TLS).</span><span class="sxs-lookup"><span data-stu-id="34a2c-268">For a TLS client, this routine may be used to change the certificate sent to a remote server at runtime after the server has identified itself in the TLS handshake (this is more rare than the TLS server use-case).</span></span>

<span data-ttu-id="34a2c-269">No caso de vários certificados poderem partilhar o mesmo nome distinto X.509, os certificados terão de ser adicionados utilizando nx_secure_tls_server_certificate_add, que introduz um identificador numérico separado do certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-269">In the case where multiple certificates may share the same X.509 distinguished name, certificates will need to be added using nx_secure_tls_server_certificate_add, which introduces a numeric identifier separate from the certificate.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-270">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-270">Parameters</span></span>

- <span data-ttu-id="34a2c-271">**session_ptr** O ponteiro para uma sessão de TLS passou para a chamada da sessão.</span><span class="sxs-lookup"><span data-stu-id="34a2c-271">**session_ptr** Pointer to a TLS Session instance passed into the session callback.</span></span>
- <span data-ttu-id="34a2c-272">**certificado** Ponteiro para um certificado X.509 inicializado que deve ser usado para a sessão atual.</span><span class="sxs-lookup"><span data-stu-id="34a2c-272">**certificate** Pointer to an initialized X.509 certificate that is to be used for the current session.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-273">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-273">Return Values</span></span>

- <span data-ttu-id="34a2c-274">**NX_SUCCESS** (0x00) Atribuição bem sucedida de certificado à sessão.</span><span class="sxs-lookup"><span data-stu-id="34a2c-274">**NX_SUCCESS** (0x00) Successful assignment of certificate to session.</span></span>
- <span data-ttu-id="34a2c-275">**NX_PTR_ERROR** (0x07) Sessão TLS inválida ou ponteiro de certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-275">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-276">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-276">Allowed From</span></span>

<span data-ttu-id="34a2c-277">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-278">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-278">Example</span></span>

```C
#define TLS_SNI_SERVER_NAME “www.example.com”
#define TLS_DEFAULT_SERVER_CERT_ID 2
#define TLS_EXAMPLE_CERT_ID 3


/* Callback for ClientHello extensions processing. */
static ULONG tls_server_callback(NX_SECURE_TLS_SESSION *tls_session,
                                 NX_SECURE_TLS_HELLO_EXTENSION *extensions,
                                 UINT num_extensions)
{
NX_SECURE_X509_DNS_NAME dns_name;
INT compare_value;
UINT status;
NX_SECURE_X509_CERT *cert_ptr;

    /* Grab a pointer to our default certificate in case the SNI extension is not
       available or the specified server name is unknown. */
    nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                     TLS_DEFAULT_SERVER_CERT_ID);


    /* Process Server Name Indication extension. */
    status = _nx_secure_tls_session_sni_extension_parse(tls_session, extensions,
                                                    num_extensions, &dns_name);

    /* If no extension found, that is OK. Use default certificate. */
    if(status == NX_SUCCESS)
    {
          /* SNI extension found, select an active certificate based on the server
             name. */

          /* Make sure our SNI name matches. */
          compare_value = memcmp(dns_name.nx_secure_x509_dns_name,
                                TLS_SNI_SERVER_NAME, strlen(TLS_SNI_SERVER_NAME));

          if(compare_value == 0 && dns_name.nx_secure_x509_dns_name_length !=
             strlen(TLS_SNI_SERVER_NAME))
          {
             /* Found a match, find the certificate we want to use. */
             _nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                                      TLS_EXAMPLE_CERT_ID);
          }
          else
          {
             /* No matching server name found. The application may choose to simply
                provide the default certificate (and probably resulting in an error
                in the remote client) or returning an error here to end the
                handshake. A user-defined non-zero error code will be sufficient –
                the error code will abort the TLS handshake and be returned to the
                caller that started the server. */
                return(0x500);
          }
      }
      else
      {
      }
      /* Set the certificate we want to use. */
      nx_secure_tls_active_certificate_set(tls_session, cert_ptr);

      /* Return success to continue TLS handshake. */
      return(NX_SUCCESS);
}

/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_TLS_SESSION server_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&server_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_tls_session_create: 0x%x\n", status);
    }

    /* Setup our packet reassembly buffer. See
       nx_secure_tls_session_packet_buffer_set for more information. */
    nx_secure_tls_session_packet_buffer_set(&server_tls_session,
                                      server_packet_buffer,
                                      sizeof(server_packet_buffer));


    /* Set callback for server TLS extension handling. */
    _nx_secure_tls_session_server_callback_set(&server_tls_session,
                                              tls_server_callback);

    /* Initialize our certificates – certificate data defined elsewhere. See
       section “Importing X.509 Certificates into NetX Secure” for more
       information. */
    nx_secure_x509_certificate_initialize(&default_certificate,
                                      default_cert_der,
                                      default _cert_der_len, NX_NULL, 0,
                                      default_cert_key_der,
                                      default_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &default_certificate,
                                         TLS_DEFAULT_SERVER_CERT_ID);

    /* Alternative identity certificate, needs to have a private key! */
    nx_secure_x509_certificate_initialize(&example_certificate,
                                      example_cert_der,
                                      example cert_der_len, NX_NULL, 0,
                                      example_cert_key_der,
                                      example_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &example_certificate,
                                         TLS_EXAMPLE_CERT_ID);

    /* Now we can start the TLS session as normal. */
       …
}
```

### <a name="see-also"></a><span data-ttu-id="34a2c-279">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-279">See Also</span></span>

- <span data-ttu-id="34a2c-280">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-280">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-281">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-281">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="34a2c-282">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-282">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="34a2c-283">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-283">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="34a2c-284">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-284">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="34a2c-285">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="34a2c-285">nx_secure_tls_server_certificate_find</span></span>
- <span data-ttu-id="34a2c-286">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="34a2c-286">nx_secure_tls_server_certificate_remove</span></span>

## <a name="nx_secure_tls_client_psk_set"></a><span data-ttu-id="34a2c-287">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-287">nx_secure_tls_client_psk_set</span></span>

<span data-ttu-id="34a2c-288">Desagure uma chave pré-partilhada para uma sessão de clientes NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="34a2c-288">Set a Pre-Shared Key for a NetX Secure TLS Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-289">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-289">Prototype</span></span>

```C
UINT  nx_secure_tls_client_psk_set(NX_SECURE_TLS_SESSION *session_ptr,
                              UCHAR *pre_shared_key, UINT psk_length,
                              UCHAR *psk_identity, UINT identity_length,
                              UCHAR *hint, UINT hint_length);
```

### <a name="description"></a><span data-ttu-id="34a2c-290">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-290">Description</span></span>

<span data-ttu-id="34a2c-291">Este serviço adiciona uma chave pré-partilhada (PSK), a sua cadeia de identidade e uma dica de identidade para um bloco de controlo de Sessão TLS, e define que o PSK deve ser usado nas ligações subsequentes do Cliente TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-291">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a TLS Session control block, and sets that PSK to be used in subsequent TLS Client connections.</span></span> <span data-ttu-id="34a2c-292">O PSK é utilizado em vez de um certificado digital quando as cifrasuites PSK são ativadas e utilizadas.</span><span class="sxs-lookup"><span data-stu-id="34a2c-292">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

<span data-ttu-id="34a2c-293">Neste caso, o PSK está associado a um Servidor TLS remoto específico com o qual o Cliente TLS deseja comunicar.</span><span class="sxs-lookup"><span data-stu-id="34a2c-293">In this case, the PSK is associated with a specific remote TLS Server with which the TLS Client wishes to communicate.</span></span> <span data-ttu-id="34a2c-294">O conjunto PSK através deste API será fornecido ao anfitrião remoto do Servidor TLS durante o próximo aperto de mão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-294">The PSK set through this API will be provided to the remote TLS Server host during the next TLS handshake.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-295">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-295">Parameters</span></span>

- <span data-ttu-id="34a2c-296">**session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-296">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-297">**pre_shared_key** O valor real do PSK.</span><span class="sxs-lookup"><span data-stu-id="34a2c-297">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="34a2c-298">**psk_length** O comprimento do valor PSK.</span><span class="sxs-lookup"><span data-stu-id="34a2c-298">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="34a2c-299">**psk_identity** Uma corda usada para identificar este valor psk.</span><span class="sxs-lookup"><span data-stu-id="34a2c-299">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="34a2c-300">**identity_length** O comprimento da identidade psk.</span><span class="sxs-lookup"><span data-stu-id="34a2c-300">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="34a2c-301">**dica** Uma cadeia usada para indicar qual grupo de PSKs escolher num servidor TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-301">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="34a2c-302">**hint_length** O comprimento da corda de sugestão.</span><span class="sxs-lookup"><span data-stu-id="34a2c-302">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-303">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-303">Return Values</span></span>

- <span data-ttu-id="34a2c-304">**NX_SUCCESS** (0x00) Adição bem sucedida de PSK.</span><span class="sxs-lookup"><span data-stu-id="34a2c-304">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="34a2c-305">**NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-305">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="34a2c-306">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Não pode adicionar outro PSK.</span><span class="sxs-lookup"><span data-stu-id="34a2c-306">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-307">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-307">Allowed From</span></span>

<span data-ttu-id="34a2c-308">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-308">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-309">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-309">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_client_psk_set(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-310">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-310">See Also</span></span>

- <span data-ttu-id="34a2c-311">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-311">nx_secure_tls_psk_add</span></span>
- <span data-ttu-id="34a2c-312">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-312">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-313">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-313">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="34a2c-314">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-314">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="34a2c-315">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-315">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_initialize"></a><span data-ttu-id="34a2c-316">nx_secure_tls_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-316">nx_secure_tls_initialize</span></span>

<span data-ttu-id="34a2c-317">Inicializa o módulo NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="34a2c-317">Initializes the NetX Secure TLS module</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-318">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-318">Prototype</span></span>

```C
VOID nx_secure_tls_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="34a2c-319">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-319">Description</span></span>

<span data-ttu-id="34a2c-320">Este serviço inicializa o módulo NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-320">This service initializes the NetX Secure TLS module.</span></span> <span data-ttu-id="34a2c-321">Deve ser chamado antes que outros serviços NetX Secure possam ser acedidos.</span><span class="sxs-lookup"><span data-stu-id="34a2c-321">It must be called before other NetX Secure services can be accessed.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-322">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-322">Parameters</span></span>

<span data-ttu-id="34a2c-323">Nenhum</span><span class="sxs-lookup"><span data-stu-id="34a2c-323">None</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-324">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-324">Return Values</span></span>

<span data-ttu-id="34a2c-325">Nenhuma</span><span class="sxs-lookup"><span data-stu-id="34a2c-325">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-326">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-326">Allowed From</span></span>

<span data-ttu-id="34a2c-327">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="34a2c-327">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-328">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-328">Example</span></span>

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a><span data-ttu-id="34a2c-329">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-329">See Also</span></span>

- <span data-ttu-id="34a2c-330">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-330">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_local_certificate_add"></a><span data-ttu-id="34a2c-331">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-331">nx_secure_tls_local_certificate_add</span></span>

<span data-ttu-id="34a2c-332">Adicione um certificado local à Sessão NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="34a2c-332">Add a local certificate to NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-333">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-333">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_add(
              NX_SECURE_TLS_SESSION *session_ptr,
              NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a><span data-ttu-id="34a2c-334">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-334">Description</span></span>

<span data-ttu-id="34a2c-335">Este serviço adiciona uma instância de estrutura NX_SECURE_X509_CERT inicializada à loja local de uma sessão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-335">This service adds an initialized NX_SECURE_X509_CERT structure instance to the local store of a TLS session.</span></span> <span data-ttu-id="34a2c-336">Este certificado pode ser utilizado pela pilha TLS para identificar o dispositivo durante o aperto de mão TLS (se tiver sido marcado como um certificado de identidade durante a inicialização da estrutura do certificado utilizando nx_secure_x509_certificate_initialize), ou como emitente como parte de uma cadeia de certificados fornecida ao anfitrião remoto durante o aperto de mão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-336">This certificate may used by the TLS stack to identify the device during the TLS handshake (if it was marked as an identity certificate during initialization of the certificate structure using nx_secure_x509_certificate_initialize), or as an issuer as part of a certificate chain provided to the remote host during the TLS handshake.</span></span>

<span data-ttu-id="34a2c-337">Se forem necessários vários certificados locais com o mesmo Nome Comum, os certificados podem ser adicionados utilizando o serviço *nx_secure_tls_server_certificate_add* (ver aviso abaixo).</span><span class="sxs-lookup"><span data-stu-id="34a2c-337">If multiple local certificates with the same Common Name are needed, certificates may be added using the *nx_secure_tls_server_certificate_add* service (see warning below).</span></span>

<span data-ttu-id="34a2c-338">É **necessário um** certificado para o modo TLS Server.</span><span class="sxs-lookup"><span data-stu-id="34a2c-338">A certificate is **required** for TLS Server mode.</span></span>

<span data-ttu-id="34a2c-339">Um certificado é *opcional* para o modo Cliente TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-339">A certificate is *optional* for TLS Client mode.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34a2c-340">*Esta API não deve ser utilizada com a mesma sessão TLS ao utilizar nx_secure_tls_server_certificate_add. O certificado de servidor API utiliza um identificador numérico único para cada certificado, e nx_secure_tls_local_certificate_add índices com base no Nome Comum X.509. Os serviços de certificados locais fornecem uma alternativa conveniente ao identificador numérico para aplicações que utilizem apenas um certificado de identidade único – utilizando o Nome Comum, a aplicação não precisa de acompanhar os identificadores numéricos.*</span><span class="sxs-lookup"><span data-stu-id="34a2c-340">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-341">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-341">Parameters</span></span>

- <span data-ttu-id="34a2c-342">**session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-342">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-343">**certificate_ptr** Ponteiro para uma instância inicializada do Certificado TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-343">**certificate_ptr** Pointer to an initialized TLS Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-344">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-344">Return Values</span></span>

- <span data-ttu-id="34a2c-345">**NX_SUCCESS** (0x00) Adição bem sucedida do certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-345">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="34a2c-346">**NX_INVALID_PARAMETERS** (0x4D) Tentou adicionar um certificado inválido ou duplicado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-346">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid or duplicate certificate.</span></span>
- <span data-ttu-id="34a2c-347">**NX_PTR_ERROR** (0x07) Sessão TLS inválida ou ponteiro de certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-347">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-348">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-348">Allowed From</span></span>

<span data-ttu-id="34a2c-349">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-350">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-350">Example</span></span>

```C
/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-351">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-351">See Also</span></span>

- <span data-ttu-id="34a2c-352">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-352">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-353">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-353">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="34a2c-354">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-354">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="34a2c-355">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="34a2c-355">nx_secure_tls_local_certificate_remove</span></span>
- <span data-ttu-id="34a2c-356">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="34a2c-356">nx_secure_tls_local_certificate_find</span></span>

## <a name="nx_secure_tls_local_certificate_find"></a><span data-ttu-id="34a2c-357">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="34a2c-357">nx_secure_tls_local_certificate_find</span></span>

<span data-ttu-id="34a2c-358">Encontre um certificado local numa Sessão De TLS Segura NetX por Nome Comum</span><span class="sxs-lookup"><span data-stu-id="34a2c-358">Find a local certificate in a NetX Secure TLS Session by Common Name</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-359">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-359">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_find(NX_SECURE_TLS_SESSION
                        *session_ptr, NX_SECURE_X509_CERT
                        **certificate, UCHAR *common_name, UINT
                        name_length);
```

### <a name="description"></a><span data-ttu-id="34a2c-360">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-360">Description</span></span>

<span data-ttu-id="34a2c-361">Este serviço encontra um certificado na loja de certificados de dispositivo local de uma sessão TLS e devolve um ponteiro à estrutura NX_SECURE_X509_CERT da loja.</span><span class="sxs-lookup"><span data-stu-id="34a2c-361">This service finds a certificate in the local device certificate store of a TLS session and returns a pointer to the NX_SECURE_X509_CERT structure in the store.</span></span> <span data-ttu-id="34a2c-362">O parâmetro common_name e o seu comprimento (name_length) são utilizados para identificar o certificado na loja, correspondendo ao campo X.509 Nome Comum do certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-362">The common_name parameter and it's length (name_length) are used to identify the certificate in the store by matching the certificate's X.509 Subject Common Name field.</span></span>

<span data-ttu-id="34a2c-363">Se estiver presente mais de um certificado com o mesmo Nome Comum, apenas o primeiro será devolvido – utilize *nx_secure_tls_server_certificate_find* em vez disso.</span><span class="sxs-lookup"><span data-stu-id="34a2c-363">If more than one certificate with the same Common Name is present, only the first one will be returned – use *nx_secure_tls_server_certificate_find* instead.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34a2c-364">*Esta API não deve ser utilizada com a mesma sessão TLS ao utilizar nx_secure_tls_server_certificate_add. O certificado de servidor API utiliza um identificador numérico único para cada certificado, e nx_secure_tls_local_certificate_add índices com base no Nome Comum X.509. Os serviços de certificados locais fornecem uma alternativa conveniente ao identificador numérico para aplicações que utilizem apenas um certificado de identidade único – utilizando o Nome Comum, a aplicação não precisa de acompanhar os identificadores numéricos.*</span><span class="sxs-lookup"><span data-stu-id="34a2c-364">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-365">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-365">Parameters</span></span>

- <span data-ttu-id="34a2c-366">**session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-366">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-367">**certificado** Devolva o Ponteiro ao certificado combinado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-367">**certificate** Return Pointer to matched certificate.</span></span>
- <span data-ttu-id="34a2c-368">**common_name** Cadeia de nome comum para combinar (nome DNS).</span><span class="sxs-lookup"><span data-stu-id="34a2c-368">**common_name** Common Name string to match (DNS name).</span></span>
- <span data-ttu-id="34a2c-369">**name_length** Comprimento dos common_name dados de cadeia.</span><span class="sxs-lookup"><span data-stu-id="34a2c-369">**name_length** Length of common_name string data.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-370">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-370">Return Values</span></span>

- <span data-ttu-id="34a2c-371">**NX_SUCCESS** certificado (0x00) foi encontrado e ponteiro devolvido no parâmetro "certificado".</span><span class="sxs-lookup"><span data-stu-id="34a2c-371">**NX_SUCCESS** (0x00) Certificate was found and pointer returned in "certificate" parameter.</span></span>
- <span data-ttu-id="34a2c-372">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Não foi encontrado nenhum certificado com o nome comum fornecido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-372">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate with the supplied Common Name was found.</span></span>
- <span data-ttu-id="34a2c-373">**NX_PTR_ERROR** (0x07) Sessão de TLS inválida, ponteiro de certificado ou cadeia de nome comum.</span><span class="sxs-lookup"><span data-stu-id="34a2c-373">**NX_PTR_ERROR** (0x07) Invalid TLS session, certificate pointer, or common name string.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-374">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-374">Allowed From</span></span>

<span data-ttu-id="34a2c-375">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-375">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-376">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-376">Example</span></span>

```C
NX_SECURE_X509_CERT *certificate_ptr;

/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */

status = nx_secure_tls_local_certificate_find(&tls_session, &certificate_ptr,
                                      “common name”, strlen(“common name”));

/* If status is NX_SUCCESS the variable “certificate_ptr” points to a certificate
   structure containing a certificate with the Common Name “common name”. */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-377">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-377">See Also</span></span>

- <span data-ttu-id="34a2c-378">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-378">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-379">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-379">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="34a2c-380">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-380">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="34a2c-381">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="34a2c-381">nx_secure_tls_local_certificate_remove</span></span>
- <span data-ttu-id="34a2c-382">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-382">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_local_certificate_remove"></a><span data-ttu-id="34a2c-383">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="34a2c-383">nx_secure_tls_local_certificate_remove</span></span>

<span data-ttu-id="34a2c-384">Remover certificado local da Sessão NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="34a2c-384">Remove local certificate from NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-385">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-385">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_remove(NX_SECURE_TLS_SESSION
                  *session_ptr, UCHAR *common_name, UINT
                  common_name_length);
```

### <a name="description"></a><span data-ttu-id="34a2c-386">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-386">Description</span></span>

<span data-ttu-id="34a2c-387">Este serviço remove uma instância de certificado local de uma sessão de TLS, chave no campo Nome Comum no certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-387">This service removes a local certificate instance from a TLS session, keyed on the Common Name field in the certificate.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34a2c-388">*Esta API não deve ser utilizada com a mesma sessão TLS ao utilizar nx_secure_tls_server_certificate_add. O certificado de servidor API utiliza um identificador numérico único para cada certificado, e nx_secure_tls_local_certificate_add índices com base no Nome Comum X.509. Os serviços de certificados locais fornecem uma alternativa conveniente ao identificador numérico para aplicações que utilizem apenas um certificado de identidade único – utilizando o Nome Comum, a aplicação não precisa de acompanhar os identificadores numéricos.*</span><span class="sxs-lookup"><span data-stu-id="34a2c-388">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-389">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-389">Parameters</span></span>

- <span data-ttu-id="34a2c-390">**session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-390">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-391">**common_name** O valor do nome comum do certificado a retirar.</span><span class="sxs-lookup"><span data-stu-id="34a2c-391">**common_name** The Common Name value of the certificate to be removed.</span></span>
- <span data-ttu-id="34a2c-392">**common_name_length** O comprimento da corda nome comum.</span><span class="sxs-lookup"><span data-stu-id="34a2c-392">**common_name_length** The length of the Common Name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-393">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-393">Return Values</span></span>

- <span data-ttu-id="34a2c-394">**NX_SUCCESS** (0x00) Adição bem sucedida do certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-394">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="34a2c-395">**NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-395">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="34a2c-396">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** certificado (0x119) não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-396">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Certificate was not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-397">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-397">Allowed From</span></span>

<span data-ttu-id="34a2c-398">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-398">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-399">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-399">Example</span></span>

```C
/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-400">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-400">See Also</span></span>

- <span data-ttu-id="34a2c-401">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-401">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-402">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-402">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="34a2c-403">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-403">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="34a2c-404">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-404">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_metadata_size_calculate"></a><span data-ttu-id="34a2c-405">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="34a2c-405">nx_secure_tls_metadata_size_calculate</span></span>

<span data-ttu-id="34a2c-406">Calcular o tamanho dos metadados criptográficos para uma Sessão de TLS NetX Secure</span><span class="sxs-lookup"><span data-stu-id="34a2c-406">Calculate size of cryptographic metadata for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-407">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-407">Prototype</span></span>

```C
UINT  nx_secure_tls_metadata_size_calculate(
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        ULONG *metadata_size);
```

### <a name="description"></a><span data-ttu-id="34a2c-408">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-408">Description</span></span>

<span data-ttu-id="34a2c-409">Este serviço calcula e devolve o tamanho dos metadados criptográficos necessários para uma sessão de TLS e tabela de criptografia TLS (consulte a secção "Inicialização de TLS com Métodos Criptográficos" para obter mais informações sobre a tabela de cifra criptográfica).</span><span class="sxs-lookup"><span data-stu-id="34a2c-409">This service calculates and returns the size of the cryptographic metadata needed for a particular TLS session and TLS cryptography table (see the section "Initializing TLS with Cryptographic Methods" for more information on the cryptographic cipher table).</span></span>

<span data-ttu-id="34a2c-410">Este serviço deve ser chamado com a tabela criptográfica desejada para calcular o tamanho do tampão de metadados transmitido em nx_secure_tls_session_create.</span><span class="sxs-lookup"><span data-stu-id="34a2c-410">This service should be called with the desired cryptographic table to calculate the size of the metadata buffer passed into nx_secure_tls_session_create.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-411">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-411">Parameters</span></span>

- <span data-ttu-id="34a2c-412">**crypto_table** Ponteiro para uma tabela completa de criptografia NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-412">**crypto_table** Pointer to a complete NetX Secure TLS cryptography table.</span></span>
- <span data-ttu-id="34a2c-413">**metadata_size** A saída do tamanho do cálculo em bytes.</span><span class="sxs-lookup"><span data-stu-id="34a2c-413">**metadata_size** The output of the size calculation in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-414">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-414">Return Values</span></span>

- <span data-ttu-id="34a2c-415">**NX_SUCCESS** (0x00) Cálculo bem sucedido do tamanho dos metadados.</span><span class="sxs-lookup"><span data-stu-id="34a2c-415">**NX_SUCCESS** (0x00) Successful calculation of metadata size.</span></span>
- <span data-ttu-id="34a2c-416">**NX_PTR_ERROR** (0x07) Mesa de cripto inválida ou ponteiro do tamanho do retorno.</span><span class="sxs-lookup"><span data-stu-id="34a2c-416">**NX_PTR_ERROR** (0x07) Invalid crypto table or return size pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-417">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-417">Allowed From</span></span>

<span data-ttu-id="34a2c-418">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-418">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-419">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-419">Example</span></span>

```C
/* Pointer to the platform-specific cipher table. */
extern nx_crypto_tls_ciphers;

/* Return variable for metadata size. */
ULONG crypto_metadata_size;

/* Calculate metadata size.  */
status =  nx_secure_tls_metadata_size_calculate(&nx_crypto_tls_ciphers,
                                                &crypto_metadata_size);


/* If status is NX_SUCCESS then crypto_metadata_size contains the size of the
   metadata buffer for the table nx_crypto_tls_ciphers.  */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-420">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-420">See Also</span></span>

- <span data-ttu-id="34a2c-421">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-421">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_packet_allocate"></a><span data-ttu-id="34a2c-422">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-422">nx_secure_tls_packet_allocate</span></span>

<span data-ttu-id="34a2c-423">Aloque um pacote para uma Sessão NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="34a2c-423">Allocate a packet for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-424">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-424">Prototype</span></span>

```C
UINT  nx_secure_tls_packet_allocate(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET_POOL *pool_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34a2c-425">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-425">Description</span></span>

<span data-ttu-id="34a2c-426">Este serviço atribui uma NX_PACKET para a sessão de TLS ativa especificada a partir do NX_PACKET_POOL especificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-426">This service allocates an NX_PACKET for the specified active TLS session from the specified NX_PACKET_POOL.</span></span> <span data-ttu-id="34a2c-427">Este serviço deve ser chamado pela aplicação para atribuir pacotes de dados a serem enviados através de uma ligação TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-427">This service should be called by the application to allocate data packets to be sent over a TLS connection.</span></span> <span data-ttu-id="34a2c-428">A sessão TLS deve ser inicializada antes de ligar para este serviço.</span><span class="sxs-lookup"><span data-stu-id="34a2c-428">The TLS session must be initialized before calling this service.</span></span>

<span data-ttu-id="34a2c-429">O pacote atribuído é devidamente inicializado de modo a que os dados do cabeçalho e do rodapé TLS possam ser adicionados após a população dos dados do pacote.</span><span class="sxs-lookup"><span data-stu-id="34a2c-429">The allocated packet is properly initialized so that TLS header and footer data may be added after the packet data is populated.</span></span> <span data-ttu-id="34a2c-430">O comportamento é idêntico ao *nx_packet_allocate*.</span><span class="sxs-lookup"><span data-stu-id="34a2c-430">The behavior is otherwise identical to *nx_packet_allocate*.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-431">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-431">Parameters</span></span>

- <span data-ttu-id="34a2c-432">**session_ptr** Ponteiro para uma sessão de TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-432">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-433">**pool_ptr** O ponteiro para um NX_PACKET_POOL a partir do qual atribuir o pacote.</span><span class="sxs-lookup"><span data-stu-id="34a2c-433">**pool_ptr** Pointer to an NX_PACKET_POOL from which to allocate the packet.</span></span>
- <span data-ttu-id="34a2c-434">**packet_ptr** Ponteiro de saída para o pacote recém-atribuído.</span><span class="sxs-lookup"><span data-stu-id="34a2c-434">**packet_ptr** Output pointer to the newly-allocated packet.</span></span>
- <span data-ttu-id="34a2c-435">**wait_option** Opção de suspensão para alocação de pacotes.</span><span class="sxs-lookup"><span data-stu-id="34a2c-435">**wait_option** Suspension option for packet allocation.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-436">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-436">Return Values</span></span>

- <span data-ttu-id="34a2c-437">**NX_SUCCESS** (0x00) Atribuição de pacotes bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="34a2c-437">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="34a2c-438">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) A atribuição de pacotes subjacentes falhou.</span><span class="sxs-lookup"><span data-stu-id="34a2c-438">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>
- <span data-ttu-id="34a2c-439">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) A sessão TLS fornecida não foi inicializada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-439">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-440">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-440">Allowed From</span></span>

<span data-ttu-id="34a2c-441">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-441">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-442">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-442">Example</span></span>

```C
/* Allocate a new TLS packet from the previously created packet pool and
previously initialized TLS session.   */

status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &packet_ptr,
                                       NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
variable packet_ptr.  */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-443">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-443">See Also</span></span>

- <span data-ttu-id="34a2c-444">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="34a2c-444">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="34a2c-445">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-445">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-446">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-446">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="34a2c-447">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="34a2c-447">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="34a2c-448">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="34a2c-448">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="34a2c-449">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="34a2c-449">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="34a2c-450">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="34a2c-450">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="34a2c-451">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="34a2c-451">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="34a2c-452">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-452">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_psk_add"></a><span data-ttu-id="34a2c-453">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-453">nx_secure_tls_psk_add</span></span>

<span data-ttu-id="34a2c-454">Adicione uma chave pré-partilhada a uma Sessão de TLS Segura NetX</span><span class="sxs-lookup"><span data-stu-id="34a2c-454">Add a Pre-Shared Key to a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-455">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-455">Prototype</span></span>

```C
UINT  nx_secure_tls_psk_add(NX_SECURE_TLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a><span data-ttu-id="34a2c-456">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-456">Description</span></span>

<span data-ttu-id="34a2c-457">Este serviço adiciona uma chave pré-partilhada (PSK), a sua cadeia de identidade e uma dica de identidade para um bloco de controlo TLS Session.</span><span class="sxs-lookup"><span data-stu-id="34a2c-457">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a TLS Session control block.</span></span> <span data-ttu-id="34a2c-458">O PSK é utilizado em vez de um certificado digital quando as cifrasuites PSK são ativadas e utilizadas.</span><span class="sxs-lookup"><span data-stu-id="34a2c-458">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-459">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-459">Parameters</span></span>

- <span data-ttu-id="34a2c-460">**session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-460">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-461">**pre_shared_key** O valor real do PSK.</span><span class="sxs-lookup"><span data-stu-id="34a2c-461">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="34a2c-462">**psk_length** O comprimento do valor PSK.</span><span class="sxs-lookup"><span data-stu-id="34a2c-462">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="34a2c-463">**psk_identity** Uma corda usada para identificar este valor psk.</span><span class="sxs-lookup"><span data-stu-id="34a2c-463">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="34a2c-464">**identity_length** O comprimento da identidade psk.</span><span class="sxs-lookup"><span data-stu-id="34a2c-464">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="34a2c-465">**dica** Uma cadeia usada para indicar qual grupo de PSKs escolher num servidor TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-465">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="34a2c-466">**hint_length** O comprimento da corda de sugestão.</span><span class="sxs-lookup"><span data-stu-id="34a2c-466">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-467">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-467">Return Values</span></span>

- <span data-ttu-id="34a2c-468">**NX_SUCCESS** (0x00) Adição bem sucedida de PSK.</span><span class="sxs-lookup"><span data-stu-id="34a2c-468">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="34a2c-469">**NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-469">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="34a2c-470">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Não pode adicionar outro PSK.</span><span class="sxs-lookup"><span data-stu-id="34a2c-470">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125)  Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-471">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-471">Allowed From</span></span>

<span data-ttu-id="34a2c-472">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-472">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-473">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-473">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_psk_add(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-474">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-474">See Also</span></span>

- <span data-ttu-id="34a2c-475">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-475">nx_secure_tls_client_psk_set</span></span>
- <span data-ttu-id="34a2c-476">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-476">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-477">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-477">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="34a2c-478">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-478">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="34a2c-479">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-479">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_remote_certificate_allocate"></a><span data-ttu-id="34a2c-480">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-480">nx_secure_tls_remote_certificate_allocate</span></span>

<span data-ttu-id="34a2c-481">Alocar espaço para o certificado fornecido por um anfitrião remoto TLS</span><span class="sxs-lookup"><span data-stu-id="34a2c-481">Allocate space for the certificate provided by a remote TLS host</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-482">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-482">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_allocate(
                 NX_SECURE_TLS_SESSION *session_ptr,
                 NX_SECURE_X509_CERT *certificate_ptr,
                 UCHAR *raw_certificate_buffer,
                 UINT raw_buffer_size);
```

### <a name="description"></a><span data-ttu-id="34a2c-483">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-483">Description</span></span>

<span data-ttu-id="34a2c-484">Este serviço adiciona uma instância de estrutura de NX_SECURE_X509_CERT não iniializada a uma sessão de TLS com o objetivo de atribuir espaço para certificados fornecidos por um anfitrião remoto durante uma sessão de TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-484">This service adds an uninitialized NX_SECURE_X509_CERT structure instance to a TLS session for the purpose of allocating space for certificates provided by a remote host during a TLS session.</span></span> <span data-ttu-id="34a2c-485">Os dados do certificado remoto são analisados pelo NetX Secure TLS e essa informação é utilizada para preencher a instância da estrutura do certificado fornecida a esta função.</span><span class="sxs-lookup"><span data-stu-id="34a2c-485">The remote certificate data is parsed by NetX Secure TLS and that information is used to populate the certificate structure instance provided to this function.</span></span> <span data-ttu-id="34a2c-486">Os certificados adicionados desta forma são colocados numa lista ligada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-486">Certificates added in this manner are placed in a linked list.</span></span>

<span data-ttu-id="34a2c-487">Se se espera que o anfitrião remoto forneça vários certificados, esta função deve ser chamada repetidamente para alocar espaço para todos os certificados.</span><span class="sxs-lookup"><span data-stu-id="34a2c-487">If it is expected that the remote host will provide multiple certificates, this function should be called repeatedly to allocate space for all certificates.</span></span> <span data-ttu-id="34a2c-488">Os certificados adicionais são adicionados ao final da lista ligada ao certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-488">The additional certificates are added to the end of the certificate linked list.</span></span>

<span data-ttu-id="34a2c-489">A não atribuição de um certificado remoto fará com que o modo do Cliente TLS falhe durante o aperto de mão TLS, a menos que esteja a ser utilizada uma cifrassuita de chave pré-partilhada (PSK).</span><span class="sxs-lookup"><span data-stu-id="34a2c-489">Failure to allocate a remote certificate will cause TLS Client mode to fail during the TLS handshake unless a Pre-Shared Key (PSK) ciphersuite is in use.</span></span>

<span data-ttu-id="34a2c-490">O *parâmetro raw_certificate_buffer* aponta para o espaço atribuído para armazenar o certificado remoto de entrada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-490">The *raw_certificate_buffer* parameter points to space allocated to store the incoming remote certificate.</span></span> <span data-ttu-id="34a2c-491">Os certificados típicos com teclas RSA de 2048 bits usando SHA-256 para assinaturas estão na gama de bytes 1000-2000.</span><span class="sxs-lookup"><span data-stu-id="34a2c-491">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="34a2c-492">O tampão deve ser grande o suficiente para pelo menos manter esse tamanho, mas dependendo dos certificados de anfitrião remoto pode ser significativamente menor ou maior.</span><span class="sxs-lookup"><span data-stu-id="34a2c-492">The buffer should be large enough to at least hold that size, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="34a2c-493">Note que se o tampão for demasiado pequeno para segurar o certificado de entrada, o aperto de mão TLS terminará com um erro.</span><span class="sxs-lookup"><span data-stu-id="34a2c-493">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

<span data-ttu-id="34a2c-494">Para o modo Servidor TLS, só é necessária uma atribuição de certificado remoto se a autenticação do certificado do cliente estiver ativada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-494">For TLS Server mode, a remote certificate allocation is needed only if client certificate authentication is enabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-495">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-495">Parameters</span></span>

- <span data-ttu-id="34a2c-496">**session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-496">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-497">**certificate_ptr** Ponteiro para uma instância de certificado X.509 não ininitializada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-497">**certificate_ptr** Pointer to an uninitialized X.509 Certificate instance.</span></span>
- <span data-ttu-id="34a2c-498">**raw_certificate_buffer** Ponteiro para um tampão para manter o certificado não analisado recebido do anfitrião remoto.</span><span class="sxs-lookup"><span data-stu-id="34a2c-498">**raw_certificate_buffer** Pointer to a buffer to hold the un-parsed certificate received from the remote host.</span></span>
- <span data-ttu-id="34a2c-499">**raw_buffer_size** Tamanho do tampão de certificado bruto.</span><span class="sxs-lookup"><span data-stu-id="34a2c-499">**raw_buffer_size** Size of the raw certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-500">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-500">Return Values</span></span>

- <span data-ttu-id="34a2c-501">**NX_SUCCESS** (0x00) Atribuição bem sucedida do certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-501">**NX_SUCCESS** (0x00) Successful allocation of certificate.</span></span>
- <span data-ttu-id="34a2c-502">**NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-502">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="34a2c-503">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) O tampão fornecido era demasiado pequeno.</span><span class="sxs-lookup"><span data-stu-id="34a2c-503">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="34a2c-504">**NX_INVALID_PARAMETERS** (0x4D) Tentou adicionar um certificado inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-504">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid certificate.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-505">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-505">Allowed From</span></span>

<span data-ttu-id="34a2c-506">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-506">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-507">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-507">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-508">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-508">See Also</span></span>

- <span data-ttu-id="34a2c-509">nx_secure_x509_certificate_initialize,</span><span class="sxs-lookup"><span data-stu-id="34a2c-509">nx_secure_x509_certificate_initialize,</span></span>
- <span data-ttu-id="34a2c-510">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-510">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_remote_certificate_buffer_allocate"></a><span data-ttu-id="34a2c-511">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-511">nx_secure_tls_remote_certificate_buffer_allocate</span></span>

<span data-ttu-id="34a2c-512">Alocar espaço para todos os certificados fornecidos por um anfitrião remoto TLS</span><span class="sxs-lookup"><span data-stu-id="34a2c-512">Allocate space for all certificates provided by a remote TLS host</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-513">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-513">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_buffer_allocate(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="34a2c-514">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-514">Description</span></span>

<span data-ttu-id="34a2c-515">Este serviço atribui espaço para processar as cadeias de certificados de entrada de anfitriões de servidores remotos de forma a realizar a autenticação e verificação X.509 numa instância do Cliente TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-515">This service allocates space to process incoming certificate chains from remote server hosts in order to perform X.509 authentication and verification in a TLS Client instance.</span></span> <span data-ttu-id="34a2c-516">No que diz o modo TLS Server, a atribuição de certificados remotos só é necessária se a autenticação do certificado do cliente X.509 estiver ativada – para as instâncias do Servidor TLS, o serviço *nx_secure_tls_session_x509_client_verify_configure* deve ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-516">For TLS Server mode, remote certificate allocation is needed only if client X.509 certificate authentication is enabled – for TLS Server instances the service *nx_secure_tls_session_x509_client_verify_configure* should be used instead.</span></span>

<span data-ttu-id="34a2c-517">A não atribuição de certificados remotos fará com que o modo do Cliente TLS falhe durante o aperto de mão TLS, a menos que esteja a ser utilizada uma cifrassuita de chave pré-partilhada (PSK).</span><span class="sxs-lookup"><span data-stu-id="34a2c-517">Failure to allocate remote certificates will cause TLS Client mode to fail during the TLS handshake unless a Pre-Shared Key (PSK) ciphersuite is in use.</span></span>

<span data-ttu-id="34a2c-518">O *parâmetro certificate_buffer* aponta para o espaço atribuído para armazenar os certificados remotos de entrada e os blocos de controlo necessários para esses certificados.</span><span class="sxs-lookup"><span data-stu-id="34a2c-518">The *certificate_buffer* parameter points to space allocated to store the incoming remote certificates and the control blocks needed for those certificates.</span></span> <span data-ttu-id="34a2c-519">O tampão será dividido pelo número de certificados *(certs_number*) com uma porção igual dada a cada certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-519">The buffer will be divided by the number of certificates (*certs_number*) with an equal portion given to each certificate.</span></span> <span data-ttu-id="34a2c-520">O parâmetro *buffer_size*  indica o tamanho do tampão.</span><span class="sxs-lookup"><span data-stu-id="34a2c-520">The *buffer_size*  parameter indicates the size of the buffer.</span></span> <span data-ttu-id="34a2c-521">O espaço necessário pode ser encontrado com a seguinte fórmula:</span><span class="sxs-lookup"><span data-stu-id="34a2c-521">The space needed can be found with the following formula:</span></span>

```C
buffer_size = (<expected max number of certificates in chain>) *
                 (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

<span data-ttu-id="34a2c-522">Os certificados típicos com teclas RSA de 2048 bits usando SHA-256 para assinaturas estão na gama de bytes 1000-2000.</span><span class="sxs-lookup"><span data-stu-id="34a2c-522">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="34a2c-523">O tampão deve ser suficientemente grande para, pelo menos, manter esse tamanho para cada certificado, mas dependendo dos certificados de anfitrião remoto podem ser significativamente menores ou maiores.</span><span class="sxs-lookup"><span data-stu-id="34a2c-523">The buffer should be large enough to at least hold that size for each certificate, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="34a2c-524">Note que se o tampão for demasiado pequeno para segurar o certificado de entrada, o aperto de mão TLS terminará com um erro.</span><span class="sxs-lookup"><span data-stu-id="34a2c-524">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-525">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-525">Parameters</span></span>

- <span data-ttu-id="34a2c-526">**session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-526">**session_ptr** Pointer to a previously created TLS Session  instance.</span></span>
- <span data-ttu-id="34a2c-527">**certs_number** Número de certificados a atribuir do tampão fornecido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-527">**certs_number** Number of certificates to allocate from the  provided buffer.</span></span>
- <span data-ttu-id="34a2c-528">**certificate_buffer** Ponteiro para um tampão para obter certificados recebidos de um hospedeiro remoto.</span><span class="sxs-lookup"><span data-stu-id="34a2c-528">**certificate_buffer** Pointer to a buffer to hold certificates received  from a remote host.</span></span>
- <span data-ttu-id="34a2c-529">**buffer_size** Tamanho do tampão de certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-529">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-530">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-530">Return Values</span></span>

- <span data-ttu-id="34a2c-531">**NX_SUCCESS** (0x00) Atribuição bem sucedida do certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-531">**NX_SUCCESS** (0x00) Successful allocation of certificate.</span></span>
- <span data-ttu-id="34a2c-532">**NX_PTR_ERROR** (0x07) Sessão TLS inválida ou ponteiro tampão.</span><span class="sxs-lookup"><span data-stu-id="34a2c-532">**NX_PTR_ERROR** (0x07) Invalid TLS session or buffer pointer.</span></span>
- <span data-ttu-id="34a2c-533">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) O tampão fornecido era demasiado pequeno.</span><span class="sxs-lookup"><span data-stu-id="34a2c-533">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="34a2c-534">**NX_INVALID_PARAMETERS** (0x4D) O tampão era demasiado pequeno para deter o número de certificados pretendido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-534">**NX_INVALID_PARAMETERS** (0x4D) The buffer was too small to hold  the desired number of certificates.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-535">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-535">Allowed From</span></span>

<span data-ttu-id="34a2c-536">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-536">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-537">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-537">Example</span></span>

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE           (CERTIFICATE_NUMBER * \
                              (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_buffer_allocate(&tls_session,
                                                      CERTIFICATE_NUMBER,
                                                      certificate_buffer,
                                                      BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-538">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-538">See Also</span></span>

- <span data-ttu-id="34a2c-539">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-539">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-540">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-540">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_remote_certificate_free_all"></a><span data-ttu-id="34a2c-541">nx_secure_tls_remote_certificate_free_all</span><span class="sxs-lookup"><span data-stu-id="34a2c-541">nx_secure_tls_remote_certificate_free_all</span></span>

<span data-ttu-id="34a2c-542">Espaço gratuito atribuído para certificados de entrada</span><span class="sxs-lookup"><span data-stu-id="34a2c-542">Free space allocated for incoming certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-543">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-543">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_free_all(
                  NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="34a2c-544">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-544">Description</span></span>

<span data-ttu-id="34a2c-545">Este serviço é utilizado para libertar todos os amortecedores de certificados atribuídos a uma sessão TLS específica, nx_secure_tls_remote_certificate_allocated devolvendo-os ao espaço de certificado gratuito da sessão.</span><span class="sxs-lookup"><span data-stu-id="34a2c-545">This service is used to free all of the certificate buffers allocated to a particular TLS Session by nx_secure_tls_remote_certificate_allocated by returning them to that session's free certificate space.</span></span> <span data-ttu-id="34a2c-546">Isto pode ser necessário se uma aplicação reutilizar um objeto de sessão TLS sem o eliminar e recriar com nx_secure_tls_session_delete e nx_secure_tls_session_create.</span><span class="sxs-lookup"><span data-stu-id="34a2c-546">This may be necessary if an application reuses a TLS session object without deleting it and recreating it with nx_secure_tls_session_delete and nx_secure_tls_session_create.</span></span>

<span data-ttu-id="34a2c-547">Note que o espaço do certificado remoto é recuperado automaticamente quando a sessão TLS é reposta como acontece em nx_secure_tls_session_end pelo que a maioria das aplicações não deve precisar de ligar para este serviço.</span><span class="sxs-lookup"><span data-stu-id="34a2c-547">Note that the remote certificate space is recovered automatically when the TLS session is reset as happens in nx_secure_tls_session_end so most applications should not need to call this service.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-548">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-548">Parameters</span></span>

- <span data-ttu-id="34a2c-549">**session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-549">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-550">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-550">Return Values</span></span>

- <span data-ttu-id="34a2c-551">**NX_SUCCESS** (0x00) Funcionamento bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-551">**NX_SUCCESS** (0x00) Successful operation.</span></span>
- <span data-ttu-id="34a2c-552">**NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-552">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="34a2c-553">**NX_INVALID_PARAMETERS** (0x4D) Erro interno – loja de certificados provavelmente corrupta.</span><span class="sxs-lookup"><span data-stu-id="34a2c-553">**NX_INVALID_PARAMETERS** (0x4D) Internal error – certificate store likely corrupt.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-554">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-554">Allowed From</span></span>

<span data-ttu-id="34a2c-555">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-555">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-556">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-556">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */

/* … TLS session setup, TCP connection, etc… */

/* End TLS session. */
nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

/* Free up certificate buffers for next connection. */
nx_secure_tls_remote_certificate_free_all(&tls_session);
```

### <a name="see-also"></a><span data-ttu-id="34a2c-557">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-557">See Also</span></span>

- <span data-ttu-id="34a2c-558">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-558">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-559">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-559">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="34a2c-560">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-560">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="34a2c-561">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="34a2c-561">nx_secure_tls_session_end</span></span>

## <a name="nx_secure_tls_server_certificate_add"></a><span data-ttu-id="34a2c-562">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-562">nx_secure_tls_server_certificate_add</span></span>

<span data-ttu-id="34a2c-563">Adicione um certificado especificamente para servidores TLS usando um identificador numérico</span><span class="sxs-lookup"><span data-stu-id="34a2c-563">Add a certificate specifically for TLS servers using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-564">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-564">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_add(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT *certificate, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="34a2c-565">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-565">Description</span></span>

<span data-ttu-id="34a2c-566">Este serviço é utilizado para adicionar um certificado à loja local de uma sessão de TLS (ver nx_secure_tls_local_certificate_add) utilizando um identificador numérico em vez de indexar a loja utilizando o Sujeito X.509 (Nome Comum) dentro do certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-566">This service is used to add a certificate to a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span> <span data-ttu-id="34a2c-567">O identificador numérico é separado do certificado e permite a adição de vários certificados como certificados de identidade a um servidor TLS, bem como permitir que vários certificados com o mesmo Nome Comum sejam adicionados à mesma loja local de sessão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-567">The numeric identifier is separate from the certificate and allows multiple certificates to be added as identity certificates to a TLS server, as well as allowing multiple certificates with the same Common Name to be added to the same TLS session local store.</span></span> <span data-ttu-id="34a2c-568">Este mesmo serviço pode ser utilizado para certificados de cliente, mas é raro um cliente TLS ter vários certificados de identidade.</span><span class="sxs-lookup"><span data-stu-id="34a2c-568">This same service can be used for client certificates, but it is rare for a TLS client to have multiple identity certificates.</span></span>

<span data-ttu-id="34a2c-569">O parâmetro cert_id é um número inteiro positivo não zero atribuído pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="34a2c-569">The cert_id parameter is a non-zero positive integer assigned by the application.</span></span> <span data-ttu-id="34a2c-570">O valor real não importa (além de zero), mas deve ser único na loja para a sessão TLS fornecida.</span><span class="sxs-lookup"><span data-stu-id="34a2c-570">The actual value does not matter (other than zero) but it must be unique in the store for the provided TLS session.</span></span> <span data-ttu-id="34a2c-571">O valor cert_id pode ser usado para encontrar e remover certificados da loja local usando nx_secure_tls_server_certificate_find e nx_secure_tls_server_certificate_remove, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="34a2c-571">The cert_id value can be used to find and remove certificates from the local store using nx_secure_tls_server_certificate_find and nx_secure_tls_server_certificate_remove, respectively.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34a2c-572">*Esta API não deve ser utilizada com a mesma sessão TLS ao utilizar nx_secure_tls_local_certificate_add. A API nx_secure_tls_server_certificate_add utiliza um identificador numérico único para cada certificado, e índice de serviços de certificado local com base no Nome Comum X.509. Os serviços de certificados de servidor permitem que existam vários certificados com dados partilhados (especialmente Nome Comum) na mesma loja local – isto é útil para um servidor com múltiplas identidades.*</span><span class="sxs-lookup"><span data-stu-id="34a2c-572">*This API should not be used with the same TLS session when using nx_secure_tls_local_certificate_add. The nx_secure_tls_server_certificate_add API uses a unique numeric identifier for each certificate, and local certificate services index based on the X.509 Common Name. The server certificate services allow multiple certificates with shared data (especially Common Name) to exist in the same local store – this is useful for a server with multiple identities.*</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-573">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-573">Parameters</span></span>

- <span data-ttu-id="34a2c-574">**session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-574">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-575">**certificado** Ponteiro para uma instância de certificado X.509 previamente inicialmente inicializada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-575">**certificate** Pointer to a previously initialized X.509 certificate instance.</span></span>
- <span data-ttu-id="34a2c-576">**cert_id** Positivo, não-zero, número de identificação de certificado relativamente único.</span><span class="sxs-lookup"><span data-stu-id="34a2c-576">**cert_id** Positive, non-zero, relatively unique certificate ID number.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-577">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-577">Return Values</span></span>

- <span data-ttu-id="34a2c-578">**NX_SUCCESS** (0x00)Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="34a2c-578">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="34a2c-579">**NX_PTR_ERROR** (0x07) Ponteiro orcertificado de sessão de TLS inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-579">**NX_PTR_ERROR** (0x07) Invalid TLS session orcertificate pointer.</span></span>
- <span data-ttu-id="34a2c-580">**NX_SECURE_TLS_CERT_ID_INVALID** (0x138) O ID do certificado fornecido tinha um valor inválido (provavelmente 0).</span><span class="sxs-lookup"><span data-stu-id="34a2c-580">**NX_SECURE_TLS_CERT_ID_INVALID** (0x138) The provided certificate ID had An invalid value (likely 0).</span></span>
- <span data-ttu-id="34a2c-581">**NX_SECURE_TLS_CERT_ID_DUPLICATE** (0x139) O certificado fornecido já estava presente na loja local.</span><span class="sxs-lookup"><span data-stu-id="34a2c-581">**NX_SECURE_TLS_CERT_ID_DUPLICATE** (0x139) The provided certificate ID was already present in the local store.</span></span>
- <span data-ttu-id="34a2c-582">**NX_INVALID_PARAMETERS(0x4D)** Erro interno – loja de certificados provavelmente corrupta.</span><span class="sxs-lookup"><span data-stu-id="34a2c-582">**NX_INVALID_PARAMETERS(0x4D)** Internal error – certificate store likely corrupt.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-583">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-583">Allowed From</span></span>

<span data-ttu-id="34a2c-584">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-584">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-585">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-585">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully added with the ID
0x12.  */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-586">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-586">See Also</span></span>

- <span data-ttu-id="34a2c-587">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-587">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-588">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-588">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="34a2c-589">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-589">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="34a2c-590">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="34a2c-590">nx_secure_tls_server_certificate_find</span></span>
- <span data-ttu-id="34a2c-591">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="34a2c-591">nx_secure_tls_server_certificate_remove</span></span>

## <a name="nx_secure_tls_server_certificate_find"></a><span data-ttu-id="34a2c-592">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="34a2c-592">nx_secure_tls_server_certificate_find</span></span>

<span data-ttu-id="34a2c-593">Encontre um certificado usando um identificador numérico</span><span class="sxs-lookup"><span data-stu-id="34a2c-593">Find a certificate using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-594">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-594">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_find(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT **certificate, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="34a2c-595">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-595">Description</span></span>

<span data-ttu-id="34a2c-596">Este serviço é utilizado para encontrar um certificado na loja local de uma sessão de TLS (ver nx_secure_tls_local_certificate_add) utilizando um identificador numérico em vez de indexar a loja utilizando o Sujeito X.509 (Nome Comum) dentro do certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-596">This service is used to find a certificate in a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span>

<span data-ttu-id="34a2c-597">O parâmetro cert_id é um número inteiro positivo não zero atribuído pelo pedido quando o certificado é adicionado à loja local de sessão TLS utilizando nx_secure_tls_server_certificate_add.</span><span class="sxs-lookup"><span data-stu-id="34a2c-597">The cert_id parameter is a non-zero positive integer assigned by the application when the certificate is added to the TLS session local store using nx_secure_tls_server_certificate_add.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34a2c-598">*Esta API não deve ser utilizada com a mesma sessão TLS ao utilizar nx_secure_tls_local_certificate_add. A API nx_secure_tls_server_certificate_add utiliza um identificador numérico único para cada certificado, e índice de serviços de certificado local com base no Nome Comum X.509. Os serviços de certificados de servidor permitem que existam vários certificados com dados partilhados (especialmente Nome Comum) na mesma loja local – isto é útil para um servidor com múltiplas identidades.*</span><span class="sxs-lookup"><span data-stu-id="34a2c-598">*This API should not be used with the same TLS session when using nx_secure_tls_local_certificate_add. The nx_secure_tls_server_certificate_add API uses a unique numeric identifier for each certificate, and local certificate services index based on the X.509 Common Name. The server certificate services allow multiple certificates with shared data (especially Common Name) to exist in the same local store – this is useful for a server with multiple identities.*</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-599">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-599">Parameters</span></span>

- <span data-ttu-id="34a2c-600">**session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-600">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-601">**certificado** Ponteiro para um ponteiro de certificado X.509 para devolver uma referência ao certificado encontrado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-601">**certificate** Pointer to an X.509 certificate pointer to return a reference to the found certificate.</span></span>
- <span data-ttu-id="34a2c-602">**cert_id** Valor de identificação de certificado positivo não zero.</span><span class="sxs-lookup"><span data-stu-id="34a2c-602">**cert_id** Non-zero positive certificate ID value.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-603">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-603">Return Values</span></span>

- <span data-ttu-id="34a2c-604">**NX_SUCCESS** (0x00)Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="34a2c-604">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="34a2c-605">**NX_PTR_ERROR** (0x07) Sessão TLS inválida ou ponteiro de certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-605">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>
- <span data-ttu-id="34a2c-606">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) O certificado fornecido não correspondia a nenhum na loja local da sessão TLS fornecida.</span><span class="sxs-lookup"><span data-stu-id="34a2c-606">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) The provided certificate ID did not match any in the local store of the provided TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-607">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-607">Allowed From</span></span>

<span data-ttu-id="34a2c-608">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-608">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-609">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-609">Example</span></span>

```C
NX_SECURE_X509_CERT *certificate;


/* Find certificate in TLS session.  */
status =  nx_secure_tls_server_certificate_find(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully found and a reference
returned in the certificate parameter.  */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-610">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-610">See Also</span></span>

- <span data-ttu-id="34a2c-611">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-611">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-612">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-612">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="34a2c-613">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-613">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="34a2c-614">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-614">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="34a2c-615">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="34a2c-615">nx_secure_tls_server_certificate_remove</span></span>

##  <a name="nx_secure_tls_server_certificate_remove"></a><span data-ttu-id="34a2c-616">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="34a2c-616">nx_secure_tls_server_certificate_remove</span></span>

<span data-ttu-id="34a2c-617">Remova um certificado de servidor local usando um identificador numérico</span><span class="sxs-lookup"><span data-stu-id="34a2c-617">Remove a local server certificate using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-618">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-618">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_remove(
                  NX_SECURE_TLS_SESSION *session_ptr, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="34a2c-619">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-619">Description</span></span>

<span data-ttu-id="34a2c-620">Este serviço é utilizado para remover um certificado da loja local de uma sessão de TLS (ver nx_secure_tls_local_certificate_add) utilizando um identificador numérico em vez de indexar a loja utilizando o Sujeito X.509 (Nome Comum) dentro do certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-620">This service is used to remove a certificate from a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span>

<span data-ttu-id="34a2c-621">O parâmetro cert_id é um número inteiro positivo não zero atribuído pelo pedido quando o certificado é adicionado à loja local de sessão TLS utilizando nx_secure_tls_server_certificate_add.</span><span class="sxs-lookup"><span data-stu-id="34a2c-621">The cert_id parameter is a non-zero positive integer assigned by the application when the certificate is added to the TLS session local store using nx_secure_tls_server_certificate_add.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-622">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-622">Parameters</span></span>

- <span data-ttu-id="34a2c-623">**session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-623">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-624">**cert_id** Valor de identificação de certificado positivo não zero.</span><span class="sxs-lookup"><span data-stu-id="34a2c-624">**cert_id** Non-zero positive certificate ID value.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-625">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-625">Return Values</span></span>

- <span data-ttu-id="34a2c-626">**NX_SUCCESS** (0x00)Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="34a2c-626">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="34a2c-627">**NX_PTR_ERROR** (0x07) Sessão TLS Inválida.</span><span class="sxs-lookup"><span data-stu-id="34a2c-627">**NX_PTR_ERROR** (0x07) Invalid TLS session.</span></span>
- <span data-ttu-id="34a2c-628">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) O certificado fornecido não correspondia a nenhum na loja local da sessão TLS fornecida.</span><span class="sxs-lookup"><span data-stu-id="34a2c-628">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) The provided certificate ID did not match any in the local store of the provided TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-629">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-629">Allowed From</span></span>

<span data-ttu-id="34a2c-630">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-630">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-631">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-631">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);
/* Use certificate in TLS session, etc… */

/* Remove certificate from TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_remove(&tls_session, 0x12);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-632">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-632">See Also</span></span>

- <span data-ttu-id="34a2c-633">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-633">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-634">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-634">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="34a2c-635">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-635">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="34a2c-636">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-636">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="34a2c-637">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="34a2c-637">nx_secure_tls_server_certificate_find</span></span>

## <a name="nx_secure_tls_session_alert_value_get"></a><span data-ttu-id="34a2c-638">nx_secure_tls_session_alert_value_get</span><span class="sxs-lookup"><span data-stu-id="34a2c-638">nx_secure_tls_session_alert_value_get</span></span>

<span data-ttu-id="34a2c-639">Obtenha o valor e o nível de alerta TLS enviados pelo anfitrião remoto</span><span class="sxs-lookup"><span data-stu-id="34a2c-639">Get the TLS alert value and level sent by the remote host</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-640">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-640">Prototype</span></span>

```C
UINT  nx_secure_tls_session_alert_value_get(
                   NX_SECURE_TLS_SESSION *session_ptr,
                   UINT *alert_level, UINT *alert_value);
```

### <a name="description"></a><span data-ttu-id="34a2c-641">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-641">Description</span></span>

<span data-ttu-id="34a2c-642">Este serviço é utilizado para recuperar o nível de alerta e valor do TLS quando o hospedeiro remoto envia um alerta em resposta a algum problema ou erro.</span><span class="sxs-lookup"><span data-stu-id="34a2c-642">This service is used to retrieve the TLS alert level and value when the remote host sends an alert in response to some problem or error.</span></span>

<span data-ttu-id="34a2c-643">Os valores dos parâmetros alert_level e alert_value só são válidos se esta função for chamada imediatamente após uma chamada da API TLS que devolveu um estado de NX_SECURE_TLS_ALERT_RECEIVED (0x114) indicando que foi recebido um alerta do hospedeiro remoto.</span><span class="sxs-lookup"><span data-stu-id="34a2c-643">The values of the alert_level and alert_value parameters are only valid if this function is called immediately following a TLS API call that returned a status of NX_SECURE_TLS_ALERT_RECEIVED (0x114) indicating that an alert was received from the remote host.</span></span>

<span data-ttu-id="34a2c-644">Note que se o anfitrião local TLS enviar um alerta, os códigos de erro devolvidos são muito mais descritivos do erro real do que o próprio alerta TLS porque os valores de alerta TLS são intencionalmente deixados ambíguos para evitar certos tipos de ataque (como um ataque de "acolchoamento oráculo" ou similar).</span><span class="sxs-lookup"><span data-stu-id="34a2c-644">Note that if the local host TLS sends an alert, the returned error codes are far more descriptive of the actual error than the TLS alert itself because TLS alert values are intentionally left ambiguous to prevent certain types of attack (such as a "padding oracle" attack or similar).</span></span>

<span data-ttu-id="34a2c-645">O nível de alerta só leva um de dois valores: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) ou NX_SECURE_TLS_ALERT_LEVEL_FATAL (0x2).</span><span class="sxs-lookup"><span data-stu-id="34a2c-645">The alert level only takes one of two values: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) or NX_SECURE_TLS_ALERT_LEVEL_FATAL (0x2).</span></span> <span data-ttu-id="34a2c-646">Em geral, apenas o Alerta CloseNotify (usado para indicar um fim bem-sucedido de uma sessão TLS) receberá um nível de "Aviso", embora algumas situações de configuração de extensão também possam ser consideradas advertências.</span><span class="sxs-lookup"><span data-stu-id="34a2c-646">In general, only the CloseNotify Alert (used to indicate a successful end to a TLS session) will be given a level of "Warning" though some extension configuration situations may also be considered warnings.</span></span> <span data-ttu-id="34a2c-647">A grande maioria dos alertas será "Fatal" indicando uma potencial falha de segurança e resultando no encerramento imediato da ligação TLS (aperto de mão ou sessão).</span><span class="sxs-lookup"><span data-stu-id="34a2c-647">The vast majority of alerts will be "Fatal" indicating a potential security failure and resulting in immediate closure of the TLS connection (handshake or session).</span></span>

<span data-ttu-id="34a2c-648">Os valores de alerta TLS são definidos nos RFCs TLS, aqui está a lista de RFC 5246 (TLSv1.2) para referência:</span><span class="sxs-lookup"><span data-stu-id="34a2c-648">The TLS alert values are defined in the TLS RFCs, here is the list from RFC 5246 (TLSv1.2) for reference:</span></span>

| <span data-ttu-id="34a2c-649">Nome do Alerta</span><span class="sxs-lookup"><span data-stu-id="34a2c-649">Alert Name</span></span>                     | <span data-ttu-id="34a2c-650">Valor</span><span class="sxs-lookup"><span data-stu-id="34a2c-650">Value</span></span> | <span data-ttu-id="34a2c-651">Descrição</span><span class="sxs-lookup"><span data-stu-id="34a2c-651">Description</span></span>                                                                                                                                                  |
| ---------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="34a2c-652">close_notify</span><span class="sxs-lookup"><span data-stu-id="34a2c-652">close_notify</span></span>                  | <span data-ttu-id="34a2c-653">0</span><span class="sxs-lookup"><span data-stu-id="34a2c-653">0</span></span>     | <span data-ttu-id="34a2c-654">Sem erro, indica fim de sessão bem-sucedido</span><span class="sxs-lookup"><span data-stu-id="34a2c-654">No error, indicates successful session end</span></span>                                                                                                                   |
| <span data-ttu-id="34a2c-655">unexpected_message</span><span class="sxs-lookup"><span data-stu-id="34a2c-655">unexpected_message</span></span>            | <span data-ttu-id="34a2c-656">10</span><span class="sxs-lookup"><span data-stu-id="34a2c-656">10</span></span>    | <span data-ttu-id="34a2c-657">TLS recebeu uma mensagem inesperada ou fora de encomenda</span><span class="sxs-lookup"><span data-stu-id="34a2c-657">TLS received an unexpected or out-of-order message</span></span>                                                                                                           |
| <span data-ttu-id="34a2c-658">bad_record_mac</span><span class="sxs-lookup"><span data-stu-id="34a2c-658">bad_record_mac</span></span>               | <span data-ttu-id="34a2c-659">20</span><span class="sxs-lookup"><span data-stu-id="34a2c-659">20</span></span>    | <span data-ttu-id="34a2c-660">A verificação de desencriptação e/ou MAC falhou</span><span class="sxs-lookup"><span data-stu-id="34a2c-660">Decryption and/or MAC verification failed</span></span>                                                                                                                    |
| <span data-ttu-id="34a2c-661">decryption_failed_RESERVED</span><span class="sxs-lookup"><span data-stu-id="34a2c-661">decryption_failed_RESERVED</span></span>   | <span data-ttu-id="34a2c-662">21</span><span class="sxs-lookup"><span data-stu-id="34a2c-662">21</span></span>    | <span data-ttu-id="34a2c-663">**PRECOTADO** A desencriptação falhou (depreciada devido a ataques de oráculo de enchimento)</span><span class="sxs-lookup"><span data-stu-id="34a2c-663">**DEPRECATED** Decryption failed (deprecated due to padding oracle attacks)</span></span>                                                                                      |
| <span data-ttu-id="34a2c-664">record_overflow</span><span class="sxs-lookup"><span data-stu-id="34a2c-664">record_overflow</span></span>               | <span data-ttu-id="34a2c-665">22</span><span class="sxs-lookup"><span data-stu-id="34a2c-665">22</span></span>    | <span data-ttu-id="34a2c-666">Foi recebido um recorde maior do que o tamanho máximo de registo do TLS</span><span class="sxs-lookup"><span data-stu-id="34a2c-666">A record was received that is larger than the TLS maximum record size</span></span>                                                                                        |
| <span data-ttu-id="34a2c-667">decompression_failure</span><span class="sxs-lookup"><span data-stu-id="34a2c-667">decompression_failure</span></span>         | <span data-ttu-id="34a2c-668">30</span><span class="sxs-lookup"><span data-stu-id="34a2c-668">30</span></span>    | <span data-ttu-id="34a2c-669">Um problema foi encontrado na compressão/descompressão de um registo TLS</span><span class="sxs-lookup"><span data-stu-id="34a2c-669">A problem was encountered in compression/decompression of a TLS record</span></span>                                                                                       |
| <span data-ttu-id="34a2c-670">handshake_failure</span><span class="sxs-lookup"><span data-stu-id="34a2c-670">handshake_failure</span></span>             | <span data-ttu-id="34a2c-671">40</span><span class="sxs-lookup"><span data-stu-id="34a2c-671">40</span></span>    | <span data-ttu-id="34a2c-672">Ocorreu um erro de aperto de mão não especificado que não está coberto por um alerta diferente.</span><span class="sxs-lookup"><span data-stu-id="34a2c-672">Some unspecified handshake error occurred that isn't covered by a different alert</span></span>                                                                            |
| <span data-ttu-id="34a2c-673">no_certificate_RESERVED</span><span class="sxs-lookup"><span data-stu-id="34a2c-673">no_certificate_RESERVED</span></span>      | <span data-ttu-id="34a2c-674">41</span><span class="sxs-lookup"><span data-stu-id="34a2c-674">41</span></span>    | <span data-ttu-id="34a2c-675">**DEPRECATED** EM TLS (apenas SSL)</span><span class="sxs-lookup"><span data-stu-id="34a2c-675">**DEPRECATED** in TLS (SSL only)</span></span>                                                                                                                                 |
| <span data-ttu-id="34a2c-676">bad_certificate</span><span class="sxs-lookup"><span data-stu-id="34a2c-676">bad_certificate</span></span>               | <span data-ttu-id="34a2c-677">42</span><span class="sxs-lookup"><span data-stu-id="34a2c-677">42</span></span>    | <span data-ttu-id="34a2c-678">Um certificado que foi recebido continha formatação inválida ou assinaturas</span><span class="sxs-lookup"><span data-stu-id="34a2c-678">A certificate that was received contained invalid formatting or signatures</span></span>                                                                                   |
| <span data-ttu-id="34a2c-679">unsupported_certificate</span><span class="sxs-lookup"><span data-stu-id="34a2c-679">unsupported_certificate</span></span>       | <span data-ttu-id="34a2c-680">43</span><span class="sxs-lookup"><span data-stu-id="34a2c-680">43</span></span>    | <span data-ttu-id="34a2c-681">Foi recebido um certificado de tipo inválido (por exemplo, certificado de assinatura utilizado para a autenticação do servidor TLS)</span><span class="sxs-lookup"><span data-stu-id="34a2c-681">A certificate was received that was of an invalid type (e.g. signing-only certificate used for TLS server authentication)</span></span>                                    |
| <span data-ttu-id="34a2c-682">certificate_revoked</span><span class="sxs-lookup"><span data-stu-id="34a2c-682">certificate_revoked</span></span>           | <span data-ttu-id="34a2c-683">44</span><span class="sxs-lookup"><span data-stu-id="34a2c-683">44</span></span>    | <span data-ttu-id="34a2c-684">O estatuto do certificado (conforme fornecido por um CRL ou OCSP) foi indicado como "revogado"</span><span class="sxs-lookup"><span data-stu-id="34a2c-684">The certificate status (as provided by a CRL or OCSP) was indicated as being "revoked"</span></span>                                                                       |
| <span data-ttu-id="34a2c-685">certificate_expired</span><span class="sxs-lookup"><span data-stu-id="34a2c-685">certificate_expired</span></span>           | <span data-ttu-id="34a2c-686">45</span><span class="sxs-lookup"><span data-stu-id="34a2c-686">45</span></span>    | <span data-ttu-id="34a2c-687">O certificado recebido estava fora do seu intervalo de datas válido (ou não válido ainda ou caducado)</span><span class="sxs-lookup"><span data-stu-id="34a2c-687">The received certificate was outside it's valid date range (either not valid yet or expired)</span></span>                                                                 |
| <span data-ttu-id="34a2c-688">certificate_unknown</span><span class="sxs-lookup"><span data-stu-id="34a2c-688">certificate_unknown</span></span>           | <span data-ttu-id="34a2c-689">46</span><span class="sxs-lookup"><span data-stu-id="34a2c-689">46</span></span>    | <span data-ttu-id="34a2c-690">Alguma emissão de certificado desconhecida foi encontrada que não foi abrangida por outros alertas</span><span class="sxs-lookup"><span data-stu-id="34a2c-690">Some unknown certificate issue was encountered that was not covered by other alerts</span></span>                                                                          |
| <span data-ttu-id="34a2c-691">illegal_parameter</span><span class="sxs-lookup"><span data-stu-id="34a2c-691">illegal_parameter</span></span>             | <span data-ttu-id="34a2c-692">47</span><span class="sxs-lookup"><span data-stu-id="34a2c-692">47</span></span>    | <span data-ttu-id="34a2c-693">Alguma configuração ou valor negociado no aperto de mão TLS foi inválido ou fora de alcance</span><span class="sxs-lookup"><span data-stu-id="34a2c-693">Some configuration or negotiated value in the TLS handshake was invalid or out of range</span></span>                                                                      |
| <span data-ttu-id="34a2c-694">unknown_ca</span><span class="sxs-lookup"><span data-stu-id="34a2c-694">unknown_ca</span></span>                    | <span data-ttu-id="34a2c-695">48</span><span class="sxs-lookup"><span data-stu-id="34a2c-695">48</span></span>    | <span data-ttu-id="34a2c-696">O certificado de identidade recebido não pôde ser rastreado através de uma cadeia de certificados a um certificado de CA de raiz fidedigna.</span><span class="sxs-lookup"><span data-stu-id="34a2c-696">The received identity certificate could not be traced via a certificate chain to a trusted root CA certificate.</span></span>                                              |
| <span data-ttu-id="34a2c-697">access_denied</span><span class="sxs-lookup"><span data-stu-id="34a2c-697">access_denied</span></span>                 | <span data-ttu-id="34a2c-698">49</span><span class="sxs-lookup"><span data-stu-id="34a2c-698">49</span></span>    | <span data-ttu-id="34a2c-699">Indica que foi recebido um certificado válido, mas o controlo de acesso a pedidos indicou que o certificado era inválido para os recursos solicitados.</span><span class="sxs-lookup"><span data-stu-id="34a2c-699">Indicates a valid certificate was received but application access control indicated that the certificate was invalid for the requested resources.</span></span>            |
| <span data-ttu-id="34a2c-700">decode_error</span><span class="sxs-lookup"><span data-stu-id="34a2c-700">decode_error</span></span>                  | <span data-ttu-id="34a2c-701">50</span><span class="sxs-lookup"><span data-stu-id="34a2c-701">50</span></span>    | <span data-ttu-id="34a2c-702">Algum campo ou valor num cabeçalho TLS ou mensagem de aperto de mão estava fora de alcance ou inválido, levando a uma falha na descodição de um registo TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-702">Some field or value in a TLS header or handshake message was out of range or invalid, leading to a failure in decoding of a TLS record.</span></span>                      |
| <span data-ttu-id="34a2c-703">decrypt_error</span><span class="sxs-lookup"><span data-stu-id="34a2c-703">decrypt_error</span></span>                 | <span data-ttu-id="34a2c-704">51</span><span class="sxs-lookup"><span data-stu-id="34a2c-704">51</span></span>    | <span data-ttu-id="34a2c-705">Não foi possível verificar um haxixe de mensagem de assinatura ou acabado durante o aperto de mão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-705">A signature or Finished message hash during the TLS handshake could not be verified.</span></span>                                                                         |
| <span data-ttu-id="34a2c-706">export_restriction_RESERVED</span><span class="sxs-lookup"><span data-stu-id="34a2c-706">export_restriction_RESERVED</span></span>  | <span data-ttu-id="34a2c-707">60</span><span class="sxs-lookup"><span data-stu-id="34a2c-707">60</span></span>    | <span data-ttu-id="34a2c-708">DEPRECATED EM TLSv1.2</span><span class="sxs-lookup"><span data-stu-id="34a2c-708">DEPRECATED in TLSv1.2</span></span>                                                                                                                                        |
| <span data-ttu-id="34a2c-709">protocol_version</span><span class="sxs-lookup"><span data-stu-id="34a2c-709">protocol_version</span></span>              | <span data-ttu-id="34a2c-710">70</span><span class="sxs-lookup"><span data-stu-id="34a2c-710">70</span></span>    | <span data-ttu-id="34a2c-711">A versão do protocolo TLS negociada durante o aperto de mão é reconhecida mas não suportada (por exemplo, tLSv1.0 foi apresentada, mas não ativada).</span><span class="sxs-lookup"><span data-stu-id="34a2c-711">The TLS protocol version negotiated during the handshake is recognized but not supported (e.g. TLSv1.0 was presented but not enabled).</span></span>                       |
| <span data-ttu-id="34a2c-712">insufficient_security</span><span class="sxs-lookup"><span data-stu-id="34a2c-712">insufficient_security</span></span>         | <span data-ttu-id="34a2c-713">71</span><span class="sxs-lookup"><span data-stu-id="34a2c-713">71</span></span>    | <span data-ttu-id="34a2c-714">Enviado sempre que um aperto de mão falha devido à falta de cifras seguras (por exemplo.key tamanho é demasiado pequeno para os requisitos de aplicação)</span><span class="sxs-lookup"><span data-stu-id="34a2c-714">Sent whenever a handshake fails due to a lack of secure ciphers (e.g. key size is too small for the application requirements)</span></span>                                |
| <span data-ttu-id="34a2c-715">internal_error</span><span class="sxs-lookup"><span data-stu-id="34a2c-715">internal_error</span></span>                | <span data-ttu-id="34a2c-716">80</span><span class="sxs-lookup"><span data-stu-id="34a2c-716">80</span></span>    | <span data-ttu-id="34a2c-717">Ocorreu alguns erros não TLS (por exemplo, problemas de atribuição de memória, problemas de aplicação) que resultaram numa sessão de TLS partida.</span><span class="sxs-lookup"><span data-stu-id="34a2c-717">Some non-TLS error (e.g. memory allocation problems, application issues) occurred resulting in a broken TLS session.</span></span>                                         |
| <span data-ttu-id="34a2c-718">user_canceled</span><span class="sxs-lookup"><span data-stu-id="34a2c-718">user_canceled</span></span>                 | <span data-ttu-id="34a2c-719">90</span><span class="sxs-lookup"><span data-stu-id="34a2c-719">90</span></span>    | <span data-ttu-id="34a2c-720">Devolvido se a sessão TLS for cancelada por um utilizador ou aplicação antes do aperto de mão estar completo (semelhante ao CloseNotify).</span><span class="sxs-lookup"><span data-stu-id="34a2c-720">Returned if the TLS session is cancelled by a user or application before the handshake is complete (similar to CloseNotify).</span></span>                                 |
| <span data-ttu-id="34a2c-721">no_renegotiation</span><span class="sxs-lookup"><span data-stu-id="34a2c-721">no_renegotiation</span></span>              | <span data-ttu-id="34a2c-722">100</span><span class="sxs-lookup"><span data-stu-id="34a2c-722">100</span></span>   | <span data-ttu-id="34a2c-723">O Anfitrião remoto não está disposto a executar apertos de mão de renegociação do TLS em resposta a um pedido de renegociação.</span><span class="sxs-lookup"><span data-stu-id="34a2c-723">Indiates that the remote host is not willing to perform TLS renegotiation handshakes in response to a renegotiation request.</span></span>                                 |
| <span data-ttu-id="34a2c-724">unsupported_extension</span><span class="sxs-lookup"><span data-stu-id="34a2c-724">unsupported_extension</span></span>         | <span data-ttu-id="34a2c-725">110</span><span class="sxs-lookup"><span data-stu-id="34a2c-725">110</span></span>   | <span data-ttu-id="34a2c-726">Enviado se um Cliente TLS receber um ServerHello contendo extensões não explicitamente solicitadas no ClientHello inicial (indicando que o servidor tem um problema).</span><span class="sxs-lookup"><span data-stu-id="34a2c-726">Sent if a TLS Client receives a ServerHello containing extensions not explicitly asked for in the initial ClientHello (indicating the server has a problem).</span></span> |

### <a name="parameters"></a><span data-ttu-id="34a2c-727">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-727">Parameters</span></span>

- <span data-ttu-id="34a2c-728">**session_ptr** Ponteiro para uma sessão de TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-728">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-729">**alert_level** Devolva o nível do alerta recebido (aviso ou fatal).</span><span class="sxs-lookup"><span data-stu-id="34a2c-729">**alert_level** Return the level of the received alert (warning or fatal).</span></span>
- <span data-ttu-id="34a2c-730">**alert_value** Devolva o valor do alerta recebido (ver tabela).</span><span class="sxs-lookup"><span data-stu-id="34a2c-730">**alert_value** Return the value of the received alert (see table).</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-731">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-731">Return Values</span></span>

- <span data-ttu-id="34a2c-732">**NX_SUCCESS** (0x00) Funcionamento bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-732">**NX_SUCCESS** (0x00) Successful operation.</span></span>
- <span data-ttu-id="34a2c-733">**NX_PTR_ERROR** (0x07) Sessão TLS Inválida.</span><span class="sxs-lookup"><span data-stu-id="34a2c-733">**NX_PTR_ERROR** (0x07) Invalid TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-734">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-734">Allowed From</span></span>

<span data-ttu-id="34a2c-735">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-735">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-736">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-736">Example</span></span>

```C
/* Return values. */
UINT status, alert_level, alert_value;


/* Start a TLS session.  */
status =  nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Check for “alert received” error. */
if(status == NX_SECURE_TLS_ALERT_RECEIVED)
{

        /* Get the alert level and value. */
        status =  nx_secure_tls_session_alert_value_get(&tls_session,
                                             &alert_level, &alert_value);

        /* Print out the received alert level and value. */
        printf("Alert recieved. Value: %d, Level: %d\n", alert_value,
                alert_level);
}
else if(status != NX_SUCCESS)
{
    /* Additional error handling. */
}
```

### <a name="see-also"></a><span data-ttu-id="34a2c-737">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-737">See Also</span></span>

- <span data-ttu-id="34a2c-738">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="34a2c-738">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="34a2c-739">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="34a2c-739">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="34a2c-740">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="34a2c-740">nx_secure_tls_session_receive</span></span>

## <a name="nx_secure_tls_session_certificate_callback_set"></a><span data-ttu-id="34a2c-741">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-741">nx_secure_tls_session_certificate_callback_set</span></span>

<span data-ttu-id="34a2c-742">Configurar uma chamada para o TLS usar para validação adicional de certificados</span><span class="sxs-lookup"><span data-stu-id="34a2c-742">Set up a callback for TLS to use for additional certificate validation</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-743">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-743">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_certificate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *session,
                                    NX_SECURE_X509_CERT *certificate));
```

### <a name="description"></a><span data-ttu-id="34a2c-744">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-744">Description</span></span>

<span data-ttu-id="34a2c-745">Este serviço atribui um ponteiro de função a uma sessão de TLS que o TLS invocará quando um certificado é recebido de um anfitrião remoto, permitindo que o pedido efetue verificações de validação como validação de DNS, revogação de certificados e aplicação da política de certificados.</span><span class="sxs-lookup"><span data-stu-id="34a2c-745">This service assigns a function pointer to a TLS session that TLS will invoke when a certificate is received from a remote host, allowing the application to perform validation checks such as DNS validation, certificate revocation, and certificate policy enforcement.</span></span>

<span data-ttu-id="34a2c-746">O NetX Secure TLS realizará a validação básica do percurso X.509 no certificado antes de invocar a chamada para garantir que o certificado pode ser rastreado até um certificado na loja de certificados fidedignos TLS, mas todas as outras validações serão tratadas por esta chamada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-746">NetX Secure TLS will perform basic X.509 path validation on the certificate before invoking the callback to assure that the certificate can be traced to a certificate in the TLS trusted certificate store, but all other validation will be handled by this callback.</span></span>

<span data-ttu-id="34a2c-747">O retorno fornece o ponteiro de sessão TLS e um ponteiro para o certificado de identidade de anfitrião remoto (a folha na cadeia de certificados).</span><span class="sxs-lookup"><span data-stu-id="34a2c-747">The callback provides the TLS session pointer and a pointer to the remote host identity certificate (the leaf in the certificate chain).</span></span> <span data-ttu-id="34a2c-748">O retorno deve voltar NX_SUCCESS se toda a validação for bem sucedida, caso contrário deverá devolver um código de erro que indique a falha de validação.</span><span class="sxs-lookup"><span data-stu-id="34a2c-748">The callback should return NX_SUCCESS if all validation is successful, otherwise it should return an error code indicating the validation failure.</span></span> <span data-ttu-id="34a2c-749">Qualquer valor que não seja NX_SUCCESS fará com que o aperto de mão TLS aborte imediatamente.</span><span class="sxs-lookup"><span data-stu-id="34a2c-749">Any value other than NX_SUCCESS will cause the TLS handshake to immediately abort.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-750">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-750">Parameters</span></span>

- <span data-ttu-id="34a2c-751">**session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-751">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-752">**func_ptr** Ponteiro para a função de retorno de validação do certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-752">**func_ptr** Pointer to the certificate validation callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-753">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-753">Return Values</span></span>

- <span data-ttu-id="34a2c-754">**NX_SUCCESS** (0x00) Atribuição bem sucedida do ponteiro função.</span><span class="sxs-lookup"><span data-stu-id="34a2c-754">**NX_SUCCESS** (0x00) Successful allocation of Function pointer.</span></span>
- <span data-ttu-id="34a2c-755">**NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-755">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-756">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-756">Allowed From</span></span>

<span data-ttu-id="34a2c-757">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-757">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-758">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-758">Example</span></span>

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
    /* Certificate validation checking goes here. */
    return(NX_SUCCESS);
}

/* In TLS setup routine. */
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                            certificate_callback);

        /* If status is NX_SUCCESS the certificate callback was added.  */
}
```

### <a name="see-also"></a><span data-ttu-id="34a2c-759">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-759">See Also</span></span>

- <span data-ttu-id="34a2c-760">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-760">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="34a2c-761">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="34a2c-761">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="34a2c-762">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="34a2c-762">nx_secure_x509_crl_revocation_check</span></span>

## <a name="nx_secure_tls_session_client_callback_set"></a><span data-ttu-id="34a2c-763">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-763">nx_secure_tls_session_client_callback_set</span></span>

<span data-ttu-id="34a2c-764">Configurar uma chamada para o TLS invocar no início de um aperto de mão do Cliente TLS</span><span class="sxs-lookup"><span data-stu-id="34a2c-764">Set up a callback for TLS to invoke at the beginning of a TLS Client handshake</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-765">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-765">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_client_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions, UINT num_extensions));
```

### <a name="description"></a><span data-ttu-id="34a2c-766">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-766">Description</span></span>

<span data-ttu-id="34a2c-767">Este serviço atribui um ponteiro de função a uma sessão de TLS que o TLS invocará quando um aperto de mão do Cliente TLS tiver recebido uma mensagem ServerHelloDone.</span><span class="sxs-lookup"><span data-stu-id="34a2c-767">This service assigns a function pointer to a TLS session that TLS will invoke when a TLS Client handshake has received a ServerHelloDone message.</span></span> <span data-ttu-id="34a2c-768">A função de retorno permite que uma aplicação processe quaisquer extensões TLS da mensagem ServerHello recebida que exijam entrada ou tomada de decisão.</span><span class="sxs-lookup"><span data-stu-id="34a2c-768">The callback function allows an application to process any TLS extensions from the received ServerHello message that require input or decision making.</span></span>

<span data-ttu-id="34a2c-769">O retorno é executado com o bloco de controlo de sessão TLS invocando e uma série de objetos NX_SECURE_TLS_HELLO_EXTENSION.</span><span class="sxs-lookup"><span data-stu-id="34a2c-769">The callback is executed with the invoking TLS session control block and an array of NX_SECURE_TLS_HELLO_EXTENSION objects.</span></span> <span data-ttu-id="34a2c-770">A matriz de objetos de extensão destina-se a ser passada para uma função auxiliar que irá encontrar e analisar uma extensão específica.</span><span class="sxs-lookup"><span data-stu-id="34a2c-770">The array of extension objects is intended to be passed into a helper function that will find and parse a specific extension.</span></span> <span data-ttu-id="34a2c-771">Atualmente, não existem extensões específicas suportadas no NetX Secure que exijam a entrada do Cliente TLS, mas o retorno está disponível para os designers de aplicações lidarem com extensões personalizadas ou novas que possam ficar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="34a2c-771">Currently, there are no specific extensions supported in NetX Secure that require TLS Client input, but the callback is available for application designers to handle custom or new extensions that may become available.</span></span> <span data-ttu-id="34a2c-772">Para uma função de ajudante de exemplo que analisa as extensões TLS fornecidas em mensagens hello, consulte *nx_secure_tls_session_sni_extension_parse*.</span><span class="sxs-lookup"><span data-stu-id="34a2c-772">For an example helper function that parses TLS extensions provided in hello messages, see *nx_secure_tls_session_sni_extension_parse*.</span></span>

<span data-ttu-id="34a2c-773">O retorno do cliente também pode ser usado para selecionar o certificado de identidade ativa usando *nx_secure_tls_ative_certificate_set* para o Cliente TLS no caso de o servidor remoto ter solicitado um certificado e fornecido informações para permitir ao Cliente TLS selecionar um certificado específico.</span><span class="sxs-lookup"><span data-stu-id="34a2c-773">The client callback may also be used to select the active identity certificate using *nx_secure_tls_active_certificate_set* for the TLS Client in the event that the remote server has requested a certificate and provided information to allow the TLS Client to select a specific certificate.</span></span> <span data-ttu-id="34a2c-774">Consulte a referência para nx_secure_tls_ative_certificate_set para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="34a2c-774">See the reference for nx_secure_tls_active_certificate_set for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-775">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-775">Parameters</span></span>

- <span data-ttu-id="34a2c-776">**session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-776">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-777">**func_ptr** Ponteiro para a função de retorno do cliente TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-777">**func_ptr** Pointer to the TLS Client callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-778">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-778">Return Values</span></span>

- <span data-ttu-id="34a2c-779">**NX_SUCCESS** (0x00) Atribuição bem sucedida do ponteiro de funções.</span><span class="sxs-lookup"><span data-stu-id="34a2c-779">**NX_SUCCESS** (0x00) Successful allocation of function pointer.</span></span>
- <span data-ttu-id="34a2c-780">**NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-780">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-781">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-781">Allowed From</span></span>

<span data-ttu-id="34a2c-782">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-782">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-783">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-783">Example</span></span>

```C
/* Callback routine used to process ServerHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the server). */

ULONG tls_client_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{

    /* Extension parsing would go here. */

    /* Set an active identity certificate – the certificate should have been added
       to the local store at application start with
       nx_secure_tls_local_certificate_add. */
    nx_secure_tls_active_certificate_set(session, &global_identity_certificate);

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
    /* Add callback to TLS session.  */
    status =  nx_secure_tls_session_client_callback_set(tls_session,
                                                        client_callback);

    /* If status is NX_SUCCESS the callback was added and will be invoked once
       a ServerHelloDone message is received. */

    return(status);
}
```

### <a name="see-also"></a><span data-ttu-id="34a2c-784">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-784">See Also</span></span>

- <span data-ttu-id="34a2c-785">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-785">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="34a2c-786">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-786">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="34a2c-787">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-787">nx_secure_tls_active_certificate_set</span></span>

## <a name="nx_secure_tls_session_x509_client_verify_configure"></a><span data-ttu-id="34a2c-788">nx_secure_tls_session_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="34a2c-788">nx_secure_tls_session_x509_client_verify_configure</span></span>

<span data-ttu-id="34a2c-789">Ativar a verificação do cliente X.509 e alocar espaço para certificados de cliente</span><span class="sxs-lookup"><span data-stu-id="34a2c-789">Enable client X.509 verification and allocate space for client certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-790">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-790">Prototype</span></span>

```C
UINT  nx_secure_tls_session_x509_client_verify_configure(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="34a2c-791">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-791">Description</span></span>

<span data-ttu-id="34a2c-792">Este serviço permite a autenticação opcional do cliente X.509 para uma instância do Servidor TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-792">This service enables the optional X.509 Client Authentication for a TLS Server instance.</span></span> <span data-ttu-id="34a2c-793">Também aloca o espaço necessário para processar as cadeias de certificados de entrada do anfitrião remoto do cliente.</span><span class="sxs-lookup"><span data-stu-id="34a2c-793">It also allocates the space needed to process incoming certificate chains from the remote client host.</span></span> <span data-ttu-id="34a2c-794">Os certificados fornecidos pelo cliente remoto serão verificados contra os certificados fidedignos do servidor TLS, atribuídos com o *serviço nx_secure_tls_trusted_certificate_add.*</span><span class="sxs-lookup"><span data-stu-id="34a2c-794">The certificates supplied by the remote client will be verified against the TLS server instance's trusted certificates, assigned with the service *nx_secure_tls_trusted_certificate_add.*</span></span>

<span data-ttu-id="34a2c-795">Para o modo cliente TLS, é necessária a atribuição de certificado remoto e o *serviço nx_secure_tls_remote_certificate_buffer_allocate* deve ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-795">For TLS Client mode, remote certificate allocation is required and the service *nx_secure_tls_remote_certificate_buffer_allocate* should be used instead.</span></span> <span data-ttu-id="34a2c-796">Ativar a autenticação do cliente X.509 numa instância do Cliente TLS não terá qualquer efeito.</span><span class="sxs-lookup"><span data-stu-id="34a2c-796">Enabling X.509 Client Authentication on a TLS Client instance will have no effect.</span></span>

<span data-ttu-id="34a2c-797">O *parâmetro certificate_buffer* aponta para o espaço atribuído para armazenar os certificados remotos de entrada e os blocos de controlo necessários para esses certificados.</span><span class="sxs-lookup"><span data-stu-id="34a2c-797">The *certificate_buffer* parameter points to space allocated to store the incoming remote certificates and the control blocks needed for those certificates.</span></span> <span data-ttu-id="34a2c-798">O tampão será dividido pelo número de certificados *(certs_number*) com uma porção igual dada a cada certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-798">The buffer will be divided by the number of certificates (*certs_number*) with an equal portion given to each certificate.</span></span> <span data-ttu-id="34a2c-799">O parâmetro *buffer_size* indica o tamanho do tampão.</span><span class="sxs-lookup"><span data-stu-id="34a2c-799">The *buffer_size* parameter indicates the size of the buffer.</span></span> <span data-ttu-id="34a2c-800">O espaço necessário pode ser encontrado com a seguinte fórmula:</span><span class="sxs-lookup"><span data-stu-id="34a2c-800">The space needed can be found with the following formula:</span></span>

```C
buffer_size = (<expected max number of certificates in chain>) *
             (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

<span data-ttu-id="34a2c-801">Os certificados típicos com teclas RSA de 2048 bits usando SHA-256 para assinaturas estão na gama de bytes 1000-2000.</span><span class="sxs-lookup"><span data-stu-id="34a2c-801">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="34a2c-802">O tampão deve ser suficientemente grande para, pelo menos, manter esse tamanho para cada certificado, mas dependendo dos certificados de anfitrião remoto podem ser significativamente menores ou maiores.</span><span class="sxs-lookup"><span data-stu-id="34a2c-802">The buffer should be large enough to at least hold that size for each certificate, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="34a2c-803">Note que se o tampão for demasiado pequeno para segurar o certificado de entrada, o aperto de mão TLS terminará com um erro.</span><span class="sxs-lookup"><span data-stu-id="34a2c-803">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-804">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-804">Parameters</span></span>

- <span data-ttu-id="34a2c-805">**session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-805">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-806">**certs_number** Número de certificados a atribuir do tampão fornecido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-806">**certs_number** Number of certificates to allocate from the provided buffer.</span></span>
- <span data-ttu-id="34a2c-807">**certificate_buffer** Ponteiro para um tampão para obter certificados recebidos de um hospedeiro remoto.</span><span class="sxs-lookup"><span data-stu-id="34a2c-807">**certificate_buffer** Pointer to a buffer to hold certificates received from a remote host.</span></span>
- <span data-ttu-id="34a2c-808">**buffer_size** Tamanho do tampão de certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-808">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-809">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-809">Return Values</span></span>

- <span data-ttu-id="34a2c-810">**NX_SUCCESS** (0x00)Atribuição bem sucedida do certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-810">**NX_SUCCESS** (0x00)Successful allocation of certificate.</span></span>
- <span data-ttu-id="34a2c-811">**NX_PTR_ERROR** (0x07) Sessão TLS inválida ou ponteiro tampão.</span><span class="sxs-lookup"><span data-stu-id="34a2c-811">**NX_PTR_ERROR** (0x07) Invalid TLS session or buffer pointer.</span></span>
- <span data-ttu-id="34a2c-812">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) O tampão fornecido era demasiado pequeno.</span><span class="sxs-lookup"><span data-stu-id="34a2c-812">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="34a2c-813">**NX_INVALID_PARAMETERS** (0x4D) O tampão era demasiado pequeno para deter o número de certificados pretendido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-813">**NX_INVALID_PARAMETERS** (0x4D) The buffer was too small to hold the desired number of certificates.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-814">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-814">Allowed From</span></span>

<span data-ttu-id="34a2c-815">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-815">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-816">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-816">Example</span></span>

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE          (CERTIFICATE_NUMBER * \
                                (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Enable X.509 Client verification and allocate certificate space in our TLS
   Server session.  */
status =  nx_secure_tls_session_x509_client_verify_configure(&tls_session,
                                                    CERTIFICATE_NUMBER,
                                                    certificate_buffer,
                                                    BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-817">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-817">See Also</span></span>

- <span data-ttu-id="34a2c-818">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-818">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-819">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-819">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="34a2c-820">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-820">nx_secure_tls_remote_certificate_buffer_allocate</span></span>

## <a name="nx_secure_tls_session_client_verify_disable"></a><span data-ttu-id="34a2c-821">nx_secure_tls_session_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="34a2c-821">nx_secure_tls_session_client_verify_disable</span></span>

<span data-ttu-id="34a2c-822">Desativar a autenticação do certificado do cliente para uma Sessão TLS Segura NetX</span><span class="sxs-lookup"><span data-stu-id="34a2c-822">Disable Client Certificate Authentication for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-823">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-823">Prototype</span></span>

```C
UINT  nx_secure_tls_session_client_verify_disable(
                              NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="34a2c-824">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-824">Description</span></span>

<span data-ttu-id="34a2c-825">Este serviço desativa a autenticação do Certificado de Cliente para uma sessão específica de TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-825">This service disables Client Certificate Authentication for a specific TLS session.</span></span> <span data-ttu-id="34a2c-826">Consulte nx_secure_tls_session_client_verify_enable para mais informações.</span><span class="sxs-lookup"><span data-stu-id="34a2c-826">See nx_secure_tls_session_client_verify_enable for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-827">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-827">Parameters</span></span>

- <span data-ttu-id="34a2c-828">**session_ptr** Ponteiro para uma sessão de TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-828">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-829">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-829">Return Values</span></span>

- <span data-ttu-id="34a2c-830">**NX_SUCCESS** (0x00) Mudança de estado bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="34a2c-830">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="34a2c-831">**NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-831">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-832">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-832">Allowed From</span></span>

<span data-ttu-id="34a2c-833">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-833">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-834">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-834">Example</span></span>

```C
/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_disable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will not
request certificates from the remote TLS client.  */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-835">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-835">See Also</span></span>

- <span data-ttu-id="34a2c-836">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="34a2c-836">nx_secure_tls_session_client_verify_enable</span></span>
- <span data-ttu-id="34a2c-837">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="34a2c-837">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="34a2c-838">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-838">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_client_verify_enable"></a><span data-ttu-id="34a2c-839">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="34a2c-839">nx_secure_tls_session_client_verify_enable</span></span>

<span data-ttu-id="34a2c-840">Ativar a autenticação do certificado de cliente para uma Sessão TLS Segura NetX</span><span class="sxs-lookup"><span data-stu-id="34a2c-840">Enable Client Certificate Authentication for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-841">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-841">Prototype</span></span>

```C
UINT  nx_secure_tls_session_client_verify_enable(
                                NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="34a2c-842">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-842">Description</span></span>

<span data-ttu-id="34a2c-843">Este serviço permite a autenticação do Certificado de Cliente para uma sessão específica de TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-843">This service enables Client Certificate Authentication for a specific TLS session.</span></span> <span data-ttu-id="34a2c-844">Permitir a autenticação do certificado de cliente para uma instância do Servidor TLS fará com que o Servidor TLS solicite um certificado a qualquer Cliente TLS remoto durante o aperto de mão TLS inicial.</span><span class="sxs-lookup"><span data-stu-id="34a2c-844">Enabling Client Certificate Authentication for a TLS Server instance will cause the TLS Server to request a certificate from any remote TLS Client during the initial TLS handshake.</span></span> <span data-ttu-id="34a2c-845">O certificado recebido do cliente TLS remoto é acompanhado por uma mensagem CertificateVerify, que o Servidor TLS utiliza para verificar se o Cliente é dono do certificado (tem acesso à chave privada associada a esse certificado).</span><span class="sxs-lookup"><span data-stu-id="34a2c-845">The certificate received from the remote TLS Client is accompanied by a CertificateVerify message, which the TLS Server uses to verify that the Client owns the certificate (has access to the private key associated with that certificate).</span></span>

<span data-ttu-id="34a2c-846">Se o certificado fornecido puder ser verificado e rastreado até um certificado na loja de certificados fidedignos do TLS Server através de uma cadeia de certificados X.509, o cliente TLS remoto é autenticado e o aperto de mão prossegue.</span><span class="sxs-lookup"><span data-stu-id="34a2c-846">If the provided certificate can be verified and traced back to a certificate in the TLS Server trusted certificate store via an X.509 certificate chain, the remote TLS Client is authenticated and the handshake proceeds.</span></span> <span data-ttu-id="34a2c-847">Em caso de erros no processamento do certificado ou mensagem CertificateVerify, o aperto de mão TLS termina com um erro.</span><span class="sxs-lookup"><span data-stu-id="34a2c-847">In case of any errors in processing the certificate or CertificateVerify message, the TLS handshake ends with an error.</span></span>

> [!NOTE]
> <span data-ttu-id="34a2c-848">*O Servidor TLS deve ter pelo menos um certificado na sua loja de confiança adicionado com nx_secure_tls_trusted_certificate_add ou autenticação falhará sempre.*</span><span class="sxs-lookup"><span data-stu-id="34a2c-848">*The TLS Server must have at least one certificate in its trusted store added with nx_secure_tls_trusted_certificate_add or authentication will always fail.*</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-849">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-849">Parameters</span></span>

- <span data-ttu-id="34a2c-850">**session_ptr** Ponteiro para uma sessão de TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-850">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-851">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-851">Return Values</span></span>

- <span data-ttu-id="34a2c-852">**NX_SUCCESS** (0x00) Mudança de estado bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="34a2c-852">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="34a2c-853">**NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-853">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-854">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-854">Allowed From</span></span>

<span data-ttu-id="34a2c-855">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-855">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-856">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-856">Example</span></span>

```C
/* Add a trusted certificate so the TLS Server has something to verify against. */
status = nx_secure_tls_trusted_certificate_add(&tls_session,
                                               &trusted_certificate);

/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_enable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will now
request and verify certificates from the remote TLS client.  */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-857">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-857">See Also</span></span>

- <span data-ttu-id="34a2c-858">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="34a2c-858">nx_secure_tls_session_client_verify_enable</span></span>
- <span data-ttu-id="34a2c-859">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="34a2c-859">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="34a2c-860">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-860">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="34a2c-861">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-861">nx_secure_tls_trusted_certificate_add</span></span>

## <a name="nx_secure_tls_session_create"></a><span data-ttu-id="34a2c-862">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-862">nx_secure_tls_session_create</span></span>

<span data-ttu-id="34a2c-863">Criar uma Sessão TLS Segura NetX para comunicações seguras</span><span class="sxs-lookup"><span data-stu-id="34a2c-863">Create a NetX Secure TLS Session for secure communications</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-864">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-864">Prototype</span></span>

```C
UINT  nx_secure_tls_session_create(NX_SECURE_TLS_SESSION *session_ptr
                                   NX_SECURE_TLS_CRYPTO *cipher_table,
                                   VOID *encryption_metadata_area,
                                   ULONG encryption_metadata_size);
```

### <a name="description"></a><span data-ttu-id="34a2c-865">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-865">Description</span></span>

<span data-ttu-id="34a2c-866">Este serviço inicializa uma NX_SECURE_TLS_SESSION exemplo de estrutura para utilização no estabelecimento de comunicações TLS seguras sobre uma ligação de rede.</span><span class="sxs-lookup"><span data-stu-id="34a2c-866">This service initializes an NX_SECURE_TLS_SESSION structure instance for use in establishing secure TLS communications over a network connection.</span></span>

<span data-ttu-id="34a2c-867">O método requer um objeto NX_SECURE_TLS_CRYPTO que é povoado com os métodos criptográficos disponíveis para ser usado para TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-867">The method takes a NX_SECURE_TLS_CRYPTO object that is populated with the available cryptographic methods to be used for TLS.</span></span> <span data-ttu-id="34a2c-868">O *encryption_metadata_area* aponta para um tampão atribuído para utilização pelo TLS para os "metadados" utilizados pelos métodos criptográficos na tabela NX_SECURE_TLS_CRYPTO para cálculos.</span><span class="sxs-lookup"><span data-stu-id="34a2c-868">The *encryption_metadata_area* points to a buffer allocated for use by TLS for the "metadata" used by the cryptographic methods in the NX_SECURE_TLS_CRYPTO table for calculations.</span></span> <span data-ttu-id="34a2c-869">O tamanho da tabela pode ser determinado utilizando o serviço nx_secure_tls_metadata_size_calculate.</span><span class="sxs-lookup"><span data-stu-id="34a2c-869">The size of the table can be determined by using the nx_secure_tls_metadata_size_calculate service.</span></span> <span data-ttu-id="34a2c-870">Consulte a secção "Criptografia em NetX Secure TLS" no Capítulo 3 para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="34a2c-870">See the section "Cryptography in NetX Secure TLS" in Chapter 3 for more details.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-871">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-871">Parameters</span></span>

- <span data-ttu-id="34a2c-872">**session_ptr** Ponteiro para uma sessão de TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-872">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-873">**cipher_table** Ponteiro para métodos criptográficos TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-873">**cipher_table** Pointer to TLS cryptographic methods.</span></span>
- <span data-ttu-id="34a2c-874">**encryption_metadata_area** Ponteiro para o espaço para metadados de criptografia.</span><span class="sxs-lookup"><span data-stu-id="34a2c-874">**encryption_metadata_area** Pointer to space for cryptography metadata.</span></span>
- <span data-ttu-id="34a2c-875">**encryption_metadata_size** Tamanho do tampão de metadados.</span><span class="sxs-lookup"><span data-stu-id="34a2c-875">**encryption_metadata_size** Size of the metadata buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-876">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-876">Return Values</span></span>

- <span data-ttu-id="34a2c-877">**NX_SUCCESS** (0x00)Iniciação bem sucedida da sessão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-877">**NX_SUCCESS** (0x00)Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="34a2c-878">**NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-878">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="34a2c-879">**NX_INVALID_PARAMETERS** (0x4D) O tampão de metadados era demasiado pequeno para os métodos dados.</span><span class="sxs-lookup"><span data-stu-id="34a2c-879">**NX_INVALID_PARAMETERS** (0x4D) The metadata buffer was too small for the given methods.</span></span>
- <span data-ttu-id="34a2c-880">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) Não foi fornecido na tabela de cifras um método de cifra necessário para a versão ativada do STS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-880">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A required cipher method for the enabled version of TLS was not supplied in the cipher table.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-881">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-881">Allowed From</span></span>

<span data-ttu-id="34a2c-882">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-882">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-883">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-883">Example</span></span>

```C
/* Reference the platform-specific TLS cryptographic method table. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;

/* Declare a buffer for the cryptographic metadata. The size should be calculated
   using nx_secure_tls_metadata_size_calculate. */
UCHAR crypto_metadata[4500];

/* Initialize TLS session.  */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* If status is NX_SUCCESS the TLS Session was successfully initialized.  */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-884">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-884">See Also</span></span>

- <span data-ttu-id="34a2c-885">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-885">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-886">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="34a2c-886">nx_secure_tls_metadata_size_calculate</span></span>
- <span data-ttu-id="34a2c-887">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-887">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="34a2c-888">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="34a2c-888">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="34a2c-889">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="34a2c-889">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="34a2c-890">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="34a2c-890">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="34a2c-891">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="34a2c-891">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="34a2c-892">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="34a2c-892">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="34a2c-893">Criptografia em NetX Secure TLS no Capítulo 3</span><span class="sxs-lookup"><span data-stu-id="34a2c-893">Cryptography in NetX Secure TLS in Chapter 3</span></span>

## <a name="nx_secure_tls_session_delete"></a><span data-ttu-id="34a2c-894">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="34a2c-894">nx_secure_tls_session_delete</span></span>

<span data-ttu-id="34a2c-895">Excluir uma Sessão de TLS Segura NetX</span><span class="sxs-lookup"><span data-stu-id="34a2c-895">Delete a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-896">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-896">Prototype</span></span>

```C
UINT  nx_secure_tls_session_delete(NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="34a2c-897">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-897">Description</span></span>

<span data-ttu-id="34a2c-898">Este serviço elimina uma sessão TLS representada por uma instância de estrutura NX_SECURE_TLS_SESSION e liberta todos os recursos do sistema detidos por essa instância de sessão.</span><span class="sxs-lookup"><span data-stu-id="34a2c-898">This service deletes a TLS session represented by an NX_SECURE_TLS_SESSION structure instance and releases all system resources owned by that session instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-899">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-899">Parameters</span></span>

- <span data-ttu-id="34a2c-900">**session_ptr** Ponteiro para uma sessão de TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-900">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-901">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-901">Return Values</span></span>

- <span data-ttu-id="34a2c-902">**NX_SUCCESS** (0x00) Iniciação bem sucedida da sessão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-902">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="34a2c-903">**NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-903">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-904">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-904">Allowed From</span></span>

<span data-ttu-id="34a2c-905">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-905">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-906">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-906">Example</span></span>

```C
/* Delete TLS session.  */
status =  nx_secure_tls_session_delete(&tls_session);


/* If status is NX_SUCCESS the TLS Session was successfully deleted.  */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-907">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-907">See Also</span></span>

- <span data-ttu-id="34a2c-908">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-908">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-909">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-909">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="34a2c-910">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="34a2c-910">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="34a2c-911">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="34a2c-911">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="34a2c-912">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="34a2c-912">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="34a2c-913">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="34a2c-913">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="34a2c-914">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-914">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_end"></a><span data-ttu-id="34a2c-915">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="34a2c-915">nx_secure_tls_session_end</span></span>

<span data-ttu-id="34a2c-916">Termine uma sessão ativa de TLS Do NetX Secure</span><span class="sxs-lookup"><span data-stu-id="34a2c-916">End an active NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-917">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-917">Prototype</span></span>

```C
UINT  nx_secure_tls_session_end(NX_SECURE_TLS_SESSION *session_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34a2c-918">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-918">Description</span></span>

<span data-ttu-id="34a2c-919">Este serviço termina uma sessão TLS representada por uma NX_SECURE_TLS_SESSION instância de estrutura enviando a mensagem TLS CloseNotify para o anfitrião remoto.</span><span class="sxs-lookup"><span data-stu-id="34a2c-919">This service ends a TLS session represented by an NX_SECURE_TLS_SESSION structure instance by sending the TLS CloseNotify message to the remote host.</span></span> <span data-ttu-id="34a2c-920">Em seguida, o serviço aguarda que o anfitrião remoto responda com a sua própria mensagem CloseNotify.</span><span class="sxs-lookup"><span data-stu-id="34a2c-920">The service then waits for the remote host to respond with its own CloseNotify message.</span></span>

<span data-ttu-id="34a2c-921">Se o anfitrião remoto não enviar uma mensagem CloseNotify, o TLS considera que se trata de um erro e de uma possível falha de segurança, pelo que verificar o valor de devolução é importante para uma ligação segura.</span><span class="sxs-lookup"><span data-stu-id="34a2c-921">If the remote host does not send a CloseNotify message, TLS considers this an error and a possible security breach, so checking the return value is important for a secure connection.</span></span> <span data-ttu-id="34a2c-922">O **parâmetro wait_option** pode ser utilizado para controlar quanto tempo o serviço deve esperar pela resposta antes de devolver o controlo ao fio de chamada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-922">The **wait_option** parameter can be used to control how long the service should wait for the response before returning control to the calling thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-923">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-923">Parameters</span></span>

- <span data-ttu-id="34a2c-924">**session_ptr** Ponteiro para uma sessão de TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-924">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-925">**wait_option** Indica quanto tempo o serviço deve esperar pela resposta do hospedeiro remoto.</span><span class="sxs-lookup"><span data-stu-id="34a2c-925">**wait_option** Indicates how long the service should wait for the response from the remote host.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-926">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-926">Return Values</span></span>

- <span data-ttu-id="34a2c-927">**NX_SUCCESS** (0x00) Iniciação bem sucedida da sessão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-927">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="34a2c-928">**NX_SECURE_TLS_NO_CLOSE_RESPONSE** (0x113) não recebeu uma resposta do anfitrião remoto antes do tempo de 200.</span><span class="sxs-lookup"><span data-stu-id="34a2c-928">**NX_SECURE_TLS_NO_CLOSE_RESPONSE** (0x113) Did not receive a response from the remote host before timing out.</span></span>
- <span data-ttu-id="34a2c-929">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Não poderia atribuir um pacote para enviar a mensagem CloseNotify.</span><span class="sxs-lookup"><span data-stu-id="34a2c-929">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate a packet to send the CloseNotify message.</span></span>
- <span data-ttu-id="34a2c-930">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Não foi possível enviar a mensagem CloseNotify sobre a tomada TCP.</span><span class="sxs-lookup"><span data-stu-id="34a2c-930">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Could not send the CloseNotify message over the TCP socket.</span></span>
- <span data-ttu-id="34a2c-931">**NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-931">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-932">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-932">Allowed From</span></span>

<span data-ttu-id="34a2c-933">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-933">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-934">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-934">Example</span></span>

```C
/* End TLS session.  */
status =  nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the TLS Session was successfully ended.  */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-935">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-935">See Also</span></span>

- <span data-ttu-id="34a2c-936">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-936">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-937">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-937">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="34a2c-938">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="34a2c-938">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="34a2c-939">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="34a2c-939">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="34a2c-940">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="34a2c-940">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="34a2c-941">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="34a2c-941">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="34a2c-942">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-942">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_packet_buffer_set"></a><span data-ttu-id="34a2c-943">nx_secure_tls_session_packet_buffer_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-943">nx_secure_tls_session_packet_buffer_set</span></span>

<span data-ttu-id="34a2c-944">Descreva o tampão de montagem do pacote para uma Sessão TLS NetX Secure</span><span class="sxs-lookup"><span data-stu-id="34a2c-944">Set the packet reassembly buffer for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-945">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-945">Prototype</span></span>

```C
UINT  nx_secure_tls_session_packet_buffer_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *buffer_ptr,
                                    ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="34a2c-946">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-946">Description</span></span>

<span data-ttu-id="34a2c-947">Este serviço associa um tampão de remontagem de pacote a uma sessão de TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-947">This service associates a packet reassembly buffer to a TLS session.</span></span> <span data-ttu-id="34a2c-948">Para desencriptar e analisar os registos TLS de entrada, os dados em cada registo devem ser reunidos a partir dos pacotes TCP subjacentes.</span><span class="sxs-lookup"><span data-stu-id="34a2c-948">In order to decrypt and parse incoming TLS records, the data in each record must be assembled from the underlying TCP packets.</span></span> <span data-ttu-id="34a2c-949">Os registos TLS podem ter até 16KB de tamanho (embora normalmente sejam muito menores) pelo que podem não caber num único pacote TCP.</span><span class="sxs-lookup"><span data-stu-id="34a2c-949">TLS records can be up to 16KB in size (though typically are much smaller) so may not fit into a single TCP packet.</span></span>

<span data-ttu-id="34a2c-950">Se souber que o tamanho da mensagem de entrada será menor do que o limite de registo TLS de 16KB, o tamanho do tampão pode ser menor, mas para lidar com dados de entrada desconhecidos, o tampão deve ser feito o maior possível.</span><span class="sxs-lookup"><span data-stu-id="34a2c-950">If you know the incoming message size will be smaller than the TLS record limit of 16KB, the buffer size can be made smaller, but in order to handle unknown incoming data the buffer should be made as large as possible.</span></span> <span data-ttu-id="34a2c-951">Se um registo de entrada for maior do que o tampão fornecido, a sessão TLS terminará com um erro.</span><span class="sxs-lookup"><span data-stu-id="34a2c-951">If an incoming record is larger than the supplied buffer, the TLS session will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-952">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-952">Parameters</span></span>

- <span data-ttu-id="34a2c-953">**session_ptr** Ponteiro para uma sessão de TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-953">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-954">**buffer_ptr** Ponteiro para tampão para TLS para utilizar para remontagem de pacotes.</span><span class="sxs-lookup"><span data-stu-id="34a2c-954">**buffer_ptr** Pointer to buffer for TLS to use for packet reassembly.</span></span>
- <span data-ttu-id="34a2c-955">**buffer_size** Tamanho do tampão fornecido em bytes.</span><span class="sxs-lookup"><span data-stu-id="34a2c-955">**buffer_size** Size of the supplied buffer in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-956">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-956">Return Values</span></span>

- <span data-ttu-id="34a2c-957">**NX_SUCCESS** (0x00) Iniciação bem sucedida da sessão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-957">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="34a2c-958">**NX_INVALID_PARAMETERS** (0x4D) Tampão inválido ou ponteiro de sessão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-958">**NX_INVALID_PARAMETERS** (0x4D) Invalid buffer or TLS session pointer.</span></span>
- <span data-ttu-id="34a2c-959">**NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-959">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-960">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-960">Allowed From</span></span>

<span data-ttu-id="34a2c-961">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-961">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-962">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-962">Example</span></span>

```C
/* Buffer for TLS packet reassembly. */
UCHAR tls_packet_buffer[16384];
/* Assign buffer to TLS session.  */
status =  nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                  sizeof(tls_packet_buffer));


/* If status is NX_SUCCESS the buffer was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-963">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-963">See Also</span></span>

- <span data-ttu-id="34a2c-964">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-964">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-965">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-965">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="34a2c-966">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="34a2c-966">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="34a2c-967">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="34a2c-967">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="34a2c-968">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="34a2c-968">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="34a2c-969">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="34a2c-969">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="34a2c-970">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-970">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_protocol_version_override"></a><span data-ttu-id="34a2c-971">nx_secure_tls_session_protocol_version_override</span><span class="sxs-lookup"><span data-stu-id="34a2c-971">nx_secure_tls_session_protocol_version_override</span></span>

<span data-ttu-id="34a2c-972">Anular a versão padrão do protocolo TLS para uma Sessão De TLS Do NetX Secure</span><span class="sxs-lookup"><span data-stu-id="34a2c-972">Override the default TLS protocol version for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-973">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-973">Prototype</span></span>

```C
UINT  nx_secure_tls_session_protocol_version_override(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              USHORT protocol_version);
```

### <a name="description"></a><span data-ttu-id="34a2c-974">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-974">Description</span></span>

<span data-ttu-id="34a2c-975">Este serviço substitui a versão padrão (mais recente) do protocolo TLS utilizada por uma determinada sessão.</span><span class="sxs-lookup"><span data-stu-id="34a2c-975">This service overrides the default (newest) TLS protocol version used by a particular session.</span></span> <span data-ttu-id="34a2c-976">Isto permite ao NetX Secure TLS utilizar uma versão mais antiga do TLS para uma Sessão TLS específica sem desativar as versões TLS mais recentes no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="34a2c-976">This enables NetX Secure TLS to use an older version of TLS for a specific TLS Session without disabling newer TLS versions at compile time.</span></span> <span data-ttu-id="34a2c-977">Isto pode ser útil em aplicações que possam necessitar de comunicar com um anfitrião mais antigo que não suporte a versão mais recente do TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-977">This may be useful in applications that may need to communicate with an older host that does not support the newest version of TLS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34a2c-978">*A partir da versão 5.11SP3, o NetX Secure TLS suporta o RFC 7507 (ver nota abaixo) e qualquer substituição a uma versão mais antiga com esta API resultará no envio de um SCSV de recuo no ClientHello. Se o servidor suportar uma versão mais recente do TLS e o SCSV de retorno de retorno estiver incluído no ClientHello, esse servidor abortará o aperto de mão TLS com um alerta de "Fallback Inadequado". O SCSV só é enviado quando a versão é uma versão mais antiga do TLS do que está ativada (por exemplo, se substituir a versão para TLS 1.2, não será enviado nenhum SCSV).*</span><span class="sxs-lookup"><span data-stu-id="34a2c-978">*As of version 5.11SP3, NetX Secure TLS supports RFC 7507 (see note below) and any override to an older version with this API will result in a fallback SCSV being sent in the ClientHello. If the server supports a newer version of TLS and the fallback SCSV is included in the ClientHello, that server will abort the TLS handshake with an "Inappropriate Fallback" alert. The SCSV is only sent when the version override is an older version of TLS than is enabled (e.g. if you override the version to TLS 1.2, no SCSV will be sent).*</span></span>

<span data-ttu-id="34a2c-979">Os valores válidos para o parâmetro protocol_version são as seguintes macros: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1 e NX_SECURE_TLS_VERSION_TLS_1_2.</span><span class="sxs-lookup"><span data-stu-id="34a2c-979">Valid values for the protocol_version parameter are the following macros: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1, and NX_SECURE_TLS_VERSION_TLS_1_2.</span></span>

<span data-ttu-id="34a2c-980">As macros NX_SECURE_TLS_DISABLE_TLS_1_1 e NX_SECURE_TLS_ENABLE_TLS_1_0 podem ser usadas para controlar as versões de TLS que são compiladas na aplicação.</span><span class="sxs-lookup"><span data-stu-id="34a2c-980">The macros NX_SECURE_TLS_DISABLE_TLS_1_1 and NX_SECURE_TLS_ENABLE_TLS_1_0 can be used to control the versions of TLS that are compiled into the application.</span></span> <span data-ttu-id="34a2c-981">A versão 1.2 do TLS está sempre ativada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-981">TLS version 1.2 is always enabled.</span></span>

<span data-ttu-id="34a2c-982">De notar que se o anfitrião remoto não suportar a versão fornecida, a ligação falhará – apenas a versão de substituição fornecida será negociada pelo NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-982">Note that if the remote host does not support the supplied version, the connection will fail – only the supplied override version will be negotiated by NetX Secure TLS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34a2c-983">RFC 7507: TLS Fallback SCSV.</span><span class="sxs-lookup"><span data-stu-id="34a2c-983">RFC 7507: TLS Fallback SCSV.</span></span> <span data-ttu-id="34a2c-984">Este RFC foi introduzido para mitigar um problema de segurança que foi originalmente causado por servidores que manuseavam indevidamente a negociação de downgrade de protocolos e, em vez disso, rejeitaram mensagens De acordo com o ClientHello válidas.</span><span class="sxs-lookup"><span data-stu-id="34a2c-984">This RFC was introduced to mitigate a security problem that was originally caused by servers that improperly handled protocol downgrade negotiation and instead rejected otherwise valid ClientHello messages.</span></span> <span data-ttu-id="34a2c-985">Numa tentativa de se manterem compatíveis com estes antigos servidores, algumas aplicações de clientes TLS começaram a voltar a tentar apertos de mão falhados com a versão TLS mais antiga (por exemplo, TLS 1.2 falhou por isso experimente o TLS 1.1).</span><span class="sxs-lookup"><span data-stu-id="34a2c-985">In an attempt to remain compatible with these old servers, some TLS client applications started to retry failed handshakes with and older TLS version (e.g. TLS 1.2 failed so try TLS 1.1).</span></span> <span data-ttu-id="34a2c-986">No entanto, esta solução introduziu um novo problema – um intruso poderia forçar um cliente a desvalorizar introduzindo artificialmente um erro de rede ou pacote que fez com que a ligação do servidor falhasse – mesmo quando o servidor suportava a versão TLS mais recente.</span><span class="sxs-lookup"><span data-stu-id="34a2c-986">This workaround however introduced a new problem – an attacker could force a client to downgrade by artificially introducing a network or packet error causing the server connection to fail – even when the server supported the newer TLS version.</span></span> <span data-ttu-id="34a2c-987">Ao reduzir para uma versão mais antiga, o intruso poderia explorar fraquezas nessa versão (o SSLv3<sup>21</sup> em particular é fraco para o ataque do POODLE).</span><span class="sxs-lookup"><span data-stu-id="34a2c-987">By downgrading to an older version the attacker could exploit weaknesses in that version (SSLv3<sup>21</sup> in particular is weak to the POODLE attack).</span></span> <span data-ttu-id="34a2c-988">Para evitar esta situação, o RFC 7507 intrometia o "BACKSV de recuo", um pseudo-cifrassuite<sup>22</sup> enviado no ClientHello que notifica um servidor TLS quando um cliente TLS está a usar uma versão TLS que não é a versão mais recente que suporta.</span><span class="sxs-lookup"><span data-stu-id="34a2c-988">To prevent this situation, RFC 7507 introdued the "fallback SCSV," a pseudo-ciphersuite<sup>22</sup> sent in the ClientHello that notifies a TLS server when a TLS client is using a TLS version that is not the newest version it supports.</span></span> <span data-ttu-id="34a2c-989">Desta forma, um servidor que suporte uma versão mais recente pode rejeitar um ClientHello contendo o SCSV de retorno e impedir que o ataque de downgrade seja bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-989">This way, a server that supports a newer version can reject a ClientHello containing the fallback SCSV and prevent the downgrade attack from succeeding.</span></span>

21. <span data-ttu-id="34a2c-990">O NetX Secure não implementa o SSLv3 devido à existência de fraquezas graves conhecidas, como o POODLE.</span><span class="sxs-lookup"><span data-stu-id="34a2c-990">NetX Secure does not implement SSLv3 due to the existence of known serious weaknesses such as POODLE.</span></span>

22. <span data-ttu-id="34a2c-991">Um pseudo-cifrasuite, ou SCSV (Signaling Cipher Suite Value), é um número de cifrasuite reservado que é usado para sinalizar implementações de TLS ativadas sobre funcionalidades que não estavam disponíveis em versões TLS mais antigas.</span><span class="sxs-lookup"><span data-stu-id="34a2c-991">A pseudo-ciphersuite, or SCSV (Signaling Cipher Suite Value), is a reserved ciphersuite number that is used to signal enabled TLS implementations about features that were not available in older TLS versions.</span></span> <span data-ttu-id="34a2c-992">O recuo SCSV e o TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746) são exemplos.</span><span class="sxs-lookup"><span data-stu-id="34a2c-992">The fallback SCSV and the TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746) are examples.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-993">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-993">Parameters</span></span>

- <span data-ttu-id="34a2c-994">**session_ptr** Ponteiro para uma sessão de TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-994">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-995">**protocol_version** Macro de versão TLS para a versão específica TLS a utilizar.</span><span class="sxs-lookup"><span data-stu-id="34a2c-995">**protocol_version** TLS version macro for the specific TLS version to use.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-996">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-996">Return Values</span></span>

- <span data-ttu-id="34a2c-997">**NX_SUCCESS** (0x00) Mudança de estado bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="34a2c-997">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="34a2c-998">**NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-998">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="34a2c-999">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Versão TLS conhecida mas não suportada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-999">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Known but unsupported TLS version.</span></span>
- <span data-ttu-id="34a2c-1000">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Versão do protocolo inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1000">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Invalid protocol version.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-1001">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-1001">Allowed From</span></span>

<span data-ttu-id="34a2c-1002">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-1002">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-1003">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-1003">Example</span></span>

```C
/* Set the protocol version to be used to TLSv1.1. */
status = nx_secure_tls_session_protocol_version_override(&tls_session,
                                              NX_SECURE_TLS_VERSION_TLS_1_1);

/* This TLS Session will use TLSv1.1 for the handshake and TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);
```

### <a name="see-also"></a><span data-ttu-id="34a2c-1004">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-1004">See Also</span></span>

- <span data-ttu-id="34a2c-1005">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="34a2c-1005">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="34a2c-1006">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-1006">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_receive"></a><span data-ttu-id="34a2c-1007">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="34a2c-1007">nx_secure_tls_session_receive</span></span>

<span data-ttu-id="34a2c-1008">Receber dados de uma Sessão De TLS Segura NetX</span><span class="sxs-lookup"><span data-stu-id="34a2c-1008">Receive data from a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-1009">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-1009">Prototype</span></span>

```C
UINT  nx_secure_tls_session_receive(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34a2c-1010">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-1010">Description</span></span>

<span data-ttu-id="34a2c-1011">Este serviço recebe dados da sessão de TLS ativa especificada, manuseando a desencriptação desses dados antes de os fornecer ao chamador no parâmetro NX_PACKET.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1011">This service receives data from the specified active TLS session, handling the decryption of that data before providing it to the caller in the NX_PACKET parameter.</span></span> <span data-ttu-id="34a2c-1012">Se não houver dados na sessão especificada, a chamada suspende com base na opção de espera fornecida.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1012">If no data is queued in the specified session, the call suspends based on the supplied wait option.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34a2c-1013">*Se NX_SUCCESS for devolvido, o pedido é responsável pela libertação do pacote recebido quando já não for necessário.*</span><span class="sxs-lookup"><span data-stu-id="34a2c-1013">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-1014">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-1014">Parameters</span></span>

- <span data-ttu-id="34a2c-1015">**session_ptr** Ponteiro para uma sessão de TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1015">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-1016">**packet_ptr** Ponteiro para um ponteiro de pacote TLS atribuído.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1016">**packet_ptr** Pointer to an allocated TLS packet pointer.</span></span>
- <span data-ttu-id="34a2c-1017">**wait_option** Indica quanto tempo o serviço deve esperar por um pacote do anfitrião remoto antes de regressar.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1017">**wait_option** Indicates how long the service should wait for a packet from the remote host before returning.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-1018">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-1018">Return Values</span></span>

- <span data-ttu-id="34a2c-1019">**NX_SUCCESS** (0x00) Iniciação bem sucedida da sessão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1019">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="34a2c-1020">**NX_NO_PACKET** (0x01) Nenhum dado recebido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1020">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="34a2c-1021">**NX_NOT_CONNECTED** (0x38) A tomada TCP subjacente já não está ligada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1021">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="34a2c-1022">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Uma mensagem recebida falhou num cheque de haxixe de autenticação.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1022">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A received message failed an authentication hash check.</span></span>
- <span data-ttu-id="34a2c-1023">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Uma mensagem recebida continha uma versão de protocolo desconhecida no seu cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1023">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received message contained an unknown protocol version in its header.</span></span>
- <span data-ttu-id="34a2c-1024">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Recebeu um alerta TLS do hospedeiro remoto.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1024">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Received a TLS alert from the remote host.</span></span>
- <span data-ttu-id="34a2c-1025">**NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1025">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="34a2c-1026">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) A sessão TLS fornecida não foi inicializada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1026">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-1027">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-1027">Allowed From</span></span>

<span data-ttu-id="34a2c-1028">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-1028">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-1029">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-1029">Example</span></span>

```C
/* Receive a packet from an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is received, blocking otherwise.
*/
status =  nx_secure_tls_session_receive(&tls_session, &packet_ptr,
NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the received packet is pointed to by  "packet_ptr". */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-1030">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-1030">See Also</span></span>

- <span data-ttu-id="34a2c-1031">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="34a2c-1031">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="34a2c-1032">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-1032">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-1033">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-1033">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="34a2c-1034">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="34a2c-1034">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="34a2c-1035">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="34a2c-1035">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="34a2c-1036">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="34a2c-1036">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="34a2c-1037">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="34a2c-1037">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="34a2c-1038">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-1038">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_renegotiate_callback_set"></a><span data-ttu-id="34a2c-1039">nx_secure_tls_session_renegotiate_callback_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-1039">nx_secure_tls_session_renegotiate_callback_set</span></span>

<span data-ttu-id="34a2c-1040">Atribua uma chamada que será invocada no início de uma renegociação da sessão</span><span class="sxs-lookup"><span data-stu-id="34a2c-1040">Assign a callback that will be invoked at the beginning of a session renegotiation</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-1041">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-1041">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_renegotiate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(struct NX_SECURE_TLS_SESSION_struct
                  *session));
```

### <a name="description"></a><span data-ttu-id="34a2c-1042">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-1042">Description</span></span>

<span data-ttu-id="34a2c-1043">Este serviço atribui uma chamada de volta a uma sessão TLS que será invocada sempre que a primeira mensagem de um aperto de mão de renegociação de sessão for recebida do anfitrião remoto.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1043">This service assigns a callback to a TLS session that will be invoked whenever the first message of a session renegotiation handshake is received from the remote host.</span></span>

<span data-ttu-id="34a2c-1044">A função de retorno destina-se a uma notificação à aplicação de que está a iniciar um aperto de mão de renegociação – a aplicação pode optar por encerrar a sessão TLS devolvendo qualquer valor não nulo da chamada que fará com que a TLS termine a sessão de TLS com um erro.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1044">The callback function is intended as a notification to the application that a renegotiation handshake is beginning – the application may choose to terminate the TLS session by returning any non-zero value from the callback which will cause TLS to end the TLS session with an error.</span></span> <span data-ttu-id="34a2c-1045">Se o pedido pretender prosseguir com a renegociação, o retorno deve voltar NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1045">If the application wishes to proceed with the renegotiation, the callback should return NX_SUCCESS.</span></span>

> [!NOTE]
> <span data-ttu-id="34a2c-1046">*Devido à semântica da renegociação do TLS, a chamada será invocada para os Clientes NetX Secure TLS sempre que um HelloRequest for recebido do servidor remoto, mas não quando o cliente iniciar a renegociação. Nos Servidores TLS Do NetX Secure, a chamada será invocada sempre que for recebida uma renegociação do ClientHello (qualquer ClientHello recebido no contexto de uma sessão de TLS ativa). Isto significa que a chamada será invocada se o anfitrião remoto ou a aplicação local iniciaram a renegociação porque o servidor TLS enviará um HelloRequest ao qual o cliente remoto responderá.*</span><span class="sxs-lookup"><span data-stu-id="34a2c-1046">*Due to the semantics of TLS renegotiation, the callback will be invoked for NetX Secure TLS Clients whenever a HelloRequest is received from the remote server, but not when the client initiates the renegotiation. On NetX Secure TLS Servers, the callback will be invoked whenever a renegotiation ClientHello is received (any ClientHello received in the context of an active TLS session). This means that the callback will be invoked whether the remote host or the local application has initiated the renegotiation because the TLS server will send a HelloRequest to which the remote client will respond.*</span></span>

<span data-ttu-id="34a2c-1047">NetX Secure TLS implementa a Extensão de Insidição de Renegociação Segura do RFC 5746 para garantir que os apertos de mão de renegociação não estão sujeitos a ataques man-in-the-middle.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1047">NetX Secure TLS implements the Secure Renegotiation Inidication Extension from RFC 5746 to ensure that renegotiation handshakes are not subject to man-in-the-middle attacks.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-1048">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-1048">Parameters</span></span>

- <span data-ttu-id="34a2c-1049">**session_ptr** Ponteiro para a sessão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1049">**session_ptr** Pointer to TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-1050">**func_ptr** Ponteiro para a função de retorno de chamadas.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1050">**func_ptr** Pointer to callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-1051">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-1051">Return Values</span></span>

- <span data-ttu-id="34a2c-1052">**NX_SUCCESS** (0x00) Atribuição bem sucedida de chamadas.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1052">**NX_SUCCESS** (0x00) Successful assignment of callback.</span></span>
- <span data-ttu-id="34a2c-1053">**NX_PTR_ERROR** (0x07) Tentou utilizar um ponteiro inválido para a função de retorno ou sessão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1053">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer for the callback function or TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-1054">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-1054">Allowed From</span></span>

<span data-ttu-id="34a2c-1055">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-1055">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-1056">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-1056">Example</span></span>

```C
/* Simple callback notifying the user that a renegotiation is starting. */
ULONG tls_renegotiation_callback(NX_SECURE_TLS_SESSION *session)
{
    printf("Renegotiation initiated by remote host\n");

    return(NX_SUCCESS);
}

/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Set callback for renegotiation notification. */
status = nx_secure_tls_session_renegotiate_callback_set(&tls_session,
                                                tls_renegotiation_callback);
```

### <a name="see-also"></a><span data-ttu-id="34a2c-1057">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-1057">See Also</span></span>

- <span data-ttu-id="34a2c-1058">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-1058">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="34a2c-1059">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="34a2c-1059">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="34a2c-1060">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="34a2c-1060">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="34a2c-1061">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="34a2c-1061">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="34a2c-1062">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="34a2c-1062">nx_secure_tls_session_renegotiate</span></span>

## <a name="nx_secure_tls_session_renegotiate"></a><span data-ttu-id="34a2c-1063">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="34a2c-1063">nx_secure_tls_session_renegotiate</span></span>

<span data-ttu-id="34a2c-1064">Inicie um aperto de mão de renegociação de sessão com o anfitrião remoto</span><span class="sxs-lookup"><span data-stu-id="34a2c-1064">Initiate a session renegotiation handshake with the remote host</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-1065">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-1065">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_renegotiate (
                  NX_SECURE_TLS_SESSION *tls_session,
                  UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="34a2c-1066">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-1066">Description</span></span>

<span data-ttu-id="34a2c-1067">Este serviço inicia um aperto de mão *de renegociação* de sessão com um anfitrião TLS remoto conectado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1067">This service initiates a session *renegotiation* handshake with a connected remote TLS host.</span></span> <span data-ttu-id="34a2c-1068">Uma renegociação consiste num segundo aperto de mão TLS no contexto de uma sessão TLS previamente estabelecida.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1068">A renegotiation consists of a second TLS handshake within the context of a previously-established TLS session.</span></span> <span data-ttu-id="34a2c-1069">Cada uma das novas mensagens de aperto de mão é encriptada utilizando a sessão TLS até que novas teclas de sessão sejam geradas e as mensagens ChangeCipherSpec sejam trocadas, altura em que as novas teclas são usadas para encriptar todas as mensagens.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1069">Each of the new handshake messages is encrypted using the TLS session until new session keys are generated and ChangeCipherSpec messages are exchanged, at which time the new keys are used to encrypt all messages.</span></span>

<span data-ttu-id="34a2c-1070">Uma renegociação pode ser iniciada a qualquer momento uma vez que uma sessão TLS é estabelecida.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1070">A renegotiation can be initiated at any time once a TLS session is established.</span></span> <span data-ttu-id="34a2c-1071">Se uma renegociação for tentada durante um aperto de mão TLS ou antes de uma sessão TLS ser estabelecida, não serão tomadas medidas.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1071">If a renegotiation is attempted during a TLS handshake or before a TLS session is established no action will be taken.</span></span>

> [!NOTE]
> <span data-ttu-id="34a2c-1072">*Um aperto de mão TLS inteiro será realizado quando este serviço for invocado para que o tempo de conclusão e o estado devolvido variem dependendo das definições e parâmetros de sessão atuais do TLS.*</span><span class="sxs-lookup"><span data-stu-id="34a2c-1072">*An entire TLS handshake will be performed when this service is invoked so the time to completion and returned status will vary depending on the current TLS settings and session parameters.*</span></span>

<span data-ttu-id="34a2c-1073">NetX Secure TLS implementa a Extensão de Insidição de Renegociação Segura do RFC 5746 para garantir que os apertos de mão de renegociação não estão sujeitos a ataques man-in-the-middle.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1073">NetX Secure TLS implements the Secure Renegotiation Inidication Extension from RFC 5746 to ensure that renegotiation handshakes are not subject to man-in-the-middle attacks.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-1074">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-1074">Parameters</span></span>

- <span data-ttu-id="34a2c-1075">**session_ptr** Ponteiro para a sessão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1075">**session_ptr** Pointer to TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-1076">**wait_option** Indica quanto tempo o serviço deve esperar por um pacote do anfitrião remoto antes de regressar.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1076">**wait_option** Indicates how long the service should wait for a packet from the remote host before returning.</span></span> <span data-ttu-id="34a2c-1077">Isto é passado para todos os serviços NetX dentro de TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1077">This is passed to all NetX services within TLS.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-1078">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-1078">Return Values</span></span>

- <span data-ttu-id="34a2c-1079">**NX_SUCCESS** (0x00) Renegociação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1079">**NX_SUCCESS** (0x00) Successful renegotiation.</span></span>
- <span data-ttu-id="34a2c-1080">**NX_NO_PACKET** (0x01) Nenhum dado recebido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1080">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="34a2c-1081">**NX_NOT_CONNECTED** (0x38) A tomada TCP subjacente já não está ligada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1081">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="34a2c-1082">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Uma mensagem recebida falhou num cheque de haxixe de autenticação.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1082">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A received message failed an authentication hash check.</span></span>
- <span data-ttu-id="34a2c-1083">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Uma mensagem recebida continha uma versão de protocolo desconhecida no seu cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1083">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received message contained an unknown protocol version in its header.</span></span>
- <span data-ttu-id="34a2c-1084">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Recebeu um alerta TLS do hospedeiro remoto.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1084">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Received a TLS alert from the remote host.</span></span>
- <span data-ttu-id="34a2c-1085">**NX_SECURE_TLS_RENEGOTIATION_SESSION_INATIVE** (0x134) A sessão TLS local ou remota está inativa, tornando impossível a renegociação.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1085">**NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE** (0x134) The local or remote TLS session is inactive, making renegotiation impossible.</span></span>
- <span data-ttu-id="34a2c-1086">**NX_SECURE_TLS_RENEGOTIATION_FAILURE** (0x13A) O anfitrião remoto não forneceu nem a extensão de renegociação segura do SCSV nem a extensão de renegociação segura, pelo que a renegociação não pode ser realizada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1086">**NX_SECURE_TLS_RENEGOTIATION_FAILURE** (0x13A) The remote host did not provide either the SCSV or Secure Renegotiation Extension and thus renegotiation cannot be performed.</span></span>
- <span data-ttu-id="34a2c-1087">**NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1087">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="34a2c-1088">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) A sessão TLS fornecida não foi inicializada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1088">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>
- <span data-ttu-id="34a2c-1089">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) A atribuição de pacotes subjacentes falhou.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1089">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-1090">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-1090">Allowed From</span></span>

<span data-ttu-id="34a2c-1091">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-1091">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-1092">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-1092">Example</span></span>

```C
/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Setup a client socket connection.  */
status = nx_tcp_client_socket_connect(&tcp_socket, server_ipv4_address,
REMOTE_SERVER_PORT, NX_WAIT_FOREVER);

/* Start the TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Send some data in the first TLS session. (Check “status” for errors…)*/
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Hello there!\r\n", 14, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);

/* Now renegotiate the session. */
status  = nx_secure_tls_session_renegotiate(&tls_session, NX_WAIT_FOREVER);

/* If status == NX_SUCCESS, new TLS session keys have been generated. */

/* Send some data in the new TLS session. This will be encrypted using the new
   keys. */
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Another message…\r\n", 18, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);
```

### <a name="see-also"></a><span data-ttu-id="34a2c-1093">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-1093">See Also</span></span>

- <span data-ttu-id="34a2c-1094">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-1094">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="34a2c-1095">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="34a2c-1095">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="34a2c-1096">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="34a2c-1096">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="34a2c-1097">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="34a2c-1097">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="34a2c-1098">nx_secure_tls_session_renegotiation_callback_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-1098">nx_secure_tls_session_renegotiation_callback_set</span></span>

## <a name="nx_secure_tls_session_reset"></a><span data-ttu-id="34a2c-1099">nx_secure_tls_session_reset</span><span class="sxs-lookup"><span data-stu-id="34a2c-1099">nx_secure_tls_session_reset</span></span>

<span data-ttu-id="34a2c-1100">Limpe e reponha uma Sessão de TLS De Segurança NetX</span><span class="sxs-lookup"><span data-stu-id="34a2c-1100">Clear out and reset a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-1101">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-1101">Prototype</span></span>

```C
UINT  nx_secure_tls_session_reset (NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="34a2c-1102">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-1102">Description</span></span>

<span data-ttu-id="34a2c-1103">Este serviço limpa uma sessão de TLS e repõe o estado como se a sessão tivesse acabado de ser criada para que um objeto de sessão TLS existente possa ser reutilizado para uma nova sessão.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1103">This service clears out a TLS session and resets the state as if the session had just been created so an existing TLS session object can be re-used for a new session.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-1104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-1104">Parameters</span></span>

- <span data-ttu-id="34a2c-1105">**session_ptr** Ponteiro para uma sessão de TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1105">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-1106">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-1106">Return Values</span></span>

- <span data-ttu-id="34a2c-1107">**NX_SUCCESS** (0x00) Iniciação bem sucedida da sessão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1107">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="34a2c-1108">**NX_INVALID_PARAMETERS** (0x4D) Ponteiro de sessão de TLS inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1108">**NX_INVALID_PARAMETERS** (0x4D) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="34a2c-1109">**NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1109">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-1110">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-1110">Allowed From</span></span>

<span data-ttu-id="34a2c-1111">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-1111">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-1112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-1112">Example</span></span>

```C
/* Reset a TLS session.  */
status =  nx_secure_tls_session_reset(&tls_session);


/* If status is NX_SUCCESS the session was successfully reset and may be reused.*/
```

### <a name="see-also"></a><span data-ttu-id="34a2c-1113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-1113">See Also</span></span>

- <span data-ttu-id="34a2c-1114">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-1114">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-1115">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-1115">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="34a2c-1116">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="34a2c-1116">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="34a2c-1117">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="34a2c-1117">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="34a2c-1118">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="34a2c-1118">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="34a2c-1119">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="34a2c-1119">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="34a2c-1120">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-1120">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_send"></a><span data-ttu-id="34a2c-1121">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="34a2c-1121">nx_secure_tls_session_send</span></span>

<span data-ttu-id="34a2c-1122">Enviar dados através de uma Sessão De TLS Segura NetX</span><span class="sxs-lookup"><span data-stu-id="34a2c-1122">Send data through a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-1123">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-1123">Prototype</span></span>

```C
UINT  nx_secure_tls_session_send(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET *packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34a2c-1124">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-1124">Description</span></span>

<span data-ttu-id="34a2c-1125">Este serviço envia dados no NX_PACKET fornecido, utilizando a sessão de TLS ativa especificada, e manuseando a encriptação desses dados antes de os enviar para o anfitrião remoto.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1125">This service sends data in the supplied NX_PACKET, using the specified active TLS session, and handling the encryption of that data before sending it to the remote host.</span></span> <span data-ttu-id="34a2c-1126">Se o último tamanho da janela anunciado pelo recetor for inferior a este pedido, o serviço suspende opcionalmente com base nas opções de espera especificadas.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1126">If the receiver's last advertised window size is less than this request, the service optionally suspends based on the wait options specified.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34a2c-1127">*A menos que um erro seja devolvido, o pedido não deve libertar o pacote após esta chamada. Ao fazê-lo, o controlador da rede libertará o pacote após a transmissão.*</span><span class="sxs-lookup"><span data-stu-id="34a2c-1127">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-1128">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-1128">Parameters</span></span>

- <span data-ttu-id="34a2c-1129">**session_ptr** Ponteiro para uma sessão de TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1129">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-1130">**packet_ptr** Ponteiro para um pacote TLS contendo dados a enviar.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1130">**packet_ptr** Pointer to a TLS packet containing data to be sent.</span></span>
- <span data-ttu-id="34a2c-1131">**wait_option** Define como o serviço se comporta se o pedido for maior do que o tamanho da janela do recetor.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1131">**wait_option** Defines how the service behaves if the request is greater than the window size of the receiver.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-1132">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-1132">Return Values</span></span>

- <span data-ttu-id="34a2c-1133">**NX_SUCCESS** (0x00) Iniciação bem sucedida da sessão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1133">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="34a2c-1134">**NX_NO_PACKET** (0x01) Nenhum dado recebido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1134">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="34a2c-1135">**NX_NOT_CONNECTED** (0x38) A tomada TCP subjacente já não está ligada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1135">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="34a2c-1136">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) A tomada TCP subjacente falhou.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1136">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) The underlying TCP socket send failed.</span></span>
- <span data-ttu-id="34a2c-1137">**NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1137">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="34a2c-1138">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) A sessão TLS fornecida não foi inicializada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1138">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-1139">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-1139">Allowed From</span></span>

<span data-ttu-id="34a2c-1140">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-1140">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-1141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-1141">Example</span></span>

```C
/* Send a packet using an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is sent, blocking otherwise.   */
status =  nx_secure_tls_session_send(&tls_session, &packet_ptr, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the packet has been sent. */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-1142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-1142">See Also</span></span>

- <span data-ttu-id="34a2c-1143">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="34a2c-1143">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="34a2c-1144">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-1144">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-1145">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-1145">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="34a2c-1146">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-1146">nx_secure_tls_packet_allocate</span></span>
- <span data-ttu-id="34a2c-1147">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="34a2c-1147">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="34a2c-1148">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="34a2c-1148">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="34a2c-1149">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="34a2c-1149">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="34a2c-1150">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="34a2c-1150">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="34a2c-1151">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-1151">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_server_callback_set"></a><span data-ttu-id="34a2c-1152">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-1152">nx_secure_tls_session_server_callback_set</span></span>

<span data-ttu-id="34a2c-1153">Configurar uma chamada para o TLS invocar no início de um aperto de mão do TLS Server</span><span class="sxs-lookup"><span data-stu-id="34a2c-1153">Set up a callback for TLS to invoke at the beginning of a TLS Server handshake</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-1154">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-1154">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_server_callback_set (
                 NX_SECURE_TLS_SESSION *tls_session,
                 ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                   NX_SECURE_TLS_HELLO_EXTENSION
                                   *extensions, UINT num_extensions));
```

### <a name="description"></a><span data-ttu-id="34a2c-1155">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-1155">Description</span></span>

<span data-ttu-id="34a2c-1156">Este serviço atribui um ponteiro de função a uma sessão de TLS que o TLS invocará quando um aperto de mão do Servidor TLS tiver recebido uma mensagem ClientHello.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1156">This service assigns a function pointer to a TLS session that TLS will invoke when a TLS Server handshake has received a ClientHello message.</span></span> <span data-ttu-id="34a2c-1157">A função de retorno permite que uma aplicação processe quaisquer extensões TLS da mensagem ClientHello recebida que exijam entrada ou tomada de decisão.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1157">The callback function allows an application to process any TLS extensions from the received ClientHello message that require input or decision making.</span></span>

<span data-ttu-id="34a2c-1158">O retorno é executado com o bloco de controlo de sessão TLS invocando e uma série de objetos NX_SECURE_TLS_HELLO_EXTENSION.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1158">The callback is executed with the invoking TLS session control block and an array of NX_SECURE_TLS_HELLO_EXTENSION objects.</span></span> <span data-ttu-id="34a2c-1159">A matriz de objetos de extensão destina-se a ser passada para uma função auxiliar que irá encontrar e analisar uma extensão específica.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1159">The array of extension objects is intended to be passed into a helper function that will find and parse a specific extension.</span></span> <span data-ttu-id="34a2c-1160">Para uma função de ajudante de exemplo que analisa as extensões TLS fornecidas em mensagens hello, consulte *nx_secure_tls_session_sni_extension_parse*.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1160">For an example helper function that parses TLS extensions provided in hello messages, see *nx_secure_tls_session_sni_extension_parse*.</span></span>

<span data-ttu-id="34a2c-1161">O retorno do servidor também pode ser usado para selecionar o certificado de identidade ativo utilizando *nx_secure_tls_ative_certificate_set* para o Servidor TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1161">The server callback may also be used to select the active identity certificate using *nx_secure_tls_active_certificate_set* for the TLS Server.</span></span> <span data-ttu-id="34a2c-1162">Isto ocorrerá na maioria das vezes em resposta a uma extensão de Indicação de Nome do Servidor (SNI) que permite a um Cliente TLS indicar que servidor está a tentar contactar.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1162">This will most often occur in response to a Server Name Indication (SNI) extension which allows a TLS Client to indicate which server it is attempting to contact.</span></span> <span data-ttu-id="34a2c-1163">Consulte as referências para *nx_secure_tls_session_sni_extension_parse* e *nx_secure_tls_ative_certificate_set* para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1163">See the references for *nx_secure_tls_session_sni_extension_parse* and *nx_secure_tls_active_certificate_set* for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-1164">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-1164">Parameters</span></span>

- <span data-ttu-id="34a2c-1165">**session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1165">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-1166">**func_ptr** Ponteiro para a função de retorno do servidor TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1166">**func_ptr** Pointer to the TLS Server callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-1167">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-1167">Return Values</span></span>

- <span data-ttu-id="34a2c-1168">**NX_SUCCESS** (0x00) Atribuição bem sucedida do ponteiro função.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1168">**NX_SUCCESS** (0x00) Successful allocation of Function pointer.</span></span>
- <span data-ttu-id="34a2c-1169">**NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1169">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-1170">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-1170">Allowed From</span></span>

<span data-ttu-id="34a2c-1171">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-1171">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-1172">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-1172">Example</span></span>

```C
/* Application-supplied function to map server DNS name to a specific certificate
   ID. The certificate ID is supplied by the application when the certificate is
   added with nx_secure_tls_server_certificate_add. */
UINT application_find_id_by_dns_name(NX_SECURE_X509_DNS_NAME *dns_name)
{
    if(strncmp(dns_name->nx_secure_x509_dns_name, “server_name”,
               dns_name->nx_secure_x509_dns_name_length) == 0)
    {
        /* DNS name matches one we know, return it’s ID. */
        return(0x12);
    }

    /* Unknown DNS name, return 0 to indicate no matching ID found. */
    return(0);
}

/* Callback routine used to process ClientHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the client). */
ULONG tls_server_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{
UINT status;
NX_SECURE_X509_DNS_NAME dns_name;
UINT cert_id;
NX_SECURE_X509_CERT *certificate;


    /* Find and parse a Server Name Indication (SNI) extension. */
    status = nx_secure_tls_session_sni_extension_parse(session, extensions,
                                                       num_extensions, &dns_name);

    if(status != NX_SUCCESS && status != NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
        /* Parsed an invalid extension, return the error. */
        return(status);
    }

    if(status == NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
            /* SNI extension not found, just return success to use the default
               certificate. */
            return(NX_SUCCESS);
    }

    /* Find the application-supplied numeric identifier for the specified DNS
       name provided by the remote client. */
    cert_id = application_find_id_by_dns_name(&dns_name);

    /* If cert_id is 0, just use the default identity certificate added with
       nx_secure_tls_local_certificate_add. */
    if(cert_id != 0)
    {
        /* Application found a matching name, find the certificate in our
           store. */
        status = nx_secure_tls_server_certificate_find(tls_session, &certificate,
                                                       cert_id);

        if(status != NX_SUCCESS)
        {
            /* Didn’t find a valid certificate with the supplied ID. Return an
               error so TLS can shut down the handshake. */
            return(NX_SECURE_TLS_CERTIFICATE_NOT_FOUND);
        }

        /* Set the active identity certificate – the certificate should have been
           added to the local store at application start with
           nx_secure_tls_local_certificate_add. */
        nx_secure_tls_active_certificate_set(session, certificate);
    }

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_server_callback_set(tls_session,
                                                            server_callback);

        /* If status is NX_SUCCESS the callback was added and will be invoked
           immediately after a ClientHello message is received. */

        return(status);
}
```

### <a name="see-also"></a><span data-ttu-id="34a2c-1173">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-1173">See Also</span></span>

- <span data-ttu-id="34a2c-1174">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-1174">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="34a2c-1175">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-1175">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="34a2c-1176">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-1176">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="34a2c-1177">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="34a2c-1177">nx_secure_tls_session_sni_extension_parse</span></span>
- <span data-ttu-id="34a2c-1178">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-1178">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="34a2c-1179">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="34a2c-1179">nx_secure_tls_server_certificate_find</span></span>

## <a name="nx_secure_tls_session_sni_extension_parse"></a><span data-ttu-id="34a2c-1180">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="34a2c-1180">nx_secure_tls_session_sni_extension_parse</span></span>

<span data-ttu-id="34a2c-1181">Parse uma extensão de indicação de nome do servidor (SNI) recebida de um cliente TLS</span><span class="sxs-lookup"><span data-stu-id="34a2c-1181">Parse a Server Name Indication (SNI) extension received from a TLS Client</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-1182">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-1182">Prototype</span></span>

```C
UINT  nx_secure_tls_session_sni_extension_parse(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions,
                                    UINT num_extensions,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a><span data-ttu-id="34a2c-1183">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-1183">Description</span></span>

<span data-ttu-id="34a2c-1184">Este serviço destina-se a ser chamado a partir de uma chamada de sessão do TLS Server, adicionada a uma sessão de TLS utilizando nx_secure_tls_session_server_callback_set.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1184">This service is intended to be called from within a TLS Server session callback, added to a TLS session using nx_secure_tls_session_server_callback_set.</span></span> <span data-ttu-id="34a2c-1185">A chamada é invocada após a receção de uma mensagem ClientHello de um cliente TLS remoto e é fornecida uma série de extensões disponíveis (e o número de extensões na matriz).</span><span class="sxs-lookup"><span data-stu-id="34a2c-1185">The callback is invoked following the reception of a ClientHello message from a remote TLS client and is supplied an array of available extensions (and the number of extensions in the array).</span></span> <span data-ttu-id="34a2c-1186">Este conjunto e o seu comprimento podem ser transmitidos diretamente a esta rotina para determinar se existe uma extensão SNI presente – se não, NX_SECURE_TLS_EXTENSION_NOT_FOUND é devolvida, indicando simplesmente que o cliente optou por não provicendo a extensão SNI (isto não é um erro).</span><span class="sxs-lookup"><span data-stu-id="34a2c-1186">That array and its length can be passed directly to this routine to determine if there is an SNI extension present – if not, NX_SECURE_TLS_EXTENSION_NOT_FOUND is returned indicating simply that the client opted not to provice the SNI extension (this is not an error).</span></span>

<span data-ttu-id="34a2c-1187">Se a extensão SNI for encontrada, o nome DNS X.509 fornecido pelo cliente TLS é devolvido na estrutura dns_name.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1187">If the SNI extension is found, the X.509 DNS name supplied by the TLS client is returned in the dns_name structure.</span></span> <span data-ttu-id="34a2c-1188">Atualmente, a extensão SNI apenas fornece uma única entrada de nome DNS, que pode ser usada pelo servidor TLS para determinar que certificado de identidade enviar para o cliente remoto.\*\*</span><span class="sxs-lookup"><span data-stu-id="34a2c-1188">Currently, the SNI extension only supplies a single DNS name entry, which may be used by the TLS server to determine which identity certificate to send to the remote client.\*\*</span></span>

<span data-ttu-id="34a2c-1189">A estrutura NX_SECURE_X509_DNS_NAME contém simplesmente o nome DNS como uma cadeia UCHAR no campo *nx_secure_x509_dns_name* e o comprimento da cadeia de nomes em *nx_secure_x509_dns_name_length*.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1189">The NX_SECURE_X509_DNS_NAME structure simply contains the DNS name as a UCHAR string in the field *nx_secure_x509_dns_name* and the length of the name string in *nx_secure_x509_dns_name_length*.</span></span> <span data-ttu-id="34a2c-1190">O NX_SECURE_X509_DNS_NAME_MAX macro controla o tamanho do tampão nx_secure_x509_dns_name.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1190">The macro NX_SECURE_X509_DNS_NAME_MAX controls the size of the nx_secure_x509_dns_name buffer.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-1191">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-1191">Parameters</span></span>

- <span data-ttu-id="34a2c-1192">**session_ptr** Ponteiro para uma sessão de TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1192">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-1193">**extensões** Ponteiro para uma variedade de extensões TLS Hello (a partir de chamada de sessão).</span><span class="sxs-lookup"><span data-stu-id="34a2c-1193">**extensions** Pointer to an array of TLS Hello extensions (from session callback).</span></span>
- <span data-ttu-id="34a2c-1194">**num_extensions** Número de extensões na matriz (a partir da chamada de sessão).</span><span class="sxs-lookup"><span data-stu-id="34a2c-1194">**num_extensions** Number of extensions in array (from session callback).</span></span>
- <span data-ttu-id="34a2c-1195">**dns_name** Devolução do nome DNS fornecido na extensão SNI.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1195">**dns_name** Return DNS name supplied in the SNI extension.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-1196">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-1196">Return Values</span></span>

- <span data-ttu-id="34a2c-1197">**NX_SUCCESS** (0x00) Análise bem sucedida da extensão.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1197">**NX_SUCCESS** (0x00) Successful parsing of the extension.</span></span>
- <span data-ttu-id="34a2c-1198">**NX_PTR_ERROR** (0x07) Matriz de extensões inválidas ou ponteiro de sessão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1198">**NX_PTR_ERROR** (0x07) Invalid extensions array or TLS session pointer.</span></span>
- <span data-ttu-id="34a2c-1199">**NX_SECURE_TLS_EXTENSION_NOT_FOUND** (0x136) extensão do SNI não encontrada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1199">**NX_SECURE_TLS_EXTENSION_NOT_FOUND** (0x136) SNI extension not found.</span></span>
- <span data-ttu-id="34a2c-1200">**NX_SECURE_TLS_SNI_EXTENSION_INVALID** (0x137) o formato de extensão SNI era inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1200">**NX_SECURE_TLS_SNI_EXTENSION_INVALID** (0x137) SNI extension format was invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-1201">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-1201">Allowed From</span></span>

<span data-ttu-id="34a2c-1202">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-1202">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-1203">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-1203">Example</span></span>

### <a name="see-also"></a><span data-ttu-id="34a2c-1204">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-1204">See Also</span></span>

- <span data-ttu-id="34a2c-1205">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-1205">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="34a2c-1206">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-1206">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="34a2c-1207">nx_secure_tls_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-1207">nx_secure_tls_server_callback_set</span></span>
- <span data-ttu-id="34a2c-1208">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-1208">nx_secure_tls_active_certificate_set</span></span>

## <a name="nx_secure_tls_session_sni_extension_set"></a><span data-ttu-id="34a2c-1209">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-1209">nx_secure_tls_session_sni_extension_set</span></span>

<span data-ttu-id="34a2c-1210">Desa estade um nome DNS de extensão de extensão de nome do servidor (SNI) para enviar para um servidor remoto</span><span class="sxs-lookup"><span data-stu-id="34a2c-1210">Set a Server Name Indication (SNI) extension DNS name to send to a remote Server</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-1211">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-1211">Prototype</span></span>

```C
UINT  nx_secure_tls_session_sni_extension_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a><span data-ttu-id="34a2c-1212">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-1212">Description</span></span>

<span data-ttu-id="34a2c-1213">Este serviço permite que uma aplicação do Cliente TLS forneça um nome DNS de servidor preferido a um servidor TLS remoto utilizando a extensão TLS de Indicação de Nome do Servidor (SNI).</span><span class="sxs-lookup"><span data-stu-id="34a2c-1213">This service allows a TLS Client application to provide a preferred server DNS name to a remote TLS server using the Server Name Indication (SNI) TLS extension.</span></span> <span data-ttu-id="34a2c-1214">A extensão SNI permite ao servidor selecionar o certificado de identidade e parâmetros adequados com base na preferência indicada do servidor do cliente.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1214">The SNI extension allows the server to select the proper identity certificate and parameters based on the client's indicated server preference.</span></span> <span data-ttu-id="34a2c-1215">A extensão SNI suporta atualmente apenas um único nome DNS a ser enviado, daí o parâmetro de nome singular.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1215">The SNI extension currently only supports a single DNS name to be sent, hence the singular name parameter.</span></span> <span data-ttu-id="34a2c-1216">O parâmetro dns_name deve ser inicializado com *nx_secure_x509_dns_name_initialize* e conterá o servidor preferido do cliente.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1216">The dns_name parameter must be initialized with *nx_secure_x509_dns_name_initialize* and will contain the client's preferred server.</span></span> <span data-ttu-id="34a2c-1217">Para desaparar o nome da extensão, basta ligar para este serviço com um valor de parâmetro "dns_name" de NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1217">To unset the extension name, simply call this service with a "dns_name" parameter value of NX_NULL.</span></span>

<span data-ttu-id="34a2c-1218">A estrutura NX_SECURE_X509_DNS_NAME contém simplesmente o nome DNS como uma cadeia UCHAR no campo  *nx_secure_x509_dns_name* e o comprimento da cadeia de nomes em *nx_secure_x509_dns_name_length*.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1218">The NX_SECURE_X509_DNS_NAME structure simply contains the DNS name as a UCHAR string in the field  *nx_secure_x509_dns_name* and the length of the name string in *nx_secure_x509_dns_name_length*.</span></span> <span data-ttu-id="34a2c-1219">O NX_SECURE_X509_DNS_NAME_MAX macro controla o tamanho do tampão nx_secure_x509_dns_name.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1219">The macro  NX_SECURE_X509_DNS_NAME_MAX controls the size of the nx_secure_x509_dns_name buffer.</span></span>

> [!NOTE]
> <span data-ttu-id="34a2c-1220">*Esta rotina deve ser chamada antes de nx_secure_tls_session_start ser invocada ou o ClientHello não conterá a extensão SNI.*</span><span class="sxs-lookup"><span data-stu-id="34a2c-1220">*This routine must be called before nx_secure_tls_session_start is invoked or the ClientHello will not contain the SNI extension.*</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-1221">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-1221">Parameters</span></span>

- <span data-ttu-id="34a2c-1222">**session_ptr** Ponteiro para uma sessão de TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1222">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-1223">**dns_name** Nome DNS fornecido pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1223">**dns_name** DNS name supplied by the application.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-1224">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-1224">Return Values</span></span>

- <span data-ttu-id="34a2c-1225">**NX_SUCCESS** (0x00) Adição bem sucedida do nome do servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1225">**NX_SUCCESS** (0x00) Successful addition of DNS server name.</span></span>
- <span data-ttu-id="34a2c-1226">**NX_PTR_ERROR** (0x07) Nome DNS inválido ou ponteiro de sessão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1226">**NX_PTR_ERROR** (0x07) Invalid DNS name or TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-1227">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-1227">Allowed From</span></span>

<span data-ttu-id="34a2c-1228">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-1228">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-1229">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-1229">Example</span></span>

```C
#define TLS_SNI_SERVER_NAME “www.example.com”

NX_SECURE_X509_DNS_NAME dns_name;
NX_SECURE_TLS_SESSION client_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&client_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));


    /* Initialize the DNS server name we want to send in the SNI extension. */
    nx_secure_x509_dns_name_initialize(&dns_name, TLS_SNI_SERVER_NAME,
                                    strlen(TLS_SNI_SERVER_NAME));

    /* The SNI server name needs to be set prior to starting the TLS session. */
    nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);

   /* Start TLS session as normal. */
}
```

### <a name="see-also"></a><span data-ttu-id="34a2c-1230">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-1230">See Also</span></span>

- <span data-ttu-id="34a2c-1231">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="34a2c-1231">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="34a2c-1232">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-1232">nx_secure_x509_dns_name_initialize</span></span>

## <a name="nx_secure_tls_session_start"></a><span data-ttu-id="34a2c-1233">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="34a2c-1233">nx_secure_tls_session_start</span></span>

<span data-ttu-id="34a2c-1234">Inicie uma Sessão De TLS Segura NetX</span><span class="sxs-lookup"><span data-stu-id="34a2c-1234">Start a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-1235">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-1235">Prototype</span></span>

```C
UINT  nx_secure_tls_session_start(NX_SECURE_TLS_SESSION *session_ptr,
                                  NX_TCP_SOCKET *tcp_socket_ptr,
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34a2c-1236">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-1236">Description</span></span>

<span data-ttu-id="34a2c-1237">Este serviço inicia uma sessão TLS utilizando o bloco de controlo de sessão TLS fornecido e uma tomada TCP conectada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1237">This service starts a TLS session using the supplied TLS session control block and a connected TCP socket.</span></span> <span data-ttu-id="34a2c-1238">A ligação TCP já deve estar completa na sequência de uma chamada bem sucedida para nx_tcp_client_socket_connect ou nx_tcp_server_socket_accept.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1238">The TCP connection must already be complete following a successful call to either nx_tcp_client_socket_connect or nx_tcp_server_socket_accept.</span></span>

<span data-ttu-id="34a2c-1239">Este serviço determinará o tipo de sessão TLS (Cliente ou Servidor) a partir da tomada TCP.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1239">This service will determine the type of TLS session (Client or Server) from the TCP socket.</span></span>

<span data-ttu-id="34a2c-1240">A opção de espera define como o serviço se comporta enquanto o aperto de mão TLS está em andamento.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1240">The wait option defines how the service behaves while the TLS handshake is in progress.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-1241">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-1241">Parameters</span></span>

- <span data-ttu-id="34a2c-1242">**session_ptr** Ponteiro para uma sessão de TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1242">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-1243">**tcp_socket_ptr** Ponteiro para uma tomada TCP ligada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1243">**tcp_socket_ptr** Pointer to a connected TCP socket.</span></span>
- <span data-ttu-id="34a2c-1244">**wait_option** Define como o serviço se comporta enquanto o aperto de mão TLS está em andamento.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1244">**wait_option** Defines how the service behaves while the TLS handshake is in progress.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-1245">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-1245">Return Values</span></span>

- <span data-ttu-id="34a2c-1246">**NX_SUCCESS** (0x00) Iniciação bem sucedida da sessão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1246">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="34a2c-1247">**NX_NOT_CONNECTED** (0x38) A tomada TCP subjacente já não está ligada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1247">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="34a2c-1248">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) Um tipo de mensagem TLS recebido está incorreto.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1248">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS message type is incorrect.</span></span>
- <span data-ttu-id="34a2c-1249">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) Uma cifra fornecida pelo hospedeiro remoto não é suportada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1249">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="34a2c-1250">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) O processamento de mensagens durante o aperto de mão TLS falhou.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1250">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="34a2c-1251">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Uma mensagem recebida falhou numa verificação de HASH MAC.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1251">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a hash MAC check.</span></span>
- <span data-ttu-id="34a2c-1252">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Um envio de tomada TCP subjacente falhou.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1252">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="34a2c-1253">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Uma mensagem recebida tinha um campo de comprimento inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1253">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="34a2c-1254">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) Uma mensagem ChangeCipherSpec recebida estava incorreta.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1254">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="34a2c-1255">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) Um certificado TLS de entrada é inutilizável para identificar o servidor TLS remoto.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1255">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) An incoming TLS certificate is unusable for identifying the remote TLS server.</span></span>
- <span data-ttu-id="34a2c-1256">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) A cifra de chave pública fornecida pelo hospedeiro remoto não é suportada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1256">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="34a2c-1257">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) O anfitrião remoto não indicou cifrasuites que sejam suportadas pela pilha NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1257">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure TLS stack.</span></span>
- <span data-ttu-id="34a2c-1258">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Uma mensagem TLS recebida tinha uma versão TLS desconhecida no seu cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1258">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received TLS message had an unknown TLS version in its header.</span></span>
- <span data-ttu-id="34a2c-1259">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Uma mensagem TLS recebida tinha uma versão TLS conhecida mas não suportada no seu cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1259">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received TLS message had a known but unsupported TLS version in its header.</span></span>
- <span data-ttu-id="34a2c-1260">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Uma atribuição interna de pacotes TLS falhou.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1260">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="34a2c-1261">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) O anfitrião remoto forneceu um certificado inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1261">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="34a2c-1262">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) O anfitrião remoto enviou um alerta indicando um erro e terminando a sessão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1262">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="34a2c-1263">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) Uma entrada na tabela cifrasumita tinha um ponteiro de função NU.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1263">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) An entry in the ciphersuite table had a NULL function pointer.</span></span>
- <span data-ttu-id="34a2c-1264">**NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** (0x146) Um cliente remoto TLS ClientHello incluiu o recuo SCSV e atacou um retorno de versão.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1264">**NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** (0x146) A remote TLS ClientHello included the fallback SCSV andattempted a version fallback.</span></span>
- <span data-ttu-id="34a2c-1265">**NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1265">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-1266">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-1266">Allowed From</span></span>

<span data-ttu-id="34a2c-1267">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-1267">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-1268">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-1268">Example</span></span>

```C
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Initialize the TLS session structure. */
nx_secure_tls_session_create(&tls_session,
                              &nx_crypto_tls_ciphers,
                              crypto_metadata,
                              sizeof(crypto_metadata));

/* Setup the TLS packet reassembly buffer. */
status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                 sizeof(tls_packet_buffer));

/* Initialize a certificate for the TLS server. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data, 500,
NX_NULL, 0, private_key, 64);

/* If status is NX_SUCCESS, certificate is initialized. */

/* Add the certificate a local certificate to identify this TLS server. */
status = nx_secure_tls_add_local_certificate(&tls_session, &certificate);

/* If status is NX_SUCCESS, certificate was added successfully. */

/* Create and start a TCP socket as a server. */
/* NOTE: This assumes an IP instance called “ip_0” has already been created. */

/* Create a TCP server socket on the previously created IP instance, with normal
   delivery, IP fragmentation enabled, default time to live, a 8192-byte receive
   window, no urgent callback routine, and the "client_disconnect" routine to
   handle disconnection initiated from the other end of the connection.  */
status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Server Socket", NX_IP_NORMAL,
                               NX_FRAGMENT_OKAY, NX_IP_TIME_TO_LIVE, 8192, NX_NULL,
                               NX_NULL);

/* If status is NX_SUCCESS, the TCP socket was created successfully. */

/* Start up a TCP server socket by listening on port 443 with a listen queue of
   size 5. */
status =  nx_tcp_server_socket_listen(&ip_0, 443, &tcp_socket, 5, NX_NULL);

/* Application main loop. */
while(1)
{
        /* Accept incoming requests on the TCP socket. */
        status =  nx_tcp_server_socket_accept(&tcp_socket, NX_WAIT_FOREVER);

        /* At this point, the TCP socket should be established (but not the TLS
        session yet). */

        /* Start the TLS session on our active TCP socket. */
        status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                             NX_WAIT_FOREVER);

        /* At this point, if status is NX_SUCCESS, the TLS session has been
           established.  Application may now send/receive data through this
           channel. */

        /* Send and receive data using the TLS session. */
        /* Allocate TLS packets using nx_secure_tls_packet_allocate, write data with
           nx_packet_data_append, read data with nx_packet_data_extract_offset. */

        /* Send TLS data. */
        nx_secure_tls_session_send(&tls_session, &send_packet, NX_WAIT_FOREVER);

        nx_secure_tls_session_receive(&tls_session, &receive_packet_ptr,
        NX_WAIT_FOREVER);


        /* Once all application data is sent/received, end the TLS session. */
        status = nx_secure_tls_session_end(&tls_session);

        /* If status is NX_SUCCESS, the TLS session has been closed properly. */

        /* Now disconnect the TCP server socket from the client.  */
        nx_tcp_socket_disconnect(&tcp_socket, 200);

        /* Unaccept the TCP server socket.  Note that unaccept is called even if
           disconnect or accept fails.  */
        nx_tcp_server_socket_unaccept(&tcp_socket);

        /* Setup server socket for listening with this socket again.  */
        nx_tcp_server_socket_relisten(&ip_0, 443, &tcp_socket);
}

/* When the server application is shut down, clean up the TLS session. */
nx_secure_tls_session_delete(&tls_session);

/* Finally, clean up the TCP socket as well. */
nx_tcp_socket_delete(&tcp_socket);
```

### <a name="see-also"></a><span data-ttu-id="34a2c-1269">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-1269">See Also</span></span>

- <span data-ttu-id="34a2c-1270">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="34a2c-1270">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="34a2c-1271">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-1271">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-1272">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-1272">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="34a2c-1273">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="34a2c-1273">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="34a2c-1274">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="34a2c-1274">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="34a2c-1275">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="34a2c-1275">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="34a2c-1276">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-1276">nx_secure_tls_packet_allocate</span></span>
- <span data-ttu-id="34a2c-1277">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="34a2c-1277">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="34a2c-1278">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-1278">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="34a2c-1279">nx_tcp_socket_accept</span><span class="sxs-lookup"><span data-stu-id="34a2c-1279">nx_tcp_socket_accept</span></span>
- <span data-ttu-id="34a2c-1280">nx_tcp_socket_listen</span><span class="sxs-lookup"><span data-stu-id="34a2c-1280">nx_tcp_socket_listen</span></span>
- <span data-ttu-id="34a2c-1281">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="34a2c-1281">nx_tcp_socket_disconnect</span></span>
- <span data-ttu-id="34a2c-1282">nx_tcp_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="34a2c-1282">nx_tcp_socket_unaccept</span></span>
- <span data-ttu-id="34a2c-1283">nx_tcp_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="34a2c-1283">nx_tcp_socket_relisten</span></span>
- <span data-ttu-id="34a2c-1284">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="34a2c-1284">nx_tcp_socket_delete</span></span>
- <span data-ttu-id="34a2c-1285">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-1285">nx_packet_allocate</span></span>
- <span data-ttu-id="34a2c-1286">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="34a2c-1286">nx_packet_data_append</span></span>
- <span data-ttu-id="34a2c-1287">nx_packet_data_extract_offset</span><span class="sxs-lookup"><span data-stu-id="34a2c-1287">nx_packet_data_extract_offset</span></span>

## <a name="nx_secure_tls_session_time_function_set"></a><span data-ttu-id="34a2c-1288">nx_secure_tls_session_time_function_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-1288">nx_secure_tls_session_time_function_set</span></span>

<span data-ttu-id="34a2c-1289">Atribua uma função de marcação de tempo a uma Sessão TLS Segura NetX</span><span class="sxs-lookup"><span data-stu-id="34a2c-1289">Assign a timestamp function to a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-1290">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-1290">Prototype</span></span>

```C
UINT  nx_secure_tls_time_function_set(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              ULONG (*time_func_ptr)(void));
```

### <a name="description"></a><span data-ttu-id="34a2c-1291">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-1291">Description</span></span>

<span data-ttu-id="34a2c-1292">Esta função configura um ponteiro de função que o TLS invocará quando precisar de obter o tempo atual, que é usado em várias mensagens de aperto de mão TLS e para verificação de certificados.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1292">This function sets up a function pointer that TLS will invoke when it needs to get the current time, which is used in various TLS handshake messages and for verification of certificates.</span></span>

<span data-ttu-id="34a2c-1293">Espera-se que a função devolva o atual GMT no formato UNIX de 32 bits (segundos desde a meia-noite a partir de 1 de janeiro de 1970, UTC, ignorando os segundos de salto), de acordo com os requisitos do ClientHello no TLS RFC 5246.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1293">The function is expected to return the current GMT in UNIX 32-bit format (seconds since the midnight starting Jan 1, 1970, UTC, ignoring leap seconds), as per the ClientHello requirements in the TLS RFC 5246.</span></span>

<span data-ttu-id="34a2c-1294">Se não for atribuída nenhuma função de calibragem de tempo, será utilizado um valor de 0 para o tempo de calibragem no aperto de mão TLS e a verificação de expiração do certificado não funcionará.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1294">If no timestamp function is assigned, a value of 0 for the timestamp in the TLS handshake will be used and certificate expiration checking will not work.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-1295">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-1295">Parameters</span></span>

- <span data-ttu-id="34a2c-1296">**session_ptr** Ponteiro para uma sessão de TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1296">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-1297">**time_func_ptr** Ponteiro para uma função que retorna a hora atual (GMT) no formato UNIX de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1297">**time_func_ptr** Pointer to a function that returns the current time (GMT) in UNIX 32-bit format.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-1298">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-1298">Return Values</span></span>

- <span data-ttu-id="34a2c-1299">**NX_SUCCESS** (0x00) Iniciação bem sucedida da sessão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1299">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="34a2c-1300">**NX_INVALID_PARAMETERS** (0x4D) Ponteiro de sessão de TLS inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1300">**NX_INVALID_PARAMETERS** (0x4D) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="34a2c-1301">**NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1301">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-1302">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-1302">Allowed From</span></span>

<span data-ttu-id="34a2c-1303">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-1303">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-1304">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-1304">Example</span></span>

```C
/* This function returns a 32-bit UNIX-style representation of the current GMT
   time. */
ULONG get_gmt_time(void)
{
ULONG time_value;

   /* Platform-specific time calculation goes here… */

   return(time_value);
}

/* Reset a TLS session.  */
status =  nx_secure_tls_timestamp_function_set(&tls_session, get_gmt_time);


/* If status is NX_SUCCESS the function was successfully added.*/
```

### <a name="see-also"></a><span data-ttu-id="34a2c-1305">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-1305">See Also</span></span>

- <span data-ttu-id="34a2c-1306">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-1306">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-1307">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-1307">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="34a2c-1308">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="34a2c-1308">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="34a2c-1309">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="34a2c-1309">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="34a2c-1310">nx_secure_tls_session_sendnx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="34a2c-1310">nx_secure_tls_session_sendnx_secure_tls_session_receive</span></span>
- <span data-ttu-id="34a2c-1311">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-1311">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_trusted_certificate_add"></a><span data-ttu-id="34a2c-1312">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-1312">nx_secure_tls_trusted_certificate_add</span></span>

<span data-ttu-id="34a2c-1313">Adicionar certificado fidedigno à Sessão TLS Do NetX Secure</span><span class="sxs-lookup"><span data-stu-id="34a2c-1313">Add trusted certificate to NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-1314">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-1314">Prototype</span></span>

```C
UINT  nx_secure_tls_trusted_certificate_add(NX_SECURE_TLS_SESSION
                            *session_ptr, NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a><span data-ttu-id="34a2c-1315">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-1315">Description</span></span>

<span data-ttu-id="34a2c-1316">Este serviço adiciona uma instância de estrutura de NX_SECURE_X509_CERT inicializada a uma sessão de TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1316">This service adds an initialized NX_SECURE_X509_CERT structure instance to a TLS session.</span></span> <span data-ttu-id="34a2c-1317">Este certificado é utilizado pela pilha TLS para verificar os certificados fornecidos pelo anfitrião remoto durante o aperto de mão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1317">This certificate is used by the TLS stack to verify certificates supplied by the remote host during the TLS handshake.</span></span>

<span data-ttu-id="34a2c-1318">São necessários certificados fidedignos para o modo cliente TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1318">Trusted certificates are required for TLS Client mode.</span></span>

<span data-ttu-id="34a2c-1319">Os certificados fidedignos só são necessários para o modo TLS Server se a autenticação do certificado do cliente estiver ativada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1319">Trusted certificates are only required for TLS Server mode if client certificate authentication is enabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-1320">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-1320">Parameters</span></span>

- <span data-ttu-id="34a2c-1321">**session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1321">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-1322">**certificate_ptr** Ponteiro para uma instância inicializada do Certificado TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1322">**certificate_ptr** Pointer to an initialized TLS Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-1323">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-1323">Return Values</span></span>

- <span data-ttu-id="34a2c-1324">**NX_SUCCESS** (0x00) Adição bem sucedida do certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1324">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="34a2c-1325">**NX_INVALID_PARAMETERS** (0x4D) Tentou adicionar um certificado inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1325">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid certificate.</span></span>
- <span data-ttu-id="34a2c-1326">**NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1326">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-1327">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-1327">Allowed From</span></span>

<span data-ttu-id="34a2c-1328">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-1328">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-1329">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-1329">Example</span></span>

```C
/* Initialize certificate structure. */
status = nx_secure_x509_certificate_initialize(&certificate, certificate_data,
                                               certificate_buffer,
                                               sizeof(certificate_buffer), 500,
                                               private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_trusted_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-1330">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-1330">See Also</span></span>

- <span data-ttu-id="34a2c-1331">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-1331">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-1332">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-1332">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="34a2c-1333">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-1333">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="34a2c-1334">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="34a2c-1334">nx_secure_tls_trusted_certificate_remove</span></span>

## <a name="nx_secure_tls_trusted_certificate_remove"></a><span data-ttu-id="34a2c-1335">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="34a2c-1335">nx_secure_tls_trusted_certificate_remove</span></span>

<span data-ttu-id="34a2c-1336">Remover certificado fidedigno da Sessão TLS Do NetX Secure</span><span class="sxs-lookup"><span data-stu-id="34a2c-1336">Remove trusted certificate from NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-1337">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-1337">Prototype</span></span>

```C
UINT  nx_secure_tls_trusted_certificate_remove(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *common_name,
                                    UINT common_name_length);
```

### <a name="description"></a><span data-ttu-id="34a2c-1338">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-1338">Description</span></span>

<span data-ttu-id="34a2c-1339">Este serviço remove um certificado de confiança de uma sessão de TLS, insutado no campo Nome Comum no certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1339">This service removes a trusted certificate from a TLS session, keyed on the Common Name field in the certificate.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-1340">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-1340">Parameters</span></span>

- <span data-ttu-id="34a2c-1341">**session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1341">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="34a2c-1342">**common_name** O valor do nome comum do certificado a retirar.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1342">**common_name** The Common Name value of the certificate to be removed.</span></span>
- <span data-ttu-id="34a2c-1343">**common_name_length** O comprimento da corda nome comum.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1343">**common_name_length** The length of the Common Name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-1344">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-1344">Return Values</span></span>

- <span data-ttu-id="34a2c-1345">**NX_SUCCESS** (0x00) Adição bem sucedida do certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1345">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="34a2c-1346">**NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1346">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="34a2c-1347">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** certificado (0x119) não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1347">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Certificate was not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-1348">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-1348">Allowed From</span></span>

<span data-ttu-id="34a2c-1349">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-1349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-1350">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-1350">Example</span></span>

```C
/* Remove certificate from TLS session.  */
status =  nx_secure_tls_trusted_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-1351">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-1351">See Also</span></span>

- <span data-ttu-id="34a2c-1352">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-1352">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="34a2c-1353">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-1353">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="34a2c-1354">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-1354">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="34a2c-1355">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-1355">nx_secure_tls_trusted_certificate_add</span></span>

## <a name="nx_secure_x509_certificate_initialize"></a><span data-ttu-id="34a2c-1356">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-1356">nx_secure_x509_certificate_initialize</span></span>

<span data-ttu-id="34a2c-1357">Inicializar o Certificado X.509 para NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="34a2c-1357">Initialize X.509 Certificate for NetX Secure TLS</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-1358">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-1358">Prototype</span></span>

```C
UINT  nx_secure_x509_certificate_initialize(
                  NX_SECURE_X509_CERT *certificate_ptr,
                  const UCHAR *certificate_data,
                  USHORT certificate_data_length,
                  UCHAR *raw_data_buffer,
                  USHORT buffer_size,
                  const UCHAR *private_key_data,
                  USHORT private_key_data_length,
                  UINT private_key_type);
```

### <a name="description"></a><span data-ttu-id="34a2c-1359">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-1359">Description</span></span>

<span data-ttu-id="34a2c-1360">Este serviço inicializa uma estrutura NX_SECURE_X509_CERT a partir de um certificado digital X.509 codificado binário para utilização numa sessão de TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1360">This service initializes an NX_SECURE_X509_CERT structure from a binary-encoded X.509 digital certificate for use in a TLS session.</span></span>

<span data-ttu-id="34a2c-1361">Os dados do certificado **devem** ser um certificado digital X.509 válido em formato binário codificado pelo DER.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1361">The certificate data **must** be a valid X.509 digital certificate in DER-encoded binary format.</span></span> <span data-ttu-id="34a2c-1362">Os dados podem alguns de qualquer fonte (por exemplo, sistema de ficheiros, tampão constante compilado, etc.) desde que seja fornecido um ponteiro UCHAR para esses dados.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1362">The data can some from any source (e.g. file system, compiled constant buffer, etc.) as long as a UCHAR pointer to that data is provided.</span></span>

<span data-ttu-id="34a2c-1363">O *parâmetro raw_data_buffer* e o seu tamanho são parâmetros opcionais que especificam um tampão dedicado no qual os dados do certificado são copiados antes da análise.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1363">The *raw_data_buffer* parameter and its size are optional parameters that specify a dedicated buffer into which the certificate data is copied before parsing.</span></span> <span data-ttu-id="34a2c-1364">Se raw_data_buffer for passado como NX_NULL, então a estrutura NX_SECURE_X509_CERT apontará diretamente para a matriz certificate_data (buffer_size é ignorada neste caso).</span><span class="sxs-lookup"><span data-stu-id="34a2c-1364">If raw_data_buffer is passed as NX_NULL then the NX_SECURE_X509_CERT structure will point directly into the certificate_data array (buffer_size is ignored in this case).</span></span> <span data-ttu-id="34a2c-1365">Se raw_data_buffer for passado como NX_NULL, ***não*** modifique os dados apontados pelo ponteiro certificate_data ou o tratamento de certificados provavelmente falhará!</span><span class="sxs-lookup"><span data-stu-id="34a2c-1365">If raw_data_buffer is passed as NX_NULL, ***do not*** modify the data pointed to by the certificate_data pointer or certificate processing will likely fail!</span></span>

<span data-ttu-id="34a2c-1366">O parâmetro chave privado é para certificados de identidade locais – a chave privada é usada pelos servidores para desencriptar os dados chave de entrada de um cliente (encriptado usando a chave pública do servidor) e pelos clientes para verificar a sua identidade num servidor quando o servidor solicita um certificado de cliente.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1366">The private key parameter is for local identity certificates – the private key is used by servers to decrypt the incoming key data from a client (encrypted using the server's public key) and by clients to verify their identity to a server when the server requests a client certificate.</span></span> <span data-ttu-id="34a2c-1367">A adição de uma chave privada com esta API marcará automaticamente o certificado associado como sendo um certificado de identidade para um pedido TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1367">Adding a private key with this API will automatically mark the associated certificate as being an identity certificate for a TLS application.</span></span> <span data-ttu-id="34a2c-1368">Ao rubricar certificados para outros fins (por exemplo, a loja de confiança), o parâmetro *private_key_data* deve ser passado como NULO, o *private_key_data_length* como 0, e o *private_key_type* deve ser passado como NX_SECURE_X509_KEY_TYPE_NONE.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1368">When initializing certificates for other purposes (e.g. the trusted store), the *private_key_data* parameter should be passed as NULL, the *private_key_data_length* as 0, and the *private_key_type* should be passed as NX_SECURE_X509_KEY_TYPE_NONE.</span></span>

<span data-ttu-id="34a2c-1369">O *parâmetro private_key_type* indica a formatação da chave privada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1369">The *private_key_type* parameter indicates the formatting of the private key.</span></span> <span data-ttu-id="34a2c-1370">Por exemplo, se a chave privada for uma chave privada RSA codificada por PKCS#1, o private_key_type deve ser passado como NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER, um tipo conhecido por NetX Secure que será analisado imediatamente e guardado para posterior utilização.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1370">For example, if the private key is a DER-encoded PKCS#1-format RSA private key, the private_key_type should be passed as NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER, a type known to NetX Secure which will be parsed immediately and saved for later use.</span></span>

<span data-ttu-id="34a2c-1371">O private_key_type também suporta os tipos de chave definidos pelo utilizador<sup>23</sup> para plataformas e aplicações que possuam formatos-chave específicos ou outras necessidades.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1371">The private_key_type also supports user-defined key types<sup>23</sup> for platforms and applications that have specific key formats or other needs.</span></span> <span data-ttu-id="34a2c-1372">Por exemplo, um motor de encriptação baseado em hardware pode usar um formato específico não compreendido pelo software NetX Secure, ou uma chave privada pode ser encriptada ou representada por um token criptográfico, como pode acontecer com um Módulo de Plataforma Fidedigna (TPM) ou hardware criptográfico PKCS#11.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1372">For example, a hardware-based encryption engine may use a specific format not understood by the NetX Secure software, or a private key may be encrypted or represented by a cryptographic token as might be the case with a Trusted Platform Module (TPM) or PKCS#11 cryptographic hardware.</span></span> <span data-ttu-id="34a2c-1373">Quando um tipo de chave definido pelo utilizador é utilizado, os dados-chave são transmitidos verbatim à rotina criptográfica apropriada - por exemplo, uma chave privada RSA seria passada, sem qualquer análise ou processamento, diretamente para a rotina criptográfica RSA fornecida ao TLS na tabela de cifrasuite.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1373">When a user-defined key type is used, the key data is passed verbatim to the appropriate cryptographic routine - for example, an RSA private key would be passed, without any parsing or processing, directly to the RSA cryptographic routine provided to TLS in the ciphersuite table.</span></span> <span data-ttu-id="34a2c-1374">O tipo de chave definida pelo utilizador também é passado para a rotina criptográfica (no caso da RSA, este é o parâmetro "op").</span><span class="sxs-lookup"><span data-stu-id="34a2c-1374">The user-defined key type is also passed to the cryptographic routine (in the case of RSA, this is the "op" parameter).</span></span>

<span data-ttu-id="34a2c-1375">A gama de teclas definidas pelo utilizador cobre a metade superior de um número inteiro não assinado de 32 bits, de 0x0001 FFFF de 0000 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1375">The range of user-defined keys covers the top half of a 32-bit unsigned integer, from 0x0001 0000-0xFFFF FFFF.</span></span> <span data-ttu-id="34a2c-1376">Valores inferiores 0x0001 0000 estão reservados para utilização NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1376">Values less than 0x0001 0000 are reserved for NetX Secure use.</span></span>

<span data-ttu-id="34a2c-1377">Os tipos de chaves definidos pelo utilizador são uma funcionalidade avançada que requer rotinas criptográficas personalizadas para lidar com os dados de chave privadas cruas.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1377">User-defined key types are an advanced feature that requires custom cryptographic routines to handle the raw private key data.</span></span> <span data-ttu-id="34a2c-1378">Contacte o seu representante express logic se precisar desta funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1378">Please contact your Express Logic representative if you have need of this feature.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-1379">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-1379">Parameters</span></span>

- <span data-ttu-id="34a2c-1380">**certificate_ptr** Ponteiro para uma instância de certificado X.509 não ininitializada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1380">**certificate_ptr** Pointer to an uninitialized X.509 Certificate instance.</span></span>
- <span data-ttu-id="34a2c-1381">**certificate_data** Ponteiro para dados binários de X.509 codificados pelo DER.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1381">**certificate_data** Pointer to DER-encoded X.509 binary data.</span></span>
- <span data-ttu-id="34a2c-1382">**raw_data_buffer** Ponteiro para o tampão de dados de certificado dedicado opcional.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1382">**raw_data_buffer** Pointer to optional dedicated certificate data buffer.</span></span>
- <span data-ttu-id="34a2c-1383">**buffer_size** Tamanho do tampão de dados de certificado dedicado opcional.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1383">**buffer_size** Size of optional dedicated certificate data buffer.</span></span>
- <span data-ttu-id="34a2c-1384">**certificate_data_length** Duração dos dados binários de certificados em bytes.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1384">**certificate_data_length** Length of certificate binary data in bytes.</span></span>
- <span data-ttu-id="34a2c-1385">**private_key_data** Ponteiro para dados chave privados opcionais.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1385">**private_key_data** Pointer to optional private key data.</span></span>
- <span data-ttu-id="34a2c-1386">**private_key_data_length** Duração dos dados das chaves privadas.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1386">**private_key_data_length** Length of private key data.</span></span>
- <span data-ttu-id="34a2c-1387">**private_key_type** Identificador do tipo chave.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1387">**private_key_type** Key type identifier.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-1388">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-1388">Return Values</span></span>

- <span data-ttu-id="34a2c-1389">**NX_SUCCESS** (0x00) Adição bem sucedida do certificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1389">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="34a2c-1390">**NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1390">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="34a2c-1391">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) Os dados do certificado não continham um certificado X.509 codificado pelo DER.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1391">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) Certificate data did not contain a DER-encoded X.509 certificate.</span></span>
- <span data-ttu-id="34a2c-1392">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** certificado (0x10D) não tinha uma cifra de chave pública que é suportada pela NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1392">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) Certificate did not have a public-key cipher that is supported by NetX Secure.</span></span>
- <span data-ttu-id="34a2c-1393">**NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** (0x186) A chave ou certificado privado não continha uma sequência ASN.1 válida.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1393">**NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** (0x186) Private key or certificate did not contain a valid ASN.1 sequence.</span></span>
- <span data-ttu-id="34a2c-1394">**NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** (0x18A) A chave privada fornecida não era uma chave PKCS#1 RSA válida.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1394">**NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** (0x18A) The provided private key was not a valid PKCS#1 RSA key.</span></span>
- <span data-ttu-id="34a2c-1395">**NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** (0x19D) O tipo de chave privada fornecido não foi definido pelo utilizador e não corresponde a qualquer tipo conhecido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1395">**NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** (0x19D) The private key type provided was not user-defined and did not match any known type.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-1396">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-1396">Allowed From</span></span>

<span data-ttu-id="34a2c-1397">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-1397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-1398">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-1398">Example</span></span>

```C
/* Initialize certificate structure. The certificate structure will point directly
   into the certificate_data array since we are passing the raw_data_buffer as
   NX_NULL. This certificate has a private key so it will be used to identify this
   device. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, NX_NULL, 0, private_key, 64, NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);


/* If status is NX_SUCCESS the certificate was successfully initialized.  */
```

### <a name="see-also"></a><span data-ttu-id="34a2c-1399">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-1399">See Also</span></span>

- <span data-ttu-id="34a2c-1400">nx_secure_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="34a2c-1400">nx_secure_local_certificate_add</span></span>
- <span data-ttu-id="34a2c-1401">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-1401">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="34a2c-1402">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="34a2c-1402">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="34a2c-1403">Importar certificados X.509 para NetX Secure no capítulo 3.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1403">Importing X.509 Certificates into NetX Secure in Chapter 3.</span></span>

## <a name="nx_secure_x509_common_name_dns_check"></a><span data-ttu-id="34a2c-1404">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="34a2c-1404">nx_secure_x509_common_name_dns_check</span></span>

<span data-ttu-id="34a2c-1405">Verifique o nome DNS contra o Certificado X.509</span><span class="sxs-lookup"><span data-stu-id="34a2c-1405">Check DNS name against X.509 Certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-1406">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-1406">Prototype</span></span>

```C
UINT  nx_secure_x509_common_name_dns_check(
                        NX_SECURE_X509_CERT *certificate,
                        const UCHAR *dns_tld, UINT dns_tld_length);
```

### <a name="description"></a><span data-ttu-id="34a2c-1407">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-1407">Description</span></span>

<span data-ttu-id="34a2c-1408">Este serviço verifica o Nome Comum de um certificado contra um nome de domínio superior (TLD) fornecido pelo chamador para efeitos de validação de DNS de um anfitrião remoto.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1408">This service checks a certificate's Common Name against a Top- Domain name (TLD) provided by the caller for the purposes of DNS validation of a remote host.</span></span> <span data-ttu-id="34a2c-1409">Esta função de utilidade destina-se a ser chamada a partir de uma rotina de validação de certificado fornecida pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1409">This utility function is intended to be called from within a certificate validation callback routine provided by the application.</span></span> <span data-ttu-id="34a2c-1410">O nome TLD deve ser a parte superior do URL utilizado para aceder ao hospedeiro remoto (o "". -corda separada antes do primeiro corte).</span><span class="sxs-lookup"><span data-stu-id="34a2c-1410">The TLD name should be the top part of the URL used to access the remote host (the "."-separated string before the first slash).</span></span> <span data-ttu-id="34a2c-1411">Se o Nome Comum contiver um wildcard (como *.example.com), o wildcard combinará qualquer um com o mesmo sufixo. Note que apenas o primeiro wildcard ("*") encontrado (lendo da direita para a esquerda) será considerado para correspondência wildcard – por exemplo, abc.\*.exemplo.com corresponderá *a qualquer* nome que termine em ".example.com".</span><span class="sxs-lookup"><span data-stu-id="34a2c-1411">If the Common Name contains a wildcard (such as *.example.com), the wildcard will match any with the same suffix. Note that only the first wildcard ("*") encountered (reading right-to-left) will be considered for wildcard matching – for example, abc.\*.example.com will match *any* name ending in ".example.com".</span></span>

<span data-ttu-id="34a2c-1412">Se o Nome Comum não corresponder à cadeia fornecida, a extensão "subjectAltName" é analisada (se existir no certificado) e são também comparadas quaisquer entradas DNSName.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1412">If the Common Name does not match the provided string, the "subjectAltName" extension is parsed (if it exists in the certificate) and any DNSName entries are also compared.</span></span> <span data-ttu-id="34a2c-1413">Se nenhuma dessas entradas corresponder, um erro é devolvido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1413">If none of those entries match, an error is returned.</span></span>

<span data-ttu-id="34a2c-1414">É importante compreender o formato do nome comum (e submeter entradas de NomeAlt) nos certificados esperados.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1414">It is important to understand the format of the common name (and subjectAltName entries) in expected certificates.</span></span> <span data-ttu-id="34a2c-1415">Por exemplo, alguns certificados podem usar um endereço IP cru ou um wild card.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1415">For example, some certificates may use a raw IP address or a wild card.</span></span> <span data-ttu-id="34a2c-1416">A cadeia DNS TLD deve ser formatada de modo a corresponder aos valores esperados nos certificados recebidos.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1416">The DNS TLD string must be formatted such that it will match the expected values in received certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-1417">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-1417">Parameters</span></span>

- <span data-ttu-id="34a2c-1418">**certificate_ptr** Ponteiro para uma instância de certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1418">**certificate_ptr** Pointer to an X.509 Certificate instance.</span></span>
- <span data-ttu-id="34a2c-1419">**dns_tld** Top-Level nome de domínio para comparar.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1419">**dns_tld** Top-Level Domain name to compare against.</span></span>
- <span data-ttu-id="34a2c-1420">**dns_tld_length** Comprimento da corda TLD.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1420">**dns_tld_length** Length of TLD string.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-1421">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-1421">Return Values</span></span>

- <span data-ttu-id="34a2c-1422">**NX_SUCCESS** (0x00) Comparação bem sucedida com nome comum ou nome sujeitoAlme.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1422">**NX_SUCCESS** (0x00) Successful comparison with Common Name or subjectAltName.</span></span>
- <span data-ttu-id="34a2c-1423">**NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** (0x195) Não foi encontrado nenhum nome correspondente.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1423">**NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** (0x195) No matching name found.</span></span>
- <span data-ttu-id="34a2c-1424">**NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1424">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-1425">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-1425">Allowed From</span></span>

<span data-ttu-id="34a2c-1426">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-1426">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-1427">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-1427">Example</span></span>

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
UCHAR *tld = “www.example.com”;

    /* Check our DNS TLD against the certificate provided by the
       remote TLS host. */
    status = nx_secure_x509_common_name_dns_check(certificate, tld, strlen(tld));

        if(status != NX_SUCCESS)
        {
            /* TLD did not match any names in the certificate. */
            return(status);
        }

        /* DNS validation and any other checks were successful. */
        return(NX_SUCCESS);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a><span data-ttu-id="34a2c-1428">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-1428">See Also</span></span>

- <span data-ttu-id="34a2c-1429">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-1429">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="34a2c-1430">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-1430">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="34a2c-1431">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="34a2c-1431">nx_secure_x509_crl_revocation_check</span></span>

## <a name="nx_secure_x509_crl_revocation_check"></a><span data-ttu-id="34a2c-1432">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="34a2c-1432">nx_secure_x509_crl_revocation_check</span></span>

<span data-ttu-id="34a2c-1433">Verifique o Certificado X.509 com uma Lista de Revogação de Certificados (CRL)</span><span class="sxs-lookup"><span data-stu-id="34a2c-1433">Check X.509 Certificate against a supplied Certificate Revocation List (CRL)</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-1434">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-1434">Prototype</span></span>

```C
UINT  nx_secure_x509_crl_revocation_check(const UCHAR *crl_data,
                              UINT crl_length,
                              NX_SECURE_X509_CERTIFICATE_STORE *store,
                              NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a><span data-ttu-id="34a2c-1435">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-1435">Description</span></span>

<span data-ttu-id="34a2c-1436">Este serviço requer uma Lista de Revogação de Certificado codificada pelo DER e procura um certificado específico nessa lista.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1436">This service takes a DER-encoded Certificate Revocation List and searches for a specific certificate in that list.</span></span> <span data-ttu-id="34a2c-1437">O emitente do CRL é validado contra uma loja de certificados fornecida, o emitente CRL é validado para ser o mesmo que o certificado que está a ser verificado, e o número de série do certificado em questão é utilizado para pesquisar a lista de certificados revogados.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1437">The issuer of the CRL is validated against a supplied certificate store, the CRL issuer is validated to be the same as the one for the certificate being checked, and the serial number of the certificate in question is used to search the revoked certificates list.</span></span> <span data-ttu-id="34a2c-1438">Se os emitentes coincidirem, a assinatura confere e o certificado **não** está presente na lista, a chamada é bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1438">If the issuers match, the signature checks out, and the certificate is **not** present in the list, the call is successful.</span></span> <span data-ttu-id="34a2c-1439">Todos os outros casos causam um erro a ser devolvido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1439">All other cases cause an error to be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-1440">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-1440">Parameters</span></span>

- <span data-ttu-id="34a2c-1441">**crl_data** Ponteiro para um CRL codificado pelo DER.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1441">**crl_data** Pointer to a DER-encoded CRL.</span></span>
- <span data-ttu-id="34a2c-1442">**crl_length** Comprimento em bytes de dados CRL.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1442">**crl_length** Length in bytes of CRL data.</span></span>
- <span data-ttu-id="34a2c-1443">**loja** Ponteiro para uma loja de certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1443">**store** Pointer to an X.509 Certificate store.</span></span>
- <span data-ttu-id="34a2c-1444">**certificate_ptr** Ponteiro para uma instância de certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1444">**certificate_ptr** Pointer to an X.509 Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-1445">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-1445">Return Values</span></span>

- <span data-ttu-id="34a2c-1446">**NX_SUCCESS** (0x00) Validação bem sucedida de que o certificado não foi revogado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1446">**NX_SUCCESS** (0x00) Successful validation that the certificate was not revoked.</span></span>
- <span data-ttu-id="34a2c-1447">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) certificado de emitente CRL não encontrado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1447">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) CRL issuer certificate not found.</span></span>
- <span data-ttu-id="34a2c-1448">**NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** 0x11B) Certificado emitente de certificado não encontrado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1448">**NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** 0x11B) Certificate issuer certificate not found.</span></span>
- <span data-ttu-id="34a2c-1449">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) O CRL ASN.1 continha um campo de comprimento inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1449">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) The CRL ASN.1 contained an invalid length field.</span></span>
- <span data-ttu-id="34a2c-1450">**NX_SECURE_X509_UNEXPECTED_ASN1_TAG(0x189)** O CRL continha ASN.1 inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1450">**NX_SECURE_X509_UNEXPECTED_ASN1_TAG(0x189)** The CRL contained invalid ASN.1.</span></span>
- <span data-ttu-id="34a2c-1451">**NX_SECURE_X509_CHAIN_VERIFY_FAILURE** (0x18C) Uma verificação da cadeia de certificados falhou.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1451">**NX_SECURE_X509_CHAIN_VERIFY_FAILURE** (0x18C) A certificate chain verification failed.</span></span>
- <span data-ttu-id="34a2c-1452">**NX_SECURE_X509_CRL_ISSUER_MISMATCH** (0x197) CRL e emitentes de certificados não correspondia.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1452">**NX_SECURE_X509_CRL_ISSUER_MISMATCH** (0x197) CRL and certificate issuers did not match.</span></span>
- <span data-ttu-id="34a2c-1453">**NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** 0x198) A assinatura CRL foi inválida.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1453">**NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** 0x198) The CRL signature was invalid.</span></span>
- <span data-ttu-id="34a2c-1454">**NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** (0x199) O certificado que está a ser verificado foi encontrado no CRL e, por conseguinte, revogado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1454">**NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** (0x199) The certificate being checked was found in the CRL and is therefore revoked.</span></span>
- <span data-ttu-id="34a2c-1455">**NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1455">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-1456">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-1456">Allowed From</span></span>

<span data-ttu-id="34a2c-1457">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-1457">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-1458">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-1458">Example</span></span>

```C
/* CRL obtained for the expected certificate issuer through some means (downloaded
   from server manually, obtained from CRL endpoint, etc…) */
const UCHAR *crl_data;
UINT crl_length = 300;

/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
NX_SECURE_X509_CERTIFICATE_STORE *store;

    /* Obtain a certificate store to check against. In the certificate callback,
       it usually makes the most sense to use the store associated with the TLS
       session. */
    store = &session -> nx_secure_tls_credentials.nx_secure_tls_certificate_store;

    /* Check our certificate against the CRL and TLS certificate store. */
    status = nx_secure_x509_crl_revocation_check(crl, crl_length, store,
                                                 certificate);

        if(status != NX_SUCCESS)
        {
            if(status == NX_SECURE_X509_CRL_CERTIFICATE_REVOKED)
            {
                /* Certificate was revoked. */
               return(status);
            }
            else
            {
               /* CRL was invalid or some other issue. In this case the certificate
                  may still be valid since the CRL itself was a problem. At this
                  point it is up to the application to decide whether to continue
                  with the TLS handshake. For this example, assume certificate is
                  valid (faulty CRL is a possible Denial-of-Service attack).*/
               status = NX_SUCCESS;
        }

    /* Other certificate checking can go here. */

    /* Return status of certificate checks. */
    return(status);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a><span data-ttu-id="34a2c-1459">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-1459">See Also</span></span>

- <span data-ttu-id="34a2c-1460">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-1460">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="34a2c-1461">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-1461">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="34a2c-1462">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="34a2c-1462">nx_secure_x509_common_name_dns_check</span></span>

## <a name="nx_secure_x509_dns_name_initialize"></a><span data-ttu-id="34a2c-1463">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="34a2c-1463">nx_secure_x509_dns_name_initialize</span></span>

<span data-ttu-id="34a2c-1464">Inicialize uma estrutura de nomeS DNS X.509</span><span class="sxs-lookup"><span data-stu-id="34a2c-1464">Initialize an X.509 DNS name structure</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-1465">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-1465">Prototype</span></span>

```C
UINT  nx_secure_x509_dns_name_initialize(
                        NX_SECURE_X509_DNS_NAME *dns_name,
                        const UCHAR *name_string, UINT length);
```

### <a name="description"></a><span data-ttu-id="34a2c-1466">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-1466">Description</span></span>

<span data-ttu-id="34a2c-1467">Este serviço inicializa um nome DNS X.509 para utilização com certos serviços API que requerem um formato de nome específico.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1467">This service initializes an X.509 DNS name for use with certain API services requiring a specific name format.</span></span> <span data-ttu-id="34a2c-1468">Por exemplo, o serviço *nx_secure_tls_sni_extension_parse* espera que um objeto NX_SECURE_X509_DNS_NAME para corresponder ao nome fornecido por um anfitrião remoto na extensão de indicação de nome do servidor durante o aperto de mão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1468">For example, the *nx_secure_tls_sni_extension_parse* service expects an NX_SECURE_X509_DNS_NAME object in order to match the name provided by a remote host in the Server Name Indication extension during the TLS handshake.</span></span> <span data-ttu-id="34a2c-1469">Um nome DNS é simplesmente uma corda de charater com um comprimento – o comprimento máximo permitido de um nome DNS (e o tamanho do tampão interno em NX_SECURE_X509_DNS_NAME) é controlado pelo NX_SECURE_X509_DNS_NAME_MAX macro (padrão 100 bytes).</span><span class="sxs-lookup"><span data-stu-id="34a2c-1469">A DNS name is simply a charater string with a length – the maximum allowed length of a DNS name (and the size of the internal buffer in NX_SECURE_X509_DNS_NAME) is controlled by the macro NX_SECURE_X509_DNS_NAME_MAX (default 100 bytes).</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-1470">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-1470">Parameters</span></span>

- <span data-ttu-id="34a2c-1471">**dns_name** Estrutura de nome DNS para inicializar.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1471">**dns_name** DNS name structure to initialize.</span></span>
- <span data-ttu-id="34a2c-1472">**name_string** Dados de cadeia de nome DNS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1472">**name_string** DNS name string data.</span></span>
- <span data-ttu-id="34a2c-1473">**comprimento** Comprimento da corda do nome.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1473">**length** Length of name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-1474">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-1474">Return Values</span></span>

- <span data-ttu-id="34a2c-1475">**NX_SUCCESS** (0x00) Inicialização bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1475">**NX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="34a2c-1476">**NX_SECURE_X509_NAME_STRING_TOO_LONG** (0x19E) A cadeia de nomes foi excedida NX_SECURE_X509_DNS_NAME_MAX.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1476">**NX_SECURE_X509_NAME_STRING_TOO_LONG** (0x19E) The given name string exceeded NX_SECURE_X509_DNS_NAME_MAX.</span></span>
- <span data-ttu-id="34a2c-1477">**NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1477">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-1478">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-1478">Allowed From</span></span>

<span data-ttu-id="34a2c-1479">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-1479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-1480">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-1480">Example</span></span>

```C
NX_SECURE_X509_DNS_NAME dns_name;

/* Initialize DNS name. */
status = nx_secure_x509_dns_name_initialize(&dns_name, “www.example.com”,
                                            strlen(“www.example.com”);

/* Use initialized DNS name to send the Server Name Indication extension to the
   remote TLS server. */
status = nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);
```

### <a name="see-also"></a><span data-ttu-id="34a2c-1481">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-1481">See Also</span></span>

- <span data-ttu-id="34a2c-1482">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="34a2c-1482">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="34a2c-1483">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="34a2c-1483">nx_secure_tls_session_sni_extension_parse</span></span>
- <span data-ttu-id="34a2c-1484">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-1484">nx_secure_tls_session_sni_extension_set</span></span>

## <a name="nx_secure_x509_extended_key_usage_extension_parse"></a><span data-ttu-id="34a2c-1485">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="34a2c-1485">nx_secure_x509_extended_key_usage_extension_parse</span></span>

<span data-ttu-id="34a2c-1486">Encontre e analise uma extensão de utilização estendida X.509 num certificado X.509</span><span class="sxs-lookup"><span data-stu-id="34a2c-1486">Find and parse an X.509 extended key usage extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-1487">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-1487">Prototype</span></span>

```C
UINT  nx_secure_x509_extended_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        UINT key_usage);
```

### <a name="description"></a><span data-ttu-id="34a2c-1488">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-1488">Description</span></span>

<span data-ttu-id="34a2c-1489">Este serviço destina-se a ser chamado a partir de uma chamada de verificação de certificado (ver *nx_secure_tls_session_certificate_callback_set)*.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1489">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)*.</span></span> <span data-ttu-id="34a2c-1490">Procurará uma chave específica de utilização OID dentro de um certificado X.509 e devolverá se o OID está presente.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1490">It will search for a specific extended key usage OID within an X.509 certificate and return whether the OID is present.</span></span> <span data-ttu-id="34a2c-1491">O parâmetro key_usage é um mapeamento inteiro dos OIDs que é usado internamente por NetX Secure X.509 e TLS para evitar passar as cordas OID de comprimento variável como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1491">The key_usage parameter is an integer mapping of the OIDs which is used internally by NetX Secure X.509 and TLS to avoid passing the variable-length OID strings as parameters.</span></span>

<span data-ttu-id="34a2c-1492">Os OIDs relevantes para a extensão de utilização da chave estendida são indicados na tabela abaixo.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1492">The relevant OIDs for the extended key usage extension are given in the table below.</span></span> <span data-ttu-id="34a2c-1493">Uma implementação típica do Cliente TLS que pretenda verificar a utilização de chaves estendidas num certificado de servidor TLS recebido verificaria a existência do NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH OID – se a extensão estiver presente mas que o OID não estiver, então o certificado seria considerado inválido para identificar o anfitrião como um servidor TLS e a chamada de verificação do certificado deve devolver um erro.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1493">A typical TLS Client implementation wishing to check extended key usage in a received TLS server certificate would check for the existence of the OID NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH – if the extension is present but that OID is not, then the certificate would be considered invalid for identifiying the host as a TLS server and the certificate verification callback should return an error.</span></span> <span data-ttu-id="34a2c-1494">Se a extensão em si faltar, então cabe à aplicação proceder ou não com o aperto de mão TLS.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1494">If the extension itself is missing, then it is up to the application whether or not to proceed with the TLS handshake.</span></span>

<span data-ttu-id="34a2c-1495">Na chamada de verificação do certificado, o código de devolução de erros NX_SECURE_X509_KEY_USAGE_ERROR está reservado para utilização de pedidos.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1495">In the certificate verification callback, the error return code NX_SECURE_X509_KEY_USAGE_ERROR is reserved for application use.</span></span> <span data-ttu-id="34a2c-1496">Se houver um erro na verificação da utilização da chave, este valor pode ser devolvido da chamada para indicar o motivo da falha.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1496">If there is an error in checking key usage, this value may be returned from the callback to indicate the reason for failure.</span></span>

| <span data-ttu-id="34a2c-1497">Identificador de segurança NetX</span><span class="sxs-lookup"><span data-stu-id="34a2c-1497">NetX Secure Identifier</span></span>                                | <span data-ttu-id="34a2c-1498">Valor OID</span><span class="sxs-lookup"><span data-stu-id="34a2c-1498">OID Value</span></span>         | <span data-ttu-id="34a2c-1499">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-1499">Description</span></span>                                      |
| --------------------------------------------------------- | --------------------- | ---------------------------------------------------- |
| <span data-ttu-id="34a2c-1500">NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH</span><span class="sxs-lookup"><span data-stu-id="34a2c-1500">NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH</span></span>   | <span data-ttu-id="34a2c-1501">1.3.6.1.5.5.7.3.1</span><span class="sxs-lookup"><span data-stu-id="34a2c-1501">1.3.6.1.5.5.7.3.1</span></span> | <span data-ttu-id="34a2c-1502">O certificado pode ser usado para identificar um servidor TLS</span><span class="sxs-lookup"><span data-stu-id="34a2c-1502">Certificate can be used to identify a TLS server</span></span> |
| <span data-ttu-id="34a2c-1503">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH</span><span class="sxs-lookup"><span data-stu-id="34a2c-1503">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH</span></span>   | <span data-ttu-id="34a2c-1504">1.3.6.1.5.5.7.3.2</span><span class="sxs-lookup"><span data-stu-id="34a2c-1504">1.3.6.1.5.5.7.3.2</span></span> | <span data-ttu-id="34a2c-1505">O certificado pode ser usado para identificar um cliente TLS</span><span class="sxs-lookup"><span data-stu-id="34a2c-1505">Certificate can be used to identify a TLS client</span></span> |
| <span data-ttu-id="34a2c-1506">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING</span><span class="sxs-lookup"><span data-stu-id="34a2c-1506">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING</span></span>  | <span data-ttu-id="34a2c-1507">1.3.6.1.5.5.7.3.3</span><span class="sxs-lookup"><span data-stu-id="34a2c-1507">1.3.6.1.5.5.7.3.3</span></span> | <span data-ttu-id="34a2c-1508">O certificado pode ser usado para assinar código</span><span class="sxs-lookup"><span data-stu-id="34a2c-1508">Certificate can be used to sign code</span></span>             |
| <span data-ttu-id="34a2c-1509">NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT</span><span class="sxs-lookup"><span data-stu-id="34a2c-1509">NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT</span></span> | <span data-ttu-id="34a2c-1510">1.3.6.1.5.5.7.3.4</span><span class="sxs-lookup"><span data-stu-id="34a2c-1510">1.3.6.1.5.5.7.3.4</span></span> | <span data-ttu-id="34a2c-1511">O certificado pode ser usado para assinar e-mails</span><span class="sxs-lookup"><span data-stu-id="34a2c-1511">Certificate can be used to sign emails</span></span>           |
| <span data-ttu-id="34a2c-1512">NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING</span><span class="sxs-lookup"><span data-stu-id="34a2c-1512">NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING</span></span> | <span data-ttu-id="34a2c-1513">1.3.6.1.5.5.7.3.8</span><span class="sxs-lookup"><span data-stu-id="34a2c-1513">1.3.6.1.5.5.7.3.8</span></span> | <span data-ttu-id="34a2c-1514">O certificado pode ser usado para assinar os tempos dos tempos</span><span class="sxs-lookup"><span data-stu-id="34a2c-1514">Certificate can be used to sign timestamps</span></span>       |
| <span data-ttu-id="34a2c-1515">NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING</span><span class="sxs-lookup"><span data-stu-id="34a2c-1515">NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING</span></span>  | <span data-ttu-id="34a2c-1516">1.3.6.1.5.5.7.3.9</span><span class="sxs-lookup"><span data-stu-id="34a2c-1516">1.3.6.1.5.5.7.3.9</span></span> | <span data-ttu-id="34a2c-1517">O certificado pode ser usado para assinar respostas OCSP</span><span class="sxs-lookup"><span data-stu-id="34a2c-1517">Certificate can be used to sign OCSP responses</span></span>   |

<span data-ttu-id="34a2c-1518">OIDs e mapeamentos para X.509 Extensão de Utilização de Chave Estendida</span><span class="sxs-lookup"><span data-stu-id="34a2c-1518">OIDs and mappings for X.509 Extended Key Usage Extension</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-1519">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-1519">Parameters</span></span>

- <span data-ttu-id="34a2c-1520">**certificado** Ponteiro para certificado sendo verificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1520">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="34a2c-1521">**key_usage** Mapeamento inteiro OID da tabela acima.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1521">**key_usage** OID integer mapping from table above.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-1522">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-1522">Return Values</span></span>

- <span data-ttu-id="34a2c-1523">**NX_SUCCESS** (0x00) Utilização de chave especificada OID encontrada.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1523">**NX_SUCCESS** (0x00) Specified key usage OID found.</span></span>
- <span data-ttu-id="34a2c-1524">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 tag multi-byte encontrada (certificado não suportado).</span><span class="sxs-lookup"><span data-stu-id="34a2c-1524">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="34a2c-1525">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Campo Invaild ASN.1 encontrado (certificado inválido).</span><span class="sxs-lookup"><span data-stu-id="34a2c-1525">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="34a2c-1526">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Classe de tag ASN.1 inválida encontrada (certificado inválido).</span><span class="sxs-lookup"><span data-stu-id="34a2c-1526">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="34a2c-1527">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Extensão inválida encontrada (certificado inválido).</span><span class="sxs-lookup"><span data-stu-id="34a2c-1527">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered (invalid certificate).</span></span>
- <span data-ttu-id="34a2c-1528">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) A extensão de utilização da chave estendida não foi encontrada no certificado fornecido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1528">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) The Extended Key Usage extension was not found in the provided certificate.</span></span>
- <span data-ttu-id="34a2c-1529">**NX_PTR_ERROR** (0x07) Ponteiro de certificado inválido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1529">**NX_PTR_ERROR** (0x07) Invalid certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-1530">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-1530">Allowed From</span></span>

<span data-ttu-id="34a2c-1531">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-1531">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-1532">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-1532">Example</span></span>

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT* certificate)
{
UINT status;

    /* Extended key usage - look for specific OIDs. */
    status = nx_secure_x509_extended_key_usage_extension_parse(certificate,
                        NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH);

    if(status != NX_SUCCESS)
    {
        if(NX_SECURE_X509_EXT_KEY_USAGE_NOT_FOUND)
        {
            printf("Extended key usage extension not found or specified key usage OID not
                    provided in extension.\n");
            /* The certificate was valid but the specified OID was not found. The
               application can decide whether to continue or abort the TLS handshake. */
            return(NX_SECURE_X509_KEY_USAGE_ERROR);
        }
        else
        {
            /* The extension or certificate was invalid. */
            return(status);
        }
    }

    /* The specified OID was found, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="34a2c-1533">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-1533">See Also</span></span>

- <span data-ttu-id="34a2c-1534">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-1534">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="34a2c-1535">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="34a2c-1535">nx_secure_x509_key_usage_extension_parse</span></span>
- <span data-ttu-id="34a2c-1536">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="34a2c-1536">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="34a2c-1537">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="34a2c-1537">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="34a2c-1538">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="34a2c-1538">nx_secure_x509_extension_find</span></span>

## <a name="nx_secure_x509_extension_find"></a><span data-ttu-id="34a2c-1539">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="34a2c-1539">nx_secure_x509_extension_find</span></span>

<span data-ttu-id="34a2c-1540">Encontre e devolva uma extensão X.509 num certificado X.509</span><span class="sxs-lookup"><span data-stu-id="34a2c-1540">Find and return an X.509 extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-1541">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-1541">Prototype</span></span>

```C
UINT  nx_secure_x509_extension_find(
                        NX_SECURE_X509_CERT *certificate,
                        NX_SECURE_X509_EXTENSION *extension,
                        USHORT extension_id);
```

### <a name="description"></a><span data-ttu-id="34a2c-1542">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-1542">Description</span></span>

<span data-ttu-id="34a2c-1543">Este serviço destina-se a ser chamado a partir de uma chamada de verificação de certificado (ver *nx_secure_tls_session_certificate_callback_set)* e é um serviço avançado X.509.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1543">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)* and is an advanced X.509 service.</span></span>

<span data-ttu-id="34a2c-1544">A função procurará uma extensão específica dentro de um certificado X.509 com base num OID e devolverá se o OID está presente, juntamente com uma estrutura que contém referências aos dados de extensão bruta relevantes.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1544">The function will search for a specific extension within an X.509 certificate based on an OID and return whether the OID is present, along with a structure containing references to the relevant raw extension data.</span></span> <span data-ttu-id="34a2c-1545">O parâmetro extension_id é um mapeamento inteiro dos OIDs que é usado internamente por NetX Secure X.509 e TLS para evitar passar as cordas OID de comprimento variável como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1545">The extension_id parameter is an integer mapping of the OIDs which is used internally by NetX Secure X.509 and TLS to avoid passing the variable-length OID strings as parameters.</span></span>

<span data-ttu-id="34a2c-1546">As funções de ajudante previstas para extensões específicas (como *nx_secure_x509_key_usage_extension_parse*) chamam nx_secure_x509_extension_find internamente para obter os dados de extensão.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1546">The helper functions provided for specific extensions (such as *nx_secure_x509_key_usage_extension_parse*) call nx_secure_x509_extension_find internally to obtain the extension data.</span></span>

<span data-ttu-id="34a2c-1547">Os OIDs relevantes para extensões conhecidas de X.509 são indicados na tabela abaixo.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1547">The relevant OIDs for known X.509 extensions are given in the table below.</span></span>

<span data-ttu-id="34a2c-1548">A estrutura NX_SECURE_X509_EXTENSION contém ponteiros no certificado X.509 que permitem que funções de ajudante, tais como *nx_secure_x509_key_usage_extension_parse,* descodificem rapidamente os dados ASN.1 codificados pela extensão bruta DER.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1548">The NX_SECURE_X509_EXTENSION structure contains pointers into the X.509 certificate that allow helper functions such as *nx_secure_x509_key_usage_extension_parse* to quickly decode the raw extension DER-encoded ASN.1 data.</span></span>

<span data-ttu-id="34a2c-1549">Para obter informações sobre extensões específicas, consulte RFC 5280 (especificação X.509) ou a referência para as funções de ajudante adequadas, se disponível.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1549">For information on specific extensions, see RFC 5280 (X.509 specification) or the reference for the appropriate helper functions if available.</span></span>

<span data-ttu-id="34a2c-1550">A versão atual do NetX Secure X.509 tem suporte limitado para extensões X.509.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1550">The current version of NetX Secure X.509 has limited support for X.509 extensions.</span></span> <span data-ttu-id="34a2c-1551">No futuro, serão adicionadas mais funções de ajudante.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1551">More helper functions will be added in the future.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34a2c-1552">*Este serviço é uma funcionalidade avançada para utilizadores familiarizados com extensões X.509 e ASN.1 codificadas por DER. É fornecido para permitir que esses utilizadores acedam a extensões para as quais o NetX Secure X.509 não fornece atualmente funções de ajudante. Para essas extensões sem funções de ajudante, você mesmo terá de analisar o ASN.1 codificado em bruto.*</span><span class="sxs-lookup"><span data-stu-id="34a2c-1552">*This service is an advanced feature for users familiar with X.509 extensions and DER-encoded ASN.1. It is provided to enable those users to access extensions for which NetX Secure X.509 does not currently provide helper functions. For those extensions without helper functions, you will have to parse the raw DER-encoded ASN.1 yourself.*</span></span>

| <span data-ttu-id="34a2c-1553">Identificador de segurança NetX</span><span class="sxs-lookup"><span data-stu-id="34a2c-1553">NetX Secure Identifier</span></span>                              | <span data-ttu-id="34a2c-1554">Valor OID</span><span class="sxs-lookup"><span data-stu-id="34a2c-1554">OID Value</span></span> | <span data-ttu-id="34a2c-1555">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-1555">Description</span></span>                                                                    | <span data-ttu-id="34a2c-1556">Função ajudante?</span><span class="sxs-lookup"><span data-stu-id="34a2c-1556">Helper function?</span></span> |
| ------------------------------------------------------- | ------------- | ---------------------------------------------------------------------------------- | -------------------- |
| <span data-ttu-id="34a2c-1557">NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES</span><span class="sxs-lookup"><span data-stu-id="34a2c-1557">NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES</span></span>  | <span data-ttu-id="34a2c-1558">2.5.29.9</span><span class="sxs-lookup"><span data-stu-id="34a2c-1558">2.5.29.9</span></span>  | <span data-ttu-id="34a2c-1559">Atributos do Diretório – atributos básicos de informação sobre o tema do certificado</span><span class="sxs-lookup"><span data-stu-id="34a2c-1559">Directory Attributes – basic information attributes about certificate subject</span></span>  | <span data-ttu-id="34a2c-1560">No</span><span class="sxs-lookup"><span data-stu-id="34a2c-1560">No</span></span>               |
| <span data-ttu-id="34a2c-1561">NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID</span><span class="sxs-lookup"><span data-stu-id="34a2c-1561">NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID</span></span>       | <span data-ttu-id="34a2c-1562">2.5.29.14</span><span class="sxs-lookup"><span data-stu-id="34a2c-1562">2.5.29.14</span></span> | <span data-ttu-id="34a2c-1563">Usado para identificar uma chave pública específica</span><span class="sxs-lookup"><span data-stu-id="34a2c-1563">Used to identify a specific public key</span></span>                                         | <span data-ttu-id="34a2c-1564">No</span><span class="sxs-lookup"><span data-stu-id="34a2c-1564">No</span></span>               |
| <span data-ttu-id="34a2c-1565">NX_SECURE_TLS_X509_TYPE_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="34a2c-1565">NX_SECURE_TLS_X509_TYPE_KEY_USAGE</span></span>             | <span data-ttu-id="34a2c-1566">2.5.29.15</span><span class="sxs-lookup"><span data-stu-id="34a2c-1566">2.5.29.15</span></span> | <span data-ttu-id="34a2c-1567">Fornece informações sobre utilizações válidas para a chave pública do certificado</span><span class="sxs-lookup"><span data-stu-id="34a2c-1567">Provides information on valid uses for the certificate public key</span></span>              | <span data-ttu-id="34a2c-1568">Yes</span><span class="sxs-lookup"><span data-stu-id="34a2c-1568">Yes</span></span>              |
| <span data-ttu-id="34a2c-1569">NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME</span><span class="sxs-lookup"><span data-stu-id="34a2c-1569">NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME</span></span>     | <span data-ttu-id="34a2c-1570">2.5.29.17</span><span class="sxs-lookup"><span data-stu-id="34a2c-1570">2.5.29.17</span></span> | <span data-ttu-id="34a2c-1571">Fornece nomes DNS alternativos para identificar o certificado</span><span class="sxs-lookup"><span data-stu-id="34a2c-1571">Provides alternative DNS names to identify the certificate</span></span>                     | <span data-ttu-id="34a2c-1572">Sim<sup>24</sup></span><span class="sxs-lookup"><span data-stu-id="34a2c-1572">Yes<sup>24</sup></span></span>        |
| <span data-ttu-id="34a2c-1573">NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME</span><span class="sxs-lookup"><span data-stu-id="34a2c-1573">NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME</span></span>      | <span data-ttu-id="34a2c-1574">2.5.29.18</span><span class="sxs-lookup"><span data-stu-id="34a2c-1574">2.5.29.18</span></span> | <span data-ttu-id="34a2c-1575">Fornece nomes DNS alternativos para identificar o emitente do certificado</span><span class="sxs-lookup"><span data-stu-id="34a2c-1575">Provides alternative DNS names to identify the certificate's issuer</span></span>            | <span data-ttu-id="34a2c-1576">No</span><span class="sxs-lookup"><span data-stu-id="34a2c-1576">No</span></span>               |
| <span data-ttu-id="34a2c-1577">NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="34a2c-1577">NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS</span></span>     | <span data-ttu-id="34a2c-1578">2.5.29.19</span><span class="sxs-lookup"><span data-stu-id="34a2c-1578">2.5.29.19</span></span> | <span data-ttu-id="34a2c-1579">Fornece informações básicas sobre restrições de utilização de certificados</span><span class="sxs-lookup"><span data-stu-id="34a2c-1579">Provides basic certificate usage constraint information</span></span>                        | <span data-ttu-id="34a2c-1580">No</span><span class="sxs-lookup"><span data-stu-id="34a2c-1580">No</span></span>               |
| <span data-ttu-id="34a2c-1581">NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="34a2c-1581">NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS</span></span>      | <span data-ttu-id="34a2c-1582">2.5.29.30</span><span class="sxs-lookup"><span data-stu-id="34a2c-1582">2.5.29.30</span></span> | <span data-ttu-id="34a2c-1583">Usado para limitar nomes de certificados a domínios específicos</span><span class="sxs-lookup"><span data-stu-id="34a2c-1583">Used to constrain certificate names to specific domains</span></span>                        | <span data-ttu-id="34a2c-1584">No</span><span class="sxs-lookup"><span data-stu-id="34a2c-1584">No</span></span>               |
| <span data-ttu-id="34a2c-1585">NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="34a2c-1585">NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION</span></span>      | <span data-ttu-id="34a2c-1586">2.5.29.31</span><span class="sxs-lookup"><span data-stu-id="34a2c-1586">2.5.29.31</span></span> | <span data-ttu-id="34a2c-1587">Fornece URIs para distribuição de CRL</span><span class="sxs-lookup"><span data-stu-id="34a2c-1587">Provides URIs for CRL distribution</span></span>                                             | <span data-ttu-id="34a2c-1588">No</span><span class="sxs-lookup"><span data-stu-id="34a2c-1588">No</span></span>               |
| <span data-ttu-id="34a2c-1589">NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES</span><span class="sxs-lookup"><span data-stu-id="34a2c-1589">NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES</span></span>  | <span data-ttu-id="34a2c-1590">2.5.29.32</span><span class="sxs-lookup"><span data-stu-id="34a2c-1590">2.5.29.32</span></span> | <span data-ttu-id="34a2c-1591">Lista de políticas de certificados para grandes sistemas PKI</span><span class="sxs-lookup"><span data-stu-id="34a2c-1591">List of certificate policies for large PKI systems</span></span>                             | <span data-ttu-id="34a2c-1592">No</span><span class="sxs-lookup"><span data-stu-id="34a2c-1592">No</span></span>               |
| <span data-ttu-id="34a2c-1593">NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS</span><span class="sxs-lookup"><span data-stu-id="34a2c-1593">NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS</span></span> | <span data-ttu-id="34a2c-1594">2.5.29.33</span><span class="sxs-lookup"><span data-stu-id="34a2c-1594">2.5.29.33</span></span> | <span data-ttu-id="34a2c-1595">Lista das políticas de certificados de CA</span><span class="sxs-lookup"><span data-stu-id="34a2c-1595">List of CA certificate policies</span></span>                                                | <span data-ttu-id="34a2c-1596">No</span><span class="sxs-lookup"><span data-stu-id="34a2c-1596">No</span></span>               |
| <span data-ttu-id="34a2c-1597">NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID</span><span class="sxs-lookup"><span data-stu-id="34a2c-1597">NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID</span></span>     | <span data-ttu-id="34a2c-1598">2.5.29.35</span><span class="sxs-lookup"><span data-stu-id="34a2c-1598">2.5.29.35</span></span> | <span data-ttu-id="34a2c-1599">Usado para identificar uma chave pública específica associada a uma assinatura de certificado</span><span class="sxs-lookup"><span data-stu-id="34a2c-1599">Used to identify a specific public key associated with a certificate signature</span></span> | <span data-ttu-id="34a2c-1600">No</span><span class="sxs-lookup"><span data-stu-id="34a2c-1600">No</span></span>               |
| <span data-ttu-id="34a2c-1601">NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="34a2c-1601">NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS</span></span>    | <span data-ttu-id="34a2c-1602">2.5.29.36</span><span class="sxs-lookup"><span data-stu-id="34a2c-1602">2.5.29.36</span></span> | <span data-ttu-id="34a2c-1603">Restrições de política da AC</span><span class="sxs-lookup"><span data-stu-id="34a2c-1603">CA policy constraints</span></span>                                                          | <span data-ttu-id="34a2c-1604">No</span><span class="sxs-lookup"><span data-stu-id="34a2c-1604">No</span></span>               |
| <span data-ttu-id="34a2c-1605">NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="34a2c-1605">NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE</span></span>   | <span data-ttu-id="34a2c-1606">2.5.29.37</span><span class="sxs-lookup"><span data-stu-id="34a2c-1606">2.5.29.37</span></span> | <span data-ttu-id="34a2c-1607">Informações adicionais de utilização das chaves baseadas em OID</span><span class="sxs-lookup"><span data-stu-id="34a2c-1607">Additional OID-based key usage information</span></span>                                     | <span data-ttu-id="34a2c-1608">Yes</span><span class="sxs-lookup"><span data-stu-id="34a2c-1608">Yes</span></span>              |
| <span data-ttu-id="34a2c-1609">NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL</span><span class="sxs-lookup"><span data-stu-id="34a2c-1609">NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL</span></span>          | <span data-ttu-id="34a2c-1610">2.5.29.46</span><span class="sxs-lookup"><span data-stu-id="34a2c-1610">2.5.29.46</span></span> | <span data-ttu-id="34a2c-1611">Fornece informações para a obtenção de CRLs delta</span><span class="sxs-lookup"><span data-stu-id="34a2c-1611">Provides information for obtaining delta CRLs</span></span>                                  | <span data-ttu-id="34a2c-1612">No</span><span class="sxs-lookup"><span data-stu-id="34a2c-1612">No</span></span>               |
| <span data-ttu-id="34a2c-1613">NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY</span><span class="sxs-lookup"><span data-stu-id="34a2c-1613">NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY</span></span>     | <span data-ttu-id="34a2c-1614">2.5.29.54</span><span class="sxs-lookup"><span data-stu-id="34a2c-1614">2.5.29.54</span></span> | <span data-ttu-id="34a2c-1615">Campo de certificados da AC indicando que a AnyPolicy não pode ser utilizada</span><span class="sxs-lookup"><span data-stu-id="34a2c-1615">CA certificate field indicating that AnyPolicy cannot be used</span></span>                  | <span data-ttu-id="34a2c-1616">No</span><span class="sxs-lookup"><span data-stu-id="34a2c-1616">No</span></span>               |

<span data-ttu-id="34a2c-1617">OIDs e mapeamentos para extensões X.509</span><span class="sxs-lookup"><span data-stu-id="34a2c-1617">OIDs and mappings for X.509 Extensions</span></span>

24. <span data-ttu-id="34a2c-1618">A extensão SubjectAltName é analisada como parte do nome DNS check no serviço nx_secure_x509_common_name_dns_check.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1618">The SubjectAltName extension is parsed as part of the DNS name check in the service nx_secure_x509_common_name_dns_check.</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-1619">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-1619">Parameters</span></span>

- <span data-ttu-id="34a2c-1620">**certificado** Ponteiro para certificado sendo verificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1620">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="34a2c-1621">**extensão** Estrutura de devolução contendo ponteiro de dados de extensão e comprimento.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1621">**extension** Return structure containing extension data pointer and length.</span></span>
- <span data-ttu-id="34a2c-1622">**extension_id** Mapeamento inteiro OID da tabela acima.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1622">**extension_id** OID integer mapping from table above.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-1623">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-1623">Return Values</span></span>

- <span data-ttu-id="34a2c-1624">**NX_SUCCESS** (0x00) Extensão especificada OID encontrada e dados devolvidos.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1624">**NX_SUCCESS** (0x00) Specified extension OID found and data returned.</span></span>
- <span data-ttu-id="34a2c-1625">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 tag multi-byte encontrada (certificado não suportado).</span><span class="sxs-lookup"><span data-stu-id="34a2c-1625">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="34a2c-1626">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Campo Invaild ASN.1 encontrado (certificado inválido).</span><span class="sxs-lookup"><span data-stu-id="34a2c-1626">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="34a2c-1627">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Classe de tag ASN.1 inválida encontrada (certificado inválido).</span><span class="sxs-lookup"><span data-stu-id="34a2c-1627">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="34a2c-1628">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Extensão inválida encontrada</span><span class="sxs-lookup"><span data-stu-id="34a2c-1628">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered</span></span>
- <span data-ttu-id="34a2c-1629">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) A extensão dada não foi encontrada no certificado fornecido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1629">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) The given extension OID was not found in the provided certificate.</span></span>
- <span data-ttu-id="34a2c-1630">**NX_PTR_ERROR** (0x07) Certificado inválido ou ponteiro de extensão.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1630">**NX_PTR_ERROR** (0x07) Invalid certificate or extension pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-1631">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-1631">Allowed From</span></span>

<span data-ttu-id="34a2c-1632">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-1632">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-1633">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-1633">Example</span></span>

```C
/* Function to parse a Basic Constraints X.509 extension. */
UINT _basic_constraints_extension_parse(NX_SECURE_X509_CERT *certificate)
{
const UCHAR             *current_buffer;
ULONG                    length;
UINT                     status;
NX_SECURE_X509_EXTENSION extension_data;

    /* Find the Basic Constraints extension in the certificate. */
    status = _nx_secure_x509_extension_find(certificate, &extension_data,
                              NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS);

    /* See if extension present - it might be OK if not present! */
    if (status != NX_SUCCESS)
    {
        return(status);
    }

    /* The extension_data structure now points to the raw extension ASN.1
      (DER-encoded). */
    current_buffer = extension_data.nx_secure_x509_extension_data;
    length = extension_data.nx_secure_x509_extension_data_length;

   /* Extension ASN.1 parsing… */

   return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="34a2c-1634">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-1634">See Also</span></span>

- <span data-ttu-id="34a2c-1635">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-1635">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="34a2c-1636">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="34a2c-1636">nx_secure_x509_key_usage_extension_parse</span></span>
- <span data-ttu-id="34a2c-1637">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="34a2c-1637">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="34a2c-1638">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="34a2c-1638">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="34a2c-1639">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="34a2c-1639">nx_secure_x509_extended_key_usage_extension_parse</span></span>

## <a name="nx_secure_x509_key_usage_extension_parse"></a><span data-ttu-id="34a2c-1640">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="34a2c-1640">nx_secure_x509_key_usage_extension_parse</span></span>

<span data-ttu-id="34a2c-1641">Encontre e analise uma extensão de utilização da chave X.509 num certificado X.509</span><span class="sxs-lookup"><span data-stu-id="34a2c-1641">Find and parse an X.509 Key Usage extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="34a2c-1642">Prototype</span><span class="sxs-lookup"><span data-stu-id="34a2c-1642">Prototype</span></span>

```C
UINT  nx_secure_x509_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        USHORT *bitfield);
```

### <a name="description"></a><span data-ttu-id="34a2c-1643">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-1643">Description</span></span>

<span data-ttu-id="34a2c-1644">Este serviço destina-se a ser chamado a partir de uma chamada de verificação de certificado (ver *nx_secure_tls_session_certificate_callback_set)*.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1644">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)*.</span></span> <span data-ttu-id="34a2c-1645">Procurará a extensão de utilização da chave e, se for encontrada, devolverá o bitfield de utilização da chave no parâmetro "bitfield".</span><span class="sxs-lookup"><span data-stu-id="34a2c-1645">It will search for the Key Usage extension and if found, will return the Key Usage bitfield in the "bitfield" parameter.</span></span>

<span data-ttu-id="34a2c-1646">As broas, tal como definidas pela especificação X.509 (RFC 5280) são dadas na tabela abaixo.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1646">The bits, as defined by the X.509 specification (RFC 5280) are given in the table below.</span></span> <span data-ttu-id="34a2c-1647">Um bitwise E com o bitmask apropriado (e verificação de não-zero) dará o valor de cada bit.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1647">A bitwise AND with the appropriate bitmask (and checking for non-zero) will give the value of each bit.</span></span>

<span data-ttu-id="34a2c-1648">Note que a codificação deR do bitfield elimina zeros extra, de modo que a posição real dos bits nos dados do certificado bruto será provavelmente diferente das suas posições no campo de bits descodificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1648">Note that the DER-encoding of the bitfield eliminates extra zeroes so the actual position of the bits in the raw certificate data will likely be different from their positions in the decoded bitfield.</span></span> <span data-ttu-id="34a2c-1649">Os bitmasks fornecidos destinam-se apenas a ser utilizados no bitfield descodificado devolvido por *nx_secure_x509_key_usage_extension_parse* e não com os dados de certificados codificados por DER em bruto.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1649">The supplied bitmasks are only intended to be used on the decoded bitfield returned by *nx_secure_x509_key_usage_extension_parse* and not with the raw DER-encoded certificate data.</span></span>

<span data-ttu-id="34a2c-1650">Na chamada de verificação do certificado, o código de devolução de erros NX_SECURE_X509_KEY_USAGE_ERROR está reservado para utilização de pedidos.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1650">In the certificate verification callback, the error return code NX_SECURE_X509_KEY_USAGE_ERROR is reserved for application use.</span></span> <span data-ttu-id="34a2c-1651">Se houver um erro na verificação da utilização da chave, este valor pode ser devolvido da chamada para indicar o motivo da falha.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1651">If there is an error in checking key usage, this value may be returned from the callback to indicate the reason for failure.</span></span>

| <span data-ttu-id="34a2c-1652">Identificador de segurança NetX</span><span class="sxs-lookup"><span data-stu-id="34a2c-1652">NetX Secure Identifier</span></span>                            | <span data-ttu-id="34a2c-1653">Posição do bit</span><span class="sxs-lookup"><span data-stu-id="34a2c-1653">Bit position</span></span> | <span data-ttu-id="34a2c-1654">Description</span><span class="sxs-lookup"><span data-stu-id="34a2c-1654">Description</span></span>                                                                                                                                                  |
| ----------------------------------------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="34a2c-1655">NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE</span><span class="sxs-lookup"><span data-stu-id="34a2c-1655">NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE</span></span>  | <span data-ttu-id="34a2c-1656">0</span><span class="sxs-lookup"><span data-stu-id="34a2c-1656">0</span></span>            | <span data-ttu-id="34a2c-1657">O certificado pode ser usado para assinaturas digitais</span><span class="sxs-lookup"><span data-stu-id="34a2c-1657">Certificate can be used for digital signatures</span></span>                                                                                                               |
| <span data-ttu-id="34a2c-1658">NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION</span><span class="sxs-lookup"><span data-stu-id="34a2c-1658">NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION</span></span>    | <span data-ttu-id="34a2c-1659">1</span><span class="sxs-lookup"><span data-stu-id="34a2c-1659">1</span></span>            | <span data-ttu-id="34a2c-1660">O certificado pode ser utilizado para verificar assinaturas digitais que não as dos certificados e CRLs</span><span class="sxs-lookup"><span data-stu-id="34a2c-1660">Certificate can be used to verify digital signatures other than those for certificates and CRLs</span></span>                                                              |
| <span data-ttu-id="34a2c-1661">NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT</span><span class="sxs-lookup"><span data-stu-id="34a2c-1661">NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT</span></span>   | <span data-ttu-id="34a2c-1662">2</span><span class="sxs-lookup"><span data-stu-id="34a2c-1662">2</span></span>            | <span data-ttu-id="34a2c-1663">O certificado pode ser usado para encriptar chaves simétricas (transporte de chaves)</span><span class="sxs-lookup"><span data-stu-id="34a2c-1663">Certificate can be used to encrypt symmetric keys (key transport)</span></span>                                                                                            |
| <span data-ttu-id="34a2c-1664">NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT</span><span class="sxs-lookup"><span data-stu-id="34a2c-1664">NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT</span></span>  | <span data-ttu-id="34a2c-1665">3</span><span class="sxs-lookup"><span data-stu-id="34a2c-1665">3</span></span>            | <span data-ttu-id="34a2c-1666">O certificado pode ser usado para encriptar diretamente os dados brutos dos utilizadores (incomuns)</span><span class="sxs-lookup"><span data-stu-id="34a2c-1666">Certificate can be used to directly encrypt raw user data (uncommon)</span></span>                                                                                         |
| <span data-ttu-id="34a2c-1667">NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT</span><span class="sxs-lookup"><span data-stu-id="34a2c-1667">NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT</span></span>      | <span data-ttu-id="34a2c-1668">4</span><span class="sxs-lookup"><span data-stu-id="34a2c-1668">4</span></span>            | <span data-ttu-id="34a2c-1669">O certificado pode ser usado para um acordo-chave (como com Diffie-Hellman)</span><span class="sxs-lookup"><span data-stu-id="34a2c-1669">Certificate can be used for key agreement (as with Diffie-Hellman)</span></span>                                                                                           |
| <span data-ttu-id="34a2c-1670">NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN</span><span class="sxs-lookup"><span data-stu-id="34a2c-1670">NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN</span></span>     | <span data-ttu-id="34a2c-1671">5</span><span class="sxs-lookup"><span data-stu-id="34a2c-1671">5</span></span>            | <span data-ttu-id="34a2c-1672">O certificado pode ser usado para assinar e verificar outros certificados (o certificado é um certificado CA ou ICA).</span><span class="sxs-lookup"><span data-stu-id="34a2c-1672">Certificate can be used to sign and verify other certificates (the certificate is a CA or ICA certificate).</span></span>                                                  |
| <span data-ttu-id="34a2c-1673">NX_SECURE_X509_KEY_USAGE_CRL_SIGN</span><span class="sxs-lookup"><span data-stu-id="34a2c-1673">NX_SECURE_X509_KEY_USAGE_CRL_SIGN</span></span>           | <span data-ttu-id="34a2c-1674">6</span><span class="sxs-lookup"><span data-stu-id="34a2c-1674">6</span></span>            | <span data-ttu-id="34a2c-1675">A chave pública do certificado é utilizada para verificar assinaturas em CRLs</span><span class="sxs-lookup"><span data-stu-id="34a2c-1675">Certificate public key is used to verify signatures on CRLs</span></span>                                                                                                  |
| <span data-ttu-id="34a2c-1676">NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY</span><span class="sxs-lookup"><span data-stu-id="34a2c-1676">NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY</span></span>      | <span data-ttu-id="34a2c-1677">7</span><span class="sxs-lookup"><span data-stu-id="34a2c-1677">7</span></span>            | <span data-ttu-id="34a2c-1678">Usado com bit do Acordo Chave (bit 4) – quando definido, a tecla de certificado só pode ser usada para encriptar durante o acordo-chave.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1678">Used with Key Agreement bit (bit 4) – when set, certificate key can only be used to encrypt during key agreement.</span></span> <span data-ttu-id="34a2c-1679">Indefinido se a parte do Acordo-Chave não for definida.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1679">Undefined if Key Agreement bit is not set.</span></span> |
| <span data-ttu-id="34a2c-1680">NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY</span><span class="sxs-lookup"><span data-stu-id="34a2c-1680">NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY</span></span>      | <span data-ttu-id="34a2c-1681">8</span><span class="sxs-lookup"><span data-stu-id="34a2c-1681">8</span></span>            | <span data-ttu-id="34a2c-1682">Utilizado com bit do Acordo Chave (bit 4) – quando definido, a tecla de certificado só pode ser usada para desencriptar durante o acordo-chave.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1682">Used with Key Agreement bit (bit 4) – when set, certificate key can only be used to decrypt during key agreement.</span></span> <span data-ttu-id="34a2c-1683">Indefinido se a parte do Acordo-Chave não for definida.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1683">Undefined if Key Agreement bit is not set.</span></span> |

<span data-ttu-id="34a2c-1684">Bitmasks e valores para extensão de utilização da chave X.509</span><span class="sxs-lookup"><span data-stu-id="34a2c-1684">Bitmasks and values for X.509 Key Usage Extension</span></span>

### <a name="parameters"></a><span data-ttu-id="34a2c-1685">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34a2c-1685">Parameters</span></span>

- <span data-ttu-id="34a2c-1686">**certificado** Ponteiro para certificado sendo verificado.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1686">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="34a2c-1687">**bitfield** Devolva todo o campo da extensão.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1687">**bitfield** Return the entire bitfield from the extension.</span></span>

### <a name="return-values"></a><span data-ttu-id="34a2c-1688">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="34a2c-1688">Return Values</span></span>

- <span data-ttu-id="34a2c-1689">**NX_SUCCESS** (0x00) Extensão de utilização da chave encontrada e bitfield devolvido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1689">**NX_SUCCESS** (0x00) Key usage extension found and bitfield returned.</span></span>
- <span data-ttu-id="34a2c-1690">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 tag multi-byte encontrada (certificado não suportado).</span><span class="sxs-lookup"><span data-stu-id="34a2c-1690">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="34a2c-1691">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Campo Invaild ASN.1 encontrado (certificado inválido).</span><span class="sxs-lookup"><span data-stu-id="34a2c-1691">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="34a2c-1692">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Classe de tag ASN.1 inválida encontrada (certificado inválido).</span><span class="sxs-lookup"><span data-stu-id="34a2c-1692">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="34a2c-1693">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Extensão inválida encontrada (certificado inválido).</span><span class="sxs-lookup"><span data-stu-id="34a2c-1693">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered (invalid certificate).</span></span>
- <span data-ttu-id="34a2c-1694">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B)A extensão de utilização da chave não foi encontrada no certificado fornecido.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1694">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B)The Key Usage extension was not found in the provided certificate.</span></span>
- <span data-ttu-id="34a2c-1695">**NX_PTR_ERROR** (0x07) Certificado inválido ou ponteiro bitfield.</span><span class="sxs-lookup"><span data-stu-id="34a2c-1695">**NX_PTR_ERROR** (0x07) Invalid certificate or bitfield pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34a2c-1696">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="34a2c-1696">Allowed From</span></span>

<span data-ttu-id="34a2c-1697">Fios</span><span class="sxs-lookup"><span data-stu-id="34a2c-1697">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34a2c-1698">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34a2c-1698">Example</span></span>

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session,
  NX_SECURE_X509_CERT* certificate)
{
UINT status;
USHORT key_usage_bitfield;

    /* Key usage – extract key usage bitfield. */
    status = nx_secure_x509_key_usage_extension_parse(certificate, &key_usage_bitfield);

   /* Check certificate for a few specific key usage bits. */
   if((key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE) == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION)   == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT)  == 0)
    {
        printf("Expected key usage bitfield bits not set!\n");
        return(NX_SECURE_X509_KEY_USAGE_ERROR);
    }

    /* The specified bits were set, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="34a2c-1699">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34a2c-1699">See Also</span></span>

- <span data-ttu-id="34a2c-1700">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="34a2c-1700">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="34a2c-1701">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="34a2c-1701">nx_secure_x509_extended_key_usage_extension_parse</span></span>
- <span data-ttu-id="34a2c-1702">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="34a2c-1702">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="34a2c-1703">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="34a2c-1703">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="34a2c-1704">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="34a2c-1704">nx_secure_x509_extension_find</span></span>
