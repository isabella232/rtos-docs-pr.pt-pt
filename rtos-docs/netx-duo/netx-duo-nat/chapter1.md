---
title: Capítulo 1 - Introdução à Tradução de Endereços de Rede
description: A tradução de endereços de rede IP (NAT) foi originalmente desenvolvida para resolver o problema de um número limitado de endereços IPv4 da Internet.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8639b87decd78f58a34fe6b8033a2427b560c872814abfdbbcb6057166412d0d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797470"
---
# <a name="chapter-1---an-introduction-to-network-address-translation"></a>Capítulo 1 - Introdução à Tradução de Endereços de Rede

## <a name="the-need-for-network-address-translation"></a>A necessidade de tradução de endereço de rede

A tradução de endereços de rede IP (NAT) foi originalmente desenvolvida para resolver o problema de um número limitado de endereços IPv4 da Internet. A necessidade de NAT surge quando vários dispositivos precisam de aceder à Internet, mas apenas um endereço de Internet IPv4 é atribuído pelo Fornecedor de Serviços de Internet (ISP).

Há outros benefícios de usar o NAT também. A topologia da rede fora do domínio local pode mudar de muitas maneiras. Os clientes podem mudar de fornecedor, as espinhas traseiras da empresa podem ser reorganizadas, ou os fornecedores podem fundir-se ou dividir-se. Sempre que a topologia externa mudar, as atribuições de endereços para anfitriões dentro do domínio local também devem ser alteradas para refletir estas alterações externas. As alterações deste tipo podem ser ocultadas dos utilizadores dentro do domínio, centralizando alterações num router de tradução de endereço único. O NAT permite o acesso dos anfitriões locais à Internet pública e protege-os do acesso direto do exterior. As organizações com uma rede criada predominantemente para uso interno, com necessidade de acesso externo ocasional são bons candidatos a este esquema.

## <a name="basic-nat-and-network-address-port-translation"></a>Tradução portuária de endereços de nat básico e endereço de rede

Um router ativado pela NAT é instalado entre a rede pública e a rede privada. O papel do router ativado pelo NAT é traduzir entre os endereços IPv4 privados internos e o endereço IPv4 público atribuído, para que todos os dispositivos da rede privada possam partilhar o mesmo endereço público IPv4.

Na implementação básica do NAT, o router NAT 'detém' um ou mais endereços IP registados globalmente diferentes do seu próprio endereço IP. Estes endereços globais estão disponíveis para atribuir aos anfitriões na sua rede privada, quer estática quer dinamicamente. NAPT, ou Tradução Portuária de Endereço de Rede, é uma variação do NAT básico, onde a tradução de endereços de rede é estendida para incluir um identificador de "transporte". Normalmente, este é o número de porta para pacotes TCP e UDP, e o ID de consulta para pacotes ICMP.

As ligações através da fronteira NAT são normalmente iniciadas por anfitriões na rede privada enviando pacotes de saída para um hospedeiro externo. Estes anfitriões são geralmente designados endereços IP *dinâmicos* (temporários) para este fim. No entanto, também é possível ter ligações iniciadas na direção oposta se a rede privada tiver 'servidores' por exemplo, servidores HTTP ou FTP que aceitarão pedidos do Cliente a partir da rede externa. A NAT irá normalmente atribuir a estes anfitriões locais um endereço IP *estático* (permanente): porta.

## <a name="how-network-address-translation-works"></a>Como funciona a tradução de endereços de rede

Uma configuração típica da rede com um router ativado pelo NAT é ilustrada na Figura 1.

![Uma configuração típica de rede com um router ativado pelo NAT](media/image2.png)

**Figura 1 - Uma configuração típica da rede com um router ativado pelo NAT**

Um router ativado pelo NAT normalmente tem duas interfaces de rede. Uma interface está ligada à Internet pública; o outro está ligado à rede privada. Um router típico nesta configuração é responsável pelo encaminhamento de datagramas ip entre a rede privada e a rede pública com base no endereço IP de destino. Um router ativado pelo NAT realiza a tradução de endereços antes de encaminhar um datagrama IPv4 entre o público e a interface privada. É estabelecida uma tradução para cada sessão de TCP ou UDP, com base no endereço de origem interna, número de porta de origem e endereço de destino externo e número de porta de destino. Para o pedido de eco ICMP e para o datagrama de resposta, o ID de consulta ICMP é utilizado em vez do número da porta.

Para ilustrar uma implementação típica da Tradução de Endereços de Rede, consideremos uma configuração de rede na Figura 2.

![Uma implementação típica da Tradução de Endereços de Rede](media/image3.png)

**Figura 2 - Uma implementação típica da Tradução de Endereços de Rede**

Neste cenário, o router NAT liga a rede privada à esquerda e a rede pública à direita. Vamos assumir no lado da rede pública, o endereço IP interface de router NAT é 202.151.25.14; na interface de rede privada, o router NAT utiliza o endereço IP 192.168.1.254. Um nó na rede privada inicia uma ligação TCP com um servidor web na Internet.

A figura 3 mostra uma visão de alto nível do processo de tradução de endereços de rede.

![Uma visão de alto nível do processo de tradução de endereços de rede](media/image4.png)

**Figura 3 - Uma visão de alto nível do processo de tradução de endereços de rede**

1. O cliente transmite uma mensagem TCP SYN para o servidor web. O endereço do remetente é 192.168.1.15, porta número 6732; o endereço de destino é 128.15.54.3, porta número 80.
1. O pacote do Cliente é recebido na interface de rede privada pelo router NAT. A regra de tráfego de saída aplica-se ao pacote: o endereço do remetente (Cliente) é traduzido para o endereço IP público do router NAT 202.15.25.14, e o número de porta de origem do remetente (Cliente) é traduzido para o número da porta TCP 2015 na interface pública.
1. O pacote é então transmitido através da Internet e, em última análise, atinge o seu anfitrião de destino 128.15.54.3. Note que do lado recetor, com base no endereço de fonte de camada IP e no número da porta da camada TCP, o pacote parece ter sido originário de 202.151.24.14, número da porta 2015.
   A figura 4 mostra o processo NAT no caminho de retorno.

   ![Processo NAT no caminho de retorno](media/image5.png)

   **Figura 4 - Processo NAT no caminho de retorno**
1. Neste cenário, o anfitrião da Internet 128.15.54.3 envia um pacote de resposta com o endereço de Internet do router NAT como destino.
1. O pacote chega ao router NAT. Uma vez que se trata de um pacote in-bound, aplicam-se as regras de tradução in-bound: o endereço de destino é alterado de volta para o endereço IP do remetente original ( Cliente) endereço IP: 192.168.1.15, porta de destino número 6732.
1. O pacote é então encaminhado para o Cliente através da interface que está ligada à rede interna.

Desta forma, o endereço da rede de internet e o número de porta do remetente não estão expostos a outros anfitriões na Internet pública.

## <a name="netx-duo-nat-features"></a>Recursos do Duo NETX NAT

Quando a instância NAT é criada usando *nx_nat_create* chamada, a tabela de tradução NAT é criada.

```C
UINT nx_nat_create(NX_NAT_DEVICE *nat_ptr, NX_IP *ip_ptr,
    UINT global_interface_index,
    VOID *dynamic_cache_memory,
    UINT dynamic_cache_size);
```

Para acompanhar as traduções de endereços de rede para todas as ligações ativas entre redes locais e externas, o router ativado pelo NetX Duo NAT mantém uma tabela de tradução com informações sobre cada ligação privada de anfitrião que inclui endereço IP de origem e destino e número de porta.

A localização desta tabela de tradução ("cache") é definida com o ponteiro dynamic_cache_memory. Esta área deve ser um espaço tampão alinhado 4 byte. O tamanho da tabela (ou número de entradas) é determinado dividindo o tamanho da cache dynamic_cache_size pelo tamanho de uma entrada de mesa NAT. O quadro deve ser suficientemente grande para o número mínimo de entradas especificadas por **NX_NAT_MIN_ENTRY_COUNT definidas em *nx_nat.h*. O valor predefinido é 3.**

O tempo limite para todas as entradas dinâmicas na tabela de tradução NetX Duo NAT é inicializado para NX_NAT_ENTRY_RESPONSE_TIMEOUT que é definido em *nx_nat.h*. O valor predefinido é de 4 minutos (ou 240 carraças de sistema para um processador de 100 mHz) como recomendado pelo RFC 2663. Cada vez que o NetX Duo NAT recebe ou envia um pacote correspondente a uma entrada dinâmica na tabela, repõe que o tempo de entrada sai para NX_NAT_ENTRY_RESPONSE_TIMEOUT. Ao pesquisar a tabela, o NetX Duo NAT também verificará a tabela para obter entradas expiradas e eliminá-las-á.

Para criar entradas de entrada como estáticas na tabela, por exemplo, para servidores na rede local, o NetX Duo NAT fornece o serviço *nx_nat_inbound_entry_create.* Se uma entrada de mesa definir a ligação do anfitrião local como estática, nunca expira.

```C
UINT nx_nat_inbound_entry_create(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *entry_ptr,
    ULONG local_ip_address, USHORT external_port,
    USHORT local_port, UCHAR protocol);
```

Este serviço é descrito mais detalhadamente no [Capítulo 4 - Descrição dos Serviços](chapter4.md)

Durante o tempo de funcionamento, se a tabela de tradução estiver cheia e não puderem ser adicionadas mais entradas, a NetX Duo NAT notificará a aplicação NAT com uma chamada completa de cache se uma estiver registada na instância NAT. Isto é feito usando o serviço *nx_nat_cache_notify_set:*

```C
UINT nx_nat_cache_notify_set(NX_NAT_DEVICE *nat_ptr,
    VOID (*cache_full_notify_cb)(NX_NAT_DEVICE *nat_ptr));
```

Consulte [o Capítulo 4 - Descrição dos Serviços](chapter4.md) para mais informações sobre este serviço.

## <a name="nat-packet-processing-in-netx-duo"></a>Processamento de pacotes NAT em NetX Duo

NetX Duo NAT destina-se a ser utilizado num router IPv4. Para que o NAT funcione, o NetX Duo tem de ser configurado para encaminhar pacotes para o servidor NAT. Consulte o Capítulo 2 na instalação NetX Duo NAT para saber como fazê-lo. O servidor NAT indica então se irá 'consumir' (tentativa de encaminhar) o pacote para um anfitrião em qualquer uma das suas redes. Se não consumir o pacote, o pacote é 'devolvido' ao NetX Duo para processar o pacote como normalmente faria.

Quando o servidor NAT recebe um pacote para encaminhar a partir do NetX Duo, determina se o pacote está de entrada ou saída.

Para pacotes de saída, o servidor NAT verifica o endereço de origem e porta do cabeçalho IP do pacote. Se a tabela de tradução não contiver uma entrada para um pacote previamente enviado por este anfitrião para o mesmo destino, a NAT criará uma nova entrada que conterá um endereço IP de origem global único:porta para a ligação, e modificará os cabeçalhos do pacote com este novo endereço IP:porta antes de enviá-lo para a rede externa.

Para pacotes de entrada, o servidor NAT procura uma entrada anterior na sua tabela de tradução com um endereço IP externo: porta que corresponde ao endereço IP do destino do pacote: porta. Se não for encontrada correspondência, descartará o pacote a menos que o endereço de destino: a porta é o endereço externo do servidor na rede local. Se encontrar uma correspondência, substituirá o endereço IP de destino externo do porta-pacotes: porta com o endereço IP privado: porta e enviará o pacote para a rede local para o anfitrião privado pretendido.

NetX Duo NAT utiliza uma gama de portas de tradução TCP, UDP e ICMP para criar endereço local único: ligações portuárias para anfitriões locais conectando-se com anfitriões externos. As seguintes opções configuráveis do utilizador, definidas em *nx_nat.h,* definem a gama para cada protocolo:

```C
NX_NAT_START_TCP_PORT

NX_NAT_END_TCP_PORT

NX_NAT_START_UDP_PORT

NX_NAT_END_UDP_PORT

NX_NAT_START_ICMP_QUERY_ID

NX_NAT_END_ICMP_QUERY_ID
```

## <a name="nat-requirements-and-constraints"></a>Requisitos e restrições do NAT

NetX Duo NAT requer NetX Duo 5.8 ou mais tarde. A aplicação NAT requer a criação de uma única instância IP e uma interface para a rede física interna e externa.

Constrangimentos:

- NetX Duo NAT suporta TCP, UDP e ICMP. O IGMP não é suportado.
- NetX Duo NAT não suporta endereço iPv6.
- O NetX Duo NAT não inclui serviços DNS ou DHCP, embora o NetX Duo NAT possa integrar esses serviços com as suas operações NAT.

## <a name="rfcs-supported-by-netx-duo-nat"></a>RFCs Suportados por NetX Duo NAT

A implementação do NetX Duo NAT baseia-se em informações apresentadas nos seguintes RFCs:

- RFC 2663: Endereço de rede IP Tradutor (NAT) Terminologia e Considerações
- RFC 3022: Endereço IP Netowrk tradicional Tradutor (NAT Tradicional)
- RFC 4787: Prescrições comportamentais de tradução de endereços de rede (NAT) para UDP Unicast
