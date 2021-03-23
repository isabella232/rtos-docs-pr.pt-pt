---
title: Capítulo 3 - Descrição dos serviços do Protocolo Azure RTOS NetX Ponto-a-Ponto (PPP)
description: Este capítulo contém uma descrição de todos os serviços de PPP Azure RTOS NetX (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f24d7366d27a8223b069a54ef7b93f6b3e38bf3a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826653"
---
# <a name="chapter-3---description-of-azure-rtos-netx-point-to-point-protocol-ppp-services"></a><span data-ttu-id="069e8-103">Capítulo 3 - Descrição dos serviços do Protocolo Azure RTOS NetX Ponto-a-Ponto (PPP)</span><span class="sxs-lookup"><span data-stu-id="069e8-103">Chapter 3 - Description of Azure RTOS NetX Point-to-Point Protocol (PPP) services</span></span>

<span data-ttu-id="069e8-104">Este capítulo contém uma descrição de todos os serviços de PPP Azure RTOS NetX (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="069e8-104">This chapter contains a description of all Azure RTOS NetX PPP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="069e8-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="069e8-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="069e8-106">**nx_ppp_byte_receive**: *Receba um byte da SÉRIE ISR*</span><span class="sxs-lookup"><span data-stu-id="069e8-106">**nx_ppp_byte_receive**: *Receive a byte from serial ISR*</span></span>
- <span data-ttu-id="069e8-107">**nx_ppp_chap_challenge**: *Gerar um desafio CHAP*</span><span class="sxs-lookup"><span data-stu-id="069e8-107">**nx_ppp_chap_challenge**: *Generate a CHAP challenge*</span></span>
- <span data-ttu-id="069e8-108">**nx_ppp_chap_enable**: *Ativar a autenticação CHAP*</span><span class="sxs-lookup"><span data-stu-id="069e8-108">**nx_ppp_chap_enable**: *Enable CHAP authentication*</span></span>
- <span data-ttu-id="069e8-109">**nx_ppp_create**: *Criar uma instância PPP*</span><span class="sxs-lookup"><span data-stu-id="069e8-109">**nx_ppp_create**: *Create a PPP instance*</span></span>
- <span data-ttu-id="069e8-110">**nx_ppp_delete**: *Eliminar uma instância de PPP*</span><span class="sxs-lookup"><span data-stu-id="069e8-110">**nx_ppp_delete**: *Delete a PPP instance*</span></span>
- <span data-ttu-id="069e8-111">**nx_ppp_dns_address_get**: *Obtenha endereço IP DNS*</span><span class="sxs-lookup"><span data-stu-id="069e8-111">**nx_ppp_dns_address_get**: *Get DNS IP address*</span></span>
- <span data-ttu-id="069e8-112">**nx_ppp_dns_address_set**:*Definir endereço IP do servidor DNS*</span><span class="sxs-lookup"><span data-stu-id="069e8-112">**nx_ppp_dns_address_set**:*Set DNS Server IP address*</span></span>
- <span data-ttu-id="069e8-113">**nx_ppp_secondary_dns_address_get**: *Obtenha o endereço IP do servidor DNS Secundário*</span><span class="sxs-lookup"><span data-stu-id="069e8-113">**nx_ppp_secondary_dns_address_get**: *Get Secondary DNS Server IP address*</span></span>
- <span data-ttu-id="069e8-114">**nx_ppp_secondary_dns_address_set**: *Definir Secondary_DNS endereço IP do servidor*</span><span class="sxs-lookup"><span data-stu-id="069e8-114">**nx_ppp_secondary_dns_address_set**: *Set Secondary_DNS Server IP address*</span></span>
- <span data-ttu-id="069e8-115">**nx_ppp_interface_index_get**: *Obtenha índice de interface IP*</span><span class="sxs-lookup"><span data-stu-id="069e8-115">**nx_ppp_interface_index_get**: *Get IP interface index*</span></span>
- <span data-ttu-id="069e8-116">**nx_ppp_ip_address_assign**: *Atribuir endereços IP para IPCP*</span><span class="sxs-lookup"><span data-stu-id="069e8-116">**nx_ppp_ip_address_assign**: *Assign IP addresses for IPCP*</span></span>
- <span data-ttu-id="069e8-117">**nx_ppp_link_down_notify**: *Notifique o pedido no link para baixo*</span><span class="sxs-lookup"><span data-stu-id="069e8-117">**nx_ppp_link_down_notify**: *Notify application on link down*</span></span>
- <span data-ttu-id="069e8-118">**nx_ppp_link_up_notify**: *Notificar o pedido no link*</span><span class="sxs-lookup"><span data-stu-id="069e8-118">**nx_ppp_link_up_notify**: *Notify application on link up*</span></span>
- <span data-ttu-id="069e8-119">**nx_ppp_nak_authentication_notify**: Notificar o pedido se a *NAK de autenticação for recebida*</span><span class="sxs-lookup"><span data-stu-id="069e8-119">**nx_ppp_nak_authentication_notify**: *Notify application if authentication NAK is received*</span></span>
- <span data-ttu-id="069e8-120">**nx_ppp_pap_enable**: *Ativar a autenticação do PAP*</span><span class="sxs-lookup"><span data-stu-id="069e8-120">**nx_ppp_pap_enable**: *Enable PAP authentication*</span></span>
- <span data-ttu-id="069e8-121">**nx_ppp_ping_request**: *Enviar um pedido de eco LCP*</span><span class="sxs-lookup"><span data-stu-id="069e8-121">**nx_ppp_ping_request**: *Send an LCP echo request*</span></span>
- <span data-ttu-id="069e8-122">**nx_ppp_raw_string_send**: *Enviar cadeia não PPP*</span><span class="sxs-lookup"><span data-stu-id="069e8-122">**nx_ppp_raw_string_send**: *Send non PPP string*</span></span>
- <span data-ttu-id="069e8-123">**nx_ppp_restart**: *Reiniciar o processamento de PPP*</span><span class="sxs-lookup"><span data-stu-id="069e8-123">**nx_ppp_restart**: *Restart PPP processing*</span></span>
- <span data-ttu-id="069e8-124">**nx_ppp_start**: *Iniciar o processamento de PPP*</span><span class="sxs-lookup"><span data-stu-id="069e8-124">**nx_ppp_start**: *Start PPP processing*</span></span>
- <span data-ttu-id="069e8-125">**nx_ppp_status_get**: *Obtenha o estado atual de PPP*</span><span class="sxs-lookup"><span data-stu-id="069e8-125">**nx_ppp_status_get**: *Get current PPP status*</span></span>
- <span data-ttu-id="069e8-126">**nx_ppp_stop**: *Parar o processamento de PPP*</span><span class="sxs-lookup"><span data-stu-id="069e8-126">**nx_ppp_stop**: *Stop PPP processing*</span></span>
- <span data-ttu-id="069e8-127">**nx_ppp_packet_receive**: *Receber pacote de PPP*</span><span class="sxs-lookup"><span data-stu-id="069e8-127">**nx_ppp_packet_receive**: *Receive PPP packet*</span></span>
- <span data-ttu-id="069e8-128">**nx_ppp_packet_send_set**: *Definir função de envio de pacote de PPP*</span><span class="sxs-lookup"><span data-stu-id="069e8-128">**nx_ppp_packet_send_set**: *Set PPP packet send function*</span></span>

## <a name="nx_ppp_byte_receive"></a><span data-ttu-id="069e8-129">nx_ppp_byte_receive</span><span class="sxs-lookup"><span data-stu-id="069e8-129">nx_ppp_byte_receive</span></span>

<span data-ttu-id="069e8-130">Receba um byte da SÉRIE ISR</span><span class="sxs-lookup"><span data-stu-id="069e8-130">Receive a byte from serial ISR</span></span>

### <a name="prototype"></a><span data-ttu-id="069e8-131">Prototype</span><span class="sxs-lookup"><span data-stu-id="069e8-131">Prototype</span></span>

```c
UINT nx_ppp_byte_receive(NX_PPP *ppp_ptr, UCHAR byte);
```

### <a name="description"></a><span data-ttu-id="069e8-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="069e8-132">Description</span></span>

<span data-ttu-id="069e8-133">Este serviço é normalmente chamado do controlador em série Interrupt Service Routine (ISR) para transferir um byte recebido para PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-133">This service is typically called from the application’s serial driver Interrupt Service Routine (ISR) to transfer a received byte to PPP.</span></span> <span data-ttu-id="069e8-134">Quando chamado, esta rotina coloca o byte recebido num tampão de byte circular e notifica o fio de PPP apropriado para o processamento.</span><span class="sxs-lookup"><span data-stu-id="069e8-134">When called, this routine places the received byte into a circular byte buffer and notifies the appropriate PPP thread for processing.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="069e8-135">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="069e8-135">Input Parameters</span></span>

- <span data-ttu-id="069e8-136">**ppp_ptr**: Ponteiro para o bloco de controlo PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-136">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="069e8-137">**byte**: Byte recebido de dispositivo de série</span><span class="sxs-lookup"><span data-stu-id="069e8-137">**byte**: Byte received from serial device</span></span>

### <a name="return-values"></a><span data-ttu-id="069e8-138">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="069e8-138">Return Values</span></span>

- <span data-ttu-id="069e8-139">**NX_SUCCESS**: (0x00) Adição de PPP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="069e8-139">**NX_SUCCESS**: (0x00) Successful PPP byte receive.</span></span>
- <span data-ttu-id="069e8-140">**NX_PPP_BUFFER_FULL**: (0xB1) O tampão de série PPP já está cheio.</span><span class="sxs-lookup"><span data-stu-id="069e8-140">**NX_PPP_BUFFER_FULL**: (0xB1) PPP serial buffer is already full.</span></span>
- <span data-ttu-id="069e8-141">NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.</span><span class="sxs-lookup"><span data-stu-id="069e8-141">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="069e8-142">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="069e8-142">Allowed From</span></span>

<span data-ttu-id="069e8-143">Threads, ISRs</span><span class="sxs-lookup"><span data-stu-id="069e8-143">Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="069e8-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069e8-144">Example</span></span>

```c
/* Notify “my_ppp” of a received byte. */
status =  nx_ppp_byte_receive(&my_ppp, new_byte);

/* If status is NX_SUCCESS the received byte was successfully
   buffered. */
```

## <a name="nx_ppp_chap_challenge"></a><span data-ttu-id="069e8-145">nx_ppp_chap_challenge</span><span class="sxs-lookup"><span data-stu-id="069e8-145">nx_ppp_chap_challenge</span></span>

<span data-ttu-id="069e8-146">Gerar um desafio CHAP</span><span class="sxs-lookup"><span data-stu-id="069e8-146">Generate a CHAP challenge</span></span>

### <a name="prototype"></a><span data-ttu-id="069e8-147">Prototype</span><span class="sxs-lookup"><span data-stu-id="069e8-147">Prototype</span></span>

```c
UINT nx_ppp_chap_challenge(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="069e8-148">Descrição</span><span class="sxs-lookup"><span data-stu-id="069e8-148">Description</span></span>

<span data-ttu-id="069e8-149">Este serviço inicia um desafio CHAP depois da ligação PPP já estar em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="069e8-149">This service initiates a CHAP challenge after the PPP connection is already up and running.</span></span> <span data-ttu-id="069e8-150">Isto dá à aplicação a capacidade de verificar a autenticidade da ligação numa base periódica.</span><span class="sxs-lookup"><span data-stu-id="069e8-150">This gives the application the ability to verify the authenticity of the connection on a periodic basis.</span></span> <span data-ttu-id="069e8-151">Se o desafio não for bem sucedido, a ligação PPP está fechada.</span><span class="sxs-lookup"><span data-stu-id="069e8-151">If the challenge is unsuccessful, the PPP link is closed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="069e8-152">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="069e8-152">Input Parameters</span></span>

- <span data-ttu-id="069e8-153">**ppp_ptr**: Ponteiro para o bloco de controlo PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-153">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="069e8-154">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="069e8-154">Return Values</span></span>

- <span data-ttu-id="069e8-155">**NX_SUCCESS**: (0x00) Desafio PPP bem sucedido iniciado.</span><span class="sxs-lookup"><span data-stu-id="069e8-155">**NX_SUCCESS**: (0x00) Successful PPP challenge initiated.</span></span>
- <span data-ttu-id="069e8-156">**NX_PPP_FAILURE**: (0xB0) Desafio PPP inválido, CHAP foi habilitado apenas para resposta.</span><span class="sxs-lookup"><span data-stu-id="069e8-156">**NX_PPP_FAILURE**: (0xB0) Invalid PPP challenge, CHAP was enabled only for response.</span></span>
- <span data-ttu-id="069e8-157">**NX_NOT_IMPLEMENTED**: (0x80) a lógica CHAP foi desativada através de NX_PPP_DISABLE_CHAP.</span><span class="sxs-lookup"><span data-stu-id="069e8-157">**NX_NOT_IMPLEMENTED**: (0x80) CHAP logic was disabled via NX_PPP_DISABLE_CHAP.</span></span>
- <span data-ttu-id="069e8-158">NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.</span><span class="sxs-lookup"><span data-stu-id="069e8-158">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="069e8-159">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="069e8-159">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="069e8-160">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="069e8-160">Allowed From</span></span>

<span data-ttu-id="069e8-161">Fios</span><span class="sxs-lookup"><span data-stu-id="069e8-161">Threads</span></span>

### <a name="example"></a><span data-ttu-id="069e8-162">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069e8-162">Example</span></span>

```c
/* Initiate a PPP challenge for instance “my_ppp”. */
status =  nx_ppp_chap_challenge(&my_ppp);

/* If status is NX_SUCCESS a CHAP challenge “my_ppp” was successfully 
initiated. */
```

## <a name="nx_ppp_chap_enable"></a><span data-ttu-id="069e8-163">nx_ppp_chap_enable</span><span class="sxs-lookup"><span data-stu-id="069e8-163">nx_ppp_chap_enable</span></span>

<span data-ttu-id="069e8-164">Ativar a autenticação CHAP</span><span class="sxs-lookup"><span data-stu-id="069e8-164">Enable CHAP authentication</span></span>

### <a name="prototype"></a><span data-ttu-id="069e8-165">Prototype</span><span class="sxs-lookup"><span data-stu-id="069e8-165">Prototype</span></span>

```c
UINT nx_ppp_chap_enable(NX_PPP *ppp_ptr, 
                        UINT (*get_challenge_values)(CHAR *rand_value,CHAR *id,CHAR *name),
                        UINT (*get_responder_values)(CHAR *system,CHAR *name,CHAR *secret),
                        UINT (*get_verification_values)(CHAR *system,CHAR *name,CHAR *secret)); 
```

### <a name="description"></a><span data-ttu-id="069e8-166">Descrição</span><span class="sxs-lookup"><span data-stu-id="069e8-166">Description</span></span>

<span data-ttu-id="069e8-167">Este serviço permite o Protocolo de Autenticação Challenge-Handshake (CHAP) para a instância de PPP especificada.</span><span class="sxs-lookup"><span data-stu-id="069e8-167">This service enables the Challenge-Handshake Authentication Protocol (CHAP) for the specified PPP instance.</span></span>

<span data-ttu-id="069e8-168">Se os ponteiros de função "\***get_challenge_values**_" e "_ \* _get_verification_values_\*\*" forem especificados, chap é exigido por esta instância de PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-168">If the “\***get_challenge_values**_” and “_\*_get_verification_values_\*\*” function pointers are specified, CHAP is required by this PPP instance.</span></span> <span data-ttu-id="069e8-169">Caso contrário, a CHAP apenas responde aos pedidos de impugnação do colega.</span><span class="sxs-lookup"><span data-stu-id="069e8-169">Otherwise, CHAP only responds to the peer’s challenge requests.</span></span>

<span data-ttu-id="069e8-170">Existem vários itens de dados referenciados abaixo nas funções de retorno necessários.</span><span class="sxs-lookup"><span data-stu-id="069e8-170">There are several data items referenced below in the required callback functions.</span></span> <span data-ttu-id="069e8-171">Espera-se que os dados *sejam fios de* terminação NU, com um tamanho máximo de NX_PPP_NAME_SIZE-1. </span><span class="sxs-lookup"><span data-stu-id="069e8-171">The data items *secret*, *name*, and *system* are expected to be NULL-terminated strings with a maximum size of NX_PPP_NAME_SIZE-1.</span></span> <span data-ttu-id="069e8-172">Espera-se que o *rand_value* de dados seja uma cadeia terminada com um tamanho máximo de NX_PPP_VALUE_SIZE-1.</span><span class="sxs-lookup"><span data-stu-id="069e8-172">The data item *rand_value* is expected to be a NULL-terminated string with a maximum size of NX_PPP_VALUE_SIZE-1.</span></span> <span data-ttu-id="069e8-173">O id de item *de dados* é um tipo simples de caracteres não assinado.</span><span class="sxs-lookup"><span data-stu-id="069e8-173">The data item *id* is a simple unsigned character type.</span></span>

>[!NOTE]
> <span data-ttu-id="069e8-174">Esta função deve ser chamada após *nx_ppp_create* mas antes de nx_ip_create ou *nx_ip_interface_attach*.</span><span class="sxs-lookup"><span data-stu-id="069e8-174">This function must be called after *nx_ppp_create* but before nx_ip_create or *nx_ip_interface_attach*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="069e8-175">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="069e8-175">Input Parameters</span></span>

- <span data-ttu-id="069e8-176">**ppp_ptr**: Ponteiro para o bloco de controlo PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-176">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="069e8-177">**get_challenge_values**: Função de inscrição para recuperar valores utilizados para o desafio.</span><span class="sxs-lookup"><span data-stu-id="069e8-177">**get_challenge_values**: Pointer to application function to retrieve values used for the challenge.</span></span> <span data-ttu-id="069e8-178">Note que os *rand_value*, *id*, e valores *secretos* devem ser copiados para os destinos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="069e8-178">Note that the *rand_value*, *id*, and *secret* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="069e8-179">**get_responder_values**: Ponteiro para a função de aplicação que recupera valores utilizados para responder a um desafio.</span><span class="sxs-lookup"><span data-stu-id="069e8-179">**get_responder_values**: Pointer to application function that retrieves values used to respond to a challenge.</span></span> <span data-ttu-id="069e8-180">Note que o *sistema,* *nome* e valores *secretos* devem ser copiados para os destinos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="069e8-180">Note that the *system*, *name*, and *secret* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="069e8-181">**get_verification_values**: Ponteiro para a função de aplicação que recupera os valores utilizados para verificar a resposta do desafio.</span><span class="sxs-lookup"><span data-stu-id="069e8-181">**get_verification_values**: Pointer to application function that retrieves values used to verify the challenge response.</span></span> <span data-ttu-id="069e8-182">Note que o *sistema,\*\*nome* e valores *secretos* devem ser copiados para os destinos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="069e8-182">Note that the *system*,*name*, and *secret* values must be copied into the supplied destinations.</span></span>

### <a name="return-values"></a><span data-ttu-id="069e8-183">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="069e8-183">Return Values</span></span>

- <span data-ttu-id="069e8-184">**NX_SUCCESS**: (0x00) PPP CHAP bem sucedido</span><span class="sxs-lookup"><span data-stu-id="069e8-184">**NX_SUCCESS**: (0x00) Successful PPP CHAP enable</span></span>
- <span data-ttu-id="069e8-185">**NX_NOT_IMPLEMENTED**: (0x80) a lógica CHAP foi desativada através de NX_PPP_DISABLE_CHAP.</span><span class="sxs-lookup"><span data-stu-id="069e8-185">**NX_NOT_IMPLEMENTED**: (0x80) CHAP logic was disabled via NX_PPP_DISABLE_CHAP.</span></span>
- <span data-ttu-id="069e8-186">NX_PTR_ERROR: (0x07) Ponteiro PPP inválido ou ponteiro da função de retorno.</span><span class="sxs-lookup"><span data-stu-id="069e8-186">NX_PTR_ERROR: (0x07) Invalid PPP pointer or callback function pointer.</span></span> <span data-ttu-id="069e8-187">Note que, se *get_challenge_values* for especificado, a função *get_verification_values* também deve ser fornecida.</span><span class="sxs-lookup"><span data-stu-id="069e8-187">Note that if *get_challenge_values* is specified, then the *get_verification_values* function must also be supplied.</span></span>
- <span data-ttu-id="069e8-188">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="069e8-188">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="069e8-189">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="069e8-189">Allowed From</span></span>

<span data-ttu-id="069e8-190">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="069e8-190">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="069e8-191">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069e8-191">Example</span></span>

```c
CHAR    name_string[] = "username";
CHAR    rand_value_string[] = "123456";
CHAR    system_string[] = "system";
CHAR    secret_string[] = "secret";

/* Enable CHAP in both directions (CHAP challenger and CHAP responder) for 
“my_ppp”. */
status =  nx_ppp_chap_enable(&my_ppp,   get_challenge_values, 
                              get_responder_values,
                              get_verification_values);


/* If status is NX_SUCCESS, “my_ppp” has CHAP enabled. */
/* Define the CHAP enable routines.  */
UINT  get_challenge_values(CHAR *rand_value, CHAR *id, CHAR *name)
{
   UINT    i;
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   *id =  '1';  /* One byte  */
   for (i = 0; i< (NX_PPP_VALUE_SIZE-1); i++)
   {
      rand_value[i] =  rand_value_string[i];
   }
   rand_value[i] =  0;
   
   return(NX_SUCCESS);  
}


UINT  get_responder_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;

   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

UINT  get_verification_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

```
## <a name="nx_ppp_create"></a><span data-ttu-id="069e8-192">nx_ppp_create</span><span class="sxs-lookup"><span data-stu-id="069e8-192">nx_ppp_create</span></span>

<span data-ttu-id="069e8-193">Criar uma instância PPP</span><span class="sxs-lookup"><span data-stu-id="069e8-193">Create a PPP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="069e8-194">Prototype</span><span class="sxs-lookup"><span data-stu-id="069e8-194">Prototype</span></span>

```c
UINT  nx_ppp_create(NX_PPP *ppp_ptr, CHAR *name, NX_IP *ip_ptr, 
                    VOID *stack_memory_ptr, ULONG stack_size, 
                    UINT thread_priority, NX_PACKET_POOL *pool_ptr,
                    void (*ppp_invalid_packet_handler)(NX_PACKET *packet_ptr),
                    void (*ppp_byte_send)(UCHAR byte));
```

### <a name="description"></a><span data-ttu-id="069e8-195">Descrição</span><span class="sxs-lookup"><span data-stu-id="069e8-195">Description</span></span>

<span data-ttu-id="069e8-196">Este serviço cria uma instância PPP para a instância IP netx especificada.</span><span class="sxs-lookup"><span data-stu-id="069e8-196">This service creates a PPP instance for the specified NetX IP instance.</span></span>

>[!NOTE]
> <span data-ttu-id="069e8-197">É geralmente uma boa ideia criar o fio IP NetX com uma prioridade maior do que a prioridade do fio PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-197">It is generally a good idea to create the NetX IP thread at a higher priority than the PPP thread priority.</span></span> <span data-ttu-id="069e8-198">Consulte o serviço *nx_ip_create* para obter mais informações sobre a especificação da prioridade do fio IP.</span><span class="sxs-lookup"><span data-stu-id="069e8-198">Please refer to the *nx_ip_create* service for more information on specifying the IP thread priority.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="069e8-199">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="069e8-199">Input Parameters</span></span>

- <span data-ttu-id="069e8-200">**ppp_ptr**: Ponteiro para o bloco de controlo PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-200">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="069e8-201">**nome**: Nome desta instância PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-201">**name**: Name of this PPP instance.</span></span>
- <span data-ttu-id="069e8-202">**ip_ptr**: Ponteiro para bloquear para instância IP ainda não criada.</span><span class="sxs-lookup"><span data-stu-id="069e8-202">**ip_ptr**: Pointer to control block for not-yet-created IP instance.</span></span>
- <span data-ttu-id="069e8-203">**stack_memory_ptr**: Ponteiro para o início da área de pilha do fio PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-203">**stack_memory_ptr**: Pointer to start of PPP thread’s stack area.</span></span>
- <span data-ttu-id="069e8-204">**stack_size:** Tamanho dos bytes na pilha do fio.</span><span class="sxs-lookup"><span data-stu-id="069e8-204">**stack_size**: Size in bytes in the thread’s stack.</span></span>
- <span data-ttu-id="069e8-205">**pool_ptr**: Ponteiro para a piscina de pacotes predefinidos.</span><span class="sxs-lookup"><span data-stu-id="069e8-205">**pool_ptr**: Pointer to default packet pool.</span></span>
- <span data-ttu-id="069e8-206">**thread_priority**: Prioridade das linhas internas de PPP (1-31).</span><span class="sxs-lookup"><span data-stu-id="069e8-206">**thread_priority**: Priority of internal PPP threads (1-31).</span></span>
- <span data-ttu-id="069e8-207">**ppp_invalid_packet_handler**: Função pointer para o manipulador da aplicação para todos os pacotes não PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-207">**ppp_invalid_packet_handler**: Function pointer to application’s handler for all non-PPP packets.</span></span> <span data-ttu-id="069e8-208">O NetX PPP normalmente chama esta rotina durante a inicialização.</span><span class="sxs-lookup"><span data-stu-id="069e8-208">The NetX PPP typically calls this routine during initialization.</span></span> <span data-ttu-id="069e8-209">É aqui que a aplicação pode responder aos comandos do modem ou no caso do Windows XP, a aplicação PPP NetX pode iniciar pPP respondendo com" CLIENT SERVER" ao "CLIENTE" inicial enviado pelo Windows XP.</span><span class="sxs-lookup"><span data-stu-id="069e8-209">This is where the application can respond to modem commands or in the case of Windows XP, the NetX PPP application can initiate PPP by responding with“ CLIENT SERVER” to the initial “CLIENT” sent by Windows XP.</span></span>
- <span data-ttu-id="069e8-210">**ppp_byte_send**: Funríssem o ponteiro para a rotina de saída de byte de série da aplicação.</span><span class="sxs-lookup"><span data-stu-id="069e8-210">**ppp_byte_send**: Function pointer to application’s serial byte output routine.</span></span>


### <a name="return-values"></a><span data-ttu-id="069e8-211">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="069e8-211">Return Values</span></span>

- <span data-ttu-id="069e8-212">**NX_SUCCESS**: (0x00) PPP bem sucedida cria.</span><span class="sxs-lookup"><span data-stu-id="069e8-212">**NX_SUCCESS**: (0x00) Successful PPP create.</span></span>
- <span data-ttu-id="069e8-213">NX_PTR_ERROR: (0x07) PPP inválido, IP ou byte output function pointer.</span><span class="sxs-lookup"><span data-stu-id="069e8-213">NX_PTR_ERROR: (0x07) Invalid PPP, IP, or byte output function pointer.</span></span>
- <span data-ttu-id="069e8-214">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="069e8-214">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="069e8-215">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="069e8-215">Allowed From</span></span>

<span data-ttu-id="069e8-216">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="069e8-216">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="069e8-217">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069e8-217">Example</span></span>

```c
/* Create “my_ppp” for IP instance “my_ip”. */
status =  nx_ppp_create(&my_ppp, “my PPP”, &my_ip, stack_start, 1024, 2, 
                        &my_pool, my_invalid_packet_handler, my_out_byte);

/* If status is NX_SUCCESS the PPP instance was successfully
   created. */
```

## <a name="nx_ppp_delete"></a><span data-ttu-id="069e8-218">nx_ppp_delete</span><span class="sxs-lookup"><span data-stu-id="069e8-218">nx_ppp_delete</span></span>

<span data-ttu-id="069e8-219">Eliminar uma instância de PPP</span><span class="sxs-lookup"><span data-stu-id="069e8-219">Delete a PPP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="069e8-220">Prototype</span><span class="sxs-lookup"><span data-stu-id="069e8-220">Prototype</span></span>

```c
UINT nx_ppp_delete(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="069e8-221">Descrição</span><span class="sxs-lookup"><span data-stu-id="069e8-221">Description</span></span>

<span data-ttu-id="069e8-222">Este serviço elimina a instância PPP anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="069e8-222">This service deletes the previously created PPP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="069e8-223">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="069e8-223">Input Parameters</span></span>

- <span data-ttu-id="069e8-224">**ppp_ptr**: Ponteiro para o bloco de controlo PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-224">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="069e8-225">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="069e8-225">Return Values</span></span>

- <span data-ttu-id="069e8-226">**NX_SUCCESS**: (0x00) Supressão bem sucedida de PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-226">**NX_SUCCESS**: (0x00) Successful PPP deletion.</span></span>
- <span data-ttu-id="069e8-227">NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.</span><span class="sxs-lookup"><span data-stu-id="069e8-227">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="069e8-228">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="069e8-228">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="069e8-229">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="069e8-229">Allowed From</span></span>

<span data-ttu-id="069e8-230">Fios</span><span class="sxs-lookup"><span data-stu-id="069e8-230">Threads</span></span>

### <a name="example"></a><span data-ttu-id="069e8-231">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069e8-231">Example</span></span>

```c
/* Delete PPP instance “my_ppp”. */
status =  nx_ppp_delete(&my_ppp);

/* If status is NX_SUCCESS the “my_ppp” was successfully deleted. */
```

## <a name="nx_ppp_dns_address_get"></a><span data-ttu-id="069e8-232">nx_ppp_dns_address_get</span><span class="sxs-lookup"><span data-stu-id="069e8-232">nx_ppp_dns_address_get</span></span>

<span data-ttu-id="069e8-233">Obtenha endereço IP DNS</span><span class="sxs-lookup"><span data-stu-id="069e8-233">Get DNS IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="069e8-234">Prototype</span><span class="sxs-lookup"><span data-stu-id="069e8-234">Prototype</span></span>

```c
UINT nx_ppp_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a><span data-ttu-id="069e8-235">Descrição</span><span class="sxs-lookup"><span data-stu-id="069e8-235">Description</span></span>

<span data-ttu-id="069e8-236">Este serviço recupera o endereço DNS IP fornecido pelo par.</span><span class="sxs-lookup"><span data-stu-id="069e8-236">This service retrieves the DNS IP address supplied by the peer.</span></span> <span data-ttu-id="069e8-237">Se nenhum endereço IP foi fornecido pelo par, um endereço IP de 0 é devolvido.</span><span class="sxs-lookup"><span data-stu-id="069e8-237">If no IP address was supplied by the peer, an IP address of 0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="069e8-238">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="069e8-238">Input Parameters</span></span>

- <span data-ttu-id="069e8-239">**ppp_ptr**: Ponteiro para o bloco de controlo PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-239">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="069e8-240">**dns_address_ptr**: Destino para endereço IP DNS</span><span class="sxs-lookup"><span data-stu-id="069e8-240">**dns_address_ptr**: Destination for DNS IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="069e8-241">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="069e8-241">Return Values</span></span>

- <span data-ttu-id="069e8-242">**NX_SUCCESS**: (0x00) Endereço de PPP bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="069e8-242">**NX_SUCCESS**: (0x00) Successful PPP address get.</span></span>
- <span data-ttu-id="069e8-243">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP não concluiu a negociação com os pares.</span><span class="sxs-lookup"><span data-stu-id="069e8-243">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="069e8-244">NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.</span><span class="sxs-lookup"><span data-stu-id="069e8-244">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="069e8-245">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="069e8-245">Allowed From</span></span>

<span data-ttu-id="069e8-246">Inicialização, fios, temporizadores, ISRs</span><span class="sxs-lookup"><span data-stu-id="069e8-246">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="069e8-247">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069e8-247">Example</span></span>

```c

ULONG  my_dns_address;

/* Get IP Server address supplied by peer. */
status =  nx_ppp_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the DNS IP address – 
   if the peer supplied one. */
```

## <a name="nx_ppp_secondary_dns_address_get"></a><span data-ttu-id="069e8-248">nx_ppp_secondary_dns_address_get</span><span class="sxs-lookup"><span data-stu-id="069e8-248">nx_ppp_secondary_dns_address_get</span></span>

<span data-ttu-id="069e8-249">Obtenha o endereço IP do servidor DNS secundário</span><span class="sxs-lookup"><span data-stu-id="069e8-249">Get Secondary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="069e8-250">Prototype</span><span class="sxs-lookup"><span data-stu-id="069e8-250">Prototype</span></span>

```c
UINT nx_ppp_secondary_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a><span data-ttu-id="069e8-251">Descrição</span><span class="sxs-lookup"><span data-stu-id="069e8-251">Description</span></span>

<span data-ttu-id="069e8-252">Este serviço recupera o endereço IP DNS secundário fornecido pelo par no aperto de mão IPCP.</span><span class="sxs-lookup"><span data-stu-id="069e8-252">This service retrieves the secondary DNS IP address supplied by the peer in the IPCP handshake.</span></span> <span data-ttu-id="069e8-253">Se nenhum endereço IP foi fornecido pelo par, um endereço IP de 0 é devolvido.</span><span class="sxs-lookup"><span data-stu-id="069e8-253">If no IP address was supplied by the peer, an IP address of 0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="069e8-254">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="069e8-254">Input Parameters</span></span>

- <span data-ttu-id="069e8-255">**ppp_ptr**: Ponteiro para o bloco de controlo PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-255">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="069e8-256">**dns_address_ptr**: Destino para endereço de servidor DNS secundário</span><span class="sxs-lookup"><span data-stu-id="069e8-256">**dns_address_ptr**: Destination for Secondary DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="069e8-257">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="069e8-257">Return Values</span></span>

- <span data-ttu-id="069e8-258">**NX_SUCCESS**: (0x00) O endereço DNS bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="069e8-258">**NX_SUCCESS**: (0x00) Successful DNS address get.</span></span>
- <span data-ttu-id="069e8-259">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP não concluiu a negociação com os pares.</span><span class="sxs-lookup"><span data-stu-id="069e8-259">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="069e8-260">NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.</span><span class="sxs-lookup"><span data-stu-id="069e8-260">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="069e8-261">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="069e8-261">Allowed From</span></span>

<span data-ttu-id="069e8-262">Inicialização, fios, temporizadores, ISRs</span><span class="sxs-lookup"><span data-stu-id="069e8-262">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="069e8-263">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069e8-263">Example</span></span>

```c
ULONG  my_dns_address;

/* Get secondary DNS Server address supplied by peer. */
status =  nx_ppp_secondary_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the secondary DNS Server address – if the peer supplied one. */
```

## <a name="nx_ppp_dns_address_set"></a><span data-ttu-id="069e8-264">nx_ppp_dns_address_set</span><span class="sxs-lookup"><span data-stu-id="069e8-264">nx_ppp_dns_address_set</span></span>

<span data-ttu-id="069e8-265">Definir o endereço IP do servidor DE DNS primário</span><span class="sxs-lookup"><span data-stu-id="069e8-265">Set primary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="069e8-266">Prototype</span><span class="sxs-lookup"><span data-stu-id="069e8-266">Prototype</span></span>

```c
UINT nx_ppp_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a><span data-ttu-id="069e8-267">Descrição</span><span class="sxs-lookup"><span data-stu-id="069e8-267">Description</span></span>

<span data-ttu-id="069e8-268">Este serviço define o endereço IP do Servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="069e8-268">This service sets the DNS Server IP address.</span></span> <span data-ttu-id="069e8-269">Se o par enviar um pedido de opção DNS Server no estado IPCP, este anfitrião fornecerá a informação.</span><span class="sxs-lookup"><span data-stu-id="069e8-269">If the peer sends a DNS Server option request in the IPCP state, this host will provide the information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="069e8-270">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="069e8-270">Input Parameters</span></span>

- <span data-ttu-id="069e8-271">**ppp_ptr**: Ponteiro para o bloco de controlo PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-271">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="069e8-272">**dns_address**: Endereço do servidor DNS</span><span class="sxs-lookup"><span data-stu-id="069e8-272">**dns_address**: DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="069e8-273">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="069e8-273">Return Values</span></span>

- <span data-ttu-id="069e8-274">**NX_SUCCESS**: (0x00) Conjunto de endereços DNS bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="069e8-274">**NX_SUCCESS**: (0x00) Successful DNS address set.</span></span>
- <span data-ttu-id="069e8-275">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP não concluiu a negociação com os pares.</span><span class="sxs-lookup"><span data-stu-id="069e8-275">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="069e8-276">NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.</span><span class="sxs-lookup"><span data-stu-id="069e8-276">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="069e8-277">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="069e8-277">Allowed From</span></span>

<span data-ttu-id="069e8-278">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="069e8-278">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="069e8-279">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069e8-279">Example</span></span>

```c

ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the DNS Server address provided if the peer requests one. */

```

## <a name="nx_ppp_secondary_dns_address_set"></a><span data-ttu-id="069e8-280">nx_ppp_secondary_dns_address_set</span><span class="sxs-lookup"><span data-stu-id="069e8-280">nx_ppp_secondary_dns_address_set</span></span>

<span data-ttu-id="069e8-281">Definir endereço IP do servidor DNS secundário</span><span class="sxs-lookup"><span data-stu-id="069e8-281">Set secondary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="069e8-282">Prototype</span><span class="sxs-lookup"><span data-stu-id="069e8-282">Prototype</span></span>

```c
UINT nx_ppp_secondary_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a><span data-ttu-id="069e8-283">Descrição</span><span class="sxs-lookup"><span data-stu-id="069e8-283">Description</span></span>

<span data-ttu-id="069e8-284">Este serviço define o endereço IP do servidor DNS secundário.</span><span class="sxs-lookup"><span data-stu-id="069e8-284">This service sets the secondary DNS Server IP address.</span></span> <span data-ttu-id="069e8-285">Se o par enviar um pedido de opção dNS Server secundário no estado IPCP, este anfitrião fornecerá as informações.</span><span class="sxs-lookup"><span data-stu-id="069e8-285">If the peer sends a secondary DNS Server option request in the IPCP state, this host will provide the information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="069e8-286">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="069e8-286">Input Parameters</span></span>

- <span data-ttu-id="069e8-287">**ppp_ptr**: Ponteiro para o bloco de controlo PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-287">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="069e8-288">**dns_address**: Endereço secundário do servidor DNS</span><span class="sxs-lookup"><span data-stu-id="069e8-288">**dns_address**: Secondary DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="069e8-289">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="069e8-289">Return Values</span></span>

- <span data-ttu-id="069e8-290">**NX_SUCCESS**: (0x00) Conjunto de endereços DNS bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="069e8-290">**NX_SUCCESS**: (0x00) Successful DNS address set.</span></span> 
- <span data-ttu-id="069e8-291">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP não concluiu a negociação com os pares.</span><span class="sxs-lookup"><span data-stu-id="069e8-291">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="069e8-292">NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.</span><span class="sxs-lookup"><span data-stu-id="069e8-292">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="069e8-293">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="069e8-293">Allowed From</span></span>

<span data-ttu-id="069e8-294">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="069e8-294">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="069e8-295">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069e8-295">Example</span></span>

```c
ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_secondary_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the secondary DNS Server address provided if the peer requests one. */

```
## <a name="nx_ppp_interface_index_get"></a><span data-ttu-id="069e8-296">nx_ppp_interface_index_get</span><span class="sxs-lookup"><span data-stu-id="069e8-296">nx_ppp_interface_index_get</span></span>

<span data-ttu-id="069e8-297">Obtenha índice de interface IP</span><span class="sxs-lookup"><span data-stu-id="069e8-297">Get IP interface index</span></span>

### <a name="prototype"></a><span data-ttu-id="069e8-298">Prototype</span><span class="sxs-lookup"><span data-stu-id="069e8-298">Prototype</span></span>

```c
UINT nx_ppp_interface_index_get(NX_PPP *ppp_ptr, UINT *index_ptr);
```

### <a name="description"></a><span data-ttu-id="069e8-299">Descrição</span><span class="sxs-lookup"><span data-stu-id="069e8-299">Description</span></span>

<span data-ttu-id="069e8-300">Este serviço recupera o índice de interface IP associado a esta instância de PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-300">This service retrieves the IP interface index associated with this PPP instance.</span></span> <span data-ttu-id="069e8-301">Isto só é útil quando a instância PPP não é a interface primária de uma instância IP.</span><span class="sxs-lookup"><span data-stu-id="069e8-301">This is only useful when the PPP instance is not the primary interface of an IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="069e8-302">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="069e8-302">Input Parameters</span></span>

- <span data-ttu-id="069e8-303">**ppp_ptr**: Ponteiro para o bloco de controlo PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-303">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="069e8-304">**index_ptr**: Destino para índice de interface</span><span class="sxs-lookup"><span data-stu-id="069e8-304">**index_ptr**: Destination for interface index</span></span>

### <a name="return-values"></a><span data-ttu-id="069e8-305">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="069e8-305">Return Values</span></span>

- <span data-ttu-id="069e8-306">**NX_SUCCESS**: (0x00) Índice de PPP bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="069e8-306">**NX_SUCCESS**: (0x00) Successful PPP index get.</span></span>
- <span data-ttu-id="069e8-307">**NX_IN_PROGRESS**: (0x37) PPP não concluiu a inicialização.</span><span class="sxs-lookup"><span data-stu-id="069e8-307">**NX_IN_PROGRESS**: (0x37) PPP has not completed initialization.</span></span>
- <span data-ttu-id="069e8-308">NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.</span><span class="sxs-lookup"><span data-stu-id="069e8-308">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="069e8-309">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="069e8-309">Allowed From</span></span>

<span data-ttu-id="069e8-310">Inicialização, fios, temporizadores, ISRs</span><span class="sxs-lookup"><span data-stu-id="069e8-310">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="069e8-311">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069e8-311">Example</span></span>

```c
ULONG  my_index;

/* Get the interface index for this PPP instance. */
status =  nx_ppp_interface_index_get(&my_ppp, &my_index);

/* If status is NX_SUCCESS the “my_index” contains the IP interface index for
   this PPP instance. */

```
## <a name="nx_ppp_ip_address_assign"></a><span data-ttu-id="069e8-312">nx_ppp_ip_address_assign</span><span class="sxs-lookup"><span data-stu-id="069e8-312">nx_ppp_ip_address_assign</span></span>

<span data-ttu-id="069e8-313">Atribuir endereços IP para IPCP</span><span class="sxs-lookup"><span data-stu-id="069e8-313">Assign IP addresses for IPCP</span></span>

### <a name="prototype"></a><span data-ttu-id="069e8-314">Prototype</span><span class="sxs-lookup"><span data-stu-id="069e8-314">Prototype</span></span>

```c
UINT nx_ppp_ip_address_assign(NX_PPP *ppp_ptr, ULONG local_ip_address, 
            ULONG peer_ip_address);
```

### <a name="description"></a><span data-ttu-id="069e8-315">Descrição</span><span class="sxs-lookup"><span data-stu-id="069e8-315">Description</span></span>

<span data-ttu-id="069e8-316">Este serviço configura os endereços IP locais e pares para utilização no Protocolo de Controlo do Protocolo de Internet (IPCP).</span><span class="sxs-lookup"><span data-stu-id="069e8-316">This service sets up the local and peer IP addresses for use in the Internet Protocol Control Protocol (IPCP).</span></span> <span data-ttu-id="069e8-317">O pedido de PPP deve invocar este serviço numa instância PPP com endereços IP válidos para si e para o outro par.</span><span class="sxs-lookup"><span data-stu-id="069e8-317">The PPP application should invoke this service on a PPP instance with valid IP addresses for itself and the other peer.</span></span>  <span data-ttu-id="069e8-318">Se não forem registados endereços válidos com uma instância PPP, deve contar com o par de PPP para definir o seu endereço IP.</span><span class="sxs-lookup"><span data-stu-id="069e8-318">If no valid addresses are registered with a PPP instance, it must rely on the PPP peer to define its IP address.</span></span>


### <a name="input-parameters"></a><span data-ttu-id="069e8-319">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="069e8-319">Input Parameters</span></span>

- <span data-ttu-id="069e8-320">**ppp_ptr**: Ponteiro para o bloco de controlo PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-320">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="069e8-321">**local_ip_address**: Endereço IP local.</span><span class="sxs-lookup"><span data-stu-id="069e8-321">**local_ip_address**: Local IP address.</span></span>
- <span data-ttu-id="069e8-322">**peer_ip_address:** Endereço IP do peer.</span><span class="sxs-lookup"><span data-stu-id="069e8-322">**peer_ip_address**: Peer’s IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="069e8-323">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="069e8-323">Return Values</span></span>

- <span data-ttu-id="069e8-324">**NX_SUCCESS:**(0x00) Atribuição de endereços de PPP bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="069e8-324">**NX_SUCCESS**: (0x00) Successful PPP address assignment.</span></span>
- <span data-ttu-id="069e8-325">NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.</span><span class="sxs-lookup"><span data-stu-id="069e8-325">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="069e8-326">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="069e8-326">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="069e8-327">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="069e8-327">Allowed From</span></span>

<span data-ttu-id="069e8-328">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="069e8-328">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="069e8-329">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069e8-329">Example</span></span>

```c
/* Set IP addresses for “my_ppp”. */
status =  nx_ppp_ip_address_assign(&my_ppp, IP_ADDRESS(256,2,2,187), 
IP_ADDRESS(256,2,2,188));


/* If status is NX_SUCCESS the “my_ppp” has the IP addresses. */
```

## <a name="nx_ppp_link_down_notify"></a><span data-ttu-id="069e8-330">nx_ppp_link_down_notify</span><span class="sxs-lookup"><span data-stu-id="069e8-330">nx_ppp_link_down_notify</span></span>

<span data-ttu-id="069e8-331">Notifique o pedido no link para baixo</span><span class="sxs-lookup"><span data-stu-id="069e8-331">Notify application on link down</span></span>

### <a name="prototype"></a><span data-ttu-id="069e8-332">Prototype</span><span class="sxs-lookup"><span data-stu-id="069e8-332">Prototype</span></span>

```c
UINT nx_ppp_link_down_notify(NX_PPP *ppp_ptr, 
                             VOID (*link_down_callback)(NX_PPP *ppp_ptr));
```

### <a name="description"></a><span data-ttu-id="069e8-333">Descrição</span><span class="sxs-lookup"><span data-stu-id="069e8-333">Description</span></span>

<span data-ttu-id="069e8-334">Este serviço regista a chamada de notificação de ligação da aplicação com a instância de PPP especificada.</span><span class="sxs-lookup"><span data-stu-id="069e8-334">This service registers the application’s link down notification callback with the specified PPP instance.</span></span> <span data-ttu-id="069e8-335">Se não for NULO, a função de retorno de ligação da aplicação é chamada sempre que o link se apaga.</span><span class="sxs-lookup"><span data-stu-id="069e8-335">If non-NULL, the application’s link down callback function is called whenever the link goes down.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="069e8-336">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="069e8-336">Input Parameters</span></span>

- <span data-ttu-id="069e8-337">**ppp_ptr**: Ponteiro para o bloco de controlo PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-337">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="069e8-338">**link_down_callback**: Link da aplicação para baixo ponteiro da função de notificação.</span><span class="sxs-lookup"><span data-stu-id="069e8-338">**link_down_callback**: Application’s link down notification function pointer.</span></span> <span data-ttu-id="069e8-339">Se a NOTificação DE NULA, a notificação de ligação para baixo está desativada.</span><span class="sxs-lookup"><span data-stu-id="069e8-339">If NULL, link down notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="069e8-340">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="069e8-340">Return Values</span></span>

- <span data-ttu-id="069e8-341">**NX_SUCCESS**: (0x00) Link de retorno de notificação com sucesso.</span><span class="sxs-lookup"><span data-stu-id="069e8-341">**NX_SUCCESS**: (0x00) Successful link down notification callback registration.</span></span>
- <span data-ttu-id="069e8-342">NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.</span><span class="sxs-lookup"><span data-stu-id="069e8-342">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="069e8-343">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="069e8-343">Allowed From</span></span>

<span data-ttu-id="069e8-344">Inicialização, fios, temporizadores, ISRs</span><span class="sxs-lookup"><span data-stu-id="069e8-344">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="069e8-345">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069e8-345">Example</span></span>

```c
/* Register “my_link_down_callback” to be called whenever the PPP
   link goes down. */
status =  nx_ppp_link_down_notify(&my_ppp, my_link_down_callback);


/* If status is NX_SUCCESS the function “my_link_down_callback” has been
   registered with this PPP instance. */

VOID my_link_down_callback(NX_PPP *ppp_ptr)
{

/* On link down, simply restart PPP.  */
    nx_ppp_restart(ppp_ptr);
} 
```
## <a name="nx_ppp_link_up_notify"></a><span data-ttu-id="069e8-346">nx_ppp_link_up_notify</span><span class="sxs-lookup"><span data-stu-id="069e8-346">nx_ppp_link_up_notify</span></span>

<span data-ttu-id="069e8-347">Notificar o pedido no link</span><span class="sxs-lookup"><span data-stu-id="069e8-347">Notify application on link up</span></span>

### <a name="prototype"></a><span data-ttu-id="069e8-348">Prototype</span><span class="sxs-lookup"><span data-stu-id="069e8-348">Prototype</span></span>

```c
UINT nx_ppp_link_up_notify(NX_PPP *ppp_ptr, 
                           VOID (*link_up_callback)(NX_PPP *ppp_ptr));
```
### <a name="description"></a><span data-ttu-id="069e8-349">Descrição</span><span class="sxs-lookup"><span data-stu-id="069e8-349">Description</span></span>

<span data-ttu-id="069e8-350">Este serviço regista a chamada de notificação de ligação da aplicação com a instância de PPP especificada.</span><span class="sxs-lookup"><span data-stu-id="069e8-350">This service registers the application’s link up notification callback with the specified PPP instance.</span></span> <span data-ttu-id="069e8-351">Se não for NULO, a função de chamada de ligação da aplicação é chamada sempre que o link aparece.</span><span class="sxs-lookup"><span data-stu-id="069e8-351">If non-NULL, the application’s link up callback function is called whenever the link comes up.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="069e8-352">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="069e8-352">Input Parameters</span></span>

- <span data-ttu-id="069e8-353">**ppp_ptr**: Ponteiro para o bloco de controlo PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-353">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="069e8-354">**link_up_callback**: Link-up de serviço de notificação da aplicação.</span><span class="sxs-lookup"><span data-stu-id="069e8-354">**link_up_callback**: Application’s link up notification function pointer.</span></span> <span data-ttu-id="069e8-355">Se o NU, a notificação de ligação é desativada.\*\*</span><span class="sxs-lookup"><span data-stu-id="069e8-355">If NULL, link up notification is disabled.\*\*</span></span>

### <a name="return-values"></a><span data-ttu-id="069e8-356">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="069e8-356">Return Values</span></span>

- <span data-ttu-id="069e8-357">**NX_SUCCESS**: (0x00) Link com sucesso link up registration de chamada de notificação.</span><span class="sxs-lookup"><span data-stu-id="069e8-357">**NX_SUCCESS**: (0x00) Successful link up notification callback registration.</span></span>
- <span data-ttu-id="069e8-358">NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.</span><span class="sxs-lookup"><span data-stu-id="069e8-358">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="069e8-359">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="069e8-359">Allowed From</span></span>

<span data-ttu-id="069e8-360">Inicialização, fios, temporizadores, ISRs</span><span class="sxs-lookup"><span data-stu-id="069e8-360">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="069e8-361">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069e8-361">Example</span></span>

```c
/* Register “my_link_up_callback” to be called whenever the PPP
   link comes up. */
status =  nx_ppp_link_up_notify(&my_ppp, my_link_up_callback);


/* If status is NX_SUCCESS the function “my_link_up_callback” has been
   registered with this PPP instance. */

VOID my_link_up_callback(NX_PPP *ppp_ptr)
{
    /* On link up, the application my want to start sending/receiving
       UPD/TCP data.  */
}
```

## <a name="nx_ppp_nak_authentication_notify"></a><span data-ttu-id="069e8-362">nx_ppp_nak_authentication_notify</span><span class="sxs-lookup"><span data-stu-id="069e8-362">nx_ppp_nak_authentication_notify</span></span>

<span data-ttu-id="069e8-363">Notificar o pedido se a autenticação NAK recebida</span><span class="sxs-lookup"><span data-stu-id="069e8-363">Notify application if authentication NAK received</span></span>

### <a name="prototype"></a><span data-ttu-id="069e8-364">Prototype</span><span class="sxs-lookup"><span data-stu-id="069e8-364">Prototype</span></span>

```c
UINT    nx_ppp_nak_authentication_notify(NX_PPP *ppp_ptr, 
                                         void (*nak_authentication_notify)(void));
```

### <a name="description"></a><span data-ttu-id="069e8-365">Descrição</span><span class="sxs-lookup"><span data-stu-id="069e8-365">Description</span></span>

<span data-ttu-id="069e8-366">Este serviço regista a chamada de notificação de autenticação da aplicação com a instância de PPP especificada.</span><span class="sxs-lookup"><span data-stu-id="069e8-366">This service registers the application’s authentication nak notification callback with the specified PPP instance.</span></span> <span data-ttu-id="069e8-367">Se não for NULO, esta função de retorno é chamada sempre que a instância PPP recebe um NAK durante a authentiaction.</span><span class="sxs-lookup"><span data-stu-id="069e8-367">If non-NULL, this callback function is called whenever the PPP instance receives a NAK during authentiaction.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="069e8-368">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="069e8-368">Input Parameters</span></span>

- <span data-ttu-id="069e8-369">**ppp_ptr**: Ponteiro para o bloco de controlo PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-369">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="069e8-370">**nak_authentication_notify**: Ponteiro para funcionar chamado quando a instância PPP recebe um NAK de autenticação.</span><span class="sxs-lookup"><span data-stu-id="069e8-370">**nak_authentication_notify**: Pointer to function called when the PPP instance receives an authentication NAK.</span></span> <span data-ttu-id="069e8-371">Se NULL, a notificação é desativada.</span><span class="sxs-lookup"><span data-stu-id="069e8-371">If NULL, the notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="069e8-372">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="069e8-372">Return Values</span></span>

- <span data-ttu-id="069e8-373">**NX_SUCCESS:**(0x00) Registo de chamada de notificação bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="069e8-373">**NX_SUCCESS**: (0x00) Successful notification callback registration.</span></span>
- <span data-ttu-id="069e8-374">NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.</span><span class="sxs-lookup"><span data-stu-id="069e8-374">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="069e8-375">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="069e8-375">Allowed From</span></span>

<span data-ttu-id="069e8-376">Inicialização, fios, temporizadores, ISRs</span><span class="sxs-lookup"><span data-stu-id="069e8-376">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="069e8-377">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069e8-377">Example</span></span>

```c
/* Register “my_nak_auth_callback” to be called whenever the PPP
   receives a NAK during authentication. */
status =  nx_ppp_nak_authentication_notify(&my_ppp, my_nak_auth_callback);

/* If status is NX_SUCCESS the function “my_nak_auth_callback” has been
   registered with this PPP instance. */

VOID my_nak_auth_callback(NX_PPP *ppp_ptr)
{
   /* Handle the situation of receiving an authentication NAK */
}

```

## <a name="nx_ppp_pap_enable"></a><span data-ttu-id="069e8-378">nx_ppp_pap_enable</span><span class="sxs-lookup"><span data-stu-id="069e8-378">nx_ppp_pap_enable</span></span>

<span data-ttu-id="069e8-379">Ativar a autenticação do PAP</span><span class="sxs-lookup"><span data-stu-id="069e8-379">Enable PAP Authentication</span></span>

### <a name="prototype"></a><span data-ttu-id="069e8-380">Prototype</span><span class="sxs-lookup"><span data-stu-id="069e8-380">Prototype</span></span>

```c

UINT  nx_ppp_pap_enable(NX_PPP *ppp_ptr, 
                        UINT (*generate_login)(CHAR *name, CHAR *password),
                        UINT (*verify_login)(CHAR *name, CHAR *password));
```

### <a name="description"></a><span data-ttu-id="069e8-381">Descrição</span><span class="sxs-lookup"><span data-stu-id="069e8-381">Description</span></span>

<span data-ttu-id="069e8-382">Este serviço permite o Protocolo de Autenticação de Palavras-Passe (PAP) para a instância de PPP especificada.</span><span class="sxs-lookup"><span data-stu-id="069e8-382">This service enables the Password Authentication Protocol (PAP) for the specified PPP instance.</span></span> <span data-ttu-id="069e8-383">Se o ponteiro de função "***verify_login***" for especificado, o PAP é exigido por esta instância de PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-383">If the “***verify_login***” function pointer is specified, PAP is required by this PPP instance.</span></span> <span data-ttu-id="069e8-384">Caso contrário, o PAP apenas responde aos requisitos de PAP do par, tal como especificado durante a negociação do LCP.</span><span class="sxs-lookup"><span data-stu-id="069e8-384">Otherwise, PAP only responds to the peer’s PAP requirements as specified during LCP negotiation.</span></span>

<span data-ttu-id="069e8-385">Existem vários itens de dados referenciados abaixo nas funções de retorno necessários.</span><span class="sxs-lookup"><span data-stu-id="069e8-385">There are several data items referenced below in the required callback functions.</span></span> <span data-ttu-id="069e8-386">Espera-se que o *nome* do item de dados seja uma cadeia terminada com um tamanho máximo de NX_PPP_NAME_SIZE-1.</span><span class="sxs-lookup"><span data-stu-id="069e8-386">The data item *name* is expected to be NULL-terminated string with a maximum size of NX_PPP_NAME_SIZE-1.</span></span> <span data-ttu-id="069e8-387">Espera-se também que a *palavra-passe* do item de dados seja uma cadeia terminada com um tamanho máximo de NX_PPP_PASSWORD_SIZE-1.</span><span class="sxs-lookup"><span data-stu-id="069e8-387">The data item *password* is also expected to be a NULL-terminated string with a maximum size of NX_PPP_PASSWORD_SIZE-1.</span></span>

>[!NOTE]
> <span data-ttu-id="069e8-388">Esta função deve ser chamada após *nx_ppp_create* mas antes *de nx_ip_create* ou *nx_ip_interface_attach*.</span><span class="sxs-lookup"><span data-stu-id="069e8-388">This function must be called after *nx_ppp_create* but before *nx_ip_create* or *nx_ip_interface_attach*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="069e8-389">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="069e8-389">Input Parameters</span></span>

- <span data-ttu-id="069e8-390">**ppp_ptr**: Ponteiro para o bloco de controlo PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-390">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="069e8-391">**generate_login**: Ponteiro para a função de aplicação que produz um *nome* e *senha* para autenticação pelo par.</span><span class="sxs-lookup"><span data-stu-id="069e8-391">**generate_login**: Pointer to application function that produces a *name* and *password* for authentication by the peer.</span></span> <span data-ttu-id="069e8-392">Note que os valores do *nome* e *da palavra-passe* devem ser copiados para os destinos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="069e8-392">Note that the *name* and *password* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="069e8-393">**verify_login**: Ponteiro para a função de aplicação que verifica o *nome* e *a palavra-passe* fornecida pelo par.</span><span class="sxs-lookup"><span data-stu-id="069e8-393">**verify_login**: Pointer to application function that verifies the *name* and *password* supplied by the peer.</span></span> <span data-ttu-id="069e8-394">Esta rotina deve comparar o *nome* e *a palavra-passe* fornecidos.</span><span class="sxs-lookup"><span data-stu-id="069e8-394">This routine must compare the supplied *name* and *password*.</span></span> <span data-ttu-id="069e8-395">Se esta rotina voltar NX_SUCCESS, o nome e a palavra-passe estão corretos e as PPP podem avançar para o passo seguinte.</span><span class="sxs-lookup"><span data-stu-id="069e8-395">If this routine returns NX_SUCCESS, the name and password are correct and PPP can proceed to the next step.</span></span> <span data-ttu-id="069e8-396">Caso contrário, esta rotina retorna NX_PPP_ERROR e PPP simplesmente espera por outro nome e senha.</span><span class="sxs-lookup"><span data-stu-id="069e8-396">Otherwise, this routine returns NX_PPP_ERROR and PPP simply waits for another name and password.</span></span>

### <a name="return-values"></a><span data-ttu-id="069e8-397">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="069e8-397">Return Values</span></span>

- <span data-ttu-id="069e8-398">**NX_SUCCESS**: (0x00) PPP PAP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="069e8-398">**NX_SUCCESS**: (0x00) Successful PPP PAP enable.</span></span>
- <span data-ttu-id="069e8-399">**NX_NOT_IMPLEMENTED**: (0x80) a lógica do PAP foi desativada através de NX_PPP_DISABLE_PAP.</span><span class="sxs-lookup"><span data-stu-id="069e8-399">**NX_NOT_IMPLEMENTED**: (0x80) PAP logic was disabled via NX_PPP_DISABLE_PAP.</span></span>
- <span data-ttu-id="069e8-400">NX_PTR_ERROR: (0x07) Ponteiro pPP inválido ou ponteiro da função de aplicação.</span><span class="sxs-lookup"><span data-stu-id="069e8-400">NX_PTR_ERROR: (0x07) Invalid PPP pointer or application function pointer.</span></span>
- <span data-ttu-id="069e8-401">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="069e8-401">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="069e8-402">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="069e8-402">Allowed From</span></span>

<span data-ttu-id="069e8-403">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="069e8-403">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="069e8-404">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069e8-404">Example</span></span>

```c
CHAR    name_string[] = "username";
CHAR    password_string[] =  "password";

/* Enable PAP for PPP instance “my_ppp”. */
status =  nx_ppp_pap_enable(&my_ppp, my_generate_login, my_verify_login);

/* If status is NX_SUCCESS the “my_ppp” now has PAP enabled. */

/* Define callback routines for PAP enable.  */

UINT  generate_login(CHAR *name, CHAR *password)
{

UINT    i;

for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
name[i] = name_string[i];
name[i] =  0;

for (i = 0; i< (NX_PPP_PASSWORD_SIZE-1); i++)
password[i] = password_string[i];
password_string[i] =  0;

return(NX_SUCCESS);  
}

UINT  verify_login(CHAR *name, CHAR *password)
{

/* Assume name and password are correct. Normally, 
a comparison would be made here!  */
printf("Name: %s, Password: %s\n", name, password);

return(NX_SUCCESS);  
}
```

## <a name="nx_ppp_ping_request"></a><span data-ttu-id="069e8-405">nx_ppp_ping_request</span><span class="sxs-lookup"><span data-stu-id="069e8-405">nx_ppp_ping_request</span></span>

<span data-ttu-id="069e8-406">Envie um pedido de ping LCP</span><span class="sxs-lookup"><span data-stu-id="069e8-406">Send an LCP ping request</span></span>

### <a name="prototype"></a><span data-ttu-id="069e8-407">Prototype</span><span class="sxs-lookup"><span data-stu-id="069e8-407">Prototype</span></span>

```c
UINT  nx_ppp_ping_request(NX_PPP *ppp_ptr, CHAR *data, 
                          UINT data_size, ULONG wait_opion);
```

### <a name="description"></a><span data-ttu-id="069e8-408">Descrição</span><span class="sxs-lookup"><span data-stu-id="069e8-408">Description</span></span>

<span data-ttu-id="069e8-409">Este serviço envia um pedido de ping LCP e estabelece uma bandeira que o dispositivo PPP está à espera de uma resposta de eco.</span><span class="sxs-lookup"><span data-stu-id="069e8-409">This service sends an LCP ping request and sets a flag that the PPP device is waiting for an echo response.</span></span> <span data-ttu-id="069e8-410">O serviço regressa assim que o pedido for enviado.</span><span class="sxs-lookup"><span data-stu-id="069e8-410">The service returns as soon as the request is sent.</span></span> <span data-ttu-id="069e8-411">Não espera uma resposta.</span><span class="sxs-lookup"><span data-stu-id="069e8-411">It does not wait for a response.</span></span> 

<span data-ttu-id="069e8-412">Quando uma resposta de eco correspondente é recebida, a tarefa de linha PPP limpará a bandeira.</span><span class="sxs-lookup"><span data-stu-id="069e8-412">When a matching echo response is received, the PPP thread task will clear the flag.</span></span> <span data-ttu-id="069e8-413">O dispositivo PPP deve ter concluído a parte LCP da negociação das PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-413">The PPP device must have completed the LCP part of the PPP negotiation.</span></span>

<span data-ttu-id="069e8-414">Este serviço é útil para configurações de PPP onde a votação do hardware para o estado de ligação pode não ser facilmente possível.</span><span class="sxs-lookup"><span data-stu-id="069e8-414">This service is useful for PPP set ups where polling the hardware for link status may not be readily possible.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="069e8-415">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="069e8-415">Input Parameters</span></span>

- <span data-ttu-id="069e8-416">**ppp_ptr**: Ponteiro para o bloco de controlo PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-416">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="069e8-417">**dados**: Ponteiro para os dados para enviar o pedido de eco.</span><span class="sxs-lookup"><span data-stu-id="069e8-417">**data**: Pointer to data to send in echo request.</span></span>
- <span data-ttu-id="069e8-418">**data_size**: Tamanho dos dados para enviar wait_option Hora para esperar para enviar a mensagem de eco LCP.</span><span class="sxs-lookup"><span data-stu-id="069e8-418">**data_size**: Size of data to send wait_option Time to wait to send the LCP echo message.</span></span>

### <a name="return-values"></a><span data-ttu-id="069e8-419">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="069e8-419">Return Values</span></span>

- <span data-ttu-id="069e8-420">**NX_SUCCESS:**(0x00) Pedido de eco enviado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="069e8-420">**NX_SUCCESS**: (0x00) Successful sent echo request.</span></span>
- <span data-ttu-id="069e8-421">**NX_PPP_NOT_ESTABLISHED:**(0xB5) ligação pPP não estabelecida.</span><span class="sxs-lookup"><span data-stu-id="069e8-421">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP connection not established.</span></span>
- <span data-ttu-id="069e8-422">NX_PTR_ERROR: (0x07) Ponteiro pPP inválido ou ponteiro da função de aplicação.</span><span class="sxs-lookup"><span data-stu-id="069e8-422">NX_PTR_ERROR: (0x07) Invalid PPP pointer or application function pointer.</span></span>
- <span data-ttu-id="069e8-423">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="069e8-423">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="069e8-424">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="069e8-424">Allowed From</span></span>

<span data-ttu-id="069e8-425">Fios de aplicação</span><span class="sxs-lookup"><span data-stu-id="069e8-425">Application threads</span></span>

### <a name="example"></a><span data-ttu-id="069e8-426">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069e8-426">Example</span></span>

```c

CHAR    buffer[] = "username";
UINT    buffer_length =  strlen("username ");

/* Send an LCP ping request”. */
status =  nx_ppp_ping_request(&my_ppp, &buffer[0], buffer_length, 200);

/* If status is NX_SUCCESS the LCP echo request was successfully sent. Now wait to 
   receive a response. */

while(my_ppp.nx_ppp_lcp_echo_reply_id > 0)
{
    tx_thread_sleep(100);
}

/* Got a valid reply! */
```

## <a name="nx_ppp_raw_string_send"></a><span data-ttu-id="069e8-427">nx_ppp_raw_string_send</span><span class="sxs-lookup"><span data-stu-id="069e8-427">nx_ppp_raw_string_send</span></span>

<span data-ttu-id="069e8-428">Envie uma cadeia ASCII crua</span><span class="sxs-lookup"><span data-stu-id="069e8-428">Send a raw ASCII string</span></span>

### <a name="prototype"></a><span data-ttu-id="069e8-429">Prototype</span><span class="sxs-lookup"><span data-stu-id="069e8-429">Prototype</span></span>

```c
UINT  nx_ppp_raw_sting_send(NX_PPP *ppp_ptr, CHAR *string_ptr);
```

### <a name="description"></a><span data-ttu-id="069e8-430">Descrição</span><span class="sxs-lookup"><span data-stu-id="069e8-430">Description</span></span>

<span data-ttu-id="069e8-431">Este serviço envia uma cadeia ASCII não PPP diretamente para fora da interface PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-431">This service sends a non-PPP ASCII string directly out the PPP interface.</span></span> <span data-ttu-id="069e8-432">É normalmente utilizado após pPP receber um pacote não PPP que contém informações de controlo do modem.</span><span class="sxs-lookup"><span data-stu-id="069e8-432">It is typically used after PPP receives a non-PPP packet that contains modem control information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="069e8-433">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="069e8-433">Input Parameters</span></span>

- <span data-ttu-id="069e8-434">**ppp_ptr**: Ponteiro para o bloco de controlo PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-434">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="069e8-435">**string_ptr**: Ponteiro para a corda para enviar.</span><span class="sxs-lookup"><span data-stu-id="069e8-435">**string_ptr**: Pointer to string to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="069e8-436">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="069e8-436">Return Values</span></span>

- <span data-ttu-id="069e8-437">**NX_SUCCESS**: (0x00) Envio de GPP com sucesso.</span><span class="sxs-lookup"><span data-stu-id="069e8-437">**NX_SUCCESS**: (0x00) Successful PPP raw string send.</span></span>
- <span data-ttu-id="069e8-438">NX_PTR_ERROR: (0x07) Ponteiro PPP inválido ou ponteiro de cordas.</span><span class="sxs-lookup"><span data-stu-id="069e8-438">NX_PTR_ERROR: (0x07) Invalid PPP pointer or string pointer.</span></span>
- <span data-ttu-id="069e8-439">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="069e8-439">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="069e8-440">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="069e8-440">Allowed From</span></span>

<span data-ttu-id="069e8-441">Fios</span><span class="sxs-lookup"><span data-stu-id="069e8-441">Threads</span></span>

### <a name="example"></a><span data-ttu-id="069e8-442">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069e8-442">Example</span></span>

```c

/* Send “CLIENTSERVER” to “CLIENT” sent by Windows 98 before PPP is
initiated.  */
status =  nx_ppp_raw_string_send(&my_ppp, “CLIENTSERVER”);

/* If status is NX_SUCCESS the raw string was successfully Sent via PPP. */
```
## <a name="nx_ppp_restart"></a><span data-ttu-id="069e8-443">nx_ppp_restart</span><span class="sxs-lookup"><span data-stu-id="069e8-443">nx_ppp_restart</span></span>

<span data-ttu-id="069e8-444">Reiniciar o processamento de PPP</span><span class="sxs-lookup"><span data-stu-id="069e8-444">Restart PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="069e8-445">Prototype</span><span class="sxs-lookup"><span data-stu-id="069e8-445">Prototype</span></span>

```c
UINT  nx_ppp_restart(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="069e8-446">Descrição</span><span class="sxs-lookup"><span data-stu-id="069e8-446">Description</span></span>

<span data-ttu-id="069e8-447">Este serviço reinicia o processamento de PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-447">This service restarts the PPP processing.</span></span> <span data-ttu-id="069e8-448">É normalmente chamado quando o link precisa ser restabelecido a partir de uma chamada de ligação para baixo ou por uma mensagem de modem não PPP indicando que a comunicação foi perdida.</span><span class="sxs-lookup"><span data-stu-id="069e8-448">It is typically called when the link needs to be re-established either from a link down callback or by a non-PPP modem message indicating communication was lost.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="069e8-449">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="069e8-449">Input Parameters</span></span>

- <span data-ttu-id="069e8-450">**ppp_ptr**: Ponteiro para o bloco de controlo PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-450">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="069e8-451">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="069e8-451">Return Values</span></span>

- <span data-ttu-id="069e8-452">**NX_SUCCESS**: (0x00) Reiniciou as PPP com sucesso.</span><span class="sxs-lookup"><span data-stu-id="069e8-452">**NX_SUCCESS**: (0x00) Successful PPP restart initiated.</span></span>
- <span data-ttu-id="069e8-453">NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.</span><span class="sxs-lookup"><span data-stu-id="069e8-453">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="069e8-454">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="069e8-454">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="069e8-455">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="069e8-455">Allowed From</span></span>

<span data-ttu-id="069e8-456">Fios</span><span class="sxs-lookup"><span data-stu-id="069e8-456">Threads</span></span>

### <a name="example"></a><span data-ttu-id="069e8-457">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069e8-457">Example</span></span>

```c
/* Restart the PPP instance “my_ppp”.  */
status =  nx_ppp_restart(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been restarted. */
```

## <a name="nx_ppp_start"></a><span data-ttu-id="069e8-458">nx_ppp_start</span><span class="sxs-lookup"><span data-stu-id="069e8-458">nx_ppp_start</span></span>

<span data-ttu-id="069e8-459">Iniciar o processamento de PPP</span><span class="sxs-lookup"><span data-stu-id="069e8-459">Start PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="069e8-460">Prototype</span><span class="sxs-lookup"><span data-stu-id="069e8-460">Prototype</span></span>

```c
UINT  nx_ppp_start(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="069e8-461">Descrição</span><span class="sxs-lookup"><span data-stu-id="069e8-461">Description</span></span>

<span data-ttu-id="069e8-462">Este serviço inicia o processamento de PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-462">This service starts the PPP processing.</span></span> <span data-ttu-id="069e8-463">É normalmente chamado após nx_ppp_stop chamado.</span><span class="sxs-lookup"><span data-stu-id="069e8-463">It is typically called after nx_ppp_stop() called.</span></span>

>[!NOTE]
> <span data-ttu-id="069e8-464">PPP inicia automaticamente o processamento de PPP quando a ligação está ativada.</span><span class="sxs-lookup"><span data-stu-id="069e8-464">PPP automatically starts the PPP processing when the link is enabled.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="069e8-465">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="069e8-465">Input Parameters</span></span>

- <span data-ttu-id="069e8-466">**ppp_ptr**: Ponteiro para o bloco de controlo PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-466">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="069e8-467">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="069e8-467">Return Values</span></span>

- <span data-ttu-id="069e8-468">**NX_SUCCESS**: (0x00) Início de PPP bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="069e8-468">**NX_SUCCESS**: (0x00) Successful PPP start initiated.</span></span> 
- <span data-ttu-id="069e8-469">**NX_PPP_ALREADY_STARTED**: PPP (0xb9) já começou.</span><span class="sxs-lookup"><span data-stu-id="069e8-469">**NX_PPP_ALREADY_STARTED**: (0xb9) PPP already started.</span></span>
- <span data-ttu-id="069e8-470">NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.</span><span class="sxs-lookup"><span data-stu-id="069e8-470">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="069e8-471">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="069e8-471">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="069e8-472">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="069e8-472">Allowed From</span></span>

<span data-ttu-id="069e8-473">Fios</span><span class="sxs-lookup"><span data-stu-id="069e8-473">Threads</span></span>

### <a name="example"></a><span data-ttu-id="069e8-474">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069e8-474">Example</span></span>

```c
/* Start the PPP instance “my_ppp”.  */
status =  nx_ppp_start(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been started. */
```

## <a name="nx_ppp_status_get"></a><span data-ttu-id="069e8-475">nx_ppp_status_get</span><span class="sxs-lookup"><span data-stu-id="069e8-475">nx_ppp_status_get</span></span>

<span data-ttu-id="069e8-476">Obtenha o estado atual de PPP</span><span class="sxs-lookup"><span data-stu-id="069e8-476">Get current PPP status</span></span>

### <a name="prototype"></a><span data-ttu-id="069e8-477">Prototype</span><span class="sxs-lookup"><span data-stu-id="069e8-477">Prototype</span></span>

```c
UINT  nx_ppp_status_get(NX_PPP *ppp_ptr, UINT *status_ptr);
```
### <a name="description"></a><span data-ttu-id="069e8-478">Descrição</span><span class="sxs-lookup"><span data-stu-id="069e8-478">Description</span></span>

<span data-ttu-id="069e8-479">Este serviço obtém o estado atual da instância de PPP especificada.</span><span class="sxs-lookup"><span data-stu-id="069e8-479">This service gets the current status of the specified PPP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="069e8-480">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="069e8-480">Input Parameters</span></span>

- <span data-ttu-id="069e8-481">**ppp_ptr**: Ponteiro para o bloco de controlo PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-481">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="069e8-482">**status_ptr**: Destino para o estado de PPP, são possíveis valores de estado:</span><span class="sxs-lookup"><span data-stu-id="069e8-482">**status_ptr**: Destination for the PPP status, the following are possible status values:</span></span>
    - <span data-ttu-id="069e8-483">**NX_PPP_STATUS_ESTABLISHED**</span><span class="sxs-lookup"><span data-stu-id="069e8-483">**NX_PPP_STATUS_ESTABLISHED**</span></span>
    - <span data-ttu-id="069e8-484">**NX_PPP_STATUS_LCP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="069e8-484">**NX_PPP_STATUS_LCP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="069e8-485">**NX_PPP_STATUS_LCP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="069e8-485">**NX_PPP_STATUS_LCP_FAILED**</span></span>
    - <span data-ttu-id="069e8-486">**NX_PPP_STATUS_PAP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="069e8-486">**NX_PPP_STATUS_PAP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="069e8-487">**NX_PPP_STATUS_PAP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="069e8-487">**NX_PPP_STATUS_PAP_FAILED**</span></span>
    - <span data-ttu-id="069e8-488">**NX_PPP_STATUS_CHAP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="069e8-488">**NX_PPP_STATUS_CHAP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="069e8-489">**NX_PPP_STATUS_CHAP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="069e8-489">**NX_PPP_STATUS_CHAP_FAILED**</span></span>
    - <span data-ttu-id="069e8-490">**NX_PPP_STATUS_IPCP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="069e8-490">**NX_PPP_STATUS_IPCP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="069e8-491">**NX_PPP_STATUS_IPCP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="069e8-491">**NX_PPP_STATUS_IPCP_FAILED**</span></span>

>[!NOTE]
> <span data-ttu-id="069e8-492">O estatuto só é válido se a API devolver NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="069e8-492">The status is only valid if the API returns NX_SUCCESS.</span></span> <span data-ttu-id="069e8-493">Além disso, se algum dos valores de estado \*_FAILED for devolvido, o processamento de PPP é efetivamente interrompido até que seja reiniciado novamente pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="069e8-493">In addition, if any of the \*_FAILED status values are returned, PPP processing is effectively stopped until it is restarted again by the application.</span></span>

### <a name="return-values"></a><span data-ttu-id="069e8-494">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="069e8-494">Return Values</span></span>

- <span data-ttu-id="069e8-495">**NX_SUCCESS:**(0x00) Pedido de estado de PPP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="069e8-495">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="069e8-496">NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.</span><span class="sxs-lookup"><span data-stu-id="069e8-496">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="069e8-497">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="069e8-497">Allowed From</span></span>

<span data-ttu-id="069e8-498">Inicialização, fios, temporizadores, ISRs</span><span class="sxs-lookup"><span data-stu-id="069e8-498">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="069e8-499">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069e8-499">Example</span></span>

```c
UINT ppp_status;
UINT status;


/* Get the current status of PPP instance “my_ppp”.  */
status =  nx_ppp_status_get(&my_ppp, &ppp_status);

/* If status is NX_SUCCESS the current internal PPP status is contained in
   “ppp_status”. */
```
## <a name="nx_ppp_stop"></a><span data-ttu-id="069e8-500">nx_ppp_stop</span><span class="sxs-lookup"><span data-stu-id="069e8-500">nx_ppp_stop</span></span>

<span data-ttu-id="069e8-501">Iniciar o processamento de PPP</span><span class="sxs-lookup"><span data-stu-id="069e8-501">Start PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="069e8-502">Prototype</span><span class="sxs-lookup"><span data-stu-id="069e8-502">Prototype</span></span>

```c
UINT  nx_ppp_stop(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="069e8-503">Descrição</span><span class="sxs-lookup"><span data-stu-id="069e8-503">Description</span></span>

<span data-ttu-id="069e8-504">Este serviço impede o processamento de PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-504">This service stops the PPP processing.</span></span> <span data-ttu-id="069e8-505">O utilizador também pode ligar nx_ppp_start para iniciar o processamento de PPP, se necessário.</span><span class="sxs-lookup"><span data-stu-id="069e8-505">User also can calls nx_ppp_start() to start the PPP processing if needed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="069e8-506">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="069e8-506">Input Parameters</span></span>

- <span data-ttu-id="069e8-507">**ppp_ptr**: Ponteiro para o bloco de controlo PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-507">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="069e8-508">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="069e8-508">Return Values</span></span>

- <span data-ttu-id="069e8-509">**NX_SUCCESS**: (0x00) Início de PPP bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="069e8-509">**NX_SUCCESS**: (0x00) Successful PPP start initiated.</span></span> 
- <span data-ttu-id="069e8-510">**NX_PPP_ALREADY_STOPPED**: (0xb8) PPP já parou.</span><span class="sxs-lookup"><span data-stu-id="069e8-510">**NX_PPP_ALREADY_STOPPED**: (0xb8) PPP already stopped.</span></span>
- <span data-ttu-id="069e8-511">NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.</span><span class="sxs-lookup"><span data-stu-id="069e8-511">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="069e8-512">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="069e8-512">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="069e8-513">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="069e8-513">Allowed From</span></span>

<span data-ttu-id="069e8-514">Fios</span><span class="sxs-lookup"><span data-stu-id="069e8-514">Threads</span></span>

### <a name="example"></a><span data-ttu-id="069e8-515">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069e8-515">Example</span></span>

```c
/* Stop the PPP instance “my_ppp”.  */
status =  nx_ppp_stop(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been stopped. */
```
## <a name="nx_ppp_packet_receive"></a><span data-ttu-id="069e8-516">nx_ppp_packet_receive</span><span class="sxs-lookup"><span data-stu-id="069e8-516">nx_ppp_packet_receive</span></span>

<span data-ttu-id="069e8-517">Receber pacote de PPP</span><span class="sxs-lookup"><span data-stu-id="069e8-517">Receive PPP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="069e8-518">Prototype</span><span class="sxs-lookup"><span data-stu-id="069e8-518">Prototype</span></span>

```c
UINT  nx_ppp_packet_receive(NX_PPP *ppp_ptr, NX_PACKET *packet_ptr);

```

### <a name="description"></a><span data-ttu-id="069e8-519">Descrição</span><span class="sxs-lookup"><span data-stu-id="069e8-519">Description</span></span>

<span data-ttu-id="069e8-520">Este serviço recebe pacote de PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-520">This service receives PPP packet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="069e8-521">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="069e8-521">Input Parameters</span></span>

- <span data-ttu-id="069e8-522">**ppp_ptr**: Ponteiro para o bloco de controlo PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-522">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="069e8-523">**packet_ptr**: Ponteiro para pacote de PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-523">**packet_ptr**: Pointer to PPP packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="069e8-524">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="069e8-524">Return Values</span></span>

- <span data-ttu-id="069e8-525">**NX_SUCCESS:**(0x00) Pedido de estado de PPP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="069e8-525">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="069e8-526">NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.</span><span class="sxs-lookup"><span data-stu-id="069e8-526">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="069e8-527">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="069e8-527">Allowed From</span></span>

<span data-ttu-id="069e8-528">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="069e8-528">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="069e8-529">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069e8-529">Example</span></span>

```c
/* Receive the PPP packet of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_receive(&my_ppp, packet_ptr);

/* If status is NX_SUCCESS the PPP packet has received. */


```
## <a name="nx_ppp_packet_send_set"></a><span data-ttu-id="069e8-530">nx_ppp_packet_send_set</span><span class="sxs-lookup"><span data-stu-id="069e8-530">nx_ppp_packet_send_set</span></span>

<span data-ttu-id="069e8-531">Desaperte a função de envio de pacote de PPP</span><span class="sxs-lookup"><span data-stu-id="069e8-531">Set the PPP packet send function</span></span>

### <a name="prototype"></a><span data-ttu-id="069e8-532">Prototype</span><span class="sxs-lookup"><span data-stu-id="069e8-532">Prototype</span></span>

```c
UINT  nx_ppp_packet_send_set(NX_PPP *ppp_ptr, 
                             VOID (*nx_ppp_packet_send)(NX_PACKET *packet_ptr));

```

### <a name="description"></a><span data-ttu-id="069e8-533">Descrição</span><span class="sxs-lookup"><span data-stu-id="069e8-533">Description</span></span>

<span data-ttu-id="069e8-534">Este serviço define o pacote de PPP enviar funciton.</span><span class="sxs-lookup"><span data-stu-id="069e8-534">This service sets the PPP packet send funciton.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="069e8-535">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="069e8-535">Input Parameters</span></span>

- <span data-ttu-id="069e8-536">**ppp_ptr**: Ponteiro para o bloco de controlo PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-536">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="069e8-537">**nx_ppp_packet_send:** Rotina para enviar pacote de PPP.</span><span class="sxs-lookup"><span data-stu-id="069e8-537">**nx_ppp_packet_send**: Routine to send PPP packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="069e8-538">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="069e8-538">Return Values</span></span>

- <span data-ttu-id="069e8-539">**NX_SUCCESS:**(0x00) Pedido de estado de PPP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="069e8-539">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="069e8-540">NX_PTR_ERROR: (0x07) Ponteiro PPP inválido.</span><span class="sxs-lookup"><span data-stu-id="069e8-540">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="069e8-541">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="069e8-541">Allowed From</span></span>

<span data-ttu-id="069e8-542">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="069e8-542">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="069e8-543">Exemplo</span><span class="sxs-lookup"><span data-stu-id="069e8-543">Example</span></span>

```c
/* Set the PPP packet send function of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_send_set(&my_ppp, nx_ppp_packet_send);

/* If status is NX_SUCCESS the PPP packet send function has set. */


```