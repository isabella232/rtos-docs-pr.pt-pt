---
title: Capítulo 2 - Instalação e Utilização do Azure RTOS NetX
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização da pilha de rede de alto desempenho Azure RTOS NetX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 80d6ba18f47ad2b017dfa32260c83ba074a6dbac
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825639"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx"></a>Capítulo 2 - Instalação e Utilização do Azure RTOS NetX

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização da pilha de rede de alto desempenho Azure RTOS NetX.

## <a name="host-considerations"></a>Considerações de Anfitrião

O desenvolvimento incorporado é geralmente realizado em computadores anfitriões Windows ou Linux (Unix). Após a compilação da aplicação, ligada e o executável é gerado no anfitrião, é descarregado para o hardware alvo para execução.

Normalmente, o download do alvo é feito a partir do depurar da ferramenta de desenvolvimento. Após o download, o depurante é responsável por fornecer controlo de execução de alvos (ir, parar, quebrar, etc.) bem como aceder aos registos de memória e processador.

A maioria dos depurares de ferramentas de desenvolvimento comunicam com o hardware-alvo através de ligações de depuro on-chip (TOC), tais como JTAG (IEEE 1149.1) e Modo de Depuramento de Fundo (BDM). Os debuggers também comunicam com o hardware alvo através de ligações In-Circuit Emulation (ICE). As ligações OCD e ICE fornecem soluções robustas com uma intrusão mínima no software residente alvo.

Quanto aos recursos utilizados no hospedeiro, o código fonte do NetX é entregue em formato ASCII e requer aproximadamente 1 Mbytes de espaço no disco rígido do computador anfitrião.

## <a name="target-considerations"></a>Considerações-alvo

NetX requer entre 5 KBytes e 45 KBytes de memória Read-Only (ROM) no alvo. São necessários mais 1 a 5 KBytes da Memória de Acesso Aleatório (RAM) do alvo para a pilha de fios NetX e outras estruturas de dados globais.

Além disso, o NetX requer a utilização de dois objetos temporizadores ThreadX e um objeto mutex ThreadX. Estas instalações são utilizadas para necessidades de processamento periódica e proteção de fios dentro da pilha de protocolo NetX.

## <a name="product-distribution"></a>Distribuição de Produtos

O Azure RTOS NetX pode ser obtido a partir do nosso repositório de código de fonte pública em <https://github.com/azure-rtos/netx/> .

Segue-se uma lista de vários ficheiros importantes no repositório:

- ***nx_api.h***: Ficheiro de cabeçalho C contendo todos os equacionares do sistema, estruturas de dados e protótipos de serviço.
- ***nx_port.h***: Ficheiro de cabeçalho C contendo todas as definições e estruturas de dados específicas da ferramenta de desenvolvimento e alvo.  
- ***demo_netx.c:*** Ficheiro C contendo um pequeno pedido de demonstração.
- ***nx.a (ou nx.lib)** _: Versão binária da biblioteca NetX C que é distribuída com o pacote _standard*.             |

## <a name="netx-installation"></a>Instalação NetX

Pode instalar o NetX clonando o repositório GitHub à sua máquina local. Segue-se a sintaxe típica para a criação de um clone do repositório NetX no seu PC:

```c
    git clone https://github.com/azure-rtos/netx
```

Em alternativa, pode descarregar uma cópia do repositório utilizando o botão **Descarregar** na página principal do GitHub.

Também encontrará instruções para a construção da biblioteca NetX na primeira página do repositório online.

> [!IMPORTANT]
> O software de aplicação precisa de acesso ao ficheiro da biblioteca NetX (geralmente ***nx.a** _ ou _*_nx.lib_*_) e o C inclui ficheiros _*_nx_api.h e nx_port.h**._ Isto é conseguido quer estabelecendo o caminho adequado para as ferramentas de desenvolvimento, quer copiando estes ficheiros para a área de desenvolvimento de aplicações.

## <a name="using-netx"></a>Utilização de NetX

Para utilizar o NetX, o código de aplicação deve incluir ***nx_api.h** _ durante a compilação e ligação com a biblioteca NetX _*_nx.a_*_ (ou _ *_nx.lib_*)*.

Seguem-se as quatro etapas necessárias para a construção de uma aplicação NetX:

1. Inclua o ficheiro ***nx_api.h*** em todos os ficheiros de aplicações que utilizam serviços NetX ou estruturas de dados.
1. Inicialize o sistema NetX chamando ***nx_system_initialize** _ da função _ *_tx_application_define_** ou de um fio de aplicação.  
1. Crie uma instância IP, ative o Protocolo de Resolução de Endereços (ARP), se necessário, e quaisquer tomadas após ***nx_system_initialize*** é chamada.  
1. Compilar fonte de aplicação e ligar-se com a biblioteca de tempo de execução NetX ***nx.a** _ (ou _*_nx.lib_**). A imagem resultante pode ser descarregada para o alvo e executada!

## <a name="troubleshooting"></a>Resolução de problemas

Cada porta NetX é entregue com uma ou mais amostras que executam numa rede real ou através de um controlador de rede simulado. É sempre uma boa ideia pôr o sistema de amostras a funcionar primeiro.

Se o sistema de amostragem não funcionar corretamente, efetuar as seguintes operações para reduzir o problema:

1. Determina quanto da amostra está a funcionar.
2. Aumente os tamanhos das pilhas em quaisquer novos fios de aplicação.
3. Recompilar a biblioteca NetX com as opções de depurg apropriadas listadas na secção de opções de configuração.
4. Examine a estrutura **NX_IP** para ver se os pacotes estão a ser enviados ou recebidos.
5. Examine a piscina de pacotes predefinidos para ver se existem pacotes disponíveis.
6. Certifique-se de que o controlador de rede está a fornecer pacotes ARP e IP com os seus cabeçalhos em limites de 4 bytes para aplicações que requerem conectividade IP.
7. Contornar temporariamente quaisquer alterações recentes para ver se o problema desaparece ou muda. Estas informações devem ser úteis aos nossos engenheiros de apoio.

Siga os procedimentos descritos no tópico [do Centro de Apoio](about-this-guide.md) ao Cliente para enviar as informações recolhidas a partir das etapas de resolução de problemas.

## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração ao construir a biblioteca NetX e a aplicação utilizando o NetX. As opções de configuração podem ser definidas na fonte de aplicação, na linha de comando ou dentro do ***ficheiro nx_user.h,*** salvo especificação em contrário.

> [!IMPORTANT]
> As opções definidas em ***nx_user.h** _ são aplicadas apenas se a aplicação e a biblioteca NetX forem construídas com _ *NX_INCLUDE_USER_DEFINE_FILE** definidas.

As secções seguintes listam as opções de configuração disponíveis no NetX.

### <a name="system-configuration-options"></a>Opções de configuração do sistema  

| Opção  | Descrição  |
|---|---|
| X_DEBUG | Definido, permite a informação opcional de depurar depuragem disponível do controlador de rede RAM Ethernet. |
| NX_DISABLE_ERROR_CHECKING | Definido, remove o erro básico netX verificando a API e melhora o desempenho. Os códigos de devolução da API que não são afetados pela verificação de erros incapacitantes estão listados em tipo de letra arrojado na definição API. Esta definição é normalmente utilizada após a depurada aplicação e quando a sua utilização melhora o desempenho e diminui o tamanho do código. |
| NX_DRIVER_DEFERRED_PROCESSING | Definido, permite o manuseamento de pacotes de controlador de rede diferido. Isto permite ao controlador de rede colocar um pacote na instância IP e ter a verdadeira rotina de processamento chamada a partir do fio de ajuda ip interno netX. |
| NX_ENABLE_EXTENDED_NOTIFY_SUPPORT | Permite mais ganchos de retorno na pilha. Estas funções de retorno são utilizadas pela camada de invólucro BSD. Por padrão esta opção não está definida. |
| NX_ENABLE_SOURCE_ADDRESS_CHECK | Definido, permite verificar o endereço de origem do pacote de entrada. Por predefinição, esta opção é desativada. |
| NX_LITTLE_ENDIAN | Definido, executa a troca de byte necessária em pequenos ambientes endianos para garantir que os cabeçalhos do protocolo estão em formato endiano adequado. Note que o padrão é normalmente configurado em ***nx_port.h***. |
| NX_MAX_PHYSICAL_INTERFACES | Especifica o número total de interfaces de rede física no dispositivo. O valor predefinido é 1 e é definido em ***nx_api.h***. Um dispositivo deve ter pelo menos uma interface física. Note que isto não inclui a interface loopback. |
| NX_PHYSICAL_HEADER | Especifica o tamanho em bytes do cabeçalho físico da armação. O valor predefinido é de 16 (baseado num quadro típico de 14 bytes Ethernet alinhado com limite de 32 bits) e é definido em ***nx_api.h** _. A aplicação pode anular o padrão definindo o valor antes _*_de nx_api.h_*_ ser incluído, como em _ *_nx_user.h_*.* |

### <a name="arp-configuration-options"></a>Opções de configuração ARP  

| Opção  | Descrição  |
|---|---|
| NX_ARP_DEFEND_BY_REPLY | Definido, permite que o NetX defenda o seu endereço IP enviando uma resposta ARP. |
| NX_ARP_DEFEND_INTERVAL | Define o intervalo, em segundos, o módulo ARP envia o próximo pacote de defesa em resposta a uma mensagem ARP que indica um endereço em conflito. |
| NX_ARP_DISABLE_AUTO_ARP_ENTRY | Renomeado para **NX_DISABLE_ARP_AUTO_ENTRY.** Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar **NX_DISABLE_ARP_AUTO_ENTRY**.
| NX_ARP_EXPIRATION_RATE | Especifica o número de segundos de entradas ARP permanecem válidas. O valor predefinido de zero desativa a expiração ou o envelhecimento das entradas ARP e é definido em ***nx_api.h** _. A aplicação pode anular o padrão definindo o valor antes de _ *_nx_api.h*_* está incluído.
| NX_ARP_MAC_CHANGE_NOTIFICATION_ENABLE | Renomeado para **NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION.** Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar **NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION**. |
| NX_ARP_MAX_QUEUE_DEPTH | Especifica o número máximo de pacotes que podem ser em fila enquanto se aguarda uma resposta ARP. O valor predefinido é de 4 e é definido em ***nx_api.h***. |
| NX_ARP_MAXIMUM_RETRIES | Especifica o número máximo de retrações ARP feitas sem uma resposta ARP. O valor predefinido é de 18 e é definido em ***nx_api.h** _. A aplicação pode anular o padrão definindo o valor antes de incluir _*_nx_api.h**._ |
| NX_ARP_UPDATE_RATE | Especifica o número de segundos entre as retríss em dia do ARP. O valor predefinido é de 10, o que representa 10 segundos, e é definido em ***nx_api.h** _. A aplicação pode anular o padrão definindo o valor antes de incluir _*_nx_api.h**._ |
| NX_DISABLE_ARP_AUTO_ENTRY | Definido, desativa a entrada de informações de pedido de ARP na cache ARP. |
| NX_DISABLE_ARP_INFO | Definido, desativa a recolha de informações ARP. |
| NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION | Definido, permite que a ARP invoque uma função de notificação de chamada na deteção do endereço MAC é atualizada. |

### <a name="icmp-configuration-options"></a>Opções de configuração do ICMP  

| Opção  | Descrição  |
|---|---|
| NX_DISABLE_ICMP_INFO | Definido, desativa a recolha de informações do ICMP. |
| NX_DISABLE_ICMP_RX_CHECKSUM | Desativa o cálculo de checkum do ICMP em pacotes ICMP recebidos. Esta opção é útil quando o controlador de interface de rede é capaz de verificar a sala de verificação ICMP, e a aplicação não utiliza a função de fragmentação IP. Por padrão esta opção não está definida. |
| NX_DISABLE_ICMP_TX_CHECKSUM | Desativa o cálculo de checkum do ICMP em pacotes ICMP transmitidos. Esta opção é útil quando o controlador de interface de rede é capaz de calcular a sala de verificação ICMP, e a aplicação não utiliza a função de fragmentação IP. Por padrão esta opção não está definida. |

### <a name="igmp-configuration-options"></a>Opções de configuração IGMP  

| Opção  | Descrição  |
|---|---| 
| NX_DISABLE_IGMP_INFO | Definido, desativa a recolha de informações do IGMP. |
| NX_DISABLE_IGMPV2 | Definido, desativa o suporte IGMPv2 e o NetX suporta apenas o IGMPv1. Por predefinição, esta opção não está definida e é definida em ***nx_api.h***. |
| NX_MAX_MULTICAST_GROUPS | Especifica o número máximo de grupos multicast que podem ser unidos. O valor predefinido é de 7 e é definido em ***nx_api.h** _. A aplicação pode anular o padrão definindo o valor antes de _ *_nx_api.h*_* está incluído. |

### <a name="ip-configuration-options"></a>Opções de configuração IP

| Opção  | Descrição  |
|---|---|
| NX_DISABLE_FRAGMENTATION | Definido, desativa a fragmentação ip e a lógica de remontagem. |
| NX_DISABLE_IP_INFO | Definido, desativa a recolha de informações IP. |
| NX_DISABLE_IP_RX_CHECKSUM | Definido, desativa a lógica de checkum em pacotes IP recebidos. Isto é útil se o dispositivo de rede for capaz de verificar a parte de verificação do cabeçalho IP, e a aplicação não utilizar a fragmentação IP. |
| NX_DISABLE_IP_TX_CHECKSUM | Definido, desativa a lógica de checkum em pacotes IP enviados. Isto é útil em situações em que o dispositivo de rede subjacente é capaz de gerar a caixa de verificação do cabeçalho IP, e a aplicação não utiliza fragmentação IP. |
| NX_DISABLE_LOOPBACK_INTERFACE | Definido, desativa o suporte NetX para a interface loopback. |
| NX_DISABLE_RX_SIZE_CHECKING | Definido, desativa o tamanho verificando os pacotes recebidos. |
| NX_ENABLE_IP_STATIC_ROUTING | Definido, permite o encaminhamento estático IP no qual um endereço de destino pode ser atribuído um próximo endereço de lúpulo específico. Por roteamento estático IP predefinido é desativado. |
| NX_IP_PERIODIC_RATE | Definido, especifica o número de tiques do temporizador ThreadX num segundo. O valor predefinido é derivado do símbolo ThreadX **TX_TIMER_TICKS_PER_SECOND,** que por padrão é definido para 100 (temporizador de 10ms). As aplicações devem ter cuidado ao modificar este valor, uma vez que os restantes módulos NetX derivam de **NX_IP_PERIODIC_RATE*.** |
| NX_IP_ROUTING_TABLE_SIZE | Definido, define o número máximo de entradas na tabela de encaminhamento estático IP, que é uma lista de uma interface de saída e o próximo lúpulo
endereços para um determinado endereço de destino. O valor predefinido é de 8 e é definido em ***nx_api.h.** _ Este símbolo só é utilizado se _ *NX_ENABLE_IP_STATIC_ROUTING** for definido. |

### <a name="packet-configuration-options"></a>Opções de configuração de pacotes  

| Opção  | Descrição  |
|---|---|
| NX_DISABLE_PACKET_INFO | Definido, desativa a recolha de informação da piscina de pacotes. | 
| NX_PACKET_HEADER_PAD | Definido, permite o enchimento no final do NX_PACKET bloco de controlo. O número de palavras **ULONG** a pad é definido por **NX_PACKET_HEADER_PAD_SIZE**. |
| NX_PACKET_HEADER_PAD_SIZE | Define o número de palavras **ULONG** a acolchoadas à estrutura NX_PACKET, permitindo que a área de carga útil do pacote comece no desejado
alinhamento. Esta funcionalidade é útil quando os descritores de tampão apontam diretamente para NX_PACKET área de carga útil, e a interface de rede recebe lógica ou a lógica de funcionamento da cache espera que o endereço inicial do tampão satisfaça determinados requisitos de alinhamento. Este valor só se torna válido quando **NX_PACKET_HEADER_PAD** é definido. |

### <a name="rarp-configuration-options"></a>Opções de configuração RARP  

| Opção  | Descrição  |
|---|---|
| NX_DISABLE_RARP_INFO | Definido, desativa a recolha de informações da RARP. |

### <a name="tcp-configuration-options"></a>Opções de configuração TCP

| Opção  | Descrição  |
|---|---|
| NX_DISABLE_RESET_DISCONNECT | Definido, desativa o processamento de reset durante a desconexão quando o valor de tempo limite fornecido for especificado como **NX_NO_WAIT**. |
| NX_DISABLE_TCP_INFO | Definido, desativa a recolha de informações da TCP. |
| NX_DISABLE_TCP_RX_CHECKSUM | Definido, desativa a lógica de checkum em pacotes TCP recebidos. Isto só é útil em situações em que a camada de ligação tem um processamento fiável de checkum ou CRC, ou o controlador de interface é capaz de verificar o checkum de verificação TCP em hardware. |
| NX_DISABLE_TCP_TX_CHECKSUM | Definido, desativa a lógica de checkum para o envio de pacotes TCP. Isto só é útil em situações em que o nó de rede recetor tem a lógica de checkum TCP recebida desativada ou o controlador de rede subjacente é capaz de gerar a sala de controlo TCP. |
| NX_ENABLE_TCP_KEEPALIVE | Definido, permite o temporizador de manter o TCP opcional. As definições predefinidos não estão ativadas. |
| NX_ENABLE_TCP_MSS_CHECKING | Definido, permite a verificação do MSS mínimo de pares antes de aceitar uma ligação TCP. Para utilizar esta função, o símbolo **NX_ENABLE_TCP_MSS_MINIMUM** deve ser definido. Por padrão, esta opção não está ativada. |
NX_ENABLE_TCP_WINDOW_SCALING | Permite a opção de escala de janela para aplicações TCP. Se definido, a opção de escala da janela é negociada durante a fase de ligação TCP, e a aplicação é capaz de especificar um tamanho de janela superior a 64K. A definição predefinida não está ativada (não definida). |
| NX_MAX_LISTEN_REQUESTS | Especifica o número máximo de pedidos de escuta do servidor. O valor predefinido é de 10 e é definido em ***nx_api.h** _. A aplicação pode anular o padrão definindo o valor antes de _ *_nx_api.h*_* está incluído. |
| NX_TCP_ACK_EVERY_N_PACKETS | Especifica o número de pacotes TCP a receber antes de enviar um ACK. Note se **NX_TCP_IMMEDIATE_ACK** estiver ativado mas **NX_TCP_ACK_EVERY_N_PACKETS** não, este valor é automaticamente definido para 1 para retrocompatibilidade. |
| NX_TCP_ACK_TIMER_RATE | Especifica como o número de carraças do sistema (NX_IP_PERIODIC_RATE) é dividido para calcular a taxa de temporizador para o processamento de ACK atrasado da TCP. O valor predefinido é de 5, que representa 200ms, e é definido em ***nx_tcp.h** _. A aplicação pode anular o padrão definindo o valor antes de incluir _*_nx_api.h**._ |
| NX_TCP_ENABLE_KEEPALIVE | Renomeado para **NX_ENABLE_TCP_KEEPALIVE.** Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar **NX_ENABLE_TCP_KEEPALIVE**. |
| NX_TCP_ENABLE_WINDOW_SCALING | Renomeado para **NX_ENABLE_TCP_WINDOW_SCALING.** Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar **NX_ENABLE_TCP_WINDOW_SCALING**. |
| NX_TCP_FAST_TIMER_RATE | Especifica como o número de tiques internos NetX (NX_IP_PERIODIC_RATE) é dividido para calcular a taxa de temporizador TCP rápida. O temporizador rápido TCP é utilizado para conduzir os vários temporizadores TCP, incluindo o temporizador ACK atrasado. O valor predefinido é de 10, o que representa 100ms assumindo que o temporizador ThreadX está a funcionar a 10ms. Este valor é definido em ***nx_tcp.h** _. A aplicação pode anular o padrão definindo o valor antes de incluir _*_nx_api.h**._ |
| NX_TCP_IMMEDIATE_ACK | Definido, permite o processamento de resposta ACK imediato opcional da TCP. Definir este símbolo equivale a definir **NX_TCP_ACK_EVERY_N_PACKETS** ser 1. |
| NX_TCP_KEEPALIVE_INITIAL | Especifica o número de segundos de inatividade antes que o temporizador de manter seja ativado. O valor predefinido é de 7200, que representa 2 horas, e é definido em ***nx_tcp.h** _. A aplicação pode anular o padrão definindo o valor antes de incluir _*_nx_api.h**._ |
| NX_TCP_KEEPALIVE_RETRIES | Especifica quantas recaídas de manter são permitidas antes da ligação ser considerada quebrada. O valor predefinido é de 10, que representa 10 retrações, e é definido em ***nx_tcp.h** _. A aplicação pode anular o padrão definindo o valor antes de _ *_nx_api.h*_* está incluído. |
| NX_TCP_KEEPALIVE_RETRY | Especifica o número de segundos entre as retrígios do temporizador de manter-se, assumindo que o outro lado da ligação não está a responder. O valor predefinido é de 75, o que representa 75 segundos entre as retrações, e é definido em ***nx_tcp.h** _. A aplicação pode anular o padrão definindo o valor antes de _ *_nx_api.h*_* está incluído. |
| NX_TCP_MAX_OUT_OF_ORDER_PACKETS | Símbolo que define o número máximo de pacotes TCP fora de encomenda que podem ser mantidos na tomada TCP receber fila. Este símbolo pode ser utilizado para limitar o número de pacotes em fila na tomada de receção TCP, evitando que a piscina do pacote seja esfomeada. Por predefinição, este símbolo não é definido, pelo que não existe limite para o número de pacotes fora de encomenda que estão a ser utilizados na tomada TCP. |
| NX_TCP_MAXIMUM_RETRIES | Especifica quantos dados transmitem as retrótaras antes da ligação ser considerada quebrada. O valor predefinido é de 10, que representa 10 retrações, e é definido em ***nx_tcp.h** _. A aplicação pode anular o padrão definindo o valor antes de incluir _*_nx_api.h**._ |
| NX_TCP_MAXIMUM_TX_QUEUE | Especifica a profundidade máxima da fila de transmissão TCP antes de os pedidos de envio de TCP serem suspensos ou rejeitados. O valor predefinido é de 20, o que significa que um máximo de 20 pacotes pode estar na fila de transmissão a qualquer momento. Os pacotes de notas permanecem na fila de transmissão até que um ACK que cubra alguns ou todos os dados do pacote seja recebido do outro lado da ligação. Esta constante é definida em ***nx_tcp.h** _. A aplicação pode anular o padrão definindo o valor antes de incluir _*_nx_api.h**._ |
| X_TCP_MSS_CHECKING_ENABLED | Renomeado para **NX_ENABLE_TCP_MSS_CHECKING.** Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar **NX_ENABLE_TCP_MSS_CHECKING**. |
| NX_TCP_MSS_MINIMUM | Símbolo que define o valor mínimo de MSS que o módulo TCP NetX aceita. Esta funcionalidade é ativada por **NX_ENABLE_TCP_MSS_CHECK** |
| NX_TCP_RETRY_SHIFT | Especifica como o período de tempo de retransmissão muda entre as retrósias. Se este valor for 0, o tempo limite inicial de retransmissão é o mesmo que os intervalos subsequentes de retransmissão. Se este valor for 1, cada retransmissão sucessiva é o dobro do tempo. Se este valor for 2, cada tempo de retransmissão subsequente é quatro vezes maior. O valor predefinido é 0 e é definido em ***nx_tcp.h** _. A aplicação pode anular o padrão definindo o valor antes de incluir _*_nx_api.h**._ |
| NX_TCP_TRANSMIT_TIMER_RATE| Especifica como o número de carraças do sistema **NX_IP_PERIODIC_RATE**) é dividido para calcular a taxa de temporizador para o processamento de retíria de transmissão TCP. O valor predefinido é de 1, que representa 1 segundo, e é definido em **_nx_tcp.h_*_. A aplicação pode anular o padrão definindo o valor antes de incluir _*_nx_api.h_**. |

### <a name="udp-configuration-options"></a>Opções de configuração do UDP
| Opção  | Descrição  |
|---|---|
| NX_DISABLE_UDP_INFO | Definido, desativa a recolha de informações da UDP. |
| NX_DISABLE_UDP_RX_CHECKSUM | Definido, desativa o cálculo de verificação da UDP em pacotes de UDP. Isto é útil se o controlador de interface de rede for capaz de verificar a parte de verificação do cabeçalho UDP no hardware, e a aplicação não ativa a lógica de fragmentação IP. |
| NX_DISABLE_UDP_TX_CHECKSUM | Definido, desativa a computação de verificação da UDP em pacotes UDP de saída. Isto é útil se o controlador de interface de rede for capaz de calcular a verificação do cabeçalho UDP e inserir o valor na cabeça IP antes de transmitir os dados, e a aplicação não ativa a lógica de fragmentação IP. |

## <a name="netx-version-id"></a>ID da versão NetX

A versão atual do NetX está disponível tanto para o utilizador como para o software da aplicação durante o tempo de funcionamento. O programador pode obter a versão NetX a partir do ficheiro **nx_port.h.** Além disso, este ficheiro contém um histórico de versão da porta correspondente. O software de aplicação pode obter a versão NetX examinando o **_nx_version_id** global de cadeias em **_nx_port.h_**.  

O software de aplicação também pode obter informações de libertação das constantes abaixo mostradas, que são definidas em ***nx_api.h**.*

Estas constantes identificam a versão atual do produto pelo nome e a versão principal e menor do produto.

```c
#define EL_PRODUCT_NETX

#define NETX_MAJOR_VERSION

#define NETX_MINOR_VERSION
```