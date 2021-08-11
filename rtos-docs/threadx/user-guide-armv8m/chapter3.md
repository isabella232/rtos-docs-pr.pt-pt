---
title: Capítulo 3 - ApIs ThreadX para ARMv8-M
description: Neste capítulo é uma descrição dos serviços ThreadX específicos da ARMv8-M.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 99633db55a5d93eb32ce4fb5429f3fe2f9ab5137cffc30b27982f702cece1ca5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791504"
---
# <a name="chapter-3--threadx-apis-for-armv8-m"></a>ApIs do Capítulo 3 ThreadX para ARMv8-M

Este capítulo contém uma descrição dos serviços ThreadX específicos armv8-M por ordem alfabética. Os seus nomes são concebidos para que todos os serviços semelhantes sejam agrupados. Na secção "Valores de Retorno" nas seguintes descrições, os valores em **BOLD** não são afetados pela **TX_DISABLE_ERROR_CHECKING** definem utilizados para desativar a verificação de erros da API; enquanto os valores mostrados em não-arrojado são completamente desativados.

- [tx_thread_secure_stack_allocate](#tx_thread_secure_stack_allocate) Aloque uma pilha de fios na memória segura.
- [tx_thread_secure_stack_free](#tx_thread_secure_stack_free) Pilha de fio livre na memória segura

## <a name="tx_thread_secure_stack_allocate"></a>tx_thread_secure_stack_allocate

Aloque uma pilha de fios na memória segura.

### <a name="prototype"></a>Prototype

```c
UINT tx_thread_secure_stack_allocate(
    TX_THREAD *thread_ptr, 
    ULONG stack_size);
```

### <a name="description"></a>Description

Este serviço aloca uma pilha de tamanho stack_size bytes em memória segura. Esta função deve ser chamada para cada fio que chama funções seguras.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **thread_ptr** Ponteiro para fio previamente criado.

- **stack_size** Tamanho da pilha segura.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Pedido de sucesso.

- **TX_SIZE_ERROR** (0x05) Stack tamanho fora do alcance.

- **TX_THREAD_ERROR** (0x0E) Ponteiro de rosca inválido.

- **TX_NO_MEMORY** (0x10) Incapaz de alocar a memória.

- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

- **TX_FEATURE_NOT_ENABLED** (0xFF) O sistema foi compilado para funcionar em modo de segurança.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Create thread.  */
tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0, pointer, DEMO_STACK_SIZE, 1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

/* Allocate secure stack so this thread can call secure functions.  */
status = tx_thread_secure_stack_allocate(&thread_0, 256);

/* If status is TX_SUCCESS the request was successful.  */
```

### <a name="see-also"></a>Consulte também

tx_thread_secure_stack_free

##  <a name="tx_thread_secure_stack_free"></a>tx_thread_secure_stack_free

Liberte uma pilha de fios em memória segura. 

### <a name="prototype"></a>Prototype

```c
UINT tx_thread_secure_stack_free(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Description

Este serviço liberta a pilha segura de um fio em memória segura. Esta função deve ser chamada se um fio tiver uma pilha segura e quando o fio já não precisar de chamar funções seguras ou se o fio for eliminado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **thread_ptr** Ponteiro para fio previamente criado.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Pedido de sucesso.

- **TX_THREAD_ERROR** (0x0E) Ponteiro de rosca inválido.

- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

- **TX_FEATURE_NOT_ENABLED** (0xFF) O sistema foi compilado para funcionar em modo de segurança.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Free thread’s secure stack.  */
status = tx_thread_secure_stack_free(&thread_0);

/* If status is TX_SUCCESS the request was successful.  */

/* Delete thread.  */
tx_thread_delete(&thread_0);
```

## <a name="see-also"></a>Consulte também

tx_thread_secure_stack_allocate
