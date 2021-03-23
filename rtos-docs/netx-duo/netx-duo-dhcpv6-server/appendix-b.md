---
title: Apêndice B - Códigos de estado do servidor Azure RTOS NetX Duo DHCPv6
description: Este capítulo contém uma descrição de todos os códigos de estado do servidor NetX Duo DHCPv6
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7c79a0c0bc9acfcfca69c7333d30cd7cab35ba5f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826059"
---
# <a name="appendix-b---azure-rtos-netx-duo-dhcpv6-server-status-codes"></a>Apêndice B - Códigos de estado do servidor Azure RTOS NetX Duo DHCPv6

| Name              | Código            | Descrição |
| ------------------- | ------------------- | --------------- |
| Com êxito | 0 | Com êxito |
| Falha não especificada | 1 | Falha, razão não especificada; este código de estado é definido pelo Servidor para indicar uma falha geral na concessão do pedido do Cliente que não corresponde aos outros códigos |
| NoAddress Disponível | 2 | O servidor não tem endereços disponíveis para atribuir ao Cliente |
| NoBinding | 3 | O endereço IA do Cliente (binding) não está disponível, por exemplo, o endereço IP solicitado não está disponível para o Servidor arrendar ou atribuir a outro Cliente. |
| NotOnLink | 4 | O prefixo do endereço indica que o endereço IP não é um endereço de ligação |
| UseMultica | 5 | Enviado por um Servidor em resposta a receber uma mensagem do Cliente utilizando o endereço unicast do Servidor em vez do *All_DHCP_Relay_Agents_and_Servers* endereço multicast |