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
# <a name="appendix-a--description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcp-client-services"></a><span data-ttu-id="e3a4c-103">Apêndice A : Descrição da funcionalidade de estado de restauração para serviços de clientes Azure RTOS NetX Duo DHCP</span><span class="sxs-lookup"><span data-stu-id="e3a4c-103">Appendix A : Description of the Restore state feature for Azure RTOS NetX Duo DHCP Client services</span></span>

<span data-ttu-id="e3a4c-104">A opção de configuração do Cliente DHDP Duo NetX, NX_DHCP_CLIENT_RESTORE_STATE, permite que um sistema restabeleça um Registo de Cliente DHCP anteriormente criado num estado vinculado entre reboots do sistema.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-104">The NetX Duo DHDP Client configuration option, NX_DHCP_CLIENT_RESTORE_STATE, allows a system to restore a previously created DHCP Client Record in a Bound state between system reboots.</span></span>

<span data-ttu-id="e3a4c-105">Quando esta opção estiver ativada, a aplicação pode suspender e retomar a linha do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-105">When this option is enabled, the application can suspend and resume the DHCP Client thread.</span></span> <span data-ttu-id="e3a4c-106">Existe também um serviço para atualizar o Cliente DHCP com o tempo decorrido entre a suspensão e o reinício do fio.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-106">There is also a service to update the DHCP Client with the elapsed time between suspending and resuming the thread.</span></span>

## <a name="restoring-the-dhcp-client-between-reboots"></a><span data-ttu-id="e3a4c-107">Restaurar o Cliente DHCP entre Reboots</span><span class="sxs-lookup"><span data-stu-id="e3a4c-107">Restoring the DHCP Client between Reboots</span></span>

<span data-ttu-id="e3a4c-108">Antes de restaurar um Cliente DHCP após o reboot, um Cliente DHCP previamente criado que deve chegar ao estado vinculado e ser atribuído um endereço IP a partir do servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-108">Before restoring a DHCP Client after rebooting, a previously created DHCP Client that must reach the Bound state and be is assigned an IP address from the DHCP server.</span></span> <span data-ttu-id="e3a4c-109">Antes de desligar, a aplicação DHCP deve então guardar o registo atual do Cliente DHCP para memória não volátil.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-109">Before it powers down, the DHCP application must then save the current DHCP Client record to non-volatile memory.</span></span> <span data-ttu-id="e3a4c-110">Deve também existir um "guardião do tempo" independente noutro sectores do sistema para acompanhar o tempo decorrido durante este estado de desaudido.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-110">There must also be an independent ‘time keeper’ elsewhere in the system to keep track of the time elapsed during this powered down state.</span></span> <span data-ttu-id="e3a4c-111">Ao ligar, a aplicação cria uma nova instância do Cliente DHCP e, em seguida, atualiza-a com o registo do Cliente DHCP anteriormente criado.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-111">On powering up, the application creates a new DHCP Client instance, and then updates it with the previously created DHCP Client record.</span></span> <span data-ttu-id="e3a4c-112">O tempo decorrido é obtido a partir do "time keeper" e, em seguida, aplicado ao tempo restante no contrato de arrendamento do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-112">The elapsed time is obtained from the “time keeper” and then applied to the time remaining on the DHCP Client lease.</span></span> <span data-ttu-id="e3a4c-113">Note que isto pode fazer com que o Cliente DHCP mude de estado, por exemplo, de BOUND para RENOVAR.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-113">Note that this may cause the DHCP Client to change states e.g. from BOUND to RENEWING.</span></span> <span data-ttu-id="e3a4c-114">Neste momento, a aplicação pode retomar o Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-114">At this point, the application can resume the DHCP Client.</span></span>

<span data-ttu-id="e3a4c-115">Se o tempo decorrido durante a desecepeição de energia colocar o estado do Cliente DHCP num estado RENOVADO ou REBIND, o Cliente DHCP iniciará automaticamente mensagens DHCP solicitando a renovação ou reencadernamento do contrato de endereço IP.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-115">If the time elapsed during power down puts the DHCP Client state in either a RENEW or REBIND state, the DHCP Client will automatically initiate DHCP messages requesting to renew or rebind the IP address lease.</span></span> <span data-ttu-id="e3a4c-116">Se o endereço IP estiver expirado, o Cliente DHCP limpará automaticamente o endereço IP na instância IP e iniciará o processo DHCP a partir do estado INIT, solicitando um novo endereço IP.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-116">If the IP address is expired, the DHCP Client will automatically clear the IP address on the IP instance and begin the DHCP process from the INIT state, requesting a new IP address.</span></span>

<span data-ttu-id="e3a4c-117">Desta forma, o Cliente DHCP pode operar entre reboots como se fosse ininterrupto.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-117">In this manner the DHCP Client can operate between reboots as if uninterrupted.</span></span>

<span data-ttu-id="e3a4c-118">Abaixo está uma ilustração desta característica.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-118">Below is an illustration of this feature.</span></span> <span data-ttu-id="e3a4c-119">Isto pressupõe que o Cliente DHCP esteja a funcionar apenas na interface principal.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-119">This assumes DHCP Client is running only on the primary interface.</span></span>

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
## <a name="resuming-the-dhcp-client-thread-after-suspension"></a><span data-ttu-id="e3a4c-120">Retomando a linha do cliente DHCP após a suspensão</span><span class="sxs-lookup"><span data-stu-id="e3a4c-120">Resuming the DHCP Client Thread after Suspension</span></span> 

<span data-ttu-id="e3a4c-121">Para suspender uma linha do Cliente DHCP sem desligar, a aplicação chama *nx_dhcp_suspend* num Cliente DHCP que alcançou o estado BOUND e que tem um endereço IP válido.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-121">To suspend a DHCP Client thread without powering down, the application calls *nx_dhcp_suspend* on a DHCP Client which has achieved the BOUND state and which has a valid IP address.</span></span> <span data-ttu-id="e3a4c-122">Quando estiver pronto para retomar o Cliente DHCP, chama pela primeira vez *nx_dhcp_client_update_time_remaining* para atualizar o tempo restante no aluguer de endereços DHCP (obtendo o tempo decorrido de um detentor do tempo independente).</span><span class="sxs-lookup"><span data-stu-id="e3a4c-122">When it is ready to resume the DHCP Client it first calls *nx_dhcp_client_update_time_remaining* to update the time remaining on the DHCP address lease (obtaining the time elapsed from an independent time keeper).</span></span> <span data-ttu-id="e3a4c-123">Em seguida, chama a *nx_dhcp_resume* para retomar a linha do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-123">Then it calls the *nx_dhcp_resume* to resume the DHCP Client thread.</span></span>

<span data-ttu-id="e3a4c-124">Se o tempo decorrido colocar o estado do Cliente DHCP num estado RENOVADO ou REBIND, o Cliente DHCP iniciará automaticamente as mensagens DHCP solicitando a renovação ou reencadernação do endereço IP.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-124">If the time elapsed puts the DHCP Client state in either a RENEW or REBIND state, the DHCP Client will automatically initiate DHCP messages requesting to renew or rebind the IP address lease.</span></span> <span data-ttu-id="e3a4c-125">Se o endereço IP estiver expirado, o Cliente DHCP limpará automaticamente o endereço IP e iniciará o processo DHCP a partir do estado INIT, solicitando um novo endereço IP.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-125">If the IP address is expired, the DHCP Client will automatically clear the IP address and begin the DHCP process from the INIT state, requesting a new IP address.</span></span>

<span data-ttu-id="e3a4c-126">Abaixo está uma ilustração de usar esta funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-126">Below is an illustration of using this feature.</span></span>

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
<span data-ttu-id="e3a4c-127">Abaixo está uma lista de serviços para restaurar um estado de cliente DHCP da memória e para suspender e retomar o Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-127">Below is a list of services for restoring a DHCP Client state from memory and for suspending and resuming the DHCP Client.</span></span>

## <a name="nx_dhcp_client_get_record"></a><span data-ttu-id="e3a4c-128">nx_dhcp_client_get_record</span><span class="sxs-lookup"><span data-stu-id="e3a4c-128">nx_dhcp_client_get_record</span></span>

<span data-ttu-id="e3a4c-129">Criar um registo do estado atual do cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="e3a4c-129">Create a record of the current DHCP Client state</span></span>

### <a name="prototype"></a><span data-ttu-id="e3a4c-130">Prototype</span><span class="sxs-lookup"><span data-stu-id="e3a4c-130">Prototype</span></span>

```c
ULONG nx_dhcp_ client_get_record(NX_DHCP *dhcp_ptr, NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a><span data-ttu-id="e3a4c-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3a4c-131">Description</span></span>

<span data-ttu-id="e3a4c-132">Este serviço salva o Cliente DHCP em execução na primeira interface ativada para DHCP encontrada na instância do Cliente DHCP para o registo apontado por record_ptr.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-132">This service saves the DHCP Client running on the first interface enabled for DHCP found on the DHCP Client instance to the record pointed to by record_ptr.</span></span> <span data-ttu-id="e3a4c-133">Isto permite que a aplicação do Cliente DHCP restaure o seu estado de Cliente DHCP depois, por exemplo, de uma energia para baixo e reiniciar.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-133">This allows the DHCP Client application restore its DHCP Client state after, for example, a power down and reboot.</span></span>

<span data-ttu-id="e3a4c-134">Para guardar um registo do Cliente DHCP numa interface específica se mais de uma interface estiver ativada para o DHCP, utilize o serviço *nx_dhcp_interface_client_get_record.*</span><span class="sxs-lookup"><span data-stu-id="e3a4c-134">To save a DHCP Client record on a specific interface if more than one interface is enabled for DHCP, use the *nx_dhcp_interface_client_get_record* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e3a4c-135">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="e3a4c-135">Input Parameters</span></span>

- <span data-ttu-id="e3a4c-136">**dhcp_ptr**: Ponteiro para o Cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="e3a4c-136">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="e3a4c-137">**record_ptr**: Pointer to DHCP Client record</span><span class="sxs-lookup"><span data-stu-id="e3a4c-137">**record_ptr**: Pointer to DHCP Client record</span></span>

### <a name="return-values"></a><span data-ttu-id="e3a4c-138">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e3a4c-138">Return Values</span></span>

- <span data-ttu-id="e3a4c-139">**NX_SUCCESS (0x0)**: Registo de clientes criado</span><span class="sxs-lookup"><span data-stu-id="e3a4c-139">**NX_SUCCESS (0x0)**: Client record created</span></span>
- <span data-ttu-id="e3a4c-140">**NX_DHCP_NOT_BOUND**: (0x94) Cliente não em estados vinculados</span><span class="sxs-lookup"><span data-stu-id="e3a4c-140">**NX_DHCP_NOT_BOUND**: (0x94) Client not in Bound states</span></span>
- <span data-ttu-id="e3a4c-141">**NX_DHCP_NO_INTERFACES_ENABLED:**(0xA5) Não há interfaces ativadas para o DHCP</span><span class="sxs-lookup"><span data-stu-id="e3a4c-141">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="e3a4c-142">NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="e3a4c-142">NX_PTR_ERROR: (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e3a4c-143">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="e3a4c-143">Allowed From</span></span>

<span data-ttu-id="e3a4c-144">Fios</span><span class="sxs-lookup"><span data-stu-id="e3a4c-144">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e3a4c-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e3a4c-145">Example</span></span>

```c
NX_DHCP_CLIENT_RECORD dhcp_record;

/* Obtain a record of the current client state. */
status=  nx_dhcp_client_get_record(dhcp_ptr, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_interface_client_get_record"></a><span data-ttu-id="e3a4c-146">nx_dhcp_interface_client_get_record</span><span class="sxs-lookup"><span data-stu-id="e3a4c-146">nx_dhcp_interface_client_get_record</span></span>

<span data-ttu-id="e3a4c-147">Criar um registo do estado atual do Cliente DHCP na interface especificada</span><span class="sxs-lookup"><span data-stu-id="e3a4c-147">Create a record of the current DHCP Client state on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="e3a4c-148">Prototype</span><span class="sxs-lookup"><span data-stu-id="e3a4c-148">Prototype</span></span>

```c
ULONG nx_dhcp_interface_client_get_record(NX_DHCP *dhcp_ptr, UINT interface_index,
                                          NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a><span data-ttu-id="e3a4c-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3a4c-149">Description</span></span>

<span data-ttu-id="e3a4c-150">Este serviço salva o Cliente DHCP em execução na interface especificada para o registo apontado por record_ptr.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-150">This service saves the DHCP Client running on the specified interface to the record pointed to by record_ptr.</span></span> <span data-ttu-id="e3a4c-151">Isto permite que a aplicação do Cliente DHCP restaure o seu estado de Cliente DHCP depois, por exemplo, de uma energia para baixo e reiniciar.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-151">This allows the DHCP Client application restore its DHCP Client state after, for example, a power down and reboot.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e3a4c-152">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="e3a4c-152">Input Parameters</span></span>

- <span data-ttu-id="e3a4c-153">**dhcp_ptr**: Ponteiro para o Cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="e3a4c-153">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="e3a4c-154">**interface_index**: Índice para obter recorde</span><span class="sxs-lookup"><span data-stu-id="e3a4c-154">**interface_index**: Index on which to get record</span></span>
- <span data-ttu-id="e3a4c-155">**record_ptr**: Pointer to DHCP Client record</span><span class="sxs-lookup"><span data-stu-id="e3a4c-155">**record_ptr**: Pointer to DHCP Client record</span></span>

### <a name="return-values"></a><span data-ttu-id="e3a4c-156">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e3a4c-156">Return Values</span></span>

- <span data-ttu-id="e3a4c-157">**NX_SUCCESS (0x0)**: Registo de clientes criado</span><span class="sxs-lookup"><span data-stu-id="e3a4c-157">**NX_SUCCESS (0x0)**: Client record created</span></span>
- <span data-ttu-id="e3a4c-158">**NX_DHCP_NOT_BOUND**: (0x94) **Cliente não em estado vinculado**</span><span class="sxs-lookup"><span data-stu-id="e3a4c-158">**NX_DHCP_NOT_BOUND**: (0x94) **Client not in Bound state**</span></span>
- <span data-ttu-id="e3a4c-159">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR:**(0x9A) Índice de interface inválido</span><span class="sxs-lookup"><span data-stu-id="e3a4c-159">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) Invalid interface index</span></span>
- <span data-ttu-id="e3a4c-160">NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-160">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="e3a4c-161">NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida</span><span class="sxs-lookup"><span data-stu-id="e3a4c-161">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e3a4c-162">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="e3a4c-162">Allowed From</span></span>

<span data-ttu-id="e3a4c-163">Fios</span><span class="sxs-lookup"><span data-stu-id="e3a4c-163">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e3a4c-164">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e3a4c-164">Example</span></span>

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
/* Obtain a record of the current client state on interface 1. */
status=  nx_dhcp_interface_client_get_record(dhcp_ptr, 1, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_-client_restore_record"></a><span data-ttu-id="e3a4c-165">nx_dhcp_ client_restore_record</span><span class="sxs-lookup"><span data-stu-id="e3a4c-165">nx_dhcp_ client_restore_record</span></span>

<span data-ttu-id="e3a4c-166">Restaurar o Cliente DHCP a partir de um registo previamente guardado</span><span class="sxs-lookup"><span data-stu-id="e3a4c-166">Restore DHCP Client from a previously saved record</span></span>

### <a name="prototype"></a><span data-ttu-id="e3a4c-167">Prototype</span><span class="sxs-lookup"><span data-stu-id="e3a4c-167">Prototype</span></span>

```c
ULONG nx_dhcp_client_restore_record(NX_DHCP *dhcp_ptr, 
                                    NX_DHCP_CLIENT_RECORD *record_ptr, 
                                    ULONG time_elapsed);

```

### <a name="description"></a><span data-ttu-id="e3a4c-168">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3a4c-168">Description</span></span>

<span data-ttu-id="e3a4c-169">Este serviço permite que uma aplicação restabeleça o seu Cliente DHCP de uma sessão anterior utilizando o registo do Cliente DHCP apontado por record_ptr.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-169">This service enables an application to restore its DHCP Client from a previous session using the DHCP Client record pointed to by record_ptr.</span></span> <span data-ttu-id="e3a4c-170">A entrada time_elapsed é aplicada ao tempo restante no arrendamento do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-170">The time_elapsed input is applied to the time remaining on DHCP Client lease.</span></span>

<span data-ttu-id="e3a4c-171">Isto requer que a aplicação do DhCP Client tenha criado um registo do Cliente DHCP antes de desligar, e guardou esse registo para memória nãovolíssia.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-171">This requires that the DHCP Client application created a record of the DHCP Client before powering down, and saved that record to nonvolatile memory.</span></span>

<span data-ttu-id="e3a4c-172">Se mais de uma interface estiver ativada para o Cliente DHCP, este serviço é aplicado à primeira interface válida encontrada na instância do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-172">If more than one interface is enabled for DHCP Client, this service is applied to the first valid interface found in the DHCP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e3a4c-173">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="e3a4c-173">Input Parameters</span></span>

- <span data-ttu-id="e3a4c-174">**dhcp_ptr**: Ponteiro para o Cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="e3a4c-174">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="e3a4c-175">**record_ptr**: Pointer to DHCP Client record</span><span class="sxs-lookup"><span data-stu-id="e3a4c-175">**record_ptr**: Pointer to DHCP Client record</span></span> 
- <span data-ttu-id="e3a4c-176">**time_elapsed:** Hora de subtrair do tempo de locação restante no registo do cliente de entrada</span><span class="sxs-lookup"><span data-stu-id="e3a4c-176">**time_elapsed**: Time to subtract from the lease time remaining in the input client record</span></span>

### <a name="return-values"></a><span data-ttu-id="e3a4c-177">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e3a4c-177">Return Values</span></span>

- <span data-ttu-id="e3a4c-178">**NX_SUCCESS**: (0x0) Registo de cliente restaurado</span><span class="sxs-lookup"><span data-stu-id="e3a4c-178">**NX_SUCCESS**: (0x0) Client record restored</span></span>
- <span data-ttu-id="e3a4c-179">**NX_DHCP_NO_INTERFACES_ENABLED:**(0xA5) Sem interfaces com DHCP</span><span class="sxs-lookup"><span data-stu-id="e3a4c-179">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces running DHCP</span></span>
- <span data-ttu-id="e3a4c-180">NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="e3a4c-180">NX_PTR_ERROR: (0x16) Invalid pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e3a4c-181">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="e3a4c-181">Allowed From</span></span>

<span data-ttu-id="e3a4c-182">Fios</span><span class="sxs-lookup"><span data-stu-id="e3a4c-182">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e3a4c-183">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e3a4c-183">Example</span></span>

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 

/* Obtain a record of the current client state. */
status=  nx_dhcp_client_restore_record(client_ptr, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr  contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_interace_client_restore_record"></a><span data-ttu-id="e3a4c-184">nx_dhcp_interace_client_restore_record</span><span class="sxs-lookup"><span data-stu-id="e3a4c-184">nx_dhcp_interace_client_restore_record</span></span>

<span data-ttu-id="e3a4c-185">Restaurar o Cliente DHCP a partir de um registo previamente guardado na interface especificada</span><span class="sxs-lookup"><span data-stu-id="e3a4c-185">Restore DHCP Client from a previously saved record on specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="e3a4c-186">Prototype</span><span class="sxs-lookup"><span data-stu-id="e3a4c-186">Prototype</span></span>

```c
ULONG nx_dhcp_interface_client_restore_record(NX_DHCP *dhcp_ptr, 
                                              NX_DHCP_CLIENT_RECORD *record_ptr, 
                                              ULONG time_elapsed);
```

### <a name="description"></a><span data-ttu-id="e3a4c-187">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3a4c-187">Description</span></span>

<span data-ttu-id="e3a4c-188">Este serviço permite que uma aplicação restabeleça o seu Cliente DHCP na interface especificada utilizando o registo do Cliente DHCP apontado por record_ptr.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-188">This service enables an application to restore its DHCP Client on the specified interface using the DHCP Client record pointed to by record_ptr.</span></span> <span data-ttu-id="e3a4c-189">A entrada time_elapsed é aplicada ao tempo restante no arrendamento do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-189">The time_elapsed input is applied to the time remaining on DHCP Client lease.</span></span>

<span data-ttu-id="e3a4c-190">Isto requer que a aplicação do DhCP Client tenha criado um registo do Cliente DHCP antes de desligar, e guardou esse registo para memória nãovolíssia.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-190">This requires that the DHCP Client application created a record of the DHCP Client before powering down, and saved that record to nonvolatile memory.</span></span>

<span data-ttu-id="e3a4c-191">Se mais de uma interface estiver ativada para o Cliente DHCP, este serviço é aplicado à primeira interface válida encontrada na instância do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-191">If more than one interface is enabled for DHCP Client, this service is applied to the first valid interface found in the DHCP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e3a4c-192">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="e3a4c-192">Input Parameters</span></span>

- <span data-ttu-id="e3a4c-193">**dhcp_ptr**: Ponteiro para o Cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="e3a4c-193">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="e3a4c-194">**record_ptr**: Pointer to DHCP Client record</span><span class="sxs-lookup"><span data-stu-id="e3a4c-194">**record_ptr**: Pointer to DHCP Client record</span></span> 
- <span data-ttu-id="e3a4c-195">**time_elapsed:** Hora de subtrair do tempo de locação restante no registo do cliente de entrada</span><span class="sxs-lookup"><span data-stu-id="e3a4c-195">**time_elapsed**: Time to subtract from the lease time remaining in the input client record</span></span>

### <a name="return-values"></a><span data-ttu-id="e3a4c-196">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e3a4c-196">Return Values</span></span>

- <span data-ttu-id="e3a4c-197">**NX_SUCCESS**: (0x0) Registo de cliente restaurado</span><span class="sxs-lookup"><span data-stu-id="e3a4c-197">**NX_SUCCESS**: (0x0) Client record restored</span></span>
- <span data-ttu-id="e3a4c-198">**NX_DHCP_NOT_BOUND:**(0x94) Cliente não vinculado ao endereço IP</span><span class="sxs-lookup"><span data-stu-id="e3a4c-198">**NX_DHCP_NOT_BOUND**: (0x94) Client not bound to IP address</span></span>
- <span data-ttu-id="e3a4c-199">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR:**(0x9A) Índice de interface inválido</span><span class="sxs-lookup"><span data-stu-id="e3a4c-199">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) Invalid interface index</span></span>
- <span data-ttu-id="e3a4c-200">NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-200">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="e3a4c-201">NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida</span><span class="sxs-lookup"><span data-stu-id="e3a4c-201">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e3a4c-202">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="e3a4c-202">Allowed From</span></span>

<span data-ttu-id="e3a4c-203">Fios</span><span class="sxs-lookup"><span data-stu-id="e3a4c-203">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e3a4c-204">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e3a4c-204">Example</span></span>

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 


/* Obtain a record of the current client state on the primary interface. */
status=  nx_dhcp_interface_client_restore_record(client_ptr, 0, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr  contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_-client_update_time_remaining"></a><span data-ttu-id="e3a4c-205">nx_dhcp_ client_update_time_remaining</span><span class="sxs-lookup"><span data-stu-id="e3a4c-205">nx_dhcp_ client_update_time_remaining</span></span>

<span data-ttu-id="e3a4c-206">Atualize o tempo restante no contrato de arrendamento do Cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="e3a4c-206">Update the time remaining on DHCP Client lease</span></span>

### <a name="prototype"></a><span data-ttu-id="e3a4c-207">Prototype</span><span class="sxs-lookup"><span data-stu-id="e3a4c-207">Prototype</span></span>

```c
ULONG nx_dhcp_client_update_time_remaining(NX_DHCP *dhcp_ptr, ULONG time_elapsed);
```

### <a name="description"></a><span data-ttu-id="e3a4c-208">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3a4c-208">Description</span></span>

<span data-ttu-id="e3a4c-209">Este serviço atualiza o tempo restante no aluguer de endereço IP do cliente DHCP com a entrada time_elapsed na primeira interface ativada para DHCP encontrada na instância do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-209">This service updates the time remaining on the DHCP Client IP address lease with the time_elapsed input on the first interface enabled for DHCP found on the DHCP Client instance.</span></span> <span data-ttu-id="e3a4c-210">A aplicação deve suspender a linha do Cliente DHCP antes de utilizar este serviço utilizando *nx_dhcp_suspend*.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-210">The application must suspend the DHCP Client thread before using this service using *nx_dhcp_suspend*.</span></span> <span data-ttu-id="e3a4c-211">Depois de ligar para este serviço, a aplicação pode retomar a linha do Cliente DHCP chamando *nx_dhcp_resume*.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-211">After calling this service, the application can resume the DHCP Client thread by calling *nx_dhcp_resume*.</span></span>

<span data-ttu-id="e3a4c-212">Isto destina-se a aplicações do Cliente DHCP que precisam de suspender a linha do Cliente DHCP por um período de tempo e, em seguida, atualizar o tempo de locação do endereço IP restante.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-212">This is intended for DHCP Client applications that need to suspend the DHCP Client thread for a period of time, and then update the IP address lease time remaining.</span></span>

<span data-ttu-id="e3a4c-213">Nota: Este serviço não se destina a ser utilizado com *nx_dhcp_client_get_record* e *nx_dhcp_client_restore_record* descritos anteriormente).</span><span class="sxs-lookup"><span data-stu-id="e3a4c-213">Note: This service is not intended to be used with *nx_dhcp_client_get_record* and *nx_dhcp_client_restore_record* described previously).</span></span> <span data-ttu-id="e3a4c-214">Estes serviços são previamente descritos nesta secção.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-214">These services are previously described in this section.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e3a4c-215">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="e3a4c-215">Input Parameters</span></span>

- <span data-ttu-id="e3a4c-216">**dhcp_ptr**: Ponteiro para o Cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="e3a4c-216">**dhcp_ptr**: Pointer to DHCP Client</span></span> 
- <span data-ttu-id="e3a4c-217">**time_elapsed:** Tempo para subtrair do tempo restante no aluguer de endereços IP</span><span class="sxs-lookup"><span data-stu-id="e3a4c-217">**time_elapsed**: Time to subtract from the time remaining on the IP address lease</span></span>

### <a name="return-values"></a><span data-ttu-id="e3a4c-218">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e3a4c-218">Return Values</span></span>

- <span data-ttu-id="e3a4c-219">**NX_SUCCESS**: (0x0) Locação IP do cliente atualizada</span><span class="sxs-lookup"><span data-stu-id="e3a4c-219">**NX_SUCCESS**: (0x0) Client IP lease updated</span></span>
- <span data-ttu-id="e3a4c-220">**NX_DHCP_NO_INTERFACES_ENABLED:**(0xA5) Não há interfaces ativadas para o DHCP</span><span class="sxs-lookup"><span data-stu-id="e3a4c-220">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="e3a4c-221">NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="e3a4c-221">NX_PTR_ERROR: (0x16) Invalid Pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e3a4c-222">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="e3a4c-222">Allowed From</span></span>

<span data-ttu-id="e3a4c-223">Fios</span><span class="sxs-lookup"><span data-stu-id="e3a4c-223">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e3a4c-224">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e3a4c-224">Example</span></span>

```c
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease. */
status=  nx_dhcp_client_update_time_remaining(client_ptr, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */
```

## <a name="nx_dhcp_interface_client_update_time_remaining"></a><span data-ttu-id="e3a4c-225">nx_dhcp_interface_client_update_time_remaining</span><span class="sxs-lookup"><span data-stu-id="e3a4c-225">nx_dhcp_interface_client_update_time_remaining</span></span>

<span data-ttu-id="e3a4c-226">Atualize o tempo restante na locação do Cliente DHCP na interface especificada</span><span class="sxs-lookup"><span data-stu-id="e3a4c-226">Update the time remaining on DHCP Client lease on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="e3a4c-227">Prototype</span><span class="sxs-lookup"><span data-stu-id="e3a4c-227">Prototype</span></span>

```c
ULONG nx_dhcp_interface_client_update_time_remaining(NX_DHCP *dhcp_ptr,
                                                     UINT interface_index,
                                                     ULONG time_elapsed);
```

### <a name="description"></a><span data-ttu-id="e3a4c-228">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3a4c-228">Description</span></span>

<span data-ttu-id="e3a4c-229">Este serviço atualiza o tempo restante no aluguer de endereços IP do Cliente DHCP com a entrada time_elapsed na interface especificada se essa interface estiver ativada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-229">This service updates the time remaining on the DHCP Client IP address lease with the time_elapsed input on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="e3a4c-230">A aplicação deve suspender a linha do Cliente DHCP antes de utilizar este serviço utilizando *nx_dhcp_suspend*.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-230">The application must suspend the DHCP Client thread before using this service using *nx_dhcp_suspend*.</span></span> <span data-ttu-id="e3a4c-231">Depois de ligar para este serviço, a aplicação pode retomar a linha do Cliente DHCP chamando *nx_dhcp_resume*.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-231">After calling this service, the application can resume the DHCP Client thread by calling *nx_dhcp_resume*.</span></span> <span data-ttu-id="e3a4c-232">Note que suspender e retomar a linha do Cliente DHCP se aplica a todas as interfaces ativadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-232">Note suspending and resuming the DHCP Client thread applies to all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="e3a4c-233">Isto destina-se a aplicações do Cliente DHCP que precisam de suspender a linha do Cliente DHCP por um período de tempo e, em seguida, atualizar o tempo de locação do endereço IP restante.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-233">This is intended for DHCP Client applications that need to suspend the DHCP Client thread for a period of time, and then update the IP address lease time remaining.</span></span>

<span data-ttu-id="e3a4c-234">Nota: Este serviço não se destina a ser utilizado com *nx_dhcp_client_get_record* e *nx_dhcp_client_restore_record* descritos anteriormente).</span><span class="sxs-lookup"><span data-stu-id="e3a4c-234">Note: This service is not intended to be used with *nx_dhcp_client_get_record* and *nx_dhcp_client_restore_record* described previously).</span></span> <span data-ttu-id="e3a4c-235">Estes serviços são previamente descritos nesta secção.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-235">These services are previously described in this section.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e3a4c-236">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="e3a4c-236">Input Parameters</span></span>

- <span data-ttu-id="e3a4c-237">**dhcp_ptr**: Ponteiro para o Cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="e3a4c-237">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="e3a4c-238">**interface_index**: Índice para interface para aplicar o tempo decorrido</span><span class="sxs-lookup"><span data-stu-id="e3a4c-238">**interface_index**: Index to interface to apply elapsed time to</span></span>
- <span data-ttu-id="e3a4c-239">**time_elapsed:** Tempo para subtrair do tempo restante no aluguer de endereços IP</span><span class="sxs-lookup"><span data-stu-id="e3a4c-239">**time_elapsed**: Time to subtract from the time remaining on the IP address lease</span></span>

### <a name="return-values"></a><span data-ttu-id="e3a4c-240">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e3a4c-240">Return Values</span></span>

- <span data-ttu-id="e3a4c-241">**NX_SUCCESS**: (0x0) Locação IP do cliente atualizada</span><span class="sxs-lookup"><span data-stu-id="e3a4c-241">**NX_SUCCESS**: (0x0) Client IP lease updated</span></span>
- <span data-ttu-id="e3a4c-242">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR:**(0x9A) Índice de interface inválido</span><span class="sxs-lookup"><span data-stu-id="e3a4c-242">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) Invalid interface index</span></span>
- <span data-ttu-id="e3a4c-243">NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-243">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="e3a4c-244">NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida</span><span class="sxs-lookup"><span data-stu-id="e3a4c-244">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e3a4c-245">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="e3a4c-245">Allowed From</span></span>

<span data-ttu-id="e3a4c-246">Fios</span><span class="sxs-lookup"><span data-stu-id="e3a4c-246">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e3a4c-247">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e3a4c-247">Example</span></span>

```c
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease on interface 1. */
status=  nx_dhcp_interface_client_update_time_remaining(client_ptr, 1, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */

```

## <a name="nx_dhcp_suspend"></a><span data-ttu-id="e3a4c-248">nx_dhcp_suspend</span><span class="sxs-lookup"><span data-stu-id="e3a4c-248">nx_dhcp_suspend</span></span>

<span data-ttu-id="e3a4c-249">Suspender a linha do cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="e3a4c-249">Suspend the DHCP Client thread</span></span>

### <a name="prototype"></a><span data-ttu-id="e3a4c-250">Prototype</span><span class="sxs-lookup"><span data-stu-id="e3a4c-250">Prototype</span></span>

```c
ULONG nx_dhcp_suspend(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="e3a4c-251">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3a4c-251">Description</span></span>

<span data-ttu-id="e3a4c-252">Este serviço suspende a atual linha do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-252">This service suspends the current DHCP Client thread.</span></span> <span data-ttu-id="e3a4c-253">Note que, ao contrário *nx_dhcp_stop,* não há qualquer alteração ao estado do Cliente DHCP quando este serviço é chamado.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-253">Note that unlike *nx_dhcp_stop*, there is no change to the DHCP Client state when this service is called.</span></span>

<span data-ttu-id="e3a4c-254">Este serviço suspende o funcionamento do DHCP em todas as interfaces ativadas para o DHCP.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-254">This service suspends DHCP running on all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="e3a4c-255">Para atualizar o estado do Cliente DHCP com o tempo decorrido enquanto o Cliente DHCP está suspenso, consulte o *nx_dhcp_client_update_time_remaining* descrito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-255">To update the DHCP Client state with elapsed time while the DHCP Client is suspended, see the *nx_dhcp_client_update_time_remaining* described previously.</span></span> <span data-ttu-id="e3a4c-256">Para retomar uma linha de cliente DHCP suspensa, a aplicação deve ligar *nx_dhcp_resume*.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-256">To resume a suspended DHCP Client thread, the application should call *nx_dhcp_resume*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e3a4c-257">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="e3a4c-257">Input Parameters</span></span>

- <span data-ttu-id="e3a4c-258">**dhcp_ptr**: Ponteiro para o Cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="e3a4c-258">**dhcp_ptr**: Pointer to DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="e3a4c-259">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e3a4c-259">Return Values</span></span>

- <span data-ttu-id="e3a4c-260">**NX_SUCCESS**: (0x0) A linha do cliente está suspensa</span><span class="sxs-lookup"><span data-stu-id="e3a4c-260">**NX_SUCCESS**: (0x0) Client thread is suspended</span></span>
- <span data-ttu-id="e3a4c-261">NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="e3a4c-261">NX_PTR_ERROR: (0x16) Invalid pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e3a4c-262">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="e3a4c-262">Allowed From</span></span>

<span data-ttu-id="e3a4c-263">Fios</span><span class="sxs-lookup"><span data-stu-id="e3a4c-263">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e3a4c-264">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e3a4c-264">Example</span></span>

```c
/* Pause the DHCP client thread. */
status=  nx_dhcp_suspend(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is paused. */
```

## <a name="nx_dhcp_resume"></a><span data-ttu-id="e3a4c-265">nx_dhcp_resume</span><span class="sxs-lookup"><span data-stu-id="e3a4c-265">nx_dhcp_resume</span></span>

<span data-ttu-id="e3a4c-266">Retomar uma linha de cliente DHCP suspensa</span><span class="sxs-lookup"><span data-stu-id="e3a4c-266">Resume a suspended DHCP Client thread</span></span>

### <a name="prototype"></a><span data-ttu-id="e3a4c-267">Prototype</span><span class="sxs-lookup"><span data-stu-id="e3a4c-267">Prototype</span></span>

```c
ULONG nx_dhcp_resume(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="e3a4c-268">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3a4c-268">Description</span></span>

<span data-ttu-id="e3a4c-269">Este serviço retoma uma linha de cliente DHCP suspensa.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-269">This service resumes a suspended DHCP Client thread.</span></span> <span data-ttu-id="e3a4c-270">Note que não há qualquer alteração ao estado real do Cliente DHCP depois de retomar a linha cliente.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-270">Note that there is no change to the actual DHCP Client state after resuming the Client thread.</span></span> <span data-ttu-id="e3a4c-271">Para atualizar o tempo restante no contrato de endereço IP do cliente DHCP com o tempo decorrido antes de ligar *nx_dhcp_resume*, consulte o *nx_dhcp_client_update_time_remaining* descrito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-271">To update the time remaining on the DHCP Client IP address lease with elapsed time before calling *nx_dhcp_resume*, see the *nx_dhcp_client_update_time_remaining* described previously.</span></span>

<span data-ttu-id="e3a4c-272">Este serviço retoma o funcionamento do DHCP em todas as interfaces ativadas para o DHCP.</span><span class="sxs-lookup"><span data-stu-id="e3a4c-272">This service resumes DHCP running on all interfaces enabled for DHCP.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e3a4c-273">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="e3a4c-273">Input Parameters</span></span>

- <span data-ttu-id="e3a4c-274">**dhcp_ptr**: Ponteiro para o Cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="e3a4c-274">**dhcp_ptr**: Pointer to DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="e3a4c-275">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="e3a4c-275">Return Values</span></span>

- <span data-ttu-id="e3a4c-276">**NX_SUCCESS**: (0x0) A linha do cliente é retomada</span><span class="sxs-lookup"><span data-stu-id="e3a4c-276">**NX_SUCCESS**: (0x0) Client thread is resumed</span></span>
- <span data-ttu-id="e3a4c-277">NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="e3a4c-277">NX_PTR_ERROR: (0x16) Invalid pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e3a4c-278">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="e3a4c-278">Allowed From</span></span>

<span data-ttu-id="e3a4c-279">Fios</span><span class="sxs-lookup"><span data-stu-id="e3a4c-279">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e3a4c-280">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e3a4c-280">Example</span></span>

```c
/* Resume the DHCP client thread. */
status=  nx_dhcp_resume(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is resumed. */
```