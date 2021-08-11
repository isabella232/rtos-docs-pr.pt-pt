---
title: Apêndice B - Códigos de estado do servidor Azure RTOS NetX Duo DHCPv6
description: Este capítulo contém uma descrição de todos os códigos de estado do servidor NetX Duo DHCPv6
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8b9795607c0fed80646ee01e36edf4ecd2aaadad7f0a023e6979e123b81e1660
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791777"
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