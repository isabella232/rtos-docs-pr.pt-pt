---
title: Capítulo 5 - ApIs gestor de módulos
author: philmea
description: Este artigo é um resumo das APIs do Gestor de Módulos disponíveis para a parte residente da aplicação.
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e8e4da0f9591fd0b5d6249292f00266d96ccb67923c42632a4cfd8c39fa1f129
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799120"
---
# <a name="chapter-5---module-manager-apis"></a>Capítulo 5 - ApIs gestor de módulos

## <a name="summary-of-module-manager-apis"></a>Resumo das APIs do Gestor de Módulos

Existem várias APIs adicionais disponíveis para a parte residente da aplicação, da seguinte forma.

- ***txm_module_manager_external_memory_enable** _ - _Enable o acesso do módulo a um espaço de memória partilhada*
- ***txm_module_manager_file_load** _ - _Load módulo do ficheiro via FileX*
- ***txm_module_manager_in_place_load** _ - _Load dados do módulo, execute no lugar*
- ***txm_module_manager_initialize** _ - _Initialize o gestor do módulo*
- ***txm_module_manager_mm_initialize** _ - _Initialize o hardware de gestão da memória*
- ***txm_module_manager_maximum_module_priority_set** _ - _set a prioridade máxima de fio permitida num módulo*
- ***txm_module_manager_memory_fault_notify** _ - _Register uma chamada de chamada de aplicação na falha de memória*
- ***txm_module_manager_memory_load** _ - _Load o módulo da memória*
- ***txm_module_manager_object_pool_create** _ - _Create uma piscina de objetos para módulos*
- ***txm_module_manager_properties_get** _ - propriedades do módulo _Get*
- ***txm_module_manager_start** _ - execução _Start do módulo especificado*
- ***txm_module_manager_stop** _ - execução _Stop do módulo especificado*
- ***txm_module_manager_unload** _ - _Unload o módulo*

---

## <a name="txm_module_manager_external_memory_enable"></a>txm_module_manager_external_memory_enable

Ativar o módulo para aceder a um espaço de memória partilhada.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_external_memory_enable(
     TXM_MODULE_INSTANCE *module_instance,
     VOID *start_address,
     ULONG length,
     UINT attributes);
```

### <a name="description"></a>Description

Este serviço cria uma entrada na tabela de hardware de gestão de memória para uma região de memória partilhada a que o módulo pode aceder.

### <a name="input-parameters"></a>Parâmetros de entrada

- **module_instance** Ponteiro para a instância do módulo.
- **start_address** Endereço inicial da região de memória partilhada.
- **comprimento** Comprimento da região da memória partilhada.
- **atributos** Atributos da região da memória (cache, ler, escrever, etc.). Os atributos são específicos da porta; ver [apêndice](appendix.md) para o formato de atributos.

### <a name="return-values"></a>Valores de retorno

- **TX_SUCCESS** (0x00) A entrada de memória criada com sucesso.
- **TX_NOT_AVAILABLE** (0x1D) Gestor não inicializado ou funcionalidade não disponível.
- **TX_PTR_ERROR** (0x03) Instância do módulo inválido.
- **TX_START_ERROR** módulo (0x10) não em estado carregado.
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Alinhamento de endereço inicial inválido.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) propriedades incompatíveis.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Create a shared memory space 256 bytes long at address 0x64005000
   with read & write, no execute, outer & inner write back cache
   attributes. Note that these attributes are port-specific. */
txm_module_manager_external_memory_enable(&my_module, (VOID*)0x64005000, 256, 0x3F);
```

---

## <a name="txm_module_manager_file_load"></a>txm_module_manager_file_load

Módulo de carga a partir de ficheiro via FileX.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_file_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```

### <a name="description"></a>Description

Este serviço carrega a imagem binária do módulo contido no ficheiro especificado na área de memória do módulo e prepara-o para a execução. Presume-se que os meios de comunicação fornecidos já estão abertos.

> [!NOTE]
> O sistema FileX é utilizado para carregar o ficheiro. Para permitir o acesso ao FileX, o módulo, biblioteca de módulos, gestor de módulos e a biblioteca ThreadX (com as fontes do Gestor do Módulo) devem ser construídos com **FX_FILEX_PRESENT** definidos nos projetos.

### <a name="input-parameters"></a>Parâmetros de entrada

- **module_instance** Ponteiro para a instância do módulo.
- **module_name** Nome do módulo.
- **media_ptr** Ponteiro para já aberto media FileX.
- **file_name** Nome do ficheiro binário do módulo.

### <a name="return-values"></a>Valores de retorno

- **TX_SUCCESS** (0x00) Carga de módulo de sucesso.
- **TX_CALLER_ERROR** (0x13) Inválido.
- **TX_NOT_AVAILABLE** (0x1D) Manager não inicializou.
- **TX_NO_MEMORY** (0x10) Não há memória suficiente para carregar o módulo.
- **TX_NOT_DONE** (0x20) Os meios de comunicação não abertos, o ficheiro não encontrado ou o ficheiro é inválido.
- **TX_PTR_ERROR** (0x03) Ponteiro do módulo inválido.
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Alinhamento inválido.
- **módulo TXM_MODULE_ALREADY_LOADED** (0xF1) já carregado.
- **| TXM_MODULE_INVALID** (0xF2) Preâmbulo do módulo inválido.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) propriedades incompatíveis.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager. */
status = txm_module_manager_initialize((VOID*)0x64010000,0x10000);

/* Load the module from a binary file. */
status = txm_module_manager_file_load(&my_module, "my module",
                                      &sdio_disk, "demo_thread_module.bin");

/* Start the module. */
status = txm_module_manager_start(&my_module);
```

### <a name="see-also"></a>Veja também

- txm_module_manager_in_place_load
- txm_module_manager_memory_load
- txm_module_manager_unload

---

## <a name="txm_module_manager_in_place_load"></a>txm_module_manager_in_place_load

Carregar apenas os dados do módulo, executar o módulo na localização existente.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_in_place_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a>Description

Este serviço carrega a área de dados do módulo apenas na área de memória do módulo e prepara-a para a execução. A execução do código do módulo será no lugar, ou seja, a partir do endereço compensado especificado pelo preâmbulo do módulo no local fornecido.

### <a name="input-parameters"></a>Parâmetros de entrada

- **module_instance** Ponteiro para a instância do módulo.
- **module_name** Nome do módulo.
- **localização** Ponteiro para a área de código do módulo, preâmbulo primeiro.

### <a name="return-values"></a>Valores de retorno

- **TX_SUCCESS** (0x00) Carga de módulo de sucesso.
- **TX_CALLER_ERROR** (0x13) Inválido.
- **TX_NOT_AVAILABLE** (0x1D) Manager não inicializou.
- **TX_NO_MEMORY** (0x10) Não há memória suficiente para carregar o módulo.
- **TX_PTR_ERROR** (0x03) Ponteiro inválido, instância do módulo ou preâmbulo do módulo.
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Alinhamento inválido.
- **módulo TXM_MODULE_ALREADY_LOADED** (0xF1) já carregado.
- **TXM_MODULE_INVALID** (0xF2) Preâmbulo do módulo inválido.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) propriedades incompatíveis.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Start the module. */
txm_module_manager_start(&my_module);
```

### <a name="see-also"></a>Veja também

- txm_module_manager_file_load
- txm_module_manager_memory_load
- txm_module_manager_unload

---

## <a name="txm_module_manager_initialize"></a>txm_module_manager_initialize

Inicialize o gestor do módulo.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_initialize(
    VOID *module_memory_start,
    ULONG module_memory_size);
```

### <a name="description"></a>Description

Este serviço inicializa os recursos internos do Gestor do Módulo, incluindo a área de memória utilizada para carregar módulos.

### <a name="input-parameters"></a>Parâmetros de entrada

- **module_memory_start** Ponteiro para o início da memória do módulo.
- **module_memory_size** Tamanho em bytes da memória do módulo.

### <a name="return-values"></a>Valores de retorno

- **TX_SUCCESS** (0x00) Inicialização bem sucedida.
- **TX_CALLER_ERROR** (0x13) Inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```c
/* Initialize the module manager with 64KB of RAM starting at
   address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);
```

### <a name="see-also"></a>Veja também

- txm_module_manager_object_pool_create

---

## <a name="txm_module_manager_initialize_mmu"></a>txm_module_manager_initialize_mmu

Inicialize o hardware de gestão da memória.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_initialize_mmu(VOID);
```

### <a name="description"></a>Description

Este serviço inicializa a MMU.

### <a name="input-parameters"></a>Parâmetros de entrada

nenhum

### <a name="return-values"></a>Valores de retorno

- **TX_SUCCESS** (0x00) Inicialização bem sucedida.
- **TX_CALLER_ERROR** (0x13) Inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e Threads

### <a name="example"></a>Exemplo

```c
/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Initialize the MMU. */
txm_module_manager_initialize_mmu();
```

---

## <a name="txm_module_manager_maximum_module_priority_set"></a>txm_module_manager_maximum_module_priority_set

Desaprote a prioridade máxima de rosca permitida num módulo.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_maximum_module_priority_set(
         TXM_MODULE_INSTANCE *module_instance,
         UINT priority);
```

### <a name="description"></a>Description

Este serviço define a prioridade máxima de linha permitida num módulo.

### <a name="input-parameters"></a>Parâmetros de entrada

- **module_instance** Ponteiro para a instância do módulo.
- **prioridade** Prioridade máxima do fio.

### <a name="return-values"></a>Valores de retorno

- **TX_SUCCESS** (0x00) Inicialização bem sucedida.
- **TX_NOT_AVAILABLE** (0x1D) Manager não inicializou.
- **TX_PTR_ERROR** (0x03) Instância do módulo inválido.
- **TX_START_ERROR** módulo (0x10) não em estado carregado.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```c
/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Set the maximum thread priority in my_module to 5. */
txm_module_manager_maximum_module_priority_set(&my_module, 5);
```

---

## <a name="txm_module_manager_memory_fault_notify"></a>txm_module_manager_memory_fault_notify

Registar uma chamada de chamada de aplicação na falha de memória.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_memory_fault_notify(
     VOID (*notify_function)(TX_THREAD *, MODULE_INSTANCE *));
```

### <a name="description"></a>Description

Este serviço regista a função de chamada de chamada de notificação de falha de memória de aplicação especificada com o Gestor do Módulo. Se ocorrer uma falha de memória, esta função é chamada com um ponteiro para o fio ofensivo e a instância do módulo correspondente ao fio ofensivo. O processamento do Gestor do Módulo termina automaticamente o fio ofensivo, mas deixa quaisquer outros fios no módulo intactos. Cabe à aplicação decidir o que fazer com o módulo associado à falha de memória.

Consulte a **estrutura** interna _txm_module_manager_memory_fault_info para obter informações específicas sobre a própria falha de memória.

> [!NOTE]
> A função de chamada de notificação por falha de memória é executada diretamente a partir da exceção da falha de memória, pelo que apenas apis ThreadX permitidos a partir de rotinas de serviço de interrupção podem ser chamados. Assim, para parar e descarregar o módulo ofensivo, a chamada de notificação de aplicação deve enviar um sinal para uma tarefa de aplicação para que o módulo possa ser parado e descarregado.

### <a name="input-parameters"></a>Parâmetros de entrada

- **notify_function** Função ponteiro para a chamada de notificação de falha de memória da aplicação. O fornecimento de um valor NUDO desativa a notificação de falha de memória.

### <a name="return-values"></a>Valores de retorno

- **TX_SUCCESS** (0x00) Registo de função de notificação com sucesso.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```c
/* Register a memory fault callback. */
txm_module_manager_memory_fault_notify(my_memory_fault_handler);
```

---

## <a name="txm_module_manager_memory_load"></a>txm_module_manager_memory_load

Módulo de carga da memória.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_memory_load (
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a>Description

Este serviço carrega o código e a área de dados do módulo na área de memória do módulo configurada por ***txm_module_manager_initialize*** e prepara-o para a execução.

### <a name="input-parameters"></a>Parâmetros de entrada

- **module_instance** Ponteiro para a instância do módulo.
- **module_name** Nome do módulo.
- **localização** Ponteiro para a área de código do módulo, preâmbulo primeiro.

### <a name="return-values"></a>Valores de retorno

- **TX_SUCCESS** (0x00) Carga de módulo de sucesso.
- **TX_CALLER_ERROR** (0x13) Inválido.
- **TX_NOT_AVAILABLE** (0x1D) Manager não inicializou.
- **TX_NO_MEMORY** (0x10) Não há memória suficiente para carregar o módulo.
- **TX_PTR_ERROR** (0x03) Ponteiro inválido, instância do módulo ou preâmbulo do módulo.
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Alinhamento inválido.
- **módulo TXM_MODULE_ALREADY_LOADED** (0xF1) já carregado.
- **TXM_MODULE_INVALID** (0xF2) Preâmbulo do módulo inválido.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) propriedades incompatíveis.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```c
TXM_MODULE_INSTANCE     my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
 txm_module_manager_memory_load(&my_module, "my module", (VOID *) 0x080F0000);
```

### <a name="see-also"></a>Veja também

- txm_module_manager_file_load
- txm_module_manager_in_place_load
- txm_module_manager_unload

---

## <a name="txm_module_manager_object_pool_create"></a>txm_module_manager_object_pool_create

Crie uma piscina de objetos para módulos.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_object_pool_create(
    VOID *pool_memory_start,
    ULONG pool_memory_size);
```

### <a name="description"></a>Description

Este serviço cria um conjunto de memória de objetos do Gestor de Módulos do qual os módulos podem alocar objetos ThreadX/NetX, mantendo assim o objeto do sistema fora da área de memória do módulo.

### <a name="input-parameters"></a>Parâmetros de entrada

- **pool_memory_start** Ponteiro para o início da memória do objeto.
- **pool_memory_size** Tamanho em bytes da piscina de memória do objeto.

### <a name="return-values"></a>Valores de retorno

- **TX_SUCCESS** (0x00) Inicialização bem sucedida.
- **TX_CALLER_ERROR** (0x13) Inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);
```

### <a name="see-also"></a>Veja também

- txm_module_manager_initialize

---

## <a name="txm_module_manager_properties_get"></a>txm_module_manager_properties_get

Obtenha propriedades de módulos.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_properties_get(
    TXM_MODULE_INSTANCE *module_instance,
    ULONG *module_properties_ptr);
```

### <a name="description"></a>Description

Este serviço devolve as propriedades (especificadas no preâmbulo) de um módulo.

### <a name="input-parameters"></a>Parâmetros de entrada

- **module_instance** Ponteiro para a instância do módulo.
- **module_properties_ptr** Ponteiro para destino para as propriedades do módulo.

### <a name="return-values"></a>Valores de retorno

- **TX_SUCCESS** (0x00) Inicialização bem sucedida.
- **TX_PTR_ERROR** (0x03) Ponteiro inválido.
- **TX_CALLER_ERROR** (0x13) Inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
TXM_MODULE_INSTANCE     my_module;
ULONG                   module_properties;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Get module properties. */
txm_module_manager_properties_get(&my_module, &module_properties);
```

---

## <a name="txm_module_manager_start"></a>txm_module_manager_start

Inicie a execução do módulo.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_start(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a>Description

Este serviço inicia a execução do módulo especificado, já carregado.

### <a name="input-parameters"></a>Parâmetros de entrada

- **module_instance** Ponteiro para a instância do módulo previamente carregada.

### <a name="return-values"></a>Valores de retorno

- **TX_SUCCESS** (0x00) Início do módulo de sucesso.
- **TX_CALLER_ERROR** (0x13) Inválido.
- **TX_NOT_AVAILABLE** (0x1D) Manager não inicializou.
- **TX_PTR_ERROR** (0x03) Indicação de ponteiro ou módulo inválido.
- **TX_START_ERROR** (0x10) Módulo já começou.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(2000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a>Veja também

- txm_module_manager_stop

---

## <a name="txm_module_manager_stop"></a>txm_module_manager_stop

Pare a execução do módulo.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_stop(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a>Description

Este serviço para um módulo que foi previamente carregado e iniciado. A paragem de um módulo inclui a execução do fio de paragem opcional do módulo, a terminação de todos os fios e a eliminação de todos os recursos associados ao módulo.

### <a name="input-parameters"></a>Parâmetros de entrada

- **module_instance** Ponteiro para a instância do módulo.

### <a name="return-values"></a>Valores de retorno

- **TX_SUCCESS** (0x00) Paragem do módulo de sucesso.
- **TX_CALLER_ERROR** (0x13) Inválido.
- **TX_NOT_AVAILABLE** (0x1D) Manager não inicializou.
- **TX_PTR_ERROR** (0x03) Indicação de ponteiro ou módulo inválido.
- **TX_START_ERROR** (0x10) Módulo não começou.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(20000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a>Veja também

- txm_module_manager_start

---

## <a name="txm_module_manager_unload"></a>txm_module_manager_unload

Descarregue o módulo.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_unload(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a>Description

Este serviço descarrega o módulo previamente carregado e parado, libertando todos os recursos de memória do módulo associado.

### <a name="input-parameters"></a>Parâmetros de entrada

- **module_instance** Ponteiro para a instância do módulo.

### <a name="return-values"></a>Valores de retorno

- **TX_SUCCESS** 0x00) Descarregamento de módulo de sucesso.
- **TX_CALLER_ERROR** (0x13) Inválido.
- **TX_NOT_AVAILABLE** (0x1D) Manager não inicializou.
- **TX_NOT_DONE** (0x20) Módulo inválido ou módulo não parado.
- **TX_PTR_ERROR** (0x03) Indicação de ponteiro ou módulo inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```c
/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
status = txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a>Veja também

- txm_module_manager_file_load
- txm_module_manager_in_place_load
- txm_module_manager_memory_load
- txm_module_manager_stop
