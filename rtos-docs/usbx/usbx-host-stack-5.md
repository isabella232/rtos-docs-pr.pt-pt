---
title: Capítulo 5 - Aulas de Anfitrião USBX API
description: Saiba mais sobre a API das Classes de Anfitriões USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: bf5876042e08a59979adcd429917bfc3fbfdbc20
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828621"
---
# <a name="chapter-5---usbx-host-classes-api"></a>Capítulo 5 - Aulas de Anfitrião USBX API

Este capítulo abrange todas as APIs expostas das classes de anfitriões USBX. As seguintes APIs para cada classe são descritas em detalhe.

- Classe HID
- Classe CDC-ACM
- Classe CDC-ECM
- Classe de armazenamento

## <a name="ux_host_class_hid_client_register"></a>ux_host_class_hid_client_register

Registe um cliente HID na classe HID.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_class_hid_client_register(
    UCHAR *hid_client_name,
    UINT (*hid_client_handler)
    (struct UX_HOST_CLASS_HID_CLIENT_COMMAND_STRUCT *));
```

### <a name="description"></a>Descrição

Esta função é utilizada para registar um cliente HID na classe HID. A classe HID precisa de encontrar uma correspondência entre um dispositivo HID e um cliente HID antes de solicitar dados deste dispositivo.

> [!NOTE]
> A cadeia C de hid_client_name deve ser anulada e o comprimento do mesmo (sem o próprio exterminador nulo) não deve ser superior **UX_HOST_CLASS_HID_MAX_CLIENT_NAME_LENGTH**.

### <a name="parameters"></a>Parâmetros

- **hid_client_name** Ponteiro para o nome do cliente HID.
- **hid_client_handler** Ponteiro para o manipulador de clientes HID.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) A transferência de dados foi concluída
- **UX_MEMORY_INSUFFICIENT** (0x12) A atribuição de memória para cliente falhou.
- **UX_MEMORY_ARRAY_FULL** (0x1a) Clientes Max já registados.
- **UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) Esta classe já existe

### <a name="example"></a>Exemplo

```c
UINT status;

/* The following example illustrates how to register a HID client, in
this case a USB mouse, to the HID class. */

status = ux_host_class_hid_client_register("ux_host_class_hid_client_mouse",
    ux_host_class_hid_mouse_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_callback_register"></a>ux_host_class_hid_report_callback_register

Registe uma chamada da classe HID.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_class_hid_report_callback_register(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_REPORT_CALLBACK *call_back);
```

### <a name="description"></a>Descrição

Esta função é utilizada para registar uma chamada da classe HID para o cliente HID quando um relatório é recebido.

### <a name="parameters"></a>Parâmetros

- **escondeu** Ponteiro para a instância da classe HID
- **call_back** Ponteiro para a estrutura call_back

### <a name="return-values"></a>Valores de retorno

- **UX_SUCCESS** (0x00) A transferência de dados foi concluída
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) Caso HID inválido.
- **UX_HOST_CLASS_HID_REPORT_ERROR** (0x79) Erro no registo de chamada do relatório.

### <a name="example"></a>Exemplo

```c
UINT status;

/* This example illustrates how to register a HID client, in this case a USB mouse, to the HID class. In this case, the HID client is asking the HID class to call the client for each usage received in the HID report. */

call_back.ux_host_class_hid_report_callback_id = 0;
call_back.ux_host_class_hid_report_callback_function = ux_host_class_hid_mouse_callback;

call_back.ux_host_class_hid_report_callback_buffer = UX_NULL;
call_back.ux_host_class_hid_report_callback_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

call_back.ux_host_class_hid_report_callback_length = 0;

status = ux_host_class_hid_report_callback_register(hid, &call_back);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_periodic_report_start"></a>ux_host_class_hid_periodic_report_start

Inicie o ponto final periódico para uma instância de classe HID.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_class_hid_periodic_report_start(UX_HOST_CLASS_HID *hid);
```

### <a name="description"></a>Descrição

Esta função é utilizada para iniciar o ponto final periódico (interromper) para o exemplo da classe HID que está ligada a este cliente HID. A classe HID não pode iniciar o ponto final periódico até que o cliente HID seja ativado e, portanto, cabe ao cliente HID iniciar este ponto final para receber relatórios.

### <a name="input-parameter"></a>Parâmetro de entrada

- **escondeu** Ponteiro para a instância da classe HID.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) Relatórios periódicos com sucesso começaram.
- **ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A) Erro no relatório periódico.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) caso de classe HID não existe.

### <a name="example"></a>Exemplo

```c
UINT status;

/* The following example illustrates how to start the periodic
endpoint. */

status = ux_host_class_hid_periodic_report_start(hid);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_periodic_report_stop"></a>ux_host_class_hid_periodic_report_stop

Pare o ponto final periódico para uma instância de classe HID.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_class_hid_periodic_report_stop(UX_HOST_CLASS_HID *hid);
```

### <a name="description"></a>Descrição

Esta função é utilizada para parar o ponto final periódico (interromper) para o exemplo da classe HID que está ligada a este cliente HID. A classe HID não pode parar o ponto final periódico até que o cliente HID seja desativado, todos os seus recursos libertados e, portanto, cabe ao cliente HID parar este ponto final.

### <a name="input-parameter"></a>Parâmetro de entrada

- **escondeu** Ponteiro para a instância da classe HID.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) Relatórios periódicos parados com sucesso.
- **ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A) Erro no relatório periódico.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) caso de classe HID não existe

### <a name="example"></a>Exemplo

```c
UINT status;

/* The following example illustrates how to stop the periodic endpoint. */

status = ux_host_class_hid_periodic_report_stop(hid);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_get"></a>ux_host_class_hid_report_get

Obtenha um relatório de uma instância da classe HID.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_class_hid_report_get(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_CLIENT_REPORT *client_report);
```

### <a name="description"></a>Descrição

Esta função é utilizada para receber um relatório diretamente do dispositivo sem depender do ponto final periódico. Este relatório provém do ponto final de controlo, mas o seu tratamento é o mesmo que se tratasse do ponto final periódico.

### <a name="parameters"></a>Parâmetros

- **escondeu** Ponteiro para a instância da classe HID.
- **client_report** Ponteiro para o relatório do cliente hid.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) O relatório foi recebido com sucesso.
- **UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) O relatório do cliente foi inválido ou erro durante a transferência.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) caso de classe HID não existe.
- **UX_BUFFER_OVERFLOW** (0x5d) O tampão fornecido não é suficientemente grande para acomodar o relatório não comprimido.

### <a name="example"></a>Exemplo

```c
UX_HOST_CLASS_HID_CLIENT_REPORT input_report;

UINT status;

/* The following example illustrates how to get a report. */

input_report.ux_host_class_hid_client_report = hid_report;
input_report.ux_host_class_hid_client_report_buffer = buffer;
input_report.ux_host_class_hid_client_report_length = length;
input_report.ux_host_class_hid_client_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

status = ux_host_class_hid_report_get(hid, &input_report);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_set"></a>ux_host_class_hid_report_set

Enviar um relatório

### <a name="prototype"></a>Prototype

```c
UINT ux_host_class_hid_report_set(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_CLIENT_REPORT *client_report);
```

### <a name="description"></a>Descrição

Esta função é utilizada para enviar um relatório diretamente para o dispositivo.

### <a name="parameters"></a>Parâmetros

- **escondeu** Ponteiro para a instância da classe HID.
- **client_report** Ponteiro para o relatório do cliente hid.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) O relatório foi enviado com sucesso.
- **UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) O relatório do cliente foi inválido ou erro durante a transferência.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) caso de classe HID não existe.
- **UX_HOST_CLASS_HID_REPORT_OVERFLOW** (0x5d) O tampão fornecido não é suficientemente grande para acomodar o relatório não comprimido.

### <a name="example"></a>Exemplo

```c
/* The following example illustrates how to send a report. */

UX_HOST_CLASS_HID_CLIENT_REPORT input_report;

input_report.ux_host_class_hid_client_report = hid_report;
input_report.ux_host_class_hid_client_report_buffer = buffer;
input_report.ux_host_class_hid_client_report_length = length;
input_report.ux_host_class_hid_client_report_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

status = ux_host_class_hid_report_set(hid, &input_report);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_mouse_buttons_get"></a>ux_host_class_hid_mouse_buttons_get

Pegue botões de rato.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_class_hid_mouse_buttons_get(
    UX_HOST_CLASS_HID_MOUSE *mouse_instance,
    ULONG *mouse_buttons);
```

### <a name="description"></a>Descrição

Esta função é usada para obter os botões do rato

### <a name="parameters"></a>Parâmetros

- **mouse_instance** Ponteiro para a instância do rato HID.
- **mouse_buttons** Ponteiro para os botões de retorno.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** botão do rato (0x00) recuperado com sucesso.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) caso de classe HID não existe.

### <a name="example"></a>Exemplo

```c
/* The following example illustrates how to obtain mouse buttons. */

UX_HOST_CLASS_HID_MOUSE *mouse_instance;

ULONG mouse_buttons;

status = ux_host_class_hid_mouse_button_get(mouse_instance, &mouse_buttons);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_mouse_position_get"></a>ux_host_class_hid_mouse_position_get

Obter a posição do rato.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_class_hid_mouse_position_get(
    UX_HOST_CLASS_HID_MOUSE *mouse_instance,
    SLONG *mouse_x_position, 
    SLONG *mouse_y_position);
```

### <a name="description"></a>Descrição

Esta função é usada para obter a posição do rato em coordenadas x & y.

### <a name="parameters"></a>Parâmetros

- **mouse_instance** Ponteiro para a instância do rato HID.
- **mouse_x_position** Ponteiro para a coordenada x.
- **mouse_y_position** Ponteiro para a coordenada y.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) X &amp; Y coordenadas com sucesso recuperadas.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) caso de classe HID não existe.

### <a name="example"></a>Exemplo

```c
/* The following example illustrates how to obtain mouse coordinates. */

UX_HOST_CLASS_HID_MOUSE *mouse_instance;

SLONG mouse_x_position;
SLONG mouse_y_position;

status = ux_host_class_hid_mouse_position_get(mouse_instance,
    &mouse_x_position, &mouse_y_position);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_keyboard_key_get"></a>ux_host_class_hid_keyboard_key_get

Pegue a chave e o estado do teclado.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_class_hid_keyboard_key_get(
    UX_HOST_CLASS_HID_KEYBOARD *keyboard_instance,
    ULONG *keyboard_key, 
    ULONG *keyboard_state);
```

### <a name="description"></a>Descrição

Esta função é utilizada para obter a chave e o estado do teclado.

### <a name="parameters"></a>Parâmetros

- **keyboard_instance** Ponteiro para a instância do teclado HID.
- **keyboard_key** Ponteiro para o recipiente da chave do teclado.
- **keyboard_state** Ponteiro para o recipiente do estado do teclado.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) Chave e estado recuperado com sucesso.
- **UX_ERROR** (0xff) Nada a relatar.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) caso de classe HID não existe.

O estado do teclado pode ter os seguintes valores.

- **0x10000** UX_HID_KEYBOARD_STATE_KEY_UP
- **UX_HID_KEYBOARD_STATE_NUM_LOCK** 0x0001
- **0x0002 UX_HID_KEYBOARD_STATE_CAPS_LOCK**
- **UX_HID_KEYBOARD_STATE_SCROLL_LOCK** 0x0004
- **UX_HID_KEYBOARD_STATE_MASK_LOCK** 0x0007
- **UX_HID_KEYBOARD_STATE_LEFT_SHIFT** 0x0100
- **UX_HID_KEYBOARD_STATE_RIGHT_SHIFT** 0x0200
- **0x0300 UX_HID_KEYBOARD_STATE_SHIFT**
- **UX_HID_KEYBOARD_STATE_LEFT_ALT** 0x0400
- **UX_HID_KEYBOARD_STATE_RIGHT_ALT** 0x0800
- **0x0a00 UX_HID_KEYBOARD_STATE_ALT**
- **UX_HID_KEYBOARD_STATE_LEFT_CTRL** 0x1000
- **0x2000 UX_HID_KEYBOARD_STATE_RIGHT_CTRL**
- **UX_HID_KEYBOARD_STATE_CTRL** 0x3000
- **UX_HID_KEYBOARD_STATE_LEFT_GUI** 0x4000
- **UX_HID_KEYBOARD_STATE_RIGHT_GUI** 0x8000
- **0xa000 UX_HID_KEYBOARD_STATE_GUI**

### <a name="example"></a>Exemplo

```c
while (1)
{

    /* Get a key/state from the keyboard. */
    status = ux_host_class_hid_keyboard_key_get(keyboard,
        &keyboard_char, &keyboard_state);

    /* Check if there is something. */
    if (status == UX_SUCCESS)
    {

        #ifdef UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE
            if (keyboard_state & UX_HID_KEYBOARD_STATE_KEY_UP)
            {
                /* The key was released. */
            } else
            {
                /* The key was pressed. */
            }
        #endif

        /* We have a character in the queue. */
        keyboard_queue[keyboard_queue_index] = (UCHAR) keyboard_char;

        /* Can we accept more ? */
        if(keyboard_queue_index < 1024)
            keyboard_queue_index++;
    }

    tx_thread_sleep(10);

}
```

## <a name="ux_host_class_hid_keyboard_ioctl"></a>ux_host_class_hid_keyboard_ioctl

Execute uma função IOCTL no teclado HID.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_class_hid_keyboard_ioctl(
    UX_HOST_CLASS_HID_KEYBOARD *keyboard_instance,
    ULONG ioctl_function, VOID *parameter);
```

### <a name="description"></a>Descrição

Esta função executa uma função de coitl específica para o teclado HID. A chamada está a bloquear e só retorna quando há um erro ou quando o comando está concluído.

### <a name="parameters"></a>Parâmetros

- **keyboard_instance** Ponteiro para a instância do teclado HID.
- **ioctl_function** função de localização. Consulte a tabela abaixo para uma das funções de coitl permitidas.
- **parâmetro** Ponteiro para um parâmetro específico do ioctl.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) A função ioctl concluída com sucesso.
- **UX_FUNCTION_NOT_SUPPORTED** (0x54) Função IOCTL desconhecida

### <a name="ioctl-functions"></a>Funções ioctl

- UX_HID_KEYBOARD_IOCTL_SET_LAYOUT
- UX_HID_KEYBOARD_IOCTL_KEY_DECODING_ENABLE
- UX_HID_KEYBOARD_IOCTL_KEY_DECODING_DISABLE

### <a name="example--change-keyboard-layout"></a>Exemplo – alterar o layout do teclado

```c
UINT status;

/* This example shows usage of the SET_LAYOUT IOCTL function.
    USBX receives raw key values from the device (these raw values
    are defined in the HID usage table specification) and optionally
    decodes them for application usage. The decoding is performed
    based on a set of arrays that act as maps – which array is used
    depends on the raw key value (i.e. keypad and non-keypad) and
    the current state of the keyboard (i.e. shift, caps lock, etc.). */

/* When the shift condition is not present and the raw key value
    is not within the keypad value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_unshifted_map[] =
{
    0,0,0,0,
    'a','b','c','d','e','f','g',
    'h','i','j','k','l','m','n',
    'o','p','q','r','s','t',
    'u','v','w','x','y','z',
    '1','2','3','4','5','6','7','8','9','0',
    0x0d,0x1b,0x08,0x07,0x20,'-','=','[',']',
    '\\','#',';',0x27,'`',',','.','/',0xf0,
    0xbb,0xbc,0xbd,0xbe,0xbf,0xc0,0xc1,0xc2,0xc3,0xc4,0xc5,0xc6,
    0x00,0xf1,0x00,0xd2,0xc7,0xc9,0xd3,0xcf,0xd1,0xcd,0xcd,0xd0,0xc8,0xf2,
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
    0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,
};

/* When the shift condition is present and the raw key value
    is not within the keypad value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_shifted_map[] =
{
    0,0,0,0,
    'A','B','C','D','E','F','G',
    'H','I','J','K','L','M','N',
    'O','P','Q','R','S','T',
    'U','V','W','X','Y','Z',
    '!','@','#','$','%','^','&','*','(',')',
    0x0d,0x1b,0x08,0x07,0x20,'_','+','{','}',
    '|','~',':','"','~','<','>','?',0xf0,
    0xbb,0xbc,0xbd,0xbe,0xbf,0xc0,0xc1,0xc2,0xc3,0xc4,0xc5,0xc6,
    0x00,0xf1,0x00,0xd2,0xc7,0xc9,0xd3,0xcf,0xd1,0xcd,0xcd,0xd0,0xc8,0xf2,
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
    0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,
};

/* When numlock is on and the raw key value is within the keypad
    value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_numlock_on_map[] =
{
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
};

/* When numlock is off and the raw key value is within the keypad value
    range, this array will be used to decode the raw key value. */
static UCHAR keyboard_layout_raw_to_numlock_off_map[] =
{
    '/','*','-','+',
    0x0d,0xcf,0xd0,0xd1,0xcb,'5',0xcd,0xc7,0xc8,0xc9,0xd2,0xd3,'\\',0x00,0x
    00,'=',
};

/* Specify the keyboard layout for USBX usage. */
static UX_HOST_CLASS_HID_KEYBOARD_LAYOUT keyboard_layout =
{
    keyboard_layout_raw_to_shifted_map,
    keyboard_layout_raw_to_unshifted_map,
    keyboard_layout_raw_to_numlock_on_map,
    keyboard_layout_raw_to_numlock_off_map,
    /* The maximum raw key value. Values larger than this are discarded. */
    UX_HID_KEYBOARD_KEYS_UPPER_RANGE,
    /* The raw key value for the letter 'a'. */
    UX_HID_KEYBOARD_KEY_LETTER_A,
    /* The raw key value for the letter 'z'. */
    UX_HID_KEYBOARD_KEY_LETTER_Z,
    /* The lower range raw key value for keypad keys - inclusive. */
    UX_HID_KEYBOARD_KEYS_KEYPAD_LOWER_RANGE,
    /* The upper range raw key value for keypad keys. */
    UX_HID_KEYBOARD_KEYS_KEYPAD_UPPER_RANGE
};

/* Call the IOCTL function to change the keyboard layout. */
status = ux_host_class_hid_keyboard_ioctl(keyboard,
    UX_HID_KEYBOARD_IOCTL_SET_LAYOUT, (VOID *)&keyboard_layout);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="example--disable-keyboard-key-decode"></a>Exemplo – desativar a chave do teclado descodificar

```c
UINT status;

/* The following example illustrates IOCTL function of Disable key decode from keyboard layout. */
status = ux_host_class_hid_keyboard_ioctl(keyboard,
    UX_HID_KEYBOARD_IOCTL_DISABLE_KEYS_DECODE, UX_NULL);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_remote_control_usage_get"></a>ux_host_class_hid_remote_control_usage_get

Obtenha o uso do controlo remoto

### <a name="prototype"></a>Prototype

```c
UINT ux_host_class_hid_remote_control_usage_get(
    UX_HOST_CLASS_HID_REMOTE_CONTROL *remote_control_instance,
    LONG *usage, 
    ULONG *value);
```

### <a name="description"></a>Descrição

Esta função é utilizada para obter os controlos remotos.

### <a name="parameters"></a>Parâmetros

- **remote_control_instance** Ponteiro para a instância de controlo remoto HID.
- **uso** Ponteiro para o uso.
- **valor** Ponteiro para o valor para a utilização.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) A transferência de dados foi concluída.
- **UX_ERROR** (0xff) Nada a relatar.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) caso de classe HID não existe.

A lista de todas as utilizações possíveis é demasiado longa para caber neste manual do utilizador. Para uma descrição completa, o ux_host_class_hid.h tem todo o conjunto de valores possíveis.

### <a name="example"></a>Exemplo

```c
/* Read usages and values as the user changes the vol/bass/treble buttons on the speaker */

while (remote_control != UX_NULL)
{
    status = ux_host_class_hid_remote_control_usage_get(remote_control, &usage, &value);
    if (status == UX_SUCCESS)
    {
        /* We have something coming from the HID remote control,
        we filter the usage here and only allow the
        volume usage which can be VOLUME, VOLUME_INCREMENT or VOLUME_DECREMENT */
        switch(usage)
        {
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME :
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME_INCREMENT :
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME_DECREMENT :

            if (value<0x80)
            {
                if (current_volume + audio_control.ux_host_class_audio_control_res < 0xffff)
                    current_volume = current_volume + audio_control.ux_host_class_audio_control_res;
                } else {
                if (current_volume > audio_control.ux_host_class_audio_control_res)
                    current_volume = current_volumeaudio_control.ux_host_class_audio_control_res;
            }

            audio_control.ux_host_class_audio_control_channel = 1;
            audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
            audio_control.ux_host_class_audio_control_cur = current_volume;
            status = ux_host_class_audio_control_value_set(audio, &audio_control);
            audio_control.ux_host_class_audio_control_channel = 2;
            audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
            audio_control.ux_host_class_audio_control_cur = current_volume;
            status = ux_host_class_audio_control_value_set(audio, &audio_control);
            break;

        }
    }
    tx_thread_sleep(10);

}
```

### <a name="ux_host_class_cdc_acm_read"></a>ux_host_class_cdc_acm_read

Leia a partir da interface cdc_acm.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_class_cdc_acm_read(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length);
```

### <a name="description"></a>Descrição

Esta função lê-se a partir da interface cdc_acm. A chamada está a bloquear e só regressa quando há um erro ou quando a transferência está completa.

### <a name="parameters"></a>Parâmetros

- **cdc_acm** Apontando para a cdc_acm exemplo de classe.
- **data_pointer** Ponteiro para o endereço tampão da carga útil dos dados.
- **requested_length** Comprimento a ser recebido.
- **atual_length** Comprimento realmente recebido.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) A transferência de dados foi concluída.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) A cdc_acm instância é inválida.
- **UX_TRANSFER_TIMEOUT** (0x5c) Transferir tempo, leitura incompleta.

### <a name="example"></a>Exemplo

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_read(cdc_acm, data_pointer,
    requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_write"></a>ux_host_class_cdc_acm_write

Escreva para a interface cdc_acm

### <a name="prototype"></a>Prototype

```c
UINT ux_host_class_cdc_acm_write(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UCHAR *data_pointer, 
    ULONG requested_length, 
    ULONG *actual_length);
```

### <a name="description"></a>Descrição

Esta função escreve para a interface cdc_acm. A chamada está a bloquear e só regressa quando há um erro ou quando a transferência está completa.

### <a name="parameters"></a>Parâmetros

- **cdc_acm** Apontando para a cdc_acm exemplo de classe.
- **data_pointer** Ponteiro para o endereço tampão da carga útil dos dados.
- **requested_length** Comprimento a ser enviado.
- **atual_length** Comprimento realmente enviado.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) A transferência de dados foi concluída.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) A cdc_acm instância é inválida.
- **UX_TRANSFER_TIMEOUT** (0x5c) Transferir tempo, escrevendo incompleto.

### <a name="example"></a>Exemplo

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_write(cdc_acm, data_pointer,
    requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_ioctl"></a>ux_host_class_cdc_acm_ioctl

Execute uma função DE IOCTL para a interface cdc_acm.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_class_cdc_acm_ioctl(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function, 
    VOID *parameter);
```

### <a name="description"></a>Descrição

Esta função desempenha uma função de coitl específica para a interface cdc_acm. A chamada está a bloquear e só retorna quando há um erro ou quando o comando está concluído.

### <a name="parameters"></a>Parâmetros

- **cdc_acm** Apontando para a cdc_acm exemplo de classe.
- **ioctl_function** função de localização. Consulte a tabela abaixo para uma das funções de coitl permitidas.
- **parâmetro** Ponteiro para um parâmetro específico do ioctl

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) A transferência de dados foi concluída.
- **UX_MEMORY_INSUFFICIENT** (0x12) Não tem memória suficiente.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) caso CDC-ACM está num estado inválido.
- **UX_FUNCTION_NOT_SUPPORTED** (0x54) Função IOCTL desconhecida.

### <a name="ioctl-functions"></a>Funções ioctl:

- UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING
- UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING
- UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE
- UX_HOST_CLASS_CDC_ACM_IOCTL_SEND_BREAK
- UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_IN_PIPE
- UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_OUT_PIPE
- UX_HOST_CLASS_CDC_ACM_IOCTL_NOTIFICATION_CALLBACK
- UX_HOST_CLASS_CDC_ACM_IOCTL_GET_DEVICE_STATUS

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_ioctl(cdc_acm,
    UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING, (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_reception_start"></a>ux_host_class_cdc_acm_reception_start

Inicia a receção de dados de fundo do dispositivo.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_class_cdc_acm_reception_start(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UX_HOST_CLASS_CDC_ACM_RECEPTION *cdc_acm_reception);
```

### <a name="description"></a>Descrição

Esta função faz com que o USBX leia continuamente os dados do dispositivo em segundo plano. Após a conclusão de cada transação, é invocada a chamada especificada em **cdc_acm_reception** para que a aplicação possa efetuar o tratamento posterior dos dados da transação.

> [!NOTE]
> **ux_host_class_cdc_acm_read** não devem ser utilizados enquanto estiver a ser utilizada a receção de fundo.

### <a name="parameters"></a>Parâmetros

- **cdc_acm** Apontando para a cdc_acm exemplo de classe.
- **cdc_acm_reception** Ponteiro para parâmetro que contém valores que definem o comportamento da receção de fundo. O layout deste parâmetro segue:

```c
typedef struct UX_HOST_CLASS_CDC_ACM_RECEPTION_STRUCT
{
    ULONG ux_host_class_cdc_acm_reception_state;
    ULONG ux_host_class_cdc_acm_reception_block_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_buffer;
    ULONG ux_host_class_cdc_acm_reception_data_buffer_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_head;
    UCHAR *ux_host_class_cdc_acm_reception_data_tail;
    VOID (*ux_host_class_cdc_acm_reception_callback)(struct UX_HOST_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *reception_buffer, ULONG reception_size);
} UX_HOST_CLASS_CDC_ACM_RECEPTION;
```

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) A receção de fundo começou com sucesso.
- **UX_HOST_CLASS_INSTANCE _UNKNOWN** (0x5b) Instância de classe errada.

```c
UINT status;
UX_HOST_CLASS_CDC_ACM_RECEPTION cdc_acm_reception;

/* Setup the background reception parameter. */

/* Set the desired max read size for each transaction.
    For example, if this value is 64, then the maximum amount of
    data received from the device in a single transaction is 64.
    If the amount of data received from the device is less than this value,
    the callback will still be invoked with the actual amount of data received. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_block_size = block_size;

/* Set the buffer where the data from the device is read to. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_data_buffer = cdc_acm_reception_buffer;

/* Set the size of the data reception buffer.
    Note that this should be at least as large as ux_host_class_cdc_acm_reception_block_size. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_data_buffer_size = cdc_acm_reception_buffer_size;

/* Set the callback that is to be invoked upon each reception transfer completion. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_callback = reception_callback;

/* Start background reception using the values we defined in the reception parameter. */
status = ux_host_class_cdc_acm_reception_start(cdc_acm_host_data, &cdc_acm_reception);

/* If status equals UX_SUCCESS, background reception has successfully started. */
```

## <a name="ux_host_class_cdc_acm_reception_stop"></a>ux_host_class_cdc_acm_reception_stop

Para a receção de fundo dos pacotes.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_class_cdc_acm_reception_stop(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UX_HOST_CLASS_CDC_ACM_RECEPTION *cdc_acm_reception);
```

### <a name="description"></a>Descrição

Esta função faz com que o USBX pare a receção de fundo previamente iniciada por **ux_host_class_cdc_acm_reception_start**.

### <a name="parameters"></a>Parâmetros

- **cdc_acm** Apontando para a cdc_acm exemplo de classe.
- **cdc_acm_reception** Ponteiro para o mesmo parâmetro que foi usado para iniciar a receção de fundo. O layout deste parâmetro segue:

```c
typedef struct UX_HOST_CLASS_CDC_ACM_RECEPTION_STRUCT
{
    ULONG ux_host_class_cdc_acm_reception_state;
    ULONG ux_host_class_cdc_acm_reception_block_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_buffer;
    ULONG ux_host_class_cdc_acm_reception_data_buffer_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_head;
    UCHAR *ux_host_class_cdc_acm_reception_data_tail;
    VOID (*ux_host_class_cdc_acm_reception_callback)(
            struct UX_HOST_CLASS_CDC_ACM_STRUCT *cdc_acm, UINT status,
            UCHAR *reception_buffer, ULONG reception_size);
} UX_HOST_CLASS_CDC_ACM_RECEPTION;
```

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) A receção de fundo parou com sucesso.
- **UX_HOST_CLASS_INSTANCE _UNKNOWN** (0x5b) Instância de classe errada.

```c
UINT status;
UX_HOST_CLASS_CDC_ACM_RECEPTION cdc_acm_reception;

/* Stop background reception. The reception parameter should be the same
    that was passed to ux_host_class_cdc_acm_reception_start. */
status = ux_host_class_cdc_acm_reception_stop(cdc_acm, &cdc_acm_reception);

/* If status equals UX_SUCCESS, background reception has successfully stopped. */
```
