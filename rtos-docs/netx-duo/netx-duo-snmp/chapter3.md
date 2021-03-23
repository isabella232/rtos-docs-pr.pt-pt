---
title: Capítulo 3 - Descrição dos serviços de agente SNMP da Azure RTOS NetX Duo
description: Este capítulo contém uma descrição de todos os serviços do Agente SNMP NetX Duo (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cf4c4cb0edb7deb7bd0f257f48949b5c7355426b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825766"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-snmp-agent-services"></a><span data-ttu-id="226d6-103">Capítulo 3 - Descrição dos serviços de agente SNMP da Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="226d6-103">Chapter 3 - Description of Azure RTOS NetX Duo SNMP agent services</span></span>

<span data-ttu-id="226d6-104">Este capítulo contém uma descrição de todos os serviços de agente SNMP Azure RTOS NetX Duo (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="226d6-104">This chapter contains a description of all Azure RTOS NetX Duo SNMP agent services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="226d6-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="226d6-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="226d6-106">nx_snmp_agent_auth_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="226d6-106">nx_snmp_agent_auth_trap_key_use</span></span>](#nx_snmp_agent_auth_trap_key_use)
   - <span data-ttu-id="226d6-107">*Especificar a chave de autenticação (apenas SNMP v3) para mensagens de armadilha*</span><span class="sxs-lookup"><span data-stu-id="226d6-107">*Specify authentication key (SNMP v3 only) for trap messages*</span></span>
- [<span data-ttu-id="226d6-108">nx_snmp_agent_authenticate_key_use</span><span class="sxs-lookup"><span data-stu-id="226d6-108">nx_snmp_agent_authenticate_key_use</span></span>](#nx_snmp_agent_authenticate_key_use)
   - <span data-ttu-id="226d6-109">*Especificar a chave de autenticação (apenas SNMP v3) para mensagens de resposta*</span><span class="sxs-lookup"><span data-stu-id="226d6-109">*Specify authentication key (SNMP v3 only) for response messages*</span></span>
- [<span data-ttu-id="226d6-110">nx_snmp_agent_community_get</span><span class="sxs-lookup"><span data-stu-id="226d6-110">nx_snmp_agent_community_get</span></span>](#nx_snmp_agent_community_get)
   - <span data-ttu-id="226d6-111">*Recuperar o nome da comunidade*</span><span class="sxs-lookup"><span data-stu-id="226d6-111">*Retrieve community name*</span></span>
- [<span data-ttu-id="226d6-112">nx_snmp_agent_context_engine_set</span><span class="sxs-lookup"><span data-stu-id="226d6-112">nx_snmp_agent_context_engine_set</span></span>](#nx_snmp_agent_context_engine_set)
   - <span data-ttu-id="226d6-113">*Motor de contexto definido (apenas SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="226d6-113">*Set context engine (SNMP v3 only)*</span></span>
- [<span data-ttu-id="226d6-114">nx_snmp_agent_context_name_set</span><span class="sxs-lookup"><span data-stu-id="226d6-114">nx_snmp_agent_context_name_set</span></span>](#nx_snmp_agent_context_name_set)
   - <span data-ttu-id="226d6-115">*Definir nome de contexto (apenas SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="226d6-115">*Set context name (SNMP v3 only)*</span></span>
- [<span data-ttu-id="226d6-116">nx_snmp_agent_create</span><span class="sxs-lookup"><span data-stu-id="226d6-116">nx_snmp_agent_create</span></span>](#nx_snmp_agent_create)
   - <span data-ttu-id="226d6-117">*Criar agente SNMP*</span><span class="sxs-lookup"><span data-stu-id="226d6-117">*Create SNMP agent*</span></span>
- [<span data-ttu-id="226d6-118">nx_snmp_agent_current_version_get</span><span class="sxs-lookup"><span data-stu-id="226d6-118">nx_snmp_agent_current_version_get</span></span>](#nx_snmp_agent_current_version_get)
   - <span data-ttu-id="226d6-119">*Obtenha a versão SNMP do pacote recebido*</span><span class="sxs-lookup"><span data-stu-id="226d6-119">*Get the SNMP version of received packet*</span></span>
- [<span data-ttu-id="226d6-120">nx_snmp_agent_request_get_type_test</span><span class="sxs-lookup"><span data-stu-id="226d6-120">nx_snmp_agent_request_get_type_test</span></span>](#nx_snmp_agent_request_get_type_test)
   - <span data-ttu-id="226d6-121">*Indicar se o último pedido do SNMP é tipo GET ou SET*</span><span class="sxs-lookup"><span data-stu-id="226d6-121">*Indicate if last SNMP request is GET or SET type*</span></span>
- [<span data-ttu-id="226d6-122">nx_snmp_agent_private_string_test</span><span class="sxs-lookup"><span data-stu-id="226d6-122">nx_snmp_agent_private_string_test</span></span>](#nx_snmp_agent_private_string_test)
   - <span data-ttu-id="226d6-123">*Determine se o string corresponde ao agente corda privada*</span><span class="sxs-lookup"><span data-stu-id="226d6-123">*Determine if string matches agent private string*</span></span>
- [<span data-ttu-id="226d6-124">nx_snmp_agent_public_string_test</span><span class="sxs-lookup"><span data-stu-id="226d6-124">nx_snmp_agent_public_string_test</span></span>](#nx_snmp_agent_public_string_test)
   - <span data-ttu-id="226d6-125">*Determine se a corda corresponde ao agente de cadeias de cordas públicas*</span><span class="sxs-lookup"><span data-stu-id="226d6-125">*Determine if string matches agent public string*</span></span>
- [<span data-ttu-id="226d6-126">nx_snmp_agent_set_interface</span><span class="sxs-lookup"><span data-stu-id="226d6-126">nx_snmp_agent_set_interface</span></span>](#nx_snmp_agent_set_interface)
   - <span data-ttu-id="226d6-127">*Definir interface de rede para mensagens SNMP*</span><span class="sxs-lookup"><span data-stu-id="226d6-127">*Set network interface for SNMP messaging*</span></span>
- [<span data-ttu-id="226d6-128">nx_snmp_agent_private_string_set</span><span class="sxs-lookup"><span data-stu-id="226d6-128">nx_snmp_agent_private_string_set</span></span>](#nx_snmp_agent_private_string_set)
   - <span data-ttu-id="226d6-129">*Definir a cadeia de comunidade privada do agente SNMP*</span><span class="sxs-lookup"><span data-stu-id="226d6-129">*Set the SNMP agent private community string*</span></span>
- [<span data-ttu-id="226d6-130">nx_snmp_agent_public_string_set</span><span class="sxs-lookup"><span data-stu-id="226d6-130">nx_snmp_agent_public_string_set</span></span>](#nx_snmp_agent_public_string_set)
   - <span data-ttu-id="226d6-131">*Definir a cadeia da comunidade pública do agente SNMP*</span><span class="sxs-lookup"><span data-stu-id="226d6-131">*Set the SNMP agent public community string*</span></span>
- [<span data-ttu-id="226d6-132">nx_snmp_agent_version_set</span><span class="sxs-lookup"><span data-stu-id="226d6-132">nx_snmp_agent_version_set</span></span>](#nx_snmp_agent_version_set)
   - <span data-ttu-id="226d6-133">*Desaponte o estado do agente SNMP para todas as versões SNMP*</span><span class="sxs-lookup"><span data-stu-id="226d6-133">*Set the SNMP agent status for all SNMP versions*</span></span>
- [<span data-ttu-id="226d6-134">nx_snmp_agent_delete</span><span class="sxs-lookup"><span data-stu-id="226d6-134">nx_snmp_agent_delete</span></span>](#nx_snmp_agent_delete)
   - <span data-ttu-id="226d6-135">*Eliminar agente SNMP*</span><span class="sxs-lookup"><span data-stu-id="226d6-135">*Delete SNMP agent*</span></span>
- [<span data-ttu-id="226d6-136">nx_snmp_agent_md5_key_create</span><span class="sxs-lookup"><span data-stu-id="226d6-136">nx_snmp_agent_md5_key_create</span></span>](#nx_snmp_agent_md5_key_create)
   - <span data-ttu-id="226d6-137">*Criar tecla md5 (apenas SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="226d6-137">*Create md5 key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="226d6-138">nx_snmp_agent_md5_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="226d6-138">nx_snmp_agent_md5_key_create_extended</span></span>](#nx_snmp_agent_md5_key_create_extended)
   - <span data-ttu-id="226d6-139">*Criar tecla md5 (apenas SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="226d6-139">*Create md5 key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="226d6-140">nx_snmp_agent_priv_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="226d6-140">nx_snmp_agent_priv_trap_key_use</span></span>](#nx_snmp_agent_priv_trap_key_use)
   - <span data-ttu-id="226d6-141">*Especificar a chave de encriptação (apenas SNMP v3) para mensagens de armadilha*</span><span class="sxs-lookup"><span data-stu-id="226d6-141">*Specify encryption key (SNMP v3 only) for trap messages*</span></span>
- [<span data-ttu-id="226d6-142">nx_snmp_agent_privacy_key_use</span><span class="sxs-lookup"><span data-stu-id="226d6-142">nx_snmp_agent_privacy_key_use</span></span>](#nx_snmp_agent_privacy_key_use)
   - <span data-ttu-id="226d6-143">*Especificar a chave de encriptação (apenas SNMP v3) para mensagens de resposta*</span><span class="sxs-lookup"><span data-stu-id="226d6-143">*Specify encryption key (SNMP v3 only) for response messages*</span></span>
- [<span data-ttu-id="226d6-144">nx_snmp_agent_sha_key_create</span><span class="sxs-lookup"><span data-stu-id="226d6-144">nx_snmp_agent_sha_key_create</span></span>](#nx_snmp_agent_sha_key_create)
   - <span data-ttu-id="226d6-145">*Criar tecla sha (apenas SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="226d6-145">*Create sha key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="226d6-146">nx_snmp_agent_sha_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="226d6-146">nx_snmp_agent_sha_key_create_extended</span></span>](#nx_snmp_agent_sha_key_create_extended)
   - <span data-ttu-id="226d6-147">*Criar tecla sha (apenas SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="226d6-147">*Create sha key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="226d6-148">nx_snmp_agent_start</span><span class="sxs-lookup"><span data-stu-id="226d6-148">nx_snmp_agent_start</span></span>](#nx_snmp_agent_start)
   - <span data-ttu-id="226d6-149">*Iniciar agente SNMP*</span><span class="sxs-lookup"><span data-stu-id="226d6-149">*Start SNMP agent*</span></span>
- [<span data-ttu-id="226d6-150">nx_snmp_agent_stop</span><span class="sxs-lookup"><span data-stu-id="226d6-150">nx_snmp_agent_stop</span></span>](#nx_snmp_agent_stop)
   - <span data-ttu-id="226d6-151">*Parar o agente SNMP*</span><span class="sxs-lookup"><span data-stu-id="226d6-151">*Stop SNMP agent*</span></span>
- [<span data-ttu-id="226d6-152">nx_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="226d6-152">nx_snmp_agent_trap_send</span></span>](#nx_snmp_agent_trap_send)
   - <span data-ttu-id="226d6-153">*Enviar armadilha SNMP v1 (apenas IPv4)*</span><span class="sxs-lookup"><span data-stu-id="226d6-153">*Send SNMP v1 trap (IPv4 only)*</span></span>
- [<span data-ttu-id="226d6-154">nx_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="226d6-154">nx_snmp_agent_trapv2_send</span></span>](#nx_snmp_agent_trapv2_send)
   - <span data-ttu-id="226d6-155">*Enviar armadilha SNMP v2 (apenas IPv4)*</span><span class="sxs-lookup"><span data-stu-id="226d6-155">*Send SNMP v2 trap (IPv4 only)*</span></span>
- [<span data-ttu-id="226d6-156">nx_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="226d6-156">nx_snmp_agent_trapv2_oid_send</span></span>](#nx_snmp_agent_trapv2_oid_send)
   - <span data-ttu-id="226d6-157">*Enviar armadilha SNMP v2 (apenas IPv4) especificando o OID*</span><span class="sxs-lookup"><span data-stu-id="226d6-157">*Send SNMP v2 trap (IPv4 only) specifying the OID*</span></span>
- [<span data-ttu-id="226d6-158">nx_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="226d6-158">nx_snmp_agent_trapv3_send</span></span>](#nx_snmp_agent_trapv3_send)
   - <span data-ttu-id="226d6-159">*Enviar armadilha SNMP v3 (apenas IPv4)*</span><span class="sxs-lookup"><span data-stu-id="226d6-159">*Send SNMP v3 trap (IPv4 only)*</span></span>
- [<span data-ttu-id="226d6-160">nx_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="226d6-160">nx_snmp_agent_trapv3_oid_send</span></span>](#nx_snmp_agent_trapv3_oid_send)
   - <span data-ttu-id="226d6-161">*Enviar armadilha SNMP v2 (apenas IPv4) especificando o OID*</span><span class="sxs-lookup"><span data-stu-id="226d6-161">*Send SNMP v2 trap (IPv4 only) specifying the OID*</span></span>
- [<span data-ttu-id="226d6-162">nxd_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="226d6-162">nxd_snmp_agent_trap_send</span></span>](#nxd_snmp_agent_trap_send)
   - <span data-ttu-id="226d6-163">*Enviar armadilha SNMP v1 (IPv4 e IPv6)*</span><span class="sxs-lookup"><span data-stu-id="226d6-163">*Send SNMP v1 trap (IPv4 and IPv6)*</span></span>
- [<span data-ttu-id="226d6-164">nxd_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="226d6-164">nxd_snmp_agent_trapv2_send</span></span>](#nxd_snmp_agent_trapv2_send)
   - <span data-ttu-id="226d6-165">*Enviar armadilha SNMP v2 (IPv4 e IPv6)*</span><span class="sxs-lookup"><span data-stu-id="226d6-165">*Send SNMP v2 trap (IPv4 and IPv6)*</span></span>
- [<span data-ttu-id="226d6-166">nxd_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="226d6-166">nxd_snmp_agent_trapv2_oid_send</span></span>](#nxd_snmp_agent_trapv2_oid_send)
   - <span data-ttu-id="226d6-167">*Enviar armadilha SNMP v2 (IPv4/IPv6) especificando o OID*</span><span class="sxs-lookup"><span data-stu-id="226d6-167">*Send SNMP v2 trap (IPv4/IPv6) specifying the OID*</span></span>
- [<span data-ttu-id="226d6-168">nxd_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="226d6-168">nxd_snmp_agent_trapv3_send</span></span>](#nxd_snmp_agent_trapv3_send)
   - <span data-ttu-id="226d6-169">*Enviar armadilha SNMP v3 (IPv4 e IPv6)*</span><span class="sxs-lookup"><span data-stu-id="226d6-169">*Send SNMP v3 trap (IPv4 and IPv6)*</span></span>
- [<span data-ttu-id="226d6-170">nxd_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="226d6-170">nxd_snmp_agent_trapv3_oid_send</span></span>](#nxd_snmp_agent_trapv3_oid_send)
   - <span data-ttu-id="226d6-171">*Enviar armadilha SNMP v2 (IPv4/IPv6) especificando o OID*</span><span class="sxs-lookup"><span data-stu-id="226d6-171">*Send SNMP v2 trap (IPv4/IPv6) specifying the OID*</span></span>
- [<span data-ttu-id="226d6-172">nx_snmp_agent_v3_context_boots_set</span><span class="sxs-lookup"><span data-stu-id="226d6-172">nx_snmp_agent_v3_context_boots_set</span></span>](#nx_snmp_agent_v3_context_boots_set)
   - <span data-ttu-id="226d6-173">*Definir o número de reboots*</span><span class="sxs-lookup"><span data-stu-id="226d6-173">*Set the number of reboots*</span></span>
- [<span data-ttu-id="226d6-174">nx_snmp_object_compare</span><span class="sxs-lookup"><span data-stu-id="226d6-174">nx_snmp_object_compare</span></span>](#nx_snmp_object_compare)
   - <span data-ttu-id="226d6-175">*Comparar dois objetos*</span><span class="sxs-lookup"><span data-stu-id="226d6-175">*Compare two objects*</span></span>
- [<span data-ttu-id="226d6-176">nx_snmp_object_compare_extended</span><span class="sxs-lookup"><span data-stu-id="226d6-176">nx_snmp_object_compare_extended</span></span>](#nx_snmp_object_compare_extended)
   - <span data-ttu-id="226d6-177">*Comparar dois objetos*</span><span class="sxs-lookup"><span data-stu-id="226d6-177">*Compare two objects*</span></span>
- [<span data-ttu-id="226d6-178">nx_snmp_object_copy</span><span class="sxs-lookup"><span data-stu-id="226d6-178">nx_snmp_object_copy</span></span>](#nx_snmp_object_copy)
   - <span data-ttu-id="226d6-179">*Copiar um objeto*</span><span class="sxs-lookup"><span data-stu-id="226d6-179">*Copy an object*</span></span>
- [<span data-ttu-id="226d6-180">nx_snmp_object_copy_extended</span><span class="sxs-lookup"><span data-stu-id="226d6-180">nx_snmp_object_copy_extended</span></span>](#nx_snmp_object_copy_extended)
   - <span data-ttu-id="226d6-181">*Copiar um objeto*</span><span class="sxs-lookup"><span data-stu-id="226d6-181">*Copy an object*</span></span>
- [<span data-ttu-id="226d6-182">nx_snmp_object_counter_get</span><span class="sxs-lookup"><span data-stu-id="226d6-182">nx_snmp_object_counter_get</span></span>](#nx_snmp_object_counter_get)
   - <span data-ttu-id="226d6-183">*Obtenha objeto de contador*</span><span class="sxs-lookup"><span data-stu-id="226d6-183">*Get counter object*</span></span>
- [<span data-ttu-id="226d6-184">nx_snmp_object_counter_set</span><span class="sxs-lookup"><span data-stu-id="226d6-184">nx_snmp_object_counter_set</span></span>](#nx_snmp_object_counter_set)
   - <span data-ttu-id="226d6-185">*Definir objeto de contador*</span><span class="sxs-lookup"><span data-stu-id="226d6-185">*Set counter object*</span></span>
- [<span data-ttu-id="226d6-186">nx_snmp_object_counter64_get</span><span class="sxs-lookup"><span data-stu-id="226d6-186">nx_snmp_object_counter64_get</span></span>](#nx_snmp_object_counter64_get)
   - <span data-ttu-id="226d6-187">*Obtenha objeto de contador de 64 bits*</span><span class="sxs-lookup"><span data-stu-id="226d6-187">*Get 64-bit counter object*</span></span>
- [<span data-ttu-id="226d6-188">nx_snmp_object_counter64_set</span><span class="sxs-lookup"><span data-stu-id="226d6-188">nx_snmp_object_counter64_set</span></span>](#nx_snmp_object_counter64_set)
   - <span data-ttu-id="226d6-189">*Definir objeto de contador de 64 bits*</span><span class="sxs-lookup"><span data-stu-id="226d6-189">*Set 64-bit counter object*</span></span>
- [<span data-ttu-id="226d6-190">nx_snmp_object_end_of_mib</span><span class="sxs-lookup"><span data-stu-id="226d6-190">nx_snmp_object_end_of_mib</span></span>](#nx_snmp_object_end_of_mib)
   - <span data-ttu-id="226d6-191">*Definir valor final de mib*</span><span class="sxs-lookup"><span data-stu-id="226d6-191">*Set end-of-mib value*</span></span>
- [<span data-ttu-id="226d6-192">nx_snmp_object_gauge_get</span><span class="sxs-lookup"><span data-stu-id="226d6-192">nx_snmp_object_gauge_get</span></span>](#nx_snmp_object_gauge_get)
   - <span data-ttu-id="226d6-193">*Obtenha objeto de bitola*</span><span class="sxs-lookup"><span data-stu-id="226d6-193">*Get gauge object*</span></span>
- [<span data-ttu-id="226d6-194">nx_snmp_object_gauge_set</span><span class="sxs-lookup"><span data-stu-id="226d6-194">nx_snmp_object_gauge_set</span></span>](#nx_snmp_object_gauge_set)
   - <span data-ttu-id="226d6-195">*Conjunto de objeto de bitola*</span><span class="sxs-lookup"><span data-stu-id="226d6-195">*Set gauge object*</span></span>
- [<span data-ttu-id="226d6-196">nx_snmp_object_id_get</span><span class="sxs-lookup"><span data-stu-id="226d6-196">nx_snmp_object_id_get</span></span>](#nx_snmp_object_id_get)
   - <span data-ttu-id="226d6-197">*Obter objeto id*</span><span class="sxs-lookup"><span data-stu-id="226d6-197">*Get object id*</span></span>
- [<span data-ttu-id="226d6-198">nx_snmp_object_id_set</span><span class="sxs-lookup"><span data-stu-id="226d6-198">nx_snmp_object_id_set</span></span>](#nx_snmp_object_id_set)
   - <span data-ttu-id="226d6-199">*Definir id objeto*</span><span class="sxs-lookup"><span data-stu-id="226d6-199">*Set object id*</span></span>
- [<span data-ttu-id="226d6-200">nx_snmp_object_integer_get</span><span class="sxs-lookup"><span data-stu-id="226d6-200">nx_snmp_object_integer_get</span></span>](#nx_snmp_object_integer_get)
   - <span data-ttu-id="226d6-201">*Obter objeto inteiro*</span><span class="sxs-lookup"><span data-stu-id="226d6-201">*Get integer object*</span></span>
- [<span data-ttu-id="226d6-202">nx_snmp_object_integer_set</span><span class="sxs-lookup"><span data-stu-id="226d6-202">nx_snmp_object_integer_set</span></span>](#nx_snmp_object_integer_set)
   - <span data-ttu-id="226d6-203">*Definir objeto inteiro*</span><span class="sxs-lookup"><span data-stu-id="226d6-203">*Set integer object*</span></span>
- [<span data-ttu-id="226d6-204">nx_snmp_object_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="226d6-204">nx_snmp_object_ip_address_get</span></span>](#nx_snmp_object_ip_address_get)
   - <span data-ttu-id="226d6-205">*Obtenha objeto de endereço IP (apenas IPv4)*</span><span class="sxs-lookup"><span data-stu-id="226d6-205">*Get IP address object (IPv4 only)*</span></span>
- [<span data-ttu-id="226d6-206">nx_snmp_object_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="226d6-206">nx_snmp_object_ip_address_set</span></span>](#nx_snmp_object_ip_address_set)
   - <span data-ttu-id="226d6-207">*Definir objeto de endereço IP (apenas IPv4)*</span><span class="sxs-lookup"><span data-stu-id="226d6-207">*Set IP address object (IPv4 only)*</span></span>
- [<span data-ttu-id="226d6-208">nx_snmp_object_ipv6_address_get</span><span class="sxs-lookup"><span data-stu-id="226d6-208">nx_snmp_object_ipv6_address_get</span></span>](#nx_snmp_object_ipv6_address_get)
   - <span data-ttu-id="226d6-209">*Obtenha objeto de endereço IP (apenas IPv6)*</span><span class="sxs-lookup"><span data-stu-id="226d6-209">*Get IP address object (IPv6 only)*</span></span>
- [<span data-ttu-id="226d6-210">nx_snmp_object_ipv6_address_set</span><span class="sxs-lookup"><span data-stu-id="226d6-210">nx_snmp_object_ipv6_address_set</span></span>](#nx_snmp_object_ipv6_address_set)
   - <span data-ttu-id="226d6-211">*Definir objeto de endereço IP (apenas IPv6)*</span><span class="sxs-lookup"><span data-stu-id="226d6-211">*Set IP address object (IPv6 only)*</span></span>
- [<span data-ttu-id="226d6-212">nx_snmp_object_no_instance</span><span class="sxs-lookup"><span data-stu-id="226d6-212">nx_snmp_object_no_instance</span></span>](#nx_snmp_object_no_instance)
   - <span data-ttu-id="226d6-213">*Definir valor sem instância*</span><span class="sxs-lookup"><span data-stu-id="226d6-213">*Set no-instance value*</span></span>
- [<span data-ttu-id="226d6-214">nx_snmp_object_not_found</span><span class="sxs-lookup"><span data-stu-id="226d6-214">nx_snmp_object_not_found</span></span>](#nx_snmp_object_not_found)
   - <span data-ttu-id="226d6-215">*Definir valor não encontrado*</span><span class="sxs-lookup"><span data-stu-id="226d6-215">*Set not-found value*</span></span>
- [<span data-ttu-id="226d6-216">nx_snmp_object_octet_string_get</span><span class="sxs-lookup"><span data-stu-id="226d6-216">nx_snmp_object_octet_string_get</span></span>](#nx_snmp_object_octet_string_get)
   - <span data-ttu-id="226d6-217">*Obtenha objeto de corda de octeto*</span><span class="sxs-lookup"><span data-stu-id="226d6-217">*Get octet string object*</span></span>
- [<span data-ttu-id="226d6-218">nx_snmp_object_octet_string_set</span><span class="sxs-lookup"><span data-stu-id="226d6-218">nx_snmp_object_octet_string_set</span></span>](#nx_snmp_object_octet_string_set)
   - <span data-ttu-id="226d6-219">*Definir objeto de corda de octeto*</span><span class="sxs-lookup"><span data-stu-id="226d6-219">*Set octet string object*</span></span>
- [<span data-ttu-id="226d6-220">nx_snmp_object_string_get</span><span class="sxs-lookup"><span data-stu-id="226d6-220">nx_snmp_object_string_get</span></span>](#nx_snmp_object_string_get)
   - <span data-ttu-id="226d6-221">*Obtenha objeto de corda ASCII*</span><span class="sxs-lookup"><span data-stu-id="226d6-221">*Get ASCII string object*</span></span>
- [<span data-ttu-id="226d6-222">nx_snmp_object_string_set</span><span class="sxs-lookup"><span data-stu-id="226d6-222">nx_snmp_object_string_set</span></span>](#nx_snmp_object_string_set)
   - <span data-ttu-id="226d6-223">*Definir objeto de corda ASCII*</span><span class="sxs-lookup"><span data-stu-id="226d6-223">*Set ASCII string object*</span></span>
- [<span data-ttu-id="226d6-224">nx_snmp_object_timetics_get</span><span class="sxs-lookup"><span data-stu-id="226d6-224">nx_snmp_object_timetics_get</span></span>](#nx_snmp_object_timetics_get)
   - <span data-ttu-id="226d6-225">*Obter objeto timetics*</span><span class="sxs-lookup"><span data-stu-id="226d6-225">*Get timetics object*</span></span>
- [<span data-ttu-id="226d6-226">nx_snmp_object_timetics_set</span><span class="sxs-lookup"><span data-stu-id="226d6-226">nx_snmp_object_timetics_set</span></span>](#nx_snmp_object_timetics_set)
   - <span data-ttu-id="226d6-227">*Objeto de timetics definido*</span><span class="sxs-lookup"><span data-stu-id="226d6-227">*Set timetics object*</span></span>

## <a name="nx_snmp_agent_auth_trap_key_use"></a><span data-ttu-id="226d6-228">nx_snmp_agent_auth_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="226d6-228">nx_snmp_agent_auth_trap_key_use</span></span>
<span data-ttu-id="226d6-229">Especificar a chave de autenticação para mensagens de armadilha</span><span class="sxs-lookup"><span data-stu-id="226d6-229">Specify authentication key for trap messages</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-230">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-230">Prototype</span></span>

```c
UINT nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a><span data-ttu-id="226d6-231">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-231">Description</span></span>

<span data-ttu-id="226d6-232">Este serviço especifica a chave a utilizar para definir parâmetros de autenticação no cabeçalho de segurança SNMPv3 em mensagens de armadilha.</span><span class="sxs-lookup"><span data-stu-id="226d6-232">This service specifies the key to be used for setting authentication parameters in the SNMPv3 security header in trap messages.</span></span> <span data-ttu-id="226d6-233">Fornecer um valor NX_NULL para a autenticação desativar a chave.</span><span class="sxs-lookup"><span data-stu-id="226d6-233">Supplying a NX_NULL value for the key disables authentication.</span></span>

> [!NOTE]
> <span data-ttu-id="226d6-234">A chave deve ser previamente criada.</span><span class="sxs-lookup"><span data-stu-id="226d6-234">The key must be previously created.</span></span> <span data-ttu-id="226d6-235">Veja nx_snmp_agent_md5_key_create ou nx_snmp_agent_sha_key_create.</span><span class="sxs-lookup"><span data-stu-id="226d6-235">See nx_snmp_agent_md5_key_create or nx_snmp_agent_sha_key_create.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-236">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-236">Input Parameters</span></span>

- <span data-ttu-id="226d6-237">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-237">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-238">**chave** Ponteiro para uma tecla MD5 ou SHA previamente criada.</span><span class="sxs-lookup"><span data-stu-id="226d6-238">**key** Pointer to a previously created MD5 or SHA key.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-239">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-239">Return Values</span></span>

- <span data-ttu-id="226d6-240">**NX_SUCCESS** conjunto de teclas de autenticação bem sucedidas (0x00).</span><span class="sxs-lookup"><span data-stu-id="226d6-240">**NX_SUCCESS** (0x00) Successful authentication key set.</span></span>
- <span data-ttu-id="226d6-241">**NX_NOT_ENABLED** (0x14) Segurança SNMP desativada</span><span class="sxs-lookup"><span data-stu-id="226d6-241">**NX_NOT_ENABLED** (0x14) SNMP Security disabled</span></span> 
- <span data-ttu-id="226d6-242">**NX_PTR_ERROR** (0x07) Ponteiro do Agente SNMP inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-242">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-243">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-243">Allowed From</span></span>

<span data-ttu-id="226d6-244">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-244">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-245">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-245">Example</span></span>

```c
/* Use previously created “my_key” for SNMPv3 trap message authentication.  */
status =  nx_snmp_agent_auth_trap_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for authentication parameters in trap messages.  */
```

## <a name="nx_snmp_agent_authenticate_key_use"></a><span data-ttu-id="226d6-246">nx_snmp_agent_authenticate_key_use</span><span class="sxs-lookup"><span data-stu-id="226d6-246">nx_snmp_agent_authenticate_key_use</span></span>
<span data-ttu-id="226d6-247">Especificar a chave de autenticação para mensagens de resposta</span><span class="sxs-lookup"><span data-stu-id="226d6-247">Specify authentication key for response messages</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-248">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-248">Prototype</span></span>

```c
UINT nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr, 
                                        NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a><span data-ttu-id="226d6-249">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-249">Description</span></span>

<span data-ttu-id="226d6-250">Este serviço especifica a chave a utilizar para parâmetros de autenticação no parâmetro de segurança SNMPv3 para todos os pedidos feitos após a sua fixação.</span><span class="sxs-lookup"><span data-stu-id="226d6-250">This service specifies the key to be used for authentication parameters in the SNMPv3 security parameter for all requests made after it is set.</span></span> <span data-ttu-id="226d6-251">Fornecer um valor NX_NULL para a autenticação desativar a chave.</span><span class="sxs-lookup"><span data-stu-id="226d6-251">Supplying a NX_NULL value for the key disables authentication.</span></span>

> [!NOTE]
> <span data-ttu-id="226d6-252">A chave deve ser previamente criada.</span><span class="sxs-lookup"><span data-stu-id="226d6-252">The key must be previously created.</span></span> <span data-ttu-id="226d6-253">Veja nx_snmp_agent_md5_key_create ou nx_snmp_agent_sha_key_create.</span><span class="sxs-lookup"><span data-stu-id="226d6-253">See nx_snmp_agent_md5_key_create or nx_snmp_agent_sha_key_create.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-254">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-254">Input Parameters</span></span>

- <span data-ttu-id="226d6-255">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-255">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-256">**chave** Ponteiro para uma tecla MD5 ou SHA previamente criada.</span><span class="sxs-lookup"><span data-stu-id="226d6-256">**key** Pointer to a previously created MD5 or SHA key.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-257">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-257">Return Values</span></span>

- <span data-ttu-id="226d6-258">**NX_SUCCESS** (0x00) Conjunto de teclas SNMP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="226d6-258">**NX_SUCCESS** (0x00) Successful SNMP key set.</span></span>
- <span data-ttu-id="226d6-259">**NX_NOT_ENABLED** (0x14) Segurança SNMP desativada</span><span class="sxs-lookup"><span data-stu-id="226d6-259">**NX_NOT_ENABLED** (0x14) SNMP Security disabled</span></span>
- <span data-ttu-id="226d6-260">**NX_PTR_ERROR** (0x07) Ponteiro do Agente SNMP inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-260">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-261">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-261">Allowed From</span></span>

<span data-ttu-id="226d6-262">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-262">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-263">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-263">Example</span></span>

```c
/* Use previously created “my_key” for SNMPv3 authentication.  */
status =  nx_snmp_agent_authenticate_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for setting the authentication parameters of SNMPv3 requests.  */
```

## <a name="nx_snmp_agent_community_get"></a><span data-ttu-id="226d6-264">nx_snmp_agent_community_get</span><span class="sxs-lookup"><span data-stu-id="226d6-264">nx_snmp_agent_community_get</span></span>
<span data-ttu-id="226d6-265">Recuperar o nome da comunidade</span><span class="sxs-lookup"><span data-stu-id="226d6-265">Retrieve community name</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-266">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-266">Prototype</span></span>

```c
UINT nx_snmp_agent_community_get(NX_SNMP_AGENT *agent_ptr, 
                                 UCHAR **community_string_ptr);
```

### <a name="description"></a><span data-ttu-id="226d6-267">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-267">Description</span></span>

<span data-ttu-id="226d6-268">Este serviço recupera o nome da comunidade a partir do mais recente pedido do SNMP recebido pelo Agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-268">This service retrieves the community name from the most recent SNMP request received by the SNMP Agent.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-269">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-269">Input Parameters</span></span>

- <span data-ttu-id="226d6-270">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-270">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-271">**community_string_ptr** Ponteiro para um ponteiro de cordas para devolver a corda comunitária do Agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-271">**community_string_ptr** Pointer to a string pointer to return the SNMP Agent community string.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-272">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-272">Return Values</span></span>

- <span data-ttu-id="226d6-273">**NX_SUCCESS** (0x00) comunidade SNMP bem sucedida obter.</span><span class="sxs-lookup"><span data-stu-id="226d6-273">**NX_SUCCESS** (0x00) Successful SNMP community get.</span></span>
- <span data-ttu-id="226d6-274">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-274">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-275">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-275">Allowed From</span></span>

<span data-ttu-id="226d6-276">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-276">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-277">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-277">Example</span></span>

```c
UCHAR *string_ptr;

/* Pickup the community string pointer for my_agent.  */
status =  nx_snmp_agent_community_get(&my_agent, &string_ptr);


/* If status is NX_SUCCESS the pointer “string_ptr” points to the
   last community name supplied to the SNMP agent.  */
```

## <a name="nx_snmp_agent_request_get_type_test"></a><span data-ttu-id="226d6-278">nx_snmp_agent_request_get_type_test</span><span class="sxs-lookup"><span data-stu-id="226d6-278">nx_snmp_agent_request_get_type_test</span></span>
<span data-ttu-id="226d6-279">Indicar se o último pedido do SNMP é tipo GET ou SET</span><span class="sxs-lookup"><span data-stu-id="226d6-279">Indicate if last SNMP request is GET or SET type</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-280">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-280">Prototype</span></span>

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

### <a name="description"></a><span data-ttu-id="226d6-281">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-281">Description</span></span>

<span data-ttu-id="226d6-282">Este serviço indica se o pedido mais recente do SNMP Manager é um tipo GET (GET, GETNEXT ou GETBULK) ou SET.</span><span class="sxs-lookup"><span data-stu-id="226d6-282">This service indicates if the most recent request from the SNMP Manager is a GET (GET, GETNEXT, or GETBULK) or SET type.</span></span> <span data-ttu-id="226d6-283">Destina-se a ser utilizado com o nome de utilizador onde a aplicação SNMPv1 ou SNMPv2 irá querer comparar a cadeia comunitária recebida com a cadeia pública do Agente SNMP se o pedido for um tipo GET, ou ao cordão privado do Agente SNMP se o pedido for um tipo SET.</span><span class="sxs-lookup"><span data-stu-id="226d6-283">It is intended for use with the username callback where the SNMPv1 or SNMPv2 application will want to compare the received community string to the SNMP Agent public string if the request is a GET type, or to the SNMP Agent private string if the request is a SET type.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-284">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-284">Input Parameters</span></span>

- <span data-ttu-id="226d6-285">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-285">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-286">**is_get_type** Ponteiro para solicitar o estado do tipo:</span><span class="sxs-lookup"><span data-stu-id="226d6-286">**is_get_type** Pointer to request type status:</span></span>  
<span data-ttu-id="226d6-287">NX_TRUE se tipo GET</span><span class="sxs-lookup"><span data-stu-id="226d6-287">NX_TRUE if GET type</span></span>  
<span data-ttu-id="226d6-288">NX_FALSE se definir o tipo</span><span class="sxs-lookup"><span data-stu-id="226d6-288">NX_FALSE if SET type</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-289">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-289">Return Values</span></span>

- <span data-ttu-id="226d6-290">**NX_SUCCESS** (0x00) Tipo devolvido com sucesso</span><span class="sxs-lookup"><span data-stu-id="226d6-290">**NX_SUCCESS** (0x00) Successfully returned type</span></span>
- <span data-ttu-id="226d6-291">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-291">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-292">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-292">Allowed From</span></span>

<span data-ttu-id="226d6-293">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-293">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-294">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-294">Example</span></span>

```c
UINT is_get_type;

/* Determine if the current SNMP request is a GET or SET type.  */
status =  nx_snmp_agent_request_get_type_test(&my_agent, &is_get_type);


/* If status is NX_SUCCESS, is_get_type will indicate the request type.  */
```

## <a name="nx_snmp_agent_context_engine_set"></a><span data-ttu-id="226d6-295">nx_snmp_agent_context_engine_set</span><span class="sxs-lookup"><span data-stu-id="226d6-295">nx_snmp_agent_context_engine_set</span></span>
<span data-ttu-id="226d6-296">Motor de contexto definido (apenas SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="226d6-296">Set context engine (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-297">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-297">Prototype</span></span>

```c
UINT nx_snmp_agent_context_engine_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *context_engine, 
                                      UINT context_engine_size);
```
### <a name="description"></a><span data-ttu-id="226d6-298">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-298">Description</span></span>

<span data-ttu-id="226d6-299">Este serviço define o motor de contexto do Agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-299">This service sets the context engine of the SNMP Agent.</span></span> <span data-ttu-id="226d6-300">Só é aplicável ao processamento do SNMPv3.</span><span class="sxs-lookup"><span data-stu-id="226d6-300">It is only applicable for SNMPv3 processing.</span></span> <span data-ttu-id="226d6-301">Isto deve ser chamado antes de criar chaves de segurança se a aplicação estiver a usar autenticação e encriptação, uma vez que o ID do motor de contexto é usado no processo de criação chave.</span><span class="sxs-lookup"><span data-stu-id="226d6-301">This should be called before creating security keys if the application is using authentication and encryption, since the context engine ID is used in the key creation process.</span></span> <span data-ttu-id="226d6-302">Caso contrário, o NetX Duo SNMP fornece um id de motor de contexto predefinido no topo da *nxd_snmp.c:*</span><span class="sxs-lookup"><span data-stu-id="226d6-302">If not, NetX Duo SNMP provides a default context engine id at the top of *nxd_snmp.c:*</span></span>

```c
UCHAR _nx_snmp_default_context_engine[NX_SNMP_MAX_CONTEXT_STRING] =  
                {0x80, 0x00, 0x03, 0x10, 0x01, 0xc0, 0xa8, 0x64, 0xaf};

```

### <a name="input-parameters"></a><span data-ttu-id="226d6-303">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-303">Input Parameters</span></span>

- <span data-ttu-id="226d6-304">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-304">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-305">**context_engine** Ponteiro para a corda do motor de contexto.</span><span class="sxs-lookup"><span data-stu-id="226d6-305">**context_engine** Pointer to the context engine string.</span></span>
- <span data-ttu-id="226d6-306">**context_engine_size** Tamanho da corda do motor de contexto.</span><span class="sxs-lookup"><span data-stu-id="226d6-306">**context_engine_size** Size of context engine string.</span></span> <span data-ttu-id="226d6-307">Note que o número máximo de bytes num motor de contexto é definido por NX_SNMP_MAX_CONTEXT_STRING.</span><span class="sxs-lookup"><span data-stu-id="226d6-307">Note that the maximum number of bytes in a context engine is defined by NX_SNMP_MAX_CONTEXT_STRING.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-308">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-308">Return Values</span></span>

- <span data-ttu-id="226d6-309">**NX_SUCCESS** (0x00) Conjunto de motores de contexto SNMP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="226d6-309">**NX_SUCCESS** (0x00) Successful SNMP context engine set.</span></span>
- <span data-ttu-id="226d6-310">**NX_NOT_ENABLED** (0x14) SNMPv3 não está ativado</span><span class="sxs-lookup"><span data-stu-id="226d6-310">**NX_NOT_ENABLED** (0x14) SNMPv3 is not enabled</span></span>
- <span data-ttu-id="226d6-311">**NX_SNMP_ERROR** (0x100) Erro de tamanho do motor de contexto.</span><span class="sxs-lookup"><span data-stu-id="226d6-311">**NX_SNMP_ERROR** (0x100) Context engine size error.</span></span>
- <span data-ttu-id="226d6-312">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-312">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-313">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-313">Allowed From</span></span>

<span data-ttu-id="226d6-314">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-314">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-315">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-315">Example</span></span>

```c
UCHAR my_engine[] = {0x80, 0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07};

/* Set the context engine for my_agent.  */
status =  nx_snmp_agent_context_engine_set(&my_agent, my_engine, 9);


/* If status is NX_SUCCESS the context engine has been set.  */
```
## <a name="nx_snmp_agent_context_name_set"></a><span data-ttu-id="226d6-316">nx_snmp_agent_context_name_set</span><span class="sxs-lookup"><span data-stu-id="226d6-316">nx_snmp_agent_context_name_set</span></span>
<span data-ttu-id="226d6-317">Definir nome de contexto (apenas SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="226d6-317">Set context name (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-318">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-318">Prototype</span></span>

```c
UINT nx_snmp_agent_context_name_set(NX_SNMP_AGENT *agent_ptr, 
                                    UCHAR *context_name, 
                                    UINT context_name_size);
```

### <a name="description"></a><span data-ttu-id="226d6-319">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-319">Description</span></span>

<span data-ttu-id="226d6-320">Este serviço define o nome de contexto do Agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-320">This service sets the context name of the SNMP Agent.</span></span> <span data-ttu-id="226d6-321">Só é aplicável ao processamento do SNMPv3.</span><span class="sxs-lookup"><span data-stu-id="226d6-321">It is only applicable for SNMPv3 processing.</span></span> <span data-ttu-id="226d6-322">Se não for chamado, o Agente SNMP da NetX Duo deixará o nome de contexto em branco.</span><span class="sxs-lookup"><span data-stu-id="226d6-322">If not called, NetX Duo SNMP Agent will leave the context name blank.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-323">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-323">Input Parameters</span></span>

- <span data-ttu-id="226d6-324">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-324">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-325">**context_name** Ponteiro para a cadeia de nome de contexto.</span><span class="sxs-lookup"><span data-stu-id="226d6-325">**context_name** Pointer to the context name string.</span></span>
- <span data-ttu-id="226d6-326">**context_name_size** Tamanho da cadeia de nome de contexto.</span><span class="sxs-lookup"><span data-stu-id="226d6-326">**context_name_size** Size of context name string.</span></span> <span data-ttu-id="226d6-327">Note que o número máximo de bytes em um nome de contexto é definido por NX_SNMP_MAX_CONTEXT_STRING.</span><span class="sxs-lookup"><span data-stu-id="226d6-327">Note that the maximum number of bytes in a context name is defined by NX_SNMP_MAX_CONTEXT_STRING.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-328">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-328">Return Values</span></span>

- <span data-ttu-id="226d6-329">**NX_SUCCESS** (0x00) Conjunto de nomes de contexto SNMP bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="226d6-329">**NX_SUCCESS** (0x00) Successful SNMP context name set.</span></span>
- <span data-ttu-id="226d6-330">**NX_SNMP_ERROR** (0x100) Erro de tamanho do nome do contexto.</span><span class="sxs-lookup"><span data-stu-id="226d6-330">**NX_SNMP_ERROR** (0x100) Context name size error.</span></span>
- <span data-ttu-id="226d6-331">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-331">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-332">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-332">Allowed From</span></span>

<span data-ttu-id="226d6-333">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-333">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-334">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-334">Example</span></span>

```c
/* Set the context name for my_agent.  */
status =  nx_snmp_agent_context_name_set(&my_agent, “my_context_name”, 15);


/* If status is NX_SUCCESS the context name has been set.  */
```

## <a name="nx_snmp_agent_create"></a><span data-ttu-id="226d6-335">nx_snmp_agent_create</span><span class="sxs-lookup"><span data-stu-id="226d6-335">nx_snmp_agent_create</span></span>
<span data-ttu-id="226d6-336">Criar agente SNMP</span><span class="sxs-lookup"><span data-stu-id="226d6-336">Create SNMP agent</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-337">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-337">Prototype</span></span>

```c
UINT nx_snmp_agent_create(NX_SNMP_AGENT *agent_ptr, 
      CHAR *snmp_agent_name, NX_IP *ip_ptr, VOID *stack_ptr, 
      ULONG stack_size, NX_PACKET_POOL *pool_ptr,
      UINT (*snmp_agent_username_process)(struct NX_SNMP_AGENT_STRUCT 
                                    *agent_ptr, UCHAR *username),
      UINT (*snmp_agent_get_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_getnext_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_set_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data));
```
### <a name="description"></a><span data-ttu-id="226d6-338">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-338">Description</span></span>

<span data-ttu-id="226d6-339">Este serviço cria um Agente SNMP na instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="226d6-339">This service creates a SNMP Agent on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-340">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-340">Input Parameters</span></span>

- <span data-ttu-id="226d6-341">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-341">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-342">**snmp_agent_name** Ponteiro para a cadeia de nomes do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-342">**snmp_agent_name** Pointer to the SNMP Agent name string.</span></span>
- <span data-ttu-id="226d6-343">**ip_ptr** Ponteiro para a instância IP.</span><span class="sxs-lookup"><span data-stu-id="226d6-343">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="226d6-344">**stack_ptr** Ponteiro para o ponteiro da pilha de fio do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-344">**stack_ptr** Pointer to SNMP Agent thread stack pointer.</span></span>
- <span data-ttu-id="226d6-345">**stack_size** Tamanho da pilha em bytes.</span><span class="sxs-lookup"><span data-stu-id="226d6-345">**stack_size** Stack size in bytes.</span></span>
- <span data-ttu-id="226d6-346">**pool_ptr** Ponter a piscina de pacotes predefinidos para este Agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-346">**pool_ptr** Pointer the default packet pool for this SNMP Agent.</span></span>
- <span data-ttu-id="226d6-347">**snmp_agent_username_process** Função ponteiro para a rotina de manuseamento do nome de utilizador da aplicação.</span><span class="sxs-lookup"><span data-stu-id="226d6-347">**snmp_agent_username_process** Function pointer to application’s username handling routine.</span></span>
- <span data-ttu-id="226d6-348">**snmp_agent_get_process** Função ponteiro para a rotina de tratamento do pedido GET da aplicação.</span><span class="sxs-lookup"><span data-stu-id="226d6-348">**snmp_agent_get_process** Function pointer to application’s GET request handling routine.</span></span>
- <span data-ttu-id="226d6-349">**snmp_agent_getnext_process** Função ponteiro para a rotina de tratamento do pedido GETNEXT da aplicação.</span><span class="sxs-lookup"><span data-stu-id="226d6-349">**snmp_agent_getnext_process** Function pointer to application’s GETNEXT request handling routine.</span></span>
- <span data-ttu-id="226d6-350">**snmp_agent_set_process** Função ponteiro para a rotina de tratamento do pedido set da aplicação.</span><span class="sxs-lookup"><span data-stu-id="226d6-350">**snmp_agent_set_process** Function pointer to application’s SET request handling routine.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-351">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-351">Return Values</span></span>

- <span data-ttu-id="226d6-352">**NX_SUCCESS** (0x00) Agente SNMP bem sucedido criar.</span><span class="sxs-lookup"><span data-stu-id="226d6-352">**NX_SUCCESS** (0x00) Successful SNMP Agent create.</span></span>
- <span data-ttu-id="226d6-353">**NX_SNMP_ERROR** (0x100) O Agente SNMP cria erro.</span><span class="sxs-lookup"><span data-stu-id="226d6-353">**NX_SNMP_ERROR** (0x100) SNMP Agent create error.</span></span>
- <span data-ttu-id="226d6-354">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-354">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-355">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-355">Allowed From</span></span>

<span data-ttu-id="226d6-356">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-356">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-357">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-357">Example</span></span>

```c
NX_SNMP_AGENT my_agent;

/* Create the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_create(&my_agent, "My SNMP Agent", &ip_0, stack_start_ptr,
                4096, &pool_0, my_username_processing, my_get_processing, 
                my_getnext_processing, my_set_processing);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been created.  */
```

## <a name="nx_snmp_agent_current_version_get"></a><span data-ttu-id="226d6-358">nx_snmp_agent_current_version_get</span><span class="sxs-lookup"><span data-stu-id="226d6-358">nx_snmp_agent_current_version_get</span></span>
<span data-ttu-id="226d6-359">Obtenha a versão do pacote SNMP</span><span class="sxs-lookup"><span data-stu-id="226d6-359">Get the SNMP packet version</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-360">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-360">Prototype</span></span>

```c
UINT nx_snmp_agent_current_version_get(NX_SNMP_AGENT *agent_ptr, 
                                       UINT *version);
```

### <a name="description"></a><span data-ttu-id="226d6-361">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-361">Description</span></span>

<span data-ttu-id="226d6-362">Este serviço recupera a versão SNMP analisada a partir do mais recente pacote SNMP recebido.</span><span class="sxs-lookup"><span data-stu-id="226d6-362">This service retrieves the SNMP version parsed from the most recent SNMP packet received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-363">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-363">Input Parameters</span></span>

- <span data-ttu-id="226d6-364">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-364">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-365">**versão** Ponteiro para a versão SNMP analisada a partir do pacote SNMP recebido</span><span class="sxs-lookup"><span data-stu-id="226d6-365">**version** Pointer to the SNMP version parsed from received SNMP packet</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-366">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-366">Return Values</span></span>

- <span data-ttu-id="226d6-367">**NX_SUCCESS** (0x00) Versão SNMP bem sucedida obter</span><span class="sxs-lookup"><span data-stu-id="226d6-367">**NX_SUCCESS** (0x00) Successful SNMP version get</span></span>
- <span data-ttu-id="226d6-368">**NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="226d6-368">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-369">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-369">Allowed From</span></span>

<span data-ttu-id="226d6-370">Fios</span><span class="sxs-lookup"><span data-stu-id="226d6-370">Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-371">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-371">Example</span></span>

```c
UINT          snmp_version;
NX_SNMP_AGENT my_agent;

/* Get the version of the last received SNMP packet. */
status =  nx_snmp_agent_current_version_get (&my_agent, &snmp_version);


/* If status is NX_SUCCESS, snmp_version contains 
   the received packet SNMP version.  */
```

## <a name="nx_snmp_agent_private_string_test"></a><span data-ttu-id="226d6-372">nx_snmp_agent_private_string_test</span><span class="sxs-lookup"><span data-stu-id="226d6-372">nx_snmp_agent_private_string_test</span></span>
<span data-ttu-id="226d6-373">Verifique as combinações de cordas privadas Agente cadeia privada</span><span class="sxs-lookup"><span data-stu-id="226d6-373">Verify private string matches Agent private string</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-374">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-374">Prototype</span></span>

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr, 
                                       UCHAR *community_string,          
                                       UINT *is_private);
```

### <a name="description"></a><span data-ttu-id="226d6-375">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-375">Description</span></span>

<span data-ttu-id="226d6-376">Este serviço compara a cadeia comunitária de entrada terminada com a cadeia privada do agente SNMP e indica se coincidem.</span><span class="sxs-lookup"><span data-stu-id="226d6-376">This service compares the null terminated input community string with the SNMP agent private string and indicates if they match.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-377">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-377">Input Parameters</span></span>

- <span data-ttu-id="226d6-378">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-378">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-379">**community_string** Ponteiro para cadeia para comparar</span><span class="sxs-lookup"><span data-stu-id="226d6-379">**community_string** Pointer to string to compare</span></span>
- <span data-ttu-id="226d6-380">**is_private** Ponteiro para o resultado da comparação</span><span class="sxs-lookup"><span data-stu-id="226d6-380">**is_private** Pointer to result of comparison</span></span>  
<span data-ttu-id="226d6-381">NX_TRUE - fósforos de cordas</span><span class="sxs-lookup"><span data-stu-id="226d6-381">NX_TRUE - string matches</span></span>  
<span data-ttu-id="226d6-382">NX_FALSE - a corda não combina</span><span class="sxs-lookup"><span data-stu-id="226d6-382">NX_FALSE - string does not match</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-383">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-383">Return Values</span></span>

- <span data-ttu-id="226d6-384">**NX_SUCCESS** (0x00) Comparação bem sucedida</span><span class="sxs-lookup"><span data-stu-id="226d6-384">**NX_SUCCESS** (0x00) Successful comparison</span></span>
- <span data-ttu-id="226d6-385">**NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="226d6-385">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-386">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-386">Allowed From</span></span>

<span data-ttu-id="226d6-387">Fios</span><span class="sxs-lookup"><span data-stu-id="226d6-387">Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-388">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-388">Example</span></span>

```c
UINT        is_private;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;

/* Determine if the community string matches the agent private string */
status =  nx_snmp_agent_private_string_test(&my_agent, community_string_ptr,  
                                            &is_private);


/* If status is NX_SUCCESS, is_private will indicate if there is a match. 
   If is_private is NX_TRUE, they match.  */
```

## <a name="nx_snmp_agent_public_string_test"></a><span data-ttu-id="226d6-389">nx_snmp_agent_public_string_test</span><span class="sxs-lookup"><span data-stu-id="226d6-389">nx_snmp_agent_public_string_test</span></span>
<span data-ttu-id="226d6-390">Verifique se a corda pública recebida corresponde à cadeia pública do agente</span><span class="sxs-lookup"><span data-stu-id="226d6-390">Verify received public string matches Agent’s public string</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-391">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-391">Prototype</span></span>

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string,          
                                      UINT *is_public);
```
### <a name="description"></a><span data-ttu-id="226d6-392">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-392">Description</span></span>

<span data-ttu-id="226d6-393">Este serviço compara uma cadeia comunitária de entrada terminada com a cadeia pública do agente SNMP e indica se correspondem.</span><span class="sxs-lookup"><span data-stu-id="226d6-393">This service compares a null terminated input community string with the SNMP agent public string and indicates if they match.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-394">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-394">Input Parameters</span></span>

- <span data-ttu-id="226d6-395">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-395">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-396">**community_string** Ponteiro para cadeia para comparar</span><span class="sxs-lookup"><span data-stu-id="226d6-396">**community_string** Pointer to string to compare</span></span>
- <span data-ttu-id="226d6-397">**is_public** Ponteiro para o resultado da comparação</span><span class="sxs-lookup"><span data-stu-id="226d6-397">**is_public** Pointer to result of comparison</span></span>  
<span data-ttu-id="226d6-398">NX_TRUE - fósforos de cordas</span><span class="sxs-lookup"><span data-stu-id="226d6-398">NX_TRUE - string matches</span></span>  
<span data-ttu-id="226d6-399">NX_FALSE - a corda não combina</span><span class="sxs-lookup"><span data-stu-id="226d6-399">NX_FALSE - string does not match</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-400">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-400">Return Values</span></span>

- <span data-ttu-id="226d6-401">**NX_SUCCESS** (0x00) Comparação bem sucedida</span><span class="sxs-lookup"><span data-stu-id="226d6-401">**NX_SUCCESS** (0x00) Successful comparison</span></span>
- <span data-ttu-id="226d6-402">**NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="226d6-402">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-403">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-403">Allowed From</span></span>

<span data-ttu-id="226d6-404">Fios</span><span class="sxs-lookup"><span data-stu-id="226d6-404">Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-405">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-405">Example</span></span>

```c
UINT        is_public;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;


/* Determine if the community string matches the agent public string */
status =  nx_snmp_agent_public_string_test(&my_agent, community_string_ptr,  
                                           &is_public);


/* If status is NX_SUCCESS, is_public will indicate if there is a match. 
   If is_public is true they match.  */
```

## <a name="nx_snmp_agent_version_set"></a><span data-ttu-id="226d6-406">nx_snmp_agent_version_set</span><span class="sxs-lookup"><span data-stu-id="226d6-406">nx_snmp_agent_version_set</span></span>
<span data-ttu-id="226d6-407">Desaponte o estado do agente SNMP para cada versão SNMP</span><span class="sxs-lookup"><span data-stu-id="226d6-407">Set the SNMP agent status for each SNMP version</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-408">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-408">Prototype</span></span>

```c
UINT nx_snmp_agent_version_set(NX_SNMP_AGENT *agent_ptr, 
                               UINT enabled_v1, UINT enable_v2, 
                               UINT enable_v3);
```

### <a name="description"></a><span data-ttu-id="226d6-409">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-409">Description</span></span>

<span data-ttu-id="226d6-410">Este serviço define o estado (ativado/desativado) para cada uma das versões SNMP, V1, V2 e V3 no agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-410">This service sets the status (enabled/disabled) for each of the SNMP versions, V1, V2 and V3 on the SNMP agent.</span></span> <span data-ttu-id="226d6-411">Note que as opções configuráveis do utilizador, NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 e NX_SNMP_DISABLE_V3, irão anular estas definições de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="226d6-411">Note that the user configurable options, NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2, and NX_SNMP_DISABLE_V3, will override these run time settings.</span></span> <span data-ttu-id="226d6-412">Por predefinição, o agente SNMP está ativado para as três versões.</span><span class="sxs-lookup"><span data-stu-id="226d6-412">By default, the SNMP agent is enabled for all three versions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-413">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-413">Input Parameters</span></span>

- <span data-ttu-id="226d6-414">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-414">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-415">**enabled_v1** Define o estado ativado para o SNMP V1 para dentro/para fora.</span><span class="sxs-lookup"><span data-stu-id="226d6-415">**enabled_v1** Sets enabled status for SNMP V1 to on/off.</span></span>
- <span data-ttu-id="226d6-416">**enabled_v2** Define o estado ativado para o SNMP V2 para dentro/para fora.</span><span class="sxs-lookup"><span data-stu-id="226d6-416">**enabled_v2** Sets enabled status for SNMP V2 to on/off.</span></span>
- <span data-ttu-id="226d6-417">**enabled_v3** Define o estado ativado para o SNMP V3 para dentro/para fora.</span><span class="sxs-lookup"><span data-stu-id="226d6-417">**enabled_v3** Sets enabled status for SNMP V3 to on/off.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-418">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-418">Return Values</span></span>

- <span data-ttu-id="226d6-419">**NX_SUCCESS** (0x00) Conjunto de versão SNMP bem-sucedida</span><span class="sxs-lookup"><span data-stu-id="226d6-419">**NX_SUCCESS** (0x00) Successful SNMP version set</span></span>
- <span data-ttu-id="226d6-420">**NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="226d6-420">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-421">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-421">Allowed From</span></span>

<span data-ttu-id="226d6-422">Fios</span><span class="sxs-lookup"><span data-stu-id="226d6-422">Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-423">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-423">Example</span></span>

```c
UINT          v1_on = NX_TRUE;
UINT          v2_on = NX_TRUE;
UINT          v3_on = NX_FALSE;

NX_SNMP_AGENT my_agent;

/* Enable/Disable each SNMP protocol (version) for the SNMP Agent) */
status =  nx_snmp_agent_version_set(&my_agent, v1_on, v2_on, v3_on);


/* If status is NX_SUCCESS, my_agent is enabled only for V1 and V2 assuming 
   NX_SNMP_DISABLE_V1 and NX_SNMP_DISABLE_V2 are not defined. */
```

## <a name="nx_snmp_agent_private_string_set"></a><span data-ttu-id="226d6-424">nx_snmp_agent_private_string_set</span><span class="sxs-lookup"><span data-stu-id="226d6-424">nx_snmp_agent_private_string_set</span></span>
<span data-ttu-id="226d6-425">Desaponte a corda privada do agente SNMP</span><span class="sxs-lookup"><span data-stu-id="226d6-425">Set the SNMP agent private string</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-426">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-426">Prototype</span></span>

```c
UINT nx_snmp_agent_private_string_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string);
```

### <a name="description"></a><span data-ttu-id="226d6-427">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-427">Description</span></span>

<span data-ttu-id="226d6-428">Este serviço define a cadeia comunitária privada do agente SNMP com a corda terminada nulo de entrada.</span><span class="sxs-lookup"><span data-stu-id="226d6-428">This service sets the SNMP agent private community string with the input null terminated string.</span></span> <span data-ttu-id="226d6-429">O valor predefinido é NU (nenhum conjunto de cordas privada), de modo que qualquer pacote SNMP recebido com uma cadeia comunitária "privada" não será aceite pelo agente SNMP para acesso de leitura/escrita.</span><span class="sxs-lookup"><span data-stu-id="226d6-429">The default value is NULL (no private string set), such that any SNMP packet received with a “private” community string will not be accepted by the SNMP agent for read/write access.</span></span> <span data-ttu-id="226d6-430">O fio de entrada deve ser inferior ou igual ao tamanho configurável do utilizador NX_SNMP_MAX_USER_NAME-1 (para permitir a interrupção do tamanho).</span><span class="sxs-lookup"><span data-stu-id="226d6-430">The input string must be less than or equal to the user configurable NX_SNMP_MAX_USER_NAME-1 (to allow room for null termination) size.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-431">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-431">Input Parameters</span></span>

- <span data-ttu-id="226d6-432">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-432">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-433">**community_string** Ponteiro para a cadeia privada para atribuir</span><span class="sxs-lookup"><span data-stu-id="226d6-433">**community_string** Pointer to the private string to assign</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-434">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-434">Return Values</span></span>

- <span data-ttu-id="226d6-435">**NX_SUCCESS** (0x00) definir com sucesso a corda privada</span><span class="sxs-lookup"><span data-stu-id="226d6-435">**NX_SUCCESS** (0x00) Successfully set private string</span></span>
- <span data-ttu-id="226d6-436">**NX_SNMP_ERROR_TOOBIG** (0x01) Tamanho da corda muito grande</span><span class="sxs-lookup"><span data-stu-id="226d6-436">**NX_SNMP_ERROR_TOOBIG** (0x01) String size too large</span></span> 
- <span data-ttu-id="226d6-437">**NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="226d6-437">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-438">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-438">Allowed From</span></span>

<span data-ttu-id="226d6-439">Fios</span><span class="sxs-lookup"><span data-stu-id="226d6-439">Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-440">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-440">Example</span></span>

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s private community string */
status =  nx_snmp_agent_private_string_set(&my_agent, “private”));


/* If status is NX_SUCCESS, the SNMP agent private string is set.  */
```

## <a name="nx_snmp_agent_public_string_set"></a><span data-ttu-id="226d6-441">nx_snmp_agent_public_string_set</span><span class="sxs-lookup"><span data-stu-id="226d6-441">nx_snmp_agent_public_string_set</span></span>
<span data-ttu-id="226d6-442">Definir a cadeia pública do agente SNMP</span><span class="sxs-lookup"><span data-stu-id="226d6-442">Set the SNMP agent public string</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-443">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-443">Prototype</span></span>

```c
UINT nx_snmp_agent_public_string_set(NX_SNMP_AGENT *agent_ptr, 
                                     UCHAR *community_string);
```

### <a name="description"></a><span data-ttu-id="226d6-444">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-444">Description</span></span>

<span data-ttu-id="226d6-445">Este serviço define a cadeia da comunidade pública do agente SNMP com a corda terminada nulo de entrada.</span><span class="sxs-lookup"><span data-stu-id="226d6-445">This service sets the SNMP agent public community string with the input null terminated string.</span></span> <span data-ttu-id="226d6-446">O fio comunitário deve ser inferior ou igual ao tamanho configurável do utilizador NX_SNMP_MAX_USER_NAME-1 (para permitir espaço para rescisão nulo).</span><span class="sxs-lookup"><span data-stu-id="226d6-446">The community string must be less than or equal to the user configurable NX_SNMP_MAX_USER_NAME-1 (to allow room for null termination) size.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-447">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-447">Input Parameters</span></span>

- <span data-ttu-id="226d6-448">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-448">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-449">**community_string** Ponteiro para a cadeia pública para atribuir</span><span class="sxs-lookup"><span data-stu-id="226d6-449">**community_string** Pointer to the public string to assign</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-450">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-450">Return Values</span></span>

- <span data-ttu-id="226d6-451">**NX_SUCCESS** (0x00) definir com sucesso a corda pública</span><span class="sxs-lookup"><span data-stu-id="226d6-451">**NX_SUCCESS** (0x00) Successfully set public string</span></span>
- <span data-ttu-id="226d6-452">**NX_SNMP_ERROR_TOOBIG** (0x01) Tamanho da corda muito grande</span><span class="sxs-lookup"><span data-stu-id="226d6-452">**NX_SNMP_ERROR_TOOBIG** (0x01) String size too large</span></span>
- <span data-ttu-id="226d6-453">**NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="226d6-453">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-454">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-454">Allowed From</span></span>

<span data-ttu-id="226d6-455">Fios</span><span class="sxs-lookup"><span data-stu-id="226d6-455">Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-456">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-456">Example</span></span>

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s public string. */
nx_snmp_agent_public_string_set(&my_agent, “my_public”));


/* If status is NX_SUCCESS, the SNMP agent public string is set.  */
```

## <a name="nx_snmp_agent_delete"></a><span data-ttu-id="226d6-457">nx_snmp_agent_delete</span><span class="sxs-lookup"><span data-stu-id="226d6-457">nx_snmp_agent_delete</span></span>
<span data-ttu-id="226d6-458">Eliminar agente SNMP</span><span class="sxs-lookup"><span data-stu-id="226d6-458">Delete SNMP agent</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-459">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-459">Prototype</span></span>

```C
UINT nx_snmp_agent_delete(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a><span data-ttu-id="226d6-460">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-460">Description</span></span>

<span data-ttu-id="226d6-461">Este serviço elimina um Agente SNMP previamente criado.</span><span class="sxs-lookup"><span data-stu-id="226d6-461">This service deletes a previously created SNMP Agent.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-462">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-462">Input Parameters</span></span>

- <span data-ttu-id="226d6-463">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-463">**agent_ptr** Pointer to SNMP Agent control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-464">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-464">Return Values</span></span>

- <span data-ttu-id="226d6-465">**NX_SUCCESS** (0x00) Agente SNMP bem sucedido apagar.</span><span class="sxs-lookup"><span data-stu-id="226d6-465">**NX_SUCCESS** (0x00) Successful SNMP Agent delete.</span></span>
- <span data-ttu-id="226d6-466">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-466">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-467">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-467">Allowed From</span></span>

<span data-ttu-id="226d6-468">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-468">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-469">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-469">Example</span></span>

```c
/* Delete the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_delete(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been deleted.  */
```

## <a name="nx_snmp_agent_set_interface"></a><span data-ttu-id="226d6-470">nx_snmp_agent_set_interface</span><span class="sxs-lookup"><span data-stu-id="226d6-470">nx_snmp_agent_set_interface</span></span>
<span data-ttu-id="226d6-471">Definir a interface de rede de agente SNMP</span><span class="sxs-lookup"><span data-stu-id="226d6-471">Set the SNMP agent network interface</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-472">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-472">Prototype</span></span>

```c
UINT nx_snmp_agent_set_interface(NX_SNMP_AGENT *agent_ptr,  
                                 UINT if_index);
```

### <a name="description"></a><span data-ttu-id="226d6-473">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-473">Description</span></span>

<span data-ttu-id="226d6-474">Este serviço define a interface de rede SNMP para o Agente SNMP, conforme especificado pelo índice de interface de entrada.</span><span class="sxs-lookup"><span data-stu-id="226d6-474">This service sets the SNMP network interface for the SNMP Agent as specified by the input interface index.</span></span> <span data-ttu-id="226d6-475">Isto só é útil para aplicações de anfitriões SNMP com NetX Duo 5.6 ou superior que suportam múltiplas interfaces de rede.</span><span class="sxs-lookup"><span data-stu-id="226d6-475">This is only useful for SNMP host applications with NetX Duo 5.6 or higher which support multiple network interfaces.</span></span> <span data-ttu-id="226d6-476">O valor predefinido se não especificado pelo hospedeiro é zero, para a interface primária.</span><span class="sxs-lookup"><span data-stu-id="226d6-476">The default value if not specified by the host is zero, for the primary interface.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-477">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-477">Input Parameters</span></span>

- <span data-ttu-id="226d6-478">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-478">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-479">**If_index** Índice que especifica a interface SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-479">**If_index** Index specifying the SNMP interface.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-480">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-480">Return Values</span></span>

- <span data-ttu-id="226d6-481">**NX_SUCCESS** (0x00) Conjunto de interface SNMP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="226d6-481">**NX_SUCCESS** (0x00) Successful SNMP interface set.</span></span>
- <span data-ttu-id="226d6-482">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-482">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-483">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-483">Allowed From</span></span>

<span data-ttu-id="226d6-484">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-484">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-485">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-485">Example</span></span>

```c
/* Set the SNMP Agent “my_agent” to the secondary interface.  */
if_index = 1;
status =  nx_snmp_agent_set_interface(&my_agent, if_index);


/* If status is NX_SUCCESS the SNMP agent interface is set.  */
```

## <a name="nx_snmp_agent_md5_key_create"></a><span data-ttu-id="226d6-486">nx_snmp_agent_md5_key_create</span><span class="sxs-lookup"><span data-stu-id="226d6-486">nx_snmp_agent_md5_key_create</span></span>
<span data-ttu-id="226d6-487">Criar tecla md5 (apenas SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="226d6-487">Create md5 key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-488">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-488">Prototype</span></span>

```c
UINT nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY 
                                       *destination_key);
```
### <a name="description"></a><span data-ttu-id="226d6-489">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-489">Description</span></span>

<span data-ttu-id="226d6-490">Este serviço cria uma chave MD5 que pode ser usada para autenticação e encriptação.</span><span class="sxs-lookup"><span data-stu-id="226d6-490">This service creates a MD5 key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="226d6-491">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="226d6-491">This service is deprecated.</span></span> <span data-ttu-id="226d6-492">Os desenvolvedores são encorajados a migrar para *nx_snmp_agent_md5_key_create_extended()*.</span><span class="sxs-lookup"><span data-stu-id="226d6-492">Developers are encouraged to migrate to *nx_snmp_agent_md5_key_create_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-493">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-493">Input Parameters</span></span>

- <span data-ttu-id="226d6-494">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-494">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-495">**senha** Ponteiro para a corda de senha.</span><span class="sxs-lookup"><span data-stu-id="226d6-495">**password** Pointer to password string.</span></span>
- <span data-ttu-id="226d6-496">**destination_key** Ponteiro para estrutura de dados chave SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-496">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-497">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-497">Return Values</span></span>

- <span data-ttu-id="226d6-498">**NX_SUCCESS** (0x00) Chave de sucesso criar.</span><span class="sxs-lookup"><span data-stu-id="226d6-498">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="226d6-499">**NX_NOT_ENABLED** (0x14) Segurança não ativada.</span><span class="sxs-lookup"><span data-stu-id="226d6-499">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="226d6-500">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-500">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-501">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-501">Allowed From</span></span>

<span data-ttu-id="226d6-502">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-502">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-503">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-503">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS an MD5 key has been created.  */
```

## <a name="nx_snmp_agent_md5_key_create_extended"></a><span data-ttu-id="226d6-504">nx_snmp_agent_md5_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="226d6-504">nx_snmp_agent_md5_key_create_extended</span></span>
<span data-ttu-id="226d6-505">Criar tecla md5 (apenas SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="226d6-505">Create md5 key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-506">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-506">Prototype</span></span>

```c
UINT nx_snmp_agent_md5_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY 
                                           *destination_key);
```
### <a name="description"></a><span data-ttu-id="226d6-507">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-507">Description</span></span>

<span data-ttu-id="226d6-508">Este serviço cria uma chave MD5 que pode ser usada para autenticação e encriptação.</span><span class="sxs-lookup"><span data-stu-id="226d6-508">This service creates a MD5 key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="226d6-509">Este serviço substitui *nx_snmp_agent_md5_key_create.*</span><span class="sxs-lookup"><span data-stu-id="226d6-509">This service replaces *nx_snmp_agent_md5_key_create().*</span></span> <span data-ttu-id="226d6-510">Esta versão requer que o chamador forneça o comprimento da palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="226d6-510">This version requires caller to supply password length.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-511">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-511">Input Parameters</span></span>

- <span data-ttu-id="226d6-512">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-512">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-513">**senha** Ponteiro para a corda de senha.</span><span class="sxs-lookup"><span data-stu-id="226d6-513">**password** Pointer to password string.</span></span>
- <span data-ttu-id="226d6-514">**password_length** Comprimento da corda da palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="226d6-514">**password_length** Length of password string.</span></span>
- <span data-ttu-id="226d6-515">**destination_key** Ponteiro para estrutura de dados chave SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-515">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-516">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-516">Return Values</span></span>

- <span data-ttu-id="226d6-517">**NX_SUCCESS** (0x00) Chave de sucesso criar.</span><span class="sxs-lookup"><span data-stu-id="226d6-517">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="226d6-518">**NX_NOT_ENABLED** (0x14) Segurança não ativada.</span><span class="sxs-lookup"><span data-stu-id="226d6-518">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="226d6-519">**NX_SNMP_FAILED** (0x102) O SNMP falhou.</span><span class="sxs-lookup"><span data-stu-id="226d6-519">**NX_SNMP_FAILED** (0x102) SNMP failed.</span></span>
- <span data-ttu-id="226d6-520">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-520">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-521">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-521">Allowed From</span></span>

<span data-ttu-id="226d6-522">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-522">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-523">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-523">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_priv_trap_key_use"></a><span data-ttu-id="226d6-524">nx_snmp_agent_priv_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="226d6-524">nx_snmp_agent_priv_trap_key_use</span></span>
<span data-ttu-id="226d6-525">Especifique a chave de encriptação para mensagens de armadilha</span><span class="sxs-lookup"><span data-stu-id="226d6-525">Specify encryption key for trap messages</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-526">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-526">Prototype</span></span>

```c
UINT nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```

### <a name="description"></a><span data-ttu-id="226d6-527">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-527">Description</span></span>

<span data-ttu-id="226d6-528">Este serviço especifica que uma chave de privacidade previamente criada deve ser usada para encriptação e desencriptação de mensagens de armadilha SNMPv3.</span><span class="sxs-lookup"><span data-stu-id="226d6-528">This service specifies that a previously created privacy key is to be used for encryption and decryption of SNMPv3 trap messages.</span></span>

> [!NOTE]
> <span data-ttu-id="226d6-529">*Uma chave de autenticação deve ser previamente criada. A privacidade do SNMP v3 (encriptação) requer autenticação. Consulte nx_snmp_agent_auth_trap_key_use para mais detalhes.*</span><span class="sxs-lookup"><span data-stu-id="226d6-529">*An authentictation key must be previously created. SNMP v3 privacy (encryption) requires authentication. See nx_snmp_agent_auth_trap_key_use for details.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-530">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-530">Input Parameters</span></span>

- <span data-ttu-id="226d6-531">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-531">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-532">**chave** Ponteiro para criar previamente a chave.</span><span class="sxs-lookup"><span data-stu-id="226d6-532">**key** Pointer to previously create key.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-533">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-533">Return Values</span></span>

- <span data-ttu-id="226d6-534">**NX_SUCCESS** (0x00) Conjunto de chaves de privacidade bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="226d6-534">**NX_SUCCESS** (0x00) Successful privacy key set.</span></span>
- <span data-ttu-id="226d6-535">**NX_NOT_ENABLED** (0x14) Segurança não ativada.</span><span class="sxs-lookup"><span data-stu-id="226d6-535">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="226d6-536">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-536">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-537">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-537">Allowed From</span></span>

<span data-ttu-id="226d6-538">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-538">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-539">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-539">Example</span></span>

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent” trap messages.   */
status =  nx_snmp_agent_priv_trap_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_privacy_key_use"></a><span data-ttu-id="226d6-540">nx_snmp_agent_privacy_key_use</span><span class="sxs-lookup"><span data-stu-id="226d6-540">nx_snmp_agent_privacy_key_use</span></span>
<span data-ttu-id="226d6-541">Especifique a chave de encriptação para mensagens de resposta</span><span class="sxs-lookup"><span data-stu-id="226d6-541">Specify encryption key for response messages</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-542">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-542">Prototype</span></span>

```c
UINT nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr, 
                                   NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a><span data-ttu-id="226d6-543">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-543">Description</span></span>

<span data-ttu-id="226d6-544">Este serviço especifica que a chave previamente criada deve ser usada para encriptação e desencriptação de mensagens de resposta SNMPv3.</span><span class="sxs-lookup"><span data-stu-id="226d6-544">This service specifies that the previously created key is to be used for encryption and decryption of SNMPv3 response messages.</span></span>

> [!NOTE]
> <span data-ttu-id="226d6-545">*Uma chave de autenticação deve ter sido previamente especificada. A encriptação V3 do SNMP requer a criação de uma chave de autenticação também. Consulte nx_snmp_agent_authentiation_key_use para mais detalhes.*</span><span class="sxs-lookup"><span data-stu-id="226d6-545">*An authentication key must have previously been specified. SNMP v3 encryption requires creation of an authentication key as well. See nx_snmp_agent_authentiation_key_use for details.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-546">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-546">Input Parameters</span></span>

- <span data-ttu-id="226d6-547">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-547">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-548">**chave** Ponteiro para criar previamente a chave.</span><span class="sxs-lookup"><span data-stu-id="226d6-548">**key** Pointer to previously create key.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-549">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-549">Return Values</span></span>

- <span data-ttu-id="226d6-550">**NX_SUCCESS** (0x00) Conjunto de chaves de privacidade bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="226d6-550">**NX_SUCCESS** (0x00) Successful privacy key set.</span></span>
- <span data-ttu-id="226d6-551">**NX_NOT_ENABLED** (0x14) Segurança não ativada.</span><span class="sxs-lookup"><span data-stu-id="226d6-551">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="226d6-552">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-552">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-553">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-553">Allowed From</span></span>

<span data-ttu-id="226d6-554">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-554">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-555">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-555">Example</span></span>

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_privacy_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_sha_key_create"></a><span data-ttu-id="226d6-556">nx_snmp_agent_sha_key_create</span><span class="sxs-lookup"><span data-stu-id="226d6-556">nx_snmp_agent_sha_key_create</span></span>
<span data-ttu-id="226d6-557">Criar tecla SHA (apenas SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="226d6-557">Create SHA key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-558">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-558">Prototype</span></span>

```c
UINT nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY  
                                  *destination_key);
```
### <a name="description"></a><span data-ttu-id="226d6-559">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-559">Description</span></span>

<span data-ttu-id="226d6-560">Este serviço cria uma chave SHA que pode ser usada para autenticação e encriptação.</span><span class="sxs-lookup"><span data-stu-id="226d6-560">This service creates a SHA key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="226d6-561">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="226d6-561">This service is deprecated.</span></span> <span data-ttu-id="226d6-562">Os desenvolvedores são encorajados a migrar para *nx_snmp_agent_sha_key_create_extended()*.</span><span class="sxs-lookup"><span data-stu-id="226d6-562">Developers are encouraged to migrate to *nx_snmp_agent_sha_key_create_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-563">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-563">Input Parameters</span></span>

- <span data-ttu-id="226d6-564">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-564">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-565">**senha** Ponteiro para a corda de senha.</span><span class="sxs-lookup"><span data-stu-id="226d6-565">**password** Pointer to password string.</span></span>
- <span data-ttu-id="226d6-566">**destination_key** Ponteiro para estrutura de dados chave SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-566">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-567">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-567">Return Values</span></span>

- <span data-ttu-id="226d6-568">**NX_SUCCESS** (0x00) Chave de sucesso criar.</span><span class="sxs-lookup"><span data-stu-id="226d6-568">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="226d6-569">**NX_SNMP_ERROR** (0x100) A chave cria erro.</span><span class="sxs-lookup"><span data-stu-id="226d6-569">**NX_SNMP_ERROR** (0x100) Key create error.</span></span>
- <span data-ttu-id="226d6-570">**NX_PTR_ERROR** (0x07) Agente SNMP inválido ou ponteiro chave.</span><span class="sxs-lookup"><span data-stu-id="226d6-570">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent or key pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-571">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-571">Allowed From</span></span>

<span data-ttu-id="226d6-572">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-572">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-573">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-573">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_sha_key_create_extended"></a><span data-ttu-id="226d6-574">nx_snmp_agent_sha_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="226d6-574">nx_snmp_agent_sha_key_create_extended</span></span>
<span data-ttu-id="226d6-575">Criar tecla SHA (apenas SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="226d6-575">Create SHA key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-576">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-576">Prototype</span></span>

```c
UINT nx_snmp_agent_sha_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY  
                                           *destination_key);
```
### <a name="description"></a><span data-ttu-id="226d6-577">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-577">Description</span></span>

<span data-ttu-id="226d6-578">Este serviço cria uma chave SHA que pode ser usada para autenticação e encriptação.</span><span class="sxs-lookup"><span data-stu-id="226d6-578">This service creates a SHA key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="226d6-579">Este serviço substitui *nx_snmp_agent_sha_key_create.*</span><span class="sxs-lookup"><span data-stu-id="226d6-579">This service replaces *nx_snmp_agent_sha_key_create().*</span></span> <span data-ttu-id="226d6-580">Esta versão requer que o chamador forneça o comprimento da palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="226d6-580">This version requires caller to supply password length.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-581">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-581">Input Parameters</span></span>

- <span data-ttu-id="226d6-582">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-582">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-583">**senha** Ponteiro para a corda de senha.</span><span class="sxs-lookup"><span data-stu-id="226d6-583">**password** Pointer to password string.</span></span>
- <span data-ttu-id="226d6-584">**password_length** Comprimento da corda da palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="226d6-584">**password_length** Length of password string.</span></span>
- <span data-ttu-id="226d6-585">**destination_key** Ponteiro para estrutura de dados chave SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-585">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-586">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-586">Return Values</span></span>

- <span data-ttu-id="226d6-587">**NX_SUCCESS** (0x00) Chave de sucesso criar.</span><span class="sxs-lookup"><span data-stu-id="226d6-587">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="226d6-588">**NX_SNMP_ERROR** (0x100) A chave cria erro.</span><span class="sxs-lookup"><span data-stu-id="226d6-588">**NX_SNMP_ERROR** (0x100) Key create error.</span></span>
- <span data-ttu-id="226d6-589">**NX_SNMP_FAILED** (0x102) A chave cria falhas.</span><span class="sxs-lookup"><span data-stu-id="226d6-589">**NX_SNMP_FAILED** (0x102) Key create failed.</span></span>
- <span data-ttu-id="226d6-590">**NX_PTR_ERROR** (0x07) Agente SNMP inválido ou ponteiro chave.</span><span class="sxs-lookup"><span data-stu-id="226d6-590">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent or key pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-591">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-591">Allowed From</span></span>

<span data-ttu-id="226d6-592">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-592">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-593">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-593">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_start"></a><span data-ttu-id="226d6-594">nx_snmp_agent_start</span><span class="sxs-lookup"><span data-stu-id="226d6-594">nx_snmp_agent_start</span></span>
<span data-ttu-id="226d6-595">Iniciar agente SNMP</span><span class="sxs-lookup"><span data-stu-id="226d6-595">Start SNMP agent</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-596">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-596">Prototype</span></span>

```c
UINT nx_snmp_agent_start(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a><span data-ttu-id="226d6-597">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-597">Description</span></span>

<span data-ttu-id="226d6-598">Este serviço liga a tomada UDP à porta SNMP 161 e inicia a tarefa de thread do Agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-598">This service binds the UDP socket to the SNMP port 161 and starts the SNMP Agent thread task.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-599">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-599">Input Parameters</span></span>

- <span data-ttu-id="226d6-600">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-600">**agent_ptr** Pointer to SNMP Agent control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-601">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-601">Return Values</span></span>

- <span data-ttu-id="226d6-602">**NX_SUCCESS** (0x00) Início bem sucedido do Agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-602">**NX_SUCCESS** (0x00) Successful start of SNMP Agent.</span></span>
- <span data-ttu-id="226d6-603">**NX_SNMP_ERROR** (0x100) Erro de arranque do Agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-603">**NX_SNMP_ERROR** (0x100) SNMP Agent start error.</span></span>
- <span data-ttu-id="226d6-604">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-604">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-605">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-605">Allowed From</span></span>

<span data-ttu-id="226d6-606">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-606">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-607">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-607">Example</span></span>

```c
/* Start the previously created SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_start(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been started.  */
```
## <a name="nx_snmp_agent_stop"></a><span data-ttu-id="226d6-608">nx_snmp_agent_stop</span><span class="sxs-lookup"><span data-stu-id="226d6-608">nx_snmp_agent_stop</span></span>
<span data-ttu-id="226d6-609">Parar o agente SNMP</span><span class="sxs-lookup"><span data-stu-id="226d6-609">Stop SNMP agent</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-610">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-610">Prototype</span></span>

```c
UINT nx_snmp_agent_stop(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a><span data-ttu-id="226d6-611">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-611">Description</span></span>

<span data-ttu-id="226d6-612">Este serviço para a tarefa de thread do Agente SNMP e desvinga a tomada UDP para a porta SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-612">This service stops the SNMP Agent thread task and unbinds the UDP socket to the SNMP port.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-613">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-613">Input Parameters</span></span>

- <span data-ttu-id="226d6-614">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-614">**agent_ptr** Pointer to SNMP Agent control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-615">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-615">Return Values</span></span>

- <span data-ttu-id="226d6-616">**NX_SUCCESS** (0x00) Paragem bem sucedida do Agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-616">**NX_SUCCESS** (0x00) Successful stop of SNMP Agent.</span></span>
- <span data-ttu-id="226d6-617">**NX_PTR_ERROR** (0x07) Ponteiro do Agente SNMP inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-617">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-618">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-618">Allowed From</span></span>

<span data-ttu-id="226d6-619">Fios</span><span class="sxs-lookup"><span data-stu-id="226d6-619">Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-620">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-620">Example</span></span>

```c
/* Stop the previously created and started SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_stop(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been stopped.  */
```
## <a name="nx_snmp_agent_trap_send"></a><span data-ttu-id="226d6-621">nx_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="226d6-621">nx_snmp_agent_trap_send</span></span>
<span data-ttu-id="226d6-622">Enviar armadilha SNMPv1 *(apenas IPv4)*</span><span class="sxs-lookup"><span data-stu-id="226d6-622">Send SNMPv1 trap *(IPv4 only)*</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-623">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-623">Prototype</span></span>

```c
UINT nx_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
                             ULONG ip_address, UCHAR *enterprise, 
                             UINT trap_type, UINT trap_code, 
                             ULONG elapsed_time, 
                             NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a><span data-ttu-id="226d6-624">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-624">Description</span></span>

<span data-ttu-id="226d6-625">Este serviço envia uma armadilha SNMP ao Gerente SNMP no endereço IPv4 especificado.</span><span class="sxs-lookup"><span data-stu-id="226d6-625">This service sends an SNMP trap to the SNMP Manager at the specified IPv4 address.</span></span> <span data-ttu-id="226d6-626">O método preferido para o envio de uma armadilha SNMP na NetX Duo é utilizar o serviço *nxd_snmp_agent_trap_send.*</span><span class="sxs-lookup"><span data-stu-id="226d6-626">The preferred method for sending an SNMP trap in NetX Duo is to use the *nxd_snmp_agent_trap_send* service.</span></span> <span data-ttu-id="226d6-627">*nx_snmp_agent_trap_send* está incluído no NetX Duo para suportar as aplicações existentes do Agente SNMP netX.</span><span class="sxs-lookup"><span data-stu-id="226d6-627">*nx_snmp_agent_trap_send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-628">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-628">Input Parameters</span></span>

- <span data-ttu-id="226d6-629">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-629">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-630">**ip_address** Endereço IPv4 do Gerente do SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-630">**ip_address** IPv4 address of the SNMP Manager.</span></span>
- <span data-ttu-id="226d6-631">**empresa** Cadeia de ID de objeto da empresa (sysObectID).</span><span class="sxs-lookup"><span data-stu-id="226d6-631">**enterprise** Enterprise object ID string (sysObectID).</span></span>
- <span data-ttu-id="226d6-632">**trap_type** Tipo de armadilha solicitada:</span><span class="sxs-lookup"><span data-stu-id="226d6-632">**trap_type** Type of trap requested, as follows:</span></span>  
   - <span data-ttu-id="226d6-633">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="226d6-633">NX_SNMP_TRAP_COLDSTART (0)</span></span>  
   - <span data-ttu-id="226d6-634">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="226d6-634">NX_SNMP_TRAP_WARMSTART (1)</span></span>  
   - <span data-ttu-id="226d6-635">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="226d6-635">NX_SNMP_TRAP_LINKDOWN (2)</span></span>  
   - <span data-ttu-id="226d6-636">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="226d6-636">NX_SNMP_TRAP_LINKUP (3)</span></span>  
   - <span data-ttu-id="226d6-637">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="226d6-637">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>  
   - <span data-ttu-id="226d6-638">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="226d6-638">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>  

- <span data-ttu-id="226d6-639">**trap_code** Código de armadilha específico.</span><span class="sxs-lookup"><span data-stu-id="226d6-639">**trap_code** Specific trap code.</span></span>
- <span data-ttu-id="226d6-640">**elapsed_time** O sistema de tempo foi para cima (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="226d6-640">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="226d6-641">**object_list_ptr** Matriz de objetos e seus valores associados a incluir na armadilha SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-641">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="226d6-642">A lista está NX_NULL terminada.</span><span class="sxs-lookup"><span data-stu-id="226d6-642">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-643">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-643">Return Values</span></span>

- <span data-ttu-id="226d6-644">**NX_SUCCESS** (0x00) Envio de armadilhas SNMP bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="226d6-644">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="226d6-645">**NX_SNMP_ERROR** (0x100) Erro de envio de armadilha SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-645">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="226d6-646">**NX_NOT_ENABLED** (0x14) SNMPv1 não está ativado.</span><span class="sxs-lookup"><span data-stu-id="226d6-646">**NX_NOT_ENABLED** (0x14) SNMPv1 not enabled.</span></span>
- <span data-ttu-id="226d6-647">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-647">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-648">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-648">Allowed From</span></span>

<span data-ttu-id="226d6-649">Fios</span><span class="sxs-lookup"><span data-stu-id="226d6-649">Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-650">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-650">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nx_snmp_agent_trap_send(&my_agent,dest_ip_address,
                                   "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, 
                                  tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trap_send"></a><span data-ttu-id="226d6-651">nxd_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="226d6-651">nxd_snmp_agent_trap_send</span></span>
<span data-ttu-id="226d6-652">Enviar armadilha SNMPv1 *(IPv4 e IPv6)*</span><span class="sxs-lookup"><span data-stu-id="226d6-652">Send SNMPv1 trap *(IPv4 and IPv6)*</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-653">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-653">Prototype</span></span>

```c
UINT nxd_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *enterprise, UINT trap_type, 
            UINT trap_code, ULONG elapsed_time, 
            NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="226d6-654">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-654">Description</span></span>

<span data-ttu-id="226d6-655">Este serviço envia uma armadilha SNMP ao Gestor SNMP no endereço IP especificado.</span><span class="sxs-lookup"><span data-stu-id="226d6-655">This service sends an SNMP trap to the SNMP Manager at the specified IP address.</span></span> <span data-ttu-id="226d6-656">O método equivalente para o envio de uma armadilha SNMP na NetX é o serviço *nxd_snmp_agent_trap_send.*</span><span class="sxs-lookup"><span data-stu-id="226d6-656">The equivalent method for sending an SNMP trap in NetX is the *nxd_snmp_agent_trap_send* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-657">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-657">Input Parameters</span></span>

- <span data-ttu-id="226d6-658">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-658">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-659">**ip_address** Endereço IPv4 ou IPv6 do Gestor do SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-659">**ip_address** IPv4 or IPv6 address of the SNMP Manager.</span></span>
- <span data-ttu-id="226d6-660">**empresa** Cadeia de ID de objeto da empresa (sysObectID).</span><span class="sxs-lookup"><span data-stu-id="226d6-660">**enterprise** Enterprise object ID string (sysObectID).</span></span>
- <span data-ttu-id="226d6-661">**trap_type** Tipo de armadilha solicitada:</span><span class="sxs-lookup"><span data-stu-id="226d6-661">**trap_type** Type of trap requested, as follows:</span></span>  
   - <span data-ttu-id="226d6-662">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="226d6-662">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="226d6-663">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="226d6-663">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="226d6-664">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="226d6-664">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="226d6-665">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="226d6-665">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="226d6-666">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="226d6-666">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="226d6-667">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="226d6-667">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

- <span data-ttu-id="226d6-668">**trap_code** Código de armadilha específico.</span><span class="sxs-lookup"><span data-stu-id="226d6-668">**trap_code** Specific trap code.</span></span>
- <span data-ttu-id="226d6-669">**elapsed_time** O sistema de tempo foi para cima (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="226d6-669">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="226d6-670">**object_list_ptr** Matriz de objetos e seus valores associados a incluir na armadilha SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-670">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="226d6-671">A lista está NX_NULL terminada.</span><span class="sxs-lookup"><span data-stu-id="226d6-671">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-672">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-672">Return Values</span></span>

- <span data-ttu-id="226d6-673">**NX_SUCCESS** (0x00) Envio de armadilhas SNMP bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="226d6-673">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="226d6-674">**NX_SNMP_ERROR** (0x100) Erro de envio de armadilha SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-674">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="226d6-675">**NX_NOT_ENABLED** (0x14) SNMPv1 não está ativado.</span><span class="sxs-lookup"><span data-stu-id="226d6-675">**NX_NOT_ENABLED** (0x14) SNMPv1 not enabled.</span></span>
- <span data-ttu-id="226d6-676">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-676">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-677">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-677">Allowed From</span></span>

<span data-ttu-id="226d6-678">Fios</span><span class="sxs-lookup"><span data-stu-id="226d6-678">Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-679">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-679">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nxd_snmp_agent_trap_send(&my_agent,&dest_ip_address,
                 "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, tx_time_get(), 
               trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_send"></a><span data-ttu-id="226d6-680">nx_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="226d6-680">nx_snmp_agent_trapv2_send</span></span>
<span data-ttu-id="226d6-681">Enviar armadilha SNMPv2 (apenas IPv4)</span><span class="sxs-lookup"><span data-stu-id="226d6-681">Send SNMPv2 trap (IPv4 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-682">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-682">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
            NXD_ADDRESS *ip_address, UCHAR *community, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="226d6-683">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-683">Description</span></span>

<span data-ttu-id="226d6-684">Este serviço envia uma armadilha SNMPv2 ao Gerente SNMP no endereço IPv4 especificado.</span><span class="sxs-lookup"><span data-stu-id="226d6-684">This service sends an SNMPv2 trap to the SNMP Manager at the specified IPv4 address.</span></span> <span data-ttu-id="226d6-685">O método preferido para o envio de uma armadilha SNMP na NetX Duo é utilizar o serviço *nxd_snmp_agent_trapv2_send.*</span><span class="sxs-lookup"><span data-stu-id="226d6-685">The preferred method for sending an SNMP trap in NetX Duo is to use the *nxd_snmp_agent_trapv2_send* service.</span></span> <span data-ttu-id="226d6-686">*nx_snmp_agent_trapv2_send* está incluído no NetX Duo para suportar as aplicações existentes do Agente SNMP netX.</span><span class="sxs-lookup"><span data-stu-id="226d6-686">*nx_snmp_agent_trapv2_send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-687">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-687">Input Parameters</span></span>

- <span data-ttu-id="226d6-688">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-688">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-689">**ip_address** Endereço IPv4 do Gerente do SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-689">**ip_address** IPv4 address of the SNMP Manager.</span></span>
- <span data-ttu-id="226d6-690">**comunidade** Nome comunitário (nome de utilizador).</span><span class="sxs-lookup"><span data-stu-id="226d6-690">**community** Community name (username).</span></span>
- <span data-ttu-id="226d6-691">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="226d6-691">**trap_type**</span></span>  
   <span data-ttu-id="226d6-692">Tipo de armadilha pedida.</span><span class="sxs-lookup"><span data-stu-id="226d6-692">Type of trap requested.</span></span> <span data-ttu-id="226d6-693">Os eventos padrão são:</span><span class="sxs-lookup"><span data-stu-id="226d6-693">The standard events are:</span></span>  
   - <span data-ttu-id="226d6-694">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="226d6-694">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="226d6-695">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="226d6-695">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="226d6-696">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="226d6-696">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="226d6-697">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="226d6-697">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="226d6-698">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="226d6-698">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="226d6-699">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="226d6-699">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

   <span data-ttu-id="226d6-700">Para dados proprietários:</span><span class="sxs-lookup"><span data-stu-id="226d6-700">For proprietary data:</span></span>  
   - <span data-ttu-id="226d6-701">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definido em *nxd_snmp.h)*</span><span class="sxs-lookup"><span data-stu-id="226d6-701">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>
   
- <span data-ttu-id="226d6-702">**elapsed_time** O sistema de tempo foi para cima (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="226d6-702">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="226d6-703">**object_list_ptr** Matriz de objetos e seus valores associados a incluir na armadilha SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-703">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="226d6-704">A lista está NX_NULL terminada.</span><span class="sxs-lookup"><span data-stu-id="226d6-704">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-705">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-705">Return Values</span></span>

- <span data-ttu-id="226d6-706">**NX_SUCCESS** (0x00) Envio de armadilhas SNMP bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="226d6-706">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="226d6-707">**NX_SNMP_ERROR** (0x100) Erro de envio de armadilha SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-707">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="226d6-708">**NX_NOT_ENABLED** (0x14) SNMPv2 não está ativado.</span><span class="sxs-lookup"><span data-stu-id="226d6-708">**NX_NOT_ENABLED** (0x14) SNMPv2 not enabled.</span></span>
- <span data-ttu-id="226d6-709">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-709">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-710">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-710">Allowed From</span></span>

<span data-ttu-id="226d6-711">Fios</span><span class="sxs-lookup"><span data-stu-id="226d6-711">Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-712">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-712">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG  dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_send(&my_agent,dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_oid_send"></a><span data-ttu-id="226d6-713">nx_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="226d6-713">nx_snmp_agent_trapv2_oid_send</span></span>
<span data-ttu-id="226d6-714">Enviar armadilha SNMPv2 especificando o OID diretamente</span><span class="sxs-lookup"><span data-stu-id="226d6-714">Send SNMPv2 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-715">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-715">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *community,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="226d6-716">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-716">Description</span></span>

<span data-ttu-id="226d6-717">Este serviço envia uma armadilha SNMPv2 para o Gestor SNMP no endereço IP especificado (apenas IPv4) e permite que o chamador especifique o OID diretamente.</span><span class="sxs-lookup"><span data-stu-id="226d6-717">This service sends an SNMPv2 trap to the SNMP Manager at the specified IP address (IPv4 only) and allows the caller to specify the OID directly.</span></span> <span data-ttu-id="226d6-718">O método preferido para o envio de uma armadilha SNMP com OID especificado na NetX Duo é utilizar o serviço *nxd_snmp_agent_trapv2_oid_send.*</span><span class="sxs-lookup"><span data-stu-id="226d6-718">The preferred method for sending an SNMP trap with specified OID in NetX Duo is to use the *nxd_snmp_agent_trapv2_oid_send* service.</span></span> <span data-ttu-id="226d6-719">*nx_snmp_agent_trapv2_oid_ envio* está incluído no NetX Duo para suportar as aplicações existentes do Agente SNMP netX.</span><span class="sxs-lookup"><span data-stu-id="226d6-719">*nx_snmp_agent_trapv2_oid_ send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-720">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-720">Input Parameters</span></span>

- <span data-ttu-id="226d6-721">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-721">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-722">**ip_address** Endereço IP do Gestor do SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-722">**ip_address** IP address of SNMP Manager.</span></span>
- <span data-ttu-id="226d6-723">**comunidade** Nome comunitário (nome de utilizador).</span><span class="sxs-lookup"><span data-stu-id="226d6-723">**community** Community name (username).</span></span>
- <span data-ttu-id="226d6-724">**oid** Ponteiro para tampão contendo OID.</span><span class="sxs-lookup"><span data-stu-id="226d6-724">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="226d6-725">**elapsed_time** O sistema de tempo foi para cima (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="226d6-725">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="226d6-726">**object_list_ptr** Matriz de objetos e seus valores associados a incluir na armadilha SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-726">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="226d6-727">A lista está NX_NULL terminada.</span><span class="sxs-lookup"><span data-stu-id="226d6-727">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-728">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-728">Return Values</span></span>

- <span data-ttu-id="226d6-729">**NX_SUCCESS** (0x00) Envio de armadilhas SNMP bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="226d6-729">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="226d6-730">**NX_SNMP_ERROR** (0x100) Erro de envio de armadilha SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-730">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="226d6-731">**NX_PTR_ERROR** (0x16) Agente SNMP inválido ou ponteiro de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="226d6-731">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="226d6-732">**NX_IP_ADDRESS_ERROR** (0x21) Endereço IP de destino inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-732">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>
- <span data-ttu-id="226d6-733">**NX_OPTION_ERROR** (0x0a) Parâmetro inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-733">**NX_OPTION_ERROR** (0x0a) Invalid parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-734">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-734">Allowed From</span></span>

<span data-ttu-id="226d6-735">Fios</span><span class="sxs-lookup"><span data-stu-id="226d6-735">Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-736">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-736">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_send"></a><span data-ttu-id="226d6-737">nxd_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="226d6-737">nxd_snmp_agent_trapv2_send</span></span>
<span data-ttu-id="226d6-738">Enviar armadilha SNMPv2 (IPv4 e IPv6)</span><span class="sxs-lookup"><span data-stu-id="226d6-738">Send SNMPv2 trap (IPv4 and IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-739">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-739">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *community, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="226d6-740">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-740">Description</span></span>

<span data-ttu-id="226d6-741">Este serviço envia uma armadilha SNMP V2 para o Gestor SNMP no endereço IP especificado.</span><span class="sxs-lookup"><span data-stu-id="226d6-741">This service sends an SNMP V2 trap to the SNMP Manager at the specified IP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-742">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-742">Input Parameters</span></span>

- <span data-ttu-id="226d6-743">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-743">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-744">**ip_address** Endereço IP (IPv4 ou IPv6) do Gestor do SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-744">**ip_address** IP (IPv4 or IPv6) address of the SNMP Manager.</span></span>
- <span data-ttu-id="226d6-745">**comunidade** Nome comunitário (nome de utilizador).</span><span class="sxs-lookup"><span data-stu-id="226d6-745">**community** Community name (username).</span></span>
- <span data-ttu-id="226d6-746">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="226d6-746">**trap_type**</span></span>  
   <span data-ttu-id="226d6-747">Tipo de armadilha pedida.</span><span class="sxs-lookup"><span data-stu-id="226d6-747">Type of trap requested.</span></span> <span data-ttu-id="226d6-748">Os eventos padrão são:</span><span class="sxs-lookup"><span data-stu-id="226d6-748">The standard events are:</span></span>  
   - <span data-ttu-id="226d6-749">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="226d6-749">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="226d6-750">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="226d6-750">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="226d6-751">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="226d6-751">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="226d6-752">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="226d6-752">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="226d6-753">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="226d6-753">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="226d6-754">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="226d6-754">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

   <span data-ttu-id="226d6-755">Para dados proprietários:</span><span class="sxs-lookup"><span data-stu-id="226d6-755">For proprietary data:</span></span>

   - <span data-ttu-id="226d6-756">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definido em *nxd_snmp.h)*</span><span class="sxs-lookup"><span data-stu-id="226d6-756">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>

- <span data-ttu-id="226d6-757">**elapsed_time** O sistema de tempo foi para cima (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="226d6-757">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="226d6-758">**object_list_ptr** Matriz de objetos e seus valores associados a incluir na armadilha SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-758">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="226d6-759">A lista está NX_NULL terminada.</span><span class="sxs-lookup"><span data-stu-id="226d6-759">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-760">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-760">Return Values</span></span>

- <span data-ttu-id="226d6-761">**NX_SUCCESS** (0x00) Envio de armadilhas SNMP bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="226d6-761">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="226d6-762">**NX_SNMP_ERROR** (0x100) Erro de envio de armadilha SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-762">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="226d6-763">**NX_NOT_ENABLED** (0x14) SNMPv2 não está ativado.</span><span class="sxs-lookup"><span data-stu-id="226d6-763">**NX_NOT_ENABLED** (0x14) SNMPv2 not enabled.</span></span>
- <span data-ttu-id="226d6-764">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Versão IP não suportada</span><span class="sxs-lookup"><span data-stu-id="226d6-764">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Unsupported IP version</span></span>
- <span data-ttu-id="226d6-765">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-765">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-766">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-766">Allowed From</span></span>

<span data-ttu-id="226d6-767">Fios</span><span class="sxs-lookup"><span data-stu-id="226d6-767">Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-768">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-768">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send a standard event trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_send(&my_agent,&dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_oid_send"></a><span data-ttu-id="226d6-769">nxd_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="226d6-769">nxd_snmp_agent_trapv2_oid_send</span></span>
<span data-ttu-id="226d6-770">Enviar armadilha SNMPv2 especificando o OID diretamente</span><span class="sxs-lookup"><span data-stu-id="226d6-770">Send SNMPv2 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-771">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-771">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *community,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                    *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="226d6-772">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-772">Description</span></span>

<span data-ttu-id="226d6-773">Este serviço envia uma armadilha de V2 SNMP para o Gestor SNMP no endereço IP especificado (IPv4/IPv6) e permite que o chamador especifique o OID diretamente.</span><span class="sxs-lookup"><span data-stu-id="226d6-773">This service sends an SNMP v2 trap to the SNMP Manager at the specified IP address (IPv4/IPv6) and allows the caller to specify the OID directly.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-774">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-774">Input Parameters</span></span>

- <span data-ttu-id="226d6-775">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-775">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-776">**ip_address** Endereço IP do Gestor do SNMP (IPv4/IPv6).</span><span class="sxs-lookup"><span data-stu-id="226d6-776">**ip_address** IP address of SNMP Manager (IPv4/IPv6).</span></span>
- <span data-ttu-id="226d6-777">**comunidade** Nome comunitário (nome de utilizador).</span><span class="sxs-lookup"><span data-stu-id="226d6-777">**community** Community name (username).</span></span>
- <span data-ttu-id="226d6-778">**oid** Ponteiro para tampão contendo OID.</span><span class="sxs-lookup"><span data-stu-id="226d6-778">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="226d6-779">**elapsed_time** O sistema de tempo foi para cima (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="226d6-779">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="226d6-780">**object_list_ptr** Matriz de objetos e seus valores associados a incluir na armadilha SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-780">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="226d6-781">A lista está NX_NULL terminada.</span><span class="sxs-lookup"><span data-stu-id="226d6-781">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-782">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-782">Return Values</span></span>

- <span data-ttu-id="226d6-783">**NX_SUCCESS** (0x00) Envio de armadilhas SNMP bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="226d6-783">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="226d6-784">**NX_SNMP_ERROR** (0x100) Erro de envio de armadilha SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-784">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="226d6-785">**NX_PTR_ERROR** (0x16) Agente SNMP inválido ou ponteiro de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="226d6-785">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="226d6-786">**NX_IP_ADDRESS_ERROR** (0x21) Endereço IP de destino inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-786">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>
- <span data-ttu-id="226d6-787">**NX_OPTION_ERROR** (0x0a) Parâmetro inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-787">**NX_OPTION_ERROR** (0x0a) Invalid parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-788">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-788">Allowed From</span></span>

<span data-ttu-id="226d6-789">Fios</span><span class="sxs-lookup"><span data-stu-id="226d6-789">Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-790">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-790">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS         address;


/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

address.nxd_ip_version = NX_IP_VERSION_V4;
address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61)

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_oid_send(&my_agent, &address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_trapv3_send"></a><span data-ttu-id="226d6-791">nx_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="226d6-791">nx_snmp_agent_trapv3_send</span></span>
<span data-ttu-id="226d6-792">Enviar armadilha SNMPv3 (apenas IPv4)</span><span class="sxs-lookup"><span data-stu-id="226d6-792">Send SNMPv3 trap (IPv4 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-793">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-793">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *username, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a><span data-ttu-id="226d6-794">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-794">Description</span></span>

<span data-ttu-id="226d6-795">Este serviço envia uma armadilha SNMPv3 para o Gerente SNMP no endereço IPv4 especificado.</span><span class="sxs-lookup"><span data-stu-id="226d6-795">This service sends an SNMPv3 trap to the SNMP Manager at the specified IPv4 address.</span></span> <span data-ttu-id="226d6-796">O método preferido para o envio de uma armadilha SNMP na NetX Duo é utilizar o serviço *nxd_snmp_agent_trapv3_send.*</span><span class="sxs-lookup"><span data-stu-id="226d6-796">The preferred method for sending an SNMP trap in NetX Duo is to use the *nxd_snmp_agent_trapv3_send* service.</span></span> <span data-ttu-id="226d6-797">*nx_snmp_agent_trapv3_send* está incluído no NetX Duo para suportar as aplicações existentes do Agente SNMP netX.</span><span class="sxs-lookup"><span data-stu-id="226d6-797">*nx_snmp_agent_trapv3_send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-798">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-798">Input Parameters</span></span>

- <span data-ttu-id="226d6-799">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-799">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-800">**ip_address** Endereço IPv4 do Gerente do SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-800">**ip_address** IPv4 address of the SNMP Manager.</span></span>
- <span data-ttu-id="226d6-801">**nome de utilizador** Nome comunitário (nome de utilizador).</span><span class="sxs-lookup"><span data-stu-id="226d6-801">**username** Community name (username).</span></span>
- <span data-ttu-id="226d6-802">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="226d6-802">**trap_type**</span></span>  
   <span data-ttu-id="226d6-803">Tipo de armadilha pedida.</span><span class="sxs-lookup"><span data-stu-id="226d6-803">Type of trap requested.</span></span> <span data-ttu-id="226d6-804">Os eventos padrão são:</span><span class="sxs-lookup"><span data-stu-id="226d6-804">The standard events are:</span></span>  
   - <span data-ttu-id="226d6-805">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="226d6-805">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="226d6-806">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="226d6-806">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="226d6-807">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="226d6-807">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="226d6-808">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="226d6-808">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="226d6-809">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="226d6-809">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="226d6-810">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="226d6-810">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

   <span data-ttu-id="226d6-811">Para dados proprietários:</span><span class="sxs-lookup"><span data-stu-id="226d6-811">For proprietary data:</span></span>
   - <span data-ttu-id="226d6-812">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definido em *nxd_snmp.h)*</span><span class="sxs-lookup"><span data-stu-id="226d6-812">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>

- <span data-ttu-id="226d6-813">**elapsed_time** O sistema de tempo foi para cima (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="226d6-813">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="226d6-814">**object_list_ptr** Matriz de objetos e seus valores associados a incluir na armadilha SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-814">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="226d6-815">A lista está NX_NULL terminada.</span><span class="sxs-lookup"><span data-stu-id="226d6-815">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-816">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-816">Return Values</span></span>

- <span data-ttu-id="226d6-817">**NX_SUCCESS** (0x00) Envio de armadilhas SNMP bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="226d6-817">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="226d6-818">**NX_SNMP_ERROR** (0x100) Erro de envio de armadilha SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-818">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="226d6-819">**NX_NOT_ENABLED** (0x14) SNMPv3 não está ativado.</span><span class="sxs-lookup"><span data-stu-id="226d6-819">**NX_NOT_ENABLED** (0x14) SNMPv3 not enabled.</span></span>
- <span data-ttu-id="226d6-820">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-820">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-821">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-821">Allowed From</span></span>

<span data-ttu-id="226d6-822">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-822">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-823">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-823">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_send(&my_agent, dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv3_oid_send"></a><span data-ttu-id="226d6-824">nx_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="226d6-824">nx_snmp_agent_trapv3_oid_send</span></span>
<span data-ttu-id="226d6-825">Enviar armadilha SNMPv3 especificando o OID diretamente</span><span class="sxs-lookup"><span data-stu-id="226d6-825">Send SNMPv3 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-826">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-826">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *username,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                   *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="226d6-827">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-827">Description</span></span>

<span data-ttu-id="226d6-828">Este serviço envia uma armadilha SNMPv3 para o Gestor SNMP no endereço IP especificado (apenas IPv4) e permite que o chamador especifique o OID diretamente.</span><span class="sxs-lookup"><span data-stu-id="226d6-828">This service sends an SNMPv3 trap to the SNMP Manager at the specified IP address (IPv4 only) and allows the caller to specify the OID directly.</span></span> <span data-ttu-id="226d6-829">O método preferido para o envio de uma armadilha SNMP com OID especificado na NetX Duo é utilizar o serviço *nxd_snmp_agent_trapv3_oid_send.*</span><span class="sxs-lookup"><span data-stu-id="226d6-829">The preferred method for sending an SNMP trap with specified OID in NetX Duo is to use the *nxd_snmp_agent_trapv3_oid_send* service.</span></span> <span data-ttu-id="226d6-830">*nx_snmp_agent_trapv3_oid_ envio* está incluído no NetX Duo para suportar as aplicações existentes do Agente SNMP netX.</span><span class="sxs-lookup"><span data-stu-id="226d6-830">*nx_snmp_agent_trapv3_oid_ send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-831">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-831">Input Parameters</span></span>

- <span data-ttu-id="226d6-832">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-832">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-833">**ip_address** Endereço IP do Gestor do SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-833">**ip_address** IP address of SNMP Manager.</span></span>
- <span data-ttu-id="226d6-834">**nome de utilizador** Nome comunitário (nome de utilizador).</span><span class="sxs-lookup"><span data-stu-id="226d6-834">**username** Community name (username).</span></span>
- <span data-ttu-id="226d6-835">**oid** Ponteiro para tampão contendo OID.</span><span class="sxs-lookup"><span data-stu-id="226d6-835">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="226d6-836">**elapsed_time** O sistema de tempo foi para cima (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="226d6-836">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="226d6-837">**object_list_ptr** Matriz de objetos e seus valores associados a incluir na armadilha SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-837">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="226d6-838">A lista está NX_NULL terminada.</span><span class="sxs-lookup"><span data-stu-id="226d6-838">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-839">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-839">Return Values</span></span>

- <span data-ttu-id="226d6-840">**NX_SUCCESS** (0x00) Envio de armadilhas SNMP bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="226d6-840">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="226d6-841">**NX_SNMP_ERROR** (0x100) Erro de envio de armadilha SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-841">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="226d6-842">**NX_PTR_ERROR** (0x16) Agente SNMP inválido ou ponteiro de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="226d6-842">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="226d6-843">**NX_IP_ADDRESS_ERROR** (0x21) Endereço IP de destino inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-843">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>
- <span data-ttu-id="226d6-844">**NX_OPTION_ERROR** (0x0a) Parâmetro inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-844">**NX_OPTION_ERROR** (0x0a) Invalid parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-845">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-845">Allowed From</span></span>

<span data-ttu-id="226d6-846">Fios</span><span class="sxs-lookup"><span data-stu-id="226d6-846">Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-847">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-847">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trapv3_send"></a><span data-ttu-id="226d6-848">nxd_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="226d6-848">nxd_snmp_agent_trapv3_send</span></span>
<span data-ttu-id="226d6-849">Enviar armadilha SNMPv3 (IPv4 e IPv6)</span><span class="sxs-lookup"><span data-stu-id="226d6-849">Send SNMPv3 trap (IPv4 and IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-850">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-850">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *username, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="226d6-851">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-851">Description</span></span>

<span data-ttu-id="226d6-852">Este serviço envia uma armadilha SNMP ao Gestor SNMP no endereço IP especificado.</span><span class="sxs-lookup"><span data-stu-id="226d6-852">This service sends an SNMP trap to the SNMP Manager at the specified IP address.</span></span> <span data-ttu-id="226d6-853">Esta armadilha é basicamente a mesma que a armadilha V2 do SNMP, exceto que o formato de mensagem de armadilha está contido no PDU SNMP v3.</span><span class="sxs-lookup"><span data-stu-id="226d6-853">This trap is basically the same as the SNMP v2 trap, except the trap message format is contained in the SNMP v3 PDU.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-854">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-854">Input Parameters</span></span>

- <span data-ttu-id="226d6-855">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-855">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-856">**ip_address** Endereço IP (IPv4 ou IPv6) do Gestor do SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-856">**ip_address** IP (IPv4 or IPv6) address of the SNMP Manager.</span></span>
- <span data-ttu-id="226d6-857">**nome de utilizador** Nome comunitário (nome de utilizador).</span><span class="sxs-lookup"><span data-stu-id="226d6-857">**username** Community name (username).</span></span>
- <span data-ttu-id="226d6-858">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="226d6-858">**trap_type**</span></span>  
   <span data-ttu-id="226d6-859">Tipo de armadilha pedida.</span><span class="sxs-lookup"><span data-stu-id="226d6-859">Type of trap requested.</span></span> <span data-ttu-id="226d6-860">Os eventos padrão são:</span><span class="sxs-lookup"><span data-stu-id="226d6-860">The standard events are:</span></span>
   - <span data-ttu-id="226d6-861">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="226d6-861">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="226d6-862">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="226d6-862">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="226d6-863">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="226d6-863">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="226d6-864">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="226d6-864">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="226d6-865">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="226d6-865">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="226d6-866">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="226d6-866">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>  
   <span data-ttu-id="226d6-867">Para dados proprietários:</span><span class="sxs-lookup"><span data-stu-id="226d6-867">For proprietary data:</span></span>
   - <span data-ttu-id="226d6-868">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definido em *nxd_snmp.h)*</span><span class="sxs-lookup"><span data-stu-id="226d6-868">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>

- <span data-ttu-id="226d6-869">**elapsed_time** O sistema de tempo foi para cima (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="226d6-869">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="226d6-870">**object_list_ptr** Matriz de objetos e seus valores associados a incluir na armadilha SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-870">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="226d6-871">A lista está NX_NULL terminada.</span><span class="sxs-lookup"><span data-stu-id="226d6-871">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-872">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-872">Return Values</span></span>

- <span data-ttu-id="226d6-873">**NX_SUCCESS** (0x00) Envio de armadilhas SNMP bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="226d6-873">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="226d6-874">**NX_SNMP_ERROR** (0x100) Erro de envio de armadilha SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-874">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="226d6-875">**NX_NOT_ENABLED** (0x14) SNMPv3 não está ativado.</span><span class="sxs-lookup"><span data-stu-id="226d6-875">**NX_NOT_ENABLED** (0x14) SNMPv3 not enabled.</span></span>
- <span data-ttu-id="226d6-876">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Versão IP não suportada</span><span class="sxs-lookup"><span data-stu-id="226d6-876">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Unsupported IP version</span></span>
- <span data-ttu-id="226d6-877">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-877">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-878">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-878">Allowed From</span></span>

<span data-ttu-id="226d6-879">Fios</span><span class="sxs-lookup"><span data-stu-id="226d6-879">Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-880">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-880">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_send(&my_agent, &dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv3_oid_send"></a><span data-ttu-id="226d6-881">nxd_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="226d6-881">nxd_snmp_agent_trapv3_oid_send</span></span>
<span data-ttu-id="226d6-882">Enviar armadilha SNMPv3 especificando o OID diretamente</span><span class="sxs-lookup"><span data-stu-id="226d6-882">Send SNMPv3 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-883">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-883">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *username,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="226d6-884">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-884">Description</span></span>

<span data-ttu-id="226d6-885">Este serviço envia uma armadilha SNMPv3 para o Gestor SNMP no endereço IP especificado (IPv4/IPv6) e permite que o chamador especifique o OID diretamente.</span><span class="sxs-lookup"><span data-stu-id="226d6-885">This service sends an SNMPv3 trap to the SNMP Manager at the specified IP address (IPv4/IPv6) and allows the caller to specify the OID directly.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-886">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-886">Input Parameters</span></span>

- <span data-ttu-id="226d6-887">**agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-887">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="226d6-888">**ip_address** Ponteiro para endereço IP do Gerente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-888">**ip_address** Pointer to IP address of SNMP Manager.</span></span>
- <span data-ttu-id="226d6-889">**nome de utilizador** Nome de utilizador (nome comunitário).</span><span class="sxs-lookup"><span data-stu-id="226d6-889">**username** Username (community name).</span></span>
- <span data-ttu-id="226d6-890">**oid** Ponteiro para tampão contendo OID.</span><span class="sxs-lookup"><span data-stu-id="226d6-890">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="226d6-891">**elapsed_time** O sistema de tempo foi para cima (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="226d6-891">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="226d6-892">**object_list_ptr** Matriz de objetos e seus valores associados a incluir na armadilha SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-892">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="226d6-893">A lista está NX_NULL terminada.</span><span class="sxs-lookup"><span data-stu-id="226d6-893">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-894">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-894">Return Values</span></span>

- <span data-ttu-id="226d6-895">**NX_SUCCESS** (0x00) Envio de armadilhas SNMP bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="226d6-895">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="226d6-896">**NX_SNMP_ERROR** (0x100) Erro de envio de armadilha SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-896">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="226d6-897">**NX_PTR_ERROR** (0x16) Agente SNMP inválido ou ponteiro de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="226d6-897">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="226d6-898">**NX_IP_ADDRESS_ERROR** (0x21) Endereço IP de destino inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-898">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-899">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-899">Allowed From</span></span>

<span data-ttu-id="226d6-900">Fios</span><span class="sxs-lookup"><span data-stu-id="226d6-900">Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-901">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-901">Example</span></span>

```c
NXD_ADDRESS         ip_address;
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

ip_address.nxd_ip_version = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61);

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_oid_send(&my_agent, &ip_address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_v3_context_boots_set"></a><span data-ttu-id="226d6-902">nx_snmp_agent_v3_context_boots_set</span><span class="sxs-lookup"><span data-stu-id="226d6-902">nx_snmp_agent_v3_context_boots_set</span></span>
<span data-ttu-id="226d6-903">Definir o número de reinicializações (se o SNMPv3 estiver ativado)</span><span class="sxs-lookup"><span data-stu-id="226d6-903">Set the number of reboots (if SNMPv3 enabled)</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-904">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-904">Prototype</span></span>

```c
UINT nx_snmp_agent_v3_context_boots_set(NX_SNMP_AGENT *agent_ptr, 
                                        UINT boots);
```

### <a name="description"></a><span data-ttu-id="226d6-905">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-905">Description</span></span>

<span data-ttu-id="226d6-906">Este serviço define o número de reinicializações registadas pelo agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="226d6-906">This service sets the number of reboots recorded by the SNMP agent.</span></span> <span data-ttu-id="226d6-907">Este serviço só está disponível se o SNMPv3 estiver habilitado para o agente SNMP, uma vez que a contagem de botas só é utilizada no protocolo SNMPv3.</span><span class="sxs-lookup"><span data-stu-id="226d6-907">This service is only available if SNMPv3 is enabled for the SNMP agent because boot count is only used in the SNMPv3 protocol.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-908">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-908">Input Parameters</span></span>

- <span data-ttu-id="226d6-909">**agent_ptr** Ponteiro para bloco de controlo do agente SNMP</span><span class="sxs-lookup"><span data-stu-id="226d6-909">**agent_ptr** Pointer to SNMP Agent control block</span></span>
- <span data-ttu-id="226d6-910">**botas** O valor para definir a contagem de botas do Agente SNMP para</span><span class="sxs-lookup"><span data-stu-id="226d6-910">**boots** The value to set SNMP Agent boot count to</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-911">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-911">Return Values</span></span>

- <span data-ttu-id="226d6-912">**NX_SUCCESS** (0x00) definir com sucesso a contagem de botas</span><span class="sxs-lookup"><span data-stu-id="226d6-912">**NX_SUCCESS** (0x00) Successfully set boot count</span></span>
- <span data-ttu-id="226d6-913">**NX_SNMP_ERROR** (0x100) Contagem de botas de definição de erro</span><span class="sxs-lookup"><span data-stu-id="226d6-913">**NX_SNMP_ERROR** (0x100) Error setting boot count</span></span>
- <span data-ttu-id="226d6-914">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="226d6-914">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-915">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-915">Allowed From</span></span>

<span data-ttu-id="226d6-916">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-916">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-917">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-917">Example</span></span>

```c
UINT my_boots = 4;

if (my_agent.nx_snmp_agent_v3_enabled == NX_TRUE)
{
   status = nx_snmp_agent_v3_context_boots_set(&my_agent, my_boots);
}


/* If status is NX_SUCCESS the SNMP boot count is set.  */
```

## <a name="nx_snmp_object_compare"></a><span data-ttu-id="226d6-918">nx_snmp_object_compare</span><span class="sxs-lookup"><span data-stu-id="226d6-918">nx_snmp_object_compare</span></span>
<span data-ttu-id="226d6-919">Comparar dois objetos</span><span class="sxs-lookup"><span data-stu-id="226d6-919">Compare two objects</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-920">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-920">Prototype</span></span>

```c
UINT nx_snmp_object_compare(UCHAR *object, UCHAR *reference_object);
```

### <a name="description"></a><span data-ttu-id="226d6-921">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-921">Description</span></span>

<span data-ttu-id="226d6-922">Este serviço compara o ID do objeto fornecido com o ID do objeto de referência.</span><span class="sxs-lookup"><span data-stu-id="226d6-922">This service compares the supplied object ID with the reference object ID.</span></span> <span data-ttu-id="226d6-923">Ambos os IDs de objeto estão na notação ASCII SMI, por exemplo, ambos os objetos devem começar com a cadeia ASCII "1.3.6".</span><span class="sxs-lookup"><span data-stu-id="226d6-923">Both object IDs are in the ASCII SMI notation, e.g., both object must start with the ASCII string “1.3.6”.</span></span>

<span data-ttu-id="226d6-924">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="226d6-924">This service is deprecated.</span></span> <span data-ttu-id="226d6-925">Os desenvolvedores são encorajados a migrar para *nx_snmp_object_compare_extended().*</span><span class="sxs-lookup"><span data-stu-id="226d6-925">Developers are encouraged to migrate to *nx_snmp_object_compare_extended().*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-926">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-926">Input Parameters</span></span>

- <span data-ttu-id="226d6-927">**objeto** Ponteiro para opor identificação.</span><span class="sxs-lookup"><span data-stu-id="226d6-927">**object** Pointer to object ID.</span></span>
- <span data-ttu-id="226d6-928">**reference_object** Ponteiro para o ID do objeto de referência.</span><span class="sxs-lookup"><span data-stu-id="226d6-928">**reference_object** Pointer to the reference object ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-929">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-929">Return Values</span></span>

- <span data-ttu-id="226d6-930">**NX_SUCCESS** (0x00) O objeto corresponde ao objeto de referência.</span><span class="sxs-lookup"><span data-stu-id="226d6-930">**NX_SUCCESS** (0x00) The object matches the reference object.</span></span>
- <span data-ttu-id="226d6-931">**NX_SNMP_NEXT_ENTRY** (0x101) O objeto é inferior ao objeto de referência.</span><span class="sxs-lookup"><span data-stu-id="226d6-931">**NX_SNMP_NEXT_ENTRY** (0x101) The object is less than the reference object.</span></span>
- <span data-ttu-id="226d6-932">**NX_SNMP_ERROR** (0x100) O objeto é maior do que o objeto de referência.</span><span class="sxs-lookup"><span data-stu-id="226d6-932">**NX_SNMP_ERROR** (0x100) The object is greater than the reference object.</span></span>
- <span data-ttu-id="226d6-933">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-933">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-934">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-934">Allowed From</span></span>

<span data-ttu-id="226d6-935">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-935">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-936">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-936">Example</span></span>

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare(requested_object, "1.3.6.1.2.1.1.1.0");

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_compare_extended"></a><span data-ttu-id="226d6-937">nx_snmp_object_compare_extended</span><span class="sxs-lookup"><span data-stu-id="226d6-937">nx_snmp_object_compare_extended</span></span>
<span data-ttu-id="226d6-938">Comparar dois objetos</span><span class="sxs-lookup"><span data-stu-id="226d6-938">Compare two objects</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-939">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-939">Prototype</span></span>

```c
UINT nx_snmp_object_compare_extended(UCHAR *request_object, 
                                     UINT requested_object_length,
                                     UCHAR *reference_object
                                     UINT reference_object_length);
```
### <a name="description"></a><span data-ttu-id="226d6-940">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-940">Description</span></span>

<span data-ttu-id="226d6-941">Este serviço compara o ID do objeto fornecido com o ID do objeto de referência.</span><span class="sxs-lookup"><span data-stu-id="226d6-941">This service compares the supplied object ID with the reference object ID.</span></span> <span data-ttu-id="226d6-942">Ambos os IDs de objeto estão na notação ASCII SMI, por exemplo, ambos os objetos devem começar com a cadeia ASCII "1.3.6".</span><span class="sxs-lookup"><span data-stu-id="226d6-942">Both object IDs are in the ASCII SMI notation, e.g., both object must start with the ASCII string “1.3.6”.</span></span>

<span data-ttu-id="226d6-943">Este serviço substitui *nx_snmp_object_compare.*</span><span class="sxs-lookup"><span data-stu-id="226d6-943">This service replaces *nx_snmp_object_compare().*</span></span> <span data-ttu-id="226d6-944">Esta versão requer que os chamadores forneçam informações de comprimento.</span><span class="sxs-lookup"><span data-stu-id="226d6-944">This version requires callers to supply length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-945">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-945">Input Parameters</span></span>

- <span data-ttu-id="226d6-946">**request_object** Ponteiro para solicitar identificação do objeto.</span><span class="sxs-lookup"><span data-stu-id="226d6-946">**request_object** Pointer to request object ID.</span></span>
- <span data-ttu-id="226d6-947">**request_object_length** Comprimento da identificação do objeto de pedido.</span><span class="sxs-lookup"><span data-stu-id="226d6-947">**request_object_length** Length of the request object ID.</span></span>
- <span data-ttu-id="226d6-948">**reference_object** Ponteiro para o ID do objeto de referência.</span><span class="sxs-lookup"><span data-stu-id="226d6-948">**reference_object** Pointer to the reference object ID.</span></span>
- <span data-ttu-id="226d6-949">**reference_object_length** Comprimento do ID do objeto de referência.</span><span class="sxs-lookup"><span data-stu-id="226d6-949">**reference_object_length** Length of the reference object ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-950">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-950">Return Values</span></span>

- <span data-ttu-id="226d6-951">**NX_SUCCESS** (0x00) O objeto corresponde ao objeto de referência.</span><span class="sxs-lookup"><span data-stu-id="226d6-951">**NX_SUCCESS** (0x00) The object matches the reference object.</span></span>
- <span data-ttu-id="226d6-952">**NX_SNMP_NEXT_ENTRY** (0x101) O objeto é inferior ao objeto de referência.</span><span class="sxs-lookup"><span data-stu-id="226d6-952">**NX_SNMP_NEXT_ENTRY** (0x101) The object is less than the reference object.</span></span>
- <span data-ttu-id="226d6-953">**NX_SNMP_ERROR** (0x100) O objeto é maior do que o objeto de referência.</span><span class="sxs-lookup"><span data-stu-id="226d6-953">**NX_SNMP_ERROR** (0x100) The object is greater than the reference object.</span></span>
- <span data-ttu-id="226d6-954">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-954">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-955">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-955">Allowed From</span></span>

<span data-ttu-id="226d6-956">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-956">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-957">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-957">Example</span></span>

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare_extended(requested_object, 17,
                                          "1.3.6.1.2.1.1.1.0", 17);

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_copy"></a><span data-ttu-id="226d6-958">nx_snmp_object_copy</span><span class="sxs-lookup"><span data-stu-id="226d6-958">nx_snmp_object_copy</span></span>
<span data-ttu-id="226d6-959">Copiar um objeto</span><span class="sxs-lookup"><span data-stu-id="226d6-959">Copy an object</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-960">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-960">Prototype</span></span>

```c
UINT  nx_snmp_object_copy(UCHAR *source_object_name, 
                          UCHAR *destination_object_name);
```
### <a name="description"></a><span data-ttu-id="226d6-961">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-961">Description</span></span>

<span data-ttu-id="226d6-962">Este serviço copia o objeto de origem na notação ASCII SIM para o objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="226d6-962">This service copies the source object in ASCII SIM notation to the destination object.</span></span>

<span data-ttu-id="226d6-963">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="226d6-963">This service is deprecated.</span></span> <span data-ttu-id="226d6-964">Os desenvolvedores são encorajados a migrar para *nx_snmp_object_copy_extended().*</span><span class="sxs-lookup"><span data-stu-id="226d6-964">Developers are encouraged to migrate to *nx_snmp_object_copy_extended().*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-965">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-965">Input Parameters</span></span>

- <span data-ttu-id="226d6-966">**source_object_name** Ponteiro para identificação do objeto de origem.</span><span class="sxs-lookup"><span data-stu-id="226d6-966">**source_object_name** Pointer to source object ID.</span></span>
- <span data-ttu-id="226d6-967">**destination_object_name** Ponteiro para o endereço de destino objeto ID.</span><span class="sxs-lookup"><span data-stu-id="226d6-967">**destination_object_name** Pointer to destination object ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-968">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-968">Return Values</span></span>

- <span data-ttu-id="226d6-969">**tamanho** Número de bytes copiados para o nome de destino.</span><span class="sxs-lookup"><span data-stu-id="226d6-969">**size** Number of bytes copied to destination name.</span></span> <span data-ttu-id="226d6-970">Se erro, zero é devolvido.</span><span class="sxs-lookup"><span data-stu-id="226d6-970">If error, zero is returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-971">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-971">Allowed From</span></span>

<span data-ttu-id="226d6-972">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-972">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-973">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-973">Example</span></span>

```c
/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, my_new_object);

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_copy_extended"></a><span data-ttu-id="226d6-974">nx_snmp_object_copy_extended</span><span class="sxs-lookup"><span data-stu-id="226d6-974">nx_snmp_object_copy_extended</span></span>
<span data-ttu-id="226d6-975">Copiar um objeto</span><span class="sxs-lookup"><span data-stu-id="226d6-975">Copy an object</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-976">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-976">Prototype</span></span>

```c
UINT  nx_snmp_object_copy_extended(UCHAR *source_object_name, 
                             UINT source_object_name_length,
                             UCHAR *destination_object_name_buffer,
                             UINT destination_object_name_buffer_size);
```

### <a name="description"></a><span data-ttu-id="226d6-977">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-977">Description</span></span>

<span data-ttu-id="226d6-978">Este serviço copia o objeto de origem na notação ASCII SIM para o objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="226d6-978">This service copies the source object in ASCII SIM notation to the destination object.</span></span>

<span data-ttu-id="226d6-979">Este serviço substitui *nx_snmp_object_copy.*</span><span class="sxs-lookup"><span data-stu-id="226d6-979">This service replaces *nx_snmp_object_copy().*</span></span> <span data-ttu-id="226d6-980">Esta versão requer que os chamadores forneçam informações de comprimento.</span><span class="sxs-lookup"><span data-stu-id="226d6-980">This version requires callers to supply length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-981">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-981">Input Parameters</span></span>

- <span data-ttu-id="226d6-982">**source_object_name** Ponteiro para identificação do objeto de origem.</span><span class="sxs-lookup"><span data-stu-id="226d6-982">**source_object_name** Pointer to source object ID.</span></span>
- <span data-ttu-id="226d6-983">**source_object_name_length** Comprimento da identificação do objeto de origem.</span><span class="sxs-lookup"><span data-stu-id="226d6-983">**source_object_name_length** Length of source object ID.</span></span>
- <span data-ttu-id="226d6-984">**destination_object_name_buffer** Ponteiro para o tampão do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="226d6-984">**destination_object_name_buffer** Pointer to destination object buffer.</span></span>
- <span data-ttu-id="226d6-985">**destination_object_name_buffer_size** Tamanho do tampão de objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="226d6-985">**destination_object_name_buffer_size** Size of destination object buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-986">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-986">Return Values</span></span>

- <span data-ttu-id="226d6-987">**tamanho** Número de bytes copiados para o nome de destino.</span><span class="sxs-lookup"><span data-stu-id="226d6-987">**size** Number of bytes copied to destination name.</span></span> <span data-ttu-id="226d6-988">Se erro, zero é devolvido.</span><span class="sxs-lookup"><span data-stu-id="226d6-988">If error, zero is returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-989">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-989">Allowed From</span></span>

<span data-ttu-id="226d6-990">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-990">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-991">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-991">Example</span></span>

```c
UCHAR   my_object = "1.3.6.1.2.1.1.1.0";
UCHAR   my_new_object[32];


/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, 17, my_new_object, sizeof(my_new_object));

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_counter_get"></a><span data-ttu-id="226d6-992">nx_snmp_object_counter_get</span><span class="sxs-lookup"><span data-stu-id="226d6-992">nx_snmp_object_counter_get</span></span>
<span data-ttu-id="226d6-993">Obtenha objeto de contador</span><span class="sxs-lookup"><span data-stu-id="226d6-993">Get counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-994">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-994">Prototype</span></span>

```c
UINT  nx_snmp_object_counter_get(VOID *source_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a><span data-ttu-id="226d6-995">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-995">Description</span></span>

<span data-ttu-id="226d6-996">Este serviço recupera o objeto de contador no endereço especificado pelo ponteiro de origem e coloca-o na estrutura de dados do objeto NetX.</span><span class="sxs-lookup"><span data-stu-id="226d6-996">This service retrieves the counter object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="226d6-997">Esta rotina é normalmente chamada da rotina de chamada de aplicação GET ou GETNEXT.</span><span class="sxs-lookup"><span data-stu-id="226d6-997">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-998">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-998">Input Parameters</span></span>

- <span data-ttu-id="226d6-999">**source_ptr** Ponteiro para contra-fonte.</span><span class="sxs-lookup"><span data-stu-id="226d6-999">**source_ptr** Pointer to counter source.</span></span>
- <span data-ttu-id="226d6-1000">**object_data** Ponteiro para a estrutura do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="226d6-1000">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-1001">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-1001">Return Values</span></span>

- <span data-ttu-id="226d6-1002">**NX_SUCCESS** (0x00) O objeto de contador foi recuperado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="226d6-1002">**NX_SUCCESS** (0x00) The counter object has be successfully retrieved.</span></span>
- <span data-ttu-id="226d6-1003">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-1003">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-1004">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-1004">Allowed From</span></span>

<span data-ttu-id="226d6-1005">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-1005">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-1006">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-1006">Example</span></span>

```c
/* Get the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object.  */
status =  nx_snmp_object_counter_get(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter_set"></a><span data-ttu-id="226d6-1007">nx_snmp_object_counter_set</span><span class="sxs-lookup"><span data-stu-id="226d6-1007">nx_snmp_object_counter_set</span></span>
<span data-ttu-id="226d6-1008">Definir objeto de contador</span><span class="sxs-lookup"><span data-stu-id="226d6-1008">Set counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-1009">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-1009">Prototype</span></span>

```c
UINT  nx_snmp_object_counter_set(VOID *destination_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="226d6-1010">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-1010">Description</span></span>

<span data-ttu-id="226d6-1011">Este serviço define o contador no endereço especificado pelo ponteiro de destino com o valor de contador na estrutura de dados do objeto NetX.</span><span class="sxs-lookup"><span data-stu-id="226d6-1011">This service sets the counter at the address specified by the destination pointer with the counter value in the NetX object data structure.</span></span> <span data-ttu-id="226d6-1012">Esta rotina é normalmente chamada da rotina de chamada de aplicação SET.</span><span class="sxs-lookup"><span data-stu-id="226d6-1012">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-1013">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-1013">Input Parameters</span></span>

- <span data-ttu-id="226d6-1014">**destination_ptr** Ponteiro para o destino de balcão.</span><span class="sxs-lookup"><span data-stu-id="226d6-1014">**destination_ptr** Pointer to counter destination.</span></span>
- <span data-ttu-id="226d6-1015">**object_data** Ponteiro para contra-fonte estrutura de objeto.</span><span class="sxs-lookup"><span data-stu-id="226d6-1015">**object_data** Pointer to counter source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-1016">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-1016">Return Values</span></span>

- <span data-ttu-id="226d6-1017">**NX_SUCCESS** (0x00) O objeto de contador foi definido com sucesso.</span><span class="sxs-lookup"><span data-stu-id="226d6-1017">**NX_SUCCESS** (0x00) The counter object has be successfully set.</span></span>
- <span data-ttu-id="226d6-1018">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-1018">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="226d6-1019">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-1019">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-1020">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-1020">Allowed From</span></span>

<span data-ttu-id="226d6-1021">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-1021">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-1022">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-1022">Example</span></span>

```c
/* Set the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object with
   the counter object value contained in my_object.  */
status =  nx_snmp_object_counter_set(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   set. */
```

## <a name="nx_snmp_object_counter64_get"></a><span data-ttu-id="226d6-1023">nx_snmp_object_counter64_get</span><span class="sxs-lookup"><span data-stu-id="226d6-1023">nx_snmp_object_counter64_get</span></span>
<span data-ttu-id="226d6-1024">Obtenha objeto de contador de 64 bits</span><span class="sxs-lookup"><span data-stu-id="226d6-1024">Get 64-bit counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-1025">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-1025">Prototype</span></span>

```c
UINT  nx_snmp_object_counter64_get(VOID *source_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="226d6-1026">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-1026">Description</span></span>

<span data-ttu-id="226d6-1027">Este serviço recupera o objeto de contador de 64 bits no endereço especificado pelo ponteiro de origem e coloca-o na estrutura de dados do objeto NetX.</span><span class="sxs-lookup"><span data-stu-id="226d6-1027">This service retrieves the 64-bit counter object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="226d6-1028">Esta rotina é normalmente chamada da rotina de chamada de aplicação GET ou GETNEXT.</span><span class="sxs-lookup"><span data-stu-id="226d6-1028">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-1029">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-1029">Input Parameters</span></span>

- <span data-ttu-id="226d6-1030">**source_ptr** Ponteiro para contra-fonte.</span><span class="sxs-lookup"><span data-stu-id="226d6-1030">**source_ptr** Pointer to counter source.</span></span>
- <span data-ttu-id="226d6-1031">**object_data** Ponteiro para a estrutura do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="226d6-1031">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-1032">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-1032">Return Values</span></span>

- <span data-ttu-id="226d6-1033">**NX_SUCCESS** (0x00) O objeto de contador foi recuperado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="226d6-1033">**NX_SUCCESS** (0x00) The counter object has be successfully retrieved.</span></span>
- <span data-ttu-id="226d6-1034">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="226d6-1034">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-1035">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-1035">Allowed From</span></span>

<span data-ttu-id="226d6-1036">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-1036">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-1037">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-1037">Example</span></span>

```c
/* Get the value of my_64_bit_counter and place it into my_object
   for return.  */
status =  nx_snmp_object_counter64_get(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter64_set"></a><span data-ttu-id="226d6-1038">nx_snmp_object_counter64_set</span><span class="sxs-lookup"><span data-stu-id="226d6-1038">nx_snmp_object_counter64_set</span></span>
<span data-ttu-id="226d6-1039">Definir objeto de contador de 64 bits</span><span class="sxs-lookup"><span data-stu-id="226d6-1039">Set 64-bit counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-1040">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-1040">Prototype</span></span>

```c
UINT  nx_snmp_object_counter64_set(VOID *destination_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a><span data-ttu-id="226d6-1041">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-1041">Description</span></span>

<span data-ttu-id="226d6-1042">Este serviço define o contador de 64 bits no endereço especificado pelo ponteiro de destino com o valor de contador na estrutura de dados do objeto NetX.</span><span class="sxs-lookup"><span data-stu-id="226d6-1042">This service sets the 64-bit counter at the address specified by the destination pointer with the counter value in the NetX object data structure.</span></span> <span data-ttu-id="226d6-1043">Esta rotina é normalmente chamada da rotina de chamada de aplicação SET.</span><span class="sxs-lookup"><span data-stu-id="226d6-1043">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-1044">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-1044">Input Parameters</span></span>

- <span data-ttu-id="226d6-1045">**destination_ptr** Ponteiro para o destino de balcão.</span><span class="sxs-lookup"><span data-stu-id="226d6-1045">**destination_ptr** Pointer to counter destination.</span></span>
- <span data-ttu-id="226d6-1046">**object_data** Ponteiro para contra-fonte estrutura de objeto.</span><span class="sxs-lookup"><span data-stu-id="226d6-1046">**object_data** Pointer to counter source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-1047">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-1047">Return Values</span></span>

- <span data-ttu-id="226d6-1048">**NX_SUCCESS** (0x00) O objeto de contador foi definido com sucesso.</span><span class="sxs-lookup"><span data-stu-id="226d6-1048">**NX_SUCCESS** (0x00) The counter object has be successfully set.</span></span>
- <span data-ttu-id="226d6-1049">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-1049">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="226d6-1050">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-1050">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-1051">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-1051">Allowed From</span></span>

<span data-ttu-id="226d6-1052">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-1052">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-1053">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-1053">Example</span></span>

```c
/* Set the value of my_64_bit_counter with the value in my_object.  */
status =  nx_snmp_object_counter64_set(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   set. */
```

## <a name="nx_snmp_object_end_of_mib"></a><span data-ttu-id="226d6-1054">nx_snmp_object_end_of_mib</span><span class="sxs-lookup"><span data-stu-id="226d6-1054">nx_snmp_object_end_of_mib</span></span>
<span data-ttu-id="226d6-1055">Definir valor final de mib</span><span class="sxs-lookup"><span data-stu-id="226d6-1055">Set end-of-mib value</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-1056">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-1056">Prototype</span></span>

```c
UINT  nx_snmp_object_end_of_mib(VOID *not_used_ptr, 
                              NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="226d6-1057">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-1057">Description</span></span>

<span data-ttu-id="226d6-1058">Este serviço cria um objeto que assinala o fim do MIB e é normalmente chamado da rotina de chamada de aplicação GET ou GETNEXT.</span><span class="sxs-lookup"><span data-stu-id="226d6-1058">This service creates an object signaling the end of the MIB and is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-1059">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-1059">Input Parameters</span></span>

- <span data-ttu-id="226d6-1060">**not_used_ptr** Ponteiro não utilizado – deve ser NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="226d6-1060">**not_used_ptr** Pointer not used – should be NX_NULL.</span></span>
- <span data-ttu-id="226d6-1061">**object_data** Ponteiro para a estrutura do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="226d6-1061">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-1062">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-1062">Return Values</span></span>

- <span data-ttu-id="226d6-1063">**NX_SUCCESS** (0x00) O objeto de fim de mib foi construído com sucesso.</span><span class="sxs-lookup"><span data-stu-id="226d6-1063">**NX_SUCCESS** (0x00) The end-of-mib object has be successfully built.</span></span>
- <span data-ttu-id="226d6-1064">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="226d6-1064">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-1065">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-1065">Allowed From</span></span>

<span data-ttu-id="226d6-1066">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-1066">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-1067">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-1067">Example</span></span>

```c
/* Place an end-of-mib value in my_object.  */
status =  nx_snmp_object_end_of_mib(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now an end-of-mib object. */
```

## <a name="nx_snmp_object_gauge_get"></a><span data-ttu-id="226d6-1068">nx_snmp_object_gauge_get</span><span class="sxs-lookup"><span data-stu-id="226d6-1068">nx_snmp_object_gauge_get</span></span>
<span data-ttu-id="226d6-1069">Obtenha objeto de bitola</span><span class="sxs-lookup"><span data-stu-id="226d6-1069">Get gauge object</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-1070">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-1070">Prototype</span></span>

```c
UINT  nx_snmp_object_gauge_get(VOID *source_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="226d6-1071">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-1071">Description</span></span>

<span data-ttu-id="226d6-1072">Este serviço recupera o objeto de bitola no endereço especificado pelo ponteiro de origem e coloca-o na estrutura de dados do objeto NetX.</span><span class="sxs-lookup"><span data-stu-id="226d6-1072">This service retrieves the gauge object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="226d6-1073">Esta rotina é normalmente chamada da rotina de chamada de aplicação GET ou GETNEXT.</span><span class="sxs-lookup"><span data-stu-id="226d6-1073">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-1074">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-1074">Input Parameters</span></span>

- <span data-ttu-id="226d6-1075">**source_ptr** Ponteiro para medir a fonte.</span><span class="sxs-lookup"><span data-stu-id="226d6-1075">**source_ptr** Pointer to gauge source.</span></span>
- <span data-ttu-id="226d6-1076">**object_data** Ponteiro para a estrutura do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="226d6-1076">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-1077">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-1077">Return Values</span></span>

- <span data-ttu-id="226d6-1078">**NX_SUCCESS** (0x00) O objeto de bitola foi recuperado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="226d6-1078">**NX_SUCCESS** (0x00) The gauge object has be successfully retrieved.</span></span>
- <span data-ttu-id="226d6-1079">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="226d6-1079">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-1080">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-1080">Allowed From</span></span>

<span data-ttu-id="226d6-1081">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-1081">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-1082">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-1082">Example</span></span>

```c
/* Get the value of ifSpeed (1.3.6.1.2.1.2.2.1.5.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_gauge_get(&ifSpeed, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ifSpeed gauge value. */
```

## <a name="nx_snmp_object_gauge_set"></a><span data-ttu-id="226d6-1083">nx_snmp_object_gauge_set</span><span class="sxs-lookup"><span data-stu-id="226d6-1083">nx_snmp_object_gauge_set</span></span>
<span data-ttu-id="226d6-1084">Conjunto de objeto de bitola</span><span class="sxs-lookup"><span data-stu-id="226d6-1084">Set gauge object</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-1085">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-1085">Prototype</span></span>

```c
UINT  nx_snmp_object_gauge_set(VOID *destination_ptr,
                                     NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="226d6-1086">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-1086">Description</span></span>

<span data-ttu-id="226d6-1087">Este serviço define o bitola no endereço especificado pelo ponteiro de destino com o valor de bitola na estrutura de dados do objeto NetX.</span><span class="sxs-lookup"><span data-stu-id="226d6-1087">This service sets the gauge at the address specified by the destination pointer with the gauge value in the NetX object data structure.</span></span> <span data-ttu-id="226d6-1088">Esta rotina é normalmente chamada da rotina de chamada de aplicação SET.</span><span class="sxs-lookup"><span data-stu-id="226d6-1088">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-1089">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-1089">Input Parameters</span></span>

- <span data-ttu-id="226d6-1090">**destination_ptr** Ponteiro para medir o destino.</span><span class="sxs-lookup"><span data-stu-id="226d6-1090">**destination_ptr** Pointer to gauge destination.</span></span>
- <span data-ttu-id="226d6-1091">**object_data** Ponteiro para medir a estrutura do objeto de origem.</span><span class="sxs-lookup"><span data-stu-id="226d6-1091">**object_data** Pointer to gauge source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-1092">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-1092">Return Values</span></span>

- <span data-ttu-id="226d6-1093">**NX_SUCCESS** (0x00) O objeto de bitola foi definido com sucesso.</span><span class="sxs-lookup"><span data-stu-id="226d6-1093">**NX_SUCCESS** (0x00) The gauge object has be successfully set.</span></span>
- <span data-ttu-id="226d6-1094">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-1094">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="226d6-1095">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="226d6-1095">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-1096">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-1096">Allowed From</span></span>

<span data-ttu-id="226d6-1097">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-1097">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-1098">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-1098">Example</span></span>

```c
/* Set the value of “my_gauge” from the gauge value in my_object.  */
status =  nx_snmp_object_gauge_set(&my_gauge, my_object);

/* If status is NX_SUCCESS, the my_gauge now contains the new gauge value. */
```

## <a name="nx_snmp_object_id_get"></a><span data-ttu-id="226d6-1099">nx_snmp_object_id_get</span><span class="sxs-lookup"><span data-stu-id="226d6-1099">nx_snmp_object_id_get</span></span>
<span data-ttu-id="226d6-1100">Obter objeto id</span><span class="sxs-lookup"><span data-stu-id="226d6-1100">Get object id</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-1101">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-1101">Prototype</span></span>

```c
UINT  nx_snmp_object_id_get(VOID *source_ptr, 
                            NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="226d6-1102">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-1102">Description</span></span>

<span data-ttu-id="226d6-1103">Este serviço recupera o ID do objeto (na notação SIM ASCII) no endereço especificado pelo ponteiro de origem e coloca-o na estrutura de dados do objeto NetX.</span><span class="sxs-lookup"><span data-stu-id="226d6-1103">This service retrieves the object ID (in ASCII SIM notation) at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="226d6-1104">Esta rotina é normalmente chamada da rotina de chamada de aplicação GET ou GETNEXT.</span><span class="sxs-lookup"><span data-stu-id="226d6-1104">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-1105">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-1105">Input Parameters</span></span>

- <span data-ttu-id="226d6-1106">**source_ptr** Ponteiro para opor fonte de identificação.</span><span class="sxs-lookup"><span data-stu-id="226d6-1106">**source_ptr** Pointer to object ID source.</span></span>
- <span data-ttu-id="226d6-1107">**object_data** Ponteiro para a estrutura do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="226d6-1107">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-1108">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-1108">Return Values</span></span>

- <span data-ttu-id="226d6-1109">**NX_SUCCESS** (0x00) O ID do objeto foi recuperado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="226d6-1109">**NX_SUCCESS** (0x00) The object ID has be successfully retrieved.</span></span>
- <span data-ttu-id="226d6-1110">**NX_SNMP_ERROR** (0x100) Comprimento inválido do objeto</span><span class="sxs-lookup"><span data-stu-id="226d6-1110">**NX_SNMP_ERROR** (0x100) Invalid length of object</span></span>
- <span data-ttu-id="226d6-1111">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="226d6-1111">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-1112">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-1112">Allowed From</span></span>

<span data-ttu-id="226d6-1113">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-1113">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-1114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-1114">Example</span></span>

```c
/* Get the value of sysObjectID(1.3.6.1.2.1.1.2.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_id_get(&sysObjectID, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysObjectID value. */
```

## <a name="nx_snmp_object_id_set"></a><span data-ttu-id="226d6-1115">nx_snmp_object_id_set</span><span class="sxs-lookup"><span data-stu-id="226d6-1115">nx_snmp_object_id_set</span></span>
<span data-ttu-id="226d6-1116">Definir id objeto</span><span class="sxs-lookup"><span data-stu-id="226d6-1116">Set object id</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-1117">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-1117">Prototype</span></span>

```c
UINT  nx_snmp_object_id_set(VOID *destination_ptr, 
                             NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="226d6-1118">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-1118">Description</span></span>

<span data-ttu-id="226d6-1119">Este serviço define o ID do objeto (na notação SIM ASCII) no endereço especificado pelo ponteiro de destino com o ID do objeto na estrutura de dados do objeto NetX.</span><span class="sxs-lookup"><span data-stu-id="226d6-1119">This service sets the object ID (in ASCII SIM notation) at the address specified by the destination pointer with the object ID in the NetX object data structure.</span></span> <span data-ttu-id="226d6-1120">Esta rotina é normalmente chamada da rotina de chamada de aplicação SET.</span><span class="sxs-lookup"><span data-stu-id="226d6-1120">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-1121">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-1121">Input Parameters</span></span>

- <span data-ttu-id="226d6-1122">**destination_ptr** Ponteiro para opor destino de identificação.</span><span class="sxs-lookup"><span data-stu-id="226d6-1122">**destination_ptr** Pointer to object ID destination.</span></span>
- <span data-ttu-id="226d6-1123">**object_data** Ponteiro para estrutura de objetos.</span><span class="sxs-lookup"><span data-stu-id="226d6-1123">**object_data** Pointer to object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-1124">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-1124">Return Values</span></span>

- <span data-ttu-id="226d6-1125">**NX_SUCCESS** (0x00) O ID do objeto foi definido com sucesso.</span><span class="sxs-lookup"><span data-stu-id="226d6-1125">**NX_SUCCESS** (0x00) The object ID has been successfully set.</span></span>
- <span data-ttu-id="226d6-1126">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-1126">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="226d6-1127">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="226d6-1127">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-1128">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-1128">Allowed From</span></span>

<span data-ttu-id="226d6-1129">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-1129">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-1130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-1130">Example</span></span>

```c
/* Set the string “my_object_id” with the object ID value contained 
   in my_object.  */
status =  nx_snmp_object_id_set(my_object_id, my_object);

/* If status is NX_SUCCESS, the my_object_id now contains the object ID value. */
```

## <a name="nx_snmp_object_integer_get"></a><span data-ttu-id="226d6-1131">nx_snmp_object_integer_get</span><span class="sxs-lookup"><span data-stu-id="226d6-1131">nx_snmp_object_integer_get</span></span>
<span data-ttu-id="226d6-1132">Obter objeto inteiro</span><span class="sxs-lookup"><span data-stu-id="226d6-1132">Get integer object</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-1133">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-1133">Prototype</span></span>

```c
UINT  nx_snmp_object_integer_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="226d6-1134">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-1134">Description</span></span>

<span data-ttu-id="226d6-1135">Este serviço recupera o objeto inteiro no endereço especificado pelo ponteiro de origem e coloca-o na estrutura de dados do objeto NetX.</span><span class="sxs-lookup"><span data-stu-id="226d6-1135">This service retrieves the integer object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="226d6-1136">Esta rotina é normalmente chamada da rotina de chamada de aplicação GET ou GETNEXT.</span><span class="sxs-lookup"><span data-stu-id="226d6-1136">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-1137">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-1137">Input Parameters</span></span>

- <span data-ttu-id="226d6-1138">**source_ptr** Ponteiro para fonte inteiro.</span><span class="sxs-lookup"><span data-stu-id="226d6-1138">**source_ptr** Pointer to integer source.</span></span>
- <span data-ttu-id="226d6-1139">**object_data** Ponteiro para a estrutura do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="226d6-1139">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-1140">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-1140">Return Values</span></span>

- <span data-ttu-id="226d6-1141">**NX_SUCCESS** (0x00) O objeto inteiro foi recuperado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="226d6-1141">**NX_SUCCESS** (0x00) The integer object has been successfully retrieved.</span></span>
- <span data-ttu-id="226d6-1142">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="226d6-1142">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-1143">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-1143">Allowed From</span></span>

<span data-ttu-id="226d6-1144">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-1144">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-1145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-1145">Example</span></span>

```c
/* Get the value of sysServices (1.3.6.1.2.1.1.7.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_integer_get(&sysServices, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysServices value. */
```

## <a name="nx_snmp_object_integer_set"></a><span data-ttu-id="226d6-1146">nx_snmp_object_integer_set</span><span class="sxs-lookup"><span data-stu-id="226d6-1146">nx_snmp_object_integer_set</span></span>
<span data-ttu-id="226d6-1147">Definir objeto inteiro</span><span class="sxs-lookup"><span data-stu-id="226d6-1147">Set integer object</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-1148">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-1148">Prototype</span></span>

```c
UINT  nx_snmp_object_integer_set(VOID *destination_ptr,
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="226d6-1149">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-1149">Description</span></span>

<span data-ttu-id="226d6-1150">Este serviço define o número inteiro no endereço especificado pelo ponteiro de destino com o valor inteiro na estrutura de dados do objeto NetX.</span><span class="sxs-lookup"><span data-stu-id="226d6-1150">This service sets the integer at the address specified by the destination pointer with the integer value in the NetX object data structure.</span></span> <span data-ttu-id="226d6-1151">Esta rotina é normalmente chamada da rotina de chamada de aplicação SET.</span><span class="sxs-lookup"><span data-stu-id="226d6-1151">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-1152">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-1152">Input Parameters</span></span>

- <span data-ttu-id="226d6-1153">**destination_ptr** Ponteiro para o destino inteiro.</span><span class="sxs-lookup"><span data-stu-id="226d6-1153">**destination_ptr** Pointer to integer destination.</span></span>
- <span data-ttu-id="226d6-1154">**object_data** Ponteiro para a estrutura de objetos de origem inteiro.</span><span class="sxs-lookup"><span data-stu-id="226d6-1154">**object_data** Pointer to integer source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-1155">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-1155">Return Values</span></span>

- <span data-ttu-id="226d6-1156">**NX_SUCCESS** (0x00) O objeto inteiro foi definido com sucesso.</span><span class="sxs-lookup"><span data-stu-id="226d6-1156">**NX_SUCCESS** (0x00) The integer object has been successfully set.</span></span>
- <span data-ttu-id="226d6-1157">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-1157">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="226d6-1158">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="226d6-1158">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-1159">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-1159">Allowed From</span></span>

<span data-ttu-id="226d6-1160">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-1160">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-1161">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-1161">Example</span></span>

```c
/* Set the value of ifAdminStatus from the integer value in my_object.  */
status =  nx_snmp_object_integer_set(&ifAdminStatus, my_object);

/* If status is NX_SUCCESS, ifAdnminStatus now contains the new integer value. */
```

## <a name="nx_snmp_object_ip_address_get"></a><span data-ttu-id="226d6-1162">nx_snmp_object_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="226d6-1162">nx_snmp_object_ip_address_get</span></span>
<span data-ttu-id="226d6-1163">Obtenha objeto de endereço IP (apenas IPv4)</span><span class="sxs-lookup"><span data-stu-id="226d6-1163">Get IP address object (IPv4 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-1164">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-1164">Prototype</span></span>

```c
UINT  nx_snmp_object_ip_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="226d6-1165">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-1165">Description</span></span>

<span data-ttu-id="226d6-1166">Este serviço recupera o objeto de endereço IP no endereço especificado pelo ponteiro de origem e coloca-o na estrutura de dados do objeto NetX.</span><span class="sxs-lookup"><span data-stu-id="226d6-1166">This service retrieves the IP address object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="226d6-1167">Esta rotina é normalmente chamada da rotina de chamada de aplicação GET ou GETNEXT.</span><span class="sxs-lookup"><span data-stu-id="226d6-1167">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-1168">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-1168">Input Parameters</span></span>

- <span data-ttu-id="226d6-1169">**source_ptr** Ponteiro para fonte de endereço IPv4.</span><span class="sxs-lookup"><span data-stu-id="226d6-1169">**source_ptr** Pointer to IPv4 address source.</span></span>
- <span data-ttu-id="226d6-1170">**object_data** Ponteiro para a estrutura do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="226d6-1170">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-1171">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-1171">Return Values</span></span>

- <span data-ttu-id="226d6-1172">**NX_SUCCESS** (0x00) O objeto de endereço IP foi recuperado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="226d6-1172">**NX_SUCCESS** (0x00) The IP address object has been successfully retrieved.</span></span>
- <span data-ttu-id="226d6-1173">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="226d6-1173">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-1174">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-1174">Allowed From</span></span>

<span data-ttu-id="226d6-1175">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-1175">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-1176">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-1176">Example</span></span>

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ip_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ipv6_address_get"></a><span data-ttu-id="226d6-1177">nx_snmp_object_ipv6_address_get</span><span class="sxs-lookup"><span data-stu-id="226d6-1177">nx_snmp_object_ipv6_address_get</span></span>
<span data-ttu-id="226d6-1178">Obtenha objeto de endereço IP (apenas IPv6)</span><span class="sxs-lookup"><span data-stu-id="226d6-1178">Get IP address object (IPv6 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="226d6-1179">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-1179">Prototype</span></span>

```c
UINT  nx_snmp_object_ipv6_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA 
                                      *object_data);
```

### <a name="description"></a><span data-ttu-id="226d6-1180">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-1180">Description</span></span>

<span data-ttu-id="226d6-1181">Este serviço recupera o objeto de endereço IPv6 no endereço especificado pelo ponteiro de origem e coloca-o na estrutura de dados do objeto NetX.</span><span class="sxs-lookup"><span data-stu-id="226d6-1181">This service retrieves the IPv6 address object at the address specified by the source pointer and places it in the NetX object data structure.</span></span>
<span data-ttu-id="226d6-1182">Esta rotina é normalmente chamada da rotina de chamada de aplicação GET ou GETNEXT.</span><span class="sxs-lookup"><span data-stu-id="226d6-1182">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-1183">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-1183">Input Parameters</span></span>

- <span data-ttu-id="226d6-1184">**source_ptr** Ponteiro para a fonte de endereço IPv6.</span><span class="sxs-lookup"><span data-stu-id="226d6-1184">**source_ptr** Pointer to IPv6 address source.</span></span>
- <span data-ttu-id="226d6-1185">**object_data** Ponteiro para a estrutura do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="226d6-1185">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-1186">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-1186">Return Values</span></span>

- <span data-ttu-id="226d6-1187">**NX_SUCCESS** (0x00) O objeto de endereço IP foi recuperado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="226d6-1187">**NX_SUCCESS** (0x00) The IP address object has been successfully retrieved.</span></span>
- <span data-ttu-id="226d6-1188">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Código de objeto SNMP de entrada incorreta</span><span class="sxs-lookup"><span data-stu-id="226d6-1188">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Incorrect input SNMP object code</span></span>
- <span data-ttu-id="226d6-1189">**IPv6** NX_NOT_ENABLED (0x14) não habilitado</span><span class="sxs-lookup"><span data-stu-id="226d6-1189">**NX_NOT_ENABLED** (0x14) IPv6 not enabled</span></span>
- <span data-ttu-id="226d6-1190">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="226d6-1190">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-1191">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-1191">Allowed From</span></span>

<span data-ttu-id="226d6-1192">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-1192">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-1193">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-1193">Example</span></span>

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ipv6_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ip_address_set"></a><span data-ttu-id="226d6-1194">nx_snmp_object_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="226d6-1194">nx_snmp_object_ip_address_set</span></span>
<span data-ttu-id="226d6-1195">Definir objeto de endereço IPv4</span><span class="sxs-lookup"><span data-stu-id="226d6-1195">Set IPv4 address object</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-1196">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-1196">Prototype</span></span>

```c
UINT  nx_snmp_object_ip_address_set(VOID *destination_ptr, 
                                    NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="226d6-1197">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-1197">Description</span></span>

<span data-ttu-id="226d6-1198">Este serviço define o endereço IPv4 no endereço especificado pelo ponteiro de destino com o endereço IP na estrutura de dados do objeto NetX.</span><span class="sxs-lookup"><span data-stu-id="226d6-1198">This service sets the IPv4 address at the address specified by the destination pointer with the IP address in the NetX object data structure.</span></span> <span data-ttu-id="226d6-1199">Esta rotina é normalmente chamada da rotina de chamada de aplicação SET.</span><span class="sxs-lookup"><span data-stu-id="226d6-1199">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-1200">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-1200">Input Parameters</span></span>

- <span data-ttu-id="226d6-1201">**destination_ptr** Ponteiro para endereço IP para definir.</span><span class="sxs-lookup"><span data-stu-id="226d6-1201">**destination_ptr** Pointer to IP address to set.</span></span>
- <span data-ttu-id="226d6-1202">**object_data** Ponteiro para a estrutura do objeto do endereço IP.</span><span class="sxs-lookup"><span data-stu-id="226d6-1202">**object_data** Pointer to IP address object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-1203">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-1203">Return Values</span></span>

- <span data-ttu-id="226d6-1204">**NX_SUCCESS** (0x00) O objeto de endereço IP foi definido com sucesso.</span><span class="sxs-lookup"><span data-stu-id="226d6-1204">**NX_SUCCESS** (0x00) The IP address object has been successfully set.</span></span>
- <span data-ttu-id="226d6-1205">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-1205">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="226d6-1206">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="226d6-1206">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-1207">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-1207">Allowed From</span></span>

<span data-ttu-id="226d6-1208">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-1208">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-1209">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-1209">Example</span></span>

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ip_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_ipv6_address_set"></a><span data-ttu-id="226d6-1210">nx_snmp_object_ipv6_address_set</span><span class="sxs-lookup"><span data-stu-id="226d6-1210">nx_snmp_object_ipv6_address_set</span></span>
<span data-ttu-id="226d6-1211">Definir objeto de endereço IPv6</span><span class="sxs-lookup"><span data-stu-id="226d6-1211">Set IPv6 address object</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-1212">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-1212">Prototype</span></span>

```c
UINT  nx_snmp_object_ipv6_address_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA  
                                      *object_data);
```

### <a name="description"></a><span data-ttu-id="226d6-1213">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-1213">Description</span></span>

<span data-ttu-id="226d6-1214">Este serviço define o endereço IPv6 no endereço especificado pelo ponteiro de destino com o endereço IP na estrutura de dados do objeto NetX.</span><span class="sxs-lookup"><span data-stu-id="226d6-1214">This service sets the IPv6 address at the address specified by the destination pointer with the IP address in the NetX object data structure.</span></span> <span data-ttu-id="226d6-1215">Esta rotina é normalmente chamada da rotina de chamada de aplicação SET.</span><span class="sxs-lookup"><span data-stu-id="226d6-1215">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-1216">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-1216">Input Parameters</span></span>

- <span data-ttu-id="226d6-1217">**destination_ptr** Ponteiro para endereço IP para definir.</span><span class="sxs-lookup"><span data-stu-id="226d6-1217">**destination_ptr** Pointer to IP address to set.</span></span>
- <span data-ttu-id="226d6-1218">**object_data** Ponteiro para a estrutura do objeto do endereço IP.</span><span class="sxs-lookup"><span data-stu-id="226d6-1218">**object_data** Pointer to IP address object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-1219">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-1219">Return Values</span></span>

- <span data-ttu-id="226d6-1220">**NX_SUCCESS** (0x00) O endereço IPv6 foi definido com sucesso.</span><span class="sxs-lookup"><span data-stu-id="226d6-1220">**NX_SUCCESS** (0x00) The IPv6 address has been successfully set.</span></span>
- <span data-ttu-id="226d6-1221">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-1221">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="226d6-1222">**IPv6** NX_NOT_ENABLED (0x14) não habilitado</span><span class="sxs-lookup"><span data-stu-id="226d6-1222">**NX_NOT_ENABLED** (0x14) IPv6 not enabled</span></span>
- <span data-ttu-id="226d6-1223">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="226d6-1223">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-1224">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-1224">Allowed From</span></span>

<span data-ttu-id="226d6-1225">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-1225">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-1226">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-1226">Example</span></span>

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ipv6_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_no_instance"></a><span data-ttu-id="226d6-1227">nx_snmp_object_no_instance</span><span class="sxs-lookup"><span data-stu-id="226d6-1227">nx_snmp_object_no_instance</span></span>
<span data-ttu-id="226d6-1228">Definir objeto sem instância</span><span class="sxs-lookup"><span data-stu-id="226d6-1228">Set no-instance object</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-1229">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-1229">Prototype</span></span>

```c
UINT  nx_snmp_object_no_instance(VOID *not_used_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="226d6-1230">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-1230">Description</span></span>

<span data-ttu-id="226d6-1231">Este serviço cria um objeto sinalizando que não havia nenhuma instância do objeto especificado e é tipicamente chamado a partir da rotina de chamada de aplicação GET ou GETNEXT.</span><span class="sxs-lookup"><span data-stu-id="226d6-1231">This service creates an object signaling that there was no instance of the specified object and is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-1232">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-1232">Input Parameters</span></span>

- <span data-ttu-id="226d6-1233">**not_used_ptr** Ponteiro não utilizado – deve ser NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="226d6-1233">**not_used_ptr** Pointer not used – should be NX_NULL.</span></span>
- <span data-ttu-id="226d6-1234">**object_data** Ponteiro para a estrutura do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="226d6-1234">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-1235">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-1235">Return Values</span></span>

- <span data-ttu-id="226d6-1236">**NX_SUCCESS** (0x00) O objeto sem exemplo foi construído com sucesso.</span><span class="sxs-lookup"><span data-stu-id="226d6-1236">**NX_SUCCESS** (0x00) The no-instance object has been successfully built.</span></span>
- <span data-ttu-id="226d6-1237">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="226d6-1237">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-1238">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-1238">Allowed From</span></span>

<span data-ttu-id="226d6-1239">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-1239">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-1240">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-1240">Example</span></span>

```c
/* Place no-instance value in my_object.  */
status =  nx_snmp_object_no_instance(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a no-instance object. */
```

## <a name="nx_snmp_object_not_found"></a><span data-ttu-id="226d6-1241">nx_snmp_object_not_found</span><span class="sxs-lookup"><span data-stu-id="226d6-1241">nx_snmp_object_not_found</span></span>
<span data-ttu-id="226d6-1242">Definir objeto não encontrado</span><span class="sxs-lookup"><span data-stu-id="226d6-1242">Set not-found object</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-1243">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-1243">Prototype</span></span>

```c
UINT  nx_snmp_object_not_found(VOID *not_used_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="226d6-1244">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-1244">Description</span></span>

<span data-ttu-id="226d6-1245">Este serviço cria um objeto que sinaliza que o objeto não foi encontrado e é normalmente chamado da rotina de chamada de aplicação GET ou GETNEXT.</span><span class="sxs-lookup"><span data-stu-id="226d6-1245">This service creates an object signaling the object was not found and is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-1246">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-1246">Input Parameters</span></span>

- <span data-ttu-id="226d6-1247">**not_used_ptr** Ponteiro não utilizado – deve ser NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="226d6-1247">**not_used_ptr** Pointer not used – should be NX_NULL.</span></span>
- <span data-ttu-id="226d6-1248">**object_data** Ponteiro para a estrutura do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="226d6-1248">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-1249">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-1249">Return Values</span></span>

- <span data-ttu-id="226d6-1250">**NX_SUCCESS** (0x00) O objeto não encontrado foi construído com sucesso.</span><span class="sxs-lookup"><span data-stu-id="226d6-1250">**NX_SUCCESS** (0x00) The not-found object has been successfully built.</span></span>
- <span data-ttu-id="226d6-1251">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="226d6-1251">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-1252">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-1252">Allowed From</span></span>

<span data-ttu-id="226d6-1253">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-1253">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-1254">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-1254">Example</span></span>

```c
/* Place not-found value in my_object.  */
status =  nx_snmp_object_not_found(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a not-found object. */
```

## <a name="nx_snmp_object_octet_string_get"></a><span data-ttu-id="226d6-1255">nx_snmp_object_octet_string_get</span><span class="sxs-lookup"><span data-stu-id="226d6-1255">nx_snmp_object_octet_string_get</span></span>
<span data-ttu-id="226d6-1256">Obtenha objeto de corda de octeto</span><span class="sxs-lookup"><span data-stu-id="226d6-1256">Get octet string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-1257">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-1257">Prototype</span></span>

```c
UINT  nx_snmp_object_octet_string_get(VOID *source_ptr,
                                            NX_SNMP_OBJECT_DATA *object_data, 
                                      UINT length);
```
### <a name="description"></a><span data-ttu-id="226d6-1258">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-1258">Description</span></span>

<span data-ttu-id="226d6-1259">Este serviço recupera a cadeia de octeto no endereço especificado pelo ponteiro de origem e coloca-o na estrutura de dados do objeto NetX.</span><span class="sxs-lookup"><span data-stu-id="226d6-1259">This service retrieves the octet string at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="226d6-1260">Esta rotina é normalmente chamada da rotina de chamada de aplicação GET ou GETNEXT.</span><span class="sxs-lookup"><span data-stu-id="226d6-1260">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-1261">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-1261">Input Parameters</span></span>

- <span data-ttu-id="226d6-1262">**source_ptr** Ponteiro para fonte de cadeia de octeto.</span><span class="sxs-lookup"><span data-stu-id="226d6-1262">**source_ptr** Pointer to octet string source.</span></span>
- <span data-ttu-id="226d6-1263">**object_data** Ponteiro para a estrutura do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="226d6-1263">**object_data** Pointer to destination object structure.</span></span>
- <span data-ttu-id="226d6-1264">**comprimento** Número de bytes na corda de octeto.</span><span class="sxs-lookup"><span data-stu-id="226d6-1264">**length** Number of bytes in octet string.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-1265">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-1265">Return Values</span></span>

- <span data-ttu-id="226d6-1266">**NX_SUCCESS** (0x00) O objeto de corda de octeto foi recuperado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="226d6-1266">**NX_SUCCESS** (0x00) The octet string object has been successfully retrieved.</span></span>
- <span data-ttu-id="226d6-1267">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="226d6-1267">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-1268">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-1268">Allowed From</span></span>

<span data-ttu-id="226d6-1269">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-1269">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-1270">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-1270">Example</span></span>

```c
/* Get the value of the 6-byte ifPhysAddress (1.3.6.1.2.1.2.2.1.6.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_octet_string_get(ifPhysAddress, my_object, 6);

/* If status is NX_SUCCESS, the my_object now contains the ifPhysAddress value. */
```

## <a name="nx_snmp_object_octet_string_set"></a><span data-ttu-id="226d6-1271">nx_snmp_object_octet_string_set</span><span class="sxs-lookup"><span data-stu-id="226d6-1271">nx_snmp_object_octet_string_set</span></span>
<span data-ttu-id="226d6-1272">Definir objeto de corda de octeto</span><span class="sxs-lookup"><span data-stu-id="226d6-1272">Set octet string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-1273">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-1273">Prototype</span></span>

```c
UINT  nx_snmp_object_octet_string_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="226d6-1274">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-1274">Description</span></span>

<span data-ttu-id="226d6-1275">Este serviço define a cadeia de octeto no endereço especificado pelo ponteiro de destino com a cadeia de octeto na estrutura de dados do objeto NetX.</span><span class="sxs-lookup"><span data-stu-id="226d6-1275">This service sets the octet string at the address specified by the destination pointer with the octet string in the NetX object data structure.</span></span> <span data-ttu-id="226d6-1276">Esta rotina é normalmente chamada da rotina de chamada de aplicação SET.</span><span class="sxs-lookup"><span data-stu-id="226d6-1276">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-1277">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-1277">Input Parameters</span></span>

- <span data-ttu-id="226d6-1278">**destination_ptr** Ponteiro para destino de cadeia de octeto.</span><span class="sxs-lookup"><span data-stu-id="226d6-1278">**destination_ptr** Pointer to octet string destination.</span></span>
- <span data-ttu-id="226d6-1279">**object_data** Ponteiro para estrutura de objeto de fonte de cadeia de octeto.</span><span class="sxs-lookup"><span data-stu-id="226d6-1279">**object_data** Pointer to octet string source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-1280">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-1280">Return Values</span></span>

- <span data-ttu-id="226d6-1281">**NX_SUCCESS** (0x00) O objeto de corda de octeto foi definido com sucesso.</span><span class="sxs-lookup"><span data-stu-id="226d6-1281">**NX_SUCCESS** (0x00) The octet string object has been successfully set.</span></span>
- <span data-ttu-id="226d6-1282">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-1282">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="226d6-1283">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="226d6-1283">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-1284">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-1284">Allowed From</span></span>

<span data-ttu-id="226d6-1285">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-1285">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-1286">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-1286">Example</span></span>

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   octet string in my_object.  */
status =  nx_snmp_object_octet_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new octet string. */
```

## <a name="nx_snmp_object_string_get"></a><span data-ttu-id="226d6-1287">nx_snmp_object_string_get</span><span class="sxs-lookup"><span data-stu-id="226d6-1287">nx_snmp_object_string_get</span></span>
<span data-ttu-id="226d6-1288">Obtenha objeto de corda ASCII</span><span class="sxs-lookup"><span data-stu-id="226d6-1288">Get ASCII string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-1289">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-1289">Prototype</span></span>

```c
UINT  nx_snmp_object_string_get(VOID *source_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="226d6-1290">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-1290">Description</span></span>

<span data-ttu-id="226d6-1291">Este serviço recupera a cadeia ASCII no endereço especificado pelo ponteiro de origem e coloca-a na estrutura de dados do objeto NetX.</span><span class="sxs-lookup"><span data-stu-id="226d6-1291">This service retrieves the ASCII string at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="226d6-1292">Esta rotina é normalmente chamada da rotina de chamada de aplicação GET ou GETNEXT.</span><span class="sxs-lookup"><span data-stu-id="226d6-1292">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-1293">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-1293">Input Parameters</span></span>

- <span data-ttu-id="226d6-1294">**source_ptr** Ponteiro para fonte de cadeia ASCII.</span><span class="sxs-lookup"><span data-stu-id="226d6-1294">**source_ptr** Pointer to ASCII string source.</span></span>
- <span data-ttu-id="226d6-1295">**object_data** Ponteiro para a estrutura do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="226d6-1295">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-1296">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-1296">Return Values</span></span>

- <span data-ttu-id="226d6-1297">**NX_SUCCESS** (0x00) O objeto de corda ASCII foi recuperado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="226d6-1297">**NX_SUCCESS** (0x00) The ASCII string object has been successfully retrieved.</span></span>
- <span data-ttu-id="226d6-1298">**NX_SNMP_ERROR** (0x100) String é muito grande</span><span class="sxs-lookup"><span data-stu-id="226d6-1298">**NX_SNMP_ERROR** (0x100) String is too big</span></span>  
- <span data-ttu-id="226d6-1299">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="226d6-1299">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-1300">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-1300">Allowed From</span></span>

<span data-ttu-id="226d6-1301">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-1301">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-1302">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-1302">Example</span></span>

```c
/* Get the value of the sysDescr (1.3.6.1.2.1.1.1.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_string_get(sysDescr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysDescr string. */
```

## <a name="nx_snmp_object_string_set"></a><span data-ttu-id="226d6-1303">nx_snmp_object_string_set</span><span class="sxs-lookup"><span data-stu-id="226d6-1303">nx_snmp_object_string_set</span></span>
<span data-ttu-id="226d6-1304">Definir objeto de corda ASCII</span><span class="sxs-lookup"><span data-stu-id="226d6-1304">Set ASCII string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-1305">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-1305">Prototype</span></span>

```c
UINT  nx_snmp_object_string_set(VOID *destination_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="226d6-1306">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-1306">Description</span></span>

<span data-ttu-id="226d6-1307">Este serviço define a cadeia ASCII no endereço especificado pelo ponteiro de destino com a cadeia ASCII na estrutura de dados do objeto NetX.</span><span class="sxs-lookup"><span data-stu-id="226d6-1307">This service sets the ASCII string at the address specified by the destination pointer with the ASCII string in the NetX object data structure.</span></span> <span data-ttu-id="226d6-1308">Esta rotina é normalmente chamada da rotina de chamada de aplicação SET.</span><span class="sxs-lookup"><span data-stu-id="226d6-1308">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-1309">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-1309">Input Parameters</span></span>

- <span data-ttu-id="226d6-1310">**destination_ptr** Ponteiro para destino de cordas ASCII.</span><span class="sxs-lookup"><span data-stu-id="226d6-1310">**destination_ptr** Pointer to ASCII string destination.</span></span>
- <span data-ttu-id="226d6-1311">**object_data** Ponteiro para a estrutura do objeto de fonte de cadeia ASCII.</span><span class="sxs-lookup"><span data-stu-id="226d6-1311">**object_data** Pointer to ASCII string source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-1312">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-1312">Return Values</span></span>

- <span data-ttu-id="226d6-1313">**NX_SUCCESS** (0x00) O objeto de corda ASCII foi definido com sucesso.</span><span class="sxs-lookup"><span data-stu-id="226d6-1313">**NX_SUCCESS** (0x00) The ASCII string object has been successfully set.</span></span>
- <span data-ttu-id="226d6-1314">**NX_SNMP_ERROR** (0x100) Corda demasiado grande.</span><span class="sxs-lookup"><span data-stu-id="226d6-1314">**NX_SNMP_ERROR** (0x100) String too large.</span></span>
- <span data-ttu-id="226d6-1315">**NX_SNMP_ERROR_BADVALUE** (0x03) Personagem inválido na corda</span><span class="sxs-lookup"><span data-stu-id="226d6-1315">**NX_SNMP_ERROR_BADVALUE** (0x03) Invalid character in string</span></span>
- <span data-ttu-id="226d6-1316">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-1316">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="226d6-1317">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="226d6-1317">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-1318">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-1318">Allowed From</span></span>

<span data-ttu-id="226d6-1319">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-1319">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-1320">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-1320">Example</span></span>

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   ASCII string in my_object.  */
status =  nx_snmp_object_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new ASCII string. */
```

## <a name="nx_snmp_object_timetics_get"></a><span data-ttu-id="226d6-1321">nx_snmp_object_timetics_get</span><span class="sxs-lookup"><span data-stu-id="226d6-1321">nx_snmp_object_timetics_get</span></span>
<span data-ttu-id="226d6-1322">Obter objeto timetics</span><span class="sxs-lookup"><span data-stu-id="226d6-1322">Get timetics object</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-1323">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-1323">Prototype</span></span>

```c
UINT  nx_snmp_object_timetics_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="226d6-1324">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-1324">Description</span></span>

<span data-ttu-id="226d6-1325">Este serviço recupera os relógios no endereço especificado pelo ponteiro de origem e coloca-o na estrutura de dados do objeto NetX.</span><span class="sxs-lookup"><span data-stu-id="226d6-1325">This service retrieves the timetics at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="226d6-1326">Esta rotina é normalmente chamada da rotina de chamada de aplicação GET ou GETNEXT.</span><span class="sxs-lookup"><span data-stu-id="226d6-1326">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-1327">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-1327">Input Parameters</span></span>

- <span data-ttu-id="226d6-1328">**source_ptr** Ponteiro para fonte de timetics.</span><span class="sxs-lookup"><span data-stu-id="226d6-1328">**source_ptr** Pointer to timetics source.</span></span>
- <span data-ttu-id="226d6-1329">**object_data** Ponteiro para a estrutura do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="226d6-1329">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-1330">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-1330">Return Values</span></span>

- <span data-ttu-id="226d6-1331">**NX_SUCCESS** (0x00) O objeto de tempotético foi recuperado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="226d6-1331">**NX_SUCCESS** (0x00) The timetics object has been successfully retrieved.</span></span>
- <span data-ttu-id="226d6-1332">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="226d6-1332">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-1333">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-1333">Allowed From</span></span>

<span data-ttu-id="226d6-1334">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-1334">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-1335">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-1335">Example</span></span>

```c
/* Get the value of the sysUpTime (1.3.6.1.2.1.1.3.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_timetics_get(sysUpTime, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysUpTime value. */
```

## <a name="nx_snmp_object_timetics_set"></a><span data-ttu-id="226d6-1336">nx_snmp_object_timetics_set</span><span class="sxs-lookup"><span data-stu-id="226d6-1336">nx_snmp_object_timetics_set</span></span>
<span data-ttu-id="226d6-1337">Objeto de timetics definido</span><span class="sxs-lookup"><span data-stu-id="226d6-1337">Set timetics object</span></span> 

### <a name="prototype"></a><span data-ttu-id="226d6-1338">Prototype</span><span class="sxs-lookup"><span data-stu-id="226d6-1338">Prototype</span></span>

```c
UINT  nx_snmp_object_timetics_set(VOID *destination_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="226d6-1339">Descrição</span><span class="sxs-lookup"><span data-stu-id="226d6-1339">Description</span></span>

<span data-ttu-id="226d6-1340">Este serviço define a variável timetics no endereço especificado pelo ponteiro de destino com os timetics na estrutura de dados do objeto NetX.</span><span class="sxs-lookup"><span data-stu-id="226d6-1340">This service sets the timetics variable at the address specified by the destination pointer with the timetics in the NetX object data structure.</span></span>
<span data-ttu-id="226d6-1341">Esta rotina é normalmente chamada da rotina de chamada de aplicação SET.</span><span class="sxs-lookup"><span data-stu-id="226d6-1341">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="226d6-1342">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="226d6-1342">Input Parameters</span></span>

- <span data-ttu-id="226d6-1343">**destination_ptr** Ponteiro para destino timetics.</span><span class="sxs-lookup"><span data-stu-id="226d6-1343">**destination_ptr** Pointer to timetics destination.</span></span>
- <span data-ttu-id="226d6-1344">**object_data** Ponteiro para a estrutura do objeto de origem timetics.</span><span class="sxs-lookup"><span data-stu-id="226d6-1344">**object_data** Pointer to timetics source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="226d6-1345">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="226d6-1345">Return Values</span></span>

- <span data-ttu-id="226d6-1346">**NX_SUCCESS** (0x00) O objeto de cronometros foi definido com sucesso.</span><span class="sxs-lookup"><span data-stu-id="226d6-1346">**NX_SUCCESS** (0x00) The timetics object has been successfully set.</span></span>
- <span data-ttu-id="226d6-1347">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto inválido.</span><span class="sxs-lookup"><span data-stu-id="226d6-1347">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="226d6-1348">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="226d6-1348">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="226d6-1349">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="226d6-1349">Allowed From</span></span>

<span data-ttu-id="226d6-1350">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="226d6-1350">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="226d6-1351">Exemplo</span><span class="sxs-lookup"><span data-stu-id="226d6-1351">Example</span></span>

```c
/* Set the value of “my_time” from the timetics value in my_object.  */
status =  nx_snmp_object_timetics_set(&my_time, my_object);

/* If status is NX_SUCCESS, my_time now contains the new timetics. */
```