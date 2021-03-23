---
title: Apêndice A - Descrição da funcionalidade de estado de restauração para serviços de clientes Azure RTOS NetX Duo DHCP
description: Este capítulo contém uma descrição da funcionalidade de estado de Restauro para os serviços de clientes Azure RTOS NetX Duo DHCP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 008ca6fb0052339e188e0240cc38a81d3a6b40e8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826144"
---
# <a name="appendix-a--description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcp-client-services"></a>Apêndice A : Descrição da funcionalidade de estado de restauração para serviços de clientes Azure RTOS NetX Duo DHCP

A opção de configuração do Cliente DHDP Duo NetX, NX_DHCP_CLIENT_RESTORE_STATE, permite que um sistema restabeleça um Registo de Cliente DHCP anteriormente criado num estado vinculado entre reboots do sistema.

Quando esta opção estiver ativada, a aplicação pode suspender e retomar a linha do Cliente DHCP. Existe também um serviço para atualizar o Cliente DHCP com o tempo decorrido entre a suspensão e o reinício do fio.

## <a name="restoring-the-dhcp-client-between-reboots"></a>Restaurar o Cliente DHCP entre Reboots

Antes de restaurar um Cliente DHCP após o reboot, um Cliente DHCP previamente criado que deve chegar ao estado vinculado e ser atribuído um endereço IP a partir do servidor DHCP. Antes de desligar, a aplicação DHCP deve então guardar o registo atual do Cliente DHCP para memória não volátil. Deve também existir um "guardião do tempo" independente noutro sectores do sistema para acompanhar o tempo decorrido durante este estado de desaudido. Ao ligar, a aplicação cria uma nova instância do Cliente DHCP e, em seguida, atualiza-a com o registo do Cliente DHCP anteriormente criado. O tempo decorrido é obtido a partir do "time keeper" e, em seguida, aplicado ao tempo restante no contrato de arrendamento do Cliente DHCP. Note que isto pode fazer com que o Cliente DHCP mude de estado, por exemplo, de BOUND para RENOVAR. Neste momento, a aplicação pode retomar o Cliente DHCP.

Se o tempo decorrido durante a desecepeição de energia colocar o estado do Cliente DHCP num estado RENOVADO ou REBIND, o Cliente DHCP iniciará automaticamente mensagens DHCP solicitando a renovação ou reencadernamento do contrato de endereço IP. Se o endereço IP estiver expirado, o Cliente DHCP limpará automaticamente o endereço IP na instância IP e iniciará o processo DHCP a partir do estado INIT, solicitando um novo endereço IP.

Desta forma, o Cliente DHCP pode operar entre reboots como se fosse ininterrupto.

Abaixo está uma ilustração desta característica. Isto pressupõe que o Cliente DHCP esteja a funcionar apenas na interface principal.

```c
/* On the power up, create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) for the DHCP Client/application
   in tx_application_define().  */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

UINT        status;
UINT        time_elapsed = 0;
NX_DHCP_CLIENT_RECORD client_nv_record;


if (/* The application checks if there is a previously saved DHCP Client record. */)
{
    /* No previously saved Client record. Start the DHCP Client in the INIT state.  */
    status =  nx_dhcp_start(&dhcp_0);

    if (status !=NX_SUCCESS)
        return;

    do
    {
        /* Wait for DHCP to assign the IP address.  */
    } while (status != NX_SUCCESS);

    /* We have a valid IP address. */
    /* At some point decide we power down the system. */
    /* Save the Client state data which we will subsequently need to restore the DHCP    
       Client. */
    status = nx_dhcp_client_get_record(&dhcp_0, &client_nv_record);               

    /* Copy this memory to non-volatile memory (not shown). */
    /* Delete the IP and DHCP Client instances before powering down. */
    nx_dhcp_delete(&dhcp_0);

    nx_ip_delete(&ip_0);
    /* Ready to power down, having released other resources as necessary. */

}
else
{

    /* The application has determined there is a previously saved record. We will 
        restore it to the current DHCP Client instance.  */

    /* Get the previous Client state data from non-volatile memory. */

    /* Apply the record to the current Client instance. This will also 
        update the IP instance with IP address, mask etc. */
    status = nx_dhcp_client_restore_record(&dhcp_0, &client_nv_record, time_elapsed);   

    if (status != NX_SUCCESS)
        return;

    /* We are ready to resume the DHCP Client thread and use the assigned IP address. */
    status = nx_dhcp_resume(&dhcp_0);

    if (status != NX_SUCCESS)
        return;

}
```
## <a name="resuming-the-dhcp-client-thread-after-suspension"></a>Retomando a linha do cliente DHCP após a suspensão 

Para suspender uma linha do Cliente DHCP sem desligar, a aplicação chama *nx_dhcp_suspend* num Cliente DHCP que alcançou o estado BOUND e que tem um endereço IP válido. Quando estiver pronto para retomar o Cliente DHCP, chama pela primeira vez *nx_dhcp_client_update_time_remaining* para atualizar o tempo restante no aluguer de endereços DHCP (obtendo o tempo decorrido de um detentor do tempo independente). Em seguida, chama a *nx_dhcp_resume* para retomar a linha do Cliente DHCP.

Se o tempo decorrido colocar o estado do Cliente DHCP num estado RENOVADO ou REBIND, o Cliente DHCP iniciará automaticamente as mensagens DHCP solicitando a renovação ou reencadernação do endereço IP. Se o endereço IP estiver expirado, o Cliente DHCP limpará automaticamente o endereço IP e iniciará o processo DHCP a partir do estado INIT, solicitando um novo endereço IP.

Abaixo está uma ilustração de usar esta funcionalidade.

```c
/* Create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) typically in tx_application_define().  */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

  /* Start the DHCP Client.  */
  status =  nx_dhcp_start(&dhcp_0);

  if (status !=NX_SUCCESS)
    return;

  while(1)
  {
   /* Wait for DHCP to obtain an IP address.  */
  }

  /* Do tasks with the IP address e.g. send pings to another host on the network...  */
  status =  nx_icmp_ping(…);

  if (status !=NX_SUCCESS)
          printf("Failed %d byte Ping!\n", length);

  /* At some later time, suspend the DHCP Client e.g. the device is going to low 
   power mode (sleep) so we do not want any threads to wake it up. */

  nx_dhcp_suspend(&dhcp_0);  

  /* During this suspended state, an independent timer is keeping track of the elapsed      
     time. */


  /* At some point, we are ready to resume the DHCP Client thread. */

  /* Update the DHCP Client lease time remaining with the time elapsed. */
  status = nx_dhcp_client_update_time_remaining(&dhcp_0, time_elapsed);   

  if (status != NX_SUCCESS)
       return;

  /* We now can resume the DHCP Client thread. */
  status = nx_dhcp_resume(&dhcp_0);

  if (status != NX_SUCCESS)
       return;

  /* Resume tasks e.g. ping another host. */
  status =  nx_icmp_ping(…);

}

```
Abaixo está uma lista de serviços para restaurar um estado de cliente DHCP da memória e para suspender e retomar o Cliente DHCP.

## <a name="nx_dhcp_client_get_record"></a>nx_dhcp_client_get_record

Criar um registo do estado atual do cliente DHCP

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_ client_get_record(NX_DHCP *dhcp_ptr, NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a>Descrição

Este serviço salva o Cliente DHCP em execução na primeira interface ativada para DHCP encontrada na instância do Cliente DHCP para o registo apontado por record_ptr. Isto permite que a aplicação do Cliente DHCP restaure o seu estado de Cliente DHCP depois, por exemplo, de uma energia para baixo e reiniciar.

Para guardar um registo do Cliente DHCP numa interface específica se mais de uma interface estiver ativada para o DHCP, utilize o serviço *nx_dhcp_interface_client_get_record.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para o Cliente DHCP
- **record_ptr**: Pointer to DHCP Client record

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS (0x0)**: Registo de clientes criado
- **NX_DHCP_NOT_BOUND**: (0x94) Cliente não em estados vinculados
- **NX_DHCP_NO_INTERFACES_ENABLED:**(0xA5) Não há interfaces ativadas para o DHCP
- NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
NX_DHCP_CLIENT_RECORD dhcp_record;

/* Obtain a record of the current client state. */
status=  nx_dhcp_client_get_record(dhcp_ptr, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_interface_client_get_record"></a>nx_dhcp_interface_client_get_record

Criar um registo do estado atual do Cliente DHCP na interface especificada

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_interface_client_get_record(NX_DHCP *dhcp_ptr, UINT interface_index,
                                          NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a>Descrição

Este serviço salva o Cliente DHCP em execução na interface especificada para o registo apontado por record_ptr. Isto permite que a aplicação do Cliente DHCP restaure o seu estado de Cliente DHCP depois, por exemplo, de uma energia para baixo e reiniciar.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para o Cliente DHCP
- **interface_index**: Índice para obter recorde
- **record_ptr**: Pointer to DHCP Client record

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS (0x0)**: Registo de clientes criado
- **NX_DHCP_NOT_BOUND**: (0x94) **Cliente não em estado vinculado**
- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR:**(0x9A) Índice de interface inválido
- NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.
- NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
/* Obtain a record of the current client state on interface 1. */
status=  nx_dhcp_interface_client_get_record(dhcp_ptr, 1, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_-client_restore_record"></a>nx_dhcp_ client_restore_record

Restaurar o Cliente DHCP a partir de um registo previamente guardado

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_client_restore_record(NX_DHCP *dhcp_ptr, 
                                    NX_DHCP_CLIENT_RECORD *record_ptr, 
                                    ULONG time_elapsed);

```

### <a name="description"></a>Descrição

Este serviço permite que uma aplicação restabeleça o seu Cliente DHCP de uma sessão anterior utilizando o registo do Cliente DHCP apontado por record_ptr. A entrada time_elapsed é aplicada ao tempo restante no arrendamento do Cliente DHCP.

Isto requer que a aplicação do DhCP Client tenha criado um registo do Cliente DHCP antes de desligar, e guardou esse registo para memória nãovolíssia.

Se mais de uma interface estiver ativada para o Cliente DHCP, este serviço é aplicado à primeira interface válida encontrada na instância do Cliente DHCP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para o Cliente DHCP
- **record_ptr**: Pointer to DHCP Client record 
- **time_elapsed:** Hora de subtrair do tempo de locação restante no registo do cliente de entrada

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x0) Registo de cliente restaurado
- **NX_DHCP_NO_INTERFACES_ENABLED:**(0xA5) Sem interfaces com DHCP
- NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 

/* Obtain a record of the current client state. */
status=  nx_dhcp_client_restore_record(client_ptr, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr  contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_interace_client_restore_record"></a>nx_dhcp_interace_client_restore_record

Restaurar o Cliente DHCP a partir de um registo previamente guardado na interface especificada

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_interface_client_restore_record(NX_DHCP *dhcp_ptr, 
                                              NX_DHCP_CLIENT_RECORD *record_ptr, 
                                              ULONG time_elapsed);
```

### <a name="description"></a>Descrição

Este serviço permite que uma aplicação restabeleça o seu Cliente DHCP na interface especificada utilizando o registo do Cliente DHCP apontado por record_ptr. A entrada time_elapsed é aplicada ao tempo restante no arrendamento do Cliente DHCP.

Isto requer que a aplicação do DhCP Client tenha criado um registo do Cliente DHCP antes de desligar, e guardou esse registo para memória nãovolíssia.

Se mais de uma interface estiver ativada para o Cliente DHCP, este serviço é aplicado à primeira interface válida encontrada na instância do Cliente DHCP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para o Cliente DHCP
- **record_ptr**: Pointer to DHCP Client record 
- **time_elapsed:** Hora de subtrair do tempo de locação restante no registo do cliente de entrada

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x0) Registo de cliente restaurado
- **NX_DHCP_NOT_BOUND:**(0x94) Cliente não vinculado ao endereço IP
- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR:**(0x9A) Índice de interface inválido
- NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.
- NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 


/* Obtain a record of the current client state on the primary interface. */
status=  nx_dhcp_interface_client_restore_record(client_ptr, 0, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr  contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_-client_update_time_remaining"></a>nx_dhcp_ client_update_time_remaining

Atualize o tempo restante no contrato de arrendamento do Cliente DHCP

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_client_update_time_remaining(NX_DHCP *dhcp_ptr, ULONG time_elapsed);
```

### <a name="description"></a>Descrição

Este serviço atualiza o tempo restante no aluguer de endereço IP do cliente DHCP com a entrada time_elapsed na primeira interface ativada para DHCP encontrada na instância do Cliente DHCP. A aplicação deve suspender a linha do Cliente DHCP antes de utilizar este serviço utilizando *nx_dhcp_suspend*. Depois de ligar para este serviço, a aplicação pode retomar a linha do Cliente DHCP chamando *nx_dhcp_resume*.

Isto destina-se a aplicações do Cliente DHCP que precisam de suspender a linha do Cliente DHCP por um período de tempo e, em seguida, atualizar o tempo de locação do endereço IP restante.

Nota: Este serviço não se destina a ser utilizado com *nx_dhcp_client_get_record* e *nx_dhcp_client_restore_record* descritos anteriormente). Estes serviços são previamente descritos nesta secção.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para o Cliente DHCP 
- **time_elapsed:** Tempo para subtrair do tempo restante no aluguer de endereços IP

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x0) Locação IP do cliente atualizada
- **NX_DHCP_NO_INTERFACES_ENABLED:**(0xA5) Não há interfaces ativadas para o DHCP
- NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease. */
status=  nx_dhcp_client_update_time_remaining(client_ptr, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */
```

## <a name="nx_dhcp_interface_client_update_time_remaining"></a>nx_dhcp_interface_client_update_time_remaining

Atualize o tempo restante na locação do Cliente DHCP na interface especificada

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_interface_client_update_time_remaining(NX_DHCP *dhcp_ptr,
                                                     UINT interface_index,
                                                     ULONG time_elapsed);
```

### <a name="description"></a>Descrição

Este serviço atualiza o tempo restante no aluguer de endereços IP do Cliente DHCP com a entrada time_elapsed na interface especificada se essa interface estiver ativada para DHCP. A aplicação deve suspender a linha do Cliente DHCP antes de utilizar este serviço utilizando *nx_dhcp_suspend*. Depois de ligar para este serviço, a aplicação pode retomar a linha do Cliente DHCP chamando *nx_dhcp_resume*. Note que suspender e retomar a linha do Cliente DHCP se aplica a todas as interfaces ativadas para DHCP.

Isto destina-se a aplicações do Cliente DHCP que precisam de suspender a linha do Cliente DHCP por um período de tempo e, em seguida, atualizar o tempo de locação do endereço IP restante.

Nota: Este serviço não se destina a ser utilizado com *nx_dhcp_client_get_record* e *nx_dhcp_client_restore_record* descritos anteriormente). Estes serviços são previamente descritos nesta secção.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para o Cliente DHCP
- **interface_index**: Índice para interface para aplicar o tempo decorrido
- **time_elapsed:** Tempo para subtrair do tempo restante no aluguer de endereços IP

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x0) Locação IP do cliente atualizada
- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR:**(0x9A) Índice de interface inválido
- NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.
- NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease on interface 1. */
status=  nx_dhcp_interface_client_update_time_remaining(client_ptr, 1, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */

```

## <a name="nx_dhcp_suspend"></a>nx_dhcp_suspend

Suspender a linha do cliente DHCP

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_suspend(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Descrição

Este serviço suspende a atual linha do Cliente DHCP. Note que, ao contrário *nx_dhcp_stop,* não há qualquer alteração ao estado do Cliente DHCP quando este serviço é chamado.

Este serviço suspende o funcionamento do DHCP em todas as interfaces ativadas para o DHCP.

Para atualizar o estado do Cliente DHCP com o tempo decorrido enquanto o Cliente DHCP está suspenso, consulte o *nx_dhcp_client_update_time_remaining* descrito anteriormente. Para retomar uma linha de cliente DHCP suspensa, a aplicação deve ligar *nx_dhcp_resume*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para o Cliente DHCP

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x0) A linha do cliente está suspensa
- NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Pause the DHCP client thread. */
status=  nx_dhcp_suspend(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is paused. */
```

## <a name="nx_dhcp_resume"></a>nx_dhcp_resume

Retomar uma linha de cliente DHCP suspensa

### <a name="prototype"></a>Prototype

```c
ULONG nx_dhcp_resume(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Descrição

Este serviço retoma uma linha de cliente DHCP suspensa. Note que não há qualquer alteração ao estado real do Cliente DHCP depois de retomar a linha cliente. Para atualizar o tempo restante no contrato de endereço IP do cliente DHCP com o tempo decorrido antes de ligar *nx_dhcp_resume*, consulte o *nx_dhcp_client_update_time_remaining* descrito anteriormente.

Este serviço retoma o funcionamento do DHCP em todas as interfaces ativadas para o DHCP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcp_ptr**: Ponteiro para o Cliente DHCP

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x0) A linha do cliente é retomada
- NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Resume the DHCP client thread. */
status=  nx_dhcp_resume(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is resumed. */
```