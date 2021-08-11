---
title: Capítulo 4 - Descrição dos serviços NAT
description: Este capítulo contém uma descrição de todos os serviços da API DA NETX Duo NAT por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: dbe2cb25607162b62b048251927bdc7671c5884d2a3b45b6b24bae539e08d24a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797300"
---
# <a name="chapter-4---description-of-nat-services"></a>Capítulo 4 - Descrição dos serviços NAT

Este capítulo contém uma descrição de todos os serviços da API DA NETX Duo NAT (listados abaixo) por ordem alfabética.

> [!NOTE]
> Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

## <a name="nx_nat_create"></a>nx_nat_create

Criar um servidor NAT

### <a name="prototype"></a>Prototype

```C
UINT nx_nat_create(NX_NAT_DEVICE *nat_ptr, NX_IP *ip_ptr,
    UINT global_interface_index,
    VOID *dynamic_cache_memory,
    UINT dynamic_cache_size);
```

### <a name="description"></a>Description

Este serviço cria uma instância do servidor NAT.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **nat_ptr** Ponteiro para a instância NAT para criar
- **ip_ptr Pointer** para a instância IP
- **global_interface_index** Índice para a interface global de rede
- **dynamic_cache_memory** Área de memória do ponteiro para a tabela NAT
- **dynamic_cache_size** Tamanho da área de memória para tabela NAT

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) servidor NAT criado com sucesso
- NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido
- NX_NAT_PARAM_ERROR (0xD01) Entrada inválida sem ponteiro
- NX_NAT_CACHE_ERROR (0xD02) Entrada inválida do ponteiro do cache

### <a name="allowed-from"></a>Permitido a partir de

Código de aplicação

### <a name="example"></a>Exemplo

```C
#define NX_NAT_ENTRY_CACHE_SIZE 20480

static UCHAR nat_cache[NX_NAT_ENTRY_CACHE_SIZE];
UINT global_interface_index = 0;

/* Create a NAT Server and cache with a global interface index. */
status = nx_nat_create(nat_ptr, ip_ptr, global_interface_index,
    nat_cache, NX_NAT_ENTRY_CACHE_SIZE);

/* If status = NX_SUCCESS, the NAT instance was successfully
    created. */
```

## <a name="nx_nat_delete"></a>nx_nat_delete

Excluir um servidor NAT

### <a name="prototype"></a>Prototype

```C
UINT nx_nat_delete(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a>Description

Este serviço elimina um SERVIDOR NAT previamente criado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **nat_ptr** Ponteiro para a instância NAT para eliminar

### <a name="return-values"></a>Valores de devolução

- **NAT NX_SUCCESS** (0x00) eliminado com sucesso
- NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Código de aplicação

### <a name="example"></a>Exemplo

```C
/* Delete the NAT instance. */
status = nx_nat_delete (nat_ptr);

/* If the NAT instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_nat_enable"></a>nx_nat_enable

Ativar a instância IP para NAT

### <a name="prototype"></a>Prototype

```C
UINT nx_nat_enable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a>Description

Este serviço permite a instância IP para NAT (por exemplo, pacotes recebidos para o servidor NAT).

### <a name="input-parameters"></a>Parâmetros de Entrada

- **nat_ptr** Ponteiro para a instância NAT

### <a name="return-values"></a>Valores de devolução

- **NAT NX_SUCCESS** (0x00) habilitado com sucesso
- NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Código de aplicação

### <a name="example"></a>Exemplo

```C
/* Enable the NAT server. */
status = nx_nat_enable (nat_ptr);

/* If status = NX_SUCCESS, the IP instance was successfully enabled for NAT. */
```

## <a name="nx_nat_disable"></a>nx_nat_disable

Desative a instância IP para NAT

### <a name="prototype"></a>Prototype

```C
UINT nx_nat_disable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a>Description

Este serviço desativa o NAT na instância IP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **nat_ptr** Ponteiro para a instância NAT

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) NAT com sucesso desativado
- NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Código de aplicação

### <a name="example"></a>Exemplo

```C
/* Disable the NAT server. */
status = nx_nat_disable (nat_ptr);

/* If status = NX_SUCCESS the NAT operation successfully disable. */
```

## <a name="nx_nat_cache_notify_set"></a>nx_nat_cache_notify_set

Desa um cache completa notifique a função de retorno de chamada

### <a name="prototype"></a>Prototype

```C
UINT nx_nat_cache_notify_set(NX_NAT_DEVICE *nat_ptr,
    VOID (*cache_full_notify_cb)
    (NX_NAT_DEVICE *nat_ptr)));
```

### <a name="description"></a>Description

Este serviço regista a chamada completa da cache com o ponteiro da função de entrada cache_full_notify_cb que aponta para uma função de notificação completa de cache definida pelo utilizador.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **nat_ptr** Ponteiro para a instância NAT
- **cache_full_notify_cb** Ponteiro para cache função de notificação completa

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Cache funciona completamente definida com sucesso
- NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido
- NX_NAT_PARAM_ERROR (0xD01) Entrada inválida sem ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Código de aplicação

### <a name="example"></a>Exemplo

```C
/* Set the cache full notify callback function to the NAT instance. */
status = nx_nat_cache_notify_set(nat_ptr, cache_full_notify_cb);

/* If status = NX_SUCCESS the callback function was successfully set. */
```

## <a name="nx_nat_inbound_entry_create"></a>nx_nat_inbound_entry_create

Criar uma entrada de entrada na tabela de tradução NAT

### <a name="prototype"></a>Prototype

```C
UINT nx_nat_inbound_entry_create(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *entry_ptr
    ULONG local_ip_address,
    USHORT external_port,
    USHORT local_port, UCHAR protocol);
```

### <a name="description"></a>Description

Este serviço cria uma entrada de entrada como estática (entrada permanente, nunca expira) e adiciona-a à tabela de tradução NAT. Estas entradas são geralmente criadas para servidores anfitriões locais onde uma ligação é iniciada a partir de um anfitrião na rede externa. O servidor NAT verifica se a porta externa ainda não está a ser utilizada na tabela de tradução ou vinculada por uma tomada NetX Duo anteriormente existente do mesmo protocolo.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **nat_ptr** Ponteiro para a instância NAT
- **entry_ptr** Ponteiro para a entrada de tradução
- **local_ip_address** Endereço IP do anfitrião local
- **external_port** Porta de destino na rede externa
- **local_port** Porto de origem (anfitrião local)
- **protocolo** Protocolo do pacote (por exemplo, TCP)

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Entrada criada com sucesso
- **porta** externa NX_NAT_PORT_UNAVAILABLE (0xD0D) Inválida
- NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido
- NX_NAT_PARAM_ERROR (0xD01) Entrada inválida sem ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Código de aplicação

### <a name="example"></a>Exemplo

```C
/* Create an entry for an inbound TCP packet. */
status = nx_nat_inbound_entry_create(nat_ptr, entry_ptr,
    IP_ADDRESS(192,168,2,2), 5001, 5001,
    NX_PROTOCOL_TCP);

/* If status = NX_SUCCESS the entry was successfully created. */
```

## <a name="nx_nat_inbound_entry_delete"></a>nx_nat_inbound_entry_delete

Eliminar uma entrada de entrada na tabela de tradução NAT

### <a name="prototype"></a>Prototype

```C
UINT nx_nat_inbound_entry_delete(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *delete_entry_ptr)
```

### <a name="description"></a>Description

Este serviço elimina a entrada especificada da tabela de tradução.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **nat_ptr** Ponteiro para a instância NAT
- **delete_entry_ptr** Ponteiro para a entrada de tradução NAT

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Entrada eliminada com sucesso
- **NX_NAT_ENTRY_NOT_FOUND** (0xD04) A entrada não é encontrada
- NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido
- NX_NAT_ENTRY_TYPE_ERROR (0xD0C) Tipo de tradução inválida

### <a name="allowed-from"></a>Permitido a partir de

Código de aplicação

### <a name="example"></a>Exemplo

```C
/* Delete the specified static entry from the translation table. */
status = nx_nat_inbound_entry_delete(nat_ptr, delete_entry_ptr);

/* If status = NX_SUCCESS the entry was successfully deleted. */
```
