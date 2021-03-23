---
title: Capítulo 8 - Azure RTOS NetX trace eventos
description: Este capítulo contém uma descrição dos eventos Azure RTOS NetX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: ce355d86d7db0b7e259ae58e306d990277b77a8f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828352"
---
# <a name="chapter-8---azure-rtos-netx-trace-events"></a><span data-ttu-id="18ca0-103">Capítulo 8 - Azure RTOS NetX trace eventos</span><span class="sxs-lookup"><span data-stu-id="18ca0-103">Chapter 8 - Azure RTOS NetX trace events</span></span>

<span data-ttu-id="18ca0-104">Este capítulo contém uma descrição dos eventos Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="18ca0-104">This chapter contains a description of the Azure RTOS NetX events.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="18ca0-105">Lista de eventos e ícones</span><span class="sxs-lookup"><span data-stu-id="18ca0-105">List of Events and Icons</span></span>

<span data-ttu-id="18ca0-106">Segue-se uma lista de eventos NetX apresentados pela TraceX.</span><span class="sxs-lookup"><span data-stu-id="18ca0-106">The following is a list of NetX events displayed by TraceX.</span></span>

| <span data-ttu-id="18ca0-107">Ícone</span><span class="sxs-lookup"><span data-stu-id="18ca0-107">Icon</span></span>                                           | <span data-ttu-id="18ca0-108">Significado</span><span class="sxs-lookup"><span data-stu-id="18ca0-108">Meaning</span></span>                 |
| -------------------------------- | ------------------------------------- |
| ![Ícone de receção de pedido de R P interno](./media/user-guide/netx-events/image1.png)    | <span data-ttu-id="18ca0-110">Pedido interno de ARP Receber</span><span class="sxs-lookup"><span data-stu-id="18ca0-110">Internal ARP Request Receive</span></span> |
| ![Interna A R P Pedido Enviar ícone](./media/user-guide/netx-events/image2.png)    | <span data-ttu-id="18ca0-112">Pedido interno de ARP Enviar</span><span class="sxs-lookup"><span data-stu-id="18ca0-112">Internal ARP Request Send</span></span> |
| ![Ícone de receção de resposta R P interna](./media/user-guide/netx-events/image3.png)    | <span data-ttu-id="18ca0-114">Resposta Interna da ARP Receber</span><span class="sxs-lookup"><span data-stu-id="18ca0-114">Internal ARP Response Receive</span></span> |
| ![Ícone de resposta R P interna](./media/user-guide/netx-events/image4.png)    | <span data-ttu-id="18ca0-116">Envio de resposta interna da ARP</span><span class="sxs-lookup"><span data-stu-id="18ca0-116">Internal ARP Response Send</span></span> |
| ![Ícone de receção interna I C M P](./media/user-guide/netx-events/image5.png)    | <span data-ttu-id="18ca0-118">ICMP Interno Receber</span><span class="sxs-lookup"><span data-stu-id="18ca0-118">Internal ICMP Receive</span></span> |
| ![I C M P Interno Enviar ícone](./media/user-guide/netx-events/image6.png)    | <span data-ttu-id="18ca0-120">Envio interno do ICMP</span><span class="sxs-lookup"><span data-stu-id="18ca0-120">Internal ICMP Send</span></span> |
| ![NetX Interno I G M P Receber ícone](./media/user-guide/netx-events/image7.png)    | <span data-ttu-id="18ca0-122">Receber Internamente netx IGMP</span><span class="sxs-lookup"><span data-stu-id="18ca0-122">Internal NetX IGMP Receive</span></span> |
| ![I P Interno Receber ícone](./media/user-guide/netx-events/image8.png)    | <span data-ttu-id="18ca0-124">Ip Interno Receber</span><span class="sxs-lookup"><span data-stu-id="18ca0-124">Internal IP Receive</span></span> |
| ![I P Interno Enviar ícone](./media/user-guide/netx-events/image9.png)    | <span data-ttu-id="18ca0-126">Envio ip interno</span><span class="sxs-lookup"><span data-stu-id="18ca0-126">Internal IP Send</span></span> |
| ![Ícone de receção de dados internos de T C P](./media/user-guide/netx-events/image10.png)    | <span data-ttu-id="18ca0-128">Dados internos da TCP recebem</span><span class="sxs-lookup"><span data-stu-id="18ca0-128">Internal TCP Data Receive</span></span> |
| ![Dados internos T C P Enviar ícone](./media/user-guide/netx-events/image11.png)    | <span data-ttu-id="18ca0-130">Envio de dados internos da TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-130">Internal TCP Data Send</span></span> |
| ![Ícone de receção de T C P Interna](./media/user-guide/netx-events/image12.png)    | <span data-ttu-id="18ca0-132">TCP FIN Interno Receber</span><span class="sxs-lookup"><span data-stu-id="18ca0-132">Internal TCP FIN Receive</span></span> |
| ![Interior T C P F I N Enviar ícone](./media/user-guide/netx-events/image13.png)    | <span data-ttu-id="18ca0-134">TCP FIN Interno Enviar</span><span class="sxs-lookup"><span data-stu-id="18ca0-134">Internal TCP FIN Send</span></span> |
| ![Ícone de receção interna T C P R S T](./media/user-guide/netx-events/image14.png)    | <span data-ttu-id="18ca0-136">Receção Interna de TCP RST</span><span class="sxs-lookup"><span data-stu-id="18ca0-136">Internal TCP RST Receive</span></span> |
| ![Ícone de envio interno T C P P S T](./media/user-guide/netx-events/image15.png)    | <span data-ttu-id="18ca0-138">Envio interno de TCP RST</span><span class="sxs-lookup"><span data-stu-id="18ca0-138">Internal TCP RST Send</span></span> |
| ![Ícone de receção interna T C P S Y N](./media/user-guide/netx-events/image16.png)    | <span data-ttu-id="18ca0-140">Receção interna do TCP SYN</span><span class="sxs-lookup"><span data-stu-id="18ca0-140">Internal TCP SYN Receive</span></span> |
| ![Ícone interno T C P S Y N Enviar](./media/user-guide/netx-events/image17.png)    | <span data-ttu-id="18ca0-142">Envio interno de TCP SYN</span><span class="sxs-lookup"><span data-stu-id="18ca0-142">Internal TCP SYN Send</span></span> |
| ![Ícone de receção interna de U D P](./media/user-guide/netx-events/image18.png)    | <span data-ttu-id="18ca0-144">UDP Interna Receber</span><span class="sxs-lookup"><span data-stu-id="18ca0-144">Internal UDP Receive</span></span> |
| ![U D P Interno Enviar ícone](./media/user-guide/netx-events/image19.png)    | <span data-ttu-id="18ca0-146">Envio interno da UDP</span><span class="sxs-lookup"><span data-stu-id="18ca0-146">Internal UDP Send</span></span> |
| ![Ícone de receção R A R P interno](./media/user-guide/netx-events/image20.png)    | <span data-ttu-id="18ca0-148">Receção interna da RARP</span><span class="sxs-lookup"><span data-stu-id="18ca0-148">Internal RARP Receive</span></span> |
| ![R A R P Interno Enviar ícone](./media/user-guide/netx-events/image21.png)    | <span data-ttu-id="18ca0-150">Envio interno da RARP</span><span class="sxs-lookup"><span data-stu-id="18ca0-150">Internal RARP Send</span></span> |
| ![Ícone interno de retografia T C P](./media/user-guide/netx-events/image22.png)    | <span data-ttu-id="18ca0-152">Redatry TCP interno</span><span class="sxs-lookup"><span data-stu-id="18ca0-152">Internal TCP Retry</span></span> |
| ![Ícone interno de mudança de estado T C P](./media/user-guide/netx-events/image23.png)    | <span data-ttu-id="18ca0-154">Mudança interna do estado da TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-154">Internal TCP State Change</span></span> |
| ![Pacote de envio de motorista interno I / O](./media/user-guide/netx-events/image24.png)    | <span data-ttu-id="18ca0-156">Pacote de motorista interno enviar</span><span class="sxs-lookup"><span data-stu-id="18ca0-156">Internal I/O Driver Packet Send</span></span> |
| ![ícone](./media/user-guide/netx-events/image25.png)    | <span data-ttu-id="18ca0-158">Inicialização interna do controlador de I/O</span><span class="sxs-lookup"><span data-stu-id="18ca0-158">Internal I/O Driver Initialize</span></span> |
| ![Ícone de inicialização do condutor interno I / O](./media/user-guide/netx-events/image26.png)    | <span data-ttu-id="18ca0-160">Ligação interna do controlador de I/O</span><span class="sxs-lookup"><span data-stu-id="18ca0-160">Internal I/O Driver Link Enable</span></span> |
| ![Ícone de desativação do controlador interno I / O](./media/user-guide/netx-events/image27.png)    | <span data-ttu-id="18ca0-162">Ligação interna do controlador de I/O Desativada</span><span class="sxs-lookup"><span data-stu-id="18ca0-162">Internal I/O Driver Link Disable</span></span> |
| ![Ícone de transmissão de pacote de motorista interno I / O](./media/user-guide/netx-events/image28.png)    | <span data-ttu-id="18ca0-164">Transmissão interna do pacote de motorista de I/O</span><span class="sxs-lookup"><span data-stu-id="18ca0-164">Internal I/O Driver Packet Broadcast</span></span> |
| ![Ícone de envio de ARP do condutor interno I / O](./media/user-guide/netx-events/image29.png)    | <span data-ttu-id="18ca0-166">Envio interno de ARP do condutor de I/O</span><span class="sxs-lookup"><span data-stu-id="18ca0-166">Internal I/O Driver ARP Send</span></span> |
| ![I / O Driver ARP Response Enviar ícone](./media/user-guide/netx-events/image30.png)    | <span data-ttu-id="18ca0-168">Envio de resposta ARP do controlador interno de I/O</span><span class="sxs-lookup"><span data-stu-id="18ca0-168">Internal I/O Driver ARP Response Send</span></span> |
| ![Ícone interno I / O Driver RARP Enviar ícone](./media/user-guide/netx-events/image31.png)    | <span data-ttu-id="18ca0-170">Envio interno de I/O do condutor RARP</span><span class="sxs-lookup"><span data-stu-id="18ca0-170">Internal I/O Driver RARP Send</span></span> |
| ![Ícone de união de controlador interno I / O Motorista](./media/user-guide/netx-events/image32.png)    | <span data-ttu-id="18ca0-172">União Multicast do controlador de I/O interna</span><span class="sxs-lookup"><span data-stu-id="18ca0-172">Internal I/O Driver Multicast Join</span></span> |
| ![Ícone de licença de controlador interno I / O](./media/user-guide/netx-events/image33.png)    | <span data-ttu-id="18ca0-174">Licença multicast do controlador interno de I/O</span><span class="sxs-lookup"><span data-stu-id="18ca0-174">Internal I/O Driver Multicast Leave</span></span> |
| ![Ícone de estado do motorista interno I / O](./media/user-guide/netx-events/image34.png)    | <span data-ttu-id="18ca0-176">O controlador interno de I/O obtém o estado</span><span class="sxs-lookup"><span data-stu-id="18ca0-176">Internal I/O Driver Get Status</span></span> |
| ![Ícone interno I / O Driver Get Speed](./media/user-guide/netx-events/image35.png)    | <span data-ttu-id="18ca0-178">Condutor interno de I/O obtém velocidade</span><span class="sxs-lookup"><span data-stu-id="18ca0-178">Internal I/O Driver Get Speed</span></span> |
| ![I / O Motorista Interno Obter ícone do tipo Duplex](./media/user-guide/netx-events/image36.png)    | <span data-ttu-id="18ca0-180">Controlador interno de I/O obter tipo duplex</span><span class="sxs-lookup"><span data-stu-id="18ca0-180">Internal I/O Driver Get Duplex Type</span></span> |
| ![Ícone interno de I / O Driver Get Error Count](./media/user-guide/netx-events/image37.png)    | <span data-ttu-id="18ca0-182">Controlador interno de I/O obtenha contagem de erros</span><span class="sxs-lookup"><span data-stu-id="18ca0-182">Internal I/O Driver Get Error Count</span></span> |
| ![I / O Condutor Interno Obter ícone de Contagem RX](./media/user-guide/netx-events/image38.png)    | <span data-ttu-id="18ca0-184">Motorista interno de I/O obtém conta de RX</span><span class="sxs-lookup"><span data-stu-id="18ca0-184">Internal I/O Driver Get RX Count</span></span> |
| ![I / O Condutor Interno Obter ícone de contagem de TX](./media/user-guide/netx-events/image39.png)    | <span data-ttu-id="18ca0-186">Condutor interno de I/O obtém contagem de TX</span><span class="sxs-lookup"><span data-stu-id="18ca0-186">Internal I/O Driver Get TX Count</span></span> |
| ![Ícone de erros de atribuição de I/O Internos](./media/user-guide/netx-events/image40.png)    | <span data-ttu-id="18ca0-188">Condutor interno de I/O obtém erros de atribuição</span><span class="sxs-lookup"><span data-stu-id="18ca0-188">Internal I/O Driver Get Allocation Errors</span></span> |
| ![Ícone interno I / O Driver Un-initialize](./media/user-guide/netx-events/image41.png)    | <span data-ttu-id="18ca0-190">Condutor interno de I/O Des-initialize</span><span class="sxs-lookup"><span data-stu-id="18ca0-190">Internal I/O Driver Un-initialize</span></span> |
| ![Ícone de processamento diferido interno I / O Driver](./media/user-guide/netx-events/image42.png)    | <span data-ttu-id="18ca0-192">Processamento diferido interno do controlador de I/O</span><span class="sxs-lookup"><span data-stu-id="18ca0-192">Internal I/O Driver Deferred Processing</span></span> |
| ![Um ícone invalidado de entradas dinâmicas R P](./media/user-guide/netx-events/image43.png)    | <span data-ttu-id="18ca0-194">**Entradas dinâmicas ARP Invalidam** *-nx_arp_dynamic_entries_invalidate)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-194">**ARP Dynamic Entries Invalidate** (*nx_arp_dynamic_entries_invalidate*)</span></span> |
| ![Um ícone de conjunto de entrada dinâmica R P](./media/user-guide/netx-events/image44.png)    | <span data-ttu-id="18ca0-196">**Conjunto de entrada dinâmica ARP** *(nx_arp_dynamic_entry_set)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-196">**ARP Dynamic Entry Set** (*nx_arp_dynamic_entry_set*)</span></span> |
| ![Um ícone de ativação R P](./media/user-guide/netx-events/image45.png)    | <span data-ttu-id="18ca0-198">**ARP Enable** *(nx_arp_enable)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-198">**ARP Enable** (*nx_arp_enable*)</span></span> |
| ![Um ícone de envio gratuito R P](./media/user-guide/netx-events/image46.png)    | <span data-ttu-id="18ca0-200">**ARP Envio Gratuito** (*nx_arp_gratuitous_send)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-200">**ARP Gratuitous Send** (*nx_arp_gratuitous_send*)</span></span> |
| ![Um ícone de endereço de hardware R P](./media/user-guide/netx-events/image47.png)    | <span data-ttu-id="18ca0-202">**ARP Hardware Address Find** *(nx_arp_hardware_address_find)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-202">**ARP Hardware Address Find** (*nx_arp_hardware_address_find*)</span></span> |
| ![Um ícone de informação R P Obtenha](./media/user-guide/netx-events/image48.png)    | <span data-ttu-id="18ca0-204">**Informação ARP Get** *(nx_arp_info_get)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-204">**ARP Information Get** (*nx_arp_info_get*)</span></span> |
| ![Um ícone de endereço IP R P](./media/user-guide/netx-events/image49.png)    | <span data-ttu-id="18ca0-206">**ARP IP Address Find** *(nx_arp_ip_address_find)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-206">**ARP IP Address Find** (*nx_arp_ip_address_find*)</span></span> |
| ![Um ícone de entrada estática R P](./media/user-guide/netx-events/image50.png)    | <span data-ttu-id="18ca0-208">**Criação de entrada estática ARP** *(nx_arp_static_entry_create)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-208">**ARP Static Entry Create** (*nx_arp_static_entry_create*)</span></span> |
| ![Um ícone de entradas estáticas R P Delete](./media/user-guide/netx-events/image51.png)    | <span data-ttu-id="18ca0-210">**ARP Estática Entradas Eliminar** *(nx_arp_static_entries_delete)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-210">**ARP Static Entries Delete** (*nx_arp_static_entries_delete*)</span></span> |
| ![Um ícone de exclusão de entrada estática R P](./media/user-guide/netx-events/image52.png)    | <span data-ttu-id="18ca0-212">**Eliminação da entrada estática ARP** *(nx_arp_static_entry_delete)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-212">**ARP Static Entry Delete** (*nx_arp_static_entry_delete*)</span></span> |
| ![Ícone de eliminação de entrada de cache de duo](./media/user-guide/netx-events/image53.png)    | <span data-ttu-id="18ca0-214">**Exclusão de entrada de cache duo** *(nxd_nd_cache_entry_delete)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-214">**Duo Cache Entry Delete** (*nxd_nd_cache_entry_delete*)</span></span> |
| ![Ícone do conjunto de conjunto de entrada de cache duo](./media/user-guide/netx-events/image54.png)    | <span data-ttu-id="18ca0-216">**Conjunto de entrada de cache duo** *(nxd_nd_cache_entry_set)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-216">**Duo Cache Entry Set** (*nxd_nd_cache_entry_set*)</span></span> |
| ![Ícone invalidado duo cache](./media/user-guide/netx-events/image55.png)    | <span data-ttu-id="18ca0-218">**Duo Cache Invalidado** *(nxd_nd_cache_invalidate)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-218">**Duo Cache Invalidate** (*nxd_nd_cache_invalidate*)</span></span> |
| ![Duo Cache I Endereço P Encontrar ícone](./media/user-guide/netx-events/image56.png)    | <span data-ttu-id="18ca0-220">**Duo Cache IP Address Find** *(nxd_nd_cache_ip_address_find)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-220">**Duo Cache IP Address Find** (*nxd_nd_cache_ip_address_find*)</span></span> |
| ![Duo I C M P Enable ícone](./media/user-guide/netx-events/image57.png)    | <span data-ttu-id="18ca0-222">**Ativação duo ICMP** *(nxd_icmp_enable)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-222">**Duo ICMP Enable** (*nxd_icmp_enable*)</span></span> |
| ![Duo I C M P I P v 6 Ping ícone](./media/user-guide/netx-events/image58.png)    | <span data-ttu-id="18ca0-224">**Duo ICMP IPv6 Ping** *(nxd_icmp_ping)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-224">**Duo ICMP IPv6 Ping** (*nxd_icmp_ping*)</span></span> |
| ![Duo I P Max Tamanho de Carga Útil Encontrar ícone](./media/user-guide/netx-events/image59.png)    | <span data-ttu-id="18ca0-226">**Duo IP Max Payload Size Find** *(nx_max_payload_size_find)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-226">**Duo IP Max Payload Size Find** (*nx_max_payload_size_find*)</span></span> |
| ![Duo I P Pacote Cru Enviar ícone](./media/user-guide/netx-events/image60.png)    | <span data-ttu-id="18ca0-228">**Duo IP Raw Packet Send** *(nxd_ip_raw_packet_send)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-228">**Duo IP Raw Packet Send** (*nxd_ip_raw_packet_send*)</span></span> |
| ![Duo I P v 6 Predefinido Router Adicionar ícone](./media/user-guide/netx-events/image61.png)    | <span data-ttu-id="18ca0-230">**Adicionar do router padrão Duo IPv6** *(nxd_ipv6_default_router_add)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-230">**Duo IPv6 Default Router Add** (*nxd_ipv6_default_router_add*)</span></span> |
| ![Duo I P v 6 Ícone de exclusão de router padrão](./media/user-guide/netx-events/image62.png)    | <span data-ttu-id="18ca0-232">**Exclusão do router padrão Duo IPv6** *(nxd_ipv6_default_router_delete)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-232">**Duo IPv6 Default Router Delete** (*nxd_ipv6_default_router_delete)*</span></span> |
| ![Duo I P v 6 Ativar ícone](./media/user-guide/netx-events/image63.png)    | <span data-ttu-id="18ca0-234">**Duo IPv6 Enable** *(nxd_ipv6_enable)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-234">**Duo IPv6 Enable** (*nxd_ipv6_enable)*</span></span> |
| ![Duo I P v 6 Global Address Obter ícone](./media/user-guide/netx-events/image64.png)    | <span data-ttu-id="18ca0-236">**Duo IPv6 Global Address Get** *(nxd_ipv6_global_address_get)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-236">**Duo IPv6 Global Address Get** (*nxd_ipv6_global_address_get*)</span></span> |
| ![Duo I P v 6 Ícone global de conjunto de endereços](./media/user-guide/netx-events/image65.png)    | <span data-ttu-id="18ca0-238">**Conjunto de endereços globais Duo IPv6** *(nxd_ipv6_global_address_set)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-238">**Duo IPv6 Global Address Set** (*nxd_ipv6_global_address_set*)</span></span> |
| ![Duo I P v6 Iniciado Ícone do Processo do Pai](./media/user-guide/netx-events/image66.png)    | <span data-ttu-id="18ca0-240">**Duo IPv6 Iniciar Processo do Pai** *(nxd_ipv6_initiate_dad_process)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-240">**Duo IPv6 Initiate Dad Process** (*nxd_ipv6_initiate_dad_process*)</span></span> |
| ![Duo I P v 6 Interface Endereço Obter ícone](./media/user-guide/netx-events/image67.png)    | <span data-ttu-id="18ca0-242">**Endereço de interface Duo IPv6 Obter** *(nxd_ipv6_interface_address_get)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-242">**Duo IPv6 Interface Address Get** (*nxd_ipv6_interface_address_get*)</span></span> |
| ![Ícone de conjunto de endereço de interface duo I P v 6](./media/user-guide/netx-events/image68.png)    | <span data-ttu-id="18ca0-244">**Conjunto de endereços de interface Duo IPv6** *(nxd_ipv6_interface_address_set*)</span><span class="sxs-lookup"><span data-stu-id="18ca0-244">**Duo IPv6 Interface Address Set** (*nxd_ipv6_interface_address_set*)</span></span> |
| ![Duo I P v 6 Link Endereço Local Obter ícone](./media/user-guide/netx-events/image69.png)    | <span data-ttu-id="18ca0-246">**Duo IPv6 Link Endereço Local Obter** *(nxd_ipv6_linklocal_address_get)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-246">**Duo IPv6 Link Local Address Get** (*nxd_ipv6_linklocal_address_get*)</span></span> |
| ![Duo I P v 6 Link Ícone de conjunto de endereço local](./media/user-guide/netx-events/image70.png)    | <span data-ttu-id="18ca0-248">**Conjunto de endereços locais de ligação duo IPv6** *(nxd_ipv6_linklocal_address_set*)</span><span class="sxs-lookup"><span data-stu-id="18ca0-248">**Duo IPv6 Link Local Address Set** (*nxd_ipv6_linklocal_address_set*)</span></span> |
| ![Duo I P v6 Raw Packet Enviar ícone](./media/user-guide/netx-events/image71.png)    | <span data-ttu-id="18ca0-250">**Duo IPv6 Raw Packet Send** *(nxd_ipv6_raw_packet_send)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-250">**Duo IPv6 Raw Packet Send** (*nxd_ipv6_raw_packet_send)*</span></span> |
| ![Duo T C P Socket Peer Info Obter ícone](./media/user-guide/netx-events/image72.png)    | <span data-ttu-id="18ca0-252">**Duo TCP Socket Peer Info Get** *(nxd_tcp_socket_peer_info_get)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-252">**Duo TCP Socket Peer Info Get** (*nxd_tcp_socket_peer_info_get*)</span></span> |
| ![Ícone de interface de conjunto de tomada de duo T C P](./media/user-guide/netx-events/image73.png)    | <span data-ttu-id="18ca0-254">**Interface de conjunto de tomadas duo TCP** *(nxd_tcp_socket_set_interface)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-254">**Duo TCP Socket Set Interface** (*nxd_tcp_socket_set_interface*)</span></span> |
| ![Tomada de duo U D P Enviar ícone](./media/user-guide/netx-events/image74.png)    | <span data-ttu-id="18ca0-256">**Tomada dupla UDP Enviar** *(nxd_udp_socket_send)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-256">**Duo UDP Socket Send** (*nxd_udp_socket_send*)</span></span> |
| ![Ícone de interface de conjunto de tomada de P duo U D P](./media/user-guide/netx-events/image75.png)    | <span data-ttu-id="18ca0-258">**Interface de conjunto de tomadas UDP duo** *(nxd_udp_socket_set_interface)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-258">**Duo UDP Socket Set Interface** (*nxd_udp_socket_set_interface*)</span></span> |
| ![Ícone de extrato de fonte duo U D P](./media/user-guide/netx-events/image76.png)    | <span data-ttu-id="18ca0-260">**Extrato de origem Duo UDP** *(nxd_udp_source_extract)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-260">**Duo UDP Source Extract** (*nxd_udp_source_extract*)</span></span> |
| ![I C M P Ativar ícone](./media/user-guide/netx-events/image77.png)    | <span data-ttu-id="18ca0-262">**ICMP Enable** *(nx_icmp_enable)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-262">**ICMP Enable** (*nx_icmp_enable*)</span></span> |
| ![I C M P Informações Obter ícone](./media/user-guide/netx-events/image78.png)    | <span data-ttu-id="18ca0-264">**Informação do ICMP Obtém** *(nx_icmp_info_get)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-264">**ICMP Information Get** (*nx_icmp_info_get*)</span></span> |
| ![I C M P Ping ícone](./media/user-guide/netx-events/image79.png)    | <span data-ttu-id="18ca0-266">**ICMP Ping** *(nx_icmp_ping)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-266">**ICMP Ping** (*nx_icmp_ping*)</span></span> |
| ![I G M P Ativar ícone](./media/user-guide/netx-events/image80.png)    | <span data-ttu-id="18ca0-268">**IGMP Enable** *(nx_igmp_enable)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-268">**IGMP Enable** (*nx_igmp_enable*)</span></span> |
| ![I G M P Informações Obter ícone](./media/user-guide/netx-events/image81.png)    | <span data-ttu-id="18ca0-270">**Informação IGMP Obter** *(nx_igmp_info_get)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-270">**IGMP Information Get** (*nx_igmp_info_get*)</span></span> |
| ![I G M P Loopback Desativar o ícone](./media/user-guide/netx-events/image82.png)    | <span data-ttu-id="18ca0-272">**IGMP Loopback Disable** *(nx_igmp_loopback_disable)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-272">**IGMP Loopback Disable** (*nx_igmp_loopback_disable*)</span></span> |
| ![I G M P Loopback Ativar o ícone](./media/user-guide/netx-events/image83.png)    | <span data-ttu-id="18ca0-274">**IGMP Loopback Enable** *(nx_igmp_loopback_enable)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-274">**IGMP Loopback Enable** (*nx_igmp_loopback_enable*)</span></span> |
| ![I G M P Multicast Juntar ícone](./media/user-guide/netx-events/image84.png)    | <span data-ttu-id="18ca0-276">**IGMP Multicast Join** *(nx_igmp_multicast_join)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-276">**IGMP Multicast Join** (*nx_igmp_multicast_join*)</span></span> |
| ![I G M P Multicast Leave ícone](./media/user-guide/netx-events/image85.png)    | <span data-ttu-id="18ca0-278">**Licença Multicast IGMP** *(nx_igmp_multicast_leave)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-278">**IGMP Multicast Leave** (*nx_igmp_multicast_leave*)</span></span> |
| ![I P Endereço Alterar Ícone de Notificação](./media/user-guide/netx-events/image86.png)    | <span data-ttu-id="18ca0-280">**Notificação de alteração de endereço IP** *(nx_ip_address_change_notify)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-280">**IP Address Change Notify** (*nx_ip_address_change_notify*)</span></span> |
| ![I Endereço P Obter ícone](./media/user-guide/netx-events/image87.png)    | <span data-ttu-id="18ca0-282">**Endereço IP Get** *(nx_ip_address_get*)</span><span class="sxs-lookup"><span data-stu-id="18ca0-282">**IP Address Get** (*nx_ip_address_get*)</span></span> |
| ![Ícone de conjunto de endereços I P](./media/user-guide/netx-events/image88.png)    | <span data-ttu-id="18ca0-284">**Conjunto de endereços IP** *(nx_ip_address_set*)</span><span class="sxs-lookup"><span data-stu-id="18ca0-284">**IP Address Set** (*nx_ip_address_set*)</span></span> |
| ![I P Criar ícone](./media/user-guide/netx-events/image89.png)    | <span data-ttu-id="18ca0-286">**Criação IP** *(nx_ip_create)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-286">**IP Create** (*nx_ip_create*)</span></span> |
| ![I P Eliminar ícone](./media/user-guide/netx-events/image90.png)    | <span data-ttu-id="18ca0-288">**Eliminação IP** (*nx_ip_delete)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-288">**IP Delete** (*nx_ip_delete*)</span></span> |
| ![I P Ícone de comando direto do motorista](./media/user-guide/netx-events/image91.png)    | <span data-ttu-id="18ca0-290">**Comando Direto do Controlador IP** *(nx_ip_driver_direct_command)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-290">**IP Driver Direct Command** (*nx_ip_driver_direct_command*)</span></span> |
| ![I P Encaminhamento Desativar ícone](./media/user-guide/netx-events/image92.png)    | <span data-ttu-id="18ca0-292">**Desativação ip** *(nx_ip_forwarding_disable)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-292">**IP Forwarding Disable** (*nx_ip_forwarding_disable*)</span></span> |
| ![I P Encaminhamento Ativar Ícone](./media/user-guide/netx-events/image93.png)    | <span data-ttu-id="18ca0-294">**Viabilizar o encaminhamento IP** *(nx_ip_forwarding_enable)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-294">**IP Forwarding Enable** (*nx_ip_forwarding_enable*)</span></span> |
| ![I P Fragmento Desativar ícone](./media/user-guide/netx-events/image94.png)    | <span data-ttu-id="18ca0-296">**Desativação de fragmentos IP** *(nx_ip_fragment_disable)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-296">**IP Fragment Disable** (*nx_ip_fragment_disable*)</span></span> |
| ![I P Fragmento Ativar ícone](./media/user-guide/netx-events/image95.png)    | <span data-ttu-id="18ca0-298">**Ativação do fragmento IP** *(nx_ip_fragment_enable)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-298">**IP Fragment Enable** (*nx_ip_fragment_enable*)</span></span>  |
| ![I P Gateway Endereço Conjunto ícone](./media/user-guide/netx-events/image96.png)    | <span data-ttu-id="18ca0-300">**Conjunto de endereços IP Gateway** *(nx_ip_gateway_address_set*)</span><span class="sxs-lookup"><span data-stu-id="18ca0-300">**IP Gateway Address Set** (*nx_ip_gateway_address_set*)</span></span> |
| ![I P Informações Obter ícone](./media/user-guide/netx-events/image97.png)    | <span data-ttu-id="18ca0-302">**Informação IP Obter** *(nx_ip_info_get)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-302">**IP Information Get** (*nx_ip_info_get*)</span></span> |
| ![Ícone de anexação i interface P](./media/user-guide/netx-events/image98.png)    | <span data-ttu-id="18ca0-304">**Anexação de interface IP** *(nx_ip_interface_attach)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-304">**IP Interface Attach** (*nx_ip_interface_attach*)</span></span> |
| ![I P Interface Info Obter ícone](./media/user-guide/netx-events/image99.png)    | <span data-ttu-id="18ca0-306">**Informação de interface IP Obtém** *(nx_ip_interface_info_get)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-306">**IP Interface Info Get** (*nx_ip_interface_info_get*)</span></span> |
| ![I P Ícone de desativação de pacotes crus](./media/user-guide/netx-events/image100.png)    | <span data-ttu-id="18ca0-308">**Ip Raw Packet Disable** *(nx_ip_raw_packet_disable)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-308">**IP Raw Packet Disable** (*nx_ip_raw_packet_disable*)</span></span> |
| ![I P Pacote Cru Enable ícone](./media/user-guide/netx-events/image101.png)    | <span data-ttu-id="18ca0-310">**IP Raw Packet Enable** *(nx_ip_raw_packet_enable)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-310">**IP Raw Packet Enable** (*nx_ip_raw_packet_enable*)</span></span> |
| ![I P Pacote Cru Receber ícone](./media/user-guide/netx-events/image102.png)    | <span data-ttu-id="18ca0-312">**IP Raw Packet Receive** *(nx_ip_raw_packet_receive)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-312">**IP Raw Packet Receive** (*nx_ip_raw_packet_receive*)</span></span> |
| ![I P Pacote Cru Enviar ícone](./media/user-guide/netx-events/image103.png)    | <span data-ttu-id="18ca0-314">**IP Raw Packet Send** *(nx_ip_raw_packet_send)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-314">**IP Raw Packet Send** (*nx_ip_raw_packet_send*)</span></span> |
| ![I P Rota Estática Adicionar ícone](./media/user-guide/netx-events/image104.png)    | <span data-ttu-id="18ca0-316">**Adiciono de rota estática IP** *(nx_ip_static_route_add)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-316">**IP Static Route Add** (*nx_ip_static_route_add*)</span></span> |
| ![I P Rota Estática Eliminar ícone](./media/user-guide/netx-events/image105.png)    | <span data-ttu-id="18ca0-318">**Eliminação da Rota Estática IP** *(nx_ip_static_route_delete)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-318">**IP Static Route Delete** (*nx_ip_static_route_delete)*</span></span> |
| ![I P Status Check ícone](./media/user-guide/netx-events/image106.png)    | <span data-ttu-id="18ca0-320">**Verificação do estado do IP** *(nx_ip_status_check)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-320">**IP Status Check** (*nx_ip_status_check*)</span></span>|
| ![I P S E C Enable icon](./media/user-guide/netx-events/image107.png)    | <span data-ttu-id="18ca0-322">**Ipsec Enable** *(nx_ipsec_enable)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-322">**IPSEC Enable** (*nx_ipsec_enable)*</span></span> |
| ![Ícone de atribuição de pacote](./media/user-guide/netx-events/image108.png)    | <span data-ttu-id="18ca0-324">**Atribuição de pacotes** *(nx_packet_allocate)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-324">**Packet Allocate** (*nx_packet_allocate*)</span></span> |
| ![Ícone de cópia de pacote](./media/user-guide/netx-events/image109.png)    | <span data-ttu-id="18ca0-326">**Cópia do pacote** *(nx_packet_copy)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-326">**Packet Copy** (*nx_packet_copy*)</span></span> |
| ![Ícone de apêndice de dados de pacote](./media/user-guide/netx-events/image110.png)    | <span data-ttu-id="18ca0-328">**Apêndice de dados do pacote** *(nx_packet_data_append)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-328">**Packet Data Append** (*nx_packet_data_append*)</span></span> |
| ![Ícone de compensação de extrato de dados de pacote](./media/user-guide/netx-events/image111.png)    | <span data-ttu-id="18ca0-330">**Compensação de extrato de dados de** pacotes *(nx_packet_data_extract_offset)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-330">**Packet Data Extract Offset** (*nx_packet_data_extract_offset*)</span></span> |
| ![Ícone de recuperação de dados de pacote](./media/user-guide/netx-events/image112.png)    | <span data-ttu-id="18ca0-332">**Recuperação de dados de pacotes** *(nx_packet_data_retrieve)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-332">**Packet Data Retrieve** (*nx_packet_data_retrieve*)</span></span> |
| ![Comprimento do pacote Obter ícone](./media/user-guide/netx-events/image113.png)    | <span data-ttu-id="18ca0-334">**Comprimento do pacote Obter** *(nx_packet_length_get)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-334">**Packet Length Get** (*nx_packet_length_get*)</span></span> |
| ![Pacote Pool Criar ícone](./media/user-guide/netx-events/image114.png)    | <span data-ttu-id="18ca0-336">**Pacote De Criação de Piscina** *(nx_packet_pool_create)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-336">**Packet Pool Create** (*nx_packet_pool_create*)</span></span> |
| ![Ícone de excluir piscina de pacote](./media/user-guide/netx-events/image115.png)    | <span data-ttu-id="18ca0-338">**Eliminação do Pacote Pool** *(nx_packet_pool_delete)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-338">**Packet Pool Delete** (*nx_packet_pool_delete*)</span></span> |
| ![Informações de piscina de pacote Obter ícone](./media/user-guide/netx-events/image116.png)    | <span data-ttu-id="18ca0-340">**Informações da piscina de pacotes obter** *(nx_packet_pool_info_get)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-340">**Packet Pool Information Get** (*nx_packet_pool_info_get*)</span></span> |
| ![Ícone de lançamento de pacote](./media/user-guide/netx-events/image117.png)    | <span data-ttu-id="18ca0-342">**Lançamento do pacote** *(nx_packet_release)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-342">**Packet Release** (*nx_packet_release*)</span></span> |
| ![Ícone de lançamento de transmissão de pacote](./media/user-guide/netx-events/image118.png)    | <span data-ttu-id="18ca0-344">**Lançamento do pacote** *(nx_packet_transmit_release)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-344">**Packet Transmit Release** (*nx_packet_transmit_release*)</span></span> |
| ![R A R P Desativar o ícone](./media/user-guide/netx-events/image119.png)    | <span data-ttu-id="18ca0-346">**RaRP Disable** *(nx_rarp_disable)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-346">**RARP Disable** (*nx_rarp_disable*)</span></span> |
| ![R A R P Ativar o ícone](./media/user-guide/netx-events/image120.png)    | <span data-ttu-id="18ca0-348">**Ativar RARP** *(nx_rarp_enable)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-348">**RARP Enable** (*nx_rarp_enable*)</span></span> |
| ![R A R P Informações Obter ícone](./media/user-guide/netx-events/image121.png)    | <span data-ttu-id="18ca0-350">**RaRP Information Get** *(nx_rarp_info_get)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-350">**RARP Information Get** (*nx_rarp_info_get*)</span></span> |
| ![Ícone inicialize o sistema](./media/user-guide/netx-events/image122.png)    | <span data-ttu-id="18ca0-352">**Inicialização do Sistema** *(nx_system_initialize)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-352">**System Initialize** (*nx_system_initialize*)</span></span> |
| ![Ícone de ligação de tomada de cliente T C P](./media/user-guide/netx-events/image123.png)    | <span data-ttu-id="18ca0-354">**Ficha de tomada de cliente TCP** *(nx_tcp_client_socket_bind)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-354">**TCP Client Socket Bind** (*nx_tcp_client_socket_bind*)</span></span> |
| ![Ícone de ligação da tomada do cliente T C P](./media/user-guide/netx-events/image124.png)    | <span data-ttu-id="18ca0-356">**Ligação da tomada de cliente TCP** *(nx_tcp_client_socket_connect)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-356">**TCP Client Socket Connect** (*nx_tcp_client_socket_connect*)</span></span> |
| ![T C P Porta de tomada de cliente Obter ícone](./media/user-guide/netx-events/image125.png)    | <span data-ttu-id="18ca0-358">**Porta de tomada de cliente TCP** *(nx_tcp_client_socket_port_get)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-358">**TCP Client Socket Port Get** (*nx_tcp_client_socket_port_get*)</span></span> |
| ![T C P Tomada de cliente Unbind ícone](./media/user-guide/netx-events/image126.png)    | <span data-ttu-id="18ca0-360">**Tomada de cliente TCP Unbind** *(nx_tcp_client_socket_unbind)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-360">**TCP Client Socket Unbind** (*nx_tcp_client_socket_unbind*)</span></span> |
| ![T C P Ativar ícone](./media/user-guide/netx-events/image127.png)    | <span data-ttu-id="18ca0-362">**TCP Enable** *(nx_tcp_enable)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-362">**TCP Enable** (*nx_tcp_enable*)</span></span> |
| ![T C P Free Port Encontrar ícone](./media/user-guide/netx-events/image128.png)    | <span data-ttu-id="18ca0-364">**Achado portuário livre TCP** *(nx_tcp_free_port_find)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-364">**TCP Free Port Find** (*nx_tcp_free_port_find*)</span></span> |
| ![Informações T C P Obter ícone](./media/user-guide/netx-events/image129.png)    | <span data-ttu-id="18ca0-366">**Informação da TCP Obter** *(nx_tcp_info_get)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-366">**TCP Information Get** (*nx_tcp_info_get*)</span></span> |
| ![T C P Tomada de servidor Aceitar ícone](./media/user-guide/netx-events/image130.png)    | <span data-ttu-id="18ca0-368">**Aceitação da tomada do servidor TCP** *(nx_tcp_server_socket_accept)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-368">**TCP Server Socket Accept** (*nx_tcp_server_socket_accept*)</span></span> |
| ![T C P Tomada de servidor Ouvir ícone](./media/user-guide/netx-events/image131.png)    | <span data-ttu-id="18ca0-370">**Tomada de servidor TCP Ouvir** *(nx_tcp_server_socket_listen)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-370">**TCP Server Socket Listen** (*nx_tcp_server_socket_listen*)</span></span> |
| ![Ícone de relisten da tomada do servidor T C P](./media/user-guide/netx-events/image132.png)    | <span data-ttu-id="18ca0-372">**Tomada de tomada do servidor TCP Relisten** *(nx_tcp_server_socket_relisten)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-372">**TCP Server Socket Relisten** (*nx_tcp_server_socket_relisten*)</span></span> |
| ![T C P Servidor Socket Unacept Ícone](./media/user-guide/netx-events/image133.png)    | <span data-ttu-id="18ca0-374">**Tomada de servidor TCP Unaccept** *(nx_tcp_server_socket_unaccept)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-374">**TCP Server Socket Unaccept** (*nx_tcp_server_socket_unaccept*)</span></span> |
| ![T C P Tomada de servidor Unlisten ícone](./media/user-guide/netx-events/image134.png)    | <span data-ttu-id="18ca0-376">**Tomada de servidor TCP Unlisten** *(nx_tcp_server_socket_unlisten)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-376">**TCP Server Socket Unlisten** (*nx_tcp_server_socket_unlisten*)</span></span> |
| ![T C P Tomada Bytes Disponíveis Ícone](./media/user-guide/netx-events/image135.png)    | <span data-ttu-id="18ca0-378">**TCP Socket Bytes Disponíveis** *(nx_tcp_socket_bytes_available)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-378">**TCP Socket Bytes Available** (*nx_tcp_socket_bytes_available*)</span></span> |
| ![Tomada T C P Criar ícone](./media/user-guide/netx-events/image136.png)    | <span data-ttu-id="18ca0-380">**Criação de tomada tCP** *(nx_tcp_socket_create)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-380">**TCP Socket Create** (*nx_tcp_socket_create*)</span></span> |
| ![T C P Socket Eliminar ícone](./media/user-guide/netx-events/image137.png)    | <span data-ttu-id="18ca0-382">**Apagar tomadas TCP** *(nx_tcp_socket_delete)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-382">**TCP Socket Delete** (*nx_tcp_socket_delete*)</span></span> |
| ![T C P Ícone de desconexão da tomada](./media/user-guide/netx-events/image138.png)    | <span data-ttu-id="18ca0-384">**Desconexão da tomada TCP** *(nx_tcp_socket_disconnect)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-384">**TCP Socket Disconnect** (*nx_tcp_socket_disconnect*)</span></span> |
| ![Informações de tomada T C P Obtenha ícone](./media/user-guide/netx-events/image139.png)    | <span data-ttu-id="18ca0-386">**Informações sobre tomadas TCP Obtêm** *(nx_tcp_socket_info_get)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-386">**TCP Socket Information Get** (*nx_tcp_socket_info_get*)</span></span> |
| ![T C P Socket MSS Obter ícone](./media/user-guide/netx-events/image140.png)    | <span data-ttu-id="18ca0-388">**TCP Socket MSS Get** *(nx_tcp_socket_mss_get)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-388">**TCP Socket MSS Get** (*nx_tcp_socket_mss_get*)</span></span> |
| ![T C P Socket MSS Peer Obter ícone](./media/user-guide/netx-events/image141.png)    | <span data-ttu-id="18ca0-390">**TCP Socket MSS Peer Get** *(nx_tcp_socket_mss_peer_get)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-390">**TCP Socket MSS Peer Get** (*nx_tcp_socket_mss_peer_get*)</span></span> |
| ![T C P Tomada MSS Conjunto ícone](./media/user-guide/netx-events/image142.png)    | <span data-ttu-id="18ca0-392">**Conjunto de MSS de tomada de TCP** *(nx_tcp_socket_mss_set)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-392">**TCP Socket MSS Set** (*nx_tcp_socket_mss_set*)</span></span> |
| ![T C P Socket Peer Info Obter ícone](./media/user-guide/netx-events/image143.png)    | <span data-ttu-id="18ca0-394">**TCP Socket Peer Info Get** *(nx_tcp_socket_peer_info_get)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-394">**TCP Socket Peer Info Get** (*nx_tcp_socket_peer_info_get*)</span></span> |
| ![T C P Tomada Receber ícone](./media/user-guide/netx-events/image144.png)    | <span data-ttu-id="18ca0-396">**Tomada TCP Receber** *(nx_tcp_socket_receive)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-396">**TCP Socket Receive** (*nx_tcp_socket_receive*)</span></span> |
| ![T C P Receber Ícone de Notificação](./media/user-guide/netx-events/image145.png)    | <span data-ttu-id="18ca0-398">**Notificação de receção de tomada de TCP** *(nx_tcp_socket_receive_notify)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-398">**TCP Socket Receive Notify** (*nx_tcp_socket_receive_notify*)</span></span> |
| ![Tomada T C P Enviar ícone](./media/user-guide/netx-events/image146.png)    | <span data-ttu-id="18ca0-400">**Envio de tomada TCP** *(nx_tcp_socket_send)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-400">**TCP Socket Send** (*nx_tcp_socket_send*)</span></span> |
| ![T C P Tomada Estado De espera ícone](./media/user-guide/netx-events/image147.png)    | <span data-ttu-id="18ca0-402">**Espera do estado da tomada TCP** *(nx_tcp_socket_state_wait)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-402">**TCP Socket State Wait** (*nx_tcp_socket_state_wait*)</span></span> |
| ![T C P Tomada Transmitir Ícone de Configuração](./media/user-guide/netx-events/image148.png)    | <span data-ttu-id="18ca0-404">**Configuração de transmissão de tomada TCP** *(nx_tcp_socket_transmit_configure)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-404">**TCP Socket Transmit Configure** (*nx_tcp_socket_transmit_configure*)</span></span> |
| ![T C P Atualização da janela da janela notificando o ícone do conjunto](./media/user-guide/netx-events/image149.png)    | <span data-ttu-id="18ca0-406">**Conjunto de notificação da janela da tomada TCP** *(nx_tcp_socket_window_update_notify_set*)</span><span class="sxs-lookup"><span data-stu-id="18ca0-406">**TCP Socket Window Update Notify Set** (*nx_tcp_socket_window_update_notify_set*)</span></span>  |
| ![U D P Ativar ícone](./media/user-guide/netx-events/image150.png)    | <span data-ttu-id="18ca0-408">**Ativação UDP** *(nx_udp_enable)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-408">**UDP Enable** (*nx_udp_enable*)</span></span> |
| ![U D P Free Port Encontrar ícone](./media/user-guide/netx-events/image151.png)    | <span data-ttu-id="18ca0-410">**UDP Free Port Find** *(nx_udp_free_port_find)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-410">**UDP Free Port Find** (*nx_udp_free_port_find*)</span></span> |
| ![U D P Informações Obter ícone](./media/user-guide/netx-events/image152.png)    | <span data-ttu-id="18ca0-412">**Informação da UDP Obter** *(nx_udp_info_get)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-412">**UDP Information Get** (*nx_udp_info_get*)</span></span> |
| ![Ícone de ligação de tomada de U D P](./media/user-guide/netx-events/image153.png)    | <span data-ttu-id="18ca0-414">**Ligação de tomada uDP** *(nx_udp_socket_bind)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-414">**UDP Socket Bind** (*nx_udp_socket_bind*)</span></span> |
| ![U D P Socket Bytes Disponíveis ícone](./media/user-guide/netx-events/image154.png)    | <span data-ttu-id="18ca0-416">**Bytes de tomada uDP disponíveis** *(nx_udp_socket_bytes_available)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-416">**UDP Socket Bytes Available** (*nx_udp_socket_bytes_available*)</span></span> |
| ![Ícone de desativação de desativação da tomada de U D P](./media/user-guide/netx-events/image155.png)    | <span data-ttu-id="18ca0-418">**Desativação do checkum da tomada UDP** *(nx_udp_socket_checksum_disable)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-418">**UDP Socket Checksum Disable** (*nx_udp_socket_checksum_disable*)</span></span> |
| ![U D P Socket Checksum Ativar o ícone](./media/user-guide/netx-events/image156.png)    | <span data-ttu-id="18ca0-420">**Ativação do custo de verificação da tomada UDP** *(nx_udp_socket_checksum_enable)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-420">**UDP Socket Checksum Enable** *(nx_udp_socket_checksum_enable)*</span></span> |
| ![Tomada U D P Criar ícone](./media/user-guide/netx-events/image157.png)    | <span data-ttu-id="18ca0-422">**Criação de tomadas UDP** *(nx_udp_socket_create)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-422">**UDP Socket Create** (*nx_udp_socket_create*)</span></span> |
| ![U D P Socket Delete ícone](./media/user-guide/netx-events/image158.png)    | <span data-ttu-id="18ca0-424">**Eliminação da tomada UDP** *(nx_udp_socket_delete)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-424">**UDP Socket Delete** (*nx_udp_socket_delete*)</span></span> |
| ![U D Informações de tomada Obter ícone](./media/user-guide/netx-events/image159.png)    | <span data-ttu-id="18ca0-426">**Informações de tomada uDP Obtêm** *(nx_udp_socket_info_get)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-426">**UDP Socket Information Get** (*nx_udp_socket_info_get*)</span></span> |
| ![Ícone de conjunto de interface de tomada de U D P](./media/user-guide/netx-events/image160.png)    | <span data-ttu-id="18ca0-428">**Conjunto de interface de tomada UDP** *(nx_udp_socket_interface_set*)</span><span class="sxs-lookup"><span data-stu-id="18ca0-428">**UDP Socket Interface Set** (*nx_udp_socket_interface_set*)</span></span> |
| ![Porta de tomada U D P Obtenha ícone](./media/user-guide/netx-events/image161.png)    | <span data-ttu-id="18ca0-430">**Porta de tomada UDP Get** *(nx_udp_socket_port_get)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-430">**UDP Socket Port Get** (*nx_udp_socket_port_get*)</span></span> |
| ![Tomada U D P Receber ícone](./media/user-guide/netx-events/image162.png)    | <span data-ttu-id="18ca0-432">**Receção da tomada UDP** *(nx_udp_socket_receive)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-432">**UDP Socket Receive** (*nx_udp_socket_receive*)</span></span> |
| ![U D P Socket Receber Ícone de Notificação](./media/user-guide/netx-events/image163.png)    | <span data-ttu-id="18ca0-434">**Notificação de receção** de tomada udp *(nx_udp_socket_receive_notify)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-434">**UDP Socket Receive Notify** (*nx_udp_socket_receive_notify*)</span></span> |
| ![Tomada U D P Enviar ícone](./media/user-guide/netx-events/image164.png)    | <span data-ttu-id="18ca0-436">**Envio de tomada uDP** *(nx_udp_socket_send)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-436">**UDP Socket Send** (*nx_udp_socket_send*)</span></span> |
| ![Ícone unbind de tomada de U D P](./media/user-guide/netx-events/image165.png)    | <span data-ttu-id="18ca0-438">**Tomada UDP Unbind** *(nx_udp_socket_unbind)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-438">**UDP Socket Unbind** (*nx_udp_socket_unbind*)</span></span> |
| ![Ícone de extrato de fonte de U D P](./media/user-guide/netx-events/image166.png)    | <span data-ttu-id="18ca0-440">**Extrato de origem UDP** *(nx_udp_source_extract)*</span><span class="sxs-lookup"><span data-stu-id="18ca0-440">**UDP Source Extract** (*nx_udp_source_extract*)</span></span> |

## <a name="event-descriptions"></a><span data-ttu-id="18ca0-441">Descrições do evento</span><span class="sxs-lookup"><span data-stu-id="18ca0-441">Event Descriptions</span></span>

<span data-ttu-id="18ca0-442">As páginas seguintes descrevem os Eventos de Rastreio da NetX.</span><span class="sxs-lookup"><span data-stu-id="18ca0-442">The following pages describe the NetX Trace Events.</span></span>

### <a name="internal-arp-request-receive"></a><span data-ttu-id="18ca0-443">Pedido interno de ARP Receber</span><span class="sxs-lookup"><span data-stu-id="18ca0-443">Internal ARP Request Receive</span></span> 

#### <a name="internal-arp-request-receive"></a><span data-ttu-id="18ca0-444">Pedido interno de ARP receber</span><span class="sxs-lookup"><span data-stu-id="18ca0-444">Internal ARP request receive</span></span>

<span data-ttu-id="18ca0-445">**Ícone** ![ Ícone de receção de pedido de ARP interno](./media/user-guide/netx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-445">**Icon** ![Internal ARP request receive icon](./media/user-guide/netx-events/image1.png)</span></span>

<span data-ttu-id="18ca0-446">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-446">**Description**</span></span>

<span data-ttu-id="18ca0-447">Este evento representa um evento interno de receção de pedido de ARP netx.</span><span class="sxs-lookup"><span data-stu-id="18ca0-447">This event represents an internal NetX ARP request receive event.</span></span>

<span data-ttu-id="18ca0-448">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-448">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-449">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-449">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-450">Info Field 2: Endereço IP de origem</span><span class="sxs-lookup"><span data-stu-id="18ca0-450">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="18ca0-451">Info Field 3: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-451">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-452">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-452">Info Field 4: Not used</span></span>

### <a name="internal-arp-request-send"></a><span data-ttu-id="18ca0-453">Pedido interno de ARP Enviar</span><span class="sxs-lookup"><span data-stu-id="18ca0-453">Internal ARP Request Send</span></span> 

#### <a name="internal-arp-request-send"></a><span data-ttu-id="18ca0-454">Pedido interno de ARP enviar</span><span class="sxs-lookup"><span data-stu-id="18ca0-454">Internal ARP request send</span></span>

<span data-ttu-id="18ca0-455">**Ícone** ![ Pedido interno de ARP enviar ícone](./media/user-guide/netx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-455">**Icon** ![Internal ARP request send icon](./media/user-guide/netx-events/image2.png)</span></span>

<span data-ttu-id="18ca0-456">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-456">**Description**</span></span>

<span data-ttu-id="18ca0-457">Este evento representa um evento interno de envio de pedidos de ARP netx.</span><span class="sxs-lookup"><span data-stu-id="18ca0-457">This event represents an internal NetX ARP request send event.</span></span>

<span data-ttu-id="18ca0-458">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-458">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-459">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-459">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-460">Info Field 2: Endereço IP de destino</span><span class="sxs-lookup"><span data-stu-id="18ca0-460">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="18ca0-461">Info Field 3: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-461">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-462">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-462">Info Field 4: Not used</span></span>

### <a name="internal-arp-response-receive"></a><span data-ttu-id="18ca0-463">Resposta Interna da ARP Receber</span><span class="sxs-lookup"><span data-stu-id="18ca0-463">Internal ARP Response Receive</span></span> 

#### <a name="internal-arp-request-receive"></a><span data-ttu-id="18ca0-464">Pedido interno de ARP receber</span><span class="sxs-lookup"><span data-stu-id="18ca0-464">Internal ARP request receive</span></span>

<span data-ttu-id="18ca0-465">**Ícone** ![ O ícone de receção de pedido interno de ARP](./media/user-guide/netx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-465">**Icon** ![The Internal ARP request receive icon](./media/user-guide/netx-events/image3.png)</span></span>

<span data-ttu-id="18ca0-466">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-466">**Description**</span></span>

<span data-ttu-id="18ca0-467">Este evento representa um evento interno de receção de resposta netx ARP.</span><span class="sxs-lookup"><span data-stu-id="18ca0-467">This event represents an internal NetX ARP response receive event.</span></span>

<span data-ttu-id="18ca0-468">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-468">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-469">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-469">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-470">Info Field 2: Endereço IP de origem</span><span class="sxs-lookup"><span data-stu-id="18ca0-470">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="18ca0-471">Info Field 3: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-471">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-472">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-472">Info Field 4: Not used</span></span>

### <a name="internal-arp-response-send"></a><span data-ttu-id="18ca0-473">Envio de resposta interna da ARP</span><span class="sxs-lookup"><span data-stu-id="18ca0-473">Internal ARP Response Send</span></span> 

#### <a name="internal-arp-request-send"></a><span data-ttu-id="18ca0-474">Pedido interno de ARP enviar</span><span class="sxs-lookup"><span data-stu-id="18ca0-474">Internal ARP request send</span></span>

<span data-ttu-id="18ca0-475">**Ícone** ![ O pedido de ARP interno enviar ícone](./media/user-guide/netx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-475">**Icon** ![The Internal ARP request send icon](./media/user-guide/netx-events/image4.png)</span></span>

<span data-ttu-id="18ca0-476">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-476">**Description**</span></span>

<span data-ttu-id="18ca0-477">Este evento representa um evento interno de envio de resposta NetX.</span><span class="sxs-lookup"><span data-stu-id="18ca0-477">This event represents an internal NetX response send event.</span></span>

<span data-ttu-id="18ca0-478">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-478">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-479">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-479">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-480">Info Field 2: Endereço IP de destino</span><span class="sxs-lookup"><span data-stu-id="18ca0-480">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="18ca0-481">Info Field 3: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-481">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-482">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-482">Info Field 4: Not used</span></span>

### <a name="internal-icmp-receive"></a><span data-ttu-id="18ca0-483">ICMP Interno Receber</span><span class="sxs-lookup"><span data-stu-id="18ca0-483">Internal ICMP Receive</span></span> 

#### <a name="internal-icmp-receive"></a><span data-ttu-id="18ca0-484">ICMP interno receber</span><span class="sxs-lookup"><span data-stu-id="18ca0-484">Internal ICMP receive</span></span>

<span data-ttu-id="18ca0-485">**Ícone** ![ Ícone de receção interna I C M P](./media/user-guide/netx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-485">**Icon** ![Internal I C M P receive icon](./media/user-guide/netx-events/image5.png)</span></span>

<span data-ttu-id="18ca0-486">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-486">**Description**</span></span>

<span data-ttu-id="18ca0-487">Este evento representa um evento interno de receção do NetX ICMP.</span><span class="sxs-lookup"><span data-stu-id="18ca0-487">This event represents an internal NetX ICMP receive event.</span></span>

<span data-ttu-id="18ca0-488">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-488">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-489">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-489">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-490">Info Field 2: Endereço IP de origem</span><span class="sxs-lookup"><span data-stu-id="18ca0-490">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="18ca0-491">Info Field 3: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-491">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-492">Info Field 4: Palavra 0 do cabeçalho ICMP</span><span class="sxs-lookup"><span data-stu-id="18ca0-492">Info Field 4: Word 0 of ICMP header</span></span>

### <a name="internal-icmp-send"></a><span data-ttu-id="18ca0-493">Envio interno do ICMP</span><span class="sxs-lookup"><span data-stu-id="18ca0-493">Internal ICMP Send</span></span> 

#### <a name="internal-icmp-send"></a><span data-ttu-id="18ca0-494">Envio interno do ICMP</span><span class="sxs-lookup"><span data-stu-id="18ca0-494">Internal ICMP send</span></span>

<span data-ttu-id="18ca0-495">**Ícone** ![ I C M P interno enviar ícone](./media/user-guide/netx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-495">**Icon** ![Internal I C M P send icon](./media/user-guide/netx-events/image6.png)</span></span>

<span data-ttu-id="18ca0-496">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-496">**Description**</span></span>

<span data-ttu-id="18ca0-497">Este evento representa um evento interno de envio de NetX ICMP.</span><span class="sxs-lookup"><span data-stu-id="18ca0-497">This event represents an internal NetX ICMP send event.</span></span>

<span data-ttu-id="18ca0-498">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-498">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-499">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-499">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-500">Info Field 2: Endereço IP de destino</span><span class="sxs-lookup"><span data-stu-id="18ca0-500">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="18ca0-501">Info Field 3: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-501">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-502">Info Field 4: Palavra 0 do cabeçalho ICMP</span><span class="sxs-lookup"><span data-stu-id="18ca0-502">Info Field 4: Word 0 of ICMP header</span></span>

### <a name="internal-igmp-receive"></a><span data-ttu-id="18ca0-503">IGMP Interno Receber</span><span class="sxs-lookup"><span data-stu-id="18ca0-503">Internal IGMP Receive</span></span> 

#### <a name="internal-igmp-receive"></a><span data-ttu-id="18ca0-504">IGMP interno receber</span><span class="sxs-lookup"><span data-stu-id="18ca0-504">Internal IGMP receive</span></span>

<span data-ttu-id="18ca0-505">**Ícone** ![ Ícone de receção interna I G M P](./media/user-guide/netx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-505">**Icon** ![Internal I G M P receive icon](./media/user-guide/netx-events/image7.png)</span></span>

<span data-ttu-id="18ca0-506">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-506">**Description**</span></span>

<span data-ttu-id="18ca0-507">Este evento representa um evento interno de receção netx IGMP.</span><span class="sxs-lookup"><span data-stu-id="18ca0-507">This event represents an internal NetX IGMP receive event.</span></span>

<span data-ttu-id="18ca0-508">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-508">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-509">Info Field 1: Ponteiro IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-509">Info Field 1: IP Pointer</span></span>
- <span data-ttu-id="18ca0-510">Info Field 2: Endereço IP de origem</span><span class="sxs-lookup"><span data-stu-id="18ca0-510">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="18ca0-511">Info Field 3: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-511">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-512">Info Field 4: Palavra 0 do cabeçalho IGMP</span><span class="sxs-lookup"><span data-stu-id="18ca0-512">Info Field 4: Word 0 of IGMP header</span></span>

### <a name="internal-ip-receive"></a><span data-ttu-id="18ca0-513">Ip Interno Receber</span><span class="sxs-lookup"><span data-stu-id="18ca0-513">Internal IP Receive</span></span> 

#### <a name="internal-ip-receive"></a><span data-ttu-id="18ca0-514">Ip interno receber</span><span class="sxs-lookup"><span data-stu-id="18ca0-514">Internal IP receive</span></span>

<span data-ttu-id="18ca0-515">**Ícone** ![ Ícone de receção I P interno](./media/user-guide/netx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-515">**Icon** ![Internal I P receive icon](./media/user-guide/netx-events/image8.png)</span></span>

<span data-ttu-id="18ca0-516">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-516">**Description**</span></span>

<span data-ttu-id="18ca0-517">Este evento representa um evento interno de receção do NetX IP.</span><span class="sxs-lookup"><span data-stu-id="18ca0-517">This event represents an internal NetX IP receive event.</span></span>

<span data-ttu-id="18ca0-518">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-518">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-519">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-519">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-520">Info Field 2: Endereço IP de origem</span><span class="sxs-lookup"><span data-stu-id="18ca0-520">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="18ca0-521">Info Field 3: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-521">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-522">Info Field 4: Comprimento do pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-522">Info Field 4: Packet length</span></span>

### <a name="internal-ip-send"></a><span data-ttu-id="18ca0-523">Envio ip interno</span><span class="sxs-lookup"><span data-stu-id="18ca0-523">Internal IP Send</span></span>

#### <a name="internal-ip-send"></a><span data-ttu-id="18ca0-524">Envio ip interno</span><span class="sxs-lookup"><span data-stu-id="18ca0-524">Internal IP send</span></span>

<span data-ttu-id="18ca0-525">**Ícone** ![ I P interno enviar ícone](./media/user-guide/netx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-525">**Icon** ![Internal I P send icon](./media/user-guide/netx-events/image9.png)</span></span>

<span data-ttu-id="18ca0-526">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-526">**Description**</span></span>

<span data-ttu-id="18ca0-527">Este evento representa um evento interno de envio de IP NetX.</span><span class="sxs-lookup"><span data-stu-id="18ca0-527">This event represents an internal NetX IP send event.</span></span>

<span data-ttu-id="18ca0-528">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-528">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-529">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-529">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-530">Info Field 2: Endereço IP de destino</span><span class="sxs-lookup"><span data-stu-id="18ca0-530">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="18ca0-531">Info Field 3: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-531">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-532">Info Field 4: Comprimento do pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-532">Info Field 4: Packet length</span></span>

### <a name="internal-tcp-data-receive"></a><span data-ttu-id="18ca0-533">Dados internos da TCP recebem</span><span class="sxs-lookup"><span data-stu-id="18ca0-533">Internal TCP Data Receive</span></span> 

#### <a name="internal-tcp-data-receive"></a><span data-ttu-id="18ca0-534">Dados internos da TCP recebem</span><span class="sxs-lookup"><span data-stu-id="18ca0-534">Internal TCP Data Receive</span></span>

<span data-ttu-id="18ca0-535">**Ícone** ![ Ícone de receção de dados internos de T C P](./media/user-guide/netx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-535">**Icon** ![Internal T C P data receive icon](./media/user-guide/netx-events/image10.png)</span></span>

<span data-ttu-id="18ca0-536">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-536">**Description**</span></span>

<span data-ttu-id="18ca0-537">Este evento representa um evento interno de receção de dados da NetX TCP.</span><span class="sxs-lookup"><span data-stu-id="18ca0-537">This event represents an internal NetX TCP data receive event.</span></span>

<span data-ttu-id="18ca0-538">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-538">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-539">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-539">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-540">Info Field 2: Endereço IP de origem</span><span class="sxs-lookup"><span data-stu-id="18ca0-540">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="18ca0-541">Info Field 3: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-541">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-542">Info Field 4: Receber número de sequência</span><span class="sxs-lookup"><span data-stu-id="18ca0-542">Info Field 4: Receive sequence number</span></span>

### <a name="internal-tcp-data-send"></a><span data-ttu-id="18ca0-543">Dados internos da TCP enviam</span><span class="sxs-lookup"><span data-stu-id="18ca0-543">Internal TCP data send</span></span> 

#### <a name="internal-tcp-data-send"></a><span data-ttu-id="18ca0-544">Envio de dados internos da TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-544">Internal TCP Data Send</span></span>

<span data-ttu-id="18ca0-545">**Ícone** ![ Dados internos de T C P enviam ícone](./media/user-guide/netx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-545">**Icon** ![Internal T C P data send icon](./media/user-guide/netx-events/image11.png)</span></span>

<span data-ttu-id="18ca0-546">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-546">**Description**</span></span>

<span data-ttu-id="18ca0-547">Este evento representa um evento interno de envio de dados da NetX TCP.</span><span class="sxs-lookup"><span data-stu-id="18ca0-547">This event represents an internal NetX TCP data send event.</span></span>

<span data-ttu-id="18ca0-548">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-548">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-549">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-549">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-550">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-550">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-551">Info Field 3: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-551">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-552">Info Field 4: Transmitir número de sequência</span><span class="sxs-lookup"><span data-stu-id="18ca0-552">Info Field 4: Transmit sequence number</span></span>

### <a name="internal-tcp-fin-receive"></a><span data-ttu-id="18ca0-553">TCP FIN Interno Receber</span><span class="sxs-lookup"><span data-stu-id="18ca0-553">Internal TCP FIN Receive</span></span> 

#### <a name="internal-tcp-fin-receive"></a><span data-ttu-id="18ca0-554">A barbatana interna da TCP recebe</span><span class="sxs-lookup"><span data-stu-id="18ca0-554">Internal TCP fin receive</span></span>

<span data-ttu-id="18ca0-555">**Ícone** ![ Ícone de receção interna T C P F I N](./media/user-guide/netx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-555">**Icon** ![Internal T C P F I N receive icon](./media/user-guide/netx-events/image12.png)</span></span>

<span data-ttu-id="18ca0-556">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-556">**Description**</span></span>

<span data-ttu-id="18ca0-557">Este evento representa um evento interno da NetX TCP FIN.</span><span class="sxs-lookup"><span data-stu-id="18ca0-557">This event represents an internal NetX TCP FIN receive event.</span></span>

<span data-ttu-id="18ca0-558">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-558">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-559">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-559">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-560">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-560">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-561">Info Field 3: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-561">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-562">Info Field 4: Receber número de sequência</span><span class="sxs-lookup"><span data-stu-id="18ca0-562">Info Field 4: Receive sequence number</span></span>

### <a name="internal-tcp-fin-send"></a><span data-ttu-id="18ca0-563">TCP FIN Interno Enviar</span><span class="sxs-lookup"><span data-stu-id="18ca0-563">Internal TCP FIN Send</span></span> 

#### <a name="internal-tcp-fin-send"></a><span data-ttu-id="18ca0-564">Sistema interno de TCP enviar</span><span class="sxs-lookup"><span data-stu-id="18ca0-564">Internal TCP fin send</span></span>

<span data-ttu-id="18ca0-565">**Ícone** ![ Ícone de envio interno T C P F I N](./media/user-guide/netx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-565">**Icon** ![Internal T C P F I N send icon](./media/user-guide/netx-events/image13.png)</span></span>

<span data-ttu-id="18ca0-566">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-566">**Description**</span></span>

<span data-ttu-id="18ca0-567">Este evento representa um evento interno de envio de NetX TCP FIN.</span><span class="sxs-lookup"><span data-stu-id="18ca0-567">This event represents an internal NetX TCP FIN send event.</span></span>

<span data-ttu-id="18ca0-568">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-568">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-569">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-569">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-570">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-570">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-571">Info Field 3: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-571">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-572">Info Field 4:Transmitir número de sequência</span><span class="sxs-lookup"><span data-stu-id="18ca0-572">Info Field 4:Transmit sequence number</span></span>

### <a name="internal-tcp-rst-receive"></a><span data-ttu-id="18ca0-573">Receção Interna de TCP RST</span><span class="sxs-lookup"><span data-stu-id="18ca0-573">Internal TCP RST Receive</span></span> 

#### <a name="internal-tcp-rst-receive"></a><span data-ttu-id="18ca0-574">Receção Interna de TCP RST</span><span class="sxs-lookup"><span data-stu-id="18ca0-574">Internal TCP RST receive</span></span>

<span data-ttu-id="18ca0-575">**Ícone** ![ Ícone de receção interna T C P R S T](./media/user-guide/netx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-575">**Icon** ![Internal T C P R S T receive icon](./media/user-guide/netx-events/image14.png)</span></span>

<span data-ttu-id="18ca0-576">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-576">**Description**</span></span>

<span data-ttu-id="18ca0-577">Este evento representa um evento interno de receção de reset NetX TCP.</span><span class="sxs-lookup"><span data-stu-id="18ca0-577">This event represents an internal NetX TCP reset receive event.</span></span>

<span data-ttu-id="18ca0-578">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-578">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-579">Info Field 1: Ponteiro para a instância IP.</span><span class="sxs-lookup"><span data-stu-id="18ca0-579">Info Field 1: Pointer to the IP instance.</span></span>
- <span data-ttu-id="18ca0-580">Info Campo 2: Ponteiro para tomada.</span><span class="sxs-lookup"><span data-stu-id="18ca0-580">Info Field 2: Pointer to socket.</span></span>
- <span data-ttu-id="18ca0-581">Info Field 3: Ponteiro para pacote.</span><span class="sxs-lookup"><span data-stu-id="18ca0-581">Info Field 3: Pointer to packet.</span></span>
- <span data-ttu-id="18ca0-582">Info Campo 4: Receber número de sequência.</span><span class="sxs-lookup"><span data-stu-id="18ca0-582">Info Field 4: Receive sequence number.</span></span>

### <a name="internal-tcp-rst-send"></a><span data-ttu-id="18ca0-583">Envio interno de TCP RST</span><span class="sxs-lookup"><span data-stu-id="18ca0-583">Internal TCP RST Send</span></span> 

#### <a name="internal-tcp-rst-send"></a><span data-ttu-id="18ca0-584">Envio interno de TCP RST</span><span class="sxs-lookup"><span data-stu-id="18ca0-584">Internal TCP RST send</span></span>

<span data-ttu-id="18ca0-585">**Ícone** ![ Ícone de envio interno T C P R S T](./media/user-guide/netx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-585">**Icon** ![Internal T C P R S T send icon](./media/user-guide/netx-events/image15.png)</span></span>

<span data-ttu-id="18ca0-586">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-586">**Description**</span></span>

<span data-ttu-id="18ca0-587">Este evento representa um evento interno de reset NetX TCP.</span><span class="sxs-lookup"><span data-stu-id="18ca0-587">This event represents an internal NetX TCP reset send event.</span></span>

<span data-ttu-id="18ca0-588">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-588">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-589">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-589">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-590">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-590">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-591">Info Field 3: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-591">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-592">Info Field 4: Transmitir número de sequência</span><span class="sxs-lookup"><span data-stu-id="18ca0-592">Info Field 4: Transmit sequence number</span></span>

### <a name="internal-tcp-syn-receive"></a><span data-ttu-id="18ca0-593">Receção interna do TCP SYN</span><span class="sxs-lookup"><span data-stu-id="18ca0-593">Internal TCP SYN Receive</span></span> 

#### <a name="internal-tcp-syn-receive"></a><span data-ttu-id="18ca0-594">SINA Interna TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-594">Internal TCP SYN receive</span></span>

<span data-ttu-id="18ca0-595">**Ícone** ![ Ícone de receção interna T C P S Y N](./media/user-guide/netx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-595">**Icon** ![Internal T C P S Y N receive icon](./media/user-guide/netx-events/image16.png)</span></span>

<span data-ttu-id="18ca0-596">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-596">**Description**</span></span>

<span data-ttu-id="18ca0-597">Este evento representa um evento interno de receção netx TCP SYN.</span><span class="sxs-lookup"><span data-stu-id="18ca0-597">This event represents an internal NetX TCP SYN receive event.</span></span>

<span data-ttu-id="18ca0-598">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-598">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-599">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-599">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-600">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-600">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-601">Info Field 3: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-601">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-602">Info Field 4: Receber número de sequência</span><span class="sxs-lookup"><span data-stu-id="18ca0-602">Info Field 4: Receive sequence number</span></span>

### <a name="internal-tcp-syn-send"></a><span data-ttu-id="18ca0-603">Envio interno de TCP SYN</span><span class="sxs-lookup"><span data-stu-id="18ca0-603">Internal TCP SYN Send</span></span> 

#### <a name="internal-tcp-syn-send"></a><span data-ttu-id="18ca0-604">TCP SYN interno enviar</span><span class="sxs-lookup"><span data-stu-id="18ca0-604">Internal TCP SYN send</span></span>

<span data-ttu-id="18ca0-605">**Ícone** ![ Ícone de envio interno T C P S Y N](./media/user-guide/netx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-605">**Icon** ![Internal T C P S Y N send icon](./media/user-guide/netx-events/image17.png)</span></span>

<span data-ttu-id="18ca0-606">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-606">**Description**</span></span>

<span data-ttu-id="18ca0-607">Este evento representa um evento interno netx TCP SYN.</span><span class="sxs-lookup"><span data-stu-id="18ca0-607">This event represents an internal NetX TCP SYN send event.</span></span>

<span data-ttu-id="18ca0-608">Campos de Informação</span><span class="sxs-lookup"><span data-stu-id="18ca0-608">Information Fields</span></span> 

- <span data-ttu-id="18ca0-609">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-609">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-610">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-610">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-611">Info Field 3: Ponteiro para pacote -Info Field 4: Transmitir número de sequência</span><span class="sxs-lookup"><span data-stu-id="18ca0-611">Info Field 3: Pointer to packet -Info Field 4: Transmit sequence number</span></span>

### <a name="internal-udp-receive"></a><span data-ttu-id="18ca0-612">UDP Interna Receber</span><span class="sxs-lookup"><span data-stu-id="18ca0-612">Internal UDP Receive</span></span> 

#### <a name="internal-udp-receive"></a><span data-ttu-id="18ca0-613">UDP interna receber</span><span class="sxs-lookup"><span data-stu-id="18ca0-613">Internal UDP receive</span></span>

<span data-ttu-id="18ca0-614">**Ícone** ![ Ícone de receção interna de U D P](./media/user-guide/netx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-614">**Icon** ![Internal U D P receive icon](./media/user-guide/netx-events/image18.png)</span></span>

<span data-ttu-id="18ca0-615">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-615">**Description**</span></span>

<span data-ttu-id="18ca0-616">Este evento representa um evento interno de receção da UDP netx.</span><span class="sxs-lookup"><span data-stu-id="18ca0-616">This event represents an internal NetX UDP receive event.</span></span>

<span data-ttu-id="18ca0-617">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-617">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-618">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-618">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-619">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-619">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-620">Info Field 3: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-620">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-621">Info Field 4: Palavra 0 do cabeçalho da UDP</span><span class="sxs-lookup"><span data-stu-id="18ca0-621">Info Field 4: Word 0 of UDP header</span></span>

### <a name="internal-udp-send"></a><span data-ttu-id="18ca0-622">Envio interno da UDP</span><span class="sxs-lookup"><span data-stu-id="18ca0-622">Internal UDP Send</span></span> 

#### <a name="internal-udp-send"></a><span data-ttu-id="18ca0-623">Envio interno da UDP</span><span class="sxs-lookup"><span data-stu-id="18ca0-623">Internal UDP send</span></span>

<span data-ttu-id="18ca0-624">**Ícone** ![ Ícone de envio interno de U D P](./media/user-guide/netx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-624">**Icon** ![Internal U D P send icon](./media/user-guide/netx-events/image19.png)</span></span>

<span data-ttu-id="18ca0-625">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-625">**Description**</span></span>

<span data-ttu-id="18ca0-626">Este evento representa um evento interno de envio de UDP NetX.</span><span class="sxs-lookup"><span data-stu-id="18ca0-626">This event represents an internal NetX UDP send event.</span></span>

<span data-ttu-id="18ca0-627">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-627">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-628">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-628">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-629">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-629">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-630">Info Field 3: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-630">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-631">Info Field 4: Palavra 0 do cabeçalho da UDP</span><span class="sxs-lookup"><span data-stu-id="18ca0-631">Info Field 4: Word 0 of UDP header</span></span>

### <a name="internal-rarp-receive"></a><span data-ttu-id="18ca0-632">Receção interna da RARP</span><span class="sxs-lookup"><span data-stu-id="18ca0-632">Internal RARP Receive</span></span> 

#### <a name="internal-rarp-receive"></a><span data-ttu-id="18ca0-633">Receção interna da RARP</span><span class="sxs-lookup"><span data-stu-id="18ca0-633">Internal RARP receive</span></span> 

<span data-ttu-id="18ca0-634">**Ícone** ![ Ícone de receção R A R P interno](./media/user-guide/netx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-634">**Icon** ![Internal R A R P receive icon](./media/user-guide/netx-events/image20.png)</span></span>

<span data-ttu-id="18ca0-635">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-635">**Description**</span></span>

<span data-ttu-id="18ca0-636">Este evento representa um evento interno de receção netx RARP.</span><span class="sxs-lookup"><span data-stu-id="18ca0-636">This event represents an internal NetX RARP receive event.</span></span>

<span data-ttu-id="18ca0-637">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-637">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-638">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-638">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-639">Info Field 2: Endereço IP alvo</span><span class="sxs-lookup"><span data-stu-id="18ca0-639">Info Field 2: Target IP address</span></span>
- <span data-ttu-id="18ca0-640">Info Field 3: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-640">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-641">Info Field 4: Palavra 1 do cabeçalho RARP</span><span class="sxs-lookup"><span data-stu-id="18ca0-641">Info Field 4: Word 1 of RARP header</span></span>

### <a name="internal-rarp-send"></a><span data-ttu-id="18ca0-642">Envio interno da RARP</span><span class="sxs-lookup"><span data-stu-id="18ca0-642">Internal RARP Send</span></span> 

#### <a name="internal-rarp-send"></a><span data-ttu-id="18ca0-643">RaRP interno enviar</span><span class="sxs-lookup"><span data-stu-id="18ca0-643">Internal RARP send</span></span> 

<span data-ttu-id="18ca0-644">**Ícone** ![ Ícone de envio interno R A R P](./media/user-guide/netx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-644">**Icon** ![Internal R A R P send icon](./media/user-guide/netx-events/image21.png)</span></span>

<span data-ttu-id="18ca0-645">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-645">**Description**</span></span>

<span data-ttu-id="18ca0-646">Este evento representa um evento interno de envio netx RARP.</span><span class="sxs-lookup"><span data-stu-id="18ca0-646">This event represents an internal NetX RARP send event.</span></span>

<span data-ttu-id="18ca0-647">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-647">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-648">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-648">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-649">Info Field 2: Endereço IP alvo</span><span class="sxs-lookup"><span data-stu-id="18ca0-649">Info Field 2: Target IP address</span></span>
- <span data-ttu-id="18ca0-650">Info Field 3: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-650">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-651">Info Field 4: Palavra 1 do cabeçalho RARP</span><span class="sxs-lookup"><span data-stu-id="18ca0-651">Info Field 4: Word 1 of RARP header</span></span>

### <a name="internal-tcp-retry"></a><span data-ttu-id="18ca0-652">Redatry TCP interno</span><span class="sxs-lookup"><span data-stu-id="18ca0-652">Internal TCP Retry</span></span> 

#### <a name="internal-tcp-retry"></a><span data-ttu-id="18ca0-653">Redação interna de TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-653">Internal TCP retry</span></span> 

<span data-ttu-id="18ca0-654">**Ícone** ![ Ícone interno de retografia T C P](./media/user-guide/netx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-654">**Icon** ![Internal T C P retry icon](./media/user-guide/netx-events/image22.png)</span></span>

<span data-ttu-id="18ca0-655">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-655">**Description**</span></span>

<span data-ttu-id="18ca0-656">Este evento representa um evento interno de relemistenção netx TCP.</span><span class="sxs-lookup"><span data-stu-id="18ca0-656">This event represents an internal NetX TCP retry event.</span></span>

<span data-ttu-id="18ca0-657">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-657">**Information Fields**</span></span>
- <span data-ttu-id="18ca0-658">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-658">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-659">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-659">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-660">Info Field 3: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-660">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-661">Info Field 4: Número de retrós em queses</span><span class="sxs-lookup"><span data-stu-id="18ca0-661">Info Field 4: Number of retries</span></span>

### <a name="internal-tcp-state-change"></a><span data-ttu-id="18ca0-662">Mudança interna do estado da TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-662">Internal TCP State Change</span></span> 

#### <a name="internal-tcp-state-change"></a><span data-ttu-id="18ca0-663">Mudança interna do estado da TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-663">Internal TCP state change</span></span> 

<span data-ttu-id="18ca0-664">**Ícone** ![ Ícone de mudança de estado de T C P interno](./media/user-guide/netx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-664">**Icon** ![Internal T C P state change icon](./media/user-guide/netx-events/image23.png)</span></span>

<span data-ttu-id="18ca0-665">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-665">**Description**</span></span>

<span data-ttu-id="18ca0-666">Este evento representa um evento interno de mudança de estado netx TCP.</span><span class="sxs-lookup"><span data-stu-id="18ca0-666">This event represents an internal NetX TCP socket state change event.</span></span>

<span data-ttu-id="18ca0-667">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-667">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-668">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-668">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-669">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-669">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-670">Info Field 3: Estado anterior</span><span class="sxs-lookup"><span data-stu-id="18ca0-670">Info Field 3: Previous state</span></span>
- <span data-ttu-id="18ca0-671">Info Field 4: Novo estado</span><span class="sxs-lookup"><span data-stu-id="18ca0-671">Info Field 4: New state</span></span>

### <a name="internal-io-driver-packet-send"></a><span data-ttu-id="18ca0-672">Pacote de motorista interno enviar</span><span class="sxs-lookup"><span data-stu-id="18ca0-672">Internal I/O Driver Packet Send</span></span> 

#### <a name="internal-io-driver-packet-send"></a><span data-ttu-id="18ca0-673">Envio de pacote de motorista de I/O interno</span><span class="sxs-lookup"><span data-stu-id="18ca0-673">Internal I/O driver packet send</span></span>

<span data-ttu-id="18ca0-674">**Ícone** ![ Ícone de envio de pacote de motorista interno I/O](./media/user-guide/netx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-674">**Icon** ![Internal I / O driver packet send icon](./media/user-guide/netx-events/image24.png)</span></span>

<span data-ttu-id="18ca0-675">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-675">**Description**</span></span>

<span data-ttu-id="18ca0-676">Este evento representa um evento interno de envio de pacotes de pilotos NetX I/O.</span><span class="sxs-lookup"><span data-stu-id="18ca0-676">This event represents an internal NetX I/O driver packet send event.</span></span>

<span data-ttu-id="18ca0-677">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-677">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-678">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-678">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-679">Info Field 2: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-679">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-680">Info Field 3: Tamanho do pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-680">Info Field 3: Packet size</span></span>
- <span data-ttu-id="18ca0-681">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-681">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-initialize"></a><span data-ttu-id="18ca0-682">Inicialização interna do controlador de I/O</span><span class="sxs-lookup"><span data-stu-id="18ca0-682">Internal I/O Driver Initialize</span></span> 

#### <a name="internal-io-driver-initialize"></a><span data-ttu-id="18ca0-683">Inicialização do controlador de I/S interno</span><span class="sxs-lookup"><span data-stu-id="18ca0-683">Internal I/O driver initialize</span></span>

<span data-ttu-id="18ca0-684">**Ícone** ![ Ícone inicializo do condutor interno I/O](./media/user-guide/netx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-684">**Icon** ![Internal I / O driver initialize icon](./media/user-guide/netx-events/image25.png)</span></span>

<span data-ttu-id="18ca0-685">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-685">**Description**</span></span>

<span data-ttu-id="18ca0-686">Este evento representa um evento interno de inicialização do piloto NetX I/O.</span><span class="sxs-lookup"><span data-stu-id="18ca0-686">This event represents an internal NetX I/O driver initialize event.</span></span>

<span data-ttu-id="18ca0-687">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-687">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-688">Info Field 1: Ponteiro para a instância IP.</span><span class="sxs-lookup"><span data-stu-id="18ca0-688">Info Field 1: Pointer to the IP instance.</span></span>
- <span data-ttu-id="18ca0-689">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="18ca0-689">Info Field 2: Not used.</span></span>
- <span data-ttu-id="18ca0-690">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="18ca0-690">Info Field 3: Not used.</span></span>
- <span data-ttu-id="18ca0-691">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="18ca0-691">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-link-enable"></a><span data-ttu-id="18ca0-692">Ligação interna do controlador de I/O</span><span class="sxs-lookup"><span data-stu-id="18ca0-692">Internal I/O Driver Link Enable</span></span> 

#### <a name="internal-io-driver-link-enable"></a><span data-ttu-id="18ca0-693">Ligação interna do controlador de I/O ativar</span><span class="sxs-lookup"><span data-stu-id="18ca0-693">Internal I/O driver link enable</span></span>

<span data-ttu-id="18ca0-694">**Ícone** ![ Ligação interna do controlador I /O ativar ícone](./media/user-guide/netx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-694">**Icon** ![Internal I / O driver link enable icon](./media/user-guide/netx-events/image26.png)</span></span>

<span data-ttu-id="18ca0-695">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-695">**Description**</span></span>

<span data-ttu-id="18ca0-696">Este evento representa uma ligação interna do controlador NetX I/O que permite o evento.</span><span class="sxs-lookup"><span data-stu-id="18ca0-696">This event represents an internal NetX I/O driver link enable event.</span></span>

<span data-ttu-id="18ca0-697">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-697">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-698">Info Field 1: Ponteiro para a instância IP.</span><span class="sxs-lookup"><span data-stu-id="18ca0-698">Info Field 1: Pointer to the IP instance.</span></span>
- <span data-ttu-id="18ca0-699">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="18ca0-699">Info Field 2: Not used.</span></span>
- <span data-ttu-id="18ca0-700">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="18ca0-700">Info Field 3: Not used.</span></span>
- <span data-ttu-id="18ca0-701">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="18ca0-701">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-link-disable"></a><span data-ttu-id="18ca0-702">Ligação interna do controlador de I/O Desativada</span><span class="sxs-lookup"><span data-stu-id="18ca0-702">Internal I/O Driver Link Disable</span></span> 

#### <a name="internal-io-driver-link-disable"></a><span data-ttu-id="18ca0-703">Desativação interna da ligação do controlador de I/O</span><span class="sxs-lookup"><span data-stu-id="18ca0-703">Internal I/O driver link disable</span></span>

<span data-ttu-id="18ca0-704">**Ícone** ![ Ícone de desativação do controlador interno I/O](./media/user-guide/netx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-704">**Icon** ![Internal I / O driver link disable icon](./media/user-guide/netx-events/image27.png)</span></span>

<span data-ttu-id="18ca0-705">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-705">**Description**</span></span>

<span data-ttu-id="18ca0-706">Este evento representa um evento interno de desativação de ligação netx I/O.</span><span class="sxs-lookup"><span data-stu-id="18ca0-706">This event represents an internal NetX I/O driver link disable event.</span></span>

<span data-ttu-id="18ca0-707">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-707">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-708">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-708">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-709">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-709">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-710">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-710">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-711">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-711">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-packet-broadcast"></a><span data-ttu-id="18ca0-712">Transmissão interna do pacote de motorista de I/O</span><span class="sxs-lookup"><span data-stu-id="18ca0-712">Internal I/O Driver Packet Broadcast</span></span> 

#### <a name="internal-io-driver-packet-broadcast"></a><span data-ttu-id="18ca0-713">Transmissão interna do pacote de motorista de I/O</span><span class="sxs-lookup"><span data-stu-id="18ca0-713">Internal I/O driver packet broadcast</span></span>

<span data-ttu-id="18ca0-714">**Ícone** ![ Ícone de transmissão de pacote de motorista interno I /O](./media/user-guide/netx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-714">**Icon** ![Internal I / O driver packet broadcast icon](./media/user-guide/netx-events/image28.png)</span></span>

<span data-ttu-id="18ca0-715">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-715">**Description**</span></span>

<span data-ttu-id="18ca0-716">Este evento representa um evento interno de transmissão de pacotes de pilotos NetX I/O.</span><span class="sxs-lookup"><span data-stu-id="18ca0-716">This event represents an internal NetX I/O driver packet broadcast event.</span></span>

<span data-ttu-id="18ca0-717">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-717">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-718">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-718">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-719">Info Field 2: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-719">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-720">Info Field 3: Tamanho do pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-720">Info Field 3: Packet size</span></span>
- <span data-ttu-id="18ca0-721">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-721">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-arp-send"></a><span data-ttu-id="18ca0-722">Envio interno de ARP do condutor de I/O</span><span class="sxs-lookup"><span data-stu-id="18ca0-722">Internal I/O Driver ARP Send</span></span> 

#### <a name="internal-io-driver-arp-send"></a><span data-ttu-id="18ca0-723">Envio interno de ARP do condutor de I/O</span><span class="sxs-lookup"><span data-stu-id="18ca0-723">Internal I/O driver ARP send</span></span>

<span data-ttu-id="18ca0-724">**Ícone** ![ Ícone de envio de ARP do controlador interno I/O](./media/user-guide/netx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-724">**Icon** ![Internal I / O driver ARP send icon](./media/user-guide/netx-events/image29.png)</span></span>

<span data-ttu-id="18ca0-725">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-725">**Description**</span></span>

<span data-ttu-id="18ca0-726">Este evento representa um evento interno de envio de ARP do condutor netx I/O.</span><span class="sxs-lookup"><span data-stu-id="18ca0-726">This event represents an internal NetX I/O driver ARP send event.</span></span>

<span data-ttu-id="18ca0-727">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-727">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-728">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-728">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-729">Info Field 2: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-729">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-730">Info Field 3: Tamanho do pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-730">Info Field 3: Packet size</span></span>
- <span data-ttu-id="18ca0-731">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-731">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-arp-response-send"></a><span data-ttu-id="18ca0-732">Envio de resposta ARP do controlador interno de I/O</span><span class="sxs-lookup"><span data-stu-id="18ca0-732">Internal I/O Driver ARP Response Send</span></span> 

#### <a name="internal-io-driver-arp-response-send"></a><span data-ttu-id="18ca0-733">Envio de resposta ARP do controlador de I/O interno</span><span class="sxs-lookup"><span data-stu-id="18ca0-733">Internal I/O driver ARP response send</span></span>

<span data-ttu-id="18ca0-734">**Ícone** ![ Ícone de envio de resposta ARP do controlador interno I/O](./media/user-guide/netx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-734">**Icon** ![Internal I / O driver ARP response send icon](./media/user-guide/netx-events/image30.png)</span></span>

<span data-ttu-id="18ca0-735">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-735">**Description**</span></span>

<span data-ttu-id="18ca0-736">Este evento representa um evento interno de envio de resposta a ARP do condutor netx I/O.</span><span class="sxs-lookup"><span data-stu-id="18ca0-736">This event represents an internal NetX I/O driver ARP response send event.</span></span>

<span data-ttu-id="18ca0-737">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-737">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-738">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-738">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-739">Info Field 2: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-739">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-740">Info Field 3: Tamanho do pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-740">Info Field 3: Packet size</span></span>
- <span data-ttu-id="18ca0-741">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-741">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-rarp-send"></a><span data-ttu-id="18ca0-742">Envio interno de I/O do condutor RARP</span><span class="sxs-lookup"><span data-stu-id="18ca0-742">Internal I/O Driver RARP Send</span></span> 

#### <a name="internal-io-driver-rarp-send"></a><span data-ttu-id="18ca0-743">Piloto interno rarp de i/o enviar</span><span class="sxs-lookup"><span data-stu-id="18ca0-743">Internal I/O driver RARP send</span></span>

<span data-ttu-id="18ca0-744">**Ícone** ![ Ícone de envio de RARP do controlador interno I/O](./media/user-guide/netx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-744">**Icon** ![Internal I / O driver RARP send icon](./media/user-guide/netx-events/image31.png)</span></span>

<span data-ttu-id="18ca0-745">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-745">**Description**</span></span>

<span data-ttu-id="18ca0-746">Este evento representa um evento interno de envio de pilotos netx I/O RARP.</span><span class="sxs-lookup"><span data-stu-id="18ca0-746">This event represents an internal NetX I/O driver RARP send event.</span></span>

<span data-ttu-id="18ca0-747">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-747">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-748">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-748">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-749">Info Field 2: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-749">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-750">Info Field 3: Tamanho do pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-750">Info Field 3: Packet size</span></span>
- <span data-ttu-id="18ca0-751">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-751">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-multicast-join"></a><span data-ttu-id="18ca0-752">União Multicast do controlador de I/O interna</span><span class="sxs-lookup"><span data-stu-id="18ca0-752">Internal I/O Driver Multicast Join</span></span> 

#### <a name="internal-io-driver-multicast-join"></a><span data-ttu-id="18ca0-753">União multicast do condutor de I/O interna</span><span class="sxs-lookup"><span data-stu-id="18ca0-753">Internal I/O driver multicast join</span></span>

<span data-ttu-id="18ca0-754">**Ícone** ![ Ícone de união multicast do condutor interno I /O](./media/user-guide/netx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-754">**Icon** ![Internal I / O driver multicast join icon](./media/user-guide/netx-events/image32.png)</span></span>

<span data-ttu-id="18ca0-755">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-755">**Description**</span></span>

<span data-ttu-id="18ca0-756">Este evento representa um evento interno de associação multicast do piloto NetX I/O.</span><span class="sxs-lookup"><span data-stu-id="18ca0-756">This event represents an internal NetX I/O driver multicast join event.</span></span>

<span data-ttu-id="18ca0-757">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-757">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-758">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-758">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-759">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-759">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-760">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-760">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-761">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-761">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-multicast-leave"></a><span data-ttu-id="18ca0-762">Licença multicast do controlador interno de I/O</span><span class="sxs-lookup"><span data-stu-id="18ca0-762">Internal I/O Driver Multicast Leave</span></span> 

#### <a name="internal-io-driver-multicast-leave"></a><span data-ttu-id="18ca0-763">Licença multicast do condutor interno de I/O</span><span class="sxs-lookup"><span data-stu-id="18ca0-763">Internal I/O driver multicast leave</span></span>

<span data-ttu-id="18ca0-764">**Ícone** ![ Ícone de licença multicast do condutor interno I /O](./media/user-guide/netx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-764">**Icon** ![Internal I / O driver multicast leave icon](./media/user-guide/netx-events/image33.png)</span></span>

<span data-ttu-id="18ca0-765">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-765">**Description**</span></span>

<span data-ttu-id="18ca0-766">Este evento representa um evento interno de licença multicast do condutor NetX I/O.</span><span class="sxs-lookup"><span data-stu-id="18ca0-766">This event represents an internal NetX I/O driver multicast leave event.</span></span>

<span data-ttu-id="18ca0-767">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-767">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-768">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-768">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-769">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-769">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-770">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-770">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-771">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-771">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-status"></a><span data-ttu-id="18ca0-772">O controlador interno de I/O obtém o estado</span><span class="sxs-lookup"><span data-stu-id="18ca0-772">Internal I/O Driver Get Status</span></span> 

#### <a name="internal-io-driver-get-status"></a><span data-ttu-id="18ca0-773">O controlador interno de I/O obtém o estado</span><span class="sxs-lookup"><span data-stu-id="18ca0-773">Internal I/O driver get status</span></span>

<span data-ttu-id="18ca0-774">**Ícone** ![ Motorista interno I/O obter ícone de estado](./media/user-guide/netx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-774">**Icon** ![Internal I / O driver get status icon](./media/user-guide/netx-events/image34.png)</span></span>

<span data-ttu-id="18ca0-775">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-775">**Description**</span></span>

<span data-ttu-id="18ca0-776">Este evento representa um evento interno do piloto netx I/O.</span><span class="sxs-lookup"><span data-stu-id="18ca0-776">This event represents an internal NetX I/O driver get status event.</span></span>

<span data-ttu-id="18ca0-777">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-777">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-778">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-778">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-779">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-779">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-780">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-780">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-781">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-781">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-speed"></a><span data-ttu-id="18ca0-782">Condutor interno de I/O obtém velocidade</span><span class="sxs-lookup"><span data-stu-id="18ca0-782">Internal I/O Driver Get Speed</span></span> 

#### <a name="internal-io-driver-get-speed"></a><span data-ttu-id="18ca0-783">Condutor de I/O interno obtém velocidade</span><span class="sxs-lookup"><span data-stu-id="18ca0-783">Internal I/O driver get speed</span></span>

<span data-ttu-id="18ca0-784">**Ícone** ![ Motorista interno I /O obter ícone de velocidade](./media/user-guide/netx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-784">**Icon** ![Internal I / O driver get speed icon](./media/user-guide/netx-events/image35.png)</span></span>

<span data-ttu-id="18ca0-785">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-785">**Description**</span></span>

<span data-ttu-id="18ca0-786">Este evento representa um piloto interno netx I/O obter evento de velocidade.</span><span class="sxs-lookup"><span data-stu-id="18ca0-786">This event represents an internal NetX I/O driver get speed event.</span></span>

<span data-ttu-id="18ca0-787">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-787">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-788">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-788">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-789">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-789">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-790">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-790">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-791">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-791">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-duplex-type"></a><span data-ttu-id="18ca0-792">Controlador interno de I/O obter tipo duplex</span><span class="sxs-lookup"><span data-stu-id="18ca0-792">Internal I/O Driver Get Duplex Type</span></span> 

#### <a name="internal-io-driver-get-duplex-type"></a><span data-ttu-id="18ca0-793">O condutor interno de I/O obtém o tipo duplex</span><span class="sxs-lookup"><span data-stu-id="18ca0-793">Internal I/O driver get duplex type</span></span>

<span data-ttu-id="18ca0-794">**Ícone** ![ Motorista interno I /O obter ícone do tipo duplex](./media/user-guide/netx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-794">**Icon** ![Internal I / O driver get duplex type icon](./media/user-guide/netx-events/image36.png)</span></span>

<span data-ttu-id="18ca0-795">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-795">**Description**</span></span>

<span data-ttu-id="18ca0-796">Este evento representa um controlador interno netx I/O obter evento tipo duplex.</span><span class="sxs-lookup"><span data-stu-id="18ca0-796">This event represents an internal NetX I/O driver get duplex type event.</span></span>

<span data-ttu-id="18ca0-797">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-797">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-798">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-798">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-799">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-799">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-800">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-800">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-801">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-801">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-error-count"></a><span data-ttu-id="18ca0-802">Controlador interno de I/O obtenha contagem de erros</span><span class="sxs-lookup"><span data-stu-id="18ca0-802">Internal I/O Driver Get Error Count</span></span>

#### <a name="internal-io-driver-get-error-count"></a><span data-ttu-id="18ca0-803">Controlador de I/O interno obtém contagem de erros</span><span class="sxs-lookup"><span data-stu-id="18ca0-803">Internal I/O driver get error count</span></span>

<span data-ttu-id="18ca0-804">**Ícone** ![ Controlador interno I /O obtém ícone de contagem de erros](./media/user-guide/netx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-804">**Icon** ![Internal I / O driver get error count icon](./media/user-guide/netx-events/image37.png)</span></span>

<span data-ttu-id="18ca0-805">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-805">**Description**</span></span>

<span data-ttu-id="18ca0-806">Este evento representa um controlador Interno NetX I/O obter evento de contagem de erros.</span><span class="sxs-lookup"><span data-stu-id="18ca0-806">This event represents an internal NetX I/O driver get error count event.</span></span>

<span data-ttu-id="18ca0-807">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-807">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-808">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-808">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-809">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-809">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-810">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-810">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-811">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-811">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-rx-count"></a><span data-ttu-id="18ca0-812">Motorista interno de I/O obtém conta de RX</span><span class="sxs-lookup"><span data-stu-id="18ca0-812">Internal I/O Driver Get RX Count</span></span> 

#### <a name="internal-io-driver-get-rx-count"></a><span data-ttu-id="18ca0-813">Condutor de I/O interno obtém contagem de RX</span><span class="sxs-lookup"><span data-stu-id="18ca0-813">Internal I/O driver get RX count</span></span>

<span data-ttu-id="18ca0-814">**Ícone** ![ Piloto interno I /O obtém ícone de contagem de RX](./media/user-guide/netx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-814">**Icon** ![Internal I / O driver get RX count icon](./media/user-guide/netx-events/image38.png)</span></span>

<span data-ttu-id="18ca0-815">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-815">**Description**</span></span>

<span data-ttu-id="18ca0-816">Este evento representa um piloto interno netx I/O obter evento de contagem RX.</span><span class="sxs-lookup"><span data-stu-id="18ca0-816">This event represents an internal NetX I/O driver get RX count event.</span></span>

<span data-ttu-id="18ca0-817">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-817">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-818">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-818">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-819">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-819">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-820">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-820">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-821">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-821">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-tx-count"></a><span data-ttu-id="18ca0-822">Condutor interno de I/O obtém contagem de TX</span><span class="sxs-lookup"><span data-stu-id="18ca0-822">Internal I/O Driver Get TX Count</span></span> 

#### <a name="internal-io-driver-get-tx-count"></a><span data-ttu-id="18ca0-823">Condutor de I/O interno obtém contagem de TX</span><span class="sxs-lookup"><span data-stu-id="18ca0-823">Internal I/O driver get TX count</span></span>

<span data-ttu-id="18ca0-824">**Ícone** ![ Piloto interno I /O obtém ícone de contagem de T X](./media/user-guide/netx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-824">**Icon** ![Internal I / O driver get T X count icon](./media/user-guide/netx-events/image39.png)</span></span>

<span data-ttu-id="18ca0-825">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-825">**Description**</span></span>

<span data-ttu-id="18ca0-826">Este evento representa um piloto interno netx I/O obter evento de contagem de TX.</span><span class="sxs-lookup"><span data-stu-id="18ca0-826">This event represents an internal NetX I/O driver get TX count event.</span></span>

<span data-ttu-id="18ca0-827">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-827">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-828">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-828">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-829">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-829">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-830">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-830">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-831">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-831">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-allocation-errors"></a><span data-ttu-id="18ca0-832">Condutor interno de I/O obtém erros de atribuição</span><span class="sxs-lookup"><span data-stu-id="18ca0-832">Internal I/O Driver Get Allocation Errors</span></span> 

#### <a name="internal-io-driver-get-allocation-errors"></a><span data-ttu-id="18ca0-833">Condutor de I/O interno obtém erros de atribuição</span><span class="sxs-lookup"><span data-stu-id="18ca0-833">Internal I/O driver get allocation errors</span></span>

<span data-ttu-id="18ca0-834">**Ícone** ![ Condutor interno I/O obtém ícone de erros de atribuição](./media/user-guide/netx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-834">**Icon** ![Internal I / O driver get allocation errors icon](./media/user-guide/netx-events/image40.png)</span></span>

<span data-ttu-id="18ca0-835">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-835">**Description**</span></span>

<span data-ttu-id="18ca0-836">Este evento representa um piloto interno netx I/O obter evento de erros de atribuição.</span><span class="sxs-lookup"><span data-stu-id="18ca0-836">This event represents an internal NetX I/O driver get allocation errors event.</span></span>

<span data-ttu-id="18ca0-837">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-837">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-838">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-838">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-839">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-839">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-840">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-840">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-841">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-841">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="18ca0-842">Condutor interno de I/O Des-initialize</span><span class="sxs-lookup"><span data-stu-id="18ca0-842">Internal I/O Driver Un-initialize</span></span> 

#### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="18ca0-843">Condutor interno de I/O desa inicializar</span><span class="sxs-lookup"><span data-stu-id="18ca0-843">Internal I/O driver un-initialize</span></span> 

<span data-ttu-id="18ca0-844">**Ícone** ![ Ícone interno I / O do condutor des-initialize](./media/user-guide/netx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-844">**Icon** ![Internal I / O driver un-initialize icon](./media/user-guide/netx-events/image41.png)</span></span>

<span data-ttu-id="18ca0-845">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-845">**Description**</span></span>

<span data-ttu-id="18ca0-846">Este evento representa um evento interno de des-initialize do piloto netx I/O.</span><span class="sxs-lookup"><span data-stu-id="18ca0-846">This event represents an internal NetX I/O driver un-initialize event.</span></span>

<span data-ttu-id="18ca0-847">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-847">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-848">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-848">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-849">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-849">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-850">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-850">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-851">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-851">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-deferred-processing"></a><span data-ttu-id="18ca0-852">Processamento diferido interno do controlador de I/O</span><span class="sxs-lookup"><span data-stu-id="18ca0-852">Internal I/O Driver Deferred Processing</span></span> 

#### <a name="internal-io-driver-deferred-processing"></a><span data-ttu-id="18ca0-853">O controlador interno de I/O diferido</span><span class="sxs-lookup"><span data-stu-id="18ca0-853">Internal I/O driver deferred processing</span></span> 

<span data-ttu-id="18ca0-854">**Ícone** ![ Ícone de processamento diferido do controlador interno I/O](./media/user-guide/netx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-854">**Icon** ![Internal I / O driver deferred processing icon](./media/user-guide/netx-events/image42.png)</span></span>

<span data-ttu-id="18ca0-855">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-855">**Description**</span></span>

<span data-ttu-id="18ca0-856">Este evento representa um evento interno de processamento diferido do piloto NetX I/O.</span><span class="sxs-lookup"><span data-stu-id="18ca0-856">This event represents an internal NetX I/O driver deferred processing event.</span></span>

<span data-ttu-id="18ca0-857">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-857">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-858">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-858">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-859">Info Field 2: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-859">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-860">Info Field 3: Comprimento do pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-860">Info Field 3: Packet length</span></span>
- <span data-ttu-id="18ca0-861">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-861">Info Field 4: Not used</span></span>

### <a name="arp-dynamic-entries-invalidate"></a><span data-ttu-id="18ca0-862">Entradas dinâmicas ARP invalidam</span><span class="sxs-lookup"><span data-stu-id="18ca0-862">ARP Dynamic Entries Invalidate</span></span> 

#### <a name="nx_arp_dynamic_entries_invalidate"></a><span data-ttu-id="18ca0-863">nx_arp_dynamic_entries_invalidate</span><span class="sxs-lookup"><span data-stu-id="18ca0-863">nx_arp_dynamic_entries_invalidate</span></span>

<span data-ttu-id="18ca0-864">**Ícone** ![ Um ícone invalidado de entradas dinâmicas R P](./media/user-guide/netx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-864">**Icon** ![A R P Dynamic Entries Invalidate icon](./media/user-guide/netx-events/image43.png)</span></span>

<span data-ttu-id="18ca0-865">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-865">**Description**</span></span>

<span data-ttu-id="18ca0-866">Este evento representa invalidar todos os ARP dinâmicos inteiros através de nx_arp_dynamic_entries_invalidate.</span><span class="sxs-lookup"><span data-stu-id="18ca0-866">This event represents invalidating all dynamic ARP entires via nx_arp_dynamic_entries_invalidate.</span></span>

<span data-ttu-id="18ca0-867">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-867">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-868">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-868">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-869">Info Field 2: Entradas invalidadas</span><span class="sxs-lookup"><span data-stu-id="18ca0-869">Info Field 2: Entries invalidated</span></span>
- <span data-ttu-id="18ca0-870">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-870">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-871">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-871">Info Field 4: Not used</span></span>

### <a name="arp-dynamic-entry-set"></a><span data-ttu-id="18ca0-872">Conjunto de entrada dinâmica ARP</span><span class="sxs-lookup"><span data-stu-id="18ca0-872">ARP Dynamic Entry Set</span></span> 

#### <a name="nx_arp_dynamic_entry_set"></a><span data-ttu-id="18ca0-873">nx_arp_dynamic_entry_set</span><span class="sxs-lookup"><span data-stu-id="18ca0-873">nx_arp_dynamic_entry_set</span></span>

<span data-ttu-id="18ca0-874">**Ícone** ![ Um ícone de conjunto de entrada dinâmica R P](./media/user-guide/netx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-874">**Icon** ![A R P Dynamic Entry Set icon](./media/user-guide/netx-events/image44.png)</span></span>

<span data-ttu-id="18ca0-875">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-875">**Description**</span></span>

<span data-ttu-id="18ca0-876">Este evento representa a definição de uma entrada dinâmica de ARP através de nx_arp_dynamic_entry_set.</span><span class="sxs-lookup"><span data-stu-id="18ca0-876">This event represents setting a dynamic ARP entry via nx_arp_dynamic_entry_set.</span></span>

<span data-ttu-id="18ca0-877">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-877">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-878">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-878">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-879">Info Field 2: endereço IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-879">Info Field 2: IP address</span></span>
- <span data-ttu-id="18ca0-880">Info Field 3: Endereço físico (MSW)</span><span class="sxs-lookup"><span data-stu-id="18ca0-880">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="18ca0-881">Info Field 4: Endereço físico (LSW)</span><span class="sxs-lookup"><span data-stu-id="18ca0-881">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-enable"></a><span data-ttu-id="18ca0-882">Ativar a ARP</span><span class="sxs-lookup"><span data-stu-id="18ca0-882">ARP Enable</span></span> 

#### <a name="nx_arp_enable"></a><span data-ttu-id="18ca0-883">nx_arp_enable</span><span class="sxs-lookup"><span data-stu-id="18ca0-883">nx_arp_enable</span></span>

<span data-ttu-id="18ca0-884">**Ícone** ![ Um ícone de ativação R P](./media/user-guide/netx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-884">**Icon** ![A R P enable icon](./media/user-guide/netx-events/image45.png)</span></span>

<span data-ttu-id="18ca0-885">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-885">**Description**</span></span>

<span data-ttu-id="18ca0-886">Este evento representa permitir a ARP através de nx_arp_enable.</span><span class="sxs-lookup"><span data-stu-id="18ca0-886">This event represents enabling ARP via nx_arp_enable.</span></span>

<span data-ttu-id="18ca0-887">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-887">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-888">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-888">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-889">Info Field 2: Ponteiro de memória de cache ARP</span><span class="sxs-lookup"><span data-stu-id="18ca0-889">Info Field 2: ARP cache memory pointer</span></span>
- <span data-ttu-id="18ca0-890">Info Field 3: Tamanho da memória da cache ARP</span><span class="sxs-lookup"><span data-stu-id="18ca0-890">Info Field 3: ARP cache memory size</span></span>
- <span data-ttu-id="18ca0-891">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-891">Info Field 4: Not used</span></span>

### <a name="arp-gratuitous-send"></a><span data-ttu-id="18ca0-892">Envio Gratuito ARP</span><span class="sxs-lookup"><span data-stu-id="18ca0-892">ARP Gratuitous Send</span></span> 

#### <a name="nx_arp_gratuitous_send"></a><span data-ttu-id="18ca0-893">nx_arp_gratuitous_send</span><span class="sxs-lookup"><span data-stu-id="18ca0-893">nx_arp_gratuitous_send</span></span>

<span data-ttu-id="18ca0-894">**Ícone** ![ Um ícone de envio gratuito R P](./media/user-guide/netx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-894">**Icon** ![A R P gratuitous send icon](./media/user-guide/netx-events/image46.png)</span></span>

<span data-ttu-id="18ca0-895">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-895">**Description**</span></span>

<span data-ttu-id="18ca0-896">Este evento representa um envio gratuito da ARP através de nx_arp_gratuitous_send.</span><span class="sxs-lookup"><span data-stu-id="18ca0-896">This event represents a gratuitous ARP send via nx_arp_gratuitous_send.</span></span>

<span data-ttu-id="18ca0-897">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-897">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-898">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-898">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-899">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-899">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-900">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-900">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-901">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-901">Info Field 4: Not used</span></span>

### <a name="arp-hardware-address-find"></a><span data-ttu-id="18ca0-902">Encontrar endereço de hardware ARP</span><span class="sxs-lookup"><span data-stu-id="18ca0-902">ARP Hardware Address Find</span></span> 

#### <a name="nx_arp_hardware_address_find"></a><span data-ttu-id="18ca0-903">nx_arp_hardware_address_find</span><span class="sxs-lookup"><span data-stu-id="18ca0-903">nx_arp_hardware_address_find</span></span>

<span data-ttu-id="18ca0-904">**Ícone** ![ Um ícone de endereço de hardware R P](./media/user-guide/netx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-904">**Icon** ![A R P Hardware Address Find icon](./media/user-guide/netx-events/image47.png)</span></span>

<span data-ttu-id="18ca0-905">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-905">**Description**</span></span>

<span data-ttu-id="18ca0-906">Este evento representa encontrar uma morada física através de nx_arp_hardware_address_find.</span><span class="sxs-lookup"><span data-stu-id="18ca0-906">This event represents finding a physical address via nx_arp_hardware_address_find.</span></span>

<span data-ttu-id="18ca0-907">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-907">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-908">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-908">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-909">Info Field 2: endereço IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-909">Info Field 2: IP address</span></span>
- <span data-ttu-id="18ca0-910">Info Field 3: Endereço físico (MSW)</span><span class="sxs-lookup"><span data-stu-id="18ca0-910">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="18ca0-911">Info Field 4: Endereço físico (LSW)</span><span class="sxs-lookup"><span data-stu-id="18ca0-911">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-information-get"></a><span data-ttu-id="18ca0-912">Informação ARP Obtém</span><span class="sxs-lookup"><span data-stu-id="18ca0-912">ARP Information Get</span></span> 

#### <a name="nx_arp_info_get"></a><span data-ttu-id="18ca0-913">nx_arp_info_get</span><span class="sxs-lookup"><span data-stu-id="18ca0-913">nx_arp_info_get</span></span>

<span data-ttu-id="18ca0-914">**Ícone** ![ Um ícone de informação R P obter](./media/user-guide/netx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-914">**Icon** ![A R P informition get icon](./media/user-guide/netx-events/image48.png)</span></span>

<span data-ttu-id="18ca0-915">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-915">**Description**</span></span>

<span data-ttu-id="18ca0-916">Este evento representa a obtenção de informação através de nx_arp_info_get.</span><span class="sxs-lookup"><span data-stu-id="18ca0-916">This event represents getting information via nx_arp_info_get.</span></span>

<span data-ttu-id="18ca0-917">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-917">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-918">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-918">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-919">Info Field 2: ARPs enviados</span><span class="sxs-lookup"><span data-stu-id="18ca0-919">Info Field 2: ARPs sent</span></span>
- <span data-ttu-id="18ca0-920">Info Field 3: Respostas ARP</span><span class="sxs-lookup"><span data-stu-id="18ca0-920">Info Field 3: ARP responses</span></span>
- <span data-ttu-id="18ca0-921">Info Field 4: ARPs recebido</span><span class="sxs-lookup"><span data-stu-id="18ca0-921">Info Field 4: ARPs received</span></span>

### <a name="arp-ip-address-find"></a><span data-ttu-id="18ca0-922">Encontrar endereço IP ARP</span><span class="sxs-lookup"><span data-stu-id="18ca0-922">ARP IP Address Find</span></span> 

#### <a name="nx_arp_ip_address_find"></a><span data-ttu-id="18ca0-923">nx_arp_ip_address_find</span><span class="sxs-lookup"><span data-stu-id="18ca0-923">nx_arp_ip_address_find</span></span>

<span data-ttu-id="18ca0-924">**Ícone** ![ Um endereço R P I P encontrar ícone](./media/user-guide/netx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-924">**Icon** ![A R P I P address find icon](./media/user-guide/netx-events/image49.png)</span></span>

<span data-ttu-id="18ca0-925">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-925">**Description**</span></span>

<span data-ttu-id="18ca0-926">Este evento representa encontrar um endereço IP associado ao endereço físico fornecido através de nx_arp_ip_address_find.</span><span class="sxs-lookup"><span data-stu-id="18ca0-926">This event represents finding an IP address associated with the supplied physical address via nx_arp_ip_address_find.</span></span>

<span data-ttu-id="18ca0-927">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-927">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-928">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-928">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-929">Info Field 2: endereço IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-929">Info Field 2: IP address</span></span>
- <span data-ttu-id="18ca0-930">Info Field 3: Endereço físico (MSW)</span><span class="sxs-lookup"><span data-stu-id="18ca0-930">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="18ca0-931">Info Field 4: Endereço físico (LSW)</span><span class="sxs-lookup"><span data-stu-id="18ca0-931">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-static-entry-create"></a><span data-ttu-id="18ca0-932">Criação de entrada estática ARP</span><span class="sxs-lookup"><span data-stu-id="18ca0-932">ARP Static Entry Create</span></span> 

#### <a name="nx_arp_static_entry_create"></a><span data-ttu-id="18ca0-933">nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="18ca0-933">nx_arp_static_entry_create</span></span>

<span data-ttu-id="18ca0-934">**Ícone** ![ Uma entrada estática R P criar ícone](./media/user-guide/netx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-934">**Icon** ![A R P static entry create icon](./media/user-guide/netx-events/image50.png)</span></span>

<span data-ttu-id="18ca0-935">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-935">**Description**</span></span>

<span data-ttu-id="18ca0-936">Este evento representa a criação de uma entrada estática de ARP através de nx_arp_static_entry_create.</span><span class="sxs-lookup"><span data-stu-id="18ca0-936">This event represents creating a static ARP entry via nx_arp_static_entry_create.</span></span>

<span data-ttu-id="18ca0-937">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-937">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-938">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-938">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-939">Info Field 2: endereço IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-939">Info Field 2: IP address</span></span>
- <span data-ttu-id="18ca0-940">Info Field 3: Endereço físico (MSW)</span><span class="sxs-lookup"><span data-stu-id="18ca0-940">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="18ca0-941">Info Field 4: Endereço físico (LSW)</span><span class="sxs-lookup"><span data-stu-id="18ca0-941">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-static-entries-delete"></a><span data-ttu-id="18ca0-942">As entradas estáticas do ARP eliminam</span><span class="sxs-lookup"><span data-stu-id="18ca0-942">ARP Static Entries Delete</span></span> 

#### <a name="nx_arp_static_entries_delete"></a><span data-ttu-id="18ca0-943">nx_arp_static_entries_delete</span><span class="sxs-lookup"><span data-stu-id="18ca0-943">nx_arp_static_entries_delete</span></span>

<span data-ttu-id="18ca0-944">**Ícone** ![ Um ícone de entradas estáticas R P](./media/user-guide/netx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-944">**Icon** ![A R P static entries delete icon](./media/user-guide/netx-events/image51.png)</span></span>

<span data-ttu-id="18ca0-945">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-945">**Description**</span></span>

<span data-ttu-id="18ca0-946">Este evento representa a eliminação de todas as entradas estáticas ARP através de nx_arp_static_entries_delete.</span><span class="sxs-lookup"><span data-stu-id="18ca0-946">This event represents deleting all ARP static entries via nx_arp_static_entries_delete.</span></span>

<span data-ttu-id="18ca0-947">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-947">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-948">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-948">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-949">Info Field 2: Entradas eliminadas</span><span class="sxs-lookup"><span data-stu-id="18ca0-949">Info Field 2: Entries deleted</span></span>
- <span data-ttu-id="18ca0-950">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-950">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-951">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-951">Info Field 4: Not used</span></span>

### <a name="arp-static-entry-delete"></a><span data-ttu-id="18ca0-952">Exclusão de entrada estática ARP</span><span class="sxs-lookup"><span data-stu-id="18ca0-952">ARP Static Entry Delete</span></span> 

### <a name="nx_arp_static_entry_delete"></a><span data-ttu-id="18ca0-953">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="18ca0-953">nx_arp_static_entry_delete</span></span>

<span data-ttu-id="18ca0-954">**Ícone** ![ Um ícone de exclusão de entrada estática R P](./media/user-guide/netx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-954">**Icon** ![A R P static entry delete icon](./media/user-guide/netx-events/image52.png)</span></span>

<span data-ttu-id="18ca0-955">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-955">**Description**</span></span>

<span data-ttu-id="18ca0-956">Este evento representa a eliminação de uma entrada estática de ARP através de nx_arp_static_entry_delete.</span><span class="sxs-lookup"><span data-stu-id="18ca0-956">This event represents deleting a static ARP entry via nx_arp_static_entry_delete.</span></span>

<span data-ttu-id="18ca0-957">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-957">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-958">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-958">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-959">Info Field 2: endereço IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-959">Info Field 2: IP address</span></span>
- <span data-ttu-id="18ca0-960">Info Field 3: Endereço físico (MSW)</span><span class="sxs-lookup"><span data-stu-id="18ca0-960">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="18ca0-961">Info Field 4: Endereço físico (LSW)</span><span class="sxs-lookup"><span data-stu-id="18ca0-961">Info Field 4: Physical address (LSW)</span></span>

### <a name="duo-cache-entry-delete"></a><span data-ttu-id="18ca0-962">Entrada duo cache Delete</span><span class="sxs-lookup"><span data-stu-id="18ca0-962">Duo Cache Entry Delete</span></span> 

#### <a name="nxd_und_cache_entry_delete"></a><span data-ttu-id="18ca0-963">nxd_und_cache_entry_delete</span><span class="sxs-lookup"><span data-stu-id="18ca0-963">nxd_und_cache_entry_delete</span></span>

<span data-ttu-id="18ca0-964">**Ícone** ![ Ícone de exclusão de entrada de cache duo](./media/user-guide/netx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-964">**Icon** ![Duo cache entry delete icon](./media/user-guide/netx-events/image53.png)</span></span>

<span data-ttu-id="18ca0-965">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-965">**Description**</span></span>

<span data-ttu-id="18ca0-966">Este evento representa a eliminação de uma entrada na mesa de cache do vizinho através de nx_udp_socket_create.</span><span class="sxs-lookup"><span data-stu-id="18ca0-966">This event represents deleting an entry in the neighbor cache table via nx_udp_socket_create.</span></span>

<span data-ttu-id="18ca0-967">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-967">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-968">Info Field 1: Quarta (menos significativa) palavra do endereço local de ligação IPv6 para eliminar</span><span class="sxs-lookup"><span data-stu-id="18ca0-968">Info Field 1: Fourth (least significant) word of the IPv6 link local address to delete</span></span>
- <span data-ttu-id="18ca0-969">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-969">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-970">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-970">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-971">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-971">Info Field 4: Not used</span></span>

### <a name="duo-cache-entry-set"></a><span data-ttu-id="18ca0-972">Conjunto de entrada de cache duo</span><span class="sxs-lookup"><span data-stu-id="18ca0-972">Duo Cache Entry Set</span></span> 

#### <a name="nxd_nd_cache_entry_set"></a><span data-ttu-id="18ca0-973">nxd_nd_cache_entry_set</span><span class="sxs-lookup"><span data-stu-id="18ca0-973">nxd_nd_cache_entry_set</span></span>

<span data-ttu-id="18ca0-974">**Ícone** ![ Ícone de conjunto de conjunto de entrada de cache duo](./media/user-guide/netx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-974">**Icon** ![Duo cache entry set icon](./media/user-guide/netx-events/image54.png)</span></span>

<span data-ttu-id="18ca0-975">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-975">**Description**</span></span>

<span data-ttu-id="18ca0-976">Este evento representa a criação de uma entrada de cache e a adição à mesa de cache do vizinho através de nxd_nd_cache_entry_set.</span><span class="sxs-lookup"><span data-stu-id="18ca0-976">This event represents creating a cache entry and adding to the neighbor cache table via nxd_nd_cache_entry_set.</span></span>

<span data-ttu-id="18ca0-977">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-977">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-978">Info Field 1: Quarta (menos significativa) palavra do endereço IPv6 para adicionar</span><span class="sxs-lookup"><span data-stu-id="18ca0-978">Info Field 1: Fourth (least significant) word of the IPv6 address to add</span></span>
- <span data-ttu-id="18ca0-979">Info Field 2: Endereço físico MSB</span><span class="sxs-lookup"><span data-stu-id="18ca0-979">Info Field 2: Physical address msb</span></span>
- <span data-ttu-id="18ca0-980">Info Field 3: Endereço físico lsb</span><span class="sxs-lookup"><span data-stu-id="18ca0-980">Info Field 3: Physical address lsb</span></span>
- <span data-ttu-id="18ca0-981">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-981">Info Field 4: Not used</span></span>

### <a name="duo-cache-invalidate"></a><span data-ttu-id="18ca0-982">Duo Cache Invalidado</span><span class="sxs-lookup"><span data-stu-id="18ca0-982">Duo Cache Invalidate</span></span> 

#### <a name="nxd_nd_cache_invalidate"></a><span data-ttu-id="18ca0-983">nxd_nd_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="18ca0-983">nxd_nd_cache_invalidate</span></span>

<span data-ttu-id="18ca0-984">**Ícone** ![ Ícone invalidado de cache duo](./media/user-guide/netx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-984">**Icon** ![Duo cache invalidate icon](./media/user-guide/netx-events/image55.png)</span></span>

<span data-ttu-id="18ca0-985">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-985">**Description**</span></span>

<span data-ttu-id="18ca0-986">Este evento representa invalidar toda a mesa de cache do vizinho através de nxd_nd_cache_invalidate.</span><span class="sxs-lookup"><span data-stu-id="18ca0-986">This event represents invalidating the entire neighbor cache table via nxd_nd_cache_invalidate.</span></span>

<span data-ttu-id="18ca0-987">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-987">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-988">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-988">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-989">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-989">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-990">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-990">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-991">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-991">Info Field 4: Not used</span></span>

### <a name="duo-cache-ip-address-find"></a><span data-ttu-id="18ca0-992">Encontrar endereço IP cache duo</span><span class="sxs-lookup"><span data-stu-id="18ca0-992">Duo Cache IP Address Find</span></span> 

#### <a name="nxd_nd_cache_ip_address_find"></a><span data-ttu-id="18ca0-993">nxd_nd_cache_ip_address_find</span><span class="sxs-lookup"><span data-stu-id="18ca0-993">nxd_nd_cache_ip_address_find</span></span>

<span data-ttu-id="18ca0-994">**Ícone** ![ Endereço de cache de duo I P encontrar ícone](./media/user-guide/netx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-994">**Icon** ![Duo cache I P address find icon](./media/user-guide/netx-events/image56.png)</span></span>

<span data-ttu-id="18ca0-995">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-995">**Description**</span></span>

<span data-ttu-id="18ca0-996">Este evento representa a recuperação de um endereço IP correspondente ao endereço físico fornecido da tabela cache através de nxd_nd_cache_ip_address_find.</span><span class="sxs-lookup"><span data-stu-id="18ca0-996">This event represents retrieving an IP address matching the supplied physical address from the cache table via nxd_nd_cache_ip_address_find.</span></span>

<span data-ttu-id="18ca0-997">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-997">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-998">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-998">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-999">Info Field 2: Quarta (menos significativa) palavra do endereço IPv6</span><span class="sxs-lookup"><span data-stu-id="18ca0-999">Info Field 2: Fourth (least significant) word of the IPv6 address</span></span>
- <span data-ttu-id="18ca0-1000">Info Field 3: Endereço físico MSB</span><span class="sxs-lookup"><span data-stu-id="18ca0-1000">Info Field 3: Physical address msb</span></span>
- <span data-ttu-id="18ca0-1001">Info Field 4: Endereço físico lsb</span><span class="sxs-lookup"><span data-stu-id="18ca0-1001">Info Field 4: Physical address lsb</span></span>

### <a name="duo-icmp-enable"></a><span data-ttu-id="18ca0-1002">Ativar duo ICMP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1002">Duo ICMP Enable</span></span> 

#### <a name="nxd_icmp_enable"></a><span data-ttu-id="18ca0-1003">nxd_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="18ca0-1003">nxd_icmp_enable</span></span>

<span data-ttu-id="18ca0-1004">**Ícone** ![ Duo I C M P ativar ícone](./media/user-guide/netx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1004">**Icon** ![Duo I C M P enable icon](./media/user-guide/netx-events/image57.png)</span></span>

<span data-ttu-id="18ca0-1005">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1005">**Description**</span></span>

<span data-ttu-id="18ca0-1006">Este evento representa serviços ICMPv4 e ICMPv6 habilitados na instância IP especificada através de nxd_icmp_enable.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1006">This event represents ICMPv4 and ICMPv6 services being enabled on the specified IP instance via nxd_icmp_enable.</span></span>

<span data-ttu-id="18ca0-1007">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1007">**Information Fields**</span></span>
- <span data-ttu-id="18ca0-1008">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1008">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1009">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1009">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-1010">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1010">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1011">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1011">Info Field 4: Not used</span></span>

### <a name="duo-icmp-ping"></a><span data-ttu-id="18ca0-1012">Duo ICMP Ping</span><span class="sxs-lookup"><span data-stu-id="18ca0-1012">Duo ICMP Ping</span></span> 

#### <a name="nxd_icmp_ping"></a><span data-ttu-id="18ca0-1013">nxd_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="18ca0-1013">nxd_icmp_ping</span></span>

<span data-ttu-id="18ca0-1014">**Ícone** ![ Ícone de ping duo I C M P](./media/user-guide/netx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1014">**Icon** ![Duo I C M P ping icon](./media/user-guide/netx-events/image58.png)</span></span>

<span data-ttu-id="18ca0-1015">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1015">**Description**</span></span>

<span data-ttu-id="18ca0-1016">Este evento representa o envio de um ping (pedido de eco) a um anfitrião IPv6 através de nxd_icmp_ping.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1016">This event represents sending a ping (echo request) to an IPv6 host via nxd_icmp_ping.</span></span>

<span data-ttu-id="18ca0-1017">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1017">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1018">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1018">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1019">Info Field 2: endereço IPv6</span><span class="sxs-lookup"><span data-stu-id="18ca0-1019">Info Field 2: IPv6 address</span></span>
- <span data-ttu-id="18ca0-1020">Info Field 3: Ponteiro para ecoar dados</span><span class="sxs-lookup"><span data-stu-id="18ca0-1020">Info Field 3: Pointer to echo data</span></span>
- <span data-ttu-id="18ca0-1021">Info Field 4: Tamanho dos dados de eco</span><span class="sxs-lookup"><span data-stu-id="18ca0-1021">Info Field 4: Size of echo data</span></span>

### <a name="duo-ip-max-payload-size-find"></a><span data-ttu-id="18ca0-1022">Duo IP Max Payload Size Find</span><span class="sxs-lookup"><span data-stu-id="18ca0-1022">Duo IP Max Payload Size Find</span></span> 

#### <a name="nxd_ip_max_payload_size"></a><span data-ttu-id="18ca0-1023">nxd_ip_max_payload_size</span><span class="sxs-lookup"><span data-stu-id="18ca0-1023">nxd_ip_max_payload_size</span></span>

<span data-ttu-id="18ca0-1024">**Ícone** ![ Duo I P tamanho de carga útil máximo encontrar ícone](./media/user-guide/netx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1024">**Icon** ![Duo I P max payload size find icon](./media/user-guide/netx-events/image59.png)</span></span>

<span data-ttu-id="18ca0-1025">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1025">**Description**</span></span>

<span data-ttu-id="18ca0-1026">Este evento calcula a carga máxima que o pacote especificado pode transportar sem necessitar de fragmentação.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1026">This event computes the max payload the specified packet can carry without requiring fragmentation.</span></span>

<span data-ttu-id="18ca0-1027">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1027">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1028">Info Field 1: Ponteiro de tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1028">Info Field 1: Socket pointer</span></span>
- <span data-ttu-id="18ca0-1029">Info Field 2: Endereço IP do peer</span><span class="sxs-lookup"><span data-stu-id="18ca0-1029">Info Field 2: Peer IP address</span></span>
- <span data-ttu-id="18ca0-1030">Info Field 3: Peer port Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1030">Info Field 3: Peer port Info Field 4: Not used</span></span>

### <a name="duo-ip-raw-packet-send"></a><span data-ttu-id="18ca0-1031">Pacote de pacote cru duo IP enviar</span><span class="sxs-lookup"><span data-stu-id="18ca0-1031">Duo IP Raw Packet Send</span></span> 

#### <a name="nxd_ip_max_packet_send"></a><span data-ttu-id="18ca0-1032">nxd_ip_max_packet_send</span><span class="sxs-lookup"><span data-stu-id="18ca0-1032">nxd_ip_max_packet_send</span></span>

<span data-ttu-id="18ca0-1033">**Ícone** ![ Duo I P pacote cru enviar ícone](./media/user-guide/netx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1033">**Icon** ![Duo I P raw packet send icon](./media/user-guide/netx-events/image60.png)</span></span>

<span data-ttu-id="18ca0-1034">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1034">**Description**</span></span>

<span data-ttu-id="18ca0-1035">Este evento representa o envio de um pacote IP bruto para fora da interface de rede especificada para o endereço de destino IP fornecido nxd_ip_raw_packet_send.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1035">This event represents sending a raw IP packet out the specified network interface to the supplied IP destination addressvia nxd_ip_raw_packet_send.</span></span>

<span data-ttu-id="18ca0-1036">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1036">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1037">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1037">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1038">Info Field 2: Ponteiro para pacote para enviar</span><span class="sxs-lookup"><span data-stu-id="18ca0-1038">Info Field 2: Pointer to packet to send</span></span>
- <span data-ttu-id="18ca0-1039">Info Field 3: Ponteiro para endereço de destino</span><span class="sxs-lookup"><span data-stu-id="18ca0-1039">Info Field 3: Pointer to destination address</span></span>
- <span data-ttu-id="18ca0-1040">Info Field 4: Protocolo de pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-1040">Info Field 4: Packet protocol</span></span>

### <a name="duo-ipv6-default-router-add"></a><span data-ttu-id="18ca0-1041">Adicionar router padrão Duo IPv6</span><span class="sxs-lookup"><span data-stu-id="18ca0-1041">Duo IPv6 Default Router Add</span></span> 

#### <a name="nxd_ipv6_default_router_add"></a><span data-ttu-id="18ca0-1042">nxd_ipv6_default_router_add</span><span class="sxs-lookup"><span data-stu-id="18ca0-1042">nxd_ipv6_default_router_add</span></span>

<span data-ttu-id="18ca0-1043">**Ícone** ![ Duo I P v 6 router padrão adicionar ícone](./media/user-guide/netx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1043">**Icon** ![Duo I P v 6 default router add icon](./media/user-guide/netx-events/image61.png)</span></span>

<span data-ttu-id="18ca0-1044">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1044">**Description**</span></span>

<span data-ttu-id="18ca0-1045">Este evento representa a adição de um router predefinido à tabela de encaminhamento IPv6 da instância IP através de nxd_ipv6_default_router_add.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1045">This event represents adding a default router to the IP instance's IPv6 routing table via nxd_ipv6_default_router_add.</span></span>

<span data-ttu-id="18ca0-1046">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1046">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1047">Info Field 1: Ponteiro para a instância IP.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1047">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="18ca0-1048">Info Field 2: Endereço da Rede de Destino.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1048">Info Field 2: Destination Network address.</span></span>
- <span data-ttu-id="18ca0-1049">Info Field 3: Informação sobre o tempo de vida.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1049">Info Field 3: Life time information.</span></span>
- <span data-ttu-id="18ca0-1050">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1050">Info Field 4: Not used.</span></span>

### <a name="duo-ipv6-default-router-delete"></a><span data-ttu-id="18ca0-1051">Exclusão do router padrão Duo IPv6</span><span class="sxs-lookup"><span data-stu-id="18ca0-1051">Duo IPv6 Default Router Delete</span></span> 

#### <a name="nxd_ipv6_default_router_delete"></a><span data-ttu-id="18ca0-1052">nxd_ipv6_default_router_delete</span><span class="sxs-lookup"><span data-stu-id="18ca0-1052">nxd_ipv6_default_router_delete</span></span>

<span data-ttu-id="18ca0-1053">**Ícone** ![ Ícone de exclusão de router duo I P v 6 padrão](./media/user-guide/netx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1053">**Icon** ![Duo I P v 6 default router delete icon](./media/user-guide/netx-events/image62.png)</span></span>

<span data-ttu-id="18ca0-1054">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1054">**Description**</span></span>

<span data-ttu-id="18ca0-1055">Este evento representa a remoção de um router predefinido da tabela de encaminhamento IPv6 da instância IP através de nxd_ipv6_default_router_delete.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1055">This event represents removing a default router from the IP instance's IPv6 routing table via nxd_ipv6_default_router_delete.</span></span>

<span data-ttu-id="18ca0-1056">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1056">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1057">Info Field 1: Ponteiro para a instância IP.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1057">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="18ca0-1058">Info Field 2: Quarta palavra (menos significativa) do endereço IPv6 do router predefinido.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1058">Info Field 2: Fourth word (least significant) of the default router IPv6 address.</span></span>
- <span data-ttu-id="18ca0-1059">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1059">Info Field 3: Not used.</span></span>
- <span data-ttu-id="18ca0-1060">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1060">Info Field 4: Not used.</span></span>

### <a name="duo-ipv6-enable"></a><span data-ttu-id="18ca0-1061">Duo IPv6 Enable</span><span class="sxs-lookup"><span data-stu-id="18ca0-1061">Duo IPv6 Enable</span></span> 

#### <a name="nxd_ipv6_enable"></a><span data-ttu-id="18ca0-1062">nxd_ipv6_enable</span><span class="sxs-lookup"><span data-stu-id="18ca0-1062">nxd_ipv6_enable</span></span>

<span data-ttu-id="18ca0-1063">**Ícone** ![ Duo I P v 6 ativar ícone](./media/user-guide/netx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1063">**Icon** ![Duo I P v 6 enable icon](./media/user-guide/netx-events/image63.png)</span></span>

<span data-ttu-id="18ca0-1064">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1064">**Description**</span></span>

<span data-ttu-id="18ca0-1065">Este evento representa a capacitação dos serviços IPv6 na instância IP fornecida através de nxd_ipv6_enable.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1065">This event represents enabling IPv6 services on the supplied IP instance via nxd_ipv6_enable.</span></span>

<span data-ttu-id="18ca0-1066">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1066">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1067">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1067">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1068">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1068">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-1069">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1069">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1070">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1070">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-global-address-get"></a><span data-ttu-id="18ca0-1071">Duo IPv6 Global Address Get</span><span class="sxs-lookup"><span data-stu-id="18ca0-1071">Duo IPv6 Global Address Get</span></span> 

#### <a name="nxd_ipv6_global_address_get"></a><span data-ttu-id="18ca0-1072">nxd_ipv6_global_address_get</span><span class="sxs-lookup"><span data-stu-id="18ca0-1072">nxd_ipv6_global_address_get</span></span>

<span data-ttu-id="18ca0-1073">**Ícone** ![ Duo I P v 6 endereço global obter ícone](./media/user-guide/netx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1073">**Icon** ![Duo I P v 6 global address get icon](./media/user-guide/netx-events/image64.png)</span></span>

<span data-ttu-id="18ca0-1074">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1074">**Description**</span></span>

<span data-ttu-id="18ca0-1075">Este evento representa a recuperação do endereço IP global (primário) na instância IP localizada no índice 1 na tabela de interface de instância IP via nxd_ipv6_global_address_get.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1075">This event represents retrieving the global (primary) IP address on the IP instance located at index 1 in the IP instance interface table via nxd_ipv6_global_address_get.</span></span>

<span data-ttu-id="18ca0-1076">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1076">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1077">Info Field 1: Ponteiro para a instância IP.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1077">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="18ca0-1078">Info Field 2: Quarta palavra (menos significativa) do endereço global</span><span class="sxs-lookup"><span data-stu-id="18ca0-1078">Info Field 2: Fourth word (least significant) of the global address</span></span>
- <span data-ttu-id="18ca0-1079">Info Campo 3: Comprimento do prefixo do endereço IPv6.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1079">Info Field 3: IPv6 address prefix length.</span></span>
- <span data-ttu-id="18ca0-1080">Info Field 4: Índice na tabela de interface IP (1).</span><span class="sxs-lookup"><span data-stu-id="18ca0-1080">Info Field 4: Index into IP interface table (1).</span></span>

### <a name="duo-ipv6-global-address-set"></a><span data-ttu-id="18ca0-1081">Conjunto de endereços globais duo IPv6</span><span class="sxs-lookup"><span data-stu-id="18ca0-1081">Duo IPv6 Global Address Set</span></span> 

#### <a name="nxd_ipv6_global_address_set"></a><span data-ttu-id="18ca0-1082">nxd_ipv6_global_address_set</span><span class="sxs-lookup"><span data-stu-id="18ca0-1082">nxd_ipv6_global_address_set</span></span>

<span data-ttu-id="18ca0-1083">**Ícone** ![ Ícone de conjunto de endereços globais Duo I P v 6](./media/user-guide/netx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1083">**Icon** ![Duo I P v 6 global address set icon](./media/user-guide/netx-events/image65.png)</span></span>

<span data-ttu-id="18ca0-1084">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1084">**Description**</span></span>

<span data-ttu-id="18ca0-1085">Este evento representa a definição do endereço IP global (primário) na instância IP localizada no índice 1 na tabela de interface de instância IP via nxd_ipv6_global_address_set.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1085">This event represents setting the global (primary) IP address on the IP instance located at index 1 in the IP instance interface table via nxd_ipv6_global_address_set.</span></span>

<span data-ttu-id="18ca0-1086">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1086">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1087">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1087">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1088">Info Field 2: Quarta palavra (menos significativa) do endereço global</span><span class="sxs-lookup"><span data-stu-id="18ca0-1088">Info Field 2: Fourth word (least significant) of the global address</span></span>
- <span data-ttu-id="18ca0-1089">Info Field 3: Comprimento do prefixo do endereço IPv6</span><span class="sxs-lookup"><span data-stu-id="18ca0-1089">Info Field 3: IPv6 address prefix length</span></span>
- <span data-ttu-id="18ca0-1090">Info Field 4: Índice na tabela de interface IP (1)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1090">Info Field 4: Index into IP interface table (1)</span></span>

### <a name="duo-ipv6-initiate-dad-process"></a><span data-ttu-id="18ca0-1091">Duo IPv6 Iniciar Processo do Pai</span><span class="sxs-lookup"><span data-stu-id="18ca0-1091">Duo IPv6 Initiate Dad Process</span></span> 

#### <a name="nxd_ipv6_initiate_dad_process"></a><span data-ttu-id="18ca0-1092">nxd_ipv6_initiate_dad_process</span><span class="sxs-lookup"><span data-stu-id="18ca0-1092">nxd_ipv6_initiate_dad_process</span></span>

<span data-ttu-id="18ca0-1093">**Ícone** ![ Duo I P v6 iniciar ícone de processo do pai](./media/user-guide/netx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1093">**Icon** ![Duo I P v 6 initiate dad process icon](./media/user-guide/netx-events/image66.png)</span></span>

<span data-ttu-id="18ca0-1094">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1094">**Description**</span></span>

<span data-ttu-id="18ca0-1095">Este evento representa o início do processo de Deteção de Endereços Duplicado (DAD) quando a instância IP é atribuída a um endereço de interface local ou IP através de nxd_ipv6_initiate_dad_process.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1095">This event represents the start of the Duplicate Address Detection (DAD) process when the IP instance is assigned a link local or an IP interface address via nxd_ipv6_initiate_dad_process.</span></span>

<span data-ttu-id="18ca0-1096">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1096">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1097">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1097">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1098">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1098">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-1099">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1099">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1100">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1100">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-interface-address-get"></a><span data-ttu-id="18ca0-1101">Endereço de interface Duo IPv6 Obter</span><span class="sxs-lookup"><span data-stu-id="18ca0-1101">Duo IPv6 Interface Address Get</span></span> 

#### <a name="nxd_ipv6_interface_address_get"></a><span data-ttu-id="18ca0-1102">nxd_ipv6_interface_address_get</span><span class="sxs-lookup"><span data-stu-id="18ca0-1102">nxd_ipv6_interface_address_get</span></span>

<span data-ttu-id="18ca0-1103">**Ícone** ![ Duo I P v 6 interface endereço obter ícone](./media/user-guide/netx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1103">**Icon** ![Duo I P v 6 interface address get icon](./media/user-guide/netx-events/image67.png)</span></span>

<span data-ttu-id="18ca0-1104">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1104">**Description**</span></span>

<span data-ttu-id="18ca0-1105">Este evento representa a recuperação do endereço IP e prefixo no índice especificado na tabela de endereços de interface de instância IP através de nxd_ipv6_interface_address_get.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1105">This event represents retrieving the IP address and prefix at the specified index into the IP instance interface address table via nxd_ipv6_interface_address_get.</span></span>

<span data-ttu-id="18ca0-1106">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1106">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1107">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1107">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1108">Info Field 2: Quarta palavra (menos significativa) do endereço IPv6 para devolver</span><span class="sxs-lookup"><span data-stu-id="18ca0-1108">Info Field 2: Fourth word (least significant) of the IPv6 address to return</span></span>
- <span data-ttu-id="18ca0-1109">Info Field 4: Índice de interface na tabela de interface de instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1109">Info Field 4: Index of interface into the IP instance interface table</span></span>

### <a name="duo-ipv6-interface-address-set"></a><span data-ttu-id="18ca0-1110">Conjunto de endereços de interface duo IPv6</span><span class="sxs-lookup"><span data-stu-id="18ca0-1110">Duo IPv6 Interface Address Set</span></span> 

### <a name="nxd_ipv6_interface_address_set"></a><span data-ttu-id="18ca0-1111">nxd_ipv6_interface_address_set</span><span class="sxs-lookup"><span data-stu-id="18ca0-1111">nxd_ipv6_interface_address_set</span></span>

<span data-ttu-id="18ca0-1112">**Ícone** ![ Duo I P v 6 endereços de interface et ícone](./media/user-guide/netx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1112">**Icon** ![Duo I P v 6 interface addresss et icon](./media/user-guide/netx-events/image68.png)</span></span>

<span data-ttu-id="18ca0-1113">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1113">**Description**</span></span>

<span data-ttu-id="18ca0-1114">Este evento representa a definição do endereço IP e prefixo no índice especificado na tabela de endereços de interface de instância IP.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1114">This event represents setting the IP address and prefix at the specified index into the IP instance interface address table.</span></span> <span data-ttu-id="18ca0-1115">Não é permitido no índice zero (link endereço local) via nxd_ipv6_interface_address_set.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1115">Not permitted on index zero (link local address) via nxd_ipv6_interface_address_set.</span></span>

<span data-ttu-id="18ca0-1116">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1116">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1117">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1117">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1118">Info Field 2: Quarta palavra (menos significativa) do endereço IPv6 para devolver</span><span class="sxs-lookup"><span data-stu-id="18ca0-1118">Info Field 2: Fourth word (least significant) of the IPv6 address to return</span></span>
- <span data-ttu-id="18ca0-1119">Info Field 3: Comprimento do prefixo</span><span class="sxs-lookup"><span data-stu-id="18ca0-1119">Info Field 3: Prefix length</span></span>
- <span data-ttu-id="18ca0-1120">Info Field 4: Índice de interface na tabela de interface de instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1120">Info Field 4: Index of interface into the IP instance interface table</span></span>

### <a name="duo-ipv6-link-local-address-get"></a><span data-ttu-id="18ca0-1121">Duo IPv6 Link Endereço Local Obter</span><span class="sxs-lookup"><span data-stu-id="18ca0-1121">Duo IPv6 Link Local Address Get</span></span> 

#### <a name="nxd_ipv6_linklocal_address_get"></a><span data-ttu-id="18ca0-1122">nxd_ipv6_linklocal_address_get</span><span class="sxs-lookup"><span data-stu-id="18ca0-1122">nxd_ipv6_linklocal_address_get</span></span>

<span data-ttu-id="18ca0-1123">**Ícone** ![ Duo I P v 6 link endereço local obter ícone](./media/user-guide/netx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1123">**Icon** ![Duo I P v 6 link local address get icon](./media/user-guide/netx-events/image69.png)</span></span>

<span data-ttu-id="18ca0-1124">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1124">**Description**</span></span>

<span data-ttu-id="18ca0-1125">Este evento representa a recuperação do endereço local de ligação da instância IP especificada através de nxd_ipv6_linklocal_address_get.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1125">This event represents retrieving the link local address of the specified IP instance via nxd_ipv6_linklocal_address_get.</span></span>

<span data-ttu-id="18ca0-1126">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1126">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1127">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1127">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1128">Info Field 2: Quarta palavra (menos significativa) do endereço local de ligação IP v6</span><span class="sxs-lookup"><span data-stu-id="18ca0-1128">Info Field 2: Fourth word (least significant) of the IP v6 link local address</span></span>
- <span data-ttu-id="18ca0-1129">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1129">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1130">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1130">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-link-local-address-set"></a><span data-ttu-id="18ca0-1131">Conjunto de endereços locais duo IPv6 Link</span><span class="sxs-lookup"><span data-stu-id="18ca0-1131">Duo IPv6 Link Local Address Set</span></span> 

#### <a name="nxd_ipv6_linklocal_address_set"></a><span data-ttu-id="18ca0-1132">nxd_ipv6_linklocal_address_set</span><span class="sxs-lookup"><span data-stu-id="18ca0-1132">nxd_ipv6_linklocal_address_set</span></span>

<span data-ttu-id="18ca0-1133">**Ícone** ![ Duo I P v 6 link ícone de conjunto de endereço local](./media/user-guide/netx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1133">**Icon** ![Duo I P v 6 link local address set icon](./media/user-guide/netx-events/image70.png)</span></span>

<span data-ttu-id="18ca0-1134">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1134">**Description**</span></span>

<span data-ttu-id="18ca0-1135">Este evento representa a definição do endereço local de ligação da instância IP através de nxd_ipv6_linklocal_address_set.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1135">This event represents setting the link local address of the IP instance via nxd_ipv6_linklocal_address_set.</span></span>

<span data-ttu-id="18ca0-1136">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1136">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1137">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1137">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1138">Info Field 2: Quarta (menos significativa) palavra do endereço local de ligação IPv6</span><span class="sxs-lookup"><span data-stu-id="18ca0-1138">Info Field 2: Fourth (least significant) word of the IPv6 link local address</span></span>
- <span data-ttu-id="18ca0-1139">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1139">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1140">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1140">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-raw-packet-send"></a><span data-ttu-id="18ca0-1141">Duo IPv6 Raw Packet Enviar</span><span class="sxs-lookup"><span data-stu-id="18ca0-1141">Duo IPv6 Raw Packet Send</span></span> 

#### <a name="nxd_ipv6_raw_packet_send"></a><span data-ttu-id="18ca0-1142">nxd_ipv6_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="18ca0-1142">nxd_ipv6_raw_packet_send</span></span>

<span data-ttu-id="18ca0-1143">**Ícone** ![ Duo I P v6 pacote cru enviar ícone](./media/user-guide/netx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1143">**Icon** ![Duo I P v 6 raw packet send icon](./media/user-guide/netx-events/image71.png)</span></span>

<span data-ttu-id="18ca0-1144">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1144">**Description**</span></span>

<span data-ttu-id="18ca0-1145">Este evento representa o envio de um pacote IP cru através da interface IP primária para o destino speficied via nxd_ip_raw_packet_send.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1145">This event represents sending a raw IP packet through the primary IP interface to the speficied destination via nxd_ip_raw_packet_send.</span></span>

<span data-ttu-id="18ca0-1146">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1146">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1147">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1147">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1148">Info Field 2: Ponteiro para pacote para enviar</span><span class="sxs-lookup"><span data-stu-id="18ca0-1148">Info Field 2: Pointer to packet to send</span></span>
- <span data-ttu-id="18ca0-1149">Info Field 3: Endereço IP de destino</span><span class="sxs-lookup"><span data-stu-id="18ca0-1149">Info Field 3: Destination IP address</span></span>
- <span data-ttu-id="18ca0-1150">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1150">Info Field 4: Not used</span></span>

### <a name="duo-tcp-socket-peer-info-get"></a><span data-ttu-id="18ca0-1151">Duo TCP Socket Peer Info Get</span><span class="sxs-lookup"><span data-stu-id="18ca0-1151">Duo TCP Socket Peer Info Get</span></span> 

#### <a name="nxd_tcp_socket_peer_info_get"></a><span data-ttu-id="18ca0-1152">nxd_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="18ca0-1152">nxd_tcp_socket_peer_info_get</span></span>

<span data-ttu-id="18ca0-1153">**Ícone** ![ Duo T C P tomada informação peer obter ícone](./media/user-guide/netx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1153">**Icon** ![Duo T C P socket peer info get icon](./media/user-guide/netx-events/image72.png)</span></span>

<span data-ttu-id="18ca0-1154">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1154">**Description**</span></span>

<span data-ttu-id="18ca0-1155">Este evento extrai os dados do remetente de um pacote TCP recebido na tomada especificada.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1155">This event extracts the sender data from a received TCP packet on the specified socket.</span></span> <span data-ttu-id="18ca0-1156">Devolve o endereço IP e a porta do remetente.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1156">It returns the IP address and port of the sender.</span></span>

<span data-ttu-id="18ca0-1157">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1157">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1158">Info Field 1: Ponteiro de tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1158">Info Field 1: Socket pointer</span></span>
- <span data-ttu-id="18ca0-1159">Info Field 2: Endereço IP do peer</span><span class="sxs-lookup"><span data-stu-id="18ca0-1159">Info Field 2: Peer IP address</span></span>
- <span data-ttu-id="18ca0-1160">Info Field 3: Porta peer</span><span class="sxs-lookup"><span data-stu-id="18ca0-1160">Info Field 3: Peer port</span></span>
- <span data-ttu-id="18ca0-1161">Info Field 4: O arrendamento significativo 32 bits do endereço IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1161">Info Field 4: The lease significant 32-bit of the IP address</span></span>

### <a name="duo-tcp-socket-set-interface"></a><span data-ttu-id="18ca0-1162">Interface de conjunto de tomada de TCP duo</span><span class="sxs-lookup"><span data-stu-id="18ca0-1162">Duo TCP Socket Set Interface</span></span> 

#### <a name="nxd_tcp_socket_set_interface"></a><span data-ttu-id="18ca0-1163">nxd_tcp_socket_set_interface</span><span class="sxs-lookup"><span data-stu-id="18ca0-1163">nxd_tcp_socket_set_interface</span></span>

<span data-ttu-id="18ca0-1164">**Ícone** ![ Ícone de interface de conjunto de tomada duo T C P](./media/user-guide/netx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1164">**Icon** ![Duo T C P socket set interface icon](./media/user-guide/netx-events/image73.png)</span></span>

<span data-ttu-id="18ca0-1165">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1165">**Description**</span></span>

<span data-ttu-id="18ca0-1166">Este evento representa a definição da interface da tomada de saída depois de um cliente ligar-se a um servidor TCP no endereço IP do servidor especificado através de nxd_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1166">This event represents setting the outgoing socket interface after a client connects with a TCP server on the specified server IP address via nxd_tcp_client_socket_connect.</span></span>

<span data-ttu-id="18ca0-1167">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1167">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1168">Info Field 1: Ponteiro para tomada TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1168">Info Field 1: Pointer to TCP Socket</span></span>
- <span data-ttu-id="18ca0-1169">Info Field 2: Interface ID</span><span class="sxs-lookup"><span data-stu-id="18ca0-1169">Info Field 2: Interface ID</span></span>
- <span data-ttu-id="18ca0-1170">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1170">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1171">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1171">Info Field 4: Not used</span></span>

### <a name="duo-udp-socket-send"></a><span data-ttu-id="18ca0-1172">Dupla UDP Socket Enviar</span><span class="sxs-lookup"><span data-stu-id="18ca0-1172">Duo UDP Socket Send</span></span> 

#### <a name="nxd_udp_socket_send"></a><span data-ttu-id="18ca0-1173">nxd_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="18ca0-1173">nxd_udp_socket_send</span></span>

<span data-ttu-id="18ca0-1174">**Ícone** ![ Tomada duo U D P enviar ícone](./media/user-guide/netx-events/image74.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1174">**Icon** ![Duo U D P socket send icon](./media/user-guide/netx-events/image74.png)</span></span>

<span data-ttu-id="18ca0-1175">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1175">**Description**</span></span>

<span data-ttu-id="18ca0-1176">Este evento representa o envio de um pacote UDP através da tomada especificada com o endereço IP de entrada e porta via nxd_udp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1176">This event represents sending a UDP packet through the specified socket with the input IP address and port via nxd_udp_socket_send.</span></span>

<span data-ttu-id="18ca0-1177">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1177">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1178">Info Field 1: Ponteiro UDP Socket</span><span class="sxs-lookup"><span data-stu-id="18ca0-1178">Info Field 1: Pointer UDP Socket</span></span>
- <span data-ttu-id="18ca0-1179">Info Field 2: Ponteiro para pacote UDP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1179">Info Field 2: Pointer to UDP packet</span></span>
- <span data-ttu-id="18ca0-1180">Info Field 3: Comprimento do pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-1180">Info Field 3: Packet length</span></span>
- <span data-ttu-id="18ca0-1181">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1181">Info Field 4: Not used</span></span>


### <a name="duo-udp-socket-set-interface"></a><span data-ttu-id="18ca0-1182">Interface de conjunto de tomada udp duo</span><span class="sxs-lookup"><span data-stu-id="18ca0-1182">Duo UDP Socket Set Interface</span></span> 

#### <a name="nxd_udp_socket_set_interface"></a><span data-ttu-id="18ca0-1183">nxd_udp_socket_set_interface</span><span class="sxs-lookup"><span data-stu-id="18ca0-1183">nxd_udp_socket_set_interface</span></span>

<span data-ttu-id="18ca0-1184">**Ícone** ![ Ícone de interface de conjunto de tomada duo U D P](./media/user-guide/netx-events/image75.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1184">**Icon** ![Duo U D P socket set interface icon](./media/user-guide/netx-events/image75.png)</span></span>

<span data-ttu-id="18ca0-1185">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1185">**Description**</span></span>

<span data-ttu-id="18ca0-1186">Este evento representa a definição da interface de saída da tomada UDP especificada para a interface correspondente ao ID da interface de entrada através de nxd_udp_socket_set_interface.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1186">This event represents setting the specified UDP socket outgoing interface to the interface corresponding to the input interface ID via nxd_udp_socket_set_interface.</span></span>

<span data-ttu-id="18ca0-1187">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1187">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1188">Info Field 1: Ponteiro para tomada UDP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1188">Info Field 1: Pointer to UDP Socket</span></span>
- <span data-ttu-id="18ca0-1189">Info Field 2: Interface ID</span><span class="sxs-lookup"><span data-stu-id="18ca0-1189">Info Field 2: Interface ID</span></span>
- <span data-ttu-id="18ca0-1190">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1190">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1191">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1191">Info Field 4: Not used</span></span>

### <a name="duo-udp-source-extract"></a><span data-ttu-id="18ca0-1192">Extrato de fonte duo UDP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1192">Duo UDP Source Extract</span></span> 

#### <a name="nxd_udp_socket_extract"></a><span data-ttu-id="18ca0-1193">nxd_udp_socket_extract</span><span class="sxs-lookup"><span data-stu-id="18ca0-1193">nxd_udp_socket_extract</span></span>

<span data-ttu-id="18ca0-1194">**Ícone** ![ Ícone de extrato de fonte duo U D P](./media/user-guide/netx-events/image76.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1194">**Icon** ![Duo U D P source extract icon](./media/user-guide/netx-events/image76.png)</span></span>

<span data-ttu-id="18ca0-1195">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1195">**Description**</span></span>

<span data-ttu-id="18ca0-1196">Este evento representa a extração do endereço IP e da porta de origem de um pacote recebido (ou IPv4 ou IPv6).</span><span class="sxs-lookup"><span data-stu-id="18ca0-1196">This event represents extracting the IP address and source port of a received packet (either IPv4 or IPv6).</span></span> <span data-ttu-id="18ca0-1197">Se o IPv6, a quarta palavra (menos significativa) do endereço IP for devolvida através de nxd_udp_source_extract.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1197">If IPv6, the fourth word (least significant) of the IP address is returned via nxd_udp_source_extract.</span></span>

<span data-ttu-id="18ca0-1198">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1198">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1199">Info Field 1: Ponteiro para o pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-1199">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="18ca0-1200">Info Field 2: versão IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1200">Info Field 2: IP version</span></span>
- <span data-ttu-id="18ca0-1201">Info Field 3: Endereço IP de origem (IPv4 ou IPv6)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1201">Info Field 3: Source IP address (IPv4 or IPv6)</span></span>
- <span data-ttu-id="18ca0-1202">Info Field 4: Porta de origem</span><span class="sxs-lookup"><span data-stu-id="18ca0-1202">Info Field 4: Source port</span></span>

### <a name="icmp-enable"></a><span data-ttu-id="18ca0-1203">ICMP Ativar</span><span class="sxs-lookup"><span data-stu-id="18ca0-1203">ICMP Enable</span></span> 

#### <a name="nx_icmp_enable"></a><span data-ttu-id="18ca0-1204">nx_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="18ca0-1204">nx_icmp_enable</span></span>

<span data-ttu-id="18ca0-1205">**Ícone** ![ I C M P ativar ícone](./media/user-guide/netx-events/image77.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1205">**Icon** ![I C M P enable icon](./media/user-guide/netx-events/image77.png)</span></span>

<span data-ttu-id="18ca0-1206">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1206">**Description**</span></span>

<span data-ttu-id="18ca0-1207">Este evento representa permitir o ICMP através de nx_icmp_enable.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1207">This event represents enabling ICMP via nx_icmp_enable.</span></span>

<span data-ttu-id="18ca0-1208">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1208">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1209">Info Field 1: Ponteiro para a instância IP l;</span><span class="sxs-lookup"><span data-stu-id="18ca0-1209">Info Field 1: Pointer to the IP instance l;</span></span>
- <span data-ttu-id="18ca0-1210">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1210">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-1211">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1211">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1212">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1212">Info Field 4: Not used</span></span>

### <a name="icmp-information-get"></a><span data-ttu-id="18ca0-1213">Informação do ICMP Obtém</span><span class="sxs-lookup"><span data-stu-id="18ca0-1213">ICMP Information Get</span></span> 

#### <a name="nx_icmp_info_get"></a><span data-ttu-id="18ca0-1214">nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="18ca0-1214">nx_icmp_info_get</span></span>

<span data-ttu-id="18ca0-1215">**Ícone** ![ I C M P informações obter ícone](./media/user-guide/netx-events/image78.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1215">**Icon** ![I C M P information get icon](./media/user-guide/netx-events/image78.png)</span></span>

<span data-ttu-id="18ca0-1216">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1216">**Description**</span></span>

<span data-ttu-id="18ca0-1217">Este evento representa a obtenção de informação através de nx_icmp_info_get.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1217">This event represents getting information via nx_icmp_info_get.</span></span>

<span data-ttu-id="18ca0-1218">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1218">**Information Fields**</span></span>
- <span data-ttu-id="18ca0-1219">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1219">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1220">Info Field 2: Pings enviados</span><span class="sxs-lookup"><span data-stu-id="18ca0-1220">Info Field 2: Pings sent</span></span>
- <span data-ttu-id="18ca0-1221">Info Field 3: Respostas de ping</span><span class="sxs-lookup"><span data-stu-id="18ca0-1221">Info Field 3: Ping responses</span></span>
- <span data-ttu-id="18ca0-1222">Info Field 4: Pings recebidos</span><span class="sxs-lookup"><span data-stu-id="18ca0-1222">Info Field 4: Pings received</span></span>

### <a name="icmp-ping"></a><span data-ttu-id="18ca0-1223">ICMP Ping</span><span class="sxs-lookup"><span data-stu-id="18ca0-1223">ICMP Ping</span></span> 

#### <a name="nx_icmp_ping"></a><span data-ttu-id="18ca0-1224">nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="18ca0-1224">nx_icmp_ping</span></span>

<span data-ttu-id="18ca0-1225">**Ícone** ![ I C M P ping ícone](./media/user-guide/netx-events/image79.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1225">**Icon** ![I C M P ping icon](./media/user-guide/netx-events/image79.png)</span></span>

<span data-ttu-id="18ca0-1226">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1226">**Description**</span></span>

<span data-ttu-id="18ca0-1227">Este evento representa a identificação de um endereço IP alvo através de nx_icmp_ping.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1227">This event represents pinging a target IP address via nx_icmp_ping.</span></span>

<span data-ttu-id="18ca0-1228">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1228">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1229">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1229">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1230">Info Field 2: endereço IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1230">Info Field 2: IP address</span></span>
- <span data-ttu-id="18ca0-1231">Info Field 3: Ponteiro para dados</span><span class="sxs-lookup"><span data-stu-id="18ca0-1231">Info Field 3: Pointer to data</span></span>
- <span data-ttu-id="18ca0-1232">Info Field 4: Tamanho dos dados</span><span class="sxs-lookup"><span data-stu-id="18ca0-1232">Info Field 4: Size of data</span></span>

### <a name="igmp-enable"></a><span data-ttu-id="18ca0-1233">IGMP Ativar</span><span class="sxs-lookup"><span data-stu-id="18ca0-1233">IGMP Enable</span></span> 

#### <a name="nx_icmp_enable"></a><span data-ttu-id="18ca0-1234">nx_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="18ca0-1234">nx_icmp_enable</span></span>

<span data-ttu-id="18ca0-1235">**Ícone** ![ I G M P ativar ícone](./media/user-guide/netx-events/image80.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1235">**Icon** ![I G M P enable icon](./media/user-guide/netx-events/image80.png)</span></span>

<span data-ttu-id="18ca0-1236">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1236">**Description**</span></span>

<span data-ttu-id="18ca0-1237">Este evento representa permitir o IGMP através de nx_igmp_enable.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1237">This event represents enabling IGMP via nx_igmp_enable.</span></span>

<span data-ttu-id="18ca0-1238">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1238">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1239">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1239">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1240">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1240">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-1241">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1241">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1242">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1242">Info Field 4: Not used</span></span>

### <a name="igmp-information-get"></a><span data-ttu-id="18ca0-1243">Informação IGMP Obter</span><span class="sxs-lookup"><span data-stu-id="18ca0-1243">IGMP Information Get</span></span> 

#### <a name="nx_icmp_info_get"></a><span data-ttu-id="18ca0-1244">nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="18ca0-1244">nx_icmp_info_get</span></span>

<span data-ttu-id="18ca0-1245">**Ícone** ![ I G M P informações obter ícone](./media/user-guide/netx-events/image81.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1245">**Icon** ![I G M P information get icon](./media/user-guide/netx-events/image81.png)</span></span>

<span data-ttu-id="18ca0-1246">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1246">**Description**</span></span>

<span data-ttu-id="18ca0-1247">Este evento representa a obtenção de informação através de nx_igmp_info_get.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1247">This event represents getting information via nx_igmp_info_get.</span></span>

<span data-ttu-id="18ca0-1248">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1248">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1249">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1249">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1250">Info Field 2: Relatórios enviados</span><span class="sxs-lookup"><span data-stu-id="18ca0-1250">Info Field 2: Reports sent</span></span>
- <span data-ttu-id="18ca0-1251">Info Field 3: Consultas recebidas</span><span class="sxs-lookup"><span data-stu-id="18ca0-1251">Info Field 3: Queries received</span></span>
- <span data-ttu-id="18ca0-1252">Info Field 4: Grupos unidos</span><span class="sxs-lookup"><span data-stu-id="18ca0-1252">Info Field 4: Groups joined</span></span>

### <a name="igmp-loopback-disable"></a><span data-ttu-id="18ca0-1253">Desativação do loopback IGMP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1253">IGMP Loopback Disable</span></span> 

#### <a name="nx_igmp_loopback_disable"></a><span data-ttu-id="18ca0-1254">nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="18ca0-1254">nx_igmp_loopback_disable</span></span>

<span data-ttu-id="18ca0-1255">**Ícone** ![ I G M P loopback ícone desativar](./media/user-guide/netx-events/image82.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1255">**Icon** ![I G M P loopback disable icon](./media/user-guide/netx-events/image82.png)</span></span>

<span data-ttu-id="18ca0-1256">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1256">**Description**</span></span>

<span data-ttu-id="18ca0-1257">Este evento representa desativar o loopback IGMP através de nx_igmp_loopback_disable.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1257">This event represents disabling IGMP loopback via nx_igmp_loopback_disable.</span></span>

<span data-ttu-id="18ca0-1258">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1258">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1259">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1259">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1260">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1260">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-1261">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1261">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1262">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1262">Info Field 4: Not used</span></span>

### <a name="igmp-loopback-enable"></a><span data-ttu-id="18ca0-1263">IGMP Loopback Ativa</span><span class="sxs-lookup"><span data-stu-id="18ca0-1263">IGMP Loopback Enable</span></span> 

#### <a name="nx_igmp_loopback_enable"></a><span data-ttu-id="18ca0-1264">nx_igmp_loopback_enable</span><span class="sxs-lookup"><span data-stu-id="18ca0-1264">nx_igmp_loopback_enable</span></span>

<span data-ttu-id="18ca0-1265">**Ícone** ![ I G M P loopback ativar ícone](./media/user-guide/netx-events/image83.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1265">**Icon** ![I G M P loopback enable icon](./media/user-guide/netx-events/image83.png)</span></span>

<span data-ttu-id="18ca0-1266">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1266">**Description**</span></span>

<span data-ttu-id="18ca0-1267">Este evento representa permitir o loopback IGMP através de nx_igmp_loopback_enable.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1267">This event represents enabling IGMP loopback via nx_igmp_loopback_enable.</span></span>

<span data-ttu-id="18ca0-1268">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1268">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1269">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1269">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1270">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1270">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-1271">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1271">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1272">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1272">Info Field 4: Not used</span></span>

### <a name="igmp-multicast-join"></a><span data-ttu-id="18ca0-1273">IGMP Multicast Join</span><span class="sxs-lookup"><span data-stu-id="18ca0-1273">IGMP Multicast Join</span></span> 

#### <a name="nx_igmp_multicast_join"></a><span data-ttu-id="18ca0-1274">nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="18ca0-1274">nx_igmp_multicast_join</span></span>

<span data-ttu-id="18ca0-1275">**Ícone** ![ I G M P multicast juntar ícone](./media/user-guide/netx-events/image84.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1275">**Icon** ![I G M P multicast join icon](./media/user-guide/netx-events/image84.png)</span></span>

<span data-ttu-id="18ca0-1276">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1276">**Description**</span></span>

<span data-ttu-id="18ca0-1277">Este evento representa a adesão a um grupo multicast através de nx_igmp_multicast_join.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1277">This event represents joining a multicast group via nx_igmp_multicast_join.</span></span>

<span data-ttu-id="18ca0-1278">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1278">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1279">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1279">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1280">Info Field 2: Endereço IP do grupo</span><span class="sxs-lookup"><span data-stu-id="18ca0-1280">Info Field 2: Group IP address</span></span>
- <span data-ttu-id="18ca0-1281">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1281">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1282">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1282">Info Field 4: Not used</span></span>

### <a name="igmp-multicast-leave"></a><span data-ttu-id="18ca0-1283">Licença Multicast IGMP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1283">IGMP Multicast Leave</span></span> 

#### <a name="nx_igmp_multicast_leave"></a><span data-ttu-id="18ca0-1284">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="18ca0-1284">nx_igmp_multicast_leave</span></span>

<span data-ttu-id="18ca0-1285">**Ícone** ![ I G M P multicast deixar ícone](./media/user-guide/netx-events/image85.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1285">**Icon** ![I G M P multicast leave icon](./media/user-guide/netx-events/image85.png)</span></span>

<span data-ttu-id="18ca0-1286">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1286">**Description**</span></span>

<span data-ttu-id="18ca0-1287">Este evento representa a saída de um grupo multicast via nx_igmp_multicast_leave.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1287">This event represents leaving a multicast group via nx_igmp_multicast_leave.</span></span>

<span data-ttu-id="18ca0-1288">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1288">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1289">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1289">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1290">Info Field 2: Endereço IP do grupo</span><span class="sxs-lookup"><span data-stu-id="18ca0-1290">Info Field 2: Group IP address</span></span>
- <span data-ttu-id="18ca0-1291">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1291">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1292">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1292">Info Field 4: Not used</span></span>

### <a name="ip-address-change-notify"></a><span data-ttu-id="18ca0-1293">Notificação de alteração de endereço IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1293">IP Address Change Notify</span></span> 

#### <a name="nx_ip_address_change_notify"></a><span data-ttu-id="18ca0-1294">nx_ip_address_change_notify</span><span class="sxs-lookup"><span data-stu-id="18ca0-1294">nx_ip_address_change_notify</span></span>

<span data-ttu-id="18ca0-1295">**Ícone** ![ I P endereço alterar ícone de notificação](./media/user-guide/netx-events/image86.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1295">**Icon** ![I P address change notify icon](./media/user-guide/netx-events/image86.png)</span></span>

<span data-ttu-id="18ca0-1296">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1296">**Description**</span></span>

<span data-ttu-id="18ca0-1297">Este evento representa o registo para notificação de alteração IP através de nx_ip_address_change_notify.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1297">This event represents registering for IP change notification via nx_ip_address_change_notify.</span></span>

<span data-ttu-id="18ca0-1298">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1298">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1299">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1299">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1300">Info Field 2: Ponteiro de função callback</span><span class="sxs-lookup"><span data-stu-id="18ca0-1300">Info Field 2: Callback function pointer</span></span>
- <span data-ttu-id="18ca0-1301">Info Field 3: Ponteiro informativo adicional</span><span class="sxs-lookup"><span data-stu-id="18ca0-1301">Info Field 3: Additional information pointer</span></span>
- <span data-ttu-id="18ca0-1302">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1302">Info Field 4: Not used</span></span>

### <a name="ip-address-get"></a><span data-ttu-id="18ca0-1303">Endereço IP Obter</span><span class="sxs-lookup"><span data-stu-id="18ca0-1303">IP Address Get</span></span> 

#### <a name="nx_ip_address_get"></a><span data-ttu-id="18ca0-1304">nx_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="18ca0-1304">nx_ip_address_get</span></span>

<span data-ttu-id="18ca0-1305">**Ícone** ![ Endereço I P obter ícone](./media/user-guide/netx-events/image87.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1305">**Icon** ![I P address get icon](./media/user-guide/netx-events/image87.png)</span></span>

<span data-ttu-id="18ca0-1306">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1306">**Description**</span></span>

<span data-ttu-id="18ca0-1307">Este evento representa obter o endereço IP através de nx_ip_address_get.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1307">This event represents getting the IP address via nx_ip_address_get.</span></span>

<span data-ttu-id="18ca0-1308">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1308">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1309">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1309">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1310">Info Field 2: endereço IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1310">Info Field 2: IP address</span></span>
- <span data-ttu-id="18ca0-1311">Info Field 3: Máscara de rede</span><span class="sxs-lookup"><span data-stu-id="18ca0-1311">Info Field 3: Network mask</span></span>
- <span data-ttu-id="18ca0-1312">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1312">Info Field 4: Not used</span></span>

### <a name="ip-address-set"></a><span data-ttu-id="18ca0-1313">Conjunto de endereços IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1313">IP Address Set</span></span> 

#### <a name="nx_ip_address_set"></a><span data-ttu-id="18ca0-1314">nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="18ca0-1314">nx_ip_address_set</span></span>

<span data-ttu-id="18ca0-1315">**Ícone** ![ Ícone de conjunto de endereço I P](./media/user-guide/netx-events/image88.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1315">**Icon** ![I P address set icon](./media/user-guide/netx-events/image88.png)</span></span>

<span data-ttu-id="18ca0-1316">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1316">**Description**</span></span>

<span data-ttu-id="18ca0-1317">Este evento representa a definição do endereço IP através de nx_ip_address_set.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1317">This event represents setting the IP address via nx_ip_address_set.</span></span>

<span data-ttu-id="18ca0-1318">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1318">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1319">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1319">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1320">Info Field 2: endereço IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1320">Info Field 2: IP address</span></span>
- <span data-ttu-id="18ca0-1321">Info Field 3: Máscara de rede</span><span class="sxs-lookup"><span data-stu-id="18ca0-1321">Info Field 3: Network mask</span></span>
- <span data-ttu-id="18ca0-1322">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1322">Info Field 4: Not used</span></span>

### <a name="ip-create"></a><span data-ttu-id="18ca0-1323">Criação IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1323">IP Create</span></span> 

#### <a name="nx_ip_create"></a><span data-ttu-id="18ca0-1324">nx_ip_create</span><span class="sxs-lookup"><span data-stu-id="18ca0-1324">nx_ip_create</span></span>

<span data-ttu-id="18ca0-1325">**Ícone** ![ I P criar ícone](./media/user-guide/netx-events/image89.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1325">**Icon** ![I P create icon](./media/user-guide/netx-events/image89.png)</span></span>

<span data-ttu-id="18ca0-1326">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1326">**Description**</span></span>

<span data-ttu-id="18ca0-1327">Este evento representa a criação de uma instância IP através de nx_ip_create.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1327">This event represents creating an IP instance via nx_ip_create.</span></span>

<span data-ttu-id="18ca0-1328">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1328">**Information Fields**</span></span> 
- <span data-ttu-id="18ca0-1329">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1329">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1330">Info Field 2: endereço IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1330">Info Field 2: IP address</span></span>
- <span data-ttu-id="18ca0-1331">Info Field 3: Máscara de rede</span><span class="sxs-lookup"><span data-stu-id="18ca0-1331">Info Field 3: Network mask</span></span>
- <span data-ttu-id="18ca0-1332">Info Field 4: Ponteiro de piscina de pacote padrão</span><span class="sxs-lookup"><span data-stu-id="18ca0-1332">Info Field 4: Default packet pool pointer</span></span>

### <a name="ip-delete"></a><span data-ttu-id="18ca0-1333">IP Delete</span><span class="sxs-lookup"><span data-stu-id="18ca0-1333">IP Delete</span></span> 

#### <a name="nx_ip_delete"></a><span data-ttu-id="18ca0-1334">nx_ip_delete</span><span class="sxs-lookup"><span data-stu-id="18ca0-1334">nx_ip_delete</span></span>

<span data-ttu-id="18ca0-1335">**Ícone** ![ I P apagar ícone](./media/user-guide/netx-events/image90.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1335">**Icon** ![I P delete icon](./media/user-guide/netx-events/image90.png)</span></span>

<span data-ttu-id="18ca0-1336">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1336">**Description**</span></span>

<span data-ttu-id="18ca0-1337">Este evento representa a eliminação de uma instância IP através de nx_ip_delete.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1337">This event represents deleting an IP instance via nx_ip_delete.</span></span>

<span data-ttu-id="18ca0-1338">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1338">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1339">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1339">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1340">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1340">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-1341">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1341">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1342">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1342">Info Field 4: Not used</span></span>

### <a name="ip-driver-direct-command"></a><span data-ttu-id="18ca0-1343">Comando Direto do Controlador IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1343">IP Driver Direct Command</span></span> 

#### <a name="nx_ip_driver_direct_command"></a><span data-ttu-id="18ca0-1344">nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="18ca0-1344">nx_ip_driver_direct_command</span></span>

<span data-ttu-id="18ca0-1345">**Ícone** ![ I P driver ícone de comando direto](./media/user-guide/netx-events/image91.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1345">**Icon** ![I P driver direct command icon](./media/user-guide/netx-events/image91.png)</span></span>

<span data-ttu-id="18ca0-1346">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1346">**Description**</span></span>

<span data-ttu-id="18ca0-1347">Este evento representa um comando de controlador de I/O direto via nx_ip_driver_direct_command.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1347">This event represents a direct I/O driver command via nx_ip_driver_direct_command.</span></span>

<span data-ttu-id="18ca0-1348">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1348">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1349">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1349">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1350">Info Field 2: Comando do condutor</span><span class="sxs-lookup"><span data-stu-id="18ca0-1350">Info Field 2: Driver command</span></span>
- <span data-ttu-id="18ca0-1351">Info Campo 3: Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="18ca0-1351">Info Field 3: Return value</span></span>
- <span data-ttu-id="18ca0-1352">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1352">Info Field 4: Not used</span></span>

### <a name="ip-forwarding-disable"></a><span data-ttu-id="18ca0-1353">Desativação ip</span><span class="sxs-lookup"><span data-stu-id="18ca0-1353">IP Forwarding Disable</span></span> 

#### <a name="nx_ip_forwarding_disable"></a><span data-ttu-id="18ca0-1354">nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="18ca0-1354">nx_ip_forwarding_disable</span></span>

<span data-ttu-id="18ca0-1355">**Ícone** ![ I P encaminhamento ícone de desativação](./media/user-guide/netx-events/image92.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1355">**Icon** ![I P forwarding disable icon](./media/user-guide/netx-events/image92.png)</span></span>

<span data-ttu-id="18ca0-1356">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1356">**Description**</span></span>

<span data-ttu-id="18ca0-1357">Este evento representa o encaminhamento IP incapacitante através de nx_ip_forwarding_disable.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1357">This event represents disabling IP forwarding via nx_ip_forwarding_disable.</span></span>

<span data-ttu-id="18ca0-1358">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1358">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1359">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1359">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1360">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1360">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-1361">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1361">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1362">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1362">Info Field 4: Not used</span></span>

### <a name="ip-forwarding-enable"></a><span data-ttu-id="18ca0-1363">Ativar o encaminhamento IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1363">IP Forwarding Enable</span></span> 

#### <a name="nx_ip_forwarding_enable"></a><span data-ttu-id="18ca0-1364">nx_ip_forwarding_enable</span><span class="sxs-lookup"><span data-stu-id="18ca0-1364">nx_ip_forwarding_enable</span></span>

<span data-ttu-id="18ca0-1365">**Ícone** ![ I P encaminhamento ativar ícone](./media/user-guide/netx-events/image93.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1365">**Icon** ![I P forwarding enable icon](./media/user-guide/netx-events/image93.png)</span></span>

<span data-ttu-id="18ca0-1366">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1366">**Description**</span></span>

<span data-ttu-id="18ca0-1367">Este evento representa permitir o encaminhamento ip através de nx_ip_forwarding_enable.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1367">This event represents enabling IP forwarding via nx_ip_forwarding_enable.</span></span>

<span data-ttu-id="18ca0-1368">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1368">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1369">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1369">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1370">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1370">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-1371">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1371">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1372">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1372">Info Field 4: Not used</span></span>

### <a name="ip-fragment-disable"></a><span data-ttu-id="18ca0-1373">Desativar fragmentos ip</span><span class="sxs-lookup"><span data-stu-id="18ca0-1373">IP Fragment Disable</span></span> 

#### <a name="nx_ip_fragment_disable"></a><span data-ttu-id="18ca0-1374">nx_ip_fragment_disable</span><span class="sxs-lookup"><span data-stu-id="18ca0-1374">nx_ip_fragment_disable</span></span>

<span data-ttu-id="18ca0-1375">**Ícone** ![ Ícone de desativação de fragmento de I P](./media/user-guide/netx-events/image94.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1375">**Icon** ![I P fragment disable icon](./media/user-guide/netx-events/image94.png)</span></span>

<span data-ttu-id="18ca0-1376">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1376">**Description**</span></span>

<span data-ttu-id="18ca0-1377">Este evento representa a desativação da fragmentação de IP através de nx_ip_fragment_disable.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1377">This event represents disabling IP fragmenting via nx_ip_fragment_disable.</span></span>

<span data-ttu-id="18ca0-1378">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1378">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1379">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1379">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1380">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1380">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-1381">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1381">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1382">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1382">Info Field 4: Not used</span></span>

### <a name="ip-fragment-enable"></a><span data-ttu-id="18ca0-1383">Ativar o fragmento ip</span><span class="sxs-lookup"><span data-stu-id="18ca0-1383">IP Fragment Enable</span></span> 

#### <a name="nx_ip_fragment_enable"></a><span data-ttu-id="18ca0-1384">nx_ip_fragment_enable</span><span class="sxs-lookup"><span data-stu-id="18ca0-1384">nx_ip_fragment_enable</span></span>

<span data-ttu-id="18ca0-1385">**Ícone** ![ I P fragmento ativar ícone](./media/user-guide/netx-events/image95.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1385">**Icon** ![I P fragment enable icon](./media/user-guide/netx-events/image95.png)</span></span>

<span data-ttu-id="18ca0-1386">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1386">**Description**</span></span>

<span data-ttu-id="18ca0-1387">Este evento representa permitir a fragmentação ip através de nx_ip_fragment_enable.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1387">This event represents enabling IP fragmenting via nx_ip_fragment_enable.</span></span>

<span data-ttu-id="18ca0-1388">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1388">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1389">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1389">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1390">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1390">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-1391">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1391">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1392">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1392">Info Field 4: Not used</span></span>

### <a name="ip-gateway-address-set"></a><span data-ttu-id="18ca0-1393">Conjunto de endereços IP Gateway</span><span class="sxs-lookup"><span data-stu-id="18ca0-1393">IP Gateway Address Set</span></span> 

#### <a name="nx_ip_gateway_address_set"></a><span data-ttu-id="18ca0-1394">nx_ip_gateway_address_set</span><span class="sxs-lookup"><span data-stu-id="18ca0-1394">nx_ip_gateway_address_set</span></span>

<span data-ttu-id="18ca0-1395">**Ícone** ![ Ícone definido de endereço de gateway I P](./media/user-guide/netx-events/image96.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1395">**Icon** ![I P gateway address set icon](./media/user-guide/netx-events/image96.png)</span></span>

<span data-ttu-id="18ca0-1396">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1396">**Description**</span></span>

<span data-ttu-id="18ca0-1397">Este evento representa a definição do endereço IP gateway através de nx_ip_gateway_address_set.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1397">This event represents setting the gateway IP address via nx_ip_gateway_address_set.</span></span>

<span data-ttu-id="18ca0-1398">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1398">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1399">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1399">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1400">Info Field 2: Endereço IP gateway</span><span class="sxs-lookup"><span data-stu-id="18ca0-1400">Info Field 2: Gateway IP address</span></span>
- <span data-ttu-id="18ca0-1401">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1401">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1402">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1402">Info Field 4: Not used</span></span>

### <a name="ip-information-get"></a><span data-ttu-id="18ca0-1403">Informação IP Obter</span><span class="sxs-lookup"><span data-stu-id="18ca0-1403">IP Information Get</span></span> 

#### <a name="nx_ip_info_get"></a><span data-ttu-id="18ca0-1404">nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="18ca0-1404">nx_ip_info_get</span></span>

<span data-ttu-id="18ca0-1405">**Ícone** ![ I P informações obter ícone](./media/user-guide/netx-events/image97.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1405">**Icon** ![I P information get icon](./media/user-guide/netx-events/image97.png)</span></span>

<span data-ttu-id="18ca0-1406">**Descrição** Este evento representa obter informações ip através de nx_ip_info_get.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1406">**Description** This event represents getting IP information via nx_ip_info_get.</span></span>

<span data-ttu-id="18ca0-1407">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1407">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1408">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1408">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1409">Info Field 2: BYTES IP enviados</span><span class="sxs-lookup"><span data-stu-id="18ca0-1409">Info Field 2: IP bytes sent</span></span>
- <span data-ttu-id="18ca0-1410">Info Field 3: BYTES IP recebidos</span><span class="sxs-lookup"><span data-stu-id="18ca0-1410">Info Field 3: IP bytes received</span></span>
- <span data-ttu-id="18ca0-1411">Info Field 4: Pacotes IP caíram</span><span class="sxs-lookup"><span data-stu-id="18ca0-1411">Info Field 4: IP packets dropped</span></span>

### <a name="ip-interface-attach"></a><span data-ttu-id="18ca0-1412">Anexação de interface IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1412">IP Interface Attach</span></span> 

#### <a name="nx_interface_attach"></a><span data-ttu-id="18ca0-1413">nx_interface_attach</span><span class="sxs-lookup"><span data-stu-id="18ca0-1413">nx_interface_attach</span></span>

<span data-ttu-id="18ca0-1414">**Ícone** ![ I ícone de anexação i p iterface](./media/user-guide/netx-events/image98.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1414">**Icon** ![I P iterface attach icon](./media/user-guide/netx-events/image98.png)</span></span>

<span data-ttu-id="18ca0-1415">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1415">**Description**</span></span>

<span data-ttu-id="18ca0-1416">Este evento representa uma interface de rede secundária sendo anexada à instância IP através de nx_ip_interface_attach.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1416">This event represents a secondary network interface being attached to the IP instance via nx_ip_interface_attach.</span></span>

<span data-ttu-id="18ca0-1417">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1417">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1418">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1418">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1419">Info Field 2: Interface ENDEREÇO IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1419">Info Field 2: Interface IP Address</span></span>
- <span data-ttu-id="18ca0-1420">Info Field 3: Índice na tabela de interface IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1420">Info Field 3: Index into IP interface table</span></span>
- <span data-ttu-id="18ca0-1421">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1421">Info Field 4: Not used</span></span>

### <a name="ip-interface-info-get"></a><span data-ttu-id="18ca0-1422">Informação de interface IP Obter</span><span class="sxs-lookup"><span data-stu-id="18ca0-1422">IP Interface Info Get</span></span> 

#### <a name="nx_ip_interface_info_get"></a><span data-ttu-id="18ca0-1423">nx_ip_interface_info_get</span><span class="sxs-lookup"><span data-stu-id="18ca0-1423">nx_ip_interface_info_get</span></span>

<span data-ttu-id="18ca0-1424">**Ícone** ![ Info de interface IP obter ícone](./media/user-guide/netx-events/image99.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1424">**Icon** ![ IP interface info get icon](./media/user-guide/netx-events/image99.png)</span></span>

<span data-ttu-id="18ca0-1425">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1425">**Description**</span></span>

<span data-ttu-id="18ca0-1426">Este evento representa informações obtidas a partir da interface de rede especificada através de nx_ip_interface_info_get.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1426">This event represents information retrieved from the specified network interface via nx_ip_interface_info_get.</span></span>

<span data-ttu-id="18ca0-1427">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1427">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1428">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1428">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1429">Info Field 2: Interface ENDEREÇO IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1429">Info Field 2: Interface IP address</span></span>
- <span data-ttu-id="18ca0-1430">Info Field 3: Interface MAC endereço MSB</span><span class="sxs-lookup"><span data-stu-id="18ca0-1430">Info Field 3: Interface MAC address msb</span></span>
- <span data-ttu-id="18ca0-1431">Info Field 4: Interface MAC endereço lsb</span><span class="sxs-lookup"><span data-stu-id="18ca0-1431">Info Field 4: Interface MAC address lsb</span></span>

### <a name="ip-raw-packet-disable"></a><span data-ttu-id="18ca0-1432">Pacote cru IP Desativar</span><span class="sxs-lookup"><span data-stu-id="18ca0-1432">IP Raw Packet Disable</span></span> 

#### <a name="nx_ip_raw_packet_disable"></a><span data-ttu-id="18ca0-1433">nx_ip_raw_packet_disable</span><span class="sxs-lookup"><span data-stu-id="18ca0-1433">nx_ip_raw_packet_disable</span></span>

<span data-ttu-id="18ca0-1434">**Ícone** ![ I P pacote cru desativar ícone](./media/user-guide/netx-events/image100.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1434">**Icon** ![I P raw packet disable icon](./media/user-guide/netx-events/image100.png)</span></span>

<span data-ttu-id="18ca0-1435">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1435">**Description**</span></span>

<span data-ttu-id="18ca0-1436">Este evento representa a desativação da comunicação de pacotes IP crus através de nx_ip_raw_packet_disable.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1436">This event represents disabling raw IP packet communication via nx_ip_raw_packet_disable.</span></span>

<span data-ttu-id="18ca0-1437">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1437">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1438">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1438">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1439">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1439">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-1440">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1440">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1441">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1441">Info Field 4: Not used</span></span>

### <a name="ip-raw-packet-enable"></a><span data-ttu-id="18ca0-1442">IP Pacote Cru Ativar</span><span class="sxs-lookup"><span data-stu-id="18ca0-1442">IP Raw Packet Enable</span></span> 

#### <a name="nx_ip_raw_packet_enable"></a><span data-ttu-id="18ca0-1443">nx_ip_raw_packet_enable</span><span class="sxs-lookup"><span data-stu-id="18ca0-1443">nx_ip_raw_packet_enable</span></span>

<span data-ttu-id="18ca0-1444">**Ícone** ![ I P pacote cru ativar ícone](./media/user-guide/netx-events/image101.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1444">**Icon** ![I P raw packet enable icon](./media/user-guide/netx-events/image101.png)</span></span>

<span data-ttu-id="18ca0-1445">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1445">**Description**</span></span>

<span data-ttu-id="18ca0-1446">Este evento representa permitir a comunicação de pacotes IP crus através de nx_ip_raw_packet_enable.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1446">This event represents enabling raw IP packet communication via nx_ip_raw_packet_enable.</span></span>

<span data-ttu-id="18ca0-1447">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1447">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1448">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1448">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1449">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1449">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-1450">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1450">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1451">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1451">Info Field 4: Not used</span></span>

### <a name="ip-raw-packet-receive"></a><span data-ttu-id="18ca0-1452">Pacote RAW IP Receber</span><span class="sxs-lookup"><span data-stu-id="18ca0-1452">IP Raw Packet Receive</span></span> 

#### <a name="nx_ip_raw_packet_receive"></a><span data-ttu-id="18ca0-1453">nx_ip_raw_packet_receive</span><span class="sxs-lookup"><span data-stu-id="18ca0-1453">nx_ip_raw_packet_receive</span></span>

<span data-ttu-id="18ca0-1454">**Ícone** ![ I P pacote cru receber ícone](./media/user-guide/netx-events/image102.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1454">**Icon** ![I P raw packet receive icon](./media/user-guide/netx-events/image102.png)</span></span>

<span data-ttu-id="18ca0-1455">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1455">**Description**</span></span>

<span data-ttu-id="18ca0-1456">Este evento representa a receção de um pacote IP cru via nx_ip_raw_packet_receive.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1456">This event represents receiving a raw IP packet via nx_ip_raw_packet_receive.</span></span>

<span data-ttu-id="18ca0-1457">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1457">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1458">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1458">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1459">Info Field 2: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-1459">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-1460">Info Field 3: Opção de espera</span><span class="sxs-lookup"><span data-stu-id="18ca0-1460">Info Field 3: Wait option</span></span>
- <span data-ttu-id="18ca0-1461">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1461">Info Field 4: Not used</span></span>

### <a name="ip-raw-packet-send"></a><span data-ttu-id="18ca0-1462">IP Pacote Cru Enviar</span><span class="sxs-lookup"><span data-stu-id="18ca0-1462">IP Raw Packet Send</span></span> 

#### <a name="nx_ip_raw_packet_send"></a><span data-ttu-id="18ca0-1463">nx_ip_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="18ca0-1463">nx_ip_raw_packet_send</span></span>

<span data-ttu-id="18ca0-1464">**Ícone** ![ I P pacote cru enviar ícone](./media/user-guide/netx-events/image103.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1464">**Icon** ![I P raw packet send icon](./media/user-guide/netx-events/image103.png)</span></span>

<span data-ttu-id="18ca0-1465">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1465">**Description**</span></span>

<span data-ttu-id="18ca0-1466">Este evento representa o envio de um pacote IP cru via nx_ip_raw_packet_send.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1466">This event represents sending a raw IP packet via nx_ip_raw_packet_send.</span></span>

<span data-ttu-id="18ca0-1467">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1467">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1468">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1468">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1469">Info Field 2: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-1469">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-1470">Info Field 3: Endereço IP de destino</span><span class="sxs-lookup"><span data-stu-id="18ca0-1470">Info Field 3: Destination IP address</span></span>
- <span data-ttu-id="18ca0-1471">Info Field 4: Tipo de serviço</span><span class="sxs-lookup"><span data-stu-id="18ca0-1471">Info Field 4: Type of service</span></span>

### <a name="ip-static-route-add"></a><span data-ttu-id="18ca0-1472">Adicionar rota estática IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1472">IP Static Route Add</span></span> 

#### <a name="nx_ip_static_route_add"></a><span data-ttu-id="18ca0-1473">nx_ip_static_route_add</span><span class="sxs-lookup"><span data-stu-id="18ca0-1473">nx_ip_static_route_add</span></span>

<span data-ttu-id="18ca0-1474">**Ícone** ![ I P rota estática adicionar ícone](./media/user-guide/netx-events/image104.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1474">**Icon** ![I P static route add icon](./media/user-guide/netx-events/image104.png)</span></span>

<span data-ttu-id="18ca0-1475">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1475">**Description**</span></span>

<span data-ttu-id="18ca0-1476">Este evento representa uma rota estática sendo adicionada à tabela de encaminhamento de instância IP através de nx_ip_static_route_add.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1476">This event represents a static route being added to the IP instance routing table via nx_ip_static_route_add.</span></span>

<span data-ttu-id="18ca0-1477">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1477">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1478">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1478">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1479">Info Field 2: Endereço de rede</span><span class="sxs-lookup"><span data-stu-id="18ca0-1479">Info Field 2: Network address</span></span>
- <span data-ttu-id="18ca0-1480">Info Field 3: Máscara de rede</span><span class="sxs-lookup"><span data-stu-id="18ca0-1480">Info Field 3: Network mask</span></span>
- <span data-ttu-id="18ca0-1481">Info Field 4: Próximo salto</span><span class="sxs-lookup"><span data-stu-id="18ca0-1481">Info Field 4: Next hop</span></span>

### <a name="ip-static-route-delete"></a><span data-ttu-id="18ca0-1482">Eliminação da Rota Estática IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1482">IP Static Route Delete</span></span> 

#### <a name="nx_ip_static_route_delete"></a><span data-ttu-id="18ca0-1483">nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="18ca0-1483">nx_ip_static_route_delete</span></span>

<span data-ttu-id="18ca0-1484">**Ícone** ![ I P rute estático apagar ícone](./media/user-guide/netx-events/image105.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1484">**Icon** ![I P static rute delete icon](./media/user-guide/netx-events/image105.png)</span></span>

<span data-ttu-id="18ca0-1485">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1485">**Description**</span></span>

<span data-ttu-id="18ca0-1486">Este evento representa uma rota estática sendo removida da tabela de encaminhamento de instância IP através de nx_ip_static_route_delete.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1486">This event represents a static route being removed from the IP instance routing table via nx_ip_static_route_delete.</span></span>

<span data-ttu-id="18ca0-1487">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1487">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1488">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1488">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1489">Info Field 2: Endereço de rede</span><span class="sxs-lookup"><span data-stu-id="18ca0-1489">Info Field 2: Network address</span></span>
- <span data-ttu-id="18ca0-1490">Info Field 3: Máscara de rede</span><span class="sxs-lookup"><span data-stu-id="18ca0-1490">Info Field 3: Network mask</span></span>
- <span data-ttu-id="18ca0-1491">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1491">Info Field 4: Not used</span></span>

### <a name="ip-status-check"></a><span data-ttu-id="18ca0-1492">Verificação do estado do IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1492">IP Status Check</span></span> 

#### <a name="nx_ip_status_check"></a><span data-ttu-id="18ca0-1493">nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="18ca0-1493">nx_ip_status_check</span></span>

<span data-ttu-id="18ca0-1494">**Ícone** ![ Ícone de verificação de estado I P](./media/user-guide/netx-events/image106.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1494">**Icon** ![I P status check icon](./media/user-guide/netx-events/image106.png)</span></span>

<span data-ttu-id="18ca0-1495">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1495">**Description**</span></span>

<span data-ttu-id="18ca0-1496">Este evento representa a verificação de um estado de IP através de nx_ip_status_check.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1496">This event represents checking for an IP status via nx_ip_status_check.</span></span>

<span data-ttu-id="18ca0-1497">Campos de Informação</span><span class="sxs-lookup"><span data-stu-id="18ca0-1497">Information Fields</span></span> 

- <span data-ttu-id="18ca0-1498">Info Field 1: Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1498">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="18ca0-1499">Info Field 2: Estado solicitado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1499">Info Field 2: Requested status</span></span>
- <span data-ttu-id="18ca0-1500">Info Field 3: Estado real</span><span class="sxs-lookup"><span data-stu-id="18ca0-1500">Info Field 3: Actual status</span></span>
- <span data-ttu-id="18ca0-1501">Info Field 4: Opção de espera</span><span class="sxs-lookup"><span data-stu-id="18ca0-1501">Info Field 4: Wait option</span></span>

### <a name="ipsec-enable"></a><span data-ttu-id="18ca0-1502">Ativar IPSEC</span><span class="sxs-lookup"><span data-stu-id="18ca0-1502">IPSEC Enable</span></span> 

#### <a name="nx_ipsec_enable"></a><span data-ttu-id="18ca0-1503">nx_ipsec_enable</span><span class="sxs-lookup"><span data-stu-id="18ca0-1503">nx_ipsec_enable</span></span>

<span data-ttu-id="18ca0-1504">**Ícone** ![ I P S E C ativar ícone](./media/user-guide/netx-events/image107.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1504">**Icon** ![I P S E C enable icon](./media/user-guide/netx-events/image107.png)</span></span>

<span data-ttu-id="18ca0-1505">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1505">**Description**</span></span>

<span data-ttu-id="18ca0-1506">Este evento representa a capacitação dos serviços IPSec na instância IP fornecida através de nx_ipsec_enable.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1506">This event represents enabling IPSec services on the supplied IP instance via nx_ipsec_enable.</span></span>

<span data-ttu-id="18ca0-1507">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1507">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1508">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1508">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1509">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1509">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-1510">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1510">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1511">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1511">Info Field 4: Not used</span></span>

### <a name="packet-allocate"></a><span data-ttu-id="18ca0-1512">Atribuição de pacotes</span><span class="sxs-lookup"><span data-stu-id="18ca0-1512">Packet Allocate</span></span> 

#### <a name="nx_packet_allocate"></a><span data-ttu-id="18ca0-1513">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="18ca0-1513">nx_packet_allocate</span></span>

<span data-ttu-id="18ca0-1514">**Ícone** ![ Ícone de atribuição de pacote](./media/user-guide/netx-events/image108.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1514">**Icon** ![Packet allocate icon](./media/user-guide/netx-events/image108.png)</span></span>

<span data-ttu-id="18ca0-1515">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1515">**Description**</span></span>

<span data-ttu-id="18ca0-1516">Este evento representa a atribuição de um pacote através de nx_packet_allocate.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1516">This event represents allocating a packet via nx_packet_allocate.</span></span>

<span data-ttu-id="18ca0-1517">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1517">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1518">Info Field 1: Ponteiro para a piscina de pacotes</span><span class="sxs-lookup"><span data-stu-id="18ca0-1518">Info Field 1: Pointer to the packet pool</span></span>
- <span data-ttu-id="18ca0-1519">Info Field 2: Ponteiro para pacote atribuído</span><span class="sxs-lookup"><span data-stu-id="18ca0-1519">Info Field 2: Pointer to packet allocated</span></span>
- <span data-ttu-id="18ca0-1520">Info Field 3: Tipo de pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-1520">Info Field 3: Packet type</span></span>
- <span data-ttu-id="18ca0-1521">Info Field 4: Pacotes disponíveis</span><span class="sxs-lookup"><span data-stu-id="18ca0-1521">Info Field 4: Available packets</span></span>

### <a name="packet-copy"></a><span data-ttu-id="18ca0-1522">Cópia de pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-1522">Packet Copy</span></span> 

#### <a name="nx_packet_copy"></a><span data-ttu-id="18ca0-1523">nx_packet_copy</span><span class="sxs-lookup"><span data-stu-id="18ca0-1523">nx_packet_copy</span></span>

<span data-ttu-id="18ca0-1524">**Ícone** ![ Ícone de pacote cpy](./media/user-guide/netx-events/image109.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1524">**Icon** ![Packet cpy icon](./media/user-guide/netx-events/image109.png)</span></span>

<span data-ttu-id="18ca0-1525">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1525">**Description**</span></span>

<span data-ttu-id="18ca0-1526">Este evento representa a cópia de um pacote através de nx_packet_copy.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1526">This event represents copying a packet via nx_packet_copy.</span></span>

<span data-ttu-id="18ca0-1527">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1527">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1528">Info Field 2: Novo ponteiro do pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-1528">Info Field 2: New packet pointer</span></span>
- <span data-ttu-id="18ca0-1529">Info Field 3: Ponteiro para pacote de piscina</span><span class="sxs-lookup"><span data-stu-id="18ca0-1529">Info Field 3: Pointer to packet pool</span></span>
- <span data-ttu-id="18ca0-1530">Info Field 4: Opção de espera</span><span class="sxs-lookup"><span data-stu-id="18ca0-1530">Info Field 4: Wait option</span></span>

### <a name="packet-data-append"></a><span data-ttu-id="18ca0-1531">Apend de dados de pacotes</span><span class="sxs-lookup"><span data-stu-id="18ca0-1531">Packet Data Append</span></span> 

#### <a name="nx_packet_data_append"></a><span data-ttu-id="18ca0-1532">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="18ca0-1532">nx_packet_data_append</span></span>

<span data-ttu-id="18ca0-1533">**Ícone** ![ Ícone de apêndice de dados de pacote](./media/user-guide/netx-events/image110.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1533">**Icon** ![Packet data append icon](./media/user-guide/netx-events/image110.png)</span></span>

<span data-ttu-id="18ca0-1534">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1534">**Description**</span></span>

<span data-ttu-id="18ca0-1535">Este evento representa dados de anexação a um pacote via nx_packet_data_append.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1535">This event represents appending data to a packet via nx_packet_data_append.</span></span>

<span data-ttu-id="18ca0-1536">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1536">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1537">Info Field 1: Ponteiro para o pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-1537">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="18ca0-1538">Info Field 2: Ponteiro para dados</span><span class="sxs-lookup"><span data-stu-id="18ca0-1538">Info Field 2: Pointer to data</span></span>
- <span data-ttu-id="18ca0-1539">Info Field 3: Tamanho dos dados</span><span class="sxs-lookup"><span data-stu-id="18ca0-1539">Info Field 3: Size of data</span></span>
- <span data-ttu-id="18ca0-1540">Info Field 4: Ponteiro para pacote de piscina</span><span class="sxs-lookup"><span data-stu-id="18ca0-1540">Info Field 4: Pointer to packet pool</span></span>

### <a name="packet-data-extract-offset"></a><span data-ttu-id="18ca0-1541">Compensação do extrato de dados do pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-1541">Packet Data Extract Offset</span></span> 

#### <a name="nx_udp_source_extract_offset"></a><span data-ttu-id="18ca0-1542">nx_udp_source_extract_offset</span><span class="sxs-lookup"><span data-stu-id="18ca0-1542">nx_udp_source_extract_offset</span></span>

<span data-ttu-id="18ca0-1543">**Ícone** ![ Ícone de compensação de extrato de dados de pacote](./media/user-guide/netx-events/image111.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1543">**Icon** ![Packet data extract offset icon](./media/user-guide/netx-events/image111.png)</span></span>

<span data-ttu-id="18ca0-1544">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1544">**Description**</span></span>

<span data-ttu-id="18ca0-1545">Este evento representa dados de pacotes que são extraídos num tampão fornecido a partir de um pacote via nx_udp_source_extract_offset.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1545">This event represents packet data that is extracted into a supplied buffer from a packet via nx_udp_source_extract_offset.</span></span>

<span data-ttu-id="18ca0-1546">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1546">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1547">Info Field 1: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-1547">Info Field 1: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-1548">Info Field 2: Tamanho do tampão especificado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1548">Info Field 2: Size of specified buffer</span></span>
- <span data-ttu-id="18ca0-1549">Info Field 3: Número de bytes copiados</span><span class="sxs-lookup"><span data-stu-id="18ca0-1549">Info Field 3: Number of bytes copied</span></span>
- <span data-ttu-id="18ca0-1550">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1550">Info Field 4: Not used</span></span>

### <a name="packet-data-retrieve"></a><span data-ttu-id="18ca0-1551">Recuperação de dados de pacotes</span><span class="sxs-lookup"><span data-stu-id="18ca0-1551">Packet Data Retrieve</span></span> 

#### <a name="nx_packet_data_retrieve"></a><span data-ttu-id="18ca0-1552">nx_packet_data_retrieve</span><span class="sxs-lookup"><span data-stu-id="18ca0-1552">nx_packet_data_retrieve</span></span>

<span data-ttu-id="18ca0-1553">**Ícone** ![ Ícone de recuperação de dados de pacote](./media/user-guide/netx-events/image112.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1553">**Icon** ![Packet data retrieve icon](./media/user-guide/netx-events/image112.png)</span></span>

<span data-ttu-id="18ca0-1554">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1554">**Description**</span></span>

<span data-ttu-id="18ca0-1555">Este evento representa a obtenção de dados de um pacote via nx_packet_data_retrieve.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1555">This event represents retrieving data from a packet via nx_packet_data_retrieve.</span></span>

<span data-ttu-id="18ca0-1556">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1556">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1557">Info Field 1: Ponteiro para o pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-1557">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="18ca0-1558">Info Field 2: Ponteiro para o início do tampão</span><span class="sxs-lookup"><span data-stu-id="18ca0-1558">Info Field 2: Pointer to start of buffer</span></span>
- <span data-ttu-id="18ca0-1559">Info Field 3: Bytes copiados</span><span class="sxs-lookup"><span data-stu-id="18ca0-1559">Info Field 3: Bytes copied</span></span>
- <span data-ttu-id="18ca0-1560">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1560">Info Field 4: Not used</span></span>

### <a name="packet-length-get"></a><span data-ttu-id="18ca0-1561">Comprimento do pacote obter</span><span class="sxs-lookup"><span data-stu-id="18ca0-1561">Packet Length Get</span></span> 

#### <a name="nx_packet_length_get"></a><span data-ttu-id="18ca0-1562">nx_packet_length_get</span><span class="sxs-lookup"><span data-stu-id="18ca0-1562">nx_packet_length_get</span></span>

<span data-ttu-id="18ca0-1563">**Ícone** ![ Comprimento do pacote obter ícone](./media/user-guide/netx-events/image113.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1563">**Icon** ![Packet length get icon](./media/user-guide/netx-events/image113.png)</span></span>

<span data-ttu-id="18ca0-1564">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1564">**Description**</span></span>

<span data-ttu-id="18ca0-1565">Este evento representa obter o comprimento de um pacote através de nx_packet_length_get.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1565">This event represents getting the length of a packet via nx_packet_length_get.</span></span>

<span data-ttu-id="18ca0-1566">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1566">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1567">Info Field 1: Ponteiro para o pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-1567">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="18ca0-1568">Info Field 2: Comprimento do pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-1568">Info Field 2: Packet length</span></span>
- <span data-ttu-id="18ca0-1569">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1569">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1570">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1570">Info Field 4: Not used</span></span>

### <a name="packet-pool-create"></a><span data-ttu-id="18ca0-1571">Criar pacotes de piscinas</span><span class="sxs-lookup"><span data-stu-id="18ca0-1571">Packet Pool Create</span></span> 

#### <a name="nx_packet_pool_create"></a><span data-ttu-id="18ca0-1572">nx_packet_pool_create</span><span class="sxs-lookup"><span data-stu-id="18ca0-1572">nx_packet_pool_create</span></span>

<span data-ttu-id="18ca0-1573">**Ícone** ![ Pacote de piscina criar ícone](./media/user-guide/netx-events/image114.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1573">**Icon** ![Packet pool create icon](./media/user-guide/netx-events/image114.png)</span></span>

<span data-ttu-id="18ca0-1574">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1574">**Description**</span></span>

<span data-ttu-id="18ca0-1575">Este evento representa a criação de uma piscina de pacotes através de nx_packet_pool_create.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1575">This event represents creating a packet pool via nx_packet_pool_create.</span></span>

<span data-ttu-id="18ca0-1576">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1576">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1577">Info Field 1: Ponteiro para a piscina de pacotes</span><span class="sxs-lookup"><span data-stu-id="18ca0-1577">Info Field 1: Pointer to the packet pool</span></span>
- <span data-ttu-id="18ca0-1578">Info Field 2: Tamanho da carga útil do pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-1578">Info Field 2: Packet payload size</span></span>
- <span data-ttu-id="18ca0-1579">Info Field 3: Ponteiro para a área da memória da piscina</span><span class="sxs-lookup"><span data-stu-id="18ca0-1579">Info Field 3: Pointer to pool memory area</span></span>
- <span data-ttu-id="18ca0-1580">Info Field 4: Tamanho da área de memória da piscina</span><span class="sxs-lookup"><span data-stu-id="18ca0-1580">Info Field 4: Size of pool memory area</span></span>

### <a name="packet-pool-delete"></a><span data-ttu-id="18ca0-1581">Excluir de pacotes de piscina</span><span class="sxs-lookup"><span data-stu-id="18ca0-1581">Packet Pool Delete</span></span> 

#### <a name="nx_packet_pool_delete"></a><span data-ttu-id="18ca0-1582">nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="18ca0-1582">nx_packet_pool_delete</span></span>

<span data-ttu-id="18ca0-1583">**Ícone** ![ Ícone de excluir piscina de pacote](./media/user-guide/netx-events/image115.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1583">**Icon** ![Packet pool delete icon](./media/user-guide/netx-events/image115.png)</span></span>

<span data-ttu-id="18ca0-1584">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1584">**Description**</span></span>

<span data-ttu-id="18ca0-1585">Este evento representa a eliminação de uma piscina de pacotes através de nx_packet_pool_delete.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1585">This event represents deleting a packet pool via nx_packet_pool_delete.</span></span>

<span data-ttu-id="18ca0-1586">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1586">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1587">Info Field 1: Ponteiro para a piscina de pacotes</span><span class="sxs-lookup"><span data-stu-id="18ca0-1587">Info Field 1: Pointer to the packet pool</span></span>
- <span data-ttu-id="18ca0-1588">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1588">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-1589">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1589">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1590">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1590">Info Field 4: Not used</span></span>

#### <a name="packet-pool-information-get"></a><span data-ttu-id="18ca0-1591">Informações de piscina de pacotes obter</span><span class="sxs-lookup"><span data-stu-id="18ca0-1591">Packet Pool Information Get</span></span> 

#### <a name="nx_packet_pool_info_get"></a><span data-ttu-id="18ca0-1592">nx_packet_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="18ca0-1592">nx_packet_pool_info_get</span></span>

<span data-ttu-id="18ca0-1593">**Ícone** ![ Informações de piscina de pacote obter ícone](./media/user-guide/netx-events/image116.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1593">**Icon** ![Packet pool information get icon](./media/user-guide/netx-events/image116.png)</span></span>

<span data-ttu-id="18ca0-1594">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1594">**Description**</span></span>

<span data-ttu-id="18ca0-1595">Este evento representa obter informações de pacotes através de nx_packet_pool_info_get.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1595">This event represents getting packet pool information via nx_packet_pool_info_get.</span></span>

<span data-ttu-id="18ca0-1596">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1596">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1597">Info Field 1: Ponteiro para pacote de piscina</span><span class="sxs-lookup"><span data-stu-id="18ca0-1597">Info Field 1: Pointer to packet pool</span></span>
- <span data-ttu-id="18ca0-1598">Info Field 2: Total de pacotes</span><span class="sxs-lookup"><span data-stu-id="18ca0-1598">Info Field 2: Total packets</span></span>
- <span data-ttu-id="18ca0-1599">Info Field 3: Pacotes disponíveis</span><span class="sxs-lookup"><span data-stu-id="18ca0-1599">Info Field 3: Available packets</span></span>
- <span data-ttu-id="18ca0-1600">Info Field 4: Pedidos vazios</span><span class="sxs-lookup"><span data-stu-id="18ca0-1600">Info Field 4: Empty requests</span></span>

### <a name="packet-release"></a><span data-ttu-id="18ca0-1601">Lançamento de pacotes</span><span class="sxs-lookup"><span data-stu-id="18ca0-1601">Packet Release</span></span> 

#### <a name="nx_packet_data_release"></a><span data-ttu-id="18ca0-1602">nx_packet_data_release</span><span class="sxs-lookup"><span data-stu-id="18ca0-1602">nx_packet_data_release</span></span>

<span data-ttu-id="18ca0-1603">**Ícone** ![ Ícone de lançamento de pacote](./media/user-guide/netx-events/image117.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1603">**Icon** ![Packet release icon](./media/user-guide/netx-events/image117.png)</span></span>

<span data-ttu-id="18ca0-1604">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1604">**Description**</span></span>

<span data-ttu-id="18ca0-1605">Este evento representa a libertação de um pacote via nx_packet_release.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1605">This event represents releasing a packet via nx_packet_release.</span></span>

<span data-ttu-id="18ca0-1606">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1606">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1607">Info Field 1: Ponteiro para o pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-1607">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="18ca0-1608">Info Field 2: Estado do pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-1608">Info Field 2: Packet status</span></span>
- <span data-ttu-id="18ca0-1609">Info Field 3: Pacotes disponíveis</span><span class="sxs-lookup"><span data-stu-id="18ca0-1609">Info Field 3: Available packets</span></span>
- <span data-ttu-id="18ca0-1610">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1610">Info Field 4: Not used</span></span>

### <a name="packet-transmit-release"></a><span data-ttu-id="18ca0-1611">Lançamento do pacote de transmissão</span><span class="sxs-lookup"><span data-stu-id="18ca0-1611">Packet Transmit Release</span></span> 

#### <a name="nx_packet_transmit_release"></a><span data-ttu-id="18ca0-1612">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="18ca0-1612">nx_packet_transmit_release</span></span>

<span data-ttu-id="18ca0-1613">**Ícone** ![ Ícone de libertação de transmissão de pacote](./media/user-guide/netx-events/image118.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1613">**Icon** ![Packet transmit release icon](./media/user-guide/netx-events/image118.png)</span></span>

<span data-ttu-id="18ca0-1614">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1614">**Description**</span></span>

<span data-ttu-id="18ca0-1615">Este evento representa a libertação de um pacote de transmissão via nx_packet_transmit_release.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1615">This event represents releasing a transmit packet via nx_packet_transmit_release.</span></span>

<span data-ttu-id="18ca0-1616">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1616">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1617">Info Field 1: Ponteiro para o pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-1617">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="18ca0-1618">Info Field 2: Estado do pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-1618">Info Field 2: Packet status</span></span>
- <span data-ttu-id="18ca0-1619">Info Field 3: Pacotes disponíveis</span><span class="sxs-lookup"><span data-stu-id="18ca0-1619">Info Field 3: Available packets</span></span>
- <span data-ttu-id="18ca0-1620">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1620">Info Field 4: Not used</span></span>

### <a name="rarp-disable"></a><span data-ttu-id="18ca0-1621">Desativar RARP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1621">RARP Disable</span></span> 

#### <a name="nx_rarp_disable"></a><span data-ttu-id="18ca0-1622">nx_rarp_disable</span><span class="sxs-lookup"><span data-stu-id="18ca0-1622">nx_rarp_disable</span></span>

<span data-ttu-id="18ca0-1623">**Ícone** ![ R A R P desativar ícone](./media/user-guide/netx-events/image119.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1623">**Icon** ![R A R P disable icon](./media/user-guide/netx-events/image119.png)</span></span>

<span data-ttu-id="18ca0-1624">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1624">**Description**</span></span>

<span data-ttu-id="18ca0-1625">Este evento representa a desativação da RARP através de nx_rarp_disable.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1625">This event represents disabling RARP via nx_rarp_disable.</span></span>

<span data-ttu-id="18ca0-1626">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1626">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1627">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1627">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1628">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1628">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-1629">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1629">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1630">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1630">Info Field 4: Not used</span></span>

### <a name="rarp-enable"></a><span data-ttu-id="18ca0-1631">Ativar RARP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1631">RARP Enable</span></span> 

#### <a name="nx_rarp_enable"></a><span data-ttu-id="18ca0-1632">nx_rarp_enable</span><span class="sxs-lookup"><span data-stu-id="18ca0-1632">nx_rarp_enable</span></span>

<span data-ttu-id="18ca0-1633">**Ícone** ![ R A R P ativar ícone](./media/user-guide/netx-events/image120.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1633">**Icon** ![R A R P enable icon](./media/user-guide/netx-events/image120.png)</span></span>

<span data-ttu-id="18ca0-1634">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1634">**Description**</span></span>

<span data-ttu-id="18ca0-1635">Este evento representa permitir a RARP através de nx_rarp_enable.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1635">This event represents enabling RARP via nx_rarp_enable.</span></span>

<span data-ttu-id="18ca0-1636">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1636">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1637">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1637">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1638">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1638">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-1639">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1639">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1640">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1640">Info Field 4: Not used</span></span>

### <a name="rarp-information-get"></a><span data-ttu-id="18ca0-1641">Informação RARP Obter</span><span class="sxs-lookup"><span data-stu-id="18ca0-1641">RARP Information Get</span></span> 

#### <a name="nx_rarp_info_get"></a><span data-ttu-id="18ca0-1642">nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="18ca0-1642">nx_rarp_info_get</span></span>

<span data-ttu-id="18ca0-1643">**Ícone** ![ R A R P informações obter ícone](./media/user-guide/netx-events/image121.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1643">**Icon** ![R A R P information get icon](./media/user-guide/netx-events/image121.png)</span></span>

<span data-ttu-id="18ca0-1644">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1644">**Description**</span></span>

<span data-ttu-id="18ca0-1645">Este evento representa obter informações da RARP através de nx_rarp_info_get.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1645">This event represents getting RARP information via nx_rarp_info_get.</span></span>

<span data-ttu-id="18ca0-1646">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1646">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1647">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1647">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1648">Info Field 2: Pedidos enviados</span><span class="sxs-lookup"><span data-stu-id="18ca0-1648">Info Field 2: Requests sent</span></span>
- <span data-ttu-id="18ca0-1649">Info Field 3: Respostas recebidas</span><span class="sxs-lookup"><span data-stu-id="18ca0-1649">Info Field 3: Responses received</span></span>
- <span data-ttu-id="18ca0-1650">Info Field 4: Respostas inválidas</span><span class="sxs-lookup"><span data-stu-id="18ca0-1650">Info Field 4: Invalid responses</span></span>

### <a name="system-initialize"></a><span data-ttu-id="18ca0-1651">Inicialização do sistema</span><span class="sxs-lookup"><span data-stu-id="18ca0-1651">System Initialize</span></span> 

#### <a name="nx_system_initialize"></a><span data-ttu-id="18ca0-1652">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="18ca0-1652">nx_system_initialize</span></span>

<span data-ttu-id="18ca0-1653">**Ícone** ![ Ícone inicializando o sistema](./media/user-guide/netx-events/image122.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1653">**Icon** ![System initialize icon](./media/user-guide/netx-events/image122.png)</span></span>

<span data-ttu-id="18ca0-1654">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1654">**Description**</span></span>

<span data-ttu-id="18ca0-1655">Este evento representa a inicialização do NetX através de nx_system_initialize.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1655">This event represents initializing NetX via nx_system_initialize.</span></span>

<span data-ttu-id="18ca0-1656">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1656">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1657">Info Field 1: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1657">Info Field 1: Not used</span></span>
- <span data-ttu-id="18ca0-1658">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1658">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-1659">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1659">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1660">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1660">Info Field 4: Not used</span></span>

### <a name="tcp-client-socket-bind"></a><span data-ttu-id="18ca0-1661">Ligação de tomada de cliente TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1661">TCP Client Socket Bind</span></span> 

#### <a name="nx_tcp_client_socket_bind"></a><span data-ttu-id="18ca0-1662">nx_tcp_client_socket_bind</span><span class="sxs-lookup"><span data-stu-id="18ca0-1662">nx_tcp_client_socket_bind</span></span>

<span data-ttu-id="18ca0-1663">**Ícone** ![ Ícone de ligação de tomada de cliente T P](./media/user-guide/netx-events/image123.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1663">**Icon** ![T  P client socket bind icon](./media/user-guide/netx-events/image123.png)</span></span>

<span data-ttu-id="18ca0-1664">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1664">**Description**</span></span>

<span data-ttu-id="18ca0-1665">Este evento representa a ligação de uma tomada de cliente a uma porta através de nx_tcp_client_socket_bind.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1665">This event represents binding a client socket to a port via nx_tcp_client_socket_bind.</span></span>

<span data-ttu-id="18ca0-1666">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1666">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1667">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1667">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1668">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1668">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1669">Info Field 3: Porta solicitada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1669">Info Field 3: Port requested</span></span>
- <span data-ttu-id="18ca0-1670">Info Field 4: Opção de espera</span><span class="sxs-lookup"><span data-stu-id="18ca0-1670">Info Field 4: Wait option</span></span>

### <a name="tcp-client-socket-connect"></a><span data-ttu-id="18ca0-1671">Ligação de tomada de cliente TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1671">TCP Client Socket Connect</span></span> 

#### <a name="nx_tcp_client_socket_connect"></a><span data-ttu-id="18ca0-1672">nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="18ca0-1672">nx_tcp_client_socket_connect</span></span>

<span data-ttu-id="18ca0-1673">**Ícone** ![ Ícone de ligação de tomada de cliente T C P](./media/user-guide/netx-events/image124.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1673">**Icon** ![T C P client socket connect icon](./media/user-guide/netx-events/image124.png)</span></span>

<span data-ttu-id="18ca0-1674">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1674">**Description**</span></span>

<span data-ttu-id="18ca0-1675">Este evento representa a realização de uma ligação de tomada de cliente através de nx_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1675">This event represents making a client socket connection via nx_tcp_client_socket_connect.</span></span>

<span data-ttu-id="18ca0-1676">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1676">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1677">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1677">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1678">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1678">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1679">Info Field 3: Endereço IP do servidor</span><span class="sxs-lookup"><span data-stu-id="18ca0-1679">Info Field 3: Server IP address</span></span>
- <span data-ttu-id="18ca0-1680">Info Field 4: Porta do servidor solicitada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1680">Info Field 4: Server port requested</span></span>

### <a name="tcp-client-socket-port-get"></a><span data-ttu-id="18ca0-1681">Porta de tomada de cliente TCP obter</span><span class="sxs-lookup"><span data-stu-id="18ca0-1681">TCP Client Socket Port Get</span></span> 

#### <a name="nx_tcp_client_socket_port_get"></a><span data-ttu-id="18ca0-1682">nx_tcp_client_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="18ca0-1682">nx_tcp_client_socket_port_get</span></span>

<span data-ttu-id="18ca0-1683">**Ícone** ![ Porta de tomada de cliente T C P obter ícone](./media/user-guide/netx-events/image125.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1683">**Icon** ![T C P client socket port get icon](./media/user-guide/netx-events/image125.png)</span></span>

<span data-ttu-id="18ca0-1684">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1684">**Description**</span></span>

<span data-ttu-id="18ca0-1685">Este evento representa obter o número da porta da tomada do cliente através de nx_tcp_client_socket_port_get.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1685">This event represents getting the client socket port number via nx_tcp_client_socket_port_get.</span></span>

<span data-ttu-id="18ca0-1686">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1686">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1687">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1687">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1688">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1688">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1689">Info Campo 3: Número de porta</span><span class="sxs-lookup"><span data-stu-id="18ca0-1689">Info Field 3: Port number</span></span>
- <span data-ttu-id="18ca0-1690">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1690">Info Field 4: Not used</span></span>

### <a name="tcp-client-socket-unbind"></a><span data-ttu-id="18ca0-1691">Tomada de cliente TCP Unbind</span><span class="sxs-lookup"><span data-stu-id="18ca0-1691">TCP Client Socket Unbind</span></span> 

#### <a name="nx_tcp_client_socket_unbind"></a><span data-ttu-id="18ca0-1692">nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="18ca0-1692">nx_tcp_client_socket_unbind</span></span>

<span data-ttu-id="18ca0-1693">**Ícone** ![ Ícone unbind de tomada de cliente T C P](./media/user-guide/netx-events/image126.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1693">**Icon** ![T C P client socket unbind icon](./media/user-guide/netx-events/image126.png)</span></span>

<span data-ttu-id="18ca0-1694">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1694">**Description**</span></span>

<span data-ttu-id="18ca0-1695">Este evento representa a desvinão da porta associada à tomada através de nx_tcp_client_socket_unbind.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1695">This event represents unbinding the port associated with the socket via nx_tcp_client_socket_unbind.</span></span>

<span data-ttu-id="18ca0-1696">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1696">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1697">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1697">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1698">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1698">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1699">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1699">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1700">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1700">Info Field 4: Not used</span></span>

### <a name="tcp-enable"></a><span data-ttu-id="18ca0-1701">Ativar TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1701">TCP Enable</span></span> 

#### <a name="nx_tcp_enable"></a><span data-ttu-id="18ca0-1702">nx_tcp_enable</span><span class="sxs-lookup"><span data-stu-id="18ca0-1702">nx_tcp_enable</span></span>

<span data-ttu-id="18ca0-1703">**Ícone** ![ T C P ativar ícone](./media/user-guide/netx-events/image127.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1703">**Icon** ![T C P enable icon](./media/user-guide/netx-events/image127.png)</span></span>

<span data-ttu-id="18ca0-1704">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1704">**Description**</span></span>

<span data-ttu-id="18ca0-1705">Este evento representa permitir a TCP através de nx_tcp_enable.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1705">This event represents enabling TCP via nx_tcp_enable.</span></span>

<span data-ttu-id="18ca0-1706">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1706">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1707">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1707">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1708">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1708">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-1709">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1709">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1710">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1710">Info Field 4: Not used</span></span>

###  <a name="tcp-free-port-find-tcp-free-port-find"></a><span data-ttu-id="18ca0-1711">Porto Livre TCP Encontre porto livre TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1711">TCP Free Port Find TCP Free Port Find</span></span> 

#### <a name="nx_tcp_free_port_find"></a><span data-ttu-id="18ca0-1712">nx_tcp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="18ca0-1712">nx_tcp_free_port_find</span></span>

<span data-ttu-id="18ca0-1713">**Ícone** ![ Ícone de encontrar porta livre T CP](./media/user-guide/netx-events/image128.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1713">**Icon** ![T  CP free port find icon](./media/user-guide/netx-events/image128.png)</span></span>

<span data-ttu-id="18ca0-1714">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1714">**Description**</span></span>

<span data-ttu-id="18ca0-1715">Este evento representa encontrar uma porta TCP gratuita através de nx_tcp_free_port_find.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1715">This event represents finding a free TCP port via nx_tcp_free_port_find.</span></span>

<span data-ttu-id="18ca0-1716">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1716">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1717">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1717">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1718">Info Field 2: Início do número da porta de pesquisa</span><span class="sxs-lookup"><span data-stu-id="18ca0-1718">Info Field 2: Starting search port number</span></span>
- <span data-ttu-id="18ca0-1719">Info Field 3: Número de porta grátis</span><span class="sxs-lookup"><span data-stu-id="18ca0-1719">Info Field 3: Free port number</span></span>
- <span data-ttu-id="18ca0-1720">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1720">Info Field 4: Not used</span></span>

###  <a name="tcp-infomation-get"></a><span data-ttu-id="18ca0-1721">Infomation TCP Obter</span><span class="sxs-lookup"><span data-stu-id="18ca0-1721">TCP Infomation Get</span></span> 

#### <a name="nx_tcp_info_get"></a><span data-ttu-id="18ca0-1722">nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="18ca0-1722">nx_tcp_info_get</span></span>

<span data-ttu-id="18ca0-1723">**Ícone** ![ T C P informações obter ícone](./media/user-guide/netx-events/image129.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1723">**Icon** ![T C P infomation get icon](./media/user-guide/netx-events/image129.png)</span></span>

<span data-ttu-id="18ca0-1724">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1724">**Description**</span></span>

<span data-ttu-id="18ca0-1725">Este evento representa a recuperação de informações TCP para a instância IP especificada através de nx_tcp_info_get.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1725">This event represents retrieving TCP information for the specified IP instance via nx_tcp_info_get.</span></span>

<span data-ttu-id="18ca0-1726">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1726">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1727">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1727">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1728">Info Field 2: Número de bytes enviados</span><span class="sxs-lookup"><span data-stu-id="18ca0-1728">Info Field 2: Number of bytes sent</span></span>
- <span data-ttu-id="18ca0-1729">Info Field 3: Número de bytes recebidos</span><span class="sxs-lookup"><span data-stu-id="18ca0-1729">Info Field 3: Number of bytes received</span></span>
- <span data-ttu-id="18ca0-1730">Info Field 4: Número de pacotes inválidos</span><span class="sxs-lookup"><span data-stu-id="18ca0-1730">Info Field 4: Number of invalid packets</span></span>

###  <a name="tcp-server-socket-accept"></a><span data-ttu-id="18ca0-1731">Tomada de servidor TCP Aceite</span><span class="sxs-lookup"><span data-stu-id="18ca0-1731">TCP Server Socket Accept</span></span> 

#### <a name="nx_tcp_server_socket_accept"></a><span data-ttu-id="18ca0-1732">nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="18ca0-1732">nx_tcp_server_socket_accept</span></span>

<span data-ttu-id="18ca0-1733">**Ícone** ![ Tomada do servidor T C P aceite ícone](./media/user-guide/netx-events/image130.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1733">**Icon** ![T C P server socket accept icon](./media/user-guide/netx-events/image130.png)</span></span>

<span data-ttu-id="18ca0-1734">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1734">**Description**</span></span>

<span data-ttu-id="18ca0-1735">Este evento representa a configuração da tomada do servidor depois de um pedido de ligação ativa ter sido recebido através de nx_tcp_server_socket_accept.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1735">This event represents setting up the server socket after an active connection request was received via nx_tcp_server_socket_accept.</span></span>

<span data-ttu-id="18ca0-1736">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1736">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1737">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1737">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1738">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1738">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1739">Info Field 3: Opção de espera</span><span class="sxs-lookup"><span data-stu-id="18ca0-1739">Info Field 3: Wait option</span></span>
- <span data-ttu-id="18ca0-1740">Info Field 4: Estado da tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1740">Info Field 4: Socket state</span></span>

###  <a name="tcp-server-socket-listen"></a><span data-ttu-id="18ca0-1741">Tomada do servidor TCP Ouvir</span><span class="sxs-lookup"><span data-stu-id="18ca0-1741">TCP Server Socket Listen</span></span> 

#### <a name="nx_tcp_server_socket_listen"></a><span data-ttu-id="18ca0-1742">nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="18ca0-1742">nx_tcp_server_socket_listen</span></span>

<span data-ttu-id="18ca0-1743">**Ícone** ![ Ícone de isten da tomada do servidor T C P](./media/user-guide/netx-events/image131.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1743">**Icon** ![T C P server socket lsten icon](./media/user-guide/netx-events/image131.png)</span></span>

<span data-ttu-id="18ca0-1744">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1744">**Description**</span></span>

<span data-ttu-id="18ca0-1745">Este evento representa registar um pedido de escuta e uma tomada de servidor para a porta TCP especificada via nx_tcp_server_socket_listen.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1745">This event represents register a listen request and a server socket for the specified TCP port via nx_tcp_server_socket_listen.</span></span>

<span data-ttu-id="18ca0-1746">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1746">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1747">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1747">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1748">Info Field 2: Número da porta TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1748">Info Field 2: TCP port number</span></span>
- <span data-ttu-id="18ca0-1749">Info Field 3: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1749">Info Field 3: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1750">Info Field 4: Número máximo de ligações que podem ser em fila</span><span class="sxs-lookup"><span data-stu-id="18ca0-1750">Info Field 4: Maximum number of connections that can be queued</span></span>

###  <a name="tcp-server-socket-relisten"></a><span data-ttu-id="18ca0-1751">Relisten da tomada do servidor TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1751">TCP Server Socket Relisten</span></span> 

#### <a name="nx_tcp_server_socket_relisten"></a><span data-ttu-id="18ca0-1752">nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="18ca0-1752">nx_tcp_server_socket_relisten</span></span>

<span data-ttu-id="18ca0-1753">**Ícone** ![ Tomada de tomada do servidor T C P realista ícone](./media/user-guide/netx-events/image132.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1753">**Icon** ![T C P server socket relisten icon](./media/user-guide/netx-events/image132.png)</span></span>

<span data-ttu-id="18ca0-1754">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1754">**Description**</span></span>

<span data-ttu-id="18ca0-1755">Este evento representa registar outra tomada de servidor para um pedido de escuta existente na porta TCP especificada através de nx_tcp_server_socket_relisten.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1755">This event represents register another server socket for an existing listen request on the specified TCP port via nx_tcp_server_socket_relisten.</span></span>

<span data-ttu-id="18ca0-1756">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1756">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1757">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1757">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1758">Info Field 2: Número da porta TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1758">Info Field 2: TCP port number</span></span>
- <span data-ttu-id="18ca0-1759">Info Field 3: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1759">Info Field 3: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1760">Info Field 4: Estado da tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1760">Info Field 4: Socket state</span></span>

###  <a name="tcp-server-socket-unaccept"></a><span data-ttu-id="18ca0-1761">Tomada de servidor TCP Desacept</span><span class="sxs-lookup"><span data-stu-id="18ca0-1761">TCP Server Socket Unaccept</span></span> 

#### <a name="nx_tcp_server_socket_unaccept"></a><span data-ttu-id="18ca0-1762">nx_tcp_server_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="18ca0-1762">nx_tcp_server_socket_unaccept</span></span>

<span data-ttu-id="18ca0-1763">**Ícone** ![ Ícone de tomada de servidor T C P não aceita](./media/user-guide/netx-events/image133.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1763">**Icon** ![T C P server socket unaccept icon](./media/user-guide/netx-events/image133.png)</span></span>

<span data-ttu-id="18ca0-1764">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1764">**Description**</span></span>

<span data-ttu-id="18ca0-1765">Este evento representa a remoção da tomada do servidor de associação com a porta que recebe uma ligação passiva anterior através de nx_tcp_server_socket_unaccept.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1765">This event represents removing the server socket from association with the port receiving an earlier passive connection via nx_tcp_server_socket_unaccept.</span></span>

<span data-ttu-id="18ca0-1766">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1766">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1767">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1767">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1768">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1768">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1769">Info Field 3: Estado da tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1769">Info Field 3: Socket state</span></span>
- <span data-ttu-id="18ca0-1770">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1770">Info Field 4: Not used</span></span>

###  <a name="tcp-server-socket-unlisten-tcp-server-socket-unlisten"></a><span data-ttu-id="18ca0-1771">Tomada do servidor TCP Desafie a tomada do servidor TCP Unlisten</span><span class="sxs-lookup"><span data-stu-id="18ca0-1771">TCP Server Socket Unlisten TCP Server Socket Unlisten</span></span> 

#### <a name="nx_tcp_server_socket_unlisten"></a><span data-ttu-id="18ca0-1772">nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="18ca0-1772">nx_tcp_server_socket_unlisten</span></span>

<span data-ttu-id="18ca0-1773">**Ícone** ![ Tomada de servidor T C P unlisten ícone](./media/user-guide/netx-events/image134.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1773">**Icon** ![T C P server socket unlisten icon](./media/user-guide/netx-events/image134.png)</span></span>

<span data-ttu-id="18ca0-1774">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1774">**Description**</span></span>

<span data-ttu-id="18ca0-1775">Este evento representa a remoção de um pedido de escuta anterior para a porta TCP especificada através de nx_tcp_server_socket_unlisten.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1775">This event represents removing a previous listen request for the specified TCP port via nx_tcp_server_socket_unlisten.</span></span>

<span data-ttu-id="18ca0-1776">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1776">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1777">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1777">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1778">Info Field 2: Número da porta TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1778">Info Field 2: TCP port number</span></span>
- <span data-ttu-id="18ca0-1779">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1779">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1780">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1780">Info Field 4: Not used</span></span>

### <a name="tcp-socket-bytes-available"></a><span data-ttu-id="18ca0-1781">TCP Socket Bytes disponíveis</span><span class="sxs-lookup"><span data-stu-id="18ca0-1781">TCP Socket Bytes Available</span></span> 

#### <a name="nx_tcp_socket_bytes_available"></a><span data-ttu-id="18ca0-1782">nx_tcp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="18ca0-1782">nx_tcp_socket_bytes_available</span></span>

<span data-ttu-id="18ca0-1783">**Ícone** ![ T C P tomada bytes disponível ícone](./media/user-guide/netx-events/image135.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1783">**Icon** ![T C P socket bytes available icon](./media/user-guide/netx-events/image135.png)</span></span>

<span data-ttu-id="18ca0-1784">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1784">**Description**</span></span>

<span data-ttu-id="18ca0-1785">Este evento representa o número de bytes atualmente disponíveis na tomada de receção TCP especificada através de nx_tcp_socket_bytes_available.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1785">This event represents the number of bytes currently available on the specified TCP receiving socket via nx_tcp_socket_bytes_available.</span></span>

<span data-ttu-id="18ca0-1786">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1786">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1787">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1787">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1788">Info Field 2: Ponteiro para tomada TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1788">Info Field 2: Pointer to TCP socket</span></span>
- <span data-ttu-id="18ca0-1789">Info Field 3: Bytes recebidos na tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1789">Info Field 3: Bytes received on the socket</span></span>
- <span data-ttu-id="18ca0-1790">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1790">Info Field 4: Not used</span></span>

### <a name="tcp-socket-create"></a><span data-ttu-id="18ca0-1791">Criação de tomada TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1791">TCP Socket Create</span></span> 

#### <a name="nx_tcp_socket_create"></a><span data-ttu-id="18ca0-1792">nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="18ca0-1792">nx_tcp_socket_create</span></span>

<span data-ttu-id="18ca0-1793">**Ícone** ![ Tomada T C P criar ícone](./media/user-guide/netx-events/image136.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1793">**Icon** ![T C P socket create icon](./media/user-guide/netx-events/image136.png)</span></span>

<span data-ttu-id="18ca0-1794">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1794">**Description**</span></span>

<span data-ttu-id="18ca0-1795">Este evento representa a criação de uma tomada TCP através de nx_tcp_socket_create.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1795">This event represents creating a TCP socket via nx_tcp_socket_create.</span></span>

<span data-ttu-id="18ca0-1796">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1796">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1797">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1797">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1798">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1798">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1799">Info Field 3: Tipo de serviço</span><span class="sxs-lookup"><span data-stu-id="18ca0-1799">Info Field 3: Type of service</span></span>
- <span data-ttu-id="18ca0-1800">Info Field 4: Receber o tamanho da janela</span><span class="sxs-lookup"><span data-stu-id="18ca0-1800">Info Field 4: Receive window size</span></span>

### <a name="tcp-socket-delete"></a><span data-ttu-id="18ca0-1801">Apagar tomada TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1801">TCP Socket Delete</span></span> 

#### <a name="nx_tcp_socket_delete"></a><span data-ttu-id="18ca0-1802">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="18ca0-1802">nx_tcp_socket_delete</span></span>

<span data-ttu-id="18ca0-1803">**Ícone** ![ Ícone de eliminação da tomada T C P](./media/user-guide/netx-events/image137.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1803">**Icon** ![T C P socket delete icon](./media/user-guide/netx-events/image137.png)</span></span>

<span data-ttu-id="18ca0-1804">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1804">**Description**</span></span>

<span data-ttu-id="18ca0-1805">Este evento representa a eliminação de uma tomada através de nx_tcp_socket_delete.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1805">This event represents deleting a socket via nx_tcp_socket_delete.</span></span>

<span data-ttu-id="18ca0-1806">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1806">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1807">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1807">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1808">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1808">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1809">Info Field 3: Estado da tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1809">Info Field 3: Socket state</span></span>
- <span data-ttu-id="18ca0-1810">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1810">Info Field 4: Not used</span></span>

### <a name="tcp-socket-disconnect"></a><span data-ttu-id="18ca0-1811">Desconexão da tomada TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1811">TCP Socket Disconnect</span></span> 

#### <a name="nx_tcp_socket_disconnect"></a><span data-ttu-id="18ca0-1812">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="18ca0-1812">nx_tcp_socket_disconnect</span></span>

<span data-ttu-id="18ca0-1813">**Ícone** ![ Ícone de desconexão da tomada T C P](./media/user-guide/netx-events/image138.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1813">**Icon** ![T C P socket disconnect icon](./media/user-guide/netx-events/image138.png)</span></span>

<span data-ttu-id="18ca0-1814">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1814">**Description**</span></span>

<span data-ttu-id="18ca0-1815">Este evento representa desligar uma tomada através de nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1815">This event represents disconnecting a socket via nx_tcp_socket_disconnect.</span></span>

<span data-ttu-id="18ca0-1816">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1816">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1817">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1817">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1818">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1818">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1819">Info Field 3: Opção de espera</span><span class="sxs-lookup"><span data-stu-id="18ca0-1819">Info Field 3: Wait option</span></span>
- <span data-ttu-id="18ca0-1820">Info Field 4: Estado da tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1820">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-information-get"></a><span data-ttu-id="18ca0-1821">Informações da tomada TCP obtêm</span><span class="sxs-lookup"><span data-stu-id="18ca0-1821">TCP Socket Information Get</span></span> 

#### <a name="nx_tcp_socket_info_get"></a><span data-ttu-id="18ca0-1822">nx_tcp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="18ca0-1822">nx_tcp_socket_info_get</span></span>

<span data-ttu-id="18ca0-1823">**Ícone** ![ T C P informações de tomada obter ícone](./media/user-guide/netx-events/image139.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1823">**Icon** ![T C P socket information get icon](./media/user-guide/netx-events/image139.png)</span></span>

<span data-ttu-id="18ca0-1824">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1824">**Description**</span></span>

<span data-ttu-id="18ca0-1825">Este evento representa obter informações sobre uma tomada através de nx_tcp_socket_info_get.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1825">This event represents getting information about a socket via nx_tcp_socket_info_get.</span></span>

<span data-ttu-id="18ca0-1826">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1826">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1827">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1827">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1828">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1828">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1829">Info Field 3: Bytes enviados através desta tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1829">Info Field 3: Bytes sent through this socket</span></span>
- <span data-ttu-id="18ca0-1830">Info Field 4: Bytes recebidos através desta tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1830">Info Field 4: Bytes received through this socket</span></span>

### <a name="tcp-socket-mss-get"></a><span data-ttu-id="18ca0-1831">MSS de tomada TCP obter</span><span class="sxs-lookup"><span data-stu-id="18ca0-1831">TCP Socket MSS Get</span></span> 

#### <a name="nx_tcp_socket_mss_get"></a><span data-ttu-id="18ca0-1832">nx_tcp_socket_mss_get</span><span class="sxs-lookup"><span data-stu-id="18ca0-1832">nx_tcp_socket_mss_get</span></span>

<span data-ttu-id="18ca0-1833">**Ícone** ![ T C P socket M S S S obter ícone](./media/user-guide/netx-events/image140.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1833">**Icon** ![T C P socket M S S get icon](./media/user-guide/netx-events/image140.png)</span></span>

<span data-ttu-id="18ca0-1834">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1834">**Description**</span></span>

<span data-ttu-id="18ca0-1835">Este evento representa obter o MSS da tomada através de nx_tcp_socket_mss_get.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1835">This event represents getting the socket's MSS via nx_tcp_socket_mss_get.</span></span>

<span data-ttu-id="18ca0-1836">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1836">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1837">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1837">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1838">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1838">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1839">Info Field 3: Tamanho máximo do segmento (MSS)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1839">Info Field 3: Maximum Segment Size (MSS)</span></span>
- <span data-ttu-id="18ca0-1840">Info Field 4: Estado da tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1840">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-mss-peer-get"></a><span data-ttu-id="18ca0-1841">TCP Socket MSS Peer Get</span><span class="sxs-lookup"><span data-stu-id="18ca0-1841">TCP Socket MSS Peer Get</span></span> 

#### <a name="nx_tcp_socket_mss_peer_get"></a><span data-ttu-id="18ca0-1842">nx_tcp_socket_mss_peer_get</span><span class="sxs-lookup"><span data-stu-id="18ca0-1842">nx_tcp_socket_mss_peer_get</span></span>

<span data-ttu-id="18ca0-1843">**Ícone** ![ T C P socket M S S peer obter ícone](./media/user-guide/netx-events/image141.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1843">**Icon** ![T C P socket M S S peer get icon](./media/user-guide/netx-events/image141.png)</span></span>

<span data-ttu-id="18ca0-1844">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1844">**Description**</span></span>

<span data-ttu-id="18ca0-1845">Este evento representa obter o valor MSS do par da tomada através de nx_tcp_socket_mss_peer_get.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1845">This event represents getting the MSS value of the socket's peer via nx_tcp_socket_mss_peer_get.</span></span>

<span data-ttu-id="18ca0-1846">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1846">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1847">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1847">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1848">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1848">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1849">Info Field 3: Peer's MSS</span><span class="sxs-lookup"><span data-stu-id="18ca0-1849">Info Field 3: Peer's MSS</span></span>
- <span data-ttu-id="18ca0-1850">Info Field 4: Estado da tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1850">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-mss-set"></a><span data-ttu-id="18ca0-1851">Conjunto de MSS de tomada de TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1851">TCP Socket MSS Set</span></span> 

#### <a name="nx_tcp_socket_mss_set"></a><span data-ttu-id="18ca0-1852">nx_tcp_socket_mss_set</span><span class="sxs-lookup"><span data-stu-id="18ca0-1852">nx_tcp_socket_mss_set</span></span>

<span data-ttu-id="18ca0-1853">**Ícone** ![ T C P tomada M S conjunto ícone](./media/user-guide/netx-events/image142.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1853">**Icon** ![T C P socket M S S set icon](./media/user-guide/netx-events/image142.png)</span></span>

<span data-ttu-id="18ca0-1854">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1854">**Description**</span></span>

<span data-ttu-id="18ca0-1855">Este evento representa a definição do MSS de uma tomada através de nx_tcp_socket_mss_set.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1855">This event represents setting a socket's MSS via nx_tcp_socket_mss_set.</span></span>

<span data-ttu-id="18ca0-1856">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1856">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1857">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1857">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1858">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1858">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1859">Info Field 3: MSS</span><span class="sxs-lookup"><span data-stu-id="18ca0-1859">Info Field 3: MSS</span></span>
- <span data-ttu-id="18ca0-1860">Info Field 4: Estado da tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1860">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-peer-info-get"></a><span data-ttu-id="18ca0-1861">Informações de pares de tomadas TCP obtêm</span><span class="sxs-lookup"><span data-stu-id="18ca0-1861">TCP Socket Peer Info Get</span></span> 

#### <a name="nx_tcp_socket_peer_info_get"></a><span data-ttu-id="18ca0-1862">nx_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="18ca0-1862">nx_tcp_socket_peer_info_get</span></span>

<span data-ttu-id="18ca0-1863">**Ícone** ![ T C P tomada informação peer obter ícone](./media/user-guide/netx-events/image143.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1863">**Icon** ![T C P socket peer info get icon](./media/user-guide/netx-events/image143.png)</span></span>

<span data-ttu-id="18ca0-1864">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1864">**Description**</span></span>

<span data-ttu-id="18ca0-1865">Este evento representa informações obtidas da tomada TCP relativas ao endereço IP (por exemplo, >anfitrião de ligação) endereço IP e porta através de nx_tcp_socket_peer_info_get.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1865">This event represents information retrieved from the TCP socket regarding the peer (e.g. >connecting host) IP address and port via nx_tcp_socket_peer_info_get.</span></span>

<span data-ttu-id="18ca0-1866">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1866">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1867">Info Field 1: Ponteiro para tomada TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1867">Info Field 1: Pointer to TCP socket</span></span>
- <span data-ttu-id="18ca0-1868">Info Field 2: Endereço IP do peer</span><span class="sxs-lookup"><span data-stu-id="18ca0-1868">Info Field 2: Peer IP address</span></span>
- <span data-ttu-id="18ca0-1869">Info Field 3: Número da porta de pares</span><span class="sxs-lookup"><span data-stu-id="18ca0-1869">Info Field 3: Peer port number</span></span>
- <span data-ttu-id="18ca0-1870">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1870">Info Field 4: Not used</span></span>

### <a name="tcp-socket-receive"></a><span data-ttu-id="18ca0-1871">Tomada TCP Receber</span><span class="sxs-lookup"><span data-stu-id="18ca0-1871">TCP Socket Receive</span></span> 

#### <a name="nx_tcp_socket_receive"></a><span data-ttu-id="18ca0-1872">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="18ca0-1872">nx_tcp_socket_receive</span></span>

<span data-ttu-id="18ca0-1873">**Ícone** ![ T C P receber ícone](./media/user-guide/netx-events/image144.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1873">**Icon** ![T C P socket receive icon](./media/user-guide/netx-events/image144.png)</span></span>

<span data-ttu-id="18ca0-1874">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1874">**Description**</span></span>

<span data-ttu-id="18ca0-1875">Este evento representa a receção de dados de uma tomada via nx_tcp_socket_receive.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1875">This event represents receiving data from a socket via nx_tcp_socket_receive.</span></span>

<span data-ttu-id="18ca0-1876">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1876">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1877">Info Field 1: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1877">Info Field 1: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1878">Info Field 2: Ponteiro para receber pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-1878">Info Field 2: Pointer to received packet</span></span>
- <span data-ttu-id="18ca0-1879">Info Field 3: Comprimento do pacote recebido</span><span class="sxs-lookup"><span data-stu-id="18ca0-1879">Info Field 3: Received packet length</span></span>
- <span data-ttu-id="18ca0-1880">Info Field 4: Receber número de sequência</span><span class="sxs-lookup"><span data-stu-id="18ca0-1880">Info Field 4: Receive sequence number</span></span>

### <a name="tcp-socket-receive-notify"></a><span data-ttu-id="18ca0-1881">Notificação da tomada TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1881">TCP Socket Receive Notify</span></span> 

#### <a name="nx_tcp_socket_receive_notify"></a><span data-ttu-id="18ca0-1882">nx_tcp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="18ca0-1882">nx_tcp_socket_receive_notify</span></span>

<span data-ttu-id="18ca0-1883">**Ícone** ![ Tomada T C P receber ícone de notificação](./media/user-guide/netx-events/image145.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1883">**Icon** ![T C P socket receive notify icon](./media/user-guide/netx-events/image145.png)</span></span>

<span data-ttu-id="18ca0-1884">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1884">**Description**</span></span>

<span data-ttu-id="18ca0-1885">Este evento representa registar uma chamada de notificação de receção para uma tomada através de nx_tcp_socket_receive_notify.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1885">This event represents registering a receive notify callback for a socket via nx_tcp_socket_receive_notify.</span></span>

<span data-ttu-id="18ca0-1886">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1886">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1887">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1887">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1888">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1888">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1889">Info Field 3: Ponteiro para receber notificação info de retorno Campo 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1889">Info Field 3: Pointer to receive notify callback Info Field 4: Not used</span></span>

### <a name="tcp-socket-send"></a><span data-ttu-id="18ca0-1890">Enviar tomada TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1890">TCP Socket Send</span></span> 

#### <a name="nx_tcp_socket_send"></a><span data-ttu-id="18ca0-1891">nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="18ca0-1891">nx_tcp_socket_send</span></span>

<span data-ttu-id="18ca0-1892">**Ícone** ![ T C P tomada enviar ícone](./media/user-guide/netx-events/image146.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1892">**Icon** ![T C P socket send icon](./media/user-guide/netx-events/image146.png)</span></span>

<span data-ttu-id="18ca0-1893">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1893">**Description**</span></span>

<span data-ttu-id="18ca0-1894">Este evento representa o envio de dados numa tomada via nx_tcp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1894">This event represents sending data on a socket via nx_tcp_socket_send.</span></span>

<span data-ttu-id="18ca0-1895">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1895">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1896">Info Field 1: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1896">Info Field 1: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1897">Info Field 2: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-1897">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-1898">Info Field 3: Comprimento do pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-1898">Info Field 3: Length of packet</span></span>
- <span data-ttu-id="18ca0-1899">Info Field 4: Transmitir número de sequência</span><span class="sxs-lookup"><span data-stu-id="18ca0-1899">Info Field 4: Transmit sequence number</span></span>

### <a name="tcp-socket-state-wait"></a><span data-ttu-id="18ca0-1900">TCP Socket State Wait</span><span class="sxs-lookup"><span data-stu-id="18ca0-1900">TCP Socket State Wait</span></span> 

#### <a name="nx_tcp_socket_state_wait"></a><span data-ttu-id="18ca0-1901">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="18ca0-1901">nx_tcp_socket_state_wait</span></span>

<span data-ttu-id="18ca0-1902">**Ícone** ![ T C P estado de espera ícone](./media/user-guide/netx-events/image147.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1902">**Icon** ![T C P socket state wait icon](./media/user-guide/netx-events/image147.png)</span></span>

<span data-ttu-id="18ca0-1903">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1903">**Description**</span></span>

<span data-ttu-id="18ca0-1904">Este evento representa esperar que uma tomada entre num determinado estado através de nx_tcp_socket_state_wait.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1904">This event represents waiting for a socket to enter a particular state via nx_tcp_socket_state_wait.</span></span>

<span data-ttu-id="18ca0-1905">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1905">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1906">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1906">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1907">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1907">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1908">Info Field 3: Estado de tomada desejada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1908">Info Field 3: Desired socket state</span></span>
- <span data-ttu-id="18ca0-1909">Info Field 4: Estado anterior da tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1909">Info Field 4: Previous socket state</span></span>

### <a name="tcp-socket-transmit-configure"></a><span data-ttu-id="18ca0-1910">Configuração de transmissão de tomada TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1910">TCP Socket Transmit Configure</span></span> 

#### <a name="nx_tcp_socket_transmit_configure"></a><span data-ttu-id="18ca0-1911">nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="18ca0-1911">nx_tcp_socket_transmit_configure</span></span>

<span data-ttu-id="18ca0-1912">**Ícone** ![ T C P tomada transmitir ícone de configuração](./media/user-guide/netx-events/image148.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1912">**Icon** ![T C P socket transmit configure icon](./media/user-guide/netx-events/image148.png)</span></span>

<span data-ttu-id="18ca0-1913">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1913">**Description**</span></span>

<span data-ttu-id="18ca0-1914">Este evento representa a configuração das opções de transmissão de uma tomada através de nx_tcp_socket_transmit_configure.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1914">This event represents configuring the transmit options for a socket via nx_tcp_socket_transmit_configure.</span></span>

<span data-ttu-id="18ca0-1915">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1915">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1916">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1916">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1917">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1917">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1918">Info Field 3: Transmitir profundidade de fila</span><span class="sxs-lookup"><span data-stu-id="18ca0-1918">Info Field 3: Transmit queue depth</span></span>
- <span data-ttu-id="18ca0-1919">Info Field 4: Valor de tempo limite</span><span class="sxs-lookup"><span data-stu-id="18ca0-1919">Info Field 4: Timeout value</span></span>

### <a name="tcp-socket-window-update-notify-set"></a><span data-ttu-id="18ca0-1920">Atualização da janela da tomada TCP notificar conjunto</span><span class="sxs-lookup"><span data-stu-id="18ca0-1920">TCP Socket Window Update Notify Set</span></span> 

#### <a name="nx_tcp_window_update_notify_set"></a><span data-ttu-id="18ca0-1921">nx_tcp_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="18ca0-1921">nx_tcp_window_update_notify_set</span></span>

<span data-ttu-id="18ca0-1922">**Ícone** ![ Atualização da janela da tomada T C P notifica o ícone do conjunto](./media/user-guide/netx-events/image149.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1922">**Icon** ![T C P socket window update notify set icon](./media/user-guide/netx-events/image149.png)</span></span>

<span data-ttu-id="18ca0-1923">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1923">**Description**</span></span>

<span data-ttu-id="18ca0-1924">Este evento representa uma tomada TCP recebendo a notificação de um aumento na janela de receção do anfitrião remoto através de nx_tcp_window_update_notify_set.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1924">This event represents a TCP socket receiving notification of an increase in the remote host receive window via nx_tcp_window_update_notify_set.</span></span>

<span data-ttu-id="18ca0-1925">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1925">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1926">Info Field 1: Ponteiro para tomada TCP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1926">Info Field 1: Pointer to TCP socket</span></span>
- <span data-ttu-id="18ca0-1927">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1927">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-1928">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1928">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1929">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1929">Info Field 4: Not used</span></span>

### <a name="udp-enable"></a><span data-ttu-id="18ca0-1930">Ativação uDP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1930">UDP Enable</span></span> 

#### <a name="nx_udp_enable"></a><span data-ttu-id="18ca0-1931">nx_udp_enable</span><span class="sxs-lookup"><span data-stu-id="18ca0-1931">nx_udp_enable</span></span>

<span data-ttu-id="18ca0-1932">**Ícone** ![ U D P ativar ícone](./media/user-guide/netx-events/image150.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1932">**Icon** ![U D P enable icon](./media/user-guide/netx-events/image150.png)</span></span>

<span data-ttu-id="18ca0-1933">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1933">**Description**</span></span>

<span data-ttu-id="18ca0-1934">Este evento representa permitir a UDP através de nx_udp_enable.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1934">This event represents enabling UDP via nx_udp_enable.</span></span>

<span data-ttu-id="18ca0-1935">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1935">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1936">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1936">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1937">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1937">Info Field 2: Not used</span></span>
- <span data-ttu-id="18ca0-1938">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1938">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1939">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1939">Info Field 4: Not used</span></span>

### <a name="udp-free-port-find"></a><span data-ttu-id="18ca0-1940">Descoberta de porto livre da UDP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1940">UDP Free Port Find</span></span> 

#### <a name="nx_udp_free_port_find"></a><span data-ttu-id="18ca0-1941">nx_udp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="18ca0-1941">nx_udp_free_port_find</span></span>

<span data-ttu-id="18ca0-1942">**Ícone** ![ U D P porta livre encontrar ícone](./media/user-guide/netx-events/image151.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1942">**Icon** ![U D P free port find icon](./media/user-guide/netx-events/image151.png)</span></span>

<span data-ttu-id="18ca0-1943">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1943">**Description**</span></span>

<span data-ttu-id="18ca0-1944">Este evento representa encontrar uma porta UDP gratuita através de nx_udp_free_port_find.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1944">This event represents finding a free UDP port via nx_udp_free_port_find.</span></span>

<span data-ttu-id="18ca0-1945">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1945">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1946">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1946">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1947">Info Field 2: Iniciar portas para pesquisar a partir de</span><span class="sxs-lookup"><span data-stu-id="18ca0-1947">Info Field 2: Starting port to search from</span></span>
- <span data-ttu-id="18ca0-1948">Info Field 3: Porta gratuita</span><span class="sxs-lookup"><span data-stu-id="18ca0-1948">Info Field 3: Free port</span></span>
- <span data-ttu-id="18ca0-1949">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1949">Info Field 4: Not used</span></span>

### <a name="udp-information-get"></a><span data-ttu-id="18ca0-1950">Informações da UDP Obtêm</span><span class="sxs-lookup"><span data-stu-id="18ca0-1950">UDP Information Get</span></span> 

#### <a name="nx_udp_info_get"></a><span data-ttu-id="18ca0-1951">nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="18ca0-1951">nx_udp_info_get</span></span>

<span data-ttu-id="18ca0-1952">**Ícone** ![ U D P informações obter ícone](./media/user-guide/netx-events/image152.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1952">**Icon** ![U D P information get icon](./media/user-guide/netx-events/image152.png)</span></span>

<span data-ttu-id="18ca0-1953">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1953">**Description**</span></span>

<span data-ttu-id="18ca0-1954">Este evento representa a obtenção de informação através de nx_udp_info_get.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1954">This event represents getting information via nx_udp_info_get.</span></span>

<span data-ttu-id="18ca0-1955">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1955">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1956">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1956">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1957">Info Field 2: Bytes UDP enviados</span><span class="sxs-lookup"><span data-stu-id="18ca0-1957">Info Field 2: UDP bytes sent</span></span>
- <span data-ttu-id="18ca0-1958">Info Field 3: Bytes UDP recebidos</span><span class="sxs-lookup"><span data-stu-id="18ca0-1958">Info Field 3: UDP bytes received</span></span>
- <span data-ttu-id="18ca0-1959">Info Field 4: Pacotes inválidos</span><span class="sxs-lookup"><span data-stu-id="18ca0-1959">Info Field 4: Invalid packets</span></span>

### <a name="udp-socket-bind"></a><span data-ttu-id="18ca0-1960">Ligação de tomada uDP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1960">UDP Socket Bind</span></span> 

#### <a name="nx_udp_socket_bind"></a><span data-ttu-id="18ca0-1961">nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="18ca0-1961">nx_udp_socket_bind</span></span>

<span data-ttu-id="18ca0-1962">**Ícone** ![ Ícone de ligação da tomada de U D P](./media/user-guide/netx-events/image153.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1962">**Icon** ![U D P socket bind icon](./media/user-guide/netx-events/image153.png)</span></span>

<span data-ttu-id="18ca0-1963">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1963">**Description**</span></span>

<span data-ttu-id="18ca0-1964">Este evento representa a ligação de uma tomada UDP a uma porta através de nx_udp_socket_bind.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1964">This event represents binding a UDP socket to a port via nx_udp_socket_bind.</span></span>

<span data-ttu-id="18ca0-1965">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1965">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1966">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1966">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1967">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1967">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1968">Info Campo 3: Número de porta</span><span class="sxs-lookup"><span data-stu-id="18ca0-1968">Info Field 3: Port number</span></span>
- <span data-ttu-id="18ca0-1969">Info Field 4: Opção de espera</span><span class="sxs-lookup"><span data-stu-id="18ca0-1969">Info Field 4: Wait option</span></span>

### <a name="udp-socket-bytes-available"></a><span data-ttu-id="18ca0-1970">Bytes de tomada uDP disponíveis</span><span class="sxs-lookup"><span data-stu-id="18ca0-1970">UDP Socket Bytes Available</span></span> 

#### <a name="nx_udp_socket_bytes_available"></a><span data-ttu-id="18ca0-1971">nx_udp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="18ca0-1971">nx_udp_socket_bytes_available</span></span>

<span data-ttu-id="18ca0-1972">**Ícone** ![ U D P tomada bytes disponíveis ícone](./media/user-guide/netx-events/image154.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1972">**Icon** ![U D P socket bytes available icon](./media/user-guide/netx-events/image154.png)</span></span>

<span data-ttu-id="18ca0-1973">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1973">**Description**</span></span>

<span data-ttu-id="18ca0-1974">Este evento representa o número atual de bytes recebidos na tomada UDP via nx_udp_socket_bytes_available.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1974">This event represents the current number of bytes received on the UDP socket via nx_udp_socket_bytes_available.</span></span>

<span data-ttu-id="18ca0-1975">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1975">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1976">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1976">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1977">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1977">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1978">Info Field 3: Bytes recebidos na tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1978">Info Field 3: Bytes received on socket</span></span>
- <span data-ttu-id="18ca0-1979">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1979">Info Field 4: Not used</span></span>

### <a name="udp-socket-checksum-disable"></a><span data-ttu-id="18ca0-1980">Desativação do checkum da tomada UDP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1980">UDP Socket Checksum Disable</span></span> 

#### <a name="nx_udp_socket_checksum_disable"></a><span data-ttu-id="18ca0-1981">nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="18ca0-1981">nx_udp_socket_checksum_disable</span></span>

<span data-ttu-id="18ca0-1982">**Ícone** ![ Ícone de desativação da tomada de U D P](./media/user-guide/netx-events/image155.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1982">**Icon** ![U D P socket checksum disable icon](./media/user-guide/netx-events/image155.png)</span></span>

<span data-ttu-id="18ca0-1983">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1983">**Description**</span></span>

<span data-ttu-id="18ca0-1984">Este evento representa a desativação da data de verificação de dados numa tomada UDP através de nx_udp_socket_checksum_disable.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1984">This event represents disabling the checksum for data on a UDP socket via nx_udp_socket_checksum_disable.</span></span>

<span data-ttu-id="18ca0-1985">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1985">**Information Fields**</span></span> 

- <span data-ttu-id="18ca0-1986">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1986">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1987">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1987">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1988">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1988">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1989">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1989">Info Field 4: Not used</span></span>

### <a name="udp-socket-checksum-enable"></a><span data-ttu-id="18ca0-1990">Ativação do checkum de verificação da tomada UDP</span><span class="sxs-lookup"><span data-stu-id="18ca0-1990">UDP Socket Checksum Enable</span></span> 

#### <a name="nx_udp_socket_checksum_enable"></a><span data-ttu-id="18ca0-1991">nx_udp_socket_checksum_enable</span><span class="sxs-lookup"><span data-stu-id="18ca0-1991">nx_udp_socket_checksum_enable</span></span>

<span data-ttu-id="18ca0-1992">**Ícone** ![ U D P socket checkum enable icon](./media/user-guide/netx-events/image156.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-1992">**Icon** ![U D P socket checksum enable icon](./media/user-guide/netx-events/image156.png)</span></span>

<span data-ttu-id="18ca0-1993">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1993">**Description**</span></span>

<span data-ttu-id="18ca0-1994">Este evento representa permitir o processamento de checkum numa tomada através de nx_udp_socket_checksum_enable.</span><span class="sxs-lookup"><span data-stu-id="18ca0-1994">This event represents enabling checksum processing on a socket via nx_udp_socket_checksum_enable.</span></span>

<span data-ttu-id="18ca0-1995">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-1995">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-1996">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-1996">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-1997">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-1997">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-1998">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1998">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-1999">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-1999">Info Field 4: Not used</span></span>

### <a name="udp-socket-create"></a><span data-ttu-id="18ca0-2000">Criação de tomada uDP</span><span class="sxs-lookup"><span data-stu-id="18ca0-2000">UDP Socket Create</span></span> 

#### <a name="nx_udp_socket_create"></a><span data-ttu-id="18ca0-2001">nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="18ca0-2001">nx_udp_socket_create</span></span>

<span data-ttu-id="18ca0-2002">**Ícone** ![ Tomada U D P criar ícone](./media/user-guide/netx-events/image157.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-2002">**Icon** ![U D P socket create icon](./media/user-guide/netx-events/image157.png)</span></span>

<span data-ttu-id="18ca0-2003">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-2003">**Description**</span></span>

<span data-ttu-id="18ca0-2004">Este evento representa a criação de uma tomada UDP através de nx_udp_socket_create.</span><span class="sxs-lookup"><span data-stu-id="18ca0-2004">This event represents creating a UDP socket via nx_udp_socket_create.</span></span>

<span data-ttu-id="18ca0-2005">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-2005">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-2006">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-2006">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-2007">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-2007">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-2008">Info Field 3: Tipo de serviço</span><span class="sxs-lookup"><span data-stu-id="18ca0-2008">Info Field 3: Type of service</span></span>
- <span data-ttu-id="18ca0-2009">Info Field 4: Fila máxima de receção</span><span class="sxs-lookup"><span data-stu-id="18ca0-2009">Info Field 4: Maximum receive queue</span></span>

### <a name="udp-socket-delete-event"></a><span data-ttu-id="18ca0-2010">Evento de eliminação de tomadas UDP</span><span class="sxs-lookup"><span data-stu-id="18ca0-2010">UDP Socket Delete Event</span></span> 

#### <a name="nx_udp_socket_delete-event"></a><span data-ttu-id="18ca0-2011">evento nx_udp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="18ca0-2011">nx_udp_socket_delete event</span></span>

<span data-ttu-id="18ca0-2012">**Ícone** ![ Tomada U D P apagar ícone do evento](./media/user-guide/netx-events/image158.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-2012">**Icon** ![U D P socket delete event icon](./media/user-guide/netx-events/image158.png)</span></span>

<span data-ttu-id="18ca0-2013">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-2013">**Description**</span></span>

<span data-ttu-id="18ca0-2014">Este evento representa a eliminação de uma tomada UDP através de nx_udp_socket_delete.</span><span class="sxs-lookup"><span data-stu-id="18ca0-2014">This event represents deleting a UDP socket via nx_udp_socket_delete.</span></span>

<span data-ttu-id="18ca0-2015">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-2015">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-2016">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-2016">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-2017">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-2017">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-2018">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-2018">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-2019">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-2019">Info Field 4: Not used</span></span>

### <a name="udp-socket-information-get-event"></a><span data-ttu-id="18ca0-2020">Informações da Tomada de UDP Obtêm Evento</span><span class="sxs-lookup"><span data-stu-id="18ca0-2020">UDP Socket Information Get Event</span></span> 

#### <a name="nx_udp_socket_info_get-event"></a><span data-ttu-id="18ca0-2021">evento nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="18ca0-2021">nx_udp_socket_info_get event</span></span>

<span data-ttu-id="18ca0-2022">**Ícone** ![ Informações de tomada U D P obtenham ícone de evento](./media/user-guide/netx-events/image159.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-2022">**Icon** ![U D P socket information get event icon](./media/user-guide/netx-events/image159.png)</span></span>

<span data-ttu-id="18ca0-2023">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-2023">**Description**</span></span>

<span data-ttu-id="18ca0-2024">Este evento representa obter informações sobre uma tomada UDP através de nx_udp_socket_info_get.</span><span class="sxs-lookup"><span data-stu-id="18ca0-2024">This event represents getting information about a UDP socket via nx_udp_socket_info_get.</span></span>

<span data-ttu-id="18ca0-2025">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-2025">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-2026">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-2026">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-2027">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-2027">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-2028">Info Field 3: Bytes enviados através da tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-2028">Info Field 3: Bytes sent through socket</span></span>
- <span data-ttu-id="18ca0-2029">Info Field 4: Bytes recebidos através da tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-2029">Info Field 4: Bytes received through socket</span></span>

### <a name="udp-socket-interface-set"></a><span data-ttu-id="18ca0-2030">Conjunto de interface de tomada de UDP</span><span class="sxs-lookup"><span data-stu-id="18ca0-2030">UDP Socket Interface Set</span></span> 

#### <a name="nx_udp_socket_interface_set-event"></a><span data-ttu-id="18ca0-2031">evento nx_udp_socket_interface_set</span><span class="sxs-lookup"><span data-stu-id="18ca0-2031">nx_udp_socket_interface_set event</span></span>

<span data-ttu-id="18ca0-2032">**Ícone** ![ Ícone de conjunto de conjunto de interface de tomada de U D P](./media/user-guide/netx-events/image160.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-2032">**Icon** ![U D P socket interface set icon](./media/user-guide/netx-events/image160.png)</span></span>

<span data-ttu-id="18ca0-2033">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-2033">**Description**</span></span>

<span data-ttu-id="18ca0-2034">Este evento representa a definição da interface de saída da tomada UDP especificada com a interface especificada através nx_udp_socket_interface_set.</span><span class="sxs-lookup"><span data-stu-id="18ca0-2034">This event represents setting the outgoing interface of the specified UDP socket with the specified interface via nx_udp_socket_interface_set.</span></span>

<span data-ttu-id="18ca0-2035">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-2035">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-2036">Info Field 1: Ponteiro para tomada UDP</span><span class="sxs-lookup"><span data-stu-id="18ca0-2036">Info Field 1: Pointer to UDP socket</span></span>
- <span data-ttu-id="18ca0-2037">Info Field 2: Índice correspondente à interface para a tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-2037">Info Field 2: Index corresponding to the interface for the socket</span></span>
- <span data-ttu-id="18ca0-2038">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-2038">Info Field 3: Not used</span></span>
- <span data-ttu-id="18ca0-2039">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-2039">Info Field 4: Not used</span></span>

### <a name="udp-socket-port-get"></a><span data-ttu-id="18ca0-2040">Porta de tomada uDP obter</span><span class="sxs-lookup"><span data-stu-id="18ca0-2040">UDP Socket Port Get</span></span> 

#### <a name="nx_udp_socket_port_get"></a><span data-ttu-id="18ca0-2041">nx_udp_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="18ca0-2041">nx_udp_socket_port_get</span></span>

<span data-ttu-id="18ca0-2042">**Ícone** ![ Porta de tomada U D P obter ícone](./media/user-guide/netx-events/image161.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-2042">**Icon** ![U D P socket port get icon](./media/user-guide/netx-events/image161.png)</span></span>

<span data-ttu-id="18ca0-2043">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-2043">**Description**</span></span>

<span data-ttu-id="18ca0-2044">Este evento representa a recuperação da porta UDP a tomada UDP especificada é obrigada a através de nx_udp_socket_port_get.</span><span class="sxs-lookup"><span data-stu-id="18ca0-2044">This event represents retrieving the UDP port the specified UDP socket is bound to via nx_udp_socket_port_get.</span></span>

<span data-ttu-id="18ca0-2045">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-2045">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-2046">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-2046">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-2047">Info Field 2: Ponteiro para tomada UDP</span><span class="sxs-lookup"><span data-stu-id="18ca0-2047">Info Field 2: Pointer to UDP socket</span></span>
- <span data-ttu-id="18ca0-2048">Info Campo 3: Número de porta</span><span class="sxs-lookup"><span data-stu-id="18ca0-2048">Info Field 3: Port number</span></span>
- <span data-ttu-id="18ca0-2049">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-2049">Info Field 4: Not used</span></span>

### <a name="udp-socket-receive"></a><span data-ttu-id="18ca0-2050">Receber tomada UDP</span><span class="sxs-lookup"><span data-stu-id="18ca0-2050">UDP Socket Receive</span></span> 

#### <a name="nx_udp_socket_receive"></a><span data-ttu-id="18ca0-2051">nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="18ca0-2051">nx_udp_socket_receive</span></span>

<span data-ttu-id="18ca0-2052">**Ícone** ![ Tomada U D P receber ícone](./media/user-guide/netx-events/image162.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-2052">**Icon** ![U D P socket receive icon](./media/user-guide/netx-events/image162.png)</span></span>

<span data-ttu-id="18ca0-2053">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-2053">**Description**</span></span>

<span data-ttu-id="18ca0-2054">Este evento representa a receção de dados sobre a tomada de UDP especificada através de nx_udp_socket_receive.</span><span class="sxs-lookup"><span data-stu-id="18ca0-2054">This event represents receiving data on the specified UDP socket via nx_udp_socket_receive.</span></span>

<span data-ttu-id="18ca0-2055">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-2055">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-2056">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-2056">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-2057">Info Field 2: Ponteiro para tomada UDP</span><span class="sxs-lookup"><span data-stu-id="18ca0-2057">Info Field 2: Pointer to UDP socket</span></span>
- <span data-ttu-id="18ca0-2058">Info Field 3: Ponteiro para receber pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-2058">Info Field 3: Pointer to received packet</span></span>
- <span data-ttu-id="18ca0-2059">Info Field 4: Tamanho do pacote recebido</span><span class="sxs-lookup"><span data-stu-id="18ca0-2059">Info Field 4: Received packet size</span></span>

### <a name="udp-socket-receive-notify"></a><span data-ttu-id="18ca0-2060">Notificação de tomada de UDP</span><span class="sxs-lookup"><span data-stu-id="18ca0-2060">UDP Socket Receive Notify</span></span> 

#### <a name="nx_udp_socket_receive_notify"></a><span data-ttu-id="18ca0-2061">nx_udp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="18ca0-2061">nx_udp_socket_receive_notify</span></span>

<span data-ttu-id="18ca0-2062">**Ícone** ![ Tomada U D P receber notificação ](./media/user-guide/netx-events/image163.png) ícone **descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-2062">**Icon** ![U D P socket receive notify icon](./media/user-guide/netx-events/image163.png)s **Description**</span></span>

<span data-ttu-id="18ca0-2063">Este evento representa registar uma chamada de notificação de receção através de nx_udp_socket_receive_notify.</span><span class="sxs-lookup"><span data-stu-id="18ca0-2063">This event represents registering a receive notify callback via nx_udp_socket_receive_notify.</span></span>

<span data-ttu-id="18ca0-2064">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-2064">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-2065">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-2065">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-2066">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-2066">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-2067">Info Field 3: Ponteiro para receber notificação função Info Campo 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-2067">Info Field 3: Pointer to receive notify function Info Field 4: Not used</span></span>

### <a name="udp-socket-send"></a><span data-ttu-id="18ca0-2068">Tomada UDP Enviar</span><span class="sxs-lookup"><span data-stu-id="18ca0-2068">UDP Socket Send</span></span> 

#### <a name="nx_udp_socket_send"></a><span data-ttu-id="18ca0-2069">nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="18ca0-2069">nx_udp_socket_send</span></span>

<span data-ttu-id="18ca0-2070">**Ícone** ![ Tomada U D P enviar ícone](./media/user-guide/netx-events/image164.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-2070">**Icon** ![U D P socket send icon](./media/user-guide/netx-events/image164.png)</span></span>

<span data-ttu-id="18ca0-2071">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-2071">**Description**</span></span>

<span data-ttu-id="18ca0-2072">Este evento representa o envio de dados através de uma tomada UDP através de nx_udp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="18ca0-2072">This event represents sending data through a UDP socket via nx_udp_socket_send.</span></span>

<span data-ttu-id="18ca0-2073">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-2073">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-2074">Info Field 1: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-2074">Info Field 1: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-2075">Info Field 2: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-2075">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-2076">Info Field 3: Comprimento do pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-2076">Info Field 3: Packet length</span></span>
- <span data-ttu-id="18ca0-2077">Info Field 4: Endereço IP de destino</span><span class="sxs-lookup"><span data-stu-id="18ca0-2077">Info Field 4: Destination IP address</span></span>

### <a name="udp-socket-unbind"></a><span data-ttu-id="18ca0-2078">Tomada UDP Unbind</span><span class="sxs-lookup"><span data-stu-id="18ca0-2078">UDP Socket Unbind</span></span> 

#### <a name="nx_udp_socket_unbind"></a><span data-ttu-id="18ca0-2079">nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="18ca0-2079">nx_udp_socket_unbind</span></span>

<span data-ttu-id="18ca0-2080">**Ícone** ![ Ícone unbind da tomada de U D P](./media/user-guide/netx-events/image165.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-2080">**Icon** ![U D P socket unbind icon](./media/user-guide/netx-events/image165.png)</span></span>

<span data-ttu-id="18ca0-2081">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-2081">**Description**</span></span>

<span data-ttu-id="18ca0-2082">Este evento representa a desvinão de uma porta UDP com uma tomada via nx_udp_socket_unbind.</span><span class="sxs-lookup"><span data-stu-id="18ca0-2082">This event represents unbinding a UDP port with a socket via nx_udp_socket_unbind.</span></span>

<span data-ttu-id="18ca0-2083">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-2083">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-2084">Info Field 1: Pointer to IP instance</span><span class="sxs-lookup"><span data-stu-id="18ca0-2084">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="18ca0-2085">Info Field 2: Ponteiro para tomada</span><span class="sxs-lookup"><span data-stu-id="18ca0-2085">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="18ca0-2086">Info Campo 3: Número de porta</span><span class="sxs-lookup"><span data-stu-id="18ca0-2086">Info Field 3: Port number</span></span>
- <span data-ttu-id="18ca0-2087">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-2087">Info Field 4: Not used</span></span>

### <a name="udp-source-extract"></a><span data-ttu-id="18ca0-2088">Extrato de origem UDP</span><span class="sxs-lookup"><span data-stu-id="18ca0-2088">UDP Source Extract</span></span> 

#### <a name="nx_udp_socket_create"></a><span data-ttu-id="18ca0-2089">nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="18ca0-2089">nx_udp_socket_create</span></span>

<span data-ttu-id="18ca0-2090">**Ícone** ![ Ícone de extrato de fonte de U D P](./media/user-guide/netx-events/image166.png)</span><span class="sxs-lookup"><span data-stu-id="18ca0-2090">**Icon** ![U D P source extract icon](./media/user-guide/netx-events/image166.png)</span></span>

<span data-ttu-id="18ca0-2091">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="18ca0-2091">**Description**</span></span>

<span data-ttu-id="18ca0-2092">Este evento representa obter o endereço IP e o número de porta de um pacote UDP recebido através de nx_udp_source_extract.</span><span class="sxs-lookup"><span data-stu-id="18ca0-2092">This event represents getting the IP address and port number of a received UDP packet via nx_udp_source_extract.</span></span>

<span data-ttu-id="18ca0-2093">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="18ca0-2093">**Information Fields**</span></span>

- <span data-ttu-id="18ca0-2094">Info Field 1: Ponteiro para pacote</span><span class="sxs-lookup"><span data-stu-id="18ca0-2094">Info Field 1: Pointer to packet</span></span>
- <span data-ttu-id="18ca0-2095">Info Field 2: Endereço IP do Remetente</span><span class="sxs-lookup"><span data-stu-id="18ca0-2095">Info Field 2: Sender's IP address</span></span>
- <span data-ttu-id="18ca0-2096">Info Field 3: Número da porta do remetente</span><span class="sxs-lookup"><span data-stu-id="18ca0-2096">Info Field 3: Sender's port number</span></span>
- <span data-ttu-id="18ca0-2097">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="18ca0-2097">Info Field 4: Not used</span></span>