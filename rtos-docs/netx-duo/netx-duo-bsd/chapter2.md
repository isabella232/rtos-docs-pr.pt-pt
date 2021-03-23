---
title: Capítulo 2 - Instalação e utilização do Azure RTOS NetX Duo BSD
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente BSD Azure RTOS NetX Duo BSD.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 582661bc66c51341fc098de9ff7b6fa2a7d746de
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826155"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-bsd"></a>Capítulo 2 - Instalação e utilização do Azure RTOS NetX Duo BSD

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente BSD Azure RTOS NetX Duo BSD.

## <a name="product-distribution"></a>Distribuição de Produtos

O Azure RTOS NetX Duo BSD pode ser obtido a partir do nosso repositório de código fonte pública em [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) . O pacote inclui dois ficheiros de origem e um ficheiro PDF que contém este documento, da seguinte forma:

- **nxd_bsd.h:** Arquivo de cabeçalho para NetX Duo BSD
- **nxd_bsd.c**: Ficheiro C Fonte para NetX Duo BSD
- **nxd_bsd.pdf**: Guia do Utilizador para o Duo BSD da NetX

Ficheiros de demonstração:

- **bsd_demo_udp.c**
- **bsd_demo_tcp.c**
- **bsd_demo_raw.c**

## <a name="netx-duo-bsd-installation"></a>Instalação BSD netx duo

Para utilizar o NetX Duo BSD, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX Duo está instalado. Por exemplo, se o NetX Duo for instalado no diretório "*\threadx\arm7\green*" então os ficheiros *nxd_bsd.h* e *nxd_bsd.c* devem ser copiados para este diretório.

## <a name="building-the-threadx-and-netx-duo-components-of-a-bsd-application"></a>Construção dos componentes ThreadX e NetX Duo de uma aplicação BSD

### <a name="threadx"></a>ThreadX

A biblioteca ThreadX deve definir `bsd_errno` no armazenamento local do fio. Recomendamos o seguinte procedimento:

1. Em *tx_port.h,* definir uma das macros TX_THREAD_EXTENSION da seguinte forma:
   - `#define TX_THREAD_EXTENSION_3     int bsd_errno`

1. Reconstruir a biblioteca ThreadX.

> [!NOTE]
> Se TX_THREAD_EXTENSION_3 já estiver utilizado, o utilizador é livre de utilizar uma das outras macros TX_THREAD_EXTENSION.

### <a name="netx-duo"></a>NetX Duo

Antes de utilizar os Serviços BSD NetX Duo, a biblioteca NetX Duo deve ser construída com NX_ENABLE_EXTENDED_NOTIFY_SUPPORT definida. Por defeito não está definido. Se as tomadas em bruto BSD forem utilizadas, a biblioteca NetX Duo deve ser construída com NX_ENABLE_IP_RAW_PACKET_FILTER definidas.

## <a name="using-netx-duo-bsd"></a>Usando o Duo BSD netx

Um projeto de aplicação NetX Duo BSD deve incluir *nxd_bsd.h* depois de incluir *tx_api.h* e *nx_api.h* para poder utilizar os serviços BSD especificados mais tarde neste guia. O pedido também deve incluir *nxd_bsd.c* no processo de construção. Este ficheiro deve ser compilado da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação. Isto é tudo o que é necessário para usar NetX Duo BSD.

Para utilizar os serviços BSD NetX Duo, a aplicação deve criar uma instância IP, criar um conjunto de pacotes para a camada BSD para alocar pacotes a partir, alocar espaço de memória para a pilha interna de fios BSD, e especificar a prioridade do fio BSD interno. A camada de BSD é inicializada chamando *bsd_initialize* e passando nos parâmetros. Isto é demonstrado nos "Pequenos Exemplos" mais tarde neste documento, mas o protótipo é mostrado abaixo:

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                    *CHAR *bsd_thread_stack_area,
                    *ULONG bsd_thread_stack_size,
                    *UINT bsd_thread_priority*);
```

O default_ip é a instância IP em que a camada de BSD funciona. O default_pool é utilizado pelos serviços da BSD para alocar pacotes a partir de. Os dois parâmetros seguintes: bsd_thread_stack_area, bsd_thread_stack_size define a área de pilha utilizada pelo fio BSD interno, e o último parâmetro, bsd_thread_priority, define a prioridade do fio.

## <a name="netx-duo-bsd-raw-socket-support"></a>Suporte de tomada bruta netx duo BSD

NetX Duo BSD também suporta tomadas brutas. Para utilizar tomadas brutas no NetX Duo BSD, a biblioteca NetX Duo deve ser compilada com NX_ENABLE_IP_RAW_PACKET_FILTER definida. Por defeito não está definido. A aplicação deve então permitir o processamento de tomadas em bruto para uma instância IP previamente criada, chamando *nx_ip_raw_packet_enable.*

Para criar uma tomada em bruto no NetX Duo BSD, a aplicação utiliza a *tomada* de serviço e especifica a família protocolar, tipo de tomada e protocolo:

```c
sock_1 = socket(INT protocolFamily, INT socket_type, INT protocol)
```

protocoloAmily é AF_INET para tomadas IPv4, ou AF_INET6 para tomadas IPv6, assumindo que o IPv6 está ativado na instância IP. O socket_type tem de ser SOCK_RAW. protocolo é específico de aplicação.

Para enviar e receber pacotes crus, bem como fechar uma tomada em bruto, a aplicação normalmente utiliza os mesmos serviços BSD que para uDP, por *exemplo, sendto, recvfrom, select* e *soc_close*. As tomadas brutas não *suportam* nem aceitam ou *ouvem* os serviços de BSD.

- Por predefinição, os dados brutos do IPv4 recebidos incluem o cabeçalho IPv4.  Inversamente, os dados brutos recebidos do IPv6 não incluem o cabeçalho IPv6.

- Por predefinição, ao enviar pacotes IPv6 ou IPv4 brutos, a camada de invólucro BSD adiciona o cabeçalho IPv6 ou IPv4 antes de enviar os dados.

NetX Duo BSD suporta opções adicionais de tomada bruta, incluindo IP_RAW_RX_NO_HEADER, IP_HDRINCL e IP_RAW_IPV6_HDRINCL.

Se IP_RAW_RX_NO_HEADER estiver definido, o cabeçalho IPv4 é removido de modo a que os dados recebidos não contenham o cabeçalho IPv4, e o comprimento da mensagem relatado não inclua o cabeçalho IPv4.  Para as tomadas IPv6, por predefinição a tomada bruta recebe não inclui cabeçalho IPv6, equivalente a ter o IP_RAW_RX_NO_HEADER conjunto de opções. A aplicação pode utilizar o serviço *setockopt* para limpar a opção IP_RAW_RX_NO_HEADER, uma vez que a opção IP_RAW_RX_NO_HEADER seja apurada, os dados em bruto do IPv6 recebidos incluem o cabeçalho IPv6, e o comprimento da mensagem relatado inclui o cabeçalho IPv6.

Esta opção não tem qualquer efeito sobre os dados transmitidos pelo IPv4 ou IPv6.

Se IP_HDRINCL estiver definido, a aplicação inclui o cabeçalho IPv4 ao enviar dados.  Esta opção não tem qualquer efeito na transmissão IPv6 e não é definida por padrão. Se IP_RAW_IPV6_HDRINCL estiver definido, a aplicação inclui o cabeçalho IPv6 ao enviar dados.  Esta opção não tem qualquer efeito na transmissão IPv4 e não é definida por padrão.

IP_HDRINCL e IP_RAW_IPV6_HDRINCL não têm qualquer efeito na receção IPv4 ou IPv6.

> [!NOTE]
> A especificação da tomada BSD 4.3 especifica que o núcleo deve copiar o pacote cru para cada tomada receber tampão. No entanto, no NetX Duo BSD, se várias tomadas forem criadas partilhando o mesmo protocolo, o comportamento é indefinido.

## <a name="netx-duo-bsd-raw-packet-support"></a>Suporte ao pacote bruto da dupla Netx BSD

Para permitir o suporte de pacotes brutos para PPPoE, o invólucro BSD NetX Duo precisa de ser construído com NX_BSD_RAW_PPPOE_SUPPORT ativado.

O seguinte comando cria uma tomada BSD para manusear pacotes crus PPPoE:

```c
Sockfd = socket(AF_PACKET, SOCK_RAW, protocol);
```

A atual implementação do BSD só suporta dois tipos de protocolos em AF_PACKET família

- `ETHERTYPE_PPPOE_DISC`: Pacotes PPPoE Discovery. No quadro de dados mac, os pacotes Discovery têm o tipo de quadro Ethernet 0x8863.

- `ETHERTYPE_PPPOE_SESS`: Pacotes de Sessão de PPP. No quadro de dados mac, os pacotes session têm o tipo de quadro Ethernet 0x8864.

A estrutura `sockaddr_ll` é utilizada para especificar parâmetros ao enviar ou receber quadros PPPoE.

`struct sockaddr_ll` é declarado como:

```c
struct sockaddr_ll
{
    USHORT  sll_family;     /* Must be AF_PACKET */
    USHORT  sll_protocol;   /* LL frame type */
    INT     sll_ifindex;    /* Interface Index. */
    USHORT  sll_hatype;     /* Header type */
    UCHAR   sll_pkttype;    /* Packet type */
    UCHAR   sll_halen;      /* Length of address */
    UCHAR   sll_addr[8];    /* Physical layer address */
};
```

> [!NOTE]
> Nem todos os campos da estrutura são utilizados por `sendto()` ou `recvfrom()` . Veja a descrição abaixo sobre como configurar os `sockaddr_ll` pacotes PPPoE para envio e receção.

A tomada criada no AF_PACKET família pode ser usada para enviar pacotes ppPoE Discovery ou pacotes de sessão de PPP, independentemente do protocolo especificado. Ao transmitir um pacote PPPoE, a aplicação deve preparar o tampão que inclui a moldura PPPoE devidamente formatada, incluindo os cabeçalhos MAC (endereço MAC de destino, endereço MAC de origem e tipo de quadro.) O tamanho do tampão inclui o cabeçalho Ethernet de 14 bytes.

A `sockaddr_ll` estrutura, a `sll_ifindex` é usada para indicar a interface física a ser usada para o envio deste pacote. O resto dos campos da estrutura não são usados. Os valores definidos para os campos não reutilizados são ignorados pelo processo interno da BSD.

O seguinte bloco de código ilustra como transmitir um pacote PPPoE:

```c
struct sockaddr_ll peer_addr;

/* Transmit a PPPoE frame using the primary network interface. */
peer_addr.sll_ifindex = 0;
n = sendto(sockfd, frame, frame_size, 0, (struct
        sockaddr*)&peer_addr, sizeof(peer_addr));
```

O valor de devolução indica o número de bytes transmitidos. Uma vez que os pacotes PPPoE são baseados em mensagens, numa transmissão bem sucedida, o número de bytes enviados corresponde ao tamanho do pacote, incluindo o cabeçalho Ethernet de 14 bytes.

Os pacotes PPPoE podem ser recebidos utilizando `recvfrom()` . O tampão de receção deve ser grande o suficiente para acomodar a mensagem do tamanho Ethernet MTU. O pacote PPPoE recebido inclui cabeçalho Ethernet de 14 byte. Ao receber pacotes PPPoE, os pacotes PPPoE Discovery só podem ser recebidos por tomada criada com protocolo `ETHERTYPE_PPPOE_DISC` . Da mesma forma, os pacotes de sessão de PPP só podem ser recebidos por tomada criada com protocolo `ETHERTYPE_PPPOE_SESS` . Se forem criadas várias tomadas para o mesmo tipo de protocolo, os pacotes PPPoE que chegam são encaminhados para a tomada criada primeiro. Se a primeira tomada criada para o protocolo estiver fechada, a próxima tomada na ordem de criação é utilizada para receber estes pacotes.

Após a ausição de um pacote PPPoE, os seguintes campos na `sockaddr_ll` estrutura são válidos:
- **sll_family**: Definido pelo BSD interno para ser AF_PACKET
- **sll_ifindex**: Indica a interface a partir da qual o pacote é recebido
- **sll_protocol**: Definir para o tipo de pacote recebido: `ETHERTYPE_PPPOE_DISC` ou `ETHERTYPE_PPPOE_SESS`

## <a name="eliminating-internal-bsd-thread"></a>Eliminação do fio interno da BSD

Por predefinição, a BSD utiliza um fio interno para executar parte do seu processamento. Em sistemas com restrições de memória apertadas, o BSD pode ser construído com NX_BSD_TIMEOUT_PROCESS_IN_TIMER definido, que elimina o fio BSD interno e, em vez disso, utiliza um temporizador interno para realizar o mesmo processamento. Isto elimina a memória necessária para o bloco interno de controlo de rosca BSD e para a pilha. No entanto, o processamento global do temporizador é significativamente aumentado e o processamento de BSD também pode executar com uma prioridade mais elevada do que o necessário.

Para configurar as tomadas BSD para funcionar no contexto do temporizador ThreadX, defina NX_BSD_TIMEOUT_PROCESS_IN_TIMER em *nxd_bsd.h*. Se a camada de BSD estiver configurada para executar as tarefas de BSD no contexto do temporizador, na chamada para *bsd_initialize*, os três parâmetros seguintes são ignorados e devem ser definidos como NU:

- **bsd_thread_stack_area**
- **bsd_thread_stack_size**
- **bsd_thread_priority**

## <a name="netx-duo-bsd-with-dns-support"></a>NetX Duo BSD com suporte dns

Se NX_BSD_ENABLE_DNS estiver definido, o NetX Duo BSD pode enviar consultas DNS para obter o nome de anfitrião ou informações IP do anfitrião. Esta funcionalidade requer que um Cliente DSNS NetX seja previamente criado utilizando o serviço *nx_dns_create.* Um ou mais endereços IP do servidor DNS devem ser registados na instância DNS utilizando o serviço *de nx_dns_server_add* para adicionar endereços de servidor IPv4, ou utilizando o serviço *de nxd_dns_server_add* para adicionar endereços de servidor IPv4 ou IPv6.

Os serviços DNS e a atribuição de memória são utilizados pelos serviços *getaddrinfo* e *getnameinfo:*

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
        const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
        char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

Quando a aplicação BSD ligar para *o getaddrinfo* com um nome de anfitrião, o NetX BSD ligará para qualquer um dos serviços abaixo para obter o endereço IP:

- **nx_dns_ipv4_address_by_name_get**
- **nxd_dns_ipv6_address_by_name_get**
- **nx_dns_cname_get**

Para *nx_dns_ipv4_address_by_name_get* e *nxd_dns_ipv6_address_by_name_get,* o NetX BSD utiliza as áreas de memória ipv4_addr_buffer e ipv6_addr_buffer, respectivamente. O tamanho destes tampão é definido por (NX_BSD_IPV4_ADDR_PER_HOST * 4) e (NX_BSD_IPV6_ADDR_PER_HOST * 16) respectivamente.

Para obter informações de endereços do *getaddrinfo,* o NetX BSD utiliza a tabela de memórias do bloco ThreadX nx_bsd_addrinfo_pool_memory, cuja área de memória é definida por outro conjunto de opções configuráveis, NX_BSD_IPV4_ADDR_MAX_NUM e NX_BSD_IPV6_ADDR_MAX_NUM.

Consulte **as Opções gerais de Configuração** para obter mais detalhes sobre as opções de configuração acima.

Além disso, se NX_DNS_ENABLE_EXTENDED_RR_TYPES estiver definido, e a entrada do anfitrião for um nome canónico, o NetX Duo BSD irá alocar a memória dinamicamente a partir de um bloco de blocos anteriormente criado '_nx_bsd_cname_block_pool

> [!NOTE]
> Depois de chamar *getaddrinfo,* a aplicação BSD é responsável por libertar a memória apontada pelo argumento res de volta à mesa de blocos usando o serviço *freeaddrinfo.*

## <a name="netx-duo-bsd-limitations"></a>NetX Duo BSD Limitações

Devido a problemas de desempenho e arquitetura, o NetX Duo BSD não suporta todas as funcionalidades da tomada BSD 4.3:

As bandeiras do INT não são suportadas para *envio, recv, envio* e *recv de* chamadas.

## <a name="general-configuration-options"></a>Opções de Configuração Geral

As opções configuráveis do utilizador em *nxd_bsd.h* permitem que a aplicação afina as tomadas BSD NetX Duo para os seus requisitos específicos de aplicação.

Segue-se a lista de opções configuráveis que são definidas no momento da compilação:

- **NX_BSD_TCP_WINDOW**: Utilizado na tomada TCP cria chamadas. 64k é o tamanho típico da janela para 100Mb Ethernet. O valor predefinido é 65535.

- **NX_BSD_SOCKFD_START**: Este é o índice lógico para o valor de partida do ficheiro de ficha BSD. Por padrão, esta opção é 32.

- **NX_BSD_MAX_SOCKETS**: Especifica o número máximo de tomadas totais disponíveis na camada BSD e deve ser um múltiplo de 32. O valor está em incumprimento para 32.

- **NX_BSD_SOCKET_QUEUE_MAX**: Especifica o número máximo de pacotes UDP armazenados na fila da tomada de receção. O valor está em incumprimento a 5.

- **NX_BSD_MAX_LISTEN_BACKLOG**: Isto especifica o tamanho da fila de escuta ('backlog') para as tomadas BSD TCP. O valor predefinido é 5.

- **NX_MICROSECOND_PER_CPU_TICK**: Especifica o número de microsegundos por cronoça do temporizador do programador.

- **NX_BSD_TIMEOUT**: Especifica o tempo limite nos tiques temporais nas chamadas internas netx duo exigidas pela BSD. O valor predefinido é (20* NX_IP_PERIODIC_RATE).

- **NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: Especifica o tempo limite no temporizador na chamada de desconexão NetX Duo. O valor predefinido é 1.

- **NX_BSD_PRINT_ERRORS**: Se for definido, a devolução do estado de erro de uma função BSD devolve um número de linha e um tipo de erro, por exemplo, NX_SOC_ERROR onde ocorre o erro. Isto requer que o desenvolvedor de aplicações defina a saída de depurar. A definição predefinida é desativada e nenhuma saída de depuração é especificada em *nxd_bsd.h*.

- **NX_BSD_TIMER_RATE**: Intervalo após o qual a tarefa do temporizador periódico BSD é executado. O valor predefinido é de 1 segundo (1 * NX_IP_PERIODIC_RATE).

- **NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: Se for definida, esta opção permite que o processo de tempo limite de BSD seja executado no contexto do temporizador do sistema. O comportamento predefinido é desativado. Esta característica é descrita mais detalhadamente no capítulo 2 "Instalação e Utilização do Duo BSD NetX".

- **NX_BSD_RAW_PPPOE_SUPPORT**: Ativar o suporte ao pacote cru ppPoE. Por padrão, esta opção não está ativada.

- **NX_BSD_ENABLE_DNS**: Se estiver ativado, o NetX Duo BSD enviará uma consulta DNS para um nome de anfitrião ou endereço IP anfitrião. Requer que uma instância do Cliente DNS seja previamente criada e iniciada. Por predefinição, não está ativado.

- **NX_BSD_SOCKET_RAW_PROTOCOL_TABLE_SIZE**: Define o tamanho da tabela de tomadas em bruto. O valor deve ser um poder de dois. NetX BSD cria uma série de tomadas de tipo NX_BSD_SOCKETS para envio e receção de pacotes crus. NX_ENABLE_IP_RAW_PACKET_FILTER deve ser ativado. Por defeito é 32.

- **NX_BSD_IPV4_ADDR_MAX_NUM**: Número máximo de endereços IPv4 devolvidos por *getaddrinfo*. Isto juntamente com NX_BSD_IPV6_ADDR_MAX_NUM define o tamanho do pool de blocos BSD NetX nx_bsd_addrinfo_block_pool para alocar a memória dinamicamente para endereçar o armazenamento de informação em *getaddrinfo*. O valor predefinido é 5.

- **NX_BSD_IPV6_ADDR_MAX_NUM**: Número máximo de endereços IPv6 devolvidos por *getaddrinfo*. Isto juntamente com NX_BSD_IPV4_ADDR_MAX_NUM define o tamanho do conjunto de blocos BSD NetX nx_bsd_addrinfo_block_pool para alocar a memória dinamicamente para endereçar o armazenamento de informação em *getaddrinfo*.

- **NX_BSD_IPV4_ADDR_PER_HOST**: Define os endereços IPv4 máximos armazenados por consulta DNS. O valor predefinido é 5.

- **NX_BSD_IPV6_ADDR_PER_HOST**: Define os endereços IPv6 máximos armazenados por consulta DNS. O valor predefinido é 2.

## <a name="bsd-socket-options"></a>Opções de tomada BSD

A seguinte lista de opções de tomada BSD NetX Duo pode ser ativada (ou desativada) no tempo de execução numa base por tomada utilizando o serviço *setsockopt:*

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, 
                const void *option_value, INT option_length);
```

Há duas configurações diferentes para option_level.

O primeiro tipo de opções de tomada de tempo de funcionamento é SOL_SOCKET para opções de nível de tomada. Para ativar uma opção de nível de tomada, ligue *para option_level* definido para SOL_SOCKET e option_name definido para a opção específica, por exemplo, SO_BROADCAST *.* Para recuperar uma definição de opção, *ligue* para o option_name com option_level novamente definido para SOL_SOCKET.

A lista das opções de nível de tomada de tempo de funcionamento é mostrada abaixo.

- **SO_BROADCAST**: Se estiver definido, isto permite o envio e receção de pacotes de transmissão a partir de tomadas Netx. Este é o comportamento padrão para o NetX Duo. Todas as tomadas têm esta capacidade.

- **SO_ERROR**: Utilizado para obter o estado da tomada no funcionamento anterior da tomada da tomada especificada, utilizando o serviço *getsockopt.* Todas as tomadas têm esta capacidade.

- **SO_KEEPALIVE**: Se estiver definido, isto permite a funcionalidade TCP Keep Alive. Isto requer que a biblioteca NetX Duo seja construída com NX_TCP_ENABLE_KEEPALIVE definida em *nx_user.h*. Por predefinição, esta função está desativada.

- **SO_RCVTIMEO**: Isto define a opção de espera em segundos para receber pacotes nas tomadas BSD NetX Duo. O valor predefinido é o NX_WAIT_FOREVER (0xFFFFFFFF) ou, se não estiver ativado o não bloqueio, NX_NO_WAIT (0x0).

- **SO_RCVBUF**: Isto define o tamanho da janela da tomada TCP. O valor predefinido, NX_BSD_TCP_WINDOW, está definido para 64k para tomadas BSD TCP. Para definir o tamanho acima de 65535 requer que a biblioteca NetX Duo seja construída com o NX_TCP_ENABLE_WINDOW_SCALING ser definida.

- **SO_REUSEADDR**: Se estiver definido, isto permite que várias tomadas sejam mapeadas para uma porta. A utilização típica é para a tomada do Servidor TCP. Este é o comportamento padrão das tomadas NetX Duo.

O segundo tipo de opções de tomada de tempo de funcionamento é o nível de opção IP. Para ativar uma opção de nível IP, ligue *para os conjuntos* de chamadas com option_level definidos para IP_PROTO e option_name definidos para a opção, por exemplo, IP_MULTICAST_TTL *.* Para recuperar uma definição de opção, *ligue* para o option_name com option_level novamente definido para IP_PROTO.

A lista de opções de nível IP de tempo de execução é mostrada abaixo.

- **IP_MULTICAST_TTL**: Este define o tempo de viver para tomadas UDP. O valor predefinido é NX_IP_TIME_TO_LIVE (0x80) quando a tomada é criada. Este valor pode ser ultrapassado chamando *setsockopt* com esta opção de tomada.

- **IP_RAW_IPV6_HDRINCL**: Se esta opção for definida, o pedido de chamada deve anexar um cabeçalho IPv6 e opcionalmente cabeçalhos de aplicação aos dados transmitidos em tomadas IPv6 em bruto criadas pela BSD. Para utilizar esta opção, o processamento da tomada em bruto deve ser ativado na tarefa IP.

- **IP_ADD_MEMBERSHIP**: Se estiver definido, esta opção permite que a tomada BSD (se aplica apenas às tomadas UDP) se junte ao grupo IGMP especificado.

- **IP_DROP_MEMBERSHIP**: Se estiver definido, esta opção permite que a tomada BSD (se aplica apenas às tomadas UDP) saia do grupo IGMP especificado.

- **IP_HDRINCL**: Se esta opção for definida, a aplicação de chamada deve anexar o cabeçalho IP e opcionalmente os cabeçalhos de aplicação aos dados transmitidos em tomadas IPv4 em bruto criadas em BSD. Para utilizar esta opção, o processamento da tomada em bruto deve ser ativado na tarefa IP.

- **IP_RAW_RX_NO_HEADER**: Se estiver limpo, o cabeçalho IPv6 é incluído com os dados recebidos para tomadas IPv6 em bruto criadas em BSD. Os cabeçalhos IPv6 são removidos por padrão em tomadas IPv6 em bruto BSD, e o comprimento do pacote não inclui o cabeçalho IPv6.

Se for definido, o cabeçalho IPv4 é removido dos dados recebidos em tomadas em bruto de BSD do tipo IPv4. Os cabeçalhos IPv4 são incluídos por predefinição nas tomadas IPv4 em bruto da BSD e o comprimento do pacote inclui o cabeçalho IPv4.

Esta opção não tem qualquer efeito nos dados de transmissão do IPv4 ou do IPv6.

## <a name="small-ipv4-example"></a>Pequeno Exemplo IPv4

Um exemplo de como utilizar os serviços BSD NetX Duo para redes IPv4 é descrito abaixo. Neste exemplo, o ficheiro incluído *nxd_bsd.h* é trazido na linha 8. Em seguida, a instância IP *bsd_ip* e *pacotes bsd_pool* são criados como variáveis globais nas linhas 20 e 21. Note que esta demonstração utiliza um controlador de rede ram (virtual),*_nx_ram_network_driver*. O cliente e o servidor partilharão o mesmo endereço IP numa única instância IP neste exemplo.

Os fios do cliente e do servidor são criados nas linhas 62 e 68. O pacote BSD para transmissão de pacotes é criado na linha 78 e usado na criação de instância IP na linha 87. Note que a tarefa de linha IP é dada prioridade 1 na *chamada nx_ip_create.* Este fio deve ser a tarefa de maior prioridade definida no programa para um desempenho netx ideal.

A instância IP está ativada para os serviços ARP e TCP nas linhas 88 e 110, respectivamente. O último requisito antes de os serviços BSD poderem ser utilizados é chamar *bsd_initialize* on line 120 para configurar todas as estruturas de dados e recursos NetX e ThreadX necessários pela BSD.

A função de entrada de fio do servidor é definida em seguida. A tomada BSD TCP é criada na linha 149. O endereço IP do servidor e a porta estão definidos nas linhas 160-163. Note a utilização do hospedeiro para a rede byte macros *htonl* e *htons aplicados* no endereço IP e na porta. Isto está em conformidade com a especificação da tomada BSD que os dados de múltiplos bytes são submetidos aos serviços BSD em ordem byte de rede.

Em seguida, a tomada do servidor principal está ligada à porta utilizando o serviço *de ligação* na linha 166. Esta é a tomada de audição para pedidos de ligação TCP utilizando o serviço *de escuta* na linha 180. A partir daqui, a função de thread do servidor, *thread_server_entry,* loops para verificar se há eventos de receção utilizando a chamada *selecionada* na linha 202. Se um evento de receção for um pedido de ligação, que é determinado comparando a lista de prontos de leitura, chama *aceitar* na linha 213. Uma tomada do servidor de criança é designada para lidar com o pedido de ligação e adicionada à lista principal de tomadas de servidor TCP ligadas a um Cliente na linha 223. Se não houver novos pedidos de ligação, o fio do servidor verifica todas as tomadas atualmente ligadas para receber eventos no loop a partir da linha 236. Quando é detetada uma espera de evento de receção, liga *para enviar* e *recv* na tomada até que não sejam recebidos dados (ligação fechada do outro lado) e a tomada é fechada utilizando o serviço *de soc_close* na linha 277.

Após a instalação da linha do servidor, a função de entrada da linha de fio cliente, *thread_client_entry,* cria uma tomada na linha 326 e liga-se à tomada do servidor TCP utilizando a chamada *de ligação* na linha 337. Em seguida, dá voltas para enviar e receber pacotes usando os serviços *de envio* e *recv,* respectivamente. Quando não são recebidos mais dados, fecha a tomada na linha 398 utilizando o serviço *soc_close.* Após a desconexão, a função de entrada de fio do cliente cria uma nova tomada TCP e faz outro pedido de ligação no ciclo de enquanto o loop começou na linha 321.

```c
/* This is a small demo of BSD Wrapper for the high-performance NetX Duo
TCP/IP stack which uses standard BSD services for TCP connection, sending,
and receiving using a simulated Ethernet driver. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nxd_bsd.h"
#include     <string.h>
#include     <stdlib.h>

#define     DEMO_STACK_SIZE     (16*1024)
#define     SERVER_PORT         87
#define     CLIENT_PORT         77

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_server;
TX_THREAD         thread_client;
NX_PACKET_POOL    bsd_pool;
NX_IP             bsd_ip;

/* Define some global data. */
CHAR     *msg0 = "Client 1:
    ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQR
    STUVWXYZ<>END";

INT     maxfd;

/* Define the counters used in the demo application... */

ULONG     error_counter;

/* Define fd_sets for the BSD server socket. */
fd_set     master_list, read_ready;

/* Define thread prototypes. */

VOID     thread_server_entry(ULONG thread_input);
VOID     thread_client_entry(ULONG thread_input);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */
int     main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void     tx_application_define(void *first_unused_memory)
{
CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create a server thread. */
    tx_thread_create(&thread_server, "Server", thread_server_entry, 0,
                    pointer, DEMO_STACK_SIZE, 8, 8, TX_NO_TIME_SLICE,
                    TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Create a Client thread. */
    tx_thread_create(&thread_client, "Client", thread_client_entry, 0,
                    pointer, DEMO_STACK_SIZE, 16, 16, TX_NO_TIME_SLICE,
                    TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a BSD packet pool. */
    status = nx_packet_pool_create(&bsd_pool, "NetX BSD Packet Pool", 128,
                                pointer, 16384);

    pointer = pointer + 16384;
    if (status)
    {
        error_counter++;
        printf("Error in creating BSD packet pool\n!");
    }

    /* Create an IP instance for BSD. */
    status = nx_ip_create(&bsd_ip, "BSD IP Instance", IP_ADDRESS(1,2,3,4),
                    0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                    pointer, 2048, 1);
                    pointer = pointer + 2048;

    if (status)
    {
        error_counter++;
        printf("Error creating BSD IP instance\n!");
    }

    /* Enable ARP and supply ARP cache memory for BSD IP Instance */
    status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable ARP \n");
    }

    /* Enable TCP processing for BSD IP instances. */
    status = nx_tcp_enable(&bsd_ip);

    /* Check TCP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable TCP \n");
    }

    /* Now initialize BSD Scoket Wrapper */
    status = bsd_initialize (&bsd_ip, &bsd_pool,pointer, 2048, 2);
}

/* Define the Server thread. */
CHAR     Server_Rcv_Buffer[100];

VOID     thread_server_entry(ULONG thread_input)
{

INT       status, sock, sock_tcp_server;
ULONG     actual_status;
INT       Clientlen;
INT       i;
UINT      is_set = NX_FALSE;
struct    sockaddr_in serverAddr;
struct    sockaddr_in ClientAddr;

    tx_thread_sleep(100);

    status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE,
        &actual_status, 100);

    /* Check status... */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Create BSD TCP Socket */
    sock_tcp_server = socket(AF_INET, SOCK_STREAM, 0);

    if (sock_tcp_server == -1)
    {
        printf("Error on Server socket %d create \n", sock_tcp_server);
        return;
    }

    printf("Server socket %d created\n", sock_tcp_server);

    /* Set the server port and IP address */
    memset(&serverAddr, 0, sizeof(serverAddr));
    serverAddr.sin_family = AF_INET;
    serverAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    serverAddr.sin_port = htons(SERVER_PORT);

    /* Bind this server socket */
    status = bind (sock_tcp_server, (struct sockaddr *) &serverAddr,
                sizeof(serverAddr));

    if (status < 0)
    {
        printf("Error on Server Socket %d Bind \n", sock_tcp_server);
        return;
    }

    FD_ZERO(&master_list);
    FD_ZERO(&read_ready);
    FD_SET(sock_tcp_server,&master_list);
    maxfd = sock_tcp_server;

    /* Now listen for any client connections for this server socket */
    status = listen (sock_tcp_server, 5);
    if (status < 0)
    {
        printf("Error on Server Socket %d Listen\n", sock_tcp_server);
        return;
    }
    else
        printf("Server socket %d listen complete\n", sock_tcp_server);

    /* All set to accept client connections */

    /* Loop to create and establish server connections. */
    while(1)
    {

        printf("\n");

        read_ready = master_list;

        tx_thread_sleep(20); /* Allow some time to other threads too */

        /* Let the underlying TCP stack determine the timeout. */
        status = select(maxfd + 1, &read_ready, 0, 0, 0);

        if ((status == 0xFFFFFFFF) || (status == 0))
        {

            printf("Error with select. Status 0x%x\n", status);

            continue;
        }

        /* Check for a connection request. */
        is_set = FD_ISSET(sock_tcp_server, &read_ready);

        if(is_set)
        {

            Clientlen = sizeof(ClientAddr);

            sock = accept(sock_tcp_server,(struct sockaddr*)&ClientAddr,
                        &Clientlen);

            /* Add this new connection to our master list */
            FD_SET(sock, &master_list);

            if ( sock \maxfd)
            {

                maxfd = sock;
            }

            continue;
        }

        /* Check the set of 'ready' sockets, e.g connected to remote host and
        waiting for notice of packets received. */
        for (i = NX_BSD_SOCKFD_START; i < (maxfd+1+NX_BSD_SOCKFD_START); i++)
        {

            if ((i != sock_tcp_server) &&
                (FD_ISSET(i , &master_list)) &&
                (FD_ISSET(i , &read_ready)))
            {

                while(1)
                {

                    status = recv(i, (VOID *)Server_Rcv_Buffer, 100, 0);

                    if (status == 0)
                    {
                        printf("(Server received no data from Client on
                            socket %d)\n", i);
                        break;
                    }
                    else if (status == NX_SOC_ERROR)
                    {
                        printf("Error on Server receiving data from Client on
                            socket %d\n", i);
                        break;
                    }
                    if(status == SERVER_RCV_BUFFER_SIZE) status--;
                    Server_Rcv_Buffer[status] = 0;
                    printf("Server socket %d received %d bytes: %s\n ",
                            i, (ULONG)status, Server_Rcv_Buffer);

                    status = send(i, "Hello\n", sizeof("Hello\n"), 0);

                    if (status == NX_SOC_ERROR)
                    {
                        printf("Error on Server socket %d sending data to
                        Client\n", i);
                    }
                    else
                    {
                        printf("Server socket %d message sent to Client:
                        Hello\n", i);
                    }
                }

                /* Close this socket */
                status = soc_close(i);

                if (status != NX_SOC_ERROR)
                {
                    printf("Server socket %d closed \n", i);
                }
                else
                {
                    printf("Error on closing Server socket %d \n", i);
                }
            }
        }

    /* Loop back to check any next client connection */
    }
}

CHAR     Client_Rcv_Buffer[100];

VOID     thread_client_entry(ULONG thread_input)
{

INT        status;
INT        sock_tcp_client, length;
struct     sockaddr_in echoServAddr;
struct     sockaddr_in localAddr; /

    /* Let the server side get set up. */
    tx_thread_sleep(200);

    /* Set local port for displaying IP address and port. */
    memset(&localAddr, 0, sizeof(localAddr));
    localAddr.sin_family = AF_INET;
    localAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    localAddr.sin_port = htons(CLIENT_PORT);

    /* Set server port and IP address which we need to connect. */
    memset(&echoServAddr, 0, sizeof(echoServAddr));
    echoServAddr.sin_family = AF_INET;
    echoServAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    echoServAddr.sin_port = htons(SERVER_PORT);

    /* Now make client connections with the server. */
    while (1)
    {

        printf("\n");

        /* Create BSD TCP Socket */
        sock_tcp_client = socket( AF_INET, SOCK_STREAM, 0);

        if (sock_tcp_client == -1)
        {
            printf("Error on Client socket %d create \n", sock_tcp_client);
            return;
        }

        printf("Client socket %d created\n", sock_tcp_client);

        /* Now connect this client to the server */
        status = connect(sock_tcp_client, (struct sockaddr *)&echoServAddr,
                        sizeof(echoServAddr));

        /* Check for error. */
        if (status != OK)
        {
            printf("Error on Client socket %d connect\n", sock_tcp_client);
                    soc_close(sock_tcp_client);
            return;
        }

        /* Get and print source and destination information */
        printf("Client socket %d connected \n", sock_tcp_client);

        status = getsockname(sock_tcp_client, (struct sockaddr *)&localAddr,
                            &length);

        printf("Client port = %lu , Client = 0x%x,",
            htonl(localAddr.sin_port), htonl(localAddr.sin_addr.s_addr));

        length = sizeof(struct sockaddr_in);

        status = getpeername( sock_tcp_client, (struct sockaddr *)
                            &echoServAddr, &length);

        printf("Remote port = %lu, Remote IP = 0x%x \n",
                htonl(echoServAddr.sin_port),
                htonl(echoServAddr.sin_addr.s_addr));

        /* Now receive the echoed packet from the server */
        while(1)
        {

            printf("Client sock %d sending packet to server\n",
            sock_tcp_client);

            status = send(sock_tcp_client, "Hello", (sizeof("Hello")), 0);

            if (status == ERROR)
            {
                printf("Error: Client Socket (%d) send \n", sock_tcp_client);
            }
            else
            {
                printf("Client socket %d sent message Hello\n",
                        sock_tcp_client);
            }

            status = recv(sock_tcp_client, (VOID *)Client_Rcv_Buffer,100,0);

            if (status <= 0)
            {

                if (status < 0)
                {
                    380 printf("Error on Client receiving on socket %d \n",
                            sock_tcp_client);
                }
                else
                {
                    printf("Nothing received by Client on socket %d\n",
                            sock_tcp_client);
                }

                break;
            }
            else
            {
                printf("Client socket %d received %d bytes: %s\n",
                        sock_tcp_client,
                        status, Client_Rcv_Buffer);
            }

        }

        /* close this client socket */
        status = soc_close(sock_tcp_client);

        if (status != ERROR)
        {
            printf("Client Socket %d closed\n", sock_tcp_client);
        }
        else
        {
            printf("Error on Client Socket %d on close \n", sock_tcp_client);
        }

        /* Make another Client connection...*/

    }
}
```

## <a name="small-ipv6-example-system"></a>Sistema de exemplo ipv6 pequeno

Um exemplo de como utilizar os serviços BSD NetX Duo para redes IPv6 é descrito no programa abaixo. Este exemplo é muito semelhante ao programa de demonstração IPv4 anteriormente descrito com algumas diferenças importantes.

As linhas de cliente e servidor, piscina de pacotes BSD, instância IP e inicialização BSD acontecem como acontece com as tomadas BSD IPv4.

Na função de entrada de fio do servidor, *thread_server_entry,* define um par de variáveis IPv6 utilizando *sockaddr_in6* e *NXD_ADDRESS* tipos de dados nas linhas 145-148. O tipo de dados NXD_ADDRESS pode armazenar os tipos de endereços IPv4 e IPv6.

Em seguida, o fio do servidor permite iPv6 e ICMPv6 na instância IP utilizando o serviço *de nxd_ipv6_enable* e *nxd_icmpv6_enable,* respectivamente, nas linhas 161 e 169. Em seguida, os endereços IP locais e globais do link estão registados na instância IP. Isto é feito usando o serviço *nxd_ipv6_address_set* nas linhas 180 e 195. Em seguida, dorme o tempo suficiente para que a tarefa de thread IP complete o protocolo de Deteção de Endereços Duplicado e registe estes endereços como endereços válidos na *chamada tx_thread_sleep* on-line 201.

Em seguida, a tomada do servidor TCP é criada com o AF_INET6 argumento de entrada do tipo tomada na linha 204. O endereço e porta do IPv6 da tomada são definidos nas linhas 216-221, observando novamente a utilização de macros *htonl* e *htons* para colocar dados em ordem de byte de rede para serviços de tomada de BSD. A partir de agora, a função de entrada de fio do servidor é praticamente idêntica ao exemplo IPv4.

A função de entrada de fio do cliente, *thread_client_entry,* é definida em seguida. Note que, uma vez que o cliente TCP neste exemplo partilha a mesma instância IP e endereço IPv6 que o servidor TCP, não precisamos de ativar os serviços IPv6 ou ICMPv6 na instância IP novamente. Além disso, o endereço IPv6 também já está registado na instância IP. Em vez disso, a função de entrada de fio do cliente simplesmente aguarda na linha 368 para que o servidor se instale. O endereço e a porta do servidor estão definidos, utilizando o anfitrião para encomendar macros de encomenda de rede nas linhas 387-392, e então o Cliente pode ligar-se ao servidor TCP na linha 412. Note que os tipos de dados de endereço IP locais nas linhas 378-383 são utilizados apenas para demonstrar o *nome getockname* e os serviços *de nome getpeerna* nas linhas 425 e 434, respectivamente. Como os dados vêm da rede, a rede para hospedar byte macros como usado nas linhas 378-383.

Em seguida, a função de entrada de fio do cliente introduz um loop no qual cria uma tomada TCP, faz uma ligação TCP e envia e recebe dados com o servidor TCP até que nenhum dado seja recebido praticamente o mesmo que o exemplo IPv4. Em seguida, fecha a tomada na linha 483, faz uma pausa breve e cria outra tomada TCP e solicita uma ligação do servidor TCP.

Uma diferença importante com o exemplo IPv4 é que as chamadas de *tomada* especificam uma tomada IPv6 utilizando o argumento de entrada AF_INET6. Outra diferença importante é que a chamada *de ligação* do Cliente TCP requer um tipo *de dados sockaddr_in6* e um argumento de comprimento definido para o tamanho do tipo de dados *sockaddr_in6.*

```c
/* This is a small demo of BSD Wrapper for the high-performance NetX Duo
TCP/IP stack which uses standard BSD services for TCP connection,
disconnection, sending, and receiving using a simulated Ethernet driver. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nxd_bsd.h"
#include     <string.h>
#include     <stdlib.h>

#define     DEMO_STACK_SIZE     (16*1024)
#define     SERVER_PORT         87
#define     CLIENT_PORT         77

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_server;
TX_THREAD         thread_client;
NX_PACKET_POOL    bsd_pool;
NX_IP             bsd_ip;

/* Define some global data. */
CHAR     *msg0 = "Client 1:
    ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>END";

INT     maxfd;

/* Define the counters used in the demo application... */
ULONG     error_counter;

/* Define fd_sets for the BSD server socket. */
fd_set     master_list, read_ready;

/* Define thread prototypes. */
VOID     thread_server_entry(ULONG thread_input);
VOID     thread_client_entry(ULONG thread_input);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

int     main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void tx_application_define(void *first_unused_memory)
{
CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create a server thread. */
    tx_thread_create(&thread_server, "Server", thread_server_entry, 0,
                    pointer, DEMO_STACK_SIZE, 8, 8,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Create a Client thread. */
    tx_thread_create(&thread_client, "Client", thread_client_entry, 0,
                    pointer, DEMO_STACK_SIZE, 16, 16,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a BSD packet pool. */
    status = nx_packet_pool_create(&bsd_pool, "NetX BSD Packet Pool",
    128, pointer, 16384);

    pointer = pointer + 16384;

    if (status)
    {
        error_counter++;
        printf("Error in creating BSD packet pool\n!");
    }

    /* Create an IP instance for BSD. */
    status = nx_ip_create(&bsd_ip, "BSD IP Instance", IP_ADDRESS(1,2,3,4),
                        0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                        pointer, 2048, 1);
                        pointer = pointer + 2048;

    if (status)
    {
        error_counter++;
        printf("Error creating BSD IP instance\n!");
    }

    /* Enable ARP and supply ARP cache memory for BSD IP Instance */
    status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in enable ARP on BSD IP instance\n");
    }

    /* Enable TCP processing for BSD IP instances. */
    status = nx_tcp_enable(&bsd_ip);

    /* Check TCP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable TCP \n");
    }

    /* Now initialize BSD Scoket Wrapper */
    status = bsd_initialize(&bsd_ip, &bsd_pool,pointer, 2048, 2);

    /* Check BSD initialize status. */
    if (status)
    {
        error_counter++;
        printf("Error in BSD initialize \n");
    }

    pointer = pointer + 2048;
}

/* Define the Server thread. */
CHAR     Server_Rcv_Buffer[100];

VOID     thread_server_entry(ULONG thread_input)
{

INT             status, sock, sock_tcp_server;
ULONG           actual_status;
INT             Clientlen;
INT             i;
UINT            is_set = NX_FALSE;
NXD_ADDRESS     ip_address;
struct          sockaddr_in6 serverAddr;
struct          sockaddr_in6 ClientAddr;
UINT            iface_index, address_index;

    status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE,
            &actual_status, 100);

    /* Check status... */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable IPv6 */
    status = nxd_ipv6_enable(&bsd_ip);
    if((status != NX_SUCCESS) && (status != NX_ALREADY_ENABLED))
    {
        printf("Error with IPv6 enable 0x%x\n", status);
        return;
    }

    /* Enable ICMPv6 */
    status = nxd_icmp_enable(&bsd_ip);

    if(status)
    {
        printf("Error with ECMPv6 enable 0x%x\n", status);
        return;
    }

    /* Set the primary interface for our DNS IPv6 addresses. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&bsd_ip, iface_index, NX_NULL, 10,
                                &address_index);

    if (status)
        return;

    /* Set ip_0 interface address. */
    ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    ip_address.nxd_ip_address.v6[0] = htonl(0x20010db8);
    ip_address.nxd_ip_address.v6[1] = htonl(0x0000f101);
    ip_address.nxd_ip_address.v6[2] = 0;
    ip_address.nxd_ip_address.v6[3] = htonl(0x101);

    /* Set the host global IP address. We are assuming a 64
    bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&bsd_ip, iface_index, &ip_address, 64,
                                &address_index);

    if (status)
        return;

    /* Wait for IPv6 stack to finish DAD process. */
    tx_thread_sleep(400);

    /* Create BSD TCP Socket */
    sock_tcp_server = socket(AF_INET6, SOCK_STREAM, 0);

    if (sock_tcp_server == -1)
    {
        printf("\nError: BSD TCP Server socket create \n");
        return;
    }

    printf("\nBSD TCP Server socket created %lu \n", sock_tcp_server);

    /* Set the server port and IP address */
    memset(&serverAddr, 0, sizeof(serverAddr));
    serverAddr.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    serverAddr.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    serverAddr.sin6_addr._S6_un._S6_u32[2] = 0x0;
    serverAddr.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    serverAddr.sin6_port = htons(SERVER_PORT);
    serverAddr.sin6_family = AF_INET6;

    /* Bind this server socket */
    status = bind(sock_tcp_server, (struct sockaddr *) &serverAddr,
                    sizeof(serverAddr));

    if (status < 0)
    {
        printf("Error: Server Socket Bind \n");
        return;
    }

    FD_ZERO(&master_list);
    FD_ZERO(&read_ready);
    FD_SET(sock_tcp_server,&master_list);
    maxfd = sock_tcp_server;

    /* Now listen for any client connections for this server socket */
    status = listen(sock_tcp_server, 5);
    if (status < 0)
    {
        printf("Error: Server Socket Listen\n");
        return;
    }
    else
        printf("Server Listen complete\n");

    /* All set to accept client connections */
    printf("Now accepting client connections\n");

    /* Loop to create and establish server connections. */
    while(1)
    {

        printf("\n");

        read_ready = master_list;

        tx_thread_sleep(20); /* Allow some time to other threads too */

        /* Let the underlying TCP stack determine the timeout. */
        status = select(maxfd + 1, &read_ready, 0, 0, 0);

        if ( (status == 0xFFFFFFFF) || (status == 0) )
        {
            printf("Error with select? Status 0x%x. Try again\n", status);

            continue;
        }

        /* Detected a connection request. */
        is_set = FD_ISSET(sock_tcp_server,&read_ready);

        if(is_set)
        {

            Clientlen = sizeof(ClientAddr);

            sock = accept(sock_tcp_server,
            (struct sockaddr*)&ClientAddr,
            &Clientlen);

            /* Add this new connection to our master list */
            FD_SET(sock, &master_list);

            if ( sock \maxfd)
            {
                printf("New connection %d\n", sock);

                maxfd = sock;
            }

            continue;
        }

        /* Check the set of 'ready' sockets, e.g connected to remote host and
        waiting for notice of packets received. */
        for (i = NX_BSD_SOCKFD_START; i < (maxfd+1+NX_BSD_SOCKFD_START); i++)
        {

            if ((i != sock_tcp_server) &&
                (FD_ISSET(i, &master_list)) &&
                (FD_ISSET(i, &read_ready)))
            {

                while(1)
                {

                    status = recv(i, (VOID *)Server_Rcv_Buffer, 100, 0);

                    if (status == 0)
                    {
                        printf("(Server socket %d received no data from
                                Client)\n", i);

                        break;
                    }
                    else if (status == 0xFFFFFFFF)
                    {
                        printf("Error on Server socket %d receiving data from
                                Client\n", i);

                        break;
                    }

                    printf("Server socket %d received from Client %lu bytes:
                            %s\n ", i, (ULONG)status,
                            Server_Rcv_Buffer);

                    status = send(i, "Hello\n", sizeof("Hello\n"), 0);

                    if (status == ERROR)
                    {
                        printf("Error on Server socket %d sending data to
                                Client \n", i);
                    }
                    else
                    {
                        printf("Server socket %d message sent to Client:
                                Hello\n", i);
                    }
                }

                /* Close this socket */
                status = soc_close(i);

                if (status != ERROR)
                {
                    printf("Server socket %d closing\n", i);
                }
                else
                {

                    printf("Error on Server socket %d closing\n", i);
                }
            }
        }

        /* Loop back to check any next client connection */
    }
}

#define     CLIENT_BUFFER_SIZE 100
CHAR        Client_Rcv_Buffer[CLIENT_BUFFER_SIZE];

VOID        thread_client_entry(ULONG thread_input)
{

INT         status;
INT         sock_tcp_client, length;
struct      sockaddr_in6 echoServAddr6;
struct      sockaddr_in6 localAddr6; address */

    /* Wait for the server side to get set up, including the DAD process. */
    tx_thread_sleep(500);

    /* ICMPv6 and IPv6 should already be enabled on the IP instance
    by the server thread entry function. */

    /* Further the IPv6 address is already established with the IP instance.
    so no need to wait for DAD completion. */

    /* Set local port and IP address (used only for getsockname call). */
    memset(&localAddr6, 0, sizeof(localAddr6));
    localAddr6.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    localAddr6.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    localAddr6.sin6_addr._S6_un._S6_u32[2] = 0x0;
    localAddr6.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    localAddr6.sin6_port = htons(CLIENT_PORT);
    localAddr6.sin6_family = AF_INET6;

    /* Set Server port and IP address to connect to the TCP server. */
    memset(&echoServAddr6, 0, sizeof(echoServAddr6));
    echoServAddr6.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    echoServAddr6.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    echoServAddr6.sin6_addr._S6_un._S6_u32[2] = 0x0;
    echoServAddr6.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    echoServAddr6.sin6_port = htons(SERVER_PORT);
    echoServAddr6.sin6_family = AF_INET6;

    /* Now make client connections with the server. */
    while (1)
    {
        printf("\n");

        /* Create BSD TCP Socket */

        sock_tcp_client = socket(AF_INET6, SOCK_STREAM, 0);

        if (sock_tcp_client == -1)
        {
            printf("Error on Client socket %d create \n");
            return;
        }

        printf("Client socket %d created \n", sock_tcp_client);

        /* Now connect this client to the server */
        status = connect(sock_tcp_client, (struct sockaddr *)&echoServAddr6,
                sizeof(echoServAddr6));

        /* Check for error. */
        if (status != NX_SOC_OK)
        {
            printf("Error on Client socket %d connect\n");
            soc_close(sock_tcp_client);
            return;

        }

        /* Get and print source and destination information */
        printf("Client socket %d connected \n", sock_tcp_client);

        status = getsockname(sock_tcp_client, (struct sockaddr *)&localAddr6,
        &length);

        printf("Client port = %lu , Client = 0x%x 0x%x 0x%x 0x%x,",
                ntohs(localAddr6.sin6_port),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[0]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[1]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[2]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[3]));

        length = sizeof(struct sockaddr_in6);

        status = getpeername(sock_tcp_client, (struct sockaddr *)
                            &echoServAddr6, &length);

        printf("Remote port = %lu, Remote IP = 0x%x 0x%x 0x%x 0x%x \n",
                ntohs(echoServAddr6.sin6_port),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[0]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[1]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[2]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[3]));

        /* Now receive the echoed packet from the server */
        while(1)
        {

            printf("Client sock %d sending packet to server\n",
                sock_tcp_client);

            status = send(sock_tcp_client, "Hello", sizeof("Hello"), 0);

            if (status == NX_SOC_ERROR)
            {
                printf("Error on Client Socket (%d) send \n",
                        sock_tcp_client);
            }
            else
            {
                printf("Client socket %d sent message: Hello\n",
                        sock_tcp_client);
            }

            status = recv(sock_tcp_client, (VOID *)Client_Rcv_Buffer,
                        CLIENT_BUFFER_SIZE, 0);

            if (status <= 0)
            {

                if (status < 0)
                {
                    printf("Error on Client receiving on socket %d \n",
                            sock_tcp_client);
                }
                else
                {
                    printf("Client received no data on socket %d\n",
                            sock_tcp_client);
                }

            break;
            }
            else
            {
                printf("Client socket %d received %d bytes and this message:
                        %s\n", sock_tcp_client, status,
                        Client_Rcv_Buffer);
            }

        }

        /* close this client socket */
        status = oc_close(sock_tcp_client);

        if (status != NX_SOC_ERROR)
        {
            printf("Client Socket %d closed\n", sock_tcp_client);
        }
        else
        {
            printf("Error on Client Socket %d on close \n", sock_tcp_client);
        }

        /* Make another Client connection...*/

    }
}
```
