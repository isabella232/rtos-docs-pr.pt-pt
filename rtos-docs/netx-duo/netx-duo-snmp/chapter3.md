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
# <a name="chapter-3---description-of-azure-rtos-netx-duo-snmp-agent-services"></a>Capítulo 3 - Descrição dos serviços de agente SNMP da Azure RTOS NetX Duo

Este capítulo contém uma descrição de todos os serviços de agente SNMP Azure RTOS NetX Duo (listados abaixo) por ordem alfabética.

Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

- [nx_snmp_agent_auth_trap_key_use](#nx_snmp_agent_auth_trap_key_use)
   - *Especificar a chave de autenticação (apenas SNMP v3) para mensagens de armadilha*
- [nx_snmp_agent_authenticate_key_use](#nx_snmp_agent_authenticate_key_use)
   - *Especificar a chave de autenticação (apenas SNMP v3) para mensagens de resposta*
- [nx_snmp_agent_community_get](#nx_snmp_agent_community_get)
   - *Recuperar o nome da comunidade*
- [nx_snmp_agent_context_engine_set](#nx_snmp_agent_context_engine_set)
   - *Motor de contexto definido (apenas SNMP v3)*
- [nx_snmp_agent_context_name_set](#nx_snmp_agent_context_name_set)
   - *Definir nome de contexto (apenas SNMP v3)*
- [nx_snmp_agent_create](#nx_snmp_agent_create)
   - *Criar agente SNMP*
- [nx_snmp_agent_current_version_get](#nx_snmp_agent_current_version_get)
   - *Obtenha a versão SNMP do pacote recebido*
- [nx_snmp_agent_request_get_type_test](#nx_snmp_agent_request_get_type_test)
   - *Indicar se o último pedido do SNMP é tipo GET ou SET*
- [nx_snmp_agent_private_string_test](#nx_snmp_agent_private_string_test)
   - *Determine se o string corresponde ao agente corda privada*
- [nx_snmp_agent_public_string_test](#nx_snmp_agent_public_string_test)
   - *Determine se a corda corresponde ao agente de cadeias de cordas públicas*
- [nx_snmp_agent_set_interface](#nx_snmp_agent_set_interface)
   - *Definir interface de rede para mensagens SNMP*
- [nx_snmp_agent_private_string_set](#nx_snmp_agent_private_string_set)
   - *Definir a cadeia de comunidade privada do agente SNMP*
- [nx_snmp_agent_public_string_set](#nx_snmp_agent_public_string_set)
   - *Definir a cadeia da comunidade pública do agente SNMP*
- [nx_snmp_agent_version_set](#nx_snmp_agent_version_set)
   - *Desaponte o estado do agente SNMP para todas as versões SNMP*
- [nx_snmp_agent_delete](#nx_snmp_agent_delete)
   - *Eliminar agente SNMP*
- [nx_snmp_agent_md5_key_create](#nx_snmp_agent_md5_key_create)
   - *Criar tecla md5 (apenas SNMP v3)*
- [nx_snmp_agent_md5_key_create_extended](#nx_snmp_agent_md5_key_create_extended)
   - *Criar tecla md5 (apenas SNMP v3)*
- [nx_snmp_agent_priv_trap_key_use](#nx_snmp_agent_priv_trap_key_use)
   - *Especificar a chave de encriptação (apenas SNMP v3) para mensagens de armadilha*
- [nx_snmp_agent_privacy_key_use](#nx_snmp_agent_privacy_key_use)
   - *Especificar a chave de encriptação (apenas SNMP v3) para mensagens de resposta*
- [nx_snmp_agent_sha_key_create](#nx_snmp_agent_sha_key_create)
   - *Criar tecla sha (apenas SNMP v3)*
- [nx_snmp_agent_sha_key_create_extended](#nx_snmp_agent_sha_key_create_extended)
   - *Criar tecla sha (apenas SNMP v3)*
- [nx_snmp_agent_start](#nx_snmp_agent_start)
   - *Iniciar agente SNMP*
- [nx_snmp_agent_stop](#nx_snmp_agent_stop)
   - *Parar o agente SNMP*
- [nx_snmp_agent_trap_send](#nx_snmp_agent_trap_send)
   - *Enviar armadilha SNMP v1 (apenas IPv4)*
- [nx_snmp_agent_trapv2_send](#nx_snmp_agent_trapv2_send)
   - *Enviar armadilha SNMP v2 (apenas IPv4)*
- [nx_snmp_agent_trapv2_oid_send](#nx_snmp_agent_trapv2_oid_send)
   - *Enviar armadilha SNMP v2 (apenas IPv4) especificando o OID*
- [nx_snmp_agent_trapv3_send](#nx_snmp_agent_trapv3_send)
   - *Enviar armadilha SNMP v3 (apenas IPv4)*
- [nx_snmp_agent_trapv3_oid_send](#nx_snmp_agent_trapv3_oid_send)
   - *Enviar armadilha SNMP v2 (apenas IPv4) especificando o OID*
- [nxd_snmp_agent_trap_send](#nxd_snmp_agent_trap_send)
   - *Enviar armadilha SNMP v1 (IPv4 e IPv6)*
- [nxd_snmp_agent_trapv2_send](#nxd_snmp_agent_trapv2_send)
   - *Enviar armadilha SNMP v2 (IPv4 e IPv6)*
- [nxd_snmp_agent_trapv2_oid_send](#nxd_snmp_agent_trapv2_oid_send)
   - *Enviar armadilha SNMP v2 (IPv4/IPv6) especificando o OID*
- [nxd_snmp_agent_trapv3_send](#nxd_snmp_agent_trapv3_send)
   - *Enviar armadilha SNMP v3 (IPv4 e IPv6)*
- [nxd_snmp_agent_trapv3_oid_send](#nxd_snmp_agent_trapv3_oid_send)
   - *Enviar armadilha SNMP v2 (IPv4/IPv6) especificando o OID*
- [nx_snmp_agent_v3_context_boots_set](#nx_snmp_agent_v3_context_boots_set)
   - *Definir o número de reboots*
- [nx_snmp_object_compare](#nx_snmp_object_compare)
   - *Comparar dois objetos*
- [nx_snmp_object_compare_extended](#nx_snmp_object_compare_extended)
   - *Comparar dois objetos*
- [nx_snmp_object_copy](#nx_snmp_object_copy)
   - *Copiar um objeto*
- [nx_snmp_object_copy_extended](#nx_snmp_object_copy_extended)
   - *Copiar um objeto*
- [nx_snmp_object_counter_get](#nx_snmp_object_counter_get)
   - *Obtenha objeto de contador*
- [nx_snmp_object_counter_set](#nx_snmp_object_counter_set)
   - *Definir objeto de contador*
- [nx_snmp_object_counter64_get](#nx_snmp_object_counter64_get)
   - *Obtenha objeto de contador de 64 bits*
- [nx_snmp_object_counter64_set](#nx_snmp_object_counter64_set)
   - *Definir objeto de contador de 64 bits*
- [nx_snmp_object_end_of_mib](#nx_snmp_object_end_of_mib)
   - *Definir valor final de mib*
- [nx_snmp_object_gauge_get](#nx_snmp_object_gauge_get)
   - *Obtenha objeto de bitola*
- [nx_snmp_object_gauge_set](#nx_snmp_object_gauge_set)
   - *Conjunto de objeto de bitola*
- [nx_snmp_object_id_get](#nx_snmp_object_id_get)
   - *Obter objeto id*
- [nx_snmp_object_id_set](#nx_snmp_object_id_set)
   - *Definir id objeto*
- [nx_snmp_object_integer_get](#nx_snmp_object_integer_get)
   - *Obter objeto inteiro*
- [nx_snmp_object_integer_set](#nx_snmp_object_integer_set)
   - *Definir objeto inteiro*
- [nx_snmp_object_ip_address_get](#nx_snmp_object_ip_address_get)
   - *Obtenha objeto de endereço IP (apenas IPv4)*
- [nx_snmp_object_ip_address_set](#nx_snmp_object_ip_address_set)
   - *Definir objeto de endereço IP (apenas IPv4)*
- [nx_snmp_object_ipv6_address_get](#nx_snmp_object_ipv6_address_get)
   - *Obtenha objeto de endereço IP (apenas IPv6)*
- [nx_snmp_object_ipv6_address_set](#nx_snmp_object_ipv6_address_set)
   - *Definir objeto de endereço IP (apenas IPv6)*
- [nx_snmp_object_no_instance](#nx_snmp_object_no_instance)
   - *Definir valor sem instância*
- [nx_snmp_object_not_found](#nx_snmp_object_not_found)
   - *Definir valor não encontrado*
- [nx_snmp_object_octet_string_get](#nx_snmp_object_octet_string_get)
   - *Obtenha objeto de corda de octeto*
- [nx_snmp_object_octet_string_set](#nx_snmp_object_octet_string_set)
   - *Definir objeto de corda de octeto*
- [nx_snmp_object_string_get](#nx_snmp_object_string_get)
   - *Obtenha objeto de corda ASCII*
- [nx_snmp_object_string_set](#nx_snmp_object_string_set)
   - *Definir objeto de corda ASCII*
- [nx_snmp_object_timetics_get](#nx_snmp_object_timetics_get)
   - *Obter objeto timetics*
- [nx_snmp_object_timetics_set](#nx_snmp_object_timetics_set)
   - *Objeto de timetics definido*

## <a name="nx_snmp_agent_auth_trap_key_use"></a>nx_snmp_agent_auth_trap_key_use
Especificar a chave de autenticação para mensagens de armadilha

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>Descrição

Este serviço especifica a chave a utilizar para definir parâmetros de autenticação no cabeçalho de segurança SNMPv3 em mensagens de armadilha. Fornecer um valor NX_NULL para a autenticação desativar a chave.

> [!NOTE]
> A chave deve ser previamente criada. Veja nx_snmp_agent_md5_key_create ou nx_snmp_agent_sha_key_create.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **chave** Ponteiro para uma tecla MD5 ou SHA previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** conjunto de teclas de autenticação bem sucedidas (0x00).
- **NX_NOT_ENABLED** (0x14) Segurança SNMP desativada 
- **NX_PTR_ERROR** (0x07) Ponteiro do Agente SNMP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Use previously created “my_key” for SNMPv3 trap message authentication.  */
status =  nx_snmp_agent_auth_trap_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for authentication parameters in trap messages.  */
```

## <a name="nx_snmp_agent_authenticate_key_use"></a>nx_snmp_agent_authenticate_key_use
Especificar a chave de autenticação para mensagens de resposta

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr, 
                                        NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>Descrição

Este serviço especifica a chave a utilizar para parâmetros de autenticação no parâmetro de segurança SNMPv3 para todos os pedidos feitos após a sua fixação. Fornecer um valor NX_NULL para a autenticação desativar a chave.

> [!NOTE]
> A chave deve ser previamente criada. Veja nx_snmp_agent_md5_key_create ou nx_snmp_agent_sha_key_create.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **chave** Ponteiro para uma tecla MD5 ou SHA previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Conjunto de teclas SNMP bem sucedida.
- **NX_NOT_ENABLED** (0x14) Segurança SNMP desativada
- **NX_PTR_ERROR** (0x07) Ponteiro do Agente SNMP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Use previously created “my_key” for SNMPv3 authentication.  */
status =  nx_snmp_agent_authenticate_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for setting the authentication parameters of SNMPv3 requests.  */
```

## <a name="nx_snmp_agent_community_get"></a>nx_snmp_agent_community_get
Recuperar o nome da comunidade

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_community_get(NX_SNMP_AGENT *agent_ptr, 
                                 UCHAR **community_string_ptr);
```

### <a name="description"></a>Descrição

Este serviço recupera o nome da comunidade a partir do mais recente pedido do SNMP recebido pelo Agente SNMP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **community_string_ptr** Ponteiro para um ponteiro de cordas para devolver a corda comunitária do Agente SNMP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) comunidade SNMP bem sucedida obter.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
UCHAR *string_ptr;

/* Pickup the community string pointer for my_agent.  */
status =  nx_snmp_agent_community_get(&my_agent, &string_ptr);


/* If status is NX_SUCCESS the pointer “string_ptr” points to the
   last community name supplied to the SNMP agent.  */
```

## <a name="nx_snmp_agent_request_get_type_test"></a>nx_snmp_agent_request_get_type_test
Indicar se o último pedido do SNMP é tipo GET ou SET

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

### <a name="description"></a>Descrição

Este serviço indica se o pedido mais recente do SNMP Manager é um tipo GET (GET, GETNEXT ou GETBULK) ou SET. Destina-se a ser utilizado com o nome de utilizador onde a aplicação SNMPv1 ou SNMPv2 irá querer comparar a cadeia comunitária recebida com a cadeia pública do Agente SNMP se o pedido for um tipo GET, ou ao cordão privado do Agente SNMP se o pedido for um tipo SET.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **is_get_type** Ponteiro para solicitar o estado do tipo:  
NX_TRUE se tipo GET  
NX_FALSE se definir o tipo

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Tipo devolvido com sucesso
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
UINT is_get_type;

/* Determine if the current SNMP request is a GET or SET type.  */
status =  nx_snmp_agent_request_get_type_test(&my_agent, &is_get_type);


/* If status is NX_SUCCESS, is_get_type will indicate the request type.  */
```

## <a name="nx_snmp_agent_context_engine_set"></a>nx_snmp_agent_context_engine_set
Motor de contexto definido (apenas SNMP v3)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_context_engine_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *context_engine, 
                                      UINT context_engine_size);
```
### <a name="description"></a>Descrição

Este serviço define o motor de contexto do Agente SNMP. Só é aplicável ao processamento do SNMPv3. Isto deve ser chamado antes de criar chaves de segurança se a aplicação estiver a usar autenticação e encriptação, uma vez que o ID do motor de contexto é usado no processo de criação chave. Caso contrário, o NetX Duo SNMP fornece um id de motor de contexto predefinido no topo da *nxd_snmp.c:*

```c
UCHAR _nx_snmp_default_context_engine[NX_SNMP_MAX_CONTEXT_STRING] =  
                {0x80, 0x00, 0x03, 0x10, 0x01, 0xc0, 0xa8, 0x64, 0xaf};

```

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **context_engine** Ponteiro para a corda do motor de contexto.
- **context_engine_size** Tamanho da corda do motor de contexto. Note que o número máximo de bytes num motor de contexto é definido por NX_SNMP_MAX_CONTEXT_STRING.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Conjunto de motores de contexto SNMP bem sucedido.
- **NX_NOT_ENABLED** (0x14) SNMPv3 não está ativado
- **NX_SNMP_ERROR** (0x100) Erro de tamanho do motor de contexto.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
UCHAR my_engine[] = {0x80, 0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07};

/* Set the context engine for my_agent.  */
status =  nx_snmp_agent_context_engine_set(&my_agent, my_engine, 9);


/* If status is NX_SUCCESS the context engine has been set.  */
```
## <a name="nx_snmp_agent_context_name_set"></a>nx_snmp_agent_context_name_set
Definir nome de contexto (apenas SNMP v3)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_context_name_set(NX_SNMP_AGENT *agent_ptr, 
                                    UCHAR *context_name, 
                                    UINT context_name_size);
```

### <a name="description"></a>Descrição

Este serviço define o nome de contexto do Agente SNMP. Só é aplicável ao processamento do SNMPv3. Se não for chamado, o Agente SNMP da NetX Duo deixará o nome de contexto em branco.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **context_name** Ponteiro para a cadeia de nome de contexto.
- **context_name_size** Tamanho da cadeia de nome de contexto. Note que o número máximo de bytes em um nome de contexto é definido por NX_SNMP_MAX_CONTEXT_STRING.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Conjunto de nomes de contexto SNMP bem sucedidos.
- **NX_SNMP_ERROR** (0x100) Erro de tamanho do nome do contexto.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Set the context name for my_agent.  */
status =  nx_snmp_agent_context_name_set(&my_agent, “my_context_name”, 15);


/* If status is NX_SUCCESS the context name has been set.  */
```

## <a name="nx_snmp_agent_create"></a>nx_snmp_agent_create
Criar agente SNMP

### <a name="prototype"></a>Prototype

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
### <a name="description"></a>Descrição

Este serviço cria um Agente SNMP na instância IP especificada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **snmp_agent_name** Ponteiro para a cadeia de nomes do agente SNMP.
- **ip_ptr** Ponteiro para a instância IP.
- **stack_ptr** Ponteiro para o ponteiro da pilha de fio do agente SNMP.
- **stack_size** Tamanho da pilha em bytes.
- **pool_ptr** Ponter a piscina de pacotes predefinidos para este Agente SNMP.
- **snmp_agent_username_process** Função ponteiro para a rotina de manuseamento do nome de utilizador da aplicação.
- **snmp_agent_get_process** Função ponteiro para a rotina de tratamento do pedido GET da aplicação.
- **snmp_agent_getnext_process** Função ponteiro para a rotina de tratamento do pedido GETNEXT da aplicação.
- **snmp_agent_set_process** Função ponteiro para a rotina de tratamento do pedido set da aplicação.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Agente SNMP bem sucedido criar.
- **NX_SNMP_ERROR** (0x100) O Agente SNMP cria erro.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
NX_SNMP_AGENT my_agent;

/* Create the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_create(&my_agent, "My SNMP Agent", &ip_0, stack_start_ptr,
                4096, &pool_0, my_username_processing, my_get_processing, 
                my_getnext_processing, my_set_processing);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been created.  */
```

## <a name="nx_snmp_agent_current_version_get"></a>nx_snmp_agent_current_version_get
Obtenha a versão do pacote SNMP

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_current_version_get(NX_SNMP_AGENT *agent_ptr, 
                                       UINT *version);
```

### <a name="description"></a>Descrição

Este serviço recupera a versão SNMP analisada a partir do mais recente pacote SNMP recebido.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **versão** Ponteiro para a versão SNMP analisada a partir do pacote SNMP recebido

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Versão SNMP bem sucedida obter
- **NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
UINT          snmp_version;
NX_SNMP_AGENT my_agent;

/* Get the version of the last received SNMP packet. */
status =  nx_snmp_agent_current_version_get (&my_agent, &snmp_version);


/* If status is NX_SUCCESS, snmp_version contains 
   the received packet SNMP version.  */
```

## <a name="nx_snmp_agent_private_string_test"></a>nx_snmp_agent_private_string_test
Verifique as combinações de cordas privadas Agente cadeia privada

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr, 
                                       UCHAR *community_string,          
                                       UINT *is_private);
```

### <a name="description"></a>Descrição

Este serviço compara a cadeia comunitária de entrada terminada com a cadeia privada do agente SNMP e indica se coincidem.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **community_string** Ponteiro para cadeia para comparar
- **is_private** Ponteiro para o resultado da comparação  
NX_TRUE - fósforos de cordas  
NX_FALSE - a corda não combina

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Comparação bem sucedida
- **NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

## <a name="nx_snmp_agent_public_string_test"></a>nx_snmp_agent_public_string_test
Verifique se a corda pública recebida corresponde à cadeia pública do agente

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string,          
                                      UINT *is_public);
```
### <a name="description"></a>Descrição

Este serviço compara uma cadeia comunitária de entrada terminada com a cadeia pública do agente SNMP e indica se correspondem.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **community_string** Ponteiro para cadeia para comparar
- **is_public** Ponteiro para o resultado da comparação  
NX_TRUE - fósforos de cordas  
NX_FALSE - a corda não combina

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Comparação bem sucedida
- **NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

## <a name="nx_snmp_agent_version_set"></a>nx_snmp_agent_version_set
Desaponte o estado do agente SNMP para cada versão SNMP

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_version_set(NX_SNMP_AGENT *agent_ptr, 
                               UINT enabled_v1, UINT enable_v2, 
                               UINT enable_v3);
```

### <a name="description"></a>Descrição

Este serviço define o estado (ativado/desativado) para cada uma das versões SNMP, V1, V2 e V3 no agente SNMP. Note que as opções configuráveis do utilizador, NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 e NX_SNMP_DISABLE_V3, irão anular estas definições de tempo de execução. Por predefinição, o agente SNMP está ativado para as três versões.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **enabled_v1** Define o estado ativado para o SNMP V1 para dentro/para fora.
- **enabled_v2** Define o estado ativado para o SNMP V2 para dentro/para fora.
- **enabled_v3** Define o estado ativado para o SNMP V3 para dentro/para fora.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Conjunto de versão SNMP bem-sucedida
- **NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

## <a name="nx_snmp_agent_private_string_set"></a>nx_snmp_agent_private_string_set
Desaponte a corda privada do agente SNMP

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_private_string_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string);
```

### <a name="description"></a>Descrição

Este serviço define a cadeia comunitária privada do agente SNMP com a corda terminada nulo de entrada. O valor predefinido é NU (nenhum conjunto de cordas privada), de modo que qualquer pacote SNMP recebido com uma cadeia comunitária "privada" não será aceite pelo agente SNMP para acesso de leitura/escrita. O fio de entrada deve ser inferior ou igual ao tamanho configurável do utilizador NX_SNMP_MAX_USER_NAME-1 (para permitir a interrupção do tamanho).

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **community_string** Ponteiro para a cadeia privada para atribuir

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) definir com sucesso a corda privada
- **NX_SNMP_ERROR_TOOBIG** (0x01) Tamanho da corda muito grande 
- **NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s private community string */
status =  nx_snmp_agent_private_string_set(&my_agent, “private”));


/* If status is NX_SUCCESS, the SNMP agent private string is set.  */
```

## <a name="nx_snmp_agent_public_string_set"></a>nx_snmp_agent_public_string_set
Definir a cadeia pública do agente SNMP

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_public_string_set(NX_SNMP_AGENT *agent_ptr, 
                                     UCHAR *community_string);
```

### <a name="description"></a>Descrição

Este serviço define a cadeia da comunidade pública do agente SNMP com a corda terminada nulo de entrada. O fio comunitário deve ser inferior ou igual ao tamanho configurável do utilizador NX_SNMP_MAX_USER_NAME-1 (para permitir espaço para rescisão nulo).

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **community_string** Ponteiro para a cadeia pública para atribuir

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) definir com sucesso a corda pública
- **NX_SNMP_ERROR_TOOBIG** (0x01) Tamanho da corda muito grande
- **NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s public string. */
nx_snmp_agent_public_string_set(&my_agent, “my_public”));


/* If status is NX_SUCCESS, the SNMP agent public string is set.  */
```

## <a name="nx_snmp_agent_delete"></a>nx_snmp_agent_delete
Eliminar agente SNMP

### <a name="prototype"></a>Prototype

```C
UINT nx_snmp_agent_delete(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>Descrição

Este serviço elimina um Agente SNMP previamente criado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Agente SNMP bem sucedido apagar.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Delete the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_delete(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been deleted.  */
```

## <a name="nx_snmp_agent_set_interface"></a>nx_snmp_agent_set_interface
Definir a interface de rede de agente SNMP

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_set_interface(NX_SNMP_AGENT *agent_ptr,  
                                 UINT if_index);
```

### <a name="description"></a>Descrição

Este serviço define a interface de rede SNMP para o Agente SNMP, conforme especificado pelo índice de interface de entrada. Isto só é útil para aplicações de anfitriões SNMP com NetX Duo 5.6 ou superior que suportam múltiplas interfaces de rede. O valor predefinido se não especificado pelo hospedeiro é zero, para a interface primária.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **If_index** Índice que especifica a interface SNMP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Conjunto de interface SNMP bem sucedido.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Set the SNMP Agent “my_agent” to the secondary interface.  */
if_index = 1;
status =  nx_snmp_agent_set_interface(&my_agent, if_index);


/* If status is NX_SUCCESS the SNMP agent interface is set.  */
```

## <a name="nx_snmp_agent_md5_key_create"></a>nx_snmp_agent_md5_key_create
Criar tecla md5 (apenas SNMP v3)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY 
                                       *destination_key);
```
### <a name="description"></a>Descrição

Este serviço cria uma chave MD5 que pode ser usada para autenticação e encriptação.

Este serviço é precotado. Os desenvolvedores são encorajados a migrar para *nx_snmp_agent_md5_key_create_extended()*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **senha** Ponteiro para a corda de senha.
- **destination_key** Ponteiro para estrutura de dados chave SNMP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Chave de sucesso criar.
- **NX_NOT_ENABLED** (0x14) Segurança não ativada.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS an MD5 key has been created.  */
```

## <a name="nx_snmp_agent_md5_key_create_extended"></a>nx_snmp_agent_md5_key_create_extended
Criar tecla md5 (apenas SNMP v3)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_md5_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY 
                                           *destination_key);
```
### <a name="description"></a>Descrição

Este serviço cria uma chave MD5 que pode ser usada para autenticação e encriptação.

Este serviço substitui *nx_snmp_agent_md5_key_create.* Esta versão requer que o chamador forneça o comprimento da palavra-passe.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **senha** Ponteiro para a corda de senha.
- **password_length** Comprimento da corda da palavra-passe.
- **destination_key** Ponteiro para estrutura de dados chave SNMP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Chave de sucesso criar.
- **NX_NOT_ENABLED** (0x14) Segurança não ativada.
- **NX_SNMP_FAILED** (0x102) O SNMP falhou.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_priv_trap_key_use"></a>nx_snmp_agent_priv_trap_key_use
Especifique a chave de encriptação para mensagens de armadilha

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```

### <a name="description"></a>Descrição

Este serviço especifica que uma chave de privacidade previamente criada deve ser usada para encriptação e desencriptação de mensagens de armadilha SNMPv3.

> [!NOTE]
> *Uma chave de autenticação deve ser previamente criada. A privacidade do SNMP v3 (encriptação) requer autenticação. Consulte nx_snmp_agent_auth_trap_key_use para mais detalhes.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **chave** Ponteiro para criar previamente a chave.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Conjunto de chaves de privacidade bem sucedida.
- **NX_NOT_ENABLED** (0x14) Segurança não ativada.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent” trap messages.   */
status =  nx_snmp_agent_priv_trap_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_privacy_key_use"></a>nx_snmp_agent_privacy_key_use
Especifique a chave de encriptação para mensagens de resposta

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr, 
                                   NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>Descrição

Este serviço especifica que a chave previamente criada deve ser usada para encriptação e desencriptação de mensagens de resposta SNMPv3.

> [!NOTE]
> *Uma chave de autenticação deve ter sido previamente especificada. A encriptação V3 do SNMP requer a criação de uma chave de autenticação também. Consulte nx_snmp_agent_authentiation_key_use para mais detalhes.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **chave** Ponteiro para criar previamente a chave.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Conjunto de chaves de privacidade bem sucedida.
- **NX_NOT_ENABLED** (0x14) Segurança não ativada.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_privacy_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_sha_key_create"></a>nx_snmp_agent_sha_key_create
Criar tecla SHA (apenas SNMP v3)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY  
                                  *destination_key);
```
### <a name="description"></a>Descrição

Este serviço cria uma chave SHA que pode ser usada para autenticação e encriptação.

Este serviço é precotado. Os desenvolvedores são encorajados a migrar para *nx_snmp_agent_sha_key_create_extended()*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **senha** Ponteiro para a corda de senha.
- **destination_key** Ponteiro para estrutura de dados chave SNMP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Chave de sucesso criar.
- **NX_SNMP_ERROR** (0x100) A chave cria erro.
- **NX_PTR_ERROR** (0x07) Agente SNMP inválido ou ponteiro chave.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_sha_key_create_extended"></a>nx_snmp_agent_sha_key_create_extended
Criar tecla SHA (apenas SNMP v3)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_sha_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY  
                                           *destination_key);
```
### <a name="description"></a>Descrição

Este serviço cria uma chave SHA que pode ser usada para autenticação e encriptação.

Este serviço substitui *nx_snmp_agent_sha_key_create.* Esta versão requer que o chamador forneça o comprimento da palavra-passe.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **senha** Ponteiro para a corda de senha.
- **password_length** Comprimento da corda da palavra-passe.
- **destination_key** Ponteiro para estrutura de dados chave SNMP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Chave de sucesso criar.
- **NX_SNMP_ERROR** (0x100) A chave cria erro.
- **NX_SNMP_FAILED** (0x102) A chave cria falhas.
- **NX_PTR_ERROR** (0x07) Agente SNMP inválido ou ponteiro chave.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_start"></a>nx_snmp_agent_start
Iniciar agente SNMP 

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_start(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>Descrição

Este serviço liga a tomada UDP à porta SNMP 161 e inicia a tarefa de thread do Agente SNMP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Início bem sucedido do Agente SNMP.
- **NX_SNMP_ERROR** (0x100) Erro de arranque do Agente SNMP.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Start the previously created SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_start(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been started.  */
```
## <a name="nx_snmp_agent_stop"></a>nx_snmp_agent_stop
Parar o agente SNMP 

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_stop(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>Descrição

Este serviço para a tarefa de thread do Agente SNMP e desvinga a tomada UDP para a porta SNMP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Paragem bem sucedida do Agente SNMP.
- **NX_PTR_ERROR** (0x07) Ponteiro do Agente SNMP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Stop the previously created and started SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_stop(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been stopped.  */
```
## <a name="nx_snmp_agent_trap_send"></a>nx_snmp_agent_trap_send
Enviar armadilha SNMPv1 *(apenas IPv4)*

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
                             ULONG ip_address, UCHAR *enterprise, 
                             UINT trap_type, UINT trap_code, 
                             ULONG elapsed_time, 
                             NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a>Descrição

Este serviço envia uma armadilha SNMP ao Gerente SNMP no endereço IPv4 especificado. O método preferido para o envio de uma armadilha SNMP na NetX Duo é utilizar o serviço *nxd_snmp_agent_trap_send.* *nx_snmp_agent_trap_send* está incluído no NetX Duo para suportar as aplicações existentes do Agente SNMP netX.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **ip_address** Endereço IPv4 do Gerente do SNMP.
- **empresa** Cadeia de ID de objeto da empresa (sysObectID).
- **trap_type** Tipo de armadilha solicitada:  
   - NX_SNMP_TRAP_COLDSTART (0)  
   - NX_SNMP_TRAP_WARMSTART (1)  
   - NX_SNMP_TRAP_LINKDOWN (2)  
   - NX_SNMP_TRAP_LINKUP (3)  
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)  
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)  

- **trap_code** Código de armadilha específico.
- **elapsed_time** O sistema de tempo foi para cima (sysUpTime).
- **object_list_ptr** Matriz de objetos e seus valores associados a incluir na armadilha SNMP. A lista está NX_NULL terminada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Envio de armadilhas SNMP bem sucedidas.
- **NX_SNMP_ERROR** (0x100) Erro de envio de armadilha SNMP.
- **NX_NOT_ENABLED** (0x14) SNMPv1 não está ativado.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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
## <a name="nxd_snmp_agent_trap_send"></a>nxd_snmp_agent_trap_send
Enviar armadilha SNMPv1 *(IPv4 e IPv6)*

### <a name="prototype"></a>Prototype

```c
UINT nxd_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *enterprise, UINT trap_type, 
            UINT trap_code, ULONG elapsed_time, 
            NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Descrição

Este serviço envia uma armadilha SNMP ao Gestor SNMP no endereço IP especificado. O método equivalente para o envio de uma armadilha SNMP na NetX é o serviço *nxd_snmp_agent_trap_send.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **ip_address** Endereço IPv4 ou IPv6 do Gestor do SNMP.
- **empresa** Cadeia de ID de objeto da empresa (sysObectID).
- **trap_type** Tipo de armadilha solicitada:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

- **trap_code** Código de armadilha específico.
- **elapsed_time** O sistema de tempo foi para cima (sysUpTime).
- **object_list_ptr** Matriz de objetos e seus valores associados a incluir na armadilha SNMP. A lista está NX_NULL terminada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Envio de armadilhas SNMP bem sucedidas.
- **NX_SNMP_ERROR** (0x100) Erro de envio de armadilha SNMP.
- **NX_NOT_ENABLED** (0x14) SNMPv1 não está ativado.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

## <a name="nx_snmp_agent_trapv2_send"></a>nx_snmp_agent_trapv2_send
Enviar armadilha SNMPv2 (apenas IPv4)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
            NXD_ADDRESS *ip_address, UCHAR *community, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Descrição

Este serviço envia uma armadilha SNMPv2 ao Gerente SNMP no endereço IPv4 especificado. O método preferido para o envio de uma armadilha SNMP na NetX Duo é utilizar o serviço *nxd_snmp_agent_trapv2_send.* *nx_snmp_agent_trapv2_send* está incluído no NetX Duo para suportar as aplicações existentes do Agente SNMP netX.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **ip_address** Endereço IPv4 do Gerente do SNMP.
- **comunidade** Nome comunitário (nome de utilizador).
- **trap_type**  
   Tipo de armadilha pedida. Os eventos padrão são:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   Para dados proprietários:  
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definido em *nxd_snmp.h)*
   
- **elapsed_time** O sistema de tempo foi para cima (sysUpTime).
- **object_list_ptr** Matriz de objetos e seus valores associados a incluir na armadilha SNMP. A lista está NX_NULL terminada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Envio de armadilhas SNMP bem sucedidas.
- **NX_SNMP_ERROR** (0x100) Erro de envio de armadilha SNMP.
- **NX_NOT_ENABLED** (0x14) SNMPv2 não está ativado.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

## <a name="nx_snmp_agent_trapv2_oid_send"></a>nx_snmp_agent_trapv2_oid_send
Enviar armadilha SNMPv2 especificando o OID diretamente 

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *community,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a>Descrição

Este serviço envia uma armadilha SNMPv2 para o Gestor SNMP no endereço IP especificado (apenas IPv4) e permite que o chamador especifique o OID diretamente. O método preferido para o envio de uma armadilha SNMP com OID especificado na NetX Duo é utilizar o serviço *nxd_snmp_agent_trapv2_oid_send.* *nx_snmp_agent_trapv2_oid_ envio* está incluído no NetX Duo para suportar as aplicações existentes do Agente SNMP netX.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **ip_address** Endereço IP do Gestor do SNMP.
- **comunidade** Nome comunitário (nome de utilizador).
- **oid** Ponteiro para tampão contendo OID.
- **elapsed_time** O sistema de tempo foi para cima (sysUpTime).
- **object_list_ptr** Matriz de objetos e seus valores associados a incluir na armadilha SNMP. A lista está NX_NULL terminada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Envio de armadilhas SNMP bem sucedidas.
- **NX_SNMP_ERROR** (0x100) Erro de envio de armadilha SNMP.
- **NX_PTR_ERROR** (0x16) Agente SNMP inválido ou ponteiro de parâmetros.
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IP de destino inválido.
- **NX_OPTION_ERROR** (0x0a) Parâmetro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

## <a name="nxd_snmp_agent_trapv2_send"></a>nxd_snmp_agent_trapv2_send
Enviar armadilha SNMPv2 (IPv4 e IPv6)

### <a name="prototype"></a>Prototype

```c
UINT nxd_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *community, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Descrição

Este serviço envia uma armadilha SNMP V2 para o Gestor SNMP no endereço IP especificado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **ip_address** Endereço IP (IPv4 ou IPv6) do Gestor do SNMP.
- **comunidade** Nome comunitário (nome de utilizador).
- **trap_type**  
   Tipo de armadilha pedida. Os eventos padrão são:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   Para dados proprietários:

   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definido em *nxd_snmp.h)*

- **elapsed_time** O sistema de tempo foi para cima (sysUpTime).
- **object_list_ptr** Matriz de objetos e seus valores associados a incluir na armadilha SNMP. A lista está NX_NULL terminada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Envio de armadilhas SNMP bem sucedidas.
- **NX_SNMP_ERROR** (0x100) Erro de envio de armadilha SNMP.
- **NX_NOT_ENABLED** (0x14) SNMPv2 não está ativado.
- **NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Versão IP não suportada
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

## <a name="nxd_snmp_agent_trapv2_oid_send"></a>nxd_snmp_agent_trapv2_oid_send
Enviar armadilha SNMPv2 especificando o OID diretamente 

### <a name="prototype"></a>Prototype

```c
UINT nxd_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *community,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                    *object_list_ptr);
```
### <a name="description"></a>Descrição

Este serviço envia uma armadilha de V2 SNMP para o Gestor SNMP no endereço IP especificado (IPv4/IPv6) e permite que o chamador especifique o OID diretamente.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **ip_address** Endereço IP do Gestor do SNMP (IPv4/IPv6).
- **comunidade** Nome comunitário (nome de utilizador).
- **oid** Ponteiro para tampão contendo OID.
- **elapsed_time** O sistema de tempo foi para cima (sysUpTime).
- **object_list_ptr** Matriz de objetos e seus valores associados a incluir na armadilha SNMP. A lista está NX_NULL terminada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Envio de armadilhas SNMP bem sucedidas.
- **NX_SNMP_ERROR** (0x100) Erro de envio de armadilha SNMP.
- **NX_PTR_ERROR** (0x16) Agente SNMP inválido ou ponteiro de parâmetros.
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IP de destino inválido.
- **NX_OPTION_ERROR** (0x0a) Parâmetro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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
## <a name="nx_snmp_agent_trapv3_send"></a>nx_snmp_agent_trapv3_send
Enviar armadilha SNMPv3 (apenas IPv4)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *username, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a>Descrição

Este serviço envia uma armadilha SNMPv3 para o Gerente SNMP no endereço IPv4 especificado. O método preferido para o envio de uma armadilha SNMP na NetX Duo é utilizar o serviço *nxd_snmp_agent_trapv3_send.* *nx_snmp_agent_trapv3_send* está incluído no NetX Duo para suportar as aplicações existentes do Agente SNMP netX.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **ip_address** Endereço IPv4 do Gerente do SNMP.
- **nome de utilizador** Nome comunitário (nome de utilizador).
- **trap_type**  
   Tipo de armadilha pedida. Os eventos padrão são:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   Para dados proprietários:
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definido em *nxd_snmp.h)*

- **elapsed_time** O sistema de tempo foi para cima (sysUpTime).
- **object_list_ptr** Matriz de objetos e seus valores associados a incluir na armadilha SNMP. A lista está NX_NULL terminada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Envio de armadilhas SNMP bem sucedidas.
- **NX_SNMP_ERROR** (0x100) Erro de envio de armadilha SNMP.
- **NX_NOT_ENABLED** (0x14) SNMPv3 não está ativado.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

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

## <a name="nx_snmp_agent_trapv3_oid_send"></a>nx_snmp_agent_trapv3_oid_send
Enviar armadilha SNMPv3 especificando o OID diretamente 

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *username,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                   *object_list_ptr);
```
### <a name="description"></a>Descrição

Este serviço envia uma armadilha SNMPv3 para o Gestor SNMP no endereço IP especificado (apenas IPv4) e permite que o chamador especifique o OID diretamente. O método preferido para o envio de uma armadilha SNMP com OID especificado na NetX Duo é utilizar o serviço *nxd_snmp_agent_trapv3_oid_send.* *nx_snmp_agent_trapv3_oid_ envio* está incluído no NetX Duo para suportar as aplicações existentes do Agente SNMP netX.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **ip_address** Endereço IP do Gestor do SNMP.
- **nome de utilizador** Nome comunitário (nome de utilizador).
- **oid** Ponteiro para tampão contendo OID.
- **elapsed_time** O sistema de tempo foi para cima (sysUpTime).
- **object_list_ptr** Matriz de objetos e seus valores associados a incluir na armadilha SNMP. A lista está NX_NULL terminada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Envio de armadilhas SNMP bem sucedidas.
- **NX_SNMP_ERROR** (0x100) Erro de envio de armadilha SNMP.
- **NX_PTR_ERROR** (0x16) Agente SNMP inválido ou ponteiro de parâmetros.
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IP de destino inválido.
- **NX_OPTION_ERROR** (0x0a) Parâmetro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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
## <a name="nxd_snmp_agent_trapv3_send"></a>nxd_snmp_agent_trapv3_send
Enviar armadilha SNMPv3 (IPv4 e IPv6)

### <a name="prototype"></a>Prototype

```c
UINT nxd_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *username, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Descrição

Este serviço envia uma armadilha SNMP ao Gestor SNMP no endereço IP especificado. Esta armadilha é basicamente a mesma que a armadilha V2 do SNMP, exceto que o formato de mensagem de armadilha está contido no PDU SNMP v3.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **ip_address** Endereço IP (IPv4 ou IPv6) do Gestor do SNMP.
- **nome de utilizador** Nome comunitário (nome de utilizador).
- **trap_type**  
   Tipo de armadilha pedida. Os eventos padrão são:
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)  
   Para dados proprietários:
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definido em *nxd_snmp.h)*

- **elapsed_time** O sistema de tempo foi para cima (sysUpTime).
- **object_list_ptr** Matriz de objetos e seus valores associados a incluir na armadilha SNMP. A lista está NX_NULL terminada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Envio de armadilhas SNMP bem sucedidas.
- **NX_SNMP_ERROR** (0x100) Erro de envio de armadilha SNMP.
- **NX_NOT_ENABLED** (0x14) SNMPv3 não está ativado.
- **NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Versão IP não suportada
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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

## <a name="nxd_snmp_agent_trapv3_oid_send"></a>nxd_snmp_agent_trapv3_oid_send
Enviar armadilha SNMPv3 especificando o OID diretamente 

### <a name="prototype"></a>Prototype

```c
UINT nxd_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *username,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a>Descrição

Este serviço envia uma armadilha SNMPv3 para o Gestor SNMP no endereço IP especificado (IPv4/IPv6) e permite que o chamador especifique o OID diretamente.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para o bloco de controlo do agente SNMP.
- **ip_address** Ponteiro para endereço IP do Gerente SNMP.
- **nome de utilizador** Nome de utilizador (nome comunitário).
- **oid** Ponteiro para tampão contendo OID.
- **elapsed_time** O sistema de tempo foi para cima (sysUpTime).
- **object_list_ptr** Matriz de objetos e seus valores associados a incluir na armadilha SNMP. A lista está NX_NULL terminada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Envio de armadilhas SNMP bem sucedidas.
- **NX_SNMP_ERROR** (0x100) Erro de envio de armadilha SNMP.
- **NX_PTR_ERROR** (0x16) Agente SNMP inválido ou ponteiro de parâmetros.
- **NX_IP_ADDRESS_ERROR** (0x21) Endereço IP de destino inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

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
## <a name="nx_snmp_agent_v3_context_boots_set"></a>nx_snmp_agent_v3_context_boots_set
Definir o número de reinicializações (se o SNMPv3 estiver ativado)

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_agent_v3_context_boots_set(NX_SNMP_AGENT *agent_ptr, 
                                        UINT boots);
```

### <a name="description"></a>Descrição

Este serviço define o número de reinicializações registadas pelo agente SNMP. Este serviço só está disponível se o SNMPv3 estiver habilitado para o agente SNMP, uma vez que a contagem de botas só é utilizada no protocolo SNMPv3.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **agent_ptr** Ponteiro para bloco de controlo do agente SNMP
- **botas** O valor para definir a contagem de botas do Agente SNMP para

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) definir com sucesso a contagem de botas
- **NX_SNMP_ERROR** (0x100) Contagem de botas de definição de erro
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
UINT my_boots = 4;

if (my_agent.nx_snmp_agent_v3_enabled == NX_TRUE)
{
   status = nx_snmp_agent_v3_context_boots_set(&my_agent, my_boots);
}


/* If status is NX_SUCCESS the SNMP boot count is set.  */
```

## <a name="nx_snmp_object_compare"></a>nx_snmp_object_compare
Comparar dois objetos 

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_object_compare(UCHAR *object, UCHAR *reference_object);
```

### <a name="description"></a>Descrição

Este serviço compara o ID do objeto fornecido com o ID do objeto de referência. Ambos os IDs de objeto estão na notação ASCII SMI, por exemplo, ambos os objetos devem começar com a cadeia ASCII "1.3.6".

Este serviço é precotado. Os desenvolvedores são encorajados a migrar para *nx_snmp_object_compare_extended().*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **objeto** Ponteiro para opor identificação.
- **reference_object** Ponteiro para o ID do objeto de referência.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O objeto corresponde ao objeto de referência.
- **NX_SNMP_NEXT_ENTRY** (0x101) O objeto é inferior ao objeto de referência.
- **NX_SNMP_ERROR** (0x100) O objeto é maior do que o objeto de referência.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare(requested_object, "1.3.6.1.2.1.1.1.0");

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_compare_extended"></a>nx_snmp_object_compare_extended
Comparar dois objetos 

### <a name="prototype"></a>Prototype

```c
UINT nx_snmp_object_compare_extended(UCHAR *request_object, 
                                     UINT requested_object_length,
                                     UCHAR *reference_object
                                     UINT reference_object_length);
```
### <a name="description"></a>Descrição

Este serviço compara o ID do objeto fornecido com o ID do objeto de referência. Ambos os IDs de objeto estão na notação ASCII SMI, por exemplo, ambos os objetos devem começar com a cadeia ASCII "1.3.6".

Este serviço substitui *nx_snmp_object_compare.* Esta versão requer que os chamadores forneçam informações de comprimento.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **request_object** Ponteiro para solicitar identificação do objeto.
- **request_object_length** Comprimento da identificação do objeto de pedido.
- **reference_object** Ponteiro para o ID do objeto de referência.
- **reference_object_length** Comprimento do ID do objeto de referência.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O objeto corresponde ao objeto de referência.
- **NX_SNMP_NEXT_ENTRY** (0x101) O objeto é inferior ao objeto de referência.
- **NX_SNMP_ERROR** (0x100) O objeto é maior do que o objeto de referência.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

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

## <a name="nx_snmp_object_copy"></a>nx_snmp_object_copy
Copiar um objeto 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_copy(UCHAR *source_object_name, 
                          UCHAR *destination_object_name);
```
### <a name="description"></a>Descrição

Este serviço copia o objeto de origem na notação ASCII SIM para o objeto de destino.

Este serviço é precotado. Os desenvolvedores são encorajados a migrar para *nx_snmp_object_copy_extended().*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **source_object_name** Ponteiro para identificação do objeto de origem.
- **destination_object_name** Ponteiro para o endereço de destino objeto ID.

### <a name="return-values"></a>Valores de devolução

- **tamanho** Número de bytes copiados para o nome de destino. Se erro, zero é devolvido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, my_new_object);

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_copy_extended"></a>nx_snmp_object_copy_extended
Copiar um objeto 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_copy_extended(UCHAR *source_object_name, 
                             UINT source_object_name_length,
                             UCHAR *destination_object_name_buffer,
                             UINT destination_object_name_buffer_size);
```

### <a name="description"></a>Descrição

Este serviço copia o objeto de origem na notação ASCII SIM para o objeto de destino.

Este serviço substitui *nx_snmp_object_copy.* Esta versão requer que os chamadores forneçam informações de comprimento.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **source_object_name** Ponteiro para identificação do objeto de origem.
- **source_object_name_length** Comprimento da identificação do objeto de origem.
- **destination_object_name_buffer** Ponteiro para o tampão do objeto de destino.
- **destination_object_name_buffer_size** Tamanho do tampão de objeto de destino.

### <a name="return-values"></a>Valores de devolução

- **tamanho** Número de bytes copiados para o nome de destino. Se erro, zero é devolvido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
UCHAR   my_object = "1.3.6.1.2.1.1.1.0";
UCHAR   my_new_object[32];


/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, 17, my_new_object, sizeof(my_new_object));

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_counter_get"></a>nx_snmp_object_counter_get
Obtenha objeto de contador 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_counter_get(VOID *source_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a>Descrição

Este serviço recupera o objeto de contador no endereço especificado pelo ponteiro de origem e coloca-o na estrutura de dados do objeto NetX. Esta rotina é normalmente chamada da rotina de chamada de aplicação GET ou GETNEXT.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **source_ptr** Ponteiro para contra-fonte.
- **object_data** Ponteiro para a estrutura do objeto de destino.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O objeto de contador foi recuperado com sucesso.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Get the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object.  */
status =  nx_snmp_object_counter_get(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter_set"></a>nx_snmp_object_counter_set
Definir objeto de contador 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_counter_set(VOID *destination_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descrição

Este serviço define o contador no endereço especificado pelo ponteiro de destino com o valor de contador na estrutura de dados do objeto NetX. Esta rotina é normalmente chamada da rotina de chamada de aplicação SET.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **destination_ptr** Ponteiro para o destino de balcão.
- **object_data** Ponteiro para contra-fonte estrutura de objeto.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O objeto de contador foi definido com sucesso.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto inválido.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Set the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object with
   the counter object value contained in my_object.  */
status =  nx_snmp_object_counter_set(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   set. */
```

## <a name="nx_snmp_object_counter64_get"></a>nx_snmp_object_counter64_get
Obtenha objeto de contador de 64 bits 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_counter64_get(VOID *source_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descrição

Este serviço recupera o objeto de contador de 64 bits no endereço especificado pelo ponteiro de origem e coloca-o na estrutura de dados do objeto NetX. Esta rotina é normalmente chamada da rotina de chamada de aplicação GET ou GETNEXT.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **source_ptr** Ponteiro para contra-fonte.
- **object_data** Ponteiro para a estrutura do objeto de destino.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O objeto de contador foi recuperado com sucesso.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Get the value of my_64_bit_counter and place it into my_object
   for return.  */
status =  nx_snmp_object_counter64_get(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter64_set"></a>nx_snmp_object_counter64_set
Definir objeto de contador de 64 bits 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_counter64_set(VOID *destination_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a>Descrição

Este serviço define o contador de 64 bits no endereço especificado pelo ponteiro de destino com o valor de contador na estrutura de dados do objeto NetX. Esta rotina é normalmente chamada da rotina de chamada de aplicação SET.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **destination_ptr** Ponteiro para o destino de balcão.
- **object_data** Ponteiro para contra-fonte estrutura de objeto.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O objeto de contador foi definido com sucesso.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto inválido.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Set the value of my_64_bit_counter with the value in my_object.  */
status =  nx_snmp_object_counter64_set(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   set. */
```

## <a name="nx_snmp_object_end_of_mib"></a>nx_snmp_object_end_of_mib
Definir valor final de mib 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_end_of_mib(VOID *not_used_ptr, 
                              NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descrição

Este serviço cria um objeto que assinala o fim do MIB e é normalmente chamado da rotina de chamada de aplicação GET ou GETNEXT.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **not_used_ptr** Ponteiro não utilizado – deve ser NX_NULL.
- **object_data** Ponteiro para a estrutura do objeto de destino.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O objeto de fim de mib foi construído com sucesso.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Place an end-of-mib value in my_object.  */
status =  nx_snmp_object_end_of_mib(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now an end-of-mib object. */
```

## <a name="nx_snmp_object_gauge_get"></a>nx_snmp_object_gauge_get
Obtenha objeto de bitola 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_gauge_get(VOID *source_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descrição

Este serviço recupera o objeto de bitola no endereço especificado pelo ponteiro de origem e coloca-o na estrutura de dados do objeto NetX. Esta rotina é normalmente chamada da rotina de chamada de aplicação GET ou GETNEXT.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **source_ptr** Ponteiro para medir a fonte.
- **object_data** Ponteiro para a estrutura do objeto de destino.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O objeto de bitola foi recuperado com sucesso.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Get the value of ifSpeed (1.3.6.1.2.1.2.2.1.5.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_gauge_get(&ifSpeed, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ifSpeed gauge value. */
```

## <a name="nx_snmp_object_gauge_set"></a>nx_snmp_object_gauge_set
Conjunto de objeto de bitola 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_gauge_set(VOID *destination_ptr,
                                     NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descrição

Este serviço define o bitola no endereço especificado pelo ponteiro de destino com o valor de bitola na estrutura de dados do objeto NetX. Esta rotina é normalmente chamada da rotina de chamada de aplicação SET.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **destination_ptr** Ponteiro para medir o destino.
- **object_data** Ponteiro para medir a estrutura do objeto de origem.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O objeto de bitola foi definido com sucesso.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto inválido.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Set the value of “my_gauge” from the gauge value in my_object.  */
status =  nx_snmp_object_gauge_set(&my_gauge, my_object);

/* If status is NX_SUCCESS, the my_gauge now contains the new gauge value. */
```

## <a name="nx_snmp_object_id_get"></a>nx_snmp_object_id_get
Obter objeto id 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_id_get(VOID *source_ptr, 
                            NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descrição

Este serviço recupera o ID do objeto (na notação SIM ASCII) no endereço especificado pelo ponteiro de origem e coloca-o na estrutura de dados do objeto NetX. Esta rotina é normalmente chamada da rotina de chamada de aplicação GET ou GETNEXT.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **source_ptr** Ponteiro para opor fonte de identificação.
- **object_data** Ponteiro para a estrutura do objeto de destino.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O ID do objeto foi recuperado com sucesso.
- **NX_SNMP_ERROR** (0x100) Comprimento inválido do objeto
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Get the value of sysObjectID(1.3.6.1.2.1.1.2.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_id_get(&sysObjectID, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysObjectID value. */
```

## <a name="nx_snmp_object_id_set"></a>nx_snmp_object_id_set
Definir id objeto 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_id_set(VOID *destination_ptr, 
                             NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descrição

Este serviço define o ID do objeto (na notação SIM ASCII) no endereço especificado pelo ponteiro de destino com o ID do objeto na estrutura de dados do objeto NetX. Esta rotina é normalmente chamada da rotina de chamada de aplicação SET.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **destination_ptr** Ponteiro para opor destino de identificação.
- **object_data** Ponteiro para estrutura de objetos.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O ID do objeto foi definido com sucesso.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto inválido.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Set the string “my_object_id” with the object ID value contained 
   in my_object.  */
status =  nx_snmp_object_id_set(my_object_id, my_object);

/* If status is NX_SUCCESS, the my_object_id now contains the object ID value. */
```

## <a name="nx_snmp_object_integer_get"></a>nx_snmp_object_integer_get
Obter objeto inteiro 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_integer_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descrição

Este serviço recupera o objeto inteiro no endereço especificado pelo ponteiro de origem e coloca-o na estrutura de dados do objeto NetX. Esta rotina é normalmente chamada da rotina de chamada de aplicação GET ou GETNEXT.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **source_ptr** Ponteiro para fonte inteiro.
- **object_data** Ponteiro para a estrutura do objeto de destino.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O objeto inteiro foi recuperado com sucesso.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Get the value of sysServices (1.3.6.1.2.1.1.7.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_integer_get(&sysServices, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysServices value. */
```

## <a name="nx_snmp_object_integer_set"></a>nx_snmp_object_integer_set
Definir objeto inteiro 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_integer_set(VOID *destination_ptr,
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descrição

Este serviço define o número inteiro no endereço especificado pelo ponteiro de destino com o valor inteiro na estrutura de dados do objeto NetX. Esta rotina é normalmente chamada da rotina de chamada de aplicação SET.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **destination_ptr** Ponteiro para o destino inteiro.
- **object_data** Ponteiro para a estrutura de objetos de origem inteiro.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O objeto inteiro foi definido com sucesso.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto inválido.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Set the value of ifAdminStatus from the integer value in my_object.  */
status =  nx_snmp_object_integer_set(&ifAdminStatus, my_object);

/* If status is NX_SUCCESS, ifAdnminStatus now contains the new integer value. */
```

## <a name="nx_snmp_object_ip_address_get"></a>nx_snmp_object_ip_address_get
Obtenha objeto de endereço IP (apenas IPv4)

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_ip_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descrição

Este serviço recupera o objeto de endereço IP no endereço especificado pelo ponteiro de origem e coloca-o na estrutura de dados do objeto NetX. Esta rotina é normalmente chamada da rotina de chamada de aplicação GET ou GETNEXT.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **source_ptr** Ponteiro para fonte de endereço IPv4.
- **object_data** Ponteiro para a estrutura do objeto de destino.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O objeto de endereço IP foi recuperado com sucesso.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ip_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ipv6_address_get"></a>nx_snmp_object_ipv6_address_get
Obtenha objeto de endereço IP (apenas IPv6)

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_ipv6_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA 
                                      *object_data);
```

### <a name="description"></a>Descrição

Este serviço recupera o objeto de endereço IPv6 no endereço especificado pelo ponteiro de origem e coloca-o na estrutura de dados do objeto NetX.
Esta rotina é normalmente chamada da rotina de chamada de aplicação GET ou GETNEXT.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **source_ptr** Ponteiro para a fonte de endereço IPv6.
- **object_data** Ponteiro para a estrutura do objeto de destino.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O objeto de endereço IP foi recuperado com sucesso.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Código de objeto SNMP de entrada incorreta
- **IPv6** NX_NOT_ENABLED (0x14) não habilitado
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ipv6_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ip_address_set"></a>nx_snmp_object_ip_address_set
Definir objeto de endereço IPv4 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_ip_address_set(VOID *destination_ptr, 
                                    NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descrição

Este serviço define o endereço IPv4 no endereço especificado pelo ponteiro de destino com o endereço IP na estrutura de dados do objeto NetX. Esta rotina é normalmente chamada da rotina de chamada de aplicação SET.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **destination_ptr** Ponteiro para endereço IP para definir.
- **object_data** Ponteiro para a estrutura do objeto do endereço IP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O objeto de endereço IP foi definido com sucesso.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto inválido.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ip_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_ipv6_address_set"></a>nx_snmp_object_ipv6_address_set
Definir objeto de endereço IPv6 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_ipv6_address_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA  
                                      *object_data);
```

### <a name="description"></a>Descrição

Este serviço define o endereço IPv6 no endereço especificado pelo ponteiro de destino com o endereço IP na estrutura de dados do objeto NetX. Esta rotina é normalmente chamada da rotina de chamada de aplicação SET.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **destination_ptr** Ponteiro para endereço IP para definir.
- **object_data** Ponteiro para a estrutura do objeto do endereço IP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O endereço IPv6 foi definido com sucesso.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto inválido.
- **IPv6** NX_NOT_ENABLED (0x14) não habilitado
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ipv6_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_no_instance"></a>nx_snmp_object_no_instance
Definir objeto sem instância 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_no_instance(VOID *not_used_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descrição

Este serviço cria um objeto sinalizando que não havia nenhuma instância do objeto especificado e é tipicamente chamado a partir da rotina de chamada de aplicação GET ou GETNEXT.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **not_used_ptr** Ponteiro não utilizado – deve ser NX_NULL.
- **object_data** Ponteiro para a estrutura do objeto de destino.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O objeto sem exemplo foi construído com sucesso.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Place no-instance value in my_object.  */
status =  nx_snmp_object_no_instance(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a no-instance object. */
```

## <a name="nx_snmp_object_not_found"></a>nx_snmp_object_not_found
Definir objeto não encontrado 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_not_found(VOID *not_used_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descrição

Este serviço cria um objeto que sinaliza que o objeto não foi encontrado e é normalmente chamado da rotina de chamada de aplicação GET ou GETNEXT.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **not_used_ptr** Ponteiro não utilizado – deve ser NX_NULL.
- **object_data** Ponteiro para a estrutura do objeto de destino.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O objeto não encontrado foi construído com sucesso.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Place not-found value in my_object.  */
status =  nx_snmp_object_not_found(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a not-found object. */
```

## <a name="nx_snmp_object_octet_string_get"></a>nx_snmp_object_octet_string_get
Obtenha objeto de corda de octeto 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_octet_string_get(VOID *source_ptr,
                                            NX_SNMP_OBJECT_DATA *object_data, 
                                      UINT length);
```
### <a name="description"></a>Descrição

Este serviço recupera a cadeia de octeto no endereço especificado pelo ponteiro de origem e coloca-o na estrutura de dados do objeto NetX. Esta rotina é normalmente chamada da rotina de chamada de aplicação GET ou GETNEXT.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **source_ptr** Ponteiro para fonte de cadeia de octeto.
- **object_data** Ponteiro para a estrutura do objeto de destino.
- **comprimento** Número de bytes na corda de octeto.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O objeto de corda de octeto foi recuperado com sucesso.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Get the value of the 6-byte ifPhysAddress (1.3.6.1.2.1.2.2.1.6.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_octet_string_get(ifPhysAddress, my_object, 6);

/* If status is NX_SUCCESS, the my_object now contains the ifPhysAddress value. */
```

## <a name="nx_snmp_object_octet_string_set"></a>nx_snmp_object_octet_string_set
Definir objeto de corda de octeto 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_octet_string_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descrição

Este serviço define a cadeia de octeto no endereço especificado pelo ponteiro de destino com a cadeia de octeto na estrutura de dados do objeto NetX. Esta rotina é normalmente chamada da rotina de chamada de aplicação SET.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **destination_ptr** Ponteiro para destino de cadeia de octeto.
- **object_data** Ponteiro para estrutura de objeto de fonte de cadeia de octeto.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O objeto de corda de octeto foi definido com sucesso.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto inválido.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   octet string in my_object.  */
status =  nx_snmp_object_octet_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new octet string. */
```

## <a name="nx_snmp_object_string_get"></a>nx_snmp_object_string_get
Obtenha objeto de corda ASCII 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_string_get(VOID *source_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descrição

Este serviço recupera a cadeia ASCII no endereço especificado pelo ponteiro de origem e coloca-a na estrutura de dados do objeto NetX. Esta rotina é normalmente chamada da rotina de chamada de aplicação GET ou GETNEXT.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **source_ptr** Ponteiro para fonte de cadeia ASCII.
- **object_data** Ponteiro para a estrutura do objeto de destino.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O objeto de corda ASCII foi recuperado com sucesso.
- **NX_SNMP_ERROR** (0x100) String é muito grande  
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Get the value of the sysDescr (1.3.6.1.2.1.1.1.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_string_get(sysDescr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysDescr string. */
```

## <a name="nx_snmp_object_string_set"></a>nx_snmp_object_string_set
Definir objeto de corda ASCII 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_string_set(VOID *destination_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descrição

Este serviço define a cadeia ASCII no endereço especificado pelo ponteiro de destino com a cadeia ASCII na estrutura de dados do objeto NetX. Esta rotina é normalmente chamada da rotina de chamada de aplicação SET.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **destination_ptr** Ponteiro para destino de cordas ASCII.
- **object_data** Ponteiro para a estrutura do objeto de fonte de cadeia ASCII.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O objeto de corda ASCII foi definido com sucesso.
- **NX_SNMP_ERROR** (0x100) Corda demasiado grande.
- **NX_SNMP_ERROR_BADVALUE** (0x03) Personagem inválido na corda
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto inválido.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   ASCII string in my_object.  */
status =  nx_snmp_object_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new ASCII string. */
```

## <a name="nx_snmp_object_timetics_get"></a>nx_snmp_object_timetics_get
Obter objeto timetics 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_timetics_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descrição

Este serviço recupera os relógios no endereço especificado pelo ponteiro de origem e coloca-o na estrutura de dados do objeto NetX. Esta rotina é normalmente chamada da rotina de chamada de aplicação GET ou GETNEXT.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **source_ptr** Ponteiro para fonte de timetics.
- **object_data** Ponteiro para a estrutura do objeto de destino.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O objeto de tempotético foi recuperado com sucesso.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Get the value of the sysUpTime (1.3.6.1.2.1.1.3.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_timetics_get(sysUpTime, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysUpTime value. */
```

## <a name="nx_snmp_object_timetics_set"></a>nx_snmp_object_timetics_set
Objeto de timetics definido 

### <a name="prototype"></a>Prototype

```c
UINT  nx_snmp_object_timetics_set(VOID *destination_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descrição

Este serviço define a variável timetics no endereço especificado pelo ponteiro de destino com os timetics na estrutura de dados do objeto NetX.
Esta rotina é normalmente chamada da rotina de chamada de aplicação SET.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **destination_ptr** Ponteiro para destino timetics.
- **object_data** Ponteiro para a estrutura do objeto de origem timetics.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O objeto de cronometros foi definido com sucesso.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto inválido.
- **NX_PTR_ERROR** (0x07) Ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Set the value of “my_time” from the timetics value in my_object.  */
status =  nx_snmp_object_timetics_set(&my_time, my_object);

/* If status is NX_SUCCESS, my_time now contains the new timetics. */
```