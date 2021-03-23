---
title: Apêndice A - Descrição da Funcionalidade de Estado de Restauro para Cliente Azure RTOS NetX Duo DHCPv6
description: A opção de configuração do cliente Azure RTOS NetX Duo DHDPv6, NX_DHCPV6_CLIENT_RESTORE_STATE, permite que um sistema restabeleça um Cliente DHCP previamente criado num estado vinculado entre reboots de sistema.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3e642af158202bb3b2a4e2a37397b47d707b566e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826101"
---
# <a name="appendix-a---description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcpv6-client"></a><span data-ttu-id="98a02-103">Apêndice A - Descrição da Funcionalidade de Estado de Restauro para Cliente Azure RTOS NetX Duo DHCPv6</span><span class="sxs-lookup"><span data-stu-id="98a02-103">Appendix A - Description of the Restore State Feature for Azure RTOS NetX Duo DHCPv6 Client</span></span>

<span data-ttu-id="98a02-104">A opção de configuração do cliente Azure RTOS NetX Duo DHDPv6, NX_DHCPV6_CLIENT_RESTORE_STATE, permite que um sistema restabeleça um Cliente DHCP previamente criado num estado vinculado entre reboots de sistema.</span><span class="sxs-lookup"><span data-stu-id="98a02-104">The Azure RTOS NetX Duo DHDPv6 Client configuration option, NX_DHCPV6_CLIENT_RESTORE_STATE, allows a system to restore a previously created DHCP Client in a Bound state between system reboots.</span></span>

<span data-ttu-id="98a02-105">Esta opção também permite que uma aplicação suspenda a linha do Cliente DHCPv6 e a retome, atualizada com o tempo decorrido entre suspender e retomar o fio sem desligar.</span><span class="sxs-lookup"><span data-stu-id="98a02-105">This option also allows an application to suspend the DHCPv6 Client thread and resume it, updated with the elapsed time between suspending and resuming the thread without powering down.</span></span>

## <a name="restoring-the-dhcpv6-client-between-reboots"></a><span data-ttu-id="98a02-106">Restaurar o Cliente DHCPv6 entre Reboots</span><span class="sxs-lookup"><span data-stu-id="98a02-106">Restoring the DHCPv6 Client between Reboots</span></span>

<span data-ttu-id="98a02-107">Para restaurar um Cliente DHCPv6 entre reboots, a aplicação DHCPv6 cria uma instância do Cliente DHCPv6, e, em seguida, obtém um contrato de endereço IP usando o protocolo normal DHCPv6 e chamando *nx_dhcpv6_start*.</span><span class="sxs-lookup"><span data-stu-id="98a02-107">To restore a DHCPv6 Client between reboots, the DHCPv6 application creates an instance of the DHCPv6 Client, and then obtains an IP address lease using the normal DHCPv6 protocol and calling *nx_dhcpv6_start*.</span></span> <span data-ttu-id="98a02-108">Em seguida, a aplicação DHCPv6 aguarda a conclusão do protocolo.</span><span class="sxs-lookup"><span data-stu-id="98a02-108">Then the DHCPv6 application waits for the protocol to complete.</span></span> <span data-ttu-id="98a02-109">Se tudo correr bem, o dispositivo alcança o estado BOUND com um endereço IP válido atribuído a partir do seu Servidor DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="98a02-109">If all goes well, the device achieves the BOUND state with an assigned valid IP address from its DHCPv6 Server.</span></span> <span data-ttu-id="98a02-110">Antes de desligar, a aplicação do Cliente DHCPv6 guarda a atual instância do Cliente DHCPv6 para um registo do Cliente DHCPv6 que é depois armazenado em memória não volátil.</span><span class="sxs-lookup"><span data-stu-id="98a02-110">Before it powers down, the DHCPv6 Client application saves the current DHCPv6 Client instance to a DHCPv6 Client record which is then stored in non-volatile memory.</span></span> <span data-ttu-id="98a02-111">Um "time keeper" independente noutros locais do sistema mantém o tempo decorrido durante este estado de down.</span><span class="sxs-lookup"><span data-stu-id="98a02-111">An independent ‘time keeper’ elsewhere in the system keeps track of the time elapsed during this powered down state.</span></span> <span data-ttu-id="98a02-112">Ao ligar, a aplicação cria uma nova instância do Cliente DHCPv6 e, em seguida, atualiza-a com o registo do Cliente DHCPv6 anteriormente criado.</span><span class="sxs-lookup"><span data-stu-id="98a02-112">On powering up, the application creates a new DHCPv6 Client instance, and then updates it with the previously created DHCPv6 Client record.</span></span> <span data-ttu-id="98a02-113">O tempo decorrido é obtido a partir do "time keeper" e, em seguida, aplicado ao tempo restante no contrato de arrendamento DHCP Clientv6.</span><span class="sxs-lookup"><span data-stu-id="98a02-113">The elapsed time is obtained from the “time keeper” and then applied to the time remaining on the DHCP Clientv6 lease.</span></span> <span data-ttu-id="98a02-114">Neste momento, a aplicação pode retomar o Cliente DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="98a02-114">At this point, the application can resume the DHCPv6 Client.</span></span>

<span data-ttu-id="98a02-115">Se o tempo decorrido durante a desecepeição colocar o estado do Cliente DHCPv6 num estado RENOVADO ou REBIND, o Cliente DHCPv6 iniciará automaticamente mensagens DHCPv6 solicitando a renovação ou reencadernação do endereço IP.</span><span class="sxs-lookup"><span data-stu-id="98a02-115">If the time elapsed during power down puts the DHCPv6 Client state in either a RENEW or REBIND state, the DHCPv6 Client will automatically initiate DHCPv6 messages requesting to renew or rebind the IP address lease.</span></span> <span data-ttu-id="98a02-116">Se o endereço IP estiver expirado, o Cliente DHCPv6 limpará automaticamente o endereço IP na instância IP e iniciará o processo DHCPv6 a partir do estado DO INIT, solicitando um novo endereço IP.</span><span class="sxs-lookup"><span data-stu-id="98a02-116">If the IP address is expired, the DHCPv6 Client will automatically clear the IP address on the IP instance and begin the DHCPv6 process from the INIT state, requesting a new IP address.</span></span>

<span data-ttu-id="98a02-117">Desta forma, o Cliente DHCPv6 pode operar entre reboots como se fosse ininterrupto.</span><span class="sxs-lookup"><span data-stu-id="98a02-117">In this manner the DHCPv6 Client can operate between reboots as if uninterrupted.</span></span>

<span data-ttu-id="98a02-118">Abaixo está uma ilustração desta característica.</span><span class="sxs-lookup"><span data-stu-id="98a02-118">Below is an illustration of this feature.</span></span>

```C
/* On the power up, create an IP instance, DHCPv6 Client, enable ICMPv6 and UDP
   and other resources (not shown) for the DHCPv6 Client/application
   in tx_application_define(). */
 
/* Define the DHCPv6 Client application thread. */     
void    thread_dhcpv6_client_entry(ULONG thread_input)
{

UINT        status;
UINT        time_elapsed = 0;
NX_DHCPV6_CLIENT_RECORD client_my_record;


    /* No previously saved Client record. Start the DHCPv6 Client in the INIT state. */
    status =  nx_dhcpv6_start(&dhcp_0);

    if (status !=NX_SUCCESS)
        return;

    while(1)    
    {
    
        /* Wait for DHCPv6 Client to get the IP address. */
    }

    /* At some point decide we power down the system. */

    /* Save the Client state data which we will subsequently need to restore the DHCPv6    
       Client. */
    status = nx_dhcpv6_client_get_record(&dhcp_0, &client_my_record);               

    /* Copy this memory to non-volatile memory (not shown). */

    /* Delete the IP and DHCPv6 Client instances before powering down. */
    nx_dhcpv6_client_delete(&dhcp_0);

    nx_ip_delete(&ip_0);

    /* Ready to power down, having released other resources as necessary. */

    /* The application has determined there is a previously saved record. We will 
       restore it to the current DHCPv6 Client instance. */

/* Create the IP and DHCPv6 Client instances, enable ICMPv6 and UDP after powering up. */

/* Calculate the time elapsed during power down */

    /* Get the previous Client state data from non-volatile memory. */

    /* Apply the record to the current Client instance. This will also 
       update the IP instance with IP address, mask etc. */
    status = nx_dhcpv6_client_restore_record(&dhcp_0, &client_my_record, time_elapsed);   

     if (status != NX_SUCCESS)
          return;

     /* We are ready to resume the DHCPv6 Client thread and use the assigned IP address. */
     status = nx_dhcpv6_resume(&dhcp_0);

     if (status != NX_SUCCESS)
          return;

}
```

## <a name="nx_dhcpv6_client_get_record"></a><span data-ttu-id="98a02-119">nx_dhcpv6_client_get_record</span><span class="sxs-lookup"><span data-stu-id="98a02-119">nx_dhcpv6_client_get_record</span></span>

<span data-ttu-id="98a02-120">Criar um registo do estado atual do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="98a02-120">Create a record of the current DHCPv6 Client state</span></span>

### <a name="prototype"></a><span data-ttu-id="98a02-121">Prototype</span><span class="sxs-lookup"><span data-stu-id="98a02-121">Prototype</span></span>

```C
ULONG nx_dhcpv6_client_get_record(NX_DHCPV6 *dhcpv6_ptr, 
                                  NX_DHCPV6_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a><span data-ttu-id="98a02-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="98a02-122">Description</span></span>

<span data-ttu-id="98a02-123">Este serviço guarda o Cliente DHCPv6 para o registo apontado por record_ptr.</span><span class="sxs-lookup"><span data-stu-id="98a02-123">This service saves the DHCPv6 Client to the record pointed to by record_ptr.</span></span> <span data-ttu-id="98a02-124">Isto permite que a aplicação do Cliente DHCPv6 restaure o seu estado de Cliente DHCPv6 depois, por exemplo, de uma energia para baixo e reiniciar.</span><span class="sxs-lookup"><span data-stu-id="98a02-124">This allows the DHCPv6 Client application restore its DHCPv6 Client state after, for example, a power down and reboot.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="98a02-125">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="98a02-125">Input Parameters</span></span>

- <span data-ttu-id="98a02-126">**dhcpv6_ptr** Ponteiro para cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="98a02-126">**dhcpv6_ptr** Pointer to DHCPv6 Client</span></span>

- <span data-ttu-id="98a02-127">**record_ptr** Ponteiro para o registo do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="98a02-127">**record_ptr** Pointer to DHCPv6 Client record</span></span>

### <a name="return-values"></a><span data-ttu-id="98a02-128">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="98a02-128">Return Values</span></span>

- <span data-ttu-id="98a02-129">**NX_SUCCESS (0x0)** Registo válido do Cliente criado</span><span class="sxs-lookup"><span data-stu-id="98a02-129">**NX_SUCCESS (0x0)** Valid Client record created</span></span>

- <span data-ttu-id="98a02-130">**NX_DHCPV6_NOT_BOUND** (0xE94) Cliente não em estado vinculado, portanto não atribuído endereço IP válido</span><span class="sxs-lookup"><span data-stu-id="98a02-130">**NX_DHCPV6_NOT_BOUND** (0xE94) Client not in bound state, therefore not assigned valid IP address</span></span>

- <span data-ttu-id="98a02-131">**NX_PTR_ERROR** (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="98a02-131">**NX_PTR_ERROR** (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="98a02-132">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="98a02-132">Allowed From</span></span>

<span data-ttu-id="98a02-133">Fios</span><span class="sxs-lookup"><span data-stu-id="98a02-133">Threads</span></span>

### <a name="example"></a><span data-ttu-id="98a02-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="98a02-134">Example</span></span>

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;


/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_get_record(&dhcpv6_ptr, &dhcpv6_record);

/* If status is NX_SUCCESS dhcpv6_record contains the current DHCPv6 client record. */
```

### <a name="see-also"></a><span data-ttu-id="98a02-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98a02-135">See Also</span></span>

- <span data-ttu-id="98a02-136">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="98a02-136">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="98a02-137">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="98a02-137">nx_dhcpv6_suspend</span></span>
- <span data-ttu-id="98a02-138">nx_dhcpv6_client_restore_record</span><span class="sxs-lookup"><span data-stu-id="98a02-138">nx_dhcpv6_client_restore_record</span></span>

## <a name="nx_dhcpv6_client_restore_record"></a><span data-ttu-id="98a02-139">nx_dhcpv6_client_restore_record</span><span class="sxs-lookup"><span data-stu-id="98a02-139">nx_dhcpv6_client_restore_record</span></span>

<span data-ttu-id="98a02-140">Restaurar o estado do cliente DHCPv6 a partir de registo guardado</span><span class="sxs-lookup"><span data-stu-id="98a02-140">Restore DHCPv6 Client state from saved record</span></span>

### <a name="prototype"></a><span data-ttu-id="98a02-141">Prototype</span><span class="sxs-lookup"><span data-stu-id="98a02-141">Prototype</span></span>

```C
ULONG nx_dhcpv6_client_restore_record(NX_DHCPV6 *dhcpv6_ptr, 
                                      NX_DHCPV6_CLIENT_RECORD       
                                      *record_ptr, ULONG time_elapsed);
```

### <a name="description"></a><span data-ttu-id="98a02-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="98a02-142">Description</span></span>

<span data-ttu-id="98a02-143">Este serviço permite que uma aplicação DHCPv6 recrie o seu estado de Cliente DHCPv6 de uma sessão anterior, atualizando o Cliente DHCPv6 com o registo do Cliente DHCPv6 apontado por record_ptr, e atualiza o tempo que resta no contrato de cliente DHCPv6 com a entrada time_elapsed.</span><span class="sxs-lookup"><span data-stu-id="98a02-143">This service enables a DHCPv6 application to recreate its DHCPv6 Client state from a previous session by updating the DHCPv6 Client with the DHCPv6 Client record pointed to by record_ptr, and updates the time remaining on DHCPv6 Client lease with the time_elapsed input.</span></span> <span data-ttu-id="98a02-144">Isto permite que a aplicação do Cliente DHCPv6 recrie o seu Cliente DHCPv6, por exemplo, depois de desligar.</span><span class="sxs-lookup"><span data-stu-id="98a02-144">This allows the DHCPv6 Client application to recreate its DHCPv6 Client, for example, after powering down.</span></span> <span data-ttu-id="98a02-145">Isto requer que a aplicação do Cliente DHCPv6 tenha criado um registo do Cliente DHCPv6 antes de desligar, e guardou esse registo para memória não volátil.</span><span class="sxs-lookup"><span data-stu-id="98a02-145">This requires that the DHCPv6 Client application created a record of the DHCPv6 Client before powering down, and saved that record to non-volatile memory.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="98a02-146">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="98a02-146">Input Parameters</span></span>

- <span data-ttu-id="98a02-147">**dhcpv6_ptr** Ponteiro para cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="98a02-147">**dhcpv6_ptr** Pointer to DHCPv6 Client</span></span>

- <span data-ttu-id="98a02-148">**record_ptr** Ponteiro para o registo do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="98a02-148">**record_ptr** Pointer to DHCPv6 Client record</span></span>

- <span data-ttu-id="98a02-149">**time_elapsed** Hora de subtrair do tempo de arrendamento restante no registo do cliente de entrada</span><span class="sxs-lookup"><span data-stu-id="98a02-149">**time_elapsed** Time to subtract from the lease time remaining in the input client record</span></span>

### <a name="return-values"></a><span data-ttu-id="98a02-150">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="98a02-150">Return Values</span></span>

- <span data-ttu-id="98a02-151">**NX_SUCCESS (0x0)** Registo do cliente restaurado</span><span class="sxs-lookup"><span data-stu-id="98a02-151">**NX_SUCCESS (0x0)** Client record restored</span></span>

- <span data-ttu-id="98a02-152">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="98a02-152">NX_PTR_ERROR (0x16) Invalid Pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="98a02-153">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="98a02-153">Allowed From</span></span>

<span data-ttu-id="98a02-154">Fios</span><span class="sxs-lookup"><span data-stu-id="98a02-154">Threads</span></span>

### <a name="example"></a><span data-ttu-id="98a02-155">Exemplo</span><span class="sxs-lookup"><span data-stu-id="98a02-155">Example</span></span>

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 

/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_restore_record(&dhcpv6_ptr, &dhcpv6_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCPv6 Client pointed to by dhcpv6_ptr contains the current client record updated for time elapsed during power down. */
```

### <a name="see-also"></a><span data-ttu-id="98a02-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98a02-156">See Also</span></span>

- <span data-ttu-id="98a02-157">nx_dhcpv6_client_get_record</span><span class="sxs-lookup"><span data-stu-id="98a02-157">nx_dhcpv6_client_get_record</span></span>