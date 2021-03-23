---
title: Capítulo 2 - Instalação e utilização de mDNS
description: Este capítulo contém uma descrição de várias questões relacionadas com a instalação, configuração e utilização do módulo NetX Duo mDNS.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6f9e3d023f1bdbde4546a94da1bc1ccb48578d0e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825921"
---
# <a name="chapter-2---installation-and-use-of-mdns"></a>Capítulo 2 - Instalação e utilização de mDNS

Este capítulo contém uma descrição de várias questões relacionadas com a instalação, configuração e utilização do módulo NetX Duo mDNS.

## <a name="product-distribution"></a>Distribuição de Produtos

NetX Duo mDNS está disponível em [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . O pacote inclui dois ficheiros de origem e um ficheiro PDF que contém este documento, da seguinte forma:

- **nxd_mdns.h** Arquivo de cabeçalho para módulo NetX Duo mDNS
- **nxd_mdns.c** Arquivo C Fonte para módulo NetX Duo mDNS
- **nxd_mdns.pdf** Descrição em PDF do mDNS para NetX Duo
- **demo_netxduo_mdns.c** Um simples programa de demonstração que ilustra os serviços prestados pelo MDNS.

## <a name="netx-duo-mdns-installation"></a>Instalação NetX Duo mDNS

Para utilizar as APIs NetX Duo mDNS, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX Duo está instalado. Por exemplo, se o NetX Duo for instalado no diretório "*c:\netxduo*" então o *nxd_mdns.h* e *nxd_mdns.c* devem ser copiados para este diretório.

## <a name="using-netx-duo-mdns"></a>Utilização do NetX Duo mDNS

A utilização do módulo NetX Duo mDNS é fácil. Basicamente, o código de aplicação deve incluir *nxd_mdns.h* depois de incluir *tx_api.h e* *nx_api.h,* para utilizar o ThreadX e o NetX Duo, respectivamente. O projeto de construção deve incluir o código fonte mDNS e o ficheiro de aplicação, e, claro, os ficheiros da biblioteca ThreadX e NetX. Isto é tudo o que é necessário para usar NetX Duo mDNS.

## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração para a construção do módulo NetX Duo mDNS. Os valores predefinidos estão listados, mas cada definição pode ser definida pela aplicação antes da inclusão do ficheiro de cabeçalho NetX Duo mDNS especificado. A seguinte lista descreve cada uma em detalhe:

- **NX_MDNS_DISABLE_SERVER** Desativa a funcionalidade do servidor mDNS/DNS-SD. Sem a funcionalidade do servidor, o módulo mDNS/DNS-SD não anuncia serviços prestados pelo anfitrião local, nem responde a inquéritos do MDNS. Este símbolo não é definido por defeito.
- **NX_MDNS_DISABLE_CLIENT** Desativa a funcionalidade do cliente mDNS/DNS-SD. Sem a funcionalidade do cliente, o mDNS/DNS-SD não envia consultas, nem mantém as respostas de consulta mDNS recebidas pela rede.
- **NX_MDNS_ENABLE_ADDRESS_CHECK** Definido, o módulo mDNS executa valida endereços (endereço de origem, endereço de destino e números de porta) a partir das mensagens mDNS recebidas. Este símbolo é definido por defeito.
- **NX_MDNS_ENABLE_CLIENT_POOF** Definido, o módulo mDNS realiza Observação Passiva de Falhas, o cliente mDNS/DNS_SD (querier) observa as consultas multicast emitidas pelos outros anfitriões da rede. Este símbolo é definido por defeito.
- **NX_MDNS_ENABLE_SERVER_NEGATIVE_RESPONSES** Definido, o servidor mDNS /DNS-SD (responder) gera respostas negativas a consultas para as quais tem propriedade legítima. Este símbolo é definido por defeito.
- **NX_MDNS_ENABLE_IPV6** Definida, a mensagem mDNS/DNS-SD enviar/processar mDNS sobre o endereço IPv6. Este símbolo não é definido por defeito.
- **NX_MDNS_IPV6_ADDRESS_COUNT** Contagem máxima de endereços IPv6 de anfitrião. O valor predefinido é 2.
- **NX_MDNS_HOST_NAME_MAX** Tamanho máximo da corda para o nome do hospedeiro. O valor predefinido é 64. Não inclui o exterminador NULO.
- **NX_MDNS_SERVICE_NAME_MAX** Tamanho máximo da corda para o nome de serviço. O valor predefinido é 64. Não inclui o exterminador NULO.
- **NX_MDNS_DOMAIN_NAME_MAX** Tamanho máximo da corda para o nome de domínio. O valor predefinido é 16. Não inclui o exterminador NULO.
- **NX_MDNS_CONFLICT_COUNT** Contagem máxima de conflito para o nome de anfitrião ou nome de serviço. O valor predefinido é 8.
- **NX_MDNS_RR_TTL_HOST** Valor TTL para registos de recursos com nome de anfitrião, em segundo. O valor predefinido é de 120 por 120s.
- **NX_MDNS_RR_TTL_OTHER** Valor TTL para outros registos de recursos, em segundo. O valor predefinido é de 4500 durante 75 minutos.
- **NX_MDNS_PROBING_TIMER_COUNT** O intervalo de tempo, em tiques, entre mensagens de sondagem mDNS. O valor predefinido é de 25 carraças para 250ms.
- **NX_MDNS_ANNOUNCING_TIMER_COUNT** O intervalo de tempo, em tiques, entre as mensagens de anúncio do MDNS. O valor predefinido é de 25 carraças para 250ms.
- **NX_MDNS_GOODBYE_TIMER_COUNT** O intervalo de tempo, em tiques, entre mensagens repetidas de "adeus". O valor predefinido é de 25 carraças para 250ms.
- **NX_MDNS_QUERY_MIN_TIMER_COUNT** O intervalo de tempo mínimo, em carrapatos, entre duas consultas. O valor padrão é de 100 carraças por 1 segundo.
- **NX_MDNS_QUERY_MAX_TIMER_COUNT** O intervalo de tempo máximo, em tiques, entre duas consultas. O valor predefinido é de 360000 por 60 segundos.
- **NX_MDNS_QUERY_DELAY_MIN** O atraso mínimo para o envio da primeira consulta, em carrapatos. O valor predefinido é de 2 carraças para 20ms.
- **NX_MDNS_QUERY_DELAY_RANGE** O intervalo de atraso para o envio da primeira consulta, em tiques. O valor predefinido é de 10 carraças para 100ms.
- **NX_MDNS_RESPONSE_INTERVAL** O intervalo de tempo, em tiques, na resposta a uma consulta para garantir um intervalo de pelo menos 1s desde a última vez que o recorde foi multicast. O valor predefinido é de 100 carraças.
- **NX_MDNS_RESPONSE_PROBING_TIMER_OUT** O intervalo de tempo, em tiques, na resposta a uma sonda pergunta para garantir um intervalo de pelo menos 250ms desde a última vez que o recorde foi multicast. O valor predefinido é de 25 carraças.
- **NX_MDNS_RESPONSE_UNIQUE_DELAY** O atraso, em tiques, na resposta a uma consulta a um serviço único para a rede local. O valor predefinido é de 1 tique para 10ms.
- **NX_MDNS_RESPONSE_SHARED_DELAY_MIN** O atraso mínimo, em carraças, na resposta a uma consulta a um recurso partilhado. O valor predefinido é de 2 carraças para 20ms.
- **NX_MDNS_RESPONSE_SHARED_DELAY_RANGE** O intervalo de atraso, em tiques, na resposta a uma consulta a um recurso partilhado. O valor predefinido é de 10 carraças para 100ms.
- **NX_MDNS_RESPONSE_TC_DELAY_MIN** O atraso mínimo, em carraças, na resposta a uma consulta com tC bit. O valor predefinido é de 40 carraças para 400ms.
- **NX_MDNS_RESPONSE_TC_DELAY_RANGE** O intervalo de atraso, em tiques, na resposta a uma consulta com tC bit. O valor predefinido é de 10 carraças para 100ms.
- **NX_MDNS_TIMER_COUNT_RANGE** Ao enviar respostas mDNS, o pacote contém respostas que de outra forma seriam enviadas dentro deste intervalo de contador de temporizador. O intervalo de contagem do temporizador é expresso em carrapatos. O valor predefinido é de 12 para 120ms. Este valor permite que uma resposta inclua mensagens que seriam enviadas dentro da faixa de 120ms seguinte se cada carrapato for de 10ms.
- **NX_MDNS_PROBING_RETRANSMIT_COUNT** O número de mensagens de sondagem retransmitidas. O valor predefinido é 3.
- **NX_MDNS_GOODBYE_RETRANSMIT_COUNT** O número de mensagens de "adeus" retransmitidas. O valor predefinido é 1.
- **NX_MDNS_POOF_MIN_COUNT** O número de consultas que não há resposta multicast, então o anfitrião pode tomar isto como uma indicação de que o registo pode deixar de ser válido. O valor predefinido é 2.
- **NX_MDNS_POOF_TIME_COUNT** O intervalo de tempo, em tiques, na eliminação do registo da cache depois de ver duas ou mais destas consultas, e não ver nenhuma resposta multicast contendo a resposta esperada. O valor predefinido é de 1000 carraças durante 10 segundos.
- **NX_MDNS_RR_DELETE_DELAY_TIMER_COUNT** O atraso para a eliminação de um registo de recursos quando o TTL deste registo é zero, em tiques, o valor padrão é de 100 carraças por 1 segundo.
