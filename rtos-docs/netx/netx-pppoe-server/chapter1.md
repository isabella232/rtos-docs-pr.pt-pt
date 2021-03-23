---
title: Capítulo 1 - Introdução ao Azure RTOS NetX PPPoE Server
description: Este documento centra-se nos detalhes do módulo Azure RTOS NetX PPPoE.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 85a762f669e31c7e753f78b270ced15677a87c4c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826611"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pppoe-server"></a><span data-ttu-id="46ed6-103">Capítulo 1 - Introdução ao Azure RTOS NetX PPPoE Server</span><span class="sxs-lookup"><span data-stu-id="46ed6-103">Chapter 1 - Introduction to Azure RTOS NetX PPPoE Server</span></span>

<span data-ttu-id="46ed6-104">PPP sobre Ethernet (PPPoE) permite que os anfitriões conectem ao servidor PPP via Ethernet em vez da comunicação tradicional da linha de série baseada em caracteres.</span><span class="sxs-lookup"><span data-stu-id="46ed6-104">PPP over Ethernet (PPPoE) allows hosts to connect to PPP server via Ethernet instead of the traditional character-based serial line communication.</span></span> <span data-ttu-id="46ed6-105">Os detalhes técnicos do PPPoE são descritos no RFC 2516: Um Método de Transmissão de PPP sobre Ethernet (PPPoE).</span><span class="sxs-lookup"><span data-stu-id="46ed6-105">The technical details of PPPoE are described in RFC 2516: A Method for Transmitting PPP over Ethernet (PPPoE).</span></span> <span data-ttu-id="46ed6-106">Este documento centra-se nos detalhes do módulo Azure RTOS NetX PPPoE.</span><span class="sxs-lookup"><span data-stu-id="46ed6-106">This document focuses on the details of Azure RTOS NetX PPPoE module.</span></span>

<span data-ttu-id="46ed6-107">Para fornecer uma ligação ponto-a-ponto sobre o Ethernet, cada sessão de PPP deve aprender o endereço Ethernet do par remoto, bem como estabelecer um identificador de sessão único.</span><span class="sxs-lookup"><span data-stu-id="46ed6-107">To provide a point-to-point connection over Ethernet, each PPP session must learn the Ethernet address of the remote peer, as well as establish a unique session identifier.</span></span>

<span data-ttu-id="46ed6-108">De acordo com o RFC 2516, o PPPoE é composto por duas etapas: a fase Discovery e o palco PPPoE Session.</span><span class="sxs-lookup"><span data-stu-id="46ed6-108">According to RFC 2516, PPPoE consists of two stages: the Discovery stage, and PPPoE Session stage.</span></span> <span data-ttu-id="46ed6-109">Quando um anfitrião (cliente) deseja iniciar uma sessão de PPP, tem primeiro de executar a Discovery para encontrar o servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="46ed6-109">When a host (client) wishes to start a PPP session, it must first perform Discovery to find PPPoE server.</span></span> <span data-ttu-id="46ed6-110">Este passo também permite que o servidor e o cliente identifiquem o endereço Ethernet MAC e SESSION_ID, que serão utilizados para o resto da sessão de PPP.</span><span class="sxs-lookup"><span data-stu-id="46ed6-110">This step also allows the server and the client to identify each other's Ethernet MAC address and SESSION_ID, which will be used for the rest of the PPP session.</span></span>

<span data-ttu-id="46ed6-111">Um quadro Ethernet é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="46ed6-111">An Ethernet frame is as follows:</span></span>

![Diagrama mostrando uma moldura Ethernet.](media/netx-pppoe-server-01.png)

<span data-ttu-id="46ed6-113">A carga útil do Ethernet para PPPoE é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="46ed6-113">The Ethernet payload for PPPoE is as follows:</span></span>

![Diagrama mostrando uma carga de ethernet para PPPoE.](media/netx-pppoe-server-02.png)

## <a name="pppoe-discovery-stage"></a><span data-ttu-id="46ed6-115">Fase de Descoberta ppPoe</span><span class="sxs-lookup"><span data-stu-id="46ed6-115">PPPoE Discovery Stage</span></span>

<span data-ttu-id="46ed6-116">A fase PPPoE Discovery permite que os clientes selecionem um servidor de todos os servidores disponíveis na rede, efetivamente para criar uma sessão antes da troca de quadros de PPP.</span><span class="sxs-lookup"><span data-stu-id="46ed6-116">The PPPoE Discovery stage allows clients to select a server from all available servers on the network, effectively to create a session prior to PPP frames being exchanged.</span></span> <span data-ttu-id="46ed6-117">No final da fase de descoberta, tanto o cliente como o servidor concordarão com um ID de sessão único, e ambos os lados precisam de saber o endereço MAC do par.</span><span class="sxs-lookup"><span data-stu-id="46ed6-117">At the end of the discovery stage, both the client and the server shall agree on a unique session ID, and both sides need to know peer's MAC address.</span></span>

| <span data-ttu-id="46ed6-118">Mensagem de Descoberta</span><span class="sxs-lookup"><span data-stu-id="46ed6-118">Discovery Message</span></span>                                  | <span data-ttu-id="46ed6-119">Código</span><span class="sxs-lookup"><span data-stu-id="46ed6-119">Code</span></span> | <span data-ttu-id="46ed6-120">Direção</span><span class="sxs-lookup"><span data-stu-id="46ed6-120">Direction</span></span>                                     |
| -------------------------------------------------- | ---- | --------------------------------------------- |
| <span data-ttu-id="46ed6-121">Iniciação da descoberta ativa ppPoe (PADI)</span><span class="sxs-lookup"><span data-stu-id="46ed6-121">PPPoE Active Discovery Initiation (PADI)</span></span>           | <span data-ttu-id="46ed6-122">0x09</span><span class="sxs-lookup"><span data-stu-id="46ed6-122">0x09</span></span> | <span data-ttu-id="46ed6-123">Do Cliente à transmissão</span><span class="sxs-lookup"><span data-stu-id="46ed6-123">From Client to broadcast</span></span>                      |
| <span data-ttu-id="46ed6-124">Oferta de descoberta ativa ppPoe (PADO)</span><span class="sxs-lookup"><span data-stu-id="46ed6-124">PPPoE Active Discovery Offer (PADO)</span></span>                | <span data-ttu-id="46ed6-125">0x07</span><span class="sxs-lookup"><span data-stu-id="46ed6-125">0x07</span></span> | <span data-ttu-id="46ed6-126">De Servidor a Cliente</span><span class="sxs-lookup"><span data-stu-id="46ed6-126">From Server to Client</span></span>                         |
| <span data-ttu-id="46ed6-127">Pedido de descoberta ativa ppPoe (PADR)</span><span class="sxs-lookup"><span data-stu-id="46ed6-127">PPPoE Active Discovery Request (PADR)</span></span>              | <span data-ttu-id="46ed6-128">0x19</span><span class="sxs-lookup"><span data-stu-id="46ed6-128">0x19</span></span> | <span data-ttu-id="46ed6-129">De Cliente a Servidor</span><span class="sxs-lookup"><span data-stu-id="46ed6-129">From Client to Server</span></span>                         |
| <span data-ttu-id="46ed6-130">Pppoe Ative Discovery Sessão de confirmação (PADS)</span><span class="sxs-lookup"><span data-stu-id="46ed6-130">PPPOE Active Discovery Session-confirmation (PADS)</span></span> | <span data-ttu-id="46ed6-131">0x65</span><span class="sxs-lookup"><span data-stu-id="46ed6-131">0x65</span></span> | <span data-ttu-id="46ed6-132">De Servidor a Cliente</span><span class="sxs-lookup"><span data-stu-id="46ed6-132">From Server to Client</span></span>                         |
| <span data-ttu-id="46ed6-133">PPPoe Ative Discovery Terminate (PADT)</span><span class="sxs-lookup"><span data-stu-id="46ed6-133">PPPoE Active Discovery Terminate (PADT)</span></span>            | <span data-ttu-id="46ed6-134">0xa7</span><span class="sxs-lookup"><span data-stu-id="46ed6-134">0xa7</span></span> | <span data-ttu-id="46ed6-135">Pode ser iniciado a partir de servidor ou cliente</span><span class="sxs-lookup"><span data-stu-id="46ed6-135">Can be initiated from either server or client</span></span> |

<span data-ttu-id="46ed6-136">Todos os quadros discovery Ethernet têm o campo de ETHER_TYPE definido para o valor 0x8863.</span><span class="sxs-lookup"><span data-stu-id="46ed6-136">All Discovery Ethernet frames have the ETHER_TYPE field set to the value 0x8863.</span></span>

## <a name="pppoe-session-message"></a><span data-ttu-id="46ed6-137">Mensagem de sessão pppoe</span><span class="sxs-lookup"><span data-stu-id="46ed6-137">PPPoE Session Message</span></span>

<span data-ttu-id="46ed6-138">Após o cliente e o servidor criarem uma sessão, os quadros de PPP podem ser transferidos como mensagens PPPoE Session.</span><span class="sxs-lookup"><span data-stu-id="46ed6-138">After the client and the server create a session, PPP frames can be transferred as PPPoE Session messages.</span></span> <span data-ttu-id="46ed6-139">Durante uma sessão, o SESSION_ID não deve ser alterado e deve ser o valor atribuído pelo servidor durante a fase Discovery.</span><span class="sxs-lookup"><span data-stu-id="46ed6-139">During a session, the SESSION_ID must not change and must be the value the server assigned during the Discovery stage.</span></span>

<span data-ttu-id="46ed6-140">Todos os quadros Ethernet da Sessão PPPoE têm o campo ETHER_TYPE definido para o valor 0x8864.</span><span class="sxs-lookup"><span data-stu-id="46ed6-140">All PPPoE Session Ethernet frames have the ETHER_TYPE field set to the value 0x8864.</span></span>