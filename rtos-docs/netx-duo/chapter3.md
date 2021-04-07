---
title: Capítulo 3 - Componentes funcionais do Azure RTOS NetX Duo
description: Este capítulo contém uma descrição da pilha Azure RTOS NetX Duo TCP/IP de uma perspetiva funcional.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 31900c7b822c88079e4b9fe28a8a388d20f819aa
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/07/2021
ms.locfileid: "106549849"
---
# <a name="chapter-3---functional-components-of-azure-rtos-netx-duo"></a>Capítulo 3 - Componentes funcionais do Azure RTOS NetX Duo

Este capítulo contém uma descrição da pilha Azure RTOS NetX Duo TCP/IP de uma perspetiva funcional. 

## <a name="execution-overview"></a>Visão geral da execução

Existem cinco tipos de execução de programas dentro de uma aplicação NetX Duo: inicialização, chamadas de interface de aplicação, fio IP interno, temporizadores periódicos IP e o controlador de rede.

> [!NOTE]
> *A NetX Duo assume a existência da ThreadX e depende da sua execução de fios, suspensão, temporizadores periódicos e instalações de exclusão mútua.*

### <a name="initialization"></a>Inicialização

O serviço ***nx_system_initialize** _ deve ser chamado antes de qualquer outro serviço NetX Duo ser chamado. A inicialização do sistema pode ser chamada a partir da função ThreadX _ *_tx_application_define_** ou a partir de fios de aplicação.

Depois de ***nx_system_initialize** _ devoluções, o sistema está pronto para criar pacotes de piscinas e instâncias IP. Como a criação de uma instância IP requer um pacote de pacotes predefinidos, pelo menos um conjunto de pacotes NetX Duo deve existir antes de criar uma instância IP. A criação de piscinas de pacotes e instâncias IP são permitidas a partir da função de inicialização ThreadX _ *_tx_application_define_** e a partir de fios de aplicação.

Internamente, a criação de uma instância IP é realizada em duas partes: A primeira parte é feita no contexto do chamador, seja a partir de ***tx_application_define*** ou do contexto de um fio de aplicação. Isto inclui a criação da estrutura de dados IP e a criação de vários recursos IP, incluindo o fio IP interno. A segunda parte é executada durante a execução inicial a partir do fio IP interno. É aqui que o controlador de rede, fornecido durante a primeira parte da criação de IP, é chamado pela primeira vez. A chamada do controlador de rede a partir da linha IP interna permite ao condutor efetuar E/S e suspender durante o processamento de inicialização.

Quando o controlador de rede regressa do seu processamento de inicialização, a criação ip fica completa.

A inicialização do IPv6 na NetX Duo requer alguns serviços adicionais da NetX Duo. Estes são descritos em maior detalhe na secção [IPv6 na NetX Duo](#ipv6-in-netx-duo) mais tarde neste capítulo.

> [!NOTE]
> *O serviço NetX Duo **nx_ip_status_check** está disponível para obter informações sobre a instância IP e o seu estado de interface primária. Essas informações de estado incluem se o link é ou não inicializado, ativado e endereço IP é resolvido. Estas informações são utilizadas para sincronizar os fios de aplicação que precisam de utilizar uma instância IP recém-criada. Para sistemas multihomes, consulte [o Multihome Support](#multihome-support). **nx_ip_interface_status_check** está disponível para obter 3 informações sobre a interface especificada.*

### <a name="application-interface-calls"></a>Chamadas de Interface de Aplicação

As chamadas da aplicação são feitas em grande parte a partir de fios de aplicação que estão a ser geridos sob o ThreadX RTOS. No entanto, algumas inicializaçãos, criar e permitir serviços podem ser chamados a partir de ***tx_application_define***. As secções "Allowed From" [do Capítulo 4 - Descrição dos Serviços Azure RTOS NetX Duo](chapter4.md) indicam a partir do qual cada serviço NetX Duo pode ser chamado.

Na maior parte das vezes, o processamento de atividades intensivas, como as despesas de computação, é feito dentro do contexto do fio de chamada , sem bloquear o acesso de outros fios à instância IP. Por exemplo, na transmissão, o cálculo da UDP checksum é realizado dentro do serviço ***nx_udp_socket_send** _ , antes de ligar para a função de envio IP subjacente. Num pacote recebido, a conta de verificação da UDP é calculada no serviço _ *_nx_udp_socket_receive*_* executado no fio da aplicação. Isto ajuda a prevenir o bloqueio de pedidos de rede de fios de maior prioridade devido ao processamento de cálculo intensivo de checkum em fios de menor prioridade.

Valores, como endereços IP e números de porta, são passados para APIs em ordem byte de anfitrião. Internamente, estes valores também são armazenados na ordem byte de anfitrião. Isto permite que os desenvolvedores vejam facilmente os valores através de um depurar. Quando estes valores são programados num quadro para transmissão, são convertidos para ordem byte de rede.

### <a name="internal-ip-thread"></a>Fio IP interno

Como mencionado, cada instância IP na NetX Duo tem o seu próprio fio. A prioridade e o tamanho da pilha do fio IP interno é definido no serviço ***nx_ip_create.*** O fio IP interno é criado num modo pronto a executar. Se o fio IP tiver uma prioridade maior do que o fio de chamada, a pré-substituição pode ocorrer dentro da chamada de criação IP.

O ponto de entrada do fio IP interno encontra-se na função interna _ ***nx_ip_thread_entry***. Quando iniciado, o fio IP interno completa primeiro a inicialização do controlador de rede, que consiste em fazer três chamadas para o controlador de rede específico da aplicação. A primeira chamada é anexar o controlador de rede à instância IP, seguida de uma chamada de inicialização, que permite ao controlador de rede passar pelo processo de inicialização. Após o retorno do controlador de rede da inicialização (pode suspender-se enquanto aguarda a instalação correta do hardware), o fio IP interno volta a ligar para o controlador de rede para ativar a ligação. Após a retorna do controlador de rede a partir da chamada de ativação de ligação, o fio IP interno introduz uma verificação de loop para sempre para vários eventos que precisam de ser processados para esta instância IP. Os eventos processados neste ciclo incluem receção de pacotes IP diferidos, montagem de fragmentos de pacote IP, processamento de ping ICMP, processamento de IGMP, processamento de fila de pacotes TCP, processamento periódico de TCP, intervalos de montagem de fragmentos IP e processamento periódico IGMP. Os eventos incluem também atividades de resolução de endereços; Processamento de pacotes ARP e processamento periódico ARP em IPv4, Deteção de Endereços Duplicados, Solicitação de Router e Descoberta de Vizinhos no IPv6.

> [!CAUTION]
> *As funções de retorno netx Duo, incluindo chamadas de escuta e desconexão, são chamadas a partir do fio IP interno - e não do fio de chamada original. A aplicação deve ter o cuidado de não suspender dentro de qualquer função de retorno NetX Duo.*

### <a name="ip-periodic-timers"></a>Temporizadores periódicos IP

Existem dois temporizadores periódicos ThreadX utilizados para cada instância IP. O primeiro é um temporizador de um segundo para ARP, IGMP, TCP timeout, e também impulsiona o processamento de remontagem de fragmentos IP. O segundo temporizador é um temporizador de 100 ms para conduzir o tempo de retransmissão TCP e as operações relacionadas com o IPv6.

### <a name="network-driver"></a>Controlador de rede

Cada instância IP no NetX Duo tem uma interface primária, que é identificada pelo seu controlador de dispositivos especificado no serviço ***nx_ip_create.*** O controlador de rede é responsável pelo tratamento de vários pedidos da NetX Duo, incluindo transmissão de pacotes, receção de pacotes e pedidos de estado e controlo. 

Para um sistema multi-casa, a instância IP tem múltiplas interfaces, cada uma com um controlador de rede associado que executa estas tarefas para a respetiva interface.

O controlador da rede também deve lidar com eventos assíncronos que ocorrem nos meios de comunicação. Eventos assíncronos dos meios de comunicação incluem receção de pacotes, conclusão da transmissão de pacotes e alterações de estado. A NetX Duo fornece ao controlador de rede várias funções de acesso para lidar com vários eventos. Estas funções foram concebidas para serem chamadas a partir da parte de rotina de serviço de interrupção do controlador de rede. Para as redes IPv4, o controlador de rede deve encaminhar todos os pacotes ARP recebidos para a função interna ***_nx_arp_packet_deferred_receive.*** Todos os pacotes RARP devem ser encaminhados para ***_nx_rarp_packet_deferred_receive** _ função interna. Existem duas opções para pacotes IP. Se for necessária uma expedição rápida dos pacotes IP, os pacotes IP de entrada devem ser encaminhados para _ *_nx_ip_packet_receive_* _ para processamento imediato. Isto melhora consideravelmente o desempenho da NetX Duo no manuseamento de pacotes IP. Caso contrário, o encaminhamento dos pacotes IP para _ *_ _nx_ip_packet_deferred_receive_** deve ser feito. Este serviço coloca o pacote IP na fila de processamento diferida, onde é depois manuseado pela linha IP interna, o que resulta na menor quantidade de tempo de processamento do ISR.

O controlador de rede também pode adiar o processamento de interrupção para ficar sem o contexto do fio IP. Neste modo, o ISR deve guardar as informações necessárias, ligar para a função interna ***_nx_ip_driver_deferred_processing***, e reconhecer o controlador de interrupção. Este serviço notifica a linha IP para agendar uma chamada ao controlador do dispositivo para completar o processo do evento que causa a interrupção.

Alguns controladores de rede são capazes de executar a computação e validação de checkum de cabeçalho TCP/IP em hardware, sem ocupar recursos valiosos da CPU. Para tirar partido da funcionalidade de capacidade de hardware, o NetX Duo oferece opções para ativar ou desativar vários cálculos de verificação de software no momento da compilação, bem como ligar ou desligar a computação checkum no tempo de execução, se o controlador do dispositivo for capaz de comunicar com a camada IP sobre as capacidades de hardware. Consulte [o Capítulo 5 - Azure RTOS NetX Duo Network Drivers](chapter5.md) para obter informações mais detalhadas sobre a escrita dos controladores de rede NetX Duo.

### <a name="multihome-support"></a>Suporte Multihome

O NetX Duo suporta sistemas ligados a múltiplos dispositivos físicos utilizando uma única instância IP. Cada interface física é atribuída a um bloco de controlo de interface na instância IP. As aplicações que desejem utilizar um sistema multihome devem definir o valor para ***NX_MAX_PHSYCIAL_INTERFACES** _ ao número de dispositivos físicos ligados ao sistema e reconstruir a biblioteca NetX Duo. Por predefinição ,*_o NX_MAX_PHYSICAL_INTERFACES_** está definido para um, criando um bloco de controlo de interface na instância IP.

A aplicação NetX Duo cria uma única instância IP para o dispositivo primário utilizando o serviço ***nx_ip_create** _ . Para cada dispositivo de rede adicional, a aplicação liga o dispositivo à instância IP utilizando o serviço _ *_nx_ip_interface_attach_** .

Cada estrutura de interface de rede contém um subconjunto de informações de rede sobre a interface de rede que está contida no bloco de controlo IP, incluindo endereço IPv4 de interface, máscara de sub-rede, tamanho IP MTU e informações de endereço de camada MAC.

> [!NOTE]
> *NetX Duo com suporte multihome é retrocompatível com versões anteriores do NetX Duo. Serviços que não levam informações de interface explícitas padrão ao dispositivo de rede primária.*

A interface primária tem índice zero na lista de instâncias IP. Cada dispositivo subsequente ligado à instância IP é atribuído o próximo índice.

Todos os serviços de protocolo de camada superior para os quais a instância IP está ativada, incluindo TCP, UDP, ICMP e IGMP, estão disponíveis para todos os dispositivos anexos.

Na maioria dos casos, o NetX Duo pode determinar o melhor endereço de origem a utilizar ao transmitir um pacote. A seleção do endereço de origem baseia-se no endereço de destino. Os serviços NetX Duo são adicionados para permitir que as aplicações especifiquem um endereço de origem específico para usar, nos casos em que o mais adequado não possa ser determinado pelo endereço de destino. Um exemplo seria num sistema multihome, uma aplicação precisa enviar um pacote para uma transmissão IPv4 ou endereços de destino multicast.

Os serviços especificamente para o desenvolvimento de aplicações multihomes incluem:

- *nx_igmp_multicast_interface_join*
- *nx_igmp_multicast_interface_leave*
- *nx_ip_driver_interface_direct_command*
- *nx_ip_interface_address_get*
- *nx_ip_interface_address_mapping_configure*
- *nx_ip_interface_address_set*  
- *nx_ip_interface_attach*
- *nx_ip_interface_capability_get* 
- *nx_ip_interface_capability_set*
- *nx_ip_interface_detach*
- *nx_ip_interface_info_get*
- *nx_ip_interface_mtu_set*
- *nx_ip_interface_physical_address_get*
- *nx_ip_interface_physical_address_set*
- *nx_ip_interface_status_check*
- *nx_ip_raw_packet_source_send*
- *nx_ipv4_multicast_interface_join*
- *nx_ipv4_multicast_interface_leave*
- *nx_udp_socket_source_send*
- *nxd_ipv6_multicast_interface_join*
- *nxd_ipv6_multicast_interface_leave* 
- *nxd_udp_socket_source_send*
- *nxd_icmp_source_ping*
- *nxd_ip_raw_packet_source_send*
- *nxd_udp_socket_source_send*

Estes serviços são explicados em maior detalhe na [Descrição dos Serviços NetX Duo.](chapter4.md)

### <a name="loopback-interface"></a>Loopback Interface

A interface loopback é uma interface de rede especial sem uma ligação física anexada. A interface loopback permite que as aplicações comuniquem utilizando o endereço de backback IPv4 127.0.0.0.1 Para utilizar uma interface de loopback lógica, certifique-se de que a opção configurável ***NX_DISABLE_LOOPBACK_INTERFACE*** não está definida.

### <a name="interface-control-blocks"></a>Blocos de controlo de interface

O número de blocos de controlo de interface na instância IP é o número de interfaces físicas (definidas por ***NX_MAX_PHYSICAL_INTERFACES** _) mais a interface loopback se estiver ativada. O número total de interfaces é definido em _*_NX_MAX_IP_INTERFACES_**.

## <a name="protocol-layering"></a>Camada de protocolo

O TCP/IP implementado pela NetX Duo é um protocolo em camadas, o que significa que protocolos mais complexos são construídos em cima de protocolos subjacentes mais simples. No TCP/IP, o protocolo de camada mais baixo está ao nível da *ligação* e é manuseado pelo controlador de rede. Este nível é tipicamente direcionado para Ethernet, mas também pode ser fibra, série ou praticamente qualquer meio físico.

Em cima da camada de ligação está a *camada de rede.* Em TCP/IP, este é o IP, que é basicamente responsável por enviar e receber pacotes simples - de forma a melhor esforço - em toda a rede. Os protocolos de tipo de gestão como o ICMP e o IGMP são tipicamente também classificados como camadas de rede, mesmo que dependam de IP para envio e receção.

A *camada de transporte* assenta em cima da camada de rede. Esta camada é responsável pela gestão do fluxo de dados entre os anfitriões na rede. Existem dois tipos de serviços de transporte apoiados pela NetX Duo: UDP e TCP. Os serviços da UDP fornecem o melhor esforço de envio e receção de dados entre dois anfitriões de forma sem ligação, enquanto a TCP fornece um serviço fiável orientado para a ligação entre duas entidades hospedeiras.

Esta camada reflete-se nos pacotes de dados de rede reais. Cada camada em TCP/IP contém um bloco de informação chamado cabeçalho. Esta técnica de dados circundantes (e possivelmente informações protocolares) com um cabeçalho é tipicamente chamada de encapsulamento de dados. A figura 1 mostra um exemplo de camadas netX Duo e a Figura 2 mostra o encapsulamento de dados resultante para os dados da UDP que estão a ser enviados.

![Camada de protocolo](./media/user-guide/image12.jpg)

**FIGURA 1. Camada de protocolo**

## <a name="packet-pools"></a>Piscinas de Pacotes

A atribuição de pacotes de forma rápida e determinística é sempre um desafio nas aplicações de networking em tempo real. Com isto em mente, o NetX Duo fornece a capacidade de criar e gerir várias piscinas de pacotes de rede de tamanho fixo.

Como as piscinas de pacotes NetX Duo consistem em blocos de memória de tamanho fixo, nunca existem problemas internos de fragmentação. Claro, a fragmentação causa comportamentos que não são inerentemente indeterminados. Além disso, o tempo necessário para alocar e libertar um pacote NetX Duo equivale a uma simples manipulação de listas ligadas. Além disso, a atribuição de pacotes e alocação de acordos são feitas no chefe da lista disponível. Isto fornece o processamento de listas mais rápido possível.

![Encapsulamento de Dados da UDP](./media/user-guide/image13.png)

**FIGURA 2. Encapsulamento de Dados da UDP**

A falta de flexibilidade é tipicamente a principal desvantagem das piscinas de pacotes de tamanho fixo. Determinar o tamanho ideal da carga útil do pacote que também lida com o pacote de entrada na pior das hipóteses é uma tarefa difícil. Os pacotes NetX Duo abordam este problema com uma funcionalidade opcional chamada chaining de pacotes. Um pacote de rede real pode ser feito de um ou mais pacotes NetX Duo ligados entre si. Além disso, o cabeçalho do pacote mantém um ponteiro para a parte superior do pacote. À medida que os protocolos adicionais são adicionados, este ponteiro é simplesmente movido para trás e o novo cabeçalho é escrito diretamente na frente dos dados. Sem a tecnologia de pacote flexível, a pilha teria de alocar outro tampão e copiar os dados para um novo tampão com o novo cabeçalho, que está a processar intensivamente.

Uma vez que cada tamanho de carga útil do pacote é fixado para um determinado pacote, os dados da aplicação maiores do que o tamanho da carga útil exigiriam vários pacotes acorrentados em conjunto. Ao preencher um pacote com dados do utilizador, a aplicação utilizará o serviço ***nx_packet_data_append***. Este serviço move os dados da aplicação para um pacote. Em situações em que um pacote não é suficiente para guardar os dados dos utilizadores, os pacotes adicionais são atribuídos para armazenar dados do utilizador. Para utilizar acorrentado de pacotes, o condutor deve poder receber ou transmitir a partir de pacotes acorrentados.

Para sistemas incorporados que não necessitam de utilizar a funcionalidade de acorrentamento de pacotes, a biblioteca NetX Duo pode ser construída com ***NX_DISABLE_PACKET_CHAIN** _ para remover a lógica de acorrentamento do pacote. Note que a função de fragmentação e remontagem IP pode precisar de utilizar a função de pacote acorrentado. Portanto, definir _*_NX_DISABLE_PACKET_CHAIN_*_ requer _ *_NX_DISABLE_FRAGMENTATION_** também ser definido. 

Cada conjunto de memórias de pacotes NetX Duo é um recurso público. NetX Duo não coloca constrangimentos na forma como as piscinas de pacotes são usadas. 

### <a name="packet-pool-memory-area"></a>Área de memória da piscina de pacotes

A área de memória para a piscina de pacotes é especificada durante a criação. Tal como outras áreas de memória para objetos ThreadX e NetX Duo, pode ser localizado em qualquer lugar do espaço de endereço do alvo. 

Esta é uma característica importante devido à considerável flexibilidade que confere à aplicação. Por exemplo, suponha que um produto de comunicação tem uma área de memória de alta velocidade para tampão de rede. Esta área de memória é facilmente utilizada transformando-a num conjunto de memórias de pacotes NetX Duo.

### <a name="creating-packet-pools"></a>Criação de piscinas de pacotes

As piscinas de pacotes são criadas durante a inicialização ou durante o tempo de execução por fios de aplicação. Não existem limites no número de piscinas de memória de pacotes numa aplicação NetX Duo.

### <a name="dual-packet-pool"></a>Piscina dual pacote

Tipicamente, o tamanho da carga útil do pacote IP predefinido é grande o suficiente para acomodar o tamanho do quadro até à interface de rede MTU. Durante o funcionamento normal, o fio IP precisa de enviar mensagens como ARP, mensagens de controlo TCP, mensagens IGMP, mensagens ICMPv6. Estas mensagens utilizam os pacotes atribuídos a partir do conjunto de pacotes predefinidos na instância IP. Num sistema limitado pela memória, onde a quantidade de memória disponível para o pool de pacotes é limitada, utilizando uma piscina de um único pacote (com o grande tamanho de carga útil para corresponder ao tamanho MTU) pode não ser uma solução ideal. O NetX Duo permite a instalação de um conjunto auxiliar de pacotes, onde o tamanho da carga útil é menor. Uma vez instalado o pacote auxiliar, o fio do ajudante IP destinaria pacotes da piscina de pacotes predefinidos ou da piscina auxiliar, dependendo do tamanho da mensagem que transmite. Para uma piscina de pacotes auxiliares, um tamanho de carga útil de 200 bytes funcionaria com a maioria das mensagens que o fio do ajudante IP transmite.

Por defeito, a biblioteca NetX Duo é construída sem permitir a piscina de pacotes duplos. Para ativar a funcionalidade, construa a biblioteca com ***NX_DUAL_PACKET_POOL_ENABLE** _ definido. Em seguida, a piscina de pacotes auxiliares pode ser definida chamando _*_nx_ip_auxiliary_packet_pool_set_**.

Há também a opção de criar mais de um pacote de piscina. Por exemplo, um conjunto de pacotes de transmissão é criado com o tamanho ideal da carga útil para tamanhos de mensagem esperados. Um pacote de receção é criado no condutor com um tamanho de carga útil definido para o condutor MTU, uma vez que não se pode prever o tamanho dos pacotes recebidos.

### <a name="packet-header-nx_packet"></a>NX_PACKET cabeçalho do pacote   
Por predefinição, o NetX Duo coloca o cabeçalho do pacote imediatamente antes da área de carga do pacote. O conjunto de memórias de pacotes é basicamente uma série de pacotes, cabeçalhos seguidos imediatamente pela carga útil do pacote. O cabeçalho do pacote ***(NX_PACKET)*** e o layout da piscina do pacote estão representados na Figura 3.

Para o controlador de dispositivos de rede que seja capaz de realizar operações de cópia zero, normalmente o endereço inicial da área de carga útil do pacote está programado na lógica DMA. Certos motores DMA têm requisitos de alinhamento na área de carga útil. Para que o endereço de partida da área de carga se alinhe corretamente para o motor DMA ou para o funcionamento da cache, o utilizador pode definir o símbolo ***NX_PACKET_ALIGNMENT***.

> [!WARNING]
> *É importante que o controlador de rede utilize a função **nx_packet_transmit_release** quando a transmissão de um pacote estiver concluída. Esta função verifica se o pacote não faz parte de uma fila de saída TCP antes de ser realmente colocado de volta na piscina disponível.*

![Cabeçalho de pacote e layout de piscina de pacote](./media/user-guide/image14.jpg)

**FIGURA 3. Cabeçalho de pacote e layout de piscina de pacote**

Os campos do cabeçalho do pacote são definidos da seguinte forma. Note que esta tabela não é uma lista completa de todos os membros da estrutura *NX_PACKET.*

|Cabeçalho de pacote | Objetivo |
|---|---|
|***nx_packet_pool_owner***|Este campo aponta para a piscina de pacotes que detém este pacote em particular. Quando o pacote é lançado, é libertado para esta piscina em particular. Com a propriedade da piscina dentro de cada pacote, é possível que um datagrama abra por vários pacotes de várias piscinas de pacotes.|
|***nx_packet_next**|Este campo aponta para o próximo pacote dentro do mesmo quadro. Se o NU, não existem pacotes adicionais que fazem parte da moldura. Este campo também é utilizado para conter pacotes fragmentados até que todo o pacote possa ser remontado. é removido se _*_NX_DISABLE_PACKET_CHAIN_**é definido.|
|***nx_packet_last**|Este campo aponta para o último pacote dentro do mesmo pacote de rede. Se o NU, este pacote representa todo o pacote de rede. Este campo é removido se _*_NX_DISABLE_PACKET_CHAIN_**é definido.|
|***nx_packet_length** _| Este campo contém o número total de bytes em todo o pacote de rede, incluindo o total de todos os bytes em todos os pacotes acorrentados pelo membro _nx_packet_next*.|
|***nx_packet_ip_interface***| Este campo é o bloco de controlo de interface que é atribuído ao pacote quando é recebido pelo controlador de interface, e pela NetX Duo para pacotes de saída. Um bloco de controlo de interface descreve a interface, por exemplo, endereço de rede, endereço MAC, endereço IP e estado de interface, como ligação ativada e mapeamento físico necessário.|
|***nx_packet_data_start**| Este campo aponta para o início da área de carga física deste pacote. Não tem de ser imediatamente após o cabeçalho NX_PACKET, mas este é o padrão para o serviço _ *_nx_packet_pool_create*_*|
|***nx_packet_data_end**|Este campo aponta para o fim da área de carga física deste pacote. A diferença entre este campo e o campo _nx_packet_data_start* representa o tamanho da carga útil.|
|***nx_packet_prepend_ptr** _|Este campo aponta para a localização de onde os dados do pacote, quer o cabeçalho do protocolo, quer os dados reais, são adicionados à frente dos dados do pacote existentes (se houver) na área de carga útil do pacote. Deve ser maior ou igual à localização do ponteiro _nx_packet_data_start* e inferior ou igual ao *ponteiro nx_packet_append_ptr.*|
> [!CAUTION]
> *Por razões de desempenho, a NetX Duo assume que quando o pacote é passado para os serviços NetX Duo para transmissão, o ponteiro pré-end aponta para um endereço alinhado com palavras longas.*

| Cabeçalho de pacote | Objetivo |
|---|---|
|***nx_packet_append_ptr**|Este campo aponta para o fim dos dados atualmente na área de carga útil do pacote. Deve estar entre o local da memória apontado por _nx_packet_prepend_ptr* e *nx_packet_data_end.* A diferença entre este campo e o campo *nx_packet_prepend_ptr* representa a quantidade de dados neste pacote.|
|***nx_packet_packet_pad**|Estes campos definem o comprimento do acolchoamento em 4 bytes para alcançar o requisito de alinhamento desejado. Este campo é removido se _*_NX_PACKET_HEADER_PAD_*_ não estiver definido. _*_Alternativamente, NX_PACKET_ALIGNMENT_*_ pode ser usado em vez de definir _nx_packet_header_pad.*|

### <a name="packet-header-offsets"></a>Compensações do cabeçalho do pacote

O tamanho do cabeçalho do pacote é definido para permitir espaço suficiente para acomodar o tamanho do cabeçalho. O serviço ***nx_packet_allocate*** é utilizado para alocar um pacote e ajusta o ponteiro pré-final no pacote de acordo com o tipo de pacote especificado. O tipo de pacote diz ao NetX Duo a compensação necessária para inserir o cabeçalho do protocolo (como UDP, TCP ou ICMP) em frente aos dados do protocolo.

Os seguintes tipos são definidos no NetX Duo para ter em conta o cabeçalho IP e a camada física (Ethernet) no pacote. Neste último caso, presume-se que sejam 16 bytes tendo em consideração o alinhamento de 4 bytes necessário. Os pacotes IPv4 ainda estão definidos no NetX Duo para aplicações para alocar pacotes para redes IPv4. Note que se a biblioteca NetX Duo for construída com iPv6 ativado, os tipos de pacotes genéricos (como NX_IP_PACKET) são mapeados para a versão IPv6. Se a Biblioteca NetX Duo for construída sem iPv6 ativada, estes tipos genéricos de pacotes são mapeados para a versão IPv4.

A tabela a seguir mostra símbolos definidos com IPv6 ativado:

|**Tipo de pacote** |**Valor** |
|---|---|
|NX_IPv6_PACKET (NX_IP_PACKET) | 0x38 |
|NX_UDPv6_PACKET (NX_UDP_PACKET) |0x40 |
|NX_TCPv6_PACKET (NX_TCP_PACKET) |0x4c |
|NX_IPv4_PACKET |0x24 |
|NX_IPv4_UDP_PACKET |0x2c |
|NX_IPv4_TCP_PACKET |0x38 |

A tabela a seguir mostra símbolos definidos com IPv6 desativado:

|**Tipo de pacote** |**Valor** |
|---|---|
|NX_IPv4_PACKET (NX_IP_PACKET) |0x24 |
|NX_IPv4_UDP_PACKET (NX_UDP_PACKET) |0x2c |
|NX_IPv4_TCP_PACKET (NX_TCP_PACKET) |0x38 |

Note que estes valores mudarão se *NX_IPSEC_ENABLE* for definido. Para obter a aplicação utilizando o IPsec, consulte o Guia do Utilizador NetX Duo IPsec para obter mais informações.

### <a name="pool-capacity"></a>Capacidade da Piscina

O número de pacotes numa piscina de pacotes é uma função do tamanho da carga útil e do número total de bytes na área de memória fornecida à piscina de pacotes criar serviço. A capacidade da piscina é calculada dividindo o tamanho do pacote (incluindo o tamanho do cabeçalho NX_PACKET, o tamanho da carga útil e o alinhamento adequado) no número total de bytes na área de memória fornecida.

### <a name="payload-area-alignment"></a>Alinhamento da área de carga útil

O design da piscina de pacotes no NetX Duo suporta cópia zero. Ao nível do controlador do dispositivo, o controlador é capaz de atribuir a área de carga útil diretamente aos descritores tampão para a receção de dados. Por vezes, o motor DMA ou o mecanismo de sincronização de cache requerem que o endereço de partida da área de carga útil tenha um determinado requisito de alinhamento. Isto pode ser conseguido definindo o requisito de alinhamento desejado (in bytes) em ***NX_PACKET_ALIGNMENT***. Ao criar uma piscina de pacotes, o endereço inicial da área de carga útil irá alinhar-se a este valor. Por predefinição, o endereço inicial está alinhado com 4 bytes.

### <a name="thread-suspension"></a>Suspensão do fio

Os fios de aplicação podem suspender enquanto esperam por um pacote de uma piscina vazia. Quando um pacote é devolvido à piscina, o fio suspenso é dado este pacote e retomado.

Se várias linhas forem suspensas na mesma piscina de pacotes, elas retomadas na ordem em que foram suspensas (FIFO).

### <a name="pool-statistics-and-errors"></a>Estatísticas e erros da piscina

Se ativado, o software de gestão de pacotes NetX Duo acompanha várias estatísticas e erros que podem ser úteis à aplicação. São mantidas as seguintes estatísticas e relatórios de erro para os pools de pacotes:

- Pacotes totais em piscina
- Pacotes gratuitos na piscina
- Total de dotações de pacotes
- Pedidos de atribuição vazios da piscina
- Suspensões de atribuição vazias da piscina
- Lançamentos de pacotes inválidos

Todas estas estatísticas e relatórios de erro, com exceção da contagem total e gratuita de pacotes na piscina, são incorporados na biblioteca NetX Duo, a menos que ***NX_DISABLE_PACKET_INFO** _ seja definido. Estes dados estão disponíveis para a aplicação com o serviço _ *_nx_packet_pool_info_get*_*

### <a name="packet-pool-control-block-nx_packet_pool"></a>Bloco de controlo de piscina de pacote NX_PACKET_POOL

As características de cada conjunto de memória de pacotes encontram-se no seu bloco de controlo. Contém informações úteis, tais como a lista ligada de pacotes gratuitos, o número de pacotes gratuitos e o tamanho da carga útil para pacotes nesta piscina. Esta estrutura é definida no ficheiro ***nx_api.h.***

Os blocos de controlo da piscina de pacote podem ser localizados em qualquer lugar da memória, mas é mais comum fazer do bloco de controlo uma estrutura global definindo-o fora do âmbito de qualquer função.

## <a name="ipv4-protocol"></a>Protocolo IPv4

O componente de Protocolo de Internet (IP) da NetX Duo é responsável pelo envio e receção de pacotes IPv4 na Internet. No NetX Duo, é o componente em última instância responsável pelo envio e receção de mensagens TCP, UDP, ICMP e IGMP, utilizando o controlador de rede subjacente.

NetX Duo suporta o protocolo IPv4 (RFC 791) e o protocolo IPv6 (RFC 2460). Esta secção discute o IPv4. O IPv6 é discutido na próxima secção.

### <a name="ipv4-addresses"></a>Endereços IPv4

Cada anfitrião na Internet tem um identificador único de 32 bits chamado endereço IP. Existem cinco classes de endereços IPv4, conforme descrito na Figura 4. As gamas das cinco classes de endereços IPv4 são as seguintes:

|Classe|Intervalo|
|---|---|
|A |0.0.0.0 para 127.255.255.255|
|B |128.0.0.0 para 191.255.255.255|
|C |192.0.0.0 para 223.255.255.255|
|D |224.0.0.0 para 239.255.255.255|
|E |240.0.0.0 para 247.255.255.255|

![Diagrama da Estrutura de Endereços IPv4.](./media/user-guide/ipv4-address-structure.png)

### <a name="figure-4-ipv4-address-structure"></a>FIGURA 4. Estrutura de endereços IPv4

Existem também três tipos de especificações de endereços: *unicast,* *transmissão* e *multicast.* Os endereços unicast são os endereços IPv4 que identificam um anfitrião específico na Internet. Os endereços Unicast podem ser uma fonte ou um endereço IPv4 de destino. Um endereço de transmissão identifica todos os anfitriões numa rede ou sub-rede específica e só pode ser usado como endereços de destino. Os endereços de transmissão são especificados tendo a parte de identificação do anfitrião do endereço definida para os outros. Endereços multicast (Classe D) especificam um grupo dinâmico de anfitriões na Internet. Os membros do grupo multicast podem juntar-se e sair quando quiserem.

> [!IMPORTANT]
> *Apenas protocolos sem ligação como o UDP sobre o IPv4 podem utilizar a transmissão e a capacidade de transmissão limitada do grupo multicast.*

> [!IMPORTANT]
> *O *IP_ADDRESS* macro é definido em ***nx_api.h** _. Permite uma especificação fácil dos endereços IPv4 utilizando vírgulas em vez de um período. Por exemplo, _IP_ADDRESS (128,0,0,0)* especifica o endereço da primeira classe B mostrado na Figura 4.*

### <a name="ipv4-gateway-address"></a>Endereço IPv4 Gateway

Os gateways de rede ajudam os anfitriões nas suas redes a transmitir pacotes destinados a destinos fora do domínio local. Cada nó tem algum conhecimento de qual próximo salto enviar para, seja o destino de um dos seus vizinhos, ou através de uma mesa de encaminhamento estático pré-programada. No entanto, se estas abordagens falharem, o nó deve encaminhar o pacote para o seu gateway predefinido, que tem um melhor conhecimento sobre como encaminhar o pacote para o seu destino. Note que o gateway predefinido deve ser diretamente acessível através de uma das interfaces físicas anexas à instância IP. A aplicação chama ***nx_ip_gateway_address_set** _ para configurar o endereço de gateway padrão IPv4. Utilize o _*_nx_ip_gateway_address_get_*_ de serviço para recuperar as atuais definições de gateway IPv4. A aplicação deve utilizar o serviço _ *_nx_ip_gateway_address_clear_** para limpar a definição do gateway.

### <a name="ipv4-header"></a>Cabeçalho IPv4

Para que qualquer pacote IPv4 seja enviado na Internet, deve ter um cabeçalho IPv4. Quando os protocolos de nível superior (UDP, TCP, ICMP ou IGMP) ligam para o componente IP para enviar um pacote, o módulo de transmissão IPv4 coloca um cabeçalho IPv4 à frente dos dados. Inversamente, quando os pacotes IP são recebidos da rede, o componente IP remove o cabeçalho IPv4 do pacote antes da entrega aos protocolos de nível superior. A figura 5 mostra o formato do cabeçalho IP.

![Formato iPv4 header](./media/user-guide/ipv4-header-format.png)

### <a name="figure-5-ipv4-header-format"></a>FIGURA 5. Formato iPv4 header

> [!IMPORTANT]
> *Espera-se que todos os cabeçalhos na implementação TCP/IP estejam em grande formato **endiano.** Neste formato, o byte mais significativo da palavra reside no endereço byte mais baixo. Por exemplo, a versão de 4 bits e o comprimento do cabeçalho de 4 bits do cabeçalho IP devem ser localizados no primeiro byte do cabeçalho.*

Os campos do cabeçalho IPv4 são definidos da seguinte forma:

|Campo de &nbsp; cabeçalho IPv4 &nbsp; |Objetivo |
|---|---|
|***Versão de 4 bits*** |Este campo contém a versão de IP que este cabeçalho representa. Para a versão IP 4, que é o que o NetX Duo suporta, o valor deste campo é 4. |
|***Comprimento do cabeçalho de 4 bits*** |Este campo especifica o número de palavras de 32 bits no cabeçalho IP. Se não houver palavras de opção, o valor para este campo é 5. |
|***Tipo de serviço de 8 bits (TOS)*** |Este campo especifica o tipo de serviço solicitado para este pacote IP. Os pedidos válidos são os seguintes:<br />- Normal: 0x00 <br />- Atraso mínimo: 0x00<br />- Dados Máximos: 0x08<br />- Fiabilidade máxima: 0x04<br />- Custo Mínimo: 0x02 |
|***Comprimento total de 16 bits*** |Este campo contém o comprimento total do datagrama IP em bytes, incluindo o cabeçalho IP. Um datagrama IP é a unidade básica de informação encontrada numa Internet TCP/IP. Contém um endereço de destino e origem para além dos dados. Por ser um campo de 16 bits, o tamanho máximo de um datagrama IP é de 65.535 bytes.|
|***Identificação de 16 bits*** |O campo é um número usado para identificar exclusivamente cada datagrama IP enviado de um anfitrião. Este número é tipicamente incrementado após o envio de um datagrama IP. É especialmente útil na montagem de fragmentos de pacotes IP recebidos.|
|***Bandeiras de 3 bits*** |Este campo contém informações de fragmentação IP. O bit 14 é a parte do "não se fragmentar". Se esta bit estiver definida, o datagrama ip de saída não será fragmentado. O bit 13 é a parte "mais fragmentos". Se esta parte estiver definida, há mais fragmentos. Se esta parte estiver clara, este é o último fragmento do pacote IP.|
|***Compensação de fragmentos de 13 bits*** |Este campo contém os 13 bits superiores da offset do fragmento. Por causa disso, as compensações de fragmentos só são permitidas em limites de 8 bytes. O primeiro fragmento de um datagrama ip fragmentado terá o conjunto de bits "mais fragmentos" e terá uma compensação de 0.|
|***8 bits de tempo para viver (TTL)*** |Este campo contém o número de routers que este datagrama pode passar, o que basicamente limita o tempo de vida útil do datagrama.|
|***Protocolo de 8 bits***|Este campo especifica qual o protocolo que está a utilizar o datagrama IP. Segue-se uma lista de protocolos válidos e seus valores:<br />- ICMP: 0x01 <br />- IGMP: 0x02<br />- TCP: 0X06<br />- UDP: 0X11 |
|***Cheque de 16 bits*** |Este campo contém a parte de verificação de 16 bits que cobre apenas o cabeçalho IP. Existem despesas de verificação adicionais nos protocolos de nível superior que cobrem a carga útil ip. |
|***Endereço IP de origem de 32 bits*** |Este campo contém o endereço IP do remetente e é sempre um endereço de anfitrião. |
|***Endereço IP de destino de 32 bits*** |Este campo contém o endereço IP do recetor ou dos recetores se o endereço for um endereço transmitido ou multicast. |

### <a name="creating-ip-instances"></a>Criação de Instâncias IP

As instâncias IP são criadas durante a inicialização ou durante o tempo de execução por fios de aplicação. O endereço IPv4 inicial, máscara de rede, conjunto de pacotes predefinidos, controlador de mídia e memória e prioridade do fio IP interno são definidos pelo serviço ***nx_ip_create*** mesmo que a aplicação pretenda utilizar apenas as redes IPv6. Se a aplicação rubricar a instância IP com o seu endereço IPv4 definido para um endereço inválido (0.0.0.0), presume-se que o endereço de interface será resolvido por configuração manual mais tarde, via RARP, ou através de DHCP ou protocolos semelhantes.

Para sistemas com múltiplas interfaces de rede, a interface primária é designada ao chamar ***nx_ip_create** _. Cada interface adicional pode ser anexada à mesma instância IP chamando _*_nx_ip_interface_attach_**. Este serviço armazena informações sobre a interface de rede (como endereço IP, máscara de rede) no bloco de controlo de interface, e associa a instância do condutor ao bloco de controlo de interface na instância IP. Como o condutor recebe um pacote de dados, precisa de armazenar a informação da interface na estrutura NX_PACKET antes de reencaminhar para a lógica de receção IP. Note que uma instância IP já deve ser criada antes de anexar quaisquer interfaces.

Os serviços IPv6 não são iniciados depois de ligar ***nx_ip_create** _. As aplicações que desejem utilizar os serviços IPv6 devem ligar para o serviço _ *_nx_ipv6_enable_** para iniciar o IPv6.

Na rede IPv6, cada interface em instância IP pode ter vários endereços globais IPv6. Além de utilizar o DHCPv6 para a atribuição de endereços IPv6, um dispositivo também pode utilizar a Configuração automática do Endereço Apátrida. Mais informações estão disponíveis nas secções "Ip Control Block" e "Resolução de Endereços IPv6" mais tarde neste capítulo.

### <a name="ip-send"></a>IP Enviar

O processamento de envio IP em NetX Duo é muito simplificado. O ponteiro pré-final do pacote é movido para trás para acomodar o cabeçalho IP. O cabeçalho IP é preenchido (com todas as opções especificadas pela camada do protocolo de chamada), a estação de verificação IP é calculada em linha (apenas para pacotes IPv4), e o pacote é enviado para o controlador de rede associado. Além disso, a fragmentação de saída também é coordenada a partir do processamento de envio de IP.

Para o IPv4, a NetX Duo inicia pedidos de ARP se for necessário mapeamento físico para o endereço IP de destino. O IPv6 usa a Neighbor Discovery para mapeamento de endereços tofísicos iPv6.

> [!NOTE]
> *Para a conectividade IPv4, os pacotes que requerem resolução de endereço IP (isto é, mapeamento físico) são encadeados na fila ARP até que o número de pacotes em fila exceda a profundidade da fila ARP (definida pelo símbolo **NX_ARP_MAX_QUEUE_DEPTH).** Se a profundidade da fila for alcançada, o NetX Duo removerá o pacote mais antigo da fila e continuará à espera da resolução de endereços para os restantes pacotes encadeados. Por outro lado, se uma entrada ARP não for resolvida, os pacotes pendentes na entrada ARP são lançados após o tempo de entrada do ARP.*

Para sistemas com múltiplas interfaces de rede, o NetX Duo escolhe uma interface baseada no endereço IP de destino. Aplica-se o seguinte procedimento ao processo de seleção:

1. Se o remetente especificar uma interface de saída e a interface for válida, utilize essa interface.
2. Se um endereço de destino for emissão IPv4 ou multicast, a primeira interface física ativada é utilizada.
3. Se o endereço de destino for encontrado na tabela de encaminhamento estático, a interface associada ao gateway é utilizada.
4. Se o destino estiver ligado, a interface on-link é utilizada.
5. Se o endereço de destino for um endereço link-local (169.254.0.0/16), é utilizada a primeira interface válida.
6. Se o gateway predefinido estiver configurado, utilize a interface associada ao gateway predefinido para transmitir o pacote.
7. Finalmente, se um dos endereços IP de interface válido for o endereço link-local (169.254.0.0/16), esta interface é utilizada como endereço de origem para a transmissão.
8. O pacote de saída é largado se tudo acima falhar.

### <a name="ip-receive"></a>IP Receber

O processamento de receção IP é chamado do controlador de rede ou do fio IP interno (para processamento de pacotes na fila de pacotes recebidos diferidos). O processamento de receção IP examina o campo do protocolo e tenta enviar o pacote para o componente de protocolo adequado. Antes de o pacote ser realmente despachado, o cabeçalho IP é removido avançando o ponteiro pré-final para além do cabeçalho IP.

O processamento de receção IP também deteta pacotes IP fragmentados e executa as medidas necessárias para os remontar se a fragmentação estiver ativada. Se for necessária fragmentação, mas não ativada, o pacote é largado.

O NetX Duo determina a interface de rede adequada com base na interface especificada no pacote. Se a interface do pacote for NU, o NetX Duo desrescumula a interface primária. Isto é feito para garantir compatibilidade com os condutores legados NetX Duo Ethernet.

### <a name="raw-ip-send"></a>Envio de IP cru

Um pacote IP cru é um quadro IP que contém carga útil do protocolo de camada superior não suportado diretamente (e processado) por NetX Duo. Um pacote cru permite que os desenvolvedores definam as suas próprias aplicações baseadas em IP. Uma aplicação pode enviar pacotes IP crus diretamente utilizando o serviço ***nxd_ip_raw_packet_send** _ se o processamento de pacotes IP crus tiver sido ativado com o serviço _*_nx_ip_raw_packet_enabled._*_ Ao transmitir um pacote unicast numa rede IPv6, a NetX Duo determina automaticamente o melhor endereço IPv6 de origem para utilizar para enviar os pacotes, com base no endereço de destino. Se o endereço de destino for um endereço multicast (ou transmitido para IPv4), no entanto, o NetX Duo irá por defeito na primeira interface (primária). Portanto, para enviar esses pacotes em interfaces secundárias, a aplicação deve utilizar o serviço _ *_nx_ip_raw_packet_source_send_** para especificar o endereço de origem a utilizar para o pacote de saída.

### <a name="raw-ip-receive"></a>Receber IP cru

Se o processamento de pacotes IP cru estiver ativado, a aplicação pode receber pacotes IP crus através do serviço ***nx_ip_raw_packet_receive** _ . Todos os pacotes de entrada são processados de acordo com o protocolo especificado no cabeçalho IP. Se o protocolo especificar UDP, TCP, IGMP ou ICMP, a NetX Duo processará o pacote utilizando o manipulador apropriado para o tipo de protocolo de pacote. Se o protocolo não for um destes protocolos, e a receção ip bruta estiver ativada, o pacote de entrada será colocado na fila de pacotes brutos à espera que a aplicação o receba através do serviço _*_nx_ip_raw_packet_receive*_* Além disso, os fios de aplicação podem suspender com um intervalo opcional enquanto aguardam um pacote IP cru. O número de pacotes que podem ser colocados na fila de pacotes brutos é limitado. O valor máximo é definido em ***NX_IP_RAW_MAX_QUEUE_DEPTH,**_ cujo valor predefinido é de 20. Uma aplicação pode alterar o valor máximo chamando o serviço _ *_nx_ip_raw_receive_queue_max_set_** .

Em alternativa, a biblioteca NetX Duo pode ser construída com ***NX_ENABLE_IP_RAW_PACKET_FILTER*.** Neste modo de funcionamento, a aplicação fornece uma função de retorno que é invocada sempre que um pacote com um tipo de protocolo não manipulado é recebido. A lógica de receção IP encaminha o pacote para o pacote cru definido pelo utilizador receber a rotina do filtro. A rotina do filtro decide se mantém ou não o pacote cru para o processo futuro. O valor de retorno da rotina de retorno indica se o pacote foi processado pelo filtro de receção de pacote cru. Se o pacote for processado pela função de retorno, o pacote deve ser libertado após a aplicação ser feita com o pacote. Caso contrário, a NetX Duo é responsável pela libertação do pacote. Consulte a **_nx_ip_raw_packet_filter_set_** para obter mais informações sobre como utilizar a função de filtro de pacotes brutos.

> [!NOTE]
> *A função de invólucro BSD para NetX Duo baseia-se na função de filtro de pacotes brutos para manusear tomadas em bruto BSD. Por isso, para suportar a tomada em bruto no invólucro BSD, a biblioteca NetX Duo deve ser construída com ***NX_ENABLE_IP_RAW_PACKET_FILTER** _ definido, e a aplicação não deve usar o _*_nx_ip_raw_packet_filter_set_*_ para instalar o seu próprio filtro de pacote cru functions._

### <a name="default-packet-pool"></a>Piscina de pacotes predefinidos

Cada instância IP recebe um pacote de pacote padrão durante a criação. Esta piscina de pacotes é usada para alocar pacotes para ARP, RARP, ICMP, IGMP, vários pacotes de controlo TCP (SYN, ACK, e assim por diante), Neighbor Discovery, Router Discovery e Duplicate Address Detection. Se o pacote predefinido estiver vazio quando o NetX Duo precisar de alocar um pacote, o NetX Duo poderá ter de abortar a operação em particular e devolverá uma mensagem de erro se possível.

### <a name="ip-helper-thread"></a>Fio de ajudante IP

Cada instância IP tem um fio de ajuda. Este fio é responsável pelo manuseamento de todo o processamento de pacotes diferidos e de todo o processamento periódico. O fio do ajudante IP é criado em ***nx_ip_create.*** É aqui que o fio é dado a sua pilha e prioridade. Note que o primeiro processamento na linha de ajuda IP é terminar a inicialização do controlador de rede associada ao serviço de criação IP. Após a inicialização do controlador de rede estar concluída, o fio do ajudante inicia um ciclo interminável para processar pacotes e pedidos periódicos.

> [!IMPORTANT]
> *Se o comportamento inexplicável for visto dentro do fio do ajudante IP, aumentar o tamanho da pilha durante o serviço de criação IP é o primeiro passo de depurar. Se a pilha for muito pequena, o fio do ajudante IP pode estar a sobrepor-se à memória, o que pode causar problemas incomuns.*

### <a name="thread-suspension"></a>Suspensão do fio

Os fios de aplicação podem suspender enquanto tentam receber pacotes IP crus. Depois de recebido um pacote cru, o novo pacote é dado ao primeiro fio suspenso e esse fio é retomado. Os serviços da NetX Duo para receber pacotes têm um tempo de suspensão opcional. Quando um pacote é recebido ou o tempo limite expira, o fio de aplicação é retomado com o estado de conclusão adequado.

### <a name="ip-statistics-and-errors"></a>Estatísticas e erros ip

Se ativado, o Duo NetX regista várias estatísticas e erros que podem ser úteis à aplicação. As seguintes estatísticas e relatórios de erro são mantidos para cada instância DEP:

- Total de pacotes IP enviados
- Total de bytes IP enviados
- Total de pacotes IP recebidos
- Total de bytes IP recebidos
- Total de pacotes inválidos IP
- Total de pacotes de receção IP abandonados
- Total IP Receber Erros de Checkum
- Total IP Enviar Pacotes Abandonados
- Total de fragmentos ip enviados
- Total de fragmentos ip recebidos

Todas estas estatísticas e relatórios de erro estão disponíveis para a aplicação com o serviço ***nx_ip_info_get.***

### <a name="ip-control-block-nx_ip"></a>NX_IP do Bloco de Controlo IP

As características de cada instância IP encontram-se no seu bloco de controlo. Contém informações úteis, tais como endereços IP e máscaras de rede de cada dispositivo de rede, e uma tabela de IP vizinho e mapeamento de endereços de hardware físico. Esta estrutura é definida na _file ***nx_api.h.** Se o IPv6 estiver ativado, também contém um conjunto de endereços IPv6, número dos quais é especificado pela opção configurável do utilizador _*_NX_MAX_IPV6_ADDRESSES_**. O valor predefinido permite que cada interface de rede física tenha três endereços IPv6.

Os blocos de controlo de instância IP podem ser localizados em qualquer lugar da memória, mas é mais comum fazer do bloco de controlo uma estrutura global definindo-o fora do âmbito de qualquer função.

### <a name="static-ipv4-routing"></a>Encaminhamento estático IPv4

A funcionalidade de encaminhamento estático permite que uma aplicação especifique uma rede IPv4 e o próximo endereço de lúpulo para endereços IP específicos fora da rede. Se o encaminhamento estático estiver ativado, o NetX Duo procura através da tabela de encaminhamento estático para uma entrada correspondente ao endereço de destino do pacote a enviar. Se não for encontrado qualquer correspondência, o NetX Duo procura através da lista de interfaces físicas e escolhe um endereço IP de origem e próximo endereço de lúpulo baseado no endereço IP de destino e na máscara de rede. Se o destino não corresponder a nenhum dos endereços IP dos controladores de rede ligados à instância IP, o NetX Duo escolhe uma interface que está diretamente ligada ao gateway predefinido e utiliza o endereço IP da interface como endereço de origem, e o gateway predefinido como o próximo salto.

As entradas podem ser adicionadas e removidas da tabela de encaminhamento estático utilizando os serviços ***nx_ip_static_route_add** _ e _ *_nx_ip_static_route_delete_** respectivamente. Para utilizar o encaminhamento estático, a aplicação do anfitrião deve ativar esta função definindo ***NX_ENABLE_IP_STATIC_ROUTING.***

> [!NOTE]
> *Ao adicionar uma entrada na tabela de encaminhamento estático, o NetX Duo verifica uma entrada correspondente para o endereço de destino especificado já na tabela. Se existir, dá preferência à entrada com a rede mais pequena (prefixo mais longo) na máscara de rede.*

### <a name="ipv4-forwarding"></a>Encaminhamento IPv4

Se o pacote IPv4 de entrada não estiver destinado a este nó e a função de reencaminhamento IPv4 estiver ativada, a NetX Duo tenta encaminhar o pacote através das outras interfaces.  

### <a name="ip-fragmentation"></a>Fragmentação ip

O dispositivo de rede pode ter limites no tamanho dos pacotes de saída. Este limite é chamado de unidade de transmissão máxima (MTU). IP MTU é o maior tamanho de quadro IP que o controlador de camada de ligação é capaz de transmitir sem fragmentar o pacote IP. Durante uma fase de inicialização do controlador do dispositivo, o módulo do condutor deve configurar o seu tamanho IP MTU através do ***serviço nx_ip_interface_mtu_set.***

Embora não recomendado, a aplicação pode gerar datagramas maiores do que o IP MTU subjacente suportado pelo dispositivo. Antes de transmitir tais datagramas de IP, a camada IP deve fragmentar estes pacotes. Ao receber quadros IP fragmentados, a extremidade recetora deve armazenar todos os quadros IP fragmentados com o mesmo ID de fragmentação e montá-los em ordem. Se a lógica de receção ip não for capaz de recolher todos os fragmentos para restaurar o quadro IP original no tempo, todos os fragmentos são libertados. Cabe ao protocolo da camada superior detetar tal perda de pacote e recuperá-la.

A fragmentação do IP aplica-se tanto aos pacotes IPv4 como IPv6.

Para suportar a fragmentação e o funcionamento da fragmentação IP, o designer de sistema deve ativar a função de fragmentação IP no NetX Duo utilizando o serviço ***nx_ip_fragment_enable.*** Se esta função não estiver ativada, os pacotes IP fragmentados de entrada são descartados, bem como pacotes que excedam o MTU do controlador de rede.

> [!NOTE]
> *A lógica de fragmentação IP pode ser completamente removida definindo ***NX_DISABLE_FRAGMENTATION** _ ao construir a biblioteca NetX Duo. Ao fazê-lo, ajuda a reduzir o tamanho do código do NetX Duo. Note que, nesta situação, as funções de fragmentação/remontagem do IPv4 e do IPv6 são disabled._

> [!NOTE]
> *Se **NX_DISABLE_CHAINED_PACKET** estiver definido, a fragmentação ip deve ser desativada.*

> [!NOTE]
> *Numa rede IPv6, os routers não fragmentam um datagrama se o tamanho do datagrama exceder o seu tamanho mínimo de MTU. Por conseguinte, cabe ao dispositivo de envio determinar o mínimo MTU entre a fonte e o destino, e garantir que o tamanho do datagrama IP não exceda o caminho MTU. No NetX Duo, a descoberta IPv6 PATH MTU pode ser ativada através da construção da biblioteca NetX Duo com o símbolo **NX_ENABLE_IPV6_PATH_MTU_DISCOVERY** definido.*

## <a name="address-resolution-protocol-arp-in-ipv4"></a>Protocolo de Resolução de Endereços (ARP) no IPv4

O Protocolo de Resolução de Endereços (ARP) é responsável por mapear dinamicamente endereços IPv4 de 32 bits aos dos meios físicos subjacentes (RFC 826). Ethernet é o meio físico mais típico, e suporta endereços de 48 bits. A necessidade de ARP é determinada pelo controlador de rede fornecido ao serviço ***nx_ip_create** _ . Se for necessário um mapeamento físico, o controlador de rede deve utilizar o serviço _ *_nx_interface_address_mapping_needed_** para configurar corretamente a interface do controlador.

### <a name="arp-enable"></a>Ativar a ARP

Para que a ARP funcione corretamente, deve primeiro ser ativada pela aplicação com o serviço ***nx_arp_enable.*** Este serviço estabelece várias estruturas de dados para o processamento de ARP, incluindo a criação de uma área de cache ARP a partir da memória fornecida ao serviço de ativação ARP.

### <a name="arp-cache"></a>ARP Cache

A cache ARP pode ser vista como uma matriz de estruturas internas de dados de mapeamento ARP. Cada estrutura interna é capaz de manter a relação entre um endereço IP e um endereço de hardware físico. Além disso, cada estrutura de dados tem ponteiros de ligação para que possa fazer parte de várias listas ligadas.

A aplicação pode procurar um endereço IP a partir da cache ARP fornecendo o endereço MAC de hardware usando o serviço ***nx_arp_ip_address_find** _ se o mapeamento existir na tabela ARP. Da mesma forma, o serviço _ *_nx_arp_hardware_address_find_** devolve o endereço MAC para um determinado endereço IP.

### <a name="arp-dynamic-entries"></a>Entradas dinâmicas ARP

Por predefinição, o ARP permite que todas as entradas na cache ARP na lista de entradas ARP dinâmicas disponíveis. Uma entrada dinâmica de ARP é atribuída a partir desta lista pela NetX Duo quando é detetado um pedido de envio para um endereço IP não mapeado. Após a atribuição, a entrada ARP é configurada e um pedido ARP é enviado para os meios físicos.

Uma entrada dinâmica também pode ser criada pelo serviço ***nx_arp_dynamic_entry_set***.

> [!IMPORTANT]
> *Se todas as entradas ARP dinâmicas estiverem a ser utilizadas, a entrada ARP menos utilizada é substituída por um novo mapeamento.*

### <a name="arp-static-entries"></a>Entradas Estáticas ARP

A aplicação também pode configurar mapeamento ARP estático usando o ***nx_arp_static_entry_create** _service. Este serviço atribui uma entrada ARP da lista dinâmica de entrada ARP e coloca-a na lista estática com as informações de mapeamento fornecidas pela aplicação. As entradas ARP estáticas não estão sujeitas a reutilização ou envelhecimento. A aplicação pode eliminar uma entrada estática utilizando o serviço _*_nx_arp_static_entry_delete_*_. Para remover todas as entradas estáticas na tabela ARP, a aplicação pode utilizar o serviço _*_nx_arp_static_entries_delete_**.

### <a name="automatic-arp-entry"></a>Entrada Automática de ARP

NetX Duo grava o mapeamento IP/MAC do par após as respostas dos pares ao pedido de ARP. O NetX Duo também implementa a funcionalidade de entrada automática de ARP onde regista o mapeamento de endereços PEER/MAC com base em pedidos ARP não solicitados da rede. Esta funcionalidade permite que a tabela ARP seja povoada com informações de pares, reduzindo o atraso necessário para passar pelo ciclo de pedido/resposta ARP. No entanto, a desvantagem com a ativação automática do ARP é que a tabela ARP tende a encher-se rapidamente numa rede movimentada com muitos nós na ligação local, o que acabaria por levar à substituição da entrada do ARP.

Esta funcionalidade é ativada por padrão. Para desativá-la, a biblioteca NetX Duo deve ser compilada com o símbolo ***NX_DISABLE_ARP_AUTO_ENTRY*** definido.</p>

### <a name="arp-messages"></a>Mensagens ARP

Como mencionado anteriormente, uma mensagem de pedido ARP é enviada quando a tarefa IP deteta que o mapeamento é necessário para um endereço IP. Os pedidos de ARP são enviados periodicamente (a cada ***NX_ARP_UPDATE_RATE** _ segundos) até que seja recebida uma resposta ARP correspondente. Um total de _ *_NX_ARP_MAXIMUM_RETRIES_** pedidos de ARP são feitos antes da tentativa de ARP ser abandonada. Quando uma resposta ARP é recebida, as informações de endereço físico associados são armazenadas na entrada ARP que está na cache.

Para sistemas multihomes, o NetX Duo determina qual a interface para enviar os pedidos e respostas ARP com base no endereço de destino especificado.

> [!NOTE]
> *Os pacotes IP de saída são em fila enquanto o NetX Duo aguarda a resposta ARP. O número de pacotes IP de saída em fila é definido pela **NX_ARP_MAX_QUEUE_DEPTH** constante .*

A NetX Duo também responde aos pedidos de ARP de outros nós na rede local IPv4. Quando é feito um pedido de ARP externo que corresponde ao endereço IP atual da interface que recebe o pedido ARP, o NetX Duo constrói uma mensagem de resposta ARP que contém o endereço físico atual.

Os formatos de pedidos e respostas Ethernet ARP são mostrados na Figura 6 e são descritos abaixo.

| **Campo de Pedido/Resposta &nbsp;**         | **Objetivo**            |
| ---------------------------------- | ---------------------- |
| ***Endereço de destino Ethernet*** | Este campo de 6 bytes contém o endereço de destino para a resposta ARP e é uma transmissão (todas) para pedidos ARP. Este campo é configurado pelo controlador de rede. 
| ***Endereço de origem Ethernet***      | Este campo de 6 bytes contém o endereço do remetente do pedido ou resposta ARP e é criado pelo controlador de rede. |
| ***Tipo de quadro*** | Este campo de 2 bytes contém o tipo de quadro Ethernet presente e, para pedidos e respostas ARP, este é igual a 0x0806. Este é o último campo que o controlador de rede é responsável pela configuração. |
| ***Tipo de hardware*** | Este campo de 2 bytes contém o tipo de hardware, que é 0x0001 para o Ethernet. |
| ***Tipo de Protocolo*** | Este campo de 2 bytes contém o tipo de protocolo, que é 0x0800 para endereços IP. |
| ***Tamanho do hardware*** | Este campo de 1 byte contém o tamanho do endereço de hardware, que é 6 para endereços Ethernet. |

![Diagrama do Formato ARP Packet.](./media/user-guide/arp-packet-format.png)

**FIGURA 6. Formato de pacote ARP**

| Campo de Pedido/Resposta &nbsp; | Objetivo |
|---|---|
| ***Tamanho do protocolo*** | Este campo de 1 byte contém o tamanho do endereço IP, que é 4 para endereços IP. |
| ***Código de Operação*** | Este campo de 2 bytes contém a operação para este pacote ARP. Um pedido ARP é especificado com o valor de 0x0001, enquanto uma resposta ARP é representada por um valor de 0x0002. |
| ***Endereço Ethernet Ethernet*** | Este campo de 6 bytes contém o endereço Ethernet do remetente. |
| ***Endereço IP remetente*** | Este campo de 4 bytes contém o endereço IP do remetente. |
| ***Endereço Ethernet alvo*** | Este campo de 6 bytes contém o endereço Ethernet do alvo. |
| ***Endereço IP alvo*** | Este campo de 4 bytes contém o endereço IP do alvo. |

> [!NOTE]
> *Os pedidos e respostas da ARP são pacotes ao nível da Ethernet. Todos os outros pacotes TCP/IP são encapsulados por um cabeçalho de pacote IP.*

> [!NOTE]
> *Espera-se que todas as mensagens ARP na implementação TCP/IP estejam em grande formato **endiano.** Neste formato, o byte mais significativo da palavra reside no endereço byte mais baixo.*

### <a name="arp-aging"></a>Envelhecimento ARP

NetX suporta a invalidação de entrada ARP dinâmica automática. ***NX_ARP_EXPIRATION_RATE** _ especifica o número de segundos que um endereço IP estabelecido para mapeamento físico permanece válido. Após a expiração, a entrada ARP é removida da cache ARP. A próxima tentativa de envio para o endereço IP correspondente resultará num novo pedido de ARP. Definição _ *_NX_ARP_EXPIRATION_RATE_** a zero desativa o envelhecimento do ARP, que é a configuração padrão.

### <a name="arp-defend"></a>ARP Defender

Quando um pacote de resposta ARP ou ARP é recebido e o remetente tem o mesmo endereço IP, que entra em conflito com o endereço IP deste nó, a NetX Duo envia um pedido ARP para esse endereço como defesa. Se o pacote ARP de conflito for recebido mais de uma vez em 10 segundos, a NetX Duo não envia mais pacotes de defesa. O intervalo padrão de 10 segundos pode ser redefinido por ***NX_ARP_DEFEND_INTERVAL** _. Este comportamento segue a política especificada em 2.4(c) de RFC5227. Uma vez que o Windows XP ignora o anúncio do ARP como resposta para a sua sonda ARP, o utilizador pode definir _ *_NX_ARP_DEFEND_BY_REPLY_** para enviar a resposta ARP como defesa adicional.

### <a name="arp-statistics-and-errors"></a>Estatísticas e erros da ARP

Se ativado, o software ARP NetX Duo acompanha várias estatísticas e erros que podem ser úteis à aplicação. São mantidas as seguintes estatísticas e relatórios de erro para o processamento de ARP de cada IP:

- Total de pedidos de ARP enviados
- Total de pedidos de ARP recebidos
- Total de respostas ARP enviadas 
- Total de respostas ARP recebidas 
- Entradas dinâmicas totais do ARP 
- Total de entradas estáticas ARP 
- Total de entradas envelhecidas em ARP 
- Total de mensagens inválidas da ARP 

Todas estas estatísticas e relatórios de erro estão disponíveis para a aplicação com o serviço ***nx_arp_info_get.***

## <a name="reverse-address-resolution-protocol-rarp-in-ipv4"></a>Protocolo de Resolução de Endereços Reversos (RARP) no IPv4

O Protocolo de Resolução de Endereços Reversos (RARP) é o protocolo para solicitar a atribuição de rede dos endereços IP de 32 bits do anfitrião (RFC 903). Isto é feito através de um pedido RARP e continua periodicamente até que um membro da rede atribua um endereço IP à interface de rede de anfitrião numa resposta RARP. A aplicação cria uma instância IP pelo serviço ***nx_ip_create*** com um endereço IP zero. Se o RARP estiver ativado pela aplicação, pode utilizar o protocolo RARP para solicitar um endereço IP a partir do servidor de rede acessível através da interface que tem um endereço IP zero.

### <a name="rarp-enable"></a>Ativar RARP

Para utilizar o RARP, a aplicação deve criar a instância IP com um endereço IP de zero e, em seguida, ativar o RARP utilizando o serviço ***nx_rarp_enable***. Para os sistemas multihome, pelo menos um dispositivo de rede associado à instância IP deve ter um endereço IP de zero. O processamento rarp envia periodicamente mensagens de pedido rarp para o sistema NetX Duo que requer um endereço IP até que seja recebida uma resposta RARP válida com o endereço IP designado pela rede. Neste momento, o processamento de RARP está completo.

Depois de o RARP ter sido ativado, este é desativado automaticamente depois de resolvidos todos os endereços de interface. O pedido pode forçar a RARP a encerrar utilizando o serviço ***nx_rarp_disable***.

### <a name="rarp-request"></a>Pedido RARP

O formato de um pacote de pedido RARP é quase idêntico ao pacote ARP indicado na [Figura 6](#arp-messages). A única diferença é que o campo do tipo de fotogramas é 0x8035 e o campo *Código de Operação* é 3, designando um pedido RARP. Como mencionado anteriormente, os pedidos de RARP serão enviados periodicamente (a cada ***NX_RARP_UPDATE_RATE*** segundos) até que seja recebida uma resposta RARP com o endereço IP atribuído à rede.

> [!NOTE]
> *Espera-se que todas as mensagens RARP na implementação TCP/IP estejam em grande formato **endiano.** Neste formato, o byte mais significativo da palavra reside no endereço byte mais baixo.*

### <a name="rarp-reply"></a>Resposta RARP

As mensagens de resposta RARP são recebidas da rede e contêm o endereço IP atribuído à rede para este anfitrião. O formato de um pacote de resposta RARP é quase idêntico ao pacote ARP indicado na Figura 6. A única diferença é que o campo do tipo de fotogramas é 0x8035 e o campo *Código de Operação* é 4, que designa uma resposta RARP. Depois de recebido, o endereço IP é configurado no caso IP, o pedido periódico de RARP é desativado, e a instância IP está agora pronta para o funcionamento normal da rede.

Para os anfitriões multihome, o endereço IP é aplicado à interface de rede de pedidos. Se existirem outras interfaces de rede que ainda solicitam uma atribuição de endereço IP, o serviço raRP periódico continua até que todos os pedidos de endereço IP de interface sejam resolvidos.

> [!NOTE]
> *O pedido não deve utilizar a instância IP até que o processamento rarp esteja completo. O **nx_ip_status_check** pode ser utilizado por aplicações para aguardar a conclusão do RARP. Para sistemas multihome, a aplicação não deve utilizar a interface de pedido até que o processamento rarp esteja completo nessa interface. O estado do endereço IP no dispositivo secundário pode ser verificado com o serviço **nx_ip_interface_status_check.***

### <a name="rarp-statistics-and-errors"></a>Estatísticas e erros da RARP

Se ativado, o software RARP netx Duo acompanha várias estatísticas e erros que podem ser úteis à aplicação. São mantidas as seguintes estatísticas e relatórios de erro para o processamento de RARP de cada IP:

- Total de pedidos de RARP enviados
- Total de respostas rarp recebidas
- Total de mensagens inválidas da RARP

Todas estas estatísticas e relatórios de erro estão disponíveis para a aplicação com o serviço ***nx_rarp_info_get.***

## <a name="internet-control-message-protocol-icmp"></a>Protocolo de mensagem de controlo da Internet (ICMP)

O Protocolo de Mensagem de Controlo de Internet para IPv4 (ICMP) limita-se a passar informações de erro e controlo entre membros da rede IP. O Protocolo de Mensagem de Controlo de Internet para iPv6 (ICMPv6) também lida com informações de erro e controlo e é necessário para protocolos de resolução de endereços, tais como Duplicado Deteção de Endereços (DAD) e autoconfiguação de endereços apátridas.

Tal como a maioria das outras mensagens de camada de aplicação (por exemplo, TCP/IP), as mensagens ICMP e ICMPv6 são encapsuladas por um cabeçalho IP com a designação do protocolo ICMP (ou ICMPv6).

### <a name="icmp-statistics-and-errors"></a>Estatísticas e erros do ICMP

Se ativado, o NetX Duo regista várias estatísticas e erros do ICMP que podem ser úteis à aplicação. São mantidas as seguintes estatísticas e relatórios de erro para o processamento do ICMP de cada IP: 

- Total de pings ICMP enviados  
- Total de tempo de ping ICMP 
- Fios de ping total do ICMP suspensos 
- Total de respostas de ping do ICMP recebidas 
- Erros totais de verificação do ICMP 
- Total de mensagens não manipuladas do ICMP 

Todas estas estatísticas e relatórios de erro estão disponíveis para a aplicação com o serviço ***nx_icmp_info_get.***

## <a name="icmpv4-services-in-netx-duo"></a>Serviços ICMPv4 em NetX Duo

### <a name="icmpv4-enable"></a>ICMPv4 Ativar

Antes de as mensagens ICMPv4 poderem ser processadas pela NetX Duo, a aplicação deve ligar para o serviço ***nx_icmp_enable*** para permitir o processamento do ICMPv4. Depois disso, a aplicação pode emitir pedidos de ping e pacotes de ping de entrada no campo.  

### <a name="icmpv4-echo-request"></a>Pedido de Eco ICMPv4

Um pedido de eco é um tipo de mensagem ICMPv4 que é normalmente usada para verificar a existência de um nó específico na rede, identificado pelo seu endereço IP anfitrião. O comando de ping popular é implementado usando mensagens de pedido de eco/eco ICMP. Se o anfitrião específico estiver presente, a sua pilha de rede processa o pedido de ping e as respostas com uma resposta de ping. A Figura 7 detalha o formato de mensagem de ping ICMPv4.

![Mensagem de ping ICMPv4](./media/user-guide/icmpv4-ping-message.png)  

**FIGURA 7. Mensagem de ping ICMPv4**

> [!NOTE]
> *Espera-se que todas as mensagens ICMPv4 na implementação TCP/IP estejam em grande formato **endiano.** Neste formato, o byte mais significativo da palavra reside no endereço byte mais baixo.*

O seguinte descreve o formato do cabeçalho ICMPv4:

|Campo de Cabeçalho |Objetivo |
|---|---|
|**Tipo** |Este campo especifica a mensagem ICMPv4 (bits 31-24). Os mais comuns são:<br />- 0: Resposta do eco<br />- 3: Destino Inalcançável<br />- 8: Pedido de Eco<br />- 11: Tempo excedido<br />- 12: Problema dos parâmetros |
|**Código** |Este campo é de contexto específico no campo tipo (bits 23-16). Para um pedido de eco ou resposta, o código está definido para zero.|
|**Checkum** |Este campo contém a parte de verificação de 16 bits da soma complementar da mensagem ICMPv4, incluindo todo o cabeçalho ICMPv4 a começar pelo campo Tipo. Antes de gerar a caixa de verificação, o campo de verificação está limpo.|
|**Identificação** | Este campo contém um valor de identificação que identifica o hospedeiro; um hospedeiro deve utilizar o ID extraído de um pedido DE ECO na RESPOSTA ECHO (bits 31-16).|
|**Número de sequência** |Este campo contém um valor de ID; um hospedeiro deve utilizar o ID extraído de um pedido DE ECO na RESPOSTA ECHO (bits 31-16). Ao contrário do campo do identificador, este valor mudará num pedido de Eco subsequente do mesmo anfitrião (bits 15-0).|

### <a name="icmpv4-echo-response"></a>Resposta do Eco ICMPv4    
Uma resposta de ping é outro tipo de mensagem ICMP que é gerada internamente pela componente ICMP em resposta a um pedido externo de ping. Além do reconhecimento, a resposta ao ping contém também uma cópia dos dados do utilizador fornecidos no pedido de ping.

### <a name="icmpv4-error-messages"></a>Mensagens de erro ICMPv4   
As seguintes mensagens de erro ICMPv4 são suportadas no NetX Duo: 
- Destino Inacessível 
- Exceder o tempo 
- Problema de parâmetros

## <a name="internet-group-management-protocol-igmp"></a>Protocolo de Gestão do Grupo de Internet (IGMP)

O Protocolo de Gestão do Grupo internet (IGMP) fornece um dispositivo para comunicar com os seus vizinhos e seus routers que pretende receber, ou aderir, um grupo multicast IPv4 (RFC 1112 e RFC 2236). Um grupo multicast é basicamente uma coleção dinâmica de membros da rede e é representado por um endereço IP classe D. Os membros do grupo multicast podem sair a qualquer momento, e os novos membros podem aderir a qualquer momento. A coordenação envolvida na adesão e saída do grupo é da responsabilidade do IGMP.

> [!NOTE]
> *O IGMP é projetado apenas para grupos multicast IPv4. Não pode ser utilizado na rede IPv6.*

### <a name="igmp-enable"></a>IGMP Ativar     
Antes de qualquer atividade multicasting poder ocorrer no NetX Duo, a aplicação deve ligar para o ***serviço nx_igmp_enable.*** Este serviço realiza a inicialização básica do IGMP em preparação para pedidos multicast.

### <a name="multicast-ipv4-addressing"></a>Endereço IPv4 multicast  
Como mencionado anteriormente, os endereços multicast são, na verdade, endereços IP de classe D, tal como mostrado na [Figura 4](#ipv4-addresses). Os 28 bits inferiores do endereço classe D correspondem ao ID do grupo multicast. Existem uma série de endereços multicast pré-definidos; no entanto, o *endereço de todos os anfitriões* (244.0.0.1) é particularmente importante para o processamento do IGMP. O *endereço de todos os anfitriões* é utilizado pelos routers para consultar todos os membros multicasts para informar em que grupos multicast pertencem.  

### <a name="physical-address-mapping-in-ipv4"></a>Mapeamento de endereço físico no IPv4
Endereços multicast classe D mapeam diretamente para endereços físicos Ethernet variando de 01.00.5e.00.00.00 a 01.00.5e.7f.ff.ff. Os 23 bits inferiores do mapa de endereços multicast IP diretamente para os 23 bits inferiores do endereço Ethernet.

### <a name="multicast-group-join"></a>Grupo Multicast Junta-se
As aplicações que precisam de aderir a um determinado grupo multicast podem fazê-lo chamando o ***serviço nx_igmp_multicast_join.*** Este serviço acompanha o número de pedidos para se juntar a este grupo multicast. Se este for o primeiro pedido de candidatura para aderir ao grupo multicast, é enviado um relatório IGMP na rede primária indicando a intenção deste anfitrião de se juntar ao grupo. Em seguida, o controlador de rede é chamado a configurar para ouvir pacotes com o endereço Ethernet para este grupo multicast.

Num sistema multihome, se o grupo multicast estiver acessível através de uma interface específica, a aplicação utilizará o serviço ***nx_igmp_multicast_interface_join** _ em vez de _*_nx_igmp_multicast_join_**, que se limita a grupos multicast na rede primária.

### <a name="multicast-group-leave"></a>Licença de grupo multicast   
As aplicações que necessitem de deixar um grupo multicast previamente aderido podem fazê-lo chamando o ***serviço nx_igmp_multicast_leave.*** Este serviço reduz a contagem interna associada à quantidade de vezes que o grupo se juntou. Se não houver pedidos de participação pendentes para um grupo, o controlador de rede é chamado a desativar a audição de pacotes com o endereço Ethernet deste grupo multicast.

### <a name="multicast-loopback"></a>Multicast Loopback    
Um pedido pode pretender receber tráfego multicast originário de uma das fontes no mesmo nó. Isto requer que o componente multicast IP tenha o loopback ativado utilizando o serviço ***nx_igmp_loopback_enable***.

### <a name="igmp-report-message"></a>Mensagem de relatório IGMP      
Quando a aplicação se junta a um grupo multicast, uma mensagem de relatório IGMP é enviada através da rede para indicar a intenção do anfitrião de se juntar a um determinado grupo multicast. O formato da mensagem de relatório IGMP é mostrado na Figura 8. O endereço de grupo multicast é utilizado tanto para a mensagem de grupo na mensagem de relatório IGMP como para o endereço IP de destino.

Na figura acima (Figura 8), o cabeçalho IGMP contém uma versão/tipo de campo, resposta máxima

![Diagrama de uma mensagem de relatório IGMP.](./media/user-guide/image17.jpg)

**FIGURA 8. Mensagem de relatório IGMP**

tempo, um campo de verificação e um campo de endereços de grupo multicast. Para as mensagens IGMPv1, o campo Tempo de Resposta Máxima está sempre definido para zero, uma vez que este não faz parte do protocolo IGMPv1. O campo Tempo de Resposta Máxima é definido quando o anfitrião recebe uma mensagem IGMP tipo consulta e apurada quando um anfitrião recebe a mensagem do tipo Relatório de outro anfitrião, tal como definido pelo protocolo IGMPv2.

O seguinte descreve o formato do cabeçalho IGMP:

|Campo de Cabeçalho|Objetivo|
|---|---|
|**Versão** |Este campo especifica a versão IGMP (bits 31-28).|
|**Tipo** |Este campo especifica o tipo de mensagem IGMP (bits 27-24).|
|**Tempo máximo de resposta** |Não utilizado em IGMP v1. No IGMP v2 este campo serve como o tempo máximo de resposta.|
|**Checkum** |Este campo contém a parte de verificação de 16 bits da soma de complemento da mensagem IGMP a começar pela versão IGMP (bits 0-15)|
|**Endereço de grupo** |Endereço IP do grupo D de 32 bits|

As mensagens de relatório IGMP também são enviadas em resposta às mensagens de consulta IGMP enviadas por um router multicast. Os routers multicast enviam periodicamente mensagens de consulta para ver quais os anfitriões que ainda precisam de ser membros do grupo. As mensagens de consulta têm o mesmo formato que a mensagem IGMP Report mostrada na Figura 8. As únicas diferenças são que o tipo IGMP é igual a 1 e o campo de endereços de grupo está definido para 0. As mensagens de consulta IGMP são enviadas para o endereço IP *de todos os anfitriões* pelo router multicast. Um anfitrião que ainda deseja manter a adesão ao grupo responde enviando outra mensagem do IGMP Report.

> [!NOTE]
> *Espera-se que todas as mensagens na implementação TCP/IP estejam em grande formato **endiano.** Neste formato, o byte mais significativo da palavra reside no endereço byte mais baixo.*

### <a name="igmp-statistics-and-errors"></a>Estatísticas e erros do IGMP    
<th><p>Se ativado, o software NetX Duo IGMP acompanha várias estatísticas e erros que podem ser úteis à aplicação. São mantidas as seguintes estatísticas e relatórios de erro para o processamento de IGMP de cada IP: 

- Total de relatórios IGMP enviados 
- Total de consultas IGMP recebidas 
- Erros totais do IGMP Checksum 
- Total de grupos atuais do IGMP aderidos 

Todas estas estatísticas e relatórios de erro estão disponíveis para a aplicação com o serviço ***nx_igmp_info_get.*** 

### <a name="multicast-without-igmp"></a>Multicast sem IGMP  
A aplicação que espera o tráfego multicast IPv4 pode juntar-se a um endereço de grupo multicast sem invocar mensagens IGMP utilizando o serviço ***nx_ipv4_multicast_interface_join***. Este serviço instrui a camada IPv4 e o controlador de interface subjacente a aceitar pacotes do endereço multicast IPv4 designado. No entanto, não há mensagens de gestão do grupo IGMP enviadas ou processadas para este grupo.

A aplicação já não pretende receber tráfego do grupo pode utilizar o ***serviço nx_ipv4_multicast_interface_leave.***

## <a name="ipv6-in-netx-duo"></a>IPv6 em NetX Duo

### <a name="ipv6-addresses"></a>Endereços IPv6   
Os endereços IPv6 são 128 bits. A arquitetura do endereço IPv6 é descrita no RFC 4291. O endereço é dividido num prefixo que contém as partes mais significativas e um endereço de anfitrião contendo as partes inferiores. O prefixo indica o tipo de endereço e é aproximadamente o equivalente ao endereço de rede na rede IPv4.

O IPv6 tem três tipos de especificações de endereço: unicast, anycast (não suportado no NetX Duo) e multicast. Os endereços unicast são os endereços IP que identificam um anfitrião específico na Internet. Os endereços Unicast podem ser uma fonte ou um endereço IP de destino. Os endereços multicast especificam um grupo dinâmico de anfitriões na Internet. Os membros do grupo multicast podem juntar-se e sair quando quiserem.

O IPv6 não tem o equivalente ao mecanismo de transmissão IPv4. A capacidade de enviar um pacote para todos os anfitriões pode ser alcançada enviando um pacote para o link-local todos os anfitriões grupo multicast.

O IPv6 utiliza endereços multicast para executar os procedimentos de configuração automática de endereços vizinhos, router e apátrida.

Existem dois tipos de endereços unicast IPv6: link endereços locais, tipicamente construídos combinando o prefixo local de ligação bem conhecido com o endereço MAC interface, e endereços IP globais, que também tem a parte de prefixo e a parte de ID do anfitrião. Um endereço global pode ser configurado manualmente, ou através da configuração automática do endereço apátrida ou DHCPv6. NetX Duo suporta o endereço local de ligação e o endereço global.

Para acomodar os formatos IPv4 e IPv6, o NetX Duo fornece um novo tipo de dados, NXD_ADDRESS, para a detenção de endereços IPv4 e IPv6. A definição desta estrutura é mostrada abaixo. O campo de endereços é uma união de endereços IPv4 e IPv6.

```c
typedef struct NXD_ADDRESS_STRUCT
{
    ULONG nxd_ip_version;
    union
    {
        ULONG v4;
        ULONG v6[4];
    } nxd_ip_address;
} NXD_ADDRESS;
```

Na estrutura NXD_ADDRESS, o primeiro elemento, *nxd_ip_version,* indica a versão IPv4 ou IPv6. Os valores suportados são NX_IP_VERSION_V4 ou NX_IP_VERSION_V6. *nxd_ip_version* indica qual o campo da *união nxd_ip_address* a utilizar como endereço IP. Os serviços da API netX Duo normalmente levam um ponteiro para NXD_ADDRESS estrutura como argumento de entrada em vez do endereço IP ULONG (32 bit).

### <a name="link-local-addresses"></a>Link Endereços Locais     
Um endereço de link-local é válido apenas na rede local. Um dispositivo pode enviar e receber pacotes para outro dispositivo na mesma rede depois de lhe ser atribuído um endereço local de ligação válido. Uma aplicação atribui um endereço link-local ligando para o serviço NetX Duo ***nxd_ipv6_address_set,*** com o parâmetro de comprimento do prefixo definido para 10. A aplicação pode fornecer um endereço link-local para o serviço, ou pode simplesmente usar NX_NULL como endereço link-local e permitir que o NetX Duo construa um endereço link-local baseado no endereço MAC do dispositivo.

O exemplo a seguir instrui o NetX Duo a configurar o endereço link-local com um prefixo de 10 no dispositivo primário (índice 0) utilizando o seu endereço MAC:

```c
nxd_ipv6_address_set(ip_ptr, 0, NX_NULL, 10, NX_NULL);
```
No exemplo acima, se o endereço MAC da interface for 54:32:10:1A:BC:67, o endereço local de ligação correspondente seria:

```c
FE80::5632:10FF:FE1A:BC67
```
Note que a parte de ID do anfitrião do endereço IPv6 **(5632:10FF:FE1A:BC67)** é composta pelo endereço MAC de 6 bytes, com as seguintes modificações:

- **0xFFFE** inseridas entre byte 3 e byte 4 do endereço MAC
- A segunda parte mais baixa do primeiro byte do endereço MAC (bit U/L) está definida para 1

Consulte o RFC 2464 (Transmissão de Pacotes IPv6 através da Rede Ethernet) para obter mais informações sobre como construir a parte hospedeira de um endereço IPv6 a partir do seu endereço MAC de interface.

Existem alguns endereços multicast especiais para o envio de mensagens multicast para um ou mais anfitriões no IPv6:

| Group  | Endereço   | Descrição  |
|---|---|---|
|Todos os grupos de nós |**FF02::1** |Todos os anfitriões da rede local|
|Todos os routers grupo |**FF02::2** |Todos os routers da rede local|
|Nó solicitado |**FF02::1:FF00:0/104** |Explicado abaixo|

Um endereço multicast de nó solicitado visa anfitriões específicos na ligação local em vez de todos os anfitriões IPv6. Consiste no prefixo **FF02::1:FF00:0/104,** que é de 104 bits e os últimos 24 bits do endereço IPv6 alvo. Por exemplo, um endereço IPv6 **205B:209D:D028::F058:D1C8:1024** tem um endereço multicast solicitado de endereço **FF02::1:FFC8:1024**.

> [!IMPORTANT]
> *A notação do cólon duplo indica que os pedaços de intervenção são todos zeros. **FF02::1:FF00:0/104** totalmente expandido parece* **FF02:0000:0000:0000:000:0001:FF00:000:000:000**

### <a name="global-addresses"></a>Endereços Globais    
Um exemplo de um endereço global IPv6 é **2001:0123:4567:89AB:CDEF::1** NetX Duo armazena endereços IPv6 na estrutura NXD_ADDRESS. No exemplo abaixo, a variável NXD_ADDRESS **global_ipv6_address** contém um endereço IPv6 unicast. O exemplo a seguir demonstra que um dispositivo NetX Duo cria um endereço global IPv6 específico para o seu dispositivo primário:

```c
NXD_ADDRESS global_ipv6_address;
UINT        primary_interface_index = 0;

global_ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
global_ipv6_address.nxd_ip_address.v6[0] = 0x20010123;
global_ipv6_address.nxd_ip_address.v6[1] = 0x456789AB;
global_ipv6_address.nxd_ip_address.v6[2] = 0xCDEF0000;
global_ipv6_address.nxd_ip_address.v6[3] = 0x00000001;

status = nxd_ipv6_address_set(
            &ip_0,
            primary_interface_index,
            &global_ipv6_address,
            64,
            NX_NULL);
```
Note que o prefixo deste endereço IPv6 é **2001:0123:4567:89AB**, que tem 64 bits de comprimento e é um comprimento prefixo comum para endereços IPv6 unicast global no Ethernet.

A estrutura NXD_ADDRESS também possui endereços IPv4. Um endereço IP de **192.1.168.10** **(0xC001A80A)** armazenado em global_ipv4_address teria o seguinte layout de memória:

|Campo |Valor |
|---|---|
|versão global_ipv4_address.nxd_ip_ |NX_IP_VERSION_V4|
|global_ipv4_address.nxd_ip_address.v4 |0xC001A80A|

Quando uma aplicação passa um endereço para os serviços NetX Duo, o campo *nxd_ip_version* deve especificar a versão IP correta para o manuseamento adequado do pacote.

Para ser retrocompatível com as aplicações NetX existentes, a NetX Duo suporta todos os serviços NetX. Internamente, o NetX Duo converte o tipo de endereço IPv4 ULONG para um tipo de dados NXD_ADDRESS antes de reencaminho para o serviço NetX Duo.

O exemplo a seguir ilustra a semelhança e as diferenças entre serviços na NetX e netX Duo.

```c
/* Make a connection to the destination IPv4 address
   192.1.168.12 through an already created TCP socket bound
   to the well known HTTP port number 80. */

global_ipv4_address.nxd_ip_version = NX_IP_VERSION_V4;
global_ipv4_address.nxd_ip_address.v4 = 0xC001A80C;

nxd_tcp_client_socket_connect(&tcp_socket,
                              &global_ipv4_address,
                              port_number,
                              NX_WAIT_FOREVER);
```

Segue-se a API líquida equivalente:

```c
ULONG         server_ip = 0xC001A80C;
NX_TCP_SOCKET tcp_socket;
UINT          port_number = 80;

nx_tcp_client_socket_connect(&tcp_socket,
                             server_ip,
                             port_number,
                             NX_WAIT_FOREVER); 
```

> [!IMPORTANT]
> *Os desenvolvedores de aplicações são encorajados a usar a versão nxd destes APIs*.

### <a name="ipv6-default-routers"></a>Routers padrão IPv6    
O IPv6 usa um router predefinido para encaminhar pacotes para destinos offlink. O serviço NetX Duo ***nxd_ipv6_default_router_add*** permite que uma aplicação adicione um router IPv6 à tabela de routers predefinido. Consulte o capítulo 4 "Descrição dos Serviços" para serviços de router mais predefinidos oferecidos pela NetX Duo.  

Ao encaminhar os pacotes IPv6, o NetX Duo verifica primeiro se o destino do pacote está ligado. Caso contrário, o NetX Duo verifica a tabela de encaminhamento predefinido para um router válido para encaminhar o pacote off-link para.  

Para remover um router da tabela de routers predefinido IPv6, a aplicação deve utilizar o serviço ***nxd_ipv6_default_router_delete** _. Para obter entradas da tabela de routers predefinido IPv6, utilize o serviço _*_nxd_ipv6_default_router_entry_get_**.

### <a name="ipv6-header"></a>Cabeçalho IPv6    
O cabeçalho IPv6 foi modificado a partir do cabeçalho IPv4. Ao atribuir um pacote, o chamador especifica o protocolo de aplicação (por exemplo, UDP, TCP), tamanho tampão em bytes e limite de lúpulo.   

A figura 9 mostra o formato do cabeçalho IPv6 e a tabela lista os componentes do cabeçalho.

![Diagrama do formato do cabeçalho IPv6.](./media/user-guide/image18.png)

**FIGURA 9. Formato iPv6 Header**

|Cabeçalho IP | Objetivo |
|---|---|
|Versão |Campo de 4 bits para a versão IP. Para as redes IPv6, o valor neste campo deve ser de 6; Para as redes IPv4 deve ser 4.|
|Classe de Tráfego |Campo de 8 bits que armazena a informação da classe de tráfego. Este campo não é utilizado pela NetX Duo.|
|Rótulo de fluxo |Campo de 20 bits para identificar exclusivamente o fluxo, se houver, com o qual um pacote está associado. Um valor de zero indica que o pacote não pertence a um fluxo específico. Este campo substitui o campo *TOS* no IPv4.|
|Comprimento da carga útil |Campo de 16 bits indicando a quantidade de dados nos bytes do pacote IPv6 após o cabeçalho de base IPv6. Isto inclui todos os cabeçalhos e dados do protocolo encapsulados.|
|Próximo Cabeçalho | Campo de 8 bits indicando o tipo do cabeçalho de extensão que segue o cabeçalho base IPv6. Este campo substitui o campo *Protocolo* no IPv4.|
|Limite de lúpulo |Campo de 8 bits que limita o número de routers que o pacote é permitido passar. Este campo substitui o campo *TTL* no IPv4.|
|Endereço de Origem |Campo de 128 bits que armazena o endereço IPv6 do remetente.|
|Endereço de destino |Campo de 128 bits que faz nerv6 do destino.|

### <a name="enabling-ipv6-in-netx-duo"></a>Ativar o IPv6 em NetX Duo    
Por padrão, o IPv6 está ativado no NetX Duo. Os serviços IPv6 estão ativados no NetX Duo se a opção configurável ***NX_DISABLE_IPV6** _ em _nx_user.h* não estiver definida. Se ***NX_DISABLE_IPV6*** estiver definido, o NetX Duo apenas oferecerá serviços IPv4, e todos os módulos e serviços relacionados com o IPv6 não estão integrados na biblioteca NetX Duo.

O seguinte serviço é fornecido para aplicações para configurar o endereço IPv6 do dispositivo: ***nxd_ipv6_address_set***

Além de configurar manualmente os endereços IPv6 do dispositivo, o sistema também pode utilizar a Configuração Automática de Endereços Apátridas. Para utilizar esta opção, a aplicação deve ligar ***nxd_ipv6_enable** _ para iniciar os serviços IPv6 no dispositivo. Além disso, os serviços ICMPv6 devem ser iniciados ligando para _*_nxd_icmp_enable,_*_ o que permite à NetX Duo realizar serviços como Solicitação router, Neighbor Discovery e Duplicate Address Detection. Note que _*_nx_icmp_enable_*_ só inicia o ICMP para os serviços IPv4. _*_nxd_icmp_enable_*_ inicia serviços ICMP tanto para iPv4 como IPv6. Se o sistema não necessitar de serviços ICMPv6, então _ *_nx_icmp_enable_** pode ser utilizado para que o módulo ICMPv6 não esteja ligado ao sistema.

O exemplo a seguir mostra um procedimento típico de inicialização NetX Duo IPv6.

```c
/* Assume ip_0 has been created and IPv4 services (such as ARP,
   ICMP, have been enabled. */
#define SECONDARY_INTERFACE 1

/* Enable IPv6 */
status = nxd_ipv6_enable(&ip_0);

if(status != NX_SUCCESS)
{
    /* nxd_ipv6_enable failed. */
}

/* Enable ICMPv6 */
status = nxd_icmp_enable(&ip_0);
if(status != NX_SUCCESS)
{
    /* nxd_icmp_enable failed. */
}

/* Configure the link local address on the primary interface. */
status = nxd_ipv6_address_set(&ip_0, 0, NX_NULL, 10, NX_NULL);

/* Configure ip_0 primary interface global address. */
ip_address.nxd_ip_version = NX_IP_VERSION_V6
ip_address.nxd_ip_address.v6[0] = 0x20010db8;
ip_address.nxd_ip_address.v6[1] = 0x0000f101;
ip_address.nxd_ip_address.v6[2] = 0;
ip_address.nxd_ip_address.v6[3] = 0x202;

/* Configure global address of the primary interface. */
status = nxd_ipv6_address_set(&ip_0, SECONDARY_INTERFACE,
                              &ip_address, 64, NX_NULL);
```                              

Os protocolos de camada superior (como TCP e UDP) podem ser ativados antes ou depois do início do IPv6.

> [!IMPORTANT]  
> *Os serviços IPv6 só estão disponíveis após a inicialção do fio IP e o dispositivo está ativado.*

Depois de a interface estar ativada (ou seja, o controlador do dispositivo de interface está pronto para enviar e receber dados, e foi obtido um endereço local de ligação válido), o dispositivo poderá obter endereços IPv6 globais por um destes métodos:

- Configuração de auto endereço apátrida;  
- Configuração manual do endereço IPv6;  
- Configuração de endereço via DHCPv6 (com pacote opcional DHCPv6)

Os dois primeiros métodos são descritos abaixo. O 3º método (DHCPv6) está descrito no pacote DHCP.

### <a name="stateless-address-autoconfiguration-using-router-solicitation"></a>Configuração automática de endereço apátrida usando solicitação do router      
Os dispositivos NetX Duo podem configurar automaticamente as suas interfaces quando ligados a uma rede IPv6 com um router que fornece informações prefixos. Os dispositivos que requerem configuração automática de endereços apátridas enviam mensagens de solicitação de router (RS). Os routers na rede respondem com mensagens de publicidade de router solicitadas (RA). As mensagens RA anunciam prefixos que identificam os endereços de rede associados a um link. Os dispositivos geram então um identificador único para a rede a que o dispositivo está ligado. O endereço é formado combinando o prefixo e o seu identificador único. Desta forma, ao receber as mensagens RA, os anfitriões geram o seu endereço IP. Os routers também podem enviar mensagens DE RA não solicitadas periódicas. 

> [!WARNING]
> *O NetX Duo permite uma aplicação para ativar ou desativar a configuração automática do endereço apátrida no tempo de execução. Para ativar esta funcionalidade, a biblioteca NetX Duo deve ser compilada com **NX_IPV6_STATELESS_AUTOCONFIG_CONTROL** definida. Uma vez ativada esta funcionalidade, as aplicações podem utilizar **nxd_ipv6_stateless_address_autoconfigure_enable** e **nxd_ipv6_stateless_address_autocofigure_disable** para ativar ou desativar o endereço apátrida IPv6 automaticamente configurar*.

### <a name="manual-ipv6-address-configuration"></a>Configuração manual do endereço IPv6     
Se for necessário um endereço IPv6 específico, a aplicação poderá utilizar ***nxd_ipv6_address_set*** para configurar manualmente um endereço IPv6. Uma interface de rede pode ter vários endereços IPv6. No entanto, tenha em mente que o número total de endereços IPv6 num sistema, obtido através da configuração automática do endereço apátrida, ou através da Configuração Manual, não pode exceder ***NX_MAX_IPV6_ADDRESSES***.

O exemplo a seguir ilustra como configurar manualmente um endereço global na interface primária (dispositivo 0) em ip_0:

```c
NXD_ADDRESS global_address;
global_address.nxd_ip_version = NX_IP_VERSION_V6;
global_address.nxd_ip_address.v6[0] = 0x20010000;
global_address.nxd_ip_address.v6[1] = 0x00000000;
global_address.nxd_ip_address.v6[2] = 0x00000000;
global_address.nxd_ip_address.v6[3] = 0x0000ABCD;
```

Em seguida, o anfitrião chama o seguinte serviço NetX Duo para atribuir este endereço como o seu endereço IP global:

```c
status = nxd_ipv6_address_set(&ip_0, 0,  
                              &global_address, 64
                              NX_NULL);
```

### <a name="duplicate-address-detection-dad"></a>Deteção de endereços duplicado (DAD)    
Depois de um sistema configurar o seu endereço IPv6, o endereço é marcado como *PROVISÓRIO*. Se a Duplicado Deteção de Endereços (DAD), descrita no RFC 4862, estiver ativada, a NetX Duo envia automaticamente mensagens de solicitação de vizinhos (NS) com este endereço provisório como destino. Se nenhum anfitrião na rede responder a estas mensagens NS num determinado período de tempo, o endereço é assumido como único na ligação local, e o seu estado transita para o estado VÁLIDO. Neste momento, a aplicação pode começar a utilizar este endereço IP para comunicação.  

A funcionalidade DAD faz parte do módulo ICMPv6. Por isso, a aplicação deve permitir serviços ICMPv6 antes que um endereço recém-configurado possa passar pelo processo DAD. Alternativamente, o processo DAD pode ser desligado definindo ***NX_DISABLE_IPV6_DAD** _ opção no ambiente de construção da biblioteca NetX Duo (definido como _*_nx_user.h)._*_ Durante o processo DAD, o parâmetro _*_NX_IPV6_DAD_TRANSMITS_*_ determina o número de mensagens NS enviadas pela NetX Duo sem receber uma resposta para determinar que o endereço é único. Por predefinição e recomendado pelo RFC 4862, _ *_NX_IPV6_DAD_TRANSMITS_** é definido em 3. Definir este símbolo a zero desativa eficazmente o PAI.

Se o ICMPv6 ou o DAD não estiverem ativados no momento em que a aplicação atribuir um endereço IPv6, o DAD não é realizado e o NetX Duo define imediatamente o estado do endereço IPv6 para VALID.

A NetX Duo não pode comunicar na rede IPv6 até que o seu endereço local e/ou global seja válido. Após a obtenção de um endereço válido, o NetX Duo tenta combinar o endereço de destino de um pacote de entrada com um dos seus endereços IPv6 configurados ou um endereço multicast ativado. Se não forem encontrados fósforos, o pacote é retirado. 

> [!WARNING]  
> *Durante o processo DAD, o número de pacotes DAD NS a transmitir é definido por ***NX_IPV6_DAD_TRANSMITS,**_que não chega a 3, e por padrão há um atraso de um segundo entre cada mensagem DAD NS é enviado. Portanto, num sistema com o PAI ativado, depois de atribuído um endereço IPv6 (e assumindo que este não é um endereço duplicado), há aproximadamente 3 segundos de atraso antes do endereço IP estar em estado VÁLIDO e estar pronto para comunicação._

As aplicações podem querer receber notificações quando os endereços IPv6 no sistema forem alterados. Para ativar a funcionalidade de notificação de alteração de endereço IPv6, a biblioteca NetX Duo deve ser construída com o símbolo **NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY** definido. Uma vez ativada a função, as aplicações podem instalar a função de retorno utilizando o serviço **_nxd_ipv6_address_change_notify._**

Uma vez que um endereço IPv6 é alterado ou se torna inválido, a função de retorno fornecida pelo utilizador é invocada com as seguintes informações:

| Função  | Descrição  |
|---|---|
|ip_ptr |Ponteiro para a instância IP|
|interface_index |Índice para a interface de rede que este endereço IPv6 está associado
|ipv6_addr_index |Índice para a tabela de endereços IPv6|
|ipv6_address |Ponteiro para o endereço IPv6, na forma de uma matriz de quatro inteiros ULONG. Os endereços Pv6 são apresentados em ordem byte de anfitrião.|

### <a name="ipv6-multicast-support-in-netx-duo"></a>Suporte multicast IPv6 na NetX Duo      
Os endereços multicast especificam um grupo dinâmico de anfitriões na Internet. Os membros do grupo multicast podem juntar-se e sair quando quiserem. A NetX Duo implementa vários protocolos ICMPv6, incluindo duplicado deteção de endereços, descoberta de vizinhos e discovery router, que requerem capacidade multicast IP. Por isso, a NetX Duo espera que o controlador do dispositivo subjacente suporte operações multicast.

Quando o NetX Duo precisa de se juntar ou sair de um grupo multicast (como o endereço multicast all-node e o endereço multicast *de nó solicitado),* emite um comando do controlador ao controlador do dispositivo para se juntar ou deixar um endereço MAC multicast. O comando do controlador para se juntar ao endereço multicast é ***NX_LINK_MULTICAST_JOIN** _. Para deixar um endereço multicast, a NetX Duo emite o comando do controlador _*_NX_LINK_MULTICAST_LEAVE_**. O controlador do dispositivo deve implementar estes dois comandos para que os protocolos ICMPv6 funcionem corretamente.

As aplicações podem aderir a um grupo multicast IPv6 utilizando o serviço ***nxd_ipv6_multicast_interface_join*.** Este serviço regista o endereço multicast com a pilha IP e, em seguida, notifica o controlador de dispositivo especificado do endereço multicast IPv6. Para deixar um grupo multicast, as aplicações utilizam o ***serviço nxd_ipv6_multicast_interface_leave.***

### <a name="neighbor-discovery-nd"></a>Neighbor Discovery (ND)    
Neighbor Discovery é um protocolo em redes IPv6 para mapear endereços físicos para os endereços IPv6 (endereço global ou endereço link-local). Este mapeamento é mantido na Cache de Descoberta do Vizinho (Cache ND). O processo ND é o equivalente ao processo ARP no IPv4, e a Cache ND é semelhante à tabela ARP. Um nó IPv6 pode obter o endereço MAC do seu vizinho usando o protocolo Neighbor Discovery (ND). Envia uma mensagem de solicitação de vizinho (NS) para o endereço multicast de nó solicitado e aguarda uma mensagem de anúncio de vizinho correspondente (NA). O endereço MAC obtido através deste processo é armazenado na Cache ND.

Cada instância IP tem uma cache ND. A Cache ND é mantida como um conjunto de entradas. O tamanho da matriz é definido no tempo de compilação, definindo a opção ***NX_IPV6_NEIGHBOR_CACHE_SIZE** _ que em _*_nx_user.h**._ Note que todas as interfaces anexas a uma instância IP partilham a mesma cache ND.

Toda a Cache ND está vazia quando o NetX Duo começar. À medida que o sistema funciona, o NetX Duo atualiza automaticamente a Cache ND, adicionando e eliminando as entradas de acordo com o protocolo ND. No entanto, uma aplicação também pode atualizar o Cache ND adicionando e eliminando manualmente as entradas de cache utilizando os seguintes serviços NetX Duo:

- ***nxd_nd_cache_entry_delete***  
- ***nxd_nd_cache_entry_set***   
- ***nxd_nd_cache_invalidate***

Ao enviar e receber pacotes IPv6, o NetX Duo atualiza automaticamente a tabela ND Cache.

## <a name="internet-control-message-protocol-in-ipv6-icmpv6"></a>Protocolo de mensagem de controlo da Internet em IPv6 (ICMPv6)  

O papel do ICMPv6 no IPv6 foi amplamente expandido para apoiar o mapeamento de endereços IPv6 e a descoberta do router. Além disso, o NetX Duo ICMPv6 suporta pedido e resposta de eco, relatórios de erro ICMPv6 e mensagens de redirecionamento ICMPv6.

### <a name="icmpv6-enable"></a>ICMPv6 Ativar    
Antes de as mensagens ICMPv6 poderem ser processadas pela NetX Duo, a aplicação deve ligar para o serviço ***nxd_icmp_enable*** para permitir o processamento do ICMPv6, conforme explicado anteriormente. 

### <a name="icmpv6-messages"></a>Mensagens ICMPv6     
A estrutura do cabeçalho ICMPv6 é semelhante à estrutura do cabeçalho ICMPv4. Como mostrado abaixo, o cabeçalho básico ICMPv6 contém os três campos, tipo, código e checkum, além do comprimento variável dos dados de opção ICMPv6. 

![Diagrama de um cabeçalho básico do ICMPv6.](./media/user-guide/image19.png)

**FIGURA 10. Cabeçalho Básico ICMPv6**

|Campo |Tamanho (bytes) |Descrição |
|-----|-----|-----|
|     | 1   |Identifica o tipo de mensagem ICMPv6; |
|     |     |1 Destino Inacessível |
|     |     |2 Pacote Muito Grande |
|     |     |3 Tempo Excedido |
|     |     |4 Problema de parâmetros |
|     |     |128 Pedido de Eco |
|     |     |129 Resposta de Eco |
|     |     |133 Solicitação do Router |
|     |     |134 Anúncio de Router |
|     |     |135 Solicitação de Vizinhos |
|     |     |136 Anúncio do Vizinho |
|     |     |137 Mensagem de Redirecionamento |
|Código | 1   |Qualifica ainda o tipo de mensagem ICMPv6. Geralmente usado com mensagens de erro. Se não for utilizado, está definido para zero. O pedido de eco/resposta e as mensagens NS não a utilizam.|
|Soma de verificação | 2 |Campo de verificação de 16 bits para o cabeçalho ICMP. Este é um complemento de 16 bits de toda a mensagem ICMPv6, incluindo o cabeçalho ICMPv6. Também inclui um pseudo-cabeçalho do endereço de origem IPv6, endereço de destino e comprimento de carga útil do pacote. |

Um exemplo do cabeçalho de solicitação do vizinho é mostrado abaixo.

![Diagrama de um exemplo cabeçalho solicitação de vizinho.](./media/user-guide/image20.jpg)

**FIGURA 11. Cabeçalho ICMPv6 para uma mensagem de solicitação do vizinho**

|Campo |Tamanho (bytes) |Descrição |
|-----|-----|-----|
|Tipo | 1   |Identifica o tipo de mensagem ICMPv6 para mensagens de solicitação de vizinhos. O valor é 135. |
|Código | 1   |Não usado. Pronto para 0. |
|Soma de verificação | 2  |Campo de verificação de 16 bits para o cabeçalho ICMPv6. |
|Reservado | 4  |4 bytes reservados definidos para 0. |
|Endereço-alvo | 16  |Endereço IPv6 do alvo da solicitação. Para a resolução de endereços IPv6, este é o endereço IP unicast real do dispositivo cujo endereço de camada de ligação precisa de ser resolvido. |
|Opções | Variável |Informação opcional especificada pelo Protocolo de Descoberta do Vizinho. |

### <a name="icmpv6-ping-request"></a>Pedido de ping ICMPv6
Nas aplicações NetX Duo utilizam ***nxd_icmp_ping*** para emitir pedidos de ping IPv6 ou IPv4, com base no endereço IP de destino especificado nos parâmetros.  

### <a name="icmpv6-ping-response"></a>Resposta ao ping ICMPv6
Uma resposta de ping ICMPv6 é outro tipo de mensagem ICMPv6 que é gerada internamente pela componente ICMPv6 em resposta a um pedido externo de ping ICMPv6. Além do reconhecimento, a resposta ao ping ICMPv6 contém também uma cópia dos dados do utilizador fornecidos no pedido de ping do ICMPv6.  

### <a name="thread-suspension"></a>Suspensão do fio
Os fios de aplicação podem ser suspensos enquanto tentam pingar outro membro da rede. Após a resposta ao ping ser recebida, a mensagem de resposta do ping é dada ao primeiro fio suspenso e esse fio é retomado. Como todos os serviços da NetX Duo, suspender um pedido de ping tem um tempo limite opcional.  

### <a name="other-icmpv6-messages"></a>Outras mensagens ICMPv6
São necessárias mensagens ICMPv6 para as seguintes funcionalidades:  

- Descoberta do Vizinho  
- Autoconfiguação de endereço apátrida 
- Descoberta do Router 
- Deteção de Inacessibilidade do Vizinho  

### <a name="neighbor-unreachability-router-and-prefix-discovery"></a>Inalabilidade do vizinho, router e prefix discovery    
Neighbor Unreachability Detection, Router Discovery e Prefix Discovery são baseados no protocolo Neighbor Discovery e são descritos abaixo. 

***Deteção de Inacessibilidade do Vizinho:*** Um dispositivo IPv6 procura a cache da Neighbor Discovery (ND) para o endereço da camada de ligação de destino quando deseja enviar um pacote. O destino imediato, por vezes referido como o "próximo salto", pode ser o destino real no mesmo link ou pode ser um router se o destino estiver fora de ligação. Uma entrada de cache ND contém o estado na capacidade de alcance de um vizinho.

Um estado de alcance indica que o vizinho é considerado acessível. Um vizinho está contactável se recebeu recentemente a confirmação de que os pacotes enviados para o vizinho foram recebidos. A confirmação no NetX Duo assume a forma de receber uma mensagem NA do vizinho em resposta a uma mensagem NS enviada pelo dispositivo NetX Duo. A NetX Duo também alterará o estado do estado do vizinho para REACHABLE se a aplicação ligar para o serviço NetX Duo ***nxd_nd_cache_entry_set*** para introduzir manualmente um registo de cache.

***Descoberta do Router:*** Um dispositivo IPv6 utiliza um router para encaminhar todos os pacotes destinados a destinos fora de ligação. Pode também utilizar informações enviadas pelo router, como mensagens de publicidade de router (RA), para configurar os seus endereços IPv6 globais.

Um dispositivo na rede pode iniciar o processo de Discovery router enviando uma mensagem de solicitação de router (RS) para o endereço multicast de todos os routers (FF01::2). Ou pode esperar no endereço multicast de todos os nós (FF::1) para um RA periódico dos routers.

Uma mensagem RA contém as informações de prefixo para configurar um endereço IPv6 para essa rede. No NetX Duo, a solicitação do router está por defeito ativada e pode ser desativada definindo a opção de configuração ***NX_DISABLE_ICMPV6_ROUTER_SOLICITATION** _ em _*_nx_user.h_**. Consulte as opções de configuração no capítulo "Instalação e Utilização da NetX Duo" para obter mais detalhes sobre a definição dos parâmetros de solicitação do router. 

***Prefix Discovery***: Um dispositivo IPv6 utiliza a descoberta do prefixo para saber quais os anfitriões-alvo que estão acessíveis diretamente sem passar por um router. Estas informações são disponibilizadas ao dispositivo IPv6 a partir de mensagens RA do router. O dispositivo IPv6 armazena a informação do prefixo numa tabela de prefixos. A descoberta do prefixo corresponde a um prefixo do prefixo do dispositivo IPv6 com um endereço alvo. Um prefixo corresponde a um endereço-alvo se todos os bits do prefixo corresponderem às partes mais significativas do endereço alvo. Se mais de um prefixo cobrir um endereço, o prefixo mais longo é selecionado.

### <a name="icmpv6-error-messages"></a>Mensagens de erro ICMPv6    
As seguintes mensagens de erro ICMPv6 são suportadas no NetX Duo:  

- Destino Inacessível  
- Pacote muito grande  
- Exceder o tempo  
- Problema de parâmetros  

## <a name="user-datagram-protocol-udp"></a>Protocolo de Datagrama do Utilizador (UDP)

O Protocolo de Datagrama do Utilizador (UDP) fornece a forma mais simples de transferência de dados entre membros da rede (RFC 768). Os pacotes de dados da UDP são enviados de um membro da rede para outro da melhor forma de esforço; ou seja, não existe um mecanismo incorporado para reconhecimento pelo destinatário do pacote. Além disso, o envio de um pacote UDP não requer qualquer ligação a ser estabelecida antecipadamente. Por causa disso, a transmissão de pacotes da UDP é muito eficiente.

Para os desenvolvedores que migram as suas aplicações NetX para o NetX Duo existem apenas algumas alterações básicas na funcionalidade UDP entre NetX e NetX Duo. Isto porque o IPv6 se preocupa principalmente com a camada ip subjacente. Todos os serviços netx Duo UDP podem ser usados para conectividade IPv4 ou IPv6.

### <a name="udp-header"></a>Cabeçalho UDP       
A UDP coloca um simples cabeçalho de pacote na frente dos dados da aplicação sobre a transmissão, e remove um cabeçalho UDP semelhante do pacote na receção antes de entregar um pacote UDP recebido à aplicação. O UDP utiliza o protocolo IP para o envio e receção de pacotes, o que significa que há um cabeçalho IP em frente ao cabeçalho da UDP quando o pacote está na rede. A figura 12 mostra o formato do cabeçalho UDP.

![Diagrama do formato do cabeçalho da UDP.](./media/user-guide/image21.png)

### <a name="figure-12-udp-header"></a>FIGURA 12. Cabeçalho UDP

> [!NOTE]
> *Espera-se que todos os cabeçalhos na implementação UDP/IP estejam em grande formato **endiano.** Neste formato, o byte mais significativo da palavra reside no endereço byte mais baixo.*

O seguinte descreve o formato do cabeçalho UDP:

|Campo de Cabeçalho |Objetivo |
|---|---|
|**Número de porta de 16 bits** |Este campo contém a porta de onde o pacote UDP está a ser enviado. As portas UDP válidas variam de 1 a 0xFFFF. |
|**Número da porta de destino de 16 bits** |Este campo contém a porta UDP para a qual o pacote está a ser enviado. As portas UDP válidas variam de 1 a 0xFFFF. |
|**Comprimento uDP de 16 bits** |Este campo contém o número de bytes no pacote UDP, incluindo o tamanho do cabeçalho UDP. |
|**16 bits UDP checksum** |Este campo contém a 16-bit checkum para o pacote, incluindo o cabeçalho UDP, a área de dados do pacote, e o cabeçalho pseudo IP. |

### <a name="udp-enable"></a>Ativação uDP   
Antes de a transmissão de pacotes da UDP ser possível, a aplicação deve primeiro permitir a UDP, ligando para o serviço ***nx_udp_enable.*** Depois de ativado, a aplicação é gratuita para enviar e receber pacotes UDP.  

### <a name="udp-socket-create"></a>Criação de tomada uDP    
As tomadas UDP são criadas durante a inicialização ou durante o tempo de funcionamento por fios de aplicação. O tipo inicial de serviço, tempo para viver e receber profundidade de fila são definidos pelo ***serviço nx_udp_socket_create.*** Não existem limites ao número de tomadas UDP numa aplicação.

### <a name="udp-checksum"></a>UDP Checksum   
O protocolo IPv6 requer um cálculo de verificação de cabeçalho UDP sobre os dados dos pacotes, enquanto no protocolo IPv4 é opcional.  

O UDP especifica a parte de verificação de 16 bits de um complemento que cobre o cabeçalho IP pseudo (composto pelo endereço IP de origem, endereço IP de destino e a palavra IP protocol/comprimento), o cabeçalho UDP e os dados do pacote UDP. As únicas diferenças entre as verificações de cabeçalho de pacote IPv4 e IPv6 UDP são que os endereços IP de origem e destino são de 32 bits no IPv4 enquanto no IPv6 são 128 bits. Se a úmis calculado da UDP for 0, é armazenada como todas (0xFFFF). Se a tomada de envio tiver a lógica de verificação UDP desativada, é colocado um zero no campo de verificação da UDP para indicar que a parte de verificação não foi calculada.

Se a sala de verificação UDP não corresponder à parte de verificação calculada pelo recetor, o pacote UDP é simplesmente descartado.

Na rede IPv4, a UDP checksum é opcional. O NetX Duo permite que uma aplicação permita ou desative o cálculo do UDP checkum numa base por tomada. Por predefinição, a lógica de verificação da tomada UDP está ativada. A aplicação pode desativar a lógica de checkum para uma determinada tomada UDP, chamando o serviço ***nx_udp_socket_checksum_disable** _ . No entanto, na rede IPv6, a UDP checksum é obrigatória. Portanto, o serviço _ *_nx_udp_socket_checksum_disable_** não desativaria a lógica de verificação da UDP ao enviar um pacote através da rede IPv6.

Certos controladores Ethernet são capazes de gerar o checkum uDP em movimento. Se o sistema for capaz de utilizar a funcionalidade de cálculo de checkum de hardware, a biblioteca NetX Duo pode ser construída sem a lógica de checkum. Para desativar a caixa de verificação de software UDP, a biblioteca NetX Duo deve ser construída com os seguintes símbolos definidos: ***NX_DISABLE_UDP_TX_CHECKSUM** _ e _*_NX_DISABLE_UDP_RX_CHECKSUM_*_ (descritos no Capítulo dois). As opções de configuração removem totalmente a lógica de verificação UDP do NetX Duo, enquanto o serviço _ *_nx_udp_socket_checksum_disable_** permite que a aplicação desative o processamento de checkum IPv4 UDP por tomada.

### <a name="udp-ports-and-binding"></a>Portos da UDP e Encadernação      
Uma porta UDP é um ponto final lógico no protocolo UDP. Existem 65.535 portas válidas na componente UDP da NetX Duo, que variam de 1 a 0xFFFF. Para enviar ou receber dados da UDP, a aplicação deve primeiro criar uma tomada UDP e, em seguida, ligá-la a uma porta desejada. Depois de ligar uma tomada UDP a uma porta, o pedido pode enviar e receber dados sobre essa tomada.

### <a name="udp-fast-pathtrade"></a>Caminho Rápido da UDP&trade;   
O UDP Fast Path &trade; é o nome para um caminho de sobrecarga de baixo pacote através da implementação do UDP NetX Duo. O envio de um pacote UDP requer apenas algumas chamadas de função: ***nx_udp_socket_send** _, _*_nx_ip_packet_send_*_, e a eventual chamada para o controlador de rede. _*_nx_udp_socket_send_*_ está disponível no NetX Duo para aplicações NetX existentes e só é aplicável para pacotes IPv4. O método preferido, no entanto, é usar o serviço _ *_nxd_udp_socket_send_** discutido abaixo. Na receção do pacote UDP, o pacote UDP é colocado na tomada UDP adequada receber fila ou entregue a um fio de aplicação suspenso numa única chamada de função do processamento de interrupção de receção do condutor da rede. Esta lógica altamente otimizada para o envio e receção de pacotes UDP é a essência da tecnologia UDP Fast Path.  

### <a name="udp-packet-send"></a>Envio de pacote de UDP    
O envio de dados UDP através das redes IPv6 ou IPv4 é facilmente realizado através da função ***nxd_udp_socket_send** _ . O chamador deve definir a versão IP no campo _nx_ip_version* do parâmetro do ponteiro NXD_ADDRESS. A NetX Duo determinará o melhor endereço de origem para pacotes de UDP transmitidos com base no endereço IPv4/IPv6 de destino. Este serviço coloca um cabeçalho UDP na frente dos dados do pacote e envia-o para a rede usando uma rotina interna de envio de IP. Não existe suspensão de fio no envio de pacotes UDP porque todas as transmissões de pacotes UDP são processadas imediatamente. 

Para destinos multicast ou de difusão, a aplicação deve especificar o endereço IP de origem para utilizar se o dispositivo NetX Duo tiver vários endereços IP para escolher. Isto pode ser feito com os serviços ***nxd_udp_socket_source_send.***

> [!IMPORTANT]    
> *Se **nx_udp_socket_send** for utilizado para transmitir pacotes multicast ou de transmissão, o endereço IP da primeira interface ativada é utilizado como endereço de origem*.

> [!NOTE] 
> *Se a lógica de verificação da UDP estiver ativada para esta tomada, a operação de checkum é realizada no contexto da linha de chamada, sem bloquear o acesso às estruturas de dados UDP ou IP*. 

> [!WARNING]    
> *Os dados de carga útil da UDP que residem na estrutura NX_PACKET devem residir num limite de palavras longas. A aplicação precisa de deixar espaço suficiente entre o ponteiro pré-final e o ponteiro de início de dados para o NetX Duo colocar os cabeçalhos UDP, IP e meios de comunicação físicos*.

### <a name="udp-packet-receive"></a>Receber pacote da UDP    
Os fios de aplicação podem receber pacotes UDP de uma determinada tomada chamando ***nx_udp_socket_receive***. A função de receção da tomada fornece o pacote mais antigo da fila de receção da tomada. Se não houver pacotes na fila de receção, o fio de chamada pode suspender (com um intervalo opcional) até chegar um pacote.

O processamento de pacotes UDP (normalmente chamado do controlador de interrupção de receção do controlador de receção do condutor da rede) é responsável por colocar o pacote na fila de receção da tomada UDP ou entregá-lo ao primeiro fio suspenso à espera de um pacote. Se o pacote estiver em fila, o processamento de receção também verifica a profundidade máxima de receção associada à tomada. Se este pacote recém-em fila exceder a profundidade da fila, o pacote mais antigo da fila é descartado.

### <a name="udp-receive-notify"></a>Notificação de receção da UDP   
Se o fio de aplicação precisar de processar dados recebidos de mais de uma tomada, deve ser utilizada a função ***nx_udp_socket_receive_notify.*** Esta função regista uma função de chamada de pacote de receção para a tomada. Sempre que um pacote é recebido na tomada, a função de retorno é executada.

O conteúdo da função de retorno é específico da aplicação; no entanto, provavelmente conteria lógica para informar o fio de processamento de que um pacote está agora disponível na tomada correspondente.

### <a name="peer-address-and-port"></a>Endereço de pares e porto   
Ao receber um pacote UDP, a aplicação pode encontrar o endereço IP e o número de porta do remetente utilizando o ***serviço nx_udp_packet_info_extract***. Na devolução bem sucedida, este serviço fornece informações sobre o endereço IP do remetente, o número de porta do remetente e a interface local através da qual o pacote foi recebido.  

### <a name="thread-suspension"></a>Suspensão do fio   
Como mencionado anteriormente, os fios de aplicação podem suspender enquanto tentam receber um pacote UDP em uma determinada porta UDP. Depois de recebido um pacote naquela porta, é dado ao primeiro fio suspenso e esse fio é retomado. Um tempo limite opcional está disponível ao suspender um pacote de receção UDP, uma funcionalidade disponível para a maioria dos serviços NetX Duo.  

### <a name="udp-socket-statistics-and-errors"></a>Estatísticas e erros da tomada de UDP     
Se ativado, o software de tomada UDP NetX Duo mantém o registo de várias estatísticas e erros que podem ser úteis à aplicação. As seguintes estatísticas e relatórios de erro são mantidos para cada instância IP/UDP:

- Total de pacotes UDP enviados  
- Total de bytes UDP enviados  
- Total de pacotes UDP recebidos   
- Total de bytes UDP recebidos  
- Total de pacotes inválidos da UDP  
- Total de pacotes de receção udp caídos  
- Total da UDP recebe erros de checkum  
- Pacotes de tomada udp enviados  
- UDP Socket Bytes Enviados  
- Pacotes de tomada udp recebidos   
- UDP Socket Bytes Recebidos  
- Pacotes de tomada uDP em fila  
- Tomada UDP receber pacotes caídos  
- Erros de verificação da tomada da UDP  

Todas estas estatísticas e relatórios de erro estão disponíveis para a aplicação com o serviço ***nx_udp_info_get** _ para estatísticas UDP acumulados em todas as tomadas UDP, e o serviço _ *_nx_udp_socket_info_get_** para estatísticas de UDP na tomada de UDP especificada.

### <a name="udp-socket-control-block-nx_udp_socket"></a>NX_UDP_SOCKET do bloco de controlo da tomada UDP
As características de cada tomada UDP encontram-se no bloco de controlo NX_UDP_SOCKET associado. Contém informações úteis, tais como a ligação à estrutura de dados IP, a interface de rede para os caminhos de envio e receção, a porta vinculada e a fila de pacotes de receção. Esta estrutura é definida no ficheiro ***nx_api.h.***

## <a name="transmission-control-protocol-tcp"></a>Protocolo de Controlo de Transmissão (TCP)

O Protocolo de Controlo de Transmissão (TCP) fornece transferência fiável de dados de fluxo entre dois membros da rede (RFC 793). Todos os dados enviados de um membro da rede são verificados e reconhecidos pelo membro recetor. Além disso, os dois membros devem ter estabelecido uma ligação antes de qualquer transferência de dados. Tudo isto resulta numa transferência de dados fiável; no entanto, requer substancialmente mais despesas do que a transferência de dados da UDP anteriormente descrita.

Exceto quando notados, não há alterações nos serviços de API do protocolo TCP entre NetX e NetX Duo porque o IPv6 está principalmente preocupado com a camada ip subjacente. Todos os serviços NetX Duo TCP podem ser utilizados para ligações IPv4 ou IPv6.

### <a name="tcp-header"></a>Cabeçalho TCP   
Na transmissão, o cabeçalho TCP é colocado na frente dos dados do utilizador. Na receção, o cabeçalho TCP é removido do pacote de entrada, deixando apenas os dados do utilizador disponíveis para a aplicação. A TCP utiliza o protocolo IP para enviar e receber pacotes, o que significa que há um cabeçalho IP em frente ao cabeçalho TCP quando o pacote está na rede. A figura 13 mostra o formato do cabeçalho TCP.

![Diagrama do formato do cabeçalho TCP.](./media/user-guide/image22.png)

### <a name="figure-13-tcp-header"></a>FIGURA 13. Cabeçalho TCP

O seguinte descreve o formato do cabeçalho TCP:

|Campo de Cabeçalho &nbsp; |Objetivo |
|------|------|
| **Número de porta de 16 bits** | Este campo contém a porta onde o pacote TCP está a ser enviado. As portas TCP válidas variam de 1 a 0xFFFF. |
| **Porto de destino de 16 bits** | Este campo contém a porta TCP para onde o pacote está a ser enviado. As portas TCP válidas variam de 1 a 0xFFFF. |
| **Número de sequência de 32 bits** | Este campo contém o número de sequência para os dados enviados a partir desta extremidade da ligação. A sequência original é estabelecida durante a sequência de ligação inicial entre dois nós TCP. Cada transferência de dados a partir desse ponto resulta num incremento do número de sequência pelo número de bytes enviados. |
| **Número de reconhecimento de 32 bits** | Este campo contém o número de sequência correspondente ao último byte recebido por este lado da ligação. Isto é usado para determinar se os dados anteriormente enviados foram recebidos com sucesso pela outra extremidade da ligação. |
| **Comprimento do cabeçalho de 4 bits** | Este campo contém o número de palavras de 32 bits no cabeçalho TCP. Se não houver opções no cabeçalho TCP, este campo é 5. |
| **Bits de código de 6 bits** |Este campo contém os seis bits de código diferentes utilizados para indicar várias informações de controlo associadas à ligação. As bits de controlo são definidas da seguinte forma:<br \> - URG (21): Presen de dados urgentes<br \> - ACK (20): O número de reconhecimento é válido<br - PSH (19): Lidar com estes dados imediatamente<br - ACK (20): O número de reconhecimento é válido<br \> - PSH (19): Lidar com estes dados imediatamente<<<br \> - RST (18): Repor a ligação<br \> - SYN (17): Sincronizar os números de sequência (utilizados para estabelecer a ligação)<br \> - FIN (16): O remetente é terminado com transmissão (utilizada para fechar a ligação) |
|**Janela de 16 bits** |Este campo é utilizado para o controlo de fluxos. Contém a quantidade de bytes que a tomada pode receber atualmente. Isto é basicamente usado para o controlo de fluxo. O remetente é responsável por se certificar de que os dados a enviar se encaixam na janela anunciada do recetor. |
|**Cheque TCP de 16 bits** |Este campo contém a 16-bit checkum para o pacote, incluindo o cabeçalho TCP, a área de dados do pacote e o cabeçalho pseudo IP. |
|**Ponteiro urgente de 16 bits** |Este campo contém a compensação positiva do último byte dos dados urgentes. Este campo só é válido se a broca de código urg estiver definida no cabeçalho. |

> [!NOTE]  
> *Espera-se que todos os cabeçalhos na implementação TCP/IP estejam em grande formato **endiano.** Neste formato, o byte mais significativo da palavra reside no endereço byte mais baixo*.

### <a name="tcp-enable"></a>Ativar TCP       
Antes de as ligações TCP e as transmissões de pacotes serem possíveis, a aplicação deve primeiro permitir a TCP, ligando para o ***serviço nx_tcp_enable.*** Depois de ativado, a aplicação é gratuita para aceder a todos os serviços TCP.  

### <a name="tcp-socket-create"></a>Criação de tomada TCP    
As tomadas TCP são criadas durante a inicialização ou durante o tempo de funcionamento por fios de aplicação. O tipo inicial de serviço, tempo para viver e tamanho da janela são definidos pelo ***serviço nx_tcp_socket_create.*** Não existem limites ao número de tomadas TCP numa aplicação.  

### <a name="tcp-checksum"></a>TCP Checksum     
A TCP especifica a parte de verificação de 16 bits de um complemento que cobre o cabeçalho IP pseudo (composto pelo endereço IP de origem, endereço IP de destino e a palavra IP protocol/comprimento), o cabeçalho TCP e os dados do pacote TCP. A única diferença entre as contas de cabeçalho de pacote IPv4 e IPv6 TCP é que os endereços IP de origem e destino são de 32 bits em IPv4 e 128 bits no IPv6. 

Certos controladores de rede são capazes de realizar cálculo e validação de verificação de TCP em hardware. Para estes sistemas, as aplicações podem pretender utilizar a lógica de hardware checksum tanto quanto possível para reduzir a sobrecarga de tempo de funcionamento. As aplicações podem desativar a lógica de cálculo de verificação TCP da biblioteca NetX Duo completamente no tempo de construção, definindo ***NX_DISABLE_TCP_TX_CHECKSUM** _ e _*_NX_DISABLE_TCP_RX_CHECKSUM_**. Desta forma, o código de verificação TCP não é compilado. No entanto, deve ter cuidado se o pacote Opcional NetX Duo IPsec for instalado, e a ligação TCP pode ter de atravessar através de um canal seguro. Neste caso, os dados em pacotes pertencentes à ligação TCP já estão encriptados, e a maioria dos módulos de verificação TCP de hardware presentes no controlador de rede não conseguem gerar o valor correto da carga útil da TCP encriptada.

Para resolver este problema, a aplicação deve manter a lógica de checkum TCP disponível na biblioteca e utilizar a funcionalidade de capacidade de interface. Com a funcionalidade de capacidade de interface ativada, o módulo TCP sabe como manusear corretamente a conta de verificação TCP se o controlador também for capaz de calcular o valor da caixa de verificação:

1) Se o pacote TCP não estiver sujeito ao processo IPsec, o hardware de interface de rede é capaz de calcular a sala de verificação. Por conseguinte, o módulo TCP não tenta calcular a caixa de verificação;

2) Se o pacote IPsec for instalado e o pacote TCP estiver sujeito ao processo IPsec, o módulo TCP calcula a parte de verificação em software antes de enviar o pacote para a camada IPsec.

### <a name="tcp-port"></a>Porta TCP     
Uma porta TCP é um ponto de ligação lógico no protocolo TCP. Existem 65.535 portas válidas na componente TCP da NetX Duo, que variam de 1 a 0xFFFF. Ao contrário da UDP em que os dados de uma porta podem ser enviados para qualquer outra porta de destino, uma porta TCP está ligada a outra porta TCP específica, e só quando esta ligação é estabelecida pode ocorrer qualquer transferência de dados — e apenas entre as duas portas que compõem a ligação.

> [!IMPORTANT]
> *As portas TCP são completamente separadas das portas UDP; por exemplo, a porta UDP número 1 não tem qualquer relação com o número da porta TCP 1*.

### <a name="client-server-model"></a>Modelo Client-Server     
Para utilizar o TCP para transferência de dados, deve primeiro ser estabelecida uma ligação entre as duas tomadas TCP. O estabelecimento da ligação é feito de forma cliente-servidor. O lado cliente da ligação é o lado que inicia a ligação, enquanto o lado do servidor simplesmente aguarda os pedidos de ligação do cliente antes de qualquer processamento ser feito.

> [!IMPORTANT]
> *Para dispositivos multihomes, o NetX Duo determina automaticamente o endereço de origem a utilizar para a ligação e o próximo endereço de lúpulo baseado no endereço IP de destino da ligação. Uma vez que a TCP se limita a enviar pacotes para endereços de destino unicast (por exemplo, não transmitidos), a NetX Duo não requer uma "dica" para escolher o endereço IPv6 de origem*.

### <a name="tcp-socket-state-machine"></a>Máquina de estado de tomada TCP      
A ligação entre duas tomadas TCP (um cliente e um servidor) é complexa e é gerida de forma estatal. Cada tomada TCP começa em estado fechado. Através de eventos de ligação, a máquina estatal de cada tomada migra para o estado ESTABELECIDO, que é onde ocorre a maior parte da transferência de dados em TCP. Quando um dos lados da ligação já não deseja enviar dados, desliga-se. Depois de o outro lado desligar, eventualmente a tomada TCP volta ao estado fechado. Este processo repete-se sempre que um cliente e servidor TCP estabelecem e fecham uma ligação. A figura 14 mostra os vários estados da máquina estatal TCP.

### <a name="tcp-client-connection"></a>Conexão ao cliente TCP       
Como mencionado anteriormente, o lado cliente da ligação TCP inicia um pedido de ligação a um servidor TCP. Antes de um pedido de ligação ser feito, o TCP deve ser ativado na instância IP do cliente. Além disso, a tomada TCP do cliente deve ser criada em seguida com o serviço ***nx_tcp_socket_create** _ e ligada a uma porta através do serviço _ *_nx_tcp_client_socket_bind_** .

Depois de a tomada do cliente estar ligada, o serviço ***nxd_tcp_client_socket_connect*** é utilizado para estabelecer uma ligação com um servidor TCP. Note que a tomada deve estar num estado fechado para iniciar uma tentativa de ligação. O estabelecimento da ligação começa com o NetX Duo a emitir um pacote SYN e, em seguida, a aguardar um pacote SYN ACK de volta do servidor, o que significa a aceitação do pedido de ligação. Após a receção do SYN ACK, a NetX Duo responde com um pacote ACK e promove a tomada do cliente para o estado estabelecido.

![Diagrama dos estados da máquina estatal TCP.](./media/user-guide/image24.png)   

**FIGURA 14. Estados da Máquina Estatal TCP**


> [!WARNING]
> *As aplicações devem utilizar **nxd_tcp_client_socket_connect** para as ligações IPv4 e IPv6 TCP. As aplicações ainda podem usar **nx_tcp_client_socket_connect** para ligações IPv4 TCP, mas os desenvolvedores são encorajados a usar **nxd_tcp_client_socket_connect** uma vez **nx_tcp_client_socket_connect** acabará por ser depreciada.*

*Da mesma forma, **nxd_tcp_socket_peer_info_get** funciona com ligações IPv4 ou IPv6 TCP. No entanto, **nx_tcp_socket_peer_info_get** ainda está disponível para aplicações antigas. Os desenvolvedores são encorajados a usar **nxd_tcp_socket_peer_info_get** a seguir em frente.*

### <a name="tcp-client-disconnection"></a>Desconexão do cliente TCP    
O fecho da ligação é realizado chamando ***nx_tcp_socket_disconnect***. Se não for especificada qualquer suspensão, a tomada do cliente envia um pacote RST para a tomada do servidor e coloca a tomada no estado FECHADO. Caso contrário, se for solicitada uma suspensão, é executada a completa do protocolo de desconexão TCP, da seguinte forma: 

- Se o servidor já tinha iniciado um pedido de desconexão (a tomada do cliente já recebeu um pacote FIN, respondeu com um ACK, e está no estado CLOSE WAIT), a NetX Duo promove o estado de tomada TCP do cliente para o estado de ÚLTIMA ACK e envia um pacote FIN. Em seguida, aguarda um ACK do servidor antes de completar a desconexão e entrar no estado FECHADO.

- Se, por outro lado, o cliente for o primeiro a iniciar um pedido de desconexão (o servidor não foi desligado e a tomada ainda se encontra no estado ESTABELECIDO), o NetX Duo envia um pacote FIN para iniciar a desconexão e espera receber uma FIN e um ACK do servidor antes de completar a desconexão e colocar a tomada num estado FECHADO.

Se ainda existirem pacotes na fila de transmissão da tomada, o NetX Duo suspende o tempo limite especificado para permitir o reconhecimento dos pacotes. Se o tempo limite expirar, o NetX Duo esvazia a fila de transmissão da tomada do cliente. 

Para desvindia a porta da tomada do cliente, a aplicação chama ***nx_tcp_client_socket_unbind***. A tomada deve estar num estado fechado ou em processo de desconexão (isto é, estado de espera TIMED) antes de a porta ser libertada; caso contrário, um erro é devolvido.

Finalmente, se a aplicação já não necessitar da tomada do cliente, chama ***nx_tcp_socket_delete*** para apagar a tomada.

### <a name="tcp-server-connection"></a>Conexão do servidor TCP      
O lado do servidor de uma ligação TCP é passivo; ou seja, o servidor aguarda que um cliente inicie o pedido de ligação. Para aceitar uma ligação ao cliente, a TCP deve primeiro ser ativada na instância IP, ligando para o serviço ***nx_tcp_enable** _. Em seguida, a aplicação deve criar uma tomada TCP utilizando o serviço _ *_nx_tcp_socket_create_** .  

A tomada do servidor também deve ser configurada para ouvir pedidos de ligação. Isto é conseguido utilizando o serviço ***nx_tcp_server_socket_listen.*** Este serviço coloca a tomada do servidor no estado LISTEN e liga a porta do servidor especificada à tomada.

> [!NOTE] 
> *Para definir uma rotina de chamada de chamada de tomada, a aplicação especifica a função de retorno adequada para o argumento tcp_listen_callback do serviço **nx_tcp_server_socket_listen.** Esta função de chamada de aplicação é então executada pela NetX Duo sempre que uma nova ligação é solicitada nesta porta do servidor. O processamento na chamada está sob controlo de aplicação.*

Para aceitar pedidos de ligação ao cliente, a aplicação liga para o serviço ***nx_tcp_server_socket_accept** _ . A tomada do servidor deve estar num estado DE ESCUTA ou num estado SYN RECEIVED (ou seja, o servidor está no estado LISTEN e recebeu um pacote SYN de um cliente que solicita uma ligação) para ligar para o serviço de aceitação. Um estado de retorno bem sucedido de _ *_nx_tcp_server_socket_accept_** indica que a ligação foi configurada e a tomada do servidor está no estado ESTABELECIDO.

Depois de a tomada do servidor ter uma ligação válida, os pedidos adicionais de ligação ao cliente são colocados na fila até à profundidade especificada pelo *listen_queue_size, transmitidos para o* serviço  * **nx_tcp_server_socket_listen** _ . Para processar as ligações subsequentes numa porta do servidor, a aplicação deve ligar para _ *_nx_tcp_server_socket_relisten_** com uma tomada disponível (ou seja, uma tomada em estado fechado). Note que a mesma tomada do servidor pode ser utilizada se a ligação anterior associada à tomada estiver concluída e a tomada estiver no estado fechado.

### <a name="tcp-server-disconnection"></a>Desconexão do servidor TCP     
O fecho da ligação é realizado chamando ***nx_tcp_socket_disconnect***. Se não for especificada qualquer suspensão, a tomada do servidor envia um pacote RST para a tomada do cliente e coloca a tomada no estado FECHADO. Caso contrário, se for solicitada uma suspensão, é executada a completa do protocolo de desconexão TCP, da seguinte forma:

- Se o cliente já tinha iniciado um pedido de desconexão (a tomada do servidor já recebeu um pacote FIN, respondeu com um ACK, e está no estado CLOSE WAIT), a NetX Duo promove o estado de tomada TCP para o estado de ÚLTIMA ACK e envia um pacote FIN. Em seguida, aguarda um ACK do cliente antes de completar a desconexão e entrar no estado FECHADO.

- Se, por outro lado, o servidor for o primeiro a iniciar um pedido de desconexão (o cliente não se desligou e a tomada ainda se encontra no estado ESTABELECIDO), a NetX Duo envia um pacote FIN para iniciar a desconexão e espera receber uma FIN e um ACK do cliente antes de completar a desconexão e colocar a tomada num estado FECHADO.

Se ainda existirem pacotes na fila de transmissão da tomada, o NetX Duo suspende o tempo limite especificado para permitir que esses pacotes sejam reconhecidos. Se o tempo limite expirar, o NetX Duo descarrega a fila de transmissão da tomada do servidor.

Após o processamento da desconexão estar concluído e a tomada do servidor estiver no estado FECHADO, a aplicação deve chamar o serviço ***nx_tcp_server_socket_unaccept** _ para terminar a associação desta tomada com a porta do servidor. Note que este serviço deve ser chamado pela aplicação mesmo _*_que nx_tcp_socket_disconnect_*_ ou _*_nx_tcp_server_socket_accept_*_ devolva um estado de erro. Após a _*_nx_tcp_server_socket_unaccept_*_ retornar, a tomada pode ser usada como cliente ou tomada de servidor, ou mesmo eliminada se já não for necessária. Se aceitar outra ligação ao cliente na mesma porta do servidor, o serviço _ *_nx_tcp_server_socket_relisten_** deve ser chamado nesta tomada.

O seguinte segmento de código ilustra a sequência de chamadas que um servidor típico de TCP utiliza:

```c
/* Set up a previously created TCP socket to
   listen on port 12 */
nx_tcp_server_socket_listen()

/* Loop to make a (another) connection. */
while(1)
{
    /* Wait for a client socket connection request
       for 100 ticks. */
    nx_tcp_server_socket_accept();

    /* (Send and receive TCP messages with the TCP
       client) */

    /* Disconnect the server socket. */
    nx_tcp_socket_disconnect();

    /* Remove this server socket from listening on
       the port. */
    nx_tcp_server_socket_unaccept(&server_socket);
    /* Set up server socket to relisten on the
       same port for the next client. */
    nx_tcp_server_socket_relisten();
}
```

### <a name="mss-validation"></a>Validação mss      
O Tamanho Máximo do Segmento (MSS) é a quantidade máxima de bytes que um hospedeiro TCP pode receber sem ser fragmentado pela camada IP subjacente. Durante a fase de estabelecimento de ligação TCP, ambas as extremidades trocam o seu próprio valor de MSS TCP, de modo que o remetente não envie um segmento de dados TCP maior do que o MSS do recetor. O módulo NetX Duo TCP validará opcionalmente o valor mss anunciado do seu pares antes de estabelecer uma ligação. Por predefinição, o NetX Duo não permite tal verificação. As candidaturas que desejem realizar a validação do MSS devem definir ***NX_ENABLE_TCP_MSS_CHECK** _ na construção da biblioteca NetX Duo, e o valor mínimo será definido em _*_NX_TCP_MSS_MINIMUM_*_. As ligações TCP recebidas com valores DESS abaixo _ *_NX_TCP_MSS_MINIMUM_** são largadas.

### <a name="stop-listening-on-a-server-port"></a>Pare de ouvir numa porta do servidor    
Se a aplicação já não pretender ouvir os pedidos de ligação ao cliente numa porta de servidor que foi previamente especificada por uma chamada para o serviço ***nx_tcp_server_socket_listen** _ , a aplicação simplesmente liga para o serviço _ *_nx_tcp_server_socket_unlisten_** . Este serviço coloca qualquer tomada à espera de uma ligação no estado FECHADO e liberta quaisquer pacotes de pedido de ligação ao cliente em fila. 

### <a name="tcp-window-size"></a>Tamanho da janela TCP   
Durante as fases de configuração e transferência de dados da ligação, cada porta reporta a quantidade de dados que pode manusear, que é chamado de tamanho da janela. À medida que os dados são recebidos e processados, este tamanho da janela é ajustado dinamicamente. Em TCP, um remetente só pode enviar uma quantidade de dados que se encaixem na janela do recetor. Na essência, o tamanho da janela fornece controlo de fluxo para transferência de dados em cada direção da ligação.   

### <a name="tcp-packet-send"></a>Envio de pacote TCP     
O envio de dados TCP é facilmente realizado através da chamada ***de nx_tcp_socket_send*** função. Se o tamanho dos dados transmitidos for maior do que o valor MSS da tomada ou o atual par receber o tamanho da janela, o que for menor, a lógica interna da TCP esculpe os dados que se encaixam em min (MSS, peer receive Window) para transmissão. Este serviço constrói então um cabeçalho TCP em frente ao pacote (incluindo o cálculo da caixa de verificação). Se o tamanho da janela do recetor não for zero, o chamador enviará o máximo de dados possível para preencher o tamanho da janela do recetor. Se a janela de receção se tornar zero, o chamador pode suspender e esperar que o tamanho da janela do recetor aumente o suficiente para que este pacote seja enviado. A qualquer momento, vários fios podem suspender-se enquanto tentam enviar dados através da mesma tomada. 

> [!WARNING]  
> *Os dados da TCP que residem na estrutura NX_PACKET devem residir num limite de palavras longas. Além disso, deve haver espaço suficiente entre o ponteiro pré-conjunto e o ponteiro de início de dados para colocar os cabeçalhos TCP, IP e meios de comunicação físicos*.

### <a name="tcp-packet-retransmit"></a>Retransmissão de pacotes TCP      
Pacotes TCP previamente transmitidos enviados realmente armazenados internamente até que um ACK seja devolvido do outro lado da ligação. Se os dados transmitidos não forem reconhecidos dentro do período de tempo limite, o pacote armazenado é reencaminhado e o período de tempo seguinte é definido. Quando um ACK é recebido, todos os pacotes cobertos pelo número de reconhecimento na fila de transmissão interna são finalmente libertados.  

> [!WARNING]   
> *A aplicação não reutilizar o pacote nem alterar o conteúdo do pacote após nx_tcp_socket_send NX_SUCCESS. O pacote transmitido é eventualmente lançado pelo tratamento interno da NetX Duo após os dados são reconhecidos pelo outro extremo*.

### <a name="tcp-keepalive"></a>TCP Keepalive     
A função TCP Keepalive permite que uma tomada detete se o seu par desliga ou não sem uma terminação adequada (por exemplo, o par se despenhou), ou para impedir que certas instalações de monitorização da rede cessem uma ligação por longos períodos de inatividade. A TCP Keepalive funciona enviando periodicamente uma moldura TCP sem dados, e o número de sequência definido para um a menos do que o número atual da sequência. Ao receber tal moldura de resalamento TCP, o destinatário, se ainda estiver vivo, responde com um ACK para o seu número de sequência atual. Isto completa a transação de manter.  

Por predefinição, a função keepalive não está ativada. Para utilizar esta funcionalidade, a biblioteca NetX Duo deve ser construída com ***NX_ENABLE_TCP_KEEPALIVE** _ definido. O símbolo _ *_NX_TCP_KEEPALIVE_INITIAL_** especifica o número de segundos de inatividade antes do início da estrutura de manter.  

### <a name="tcp-packet-receive"></a>Receber pacote TCP   
O processamento de pacotes de receção de TCP (chamado a partir do fio do ajudante IP) é responsável pelo manuseamento de várias ações de ligação e desconexão, bem como pelo processamento de reconhecimento de transmissão. Além disso, o processamento de pacotes de receção de TCP é responsável pela colocação de pacotes com dados de receção da fila de receção da tomada TCP adequada ou entregando o pacote ao primeiro fio suspenso à espera de um pacote.

### <a name="tcp-receive-notify"></a>Notificação de receção de TCP     
Se o fio de aplicação precisar de processar dados recebidos de mais de uma tomada, deve ser utilizada a função ***nx_tcp_socket_receive_notify.*** Esta função regista uma função de chamada de pacote de receção para a tomada. Sempre que um pacote é recebido na tomada, a função de retorno é executada.  

O conteúdo da função de retorno são específicos das aplicações; no entanto, a função provavelmente conteria lógica para informar o fio de processamento de que um pacote está disponível na tomada correspondente. 

### <a name="thread-suspension"></a>Suspensão do fio      
Como mencionado anteriormente, os fios de aplicação podem suspender enquanto tentam receber dados de uma determinada porta TCP. Depois de recebido um pacote naquela porta, é dado ao primeiro fio suspenso e esse fio é retomado. Um tempo limite opcional está disponível ao suspender um pacote de receção TCP, uma funcionalidade disponível para a maioria dos serviços NetX Duo.  

A suspensão thread também está disponível para serviços de ligação (cliente e servidor), ligação ao cliente e serviços de desconexão.  

### <a name="tcp-socket-statistics-and-errors"></a>Estatísticas e erros da tomada TCP     
Se ativado, o software de tomada TCP NetX Duo regista várias estatísticas e erros que podem ser úteis à aplicação. São mantidas as seguintes estatísticas e relatórios de erro para cada instância IP/TCP:   

- Total de pacotes TCP enviados  
- Total de bytes TCP enviados  
- Total de pacotes TCP recebidos   
- Total de bytes TCP recebidos   
- Total de pacotes inválidos TCP   
- Total de pacotes de receção TCP caídos    
- Total de erros de receção de TCP   
- Total de ligações TCP   
- Total de desconexões TCP   
- Total de ligações TCP caídas    
- Retransmissão total de pacotes TCP   
- Pacotes de tomada TCP enviados   
- TCP Socket Bytes Enviados   
- Pacotes de tomada TCP recebidos   
- TCP Socket Bytes Recebidos   
- Retransmissão do pacote de tomada TCP    
- Pacotes de tomada TCP em fila    
- Erros de verificação da tomada TCP    
- Estado da tomada TCP    
- Órbita de transmissão da tomada TCP    
- Tamanho da janela de transmissão da tomada TCP    
- Tomada TCP receber tamanho da janela    

Todas estas estatísticas e relatórios de erro estão disponíveis para a aplicação com o serviço ***nx_tcp_info_get** _ para o total das estatísticas TCP e o serviço _ *_nx_tcp_socket_info_get_** para as estatísticas de TCP por tomada.

### <a name="tcp-socket-control-block-nx_tcp_socket"></a>NX_TCP_SOCKET do bloco de controlo da tomada TCP      
As características de cada tomada TCP encontram-se no bloco de controlo *NX_TCP_SOCKET* associado, que contém informações úteis, tais como a ligação à estrutura de dados IP, a interface de ligação à rede, a porta vinculada e a fila do pacote de receção. Esta estrutura é definida no ficheiro ***nx_api.h.***