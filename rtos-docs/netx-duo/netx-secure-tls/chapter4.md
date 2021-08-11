---
title: Capítulo 4 - Descrição dos serviços Azure RTOS NetX Secure
description: Este capítulo contém uma descrição de todos os serviços NetX Secure (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b10260778f7f5e1a5bd0a38aded2339008b066cca77f2439a5881d28a0489524
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797760"
---
# <a name="chapter-4---description-of-azure-rtos-netx-secure-services"></a>Capítulo 4 - Descrição dos serviços Azure RTOS NetX Secure

Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX Secure (listados abaixo) por ordem alfabética.

Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pela macro **NX_SECURE_DISABLE_ERROR_CHECKING** que é utilizada para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

- [nx_secure_crypto_table_self_test](#nx_secure_crypto_table_self_test)
  - Realize self_test sobre os métodos cripto
- [nx_secure_module_hash_compute](#nx_secure_module_hash_compute)
  - Valor do haxixe computativo usando user_supplied função de haxixe
- [nx_secure_tls_active_certificate_set](#nx_secure_tls_active_certificate_set)
  - Definir o certificado de identidade ativa para uma Sessão TLS NetX Secure
- [nx_secure_tls_client_psk_set](#nx_secure_tls_client_psk_set)
  - Desagure uma chave de Pre_Shared para uma sessão de clientes NetX Secure TLS
- [nx_secure_tls_initialize](#nx_secure_tls_initialize)
  - Inicializa o módulo NetX Secure TLS]
- [nx_secure_tls_local_certificate_add](#nx_secure_tls_local_certificate_add)
  - Adicione um certificado local à Sessão NetX Secure TLS
- [nx_secure_tls_local_certificate_find](#nx_secure_tls_local_certificate_find)
  - Encontre um certificado local numa Sessão De TLS Segura NetX por Nome Comum
- [nx_secure_tls_local_certificate_remove](#nx_secure_tls_local_certificate_remove)
  - Remover certificado local da Sessão NetX Secure TLS
- [nx_secure_tls_metadata_size_calculate](#nx_secure_tls_metadata_size_calculate)
  - Calcular o tamanho dos metadados criptográficos para uma Sessão de TLS NetX Secure
- [nx_secure_tls_packet_allocate](#nx_secure_tls_packet_allocate)
  - Aloque um pacote para uma Sessão NetX Secure TLS
- [nx_secure_tls_psk_add](#nx_secure_tls_psk_add)
  - Adicione uma chave Pre_Shared a uma Sessão De TLS Segura NetX
- [nx_secure_tls_remote_certificate_allocate](#nx_secure_tls_remote_certificate_allocate)
  - Alocar espaço para o certificado fornecido por um anfitrião remoto TLS
- [nx_secure_tls_remote_certificate_buffer_allocate](#nx_secure_tls_remote_certificate_buffer_allocate)
  - Alocar espaço para todos os certificados fornecidos por um anfitrião remoto TLS
- [nx_secure_tls_remote_certificate_free_all](#nx_secure_tls_remote_certificate_free_all)
  - Espaço gratuito atribuído para certificados de entrada
- [nx_secure_tls_server_certificate_add](#nx_secure_tls_server_certificate_add)
  - Adicione um certificado especificamente para servidores TLS usando um identificador numérico
- [nx_secure_tls_server_certificate_find](#nx_secure_tls_server_certificate_find)
  - Encontre um certificado usando um identificador numérico
- [nx_secure_tls_server_certificate_remove](#nx_secure_tls_server_certificate_remove)
  - Remova um certificado de servidor local usando um identificador numérico
- [nx_secure_tls_session_certificate_callback_set](#nx_secure_tls_session_certificate_callback_set)
  - Configurar uma chamada para o TLS usar para validação adicional de certificados
- [nx_secure_tls_session_client_callback_set](#nx_secure_tls_session_client_callback_set)
  - Configurar uma chamada para o TLS invocar no início de um aperto de mão do Cliente TLS
- [nx_secure_tls_session_x509_client_verify_configure](#nx_secure_tls_session_x509_client_verify_configure)
  - Ativar a verificação do cliente X.509 e alocar espaço para certificados de cliente
- [nx_secure_tls_session_client_verify_disable](#nx_secure_tls_session_client_verify_disable)
  - Desativar a autenticação do certificado do cliente para uma Sessão TLS Segura NetX
- [nx_secure_tls_session_client_verify_enable](#nx_secure_tls_session_client_verify_enable)
  - Ativar a autenticação do certificado de cliente para uma Sessão TLS Segura NetX
- [nx_secure_tls_session_create](#nx_secure_tls_session_create)
  - Criar uma Sessão TLS Segura NetX para comunicações seguras
- [nx_secure_tls_session_delete](#nx_secure_tls_session_delete)
  - Excluir uma Sessão de TLS Segura NetX
- [nx_secure_tls_session_end](#nx_secure_tls_session_end)
  - Termine uma sessão ativa de TLS Do NetX Secure
- [nx_secure_tls_session_packet_buffer_set](#nx_secure_tls_session_packet_buffer_set)
  - Descreva o tampão de montagem do pacote para uma Sessão TLS NetX Secure
- [nx_secure_tls_session_protocol_version_override](#nx_secure_tls_session_protocol_version_override)
  - Anular a versão padrão do protocolo TLS para uma Sessão De TLS Do NetX Secure
- [nx_secure_tls_session_receive](#nx_secure_tls_session_receive)
  - Receber dados de uma Sessão De TLS Segura NetX
- [nx_secure_tls_session_renegotiate_callback_set](#nx_secure_tls_session_renegotiate_callback_set)
  - Atribua uma chamada que será invocada no início de uma renegociação da sessão
- [nx_secure_tls_session_renegotiate](#nx_secure_tls_session_renegotiate)
  - Inicie um aperto de mão de renegociação de sessão com o anfitrião remoto
- [nx_secure_tls_session_reset](#nx_secure_tls_session_reset)
  - Limpe e reponha uma Sessão de TLS De Segurança NetX
- [nx_secure_tls_session_send](#nx_secure_tls_session_send)
  - Enviar dados através de uma Sessão De TLS Segura NetX
- [nx_secure_tls_session_server_callback_set](#nx_secure_tls_session_server_callback_set)
  - Configurar uma chamada para o TLS invocar no início de um aperto de mão do TLS Server
- [nx_secure_tls_session_sni_extension_parse](#nx_secure_tls_session_sni_extension_parse)
  - Parse uma extensão de indicação de nome do servidor (SNI) recebida de um cliente TLS
- [nx_secure_tls_session_sni_extension_set](#nx_secure_tls_session_sni_extension_set)
  - Desa estade um nome DNS de extensão de extensão de nome do servidor (SNI) para enviar para um servidor remoto
- [nx_secure_tls_session_start](#nx_secure_tls_session_start)
  - Inicie uma Sessão De TLS Segura NetX
- [nx_secure_tls_session_time_function_set](#nx_secure_tls_session_time_function_set)
  - Atribua uma função de marcação de tempo a uma Sessão TLS Segura NetX
- [nx_secure_tls_trusted_certificate_add](#nx_secure_tls_trusted_certificate_add)
  - Adicionar certificado fidedigno à Sessão TLS Do NetX Secure
- [nx_secure_tls_trusted_certificate_remove](#nx_secure_tls_trusted_certificate_remove)
  - Remover certificado fidedigno da Sessão TLS Do NetX Secure
- [nx_secure_x509_certificate_initialize](#nx_secure_x509_certificate_initialize)
  - Inicializar o Certificado X.509 para NetX Secure TLS
- [nx_secure_x509_common_name_dns_check](#nx_secure_x509_common_name_dns_check)
  - Verifique o nome DNS contra o Certificado X.509
- [nx_secure_x509_crl_revocation_check](#nx_secure_x509_crl_revocation_check)
  - Verifique o Certificado X.509 com uma Lista de Revogação de Certificados (CRL)]
- [nx_secure_x509_dns_name_initialize](#nx_secure_x509_dns_name_initialize)
  - Inicialize uma estrutura de nomeS DNS X.509
- [nx_secure_x509_extended_key_usage_extension_parse](#nx_secure_x509_extended_key_usage_extension_parse)
  - Encontre e analise uma extensão de utilização estendida X.509 num certificado X.509
- [nx_secure_x509_extension_find](#nx_secure_x509_extension_find)
  - Encontre e devolva uma extensão X.509 num certificado X.509
- [nx_secure_x509_key_usage_extension_parse](#nx_secure_x509_key_usage_extension_parse)
  - Encontre e analise uma extensão de utilização da chave X.509 num certificado X.509

## <a name="nx_secure_crypto_table_self_test"></a>nx_secure_crypto_table_self_test

Realizar auto-teste nos métodos cripto

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_crypto_table_self_test(
                                  const NX_SECURE_TLS_CRYPTO *crypto_table,
                                  VOID *metadata, UINT metadata_size);
```

### <a name="description"></a>Description

Este serviço executa através do método cripto-método auto-testes para validar. O auto-teste só está disponível se a biblioteca NetX Secure for construída com o símbolo NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK definido.

Para cada método cripto suportado, o auto-teste fornece dados de entrada pré-definidos e verificado que a saída corresponde ao valor esperado pré-definido.

NetX Secure crypto self test suporta os seguintes algoritmos e tamanhos chave:

- DES: encriptação e desencriptação
- DES Triplo (3DES): encriptação e desencriptação
- AES: tamanho da chave de 128, 192, 256 bits, encriptação e desencriptação, no modo CBC e no modo de contador.
- HMAC-MD5: autenticação e computação de haxixe
- HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2-512, autenticação e computação de haxixe
- MD5: autenticação
- Função pseudoaleatória (PRF): PRF_HMAC_SHA1 e PRF_HMAC_SHA2-256
- RSA: operação rsa 1024-, 2048-, 4096-bit RSA power-modulus
- SHA1 (96- e 160 bits), SHA2 (256bit, 384bit, 512bit) autenticação

Esta função tem os vetores incorporados para os algoritmos cripto listados acima. No entanto, apenas testa os listados no *cipher_table* passaram para esta função. Por exemplo, para uma sessão de TLS utiliza apenas o TLS_RSA_WITH_AES_128_CBC_SHA cifrasuita, esta função realizará auto-teste no RSA (1024-, 2048-, 4096-bit), AES-CBC (128-bit) e SHA1.

### <a name="parameters"></a>Parâmetros

- **crypto_table** Ponteiro para a tabela cripto que está a ser usada pela sessão TLS. Esta é a mesma crypto_table a ser passada para a **_chamada nx_secure_tls_session_create()._**
- **metadados** Ponteiro para o espaço para a área de metadados de criptografia. .
- **metadata_size** Tamanho do tampão de metadados.

### <a name="return-values"></a>Valores de devolução

- **NX_SECURE_TLS_SUCCESS** (0x00) testaram com sucesso os métodos de cripto fornecidos.
- **NX_PTR_ERROR** (0x07) Estrutura do método do cripto inválido
- **NX_NOT_SUCCESSFUL** (0x43) O auto-teste crypto falha.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_tls_session_create

## <a name="nx_secure_module_hash_compute"></a>nx_secure_module_hash_compute

Valor de haxixe computativo usando a função de haxixe fornecida pelo utilizador

### <a name="prototype"></a>Prototype

```C
UINT nx_secure_module_hash_compute(
                      NX_CRYPTO_METHOD *hamc_ptr,
                      UINT start_address, UINT end_address,
                      UCHAR *key, UINT key_length,
                      VOID *metadata, UINT metadata_size,
                      UCHAR *output_buffer, UINT output_buffer_size,
                      UINT *actual_size);
```

### <a name="description"></a>Description

Esta função calcula o valor do hash do fluxo de dados na área de memória especificada, utilizando o método de cripto HMAC fornecido e a cadeia de chaves. A função de computação de haxixe do módulo só está disponível se a biblioteca NetX Secure for construída com o seguinte símbolo a ser definido: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK

### <a name="parameters"></a>Parâmetros

- **hmac_ptr** Ponteiro para o método de cripto HMAC que está a ser utilizado para a computação de valor de haxixe.
- **start_address** O endereço inicial do tampão de dados
- **end_address** O endereço final do tampão de dados. Note que o cálculo de haxixe não cobre os dados neste end_address.
- **chave** A corda chave que está a ser utilizada na computação HMAC.
- **key_length** O tamanho da corda chave, em bytes
- **metadados** Ponteiro para o espaço usado pelo algoritmo HMAC.
- **metadata_size** Tamanho do tampão de metadados.
- **output_buffer** O local de memória onde a saída de haxixe está a ser armazenada.
- **output_buffer_size** O espaço disponível do tampão de saída, em bytes
- **atual_size** Devolvido pela função indicando o número real de bytes que estão a ser escritos no output_buffer.

### <a name="return-values"></a>Valores de devolução

- **0** Comumente computação com sucesso o valor do haxixe.
- **1** A computação de haxixe falhou.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_crypto_method_self_test

## <a name="nx_secure_tls_active_certificate_set"></a>nx_secure_tls_active_certificate_set

Definir o certificado de identidade ativa para uma Sessão TLS NetX Secure

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_active_certificate_set(
                   NX_SECURE_TLS_SESSION *tls_session,
                   NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a>Description

Este serviço destina-se a ser chamado a partir de uma chamada de sessão (ver nx_secure_tls_session_client_callback_set e nx_secure_tls_session_server_callback_set). Quando chamado com uma estrutura de NX_SECURE_X509_CERT previamente inicializada, esse certificado será utilizado em vez do certificado de identidade padrão. Na maioria dos casos, o certificado deve ter sido adicionado à loja local (ver nx_secure_tls_local_certificate_add) ou o aperto de mão TLS pode falhar.

Este serviço destina-se a permitir que a TLS suporte vários certificados de identidade. Isto é útil para um servidor TLS que presta serviços múltiplos endereços de rede para que o servidor possa escolher um certificado apropriado para fornecer ao cliente remoto dependendo do ponto de entrada do cliente. Para um cliente TLS, esta rotina pode ser usada para alterar o certificado enviado para um servidor remoto em tempo de execução depois de o servidor se ter identificado no aperto de mão TLS (isto é mais raro do que o caso de utilização do servidor TLS).

No caso de vários certificados poderem partilhar o mesmo nome distinto X.509, os certificados terão de ser adicionados utilizando nx_secure_tls_server_certificate_add, que introduz um identificador numérico separado do certificado.

### <a name="parameters"></a>Parâmetros

- **session_ptr** O ponteiro para uma sessão de TLS passou para a chamada da sessão.
- **certificado** Ponteiro para um certificado X.509 inicializado que deve ser usado para a sessão atual.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Atribuição bem sucedida de certificado à sessão.
- **NX_PTR_ERROR** (0x07) Sessão TLS inválida ou ponteiro de certificado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_session_client_callback_set
- nx_secure_tls_session_server_callback_set
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_find
- nx_secure_tls_server_certificate_remove

## <a name="nx_secure_tls_client_psk_set"></a>nx_secure_tls_client_psk_set

Desagure uma chave pré-partilhada para uma sessão de clientes NetX Secure TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_client_psk_set(NX_SECURE_TLS_SESSION *session_ptr,
                              UCHAR *pre_shared_key, UINT psk_length,
                              UCHAR *psk_identity, UINT identity_length,
                              UCHAR *hint, UINT hint_length);
```

### <a name="description"></a>Description

Este serviço adiciona uma chave pré-partilhada (PSK), a sua cadeia de identidade e uma dica de identidade para um bloco de controlo de Sessão TLS, e define que o PSK deve ser usado nas ligações subsequentes do Cliente TLS. O PSK é utilizado em vez de um certificado digital quando as cifrasuites PSK são ativadas e utilizadas.

Neste caso, o PSK está associado a um Servidor TLS remoto específico com o qual o Cliente TLS deseja comunicar. O conjunto PSK através deste API será fornecido ao anfitrião remoto do Servidor TLS durante o próximo aperto de mão TLS.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.
- **pre_shared_key** O valor real do PSK.
- **psk_length** O comprimento do valor PSK.
- **psk_identity** Uma corda usada para identificar este valor psk.
- **identity_length** O comprimento da identidade psk.
- **dica** Uma cadeia usada para indicar qual grupo de PSKs escolher num servidor TLS.
- **hint_length** O comprimento da corda de sugestão.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Adição bem sucedida de PSK.
- **NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Não pode adicionar outro PSK.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_client_psk_set(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a>Consulte também

- nx_secure_tls_psk_add
- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_initialize"></a>nx_secure_tls_initialize

Inicializa o módulo NetX Secure TLS

### <a name="prototype"></a>Prototype

```C
VOID nx_secure_tls_initialize(VOID);
```

### <a name="description"></a>Description

Este serviço inicializa o módulo NetX Secure TLS. Deve ser chamado antes que outros serviços NetX Secure possam ser acedidos.

### <a name="parameters"></a>Parâmetros

Nenhum

### <a name="return-values"></a>Valores de devolução

Nenhuma

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a>Consulte também

- nx_secure_tls_session_create

## <a name="nx_secure_tls_local_certificate_add"></a>nx_secure_tls_local_certificate_add

Adicione um certificado local à Sessão NetX Secure TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_local_certificate_add(
              NX_SECURE_TLS_SESSION *session_ptr,
              NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a>Description

Este serviço adiciona uma instância de estrutura NX_SECURE_X509_CERT inicializada à loja local de uma sessão TLS. Este certificado pode ser utilizado pela pilha TLS para identificar o dispositivo durante o aperto de mão TLS (se tiver sido marcado como um certificado de identidade durante a inicialização da estrutura do certificado utilizando nx_secure_x509_certificate_initialize), ou como emitente como parte de uma cadeia de certificados fornecida ao anfitrião remoto durante o aperto de mão TLS.

Se forem necessários vários certificados locais com o mesmo Nome Comum, os certificados podem ser adicionados utilizando o serviço *nx_secure_tls_server_certificate_add* (ver aviso abaixo).

É **necessário um** certificado para o modo TLS Server.

Um certificado é *opcional* para o modo Cliente TLS.

> [!IMPORTANT]
> *Esta API não deve ser utilizada com a mesma sessão TLS ao utilizar nx_secure_tls_server_certificate_add. O certificado de servidor API utiliza um identificador numérico único para cada certificado, e nx_secure_tls_local_certificate_add índices com base no Nome Comum X.509. Os serviços de certificados locais fornecem uma alternativa conveniente ao identificador numérico para aplicações que utilizem apenas um certificado de identidade único – utilizando o Nome Comum, a aplicação não precisa de acompanhar os identificadores numéricos.*

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.
- **certificate_ptr** Ponteiro para uma instância inicializada do Certificado TLS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Adição bem sucedida do certificado.
- **NX_INVALID_PARAMETERS** (0x4D) Tentou adicionar um certificado inválido ou duplicado.
- **NX_PTR_ERROR** (0x07) Sessão TLS inválida ou ponteiro de certificado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a>Consulte também

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_remove
- nx_secure_tls_local_certificate_find

## <a name="nx_secure_tls_local_certificate_find"></a>nx_secure_tls_local_certificate_find

Encontre um certificado local numa Sessão De TLS Segura NetX por Nome Comum

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_local_certificate_find(NX_SECURE_TLS_SESSION
                        *session_ptr, NX_SECURE_X509_CERT
                        **certificate, UCHAR *common_name, UINT
                        name_length);
```

### <a name="description"></a>Description

Este serviço encontra um certificado na loja de certificados de dispositivo local de uma sessão TLS e devolve um ponteiro à estrutura NX_SECURE_X509_CERT da loja. O parâmetro common_name e o seu comprimento (name_length) são utilizados para identificar o certificado na loja, correspondendo ao campo X.509 Nome Comum do certificado.

Se estiver presente mais de um certificado com o mesmo Nome Comum, apenas o primeiro será devolvido – utilize *nx_secure_tls_server_certificate_find* em vez disso.

> [!IMPORTANT]
> *Esta API não deve ser utilizada com a mesma sessão TLS ao utilizar nx_secure_tls_server_certificate_add. O certificado de servidor API utiliza um identificador numérico único para cada certificado, e nx_secure_tls_local_certificate_add índices com base no Nome Comum X.509. Os serviços de certificados locais fornecem uma alternativa conveniente ao identificador numérico para aplicações que utilizem apenas um certificado de identidade único – utilizando o Nome Comum, a aplicação não precisa de acompanhar os identificadores numéricos.*

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.
- **certificado** Devolva o Ponteiro ao certificado combinado.
- **common_name** Cadeia de nome comum para combinar (nome DNS).
- **name_length** Comprimento dos common_name dados de cadeia.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** certificado (0x00) foi encontrado e ponteiro devolvido no parâmetro "certificado".
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Não foi encontrado nenhum certificado com o nome comum fornecido.
- **NX_PTR_ERROR** (0x07) Sessão de TLS inválida, ponteiro de certificado ou cadeia de nome comum.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_remove
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_local_certificate_remove"></a>nx_secure_tls_local_certificate_remove

Remover certificado local da Sessão NetX Secure TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_local_certificate_remove(NX_SECURE_TLS_SESSION
                  *session_ptr, UCHAR *common_name, UINT
                  common_name_length);
```

### <a name="description"></a>Description

Este serviço remove uma instância de certificado local de uma sessão de TLS, chave no campo Nome Comum no certificado.

> [!IMPORTANT]
> *Esta API não deve ser utilizada com a mesma sessão TLS ao utilizar nx_secure_tls_server_certificate_add. O certificado de servidor API utiliza um identificador numérico único para cada certificado, e nx_secure_tls_local_certificate_add índices com base no Nome Comum X.509. Os serviços de certificados locais fornecem uma alternativa conveniente ao identificador numérico para aplicações que utilizem apenas um certificado de identidade único – utilizando o Nome Comum, a aplicação não precisa de acompanhar os identificadores numéricos.*

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.
- **common_name** O valor do nome comum do certificado a retirar.
- **common_name_length** O comprimento da corda nome comum.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Adição bem sucedida do certificado.
- **NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** certificado (0x119) não foi encontrado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a>Consulte também

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_metadata_size_calculate"></a>nx_secure_tls_metadata_size_calculate

Calcular o tamanho dos metadados criptográficos para uma Sessão de TLS NetX Secure

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_metadata_size_calculate(
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        ULONG *metadata_size);
```

### <a name="description"></a>Description

Este serviço calcula e devolve o tamanho dos metadados criptográficos necessários para uma sessão de TLS e tabela de criptografia TLS (consulte a secção "Inicialização de TLS com Métodos Criptográficos" para obter mais informações sobre a tabela de cifra criptográfica).

Este serviço deve ser chamado com a tabela criptográfica desejada para calcular o tamanho do tampão de metadados transmitido em nx_secure_tls_session_create.

### <a name="parameters"></a>Parâmetros

- **crypto_table** Ponteiro para uma tabela completa de criptografia NetX Secure TLS.
- **metadata_size** A saída do tamanho do cálculo em bytes.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Cálculo bem sucedido do tamanho dos metadados.
- **NX_PTR_ERROR** (0x07) Mesa de cripto inválida ou ponteiro do tamanho do retorno.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_tls_session_create

## <a name="nx_secure_tls_packet_allocate"></a>nx_secure_tls_packet_allocate

Aloque um pacote para uma Sessão NetX Secure TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_packet_allocate(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET_POOL *pool_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço atribui uma NX_PACKET para a sessão de TLS ativa especificada a partir do NX_PACKET_POOL especificado. Este serviço deve ser chamado pela aplicação para atribuir pacotes de dados a serem enviados através de uma ligação TLS. A sessão TLS deve ser inicializada antes de ligar para este serviço.

O pacote atribuído é devidamente inicializado de modo a que os dados do cabeçalho e do rodapé TLS possam ser adicionados após a população dos dados do pacote. O comportamento é idêntico ao *nx_packet_allocate*.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma sessão de TLS.
- **pool_ptr** O ponteiro para um NX_PACKET_POOL a partir do qual atribuir o pacote.
- **packet_ptr** Ponteiro de saída para o pacote recém-atribuído.
- **wait_option** Opção de suspensão para alocação de pacotes.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Atribuição de pacotes bem sucedidos.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) A atribuição de pacotes subjacentes falhou.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) A sessão TLS fornecida não foi inicializada.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Allocate a new TLS packet from the previously created packet pool and
previously initialized TLS session.   */

status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &packet_ptr,
                                       NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
variable packet_ptr.  */
```

### <a name="see-also"></a>Consulte também

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_receive
- nx_secure_tls_session_send
- nx_secure_tls_session_end
- nx_secure_tls_session_create

## <a name="nx_secure_tls_psk_add"></a>nx_secure_tls_psk_add

Adicione uma chave pré-partilhada a uma Sessão de TLS Segura NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_psk_add(NX_SECURE_TLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a>Description

Este serviço adiciona uma chave pré-partilhada (PSK), a sua cadeia de identidade e uma dica de identidade para um bloco de controlo TLS Session. O PSK é utilizado em vez de um certificado digital quando as cifrasuites PSK são ativadas e utilizadas.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.
- **pre_shared_key** O valor real do PSK.
- **psk_length** O comprimento do valor PSK.
- **psk_identity** Uma corda usada para identificar este valor psk.
- **identity_length** O comprimento da identidade psk.
- **dica** Uma cadeia usada para indicar qual grupo de PSKs escolher num servidor TLS.
- **hint_length** O comprimento da corda de sugestão.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Adição bem sucedida de PSK.
- **NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Não pode adicionar outro PSK.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_psk_add(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a>Consulte também

- nx_secure_tls_client_psk_set
- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_remote_certificate_allocate"></a>nx_secure_tls_remote_certificate_allocate

Alocar espaço para o certificado fornecido por um anfitrião remoto TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_remote_certificate_allocate(
                 NX_SECURE_TLS_SESSION *session_ptr,
                 NX_SECURE_X509_CERT *certificate_ptr,
                 UCHAR *raw_certificate_buffer,
                 UINT raw_buffer_size);
```

### <a name="description"></a>Description

Este serviço adiciona uma instância de estrutura de NX_SECURE_X509_CERT não iniializada a uma sessão de TLS com o objetivo de atribuir espaço para certificados fornecidos por um anfitrião remoto durante uma sessão de TLS. Os dados do certificado remoto são analisados pelo NetX Secure TLS e essa informação é utilizada para preencher a instância da estrutura do certificado fornecida a esta função. Os certificados adicionados desta forma são colocados numa lista ligada.

Se se espera que o anfitrião remoto forneça vários certificados, esta função deve ser chamada repetidamente para alocar espaço para todos os certificados. Os certificados adicionais são adicionados ao final da lista ligada ao certificado.

A não atribuição de um certificado remoto fará com que o modo do Cliente TLS falhe durante o aperto de mão TLS, a menos que esteja a ser utilizada uma cifrassuita de chave pré-partilhada (PSK).

O *parâmetro raw_certificate_buffer* aponta para o espaço atribuído para armazenar o certificado remoto de entrada. Os certificados típicos com teclas RSA de 2048 bits usando SHA-256 para assinaturas estão na gama de bytes 1000-2000. O tampão deve ser grande o suficiente para pelo menos manter esse tamanho, mas dependendo dos certificados de anfitrião remoto pode ser significativamente menor ou maior. Note que se o tampão for demasiado pequeno para segurar o certificado de entrada, o aperto de mão TLS terminará com um erro.

Para o modo Servidor TLS, só é necessária uma atribuição de certificado remoto se a autenticação do certificado do cliente estiver ativada.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.
- **certificate_ptr** Ponteiro para uma instância de certificado X.509 não ininitializada.
- **raw_certificate_buffer** Ponteiro para um tampão para manter o certificado não analisado recebido do anfitrião remoto.
- **raw_buffer_size** Tamanho do tampão de certificado bruto.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Atribuição bem sucedida do certificado.
- **NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) O tampão fornecido era demasiado pequeno.
- **NX_INVALID_PARAMETERS** (0x4D) Tentou adicionar um certificado inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_x509_certificate_initialize,
- nx_secure_tls_session_create

## <a name="nx_secure_tls_remote_certificate_buffer_allocate"></a>nx_secure_tls_remote_certificate_buffer_allocate

Alocar espaço para todos os certificados fornecidos por um anfitrião remoto TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_remote_certificate_buffer_allocate(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a>Description

Este serviço atribui espaço para processar as cadeias de certificados de entrada de anfitriões de servidores remotos de forma a realizar a autenticação e verificação X.509 numa instância do Cliente TLS. No que diz o modo TLS Server, a atribuição de certificados remotos só é necessária se a autenticação do certificado do cliente X.509 estiver ativada – para as instâncias do Servidor TLS, o serviço *nx_secure_tls_session_x509_client_verify_configure* deve ser utilizado.

A não atribuição de certificados remotos fará com que o modo do Cliente TLS falhe durante o aperto de mão TLS, a menos que esteja a ser utilizada uma cifrassuita de chave pré-partilhada (PSK).

O *parâmetro certificate_buffer* aponta para o espaço atribuído para armazenar os certificados remotos de entrada e os blocos de controlo necessários para esses certificados. O tampão será dividido pelo número de certificados *(certs_number*) com uma porção igual dada a cada certificado. O parâmetro *buffer_size*  indica o tamanho do tampão. O espaço necessário pode ser encontrado com a seguinte fórmula:

```C
buffer_size = (<expected max number of certificates in chain>) *
                 (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

Os certificados típicos com teclas RSA de 2048 bits usando SHA-256 para assinaturas estão na gama de bytes 1000-2000. O tampão deve ser suficientemente grande para, pelo menos, manter esse tamanho para cada certificado, mas dependendo dos certificados de anfitrião remoto podem ser significativamente menores ou maiores. Note que se o tampão for demasiado pequeno para segurar o certificado de entrada, o aperto de mão TLS terminará com um erro.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.
- **certs_number** Número de certificados a atribuir do tampão fornecido.
- **certificate_buffer** Ponteiro para um tampão para obter certificados recebidos de um hospedeiro remoto.
- **buffer_size** Tamanho do tampão de certificado.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Atribuição bem sucedida do certificado.
- **NX_PTR_ERROR** (0x07) Sessão TLS inválida ou ponteiro tampão.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) O tampão fornecido era demasiado pequeno.
- **NX_INVALID_PARAMETERS** (0x4D) O tampão era demasiado pequeno para deter o número de certificados pretendido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create

## <a name="nx_secure_tls_remote_certificate_free_all"></a>nx_secure_tls_remote_certificate_free_all

Espaço gratuito atribuído para certificados de entrada

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_remote_certificate_free_all(
                  NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Description

Este serviço é utilizado para libertar todos os amortecedores de certificados atribuídos a uma sessão TLS específica, nx_secure_tls_remote_certificate_allocated devolvendo-os ao espaço de certificado gratuito da sessão. Isto pode ser necessário se uma aplicação reutilizar um objeto de sessão TLS sem o eliminar e recriar com nx_secure_tls_session_delete e nx_secure_tls_session_create.

Note que o espaço do certificado remoto é recuperado automaticamente quando a sessão TLS é reposta como acontece em nx_secure_tls_session_end pelo que a maioria das aplicações não deve precisar de ligar para este serviço.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Funcionamento bem sucedido.
- **NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.
- **NX_INVALID_PARAMETERS** (0x4D) Erro interno – loja de certificados provavelmente corrupta.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_end

## <a name="nx_secure_tls_server_certificate_add"></a>nx_secure_tls_server_certificate_add

Adicione um certificado especificamente para servidores TLS usando um identificador numérico

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_server_certificate_add(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT *certificate, UINT cert_id);
```

### <a name="description"></a>Description

Este serviço é utilizado para adicionar um certificado à loja local de uma sessão de TLS (ver nx_secure_tls_local_certificate_add) utilizando um identificador numérico em vez de indexar a loja utilizando o Sujeito X.509 (Nome Comum) dentro do certificado. O identificador numérico é separado do certificado e permite a adição de vários certificados como certificados de identidade a um servidor TLS, bem como permitir que vários certificados com o mesmo Nome Comum sejam adicionados à mesma loja local de sessão TLS. Este mesmo serviço pode ser utilizado para certificados de cliente, mas é raro um cliente TLS ter vários certificados de identidade.

O parâmetro cert_id é um número inteiro positivo não zero atribuído pela aplicação. O valor real não importa (além de zero), mas deve ser único na loja para a sessão TLS fornecida. O valor cert_id pode ser usado para encontrar e remover certificados da loja local usando nx_secure_tls_server_certificate_find e nx_secure_tls_server_certificate_remove, respectivamente.

> [!IMPORTANT]
> *Esta API não deve ser utilizada com a mesma sessão TLS ao utilizar nx_secure_tls_local_certificate_add. A API nx_secure_tls_server_certificate_add utiliza um identificador numérico único para cada certificado, e índice de serviços de certificado local com base no Nome Comum X.509. Os serviços de certificados de servidor permitem que existam vários certificados com dados partilhados (especialmente Nome Comum) na mesma loja local – isto é útil para um servidor com múltiplas identidades.*

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.
- **certificado** Ponteiro para uma instância de certificado X.509 previamente inicialmente inicializada.
- **cert_id** Positivo, não-zero, número de identificação de certificado relativamente único.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00)Operação bem sucedida.
- **NX_PTR_ERROR** (0x07) Ponteiro orcertificado de sessão de TLS inválido.
- **NX_SECURE_TLS_CERT_ID_INVALID** (0x138) O ID do certificado fornecido tinha um valor inválido (provavelmente 0).
- **NX_SECURE_TLS_CERT_ID_DUPLICATE** (0x139) O certificado fornecido já estava presente na loja local.
- **NX_INVALID_PARAMETERS(0x4D)** Erro interno – loja de certificados provavelmente corrupta.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully added with the ID
0x12.  */
```

### <a name="see-also"></a>Consulte também

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_active_certificate_set
- nx_secure_tls_server_certificate_find
- nx_secure_tls_server_certificate_remove

## <a name="nx_secure_tls_server_certificate_find"></a>nx_secure_tls_server_certificate_find

Encontre um certificado usando um identificador numérico

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_server_certificate_find(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT **certificate, UINT cert_id);
```

### <a name="description"></a>Description

Este serviço é utilizado para encontrar um certificado na loja local de uma sessão de TLS (ver nx_secure_tls_local_certificate_add) utilizando um identificador numérico em vez de indexar a loja utilizando o Sujeito X.509 (Nome Comum) dentro do certificado.

O parâmetro cert_id é um número inteiro positivo não zero atribuído pelo pedido quando o certificado é adicionado à loja local de sessão TLS utilizando nx_secure_tls_server_certificate_add.

> [!IMPORTANT]
> *Esta API não deve ser utilizada com a mesma sessão TLS ao utilizar nx_secure_tls_local_certificate_add. A API nx_secure_tls_server_certificate_add utiliza um identificador numérico único para cada certificado, e índice de serviços de certificado local com base no Nome Comum X.509. Os serviços de certificados de servidor permitem que existam vários certificados com dados partilhados (especialmente Nome Comum) na mesma loja local – isto é útil para um servidor com múltiplas identidades.*

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.
- **certificado** Ponteiro para um ponteiro de certificado X.509 para devolver uma referência ao certificado encontrado.
- **cert_id** Valor de identificação de certificado positivo não zero.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00)Operação bem sucedida.
- **NX_PTR_ERROR** (0x07) Sessão TLS inválida ou ponteiro de certificado.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) O certificado fornecido não correspondia a nenhum na loja local da sessão TLS fornecida.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
NX_SECURE_X509_CERT *certificate;


/* Find certificate in TLS session.  */
status =  nx_secure_tls_server_certificate_find(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully found and a reference
returned in the certificate parameter.  */
```

### <a name="see-also"></a>Consulte também

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_active_certificate_set
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_remove

##  <a name="nx_secure_tls_server_certificate_remove"></a>nx_secure_tls_server_certificate_remove

Remova um certificado de servidor local usando um identificador numérico

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_server_certificate_remove(
                  NX_SECURE_TLS_SESSION *session_ptr, UINT cert_id);
```

### <a name="description"></a>Description

Este serviço é utilizado para remover um certificado da loja local de uma sessão de TLS (ver nx_secure_tls_local_certificate_add) utilizando um identificador numérico em vez de indexar a loja utilizando o Sujeito X.509 (Nome Comum) dentro do certificado.

O parâmetro cert_id é um número inteiro positivo não zero atribuído pelo pedido quando o certificado é adicionado à loja local de sessão TLS utilizando nx_secure_tls_server_certificate_add.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.
- **cert_id** Valor de identificação de certificado positivo não zero.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00)Operação bem sucedida.
- **NX_PTR_ERROR** (0x07) Sessão TLS Inválida.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) O certificado fornecido não correspondia a nenhum na loja local da sessão TLS fornecida.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_active_certificate_set
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_find

## <a name="nx_secure_tls_session_alert_value_get"></a>nx_secure_tls_session_alert_value_get

Obtenha o valor e o nível de alerta TLS enviados pelo anfitrião remoto

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_alert_value_get(
                   NX_SECURE_TLS_SESSION *session_ptr,
                   UINT *alert_level, UINT *alert_value);
```

### <a name="description"></a>Description

Este serviço é utilizado para recuperar o nível de alerta e valor do TLS quando o hospedeiro remoto envia um alerta em resposta a algum problema ou erro.

Os valores dos parâmetros alert_level e alert_value só são válidos se esta função for chamada imediatamente após uma chamada da API TLS que devolveu um estado de NX_SECURE_TLS_ALERT_RECEIVED (0x114) indicando que foi recebido um alerta do hospedeiro remoto.

Note que se o anfitrião local TLS enviar um alerta, os códigos de erro devolvidos são muito mais descritivos do erro real do que o próprio alerta TLS porque os valores de alerta TLS são intencionalmente deixados ambíguos para evitar certos tipos de ataque (como um ataque de "acolchoamento oráculo" ou similar).

O nível de alerta só leva um de dois valores: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) ou NX_SECURE_TLS_ALERT_LEVEL_FATAL (0x2). Em geral, apenas o Alerta CloseNotify (usado para indicar um fim bem-sucedido de uma sessão TLS) receberá um nível de "Aviso", embora algumas situações de configuração de extensão também possam ser consideradas advertências. A grande maioria dos alertas será "Fatal" indicando uma potencial falha de segurança e resultando no encerramento imediato da ligação TLS (aperto de mão ou sessão).

Os valores de alerta TLS são definidos nos RFCs TLS, aqui está a lista de RFC 5246 (TLSv1.2) para referência:

| Nome do Alerta                     | Valor | Descrição                                                                                                                                                  |
| ---------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| close_notify                  | 0     | Sem erro, indica fim de sessão bem-sucedido                                                                                                                   |
| unexpected_message            | 10    | TLS recebeu uma mensagem inesperada ou fora de encomenda                                                                                                           |
| bad_record_mac               | 20    | A verificação de desencriptação e/ou MAC falhou                                                                                                                    |
| decryption_failed_RESERVED   | 21    | **PRECOTADO** A desencriptação falhou (depreciada devido a ataques de oráculo de enchimento)                                                                                      |
| record_overflow               | 22    | Foi recebido um recorde maior do que o tamanho máximo de registo do TLS                                                                                        |
| decompression_failure         | 30    | Um problema foi encontrado na compressão/descompressão de um registo TLS                                                                                       |
| handshake_failure             | 40    | Ocorreu um erro de aperto de mão não especificado que não está coberto por um alerta diferente.                                                                            |
| no_certificate_RESERVED      | 41    | **DEPRECATED** EM TLS (apenas SSL)                                                                                                                                 |
| bad_certificate               | 42    | Um certificado que foi recebido continha formatação inválida ou assinaturas                                                                                   |
| unsupported_certificate       | 43    | Foi recebido um certificado de tipo inválido (por exemplo, certificado de assinatura utilizado para a autenticação do servidor TLS)                                    |
| certificate_revoked           | 44    | O estatuto do certificado (conforme fornecido por um CRL ou OCSP) foi indicado como "revogado"                                                                       |
| certificate_expired           | 45    | O certificado recebido estava fora do seu intervalo de datas válido (ou não válido ainda ou caducado)                                                                 |
| certificate_unknown           | 46    | Alguma emissão de certificado desconhecida foi encontrada que não foi abrangida por outros alertas                                                                          |
| illegal_parameter             | 47    | Alguma configuração ou valor negociado no aperto de mão TLS foi inválido ou fora de alcance                                                                      |
| unknown_ca                    | 48    | O certificado de identidade recebido não pôde ser rastreado através de uma cadeia de certificados a um certificado de CA de raiz fidedigna.                                              |
| access_denied                 | 49    | Indica que foi recebido um certificado válido, mas o controlo de acesso a pedidos indicou que o certificado era inválido para os recursos solicitados.            |
| decode_error                  | 50    | Algum campo ou valor num cabeçalho TLS ou mensagem de aperto de mão estava fora de alcance ou inválido, levando a uma falha na descodição de um registo TLS.                      |
| decrypt_error                 | 51    | Não foi possível verificar um haxixe de mensagem de assinatura ou acabado durante o aperto de mão TLS.                                                                         |
| export_restriction_RESERVED  | 60    | DEPRECATED EM TLSv1.2                                                                                                                                        |
| protocol_version              | 70    | A versão do protocolo TLS negociada durante o aperto de mão é reconhecida mas não suportada (por exemplo, tLSv1.0 foi apresentada, mas não ativada).                       |
| insufficient_security         | 71    | Enviado sempre que um aperto de mão falha devido à falta de cifras seguras (por exemplo.key tamanho é demasiado pequeno para os requisitos de aplicação)                                |
| internal_error                | 80    | Ocorreu alguns erros não TLS (por exemplo, problemas de atribuição de memória, problemas de aplicação) que resultaram numa sessão de TLS partida.                                         |
| user_canceled                 | 90    | Devolvido se a sessão TLS for cancelada por um utilizador ou aplicação antes do aperto de mão estar completo (semelhante ao CloseNotify).                                 |
| no_renegotiation              | 100   | O Anfitrião remoto não está disposto a executar apertos de mão de renegociação do TLS em resposta a um pedido de renegociação.                                 |
| unsupported_extension         | 110   | Enviado se um Cliente TLS receber um ServerHello contendo extensões não explicitamente solicitadas no ClientHello inicial (indicando que o servidor tem um problema). |

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma sessão de TLS.
- **alert_level** Devolva o nível do alerta recebido (aviso ou fatal).
- **alert_value** Devolva o valor do alerta recebido (ver tabela).

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Funcionamento bem sucedido.
- **NX_PTR_ERROR** (0x07) Sessão TLS Inválida.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_tls_session_start
- nx_secure_tls_session_send
- nx_secure_tls_session_receive

## <a name="nx_secure_tls_session_certificate_callback_set"></a>nx_secure_tls_session_certificate_callback_set

Configurar uma chamada para o TLS usar para validação adicional de certificados

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_ session_certificate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *session,
                                    NX_SECURE_X509_CERT *certificate));
```

### <a name="description"></a>Description

Este serviço atribui um ponteiro de função a uma sessão de TLS que o TLS invocará quando um certificado é recebido de um anfitrião remoto, permitindo que o pedido efetue verificações de validação como validação de DNS, revogação de certificados e aplicação da política de certificados.

O NetX Secure TLS realizará a validação básica do percurso X.509 no certificado antes de invocar a chamada para garantir que o certificado pode ser rastreado até um certificado na loja de certificados fidedignos TLS, mas todas as outras validações serão tratadas por esta chamada.

O retorno fornece o ponteiro de sessão TLS e um ponteiro para o certificado de identidade de anfitrião remoto (a folha na cadeia de certificados). O retorno deve voltar NX_SUCCESS se toda a validação for bem sucedida, caso contrário deverá devolver um código de erro que indique a falha de validação. Qualquer valor que não seja NX_SUCCESS fará com que o aperto de mão TLS aborte imediatamente.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.
- **func_ptr** Ponteiro para a função de retorno de validação do certificado.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Atribuição bem sucedida do ponteiro função.
- **NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_tls_session_create
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_crl_revocation_check

## <a name="nx_secure_tls_session_client_callback_set"></a>nx_secure_tls_session_client_callback_set

Configurar uma chamada para o TLS invocar no início de um aperto de mão do Cliente TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_ session_client_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions, UINT num_extensions));
```

### <a name="description"></a>Description

Este serviço atribui um ponteiro de função a uma sessão de TLS que o TLS invocará quando um aperto de mão do Cliente TLS tiver recebido uma mensagem ServerHelloDone. A função de retorno permite que uma aplicação processe quaisquer extensões TLS da mensagem ServerHello recebida que exijam entrada ou tomada de decisão.

O retorno é executado com o bloco de controlo de sessão TLS invocando e uma série de objetos NX_SECURE_TLS_HELLO_EXTENSION. A matriz de objetos de extensão destina-se a ser passada para uma função auxiliar que irá encontrar e analisar uma extensão específica. Atualmente, não existem extensões específicas suportadas no NetX Secure que exijam a entrada do Cliente TLS, mas o retorno está disponível para os designers de aplicações lidarem com extensões personalizadas ou novas que possam ficar disponíveis. Para uma função de ajudante de exemplo que analisa as extensões TLS fornecidas em mensagens hello, consulte *nx_secure_tls_session_sni_extension_parse*.

O retorno do cliente também pode ser usado para selecionar o certificado de identidade ativa usando *nx_secure_tls_ative_certificate_set* para o Cliente TLS no caso de o servidor remoto ter solicitado um certificado e fornecido informações para permitir ao Cliente TLS selecionar um certificado específico. Consulte a referência para nx_secure_tls_ative_certificate_set para obter mais informações.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.
- **func_ptr** Ponteiro para a função de retorno do cliente TLS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Atribuição bem sucedida do ponteiro de funções.
- **NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_tls_session_create
- nx_secure_tls_session_server_callback_set
- nx_secure_tls_active_certificate_set

## <a name="nx_secure_tls_session_x509_client_verify_configure"></a>nx_secure_tls_session_x509_client_verify_configure

Ativar a verificação do cliente X.509 e alocar espaço para certificados de cliente

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_x509_client_verify_configure(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a>Description

Este serviço permite a autenticação opcional do cliente X.509 para uma instância do Servidor TLS. Também aloca o espaço necessário para processar as cadeias de certificados de entrada do anfitrião remoto do cliente. Os certificados fornecidos pelo cliente remoto serão verificados contra os certificados fidedignos do servidor TLS, atribuídos com o *serviço nx_secure_tls_trusted_certificate_add.*

Para o modo cliente TLS, é necessária a atribuição de certificado remoto e o *serviço nx_secure_tls_remote_certificate_buffer_allocate* deve ser utilizado. Ativar a autenticação do cliente X.509 numa instância do Cliente TLS não terá qualquer efeito.

O *parâmetro certificate_buffer* aponta para o espaço atribuído para armazenar os certificados remotos de entrada e os blocos de controlo necessários para esses certificados. O tampão será dividido pelo número de certificados *(certs_number*) com uma porção igual dada a cada certificado. O parâmetro *buffer_size* indica o tamanho do tampão. O espaço necessário pode ser encontrado com a seguinte fórmula:

```C
buffer_size = (<expected max number of certificates in chain>) *
             (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

Os certificados típicos com teclas RSA de 2048 bits usando SHA-256 para assinaturas estão na gama de bytes 1000-2000. O tampão deve ser suficientemente grande para, pelo menos, manter esse tamanho para cada certificado, mas dependendo dos certificados de anfitrião remoto podem ser significativamente menores ou maiores. Note que se o tampão for demasiado pequeno para segurar o certificado de entrada, o aperto de mão TLS terminará com um erro.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.
- **certs_number** Número de certificados a atribuir do tampão fornecido.
- **certificate_buffer** Ponteiro para um tampão para obter certificados recebidos de um hospedeiro remoto.
- **buffer_size** Tamanho do tampão de certificado.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00)Atribuição bem sucedida do certificado.
- **NX_PTR_ERROR** (0x07) Sessão TLS inválida ou ponteiro tampão.
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) O tampão fornecido era demasiado pequeno.
- **NX_INVALID_PARAMETERS** (0x4D) O tampão era demasiado pequeno para deter o número de certificados pretendido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_buffer_allocate

## <a name="nx_secure_tls_session_client_verify_disable"></a>nx_secure_tls_session_client_verify_disable

Desativar a autenticação do certificado do cliente para uma Sessão TLS Segura NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_client_verify_disable(
                              NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Description

Este serviço desativa a autenticação do Certificado de Cliente para uma sessão específica de TLS. Consulte nx_secure_tls_session_client_verify_enable para mais informações.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma sessão de TLS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Mudança de estado bem sucedida.
- **NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_disable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will not
request certificates from the remote TLS client.  */
```

### <a name="see-also"></a>Consulte também

- nx_secure_tls_session_client_verify_enable
- nx_secure_tls_session_start
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_client_verify_enable"></a>nx_secure_tls_session_client_verify_enable

Ativar a autenticação do certificado de cliente para uma Sessão TLS Segura NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_client_verify_enable(
                                NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Description

Este serviço permite a autenticação do Certificado de Cliente para uma sessão específica de TLS. Permitir a autenticação do certificado de cliente para uma instância do Servidor TLS fará com que o Servidor TLS solicite um certificado a qualquer Cliente TLS remoto durante o aperto de mão TLS inicial. O certificado recebido do cliente TLS remoto é acompanhado por uma mensagem CertificateVerify, que o Servidor TLS utiliza para verificar se o Cliente é dono do certificado (tem acesso à chave privada associada a esse certificado).

Se o certificado fornecido puder ser verificado e rastreado até um certificado na loja de certificados fidedignos do TLS Server através de uma cadeia de certificados X.509, o cliente TLS remoto é autenticado e o aperto de mão prossegue. Em caso de erros no processamento do certificado ou mensagem CertificateVerify, o aperto de mão TLS termina com um erro.

> [!NOTE]
> *O Servidor TLS deve ter pelo menos um certificado na sua loja de confiança adicionado com nx_secure_tls_trusted_certificate_add ou autenticação falhará sempre.*

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma sessão de TLS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Mudança de estado bem sucedida.
- **NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Add a trusted certificate so the TLS Server has something to verify against. */
status = nx_secure_tls_trusted_certificate_add(&tls_session,
                                               &trusted_certificate);

/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_enable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will now
request and verify certificates from the remote TLS client.  */
```

### <a name="see-also"></a>Consulte também

- nx_secure_tls_session_client_verify_enable
- nx_secure_tls_session_start
- nx_secure_tls_session_create
- nx_secure_tls_trusted_certificate_add

## <a name="nx_secure_tls_session_create"></a>nx_secure_tls_session_create

Criar uma Sessão TLS Segura NetX para comunicações seguras

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_create(NX_SECURE_TLS_SESSION *session_ptr
                                   NX_SECURE_TLS_CRYPTO *cipher_table,
                                   VOID *encryption_metadata_area,
                                   ULONG encryption_metadata_size);
```

### <a name="description"></a>Description

Este serviço inicializa uma NX_SECURE_TLS_SESSION exemplo de estrutura para utilização no estabelecimento de comunicações TLS seguras sobre uma ligação de rede.

O método requer um objeto NX_SECURE_TLS_CRYPTO que é povoado com os métodos criptográficos disponíveis para ser usado para TLS. O *encryption_metadata_area* aponta para um tampão atribuído para utilização pelo TLS para os "metadados" utilizados pelos métodos criptográficos na tabela NX_SECURE_TLS_CRYPTO para cálculos. O tamanho da tabela pode ser determinado utilizando o serviço nx_secure_tls_metadata_size_calculate. Consulte a secção "Criptografia em NetX Secure TLS" no Capítulo 3 para obter mais detalhes.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma sessão de TLS.
- **cipher_table** Ponteiro para métodos criptográficos TLS.
- **encryption_metadata_area** Ponteiro para o espaço para metadados de criptografia.
- **encryption_metadata_size** Tamanho do tampão de metadados.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00)Iniciação bem sucedida da sessão TLS.
- **NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.
- **NX_INVALID_PARAMETERS** (0x4D) O tampão de metadados era demasiado pequeno para os métodos dados.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) Não foi fornecido na tabela de cifras um método de cifra necessário para a versão ativada do STS.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_x509_certificate_initialize
- nx_secure_tls_metadata_size_calculate
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_end
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_delete
- Criptografia em NetX Secure TLS no Capítulo 3

## <a name="nx_secure_tls_session_delete"></a>nx_secure_tls_session_delete

Excluir uma Sessão de TLS Segura NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_delete(NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Description

Este serviço elimina uma sessão TLS representada por uma instância de estrutura NX_SECURE_TLS_SESSION e liberta todos os recursos do sistema detidos por essa instância de sessão.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma sessão de TLS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Iniciação bem sucedida da sessão TLS.
- **NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Delete TLS session.  */
status =  nx_secure_tls_session_delete(&tls_session);


/* If status is NX_SUCCESS the TLS Session was successfully deleted.  */
```

### <a name="see-also"></a>Consulte também

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_end
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_end"></a>nx_secure_tls_session_end

Termine uma sessão ativa de TLS Do NetX Secure

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_end(NX_SECURE_TLS_SESSION *session_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço termina uma sessão TLS representada por uma NX_SECURE_TLS_SESSION instância de estrutura enviando a mensagem TLS CloseNotify para o anfitrião remoto. Em seguida, o serviço aguarda que o anfitrião remoto responda com a sua própria mensagem CloseNotify.

Se o anfitrião remoto não enviar uma mensagem CloseNotify, o TLS considera que se trata de um erro e de uma possível falha de segurança, pelo que verificar o valor de devolução é importante para uma ligação segura. O **parâmetro wait_option** pode ser utilizado para controlar quanto tempo o serviço deve esperar pela resposta antes de devolver o controlo ao fio de chamada.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma sessão de TLS.
- **wait_option** Indica quanto tempo o serviço deve esperar pela resposta do hospedeiro remoto.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Iniciação bem sucedida da sessão TLS.
- **NX_SECURE_TLS_NO_CLOSE_RESPONSE** (0x113) não recebeu uma resposta do anfitrião remoto antes do tempo de 200.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Não poderia atribuir um pacote para enviar a mensagem CloseNotify.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Não foi possível enviar a mensagem CloseNotify sobre a tomada TCP.
- **NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* End TLS session.  */
status =  nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the TLS Session was successfully ended.  */
```

### <a name="see-also"></a>Consulte também

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_packet_buffer_set"></a>nx_secure_tls_session_packet_buffer_set

Descreva o tampão de montagem do pacote para uma Sessão TLS NetX Secure

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_packet_buffer_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *buffer_ptr,
                                    ULONG buffer_size);
```

### <a name="description"></a>Description

Este serviço associa um tampão de remontagem de pacote a uma sessão de TLS. Para desencriptar e analisar os registos TLS de entrada, os dados em cada registo devem ser reunidos a partir dos pacotes TCP subjacentes. Os registos TLS podem ter até 16KB de tamanho (embora normalmente sejam muito menores) pelo que podem não caber num único pacote TCP.

Se souber que o tamanho da mensagem de entrada será menor do que o limite de registo TLS de 16KB, o tamanho do tampão pode ser menor, mas para lidar com dados de entrada desconhecidos, o tampão deve ser feito o maior possível. Se um registo de entrada for maior do que o tampão fornecido, a sessão TLS terminará com um erro.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma sessão de TLS.
- **buffer_ptr** Ponteiro para tampão para TLS para utilizar para remontagem de pacotes.
- **buffer_size** Tamanho do tampão fornecido em bytes.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Iniciação bem sucedida da sessão TLS.
- **NX_INVALID_PARAMETERS** (0x4D) Tampão inválido ou ponteiro de sessão TLS.
- **NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Buffer for TLS packet reassembly. */
UCHAR tls_packet_buffer[16384];
/* Assign buffer to TLS session.  */
status =  nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                  sizeof(tls_packet_buffer));


/* If status is NX_SUCCESS the buffer was successfully added.  */
```

### <a name="see-also"></a>Consulte também

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_protocol_version_override"></a>nx_secure_tls_session_protocol_version_override

Anular a versão padrão do protocolo TLS para uma Sessão De TLS Do NetX Secure

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_protocol_version_override(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              USHORT protocol_version);
```

### <a name="description"></a>Description

Este serviço substitui a versão padrão (mais recente) do protocolo TLS utilizada por uma determinada sessão. Isto permite ao NetX Secure TLS utilizar uma versão mais antiga do TLS para uma Sessão TLS específica sem desativar as versões TLS mais recentes no momento da compilação. Isto pode ser útil em aplicações que possam necessitar de comunicar com um anfitrião mais antigo que não suporte a versão mais recente do TLS.

> [!IMPORTANT]
> *A partir da versão 5.11SP3, o NetX Secure TLS suporta o RFC 7507 (ver nota abaixo) e qualquer substituição a uma versão mais antiga com esta API resultará no envio de um SCSV de recuo no ClientHello. Se o servidor suportar uma versão mais recente do TLS e o SCSV de retorno de retorno estiver incluído no ClientHello, esse servidor abortará o aperto de mão TLS com um alerta de "Fallback Inadequado". O SCSV só é enviado quando a versão é uma versão mais antiga do TLS do que está ativada (por exemplo, se substituir a versão para TLS 1.2, não será enviado nenhum SCSV).*

Os valores válidos para o parâmetro protocol_version são as seguintes macros: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1 e NX_SECURE_TLS_VERSION_TLS_1_2.

As macros NX_SECURE_TLS_DISABLE_TLS_1_1 e NX_SECURE_TLS_ENABLE_TLS_1_0 podem ser usadas para controlar as versões de TLS que são compiladas na aplicação. A versão 1.2 do TLS está sempre ativada.

De notar que se o anfitrião remoto não suportar a versão fornecida, a ligação falhará – apenas a versão de substituição fornecida será negociada pelo NetX Secure TLS.

> [!IMPORTANT]
> RFC 7507: TLS Fallback SCSV. Este RFC foi introduzido para mitigar um problema de segurança que foi originalmente causado por servidores que manuseavam indevidamente a negociação de downgrade de protocolos e, em vez disso, rejeitaram mensagens De acordo com o ClientHello válidas. Numa tentativa de se manterem compatíveis com estes antigos servidores, algumas aplicações de clientes TLS começaram a voltar a tentar apertos de mão falhados com a versão TLS mais antiga (por exemplo, TLS 1.2 falhou por isso experimente o TLS 1.1). No entanto, esta solução introduziu um novo problema – um intruso poderia forçar um cliente a desvalorizar introduzindo artificialmente um erro de rede ou pacote que fez com que a ligação do servidor falhasse – mesmo quando o servidor suportava a versão TLS mais recente. Ao reduzir para uma versão mais antiga, o intruso poderia explorar fraquezas nessa versão (o SSLv3<sup>21</sup> em particular é fraco para o ataque do POODLE). Para evitar esta situação, o RFC 7507 intrometia o "BACKSV de recuo", um pseudo-cifrassuite<sup>22</sup> enviado no ClientHello que notifica um servidor TLS quando um cliente TLS está a usar uma versão TLS que não é a versão mais recente que suporta. Desta forma, um servidor que suporte uma versão mais recente pode rejeitar um ClientHello contendo o SCSV de retorno e impedir que o ataque de downgrade seja bem sucedido.

21. O NetX Secure não implementa o SSLv3 devido à existência de fraquezas graves conhecidas, como o POODLE.

22. Um pseudo-cifrasuite, ou SCSV (Signaling Cipher Suite Value), é um número de cifrasuite reservado que é usado para sinalizar implementações de TLS ativadas sobre funcionalidades que não estavam disponíveis em versões TLS mais antigas. O recuo SCSV e o TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746) são exemplos.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma sessão de TLS.
- **protocol_version** Macro de versão TLS para a versão específica TLS a utilizar.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Mudança de estado bem sucedida.
- **NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Versão TLS conhecida mas não suportada.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Versão do protocolo inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Set the protocol version to be used to TLSv1.1. */
status = nx_secure_tls_session_protocol_version_override(&tls_session,
                                              NX_SECURE_TLS_VERSION_TLS_1_1);

/* This TLS Session will use TLSv1.1 for the handshake and TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);
```

### <a name="see-also"></a>Consulte também

- nx_secure_tls_session_start
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_receive"></a>nx_secure_tls_session_receive

Receber dados de uma Sessão De TLS Segura NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_receive(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço recebe dados da sessão de TLS ativa especificada, manuseando a desencriptação desses dados antes de os fornecer ao chamador no parâmetro NX_PACKET. Se não houver dados na sessão especificada, a chamada suspende com base na opção de espera fornecida.

> [!IMPORTANT]
> *Se NX_SUCCESS for devolvido, o pedido é responsável pela libertação do pacote recebido quando já não for necessário.*

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma sessão de TLS.
- **packet_ptr** Ponteiro para um ponteiro de pacote TLS atribuído.
- **wait_option** Indica quanto tempo o serviço deve esperar por um pacote do anfitrião remoto antes de regressar.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Iniciação bem sucedida da sessão TLS.
- **NX_NO_PACKET** (0x01) Nenhum dado recebido.
- **NX_NOT_CONNECTED** (0x38) A tomada TCP subjacente já não está ligada.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Uma mensagem recebida falhou num cheque de haxixe de autenticação.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Uma mensagem recebida continha uma versão de protocolo desconhecida no seu cabeçalho.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Recebeu um alerta TLS do hospedeiro remoto.
- **NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) A sessão TLS fornecida não foi inicializada.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Receive a packet from an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is received, blocking otherwise.
*/
status =  nx_secure_tls_session_receive(&tls_session, &packet_ptr,
NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the received packet is pointed to by  "packet_ptr". */
```

### <a name="see-also"></a>Consulte também

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_end
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_renegotiate_callback_set"></a>nx_secure_tls_session_renegotiate_callback_set

Atribua uma chamada que será invocada no início de uma renegociação da sessão

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_ session_renegotiate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(struct NX_SECURE_TLS_SESSION_struct
                  *session));
```

### <a name="description"></a>Description

Este serviço atribui uma chamada de volta a uma sessão TLS que será invocada sempre que a primeira mensagem de um aperto de mão de renegociação de sessão for recebida do anfitrião remoto.

A função de retorno destina-se a uma notificação à aplicação de que está a iniciar um aperto de mão de renegociação – a aplicação pode optar por encerrar a sessão TLS devolvendo qualquer valor não nulo da chamada que fará com que a TLS termine a sessão de TLS com um erro. Se o pedido pretender prosseguir com a renegociação, o retorno deve voltar NX_SUCCESS.

> [!NOTE]
> *Devido à semântica da renegociação do TLS, a chamada será invocada para os Clientes NetX Secure TLS sempre que um HelloRequest for recebido do servidor remoto, mas não quando o cliente iniciar a renegociação. Nos Servidores TLS Do NetX Secure, a chamada será invocada sempre que for recebida uma renegociação do ClientHello (qualquer ClientHello recebido no contexto de uma sessão de TLS ativa). Isto significa que a chamada será invocada se o anfitrião remoto ou a aplicação local iniciaram a renegociação porque o servidor TLS enviará um HelloRequest ao qual o cliente remoto responderá.*

NetX Secure TLS implementa a Extensão de Insidição de Renegociação Segura do RFC 5746 para garantir que os apertos de mão de renegociação não estão sujeitos a ataques man-in-the-middle.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para a sessão TLS.
- **func_ptr** Ponteiro para a função de retorno de chamadas.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Atribuição bem sucedida de chamadas.
- **NX_PTR_ERROR** (0x07) Tentou utilizar um ponteiro inválido para a função de retorno ou sessão TLS.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_tls_session_create
- nx_secure_tls_session_start
- nx_secure_tls_session_receive
- nx_secure_tls_session_send
- nx_secure_tls_session_renegotiate

## <a name="nx_secure_tls_session_renegotiate"></a>nx_secure_tls_session_renegotiate

Inicie um aperto de mão de renegociação de sessão com o anfitrião remoto

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_ session_renegotiate (
                  NX_SECURE_TLS_SESSION *tls_session,
                  UINT wait_option);
```

### <a name="description"></a>Description

Este serviço inicia um aperto de mão *de renegociação* de sessão com um anfitrião TLS remoto conectado. Uma renegociação consiste num segundo aperto de mão TLS no contexto de uma sessão TLS previamente estabelecida. Cada uma das novas mensagens de aperto de mão é encriptada utilizando a sessão TLS até que novas teclas de sessão sejam geradas e as mensagens ChangeCipherSpec sejam trocadas, altura em que as novas teclas são usadas para encriptar todas as mensagens.

Uma renegociação pode ser iniciada a qualquer momento uma vez que uma sessão TLS é estabelecida. Se uma renegociação for tentada durante um aperto de mão TLS ou antes de uma sessão TLS ser estabelecida, não serão tomadas medidas.

> [!NOTE]
> *Um aperto de mão TLS inteiro será realizado quando este serviço for invocado para que o tempo de conclusão e o estado devolvido variem dependendo das definições e parâmetros de sessão atuais do TLS.*

NetX Secure TLS implementa a Extensão de Insidição de Renegociação Segura do RFC 5746 para garantir que os apertos de mão de renegociação não estão sujeitos a ataques man-in-the-middle.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para a sessão TLS.
- **wait_option** Indica quanto tempo o serviço deve esperar por um pacote do anfitrião remoto antes de regressar. Isto é passado para todos os serviços NetX dentro de TLS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Renegociação bem sucedida.
- **NX_NO_PACKET** (0x01) Nenhum dado recebido.
- **NX_NOT_CONNECTED** (0x38) A tomada TCP subjacente já não está ligada.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Uma mensagem recebida falhou num cheque de haxixe de autenticação.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Uma mensagem recebida continha uma versão de protocolo desconhecida no seu cabeçalho.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Recebeu um alerta TLS do hospedeiro remoto.
- **NX_SECURE_TLS_RENEGOTIATION_SESSION_INATIVE** (0x134) A sessão TLS local ou remota está inativa, tornando impossível a renegociação.
- **NX_SECURE_TLS_RENEGOTIATION_FAILURE** (0x13A) O anfitrião remoto não forneceu nem a extensão de renegociação segura do SCSV nem a extensão de renegociação segura, pelo que a renegociação não pode ser realizada.
- **NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) A sessão TLS fornecida não foi inicializada.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) A atribuição de pacotes subjacentes falhou.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_tls_session_create
- nx_secure_tls_session_start
- nx_secure_tls_session_receive
- nx_secure_tls_session_send
- nx_secure_tls_session_renegotiation_callback_set

## <a name="nx_secure_tls_session_reset"></a>nx_secure_tls_session_reset

Limpe e reponha uma Sessão de TLS De Segurança NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_reset (NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>Description

Este serviço limpa uma sessão de TLS e repõe o estado como se a sessão tivesse acabado de ser criada para que um objeto de sessão TLS existente possa ser reutilizado para uma nova sessão.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma sessão de TLS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Iniciação bem sucedida da sessão TLS.
- **NX_INVALID_PARAMETERS** (0x4D) Ponteiro de sessão de TLS inválido.
- **NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Reset a TLS session.  */
status =  nx_secure_tls_session_reset(&tls_session);


/* If status is NX_SUCCESS the session was successfully reset and may be reused.*/
```

### <a name="see-also"></a>Consulte também

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_send"></a>nx_secure_tls_session_send

Enviar dados através de uma Sessão De TLS Segura NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_send(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET *packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço envia dados no NX_PACKET fornecido, utilizando a sessão de TLS ativa especificada, e manuseando a encriptação desses dados antes de os enviar para o anfitrião remoto. Se o último tamanho da janela anunciado pelo recetor for inferior a este pedido, o serviço suspende opcionalmente com base nas opções de espera especificadas.

> [!IMPORTANT]
> *A menos que um erro seja devolvido, o pedido não deve libertar o pacote após esta chamada. Ao fazê-lo, o controlador da rede libertará o pacote após a transmissão.*

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma sessão de TLS.
- **packet_ptr** Ponteiro para um pacote TLS contendo dados a enviar.
- **wait_option** Define como o serviço se comporta se o pedido for maior do que o tamanho da janela do recetor.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Iniciação bem sucedida da sessão TLS.
- **NX_NO_PACKET** (0x01) Nenhum dado recebido.
- **NX_NOT_CONNECTED** (0x38) A tomada TCP subjacente já não está ligada.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) A tomada TCP subjacente falhou.
- **NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) A sessão TLS fornecida não foi inicializada.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Send a packet using an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is sent, blocking otherwise.   */
status =  nx_secure_tls_session_send(&tls_session, &packet_ptr, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the packet has been sent. */
```

### <a name="see-also"></a>Consulte também

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_packet_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_receive
- nx_secure_tls_session_end
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_server_callback_set"></a>nx_secure_tls_session_server_callback_set

Configurar uma chamada para o TLS invocar no início de um aperto de mão do TLS Server

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_ session_server_callback_set (
                 NX_SECURE_TLS_SESSION *tls_session,
                 ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                   NX_SECURE_TLS_HELLO_EXTENSION
                                   *extensions, UINT num_extensions));
```

### <a name="description"></a>Description

Este serviço atribui um ponteiro de função a uma sessão de TLS que o TLS invocará quando um aperto de mão do Servidor TLS tiver recebido uma mensagem ClientHello. A função de retorno permite que uma aplicação processe quaisquer extensões TLS da mensagem ClientHello recebida que exijam entrada ou tomada de decisão.

O retorno é executado com o bloco de controlo de sessão TLS invocando e uma série de objetos NX_SECURE_TLS_HELLO_EXTENSION. A matriz de objetos de extensão destina-se a ser passada para uma função auxiliar que irá encontrar e analisar uma extensão específica. Para uma função de ajudante de exemplo que analisa as extensões TLS fornecidas em mensagens hello, consulte *nx_secure_tls_session_sni_extension_parse*.

O retorno do servidor também pode ser usado para selecionar o certificado de identidade ativo utilizando *nx_secure_tls_ative_certificate_set* para o Servidor TLS. Isto ocorrerá na maioria das vezes em resposta a uma extensão de Indicação de Nome do Servidor (SNI) que permite a um Cliente TLS indicar que servidor está a tentar contactar. Consulte as referências para *nx_secure_tls_session_sni_extension_parse* e *nx_secure_tls_ative_certificate_set* para obter mais informações.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.
- **func_ptr** Ponteiro para a função de retorno do servidor TLS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Atribuição bem sucedida do ponteiro função.
- **NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_tls_session_create
- nx_secure_tls_session_client_callback_set
- nx_secure_tls_active_certificate_set
- nx_secure_tls_session_sni_extension_parse
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_find

## <a name="nx_secure_tls_session_sni_extension_parse"></a>nx_secure_tls_session_sni_extension_parse

Parse uma extensão de indicação de nome do servidor (SNI) recebida de um cliente TLS

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_sni_extension_parse(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions,
                                    UINT num_extensions,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a>Description

Este serviço destina-se a ser chamado a partir de uma chamada de sessão do TLS Server, adicionada a uma sessão de TLS utilizando nx_secure_tls_session_server_callback_set. A chamada é invocada após a receção de uma mensagem ClientHello de um cliente TLS remoto e é fornecida uma série de extensões disponíveis (e o número de extensões na matriz). Este conjunto e o seu comprimento podem ser transmitidos diretamente a esta rotina para determinar se existe uma extensão SNI presente – se não, NX_SECURE_TLS_EXTENSION_NOT_FOUND é devolvida, indicando simplesmente que o cliente optou por não provicendo a extensão SNI (isto não é um erro).

Se a extensão SNI for encontrada, o nome DNS X.509 fornecido pelo cliente TLS é devolvido na estrutura dns_name. Atualmente, a extensão SNI apenas fornece uma única entrada de nome DNS, que pode ser usada pelo servidor TLS para determinar que certificado de identidade enviar para o cliente remoto.**

A estrutura NX_SECURE_X509_DNS_NAME contém simplesmente o nome DNS como uma cadeia UCHAR no campo *nx_secure_x509_dns_name* e o comprimento da cadeia de nomes em *nx_secure_x509_dns_name_length*. O NX_SECURE_X509_DNS_NAME_MAX macro controla o tamanho do tampão nx_secure_x509_dns_name.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma sessão de TLS.
- **extensões** Ponteiro para uma variedade de extensões TLS Hello (a partir de chamada de sessão).
- **num_extensions** Número de extensões na matriz (a partir da chamada de sessão).
- **dns_name** Devolução do nome DNS fornecido na extensão SNI.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Análise bem sucedida da extensão.
- **NX_PTR_ERROR** (0x07) Matriz de extensões inválidas ou ponteiro de sessão TLS.
- **NX_SECURE_TLS_EXTENSION_NOT_FOUND** (0x136) extensão do SNI não encontrada.
- **NX_SECURE_TLS_SNI_EXTENSION_INVALID** (0x137) o formato de extensão SNI era inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

### <a name="see-also"></a>Consulte também

- nx_secure_tls_session_server_callback_set
- nx_secure_tls_session_client_callback_set
- nx_secure_tls_server_callback_set
- nx_secure_tls_active_certificate_set

## <a name="nx_secure_tls_session_sni_extension_set"></a>nx_secure_tls_session_sni_extension_set

Desa estade um nome DNS de extensão de extensão de nome do servidor (SNI) para enviar para um servidor remoto

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_sni_extension_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a>Description

Este serviço permite que uma aplicação do Cliente TLS forneça um nome DNS de servidor preferido a um servidor TLS remoto utilizando a extensão TLS de Indicação de Nome do Servidor (SNI). A extensão SNI permite ao servidor selecionar o certificado de identidade e parâmetros adequados com base na preferência indicada do servidor do cliente. A extensão SNI suporta atualmente apenas um único nome DNS a ser enviado, daí o parâmetro de nome singular. O parâmetro dns_name deve ser inicializado com *nx_secure_x509_dns_name_initialize* e conterá o servidor preferido do cliente. Para desaparar o nome da extensão, basta ligar para este serviço com um valor de parâmetro "dns_name" de NX_NULL.

A estrutura NX_SECURE_X509_DNS_NAME contém simplesmente o nome DNS como uma cadeia UCHAR no campo  *nx_secure_x509_dns_name* e o comprimento da cadeia de nomes em *nx_secure_x509_dns_name_length*. O NX_SECURE_X509_DNS_NAME_MAX macro controla o tamanho do tampão nx_secure_x509_dns_name.

> [!NOTE]
> *Esta rotina deve ser chamada antes de nx_secure_tls_session_start ser invocada ou o ClientHello não conterá a extensão SNI.*

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma sessão de TLS.
- **dns_name** Nome DNS fornecido pela aplicação.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Adição bem sucedida do nome do servidor DNS.
- **NX_PTR_ERROR** (0x07) Nome DNS inválido ou ponteiro de sessão TLS.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_tls_session_start
- nx_secure_x509_dns_name_initialize

## <a name="nx_secure_tls_session_start"></a>nx_secure_tls_session_start

Inicie uma Sessão De TLS Segura NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_session_start(NX_SECURE_TLS_SESSION *session_ptr,
                                  NX_TCP_SOCKET *tcp_socket_ptr,
                                  ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço inicia uma sessão TLS utilizando o bloco de controlo de sessão TLS fornecido e uma tomada TCP conectada. A ligação TCP já deve estar completa na sequência de uma chamada bem sucedida para nx_tcp_client_socket_connect ou nx_tcp_server_socket_accept.

Este serviço determinará o tipo de sessão TLS (Cliente ou Servidor) a partir da tomada TCP.

A opção de espera define como o serviço se comporta enquanto o aperto de mão TLS está em andamento.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma sessão de TLS.
- **tcp_socket_ptr** Ponteiro para uma tomada TCP ligada.
- **wait_option** Define como o serviço se comporta enquanto o aperto de mão TLS está em andamento.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Iniciação bem sucedida da sessão TLS.
- **NX_NOT_CONNECTED** (0x38) A tomada TCP subjacente já não está ligada.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) Um tipo de mensagem TLS recebido está incorreto.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) Uma cifra fornecida pelo hospedeiro remoto não é suportada.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) O processamento de mensagens durante o aperto de mão TLS falhou.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Uma mensagem recebida falhou numa verificação de HASH MAC.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Um envio de tomada TCP subjacente falhou.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Uma mensagem recebida tinha um campo de comprimento inválido.
- **NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) Uma mensagem ChangeCipherSpec recebida estava incorreta.
- **NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) Um certificado TLS de entrada é inutilizável para identificar o servidor TLS remoto.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) A cifra de chave pública fornecida pelo hospedeiro remoto não é suportada.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) O anfitrião remoto não indicou cifrasuites que sejam suportadas pela pilha NetX Secure TLS.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Uma mensagem TLS recebida tinha uma versão TLS desconhecida no seu cabeçalho.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Uma mensagem TLS recebida tinha uma versão TLS conhecida mas não suportada no seu cabeçalho.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Uma atribuição interna de pacotes TLS falhou.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) O anfitrião remoto forneceu um certificado inválido.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) O anfitrião remoto enviou um alerta indicando um erro e terminando a sessão TLS.
- **NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) Uma entrada na tabela cifrasumita tinha um ponteiro de função NU.
- **NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** (0x146) Um cliente remoto TLS ClientHello incluiu o recuo SCSV e atacou um retorno de versão.
- **NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_send
- nx_secure_tls_session_delete
- nx_secure_tls_session_receive
- nx_secure_tls_packet_allocate
- nx_secure_tls_session_end
- nx_secure_tls_session_create
- nx_tcp_socket_accept
- nx_tcp_socket_listen
- nx_tcp_socket_disconnect
- nx_tcp_socket_unaccept
- nx_tcp_socket_relisten
- nx_tcp_socket_delete
- nx_packet_allocate
- nx_packet_data_append
- nx_packet_data_extract_offset

## <a name="nx_secure_tls_session_time_function_set"></a>nx_secure_tls_session_time_function_set

Atribua uma função de marcação de tempo a uma Sessão TLS Segura NetX

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_time_function_set(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              ULONG (*time_func_ptr)(void));
```

### <a name="description"></a>Description

Esta função configura um ponteiro de função que o TLS invocará quando precisar de obter o tempo atual, que é usado em várias mensagens de aperto de mão TLS e para verificação de certificados.

Espera-se que a função devolva o atual GMT em UNIX formato de 32 bits (segundos desde a meia-noite a partir de 1 de janeiro de 1970, UTC, ignorando os segundos de salto), de acordo com os requisitos do ClientHello no TLS RFC 5246.

Se não for atribuída nenhuma função de calibragem de tempo, será utilizado um valor de 0 para o tempo de calibragem no aperto de mão TLS e a verificação de expiração do certificado não funcionará.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma sessão de TLS.
- **time_func_ptr** Ponteiro para uma função que retorna a hora atual (GMT) em UNIX formato de 32 bits.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Iniciação bem sucedida da sessão TLS.
- **NX_INVALID_PARAMETERS** (0x4D) Ponteiro de sessão de TLS inválido.
- **NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_sendnx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_trusted_certificate_add"></a>nx_secure_tls_trusted_certificate_add

Adicionar certificado fidedigno à Sessão TLS Do NetX Secure

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_trusted_certificate_add(NX_SECURE_TLS_SESSION
                            *session_ptr, NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a>Description

Este serviço adiciona uma instância de estrutura de NX_SECURE_X509_CERT inicializada a uma sessão de TLS. Este certificado é utilizado pela pilha TLS para verificar os certificados fornecidos pelo anfitrião remoto durante o aperto de mão TLS.

São necessários certificados fidedignos para o modo cliente TLS.

Os certificados fidedignos só são necessários para o modo TLS Server se a autenticação do certificado do cliente estiver ativada.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.
- **certificate_ptr** Ponteiro para uma instância inicializada do Certificado TLS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Adição bem sucedida do certificado.
- **NX_INVALID_PARAMETERS** (0x4D) Tentou adicionar um certificado inválido.
- **NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_trusted_certificate_remove

## <a name="nx_secure_tls_trusted_certificate_remove"></a>nx_secure_tls_trusted_certificate_remove

Remover certificado fidedigno da Sessão TLS Do NetX Secure

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_tls_trusted_certificate_remove(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *common_name,
                                    UINT common_name_length);
```

### <a name="description"></a>Description

Este serviço remove um certificado de confiança de uma sessão de TLS, insutado no campo Nome Comum no certificado.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para uma instância de Sessão TLS previamente criada.
- **common_name** O valor do nome comum do certificado a retirar.
- **common_name_length** O comprimento da corda nome comum.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Adição bem sucedida do certificado.
- **NX_PTR_ERROR** (0x07) Ponteiro de sessão de TLS inválido.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** certificado (0x119) não foi encontrado.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Remove certificate from TLS session.  */
status =  nx_secure_tls_trusted_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a>Consulte também

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_trusted_certificate_add

## <a name="nx_secure_x509_certificate_initialize"></a>nx_secure_x509_certificate_initialize

Inicializar o Certificado X.509 para NetX Secure TLS

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Description

Este serviço inicializa uma estrutura NX_SECURE_X509_CERT a partir de um certificado digital X.509 codificado binário para utilização numa sessão de TLS.

Os dados do certificado **devem** ser um certificado digital X.509 válido em formato binário codificado pelo DER. Os dados podem alguns de qualquer fonte (por exemplo, sistema de ficheiros, tampão constante compilado, etc.) desde que seja fornecido um ponteiro UCHAR para esses dados.

O *parâmetro raw_data_buffer* e o seu tamanho são parâmetros opcionais que especificam um tampão dedicado no qual os dados do certificado são copiados antes da análise. Se raw_data_buffer for passado como NX_NULL, então a estrutura NX_SECURE_X509_CERT apontará diretamente para a matriz certificate_data (buffer_size é ignorada neste caso). Se raw_data_buffer for passado como NX_NULL, ***não*** modifique os dados apontados pelo ponteiro certificate_data ou o tratamento de certificados provavelmente falhará!

O parâmetro chave privado é para certificados de identidade locais – a chave privada é usada pelos servidores para desencriptar os dados chave de entrada de um cliente (encriptado usando a chave pública do servidor) e pelos clientes para verificar a sua identidade num servidor quando o servidor solicita um certificado de cliente. A adição de uma chave privada com esta API marcará automaticamente o certificado associado como sendo um certificado de identidade para um pedido TLS. Ao rubricar certificados para outros fins (por exemplo, a loja de confiança), o parâmetro *private_key_data* deve ser passado como NULO, o *private_key_data_length* como 0, e o *private_key_type* deve ser passado como NX_SECURE_X509_KEY_TYPE_NONE.

O *parâmetro private_key_type* indica a formatação da chave privada. Por exemplo, se a chave privada for uma chave privada RSA codificada por PKCS#1, o private_key_type deve ser passado como NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER, um tipo conhecido por NetX Secure que será analisado imediatamente e guardado para posterior utilização.

O private_key_type também suporta os tipos de chave definidos pelo utilizador<sup>23</sup> para plataformas e aplicações que possuam formatos-chave específicos ou outras necessidades. Por exemplo, um motor de encriptação baseado em hardware pode usar um formato específico não compreendido pelo software NetX Secure, ou uma chave privada pode ser encriptada ou representada por um token criptográfico, como pode acontecer com um Módulo de Plataforma Fidedigna (TPM) ou hardware criptográfico PKCS#11. Quando um tipo de chave definido pelo utilizador é utilizado, os dados-chave são transmitidos verbatim à rotina criptográfica apropriada - por exemplo, uma chave privada RSA seria passada, sem qualquer análise ou processamento, diretamente para a rotina criptográfica RSA fornecida ao TLS na tabela de cifrasuite. O tipo de chave definida pelo utilizador também é passado para a rotina criptográfica (no caso da RSA, este é o parâmetro "op").

A gama de teclas definidas pelo utilizador cobre a metade superior de um número inteiro não assinado de 32 bits, de 0x0001 FFFF de 0000 0xFFFF. Valores inferiores 0x0001 0000 estão reservados para utilização NetX Secure.

Os tipos de chaves definidos pelo utilizador são uma funcionalidade avançada que requer rotinas criptográficas personalizadas para lidar com os dados de chave privadas cruas. Contacte o seu representante express logic se precisar desta funcionalidade.

### <a name="parameters"></a>Parâmetros

- **certificate_ptr** Ponteiro para uma instância de certificado X.509 não ininitializada.
- **certificate_data** Ponteiro para dados binários de X.509 codificados pelo DER.
- **raw_data_buffer** Ponteiro para o tampão de dados de certificado dedicado opcional.
- **buffer_size** Tamanho do tampão de dados de certificado dedicado opcional.
- **certificate_data_length** Duração dos dados binários de certificados em bytes.
- **private_key_data** Ponteiro para dados chave privados opcionais.
- **private_key_data_length** Duração dos dados das chaves privadas.
- **private_key_type** Identificador do tipo chave.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Adição bem sucedida do certificado.
- **NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) Os dados do certificado não continham um certificado X.509 codificado pelo DER.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** certificado (0x10D) não tinha uma cifra de chave pública que é suportada pela NetX Secure.
- **NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** (0x186) A chave ou certificado privado não continha uma sequência ASN.1 válida.
- **NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** (0x18A) A chave privada fornecida não era uma chave PKCS#1 RSA válida.
- **NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** (0x19D) O tipo de chave privada fornecido não foi definido pelo utilizador e não corresponde a qualquer tipo conhecido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Initialize certificate structure. The certificate structure will point directly
   into the certificate_data array since we are passing the raw_data_buffer as
   NX_NULL. This certificate has a private key so it will be used to identify this
   device. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, NX_NULL, 0, private_key, 64, NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);


/* If status is NX_SUCCESS the certificate was successfully initialized.  */
```

### <a name="see-also"></a>Consulte também

- nx_secure_local_certificate_add
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- Importar certificados X.509 para NetX Secure no capítulo 3.

## <a name="nx_secure_x509_common_name_dns_check"></a>nx_secure_x509_common_name_dns_check

Verifique o nome DNS contra o Certificado X.509

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_x509_common_name_dns_check(
                        NX_SECURE_X509_CERT *certificate,
                        const UCHAR *dns_tld, UINT dns_tld_length);
```

### <a name="description"></a>Description

Este serviço verifica o Nome Comum de um certificado contra um nome de domínio superior (TLD) fornecido pelo chamador para efeitos de validação de DNS de um anfitrião remoto. Esta função de utilidade destina-se a ser chamada a partir de uma rotina de validação de certificado fornecida pela aplicação. O nome TLD deve ser a parte superior do URL utilizado para aceder ao hospedeiro remoto (o "". -corda separada antes do primeiro corte). Se o Nome Comum contiver um wildcard (como *.example.com), o wildcard combinará qualquer um com o mesmo sufixo. Note que apenas o primeiro wildcard ("*") encontrado (lendo da direita para a esquerda) será considerado para correspondência wildcard – por exemplo, abc.*.exemplo.com corresponderá *a qualquer* nome que termine em ".example.com".

Se o Nome Comum não corresponder à cadeia fornecida, a extensão "subjectAltName" é analisada (se existir no certificado) e são também comparadas quaisquer entradas DNSName. Se nenhuma dessas entradas corresponder, um erro é devolvido.

É importante compreender o formato do nome comum (e submeter entradas de NomeAlt) nos certificados esperados. Por exemplo, alguns certificados podem usar um endereço IP cru ou um wild card. A cadeia DNS TLD deve ser formatada de modo a corresponder aos valores esperados nos certificados recebidos.

### <a name="parameters"></a>Parâmetros

- **certificate_ptr** Ponteiro para uma instância de certificado X.509.
- **dns_tld** Top-Level nome de domínio para comparar.
- **dns_tld_length** Comprimento da corda TLD.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Comparação bem sucedida com nome comum ou nome sujeitoAlme.
- **NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** (0x195) Não foi encontrado nenhum nome correspondente.
- **NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_tls_session_create
- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_crl_revocation_check

## <a name="nx_secure_x509_crl_revocation_check"></a>nx_secure_x509_crl_revocation_check

Verifique o Certificado X.509 com uma Lista de Revogação de Certificados (CRL)

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_x509_crl_revocation_check(const UCHAR *crl_data,
                              UINT crl_length,
                              NX_SECURE_X509_CERTIFICATE_STORE *store,
                              NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a>Description

Este serviço requer uma Lista de Revogação de Certificado codificada pelo DER e procura um certificado específico nessa lista. O emitente do CRL é validado contra uma loja de certificados fornecida, o emitente CRL é validado para ser o mesmo que o certificado que está a ser verificado, e o número de série do certificado em questão é utilizado para pesquisar a lista de certificados revogados. Se os emitentes coincidirem, a assinatura confere e o certificado **não** está presente na lista, a chamada é bem sucedida. Todos os outros casos causam um erro a ser devolvido.

### <a name="parameters"></a>Parâmetros

- **crl_data** Ponteiro para um CRL codificado pelo DER.
- **crl_length** Comprimento em bytes de dados CRL.
- **loja** Ponteiro para uma loja de certificados X.509.
- **certificate_ptr** Ponteiro para uma instância de certificado X.509.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Validação bem sucedida de que o certificado não foi revogado.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) certificado de emitente CRL não encontrado.
- **NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** 0x11B) Certificado emitente de certificado não encontrado.
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) O CRL ASN.1 continha um campo de comprimento inválido.
- **NX_SECURE_X509_UNEXPECTED_ASN1_TAG(0x189)** O CRL continha ASN.1 inválido.
- **NX_SECURE_X509_CHAIN_VERIFY_FAILURE** (0x18C) Uma verificação da cadeia de certificados falhou.
- **NX_SECURE_X509_CRL_ISSUER_MISMATCH** (0x197) CRL e emitentes de certificados não correspondia.
- **NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** 0x198) A assinatura CRL foi inválida.
- **NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** (0x199) O certificado que está a ser verificado foi encontrado no CRL e, por conseguinte, revogado.
- **NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_tls_session_create
- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_common_name_dns_check

## <a name="nx_secure_x509_dns_name_initialize"></a>nx_secure_x509_dns_name_initialize

Inicialize uma estrutura de nomeS DNS X.509

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_x509_dns_name_initialize(
                        NX_SECURE_X509_DNS_NAME *dns_name,
                        const UCHAR *name_string, UINT length);
```

### <a name="description"></a>Description

Este serviço inicializa um nome DNS X.509 para utilização com certos serviços API que requerem um formato de nome específico. Por exemplo, o serviço *nx_secure_tls_sni_extension_parse* espera que um objeto NX_SECURE_X509_DNS_NAME para corresponder ao nome fornecido por um anfitrião remoto na extensão de indicação de nome do servidor durante o aperto de mão TLS. Um nome DNS é simplesmente uma corda de charater com um comprimento – o comprimento máximo permitido de um nome DNS (e o tamanho do tampão interno em NX_SECURE_X509_DNS_NAME) é controlado pelo NX_SECURE_X509_DNS_NAME_MAX macro (padrão 100 bytes).

### <a name="parameters"></a>Parâmetros

- **dns_name** Estrutura de nome DNS para inicializar.
- **name_string** Dados de cadeia de nome DNS.
- **comprimento** Comprimento da corda do nome.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Inicialização bem sucedida.
- **NX_SECURE_X509_NAME_STRING_TOO_LONG** (0x19E) A cadeia de nomes foi excedida NX_SECURE_X509_DNS_NAME_MAX.
- **NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
NX_SECURE_X509_DNS_NAME dns_name;

/* Initialize DNS name. */
status = nx_secure_x509_dns_name_initialize(&dns_name, “www.example.com”,
                                            strlen(“www.example.com”);

/* Use initialized DNS name to send the Server Name Indication extension to the
   remote TLS server. */
status = nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);
```

### <a name="see-also"></a>Consulte também

- nx_secure_tls_session_create
- nx_secure_tls_session_sni_extension_parse
- nx_secure_tls_session_sni_extension_set

## <a name="nx_secure_x509_extended_key_usage_extension_parse"></a>nx_secure_x509_extended_key_usage_extension_parse

Encontre e analise uma extensão de utilização estendida X.509 num certificado X.509

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_x509_extended_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        UINT key_usage);
```

### <a name="description"></a>Description

Este serviço destina-se a ser chamado a partir de uma chamada de verificação de certificado (ver *nx_secure_tls_session_certificate_callback_set)*. Procurará uma chave específica de utilização OID dentro de um certificado X.509 e devolverá se o OID está presente. O parâmetro key_usage é um mapeamento inteiro dos OIDs que é usado internamente por NetX Secure X.509 e TLS para evitar passar as cordas OID de comprimento variável como parâmetros.

Os OIDs relevantes para a extensão de utilização da chave estendida são indicados na tabela abaixo. Uma implementação típica do Cliente TLS que pretenda verificar a utilização de chaves estendidas num certificado de servidor TLS recebido verificaria a existência do NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH OID – se a extensão estiver presente mas que o OID não estiver, então o certificado seria considerado inválido para identificar o anfitrião como um servidor TLS e a chamada de verificação do certificado deve devolver um erro. Se a extensão em si faltar, então cabe à aplicação proceder ou não com o aperto de mão TLS.

Na chamada de verificação do certificado, o código de devolução de erros NX_SECURE_X509_KEY_USAGE_ERROR está reservado para utilização de pedidos. Se houver um erro na verificação da utilização da chave, este valor pode ser devolvido da chamada para indicar o motivo da falha.

| Identificador de segurança NetX                                | Valor OID         | Description                                      |
| --------------------------------------------------------- | --------------------- | ---------------------------------------------------- |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH   | 1.3.6.1.5.5.7.3.1 | O certificado pode ser usado para identificar um servidor TLS |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH   | 1.3.6.1.5.5.7.3.2 | O certificado pode ser usado para identificar um cliente TLS |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING  | 1.3.6.1.5.5.7.3.3 | O certificado pode ser usado para assinar código             |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT | 1.3.6.1.5.5.7.3.4 | O certificado pode ser usado para assinar e-mails           |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING | 1.3.6.1.5.5.7.3.8 | O certificado pode ser usado para assinar os tempos dos tempos       |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING  | 1.3.6.1.5.5.7.3.9 | O certificado pode ser usado para assinar respostas OCSP   |

OIDs e mapeamentos para X.509 Extensão de Utilização de Chave Estendida

### <a name="parameters"></a>Parâmetros

- **certificado** Ponteiro para certificado sendo verificado.
- **key_usage** Mapeamento inteiro OID da tabela acima.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Utilização de chave especificada OID encontrada.
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 tag multi-byte encontrada (certificado não suportado).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Campo Invaild ASN.1 encontrado (certificado inválido).
- **NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Classe de tag ASN.1 inválida encontrada (certificado inválido).
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Extensão inválida encontrada (certificado inválido).
- **NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) A extensão de utilização da chave estendida não foi encontrada no certificado fornecido.
- **NX_PTR_ERROR** (0x07) Ponteiro de certificado inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_key_usage_extension_parse
- nx_secure_x509_crl_revocation_check
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_extension_find

## <a name="nx_secure_x509_extension_find"></a>nx_secure_x509_extension_find

Encontre e devolva uma extensão X.509 num certificado X.509

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_x509_extension_find(
                        NX_SECURE_X509_CERT *certificate,
                        NX_SECURE_X509_EXTENSION *extension,
                        USHORT extension_id);
```

### <a name="description"></a>Description

Este serviço destina-se a ser chamado a partir de uma chamada de verificação de certificado (ver *nx_secure_tls_session_certificate_callback_set)* e é um serviço avançado X.509.

A função procurará uma extensão específica dentro de um certificado X.509 com base num OID e devolverá se o OID está presente, juntamente com uma estrutura que contém referências aos dados de extensão bruta relevantes. O parâmetro extension_id é um mapeamento inteiro dos OIDs que é usado internamente por NetX Secure X.509 e TLS para evitar passar as cordas OID de comprimento variável como parâmetros.

As funções de ajudante previstas para extensões específicas (como *nx_secure_x509_key_usage_extension_parse*) chamam nx_secure_x509_extension_find internamente para obter os dados de extensão.

Os OIDs relevantes para extensões conhecidas de X.509 são indicados na tabela abaixo.

A estrutura NX_SECURE_X509_EXTENSION contém ponteiros no certificado X.509 que permitem que funções de ajudante, tais como *nx_secure_x509_key_usage_extension_parse,* descodificem rapidamente os dados ASN.1 codificados pela extensão bruta DER.

Para obter informações sobre extensões específicas, consulte RFC 5280 (especificação X.509) ou a referência para as funções de ajudante adequadas, se disponível.

A versão atual do NetX Secure X.509 tem suporte limitado para extensões X.509. No futuro, serão adicionadas mais funções de ajudante.

> [!IMPORTANT]
> *Este serviço é uma funcionalidade avançada para utilizadores familiarizados com extensões X.509 e ASN.1 codificadas por DER. É fornecido para permitir que esses utilizadores acedam a extensões para as quais o NetX Secure X.509 não fornece atualmente funções de ajudante. Para essas extensões sem funções de ajudante, você mesmo terá de analisar o ASN.1 codificado em bruto.*

| Identificador de segurança NetX                              | Valor OID | Description                                                                    | Função ajudante? |
| ------------------------------------------------------- | ------------- | ---------------------------------------------------------------------------------- | -------------------- |
| NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES  | 2.5.29.9  | Atributos do Diretório – atributos básicos de informação sobre o tema do certificado  | No               |
| NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID       | 2.5.29.14 | Usado para identificar uma chave pública específica                                         | No               |
| NX_SECURE_TLS_X509_TYPE_KEY_USAGE             | 2.5.29.15 | Fornece informações sobre utilizações válidas para a chave pública do certificado              | Yes              |
| NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME     | 2.5.29.17 | Fornece nomes DNS alternativos para identificar o certificado                     | Sim<sup>24</sup>        |
| NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME      | 2.5.29.18 | Fornece nomes DNS alternativos para identificar o emitente do certificado            | No               |
| NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS     | 2.5.29.19 | Fornece informações básicas sobre restrições de utilização de certificados                        | No               |
| NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS      | 2.5.29.30 | Usado para limitar nomes de certificados a domínios específicos                        | No               |
| NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION      | 2.5.29.31 | Fornece URIs para distribuição de CRL                                             | No               |
| NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES  | 2.5.29.32 | Lista de políticas de certificados para grandes sistemas PKI                             | No               |
| NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS | 2.5.29.33 | Lista das políticas de certificados de CA                                                | No               |
| NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID     | 2.5.29.35 | Usado para identificar uma chave pública específica associada a uma assinatura de certificado | No               |
| NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS    | 2.5.29.36 | Restrições de política da AC                                                          | No               |
| NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE   | 2.5.29.37 | Informações adicionais de utilização das chaves baseadas em OID                                     | Yes              |
| NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL          | 2.5.29.46 | Fornece informações para a obtenção de CRLs delta                                  | No               |
| NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY     | 2.5.29.54 | Campo de certificados da AC indicando que a AnyPolicy não pode ser utilizada                  | No               |

OIDs e mapeamentos para extensões X.509

24. A extensão SubjectAltName é analisada como parte do nome DNS check no serviço nx_secure_x509_common_name_dns_check.

### <a name="parameters"></a>Parâmetros

- **certificado** Ponteiro para certificado sendo verificado.
- **extensão** Estrutura de devolução contendo ponteiro de dados de extensão e comprimento.
- **extension_id** Mapeamento inteiro OID da tabela acima.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Extensão especificada OID encontrada e dados devolvidos.
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 tag multi-byte encontrada (certificado não suportado).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Campo Invaild ASN.1 encontrado (certificado inválido).
- **NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Classe de tag ASN.1 inválida encontrada (certificado inválido).
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Extensão inválida encontrada
- **NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) A extensão dada não foi encontrada no certificado fornecido.
- **NX_PTR_ERROR** (0x07) Certificado inválido ou ponteiro de extensão.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_key_usage_extension_parse
- nx_secure_x509_crl_revocation_check
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_extended_key_usage_extension_parse

## <a name="nx_secure_x509_key_usage_extension_parse"></a>nx_secure_x509_key_usage_extension_parse

Encontre e analise uma extensão de utilização da chave X.509 num certificado X.509

### <a name="prototype"></a>Prototype

```C
UINT  nx_secure_x509_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        USHORT *bitfield);
```

### <a name="description"></a>Description

Este serviço destina-se a ser chamado a partir de uma chamada de verificação de certificado (ver *nx_secure_tls_session_certificate_callback_set)*. Procurará a extensão de utilização da chave e, se for encontrada, devolverá o bitfield de utilização da chave no parâmetro "bitfield".

As broas, tal como definidas pela especificação X.509 (RFC 5280) são dadas na tabela abaixo. Um bitwise E com o bitmask apropriado (e verificação de não-zero) dará o valor de cada bit.

Note que a codificação deR do bitfield elimina zeros extra, de modo que a posição real dos bits nos dados do certificado bruto será provavelmente diferente das suas posições no campo de bits descodificado. Os bitmasks fornecidos destinam-se apenas a ser utilizados no bitfield descodificado devolvido por *nx_secure_x509_key_usage_extension_parse* e não com os dados de certificados codificados por DER em bruto.

Na chamada de verificação do certificado, o código de devolução de erros NX_SECURE_X509_KEY_USAGE_ERROR está reservado para utilização de pedidos. Se houver um erro na verificação da utilização da chave, este valor pode ser devolvido da chamada para indicar o motivo da falha.

| Identificador de segurança NetX                            | Posição do bit | Description                                                                                                                                                  |
| ----------------------------------------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE  | 0            | O certificado pode ser usado para assinaturas digitais                                                                                                               |
| NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION    | 1            | O certificado pode ser utilizado para verificar assinaturas digitais que não as dos certificados e CRLs                                                              |
| NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT   | 2            | O certificado pode ser usado para encriptar chaves simétricas (transporte de chaves)                                                                                            |
| NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT  | 3            | O certificado pode ser usado para encriptar diretamente os dados brutos dos utilizadores (incomuns)                                                                                         |
| NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT      | 4            | O certificado pode ser usado para um acordo-chave (como com Diffie-Hellman)                                                                                           |
| NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN     | 5            | O certificado pode ser usado para assinar e verificar outros certificados (o certificado é um certificado CA ou ICA).                                                  |
| NX_SECURE_X509_KEY_USAGE_CRL_SIGN           | 6            | A chave pública do certificado é utilizada para verificar assinaturas em CRLs                                                                                                  |
| NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY      | 7            | Usado com bit do Acordo Chave (bit 4) – quando definido, a tecla de certificado só pode ser usada para encriptar durante o acordo-chave. Indefinido se a parte do Acordo-Chave não for definida. |
| NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY      | 8            | Utilizado com bit do Acordo Chave (bit 4) – quando definido, a tecla de certificado só pode ser usada para desencriptar durante o acordo-chave. Indefinido se a parte do Acordo-Chave não for definida. |

Bitmasks e valores para extensão de utilização da chave X.509

### <a name="parameters"></a>Parâmetros

- **certificado** Ponteiro para certificado sendo verificado.
- **bitfield** Devolva todo o campo da extensão.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Extensão de utilização da chave encontrada e bitfield devolvido.
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 tag multi-byte encontrada (certificado não suportado).
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Campo Invaild ASN.1 encontrado (certificado inválido).
- **NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Classe de tag ASN.1 inválida encontrada (certificado inválido).
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Extensão inválida encontrada (certificado inválido).
- **NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B)A extensão de utilização da chave não foi encontrada no certificado fornecido.
- **NX_PTR_ERROR** (0x07) Certificado inválido ou ponteiro bitfield.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

### <a name="see-also"></a>Consulte também

- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_extended_key_usage_extension_parse
- nx_secure_x509_crl_revocation_check
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_extension_find
