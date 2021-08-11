---
title: Capítulo 1 - Introdução ao Azure RTOS NetX Duo DHCP Server
description: No NetX Duo, o endereço IP da aplicação é um dos parâmetros fornecidos para a chamada de serviço *nx_ip_create.*
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a56f692059cbd3e2a72d64cf80ee90a917b80987add8130d3a1df70b3b0c3a71
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788478"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-dhcp-server"></a>Capítulo 1 - Introdução ao servidor DHCP Azure RTOS NetX Duo DHCP

No NetX Duo, o endereço IP da aplicação é um dos parâmetros fornecidos para a chamada de serviço *nx_ip_create.* O fornecimento do endereço IP não levanta qualquer problema se o endereço IP for conhecido da aplicação, quer estática quer através da configuração do utilizador. No entanto, existem alguns casos em que a aplicação não sabe ou se importa com o seu endereço IP. Nestas situações, deve ser fornecido um endereço IP zero à função *nx_ip_create* e a aplicação estabelece a comunicação com o seu servidor DHCP para solicitar e obter um endereço IP dinamicamente.

## <a name="dynamic-ip-address-assignment"></a>Atribuição dinâmica de endereços IP

O serviço básico utilizado para obter um endereço IP dinâmico da rede é o Protocolo de Resolução de Endereços Reversos (RARP). Este protocolo é semelhante ao ARP, exceto que foi concebido para obter um endereço IP para si mesmo em vez de encontrar o endereço MAC para outro nó de rede. A mensagem RARP de baixo nível é transmitida na rede local e é da responsabilidade de um servidor na rede responder com uma resposta RARP, que contém um endereço IP atribuído dinamicamente.

Embora a RARP ofereça um serviço de alocação dinâmica de endereços IP, tem várias deficiências. A deficiência mais gritante é que o RARP apenas fornece uma atribuição dinâmica do endereço IP. Na maioria das situações, é necessária mais informação para que um dispositivo participe adequadamente numa rede. Além de um endereço IP, a maioria dos dispositivos precisa da máscara de rede e do endereço IP gateway. O endereço IP de um servidor DNS e outras informações de rede também podem ser necessários. A RARP não tem a capacidade de fornecer esta informação.

## <a name="rarp-alternatives"></a>Alternativas RARP

Para superar as deficiências da RARP, os investigadores desenvolveram um mecanismo de atribuição de endereços IP mais abrangente chamado Protocolo de Bootstrap (BOOTP). Este protocolo tem a capacidade de alocar dinamicamente um endereço IP e também fornecer informações adicionais importantes de rede. No entanto, o BOOTP tem a desvantagem de ser projetado para configurações de rede estática. Não permite uma atribuição rápida ou automatizada de endereços.

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

O Servidor DHCP utiliza o protocolo UDP para receber pedidos do Cliente DHCP e transmitir respostas. Antes de ter um endereço IP, as mensagens UDP que transportam as informações do DHCP são enviadas e recebidas utilizando o endereço de transmissão IP de 255.255.255.255.255. No entanto, se o Cliente souber o endereço do Servidor DHCP, poderá enviar mensagens DHCP utilizando mensagens unicast.

## <a name="dhcp-server-state-machine"></a>Máquina de estado do servidor DHCP

O Servidor DHCP é implementado como uma máquina estatal de duas etapas processada por um fio DHCP interno que é criado durante *nx_dhcp_server_create* processamento. Os principais estados do Servidor DHCP são 1) recebendo uma mensagem DISCOVER de um cliente DHCP e 2) recebendo uma mensagem REQUEST.

Abaixo estão os correspondentes estados do Cliente DHCP:

- **NX_DHCP_STATE_BOOT** Começando com um endereço IP anterior
- **NX_DHCP_STATE_INIT** Começando sem o valor do endereço IP anterior
- **NX_DHCP_STATE_SELECTING** À espera de uma resposta de qualquer servidor DHCP
- **NX_DHCP_STATE_REQUESTING** Servidor DHCP identificado, pedido de endereço IP enviado
- **NX_DHCP_STATE_BOUND** DhCP IP Endereço de arrendamento estabelecido
- **NX_DHCP_STATE_RENEWING** DHCP IP Endereço prazo de renovação de contrato decorrido, renovação solicitada
- **NX_DHCP_STATE_REBINDING** DHCP IP Endereço de locação reencambido tempo decorrido, renovação solicitada
- **NX_DHCP_STATE_FORCERENEW** DHCP IP Endereço de arrendamento estabelecido, renovação forçada por servidor ou por aplicação
- **NX_DHCP_STATE_FAILED** Nenhum servidor encontrado ou nenhuma resposta do servidor recebido

## <a name="dhcp-additional-parameters"></a>Parâmetros adicionais do DHCP

O NetX Duo DHCP Server tem uma lista predefinição de parâmetros de opção que está definido na opção configurável NX_DHCP_DEFAULT_SERVER_OPTION_LIST em *nxd_dhcp_server.h* para fornecer aos Clientes DHCP parâmetros de configuração de rede comuns/críticos, por exemplo, router ou endereço de gateway e servidor DNS para o Cliente DHCP.

## <a name="dhcp-rfcs"></a>DHCP RFCs

O NetX Duo DHCP Server está em conformidade com o RFC2132, RFC2131 e RFCs relacionados.
