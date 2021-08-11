---
title: Capítulo 3 - Descrição dos Serviços de Clientes Azure RTOS NetX Duo PTP
description: Este capítulo contém uma descrição de todos os serviços de clientes NetX Duo PTP por ordem alfabética.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 686db68181e3712f9f6a09a9f471626eff610fd7f45ec5b83ba56f8b7aa378cc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798015"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-ptp-client-services"></a>Capítulo 3 - Descrição dos Serviços de Clientes Azure RTOS NetX Duo PTP

Este capítulo contém uma descrição de todos os serviços de clientes NetX Duo PTP (listados abaixo) por ordem alfabética.

[!NOTE]
> *Na secção **Valores de Retorno** nas seguintes descrições da função API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.*

## <a name="nx_ptp_client_create"></a>nx_ptp_client_create

Criar uma instância de cliente PTP.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_create(
    NX_PTP_CLIENT *client_ptr, NX_IP *ip_ptr, 
    UINT interface_index,
    NX_PACKET_POOL *packet_pool_ptr, 
    UINT thread_priority, 
    UCHAR *thread_stack, 
    UINT stack_size,
    NX_PTP_CLIENT_CLOCK_CALLBACK clock_callback, 
    VOID *clock_callback_data);
```

### <a name="description"></a>Description

Este serviço cria uma instância do cliente PTP.

Note que a aplicação deve primeiro criar uma instância IP e um pacote de piscina para o cliente PTP transmitir pacotes. Para o conjunto de pacotes, a aplicação pode utilizar o mesmo pacote de piscina na instância IP; ou pode criar uma piscina de pacotes dedicada para cliente PTP.  A abordagem dedicada à piscina de pacotes tem a vantagem de usar pequenos pacotes (128 bytes pacotes se o IPv6 for usado, ou 108 bytes apenas para IPv4).

### <a name="input-parameters"></a>Parâmetros de Entrada
* **client_ptr** Ponteiro para cliente PTP para criar
* **ip_ptr** Indicação para a instância IP
* **interface_index** Índice de interface de rede PTP
* **packet_pool_ptr** Ponteiro para piscina de pacotes de clientes
* **thread_priority**  Prioridade do fio PTP
* **thread_stack** Ponteiro para pilha de rosca
* **stack_size** Tamanho da pilha de fio
* **clock_callback** Chamada do relógio PTP
* **clock_callback_data** Dados para a chamada do relógio

### <a name="return-values"></a>Valores de devolução
* **NX_SUCCESS** (0x00) Cliente criado com sucesso
* **NX_PTP_CLIENT_INSUFFICIENT_PACKET_PAYLOAD** (0xD04) Carga de pacote muito pequena
* **falha NX_PTP_CLIENT_CLOCK_CALLBACK_FAILURE** (0xD05) na chamada do relógio
* **estado** Conclusão do estado das chamadas de serviço NetX Duo e ThreadX
* NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido
* interface NX_INVALID_INTERFACE (0x4C) Inválida

### <a name="allowed-from"></a>Permitido a partir de
Fios

### <a name="example"></a>Exemplo
```C
/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_delete"></a>nx_ptp_client_delete

Elimina uma instância de cliente PTP.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_delete(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a>Description

Este serviço elimina uma instância do cliente PTP.

### <a name="input-parameters"></a>Parâmetros de Entrada
* **client_ptr** Ponteiro para cliente PTP para apagar

### <a name="return-values"></a>Valores de devolução
* **NX_SUCCESS** (0x00) Cliente eliminado com sucesso
* NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de
Fios

### <a name="example"></a>Exemplo
```C
/* Delete the PTP client instance */
status = nx_ptp_client_delete(&ptp_client);

/* If the client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_master_info_get"></a>nx_ptp_client_master_info_get

Obtenha informações do relógio principal.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_master_info_get(
    NX_PTP_CLIENT_MASTER *master_ptr, 
    NXD_ADDRESS *address, 
    UCHAR **port_identity, 
    UINT *port_identity_length, 
    UCHAR *priority1, 
    UCHAR *priority2, 
    UCHAR *clock_class, UCHAR *clock_accuracy, 
    USHORT *clock_variance, 
    UCHAR **grandmaster_identity,
    UINT *grandmaster_identity_length, 
    USHORT *steps_removed, 
    UCHAR *time_source);
```

### <a name="description"></a>Description
Este serviço obtém informações do relógio principal. O bloco de controlo principal é passado para a aplicação do utilizador através da função de retorno do evento.

### <a name="input-parameters"></a>Parâmetros de Entrada
* **master_ptr** Ponteiro para o relógio master PTP
* **endereço** Endereço do relógio principal
* **port_identity** PtP master porto e identidade
* **port_identity_length** Comprimento da porta-mestre ptp e identidade
* **prioridade1** Prioridade1 do relógio master PTP
* **prioridade2** Prioridade2 do relógio master PTP
* **clock_class** Classe de relógio master PTP
* **clock_accuracy** Precisão do relógio master PTP
* **clock_variance** Variação do relógio mestre PTP
* **grandmaster_identity** Identidade do relógio grandmaster
* **grandmaster_identity_length** Comprimento da identidade do grão-mestre
* **steps_removed** Passos removidos do cabeçalho PTP
* **time_source** A fonte do temporizador usado pelo relógio grandmaster

### <a name="return-values"></a>Valores de devolução
* **NX_SUCCESS** (0x00) Obtenha informações do relógio principal com sucesso
* NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de
Fios

### <a name="example"></a>Exemplo
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
NXD_ADDRESS address;
UCHAR *port_identity;
UINT port_identity_length;
UCHAR priority1, priority2;
UCHAR clock_class, clock_accuracy;
USHORT clock_variance;
UCHAR *grandmaster_identity;
UINT grandmaster_identity_length;
USHORT steps_removed;
UCHAR time_source;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_MASTER:
        {
            status = nx_ptp_client_master_info_get((NX_PTP_CLIENT_MASTER *)event_data, 
                                                   &address, &port_identity,
                                                   &port_identity_length, &priority1, 
                                                   &priority2, &clock_class,
                                                   &clock_accuracy, &clock_variance, 
                                                   &grandmaster_identity,
                                                   &grandmaster_identity_length, 
                                                   &steps_removed, &time_source);

            /* If the master clock information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_packet_timestamp_notify"></a>nx_ptp_client_packet_timestamp_notify

Notifique o cliente PTP da hora do pacote.

### <a name="prototype"></a>Prototype

```C
VOID nx_ptp_client_packet_timestamp_notify(
    NX_PTP_CLIENT *client_ptr, 
    NX_PACKET *packet_ptr, 
    NX_PTP_TIME *timestamp_ptr);
```

### <a name="description"></a>Description
Este serviço notifica o cliente PTP de que o pacote é transmitido com a hora de jogo. Este serviço foi concebido para o controlador de rede e invocado quando o pacote é transmitido. A estamp de tempo é geralmente gerada por hardware.

### <a name="input-parameters"></a>Parâmetros de Entrada
* **client_ptr** Ponteiro para cliente PTP para criar
* **packet_ptr** Ponteiro para pacote PTP que é transmitido
* **timestamp_ptr** Ponteiro para o tempotamp do pacote PTP

### <a name="return-values"></a>Valores de devolução
Nenhuma

### <a name="allowed-from"></a>Permitido a partir de
Fios

### <a name="example"></a>Exemplo
```C
/* Call notification callback */
nx_ptp_client_packet_timestamp_notify(client_ptr, packet_ptr, &ts);
```

## <a name="nx_ptp_client_soft_clock_callback"></a>nx_ptp_client_soft_clock_callback

Implementação de software de um relógio PTP.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_soft_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```

### <a name="description"></a>Description
Esta função de retorno serve como uma fonte de relógio de baixa resolução simulada para PTP. Esta rotina é fornecida como referência e não pode ser utilizada para a produção.

### <a name="input-parameters"></a>Parâmetros de Entrada
* **client_ptr** Ponteiro para cliente PTP para criar
* **operação** Operação de retorno, valores válidos são definidos como:
  * **NX_PTP_CLIENT_CLOCK_INIT** Inicialize o relógio.
  * **NX_PTP_CLIENT_CLOCK_SET** Definir a temperatura de corrente especificada por `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_GET** Devolva a hora atual para `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extraição de hora de `packet_ptr` . `time_ptr`
  * **NX_PTP_CLIENT_CLOCK_ADJUST** Ajuste a corrente da hora de seqdós menos de *1* segundo.
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Marque o `packet_ptr` que requer notificar o cliente PTP da marca de tempo quando é transmitido.
  * **NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Atualize o temporizador suave. Pode ser ignorado pelo relógio de hardware.
* **time_ptr** Ponteiro para a marca de tempo.
* **packet_ptr** Ponteiro para pacote.
* **callback_data** Ponteiro para dados de retorno opaco.

### <a name="return-values"></a>Valores de devolução
* **NX_SUCCESS** (0x00) Operação com sucesso
* **NX_PTP_PARAM_ERROR** (0xD03) Parâmetro inválido

### <a name="allowed-from"></a>Permitido a partir de
PTP interno

### <a name="example"></a>Exemplo
```C/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              nx_ptp_client_soft_clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_start"></a>nx_ptp_client_start

Iniciar cliente PTP.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_start(
    NX_PTP_CLIENT *client_ptr, 
    UCHAR *client_port_identity_ptr, 
    UINT client_port_identity_length,
    UINT domain, 
    UINT transport_specific, 
    NX_PTP_CLIENT_EVENT_CALLBACK event_callback,
    VOID *event_callback_data)
```

### <a name="description"></a>Description
Este serviço inicia uma instância de cliente PTP previamente criada.

### <a name="input-parameters"></a>Parâmetros de Entrada
* **client_ptr** Ponteiro para cliente PTP para criar
* **client_port_identity_ptr** Ponteiro para a porta e identidade do cliente, pode ser NULO
* **client_port_identity_length** Comprimento da porta e identidade do cliente. Deve ser 0 se client_port_identity_ptr for NULO ou NX_PTP_CLOCK_PORT_IDENTITY_SIZE (10)
* **domínio** Domínio do relógio PTP
* **transport_specific** 4 bits de transporte específicos
* **event_callback** Função de retorno invocada no evento
* **event_callback_data** Dados para a chamada do evento

### <a name="return-values"></a>Valores de devolução
* **NX_SUCCESS** (0x00) Cliente começou com sucesso
* **NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) cliente PTP já começou
* **estado** Conclusão do estado das chamadas de serviço NetX Duo e ThreadX
* NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de
Fios

### <a name="example"></a>Exemplo
```C
status = nx_ptp_client_start(&ptp_client, NX_NULL, 0, 0, 0, ptp_event_callback, NX_NULL);

/* If the client was successfully started, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_stop"></a>nx_ptp_client_stop

Pare o cliente PTP.  Depois de o cliente PTP ser parado, não processa pacotes de PTP, nem transmite pacotes ptp.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_stop(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a>Description
Este serviço para uma instância de cliente ptp previamente criada e iniciada.

### <a name="input-parameters"></a>Parâmetros de Entrada
* **client_ptr** Ponteiro para cliente PTP para parar

### <a name="return-values"></a>Valores de devolução
* **NX_SUCCESS** (0x00) Cliente parou com sucesso
* **NX_PTP_CLIENT_NOT_STARTED** (0xD01) Cliente não começou
* NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de
Fios

### <a name="example"></a>Exemplo
```C
status = nx_ptp_client_stop(&ptp_client);

/* If the client was successfully stopped, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_sync_info_get"></a>nx_ptp_client_sync_info_get

Obtenha informações de Sync.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_sync_info_get(
    NX_PTP_CLIENT_SYNC *sync_ptr, 
    USHORT *flags, 
    SHORT *utc_offset);
```

### <a name="description"></a>Description
Este serviço obtém informações da mensagem Sync. O bloco de controlo Sync é passado para a aplicação do utilizador através da função de retorno do evento.

### <a name="input-parameters"></a>Parâmetros de Entrada
* **client_ptr** Ponteiro para cliente PTP para criar
* **bandeiras** Bandeiras na mensagem sync
* **utc_offset** Compensação entre TAI e UTC

### <a name="return-values"></a>Valores de devolução
* **NX_SUCCESS** (0x00) Obtenha informações de Sincronização com sucesso
* NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de
Fios

### <a name="example"></a>Exemplo
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
USHORT utc_offset;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_SYNC:
        {
            nx_ptp_client_sync_info_get((NX_PTP_CLIENT_SYNC *)event_data, NX_NULL, &utc_offset);

            /* If the Sync information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_time_get"></a>nx_ptp_client_time_get

Obtenha a hora atual.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_time_get(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a>Description
Este serviço obtém o valor atual do relógio PTP. Está disponível independentemente do cliente PTP estar sincronizado com o relógio principal ou não.

### <a name="input-parameters"></a>Parâmetros de Entrada
* **client_ptr** Ponteiro para cliente PTP para criar
* **time_ptr** Ponteiro para o tempo ptp

### <a name="return-values"></a>Valores de devolução
* **NX_SUCCESS** (0x00) Cliente criado com sucesso
* NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de
Fios

### <a name="example"></a>Exemplo
```C
/* Get the PTP clock */
nx_ptp_client_time_get(&ptp_client, &tm);
```

## <a name="nx_ptp_client_time_set"></a>nx_ptp_client_time_set

Desa um pouco de tempo.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_time_set(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a>Description
Este serviço define o valor atual do relógio PTP. Deve ser invocado antes do início do cliente PTP.

### <a name="input-parameters"></a>Parâmetros de Entrada
* **client_ptr** Ponteiro para cliente PTP para criar
* **time_ptr** Ponteiro para o tempo ptp

### <a name="return-values"></a>Valores de devolução
* **NX_SUCCESS** (0x00) Cliente criado com sucesso
* **NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) cliente PTP já começou
* NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de
Fios

### <a name="example"></a>Exemplo
```C
/* Set current time before PTP client started.  */
status = nx_ptp_client_time_set(&ptp_client, &tm);
```

## <a name="nx_ptp_client_utility_convert_time_to_date"></a>nx_ptp_client_utility_convert_time_to_date

Converter a hora do PTP para uma data e hora UTC.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_utility_convert_time_to_date(
    NX_PTP_TIME *time_ptr, 
    LONG offset, 
    NX_PTP_DATE_TIME *date_time_ptr);
```

### <a name="description"></a>Description
Este serviço converte a hora ptp para uma data e hora UTC.

### <a name="input-parameters"></a>Parâmetros de Entrada
* **time_ptr** Ponteiro para o tempo ptp
* **compensar** Segundo offset assinado para adicionar o tempo ptp
* **date_time_ptr** Ponteiro até à data resultante

### <a name="return-values"></a>Valores de devolução
* **NX_SUCCESS** (0x00) Cliente criado com sucesso
* **Ponteiro até à data resultante** (0xD03) Parâmetro de entrada inválido
* NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de
Fios

### <a name="example"></a>Exemplo
```C
/* convert PTP time to UTC date and time */
status = nx_ptp_client_utility_convert_time_to_date(&tm, -ptp_utc_offset, &date);

/* If the time was successfully converted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_utility_time_diff"></a>nx_ptp_client_utility_time_diff

Diff duas vezes PTP.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_utility_time_diff(
    NX_PTP_TIME *time1_ptr, 
    NX_PTP_TIME *time2_ptr, 
    NX_PTP_TIME *result_ptr);
```

### <a name="description"></a>Description
Este serviço calcula a diferença entre duas vezes PTP.

### <a name="input-parameters"></a>Parâmetros de Entrada
* **time1_ptr** Ponteiro para a primeira vez PTP
* **time2_ptr** Ponteiro para o segundo tempo ptp
* **result_ptr** Ponteiro para o resultado time1-time2

### <a name="return-values"></a>Valores de devolução
* **NX_SUCCESS** (0x00) Cliente criado com sucesso
* NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de
Fios

### <a name="example"></a>Exemplo
```C
/* Diff time.  */
status = nx_ptp_client_utility_time_diff(&time1, &time2, &result);

/* If the calculation was successfully, status = NX_SUCCESS. */
```