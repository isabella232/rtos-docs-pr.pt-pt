---
title: Apêndice A – Códigos de opção Azure RTOS NetX Duo DHCPv6
description: Este capítulo contém uma descrição de todos os códigos de opção NetX Duo DHCPv6
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 58b6e36fab4de02a9fb973894500a48f2656809ec2baa3dfc65fcd80ae33b832
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791839"
---
# <a name="appendix-a--azure-rtos-netx-duo-dhcpv6-option-codes"></a>Apêndice A – Códigos de opção Azure RTOS NetX Duo DHCPv6

| Opção              | Código            | Descrição |
| ------------------- | ------------------- | --------------- |
| Identificador de cliente DUID | 1 | Identifica exclusivamente um anfitrião do Cliente na rede |
| Identificador de servidor (DUID) | 2 | Identifica exclusivamente o hospedeiro DHCPv6Server na rede |
| Associação de Identidade para Endereços Não Temporários (IANA) | 3 | Parâmetros para uma atribuição de endereço IP não temporário |
| Associação de Identidade para Endereços Temporários (IATA) | 4 | Parâmetros para uma atribuição temporária de endereço IP |
| Endereço IA | 5 | Endereço IPv6 real e vida útil de endereço IPv6 a atribuir ao Cliente |
| Pedido de Opção | 6 | Uma lista de pedidos de informação para obter informações de rede, como servidor DNS e outros parâmetros de configuração de rede. |
| Preferência | 7 | Incluído no servidor Enviar por palavra de forma positiva ao cliente para influenciar a escolha dos servidores do Cliente. O Cliente deve escolher um servidor com maior valor de preferência em relação a outros servidores. 255 é o valor máximo, enquanto zero indica que o cliente pode escolher qualquer servidor que responda a eles |
| Tempo decorrido | 8 | Contém o tempo (em 0,01 segundos) quando o Cliente inicia a troca DHCPv6 com o servidor. Utilizado por servidores secundários para determinar se o servidor primário responde a tempo ao pedido do Cliente. |
| Mensagem de retransmissão | 9 | Contém a mensagem original na mensagem de retransmissão | 
| Autenticação | 11 | Contém informações para autenticar a identidade e o conteúdo das mensagens DHCPv6 |
| Servidor Unicast | 12 | O servidor envia esta opção para informar o Cliente de que o servidor aceitará mensagens unicast diretamente do Cliente em vez de multicast. |

As opções IATA, Relay Message, Authentication e Server Unicast não são suportadas nesta versão do NetX Duo DHCPv6 Server. O atual código de opção do protocolo DHCPv6 10 é deixado indefinido no RFC 3315.