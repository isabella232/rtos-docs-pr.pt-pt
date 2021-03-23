---
title: Capítulo 4 - Azure RTOS NetX Crypto API descrição
description: Descrição da Azure RTOS NetX Crypto API
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 04e732bc1fd6012636aab3a57391829f529724cf
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826810"
---
# <a name="chapter-4---azure-rtos-netx-crypto-api-description"></a><span data-ttu-id="e1337-103">Capítulo 4 - Azure RTOS NetX Crypto API descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-103">Chapter 4 - Azure RTOS NetX Crypto API description</span></span>

## <a name="nx_crypto_initialize"></a><span data-ttu-id="e1337-104">nx_crypto_initialize</span><span class="sxs-lookup"><span data-stu-id="e1337-104">nx_crypto_initialize</span></span>

<span data-ttu-id="e1337-105">Inicializa a Biblioteca Segura NetX</span><span class="sxs-lookup"><span data-stu-id="e1337-105">Initializes the NetX Secure Library</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-106">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-106">Prototype</span></span>

```c
UINT nx_crypto_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="e1337-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-107">Description</span></span>

<span data-ttu-id="e1337-108">Esta função inicializa o módulo de biblioteca Azure RTOS NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-108">This function initializes the Azure RTOS NetX Crypto library module.</span></span> <span data-ttu-id="e1337-109">Antes de utilizar qualquer outra função criptográfica, a aplicação deve chamar esta função para executar a inicialização e validar a integridade da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="e1337-109">Before using any of the other cryptographic functions, the application must call this function to perform initialization and to validate the integrity of the library.</span></span> <span data-ttu-id="e1337-110">A não utilização desta função antes de utilizar outros serviços NetX Crypto resultará na devolvição de erros.</span><span class="sxs-lookup"><span data-stu-id="e1337-110">Failure to call this function before using other NetX Crypto services will result in errors being returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-111">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-111">Parameters</span></span>

- <span data-ttu-id="e1337-112">**Nenhuma**</span><span class="sxs-lookup"><span data-stu-id="e1337-112">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-113">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-113">Return Values</span></span>

- <span data-ttu-id="e1337-114">**NX_CRYPTO_SUCCESS** (0x00) Biblioteca NetX Crypto inicializada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="e1337-114">**NX_CRYPTO_SUCCESS** (0x00) Successful initialized NetX Crypto library.</span></span> <span data-ttu-id="e1337-115">As funções da biblioteca estão agora prontas e podem ser usadas.</span><span class="sxs-lookup"><span data-stu-id="e1337-115">The library functions are now ready, and can be used.</span></span>
- <span data-ttu-id="e1337-116">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A criptobigrafia não inicia ou falha na verificação de integridade.</span><span class="sxs-lookup"><span data-stu-id="e1337-116">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library fails to initialize, or fails the integrity check.</span></span> <span data-ttu-id="e1337-117">A aplicação não pode usar esta biblioteca.</span><span class="sxs-lookup"><span data-stu-id="e1337-117">Application cannot use this library.</span></span>

### <a name="example"></a><span data-ttu-id="e1337-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1337-118">Example</span></span>

<span data-ttu-id="e1337-119">TODO</span><span class="sxs-lookup"><span data-stu-id="e1337-119">TODO</span></span>

## <a name="nx_crypto_module_state_get"></a><span data-ttu-id="e1337-120">nx_crypto_module_state_get</span><span class="sxs-lookup"><span data-stu-id="e1337-120">nx_crypto_module_state_get</span></span>

<span data-ttu-id="e1337-121">Recuperar o estado atual do módulo ativado pelo FIPS</span><span class="sxs-lookup"><span data-stu-id="e1337-121">Retrieve the current status of the FIPS-enabled module</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-122">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-122">Prototype</span></span>

```c
UINT nx_crypto_module_state_get(VOID);
```

### <a name="description"></a><span data-ttu-id="e1337-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-123">Description</span></span>

<span data-ttu-id="e1337-124">Este serviço só está disponível na biblioteca de construção FIPS.</span><span class="sxs-lookup"><span data-stu-id="e1337-124">This service is only available in the FIPS build library.</span></span> <span data-ttu-id="e1337-125">Devolve o estado atual da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-125">It returns the state of the current state of the NetX Crypto library.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-126">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-126">Parameters</span></span>

- <span data-ttu-id="e1337-127">**Nenhuma**</span><span class="sxs-lookup"><span data-stu-id="e1337-127">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-128">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-128">Return Values</span></span>

- <span data-ttu-id="e1337-129">**Bandeira de estado:**</span><span class="sxs-lookup"><span data-stu-id="e1337-129">**Status Flag:**</span></span>
  - <span data-ttu-id="e1337-130">NX_CRYPTO_LIBRARY_STATE_UNINITIALIZED 0x00000001</span><span class="sxs-lookup"><span data-stu-id="e1337-130">NX_CRYPTO_LIBRARY_STATE_UNINITIALIZED 0x00000001</span></span>
  - <span data-ttu-id="e1337-131">NX_CRYPTO_LIBRARY_STATE_POST_IN_PROGRESS 0x00000002</span><span class="sxs-lookup"><span data-stu-id="e1337-131">NX_CRYPTO_LIBRARY_STATE_POST_IN_PROGRESS 0x00000002</span></span>
  - <span data-ttu-id="e1337-132">NX_CRYPTO_LIBRARY_STATE_INTEGRITY_TEST_FAILED 0x00000004</span><span class="sxs-lookup"><span data-stu-id="e1337-132">NX_CRYPTO_LIBRARY_STATE_INTEGRITY_TEST_FAILED 0x00000004</span></span>
  - <span data-ttu-id="e1337-133">NX_CRYPTO_LIBRARY_STATE_FUNCTIONAL_TEST_FAILED 0x00000008</span><span class="sxs-lookup"><span data-stu-id="e1337-133">NX_CRYPTO_LIBRARY_STATE_FUNCTIONAL_TEST_FAILED 0x00000008</span></span>
  - <span data-ttu-id="e1337-134">NX_CRYPTO_LIBRARY_STATE_OPERATIONAL 0x80000000</span><span class="sxs-lookup"><span data-stu-id="e1337-134">NX_CRYPTO_LIBRARY_STATE_OPERATIONAL 0x80000000</span></span>
- <span data-ttu-id="e1337-135">**Todos os outros valores são inválidos.**</span><span class="sxs-lookup"><span data-stu-id="e1337-135">**All other values are invalid.**</span></span>

### <a name="example"></a><span data-ttu-id="e1337-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1337-136">Example</span></span>

<span data-ttu-id="e1337-137">TODO</span><span class="sxs-lookup"><span data-stu-id="e1337-137">TODO</span></span>

## <a name="_nx_crypto_method_aes_init"></a><span data-ttu-id="e1337-138">_nx_crypto_method_aes_init</span><span class="sxs-lookup"><span data-stu-id="e1337-138">_nx_crypto_method_aes_init</span></span>

<span data-ttu-id="e1337-139">Inicializa o bloco de controlo cripto AES</span><span class="sxs-lookup"><span data-stu-id="e1337-139">Initializes the AES crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-140">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-140">Prototype</span></span>

```c
UINT _nx_crypto_method_aes_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="e1337-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-141">Description</span></span>

<span data-ttu-id="e1337-142">Esta função inicializa o bloco de controlo AES com a chave dada.</span><span class="sxs-lookup"><span data-stu-id="e1337-142">This function initializes the AES control block with the given key string.</span></span> <span data-ttu-id="e1337-143">Uma vez iniciado o bloco de controlo AES, a operação AES subsequente utilizará a mesma chave e tamanho da chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-143">Once the AES control block is initialized, subsequent AES operation will be using the same key and key size.</span></span>

<span data-ttu-id="e1337-144">A aplicação pode criar vários blocos de controlo AES, cada um representa uma sessão.</span><span class="sxs-lookup"><span data-stu-id="e1337-144">Application may create multiple AES control blocks, each represents a session.</span></span> <span data-ttu-id="e1337-145">Uma chave é atribuída a um bloco de controlo.</span><span class="sxs-lookup"><span data-stu-id="e1337-145">A key is assigned to a control block.</span></span> <span data-ttu-id="e1337-146">A encriptação ou a operação de desencriptação subsequentes podem fazer referência ao mesmo bloco de controlo AES sem a necessidade de re-inicializar o bloco de controlo AES.</span><span class="sxs-lookup"><span data-stu-id="e1337-146">Subsequent encryption or decryption operation can reference to the same AES control block without the need to re-initialize the AES control block.</span></span> <span data-ttu-id="e1337-147">Se a chave para a sessão for alterada, a aplicação precisa de re-inicializar o bloco de controlo AES com a chave atualizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-147">If the key for the session is changed, application needs to re-initialize AES control block with the updated key.</span></span>

<span data-ttu-id="e1337-148">Chamando _ *nx_crypto_method_aes_init()* atualiza automaticamente uma chave e tamanho de chave previamente configurados para a nova chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-148">Calling _ *nx_crypto_method_aes_init()* automatically updates a previously configured key and key size to the new key.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-149">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-149">Parameters</span></span>

- <span data-ttu-id="e1337-150">**método** Ponteiro para um bloco de controlo de método cripto AES válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-150">**method** Pointer to a valid AES crypto method control block.</span></span> <span data-ttu-id="e1337-151">Estão disponíveis os seguintes métodos cripto AES pré-definidos:</span><span class="sxs-lookup"><span data-stu-id="e1337-151">The following pre-defined AES crypto methods are available:</span></span>
  - <span data-ttu-id="e1337-152">*crypto_method_aes_cbc_128*</span><span class="sxs-lookup"><span data-stu-id="e1337-152">*crypto_method_aes_cbc_128*</span></span>
  - <span data-ttu-id="e1337-153">*crypto_method_aes_cbc_192*</span><span class="sxs-lookup"><span data-stu-id="e1337-153">*crypto_method_aes_cbc_192*</span></span>
  - <span data-ttu-id="e1337-154">*crypto_method_aes_cbc_256*</span><span class="sxs-lookup"><span data-stu-id="e1337-154">*crypto_method_aes_cbc_256*</span></span>
  - <span data-ttu-id="e1337-155">*crypto_method_aes_ctr_128*</span><span class="sxs-lookup"><span data-stu-id="e1337-155">*crypto_method_aes_ctr_128*</span></span>
  - <span data-ttu-id="e1337-156">*crypto_method_aes_ctr_192*</span><span class="sxs-lookup"><span data-stu-id="e1337-156">*crypto_method_aes_ctr_192*</span></span>
  - <span data-ttu-id="e1337-157">*crypto_method_aes_ctr_256*</span><span class="sxs-lookup"><span data-stu-id="e1337-157">*crypto_method_aes_ctr_256*</span></span>
  - <span data-ttu-id="e1337-158">*crypto_method_aes_xcbc_128*</span><span class="sxs-lookup"><span data-stu-id="e1337-158">*crypto_method_aes_xcbc_128*</span></span>
  - <span data-ttu-id="e1337-159">*crypto_method_aes_ccm_8_128*</span><span class="sxs-lookup"><span data-stu-id="e1337-159">*crypto_method_aes_ccm_8_128*</span></span>
- <span data-ttu-id="e1337-160">**chave** Aponta para um tampão que contém a chave AES</span><span class="sxs-lookup"><span data-stu-id="e1337-160">**key** Points to a buffer containing the AES key</span></span>
- <span data-ttu-id="e1337-161">**key_size_in_bits** Tamanho da chave, em pedaços.</span><span class="sxs-lookup"><span data-stu-id="e1337-161">**key_size_in_bits** Size of the key, in bits.</span></span> <span data-ttu-id="e1337-162">Os valores válidos são:</span><span class="sxs-lookup"><span data-stu-id="e1337-162">Valid values are:</span></span>
  - <span data-ttu-id="e1337-163">*NX_CRYPTO_AES_KEY_SIZE_128_BITS*</span><span class="sxs-lookup"><span data-stu-id="e1337-163">*NX_CRYPTO_AES_KEY_SIZE_128_BITS*</span></span>
  - <span data-ttu-id="e1337-164">*NX_CRYPTO_AES_KEY_SIZE_192_BITS*</span><span class="sxs-lookup"><span data-stu-id="e1337-164">*NX_CRYPTO_AES_KEY_SIZE_192_BITS*</span></span>
  - <span data-ttu-id="e1337-165">*NX_CRYPTO_AES_KEY_SIZE_256_BITS*</span><span class="sxs-lookup"><span data-stu-id="e1337-165">*NX_CRYPTO_AES_KEY_SIZE_256_BITS*</span></span>
  - <span data-ttu-id="e1337-166">**Todos os outros valores são inválidos.**</span><span class="sxs-lookup"><span data-stu-id="e1337-166">**All other values are invalid.**</span></span>
- <span data-ttu-id="e1337-167">**cabo** Este serviço devolve uma manípula ao autor da chamada.</span><span class="sxs-lookup"><span data-stu-id="e1337-167">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="e1337-168">O cabo é dependente da implementação e não está a ser utilizado nesta implementação.</span><span class="sxs-lookup"><span data-stu-id="e1337-168">The handle is implementation-dependent, and is not being used in this implementation.</span></span> <span data-ttu-id="e1337-169">O pedido deve passar NU PARA o cabo.</span><span class="sxs-lookup"><span data-stu-id="e1337-169">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="e1337-170">**crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo AES.</span><span class="sxs-lookup"><span data-stu-id="e1337-170">**crypto_metadata** Pointer to a valid memory space for the AES control block.</span></span> <span data-ttu-id="e1337-171">O endereço inicial do espaço de memória deve estar alinhado a 4 byte.</span><span class="sxs-lookup"><span data-stu-id="e1337-171">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="e1337-172">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-172">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-173">Para a AES, o tamanho dos metadados deve ser *de dimensão (NX_AES)*</span><span class="sxs-lookup"><span data-stu-id="e1337-173">For AES, the metadata size must be *sizeof(NX_AES)*</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-174">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-174">Return Values</span></span>

- <span data-ttu-id="e1337-175">**NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo AES com a chave e o tamanho da chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-175">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the AES control block with the key and key size.</span></span>
- <span data-ttu-id="e1337-176">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-176">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-177">**NX_PTR_ERROR (0x07)** Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-177">**NX_PTR_ERROR (0x07)** Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>
- <span data-ttu-id="e1337-178">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) O tamanho da chave não é válido para AES.</span><span class="sxs-lookup"><span data-stu-id="e1337-178">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) Key size is not a valid for AES.</span></span>

## <a name="_nx_crypto_method_aes_operation"></a><span data-ttu-id="e1337-179">_nx_crypto_method_aes_operation</span><span class="sxs-lookup"><span data-stu-id="e1337-179">_nx_crypto_method_aes_operation</span></span>

<span data-ttu-id="e1337-180">Efetuar uma operação AES (encriptação ou desencriptação).</span><span class="sxs-lookup"><span data-stu-id="e1337-180">Perform an AES operation (encryption or decryption).</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-181">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-181">Prototype</span></span>

```c
UINT _nx_crypto_method_aes_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT status));
```

### <a name="description"></a><span data-ttu-id="e1337-182">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-182">Description</span></span>

<span data-ttu-id="e1337-183">Esta função executa a encriptação ou operação de desencriptação AES.</span><span class="sxs-lookup"><span data-stu-id="e1337-183">This function performs AES encryption or decryption operation.</span></span> <span data-ttu-id="e1337-184">O bloco de controlo AES deve ter sido inicializado com _ *nx_crypto_method_aes_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-184">The AES control block must have been initialized with _ *nx_crypto_method_aes_init()*.</span></span> <span data-ttu-id="e1337-185">O algoritmo AES a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*</span><span class="sxs-lookup"><span data-stu-id="e1337-185">The AES algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="e1337-186">O tamanho do tampão de entrada deve ser um múltiplo de 16 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-186">The input buffer size must be a multiple of 16 bytes.</span></span> <span data-ttu-id="e1337-187">O tamanho dos dados desencriptados é do mesmo tamanho do tamanho dos dados de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-187">The size of the decrypted data is the same size of the input data size.</span></span> <span data-ttu-id="e1337-188">Se os dados encriptados forem acolchoados para obter um múltiplo do tamanho do bloco AES, o acolchoamento será incluído no tampão de saída e deve ser tratado pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="e1337-188">If the encrypted data was padded to achieve an even multiple of the AES block size, the padding will be included in the output buffer and must be handled by the application.</span></span>

<span data-ttu-id="e1337-189">Esta operação não guarda informações estatais e não altera o material chave no bloco de controlo AES.</span><span class="sxs-lookup"><span data-stu-id="e1337-189">This operation does not keep state information, and does not alter the key material in the AES control block.</span></span>

<span data-ttu-id="e1337-190">Quando a operação é NX_CRYPTO_SET_ADDITIONAL_DATA e o algoritm é AES-CCM8, a entrada aponta para dados adicionais e input_length_in_byte é o comprimento de dados adicionais.</span><span class="sxs-lookup"><span data-stu-id="e1337-190">When the op is NX_CRYPTO_SET_ADDITIONAL_DATA and algoritm is AES-CCM8, the input points to additional data and input_length_in_byte is the length of additional data.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-191">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-191">Parameters</span></span>

- <span data-ttu-id="e1337-192">**op** Tipo de operação para realizar.</span><span class="sxs-lookup"><span data-stu-id="e1337-192">**op** Type of operation to perform.</span></span> <span data-ttu-id="e1337-193">As operações válidas são:</span><span class="sxs-lookup"><span data-stu-id="e1337-193">Valid opertions are:</span></span>
  - <span data-ttu-id="e1337-194">*NX_CRYPTO_ENCRYPT*</span><span class="sxs-lookup"><span data-stu-id="e1337-194">*NX_CRYPTO_ENCRYPT*</span></span>
  - <span data-ttu-id="e1337-195">*NX_CRYPTO_DECRYPT*</span><span class="sxs-lookup"><span data-stu-id="e1337-195">*NX_CRYPTO_DECRYPT*</span></span>
  - <span data-ttu-id="e1337-196">*NX_CRYPTO_AUTHENTICATE (apenas AES-XCBC)*</span><span class="sxs-lookup"><span data-stu-id="e1337-196">*NX_CRYPTO_AUTHENTICATE (AES-XCBC only)*</span></span>
  - <span data-ttu-id="e1337-197">*NX_CRYPTO_SET_ADDITIONAL_DATA (apenas AES-CCM8)*</span><span class="sxs-lookup"><span data-stu-id="e1337-197">*NX_CRYPTO_SET_ADDITIONAL_DATA (AES-CCM8 only)*</span></span>
- <span data-ttu-id="e1337-198">**cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-198">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-199">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-199">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-200">**método** Ponteiro para o método cripto AES válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-200">**method** Pointer to the valid AES crypto method.</span></span> <span data-ttu-id="e1337-201">O método cripto utilizado aqui deve ser o mesmo utilizado no *nx_crypto_method_aes_init().*</span><span class="sxs-lookup"><span data-stu-id="e1337-201">The crypto method used here must be the same used in the *nx_crypto_method_aes_init().*</span></span>
- <span data-ttu-id="e1337-202">**input_data** Aponta para um tampão que contém dados de texto encriptados.</span><span class="sxs-lookup"><span data-stu-id="e1337-202">**input_data** Points to a buffer containing encrypted text data.</span></span> <span data-ttu-id="e1337-203">Não existem restrições ao tampão de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-203">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="e1337-204">**input_data_size** Tamanho dos dados de entrada, bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-204">**input_data_size** Size of the input data, in bytes.</span></span> <span data-ttu-id="e1337-205">O tamanho dos dados de entrada deve ser um múltiplo de 16 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-205">The input data size must be a multiple of 16 bytes.</span></span>
- <span data-ttu-id="e1337-206">**iv_ptr** Ponteiro para o vetor inicial.</span><span class="sxs-lookup"><span data-stu-id="e1337-206">**iv_ptr** Pointer to the Initial Vector.</span></span> <span data-ttu-id="e1337-207">Não há restrições ao tampão IV.</span><span class="sxs-lookup"><span data-stu-id="e1337-207">There are no restrictions on the IV buffer.</span></span>
- <span data-ttu-id="e1337-208">**iv_size** Tamanho do bloco de vetor inicial, em bytes Este campo deve ser 16.</span><span class="sxs-lookup"><span data-stu-id="e1337-208">**iv_size** Size of the Initial Vector block, in bytes This field must be 16.</span></span>
- <span data-ttu-id="e1337-209">**output_buffer** Ponteiro para a área de memória para a AES armazenar os dados de texto claros.</span><span class="sxs-lookup"><span data-stu-id="e1337-209">**output_buffer** Pointer to the memory area for AES to store the clear text data.</span></span> <span data-ttu-id="e1337-210">A aplicação deve atribuir espaço para o tampão de saída.</span><span class="sxs-lookup"><span data-stu-id="e1337-210">Application must allocate space for the output buffer.</span></span> <span data-ttu-id="e1337-211">O tampão de saída pode sobrepor-se ao tampão de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-211">Output buffer may overlap with input buffer.</span></span> <span data-ttu-id="e1337-212">O tampão de saída pode sobrepor-se ao tampão de entrada se partilharem o mesmo endereço inicial.</span><span class="sxs-lookup"><span data-stu-id="e1337-212">The output buffer may overlap with the input buffer if they share the same starting address.</span></span>
- <span data-ttu-id="e1337-213">**output_buffer_size** Tamanho do tampão de saída em bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-213">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="e1337-214">O tamanho do tampão de saída deve ser pelo menos o mesmo do tamanho do tampão de entrada, e o tamanho do tampão de saída deve ser um múltiplo de 16 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-214">Output buffer size must be at least the same of the input buffer size, and the output buffer size must be a multiple of 16 bytes.</span></span>
- <span data-ttu-id="e1337-215">**crypto_metadata** Ponteiro para o bloco de controlo AES utilizado em *_nx_crypto_method_aes_init() \* . \**</span><span class="sxs-lookup"><span data-stu-id="e1337-215">**crypto_metadata** Pointer to the AES control block used in *_nx_crypto_method_aes_init()\*.\**</span></span>
- <span data-ttu-id="e1337-216">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-216">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-217">Para a AES, o tamanho dos metadados deve *ser do tamanho (NX_AES)*</span><span class="sxs-lookup"><span data-stu-id="e1337-217">For AES, the metadata size must *sizeof(NX_AES)*</span></span>
- <span data-ttu-id="e1337-218">**packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-218">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-219">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-219">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-220">**nx_crypto_hw_process_callback** - Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-220">**nx_crypto_hw_process_callback** - This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-221">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-221">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-222">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-222">Return Values</span></span>

- <span data-ttu-id="e1337-223">**NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação AES.</span><span class="sxs-lookup"><span data-stu-id="e1337-223">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the AES operation.</span></span>
- <span data-ttu-id="e1337-224">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-224">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-225">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.</span><span class="sxs-lookup"><span data-stu-id="e1337-225">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="e1337-226">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Algoritmo AES inválido sendo especificado\*\*.</span><span class="sxs-lookup"><span data-stu-id="e1337-226">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid AES algorithm being specified\*\*.</span></span>

## <a name="_nx_crypto_method_aes_cleanup"></a><span data-ttu-id="e1337-227">_nx_crypto_method_aes_cleanup</span><span class="sxs-lookup"><span data-stu-id="e1337-227">_nx_crypto_method_aes_cleanup</span></span>

<span data-ttu-id="e1337-228">Limpe o bloco de controlo AES.</span><span class="sxs-lookup"><span data-stu-id="e1337-228">Clean up the AES control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-229">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-229">Prototype</span></span>

```c
UINT _nx_crypto_method_aes_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="e1337-230">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-230">Description</span></span>

<span data-ttu-id="e1337-231">A aplicação chama a esta função para limpar o bloco de controlo AES depois de determinar que esta sessão AES já não é necessária.</span><span class="sxs-lookup"><span data-stu-id="e1337-231">Application calls this function to clean up the AES control block after it determines this AES session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-232">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-232">Parameters</span></span>

- <span data-ttu-id="e1337-233">**crypto_metadata** Ponteiro para o bloco de controlo AES utilizado em *_nx_crypto_method_aes_init() \* . \**</span><span class="sxs-lookup"><span data-stu-id="e1337-233">**crypto_metadata** Pointer to the AES control block used in *_nx_crypto_method_aes_init()\*.\**</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-234">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-234">Return Values</span></span>

- <span data-ttu-id="e1337-235">**NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão AES.</span><span class="sxs-lookup"><span data-stu-id="e1337-235">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the AES session.</span></span>
- <span data-ttu-id="e1337-236">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-236">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_3des_init"></a><span data-ttu-id="e1337-237">_nx_crypto_method_3des_init</span><span class="sxs-lookup"><span data-stu-id="e1337-237">_nx_crypto_method_3des_init</span></span>

<span data-ttu-id="e1337-238">Inicialize o bloco de controlo 3DES.</span><span class="sxs-lookup"><span data-stu-id="e1337-238">Initialize the 3DES control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-239">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-239">Prototype</span></span>

```c
UINT _nx_crypto_method_3des_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="e1337-240">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-240">Description</span></span>

<span data-ttu-id="e1337-241">Esta função inicializa o bloco de controlo Triple DES (3DES) com as três cordas de teclas.</span><span class="sxs-lookup"><span data-stu-id="e1337-241">This function initializes the Triple DES (3DES) control block with the given three key strings.</span></span> <span data-ttu-id="e1337-242">As cordas das chaves devem ser de 8 bytes cada.</span><span class="sxs-lookup"><span data-stu-id="e1337-242">The key strings must be 8 bytes each.</span></span> <span data-ttu-id="e1337-243">As três teclas DES devem ser concatenadas na memória contígua do tampão de 24 byte.</span><span class="sxs-lookup"><span data-stu-id="e1337-243">The three DES keys must be concatenated into contiguous memory of 24-byte buffer.</span></span> <span data-ttu-id="e1337-244">Para a construção compatível com o FIPS, as três teclas devem ser diferentes de cada uma ou a função retornará o erro NX_CRYPTO_INVALID_KEY.</span><span class="sxs-lookup"><span data-stu-id="e1337-244">For FIPS-compliant build, the three keys must be different from each or the function will return the NX_CRYPTO_INVALID_KEY error.</span></span> <span data-ttu-id="e1337-245">Uma vez inicializado o bloco de controlo 3DES, as operações subsequentes em 3DES utilizarão as mesmas teclas.</span><span class="sxs-lookup"><span data-stu-id="e1337-245">Once the 3DES control block is initialized, subsequent 3DES operations will use the same keys.</span></span>

<span data-ttu-id="e1337-246">Uma aplicação pode criar vários blocos de controlo 3DES, cada um representando uma sessão.</span><span class="sxs-lookup"><span data-stu-id="e1337-246">An application may create multiple 3DES control blocks, each representing a session.</span></span> <span data-ttu-id="e1337-247">Uma chave é atribuída a um bloco de controlo e as operações subsequentes de encriptação ou desencriptação podem referenciar o mesmo bloco de controlo sem necessidade de re-inicializar.</span><span class="sxs-lookup"><span data-stu-id="e1337-247">A key is assigned to a control block and subsequent encryption or decryption operations can reference the same control block without needing to re-initialize.</span></span> <span data-ttu-id="e1337-248">Se a chave para uma sessão for alterada, a aplicação terá de re-inicializar o bloco de controlo com a tecla atualizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-248">If the key for a session is changed, the application will need to re-initialize the control block with the updated key.</span></span>

<span data-ttu-id="e1337-249">Chamando _ *nx_crypto_method_3des_init()* atualiza automaticamente uma chave previamente configurada para as novas teclas.</span><span class="sxs-lookup"><span data-stu-id="e1337-249">Calling _ *nx_crypto_method_3des_init()* automatically updates a previously configured key to the new keys.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-250">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-250">Parameters</span></span>

- <span data-ttu-id="e1337-251">**método** Ponteiro para um bloco de controlo de método cripto 3DES válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-251">**method** Pointer to a valid 3DES crypto method control block.</span></span> <span data-ttu-id="e1337-252">Está disponível o seguinte método cripto 3DES pré-definido: ***crypto_method_3des***</span><span class="sxs-lookup"><span data-stu-id="e1337-252">The following pre-defined 3DES crypto method is available: ***crypto_method_3des***</span></span>
- <span data-ttu-id="e1337-253">**chave** Aponta para um tampão que contém a chave de três (3) DES</span><span class="sxs-lookup"><span data-stu-id="e1337-253">**key** Points to a buffer containing the three (3) DES key</span></span>
- <span data-ttu-id="e1337-254">**key_size_in_bits** Devem ser 192 (3 teclas, cada 64 bits).</span><span class="sxs-lookup"><span data-stu-id="e1337-254">**key_size_in_bits** Must be 192 (3 keys, each 64 bits).</span></span>
- <span data-ttu-id="e1337-255">**cabo** Este serviço devolve uma manípula ao autor da chamada.</span><span class="sxs-lookup"><span data-stu-id="e1337-255">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="e1337-256">O cabo identifica o bloco de controlo 3DES que está a ser inicializado.</span><span class="sxs-lookup"><span data-stu-id="e1337-256">The handle identifies the 3DES control block being initialized.</span></span> <span data-ttu-id="e1337-257">As operações subsequentes 3DES (encriptação, desencriptação e limpeza) utilizam este cabo para aceder ao bloco de controlo 3DES</span><span class="sxs-lookup"><span data-stu-id="e1337-257">Subsequent 3DES operations (encryption, decryption, and cleanup) use this handle to access the 3DES control block</span></span>
- <span data-ttu-id="e1337-258">**crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo 3DES.</span><span class="sxs-lookup"><span data-stu-id="e1337-258">**crypto_metadata** Pointer to a valid memory space for the 3DES control block.</span></span> <span data-ttu-id="e1337-259">O endereço inicial do espaço de memória deve estar alinhado a 4 byte.</span><span class="sxs-lookup"><span data-stu-id="e1337-259">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="e1337-260">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-260">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-261">Para 3DES, o tamanho dos metadados deve ser *de tamanho (NX_3DES)*</span><span class="sxs-lookup"><span data-stu-id="e1337-261">For 3DES, the metadata size must be *sizeof(NX_3DES)*</span></span>

### <a name="return-value"></a><span data-ttu-id="e1337-262">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="e1337-262">Return Value</span></span>

- <span data-ttu-id="e1337-263">**NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo 3DES com a chave e o tamanho da chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-263">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the 3DES control block with the key and key size.</span></span>
- <span data-ttu-id="e1337-264">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-264">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-265">**NX_PTR_ERROR (0x07)** Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-265">**NX_PTR_ERROR (0x07)** Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>
- <span data-ttu-id="e1337-266">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) O tamanho da chave não é válido para 3DES.</span><span class="sxs-lookup"><span data-stu-id="e1337-266">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) Key size is not a valid for 3DES.</span></span>

## <a name="_nx_crypto_method_3des_operation"></a><span data-ttu-id="e1337-267">_nx_crypto_method_3des_operation</span><span class="sxs-lookup"><span data-stu-id="e1337-267">_nx_crypto_method_3des_operation</span></span>

<span data-ttu-id="e1337-268">Criptografe ou desencripta com 3DES.</span><span class="sxs-lookup"><span data-stu-id="e1337-268">Encrypt or Decrypt with 3DES.</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-269">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-269">Prototype</span></span>

```c
UINT _nx_crypto_method_3des_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="e1337-270">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-270">Description</span></span>

<span data-ttu-id="e1337-271">Esta função executa a encriptação ou operação de desencriptação 3DES.</span><span class="sxs-lookup"><span data-stu-id="e1337-271">This function performs 3DES encryption or decryption operation.</span></span> <span data-ttu-id="e1337-272">O bloco de controlo 3DES deve ter sido inicializado com _ *nx_crypto_method_3des_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-272">The 3DES control block must have been initialized with _ *nx_crypto_method_3des_init()*.</span></span> <span data-ttu-id="e1337-273">O algoritmo 3DES a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*</span><span class="sxs-lookup"><span data-stu-id="e1337-273">The 3DES algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="e1337-274">O tamanho do tampão de entrada deve ser um múltiplo de 8 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-274">The input buffer size must be a multiple of 8 bytes.</span></span> <span data-ttu-id="e1337-275">O tamanho dos dados desencriptados é do mesmo tamanho do tamanho dos dados de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-275">The size of the decrypted data is the same size of the input data size.</span></span> <span data-ttu-id="e1337-276">Se os dados encriptados foram acolchoados para obter um múltiplo do tamanho do bloco 3DES, o acolchoamento será incluído no tampão de saída e deve ser tratado pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="e1337-276">If the encrypted data was padded to achieve an even multiple of the 3DES block size, the padding will be included in the output buffer and must be handled by the application.</span></span>

<span data-ttu-id="e1337-277">Esta operação não guarda informações estatais e não altera o material chave no bloco de controlo 3DES.</span><span class="sxs-lookup"><span data-stu-id="e1337-277">This operation does not keep state information, and does not alter the key material in the 3DES control block.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-278">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-278">Parameters</span></span>

- <span data-ttu-id="e1337-279">**op** Tipo de operação para realizar.</span><span class="sxs-lookup"><span data-stu-id="e1337-279">**op** Type of operation to perform.</span></span> <span data-ttu-id="e1337-280">As operações válidas são:</span><span class="sxs-lookup"><span data-stu-id="e1337-280">Valid operations are:</span></span>
  - <span data-ttu-id="e1337-281">*NX_CRYPTO_ENCRYPT*</span><span class="sxs-lookup"><span data-stu-id="e1337-281">*NX_CRYPTO_ENCRYPT*</span></span>
  - <span data-ttu-id="e1337-282">*NX_CRYPTO_DECRYPT*</span><span class="sxs-lookup"><span data-stu-id="e1337-282">*NX_CRYPTO_DECRYPT*</span></span>
- <span data-ttu-id="e1337-283">**cabo** A pega inicializada por *_nx_crypto_method_3des_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-283">**handle** The handle initialized by *_nx_crypto_method_3des_init()*.</span></span>
- <span data-ttu-id="e1337-284">**método** Ponteiro para o método cripto 3DES válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-284">**method** Pointer to the valid 3DES crypto method.</span></span> <span data-ttu-id="e1337-285">O método cripto utilizado aqui deve ser o mesmo utilizado no *nx_crypto_method_3des_init().*</span><span class="sxs-lookup"><span data-stu-id="e1337-285">The crypto method used here must be the same used in the *nx_crypto_method_3des_init().*</span></span>
- <span data-ttu-id="e1337-286">**input_data** Aponta para um tampão que contém dados de texto encriptados.</span><span class="sxs-lookup"><span data-stu-id="e1337-286">**input_data** Points to a buffer containing encrypted text data.</span></span>
<span data-ttu-id="e1337-287">Não existem restrições ao tampão de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-287">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="e1337-288">**input_data_size** Tamanho dos dados de entrada, bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-288">**input_data_size** Size of the input data, in bytes.</span></span> <span data-ttu-id="e1337-289">O tamanho dos dados de entrada deve ser um múltiplo de 8 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-289">The input data size must be a multiple of 8 bytes.</span></span>
- <span data-ttu-id="e1337-290">**iv_ptr** Ponteiro para o vetor inicial.</span><span class="sxs-lookup"><span data-stu-id="e1337-290">**iv_ptr** Pointer to the Initial Vector.</span></span> <span data-ttu-id="e1337-291">Não há restrições ao tampão IV.</span><span class="sxs-lookup"><span data-stu-id="e1337-291">There are no restrictions on the IV buffer.</span></span>
- <span data-ttu-id="e1337-292">**iv_size** Tamanho do bloco de vetor inicial, em bytes Este campo deve ser 8.</span><span class="sxs-lookup"><span data-stu-id="e1337-292">**iv_size** Size of the Initial Vector block, in bytes This field must be 8.</span></span>
- <span data-ttu-id="e1337-293">**output_buffer** Ponteiro para a área de memória para 3DES para armazenar os dados de texto claros.</span><span class="sxs-lookup"><span data-stu-id="e1337-293">**output_buffer** Pointer to the memory area for 3DES to store the clear text data.</span></span> <span data-ttu-id="e1337-294">A aplicação deve atribuir espaço para o tampão de saída.</span><span class="sxs-lookup"><span data-stu-id="e1337-294">Application must allocate space for the output buffer.</span></span> <span data-ttu-id="e1337-295">O tampão de saída pode sobrepor-se ao tampão de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-295">Output buffer may overlap with input buffer.</span></span> <span data-ttu-id="e1337-296">O tampão de saída pode sobrepor-se ao tampão de entrada se partilharem o mesmo endereço inicial.</span><span class="sxs-lookup"><span data-stu-id="e1337-296">The output buffer may overlap with the input buffer if they share the same starting address.</span></span>
- <span data-ttu-id="e1337-297">**output_buffer_size** Tamanho do tampão de saída em bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-297">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="e1337-298">O tamanho do tampão de saída deve ser pelo menos o mesmo do tamanho do tampão de entrada, e o tamanho do tampão de saída deve ser um múltiplo de 8 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-298">Output buffer size must be at least the same of the input buffer size, and the output buffer size must be a multiple of 8 bytes.</span></span>
- <span data-ttu-id="e1337-299">**crypto_metadata** Ponteiro para o bloco de controlo 3DES utilizado em *_nx_crypto_method_3des_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-299">**crypto_metadata** Pointer to the 3DES control block used in *_nx_crypto_method_3des_init()*.</span></span>
- <span data-ttu-id="e1337-300">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-300">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-301">Para 3DES, o tamanho dos metadados deve ser *de tamanho (NX_3DES)*</span><span class="sxs-lookup"><span data-stu-id="e1337-301">For 3DES, the metadata size must be *sizeof(NX_3DES)*</span></span>
- <span data-ttu-id="e1337-302">**packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-302">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-303">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-303">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-304">**nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-304">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-305">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-305">Any values passed in are silently ignored.</span></span>

### <a name="description"></a><span data-ttu-id="e1337-306">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-306">Description</span></span>

<span data-ttu-id="e1337-307">Esta função executa encriptação 3DES.</span><span class="sxs-lookup"><span data-stu-id="e1337-307">This function performs 3DES encryption.</span></span> <span data-ttu-id="e1337-308">O bloco de controlo 3DES deve ter sido inicializado com _ *nx_crypto_moethod_3des_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-308">The 3DES control block must have been initialized with _ *nx_crypto_moethod_3des_init()*.</span></span> <span data-ttu-id="e1337-309">Esta operação não guarda informações estatais e não altera o material chave no bloco de controlo 3DES.</span><span class="sxs-lookup"><span data-stu-id="e1337-309">This operation does not keep state information, and does not alter the key material in the 3DES control block.</span></span> <span data-ttu-id="e1337-310">Note que o estofamento não é adicionado por esta função, pelo que o chamador terá de manusear o estofamento antes de invocar a operação de encriptação.</span><span class="sxs-lookup"><span data-stu-id="e1337-310">Note that padding is not added by this function so the caller will need to handle padding before invoking the encryption operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-311">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-311">Return Values</span></span>

- <span data-ttu-id="e1337-312">**NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo 3DES com a chave e o tamanho da chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-312">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the 3DES control block with the key and key size.</span></span>
- <span data-ttu-id="e1337-313">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-313">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-314">**NX_PTR_ERROR (0x07)** Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-314">**NX_PTR_ERROR (0x07)** Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_3des_cleanup"></a><span data-ttu-id="e1337-315">_nx_crypto_method_3des_cleanup</span><span class="sxs-lookup"><span data-stu-id="e1337-315">_nx_crypto_method_3des_cleanup</span></span>

<span data-ttu-id="e1337-316">Limpe o bloco de controlo 3DES.</span><span class="sxs-lookup"><span data-stu-id="e1337-316">Clean up the 3DES control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-317">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-317">Prototype</span></span>

```c
UINT _nx_crypto_method_3des_cleanup(VOID *crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="e1337-318">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-318">Description</span></span>

<span data-ttu-id="e1337-319">A aplicação chama esta função para limpar o bloco de controlo 3DES depois de determinar que esta sessão 3DES já não é necessária.</span><span class="sxs-lookup"><span data-stu-id="e1337-319">Application calls this function to clean up the 3DES control block after it determines this 3DES session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-320">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-320">Parameters</span></span>

- <span data-ttu-id="e1337-321">**cabo** A pega inicializada por *_nx_crypto_method_3des_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-321">**handle** The handle initialized by *_nx_crypto_method_3des_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-322">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-322">Return Values</span></span>

- <span data-ttu-id="e1337-323">**NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão 3DES.</span><span class="sxs-lookup"><span data-stu-id="e1337-323">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the 3DES session.</span></span>
- <span data-ttu-id="e1337-324">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-324">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_drbg_init"></a><span data-ttu-id="e1337-325">_nx_crypto_method_drbg_init</span><span class="sxs-lookup"><span data-stu-id="e1337-325">_nx_crypto_method_drbg_init</span></span>

<span data-ttu-id="e1337-326">Inicializa o bloco de controlo cripto DRBG</span><span class="sxs-lookup"><span data-stu-id="e1337-326">Initializes the DRBG crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-327">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-327">Prototype</span></span>

```c
UINT _nx_crypto_method_drbg_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="e1337-328">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-328">Description</span></span>

<span data-ttu-id="e1337-329">Esta função inicializa o bloco de controlo DRBG com a chave dada.</span><span class="sxs-lookup"><span data-stu-id="e1337-329">This function initializes the DRBG control block with the given key string.</span></span> <span data-ttu-id="e1337-330">Uma vez iniciado o bloco de controlo DRBG, a operação DRBG subsequente deve utilizar o mesmo bloco de controlo.</span><span class="sxs-lookup"><span data-stu-id="e1337-330">Once the DRBG control block is initialized, subsequent DRBG operation shall be using the same control block.</span></span>

<span data-ttu-id="e1337-331">A aplicação pode criar vários blocos de controlo DRBG, cada um representa uma sessão.</span><span class="sxs-lookup"><span data-stu-id="e1337-331">Application may create multiple DRBG control blocks, each represents a session.</span></span> <span data-ttu-id="e1337-332">A inicialização do bloco de controlo DRBG inicia uma nova sessão de computação de haxixe.</span><span class="sxs-lookup"><span data-stu-id="e1337-332">Initializing the DRBG control block starts a new hash computation session.</span></span> <span data-ttu-id="e1337-333">A re-inicialização do bloco de controlo DRBG abandona a sessão atual e protagoniza uma nova.</span><span class="sxs-lookup"><span data-stu-id="e1337-333">Re-initializing the DRBG control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-334">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-334">Parameters</span></span>

- <span data-ttu-id="e1337-335">**método** Ponteiro para um bloco de controlo de método cripto DRBG válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-335">**method** Pointer to a valid DRBG crypto method control block.</span></span> <span data-ttu-id="e1337-336">Estão disponíveis os seguintes métodos cripto pré-definidos:</span><span class="sxs-lookup"><span data-stu-id="e1337-336">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="e1337-337">*crypto_method_drbg*</span><span class="sxs-lookup"><span data-stu-id="e1337-337">*crypto_method_drbg*</span></span>
- <span data-ttu-id="e1337-338">**chave** Este campo não é utilizado para a DRBG.</span><span class="sxs-lookup"><span data-stu-id="e1337-338">**key** This field is not used for DRBG.</span></span>
- <span data-ttu-id="e1337-339">**key_size_in_bits** Este campo não é utilizado para a DRBG.</span><span class="sxs-lookup"><span data-stu-id="e1337-339">**key_size_in_bits** This field is not used for DRBG.</span></span>
- <span data-ttu-id="e1337-340">**cabo** Este serviço devolve uma manípula ao autor da chamada.</span><span class="sxs-lookup"><span data-stu-id="e1337-340">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="e1337-341">O cabo é dependente da implementação e não está a ser utilizado nesta implementação.</span><span class="sxs-lookup"><span data-stu-id="e1337-341">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="e1337-342">O pedido deve passar NU PARA o cabo.</span><span class="sxs-lookup"><span data-stu-id="e1337-342">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="e1337-343">**crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo DRBG.</span><span class="sxs-lookup"><span data-stu-id="e1337-343">**crypto_metadata** Pointer to a valid memory space for the DRBG control block.</span></span> <span data-ttu-id="e1337-344">O endereço inicial do espaço de memória deve estar alinhado a 4 byte.</span><span class="sxs-lookup"><span data-stu-id="e1337-344">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="e1337-345">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-345">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-346">Para a DRBG, o tamanho dos metadados deve ser *de tamanho (NX_CRYPTO_DRBG)*</span><span class="sxs-lookup"><span data-stu-id="e1337-346">For DRBG, the metadata size must be *sizeof(NX_CRYPTO_DRBG)*</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-347">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-347">Return Values</span></span>

- <span data-ttu-id="e1337-348">**NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo DRBG com a chave e o tamanho da chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-348">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the DRBG control block with the key and key size.</span></span>
- <span data-ttu-id="e1337-349">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-349">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-350">**NX_PTR_ERROR** (0x07) Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-350">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_drbg_operation"></a><span data-ttu-id="e1337-351">_nx_crypto_method_drbg_operation</span><span class="sxs-lookup"><span data-stu-id="e1337-351">_nx_crypto_method_drbg_operation</span></span>

<span data-ttu-id="e1337-352">Executar operação DRBG</span><span class="sxs-lookup"><span data-stu-id="e1337-352">Perform DRBG operation</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-353">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-353">Prototype</span></span>

```c
UINT __nx_crypto_method_drbg_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="e1337-354">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-354">Description</span></span>

<span data-ttu-id="e1337-355">Esta função executa o funcionamento drbg.</span><span class="sxs-lookup"><span data-stu-id="e1337-355">This function performs DRBG operation.</span></span> <span data-ttu-id="e1337-356">O bloco de controlo DRBG deve ter sido inicializado com _ *nx_crypto_method_drbg_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-356">The DRBG control block must have been initialized with _ *nx_crypto_method_drbg_init()*.</span></span> <span data-ttu-id="e1337-357">O algoritmo DRBG a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*</span><span class="sxs-lookup"><span data-stu-id="e1337-357">The DRBG algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span> <span data-ttu-id="e1337-358">Por predefinição, o AES-128 é utilizado para a DRBG.</span><span class="sxs-lookup"><span data-stu-id="e1337-358">By default AES-128 is used for DRBG.</span></span>

<span data-ttu-id="e1337-359">Quando a operação é NX_CRYPTO_DRBG_OPTIONS_SET, a entrada aponta para NX_CRYPTO_DRBG_OPTIONS estrutura.</span><span class="sxs-lookup"><span data-stu-id="e1337-359">When the operation is NX_CRYPTO_DRBG_OPTIONS_SET, the input points to NX_CRYPTO_DRBG_OPTIONS structure.</span></span> <span data-ttu-id="e1337-360">Quando a operação é NX_CRYPTO_DRBG_INSTANTIATE, a chave aponta para nonce, a entrada aponta para a cadeia de personalização.</span><span class="sxs-lookup"><span data-stu-id="e1337-360">When the operation is NX_CRYPTO_DRBG_INSTANTIATE, the key points to nonce, input points to personalization string.</span></span> <span data-ttu-id="e1337-361">Quando a operação é NX_CRYPTO_DRBG_RESEED ou NX_CRYPTO_DRBG_GENERATE, a entrada aponta para uma entrada adicional.</span><span class="sxs-lookup"><span data-stu-id="e1337-361">When the operation is NX_CRYPTO_DRBG_RESEED or NX_CRYPTO_DRBG_GENERATE, the input points to additional input.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-362">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-362">Parameters</span></span>

- <span data-ttu-id="e1337-363">**op** Tipo de operação para realizar.</span><span class="sxs-lookup"><span data-stu-id="e1337-363">**op** Type of operation to perform.</span></span> <span data-ttu-id="e1337-364">A operação válida é:</span><span class="sxs-lookup"><span data-stu-id="e1337-364">Valid operation is:</span></span>
  - <span data-ttu-id="e1337-365">*NX_CRYPTO_DRBG_OPTIONS_SET*</span><span class="sxs-lookup"><span data-stu-id="e1337-365">*NX_CRYPTO_DRBG_OPTIONS_SET*</span></span>
  - <span data-ttu-id="e1337-366">*NX_CRYPTO_DRBG_INSTANTIATE*</span><span class="sxs-lookup"><span data-stu-id="e1337-366">*NX_CRYPTO_DRBG_INSTANTIATE*</span></span>
  - <span data-ttu-id="e1337-367">*NX_CRYPTO_DRBG_RESEED NX_CRYPTO_DRBG_GENERATE*</span><span class="sxs-lookup"><span data-stu-id="e1337-367">*NX_CRYPTO_DRBG_RESEED NX_CRYPTO_DRBG_GENERATE*</span></span>
- <span data-ttu-id="e1337-368">**cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-368">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-369">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-369">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-370">**método** Ponteiro para o método cripto DRBG válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-370">**method** Pointer to the valid DRBG crypto method.</span></span> <span data-ttu-id="e1337-371">O método cripto utilizado aqui deve ser o mesmo utilizado no _ *nx_crypto_method_drbg_init().*</span><span class="sxs-lookup"><span data-stu-id="e1337-371">The crypto method used here must be the same used in the _ *nx_crypto_method_drbg_init().*</span></span>
- <span data-ttu-id="e1337-372">**chave** Ponteiro para o nó para a operação instantânea.</span><span class="sxs-lookup"><span data-stu-id="e1337-372">**key** Pointer to the the nonce for the instantiate operation.</span></span> <span data-ttu-id="e1337-373">Este campo não é utilizado para outras operações.</span><span class="sxs-lookup"><span data-stu-id="e1337-373">This field is not used for other operations.</span></span>
- <span data-ttu-id="e1337-374">**key_size_in_bits** Tamanho do nonce, em pedaços.</span><span class="sxs-lookup"><span data-stu-id="e1337-374">**key_size_in_bits** Size of the nonce, in bits.</span></span> <span data-ttu-id="e1337-375">Este campo não é utilizado para outras operações.</span><span class="sxs-lookup"><span data-stu-id="e1337-375">This field is not used for other operations.</span></span>
- <span data-ttu-id="e1337-376">**entrada** Quando a operação é NX_CRYPTO_DRBG_OPTIONS_SET, este campo aponta para as opções de DRBG.</span><span class="sxs-lookup"><span data-stu-id="e1337-376">**input** When op is NX_CRYPTO_DRBG_OPTIONS_SET, this field points to DRBG options.</span></span> <span data-ttu-id="e1337-377">Quando a operação é NX_CRYPTO_DRBG_INSTANTIATE, este campo aponta para a cadeia de personalização.</span><span class="sxs-lookup"><span data-stu-id="e1337-377">When op is NX_CRYPTO_DRBG_INSTANTIATE, this field points to personalization string.</span></span> <span data-ttu-id="e1337-378">Quando a operação é NX_CRYPTO_DRBG_RESEED ou NX_CRYPTO_DRBG_GENERATE, este campo aponta para dados adicionais de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-378">When op is NX_CRYPTO_DRBG_RESEED or NX_CRYPTO_DRBG_GENERATE, this field points to additional input data.</span></span>
- <span data-ttu-id="e1337-379">**input_length_in_byte** Tamanho dos dados de entrada, bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-379">**input_length_in_byte** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="e1337-380">**iv_ptr** Este campo não é utilizado para a DRBG.</span><span class="sxs-lookup"><span data-stu-id="e1337-380">**iv_ptr** This field is not used for DRBG.</span></span>
- <span data-ttu-id="e1337-381">**saída** Quando a operação é NX_CRYPTO_DRBG_GENERATE, este campo aponta para a área de memória para o DRBG gerado.</span><span class="sxs-lookup"><span data-stu-id="e1337-381">**output** When op is NX_CRYPTO_DRBG_GENERATE, this field points to the memory area for the generated DRBG.</span></span> <span data-ttu-id="e1337-382">Caso contrário, este campo não é utilizado.</span><span class="sxs-lookup"><span data-stu-id="e1337-382">Otherwise, this field is not used.</span></span>
- <span data-ttu-id="e1337-383">**output_length_in_byte** Tamanho do tampão de saída em bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-383">**output_length_in_byte** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="e1337-384">**crypto_metadata** Ponteiro para o bloco de controlo DRBG utilizado em *_nx_crypto_method_drbg_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-384">**crypto_metadata** Pointer to the DRBG control block used in *_nx_crypto_method_drbg_init()*.</span></span>
- <span data-ttu-id="e1337-385">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-385">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-386">Para a DRBG, o tamanho dos metadados deve ser *do tamanho (NX_CRYPTO_DRBG)*</span><span class="sxs-lookup"><span data-stu-id="e1337-386">For DRBG, the metadata size must *sizeof(NX_CRYPTO_DRBG)*</span></span>
- <span data-ttu-id="e1337-387">**packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-387">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-388">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-388">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-389">**nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-389">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-390">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-390">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-391">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-391">Return Values</span></span>

- <span data-ttu-id="e1337-392">**NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação DRBG.</span><span class="sxs-lookup"><span data-stu-id="e1337-392">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the DRBG operation.</span></span>
- <span data-ttu-id="e1337-393">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-393">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-394">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.</span><span class="sxs-lookup"><span data-stu-id="e1337-394">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="e1337-395">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) algoritmo DRBG inválido sendo especificado.</span><span class="sxs-lookup"><span data-stu-id="e1337-395">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid DRBG algorithm being specified.</span></span>
- <span data-ttu-id="e1337-396">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamanho do tampão de saída inválido.</span><span class="sxs-lookup"><span data-stu-id="e1337-396">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_drbg_cleanup"></a><span data-ttu-id="e1337-397">_nx_crypto_method_drbg_cleanup</span><span class="sxs-lookup"><span data-stu-id="e1337-397">_nx_crypto_method_drbg_cleanup</span></span>

<span data-ttu-id="e1337-398">Limpe o bloco de controlo DRBG.</span><span class="sxs-lookup"><span data-stu-id="e1337-398">Clean up the DRBG control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-399">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-399">Prototype</span></span>

```c
UINT _nx_crypto_method_drbg_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="e1337-400">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-400">Description</span></span>

<span data-ttu-id="e1337-401">A aplicação chama a esta função para limpar o bloco de controlo DRBG depois de determinar que esta sessão de DRBG já não é necessária.</span><span class="sxs-lookup"><span data-stu-id="e1337-401">Application calls this function to clean up the DRBG control block after it determines this DRBG session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-402">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-402">Parameters</span></span>

- <span data-ttu-id="e1337-403">**crypto_metadata** Ponteiro para o bloco de controlo DRBG utilizado em *_nx_crypto_method_drbg_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-403">**crypto_metadata** Pointer to the DRBG control block used in *_nx_crypto_method_drbg_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-404">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-404">Return Values</span></span>

- <span data-ttu-id="e1337-405">**NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão de DRBG.</span><span class="sxs-lookup"><span data-stu-id="e1337-405">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the DRBG session.</span></span>
- <span data-ttu-id="e1337-406">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-406">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_ecdh_init"></a><span data-ttu-id="e1337-407">_nx_crypto_method_ecdh_init</span><span class="sxs-lookup"><span data-stu-id="e1337-407">_nx_crypto_method_ecdh_init</span></span>

<span data-ttu-id="e1337-408">Inicializa o bloco de controlo cripto do ECDH</span><span class="sxs-lookup"><span data-stu-id="e1337-408">Initializes the ECDH crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-409">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-409">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdh_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="e1337-410">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-410">Description</span></span>

<span data-ttu-id="e1337-411">Esta função inicializa o bloco de controlo ECDH com a corda de chave dada.</span><span class="sxs-lookup"><span data-stu-id="e1337-411">This function initializes the ECDH control block with the given key string.</span></span> <span data-ttu-id="e1337-412">Uma vez iniciada a inicial do bloco de controlo do ECDH, a operação subsequente do ECDH deve utilizar o mesmo bloco de controlo.</span><span class="sxs-lookup"><span data-stu-id="e1337-412">Once the ECDH control block is initialized, subsequent ECDH operation shall be using the same control block.</span></span>

<span data-ttu-id="e1337-413">A aplicação pode criar vários blocos de controlo ECDH, cada um representa uma sessão.</span><span class="sxs-lookup"><span data-stu-id="e1337-413">Application may create multiple ECDH control blocks, each represents a session.</span></span> <span data-ttu-id="e1337-414">A inicialização do bloco de controlo do ECDH inicia uma nova sessão de computação de haxixe.</span><span class="sxs-lookup"><span data-stu-id="e1337-414">Initializing the ECDH control block starts a new hash computation session.</span></span> <span data-ttu-id="e1337-415">A re-inicialização do bloco de controlo do ECDH abandona a sessão atual e protagoniza uma nova.</span><span class="sxs-lookup"><span data-stu-id="e1337-415">Re-initializing the ECDH control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-416">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-416">Parameters</span></span>

- <span data-ttu-id="e1337-417">**método** Ponteiro para um bloco de controlo de método cripto ECDH válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-417">**method** Pointer to a valid ECDH crypto method control block.</span></span> <span data-ttu-id="e1337-418">Estão disponíveis os seguintes métodos cripto pré-definidos:</span><span class="sxs-lookup"><span data-stu-id="e1337-418">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="e1337-419">*crypto_method_ecdh*</span><span class="sxs-lookup"><span data-stu-id="e1337-419">*crypto_method_ecdh*</span></span>
- <span data-ttu-id="e1337-420">**chave** Este campo não é usado para o ECDH.</span><span class="sxs-lookup"><span data-stu-id="e1337-420">**key** This field is not used for ECDH.</span></span>
- <span data-ttu-id="e1337-421">**key_size_in_bits** Este campo não é usado para o ECDH.</span><span class="sxs-lookup"><span data-stu-id="e1337-421">**key_size_in_bits** This field is not used for ECDH.</span></span>
- <span data-ttu-id="e1337-422">**cabo** Este serviço devolve uma manípula ao autor da chamada.</span><span class="sxs-lookup"><span data-stu-id="e1337-422">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="e1337-423">O cabo é dependente da implementação e não está a ser utilizado nesta implementação.</span><span class="sxs-lookup"><span data-stu-id="e1337-423">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="e1337-424">O pedido deve passar NU PARA o cabo.</span><span class="sxs-lookup"><span data-stu-id="e1337-424">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="e1337-425">**crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo ECDH.</span><span class="sxs-lookup"><span data-stu-id="e1337-425">**crypto_metadata** Pointer to a valid memory space for the ECDH control block.</span></span> <span data-ttu-id="e1337-426">O endereço inicial do espaço de memória deve estar alinhado a 4 byte.</span><span class="sxs-lookup"><span data-stu-id="e1337-426">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="e1337-427">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-427">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-428">Para o ECDH, o tamanho dos metadados deve ser *de tamanho (NX_CRYPTO_ECDH)*</span><span class="sxs-lookup"><span data-stu-id="e1337-428">For ECDH, the metadata size must be *sizeof(NX_CRYPTO_ECDH)*</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-429">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-429">Return Values</span></span>

- <span data-ttu-id="e1337-430">**NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo do ECDH com a chave e o tamanho da chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-430">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the ECDH control block with the key and key size.</span></span>
- <span data-ttu-id="e1337-431">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-431">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-432">**NX_PTR_ERROR** (0x07) Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-432">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_ecdh_operation"></a><span data-ttu-id="e1337-433">_nx_crypto_method_ecdh_operation</span><span class="sxs-lookup"><span data-stu-id="e1337-433">_nx_crypto_method_ecdh_operation</span></span>

<span data-ttu-id="e1337-434">Realizar operação ECDH</span><span class="sxs-lookup"><span data-stu-id="e1337-434">Perform ECDH operation</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-435">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-435">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdh_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="e1337-436">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-436">Description</span></span>

<span data-ttu-id="e1337-437">Esta função executa a operação ECDH.</span><span class="sxs-lookup"><span data-stu-id="e1337-437">This function performs ECDH operation.</span></span> <span data-ttu-id="e1337-438">O bloco de controlo do ECDH deve ter sido inicializado com _ *nx_crypto_method_ecdh_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-438">The ECDH control block must have been initialized with _ *nx_crypto_method_ecdh_init()*.</span></span> <span data-ttu-id="e1337-439">O algoritmo ECDH a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*</span><span class="sxs-lookup"><span data-stu-id="e1337-439">The ECDH algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="e1337-440">Quando a operação é NX_CRYPTO_EC_CURVE_SET, a entrada aponta para o método cripto da curva elíptica.</span><span class="sxs-lookup"><span data-stu-id="e1337-440">When the operation is NX_CRYPTO_EC_CURVE_SET, the input points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="e1337-441">Quando a operação é NX_CRYPTO_EC_KEY_PAIR_GENERATE, a saída aponta para NX_CRYPTO_EXTENDED_OUTPUT estrutura e o par de chaves é copiado para nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="e1337-441">When the operation is NX_CRYPTO_EC_KEY_PAIR_GENERATE, the output points to NX_CRYPTO_EXTENDED_OUTPUT structure and the key pair is copied to nx_crypto_extended_output_data.</span></span> <span data-ttu-id="e1337-442">Quando a operação é NX_CRYPTO_DH_SETUP, a chave pública é devolvida a nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="e1337-442">When the operation is NX_CRYPTO_DH_SETUP, the public key is returned to nx_crypto_extended_output_data.</span></span> <span data-ttu-id="e1337-443">Quando a operação é NX_CRYPTO_DH_KEY_PAIR_IMPORT, a entrada aponta para a chave pública e pontos-chave para a chave privada.</span><span class="sxs-lookup"><span data-stu-id="e1337-443">When the operation is NX_CRYPTO_DH_KEY_PAIR_IMPORT, the input points to public key and key points to private key.</span></span> <span data-ttu-id="e1337-444">Quando a operação é NX_CRYPTO_DH_PRIVATE_KEY_EXPORT, a chave privada é copiada para nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="e1337-444">When the operation is NX_CRYPTO_DH_PRIVATE_KEY_EXPORT, the private key is copied to nx_crypto_extended_output_data.</span></span> <span data-ttu-id="e1337-445">Quando a operação é NX_CRYPTO_DH_CALCULATE, a entrada aponta para a chave pública remota e o segredo partilhado é copiado para nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="e1337-445">When the operation is NX_CRYPTO_DH_CALCULATE, the input points to remote public key and the shared secret is copied to nx_crypto_extended_output_data.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-446">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-446">Parameters</span></span>

- <span data-ttu-id="e1337-447">**op** Tipo de operação para realizar.</span><span class="sxs-lookup"><span data-stu-id="e1337-447">**op** Type of operation to perform.</span></span> <span data-ttu-id="e1337-448">A operação válida é:</span><span class="sxs-lookup"><span data-stu-id="e1337-448">Valid operation is:</span></span>
  - <span data-ttu-id="e1337-449">*NX_CRYPTO_EC_CURVE_SET*</span><span class="sxs-lookup"><span data-stu-id="e1337-449">*NX_CRYPTO_EC_CURVE_SET*</span></span>
  - <span data-ttu-id="e1337-450">*NX_CRYPTO_DH_SETUP*</span><span class="sxs-lookup"><span data-stu-id="e1337-450">*NX_CRYPTO_DH_SETUP*</span></span>
  - <span data-ttu-id="e1337-451">*NX_CRYPTO_DH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="e1337-451">*NX_CRYPTO_DH_CALCULATE*</span></span>
  - <span data-ttu-id="e1337-452">*NX_CRYPTO_DH_KEY_PAIR_IMPOPRT*</span><span class="sxs-lookup"><span data-stu-id="e1337-452">*NX_CRYPTO_DH_KEY_PAIR_IMPOPRT*</span></span>
  - <span data-ttu-id="e1337-453">*NX_CRYPTO_DH_KEY_PAIR_GENERATE*</span><span class="sxs-lookup"><span data-stu-id="e1337-453">*NX_CRYPTO_DH_KEY_PAIR_GENERATE*</span></span>
  - <span data-ttu-id="e1337-454">*NX_CRYPTO_DH_PRIVATE_KEY_EXPORT*</span><span class="sxs-lookup"><span data-stu-id="e1337-454">*NX_CRYPTO_DH_PRIVATE_KEY_EXPORT*</span></span>
- <span data-ttu-id="e1337-455">**cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-455">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-456">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-456">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-457">**método** Ponteiro para o método cripto ECDH válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-457">**method** Pointer to the valid ECDH crypto method.</span></span> <span data-ttu-id="e1337-458">O método cripto utilizado aqui deve ser o mesmo utilizado no _ *nx_crypto_method_ecdh_init().*</span><span class="sxs-lookup"><span data-stu-id="e1337-458">The crypto method used here must be the same used in the _ *nx_crypto_method_ecdh_init().*</span></span>
- <span data-ttu-id="e1337-459">**chave** Quando a operação é NX_CRYPTO_DH_IMPORT_KEY_PAIR, este campo aponta para chave privada.</span><span class="sxs-lookup"><span data-stu-id="e1337-459">**key** When op is NX_CRYPTO_DH_IMPORT_KEY_PAIR, this field points to private key.</span></span> <span data-ttu-id="e1337-460">Caso contrário, este campo não é utilizado para o ECDH.</span><span class="sxs-lookup"><span data-stu-id="e1337-460">Otherwise, this field is not used for ECDH.</span></span>
- <span data-ttu-id="e1337-461">**key_size_in_bits** Tamanho da chave, em pedaços.</span><span class="sxs-lookup"><span data-stu-id="e1337-461">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="e1337-462">**entrada** Quando a operação é NX_CRYPTO_EC_CURVE_SET, este campo aponta para o método cripto da Curva Elíptica.</span><span class="sxs-lookup"><span data-stu-id="e1337-462">**input** When op is NX_CRYPTO_EC_CURVE_SET, this field points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="e1337-463">Quando a operação é NX_CRYPTO_DH_SETUP, este campo não é usado.</span><span class="sxs-lookup"><span data-stu-id="e1337-463">When op is NX_CRYPTO_DH_SETUP, this field is not used.</span></span> <span data-ttu-id="e1337-464">Quando a operação é NX_CRYPTO_DH_CALCULATE, este campo aponta para um tampão contendo dados de texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-464">When op is NX_CRYPTO_DH_CALCULATE, this field points to a buffer containing input text data.</span></span> <span data-ttu-id="e1337-465">Quando a operação é NX_CRYPTO_DH_IMPORT_KEY_PAIR, este campo aponta para a chave pública.</span><span class="sxs-lookup"><span data-stu-id="e1337-465">When op is NX_CRYPTO_DH_IMPORT_KEY_PAIR, this field points to public key.</span></span>
- <span data-ttu-id="e1337-466">**input_length_in_byte** Tamanho dos dados de entrada, bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-466">**input_length_in_byte** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="e1337-467">**iv_ptr** Este campo não é usado para o ECDH.</span><span class="sxs-lookup"><span data-stu-id="e1337-467">**iv_ptr** This field is not used for ECDH.</span></span>
- <span data-ttu-id="e1337-468">**saída** Quando a operação é NX_CRYPTO_EC_CURVE_SET ou NX_CRYPTO_DH_IMPORT_KEY_PAIR, este campo não é utilizado.</span><span class="sxs-lookup"><span data-stu-id="e1337-468">**output** When op is NX_CRYPTO_EC_CURVE_SET or NX_CRYPTO_DH_IMPORT_KEY_PAIR, this field is not used.</span></span> <span data-ttu-id="e1337-469">Quando a operação é NX_CRYPTO_DH_SETUP, este campo aponta para a área de memória para a chave pública gerada do ECDH.</span><span class="sxs-lookup"><span data-stu-id="e1337-469">When op is NX_CRYPTO_DH_SETUP, this field points to the memory area for the generated ECDH public key.</span></span> <span data-ttu-id="e1337-470">Quando a operação é NX_CRYPTO_DH_CALCULATE, este campo aponta para a área de memória para o segredo partilhado do ECDH gerado.</span><span class="sxs-lookup"><span data-stu-id="e1337-470">When op is NX_CRYPTO_DH_CALCULATE, this field points to the memory area for the generated ECDH shared secret.</span></span>
- <span data-ttu-id="e1337-471">**output_length_in_byte** Tamanho do tampão de saída em bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-471">**output_length_in_byte** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="e1337-472">**crypto_metadata** Ponteiro para o bloco de controlo do ECDH utilizado em *_nx_crypto_method_ecdh_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-472">**crypto_metadata** Pointer to the ECDH control block used in *_nx_crypto_method_ecdh_init()*.</span></span>
- <span data-ttu-id="e1337-473">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-473">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-474">Para o ECDH, o tamanho dos metadados deve ser *do tamanho (NX_CRYPTO_ECDH)*</span><span class="sxs-lookup"><span data-stu-id="e1337-474">For ECDH, the metadata size must *sizeof(NX_CRYPTO_ECDH)*</span></span>
- <span data-ttu-id="e1337-475">**packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-475">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-476">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-476">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-477">**nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-477">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-478">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-478">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-479">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-479">Return Values</span></span>

- <span data-ttu-id="e1337-480">**NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação ECDH.</span><span class="sxs-lookup"><span data-stu-id="e1337-480">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the ECDH operation.</span></span>
- <span data-ttu-id="e1337-481">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-481">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-482">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.</span><span class="sxs-lookup"><span data-stu-id="e1337-482">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="e1337-483">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Algoritmo ECDH inválido sendo especificado.</span><span class="sxs-lookup"><span data-stu-id="e1337-483">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid ECDH algorithm being specified.</span></span>
- <span data-ttu-id="e1337-484">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamanho do tampão de saída inválido.</span><span class="sxs-lookup"><span data-stu-id="e1337-484">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_ecdh_cleanup"></a><span data-ttu-id="e1337-485">_nx_crypto_method_ecdh_cleanup</span><span class="sxs-lookup"><span data-stu-id="e1337-485">_nx_crypto_method_ecdh_cleanup</span></span>

<span data-ttu-id="e1337-486">Limpe o bloco de controlo do ECDH.</span><span class="sxs-lookup"><span data-stu-id="e1337-486">Clean up the ECDH control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-487">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-487">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdh_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="e1337-488">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-488">Description</span></span>

<span data-ttu-id="e1337-489">A aplicação chama a esta função para limpar o bloco de controlo do ECDH depois de determinar que esta sessão do ECDH já não é necessária.</span><span class="sxs-lookup"><span data-stu-id="e1337-489">Application calls this function to clean up the ECDH control block after it determines this ECDH session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-490">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-490">Parameters</span></span>

- <span data-ttu-id="e1337-491">**crypto_metadata** Ponteiro para o bloco de controlo do ECDH utilizado em *_nx_crypto_method_ecdh_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-491">**crypto_metadata** Pointer to the ECDH control block used in *_nx_crypto_method_ecdh_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-492">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-492">Return Values</span></span>

- <span data-ttu-id="e1337-493">**NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão do ECDH.</span><span class="sxs-lookup"><span data-stu-id="e1337-493">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the ECDH session.</span></span>
- <span data-ttu-id="e1337-494">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-494">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_ecdsa_init"></a><span data-ttu-id="e1337-495">_nx_crypto_method_ecdsa_init</span><span class="sxs-lookup"><span data-stu-id="e1337-495">_nx_crypto_method_ecdsa_init</span></span>

<span data-ttu-id="e1337-496">Inicializa o bloco de controlo cripto do ECDSA</span><span class="sxs-lookup"><span data-stu-id="e1337-496">Initializes the ECDSA crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-497">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-497">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdsa_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="e1337-498">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-498">Description</span></span>

<span data-ttu-id="e1337-499">Esta função inicializa o bloco de controlo ECDSA com a corda de chave dada.</span><span class="sxs-lookup"><span data-stu-id="e1337-499">This function initializes the ECDSA control block with the given key string.</span></span> <span data-ttu-id="e1337-500">Uma vez iniciada a inicial do bloco de controlo ECDSA, a operação subsequente do ECDSA deve utilizar o mesmo bloco de controlo.</span><span class="sxs-lookup"><span data-stu-id="e1337-500">Once the ECDSA control block is initialized, subsequent ECDSA operation shall be using the same control block.</span></span>

<span data-ttu-id="e1337-501">A aplicação pode criar vários blocos de controlo ECDSA, cada um representa uma sessão.</span><span class="sxs-lookup"><span data-stu-id="e1337-501">Application may create multiple ECDSA control blocks, each represents a session.</span></span> <span data-ttu-id="e1337-502">A inicialização do bloco de controlo ECDSA inicia uma nova sessão de computação de haxixe.</span><span class="sxs-lookup"><span data-stu-id="e1337-502">Initializing the ECDSA control block starts a new hash computation session.</span></span> <span data-ttu-id="e1337-503">A re-inicialização do bloco de controlo do ECDSA abandona a sessão atual e protagoniza uma nova.</span><span class="sxs-lookup"><span data-stu-id="e1337-503">Re-initializing the ECDSA control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-504">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-504">Parameters</span></span>

- <span data-ttu-id="e1337-505">**método** Ponteiro para um bloco de controlo de método cripto ECDSA válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-505">**method** Pointer to a valid ECDSA crypto method control block.</span></span> <span data-ttu-id="e1337-506">Estão disponíveis os seguintes métodos cripto pré-definidos:</span><span class="sxs-lookup"><span data-stu-id="e1337-506">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="e1337-507">*crypto_method_ecdsa*</span><span class="sxs-lookup"><span data-stu-id="e1337-507">*crypto_method_ecdsa*</span></span>
- <span data-ttu-id="e1337-508">**chave** Este campo não é utilizado para o ECDSA.</span><span class="sxs-lookup"><span data-stu-id="e1337-508">**key** This field is not used for ECDSA.</span></span>
- <span data-ttu-id="e1337-509">**key_size_in_bits** Este campo não é utilizado para o ECDSA.</span><span class="sxs-lookup"><span data-stu-id="e1337-509">**key_size_in_bits** This field is not used for ECDSA.</span></span>
- <span data-ttu-id="e1337-510">**cabo** Este serviço devolve uma manípula ao autor da chamada.</span><span class="sxs-lookup"><span data-stu-id="e1337-510">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="e1337-511">O cabo é dependente da implementação e não está a ser utilizado nesta implementação.</span><span class="sxs-lookup"><span data-stu-id="e1337-511">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="e1337-512">O pedido deve passar NU PARA o cabo.</span><span class="sxs-lookup"><span data-stu-id="e1337-512">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="e1337-513">**crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo ECDSA.</span><span class="sxs-lookup"><span data-stu-id="e1337-513">**crypto_metadata** Pointer to a valid memory space for the ECDSA control block.</span></span> <span data-ttu-id="e1337-514">O endereço inicial do espaço de memória deve estar alinhado a 4 byte.</span><span class="sxs-lookup"><span data-stu-id="e1337-514">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="e1337-515">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-515">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-516">Para o ECDSA, o tamanho dos metadados deve ser *de tamanho (NX_CRYPTO_ECDSA)*</span><span class="sxs-lookup"><span data-stu-id="e1337-516">For ECDSA, the metadata size must be *sizeof(NX_CRYPTO_ECDSA)*</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-517">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-517">Return Values</span></span>

- <span data-ttu-id="e1337-518">**NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo ECDSA com a chave e o tamanho da chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-518">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the ECDSA control block with the key and key size.</span></span>
- <span data-ttu-id="e1337-519">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-519">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-520">**NX_PTR_ERROR** (0x07) Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-520">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_ecdsa_operation"></a><span data-ttu-id="e1337-521">_nx_crypto_method_ecdsa_operation</span><span class="sxs-lookup"><span data-stu-id="e1337-521">_nx_crypto_method_ecdsa_operation</span></span>

<span data-ttu-id="e1337-522">Realizar operação ECDSA</span><span class="sxs-lookup"><span data-stu-id="e1337-522">Perform ECDSA operation</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-523">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-523">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdsa_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="e1337-524">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-524">Description</span></span>

<span data-ttu-id="e1337-525">Esta função executa a operação ECDSA.</span><span class="sxs-lookup"><span data-stu-id="e1337-525">This function performs ECDSA operation.</span></span> <span data-ttu-id="e1337-526">O bloco de controlo ECDSA deve ter sido inicializado com _ *nx_crypto_method_ecdsa_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-526">The ECDSA control block must have been initialized with _ *nx_crypto_method_ecdsa_init()*.</span></span> <span data-ttu-id="e1337-527">O algoritmo ECDSA a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*</span><span class="sxs-lookup"><span data-stu-id="e1337-527">The ECDSA algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="e1337-528">Quando a operação é NX_CRYPTO_EC_CURVE_SET, a entrada aponta para o método cripto da curva elíptica.</span><span class="sxs-lookup"><span data-stu-id="e1337-528">When the operation is NX_CRYPTO_EC_CURVE_SET, the input points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="e1337-529">Quando a operação é NX_CRYPTO_EC_KEY_PAIR_GENERATE, a saída aponta para NX_CRYPTO_EXTENDED_OUTPUT estrutura e o par de chaves é copiado para nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="e1337-529">When the operation is NX_CRYPTO_EC_KEY_PAIR_GENERATE, the output points to NX_CRYPTO_EXTENDED_OUTPUT structure and the key pair is copied to nx_crypto_extended_output_data.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-530">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-530">Parameters</span></span>

- <span data-ttu-id="e1337-531">**op** Tipo de operação para realizar.</span><span class="sxs-lookup"><span data-stu-id="e1337-531">**op** Type of operation to perform.</span></span> <span data-ttu-id="e1337-532">A operação válida é:</span><span class="sxs-lookup"><span data-stu-id="e1337-532">Valid operation is:</span></span>
  - <span data-ttu-id="e1337-533">*NX_CRYPTO_EC_CURVE_SET*</span><span class="sxs-lookup"><span data-stu-id="e1337-533">*NX_CRYPTO_EC_CURVE_SET*</span></span>
  - <span data-ttu-id="e1337-534">*NX_CRYPTO_AUTHENTICATE*</span><span class="sxs-lookup"><span data-stu-id="e1337-534">*NX_CRYPTO_AUTHENTICATE*</span></span>
  - <span data-ttu-id="e1337-535">*NX_CRYPTO_VERIFY*</span><span class="sxs-lookup"><span data-stu-id="e1337-535">*NX_CRYPTO_VERIFY*</span></span>
- <span data-ttu-id="e1337-536">**cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-536">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-537">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-537">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-538">**método** Ponteiro para o método cripto ECDSA válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-538">**method** Pointer to the valid ECDSA crypto method.</span></span> <span data-ttu-id="e1337-539">O método cripto utilizado aqui deve ser o mesmo utilizado no _ *nx_crypto_method_ecdsa_init().*</span><span class="sxs-lookup"><span data-stu-id="e1337-539">The crypto method used here must be the same used in the _ *nx_crypto_method_ecdsa_init().*</span></span>
- <span data-ttu-id="e1337-540">**chave** Aponta para a chave quando a operação é NX_CRYPTO_VERIFY.</span><span class="sxs-lookup"><span data-stu-id="e1337-540">**key** Points to the key when op is NX_CRYPTO_VERIFY.</span></span> <span data-ttu-id="e1337-541">Não existem restrições ao tampão-chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-541">There are not restrictions on key buffer.</span></span> <span data-ttu-id="e1337-542">Este campo não é utilizado para outros valores de op.</span><span class="sxs-lookup"><span data-stu-id="e1337-542">This field is not used for other values of op.</span></span>
- <span data-ttu-id="e1337-543">**key_size_in_bits** Tamanho da chave, em pedaços.</span><span class="sxs-lookup"><span data-stu-id="e1337-543">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="e1337-544">**entrada** Quando a operação é NX_CRYPTO_EC_CURVE_SET, este campo aponta para o método cripto da Curva Elíptica.</span><span class="sxs-lookup"><span data-stu-id="e1337-544">**input** When op is NX_CRYPTO_EC_CURVE_SET, this field points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="e1337-545">Caso contrário, este campo aponta para um tampão que contém dados de texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-545">Otherwise, this field points to a buffer containing input text data.</span></span>
- <span data-ttu-id="e1337-546">**input_length_in_byte** Tamanho dos dados de entrada, bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-546">**input_length_in_byte** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="e1337-547">**iv_ptr** Este campo não é utilizado para o ECDSA.</span><span class="sxs-lookup"><span data-stu-id="e1337-547">**iv_ptr** This field is not used for ECDSA.</span></span>
- <span data-ttu-id="e1337-548">**saída** Quando a operação é NX_CRYPTO_EC_CURVE_SET, este campo não é usado.</span><span class="sxs-lookup"><span data-stu-id="e1337-548">**output** When op is NX_CRYPTO_EC_CURVE_SET, this field is not used.</span></span> <span data-ttu-id="e1337-549">Quando a operação é NX_CRYPTO_AUTHENTICATE, este campo aponta para a área de memória para a assinatura gerada do ECDSA.</span><span class="sxs-lookup"><span data-stu-id="e1337-549">When op is NX_CRYPTO_AUTHENTICATE, this field points to the memory area for the generated ECDSA signature.</span></span> <span data-ttu-id="e1337-550">Quando a operação é NX_CRYPTO_VERIFY, este campo aponta para a área de memória para a assinatura verificada do ECDSA.</span><span class="sxs-lookup"><span data-stu-id="e1337-550">When op is NX_CRYPTO_VERIFY, this field points to the memory area for the verified ECDSA signature.</span></span>
- <span data-ttu-id="e1337-551">**output_length_in_byte** Tamanho do tampão de saída em bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-551">**output_length_in_byte** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="e1337-552">**crypto_metadata** Ponteiro para o bloco de controlo ECDSA utilizado em *_nx_crypto_method_ecdsa_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-552">**crypto_metadata** Pointer to the ECDSA control block used in *_nx_crypto_method_ecdsa_init()*.</span></span>
- <span data-ttu-id="e1337-553">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-553">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-554">Para o ECDSA, o tamanho dos metadados deve ser *do tamanho (NX_CRYPTO_ECDSA)*</span><span class="sxs-lookup"><span data-stu-id="e1337-554">For ECDSA, the metadata size must *sizeof(NX_CRYPTO_ECDSA)*</span></span>
- <span data-ttu-id="e1337-555">**packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-555">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-556">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-556">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-557">**nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-557">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-558">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-558">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-559">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-559">Return Values</span></span>

- <span data-ttu-id="e1337-560">**NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação ECDSA.</span><span class="sxs-lookup"><span data-stu-id="e1337-560">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the ECDSA operation.</span></span>
- <span data-ttu-id="e1337-561">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-561">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-562">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.</span><span class="sxs-lookup"><span data-stu-id="e1337-562">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="e1337-563">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Algoritmo ECDSA inválido sendo especificado.</span><span class="sxs-lookup"><span data-stu-id="e1337-563">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid ECDSA algorithm being specified.</span></span>
- <span data-ttu-id="e1337-564">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamanho do tampão de saída inválido.</span><span class="sxs-lookup"><span data-stu-id="e1337-564">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_ecdsa_cleanup"></a><span data-ttu-id="e1337-565">_nx_crypto_method_ecdsa_cleanup</span><span class="sxs-lookup"><span data-stu-id="e1337-565">_nx_crypto_method_ecdsa_cleanup</span></span>

<span data-ttu-id="e1337-566">Limpe o bloco de controlo do ECDSA.</span><span class="sxs-lookup"><span data-stu-id="e1337-566">Clean up the ECDSA control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-567">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-567">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdsa_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="e1337-568">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-568">Description</span></span>

<span data-ttu-id="e1337-569">A aplicação chama a esta função para limpar o bloco de controlo ECDSA depois de determinar que esta sessão do ECDSA já não é necessária.</span><span class="sxs-lookup"><span data-stu-id="e1337-569">Application calls this function to clean up the ECDSA control block after it determines this ECDSA session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-570">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-570">Parameters</span></span>

- <span data-ttu-id="e1337-571">**crypto_metadata** Ponteiro para o bloco de controlo ECDSA utilizado em *_nx_crypto_method_ecdsa_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-571">**crypto_metadata** Pointer to the ECDSA control block used in *_nx_crypto_method_ecdsa_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-572">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-572">Return Values</span></span>

- <span data-ttu-id="e1337-573">**NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão do ECDSA.</span><span class="sxs-lookup"><span data-stu-id="e1337-573">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the ECDSA session.</span></span>
- <span data-ttu-id="e1337-574">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-574">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_hmac_md5_init"></a><span data-ttu-id="e1337-575">_nx_crypto_method_hmac_md5_init</span><span class="sxs-lookup"><span data-stu-id="e1337-575">_nx_crypto_method_hmac_md5_init</span></span>

<span data-ttu-id="e1337-576">Inicializa o bloco de controlo cripto MD5 HMAC MD5</span><span class="sxs-lookup"><span data-stu-id="e1337-576">Initializes the HMAC MD5 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-577">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-577">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="e1337-578">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-578">Description</span></span>

<span data-ttu-id="e1337-579">Esta função inicializa o bloco de controlo HMAC MD5 com a chave dada.</span><span class="sxs-lookup"><span data-stu-id="e1337-579">This function initializes the HMAC MD5 control block with the given key string.</span></span> <span data-ttu-id="e1337-580">Uma vez iniciada a inicialidade do bloco de controlo HMAC MD5, a operação subsequente do HMAC MD5 deve utilizar o mesmo bloco de comando.</span><span class="sxs-lookup"><span data-stu-id="e1337-580">Once the HMAC MD5 control block is initialized, subsequent HMAC MD5 operation shall be using the same control block.</span></span>

<span data-ttu-id="e1337-581">A aplicação pode criar vários blocos de controlo HMAC MD5, cada um representa uma sessão.</span><span class="sxs-lookup"><span data-stu-id="e1337-581">Application may create multiple HMAC MD5 control blocks, each represents a session.</span></span> <span data-ttu-id="e1337-582">A inicialização do bloco de controlo HMAC MD5 inicia uma nova sessão de computação de haxixe.</span><span class="sxs-lookup"><span data-stu-id="e1337-582">Initializing the HMAC MD5 control block starts a new hash computation session.</span></span> <span data-ttu-id="e1337-583">A re-inicialização do bloco de controlo HMAC MD5 abandona a sessão atual e protagoniza uma nova.</span><span class="sxs-lookup"><span data-stu-id="e1337-583">Re-initializing the HMAC MD5 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-584">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-584">Parameters</span></span>

- <span data-ttu-id="e1337-585">**método** Ponteiro para um bloco de controlo de método cripto MD5 válido HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="e1337-585">**method** Pointer to a valid HMAC MD5 crypto method control block.</span></span>
<span data-ttu-id="e1337-586">Estão disponíveis os seguintes métodos cripto pré-definidos:</span><span class="sxs-lookup"><span data-stu-id="e1337-586">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="e1337-587">*crypto_method_hmac_md5*</span><span class="sxs-lookup"><span data-stu-id="e1337-587">*crypto_method_hmac_md5*</span></span>
- <span data-ttu-id="e1337-588">**chave** Aponta para a chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-588">**key** Points to the key.</span></span> <span data-ttu-id="e1337-589">Não existem restrições ao tampão-chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-589">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="e1337-590">**key_size_in_bits** Tamanho da chave, em pedaços.</span><span class="sxs-lookup"><span data-stu-id="e1337-590">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="e1337-591">**cabo** Este serviço devolve uma manípula ao autor da chamada.</span><span class="sxs-lookup"><span data-stu-id="e1337-591">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="e1337-592">O cabo é dependente da implementação e não está a ser utilizado nesta implementação.</span><span class="sxs-lookup"><span data-stu-id="e1337-592">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="e1337-593">O pedido deve passar NU PARA o cabo.</span><span class="sxs-lookup"><span data-stu-id="e1337-593">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="e1337-594">**crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="e1337-594">**crypto_metadata** Pointer to a valid memory space for the HMAC MD5 control block.</span></span> <span data-ttu-id="e1337-595">O endereço inicial do espaço de memória deve estar alinhado a 4 byte.</span><span class="sxs-lookup"><span data-stu-id="e1337-595">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="e1337-596">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-596">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-597">Para o HMAC MD5, o tamanho dos metadados deve ser *de tamanho (NX_CRYPTO_MD5_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="e1337-597">For HMAC MD5, the metadata size must be *sizeof(NX_CRYPTO_MD5_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-598">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-598">Return Values</span></span>

- <span data-ttu-id="e1337-599">**NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo HMAC MD5 com a chave e o tamanho da chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-599">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC MD5 control block with the key and key size.</span></span>
- <span data-ttu-id="e1337-600">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-600">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-601">**NX_PTR_ERROR** (0x07) Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-601">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_md5_operation"></a><span data-ttu-id="e1337-602">_nx_crypto_method_hmac_md5_operation</span><span class="sxs-lookup"><span data-stu-id="e1337-602">_nx_crypto_method_hmac_md5_operation</span></span>

<span data-ttu-id="e1337-603">Efetuar uma operação de hash HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="e1337-603">Perform an HMAC MD5 hash operation.</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-604">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-604">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_md5_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="e1337-605">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-605">Description</span></span>

<span data-ttu-id="e1337-606">Esta função executa o funcionamento do hash HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="e1337-606">This function performs HMAC MD5 hash operation.</span></span> <span data-ttu-id="e1337-607">O bloco de controlo HMAC MD5 deve ter sido inicializado com _ *nx_crypto_method_hmac_md5_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-607">The HMAC MD5 control block must have been initialized with _ *nx_crypto_method_hmac_md5_init()*.</span></span> <span data-ttu-id="e1337-608">O algoritmo HMAC MD5 a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*</span><span class="sxs-lookup"><span data-stu-id="e1337-608">The HMAC MD5 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="e1337-609">Para a operação *de NX_CRYPTO_HASH_CALCULATE* final, o tamanho do tampão de saída deve ser de 16 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-609">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 16 bytes.</span></span>

<span data-ttu-id="e1337-610">Esta operação não guarda informações estatais e não altera o material chave no bloco de controlo HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="e1337-610">This operation does not keep state information, and does not alter the key material in the HMAC MD5 control block.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-611">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-611">Parameters</span></span>

- <span data-ttu-id="e1337-612">**op** Tipo de operação para realizar.</span><span class="sxs-lookup"><span data-stu-id="e1337-612">**op** Type of operation to perform.</span></span> <span data-ttu-id="e1337-613">A operação válida é:</span><span class="sxs-lookup"><span data-stu-id="e1337-613">Valid operation is:</span></span>
  - <span data-ttu-id="e1337-614">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="e1337-614">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="e1337-615">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="e1337-615">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="e1337-616">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="e1337-616">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="e1337-617">**cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-617">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-618">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-618">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-619">**método** Ponteiro para o método de cripto HMAC MD5 válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-619">**method** Pointer to the valid HMAC MD5 crypto method.</span></span> <span data-ttu-id="e1337-620">O método cripto utilizado aqui deve ser o mesmo utilizado no *nx_crypto_method_hmac_md5_init().*</span><span class="sxs-lookup"><span data-stu-id="e1337-620">The crypto method used here must be the same used in the *nx_crypto_method_hmac_md5_init().*</span></span>
- <span data-ttu-id="e1337-621">**chave** Aponta para a chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-621">**key** Points to the key.</span></span> <span data-ttu-id="e1337-622">Não existem restrições ao tampão-chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-622">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="e1337-623">**key_size_in_bits** Tamanho da chave, em pedaços.</span><span class="sxs-lookup"><span data-stu-id="e1337-623">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="e1337-624">**input_data** Aponta para um tampão que contém dados de texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-624">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="e1337-625">Não existem restrições ao tampão de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-625">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="e1337-626">**input_data_size** Tamanho dos dados de entrada, bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-626">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="e1337-627">**iv_ptr** Este campo não é utilizado para HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="e1337-627">**iv_ptr** This field is not used for HMAC MD5.</span></span>
- <span data-ttu-id="e1337-628">**iv_size** Este campo não é utilizado para HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="e1337-628">**iv_size** This field is not used for HMAC MD5.</span></span>
- <span data-ttu-id="e1337-629">**output_buffer** Ponteiro para a área de memória para o haxixe HMAC MD5 gerado.</span><span class="sxs-lookup"><span data-stu-id="e1337-629">**output_buffer** Pointer to the memory area for the generated HMAC MD5 hash.</span></span>
- <span data-ttu-id="e1337-630">**output_buffer_size** Tamanho do tampão de saída em bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-630">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="e1337-631">**crypto_metadata** Ponteiro para o bloco de controlo HMAC MD5 utilizado em *_nx_crypto_method_hmac_md5_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-631">**crypto_metadata** Pointer to the HMAC MD5 control block used in *_nx_crypto_method_hmac_md5_init()*.</span></span>
- <span data-ttu-id="e1337-632">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-632">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-633">Para o HMAC MD5, o tamanho dos metadados deve ser *do tamanho (NX_CRYPTO_MD5_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="e1337-633">For HMAC MD5, the metadata size must *sizeof(NX_CRYPTO_MD5_HMAC)*</span></span>
- <span data-ttu-id="e1337-634">**packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-634">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-635">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-635">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-636">**nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-636">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-637">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-637">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-638">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-638">Return Values</span></span>

- <span data-ttu-id="e1337-639">**NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="e1337-639">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC MD5 operation.</span></span>
- <span data-ttu-id="e1337-640">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-640">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-641">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.</span><span class="sxs-lookup"><span data-stu-id="e1337-641">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="e1337-642">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Algoritmo HMAC MD5 inválido sendo especificado.</span><span class="sxs-lookup"><span data-stu-id="e1337-642">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC MD5 algorithm being specified.</span></span>
- <span data-ttu-id="e1337-643">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamanho do tampão de saída inválido.</span><span class="sxs-lookup"><span data-stu-id="e1337-643">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha1_init"></a><span data-ttu-id="e1337-644">_nx_crypto_method_hmac_sha1_init</span><span class="sxs-lookup"><span data-stu-id="e1337-644">_nx_crypto_method_hmac_sha1_init</span></span>

<span data-ttu-id="e1337-645">Inicializa o bloco de controlo cripto HMAC SHA1</span><span class="sxs-lookup"><span data-stu-id="e1337-645">Initializes the HMAC SHA1 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-646">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-646">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="e1337-647">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-647">Description</span></span>

<span data-ttu-id="e1337-648">Esta função inicializa o bloco de controlo HMAC SHA1 com a chave dada.</span><span class="sxs-lookup"><span data-stu-id="e1337-648">This function initializes the HMAC SHA1 control block with the given key string.</span></span> <span data-ttu-id="e1337-649">Uma vez iniciada a inicialidade do bloco de comandoS HMAC SHA1, a operação subsequente do HMAC SHA1 deve utilizar o mesmo bloco de comando.</span><span class="sxs-lookup"><span data-stu-id="e1337-649">Once the HMAC SHA1 control block is initialized, subsequent HMAC SHA1 operation shall be using the same control block.</span></span>

<span data-ttu-id="e1337-650">A aplicação pode criar vários blocos de controlo HMAC SHA1, cada um representa uma sessão.</span><span class="sxs-lookup"><span data-stu-id="e1337-650">Application may create multiple HMAC SHA1 control blocks, each represents a session.</span></span> <span data-ttu-id="e1337-651">A inicialização do bloco de controlo HMAC SHA1 inicia uma nova sessão de computação de haxixe.</span><span class="sxs-lookup"><span data-stu-id="e1337-651">Initializing the HMAC SHA1 control block starts a new hash computation session.</span></span> <span data-ttu-id="e1337-652">A re-inicialização do bloco de controlo HMAC SHA1 abandona a sessão atual e protagoniza uma nova.</span><span class="sxs-lookup"><span data-stu-id="e1337-652">Re-initializing the HMAC SHA1 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-653">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-653">Parameters</span></span>

- <span data-ttu-id="e1337-654">**método** Ponteiro para um bloco de controlo de método cripto HMAC SHA1 válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-654">**method** Pointer to a valid HMAC SHA1 crypto method control block.</span></span> <span data-ttu-id="e1337-655">Estão disponíveis os seguintes métodos cripto pré-definidos:</span><span class="sxs-lookup"><span data-stu-id="e1337-655">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="e1337-656">*crypto_method_hmac_sha1*</span><span class="sxs-lookup"><span data-stu-id="e1337-656">*crypto_method_hmac_sha1*</span></span>
- <span data-ttu-id="e1337-657">**chave** Aponta para a chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-657">**key** Points to the key.</span></span> <span data-ttu-id="e1337-658">Não existem restrições ao tampão-chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-658">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="e1337-659">**key_size_in_bits** Tamanho da chave, em pedaços.</span><span class="sxs-lookup"><span data-stu-id="e1337-659">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="e1337-660">**cabo** Este serviço devolve uma manípula ao autor da chamada.</span><span class="sxs-lookup"><span data-stu-id="e1337-660">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="e1337-661">O cabo é dependente da implementação e não está a ser utilizado nesta implementação.</span><span class="sxs-lookup"><span data-stu-id="e1337-661">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="e1337-662">O pedido deve passar NU PARA o cabo.</span><span class="sxs-lookup"><span data-stu-id="e1337-662">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="e1337-663">**crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="e1337-663">**crypto_metadata** Pointer to a valid memory space for the HMAC SHA1 control block.</span></span> <span data-ttu-id="e1337-664">O endereço inicial do espaço de memória deve estar alinhado a 4 byte.</span><span class="sxs-lookup"><span data-stu-id="e1337-664">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="e1337-665">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-665">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-666">Para o HMAC SHA1, o tamanho dos metadados deve ser *de tamanho (NX_CRYPTO_SHA1_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="e1337-666">For HMAC SHA1, the metadata size must be *sizeof(NX_CRYPTO_SHA1_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-667">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-667">Return Values</span></span>

- <span data-ttu-id="e1337-668">**NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo HMAC SHA1 com a chave e o tamanho da chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-668">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC SHA1control block with the key and key size.</span></span>
- <span data-ttu-id="e1337-669">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-669">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-670">**NX_PTR_ERROR** (0x07) Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-670">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_sha1_operation"></a><span data-ttu-id="e1337-671">_nx_crypto_method_hmac_sha1_operation</span><span class="sxs-lookup"><span data-stu-id="e1337-671">_nx_crypto_method_hmac_sha1_operation</span></span>

<span data-ttu-id="e1337-672">Realizar a operação de haxixe HMAC SHA1</span><span class="sxs-lookup"><span data-stu-id="e1337-672">Perform HMAC SHA1 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-673">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-673">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha1_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="e1337-674">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-674">Description</span></span>

<span data-ttu-id="e1337-675">Esta função executa o funcionamento do hash HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="e1337-675">This function performs HMAC SHA1 hash operation.</span></span> <span data-ttu-id="e1337-676">O bloco de controlo HMAC SHA1 deve ter sido inicializado com _ *nx_crypto_method_hmac_sha1_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-676">The HMAC SHA1 control block must have been initialized with _ *nx_crypto_method_hmac_sha1_init()*.</span></span> <span data-ttu-id="e1337-677">O algoritmo HMAC SHA1 a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*</span><span class="sxs-lookup"><span data-stu-id="e1337-677">The HMAC SHA1 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="e1337-678">Para a operação *final NX_CRYPTO_HASH_CALCULATE,* o tamanho do tampão de saída deve ser de 20 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-678">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 20 bytes.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-679">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-679">Parameters</span></span>

- <span data-ttu-id="e1337-680">**op** Tipo de operação para realizar.</span><span class="sxs-lookup"><span data-stu-id="e1337-680">**op** Type of operation to perform.</span></span> <span data-ttu-id="e1337-681">A operação válida é:</span><span class="sxs-lookup"><span data-stu-id="e1337-681">Valid operation is:</span></span>
  - <span data-ttu-id="e1337-682">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="e1337-682">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="e1337-683">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="e1337-683">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="e1337-684">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="e1337-684">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="e1337-685">**cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-685">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-686">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-686">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-687">**método** Ponteiro para o método de cripto HMAC SHA1 válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-687">**method** Pointer to the valid HMAC SHA1 crypto method.</span></span> <span data-ttu-id="e1337-688">O método cripto utilizado aqui deve ser o mesmo utilizado no _ *nx_crypto_method_hmac_sha1_init().*</span><span class="sxs-lookup"><span data-stu-id="e1337-688">The crypto method used here must be the same used in the _ *nx_crypto_method_hmac_sha1_init().*</span></span>
- <span data-ttu-id="e1337-689">**chave** Aponta para a chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-689">**key** Points to the key.</span></span> <span data-ttu-id="e1337-690">Não existem restrições ao tampão-chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-690">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="e1337-691">**key_size_in_bits** Tamanho da chave, em pedaços.</span><span class="sxs-lookup"><span data-stu-id="e1337-691">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="e1337-692">**input_data** Aponta para um tampão que contém dados de texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-692">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="e1337-693">Não existem restrições ao tampão de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-693">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="e1337-694">**input_data_size** Tamanho dos dados de entrada, bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-694">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="e1337-695">**iv_ptr** Este campo não é utilizado para hmac SHA1.</span><span class="sxs-lookup"><span data-stu-id="e1337-695">**iv_ptr** This field is not used for HMAC SHA1.</span></span>
- <span data-ttu-id="e1337-696">**iv_size** Este campo não é utilizado para hmac SHA1.</span><span class="sxs-lookup"><span data-stu-id="e1337-696">**iv_size** This field is not used for HMAC SHA1.</span></span>
- <span data-ttu-id="e1337-697">**output_buffer** Ponteiro para a área de memória para o haxixe HMAC SHA1 gerado.</span><span class="sxs-lookup"><span data-stu-id="e1337-697">**output_buffer** Pointer to the memory area for the generated HMAC SHA1 hash.</span></span>
- <span data-ttu-id="e1337-698">**output_buffer_size** Tamanho do tampão de saída em bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-698">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="e1337-699">**crypto_metadata** Ponteiro para o bloco de controlo HMAC SHA1 utilizado em *_nx_crypto_method_hmac_sha1_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-699">**crypto_metadata** Pointer to the HMAC SHA1 control block used in *_nx_crypto_method_hmac_sha1_init()*.</span></span>
- <span data-ttu-id="e1337-700">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-700">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-701">Para o HMAC SHA1, o tamanho dos metadados deve ser *do tamanho (NX_CRYPTO_SHA1_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="e1337-701">For HMAC SHA1, the metadata size must *sizeof(NX_CRYPTO_SHA1_HMAC)*</span></span>
- <span data-ttu-id="e1337-702">**packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-702">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-703">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-703">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-704">**nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-704">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-705">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-705">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-706">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-706">Return Values</span></span>

- <span data-ttu-id="e1337-707">**NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="e1337-707">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC SHA1 operation.</span></span>
- <span data-ttu-id="e1337-708">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-708">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-709">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.</span><span class="sxs-lookup"><span data-stu-id="e1337-709">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="e1337-710">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Algoritmo HMAC SHA1 inválido sendo especificado.</span><span class="sxs-lookup"><span data-stu-id="e1337-710">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC SHA1 algorithm being specified.</span></span>
- <span data-ttu-id="e1337-711">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamanho do tampão de saída inválido.</span><span class="sxs-lookup"><span data-stu-id="e1337-711">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha1_cleanup"></a><span data-ttu-id="e1337-712">_nx_crypto_method_hmac_sha1_cleanup</span><span class="sxs-lookup"><span data-stu-id="e1337-712">_nx_crypto_method_hmac_sha1_cleanup</span></span>

<span data-ttu-id="e1337-713">Limpe o bloco de controlo HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="e1337-713">Clean up the HMAC SHA1 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-714">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-714">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="e1337-715">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-715">Description</span></span>

<span data-ttu-id="e1337-716">A aplicação chama a esta função para limpar o bloco de controlo HMAC SHA1 depois de determinar que esta sessão HMAC SHA1 já não é necessária.</span><span class="sxs-lookup"><span data-stu-id="e1337-716">Application calls this function to clean up the HMAC SHA1 control block after it determines this HMAC SHA1 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-717">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-717">Parameters</span></span>

- <span data-ttu-id="e1337-718">**crypto_metadata** Ponteiro para o bloco de controlo HMAC SHA1 utilizado em *_nx_crypto_method_hmac_sha1_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-718">**crypto_metadata** Pointer to the HMAC SHA1 control block used in *_nx_crypto_method_hmac_sha1_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-719">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-719">Return Values</span></span>

- <span data-ttu-id="e1337-720">**NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão HMAC SHA1.</span><span class="sxs-lookup"><span data-stu-id="e1337-720">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the HMAC SHA1 session.</span></span>
- <span data-ttu-id="e1337-721">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-721">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_hmac_sha256_init"></a><span data-ttu-id="e1337-722">_nx_crypto_method_hmac_sha256_init</span><span class="sxs-lookup"><span data-stu-id="e1337-722">_nx_crypto_method_hmac_sha256_init</span></span>

<span data-ttu-id="e1337-723">Inicializa o bloco de controlo cripto HMAC SHA256</span><span class="sxs-lookup"><span data-stu-id="e1337-723">Initializes the HMAC SHA256 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-724">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-724">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="e1337-725">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-725">Description</span></span>

<span data-ttu-id="e1337-726">Esta função inicializa o bloco de controlo HMAC SHA256 com a chave dada.</span><span class="sxs-lookup"><span data-stu-id="e1337-726">This function initializes the HMAC SHA256 control block with the given key string.</span></span> <span data-ttu-id="e1337-727">Uma vez iniciada a inicialidade do bloco de comando HMAC SHA256, a operação subsequente do HMAC SHA256 deve utilizar o mesmo bloco de comando.</span><span class="sxs-lookup"><span data-stu-id="e1337-727">Once the HMAC SHA256 control block is initialized, subsequent HMAC SHA256 operation shall be using the same control block.</span></span>

<span data-ttu-id="e1337-728">A aplicação pode criar vários blocos de controlo HMAC SHA256, cada um representa uma sessão.</span><span class="sxs-lookup"><span data-stu-id="e1337-728">Application may create multiple HMAC SHA256 control blocks, each represents a session.</span></span> <span data-ttu-id="e1337-729">A inicialização do bloco de controlo HMAC SH256 inicia uma nova sessão de computação de haxixe.</span><span class="sxs-lookup"><span data-stu-id="e1337-729">Initializing the HMAC SH256 control block starts a new hash computation session.</span></span> <span data-ttu-id="e1337-730">A re-inicialização do bloco de controlo HMAC SHA256 abandona a sessão atual e protagoniza uma nova com uma nova chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-730">Re-initializing the HMAC SHA256 control block abandons the current session and stars a new one with a new key.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-731">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-731">Parameters</span></span>

- <span data-ttu-id="e1337-732">**método** Ponteiro para um bloco de controlo de método cripto HMAC 256 válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-732">**method** Pointer to a valid HMAC SHA256 crypto method control block.</span></span> <span data-ttu-id="e1337-733">Estão disponíveis os seguintes métodos cripto pré-definidos:</span><span class="sxs-lookup"><span data-stu-id="e1337-733">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="e1337-734">*crypto_method_hmac_sha224*</span><span class="sxs-lookup"><span data-stu-id="e1337-734">*crypto_method_hmac_sha224*</span></span>
  - <span data-ttu-id="e1337-735">*crypto_method_hmac_sha256*</span><span class="sxs-lookup"><span data-stu-id="e1337-735">*crypto_method_hmac_sha256*</span></span>
- <span data-ttu-id="e1337-736">**chave** Aponta para a chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-736">**key** Points to the key.</span></span> <span data-ttu-id="e1337-737">Não existem restrições ao tampão-chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-737">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="e1337-738">**key_size_in_bits** Tamanho da chave, em pedaços.</span><span class="sxs-lookup"><span data-stu-id="e1337-738">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="e1337-739">**cabo** Este serviço devolve uma manípula ao autor da chamada.</span><span class="sxs-lookup"><span data-stu-id="e1337-739">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="e1337-740">O cabo é dependente da implementação e não está a ser utilizado nesta implementação.</span><span class="sxs-lookup"><span data-stu-id="e1337-740">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="e1337-741">O pedido deve passar NU PARA o cabo.</span><span class="sxs-lookup"><span data-stu-id="e1337-741">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="e1337-742">**crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="e1337-742">**crypto_metadata** Pointer to a valid memory space for the HMAC SHA256 control block.</span></span> <span data-ttu-id="e1337-743">O endereço inicial do espaço de memória deve estar alinhado a 4 byte.</span><span class="sxs-lookup"><span data-stu-id="e1337-743">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="e1337-744">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-744">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-745">Para o HMAC SHA256, o tamanho dos metadados deve ser *de tamanho (NX_CRYTPO_SHA256_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="e1337-745">For HMAC SHA256, the metadata size must be *sizeof(NX_CRYTPO_SHA256_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-746">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-746">Return Values</span></span>

- <span data-ttu-id="e1337-747">**NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo HMAC SHA256 com a chave e o tamanho da chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-747">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC SHA256 control block with the key and key size.</span></span>
- <span data-ttu-id="e1337-748">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-748">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-749">**NX_PTR_ERROR** (0x07) Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-749">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_sha256_operation"></a><span data-ttu-id="e1337-750">_nx_crypto_method_hmac_sha256_operation</span><span class="sxs-lookup"><span data-stu-id="e1337-750">_nx_crypto_method_hmac_sha256_operation</span></span>

<span data-ttu-id="e1337-751">Executar a operação de haxixe HMAC SHA256</span><span class="sxs-lookup"><span data-stu-id="e1337-751">Perform HMAC SHA256 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-752">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-752">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha256_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="e1337-753">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-753">Description</span></span>

<span data-ttu-id="e1337-754">Esta função executa o funcionamento do hash HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="e1337-754">This function performs HMAC SHA256 hash operation.</span></span> <span data-ttu-id="e1337-755">O bloco de controlo HMAC SHA256 deve ter sido inicializado com _ *nx_crypto_method_hmac_sha256_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-755">The HMAC SHA256 control block must have been initialized with _ *nx_crypto_method_hmac_sha256_init()*.</span></span> <span data-ttu-id="e1337-756">O algoritmo HMAC SHA256 a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*</span><span class="sxs-lookup"><span data-stu-id="e1337-756">The HMAC SHA256 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="e1337-757">Para a operação *de NX_CRYPTO_HASH_CALCULATE* final, o tamanho do tampão de saída deve ser de 32 bytes para SHA256, ou 28 bytes para SHA224.</span><span class="sxs-lookup"><span data-stu-id="e1337-757">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 32 bytes for SHA256, or 28 bytes for SHA224.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-758">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-758">Parameters</span></span>

- <span data-ttu-id="e1337-759">**op** Tipo de operação para realizar.</span><span class="sxs-lookup"><span data-stu-id="e1337-759">**op** Type of operation to perform.</span></span> <span data-ttu-id="e1337-760">A operação válida é:</span><span class="sxs-lookup"><span data-stu-id="e1337-760">Valid operation is:</span></span>
  - <span data-ttu-id="e1337-761">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="e1337-761">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="e1337-762">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="e1337-762">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="e1337-763">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="e1337-763">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="e1337-764">**cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-764">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-765">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-765">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-766">**método** Ponteiro para o método de cripto HMAC SHA256 válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-766">**method** Pointer to the valid HMAC SHA256 crypto method.</span></span> <span data-ttu-id="e1337-767">O método cripto utilizado aqui deve ser o mesmo utilizado no _ *nx_crypto_method_hmac_sha256_init().*</span><span class="sxs-lookup"><span data-stu-id="e1337-767">The crypto method used here must be the same used in the _ *nx_crypto_method_hmac_sha256_init().*</span></span>
- <span data-ttu-id="e1337-768">**chave** Aponta para a chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-768">**key** Points to the key.</span></span> <span data-ttu-id="e1337-769">Não existem restrições ao tampão-chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-769">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="e1337-770">**key_size_in_bits** Tamanho da chave, em pedaços.</span><span class="sxs-lookup"><span data-stu-id="e1337-770">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="e1337-771">**input_data** Aponta para um tampão que contém dados de texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-771">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="e1337-772">Não existem restrições ao tampão de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-772">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="e1337-773">**input_data_size** Tamanho dos dados de entrada, bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-773">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="e1337-774">**iv_ptr** Este campo não é utilizado para HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="e1337-774">**iv_ptr** This field is not used for HMAC SHA256.</span></span>
- <span data-ttu-id="e1337-775">**iv_size** Este campo não é utilizado para HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="e1337-775">**iv_size** This field is not used for HMAC SHA256.</span></span>
- <span data-ttu-id="e1337-776">**output_buffer** Ponteiro para a área de memória para o haxixe HMAC SHA256 gerado.</span><span class="sxs-lookup"><span data-stu-id="e1337-776">**output_buffer** Pointer to the memory area for the generated HMAC SHA256 hash.</span></span>
- <span data-ttu-id="e1337-777">**output_buffer_size** Tamanho do tampão de saída em bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-777">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="e1337-778">**crypto_metadata** Ponteiro para o bloco de controlo HMAC SHA256 utilizado em *_nx_crypto_method_hmac_sha256_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-778">**crypto_metadata** Pointer to the HMAC SHA256 control block used in *_nx_crypto_method_hmac_sha256_init()*.</span></span>
- <span data-ttu-id="e1337-779">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-779">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-780">Para o HMAC SHA256, o tamanho dos metadados deve ser *do tamanho (NX_CRYPTO_SHA256_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="e1337-780">For HMAC SHA256, the metadata size must *sizeof(NX_CRYPTO_SHA256_HMAC)*</span></span>
- <span data-ttu-id="e1337-781">**packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-781">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-782">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-782">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-783">**nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-783">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-784">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-784">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-785">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-785">Return Values</span></span>

- <span data-ttu-id="e1337-786">**NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="e1337-786">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC SHA256 operation.</span></span>
- <span data-ttu-id="e1337-787">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-787">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-788">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.</span><span class="sxs-lookup"><span data-stu-id="e1337-788">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="e1337-789">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Algoritmo HMAC SHA256 inválido sendo especificado.</span><span class="sxs-lookup"><span data-stu-id="e1337-789">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC SHA256 algorithm being specified.</span></span>
- <span data-ttu-id="e1337-790">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamanho do tampão de saída inválido.</span><span class="sxs-lookup"><span data-stu-id="e1337-790">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha256_cleanup"></a><span data-ttu-id="e1337-791">_nx_crypto_method_hmac_sha256_cleanup</span><span class="sxs-lookup"><span data-stu-id="e1337-791">_nx_crypto_method_hmac_sha256_cleanup</span></span>

<span data-ttu-id="e1337-792">Limpe o bloco de controlo HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="e1337-792">Clean up the HMAC SHA256 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-793">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-793">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="e1337-794">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-794">Description</span></span>

<span data-ttu-id="e1337-795">A aplicação chama a esta função para limpar o bloco de controlo HMAC SHA256 depois de determinar que esta sessão HMAC SHA256 já não é necessária.</span><span class="sxs-lookup"><span data-stu-id="e1337-795">Application calls this function to clean up the HMAC SHA256 control block after it determines this HMAC SHA256 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-796">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-796">Parameters</span></span>

- <span data-ttu-id="e1337-797">**crypto_metadata** Ponteiro para o bloco de controlo HMAC SHA256 utilizado em *_nx_crypto_method_hmac_sha256_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-797">**crypto_metadata** Pointer to the HMAC SHA256 control block used in *_nx_crypto_method_hmac_sha256_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-798">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-798">Return Values</span></span>

- <span data-ttu-id="e1337-799">**NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="e1337-799">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the HMAC SHA256 session.</span></span>
- <span data-ttu-id="e1337-800">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-800">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_hmac_sha512_init"></a><span data-ttu-id="e1337-801">_nx_crypto_method_hmac_sha512_init</span><span class="sxs-lookup"><span data-stu-id="e1337-801">_nx_crypto_method_hmac_sha512_init</span></span>

<span data-ttu-id="e1337-802">Inicializa o bloco de controlo cripto HMAC SHA512</span><span class="sxs-lookup"><span data-stu-id="e1337-802">Initializes the HMAC SHA512 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-803">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-803">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="e1337-804">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-804">Description</span></span>

<span data-ttu-id="e1337-805">Esta função inicializa o bloco de controlo HMAC SHA512 com a chave dada.</span><span class="sxs-lookup"><span data-stu-id="e1337-805">This function initializes the HMAC SHA512 control block with the given key string.</span></span> <span data-ttu-id="e1337-806">Uma vez iniciada a inicialidade do bloco de comandoS HMAC SHA512, a operação subsequente do HMAC SHA512 deve utilizar o mesmo bloco de comando.</span><span class="sxs-lookup"><span data-stu-id="e1337-806">Once the HMAC SHA512 control block is initialized, subsequent HMAC SHA512 operation shall be using the same control block.</span></span>

<span data-ttu-id="e1337-807">A aplicação pode criar vários blocos de controlo HMAC SHA512, cada um representa uma sessão.</span><span class="sxs-lookup"><span data-stu-id="e1337-807">Application may create multiple HMAC SHA512 control blocks, each represents a session.</span></span> <span data-ttu-id="e1337-808">A inicialização do bloco de controlo HMAC SH512 inicia uma nova sessão de computação de haxixe.</span><span class="sxs-lookup"><span data-stu-id="e1337-808">Initializing the HMAC SH512 control block starts a new hash computation session.</span></span> <span data-ttu-id="e1337-809">A re-inicialização do bloco de controlo HMAC SHA512 abandona a sessão atual e protagoniza uma nova com uma nova chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-809">Re-initializing the HMAC SHA512 control block abandons the current session and stars a new one with a new key.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-810">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-810">Parameters</span></span>

- <span data-ttu-id="e1337-811">**método** Ponteiro para um bloco de controlo de método cripto HMAC SHA512 válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-811">**method** Pointer to a valid HMAC SHA512 crypto method control block.</span></span> <span data-ttu-id="e1337-812">Estão disponíveis os seguintes métodos cripto pré-definidos:</span><span class="sxs-lookup"><span data-stu-id="e1337-812">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="e1337-813">*crypto_method_hmac_sha384*</span><span class="sxs-lookup"><span data-stu-id="e1337-813">*crypto_method_hmac_sha384*</span></span>
  - <span data-ttu-id="e1337-814">*crypto_method_hmac_sha512*</span><span class="sxs-lookup"><span data-stu-id="e1337-814">*crypto_method_hmac_sha512*</span></span>
- <span data-ttu-id="e1337-815">**chave** Aponta para a chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-815">**key** Points to the key.</span></span> <span data-ttu-id="e1337-816">Não existem restrições ao tampão-chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-816">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="e1337-817">**key_size_in_bits** Tamanho da chave, em pedaços.</span><span class="sxs-lookup"><span data-stu-id="e1337-817">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="e1337-818">**cabo** Este serviço devolve uma manípula ao autor da chamada.</span><span class="sxs-lookup"><span data-stu-id="e1337-818">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="e1337-819">O cabo é dependente da implementação e não está a ser utilizado nesta implementação.</span><span class="sxs-lookup"><span data-stu-id="e1337-819">The handle is implementation-dependent, and is not being used in this implementation.</span></span> <span data-ttu-id="e1337-820">O pedido deve passar NU PARA o cabo.</span><span class="sxs-lookup"><span data-stu-id="e1337-820">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="e1337-821">**crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="e1337-821">**crypto_metadata** Pointer to a valid memory space for the HMAC SHA512 control block.</span></span> <span data-ttu-id="e1337-822">O endereço inicial do espaço de memória deve estar alinhado a 4 byte.</span><span class="sxs-lookup"><span data-stu-id="e1337-822">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="e1337-823">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-823">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-824">Para o HMAC SHA512, o tamanho dos metadados deve ser *de tamanho (NX_CRYPTO_SHA512_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="e1337-824">For HMAC SHA512, the metadata size must be *sizeof(NX_CRYPTO_SHA512_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-825">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-825">Return Values</span></span>

- <span data-ttu-id="e1337-826">**NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo HMAC SHA512 com a chave e o tamanho da chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-826">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC SHA512 control block with the key and key size.</span></span>
- <span data-ttu-id="e1337-827">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-827">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-828">**NX_PTR_ERROR** (0x07) Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-828">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_sha512_operation"></a><span data-ttu-id="e1337-829">_nx_crypto_method_hmac_sha512_operation</span><span class="sxs-lookup"><span data-stu-id="e1337-829">_nx_crypto_method_hmac_sha512_operation</span></span>

<span data-ttu-id="e1337-830">Executar a operação de haxixe HMAC SHA512</span><span class="sxs-lookup"><span data-stu-id="e1337-830">Perform HMAC SHA512 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-831">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-831">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha512_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="e1337-832">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-832">Description</span></span>

<span data-ttu-id="e1337-833">Esta função executa o funcionamento do hash HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="e1337-833">This function performs HMAC SHA512 hash operation.</span></span> <span data-ttu-id="e1337-834">O bloco de controlo HMAC SHA512 deve ter sido inicializado com _ *nx_crypto_method_hmac_sha512_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-834">The HMAC SHA512 control block must have been initialized with _ *nx_crypto_method_hmac_sha512_init()*.</span></span> <span data-ttu-id="e1337-835">O algoritmo HMAC SHA512 a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*</span><span class="sxs-lookup"><span data-stu-id="e1337-835">The HMAC SHA512 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="e1337-836">Para a operação *de NX_CRYPTO_HASH_CALCULATE* final, o tamanho do tampão de saída deve ser de 64 bytes para SHA512, ou 48 bytes para SHA384.</span><span class="sxs-lookup"><span data-stu-id="e1337-836">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 64 bytes for SHA512, or 48 bytes for SHA384.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-837">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-837">Parameters</span></span>

- <span data-ttu-id="e1337-838">**op** Tipo de operação para realizar.</span><span class="sxs-lookup"><span data-stu-id="e1337-838">**op** Type of operation to perform.</span></span> <span data-ttu-id="e1337-839">A operação válida é:</span><span class="sxs-lookup"><span data-stu-id="e1337-839">Valid operation is:</span></span>
  - <span data-ttu-id="e1337-840">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="e1337-840">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="e1337-841">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="e1337-841">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="e1337-842">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="e1337-842">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="e1337-843">**cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-843">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-844">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-844">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-845">**método** Ponteiro para o método de cripto HMAC SHA512 válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-845">**method** Pointer to the valid HMAC SHA512 crypto method.</span></span> <span data-ttu-id="e1337-846">O método cripto utilizado aqui deve ser o mesmo utilizado no _ *nx_crypto_method_hmac_sha512_init().*</span><span class="sxs-lookup"><span data-stu-id="e1337-846">The crypto method used here must be the same used in the _ *nx_crypto_method_hmac_sha512_init().*</span></span>
- <span data-ttu-id="e1337-847">**chave** Aponta para a chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-847">**key** Points to the key.</span></span> <span data-ttu-id="e1337-848">Não existem restrições ao tampão-chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-848">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="e1337-849">**key_size_in_bits** Tamanho da chave, em pedaços.</span><span class="sxs-lookup"><span data-stu-id="e1337-849">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="e1337-850">**input_data** Aponta para um tampão que contém dados de texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-850">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="e1337-851">Não existem restrições ao tampão de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-851">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="e1337-852">**input_data_size** Tamanho dos dados de entrada, bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-852">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="e1337-853">**iv_ptr** Este campo não é utilizado para hmac SHA512.</span><span class="sxs-lookup"><span data-stu-id="e1337-853">**iv_ptr** This field is not used for HMAC SHA512.</span></span>
- <span data-ttu-id="e1337-854">**iv_size** Este campo não é utilizado para hmac SHA512.</span><span class="sxs-lookup"><span data-stu-id="e1337-854">**iv_size** This field is not used for HMAC SHA512.</span></span>
- <span data-ttu-id="e1337-855">**output_buffer** Ponteiro para a área de memória para o haxixe HMAC SHA512 gerado.</span><span class="sxs-lookup"><span data-stu-id="e1337-855">**output_buffer** Pointer to the memory area for the generated HMAC SHA512 hash.</span></span>
- <span data-ttu-id="e1337-856">**output_buffer_size** Tamanho do tampão de saída em bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-856">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="e1337-857">**crypto_metadata** Ponteiro para o bloco de controlo HMAC SHA512 utilizado em *_nx_crypto_method_hmac_sha512_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-857">**crypto_metadata** Pointer to the HMAC SHA512 control block used in *_nx_crypto_method_hmac_sha512_init()*.</span></span>
- <span data-ttu-id="e1337-858">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-858">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-859">Para o HMAC SHA512, o tamanho dos metadados deve ser *do tamanho (NX_CRYPTO_SHA512_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="e1337-859">For HMAC SHA512, the metadata size must *sizeof(NX_CRYPTO_SHA512_HMAC)*</span></span>
- <span data-ttu-id="e1337-860">**packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-860">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-861">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-861">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-862">**nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-862">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-863">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-863">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-864">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-864">Return Values</span></span>

- <span data-ttu-id="e1337-865">**NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="e1337-865">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC SHA512 operation.</span></span>
- <span data-ttu-id="e1337-866">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-866">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-867">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.</span><span class="sxs-lookup"><span data-stu-id="e1337-867">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="e1337-868">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Algoritmo HMAC SHA512 inválido sendo especificado.</span><span class="sxs-lookup"><span data-stu-id="e1337-868">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC SHA512 algorithm being specified.</span></span>
- <span data-ttu-id="e1337-869">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamanho do tampão de saída inválido.</span><span class="sxs-lookup"><span data-stu-id="e1337-869">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha512_cleanup"></a><span data-ttu-id="e1337-870">_nx_crypto_method_hmac_sha512_cleanup</span><span class="sxs-lookup"><span data-stu-id="e1337-870">_nx_crypto_method_hmac_sha512_cleanup</span></span>

<span data-ttu-id="e1337-871">Limpe o bloco de controlo HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="e1337-871">Clean up the HMAC SHA512 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-872">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-872">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="e1337-873">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-873">Description</span></span>

<span data-ttu-id="e1337-874">A aplicação chama a esta função para limpar o bloco de controlo HMAC SHA512 depois de determinar que esta sessão HMAC SHA512 já não é necessária.</span><span class="sxs-lookup"><span data-stu-id="e1337-874">Application calls this function to clean up the HMAC SHA512 control block after it determines this HMAC SHA512 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-875">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-875">Parameters</span></span>

- <span data-ttu-id="e1337-876">**crypto_metadata** Ponteiro para o bloco de controlo HMAC SHA512 utilizado em *_nx_crypto_method_hmac_sha512_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-876">**crypto_metadata** Pointer to the HMAC SHA512 control block used in *_nx_crypto_method_hmac_sha512_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-877">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-877">Return Values</span></span>

- <span data-ttu-id="e1337-878">**NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="e1337-878">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the HMAC SHA512 session.</span></span>
- <span data-ttu-id="e1337-879">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-879">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

### <a name="example"></a><span data-ttu-id="e1337-880">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1337-880">Example</span></span> 

## <a name="_nx_crypto_method_md5_init"></a><span data-ttu-id="e1337-881">_nx_crypto_method_md5_init</span><span class="sxs-lookup"><span data-stu-id="e1337-881">_nx_crypto_method_md5_init</span></span>

<span data-ttu-id="e1337-882">Inicializa o bloco de controlo cripto MD5</span><span class="sxs-lookup"><span data-stu-id="e1337-882">Initializes the MD5 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-883">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-883">Prototype</span></span>

```c
UINT _nx_crypto_method_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="e1337-884">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-884">Description</span></span>

<span data-ttu-id="e1337-885">Esta função inicializa o bloco de controlo MD5 com a chave dada.</span><span class="sxs-lookup"><span data-stu-id="e1337-885">This function initializes the MD5 control block with the given key string.</span></span> <span data-ttu-id="e1337-886">Uma vez iniciada a inicial do bloco de controlo MD5, a operação MD5 subsequente deve utilizar o mesmo bloco de comando.</span><span class="sxs-lookup"><span data-stu-id="e1337-886">Once the MD5 control block is initialized, subsequent MD5 operation shall be using the same control block.</span></span>

<span data-ttu-id="e1337-887">A aplicação pode criar vários blocos de controlo MD5, cada um representa uma sessão.</span><span class="sxs-lookup"><span data-stu-id="e1337-887">Application may create multiple MD5 control blocks, each represents a session.</span></span> <span data-ttu-id="e1337-888">A inicialização do bloco de controlo MD5 inicia uma nova sessão de computação de haxixe.</span><span class="sxs-lookup"><span data-stu-id="e1337-888">Initializing the MD5 control block starts a new hash computation session.</span></span> <span data-ttu-id="e1337-889">A re-inicialização do bloco de controlo MD5 abandona a sessão atual e protagoniza uma nova.</span><span class="sxs-lookup"><span data-stu-id="e1337-889">Re-initializing the MD5 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-890">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-890">Parameters</span></span>

- <span data-ttu-id="e1337-891">**método** Ponteiro para um bloco de controlo de método cripto MD5 válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-891">**method** Pointer to a valid MD5 crypto method control block.</span></span> <span data-ttu-id="e1337-892">Estão disponíveis os seguintes métodos cripto pré-definidos:</span><span class="sxs-lookup"><span data-stu-id="e1337-892">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="e1337-893">*crypto_method_md5*</span><span class="sxs-lookup"><span data-stu-id="e1337-893">*crypto_method_md5*</span></span>
- <span data-ttu-id="e1337-894">**chave** Este campo não é utilizado para MD5.</span><span class="sxs-lookup"><span data-stu-id="e1337-894">**key** This field is not used for MD5.</span></span>
- <span data-ttu-id="e1337-895">**key_size_in_bits** Este campo não é usado para MD5</span><span class="sxs-lookup"><span data-stu-id="e1337-895">**key_size_in_bits** This field is not used for MD5</span></span>
- <span data-ttu-id="e1337-896">**cabo** Este serviço devolve uma manípula ao autor da chamada.</span><span class="sxs-lookup"><span data-stu-id="e1337-896">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="e1337-897">O cabo é dependente da implementação e não está a ser utilizado nesta implementação.</span><span class="sxs-lookup"><span data-stu-id="e1337-897">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="e1337-898">O pedido deve passar NU PARA o cabo.</span><span class="sxs-lookup"><span data-stu-id="e1337-898">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="e1337-899">**crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo MD5.</span><span class="sxs-lookup"><span data-stu-id="e1337-899">**crypto_metadata** Pointer to a valid memory space for the MD5 control block.</span></span> <span data-ttu-id="e1337-900">O endereço inicial do espaço de memória deve estar alinhado a 4 byte.</span><span class="sxs-lookup"><span data-stu-id="e1337-900">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="e1337-901">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-901">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-902">Para mD5, o tamanho dos metadados deve ser *de tamanho (NX_CRYPTO_MD5)*</span><span class="sxs-lookup"><span data-stu-id="e1337-902">For MD5, the metadata size must be *sizeof(NX_CRYPTO_MD5)*</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-903">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-903">Return Values</span></span>

- <span data-ttu-id="e1337-904">**NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo MD5 com a chave e o tamanho da chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-904">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the MD5 control block with the key and key size.</span></span>
- <span data-ttu-id="e1337-905">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-905">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-906">**NX_PTR_ERROR** (0x07) Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-906">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

### <a name="example"></a><span data-ttu-id="e1337-907">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1337-907">Example</span></span>

## <a name="_nx_crypto_method_md5_operation"></a><span data-ttu-id="e1337-908">_nx_crypto_method_md5_operation</span><span class="sxs-lookup"><span data-stu-id="e1337-908">_nx_crypto_method_md5_operation</span></span>

<span data-ttu-id="e1337-909">Efetuar uma operação de haxixe MD5.</span><span class="sxs-lookup"><span data-stu-id="e1337-909">Perform an MD5 hash operation.</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-910">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-910">Prototype</span></span>

```c
UINT _nx_crypto_method_md5_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="e1337-911">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-911">Description</span></span>

<span data-ttu-id="e1337-912">Esta função executa o funcionamento do hash MD5.</span><span class="sxs-lookup"><span data-stu-id="e1337-912">This function performs MD5 hash operation.</span></span> <span data-ttu-id="e1337-913">O bloco de controlo MD5 deve ter sido inicializado com _ *nx_crypto_method_md5_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-913">The MD5 control block must have been initialized with _ *nx_crypto_method_md5_init()*.</span></span> <span data-ttu-id="e1337-914">O algoritmo MD5 a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*</span><span class="sxs-lookup"><span data-stu-id="e1337-914">The MD5 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="e1337-915">Para a operação *de NX_CRYPTO_HASH_CALCULATE* final, o tamanho do tampão de saída deve ser de 16 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-915">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 16 bytes.</span></span>

<span data-ttu-id="e1337-916">Esta operação não guarda informações estatais e não altera o material chave no bloco de comandoS MD5.</span><span class="sxs-lookup"><span data-stu-id="e1337-916">This operation does not keep state information and does not alter the key material in the MD5 control block.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-917">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-917">Parameters</span></span>

- <span data-ttu-id="e1337-918">**op** Tipo de operação para realizar.</span><span class="sxs-lookup"><span data-stu-id="e1337-918">**op** Type of operation to perform.</span></span> <span data-ttu-id="e1337-919">A operação válida é:</span><span class="sxs-lookup"><span data-stu-id="e1337-919">Valid operation is:</span></span>
  - <span data-ttu-id="e1337-920">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="e1337-920">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="e1337-921">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="e1337-921">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="e1337-922">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="e1337-922">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="e1337-923">**cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-923">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-924">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-924">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-925">**método** Ponteiro para o método de cripto MD5 válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-925">**method** Pointer to the valid MD5 crypto method.</span></span> <span data-ttu-id="e1337-926">O método cripto utilizado aqui deve ser o mesmo utilizado no _ *nx_crypto_method_md5_init().*</span><span class="sxs-lookup"><span data-stu-id="e1337-926">The crypto method used here must be the same used in the _ *nx_crypto_method_md5_init().*</span></span>
- <span data-ttu-id="e1337-927">**input_data** Aponta para um tampão que contém dados de texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-927">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="e1337-928">Não existem restrições ao tampão de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-928">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="e1337-929">**input_data_size** Tamanho dos dados de entrada, bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-929">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="e1337-930">**iv_ptr** Este campo não é utilizado para MD5.</span><span class="sxs-lookup"><span data-stu-id="e1337-930">**iv_ptr** This field is not used for MD5.</span></span>
- <span data-ttu-id="e1337-931">**iv_size** Este campo não é utilizado para MD5.</span><span class="sxs-lookup"><span data-stu-id="e1337-931">**iv_size** This field is not used for MD5.</span></span>
- <span data-ttu-id="e1337-932">**output_buffer** Ponteiro para a área de memória para o hash MD5 gerado.</span><span class="sxs-lookup"><span data-stu-id="e1337-932">**output_buffer** Pointer to the memory area for the generated MD5 hash.</span></span>
- <span data-ttu-id="e1337-933">**output_buffer_size** Tamanho do tampão de saída em bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-933">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="e1337-934">Para MD5 o tamanho do tampão deve ser de 16 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-934">For MD5 the buffer size must be 16 bytes.</span></span>
- <span data-ttu-id="e1337-935">**crypto_metadata** Ponteiro para o bloco de controlo MD5 utilizado em *_nx_crypto_method_md5_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-935">**crypto_metadata** Pointer to the MD5 control block used in *_nx_crypto_method_md5_init()*.</span></span>
- <span data-ttu-id="e1337-936">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-936">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-937">Para mD5, o tamanho dos metadados deve *ser do tamanho (NX_CRYPTO_MD5)*</span><span class="sxs-lookup"><span data-stu-id="e1337-937">For MD5, the metadata size must *sizeof(NX_CRYPTO_MD5)*</span></span>
- <span data-ttu-id="e1337-938">**packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-938">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-939">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-939">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-940">**nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-940">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-941">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-941">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-942">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-942">Return Values</span></span>

- <span data-ttu-id="e1337-943">**NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação MD5.</span><span class="sxs-lookup"><span data-stu-id="e1337-943">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the MD5 operation.</span></span>
- <span data-ttu-id="e1337-944">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-944">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-945">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.</span><span class="sxs-lookup"><span data-stu-id="e1337-945">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="e1337-946">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) algoritmo MD5 inválido sendo especificado.</span><span class="sxs-lookup"><span data-stu-id="e1337-946">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid MD5 algorithm being specified.</span></span>
- <span data-ttu-id="e1337-947">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamanho do tampão de saída inválido.</span><span class="sxs-lookup"><span data-stu-id="e1337-947">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_md5_cleanup"></a><span data-ttu-id="e1337-948">_nx_crypto_method_md5_cleanup</span><span class="sxs-lookup"><span data-stu-id="e1337-948">_nx_crypto_method_md5_cleanup</span></span>

<span data-ttu-id="e1337-949">Limpe o bloco de controlo MD5.</span><span class="sxs-lookup"><span data-stu-id="e1337-949">Clean up the MD5 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-950">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-950">Prototype</span></span>

```c
UINT _nx_crypto_method_md5_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="e1337-951">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-951">Description</span></span>

<span data-ttu-id="e1337-952">A aplicação chama esta função para limpar o bloco de controlo MD5 depois de determinar que esta sessão MD5 já não é necessária.</span><span class="sxs-lookup"><span data-stu-id="e1337-952">Application calls this function to clean up the MD5 control block after it determines this MD5 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-953">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-953">Parameters</span></span>

- <span data-ttu-id="e1337-954">**crypto_metadata** Ponteiro para o bloco de controlo MD5 utilizado em *_nx_crypto_method_md5_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-954">**crypto_metadata** Pointer to the MD5 control block used in *_nx_crypto_method_md5_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-955">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-955">Return Values</span></span>

- <span data-ttu-id="e1337-956">**NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão MD5.</span><span class="sxs-lookup"><span data-stu-id="e1337-956">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the MD5 session.</span></span>
- <span data-ttu-id="e1337-957">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-957">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_sha1_init"></a><span data-ttu-id="e1337-958">_nx_crypto_method_sha1_init</span><span class="sxs-lookup"><span data-stu-id="e1337-958">_nx_crypto_method_sha1_init</span></span>

<span data-ttu-id="e1337-959">Inicializa o bloco de controlo cripto SHA1</span><span class="sxs-lookup"><span data-stu-id="e1337-959">Initializes the SHA1 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-960">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-960">Prototype</span></span>

```c
UINT _nx_crypto_method_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="e1337-961">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-961">Description</span></span>

<span data-ttu-id="e1337-962">Esta função inicializa o bloco de controlo SHA1 com a chave dada.</span><span class="sxs-lookup"><span data-stu-id="e1337-962">This function initializes the SHA1 control block with the given key string.</span></span> <span data-ttu-id="e1337-963">Uma vez iniciada a inicial do bloco de controlo SHA1, a operação SUBSEQUENTE SHA1 deve utilizar o mesmo bloco de comando.</span><span class="sxs-lookup"><span data-stu-id="e1337-963">Once the SHA1 control block is initialized, subsequent SHA1 operation shall be using the same control block.</span></span>

<span data-ttu-id="e1337-964">A aplicação pode criar vários blocos de controlo SHA1, cada um representa uma sessão.</span><span class="sxs-lookup"><span data-stu-id="e1337-964">Application may create multiple SHA1 control blocks, each represents a session.</span></span> <span data-ttu-id="e1337-965">A inicialização do bloco de controlo SHA1 inicia uma nova sessão de computação de haxixe.</span><span class="sxs-lookup"><span data-stu-id="e1337-965">Initializing the SHA1 control block starts a new hash computation session.</span></span> <span data-ttu-id="e1337-966">A re-inicialização do bloco de controlo SHA1 abandona a sessão atual e protagoniza uma nova.</span><span class="sxs-lookup"><span data-stu-id="e1337-966">Re-initializing the SHA1 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-967">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-967">Parameters</span></span>

- <span data-ttu-id="e1337-968">**método** Ponteiro para um bloco de controlo de método cripto SHA1 válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-968">**method** Pointer to a valid SHA1 crypto method control block.</span></span> <span data-ttu-id="e1337-969">Estão disponíveis os seguintes métodos cripto pré-definidos:</span><span class="sxs-lookup"><span data-stu-id="e1337-969">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="e1337-970">*crypto_method_sha1*</span><span class="sxs-lookup"><span data-stu-id="e1337-970">*crypto_method_sha1*</span></span>
- <span data-ttu-id="e1337-971">**chave** Este campo não é utilizado para SHA1.</span><span class="sxs-lookup"><span data-stu-id="e1337-971">**key** This field is not used for SHA1.</span></span>
- <span data-ttu-id="e1337-972">**key_size_in_bits** Este campo não é usado para SHA1</span><span class="sxs-lookup"><span data-stu-id="e1337-972">**key_size_in_bits** This field is not used for SHA1</span></span>
- <span data-ttu-id="e1337-973">**cabo** Este serviço devolve uma manípula ao autor da chamada.</span><span class="sxs-lookup"><span data-stu-id="e1337-973">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="e1337-974">O cabo é dependente da implementação e não está a ser utilizado nesta implementação.</span><span class="sxs-lookup"><span data-stu-id="e1337-974">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="e1337-975">O pedido deve passar NU PARA o cabo.</span><span class="sxs-lookup"><span data-stu-id="e1337-975">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="e1337-976">**crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo SHA1.</span><span class="sxs-lookup"><span data-stu-id="e1337-976">**crypto_metadata** Pointer to a valid memory space for the SHA1 control block.</span></span> <span data-ttu-id="e1337-977">O endereço inicial do espaço de memória deve estar alinhado a 4 byte.</span><span class="sxs-lookup"><span data-stu-id="e1337-977">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="e1337-978">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-978">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-979">Para SHA1, o tamanho dos metadados deve ser *de tamanho (NX_CRYPTO_SHA1)*</span><span class="sxs-lookup"><span data-stu-id="e1337-979">For SHA1, the metadata size must be *sizeof(NX_CRYPTO_SHA1)*</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-980">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-980">Return Values</span></span>

- <span data-ttu-id="e1337-981">**NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo SHA1 com a chave e o tamanho da chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-981">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the SHA1control block with the key and key size.</span></span>
- <span data-ttu-id="e1337-982">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-982">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-983">**NX_PTR_ERROR** (0x07) Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-983">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_sha1_operation"></a><span data-ttu-id="e1337-984">_nx_crypto_method_sha1_operation</span><span class="sxs-lookup"><span data-stu-id="e1337-984">_nx_crypto_method_sha1_operation</span></span>

<span data-ttu-id="e1337-985">Realizar operação de haxixe SHA1</span><span class="sxs-lookup"><span data-stu-id="e1337-985">Perform SHA1 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-986">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-986">Prototype</span></span>

```c
UINT _nx_crypto_method_sha1_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="e1337-987">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-987">Description</span></span>

<span data-ttu-id="e1337-988">Esta função executa a operação de haxixe SHA1.</span><span class="sxs-lookup"><span data-stu-id="e1337-988">This function performs SHA1 hash operation.</span></span> <span data-ttu-id="e1337-989">O bloco de controlo SHA1 deve ter sido inicializado com _ *nx_crypto_method_sha1_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-989">The SHA1 control block must have been initialized with _ *nx_crypto_method_sha1_init()*.</span></span> <span data-ttu-id="e1337-990">O algoritmo SHA1 a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*</span><span class="sxs-lookup"><span data-stu-id="e1337-990">The SHA1 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="e1337-991">Para a operação *final NX_CRYPTO_HASH_CALCULATE,* o tamanho do tampão de saída deve ser de 20 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-991">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 20 bytes.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-992">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-992">Parameters</span></span>

- <span data-ttu-id="e1337-993">**op** Tipo de operação para realizar.</span><span class="sxs-lookup"><span data-stu-id="e1337-993">**op** Type of operation to perform.</span></span> <span data-ttu-id="e1337-994">A operação válida é:</span><span class="sxs-lookup"><span data-stu-id="e1337-994">Valid operation is:</span></span>
  - <span data-ttu-id="e1337-995">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="e1337-995">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="e1337-996">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="e1337-996">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="e1337-997">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="e1337-997">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="e1337-998">**cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-998">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-999">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-999">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-1000">**método** Ponteiro para o método cripto sha1 válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-1000">**method** Pointer to the valid SHA1 crypto method.</span></span> <span data-ttu-id="e1337-1001">O método cripto utilizado aqui deve ser o mesmo utilizado no *nx_crypto_method_sha1_init().*</span><span class="sxs-lookup"><span data-stu-id="e1337-1001">The crypto method used here must be the same used in the *nx_crypto_method_sha1_init().*</span></span>
- <span data-ttu-id="e1337-1002">**input_data** Aponta para um tampão que contém dados de texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-1002">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="e1337-1003">Não existem restrições ao tampão de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-1003">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="e1337-1004">**input_data_size** Tamanho dos dados de entrada, bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-1004">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="e1337-1005">**iv_ptr** Este campo não é utilizado para SHA1.</span><span class="sxs-lookup"><span data-stu-id="e1337-1005">**iv_ptr** This field is not used for SHA1.</span></span>
- <span data-ttu-id="e1337-1006">**iv_size** Este campo não é utilizado para SHA1.</span><span class="sxs-lookup"><span data-stu-id="e1337-1006">**iv_size** This field is not used for SHA1.</span></span>
- <span data-ttu-id="e1337-1007">**output_buffer** Ponteiro para a área de memória para o haxixe SHA1 gerado.</span><span class="sxs-lookup"><span data-stu-id="e1337-1007">**output_buffer** Pointer to the memory area for the generated SHA1 hash.</span></span>
- <span data-ttu-id="e1337-1008">**output_buffer_size** Tamanho do tampão de saída em bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-1008">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="e1337-1009">Para SHA1 o tamanho do tampão deve ser de 20 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-1009">For SHA1 the buffer size must be 20 bytes.</span></span>
- <span data-ttu-id="e1337-1010">**crypto_metadata** Ponteiro para o bloco de controlo SHA1 utilizado em *_nx_crypto_method_sha1_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-1010">**crypto_metadata** Pointer to the SHA1 control block used in *_nx_crypto_method_sha1_init()*.</span></span>
- <span data-ttu-id="e1337-1011">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-1011">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-1012">Para SHA1, o tamanho dos metadados deve *ser do tamanho (NX_CRYPTO_SHA1)*</span><span class="sxs-lookup"><span data-stu-id="e1337-1012">For SHA1, the metadata size must *sizeof(NX_CRYPTO_SHA1)*</span></span>
- <span data-ttu-id="e1337-1013">**packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-1013">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-1014">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-1014">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-1015">**nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-1015">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-1016">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-1016">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-1017">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-1017">Return Values</span></span>

- <span data-ttu-id="e1337-1018">**NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação SHA1.</span><span class="sxs-lookup"><span data-stu-id="e1337-1018">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the SHA1 operation.</span></span>
- <span data-ttu-id="e1337-1019">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-1019">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-1020">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.</span><span class="sxs-lookup"><span data-stu-id="e1337-1020">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="e1337-1021">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) algoritmo SHA1 inválido sendo especificado.</span><span class="sxs-lookup"><span data-stu-id="e1337-1021">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid SHA1 algorithm being specified.</span></span>
- <span data-ttu-id="e1337-1022">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamanho do tampão de saída inválido.</span><span class="sxs-lookup"><span data-stu-id="e1337-1022">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

### <a name="example"></a><span data-ttu-id="e1337-1023">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1337-1023">Example</span></span>

## <a name="_nx_crypto_method_sha1_cleanup"></a><span data-ttu-id="e1337-1024">_nx_crypto_method_sha1_cleanup</span><span class="sxs-lookup"><span data-stu-id="e1337-1024">_nx_crypto_method_sha1_cleanup</span></span>

<span data-ttu-id="e1337-1025">Limpe o bloco de controlo SHA1.</span><span class="sxs-lookup"><span data-stu-id="e1337-1025">Clean up the SHA1 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-1026">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-1026">Prototype</span></span>

```c
UINT _nx_crypto_method_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="e1337-1027">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-1027">Description</span></span>

<span data-ttu-id="e1337-1028">A aplicação chama a esta função para limpar o bloco de controlo SHA1 depois de determinar que esta sessão SHA1 já não é necessária.</span><span class="sxs-lookup"><span data-stu-id="e1337-1028">Application calls this function to clean up the SHA1 control block after it determines this SHA1 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-1029">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-1029">Parameters</span></span>

- <span data-ttu-id="e1337-1030">**crypto_metadata** Ponteiro para o bloco de controlo SHA1 utilizado em *_nx_crypto_method_sha1_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-1030">**crypto_metadata** Pointer to the SHA1 control block used in *_nx_crypto_method_sha1_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-1031">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-1031">Return Values</span></span>

- <span data-ttu-id="e1337-1032">**NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão SHA1.</span><span class="sxs-lookup"><span data-stu-id="e1337-1032">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the SHA1 session.</span></span>
- <span data-ttu-id="e1337-1033">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-1033">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_sha256_init"></a><span data-ttu-id="e1337-1034">_nx_crypto_method_sha256_init</span><span class="sxs-lookup"><span data-stu-id="e1337-1034">_nx_crypto_method_sha256_init</span></span>

<span data-ttu-id="e1337-1035">Inicializa o bloco de controlo cripto SHA256</span><span class="sxs-lookup"><span data-stu-id="e1337-1035">Initializes the SHA256 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-1036">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-1036">Prototype</span></span>

```c
UINT _nx_crypto_method_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size)
```

### <a name="description"></a><span data-ttu-id="e1337-1037">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-1037">Description</span></span>

<span data-ttu-id="e1337-1038">Esta função inicializa o bloco de controlo SHA256 com a chave dada.</span><span class="sxs-lookup"><span data-stu-id="e1337-1038">This function initializes the SHA256 control block with the given key string.</span></span> <span data-ttu-id="e1337-1039">Uma vez iniciada a inicial do bloco de controlo SHA256, a operação subsequente do SHA256 deve utilizar o mesmo bloco de comando.</span><span class="sxs-lookup"><span data-stu-id="e1337-1039">Once the SHA256 control block is initialized, subsequent SHA256 operation shall be using the same control block.</span></span>

<span data-ttu-id="e1337-1040">A aplicação pode criar vários blocos de controlo SHA256, cada um representa uma sessão.</span><span class="sxs-lookup"><span data-stu-id="e1337-1040">Application may create multiple SHA256 control blocks, each represents a session.</span></span> <span data-ttu-id="e1337-1041">A inicialização do bloco de controlo SHA256 inicia uma nova sessão de computação de haxixe.</span><span class="sxs-lookup"><span data-stu-id="e1337-1041">Initializing the SHA256 control block starts a new hash computation session.</span></span> <span data-ttu-id="e1337-1042">A re-inicialização do bloco de controlo SHA256 abandona a sessão atual e protagoniza uma nova.</span><span class="sxs-lookup"><span data-stu-id="e1337-1042">Re-initializing the SHA256 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-1043">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-1043">Parameters</span></span>

- <span data-ttu-id="e1337-1044">**método** Ponteiro para um bloco de controlo de método cripto SHA256 válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-1044">**method** Pointer to a valid SHA256 crypto method control block.</span></span> <span data-ttu-id="e1337-1045">Estão disponíveis os seguintes métodos cripto pré-definidos:</span><span class="sxs-lookup"><span data-stu-id="e1337-1045">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="e1337-1046">*crypto_method_sha256*</span><span class="sxs-lookup"><span data-stu-id="e1337-1046">*crypto_method_sha256*</span></span>
  - <span data-ttu-id="e1337-1047">*crypto_method_sha224*</span><span class="sxs-lookup"><span data-stu-id="e1337-1047">*crypto_method_sha224*</span></span>
- <span data-ttu-id="e1337-1048">**chave** Este campo não é utilizado para SHA256.</span><span class="sxs-lookup"><span data-stu-id="e1337-1048">**key** This field is not used for SHA256.</span></span>
- <span data-ttu-id="e1337-1049">**key_size_in_bits** Este campo não é usado para SHA256</span><span class="sxs-lookup"><span data-stu-id="e1337-1049">**key_size_in_bits** This field is not used for SHA256</span></span>
- <span data-ttu-id="e1337-1050">**cabo** Este serviço devolve uma manípula ao autor da chamada.</span><span class="sxs-lookup"><span data-stu-id="e1337-1050">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="e1337-1051">O cabo é dependente da implementação e não está a ser utilizado nesta implementação.</span><span class="sxs-lookup"><span data-stu-id="e1337-1051">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="e1337-1052">O pedido deve passar NU PARA o cabo.</span><span class="sxs-lookup"><span data-stu-id="e1337-1052">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="e1337-1053">**crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo SHA256.</span><span class="sxs-lookup"><span data-stu-id="e1337-1053">**crypto_metadata** Pointer to a valid memory space for the SHA256 control block.</span></span> <span data-ttu-id="e1337-1054">O endereço inicial do espaço de memória deve estar alinhado a 4 byte.</span><span class="sxs-lookup"><span data-stu-id="e1337-1054">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="e1337-1055">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-1055">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-1056">Para SHA256, o tamanho dos metadados deve ser *de tamanho (NX_CRYPTO_SHA256)*</span><span class="sxs-lookup"><span data-stu-id="e1337-1056">For SHA256, the metadata size must be *sizeof(NX_CRYPTO_SHA256)*</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-1057">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-1057">Return Values</span></span>

- <span data-ttu-id="e1337-1058">**NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo SHA256 com a chave e o tamanho da chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-1058">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the SHA256 control block with the key and key size.</span></span>
- <span data-ttu-id="e1337-1059">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-1059">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-1060">**NX_PTR_ERROR** (0x07) Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-1060">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_sha256_operation"></a><span data-ttu-id="e1337-1061">_nx_crypto_method_sha256_operation</span><span class="sxs-lookup"><span data-stu-id="e1337-1061">_nx_crypto_method_sha256_operation</span></span>

<span data-ttu-id="e1337-1062">Realizar operação de haxixe SHA256</span><span class="sxs-lookup"><span data-stu-id="e1337-1062">Perform SHA256 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-1063">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-1063">Prototype</span></span>

```c
UINT _nx_crypto_method_sha256_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="e1337-1064">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-1064">Description</span></span>

<span data-ttu-id="e1337-1065">Esta função executa a operação hash SHA256.</span><span class="sxs-lookup"><span data-stu-id="e1337-1065">This function performs SHA256 hash operation.</span></span> <span data-ttu-id="e1337-1066">O bloco de controlo SHA256 deve ter sido inicializado com _ ***nx_crypto_method_sha256_init()***.</span><span class="sxs-lookup"><span data-stu-id="e1337-1066">The SHA256 control block must have been initialized with _ ***nx_crypto_method_sha256_init()***.</span></span> <span data-ttu-id="e1337-1067">O algoritmo SHA256 a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*</span><span class="sxs-lookup"><span data-stu-id="e1337-1067">The SHA256 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="e1337-1068">Para a operação *de NX_CRYPTO_HASH_CALCULATE* final, o tamanho do tampão de saída deve ser de 32 bytes para SHA256, ou 28 bytes para SHA224.</span><span class="sxs-lookup"><span data-stu-id="e1337-1068">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 32 bytes for SHA256, or 28 bytes for SHA224.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-1069">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-1069">Parameters</span></span>

- <span data-ttu-id="e1337-1070">**op** Tipo de operação para realizar.</span><span class="sxs-lookup"><span data-stu-id="e1337-1070">**op** Type of operation to perform.</span></span> <span data-ttu-id="e1337-1071">A operação válida é:</span><span class="sxs-lookup"><span data-stu-id="e1337-1071">Valid operation is:</span></span>
  - <span data-ttu-id="e1337-1072">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="e1337-1072">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="e1337-1073">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="e1337-1073">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="e1337-1074">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="e1337-1074">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="e1337-1075">**cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-1075">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-1076">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-1076">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-1077">**método** Ponteiro para o método cripto sha256 válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-1077">**method** Pointer to the valid SHA256 crypto method.</span></span> <span data-ttu-id="e1337-1078">O método cripto utilizado aqui deve ser o mesmo utilizado no _ *nx_crypto_method_sha256_init().*</span><span class="sxs-lookup"><span data-stu-id="e1337-1078">The crypto method used here must be the same used in the _ *nx_crypto_method_sha256_init().*</span></span>
- <span data-ttu-id="e1337-1079">**input_data** Aponta para um tampão que contém dados de texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-1079">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="e1337-1080">Não existem restrições ao tampão de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-1080">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="e1337-1081">**input_data_size** Tamanho dos dados de entrada, bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-1081">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="e1337-1082">**iv_ptr** Este campo não é utilizado para SHA256.</span><span class="sxs-lookup"><span data-stu-id="e1337-1082">**iv_ptr** This field is not used for SHA256.</span></span>
- <span data-ttu-id="e1337-1083">**iv_size** Este campo não é utilizado para SHA256.</span><span class="sxs-lookup"><span data-stu-id="e1337-1083">**iv_size** This field is not used for SHA256.</span></span>
- <span data-ttu-id="e1337-1084">**output_buffer** Ponteiro para a área de memória para o haxixe SHA256 gerado.</span><span class="sxs-lookup"><span data-stu-id="e1337-1084">**output_buffer** Pointer to the memory area for the generated SHA256 hash.</span></span>
- <span data-ttu-id="e1337-1085">**output_buffer_size** Tamanho do tampão de saída em bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-1085">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="e1337-1086">Para SHA256 o tamanho do tampão deve ser de 32 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-1086">For SHA256 the buffer size must be 32 bytes.</span></span> <span data-ttu-id="e1337-1087">Para SHA224 o tamanho do tampão deve ser de 28 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-1087">For SHA224 the buffer size must be 28 bytes.</span></span>
- <span data-ttu-id="e1337-1088">**crypto_metadata** Ponteiro para o bloco de controlo SHA2 utilizado em *_nx_crypto_method_sha2_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-1088">**crypto_metadata** Pointer to the SHA2 control block used in *_nx_crypto_method_sha2_init()*.</span></span>
- <span data-ttu-id="e1337-1089">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-1089">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-1090">Para SHA256, o tamanho dos metadados deve *ser do tamanho (NX_CRYPTO_SHA256)*</span><span class="sxs-lookup"><span data-stu-id="e1337-1090">For SHA256, the metadata size must *sizeof(NX_CRYPTO_SHA256)*</span></span>
- <span data-ttu-id="e1337-1091">**packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-1091">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-1092">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-1092">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-1093">**nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-1093">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-1094">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-1094">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-1095">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-1095">Return Values</span></span>

- <span data-ttu-id="e1337-1096">**NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação SHA256.</span><span class="sxs-lookup"><span data-stu-id="e1337-1096">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the SHA256 operation.</span></span>
- <span data-ttu-id="e1337-1097">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-1097">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-1098">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.</span><span class="sxs-lookup"><span data-stu-id="e1337-1098">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="e1337-1099">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Algoritmo INválido SHA256 sendo especificado.</span><span class="sxs-lookup"><span data-stu-id="e1337-1099">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid SHA256 algorithm being specified.</span></span>
- <span data-ttu-id="e1337-1100">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamanho do tampão de saída inválido.</span><span class="sxs-lookup"><span data-stu-id="e1337-1100">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_sha256_cleanup"></a><span data-ttu-id="e1337-1101">_nx_crypto_method_sha256_cleanup</span><span class="sxs-lookup"><span data-stu-id="e1337-1101">_nx_crypto_method_sha256_cleanup</span></span>

<span data-ttu-id="e1337-1102">Limpe o bloco de controlo SHA256.</span><span class="sxs-lookup"><span data-stu-id="e1337-1102">Clean up the SHA256 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-1103">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-1103">Prototype</span></span>

```c
UINT _nx_crypto_method_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="e1337-1104">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-1104">Description</span></span>

<span data-ttu-id="e1337-1105">A aplicação chama a esta função para limpar o bloco de controlo SHA256 depois de determinar que esta sessão SHA256 já não é necessária.</span><span class="sxs-lookup"><span data-stu-id="e1337-1105">Application calls this function to clean up the SHA256 control block after it determines this SHA256 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-1106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-1106">Parameters</span></span>

- <span data-ttu-id="e1337-1107">**crypto_metadata** Ponteiro para o bloco de controlo SHA256 utilizado em *_nx_crypto_method_sha256_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-1107">**crypto_metadata** Pointer to the SHA256 control block used in *_nx_crypto_method_sha256_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-1108">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-1108">Return Values</span></span>

- <span data-ttu-id="e1337-1109">**NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão SHA256.</span><span class="sxs-lookup"><span data-stu-id="e1337-1109">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the SHA256 session.</span></span>
- <span data-ttu-id="e1337-1110">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-1110">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_sha512_init"></a><span data-ttu-id="e1337-1111">_nx_crypto_method_sha512_init</span><span class="sxs-lookup"><span data-stu-id="e1337-1111">_nx_crypto_method_sha512_init</span></span>

<span data-ttu-id="e1337-1112">Inicializa o bloco de controlo cripto SHA512</span><span class="sxs-lookup"><span data-stu-id="e1337-1112">Initializes the SHA512 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-1113">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-1113">Prototype</span></span>

```c
UINT _nx_crypto_method_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="e1337-1114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-1114">Description</span></span>

<span data-ttu-id="e1337-1115">Esta função inicializa o bloco de controlo SHA512 com a chave dada.</span><span class="sxs-lookup"><span data-stu-id="e1337-1115">This function initializes the SHA512 control block with the given key string.</span></span> <span data-ttu-id="e1337-1116">Uma vez iniciada a inicial do bloco de controlo SHA512, a operação subsequente do SHA512 deve utilizar o mesmo bloco de comando.</span><span class="sxs-lookup"><span data-stu-id="e1337-1116">Once the SHA512 control block is initialized, subsequent SHA512 operation shall be using the same control block.</span></span>

<span data-ttu-id="e1337-1117">A aplicação pode criar vários blocos de controlo SHA512, cada um representa uma sessão.</span><span class="sxs-lookup"><span data-stu-id="e1337-1117">Application may create multiple SHA512 control blocks, each represents a session.</span></span> <span data-ttu-id="e1337-1118">A inicialização do bloco de controlo SHA512 inicia uma nova sessão de computação de haxixe.</span><span class="sxs-lookup"><span data-stu-id="e1337-1118">Initializing the SHA512 control block starts a new hash computation session.</span></span> <span data-ttu-id="e1337-1119">A re-inicialização do bloco de controlo SHA512 abandona a sessão atual e protagoniza uma nova.</span><span class="sxs-lookup"><span data-stu-id="e1337-1119">Re-initializing the SHA512 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-1120">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-1120">Parameters</span></span>

- <span data-ttu-id="e1337-1121">**método** Ponteiro para um bloco de controlo de método cripto SHA512 válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-1121">**method** Pointer to a valid SHA512 crypto method control block.</span></span> <span data-ttu-id="e1337-1122">Estão disponíveis os seguintes métodos cripto pré-definidos:</span><span class="sxs-lookup"><span data-stu-id="e1337-1122">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="e1337-1123">*crypto_method_sha512*</span><span class="sxs-lookup"><span data-stu-id="e1337-1123">*crypto_method_sha512*</span></span>
  - <span data-ttu-id="e1337-1124">*crypto_method_sha384*</span><span class="sxs-lookup"><span data-stu-id="e1337-1124">*crypto_method_sha384*</span></span>
- <span data-ttu-id="e1337-1125">**chave** Este campo não é utilizado para SHA512.</span><span class="sxs-lookup"><span data-stu-id="e1337-1125">**key** This field is not used for SHA512.</span></span>
- <span data-ttu-id="e1337-1126">**key_size_in_bits** Este campo não é usado para SHA512</span><span class="sxs-lookup"><span data-stu-id="e1337-1126">**key_size_in_bits** This field is not used for SHA512</span></span>
- <span data-ttu-id="e1337-1127">**cabo** Este serviço devolve uma manípula ao autor da chamada.</span><span class="sxs-lookup"><span data-stu-id="e1337-1127">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="e1337-1128">O cabo é dependente da implementação e não está a ser utilizado nesta implementação.</span><span class="sxs-lookup"><span data-stu-id="e1337-1128">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="e1337-1129">O pedido deve passar NU PARA o cabo.</span><span class="sxs-lookup"><span data-stu-id="e1337-1129">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="e1337-1130">**crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo SHA512.</span><span class="sxs-lookup"><span data-stu-id="e1337-1130">**crypto_metadata** Pointer to a valid memory space for the SHA512 control block.</span></span> <span data-ttu-id="e1337-1131">O endereço inicial do espaço de memória deve estar alinhado a 4 byte.</span><span class="sxs-lookup"><span data-stu-id="e1337-1131">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="e1337-1132">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-1132">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-1133">Para SHA512, o tamanho dos metadados deve ser *de tamanho (NX_CRYPTO_SHA512)*</span><span class="sxs-lookup"><span data-stu-id="e1337-1133">For SHA512, the metadata size must be *sizeof(NX_CRYPTO_SHA512)*</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-1134">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-1134">Return Values</span></span>

- <span data-ttu-id="e1337-1135">**NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo SHA512 com a chave e o tamanho da chave.</span><span class="sxs-lookup"><span data-stu-id="e1337-1135">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the SHA512 control block with the key and key size.</span></span>
- <span data-ttu-id="e1337-1136">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-1136">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-1137">**NX_PTR_ERROR** (0x07) Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-1137">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_sha512_operation"></a><span data-ttu-id="e1337-1138">_nx_crypto_method_sha512_operation</span><span class="sxs-lookup"><span data-stu-id="e1337-1138">_nx_crypto_method_sha512_operation</span></span>

<span data-ttu-id="e1337-1139">Realizar operação de haxixe SHA512</span><span class="sxs-lookup"><span data-stu-id="e1337-1139">Perform SHA512 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-1140">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-1140">Prototype</span></span>

```c
UINT _nx_crypto_method_sha512_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT status));
```

### <a name="description"></a><span data-ttu-id="e1337-1141">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-1141">Description</span></span>

<span data-ttu-id="e1337-1142">Esta função executa a operação de haxixe SHA512.</span><span class="sxs-lookup"><span data-stu-id="e1337-1142">This function performs SHA512 hash operation.</span></span> <span data-ttu-id="e1337-1143">O bloco de controlo SHA512 deve ter sido inicializado com _ *nx_crypto_method_sha512_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-1143">The SHA512 control block must have been initialized with _ *nx_crypto_method_sha512_init()*.</span></span> <span data-ttu-id="e1337-1144">O algoritmo SHA512 a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*</span><span class="sxs-lookup"><span data-stu-id="e1337-1144">The SHA512 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="e1337-1145">Para a operação *de NX_CRYPTO_HASH_CALCULATE* final, o tamanho do tampão de saída deve ser de 64 bytes para SHA512, ou 48 bytes para SHA384.</span><span class="sxs-lookup"><span data-stu-id="e1337-1145">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 64 bytes for SHA512, or 48 bytes for SHA384.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-1146">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-1146">Parameters</span></span>

- <span data-ttu-id="e1337-1147">**op** Tipo de operação para realizar.</span><span class="sxs-lookup"><span data-stu-id="e1337-1147">**op** Type of operation to perform.</span></span> <span data-ttu-id="e1337-1148">A operação válida é:</span><span class="sxs-lookup"><span data-stu-id="e1337-1148">Valid operation is:</span></span>
  - <span data-ttu-id="e1337-1149">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="e1337-1149">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="e1337-1150">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="e1337-1150">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="e1337-1151">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="e1337-1151">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="e1337-1152">**cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-1152">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-1153">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-1153">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-1154">**método** Ponteiro para o método cripto sha512 válido.</span><span class="sxs-lookup"><span data-stu-id="e1337-1154">**method** Pointer to the valid SHA512 crypto method.</span></span> <span data-ttu-id="e1337-1155">O método cripto utilizado aqui deve ser o mesmo utilizado no _ *nx_crypto_method_sha512_init().*</span><span class="sxs-lookup"><span data-stu-id="e1337-1155">The crypto method used here must be the same used in the _ *nx_crypto_method_sha512_init().*</span></span>
- <span data-ttu-id="e1337-1156">**input_data** Aponta para um tampão que contém dados de texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-1156">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="e1337-1157">Não existem restrições ao tampão de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1337-1157">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="e1337-1158">**input_data_size** Tamanho dos dados de entrada, bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-1158">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="e1337-1159">**iv_ptr** Este campo não é utilizado para SHA512.</span><span class="sxs-lookup"><span data-stu-id="e1337-1159">**iv_ptr** This field is not used for SHA512.</span></span>
- <span data-ttu-id="e1337-1160">**iv_size** Este campo não é utilizado para SHA512.</span><span class="sxs-lookup"><span data-stu-id="e1337-1160">**iv_size** This field is not used for SHA512.</span></span>
- <span data-ttu-id="e1337-1161">**output_buffer** Ponteiro para a área de memória para o haxixe SHA512 gerado.</span><span class="sxs-lookup"><span data-stu-id="e1337-1161">**output_buffer** Pointer to the memory area for the generated SHA512 hash.</span></span>
- <span data-ttu-id="e1337-1162">**output_buffer_size** Tamanho do tampão de saída em bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-1162">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="e1337-1163">Para SHA512 o tamanho do tampão deve ser de 64 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-1163">For SHA512 the buffer size must be 64 bytes.</span></span> <span data-ttu-id="e1337-1164">Para SHA384 o tamanho do tampão deve ser de 48 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1337-1164">For SHA384 the buffer size must be 48 bytes.</span></span>
- <span data-ttu-id="e1337-1165">**crypto_metadata** Ponteiro para o bloco de controlo SHA512 utilizado em *_nx_crypto_method_sha512_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-1165">**crypto_metadata** Pointer to the SHA512 control block used in *_nx_crypto_method_sha512_init()*.</span></span>
- <span data-ttu-id="e1337-1166">**crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="e1337-1166">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="e1337-1167">Para SHA512, o tamanho dos metadados deve *ser do tamanho (NX_CRYPTO_SHA512)*</span><span class="sxs-lookup"><span data-stu-id="e1337-1167">For SHA512, the metadata size must *sizeof(NX_CRYPTO_SHA512)*</span></span>
- <span data-ttu-id="e1337-1168">**packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-1168">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-1169">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-1169">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="e1337-1170">**nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="e1337-1170">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="e1337-1171">Todos os valores passados são silenciosamente ignorados.</span><span class="sxs-lookup"><span data-stu-id="e1337-1171">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-1172">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-1172">Return Values</span></span>

- <span data-ttu-id="e1337-1173">**NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação SHA512.</span><span class="sxs-lookup"><span data-stu-id="e1337-1173">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the SHA512 operation.</span></span>
- <span data-ttu-id="e1337-1174">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-1174">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="e1337-1175">**NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.</span><span class="sxs-lookup"><span data-stu-id="e1337-1175">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="e1337-1176">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Algoritmo INválido SHA512 sendo especificado.</span><span class="sxs-lookup"><span data-stu-id="e1337-1176">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid SHA512 algorithm being specified.</span></span>
- <span data-ttu-id="e1337-1177">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamanho do tampão de saída inválido.</span><span class="sxs-lookup"><span data-stu-id="e1337-1177">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_sha512_cleanup"></a><span data-ttu-id="e1337-1178">_nx_crypto_method_sha512_cleanup</span><span class="sxs-lookup"><span data-stu-id="e1337-1178">_nx_crypto_method_sha512_cleanup</span></span>

<span data-ttu-id="e1337-1179">Limpe o bloco de controlo SHA512.</span><span class="sxs-lookup"><span data-stu-id="e1337-1179">Clean up the SHA512 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="e1337-1180">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1337-1180">Prototype</span></span>

```c
UINT _nx_crypto_method_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="e1337-1181">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1337-1181">Description</span></span>

<span data-ttu-id="e1337-1182">A aplicação chama a esta função para limpar o bloco de controlo SHA512 depois de determinar que esta sessão SHA512 já não é necessária.</span><span class="sxs-lookup"><span data-stu-id="e1337-1182">Application calls this function to clean up the SHA512 control block after it determines this SHA512 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="e1337-1183">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e1337-1183">Parameters</span></span>

- <span data-ttu-id="e1337-1184">**crypto_metadata** Ponteiro para o bloco de controlo SHA512 utilizado em *_nx_crypto_method_sha512_init()*.</span><span class="sxs-lookup"><span data-stu-id="e1337-1184">**crypto_metadata** Pointer to the SHA512 control block used in *_nx_crypto_method_sha512_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1337-1185">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e1337-1185">Return Values</span></span>

- <span data-ttu-id="e1337-1186">**NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão SHA512.</span><span class="sxs-lookup"><span data-stu-id="e1337-1186">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the SHA512 session.</span></span>
- <span data-ttu-id="e1337-1187">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="e1337-1187">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>