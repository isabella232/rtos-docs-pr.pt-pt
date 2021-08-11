---
title: Capítulo 3 - Azure RTOS NetX Duo DHCPv6 opções de configuração
description: Existem várias opções de configuração para a construção do Azure RTOS NetX Duo DHCPv6.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 129d1421215452448b1de4626fdeda530a5466bd63ed0c758676c3ad60f9d6fb
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782426"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-configuration-options"></a>Capítulo 3 - Azure RTOS NetX Duo DHCPv6 opções de configuração

Existem várias opções de configuração para a construção do Azure RTOS NetX Duo DHCPv6. A seguinte lista descreve cada uma em detalhe:  
  
  
- **NX_DHCPV6_THREAD_PRIORITY** Prioridade da linha do Cliente. Por predefinição, este valor especifica que a linha Cliente funciona na prioridade 2.

- **NX_DHCPV6_MUTEX_WAIT** A opção Time out para obter um bloqueio exclusivo num mutex do Cliente DHCPv6. O valor predefinido é TX_WAIT_FOREVER.

- **NX_DHCPV6_TICKS_PER_SECOND** Relação de tiques a segundos. Isto é dependente do processador. O valor predefinido é 100.

- **NX_DHCPV6_IP_LIFETIME_TIMER_INTERVAL**  Intervalo de tempo em segundos em que o temporizador de vida IP atualiza o tempo que o endereço IP atual foi atribuído ao Cliente. Por predefinição, este valor é 1.

- **NX_DHCPV6_SESSION_TIMER_INTERVAL**  Intervalo de tempo em segundos em que o temporizador da sessão atualiza o tempo que o Cliente esteve em sessão comunicando com o Servidor. Por predefinição, este valor é 1.

- **NX_DHCPV6_MAX_IA_ADDRESS** O número máximo de endereços IA que podem ser adicionados ao registo do Cliente. O valor predefinido é 1. 

- **NX_DHCPV6_NUM_DNS_SERVERS** Número de servidores DNS para armazenar no registo do cliente. O valor predefinido é 2.

- **NX_DHCPV6_NUM_TIME_SERVERS** Número de servidores de tempo para armazenar no registo do cliente. O valor predefinido é 1.

- **NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE**  Tamanho do tampão no registo do Cliente para deter o nome de domínio de rede do cliente. O valor predefinido é 30.

- **NX_DHCPV6_TIME_ZONE_BUFFER_SIZE**  Tamanho do tampão no registo do Cliente para manter o fuso horário do Cliente. O valor predefinido é 10.

- **NX_DHCPV6_MAX_MESSAGE_SIZE** Tamanho do tampão no registo do Cliente para manter a mensagem de estado de opção numa resposta do Servidor. O valor predefinido é de 100 bytes.

- **NX_DHCPV6_PACKET_TIME_OUT** Tempo para fora em segundos para alocar um pacote da piscina de pacotes do Cliente. O valor predefinido é de 3 segundos.

- **NX_DHCPV6_TYPE_OF_SERVICE** Isto define o tipo de serviço para a transmissão de pacotes UDP a partir da tomada do Cliente DHCPv6. O valor **predefinido** é NX_IP_NORMAL .

- **NX_DHCPV6_TIME_TO_LIVE** O número de vezes que um pacote do Cliente é reencaminhado por um router de rede antes de o pacote ser descartado. O valor predefinido é 0x80.

- **NX_DHCPV6_QUEUE_DEPTH** Especifica o número de pacotes a manter na tomada UDP do cliente receber fila antes que o NetX Duo deite fora os pacotes. O valor predefinido é 5.

## <a name="dhcpv6-message-transmission"></a>Transmissão de mensagens DHCPv6

Existem um conjunto de opções do Cliente DHCPv6 para definir parâmetros na transmissão de mensagens DHCPv6. Esses avisos são: 

  - tempo limite inicial

  - atraso máximo na primeira transmissão

  - prazo máximo de retransmissão 

  - número máximo de retransmissão 

  - duração máxima para esperar pela resposta do servidor

Estes parâmetros aplicam-se a cada uma das mensagens do Cliente DHCPv6:

- SOLICIT

- PEDIDO

- RENOVAR

- REBIND

- LANÇAMENTO

- DECLÍNIO

- CONFIRMAR

- INFORMAR

Segue-se uma lista completa destas opções configuráveis e o seu padrão 

valores:

```C
NX_DHCPV6_FIRST_SOL_MAX_DELAY                   (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_INIT_SOL_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_TIMEOUT        (120 *
                                                NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_COUNT          0
NX_DHCPV6_MAX_SOL_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_REQ_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_TIMEOUT        (30 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_COUNT          10
NX_DHCPV6_MAX_REQ_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_RENEW_TRANSMISSION_TIMEOUT       (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_TIMEOUT      (600*   
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_COUNT        0

NX_DHCPV6_INIT_REBIND_TRANSMISSION_TIMEOUT      (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_TIMEOUT     (600*  
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_COUNT       0 

NX_DHCPV6_INIT_RELEASE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_TIMEOUT    0 
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_DURATION   0

NX_DHCPV6_INIT_DECLINE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_TIMEOUT    0
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_DURATION   0
NX_DHCPV6_FIRST_CONFIRM_MAX_DELAY               (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_CONFIRM_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_TIMEOUT    (4*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_COUNT      0  
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_DURATION   10

NX_DHCPV6_FIRST_INFORM_MAX_DELAY                (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_INFORM_TRANSMISSION_TIMEOUT      (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_TIMEOUT     (120*   
                                                NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_COUNT       0 
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_DURATION    0
```

Para não limitar o tempo limite de retransmissão, decrete a contagem de retransmissão da mensagem para 0. Para não limitar o número de vezes que uma mensagem do Cliente DHCPv6 é retransmitida (recauchutado), decreta a contagem de retransmissão da mensagem para 0.

> [!NOTE]
> Independentemente do tempo limite ou do número de retrações, quando um endereço IPv6 válido expira, é removido da tabela de endereços IP e já não pode ser utilizado pelo Cliente. O Cliente NetX Duo DHCPv6 começará automaticamente a enviar mensagens SOLICIT solicitando um novo endereço IPv6.