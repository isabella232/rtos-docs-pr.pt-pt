---
title: Apêndice A - Descrição da Funcionalidade de Estado de Restauro para Cliente Azure RTOS NetX Duo DHCPv6
description: A opção de configuração do cliente Azure RTOS NetX Duo DHDPv6, NX_DHCPV6_CLIENT_RESTORE_STATE, permite que um sistema restabeleça um Cliente DHCP previamente criado num estado vinculado entre reboots de sistema.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6840f89e66d713b1839ac84427b73273b3f9601d4b6d9d39cd94908ac77a77ca
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791334"
---
# <a name="appendix-a---description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcpv6-client"></a>Apêndice A - Descrição da Funcionalidade de Estado de Restauro para Cliente Azure RTOS NetX Duo DHCPv6

A opção de configuração do cliente Azure RTOS NetX Duo DHDPv6, NX_DHCPV6_CLIENT_RESTORE_STATE, permite que um sistema restabeleça um Cliente DHCP previamente criado num estado vinculado entre reboots de sistema.

Esta opção também permite que uma aplicação suspenda a linha do Cliente DHCPv6 e a retome, atualizada com o tempo decorrido entre suspender e retomar o fio sem desligar.

## <a name="restoring-the-dhcpv6-client-between-reboots"></a>Restaurar o Cliente DHCPv6 entre Reboots

Para restaurar um Cliente DHCPv6 entre reboots, a aplicação DHCPv6 cria uma instância do Cliente DHCPv6, e, em seguida, obtém um contrato de endereço IP usando o protocolo normal DHCPv6 e chamando *nx_dhcpv6_start*. Em seguida, a aplicação DHCPv6 aguarda a conclusão do protocolo. Se tudo correr bem, o dispositivo alcança o estado BOUND com um endereço IP válido atribuído a partir do seu Servidor DHCPv6. Antes de desligar, a aplicação do Cliente DHCPv6 guarda a atual instância do Cliente DHCPv6 para um registo do Cliente DHCPv6 que é depois armazenado em memória não volátil. Um "time keeper" independente noutros locais do sistema mantém o tempo decorrido durante este estado de down. Ao ligar, a aplicação cria uma nova instância do Cliente DHCPv6 e, em seguida, atualiza-a com o registo do Cliente DHCPv6 anteriormente criado. O tempo decorrido é obtido a partir do "time keeper" e, em seguida, aplicado ao tempo restante no contrato de arrendamento DHCP Clientv6. Neste momento, a aplicação pode retomar o Cliente DHCPv6.

Se o tempo decorrido durante a desecepeição colocar o estado do Cliente DHCPv6 num estado RENOVADO ou REBIND, o Cliente DHCPv6 iniciará automaticamente mensagens DHCPv6 solicitando a renovação ou reencadernação do endereço IP. Se o endereço IP estiver expirado, o Cliente DHCPv6 limpará automaticamente o endereço IP na instância IP e iniciará o processo DHCPv6 a partir do estado DO INIT, solicitando um novo endereço IP.

Desta forma, o Cliente DHCPv6 pode operar entre reboots como se fosse ininterrupto.

Abaixo está uma ilustração desta característica.

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

## <a name="nx_dhcpv6_client_get_record"></a>nx_dhcpv6_client_get_record

Criar um registo do estado atual do cliente DHCPv6

### <a name="prototype"></a>Prototype

```C
ULONG nx_dhcpv6_client_get_record(NX_DHCPV6 *dhcpv6_ptr, 
                                  NX_DHCPV6_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a>Description

Este serviço guarda o Cliente DHCPv6 para o registo apontado por record_ptr. Isto permite que a aplicação do Cliente DHCPv6 restaure o seu estado de Cliente DHCPv6 depois, por exemplo, de uma energia para baixo e reiniciar.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para cliente DHCPv6

- **record_ptr** Ponteiro para o registo do cliente DHCPv6

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS (0x0)** Registo válido do Cliente criado

- **NX_DHCPV6_NOT_BOUND** (0xE94) Cliente não em estado vinculado, portanto não atribuído endereço IP válido

- **NX_PTR_ERROR** (0x16) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;


/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_get_record(&dhcpv6_ptr, &dhcpv6_record);

/* If status is NX_SUCCESS dhcpv6_record contains the current DHCPv6 client record. */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_resume
- nx_dhcpv6_suspend
- nx_dhcpv6_client_restore_record

## <a name="nx_dhcpv6_client_restore_record"></a>nx_dhcpv6_client_restore_record

Restaurar o estado do cliente DHCPv6 a partir de registo guardado

### <a name="prototype"></a>Prototype

```C
ULONG nx_dhcpv6_client_restore_record(NX_DHCPV6 *dhcpv6_ptr, 
                                      NX_DHCPV6_CLIENT_RECORD       
                                      *record_ptr, ULONG time_elapsed);
```

### <a name="description"></a>Description

Este serviço permite que uma aplicação DHCPv6 recrie o seu estado de Cliente DHCPv6 de uma sessão anterior, atualizando o Cliente DHCPv6 com o registo do Cliente DHCPv6 apontado por record_ptr, e atualiza o tempo que resta no contrato de cliente DHCPv6 com a entrada time_elapsed. Isto permite que a aplicação do Cliente DHCPv6 recrie o seu Cliente DHCPv6, por exemplo, depois de desligar. Isto requer que a aplicação do Cliente DHCPv6 tenha criado um registo do Cliente DHCPv6 antes de desligar, e guardou esse registo para memória não volátil.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **dhcpv6_ptr** Ponteiro para cliente DHCPv6

- **record_ptr** Ponteiro para o registo do cliente DHCPv6

- **time_elapsed** Hora de subtrair do tempo de arrendamento restante no registo do cliente de entrada

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS (0x0)** Registo do cliente restaurado

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 

/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_restore_record(&dhcpv6_ptr, &dhcpv6_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCPv6 Client pointed to by dhcpv6_ptr contains the current client record updated for time elapsed during power down. */
```

### <a name="see-also"></a>Consulte também

- nx_dhcpv6_client_get_record