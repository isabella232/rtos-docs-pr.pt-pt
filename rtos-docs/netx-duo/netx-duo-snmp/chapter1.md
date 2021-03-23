---
title: Capítulo 1 - Introdução ao Azure RTOS NetX Duo SNMP
description: A implementação do SNMP da NetX Duo é a de um Agente SNMP. Um agente é responsável por responder aos comandos do SNMP Manager e enviar armadilhas conduzidas por eventos.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5760e35fdbe8d7b27e2ccc82abac37b1f6fb5118
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825783"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-snmp"></a><span data-ttu-id="d3cc1-104">Capítulo 1 - Introdução ao Azure RTOS NetX Duo SNMP</span><span class="sxs-lookup"><span data-stu-id="d3cc1-104">Chapter 1 - Introduction to Azure RTOS NetX Duo SNMP</span></span>

<span data-ttu-id="d3cc1-105">O Simple Network Management Protocol (SNMP) é um protocolo concebido para gerir dispositivos na internet.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-105">The Simple Network Management Protocol (SNMP) is a protocol designed for managing devices on the internet.</span></span> <span data-ttu-id="d3cc1-106">O SNMP é um protocolo que utiliza os serviços do Protocolo de Datagramgram do Utilizador sem Ligação (UDP) para desempenhar a sua função de gestão.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-106">SNMP is a protocol that utilizes the connectionless User Datagram Protocol (UDP) services to perform its management function.</span></span> <span data-ttu-id="d3cc1-107">A implementação do Azure RTOS NetX Duo SNMP é a de um Agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-107">The Azure RTOS NetX Duo SNMP implementation is that of an SNMP Agent.</span></span> <span data-ttu-id="d3cc1-108">Um agente é responsável por responder aos comandos do SNMP Manager e enviar armadilhas conduzidas por eventos.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-108">An agent is responsible for responding to SNMP Manager’s commands and sending event driven traps.</span></span> 

<span data-ttu-id="d3cc1-109">O NetX Duo SNMP suporta a comunicação IPv4 e IPv6 com os Gestores SNMP.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-109">NetX Duo SNMP supports both IPv4 and IPv6 communication with SNMP Managers.</span></span> <span data-ttu-id="d3cc1-110">As aplicações NetX SNMP devem compilar e executar no NetX Duo SNMP.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-110">NetX SNMP applications should compile and run in NetX Duo SNMP.</span></span> <span data-ttu-id="d3cc1-111">No entanto, o desenvolvedor é encorajado a apresentar aplicações SNMP existentes para usar os serviços equivalentes de "duo".</span><span class="sxs-lookup"><span data-stu-id="d3cc1-111">However, the developer is encouraged to port existing SNMP applications to using the equivalent “duo” services.</span></span> <span data-ttu-id="d3cc1-112">Por exemplo, ao enviar mensagens de armadilha SNMP, os seguintes serviços de 'duo' devem substituir o seu equivalente NetX:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-112">For example, when sending SNMP trap messages, the following ‘duo’ services should replace their NetX equivalent:</span></span>

<span data-ttu-id="d3cc1-113">*nxd_snmp_object_trap_send*</span><span class="sxs-lookup"><span data-stu-id="d3cc1-113">*nxd_snmp_object_trap_send*</span></span>

<span data-ttu-id="d3cc1-114">*nxd_snmp_object_trapv2_send*</span><span class="sxs-lookup"><span data-stu-id="d3cc1-114">*nxd_snmp_object_trapv2_send*</span></span>

<span data-ttu-id="d3cc1-115">*nxd_snmp_object_trapv3_send*</span><span class="sxs-lookup"><span data-stu-id="d3cc1-115">*nxd_snmp_object_trapv3_send*</span></span>

<span data-ttu-id="d3cc1-116">Para mais detalhes, consulte **descrição dos Serviços de Agentes da SNMP** em outros lugares neste Manual do Utilizador para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-116">For more details, see **Description of SNMP Agent Services** elsewhere in this User Guide for more details.</span></span>

## <a name="netx-duo-snmp-agent-requirements"></a><span data-ttu-id="d3cc1-117">Requisitos do agente SNMP da NetX Duo</span><span class="sxs-lookup"><span data-stu-id="d3cc1-117">NetX Duo SNMP Agent Requirements</span></span>

<span data-ttu-id="d3cc1-118">O pacote NetX Duo SNMP requer que já tenha sido criada uma instância IP.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-118">The NetX Duo SNMP package requires that an IP instance has already been created.</span></span> <span data-ttu-id="d3cc1-119">Além disso, a UDP deve ser ativada nessa mesma instância DEP.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-119">In addition, UDP must be enabled on that same IP instance.</span></span>

<span data-ttu-id="d3cc1-120">O Agente SNMP da NetX Duo tem vários requisitos adicionais.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-120">The NetX Duo SNMP Agent has several additional requirements.</span></span> <span data-ttu-id="d3cc1-121">Em primeiro lugar, requer acesso ao porto 161 para lidar com todos os pedidos do gestor do SNMP.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-121">First, it requires access to port 161 for handling all SNMP manager requests.</span></span> <span data-ttu-id="d3cc1-122">Também requer acesso à porta 162 para o envio de mensagens de armadilha para o Gestor.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-122">It also requires access to port 162 for sending trap messages to the Manager.</span></span>

<span data-ttu-id="d3cc1-123">Para utilizar o Agente SNMP NetX Duo com mais de IPv6 e para obter objetos IPv6, o IPv6 deve ser ativado no NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-123">To use NetX Duo SNMP Agent with over IPv6 and to obtain IPv6 objects, IPv6 must be enabled in NetX Duo.</span></span> <span data-ttu-id="d3cc1-124">Consulte o Guia de ***Utilizador netX Duo*** para obter mais informações sobre como ativar a instância IP para os serviços IPv6.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-124">See the ***NetX Duo User Guide*** for details on enabling the IP instance for IPv6 services.</span></span>

## <a name="netx-duo-snmp-constraints"></a><span data-ttu-id="d3cc1-125">Restrições SNMP da NetX Duo</span><span class="sxs-lookup"><span data-stu-id="d3cc1-125">NetX Duo SNMP Constraints</span></span>

<span data-ttu-id="d3cc1-126">O protocolo NetX Duo SNMP implementa as versões 1, 2 e 3 da SNMP.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-126">The NetX Duo SNMP protocol implements SNMP Version 1, 2, and 3.</span></span> <span data-ttu-id="d3cc1-127">A implementação do SNMPv3 suporta a autenticação MD5 e SHA e a encriptação DES.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-127">The SNMPv3 implementation supports MD5 and SHA authentication, and DES encryption.</span></span> <span data-ttu-id="d3cc1-128">Esta versão do Agente SNMP Da NetX Duo tem os seguintes constrangimentos:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-128">This version of the NetX Duo SNMP Agent has the following constraints:</span></span>

1. <span data-ttu-id="d3cc1-129">Um agente SNMP por Instância IP NetX</span><span class="sxs-lookup"><span data-stu-id="d3cc1-129">One SNMP Agent per NetX IP Instance</span></span>
2. <span data-ttu-id="d3cc1-130">Sem apoio para a RMON</span><span class="sxs-lookup"><span data-stu-id="d3cc1-130">No support for RMON</span></span>
3. <span data-ttu-id="d3cc1-131">SNMP v3 Inform mensagens não são suportadas</span><span class="sxs-lookup"><span data-stu-id="d3cc1-131">SNMP v3 Inform messages are not supported</span></span>
4. <span data-ttu-id="d3cc1-132">Os tipos de dados opacos e NSAP não são suportados</span><span class="sxs-lookup"><span data-stu-id="d3cc1-132">OPAQUE and NSAP data types are not supported</span></span>
5. <span data-ttu-id="d3cc1-133">Os endereços IPv6 são definidos como cordas de octeto, e a verificação de formato é deixada para a aplicação.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-133">IPv6 addresses are defined as octet strings, and format checking is left to the application.</span></span>

## <a name="snmp-object-names"></a><span data-ttu-id="d3cc1-134">Nomes de objetos SNMP</span><span class="sxs-lookup"><span data-stu-id="d3cc1-134">SNMP Object Names</span></span>

<span data-ttu-id="d3cc1-135">O protocolo SNMP foi concebido para gerir dispositivos na internet.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-135">The SNMP protocol is designed to manage devices on the internet.</span></span> <span data-ttu-id="d3cc1-136">Para isso, cada dispositivo gerido pelo SNMP tem um conjunto de objetos que são definidos pela Estrutura de Informação de Gestão (SMI) conforme definido pelo RFC 1155.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-136">To accomplish this, each SNMP managed device has a set of objects that are defined by the Structure of Management Information (SMI) as defined by RFC 1155.</span></span> <span data-ttu-id="d3cc1-137">A estrutura é um tipo hierárquico de estrutura que se parece com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-137">The structure is a hierarchical tree type of structure that looks like the following:</span></span>

![Diagrama da Estrutura de Informação de Gestão.](media/image3.png)

<span data-ttu-id="d3cc1-139">Cada nó na árvore é um objeto.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-139">Each node in the tree is an object.</span></span> <span data-ttu-id="d3cc1-140">O objeto "dod" na árvore é identificado pela notação 1.3.6, enquanto o objeto "internet" na árvore é identificado pela notação 1.3.6.1.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-140">The “dod” object in the tree is identified by the notation 1.3.6, while the “internet” object in the tree is identified by the notation 1.3.6.1.</span></span> <span data-ttu-id="d3cc1-141">Todos os nomes dos objetos SNMP começam com a notação 1.3.6.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-141">All SNMP object names begin with the notation 1.3.6.</span></span>

<span data-ttu-id="d3cc1-142">Um Gestor SNMP utiliza esta notação de objetos para especificar que objeto no dispositivo deseja obter ou definir.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-142">An SNMP Manager uses this object notation to specify what object in the device it wishes to get or set.</span></span> <span data-ttu-id="d3cc1-143">O Agente SNMP da NetX Duo interpreta tais pedidos de gerente e fornece mecanismos para a aplicação para realizar a operação solicitada.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-143">The NetX Duo SNMP Agent interprets such manager requests and provides mechanisms for the application to perform the requested operation.</span></span>

## <a name="snmp-manager-requests"></a><span data-ttu-id="d3cc1-144">Pedidos do Gerente SNMP</span><span class="sxs-lookup"><span data-stu-id="d3cc1-144">SNMP Manager Requests</span></span>

<span data-ttu-id="d3cc1-145">O SNMP tem um mecanismo simples de gestão de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-145">The SNMP has a simple mechanism for managing devices.</span></span> <span data-ttu-id="d3cc1-146">Existe um conjunto de comandos SNMP padrão que são emitidos pelo SNMP Manager para o dispositivo SNMP na *porta 161*.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-146">There is a set of standard SNMP commands that are issued by the SNMP Manager to the SNMP device on *port 161*.</span></span> <span data-ttu-id="d3cc1-147">O seguinte mostra alguns dos comandos básicos do SNMP Manager:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-147">The following shows some of the basic SNMP Manager commands:</span></span>

| <span data-ttu-id="d3cc1-148">Comando SNMP</span><span class="sxs-lookup"><span data-stu-id="d3cc1-148">SNMP Command</span></span> | <span data-ttu-id="d3cc1-149">Significado</span><span class="sxs-lookup"><span data-stu-id="d3cc1-149">Meaning</span></span>                                                        |
|--------------|----------------------------------------------------------------|
| <span data-ttu-id="d3cc1-150">GET</span><span class="sxs-lookup"><span data-stu-id="d3cc1-150">GET</span></span>          | <span data-ttu-id="d3cc1-151">*Obtenha o objeto especificado*</span><span class="sxs-lookup"><span data-stu-id="d3cc1-151">*Get the specified object*</span></span>                                       |
| <span data-ttu-id="d3cc1-152">GETNEXT</span><span class="sxs-lookup"><span data-stu-id="d3cc1-152">GETNEXT</span></span>      | <span data-ttu-id="d3cc1-153">*Obtenha o próximo objeto lógico após o ID do objeto especificado*</span><span class="sxs-lookup"><span data-stu-id="d3cc1-153">*Get the next logical object after the specified object ID*</span></span>      |
| <span data-ttu-id="d3cc1-154">GETBULK</span><span class="sxs-lookup"><span data-stu-id="d3cc1-154">GETBULK</span></span>      | <span data-ttu-id="d3cc1-155">*Obtenha os múltiplos objetos lógicos após o ID do objeto especificado*</span><span class="sxs-lookup"><span data-stu-id="d3cc1-155">*Get the multiple logical objects after the specified object ID*</span></span> |
| <span data-ttu-id="d3cc1-156">SET</span><span class="sxs-lookup"><span data-stu-id="d3cc1-156">SET</span></span>          | <span data-ttu-id="d3cc1-157">*Desajei o objeto especificado*</span><span class="sxs-lookup"><span data-stu-id="d3cc1-157">*Set the specified object*</span></span>                                       |

<span data-ttu-id="d3cc1-158">Estes comandos estão codificados no formato Notação De Sintaxe Abstrata Um (ASN.1) e residem na carga útil do pacote UDP enviado pelo SNMP Manager.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-158">These commands are encoded in the Abstract Syntax Notation One (ASN.1) format and reside in the payload of the UDP packet sent by the SNMP Manager.</span></span> <span data-ttu-id="d3cc1-159">O Agente SNMP NetX Duo processa o pedido e, em seguida, chama a rotina de manuseamento correspondente especificada na chamada ***nx_snmp_agent_create.***</span><span class="sxs-lookup"><span data-stu-id="d3cc1-159">The NetX Duo SNMP Agent processes the request and then calls the corresponding handling routine specified in the ***nx_snmp_agent_create*** call.</span></span>

## <a name="netx-duo-snmp-agent-traps"></a><span data-ttu-id="d3cc1-160">Armadilhas de agente SNMP netx duo</span><span class="sxs-lookup"><span data-stu-id="d3cc1-160">NetX Duo SNMP Agent Traps</span></span>

<span data-ttu-id="d3cc1-161">O Agente SNMP da NetX Duo fornece a capacidade de alertar também um Gestor de Eventos SNMP de forma assíncronea.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-161">The NetX Duo SNMP Agent provides the ability to also alert an SNMP Manager of events asynchronously.</span></span> <span data-ttu-id="d3cc1-162">Isto é feito através de um comando de armadilha SNMP.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-162">This is done via an SNMP trap command.</span></span> <span data-ttu-id="d3cc1-163">Existe uma API única para cada versão do SNMP para o envio de armadilhas para um Gestor SNMP.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-163">There is a unique API for each version of SNMP for sending traps to an SNMP Manager.</span></span> <span data-ttu-id="d3cc1-164">Por predefinição, as armadilhas são enviadas para o SNMP Manager na porta 162.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-164">By default, the traps are sent to the SNMP Manager on port 162.</span></span>

<span data-ttu-id="d3cc1-165">O Agente SNMP NetX Duo fornece chaves de segurança separadas para mensagens de armadilha SNMPv3.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-165">The NetX Duo SNMP Agent provides separate security keys for SNMPv3 trap messages.</span></span> <span data-ttu-id="d3cc1-166">Para tal, a aplicação SNMP deve criar um conjunto separado de chaves das que são aplicadas às respostas aos pedidos do Gestor.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-166">To do so, the SNMP application must create a separate set of keys from those applied to responses to Manager requests.</span></span> <span data-ttu-id="d3cc1-167">A segurança do trap permite ao Agente SNMP utilizar as mesmas palavras-passe ou senhas diferentes para autenticação e privacidade.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-167">Trap security enables the SNMP Agent to use the same or different passwords for authentication and privacy.</span></span> <span data-ttu-id="d3cc1-168">Para obter mais informações sobre a criação de chaves de segurança, consulte **a Autenticação e Encriptação SNMP do NetX Duo** na secção seguinte.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-168">For more information on creating security keys, see **NetX Duo SNMP Authentication and Encryption** in the next section.</span></span>

<span data-ttu-id="d3cc1-169">Uma lista de variáveis de armadilha snmp padrão é enumerada no topo de *nxd_snmp.h:*</span><span class="sxs-lookup"><span data-stu-id="d3cc1-169">A list of standard SNMP trap variables is enumerated at the top of *nxd_snmp.h:*</span></span>

| <span data-ttu-id="d3cc1-170">Variáveis</span><span class="sxs-lookup"><span data-stu-id="d3cc1-170">Variables</span></span>                                 | <span data-ttu-id="d3cc1-171">Valor</span><span class="sxs-lookup"><span data-stu-id="d3cc1-171">Value</span></span>  |
|-------------------------------------------|---|
| <span data-ttu-id="d3cc1-172">#define NX_SNMP_TRAP_COLDSTART</span><span class="sxs-lookup"><span data-stu-id="d3cc1-172">#define NX_SNMP_TRAP_COLDSTART</span></span>            | <span data-ttu-id="d3cc1-173">0</span><span class="sxs-lookup"><span data-stu-id="d3cc1-173">0</span></span> |
| <span data-ttu-id="d3cc1-174">#define NX_SNMP_TRAP_WARMSTART</span><span class="sxs-lookup"><span data-stu-id="d3cc1-174">#define NX_SNMP_TRAP_WARMSTART</span></span>            | <span data-ttu-id="d3cc1-175">1</span><span class="sxs-lookup"><span data-stu-id="d3cc1-175">1</span></span> |
| <span data-ttu-id="d3cc1-176">#define NX_SNMP_TRAP_LINKDOWN</span><span class="sxs-lookup"><span data-stu-id="d3cc1-176">#define NX_SNMP_TRAP_LINKDOWN</span></span>             | <span data-ttu-id="d3cc1-177">2</span><span class="sxs-lookup"><span data-stu-id="d3cc1-177">2</span></span> |
| <span data-ttu-id="d3cc1-178">#define NX_SNMP_TRAP_LINKUP</span><span class="sxs-lookup"><span data-stu-id="d3cc1-178">#define NX_SNMP_TRAP_LINKUP</span></span>               | <span data-ttu-id="d3cc1-179">3</span><span class="sxs-lookup"><span data-stu-id="d3cc1-179">3</span></span> |
| <span data-ttu-id="d3cc1-180">#define NX_SNMP_TRAP_AUTHENTICATE_FAILURE</span><span class="sxs-lookup"><span data-stu-id="d3cc1-180">#define NX_SNMP_TRAP_AUTHENTICATE_FAILURE</span></span> | <span data-ttu-id="d3cc1-181">4</span><span class="sxs-lookup"><span data-stu-id="d3cc1-181">4</span></span> |
| <span data-ttu-id="d3cc1-182">#define NX_SNMP_TRAP_EGPNEIGHBORLOSS</span><span class="sxs-lookup"><span data-stu-id="d3cc1-182">#define NX_SNMP_TRAP_EGPNEIGHBORLOSS</span></span>      | <span data-ttu-id="d3cc1-183">5</span><span class="sxs-lookup"><span data-stu-id="d3cc1-183">5</span></span> |
| <span data-ttu-id="d3cc1-184">#define NX_SNMP_TRAP_ENTERPRISESPECIFIC</span><span class="sxs-lookup"><span data-stu-id="d3cc1-184">#define NX_SNMP_TRAP_ENTERPRISESPECIFIC</span></span>   | <span data-ttu-id="d3cc1-185">6</span><span class="sxs-lookup"><span data-stu-id="d3cc1-185">6</span></span> |

<span data-ttu-id="d3cc1-186">Para incluir estas variáveis na mensagem de armadilha, o argumento de entrada trap_type em *nx_snmp_agent_trapv2_send* (SNMPv2) ou *nx_snmp_agent_trapv3_send* (SNMPv3) é definido para o valor enumerado destas variáveis.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-186">To include these variables in the trap message, the trap_type input argument in *nx_snmp_agent_trapv2_send* (SNMPv2) or *nx_snmp_agent_trapv3_send* (SNMPv3) is set to the enumerated value of these variables.</span></span> <span data-ttu-id="d3cc1-187">Um exemplo é mostrado abaixo para o SNMPv2 notificar o Gerente SNMP de um evento de arranque a frio:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-187">An example is shown below for SNMPv2 to notify the SNMP Manager of a cold start event:</span></span>

```c
UINT trap_type = NX_SNMP_TRAP_COLDSTART;

status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                  (UCHAR *)"public", trap_type,
                                  tx_time_get(), NX_NULL);

```

<span data-ttu-id="d3cc1-188">Para incluir variáveis proprietárias na mensagem de armadilha, o argumento de entrada trap_type é definido para NX_SNMP_TRAP_CUSTOM e o argumento de entrada da lista de armadilhas contém os dados proprietários.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-188">To include proprietary variables in the trap message, the trap_type input argument is set to NX_SNMP_TRAP_CUSTOM and the trap list input argument contains the proprietary data.</span></span> <span data-ttu-id="d3cc1-189">Note que a mensagem da armadilha conterá como o tempo de subida do sistema (1.3.6.1.6.3.1.1.4.1.0).</span><span class="sxs-lookup"><span data-stu-id="d3cc1-189">Note that the trap message will contain as the system up time (1.3.6.1.6.3.1.1.4.1.0).</span></span> <span data-ttu-id="d3cc1-190">Um exemplo é mostrado abaixo para SNMPv2:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-190">An example is shown below for SNMPv2:</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[3];
NX_SNMP_OBJECT_DATA trap_data0;

    /* Load the data into the OBJECT. */
    nx_snmp_object_id_get((void*)"1.3.6.1.4.1.7428.1.3.2.0", &trap_data0);

    /* Update the Trap Object with the object and OID. */
    trap_list[0].nx_snmp_object_string_ptr = (UCHAR *)"1.3.6.1.6.3.1.1.4.0";
    trap_list[0].nx_snmp_object_data  = &trap_data0;

    /* Null terminate the trap list. */
    trap_list[1].nx_snmp_object_string_ptr = NX_NULL;

    status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                      (UCHAR *)"trapduo",
                                      NX_SNMP_TRAP_CUSTOM,
                                      tx_time_get(), trap_list);
```

## <a name="netx-duo-snmp-authentication-and-encryption"></a><span data-ttu-id="d3cc1-191">Autenticação e Encriptação SNMP do Duo NetX</span><span class="sxs-lookup"><span data-stu-id="d3cc1-191">NetX Duo SNMP Authentication and Encryption</span></span>

<span data-ttu-id="d3cc1-192">Existem dois sabores de autenticação, nomeadamente *básicos* e *digeridos.*</span><span class="sxs-lookup"><span data-stu-id="d3cc1-192">There are two flavors of authentication, namely *basic* and *digest*.</span></span> <span data-ttu-id="d3cc1-193">A autenticação básica equivale a uma simples autenticação de *nome de utilizador* de texto simples encontrada em muitos protocolos.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-193">Basic authentication is equivalent to a simple plain text *username* authentication found in many protocols.</span></span> <span data-ttu-id="d3cc1-194">Na autenticação básica do SNMP, o utilizador limita-se a verificar se o nome de utilizador fornecido é válido para a realização de operações do SNMP.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-194">In SNMP basic authentication, the user simply verifies that the supplied username is valid for performing SNMP operations.</span></span> <span data-ttu-id="d3cc1-195">A autenticação básica é a única opção para as versões SNMP 1 e 2.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-195">Basic authentication is the only option for SNMP versions 1 and 2.</span></span>

<span data-ttu-id="d3cc1-196">A principal desvantagem da autenticação básica é que o nome de utilizador é transmitido em texto simples.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-196">The main disadvantage of basic authentication is the username is transmitted in plain text.</span></span> <span data-ttu-id="d3cc1-197">A autenticação digestiva SNMPv3 aborda este problema nunca transmitindo o nome de utilizador em texto simples.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-197">The SNMPv3 digest authentication addresses this problem by never transmitting the username in plain text.</span></span> <span data-ttu-id="d3cc1-198">Em vez disso, um algoritmo é usado para obter uma 'digestão' de 96 bits a partir do nome de utilizador, motor de contexto e outras informações.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-198">Instead, an algorithm is used to derive a 96-bit ‘digest’ from the username, context engine, and other information.</span></span> <span data-ttu-id="d3cc1-199">O Agente SNMP NetX Duo suporta algoritmos MD5 e SHA digest.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-199">The NetX Duo SNMP Agent supports both MD5 and SHA digest algorithms.</span></span>

<span data-ttu-id="d3cc1-200">Para ativar a autenticação, o Agente SNMP deve definir o seu ID do motor de contexto utilizando o serviço *nx_snmp_agent_context_engine_set.*</span><span class="sxs-lookup"><span data-stu-id="d3cc1-200">To enable authentication, the SNMP Agent must set its Context Engine ID using the *nx_snmp_agent_context_engine_set* service.</span></span> <span data-ttu-id="d3cc1-201">O ID do motor de contexto é utilizado na criação da chave de autenticação.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-201">The Context Engine ID is used in the creation of the authentication key.</span></span>

<span data-ttu-id="d3cc1-202">A encriptação dos dados SNMPv3 está disponível usando o algoritmo DES.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-202">Encryption of SNMPv3 data is available using the DES algorithm.</span></span> <span data-ttu-id="d3cc1-203">A encriptação requer que a autenticação seja ativada (não se pode encriptar dados sem definir os parâmetros de autenticação).</span><span class="sxs-lookup"><span data-stu-id="d3cc1-203">Encryption requires that authentication be enabled (one cannot encrypt data without setting the authentication parameters).</span></span>

<span data-ttu-id="d3cc1-204">Para criar chaves de autenticação e privacidade, são utilizadas as seguintes API:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-204">To create authentication and privacy keys, the following API are used:</span></span>

```c
UINT  _nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)

UINT  _nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)
```

<span data-ttu-id="d3cc1-205">Em seguida, o agente SNMP deve ser configurado para utilizar estas chaves.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-205">Next, the SNMP agent must be configured to use these keys.</span></span> <span data-ttu-id="d3cc1-206">Para registar uma chave com o agente SNMP, são utilizadas as seguintes API:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-206">To register a key with the SNMP agent, the following API are used:</span></span>

```c
UINT  _nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr,
                                          NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr,
                                    NX_SNMP_SECURITY_KEY *key)
```

<span data-ttu-id="d3cc1-207">Podem ser criadas teclas separadas para mensagens de armadilha.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-207">Separate keys can be created for trap messages.</span></span> <span data-ttu-id="d3cc1-208">Para aplicar chaves para mensagens de armadilha, estão disponíveis a seguinte API:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-208">To apply keys for trap messages the following API are available:</span></span>

```c
UINT  _nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)
```

<span data-ttu-id="d3cc1-209">Para desativar a autenticação ou encriptação para mensagens de resposta e envio de armadilhas, utilize estes serviços com a entrada do ponteiro chave definida para NU.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-209">To disable authentication or encryption for response messages and sending traps, use these services with the key pointer input set to NULL.</span></span>

## <a name="netx-duo-snmp-community-strings"></a><span data-ttu-id="d3cc1-210">Cordas comunitárias NetX Duo SNMP</span><span class="sxs-lookup"><span data-stu-id="d3cc1-210">NetX Duo SNMP Community Strings</span></span>

<span data-ttu-id="d3cc1-211">O Agente SNMP NetX Duo suporta cordas da comunidade pública e privada.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-211">The NetX Duo SNMP Agent supports both public and private community strings.</span></span> <span data-ttu-id="d3cc1-212">A corda pública está definida com o serviço *nx_snmp_agent _public_string_set.*</span><span class="sxs-lookup"><span data-stu-id="d3cc1-212">The public string is set with the *nx_snmp_agent _public_string_set* service.</span></span> <span data-ttu-id="d3cc1-213">A cadeia privada NetX Duo SNMP Agent está definida utilizando o serviço *nx_snmp_agent_private_string_set.*</span><span class="sxs-lookup"><span data-stu-id="d3cc1-213">The NetX Duo SNMP Agent private string is set using the *nx_snmp_agent_private_string_set* service.</span></span>

## <a name="netx-duo-snmp-username-callback"></a><span data-ttu-id="d3cc1-214">Retenção de nome de utilizador SNMP da NetX Duo SNMP</span><span class="sxs-lookup"><span data-stu-id="d3cc1-214">NetX Duo SNMP Username Callback</span></span>

<span data-ttu-id="d3cc1-215">O pacote NetX Duo SNMP Agent permite que a aplicação especifique (através da chamada ***nx_snmp_agent_create)*** uma chamada de nome de utilizador que é chamada no início do tratamento de cada pedido do Cliente SNMP.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-215">The NetX Duo SNMP Agent package allows the application to specify (via the ***nx_snmp_agent_create*** call) a username callback  that is called at the beginning of handling each SNMP Client request.</span></span>

<span data-ttu-id="d3cc1-216">A rotina de retorno fornece ao Agente SNMP NetX Duo com o nome de utilizador.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-216">The callback routine provides the NetX Duo SNMP Agent with the username.</span></span> <span data-ttu-id="d3cc1-217">Se o nome de utilizador fornecido for válido ou se não for necessária qualquer verificação do nome de utilizador para responder ao pedido, a chamada com o nome de utilizador deve devolver o valor de **NX_SUCCESS**.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-217">If the supplied username is valid or if no username check is necessary for the responding to the request, the username callback should return the value of **NX_SUCCESS**.</span></span> <span data-ttu-id="d3cc1-218">Caso contrário, a rotina deve voltar **NX_SNMP_ERROR** para indicar que o nome de utilizador especificado é inválido.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-218">Otherwise, the routine should return **NX_SNMP_ERROR** to indicate the specified username is invalid.</span></span>

<span data-ttu-id="d3cc1-219">O formato da rotina de chamada de nome de utilizador da aplicação é definido abaixo:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-219">The format of the application username callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_username_process(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *username);
```

<span data-ttu-id="d3cc1-220">Os parâmetros de entrada são definidos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-220">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="d3cc1-221">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="d3cc1-221">Parameter</span></span> | <span data-ttu-id="d3cc1-222">Significado</span><span class="sxs-lookup"><span data-stu-id="d3cc1-222">Meaning</span></span>                                              |
|-----------|------------------------------------------------------|
| <span data-ttu-id="d3cc1-223">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="d3cc1-223">*agent_ptr*</span></span> | <span data-ttu-id="d3cc1-224">Ponteiro para chamar agente do SNMP</span><span class="sxs-lookup"><span data-stu-id="d3cc1-224">Pointer to calling SNMP agent</span></span>                        |
| <span data-ttu-id="d3cc1-225">nome de utilizador</span><span class="sxs-lookup"><span data-stu-id="d3cc1-225">username</span></span>  | <span data-ttu-id="d3cc1-226">Destino para o ponteiro para o nome de utilizador necessário</span><span class="sxs-lookup"><span data-stu-id="d3cc1-226">Destination for the pointer to the required username</span></span> |

<span data-ttu-id="d3cc1-227">Para as sessões SNMPvv1 e SNMPv2/v2C, a aplicação irá querer examinar a cadeia comunitária num pedido do SNMP para determinar se o pedido do SNMP tem uma cadeia comunitária válida.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-227">For SNMPv1 and SNMPv2/v2C sessions, the application will want to examine the community string on an incoming SNMP request to determine if the SNMP request has a valid community string.</span></span> <span data-ttu-id="d3cc1-228">Existem vários serviços para a aplicação do SNMP para o fazer.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-228">There are several services for the SNMP application to do this.</span></span>

<span data-ttu-id="d3cc1-229">A aplicação SNMP pode inquirir se o atual pedido do SNMP Manager é um GET (por exemplo, GET, GETNEXT ou GETBULK) ou tipo de pedido SET utilizando este serviço:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-229">The SNMP application can inquire if the current SNMP Manager request is a GET (e.g. GET, GETNEXT, or GETBULK) or SET type of request using this service:</span></span>

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

<span data-ttu-id="d3cc1-230">Se o pedido for um tipo GET, a aplicação irá querer comparar a cadeia comunitária de entrada com a cadeia pública do Agente SNMP:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-230">If the request is a GET type, the application will want to compare the input community string to the SNMP Agent’s public string:</span></span>

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr,
                                      UCHAR *username,
                                      UINT *is_public);
```

<span data-ttu-id="d3cc1-231">Da mesma forma, se o pedido for um tipo SET, a aplicação irá querer comparar a cadeia comunitária de entrada com a cadeia privada do Agente SNMP:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-231">Similarly if the request is a SET type, the application will want to compare the input community string to the SNMP Agent’s private string:</span></span>

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr,
                                       UCHAR *username,
                                       UINT *is_private);
```

<span data-ttu-id="d3cc1-232">Os valores de retorno is_public e is_private indicam, respectivamente, se a cadeia comunitária de entrada é uma cadeia comunitária pública ou privada válida.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-232">The is_public and is_private return values indicate respectively if the input community string is a valid public or private community string.</span></span>

<span data-ttu-id="d3cc1-233">O valor de devolução da rotina de chamada do nome de utilizador indica se o nome de utilizador é válido.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-233">The return value of the username callback routine indicates if the username is valid.</span></span> <span data-ttu-id="d3cc1-234">O valor **NX_SUCCESS** é devolvido se o nome de utilizador for válido ou **NX_SNMP_ERROR** se o nome de utilizador for inválido.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-234">The value **NX_SUCCESS** is returned if the username is valid, or **NX_SNMP_ERROR** if the username is invalid.</span></span>

## <a name="netx-duo-snmp-agent-get-callback"></a><span data-ttu-id="d3cc1-235">NetX Duo SNMP Agent GET Callback</span><span class="sxs-lookup"><span data-stu-id="d3cc1-235">NetX Duo SNMP Agent GET Callback</span></span>

<span data-ttu-id="d3cc1-236">A aplicação deve definir uma rotina de retorno para lidar com pedidos de objetos GET do SNMP Manager.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-236">The application must set a callback routine for handling GET object requests from the SNMP Manager.</span></span> <span data-ttu-id="d3cc1-237">O retorno recupera o valor do objeto especificado no pedido.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-237">The callback retrieves the value of the object specified in the request.</span></span>

<span data-ttu-id="d3cc1-238">A rotina de chamada de pedido GET da aplicação é definida abaixo:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-238">The application GET request callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_get_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

<span data-ttu-id="d3cc1-239">Os parâmetros de entrada são definidos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-239">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="d3cc1-240">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="d3cc1-240">Parameter</span></span>        | <span data-ttu-id="d3cc1-241">Significado</span><span class="sxs-lookup"><span data-stu-id="d3cc1-241">Meaning</span></span> |
|------------------|----------------------------------|
| <span data-ttu-id="d3cc1-242">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="d3cc1-242">*agent_ptr*</span></span>        | <span data-ttu-id="d3cc1-243">Ponteiro para chamar agente do SNMP</span><span class="sxs-lookup"><span data-stu-id="d3cc1-243">Pointer to calling SNMP agent</span></span> |
| <span data-ttu-id="d3cc1-244">object_requested</span><span class="sxs-lookup"><span data-stu-id="d3cc1-244">object_requested</span></span> | <span data-ttu-id="d3cc1-245">Cadeia ASCII que representa o ID do objeto para a operação GET é para.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-245">ASCII string representing the object ID the GET operation is for.</span></span> |
| <span data-ttu-id="d3cc1-246">object_data</span><span class="sxs-lookup"><span data-stu-id="d3cc1-246">object_data</span></span>      | <span data-ttu-id="d3cc1-247">Estrutura de dados para manter o valor recuperado pela chamada.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-247">Data structure to hold the value retrieved by the callback.</span></span> <span data-ttu-id="d3cc1-248">Isto pode ser definido com uma série de API SNMP SNMP da NetX descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-248">This can be set with a series of NetX Duo SNMP API’s described below.</span></span> |

> [!NOTE]
> <span data-ttu-id="d3cc1-249">*Para as cordas de octeto, o objeto deve ser atribuído o comprimento de modo a que a função interna saiba quanto tempo o comprimento é, uma vez que a própria chamada não tem um argumento de comprimento:*</span><span class="sxs-lookup"><span data-stu-id="d3cc1-249">*For octet strings, the object must be assigned the length so that the internal function knows how long the length is since the callback itself does not have a length argument:*</span></span>

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

<span data-ttu-id="d3cc1-250">Uma vez que o tipo de dados não é conhecido da chamada GET, não há necessidade de verificar o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-250">Since the type of data is not known to the GET callback, there is no need to check the data type.</span></span> <span data-ttu-id="d3cc1-251">O comprimento não terá qualquer efeito sobre tipos ou cordas numéricas que sejam delimitadas nulas.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-251">Length will not have any effect on numeric types or strings which are null delimited.</span></span>

<span data-ttu-id="d3cc1-252">Em seguida, chame a função interna:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-252">Then call the internal function:</span></span>

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

<span data-ttu-id="d3cc1-253">Se a função de retorno não encontrar o objeto solicitado, o código de erro **NX_SNMP_ERROR_NOSUCHNAME** deve ser devolvido.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-253">If the callback function cannot find the requested object, the **NX_SNMP_ERROR_NOSUCHNAME** error code should be returned.</span></span> <span data-ttu-id="d3cc1-254">Se for detetado qualquer outro erro, o **NX_SNMP_ERROR** deve ser devolvido.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-254">If any other error is detected, the **NX_SNMP_ERROR** should be returned.</span></span>

## <a name="netx-duo-snmp-agent-getnext-callback"></a><span data-ttu-id="d3cc1-255">NetX Duo SNMP Agent GETNEXT Callback</span><span class="sxs-lookup"><span data-stu-id="d3cc1-255">NetX Duo SNMP Agent GETNEXT Callback</span></span>

<span data-ttu-id="d3cc1-256">A aplicação também deve definir a rotina de retorno para pedidos de objeto GETNEXT do Gerente SNMP.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-256">The application must also set the callback routine for GETNEXT object requests from the SNMP Manager.</span></span> <span data-ttu-id="d3cc1-257">A chamada GETNEXT recupera o valor do próximo objeto especificado pelo pedido.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-257">The GETNEXT callback retrieves the value of the next object specified by the request.</span></span>

<span data-ttu-id="d3cc1-258">A rotina de chamada de pedido GETNEXT da aplicação é definida abaixo:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-258">The application GETNEXT request callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_getnext_process(NX_SNMP_AGENT *agent_ptr,
                                   UCHAR *object_requested,
                                   NX_SNMP_OBJECT_DATA *object_data);
```

<span data-ttu-id="d3cc1-259">Os parâmetros de entrada são definidos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-259">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="d3cc1-260">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="d3cc1-260">Parameter</span></span>        | <span data-ttu-id="d3cc1-261">Significado</span><span class="sxs-lookup"><span data-stu-id="d3cc1-261">Meaning</span></span> |
|------------------|-------------------------------------------|
| <span data-ttu-id="d3cc1-262">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="d3cc1-262">*agent_ptr*</span></span>        | <span data-ttu-id="d3cc1-263">Ponteiro para chamar agente do SNMP</span><span class="sxs-lookup"><span data-stu-id="d3cc1-263">Pointer to calling SNMP agent</span></span> |
| <span data-ttu-id="d3cc1-264">object_requested</span><span class="sxs-lookup"><span data-stu-id="d3cc1-264">object_requested</span></span> | <span data-ttu-id="d3cc1-265">Cadeia ASCII que representa o objeto ID a operação GETNEXT é para.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-265">ASCII string representing the object ID the GETNEXT operation is for.</span></span> |
| <span data-ttu-id="d3cc1-266">object_data</span><span class="sxs-lookup"><span data-stu-id="d3cc1-266">object_data</span></span>      | <span data-ttu-id="d3cc1-267">Estrutura de dados para manter o valor recuperado pela chamada.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-267">Data structure to hold the value retrieved by the callback.</span></span> <span data-ttu-id="d3cc1-268">Isto pode ser definido com uma série de API SNMP SNMP da NetX descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-268">This can be set with a series of NetX Duo SNMP API’s described below.</span></span> |

<span data-ttu-id="d3cc1-269">O mesmo que é verdade para as chamadas GET, os objetos com dados de cadeia de octeto devem ser atribuídos ao comprimento para que a função interna saiba quanto tempo o comprimento é, uma vez que a própria chamada não tem um argumento de comprimento:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-269">Same as is true for GET callbacks, objects with octet string data must be assigned the length so that the internal function knows how long the length is since the callback itself does not have a length argument:</span></span>

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

<span data-ttu-id="d3cc1-270">Uma vez que o tipo de dados não é conhecido da chamada GET, não há necessidade de verificar o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-270">Since the type of data is not known to the GET callback, there is no need to check the data type.</span></span> <span data-ttu-id="d3cc1-271">O comprimento não terá qualquer efeito sobre tipos ou cordas numéricas que sejam delimitadas nulas.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-271">Length will not have any effect on numeric types or strings which are null delimited.</span></span>

<span data-ttu-id="d3cc1-272">Em seguida, chame a função interna:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-272">Then call the internal function:</span></span>

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

<span data-ttu-id="d3cc1-273">Se a função de retorno não encontrar o objeto solicitado, o código de erro **NX_SNMP_ERROR_NOSUCHNAME** deve ser devolvido.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-273">If the callback function cannot find the requested object, the **NX_SNMP_ERROR_NOSUCHNAME** error code should be returned.</span></span> <span data-ttu-id="d3cc1-274">Se for detetado qualquer outro erro, o **NX_SNMP_ERROR** deve ser devolvido.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-274">If any other error is detected, the **NX_SNMP_ERROR** should be returned.</span></span>

## <a name="netx-duo-snmp-agent-set-callback"></a><span data-ttu-id="d3cc1-275">NetX Duo SNMP Agent SET Callback</span><span class="sxs-lookup"><span data-stu-id="d3cc1-275">NetX Duo SNMP Agent SET Callback</span></span>

<span data-ttu-id="d3cc1-276">A aplicação deve definir a rotina de retorno para o tratamento dos pedidos de objetos SET do SNMP.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-276">The application should set the callback routine for handling SET object requests from the SNMP Manager.</span></span> <span data-ttu-id="d3cc1-277">A chamada SET define o valor do objeto especificado pelo pedido.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-277">The SET callback sets the value of the object specified by the request.</span></span>

<span data-ttu-id="d3cc1-278">A rotina de chamada de pedido de pedido de candidatura set é definida abaixo:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-278">The application SET request callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_set_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

<span data-ttu-id="d3cc1-279">Os parâmetros de entrada são definidos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-279">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="d3cc1-280">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="d3cc1-280">Parameter</span></span>        | <span data-ttu-id="d3cc1-281">Significado</span><span class="sxs-lookup"><span data-stu-id="d3cc1-281">Meaning</span></span> |
|------------------|-------- |
| <span data-ttu-id="d3cc1-282">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="d3cc1-282">*agent_ptr*</span></span>      | <span data-ttu-id="d3cc1-283">Ponteiro para chamar agente do SNMP</span><span class="sxs-lookup"><span data-stu-id="d3cc1-283">Pointer to calling SNMP agent</span></span> |
| <span data-ttu-id="d3cc1-284">object_requested</span><span class="sxs-lookup"><span data-stu-id="d3cc1-284">object_requested</span></span> | <span data-ttu-id="d3cc1-285">Cadeia ASCII que representa o ID do objeto para a operação SET é para.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-285">ASCII string representing the object ID the SET operation is for.</span></span> |
| <span data-ttu-id="d3cc1-286">object_data</span><span class="sxs-lookup"><span data-stu-id="d3cc1-286">object_data</span></span>      | <span data-ttu-id="d3cc1-287">Estrutura de dados que contém o novo valor para o objeto especificado.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-287">Data structure that contains the new value for the specified object.</span></span> <span data-ttu-id="d3cc1-288">A operação real pode ser feita utilizando o API da API do SNMP Da NetX Duo descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-288">The actual operation can be done using the NetX Duo SNMP API’s described below.</span></span> |

<span data-ttu-id="d3cc1-289">Note que para as cordas de octeto, o retorno SET deve atualizar a tabela MIB com o comprimento dos dados uma vez que o Agente SNMP analisou os dados e sabe o tipo e comprimento:</span><span class="sxs-lookup"><span data-stu-id="d3cc1-289">Note that for octet strings, the SET callback should update the MIB table with the length of the data since the SNMP Agent has parsed the data and knows the type and length:</span></span>

```c
if (object_data -> nx_snmp_object_data_type ==
                           NX_SNMP_ANS1_OCTET_STRING)
{
    mib2_mib[i].length =
        object_data -> nx_snmp_object_octet_string_size;
}

object_data -> nx_snmp_object_octet_string_size =
                                 mib2_mib[i].length;
```

<span data-ttu-id="d3cc1-290">Se a função de retorno não encontrar o objeto solicitado, o código de erro **NX_SNMP_ERROR_NOSUCHNAME** deve ser devolvido.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-290">If the callback function cannot find the requested object, the **NX_SNMP_ERROR_NOSUCHNAME** error code should be returned.</span></span>

<span data-ttu-id="d3cc1-291">Se o anfitrião NetX Duo SNMP criou cordas comunitárias privadas, e o remetente SNMP do pedido SET não tiver a cadeia privada correspondente, poderá devolver um erro **de NX_SNMP_ERROR_NOACCESS.**</span><span class="sxs-lookup"><span data-stu-id="d3cc1-291">If the NetX Duo SNMP host has created private community strings, and the SNMP sender of the SET request does not have the matching private string, it may return an **NX_SNMP_ERROR_NOACCESS** error.</span></span> <span data-ttu-id="d3cc1-292">Se for detetado qualquer outro erro, o **NX_SNMP_ERROR** deve ser devolvido.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-292">If any other error is detected, the **NX_SNMP_ERROR** should be returned.</span></span>

> [!NOTE]
> <span data-ttu-id="d3cc1-293">*Embora o Agente SNMP Da NetX Duo forneça uma base de dados SNMP MIB com a distribuição, destina-se principalmente a fins de teste e desenvolvimento. O desenvolvedor provavelmente exigirá uma base de dados de MIB proprietária para uma aplicação profissional do SNMP.*</span><span class="sxs-lookup"><span data-stu-id="d3cc1-293">*Although NetX Duo SNMP Agent supplies an SNMP MIB database with the distribution, it is primarily for testing and development purposes. The developer will likely require a proprietary MIB database for a professional SNMP application.*</span></span>

## <a name="changing-snmp-version-at-run-time"></a><span data-ttu-id="d3cc1-294">Alterar a versão SNMP no tempo de execução</span><span class="sxs-lookup"><span data-stu-id="d3cc1-294">Changing SNMP Version at Run Time</span></span>

<span data-ttu-id="d3cc1-295">O anfitrião do Agente SNMP pode alterar a versão SNMP para cada uma das três versões em execução utilizando o serviço *nx_snmp_agent_set_version.*</span><span class="sxs-lookup"><span data-stu-id="d3cc1-295">The SNMP Agent host can change SNMP version for each of the three versions at run time using the *nx_snmp_agent_set_version* service.</span></span> <span data-ttu-id="d3cc1-296">O Agente SNMP está habilitado por padrão para as três versões quando o Agente SNMP é criado em *nx_snmp_agent_create*.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-296">The SNMP Agent is by default enabled for all three versions when the SNMP Agent is created in *nx_snmp_agent_create*.</span></span> <span data-ttu-id="d3cc1-297">No entanto, a aplicação pode limitar isso a um subconjunto de todas as versões.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-297">However, the application can limit that to a subset of all versions.</span></span>

> [!NOTE]
> <span data-ttu-id="d3cc1-298">*Se as opções de configuração NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 e/ou NX_SNMP_DISABLE_V3 forem definidas, esta função não terá qualquer efeito que permita as versões efetuadas.*</span><span class="sxs-lookup"><span data-stu-id="d3cc1-298">*If the configuration options NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 and/or NX_SNMP_DISABLE_V3 are defined, this function will have no effect enabling the effected versions.*</span></span>

<span data-ttu-id="d3cc1-299">O Agente SNMP pode recuperar a versão SNMP do mais recente pacote SNMP recebido através do serviço *nx_snmp_agent_get_current_version.*</span><span class="sxs-lookup"><span data-stu-id="d3cc1-299">The SNMP Agent can retrieve the SNMP version of the latest SNMP packet received using the *nx_snmp_agent_get_current_version* service.</span></span>

## <a name="snmpv3-discovery"></a><span data-ttu-id="d3cc1-300">Descoberta SNMPv3</span><span class="sxs-lookup"><span data-stu-id="d3cc1-300">SNMPv3 Discovery</span></span>

<span data-ttu-id="d3cc1-301">O Agente SNMP, se estiver habilitado para o SNMPv3, responderá aos pedidos de descoberta do Gestor do SNMP.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-301">The SNMP Agent, if enabled for SNMPv3, will respond to discovery requests from the SNMP Manager.</span></span> <span data-ttu-id="d3cc1-302">Tal pedido contém dados de parâmetros de segurança com valores nulos para ID do motor autoritário, nome de utilizador, contagem de botas e tempo de arranque.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-302">Such a request contains security parameter data with null values for Authoritative Engine ID, user name, boot count and boot time.</span></span> <span data-ttu-id="d3cc1-303">Os parâmetros de autenticação não são aplicados à mensagem DISCOVERY.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-303">Authentication parameters are not applied to the DISCOVERY message.</span></span> <span data-ttu-id="d3cc1-304">A lista de encadernação variável no pedido está vazia (contém zero itens).</span><span class="sxs-lookup"><span data-stu-id="d3cc1-304">The variable binding list in the request is empty (contains zero items).</span></span> <span data-ttu-id="d3cc1-305">O agente SNMP responde com um tempo e contagem zero de arranque, e a lista de encadernação variável contendo 1 item, *usmStatsUnknownEngineIDs,* que é a contagem de pedidos recebidos com um ID de motor desconhecido (nulo).</span><span class="sxs-lookup"><span data-stu-id="d3cc1-305">The SNMP agent responds with a zero boot time and count, and the variable binding list containing 1 item, *usmStatsUnknownEngineIDs*, which is the count of requests received with an unknown (null) engine ID.</span></span> <span data-ttu-id="d3cc1-306">No pedido getneXT subsequente do Browser/Manager, os dados de arranque e os parâmetros de segurança só são preenchidos se a segurança estiver ativada.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-306">On the subsequent GETNEXT request from the Browser/Manager, the boot data and security parameters are filled in only if security is enabled.</span></span> <span data-ttu-id="d3cc1-307">Em caso afirmativo, também enviará uma atualização de dados NotInTime no PDU.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-307">If so it will also send a NotInTime data update in the PDU.</span></span> <span data-ttu-id="d3cc1-308">Os parâmetros de segurança, por exemplo, a autenticação comprovam a identidade do Agente ao Gestor.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-308">The security parameters, e.g. authentication prove the identity of the Agent to the Manager.</span></span>

<span data-ttu-id="d3cc1-309">Informações mais detalhadas sobre a autenticação do SNMPv3 estão disponíveis no RFC 3414 "Modelo de Segurança Baseado no Utilizador (USM) para a versão 3 do Protocolo de Gestão de Redes Simples (SNMPv3)".</span><span class="sxs-lookup"><span data-stu-id="d3cc1-309">More detailed information on SNMPv3 authentication is available in RFC 3414 “User-based Security Model (USM) for version 3 of the Simple Network Management Protocol (SNMPv3)”.</span></span>

## <a name="netx-duo-snmp-rfcs"></a><span data-ttu-id="d3cc1-310">NetX Duo SNMP RFCs</span><span class="sxs-lookup"><span data-stu-id="d3cc1-310">NetX Duo SNMP RFCs</span></span>

<span data-ttu-id="d3cc1-311">NetX Duo SNMP está em conformidade com RFC1155, RFC1157, RFC1215, RFC1901, RFC1905, RFC1906, RFC1907, RFC1908, RFC2571, RFC2572, RFC2574, RFC2574, RFC2575, RFC2575, RFC2575, RFC2575, RFC2575, RFC2575, RFC2575, RFC2575, RFC2575, RFC 3414 e relacionados.</span><span class="sxs-lookup"><span data-stu-id="d3cc1-311">NetX Duo SNMP is compliant with RFC1155, RFC1157, RFC1215, RFC1901, RFC1905, RFC1906, RFC1907, RFC1908, RFC2571, RFC2572, RFC2574, RFC2575, RFC 3414 and related RFCs.</span></span>
