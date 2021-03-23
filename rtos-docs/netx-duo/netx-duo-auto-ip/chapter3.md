---
title: Capítulo 3 - Descrição dos serviços Azure RTOS NetX Duo AutoIP
description: Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX Duo AutoIP (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0935295ef9f7255c0851e1f64013884dce4c52f1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826167"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-autoip-services"></a>Capítulo 3 - Descrição dos serviços Azure RTOS NetX Duo AutoIP

Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX Duo AutoIP (listados abaixo) por ordem alfabética.

Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

- **nx_auto_ip_create**: *Criar instância autoIP*
- **nx_auto_ip_delete**: *Eliminar instância autoIP*
- **nx_auto_ip_get_address**: *Obtenha o endereço autoIP atual*
- **nx_auto_ip_set_interface**: *Definir interface IP que necessite de um endereço AutoIP*
- **nx_auto_ip_start**: *Iniciar o processamento do AutoIP*
- **nx_auto_ip_stop**: *Parar o processamento de AutoIP*

## <a name="nx_auto_ip_create"></a>nx_auto_ip_create

Criar exemplo de AutoIP

### <a name="prototype"></a>Prototype

```c
UINT nx_auto_ip_create(NX_AUTO_IP *auto_ip_ptr, CHAR *name,
                    NX_IP *ip_ptr, VOID *stack_ptr, ULONG stack_size,
                    UINT priority);
```

### <a name="description"></a>Descrição

Este serviço cria uma instância AutoIP na instância IP especificada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **auto_ip_ptr**: Ponteiro para o bloco de controlo AutoIP.
- **nome**: Nome da instância AutoIP.
- **ip_ptr**: Indicação para a instância IP.
- **stack_ptr**: Ponteiro para a área da pilha de fio AutoIP.
- **stack_size**: Tamanho da área da pilha de fio AutoIP.
- **prioridade**: Prioridade da linha AutoIP.

> [!NOTE]
> Se o DHCP for utilizado, o fio DHCP deve ter uma prioridade maior do que o fio de instância IP e o fio AutoIP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Criação autoIP bem sucedida.
- **NX_AUTO_IP_ERROR**: (0xA00) O AutoIP cria erro.
- NX_PTR_ERROR: (0x16) Invalid AutoIP, ip_ptr ou ponteiro de pilha.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Create the AutoIP instance "auto_ip_0" on "ip_0". */
status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);

/* If status is NX_SUCCESS an AutoIP instance was successfully created. */
```

### <a name="see-also"></a>Consulte também

nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start nx_auto_ip_stop

## <a name="nx_auto_ip_delete"></a>nx_auto_ip_delete

Apagar a instância AutoIP

### <a name="prototype"></a>Prototype

```c
UINT nx_auto_ip_delete(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a>Descrição

Este serviço elimina uma instância AutoIP previamente criada na instância IP especificada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **auto_ip_ptr**: Ponteiro para o bloco de controlo AutoIP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Eliminar autoIP com sucesso.
- **NX_AUTO_IP_ERROR**: (0xA00) Erro de eliminação automática.
- NX_PTR_ERROR: (0x16) Ponteiro AutoIP inválido.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Delete the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_delete(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully deleted. */
```

### <a name="see-also"></a>Consulte também

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start nx_auto_ip_stop

## <a name="nx_auto_ip_get_address"></a>nx_auto_ip_get_address

Obtenha o endereço AutoIP atual

### <a name="prototype"></a>Prototype

```c
UINT nx_auto_ip_get_address(NX_AUTO_IP *auto_ip_ptr,
                            ULONG *local_ip_address);
```

### <a name="description"></a>Descrição

Este serviço recupera o endereço AutoIP atualmente configurado. Se não houver um, é devolvido um endereço IP de 0.0.0.0.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **auto_ip_ptr**: Ponteiro para o bloco de controlo AutoIP.
- **local_ip_address**: Destino para endereço IP de devolução.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) O endereço AutoIP bem sucedido obtém.
- **NX_AUTO_IP_NO_LOCAL:**(0xA01) Sem endereço AutoIP válido.
- NX_PTR_ERROR: (0x16) Ponteiro AutoIP inválido.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Temporizadores, Fios, ISRs

### <a name="example"></a>Exemplo

```c
ULONG local_address;

/* Get the AutoIP address resolved by the instance "auto_ip_0." */
status = nx_auto_ip_get_address(&auto_ip_0, &local_address);

/* If status is NX_SUCCESS the local IP address is in "local_address." */
```

### <a name="see-also"></a>Consulte também

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start nx_auto_ip_stop

## <a name="nx_auto_ip_set_interface"></a>nx_auto_ip_set_interface

Definir interface de rede para AutoIP

### <a name="prototype"></a>Prototype

```c
UINT nx_auto_ip_set_interface(NX_AUTO_IP *auto_ip_ptr,
                            UINT interface_index);
```

### <a name="description"></a>Descrição

Este serviço define o índice para a interface de rede AutoIP irá sondar para um endereço IP de rede. O padrão é zero (a interface de rede primária). Apenas aplicável a dispositivos multihomed.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **auto_ip_ptr**: Ponteiro para o bloco de controlo AutoIP.
- **interface_index**: Interface para sondar o endereço IP

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) conjunto de interface autoIP bem sucedido
- **NX_AUTO_IP_BAD_INTERFACE_INDEX:**(0xA02) Interface de rede inválida NX_PTR_ERROR (0x16) Ponteiro AutoIP inválido.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Temporizadores, Fios, ISRs

### <a name="example"></a>Exemplo

```c
ULONG interface_index;

/* Set the network interface on which AutoIP probes for host address. */
status = nx_auto_ip_set_interface(&auto_ip_0, interface_index);

/* If status is NX_SUCCESS the network interface is valid and set in the AutoIP control block *auto_ip_0*. */
```

### <a name="see-also"></a>Consulte também

nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start nx_auto_ip_stop nx_auto_ip_stop

## <a name="nx_auto_ip_start"></a>nx_auto_ip_start

Iniciar o processamento de AutoIP

### <a name="prototype"></a>Prototype

```c
UINT nx_auto_ip_start(NX_AUTO_IP *auto_ip_ptr,
                    ULONG starting_local_address);
```

### <a name="description"></a>Descrição

Este serviço inicia o protocolo AutoIP numa instância AutoIP previamente criada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **auto_ip_ptr**: Ponteiro para o bloco de controlo AutoIP.
- **starting_local_address**: Endereço de partida autoIP opcional. Um valor de IP_ADDRESS (0,0,0,0) especifica que deve ser derivado um endereço AutoIP aleatório. Caso contrário, se for especificado um endereço AutoIP válido, o NetX AutoIP tenta atribuir esse endereço.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Arranque autoIP bem sucedido.
- **NX_AUTO_IP_ERROR**: (0xA00) Erro de arranque autoIP.
- NX_PTR_ERROR: (0x16) Ponteiro AutoIP inválido.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Start the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_start(&auto_ip_0, IP_ADDRESS(0,0,0,0));

/* If status is NX_SUCCESS an AutoIP instance was successfully started. */
```

### <a name="see-also"></a>Consulte também

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address nx_auto_ip_stop

## <a name="nx_auto_ip_stop"></a>nx_auto_ip_stop

Parar o processamento de AutoIP

### <a name="prototype"></a>Prototype

```c
UINT nx_auto_ip_stop(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a>Descrição

Este serviço para o protocolo AutoIP numa instância autoIP previamente criada e iniciada. Este serviço é normalmente utilizado quando o endereço IP é alterado via DHCP ou manualmente para um endereço não AutoIP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **auto_ip_ptr**: Ponteiro para o bloco de controlo AutoIP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:**(0x00) Paragem autoIP bem sucedida.
- **NX_AUTO_IP_ERROR**: (0xA00) Erro de paragem autoIP.
- NX_PTR_ERROR: (0x16) Ponteiro AutoIP inválido.
- NX_CALLER_ERROR: (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Stop the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_stop(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully stopped. */
```

### <a name="see-also"></a>Consulte também

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address nx_auto_ip_start