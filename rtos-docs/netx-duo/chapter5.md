---
title: Capítulo 5 - Azure RTOS NetX Duo Network Drivers
description: Este capítulo contém uma descrição dos controladores de rede para a Azure RTOS NetX Duo.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 305c333bf3fb3f6fe76d661426c196afe25fbd5d
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/07/2021
ms.locfileid: "106549798"
---
# <a name="chapter-5---azure-rtos-netx-duo-network-drivers"></a>Capítulo 5 - Azure RTOS NetX Duo Network Drivers

Este capítulo contém uma descrição dos controladores de rede para a Azure RTOS NetX Duo. A informação apresentada destina-se a ajudar os desenvolvedores a escreverem controladores de rede específicos para a NetX Duo.

## <a name="driver-introduction"></a>Introdução do Condutor

A estrutura NX_IP contém tudo para gerir uma única instância IP. Isto inclui informações gerais do protocolo TCP/IP, bem como a rotina de entrada do condutor da rede física específica para aplicações. A rotina de entrada do condutor é definida durante o serviço ***nx_ip_create** _ . Podem ser adicionados dispositivos adicionais à instância IP através do serviço _ *_nx_ip_interface_attach_** .

A comunicação entre a NetX Duo e o controlador de rede da aplicação é realizada através da estrutura **de pedido NX_IP_DRIVER.** Esta estrutura é mais frequentemente definida localmente na pilha do chamador e é, portanto, libertada após o retorno da função de condutor e chamada. A estrutura é definida da seguinte forma.

```c
typedef struct NX_IP_DRIVER_STRUCT
{
      UINT           nx_ip_driver_command;
      UINT           nx_ip_driver_status;
      ULONG          nx_ip_driver_physical_address_msw;
      ULONG          nx_ip_driver_physical_address_lsw;
      NX_PACKET      *nx_ip_driver_packet;
      ULONG          *nx_ip_driver_return_ptr;
      NX_IP          *nx_ip_driver_ptr;
      NX_INTERFACE   *nx_ip_driver_interface;01
} NX_IP_DRIVER;
```
## <a name="driver-entry"></a>Entrada do condutor 

A NetX Duo invoca a função de entrada do controlador de rede para a inicialização do condutor e para o envio de pacotes e para várias operações de controlo e estado, incluindo a inicialização e ativação do dispositivo de rede. NetX Duo emite comandos ao controlador de rede definindo o campo ***nx_ip_driver_command** _ na estrutura de pedido _ *NX_IP_DRIVER** . A função de entrada do controlador tem o seguinte formato:

```c
VOID my_driver_entry(NX_IP_DRIVER *request);
```
## <a name="driver-requests"></a>Pedidos de motorista

NetX Duo cria o pedido do controlador com um comando específico e invoca a função de entrada do controlador para executar o comando. Como cada controlador de rede tem uma única função de entrada, o NetX Duo faz todos os pedidos através da estrutura de dados de pedido do condutor. O ***nx_ip_driver_command** _ membro da estrutura de dados do pedido do condutor _(*NX_IP_DRIVER**) define o pedido. As informações sobre o estado são comunicadas ao autor da chamada no membro **_nx_ip_driver_status_*_. Se este campo for _*NX_SUCCESS**, o pedido do condutor foi concluído com sucesso.

NetX Duo serializa todo o acesso ao condutor. Por isso, o controlador não necessita de manusear vários fios assíncronos, chamando a função de entrada. Note que a função do controlador do dispositivo executa com o mutex IP bloqueado. Por conseguinte, a função interna do controlador do dispositivo não deve bloquear-se sozinha.

Normalmente, o controlador do dispositivo também lida com interrupções. Por isso, todas as funções do controlador devem ser interrompidas.

### <a name="driver-initialization"></a>Inicialização do condutor   
Embora o processamento de inicialização do condutor real seja específico da aplicação, geralmente consiste na estrutura de dados e na inicialização de hardware físico. A informação exigida ao NetX Duo para a inicialização do condutor é a Unidade de Transmissão Máxima IP (MTU), que é o número de bytes disponíveis para a carga útil da camada IP, incluindo o cabeçalho IPv4 ou IPv6) e se a interface física necessitar de mapeamento lógico-físico. O controlador configura o valor da interface MTU chamando ***nx_ip_interface_mtu_set***.

O controlador do dispositivo precisa de ligar ***nx_ip_interface_address_mapping_configure** _ para informar o NetX Duo se é ou não necessário mapear endereços de interface. Se for necessário mapeamento de endereços, o controlador é responsável por configurar a interface com endereço MAC válido e fornecer o endereço MAC ao NetX via _*_nx_ip_interface_physical_address_set_**.

Quando o controlador de rede recebe o pedido de NX_LINK INITIALIZE da NetX Duo, recebe um ponteiro para o bloco de controlo IP como parte do NX_IP_DRIVER bloco de controlo de pedido acima indicado.

Após a chamada de aplicação ***nx_ip_create,*** o fio do ajudante IP envia um pedido do controlador com o conjunto de comando para NX_LINK_INITIALIZE ao controlador para inicializar a sua interface de rede física. Os seguintes membros NX_IP_DRIVER são utilizados para o pedido de inicialização.

| NX_IP_DRIVER &nbsp; membro | Significado    |
| ------------------------- | ----------------------------- |
| nx_ip_driver_command   | NX_LINK_INITIALIZE    |
| nx_ip_driver_ptr       | Ponteiro para a instância IP. Este valor deve ser guardado pelo controlador para que a função do controlador possa encontrar a instância IP para operar.    |
| nx_ip_driver_interface | Ponteiro para a estrutura da interface de rede dentro da instância IP. Esta informação deve ser guardada pelo condutor. Ao receber os pacotes, o condutor utilizará as informações da estrutura da interface ao enviar o pacote para cima da pilha. O índice de interface (índice do dispositivo) pode ser obtido lendo o membro nx_interface_index dentro desta estrutura de dados. |
| nx_ip_driver_status    | Estado de conclusão. Se o controlador não conseguir inicializar a interface especificada para a instância IP, retornará um estado de erro não zero. |


> [!NOTE]  
> *O condutor é na verdade chamado a partir do fio de ajuda ip que foi criado para a instância IP. Por isso, a rotina do condutor deve evitar a realização de operações de bloqueio, ou o fio do ajudante IP pode travar, causando atrasos ilimitados em aplicações que dependem do fio IP*.

### <a name="enable-link"></a>Ativar ligação   
Em seguida, o fio de ajuda IP permite que a rede física, definindo o comando do controlador para NX_LINK_ENABLE no pedido do condutor e enviando o pedido ao controlador de rede. Isto acontece pouco depois de o fio do ajudante IP completar o pedido de inicialização. Ativar o link pode ser tão simples como definir o campo *nx_interface_link_up* no caso da interface. Mas também pode envolver manipulação do hardware físico. Os seguintes membros NX_IP_DRIVER são utilizados para o pedido de ligação de ativação.

| NX_IP_DRIVER &nbsp; membro       | Significado                      |
| ------------------------- | ---------------------------- |
| nx_ip_driver_command   | NX_LINK_ENABLE   |
| nx_ip_driver_ptr       | Indicação para a instância IP  |
| nx_ip_driver_interface | Ponteiro para a instância da interface |
| nx_ip_driver_status    | Estado de conclusão. Se o controlador não conseguir ativar a interface especificada, retornará um estado de erro não zero. |

### <a name="disable-link"></a>Ligação de desativação   
Este pedido é feito pela NetX Duo durante a supressão de uma instância IP pelo serviço ***nx_ip_delete** _ . Ou uma aplicação pode emitir este comando para desativar temporariamente a ligação para economizar energia. Este serviço desativa a interface de rede física na instância IP. O processamento para desativar a ligação pode ser tão simples como limpar a _bandeira nx_interface_link_up* no caso da interface. Mas também pode envolver manipulação do hardware físico. Normalmente é uma operação inversa da operação ***Ativar a ligação.**_ Depois de desativar o link, o pedido de pedido _ *_Ativar_* a operação Link * para ativar a interface.

Os seguintes membros NX_IP_DRIVER são utilizados para o pedido de ligação para desativação.

| NX_IP_DRIVER &nbsp; membro     | Significado                      |
| ------------------------- | ---------------------------- |
| nx_ip_driver_command   | NX_LINK_DISABLE    |
| nx_ip_driver_ptr       | Indicação para a instância IP   |
| nx_ip_driver_interface | Ponteiro para a instância da interface   |
| nx_ip_driver_status    | Estado de conclusão. Se o controlador não conseguir desativar a interface especificada na instância IP, retornará um estado de erro não zero. |

### <a name="uninitialize-link"></a>Ligação Uninitialize   
Este pedido é feito pela NetX Duo durante a supressão de uma instância IP pelo serviço ***nx_ip_delete** _ . Este pedido não insinializa a interface e liberta todos os recursos criados durante a fase de inicialização. Normalmente é uma operação inversa da operação _ *_Initialize Link_** . Depois de a interface não ser inintalizada, o dispositivo não pode ser utilizado até que a interface seja novamente inicializada.

Os seguintes membros NX_IP_DRIVER são utilizados para o pedido de ligação para desativação.

| NX_IP_DRIVER &nbsp; membro    | Significado                  |
|------------------------|--------------------------|
| nx_ip_driver_command   | NX_LINK_UNINITIALZE      |
| nx_ip_driver_ptr       | Indicação para a instância IP   |
| nx_ip_driver_interface | Ponteiro para a instância da interface |
| nx_ip_driver_status    | Estado de conclusão. Se o controlador não conseguir desintitializar a interface especificada para a instância IP, retornará um estado de erro não zero. |

### <a name="packet-send"></a>Envio de pacote   
Este pedido é feito durante o processamento interno de envio de IPv4 ou IPv6, que todos os protocolos NetX Duo usam para transmitir pacotes (exceto ARP, RARP). Ao receber o comando de envio do pacote, o *nx_packet_prepend_ptr* aponta para o início do pacote a enviar, que é o início do cabeçalho IPv4 ou IPv6. *nx_packet_length* indica o tamanho total (in bytes) dos dados transmitidos. Se *nx_packet_next* for válido, o datagrama IP de saída é armazenado em vários pacotes, o controlador é obrigado a seguir o pacote acorrentado e transmitir todo o quadro. Note que a área de dados válida em cada pacote acorrentado é armazenada entre *nx_packet_prepend_ptr* e *nx_packet_append_ptr*.

O condutor é responsável pela construção do cabeçalho físico. Se for necessário um endereço físico para o mapeamento de endereços IP (como o Ethernet), a camada IP já resolveu o endereço MAC. O endereço MAC de destino é passado a partir da instância IP, armazenado em *nx_ip_driver_physical_address_msw e nx_ip_driver_physical_address_lsw*.

Depois de adicionar o cabeçalho físico, o processamento de envio do pacote chama então a função de saída do condutor para transmitir o pacote.

Os seguintes membros NX_IP_DRIVER são utilizados para o pedido de envio de pacotes.

| NX_IP_DRIVER &nbsp; membro              | Significado                               |
| -----------------------------------| --------------------------------------|
| nx_ip_driver_command            | NX_LINK_PACKET_SEND                |
| nx_ip_driver_ptr                | Indicação para a instância IP                |
| nx_ip_driver_packet             | Ponteiro para o pacote para enviar         |
| nx_ip_driver_interface          | Ponteiro para a instância da interface.    |
| nx_ip_driver_physical_address_msw | 32 bits de endereço físico mais significativos (apenas se necessário mapeamento físico) |
| nx_ip_driver_physical_address_lsw | Menos significativos 32 bits de endereço físico (apenas se necessário mapeamento físico) |
| nx_ip_driver_status             | Estado de conclusão. Se o controlador não conseguir enviar o pacote, retornará um estado de erro não zero. |

### <a name="packet-broadcastipv4-packets-only"></a>Emissão de pacotes (apenas pacotes IPv4)  
Este pedido é quase idêntico ao pedido de envio de pacotes. A única diferença é que os campos de endereço físico de destino estão definidos para o endereço MAC de transmissão Ethernet. Os seguintes membros NX_IP_DRIVER são utilizados para o pedido de transmissão de pacotes.

| NX_IP_DRIVER &nbsp; membro                | Significado                                                                                                  |
|------------------------------------|----------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command               | NX_LINK_PACKET_BROADCAST                                                                                 |
| nx_ip_driver_ptr                   | Indicação para a instância IP                                                                                   |
| nx_ip_driver_packet                | Ponteiro para o pacote para enviar                                                                            |
| nx_ip_driver_physical_address_ms w | 0x0000FFFF (transmissão)                                                                                   |
| nx_ip_driver_physical_address_lsw  | 0xFFFFFFFF (transmissão)                                                                                   |
| nx_ip_driver_interface             | Ponteiro para a instância da interface.                                                                       |
| nx_ip_driver_status                | Estado de conclusão. Se o controlador não conseguir enviar o pacote, retornará um estado de erro não zero. |

### <a name="arp-send"></a>Envio ARP  
Este pedido também é semelhante ao pedido de envio de pacote IP. A única diferença é que o cabeçalho Ethernet especifica um pacote ARP em vez de um pacote IP, e os campos de endereço físico de destino são definidos para endereço de transmissão MAC. Os seguintes membros NX_IP_DRIVER são utilizados para o pedido de envio ARP.

| NX_IP_DRIVER &nbsp; membro                | Significado                                                                                                      |
|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command               | NX_LINK_ARP_SEND                                                                                             |
| nx_ip_driver_ptr                   | Indicação para a instância IP                                                                                       |
| nx_ip_driver_packet                | Ponteiro para o pacote para enviar                                                                                |
| nx_ip_driver_physical_address_ms w | 0x0000FFFF (transmissão)                                                                                       |
| nx_ip_driver_physical_address_lsw  | 0xFFFFFFFF (transmissão)                                                                                       |
| nx_ip_driver_interface             | Ponteiro para a instância da interface.                                                                           |
| nx_ip_driver_status                | Estado de conclusão. Se o controlador não conseguir enviar o pacote ARP, retornará um estado de erro não zero. |

> [!IMPORTANT]  
> *Se não for necessário mapeamento físico, a implementação deste pedido não é necessária*.

*Embora a ARP tenha sido substituída pelo Protocolo de Descoberta de Vizinhos e pelo Protocolo de Descoberta do Router no IPv6, os controladores da rede Ethernet ainda devem ser compatíveis com pares IPv4 e routers. Por isso, os condutores ainda devem manusear pacotes ARP*.

### <a name="arp-response-send"></a>Envio de resposta ARP  
Este pedido é quase idêntico ao pedido de envio de pacotes ARP. A única diferença é que os campos de endereços físicos de destino são passados a partir da instância IP. Os seguintes membros NX_IP_DRIVER são utilizados para o pedido de envio de resposta ARP.

| NX_IP_DRIVER &nbsp; membro                  | Significado                                  |
| -------------------------------------- | -----------------------------------------|
| nx_ip_driver_command                | NX_LINK_ARP_RESPONSE_SEND            |
| nx_ip_driver_ptr                    | Indicação para a instância IP   |
| nx_ip_driver_packet                 | Ponteiro para o pacote para enviar          |
| nx_ip_driver_physical_address_msw | Mais significativo 32 bits de endereço físico |
| nx_ip_driver_physical_address_lsw | Menos significativo 32 bits de endereço físico |
| nx_ip_driver_interface              | Ponteiro para a instância da interface |
| nx_ip_driver_status                 | Estado de conclusão. Se o controlador não conseguir enviar o pacote ARP, retornará um estado de erro não zero. |

> [!IMPORTANT]  
> *Se não for necessário mapeamento físico, a implementação deste pedido não é necessária*.

### <a name="rarp-send"></a>RARP Enviar   
Este pedido é quase idêntico ao pedido de envio de pacotes ARP. As únicas diferenças são o tipo de cabeçalho de pacote e os campos de endereço físico não são necessários porque o destino físico é sempre um endereço de transmissão.

Os seguintes membros NX_IP_DRIVER são utilizados para o pedido de envio da RARP.

| NX_IP_DRIVER &nbsp; membro                | Significado                                                                                                       |
|------------------------------------|---------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command               | NX_LINK_RARP_SEND                                                                                             |
| nx_ip_driver_ptr                   | Indicação para a instância IP                                                                                        |
| nx_ip_driver_packet                | Ponteiro para o pacote para enviar                                                                                 |
| nx_ip_driver_physical_address_ms w | 0x0000FFFF (transmissão)                                                                                        |
| nx_ip_driver_physical_address_lsw  | 0xFFFFFFFF (transmissão)                                                                                        |
| nx_ip_driver_interface             | Ponteiro para a instância da interface.                                                                            |
| nx_ip_driver_status                | Estado de conclusão. Se o controlador não conseguir enviar o pacote RARP, retornará um estado de erro não zero. |

> [!IMPORTANT]  
> *As aplicações que requerem o serviço RARP devem implementar este comando*.

### <a name="multicast-group-join"></a>Grupo Multicast Junta-se   
Este pedido é feito com o serviço ***nx_igmp_multicast_interface join** _ e _*_nx_ipv4_multicast_interface_join_*_ em IPv4, _ *_nxd_ipv6_multicast_interface_join_** serviço no IPv6, e várias operações exigidas pelo IPv6. O controlador de rede pega no endereço de grupo multicast fornecido e configura os meios físicos para aceitar pacotes de entrada a partir desse endereço de grupo multicast. Note que para os condutores que não suportam filtro multicast, a lógica de receção do condutor pode ter de estar em modo promíscuo. Neste caso, o condutor poderá ter de filtrar os quadros de entrada com base no endereço MAC de destino, reduzindo assim a quantidade de tráfego passado para a instância IP. Os seguintes membros NX_IP_DRIVER são utilizados para o pedido de associação do grupo multicast.

| NX_IP_DRIVER &nbsp; membro                  | Significado                                 |
| -------------------------------------- | --------------------------------------- |
| nx_ip_driver_command                | NX_LINK_MULTICAST_JOIN               |
| nx_ip_driver_ptr                    | Indicação para a instância IP  |
| nx_ip_driver_physical_address_msw | Mais significativo 32 bits de endereço físico multicast |
| nx_ip_driver_physical_address_lsw | Menos significativo 32 bits de endereço físico multicast |
| nx_ip_driver_interface              | Ponteiro para a instância da interface |
| nx_ip_driver_status                 | Estado de conclusão. Se o condutor não conseguir aderir ao grupo multicast, retornará um estado de erro não zero. |

> [!NOTE]  
> *As aplicações IPv6 exigirão que o multicast seja implementado no controlador para protocolos baseados no ICMPv6, como a configuração de endereços. No entanto, para aplicações IPv4, a implementação deste pedido não é necessária se não forem necessárias capacidades multicast*.

> [!IMPORTANT]  
> *Se o IPv6 não estiver ativado e não forem necessárias capacidades multicast pelo IPv4, a implementação deste pedido não é necessária*.

### <a name="multicast-group-leave"></a>Licença de grupo multicast  
Este pedido é invocado chamando explicitamente os serviços ***nx_igmp_multicast_interface_leave** _ ou _*_nx_ipv4_multicast_interface_leave_*_ em IPv4, _ *_nxd_ipv6_multicast_interface_leave_** serviço no IPv6, ou por várias operações internas da NetX Duo necessárias para o IPv6. O controlador remove o endereço multicast Ethernet fornecido da lista multicast. Depois de um anfitrião ter deixado um grupo multicast, os pacotes na rede com este endereço multicast Ethernet já não são recebidos por esta instância IP. Os seguintes membros NX_IP_DRIVER são utilizados para o pedido de licença de grupo multicast.

| NX_IP_DRIVER &nbsp; membro              | Significado                              |
| -----------------------------------| -------------------------------------|
| nx_ip_driver_command            | NX_LINK_MULTICAST_LEAVE           |
| nx_ip_driver_ptr                | Indicação para a instância IP   |
| nx_ip_driver_physical_address_msw | Mais significativo 32 bits de endereço físico multicast |
| nx_ip_driver_physical_address_lsw | Menos significativos 32 bits de endereço físico multicast |
| nx_ip_driver_interface              | Ponteiro para a instância da interface |
| nx_ip_driver_status                 | Estado de conclusão. Se o condutor não conseguir sair do grupo multicast, retornará um estado de erro não zero. |

> [!IMPORTANT]  
> *Se não forem necessárias capacidades multicast por IPv4 ou IPv6, a implementação deste pedido não é necessária*.

### <a name="attach-interface"></a>Interface anexa  
Este pedido é invocado do Duo NetX ao controlador do dispositivo, permitindo ao condutor associar a instância do condutor à instância IP correspondente e à instância de interface física dentro do IP. Os seguintes membros NX_IP_DRIVER são utilizados para o pedido de interface anexa.

| NX_IP_DRIVER &nbsp; membro    | Significado                  |
|------------------------|--------------------------|
| nx_ip_driver_command   | NX_LINK_INTERFACE_ATTACH |
| nx_ip_driver_ptr       | Indicação para a instância IP   |
| nx_ip_driver_interface | Ponteiro para a instância da interface.|
| nx_ip_driver_status    | Estado de conclusão. Se o controlador não conseguir separar a interface especificada da instância IP, retornará um estado de erro não zero. |

### <a name="detach-interface"></a>Interface de descolexo    
Este pedido é invocado pela NetX Duo ao controlador do dispositivo, permitindo ao condutor dissociar a instância do condutor com a instância IP correspondente e a instância de interface física dentro do IP. Os seguintes membros NX_IP_DRIVER são utilizados para o pedido de interface anexa.

| NX_IP_DRIVER &nbsp; membro    | Significado                                                                                                                                    |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command   | NX_LINK_INTERFACE_DETACH                                                                                                                   |
| nx_ip_driver_ptr       | Indicação para a instância IP                                                                                                                     |
| nx_ip_driver_interface | Ponteiro para a instância da interface.                                                                                                         |
| nx_ip_driver_status    | Estado de conclusão. Se o controlador não conseguir ligar a interface especificada à instância IP, retornará um estado de erro não zero. |

### <a name="get-link-status"></a>Obtenha o estado do link    
A aplicação pode consultar o estado da ligação de interface de rede utilizando o serviço ***netX*** Duo nx_ip_interface_status_check serviço para qualquer interface no anfitrião. Consulte o Capítulo 4, "Descrição dos Serviços NetX Duo" na página 149, para obter mais detalhes sobre estes serviços.

O estado do link está contido no campo *nx_interface_link_up* na estrutura NX_INTERFACE apontada por *nx_ip_driver_interface* ponteiro. Os seguintes membros NX_IP_DRIVER são utilizados para o pedido de estado de ligação.

| NX_IP_DRIVER &nbsp; membro       | Significado                  |
| --------------------------- | -------------------------|
| nx_ip_driver_command     | NX_LINK_GET_STATUS    |
| nx_ip_driver_ptr         | Indicação para a instância IP   |
| nx_ip_driver_return_ptr | Ponteiro para o destino para colocar o estado. |
| nx_ip_driver_interface   | Ponteiro para a instância da interface   |
| nx_ip_driver_status      | Estado de conclusão. Se o controlador não conseguir obter um estado específico, retornará um estado de erro não zero. |

> [!NOTE]  
> ***nx_ip_status_check** _ ainda está disponível para verificar o estado da interface primária. No entanto, os desenvolvedores de aplicações são encorajados a usar o serviço específico da interface: _ *_nx_ip_interface_status_check._**

### <a name="get-link-speed"></a>Obtenha velocidade de ligação  
Este pedido é feito a partir do serviço ***nx_ip_driver_direct_command.*** O condutor armazena a velocidade da linha do link no destino fornecido. Os seguintes membros NX_IP_DRIVER são utilizados para o pedido de velocidade da linha de ligação.

| NX_IP_DRIVER &nbsp; membro   | Significado                   |
| ------------------------| ------------------------- |
| nx_ip_driver_command     | NX_LINK_GET_SPEED          |
| nx_ip_driver_ptr         | Indicação para a instância IP                                                                                         |
| nx_ip_driver_return_ptr | Ponteiro para o destino para colocar a velocidade da linha                                                             |
| nx_ip_driver_interface   | Ponteiro para a instância da interface                                                                              |
| nx_ip_driver_status      | Estado de conclusão. Se o condutor não conseguir obter informações de velocidade, retornará um estado de erro não zero. |

> [!IMPORTANT]  
> *Este pedido não é utilizado internamente pela NetX Duo pelo que a sua implementação é opcional.*

### <a name="get-duplex-type"></a>Obter Tipo Duplex   
Este pedido é feito a partir do serviço ***nx_ip_driver_direct_command.*** O condutor armazena o tipo duplex do link no destino fornecido. Os seguintes membros NX_IP_DRIVER são utilizados para o pedido do tipo duplex.

| NX_IP_DRIVER &nbsp; membro   | Significado                                                                                                    |
| --------------------------- | -------------------------------------------------------------------------------------------------------------- |
| nx_ip_driver_command     | NX_LINK_GET_DUPLEX_TYPE                                                                                    |
| nx_ip_driver_ptr         | Indicação para a instância IP                                                                                         |
| nx_ip_driver_return_ptr | Ponteiro para o destino para colocar o tipo duplex                                                            |
| nx_ip_driver_interface   | Ponteiro para a instância da interface                                                                              |
| nx_ip_driver_status      | Estado de conclusão. Se o controlador não conseguir obter informações duplex, irá retornar um estado de erro não zero. |

> [!IMPORTANT]  
> *Este pedido não é utilizado internamente pela NetX Duo pelo que a sua implementação é opcional.*

### <a name="get-error-count"></a>Obtenha a contagem de erros   
Este pedido é feito a partir do serviço ***nx_ip_driver_direct_command.*** O condutor armazena a contagem de erros do link no destino fornecido. Para suportar esta funcionalidade, o controlador necessita de rastrear os erros de funcionamento. Os seguintes membros NX_IP_DRIVER são utilizados para o pedido de contagem de erros de ligação.

| NX_IP_DRIVER &nbsp; membro   | Significado                   |
| --------------------------- | -------------------------------|
| nx_ip_driver_command     | NX_LINK_GET_ERROR_COUNT   |
| nx_ip_driver_ptr         | Indicação para a instância IP   |
| nx_ip_driver_return_ptr | Ponteiro para o destino para colocar a contagem de erros |
| nx_ip_driver_interface   | Ponteiro para a instância da interface|
| nx_ip_driver_status      | Estado de conclusão. Se o controlador não conseguir obter a contagem de erros, retornará um estado de erro não zero. |

> [!IMPORTANT]
> *Este pedido não é utilizado internamente pela NetX Duo pelo que a sua implementação é opcional.*

### <a name="get-receive-packet-count"></a>Receber Contagem de Pacotes    
Este pedido é feito a partir do serviço ***nx_ip_driver_direct_command.*** O condutor armazena a contagem de pacotes de receção do link no destino fornecido. Para suportar esta funcionalidade, o controlador precisa de acompanhar o número de pacotes recebidos. Os seguintes membros NX_IP_DRIVER são utilizados para o pedido de contagem de pacotes de ligação.

| NX_IP_DRIVER &nbsp; membro       | Significado                        |
| --------------------------- | -------------------------------|
| nx_ip_driver_command     | NX_LINK_GET_RX_COUNT      |
| nx_ip_driver_ptr         | Indicação para a instância IP  |
| nx_ip_driver_return_ptr | Ponteiro para o destino para colocar a contagem de pacotes de receção   |
| nx_ip_driver_interface   | Ponteiro para a interface de rede física  |
| nx_ip_driver_status      | Estado de conclusão. Se o condutor não conseguir receber a contagem, retornará um estado de erro não zero. |

> [!IMPORTANT]  
> *Este pedido não é utilizado internamente pela NetX Duo pelo que a sua implementação é opcional.*

### <a name="get-transmit-packet-count"></a>Obtenha a contagem de pacotes de transmissão   
Este pedido é feito a partir do serviço ***nx_ip_driver_direct_command.*** O condutor armazena a contagem de pacotes de transmissão do link no destino fornecido. Para suportar esta funcionalidade, o controlador necessita de acompanhar cada pacote que transmite em cada interface. Os seguintes membros NX_IP_DRIVER são utilizados para o pedido de contagem de pacotes de transmissão de ligação.

| NX_IP_DRIVER &nbsp; membro   | Significado                   |
| ----------------------- | ------------------------- |
| nx_ip_driver_command | NX_LINK_GET_TX_COUNT  |
| nx_ip_driver_ptr     | Indicação para a instância IP    |
| nx_ip_driver_return_ptr | Ponteiro para o destino para colocar a contagem de pacotes de transmissão  |
| nx_ip_driver_interface   | Ponteiro para a instância da interface   |
| nx_ip_driver_status      | Estado de conclusão. Se o controlador não conseguir obter a contagem de transmissão, retornará um estado de erro não zero. |

> [!IMPORTANT]  
> *Este pedido não é utilizado internamente pela NetX Duo pelo que a sua implementação é opcional.*

### <a name="get-allocation-errors"></a>Obter erros de atribuição   
Este pedido é feito a partir do serviço ***nx_ip_driver_direct_command.*** O condutor armazena a contagem de erros de atribuição de pacotes do link no destino fornecido. Os membros seguintes NX_IP_DRIVER são utilizados para o pedido de contagem de erros de atribuição de ligações.

| NX_IP_DRIVER &nbsp; membro       | Significado                       |
| --------------------------- | ----------------------------- |
| nx_ip_driver_command     | NX_LINK_GET_ALLOC_ERRORS  |
| nx_ip_driver_ptr         | Indicação para a instância IP     |
| nx_ip_driver_return_ptr | Ponteiro para o destino para colocar a contagem de erros de atribuição  |
| nx_ip_driver_interface   | Ponteiro para a instância da interface  |
| nx_ip_driver_status      | Estado de conclusão. Se o condutor não conseguir obter erros de atribuição, retornará um estado de erro não zero. |

> [!IMPORTANT]  
> *Este pedido não é utilizado internamente pela NetX Duo pelo que a sua implementação é opcional.*

### <a name="driver-deferred-processing"></a>Processamento diferido do condutor    
Este pedido é feito a partir do fio do ajudante IP em resposta ao condutor que chama a _* **rotina de nx_ip_driver_deferred_processing**_ de um isr de transmissão ou receção. Isto permite ao controlador ISR adiar o pacote receber e transmitir o processamento para o fio do ajudante IP e assim reduzir a quantidade para processar no ISR. O campo _nx_interface_additional_link_info* na estrutura NX_INTERFACE apontada por *nx_ip_driver_interface* pode ser utilizado pelo condutor para armazenar informações sobre o evento de processamento diferido a partir do contexto do fio do ajudante IP. Os seguintes membros NX_IP_DRIVER são utilizados para o evento de processamento diferido.

| NX_IP_DRIVER &nbsp; membro     | Significado                           |
| ------------------------- | --------------------------------- |
| nx_ip_driver_command   | NX_LINK_DEFERRED_PROCESSING    |
| nx_ip_driver_ptr       | Indicação para a instância IP            |
| nx_ip_driver_interface | Ponteiro para a instância da interface |

### <a name="set-physical-address"></a>Definir endereço físico  
Este pedido é feito a partir do serviço ***nx_ip_interface_physical_address_set** _ . Este serviço permite que uma aplicação altere o endereço físico da interface no tempo de execução. Ao receber este comando, o controlador é obrigado a reconfigure o endereço de hardware da interface de rede para o endereço físico fornecido. Uma vez que a instância IP já tem o novo endereço, não há necessidade de chamar o serviço _ *_nx_ip_interface_address_set_** deste comando.

Os seguintes membros NX_IP_DRIVER são utilizados para o pedido de comando do utilizador.

| NX_IP_DRIVER &nbsp; membro      | Significado                      |
| -------------------------- | ---------------------------- |
| nx_ip_driver_command    | NX_LINK_SET_PHYSICAL_ADDRESS  |
| nx_ip_driver_ptr        | Indicação para a instância IP  |
| nx_ip_driver_interface  | Ponteiro para a instância da interface   |
| nx_ip_driver_physical_ad dress_msw | 32 bits mais significativos do novo endereço físico  |
| nx_ip_driver_physical_ad dress_lsw | Menos significativos 32 bits do novo endereço físico  |
| nx_ip_driver_status                  | Estado de conclusão. Se o controlador não conseguir reconfigurar o endereço físico, retornará um estado de erro não zero. |

### <a name="user-commands"></a>Comandos do Utilizador    
Este pedido é feito a partir do serviço ***nx_ip_driver_direct_command.*** O controlador processa os comandos específicos do utilizador da aplicação. Os seguintes membros NX_IP_DRIVER são utilizados para o pedido de comando do utilizador.

| NX_IP_DRIVER &nbsp; membro       | Significado                       |
| --------------------------- | ----------------------------- |
| nx_ip_driver_command     | NX_LINK_USER_COMMAND       |
| nx_ip_driver_ptr         | Indicação para a instância IP        |
| nx_ip_driver_return_ptr | Utilizador definido       |
| nx_ip_driver_interface   | Ponteiro para a instância da interface    |
| nx_ip_driver_status      | Estado de conclusão. Se o controlador não conseguir executar comandos de utilizador, retornará um estado de erro não zero. |

> [!IMPORTANT] 
> *Este pedido não é utilizado internamente pela NetX Duo pelo que a sua implementação é opcional.*

### <a name="unimplemented-commands"></a>Comandos não implacáveis  
Os comandos não simplificados pelo controlador de rede devem ter o campo de devolução definido para NX_UNHANDLED_COMMAND.

## <a name="driver-capability"></a>Capacidade do condutor

Algumas interfaces de rede oferecem funcionalidades de descarregamento de checksum. Os controladores de dispositivos podem aproveitar as acelerações de hardware para libertar o tempo de CPU de executar vários cálculos de checkum.

Dependendo do nível de suporte de verificação de hardware do hardware do hardware, o controlador do dispositivo precisa de informar a instância IP de que funcionalidade de hardware está ativada. Desta forma, a instância IP está ciente da funcionalidade de hardware e descarrega o máximo de cálculo possível para o hardware. O controlador deve utilizar o ***nx_ip_interface_capability_set*** API para definir todas as funcionalidades que a interface física é capaz de manusear.

As seguintes funcionalidades podem ser utilizadas:

- NX_INTERFACE_CAPABILITY_IPV4_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_IPV4_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_TCP_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_TCP_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_UDP_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_UDP_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_ICMPV4_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_ICMPV4_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_ICMPV6_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_ICMPV6_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_IGMP_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_IGMP_RX_CHECKSUM

Para um cálculo de checkum que possa ser realizado em hardware, o controlador deve configurar corretamente o hardware ou os descritores de tampão para que a parte de verificação de um pacote de saída possa ser gerada e inserida no cabeçalho pelo hardware. Ao receber um pacote, a lógica de verificação de hardware deve ser capaz de verificar o valor da parte de verificação. Se o valor da quantidade de cheques estiver incorreto, a moldura recebida deve ser descartada.

Mesmo com a capacidade de realizar a computação de checksum em hardware, a instância IP ainda mantém a capacidade de checkum. Em certos cenários, por exemplo, um datagrama de UDP que passa pela proteção IPsec, o checkum da UDP deve ser calculado em software antes de passar o quadro da UDP para baixo da pilha. A maioria das funcionalidades de verificação de hardware não suporta o cálculo de checkum para um segmento de dados protegidos pelo IPsec. Para um quadro UDP ou ICMP que precisa de ser fragmentado, o checkum UDP ou ICMP precisa de ser calculado em software. A maior parte da lógica de verificação de hardware não lida com o caso em que os dados são divididos em vários quadros.

## <a name="driver-output"></a>Saída do condutor  

Todos os pedidos de transmissão de pacotes previamente mencionados requerem uma função de saída implementada no controlador. A lógica de transmissão específica é específica do hardware, mas geralmente consiste em verificar a capacidade de hardware para enviar o pacote imediatamente. Se possível, a carga útil do pacote (e cargas adicionais na cadeia de pacotes) são carregadas num ou mais tampões de transmissão de hardware e é iniciada uma operação de transmissão. Se o pacote não encaixar nos amortecedores de transmissão disponíveis, o pacote deve ser em fila e ser transmitido quando os amortecedores de transmissão ficarem disponíveis.

A fila de transmissão recomendada é uma lista ligada ao canto, com ponteiros de cabeça e cauda. Novos pacotes são adicionados ao final da fila, mantendo o pacote mais antigo na frente. O *campo nx_packet_queue_next* é usado como o próximo link do pacote na fila. O condutor define os ponteiros da cabeça e da cauda da fila de transmissão.

> [!CAUTION]  
> *Uma vez que esta fila é acedida a partir de linhas e porções de interrupção do condutor, a proteção de interrupção deve ser colocada em torno das manipulações da fila*.

A maioria das implementações de hardware físico geram uma interrupção após a conclusão do pacote. Quando o condutor recebe tal interrupção, normalmente liberta os recursos associados ao pacote que acaba de ser transmitido. Caso a lógica de transmissão leia os dados diretamente do tampão NX_PACKET, o controlador deve utilizar o serviço ***de nx_packet_transmit_release*** para libertar o pacote associado à interrupção completa do transmissor para o conjunto de pacotes disponíveis. Em seguida, o condutor examina a fila de transmissão para pacotes adicionais à espera de serem enviados. Como muitos dos pacotes de transmissão em fila que se encaixam no(s) buffer(s) de hardware são desaltados e carregados nos tampão. Isto é seguido pelo início de outra operação de envio.

Assim que os dados do NX_PACKET foram transferidos para o emissor FIFO (ou caso um condutor suporte a uma operação de cópia zero, os dados em NX_PACKET foram transmitidos), o condutor deve mover a *nx_packet_prepend_ptr* para o início do cabeçalho IP antes de ligar ***nx_packet_transmit_release.** _ Lembre-se de ajustar _nx_packet_length* em conformidade. Se uma moldura IP for composta por vários pacotes, apenas a cabeça da cadeia de pacotes precisa de ser libertada.

## <a name="driver-input"></a>Entrada do condutor

Após a receção de uma interrupção de pacote recebida, o controlador de rede recupera o pacote dos amortecedores de hardware físico e constrói um pacote NetX Duo válido. A construção de um pacote NetX Duo válido envolve a criação do campo de comprimento apropriado e acorrentar vários pacotes se o tamanho do pacote de entrada for maior do que uma carga útil de um único pacote. Uma vez devidamente construído, o *prepend_ptr* é movido após o cabeçalho da camada física e o pacote de receção é enviado para NetX Duo.

NetX Duo assume que os cabeçalhos IP (IPv4 e IPv6) e ARP estão alinhados num limite **ULONG.** O controlador NetX Duo deve, portanto, assegurar este alinhamento. Nos ambientes Ethernet isto é feito iniciando o cabeçalho Ethernet dois bytes desde o início do pacote. Quando o *nx_packet_prepend_ptr* é movido para além do cabeçalho Ethernet, o cabeçalho IP subjacente (IPv4 e IPv6) ou cabeça de ARP é alinhado em 4 bytes.

> [!WARNING] 
> *Consulte a secção "Cabeçalhos Ethernet" abaixo para obter diferenças importantes entre os cabeçalhos IPv6 e IPv6 Ethernet*.

Existem várias funções de pacote de receção disponíveis no NetX Duo. Se o pacote recebido for um pacote ARP, _* **nx_arp_packet_deferred_receive**_ é chamado. Se o pacote recebido for um pacote RARP, _ _*_nx_rarp_packet_deferred_receive_*_ é chamado. Existem várias opções para lidar com pacotes IP de entrada. Para o manuseamento mais rápido dos pacotes IP, é chamado _ _*_nx_ip_packet_receive._*_ Esta abordagem tem a menor sobrecarga, mas requer mais processamento no manipulador de serviço de interrupção de receção do condutor (ISR). Para um processamento mínimo de ISR __ *_nx_ip_packet_deferred_receive_** é chamado.

Após a construção do novo pacote de receção, os amortecedores de receção de hardware físico são configurados para receber mais dados. Isto pode exigir a atribuição de pacotes NetX Duo e a colocação do endereço de carga útil no tampão de receção de hardware ou pode simplesmente ser alterado para alterar uma definição no tampão de receção de hardware. Para minimizar as possibilidades de superação, é importante que os buffers de receção do hardware tenham tampão disponíveis o mais rapidamente possível após a receção de um pacote.

> [!IMPORTANT] 
> *Os amortecedores de receção inicial são configurados durante a inicialização do condutor*.

### <a name="deferred-receive-packet-handling"></a>Tratamento de pacotes diferidos  
O controlador pode adiar o processamento de pacotes para o fio de ajuda do NetX Duo IP. Para algumas aplicações, isto pode ser necessário para minimizar o processamento do ISR, bem como pacotes abandonados. 

Para utilizar o manuseamento de pacotes diferidos, a biblioteca NetX Duo tem primeiro de ser compilada com ***NX_DRIVER_DEFERRED_PROCESSING** _ definido. Isto adiciona a lógica do pacote diferido ao fio de ajuda do NetX Duo IP. Em seguida, ao receber um pacote de dados, o condutor deve chamar __nx_ip_packet_deferred_receive():*

```c
_nx_ip_packet_deferred_receive(ip_ptr, packet_ptr);
```
A função de receção diferida coloca o pacote de receção representado por *packet_ptr* numa FIFO (lista ligada) e notifica o fio do ajudante IP. Após a execução, o ajudante ip chama repetidamente a função de manuseamento diferido para processar cada pacote diferido. O processamento de manipulador diferido inclui normalmente a remoção do cabeçalho de camada física do pacote (geralmente Ethernet) e o envio para uma destas funções de receção NetX Duo:

- ***_nx_ip_packet_receive***
- ***_nx_arp_packet_deferred_receive***
- ***_nx_rarp_packet_deferred_receive***

## <a name="ethernet-headers"></a>Cabeçalhos Ethernet 

Uma das diferenças mais significativas entre iPv6 e IPv4 para cabeçalhos Ethernet é a definição do tipo de fotograma. Ao enviar pacotes, o controlador Ethernet é responsável pela definição do tipo de fotograma Ethernet em pacotes de saída. Para os pacotes IPv6, o tipo de armação deve ser 0x86DD; para os pacotes IPv4, o tipo de fotograma deve ser 0x0800.

O seguinte segmento de código ilustra este processo:

```c
NX_PACKET *packet_ptr;
packet_ptr = driver_req_ptr -> nx_ip_driver_packet;
if (packet_ptr -> nx_packet_ip_version == NX_IP_VERSION_V4)
{

   /* Set Ethernet frame type to IPv4 /*
   ethernet_frame_ptr -> frame_type = 0x0800;

   /* Swap endian-ness for little endian targets.*/
   NX_CHANGE_USHORT_ENDIAN(ethernet_frame_ptr -> frame_type);
}
else if (packet_ptr -> nx_packet_ip_version == NX_IP_VERSION_V6)
{

   /* Set Ethernet frame type to IPv6. /*
   ethernet_frame_ptr -> frame_type = 0x86DD;

   /* Swap endian-ness for little endian targets.*/
   NX_CHANGE_USHORT_ENDIAN(ethernet_frame_ptr -> frame_type);
}
else
{

   /* Unknown IP version. Free the packet we will not send. */
   nx_packet_transmit_release(packet_ptr);
}
```
Da mesma forma, para os pacotes de entrada, o controlador Ethernet deve determinar o tipo de pacote do tipo de fotograma Ethernet. Deve ser implementado para aceitar os tipos de moldura IPv6 (0x86DD), IPv4 (0x0800), ARP (0x0806) e RARP (0x8035).

## <a name="example-ram-ethernet-network-driver"></a>Exemplo RAM Ethernet Network Driver

O sistema de demonstração NetX Duo é entregue com um pequeno controlador de rede baseado em RAM, definido no ficheiro ***nx_ram_network_driver.c.*** Este controlador assume que as instâncias IP estão todas na mesma rede e simplesmente atribui endereços de hardware virtuais (endereços MAC) a cada instância do dispositivo à medida que são criadas. Este ficheiro fornece um bom exemplo da estrutura básica dos controladores de rede física NetX Duo. Os utilizadores podem desenvolver os seus próprios controladores de rede utilizando a estrutura do condutor apresentada neste exemplo.

A função de entrada do controlador de rede é ***_nx_ram_network_driver(),** _ que é passada para a instância IP criar chamada. As funções de entrada para interfaces de rede adicionais podem ser passadas para o serviço _nx_ip_interface_attach()* Após o funcionamento da instância IP, a função de entrada do controlador é invocada para inicializar e ativar o dispositivo (consulte a caixa **NX_LINK_INITIALIZE** e **NX_LINK_ENABLE).** Após a **emissão do** comando NX_LINK_ENABLE, o dispositivo deve estar pronto para transmitir e receber pacotes. 

A instância IP transmite pacotes de rede através de um destes comandos:

| Comando                         |  Descrição                                                   |
| ------------------------------- | -------------------------------------------------------------- |
| ***NX_LINK_PACKET_SEND***    | Um pacote IPv4 ou IPv6 está a ser transmitido,                   |
| ***NX_LINK_ARP_SEND***       | Está a ser transmitido um pedido ARP ou um pacote de resposta ARP,    |
| ***NX_LINK_ARP_RARP_SEND*** | Está a ser transmitido um pacote de pedido ou resposta reverso da ARP, |

No processamento destes comandos, o controlador de rede precisa de preparar o cabeçalho de quadro Ethernet apropriado e, em seguida, enviá-lo para o hardware subjacente para transmissão. Durante o processo de transmissão, o controlador de rede tem a propriedade exclusiva da área tampão do pacote. Assim que os dados estiverem a ser transmitidos (ou uma vez que os dados tenham sido copiados para o tampão de transferência interno do controlador), o controlador de rede é responsável pela libertação do amortecedor de pacotes, movendo primeiro o ponteiro pré-final para além do cabeçalho Ethernet para o cabeçalho IP (e ajuste o comprimento do pacote em conformidade), e, em seguida, chamando o serviço ***de nx_packet_transmit_release()*** para libertar o pacote. Não libertar o pacote após a transmissão de dados fará com que os pacotes vazem.

O controlador do dispositivo de rede é também responsável pelo tratamento dos pacotes de dados recebidos. No exemplo do condutor da RAM, o pacote recebido é processado pela função ***_nx_ram_network_driver_receive()***. Uma vez que o dispositivo recebe uma moldura Ethernet, o controlador é responsável por armazenar os dados na estrutura NX_PACKET. Note que o NetX Duo assume que o cabeçalho IP começa a partir de um endereço alinhado de 4 bytes. Uma vez que o comprimento do cabeçalho Ethernet é de 14bytes, o controlador precisa de armazenar o arranque do cabeçalho Ethernet no endereço alinhado de 2 bytes para garantir que o cabeçalho IP começa com um endereço alinhado de 4 bytes.