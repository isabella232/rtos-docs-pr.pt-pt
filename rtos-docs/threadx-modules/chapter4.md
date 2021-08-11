---
title: Capítulo 4 - APIs do módulo
author: philmea
ms.author: philmea
description: Este artigo é um resumo das APIs adicionais disponíveis para um módulo.
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1c7590d0ccddc606a6cacdfeb3b3a99631e125554b524c4ce65c8154e65a20ee
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799137"
---
# <a name="chapter-4---module-apis"></a>Capítulo 4 - APIs do módulo

## <a name="summary-of-module-apis"></a>Resumo das APIs do Módulo

Existem várias funções API adicionais disponíveis para um módulo, da seguinte forma:

- ***txm_module_application_request** _ - pedido específico de _Application ao código residente*
- ***txm_module_object_allocate** _ - _Allocate memória fora do módulo para objeto*
- ***txm_module_object_deallocate** _ - _Deallocate memória de objeto previamente atribuída*
- ***txm_module_object_pointer_get** _ - _Find objeto do sistema e recuperar o ponteiro do objeto*
- ***txm_module_object_pointer_get_extended** _ - _Find objeto do sistema e recuperar o ponteiro do objeto, a segurança do comprimento do nome*

## <a name="return-values"></a>Valores de retorno

Códigos de erro adicionais são devolvidos para algumas APOs RTOS Azure. Estes códigos de erro adicionais são definidos da seguinte forma:

- **TXM_MODULE_INVALID_PROPERTIES** (0xF3): Indica que o módulo não tem as propriedades corretas para fazer uma chamada API. Por exemplo, chamar apis de rastreio no modo de utilizador.
- **TXM_MODULE_INVALID_MEMORY** (0xF4): Indica que a memória fornecida pelo módulo é inválida ou está num local inválido. Por exemplo, nos módulos protegidos pela memória, os blocos de controlo de objetos não podem ser localizados na memória que o módulo possa aceder.
- **TXM_MODULE_INVALID_CALLBACK** (0xF5): A chamada especificada na API está fora do alcance do código do módulo e, portanto, é inválida.

---

## <a name="txm_module_application_request"></a>txm_module_application_request

Pedido específico de inscrição para código residente.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_application_request(
    ULONG request, 
    ULONG param_1,
    ULONG param_2,
    ULONG param_3);
```

### <a name="description"></a>Description

Este serviço faz o pedido especificado à parte residente do pedido. Presume-se que a estrutura do pedido é preparada antes da chamada. O processamento efetivo do pedido ocorre no código residente na função ***_txm_module_manager_application_request***. Por predefinição, esta função é deixada vazia e foi concebida para que o desenvolvedor de aplicações residentes se modifique.

### <a name="input-parameters"></a>Parâmetros de entrada

- **pedido** ID do pedido (candidatura definida)
- **param_1** Primeiro parâmetro
- **param_2** Segundo parâmetro
- **param_3** Terceiro parâmetro

### <a name="return-values"></a>Valores de retorno

- **TX_SUCCESS** (0x00) Pedido de sucesso.
- **TX_NOT_AVAILABLE** (0x1D) Pedido não suportado pelo código residente.

### <a name="allowed-from"></a>Permitido a partir de

Fios de módulos

### <a name="example"></a>Exemplo

```c
/* Call application resident code with ID=77 and the
   parameters set to 1, 2, 3. */
status = txm_module_application_request(77, 1, 2, 3);

/* If status is TX_SUCCESS the request was successful. */
```

---

## <a name="txm_module_object_allocate"></a>txm_module_object_allocate

Aloque a memória na piscina de objetos (criada pela aplicação residente) para um bloco de controlo de objetos de módulo.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_object_allocate(
   VOID **object_ptr, 
   ULONG object_size);
```

### <a name="description"></a>Description

Este serviço atribui a memória a um objeto de módulo da memória fora do módulo, o que ajuda a prevenir a corrupção do bloco de controlo de objetos pelo código do módulo. Nos sistemas protegidos pela memória, todos os blocos de controlo de objetos devem ser atribuídos com esta API antes de poderem ser criados.

### <a name="input-parameters"></a>Parâmetros de entrada

- **object_ptr** Destino do ponteiro de objetos na atribuição bem sucedida.
- **object_size** Tamanho em bytes do objeto a atribuir.

### <a name="return-values"></a>Valores de retorno

- **TX_SUCCESS** (0x00) Alocado objeto bem sucedido.
- **TX_NO_MEMORY** (0x10) Não há memória suficiente.
- **TX_NOT_AVAILABLE** (0x1D) Gestor de módulos não criou um pool de objetos para alocar a partir de

### <a name="allowed-from"></a>Permitido a partir de

Fios de módulos

### <a name="example"></a>Exemplo

```c
TX_QUEUE *queue_pointer;

/* Allocate a control block for a module message queue. */
status = txm_module_object_allocate(&queue_pointer, sizeof(TX_QUEUE));

/* If status is TX_SUCCESS the queue_pointer points to
   memory allocated outside of the module and can be supplied
   to tx_queue_create to create a queue for the module. */
```

### <a name="see-also"></a>Veja também

- txm_module_object_deallocate
- txm_module_object_pointer_get

---

## <a name="txm_module_object_deallocate"></a>txm_module_object_deallocate

Deallocate memória de objeto previamente atribuída

### <a name="prototype"></a>Prototype

```c
UINT txm_module_object_deallocate(VOID *object_ptr);
```

### <a name="description"></a>Description

***Este serviço foi depreciado porque já não é necessário.***

A memória que foi previamente atribuída através ***de txm_module_object_allocate**_ é transatada no* serviço _ _tx_ \_ _delete***.

### <a name="input-parameters"></a>Parâmetros de entrada

- **object_ptr** Ponteiro de objeto para negociar.

### <a name="return-values"></a>Valores de retorno

- **TX_SUCCESS** (0x00) Alocado objeto bem sucedido.

### <a name="allowed-from"></a>Permitido a partir de

Fios de módulos

### <a name="example"></a>Exemplo

```c
TX_QUEUE *queue_pointer;

/* Deallocate control block for a module message queue. */
status = txm_module_object_deallocate(queue_pointer);

/* If status is TX_SUCCESS the object memory associated
   with queue_pointer is deallocated. */
```

### <a name="see-also"></a>Veja também

- txm_module_object_allocate
- txm_module_object_pointer_get

---

## <a name="txm_module_object_pointer_get"></a>txm_module_object_pointer_get

Encontre objeto do sistema e recupere o ponteiro do objeto

### <a name="prototype"></a>Prototype

```c
UINT txm_module_object_pointer_get(
   UINT object_type, CHAR *name, 
   VOID **object_ptr);
```

### <a name="description"></a>Description

Este serviço recupera o ponteiro de objetos de um tipo específico com um nome específico. Se o objeto não for encontrado, é devolvido um erro. Caso contrário, se o objeto for encontrado, o endereço desse objeto é colocado em "object_ptr". Este ponteiro pode então ser utilizado para fazer chamadas de serviço do sistema, para interagir com o código residente e/ou outros módulos carregados no sistema.

### <a name="input-parameters"></a>Parâmetros de entrada

- **object_type** Tipo de objeto ThreadX solicitado. Os tipos válidos são os seguintes:
  - TXM_BLOCK_POOL_OBJECT
  - TXM_BYTE_POOL_OBJECT
  - TXM_EVENT_FLAGS_OBJECT
  - TXM_MUTEX_OBJECT
  - TXM_QUEUE_OBJECT
  - TXM_SEMAPHORE_OBJECT
  - TXM_THREAD_OBJECT
  - TXM_TIMER_OBJECT
  - TXM_IP_OBJECT
  - TXM_PACKET_POOL_OBJECT
  - TXM_UDP_SOCKET_OBJECT
  - TXM_TCP_SOCKET_OBJECT
- **nome** Nome do objeto específico da aplicação, tal como definido quando o objeto foi criado.
- **object_ptr** Destino para ponteiro de objetos.

### <a name="return-values"></a>Valores de retorno

- **TX_SUCCESS** (0x00) Objeto bem sucedido obter.
- **TX_OPTION_ERROR** (0x08) Tipo de objeto inválido.
- **TX_PTR_ERROR** (0x03) Destino inválido.
- **TX_SIZE_ERROR** (0x05) Tamanho inválido.
- **TX_NO_INSTANCE** (0x0D) Objeto não encontrado.

### <a name="allowed-from"></a>Permitido a partir de

Fios de módulos

### <a name="example"></a>Exemplo

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
status = txm_module_object_pointer_get(TXM_QUEUE_OBJECT,
         "fft_queue", &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a>Veja também

- txm_module_manager_object_pointer_get_extended

---

## <a name="txm_module_object_pointer_get_extended"></a>txm_module_object_pointer_get_extended

Encontre objeto do sistema e recupere o ponteiro do objeto

### <a name="prototype"></a>Prototype

```c
UINT txm_module_object_pointer_get_extended(UINT object_type,
                                            CHAR *name,
                                            UINT name_length,
                                            VOID **object_ptr);
```

### <a name="description"></a>Description

Este serviço recupera o ponteiro de objetos de um tipo específico com um nome específico. Se o objeto não for encontrado, é devolvido um erro. Caso contrário, se o objeto for encontrado, o endereço desse objeto é colocado em "object_ptr". Este ponteiro pode então ser utilizado para fazer chamadas de serviço do sistema, para interagir com o código residente e/ou outros módulos carregados no sistema.

### <a name="input-parameters"></a>Parâmetros de entrada

- **object_type** Tipo de objeto ThreadX solicitado. Os tipos válidos são os seguintes:
  - TXM_BLOCK_POOL_OBJECT
  - TXM_BYTE_POOL_OBJECT
  - TXM_EVENT_FLAGS_OBJECT
  - TXM_MUTEX_OBJECT
  - TXM_QUEUE_OBJECT
  - TXM_SEMAPHORE_OBJECT
  - TXM_THREAD_OBJECT
  - TXM_TIMER_OBJECT
  - TXM_IP_OBJECT
  - TXM_PACKET_POOL_OBJECT
  - TXM_UDP_SOCKET_OBJECT
  - TXM_TCP_SOCKET_OBJECT
- **nome** Nome do objeto específico da aplicação, tal como definido quando o objeto foi criado.
- **name_length** Comprimento do nome.
- **object_ptr** Destino para ponteiro de objetos.

### <a name="return-values"></a>Valores de retorno

- **TX_SUCCESS** (0x00) Objeto bem sucedido obter.
- **TX_OPTION_ERROR** (0x08) Tipo de objeto inválido.
- **TX_PTR_ERROR** (0x03) Destino inválido.
- **TX_SIZE_ERROR** (0x05) Tamanho inválido.
- **TX_NO_INSTANCE** (0x0D) Objeto não encontrado.

### <a name="allowed-from"></a>Permitido a partir de

Fios de módulos

### <a name="example"></a>Exemplo

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
   status = txm_module_object_pointer_get_extended(TXM_QUEUE_OBJECT,
            "fft_queue", 9, &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a>Veja também

- txm_module_manager_object_pointer_get
