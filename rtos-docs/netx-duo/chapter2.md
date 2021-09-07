---
title: Capítulo 2 - Instalação e Utilização do Azure RTOS NetX Duo
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização da pilha de rede de alto desempenho Azure RTOS NetX Duo.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 08697d7155c79a7850f834af2e7e88f461d48188
ms.sourcegitcommit: 20a136b06a25e31bbde718b4d12a03ddd8db9051
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/07/2021
ms.locfileid: "123552352"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo"></a>Capítulo 2 - Instalação e Utilização do Azure RTOS NetX Duo

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização da pilha de rede de alto desempenho Azure RTOS NetX Duo, incluindo os seguintes: 

## <a name="host-considerations"></a>Considerações de Anfitrião

O desenvolvimento incorporado é geralmente realizado em computadores de Windows ou Linux (Unix). Após a compilação da aplicação, ligada e o executável é gerado no anfitrião, é descarregado para o hardware alvo para execução.

Normalmente, o download do alvo é feito a partir do depurar da ferramenta de desenvolvimento. Após o download, o depurante é responsável por fornecer controlo de execução de alvos (ir, parar, quebrar, etc.) bem como aceder aos registos de memória e processador.

A maioria dos depurares de ferramentas de desenvolvimento comunicam com o hardware-alvo através de ligações de depuro on-chip (TOC), tais como JTAG (IEEE 1149.1) e Modo de Depuramento de Fundo (BDM). Os debuggers também comunicam com o hardware alvo através de ligações In-Circuit Emulation (ICE). As ligações OCD e ICE fornecem soluções robustas com uma intrusão mínima no software residente alvo.

Quanto aos recursos utilizados no anfitrião, o código fonte do NetX Duo é entregue em formato ASCII e requer aproximadamente 1 Mbytes de espaço no disco rígido do computador anfitrião.

## <a name="target-considerations"></a>Considerações-alvo

NetX Duo requer entre 5 KBytes e 45 KBytes de Read-Only Memory (ROM) no alvo. São necessários mais 1 a 5KBytes da Memória de Acesso Aleatório (RAM) do alvo para a pilha de fios NetX Duo e outras estruturas de dados globais.

Além disso, o NetX Duo requer a utilização de dois objetos temporizadores ThreadX e um objeto mutex ThreadX. Estas instalações são utilizadas para necessidades de processamento periódica e proteção de fios dentro da pilha de protocolo NetX Duo.

## <a name="product-distribution"></a>Distribuição de Produtos

O Azure RTOS NetX Duo pode ser obtido a partir do nosso repositório de código fonte pública em <https://github.com/azure-rtos/netxduo/> .

Segue-se uma lista de vários ficheiros importantes no repositório:

**nx_api.h**  
Ficheiro de cabeçalho C contendo todos os equacionares do sistema, estruturas de dados e protótipos de serviço.

**nx_port.h** Ficheiro de cabeçalho C contendo todas as definições e estruturas específicas de dados de desenvolvimento e de destino. 

**demo_netx.c** Ficheiro C contendo um pequeno pedido de demonstração.

**nx.a (ou nx.lib)**  
Versão binária da biblioteca NetX C que é distribuída com o pacote padrão.

## <a name="netx-duo-installation"></a>Instalação NetX Duo

O NetX Duo é instalado clonando o repositório GitHub à sua máquina local. Segue-se a sintaxe típica para a criação de um clone do repositório NetX Duo no seu PC:

```c
    git clone https://github.com/azure-rtos/netxduo
```

Em alternativa, pode descarregar uma cópia do repositório utilizando o botão de descarregamento na página principal GitHub.

Você também encontrará instruções para a construção da biblioteca NetX Duo na primeira página do repositório online.

> [!IMPORTANT]
> *O software de aplicação precisa de acesso ao ficheiro da biblioteca NetX Duo (geralmente **nx.a** ou **nx.lib)** e o C inclui ficheiros **nx_api.h e nx_port.h**. Isto é conseguido quer estabelecendo o caminho adequado para as ferramentas de desenvolvimento, quer copiando estes ficheiros para a área de desenvolvimento de aplicações.*

## <a name="using-netx-duo"></a>Usando a Dupla NetX

Usar o NetX Duo é fácil. Basicamente, o código de aplicação deve incluir ***nx_api.h** _ durante a compilação e ligação com a biblioteca NetX Duo _*_nx.a_*_ (ou _ *_nx.lib_*)*.

Seguem-se os quatro passos fáceis necessários para a construção de uma aplicação NetX Duo:

| Passo  | Description  |
|---|---|
|Passo &nbsp; 1: |Inclua o ficheiro ***nx_api.h*** em todos os ficheiros de aplicações que utilizam serviços NetX Duo ou estruturas de dados.|
|Passo &nbsp; 2: |Inicialize o sistema NetX Duo chamando ***nx_system_initialize** _ da função _ *_tx_application_define_** ou de um fio de aplicação.|
|Passo &nbsp; 3: |Crie uma instância IP, ative o Protocolo de Resolução de Endereços (ARP), se necessário, e quaisquer tomadas após ***nx_system_initialize*** é chamada.|
|Passo &nbsp; 4: |Compilar fonte de aplicação e ligar-se com a biblioteca de tempo de execução NetX Duo ***nx.a** _ (ou _*_nx.lib_**). A imagem resultante pode ser descarregada para o alvo e executada!|

## <a name="troubleshooting"></a>Resolução de problemas

Cada porta NetX Duo é entregue com uma ou mais demonstrações que executam numa rede real ou através de um controlador de rede simulado. É sempre uma boa ideia pôr o sistema de demonstração a funcionar primeiro.

Se o sistema de demonstração não funcionar corretamente, efetuar as seguintes operações para reduzir o problema:

1. Determina quanto da demonstração está a decorrer.
2. Aumente os tamanhos das pilhas em quaisquer novos fios de aplicação.
3. Recompilar a biblioteca NetX Duo com as opções de depurg apropriadas listadas na secção de opções de configuração.
4. Examine a estrutura NX_IP para ver se os pacotes estão a ser enviados ou recebidos.
5. Examine a piscina de pacotes predefinidos para ver se existem pacotes disponíveis.
6. Certifique-se de que o controlador de rede está a fornecer pacotes ARP e IP com os seus cabeçalhos em limites de 4 bytes para aplicações que requerem conectividade IPv4 ou IPv6.
7. Contornar temporariamente quaisquer alterações recentes para ver se o problema desaparece ou muda. Estas informações devem revelar-se úteis aos engenheiros de suporte da Microsoft.

Siga os procedimentos descritos no "What We Need From You" na página 12 para enviar as informações recolhidas a partir das etapas de resolução de problemas.

## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração ao construir a biblioteca NetX Duo e a aplicação usando o NetX Duo. As opções de configuração podem ser definidas na fonte de aplicação, na linha de comando ou dentro do ***ficheiro nx_user.h,*** salvo especificação em contrário.

> [!NOTE]
> *As opções definidas em **nx_user.h** são aplicadas apenas se a aplicação e a biblioteca NetX Duo forem construídas com* **NX_INCLUDE_USER_DEFINE_FILE** definidas.*

As secções seguintes listam as opções de configuração disponíveis no NetX Duo. As opções gerais aplicáveis tanto ao IPv4 como ao IPv6 são listadas em primeiro lugar, seguidas por opções específicas do IPv6.

### <a name="system-configuration-options"></a>Opções de configuração do sistema

| Opção  | Descrição  |
|---|---|
| NX_ASSERT_FAIL    | Símbolo que define a declaração de depurar para usar quando uma afirmação falha.                               |
| NX_DEBUG           | Definido, permite a informação opcional de depurar depuragem disponível do controlador de rede RAM Ethernet. |
| NX_DEBUG_PACKET   | Definido, permite o despejo opcional de pacotes de depurativo disponível no controlador da rede RAM Ethernet.      |
| NX_DISABLE_ASSERT | Definido, desativa as verificações ASSERT no código fonte. Por padrão esta opção não está definida.            |
|NX_DISABLE_ERROR_CHECKING | Definido, remove o erro básico netx duo verificando a API e melhora o desempenho. Os códigos de devolução da API não afetados pela verificação de erros incapacitantes estão listados em tipo de letra arrojado na definição API. Esta definição é normalmente utilizada após a depurada da aplicação e a sua utilização melhora o desempenho e diminui o tamanho do código.|
|NX_DRIVER_DEFERRED_PROCESSING | Definido, permite o manuseamento de pacotes de controlador de rede diferido. Isto permite ao controlador de rede colocar um pacote na instância IP e ter a verdadeira rotina de processamento chamada a partir do fio de ajuda ip interno netx duo.|
|NX_DUAL_PACKET_POOL_ENABLE | Renomeado para ***NX_ENABLE_DUAL_PACKET_POOL** _. Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar _*_NX_ENABLE_DUAL_PACKET_POOL_**.|
|NX_ENABLE_DUAL_PACKET_POOL | Definido, permite que a pilha use duas piscinas de pacotes, uma com grande tamanho de carga útil e outra com menor tamanho de carga útil. Por padrão, esta opção não está ativada.|
|NX_ENABLE_EXTENDED_NOTIFY_SUPPORT| Definido, permite mais ganchos de retorno na pilha. Estas funções de retorno são utilizadas pela camada de invólucro BSD. Por padrão esta opção não está definida.|
|NX_ENABLE_INTERFACE_CAPABILITY| Definido, permite ao controlador do dispositivo de interface especificar informações extra de capacidade, tais como checkum off-loading. Por padrão esta opção não está definida.|
|NX_ENABLE_SOURCE_ADDRESS_CHECK| Definido, permite verificar o endereço de origem do pacote de entrada. Por predefinição, esta opção é desativada.|
| NX_IPSEC_ENABLE  | Definida, permite que a biblioteca NetX Duo suporte operações IPsec. Esta funcionalidade requer o módulo IPsec NetX Duo opcional. Por padrão, esta funcionalidade não está ativada.            |
| NX_LITTLE_ENDIAN | Definido, executa a troca de byte necessária em pequenos ambientes endianos para garantir que os cabeçalhos do protocolo estão em formato endiano adequado. Note que o padrão é normalmente configurado em ***nx_port.h***.|
|NX_MAX_PHYSICAL_INTERFACES | Especifica o número total de interfaces de rede física no dispositivo. O valor predefinido é 1 e é definido em ***nx_api.h;*** um dispositivo deve ter pelo menos uma interface física. Note que isto não inclui a interface loopback.|
| NX_NAT_ENABLE | Definido, NetX Duo é construído com processo NAT. Por padrão esta opção não está definida.|
| NX_PHYSICAL_HEADER  | Especifica o tamanho em bytes do cabeçalho físico da armação. O valor predefinido é de 16 (baseado num quadro típico de 14 bytes Ethernet alinhado com limite de 32 bits) e é definido em ***nx_api.h** _. A aplicação pode anular o padrão definindo o valor antes _*_de nx_api.h_*_ ser incluído, como em _ *_nx_user.h_*.* |
| NX_PHYSICAL_TRAILER | Especifica o tamanho em bytes do reboque de pacote físico e é normalmente usado para reservar armazenamento para coisas como CRCs Ethernet, etc. O valor predefinido é de 4 e é definido em ***nx_api.h***.|

### <a name="arp-configuration-options"></a>Opções de configuração ARP

| Opção  | Descrição  |
|---|---|
|NX_ARP_DEFEND_BY_REPLY | Definido, permite que a NetX Duo defenda o seu endereço IP enviando uma resposta ARP.|
|NX_ARP_DEFEND_INTERVAL| Define o intervalo, em segundos, o módulo ARP envia o próximo pacote de defesa em resposta a uma mensagem ARP que indica um endereço em conflito.|
|NX_ARP_DISABLE_AUTO_ARP_ENTRY|  Renomeado para ***NX_DISABLE_ARP_AUTO_ENTRY** _. Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar _*_NX_DISABLE_ARP_AUTO_ENTRY_**.|
|NX_ARP_EXPIRATION_RATE| Especifica o número de segundos de entradas ARP permanecem válidas. O valor predefinido de zero desativa a expiração ou o envelhecimento das entradas ARP e é definido em ***nx_api.h** _. A aplicação pode anular o padrão definindo o valor antes de _ *_nx_api.h*_* está incluído.|
|NX_ARP_MAC_CHANGE_NOTIFICATION_ENABLE | Renomeado para ***NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION** _. Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar _*_NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION_**.|
|NX_ARP_MAX_QUEUE_DEPTH | Especifica o número máximo de pacotes que podem ser em fila enquanto se aguarda uma resposta ARP. O valor predefinido é de 4 e é definido em ***nx_api.h***.|
|NX_ARP_MAXIMUM_RETRIES | Especifica o número máximo de retrações ARP feitas sem uma resposta ARP. O valor predefinido é de 18 e é definido em ***nx_api.h** _. A aplicação pode anular o padrão definindo o valor antes de _ *_nx_api.h*_* está incluído.|
|NX_ARP_UPDATE_RATE | Especifica o número de segundos entre as retríss em dia do ARP. O valor predefinido é de 10, o que representa 10 segundos, e é definido em ***nx_api.h** _. A aplicação pode anular o padrão definindo o valor antes de _ *_nx_api.h*_* está incluído.|
|NX_DISABLE_ARP_AUTO_ENTRY | Definido, desativa a entrada de informações de pedido de ARP na cache ARP.|
|NX_DISABLE_ARP_INFO | Definido, desativa a recolha de informações ARP.|
|NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION| Definido, permite que a ARP invoque uma função de notificação de chamada na deteção do endereço MAC é atualizada.|

### <a name="icmp-configuration-options"></a>Opções de configuração do ICMP

| Opção  | Descrição  |
|---|---|
|NX_DISABLE_ICMP_INFO| Definido, desativa a recolha de informações do ICMP.|
|NX_DISABLE_ICMP_RX_CHECKSUM| Definido, desativa tanto o cálculo de verificação ICMPv4 como o ICMPv6 em pacotes ICMP recebidos. Esta opção é útil quando o controlador de interface de rede é capaz de verificar a sala de verificação ICMPv4 e ICMPv6, e a aplicação não utiliza a função de fragmentação IP ou a funcionalidade IPsec. Por padrão esta opção não está definida.|
|NX_DISABLE_ICMP_TX_CHECKSUM | Definido, desativa tanto o cálculo de verificação ICMPv4 como o ICMPv6 em pacotes ICMP transmitidos. Esta opção é útil quando o controlador de interface de rede é capaz de calcular o checkum ICMPv4 e ICMPv6,
e a aplicação não utiliza a função de fragmentação IP ou iPsec. Por padrão esta opção não está definida.|
|NX_DISABLE_ICMPV4_ERROR_MESSAGE | Definido, o NetX Duo não envia Mensagens de Erro ICMPv4 em resposta a condições de erro tais como cabeçalho IPv4 indevidamente formatado. Por padrão esta opção não está definida.|
|NX_DISABLE_ICMPV4_RX_CHECKSUM | Definido, desativa o cálculo de checkum ICMPv4 em pacotes ICMP recebidos. Esta opção é definida automaticamente se ***NX_DISABLE_ICMP_RX_CHECKSUM*** for definida. Por padrão esta opção não está definida.|
|NX_DISABLE_ICMPv4_RX_CHECKSUM | Renomeado para ***NX_DISABLE_ICMPV4_RX_CHECKSUM** _. Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar _*_NX_DISABLE_ICMPV4_RX_CHECKSUM_**.|
|NX_DISABLE_ICMPV4_TX_CHECKSUM | Definido, desativa o cálculo de checkum ICMPv4 em pacotes ICMP transmitidos. Esta opção é definida automaticamente se ***NX_DISABLE_ICMP_TX_CHECKSUM*** for definida. Por padrão esta opção não está definida.|
|NX_DISABLE_ICMPv4_TX_CHECKSUM | Renomeado para ***NX_DISABLE_ICMPV4_TX_CHECKSUM** _.</br>Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar _*_NX_DISABLE_ICMPV4_TX_CHECKSUM_**.|
|NX_ENABLE_ICMP_ADDRESS_CHECK | Definido, o endereço de destino do pacote ICMP é verificado. A predefinição é Desativado. Um Pedido de Eco ICMP destinado a uma transmissão IP ou endereço multicast IP será descartado silenciosamente.|

### <a name="igmp-configuration-options"></a>Opções de configuração IGMP

| Opção  | Descrição  |
|---|---|
|NX_DISABLE_IGMP_INFO | Definido, desativa a recolha de informações do IGMP.|
|NX_DISABLE_IGMPV2 | Definido, desativa o suporte IGMPv2 e o NetX Duo suporta apenas o IGMPv1. Por predefinição, esta opção não está definida e é definida em ***nx_api.h***.|
|NX_MAX_MULTICAST_GROUPS | Especifica o número máximo de grupos multicast que podem ser unidos. O valor predefinido é de 7 e é definido em ***nx_api.h** _. A aplicação pode anular o padrão definindo o valor antes de _ *_nx_api.h*_* está incluído.|

### <a name="ip-configuration-options"></a>Opções de configuração IP

| Opção  | Descrição  |
|---|---|
|NX_DISABLE_FRAGMENTATION | Definido, desativa a fragmentação do IPv4 e do IPv6 e a lógica de remontagem.|
| NX_DISABLE_IPV4     | Definido, desativa a funcionalidade IPv4. Esta opção pode ser usada para construir o NetX Duo apenas para suupportar o IPv6. Por padrão esta opção não está definida. |
| NX_DISABLE_IP_INFO | Definido, desativa a recolha de informações IP.|
|NX_DISABLE_IP_RX_CHECKSUM | Definido, desativa a lógica de checkum em pacotes IPv4 recebidos. Isto é útil se o dispositivo de rede for capaz de verificar a sala de verificação IPv4, e a aplicação não espera usar fragmentação IP ou IPsec.|
|NX_DISABLE_IP_TX_CHECKSUM | Definido, desativa a lógica de checkum nos pacotes IPv4 enviados. Isto é útil em situações em que o dispositivo de rede subjacente é capaz de gerar a sala de verificação do cabeçalho IPv4, e a aplicação não espera usar fragmentação IP ou IPsec.|
|NX_DISABLE_LOOPBACK_INTERFACE | Definido, desativa o suporte NetX Duo para a interface loopback.|
|NX_DISABLE_RX_SIZE_CHECKING | Definido, desativa o tamanho verificando os pacotes recebidos.|
|NX_ENABLE_IP_RAW_PACKET_FILTER | Definido, permite que o pacote cru IP receba a funcionalidade do filtro. As aplicações que requerem mais controlo sobre o tipo de pacotes IP crus a receber podem utilizar esta funcionalidade. A função de filtro de pacotes crus IP também suporta o funcionamento da tomada bruta na camada de compatibilidade BSD. Por padrão esta opção não está definida.|
|NX_ENABLE_IP_STATIC_ROUTING | Definido, permite o encaminhamento estático IPv4 no qual um endereço de destino pode ser atribuído um próximo endereço de lúpulo específico. Por defeito, o encaminhamento estático IPv4 é desativado.|
|NX_FRAGMENT_IMMEDIATE_ASSEMBLY | Definido, permite que a lógica de montagem IPv4 e IPv6 execute imediatamente após receber um fragmento de IP. Por padrão esta opção não está definida.|
|NX_IP_MAX_REASSEMBLY_TIME | Símbolo que controla o tempo máximo permitido para remontar fragmento iPv4 e fragmento IPv6. Note o valor definido aqui sobreapor-se ***NX_IPV4_MAX_REASSEMBLY_TIME** _ e _*_NX_IPV6_MAX_REASSEMBLY_TIME_**.|
|NX_IP_PERIODIC_RATE | Definido, especifica o número de tiques do temporizador ThreadX num segundo. O valor predefinido é derivado do símbolo ThreadX ***TX_TIMER_TICKS_PER_SECOND,** _ que por padrão é definido para 100 (temporizador de 10ms). As aplicações devem ter cuidado ao modificar este valor, uma vez que os restantes módulos NetX Duo derivam informações de tempo de _ *_NX_IP_PERIODIC_RATE_.**|
|NX_IP_RAW_MAX_QUEUE_DEPTH | O símbolo que controla o número de pacotes IP crus pode ser colocado na fila de receção do pacote bruto. Por padrão o valor é definido para 20.| 
|NX_IP_ROUTING_TABLE_SIZE | Definido, define o número máximo de entradas na tabela de encaminhamento estático IPv4, que é uma lista de uma interface de saída e os seguintes endereços de lúpulo para um determinado endereço de destino. O valor predefinido é de 8 e é definido em ***nx_api.h.** _ Este símbolo só é utilizado se _ *_NX_ENABLE_IP_STATIC_ROUTING_** for definido.|
|NX_IPV4_MAX_REASSEMBLY_TIME | Símbolo que controla o tempo máximo permitido para remontar o fragmento IPv4. Note o valor definido em NX_IP_MAX_REASSEMBLY_TIME substitui este valor.|
|NX_ENABLE_TCPIP_OFFLOAD | Símbolo que permite a função de descarregamento TCP/IP. Note NX_ENABLE_INTERFACE_CAPABILITY devem ser definidos para ativar esta função.|

### <a name="packet-configuration-options"></a>Opções de configuração de pacotes

| Opção  | Descrição  |
|---|---|
|NX_DISABLE_PACKET_CHAIN | Definido, desativa a lógica da cadeia de pacotes. Por defeito, isto não está definido.|
|NX_DISABLE_PACKET_INFO | Definido, desativa a recolha de informação da piscina de pacotes.|
|NX_ENABLE_LOW_WATERMARK | Definido, permite a funcionalidade de baixa marca de água da piscina netx duo. A aplicação define baixo valor de marca de água. Ao receber pacotes TCP, se a marca de água baixa da piscina de pacotes for alcançada, a NetX Duo descarta silenciosamente o pacote libertando-o, evitando que a piscina do pacote seja de fome. Por padrão, esta funcionalidade não está ativada.|
|NX_ENABLE_PACKET_DEBUG_INFO | Definido, registos dedesorça informações.|
|NX_PACKET_ALIGNMENT | Definido, especifica o requisito de alinhamento, em bytes, para o endereço inicial da área de carga do pacote. Esta opção deprecia ***NX_PACKET_HEADER_PAD** _ e _*_NX_PACKET_HEADER_PAD_SIZE_**. Por predefinição, esta opção é definida como 4, alinhando o endereço inicial da área de carga útil 4 byte.|
|NX_PACKET_HEADER_PAD | Definido, permite o enchimento no final do NX_PACKET bloco de controlo. O número de palavras ULONG a pad é definido por ***NX_PACKET_HEADER_PAD_SIZE** _. Note que esta opção é amortizada por _*_NX_PACKET_ALIGNMENT_**.|
|NX_PACKET_HEADER_PAD_SIZE | Define o número de palavras ULONG a acolchoadas à estrutura NX_PACKET, permitindo que a área de carga do pacote comece no alinhamento pretendido. Esta funcionalidade é útil quando os descritores de tampão apontam diretamente para NX_PACKET área de carga útil, e a interface de rede recebe lógica ou a lógica de funcionamento da cache espera que o endereço inicial do tampão satisfaça determinados requisitos de alinhamento. Este valor só se torna válido quando ***NX_PACKET_HEADER_PAD** _ é definido. Note que esta opção é depreciada por _*_NX_PACKET_ALIGNMENT_**.|

### <a name="rarp-configuration-options"></a>Opções de configuração RARP

| Opção  | Descrição  |
|---|---|
|NX_DISABLE_RARP_INFO | Definido, desativa a recolha de informações da RARP.|

### <a name="tcp-configuration-options"></a>Opções de configuração TCP

| Opção | Descrição |
|---|---|
|NX_DISABLE_RESET_DISCONNECT | Definido, desativa o processamento de reset durante a desconexão quando o valor de tempo limite fornecido for especificado como ***NX_NO_WAIT***.|
|NX_DISABLE_TCP_INFO | Definido, desativa a recolha de informações da TCP.|
|NX_DISABLE_TCP_RX_CHECKSUM | Definido, desativa a lógica de checkum em pacotes TCP recebidos. Isto só é útil em situações em que a camada de ligação tem um processamento fiável de checkum ou CRC, ou o controlador de interface é capaz de verificar a sala de verificação TCP em hardware, e a aplicação não utiliza O IPsec.|
|NX_DISABLE_TCP_TX_CHECKSUM | Definido, desativa a lógica de checkum para o envio de pacotes TCP. Isto só é útil em situações em que o nó de rede recetor recebeu a lógica de checkum TCP desativada ou o controlador de rede subjacente é capaz de gerar a sala de verificação TCP, e a aplicação não utiliza o IPsec.|
|NX_ENABLE_TCP_KEEPALIVE | Definido, permite o temporizador de manter o TCP opcional. As definições predefinidos não estão ativadas.|
|NX_ENABLE_TCP_MSS_CHECK | Definido, permite a verificação do MSS mínimo de pares antes de aceitar uma ligação TCP. Para utilizar esta função, o símbolo ***NX_ENABLE_TCP_MSS_MINIMUM*** deve ser definido. Por padrão, esta opção não está ativada.|
|NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY| Definido, permite que a aplicação instale uma função de retorno que é invocada quando a profundidade da fila de transmissão TCP já não está no valor máximo. Esta chamada serve como indicação de que a tomada TCP está pronta para transmitir mais dados. Por padrão, esta opção não está ativada.|
|NX_ENABLE_TCP_WINDOW_SCALING | Permite a opção de escala de janela para aplicações TCP. Se definido, a opção de escala de janela é negociada durante a fase de ligação TCP, e a aplicação é capaz de especificar um tamanho de janela superior a 64K. A definição predefinida não está ativada (não definida).|
|NX_MAX_LISTEN_REQUESTS | Especifica o número máximo de pedidos de escuta do servidor. O valor predefinido é de 10 e é definido em ***nx_api.h** _. A aplicação pode anular o padrão definindo o valor antes de _ *_nx_api.h*_* está incluído.|
|NX_TCP_ACK_EVERY_N_PACKETS | Especifica o número de pacotes TCP a receber antes de enviar um ACK. Note se ***NX_TCP_IMMEDIATE_ACK** _ estiver ativado mas _ *_NX_TCP_ACK_EVERY_N_PACKETS_** não é, este valor é automaticamente definido para 1 para retrocompatibilidade.|
|NX_TCP_ACK_TIMER_RATE | Especifica como o número de carraças do sistema (NX_IP_PERIODIC_RATE) é dividido para calcular a taxa de temporizador para o processamento de ACK atrasado da TCP. O valor predefinido é de 5, que representa 200ms, e é definido em ***nx_tcp.h** _. A aplicação pode anular o padrão definindo o valor antes de _ *_nx_api.h*_* está incluído.|
|NX_TCP_ENABLE_KEEPALIVE | Renomeado para ***NX_ENABLE_TCP_KEEPALIVE** _. Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar _*_NX_ENABLE_TCP_KEEPALIVE_**.|
|NX_TCP_ENABLE_MSS_CHECK | Renomeado para ***NX_ENABLE_TCP_MSS_CHECK** _. Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar _ *_NX_ENABLE_TCP_MSS_CHECK._**|
|NX_TCP_ENABLE_WINDOW_SCALING | Renomeado para ***NX_ENABLE_TCP_WINDOW_SCALING** _. Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar _*_NX_ENABLE_TCP_WINDOW_SCALING_**.|
|NX_TCP_FAST_TIMER_RATE | Especifica como o número de tiques internos NetX Duo (NX_IP_PERIODIC_RATE) é dividido para calcular a taxa de temporizador rápido TCP. O temporizador rápido TCP é utilizado para conduzir os vários temporizadores TCP, incluindo o temporizador ACK atrasado. O valor predefinido é de 10, o que representa 100ms assumindo que o temporizador ThreadX está a funcionar a 10ms. Este valor é definido em ***nx_tcp.h** _. A aplicação pode anular o padrão definindo o valor antes de _ *_nx_api.h*_* está incluído.|
|NX_TCP_IMMEDIATE_ACK| Definido, permite o processamento de resposta ACK imediato opcional da TCP. Definir este símbolo equivale a definir  ***NX_TCP_ACK_EVERY_N_PACKETS*** ser 1.|
|NX_TCP_KEEPALIVE_INITIAL | Especifica o número de segundos de inatividade antes que o temporizador de manter seja ativado. O valor predefinido é de 7200, que representa 2 horas, e é definido em ***nx_tcp.h** _. A aplicação pode anular o padrão definindo o valor antes de _ *_nx_api.h*_* está incluído.|
|NX_TCP_KEEPALIVE_RETRIES | Especifica quantas recaídas de manter são permitidas antes da ligação ser considerada quebrada. O valor predefinido é de 10, que representa 10 retrações, e é definido em ***nx_tcp.h** _. A aplicação pode anular o padrão definindo o valor antes de _ *_nx_api.h*_* está incluído.|
|NX_TCP_KEEPALIVE_RETRY | Especifica o número de segundos entre as retrígios do temporizador de manter-se, assumindo que o outro lado da ligação não está a responder. O valor predefinido é de 75, o que representa 75 segundos entre as retrações, e é definido em ***nx_tcp.h** _. A aplicação pode anular o padrão definindo o valor antes de _ *_nx_api.h*_* está incluído.|
|NX_TCP_MAX_OUT_OF_ORDER_PACKETS | O símbolo que define o número máximo de pacotes TCP fora de serviço pode ser mantido na fila de receção da tomada TCP. Este símbolo pode ser utilizado para limitar o número de pacotes em fila na tomada de receção TCP, evitando que a piscina do pacote seja esfomeada. Por predefinição, este símbolo não é definido, pelo que não existe limite para o número de pacotes fora de encomenda que estão a ser utilizados na tomada TCP.|
|NX_TCP_MAXIMUM_RETRIES | Especifica quantos dados transmitem as retrótaras antes da ligação ser considerada quebrada. O valor predefinido é de 10, que representa 10 retrações, e é definido em ***nx_tcp.h** _. A aplicação pode anular o padrão definindo o valor antes de _ *_nx_api.h*_* está incluído.|
|NX_TCP_MAXIMUM_RX_QUEUE | Símbolo que define a fila máxima de receção para tomadas TCP. Esta funcionalidade é ativada por ***NX_ENABLE_LOW_WATERMARK***.|
|NX_TCP_MAXIMUM_TX_QUEUE | Especifica a profundidade máxima da fila de transmissão TCP antes de os pedidos de envio de TCP serem suspensos ou rejeitados. O valor predefinido é de 20, o que significa que um máximo de 20 pacotes pode estar na fila de transmissão a qualquer momento. Os pacotes de notas permanecem na fila de transmissão até que um ACK que cubra alguns ou todos os dados do pacote seja recebido do outro lado da ligação. Esta constante é definida em ***nx_tcp.h** _. A aplicação pode anular o padrão definindo o valor antes de _ *_nx_api.h*_* está incluído.|
|NX_TCP_MSS_MINIMUM | Símbolo que define o valor mínimo de MSS NetX Duo TCP aceita. Esta funcionalidade é ativada por ***NX_ENABLE_TCP_MSS_CHECK***.|
|NX_TCP_QUEUE_DEPTH_UPDATE_NOTIFY_ENABLE | Renomeado para ***NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY** _. Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar _*_NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY_**.|
|NX_TCP_RETRY_SHIFT | Especifica como o período de tempo de retransmissão muda entre as retrósias. Se este valor for 0, o tempo limite inicial de retransmissão é o mesmo que os intervalos subsequentes de retransmissão. Se este valor for 1, cada retransmissão sucessiva é o dobro do tempo. Se este valor for 2, cada tempo de retransmissão subsequente é quatro vezes maior. O valor predefinido é 0 e é definido em ***nx_tcp.h** _. A aplicação pode anular o padrão definindo o valor antes de _ *_nx_api.h*_* está incluído.|
|NX_TCP_TRANSMIT_TIMER_RATE | Especifica como o número de carraças do sistema (***NX_IP_PERIODIC_RATE** _) é dividido para calcular a taxa de temporizador para o processamento de retíria de transmissão TCP. O valor predefinido é de 1, que representa 1 segundo, e é definido em _*_nx_tcp.h_*_. A aplicação pode anular o padrão definindo o valor antes de _ *_nx_api.h*_* está incluído.|

### <a name="udp-configuration-options"></a>Opções de configuração do UDP

| Opção  | Descrição  |
|---|---|
|NX_DISABLE_UDP_INFO | Definido, desativa a recolha de informações da UDP.|
|NX_DISABLE_UDP_RX_CHECKSUM | Definido, desativa o cálculo de verificação da UDP em pacotes de UDP. Isto é útil se o controlador de interface de rede for capaz de verificar a parte de verificação do cabeçalho UDP no hardware, e a aplicação não ativa a lógica de fragmentação IPsec ou IP.|
|NX_DISABLE_UDP_TX_CHECKSUM | Definido, desativa a computação de verificação da UDP em pacotes UDP de saída. Isto é útil se o controlador de interface de rede for capaz de calcular a parte de verificação do cabeçalho UDP e inserir o valor na cabeça IP antes de transmitir os dados, e a aplicação não permite a lógica de fragmentação IPsec ou IP.|

### <a name="ipv6-options"></a>Opções IPv6  

| Opção  | Descrição  |
|---|---|
| NX_DISABLE_IPV6 | Desativa a funcionalidade IPv6 quando a biblioteca NetX Duo é construída. Para aplicações que não necessitam de IPv6, isto evita puxar o código e espaço de armazenamento adicional necessário para suportar o IPv6.|
|NX_DISABLE_IPV6_PATH_MTU_DISCOVERY | Definido, desativa a descoberta do caminho MTU, que é usado para determinar o máximo MTU no caminho para um alvo na tabela de destino de anfitrião NetX Duo. Isto permite ao anfitrião NetX Duo enviar o maior pacote possível que não exigirá fragmentação. Por predefinição, esta opção é definida (o caminho MTU está desativado).|
|NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY | Definido, permite que uma função de retorno seja invocada quando o endereço IPv6 é alterado. Por padrão, esta opção não está ativada.|
|NX_ENABLE_IPV6_MULTICAST | Definido, permite a função de junção/saída multicast IPv6. Por padrão, esta opção não está ativada.|
|NX_ENABLE_IPV6_PATH_MTU_DISCOVERY | Definido, permite a funcionalidade de descoberta do caminho IPv6 MTU. Por padrão, esta opção não está ativada.|
|NX_IPV6_ADDRESS_CHANGE_NOTIFY_ENABLE | Renomeado para ***NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY** _. Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar _*_NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY_**.|
|NX_IPV6_DEFAULT_ROUTER_TABLE_SIZE | Especifica o número de entradas na tabela de encaminhamento IPv6. Pelo menos na entrada S é necessária para o router predefinido. Definido em ***nx_api.h,*** o valor predefinido é de 8.|
|NX_IPV6_DESTINATION_TABLE_SIZE | Especifica o número de entradas na tabela de destinos IPv6. Isto armazena informações sobre os próximos endereços hop para endereços IPv6. Definido em ***nx_api.h,*** o valor predefinido é de 8.|
|NX_IPV6_MAX_REASSEMBLY_TIME | Símbolo que controla o tempo máximo permitido para remontar o fragmento IPv6.|
|NX_IPV6_MULTICAST_ENABLE | Renomeado para ***NX_ENABLE_IPV6_MULTICAST** _. Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar _*_NX_ENABLE_IPV6_MULTICAST_**.|
|NX_IPV6_PREFIX_LIST_TABLE_SIZE | Especifica o tamanho da tabela de prefixos. As informações de prefixo são obtidas a partir de anúncios de router e fazem parte da configuração do endereço IPv6. Definido em ***nx_api.h,*** o valor predefinido é de 8.|
|NX_IPV6_STATELESS_AUTOCONFIG_CONTROL | Definido, permite ao NetX Duo desativar a função de configuração automática de endereços apátridas. Por padrão, esta opção não está ativada.|
|NX_MAX_IPV6_ADDRESSES | Especifica o número de entradas no conjunto de endereços IPv6. Durante a configuração da interface, o NetX Duo utiliza entradas IPv6 a partir da piscina. Está em incumprimento (NX_MAX_PHYSICAL_INTERFACES \* 3) para permitir que cada interface tenha pelo menos um endereço local de ligação e dois endereços globais. Note que todas as interfaces partilham o conjunto de endereços IPv6.|
|NX_PATH_MTU_INCREASE_WAIT_INTERVAL | Especifica o intervalo de espera nos tiques do temporizador para redefinir o caminho MTU para um alvo específico na tabela de destino. Se ***NX_DISABLE_IPV6_PATH_MTU_DISCOVERY*** for definido, definir este símbolo não tem efeito.|
|NX_PATH_MTU_INCREASE_WAIT_INTERVAL | Símbolo que especifica o intervalo de espera (em segundos) para redefinir o valor do caminho MTU para uma entrada na tabela de destino. Só é válido se ***NX_ENABLE_IPV6_PATH_MTU_DISCOVERY*** for definido. Por predefinição, este valor é definido para 600 (segundos).|

### <a name="neighbor-cache-configuration-options"></a>Opções de configuração da cache do vizinho

| Opção  | Descrição  |
|---|---|
|NX_DELAY_FIRST_PROBE_TIME | Especifica o atraso em segundos antes de a primeira solicitação ser enviada para uma entrada de cache no estado STALE. Definido em ***nx_nd_cache.h,*** o valor predefinido é 5.|
|NX_DISABLE_IPV6_DAD | Definida, esta opção desativa a Deteção de Endereços Duplicado (DAD) durante a atribuição de endereços IPv6. Os endereços são definidos por configuração manual ou pela configuração auto do endereço apátrida.|
|NX_DISABLE_IPV6_PURGE_UNUSED_CACHE_ENTRIES | Definida, esta opção impede o NetX Duo de remover as entradas de mesa de cache mais antigas antes que o seu tempo limite expire para dar espaço a novas entradas quando a tabela estiver cheia. As entradas estáticas e router nunca são purgadas.|
|NX_IPV6_DAD_TRANSMITS | Especifica o número de mensagens de Solicitação de Vizinhos a enviar antes que o NetX Duo marque um endereço de interface como válido. Se ***NX_DISABLE_IPV6_DAD** _ é definido (DAD desativado), definir esta opção não tem efeito. Em alternativa, um valor de zero (0) desliga o DAD mas deixa a funcionalidade DAD no NetX Duo. Definido em _*_nx_api.h**,_ o valor predefinido é 3.|
|NX_IPV6_DISABLE_PURGE_UNUSED_CACHE_ENTRIES | Renomeado para ***NX_DISABLE_IPV6_PURGE_UNUSED_CACHE_ENTRIES** _. Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar _*_NX_DISABLE_IPV6_PURGE_UNUSED_CACHE_ENTRIES_**.|
|NX_IPV6_NEIGHBOR_CACHE_SIZE | Especifica o número de entradas na tabela cache do vizinho IPv6. Definido em ***nx_nd_cache.h,*** o valor predefinido é de 16.|
|NX_MAX_MULTICAST_SOLICIT | Especifica o número de mensagens de solicitação de vizinhos que o NetX Duo transmite como parte do protocolo IPv6 Neighbor Discovery ao mapear entre o endereço IPv6 e o endereço MAC. Definido em ***nx_nd_cache.h,*** o valor predefinido é 3.|
|NX_MAX_UNICAST_SOLICIT | Especifica o número de mensagens de solicitação de vizinhos que o NetX Duo transmite para determinar a capacidade de alcance de um vizinho específico. Definido em ***nx_nd_cache.h,*** o valor predefinido é 3.|
|NX_ND_MAX_QUEUE_DEPTH | Símbolo que define o número máximo de pacotes na fila para que a cache ND seja resolvida. Por predefinição, este símbolo é definido para 4.|
|NX_REACHABLE_TIME | Especifica o tempo de intervalo em segundos para que exista uma entrada de cache no estado REACHABLE sem pacotes recebidos do endereço IPv6 do destino cache. Definido em ***nx_nd_cache.h,*** o valor predefinido é de 30.|
|NX_RETRANS_TIMER  | Especifica em milissegundos o comprimento de atraso entre os pacotes de solicitação enviados pela NetX Duo. Definido em ***nx_nd_cache.h,*** o valor predefinido é de 1000.|
| NXDUO_DISABLE_DAD | Renomeado para ***NX_DISABLE_IPV6_DAD** _. Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar _*_NX_DISABLE_IPV6_DAD_**.|
|NXDUO_DUP_ADDR_DETECT_TRANSMITS | Renomeado para ***NX_IPV6_DAD_TRANSMITS** _. Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar _*_NX_IPV6_DAD_TRANSMITS_**.|

### <a name="miscellaneous-icmpv6-configuration-options"></a>Opções de configuração ICMPv6 diversas

| Opção  | Descrição  |
|---|---|
|NX_DISABLE_ICMPV6_ERROR_MESSAGE | Definido, desativa o NetX Duo de enviar uma mensagem de erro ICMPv6 em resposta a um pacote de problemas (por exemplo, cabeçalho formatado indevidamente ou tipo de cabeçalho de pacote é depreciado) recebido de outro anfitrião.|
|NX_DISABLE_ICMPV6_REDIRECT_PROCESS | Definido, desativa o processamento de pacotes de redirecionamento ICMPv6. NetX Duo por padrão processa redirecionar mensagens e atualizar a tabela de destino com as próximas informações de endereço IP hop.|
|NX_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS | Definido, desativa o NetX Duo do processamento de informações recebidas em pacotes de anúncios de router IPv6.|
|NX_DISABLE_ICMPV6_ROUTER_SOLICITATION | Definido, desativa o NetX Duo do envio de mensagens de solicitação de router IPv6 em intervalos regulares para o router.|
|NX_DISABLE_ICMPV6_RX_CHECKSUM | Definido, desativa o cálculo de checkum ICMPv6 em pacotes ICMP recebidos.|
|NX_DISABLE_ICMPv6_RX_CHECKSUM | Renomeado para ***NX_DISABLE_ICMPV6_RX_CHECKSUM** _. Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar _*_NX_DISABLE_CMPV6_RX_CHECKSUM_**.|
|NX_DISABLE_ICMPV6_TX_CHECKSUM | Definido, desativado e cálculo de checkum ICMPv6 em pacotes ICMP transmitidos.|
|NX_DISABLE_ICMPV6_TX_CHECKSUM | Renomeado para ***NX_DISABLE_ICMPV6_TX_CHECKSUM** _. Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar _*_NX_DISABLE_ICMPV6_TX_CHECKSUM_**.|
|NX_ICMPV6_MAX_RTR_SOLICITATIONS | Defina o número máximo de solicitações de router que um anfitrião envia até que seja recebida uma resposta do router. Se não for recebida qualquer resposta, o anfitrião conclui que não existe nenhum router presente. O valor predefinido é 3.|
|NX_ICMPV6_RTR_SOLICITATION_DELAY | Especifica o atraso máximo para a solicitação inicial do router em segundos.|
|NX_ICMPV6_RTR_SOLICITATION_INTERVAL | Especifica o intervalo entre duas mensagens de solicitação do router. O valor predefinido é 4.|
|NXDUO_DESTINATION_TABLE_SIZE | Renomeado para ***NX_IPV6_DESTINATION_TABLE_SIZE** _. Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar _*_NX_IPV6_DESTINATION_TABLE_SIZE_**.|
|NXDUO_DISABLE_ICMPV6_ERROR_MESSAGE | Renomeado para ***NX_DISABLE_ICMPV6_ERROR_MESSAGE** _. Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar _*_NX_DISABLE_ICMPV6_ERROR_MESSAGE_**.|
|NXDUO_DISABLE_ICMPV6_REDIRECT_PROCESS | Renomeado para ***NX_DISABLE_ICMPV6_REDIRECT_PROCESS** _. Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar _ *_NX_DISABLE_ICMPV6_REDIRECT_PROCESS_**|  
|NXDUO_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS| Renomeado para ***NX_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS** _. Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar _*_NX_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS_**.|
|NXDUO_DISABLE_ICMPV6_ROUTER_SOLICITATION | Renomeado para ***NX_DISABLE_ICMPV6_ROUTER_SOLICITATION** _. Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar _*_NX_DISABLE_ICMPV6_ROUTER_SOLICITATION_**.|
|NXDUO_ICMPV6_MAX_RTR_SOLICITATIONS | Renomeado para ***NX_ICMPV6_MAX_RTR_SOLICITATIONS** _. Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar _*_NX_ICMPV6_MAX_RTR_SOLICITATIONS_**.|
|NXDUO_ICMPV6_RTR_SOLICITATION_INTERVAL | Renomeado para ***NX_ICMPV6_RTR_SOLICITATION_INTERVAL** _. Este símbolo está a ser desvalorizado. Apesar de ainda estar a ser apoiado, novos designs são encorajados a usar _ *_NX_ICMPV6_RTR_SOLICITATION_INTERVAL_**|

## <a name="netx-duo-version-id"></a>ID da versão do duo Netx

A versão atual do NetX Duo está disponível tanto para o utilizador como para o software da aplicação durante o tempo de funcionamento. Pode obter a versão NetX Duo a partir do exame do ficheiro **nx_port.h.** Além disso, este ficheiro também contém um histórico de versão da porta correspondente. O software de aplicação pode obter a versão NetX Duo examinando o _* *_nx_version_id_*_ global de cadeias em _*_nx_port.h**._

O software de aplicação também pode obter informações de libertação das constantes abaixo mostradas definidas em ***nx_api.h***.

Estas constantes identificam a versão atual do produto pelo nome e a versão principal e menor do produto.

\#definir EL_PRODUCT_NETXDUO  
\#definir NETXDUO_MAJOR_VERSION  
\#definir NETXDUO_MINOR_VERSION