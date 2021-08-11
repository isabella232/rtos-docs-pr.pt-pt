---
title: Capítulo 3 - Azure RTOS NetX Duo DHCPv6 opções de configuração do servidor
description: Este capítulo contém uma descrição das opções de configuração do servidor Azure RTOS NetX Duo DHCPv6.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1dc0d6e41118a2f67fe98758f1f31f84d074d7af342b9db93162ffe6354077ea
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792133"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-server-configuration-options"></a>Capítulo 3 - Azure RTOS NetX Duo DHCPv6 opções de configuração do servidor

Existem várias opções de configuração para a construção de uma aplicação NetX Duo DHCPv6 Server. A seguinte lista descreve cada uma em detalhe:
  
- **NX_DISABLE_ERROR_CHECKING** Esta opção remove a verificação de erros DHCPv6. Normalmente ativado quando a aplicação é depurada.  
  
- **NX_DHCPV6_SERVER_THREAD_STACK_SIZE** Isto define o tamanho da pilha de fios DHCPv6. Por padrão, o tamanho é de 4096 bytes, o que é mais do que suficiente para a maioria das aplicações NetX Duo.

- **NX_DHCPV6_SERVER_THREAD_PRIORITY** Isto define a prioridade do fio DHCPv6Server. Isto deve ser inferior à prioridade de tarefa ip do servidor DHCPv6. O valor predefinido é 2.

- **NX_DHCPV6_IP_LEASE_TIMER_INTERVAL** Intervalo de temporizador em segundos quando a função de entrada do temporizador de locação é chamada pelo programador ThreadX. A função de entrada define uma bandeira para o Servidor DHCPv6 para aumentar o tempo acumulado de todos os Clientes no seu aluguer pelo intervalo do temporizador. Por padrão, este valor é de 60.

- **NX_DHCPV6_SESSION_TIMER_INTERVAL** Intervalo de temporizador em segundos quando a função de entrada do temporizador de sessão é chamada pelo programador ThreadX. A função de entrada define uma bandeira para o Servidor DHCPv6 para incrementar todo o tempo de sessão do Cliente ativo acumulado pelo intervalo do temporizador. Por predefinição, este valor é 3.

As seguintes definições aplicam-se ao tipo de mensagem de opção de estado e à mensagem configurável do utilizador. A opção de estado indica o resultado de um pedido de Cliente:

- **NX_DHCPV6_STATUS_MESSAGE_SUCCESS** *"OPÇÃO IA CONCEDIDA"*

- **NX_DHCPV6_STATUS_NO_ADDRS_AVAILABLE** *"OPÇÃO IA NÃO CONCEDIDO-SEM ENDEREÇOS DISPONÍVEIS"*

- **NX_DHCPV6_STATUS_MESSAGE_NO_BINDING** *"OPÇÃO IA NÃO INVÁLIDA PEDIDO DE CLIENTE"*

- **NX_DHCPV6_STATUS_MESSAGE_NOT_ON_LINK** *"OPÇÃO IA NÃO CONCEDIDA-CLIENTE NÃO NO LINK"*

- **NX_DHCPV6_STATUS_MESSAGE_USE_MULTICAST** *"OPÇÃO IA NÃO CONCEDIDA-CLIENTE DEVE USAR MULTICAST"*

- **NX_DHCPV6_STATUS_MESSAGE_NO_ADDRS_AVAILABLE** *OPÇÃO IA NÃO CONCEDIDO-SEM ENDEREÇOS DISPONÍVEIS*

- **NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID** Crie um Servidor DUID com um ID atribuído ao fornecedor. Note que o tipo DUID deve ser definido NX_DHCPV6_DUID_TYPE_VENDOR_ASSIGNED.

- **NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_LENGTH** Define o limite superior no ID atribuído ao Fornecedor. O valor predefinido é 48.

- **NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID** Define o tipo de empresa do DUID para o tipo de fornecedor privado.

- **NX_DHCPV6_PACKET_WAIT_OPTION** Isto define a opção de espera para o servidor *nx_udp_socket_receive* chamada. Isto é perfunctório uma vez que a tomada tem uma chamada de notificação de receção do NetX Duo, pelo que o pacote já está enfetuado quando o servidor DHCPv6 chama a função de receção. O valor predefinido é de 1 segundo (1 * NX_IP_PERIODIC_RATE).

- **NX_DHCPV6_SERVER_DUID_TYPE** Isto define o tipo DUID do Servidor que o Servidor inclui em todas as mensagens aos Clientes. O valor predefinido é camada de ligação mais tempo (NX_DHCPV6_SERVER_DUID_TYPE_LINK_TIME).

- **NX_DHCPV6_SERVER_HW_TYPE** Isto define o tipo de hardware na camada de ligação DUID e opções de camada de ligação mais tempo. O valor predefinido é NX_DHCPV6_SERVER_HARDWARE_TYPE_ETHERNET.

- **NX_DHCPV6_PREFERENCE_VALUE** Isto define o valor da opção preferencial entre 0 e 255, onde quanto maior o valor maior a preferência, na opção DHCPv6 com o mesmo nome. Isto diz ao Cliente qual a preferência de colocar na oferta deste Servidor onde vários Servidores DHCPv6 estão disponíveis para atribuir endereços IP. Um valor de 255 instrui o Cliente a escolher este servidor. Um valor de zero indica que o Cliente é livre de escolher. O valor predefinido é zero.

- **NX_DHCPV6_MAX_OPTION_REQUEST_OPTIONS** Isto define o número máximo de pedidos de opção num pedido de Cliente que pode ser guardado para um registo do Cliente. O valor predefinido é 6.

- **NX_DHCPV6_DEFAULT_T1_TIME** O tempo em segundos atribuído pelo Servidor num contrato de endereço do Cliente para quando o Cliente deve começar a renovar o seu endereço IP. O valor predefinido é de 2000 segundos.

- **NX_DHCPV6_DEFAULT_T2_TIME** O tempo em segundos atribuído pelo Servidor num contrato de endereço do Cliente para quando o Cliente deve começar a reencambido o seu endereço IP assumindo que a sua tentativa de renovação falhou. O valor predefinido é de 3000 segundos.

- **NX_DHCPV6_DEFAULT_PREFERRED_TIME** Isto define o tempo em segundos atribuídos pelo Servidor para quando um contrato de endereço IP do cliente atribuído é depreciado. O valor predefinido é de 2 NX_DHCPV6_DEFAULT_T1_TIME.

- **NX_DHCPV6_DEFAULT_VALID_TIME** Isto define a expiração do tempo em segundos atribuídos pelo Servidor numa locação de endereço IP do cliente atribuído. Após o termo deste tempo, o endereço IP do Cliente é inválido. O valor predefinido é de 2 NX_DHCPV6_DEFAULT_PREFERRED_TIME.

- **NX_DHCPV6_STATUS_MESSAGE_MAX** Define o tamanho máximo da mensagem do Servidor no campo de mensagem de opção de estado . O valor predefinido é de 100 bytes.

- **NX_DHCPV6_MAX_LEASES** Define o tamanho da tabela de locação IP do Servidor (por exemplo, o número máximo de endereço IPv6 disponível para locação que pode ser armazenada). Por padrão, este valor é de 100.

- **NX_DHCPV6_MAX_CLIENTS** Define o tamanho da tabela de registos do Cliente do Servidor (por exemplo.max número de Clientes que podem ser armazenados). Este valor deve ser inferior ou igual ao valor NX_DHCPV6_MAX_LEASES. Por padrão, este valor é de 120.

- **NX_DHCPV6_PACKET_TIME_OUT** Define a opção de espera nos tiques temporais para o Servidor DHCPv6 aguardar as alocações de pacotes. O valor predefinido é de 3 * NX_DHCPV6_SERVER_TICKS_PER_SECOND.

- **NX_DHCPV6_PACKET_RECEIVE_WAIT** Define a opção de espera no pacote alocar chamadas na piscina de pacotes do Servidor. O valor predefinido é (3* NX_DHCPV6_SERVER_TICKS_PER_SECOND) ou 3 segundos.

- **NX_DHCPV6_PACKET_SIZE** Isto define a carga útil do pacote do servidor pacotes de pacotes. O valor predefinido é de 500 bytes.

- **NX_DHCPV6_PACKET_POOL_SIZE** Define o tamanho da piscina do pacote do Servidor para pacotes que o Servidor irá atribuir para enviar mensagens DHCPv6. O valor predefinido é (10* NX_DHCPV6_PACKET_SIZE).

- **NX_DHCPV6_TYPE_OF_SERVICE** Isto define o tipo de serviço para a transmissão de pacotes UDP. Por padrão, este valor é NX_IP_NORMAL.

- **NX_DHCPV6_FRAGMENT_OPTION** Isto define a opção de fragmentação da tomada do servidor. O valor predefinido é NX_DON'T_FRAGMENT

- **NX_DHCPV6_TIME_TO_LIVE** Especifica o número de pacotes de routers DHCPv6 do Servidor pode 'saltar' antes de os pacotes serem descartados. O valor predefinido é definido para 0x80.

- **NX_DHCPV6_QUEUE_DEPTH** Especifica o número de pacotes a manter na tomada UDP do servidor, receber fila antes que o NetX Duo deite fora os pacotes.