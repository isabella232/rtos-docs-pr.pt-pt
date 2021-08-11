---
title: Aulas de anfitrião USBX API
description: Este capítulo abrange todas as APIs expostas das classes de anfitriões USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 28e733e37b06da7053f238e23e2b8b8046df2dd9940e50cd0321ccf15c27ec47
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802112"
---
# <a name="chapter-2-usbx-host-classes-api"></a>Capítulo 2: Aulas de anfitrião USBX API

Este capítulo abrange todas as APIs expostas das classes de anfitriões USBX. As seguintes APIs para cada classe são descritas em detalhe.

- Classe de impressora
- Classe de áudio
- Classe Asix
- Aula de Pima/PTP
- Classe prolífica
- Classe em série genérica

## <a name="ux_host_class_printer_read"></a>ux_host_class_printer_read

Leia a partir da interface da impressora.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_printer_read(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Description

Esta função lê-se a partir da interface da impressora. A chamada está a bloquear e só regressa quando há um erro ou quando a transferência está completa. Uma leitura só é permitida em impressoras bidis.

### <a name="parameters"></a>Parâmetros

- **impressora**: Ponteiro para a instância da classe da impressora.
- **data_pointer**: Ponteiro para o endereço-tampão da carga útil dos dados.
- **requested_length:** Comprimento a receber.
- **atual_length:** Comprimento realmente recebido.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) A transferência de dados foi concluída.
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) Função não suportada porque a impressora não é bidisal.
- **UX_TRANSFER_TIMEOUT**: (0x5c) Transferir tempo, leitura incompleta.

### <a name="example"></a>Exemplo

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_read(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_write"></a>ux_host_class_printer_write

Escreva para a interface da impressora.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_printer_write(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,  
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Description

Esta função escreve para a interface da impressora. A chamada está a bloquear e só regressa quando há um erro ou quando a transferência está completa.

### <a name="parameters"></a>Parâmetros

- **impressora**: Ponteiro para a instância da classe da impressora.
- **data_pointer**: Ponteiro para o endereço-tampão da carga útil dos dados.
- **requested_length:** Comprimento a enviar.
- **atual_length:** Comprimento realmente enviado.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) A transferência de dados foi concluída.
- **UX_TRANSFER_TIMEOUT**: (0x5c) Transferir tempo limite, escrever incompleto.

### <a name="example"></a>Exemplo

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_write(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_soft_reset"></a>ux_host_class_printer_soft_reset

Execute um reset suave à impressora.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_printer_soft_reset(UX_HOST_CLASS_PRINTER *printer)
```

### <a name="description"></a>Description

Esta função executa um reset suave à impressora.

### <a name="input-parameter"></a>Parâmetro de entrada

- **impressora**: Ponteiro para a instância da classe da impressora.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00)O reset foi concluído.
- **UX_TRANSFER_TIMEOUT**: (0x5c) Tempo de transferência, reset não concluído.

### <a name="example"></a>Exemplo

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_soft_reset(printer);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_status_get"></a>ux_host_class_printer_status_get

Obtenha o estado da impressora

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_printer_status_get( 
    UX_HOST_CLASS_PRINTER *printer,
    ULONG *printer_status)
```

### <a name="description"></a>Description

Esta função obtém o estado da impressora. O estado da impressora é semelhante ao estado LPT (padrão 1284).

### <a name="parameters"></a>Parâmetros

- **impressora**: Ponteiro para a instância da classe da impressora.
- **printer_status**: Endereço do estado a devolver.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00): O reset foi concluído.
- **UX_MEMORY_INSUFFICIENT**: (0x12) Não há memória suficiente para efetuar a operação.
- **UX_TRANSFER_TIMEOUT**: (0x5c) Tempo de transferência, reset não concluído

### <a name="example"></a>Exemplo

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_status_get(printer, printer_status);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_device_id_get"></a>ux_host_class_printer_device_id_get

Pegue o dispositivo da impressora.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_printer_device_id_get( 
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *descriptor_buffer, 
    ULONG length)
```

### <a name="description"></a>Description

Esta função obtém a cadeia de ID do dispositivo ID do dispositivo IEEE 1284 (incluindo o comprimento nos dois primeiros bytes em grande formato endiano).

### <a name="parameters"></a>Parâmetros

- **impressora**: Ponteiro para a instância da classe da impressora.
- **descriptor_buffer**: Ponteiro para um tampão para encher a cadeia de ID do dispositivo ID do dispositivo IEEE 1284 (incluindo o comprimento nos dois primeiros bytes em formato BE) 
- **comprimento**: Comprimento do tampão em bytes.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00): A operação foi bem sucedida.
- **UX_MEMORY_INSUFFICIENT**: (0x12) Não há memória suficiente para efetuar a operação.
- **UX_TRANSFER_TIMEOUT:**(0x5c) Tempo de transferência, pedido não concluído
- **UX_TRANSFER_NOT_READY**: (0x25) O aparelho encontrava-se num estado inválido – deve ser anexado, endereçado ou configurado.
- **UX_TRANSFER_STALL**: (0x21) A transferência parou.
- **TX_WAIT_ABORTED** (0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.
- **TX_SEMAPHORE_ERROR** (0x0C) Ponteiro semaphore de contagem inválida.
- **TX_WAIT_ERROR** (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de um não-fio.

### <a name="example"></a>Exemplo

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_device_id_get(printer, descriptor_buffer, length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_read"></a>ux_host_class_audio_read

Leia a partir da interface áudio.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_audio_read(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST
    *audio_transfer_request)
```

### <a name="description"></a>Description

Esta função lê a partir da interface de áudio. A chamada não está a bloquear. A aplicação deve garantir que a definição alternativa adequada foi selecionada para a interface de streaming de áudio.

### <a name="parameters"></a>Parâmetros

- **áudio**: Ponteiro para a instância da classe áudio.
- **audio_transfer_request**: Ponteiro para a estrutura de transferência de áudio.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) A transferência de dados foi concluída
- **UX_FUNCTION_NOT_SUPPORTED**" (0x54) Função não suportada

### <a name="example"></a>Exemplo

```C
/* The following example reads from the audio interface. */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;

status = ux_host_class_audio_read(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_write"></a>ux_host_class_audio_write

Escreva para a interface de áudio.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_audio_write(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST *audio_transfer_request)
```

### <a name="description"></a>Description

Esta função escreve para a interface de áudio. A chamada não está a bloquear. A aplicação deve garantir que a definição alternativa adequada foi selecionada para a interface de streaming de áudio.

### <a name="parameters"></a>Parâmetros

- **áudio**: Ponteiro para a instância da classe áudio
- **audio_transfer_request**: Ponteiro para a estrutura de transferência de áudio

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) A transferência de dados foi concluída.
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) Função não suportada.
- **ux_host_CLASS_AUDIO_WRONG_INTERFACE:**(0x81) Interface incorreta.

### <a name="example"></a>Exemplo

```C
UINT status;

/* The following example writes to the audio interface */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;
status = ux_host_class_audio_write(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_get"></a>ux_host_class_audio_control_get

Obtenha um controlo específico da interface de controlo de áudio.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_audio_control_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

### <a name="description"></a>Description

Esta função lê um controlo específico da interface de controlo de áudio.

### <a name="parameters"></a>Parâmetros

- **áudio**: Ponteiro para a instância da classe áudio
- **audio_control**: Ponteiro para a estrutura de controlo de áudio

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) A transferência de dados foi concluída
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) Função não suportada
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE:**(0x81) Interface incorreta

### <a name="example"></a>Exemplo

```C
UINT status;

/* The following example reads the volume control from a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */

audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_value_set"></a>ux_host_class_audio_control_value_set

Desa ajuste um controlo específico à interface de controlo de áudio.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_audio_control_value_set(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

**Descrição **

Esta função define um controlo específico da interface de controlo de áudio.

### <a name="parameters"></a>Parâmetros

- **áudio**: Ponteiro para a instância da classe áudio
- **audio_control**: Ponteiro para a estrutura de controlo de áudio

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) A transferência de dados foi concluída
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) Função não suportada
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE:**(0x81) Interface incorreta

### <a name="example"></a>Exemplo

```C
/* The following example sets the volume control of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

UINT status;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */

current_volume = audio_control.audio_control_cur;
audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_set"></a>ux_host_class_audio_streaming_sampling_set

Defina uma interface de definição alternativa da interface de streaming de áudio.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_audio_streaming_sampling_set
    (UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING *audio_sampling)
```

### <a name="description"></a>Description

Esta função define a interface de regulação alternativa adequada da interface de streaming de áudio de acordo com uma estrutura de amostragem específica.

### <a name="parameters"></a>Parâmetros

- **áudio**: Ponteiro para a instância da classe áudio.
- **audio_sampling**: Ponteiro para a estrutura de amostragem de áudio.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) A transferência de dados foi concluída
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) Função não suportada
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE:**(0x81) Interface incorreta
- **UX_NO_ALTERNATE_SETTING**: (0x5e) Não há definição alternativa para os valores de amostragem

### <a name="example"></a>Exemplo

```C
/* The following example sets the alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels = 2;
sampling.ux_host_class_audio_sampling_frequency = AUDIO_FREQUENCY;
sampling. ux_host_class_audio_sampling_resolution = 16;

status = ux_host_class_audio_streaming_sampling_set(audio, &sampling);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_get"></a>ux_host_class_audio_streaming_sampling_get

Obtenha possíveis definições de amostragem da interface de streaming de áudio.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_audio_streaming_sampling_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS *audio_sampling)
```

### <a name="description"></a>Description

Esta função obtém, uma a uma, todas as definições de amostragem possíveis disponíveis em cada uma das definições alternativas da interface de streaming de áudio. Na primeira vez que a função for utilizada, todos os campos do ponteiro da estrutura de chamada devem ser reiniciados. A função retornará um conjunto específico de valores de streaming após a devolução, a menos que tenha sido atingido o fim das definições alternativas. Quando esta função for reutilizada, os valores de amostragem anteriores serão utilizados para encontrar os valores de amostragem seguintes.

### <a name="parameters"></a>Parâmetros

- **áudio**: Ponteiro para a instância da classe áudio.
- **audio_sampling**: Ponteiro para a estrutura de amostragem de áudio.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) A transferência de dados foi concluída
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) Função não suportada
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE:**(0x81) Interface incorreta
- **UX_NO_ALTERNATE_SETTING**: (0x5e) Não há definição alternativa para os valores de amostragem

### <a name="example"></a>Exemplo

```C
/* The following example gets the sampling values for the first alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels=0;
sampling.ux_host_class_audio_sampling_frequency_low=0;
sampling.ux_host_class_audio_sampling_frequency_high=0;
sampling.ux_host_class_audio_sampling_resolution=0;

status = ux_host_class_audio_streaming_sampling_get(audio, &sampling);

/* If status equals UX_SUCCESS, the operation was successful and information could be displayed as follows:

printf("Number of channels %d, Resolution %d bits, frequency range %d-%d\n",
    sampling.audio_channels, sampling.audio_resolution,
    sampling.audio_frequency_low, sampling.audio_frequency_high);

*/
```

## <a name="ux_host_class_asix_read"></a>ux_host_class_asix_read

Leia a partir da interface asix.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_asix_read(
    UX_HOST_CLASS_ASIX *asix,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Description

Esta função lê-se a partir da interface asix. A chamada está a bloquear e só regressa quando há um erro ou quando a transferência está completa.

### <a name="parameters"></a>Parâmetros

- **asix**: Ponteiro para a instância de classe asix.
- **data_pointer**: Ponteiro para o endereço-tampão da carga útil dos dados.
- **requested_length:** Comprimento a receber.
- **atual_length:** Comprimento realmente recebido.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) A transferência de dados foi concluída.
- **UX_TRANSFER_TIMEOUT**: (0x5c) Transferir tempo, leitura incompleta.

### <a name="example"></a>Exemplo

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_read(asix, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_asix_write"></a>ux_host_class_asix_write

Escreva para a interface asix.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_asix_write(
    VOID *asix_class,
    NX_PACKET *packet)
```

### <a name="description"></a>Description

Esta função escreve para a interface asix. A chamada não está a bloquear.

### <a name="parameters"></a>Parâmetros

- **asix**: Ponteiro para a instância de classe asix.
- **pacote**: Pacote de dados Netx

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) A transferência de dados foi concluída.
- **UX_ERROR:**(0xFF) Não foi possível solicitar a transferência.

### <a name="example"></a>Exemplo

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_write(asix, packet);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_pima_session_open"></a>ux_host_class_pima_session_open

Abra uma sessão entre Iniciador e Responder.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_session_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a>Description

Esta função abre uma sessão entre um Iniciador PIMA e um PIMA Responder. Uma vez aberta uma sessão com sucesso, a maioria dos comandos PIMA podem ser executados.

### <a name="parameters"></a>Parâmetros

- **pima**: Ponteiro para a instância da classe pima.
- **pima_sessio**:< da sessão de ponte para o PIMA

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) Sessão aberta com sucesso
- **UX_HOST_CLASS_PIMA_RC_SESSION_ALREADY_OPENED**: (0x201E) Sessão já aberta

### <a name="example"></a>Exemplo

```C
/* Open a pima session. */

status = ux_host_class_pima_session_open(pima, pima_session);

if (status != UX_SUCCESS)
    return(UX_PICTBRIDGE_ERROR_SESSION_NOT_OPEN);
```

## <a name="ux_host_class_pima_session_close"></a>ux_host_class_pima_session_close

Feche uma sessão entre o Iniciador e o Responder.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_session_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a>Description

Esta função encerra uma sessão que foi previamente aberta entre um Iniciador PIMA e um PIMA Responder. Uma vez que uma sessão é fechada, a maioria dos comandos PIMA não podem mais ser executados.

### <a name="parameters"></a>Parâmetros

- **pima**: Ponteiro para a instância da classe pima.
- **pima_session**: Pointer to PIMA session.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) A sessão foi encerrada.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta.

### <a name="example"></a>Exemplo

```C
/* Close the pima session. */

status = ux_host_class_pima_session_close(pima, pima_session);
```

## <a name="ux_host_class_pima_storage_ids_get"></a>ux_host_class_pima_storage_ids_get

Obtenha o conjunto de identificação de armazenamento do Responder.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_storage_ids_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *storage_ids_array,
    ULONG storage_id_length)
```

### <a name="description"></a>Description

Esta função obtém a matriz de identificação de armazenamento do respondente.

### <a name="parameters"></a>Parâmetros

- **pima**: Ponteiro para a instância da classe pima.
- **pima_session**: Sessão de Ponte para PIMA
- **storage_ids_array**: Array onde os IDs de armazenamento serão devolvidos
- **storage_id_length**: Comprimento da matriz de armazenamento

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) A matriz de ID de armazenamento foi povoada
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta
- **UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente para criar o comando PIMA.

### <a name="example"></a>Exemplo

```C
/* Get the number of storage IDs. */
status = ux_host_class_pima_storage_ids_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids, 64);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_storage_info_get"></a>ux_host_class_pima_storage_info_get

Obtenha a informação de armazenamento do Responder.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_storage_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    UX_HOST_CLASS_PIMA_STORAGE *storage)
```

### <a name="description"></a>Description

Esta função obtém a informação de armazenamento de um recipiente de armazenamento de valor *storage_id*.

### <a name="parameters"></a>Parâmetros

- **pima**: Ponteiro para a instância da classe pima.
- **pima_session**: Sessão de Ponte para PIMA
- **storage_id**: Identificação do recipiente de armazenamento
- **armazenamento**: Ponteiro para o recipiente de informação de armazenamento

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) A informação de armazenamento foi recuperada
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta
- **UX_MEMORY_INSUFFICIENT** (0x12) Não há memória suficiente para criar o comando PIMA.

### <a name="example"></a>Exemplo

```C
/* Get the first storage ID info container. */
status = ux_host_class_pima_storage_info_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids[0],
    (UX_HOST_CLASS_PIMA_STORAGE *)pictbridge ->ux_pictbridge_storage);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pictbridge ->
        ux_pictbridge_pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_num_objects_get"></a>ux_host_class_pima_num_objects_get

Obtenha o número de objetos num recipiente de armazenamento da Responder.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_num_objects_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG object_format_code)
```

### <a name="description"></a>Description

Esta função obtém o número de objetos armazenados num recipiente de armazenamento específico de valor storage_id que correspondem a um código de formato específico. O número de objetos é devolvido no campo: ux_host_class_pima_session_nb_objects da estrutura pima_session.

### <a name="parameters"></a>Parâmetros

- **pima**: Ponteiro para a instância da classe pima.
- **pima_session**: Sessão de Ponte para PIMA
- **storage_id**: Identificação do recipiente de armazenamento
- **object_format_code**: Filtro de código de formato de objetos.

Os Códigos de Formato de Objeto podem ter um dos seguintes valores.

| Código de formato de objeto               | Description   |     Código USBX                          |
|----------------------------------|---------------|------------------------------------------|
| 0x3000                           | Objeto indefinido não-imagem indefinida | UX_HOST_CLASS_PIMA_OFC_UNDEFINED   |
| 0x3001                           | Associação associação (por exemplo, pasta) | UX_HOST_CLASS_PIMA_OFC_ASSOCIATION |
| 0x3002                           | Script device-modelo script específico script | UX_HOST_CLASS_PIMA_OFC_SCRIPT      |
| 0x3003                           | Executável dispositivo binário específico do modelo do dispositivo executável | UX_HOST_CLASS_PIMA_OFC_EXECUTABLE  |
| 0x3004                           | Ficheiro de texto de texto  |   UX_HOST_CLASS_PIMA_OFC_TEXT        |
| 0x3005                           | HTML Ficheiro de Linguagem de Marcação HyperText (texto) | UX_HOST_CLASS_PIMA_OFC_HTML        |
| 0x3006                           | Ficheiro de formato de ordem de impressão digital DPOF (texto) | UX_HOST_CLASS_PIMA_OFC_DPOF        |
| 0x3007                           | Clipe de áudio AIFF  |  UX_HOST_CLASS_PIMA_OFC_AIFF        |
| 0x3008                           | Clipe de áudio WAV   |  UX_HOST_CLASS_PIMA_OFC_WAV         |
| 0x3009                           | Clipe de áudio MP3   |  UX_HOST_CLASS_PIMA_OFC_MP3         |
| 0x300A                           | Clipe de vídeo DA AVI   |  UX_HOST_CLASS_PIMA_OFC_AVI         |
| 0x300B                           | Clipe de vídeo MPEG  |  UX_HOST_CLASS_PIMA_OFC_MPEG        |
| 0x300C                           | Formato avançado de streaming asf Microsoft (vídeo) | UX_HOST_CLASS_PIMA_OFC_ASF         |
| 0x3800                           | Objeto de imagem desconhecido indefinido | UX_HOST_CLASS_PIMA_OFC_QT          |
| 0x3801                           | Formato de ficheiro permutável EXIF/JPEG, padrão JEIDA | UX_HOST_CLASS_PIMA_OFC_EXIF_JPEG   |
| 0x3802                           | TIFF/EP Tag Formato de ficheiro de imagem para fotografia eletrónica | UX_HOST_CLASS_PIMA_OFC_TIFF_EP     |
| 0x3803                           | Formato de imagem de Armazenamento estruturado FlashPix | UX_HOST_CLASS_PIMA_OFC_FLASHPIX    |
| 0x3804                           | BMP Microsoft Windows ficheiro Bitmap | UX_HOST_CLASS_PIMA_OFC_BMP         |
| 0x3805                           | Formato de ficheiro de imagem da câmera cânone CIFF | UX_HOST_CLASS_PIMA_OFC_CIFF        |
| 0x3806                           | Reservado indefinido |  |
| 0x3807                           | Formato de troca de gráficos GIF | UX_HOST_CLASS_PIMA_OFC_GIF         |
| 0x3808                           | Formato de troca de ficheiros JFIF JPEG | UX_HOST_CLASS_PIMA_OFC_JFIF        |
| 0x3809                           | PCD PhotoCD Image Pac | UX_HOST_CLASS_PIMA_OFC_PCD         |
| 0x380A                           | Formato de imagem de quickdraw PICT | UX_HOST_CLASS_PIMA_OFC_PICT        |
| 0x380B                           | Gráficos de rede portáteis png | UX_HOST_CLASS_PIMA_OFC_PNG         |
| 0x380C                           | Reservado indefinido |   |
| 0x380D                           | Formato de ficheiro de imagem de marcação TIFF | UX_HOST_CLASS_PIMA_OFC_TIFF        |
| 0x380E                           | TIFF/IT Tag Formato de ficheiro de imagem para tecnologias de informação (artes gráficas) | UX_HOST_CLASS_PIMA_OFC_TIFF_IT     |
| 0x380F                           | JP2 JPEG2000 Formato de ficheiro de base | UX_HOST_CLASS_PIMA_OFC_JP2         |
| 0x3810                           | JPX JPEG2000 Formato de ficheiro estendido | UX_HOST_CLASS_PIMA_OFC_JPX         |
| Todos os outros códigos com MSN de 0011 | Qualquer reservado indefinido para uso futuro |                                    |
| Todos os outros códigos com MSN de 1011 | Qualquer tipo definido pelo fornecedor definido pelo fornecedor: Imagem |                                    |

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) A transferência de dados foi concluída.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta
- **UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente para criar o comando PIMA.

### <a name="example"></a>Exemplo

```C
/* Get the number of objects on all containers matching a SCRIPT object. */
status = ux_host_class_pima_num_objects_get(pima, pima_session,
    UX_PICTBRIDGE_ALL_CONTAINERS, UX_PICTBRIDGE_OBJECT_SCRIPT);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_**host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
} else
    /* The number of objects is returned in the field: pima_session -> ux_host_class_pima_session_nb_objects */
```

## <a name="ux_host_class_pima_object_handles_get"></a>ux_host_class_pima_object_handles_get

Obtenha pegas de objeto do Responder.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_object_handles_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *object_handles_array,
    ULONG object_handles_length,
    ULONG storage_id,
    ULONG object_format_code,
    ULONG object_handle_association)
```

### <a name="description"></a>Description

Devolve uma matriz de pegas de objeto presentes no recipiente de armazenamento indicado pelo parâmetro storage_id. Se for desejada uma lista agregada em todas as lojas, este valor será definido para 0xFFFFFFFF.

### <a name="parameters"></a>Parâmetros

- **pima**: Ponteiro para a instância da classe pima.
- **pima_session**: Sessão de Ponte para PIMA
- **object_handes_array**: Array onde as pegas são devolvidas
- **object_handles_length**: Comprimento da matriz
- **storage_id**: Identificação do recipiente de armazenamento
- **object_format_code:** Código de formato para objeto (ver tabela para função ux_host_class_pima_num_objects_get)
- **object_handle_association**: Valor opcional da associação de objetos

A associação de pega de objeto pode ser um dos valores da tabela abaixo:

| Código de Associação                        | Tipo de Associação      | Interpretação       |
|----------------------------------------|----------------------|----------------------|
| 0x0000                                 | Indefinido            | Indefinido            |
| 0x0001                                 | Genérico        | Não é bem-de-suso               |
| 0x0002                                 | Álbum                | Reservado             |
| 0x0003                                 | TimeSequence         | DefaultPlaybackDelta |
| 0x0004                                 | HorizontalPanoramic  | Não é bem-de-suso               |
| 0x0005                                 | VerticalPanoramic    | Não é bem-de-suso               |
| 0x0006                                 | 2DPanoramic          | ImagesPerRow         |
| 0x0007                                 | Data Auxiliar        | Indefinido            |
| Todos os outros valores com bit 15 definido para 0  | Reservado             | Indefinido            |
| Todos os valores com bit 15 definido para 1        | Definido pelo fornecedor       | Definido pelo fornecedor       |

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) A transferência de dados foi concluída.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta
- **UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente para criar o comando PIMA.

### <a name="example"></a>Exemplo

```C
/* Get the array of objects handles on the container. */
status = ux_**host_class_pima_object_handles_get(pima, pima_session,
    pictbridge ->ux_pictbridge_object_handles_array,
    4 * pima_session ->ux_host_class_pima_session_nb_objects,
    UX_PICTBRIDGE_ALL_CONTAINERS,
    UX_PICTBRIDGE_OBJECT_SCRIPT, 0);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_object_info_get"></a>ux_host_class_pima_object_info_get

Obtenha a informação do objeto do Responder.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_object_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Description

Esta função obtém a informação do objeto para uma pega de objeto.

### <a name="parameters"></a>Parâmetros

- **pima**: Ponteiro para a instância da classe pima.
- **pima_session**: Sessão de Ponte para PIMA
- **object_handle**: Cabo do objeto
- **objeto**: Ponteiro para objeto de informação

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) A transferência de dados foi concluída.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta
- **UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente para criar o comando PIMA.

### <a name="example"></a>Exemplo

```C
/* We search for an object that is a picture or a script. */
object_index = 0;

while (object_index < pima_session -> ux_host_class_pima_session_nb_objects)
{
    /* Get the object info structure. */
    status = ux_**host_class_pima_object_info_get(pima, pima_session,
        pictbridge -> ux_pictbridge_object_handles_array[object_index], 
        pima_object);

    if (status != UX_SUCCESS)
    {
        /* Close the pima session. */
        status = ux_host_class_pima_session_close(pima, pima_session);

        return(UX_PICTBRIDGE_ERROR_INVALID_OBJECT_HANDLE );
    }
}
```

## <a name="ux_host_class_pima_object_info_send"></a>ux_host_class_pima_object_info_send

Envie a informação do objeto para o Responder.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_object_info_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG parent_object_id,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Description

Esta função envia as informações de armazenamento para um recipiente de armazenamento de valor storage_id. O Iniciador deve utilizar este comando antes de enviar um objeto ao socorrista.

### <a name="parameters"></a>Parâmetros

- **pima**: Ponteiro para a instância da classe pima.
- **pima_session**: Pointer to PIMA session.
- **storage_id**: ID de armazenamento de destino.
- **parent_object_id**: Parent ObjectHandle on Responder onde o objeto deve ser colocado.
- **objeto**: Ponteiro para objeto de informação.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) A transferência de dados foi concluída.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta
- **UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente para criar o comando PIMA.

### <a name="example"></a>Exemplo

```C
/* Send a script info. */
status = ux_host_class_pima_object_info_send(pima, pima_session,
    0, 0, pima_object);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_ERROR);
}
```

## <a name="ux_host_class_pima_object_open"></a>ux_host_class_pima_object_open

Abra um objeto armazenado no Responder.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_object_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Description

Esta função abre um objeto no respondente antes de ler ou escrever.

### <a name="parameters"></a>Parâmetros

- **pima**: Ponteiro para a instância da classe pima.
- **pima_session**: Pointer to PIMA session.
- **object_handle:** manuseie o objeto.
- Objec : **Ponteiros** de objeção ao recipiente de informações.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) A transferência de dados foi concluída.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta
- **UX_HOST_CLASS_PIMA_RC_OBJECT_ALREADY_OPENED**: (0x2021) Objeto já aberto.
- **UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente para criar o comando PIMA.

### <a name="example"></a>Exemplo

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_get"></a>ux_host_class_pima_object_get

Guarde um objeto no Responder.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_object_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer,
    ULONG object_buffer_length,
    ULONG *object_actual_length)
```

### <a name="description"></a>Description

Esta função recebe um objeto no respondente.

### <a name="parameters"></a>Parâmetros

- **pima**: Ponteiro para a instância da classe pima.
- **pima_session**: Sessão de Ponte para PIMA
- **object_handle:** cabo do objeto
- **objeto**: Ponteiro para objeto de informação
- **object_buffer**: Endereço de dados de objetos
- **object_buffer_length**: Comprimento solicitado do objeto
- **object_atual_length**: Comprimento do objeto devolvido

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS:**(0x00) O objeto foi transferido
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Objeto não aberto.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Acesso a objeto negado
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER:**(0x2007) A transferência está incompleta
- **UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente para criar o comando PIMA.
- **UX_TRANSFER_ERROR**: (0x23) Erro de transferência ao ler objeto

### <a name="example"></a>Exemplo

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);

/* Set the object buffer pointer. */
object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Obtain all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Get the object data. */
    status = ux_host_class_pima_object_get(pima, pima_session,
        object_handle, pima_object, object_buffer,
        requested_length, &actual_length);

    if (status != UX_SUCCESS)
    {
        /* We had a problem, abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* And close the object. */
        ux_host_class_pima_object_close(pima, pima_session,
            object_handle, pima_object, object);

        return(status);

    }

    /* We have received some data, update the length remaining. */
    object_length -= actual_length;

    /* Update the buffer address. */
    object_buffer += actual_length;

}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session,
    object_handle, pima_object, object);
```

## <a name="ux_host_class_pima_object_send"></a>ux_host_class_pima_object_send

Envie um objeto armazenado no Responder.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_object_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer, ULONG object_buffer_length)
```

### <a name="description"></a>Description

Esta função envia um objeto para o socorrista.

### <a name="parameters"></a>Parâmetros

- **pima**: Ponteiro para a instância da classe pima.
- **pima_sessio**: Sessão de Ponte para PIMA
- **object_handle:** cabo do objeto
- **objeto**: Ponteiro para objeto de informação
- **object_buffer**: Endereço de dados de objetos
- **object_buffer_length**: Comprimento solicitado do objeto

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) A transferência de dados foi concluída.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Objeto não aberto.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Acesso a objeto negado
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER:**(0x2007) A transferência está incompleta
- **UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente para criar o comando PIMA.
- **UX_TRANSFER_ERROR**: (0x23) Erro de transferência ao escrever objeto

### <a name="example"></a>Exemplo

```C
/* Open the object. */
status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Get the object length. */
object_length = pima_object ->ux_host_class_pima_object_compressed_size;

/* Recall the object buffer address. */
pima_object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Send all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Send the object data. */
    status = ux_host_class_pima_object_send(pima,
        pima_session, pima_object,
        pima_object_buffer, requested_length);

    if (status != UX_SUCCESS)
    {
        /* Abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* Return status. */
        return(status);
    }

    /* We have sent some data, update the length remaining. */
    object_length -= requested_length;
}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle,
    pima_object, object);
```

## <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

Guarde um objeto de polegar no Responder.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_thumb_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *thumb_buffer, ULONG thumb_buffer_length,
    ULONG *thumb_actual_length)
```

### <a name="description"></a>Description

Esta função recebe um objeto de polegar no socorrista.

### <a name="parameters"></a>Parâmetros

- **pima**: Ponteiro para a instância da classe pima.
- **pima_session**: Pointer to PIMA session.
- **object_handle:** manuseie o objeto.
- **objeto**: Ponteiro para objeto de informação.
- **thumb_buffer**: Endereço dos dados dos objetos de polegar.
- **thumb_buffer_length:** Comprimento solicitado do objeto do polegar.
- **thumb_atual_length:** Comprimento do objeto do polegar devolvido.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) A transferência de dados foi concluída.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta.
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Objeto não aberto.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Acesso ao objeto negado.
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER:**(0x2007) A transferência está incompleta.
- **UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente para criar o comando PIMA.
- **UX_TRANSFER_ERROR**: (0x23) Erro de transferência durante a leitura do objeto.

### <a name="example"></a>Exemplo

```C
/* Get the thumb object data. */

status = ux_host_class_pima_thumb_get(pima, pima_session,
    object_handle, pima_object, object_buffer,
    requested_length, &actual_length);

if (status != UX_SUCCESS)
{
    /* And close the object. */
    ux_host_class_pima_object_close(pima, pima_session, object_handle, pima_object, object);

    return(status);
}
```

## <a name="ux_host_class_pima_object_delete"></a>ux_host_class_pima_object_delete

Elimine um objeto armazenado no Respondente.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_object_delete(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle)
```

### <a name="description"></a>Description

Esta função elimina um objeto no respondente

### <a name="parameters"></a>Parâmetros

- **pima**: Ponteiro para a instância da classe pima.
- **pima_session**: Sessão de Ponte para PIMA
- **object_handle:** cabo do objeto

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) O objeto foi apagado.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED:**(0x200f) Não pode eliminar objeto.
- **UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente para criar o comando PIMA.

### <a name="example"></a>Exemplo

```C
/* Delete the object. */
status = ux_host_class_pima_object_delete(pima, pima_session, object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_close"></a>ux_host_class_pima_object_close

Feche um objeto armazenado no Responder

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_object_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle, UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Description

Esta função fecha um objeto no respondente.

### <a name="parameters"></a>Parâmetros

- **pima**: Ponteiro para a instância da classe pima.
- **pima_session**: Pointer to PIMA session.
- **object_handle:** Manuseie o objeto.
- **objeto**: Ponteiro para opor.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS:**(0x00) O objeto foi fechado.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta.
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Objeto não aberto.
- **UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente para criar o comando PIMA.

### <a name="example"></a>Exemplo

```C
/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle, object);
```

## <a name="ux_host_class_gser_read"></a>ux_host_class_gser_read

Leia a partir da interface de série genérica.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_gser_read(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Description

Esta função lê-se a partir da interface de série genérica. A chamada está a bloquear e só regressa quando há um erro ou quando a transferência está completa.

### <a name="parameters"></a>Parâmetros

- **gser**: Ponteiro para a instância da classe gser.
- **interface_index**: Índice de interface para ler.
- **data_pointer**: Ponteiro para o endereço-tampão da carga útil dos dados.
- **requested_length:** Comprimento a receber.
- **atual_length:** Comprimento realmente recebido.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) A transferência de dados foi concluída.
- **UX_TRANSFER_TIMEOUT**: (0x5c) Transferir tempo, leitura incompleta.

### <a name="example"></a>Exemplo

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_gser_read(cdc_acm, interface_index,data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_write"></a>ux_host_class_gser_write

Escreva para a interface de série genérica.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_gser_write(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Description

Esta função escreve para a interface de série genérica. A chamada está a bloquear e só regressa quando há um erro ou quando a transferência está completa.

### <a name="parameters"></a>Parâmetros

- **gser**: Ponteiro para a instância da classe gser.
- **interface_index**: Interface para a qual escrever.
- **data_pointer**: Ponteiro para o endereço-tampão da carga útil dos dados.
- **requested_length:** Comprimento a enviar.
- **atual_length:** Comprimento realmente enviado.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) A transferência de dados foi concluída.
- **UX_TRANSFER_TIMEOUT**: (0x5c) Transferir tempo limite, escrever incompleto.

### <a name="example"></a>Exemplo

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_cdc_acm_write(gser, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_ioctl"></a>ux_host_class_gser_ioctl

Execute uma função IOCTL para a interface de série genérica.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_gser_ioctl(
    UX_HOST_CLASS_GSER *gser,
    ULONG ioctl_function,
    VOID *parameter)
```

### <a name="description"></a>Description

Esta função desempenha uma função de coitl específica para a interface gser. A chamada está a bloquear e só retorna quando há um erro ou quando o comando está concluído.

### <a name="parameters"></a>Parâmetros

- **gser**: Ponteiro para a instância da classe gser.
- **ioctl_function:** função de ioctl a desempenhar. Consulte a tabela abaixo para uma das funções de coitl permitidas.
- **parâmetro**: Pointer to a parameter specific to the ioctl

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) A transferência de dados foi concluída.
- **UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente.
- **UX_HOST_CLASS_UNKNOWN**: (0x59) Instância de classe errada
- **UX_FUNCTION_NOT_SUPPORTED:**(0x54) Função IOCTL desconhecida.

### <a name="ioctl-functions"></a>Funções ioctl

- UX_HOST_CLASS_GSER_IOCTL_SET_LINE_CODING
- UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING
- UX_HOST_CLASS_GSER_IOCTL_SET_LINE_STATE
- UX_HOST_CLASS_GSER_IOCTL_SEND_BREAK
- UX_HOST_CLASS_GSER_IOCTL_ABORT_IN_PIPE
- UX_HOST_CLASS_GSER_IOCTL_ABORT_OUT_PIPE
- UX_HOST_CLASS_GSER_IOCTL_NOTIFICATION_CALLBACK
- UX_HOST_CLASS_GSER_IOCTL_GET_DEVICE_STATUS

### <a name="example"></a>Exemplo

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_gser_ioctl(gser,
    UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING,
    (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_reception_start"></a>ux_host_class_gser_reception_start

Inicie a receção na interface de série genérica

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_gser_reception_start(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a>Description

Esta função inicia a receção na interface genérica de classe em série. Esta função permite a receção não bloqueada. Quando um tampão é recebido, uma chamada de volta invocada para o pedido.

### <a name="parameters"></a>Parâmetros

- **gser** Ponteiro para a instância da classe GSER.
- **gser_reception** Estrutura que contém os parâmetros de receção

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) A transferência de dados foi concluída.
- **UX_HOST_CLASS_UNKNOWN** (0x59) Instância de classe errada
- **Erro UX_ERROR** (0x01)

### <a name="example"></a>Exemplo

```C
/* Start the reception for gser. AT commands are on interface 2. */
gser_reception.ux_host_class_gser_reception_interface_index =
    UX_DEMO_GSER_AT_INTERFACE;
gser_reception.ux_host_class_gser_reception_block_size =
    UX_DEMO_RECEPTION_BLOCK_SIZE;
gser_reception.ux_host_class_gser_reception_data_buffer =
    gser_reception_buffer;
gser_reception.ux_host_class_gser_reception_data_buffer_size =
    UX_DEMO_RECEPTION_BUFFER_SIZE;
gser_reception.ux_host_class_gser_reception_callback =
    tx_demo_thread_callback;

ux_host_class_gser_reception_start(gser, &gser_reception);
```

## <a name="ux_host_class_gser_reception_stop"></a>ux_host_class_gser_reception_stop

Parar a receção na interface de série genérica

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_gser_reception_stop(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a>Description

Esta função impede a receção na interface genérica de classe em série.

### <a name="parameters"></a>Parâmetros

- **gser** Ponteiro para a instância da classe GSER.
- **gser_reception** Estrutura que contém os parâmetros de receção

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) A transferência de dados foi concluída.
- **UX_HOST_CLASS_UNKNOWN** (0x59) Instância de classe errada
- **Erro UX_ERROR** (0x01)

### <a name="example"></a>Exemplo

```C
/* Stops the reception for gser. */
ux_host_class_gser_reception_stop(gser, &gser_reception);
```
