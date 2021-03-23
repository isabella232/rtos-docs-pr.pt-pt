---
title: Capítulo 1 - Introdução ao Cliente DHCP Azure RTOS NetX Duo DHCP
description: No Azure RTOS NetX Duo DHCP Cliente, o endereço IP da aplicação é um dos parâmetros fornecidos para a chamada de serviço *nx_ip_create.*
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f5b2f2ef7b440e2f2ee8aa6a9bd6ed199eaf13fb
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826137"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-dhcp-client"></a>Capítulo 1 - Introdução ao Cliente DHCP Azure RTOS NetX Duo DHCP

No Azure RTOS NetX Duo DHCP Cliente, o endereço IP da aplicação é um dos parâmetros fornecidos para a chamada de serviço *nx_ip_create.* O fornecimento do endereço IP não levanta qualquer problema se o endereço IP for conhecido da aplicação, quer estática quer através da configuração do utilizador. No entanto, existem alguns casos em que a aplicação não sabe ou se importa com o seu endereço IP. Nestas situações, deve ser fornecido um endereço IP zero à função *nx_ip_create* e o protocolo do Cliente DHCP deve ser utilizado para obter dinamicamente um endereço IP.

## <a name="dynamic-ip-address-assignment"></a>Atribuição dinâmica de endereços IP

O serviço básico utilizado para obter um endereço IP dinâmico da rede é o Protocolo de Resolução de Endereços Reversos (RARP). Este protocolo é semelhante ao ARP, exceto que foi concebido para obter um endereço IP para si mesmo em vez de encontrar o endereço MAC para outro nó de rede. A mensagem RARP de baixo nível é transmitida na rede local e é da responsabilidade de um servidor na rede responder com uma resposta RARP, que contém um endereço IP atribuído dinamicamente.

Embora a RARP ofereça um serviço de alocação dinâmica de endereços IP, tem várias deficiências. A deficiência mais gritante é que o RARP apenas fornece uma atribuição dinâmica do endereço IP. Na maioria das situações, é necessária mais informação para que um dispositivo participe adequadamente numa rede. Além de um endereço IP, a maioria dos dispositivos precisa da máscara de rede e do endereço IP gateway. O endereço IP de um servidor DNS e outras informações de rede também podem ser necessários. A RARP não tem a capacidade de fornecer esta informação.

## <a name="rarp-alternatives"></a>Alternativas RARP

Para superar as deficiências da RARP, os investigadores desenvolveram um mecanismo de atribuição de endereços IP mais abrangente chamado Protocolo de Correia de Arranque (BOOTP). Este protocolo tem a capacidade de alocar dinamicamente um endereço IP e também fornecer informações adicionais importantes de rede. No entanto, o BOOTP tem a desvantagem de ser projetado para configurações de rede estática. Não permite uma atribuição rápida ou automatizada de endereços.

É aqui que o Protocolo de Configuração do Anfitrião Dinâmico (DHCP) é extremamente útil. O DHCP foi concebido para alargar a funcionalidade básica do BOOTP para incluir a atribuição de servidores IP completamente automatizados e alocação de endereços IP completamente dinâmicos através da "locação" de um endereço IP a um cliente por um período de tempo especificado. O DHCP também pode ser configurado para alocar endereços IP de forma estática como o BOOTP.

## <a name="dhcp-messages"></a>Mensagens DHCP

Embora o DHCP melhore consideravelmente a funcionalidade do BOOTP, o DHCP utiliza o mesmo formato de mensagem que o BOOTP e suporta as mesmas opções de fornecedor que o BOOTP. Para desempenhar a sua função, a DHCP introduz sete novas opções específicas do DHCP, da seguinte forma:

- DESCUBRA (1) (enviado pelo Cliente DHCP)
- OFERTA (2) (enviado pelo Servidor DHCP)
- PEDIDO (3) (enviado pelo Cliente DHCP)
- DECLÍNIO (4) (enviado pelo Cliente DHCP)
- ACK (5) (enviado pelo Servidor DHCP)
- NACK (6) (enviado pelo Servidor DHCP)
- LANÇAMENTO (7) (enviado pelo Cliente DHCP)
- INFORM (8) (enviado pelo Cliente DHCP)
- FORCERENEW (9) (enviado pelo Cliente DHCP)

## <a name="dhcp-communication"></a>Comunicação DHCP

O DHCP utiliza o protocolo UDP para enviar pedidos e respostas de campo. Antes de ter um endereço IP, as mensagens UDP que transportam as informações do DHCP são enviadas e recebidas utilizando o endereço de transmissão IP de 255.255.255.255.255.

## <a name="dhcp-client-state-machine"></a>Máquina do Estado do cliente DHCP

O Cliente DHCP é implementado como uma máquina estatal. A máquina estatal é processada por um fio DHCP interno que é criado durante *nx_dhcp_create* processamento. Os principais estados do Cliente DHCP são os seguintes:

- **NX_DHCP_STATE_BOOT** Começando com um endereço IP anterior
- **NX_DHCP_STATE_INIT** Começando sem o valor do endereço IP anterior
- **NX_DHCP_STATE_SELECTING** À espera de uma resposta de qualquer servidor DHCP
- **NX_DHCP_STATE_REQUESTING** Servidor DHCP identificado, pedido de endereço IP enviado
- **NX_DHCP_STATE_BOUND** DhCP IP Endereço de arrendamento estabelecido
- **NX_DHCP_STATE_RENEWING** DHCP IP Endereço prazo de renovação de contrato decorrido, renovação solicitada
- **NX_DHCP_STATE_REBINDING** DHCP IP Endereço de locação reencambido tempo decorrido, renovação solicitada
- **NX_DHCP_STATE_FORCERENEW** DhCP IP Endereço de aluguer estabelecido, renovação de força por servidor (atualmente não suportado) ou pela chamada de nx_dhcp_force_renew
- **NX_DHCP_STATE_ADDRESS_PROBING** Sondagem do Endereço IP do DHCP, envie a sonda ARP para detetar o conflito de endereços IP.

## <a name="dhcp-client-multiple-interface-support"></a>Suporte de interface múltipla do cliente DHCP

O Cliente DHCP foi previamente implementado para funcionar apenas numa única interface de rede. O comportamento padrão foi (e ainda é) para o Cliente DHCP funcionar na interface principal. Ao chamar *nx_dhcp_set_interface_index,* a aplicação poderia (e ainda pode) executar DHCP numa interface de rede secundária em vez da interface primária.

Suporta agora o DHCP em várias interfaces em paralelo. Consulte **o Cliente DHCP em Múltiplas Interfaces Simultaneamente** no Capítulo Dois para obter detalhes específicos sobre como executar o Cliente DHCP em mais de uma interface física simultaneamente.

## <a name="dhcp-user-request"></a>Pedido de utilizador DHCP

Uma vez que o servidor DHCP concede um endereço IP, o processamento do cliente DHCP pode solicitar parâmetros adicionais - um de cada vez - utilizando o serviço *nx_dhcp_user_option_request.*

## <a name="dhcp-client-socket-queue"></a>Fila de tomada de cliente DHCP 

O Cliente DHCP limpa automaticamente os pacotes de transmissão dos Servidores DHPC destinados a outros Clientes DHCP da sua tomada recebem fila enquanto espera que o Servidor responda a si próprio. Numa rede movimentada, não fazê-lo poderia fazer com que os pacotes destinados ao Cliente fossem abandonados.

## <a name="dhcp-rfcs"></a>DHCP RFCs

O Cliente DHCP da NetX Duo está em conformidade com o RFC2132, RFC2131 e RFCs relacionados.