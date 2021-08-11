---
title: Capítulo 1 - Introdução ao Cliente DHCPv6 da Azure RTOS NetX Duo DHCPv6
description: Nas redes IPv6, o DHCPv6 substitui o DHCP por uma atribuição dinâmica global de endereços IP a partir de um Servidor DHCPv6, e oferece a maioria das mesmas funcionalidades, bem como muitas melhorias.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f938be404c121f3080cfed1a81aa356f698538c4f557387009d951df40496a6d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791317"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-dhcpv6-client"></a>Capítulo 1 - Introdução ao Cliente DHCPv6 da Azure RTOS NetX Duo DHCPv6

Nas redes IPv6, o DHCPv6 substitui o DHCP por uma atribuição dinâmica global de endereços IP a partir de um Servidor DHCPv6, e oferece a maioria das mesmas funcionalidades, bem como muitas melhorias. Este documento explicará em detalhe como é utilizada a API do Cliente Azure RTOS NetX Duo DHCPv6 para obter endereços IPv6.

## <a name="dhcpv6-communication"></a>Comunicação DHCPv6

O protocolo DHCPv6 utiliza uDP. O Cliente utiliza a porta 546 e o Servidor utiliza a porta 547 para trocar mensagens DHCPv6. O Cliente utiliza o seu endereço local de ligação para um endereço de origem para iniciar os pedidos DHCPv6 para os servidores(s) DHCPv6 disponíveis. Quando o Cliente envia mensagens destinadas a todos os servidores DHCPv6 da rede, utiliza o endereço multicast *All_DHCP_Relay_Agents_and_Servers* *FF02::01:02*. Este é um endereço multicast reservado e com âmbito de ligação.

## <a name="dhcpv6-process-of-requesting-an-ipv6-address"></a>DHCPv6 Processo de Solicitação de Um Endereço IPv6

Para iniciar o processo de solicitação de uma atribuição global de endereços IPv6, um Cliente envia primeiro uma mensagem SOLICIT utilizando o serviço *nx_dhcpv6_send_solicit:*

**UINT nx_dhcpv6_request_solicit(NX_DHCPV6 \* dhcpv6_ptr)**

Esta mensagem é enviada para todos os servidores utilizando o endereço *All_DHCP_Relay_Agents_and_Servers.* No pedido SOLICIT, o Cliente poderá solicitar a atribuição de endereços IPv6 específicos(es) como uma dica para o Servidor. Também pode solicitar outras informações de configuração de rede a partir do Servidor, como servidor DNS, servidor NTP e outras opções no Pedido de Opção na mensagem SOLICIT.

Um Servidor DHCPv6 que pode servir um pedido de Cliente responde com uma mensagem DE ANÚNCIO contendo o endereço IPv6(es) que pode atribuir ao Cliente, o tempo de locação de endereço iPv6 e qualquer informação adicional solicitada pelo Cliente. O protocolo do Cliente DHCPv6 exige que o Cliente aguarde um período de tempo para receber mensagens DE ANÚNCIO DE TODOS os Servidores DHCPv6 da rede. Ele pré-processa cada mensagem ADVERTISE para ser uma mensagem válida, e digitaliza os dados de opção para vários parâmetros DHCPv6. Verifica também o valor preferencial na Opção Preferência, se for fornecido pelo Servidor. Se mais de uma mensagem DE ANÚNCIO for recebida, o Cliente NetX DHCPv6 escolhe o Servidor com o valor de preferência mais elevado recebido no final do período de espera.

A exceção é se o Cliente receber uma mensagem DE ANÚNCIO COM um valor preferencial de 255. Aceita essa mensagem imediatamente e descarta todas as mensagens de PUBLICIDADE subsequentes.

O período de espera é definido como o período de retransmissão que o Cliente DHCPv6 aguarda antes de enviar outra mensagem SOLICIT se não tiver recebido uma resposta de qualquer Servidor. O tempo limite inicial de retransmissão no estado SOLICIT é definido pelo protocolo DHCPv6 descrito no RFC 3315 para ser de 1 segundo. Os intervalos de retransmissão subsequentes, se o Cliente DHCPv6 não receber uma resposta válida do Servidor, são duplicados até um máximo de 120 segundos.

Tendo escolhido o Servidor, o Cliente extrai dados da mensagem "ANÚNCIO" e envia uma mensagem REQUEST de volta ao Servidor para aceitar as informações de endereço e os tempos de locação atribuídos. O Servidor responde com uma mensagem RESPOSTA para confirmar que o endereço (es) do Cliente IPv6 está registado no Servidor conforme atribuído ao Cliente.

O Cliente DHCPv6 regista o endereço IPv6 atribuído(es) com a instância IP (por exemplo, NetX Duo). Se configurado para o protocolo de Deteção de Endereços Duplicado (DAD) (ativado por padrão), o NetX Duo enviará automaticamente mensagens Neighbor Solicit para verificar se os endereços atribuídos são únicos na rede. Em caso afirmativo, notifica o Cliente DHCPv6 quando cada endereço atribuído foi promovido de PROVISÓRIO a VALID. O Cliente DHCPv6 é promovido ao estado BOUND e o dispositivo pode usar esse endereço IPv6 para enviar e transmitir mensagens. Se o protocolo DAD falhar, a NetX Duo notifica o Cliente DHCPv6 e o Cliente DHCPv6 envia uma mensagem DECLINante para o endereço IPv6(es) atribuído de volta ao Servidor e repõe o estado do Cliente DHCPv6 para o estado INIT.

### <a name="notification-of-successful-address-assignment-and-validation"></a>Notificação de atribuição e validação de endereços bem sucedidos

A aplicação pode determinar o resultado da solicitação de endereço do Cliente DHCPv6 a partir das alterações do estado se o Cliente DHCPv6 estiver configurado com a chamada de alteração do Estado no serviço *nx_dhcpv6_client_create.* Se não receber resposta do Servidor, a alteração de estado observada é de SOLICIT para INIT. Se recebeu uma resposta do Servidor mas o Servidor não conseguir atribuir o endereço, a aplicação será notificada pela chamada de erro do servidor do cliente DHCPv6 se configurada com uma (também em *nx_dhcpv6_client_create).* Se o Cliente alcançou o estado BOUND mas depois falhou na verificação do PAI, verá uma mudança de estado de BOUND para INIT. Note que uma aplicação ativada para o PAI deve dar tempo para o cheque do PAI após o início do processo de pedido. Normalmente, isto é cerca de 400-500 carrapatos (4-5 segundos na maioria dos casos).

### <a name="relinquishing-an-ipv6-address"></a>Renunciar a um endereço IPv6

Se e quando o Cliente precisar de lançar um endereço IPv6 atribuído, informa o servidor DHCPv6 ligando para o serviço *nx_dhcpv6_request_release:*

### <a name="uint-nx_dhcpv6_request_releasenx_dhcpv6-dhcpv6_ptr"></a>UINT nx_dhcpv6_request_release(dhcpv6_ptr \* NX_DHCPV6)

O Cliente DHCPv6 envia uma mensagem de LANÇAMENTO unicast contendo os endereços atribuídos ao Servidor que atribuiu o endereço e aguarda uma RESPOSTA confirmando que o Servidor recebeu a mensagem.

Nota: Existe um processo diferente para o Cliente que está a desligar-se mas planeia continuar a utilizar os endereços IPv6 atribuídos no reboot. Não envia a mensagem RELEASE ao desligar a menos que planeie solicitar um novo endereço de alimentação. Consulte "Requisitos de Memória Não Voláteis" para obter uma explicação sobre esta situação.

### <a name="dhcpv6-lease-timeouts"></a>Intervalos de tempo de locação DHCPv6

O contrato de arrendamento IPv6 atribuído pelo Servidor contém dois parâmetros de tempo limite, T1 e T2 em cada bloco De Associação de Identidade – Endereços Não Temporários (IANA). Um IANA é descrito em outros lugares neste Manual do Utilizador. Se o tempo decorrido a partir do momento em que o Cliente DHCPv6 estava vinculado ao endereço IPv6 atribuído é igual a T1, o Cliente DHCPv6 começa automaticamente a renovar o endereço IPv6 enviando uma mensagem RENOVAR. Se o tempo decorrido for igual a T2, o Cliente DHCPv6 envia automaticamente uma mensagem REBIND se não receber respostas aos seus pedidos DEV.

Dois outros parâmetros de locação IPv6, preferidos e válidos, são atribuídos a cada bloco da Associação de Identidade (IA) contido no bloco IANA. As vidas preferidas e válidas são quando o endereço IPv6 atribuído é depreciado ou inválido, respectivamente. T1 deve ser menos do que a vida preferida. T2 deve ser inferior à vida útil válida.

### <a name="ip-thread-task-requirements"></a>Requisitos de tarefa ip thread

O Cliente NetX Duo DHCPv6 requer a criação de uma instância IP NetX Duo anterior à criação do Cliente DHCPv6 para utilizar os serviços de clientes DHCPv6.

UDP, IPv6 e ICMPv6 devem ser ativados na instância IP antes da utilização do Cliente DHCPv6.

  - *nx_udp_enable*

  - *nxd_ipv6_enable*

  - *nxd_icmp_enable*

### <a name="packet-pool-requirements"></a>Requisitos de piscina de pacotes

NetX Duo DHCPv6 A criação do cliente requer um pacote de pacotes previamente criado para o envio de mensagens DHCPv6. O tamanho do pacote em termos de carga útil de pacotes e número de pacotes disponíveis é configurável pelo utilizador, e depende do volume antecipado de mensagens DHCPv6 e outras transmissões que a aplicação irá enviar.

Uma mensagem típica de DHCPv6 é de cerca de 200 bytes dependendo do número de endereços IA e opções DHCPv6 solicitadas pelo Cliente.

### <a name="network-requirements"></a>Requisitos de rede

O Cliente NetX Duo DHCPv6 requer a criação de uma tomada UDP ligada à porta 546. A tomada é criada quando a tarefa do Cliente DHCPv6 é criada.

### <a name="non-volatile-memory-requirements"></a>Requisitos de memória não voláteis

Se um Cliente DHCPv6 lançar o seu contrato de arrendamento IPv6 com o Servidor DHCPv6 ao desligar-se e solicitar novos endereços IPv6 no reboot, então não é necessário armazenamento de memória não volátil. Se um Cliente pretender continuar a utilizar o seu contrato de arrendamento atribuído, deve armazenar determinadas informações sobre o Cliente DHCPv6 para memória não volátil através de reboots.

Os requisitos de memória não voláteis e a API do cliente DHCPv6 são discutidos mais aprofundadamente na **Utilização do Cliente DHCPv6 da NetX Duo** no Capítulo Dois.

### <a name="netx-duo-dhcpv6-client-limitations"></a>Limitações do cliente NetX Duo DHCPv6

O lançamento atual do Cliente DhCPv6 da NetX Duo tem as seguintes limitações:

  - O Cliente NetX Duo DHCPv6 não suporta a opção Server Unicast para enviar mensagens UNICAST DHCPv6 para o Servidor DHCPv6, mesmo que o Servidor indique que tal é permitido.

  - O Cliente NetX Duo DHCPv6 não suporta o pedido de Reconfigure no qual um Servidor inicia alterações de endereço IPv6 aos Clientes da rede.

  - O Cliente NetX Duo DHCPv6 não suporta o formato Enterprise para o bloco de controlo de identificador exclusivo DHCPv6. Suporta apenas o formato Link Layer e Link Layer Plus Time.

  - O Cliente NetX Duo DHCPv6 não suporta pedidos de endereço da Associação Temporária (TA), mas apoia pedidos de opção não temporários (IANA).

## <a name="multihome-and-multiple-address-support"></a>Suporte multihome e de endereços múltiplos

O Cliente DHCPv6 suporta múltiplas interfaces e vários endereços por interface. O serviço dhcpv6 Client, *nx_dhcpv6_client_set_interface* permite que a aplicação do Cliente desabrada a interface de rede na qual a aplicação irá comunicar com o Servidor DHCPv6. O Cliente DHCPv6 falha na interface primária (índice zero).

Para vários endereços por interface, o Cliente DHCPv6 mantém uma lista interna de endereços a partir do índice 0. Note que o mesmo endereço registado no Cliente DHCPv6 pode não estar necessariamente localizado no mesmo índice na tabela IP dos endereços de interface.

Para os serviços de clientes DHCPv6 que recuperam informações sobre o contrato de arrendamento de endereços IPv6 do Cliente, alguns exigem que seja especificado um índice de endereço. Um exemplo para a obtenção das vidas preferidas e válidas é mostrado abaixo:

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                              UINT address_index, 
                                              NXD_ADDRESS *ip_address,
                                              ULONG preferred_lifetime, 
                                              ULONG *valid_lifetime)
```

A aplicação Do Cliente também pode recuperar o número de endereços IPv6 válidos atribuídos a partir do serviço *nx_dhcpv6_get_valid_ip_address_count:*

```C
UINT nx_dhcpv6_get_valid_ip_address_count(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT *address_count)
```

Os serviços de clientes Legacy DHCPv6 que foram criados antes de vários endereços terem sido suportados no NetX Duo não têm um índice de endereços. Portanto, com estes serviços, os dados solicitados são retirados do endereço principal global da IA, independentemente de quantos endereços de IA são atribuídos ao Cliente. Apresentamos um exemplo abaixo:

```C
UINT nx_dhcpv6_get_IP_address(NX_DHCPV6 *dhcpv6_ptr, 
                              NXD_ADDRESS *ip_address)
```

## <a name="netx-duo-dhcpv6-client-callback-functions"></a>Funções de callback de clientes NetX Duo DHCPv6

*nx_dhcpv6_state_change_callback*

Quando o Cliente DHCPv6 muda para um novo estado DHCPv6 como resultado do processamento de um pedido DHCPv6, notifica a aplicação com esta função de retorno.

*nx_dhcpv6_server_error_handler*

Quando o Cliente DHCPv6 recebe uma resposta do Servidor contendo uma opção *de Estado* com um estado não-zero (não bem sucedido), notifica a aplicação com esta chamada que inclui o código de estado de erro do Servidor.

Nota: Uma vez que estas funções de retorno são chamadas da tarefa de thread do Cliente DHCPv6, a aplicação do Cliente NÃO deve ligar para nenhum serviço de Cliente NetX Duo DHCPv6 que exija controlo mutex do Cliente DHCPv6, como *nx_dhcpv6_start, nx_dhcpv6_stop* e qualquer um dos API que enviam mensagens diretamente a partir da *chamada, por exemplo, nx_dhcpv6_request_release*.

## <a name="dhcpv6-rfcs"></a>DHCPv6 RFCs

NetX Duo DHCP está em conformidade com RFC3315, RFC3646 e RFCs relacionados.