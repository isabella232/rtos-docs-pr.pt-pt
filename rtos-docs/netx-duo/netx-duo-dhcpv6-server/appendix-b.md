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
# <a name="appendix-b---azure-rtos-netx-duo-dhcpv6-server-status-codes"></a><span data-ttu-id="11f54-103">Apêndice B - Códigos de estado do servidor Azure RTOS NetX Duo DHCPv6</span><span class="sxs-lookup"><span data-stu-id="11f54-103">Appendix B - Azure RTOS NetX Duo DHCPv6 server status codes</span></span>

| <span data-ttu-id="11f54-104">Name</span><span class="sxs-lookup"><span data-stu-id="11f54-104">Name</span></span>              | <span data-ttu-id="11f54-105">Código</span><span class="sxs-lookup"><span data-stu-id="11f54-105">Code</span></span>            | <span data-ttu-id="11f54-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="11f54-106">Description</span></span> |
| ------------------- | ------------------- | --------------- |
| <span data-ttu-id="11f54-107">Com êxito</span><span class="sxs-lookup"><span data-stu-id="11f54-107">Success</span></span> | <span data-ttu-id="11f54-108">0</span><span class="sxs-lookup"><span data-stu-id="11f54-108">0</span></span> | <span data-ttu-id="11f54-109">Com êxito</span><span class="sxs-lookup"><span data-stu-id="11f54-109">Success</span></span> |
| <span data-ttu-id="11f54-110">Falha não especificada</span><span class="sxs-lookup"><span data-stu-id="11f54-110">Unspecified Failure</span></span> | <span data-ttu-id="11f54-111">1</span><span class="sxs-lookup"><span data-stu-id="11f54-111">1</span></span> | <span data-ttu-id="11f54-112">Falha, razão não especificada; este código de estado é definido pelo Servidor para indicar uma falha geral na concessão do pedido do Cliente que não corresponde aos outros códigos</span><span class="sxs-lookup"><span data-stu-id="11f54-112">Failure, reason unspecified; this status code is set by the Server to indicate a general failure in granting the Client request not matching the other codes</span></span> |
| <span data-ttu-id="11f54-113">NoAddress Disponível</span><span class="sxs-lookup"><span data-stu-id="11f54-113">NoAddress Available</span></span> | <span data-ttu-id="11f54-114">2</span><span class="sxs-lookup"><span data-stu-id="11f54-114">2</span></span> | <span data-ttu-id="11f54-115">O servidor não tem endereços disponíveis para atribuir ao Cliente</span><span class="sxs-lookup"><span data-stu-id="11f54-115">Server has no addresses available to assign to the Client</span></span> |
| <span data-ttu-id="11f54-116">NoBinding</span><span class="sxs-lookup"><span data-stu-id="11f54-116">NoBinding</span></span> | <span data-ttu-id="11f54-117">3</span><span class="sxs-lookup"><span data-stu-id="11f54-117">3</span></span> | <span data-ttu-id="11f54-118">O endereço IA do Cliente (binding) não está disponível, por exemplo, o endereço IP solicitado não está disponível para o Servidor arrendar ou atribuir a outro Cliente.</span><span class="sxs-lookup"><span data-stu-id="11f54-118">Client IA address (binding) is not available e.g. the requested IP address is not available for the Server to lease or assigned to another Client.</span></span> |
| <span data-ttu-id="11f54-119">NotOnLink</span><span class="sxs-lookup"><span data-stu-id="11f54-119">NotOnLink</span></span> | <span data-ttu-id="11f54-120">4</span><span class="sxs-lookup"><span data-stu-id="11f54-120">4</span></span> | <span data-ttu-id="11f54-121">O prefixo do endereço indica que o endereço IP não é um endereço de ligação</span><span class="sxs-lookup"><span data-stu-id="11f54-121">The prefix for the address indicates the IP address is not an on link address</span></span> |
| <span data-ttu-id="11f54-122">UseMultica</span><span class="sxs-lookup"><span data-stu-id="11f54-122">UseMulticast</span></span> | <span data-ttu-id="11f54-123">5</span><span class="sxs-lookup"><span data-stu-id="11f54-123">5</span></span> | <span data-ttu-id="11f54-124">Enviado por um Servidor em resposta a receber uma mensagem do Cliente utilizando o endereço unicast do Servidor em vez do *All_DHCP_Relay_Agents_and_Servers* endereço multicast</span><span class="sxs-lookup"><span data-stu-id="11f54-124">Sent by a Server in response to receiving a Client message using the Server’s unicast address instead of the *All_DHCP_Relay_Agents_and_Servers* multicast address</span></span> |