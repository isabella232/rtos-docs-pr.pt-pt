---
title: Capítulo 4 - Descrição dos serviços Azure RTOS NetX LWM2M
description: Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX LWM2M (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d5a402790387c2720db304fe93d74252494d7638
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826672"
---
# <a name="chapter-4---description-of-azure-rtos-netx-lwm2m-services"></a><span data-ttu-id="6e366-103">Capítulo 4 - Descrição dos serviços Azure RTOS NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="6e366-103">Chapter 4 - Description of Azure RTOS NetX LWM2M services</span></span>

<span data-ttu-id="6e366-104">Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX LWM2M (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="6e366-104">This chapter contains a description of all Azure RTOS NetX LWM2M services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="6e366-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="6e366-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

### <a name="lwm2m-client-management"></a><span data-ttu-id="6e366-106">Gestão de Clientes LWM2M</span><span class="sxs-lookup"><span data-stu-id="6e366-106">LWM2M Client Management</span></span>

- <span data-ttu-id="6e366-107">**nx_lwm2m_client_create**: *Criar cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6e366-107">**nx_lwm2m_client_create**: *Create LWM2M Client*</span></span>
- <span data-ttu-id="6e366-108">**nx_lwm2m_client_delete**: *Eliminar cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6e366-108">**nx_lwm2m_client_delete**: *Delete LWM2M Client*</span></span>
- <span data-ttu-id="6e366-109">**nx_lwm2m_client_lock**: *Bloquear cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6e366-109">**nx_lwm2m_client_lock**: *Lock LWM2M Client*</span></span>
- <span data-ttu-id="6e366-110">**nx_lwm2m_client_object_add**: *Adicionar implementação de objeto ao Cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6e366-110">**nx_lwm2m_client_object_add**: *Add Object implementation to the LWM2M Client*</span></span>
- <span data-ttu-id="6e366-111">**nx_lwm2m_client_unlock**: *Desbloquear Cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6e366-111">**nx_lwm2m_client_unlock**: *Unlock LWM2M Client*</span></span>

### <a name="lwm2m-client-session-management"></a><span data-ttu-id="6e366-112">Gestão de Sessão de Clientes LWM2M</span><span class="sxs-lookup"><span data-stu-id="6e366-112">LWM2M Client Session Management</span></span>

- <span data-ttu-id="6e366-113">**nx_lwm2m_client_session_bootstrap**: *Inicie uma sessão com um Servidor Bootstrap*</span><span class="sxs-lookup"><span data-stu-id="6e366-113">**nx_lwm2m_client_session_bootstrap**: *Start a session with a Bootstrap Server*</span></span>
- <span data-ttu-id="6e366-114">**nx_lwm2m_client_session_bootstrap_dtls**: *Inicie uma sessão segura com um Servidor Bootstrap*</span><span class="sxs-lookup"><span data-stu-id="6e366-114">**nx_lwm2m_client_session_bootstrap_dtls**: *Start a secure session with a Bootstrap Server*</span></span>
- <span data-ttu-id="6e366-115">**nx_lwm2m_client_session_create**: *Criar sessão de clientes LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6e366-115">**nx_lwm2m_client_session_create**: *Create LWM2M Client Session*</span></span>
- <span data-ttu-id="6e366-116">**nx_lwm2m_client_session_delete**: *Eliminar sessão de clientes LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6e366-116">**nx_lwm2m_client_session_delete**: *Delete LWM2M Client Session*</span></span>
- <span data-ttu-id="6e366-117">**nx_lwm2m_client_session_deregister**: *Terminar uma sessão com um Servidor LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6e366-117">**nx_lwm2m_client_session_deregister**: *Terminate a session with a LWM2M Server*</span></span>
- <span data-ttu-id="6e366-118">**nx_lwm2m_client_session_error_get**: *Obtenha o último erro de uma sessão*</span><span class="sxs-lookup"><span data-stu-id="6e366-118">**nx_lwm2m_client_session_error_get**: *Get last error of a session*</span></span>
- <span data-ttu-id="6e366-119">**nx_lwm2m_client_session_register**: *Inicie uma sessão com um Servidor LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6e366-119">**nx_lwm2m_client_session_register**: *Start a session with a LWM2M Server*</span></span>
- <span data-ttu-id="6e366-120">**nx_lwm2m_client_session_register_dtls**: *Inicie uma sessão segura com um Servidor LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6e366-120">**nx_lwm2m_client_session_register_dtls**: *Start a secure session with a LWM2M Server*</span></span>
- <span data-ttu-id="6e366-121">**nx_lwm2m_client_session_update**: *Atualizar uma sessão com um Servidor LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6e366-121">**nx_lwm2m_client_session_update**: *Update a session with a LWM2M Server*</span></span>

### <a name="security-object-implementation"></a><span data-ttu-id="6e366-122">Implementação de objetos de segurança</span><span class="sxs-lookup"><span data-stu-id="6e366-122">Security Object Implementation</span></span>

- <span data-ttu-id="6e366-123">**nx_lwm2m_client_security_key_callbacks_set**: *Definir chamadas de gestão de chaves de segurança*</span><span class="sxs-lookup"><span data-stu-id="6e366-123">**nx_lwm2m_client_security_key_callbacks_set**: *Set security key management callbacks*</span></span>

### <a name="device-object-implementation"></a><span data-ttu-id="6e366-124">Implementação de objetos de dispositivo</span><span class="sxs-lookup"><span data-stu-id="6e366-124">Device Object Implementation</span></span>

- <span data-ttu-id="6e366-125">**nx_lwm2m_client_device_callbacks_set**: *Definir chamadas de aplicação de objeto de dispositivo*</span><span class="sxs-lookup"><span data-stu-id="6e366-125">**nx_lwm2m_client_device_callbacks_set**: *Set Device Object application callbacks*</span></span>
- <span data-ttu-id="6e366-126">**nx_lwm2m_client_device_error_push**: *Adicione código de erro ao objeto do dispositivo*</span><span class="sxs-lookup"><span data-stu-id="6e366-126">**nx_lwm2m_client_device_error_push**: *Add error code to Device Object*</span></span>
- <span data-ttu-id="6e366-127">**nx_lwm2m_client_device_error_reset**: *Redefinir códigos de erro do objeto do dispositivo*</span><span class="sxs-lookup"><span data-stu-id="6e366-127">**nx_lwm2m_client_device_error_reset**: *Reset error codes of Device Object*</span></span>
- <span data-ttu-id="6e366-128">**nx_lwm2m_client_device_resource_changed**: Alteração *do sinal do recurso objeto de dispositivo*</span><span class="sxs-lookup"><span data-stu-id="6e366-128">**nx_lwm2m_client_device_resource_changed**: *Signal change of Device Object resource*</span></span>

### <a name="custom-objects-implementation"></a><span data-ttu-id="6e366-129">Implementação de objetos personalizados</span><span class="sxs-lookup"><span data-stu-id="6e366-129">Custom Objects Implementation</span></span>

- <span data-ttu-id="6e366-130">**nx_lwm2m_object_resource_changed**: *Alteração do sinal de um valor de recurso de uma Instância de Objeto*</span><span class="sxs-lookup"><span data-stu-id="6e366-130">**nx_lwm2m_object_resource_changed**: *Signal change of a resource value of an Object Instance*</span></span>

### <a name="local-device-management"></a><span data-ttu-id="6e366-131">Gestão local de dispositivos</span><span class="sxs-lookup"><span data-stu-id="6e366-131">Local Device Management</span></span>

- <span data-ttu-id="6e366-132">**nx_lwm2m_client_object_create**: *Criar uma nova instância de objeto*</span><span class="sxs-lookup"><span data-stu-id="6e366-132">**nx_lwm2m_client_object_create**: *Create a new Object Instance*</span></span>
- <span data-ttu-id="6e366-133">**nx_lwm2m_client_object_delete**: *Eliminar uma instância de objeto*</span><span class="sxs-lookup"><span data-stu-id="6e366-133">**nx_lwm2m_client_object_delete**: *Delete an Object Instance*</span></span>
- <span data-ttu-id="6e366-134">**nx_lwm2m_client_object_discover**: *Descubra os recursos de uma instância de objeto*</span><span class="sxs-lookup"><span data-stu-id="6e366-134">**nx_lwm2m_client_object_discover**: *Discover resources of an Object Instance*</span></span>
- <span data-ttu-id="6e366-135">**nx_lwm2m_client_object_execute**: *Executar recurso de uma instância de objeto*</span><span class="sxs-lookup"><span data-stu-id="6e366-135">**nx_lwm2m_client_object_execute**: *Execute resource of an Object Instance*</span></span>
- <span data-ttu-id="6e366-136">**nx_lwm2m_client_object_get_next**: *Obtenha a lista de Objetos implementados pelo Cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="6e366-136">**nx_lwm2m_client_object_get_next**: *Get the list of Objects implemented by the LWM2M Client*</span></span>
- <span data-ttu-id="6e366-137">**nx_lwm2m_client_object_instance_get_next**: *Obtenha a lista de instâncias de um objeto*</span><span class="sxs-lookup"><span data-stu-id="6e366-137">**nx_lwm2m_client_object_instance_get_next**: *Get the list of Instances of an Object*</span></span>
- <span data-ttu-id="6e366-138">**nx_lwm2m_client_object_read**: *Leia os valores dos recursos de uma Instância de Objeto*</span><span class="sxs-lookup"><span data-stu-id="6e366-138">**nx_lwm2m_client_object_read**: *Read resources values of an Object Instance*</span></span>
- <span data-ttu-id="6e366-139">**nx_lwm2m_client_object_write**: *Alterar os valores de recursos de uma instância de objeto*</span><span class="sxs-lookup"><span data-stu-id="6e366-139">**nx_lwm2m_client_object_write**: *Change resources values of an Object instance*</span></span>

### <a name="resources-values-decoding"></a><span data-ttu-id="6e366-140">Descodagem de Valores de Recursos</span><span class="sxs-lookup"><span data-stu-id="6e366-140">Resources Values Decoding</span></span>

- <span data-ttu-id="6e366-141">**nx_lwm2m_resource_get_boolean**: *Obtenha o valor de um Recurso Boolean*</span><span class="sxs-lookup"><span data-stu-id="6e366-141">**nx_lwm2m_resource_get_boolean**: *Get the value of a Boolean Resource*</span></span>
- <span data-ttu-id="6e366-142">**nx_lwm2m_resource_get_float32**: *Obtenha o valor de um recurso de ponto flutuante de 32 bits*</span><span class="sxs-lookup"><span data-stu-id="6e366-142">**nx_lwm2m_resource_get_float32**: *Get the value of a 32-bit Floating Point Resource*</span></span>
- <span data-ttu-id="6e366-143">**nx_lwm2m_resource_get_float64**: *Obtenha o valor de um recurso de ponto flutuante de 64 bits*</span><span class="sxs-lookup"><span data-stu-id="6e366-143">**nx_lwm2m_resource_get_float64**: *Get the value of a 64-bit Floating Point Resource*</span></span>
- <span data-ttu-id="6e366-144">**nx_lwm2m_resource_get_integer32**: *Obtenha o valor de um recurso inteiro de 32 bits*</span><span class="sxs-lookup"><span data-stu-id="6e366-144">**nx_lwm2m_resource_get_integer32**: *Get the value of a 32-Bit Integer Resource*</span></span>
- <span data-ttu-id="6e366-145">**nx_lwm2m_resource_get_integer64**: *Obtenha o valor de um recurso inteiro de 64 bits*</span><span class="sxs-lookup"><span data-stu-id="6e366-145">**nx_lwm2m_resource_get_integer64**: *Get the value of a 64-Bit Integer Resource*</span></span>
- <span data-ttu-id="6e366-146">**nx_lwm2m_resource_get_objlnk**: *Obtenha o valor de um recurso de ligação de objeto*</span><span class="sxs-lookup"><span data-stu-id="6e366-146">**nx_lwm2m_resource_get_objlnk**: *Get the value of an Object Link Resource*</span></span>
- <span data-ttu-id="6e366-147">**nx_lwm2m_resource_get_opaque**: *Obtenha o valor de um Recurso Opaco*</span><span class="sxs-lookup"><span data-stu-id="6e366-147">**nx_lwm2m_resource_get_opaque**: *Get the value of an Opaque Resource*</span></span>
- <span data-ttu-id="6e366-148">**nx_lwm2m_resource_get_string**: *Obtenha o valor de um recurso de corda*</span><span class="sxs-lookup"><span data-stu-id="6e366-148">**nx_lwm2m_resource_get_string**: *Get the value of a String Resource*</span></span>
- <span data-ttu-id="6e366-149">**nx_lwm2m_resource_multiple_get_boolean**: *Obtenha o valor de uma instância de recursos múltiplos de recurso boolean*</span><span class="sxs-lookup"><span data-stu-id="6e366-149">**nx_lwm2m_resource_multiple_get_boolean**: *Get the value of a Boolean Resource Multiple Resource Instance*</span></span>
- <span data-ttu-id="6e366-150">**nx_lwm2m_resource_multiple_get_float32**: *Obtenha o valor de uma instância de recursos múltiplos de ponto flutuante de 32 bits*</span><span class="sxs-lookup"><span data-stu-id="6e366-150">**nx_lwm2m_resource_multiple_get_float32**: *Get the value of a 32-bit Floating Point Multiple Resource Instance*</span></span>
- <span data-ttu-id="6e366-151">**nx_lwm2m_resource_multiple_get_float64**: *Obtenha o valor de uma instância de recursos múltiplos de ponto flutuante de 64 bits*</span><span class="sxs-lookup"><span data-stu-id="6e366-151">**nx_lwm2m_resource_multiple_get_float64**: *Get the value of a 64-bit Floating Point Multiple Resource Instance*</span></span>
- <span data-ttu-id="6e366-152">**nx_lwm2m_resource_multiple_get_integer32**: *Obtenha o valor de uma instância de recursos múltiplos de 32 bits*</span><span class="sxs-lookup"><span data-stu-id="6e366-152">**nx_lwm2m_resource_multiple_get_integer32**: *Get the value of a 32-Bit Integer Multiple Resource Instance*</span></span>
- <span data-ttu-id="6e366-153">**nx_lwm2m_resource_multiple_get_integer64**: *Obtenha o valor de uma instância de recursos múltiplos de 64 bits*</span><span class="sxs-lookup"><span data-stu-id="6e366-153">**nx_lwm2m_resource_multiple_get_integer64**: *Get the value of a 64-Bit Integer Multiple Resource Instance*</span></span>
- <span data-ttu-id="6e366-154">**nx_lwm2m_resource_multiple_get_objlnk**: *Obtenha o valor de uma instância de recursos múltiplos de ligação de objetos*</span><span class="sxs-lookup"><span data-stu-id="6e366-154">**nx_lwm2m_resource_multiple_get_objlnk**: *Get the value of an Object Link Multiple Resource Instance*</span></span>
- <span data-ttu-id="6e366-155">**nx_lwm2m_resource_multiple_get_opaque**: *Obtenha o valor de uma instância de recursos múltiplos opaco*</span><span class="sxs-lookup"><span data-stu-id="6e366-155">**nx_lwm2m_resource_multiple_get_opaque**: *Get the value of an Opaque Multiple Resource Instance*</span></span>
- <span data-ttu-id="6e366-156">**nx_lwm2m_resource_multiple_get_string**: *Obtenha o valor de uma instância de recursos múltiplos de cordas*</span><span class="sxs-lookup"><span data-stu-id="6e366-156">**nx_lwm2m_resource_multiple_get_string**: *Get the value of a String Multiple Resource Instance*</span></span>

### <a name="firmware-update-object"></a><span data-ttu-id="6e366-157">Objeto de atualização de firmware</span><span class="sxs-lookup"><span data-stu-id="6e366-157">Firmware Update Object</span></span>

- <span data-ttu-id="6e366-158">**nx_lwm2m_firmware_create**: *Criar objeto de atualização de firmware*</span><span class="sxs-lookup"><span data-stu-id="6e366-158">**nx_lwm2m_firmware_create**: *Create Firmware Update Object*</span></span>
- <span data-ttu-id="6e366-159">**nx_lwm2m_firmware_package_info_set**: Definir informações do *pacote de atualização de firmware*</span><span class="sxs-lookup"><span data-stu-id="6e366-159">**nx_lwm2m_firmware_package_info_set**: *Set Firmware Update Package Information*</span></span>
- <span data-ttu-id="6e366-160">**nx_lwm2m_firmware_result_set**: *Definir resultado da atualização do firmware*</span><span class="sxs-lookup"><span data-stu-id="6e366-160">**nx_lwm2m_firmware_result_set**: *Set Firmware Update Result*</span></span>
- <span data-ttu-id="6e366-161">**nx_lwm2m_firmware_state_set**: *Definir Estado de atualização de firmware*</span><span class="sxs-lookup"><span data-stu-id="6e366-161">**nx_lwm2m_firmware_state_set**: *Set Firmware Update State*</span></span>

## <a name="nx_lwm2m_client_create"></a><span data-ttu-id="6e366-162">nx_lwm2m_client_create</span><span class="sxs-lookup"><span data-stu-id="6e366-162">nx_lwm2m_client_create</span></span>

<span data-ttu-id="6e366-163">Criar cliente LWM2M</span><span class="sxs-lookup"><span data-stu-id="6e366-163">Create LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-164">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-164">Prototype</span></span>

```c
UINT nx_lwm2m_client_create(NX_LWM2M_CLIENT *client_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr, UINT local_port, const CHAR *name_ptr,
    const CHAR *msisdn_ptr, UCHAR binding_modes, VOID *stack_ptr, ULONG stack_size);
```

### <a name="description"></a><span data-ttu-id="6e366-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-165">Description</span></span>

<span data-ttu-id="6e366-166">Este serviço cria uma instância de cliente LWM2M, que funciona no contexto da sua própria linha ThreadX.</span><span class="sxs-lookup"><span data-stu-id="6e366-166">This service creates a LWM2M Client instance, which runs in the context of its own ThreadX thread.</span></span>

<span data-ttu-id="6e366-167">O Cliente LWM2M implementa os seguintes objetos OMA LWM2M: Segurança (0), Servidor (1), Controlo de Acesso (2) e Dispositivo (3).</span><span class="sxs-lookup"><span data-stu-id="6e366-167">The LWM2M Client implements the following OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="6e366-168">As implementações dos outros objetos devem ser adicionadas pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="6e366-168">The other objects implementations must be added by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-169">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-169">Parameters</span></span>

- <span data-ttu-id="6e366-170">**client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-170">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6e366-171">**ip_ptr**: Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="6e366-171">**ip_ptr**: Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="6e366-172">**packet_pool_ptr**: Ponter para a piscina de pacotes predefinidos para este Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-172">**packet_pool_ptr**: Pointer to the default packet pool for this LWM2M Client.</span></span>
- <span data-ttu-id="6e366-173">**local_port**: A porta UDP local utilizada para comunicação não segura.</span><span class="sxs-lookup"><span data-stu-id="6e366-173">**local_port**: The local UDP port used for non-secure communication.</span></span>
- <span data-ttu-id="6e366-174">**name_ptr**: Ponteiro para o nome final do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-174">**name_ptr**: Pointer to LWM2M Client endpoint name.</span></span>
- <span data-ttu-id="6e366-175">**msisdn_ptr**: Ponte rumo ao MSISDN onde o Cliente LWM2M pode ser contactado para ser utilizado com a ligação SMS, pode ser NU SE a ligação SMS não for suportada.</span><span class="sxs-lookup"><span data-stu-id="6e366-175">**msisdn_ptr**: Pointer to the MSISDN where the LWM2M Client can be reached for use with the SMS binding, can be NULL if SMS binding is not supported.</span></span>
- <span data-ttu-id="6e366-176">**binding_modes**: A encadernação e os modos suportados pelo Cliente LWM2M devem ser uma combinação de bandeiras de NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S e NX_LWM2M_BINDING_SQ.</span><span class="sxs-lookup"><span data-stu-id="6e366-176">**binding_modes**: The binding and modes supported by the LWM2M Client, must be a combination of NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S and NX_LWM2M_BINDING_SQ flags.</span></span>
- <span data-ttu-id="6e366-177">**stack_ptr**: Ponteiro para a área da pilha de fio do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-177">**stack_ptr**: Pointer to LWM2M Client thread stack area.</span></span>
- <span data-ttu-id="6e366-178">**stack_size**: O tamanho da pilha de fio do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-178">**stack_size**: The LWM2M Client thread stack size.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-179">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-179">Return Values</span></span>

- <span data-ttu-id="6e366-180">**NX_SUCCESS**: O Cliente LWM2M foi criado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="6e366-180">**NX_SUCCESS**: The LWM2M Client has been successfully created.</span></span>
- <span data-ttu-id="6e366-181">**NX_LWM2M_ERROR**: O Cliente LWM2M cria erro.</span><span class="sxs-lookup"><span data-stu-id="6e366-181">**NX_LWM2M_ERROR**: LWM2M Client create error.</span></span>
- <span data-ttu-id="6e366-182">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-182">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_delete"></a><span data-ttu-id="6e366-183">nx_lwm2m_client_delete</span><span class="sxs-lookup"><span data-stu-id="6e366-183">nx_lwm2m_client_delete</span></span>

<span data-ttu-id="6e366-184">Excluir cliente LWM2M</span><span class="sxs-lookup"><span data-stu-id="6e366-184">Delete LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-185">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-185">Prototype</span></span>

```c
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-186">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-186">Description</span></span>

<span data-ttu-id="6e366-187">Este serviço elimina uma instância de cliente LWM2M anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="6e366-187">This service deletes a previously created LWM2M Client instance.</span></span>

<span data-ttu-id="6e366-188">Todas as sessões atualmente anexadas ao cliente também são eliminadas por esta chamada.</span><span class="sxs-lookup"><span data-stu-id="6e366-188">All sessions currently attached the client are also deleted by this call.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-189">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-189">Parameters</span></span>

- <span data-ttu-id="6e366-190">**client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-190">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-191">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-191">Return Values</span></span>

- <span data-ttu-id="6e366-192">**NX_SUCCESS**: O Cliente LWM2M foi eliminado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="6e366-192">**NX_SUCCESS**: The LWM2M Client has been successfully deleted.</span></span>
- <span data-ttu-id="6e366-193">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-193">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_callbacks_set"></a><span data-ttu-id="6e366-194">nx_lwm2m_client_device_callbacks_set</span><span class="sxs-lookup"><span data-stu-id="6e366-194">nx_lwm2m_client_device_callbacks_set</span></span>

<span data-ttu-id="6e366-195">Definir chamadas de aplicação de objeto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="6e366-195">Set Device Object application callbacks</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-196">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-196">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_READ_CALLBACK read_callback,
    NX_LWM2M_CLIENT_DEVICE_DISCOVER_CALLBACK discover_callback,
    NX_LWM2M_CLIENT_DEVICE_WRITE_CALLBACK write_callback,
    NX_LWM2M_CLIENT_DEVICE_EXECUTE_CALLBACK execute_callback);
```

### <a name="description"></a><span data-ttu-id="6e366-197">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-197">Description</span></span>

<span data-ttu-id="6e366-198">Este serviço instala as chamadas de aplicação para implementação de operações nos recursos do Objeto de Dispositivo LWM2M que não são tratados pelo Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-198">This service installs the application callbacks for implementing operations on the LWM2M Device Object resources that are not handled by the LWM2M Client.</span></span>

<span data-ttu-id="6e366-199">O Cliente LWM2M implementa os seguintes recursos : Código de Erro (11), Código de Erro de Reset (12) e Ligação e Modos Suportados (16), as operações para os outros recursos são redirecionadas para a aplicação.</span><span class="sxs-lookup"><span data-stu-id="6e366-199">The LWM2M Client implements the following resources : Error Code (11), Reset Error Code (12) and Supported Binding and Modes (16), operations to the other resources are redirected to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-200">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-200">Parameters</span></span>

- <span data-ttu-id="6e366-201">**client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-201">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6e366-202">**read_callback**: O chamado 'Ler' do método .</span><span class="sxs-lookup"><span data-stu-id="6e366-202">**read_callback**: The 'Read' method callback.</span></span>
- <span data-ttu-id="6e366-203">**discover_callback**: O chamado 'Descobrir'.</span><span class="sxs-lookup"><span data-stu-id="6e366-203">**discover_callback**: The 'Discover' method callback.</span></span>
- <span data-ttu-id="6e366-204">**write_callback**: O chamado devolução do método 'Write'.</span><span class="sxs-lookup"><span data-stu-id="6e366-204">**write_callback**: The 'Write' method callback.</span></span>
- <span data-ttu-id="6e366-205">**execute_callback**: O chamado 'Executar'.</span><span class="sxs-lookup"><span data-stu-id="6e366-205">**execute_callback**: The 'Execute' method callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-206">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-206">Return Values</span></span>

- <span data-ttu-id="6e366-207">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-207">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-208">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-208">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_error_push"></a><span data-ttu-id="6e366-209">nx_lwm2m_client_device_error_push</span><span class="sxs-lookup"><span data-stu-id="6e366-209">nx_lwm2m_client_device_error_push</span></span>

<span data-ttu-id="6e366-210">Adicione código de erro ao objeto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="6e366-210">Add error code to Device Object</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-211">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-211">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_error_push(NX_LWM2M_CLIENT *client_ptr, UCHAR code);
```

### <a name="description"></a><span data-ttu-id="6e366-212">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-212">Description</span></span>

<span data-ttu-id="6e366-213">Este serviço adiciona uma nova instância ao recurso Error Code (11) do Dispositivo Objeto.</span><span class="sxs-lookup"><span data-stu-id="6e366-213">This service adds a new instance to the Error Code (11) resource of the Object Device.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-214">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-214">Parameters</span></span>

- <span data-ttu-id="6e366-215">**client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-215">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6e366-216">**código**: O novo código de erro.</span><span class="sxs-lookup"><span data-stu-id="6e366-216">**code**: The new error code.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-217">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-217">Return Values</span></span>

- <span data-ttu-id="6e366-218">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-218">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-219">**NX_LWM2M_BUFFER_TOO_SMALL**: O número máximo de códigos de erro armazenados foi atingido.</span><span class="sxs-lookup"><span data-stu-id="6e366-219">**NX_LWM2M_BUFFER_TOO_SMALL**: The maximum number of stored error codes has been reached.</span></span>
- <span data-ttu-id="6e366-220">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-220">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_error_reset"></a><span data-ttu-id="6e366-221">nx_lwm2m_client_device_error_reset</span><span class="sxs-lookup"><span data-stu-id="6e366-221">nx_lwm2m_client_device_error_reset</span></span>

<span data-ttu-id="6e366-222">Redefinir códigos de erro do objeto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="6e366-222">Reset error codes of Device Object</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-223">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-223">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-224">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-224">Description</span></span>

<span data-ttu-id="6e366-225">Este serviço elimina todas as instâncias de código de erro do Objeto do Dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6e366-225">This service deletes all error code resource instances from the Device Object.</span></span> <span data-ttu-id="6e366-226">Isto equivale a executar o código de erro de reposição de recursos (12).</span><span class="sxs-lookup"><span data-stu-id="6e366-226">This is equivalent to executing the resource Reset Error Code (12).</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-227">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-227">Parameters</span></span>

- <span data-ttu-id="6e366-228">**client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-228">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-229">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-229">Return Values</span></span>

- <span data-ttu-id="6e366-230">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-230">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-231">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-231">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_resource_changed"></a><span data-ttu-id="6e366-232">nx_lwm2m_client_device_resource_changed</span><span class="sxs-lookup"><span data-stu-id="6e366-232">nx_lwm2m_client_device_resource_changed</span></span>

<span data-ttu-id="6e366-233">Alteração de sinal do recurso objeto do dispositivo</span><span class="sxs-lookup"><span data-stu-id="6e366-233">Signal change of Device Object resource</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-234">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-234">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_resource_changed(NX_LWM2M_CLIENT *client_ptr,
                                    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a><span data-ttu-id="6e366-235">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-235">Description</span></span>

<span data-ttu-id="6e366-236">O serviço é utilizado pela aplicação para sinalizar ao Cliente LWM2M que um recurso do Dispositivo De Objeto mudou.</span><span class="sxs-lookup"><span data-stu-id="6e366-236">The service is used by the application to signal to the LWM2M Client that a resource of the Object Device has changed.</span></span> <span data-ttu-id="6e366-237">O Cliente LWM2M enviará uma notificação se o recurso for observado por um Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-237">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-238">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-238">Parameters</span></span>

- <span data-ttu-id="6e366-239">**client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-239">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6e366-240">**recurso**: Ponteiro para a estrutura que descreve o recurso que mudou.</span><span class="sxs-lookup"><span data-stu-id="6e366-240">**resource**: Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-241">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-241">Return Values</span></span>

- <span data-ttu-id="6e366-242">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-242">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-243">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-243">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_lock"></a><span data-ttu-id="6e366-244">nx_lwm2m_client_lock</span><span class="sxs-lookup"><span data-stu-id="6e366-244">nx_lwm2m_client_lock</span></span>

<span data-ttu-id="6e366-245">Cliente Lock LWM2M</span><span class="sxs-lookup"><span data-stu-id="6e366-245">Lock LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-246">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-246">Prototype</span></span>

```c
UINT nx_lwm2m_client_lock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-247">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-247">Description</span></span>

<span data-ttu-id="6e366-248">Este serviço bloqueia o Cliente LWM2M para evitar o acesso concutivo aos objetos LWM2M dos servidores ou de outro fio de aplicação.</span><span class="sxs-lookup"><span data-stu-id="6e366-248">This service locks the LWM2M Client to prevent concurent access to the LWM2M objects from the servers or another application thread.</span></span>

<span data-ttu-id="6e366-249">Se o Cliente LWM2M estiver atualmente bloqueado por outro fio, a função bloqueará até que o Cliente LWM2M seja desbloqueado.</span><span class="sxs-lookup"><span data-stu-id="6e366-249">If the LWM2M Client is currently locked by another thread, the function will block until the LWM2M Client is unlocked.</span></span>

<span data-ttu-id="6e366-250">As chamadas para pares nx_lwm2m_client_lock()/nx_lwm2m_client_unlock() podem ser aninhadas.</span><span class="sxs-lookup"><span data-stu-id="6e366-250">Calls to nx_lwm2m_client_lock()/nx_lwm2m_client_unlock() pairs can be nested.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-251">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-251">Parameters</span></span>

- <span data-ttu-id="6e366-252">**client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-252">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-253">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-253">Return Values</span></span>

- <span data-ttu-id="6e366-254">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-254">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-255">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-255">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_add"></a><span data-ttu-id="6e366-256">nx_lwm2m_client_object_add</span><span class="sxs-lookup"><span data-stu-id="6e366-256">nx_lwm2m_client_object_add</span></span>

<span data-ttu-id="6e366-257">Adicionar implementação de objeto ao Cliente LWM2M</span><span class="sxs-lookup"><span data-stu-id="6e366-257">Add Object implementation to the LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-258">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-258">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_add(NX_LWM2M_CLIENT *client_ptr,
                                NX_LWM2M_OBJECT *object_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-259">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-259">Description</span></span>

<span data-ttu-id="6e366-260">Este serviço adiciona uma nova implementação de Objeto ao Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-260">This service adds a new Object implementation to the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-261">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-261">Parameters</span></span>

- <span data-ttu-id="6e366-262">**client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-262">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6e366-263">**object_ptr**: Ponteiro para a estrutura que define a implementação do Objeto.</span><span class="sxs-lookup"><span data-stu-id="6e366-263">**object_ptr**: Pointer to the structure defining the Object implementation.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-264">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-264">Return Values</span></span>

- <span data-ttu-id="6e366-265">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-265">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-266">**NX_LWM2M_ALREADY_EXIST:** O ID do objeto já existe.</span><span class="sxs-lookup"><span data-stu-id="6e366-266">**NX_LWM2M_ALREADY_EXIST**: The Object ID already exists.</span></span>
- <span data-ttu-id="6e366-267">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-267">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_create"></a><span data-ttu-id="6e366-268">nx_lwm2m_client_object_create</span><span class="sxs-lookup"><span data-stu-id="6e366-268">nx_lwm2m_client_object_create</span></span>

<span data-ttu-id="6e366-269">Criar uma nova instância de objeto</span><span class="sxs-lookup"><span data-stu-id="6e366-269">Create a new Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-270">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-270">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_create(NX_LWM2M_CLIENT *client_ptr,
            NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr,
            UINT num_values, const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-271">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-271">Description</span></span>

<span data-ttu-id="6e366-272">Este serviço executa uma operação 'Criar' num Objeto do Cliente LWM2M para criar uma nova Instância de Objeto.</span><span class="sxs-lookup"><span data-stu-id="6e366-272">This service performs a 'Create' operation on an Object of the LWM2M Client to create a new Object Instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-273">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-273">Parameters</span></span>

- <span data-ttu-id="6e366-274">**client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-274">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6e366-275">**object_id:** O ID do objeto.</span><span class="sxs-lookup"><span data-stu-id="6e366-275">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="6e366-276">**instance_id_ptr**: O ponteiro para o ID da nova instância, pode ser NULO se o Cliente LWM2M tiver de atribuir um ID de instância.</span><span class="sxs-lookup"><span data-stu-id="6e366-276">**instance_id_ptr**: Pointer to the ID of the new instance, can be NULL if the LWM2M Client must assign an Instance ID.</span></span> <span data-ttu-id="6e366-277">Se o ID for o valor reservado 65535, o Cliente LWM2M atribuirá um ID de instância.</span><span class="sxs-lookup"><span data-stu-id="6e366-277">If the ID is the reserved value 65535 the LWM2M Client will assign an Instance ID.</span></span> <span data-ttu-id="6e366-278">Se não não null, o ID atribuído é devolvido após a chamada.</span><span class="sxs-lookup"><span data-stu-id="6e366-278">If not NULL the assigned ID is returned after the call.</span></span>
- <span data-ttu-id="6e366-279">**num_values**: O número de valores a definir.</span><span class="sxs-lookup"><span data-stu-id="6e366-279">**num_values**: The number of values to set.</span></span>
- <span data-ttu-id="6e366-280">**values_ptr**: Ponteize para uma matriz de valores de recursos para rubricar a nova Instância de Objeto.</span><span class="sxs-lookup"><span data-stu-id="6e366-280">**values_ptr**: Pointer to an array of resource values to initialize the new Object Instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-281">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-281">Return Values</span></span>

- <span data-ttu-id="6e366-282">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-282">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-283">**NX_LWM2M_ALREADY_EXIST**: O ID de instância de objeto já existe.</span><span class="sxs-lookup"><span data-stu-id="6e366-283">**NX_LWM2M_ALREADY_EXIST**: The Object Instance ID already exists.</span></span>
- <span data-ttu-id="6e366-284">**NX_LWM2M_METHOD_NOT_ALLOWED:** O Objeto não suporta a criação de instâncias.</span><span class="sxs-lookup"><span data-stu-id="6e366-284">**NX_LWM2M_METHOD_NOT_ALLOWED**: The Object doesn't support instance creation.</span></span>
- <span data-ttu-id="6e366-285">**NX_LWM2M_NO_MEMORY**: Não é possível alocar a memória para armazenar o novo caso.</span><span class="sxs-lookup"><span data-stu-id="6e366-285">**NX_LWM2M_NO_MEMORY**: Cannot allocate memory to store the new instance.</span></span>
- <span data-ttu-id="6e366-286">**NX_LWM2M_NOT_FOUND:** O ID do objeto não existe.</span><span class="sxs-lookup"><span data-stu-id="6e366-286">**NX_LWM2M_NOT_FOUND**: The Object ID doesn't exist.</span></span>
- <span data-ttu-id="6e366-287">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-287">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_delete"></a><span data-ttu-id="6e366-288">nx_lwm2m_client_object_delete</span><span class="sxs-lookup"><span data-stu-id="6e366-288">nx_lwm2m_client_object_delete</span></span>

<span data-ttu-id="6e366-289">Eliminar uma instância de objeto</span><span class="sxs-lookup"><span data-stu-id="6e366-289">Delete an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-290">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-290">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_delete(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id);
```

### <a name="description"></a><span data-ttu-id="6e366-291">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-291">Description</span></span>

<span data-ttu-id="6e366-292">Este serviço executa uma operação 'Eliminar' numa Instância de Objeto do Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-292">This service performs a 'Delete' operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-293">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-293">Parameters</span></span>

- <span data-ttu-id="6e366-294">**client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-294">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6e366-295">**object_id:** O ID do objeto.</span><span class="sxs-lookup"><span data-stu-id="6e366-295">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="6e366-296">**instance_id**: O ID da instância do objeto.</span><span class="sxs-lookup"><span data-stu-id="6e366-296">**instance_id**: The Object Instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-297">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-297">Return Values</span></span>

- <span data-ttu-id="6e366-298">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-298">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-299">**NX_LWM2M_METHOD_NOT_ALLOWED:** O Objeto não suporta a eliminação de instâncias.</span><span class="sxs-lookup"><span data-stu-id="6e366-299">**NX_LWM2M_METHOD_NOT_ALLOWED**: The Object doesn't support instance deletion.</span></span>
- <span data-ttu-id="6e366-300">**NX_LWM2M_NOT_FOUND:** O ID do objeto ou iD de instância de objeto não existe.</span><span class="sxs-lookup"><span data-stu-id="6e366-300">**NX_LWM2M_NOT_FOUND**: The Object ID or Object Instance ID doesn't exist.</span></span>
- <span data-ttu-id="6e366-301">NX_PTR_ERROR ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-301">NX_PTR_ERROR Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_discover"></a><span data-ttu-id="6e366-302">nx_lwm2m_client_object_discover</span><span class="sxs-lookup"><span data-stu-id="6e366-302">nx_lwm2m_client_object_discover</span></span>

<span data-ttu-id="6e366-303">Descubra recursos de uma instância de objeto</span><span class="sxs-lookup"><span data-stu-id="6e366-303">Discover resources of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-304">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-304">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_discover(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT *num_resources_ptr, NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-305">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-305">Description</span></span>

<span data-ttu-id="6e366-306">Este serviço executa uma operação 'Discover' numa Instância de Objeto do Cliente LWM2M, esta devolve a lista de recursos implementados pelo Objeto.</span><span class="sxs-lookup"><span data-stu-id="6e366-306">This service performs a 'Discover' operation on an Object Instance of the LWM2M Client, this returns the list of resources implemented by the Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-307">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-307">Parameters</span></span>

- <span data-ttu-id="6e366-308">**client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-308">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6e366-309">**object_id:** O ID do objeto.</span><span class="sxs-lookup"><span data-stu-id="6e366-309">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="6e366-310">**instance_id**: O ID da instância do objeto.</span><span class="sxs-lookup"><span data-stu-id="6e366-310">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="6e366-311">**num_resources_ptr**: No tamanho do tampão de destino, na saída o número de elementos escritos para o tampão.</span><span class="sxs-lookup"><span data-stu-id="6e366-311">**num_resources_ptr**: On input the size of the destination buffer, on output the number of elements writen to the buffer.</span></span>
- <span data-ttu-id="6e366-312">**resources_ptr**: Ponteiro para o tampão de destino.</span><span class="sxs-lookup"><span data-stu-id="6e366-312">**resources_ptr**: Pointer to the destination buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-313">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-313">Return Values</span></span>

- <span data-ttu-id="6e366-314">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-314">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="6e366-315">**NX_LWM2M_BUFFER_TOO_SMALL**: O tampão de recursos é demasiado pequeno para armazenar a lista de recursos.</span><span class="sxs-lookup"><span data-stu-id="6e366-315">**NX_LWM2M_BUFFER_TOO_SMALL**: The resources buffer is too small to store the list of resources.</span></span>
- <span data-ttu-id="6e366-316">**NX_LWM2M_NOT_FOUND:** O ID do objeto ou iD de instância de objeto não existe.</span><span class="sxs-lookup"><span data-stu-id="6e366-316">**NX_LWM2M_NOT_FOUND**: The Object ID or Object Instance ID doesn't exist.</span></span>
- <span data-ttu-id="6e366-317">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-317">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_execute"></a><span data-ttu-id="6e366-318">nx_lwm2m_client_object_execute</span><span class="sxs-lookup"><span data-stu-id="6e366-318">nx_lwm2m_client_object_execute</span></span>

<span data-ttu-id="6e366-319">Executar recurso de uma instância de objeto</span><span class="sxs-lookup"><span data-stu-id="6e366-319">Execute resource of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-320">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-320">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_execute(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr, UINT arguments_length);
```

### <a name="description"></a><span data-ttu-id="6e366-321">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-321">Description</span></span>

<span data-ttu-id="6e366-322">Este serviço executa a operação 'Executar' num recurso de instância de objeto do Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-322">This service performs the 'Execute' operation on an Object Instance Resource of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-323">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-323">Parameters</span></span>

- <span data-ttu-id="6e366-324">**client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-324">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6e366-325">**object_id:** O ID do objeto.</span><span class="sxs-lookup"><span data-stu-id="6e366-325">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="6e366-326">**instance_id**: O ID da instância do objeto.</span><span class="sxs-lookup"><span data-stu-id="6e366-326">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="6e366-327">**resource_id:** O ID do recurso.</span><span class="sxs-lookup"><span data-stu-id="6e366-327">**resource_id**: The Resource ID.</span></span>
- <span data-ttu-id="6e366-328">**arguments_ptr**: Ponto a partir dos argumentos da operação de execução.</span><span class="sxs-lookup"><span data-stu-id="6e366-328">**arguments_ptr**: Pointer to the arguments of the execute operation.</span></span> <span data-ttu-id="6e366-329">Pode ser NULO se arguments_length for zero.</span><span class="sxs-lookup"><span data-stu-id="6e366-329">Can be NULL if arguments_length is zero.</span></span>
- <span data-ttu-id="6e366-330">**arguments_length:** A duração dos argumentos.</span><span class="sxs-lookup"><span data-stu-id="6e366-330">**arguments_length**: The length of the arguments.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-331">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-331">Return Values</span></span>

- <span data-ttu-id="6e366-332">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-332">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-333">**NX_LWM2M_METHOD_NOT_ALLOWED:** O recurso não suporta a operação de execução.</span><span class="sxs-lookup"><span data-stu-id="6e366-333">**NX_LWM2M_METHOD_NOT_ALLOWED**: The resource doesn't support the execute operation.</span></span>
- <span data-ttu-id="6e366-334">**NX_LWM2M_NOT_FOUND:** O ID do Objeto, o ID da Instância do Objeto ou o ID do recurso não existem.</span><span class="sxs-lookup"><span data-stu-id="6e366-334">**NX_LWM2M_NOT_FOUND**: The Object ID, Object Instance ID or the resource ID doesn't exist.</span></span>
- <span data-ttu-id="6e366-335">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-335">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_get_next"></a><span data-ttu-id="6e366-336">nx_lwm2m_client_object_get_next</span><span class="sxs-lookup"><span data-stu-id="6e366-336">nx_lwm2m_client_object_get_next</span></span>

<span data-ttu-id="6e366-337">Obtenha a lista de Objetos implementados pelo Cliente LWM2M</span><span class="sxs-lookup"><span data-stu-id="6e366-337">Get the list of Objects implemented by the LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-338">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-338">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_get_next(NX_LWM2M_CLIENT *client_ptr,
                                    NX_LWM2M_ID *object_id_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-339">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-339">Description</span></span>

<span data-ttu-id="6e366-340">Este serviço devolve o ID do próximo Objeto implementado pelo Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-340">This service returns the ID of the next Object implemented by the LWM2M Client.</span></span> <span data-ttu-id="6e366-341">Se o ID do objeto atual estiver definido para NX_LWM2M_RESERVED_ID (65535) o primeiro ID do objeto é devolvido.</span><span class="sxs-lookup"><span data-stu-id="6e366-341">If the current Object ID is set to NX_LWM2M_RESERVED_ID (65535) the first Object ID is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-342">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-342">Parameters</span></span>

- <span data-ttu-id="6e366-343">**client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-343">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6e366-344">**object_id_ptr**: Ponteiro para o ID do objeto atual.</span><span class="sxs-lookup"><span data-stu-id="6e366-344">**object_id_ptr**: Pointer to the current Object ID.</span></span> <span data-ttu-id="6e366-345">Na devolução contém o próximo ID do Objeto implementado pelo Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-345">On return contains the next Object ID implemented by the LWM2M Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-346">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-346">Return Values</span></span>

- <span data-ttu-id="6e366-347">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-347">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="6e366-348">**NX_LWM2M_NOT_FOUND**: O ID dado objeto é o último da base de dados.</span><span class="sxs-lookup"><span data-stu-id="6e366-348">**NX_LWM2M_NOT_FOUND**: The given Object ID is the last of the database.</span></span>
- <span data-ttu-id="6e366-349">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-349">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_instance_get_next"></a><span data-ttu-id="6e366-350">nx_lwm2m_client_object_instance_get_next</span><span class="sxs-lookup"><span data-stu-id="6e366-350">nx_lwm2m_client_object_instance_get_next</span></span>

<span data-ttu-id="6e366-351">Obtenha a lista de instâncias de um objeto</span><span class="sxs-lookup"><span data-stu-id="6e366-351">Get the list of Instances of an Object</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-352">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-352">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_get_next(NX_LWM2M_CLIENT *client_ptr,
                    NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-353">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-353">Description</span></span>

<span data-ttu-id="6e366-354">Este serviço devolve o ID da próxima Instância de Objeto do Objeto dado.</span><span class="sxs-lookup"><span data-stu-id="6e366-354">This service returns the ID of the next Object Instance of the given Object.</span></span> <span data-ttu-id="6e366-355">Se o ID de instância atual estiver definido para NX_LWM2M_RESERVED_ID (65535) o ID da primeira instância é devolvido.</span><span class="sxs-lookup"><span data-stu-id="6e366-355">If the current Instance ID is set to NX_LWM2M_RESERVED_ID (65535) the ID of the first instance is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-356">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-356">Parameters</span></span>

- <span data-ttu-id="6e366-357">**client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-357">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6e366-358">**object_id:** O ID do objeto.</span><span class="sxs-lookup"><span data-stu-id="6e366-358">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="6e366-359">**instance_id_ptr**: Ponteiro para o ID de instância do objeto atual.</span><span class="sxs-lookup"><span data-stu-id="6e366-359">**instance_id_ptr**: Pointer to the current Object Instance ID.</span></span> <span data-ttu-id="6e366-360">No retorno contém o próximo ID de instância do objeto.</span><span class="sxs-lookup"><span data-stu-id="6e366-360">On return contains the next Instance ID of the Object.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-361">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-361">Return Values</span></span>

- <span data-ttu-id="6e366-362">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-362">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="6e366-363">**NX_LWM2M_NOT_FOUND**: O ID dado o caso é o último do objeto, ou o ID do objeto não é implementado.</span><span class="sxs-lookup"><span data-stu-id="6e366-363">**NX_LWM2M_NOT_FOUND**: The given Instance ID is the last of the object, or the Object ID is not implemented.</span></span>
- <span data-ttu-id="6e366-364">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-364">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_read"></a><span data-ttu-id="6e366-365">nx_lwm2m_client_object_read</span><span class="sxs-lookup"><span data-stu-id="6e366-365">nx_lwm2m_client_object_read</span></span>

<span data-ttu-id="6e366-366">Leia os valores de recursos de uma Instância de Objeto</span><span class="sxs-lookup"><span data-stu-id="6e366-366">Read resources values of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-367">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-367">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_read(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT num_values, NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a><span data-ttu-id="6e366-368">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-368">Description</span></span>

<span data-ttu-id="6e366-369">Este serviço executa uma operação 'Ler' numa Instância de Objeto do Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-369">This service performs a 'Read' operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-370">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-370">Parameters</span></span>

- <span data-ttu-id="6e366-371">**client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-371">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6e366-372">**object_id:** O ID do objeto.</span><span class="sxs-lookup"><span data-stu-id="6e366-372">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="6e366-373">**instance_id**: O ID da instância do objeto.</span><span class="sxs-lookup"><span data-stu-id="6e366-373">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="6e366-374">**num_values:** O número de recursos a ler.</span><span class="sxs-lookup"><span data-stu-id="6e366-374">**num_values**: The number of resources to read.</span></span>
- <span data-ttu-id="6e366-375">**values_ptr**: Ponteiro para uma série de NX_LWM2M_RESOURCE contendo os IDs dos recursos para ler.</span><span class="sxs-lookup"><span data-stu-id="6e366-375">**values_ptr**: Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources to read.</span></span> <span data-ttu-id="6e366-376">Na volta, a matriz é preenchida com os tipos e valores correspondentes.</span><span class="sxs-lookup"><span data-stu-id="6e366-376">On return the array is filled with the corresponding types and values.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-377">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-377">Return Values</span></span>

- <span data-ttu-id="6e366-378">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-378">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-379">**NX_LWM2M_METHOD_NOT_ALLOWED:** Um recurso não suporta a operação de leitura.</span><span class="sxs-lookup"><span data-stu-id="6e366-379">**NX_LWM2M_METHOD_NOT_ALLOWED**: A resource doesn't support the read operation.</span></span>
- <span data-ttu-id="6e366-380">**NX_LWM2M_NOT_FOUND**: O ID do objeto, o ID da instância do objeto ou um ID de recurso não existem.</span><span class="sxs-lookup"><span data-stu-id="6e366-380">**NX_LWM2M_NOT_FOUND**: The Object ID, Object Instance ID or a resource ID doesn't exist.</span></span>
- <span data-ttu-id="6e366-381">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-381">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_write"></a><span data-ttu-id="6e366-382">nx_lwm2m_client_object_write</span><span class="sxs-lookup"><span data-stu-id="6e366-382">nx_lwm2m_client_object_write</span></span>

<span data-ttu-id="6e366-383">Alterar os valores de recursos de uma instância de objeto</span><span class="sxs-lookup"><span data-stu-id="6e366-383">Change resources values of an Object instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-384">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-384">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_write(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, UINT num_values,
        const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

### <a name="description"></a><span data-ttu-id="6e366-385">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-385">Description</span></span>

<span data-ttu-id="6e366-386">Este serviço executa uma operação de 'Write' numa Instância de Objeto do Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-386">This service performs a 'Write' operation on an Object Instance of the LWM2M Client.</span></span>

<span data-ttu-id="6e366-387">As seguintes operações de escrita podem ser especificadas para o parâmetro *write_op:*</span><span class="sxs-lookup"><span data-stu-id="6e366-387">The following write operations can be specified to the *write_op* parameter:</span></span>

- <span data-ttu-id="6e366-388">**0** &mdash; Atualização Parcial: adição ou atualizações Recursos fornecidos no novo valor e deixa outros Recursos existentes inalterados,</span><span class="sxs-lookup"><span data-stu-id="6e366-388">**0** &mdash; Partial Update: adds or updates Resources provided in the new value and leaves other existing Resources unchanged,</span></span>

- <span data-ttu-id="6e366-389">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Instância de substituição: substitui a Instância do Objeto pelos novos valores de recursos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="6e366-389">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Replace Instance: replaces the Object Instance with the new provided resource values.</span></span>

- <span data-ttu-id="6e366-390">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Substituir Recurso: substitui os Recursos pelos novos valores de recursos fornecidos (utilizados para substituir Múltiplos Recursos).</span><span class="sxs-lookup"><span data-stu-id="6e366-390">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Replace Resource: replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span>

- <span data-ttu-id="6e366-391">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap Write: indica uma chamada de uma sequência de Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="6e366-391">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap Write: indicates a call from a Bootstrap sequence.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-392">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-392">Parameters</span></span>

- <span data-ttu-id="6e366-393">**client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-393">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6e366-394">**object_id:** O ID do objeto.</span><span class="sxs-lookup"><span data-stu-id="6e366-394">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="6e366-395">**instance_id**: O ID da instância do objeto.</span><span class="sxs-lookup"><span data-stu-id="6e366-395">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="6e366-396">**num_values:** O número de recursos para escrever.</span><span class="sxs-lookup"><span data-stu-id="6e366-396">**num_values**: The number of resources to write.</span></span>
- <span data-ttu-id="6e366-397">**values_ptr**: Ponteiro para uma série de NX_LWM2M_RESOURCE contendo os IDs dos recursos, os tipos e os valores a escrever.</span><span class="sxs-lookup"><span data-stu-id="6e366-397">**values_ptr**: Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources, the types and the values to write.</span></span>
- <span data-ttu-id="6e366-398">**write_op:** O tipo de operação de escrita.</span><span class="sxs-lookup"><span data-stu-id="6e366-398">**write_op**: The type of write operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-399">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-399">Return Values</span></span>

- <span data-ttu-id="6e366-400">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-400">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-401">**NX_LWM2M_BAD_ENCODING**: O tipo de recurso não é válido.</span><span class="sxs-lookup"><span data-stu-id="6e366-401">**NX_LWM2M_BAD_ENCODING**: The type of a resource is not valid.</span></span>
- <span data-ttu-id="6e366-402">**NX_LWM2M_BUFFER_TOO_SMALL**: O comprimento de um valor é demasiado grande para ser armazenado no caso.</span><span class="sxs-lookup"><span data-stu-id="6e366-402">**NX_LWM2M_BUFFER_TOO_SMALL**: The length of a value is too big to be stored in the instance.</span></span>
- <span data-ttu-id="6e366-403">**NX_LWM2M_METHOD_NOT_ALLOWED:** Um recurso não suporta a operação de escrita.</span><span class="sxs-lookup"><span data-stu-id="6e366-403">**NX_LWM2M_METHOD_NOT_ALLOWED**: A resource doesn't support the write operation.</span></span>
- <span data-ttu-id="6e366-404">**NX_LWM2M_NO_MEMORY**: Não é possível alocar a memória para armazenar um valor de recurso.</span><span class="sxs-lookup"><span data-stu-id="6e366-404">**NX_LWM2M_NO_MEMORY**: Cannot allocate memory to store a resource value.</span></span>
- <span data-ttu-id="6e366-405">**NX_LWM2M_NOT_ACCEPTABLE**: O valor de um recurso não é válido.</span><span class="sxs-lookup"><span data-stu-id="6e366-405">**NX_LWM2M_NOT_ACCEPTABLE**: The value of a resource is not valid.</span></span>
- <span data-ttu-id="6e366-406">**NX_LWM2M_NOT_FOUND**: O ID do objeto, o ID da instância do objeto ou um ID de recurso não existem.</span><span class="sxs-lookup"><span data-stu-id="6e366-406">**NX_LWM2M_NOT_FOUND**: The Object ID, Object Instance ID or a resource ID doesn't exist.</span></span>
- <span data-ttu-id="6e366-407">NX_OPTION_ERROR: Tipo inválido de operação de escrita.</span><span class="sxs-lookup"><span data-stu-id="6e366-407">NX_OPTION_ERROR: Invalid type of write operation.</span></span>
- <span data-ttu-id="6e366-408">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-408">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_security_key_callbacks_set"></a><span data-ttu-id="6e366-409">nx_lwm2m_client_security_key_callbacks_set</span><span class="sxs-lookup"><span data-stu-id="6e366-409">nx_lwm2m_client_security_key_callbacks_set</span></span>

<span data-ttu-id="6e366-410">Definir chamadas de gestão de chaves de objeto de segurança</span><span class="sxs-lookup"><span data-stu-id="6e366-410">Set Security Object key management callbacks</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-411">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-411">Prototype</span></span>

```c
UINT nx_lwm2m_client_security_key_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_CLIENT_SECURITY_KEY_WRITE_CALLBACK write_callback,
                NX_LWM2M_CLIENT_SECURITY_KEY_DELETE_CALLBACK delete_callback);
```

### <a name="description"></a><span data-ttu-id="6e366-412">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-412">Description</span></span>

<span data-ttu-id="6e366-413">Este serviço instala as chamadas de aplicação para implementação de operações nos recursos do LWM2M Security Object relacionados com as chaves de segurança.</span><span class="sxs-lookup"><span data-stu-id="6e366-413">This service installs the application callbacks for implementing operations on the LWM2M Security Object resources related to the security keys.</span></span>

<span data-ttu-id="6e366-414">O Cliente LWM2M delega a gestão da chave de segurança para a aplicação durante as sessões de Bootstrap, as chamadas serão chamadas quando o Servidor Bootstrap escrever ou eliminar os seguintes recursos numa Instância de Objeto de Segurança: Chave Pública ou Identidade (3), Chave Pública do Servidor (4), Chave Secreta (5).</span><span class="sxs-lookup"><span data-stu-id="6e366-414">The LWM2M Client delegates the security key management to the application during the Bootstrap sessions, the callbacks will be called when the Bootstrap Server writes or deletes the following resources on a Security Object Instance: Public Key or Identity (3), Server Public Key (4), Secret Key (5).</span></span>

<span data-ttu-id="6e366-415">A aplicação é responsável pelo armazenamento dos dados das chaves e pela configuração das sessões DTLS utilizadas pelo cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-415">The application is responsible for storing the keys data and for configuring the DTLS sessions used by the LWM2M client.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-416">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-416">Parameters</span></span>

- <span data-ttu-id="6e366-417">**client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-417">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="6e366-418">**write_callback**: O chamado devolução do método da chave 'Write'.</span><span class="sxs-lookup"><span data-stu-id="6e366-418">**write_callback**: The 'Write' key method callback.</span></span>
- <span data-ttu-id="6e366-419">**delete_callback**: O chamado devolução do método da chave 'Eliminar'.</span><span class="sxs-lookup"><span data-stu-id="6e366-419">**delete_callback**: The 'Delete' key method callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-420">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-420">Return Values</span></span>

- <span data-ttu-id="6e366-421">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-421">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-422">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-422">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_bootstrap"></a><span data-ttu-id="6e366-423">nx_lwm2m_client_session_bootstrap</span><span class="sxs-lookup"><span data-stu-id="6e366-423">nx_lwm2m_client_session_bootstrap</span></span>

<span data-ttu-id="6e366-424">Inicie uma sessão com um Servidor Bootstrap</span><span class="sxs-lookup"><span data-stu-id="6e366-424">Start a session with a Bootstrap Server</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-425">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-425">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap(NX_LWM2M_CLIENT_SESSION
    *session_ptr, NX_LWM2M_ID security_id, ULONG ip_address, UINT port);
```

### <a name="description"></a><span data-ttu-id="6e366-426">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-426">Description</span></span>

<span data-ttu-id="6e366-427">Este serviço inicia uma sessão com um Servidor Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="6e366-427">This service start a session with a Bootstrap Server.</span></span> <span data-ttu-id="6e366-428">O servidor deve ter uma instância de segurança correspondente no Objeto de Segurança.</span><span class="sxs-lookup"><span data-stu-id="6e366-428">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="6e366-429">Se o recurso 'Hold Off' for diferente de zero na Instância de Segurança associada a este servidor, a sessão aguardará uma bota iniciada pelo servidor, se não for iniciada nenhuma bota pelo servidor após este período de tempo, será executada uma Boostrap iniciada pelo Cliente.</span><span class="sxs-lookup"><span data-stu-id="6e366-429">If the 'Hold Off' resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, if no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span>

<span data-ttu-id="6e366-430">Qualquer sessão ativa atual é abortada por esta chamada e substituída pela nova sessão do Bootstrap Server.</span><span class="sxs-lookup"><span data-stu-id="6e366-430">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-431">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-431">Parameters</span></span>

- <span data-ttu-id="6e366-432">**session_ptr**: Ponteiro para o bloco de controlo da Sessão de Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-432">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="6e366-433">**security_id**: O ID de identificação do Servidor Bootstrap deve ser definido para NX_LWM2M_RESERVED_ID (65535) se o Servidor Bootstrap não tiver nenhuma Instância de Segurança definida.</span><span class="sxs-lookup"><span data-stu-id="6e366-433">**security_id**: The Security Instance ID of the Bootstrap Server, must be set to NX_LWM2M_RESERVED_ID (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="6e366-434">**ip_address**: O endereço IP do servidor.</span><span class="sxs-lookup"><span data-stu-id="6e366-434">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="6e366-435">**porta**: A porta UDP do servidor.</span><span class="sxs-lookup"><span data-stu-id="6e366-435">**port**: The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-436">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-436">Return Values</span></span>

- <span data-ttu-id="6e366-437">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-437">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-438">**NX_LWM2M_NOT_FOUND**: Não existe nenhuma instância de objeto de segurança correspondente ao ID de instância de segurança.</span><span class="sxs-lookup"><span data-stu-id="6e366-438">**NX_LWM2M_NOT_FOUND**: There is No Security Object instance corresponding to the Security Instance ID.</span></span>
- <span data-ttu-id="6e366-439">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-439">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a><span data-ttu-id="6e366-440">nx_lwm2m_client_session_bootstrap_dtls</span><span class="sxs-lookup"><span data-stu-id="6e366-440">nx_lwm2m_client_session_bootstrap_dtls</span></span>

<span data-ttu-id="6e366-441">Inicie uma sessão segura com um Servidor Bootstrap</span><span class="sxs-lookup"><span data-stu-id="6e366-441">Start a secure session with a Bootstrap Server</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-442">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-442">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID security_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a><span data-ttu-id="6e366-443">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-443">Description</span></span>

<span data-ttu-id="6e366-444">Este serviço inicia uma sessão com um Servidor Bootstrap utilizando uma ligação DTLS segura.</span><span class="sxs-lookup"><span data-stu-id="6e366-444">This service start a session with a Bootstrap Server using a secure DTLS connection.</span></span> <span data-ttu-id="6e366-445">O servidor deve ter uma instância de segurança correspondente no Objeto de Segurança.</span><span class="sxs-lookup"><span data-stu-id="6e366-445">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="6e366-446">A sessão DTLS deve ter sido configurada com as suites de cifra adequadas e material chave antes de chamar esta função.</span><span class="sxs-lookup"><span data-stu-id="6e366-446">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="6e366-447">NX_SECURE_ENABLE_DTLS deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="6e366-447">NX_SECURE_ENABLE_DTLS must be defined.</span></span>

<span data-ttu-id="6e366-448">Se o recurso 'Hold Off' for diferente de zero na Instância de Segurança associada a este servidor, a sessão aguardará uma bota iniciada pelo servidor, se não for iniciada nenhuma bota pelo servidor após este período de tempo, será executada uma Boostrap iniciada pelo Cliente.</span><span class="sxs-lookup"><span data-stu-id="6e366-448">If the 'Hold Off' resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, if no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span>

<span data-ttu-id="6e366-449">Qualquer sessão ativa atual é abortada por esta chamada e substituída pela nova sessão do Bootstrap Server.</span><span class="sxs-lookup"><span data-stu-id="6e366-449">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-450">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-450">Parameters</span></span>

- <span data-ttu-id="6e366-451">**session_ptr**: Ponteiro para o bloco de controlo da Sessão de Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-451">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="6e366-452">**security_id**: O ID de identificação do Servidor Bootstrap deve ser definido para NX_LWM2M_RESERVED_ID (65535) se o Servidor Bootstrap não tiver nenhuma Instância de Segurança definida.</span><span class="sxs-lookup"><span data-stu-id="6e366-452">**security_id**: The Security Instance ID of the Bootstrap Server, must be set to NX_LWM2M_RESERVED_ID (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="6e366-453">**ip_address**: O endereço IP do servidor.</span><span class="sxs-lookup"><span data-stu-id="6e366-453">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="6e366-454">**porta**: A porta UDP do servidor.</span><span class="sxs-lookup"><span data-stu-id="6e366-454">**port**: The UDP port of the server.</span></span>
- <span data-ttu-id="6e366-455">**dtls_session_ptr**: A sessão DTLS para utilizar para a sessão Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="6e366-455">**dtls_session_ptr**: The DTLS session to use for the Bootstrap session.</span></span>
- <span data-ttu-id="6e366-456">**dtls_local_port**: A porta UDP local utilizada para a sessão DTLS.</span><span class="sxs-lookup"><span data-stu-id="6e366-456">**dtls_local_port**: The local UDP port used for the DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-457">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-457">Return Values</span></span>

- <span data-ttu-id="6e366-458">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-458">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-459">**NX_LWM2M_NOT_FOUND**: Não existe nenhuma instância de objeto de segurança correspondente ao ID de instância de segurança.</span><span class="sxs-lookup"><span data-stu-id="6e366-459">**NX_LWM2M_NOT_FOUND**: There is No Security Object instance corresponding to the Security Instance ID.</span></span>
- <span data-ttu-id="6e366-460">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-460">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_create"></a><span data-ttu-id="6e366-461">nx_lwm2m_client_session_create</span><span class="sxs-lookup"><span data-stu-id="6e366-461">nx_lwm2m_client_session_create</span></span>

<span data-ttu-id="6e366-462">Criar sessão de clientes LWM2M</span><span class="sxs-lookup"><span data-stu-id="6e366-462">Create LWM2M Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-463">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-463">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_create(NX_LWM2M_CLIENT_SESSION *session_ptr,
         NX_LWM2M_CLIENT *client_ptr,
         NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a><span data-ttu-id="6e366-464">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-464">Description</span></span>

<span data-ttu-id="6e366-465">Este serviço cria uma nova Sessão de Cliente LWM2M anexada a um Cliente LWM2M existente.</span><span class="sxs-lookup"><span data-stu-id="6e366-465">This service creates a new LWM2M Client Session attached to an existing LWM2M Client.</span></span> <span data-ttu-id="6e366-466">A sessão é utilizada pelo Cliente LWM2M para comunicar com um Servidor Bootstrap ou um Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-466">The session is used by the LWM2M Client to communicate with a Bootstrap Server or a LWM2M Server.</span></span>

<span data-ttu-id="6e366-467">A aplicação deve fornecer uma função de retorno que será chamada quando o estado da sessão for atualizado.</span><span class="sxs-lookup"><span data-stu-id="6e366-467">The application must provide a callback function that will be called when the state of the session is updated.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-468">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-468">Parameters</span></span>

- <span data-ttu-id="6e366-469">**session_ptr**: Ponteiro para o bloco de controlo da Sessão de Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-469">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="6e366-470">**client_ptr**: Ponteiro para o cliente LWM2M anteriormente criado.</span><span class="sxs-lookup"><span data-stu-id="6e366-470">**client_ptr**: Pointer to the previously created LWM2M Client.</span></span>
- <span data-ttu-id="6e366-471">**state_callback**: Chamada de chamada quando o estado da sessão tiver mudado.</span><span class="sxs-lookup"><span data-stu-id="6e366-471">**state_callback**: Application callback that is called when the state of the session has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-472">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-472">Return Values</span></span>

- <span data-ttu-id="6e366-473">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-473">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-474">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-474">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_delete"></a><span data-ttu-id="6e366-475">nx_lwm2m_client_session_delete</span><span class="sxs-lookup"><span data-stu-id="6e366-475">nx_lwm2m_client_session_delete</span></span>

<span data-ttu-id="6e366-476">Eliminar sessão de clientes LWM2M</span><span class="sxs-lookup"><span data-stu-id="6e366-476">Delete LWM2M Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-477">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-477">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-478">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-478">Description</span></span>

<span data-ttu-id="6e366-479">Este serviço elimina uma Sessão de Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-479">This service deletes a LWM2M Client Session.</span></span>

<span data-ttu-id="6e366-480">Quando um Cliente LWM2M é eliminado ligando nx_lwm2m_client_delete todas as sessões anexas ao cliente também são eliminadas.</span><span class="sxs-lookup"><span data-stu-id="6e366-480">When a LWM2M Client is deleted by calling nx_lwm2m_client_delete all sessions attached to the client are also deleted.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-481">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-481">Parameters</span></span>

- <span data-ttu-id="6e366-482">**session_ptr**: Ponteiro para o bloco de controlo da Sessão de Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-482">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-483">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-483">Return Values</span></span>

- <span data-ttu-id="6e366-484">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-484">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-485">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-485">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_deregister"></a><span data-ttu-id="6e366-486">nx_lwm2m_client_session_deregister</span><span class="sxs-lookup"><span data-stu-id="6e366-486">nx_lwm2m_client_session_deregister</span></span>

<span data-ttu-id="6e366-487">Termine uma sessão com um Servidor LWM2M</span><span class="sxs-lookup"><span data-stu-id="6e366-487">Terminate a session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-488">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-488">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-489">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-489">Description</span></span>

<span data-ttu-id="6e366-490">Este serviço executa uma operação 'De-Register' para um Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-490">This service performs a 'De-Register' operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-491">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-491">Parameters</span></span>

- <span data-ttu-id="6e366-492">**session_ptr**: Ponteiro para o bloco de controlo da Sessão de Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-492">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-493">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-493">Return Values</span></span>

- <span data-ttu-id="6e366-494">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-494">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-495">**NX_LWM2M_NOT_REGISTERED:** O cliente não está registado no servidor.</span><span class="sxs-lookup"><span data-stu-id="6e366-495">**NX_LWM2M_NOT_REGISTERED**: The client is not registered to the server.</span></span>
- <span data-ttu-id="6e366-496">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-496">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_error_get"></a><span data-ttu-id="6e366-497">nx_lwm2m_client_session_error_get</span><span class="sxs-lookup"><span data-stu-id="6e366-497">nx_lwm2m_client_session_error_get</span></span>

<span data-ttu-id="6e366-498">Obtenha o último erro de uma sessão</span><span class="sxs-lookup"><span data-stu-id="6e366-498">Get last error of a session</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-499">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-499">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-500">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-500">Description</span></span>

<span data-ttu-id="6e366-501">Este serviço devolve o código de erro da sessão quando a sessão está num estado de erro.</span><span class="sxs-lookup"><span data-stu-id="6e366-501">This service returns the error code of the session when the session is in an error state.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-502">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-502">Parameters</span></span>

- <span data-ttu-id="6e366-503">**session_ptr**: Ponteiro para o bloco de controlo da Sessão de Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-503">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-504">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-504">Return Values</span></span>

- <span data-ttu-id="6e366-505">**NX_SUCCESS**: A sessão não está em estado de erro.</span><span class="sxs-lookup"><span data-stu-id="6e366-505">**NX_SUCCESS**: The session is not in error state.</span></span>
- <span data-ttu-id="6e366-506">**NX_LWM2M_ADDRESS_ERROR:** Endereço do servidor inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-506">**NX_LWM2M_ADDRESS_ERROR**: Invalid server address.</span></span>
- <span data-ttu-id="6e366-507">**NX_LWM2M_BUFFER_TOO_SMALL:** A carga de pedido não se enquadra no tampão de rede.</span><span class="sxs-lookup"><span data-stu-id="6e366-507">**NX_LWM2M_BUFFER_TOO_SMALL**: Payload of request doesn't fit in network buffer.</span></span>
- <span data-ttu-id="6e366-508">**NX_LWM2M_DTLS_ERROR:** Não conseguiu estabelecer uma ligação segura com o servidor.</span><span class="sxs-lookup"><span data-stu-id="6e366-508">**NX_LWM2M_DTLS_ERROR**: Failed to establish secured connection with server.</span></span>
- <span data-ttu-id="6e366-509">**NX_LWM2M_ERROR:** Erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="6e366-509">**NX_LWM2M_ERROR**: Unspecified error.</span></span>
- <span data-ttu-id="6e366-510">**NX_LWM2M_FORBIDDEN:** Registo recusado por servidor.</span><span class="sxs-lookup"><span data-stu-id="6e366-510">**NX_LWM2M_FORBIDDEN**: Registration refused by server.</span></span>
- <span data-ttu-id="6e366-511">**NX_LWM2M_NOT_FOUND**: Cliente não encontrado pelo servidor ao atualizar/desregistar.</span><span class="sxs-lookup"><span data-stu-id="6e366-511">**NX_LWM2M_NOT_FOUND**: Client not found by server when updating/deregistering.</span></span>
- <span data-ttu-id="6e366-512">**NX_LWM2M_SERVER_INSTANCE_DELETED**: A instância do objeto do servidor correspondente à sessão foi eliminada.</span><span class="sxs-lookup"><span data-stu-id="6e366-512">**NX_LWM2M_SERVER_INSTANCE_DELETED**: The Server Object Instance corresponding to the session has been deleted.</span></span>
- <span data-ttu-id="6e366-513">**NX_LWM2M_TIMED_OUT:** Nenhuma resposta do servidor.</span><span class="sxs-lookup"><span data-stu-id="6e366-513">**NX_LWM2M_TIMED_OUT**: No answer from server.</span></span>
- <span data-ttu-id="6e366-514">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-514">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_register"></a><span data-ttu-id="6e366-515">nx_lwm2m_client_session_register</span><span class="sxs-lookup"><span data-stu-id="6e366-515">nx_lwm2m_client_session_register</span></span>

<span data-ttu-id="6e366-516">Inicie uma sessão com um Servidor LWM2M</span><span class="sxs-lookup"><span data-stu-id="6e366-516">Start a session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-517">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-517">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register(NX_LWM2M_CLIENT_SESSION *session_ptr,
                    NX_LWM2M_ID server_id, ULONG ip_address, UINT port);
```

### <a name="description"></a><span data-ttu-id="6e366-518">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-518">Description</span></span>

<span data-ttu-id="6e366-519">Este serviço executa uma operação 'Registar' para um Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-519">This service performs a 'Register' operation to a LWM2M Server.</span></span> <span data-ttu-id="6e366-520">O servidor deve ter uma instância de servidor correspondente no Objeto do Servidor.</span><span class="sxs-lookup"><span data-stu-id="6e366-520">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="6e366-521">Se o registo for bem sucedido, o Cliente LWM2M processará novas operações a partir do servidor e enviará periodicamente mensagens de 'Update' até que o cliente seja descista.</span><span class="sxs-lookup"><span data-stu-id="6e366-521">If the registration is successful the LWM2M Client will process further operations from the server and will periodically send 'Update' messages until the client is de-registered.</span></span>

<span data-ttu-id="6e366-522">Qualquer sessão ativa atual é abortada por esta chamada e substituída pela nova sessão do Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-522">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-523">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-523">Parameters</span></span>

- <span data-ttu-id="6e366-524">**session_ptr**: Ponteiro para o bloco de controlo da Sessão de Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-524">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="6e366-525">**server_id**: O ID do Servidor Curto do Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-525">**server_id**: The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="6e366-526">**ip_address**: O endereço IP do servidor.</span><span class="sxs-lookup"><span data-stu-id="6e366-526">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="6e366-527">**porta**: A porta UDP do servidor.</span><span class="sxs-lookup"><span data-stu-id="6e366-527">**port**: The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-528">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-528">Return Values</span></span>

- <span data-ttu-id="6e366-529">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-529">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="6e366-530">**NX_LWM2M_NOT_FOUND**: Não existe nenhuma instância de objeto de servidor correspondente ao ID do servidor curto.</span><span class="sxs-lookup"><span data-stu-id="6e366-530">**NX_LWM2M_NOT_FOUND**: There is No Server Object instance corresponding to the Short Server ID.</span></span>
- <span data-ttu-id="6e366-531">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-531">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_register_dtls"></a><span data-ttu-id="6e366-532">nx_lwm2m_client_session_register_dtls</span><span class="sxs-lookup"><span data-stu-id="6e366-532">nx_lwm2m_client_session_register_dtls</span></span>

<span data-ttu-id="6e366-533">Inicie uma sessão segura com um Servidor LWM2M</span><span class="sxs-lookup"><span data-stu-id="6e366-533">Start a secure session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-534">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-534">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID server_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a><span data-ttu-id="6e366-535">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-535">Description</span></span>

<span data-ttu-id="6e366-536">Este serviço executa uma operação 'Register' para um Servidor LWM2M utilizando uma ligação DTLS segura.</span><span class="sxs-lookup"><span data-stu-id="6e366-536">This service performs a 'Register' operation to a LWM2M Server using a secure DTLS connection.</span></span> <span data-ttu-id="6e366-537">O servidor deve ter uma instância de servidor correspondente no Objeto do Servidor.</span><span class="sxs-lookup"><span data-stu-id="6e366-537">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="6e366-538">A sessão DTLS deve ter sido configurada com as suites de cifra adequadas e material chave antes de chamar esta função.</span><span class="sxs-lookup"><span data-stu-id="6e366-538">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="6e366-539">NX_SECURE_ENABLE_DTLS deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="6e366-539">NX_SECURE_ENABLE_DTLS must be defined.</span></span>

<span data-ttu-id="6e366-540">Cada sessão DTLS utiliza a sua própria tomada UDP para comunicação, pelo que o porto local dtls_local_port deve ser diferente para cada sessão se a aplicação criar várias sessões seguras.</span><span class="sxs-lookup"><span data-stu-id="6e366-540">Each DTLS session uses its own UDP socket for communication, so the local port dtls_local_port must be different for each session if the application creates several secure sessions.</span></span>

<span data-ttu-id="6e366-541">Se o registo for bem sucedido, o Cliente LWM2M processará novas operações a partir do servidor e enviará periodicamente mensagens de 'Update' até que o cliente seja descista.</span><span class="sxs-lookup"><span data-stu-id="6e366-541">If the registration is successful the LWM2M Client will process further operations from the server and will periodically send 'Update' messages until the client is de-registered.</span></span>

<span data-ttu-id="6e366-542">Qualquer sessão ativa atual é abortada por esta chamada e substituída pela nova sessão do Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-542">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-543">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-543">Parameters</span></span>

- <span data-ttu-id="6e366-544">**session_ptr**: Ponteiro para o bloco de controlo da Sessão de Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-544">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="6e366-545">**server_id**: O ID do Servidor Curto do Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-545">**server_id**: The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="6e366-546">**ip_address**: O endereço IP do servidor.</span><span class="sxs-lookup"><span data-stu-id="6e366-546">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="6e366-547">**porta**: A porta UDP do servidor.</span><span class="sxs-lookup"><span data-stu-id="6e366-547">**port**: The UDP port of the server.</span></span>
- <span data-ttu-id="6e366-548">**dtls_session_ptr**: A sessão DTLS para utilizar para a sessão LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-548">**dtls_session_ptr**: The DTLS session to use for the LWM2M session.</span></span>
- <span data-ttu-id="6e366-549">**dtls_local_port**: A porta UDP local utilizada para a sessão DTLS.</span><span class="sxs-lookup"><span data-stu-id="6e366-549">**dtls_local_port**: The local UDP port used for the DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-550">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-550">Return Values</span></span>

- <span data-ttu-id="6e366-551">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-551">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-552">**NX_LWM2M_NOT_FOUND**: Não existe nenhuma instância de objeto de servidor correspondente ao ID do servidor curto.</span><span class="sxs-lookup"><span data-stu-id="6e366-552">**NX_LWM2M_NOT_FOUND**: There is No Server Object instance corresponding to the Short Server ID.</span></span>
- <span data-ttu-id="6e366-553">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-553">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_update"></a><span data-ttu-id="6e366-554">nx_lwm2m_client_session_update</span><span class="sxs-lookup"><span data-stu-id="6e366-554">nx_lwm2m_client_session_update</span></span>

<span data-ttu-id="6e366-555">Atualize uma sessão com um Servidor LWM2M</span><span class="sxs-lookup"><span data-stu-id="6e366-555">Update a session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-556">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-556">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-557">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-557">Description</span></span>

<span data-ttu-id="6e366-558">Este serviço executa uma operação 'Update' para um Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-558">This service performs an 'Update' operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-559">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-559">Parameters</span></span>

- <span data-ttu-id="6e366-560">**session_ptr**: Ponteiro para o bloco de controlo da Sessão de Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-560">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-561">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-561">Return Values</span></span>

- <span data-ttu-id="6e366-562">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-562">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-563">**NX_LWM2M_NOT_REGISTERED:** O cliente não está registado no servidor.</span><span class="sxs-lookup"><span data-stu-id="6e366-563">**NX_LWM2M_NOT_REGISTERED**: The client is not registered to the server.</span></span>
- <span data-ttu-id="6e366-564">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-564">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_unlock"></a><span data-ttu-id="6e366-565">nx_lwm2m_client_unlock</span><span class="sxs-lookup"><span data-stu-id="6e366-565">nx_lwm2m_client_unlock</span></span>

<span data-ttu-id="6e366-566">Desbloquear Cliente LWM2M</span><span class="sxs-lookup"><span data-stu-id="6e366-566">Unlock LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-567">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-567">Prototype</span></span>

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-568">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-568">Description</span></span>

<span data-ttu-id="6e366-569">Este serviço desbloqueia a previoulsy do Cliente LWM2M bloqueada por uma chamada para nx_lwm2m_client_unlock().</span><span class="sxs-lookup"><span data-stu-id="6e366-569">This service unlocks the LWM2M Client previoulsy locked by a call to nx_lwm2m_client_unlock().</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-570">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-570">Parameters</span></span>

- <span data-ttu-id="6e366-571">**client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-571">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-572">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-572">Return Values</span></span>

- <span data-ttu-id="6e366-573">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-573">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-574">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-574">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_create"></a><span data-ttu-id="6e366-575">nx_lwm2m_firmware_create</span><span class="sxs-lookup"><span data-stu-id="6e366-575">nx_lwm2m_firmware_create</span></span>

<span data-ttu-id="6e366-576">Criar objeto de atualização de firmware</span><span class="sxs-lookup"><span data-stu-id="6e366-576">Create Firmware Update Object</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-577">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-577">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_create(NX_LWM2M_FIRMWARE *firmware_ptr,
    NX_LWM2M_CLIENT *client_ptr, UINT protocols,
    NX_LWM2M_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_FIRMWARE_UPDATE_CALLBACK update_callback);
```

### <a name="description"></a><span data-ttu-id="6e366-578">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-578">Description</span></span>

<span data-ttu-id="6e366-579">Este serviço inicializa um Objeto de Atualização de Firmware e adiciona o Objeto a um Cliente LWM2M anteriormente criado.</span><span class="sxs-lookup"><span data-stu-id="6e366-579">This service initializes a Firmware Update Object and adds the Object to a previously created LWM2M Client.</span></span> <span data-ttu-id="6e366-580">O Firmware Update Object implementa os recursos para comunicar com um Servidor LWM2M, mas a aplicação deve fornecer chamadas para implementar as operações reais no firmware (dowloading, armazenamento e atualização do firmware).</span><span class="sxs-lookup"><span data-stu-id="6e366-580">The Firmware Update Object implements the resources for communicating with a LWM2M Server but the application must provide callbacks for implementing the actual operations on the firmware (dowloading, storing, and updating the firmware).</span></span>

<span data-ttu-id="6e366-581">O parâmetro de protocolo indica quais os protocolos suportados pela aplicação de recuperação do firmware com o recurso 'Package URI', são definidas as seguintes bandeiras:</span><span class="sxs-lookup"><span data-stu-id="6e366-581">The protocols parameter indicates which protocols are supported by the application for retrieving the firmware with the 'Package URI' resource, the following flags are defined:</span></span>

<span data-ttu-id="6e366-582">NX_LWM2M_FIRMWARE_PROTOCOL_COAP, NX_LWM2M_FIRMWARE_PROTOCOL_COAPS, NX_LWM2M_FIRMWARE_PROTOCOL_HTTP, NX_LWM2M_FIRMWARE_PROTOCOL_HTPPS.</span><span class="sxs-lookup"><span data-stu-id="6e366-582">NX_LWM2M_FIRMWARE_PROTOCOL_COAP, NX_LWM2M_FIRMWARE_PROTOCOL_COAPS, NX_LWM2M_FIRMWARE_PROTOCOL_HTTP, NX_LWM2M_FIRMWARE_PROTOCOL_HTPPS.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-583">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-583">Parameters</span></span>

- <span data-ttu-id="6e366-584">**firmware_ptr**: Ponteiro para o bloco de controlo do objeto Firmware.</span><span class="sxs-lookup"><span data-stu-id="6e366-584">**firmware_ptr**: Pointer to the Firmware Object control block.</span></span>
- <span data-ttu-id="6e366-585">**client_ptr**: Ponteiro para o cliente LWM2M criado previsivelmente.</span><span class="sxs-lookup"><span data-stu-id="6e366-585">**client_ptr**: Pointer to previsously created LWM2M Client.</span></span>
- <span data-ttu-id="6e366-586">**protocolos**: Bandeiras que indicam quais os protocolos suportados pelo recurso Package URI.</span><span class="sxs-lookup"><span data-stu-id="6e366-586">**protocols**: Flags indicating which protocols are supported by the Package URI resource.</span></span>
- <span data-ttu-id="6e366-587">**package_callback**: Deve ser NU [TBD].</span><span class="sxs-lookup"><span data-stu-id="6e366-587">**package_callback**: Must be NULL [TBD].</span></span>
- <span data-ttu-id="6e366-588">**package_uri_callback**: Callback usado para implementar o recurso Package URI.</span><span class="sxs-lookup"><span data-stu-id="6e366-588">**package_uri_callback**: Callback used to implement the Package URI resource.</span></span>
- <span data-ttu-id="6e366-589">**update_callback**: Callback usado para implementar o recurso Update.</span><span class="sxs-lookup"><span data-stu-id="6e366-589">**update_callback**: Callback used to implement the Update resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-590">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-590">Return Values</span></span>

- <span data-ttu-id="6e366-591">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-591">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-592">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-592">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_package_info_set"></a><span data-ttu-id="6e366-593">nx_lwm2m_firmware_package_info_set</span><span class="sxs-lookup"><span data-stu-id="6e366-593">nx_lwm2m_firmware_package_info_set</span></span>

<span data-ttu-id="6e366-594">Definir informações do pacote de atualização de firmware</span><span class="sxs-lookup"><span data-stu-id="6e366-594">Set Firmware Update Package Information</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-595">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-595">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_package_info_set(NX_LWM2M_FIRMWARE *firmware_ptr,
                                const CHAR *name, const CHAR *version);
```

### <a name="description"></a><span data-ttu-id="6e366-596">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-596">Description</span></span>

<span data-ttu-id="6e366-597">Este serviço altera os valores dos recursos 'PkgName' (6) e 'PkgVersion' (7) do Firmware Update Object.</span><span class="sxs-lookup"><span data-stu-id="6e366-597">This service changes the values of the 'PkgName' (6) and 'PkgVersion' (7) resources of the Firmware Update Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-598">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-598">Parameters</span></span>

- <span data-ttu-id="6e366-599">**firmware_ptr**: Ponter para o objeto de atualização de firmware.</span><span class="sxs-lookup"><span data-stu-id="6e366-599">**firmware_ptr**: Pointer to the Firmware Update Object.</span></span>
- <span data-ttu-id="6e366-600">**nome**: O novo valor do Nome do Pacote.</span><span class="sxs-lookup"><span data-stu-id="6e366-600">**name**: The new value of the Package Name.</span></span>
- <span data-ttu-id="6e366-601">**versão**: O novo valor da versão pacote.</span><span class="sxs-lookup"><span data-stu-id="6e366-601">**version**: The new value of the Package Version.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-602">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-602">Return Values</span></span>

- <span data-ttu-id="6e366-603">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-603">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-604">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-604">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_result_set"></a><span data-ttu-id="6e366-605">nx_lwm2m_firmware_result_set</span><span class="sxs-lookup"><span data-stu-id="6e366-605">nx_lwm2m_firmware_result_set</span></span>

<span data-ttu-id="6e366-606">Definir resultado da atualização do firmware</span><span class="sxs-lookup"><span data-stu-id="6e366-606">Set Firmware Update Result</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-607">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-607">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_result_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR result);
```

### <a name="description"></a><span data-ttu-id="6e366-608">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-608">Description</span></span>

<span data-ttu-id="6e366-609">Este serviço altera o valor do recurso 'Resultado de actualização' (5) do Objeto de Atualização de Firmware.</span><span class="sxs-lookup"><span data-stu-id="6e366-609">This service changes the value of the 'Update Result' (5) resource of the Firmware Update Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-610">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-610">Parameters</span></span>

- <span data-ttu-id="6e366-611">**firmware_ptr**: Ponter para o objeto de atualização de firmware.</span><span class="sxs-lookup"><span data-stu-id="6e366-611">**firmware_ptr**: Pointer to the Firmware Update Object.</span></span>
- <span data-ttu-id="6e366-612">**resultado**: O novo valor do recurso Resultado de Atualização.</span><span class="sxs-lookup"><span data-stu-id="6e366-612">**result**: The new value of the Update Result resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-613">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-613">Return Values</span></span>

- <span data-ttu-id="6e366-614">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-614">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-615">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-615">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_state_set"></a><span data-ttu-id="6e366-616">nx_lwm2m_firmware_state_set</span><span class="sxs-lookup"><span data-stu-id="6e366-616">nx_lwm2m_firmware_state_set</span></span>

<span data-ttu-id="6e366-617">Definir Estado de Atualização de Firmware</span><span class="sxs-lookup"><span data-stu-id="6e366-617">Set Firmware Update State</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-618">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-618">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_state_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR state);
```

### <a name="description"></a><span data-ttu-id="6e366-619">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-619">Description</span></span>

<span data-ttu-id="6e366-620">Este serviço altera o valor do recurso 'Estado' (3) do Objeto de Atualização de Firmware.</span><span class="sxs-lookup"><span data-stu-id="6e366-620">This service changes the value of the 'State' (3) resource of the Firmware Update Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-621">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-621">Parameters</span></span>

- <span data-ttu-id="6e366-622">**firmware_ptr**: Ponter para o objeto de atualização de firmware.</span><span class="sxs-lookup"><span data-stu-id="6e366-622">**firmware_ptr**: Pointer to the Firmware Update Object.</span></span>
- <span data-ttu-id="6e366-623">**estado**: O novo valor do recurso do Estado.</span><span class="sxs-lookup"><span data-stu-id="6e366-623">**state**: The new value of the State resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-624">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-624">Return Values</span></span>

- <span data-ttu-id="6e366-625">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-625">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-626">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-626">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_object_resource_changed"></a><span data-ttu-id="6e366-627">nx_lwm2m_object_resource_changed</span><span class="sxs-lookup"><span data-stu-id="6e366-627">nx_lwm2m_object_resource_changed</span></span>

<span data-ttu-id="6e366-628">Alteração de sinal de um valor de recurso de uma Instância de Objeto</span><span class="sxs-lookup"><span data-stu-id="6e366-628">Signal change of a resource value of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-629">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-629">Prototype</span></span>

```c
UINT nx_lwm2m_object_resource_changed(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a><span data-ttu-id="6e366-630">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-630">Description</span></span>

<span data-ttu-id="6e366-631">Este serviço é utilizado por uma implementação de Objeto para sinalizar o Cliente LWM2M que um dos seus valores de recursos mudou.</span><span class="sxs-lookup"><span data-stu-id="6e366-631">This service is used by an Object implementation to signals the LWM2M Client that one of its resource value has changed.</span></span> <span data-ttu-id="6e366-632">O Cliente LWM2M enviará uma notificação se o recurso for observado por um Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="6e366-632">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-633">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-633">Parameters</span></span>

- <span data-ttu-id="6e366-634">**object_ptr**: Ponteiro para a implementação do objeto.</span><span class="sxs-lookup"><span data-stu-id="6e366-634">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="6e366-635">**instance_ptr**: Ponteiro para a Instância do Objeto.</span><span class="sxs-lookup"><span data-stu-id="6e366-635">**instance_ptr**: Pointer to the Object Instance.</span></span>
- <span data-ttu-id="6e366-636">**recurso**: Ponteiro para a estrutura que descreve o recurso que mudou.</span><span class="sxs-lookup"><span data-stu-id="6e366-636">**resource**: Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-637">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-637">Return Values</span></span>

- <span data-ttu-id="6e366-638">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-638">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-639">NX_PTR_ERROR: Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6e366-639">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_resource_get_boolean"></a><span data-ttu-id="6e366-640">nx_lwm2m_resource_get_boolean</span><span class="sxs-lookup"><span data-stu-id="6e366-640">nx_lwm2m_resource_get_boolean</span></span>

<span data-ttu-id="6e366-641">Obtenha o valor de um Recurso Boolean</span><span class="sxs-lookup"><span data-stu-id="6e366-641">Get the value of a Boolean Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-642">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-642">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_boolean(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-643">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-643">Description</span></span>

<span data-ttu-id="6e366-644">O serviço recupera o valor de um Recurso Boolean.</span><span class="sxs-lookup"><span data-stu-id="6e366-644">The service retrieves the value of a Boolean Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-645">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-645">Parameters</span></span>

- <span data-ttu-id="6e366-646">**valor**: Ponteiro para descrição do valor do recurso.</span><span class="sxs-lookup"><span data-stu-id="6e366-646">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="6e366-647">**bool_ptr**: Ponte para o destino Valor Boolean.</span><span class="sxs-lookup"><span data-stu-id="6e366-647">**bool_ptr**: Pointer to the destination Boolean value.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-648">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-648">Return Values</span></span>

- <span data-ttu-id="6e366-649">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-649">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-650">**NX_LWM2M_BAD_ENCODING**: O valor do recurso não é um valor Boolean.</span><span class="sxs-lookup"><span data-stu-id="6e366-650">**NX_LWM2M_BAD_ENCODING**: The resource value is not a Boolean value.</span></span>

## <a name="nx_lwm2m_resource_get_float32"></a><span data-ttu-id="6e366-651">nx_lwm2m_resource_get_float32</span><span class="sxs-lookup"><span data-stu-id="6e366-651">nx_lwm2m_resource_get_float32</span></span>

<span data-ttu-id="6e366-652">Obtenha o valor de um recurso de ponto flutuante de 32 bits</span><span class="sxs-lookup"><span data-stu-id="6e366-652">Get the value of a 32-bit Floating Point Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-653">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-653">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_float32(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-654">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-654">Description</span></span>

<span data-ttu-id="6e366-655">O serviço recupera o valor de um recurso flutuante de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="6e366-655">The service retrieves the value of a 32-bit Floating Point Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-656">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-656">Parameters</span></span>

- <span data-ttu-id="6e366-657">**valor**: Ponteiro para descrição do valor do recurso.</span><span class="sxs-lookup"><span data-stu-id="6e366-657">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="6e366-658">**float32_ptr**: Ponte para o destino 32-Bit Floating Point valor.</span><span class="sxs-lookup"><span data-stu-id="6e366-658">**float32_ptr**: Pointer to the destination 32-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-659">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-659">Return Values</span></span>

- <span data-ttu-id="6e366-660">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-660">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-661">**NX_LWM2M_BAD_ENCODING**: O valor do recurso não é um valor de Ponto Flutuante.</span><span class="sxs-lookup"><span data-stu-id="6e366-661">**NX_LWM2M_BAD_ENCODING**: The resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_get_float64"></a><span data-ttu-id="6e366-662">nx_lwm2m_resource_get_float64</span><span class="sxs-lookup"><span data-stu-id="6e366-662">nx_lwm2m_resource_get_float64</span></span>

<span data-ttu-id="6e366-663">Obtenha o valor de um recurso de ponto flutuante de 64 bits</span><span class="sxs-lookup"><span data-stu-id="6e366-663">Get the value of a 64-bit Floating Point Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-664">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-664">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_float64(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-665">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-665">Description</span></span>

<span data-ttu-id="6e366-666">O serviço recupera o valor de um recurso flutuante de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="6e366-666">The service retrieves the value of a 64-bit Floating Point Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-667">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-667">Parameters</span></span>

- <span data-ttu-id="6e366-668">**valor**: Ponteiro para descrição do valor do recurso.</span><span class="sxs-lookup"><span data-stu-id="6e366-668">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="6e366-669">**float64_ptr**: Ponte para o destino 64-Bit Floating Point value.</span><span class="sxs-lookup"><span data-stu-id="6e366-669">**float64_ptr**: Pointer to the destination 64-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-670">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-670">Return Values</span></span>

- <span data-ttu-id="6e366-671">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-671">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-672">**NX_LWM2M_BAD_ENCODING**: O valor do recurso não é um valor de Ponto Flutuante.</span><span class="sxs-lookup"><span data-stu-id="6e366-672">**NX_LWM2M_BAD_ENCODING**: The resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_get_integer32"></a><span data-ttu-id="6e366-673">nx_lwm2m_resource_get_integer32</span><span class="sxs-lookup"><span data-stu-id="6e366-673">nx_lwm2m_resource_get_integer32</span></span>

<span data-ttu-id="6e366-674">Obtenha o valor de um recurso inteiro de 32 bits</span><span class="sxs-lookup"><span data-stu-id="6e366-674">Get the value of a 32-Bit Integer Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-675">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-675">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_integer32(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-676">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-676">Description</span></span>

<span data-ttu-id="6e366-677">O serviço recupera o valor de um recurso inteiro de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="6e366-677">The service retrieves the value of a 32-Bit Integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-678">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-678">Parameters</span></span>

- <span data-ttu-id="6e366-679">**valor**: Ponteiro para descrição do valor do recurso.</span><span class="sxs-lookup"><span data-stu-id="6e366-679">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="6e366-680">**int32_ptr**: Ponte para o destino valor inteiro de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="6e366-680">**int32_ptr**: Pointer to the destination 32-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-681">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-681">Return Values</span></span>

- <span data-ttu-id="6e366-682">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-682">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-683">**NX_LWM2M_BAD_ENCODING**: O valor do recurso não é um valor Inteiro, ou o valor Inteiro não se encaixa num número de 32 Bits.</span><span class="sxs-lookup"><span data-stu-id="6e366-683">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Integer value, or the Integer value doesn't fit in a 32-Bit number.</span></span>

## <a name="nx_lwm2m_resource_get_integer64"></a><span data-ttu-id="6e366-684">nx_lwm2m_resource_get_integer64</span><span class="sxs-lookup"><span data-stu-id="6e366-684">nx_lwm2m_resource_get_integer64</span></span>

<span data-ttu-id="6e366-685">Obtenha o valor de um recurso inteiro de 64 bits</span><span class="sxs-lookup"><span data-stu-id="6e366-685">Get the value of a 64-Bit Integer Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-686">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-686">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_integer64(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-687">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-687">Description</span></span>

<span data-ttu-id="6e366-688">O serviço recupera o valor de um recurso inteiro de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="6e366-688">The service retrieves the value of a 64-Bit Integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-689">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-689">Parameters</span></span>

- <span data-ttu-id="6e366-690">**valor**: Ponteiro para descrição do valor do recurso.</span><span class="sxs-lookup"><span data-stu-id="6e366-690">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="6e366-691">**int64_ptr**: Ponte para o destino 64-Bit Valor Inteiro.</span><span class="sxs-lookup"><span data-stu-id="6e366-691">**int64_ptr**: Pointer to the destination 64-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-692">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-692">Return Values</span></span>

- <span data-ttu-id="6e366-693">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-693">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-694">**NX_LWM2M_BAD_ENCODING**: O valor do recurso não é um valor Inteiro.</span><span class="sxs-lookup"><span data-stu-id="6e366-694">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Integer value.</span></span>

## <a name="nx_lwm2m_resource_get_objlnk"></a><span data-ttu-id="6e366-695">nx_lwm2m_resource_get_objlnk</span><span class="sxs-lookup"><span data-stu-id="6e366-695">nx_lwm2m_resource_get_objlnk</span></span>

<span data-ttu-id="6e366-696">Obtenha o valor de um recurso de ligação de objeto</span><span class="sxs-lookup"><span data-stu-id="6e366-696">Get the value of an Object Link Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-697">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-697">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_objlnk(const NX_LWM2M_RESOURCE *value,
                                    NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-698">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-698">Description</span></span>

<span data-ttu-id="6e366-699">O serviço recupera o valor de um recurso de ligação de objetos.</span><span class="sxs-lookup"><span data-stu-id="6e366-699">The service retrieves the value of an Object Link Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-700">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-700">Parameters</span></span>

- <span data-ttu-id="6e366-701">**valor**: Ponteiro para descrição do valor do recurso.</span><span class="sxs-lookup"><span data-stu-id="6e366-701">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="6e366-702">**objlnk_ptr**: Ponter para o valor de Link do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="6e366-702">**objlnk_ptr**: Pointer to the destination Object Link value.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-703">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-703">Return Values</span></span>

- <span data-ttu-id="6e366-704">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-704">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-705">**NX_LWM2M_BAD_ENCODING**: O valor do recurso não é um valor de Ligação de Objeto.</span><span class="sxs-lookup"><span data-stu-id="6e366-705">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Object Link value.</span></span>

## <a name="nx_lwm2m_resource_get_opaque"></a><span data-ttu-id="6e366-706">nx_lwm2m_resource_get_opaque</span><span class="sxs-lookup"><span data-stu-id="6e366-706">nx_lwm2m_resource_get_opaque</span></span>

<span data-ttu-id="6e366-707">Obtenha o valor de um Recurso Opaco</span><span class="sxs-lookup"><span data-stu-id="6e366-707">Get the value of an Opaque Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-708">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-708">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_opaque(const NX_LWM2M_RESOURCE *value,
            const VOID **opaque_ptr_ptr, UINT *opaque_length_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-709">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-709">Description</span></span>

<span data-ttu-id="6e366-710">O serviço recupera o valor de um Recurso Opaco.</span><span class="sxs-lookup"><span data-stu-id="6e366-710">The service retrieves the value of an Opaque Resource.</span></span>

<span data-ttu-id="6e366-711">Um valor de recurso opaco consiste num ponteiro para um tampão e um comprimento.</span><span class="sxs-lookup"><span data-stu-id="6e366-711">An opaque resource value consists of a pointer to a buffer and a length.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-712">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-712">Parameters</span></span>

- <span data-ttu-id="6e366-713">**valor**: Ponteiro para descrição do valor do recurso.</span><span class="sxs-lookup"><span data-stu-id="6e366-713">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="6e366-714">**opaque_ptr_ptr**: Ponteiro para o ponteiro tampão opaco de destino.</span><span class="sxs-lookup"><span data-stu-id="6e366-714">**opaque_ptr_ptr**: Pointer to the destination opaque buffer pointer.</span></span>
- <span data-ttu-id="6e366-715">**opaque_length_ptr**: Ponteiro para o comprimento do tampão opaco de destino.</span><span class="sxs-lookup"><span data-stu-id="6e366-715">**opaque_length_ptr**: Pointer to the destination opaque buffer length.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-716">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-716">Return Values</span></span>

- <span data-ttu-id="6e366-717">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-717">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-718">**NX_LWM2M_BAD_ENCODING**: O valor do recurso não é um valor opaco.</span><span class="sxs-lookup"><span data-stu-id="6e366-718">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Opaque value.</span></span>

## <a name="nx_lwm2m_resource_get_string"></a><span data-ttu-id="6e366-719">nx_lwm2m_resource_get_string</span><span class="sxs-lookup"><span data-stu-id="6e366-719">nx_lwm2m_resource_get_string</span></span>

<span data-ttu-id="6e366-720">Obtenha o valor de um recurso de corda</span><span class="sxs-lookup"><span data-stu-id="6e366-720">Get the value of a String Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-721">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-721">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_string(const NX_LWM2M_RESOURCE *value,
            const CHAR **string_ptr_ptr, UINT *string_length_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-722">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-722">Description</span></span>

<span data-ttu-id="6e366-723">O serviço recupera o valor de um Recurso de Corda.</span><span class="sxs-lookup"><span data-stu-id="6e366-723">The service retrieves the value of a String Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-724">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-724">Parameters</span></span>

- <span data-ttu-id="6e366-725">**valor**: Ponteiro para descrição do valor do recurso.</span><span class="sxs-lookup"><span data-stu-id="6e366-725">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="6e366-726">**string_ptr_ptr**: Ponteiro para o ponteiro de cadeia de destino.</span><span class="sxs-lookup"><span data-stu-id="6e366-726">**string_ptr_ptr**: Pointer to the destination string pointer.</span></span>
- <span data-ttu-id="6e366-727">**string_length_ptr**: Ponte até ao comprimento da corda de destino.</span><span class="sxs-lookup"><span data-stu-id="6e366-727">**string_length_ptr**: Pointer to the destination string length.</span></span> <span data-ttu-id="6e366-728">Pode ser NU SE a cadeia estiver nula.</span><span class="sxs-lookup"><span data-stu-id="6e366-728">Can be NULL if the string is null-terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-729">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-729">Return Values</span></span>

- <span data-ttu-id="6e366-730">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-730">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-731">**NX_LWM2M_BAD_ENCODING**: O valor do recurso não é um valor de corda.</span><span class="sxs-lookup"><span data-stu-id="6e366-731">**NX_LWM2M_BAD_ENCODING**: The resource value is not a String value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_boolean"></a><span data-ttu-id="6e366-732">nx_lwm2m_resource_multiple_get_boolean</span><span class="sxs-lookup"><span data-stu-id="6e366-732">nx_lwm2m_resource_multiple_get_boolean</span></span>

<span data-ttu-id="6e366-733">Obtenha o valor de uma Instância de Recursos Múltiplos de Recurso Boolean</span><span class="sxs-lookup"><span data-stu-id="6e366-733">Get the value of a Boolean Resource Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-734">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-734">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_boolean(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-735">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-735">Description</span></span>

<span data-ttu-id="6e366-736">O serviço recupera o valor de uma Instância de Recursos Boolean de um Recurso Múltiplo.</span><span class="sxs-lookup"><span data-stu-id="6e366-736">The service retrieves the value of a Boolean Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-737">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-737">Parameters</span></span>

- <span data-ttu-id="6e366-738">**valor**: Ponteiro para a descrição do valor de recursos múltiplos.</span><span class="sxs-lookup"><span data-stu-id="6e366-738">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="6e366-739">**índice**: Índice da Instância para recuperar na matriz de valor de recurso.</span><span class="sxs-lookup"><span data-stu-id="6e366-739">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="6e366-740">**instance_id_ptr**: Ponteiro para o destino Identificação de Exemplo.</span><span class="sxs-lookup"><span data-stu-id="6e366-740">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="6e366-741">**bool_ptr**: Ponte para o destino Valor Boolean.</span><span class="sxs-lookup"><span data-stu-id="6e366-741">**bool_ptr**: Pointer to the destination Boolean value.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-742">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-742">Return Values</span></span>

- <span data-ttu-id="6e366-743">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-743">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-744">**NX_LWM2M_BAD_PARAMETER**: O índice está fora de alcance.</span><span class="sxs-lookup"><span data-stu-id="6e366-744">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="6e366-745">**NX_LWM2M_BAD_ENCODING**: O recurso não é um recurso múltiplo, ou o valor do recurso não é um valor Boolean.</span><span class="sxs-lookup"><span data-stu-id="6e366-745">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not a Boolean value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_float32"></a><span data-ttu-id="6e366-746">nx_lwm2m_resource_multiple_get_float32</span><span class="sxs-lookup"><span data-stu-id="6e366-746">nx_lwm2m_resource_multiple_get_float32</span></span>

<span data-ttu-id="6e366-747">Obtenha o valor de uma instância de recursos múltiplos de ponto flutuante de 32 bits</span><span class="sxs-lookup"><span data-stu-id="6e366-747">Get the value of a 32-bit Floating Point Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-748">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-748">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_float32(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-749">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-749">Description</span></span>

<span data-ttu-id="6e366-750">O serviço recupera o valor de uma instância de recursos flutuantes de 32 bits de um recurso múltiplo.</span><span class="sxs-lookup"><span data-stu-id="6e366-750">The service retrieves the value of a 32-bit Floating Point Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-751">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-751">Parameters</span></span>

- <span data-ttu-id="6e366-752">**valor**: Ponteiro para a descrição do valor de recursos múltiplos.</span><span class="sxs-lookup"><span data-stu-id="6e366-752">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="6e366-753">**índice**: Índice da Instância para recuperar na matriz de valor de recurso.</span><span class="sxs-lookup"><span data-stu-id="6e366-753">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="6e366-754">**instance_id_ptr**: Ponteiro para o destino Identificação de Exemplo.</span><span class="sxs-lookup"><span data-stu-id="6e366-754">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="6e366-755">**float32_ptr**: Ponte para o destino 32-Bit Floating Point valor.</span><span class="sxs-lookup"><span data-stu-id="6e366-755">**float32_ptr**: Pointer to the destination 32-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-756">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-756">Return Values</span></span>

- <span data-ttu-id="6e366-757">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-757">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-758">**NX_LWM2M_BAD_PARAMETER**: O índice está fora de alcance.</span><span class="sxs-lookup"><span data-stu-id="6e366-758">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="6e366-759">**NX_LWM2M_BAD_ENCODING**: O recurso não é um recurso múltiplo, ou o valor do recurso não é um valor de Ponto Flutuante.</span><span class="sxs-lookup"><span data-stu-id="6e366-759">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_float64"></a><span data-ttu-id="6e366-760">nx_lwm2m_resource_multiple_get_float64</span><span class="sxs-lookup"><span data-stu-id="6e366-760">nx_lwm2m_resource_multiple_get_float64</span></span>

<span data-ttu-id="6e366-761">Obtenha o valor de uma instância de recursos múltiplos de ponto flutuante de 64 bits</span><span class="sxs-lookup"><span data-stu-id="6e366-761">Get the value of a 64-bit Floating Point Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-762">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-762">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_float64(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-763">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-763">Description</span></span>

<span data-ttu-id="6e366-764">O serviço recupera o valor de uma instância de recursos flutuantes de 64 bits de um recurso múltiplo.</span><span class="sxs-lookup"><span data-stu-id="6e366-764">The service retrieves the value of a 64-bit Floating Point Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-765">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-765">Parameters</span></span>

- <span data-ttu-id="6e366-766">**valor**: Ponteiro para a descrição do valor de recursos múltiplos.</span><span class="sxs-lookup"><span data-stu-id="6e366-766">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="6e366-767">**índice**: Índice da Instância para recuperar na matriz de valor de recurso.</span><span class="sxs-lookup"><span data-stu-id="6e366-767">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="6e366-768">**instance_id_ptr**: Ponteiro para o destino Identificação de Exemplo.</span><span class="sxs-lookup"><span data-stu-id="6e366-768">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="6e366-769">**float64_ptr**: Ponte para o destino 64-Bit Floating Point value.</span><span class="sxs-lookup"><span data-stu-id="6e366-769">**float64_ptr**: Pointer to the destination 64-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-770">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-770">Return Values</span></span>

- <span data-ttu-id="6e366-771">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-771">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-772">**NX_LWM2M_BAD_PARAMETER**: O índice está fora de alcance.</span><span class="sxs-lookup"><span data-stu-id="6e366-772">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="6e366-773">**NX_LWM2M_BAD_ENCODING**: O recurso não é um recurso múltiplo, ou o valor do recurso não é um valor de Ponto Flutuante.</span><span class="sxs-lookup"><span data-stu-id="6e366-773">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_integer32"></a><span data-ttu-id="6e366-774">nx_lwm2m_resource_multiple_get_integer32</span><span class="sxs-lookup"><span data-stu-id="6e366-774">nx_lwm2m_resource_multiple_get_integer32</span></span>

<span data-ttu-id="6e366-775">Obtenha o valor de uma instância de recursos múltiplos de 32 bits</span><span class="sxs-lookup"><span data-stu-id="6e366-775">Get the value of a 32-Bit Integer Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-776">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-776">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_integer32(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-777">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-777">Description</span></span>

<span data-ttu-id="6e366-778">O serviço recupera o valor de uma instância de recursos inteiros de 32 bits de um recurso múltiplo.</span><span class="sxs-lookup"><span data-stu-id="6e366-778">The service retrieves the value of a 32-Bit Integer Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-779">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-779">Parameters</span></span>

- <span data-ttu-id="6e366-780">**valor**: Ponteiro para a descrição do valor de recursos múltiplos.</span><span class="sxs-lookup"><span data-stu-id="6e366-780">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="6e366-781">**índice**: Índice da Instância para recuperar na matriz de valor de recurso.</span><span class="sxs-lookup"><span data-stu-id="6e366-781">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="6e366-782">**instance_id_ptr**: Ponteiro para o destino Identificação de Exemplo.</span><span class="sxs-lookup"><span data-stu-id="6e366-782">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="6e366-783">**int32_ptr**: Ponte para o destino valor inteiro de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="6e366-783">**int32_ptr**: Pointer to the destination 32-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-784">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-784">Return Values</span></span>

- <span data-ttu-id="6e366-785">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-785">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-786">**NX_LWM2M_BAD_PARAMETER**: O índice está fora de alcance.</span><span class="sxs-lookup"><span data-stu-id="6e366-786">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="6e366-787">**NX_LWM2M_BAD_ENCODING**: O recurso não é um recurso múltiplo, ou o valor do recurso não é um valor Inteiro, ou o valor Inteiro não se encaixa num número de 32 Bits.</span><span class="sxs-lookup"><span data-stu-id="6e366-787">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Integer value, or the Integer value doesn't fit in a 32-Bit number.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_integer64"></a><span data-ttu-id="6e366-788">nx_lwm2m_resource_multiple_get_integer64</span><span class="sxs-lookup"><span data-stu-id="6e366-788">nx_lwm2m_resource_multiple_get_integer64</span></span>

<span data-ttu-id="6e366-789">Obtenha o valor de uma instância de recursos múltiplos de 64 bits</span><span class="sxs-lookup"><span data-stu-id="6e366-789">Get the value of a 64-Bit Integer Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-790">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-790">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_integer64(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-791">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-791">Description</span></span>

<span data-ttu-id="6e366-792">O serviço recupera o valor de uma instância de recursos inteiros de 64 bits de um recurso múltiplo.</span><span class="sxs-lookup"><span data-stu-id="6e366-792">The service retrieves the value of a 64-Bit Integer Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-793">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-793">Parameters</span></span>

- <span data-ttu-id="6e366-794">**valor**: Ponteiro para a descrição do valor de recursos múltiplos.</span><span class="sxs-lookup"><span data-stu-id="6e366-794">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="6e366-795">**índice**: Índice da Instância para recuperar na matriz de valor de recurso.</span><span class="sxs-lookup"><span data-stu-id="6e366-795">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="6e366-796">**instance_id_ptr**: Ponteiro para o destino Identificação de Exemplo.</span><span class="sxs-lookup"><span data-stu-id="6e366-796">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="6e366-797">**int64_ptr**: Ponte para o destino 64-Bit Valor Inteiro.</span><span class="sxs-lookup"><span data-stu-id="6e366-797">**int64_ptr**: Pointer to the destination 64-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-798">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-798">Return Values</span></span>

- <span data-ttu-id="6e366-799">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-799">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-800">**NX_LWM2M_BAD_PARAMETER**: O índice está fora de alcance.</span><span class="sxs-lookup"><span data-stu-id="6e366-800">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="6e366-801">**NX_LWM2M_BAD_ENCODING**: O recurso não é um recurso múltiplo, ou o valor do recurso não é um valor Inteiro.</span><span class="sxs-lookup"><span data-stu-id="6e366-801">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Integer value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_objlnk"></a><span data-ttu-id="6e366-802">nx_lwm2m_resource_multiple_get_objlnk</span><span class="sxs-lookup"><span data-stu-id="6e366-802">nx_lwm2m_resource_multiple_get_objlnk</span></span>

<span data-ttu-id="6e366-803">Obtenha o valor de uma instância de recursos múltiplos de ligação de objetos</span><span class="sxs-lookup"><span data-stu-id="6e366-803">Get the value of an Object Link Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-804">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-804">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_objlnk(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-805">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-805">Description</span></span>

<span data-ttu-id="6e366-806">O serviço recupera o valor de uma instância de recurso de ligação de objetos a partir de um recurso múltiplo.</span><span class="sxs-lookup"><span data-stu-id="6e366-806">The service retrieves the value of an Object Link Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-807">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-807">Parameters</span></span>

- <span data-ttu-id="6e366-808">**valor**: Ponteiro para a descrição do valor de recursos múltiplos.</span><span class="sxs-lookup"><span data-stu-id="6e366-808">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="6e366-809">**índice**: Índice da Instância para recuperar na matriz de valor de recurso.</span><span class="sxs-lookup"><span data-stu-id="6e366-809">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="6e366-810">**instance_id_ptr**: Ponteiro para o destino Identificação de Exemplo.</span><span class="sxs-lookup"><span data-stu-id="6e366-810">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="6e366-811">**objlnk_ptr**: Ponter para o valor de Link do objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="6e366-811">**objlnk_ptr**: Pointer to the destination Object Link value.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-812">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-812">Return Values</span></span>

- <span data-ttu-id="6e366-813">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-813">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-814">**NX_LWM2M_BAD_PARAMETER**: O índice está fora de alcance.</span><span class="sxs-lookup"><span data-stu-id="6e366-814">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="6e366-815">**NX_LWM2M_BAD_ENCODING**: O recurso não é um recurso múltiplo, ou o valor do recurso não é um valor de Ligação de Objeto.</span><span class="sxs-lookup"><span data-stu-id="6e366-815">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Object Link value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_opaque"></a><span data-ttu-id="6e366-816">nx_lwm2m_resource_multiple_get_opaque</span><span class="sxs-lookup"><span data-stu-id="6e366-816">nx_lwm2m_resource_multiple_get_opaque</span></span>

<span data-ttu-id="6e366-817">Obtenha o valor de uma instância de recursos múltiplos opaco</span><span class="sxs-lookup"><span data-stu-id="6e366-817">Get the value of an Opaque Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-818">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-818">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_opaque(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const VOID **opaque_ptr_ptr,
    UINT *opaque_length_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-819">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-819">Description</span></span>

<span data-ttu-id="6e366-820">O serviço recupera o valor de uma Instância de Recursos Opacos a partir de um Recurso Múltiplo.</span><span class="sxs-lookup"><span data-stu-id="6e366-820">The service retrieves the value of an Opaque Resource Instance from a Multiple Resource.</span></span>

<span data-ttu-id="6e366-821">Um valor de recurso opaco consiste num ponteiro para um tampão e um comprimento.</span><span class="sxs-lookup"><span data-stu-id="6e366-821">An opaque resource value consists of a pointer to a buffer and a length.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-822">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-822">Parameters</span></span>

- <span data-ttu-id="6e366-823">**valor**: Ponteiro para a descrição do valor de recursos múltiplos.</span><span class="sxs-lookup"><span data-stu-id="6e366-823">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="6e366-824">**índice**: Índice da Instância para recuperar na matriz de valor de recurso.</span><span class="sxs-lookup"><span data-stu-id="6e366-824">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="6e366-825">**instance_id_ptr**: Ponteiro para o destino Identificação de Exemplo.</span><span class="sxs-lookup"><span data-stu-id="6e366-825">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="6e366-826">**opaque_ptr_ptr**: Ponteiro para o ponteiro tampão opaco de destino.</span><span class="sxs-lookup"><span data-stu-id="6e366-826">**opaque_ptr_ptr**: Pointer to the destination opaque buffer pointer.</span></span>
- <span data-ttu-id="6e366-827">**opaque_length_ptr**: Ponteiro para o comprimento do tampão opaco de destino.</span><span class="sxs-lookup"><span data-stu-id="6e366-827">**opaque_length_ptr**: Pointer to the destination opaque buffer length.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-828">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-828">Return Values</span></span>

- <span data-ttu-id="6e366-829">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-829">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-830">**NX_LWM2M_BAD_PARAMETER**: O índice está fora de alcance.</span><span class="sxs-lookup"><span data-stu-id="6e366-830">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="6e366-831">**NX_LWM2M_BAD_ENCODING**: O recurso não é um recurso múltiplo, ou o valor do recurso não é um valor opaco.</span><span class="sxs-lookup"><span data-stu-id="6e366-831">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Opaque value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_string"></a><span data-ttu-id="6e366-832">nx_lwm2m_resource_multiple_get_string</span><span class="sxs-lookup"><span data-stu-id="6e366-832">nx_lwm2m_resource_multiple_get_string</span></span>

<span data-ttu-id="6e366-833">Obtenha o valor de uma instância de recursos múltiplos de cordas</span><span class="sxs-lookup"><span data-stu-id="6e366-833">Get the value of a String Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6e366-834">Prototype</span><span class="sxs-lookup"><span data-stu-id="6e366-834">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_string(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const CHAR **string_ptr_ptr,
    UINT *string_length_ptr);
```

### <a name="description"></a><span data-ttu-id="6e366-835">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e366-835">Description</span></span>

<span data-ttu-id="6e366-836">O serviço recupera o valor de uma Instância de Recursos de Cadeia de um Recurso Múltiplo.</span><span class="sxs-lookup"><span data-stu-id="6e366-836">The service retrieves the value of a String Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="6e366-837">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e366-837">Parameters</span></span>

- <span data-ttu-id="6e366-838">**valor**: Ponteiro para a descrição do valor de recursos múltiplos.</span><span class="sxs-lookup"><span data-stu-id="6e366-838">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="6e366-839">**índice**: Índice da Instância para recuperar na matriz de valor de recurso.</span><span class="sxs-lookup"><span data-stu-id="6e366-839">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="6e366-840">**instance_id_ptr**: Ponteiro para o destino Identificação de Exemplo.</span><span class="sxs-lookup"><span data-stu-id="6e366-840">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="6e366-841">**string_ptr_ptr**: Ponteiro para o ponteiro de cadeia de destino.</span><span class="sxs-lookup"><span data-stu-id="6e366-841">**string_ptr_ptr**: Pointer to the destination string pointer.</span></span>
- <span data-ttu-id="6e366-842">**string_length_ptr**: Ponte até ao comprimento da corda de destino.</span><span class="sxs-lookup"><span data-stu-id="6e366-842">**string_length_ptr**: Pointer to the destination string length.</span></span> <span data-ttu-id="6e366-843">Pode ser NU SE a cadeia estiver nula.</span><span class="sxs-lookup"><span data-stu-id="6e366-843">Can be NULL if the string is null-terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="6e366-844">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6e366-844">Return Values</span></span>

- <span data-ttu-id="6e366-845">**NX_SUCCESS:** Operação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6e366-845">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="6e366-846">**NX_LWM2M_BAD_PARAMETER**: O índice está fora de alcance.</span><span class="sxs-lookup"><span data-stu-id="6e366-846">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="6e366-847">**NX_LWM2M_BAD_ENCODING**: O recurso não é um recurso múltiplo, ou o valor da instância não é um valor de corda.</span><span class="sxs-lookup"><span data-stu-id="6e366-847">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the instance value is not a String value.</span></span>
