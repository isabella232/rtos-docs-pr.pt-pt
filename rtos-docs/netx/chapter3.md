---
title: Capítulo 3 - Componentes funcionais do Azure RTOS NetX
description: Este capítulo contém uma descrição da pilha Azure RTOS NetX TCP/IP de alto desempenho de uma perspetiva funcional.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: db23aa152b2765ac7cc9be098723fc5df0947484
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826887"
---
# <a name="chapter-3---functional-components-of-azure-rtos-netx"></a>Capítulo 3 - Componentes funcionais do Azure RTOS NetX

Este capítulo contém uma descrição da pilha Azure RTOS NetX TCP/IP de alto desempenho de uma perspetiva funcional. 

## <a name="execution-overview"></a>Visão geral da execução

Existem cinco tipos de execução de programas dentro de uma aplicação NetX: inicialização, chamadas de interface de aplicação, fio IP interno, temporizadores periódicos IP e o controlador de rede.

> [!IMPORTANT]
> A NetX requer a instalação da ThreadX e depende da sua execução de fios, suspensão, temporizadores periódicos e instalações de exclusão mútua.

### <a name="initialization"></a>Inicialização

O serviço ***nx_system_initialize** _ deve ser chamado antes de qualquer outro serviço NetX ser chamado. A inicialização do sistema pode ser chamada a partir da rotina ThreadX _ *_tx_application_define_** ou a partir de fios de aplicação.

Depois de ***nx_system_initialize** _ devoluções, o sistema está pronto para criar pacotes de piscinas e instâncias IP. Como a criação de uma instância IP requer um pacote de pacotes predefinidos, pelo menos um conjunto de pacotes NetX deve existir antes de criar uma instância IP. A criação de piscinas de pacotes e instâncias IP são permitidas a partir da função de inicialização ThreadX _ *_tx_application_define_** e a partir de fios de aplicação.

Internamente, a criação de um caso IP é realizada em duas partes. A primeira parte é feita no contexto do chamador, quer a partir de ***tx_application_define*** quer do contexto de um fio de aplicação. Isto inclui a criação da estrutura de dados IP e a criação de vários recursos IP, incluindo o fio IP interno. A segunda parte é executada durante a execução inicial a partir do fio IP interno. É aqui que o controlador de rede, fornecido durante a primeira parte da criação de IP, é chamado pela primeira vez. A chamada do controlador de rede a partir da linha IP interna permite ao condutor efetuar E/S e suspender durante o processamento de inicialização. Quando o controlador de rede regressa do seu processamento de inicialização, a criação ip fica completa.

> [!IMPORTANT]
> O **nx_ip_status_check** de serviço NetX está disponível para obter informações sobre a instância IP e o seu estado de interface primária. Essas informações de estado incluem se o link é ou não inicializado, ativado e o endereço IP é resolvido. Estas informações são utilizadas para sincronizar os fios de aplicação que precisam de utilizar uma instância IP recém-criada. Para sistemas multihomes, consulte "Multihome Support" abaixo. **nx_ip_interface_status_check** está disponível para obter informações sobre a interface especificada.

### <a name="application-interface-calls"></a>Chamadas de Interface de Aplicação

As chamadas da aplicação são feitas em grande parte a partir de fios de aplicação que estão a ser geridos sob o ThreadX RTOS. No entanto, algumas inicializaçãos, criar e permitir serviços podem ser chamados a partir de ***tx_application_define***. As secções "Allowed From" do Capítulo 4 indicam a partir da qual cada serviço NetX pode ser chamado.

Na maior parte das vezes, o processamento de atividades intensivas, como as despesas de computação, é feito dentro do contexto do fio de chamada , sem bloquear o acesso de outros fios à instância IP. Por exemplo, na transmissão, o cálculo da UDP checksum é realizado dentro do serviço ***nx_udp_socket_send,*** antes de ligar para a função de envio IP subjacente. Num pacote recebido, a conta de verificação da UDP é calculada no serviço ***nx_udp_socket_receive,*** executado no contexto do fio de aplicação. Isto ajuda a prevenir o bloqueio de pedidos de rede de fios de maior prioridade devido ao processamento de cálculo intensivo de checkum em fios de menor prioridade.

Valores, como endereços IP e números de porta, são passados para funções API na ordem byte de anfitrião. Internamente, estes valores também são armazenados na ordem byte de anfitrião. Isto permite que os desenvolvedores vejam facilmente os valores através de um depurar. Quando estes valores são programados num quadro para transmissão, são convertidos para ordem byte de rede.

### <a name="internal-ip-thread"></a>Fio IP interno

Como mencionado, cada instância IP no NetX tem o seu próprio fio. A prioridade e o tamanho da pilha do fio IP interno é definido no serviço ***nx_ip_create.*** O fio IP interno é criado num modo pronto a executar. Se o fio IP tiver uma prioridade maior do que o fio de chamada, a pré-substituição pode ocorrer dentro da chamada de criação IP.

O ponto de entrada do fio IP interno encontra-se na função interna ***_nx_ip_thread_entry***. Quando iniciado, o fio IP interno completa primeiro a inicialização do controlador de rede, que consiste em fazer três chamadas para o controlador de rede específico da aplicação. A primeira chamada é anexar o controlador de rede à instância IP, seguida de uma chamada de inicialização, que permite ao controlador de rede passar pelo processo de inicialização. Após o retorno do controlador de rede da inicialização (pode suspender-se enquanto aguarda a instalação correta do hardware), o fio IP interno volta a ligar para o controlador de rede para ativar a ligação. 

Após a retorna do controlador de rede a partir da chamada de ativação de ligação, o fio IP interno introduz uma verificação interminável de loop para vários eventos que precisam de ser processados para esta instância IP. Os eventos processados neste ciclo incluem receção de pacotes IP diferidos, montagem de fragmentos de pacote IP, processamento de ping ICMP, processamento de IGMP, processamento de fila de pacotes TCP, processamento periódico de TCP, intervalos de montagem de fragmentos IP e processamento periódico IGMP. Os eventos incluem também atividades de resolução de endereços: processamento de pacotes ARP e processamento periódico ARP na rede IP.

> [!NOTE]
> *As funções de retorno NetX, incluindo chamadas de escuta e desconexão, são chamadas a partir do fio IP interno - e não do fio de chamada original. A aplicação deve ter o cuidado de não suspender dentro de qualquer função de retorno NetX.*

### <a name="ip-periodic-timers"></a>Temporizadores periódicos IP
Existem dois temporizadores periódicos ThreadX utilizados para cada instância IP. O primeiro é um temporizador de um segundo para ARP, IGMP, TCP timeout, e também impulsiona o processamento de remontagem de fragmentos IP. O segundo temporizador é um temporizador de 100ms para conduzir o tempo limite de retransmissão TCP.

### <a name="network-driver"></a>Controlador de rede
Cada instância IP no NetX tem uma interface primária, que é identificada pelo seu controlador de dispositivos especificado no serviço ***nx_ip_create.*** O controlador da rede é responsável pelo tratamento de vários pedidos NetX, incluindo transmissão de pacotes, receção de pacotes e pedidos de estado e controlo.

Para um sistema multi-casa, a instância IP tem múltiplas interfaces, cada uma com um controlador de rede associado que executa estas tarefas para a respetiva interface.

O controlador da rede também deve lidar com eventos assíncronos que ocorrem nos meios de comunicação. Eventos assíncronos dos meios de comunicação incluem receção de pacotes, conclusão da transmissão de pacotes e alterações de estado. A NetX fornece ao controlador de rede várias funções de acesso para lidar com vários eventos. Estas funções foram concebidas para serem chamadas a partir da parte de rotina de serviço de interrupção do controlador de rede. Para as redes IP, o controlador de rede deve encaminhar todos os pacotes ARP recebidos para a função interna ***_nx_arp_packet_deferred_receive** _ . Todos os pacotes RARP devem ser encaminhados para _ *_nx_rarp_packet_deferred_receive_* _ função interna. Existem duas opções para pacotes IP. Se for necessária uma expedição rápida dos pacotes IP, os pacotes IP de entrada devem ser encaminhados para _ *_nx_ip_packet_receive_* _ para processamento imediato. Isto melhora consideravelmente o desempenho do NetX no manuseamento de pacotes IP. Caso contrário, o controlador de rede deve encaminhar os pacotes IP para _*_ _nx_ip_packet_deferred_receive_**. Este serviço coloca o pacote IP na fila de processamento diferida, onde é depois manuseado pela linha IP interna, o que resulta na menor quantidade de tempo de processamento do ISR.

O controlador de rede também pode adiar o processamento de interrupção para ficar sem o contexto do fio IP. Neste modo, o ISR deve guardar as informações necessárias, ligar para a função interna ***_nx_ip_driver_deferred_processing***, e reconhecer o controlador de interrupção. Este serviço notifica a linha IP para agendar uma chamada ao controlador do dispositivo para completar o processamento do evento que causa a interrupção.

Alguns controladores de rede são capazes de executar a computação e validação de checkum de cabeçalho TCP/IP em hardware, sem ocupar recursos valiosos da CPU. Para tirar partido da funcionalidade de capacidade de hardware, o NetX fornece opções para ativar ou desativar vários cálculos de checkum de software no momento da compilação, bem como ligar ou desligar a computação checkum no tempo de execução. Consulte "[Chapter 5 NetX Network Drivers](chapter5.md)" para obter informações mais detalhadas sobre a escrita de controladores de rede NetX.

### <a name="multihome-support"></a>Suporte Multihome
O NetX suporta sistemas ligados a múltiplos dispositivos físicos utilizando uma única instância IP. Cada interface física é atribuída a um bloco de controlo de interface na instância IP. As aplicações que desejem utilizar um sistema multihome devem definir o valor para **NX_MAX_PHSYCIAL_INTERFACES** ao número de dispositivos físicos ligados ao sistema e reconstruir a biblioteca NetX. Por **predefinição, NX_MAX_PHYSICAL_INTERFACES** é definido para um, criando um bloco de controlo de interface na instância IP.

A aplicação NetX cria uma única instância IP para o dispositivo primário utilizando o serviço ***nx_ip_create** _ . Para cada dispositivo de rede adicional, a aplicação liga o dispositivo à instância IP utilizando o serviço _ *_nx_ip_interface_attach_** .

Cada estrutura de interface de rede contém um subconjunto de informações de rede sobre a interface de rede que está contida no bloco de controlo IP, incluindo endereço IP de interface, máscara de sub-rede, tamanho IP MTU e informações de endereço de camada MAC.

> [!IMPORTANT]
> *NetX com suporte multihome é compatível com versões anteriores do NetX. Serviços que não levam informações de interface explícitas padrão ao dispositivo de rede primária.*

A interface primária tem índice zero na lista de instâncias IP. Cada dispositivo subsequente ligado à instância IP é atribuído o próximo índice.

Todos os serviços de protocolo de camada superior para os quais a instância IP está ativada, incluindo TCP, UDP, ICMP e IGMP, estão disponíveis para todos os dispositivos anexos.

Na maioria dos casos, o NetX pode determinar o melhor endereço de origem a utilizar ao transmitir um pacote. A seleção do endereço de origem baseia-se no endereço de destino. Os serviços NetX são fornecidos para permitir que as aplicações especifiquem um endereço de origem específico para utilizar, nos casos em que o mais adequado não possa ser determinado pelo endereço de destino. Um exemplo seria num sistema multihome, uma aplicação precisa enviar um pacote para uma transmissão IP ou endereços de destino multicast.

Os serviços especificamente para o desenvolvimento de aplicações multihomes incluem:

*nx_igmp_multicast_interface_join nx_ip_driver_interface_direct_command nx_ip_interface_address_get nx_ip_interface_address_set nx_ip_interface_attach nx_ip_interface_info_get nx_ip_interface_status_check nx_ip_raw_packet_interface_send nx_udp_socket_interface_send*

Estes serviços são explicados em maior detalhe no capítulo[4 - Descrição dos Serviços Azure RTOS NetX](chapter4.md)".

### <a name="loopback-interface"></a>Loopback Interface
A interface loopback é uma interface de rede especial sem uma ligação física anexada. A interface loopback permite que as aplicações comuniquem através do endereço IP loopback 127.0.0.1

Para utilizar uma interface lógico de loopback, certifique-se de que a opção configurável ***NX_DISABLE_LOOPBACK_INTERFACE*** não está definida.

### <a name="interface-control-blocks"></a>Blocos de controlo de interface
O número de blocos de controlo de interface na instância IP é o número de interfaces físicas (definidas por ***NX_MAX_PHYSICAL_INTERFACES** _) mais a interface loopback se estiver ativada. O número total de interfaces é definido em _*_NX_MAX_IP_INTERFACES_**.

## <a name="protocol-layering"></a>Camada de protocolo

O TCP/IP implementado pela NetX é um protocolo em camadas, o que significa que protocolos mais complexos são construídos em cima de protocolos subjacentes mais simples. Em TCP/IP, o protocolo de camada mais baixa está na *camada de ligação* e é manuseado pelo controlador de rede. Este nível é tipicamente direcionado para Ethernet, mas também pode ser fibra, série ou praticamente qualquer meio físico.

Em cima da camada de ligação está a *camada de Rede.* No TCP/IP, este é o IP, que é basicamente responsável pelo envio e receção de pacotes simples, de forma de melhor esforço, em toda a rede. Os protocolos de tipo de gestão como o ICMP e o IGMP são tipicamente também categorizados como camadas de rede, mesmo que dependam de IP para envio e receção.

A *camada de transporte* assenta em cima da camada de rede. Esta camada é responsável pela gestão do fluxo de dados entre os anfitriões na rede. Existem dois tipos de serviços de transporte apoiados pela NetX: UDP e TCP. Os serviços da UDP fornecem o melhor esforço de envio e receção de dados entre dois anfitriões de forma sem ligação, enquanto a TCP fornece um serviço fiável orientado para a ligação entre duas entidades hospedeiras.

Esta camada reflete-se nos pacotes de dados de rede reais. Cada camada em TCP/IP contém um bloco de informação chamado cabeçalho. Esta técnica de dados circundantes (e possivelmente informações protocolares) com um cabeçalho é tipicamente chamada de encapsulamento de dados. A figura 1 mostra um exemplo de camadas NetX e a Figura 2 mostra o encapsulamento de dados resultante para os dados da UDP que estão a ser enviados.

![Camada de protocolo](./media/user-guide/protocol-layering.png)

**FIGURA 1. Camada de protocolo**

![Encapsulamento de Dados da UDP](./media/user-guide/udp-data-encapsulation.png)

**FIGURA 2. Encapsulamento de Dados da UDP**

## <a name="packet-pools"></a>Piscinas de Pacotes

A atribuição de pacotes de forma rápida e determinística é sempre um desafio nas aplicações de networking em tempo real. Com isto em mente, o NetX fornece a capacidade de criar e gerir várias piscinas de pacotes de rede de tamanho fixo.

Como as piscinas de pacotes NetX consistem em blocos de memória de tamanho fixo, nunca existem problemas de fragmentação interna. Claro, a fragmentação causa comportamentos que não são inerentemente indeterminados.

Além disso, o tempo necessário para alocar e libertar um pacote NetX equivale a uma simples manipulação de listas ligadas. Além disso, a atribuição de pacotes e alocação de acordos são feitas no chefe da lista disponível. Isto fornece o processamento de listas mais rápido possível.

A falta de flexibilidade é tipicamente a principal desvantagem das piscinas de pacotes de tamanho fixo. Determinar o tamanho ideal da carga útil do pacote que também lida com o pacote de entrada na pior das hipóteses é uma tarefa difícil. Os pacotes NetX abordam este problema com uma funcionalidade opcional chamada *chaining de pacotes*. Um pacote de rede real pode ser feito de um ou mais pacotes NetX ligados entre si. Além disso, o cabeçalho do pacote mantém um ponteiro para a parte superior do pacote. À medida que os protocolos adicionais são adicionados, este ponteiro é simplesmente movido para trás e o novo cabeçalho é escrito diretamente na frente dos dados. Sem a tecnologia de pacote flexível, a pilha teria de alocar outro tampão e copiar os dados para um novo tampão com o novo cabeçalho, que está a processar intensivamente.

Uma vez que cada tamanho de carga útil do pacote é fixado para um determinado pacote, os dados de aplicação maiores do que o tamanho da carga útil requer vários pacotes acorrentados juntos. Ao preencher um pacote com dados do utilizador, a aplicação deve utilizar o serviço ***nx_packet_data_append***. Este serviço move os dados da aplicação para um pacote. Em situações em que um pacote não é suficiente para guardar os dados dos utilizadores, os pacotes adicionais são atribuídos para armazenar dados do utilizador. Para utilizar acorrentado de pacotes, o condutor deve poder receber ou transmitir a partir de pacotes acorrentados.

Cada conjunto de memórias de pacotes NetX é um recurso público. A NetX não coloca constrangimentos na forma como as piscinas de pacotes são utilizadas.

### <a name="packet-pool-memory-area"></a>Área de memória da piscina de pacotes
A área de memória para a piscina de pacotes é especificada durante a criação. Tal como outras áreas de memória para objetos ThreadX e NetX, pode ser localizado em qualquer lugar do espaço de endereço do alvo. Esta é uma característica importante devido à considerável flexibilidade que confere à aplicação. Por exemplo, suponha que um produto de comunicação tem uma área de memória de alta velocidade para tampão de rede. Esta área de memória é facilmente utilizada transformando-a num conjunto de memórias de pacotes NetX.

### <a name="creating-packet-pools"></a>Criação de piscinas de pacotes
As piscinas de pacotes são criadas durante a inicialização ou durante o tempo de execução por fios de aplicação. Não existem limites no número de conjuntos de memória de pacotes numa aplicação NetX.

### <a name="packet-header-nx_packet"></a>NX_PACKET cabeçalho do pacote
Por predefinição, o NetX coloca o cabeçalho do pacote imediatamente antes da área de carga do pacote. O conjunto de memórias do pacote é basicamente uma série de pacotes — cabeçalhos seguidos imediatamente pela carga útil do pacote. O cabeçalho do pacote ***(NX_PACKET)*** e o layout da piscina do pacote estão representados na Figura 3.

Para o controlador de dispositivos de rede que seja capaz de realizar operações de cópia zero, normalmente o endereço inicial da área de carga útil do pacote está programado na lógica DMA. Certos motores DMA têm requisitos de alinhamento na área de carga útil.

> [!IMPORTANT]
> *O controlador de rede deve ligar para a função ***nx_packet_transmit_release** _ quando a transmissão de um pacote estiver completa. Esta função verifica se o pacote não faz parte de uma fila de saída TCP antes de ser realmente colocado de volta na piscina disponível. A não chamada desta função pode resultar em behavior._ imprevisíveis

![Cabeçalho de pacote e layout de piscina de pacote](./media/user-guide/packet-header-packet-pool-layout.png)

**FIGURA 3. Cabeçalho de pacote e layout de piscina de pacote**

Os campos do cabeçalho do pacote são definidos como mostrado na tabela seguinte. Note que esta tabela não é uma lista completa de todos os membros da estrutura *NX_PACKET.*

| Cabeçalho de pacote          | Objetivo                                                                                                                                                                                                                                                                                                                            |
|------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *nx_packet_pool_owner*   | Este campo aponta para a piscina de pacotes que detém este pacote em particular. Quando o pacote é lançado, é libertado para esta piscina em particular. Com a propriedade da piscina dentro de cada pacote, é possível que um datagrama abra por vários pacotes de várias piscinas de pacotes.                                                         |
| *nx_packet_next*         | Este campo aponta para o próximo pacote dentro do mesmo quadro. Se o NU, não existem pacotes adicionais que fazem parte da moldura. |
| *nx_packet_last*         | Este campo aponta para o último pacote dentro do mesmo pacote de rede. Se o NU, este pacote representa todo o pacote de rede.  |
| *nx_packet_length*       | Este campo contém o número total de bytes em todo o pacote de rede, incluindo o total de todos os bytes em todos os pacotes acorrentados pelo membro *nx_packet_next.* |
| *nx_packet_ip_interface* | Este campo é o bloco de controlo de interface que é atribuído ao pacote quando é recebido pelo controlador de interface, e pelo NetX para pacotes de saída. Um bloco de controlo de interface descreve a interface, por exemplo, endereço de rede, endereço MAC, endereço IP e estado de interface, como ligação ativada e mapeamento físico necessário. |
| *nx_packet_data_start*   | Este campo aponta para o início da área de carga física deste pacote. Não tem de ser imediatamente a seguir o cabeçalho NX_PACKET, mas é o padrão para o serviço ***nx_packet_pool_create.*** |
| *nx_packet_data_end*     | Este campo aponta para o fim da área de carga física deste pacote. A diferença entre este campo e o campo nx_packet_data_start representa o tamanho da carga útil. |
| *nx_packet_prepend_ptr*  | Este campo aponta para a localização de onde os dados do pacote, quer o cabeçalho do protocolo, quer os dados reais, são adicionados à frente dos dados do pacote existentes (se houver) na área de carga útil do pacote. Deve ser maior ou igual ao local do ponteiro *nx_packet_data_start* e inferior ou igual ao *ponteiro nx_packet_append_ptr.*  *Por razões de desempenho, a NetX assume que quando o pacote é passado para os serviços NetX para transmissão, o ponteiro pré-end aponta para um endereço alinhado com palavras longas.* |
| *nx_packet_append_ptr*    | Este campo aponta para o fim dos dados atualmente na área de carga útil do pacote. Deve estar entre o local de memória apontado por *nx_packet_prepend_ptr* e *nx_packet_data_end*. A diferença entre este campo e o campo *nx_packet_prepend_ptr* representa a quantidade de dados neste pacote. |
| *nx_packet_fragment_next* | Este campo é utilizado para conter pacotes fragmentados até que todo o pacote possa ser remontado. |
| *nx_packet_pad*           | Estes campos definem o comprimento do acolchoamento em 4 palavras byte para alcançar o requisito de alinhamento desejado. Este campo é removido se *NX_PACKET_HEADER_PAD* não estiver definido. |
|  |  |

### <a name="packet-header-offsets"></a>Compensações do cabeçalho do pacote

O tamanho do cabeçalho do pacote é definido para permitir espaço suficiente para acomodar o tamanho do cabeçalho. O serviço *nx_packet_allocate* é utilizado para alocar um pacote e ajusta o ponteiro pré-final no pacote de acordo com o tipo de pacote especificado. O tipo de pacote diz ao NetX a compensação necessária para inserir o cabeçalho do protocolo (como UDP, TCP ou ICMP) em frente aos dados do protocolo.

Os seguintes tipos são definidos no NetX para ter em conta o cabeçalho IP e a camada física (Ethernet) no pacote. Neste último caso, presume-se que sejam 16 bytes tendo em consideração o alinhamento de 4 bytes necessário. Os pacotes IP ainda estão definidos no NetX para aplicações para alocar pacotes para redes IP. A tabela a seguir mostra símbolos definidos:

| Tipo de pacote   | Valor |
|---------------|-------|
| NX_IP_PACKET  | 0x24  |
| NX_UDP_PACKET | 0x2c  |
| NX_TCP_PACKET | 0x38  |
|               |       |

### <a name="pool-capacity"></a>Capacidade da Piscina
O número de pacotes numa piscina de pacotes é uma função do tamanho da carga útil e do número total de bytes na área de memória fornecida à piscina de pacotes criar serviço. A capacidade da piscina é calculada dividindo o tamanho do pacote (incluindo o tamanho do cabeçalho NX_PACKET, o tamanho da carga útil e o alinhamento adequado) no número total de bytes na área de memória fornecida.

### <a name="thread-suspension"></a>Suspensão do fio
Os fios de aplicação podem suspender enquanto esperam por um pacote de uma piscina vazia. Quando um pacote é devolvido à piscina, o fio suspenso é dado este pacote e retomado.

Se várias linhas forem suspensas na mesma piscina de pacotes, são retomadas na ordem em que foram suspensas (FIFO).

### <a name="pool-statistics-and-errors"></a>Estatísticas e erros da piscina
Se ativado, o software de gestão de **pacotes** NetX Errors regista várias estatísticas e erros que podem ser úteis para a aplicação. São mantidas as seguintes estatísticas e relatórios de erro para os pools de pacotes:

* Pacotes totais em piscina
* Pacotes gratuitos na piscina
* Pedidos de atribuição vazios da piscina
* Suspensões de atribuição vazias da piscina
* Lançamentos de pacotes inválidos

Todas estas estatísticas e relatórios de erro, com exceção da contagem total e gratuita de pacotes na piscina, são incorporados na biblioteca NetX, a menos que ***NX_DISABLE_PACKET_INFO** _ seja definido. Estes dados estão disponíveis para a aplicação com o serviço _ *_nx_packet_pool_info_get*_*

### <a name="packet-pool-control-block-nx_packet_pool"></a>Bloco de controlo de piscina de pacote NX_PACKET_POOL

As características de cada conjunto de memória de pacotes encontram-se no seu bloco de controlo. Contém informações úteis, tais como a lista ligada de pacotes gratuitos, o número de pacotes gratuitos e o tamanho da carga útil para pacotes nesta piscina. Esta estrutura é definida no ficheiro *nx_api.h.*

Os blocos de controlo da piscina de pacote podem ser localizados em qualquer lugar da memória, mas é mais comum fazer do bloco de controlo uma estrutura global definindo-o fora do âmbito de qualquer função.

## <a name="ip-protocol"></a>Protocolo IP

O componente de Protocolo de Internet (IP) do NetX é responsável pelo envio e receção de pacotes IP na Internet. Na NetX, é o componente em última instância responsável pelo envio e receção de mensagens TCP, UDP, ICMP e IGMP, utilizando o controlador de rede subjacente.

NetX suporta protocolo IP (RFC 791)

### <a name="ip-addresses"></a>Endereços IP

Cada anfitrião na Internet tem um identificador único de 32 bits chamado endereço IP. Existem cinco classes de endereços IP, conforme descrito na Figura 4. As gamas das cinco classes de endereços IP são as seguintes:

| Classe | Intervalo                        |
|-------|------------------------------|
| A     | 0.0.0.0 para 127.255.255.255   |
| B     | 128.0.0.0 para 191.255.255.255 |
| C     | 192.0.0.0 para 223.255.255.255 |
| D     | 224.0.0.0 para 239.255.255.255 |
| E     | 240.0.0.0 para 247.255.255.255 |

**7 bits 24 bits**

![Estrutura de endereços IP](./media/user-guide/ip-address-structure.png)

**FIGURA 4. Estrutura de endereços IP**

Existem também três tipos de especificações de endereços: *unicast,* *transmissão* e *multicast.* Os endereços unicast são os endereços IP que identificam um anfitrião específico na Internet. Os endereços Unicast podem ser uma fonte ou um endereço IP de destino. Um endereço de transmissão identifica todos os anfitriões numa rede ou sub-rede específica e só pode ser usado como endereços de destino. Os endereços de transmissão são especificados tendo a parte de identificação do anfitrião do endereço definida para os outros. Endereços multicast (Classe D) especificam um grupo dinâmico de anfitriões na Internet. Os membros do grupo multicast podem juntar-se e sair quando quiserem.

> [!IMPORTANT]
> *Apenas protocolos sem ligação como uDP sobre IP podem utilizar a difusão e a capacidade de transmissão limitada do grupo multicast.*

> [!IMPORTANT]
> *A macro* IP_ADDRESS é *definido em*  * **nx_api.h_.** Permite uma especificação fácil dos endereços IP utilizando vírgulas em vez de um período. Por exemplo, IP_ADDRESS (128,0,0,0) _specifies o endereço da primeira classe B mostrado na Figura 4.*

### <a name="ip-gateway-address"></a>Endereço IP Gateway

Os gateways de rede ajudam os anfitriões nas suas redes a transmitir pacotes destinados a destinos fora do domínio local. Cada nó tem algum conhecimento de qual próximo salto enviar para, seja o destino de um dos seus vizinhos, ou através de uma mesa de encaminhamento estático pré-programada. No entanto, se estas abordagens falharem, o nó deve encaminhar o pacote para o seu gateway predefinido, que tem mais informações sobre como encaminhar o pacote para o seu destino. Note que o gateway predefinido deve ser diretamente acessível através de uma das interfaces físicas anexas à instância IP. A aplicação chama ***nx_ip_gateway_address_set*** para configurar o endereço de gateway ip predefinido.

### <a name="ip-header"></a>Cabeçalho IP

Para que qualquer pacote IP seja enviado na Internet, deve ter um cabeçalho IP. Quando os protocolos de nível superior (UDP, TCP, ICMP ou IGMP) ligam para o componente IP para enviar um pacote, o módulo de transmissão IP coloca um cabeçalho IP na frente dos dados. Inversamente, quando os pacotes IP são recebidos da rede, o componente IP remove o cabeçalho IP do pacote antes da entrega aos protocolos de nível superior. A figura 5 mostra o formato do cabeçalho IP.

![Formato de cabeçalho IP](./media/user-guide/ip-header-format.png)

**FIGURA 5. Formato de cabeçalho IP**

> [!IMPORTANT]
> *Espera-se que todos os cabeçalhos na implementação TCP/IP estejam em grande formato endiano. Neste formato, o byte mais significativo da palavra reside no endereço byte mais baixo. Por exemplo, a versão de 4 bits e o comprimento do cabeçalho de 4 bits do cabeçalho IP devem ser localizados no primeiro byte do cabeçalho.*

Os campos do cabeçalho IP são definidos da seguinte forma:

**Finalidade do campo do cabeçalho IP**

***Versão de 4 bits*** Este campo contém a versão de IP que este cabeçalho representa. Para a versão IP 4, que é o que o NetX suporta, o valor deste campo é 4.

***Comprimento do cabeçalho de 4 bits*** Este campo especifica o número de palavras de 32 bits no cabeçalho IP. Se não houver palavras de opção, o valor para este campo é 5.

***Tipo de serviço de 8 bits (TOS)*** Este campo especifica o tipo de serviço solicitado para este pacote IP. Os pedidos válidos são os seguintes:

| **Pedido de TOS**     | **Valor** |
| ------------------- | --------- |
| Normal              | 0x00      |
| Atraso Mínimo       | 0x10      |
| Dados Máximos        | 0x08      |
| Fiabilidade máxima | 0x04      |
| Custo Mínimo        | 0x02      |

***Comprimento total de 16 bits*** Este campo contém o comprimento total do datagrama IP em bytes, incluindo o cabeçalho IP. Um datagrama IP é a unidade básica de informação encontrada numa Internet TCP/IP. Contém um endereço de destino e origem para além dos dados. Por ser um campo de 16 bits, o tamanho máximo de um datagrama IP é de 65.535 bytes.

***Identificação de 16 bits*** O campo é um número usado para identificar exclusivamente cada datagrama IP enviado de um anfitrião. Este número é tipicamente incrementado após o envio de um datagrama IP. É especialmente útil na montagem de fragmentos de pacotes IP recebidos.

***Bandeiras de 3 bits*** Este campo contém informações de fragmentação IP. O bit 14 é a parte do "não se fragmentar". Se esta bit estiver definida, o datagrama ip de saída não será fragmentado. O bit 13 é a parte "mais fragmentos". Se esta parte estiver definida, há mais fragmentos. Se esta parte estiver clara, este é o último fragmento do pacote IP.

**Finalidade do campo do cabeçalho IP**

***Compensação de fragmentos de 13 bits*** Este campo contém os 13 bits superiores da offset do fragmento. Por causa disso, as compensações de fragmentos só são permitidas em limites de 8 bytes. O primeiro fragmento de um datagrama ip fragmentado terá o conjunto de bits "mais fragmentos" e terá uma compensação de 0.

***8 bits de tempo para viver (TTL)*** Este campo contém o número de routers que este datagrama pode passar, o que limita o tempo de vida útil do datagrama.

***Protocolo de 8 bits*** Este campo especifica qual o protocolo que está a utilizar o datagrama IP. Segue-se uma lista de protocolos válidos e seus valores:

| Protocolo | Valor |
|----------|-------|
| ICMP     | 0x01  |
| IGMP     | 0x02  |
| TCP      | 0X06  |
| UDP      | 0X11  |
|          |       |


***Cheque de 16 bits*** Este campo contém a parte de verificação de 16 bits que cobre apenas o cabeçalho IP. Existem despesas de verificação adicionais nos protocolos de nível superior que cobrem a carga útil ip.

***Endereço IP de origem de 32 bits*** Este campo contém o endereço IP do remetente e é sempre um endereço de anfitrião.

***Endereço IP de destino de 32 bits*** Este campo contém o endereço IP do recetor ou dos recetores se o endereço for um endereço transmitido ou multicast.

### <a name="creating-ip-instances"></a>Criação de Instâncias IP

As instâncias IP são criadas durante a inicialização ou durante o tempo de execução por fios de aplicação. O endereço IP inicial, máscara de rede, conjunto de pacotes predefinidos, controlador de mídia e memória e prioridade do fio IP interno são definidos pelo serviço *nx_ip_create.* Se a aplicação rubricar a instância IP com o seu endereço IP definido para um endereço inválido (0.0.0.0), presume-se que o endereço de interface será resolvido por configuração manual mais tarde, via RARP, ou através de DHCP ou protocolos semelhantes.

Para sistemas com múltiplas interfaces de rede, a interface principal é designada quando se chama *nx_ip_create*. Cada interface adicional pode ser anexada à mesma instância IP, chamando *nx_ip_interface_attach*. Este serviço armazena informações sobre a interface de rede (como endereço IP, máscara de rede) no bloco de controlo de interface, e associa a instância do condutor ao bloco de controlo de interface na instância IP. Como o condutor recebe um pacote de dados, precisa de armazenar a informação da interface na estrutura NX_PACKET antes de reencaminhar para a lógica de receção IP. Note que uma instância IP já deve ser criada antes de anexar quaisquer interfaces.

 ### <a name="ip-send"></a>IP Enviar
 O processamento de envio IP no NetX é muito simplificado.

O ponteiro pré-final do pacote é movido para trás para acomodar o cabeçalho IP. O cabeçalho IP é preenchido (com todas as opções especificadas pela camada do protocolo de chamada), a estação de verificação IP é calculada em linha e o pacote é enviado para o controlador de rede associado. Além disso, a fragmentação de saída também é coordenada a partir do processamento de envio de IP.

Para IP, o NetX inicia pedidos de ARP se for necessário mapeamento físico para o endereço IP de destino.

> [!IMPORTANT]
> *Para a conectividade IP, os pacotes que requerem resolução de endereço IP (isto é, mapeamento físico) são encadeados na fila ARP até que o número de pacotes em fila exceda a profundidade da fila ARP (definida pelo* *símbolo **NX_ARP_MAX_QUEUE_DEPTH).** Se a* profundidade da *fila for alcançada, o NetX removerá o pacote mais antigo da fila e continuará à espera da resolução de endereços para os restantes pacotes encadeados. Por outro lado, se uma entrada ARP não for resolvida, os pacotes pendentes na entrada ARP são lançados após o tempo de entrada do ARP.*

Para sistemas com múltiplas interfaces de rede, o NetX escolhe uma interface com base no endereço IP de destino. Aplica-se o seguinte procedimento ao processo de seleção:

1. Se um endereço de destino for transmitido IP ou multicast, e se for especificada uma interface de saída válida, utilize essa interface. Caso contrário, a primeira interface física é usada.

2. Se o endereço de destino for encontrado na tabela de encaminhamento estático, a interface associada ao gateway é utilizada.

3. Se o destino estiver ligado, a interface on-link é utilizada.

4. Se o endereço de destino for um endereço de retorno 127.0.0.1, a interface loopback é utilizada.

5. Se o gateway predefinido estiver corretamente configurado, utilize a interface associada ao gateway predefinido para transmitir o pacote.

6. O pacote de saída é retirado se tudo o que precede falhar.

### <a name="ip-receive"></a>IP Receber

O processamento de receção IP é chamado do controlador de rede ou do fio IP interno (para processamento de pacotes na fila de pacotes recebidos diferidos). O processamento de receção IP examina o campo do protocolo e tenta enviar o pacote para o componente de protocolo adequado. Antes de o pacote ser realmente despachado, o cabeçalho IP é removido avançando o ponteiro pré-final para além do cabeçalho IP.

O processamento de receção IP também deteta pacotes IP fragmentados e executa as medidas necessárias para os remontar se a fragmentação estiver ativada. Se for necessária fragmentação, mas não ativada, o pacote é largado.

O NetX determina a interface de rede adequada com base na interface especificada no pacote. Se a interface do pacote for NU, o NetX desrescumula a interface primária. Isto é feito para garantir compatibilidade com os condutores legados NetX Ethernet.

### <a name="raw-ip-send"></a>Envio de IP cru

Um pacote IP cru é um quadro IP que contém carga útil do protocolo de camada superior não suportado diretamente (e processado) pelo NetX. Um pacote cru permite que os desenvolvedores definam as suas próprias aplicações baseadas em IP. Uma aplicação pode enviar pacotes IP crus diretamente utilizando o serviço ***nx_ip_raw_packet_send** _ se o processamento de pacotes IP crus tiver sido ativado com o serviço _*_nx_ip_raw_packet_enabled._*_ Se o endereço de destino for um endereço multicast ou de transmissão, no entanto, o NetX desrescume da primeira interface (primária). Portanto, para enviar esses pacotes em interfaces secundárias, a aplicação deve utilizar o serviço _ *_nx_ip_raw_packet_interface_send_** para especificar o endereço de origem a utilizar para o pacote de saída.

### <a name="raw-ip-receive"></a>Receber IP cru

Se o processamento de pacotes IP cru estiver ativado, a aplicação pode receber pacotes IP crus através do serviço ***nx_ip_raw_packet_receive** _ . Todos os pacotes de entrada são processados de acordo com o protocolo especificado no cabeçalho IP. Se o protocolo especificar UDP, TCP, IGMP ou ICMP, a NetX processará o pacote utilizando o manipulador apropriado para o tipo de protocolo de pacote. Se o protocolo não for um destes protocolos, e a receção ip bruta estiver ativada, o pacote de entrada será colocado na fila de pacotes brutos à espera que a aplicação o receba através do serviço _ *_nx_ip_raw_packet_receive*_*. Além disso, os fios de aplicação podem suspender com um intervalo opcional enquanto aguardam um pacote IP cru.

### <a name="default-packet-pool"></a>Piscina de pacotes predefinidos

Cada instância IP recebe um pacote de pacote padrão durante a criação. Este pacote de piscina é utilizado para alocar pacotes para ARP, RARP, ICMP, IGMP, vários pacotes de controlo TCP (tais como SYN, ACK). Se o pacote predefinido estiver vazio quando o NetX precisar de alocar um pacote, o NetX poderá ter de abortar a operação em particular e devolver uma mensagem de erro se possível.

### <a name="ip-helper-thread"></a>Fio de ajudante IP

Cada instância IP tem um fio de ajuda. Este fio é responsável pelo manuseamento de todo o processamento de pacotes diferidos e de todo o processamento periódico. O fio do ajudante IP é criado em ***nx_ip_create.*** É aqui que o fio é dado a sua pilha e prioridade. Note que o primeiro processamento na linha de ajuda IP é terminar a inicialização do controlador de rede associada ao serviço de criação IP. Após a inicialização do controlador de rede estar concluída, o fio do ajudante inicia um ciclo interminável para processar pacotes e pedidos periódicos.

> [!IMPORTANT]
> *Se o comportamento inexplicável for visto dentro do fio do ajudante IP, aumentar o tamanho da pilha durante o serviço de criação IP é o primeiro passo de depurar. Se a pilha for muito pequena, o fio do ajudante IP pode estar a sobrepor-se à memória, o que pode causar problemas incomuns.*

### <a name="thread-suspension"></a>Suspensão do fio

Os fios de aplicação podem suspender enquanto tentam receber pacotes IP crus. Depois de recebido um pacote cru, o novo pacote é dado ao primeiro fio suspenso e esse fio é retomado. Os serviços NetX para receber pacotes têm um tempo de suspensão opcional. Quando um pacote é recebido ou o tempo limite expira, o fio de aplicação é retomado com o estado de conclusão adequado.

### <a name="ip-statistics-and-errors"></a>Estatísticas e erros ip

Se ativado, o NetX regista várias estatísticas e erros que podem ser úteis à aplicação. As seguintes estatísticas e relatórios de erro são mantidos para cada instância DEP:

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

As características de cada instância IP encontram-se no seu bloco de controlo. Contém informações úteis, tais como endereços IP e máscaras de rede de cada dispositivo de rede, e uma tabela de IP vizinho e mapeamento de endereços de hardware físico. Esta estrutura é definida nos blocos de controlo de instância ip ***nx_api.h*** podem ser localizados em qualquer lugar da memória, mas é mais comum fazer do bloco de controlo uma estrutura global definindo-o fora do âmbito de qualquer função.

### <a name="static-ip-routing"></a>Encaminhamento IP estático

A funcionalidade de encaminhamento estático permite que uma aplicação especifique uma rede IP e o próximo endereço de lúpulo para endereços IP específicos fora da rede. Se o encaminhamento estático estiver ativado, o NetX procura através da tabela de encaminhamento estático para uma entrada correspondente ao endereço de destino do pacote a enviar. Se não for encontrado qualquer correspondência, o NetX procura através da lista de interfaces físicas e escolhe um endereço IP de origem e próximo endereço de lúpulo baseado no endereço IP de destino e na máscara de rede. Se o destino não corresponder a nenhum dos endereços IP dos controladores de rede ligados à instância IP, o NetX escolhe uma interface que está diretamente ligada ao gateway predefinido e utiliza o endereço IP da interface como endereço de origem e o gateway predefinido como o próximo salto.

As entradas podem ser adicionadas e removidas da tabela de encaminhamento estático utilizando os serviços ***nx_ip_static_route_add*** e ***nx_ip_static_route_delete** _, respectivamente. Para utilizar o encaminhamento estático, a aplicação do anfitrião deve ativar esta função definindo _ *_NX_ENABLE_IP_STATIC_ROUTING_*.*

> [!IMPORTANT]
> *Ao adicionar uma entrada na tabela de encaminhamento estático, o NetX verifica uma entrada correspondente para o endereço de destino especificado já na tabela. Se existir, dá preferência à entrada com a rede mais pequena (prefixo mais longo) na máscara de rede.*

### <a name="ip-fragmentation"></a>Fragmentação ip

O dispositivo de rede pode ter limites no tamanho dos pacotes de saída. Este limite é chamado de unidade de transmissão máxima (MTU). IP MTU é o maior tamanho de quadro IP que o controlador de camada de ligação é capaz de transmitir sem fragmentar o pacote IP. Durante uma fase de inicialização do controlador do dispositivo, o módulo do condutor deve configurar o seu tamanho IP MTU através do serviço ***nx_ip_interface_mtu_set**.*

Embora não recomendado, a aplicação pode gerar datagramas maiores do que o IP MTU subjacente suportado pelo dispositivo. Antes de transmitir tais datagramas de IP, a camada IP deve fragmentar estes pacotes. Ao receber quadros IP fragmentados, a extremidade recetora deve armazenar todos os quadros IP fragmentados com o mesmo ID de fragmentação e montá-los em ordem. Se a lógica de receção ip não for capaz de recolher todos os fragmentos para restaurar o quadro IP original no tempo, todos os fragmentos são libertados. Cabe ao protocolo da camada superior detetar tal perda de pacote e recuperá-la.

Para suportar a fragmentação e o funcionamento da fragmentação ip, o designer de sistema deve ativar a função de fragmentação IP no NetX utilizando o serviço ***nx_ip_fragment_enable.*** Se esta função não estiver ativada, os pacotes IP fragmentados de entrada são descartados, bem como pacotes que excedam o MTU do controlador de rede.

> [!IMPORTANT]
> *A lógica de fragmentação IP pode ser completamente removida definindo*  * **NX_DISABLE_FRAGMENTATION** _ _when construindo a bibliotecaNetX. Fazê-lo ajuda a reduzir o tamanho do código do NetX.*

## <a name="address-resolution-protocol-arp-in-ip"></a>Protocolo de Resolução de Endereços (ARP) em IP

O Protocolo de Resolução de Endereços (ARP) é responsável por mapear dinamicamente endereços IP de 32 bits aos dos meios físicos subjacentes (RFC 826). Ethernet é o meio físico mais típico, e suporta endereços de 48 bits. A necessidade de ARP é determinada pelo controlador de rede fornecido ao serviço ***nx_ip_create.*** Se for necessário um mapeamento físico, o controlador da rede deve definir a bandeira ***nx_interface_address_mapping_needed*** no strcuture da interface.

### <a name="arp-enable"></a>Ativar a ARP
Para que a ARP funcione corretamente, deve primeiro ser ativada pela aplicação com o serviço ***nx_arp_enable.*** Este serviço estabelece várias estruturas de dados para o processamento de ARP, incluindo a criação de uma área de cache ARP a partir da memória fornecida ao serviço de ativação ARP.

### <a name="arp-cache"></a>ARP Cache
A cache ARP pode ser vista como uma matriz de estruturas internas de dados de mapeamento ARP. Cada estrutura interna é capaz de manter a relação entre um endereço IP e um endereço de hardware físico. Além disso, cada estrutura de dados tem ponteiros de ligação para que possa fazer parte de várias listas ligadas.

A aplicação pode procurar um endereço IP a partir da cache ARP fornecendo o endereço MAC de hardware usando o serviço ***nx_arp_ip_address_find** _ se o mapeamento existir na tabela ARP. Da mesma forma, o serviço _ *_nx_arp_hardware_address_find_** devolve o endereço MAC para um determinado endereço IP.


### <a name="arp-dynamic-entries"></a>Entradas dinâmicas ARP

Por predefinição, o ARP permite que todas as entradas na cache ARP na lista de entradas ARP dinâmicas disponíveis. Uma entrada dinâmica de ARP é atribuída a partir desta lista pelo NetX quando é detetado um pedido de envio para um endereço IP não mapeado. Após a atribuição, a entrada ARP é configurada e um pedido ARP é enviado para os meios físicos.

Uma entrada dinâmica também pode ser criada pelo serviço ***nx_arp_dynamic_entry_set***.

> [!IMPORTANT]
> *Se todas as entradas ARP dinâmicas estiverem a ser utilizadas, a entrada ARP menos utilizada é substituída por um novo mapeamento.*

### <a name="arp-static-entries"></a>Entradas Estáticas ARP
A aplicação também pode configurar mapeamento ARP estático utilizando o serviço ***nx_arp_static_entry_create.*** Este serviço atribui uma entrada ARP da lista dinâmica de entrada ARP e coloca-a na lista estática com as informações de mapeamento fornecidas pela aplicação. As entradas ARP estáticas não estão sujeitas a reutilização ou envelhecimento. A aplicação pode eliminar uma entrada estática utilizando o serviço ***nx_arp_static_entry_delete***.
Para remover todas as entradas estáticas na tabela ARP, a aplicação pode utilizar o serviço ***nx_arp_static_entries_delete***.

### <a name="automatic-arp-entry"></a>Entrada Automática de ARP
NetX regista o mapeamento IP/MAC do par após as respostas dos pares ao pedido de ARP. O NetX também implementa a funcionalidade de entrada automática de ARP onde regista o mapeamento de endereços PEER/MAC com base em pedidos ARP não solicitados da rede. Esta funcionalidade permite que a tabela ARP seja povoada com informações de pares, reduzindo o atraso necessário para passar pelo ciclo de pedido/resposta ARP. No entanto, a desvantagem com a ativação automática do ARP é que a tabela ARP tende a encher-se rapidamente numa rede movimentada com muitos nós na ligação local, o que acabaria por levar à substituição da entrada do ARP.

Esta funcionalidade é ativada por padrão. Para desativá-la, a biblioteca NetX deve ser compilada com o símbolo ***NX_DISABLE_ARP_AUTO_ENTRY*** definido.

### <a name="arp-messages"></a>Mensagens ARP

Como mencionado anteriormente, uma mensagem de pedido ARP é enviada quando a tarefa IP deteta que o mapeamento é necessário para um endereço IP. Os pedidos de ARP são enviados periodicamente (a cada ***NX_ARP_UPDATE_RATE** _ segundos) até que seja recebida uma resposta ARP correspondente. Um total de _ *_NX_ARP_MAXIMUM_RETRIES_** pedidos de ARP são feitos antes da tentativa de ARP ser abandonada. Quando uma resposta ARP é recebida, as informações de endereço físico associados são armazenadas na entrada ARP que está na cache.

Para sistemas multihomes, o NetX determina qual a interface para enviar os pedidos e respostas ARP com base no endereço de destino especificado.

> [!IMPORTANT]
> *Os pacotes IP de saída são em fila enquanto o NetX aguarda a resposta ARP. O número de* *pacotes* IP de saída em fila é definido pela NX_ARP_MAX_QUEUE_DEPTH constante  * .*

NetX também responde a pedidos de ARP de outros nós na rede IP local. Quando é feito um pedido de ARP externo que corresponde ao endereço IP atual da interface que recebe o pedido ARP, o NetX constrói uma mensagem de resposta ARP que contém o endereço físico atual.

Os formatos dos pedidos e respostas da Ethernet ARP são apresentados na Figura 6 e são descritos abaixo:

| Campo de Pedido/Resposta       | Objetivo    |
|------------------------------|-----------------|
| Endereço de destino Ethernet | Este campo de 6 bytes contém o endereço de destino para a resposta ARP e é uma transmissão (todas) para pedidos ARP. Este campo é configurado pelo controlador de rede. |
| Endereço de origem Ethernet      | Este campo de 6 bytes contém o endereço do remetente do pedido ou resposta ARP e é criado pelo controlador de rede. |
| Tipo de quadro                   | Este campo de 2 bytes contém o tipo de quadro Ethernet presente e, para pedidos e respostas ARP, este é igual a 0x0806. Este é o último campo que o controlador de rede é responsável pela configuração. |
| Tipo de hardware                | Este campo de 2 bytes contém o tipo de hardware, que é 0x0001 para o Ethernet. |
| Tipo de Protocolo                | Este campo de 2 bytes contém o tipo de protocolo, que é 0x0800 para endereços IP. |
| Tamanho do hardware                | Este campo de 1 byte contém o tamanho do endereço de hardware, que é 6 para endereços Ethernet. |


![Formato de pacote ARP](./media/user-guide/arp-packet-format.png)

**FIGURA 6. Formato de pacote ARP**

| Campo de Pedido/Resposta | Objetivo  |
|---|---|
| Tamanho do protocolo | Este campo de 1 byte contém o tamanho do endereço IP, que é 4 para endereços IP.  |
| Código de Operação | Este campo de 2 bytes contém a operação para este pacote ARP. Um pedido ARP é especificado com o valor de 0x0001, enquanto uma resposta ARP é representada por um valor de 0x0002.  |
| Endereço Ethernet Ethernet | Este campo de 6 bytes contém o endereço Ethernet do remetente. |
| Endereço IP remetente | Este campo de 4 bytes contém o endereço IP do remetente. |
| Endereço Ethernet alvo | Este campo de 6 bytes contém o endereço Ethernet do alvo. |
| Endereço IP alvo | Este campo de 4 bytes contém o endereço IP do alvo. |

> [!IMPORTANT]
> *Os pedidos e respostas da ARP são pacotes ao nível da Ethernet. Todos os outros pacotes TCP/IP são encapsulados por um cabeçalho de pacote IP.*

> [!IMPORTANT]
> *Espera-se que todas as mensagens ARP na implementação TCP/IP estejam em grande formato endiano. Neste formato, o byte mais significativo da palavra reside no endereço byte mais baixo.*

### <a name="arp-aging"></a>Envelhecimento ARP

NetX suporta a invalidação de entrada ARP dinâmica automática. ***NX_ARP_EXPIRATION_RATE** _specifies o número de segundos que um endereço IP estabelecido para mapeamento físico permanece válido. Após a expiração, a entrada ARP é removida da cache ARP. A próxima tentativa de envio para o endereço IP correspondente resultará num novo pedido de ARP. Definição _ *_NX_ARP_EXPIRATION_RATE_** a zero desativa o envelhecimento do ARP, que é a configuração padrão.

### <a name="arp-defend"></a>ARP Defender

Quando um pacote de resposta ARP ou ARP é recebido e o remetente tem o mesmo endereço IP, que entra em conflito com o endereço IP deste nó, o NetX envia um pedido de ARP para esse endereço como defesa. Se o pacote ARP de conflito for recebido mais de uma vez em 10 segundos, a NetX não envia mais pacotes de defesa. O intervalo padrão de 10 segundos pode ser redefinido por ***NX_ARP_DEFEND_INTERVAL** _. Este comportamento segue a política especificada em 2.4(c) de RFC5227. Uma vez que o Windows XP ignora o anúncio do ARP como resposta para a sua sonda ARP, o utilizador pode definir _*_NX_ARP_DEFEND_BY_REPLY_**para enviar a resposta ARP como defesa adicional.

### <a name="arp-statistics-and-errors"></a>Estatísticas e erros da ARP

Se ativado, o software ARP NetX regista várias estatísticas e erros que podem ser úteis à aplicação. São mantidas as seguintes estatísticas e relatórios de erro para o processamento de ARP de cada IP:

- Total de pedidos de ARP enviados
- Total de pedidos de ARP recebidos
- Total de respostas ARP enviadas
- Total de respostas ARP recebidas
- Entradas dinâmicas totais do ARP
- Total de entradas estáticas ARP
- Total de entradas envelhecidas em ARP
- Total de mensagens inválidas da ARP

Todas estas estatísticas e relatórios de erro estão disponíveis para a aplicação com o serviço ***nx_arp_info_get.***

## <a name="reverse-address-resolution-protocol-rarp-in-ip"></a>Protocolo de Resolução de Endereços Reversos (RARP) em IP

O Protocolo de Resolução de Endereços Reversos (RARP) é o protocolo para solicitar a atribuição de rede dos endereços IP de 32 bits do anfitrião (RFC 903). Isto é feito através de um pedido RARP e continua periodicamente até que um membro da rede atribua um endereço IP à interface de rede de anfitrião numa resposta RARP. A aplicação cria uma instância IP pelo serviço ***nx_ip_create*** com um endereço IP zero. Se o RARP estiver ativado pela aplicação, pode utilizar o protocolo RARP para solicitar um endereço IP a partir do servidor de rede acessível através da interface que tem um endereço IP zero.

### <a name="rarp-enable"></a>Ativar RARP

Para utilizar o RARP, a aplicação deve criar a instância IP com um endereço IP de zero e, em seguida, ativar o RARP utilizando o serviço ***nx_rarp_enable***. Para os sistemas multihome, pelo menos um dispositivo de rede associado à instância IP deve ter um endereço IP de zero. O processamento rarp envia periodicamente mensagens de pedido rarp para o sistema NetX que requer um endereço IP até que seja recebida uma resposta RARP válida com o endereço IP designado pela rede. Neste momento, o processamento de RARP está completo.

Depois de o RARP ter sido ativado, este é desativado automaticamente depois de resolvidos todos os endereços de interface. O pedido pode forçar a RARP a encerrar utilizando o serviço ***nx_rarp_disable***.

###  <a name="rarp-request"></a>Pedido RARP

O formato de um pacote de pedido RARP é quase idêntico ao pacote ARP mostrado na Figura 6 no tópico [ARP Messages](#arp-messages). A única diferença é que o campo do tipo de fotogramas é 0x8035 e o campo *Código de Operação* é 3, designando um pedido RARP. Como mencionado anteriormente, os pedidos de RARP serão enviados periodicamente (a cada ***NX_RARP_UPDATE_RATE*** segundos) até que seja recebida uma resposta RARP com o endereço IP atribuído à rede.

> [!IMPORTANT]
> *Espera-se que todas as mensagens RARP na implementação TCP/IP estejam em grande formato endiano. Neste formato, o byte mais significativo da palavra reside no endereço byte mais baixo.*

### <a name="rarp-reply"></a>Resposta RARP

As mensagens de resposta RARP são recebidas da rede e contêm o endereço IP atribuído à rede para este anfitrião. O formato de um pacote de resposta RARP é quase idêntico ao pacote ARP indicado na Figura 6. A única diferença é que o campo do tipo de fotogramas é 0x8035 e o campo *Código de Operação* é 4, que designa uma resposta RARP. Depois de recebido, o endereço IP é configurado no caso IP, o pedido periódico de RARP é desativado, e a instância IP está agora pronta para o funcionamento normal da rede.

Para os anfitriões multihome, o endereço IP é aplicado à interface de rede de pedidos. Se existirem outras interfaces de rede que ainda solicitam uma atribuição de endereço IP, o serviço raRP periódico continua até que todos os pedidos de endereço IP de interface sejam resolvidos.

> [!IMPORTANT]
> *O pedido não deve utilizar a instância IP até que o processamento rarp esteja completo. O **nx_ip_status_check** pode ser utilizado por aplicações para aguardar a conclusão do RARP. Para sistemas multihome, a aplicação não deve utilizar a interface de pedido até que o processamento rarp esteja completo nessa interface. O estado do endereço IP no dispositivo secundário pode ser verificado com o serviço **nx_ip_interface_status_check.***

### <a name="rarp-statistics-and-errors"></a>Estatísticas e erros da RARP

Se ativado, o software NetX RARP regista várias estatísticas e erros que podem ser úteis à aplicação. São mantidas as seguintes estatísticas e relatórios de erro para o processamento de RARP de cada IP:

- Total de pedidos de RARP enviados
- Total de respostas rarp recebidas
- Total de mensagens inválidas da RARP

Todas estas estatísticas e relatórios de erro estão disponíveis para a aplicação com o serviço ***nx_rarp_info_get.***

## <a name="internet-control-message-protocol-icmp"></a>Protocolo de mensagem de controlo da Internet (ICMP)

O Protocolo de Mensagem de Controlo de Internet para IP (ICMP) limita-se a passar informações de erro e controlo entre membros da rede IP.

Tal como a maioria das outras mensagens de camada de aplicação (por exemplo, TCP/IP), as mensagens ICMP são encapsuladas por um cabeçalho IP com a designação do protocolo ICMP.

### <a name="icmp-statistics-and-errors"></a>Estatísticas e erros do ICMP

Se ativado, o NetX regista várias estatísticas e erros do ICMP que podem ser úteis à aplicação. São mantidas as seguintes estatísticas e relatórios de erro para o processamento do ICMP de cada IP:

- Total de pings ICMP enviados
- Total de tempo de ping ICMP
- Fios de ping total do ICMP suspensos
- Total de respostas de ping do ICMP recebidas
- Erros totais de verificação do ICMP
- Total de mensagens não manipuladas do ICMP

Todas estas estatísticas e relatórios de erro estão disponíveis para a aplicação com o serviço ***nx_icmp_info_get.***

### <a name="icmp-enable"></a>ICMP Ativar
Antes de as mensagens ICMP poderem ser processadas pelo NetX, a aplicação deve ligar para o serviço ***nx_icmp_enable*** para permitir o processamento do ICMP. Depois disso, a aplicação pode emitir pedidos de ping e pacotes de ping de entrada no campo.

### <a name="icmp-echo-request"></a>Pedido de Eco ICMP
Um pedido de eco é um tipo de mensagem ICMP que é normalmente usada para verificar a existência de um nó específico na rede, identificado pelo seu endereço IP anfitrião. O comando de ping popular é implementado usando mensagens de pedido de eco/eco ICMP. Se o anfitrião específico estiver presente, a sua pilha de rede processa o pedido de ping e as respostas com uma resposta de ping. A Figura 7 detalha o formato de mensagem de ping ICMP.

![Mensagem de ping ICMP](./media/user-guide/icmp-ping-message.png)

**FIGURA 7. Mensagem de ping ICMP**

> [!IMPORTANT]
> *Espera-se que todas as mensagens ICMP na implementação TCP/IP estejam em grande formato endiano. Neste formato, o byte mais significativo da palavra reside no endereço byte mais baixo.*

A tabela a seguir descreve o formato do cabeçalho ICMP:

| Campo de Cabeçalho    | Objetivo |
|-----------------|---------------------------------------------------|
| Tipo            | Este campo especifica a mensagem ICMP (bits 31-24). As mais comuns são: 0 Echo Answer 8 Echo Request |
| Código            | Este campo é de contexto específico no campo tipo (bits 23-16). Para um pedido de eco ou resposta, o código está definido para zero. |
| Soma de verificação        | Este campo contém a parte de verificação de 16 bits da soma complementar da mensagem ICMP, incluindo todo o cabeçalho ICMP a começar pelo campo Tipo. Antes de gerar a caixa de verificação, o campo de verificação está limpo.                 |
| Identificação  | Este campo contém um valor de identificação que identifica o hospedeiro; um hospedeiro deve utilizar o ID extraído de um pedido DE ECO na RESPOSTA ECHO (bits 31-16). |
| Número de sequência | Este campo contém um valor de ID; um hospedeiro deve utilizar o ID extraído de um pedido DE ECO na RESPOSTA ECHO (bits 31-16). Ao contrário do campo do identificador, este valor mudará num pedido de Eco subsequente do mesmo anfitrião (bits 15-0). |


### <a name="icmp-echo-response"></a>Resposta ao eco do ICMP
Uma resposta de ping é outro tipo de mensagem ICMP que é gerada internamente pela componente ICMP em resposta a um pedido externo de ping. Além do reconhecimento, a resposta ao ping contém também uma cópia dos dados do utilizador fornecidos no pedido de ping.

## <a name="internet-group-management-protocol-igmp"></a>Protocolo de Gestão do Grupo de Internet (IGMP)

O Protocolo de Gestão do Grupo internet (IGMP) fornece um dispositivo para comunicar com os seus vizinhos e seus routers que pretende receber, ou aderir, a um grupo multicast IP (RFC 1112 e RFC 2236). Um grupo multicast é basicamente uma coleção dinâmica de membros da rede e é representado por um endereço IP classe D. Os membros do grupo multicast podem sair a qualquer momento, e os novos membros podem aderir a qualquer momento. A coordenação envolvida na adesão e saída do grupo é da responsabilidade do IGMP.

### <a name="igmp-enable"></a>IGMP Ativar

Antes de qualquer atividade multicasting poder ocorrer no NetX, a aplicação deve ligar para o ***serviço nx_igmp_enable.*** Este serviço realiza a inicialização básica do IGMP em preparação para pedidos multicast.

### <a name="multicast-ip-addressing"></a>Endereço IP multicast

Como mencionado anteriormente, os endereços multicast são na verdade endereços IP de classe D, como mostrado na Figura 4 na página 58. Os 28 bits inferiores do endereço classe D correspondem ao ID do grupo multicast. Há uma série de endereços multicast pré-definidos. No entanto, o *endereço de todos os anfitriões* (244.0.0.1) é particularmente importante para o processamento do IGMP. O *endereço de todos os anfitriões* é utilizado pelos routers para consultar todos os membros multicasts para informar em que grupos multicast pertencem.

### <a name="physical-address-mapping-in-ip"></a>Mapeamento de endereço físico em IP

Endereços multicast classe D mapeam diretamente para endereços físicos Ethernet variando de 01.00.5e.00.00.00 a 01.00.5e.7f.ff.ff. Os 23 bits inferiores do mapa de endereços multicast IP diretamente para os 23 bits inferiores do endereço Ethernet.

### <a name="multicast-group-join"></a>Grupo Multicast Junta-se

As aplicações que precisam de aderir a um determinado grupo multicast podem fazê-lo chamando o ***serviço nx_igmp_multicast_join.*** Este serviço acompanha o número de pedidos para se juntar a este grupo multicast. Se este for o primeiro pedido de candidatura para aderir ao grupo multicast, é enviado um relatório IGMP na rede primária indicando a intenção deste anfitrião de se juntar ao grupo. Em seguida, o controlador de rede é chamado a configurar para ouvir pacotes com o endereço Ethernet para este grupo multicast.

Num sistema multihome, se o grupo multicast estiver acessível através de uma interface específica, a aplicação utilizará o serviço ***nx_igmp_multicast_interface_join*** em vez de ***nx_igmp_multicast_join****, que se limita a grupos multicast na rede primária.

### <a name="multicast-group-leave"></a>Licença de grupo multicast

As aplicações que necessitem de deixar um grupo multicast previamente aderido podem fazê-lo chamando o ***serviço nx_igmp_multicast_leave.*** Este serviço reduz a contagem interna associada à quantidade de vezes que o grupo se juntou. Se não houver pedidos de participação pendentes para um grupo, o controlador de rede é chamado a desativar a audição de pacotes com o endereço Ethernet deste grupo multicast

### <a name="multicast-loopback"></a>Multicast Loopback

Um pedido pode pretender receber tráfego multicast originário de uma das fontes no mesmo nó. Isto requer que o componente multicast IP tenha o loopback ativado utilizando o serviço ***nx_igmp_loopback_enable***.

### <a name="igmp-report-message"></a>Mensagem de relatório IGMP

Quando a aplicação se junta a um grupo multicast, uma mensagem de relatório IGMP é enviada através da rede para indicar a intenção do anfitrião de se juntar a um determinado grupo multicast. O formato da mensagem de relatório IGMP é mostrado na Figura 8. O endereço de grupo multicast é utilizado tanto para a mensagem de grupo na mensagem de relatório IGMP como para o endereço IP de destino.

![Mensagem de relatório IGMP](./media/user-guide/igmp-report-message.png)

**FIGURA 8. Mensagem de relatório IGMP**

Na figura acima (Figura 8), o cabeçalho IGMP contém uma versão/tipo de campo, tempo de resposta máximo, um campo de verificação e um campo de endereços de grupo multicast. Para as mensagens IGMPv1, o campo Tempo de Resposta Máxima está sempre definido para zero, uma vez que este não faz parte do protocolo IGMPv1. O campo Tempo de Resposta Máxima é definido quando o anfitrião recebe uma mensagem IGMP tipo consulta e apurada quando um anfitrião recebe a mensagem do tipo Relatório de outro anfitrião, tal como definido pelo protocolo IGMPv2.

O seguinte descreve o formato do cabeçalho IGMP:

| **Campo de Cabeçalho**          | **Objetivo** |
|-----------------------|--------------------------------------------------------------------|
| Versão               | Este campo especifica a versão IGMP (bits 31-28).                                                                               |
| Tipo                  | Este campo especifica o tipo de mensagem IGMP (bits 27-24).                                                                       |
| Tempo máximo de resposta | Não usado no IGMPv1. No IGMPv2 este campo serve como o tempo máximo de resposta.                                                      |
| Soma de verificação              | Este campo contém a parte de verificação de 16 bits da soma de complemento da mensagem IGMP a começar pela versão IGMP (bits 0-15) |
| Endereço de grupo         | Endereço IP do grupo D de 32 bits |


As mensagens de relatório IGMP também são enviadas em resposta às mensagens de consulta IGMP enviadas por um router multicast. Os routers multicast enviam periodicamente mensagens de consulta para ver quais os anfitriões que ainda precisam de ser membros do grupo. As mensagens de consulta têm o mesmo formato que a mensagem IGMP Report mostrada na Figura 8. As únicas diferenças são que o tipo IGMP é igual a 1 e o campo de endereços de grupo está definido para 0. As mensagens de consulta IGMP são enviadas para o endereço IP *de todos os anfitriões* pelo router multicast. Um anfitrião que ainda deseja manter a adesão ao grupo responde enviando outra mensagem do IGMP Report.

> [!IMPORTANT]
> *Espera-se que todas as mensagens na implementação TCP/IP estejam em grande formato **endiano.** Neste formato, o byte mais significativo da palavra reside no endereço byte mais baixo.*

### <a name="igmp-statistics-and-errors"></a>Estatísticas e erros do IGMP

Se ativado, o software NetX IGMP regista várias estatísticas e erros que podem ser úteis à aplicação. São mantidas as seguintes estatísticas e relatórios de erro para o processamento de IGMP de cada IP:

- Total de relatórios IGMP enviados
- Total de consultas IGMP recebidas
- Erros totais do IGMP Checksum
- Total de grupos atuais do IGMP aderidos

Todas estas estatísticas e relatórios de erro estão disponíveis para a aplicação com o serviço ***nx_igmp_info_get.***

## <a name="user-datagram-protocol-udp"></a>Protocolo de Datagrama do Utilizador (UDP)

O Protocolo de Datagrama do Utilizador (UDP) fornece a forma mais simples de transferência de dados entre membros da rede (RFC 768). Os pacotes de dados da UDP são enviados de um membro da rede para outro da melhor forma de esforço; ou seja, não existe um mecanismo incorporado para reconhecimento pelo destinatário do pacote. Além disso, o envio de um pacote UDP não requer qualquer ligação a ser estabelecida antecipadamente. Por causa disso, a transmissão de pacotes da UDP é muito eficiente.

### <a name="udp-header"></a>Cabeçalho UDP
A UDP coloca um simples cabeçalho de pacote na frente dos dados da aplicação sobre a transmissão, e remove um cabeçalho UDP semelhante do pacote na receção antes de entregar um pacote UDP recebido à aplicação. O UDP utiliza o protocolo IP para o envio e receção de pacotes, o que significa que há um cabeçalho IP em frente ao cabeçalho da UDP quando o pacote está na rede. A figura 9 mostra o formato do cabeçalho da UDP.

![Cabeçalho UDP](./media/user-guide/udp-header.png)

**FIGURA 9. Cabeçalho UDP**

> [!IMPORTANT]
> *Espera-se que todos os cabeçalhos na implementação UDP/IP estejam em grande formato endiano. Neste formato, o byte mais significativo da palavra reside no endereço byte mais baixo.*

O seguinte descreve o formato do cabeçalho UDP:

| Campo de Cabeçalho                   | Objetivo |
|--------------------------------|---------------------------------------------|
| Número de porta de 16 bits      | Este campo contém a porta de onde o pacote UDP está a ser enviado. As portas UDP válidas variam de 1 a 0xFFFF. |
| Número da porta de destino de 16 bits | Este campo contém a porta UDP para a qual o pacote está a ser enviado. As portas UDP válidas variam de 1 a 0xFFFF.   |
| Comprimento uDP de 16 bits   | Este campo contém o número de bytes no pacote UDP, incluindo o tamanho do cabeçalho UDP.                                  |
| 16 bits UDP checksum | Este campo contém a 16-bit checkum para o pacote, incluindo o cabeçalho UDP, a área de dados do pacote, e o cabeçalho pseudo IP. |

### <a name="udp-enable"></a>Ativação uDP

Antes de a transmissão de pacotes da UDP ser possível, a aplicação deve primeiro permitir a UDP, ligando para o serviço ***nx_udp_enable.*** Depois de ativado, a aplicação é gratuita para enviar e receber pacotes UDP.

### <a name="udp-socket-create"></a>Criação de tomada uDP

As tomadas UDP são criadas durante a inicialização ou durante o tempo de funcionamento por fios de aplicação. O tipo inicial de serviço, tempo para viver e receber profundidade de fila são definidos pelo ***serviço nx_udp_socket_create.*** Não existem limites ao número de tomadas UDP numa aplicação.

### <a name="udp-checksum"></a>UDP Checksum

O UDP especifica a parte de verificação de 16 bits de um complemento que cobre o cabeçalho IP pseudo (composto pelo endereço IP de origem, endereço IP de destino e a palavra IP protocol/comprimento), o cabeçalho UDP e os dados do pacote UDP. Se a úmis calculado da UDP for 0, é armazenada como todas (0xFFFF). Se a tomada de envio tiver a lógica de verificação UDP desativada, é colocado um zero no campo de verificação da UDP para indicar que a parte de verificação não foi calculada. Se a sala de verificação UDP não corresponder à parte de verificação calculada pelo recetor, o pacote UDP é simplesmente descartado.

Na rede IP, a UDP checksum é opcional. O NetX permite que uma aplicação permita ou desative o cálculo do UDP checkum numa base por tomada. Por predefinição, a lógica de verificação da tomada UDP está ativada. A aplicação pode desativar a lógica de checkum para uma determinada tomada UDP, chamando o serviço ***nx_udp_socket_checksum_disable.***

Certos controladores Ethernet são capazes de gerar o checkum uDP em movimento. Se o sistema for capaz de utilizar a funcionalidade de cálculo de checkum de hardware, a biblioteca NetX pode ser construída sem a lógica de checkum. Para desativar a caixa de verificação do software UDP, a biblioteca NetX deve ser construída com os seguintes símbolos definidos: ***NX_DISABLE_UDP_TX_CHECKSUM*** e ***NX_DISABLE_UDP_RX_CHECKSUM**_ (descrito no [capítulo 2](chapter2.md)). As opções de configuração removem totalmente a lógica de verificação do UDP do NetX, enquanto o**** serviço de nx_udp_socket_checksum_disable _ permite que a aplicação desative o processamento de checkum ipdp numa base de tomada.

### <a name="udp-ports-and-binding"></a>Portos da UDP e Encadernação

Uma porta UDP é um ponto final lógico no protocolo UDP. Existem 65.535 portas válidas na componente UDP da NetX, que variam de 1 a 0xFFFF. Para enviar ou receber dados da UDP, a aplicação deve primeiro criar uma tomada UDP e, em seguida, ligá-la a uma porta desejada. Depois de ligar uma tomada UDP a uma porta, o pedido pode enviar e receber dados sobre essa tomada.

### <a name="udp-fast-pathtrade"></a>Caminho Rápido da UDP&trade;

O Caminho Rápido da UDP &trade; é o nome para um caminho de sobrecarga de baixo pacote através da implementação do NetX UDP. O envio de um pacote UDP requer apenas algumas chamadas de função: ***nx_udp_socket_send** _, _*_nx_ip_packet_send_*_, e a eventual chamada para o controlador de rede. _*_nx_udp_socket_send_*_ está disponível no NetX para aplicações NetX existentes e só é aplicável para pacotes IP. O método preferido, no entanto, é usar o serviço _ *_nx_udp_socket_send_** discutido abaixo. Na receção do pacote UDP, o pacote UDP é colocado na tomada UDP adequada receber fila ou entregue a um fio de aplicação suspenso numa única chamada de função do processamento de interrupção de receção do condutor da rede. Esta lógica altamente otimizada para o envio e receção de pacotes UDP é a essência da tecnologia UDP Fast Path.

### <a name="udp-packet-send"></a>Envio de pacote de UDP

O envio de dados UDP através de redes IP é facilmente realizado através da função ***nx_udp_socket_send** _ . O chamador deve definir a versão IP no campo _IP endereço*. O NetX determinará o melhor endereço de origem para pacotes de UDP transmitidos com base no endereço IP de destino. Este serviço coloca um cabeçalho UDP na frente dos dados do pacote e envia-o para a rede usando uma rotina interna de envio de IP. Não existe suspensão de fio no envio de pacotes UDP porque todas as transmissões de pacotes UDP são processadas imediatamente.

Para destinos multicast ou de difusão, a aplicação deve especificar o endereço IP de origem para utilizar se o dispositivo NetX tiver vários endereços IP para escolher. Isto pode ser feito com os serviços ***nx_udp_socket_interface_send.***

> [!IMPORTANT]
> *Se **nx_udp_socket_send** for utilizado para transmitir pacotes multicast ou de transmissão, o endereço IP da primeira interface é utilizado como endereço de origem.*

> [!IMPORTANT]
> *Se a lógica de verificação da UDP estiver ativada para esta tomada, a operação de checkum é realizada no contexto do fio de chamada, sem bloquear o acesso às estruturas de dados UDP ou IP.*

> [!NOTE]
> *Os dados de carga útil da UDP que residem na estrutura **NX_PACKET** devem residir num limite de palavras longas. A aplicação precisa de deixar espaço suficiente entre o ponteiro pré-reto e o ponteiro de início de dados para o NetX colocar os cabeçalhos UDP, IP e meios de comunicação físicos.*

### <a name="udp-packet-receive"></a>Receber pacote da UDP

Os fios de aplicação podem receber pacotes UDP de uma determinada tomada chamando ***nx_udp_socket_receive***. A função de receção da tomada fornece o pacote mais antigo da fila de receção da tomada. Se não houver pacotes na fila de receção, o fio de chamada pode suspender (com um intervalo opcional) até chegar um pacote.

O processamento de pacotes UDP (normalmente chamado do controlador de interrupção de receção do controlador de receção do condutor da rede) é responsável por colocar o pacote na fila de receção da tomada UDP ou entregá-lo ao primeiro fio suspenso à espera de um pacote. Se o pacote estiver em fila, o processamento de receção também verifica a profundidade máxima de receção associada à tomada. Se este pacote recém-em fila exceder a profundidade da fila, o pacote mais antigo da fila é descartado.

### <a name="udp-receive-notify"></a>Notificação de receção da UDP

Se o fio de aplicação precisar de processar dados recebidos de mais de uma tomada, deve ser utilizada a função ***nx_udp_socket_receive_notify.*** Esta função regista uma função de chamada de pacote de receção para a tomada. Sempre que um pacote é recebido na tomada, a função de retorno é executada.

O conteúdo da função de retorno é específico da aplicação. No entanto, provavelmente conteria lógica para informar o fio de processamento de que um pacote está agora disponível na tomada correspondente.

### <a name="peer-address-and-port"></a>Endereço de pares e porto

Ao receber um pacote UDP, a aplicação pode encontrar o endereço IP e o número de porta do remetente utilizando o ***serviço nx_udp_packet_info_extract***. Na devolução bem sucedida, este serviço fornece informações sobre o endereço IP do remetente, o número de porta do remetente e a interface local através da qual o pacote foi recebido.

### <a name="thread-suspension"></a>Suspensão do fio

Como mencionado anteriormente, os fios de aplicação podem suspender enquanto tentam receber um pacote UDP em uma determinada porta UDP. Depois de recebido um pacote naquela porta, é dado ao primeiro fio suspenso e esse fio é retomado. Um tempo limite opcional está disponível ao suspender um pacote de receção UDP, uma funcionalidade disponível para a maioria dos serviços NetX.

### <a name="udp-socket-statistics-and-errors"></a>Estatísticas e erros da tomada de UDP

Se ativado, o software de tomadas UDP NetX mantém o registo de várias estatísticas e erros que podem ser úteis à aplicação. As seguintes estatísticas e relatórios de erro são mantidos para cada instância IP/UDP:

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

Todas estas estatísticas e relatórios de erro estão disponíveis para a aplicação com o serviço ***nx_udp_info_get*** para estatísticas de UDP acumulados em todas as tomadas UDP, e o serviço ***de nx_udp_socket_info_get*** para estatísticas de UDP na tomada de UDP especificada.

### <a name="udp-socket-control-block-nx_udp_socket"></a>NX_UDP_SOCKET do bloco de controlo da tomada UDP

As características de cada tomada UDP encontram-se no bloco de controlo **NX_UDP_SOCKET** associado. Contém informações úteis, tais como a ligação à estrutura de dados IP, a interface de rede para os caminhos de envio e receção, a porta vinculada e a fila de pacotes de receção. Esta estrutura é definida no ficheiro **_nx_api.h._**

## <a name="transmission-control-protocol-tcp"></a>Protocolo de Controlo de Transmissão (TCP)

O Protocolo de Controlo de Transmissão (TCP) fornece transferência fiável de dados de fluxo entre dois membros da rede (RFC 793). Todos os dados enviados de um membro da rede são verificados e reconhecidos pelo membro recetor. Além disso, os dois membros devem ter estabelecido uma ligação antes de qualquer transferência de dados. Tudo isto resulta numa transferência de dados fiável; no entanto, requer substancialmente mais despesas do que a transferência de dados da UDP anteriormente descrita.

### <a name="tcp-header"></a>Cabeçalho TCP

Na transmissão, o cabeçalho TCP é colocado na frente dos dados do utilizador. Na receção, o cabeçalho TCP é removido do pacote de entrada, deixando apenas os dados do utilizador disponíveis para a aplicação. A TCP utiliza o protocolo IP para enviar e receber pacotes, o que significa que há um cabeçalho IP em frente ao cabeçalho TCP quando o pacote está na rede. A figura 10 mostra o formato do cabeçalho TCP.

![Cabeçalho TCP](./media/user-guide/tcp-header.png)

**FIGURA 10. Cabeçalho TCP**

O seguinte descreve o formato do cabeçalho TCP:

| Campo de Cabeçalho | Objetivo |
|---|---|
| Número de porta de 16 bits | Este campo contém a porta onde o pacote TCP está a ser enviado. As portas TCP válidas variam de 1 a 0xFFFF. |
| Número da porta de destino de 16 bits | Este campo contém a porta TCP para onde o pacote está a ser enviado. As portas TCP válidas variam de 1 a 0xFFFF. |
| Número de sequência de 32 bits | Este campo contém o número de sequência para os dados enviados a partir desta extremidade da ligação. A sequência original é estabelecida durante a sequência de ligação inicial entre dois nós TCP. Cada transferência de dados a partir desse ponto resulta num incremento do número de sequência pelo número de bytes enviados. |
| Número de reconhecimento de 32 bits | Este campo contém o número de sequência correspondente ao último byte recebido por este lado da ligação. Isto é usado para determinar se os dados anteriormente enviados foram recebidos com sucesso pela outra extremidade da ligação. |
| Comprimento do cabeçalho de 4 bits           | Este campo contém o número de palavras de 32 bits no cabeçalho TCP. Se não houver opções no cabeçalho TCP, este campo é 5. |
| Bits de código de 6 bits               | Este campo contém os seis bits de código diferentes utilizados para indicar várias informações de controlo associadas à ligação. As bits de controlo são definidas da seguinte forma: |



| Name | Pouco | Significado                                                     |
|------|-----|-------------------------------------------------------------|
| URG  | 21  | Dados urgentes presentes                                         |
| Rio ACK  | 20  | O número de agradecimento é válido                             |
| PSH  | 19  | Trate estes dados imediatamente                                |
| RST  | 18  | Repor a ligação                                        |
| SIN  | 17  | Sincronizar os números de sequência (usado para estabelecer a ligação) |
| FIN  | 16  | O remetente é terminado com o transmissor (usado para fechar a ligação) |

**Janela de 16 bits**

Este campo é utilizado para o controlo de fluxos. Contém a quantidade de bytes que a tomada pode receber atualmente. Isto é basicamente usado para o controlo de fluxo. O remetente é responsável por se certificar de que os dados a enviar se encaixam na janela anunciada do recetor.

| **Campo de Cabeçalho**          | **Objetivo** |
| ------------------------- | --- |
| **Cheque TCP de 16 bits**   | Este campo contém a 16-bit checkum para o pacote, incluindo o cabeçalho TCP, a área de dados do pacote e o cabeçalho pseudo IP.                |
| **Ponteiro urgente de 16 bits** | Este campo contém a compensação positiva do último byte dos dados urgentes. Este campo só é válido se a broca de código urg estiver definida no cabeçalho. |

> [!IMPORTANT]
> *Espera-se que todos os cabeçalhos na implementação TCP/IP estejam em grande formato endiano. Neste formato, o byte mais significativo da palavra reside no endereço byte mais baixo.*

### <a name="tcp-enable"></a>Ativar TCP

Antes de as ligações TCP e as transmissões de pacotes serem possíveis, a aplicação deve primeiro permitir a TCP, ligando para o serviço nx_tcp_enable. Depois de ativado, a aplicação é gratuita para aceder a todos os serviços TCP.

### <a name="tcp-socket-create"></a>Criação de tomada TCP

As tomadas TCP são criadas durante a inicialização ou durante o tempo de funcionamento por fios de aplicação. O tipo inicial de serviço, tempo para viver e tamanho da janela são definidos pelo ***serviço nx_tcp_socket_create.*** Não existem limites ao número de tomadas TCP numa aplicação.

### <a name="tcp-checksum"></a>TCP Checksum

A TCP especifica a parte de verificação de 16 bits de um complemento que cobre o cabeçalho IP pseudo (composto pelo endereço IP de origem, endereço IP de destino e a palavra IP protocol/comprimento), o cabeçalho TCP e os dados do pacote TCP.

Certos controladores de rede são capazes de realizar cálculo e validação de verificação de TCP em hardware. Para estes sistemas, as aplicações podem pretender utilizar a lógica de hardware checksum tanto quanto possível para reduzir a sobrecarga de tempo de funcionamento. As aplicações podem desativar a lógica de cálculo de checkum da TCP da biblioteca NetX completamente no tempo de construção, definindo **NX_DISABLE_TCP_TX_CHECKSUM** e **NX_DISABLE_TCP_RX_CHECKSUM**. Desta forma, o código de verificação TCP não é compilado.

### <a name="tcp-port"></a>Porta TCP

Uma porta TCP é um ponto de ligação lógico no protocolo TCP. Existem 65.535 portas válidas na componente TCP da NetX, que variam de 1 a 0xFFFF. Ao contrário da UDP em que os dados de uma porta podem ser enviados para qualquer outra porta de destino, uma porta TCP está ligada a outra porta TCP específica, e só quando esta ligação é estabelecida pode ocorrer qualquer transferência de dados — e apenas entre as duas portas que compõem a ligação.

> [!IMPORTANT]
> *As portas TCP são completamente separadas das portas UDP; por exemplo, a porta udp número 1 não tem qualquer relação com a porta TCP número 1.*

## <a name="client-server-model"></a>Modelo Client-Server

Para utilizar o TCP para transferência de dados, deve primeiro ser estabelecida uma ligação entre as duas tomadas TCP. O estabelecimento da ligação é feito de forma cliente-servidor. O lado cliente da ligação é o lado que inicia a ligação, enquanto o lado do servidor simplesmente aguarda os pedidos de ligação do cliente antes de qualquer processamento ser feito.

> [!IMPORTANT]
> *Para dispositivos multihomes, o NetX determina automaticamente o endereço de origem a utilizar para a ligação e o próximo endereço de lúpulo baseado no endereço IP de destino da ligação.*

### <a name="tcp-socket-state-machine"></a>Máquina de estado de tomada TCP

A ligação entre duas tomadas TCP (um cliente e um servidor) é complexa e é gerida de forma estatal. Cada tomada TCP começa em estado fechado. Através de eventos de ligação, a máquina estatal de cada tomada migra para o estado ESTABELECIDO, que é onde ocorre a maior parte da transferência de dados em TCP. Quando um dos lados da ligação já não deseja enviar dados, desliga-se. Depois de o outro lado desligar, eventualmente a tomada TCP volta ao estado fechado. Este processo repete-se sempre que um cliente e servidor TCP estabelecem e fecham uma ligação. A figura 11 mostra os vários estados da máquina estatal TCP.

![Estados da Máquina Estatal TCP](./media/user-guide/states-tcp-state-machine.png)

### <a name="figure-11-states-of-the-tcp-state-machine"></a>FIGURA 11. Estados da Máquina Estatal TCP

### <a name="tcp-client-connection"></a>Conexão ao cliente TCP

Como mencionado anteriormente, o lado cliente da ligação TCP inicia um pedido de ligação a um servidor TCP. Antes de um pedido de ligação ser feito, o TCP deve ser ativado na instância IP do cliente. Além disso, a tomada TCP do cliente deve ser criada em seguida com o serviço ***nx_tcp_socket_create** _ e vinculada a uma porta através do serviço _*_nx_tcp_client_socket_bind._*_ Depois de a tomada do cliente estar ligada, o serviço _ *_nx_tcp_client_socket_connect_** é utilizado para estabelecer uma ligação com um servidor TCP. Note que a tomada deve estar num estado fechado para iniciar uma tentativa de ligação. O estabelecimento da ligação começa com a emissão de um pacote SYN E, em seguida, à espera de um pacote SYN ACK de volta do servidor, o que significa a aceitação do pedido de ligação. Após a receção do SYN ACK, a NetX responde com um pacote ACK e promove a tomada do cliente para o estado estabelecido.

### <a name="tcp-client-disconnection"></a>Desconexão do cliente TCP

O fecho da ligação é realizado chamando ***nx_tcp_socket_disconnect***. Se não for especificada qualquer suspensão, a tomada do cliente envia um pacote RST para a tomada do servidor e coloca a tomada no estado FECHADO. Caso contrário, se for solicitada uma suspensão, é executada a completa do protocolo de desconexão TCP, da seguinte forma:

- Se o servidor já tinha iniciado um pedido de desconexão (a tomada do cliente já recebeu um pacote FIN, respondeu com um ACK, e está no estado CLOSE WAIT), a NetX promove o estado de tomada TCP do cliente para o estado de ÚLTIMA ACK e envia um pacote FIN. Em seguida, aguarda um ACK do servidor antes de completar a desconexão e entrar no estado FECHADO.

- Se, por outro lado, o cliente for o primeiro a iniciar um pedido de desconexão (o servidor não foi desligado e a tomada ainda se encontra no estado ESTABELECIDO), o NetX envia um pacote FIN para iniciar a desconexão e espera receber uma FIN e um ACK do servidor antes de completar a desconexão e colocar a tomada num estado FECHADO.

Se ainda existirem pacotes na fila de transmissão da tomada, o NetX suspende o tempo limite especificado para permitir o reconhecimento dos pacotes. Se o tempo limite expirar, o NetX esvazia a fila de transmissão da tomada do cliente.

Para desvindia a porta da tomada do cliente, a aplicação chama ***nx_tcp_client_socket_unbind***. A tomada deve estar num estado fechado ou em processo de desconexão (isto é, estado de espera TIMED) antes de a porta ser libertada; caso contrário, um erro é devolvido.

Finalmente, se a aplicação já não necessitar da tomada do cliente, chama ***nx_tcp_socket_delete*** para apagar a tomada.

### <a name="tcp-server-connection"></a>Conexão do servidor TCP

O lado do servidor de uma ligação TCP é passivo; ou seja, o servidor aguarda que um cliente inicie o pedido de ligação. Para aceitar uma ligação ao cliente, a TCP deve primeiro ser ativada na instância IP, ligando para o serviço ***nx_tcp_enable** _. Em seguida, a aplicação deve criar uma tomada TCP utilizando o serviço _ *_nx_tcp_socket_create_** .

A tomada do servidor também deve ser configurada para ouvir pedidos de ligação. Isto é conseguido utilizando o serviço ***nx_tcp_server_socket_listen.*** Este serviço coloca a tomada do servidor no estado LISTEN e liga a porta do servidor especificada à tomada.

> [!IMPORTANT]
> *Para definir uma rotina de chamada de chamada de tomada, a aplicação especifica a função de retorno adequada para o argumento tcp_listen_callback do serviço **nx_tcp_server_socket_listen.** Esta função de chamada de aplicação é então executada pelo NetX sempre que uma nova ligação é solicitada nesta porta do servidor. O processamento na chamada está sob controlo de aplicação.*

Para aceitar pedidos de ligação ao cliente, a aplicação liga para o serviço ***nx_tcp_server_socket_accept** _ . A tomada do servidor deve estar num estado DE ESCUTA ou num estado SYN RECEIVED (ou seja, o servidor está no estado LISTEN e recebeu um pacote SYN de um cliente que solicita uma ligação) para ligar para o serviço de aceitação. Um estado de retorno bem sucedido de _ *_nx_tcp_server_socket_accept_** indica que a ligação foi configurada e a tomada do servidor está no estado ESTABELECIDO.

Depois de a tomada do servidor ter uma ligação válida, os pedidos adicionais de ligação ao cliente são colocados na fila até à profundidade especificada pelo *listen_queue_size,* transmitidos para o serviço ***nx_tcp_server_socket_listen** _ . Para processar as ligações subsequentes numa porta do servidor, a aplicação deve ligar para _ *_nx_tcp_server_socket_relisten_** com uma tomada disponível (ou seja, uma tomada em estado fechado). Note que a mesma tomada do servidor pode ser utilizada se a ligação anterior associada à tomada estiver concluída e a tomada estiver no estado fechado.

### <a name="tcp-server-disconnection"></a>Desconexão do servidor TCP

O fecho da ligação é realizado chamando ***nx_tcp_socket_disconnect***. Se não for especificada qualquer suspensão, a tomada do servidor envia um pacote RST para a tomada do cliente e coloca a tomada no estado FECHADO. Caso contrário, se for solicitada uma suspensão, é executada a completa do protocolo de desconexão TCP: |

- Se o cliente já tinha iniciado um pedido de desconexão (a tomada do servidor já recebeu um pacote FIN, respondeu com um ACK, e está no estado CLOSE WAIT), a NetX promove o estado de tomada TCP para o estado de última ACK e envia um pacote FIN. Em seguida, aguarda um ACK do cliente antes de completar a desconexão e entrar no estado FECHADO.

- Se, por outro lado, o servidor for o primeiro a iniciar um pedido de desconexão (o cliente não se desligou e a tomada ainda se encontra no estado ESTABELECIDO), a NetX envia um pacote FIN para iniciar a desconexão e espera receber uma FIN e um ACK do cliente antes de completar a desconexão e colocar a tomada num estado FECHADO.

Se ainda existirem pacotes na fila de transmissão da tomada, o NetX suspende o tempo limite especificado para permitir que esses pacotes sejam reconhecidos. Se o tempo limite expirar, o NetX descarrega a fila de transmissão da tomada do servidor.

Após o processamento da desconexão estar concluído e a tomada do servidor estiver no estado FECHADO, a aplicação deve chamar o serviço ***nx_tcp_server_socket_unaccept*** para terminar a associação desta tomada com a porta do servidor. Note que este serviço deve ser chamado pela aplicação mesmo ***que nx_tcp_socket_disconnect*** ou ***nx_tcp_server_socket_accept** _ devolva um estado de erro. Após a devolução do _ *_nx_tcp_server_socket_unaccept*_* a tomada pode ser utilizada como tomada de cliente ou servidor, ou mesmo eliminada se já não for necessária. Se aceitar outra ligação ao cliente na mesma porta do servidor, o serviço ***nx_tcp_server_socket_relisten*** deve ser chamado nesta tomada.

O seguinte segmento de código ilustra a sequência de chamadas que um servidor típico de TCP utiliza:

```c
/* Set up a previously created TCP socket to listen on port 12 */

nx_tcp_server_socket_listen()

/* Loop to make a (another) connection. */
while(1) {

    /* Wait for a client socket connection request for 100 ticks. */
    nx_tcp_server_socket_accept();

    /* (Send and receive TCP messages with the TCP client) */

    /* Disconnect the server socket. */
    nx_tcp_socket_disconnect();

    /* Remove this server socket from listening on the port. */

    nx_tcp_server_socket_unaccept(&server_socket);

    /* Set up server socket to relisten on the same port for the next
    client. */
    nx_tcp_server_socket_relisten();
}
```

### <a name="mss-validation"></a>Validação mss

O Tamanho Máximo do Segmento (MSS) é a quantidade máxima de bytes que um hospedeiro TCP pode receber sem ser fragmentado pela camada IP subjacente. Durante a fase de estabelecimento de ligação TCP, ambas as extremidades trocam o seu próprio valor de MSS TCP, de modo que o remetente não envie um segmento de dados TCP maior do que o MSS do recetor. O módulo NetX TCP validará opcionalmente o valor mss anunciado do seu par antes de estabelecer uma ligação. Por predefinição, o NetX não permite tal verificação. As candidaturas que desejem realizar a validação do MSS devem definir ***NX_ENABLE_TCP_MSS_CHECKING** _ na construção da biblioteca NetX, e o valor mínimo será definido em _*_NX_TCP_MSS_MINIMUM_*_. As ligações TCP recebidas com valores DESS abaixo _ *_NX_TCP_MSS_MINIMUM_** são largadas.

### <a name="stop-listening-on-a-server-port"></a>Pare de ouvir numa porta do servidor

Se a aplicação já não pretender ouvir os pedidos de ligação ao cliente numa porta de servidor que foi previamente especificada por uma chamada para o serviço ***nx_tcp_server_socket_listen** _ , a aplicação simplesmente liga para o serviço _ *_nx_tcp_server_socket_unlisten_** . Este serviço coloca qualquer tomada à espera de uma ligação no estado FECHADO e liberta quaisquer pacotes de pedido de ligação ao cliente em fila.

### <a name="tcp-window-size"></a>Tamanho da janela TCP

Durante as fases de configuração e transferência de dados da ligação, cada porta reporta a quantidade de dados que pode manusear, que é chamado de tamanho da janela. À medida que os dados são recebidos e processados, este tamanho da janela é ajustado dinamicamente. Em TCP, um remetente só pode enviar uma quantidade de dados que se encaixem na janela do recetor. Na essência, o tamanho da janela fornece controlo de fluxo para transferência de dados em cada direção da ligação.

### <a name="tcp-packet-send"></a>Envio de pacote TCP

O envio de dados TCP é facilmente realizado através da chamada ***de nx_tcp_socket_send*** função. Se o tamanho dos dados transmitidos for maior do que o valor MSS da tomada ou o atual par receber o tamanho da janela, o que for menor, a lógica interna da TCP esculpe os dados que se encaixam em min (MSS, peer receive Window) para transmissão. Este serviço constrói então um cabeçalho TCP em frente ao pacote (incluindo o cálculo da caixa de verificação). Se o tamanho da janela do recetor não for zero, o chamador enviará o máximo de dados possível para preencher o tamanho da janela do recetor. Se a janela de receção se tornar zero, o chamador pode suspender e esperar que o tamanho da janela do recetor aumente o suficiente para que este pacote seja enviado. A qualquer momento, vários fios podem suspender-se enquanto tentam enviar dados através da mesma tomada.

> [!IMPORTANT]
> *Os dados da TCP que residem na estrutura NX_PACKET devem residir num limite de palavras longas. Além disso, deve haver espaço suficiente entre o ponteiro pré-remend e o ponteiro de início de dados para colocar os cabeçalhos TCP, IP e meios de comunicação físicos.*

### <a name="tcp-packet-retransmit"></a>Retransmissão de pacotes TCP

Pacotes TCP previamente transmitidos enviados realmente armazenados internamente até que um ACK seja devolvido do outro lado da ligação. Se os dados transmitidos não forem reconhecidos dentro do período de tempo limite, o pacote armazenado é reencaminhado e o período de tempo seguinte é definido. Quando um ACK é recebido, todos os pacotes cobertos pelo número de reconhecimento na fila de transmissão interna são finalmente libertados.

> [!IMPORTANT]
> *A aplicação não reutilizar o pacote nem alterar o conteúdo do pacote após o ***nx_tcp_socket_send** _ função retorna com NX_SUCCESS. O pacote transmitido é eventualmente libertado pelo processamento interno da NetX após os dados ser reconhecidos pelo outro end._

### <a name="tcp-keepalive"></a>TCP Keepalive

A função TCP Keepalive permite que uma tomada detete se o seu par desliga ou não sem uma terminação adequada (por exemplo, o par se despenhou), ou para impedir que certas instalações de monitorização da rede cessem uma ligação por longos períodos de inatividade. A TCP Keepalive funciona enviando periodicamente uma moldura TCP sem dados, e o número de sequência definido para um a menos do que o número atual da sequência. Ao receber tal moldura de resalamento TCP, o destinatário, se ainda estiver vivo, responde com um ACK para o seu número de sequência atual. Isto completa a transação de manter.

Por predefinição, a função keepalive não está ativada. Para utilizar esta função, a biblioteca NetX deve ser construída com ***NX_ENABLE_TCP_KEEPALIVE** _ definido. O símbolo _ *_NX_TCP_KEEPALIVE_INITIAL_** especifica o número de segundos de inatividade antes do início da estrutura de manter.

### <a name="tcp-packet-receive"></a>Receber pacote TCP

O processamento de pacotes de receção de TCP (chamado a partir do fio do ajudante IP) é responsável pelo manuseamento de várias ações de ligação e desconexão, bem como pelo processamento de reconhecimento de transmissão. Além disso, o processamento de pacotes de receção de TCP é responsável pela colocação de pacotes com dados de receção da fila de receção da tomada TCP adequada ou entregando o pacote ao primeiro fio suspenso à espera de um pacote.

### <a name="tcp-receive-notify"></a>Notificação de receção de TCP

Se o fio de aplicação precisar de processar dados recebidos de mais de uma tomada, deve ser utilizada a função ***nx_tcp_socket_receive_notify.*** Esta função regista uma função de chamada de pacote de receção para a tomada. Sempre que um pacote é recebido na tomada, a função de retorno é executada.

O conteúdo da função de retorno é específico da aplicação; no entanto, a função provavelmente conteria lógica para informar o fio de processamento de que um pacote está disponível na tomada correspondente.

### <a name="thread-suspension"></a>Suspensão do fio

Como mencionado anteriormente, os fios de aplicação podem suspender enquanto tentam receber dados de uma determinada porta TCP. Depois de recebido um pacote naquela porta, é dado ao primeiro fio suspenso e esse fio é retomado. Um tempo limite opcional está disponível ao suspender um pacote de receção TCP, uma funcionalidade disponível para a maioria dos serviços NetX.

A suspensão thread também está disponível para serviços de ligação (cliente e servidor), ligação ao cliente e serviços de desconexão.

### <a name="tcp-socket-statistics-and-errors"></a>Estatísticas e erros da tomada TCP

Se ativado, o software de tomada NetX TCP regista várias estatísticas e erros que podem ser úteis à aplicação. São mantidas as seguintes estatísticas e relatórios de erro para cada instância IP/TCP:

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

## <a name="tcp-socket-control-block-nx_tcp_socket"></a>NX_TCP_SOCKET do bloco de controlo da tomada TCP

As características de cada tomada TCP encontram-se no bloco de controlo *NX_TCP_SOCKET* associado, que contém informações úteis, tais como a ligação à estrutura de dados IP, a interface de ligação à rede, a porta vinculada e a fila do pacote de receção. Esta estrutura é definida no ficheiro ***nx_api.h.***
