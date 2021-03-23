---
title: Capítulo 4 - Descrição dos Serviços LWM2M CLIENTE
description: Este capítulo contém uma descrição de todos os serviços do Cliente LWM2M por ordem alfabética.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 825a215ba756b39b6d76e6cc773c288e8b8aab01
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825928"
---
# <a name="chapter-4--description-of-lwm2m-client-services"></a><span data-ttu-id="5ada2-103">Capítulo 4 Descrição dos serviços LWM2M CLIENTE</span><span class="sxs-lookup"><span data-stu-id="5ada2-103">Chapter 4  Description of LWM2M CLIENT Services</span></span>

<span data-ttu-id="5ada2-104">Este capítulo contém uma descrição de todos os serviços do Cliente LWM2M listados abaixo por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="5ada2-104">This chapter contains a description of all LWM2M Client services listed below in alphabetic order.</span></span>

<span data-ttu-id="5ada2-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo  **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the  **NX_DISABLE_ERROR_CHECKING** define that is used to disable API  error checking, while non-bold values are completely disabled.</span></span>

<span data-ttu-id="5ada2-106">**Gestão de Clientes LWM2M:**</span><span class="sxs-lookup"><span data-stu-id="5ada2-106">**LWM2M Client Management:**</span></span>

- <span data-ttu-id="5ada2-107">nx_lwm2m_client_create: *Criar cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="5ada2-107">nx_lwm2m_client_create: *Create LWM2M Client*</span></span>

- <span data-ttu-id="5ada2-108">nx_lwm2m_client_delete: *Eliminar cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="5ada2-108">nx_lwm2m_client_delete: *Delete LWM2M Client*</span></span>

- <span data-ttu-id="5ada2-109">nx_lwm2m_client_lock: Bloquear *cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="5ada2-109">nx_lwm2m_client_lock: *Lock LWM2M Client*</span></span>

- <span data-ttu-id="5ada2-110">nx_lwm2m_client_unlock: Desbloquear *Cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="5ada2-110">nx_lwm2m_client_unlock: *Unlock LWM2M Client*</span></span>

<span data-ttu-id="5ada2-111">**Gestão de Sessão de Clientes LWM2M:**</span><span class="sxs-lookup"><span data-stu-id="5ada2-111">**LWM2M Client Session Management:**</span></span>

- <span data-ttu-id="5ada2-112">nx_lwm2m_client_session_create: *Criar sessão de clientes LWM2M*</span><span class="sxs-lookup"><span data-stu-id="5ada2-112">nx_lwm2m_client_session_create: *Create LWM2M Client Session*</span></span>

- <span data-ttu-id="5ada2-113">nx_lwm2m_client_session_delete: Eliminar *sessão de clientes LWM2M*</span><span class="sxs-lookup"><span data-stu-id="5ada2-113">nx_lwm2m_client_session_delete: *Delete LWM2M Client Session*</span></span>

- <span data-ttu-id="5ada2-114">nx_lwm2m_client_session_bootstrap: Inicie *uma sessão com um Servidor Bootstrap*</span><span class="sxs-lookup"><span data-stu-id="5ada2-114">nx_lwm2m_client_session_bootstrap: *Start a session with a Bootstrap Server*</span></span>

- <span data-ttu-id="5ada2-115">nx_lwm2m_client_session_bootstrap_dtls: Inicie *uma sessão segura com um Servidor Bootstrap*</span><span class="sxs-lookup"><span data-stu-id="5ada2-115">nx_lwm2m_client_session_bootstrap_dtls: *Start a secure session with a Bootstrap Server*</span></span>

- <span data-ttu-id="5ada2-116">nx_lwm2m_client_session_register_info_get: Obtenha *informações de registo do servidor LWM2M*</span><span class="sxs-lookup"><span data-stu-id="5ada2-116">nx_lwm2m_client_session_register_info_get: *Get LWM2M Server register info*</span></span>

- <span data-ttu-id="5ada2-117">nx_lwm2m_client_session_register: Inicie *uma sessão com um Servidor LWM2M*</span><span class="sxs-lookup"><span data-stu-id="5ada2-117">nx_lwm2m_client_session_register: *Start a session with a LWM2M Server*</span></span>

- <span data-ttu-id="5ada2-118">nx_lwm2m_client_session_register_dtls: Inicie *uma sessão segura com um Servidor LWM2M*</span><span class="sxs-lookup"><span data-stu-id="5ada2-118">nx_lwm2m_client_session_register_dtls: *Start a secure session with a LWM2M Server*</span></span>

- <span data-ttu-id="5ada2-119">nx_lwm2m_client_session_update: Atualizar *uma sessão com um Servidor LWM2M*</span><span class="sxs-lookup"><span data-stu-id="5ada2-119">nx_lwm2m_client_session_update: *Update a session with a LWM2M Server*</span></span>

- <span data-ttu-id="5ada2-120">nx_lwm2m_client_session_deregister: Terminar *uma sessão com um servidor LWM2M*</span><span class="sxs-lookup"><span data-stu-id="5ada2-120">nx_lwm2m_client_session_deregister: *Terminate a session with a LWM2M Server*</span></span>

- <span data-ttu-id="5ada2-121">nx_lwm2m_client_session_error_get: Obtenha *o último erro de uma sessão*</span><span class="sxs-lookup"><span data-stu-id="5ada2-121">nx_lwm2m_client_session_error_get: *Get last error of a session*</span></span>

<span data-ttu-id="5ada2-122">**Implementação do objeto do dispositivo:**</span><span class="sxs-lookup"><span data-stu-id="5ada2-122">**Device Object Implementation:**</span></span>

- <span data-ttu-id="5ada2-123">nx_lwm2m_client_device_callbacks_set: *Definir chamadas de aplicação de objeto de dispositivo*</span><span class="sxs-lookup"><span data-stu-id="5ada2-123">nx_lwm2m_client_device_callbacks_set: *Set Device Object application callbacks*</span></span>

- <span data-ttu-id="5ada2-124">nx_lwm2m_client_device_error_push: Adicionar *código de erro ao objeto do dispositivo*</span><span class="sxs-lookup"><span data-stu-id="5ada2-124">nx_lwm2m_client_device_error_push: *Add error code to Device Object*</span></span>

- <span data-ttu-id="5ada2-125">nx_lwm2m_client_device_error_reset: Redefinir *códigos de erro do objeto do dispositivo*</span><span class="sxs-lookup"><span data-stu-id="5ada2-125">nx_lwm2m_client_device_error_reset: *Reset error codes of Device Object*</span></span>

- <span data-ttu-id="5ada2-126">nx_lwm2m_client_device_resource_changed: *Alteração do sinal do recurso objeto do dispositivo*</span><span class="sxs-lookup"><span data-stu-id="5ada2-126">nx_lwm2m_client_device_resource_changed: *Signal change of Device Object resource*</span></span>

<span data-ttu-id="5ada2-127">**Implementação do objeto de atualização de firmware:**</span><span class="sxs-lookup"><span data-stu-id="5ada2-127">**Firmware Update Object Implementation:**</span></span>

- <span data-ttu-id="5ada2-128">nx_lwm2m_firmware_create: Criar *objeto de atualização de firmware*</span><span class="sxs-lookup"><span data-stu-id="5ada2-128">nx_lwm2m_firmware_create: *Create Firmware Update Object*</span></span>

- <span data-ttu-id="5ada2-129">nx_lwm2m_firmware_package_info_set: Definir *informações do pacote de atualização de firmware*</span><span class="sxs-lookup"><span data-stu-id="5ada2-129">nx_lwm2m_firmware_package_info_set: *Set Firmware Update Package Information*</span></span>

- <span data-ttu-id="5ada2-130">nx_lwm2m_firmware_result_set: Definir *resultado da atualização do firmware*</span><span class="sxs-lookup"><span data-stu-id="5ada2-130">nx_lwm2m_firmware_result_set: *Set Firmware Update Result*</span></span>

- <span data-ttu-id="5ada2-131">nx_lwm2m_firmware_state_set: Definir *Estado de Atualização de Firmware*</span><span class="sxs-lookup"><span data-stu-id="5ada2-131">nx_lwm2m_firmware_state_set: *Set Firmware Update State*</span></span>

<span data-ttu-id="5ada2-132">**Implementação de objetos personalizados:**</span><span class="sxs-lookup"><span data-stu-id="5ada2-132">**Custom Objects Implementation:**</span></span>

- <span data-ttu-id="5ada2-133">nx_lwm2m_client_object_add: Adicionar *implementação de objeto ao cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="5ada2-133">nx_lwm2m_client_object_add: *Add Object implementation to LWM2M Client*</span></span>

- <span data-ttu-id="5ada2-134">nx_lwm2m_client_object_remove: Remover *a implementação do objeto do cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="5ada2-134">nx_lwm2m_client_object_remove: *Remove Object implementation from LWM2M Client*</span></span>

- <span data-ttu-id="5ada2-135">nx_lwm2m_client_object_instance_add: Adicionar *instância de objeto ao cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="5ada2-135">nx_lwm2m_client_object_instance_add: *Add Object Instance to LWM2M Client*</span></span>

- <span data-ttu-id="5ada2-136">nx_lwm2m_client_object_instance_remove: Remover *a instância do objeto do cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="5ada2-136">nx_lwm2m_client_object_instance_remove: *Remove Object Instance from LWM2M Client*</span></span>

- <span data-ttu-id="5ada2-137">nx_lwm2m_object_resource_changed: Alteração *do sinal de um valor de recurso de uma Instância de Objeto*</span><span class="sxs-lookup"><span data-stu-id="5ada2-137">nx_lwm2m_object_resource_changed: *Signal change of a resource value of an Object Instance*</span></span>

<span data-ttu-id="5ada2-138">**Gestão local de dispositivos**</span><span class="sxs-lookup"><span data-stu-id="5ada2-138">**Local Device Management**</span></span>

- <span data-ttu-id="5ada2-139">nx_lwm2m_client_object_create: Criar *uma nova instância de objeto*</span><span class="sxs-lookup"><span data-stu-id="5ada2-139">nx_lwm2m_client_object_create: *Create a new Object Instance*</span></span>

- <span data-ttu-id="5ada2-140">nx_lwm2m_client_object_delete: Eliminar *uma instância de objeto*</span><span class="sxs-lookup"><span data-stu-id="5ada2-140">nx_lwm2m_client_object_delete: *Delete an Object Instance*</span></span>

- <span data-ttu-id="5ada2-141">nx_lwm2m_client_object_discover: Descubra *os recursos de uma instância de objeto*</span><span class="sxs-lookup"><span data-stu-id="5ada2-141">nx_lwm2m_client_object_discover: *Discover resources of an Object Instance*</span></span>

- <span data-ttu-id="5ada2-142">nx_lwm2m_client_object_execute: Executar *recurso de uma instância de objeto*</span><span class="sxs-lookup"><span data-stu-id="5ada2-142">nx_lwm2m_client_object_execute: *Execute resource of an Object Instance*</span></span>

- <span data-ttu-id="5ada2-143">nx_lwm2m_client_object_next_get: *Obtenha a lista de Objetos implementados pelo Cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="5ada2-143">nx_lwm2m_client_object_next_get: *Get the list of Objects implemented by the LWM2M Client*</span></span>

- <span data-ttu-id="5ada2-144">nx_lwm2m_client_object_instance_next_get: *Obtenha a lista de instâncias de um objeto*</span><span class="sxs-lookup"><span data-stu-id="5ada2-144">nx_lwm2m_client_object_instance_next_get: *Get the list of Instances of an Object*</span></span>

- <span data-ttu-id="5ada2-145">nx_lwm2m_client_object_read: Ler *os valores dos recursos de uma Instância de Objeto*</span><span class="sxs-lookup"><span data-stu-id="5ada2-145">nx_lwm2m_client_object_read: *Read resources values of an Object Instance*</span></span>

- <span data-ttu-id="5ada2-146">nx_lwm2m_client_object_write: Alterar *os valores de recursos de uma instância de objeto*</span><span class="sxs-lookup"><span data-stu-id="5ada2-146">nx_lwm2m_client_object_write: *Change resources values of an Object instance*</span></span>

<span data-ttu-id="5ada2-147">**Definição de Informações e Valores de Recursos:**</span><span class="sxs-lookup"><span data-stu-id="5ada2-147">**Resources Info and Values Setting:**</span></span>

- <span data-ttu-id="5ada2-148">nx_lwm2m_client_resource_info_set: Definir *a informação de recursos*</span><span class="sxs-lookup"><span data-stu-id="5ada2-148">nx_lwm2m_client_resource_info_set: *Set the resource info*</span></span>

- <span data-ttu-id="5ada2-149">nx_lwm2m_client_resource_string_set: *Definir o valor do recurso como cadeia*</span><span class="sxs-lookup"><span data-stu-id="5ada2-149">nx_lwm2m_client_resource_string_set: *Set the resource value as string*</span></span>

- <span data-ttu-id="5ada2-150">nx_lwm2m_client_resource_integer32_set: *Desaprote o valor do recurso como inteiro de 32 Bits*</span><span class="sxs-lookup"><span data-stu-id="5ada2-150">nx_lwm2m_client_resource_integer32_set: *Set the resource value as 32-Bit integer*</span></span>

- <span data-ttu-id="5ada2-151">nx_lwm2m_client_resource_integer64_set: *Desaprote o valor do recurso como inteiro de 64 Bits*</span><span class="sxs-lookup"><span data-stu-id="5ada2-151">nx_lwm2m_client_resource_integer64_set: *Set the resource value as 64-Bit integer*</span></span>

- <span data-ttu-id="5ada2-152">nx_lwm2m_client_resource_float32_set: *Desaprova o valor do recurso como boia de 32 Bits*</span><span class="sxs-lookup"><span data-stu-id="5ada2-152">nx_lwm2m_client_resource_float32_set: *Set the resource value as 32-Bit float*</span></span>

- <span data-ttu-id="5ada2-153">nx_lwm2m_client_resource_float64_set: *Desaprova o valor do recurso como boia de 64 Bits*</span><span class="sxs-lookup"><span data-stu-id="5ada2-153">nx_lwm2m_client_resource_float64_set: *Set the resource value as 64-Bit float*</span></span>

- <span data-ttu-id="5ada2-154">nx_lwm2m_client_resource_boolean_set: *Desaprova o valor do recurso como boolean*</span><span class="sxs-lookup"><span data-stu-id="5ada2-154">nx_lwm2m_client_resource_boolean_set: *Set the resource value as boolean*</span></span>

- <span data-ttu-id="5ada2-155">nx_lwm2m_client_resource_objlnk_set: Definir *o valor do recurso como ligação de objeto*</span><span class="sxs-lookup"><span data-stu-id="5ada2-155">nx_lwm2m_client_resource_objlnk_set: *Set the resource value as object link*</span></span>

- <span data-ttu-id="5ada2-156">nx_lwm2m_client_resource_opaque_set: Definir *o valor do recurso como opaco*</span><span class="sxs-lookup"><span data-stu-id="5ada2-156">nx_lwm2m_client_resource_opaque_set: *Set the resource value as opaque*</span></span>

- <span data-ttu-id="5ada2-157">nx_lwm2m_client_resource_instance_set: Definir *o valor do recurso como exemplo para vários recursos*</span><span class="sxs-lookup"><span data-stu-id="5ada2-157">nx_lwm2m_client_resource_instance_set: *Set the resource value as instance for multiple resource*</span></span>
-
- <span data-ttu-id="5ada2-158">nx_lwm2m_client_resource_dim_set: *Deslote a dimensão do recurso para recursos múltiplos.*</span><span class="sxs-lookup"><span data-stu-id="5ada2-158">nx_lwm2m_client_resource_dim_set: *Set the resource dimension for multiple resource.*</span></span>

<span data-ttu-id="5ada2-159">**Informação de Recursos e Valores Obtenção:**</span><span class="sxs-lookup"><span data-stu-id="5ada2-159">**Resources Info and Values Getting:**</span></span>

- <span data-ttu-id="5ada2-160">nx_lwm2m_client_resource_info_get: Obtenha *a informação de recursos*</span><span class="sxs-lookup"><span data-stu-id="5ada2-160">nx_lwm2m_client_resource_info_get: *Get the resource info*</span></span>

- <span data-ttu-id="5ada2-161">nx_lwm2m_client_resource_string_get: Obtenha *o valor de um recurso de corda*</span><span class="sxs-lookup"><span data-stu-id="5ada2-161">nx_lwm2m_client_resource_string_get: *Get the value of a string resource*</span></span>

- <span data-ttu-id="5ada2-162">nx_lwm2m_client_resource_integer32_get: Obtenha *o valor de um recurso inteiro de 32 Bits*</span><span class="sxs-lookup"><span data-stu-id="5ada2-162">nx_lwm2m_client_resource_integer32_get: *Get the value of a 32-Bit integer resource*</span></span>

- <span data-ttu-id="5ada2-163">nx_lwm2m_client_resource_integer64_get: *Obtenha o valor de um recurso inteiro de 64 Bits*</span><span class="sxs-lookup"><span data-stu-id="5ada2-163">nx_lwm2m_client_resource_integer64_get: *Get the value of a 64-Bit integer resource*</span></span>

- <span data-ttu-id="5ada2-164">nx_lwm2m_client_resource_float32_get: Obtenha *o valor de um recurso flutuante de 32 Bits*</span><span class="sxs-lookup"><span data-stu-id="5ada2-164">nx_lwm2m_client_resource_float32_get: *Get the value of a 32-Bit float resource*</span></span>

- <span data-ttu-id="5ada2-165">nx_lwm2m_client_resource_float64_get: *Obtenha o valor de um recurso flutuante de 64 Bits*</span><span class="sxs-lookup"><span data-stu-id="5ada2-165">nx_lwm2m_client_resource_float64_get: *Get the value of a 64-Bit float resource*</span></span>

- <span data-ttu-id="5ada2-166">nx_lwm2m_client_resource_boolean_get: *Obtenha o valor de um recurso booleano*</span><span class="sxs-lookup"><span data-stu-id="5ada2-166">nx_lwm2m_client_resource_boolean_get: *Get the value of a boolean resource*</span></span>

- <span data-ttu-id="5ada2-167">nx_lwm2m_client_resource_objlnk_get: Obtenha *o valor de um recurso de ligação de objeto*</span><span class="sxs-lookup"><span data-stu-id="5ada2-167">nx_lwm2m_client_resource_objlnk_get: *Get the value of an object link resource*</span></span>

- <span data-ttu-id="5ada2-168">nx_lwm2m_client_resource_opaque_get: Obtenha *o valor de um recurso opaco*</span><span class="sxs-lookup"><span data-stu-id="5ada2-168">nx_lwm2m_client_resource_opaque_get: *Get the value of an opaque resource*</span></span>

- <span data-ttu-id="5ada2-169">nx_lwm2m_client_resource_instance_get: Obtenha *a instância de recursos para vários recursos*</span><span class="sxs-lookup"><span data-stu-id="5ada2-169">nx_lwm2m_client_resource_instance_get: *Get the resource instance for multiple resource*</span></span>

- <span data-ttu-id="5ada2-170">nx_lwm2m_client_resource_dim_get: Obtenha *a dimensão do recurso para recursos múltiplos.*</span><span class="sxs-lookup"><span data-stu-id="5ada2-170">nx_lwm2m_client_resource_dim_get: *Get the resource dimension for multiple resource.*</span></span>

## <a name="nx_lwm2m_client_create"></a><span data-ttu-id="5ada2-171">nx_lwm2m_client_create</span><span class="sxs-lookup"><span data-stu-id="5ada2-171">nx_lwm2m_client_create</span></span>

<span data-ttu-id="5ada2-172">Cria um cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-172">Creates a LWM2M client.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-173">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-173">Prototype</span></span>

```C
UINT nx_lwm2m_client_create(
    NX_LWM2M_CLIENT client_ptr,
    NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    const CHAR *name_ptr,
    UINT name_length,
    const CHAR *msisdn_ptr,
    UINT msisdn_length,
    UCHAR binding_modes,
    VOID *stack_ptr,
    ULONG stack_size,
    UINT priority);
```

### <a name="description"></a><span data-ttu-id="5ada2-174">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-174">Description</span></span>

<span data-ttu-id="5ada2-175">Este serviço cria uma instância de cliente LWM2M, que funciona no contexto da sua própria linha ThreadX.</span><span class="sxs-lookup"><span data-stu-id="5ada2-175">This service creates a LWM2M Client instance, which runs in the context of its own ThreadX thread.</span></span>

<span data-ttu-id="5ada2-176">O Cliente LWM2M implementa os seguintes objetos OMA LWM2M: Segurança (0), Servidor (1), Controlo de Acesso (2) e Dispositivo (3).</span><span class="sxs-lookup"><span data-stu-id="5ada2-176">The LWM2M Client implements the following OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="5ada2-177">As implementações dos outros objetos devem ser adicionadas pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="5ada2-177">The other objects implementations must be added by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-178">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-178">Parameters</span></span>

- <span data-ttu-id="5ada2-179">**client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-179">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="5ada2-180">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="5ada2-180">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="5ada2-181">**packet_pool_ptr** Ponteiro para a piscina de pacotes predefinidos para este Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-181">**packet_pool_ptr** Pointer to the default packet pool for this LWM2M Client.</span></span>
- <span data-ttu-id="5ada2-182">**name_ptr** Ponteiro para o nome do ponto final do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-182">**name_ptr** Pointer to LWM2M Client endpoint name.</span></span>
- <span data-ttu-id="5ada2-183">**name_length** Comprimento do nome do ponto final do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-183">**name_length** Length of LWM2M Client endpoint name.</span></span>
- <span data-ttu-id="5ada2-184">**msisdn_ptr** O ponteiro para o MSISDN onde o Cliente LWM2M pode ser contactado para ser utilizado com a ligação SMS, pode ser NULO se a ligação SMS não for suportada.</span><span class="sxs-lookup"><span data-stu-id="5ada2-184">**msisdn_ptr** Pointer to the MSISDN where the LWM2M Client can be reached for use with the SMS binding, can be NULL if SMS binding is not supported.</span></span>
- <span data-ttu-id="5ada2-185">**msisdn_length** Comprimento do número MSISDN.</span><span class="sxs-lookup"><span data-stu-id="5ada2-185">**msisdn_length** Length of MSISDN number.</span></span>
- <span data-ttu-id="5ada2-186">**binding_modes** A encadernação e os modos suportados pelo Cliente LWM2M devem ser uma combinação de NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S e bandeiras NX_LWM2M_BINDING_SQ.</span><span class="sxs-lookup"><span data-stu-id="5ada2-186">**binding_modes** The binding and modes supported by the LWM2M Client, must be a combination of NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S and NX_LWM2M_BINDING_SQ flags.</span></span>
- <span data-ttu-id="5ada2-187">**stack_ptr** Ponteiro para a área de pilha de fio do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-187">**stack_ptr** Pointer to LWM2M Client thread stack area.</span></span>
- <span data-ttu-id="5ada2-188">**stack_size** O tamanho da pilha de fio do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-188">**stack_size** The LWM2M Client thread stack size.</span></span>
- <span data-ttu-id="5ada2-189">**prioridade** Prioridade do Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-189">**priority** Priority of LWM2M Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-190">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-190">Return Values</span></span>

- <span data-ttu-id="5ada2-191">**NX_SUCCESS** O Cliente LWM2M foi criado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-191">**NX_SUCCESS** The LWM2M Client has been successfully created.</span></span>
- <span data-ttu-id="5ada2-192">**NX_LWM2M_CLIENT_ERROR** O Cliente LWM2M cria erro.</span><span class="sxs-lookup"><span data-stu-id="5ada2-192">**NX_LWM2M_CLIENT_ERROR** LWM2M Client create error.</span></span>
- <span data-ttu-id="5ada2-193">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** A porta não está disponível.</span><span class="sxs-lookup"><span data-stu-id="5ada2-193">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="5ada2-194">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-194">**NX_PTR_ERROR** Invalid pointer.</span></span>
- <span data-ttu-id="5ada2-195">**NX_SIZE_ERROR** Tamanho da pilha inválida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-195">**NX_SIZE_ERROR** Invalid stack size.</span></span>
- <span data-ttu-id="5ada2-196">**NX_OPTION_ERROR** Prioridade inválida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-196">**NX_OPTION_ERROR** Invalid priority.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-197">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-197">Allowed From</span></span>

<span data-ttu-id="5ada2-198">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-198">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-199">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-199">Example</span></span>

```C
/* Create LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client, &ip_0, &pool_0, 
  "netxlwm2mclient", sizeof("netxlwm2mclient") - 1,           
                                NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, 
                                stack_ptr, stack_size, priority);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully created.  */
```

## <a name="nx_lwm2m_client_delete"></a><span data-ttu-id="5ada2-200">nx_lwm2m_client_delete</span><span class="sxs-lookup"><span data-stu-id="5ada2-200">nx_lwm2m_client_delete</span></span>

<span data-ttu-id="5ada2-201">Elimina um Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-201">Deletes a LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-202">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-202">Prototype</span></span>

```C
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="5ada2-203">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-203">Description</span></span>

<span data-ttu-id="5ada2-204">Este serviço elimina uma instância de cliente LWM2M anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="5ada2-204">This service deletes a previously created LWM2M Client instance.</span></span>

<span data-ttu-id="5ada2-205">Todas as sessões atualmente anexadas ao cliente também são eliminadas por esta chamada.</span><span class="sxs-lookup"><span data-stu-id="5ada2-205">All sessions currently attached the client are also deleted by this call.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-206">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-206">Parameters</span></span>

- <span data-ttu-id="5ada2-207">**client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-207">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-208">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-208">Return Values</span></span>

- <span data-ttu-id="5ada2-209">**NX_SUCCESS** O Cliente LWM2M foi eliminado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-209">**NX_SUCCESS** The LWM2M Client has been successfully deleted.</span></span>
- <span data-ttu-id="5ada2-210">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-210">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-211">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-211">Allowed From</span></span>

<span data-ttu-id="5ada2-212">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-212">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-213">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-213">Example</span></span>

```c
/* Delete the LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_device_callback_set"></a><span data-ttu-id="5ada2-214">nx_lwm2m_client_device_callback_set</span><span class="sxs-lookup"><span data-stu-id="5ada2-214">nx_lwm2m_client_device_callback_set</span></span>

<span data-ttu-id="5ada2-215">Define a chamada de aplicação de um objeto do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5ada2-215">Sets a device object's application callback.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-216">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-216">Prototype</span></span>

```C
UINT **nx_lwm2m_client_device_callback_set**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_OPERATION_CALLBACK operation_callback);
```

### <a name="description"></a><span data-ttu-id="5ada2-217">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-217">Description</span></span>

<span data-ttu-id="5ada2-218">Este serviço instala a chamada de aplicação para implementação de operações nos recursos do Objeto de Dispositivo LWM2M que não são tratados pelo Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-218">This service installs the application callback for implementing operations on the LWM2M Device Object resources that are not handled by the LWM2M Client.</span></span>

<span data-ttu-id="5ada2-219">O Cliente LWM2M implementa os seguintes recursos: Código de Erro (11), Código de Erro de Reset (12) e Ligação e Modos Suportados (16), as operações para os outros recursos são redirecionadas para a aplicação.</span><span class="sxs-lookup"><span data-stu-id="5ada2-219">The LWM2M Client implements the following resources: Error Code (11), Reset Error Code (12) and Supported Binding and Modes (16), operations to the other resources are redirected to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-220">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-220">Parameters</span></span>

- <span data-ttu-id="5ada2-221">**client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-221">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="5ada2-222">**operation_callback** A operação de chamada para "Ler", "Descobrir", "Escrever" e "Executar".</span><span class="sxs-lookup"><span data-stu-id="5ada2-222">**operation_callback** The operation callback for “Read”, “Discover”, “Write” and “Execute”.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-223">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-223">Return Values</span></span>

- <span data-ttu-id="5ada2-224">**NX_SUCCESS** A chamada de operação foi definida com sucesso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-224">**NX_SUCCESS** The operation callback has been successfully set.</span></span>
- <span data-ttu-id="5ada2-225">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-225">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-226">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-226">Allowed From</span></span>

<span data-ttu-id="5ada2-227">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-227">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-228">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-228">Example</span></span>

```c
/* Set device callback.  */
status = nx_lwm2m_client_device_callback_set(&lwm2m_client, device_operation);

/* If status is NX_SUCCESS a device callback was successfully set.  */
```

## <a name="nx_lwm2m_client_device_error_push"></a><span data-ttu-id="5ada2-229">nx_lwm2m_client_device_error_push</span><span class="sxs-lookup"><span data-stu-id="5ada2-229">nx_lwm2m_client_device_error_push</span></span>
<span data-ttu-id="5ada2-230">Adiciona um código de erro a um objeto do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5ada2-230">Adds an error code to a device object.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-231">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-231">Prototype</span></span>

```C
UINT **nx_lwm2m_client_device_error_push**(
    NX_LWM2M_CLIENT *client_ptr,
    UCHAR code);
```

### <a name="description"></a><span data-ttu-id="5ada2-232">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-232">Description</span></span>

<span data-ttu-id="5ada2-233">Este serviço adiciona uma nova instância ao recurso Error Code (11) do Dispositivo Objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-233">This service adds a new instance to the Error Code (11) resource of the Object Device.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-234">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-234">Parameters</span></span>

- <span data-ttu-id="5ada2-235">**client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-235">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="5ada2-236">**código** O novo código de erro.</span><span class="sxs-lookup"><span data-stu-id="5ada2-236">**code** The new error code.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-237">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-237">Return Values</span></span>

- <span data-ttu-id="5ada2-238">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-238">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-239">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**</span><span class="sxs-lookup"><span data-stu-id="5ada2-239">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**</span></span>

<span data-ttu-id="5ada2-240">O número máximo de códigos de erro armazenados tem</span><span class="sxs-lookup"><span data-stu-id="5ada2-240">The maximum number of stored error codes has</span></span>

<span data-ttu-id="5ada2-241">foi alcançado.</span><span class="sxs-lookup"><span data-stu-id="5ada2-241">been reached.</span></span>

<span data-ttu-id="5ada2-242">NX_PTR_ERROR ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-242">NX_PTR_ERROR Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-243">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-243">Allowed From</span></span>

<span data-ttu-id="5ada2-244">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-244">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-245">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-245">Example</span></span>

```C
/* Push device error 1 (Low battery power) to server.  */
status = nx_lwm2m_client_device_error_push(&lwm2m_client, 1);

/* If status is NX_SUCCESS a device error was successfully pushed.  */
```

## <a name="nx_lwm2m_client_device_error_reset"></a><span data-ttu-id="5ada2-246">nx_lwm2m_client_device_error_reset</span><span class="sxs-lookup"><span data-stu-id="5ada2-246">nx_lwm2m_client_device_error_reset</span></span>

<span data-ttu-id="5ada2-247">Reinicia os códigos de erro do Objeto do Dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5ada2-247">Resets the error codes of Device Object.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-248">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-248">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="5ada2-249">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-249">Description</span></span>

<span data-ttu-id="5ada2-250">Este serviço elimina todas as instâncias de código de erro do Objeto do Dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5ada2-250">This service deletes all error code resource instances from the Device Object.</span></span> <span data-ttu-id="5ada2-251">Isto equivale a executar o código de erro de reposição de recursos (12).</span><span class="sxs-lookup"><span data-stu-id="5ada2-251">This is equivalent to executing the resource Reset Error Code (12).</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-252">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-252">Parameters</span></span>

- <span data-ttu-id="5ada2-253">**client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-253">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-254">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-254">Return Values</span></span>

- <span data-ttu-id="5ada2-255">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-255">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-256">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-256">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-257">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-257">Allowed From</span></span>

<span data-ttu-id="5ada2-258">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-258">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-259">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-259">Example</span></span>

```c
/* Delete all device error code.  */
status = nx_lwm2m_client_device_error_reset(&lwm2m_client);

/* If status is NX_SUCCESS, reset device error successfully.  */
```

## <a name="nx_lwm2m_client_device_resource_changed"></a><span data-ttu-id="5ada2-260">nx_lwm2m_client_device_resource_changed</span><span class="sxs-lookup"><span data-stu-id="5ada2-260">nx_lwm2m_client_device_resource_changed</span></span>

<span data-ttu-id="5ada2-261">Sinaliza uma alteração para um recurso de objeto de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5ada2-261">Signals a change to a Device Object resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-262">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-262">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_resource_changed(
    NX_LWM2M_CLIENT *client_ptr, 
    const NX_LWM2M_RESOURCE *resource);

```

### <a name="description"></a><span data-ttu-id="5ada2-263">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-263">Description</span></span>

<span data-ttu-id="5ada2-264">O serviço é utilizado pela aplicação para sinalizar ao Cliente LWM2M que um recurso do Dispositivo De Objeto mudou.</span><span class="sxs-lookup"><span data-stu-id="5ada2-264">The service is used by the application to signal to the LWM2M Client that a resource of the Object Device has changed.</span></span> <span data-ttu-id="5ada2-265">O Cliente LWM2M enviará uma notificação se o recurso for observado por um Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-265">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-266">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-266">Parameters</span></span>

- <span data-ttu-id="5ada2-267">**client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-267">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="5ada2-268">**recurso** Ponteiro para a estrutura descrevendo o recurso que mudou.</span><span class="sxs-lookup"><span data-stu-id="5ada2-268">**resource** Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-269">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-269">Return Values</span></span>

- <span data-ttu-id="5ada2-270">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-270">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-271">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-271">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-272">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-272">Allowed From</span></span>

<span data-ttu-id="5ada2-273">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-273">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-274">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-274">Example</span></span>

```c
/* Change device resource.  */
status = nx_lwm2m_client_device_resource_changed(&lwm2m_client, &resource);

/* If status is NX_SUCCESS, a device resource was successfully changed.  */
```

##  <a name="nx_lwm2m_client_firmware_create"></a><span data-ttu-id="5ada2-275">nx_lwm2m_client_firmware_create</span><span class="sxs-lookup"><span data-stu-id="5ada2-275">nx_lwm2m_client_firmware_create</span></span>

<span data-ttu-id="5ada2-276">Crie um objeto de firmware de cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-276">Create a LWM2M Client Firmware Object.</span></span> 

### <a name="prototype"></a><span data-ttu-id="5ada2-277">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-277">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_create(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    NX_LWM2M_CLIENT *client_ptr, 
    UINT protocols,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK update_callback);
```

### <a name="description"></a><span data-ttu-id="5ada2-278">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-278">Description</span></span>

<span data-ttu-id="5ada2-279">O serviço é utilizado pela aplicação para criar objeto firmware.</span><span class="sxs-lookup"><span data-stu-id="5ada2-279">The service is used by the application to create firmware object.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-280">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-280">Parameters</span></span>

- <span data-ttu-id="5ada2-281">**firmware_ptr** Ponteiro para o objeto LWM2M Client Firmware.</span><span class="sxs-lookup"><span data-stu-id="5ada2-281">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="5ada2-282">**client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-282">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="5ada2-283">**protocolos** Os protocolos apoiados.</span><span class="sxs-lookup"><span data-stu-id="5ada2-283">**protocols** The supported protocols.</span></span>
- <span data-ttu-id="5ada2-284">**package_callback** A chamada do pacote.</span><span class="sxs-lookup"><span data-stu-id="5ada2-284">**package_callback** The package callback.</span></span>
- <span data-ttu-id="5ada2-285">**package_uri_callback** O pacote uri callback.</span><span class="sxs-lookup"><span data-stu-id="5ada2-285">**package_uri_callback** The package URI callback.</span></span>
- <span data-ttu-id="5ada2-286">**update_callback** A chamada de atualização.</span><span class="sxs-lookup"><span data-stu-id="5ada2-286">**update_callback** The update callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-287">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-287">Return Values</span></span>

<span data-ttu-id="5ada2-288">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-288">**NX_SUCCESS** Successful operation.</span></span>
<span data-ttu-id="5ada2-289">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-289">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-290">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-290">Allowed From</span></span>

<span data-ttu-id="5ada2-291">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-291">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-292">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-292">Example</span></span>

```c
/* Create firmware object.  */
status = nx_lwm2m_client_firmware_create(&firmware, &lwm2m_client,     
                                         NX_LWM2M_CLIENT_FIRMWARE_PROTOCOL_HTTP, 
                                         NX_NULL, firmware_packet_uri,
                                         firmware_update);

/* If status is NX_SUCCESS, firmware object was successfully created.  */
```

##  <a name="nx_lwm2m_client_firmware_package_info_set"></a><span data-ttu-id="5ada2-293">nx_lwm2m_client_firmware_package_info_set</span><span class="sxs-lookup"><span data-stu-id="5ada2-293">nx_lwm2m_client_firmware_package_info_set</span></span>

<span data-ttu-id="5ada2-294">Define as informações do pacote LWM2M Client Firmware.</span><span class="sxs-lookup"><span data-stu-id="5ada2-294">Sets the LWM2M Client Firmware package information.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-295">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-295">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_package_info_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    const CHAR *name, 
    UINT name_length, 
    const CHAR *version, 
    UINT version_length);
```

### <a name="description"></a><span data-ttu-id="5ada2-296">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-296">Description</span></span>

<span data-ttu-id="5ada2-297">O serviço é utilizado pela aplicação para definir os recursos de informação do pacote do objeto de atualização do firmware.</span><span class="sxs-lookup"><span data-stu-id="5ada2-297">The service is used by the application to set the package information resources of the firmware update object.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-298">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-298">Parameters</span></span>

- <span data-ttu-id="5ada2-299">**firmware_ptr** Ponteiro para o objeto LWM2M Client Firmware.</span><span class="sxs-lookup"><span data-stu-id="5ada2-299">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="5ada2-300">**nome** O nome do pacote firmware.</span><span class="sxs-lookup"><span data-stu-id="5ada2-300">**name** The name of firmware package.</span></span>
- <span data-ttu-id="5ada2-301">**name_length** O comprimento do nome.</span><span class="sxs-lookup"><span data-stu-id="5ada2-301">**name_length** The length of name.</span></span>
- <span data-ttu-id="5ada2-302">**versão** A versão do pacote firmware.</span><span class="sxs-lookup"><span data-stu-id="5ada2-302">**version** The version of firmware package.</span></span>
- <span data-ttu-id="5ada2-303">**version_length** O comprimento da versão.</span><span class="sxs-lookup"><span data-stu-id="5ada2-303">**version_length** The length of version.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-304">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-304">Return Values</span></span>

- <span data-ttu-id="5ada2-305">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-305">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-306">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-306">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-307">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-307">Allowed From</span></span>

<span data-ttu-id="5ada2-308">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-308">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-309">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-309">Example</span></span>

```c
/* Set the package information resources of the firmware object.  */
status = nx_lwm2m_client_firmware_package_info_set(&firmware, 2m_client,     
                                    “LWM2M Firmware”, sizeof(“LWM2M Firmware”) -1,
                                    “1.0.0.0”, sizeof(“1.0.0.0”) - 1);

/* If status is NX_SUCCESS, package information resources was successfully set. */
```

##  <a name="nx_lwm2m_client_firmware_result_set"></a><span data-ttu-id="5ada2-310">nx_lwm2m_client_firmware_result_set</span><span class="sxs-lookup"><span data-stu-id="5ada2-310">nx_lwm2m_client_firmware_result_set</span></span>

<span data-ttu-id="5ada2-311">Define o recurso de resultado de atualização do objeto de atualização do firmware.</span><span class="sxs-lookup"><span data-stu-id="5ada2-311">Sets the update result resource of the firmware update object.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-312">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-312">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_result_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a><span data-ttu-id="5ada2-313">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-313">Description</span></span>

<span data-ttu-id="5ada2-314">O serviço é utilizado pela aplicação para definir o recurso de resultado de atualização do objeto de atualização do firmware.</span><span class="sxs-lookup"><span data-stu-id="5ada2-314">The service is used by the application to set the update result resource of the firmware update object.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-315">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-315">Parameters</span></span>

- <span data-ttu-id="5ada2-316">**firmware_ptr** Ponteiro para o objeto LWM2M Client Firmware.</span><span class="sxs-lookup"><span data-stu-id="5ada2-316">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="5ada2-317">**resultado** O resultado da atualização.</span><span class="sxs-lookup"><span data-stu-id="5ada2-317">**result** The update result.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-318">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-318">Return Values</span></span>

- <span data-ttu-id="5ada2-319">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-319">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-320">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-320">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-321">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-321">Allowed From</span></span>

<span data-ttu-id="5ada2-322">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-322">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-323">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-323">Example</span></span>

```c
/* Set the update result resource of the firmware object.  */
status = nx_lwm2m_client_firmware_result_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_RESULT_SUCCESS);

/* If status is NX_SUCCESS, the update result resource was successfully set.  */
```

##  <a name="nx_lwm2m_client_firmware_state_set"></a><span data-ttu-id="5ada2-324">nx_lwm2m_client_firmware_state_set</span><span class="sxs-lookup"><span data-stu-id="5ada2-324">nx_lwm2m_client_firmware_state_set</span></span>

<span data-ttu-id="5ada2-325">Define o recurso de resultado de atualização do objeto de atualização do firmware.</span><span class="sxs-lookup"><span data-stu-id="5ada2-325">Sets the update result resource of the firmware update object.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-326">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-326">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_state_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a><span data-ttu-id="5ada2-327">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-327">Description</span></span>

<span data-ttu-id="5ada2-328">O serviço é utilizado pela aplicação para definir o estado do objeto de atualização do firmware.</span><span class="sxs-lookup"><span data-stu-id="5ada2-328">The service is used by the application to set the state of the firmware update object.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-329">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-329">Parameters</span></span>

- <span data-ttu-id="5ada2-330">**firmware_ptr** Ponteiro para o objeto LWM2M Client Firmware.</span><span class="sxs-lookup"><span data-stu-id="5ada2-330">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="5ada2-331">**estado** O estado do objeto do firmware.</span><span class="sxs-lookup"><span data-stu-id="5ada2-331">**state** The state of the firmware object.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-332">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-332">Return Values</span></span>

- <span data-ttu-id="5ada2-333">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-333">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-334">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-334">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-335">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-335">Allowed From</span></span>

<span data-ttu-id="5ada2-336">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-336">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-337">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-337">Example</span></span>

```c
/* Set the state of the firmware object.  */
status = nx_lwm2m_client_firmware_state_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_STATE_IDLE);

/* If status is NX_SUCCESS, the state was successfully set.  */
```

## <a name="nx_lwm2m_client_lock"></a><span data-ttu-id="5ada2-338">nx_lwm2m_client_lock</span><span class="sxs-lookup"><span data-stu-id="5ada2-338">nx_lwm2m_client_lock</span></span>

<span data-ttu-id="5ada2-339">Bloqueia o Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-339">Locks the LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-340">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-340">Prototype</span></span>

```c
UINT **nx_lwm2m_client_lock**(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="5ada2-341">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-341">Description</span></span>

<span data-ttu-id="5ada2-342">Este serviço bloqueia o Cliente LWM2M para evitar o acesso simultâneo aos objetos LWM2M dos servidores ou de outro fio de aplicação.</span><span class="sxs-lookup"><span data-stu-id="5ada2-342">This service locks the LWM2M Client to prevent concurrent access to the LWM2M objects from the servers or another application thread.</span></span>

<span data-ttu-id="5ada2-343">Se o Cliente LWM2M estiver atualmente bloqueado por outro fio, a função bloqueará até que o Cliente LWM2M seja desbloqueado.</span><span class="sxs-lookup"><span data-stu-id="5ada2-343">If the LWM2M Client is currently locked by another thread, the function will block until the LWM2M Client is unlocked.</span></span>

<span data-ttu-id="5ada2-344">As chamadaspara os pares _/_ *_nx_lwm2m_client_lock nx_lwm2m_client_unlock_*\* podem ser aninhadas.</span><span class="sxs-lookup"><span data-stu-id="5ada2-344">Calls to \***nx_lwm2m_client_lock**_/_*_nx_lwm2m_client_unlock_*\* pairs can be nested.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-345">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-345">Parameters</span></span>

- <span data-ttu-id="5ada2-346">**client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-346">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-347">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-347">Return Values</span></span>

- <span data-ttu-id="5ada2-348">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-348">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-349">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-349">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-350">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-350">Allowed From</span></span>

<span data-ttu-id="5ada2-351">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-351">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-352">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-352">Example</span></span>

```c
/* Lock the LWM2M client.  */
status = nx_lwm2m_client_lock(&lwm2m_client);

/* If status is NX_SUCCESS, lwm2m client was successfully locked.  */
```

## <a name="nx_lwm2m_client_object_add"></a><span data-ttu-id="5ada2-353">nx_lwm2m_client_object_add</span><span class="sxs-lookup"><span data-stu-id="5ada2-353">nx_lwm2m_client_object_add</span></span>

<span data-ttu-id="5ada2-354">Adiciona uma implementação de objeto ao Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-354">Adds an Object implementation to the LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-355">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-355">Prototype</span></span>

```c
UINT **nx_lwm2m_client_object_add**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK object_operation);
```

### <a name="description"></a><span data-ttu-id="5ada2-356">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-356">Description</span></span>

<span data-ttu-id="5ada2-357">Este serviço adiciona uma nova implementação de Objeto ao Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-357">This service adds a new Object implementation to the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-358">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-358">Parameters</span></span>

- <span data-ttu-id="5ada2-359">**client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-359">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="5ada2-360">**object_ptr** Ponteiro para a estrutura que define a implementação do Objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-360">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="5ada2-361">**object_id** O objeto identifica.</span><span class="sxs-lookup"><span data-stu-id="5ada2-361">**object_id** The object id.</span></span>
- <span data-ttu-id="5ada2-362">**object_operation** A função de retorno de operação do objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-362">**object_operation** The object operation callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-363">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-363">Return Values</span></span>

- <span data-ttu-id="5ada2-364">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-364">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-365">**NX_LWM2M_CLIENT_ALREADY_EXIST** O ID do objeto já existe.</span><span class="sxs-lookup"><span data-stu-id="5ada2-365">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="5ada2-366">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-366">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-367">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-367">Allowed From</span></span>

<span data-ttu-id="5ada2-368">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-368">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-369">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-369">Example</span></span>

```c
/* Add new object to the lwm2m client.  */
status = nx_lwm2m_client_object_add(&lwm2m_client, &object, 
                                    3303, object_operation);

/* If status is NX_SUCCESS, the new object was successfully added.  */
```

## <a name="nx_lwm2m_client_object_create"></a><span data-ttu-id="5ada2-370">nx_lwm2m_client_object_create</span><span class="sxs-lookup"><span data-stu-id="5ada2-370">nx_lwm2m_client_object_create</span></span>

<span data-ttu-id="5ada2-371">Cria uma nova instância de objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-371">Creates a new Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-372">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-372">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_create(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a><span data-ttu-id="5ada2-373">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-373">Description</span></span>

<span data-ttu-id="5ada2-374">Este serviço executa uma operação 'Criar' num Objeto do Cliente LWM2M para criar uma nova Instância de Objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-374">This service performs a ‘Create’ operation on an Object of the LWM2M Client to create a new Object Instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-375">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-375">Parameters</span></span>

- <span data-ttu-id="5ada2-376">**client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-376">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="5ada2-377">**object_id** A identificação do objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-377">**object_id** The Object ID.</span></span>
- <span data-ttu-id="5ada2-378">**instance_id_ptr** O ponteiro para o ID da nova instância, pode ser **NULO** se o Cliente LWM2M tiver de atribuir um ID de instância.</span><span class="sxs-lookup"><span data-stu-id="5ada2-378">**instance_id_ptr** Pointer to the ID of the new instance, can be **NULL** if the LWM2M Client must assign an Instance ID.</span></span> <span data-ttu-id="5ada2-379">Se o ID for o valor reservado 65535, o Cliente LWM2M atribuirá um ID de instância.</span><span class="sxs-lookup"><span data-stu-id="5ada2-379">If the ID is the reserved value 65535 the LWM2M Client will assign an Instance ID.</span></span> <span data-ttu-id="5ada2-380">Se não não null, o ID atribuído é devolvido após a chamada.</span><span class="sxs-lookup"><span data-stu-id="5ada2-380">If not NULL the assigned ID is returned after the call.</span></span>
- <span data-ttu-id="5ada2-381">**num_values** O número de valores a definir.</span><span class="sxs-lookup"><span data-stu-id="5ada2-381">**num_values** The number of values to set.</span></span>
- <span data-ttu-id="5ada2-382">**values_ptr** Ponteiro para uma matriz de valores de recursos para inicializar a nova Instância de Objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-382">**values_ptr** Pointer to an array of resource values to initialize the new Object Instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-383">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-383">Return Values</span></span>

- <span data-ttu-id="5ada2-384">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-384">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-385">**NX_LWM2M_CLIENT_ALREADY_EXIST** O ID da instância do objeto já existe.</span><span class="sxs-lookup"><span data-stu-id="5ada2-385">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object Instance ID already exists.</span></span>
- <span data-ttu-id="5ada2-386">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** O Objeto não suporta a criação de exemplos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-386">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** The Object doesn’t support instance creation.</span></span>
- <span data-ttu-id="5ada2-387">**NX_LWM2M_CLIENT_NO_MEMORY** Não é possível alocar memória para armazenar o novo caso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-387">**NX_LWM2M_CLIENT_NO_MEMORY** Cannot allocate memory to store the new instance.</span></span>
- <span data-ttu-id="5ada2-388">**NX_LWM2M_CLIENT_NOT_FOUND** A identificação do objeto não existe.</span><span class="sxs-lookup"><span data-stu-id="5ada2-388">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID doesn’t exist.</span></span>
- <span data-ttu-id="5ada2-389">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-389">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-390">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-390">Allowed From</span></span>

<span data-ttu-id="5ada2-391">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-391">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-392">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-392">Example</span></span>

```c
/* Create new object instance.  */
status = nx_lwm2m_client_object_create(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, a new object instance was successfully created.  */
```

## <a name="nx_lwm2m_client_object_delete"></a><span data-ttu-id="5ada2-393">nx_lwm2m_client_object_delete</span><span class="sxs-lookup"><span data-stu-id="5ada2-393">nx_lwm2m_client_object_delete</span></span>

<span data-ttu-id="5ada2-394">Elimina uma Instância de Objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-394">Deletes an Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-395">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-395">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_delete(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a><span data-ttu-id="5ada2-396">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-396">Description</span></span>

<span data-ttu-id="5ada2-397">Este serviço executa uma operação 'Eliminar' numa Instância de Objeto do Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-397">This service performs a ‘Delete’ operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-398">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-398">Parameters</span></span>

- <span data-ttu-id="5ada2-399">**client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-399">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="5ada2-400">**object_id** A identificação do objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-400">**object_id** The Object ID.</span></span>
- <span data-ttu-id="5ada2-401">**instance_id** A identificação do caso do objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-401">**instance_id** The Object Instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-402">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-402">Return Values</span></span>

- <span data-ttu-id="5ada2-403">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-403">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-404">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** O Objeto não suporta a eliminação de exemplos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-404">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** The Object doesn’t support instance deletion.</span></span>
- <span data-ttu-id="5ada2-405">**NX_LWM2M_CLIENT_NOT_FOUND** O ID do objeto ou iD de instância de objeto não existe.</span><span class="sxs-lookup"><span data-stu-id="5ada2-405">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID or Object Instance ID doesn’t exist.</span></span>
- <span data-ttu-id="5ada2-406">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-406">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-407">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-407">Allowed From</span></span>

<span data-ttu-id="5ada2-408">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-408">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-409">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-409">Example</span></span>

```c
/* Delete an object instance.  */
status = nx_lwm2m_client_object_delete(&lwm2m_client, 3303, 0);

/* If status is NX_SUCCESS, an object instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_object_discover"></a><span data-ttu-id="5ada2-410">nx_lwm2m_client_object_discover</span><span class="sxs-lookup"><span data-stu-id="5ada2-410">nx_lwm2m_client_object_discover</span></span>

<span data-ttu-id="5ada2-411">Descobre recursos de uma Instância de Objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-411">Discovers resources of an Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-412">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-412">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_discover(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT *num_resources,
    NX_LWM2M_CLIENT_RESOURCE *resources);

```

### <a name="description"></a><span data-ttu-id="5ada2-413">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-413">Description</span></span>

<span data-ttu-id="5ada2-414">Este serviço executa uma operação 'Discover' numa Instância de Objeto do Cliente LWM2M, esta devolve a lista de recursos implementados pelo Objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-414">This service performs a ‘Discover’ operation on an Object Instance of the LWM2M Client, this returns the list of resources implemented by the Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-415">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-415">Parameters</span></span>

- <span data-ttu-id="5ada2-416">**client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-416">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="5ada2-417">**object_id** A identificação do objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-417">**object_id** The Object ID.</span></span>
- <span data-ttu-id="5ada2-418">**instance_id** A identificação do caso do objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-418">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="5ada2-419">**num_resources** Na entrada do tamanho do tampão de destino, na saída o número de elementos escritos no tampão.</span><span class="sxs-lookup"><span data-stu-id="5ada2-419">**num_resources** On input the size of the destination buffer, on output the number of elements written to the buffer.</span></span>
- <span data-ttu-id="5ada2-420">**recursos** Ponteiro para o tampão de destino.</span><span class="sxs-lookup"><span data-stu-id="5ada2-420">**resources** Pointer to the destination buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-421">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-421">Return Values</span></span>

- <span data-ttu-id="5ada2-422">*NX_SUCCESS* operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-422">*NX_SUCCESS*\* Successful operation.</span></span>
- <span data-ttu-id="5ada2-423">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** O amortecedor de recursos é muito pequeno para armazenar a lista de recursos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-423">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** The resources buffer is too small to store the list of resources.</span></span>
- <span data-ttu-id="5ada2-424">**NX_LWM2M_CLIENT_NOT_FOUND** O ID do objeto ou iD de instância de objeto não existe.</span><span class="sxs-lookup"><span data-stu-id="5ada2-424">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID or Object Instance ID doesn’t exist.</span></span>
- <span data-ttu-id="5ada2-425">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-425">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-426">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-426">Allowed From</span></span>

<span data-ttu-id="5ada2-427">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-427">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-428">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-428">Example</span></span>

```c
NX_LWM2M_CLIENT_RESOURCE resources[10]
UINT num_resources = 10;

/* Discover object resources.  */
status = nx_lwm2m_client_object_discover(&lwm2m_client, 3303, 0, 
                                         &num_resources, resource);

/* If status is NX_SUCCESS, discover object resources successfully.  */
```

## <a name="nx_lwm2m_client_object_execute"></a><span data-ttu-id="5ada2-429">nx_lwm2m_client_object_execute</span><span class="sxs-lookup"><span data-stu-id="5ada2-429">nx_lwm2m_client_object_execute</span></span>

<span data-ttu-id="5ada2-430">Executa uma operação 'Executar' num recurso de uma Instância de Objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-430">Performs an 'Execute' operation on a resource of an Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-431">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-431">Prototype</span></span>

```C
UINT **nx_lwm2m_client_object_execute**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr,
    UINT arguments_length);
```

### <a name="description"></a><span data-ttu-id="5ada2-432">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-432">Description</span></span>

<span data-ttu-id="5ada2-433">Este serviço executa a operação 'Executar' num recurso de instância de objeto do Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-433">This service performs the ‘Execute’ operation on an Object Instance Resource of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-434">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-434">Parameters</span></span>

- <span data-ttu-id="5ada2-435">**client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-435">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="5ada2-436">**object_id** A identificação do objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-436">**object_id** The Object ID.</span></span>
- <span data-ttu-id="5ada2-437">**instance_id** A identificação do caso do objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-437">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="5ada2-438">**resource_id** A identificação de recursos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-438">**resource_id** The Resource ID.</span></span>
- <span data-ttu-id="5ada2-439">**arguments_ptr** Apontando para os argumentos da operação de execução.</span><span class="sxs-lookup"><span data-stu-id="5ada2-439">**arguments_ptr** Pointer to the arguments of the execute operation.</span></span> <span data-ttu-id="5ada2-440">Pode ser NULO se arguments_length for zero.</span><span class="sxs-lookup"><span data-stu-id="5ada2-440">Can be NULL if arguments_length is zero.</span></span>
- <span data-ttu-id="5ada2-441">**arguments_length** A duração dos argumentos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-441">**arguments_length** The length of the arguments.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-442">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-442">Return Values</span></span>

- <span data-ttu-id="5ada2-443">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-443">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-444">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** O amortecedor de recursos é muito pequeno para armazenar a lista de recursos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-444">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** The resources buffer is too small to store the list of resources.</span></span>
- <span data-ttu-id="5ada2-445">**NX_LWM2M_CLIENT_NOT_FOUND** O ID do objeto ou iD de instância de objeto não existe.</span><span class="sxs-lookup"><span data-stu-id="5ada2-445">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID or Object Instance ID doesn’t exist.</span></span>
- <span data-ttu-id="5ada2-446">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-446">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-447">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-447">Allowed From</span></span>

<span data-ttu-id="5ada2-448">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-448">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-449">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-449">Example</span></span>

```c
/* Execute object resource.  */
status = nx_lwm2m_client_object_execute (&lwm2m_client, 3303, 0, 0,  
                                         “5”, 1);

/* If status is NX_SUCCESS, an object resource was successfully executed.  */
```

## <a name="nx_lwm2m_client_object_instance_add"></a><span data-ttu-id="5ada2-450">nx_lwm2m_client_object_instance_add</span><span class="sxs-lookup"><span data-stu-id="5ada2-450">nx_lwm2m_client_object_instance_add</span></span>

<span data-ttu-id="5ada2-451">Adiciona uma implementação de instância de objeto a um objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-451">Adds an Object instance implementation to an object.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-452">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-452">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_add(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a><span data-ttu-id="5ada2-453">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-453">Description</span></span>

<span data-ttu-id="5ada2-454">Este serviço adiciona uma nova implementação de instância de objeto ao Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-454">This service adds a new Object instance implementation to the LWM2M Client.</span></span> <span data-ttu-id="5ada2-455">Se o valor do instance_id_ptr for **NX_LWM2M_CLIENT_RESERVED_ID**, o Cliente LWM2M atribuirá automaticamente um id de instância não utilizado, caso contrário, o Cliente LWM2M utilizará o conjunto de aplicações de valor.</span><span class="sxs-lookup"><span data-stu-id="5ada2-455">If the value of instance_id_ptr is **NX_LWM2M_CLIENT_RESERVED_ID**, LWM2M Client will automatically assign an unused instance id, otherwise, LWM2M Client will use the value application set.</span></span> <span data-ttu-id="5ada2-456">Uma vez que a nova instância foi adicionada com sucesso, o instance_id será preenchido em instance_id_ptr para voltar à aplicação.</span><span class="sxs-lookup"><span data-stu-id="5ada2-456">Once new instance was added successfully, the instance_id will be filled in instance_id_ptr to return to application.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-457">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-457">Parameters</span></span>

- <span data-ttu-id="5ada2-458">**object_ptr** Ponteiro para a estrutura que define a implementação do Objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-458">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="5ada2-459">**instance_ptr** Ponteiro para a estrutura que define a implementação do caso Objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-459">**instance_ptr** Pointer to the structure defining the Object instance implementation.</span></span>
- <span data-ttu-id="5ada2-460">**instance_id_ptr** Ponteiro para o id da instância do objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-460">**instance_id_ptr** Pointer to the object instance id.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-461">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-461">Return Values</span></span>

- <span data-ttu-id="5ada2-462">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-462">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-463">**NX_CLIENT_LWM2M_ALREADY_EXIST** O ID do objeto já existe.</span><span class="sxs-lookup"><span data-stu-id="5ada2-463">**NX_CLIENT_LWM2M_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="5ada2-464">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-464">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-465">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-465">Allowed From</span></span>

<span data-ttu-id="5ada2-466">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-466">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-467">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-467">Example</span></span>

```c
/* Add new object instance to the object.  */
status = nx_lwm2m_client_object_instance_add(&object, &object_instance,
                                             &instance_id);

/* If status is NX_SUCCESS, the new object instance was successfully added.  */
```

## <a name="nx_lwm2m_client_object_instance_next_get"></a><span data-ttu-id="5ada2-468">nx_lwm2m_client_object_instance_next_get</span><span class="sxs-lookup"><span data-stu-id="5ada2-468">nx_lwm2m_client_object_instance_next_get</span></span>

<span data-ttu-id="5ada2-469">Obtém a próxima instância de um objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-469">Gets the next instance of an Object.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-470">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-470">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a><span data-ttu-id="5ada2-471">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-471">Description</span></span>

<span data-ttu-id="5ada2-472">Este serviço devolve o ID da próxima Instância de Objeto do Objeto dado.</span><span class="sxs-lookup"><span data-stu-id="5ada2-472">This service returns the ID of the next Object Instance of the given Object.</span></span> <span data-ttu-id="5ada2-473">Se o ID de instância atual estiver definido para NX_LWM2M_RESERVED_ID (65535) o ID da primeira instância é devolvido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-473">If the current Instance ID is set to NX_LWM2M_RESERVED_ID (65535) the ID of the first instance is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-474">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-474">Parameters</span></span>

- <span data-ttu-id="5ada2-475">**client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-475">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="5ada2-476">**object_id** A identificação do objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-476">**object_id** The Object ID.</span></span>
- <span data-ttu-id="5ada2-477">**instance_id_ptr** Ponteiro para o ID de instância de objeto atual.</span><span class="sxs-lookup"><span data-stu-id="5ada2-477">**instance_id_ptr** Pointer to the current Object Instance ID.</span></span> <span data-ttu-id="5ada2-478">No retorno contém o próximo ID de instância do objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-478">On return contains the next Instance ID of the Object.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-479">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-479">Return Values</span></span>

- <span data-ttu-id="5ada2-480">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-480">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-481">**NX_CLIENT_LWM2M_NOT_FOUND** O ID de instância dado é o último do objeto, ou o ID do objeto não é implementado.</span><span class="sxs-lookup"><span data-stu-id="5ada2-481">**NX_CLIENT_LWM2M_NOT_FOUND** The given Instance ID is the last of the object, or the Object ID is not implemented.</span></span>
- <span data-ttu-id="5ada2-482">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-482">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-483">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-483">Allowed From</span></span>

<span data-ttu-id="5ada2-484">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-484">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-485">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-485">Example</span></span>

```c
/* Get the next instance of an object.  */
status = nx_lwm2m_client_object_instance_next_get(&lwm2m_client, 3303, 
                                                  &instance_id);

/* If status is NX_SUCCESS, get the next instance successfully.  */
```

## <a name="nx_lwm2m_client_object_instance_remove"></a><span data-ttu-id="5ada2-486">nx_lwm2m_client_object_instance_remove</span><span class="sxs-lookup"><span data-stu-id="5ada2-486">nx_lwm2m_client_object_instance_remove</span></span>

<span data-ttu-id="5ada2-487">Remove a implementação de uma instância de objeto de um objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-487">Removes an  Object instance implementation from an object.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-488">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-488">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_remove(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr);
```

### <a name="description"></a><span data-ttu-id="5ada2-489">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-489">Description</span></span>

<span data-ttu-id="5ada2-490">Este serviço remove uma instância de objeto de um objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-490">This service removes an Object instance from an object.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-491">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-491">Parameters</span></span>

- <span data-ttu-id="5ada2-492">***object_ptr*** Ponteiro para a estrutura que define a implementação do Objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-492">***object_ptr*** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="5ada2-493">**instance_ptr** Ponteiro para a estrutura que define a implementação do caso Objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-493">**instance_ptr** Pointer to the structure defining the Object instance implementation.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-494">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-494">Return Values</span></span>

- <span data-ttu-id="5ada2-495">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-495">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-496">**NX_LWM2M_CLIENT_ALREADY_EXIST** O ID do objeto já existe.</span><span class="sxs-lookup"><span data-stu-id="5ada2-496">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="5ada2-497">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-497">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-498">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-498">Allowed From</span></span>

<span data-ttu-id="5ada2-499">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-499">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-500">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-500">Example</span></span>

```c
/* Remove object instance from an object.  */
status = nx_lwm2m_client_object_instance_remove(&object, &object_instance);

/* If status is NX_SUCCESS, the object instance was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_next_get"></a><span data-ttu-id="5ada2-501">nx_lwm2m_client_object_next_get</span><span class="sxs-lookup"><span data-stu-id="5ada2-501">nx_lwm2m_client_object_next_get</span></span>

<span data-ttu-id="5ada2-502">Obtém o próximo objeto do Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-502">Gets the next object of the LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-503">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-503">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID \*object_id_ptr);
```

### <a name="description"></a><span data-ttu-id="5ada2-504">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-504">Description</span></span>

<span data-ttu-id="5ada2-505">Este serviço devolve o ID do próximo Objeto implementado pelo Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-505">This service returns the ID of the next Object implemented by the LWM2M Client.</span></span> <span data-ttu-id="5ada2-506">Se o ID do objeto atual estiver definido para NX_LWM2M_RESERVED_ID (65535) o primeiro ID do objeto é devolvido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-506">If the current Object ID is set to NX_LWM2M_RESERVED_ID (65535) the first Object ID is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-507">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-507">Parameters</span></span>

- <span data-ttu-id="5ada2-508">**client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-508">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="5ada2-509">**object_id_ptr** Ponteiro para o ID do objeto atual.</span><span class="sxs-lookup"><span data-stu-id="5ada2-509">**object_id_ptr** Pointer to the current Object ID.</span></span> <span data-ttu-id="5ada2-510">Na devolução contém o próximo ID do Objeto implementado pelo Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-510">On return contains the next Object ID implemented by the LWM2M Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-511">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-511">Return Values</span></span>

- <span data-ttu-id="5ada2-512">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-512">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-513">**NX_LWM2M_CLIENT_NOT_FOUND** O ID dado objeto é o último da base de dados.</span><span class="sxs-lookup"><span data-stu-id="5ada2-513">**NX_LWM2M_CLIENT_NOT_FOUND** The given Object ID is the last of the database.</span></span>
<span data-ttu-id="5ada2-514">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-514">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-515">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-515">Allowed From</span></span>

<span data-ttu-id="5ada2-516">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-516">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-517">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-517">Example</span></span>

```c
/* Get the next object of lwm2m client.  */
status = nx_lwm2m_client_object_next_get(&lwm2m_client, &object_id);

/* If status is NX_SUCCESS, get the next object successfully.  */
```

## <a name="nx_lwm2m_client_object_read"></a><span data-ttu-id="5ada2-518">nx_lwm2m_client_object_read</span><span class="sxs-lookup"><span data-stu-id="5ada2-518">nx_lwm2m_client_object_read</span></span>

<span data-ttu-id="5ada2-519">Lê os valores dos recursos de uma instância de objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-519">Reads an Object Instance's resource's values.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-520">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-520">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_read(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a><span data-ttu-id="5ada2-521">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-521">Description</span></span>

<span data-ttu-id="5ada2-522">Este serviço executa uma operação 'Ler' numa Instância de Objeto do Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-522">This service performs a ‘Read’ operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-523">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-523">Parameters</span></span>

- <span data-ttu-id="5ada2-524">**client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-524">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="5ada2-525">**object_id** A identificação do objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-525">**object_id** The Object ID.</span></span>
- <span data-ttu-id="5ada2-526">**instance_id** A identificação do caso do objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-526">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="5ada2-527">**num_values** O número de recursos para ler.</span><span class="sxs-lookup"><span data-stu-id="5ada2-527">**num_values** The number of resources to read.</span></span>
- <span data-ttu-id="5ada2-528">**values_ptr** Ponteiro para uma série de NX_LWM2M_RESOURCE contendo as identificações dos recursos para ler.</span><span class="sxs-lookup"><span data-stu-id="5ada2-528">**values_ptr** Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources to read.</span></span> <span data-ttu-id="5ada2-529">Na volta, a matriz é preenchida com os tipos e valores correspondentes.</span><span class="sxs-lookup"><span data-stu-id="5ada2-529">On return the array is filled with the corresponding types and values.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-530">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-530">Return Values</span></span>

- <span data-ttu-id="5ada2-531">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-531">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-532">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Um recurso não suporta a operação de leitura.</span><span class="sxs-lookup"><span data-stu-id="5ada2-532">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** A resource doesn’t support the read operation.</span></span>
- <span data-ttu-id="5ada2-533">**NX_LWM2M_CLIENT_NOT_FOUND** O ID do objeto, iD de instância de objeto ou um ID de recurso não existe.</span><span class="sxs-lookup"><span data-stu-id="5ada2-533">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID, Object Instance ID or a resource ID doesn’t exist.</span></span>
- <span data-ttu-id="5ada2-534">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-534">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-535">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-535">Allowed From</span></span>

<span data-ttu-id="5ada2-536">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-536">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-537">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-537">Example</span></span>

```c
/* Read the object resources.  */
status = nx_lwm2m_client_object_read(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, the resources were successfully read.  */
```

## <a name="nx_lwm2m_client_object_remove"></a><span data-ttu-id="5ada2-538">nx_lwm2m_client_object_remove</span><span class="sxs-lookup"><span data-stu-id="5ada2-538">nx_lwm2m_client_object_remove</span></span>

<span data-ttu-id="5ada2-539">Remove a implementação de uma instância de objeto de um objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-539">Removes an Object instance implementation from an object.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-540">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-540">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_remove(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr);
```

### <a name="description"></a><span data-ttu-id="5ada2-541">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-541">Description</span></span>

<span data-ttu-id="5ada2-542">Este serviço remove um Objeto do Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-542">This service removes an Object from the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-543">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-543">Parameters</span></span>

- <span data-ttu-id="5ada2-544">**client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-544">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="5ada2-545">**object_ptr** Ponteiro para a estrutura que define a implementação do Objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-545">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-546">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-546">Return Values</span></span>

- <span data-ttu-id="5ada2-547">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-547">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-548">**NX_LWM2M_CLIENT_ALREADY_EXIST** O ID do objeto já existe.</span><span class="sxs-lookup"><span data-stu-id="5ada2-548">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="5ada2-549">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-549">**NX_PTR_ERROR** Invalid pointer.</span></span>
- <span data-ttu-id="5ada2-550">**NX_LWM2M_CLIENT_FORBIDDEN** A remoção do objeto interno é proibida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-550">**NX_LWM2M_CLIENT_FORBIDDEN** Removing internal object is forbidden.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-551">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-551">Allowed From</span></span>

<span data-ttu-id="5ada2-552">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-552">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-553">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-553">Example</span></span>

```c
/* Remove object from lwm2m client.  */
status = nx_lwm2m_client_object_remove(&lwm2m_client, &object);

/* If status is NX_SUCCESS, the object was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_resource_changed"></a><span data-ttu-id="5ada2-554">nx_lwm2m_client_object_resource_changed</span><span class="sxs-lookup"><span data-stu-id="5ada2-554">nx_lwm2m_client_object_resource_changed</span></span>

<span data-ttu-id="5ada2-555">Sinaliza uma mudança de recurso de objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-555">Signals a change of an Object resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-556">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-556">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_resource_changed(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a><span data-ttu-id="5ada2-557">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-557">Description</span></span>

<span data-ttu-id="5ada2-558">O serviço é utilizado pela aplicação para sinalizar ao Cliente LWM2M que um recurso do Objeto mudou.</span><span class="sxs-lookup"><span data-stu-id="5ada2-558">The service is used by the application to signal to the LWM2M Client that a resource of the Object has changed.</span></span> <span data-ttu-id="5ada2-559">O Cliente LWM2M enviará uma notificação se o recurso for observado por um Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-559">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-560">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-560">Parameters</span></span>

- <span data-ttu-id="5ada2-561">**object_ptr** Ponteiro para a estrutura que define a implementação do Objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-561">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="5ada2-562">***instance_ptr*** Ponteiro para a estrutura que define a implementação do caso Objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-562">***instance_ptr*** Pointer to the structure defining the Object instance implementation.</span></span>
- <span data-ttu-id="5ada2-563">**recurso** Ponteiro para a estrutura descrevendo o recurso que mudou.</span><span class="sxs-lookup"><span data-stu-id="5ada2-563">**resource** Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-564">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-564">Return Values</span></span>

- <span data-ttu-id="5ada2-565">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-565">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-566">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-566">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-567">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-567">Allowed From</span></span>

<span data-ttu-id="5ada2-568">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-568">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-569">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-569">Example</span></span>

```c
/* Change object resource.  */
status = nx_lwm2m_client_object_resource_changed(&object, &instance, &resource);

/* If status is NX_SUCCESS, a resource was successfully changed.  */
```

## <a name="nx_lwm2m_client_object_write"></a><span data-ttu-id="5ada2-570">nx_lwm2m_client_object_write</span><span class="sxs-lookup"><span data-stu-id="5ada2-570">nx_lwm2m_client_object_write</span></span>

<span data-ttu-id="5ada2-571">Altera os valores do recurso de uma instância do Objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-571">Changes resource's values of an Object instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-572">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-572">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_write(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr,
    UINT write_op);
```

### <a name="description"></a><span data-ttu-id="5ada2-573">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-573">Description</span></span>

<span data-ttu-id="5ada2-574">Este serviço executa uma operação de 'Write' numa Instância de Objeto do Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-574">This service performs a ‘Write’ operation on an Object Instance of the LWM2M Client.</span></span>

<span data-ttu-id="5ada2-575">As seguintes operações de escrita podem ser especificadas para o parâmetro *write_op.*</span><span class="sxs-lookup"><span data-stu-id="5ada2-575">The following write operations can be specified to the *write_op* parameter.</span></span>

| <span data-ttu-id="5ada2-576">Valor</span><span class="sxs-lookup"><span data-stu-id="5ada2-576">Value</span></span> | <span data-ttu-id="5ada2-577">&nbsp;Escrever Operação</span><span class="sxs-lookup"><span data-stu-id="5ada2-577">Write&nbsp;Operation</span></span> | <span data-ttu-id="5ada2-578">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-578">Description</span></span> |
| --- | ---| --- |
| <span data-ttu-id="5ada2-579">0</span><span class="sxs-lookup"><span data-stu-id="5ada2-579">0</span></span> | <span data-ttu-id="5ada2-580">Atualização Parcial</span><span class="sxs-lookup"><span data-stu-id="5ada2-580">Partial Update</span></span> | <span data-ttu-id="5ada2-581">Adiciona ou atualiza Recursos fornecidos no novo valor e deixa outros Recursos existentes inalterados.</span><span class="sxs-lookup"><span data-stu-id="5ada2-581">Adds or updates Resources provided in the new value and leaves other existing Resources unchanged.</span></span> |
| <span data-ttu-id="5ada2-582">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span><span class="sxs-lookup"><span data-stu-id="5ada2-582">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span></span> | <span data-ttu-id="5ada2-583">Substituir Instância</span><span class="sxs-lookup"><span data-stu-id="5ada2-583">Replace Instance</span></span> | <span data-ttu-id="5ada2-584">Substitui a Instância do Objeto pelos novos valores de recursos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-584">Replaces the Object Instance with the new provided resource values.</span></span> |
| <span data-ttu-id="5ada2-585">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span><span class="sxs-lookup"><span data-stu-id="5ada2-585">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span></span> | <span data-ttu-id="5ada2-586">Substituir recursos</span><span class="sxs-lookup"><span data-stu-id="5ada2-586">Replace Resource</span></span> | <span data-ttu-id="5ada2-587">Substitui os Recursos pelos novos valores de recursos fornecidos (utilizados para substituir Múltiplos Recursos).</span><span class="sxs-lookup"><span data-stu-id="5ada2-587">Replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span> |
| <span data-ttu-id="5ada2-588">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span><span class="sxs-lookup"><span data-stu-id="5ada2-588">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span></span> | <span data-ttu-id="5ada2-589">Escrita de Bootstrap</span><span class="sxs-lookup"><span data-stu-id="5ada2-589">Bootstrap Write</span></span> | <span data-ttu-id="5ada2-590">Indica uma chamada de uma sequência de Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="5ada2-590">Indicates a call from a Bootstrap sequence.</span></span> |

### <a name="parameters"></a><span data-ttu-id="5ada2-591">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-591">Parameters</span></span>

- <span data-ttu-id="5ada2-592">**client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-592">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="5ada2-593">**object_id** A identificação do objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-593">**object_id** The Object ID.</span></span>
- <span data-ttu-id="5ada2-594">**instance_id** A identificação do caso do objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-594">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="5ada2-595">**num_values** O número de recursos para escrever.</span><span class="sxs-lookup"><span data-stu-id="5ada2-595">**num_values** The number of resources to write.</span></span>
- <span data-ttu-id="5ada2-596">**values_ptr** Ponteiro para uma série de NX_LWM2M_RESOURCE contendo os IDs dos recursos, os tipos e os valores para escrever.</span><span class="sxs-lookup"><span data-stu-id="5ada2-596">**values_ptr** Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources, the types and the values to write.</span></span>
- <span data-ttu-id="5ada2-597">**write_op** O tipo de operação de escrita.</span><span class="sxs-lookup"><span data-stu-id="5ada2-597">**write_op** The type of write operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-598">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-598">Return Values</span></span>

- <span data-ttu-id="5ada2-599">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-599">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-600">**NX_LWM2M_CLIENT_BAD_ENCODING** O tipo de recurso não é válido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-600">**NX_LWM2M_CLIENT_BAD_ENCODING** The type of a resource is not valid.</span></span>
- <span data-ttu-id="5ada2-601">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** O comprimento de um valor é demasiado grande para ser armazenado no caso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-601">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** The length of a value is too big to be stored in the instance.</span></span>
- <span data-ttu-id="5ada2-602">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Um recurso não suporta a operação de escrita.</span><span class="sxs-lookup"><span data-stu-id="5ada2-602">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** A resource doesn’t support the write operation.</span></span>
- <span data-ttu-id="5ada2-603">**NX_LWM2M_CLIENT_NO_MEMORY** Não é possível alocar memória para armazenar um valor de recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-603">**NX_LWM2M_CLIENT_NO_MEMORY** Cannot allocate memory to store a resource value.</span></span>
- <span data-ttu-id="5ada2-604">**NX_LWM2M_CLIENT_NOT_ACCEPTABLE** O valor de um recurso não é válido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-604">**NX_LWM2M_CLIENT_NOT_ACCEPTABLE** The value of a resource is not valid.</span></span>
- <span data-ttu-id="5ada2-605">**NX_LWM2M_CLIENT_NOT_FOUND** O ID do objeto, iD de instância de objeto ou um ID de recurso não existe.</span><span class="sxs-lookup"><span data-stu-id="5ada2-605">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID, Object Instance ID or a resource ID doesn’t exist.</span></span>
- <span data-ttu-id="5ada2-606">**NX_OPTION_ERROR** Tipo inválido de operação de escrita.</span><span class="sxs-lookup"><span data-stu-id="5ada2-606">**NX_OPTION_ERROR** Invalid type of write operation.</span></span> 
- <span data-ttu-id="5ada2-607">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-607">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-608">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-608">Allowed From</span></span>

<span data-ttu-id="5ada2-609">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-609">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-610">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-610">Example</span></span>

```c
/* Write object resources.  */
status = nx_lwm2m_client_object_write(&lwm2m_client, 3303, 0, 2, &resource,
                                      NX_LWM2M_CLIENT_OBJECT_WRITE_UPDATE);

/* If status is NX_SUCCESS, write object resources successfully.  */
```

## <a name="nx_lwm2m_client_resource_boolean_get"></a><span data-ttu-id="5ada2-611">nx_lwm2m_client_resource_boolean_get</span><span class="sxs-lookup"><span data-stu-id="5ada2-611">nx_lwm2m_client_resource_boolean_get</span></span>

<span data-ttu-id="5ada2-612">Obtém o valor de um Recurso Boolean.</span><span class="sxs-lookup"><span data-stu-id="5ada2-612">Gets the value of a Boolean Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-613">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-613">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_boolean_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a><span data-ttu-id="5ada2-614">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-614">Description</span></span>

<span data-ttu-id="5ada2-615">O serviço recupera o valor de um Recurso Boolean.</span><span class="sxs-lookup"><span data-stu-id="5ada2-615">The service retrieves the value of a Boolean Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-616">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-616">Parameters</span></span>

- <span data-ttu-id="5ada2-617">**recurso** Ponteiro para descrição do valor do recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-617">**resource** Pointer to Resource value description.</span></span>
- <span data-ttu-id="5ada2-618">**bool_ptr** Ponteiro para o destino Valor Boolean.</span><span class="sxs-lookup"><span data-stu-id="5ada2-618">**bool_ptr** Pointer to the destination Boolean value.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-619">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-619">Return Values</span></span>

- <span data-ttu-id="5ada2-620">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-620">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-621">**NX_LWM2M_CLIENT_BAD_ENCODING** O valor do recurso não é um valor Boolean.</span><span class="sxs-lookup"><span data-stu-id="5ada2-621">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="5ada2-622">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-622">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-623">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-623">Allowed From</span></span>

<span data-ttu-id="5ada2-624">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-624">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-625">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-625">Example</span></span>

```c
/* Get the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_get(&resource, &bool);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_boolean_set"></a><span data-ttu-id="5ada2-626">nx_lwm2m_client_resource_boolean_set</span><span class="sxs-lookup"><span data-stu-id="5ada2-626">nx_lwm2m_client_resource_boolean_set</span></span>

<span data-ttu-id="5ada2-627">Define o valor de um Recurso Boolean.</span><span class="sxs-lookup"><span data-stu-id="5ada2-627">Sets the value of a Boolean Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-628">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-628">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_boolean_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL bool_data);
```

### <a name="description"></a><span data-ttu-id="5ada2-629">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-629">Description</span></span>

<span data-ttu-id="5ada2-630">O serviço define o valor de um Recurso Boolean.</span><span class="sxs-lookup"><span data-stu-id="5ada2-630">The service sets the value of a Boolean Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-631">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-631">Parameters</span></span>

- <span data-ttu-id="5ada2-632">**recurso** Ponteiro para recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-632">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="5ada2-633">**bool_data** Dados boolean.</span><span class="sxs-lookup"><span data-stu-id="5ada2-633">**bool_data** Boolean data.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-634">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-634">Return Values</span></span>

- <span data-ttu-id="5ada2-635">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-635">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-636">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-636">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-637">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-637">Allowed From</span></span>

<span data-ttu-id="5ada2-638">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-638">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-639">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-639">Example</span></span>

```c
/* Set the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_set(&resource, NX_TRUE);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_dim_get"></a><span data-ttu-id="5ada2-640">nx_lwm2m_client_resource_dim_get</span><span class="sxs-lookup"><span data-stu-id="5ada2-640">nx_lwm2m_client_resource_dim_get</span></span>

<span data-ttu-id="5ada2-641">Obtém a dimensão de recursos para vários recursos</span><span class="sxs-lookup"><span data-stu-id="5ada2-641">Gets the resource dimension for multiple Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-642">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-642">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_dim_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    UCHAR *dim);
```

### <a name="description"></a><span data-ttu-id="5ada2-643">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-643">Description</span></span>

<span data-ttu-id="5ada2-644">O serviço recupera a dimensão do recurso para recursos múltiplos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-644">The service retrieves the resource dimension for multiple resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-645">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-645">Parameters</span></span>

- <span data-ttu-id="5ada2-646">**recurso** Ponteiro para recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-646">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="5ada2-647">**ponteiro dim** para a dimensão do destino.</span><span class="sxs-lookup"><span data-stu-id="5ada2-647">**dim** Pointer to the destination dimension.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-648">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-648">Return Values</span></span>

- <span data-ttu-id="5ada2-649">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-649">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-650">**NX_LWM2M_CLIENT_BAD_ENCODING** O valor do recurso não é um valor Boolean.</span><span class="sxs-lookup"><span data-stu-id="5ada2-650">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="5ada2-651">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-651">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-652">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-652">Allowed From</span></span>

<span data-ttu-id="5ada2-653">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-653">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-654">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-654">Example</span></span>

```c
/* Get the resource dimension for multiple resource.  */
status = nx_lwm2m_client_resource_dim_get(&resource, &dim);

/* If status is NX_SUCCESS, the resource dimension was successfully get. */
```

## <a name="nx_lwm2m_client_resource_dim_set"></a><span data-ttu-id="5ada2-655">nx_lwm2m_client_resource_dim_set</span><span class="sxs-lookup"><span data-stu-id="5ada2-655">nx_lwm2m_client_resource_dim_set</span></span>

<span data-ttu-id="5ada2-656">Define a dimensão do recurso para recursos múltiplos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-656">Sets the resource dimension for multiple resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-657">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-657">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_dim_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR dim);
```

### <a name="description"></a><span data-ttu-id="5ada2-658">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-658">Description</span></span>

<span data-ttu-id="5ada2-659">O serviço define a dimensão do recurso para recursos múltiplos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-659">The service sets the resource dimension for multiple resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-660">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-660">Parameters</span></span>

- <span data-ttu-id="5ada2-661">**valor** Ponteiro para descrição do valor do recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-661">**value** Pointer to Resource value description.</span></span>
- <span data-ttu-id="5ada2-662">dim **valor** de dimensão.</span><span class="sxs-lookup"><span data-stu-id="5ada2-662">**dim** Dimension value.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-663">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-663">Return Values</span></span>

- <span data-ttu-id="5ada2-664">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-664">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-665">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-665">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-666">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-666">Allowed From</span></span>

<span data-ttu-id="5ada2-667">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-667">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-668">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-668">Example</span></span>

```c
/* Set the resource dimension.  */
status = nx_lwm2m_client_resource_dim_set(&resource, 3);

/* If status is NX_SUCCESS, the resource dimension was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float32_get"></a><span data-ttu-id="5ada2-669">nx_lwm2m_client_resource_float32_get</span><span class="sxs-lookup"><span data-stu-id="5ada2-669">nx_lwm2m_client_resource_float32_get</span></span>

<span data-ttu-id="5ada2-670">Obtém o valor de um recurso **flutuante** de 32 Bits</span><span class="sxs-lookup"><span data-stu-id="5ada2-670">Gets the value of a 32-Bit **float** Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-671">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-671">Prototype</span></span>

```C
UINT nx_lwm2m_client_resource_float32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a><span data-ttu-id="5ada2-672">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-672">Description</span></span>

<span data-ttu-id="5ada2-673">O serviço recupera o valor de um recurso **flutuante** de 32 Bits.</span><span class="sxs-lookup"><span data-stu-id="5ada2-673">The service retrieves the value of a 32-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-674">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-674">Parameters</span></span>

- <span data-ttu-id="5ada2-675">**recurso** Ponteiro para recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-675">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="5ada2-676">**float32_ptr** Ponteiro para o destino 32-Bit **valor flutuante.**</span><span class="sxs-lookup"><span data-stu-id="5ada2-676">**float32_ptr** Pointer to the destination 32-Bit **float** value.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-677">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-677">Return Values</span></span>

- <span data-ttu-id="5ada2-678">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-678">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-679">**NX_LWM2M_CLIENT_BAD_ENCODING** O valor do recurso não é um valor Boolean.</span><span class="sxs-lookup"><span data-stu-id="5ada2-679">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="5ada2-680">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-680">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-681">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-681">Allowed From</span></span>

<span data-ttu-id="5ada2-682">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-682">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-683">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-683">Example</span></span>

```C
/* Get the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_get(&resource, &float32);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float32_set"></a><span data-ttu-id="5ada2-684">nx_lwm2m_client_resource_float32_set</span><span class="sxs-lookup"><span data-stu-id="5ada2-684">nx_lwm2m_client_resource_float32_set</span></span>

<span data-ttu-id="5ada2-685">Define o valor de um recurso **flutuante** de 32 bits</span><span class="sxs-lookup"><span data-stu-id="5ada2-685">Sets the value of a 32-Bit **float** Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-686">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-686">Prototype</span></span>

```C
UINT nx_lwm2m_client_resource_float32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 float32_data);
```

### <a name="description"></a><span data-ttu-id="5ada2-687">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-687">Description</span></span>

<span data-ttu-id="5ada2-688">O serviço define o valor de um recurso **flutuante** de 32 Bits.</span><span class="sxs-lookup"><span data-stu-id="5ada2-688">The service sets the value of a 32-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-689">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-689">Parameters</span></span>

- <span data-ttu-id="5ada2-690">**recurso** Ponteiro para recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-690">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="5ada2-691">**float32_data** dados **flutuantes** de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="5ada2-691">**float32_data** 32-Bit **float** data.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-692">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-692">Return Values</span></span>

- <span data-ttu-id="5ada2-693">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-693">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-694">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-694">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-695">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-695">Allowed From</span></span>

<span data-ttu-id="5ada2-696">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-696">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-697">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-697">Example</span></span>

```c
/* Set the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float64_get"></a><span data-ttu-id="5ada2-698">nx_lwm2m_client_resource_float64_get</span><span class="sxs-lookup"><span data-stu-id="5ada2-698">nx_lwm2m_client_resource_float64_get</span></span>

<span data-ttu-id="5ada2-699">Obtém o valor de um recurso flutuante de 64 Bits.</span><span class="sxs-lookup"><span data-stu-id="5ada2-699">Gets the value of a 64-Bit float Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-700">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-700">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_float64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a><span data-ttu-id="5ada2-701">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-701">Description</span></span>

<span data-ttu-id="5ada2-702">O serviço recupera o valor de um recurso **flutuante** de 64 Bits.</span><span class="sxs-lookup"><span data-stu-id="5ada2-702">The service retrieves the value of a 64-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-703">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-703">Parameters</span></span>

- <span data-ttu-id="5ada2-704">**recurso** Ponteiro para recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-704">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="5ada2-705">**float64_ptr** Ponteiro para o destino 64-Bit **valor flutuante.**</span><span class="sxs-lookup"><span data-stu-id="5ada2-705">**float64_ptr** Pointer to the destination 64-Bit **float** value.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-706">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-706">Return Values</span></span>

- <span data-ttu-id="5ada2-707">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-707">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-708">**NX_LWM2M_CLIENT_BAD_ENCODING** O valor do recurso não é um valor flutuante.</span><span class="sxs-lookup"><span data-stu-id="5ada2-708">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a float value.</span></span>
- <span data-ttu-id="5ada2-709">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-709">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-710">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-710">Allowed From</span></span>

<span data-ttu-id="5ada2-711">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-711">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-712">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-712">Example</span></span>

```c
/* Get the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_get(&resource, &float64);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float64_set"></a><span data-ttu-id="5ada2-713">nx_lwm2m_client_resource_float64_set</span><span class="sxs-lookup"><span data-stu-id="5ada2-713">nx_lwm2m_client_resource_float64_set</span></span>

<span data-ttu-id="5ada2-714">Define o valor de um recurso **flutuante** de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="5ada2-714">Sets the value of a 64-Bit **float** Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-715">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-715">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_float64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a><span data-ttu-id="5ada2-716">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-716">Description</span></span>

<span data-ttu-id="5ada2-717">O serviço define o valor de um recurso **flutuante** de 64 Bits.</span><span class="sxs-lookup"><span data-stu-id="5ada2-717">The service sets the value of a 64-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-718">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-718">Parameters</span></span>

- <span data-ttu-id="5ada2-719">**recurso** Ponteiro para recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-719">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="5ada2-720">**float64_data** dados **flutuantes** de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="5ada2-720">**float64_data** 64-bit **float** data.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-721">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-721">Return Values</span></span>

- <span data-ttu-id="5ada2-722">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-722">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-723">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-723">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-724">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-724">Allowed From</span></span>

<span data-ttu-id="5ada2-725">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-725">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-726">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-726">Example</span></span>

```c
/* Set the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_info_get"></a><span data-ttu-id="5ada2-727">nx_lwm2m_client_resource_info_get</span><span class="sxs-lookup"><span data-stu-id="5ada2-727">nx_lwm2m_client_resource_info_get</span></span>

<span data-ttu-id="5ada2-728">Obtém a informação de recursos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-728">Gets the resource info.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-729">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-729">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_info_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *resource_id, 
    ULONG *operation);
```

### <a name="description"></a><span data-ttu-id="5ada2-730">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-730">Description</span></span>

<span data-ttu-id="5ada2-731">O serviço recupera a informação de recursos do Recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-731">The service retrieves the resource information of Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-732">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-732">Parameters</span></span>

- <span data-ttu-id="5ada2-733">**recurso** Ponteiro para recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-733">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="5ada2-734">**resource_id** Ponteiro para o ID do recurso de destino.</span><span class="sxs-lookup"><span data-stu-id="5ada2-734">**resource_id** Pointer to the destination resource ID.</span></span>
- <span data-ttu-id="5ada2-735">**operação** Ponteiro para a operação de recursos de destino.</span><span class="sxs-lookup"><span data-stu-id="5ada2-735">**operation** Pointer to the destination resource operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-736">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-736">Return Values</span></span>

- <span data-ttu-id="5ada2-737">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-737">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-738">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-738">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-739">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-739">Allowed From</span></span>

<span data-ttu-id="5ada2-740">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-740">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-741">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-741">Example</span></span>

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_info_get(&resource, &resource_id, &operation);

/* If status is NX_SUCCESS, the resource information was successfully get. */
```

## <a name="nx_lwm2m_client_resource_info_set"></a><span data-ttu-id="5ada2-742">nx_lwm2m_client_resource_info_set</span><span class="sxs-lookup"><span data-stu-id="5ada2-742">nx_lwm2m_client_resource_info_set</span></span>

<span data-ttu-id="5ada2-743">Define a informação de recursos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-743">Sets the resource information.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-744">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-744">Prototype</span></span>

```C
UINT nx_lwm2m_client_resource_info_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a><span data-ttu-id="5ada2-745">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-745">Description</span></span>

<span data-ttu-id="5ada2-746">O serviço define a informação do recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-746">The service sets the resource information.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-747">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-747">Parameters</span></span>

- <span data-ttu-id="5ada2-748">**recurso** Ponteiro para recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-748">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="5ada2-749">**resource_id** Identificação do recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-749">**resource_id** ID of the resource.</span></span>
- <span data-ttu-id="5ada2-750">**operação** Operação do recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-750">**operation** Operation of the resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-751">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-751">Return Values</span></span>

- <span data-ttu-id="5ada2-752">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-752">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-753">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-753">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-754">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-754">Allowed From</span></span>

<span data-ttu-id="5ada2-755">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-755">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-756">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-756">Example</span></span>

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_info_set(&resource, 0, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

/* If status is NX_SUCCESS, the resource information was successfully set. */
```

## <a name="nx_lwm2m_client_resource_instances_get"></a><span data-ttu-id="5ada2-757">nx_lwm2m_client_resource_instances_get</span><span class="sxs-lookup"><span data-stu-id="5ada2-757">nx_lwm2m_client_resource_instances_get</span></span>

<span data-ttu-id="5ada2-758">Obtém a instância de vários recursos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-758">Gets the instance of multiple resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-759">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-759">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_instances_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT *count);
```

### <a name="description"></a><span data-ttu-id="5ada2-760">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-760">Description</span></span>

<span data-ttu-id="5ada2-761">O serviço recupera a informação de recursos do Recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-761">The service retrieves the resource information of Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-762">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-762">Parameters</span></span>

- <span data-ttu-id="5ada2-763">**recurso** Ponteiro para recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-763">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="5ada2-764">**resource_instances** Ponteiro para o ID do recurso de destino.</span><span class="sxs-lookup"><span data-stu-id="5ada2-764">**resource_instances** Pointer to the destination resource ID.</span></span>
- <span data-ttu-id="5ada2-765">**contar** Ponteiro para a contagem.</span><span class="sxs-lookup"><span data-stu-id="5ada2-765">**count** Pointer to the count.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-766">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-766">Return Values</span></span>

- <span data-ttu-id="5ada2-767">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-767">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-768">**NX_LWM2M_CLIENT_BAD_ENCODING** O valor do recurso não é um valor Boolean.</span><span class="sxs-lookup"><span data-stu-id="5ada2-768">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="5ada2-769">**NX_LWM2M_CLIENT_NO_MEMORY** Sem memória para preencher casos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-769">**NX_LWM2M_CLIENT_NO_MEMORY** No memory to fill out instances.</span></span>
- <span data-ttu-id="5ada2-770">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-770">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-771">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-771">Allowed From</span></span>

<span data-ttu-id="5ada2-772">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-772">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-773">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-773">Example</span></span>

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_instances_get(&resource, &resource_instances,
                                                &count);

/* If status is NX_SUCCESS, the instances of multiple resource information were successfully get. */
```

## <a name="nx_lwm2m_client_resource_instances_set"></a><span data-ttu-id="5ada2-774">nx_lwm2m_client_resource_instances_set</span><span class="sxs-lookup"><span data-stu-id="5ada2-774">nx_lwm2m_client_resource_instances_set</span></span>

<span data-ttu-id="5ada2-775">Define as instâncias de recursos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-775">Sets the resource instances.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-776">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-776">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_instances_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT count);
```
### <a name="description"></a><span data-ttu-id="5ada2-777">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-777">Description</span></span>

<span data-ttu-id="5ada2-778">O serviço define as instâncias de recursos para vários recursos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-778">The service sets the resource instances for multiple resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-779">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-779">Parameters</span></span>

- <span data-ttu-id="5ada2-780">**recurso** Ponteiro para recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-780">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="5ada2-781">**resource_instance** Ponteiro para instâncias de recursos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-781">**resource_instance** Pointer to resource instances.</span></span>
- <span data-ttu-id="5ada2-782">**contar** Contagem de casos de recursos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-782">**count** Count of resource instances.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-783">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-783">Return Values</span></span>

- <span data-ttu-id="5ada2-784">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-784">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-785">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-785">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-786">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-786">Allowed From</span></span>

<span data-ttu-id="5ada2-787">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-787">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-788">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-788">Example</span></span>

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_instances_set(&resource, &resource_instance, 2);

/* If status is NX_SUCCESS, the resource instances were successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer32_get"></a><span data-ttu-id="5ada2-789">nx_lwm2m_client_resource_integer32_get</span><span class="sxs-lookup"><span data-stu-id="5ada2-789">nx_lwm2m_client_resource_integer32_get</span></span>

<span data-ttu-id="5ada2-790">Obtém o valor de um recurso inteiro de 32 Bits.</span><span class="sxs-lookup"><span data-stu-id="5ada2-790">Gets the value of a 32-Bit integer Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-791">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-791">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 *integer32_ptr);
```

### <a name="description"></a><span data-ttu-id="5ada2-792">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-792">Description</span></span>

<span data-ttu-id="5ada2-793">O serviço recupera o valor de um recurso inteiro de 32 Bits.</span><span class="sxs-lookup"><span data-stu-id="5ada2-793">The service retrieves the value of a 32-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-794">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-794">Parameters</span></span>

- <span data-ttu-id="5ada2-795">**recurso** Ponteiro para recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-795">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="5ada2-796">**integer32_ptr** Ponteiro para o valor inteiro de 32 Bits.</span><span class="sxs-lookup"><span data-stu-id="5ada2-796">**integer32_ptr** Pointer to the 32-Bit integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-797">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-797">Return Values</span></span>

- <span data-ttu-id="5ada2-798">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-798">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-799">**NX_LWM2M_CLIENT_BAD_ENCODING** O valor do recurso não é valor inteiro.</span><span class="sxs-lookup"><span data-stu-id="5ada2-799">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not integer value.</span></span>
- <span data-ttu-id="5ada2-800">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-800">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-801">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-801">Allowed From</span></span>

<span data-ttu-id="5ada2-802">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-802">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-803">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-803">Example</span></span>

```c
/* Get the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_get(&resource, &integer32);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer32_set"></a><span data-ttu-id="5ada2-804">nx_lwm2m_client_resource_integer32_set</span><span class="sxs-lookup"><span data-stu-id="5ada2-804">nx_lwm2m_client_resource_integer32_set</span></span>

<span data-ttu-id="5ada2-805">Define o valor de um recurso inteiro de 32 Bits.</span><span class="sxs-lookup"><span data-stu-id="5ada2-805">Sets the value of a 32-Bit integer Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-806">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-806">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 integer32_data);
```

### <a name="description"></a><span data-ttu-id="5ada2-807">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-807">Description</span></span>

<span data-ttu-id="5ada2-808">O serviço define o valor de um recurso inteiro de 32 Bits.</span><span class="sxs-lookup"><span data-stu-id="5ada2-808">The service sets the value of a 32-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-809">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-809">Parameters</span></span>

- <span data-ttu-id="5ada2-810">**recurso** Ponteiro para recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-810">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="5ada2-811">**integer32_data** dados inteiros de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="5ada2-811">**integer32_data** 32-Bit integer data.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-812">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-812">Return Values</span></span>

- <span data-ttu-id="5ada2-813">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-813">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-814">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-814">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-815">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-815">Allowed From</span></span>

<span data-ttu-id="5ada2-816">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-816">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-817">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-817">Example</span></span>

```c
/* Set the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_set(&resource, 8);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer64_get"></a><span data-ttu-id="5ada2-818">nx_lwm2m_client_resource_integer64_get</span><span class="sxs-lookup"><span data-stu-id="5ada2-818">nx_lwm2m_client_resource_integer64_get</span></span>

<span data-ttu-id="5ada2-819">Obtém o valor de um recurso inteiro de 64 Bits.</span><span class="sxs-lookup"><span data-stu-id="5ada2-819">Gets the value of a 64-Bit integer Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-820">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-820">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 *integer64_ptr);
```

### <a name="description"></a><span data-ttu-id="5ada2-821">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-821">Description</span></span>

<span data-ttu-id="5ada2-822">O serviço recupera o valor de um recurso inteiro de 64 Bits.</span><span class="sxs-lookup"><span data-stu-id="5ada2-822">The service retrieves the value of a 64-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-823">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-823">Parameters</span></span>

- <span data-ttu-id="5ada2-824">**recurso** Ponteiro para recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-824">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="5ada2-825">**integer64_ptr** Ponteiro para o valor inteiro de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="5ada2-825">**integer64_ptr** Pointer to the 64-Bit integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-826">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-826">Return Values</span></span>

- <span data-ttu-id="5ada2-827">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-827">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-828">**NX_LWM2M_CLIENT_BAD_ENCODING** O valor do recurso não é o valor inteiro de 64 Bits.</span><span class="sxs-lookup"><span data-stu-id="5ada2-828">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not 64-Bit integer value.</span></span>
- <span data-ttu-id="5ada2-829">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-829">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-830">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-830">Allowed From</span></span>

<span data-ttu-id="5ada2-831">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-831">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-832">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-832">Example</span></span>

```c
/* Get the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_get(&resource, &integer64);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer64_set"></a><span data-ttu-id="5ada2-833">nx_lwm2m_client_resource_integer64_set</span><span class="sxs-lookup"><span data-stu-id="5ada2-833">nx_lwm2m_client_resource_integer64_set</span></span>

## <a name="set-the-value-of-a-64-bit-integer-resource"></a><span data-ttu-id="5ada2-834">Desajei o valor de um recurso inteiro de 64 Bits</span><span class="sxs-lookup"><span data-stu-id="5ada2-834">Set the value of a 64-Bit integer Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-835">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-835">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 integer64_data);
```

### <a name="description"></a><span data-ttu-id="5ada2-836">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-836">Description</span></span>

<span data-ttu-id="5ada2-837">O serviço define o valor de um recurso inteiro de 64 Bits.</span><span class="sxs-lookup"><span data-stu-id="5ada2-837">The service sets the value of a 64-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-838">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-838">Parameters</span></span>

- <span data-ttu-id="5ada2-839">**recurso** Ponteiro para recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-839">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="5ada2-840">**integer64_data** inteiro de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="5ada2-840">**integer64_data** 64-bit integer.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-841">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-841">Return Values</span></span>

- <span data-ttu-id="5ada2-842">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-842">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-843">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-843">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-844">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-844">Allowed From</span></span>

<span data-ttu-id="5ada2-845">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-845">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-846">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-846">Example</span></span>

```c
/* Set the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_set(&resource, 32323);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully set. */
```

##  <a name="nx_lwm2m_client_resource_objlnk_get"></a><span data-ttu-id="5ada2-847">nx_lwm2m_client_resource_objlnk_get</span><span class="sxs-lookup"><span data-stu-id="5ada2-847">nx_lwm2m_client_resource_objlnk_get</span></span>

<span data-ttu-id="5ada2-848">Obtém o valor de um recurso de ligação de objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-848">Gets the value of an object link resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-849">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-849">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_objlnk_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *object_id, 
    NX_LWM2M_ID *instance_id);
```

### <a name="description"></a><span data-ttu-id="5ada2-850">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-850">Description</span></span>

<span data-ttu-id="5ada2-851">O serviço recupera o valor da ligação de objetos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-851">The service retrieves the value of object link.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-852">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-852">Parameters</span></span>

- <span data-ttu-id="5ada2-853">**recurso** Ponteiro para recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-853">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="5ada2-854">**object_id** Ponteiro para a identificação do objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-854">**object_id** Pointer to the object ID.</span></span>
- <span data-ttu-id="5ada2-855">**instance_id** Ponteiro para o iD da instância do objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-855">**instance_id** Pointer to the object instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-856">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-856">Return Values</span></span>

- <span data-ttu-id="5ada2-857">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-857">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-858">**NX_LWM2M_CLIENT_BAD_ENCODING** O valor do recurso não é um valor de ligação de objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-858">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not an object link value.</span></span>
- <span data-ttu-id="5ada2-859">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-859">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-860">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-860">Allowed From</span></span>

<span data-ttu-id="5ada2-861">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-861">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-862">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-862">Example</span></span>

```c
/* Get the value of the object link resource.  */
status = nx_lwm2m_client_resource_objlnk_get(&resource, &object_id, &instance_id);

/* If status is NX_SUCCESS, the object link value was successfully get. */
```

## <a name="nx_lwm2m_client_resource_objlnk_set"></a><span data-ttu-id="5ada2-863">nx_lwm2m_client_resource_objlnk_set</span><span class="sxs-lookup"><span data-stu-id="5ada2-863">nx_lwm2m_client_resource_objlnk_set</span></span>

<span data-ttu-id="5ada2-864">Define as instâncias de recursos</span><span class="sxs-lookup"><span data-stu-id="5ada2-864">Sets the resource instances</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-865">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-865">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_objlnk_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_ID object_id, 
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a><span data-ttu-id="5ada2-866">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-866">Description</span></span>

<span data-ttu-id="5ada2-867">O serviço define o valor do recurso de ligação de objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-867">The service sets the value of the object link resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-868">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-868">Parameters</span></span>

- <span data-ttu-id="5ada2-869">**recurso** Ponteiro para recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-869">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="5ada2-870">**object_id** Identificação de objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-870">**object_id** Object ID.</span></span>
- <span data-ttu-id="5ada2-871">**instance_id** Identificação de instância de objeto.</span><span class="sxs-lookup"><span data-stu-id="5ada2-871">**instance_id** Object instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-872">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-872">Return Values</span></span>

- <span data-ttu-id="5ada2-873">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-873">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-874">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-874">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-875">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-875">Allowed From</span></span>

<span data-ttu-id="5ada2-876">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-876">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-877">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-877">Example</span></span>

```c
/* Set the value of object link resource.  */
status = nx_lwm2m_client_resource_objlnk_set(&resource, 3303, 2);

/* If status is NX_SUCCESS, the value of object link resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_opaque_get"></a><span data-ttu-id="5ada2-878">nx_lwm2m_client_resource_opaque_get</span><span class="sxs-lookup"><span data-stu-id="5ada2-878">nx_lwm2m_client_resource_opaque_get</span></span>

<span data-ttu-id="5ada2-879">Obtém o valor de um recurso opaco.</span><span class="sxs-lookup"><span data-stu-id="5ada2-879">Gets the value of an opaque Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-880">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-880">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_opaque_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const VOID **opaque_ptr, 
    UINT \*opaque_length);
```


### <a name="description"></a><span data-ttu-id="5ada2-881">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-881">Description</span></span>

<span data-ttu-id="5ada2-882">O serviço recupera o valor de um Recurso opaco.</span><span class="sxs-lookup"><span data-stu-id="5ada2-882">The service retrieves the value of an opaque Resource.</span></span> <span data-ttu-id="5ada2-883">Um valor de recurso opaco consiste num ponteiro para um tampão e um comprimento.</span><span class="sxs-lookup"><span data-stu-id="5ada2-883">An opaque resource value consists of a pointer to a buffer and a length.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-884">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-884">Parameters</span></span>

- <span data-ttu-id="5ada2-885">**recurso** Ponteiro para recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-885">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="5ada2-886">**opaque_ptr** Ponteiro para os dados opacos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-886">**opaque_ptr** Pointer to the opaque data.</span></span>
- <span data-ttu-id="5ada2-887">**opaque_length** Ponteiro para o comprimento de dados opacos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-887">**opaque_length** Pointer to the opaque data length.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-888">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-888">Return Values</span></span>

- <span data-ttu-id="5ada2-889">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-889">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-890">**NX_LWM2M_CLIENT_BAD_ENCODING** O valor dos recursos não é um recurso opaco.</span><span class="sxs-lookup"><span data-stu-id="5ada2-890">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not an opaque resource.</span></span>
- <span data-ttu-id="5ada2-891">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-891">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-892">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-892">Allowed From</span></span>

<span data-ttu-id="5ada2-893">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-893">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-894">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-894">Example</span></span>

```c
/* Get the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_get(&resource, &opaque_ptr, &opaque_length);

/* If status is NX_SUCCESS, the value of opaque resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_opaque_set"></a><span data-ttu-id="5ada2-895">nx_lwm2m_client_resource_opaque_set</span><span class="sxs-lookup"><span data-stu-id="5ada2-895">nx_lwm2m_client_resource_opaque_set</span></span>

<span data-ttu-id="5ada2-896">Define o valor de um recurso opaco.</span><span class="sxs-lookup"><span data-stu-id="5ada2-896">Sets the value of an opaque Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-897">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-897">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_opaque_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    VOID *opaque_ptr, 
    UINT opaque_length);
```

### <a name="description"></a><span data-ttu-id="5ada2-898">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-898">Description</span></span>

<span data-ttu-id="5ada2-899">O serviço define o valor de um Recurso opaco.</span><span class="sxs-lookup"><span data-stu-id="5ada2-899">The service sets the value of an opaque Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-900">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-900">Parameters</span></span>

- <span data-ttu-id="5ada2-901">**recurso** Ponteiro para recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-901">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="5ada2-902">**opaque_ptr** Ponteiro para os dados opacos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-902">**opaque_ptr** Pointer to the opaque data.</span></span>
- <span data-ttu-id="5ada2-903">**opaque_length** Comprimento dos dados opacos.</span><span class="sxs-lookup"><span data-stu-id="5ada2-903">**opaque_length** Length of the opaque data.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-904">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-904">Return Values</span></span>

- <span data-ttu-id="5ada2-905">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-905">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-906">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-906">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-907">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-907">Allowed From</span></span>

<span data-ttu-id="5ada2-908">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-908">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-909">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-909">Example</span></span>

```c
/* Set the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_set(&resource, “AQIDBAU=”, 8);

/* If status is NX_SUCCESS, the value of opaque resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_string_get"></a><span data-ttu-id="5ada2-910">nx_lwm2m_client_resource_string_get</span><span class="sxs-lookup"><span data-stu-id="5ada2-910">nx_lwm2m_client_resource_string_get</span></span>

<span data-ttu-id="5ada2-911">Obtém o valor de um recurso de corda.</span><span class="sxs-lookup"><span data-stu-id="5ada2-911">Gets the value of a string Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-912">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-912">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_string_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const CHAR **string_ptr, 
    UINT *string_length);
```

### <a name="description"></a><span data-ttu-id="5ada2-913">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-913">Description</span></span>

<span data-ttu-id="5ada2-914">O serviço recupera o valor de um recurso de corda.</span><span class="sxs-lookup"><span data-stu-id="5ada2-914">The service retrieves the value of a string Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-915">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-915">Parameters</span></span>

- <span data-ttu-id="5ada2-916">**recurso** Ponteiro para recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-916">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="5ada2-917">**string_ptr** Ponteiro para o ponteiro de corda de destino.</span><span class="sxs-lookup"><span data-stu-id="5ada2-917">**string_ptr** Pointer to the destination string pointer.</span></span>
- <span data-ttu-id="5ada2-918">**string_length** Ponteiro para o comprimento da corda de destino.</span><span class="sxs-lookup"><span data-stu-id="5ada2-918">**string_length** Pointer to the destination string length.</span></span> <span data-ttu-id="5ada2-919">Pode ser **NU SE** a cadeia estiver nula.</span><span class="sxs-lookup"><span data-stu-id="5ada2-919">Can be **NULL** if the string is null-terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-920">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-920">Return Values</span></span>

- <span data-ttu-id="5ada2-921">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-921">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-922">**NX_LWM2M_CLIENT_BAD_ENCODING** O valor do recurso não é um valor de corda.</span><span class="sxs-lookup"><span data-stu-id="5ada2-922">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a string value.</span></span>
- <span data-ttu-id="5ada2-923">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-923">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-924">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-924">Allowed From</span></span>

<span data-ttu-id="5ada2-925">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-925">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-926">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-926">Example</span></span>

```c
/* Get the value of a string resource.  */
status = nx_lwm2m_client_resource_string_get(&resource, &string_ptr, &string_length);

/* If status is NX_SUCCESS, the value of string resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_string_set"></a><span data-ttu-id="5ada2-927">nx_lwm2m_client_resource_string_set</span><span class="sxs-lookup"><span data-stu-id="5ada2-927">nx_lwm2m_client_resource_string_set</span></span>

<span data-ttu-id="5ada2-928">Define o valor de um recurso de corda.</span><span class="sxs-lookup"><span data-stu-id="5ada2-928">Sets the value of a string Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-929">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-929">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_string_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR *string_ptr, 
    UINT string_length);
```

### <a name="description"></a><span data-ttu-id="5ada2-930">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-930">Description</span></span>

<span data-ttu-id="5ada2-931">O serviço define o valor de um recurso inteiro de 64 Bits.</span><span class="sxs-lookup"><span data-stu-id="5ada2-931">The service sets the value of a 64-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-932">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-932">Parameters</span></span>

- <span data-ttu-id="5ada2-933">**recurso** Ponteiro para recurso.</span><span class="sxs-lookup"><span data-stu-id="5ada2-933">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="5ada2-934">**string_ptr** Ponteiro para a corda.</span><span class="sxs-lookup"><span data-stu-id="5ada2-934">**string_ptr** Pointer to the string.</span></span>
- <span data-ttu-id="5ada2-935">**string_length** Comprimento da corda.</span><span class="sxs-lookup"><span data-stu-id="5ada2-935">**string_length** Length of the string.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-936">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-936">Return Values</span></span>

- <span data-ttu-id="5ada2-937">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-937">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-938">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-938">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-939">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-939">Allowed From</span></span>

<span data-ttu-id="5ada2-940">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-940">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-941">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-941">Example</span></span>

```c
/* Set the value of a string resource.  */
status = nx_lwm2m_client_resource_string_set(&resource, “test”, sizeof(“test”) - 1);

/* If status is NX_SUCCESS, the value of string resource was successfully set. */
```

## <a name="nx_lwm2m_client_session_bootstrap"></a><span data-ttu-id="5ada2-942">nx_lwm2m_client_session_bootstrap</span><span class="sxs-lookup"><span data-stu-id="5ada2-942">nx_lwm2m_client_session_bootstrap</span></span>

<span data-ttu-id="5ada2-943">Inicia uma sessão com um Servidor Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="5ada2-943">Starts a session with a Bootstrap Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-944">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-944">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port);
```

### <a name="description"></a><span data-ttu-id="5ada2-945">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-945">Description</span></span>

<span data-ttu-id="5ada2-946">Este serviço inicia uma sessão com um Servidor Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="5ada2-946">This service starts a session with a Bootstrap Server.</span></span> <span data-ttu-id="5ada2-947">O servidor deve ter uma instância de segurança correspondente no Objeto de Segurança.</span><span class="sxs-lookup"><span data-stu-id="5ada2-947">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="5ada2-948">Se o recurso 'Hold Off' for diferente de zero na Instância de Segurança associada a este servidor, a sessão aguardará uma bota iniciada pelo servidor, se não for iniciada nenhuma bota pelo servidor após este período de tempo, será executada uma Boostrap iniciada pelo Cliente.</span><span class="sxs-lookup"><span data-stu-id="5ada2-948">If the ‘Hold Off’ resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, If no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span>

<span data-ttu-id="5ada2-949">Qualquer sessão ativa atual é abortada por esta chamada e substituída pela nova sessão do Bootstrap Server.</span><span class="sxs-lookup"><span data-stu-id="5ada2-949">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-950">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-950">Parameters</span></span>

- <span data-ttu-id="5ada2-951">**session_ptr** Ponteiro para o bloco de controlo de sessão de cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-951">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="5ada2-952">**security_id** O ID de Instância de Segurança do Servidor Bootstrap deve ser definido para NX_LWM2M_RESERVED_ID (65535) se o Servidor Bootstrap não tiver nenhuma Instância de Segurança definida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-952">**security_id** The Security Instance ID of the Bootstrap Server, must be set to NX_LWM2M_RESERVED_ID (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="5ada2-953">**ip_address** O endereço IP do servidor.</span><span class="sxs-lookup"><span data-stu-id="5ada2-953">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="5ada2-954">**porto** A porta UDP do servidor.</span><span class="sxs-lookup"><span data-stu-id="5ada2-954">**port** The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-955">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-955">Return Values</span></span>

- <span data-ttu-id="5ada2-956">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-956">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-957">**NX_LWM2M_CLIENT_ERROR** Erro de botas.</span><span class="sxs-lookup"><span data-stu-id="5ada2-957">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="5ada2-958">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** A porta não está disponível.</span><span class="sxs-lookup"><span data-stu-id="5ada2-958">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="5ada2-959">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-959">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-960">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-960">Allowed From</span></span>

<span data-ttu-id="5ada2-961">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-961">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-962">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-962">Example</span></span>

```c
/* Start bootstrap.  */
status = nx_lwm2m_client_session_bootstrap(&lwm2m_client, 0, &ip_address, 5783);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a><span data-ttu-id="5ada2-963">nx_lwm2m_client_session_bootstrap_dtls</span><span class="sxs-lookup"><span data-stu-id="5ada2-963">nx_lwm2m_client_session_bootstrap_dtls</span></span>

<span data-ttu-id="5ada2-964">Inicia uma sessão segura com um Servidor Bootstrap</span><span class="sxs-lookup"><span data-stu-id="5ada2-964">Starts a secure session with a Bootstrap Server</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-965">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-965">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port, 
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a><span data-ttu-id="5ada2-966">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-966">Description</span></span>

<span data-ttu-id="5ada2-967">Este serviço inicia uma sessão com um Servidor Bootstrap utilizando uma ligação DTLS segura.</span><span class="sxs-lookup"><span data-stu-id="5ada2-967">This service start a session with a Bootstrap Server using a secure DTLS connection.</span></span> <span data-ttu-id="5ada2-968">O servidor deve ter uma instância de segurança correspondente no Objeto de Segurança.</span><span class="sxs-lookup"><span data-stu-id="5ada2-968">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="5ada2-969">A sessão DTLS deve ter sido configurada com as suites de cifra adequadas e material chave antes de chamar esta função.</span><span class="sxs-lookup"><span data-stu-id="5ada2-969">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="5ada2-970">**NX_SECURE_ENABLE_DTLS** deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-970">**NX_SECURE_ENABLE_DTLS** must be defined.</span></span>

<span data-ttu-id="5ada2-971">Se o recurso 'Hold Off' for diferente de zero na Instância de Segurança associada a este servidor, a sessão aguardará uma bota iniciada pelo servidor, se não for iniciada nenhuma bota pelo servidor após este período de tempo, será executada uma Boostrap iniciada pelo Cliente.</span><span class="sxs-lookup"><span data-stu-id="5ada2-971">If the ‘Hold Off’ resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, if no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span> 

<span data-ttu-id="5ada2-972">Qualquer sessão ativa atual é abortada por esta chamada e substituída pela nova sessão do Bootstrap Server.</span><span class="sxs-lookup"><span data-stu-id="5ada2-972">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-973">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-973">Parameters</span></span>

- <span data-ttu-id="5ada2-974">**session_ptr** Ponteiro para o bloco de controlo de sessão de cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-974">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="5ada2-975">**security_id** O ID de Instância de Segurança do Servidor Bootstrap deve ser definido para **NX_LWM2M_RESERVED_ID** (65535) se o Servidor Bootstrap não tiver nenhuma Instância de Segurança definida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-975">**security_id** The Security Instance ID of the Bootstrap Server, must be set to **NX_LWM2M_RESERVED_ID** (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="5ada2-976">**ip_address** O endereço IP do servidor.</span><span class="sxs-lookup"><span data-stu-id="5ada2-976">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="5ada2-977">**porto** A porta UDP do servidor.</span><span class="sxs-lookup"><span data-stu-id="5ada2-977">**port** The UDP port of the server.</span></span>
- <span data-ttu-id="5ada2-978">**dtls_session_ptr** A sessão DTLS para utilizar para a sessão Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="5ada2-978">**dtls_session_ptr** The DTLS session to use for the Bootstrap session.</span></span>
- <span data-ttu-id="5ada2-979">**dtls_local_port** A porta UDP local utilizada para a sessão DTLS.</span><span class="sxs-lookup"><span data-stu-id="5ada2-979">**dtls_local_port** The local UDP port used for the DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-980">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-980">Return Values</span></span>

- <span data-ttu-id="5ada2-981">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-981">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-982">**NX_LWM2M_CLIENT_ERROR** Erro de botas.</span><span class="sxs-lookup"><span data-stu-id="5ada2-982">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="5ada2-983">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** A porta não está disponível.</span><span class="sxs-lookup"><span data-stu-id="5ada2-983">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="5ada2-984">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-984">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-985">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-985">Allowed From</span></span>

<span data-ttu-id="5ada2-986">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-986">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-987">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-987">Example</span></span>

```c
/* Start bootstrap with DTLS.  */
status = nx_lwm2m_client_session_bootstrap_dtls(&lwm2m_client, 0, &ip_address, 5784, &dtls_session);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_create"></a><span data-ttu-id="5ada2-988">nx_lwm2m_client_session_create</span><span class="sxs-lookup"><span data-stu-id="5ada2-988">nx_lwm2m_client_session_create</span></span>

<span data-ttu-id="5ada2-989">Cria uma Sessão de Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-989">Creates a LWM2M Client Session.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-990">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-990">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_create(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a><span data-ttu-id="5ada2-991">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-991">Description</span></span>

<span data-ttu-id="5ada2-992">Este serviço cria uma nova Sessão de Cliente LWM2M anexada a um Cliente LWM2M existente.</span><span class="sxs-lookup"><span data-stu-id="5ada2-992">This service creates a new LWM2M Client Session attached to an existing LWM2M Client.</span></span> <span data-ttu-id="5ada2-993">A sessão é utilizada pelo Cliente LWM2M para comunicar com um Servidor Bootstrap ou um Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-993">The session is used by the LWM2M Client to communicate with a Bootstrap Server or a LWM2M Server.</span></span> 

<span data-ttu-id="5ada2-994">A aplicação deve fornecer uma função de retorno que será chamada quando o estado da sessão for atualizado.</span><span class="sxs-lookup"><span data-stu-id="5ada2-994">The application must provide a callback function that will be called when the state of the session is updated.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-995">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-995">Parameters</span></span>

- <span data-ttu-id="5ada2-996">**session_ptr** Ponteiro para o bloco de controlo de sessão de cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-996">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="5ada2-997">**client_ptr** Ponteiro para o cliente LWM2M anteriormente criado.</span><span class="sxs-lookup"><span data-stu-id="5ada2-997">**client_ptr** Pointer to the previously created LWM2M Client.</span></span>
- <span data-ttu-id="5ada2-998">**state_callback** Chamada de chamada de chamada que é chamada quando o estado da sessão mudou.</span><span class="sxs-lookup"><span data-stu-id="5ada2-998">**state_callback** Application callback that is called when the state of the session has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-999">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-999">Return Values</span></span>

- <span data-ttu-id="5ada2-1000">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1000">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-1001">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1001">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-1002">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-1002">Allowed From</span></span>

<span data-ttu-id="5ada2-1003">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-1003">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-1004">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-1004">Example</span></span>

```c
/* Create session.  */
status = nx_lwm2m_client_session_create(&session, &lwm2m_client, session_callback);

/* If status is NX_SUCCESS, a session was successfully created.  */
```

## <a name="nx_lwm2m_client_session_delete"></a><span data-ttu-id="5ada2-1005">nx_lwm2m_client_session_delete</span><span class="sxs-lookup"><span data-stu-id="5ada2-1005">nx_lwm2m_client_session_delete</span></span>

<span data-ttu-id="5ada2-1006">Elimina uma Sessão de Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1006">Deletes a LWM2M Client Session.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-1007">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-1007">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="5ada2-1008">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-1008">Description</span></span>

<span data-ttu-id="5ada2-1009">Este serviço elimina uma Sessão de Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1009">This service deletes a LWM2M Client Session.</span></span>

<span data-ttu-id="5ada2-1010">Quando um Cliente LWM2M é eliminado ligando nx_lwm2m_client_delete todas as sessões anexas ao cliente também são eliminadas.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1010">When a LWM2M Client is deleted by calling nx_lwm2m_client_delete all sessions attached to the client are also deleted.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-1011">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-1011">Parameters</span></span>

- <span data-ttu-id="5ada2-1012">**session_ptr** Ponteiro para o bloco de controlo de sessão de cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1012">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-1013">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-1013">Return Values</span></span>

- <span data-ttu-id="5ada2-1014">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1014">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-1015">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1015">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-1016">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-1016">Allowed From</span></span>

<span data-ttu-id="5ada2-1017">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-1017">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-1018">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-1018">Example</span></span>

```c
/* Delete session.  */
status = nx_lwm2m_client_session_delete(&session);

/* If status is NX_SUCCESS, a session was successfully deleted.  */
```

## <a name="nx_lwm2m_client_session_deregister"></a><span data-ttu-id="5ada2-1019">nx_lwm2m_client_session_deregister</span><span class="sxs-lookup"><span data-stu-id="5ada2-1019">nx_lwm2m_client_session_deregister</span></span>

<span data-ttu-id="5ada2-1020">Termina uma sessão com um Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1020">Terminates a session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-1021">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-1021">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="5ada2-1022">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-1022">Description</span></span>

<span data-ttu-id="5ada2-1023">Este serviço executa uma operação 'De-Register' para um Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1023">This service performs a ‘De-Register’ operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-1024">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-1024">Parameters</span></span>

- <span data-ttu-id="5ada2-1025">**session_ptr** Ponteiro para o bloco de controlo de sessão de cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1025">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-1026">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-1026">Return Values</span></span>

- <span data-ttu-id="5ada2-1027">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1027">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-1028">**NX_LWM2M_CLIENT_NOT_REGISTERED** O cliente não está registado no servidor.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1028">**NX_LWM2M_CLIENT_NOT_REGISTERED** The client is not registered to the server.</span></span>
- <span data-ttu-id="5ada2-1029">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1029">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-1030">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-1030">Allowed From</span></span>

<span data-ttu-id="5ada2-1031">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-1031">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-1032">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-1032">Example</span></span>

```c
/* De-register session.  */
status = nx_lwm2m_client_session_deregister(&session);

/* If status is NX_SUCCESS, session was successfully de-registered.  */
```

## <a name="nx_lwm2m_client_session_error_get"></a><span data-ttu-id="5ada2-1033">nx_lwm2m_client_session_error_get</span><span class="sxs-lookup"><span data-stu-id="5ada2-1033">nx_lwm2m_client_session_error_get</span></span>

<span data-ttu-id="5ada2-1034">Obtém o último erro de uma sessão.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1034">Gets the last error of a session.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-1035">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-1035">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="5ada2-1036">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-1036">Description</span></span>

<span data-ttu-id="5ada2-1037">Este serviço devolve o código de erro da sessão quando a sessão está num estado de erro.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1037">This service returns the error code of the session when the session is in an error state.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-1038">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-1038">Parameters</span></span>

- <span data-ttu-id="5ada2-1039">**session_ptr** Ponteiro para o bloco de controlo de sessão de cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1039">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-1040">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-1040">Return Values</span></span>

- <span data-ttu-id="5ada2-1041">**NX_SUCCESS** A sessão não está em estado de erro.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1041">**NX_SUCCESS** The session is not in error state.</span></span>
- <span data-ttu-id="5ada2-1042">**NX_LWM2M_CLIENT_ADDRESS_ERROR** Endereço de servidor inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1042">**NX_LWM2M_CLIENT_ADDRESS_ERROR** Invalid server address.</span></span>
- <span data-ttu-id="5ada2-1043">**NX_LWM2M_ CLIENT_BUFFER_TOO_SMALL** A carga de pedido não se encaixa no tampão da rede.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1043">**NX_LWM2M_ CLIENT_BUFFER_TOO_SMALL** Payload of request doesn’t fit in network buffer.</span></span>
- <span data-ttu-id="5ada2-1044">**NX_LWM2M_ CLIENT_DTLS_ERROR** Não conseguiu estabelecer uma ligação segura com o servidor.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1044">**NX_LWM2M_ CLIENT_DTLS_ERROR** Failed to establish secured connection with server.</span></span>
- <span data-ttu-id="5ada2-1045">**NX_LWM2M_ CLIENT_ERROR** Erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1045">**NX_LWM2M_ CLIENT_ERROR** Unspecified error.</span></span>
- <span data-ttu-id="5ada2-1046">**NX_LWM2M_ CLIENT_FORBIDDEN** Registo recusado pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1046">**NX_LWM2M_ CLIENT_FORBIDDEN** Registration refused by server.</span></span>
- <span data-ttu-id="5ada2-1047">**NX_LWM2M_ CLIENT_NOT_FOUND** Cliente não encontrado pelo servidor ao atualizar/desregissar.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1047">**NX_LWM2M_ CLIENT_NOT_FOUND** Client not found by server when updating/deregistering.</span></span>
- <span data-ttu-id="5ada2-1048">**NX_LWM2M_ CLIENT_SERVER_INSTANCE_DELETED** A instância do objeto do servidor correspondente à sessão foi eliminada.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1048">**NX_LWM2M_ CLIENT_SERVER_INSTANCE_DELETED** The Server Object Instance corresponding to the session has been deleted.</span></span>
- <span data-ttu-id="5ada2-1049">**NX_LWM2M_ CLIENT_TIMED_OUT** Sem resposta do servidor.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1049">**NX_LWM2M_ CLIENT_TIMED_OUT** No answer from server.</span></span>
- <span data-ttu-id="5ada2-1050">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1050">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-1051">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-1051">Allowed From</span></span>

<span data-ttu-id="5ada2-1052">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-1052">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-1053">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-1053">Example</span></span>

```c
/* Get the error.  */
status = nx_lwm2m_client_session_error_get(&session);
```
## <a name="nx_lwm2m_client_session_register"></a><span data-ttu-id="5ada2-1054">nx_lwm2m_client_session_register</span><span class="sxs-lookup"><span data-stu-id="5ada2-1054">nx_lwm2m_client_session_register</span></span>

<span data-ttu-id="5ada2-1055">Inicia uma sessão com um Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1055">Starts a session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-1056">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-1056">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port);
```


### <a name="description"></a><span data-ttu-id="5ada2-1057">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-1057">Description</span></span>

<span data-ttu-id="5ada2-1058">Este serviço executa uma operação 'Registar' para um Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1058">This service performs a ‘Register’ operation to a LWM2M Server.</span></span> <span data-ttu-id="5ada2-1059">O servidor deve ter uma instância de servidor correspondente no Objeto do Servidor.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1059">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="5ada2-1060">Se o registo for bem sucedido, o Cliente LWM2M processará novas operações a partir do servidor e enviará periodicamente mensagens de 'Update' até que o cliente seja descista.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1060">If the registration is successfully the LWM2M Client will process further operations from the server and will periodically send ‘Update’ messages until the client is de-registered.</span></span>

<span data-ttu-id="5ada2-1061">Qualquer sessão ativa atual é abortada por esta chamada e substituída pela nova sessão do Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1061">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-1062">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-1062">Parameters</span></span>

- <span data-ttu-id="5ada2-1063">**session_ptr** Ponteiro para o bloco de controlo de sessão de cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1063">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="5ada2-1064">**server_id** O ID do Servidor Curto do Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1064">**server_id** The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="5ada2-1065">**ip_address** O endereço IP do servidor.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1065">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="5ada2-1066">**porto** A porta UDP do servidor.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1066">**port** The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-1067">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-1067">Return Values</span></span>

- <span data-ttu-id="5ada2-1068">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1068">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-1069">**NX_LWM2M_CLIENT_ERROR** Erro de botas.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1069">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="5ada2-1070">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** A porta não está disponível.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1070">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="5ada2-1071">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1071">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-1072">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-1072">Allowed From</span></span>

<span data-ttu-id="5ada2-1073">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-1073">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-1074">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-1074">Example</span></span>

```c
/* Start register.  */
status = nx_lwm2m_client_session_register (&lwm2m_client, 123, &ip_address, 5683);

/* If status is NX_SUCCESS, start register successfully.  */
```

## <a name="nx_lwm2m_client_session_register_dtls"></a><span data-ttu-id="5ada2-1075">nx_lwm2m_client_session_register_dtls</span><span class="sxs-lookup"><span data-stu-id="5ada2-1075">nx_lwm2m_client_session_register_dtls</span></span>

<span data-ttu-id="5ada2-1076">Inicia uma sessão segura com um Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1076">Starts a secure session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-1077">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-1077">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port,
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a><span data-ttu-id="5ada2-1078">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-1078">Description</span></span>

<span data-ttu-id="5ada2-1079">Este serviço executa uma operação 'Register' para um Servidor LWM2M utilizando uma ligação DTLS segura.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1079">This service performs a ‘Register’ operation to a LWM2M Server using a secure DTLS connection.</span></span> <span data-ttu-id="5ada2-1080">O servidor deve ter uma instância de servidor correspondente no Objeto do Servidor.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1080">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="5ada2-1081">A sessão DTLS deve ter sido configurada com as suites de cifra adequadas e material chave antes de chamar esta função.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1081">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="5ada2-1082">**NX_SECURE_ENABLE_DTLS** deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1082">**NX_SECURE_ENABLE_DTLS** must be defined.</span></span>

<span data-ttu-id="5ada2-1083">Se o registo for bem sucedido, o Cliente LWM2M processará novas operações a partir do servidor e enviará periodicamente mensagens de 'Update' até que o cliente seja descista.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1083">If the registration is successfully the LWM2M Client will process further operations from the server and will periodically send ‘Update’ messages until the client is de-registered.</span></span>

<span data-ttu-id="5ada2-1084">Qualquer sessão ativa atual é abortada por esta chamada e substituída pela nova sessão do Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1084">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-1085">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-1085">Parameters</span></span>

- <span data-ttu-id="5ada2-1086">**session_ptr** Ponteiro para o bloco de controlo de sessão de cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1086">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="5ada2-1087">**server_id** O ID do Servidor Curto do Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1087">**server_id** The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="5ada2-1088">**ip_address** O endereço IP do servidor.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1088">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="5ada2-1089">**porto** A porta UDP do servidor.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1089">**port** The UDP port of the server.</span></span>
- <span data-ttu-id="5ada2-1090">**dtls_session_ptr** A sessão DTLS para utilizar para a sessão LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1090">**dtls_session_ptr** The DTLS session to use for the LWM2M session.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-1091">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-1091">Return Values</span></span>

- <span data-ttu-id="5ada2-1092">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1092">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-1093">**NX_LWM2M_CLIENT_ERROR** Erro de botas.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1093">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="5ada2-1094">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** A porta não está disponível.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1094">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="5ada2-1095">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1095">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-1096">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-1096">Allowed From</span></span>

<span data-ttu-id="5ada2-1097">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-1097">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-1098">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-1098">Example</span></span>

```c
/* Start register with DTLS.  */
status = nx_lwm2m_client_session_register_dtls(&lwm2m_client, 123, &ip_address, 5683, &dtls_session);

/* If status is NX_SUCCESS, start register with DTLS successfully.  */
```

## <a name="nx_lwm2m_client_session_register_info_get"></a><span data-ttu-id="5ada2-1099">nx_lwm2m_client_session_register_info_get</span><span class="sxs-lookup"><span data-stu-id="5ada2-1099">nx_lwm2m_client_session_register_info_get</span></span>

<span data-ttu-id="5ada2-1100">Inicia uma sessão segura com um Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1100">Starts a secure session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-1101">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-1101">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    UINT security_instance_id, 
    NX_LWM2M_ID *server_id,
    CHAR **server_uri, 
    UINT *server_uri_length, 
    UCHAR *security_mode, 
    UCHAR **pub_key_or_id, 
    UINT *pub_key_or_id_len, 
    UCHAR **server_pub_key, 
    UINT *server_pub_key_len, 
    UCHAR **secret_key, 
    UINT *secret_key_len);
```

### <a name="description"></a><span data-ttu-id="5ada2-1102">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-1102">Description</span></span>

<span data-ttu-id="5ada2-1103">Uma vez estabelecida uma sessão de comunicação com um servidor Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1103">Once a communication session with a Bootstrap server was established.</span></span> <span data-ttu-id="5ada2-1104">A aplicação pode ligar para esta api para obter o servidor e informações de segurança para o próximo passo de registo.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1104">Application can call this api to get the server and security information for the next registration step.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-1105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-1105">Parameters</span></span>

- <span data-ttu-id="5ada2-1106">**session_ptr** Ponteiro para o bloco de controlo de sessão de cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1106">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="5ada2-1107">**security_instance_id** Identificação de instância de segurança.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1107">**security_instance_id** Security instance ID.</span></span>
- <span data-ttu-id="5ada2-1108">**server_id** Ponteiro para o ID do servidor de destino.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1108">**server_id** Pointer to destination server ID.</span></span>
- <span data-ttu-id="5ada2-1109">**server_uri** Ponteiro para o servidor de destino uri.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1109">**server_uri** Pointer to destination server uri.</span></span>
- <span data-ttu-id="5ada2-1110">**server_uri_len** Ponteiro para o destino servidor uri comprimento.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1110">**server_uri_len** Pointer to destination server uri length.</span></span>
- <span data-ttu-id="5ada2-1111">**security_mode** Ponteiro para o modo de segurança de destino.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1111">**security_mode** Pointer to destination security mode.</span></span>
- <span data-ttu-id="5ada2-1112">**pub_key_or_id** Ponteiro para destino chave ou identidade pública de destino.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1112">**pub_key_or_id** Pointer to destination public key or identity.</span></span>
- <span data-ttu-id="5ada2-1113">**pub_key_or_id_len** Ponteiro para destino chave pública ou comprimento de identidade.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1113">**pub_key_or_id_len** Pointer to destination public key or identity length.</span></span>
- <span data-ttu-id="5ada2-1114">**server_pub_key** Ponteiro para a chave pública do servidor de destino.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1114">**server_pub_key** Pointer to destination server public key.</span></span>
- <span data-ttu-id="5ada2-1115">**server_pub_key_len** Ponteiro para o comprimento da chave pública do servidor de destino.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1115">**server_pub_key_len** Pointer to destination server public key length.</span></span>
- <span data-ttu-id="5ada2-1116">**secret_key** Ponteiro para a chave secreta do destino.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1116">**secret_key** Pointer to destination secret key.</span></span>
- <span data-ttu-id="5ada2-1117">**secret_key_len** Ponteiro para o comprimento da chave secreta do destino.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1117">**secret_key_len** Pointer to destination secret key length.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-1118">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-1118">Return Values</span></span>

- <span data-ttu-id="5ada2-1119">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1119">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-1120">**NX_LWM2M_CLIENT_NOT_FOUND** Não há nenhuma instância de segurança.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1120">**NX_LWM2M_CLIENT_NOT_FOUND** There is no security Object instance.</span></span>
- <span data-ttu-id="5ada2-1121">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1121">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-1122">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-1122">Allowed From</span></span>

<span data-ttu-id="5ada2-1123">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-1123">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-1124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-1124">Example</span></span>

```c
/* Get the register information.  */
status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_length, &security_mode, &pub_key_or_id, &pub_key_or_id_len, NX_NULL, NX_NULL, &secret_key, &secret_key_len);

/* If status is NX_SUCCESS, the register information was successfully gotten.  */
```

## <a name="nx_lwm2m_client_session_update"></a><span data-ttu-id="5ada2-1125">nx_lwm2m_client_session_update</span><span class="sxs-lookup"><span data-stu-id="5ada2-1125">nx_lwm2m_client_session_update</span></span>

<span data-ttu-id="5ada2-1126">Atualiza uma sessão com um Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1126">Updates a session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-1127">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-1127">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="5ada2-1128">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-1128">Description</span></span>

<span data-ttu-id="5ada2-1129">Este serviço executa uma operação 'Update' para um Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1129">This service performs an ‘Update’ operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-1130">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-1130">Parameters</span></span>

- <span data-ttu-id="5ada2-1131">**session_ptr** Ponteiro para o bloco de controlo de sessão de cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1131">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-1132">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-1132">Return Values</span></span>

- <span data-ttu-id="5ada2-1133">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1133">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-1134">**NX_LWM2M_CLIENT_NOT_REGISTERED** O cliente não está registado no servidor.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1134">**NX_LWM2M_CLIENT_NOT_REGISTERED** The client is not registered to the server.</span></span>
- <span data-ttu-id="5ada2-1135">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1135">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-1136">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-1136">Allowed From</span></span>

<span data-ttu-id="5ada2-1137">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-1137">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-1138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-1138">Example</span></span>

```c
/* Update a session.  */
status = nx_lwm2m_client_session_update(&session);

/* If status is NX_SUCCESS, a session was successfully updated.  */
```

## <a name="nx_lwm2m_client_unlock"></a><span data-ttu-id="5ada2-1139">nx_lwm2m_client_unlock</span><span class="sxs-lookup"><span data-stu-id="5ada2-1139">nx_lwm2m_client_unlock</span></span>

<span data-ttu-id="5ada2-1140">Desbloqueia um Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1140">Unlocks a LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="5ada2-1141">Prototype</span><span class="sxs-lookup"><span data-stu-id="5ada2-1141">Prototype</span></span>

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="5ada2-1142">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ada2-1142">Description</span></span>

<span data-ttu-id="5ada2-1143">Este serviço desbloqueia o Cliente LWM2M previamente bloqueado por uma chamada para ***nx_lwm2m_client_unlock***.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1143">This service unlocks the LWM2M Client previously locked by a call to ***nx_lwm2m_client_unlock***.</span></span>

### <a name="parameters"></a><span data-ttu-id="5ada2-1144">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ada2-1144">Parameters</span></span>

- <span data-ttu-id="5ada2-1145">**client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1145">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="5ada2-1146">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5ada2-1146">Return Values</span></span>

- <span data-ttu-id="5ada2-1147">**NX_SUCCESS** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1147">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="5ada2-1148">**NX_PTR_ERROR** Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5ada2-1148">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5ada2-1149">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5ada2-1149">Allowed From</span></span>

<span data-ttu-id="5ada2-1150">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="5ada2-1150">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5ada2-1151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ada2-1151">Example</span></span>

```c
/* Unlock lwm2m client.  */
status = nx_lwm2m_client_unlock(&lwm2m_client);

/* If status is NX_SUCCESS, unlock lwm2m client successfully.  */
```