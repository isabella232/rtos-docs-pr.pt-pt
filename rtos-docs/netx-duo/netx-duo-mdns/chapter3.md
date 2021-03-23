---
title: Capítulo 3 - Descrição da cache de serviço interno
description: 'O módulo NetX Duo mDNS gere duas caches de serviços internos: a cache de serviço local e a cache de serviço de pares.'
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 007f1080a076730cfbcdedc9f063ac0c427a414c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825915"
---
# <a name="chapter-3---description-of-internal-service-cache"></a>Capítulo 3 - Descrição da cache de serviço interno

O módulo NetX Duo mDNS gere duas caches de serviços internos: a cache de serviço local e a cache de serviço de pares. O serviço local armazena a Resource Records relacionada com os serviços oferecidos por aplicações em execução no nó. Para consultas recebidas, se a pergunta corresponder ao serviço oferecido, as respostas do mDNS com respostas armazenadas na cache de serviço local. Os pedidos registam serviços através da *nx_mdns_service_add da API()*. Para remover os serviços, as aplicações utilizam a *API nx_mdns_service_delete()* que por sua vez enviará mensagens de "adeus" antes de remover as entradas correspondentes na cache de serviço local.

Quando um serviço é adicionado, o mDNS mantém pelo menos 3 Registos de Recursos na cache de serviço local: SRV, PTR e TXT. O Registo adicional de Recursos PTR pode ser adicionado se o tipo de serviço incluir o subtipo. Por exemplo, uma aplicação regista um serviço:

```
*name*._*subtype*._sub._*type*._tcp.local,
```

dois Registos de Recursos PTR são adicionados à cache de serviço local, um para

```
“*_subtype._*sub*._type._*tcp.local *PTR name.type._*tcp*.*local”
```

e o outro para

```
*“_type._*tcp*.*local *PTR name.type._*tcp*.*local”.
```

A cache de serviço de pares contém mDNS Resource Records recebidos de nós vizinhos. o módulo mDNS recolhe Registos de Recursos anunciados por outros nós na rede e armazena a informação recebida na cache de serviço de pares. Quando as consultas de aplicação para obter informações como endereços IPv4 ou IPv6 de anfitrião, o mDNS procura a cache de serviço de pares para obter respostas em cache local. Quando as consultas de aplicação para serviços oferecidos pelos pares, o mDNS procura através da cache registos de endereços PTR, SRV, TXT e IPvv4/IPv6. A cache de serviço de pares também armazena consultas enviadas para o nó. Por exemplo, um pedido pode solicitar um determinado serviço ligando *nx_mdns_service_one_shot_query.* Se o serviço não for encontrado na cache de serviço de pares, o mDNS cria questões de consulta (PTR, SRV e TXT) na cache de serviço de pares. Estas questões de consulta serão enviadas periodicamente para a rede até que o serviço seja resolvido, ou o tempo limite. Da mesma forma, o pedido pode utilizar a *API nx_mdns_service_continous_query()* para solicitar um determinado serviço durante um longo período de tempo (a aplicação cancela uma consulta contínua previamente emitida através da *nx_mdns_service_query_stop da API().* Para procurar um determinado serviço na cache de serviço de pares sem enviar consultas para a rede, as aplicações podem utilizar o *nx_mdns_serivce_lookup API().* Esta API apenas procura os registos de recursos na cache de serviço de pares.

Cada Registo de Recursos é armazenado numa estrutura de dados *NX_MDNS_RR* nas caches de serviço. As cadeias em Registos de Recursos são de comprimento variável, portanto não são armazenadas na estrutura *NX_MDNS_RR.* O Registo de Recursos contém um ponteiro para o local de memória real onde a cadeia é armazenada. A tabela de cordas e os Registos de Recursos partilham a cache de serviço. Os Registos de Recursos são armazenados desde o início da cache de serviço e crescem no final da cache. A mesa de cordas começa a partir do fim da cache de serviço e cresce para o início da cache. Cada corda na mesa de cordas tem um campo de comprimento e um contra-campo. Quando uma corda é adicionada à tabela de cordas, se a mesma corda já estiver presente na tabela, o valor do contador é incrementado e nenhuma memória é atribuída para a cadeia. A cache de serviço é considerada completa se não puderem ser adicionados mais registos de recursos ou novas cordas à cache de serviço.

Existem duas formas de uma aplicação para encontrar serviços oferecidos na rede local. Pode emitir um serviço específico através de uma consulta de um tiro, ou pode iniciar uma consulta contínua para "monitorizar" as atividades na rede. No cenário de consulta de um curto prazo, a aplicação deve especificar o tipo de serviço. mDNS procura através da cache de serviço local e da cache de serviço de pares. Se estiver em casos de serviço, a consulta de um tiro retorna com as informações encontradas nos Registos de Recursos. Se não houver registos na cache de serviço local ou na cache de serviço de pares, o mDNS envia mensagens de consulta. Se o nome da instância for especificado, um tipo *QUALQUER* (consulta do tipo SRV e TXT) com o nome de instância específica, sob a forma de "name.type.local", é enviado para a rede local. Se o nome da instância não for especificado, é enviado um tipo de consulta PTR para a rede local. O primeiro serviço completo recebido é devolvido ao chamador.

A consulta contínua funciona de forma diferente. O caso típico de utilização para uma consulta contínua é monitorizar a rede local para um serviço específico (por exemplo, procurar constantemente serviços de impressão na rede local). Neste caso, a aplicação emite uma consulta de pesquisa (através da consulta *nx_mdns_service_continious_* API) para determinado tipo de serviços. Normalmente, o chamador não espera por uma resposta específica. Para consultas submetidas como consulta contínua, o módulo mDNS transmite periodicamente as consultas com intervalos exponencialmente crescentes. Para parar a consulta, a aplicação deve utilizar o *nx_mdns_service_query_stop* da API para parar o temporizador interno nestas consultas. O tipo de consulta pode ser NU, caso em que o tipo de consulta é definido para o tipo de PTR especial "_services._dns-sd._udp.local". Este tipo de serviço é definido pelo mDNS como uma forma de descobrir todos os serviços disponíveis na rede local. Se o nome da instância for fornecido, é enviado para a rede local um tipo QUALQUER (consulta do tipo SRV e TXT) com o nome de instância específica "name.type.local". Se o nome da instância for NU, é enviado um tipo de consulta PTR para a rede local,

Todas as respostas, incluindo respostas de consultas não solicitadas, são registadas na cache de serviço de pares. Posteriormente, a aplicação utiliza a *API nx_mdns_service_lookup* para recuperar o serviço específico a partir da cache de serviço de pares.

Nota especial sobre fragmentação: Cada *NX_MDNS_RR* estrutura é fixada em tamanho, pelo que não está sujeita a fragmentação à medida que o mDNS adiciona e elimina rrs. No entanto, as cordas têm um comprimento variável. Depois de uma corda ser eliminada, o espaço fica disponível e pode ser usado para uma nova corda se a nova corda for capaz de se encaixar. Mas esta operação faz com que a memória se fragmente. À medida que os serviços são adicionados e removidos, a tabela de cordas pode ser fragmentada ao ponto de não serem adicionadas novas cordas, mesmo que a cache de serviço contenha bytes não reutilizados suficientes para a cadeia. As aplicações locais tendem a ser mais estáveis e previsíveis. Portanto, a cache de serviço local é menos suscetível de sofrer de fragmentação. A cache de serviço por pares, por outro lado, adiciona constantemente RRs à medida que os serviços ficam disponíveis, ou remove rrs à medida que os serviços são eliminados pelos nós na rede. Os serviços na rede vêm e vão, causando operações mais frequentes de atribuição/eliminação na tabela de cordas. Com o tempo é possível que a mesa de cordas se fragmente. Quando esta situação acontece, uma solução simples é lavar toda a cache de serviço de pares. Isto pode ser feito chamando a API *nx_mdns_peer_cache_clear().* Note que esta API termina automaticamente quaisquer consultas contínuas pendentes.
