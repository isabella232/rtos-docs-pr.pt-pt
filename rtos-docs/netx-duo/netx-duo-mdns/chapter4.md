---
title: Capítulo 4 - Descrição dos serviços mDNS
description: Este capítulo contém uma descrição de todos os serviços netX mDNS
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6e37698ac6023b4cff6cb4fc05330a73b678ef3d2a813a706c9b821381e123db
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797573"
---
# <a name="chapter-4---description-of-mdns-services"></a>Capítulo 4 - Descrição dos serviços mDNS

Este capítulo contém uma descrição de todos os serviços netX mDNS (listados abaixo).

> [!NOTE]
> Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

## <a name="nx_mdns_create"></a>nx_mdns_create

Criar uma instância mDNS

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_create(NX_MDNS *mdns_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool,
    UINT priority, VOID *stack_ptr,
    UINT stack_size, UCHAR *host_name,
    VOID *local_service_cache,
    UINT local_service_cache_size,
    VOID *peer_service_cache,
    UINT peer_service_cache_size,
    VOID (*probing_notify)(NX_MDNS *mdns_ptr,
        UCHAR *name, UINT probing_state));
```

### <a name="description"></a>Description

Este serviço cria uma instância mDNS sobre a instância IP específica e recursos associados. Um fio também é criado para lidar com mensagens mDNS recebidas, para responder a consultas e para transmitir periodicamente mensagens de consulta.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **mdns_ptr** Ponteiro para o bloco de controlo mDNS.
- **ip_ptr** Ponteiro para a instância IP associada.
- **packet_pool** Ponteiro para uma piscina de pacotes válido.
- **prioridade** Prioridade da linha mDNS.
- **stack_ptr** Ponteiro para a área da pilha para o fio mDNS
- **stack_size** Tamanho da área da pilha.
- **host_name** Nome de anfitrião atribuído a este nó.
- **local_service_cache** Armazenamento espaço para serviços registados locais.
- **local_service_cache_size** Tamanho da cache de serviço local.
- **peer_service_cache** Armazenamento espaço para informação de serviço recebida
- **peer_service_cache_size** Tamanho da cache de serviço de pares
- **probing_notify** Função de retorno opcional invocada no final da operação de sondagem. Notifica a aplicação se o nome de anfitrião (ao ativar o mDNS numa interface local), ou o nome de serviço (após registar um serviço) é único.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) criou com sucesso a instância mDNS.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
UCHAR stack_ptr[2048];
UCHAR local_cache_ptr[2048];
UCHAR peer_cache_ptr[8192];

/* Create a mDNS instance. */
status = nx_mdns_create(&my_mdns, &ip_0, &pool_0,
    3, stack_ptr, 2048,
    “NETX-MDNS-HOST”,
    local_cache_ptr, 2048,
    peer_cache_ptr, 8192,
    probing_notify);

/* If status is NX_SUCCESS, mDNS instance was created. */
```

## <a name="nx_mdns_delete"></a>nx_mdns_delete

Eliminar uma instância mDNS

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_delete(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Description

Este serviço elimina a instância mDNS e liberta os seus recursos.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **mdns_ptr** Ponteiro para o bloco de controlo mDNS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) eliminou com sucesso a instância mDNS.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Delete a previously created mDNS instance. */

status = nx_mdns_delete(&my_mdns);

/* If status is NX_SUCCESS, the mDNS instance has been deleted. */
```

## <a name="nx_mdns_enable"></a>nx_mdns_enable

Inicie o serviço mDNS

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_enable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a>Description

Esta API permite o serviço mDNS em interface física específica. Uma vez que o serviço está ativado, o módulo mDNS sonda primeiro todos os seus nomes de serviço únicos na rede antes de responder às consultas recebidas na interface.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **mdns_ptr** Ponteiro para o bloco de controlo de instância mDNS.
- **interface_index** Índice para a interface onde o serviço deve ser ativado

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) ativou com sucesso o serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Enable mDNS service on specific interface. */

status = nx_mdns_enable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was enabled. */
```

## <a name="nx_mdns_disable"></a>nx_mdns_disable

Desativar o serviço mDNS

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_disable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a>Description

Esta API desativa o serviço mDNS na interface física específica. Uma vez desativado o serviço, o mDNS envia mensagens de "adeus" para cada serviço local para a rede que está ligada à interface, para que os nós vizinhos sejam notificados.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **mdns_ptr** Ponteiro para o bloco de controlo mDNS.
- **interface_index** Índice para a interface onde o serviço deve ser desativado

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) desativou com sucesso o serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Disable mDNS service on specific interface. */

status = nx_mdns_disable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was disabled. */
```

## <a name="nx_mdns_cache_notify_set"></a>nx_mdns_cache_notify_set

Instala a função de notificação completa da cache mDNS

### <a name="prototype"></a>Prototype

```c
UINT nx_mdns_cache_notify_set(NX_MDNS *mdns_ptr,
    VOID (*cache_full_notify_cb)(NX_MDNS *mdns_ptr,
        UINT state, UINT cache_type));
```

### <a name="description"></a>Description

Este serviço instala uma função de retorno fornecida pelo utilizador, que é invocada quando a cache de serviço local ou a cache de serviço de pares ficam cheias. Quando a cache de serviço estiver cheia, não pode ser adicionado mais mDNS Resource Record. Note que a cache de serviço pode ficar cheia em resultado de fragmentação interna, quando os serviços com vários comprimentos de corda são adicionados e removidos. Ao receber uma notificação completa de cache na cache de serviço de pares, a aplicação pode usar o serviço "*nx_mdns_service_cache_clear"* para apagar todas as entradas na cache de serviço de pares.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **mdns_ptr** Ponteiro para o bloco de controlo mDNS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Instalou com sucesso a cache mDNS notificando a função de retorno.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Set mDNS cache notify callback. */

status = nx_mdns_cache_notify_set(&my_mdns, cache_full_nofiy_cb);

/* If status is NX_SUCCESS, mDNS cache notify callback was set. */
```

## <a name="nx_mdns_cache_notify_clear"></a>nx_mdns_cache_notify_clear

Limpe a cache de serviço mDNS na função de notificação completa

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_cache_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Description

Este serviço limpa uma cache de serviço fornecida pelo utilizador para notificar a função de retorno de chamada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **mdns_ptr** Ponteiro para o bloco de controlo mDNS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) limpou com sucesso a cache de serviço mDNS notificando a função de retorno de chamada.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Clear mDNS cache notify callback. */

status = nx_mdns_cache_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, mDNS cache notify callback clear. */
```

## <a name="nx_mdns_domain_name_set"></a>nx_mdns_domain_name_set

Define o nome de domínio

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_domain_name_set(NX_MDNS *mdns_ptr, CHAR *domain_name);
```

### <a name="description"></a>Description

Este serviço configura o nome de domínio local padrão. Quando a instância mDNS é criada, o nome de domínio local predefinido é definido como ".local". Esta API permite que uma aplicação substitua o nome de domínio local predefinido.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **mdns_ptr** Ponteiro para o bloco de controlo mDNS.
- **domain_name** O nome de domínio a ser usado.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) configuraram com sucesso o domínio local.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Set the domain name. */

status = nx_mdns_domain_name_set(&my_mdns, “home”);

/* If status is NX_SUCCESS, the “home” domain name was set. */
```

## <a name="nx_mdns_service_announcement_timing_set"></a>nx_mdns_service_announcement_timing_set

Define os parâmetros de tempo para mensagens de anúncio de serviço

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_announcement_timing_set(NX_MDNS *mdns_ptr,
    UINT t, UINT p, UINT k, UINT retrans_interval,
    UINT period_interval, UINT max_time);
```

### <a name="description"></a>Description

Este serviço reconfigura os parâmetros de tempo utilizados pelo mDNS ao enviar os anúncios de serviço. O período de publicação começa a partir de *t* ticks e pode ser expandido telescopicamente com 2 para o poder do fator *k.* O número de repetições por anúncio é *p,* o intervalo entre cada anúncio repetido é de tiques *de intervalo,* e o número de período de anúncio é max_time. Por predefinição, o período inicial é definido para 1 segundo, com k = 1 (o período duplica cada vez), *p = 1* (sem repetição), retrans_interval = 0 (sem intervalo de tempo), period_interval = 0xFFFFFFFF (intervalo do período máximo) e max_time = 3 (número de publicidade).

### <a name="input-parameters"></a>Parâmetros de Entrada

- **mdns_ptr** Ponteiro para o bloco de controlo mDNS.
- **t** Número de carraças para o período inicial. O padrão é de 100 carrapatos por 1 segundo.
- **p** Número de repetições. O valor predefinido é 1.
- **k** Fator telescópico. O valor predefinido é 1.
- **retrans_interval** Número de carraças para esperar antes de enviar mensagens de anúncio repetidas. O valor predefinido é 0.
- **period_interval** Número de tiques entre dois períodos de anúncio. O valor predefinido é 0xFFFFFFFF.
- **max_time** Número de período de anúncio a utilizar para o anúncio. Após os *períodos de anúncio max_time,* não são enviadas mais mensagens de anúncio. O valor predefinido é 3.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) define com sucesso os valores de tempo.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Set the service announcement timing. */

status = nx_mdns_service_announcement_timing_set(&my_mdns, 100,
    1, 1, 0, 0xFFFFFFFF, 3);

/* If status is NX_SUCCESS, the service announcement timing was set. */
```

## <a name="nx_mdns_service_add"></a>nx_mdns_service_add

Adicione um serviço local

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_add(NX_MDNS *mdns_ptr, CHAR *instance,
    CHAR *service, CHAR *subtype, UINT ttl, USHORT priority,
    USHORT weight, USHORT port, UCHAR *text, UCHAR is_unique,
    UINT interface_index);
```

### <a name="description"></a>Description

Esta API regista um serviço oferecido pela aplicação. Se a *bandeira is_unique* estiver definida, o mDNS sonda o nome de serviço para se certificar de que é único na rede local antes de começar a anunciar o serviço na rede. *Exemplo* é a parte do caso do nome de serviço. O *serviço* é a parte de serviço do nome de serviço. Por exemplo, "_http._tcp" é um serviço. Para descrever um serviço com subtipo, o chamador deve utilizar o parâmetro do *subtipo.* Por exemplo, se o serviço pretendido for "_printer._sub._http._tcp", o campo de serviço é "_http._tcp:, e o campo de subtipo é "_printer".

### <a name="input-parameters"></a>Parâmetros de Entrada

- **mdns_ptr** Ponteiro para o bloco de controlo mDNS.
- **exemplo** Ponteiro para o nome do serviço.
- **serviço** Ponteiro para o tipo de serviço mDNS, excluindo informações de subtipo.
- **subtipo** Ponteiro para a parte do subtipo do serviço mDNS, se aplicável.
- **prioridade** Prioridade de serviço
- **peso** Peso de serviço
- **porto** Número de porta TCP ou UDP que o serviço utiliza
- **texto** Informações adicionais de texto
- **is_unique** Bandeira booleana indicando se o serviço é partilhado ou único. Para serviços registados como únicos, o mDNS deve sondar o serviço na rede antes de começar a oferecê-lo.
- **Interface_index** Interface física o serviço é oferecido através. Para um serviço que é oferecido através de qualquer um dos serviços anexos, o valor *NX_MDNS_ALL_INTERFACES* é utilizado.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) registou com sucesso o serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Add local service. */

status = nx_mdns_service_add(&my_mdns, “NETX-SERVICE”,
    “_http._tcp”, NX_NULL,
    NX_NULL, 0, 0, 0, 80, NX_TRUE, 0);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was added. */
```

## <a name="nx_mdns_service_delete"></a>nx_mdns_service_delete

Remover um serviço registado anterior

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_delete(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype);
```

### <a name="description"></a>Description

Esta API elimina um serviço registado anterior. À medida que o serviço é apagado, as mensagens de "adeus" são enviadas para a rede local para que os nós vizinhos sejam notificados.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **mdns_ptr** Ponteiro para o bloco de controlo mDNS.
- **exemplo** Ponteiro para o nome do serviço.
- **serviço** Ponteiro para o tipo de serviço mDNS, excluindo informações de subtipo.
- **subtipo** Ponteiro para a parte do subtipo do serviço mDNS, se aplicável.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) apagou com sucesso o serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Delete local service. */

status = nx_mdns_service_delete(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was deleted. */
```

## <a name="nx_mdns_service_one_shot_query"></a>nx_mdns_service_one_shot_query

Iniciar a descoberta de serviço de um tiro

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_one_shot_query(NX_MDNS *mdns_ptr,
    UCHAR *instance,
    UCHAR *service,
    UCHAR *subtype,
    NX_MDNS_SERVICE *service_ptr, ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço executa uma consulta mDNS de uma só vez. Se o serviço especificado for encontrado na cache de serviço por pares, a primeira instância é devolvida. Se não forem encontrados serviços na cache de serviço de pares local, o módulo mDNS emite um comando de consulta e aguarda a resposta. O serviço está bloqueado até que a primeira resposta seja recebida ou os tempos de consulta esgotados.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **mdns_ptr** Ponteiro para o bloco de controlo mDNS.
- **exemplo** Ponteiro para o nome da instância do serviço, se aplicável.
- **serviço** Ponteiro para o tipo de serviço mDNS, excluindo informações de subtipo. o pedido deve especificar o tipo de serviço.
- **subtipo** Ponteiro para a parte do subtipo do serviço mDNS, se aplicável.
- **service_ptr** O utilizador forneceu o ponteiro para NX_MDNS_SERVICE estrutura que armazena os resultados da consulta.
- **wait_option** A quantidade de tempo, em carraças, para esperar por uma resposta.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) obteve com sucesso informações de serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Start service one shot query. */

status = nx_mdns_service_one_shot_query(&my_mdns, “NETX-SERVICE”, “_http._tcp”,
    NX_NULL, service_ptr, 500);

/* If status is NX_SUCCESS, The query with
    name: NetX-SERVICE._http._tcp.local,
     type: ANY (SRV and TXT) was sent.
    And the answer was stored in service_ptr if success. */
```

## <a name="nx_mdns_service_continuous_query"></a>nx_mdns_service_continuous_query

Iniciar descoberta de serviço contínuo

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_continous_query(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a>Description

Este serviço inicia uma consulta contínua. Note que o serviço regressa imediatamente. Após a emissão de uma consulta contínua, a aplicação pode recuperar o registo de serviço utilizando o *nx_mdns_service_lookup* da API . Para parar a consulta contínua, a aplicação pode utilizar a API *nx_mdns_service_query_stop*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **mdns_ptr** Ponteiro para o bloco de controlo mDNS.
- **exemplo** Ponteiro para o nome da instância do serviço, se aplicável.
- **serviço** Ponteiro para o tipo de serviço mDNS, excluindo informações de subtipo, se aplicável.
- **subtipo** Ponteiro para a parte do subtipo do serviço mDNS, se aplicável.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Começou com sucesso a consulta.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Start service continuous query. */

status = nx_mdns_service_continuous_query(&my_mdns,
    “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was added.
    And the query will be periodically sent. */
```

## <a name="nx_mdns_service_query_stop"></a>nx_mdns_service_query_stop

Cessar uma descoberta de serviço contínuo previamente emitida

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_query_stop(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a>Description

Esta API encerra uma descoberta de serviço contínuo emitida anteriormente.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **mdns_ptr** Ponteiro para o bloco de controlo mDNS.
- **exemplo** Ponteiro para o nome do serviço.
- **serviço** Ponteiro para o tipo de serviço mDNS, informações de subtipo.
- **subtipo** Ponteiro para a parte do subtipo do serviço mDNS, se aplicável.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) parou com sucesso continua a consulta.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Stop service continuous query. */

status = nx_mdns_service_query_stop(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was stopped. */
```

## <a name="nx_mdns_service_lookup"></a>nx_mdns_service_lookup

Recupera o serviço a partir da cache de serviço de pares local

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_lookup(NXD_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype, UINT instance_index,
    NXD_MDNS_SERVICE *service_ptr);
```

### <a name="description"></a>Description

Este serviço procura serviços que correspondam ao nome da instância (se fornecido) e ao tipo de serviço na cache de serviço de pares local. A aplicação iniciará a procura de serviço com *instance_index* definido para zero para o primeiro serviço na cache que corresponda à descrição. A aplicação continuará a utilizar este serviço com um valor *instance_index* crescente para serviços adicionais encontrados na cache, até que o serviço *NX_NO_MORE_ENTRIES,* o que indica o fim da cache.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **mdns_ptr** Ponteiro para o bloco de controlo mDNS.
- **exemplo** Ponteiro para o nome da instância do serviço, se aplicável.
- **serviço** Ponteiro para o tipo de serviço mDNS, excluindo informações de subtipo, se aplicável.
- **subtipo** Ponteiro para a parte do subtipo do serviço mDNS, se aplicável.
- **Instance_index** Número de índice para o caso a ser devolvido.
- **service_ptr** O utilizador forneceu o ponteiro para NX_MDNS_SERVICE estrutura que armazena os resultados da pesquisa.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) recuperou com sucesso o serviço
- **NX_NO_MORE_ENTRIES** (0x17) Não se encontra nenhuma entrada de serviço no número de índice especificado. Este código de erro indica o fim da pesquisa.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Lookup the service on specific index. */

status = nx_mdns_service_lookup(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL,
    0, service_ptr);

/* If status is NX_SUCCESS, The service with
    name: NetX-SERVICE._http._tcp.local, was retrieved. */
```

## <a name="nx_mdns_service_ignore_set"></a>nx_mdns_service_ignore_set

Configura um conjunto de ignoram o serviço

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_ignore_set(NX_MDNS *mdns_ptr, ULONG service_mask);
```

### <a name="description"></a>Description

Esta API configura uma máscara para ignorar os serviços especificados pela *service_mask* bitmask. O utilizador pode utilizar opcionalmente o service_mask para selecionar tipos de serviço que não deseja estar em cache. Uma lista de serviços é definida na *tabela nx_mdns_service_types* em *nxd_mdns.c.* A máscara correspondente do primeiro tipo de serviço em nx_mdns_service_types[] é 0x00000001, a máscara do segundo tipo de serviço é 0x00000002, e assim por diante.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **mdns_ptr** Ponteiro para o bloco de controlo mDNS.
- **service_mask** Tipos de serviço definidos pelo utilizador para ignorar. A máscara é do tipo ULONG de 32 bits. Cada bit representa uma entrada no conjunto *de nx_mdns_service_types* definido pelo utilizador. Se um pouco estiver definido, o tipo de serviço correspondente especificado no *nx_mdns_service_type* matriz não será armazenado na cache de serviço de pares.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) define com sucesso a máscara de ignorar o serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Set the service mask to ignore the specified service. */

status = nx_mdns_service_ignore_set(&my_mdns, 0x00000003);

/* If status is NX_SUCCESS, The service with
    type “_device-info” and “_http” will be ignored. */
```

## <a name="nx_mdns_service_notify_set"></a>nx_mdns_service_notify_set

Configura uma alteração de serviço notifica a função de retorno

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_notify_set(NX_MDNS *mdns_ptr, ULONG service_mask,
    VOID (*service_change_notify)(NX_MDNS *mdns_ptr,
    NX_MDNS_SERVICE *service_ptr, UINT state));
```

### <a name="description"></a>Description

Esta API configura uma alteração de serviço notificando a função de retorno. Esta função de retorno é invocada quando um serviço oferecido por outros nós na rede é adicionado, alterado ou já não está disponível. O utilizador pode utilizar opcionalmente o service_mask para selecionar os tipos de serviço que pretende monitorizar. Uma lista de serviços que estão a ser monitorizados está codificada na *tabela nx_mdns_service_types* em *nxd_mdns.c.*

A máscara correspondente do primeiro tipo de serviço em nx_mdns_service_types[] é 0x00000001, a máscara do segundo tipo de serviço é 0x00000002, e assim por diante.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **mdns_ptr** Ponteiro para o bloco de controlo mDNS.
- **service_mask** Tipos de serviço definidos pelo utilizador para monitorizar. A máscara é do tipo ULONG de 32 bits. Cada bit representa uma entrada na matriz *nx_mdns_service_types.*
- **service_change_notify** A função de retorno a invocar quando o serviço especificado for alterado. A informação detalhada do serviço é devolvida na memória apontada por *service_ptr.* Note que o conteúdo na memória é inválido após o regresso da função de chamada de notificação.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) instalou com sucesso a função de retorno.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Set the service mask to notify the specified service. */

status = nx_mdns_service_notify_set(&my_mdns, 0x00000002, service_change_notify);

/* If status is NX_SUCCESS, the callback will be called
    if received the service with type “_http”. */
```

## <a name="nx_mdns_service_notify_clear"></a>nx_mdns_service_notify_clear

Limpar a alteração de serviço notificar a função de retorno

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Description

Esta API limpa a alteração de serviço notificando a função de retorno e a .

### <a name="input-parameters"></a>Parâmetros de Entrada

- **mdns_ptr** Ponteiro para o bloco de controlo mDNS..

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) limpou com sucesso a função de retorno.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Clear the service notify. */

status = nx_mdns_service_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, the service notify function clear. */
```

## <a name="nx_mdns_host_address_get"></a>nx_mdns_host_address_get

Obtenha o endereço de anfitrião

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_host_address_get(NX_MDNS *mdns_ptr,
    UCHAR *host_name, ULONG *ipv4_address,
    ULONG *ipv6_address, ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço realiza uma consulta mDNS nos endereços IPv4 e IPv6 do anfitrião. Se o endereço do nome de anfitrião especificado for encontrado na cache de serviço de pares, o endereço é devolvido. Se não for encontrado nenhum endereço na cache de serviço de pares, o módulo mDNS emite consultas de tipo A e AAAA e aguarda a resposta. Esta API bloqueia até que uma resposta seja recebida ou os tempos de consulta saem.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **mdns_ptr** Ponteiro para o bloco de controlo mDNS.
- **host_name** Ponteiro para o nome de anfitrião.
- **ipv4_address** Ponteiro para um endereço alinhado de 4 byte para o espaço de armazenamento de endereços IPv4. O utilizador atribuirá 4 bytes de espaço para o endereço IPv4. NX_NULL endereço pode ser transmitido para esta API se a aplicação não precisar de recuperar o endereço IPv4.
- **ipv6_address** Ponteiro para o endereço alinhado de 4 byte para o espaço de armazenamento de endereços IPv6. O utilizador atribuirá 16 bytes de espaço para o endereço - IPv6. NX_NULL endereço pode ser transmitido para esta API se a aplicação não precisar de recuperar o endereço IPv6.
- **wait_option** A quantidade de tempo, em carraças, para esperar por uma resposta.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) obteve com sucesso o endereço de anfitrião.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
ULONG ipv4_address;
ULONG ipv6_address[4];

/* Get the IP address of specified host. */
status = nx_mdns_host_address_get(&my_mdns, “MDNS-Host”, &ipv4_address, ipv6_address, 500);

/* If status is NX_SUCCESS, the IP address of specified host was retrieved. */
```

## <a name="nx_mdns_local_cache_clear"></a>nx_mdns_local_cache_clear

Apagar todos os serviços locais

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_local_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Description

Este serviço limpa todas as entradas na cache de serviço local após o envio da mensagem de Adeus.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **mdns_ptr** Ponteiro para o bloco de controlo mDNS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) apagou com sucesso todas as entradas na cache.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Clear the local cache, delete all local service. */

status = nx_mdns_local_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of local cache were deleted. */
```

## <a name="nx_mdns_peer_cache_clear"></a>nx_mdns_peer_cache_clear

Apagar todos os serviços descobertos

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_peer_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Description

Este serviço limpa todas as entradas na cache de serviço de pares.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **mdns_ptr** Ponteiro para o bloco de controlo mDNS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) apagou com sucesso todas as entradas na cache.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Clear the peer cache, delete all peer service. */

status = nx_mdns_peer_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of peer cache were deleted. */
```
