---
title: Capítulo 4 - Azure RTOS NetX Crypto API descrição
description: Descrição da Azure RTOS NetX Crypto API
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5bd4cdae28a293ec9ef259bbd29fdb8f8d6dc43f964cbc184290b82ee8f590a3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788809"
---
# <a name="chapter-4---azure-rtos-netx-crypto-api-description"></a>Capítulo 4 - Azure RTOS NetX Crypto API descrição

## <a name="nx_crypto_initialize"></a>nx_crypto_initialize

Inicializa a Biblioteca Segura NetX

### <a name="prototype"></a>Prototype

```c
UINT nx_crypto_initialize(VOID);
```

### <a name="description"></a>Description

Esta função inicializa o módulo de biblioteca Azure RTOS NetX Crypto. Antes de utilizar qualquer outra função criptográfica, a aplicação deve chamar esta função para executar a inicialização e validar a integridade da biblioteca. A não utilização desta função antes de utilizar outros serviços NetX Crypto resultará na devolvição de erros.

### <a name="parameters"></a>Parâmetros

- **Nenhuma**

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) Biblioteca NetX Crypto inicializada com sucesso. As funções da biblioteca estão agora prontas e podem ser usadas.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A criptobigrafia não inicia ou falha na verificação de integridade. A aplicação não pode usar esta biblioteca.

### <a name="example"></a>Exemplo

TODO

## <a name="nx_crypto_module_state_get"></a>nx_crypto_module_state_get

Recuperar o estado atual do módulo ativado pelo FIPS

### <a name="prototype"></a>Prototype

```c
UINT nx_crypto_module_state_get(VOID);
```

### <a name="description"></a>Description

Este serviço só está disponível na biblioteca de construção FIPS. Devolve o estado atual da biblioteca NetX Crypto.

### <a name="parameters"></a>Parâmetros

- **Nenhuma**

### <a name="return-values"></a>Valores de devolução

- **Bandeira de estado:**
  - NX_CRYPTO_LIBRARY_STATE_UNINITIALIZED 0x00000001
  - NX_CRYPTO_LIBRARY_STATE_POST_IN_PROGRESS 0x00000002
  - NX_CRYPTO_LIBRARY_STATE_INTEGRITY_TEST_FAILED 0x00000004
  - NX_CRYPTO_LIBRARY_STATE_FUNCTIONAL_TEST_FAILED 0x00000008
  - NX_CRYPTO_LIBRARY_STATE_OPERATIONAL 0x80000000
- **Todos os outros valores são inválidos.**

### <a name="example"></a>Exemplo

TODO

## <a name="_nx_crypto_method_aes_init"></a>_nx_crypto_method_aes_init

Inicializa o bloco de controlo cripto AES

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_aes_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Esta função inicializa o bloco de controlo AES com a chave dada. Uma vez iniciado o bloco de controlo AES, a operação AES subsequente utilizará a mesma chave e tamanho da chave.

A aplicação pode criar vários blocos de controlo AES, cada um representa uma sessão. Uma chave é atribuída a um bloco de controlo. A encriptação ou a operação de desencriptação subsequentes podem fazer referência ao mesmo bloco de controlo AES sem a necessidade de re-inicializar o bloco de controlo AES. Se a chave para a sessão for alterada, a aplicação precisa de re-inicializar o bloco de controlo AES com a chave atualizada.

Chamando _ *nx_crypto_method_aes_init()* atualiza automaticamente uma chave e tamanho de chave previamente configurados para a nova chave.

### <a name="parameters"></a>Parâmetros

- **método** Ponteiro para um bloco de controlo de método cripto AES válido. Estão disponíveis os seguintes métodos cripto AES pré-definidos:
  - *crypto_method_aes_cbc_128*
  - *crypto_method_aes_cbc_192*
  - *crypto_method_aes_cbc_256*
  - *crypto_method_aes_ctr_128*
  - *crypto_method_aes_ctr_192*
  - *crypto_method_aes_ctr_256*
  - *crypto_method_aes_xcbc_128*
  - *crypto_method_aes_ccm_8_128*
- **chave** Aponta para um tampão que contém a chave AES
- **key_size_in_bits** Tamanho da chave, em pedaços. Os valores válidos são:
  - *NX_CRYPTO_AES_KEY_SIZE_128_BITS*
  - *NX_CRYPTO_AES_KEY_SIZE_192_BITS*
  - *NX_CRYPTO_AES_KEY_SIZE_256_BITS*
  - **Todos os outros valores são inválidos.**
- **cabo** Este serviço devolve uma manípula ao autor da chamada. O cabo é dependente da implementação e não está a ser utilizado nesta implementação. O pedido deve passar NU PARA o cabo.
- **crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo AES. O endereço inicial do espaço de memória deve estar alinhado a 4 byte.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para a AES, o tamanho dos metadados deve ser *de dimensão (NX_AES)*

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo AES com a chave e o tamanho da chave.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR (0x07)** Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.
- **NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) O tamanho da chave não é válido para AES.

## <a name="_nx_crypto_method_aes_operation"></a>_nx_crypto_method_aes_operation

Efetuar uma operação AES (encriptação ou desencriptação).

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Description

Esta função executa a encriptação ou operação de desencriptação AES. O bloco de controlo AES deve ter sido inicializado com _ *nx_crypto_method_aes_init()*. O algoritmo AES a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*

O tamanho do tampão de entrada deve ser um múltiplo de 16 bytes. O tamanho dos dados desencriptados é do mesmo tamanho do tamanho dos dados de entrada. Se os dados encriptados forem acolchoados para obter um múltiplo do tamanho do bloco AES, o acolchoamento será incluído no tampão de saída e deve ser tratado pela aplicação.

Esta operação não guarda informações estatais e não altera o material chave no bloco de controlo AES.

Quando a operação é NX_CRYPTO_SET_ADDITIONAL_DATA e o algoritm é AES-CCM8, a entrada aponta para dados adicionais e input_length_in_byte é o comprimento de dados adicionais.

### <a name="parameters"></a>Parâmetros

- **op** Tipo de operação para realizar. As operações válidas são:
  - *NX_CRYPTO_ENCRYPT*
  - *NX_CRYPTO_DECRYPT*
  - *NX_CRYPTO_AUTHENTICATE (apenas AES-XCBC)*
  - *NX_CRYPTO_SET_ADDITIONAL_DATA (apenas AES-CCM8)*
- **cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **método** Ponteiro para o método cripto AES válido. O método cripto utilizado aqui deve ser o mesmo utilizado no *nx_crypto_method_aes_init().*
- **input_data** Aponta para um tampão que contém dados de texto encriptados. Não existem restrições ao tampão de entrada.
- **input_data_size** Tamanho dos dados de entrada, bytes. O tamanho dos dados de entrada deve ser um múltiplo de 16 bytes.
- **iv_ptr** Ponteiro para o vetor inicial. Não há restrições ao tampão IV.
- **iv_size** Tamanho do bloco de vetor inicial, em bytes Este campo deve ser 16.
- **output_buffer** Ponteiro para a área de memória para a AES armazenar os dados de texto claros. A aplicação deve atribuir espaço para o tampão de saída. O tampão de saída pode sobrepor-se ao tampão de entrada. O tampão de saída pode sobrepor-se ao tampão de entrada se partilharem o mesmo endereço inicial.
- **output_buffer_size** Tamanho do tampão de saída em bytes. O tamanho do tampão de saída deve ser pelo menos o mesmo do tamanho do tampão de entrada, e o tamanho do tampão de saída deve ser um múltiplo de 16 bytes.
- **crypto_metadata** Ponteiro para o bloco de controlo AES utilizado em *_nx_crypto_method_aes_init() \* . \**
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para a AES, o tamanho dos metadados deve *ser do tamanho (NX_AES)*
- **packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **nx_crypto_hw_process_callback** - Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação AES.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Algoritmo AES inválido sendo especificado**.

## <a name="_nx_crypto_method_aes_cleanup"></a>_nx_crypto_method_aes_cleanup

Limpe o bloco de controlo AES.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_aes_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

A aplicação chama a esta função para limpar o bloco de controlo AES depois de determinar que esta sessão AES já não é necessária.

### <a name="parameters"></a>Parâmetros

- **crypto_metadata** Ponteiro para o bloco de controlo AES utilizado em *_nx_crypto_method_aes_init() \* . \**

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão AES.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.

## <a name="_nx_crypto_method_3des_init"></a>_nx_crypto_method_3des_init

Inicialize o bloco de controlo 3DES.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_3des_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Esta função inicializa o bloco de controlo Triple DES (3DES) com as três cordas de teclas. As cordas das chaves devem ser de 8 bytes cada. As três teclas DES devem ser concatenadas na memória contígua do tampão de 24 byte. Para a construção compatível com o FIPS, as três teclas devem ser diferentes de cada uma ou a função retornará o erro NX_CRYPTO_INVALID_KEY. Uma vez inicializado o bloco de controlo 3DES, as operações subsequentes em 3DES utilizarão as mesmas teclas.

Uma aplicação pode criar vários blocos de controlo 3DES, cada um representando uma sessão. Uma chave é atribuída a um bloco de controlo e as operações subsequentes de encriptação ou desencriptação podem referenciar o mesmo bloco de controlo sem necessidade de re-inicializar. Se a chave para uma sessão for alterada, a aplicação terá de re-inicializar o bloco de controlo com a tecla atualizada.

Chamando _ *nx_crypto_method_3des_init()* atualiza automaticamente uma chave previamente configurada para as novas teclas.

### <a name="parameters"></a>Parâmetros

- **método** Ponteiro para um bloco de controlo de método cripto 3DES válido. Está disponível o seguinte método cripto 3DES pré-definido: ***crypto_method_3des***
- **chave** Aponta para um tampão que contém a chave de três (3) DES
- **key_size_in_bits** Devem ser 192 (3 teclas, cada 64 bits).
- **cabo** Este serviço devolve uma manípula ao autor da chamada. O cabo identifica o bloco de controlo 3DES que está a ser inicializado. As operações subsequentes 3DES (encriptação, desencriptação e limpeza) utilizam este cabo para aceder ao bloco de controlo 3DES
- **crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo 3DES. O endereço inicial do espaço de memória deve estar alinhado a 4 byte.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para 3DES, o tamanho dos metadados deve ser *de tamanho (NX_3DES)*

### <a name="return-value"></a>Devolver Valor

- **NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo 3DES com a chave e o tamanho da chave.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR (0x07)** Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.
- **NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) O tamanho da chave não é válido para 3DES.

## <a name="_nx_crypto_method_3des_operation"></a>_nx_crypto_method_3des_operation

Criptografe ou desencripta com 3DES.

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Description

Esta função executa a encriptação ou operação de desencriptação 3DES. O bloco de controlo 3DES deve ter sido inicializado com _ *nx_crypto_method_3des_init()*. O algoritmo 3DES a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*

O tamanho do tampão de entrada deve ser um múltiplo de 8 bytes. O tamanho dos dados desencriptados é do mesmo tamanho do tamanho dos dados de entrada. Se os dados encriptados foram acolchoados para obter um múltiplo do tamanho do bloco 3DES, o acolchoamento será incluído no tampão de saída e deve ser tratado pela aplicação.

Esta operação não guarda informações estatais e não altera o material chave no bloco de controlo 3DES.

### <a name="parameters"></a>Parâmetros

- **op** Tipo de operação para realizar. As operações válidas são:
  - *NX_CRYPTO_ENCRYPT*
  - *NX_CRYPTO_DECRYPT*
- **cabo** A pega inicializada por *_nx_crypto_method_3des_init()*.
- **método** Ponteiro para o método cripto 3DES válido. O método cripto utilizado aqui deve ser o mesmo utilizado no *nx_crypto_method_3des_init().*
- **input_data** Aponta para um tampão que contém dados de texto encriptados.
Não existem restrições ao tampão de entrada.
- **input_data_size** Tamanho dos dados de entrada, bytes. O tamanho dos dados de entrada deve ser um múltiplo de 8 bytes.
- **iv_ptr** Ponteiro para o vetor inicial. Não há restrições ao tampão IV.
- **iv_size** Tamanho do bloco de vetor inicial, em bytes Este campo deve ser 8.
- **output_buffer** Ponteiro para a área de memória para 3DES para armazenar os dados de texto claros. A aplicação deve atribuir espaço para o tampão de saída. O tampão de saída pode sobrepor-se ao tampão de entrada. O tampão de saída pode sobrepor-se ao tampão de entrada se partilharem o mesmo endereço inicial.
- **output_buffer_size** Tamanho do tampão de saída em bytes. O tamanho do tampão de saída deve ser pelo menos o mesmo do tamanho do tampão de entrada, e o tamanho do tampão de saída deve ser um múltiplo de 8 bytes.
- **crypto_metadata** Ponteiro para o bloco de controlo 3DES utilizado em *_nx_crypto_method_3des_init()*.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para 3DES, o tamanho dos metadados deve ser *de tamanho (NX_3DES)*
- **packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.

### <a name="description"></a>Description

Esta função executa encriptação 3DES. O bloco de controlo 3DES deve ter sido inicializado com _ *nx_crypto_moethod_3des_init()*. Esta operação não guarda informações estatais e não altera o material chave no bloco de controlo 3DES. Note que o estofamento não é adicionado por esta função, pelo que o chamador terá de manusear o estofamento antes de invocar a operação de encriptação.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo 3DES com a chave e o tamanho da chave.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR (0x07)** Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.

## <a name="_nx_crypto_method_3des_cleanup"></a>_nx_crypto_method_3des_cleanup

Limpe o bloco de controlo 3DES.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_3des_cleanup(VOID *crypto_metadata);
```

### <a name="description"></a>Description

A aplicação chama esta função para limpar o bloco de controlo 3DES depois de determinar que esta sessão 3DES já não é necessária.

### <a name="parameters"></a>Parâmetros

- **cabo** A pega inicializada por *_nx_crypto_method_3des_init()*.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão 3DES.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.

## <a name="_nx_crypto_method_drbg_init"></a>_nx_crypto_method_drbg_init

Inicializa o bloco de controlo cripto DRBG

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_drbg_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Esta função inicializa o bloco de controlo DRBG com a chave dada. Uma vez iniciado o bloco de controlo DRBG, a operação DRBG subsequente deve utilizar o mesmo bloco de controlo.

A aplicação pode criar vários blocos de controlo DRBG, cada um representa uma sessão. A inicialização do bloco de controlo DRBG inicia uma nova sessão de computação de haxixe. A re-inicialização do bloco de controlo DRBG abandona a sessão atual e protagoniza uma nova.

### <a name="parameters"></a>Parâmetros

- **método** Ponteiro para um bloco de controlo de método cripto DRBG válido. Estão disponíveis os seguintes métodos cripto pré-definidos:
  - *crypto_method_drbg*
- **chave** Este campo não é utilizado para a DRBG.
- **key_size_in_bits** Este campo não é utilizado para a DRBG.
- **cabo** Este serviço devolve uma manípula ao autor da chamada. O cabo é dependente da implementação e não está a ser utilizado nesta implementação. O pedido deve passar NU PARA o cabo.
- **crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo DRBG. O endereço inicial do espaço de memória deve estar alinhado a 4 byte.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para a DRBG, o tamanho dos metadados deve ser *de tamanho (NX_CRYPTO_DRBG)*

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo DRBG com a chave e o tamanho da chave.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.

## <a name="_nx_crypto_method_drbg_operation"></a>_nx_crypto_method_drbg_operation

Executar operação DRBG

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Description

Esta função executa o funcionamento drbg. O bloco de controlo DRBG deve ter sido inicializado com _ *nx_crypto_method_drbg_init()*. O algoritmo DRBG a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.* Por predefinição, o AES-128 é utilizado para a DRBG.

Quando a operação é NX_CRYPTO_DRBG_OPTIONS_SET, a entrada aponta para NX_CRYPTO_DRBG_OPTIONS estrutura. Quando a operação é NX_CRYPTO_DRBG_INSTANTIATE, a chave aponta para nonce, a entrada aponta para a cadeia de personalização. Quando a operação é NX_CRYPTO_DRBG_RESEED ou NX_CRYPTO_DRBG_GENERATE, a entrada aponta para uma entrada adicional.

### <a name="parameters"></a>Parâmetros

- **op** Tipo de operação para realizar. A operação válida é:
  - *NX_CRYPTO_DRBG_OPTIONS_SET*
  - *NX_CRYPTO_DRBG_INSTANTIATE*
  - *NX_CRYPTO_DRBG_RESEED NX_CRYPTO_DRBG_GENERATE*
- **cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **método** Ponteiro para o método cripto DRBG válido. O método cripto utilizado aqui deve ser o mesmo utilizado no _ *nx_crypto_method_drbg_init().*
- **chave** Ponteiro para o nó para a operação instantânea. Este campo não é utilizado para outras operações.
- **key_size_in_bits** Tamanho do nonce, em pedaços. Este campo não é utilizado para outras operações.
- **entrada** Quando a operação é NX_CRYPTO_DRBG_OPTIONS_SET, este campo aponta para as opções de DRBG. Quando a operação é NX_CRYPTO_DRBG_INSTANTIATE, este campo aponta para a cadeia de personalização. Quando a operação é NX_CRYPTO_DRBG_RESEED ou NX_CRYPTO_DRBG_GENERATE, este campo aponta para dados adicionais de entrada.
- **input_length_in_byte** Tamanho dos dados de entrada, bytes.
- **iv_ptr** Este campo não é utilizado para a DRBG.
- **saída** Quando a operação é NX_CRYPTO_DRBG_GENERATE, este campo aponta para a área de memória para o DRBG gerado. Caso contrário, este campo não é utilizado.
- **output_length_in_byte** Tamanho do tampão de saída em bytes.
- **crypto_metadata** Ponteiro para o bloco de controlo DRBG utilizado em *_nx_crypto_method_drbg_init()*.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para a DRBG, o tamanho dos metadados deve ser *do tamanho (NX_CRYPTO_DRBG)*
- **packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação DRBG.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) algoritmo DRBG inválido sendo especificado.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamanho do tampão de saída inválido.

## <a name="_nx_crypto_method_drbg_cleanup"></a>_nx_crypto_method_drbg_cleanup

Limpe o bloco de controlo DRBG.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_drbg_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

A aplicação chama a esta função para limpar o bloco de controlo DRBG depois de determinar que esta sessão de DRBG já não é necessária.

### <a name="parameters"></a>Parâmetros

- **crypto_metadata** Ponteiro para o bloco de controlo DRBG utilizado em *_nx_crypto_method_drbg_init()*.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão de DRBG.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.

## <a name="_nx_crypto_method_ecdh_init"></a>_nx_crypto_method_ecdh_init

Inicializa o bloco de controlo cripto do ECDH

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_ecdh_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Esta função inicializa o bloco de controlo ECDH com a corda de chave dada. Uma vez iniciada a inicial do bloco de controlo do ECDH, a operação subsequente do ECDH deve utilizar o mesmo bloco de controlo.

A aplicação pode criar vários blocos de controlo ECDH, cada um representa uma sessão. A inicialização do bloco de controlo do ECDH inicia uma nova sessão de computação de haxixe. A re-inicialização do bloco de controlo do ECDH abandona a sessão atual e protagoniza uma nova.

### <a name="parameters"></a>Parâmetros

- **método** Ponteiro para um bloco de controlo de método cripto ECDH válido. Estão disponíveis os seguintes métodos cripto pré-definidos:
  - *crypto_method_ecdh*
- **chave** Este campo não é usado para o ECDH.
- **key_size_in_bits** Este campo não é usado para o ECDH.
- **cabo** Este serviço devolve uma manípula ao autor da chamada. O cabo é dependente da implementação e não está a ser utilizado nesta implementação. O pedido deve passar NU PARA o cabo.
- **crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo ECDH. O endereço inicial do espaço de memória deve estar alinhado a 4 byte.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para o ECDH, o tamanho dos metadados deve ser *de tamanho (NX_CRYPTO_ECDH)*

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo do ECDH com a chave e o tamanho da chave.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.

## <a name="_nx_crypto_method_ecdh_operation"></a>_nx_crypto_method_ecdh_operation

Realizar operação ECDH

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Description

Esta função executa a operação ECDH. O bloco de controlo do ECDH deve ter sido inicializado com _ *nx_crypto_method_ecdh_init()*. O algoritmo ECDH a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*

Quando a operação é NX_CRYPTO_EC_CURVE_SET, a entrada aponta para o método cripto da curva elíptica. Quando a operação é NX_CRYPTO_EC_KEY_PAIR_GENERATE, a saída aponta para NX_CRYPTO_EXTENDED_OUTPUT estrutura e o par de chaves é copiado para nx_crypto_extended_output_data. Quando a operação é NX_CRYPTO_DH_SETUP, a chave pública é devolvida a nx_crypto_extended_output_data. Quando a operação é NX_CRYPTO_DH_KEY_PAIR_IMPORT, a entrada aponta para a chave pública e pontos-chave para a chave privada. Quando a operação é NX_CRYPTO_DH_PRIVATE_KEY_EXPORT, a chave privada é copiada para nx_crypto_extended_output_data. Quando a operação é NX_CRYPTO_DH_CALCULATE, a entrada aponta para a chave pública remota e o segredo partilhado é copiado para nx_crypto_extended_output_data.

### <a name="parameters"></a>Parâmetros

- **op** Tipo de operação para realizar. A operação válida é:
  - *NX_CRYPTO_EC_CURVE_SET*
  - *NX_CRYPTO_DH_SETUP*
  - *NX_CRYPTO_DH_CALCULATE*
  - *NX_CRYPTO_DH_KEY_PAIR_IMPOPRT*
  - *NX_CRYPTO_DH_KEY_PAIR_GENERATE*
  - *NX_CRYPTO_DH_PRIVATE_KEY_EXPORT*
- **cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **método** Ponteiro para o método cripto ECDH válido. O método cripto utilizado aqui deve ser o mesmo utilizado no _ *nx_crypto_method_ecdh_init().*
- **chave** Quando a operação é NX_CRYPTO_DH_IMPORT_KEY_PAIR, este campo aponta para chave privada. Caso contrário, este campo não é utilizado para o ECDH.
- **key_size_in_bits** Tamanho da chave, em pedaços.
- **entrada** Quando a operação é NX_CRYPTO_EC_CURVE_SET, este campo aponta para o método cripto da Curva Elíptica. Quando a operação é NX_CRYPTO_DH_SETUP, este campo não é usado. Quando a operação é NX_CRYPTO_DH_CALCULATE, este campo aponta para um tampão contendo dados de texto de entrada. Quando a operação é NX_CRYPTO_DH_IMPORT_KEY_PAIR, este campo aponta para a chave pública.
- **input_length_in_byte** Tamanho dos dados de entrada, bytes.
- **iv_ptr** Este campo não é usado para o ECDH.
- **saída** Quando a operação é NX_CRYPTO_EC_CURVE_SET ou NX_CRYPTO_DH_IMPORT_KEY_PAIR, este campo não é utilizado. Quando a operação é NX_CRYPTO_DH_SETUP, este campo aponta para a área de memória para a chave pública gerada do ECDH. Quando a operação é NX_CRYPTO_DH_CALCULATE, este campo aponta para a área de memória para o segredo partilhado do ECDH gerado.
- **output_length_in_byte** Tamanho do tampão de saída em bytes.
- **crypto_metadata** Ponteiro para o bloco de controlo do ECDH utilizado em *_nx_crypto_method_ecdh_init()*.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para o ECDH, o tamanho dos metadados deve ser *do tamanho (NX_CRYPTO_ECDH)*
- **packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação ECDH.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Algoritmo ECDH inválido sendo especificado.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamanho do tampão de saída inválido.

## <a name="_nx_crypto_method_ecdh_cleanup"></a>_nx_crypto_method_ecdh_cleanup

Limpe o bloco de controlo do ECDH.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_ecdh_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

A aplicação chama a esta função para limpar o bloco de controlo do ECDH depois de determinar que esta sessão do ECDH já não é necessária.

### <a name="parameters"></a>Parâmetros

- **crypto_metadata** Ponteiro para o bloco de controlo do ECDH utilizado em *_nx_crypto_method_ecdh_init()*.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão do ECDH.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.

## <a name="_nx_crypto_method_ecdsa_init"></a>_nx_crypto_method_ecdsa_init

Inicializa o bloco de controlo cripto do ECDSA

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_ecdsa_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Esta função inicializa o bloco de controlo ECDSA com a corda de chave dada. Uma vez iniciada a inicial do bloco de controlo ECDSA, a operação subsequente do ECDSA deve utilizar o mesmo bloco de controlo.

A aplicação pode criar vários blocos de controlo ECDSA, cada um representa uma sessão. A inicialização do bloco de controlo ECDSA inicia uma nova sessão de computação de haxixe. A re-inicialização do bloco de controlo do ECDSA abandona a sessão atual e protagoniza uma nova.

### <a name="parameters"></a>Parâmetros

- **método** Ponteiro para um bloco de controlo de método cripto ECDSA válido. Estão disponíveis os seguintes métodos cripto pré-definidos:
  - *crypto_method_ecdsa*
- **chave** Este campo não é utilizado para o ECDSA.
- **key_size_in_bits** Este campo não é utilizado para o ECDSA.
- **cabo** Este serviço devolve uma manípula ao autor da chamada. O cabo é dependente da implementação e não está a ser utilizado nesta implementação. O pedido deve passar NU PARA o cabo.
- **crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo ECDSA. O endereço inicial do espaço de memória deve estar alinhado a 4 byte.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para o ECDSA, o tamanho dos metadados deve ser *de tamanho (NX_CRYPTO_ECDSA)*

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo ECDSA com a chave e o tamanho da chave.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.

## <a name="_nx_crypto_method_ecdsa_operation"></a>_nx_crypto_method_ecdsa_operation

Realizar operação ECDSA

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Description

Esta função executa a operação ECDSA. O bloco de controlo ECDSA deve ter sido inicializado com _ *nx_crypto_method_ecdsa_init()*. O algoritmo ECDSA a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*

Quando a operação é NX_CRYPTO_EC_CURVE_SET, a entrada aponta para o método cripto da curva elíptica. Quando a operação é NX_CRYPTO_EC_KEY_PAIR_GENERATE, a saída aponta para NX_CRYPTO_EXTENDED_OUTPUT estrutura e o par de chaves é copiado para nx_crypto_extended_output_data.

### <a name="parameters"></a>Parâmetros

- **op** Tipo de operação para realizar. A operação válida é:
  - *NX_CRYPTO_EC_CURVE_SET*
  - *NX_CRYPTO_AUTHENTICATE*
  - *NX_CRYPTO_VERIFY*
- **cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **método** Ponteiro para o método cripto ECDSA válido. O método cripto utilizado aqui deve ser o mesmo utilizado no _ *nx_crypto_method_ecdsa_init().*
- **chave** Aponta para a chave quando a operação é NX_CRYPTO_VERIFY. Não existem restrições ao tampão-chave. Este campo não é utilizado para outros valores de op.
- **key_size_in_bits** Tamanho da chave, em pedaços.
- **entrada** Quando a operação é NX_CRYPTO_EC_CURVE_SET, este campo aponta para o método cripto da Curva Elíptica. Caso contrário, este campo aponta para um tampão que contém dados de texto de entrada.
- **input_length_in_byte** Tamanho dos dados de entrada, bytes.
- **iv_ptr** Este campo não é utilizado para o ECDSA.
- **saída** Quando a operação é NX_CRYPTO_EC_CURVE_SET, este campo não é usado. Quando a operação é NX_CRYPTO_AUTHENTICATE, este campo aponta para a área de memória para a assinatura gerada do ECDSA. Quando a operação é NX_CRYPTO_VERIFY, este campo aponta para a área de memória para a assinatura verificada do ECDSA.
- **output_length_in_byte** Tamanho do tampão de saída em bytes.
- **crypto_metadata** Ponteiro para o bloco de controlo ECDSA utilizado em *_nx_crypto_method_ecdsa_init()*.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para o ECDSA, o tamanho dos metadados deve ser *do tamanho (NX_CRYPTO_ECDSA)*
- **packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação ECDSA.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Algoritmo ECDSA inválido sendo especificado.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamanho do tampão de saída inválido.

## <a name="_nx_crypto_method_ecdsa_cleanup"></a>_nx_crypto_method_ecdsa_cleanup

Limpe o bloco de controlo do ECDSA.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_ecdsa_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

A aplicação chama a esta função para limpar o bloco de controlo ECDSA depois de determinar que esta sessão do ECDSA já não é necessária.

### <a name="parameters"></a>Parâmetros

- **crypto_metadata** Ponteiro para o bloco de controlo ECDSA utilizado em *_nx_crypto_method_ecdsa_init()*.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão do ECDSA.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.

## <a name="_nx_crypto_method_hmac_md5_init"></a>_nx_crypto_method_hmac_md5_init

Inicializa o bloco de controlo cripto MD5 HMAC MD5

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_hmac_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Esta função inicializa o bloco de controlo HMAC MD5 com a chave dada. Uma vez iniciada a inicialidade do bloco de controlo HMAC MD5, a operação subsequente do HMAC MD5 deve utilizar o mesmo bloco de comando.

A aplicação pode criar vários blocos de controlo HMAC MD5, cada um representa uma sessão. A inicialização do bloco de controlo HMAC MD5 inicia uma nova sessão de computação de haxixe. A re-inicialização do bloco de controlo HMAC MD5 abandona a sessão atual e protagoniza uma nova.

### <a name="parameters"></a>Parâmetros

- **método** Ponteiro para um bloco de controlo de método cripto MD5 válido HMAC MD5.
Estão disponíveis os seguintes métodos cripto pré-definidos:
  - *crypto_method_hmac_md5*
- **chave** Aponta para a chave. Não existem restrições ao tampão-chave.
- **key_size_in_bits** Tamanho da chave, em pedaços.
- **cabo** Este serviço devolve uma manípula ao autor da chamada. O cabo é dependente da implementação e não está a ser utilizado nesta implementação. O pedido deve passar NU PARA o cabo.
- **crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo HMAC MD5. O endereço inicial do espaço de memória deve estar alinhado a 4 byte.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para o HMAC MD5, o tamanho dos metadados deve ser *de tamanho (NX_CRYPTO_MD5_HMAC)*

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo HMAC MD5 com a chave e o tamanho da chave.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.

## <a name="_nx_crypto_method_hmac_md5_operation"></a>_nx_crypto_method_hmac_md5_operation

Efetuar uma operação de hash HMAC MD5.

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Description

Esta função executa o funcionamento do hash HMAC MD5. O bloco de controlo HMAC MD5 deve ter sido inicializado com _ *nx_crypto_method_hmac_md5_init()*. O algoritmo HMAC MD5 a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*

Para a operação *de NX_CRYPTO_HASH_CALCULATE* final, o tamanho do tampão de saída deve ser de 16 bytes.

Esta operação não guarda informações estatais e não altera o material chave no bloco de controlo HMAC MD5.

### <a name="parameters"></a>Parâmetros

- **op** Tipo de operação para realizar. A operação válida é:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **método** Ponteiro para o método de cripto HMAC MD5 válido. O método cripto utilizado aqui deve ser o mesmo utilizado no *nx_crypto_method_hmac_md5_init().*
- **chave** Aponta para a chave. Não existem restrições ao tampão-chave.
- **key_size_in_bits** Tamanho da chave, em pedaços.
- **input_data** Aponta para um tampão que contém dados de texto de entrada. Não existem restrições ao tampão de entrada.
- **input_data_size** Tamanho dos dados de entrada, bytes.
- **iv_ptr** Este campo não é utilizado para HMAC MD5.
- **iv_size** Este campo não é utilizado para HMAC MD5.
- **output_buffer** Ponteiro para a área de memória para o haxixe HMAC MD5 gerado.
- **output_buffer_size** Tamanho do tampão de saída em bytes.
- **crypto_metadata** Ponteiro para o bloco de controlo HMAC MD5 utilizado em *_nx_crypto_method_hmac_md5_init()*.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para o HMAC MD5, o tamanho dos metadados deve ser *do tamanho (NX_CRYPTO_MD5_HMAC)*
- **packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação HMAC MD5.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Algoritmo HMAC MD5 inválido sendo especificado.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamanho do tampão de saída inválido.

## <a name="_nx_crypto_method_hmac_sha1_init"></a>_nx_crypto_method_hmac_sha1_init

Inicializa o bloco de controlo cripto HMAC SHA1

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_hmac_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Esta função inicializa o bloco de controlo HMAC SHA1 com a chave dada. Uma vez iniciada a inicialidade do bloco de comandoS HMAC SHA1, a operação subsequente do HMAC SHA1 deve utilizar o mesmo bloco de comando.

A aplicação pode criar vários blocos de controlo HMAC SHA1, cada um representa uma sessão. A inicialização do bloco de controlo HMAC SHA1 inicia uma nova sessão de computação de haxixe. A re-inicialização do bloco de controlo HMAC SHA1 abandona a sessão atual e protagoniza uma nova.

### <a name="parameters"></a>Parâmetros

- **método** Ponteiro para um bloco de controlo de método cripto HMAC SHA1 válido. Estão disponíveis os seguintes métodos cripto pré-definidos:
  - *crypto_method_hmac_sha1*
- **chave** Aponta para a chave. Não existem restrições ao tampão-chave.
- **key_size_in_bits** Tamanho da chave, em pedaços.
- **cabo** Este serviço devolve uma manípula ao autor da chamada. O cabo é dependente da implementação e não está a ser utilizado nesta implementação. O pedido deve passar NU PARA o cabo.
- **crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo HMAC SHA1. O endereço inicial do espaço de memória deve estar alinhado a 4 byte.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para o HMAC SHA1, o tamanho dos metadados deve ser *de tamanho (NX_CRYPTO_SHA1_HMAC)*

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo HMAC SHA1 com a chave e o tamanho da chave.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.

## <a name="_nx_crypto_method_hmac_sha1_operation"></a>_nx_crypto_method_hmac_sha1_operation

Realizar a operação de haxixe HMAC SHA1

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Description

Esta função executa o funcionamento do hash HMAC SHA1. O bloco de controlo HMAC SHA1 deve ter sido inicializado com _ *nx_crypto_method_hmac_sha1_init()*. O algoritmo HMAC SHA1 a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*

Para a operação *final NX_CRYPTO_HASH_CALCULATE,* o tamanho do tampão de saída deve ser de 20 bytes.

### <a name="parameters"></a>Parâmetros

- **op** Tipo de operação para realizar. A operação válida é:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **método** Ponteiro para o método de cripto HMAC SHA1 válido. O método cripto utilizado aqui deve ser o mesmo utilizado no _ *nx_crypto_method_hmac_sha1_init().*
- **chave** Aponta para a chave. Não existem restrições ao tampão-chave.
- **key_size_in_bits** Tamanho da chave, em pedaços.
- **input_data** Aponta para um tampão que contém dados de texto de entrada. Não existem restrições ao tampão de entrada.
- **input_data_size** Tamanho dos dados de entrada, bytes.
- **iv_ptr** Este campo não é utilizado para hmac SHA1.
- **iv_size** Este campo não é utilizado para hmac SHA1.
- **output_buffer** Ponteiro para a área de memória para o haxixe HMAC SHA1 gerado.
- **output_buffer_size** Tamanho do tampão de saída em bytes.
- **crypto_metadata** Ponteiro para o bloco de controlo HMAC SHA1 utilizado em *_nx_crypto_method_hmac_sha1_init()*.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para o HMAC SHA1, o tamanho dos metadados deve ser *do tamanho (NX_CRYPTO_SHA1_HMAC)*
- **packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação HMAC SHA1.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Algoritmo HMAC SHA1 inválido sendo especificado.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamanho do tampão de saída inválido.

## <a name="_nx_crypto_method_hmac_sha1_cleanup"></a>_nx_crypto_method_hmac_sha1_cleanup

Limpe o bloco de controlo HMAC SHA1.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_hmac_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

A aplicação chama a esta função para limpar o bloco de controlo HMAC SHA1 depois de determinar que esta sessão HMAC SHA1 já não é necessária.

### <a name="parameters"></a>Parâmetros

- **crypto_metadata** Ponteiro para o bloco de controlo HMAC SHA1 utilizado em *_nx_crypto_method_hmac_sha1_init()*.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão HMAC SHA1.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.

## <a name="_nx_crypto_method_hmac_sha256_init"></a>_nx_crypto_method_hmac_sha256_init

Inicializa o bloco de controlo cripto HMAC SHA256

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_hmac_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Esta função inicializa o bloco de controlo HMAC SHA256 com a chave dada. Uma vez iniciada a inicialidade do bloco de comando HMAC SHA256, a operação subsequente do HMAC SHA256 deve utilizar o mesmo bloco de comando.

A aplicação pode criar vários blocos de controlo HMAC SHA256, cada um representa uma sessão. A inicialização do bloco de controlo HMAC SH256 inicia uma nova sessão de computação de haxixe. A re-inicialização do bloco de controlo HMAC SHA256 abandona a sessão atual e protagoniza uma nova com uma nova chave.

### <a name="parameters"></a>Parâmetros

- **método** Ponteiro para um bloco de controlo de método cripto HMAC 256 válido. Estão disponíveis os seguintes métodos cripto pré-definidos:
  - *crypto_method_hmac_sha224*
  - *crypto_method_hmac_sha256*
- **chave** Aponta para a chave. Não existem restrições ao tampão-chave.
- **key_size_in_bits** Tamanho da chave, em pedaços.
- **cabo** Este serviço devolve uma manípula ao autor da chamada. O cabo é dependente da implementação e não está a ser utilizado nesta implementação. O pedido deve passar NU PARA o cabo.
- **crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo HMAC SHA256. O endereço inicial do espaço de memória deve estar alinhado a 4 byte.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para o HMAC SHA256, o tamanho dos metadados deve ser *de tamanho (NX_CRYTPO_SHA256_HMAC)*

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo HMAC SHA256 com a chave e o tamanho da chave.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.

## <a name="_nx_crypto_method_hmac_sha256_operation"></a>_nx_crypto_method_hmac_sha256_operation

Executar a operação de haxixe HMAC SHA256

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Description

Esta função executa o funcionamento do hash HMAC SHA256. O bloco de controlo HMAC SHA256 deve ter sido inicializado com _ *nx_crypto_method_hmac_sha256_init()*. O algoritmo HMAC SHA256 a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*

Para a operação *de NX_CRYPTO_HASH_CALCULATE* final, o tamanho do tampão de saída deve ser de 32 bytes para SHA256, ou 28 bytes para SHA224.

### <a name="parameters"></a>Parâmetros

- **op** Tipo de operação para realizar. A operação válida é:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **método** Ponteiro para o método de cripto HMAC SHA256 válido. O método cripto utilizado aqui deve ser o mesmo utilizado no _ *nx_crypto_method_hmac_sha256_init().*
- **chave** Aponta para a chave. Não existem restrições ao tampão-chave.
- **key_size_in_bits** Tamanho da chave, em pedaços.
- **input_data** Aponta para um tampão que contém dados de texto de entrada. Não existem restrições ao tampão de entrada.
- **input_data_size** Tamanho dos dados de entrada, bytes.
- **iv_ptr** Este campo não é utilizado para HMAC SHA256.
- **iv_size** Este campo não é utilizado para HMAC SHA256.
- **output_buffer** Ponteiro para a área de memória para o haxixe HMAC SHA256 gerado.
- **output_buffer_size** Tamanho do tampão de saída em bytes.
- **crypto_metadata** Ponteiro para o bloco de controlo HMAC SHA256 utilizado em *_nx_crypto_method_hmac_sha256_init()*.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para o HMAC SHA256, o tamanho dos metadados deve ser *do tamanho (NX_CRYPTO_SHA256_HMAC)*
- **packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação HMAC SHA256.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Algoritmo HMAC SHA256 inválido sendo especificado.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamanho do tampão de saída inválido.

## <a name="_nx_crypto_method_hmac_sha256_cleanup"></a>_nx_crypto_method_hmac_sha256_cleanup

Limpe o bloco de controlo HMAC SHA256.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_hmac_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

A aplicação chama a esta função para limpar o bloco de controlo HMAC SHA256 depois de determinar que esta sessão HMAC SHA256 já não é necessária.

### <a name="parameters"></a>Parâmetros

- **crypto_metadata** Ponteiro para o bloco de controlo HMAC SHA256 utilizado em *_nx_crypto_method_hmac_sha256_init()*.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão HMAC SHA256.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.

## <a name="_nx_crypto_method_hmac_sha512_init"></a>_nx_crypto_method_hmac_sha512_init

Inicializa o bloco de controlo cripto HMAC SHA512

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_hmac_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Esta função inicializa o bloco de controlo HMAC SHA512 com a chave dada. Uma vez iniciada a inicialidade do bloco de comandoS HMAC SHA512, a operação subsequente do HMAC SHA512 deve utilizar o mesmo bloco de comando.

A aplicação pode criar vários blocos de controlo HMAC SHA512, cada um representa uma sessão. A inicialização do bloco de controlo HMAC SH512 inicia uma nova sessão de computação de haxixe. A re-inicialização do bloco de controlo HMAC SHA512 abandona a sessão atual e protagoniza uma nova com uma nova chave.

### <a name="parameters"></a>Parâmetros

- **método** Ponteiro para um bloco de controlo de método cripto HMAC SHA512 válido. Estão disponíveis os seguintes métodos cripto pré-definidos:
  - *crypto_method_hmac_sha384*
  - *crypto_method_hmac_sha512*
- **chave** Aponta para a chave. Não existem restrições ao tampão-chave.
- **key_size_in_bits** Tamanho da chave, em pedaços.
- **cabo** Este serviço devolve uma manípula ao autor da chamada. O cabo é dependente da implementação e não está a ser utilizado nesta implementação. O pedido deve passar NU PARA o cabo.
- **crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo HMAC SHA512. O endereço inicial do espaço de memória deve estar alinhado a 4 byte.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para o HMAC SHA512, o tamanho dos metadados deve ser *de tamanho (NX_CRYPTO_SHA512_HMAC)*

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo HMAC SHA512 com a chave e o tamanho da chave.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.

## <a name="_nx_crypto_method_hmac_sha512_operation"></a>_nx_crypto_method_hmac_sha512_operation

Executar a operação de haxixe HMAC SHA512

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Description

Esta função executa o funcionamento do hash HMAC SHA512. O bloco de controlo HMAC SHA512 deve ter sido inicializado com _ *nx_crypto_method_hmac_sha512_init()*. O algoritmo HMAC SHA512 a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*

Para a operação *de NX_CRYPTO_HASH_CALCULATE* final, o tamanho do tampão de saída deve ser de 64 bytes para SHA512, ou 48 bytes para SHA384.

### <a name="parameters"></a>Parâmetros

- **op** Tipo de operação para realizar. A operação válida é:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **método** Ponteiro para o método de cripto HMAC SHA512 válido. O método cripto utilizado aqui deve ser o mesmo utilizado no _ *nx_crypto_method_hmac_sha512_init().*
- **chave** Aponta para a chave. Não existem restrições ao tampão-chave.
- **key_size_in_bits** Tamanho da chave, em pedaços.
- **input_data** Aponta para um tampão que contém dados de texto de entrada. Não existem restrições ao tampão de entrada.
- **input_data_size** Tamanho dos dados de entrada, bytes.
- **iv_ptr** Este campo não é utilizado para hmac SHA512.
- **iv_size** Este campo não é utilizado para hmac SHA512.
- **output_buffer** Ponteiro para a área de memória para o haxixe HMAC SHA512 gerado.
- **output_buffer_size** Tamanho do tampão de saída em bytes.
- **crypto_metadata** Ponteiro para o bloco de controlo HMAC SHA512 utilizado em *_nx_crypto_method_hmac_sha512_init()*.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para o HMAC SHA512, o tamanho dos metadados deve ser *do tamanho (NX_CRYPTO_SHA512_HMAC)*
- **packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação HMAC SHA512.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Algoritmo HMAC SHA512 inválido sendo especificado.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamanho do tampão de saída inválido.

## <a name="_nx_crypto_method_hmac_sha512_cleanup"></a>_nx_crypto_method_hmac_sha512_cleanup

Limpe o bloco de controlo HMAC SHA512.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_hmac_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

A aplicação chama a esta função para limpar o bloco de controlo HMAC SHA512 depois de determinar que esta sessão HMAC SHA512 já não é necessária.

### <a name="parameters"></a>Parâmetros

- **crypto_metadata** Ponteiro para o bloco de controlo HMAC SHA512 utilizado em *_nx_crypto_method_hmac_sha512_init()*.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão HMAC SHA512.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.

### <a name="example"></a>Exemplo 

## <a name="_nx_crypto_method_md5_init"></a>_nx_crypto_method_md5_init

Inicializa o bloco de controlo cripto MD5

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Esta função inicializa o bloco de controlo MD5 com a chave dada. Uma vez iniciada a inicial do bloco de controlo MD5, a operação MD5 subsequente deve utilizar o mesmo bloco de comando.

A aplicação pode criar vários blocos de controlo MD5, cada um representa uma sessão. A inicialização do bloco de controlo MD5 inicia uma nova sessão de computação de haxixe. A re-inicialização do bloco de controlo MD5 abandona a sessão atual e protagoniza uma nova.

### <a name="parameters"></a>Parâmetros

- **método** Ponteiro para um bloco de controlo de método cripto MD5 válido. Estão disponíveis os seguintes métodos cripto pré-definidos:
  - *crypto_method_md5*
- **chave** Este campo não é utilizado para MD5.
- **key_size_in_bits** Este campo não é usado para MD5
- **cabo** Este serviço devolve uma manípula ao autor da chamada. O cabo é dependente da implementação e não está a ser utilizado nesta implementação. O pedido deve passar NU PARA o cabo.
- **crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo MD5. O endereço inicial do espaço de memória deve estar alinhado a 4 byte.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para mD5, o tamanho dos metadados deve ser *de tamanho (NX_CRYPTO_MD5)*

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo MD5 com a chave e o tamanho da chave.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.

### <a name="example"></a>Exemplo

## <a name="_nx_crypto_method_md5_operation"></a>_nx_crypto_method_md5_operation

Efetuar uma operação de haxixe MD5.

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Description

Esta função executa o funcionamento do hash MD5. O bloco de controlo MD5 deve ter sido inicializado com _ *nx_crypto_method_md5_init()*. O algoritmo MD5 a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*

Para a operação *de NX_CRYPTO_HASH_CALCULATE* final, o tamanho do tampão de saída deve ser de 16 bytes.

Esta operação não guarda informações estatais e não altera o material chave no bloco de comandoS MD5.

### <a name="parameters"></a>Parâmetros

- **op** Tipo de operação para realizar. A operação válida é:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **método** Ponteiro para o método de cripto MD5 válido. O método cripto utilizado aqui deve ser o mesmo utilizado no _ *nx_crypto_method_md5_init().*
- **input_data** Aponta para um tampão que contém dados de texto de entrada. Não existem restrições ao tampão de entrada.
- **input_data_size** Tamanho dos dados de entrada, bytes.
- **iv_ptr** Este campo não é utilizado para MD5.
- **iv_size** Este campo não é utilizado para MD5.
- **output_buffer** Ponteiro para a área de memória para o hash MD5 gerado.
- **output_buffer_size** Tamanho do tampão de saída em bytes. Para MD5 o tamanho do tampão deve ser de 16 bytes.
- **crypto_metadata** Ponteiro para o bloco de controlo MD5 utilizado em *_nx_crypto_method_md5_init()*.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para mD5, o tamanho dos metadados deve *ser do tamanho (NX_CRYPTO_MD5)*
- **packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação MD5.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) algoritmo MD5 inválido sendo especificado.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamanho do tampão de saída inválido.

## <a name="_nx_crypto_method_md5_cleanup"></a>_nx_crypto_method_md5_cleanup

Limpe o bloco de controlo MD5.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_md5_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

A aplicação chama esta função para limpar o bloco de controlo MD5 depois de determinar que esta sessão MD5 já não é necessária.

### <a name="parameters"></a>Parâmetros

- **crypto_metadata** Ponteiro para o bloco de controlo MD5 utilizado em *_nx_crypto_method_md5_init()*.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão MD5.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.

## <a name="_nx_crypto_method_sha1_init"></a>_nx_crypto_method_sha1_init

Inicializa o bloco de controlo cripto SHA1

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Esta função inicializa o bloco de controlo SHA1 com a chave dada. Uma vez iniciada a inicial do bloco de controlo SHA1, a operação SUBSEQUENTE SHA1 deve utilizar o mesmo bloco de comando.

A aplicação pode criar vários blocos de controlo SHA1, cada um representa uma sessão. A inicialização do bloco de controlo SHA1 inicia uma nova sessão de computação de haxixe. A re-inicialização do bloco de controlo SHA1 abandona a sessão atual e protagoniza uma nova.

### <a name="parameters"></a>Parâmetros

- **método** Ponteiro para um bloco de controlo de método cripto SHA1 válido. Estão disponíveis os seguintes métodos cripto pré-definidos:
  - *crypto_method_sha1*
- **chave** Este campo não é utilizado para SHA1.
- **key_size_in_bits** Este campo não é usado para SHA1
- **cabo** Este serviço devolve uma manípula ao autor da chamada. O cabo é dependente da implementação e não está a ser utilizado nesta implementação. O pedido deve passar NU PARA o cabo.
- **crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo SHA1. O endereço inicial do espaço de memória deve estar alinhado a 4 byte.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para SHA1, o tamanho dos metadados deve ser *de tamanho (NX_CRYPTO_SHA1)*

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo SHA1 com a chave e o tamanho da chave.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.

## <a name="_nx_crypto_method_sha1_operation"></a>_nx_crypto_method_sha1_operation

Realizar operação de haxixe SHA1

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Description

Esta função executa a operação de haxixe SHA1. O bloco de controlo SHA1 deve ter sido inicializado com _ *nx_crypto_method_sha1_init()*. O algoritmo SHA1 a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*

Para a operação *final NX_CRYPTO_HASH_CALCULATE,* o tamanho do tampão de saída deve ser de 20 bytes.

### <a name="parameters"></a>Parâmetros

- **op** Tipo de operação para realizar. A operação válida é:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **método** Ponteiro para o método cripto sha1 válido. O método cripto utilizado aqui deve ser o mesmo utilizado no *nx_crypto_method_sha1_init().*
- **input_data** Aponta para um tampão que contém dados de texto de entrada. Não existem restrições ao tampão de entrada.
- **input_data_size** Tamanho dos dados de entrada, bytes.
- **iv_ptr** Este campo não é utilizado para SHA1.
- **iv_size** Este campo não é utilizado para SHA1.
- **output_buffer** Ponteiro para a área de memória para o haxixe SHA1 gerado.
- **output_buffer_size** Tamanho do tampão de saída em bytes. Para SHA1 o tamanho do tampão deve ser de 20 bytes.
- **crypto_metadata** Ponteiro para o bloco de controlo SHA1 utilizado em *_nx_crypto_method_sha1_init()*.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para SHA1, o tamanho dos metadados deve *ser do tamanho (NX_CRYPTO_SHA1)*
- **packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação SHA1.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) algoritmo SHA1 inválido sendo especificado.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamanho do tampão de saída inválido.

### <a name="example"></a>Exemplo

## <a name="_nx_crypto_method_sha1_cleanup"></a>_nx_crypto_method_sha1_cleanup

Limpe o bloco de controlo SHA1.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

A aplicação chama a esta função para limpar o bloco de controlo SHA1 depois de determinar que esta sessão SHA1 já não é necessária.

### <a name="parameters"></a>Parâmetros

- **crypto_metadata** Ponteiro para o bloco de controlo SHA1 utilizado em *_nx_crypto_method_sha1_init()*.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão SHA1.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.

## <a name="_nx_crypto_method_sha256_init"></a>_nx_crypto_method_sha256_init

Inicializa o bloco de controlo cripto SHA256

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size)
```

### <a name="description"></a>Description

Esta função inicializa o bloco de controlo SHA256 com a chave dada. Uma vez iniciada a inicial do bloco de controlo SHA256, a operação subsequente do SHA256 deve utilizar o mesmo bloco de comando.

A aplicação pode criar vários blocos de controlo SHA256, cada um representa uma sessão. A inicialização do bloco de controlo SHA256 inicia uma nova sessão de computação de haxixe. A re-inicialização do bloco de controlo SHA256 abandona a sessão atual e protagoniza uma nova.

### <a name="parameters"></a>Parâmetros

- **método** Ponteiro para um bloco de controlo de método cripto SHA256 válido. Estão disponíveis os seguintes métodos cripto pré-definidos:
  - *crypto_method_sha256*
  - *crypto_method_sha224*
- **chave** Este campo não é utilizado para SHA256.
- **key_size_in_bits** Este campo não é usado para SHA256
- **cabo** Este serviço devolve uma manípula ao autor da chamada. O cabo é dependente da implementação e não está a ser utilizado nesta implementação. O pedido deve passar NU PARA o cabo.
- **crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo SHA256. O endereço inicial do espaço de memória deve estar alinhado a 4 byte.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para SHA256, o tamanho dos metadados deve ser *de tamanho (NX_CRYPTO_SHA256)*

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo SHA256 com a chave e o tamanho da chave.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.

## <a name="_nx_crypto_method_sha256_operation"></a>_nx_crypto_method_sha256_operation

Realizar operação de haxixe SHA256

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Description

Esta função executa a operação hash SHA256. O bloco de controlo SHA256 deve ter sido inicializado com _ ***nx_crypto_method_sha256_init()***. O algoritmo SHA256 a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*

Para a operação *de NX_CRYPTO_HASH_CALCULATE* final, o tamanho do tampão de saída deve ser de 32 bytes para SHA256, ou 28 bytes para SHA224.

### <a name="parameters"></a>Parâmetros

- **op** Tipo de operação para realizar. A operação válida é:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **método** Ponteiro para o método cripto sha256 válido. O método cripto utilizado aqui deve ser o mesmo utilizado no _ *nx_crypto_method_sha256_init().*
- **input_data** Aponta para um tampão que contém dados de texto de entrada. Não existem restrições ao tampão de entrada.
- **input_data_size** Tamanho dos dados de entrada, bytes.
- **iv_ptr** Este campo não é utilizado para SHA256.
- **iv_size** Este campo não é utilizado para SHA256.
- **output_buffer** Ponteiro para a área de memória para o haxixe SHA256 gerado.
- **output_buffer_size** Tamanho do tampão de saída em bytes. Para SHA256 o tamanho do tampão deve ser de 32 bytes. Para SHA224 o tamanho do tampão deve ser de 28 bytes.
- **crypto_metadata** Ponteiro para o bloco de controlo SHA2 utilizado em *_nx_crypto_method_sha2_init()*.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para SHA256, o tamanho dos metadados deve *ser do tamanho (NX_CRYPTO_SHA256)*
- **packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação SHA256.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Algoritmo INválido SHA256 sendo especificado.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamanho do tampão de saída inválido.

## <a name="_nx_crypto_method_sha256_cleanup"></a>_nx_crypto_method_sha256_cleanup

Limpe o bloco de controlo SHA256.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

A aplicação chama a esta função para limpar o bloco de controlo SHA256 depois de determinar que esta sessão SHA256 já não é necessária.

### <a name="parameters"></a>Parâmetros

- **crypto_metadata** Ponteiro para o bloco de controlo SHA256 utilizado em *_nx_crypto_method_sha256_init()*.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão SHA256.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.

## <a name="_nx_crypto_method_sha512_init"></a>_nx_crypto_method_sha512_init

Inicializa o bloco de controlo cripto SHA512

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Esta função inicializa o bloco de controlo SHA512 com a chave dada. Uma vez iniciada a inicial do bloco de controlo SHA512, a operação subsequente do SHA512 deve utilizar o mesmo bloco de comando.

A aplicação pode criar vários blocos de controlo SHA512, cada um representa uma sessão. A inicialização do bloco de controlo SHA512 inicia uma nova sessão de computação de haxixe. A re-inicialização do bloco de controlo SHA512 abandona a sessão atual e protagoniza uma nova.

### <a name="parameters"></a>Parâmetros

- **método** Ponteiro para um bloco de controlo de método cripto SHA512 válido. Estão disponíveis os seguintes métodos cripto pré-definidos:
  - *crypto_method_sha512*
  - *crypto_method_sha384*
- **chave** Este campo não é utilizado para SHA512.
- **key_size_in_bits** Este campo não é usado para SHA512
- **cabo** Este serviço devolve uma manípula ao autor da chamada. O cabo é dependente da implementação e não está a ser utilizado nesta implementação. O pedido deve passar NU PARA o cabo.
- **crypto_metadata** Ponteiro para um espaço de memória válido para o bloco de controlo SHA512. O endereço inicial do espaço de memória deve estar alinhado a 4 byte.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para SHA512, o tamanho dos metadados deve ser *de tamanho (NX_CRYPTO_SHA512)*

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) Iniciação bem sucedida do bloco de controlo SHA512 com a chave e o tamanho da chave.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR** (0x07) Ponteiro inválido da chave, ou crypto_metadata ou crypto_metadata_size inválidos, ou crypto_metadata não esteja alinhado com 4 bytes.

## <a name="_nx_crypto_method_sha512_operation"></a>_nx_crypto_method_sha512_operation

Realizar operação de haxixe SHA512

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Description

Esta função executa a operação de haxixe SHA512. O bloco de controlo SHA512 deve ter sido inicializado com _ *nx_crypto_method_sha512_init()*. O algoritmo SHA512 a ser realizado baseia-se no algoritmo especificado no bloco de controlo do *método.*

Para a operação *de NX_CRYPTO_HASH_CALCULATE* final, o tamanho do tampão de saída deve ser de 64 bytes para SHA512, ou 48 bytes para SHA384.

### <a name="parameters"></a>Parâmetros

- **op** Tipo de operação para realizar. A operação válida é:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **cabo** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **método** Ponteiro para o método cripto sha512 válido. O método cripto utilizado aqui deve ser o mesmo utilizado no _ *nx_crypto_method_sha512_init().*
- **input_data** Aponta para um tampão que contém dados de texto de entrada. Não existem restrições ao tampão de entrada.
- **input_data_size** Tamanho dos dados de entrada, bytes.
- **iv_ptr** Este campo não é utilizado para SHA512.
- **iv_size** Este campo não é utilizado para SHA512.
- **output_buffer** Ponteiro para a área de memória para o haxixe SHA512 gerado.
- **output_buffer_size** Tamanho do tampão de saída em bytes. Para SHA512 o tamanho do tampão deve ser de 64 bytes. Para SHA384 o tamanho do tampão deve ser de 48 bytes.
- **crypto_metadata** Ponteiro para o bloco de controlo SHA512 utilizado em *_nx_crypto_method_sha512_init()*.
- **crypto_metadata_size** Tamanho, em bytes, da área de crypto_metadata. Para SHA512, o tamanho dos metadados deve *ser do tamanho (NX_CRYPTO_SHA512)*
- **packet_ptr** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.
- **nx_crypto_hw_process_callback** Este campo não é utilizado na implementação de software da biblioteca NetX Crypto. Todos os valores passados são silenciosamente ignorados.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) executou com sucesso a operação SHA512.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido ou comprimento inválido.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Algoritmo INválido SHA512 sendo especificado.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Tamanho do tampão de saída inválido.

## <a name="_nx_crypto_method_sha512_cleanup"></a>_nx_crypto_method_sha512_cleanup

Limpe o bloco de controlo SHA512.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

A aplicação chama a esta função para limpar o bloco de controlo SHA512 depois de determinar que esta sessão SHA512 já não é necessária.

### <a name="parameters"></a>Parâmetros

- **crypto_metadata** Ponteiro para o bloco de controlo SHA512 utilizado em *_nx_crypto_method_sha512_init()*.

### <a name="return-values"></a>Valores de devolução

- **NX_CRYPTO_SUCCESS** (0x00) limpou com sucesso a sessão SHA512.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) A biblioteca cripto está em estado inválido e não pode ser utilizada.