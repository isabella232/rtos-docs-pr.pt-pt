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
# <a name="chapter-8---azure-rtos-netx-trace-events"></a>Capítulo 8 - Azure RTOS NetX trace eventos

Este capítulo contém uma descrição dos eventos Azure RTOS NetX. 

## <a name="list-of-events-and-icons"></a>Lista de eventos e ícones

Segue-se uma lista de eventos NetX apresentados pela TraceX.

| Ícone                                           | Significado                 |
| -------------------------------- | ------------------------------------- |
| ![Ícone de receção de pedido de R P interno](./media/user-guide/netx-events/image1.png)    | Pedido interno de ARP Receber |
| ![Interna A R P Pedido Enviar ícone](./media/user-guide/netx-events/image2.png)    | Pedido interno de ARP Enviar |
| ![Ícone de receção de resposta R P interna](./media/user-guide/netx-events/image3.png)    | Resposta Interna da ARP Receber |
| ![Ícone de resposta R P interna](./media/user-guide/netx-events/image4.png)    | Envio de resposta interna da ARP |
| ![Ícone de receção interna I C M P](./media/user-guide/netx-events/image5.png)    | ICMP Interno Receber |
| ![I C M P Interno Enviar ícone](./media/user-guide/netx-events/image6.png)    | Envio interno do ICMP |
| ![NetX Interno I G M P Receber ícone](./media/user-guide/netx-events/image7.png)    | Receber Internamente netx IGMP |
| ![I P Interno Receber ícone](./media/user-guide/netx-events/image8.png)    | Ip Interno Receber |
| ![I P Interno Enviar ícone](./media/user-guide/netx-events/image9.png)    | Envio ip interno |
| ![Ícone de receção de dados internos de T C P](./media/user-guide/netx-events/image10.png)    | Dados internos da TCP recebem |
| ![Dados internos T C P Enviar ícone](./media/user-guide/netx-events/image11.png)    | Envio de dados internos da TCP |
| ![Ícone de receção de T C P Interna](./media/user-guide/netx-events/image12.png)    | TCP FIN Interno Receber |
| ![Interior T C P F I N Enviar ícone](./media/user-guide/netx-events/image13.png)    | TCP FIN Interno Enviar |
| ![Ícone de receção interna T C P R S T](./media/user-guide/netx-events/image14.png)    | Receção Interna de TCP RST |
| ![Ícone de envio interno T C P P S T](./media/user-guide/netx-events/image15.png)    | Envio interno de TCP RST |
| ![Ícone de receção interna T C P S Y N](./media/user-guide/netx-events/image16.png)    | Receção interna do TCP SYN |
| ![Ícone interno T C P S Y N Enviar](./media/user-guide/netx-events/image17.png)    | Envio interno de TCP SYN |
| ![Ícone de receção interna de U D P](./media/user-guide/netx-events/image18.png)    | UDP Interna Receber |
| ![U D P Interno Enviar ícone](./media/user-guide/netx-events/image19.png)    | Envio interno da UDP |
| ![Ícone de receção R A R P interno](./media/user-guide/netx-events/image20.png)    | Receção interna da RARP |
| ![R A R P Interno Enviar ícone](./media/user-guide/netx-events/image21.png)    | Envio interno da RARP |
| ![Ícone interno de retografia T C P](./media/user-guide/netx-events/image22.png)    | Redatry TCP interno |
| ![Ícone interno de mudança de estado T C P](./media/user-guide/netx-events/image23.png)    | Mudança interna do estado da TCP |
| ![Pacote de envio de motorista interno I / O](./media/user-guide/netx-events/image24.png)    | Pacote de motorista interno enviar |
| ![ícone](./media/user-guide/netx-events/image25.png)    | Inicialização interna do controlador de I/O |
| ![Ícone de inicialização do condutor interno I / O](./media/user-guide/netx-events/image26.png)    | Ligação interna do controlador de I/O |
| ![Ícone de desativação do controlador interno I / O](./media/user-guide/netx-events/image27.png)    | Ligação interna do controlador de I/O Desativada |
| ![Ícone de transmissão de pacote de motorista interno I / O](./media/user-guide/netx-events/image28.png)    | Transmissão interna do pacote de motorista de I/O |
| ![Ícone de envio de ARP do condutor interno I / O](./media/user-guide/netx-events/image29.png)    | Envio interno de ARP do condutor de I/O |
| ![I / O Driver ARP Response Enviar ícone](./media/user-guide/netx-events/image30.png)    | Envio de resposta ARP do controlador interno de I/O |
| ![Ícone interno I / O Driver RARP Enviar ícone](./media/user-guide/netx-events/image31.png)    | Envio interno de I/O do condutor RARP |
| ![Ícone de união de controlador interno I / O Motorista](./media/user-guide/netx-events/image32.png)    | União Multicast do controlador de I/O interna |
| ![Ícone de licença de controlador interno I / O](./media/user-guide/netx-events/image33.png)    | Licença multicast do controlador interno de I/O |
| ![Ícone de estado do motorista interno I / O](./media/user-guide/netx-events/image34.png)    | O controlador interno de I/O obtém o estado |
| ![Ícone interno I / O Driver Get Speed](./media/user-guide/netx-events/image35.png)    | Condutor interno de I/O obtém velocidade |
| ![I / O Motorista Interno Obter ícone do tipo Duplex](./media/user-guide/netx-events/image36.png)    | Controlador interno de I/O obter tipo duplex |
| ![Ícone interno de I / O Driver Get Error Count](./media/user-guide/netx-events/image37.png)    | Controlador interno de I/O obtenha contagem de erros |
| ![I / O Condutor Interno Obter ícone de Contagem RX](./media/user-guide/netx-events/image38.png)    | Motorista interno de I/O obtém conta de RX |
| ![I / O Condutor Interno Obter ícone de contagem de TX](./media/user-guide/netx-events/image39.png)    | Condutor interno de I/O obtém contagem de TX |
| ![Ícone de erros de atribuição de I/O Internos](./media/user-guide/netx-events/image40.png)    | Condutor interno de I/O obtém erros de atribuição |
| ![Ícone interno I / O Driver Un-initialize](./media/user-guide/netx-events/image41.png)    | Condutor interno de I/O Des-initialize |
| ![Ícone de processamento diferido interno I / O Driver](./media/user-guide/netx-events/image42.png)    | Processamento diferido interno do controlador de I/O |
| ![Um ícone invalidado de entradas dinâmicas R P](./media/user-guide/netx-events/image43.png)    | **Entradas dinâmicas ARP Invalidam** *-nx_arp_dynamic_entries_invalidate)* |
| ![Um ícone de conjunto de entrada dinâmica R P](./media/user-guide/netx-events/image44.png)    | **Conjunto de entrada dinâmica ARP** *(nx_arp_dynamic_entry_set)* |
| ![Um ícone de ativação R P](./media/user-guide/netx-events/image45.png)    | **ARP Enable** *(nx_arp_enable)* |
| ![Um ícone de envio gratuito R P](./media/user-guide/netx-events/image46.png)    | **ARP Envio Gratuito** (*nx_arp_gratuitous_send)* |
| ![Um ícone de endereço de hardware R P](./media/user-guide/netx-events/image47.png)    | **ARP Hardware Address Find** *(nx_arp_hardware_address_find)* |
| ![Um ícone de informação R P Obtenha](./media/user-guide/netx-events/image48.png)    | **Informação ARP Get** *(nx_arp_info_get)* |
| ![Um ícone de endereço IP R P](./media/user-guide/netx-events/image49.png)    | **ARP IP Address Find** *(nx_arp_ip_address_find)* |
| ![Um ícone de entrada estática R P](./media/user-guide/netx-events/image50.png)    | **Criação de entrada estática ARP** *(nx_arp_static_entry_create)* |
| ![Um ícone de entradas estáticas R P Delete](./media/user-guide/netx-events/image51.png)    | **ARP Estática Entradas Eliminar** *(nx_arp_static_entries_delete)* |
| ![Um ícone de exclusão de entrada estática R P](./media/user-guide/netx-events/image52.png)    | **Eliminação da entrada estática ARP** *(nx_arp_static_entry_delete)* |
| ![Ícone de eliminação de entrada de cache de duo](./media/user-guide/netx-events/image53.png)    | **Exclusão de entrada de cache duo** *(nxd_nd_cache_entry_delete)* |
| ![Ícone do conjunto de conjunto de entrada de cache duo](./media/user-guide/netx-events/image54.png)    | **Conjunto de entrada de cache duo** *(nxd_nd_cache_entry_set)* |
| ![Ícone invalidado duo cache](./media/user-guide/netx-events/image55.png)    | **Duo Cache Invalidado** *(nxd_nd_cache_invalidate)* |
| ![Duo Cache I Endereço P Encontrar ícone](./media/user-guide/netx-events/image56.png)    | **Duo Cache IP Address Find** *(nxd_nd_cache_ip_address_find)* |
| ![Duo I C M P Enable ícone](./media/user-guide/netx-events/image57.png)    | **Ativação duo ICMP** *(nxd_icmp_enable)* |
| ![Duo I C M P I P v 6 Ping ícone](./media/user-guide/netx-events/image58.png)    | **Duo ICMP IPv6 Ping** *(nxd_icmp_ping)* |
| ![Duo I P Max Tamanho de Carga Útil Encontrar ícone](./media/user-guide/netx-events/image59.png)    | **Duo IP Max Payload Size Find** *(nx_max_payload_size_find)* |
| ![Duo I P Pacote Cru Enviar ícone](./media/user-guide/netx-events/image60.png)    | **Duo IP Raw Packet Send** *(nxd_ip_raw_packet_send)* |
| ![Duo I P v 6 Predefinido Router Adicionar ícone](./media/user-guide/netx-events/image61.png)    | **Adicionar do router padrão Duo IPv6** *(nxd_ipv6_default_router_add)* |
| ![Duo I P v 6 Ícone de exclusão de router padrão](./media/user-guide/netx-events/image62.png)    | **Exclusão do router padrão Duo IPv6** *(nxd_ipv6_default_router_delete)* |
| ![Duo I P v 6 Ativar ícone](./media/user-guide/netx-events/image63.png)    | **Duo IPv6 Enable** *(nxd_ipv6_enable)* |
| ![Duo I P v 6 Global Address Obter ícone](./media/user-guide/netx-events/image64.png)    | **Duo IPv6 Global Address Get** *(nxd_ipv6_global_address_get)* |
| ![Duo I P v 6 Ícone global de conjunto de endereços](./media/user-guide/netx-events/image65.png)    | **Conjunto de endereços globais Duo IPv6** *(nxd_ipv6_global_address_set)* |
| ![Duo I P v6 Iniciado Ícone do Processo do Pai](./media/user-guide/netx-events/image66.png)    | **Duo IPv6 Iniciar Processo do Pai** *(nxd_ipv6_initiate_dad_process)* |
| ![Duo I P v 6 Interface Endereço Obter ícone](./media/user-guide/netx-events/image67.png)    | **Endereço de interface Duo IPv6 Obter** *(nxd_ipv6_interface_address_get)* |
| ![Ícone de conjunto de endereço de interface duo I P v 6](./media/user-guide/netx-events/image68.png)    | **Conjunto de endereços de interface Duo IPv6** *(nxd_ipv6_interface_address_set*) |
| ![Duo I P v 6 Link Endereço Local Obter ícone](./media/user-guide/netx-events/image69.png)    | **Duo IPv6 Link Endereço Local Obter** *(nxd_ipv6_linklocal_address_get)* |
| ![Duo I P v 6 Link Ícone de conjunto de endereço local](./media/user-guide/netx-events/image70.png)    | **Conjunto de endereços locais de ligação duo IPv6** *(nxd_ipv6_linklocal_address_set*) |
| ![Duo I P v6 Raw Packet Enviar ícone](./media/user-guide/netx-events/image71.png)    | **Duo IPv6 Raw Packet Send** *(nxd_ipv6_raw_packet_send)* |
| ![Duo T C P Socket Peer Info Obter ícone](./media/user-guide/netx-events/image72.png)    | **Duo TCP Socket Peer Info Get** *(nxd_tcp_socket_peer_info_get)* |
| ![Ícone de interface de conjunto de tomada de duo T C P](./media/user-guide/netx-events/image73.png)    | **Interface de conjunto de tomadas duo TCP** *(nxd_tcp_socket_set_interface)* |
| ![Tomada de duo U D P Enviar ícone](./media/user-guide/netx-events/image74.png)    | **Tomada dupla UDP Enviar** *(nxd_udp_socket_send)* |
| ![Ícone de interface de conjunto de tomada de P duo U D P](./media/user-guide/netx-events/image75.png)    | **Interface de conjunto de tomadas UDP duo** *(nxd_udp_socket_set_interface)* |
| ![Ícone de extrato de fonte duo U D P](./media/user-guide/netx-events/image76.png)    | **Extrato de origem Duo UDP** *(nxd_udp_source_extract)* |
| ![I C M P Ativar ícone](./media/user-guide/netx-events/image77.png)    | **ICMP Enable** *(nx_icmp_enable)* |
| ![I C M P Informações Obter ícone](./media/user-guide/netx-events/image78.png)    | **Informação do ICMP Obtém** *(nx_icmp_info_get)* |
| ![I C M P Ping ícone](./media/user-guide/netx-events/image79.png)    | **ICMP Ping** *(nx_icmp_ping)* |
| ![I G M P Ativar ícone](./media/user-guide/netx-events/image80.png)    | **IGMP Enable** *(nx_igmp_enable)* |
| ![I G M P Informações Obter ícone](./media/user-guide/netx-events/image81.png)    | **Informação IGMP Obter** *(nx_igmp_info_get)* |
| ![I G M P Loopback Desativar o ícone](./media/user-guide/netx-events/image82.png)    | **IGMP Loopback Disable** *(nx_igmp_loopback_disable)* |
| ![I G M P Loopback Ativar o ícone](./media/user-guide/netx-events/image83.png)    | **IGMP Loopback Enable** *(nx_igmp_loopback_enable)* |
| ![I G M P Multicast Juntar ícone](./media/user-guide/netx-events/image84.png)    | **IGMP Multicast Join** *(nx_igmp_multicast_join)* |
| ![I G M P Multicast Leave ícone](./media/user-guide/netx-events/image85.png)    | **Licença Multicast IGMP** *(nx_igmp_multicast_leave)* |
| ![I P Endereço Alterar Ícone de Notificação](./media/user-guide/netx-events/image86.png)    | **Notificação de alteração de endereço IP** *(nx_ip_address_change_notify)* |
| ![I Endereço P Obter ícone](./media/user-guide/netx-events/image87.png)    | **Endereço IP Get** *(nx_ip_address_get*) |
| ![Ícone de conjunto de endereços I P](./media/user-guide/netx-events/image88.png)    | **Conjunto de endereços IP** *(nx_ip_address_set*) |
| ![I P Criar ícone](./media/user-guide/netx-events/image89.png)    | **Criação IP** *(nx_ip_create)* |
| ![I P Eliminar ícone](./media/user-guide/netx-events/image90.png)    | **Eliminação IP** (*nx_ip_delete)* |
| ![I P Ícone de comando direto do motorista](./media/user-guide/netx-events/image91.png)    | **Comando Direto do Controlador IP** *(nx_ip_driver_direct_command)* |
| ![I P Encaminhamento Desativar ícone](./media/user-guide/netx-events/image92.png)    | **Desativação ip** *(nx_ip_forwarding_disable)* |
| ![I P Encaminhamento Ativar Ícone](./media/user-guide/netx-events/image93.png)    | **Viabilizar o encaminhamento IP** *(nx_ip_forwarding_enable)* |
| ![I P Fragmento Desativar ícone](./media/user-guide/netx-events/image94.png)    | **Desativação de fragmentos IP** *(nx_ip_fragment_disable)* |
| ![I P Fragmento Ativar ícone](./media/user-guide/netx-events/image95.png)    | **Ativação do fragmento IP** *(nx_ip_fragment_enable)*  |
| ![I P Gateway Endereço Conjunto ícone](./media/user-guide/netx-events/image96.png)    | **Conjunto de endereços IP Gateway** *(nx_ip_gateway_address_set*) |
| ![I P Informações Obter ícone](./media/user-guide/netx-events/image97.png)    | **Informação IP Obter** *(nx_ip_info_get)* |
| ![Ícone de anexação i interface P](./media/user-guide/netx-events/image98.png)    | **Anexação de interface IP** *(nx_ip_interface_attach)* |
| ![I P Interface Info Obter ícone](./media/user-guide/netx-events/image99.png)    | **Informação de interface IP Obtém** *(nx_ip_interface_info_get)* |
| ![I P Ícone de desativação de pacotes crus](./media/user-guide/netx-events/image100.png)    | **Ip Raw Packet Disable** *(nx_ip_raw_packet_disable)* |
| ![I P Pacote Cru Enable ícone](./media/user-guide/netx-events/image101.png)    | **IP Raw Packet Enable** *(nx_ip_raw_packet_enable)* |
| ![I P Pacote Cru Receber ícone](./media/user-guide/netx-events/image102.png)    | **IP Raw Packet Receive** *(nx_ip_raw_packet_receive)* |
| ![I P Pacote Cru Enviar ícone](./media/user-guide/netx-events/image103.png)    | **IP Raw Packet Send** *(nx_ip_raw_packet_send)* |
| ![I P Rota Estática Adicionar ícone](./media/user-guide/netx-events/image104.png)    | **Adiciono de rota estática IP** *(nx_ip_static_route_add)* |
| ![I P Rota Estática Eliminar ícone](./media/user-guide/netx-events/image105.png)    | **Eliminação da Rota Estática IP** *(nx_ip_static_route_delete)* |
| ![I P Status Check ícone](./media/user-guide/netx-events/image106.png)    | **Verificação do estado do IP** *(nx_ip_status_check)*|
| ![I P S E C Enable icon](./media/user-guide/netx-events/image107.png)    | **Ipsec Enable** *(nx_ipsec_enable)* |
| ![Ícone de atribuição de pacote](./media/user-guide/netx-events/image108.png)    | **Atribuição de pacotes** *(nx_packet_allocate)* |
| ![Ícone de cópia de pacote](./media/user-guide/netx-events/image109.png)    | **Cópia do pacote** *(nx_packet_copy)* |
| ![Ícone de apêndice de dados de pacote](./media/user-guide/netx-events/image110.png)    | **Apêndice de dados do pacote** *(nx_packet_data_append)* |
| ![Ícone de compensação de extrato de dados de pacote](./media/user-guide/netx-events/image111.png)    | **Compensação de extrato de dados de** pacotes *(nx_packet_data_extract_offset)* |
| ![Ícone de recuperação de dados de pacote](./media/user-guide/netx-events/image112.png)    | **Recuperação de dados de pacotes** *(nx_packet_data_retrieve)* |
| ![Comprimento do pacote Obter ícone](./media/user-guide/netx-events/image113.png)    | **Comprimento do pacote Obter** *(nx_packet_length_get)* |
| ![Pacote Pool Criar ícone](./media/user-guide/netx-events/image114.png)    | **Pacote De Criação de Piscina** *(nx_packet_pool_create)* |
| ![Ícone de excluir piscina de pacote](./media/user-guide/netx-events/image115.png)    | **Eliminação do Pacote Pool** *(nx_packet_pool_delete)* |
| ![Informações de piscina de pacote Obter ícone](./media/user-guide/netx-events/image116.png)    | **Informações da piscina de pacotes obter** *(nx_packet_pool_info_get)* |
| ![Ícone de lançamento de pacote](./media/user-guide/netx-events/image117.png)    | **Lançamento do pacote** *(nx_packet_release)* |
| ![Ícone de lançamento de transmissão de pacote](./media/user-guide/netx-events/image118.png)    | **Lançamento do pacote** *(nx_packet_transmit_release)* |
| ![R A R P Desativar o ícone](./media/user-guide/netx-events/image119.png)    | **RaRP Disable** *(nx_rarp_disable)* |
| ![R A R P Ativar o ícone](./media/user-guide/netx-events/image120.png)    | **Ativar RARP** *(nx_rarp_enable)* |
| ![R A R P Informações Obter ícone](./media/user-guide/netx-events/image121.png)    | **RaRP Information Get** *(nx_rarp_info_get)* |
| ![Ícone inicialize o sistema](./media/user-guide/netx-events/image122.png)    | **Inicialização do Sistema** *(nx_system_initialize)* |
| ![Ícone de ligação de tomada de cliente T C P](./media/user-guide/netx-events/image123.png)    | **Ficha de tomada de cliente TCP** *(nx_tcp_client_socket_bind)* |
| ![Ícone de ligação da tomada do cliente T C P](./media/user-guide/netx-events/image124.png)    | **Ligação da tomada de cliente TCP** *(nx_tcp_client_socket_connect)* |
| ![T C P Porta de tomada de cliente Obter ícone](./media/user-guide/netx-events/image125.png)    | **Porta de tomada de cliente TCP** *(nx_tcp_client_socket_port_get)* |
| ![T C P Tomada de cliente Unbind ícone](./media/user-guide/netx-events/image126.png)    | **Tomada de cliente TCP Unbind** *(nx_tcp_client_socket_unbind)* |
| ![T C P Ativar ícone](./media/user-guide/netx-events/image127.png)    | **TCP Enable** *(nx_tcp_enable)* |
| ![T C P Free Port Encontrar ícone](./media/user-guide/netx-events/image128.png)    | **Achado portuário livre TCP** *(nx_tcp_free_port_find)* |
| ![Informações T C P Obter ícone](./media/user-guide/netx-events/image129.png)    | **Informação da TCP Obter** *(nx_tcp_info_get)* |
| ![T C P Tomada de servidor Aceitar ícone](./media/user-guide/netx-events/image130.png)    | **Aceitação da tomada do servidor TCP** *(nx_tcp_server_socket_accept)* |
| ![T C P Tomada de servidor Ouvir ícone](./media/user-guide/netx-events/image131.png)    | **Tomada de servidor TCP Ouvir** *(nx_tcp_server_socket_listen)* |
| ![Ícone de relisten da tomada do servidor T C P](./media/user-guide/netx-events/image132.png)    | **Tomada de tomada do servidor TCP Relisten** *(nx_tcp_server_socket_relisten)* |
| ![T C P Servidor Socket Unacept Ícone](./media/user-guide/netx-events/image133.png)    | **Tomada de servidor TCP Unaccept** *(nx_tcp_server_socket_unaccept)* |
| ![T C P Tomada de servidor Unlisten ícone](./media/user-guide/netx-events/image134.png)    | **Tomada de servidor TCP Unlisten** *(nx_tcp_server_socket_unlisten)* |
| ![T C P Tomada Bytes Disponíveis Ícone](./media/user-guide/netx-events/image135.png)    | **TCP Socket Bytes Disponíveis** *(nx_tcp_socket_bytes_available)* |
| ![Tomada T C P Criar ícone](./media/user-guide/netx-events/image136.png)    | **Criação de tomada tCP** *(nx_tcp_socket_create)* |
| ![T C P Socket Eliminar ícone](./media/user-guide/netx-events/image137.png)    | **Apagar tomadas TCP** *(nx_tcp_socket_delete)* |
| ![T C P Ícone de desconexão da tomada](./media/user-guide/netx-events/image138.png)    | **Desconexão da tomada TCP** *(nx_tcp_socket_disconnect)* |
| ![Informações de tomada T C P Obtenha ícone](./media/user-guide/netx-events/image139.png)    | **Informações sobre tomadas TCP Obtêm** *(nx_tcp_socket_info_get)* |
| ![T C P Socket MSS Obter ícone](./media/user-guide/netx-events/image140.png)    | **TCP Socket MSS Get** *(nx_tcp_socket_mss_get)* |
| ![T C P Socket MSS Peer Obter ícone](./media/user-guide/netx-events/image141.png)    | **TCP Socket MSS Peer Get** *(nx_tcp_socket_mss_peer_get)* |
| ![T C P Tomada MSS Conjunto ícone](./media/user-guide/netx-events/image142.png)    | **Conjunto de MSS de tomada de TCP** *(nx_tcp_socket_mss_set)* |
| ![T C P Socket Peer Info Obter ícone](./media/user-guide/netx-events/image143.png)    | **TCP Socket Peer Info Get** *(nx_tcp_socket_peer_info_get)* |
| ![T C P Tomada Receber ícone](./media/user-guide/netx-events/image144.png)    | **Tomada TCP Receber** *(nx_tcp_socket_receive)* |
| ![T C P Receber Ícone de Notificação](./media/user-guide/netx-events/image145.png)    | **Notificação de receção de tomada de TCP** *(nx_tcp_socket_receive_notify)* |
| ![Tomada T C P Enviar ícone](./media/user-guide/netx-events/image146.png)    | **Envio de tomada TCP** *(nx_tcp_socket_send)* |
| ![T C P Tomada Estado De espera ícone](./media/user-guide/netx-events/image147.png)    | **Espera do estado da tomada TCP** *(nx_tcp_socket_state_wait)* |
| ![T C P Tomada Transmitir Ícone de Configuração](./media/user-guide/netx-events/image148.png)    | **Configuração de transmissão de tomada TCP** *(nx_tcp_socket_transmit_configure)* |
| ![T C P Atualização da janela da janela notificando o ícone do conjunto](./media/user-guide/netx-events/image149.png)    | **Conjunto de notificação da janela da tomada TCP** *(nx_tcp_socket_window_update_notify_set*)  |
| ![U D P Ativar ícone](./media/user-guide/netx-events/image150.png)    | **Ativação UDP** *(nx_udp_enable)* |
| ![U D P Free Port Encontrar ícone](./media/user-guide/netx-events/image151.png)    | **UDP Free Port Find** *(nx_udp_free_port_find)* |
| ![U D P Informações Obter ícone](./media/user-guide/netx-events/image152.png)    | **Informação da UDP Obter** *(nx_udp_info_get)* |
| ![Ícone de ligação de tomada de U D P](./media/user-guide/netx-events/image153.png)    | **Ligação de tomada uDP** *(nx_udp_socket_bind)* |
| ![U D P Socket Bytes Disponíveis ícone](./media/user-guide/netx-events/image154.png)    | **Bytes de tomada uDP disponíveis** *(nx_udp_socket_bytes_available)* |
| ![Ícone de desativação de desativação da tomada de U D P](./media/user-guide/netx-events/image155.png)    | **Desativação do checkum da tomada UDP** *(nx_udp_socket_checksum_disable)* |
| ![U D P Socket Checksum Ativar o ícone](./media/user-guide/netx-events/image156.png)    | **Ativação do custo de verificação da tomada UDP** *(nx_udp_socket_checksum_enable)* |
| ![Tomada U D P Criar ícone](./media/user-guide/netx-events/image157.png)    | **Criação de tomadas UDP** *(nx_udp_socket_create)* |
| ![U D P Socket Delete ícone](./media/user-guide/netx-events/image158.png)    | **Eliminação da tomada UDP** *(nx_udp_socket_delete)* |
| ![U D Informações de tomada Obter ícone](./media/user-guide/netx-events/image159.png)    | **Informações de tomada uDP Obtêm** *(nx_udp_socket_info_get)* |
| ![Ícone de conjunto de interface de tomada de U D P](./media/user-guide/netx-events/image160.png)    | **Conjunto de interface de tomada UDP** *(nx_udp_socket_interface_set*) |
| ![Porta de tomada U D P Obtenha ícone](./media/user-guide/netx-events/image161.png)    | **Porta de tomada UDP Get** *(nx_udp_socket_port_get)* |
| ![Tomada U D P Receber ícone](./media/user-guide/netx-events/image162.png)    | **Receção da tomada UDP** *(nx_udp_socket_receive)* |
| ![U D P Socket Receber Ícone de Notificação](./media/user-guide/netx-events/image163.png)    | **Notificação de receção** de tomada udp *(nx_udp_socket_receive_notify)* |
| ![Tomada U D P Enviar ícone](./media/user-guide/netx-events/image164.png)    | **Envio de tomada uDP** *(nx_udp_socket_send)* |
| ![Ícone unbind de tomada de U D P](./media/user-guide/netx-events/image165.png)    | **Tomada UDP Unbind** *(nx_udp_socket_unbind)* |
| ![Ícone de extrato de fonte de U D P](./media/user-guide/netx-events/image166.png)    | **Extrato de origem UDP** *(nx_udp_source_extract)* |

## <a name="event-descriptions"></a>Descrições do evento

As páginas seguintes descrevem os Eventos de Rastreio da NetX.

### <a name="internal-arp-request-receive"></a>Pedido interno de ARP Receber 

#### <a name="internal-arp-request-receive"></a>Pedido interno de ARP receber

**Ícone** ![ Ícone de receção de pedido de ARP interno](./media/user-guide/netx-events/image1.png)

**Descrição**

Este evento representa um evento interno de receção de pedido de ARP netx.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Endereço IP de origem
- Info Field 3: Ponteiro para pacote
- Info Field 4: Não utilizado

### <a name="internal-arp-request-send"></a>Pedido interno de ARP Enviar 

#### <a name="internal-arp-request-send"></a>Pedido interno de ARP enviar

**Ícone** ![ Pedido interno de ARP enviar ícone](./media/user-guide/netx-events/image2.png)

**Descrição**

Este evento representa um evento interno de envio de pedidos de ARP netx.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Endereço IP de destino
- Info Field 3: Ponteiro para pacote
- Info Field 4: Não utilizado

### <a name="internal-arp-response-receive"></a>Resposta Interna da ARP Receber 

#### <a name="internal-arp-request-receive"></a>Pedido interno de ARP receber

**Ícone** ![ O ícone de receção de pedido interno de ARP](./media/user-guide/netx-events/image3.png)

**Descrição**

Este evento representa um evento interno de receção de resposta netx ARP.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Endereço IP de origem
- Info Field 3: Ponteiro para pacote
- Info Field 4: Não utilizado

### <a name="internal-arp-response-send"></a>Envio de resposta interna da ARP 

#### <a name="internal-arp-request-send"></a>Pedido interno de ARP enviar

**Ícone** ![ O pedido de ARP interno enviar ícone](./media/user-guide/netx-events/image4.png)

**Descrição**

Este evento representa um evento interno de envio de resposta NetX.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Endereço IP de destino
- Info Field 3: Ponteiro para pacote
- Info Field 4: Não utilizado

### <a name="internal-icmp-receive"></a>ICMP Interno Receber 

#### <a name="internal-icmp-receive"></a>ICMP interno receber

**Ícone** ![ Ícone de receção interna I C M P](./media/user-guide/netx-events/image5.png)

**Descrição**

Este evento representa um evento interno de receção do NetX ICMP.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Endereço IP de origem
- Info Field 3: Ponteiro para pacote
- Info Field 4: Palavra 0 do cabeçalho ICMP

### <a name="internal-icmp-send"></a>Envio interno do ICMP 

#### <a name="internal-icmp-send"></a>Envio interno do ICMP

**Ícone** ![ I C M P interno enviar ícone](./media/user-guide/netx-events/image6.png)

**Descrição**

Este evento representa um evento interno de envio de NetX ICMP.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Endereço IP de destino
- Info Field 3: Ponteiro para pacote
- Info Field 4: Palavra 0 do cabeçalho ICMP

### <a name="internal-igmp-receive"></a>IGMP Interno Receber 

#### <a name="internal-igmp-receive"></a>IGMP interno receber

**Ícone** ![ Ícone de receção interna I G M P](./media/user-guide/netx-events/image7.png)

**Descrição**

Este evento representa um evento interno de receção netx IGMP.

**Campos de Informação**

- Info Field 1: Ponteiro IP
- Info Field 2: Endereço IP de origem
- Info Field 3: Ponteiro para pacote
- Info Field 4: Palavra 0 do cabeçalho IGMP

### <a name="internal-ip-receive"></a>Ip Interno Receber 

#### <a name="internal-ip-receive"></a>Ip interno receber

**Ícone** ![ Ícone de receção I P interno](./media/user-guide/netx-events/image8.png)

**Descrição**

Este evento representa um evento interno de receção do NetX IP.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Endereço IP de origem
- Info Field 3: Ponteiro para pacote
- Info Field 4: Comprimento do pacote

### <a name="internal-ip-send"></a>Envio ip interno

#### <a name="internal-ip-send"></a>Envio ip interno

**Ícone** ![ I P interno enviar ícone](./media/user-guide/netx-events/image9.png)

**Descrição**

Este evento representa um evento interno de envio de IP NetX.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Endereço IP de destino
- Info Field 3: Ponteiro para pacote
- Info Field 4: Comprimento do pacote

### <a name="internal-tcp-data-receive"></a>Dados internos da TCP recebem 

#### <a name="internal-tcp-data-receive"></a>Dados internos da TCP recebem

**Ícone** ![ Ícone de receção de dados internos de T C P](./media/user-guide/netx-events/image10.png)

**Descrição**

Este evento representa um evento interno de receção de dados da NetX TCP.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Endereço IP de origem
- Info Field 3: Ponteiro para pacote
- Info Field 4: Receber número de sequência

### <a name="internal-tcp-data-send"></a>Dados internos da TCP enviam 

#### <a name="internal-tcp-data-send"></a>Envio de dados internos da TCP

**Ícone** ![ Dados internos de T C P enviam ícone](./media/user-guide/netx-events/image11.png)

**Descrição**

Este evento representa um evento interno de envio de dados da NetX TCP.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Ponteiro para tomada
- Info Field 3: Ponteiro para pacote
- Info Field 4: Transmitir número de sequência

### <a name="internal-tcp-fin-receive"></a>TCP FIN Interno Receber 

#### <a name="internal-tcp-fin-receive"></a>A barbatana interna da TCP recebe

**Ícone** ![ Ícone de receção interna T C P F I N](./media/user-guide/netx-events/image12.png)

**Descrição**

Este evento representa um evento interno da NetX TCP FIN.

**Campos de Informação** 

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Ponteiro para tomada
- Info Field 3: Ponteiro para pacote
- Info Field 4: Receber número de sequência

### <a name="internal-tcp-fin-send"></a>TCP FIN Interno Enviar 

#### <a name="internal-tcp-fin-send"></a>Sistema interno de TCP enviar

**Ícone** ![ Ícone de envio interno T C P F I N](./media/user-guide/netx-events/image13.png)

**Descrição**

Este evento representa um evento interno de envio de NetX TCP FIN.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Ponteiro para tomada
- Info Field 3: Ponteiro para pacote
- Info Field 4:Transmitir número de sequência

### <a name="internal-tcp-rst-receive"></a>Receção Interna de TCP RST 

#### <a name="internal-tcp-rst-receive"></a>Receção Interna de TCP RST

**Ícone** ![ Ícone de receção interna T C P R S T](./media/user-guide/netx-events/image14.png)

**Descrição**

Este evento representa um evento interno de receção de reset NetX TCP.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP.
- Info Campo 2: Ponteiro para tomada.
- Info Field 3: Ponteiro para pacote.
- Info Campo 4: Receber número de sequência.

### <a name="internal-tcp-rst-send"></a>Envio interno de TCP RST 

#### <a name="internal-tcp-rst-send"></a>Envio interno de TCP RST

**Ícone** ![ Ícone de envio interno T C P R S T](./media/user-guide/netx-events/image15.png)

**Descrição**

Este evento representa um evento interno de reset NetX TCP.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Ponteiro para tomada
- Info Field 3: Ponteiro para pacote
- Info Field 4: Transmitir número de sequência

### <a name="internal-tcp-syn-receive"></a>Receção interna do TCP SYN 

#### <a name="internal-tcp-syn-receive"></a>SINA Interna TCP

**Ícone** ![ Ícone de receção interna T C P S Y N](./media/user-guide/netx-events/image16.png)

**Descrição**

Este evento representa um evento interno de receção netx TCP SYN.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Ponteiro para tomada
- Info Field 3: Ponteiro para pacote
- Info Field 4: Receber número de sequência

### <a name="internal-tcp-syn-send"></a>Envio interno de TCP SYN 

#### <a name="internal-tcp-syn-send"></a>TCP SYN interno enviar

**Ícone** ![ Ícone de envio interno T C P S Y N](./media/user-guide/netx-events/image17.png)

**Descrição**

Este evento representa um evento interno netx TCP SYN.

Campos de Informação 

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Ponteiro para tomada
- Info Field 3: Ponteiro para pacote -Info Field 4: Transmitir número de sequência

### <a name="internal-udp-receive"></a>UDP Interna Receber 

#### <a name="internal-udp-receive"></a>UDP interna receber

**Ícone** ![ Ícone de receção interna de U D P](./media/user-guide/netx-events/image18.png)

**Descrição**

Este evento representa um evento interno de receção da UDP netx.

**Campos de Informação** 

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Ponteiro para tomada
- Info Field 3: Ponteiro para pacote
- Info Field 4: Palavra 0 do cabeçalho da UDP

### <a name="internal-udp-send"></a>Envio interno da UDP 

#### <a name="internal-udp-send"></a>Envio interno da UDP

**Ícone** ![ Ícone de envio interno de U D P](./media/user-guide/netx-events/image19.png)

**Descrição**

Este evento representa um evento interno de envio de UDP NetX.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Ponteiro para tomada
- Info Field 3: Ponteiro para pacote
- Info Field 4: Palavra 0 do cabeçalho da UDP

### <a name="internal-rarp-receive"></a>Receção interna da RARP 

#### <a name="internal-rarp-receive"></a>Receção interna da RARP 

**Ícone** ![ Ícone de receção R A R P interno](./media/user-guide/netx-events/image20.png)

**Descrição**

Este evento representa um evento interno de receção netx RARP.

**Campos de Informação** 

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Endereço IP alvo
- Info Field 3: Ponteiro para pacote
- Info Field 4: Palavra 1 do cabeçalho RARP

### <a name="internal-rarp-send"></a>Envio interno da RARP 

#### <a name="internal-rarp-send"></a>RaRP interno enviar 

**Ícone** ![ Ícone de envio interno R A R P](./media/user-guide/netx-events/image21.png)

**Descrição**

Este evento representa um evento interno de envio netx RARP.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Endereço IP alvo
- Info Field 3: Ponteiro para pacote
- Info Field 4: Palavra 1 do cabeçalho RARP

### <a name="internal-tcp-retry"></a>Redatry TCP interno 

#### <a name="internal-tcp-retry"></a>Redação interna de TCP 

**Ícone** ![ Ícone interno de retografia T C P](./media/user-guide/netx-events/image22.png)

**Descrição**

Este evento representa um evento interno de relemistenção netx TCP.

**Campos de Informação**
- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Ponteiro para tomada
- Info Field 3: Ponteiro para pacote
- Info Field 4: Número de retrós em queses

### <a name="internal-tcp-state-change"></a>Mudança interna do estado da TCP 

#### <a name="internal-tcp-state-change"></a>Mudança interna do estado da TCP 

**Ícone** ![ Ícone de mudança de estado de T C P interno](./media/user-guide/netx-events/image23.png)

**Descrição**

Este evento representa um evento interno de mudança de estado netx TCP.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Ponteiro para tomada
- Info Field 3: Estado anterior
- Info Field 4: Novo estado

### <a name="internal-io-driver-packet-send"></a>Pacote de motorista interno enviar 

#### <a name="internal-io-driver-packet-send"></a>Envio de pacote de motorista de I/O interno

**Ícone** ![ Ícone de envio de pacote de motorista interno I/O](./media/user-guide/netx-events/image24.png)

**Descrição**

Este evento representa um evento interno de envio de pacotes de pilotos NetX I/O.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Ponteiro para pacote
- Info Field 3: Tamanho do pacote
- Info Field 4: Não utilizado

### <a name="internal-io-driver-initialize"></a>Inicialização interna do controlador de I/O 

#### <a name="internal-io-driver-initialize"></a>Inicialização do controlador de I/S interno

**Ícone** ![ Ícone inicializo do condutor interno I/O](./media/user-guide/netx-events/image25.png)

**Descrição**

Este evento representa um evento interno de inicialização do piloto NetX I/O.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="internal-io-driver-link-enable"></a>Ligação interna do controlador de I/O 

#### <a name="internal-io-driver-link-enable"></a>Ligação interna do controlador de I/O ativar

**Ícone** ![ Ligação interna do controlador I /O ativar ícone](./media/user-guide/netx-events/image26.png)

**Descrição**

Este evento representa uma ligação interna do controlador NetX I/O que permite o evento.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="internal-io-driver-link-disable"></a>Ligação interna do controlador de I/O Desativada 

#### <a name="internal-io-driver-link-disable"></a>Desativação interna da ligação do controlador de I/O

**Ícone** ![ Ícone de desativação do controlador interno I/O](./media/user-guide/netx-events/image27.png)

**Descrição**

Este evento representa um evento interno de desativação de ligação netx I/O.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="internal-io-driver-packet-broadcast"></a>Transmissão interna do pacote de motorista de I/O 

#### <a name="internal-io-driver-packet-broadcast"></a>Transmissão interna do pacote de motorista de I/O

**Ícone** ![ Ícone de transmissão de pacote de motorista interno I /O](./media/user-guide/netx-events/image28.png)

**Descrição**

Este evento representa um evento interno de transmissão de pacotes de pilotos NetX I/O.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Ponteiro para pacote
- Info Field 3: Tamanho do pacote
- Info Field 4: Não utilizado

### <a name="internal-io-driver-arp-send"></a>Envio interno de ARP do condutor de I/O 

#### <a name="internal-io-driver-arp-send"></a>Envio interno de ARP do condutor de I/O

**Ícone** ![ Ícone de envio de ARP do controlador interno I/O](./media/user-guide/netx-events/image29.png)

**Descrição**

Este evento representa um evento interno de envio de ARP do condutor netx I/O.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Ponteiro para pacote
- Info Field 3: Tamanho do pacote
- Info Field 4: Não utilizado

### <a name="internal-io-driver-arp-response-send"></a>Envio de resposta ARP do controlador interno de I/O 

#### <a name="internal-io-driver-arp-response-send"></a>Envio de resposta ARP do controlador de I/O interno

**Ícone** ![ Ícone de envio de resposta ARP do controlador interno I/O](./media/user-guide/netx-events/image30.png)

**Descrição**

Este evento representa um evento interno de envio de resposta a ARP do condutor netx I/O.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Ponteiro para pacote
- Info Field 3: Tamanho do pacote
- Info Field 4: Não utilizado

### <a name="internal-io-driver-rarp-send"></a>Envio interno de I/O do condutor RARP 

#### <a name="internal-io-driver-rarp-send"></a>Piloto interno rarp de i/o enviar

**Ícone** ![ Ícone de envio de RARP do controlador interno I/O](./media/user-guide/netx-events/image31.png)

**Descrição**

Este evento representa um evento interno de envio de pilotos netx I/O RARP.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Ponteiro para pacote
- Info Field 3: Tamanho do pacote
- Info Field 4: Não utilizado

### <a name="internal-io-driver-multicast-join"></a>União Multicast do controlador de I/O interna 

#### <a name="internal-io-driver-multicast-join"></a>União multicast do condutor de I/O interna

**Ícone** ![ Ícone de união multicast do condutor interno I /O](./media/user-guide/netx-events/image32.png)

**Descrição**

Este evento representa um evento interno de associação multicast do piloto NetX I/O.

**Campos de Informação** 

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="internal-io-driver-multicast-leave"></a>Licença multicast do controlador interno de I/O 

#### <a name="internal-io-driver-multicast-leave"></a>Licença multicast do condutor interno de I/O

**Ícone** ![ Ícone de licença multicast do condutor interno I /O](./media/user-guide/netx-events/image33.png)

**Descrição**

Este evento representa um evento interno de licença multicast do condutor NetX I/O.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="internal-io-driver-get-status"></a>O controlador interno de I/O obtém o estado 

#### <a name="internal-io-driver-get-status"></a>O controlador interno de I/O obtém o estado

**Ícone** ![ Motorista interno I/O obter ícone de estado](./media/user-guide/netx-events/image34.png)

**Descrição**

Este evento representa um evento interno do piloto netx I/O.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="internal-io-driver-get-speed"></a>Condutor interno de I/O obtém velocidade 

#### <a name="internal-io-driver-get-speed"></a>Condutor de I/O interno obtém velocidade

**Ícone** ![ Motorista interno I /O obter ícone de velocidade](./media/user-guide/netx-events/image35.png)

**Descrição**

Este evento representa um piloto interno netx I/O obter evento de velocidade.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="internal-io-driver-get-duplex-type"></a>Controlador interno de I/O obter tipo duplex 

#### <a name="internal-io-driver-get-duplex-type"></a>O condutor interno de I/O obtém o tipo duplex

**Ícone** ![ Motorista interno I /O obter ícone do tipo duplex](./media/user-guide/netx-events/image36.png)

**Descrição**

Este evento representa um controlador interno netx I/O obter evento tipo duplex.

**Campos de Informação** 

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="internal-io-driver-get-error-count"></a>Controlador interno de I/O obtenha contagem de erros

#### <a name="internal-io-driver-get-error-count"></a>Controlador de I/O interno obtém contagem de erros

**Ícone** ![ Controlador interno I /O obtém ícone de contagem de erros](./media/user-guide/netx-events/image37.png)

**Descrição**

Este evento representa um controlador Interno NetX I/O obter evento de contagem de erros.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="internal-io-driver-get-rx-count"></a>Motorista interno de I/O obtém conta de RX 

#### <a name="internal-io-driver-get-rx-count"></a>Condutor de I/O interno obtém contagem de RX

**Ícone** ![ Piloto interno I /O obtém ícone de contagem de RX](./media/user-guide/netx-events/image38.png)

**Descrição**

Este evento representa um piloto interno netx I/O obter evento de contagem RX.

**Campos de Informação** 

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="internal-io-driver-get-tx-count"></a>Condutor interno de I/O obtém contagem de TX 

#### <a name="internal-io-driver-get-tx-count"></a>Condutor de I/O interno obtém contagem de TX

**Ícone** ![ Piloto interno I /O obtém ícone de contagem de T X](./media/user-guide/netx-events/image39.png)

**Descrição**

Este evento representa um piloto interno netx I/O obter evento de contagem de TX.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="internal-io-driver-get-allocation-errors"></a>Condutor interno de I/O obtém erros de atribuição 

#### <a name="internal-io-driver-get-allocation-errors"></a>Condutor de I/O interno obtém erros de atribuição

**Ícone** ![ Condutor interno I/O obtém ícone de erros de atribuição](./media/user-guide/netx-events/image40.png)

**Descrição**

Este evento representa um piloto interno netx I/O obter evento de erros de atribuição.

**Campos de Informação** 

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="internal-io-driver-un-initialize"></a>Condutor interno de I/O Des-initialize 

#### <a name="internal-io-driver-un-initialize"></a>Condutor interno de I/O desa inicializar 

**Ícone** ![ Ícone interno I / O do condutor des-initialize](./media/user-guide/netx-events/image41.png)

**Descrição**

Este evento representa um evento interno de des-initialize do piloto netx I/O.

**Campos de Informação** 

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="internal-io-driver-deferred-processing"></a>Processamento diferido interno do controlador de I/O 

#### <a name="internal-io-driver-deferred-processing"></a>O controlador interno de I/O diferido 

**Ícone** ![ Ícone de processamento diferido do controlador interno I/O](./media/user-guide/netx-events/image42.png)

**Descrição**

Este evento representa um evento interno de processamento diferido do piloto NetX I/O.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Ponteiro para pacote
- Info Field 3: Comprimento do pacote
- Info Field 4: Não utilizado

### <a name="arp-dynamic-entries-invalidate"></a>Entradas dinâmicas ARP invalidam 

#### <a name="nx_arp_dynamic_entries_invalidate"></a>nx_arp_dynamic_entries_invalidate

**Ícone** ![ Um ícone invalidado de entradas dinâmicas R P](./media/user-guide/netx-events/image43.png)

**Descrição**

Este evento representa invalidar todos os ARP dinâmicos inteiros através de nx_arp_dynamic_entries_invalidate.

**Campos de Informação** 

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Entradas invalidadas
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="arp-dynamic-entry-set"></a>Conjunto de entrada dinâmica ARP 

#### <a name="nx_arp_dynamic_entry_set"></a>nx_arp_dynamic_entry_set

**Ícone** ![ Um ícone de conjunto de entrada dinâmica R P](./media/user-guide/netx-events/image44.png)

**Descrição**

Este evento representa a definição de uma entrada dinâmica de ARP através de nx_arp_dynamic_entry_set.

**Campos de Informação** 

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: endereço IP
- Info Field 3: Endereço físico (MSW)
- Info Field 4: Endereço físico (LSW)

### <a name="arp-enable"></a>Ativar a ARP 

#### <a name="nx_arp_enable"></a>nx_arp_enable

**Ícone** ![ Um ícone de ativação R P](./media/user-guide/netx-events/image45.png)

**Descrição**

Este evento representa permitir a ARP através de nx_arp_enable.

**Campos de Informação** 

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Ponteiro de memória de cache ARP
- Info Field 3: Tamanho da memória da cache ARP
- Info Field 4: Não utilizado

### <a name="arp-gratuitous-send"></a>Envio Gratuito ARP 

#### <a name="nx_arp_gratuitous_send"></a>nx_arp_gratuitous_send

**Ícone** ![ Um ícone de envio gratuito R P](./media/user-guide/netx-events/image46.png)

**Descrição**

Este evento representa um envio gratuito da ARP através de nx_arp_gratuitous_send.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="arp-hardware-address-find"></a>Encontrar endereço de hardware ARP 

#### <a name="nx_arp_hardware_address_find"></a>nx_arp_hardware_address_find

**Ícone** ![ Um ícone de endereço de hardware R P](./media/user-guide/netx-events/image47.png)

**Descrição**

Este evento representa encontrar uma morada física através de nx_arp_hardware_address_find.

**Campos de Informação** 

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: endereço IP
- Info Field 3: Endereço físico (MSW)
- Info Field 4: Endereço físico (LSW)

### <a name="arp-information-get"></a>Informação ARP Obtém 

#### <a name="nx_arp_info_get"></a>nx_arp_info_get

**Ícone** ![ Um ícone de informação R P obter](./media/user-guide/netx-events/image48.png)

**Descrição**

Este evento representa a obtenção de informação através de nx_arp_info_get.

**Campos de Informação** 

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: ARPs enviados
- Info Field 3: Respostas ARP
- Info Field 4: ARPs recebido

### <a name="arp-ip-address-find"></a>Encontrar endereço IP ARP 

#### <a name="nx_arp_ip_address_find"></a>nx_arp_ip_address_find

**Ícone** ![ Um endereço R P I P encontrar ícone](./media/user-guide/netx-events/image49.png)

**Descrição**

Este evento representa encontrar um endereço IP associado ao endereço físico fornecido através de nx_arp_ip_address_find.

**Campos de Informação** 

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: endereço IP
- Info Field 3: Endereço físico (MSW)
- Info Field 4: Endereço físico (LSW)

### <a name="arp-static-entry-create"></a>Criação de entrada estática ARP 

#### <a name="nx_arp_static_entry_create"></a>nx_arp_static_entry_create

**Ícone** ![ Uma entrada estática R P criar ícone](./media/user-guide/netx-events/image50.png)

**Descrição**

Este evento representa a criação de uma entrada estática de ARP através de nx_arp_static_entry_create.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: endereço IP
- Info Field 3: Endereço físico (MSW)
- Info Field 4: Endereço físico (LSW)

### <a name="arp-static-entries-delete"></a>As entradas estáticas do ARP eliminam 

#### <a name="nx_arp_static_entries_delete"></a>nx_arp_static_entries_delete

**Ícone** ![ Um ícone de entradas estáticas R P](./media/user-guide/netx-events/image51.png)

**Descrição**

Este evento representa a eliminação de todas as entradas estáticas ARP através de nx_arp_static_entries_delete.

**Campos de Informação** 

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Entradas eliminadas
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="arp-static-entry-delete"></a>Exclusão de entrada estática ARP 

### <a name="nx_arp_static_entry_delete"></a>nx_arp_static_entry_delete

**Ícone** ![ Um ícone de exclusão de entrada estática R P](./media/user-guide/netx-events/image52.png)

**Descrição**

Este evento representa a eliminação de uma entrada estática de ARP através de nx_arp_static_entry_delete.

**Campos de Informação** 

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: endereço IP
- Info Field 3: Endereço físico (MSW)
- Info Field 4: Endereço físico (LSW)

### <a name="duo-cache-entry-delete"></a>Entrada duo cache Delete 

#### <a name="nxd_und_cache_entry_delete"></a>nxd_und_cache_entry_delete

**Ícone** ![ Ícone de exclusão de entrada de cache duo](./media/user-guide/netx-events/image53.png)

**Descrição**

Este evento representa a eliminação de uma entrada na mesa de cache do vizinho através de nx_udp_socket_create.

**Campos de Informação** 

- Info Field 1: Quarta (menos significativa) palavra do endereço local de ligação IPv6 para eliminar
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="duo-cache-entry-set"></a>Conjunto de entrada de cache duo 

#### <a name="nxd_nd_cache_entry_set"></a>nxd_nd_cache_entry_set

**Ícone** ![ Ícone de conjunto de conjunto de entrada de cache duo](./media/user-guide/netx-events/image54.png)

**Descrição**

Este evento representa a criação de uma entrada de cache e a adição à mesa de cache do vizinho através de nxd_nd_cache_entry_set.

**Campos de Informação** 

- Info Field 1: Quarta (menos significativa) palavra do endereço IPv6 para adicionar
- Info Field 2: Endereço físico MSB
- Info Field 3: Endereço físico lsb
- Info Field 4: Não utilizado

### <a name="duo-cache-invalidate"></a>Duo Cache Invalidado 

#### <a name="nxd_nd_cache_invalidate"></a>nxd_nd_cache_invalidate

**Ícone** ![ Ícone invalidado de cache duo](./media/user-guide/netx-events/image55.png)

**Descrição**

Este evento representa invalidar toda a mesa de cache do vizinho através de nxd_nd_cache_invalidate.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="duo-cache-ip-address-find"></a>Encontrar endereço IP cache duo 

#### <a name="nxd_nd_cache_ip_address_find"></a>nxd_nd_cache_ip_address_find

**Ícone** ![ Endereço de cache de duo I P encontrar ícone](./media/user-guide/netx-events/image56.png)

**Descrição**

Este evento representa a recuperação de um endereço IP correspondente ao endereço físico fornecido da tabela cache através de nxd_nd_cache_ip_address_find.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Quarta (menos significativa) palavra do endereço IPv6
- Info Field 3: Endereço físico MSB
- Info Field 4: Endereço físico lsb

### <a name="duo-icmp-enable"></a>Ativar duo ICMP 

#### <a name="nxd_icmp_enable"></a>nxd_icmp_enable

**Ícone** ![ Duo I C M P ativar ícone](./media/user-guide/netx-events/image57.png)

**Descrição**

Este evento representa serviços ICMPv4 e ICMPv6 habilitados na instância IP especificada através de nxd_icmp_enable.

**Campos de Informação**
- Info Field 1: Pointer to IP instance
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="duo-icmp-ping"></a>Duo ICMP Ping 

#### <a name="nxd_icmp_ping"></a>nxd_icmp_ping

**Ícone** ![ Ícone de ping duo I C M P](./media/user-guide/netx-events/image58.png)

**Descrição**

Este evento representa o envio de um ping (pedido de eco) a um anfitrião IPv6 através de nxd_icmp_ping.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: endereço IPv6
- Info Field 3: Ponteiro para ecoar dados
- Info Field 4: Tamanho dos dados de eco

### <a name="duo-ip-max-payload-size-find"></a>Duo IP Max Payload Size Find 

#### <a name="nxd_ip_max_payload_size"></a>nxd_ip_max_payload_size

**Ícone** ![ Duo I P tamanho de carga útil máximo encontrar ícone](./media/user-guide/netx-events/image59.png)

**Descrição**

Este evento calcula a carga máxima que o pacote especificado pode transportar sem necessitar de fragmentação.

**Campos de Informação**

- Info Field 1: Ponteiro de tomada
- Info Field 2: Endereço IP do peer
- Info Field 3: Peer port Info Field 4: Não utilizado

### <a name="duo-ip-raw-packet-send"></a>Pacote de pacote cru duo IP enviar 

#### <a name="nxd_ip_max_packet_send"></a>nxd_ip_max_packet_send

**Ícone** ![ Duo I P pacote cru enviar ícone](./media/user-guide/netx-events/image60.png)

**Descrição**

Este evento representa o envio de um pacote IP bruto para fora da interface de rede especificada para o endereço de destino IP fornecido nxd_ip_raw_packet_send.

**Campos de Informação** 

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para pacote para enviar
- Info Field 3: Ponteiro para endereço de destino
- Info Field 4: Protocolo de pacote

### <a name="duo-ipv6-default-router-add"></a>Adicionar router padrão Duo IPv6 

#### <a name="nxd_ipv6_default_router_add"></a>nxd_ipv6_default_router_add

**Ícone** ![ Duo I P v 6 router padrão adicionar ícone](./media/user-guide/netx-events/image61.png)

**Descrição**

Este evento representa a adição de um router predefinido à tabela de encaminhamento IPv6 da instância IP através de nxd_ipv6_default_router_add.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP.
- Info Field 2: Endereço da Rede de Destino.
- Info Field 3: Informação sobre o tempo de vida.
- Info Field 4: Não utilizado.

### <a name="duo-ipv6-default-router-delete"></a>Exclusão do router padrão Duo IPv6 

#### <a name="nxd_ipv6_default_router_delete"></a>nxd_ipv6_default_router_delete

**Ícone** ![ Ícone de exclusão de router duo I P v 6 padrão](./media/user-guide/netx-events/image62.png)

**Descrição**

Este evento representa a remoção de um router predefinido da tabela de encaminhamento IPv6 da instância IP através de nxd_ipv6_default_router_delete.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP.
- Info Field 2: Quarta palavra (menos significativa) do endereço IPv6 do router predefinido.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="duo-ipv6-enable"></a>Duo IPv6 Enable 

#### <a name="nxd_ipv6_enable"></a>nxd_ipv6_enable

**Ícone** ![ Duo I P v 6 ativar ícone](./media/user-guide/netx-events/image63.png)

**Descrição**

Este evento representa a capacitação dos serviços IPv6 na instância IP fornecida através de nxd_ipv6_enable.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="duo-ipv6-global-address-get"></a>Duo IPv6 Global Address Get 

#### <a name="nxd_ipv6_global_address_get"></a>nxd_ipv6_global_address_get

**Ícone** ![ Duo I P v 6 endereço global obter ícone](./media/user-guide/netx-events/image64.png)

**Descrição**

Este evento representa a recuperação do endereço IP global (primário) na instância IP localizada no índice 1 na tabela de interface de instância IP via nxd_ipv6_global_address_get.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP.
- Info Field 2: Quarta palavra (menos significativa) do endereço global
- Info Campo 3: Comprimento do prefixo do endereço IPv6.
- Info Field 4: Índice na tabela de interface IP (1).

### <a name="duo-ipv6-global-address-set"></a>Conjunto de endereços globais duo IPv6 

#### <a name="nxd_ipv6_global_address_set"></a>nxd_ipv6_global_address_set

**Ícone** ![ Ícone de conjunto de endereços globais Duo I P v 6](./media/user-guide/netx-events/image65.png)

**Descrição**

Este evento representa a definição do endereço IP global (primário) na instância IP localizada no índice 1 na tabela de interface de instância IP via nxd_ipv6_global_address_set.

**Campos de Informação** 

- Info Field 1: Pointer to IP instance
- Info Field 2: Quarta palavra (menos significativa) do endereço global
- Info Field 3: Comprimento do prefixo do endereço IPv6
- Info Field 4: Índice na tabela de interface IP (1)

### <a name="duo-ipv6-initiate-dad-process"></a>Duo IPv6 Iniciar Processo do Pai 

#### <a name="nxd_ipv6_initiate_dad_process"></a>nxd_ipv6_initiate_dad_process

**Ícone** ![ Duo I P v6 iniciar ícone de processo do pai](./media/user-guide/netx-events/image66.png)

**Descrição**

Este evento representa o início do processo de Deteção de Endereços Duplicado (DAD) quando a instância IP é atribuída a um endereço de interface local ou IP através de nxd_ipv6_initiate_dad_process.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="duo-ipv6-interface-address-get"></a>Endereço de interface Duo IPv6 Obter 

#### <a name="nxd_ipv6_interface_address_get"></a>nxd_ipv6_interface_address_get

**Ícone** ![ Duo I P v 6 interface endereço obter ícone](./media/user-guide/netx-events/image67.png)

**Descrição**

Este evento representa a recuperação do endereço IP e prefixo no índice especificado na tabela de endereços de interface de instância IP através de nxd_ipv6_interface_address_get.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Quarta palavra (menos significativa) do endereço IPv6 para devolver
- Info Field 4: Índice de interface na tabela de interface de instância IP

### <a name="duo-ipv6-interface-address-set"></a>Conjunto de endereços de interface duo IPv6 

### <a name="nxd_ipv6_interface_address_set"></a>nxd_ipv6_interface_address_set

**Ícone** ![ Duo I P v 6 endereços de interface et ícone](./media/user-guide/netx-events/image68.png)

**Descrição**

Este evento representa a definição do endereço IP e prefixo no índice especificado na tabela de endereços de interface de instância IP. Não é permitido no índice zero (link endereço local) via nxd_ipv6_interface_address_set.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Quarta palavra (menos significativa) do endereço IPv6 para devolver
- Info Field 3: Comprimento do prefixo
- Info Field 4: Índice de interface na tabela de interface de instância IP

### <a name="duo-ipv6-link-local-address-get"></a>Duo IPv6 Link Endereço Local Obter 

#### <a name="nxd_ipv6_linklocal_address_get"></a>nxd_ipv6_linklocal_address_get

**Ícone** ![ Duo I P v 6 link endereço local obter ícone](./media/user-guide/netx-events/image69.png)

**Descrição**

Este evento representa a recuperação do endereço local de ligação da instância IP especificada através de nxd_ipv6_linklocal_address_get.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Quarta palavra (menos significativa) do endereço local de ligação IP v6
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="duo-ipv6-link-local-address-set"></a>Conjunto de endereços locais duo IPv6 Link 

#### <a name="nxd_ipv6_linklocal_address_set"></a>nxd_ipv6_linklocal_address_set

**Ícone** ![ Duo I P v 6 link ícone de conjunto de endereço local](./media/user-guide/netx-events/image70.png)

**Descrição**

Este evento representa a definição do endereço local de ligação da instância IP através de nxd_ipv6_linklocal_address_set.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Quarta (menos significativa) palavra do endereço local de ligação IPv6
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="duo-ipv6-raw-packet-send"></a>Duo IPv6 Raw Packet Enviar 

#### <a name="nxd_ipv6_raw_packet_send"></a>nxd_ipv6_raw_packet_send

**Ícone** ![ Duo I P v6 pacote cru enviar ícone](./media/user-guide/netx-events/image71.png)

**Descrição**

Este evento representa o envio de um pacote IP cru através da interface IP primária para o destino speficied via nxd_ip_raw_packet_send.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para pacote para enviar
- Info Field 3: Endereço IP de destino
- Info Field 4: Não utilizado

### <a name="duo-tcp-socket-peer-info-get"></a>Duo TCP Socket Peer Info Get 

#### <a name="nxd_tcp_socket_peer_info_get"></a>nxd_tcp_socket_peer_info_get

**Ícone** ![ Duo T C P tomada informação peer obter ícone](./media/user-guide/netx-events/image72.png)

**Descrição**

Este evento extrai os dados do remetente de um pacote TCP recebido na tomada especificada. Devolve o endereço IP e a porta do remetente.

**Campos de Informação**

- Info Field 1: Ponteiro de tomada
- Info Field 2: Endereço IP do peer
- Info Field 3: Porta peer
- Info Field 4: O arrendamento significativo 32 bits do endereço IP

### <a name="duo-tcp-socket-set-interface"></a>Interface de conjunto de tomada de TCP duo 

#### <a name="nxd_tcp_socket_set_interface"></a>nxd_tcp_socket_set_interface

**Ícone** ![ Ícone de interface de conjunto de tomada duo T C P](./media/user-guide/netx-events/image73.png)

**Descrição**

Este evento representa a definição da interface da tomada de saída depois de um cliente ligar-se a um servidor TCP no endereço IP do servidor especificado através de nxd_tcp_client_socket_connect.

**Campos de Informação** 

- Info Field 1: Ponteiro para tomada TCP
- Info Field 2: Interface ID
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="duo-udp-socket-send"></a>Dupla UDP Socket Enviar 

#### <a name="nxd_udp_socket_send"></a>nxd_udp_socket_send

**Ícone** ![ Tomada duo U D P enviar ícone](./media/user-guide/netx-events/image74.png)

**Descrição**

Este evento representa o envio de um pacote UDP através da tomada especificada com o endereço IP de entrada e porta via nxd_udp_socket_send.

**Campos de Informação** 

- Info Field 1: Ponteiro UDP Socket
- Info Field 2: Ponteiro para pacote UDP
- Info Field 3: Comprimento do pacote
- Info Field 4: Não utilizado


### <a name="duo-udp-socket-set-interface"></a>Interface de conjunto de tomada udp duo 

#### <a name="nxd_udp_socket_set_interface"></a>nxd_udp_socket_set_interface

**Ícone** ![ Ícone de interface de conjunto de tomada duo U D P](./media/user-guide/netx-events/image75.png)

**Descrição**

Este evento representa a definição da interface de saída da tomada UDP especificada para a interface correspondente ao ID da interface de entrada através de nxd_udp_socket_set_interface.

**Campos de Informação** 

- Info Field 1: Ponteiro para tomada UDP
- Info Field 2: Interface ID
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="duo-udp-source-extract"></a>Extrato de fonte duo UDP 

#### <a name="nxd_udp_socket_extract"></a>nxd_udp_socket_extract

**Ícone** ![ Ícone de extrato de fonte duo U D P](./media/user-guide/netx-events/image76.png)

**Descrição**

Este evento representa a extração do endereço IP e da porta de origem de um pacote recebido (ou IPv4 ou IPv6). Se o IPv6, a quarta palavra (menos significativa) do endereço IP for devolvida através de nxd_udp_source_extract.

**Campos de Informação**

- Info Field 1: Ponteiro para o pacote
- Info Field 2: versão IP
- Info Field 3: Endereço IP de origem (IPv4 ou IPv6)
- Info Field 4: Porta de origem

### <a name="icmp-enable"></a>ICMP Ativar 

#### <a name="nx_icmp_enable"></a>nx_icmp_enable

**Ícone** ![ I C M P ativar ícone](./media/user-guide/netx-events/image77.png)

**Descrição**

Este evento representa permitir o ICMP através de nx_icmp_enable.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP l;
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="icmp-information-get"></a>Informação do ICMP Obtém 

#### <a name="nx_icmp_info_get"></a>nx_icmp_info_get

**Ícone** ![ I C M P informações obter ícone](./media/user-guide/netx-events/image78.png)

**Descrição**

Este evento representa a obtenção de informação através de nx_icmp_info_get.

**Campos de Informação**
- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Pings enviados
- Info Field 3: Respostas de ping
- Info Field 4: Pings recebidos

### <a name="icmp-ping"></a>ICMP Ping 

#### <a name="nx_icmp_ping"></a>nx_icmp_ping

**Ícone** ![ I C M P ping ícone](./media/user-guide/netx-events/image79.png)

**Descrição**

Este evento representa a identificação de um endereço IP alvo através de nx_icmp_ping.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: endereço IP
- Info Field 3: Ponteiro para dados
- Info Field 4: Tamanho dos dados

### <a name="igmp-enable"></a>IGMP Ativar 

#### <a name="nx_icmp_enable"></a>nx_icmp_enable

**Ícone** ![ I G M P ativar ícone](./media/user-guide/netx-events/image80.png)

**Descrição**

Este evento representa permitir o IGMP através de nx_igmp_enable.

**Campos de Informação** 

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="igmp-information-get"></a>Informação IGMP Obter 

#### <a name="nx_icmp_info_get"></a>nx_icmp_info_get

**Ícone** ![ I G M P informações obter ícone](./media/user-guide/netx-events/image81.png)

**Descrição**

Este evento representa a obtenção de informação através de nx_igmp_info_get.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Relatórios enviados
- Info Field 3: Consultas recebidas
- Info Field 4: Grupos unidos

### <a name="igmp-loopback-disable"></a>Desativação do loopback IGMP 

#### <a name="nx_igmp_loopback_disable"></a>nx_igmp_loopback_disable

**Ícone** ![ I G M P loopback ícone desativar](./media/user-guide/netx-events/image82.png)

**Descrição**

Este evento representa desativar o loopback IGMP através de nx_igmp_loopback_disable.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="igmp-loopback-enable"></a>IGMP Loopback Ativa 

#### <a name="nx_igmp_loopback_enable"></a>nx_igmp_loopback_enable

**Ícone** ![ I G M P loopback ativar ícone](./media/user-guide/netx-events/image83.png)

**Descrição**

Este evento representa permitir o loopback IGMP através de nx_igmp_loopback_enable.

**Campos de Informação** 

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="igmp-multicast-join"></a>IGMP Multicast Join 

#### <a name="nx_igmp_multicast_join"></a>nx_igmp_multicast_join

**Ícone** ![ I G M P multicast juntar ícone](./media/user-guide/netx-events/image84.png)

**Descrição**

Este evento representa a adesão a um grupo multicast através de nx_igmp_multicast_join.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Endereço IP do grupo
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="igmp-multicast-leave"></a>Licença Multicast IGMP 

#### <a name="nx_igmp_multicast_leave"></a>nx_igmp_multicast_leave

**Ícone** ![ I G M P multicast deixar ícone](./media/user-guide/netx-events/image85.png)

**Descrição**

Este evento representa a saída de um grupo multicast via nx_igmp_multicast_leave.

**Campos de Informação** 

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Endereço IP do grupo
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="ip-address-change-notify"></a>Notificação de alteração de endereço IP 

#### <a name="nx_ip_address_change_notify"></a>nx_ip_address_change_notify

**Ícone** ![ I P endereço alterar ícone de notificação](./media/user-guide/netx-events/image86.png)

**Descrição**

Este evento representa o registo para notificação de alteração IP através de nx_ip_address_change_notify.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Ponteiro de função callback
- Info Field 3: Ponteiro informativo adicional
- Info Field 4: Não utilizado

### <a name="ip-address-get"></a>Endereço IP Obter 

#### <a name="nx_ip_address_get"></a>nx_ip_address_get

**Ícone** ![ Endereço I P obter ícone](./media/user-guide/netx-events/image87.png)

**Descrição**

Este evento representa obter o endereço IP através de nx_ip_address_get.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: endereço IP
- Info Field 3: Máscara de rede
- Info Field 4: Não utilizado

### <a name="ip-address-set"></a>Conjunto de endereços IP 

#### <a name="nx_ip_address_set"></a>nx_ip_address_set

**Ícone** ![ Ícone de conjunto de endereço I P](./media/user-guide/netx-events/image88.png)

**Descrição**

Este evento representa a definição do endereço IP através de nx_ip_address_set.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: endereço IP
- Info Field 3: Máscara de rede
- Info Field 4: Não utilizado

### <a name="ip-create"></a>Criação IP 

#### <a name="nx_ip_create"></a>nx_ip_create

**Ícone** ![ I P criar ícone](./media/user-guide/netx-events/image89.png)

**Descrição**

Este evento representa a criação de uma instância IP através de nx_ip_create.

**Campos de Informação** 
- Info Field 1: Ponteiro para a instância IP
- Info Field 2: endereço IP
- Info Field 3: Máscara de rede
- Info Field 4: Ponteiro de piscina de pacote padrão

### <a name="ip-delete"></a>IP Delete 

#### <a name="nx_ip_delete"></a>nx_ip_delete

**Ícone** ![ I P apagar ícone](./media/user-guide/netx-events/image90.png)

**Descrição**

Este evento representa a eliminação de uma instância IP através de nx_ip_delete.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="ip-driver-direct-command"></a>Comando Direto do Controlador IP 

#### <a name="nx_ip_driver_direct_command"></a>nx_ip_driver_direct_command

**Ícone** ![ I P driver ícone de comando direto](./media/user-guide/netx-events/image91.png)

**Descrição**

Este evento representa um comando de controlador de I/O direto via nx_ip_driver_direct_command.

**Campos de Informação** 

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Comando do condutor
- Info Campo 3: Valor de retorno
- Info Field 4: Não utilizado

### <a name="ip-forwarding-disable"></a>Desativação ip 

#### <a name="nx_ip_forwarding_disable"></a>nx_ip_forwarding_disable

**Ícone** ![ I P encaminhamento ícone de desativação](./media/user-guide/netx-events/image92.png)

**Descrição**

Este evento representa o encaminhamento IP incapacitante através de nx_ip_forwarding_disable.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="ip-forwarding-enable"></a>Ativar o encaminhamento IP 

#### <a name="nx_ip_forwarding_enable"></a>nx_ip_forwarding_enable

**Ícone** ![ I P encaminhamento ativar ícone](./media/user-guide/netx-events/image93.png)

**Descrição**

Este evento representa permitir o encaminhamento ip através de nx_ip_forwarding_enable.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="ip-fragment-disable"></a>Desativar fragmentos ip 

#### <a name="nx_ip_fragment_disable"></a>nx_ip_fragment_disable

**Ícone** ![ Ícone de desativação de fragmento de I P](./media/user-guide/netx-events/image94.png)

**Descrição**

Este evento representa a desativação da fragmentação de IP através de nx_ip_fragment_disable.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="ip-fragment-enable"></a>Ativar o fragmento ip 

#### <a name="nx_ip_fragment_enable"></a>nx_ip_fragment_enable

**Ícone** ![ I P fragmento ativar ícone](./media/user-guide/netx-events/image95.png)

**Descrição**

Este evento representa permitir a fragmentação ip através de nx_ip_fragment_enable.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="ip-gateway-address-set"></a>Conjunto de endereços IP Gateway 

#### <a name="nx_ip_gateway_address_set"></a>nx_ip_gateway_address_set

**Ícone** ![ Ícone definido de endereço de gateway I P](./media/user-guide/netx-events/image96.png)

**Descrição**

Este evento representa a definição do endereço IP gateway através de nx_ip_gateway_address_set.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Endereço IP gateway
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="ip-information-get"></a>Informação IP Obter 

#### <a name="nx_ip_info_get"></a>nx_ip_info_get

**Ícone** ![ I P informações obter ícone](./media/user-guide/netx-events/image97.png)

**Descrição** Este evento representa obter informações ip através de nx_ip_info_get.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: BYTES IP enviados
- Info Field 3: BYTES IP recebidos
- Info Field 4: Pacotes IP caíram

### <a name="ip-interface-attach"></a>Anexação de interface IP 

#### <a name="nx_interface_attach"></a>nx_interface_attach

**Ícone** ![ I ícone de anexação i p iterface](./media/user-guide/netx-events/image98.png)

**Descrição**

Este evento representa uma interface de rede secundária sendo anexada à instância IP através de nx_ip_interface_attach.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Interface ENDEREÇO IP
- Info Field 3: Índice na tabela de interface IP
- Info Field 4: Não utilizado

### <a name="ip-interface-info-get"></a>Informação de interface IP Obter 

#### <a name="nx_ip_interface_info_get"></a>nx_ip_interface_info_get

**Ícone** ![ Info de interface IP obter ícone](./media/user-guide/netx-events/image99.png)

**Descrição**

Este evento representa informações obtidas a partir da interface de rede especificada através de nx_ip_interface_info_get.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Interface ENDEREÇO IP
- Info Field 3: Interface MAC endereço MSB
- Info Field 4: Interface MAC endereço lsb

### <a name="ip-raw-packet-disable"></a>Pacote cru IP Desativar 

#### <a name="nx_ip_raw_packet_disable"></a>nx_ip_raw_packet_disable

**Ícone** ![ I P pacote cru desativar ícone](./media/user-guide/netx-events/image100.png)

**Descrição**

Este evento representa a desativação da comunicação de pacotes IP crus através de nx_ip_raw_packet_disable.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="ip-raw-packet-enable"></a>IP Pacote Cru Ativar 

#### <a name="nx_ip_raw_packet_enable"></a>nx_ip_raw_packet_enable

**Ícone** ![ I P pacote cru ativar ícone](./media/user-guide/netx-events/image101.png)

**Descrição**

Este evento representa permitir a comunicação de pacotes IP crus através de nx_ip_raw_packet_enable.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="ip-raw-packet-receive"></a>Pacote RAW IP Receber 

#### <a name="nx_ip_raw_packet_receive"></a>nx_ip_raw_packet_receive

**Ícone** ![ I P pacote cru receber ícone](./media/user-guide/netx-events/image102.png)

**Descrição**

Este evento representa a receção de um pacote IP cru via nx_ip_raw_packet_receive.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Ponteiro para pacote
- Info Field 3: Opção de espera
- Info Field 4: Não utilizado

### <a name="ip-raw-packet-send"></a>IP Pacote Cru Enviar 

#### <a name="nx_ip_raw_packet_send"></a>nx_ip_raw_packet_send

**Ícone** ![ I P pacote cru enviar ícone](./media/user-guide/netx-events/image103.png)

**Descrição**

Este evento representa o envio de um pacote IP cru via nx_ip_raw_packet_send.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Ponteiro para pacote
- Info Field 3: Endereço IP de destino
- Info Field 4: Tipo de serviço

### <a name="ip-static-route-add"></a>Adicionar rota estática IP 

#### <a name="nx_ip_static_route_add"></a>nx_ip_static_route_add

**Ícone** ![ I P rota estática adicionar ícone](./media/user-guide/netx-events/image104.png)

**Descrição**

Este evento representa uma rota estática sendo adicionada à tabela de encaminhamento de instância IP através de nx_ip_static_route_add.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Endereço de rede
- Info Field 3: Máscara de rede
- Info Field 4: Próximo salto

### <a name="ip-static-route-delete"></a>Eliminação da Rota Estática IP 

#### <a name="nx_ip_static_route_delete"></a>nx_ip_static_route_delete

**Ícone** ![ I P rute estático apagar ícone](./media/user-guide/netx-events/image105.png)

**Descrição**

Este evento representa uma rota estática sendo removida da tabela de encaminhamento de instância IP através de nx_ip_static_route_delete.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Endereço de rede
- Info Field 3: Máscara de rede
- Info Field 4: Não utilizado

### <a name="ip-status-check"></a>Verificação do estado do IP 

#### <a name="nx_ip_status_check"></a>nx_ip_status_check

**Ícone** ![ Ícone de verificação de estado I P](./media/user-guide/netx-events/image106.png)

**Descrição**

Este evento representa a verificação de um estado de IP através de nx_ip_status_check.

Campos de Informação 

- Info Field 1: Ponteiro para a instância IP
- Info Field 2: Estado solicitado
- Info Field 3: Estado real
- Info Field 4: Opção de espera

### <a name="ipsec-enable"></a>Ativar IPSEC 

#### <a name="nx_ipsec_enable"></a>nx_ipsec_enable

**Ícone** ![ I P S E C ativar ícone](./media/user-guide/netx-events/image107.png)

**Descrição**

Este evento representa a capacitação dos serviços IPSec na instância IP fornecida através de nx_ipsec_enable.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="packet-allocate"></a>Atribuição de pacotes 

#### <a name="nx_packet_allocate"></a>nx_packet_allocate

**Ícone** ![ Ícone de atribuição de pacote](./media/user-guide/netx-events/image108.png)

**Descrição**

Este evento representa a atribuição de um pacote através de nx_packet_allocate.

**Campos de Informação**

- Info Field 1: Ponteiro para a piscina de pacotes
- Info Field 2: Ponteiro para pacote atribuído
- Info Field 3: Tipo de pacote
- Info Field 4: Pacotes disponíveis

### <a name="packet-copy"></a>Cópia de pacote 

#### <a name="nx_packet_copy"></a>nx_packet_copy

**Ícone** ![ Ícone de pacote cpy](./media/user-guide/netx-events/image109.png)

**Descrição**

Este evento representa a cópia de um pacote através de nx_packet_copy.

**Campos de Informação**

- Info Field 2: Novo ponteiro do pacote
- Info Field 3: Ponteiro para pacote de piscina
- Info Field 4: Opção de espera

### <a name="packet-data-append"></a>Apend de dados de pacotes 

#### <a name="nx_packet_data_append"></a>nx_packet_data_append

**Ícone** ![ Ícone de apêndice de dados de pacote](./media/user-guide/netx-events/image110.png)

**Descrição**

Este evento representa dados de anexação a um pacote via nx_packet_data_append.

**Campos de Informação**

- Info Field 1: Ponteiro para o pacote
- Info Field 2: Ponteiro para dados
- Info Field 3: Tamanho dos dados
- Info Field 4: Ponteiro para pacote de piscina

### <a name="packet-data-extract-offset"></a>Compensação do extrato de dados do pacote 

#### <a name="nx_udp_source_extract_offset"></a>nx_udp_source_extract_offset

**Ícone** ![ Ícone de compensação de extrato de dados de pacote](./media/user-guide/netx-events/image111.png)

**Descrição**

Este evento representa dados de pacotes que são extraídos num tampão fornecido a partir de um pacote via nx_udp_source_extract_offset.

**Campos de Informação**

- Info Field 1: Ponteiro para pacote
- Info Field 2: Tamanho do tampão especificado
- Info Field 3: Número de bytes copiados
- Info Field 4: Não utilizado

### <a name="packet-data-retrieve"></a>Recuperação de dados de pacotes 

#### <a name="nx_packet_data_retrieve"></a>nx_packet_data_retrieve

**Ícone** ![ Ícone de recuperação de dados de pacote](./media/user-guide/netx-events/image112.png)

**Descrição**

Este evento representa a obtenção de dados de um pacote via nx_packet_data_retrieve.

**Campos de Informação** 

- Info Field 1: Ponteiro para o pacote
- Info Field 2: Ponteiro para o início do tampão
- Info Field 3: Bytes copiados
- Info Field 4: Não utilizado

### <a name="packet-length-get"></a>Comprimento do pacote obter 

#### <a name="nx_packet_length_get"></a>nx_packet_length_get

**Ícone** ![ Comprimento do pacote obter ícone](./media/user-guide/netx-events/image113.png)

**Descrição**

Este evento representa obter o comprimento de um pacote através de nx_packet_length_get.

**Campos de Informação**

- Info Field 1: Ponteiro para o pacote
- Info Field 2: Comprimento do pacote
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="packet-pool-create"></a>Criar pacotes de piscinas 

#### <a name="nx_packet_pool_create"></a>nx_packet_pool_create

**Ícone** ![ Pacote de piscina criar ícone](./media/user-guide/netx-events/image114.png)

**Descrição**

Este evento representa a criação de uma piscina de pacotes através de nx_packet_pool_create.

**Campos de Informação** 

- Info Field 1: Ponteiro para a piscina de pacotes
- Info Field 2: Tamanho da carga útil do pacote
- Info Field 3: Ponteiro para a área da memória da piscina
- Info Field 4: Tamanho da área de memória da piscina

### <a name="packet-pool-delete"></a>Excluir de pacotes de piscina 

#### <a name="nx_packet_pool_delete"></a>nx_packet_pool_delete

**Ícone** ![ Ícone de excluir piscina de pacote](./media/user-guide/netx-events/image115.png)

**Descrição**

Este evento representa a eliminação de uma piscina de pacotes através de nx_packet_pool_delete.

**Campos de Informação** 

- Info Field 1: Ponteiro para a piscina de pacotes
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

#### <a name="packet-pool-information-get"></a>Informações de piscina de pacotes obter 

#### <a name="nx_packet_pool_info_get"></a>nx_packet_pool_info_get

**Ícone** ![ Informações de piscina de pacote obter ícone](./media/user-guide/netx-events/image116.png)

**Descrição**

Este evento representa obter informações de pacotes através de nx_packet_pool_info_get.

**Campos de Informação**

- Info Field 1: Ponteiro para pacote de piscina
- Info Field 2: Total de pacotes
- Info Field 3: Pacotes disponíveis
- Info Field 4: Pedidos vazios

### <a name="packet-release"></a>Lançamento de pacotes 

#### <a name="nx_packet_data_release"></a>nx_packet_data_release

**Ícone** ![ Ícone de lançamento de pacote](./media/user-guide/netx-events/image117.png)

**Descrição**

Este evento representa a libertação de um pacote via nx_packet_release.

**Campos de Informação**

- Info Field 1: Ponteiro para o pacote
- Info Field 2: Estado do pacote
- Info Field 3: Pacotes disponíveis
- Info Field 4: Não utilizado

### <a name="packet-transmit-release"></a>Lançamento do pacote de transmissão 

#### <a name="nx_packet_transmit_release"></a>nx_packet_transmit_release

**Ícone** ![ Ícone de libertação de transmissão de pacote](./media/user-guide/netx-events/image118.png)

**Descrição**

Este evento representa a libertação de um pacote de transmissão via nx_packet_transmit_release.

**Campos de Informação**

- Info Field 1: Ponteiro para o pacote
- Info Field 2: Estado do pacote
- Info Field 3: Pacotes disponíveis
- Info Field 4: Não utilizado

### <a name="rarp-disable"></a>Desativar RARP 

#### <a name="nx_rarp_disable"></a>nx_rarp_disable

**Ícone** ![ R A R P desativar ícone](./media/user-guide/netx-events/image119.png)

**Descrição**

Este evento representa a desativação da RARP através de nx_rarp_disable.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="rarp-enable"></a>Ativar RARP 

#### <a name="nx_rarp_enable"></a>nx_rarp_enable

**Ícone** ![ R A R P ativar ícone](./media/user-guide/netx-events/image120.png)

**Descrição**

Este evento representa permitir a RARP através de nx_rarp_enable.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="rarp-information-get"></a>Informação RARP Obter 

#### <a name="nx_rarp_info_get"></a>nx_rarp_info_get

**Ícone** ![ R A R P informações obter ícone](./media/user-guide/netx-events/image121.png)

**Descrição**

Este evento representa obter informações da RARP através de nx_rarp_info_get.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Pedidos enviados
- Info Field 3: Respostas recebidas
- Info Field 4: Respostas inválidas

### <a name="system-initialize"></a>Inicialização do sistema 

#### <a name="nx_system_initialize"></a>nx_system_initialize

**Ícone** ![ Ícone inicializando o sistema](./media/user-guide/netx-events/image122.png)

**Descrição**

Este evento representa a inicialização do NetX através de nx_system_initialize.

**Campos de Informação**

- Info Field 1: Não utilizado
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="tcp-client-socket-bind"></a>Ligação de tomada de cliente TCP 

#### <a name="nx_tcp_client_socket_bind"></a>nx_tcp_client_socket_bind

**Ícone** ![ Ícone de ligação de tomada de cliente T P](./media/user-guide/netx-events/image123.png)

**Descrição**

Este evento representa a ligação de uma tomada de cliente a uma porta através de nx_tcp_client_socket_bind.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Field 3: Porta solicitada
- Info Field 4: Opção de espera

### <a name="tcp-client-socket-connect"></a>Ligação de tomada de cliente TCP 

#### <a name="nx_tcp_client_socket_connect"></a>nx_tcp_client_socket_connect

**Ícone** ![ Ícone de ligação de tomada de cliente T C P](./media/user-guide/netx-events/image124.png)

**Descrição**

Este evento representa a realização de uma ligação de tomada de cliente através de nx_tcp_client_socket_connect.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Field 3: Endereço IP do servidor
- Info Field 4: Porta do servidor solicitada

### <a name="tcp-client-socket-port-get"></a>Porta de tomada de cliente TCP obter 

#### <a name="nx_tcp_client_socket_port_get"></a>nx_tcp_client_socket_port_get

**Ícone** ![ Porta de tomada de cliente T C P obter ícone](./media/user-guide/netx-events/image125.png)

**Descrição**

Este evento representa obter o número da porta da tomada do cliente através de nx_tcp_client_socket_port_get.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Campo 3: Número de porta
- Info Field 4: Não utilizado

### <a name="tcp-client-socket-unbind"></a>Tomada de cliente TCP Unbind 

#### <a name="nx_tcp_client_socket_unbind"></a>nx_tcp_client_socket_unbind

**Ícone** ![ Ícone unbind de tomada de cliente T C P](./media/user-guide/netx-events/image126.png)

**Descrição**

Este evento representa a desvinão da porta associada à tomada através de nx_tcp_client_socket_unbind.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="tcp-enable"></a>Ativar TCP 

#### <a name="nx_tcp_enable"></a>nx_tcp_enable

**Ícone** ![ T C P ativar ícone](./media/user-guide/netx-events/image127.png)

**Descrição**

Este evento representa permitir a TCP através de nx_tcp_enable.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

###  <a name="tcp-free-port-find-tcp-free-port-find"></a>Porto Livre TCP Encontre porto livre TCP 

#### <a name="nx_tcp_free_port_find"></a>nx_tcp_free_port_find

**Ícone** ![ Ícone de encontrar porta livre T CP](./media/user-guide/netx-events/image128.png)

**Descrição**

Este evento representa encontrar uma porta TCP gratuita através de nx_tcp_free_port_find.

**Campos de Informação** 

- Info Field 1: Pointer to IP instance
- Info Field 2: Início do número da porta de pesquisa
- Info Field 3: Número de porta grátis
- Info Field 4: Não utilizado

###  <a name="tcp-infomation-get"></a>Infomation TCP Obter 

#### <a name="nx_tcp_info_get"></a>nx_tcp_info_get

**Ícone** ![ T C P informações obter ícone](./media/user-guide/netx-events/image129.png)

**Descrição**

Este evento representa a recuperação de informações TCP para a instância IP especificada através de nx_tcp_info_get.

**Campos de Informação** 

- Info Field 1: Pointer to IP instance
- Info Field 2: Número de bytes enviados
- Info Field 3: Número de bytes recebidos
- Info Field 4: Número de pacotes inválidos

###  <a name="tcp-server-socket-accept"></a>Tomada de servidor TCP Aceite 

#### <a name="nx_tcp_server_socket_accept"></a>nx_tcp_server_socket_accept

**Ícone** ![ Tomada do servidor T C P aceite ícone](./media/user-guide/netx-events/image130.png)

**Descrição**

Este evento representa a configuração da tomada do servidor depois de um pedido de ligação ativa ter sido recebido através de nx_tcp_server_socket_accept.

**Campos de Informação** 

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Field 3: Opção de espera
- Info Field 4: Estado da tomada

###  <a name="tcp-server-socket-listen"></a>Tomada do servidor TCP Ouvir 

#### <a name="nx_tcp_server_socket_listen"></a>nx_tcp_server_socket_listen

**Ícone** ![ Ícone de isten da tomada do servidor T C P](./media/user-guide/netx-events/image131.png)

**Descrição**

Este evento representa registar um pedido de escuta e uma tomada de servidor para a porta TCP especificada via nx_tcp_server_socket_listen.

**Campos de Informação** 

- Info Field 1: Pointer to IP instance
- Info Field 2: Número da porta TCP
- Info Field 3: Ponteiro para tomada
- Info Field 4: Número máximo de ligações que podem ser em fila

###  <a name="tcp-server-socket-relisten"></a>Relisten da tomada do servidor TCP 

#### <a name="nx_tcp_server_socket_relisten"></a>nx_tcp_server_socket_relisten

**Ícone** ![ Tomada de tomada do servidor T C P realista ícone](./media/user-guide/netx-events/image132.png)

**Descrição**

Este evento representa registar outra tomada de servidor para um pedido de escuta existente na porta TCP especificada através de nx_tcp_server_socket_relisten.

**Campos de Informação** 

- Info Field 1: Pointer to IP instance
- Info Field 2: Número da porta TCP
- Info Field 3: Ponteiro para tomada
- Info Field 4: Estado da tomada

###  <a name="tcp-server-socket-unaccept"></a>Tomada de servidor TCP Desacept 

#### <a name="nx_tcp_server_socket_unaccept"></a>nx_tcp_server_socket_unaccept

**Ícone** ![ Ícone de tomada de servidor T C P não aceita](./media/user-guide/netx-events/image133.png)

**Descrição**

Este evento representa a remoção da tomada do servidor de associação com a porta que recebe uma ligação passiva anterior através de nx_tcp_server_socket_unaccept.

**Campos de Informação** 

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Field 3: Estado da tomada
- Info Field 4: Não utilizado

###  <a name="tcp-server-socket-unlisten-tcp-server-socket-unlisten"></a>Tomada do servidor TCP Desafie a tomada do servidor TCP Unlisten 

#### <a name="nx_tcp_server_socket_unlisten"></a>nx_tcp_server_socket_unlisten

**Ícone** ![ Tomada de servidor T C P unlisten ícone](./media/user-guide/netx-events/image134.png)

**Descrição**

Este evento representa a remoção de um pedido de escuta anterior para a porta TCP especificada através de nx_tcp_server_socket_unlisten.

**Campos de Informação** 

- Info Field 1: Pointer to IP instance
- Info Field 2: Número da porta TCP
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="tcp-socket-bytes-available"></a>TCP Socket Bytes disponíveis 

#### <a name="nx_tcp_socket_bytes_available"></a>nx_tcp_socket_bytes_available

**Ícone** ![ T C P tomada bytes disponível ícone](./media/user-guide/netx-events/image135.png)

**Descrição**

Este evento representa o número de bytes atualmente disponíveis na tomada de receção TCP especificada através de nx_tcp_socket_bytes_available.

**Campos de Informação** 

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada TCP
- Info Field 3: Bytes recebidos na tomada
- Info Field 4: Não utilizado

### <a name="tcp-socket-create"></a>Criação de tomada TCP 

#### <a name="nx_tcp_socket_create"></a>nx_tcp_socket_create

**Ícone** ![ Tomada T C P criar ícone](./media/user-guide/netx-events/image136.png)

**Descrição**

Este evento representa a criação de uma tomada TCP através de nx_tcp_socket_create.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Field 3: Tipo de serviço
- Info Field 4: Receber o tamanho da janela

### <a name="tcp-socket-delete"></a>Apagar tomada TCP 

#### <a name="nx_tcp_socket_delete"></a>nx_tcp_socket_delete

**Ícone** ![ Ícone de eliminação da tomada T C P](./media/user-guide/netx-events/image137.png)

**Descrição**

Este evento representa a eliminação de uma tomada através de nx_tcp_socket_delete.

**Campos de Informação** 

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Field 3: Estado da tomada
- Info Field 4: Não utilizado

### <a name="tcp-socket-disconnect"></a>Desconexão da tomada TCP 

#### <a name="nx_tcp_socket_disconnect"></a>nx_tcp_socket_disconnect

**Ícone** ![ Ícone de desconexão da tomada T C P](./media/user-guide/netx-events/image138.png)

**Descrição**

Este evento representa desligar uma tomada através de nx_tcp_socket_disconnect.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Field 3: Opção de espera
- Info Field 4: Estado da tomada

### <a name="tcp-socket-information-get"></a>Informações da tomada TCP obtêm 

#### <a name="nx_tcp_socket_info_get"></a>nx_tcp_socket_info_get

**Ícone** ![ T C P informações de tomada obter ícone](./media/user-guide/netx-events/image139.png)

**Descrição**

Este evento representa obter informações sobre uma tomada através de nx_tcp_socket_info_get.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Field 3: Bytes enviados através desta tomada
- Info Field 4: Bytes recebidos através desta tomada

### <a name="tcp-socket-mss-get"></a>MSS de tomada TCP obter 

#### <a name="nx_tcp_socket_mss_get"></a>nx_tcp_socket_mss_get

**Ícone** ![ T C P socket M S S S obter ícone](./media/user-guide/netx-events/image140.png)

**Descrição**

Este evento representa obter o MSS da tomada através de nx_tcp_socket_mss_get.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Field 3: Tamanho máximo do segmento (MSS)
- Info Field 4: Estado da tomada

### <a name="tcp-socket-mss-peer-get"></a>TCP Socket MSS Peer Get 

#### <a name="nx_tcp_socket_mss_peer_get"></a>nx_tcp_socket_mss_peer_get

**Ícone** ![ T C P socket M S S peer obter ícone](./media/user-guide/netx-events/image141.png)

**Descrição**

Este evento representa obter o valor MSS do par da tomada através de nx_tcp_socket_mss_peer_get.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Field 3: Peer's MSS
- Info Field 4: Estado da tomada

### <a name="tcp-socket-mss-set"></a>Conjunto de MSS de tomada de TCP 

#### <a name="nx_tcp_socket_mss_set"></a>nx_tcp_socket_mss_set

**Ícone** ![ T C P tomada M S conjunto ícone](./media/user-guide/netx-events/image142.png)

**Descrição**

Este evento representa a definição do MSS de uma tomada através de nx_tcp_socket_mss_set.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Field 3: MSS
- Info Field 4: Estado da tomada

### <a name="tcp-socket-peer-info-get"></a>Informações de pares de tomadas TCP obtêm 

#### <a name="nx_tcp_socket_peer_info_get"></a>nx_tcp_socket_peer_info_get

**Ícone** ![ T C P tomada informação peer obter ícone](./media/user-guide/netx-events/image143.png)

**Descrição**

Este evento representa informações obtidas da tomada TCP relativas ao endereço IP (por exemplo, >anfitrião de ligação) endereço IP e porta através de nx_tcp_socket_peer_info_get.

**Campos de Informação**

- Info Field 1: Ponteiro para tomada TCP
- Info Field 2: Endereço IP do peer
- Info Field 3: Número da porta de pares
- Info Field 4: Não utilizado

### <a name="tcp-socket-receive"></a>Tomada TCP Receber 

#### <a name="nx_tcp_socket_receive"></a>nx_tcp_socket_receive

**Ícone** ![ T C P receber ícone](./media/user-guide/netx-events/image144.png)

**Descrição**

Este evento representa a receção de dados de uma tomada via nx_tcp_socket_receive.

**Campos de Informação**

- Info Field 1: Ponteiro para tomada
- Info Field 2: Ponteiro para receber pacote
- Info Field 3: Comprimento do pacote recebido
- Info Field 4: Receber número de sequência

### <a name="tcp-socket-receive-notify"></a>Notificação da tomada TCP 

#### <a name="nx_tcp_socket_receive_notify"></a>nx_tcp_socket_receive_notify

**Ícone** ![ Tomada T C P receber ícone de notificação](./media/user-guide/netx-events/image145.png)

**Descrição**

Este evento representa registar uma chamada de notificação de receção para uma tomada através de nx_tcp_socket_receive_notify.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Field 3: Ponteiro para receber notificação info de retorno Campo 4: Não utilizado

### <a name="tcp-socket-send"></a>Enviar tomada TCP 

#### <a name="nx_tcp_socket_send"></a>nx_tcp_socket_send

**Ícone** ![ T C P tomada enviar ícone](./media/user-guide/netx-events/image146.png)

**Descrição**

Este evento representa o envio de dados numa tomada via nx_tcp_socket_send.

**Campos de Informação**

- Info Field 1: Ponteiro para tomada
- Info Field 2: Ponteiro para pacote
- Info Field 3: Comprimento do pacote
- Info Field 4: Transmitir número de sequência

### <a name="tcp-socket-state-wait"></a>TCP Socket State Wait 

#### <a name="nx_tcp_socket_state_wait"></a>nx_tcp_socket_state_wait

**Ícone** ![ T C P estado de espera ícone](./media/user-guide/netx-events/image147.png)

**Descrição**

Este evento representa esperar que uma tomada entre num determinado estado através de nx_tcp_socket_state_wait.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Field 3: Estado de tomada desejada
- Info Field 4: Estado anterior da tomada

### <a name="tcp-socket-transmit-configure"></a>Configuração de transmissão de tomada TCP 

#### <a name="nx_tcp_socket_transmit_configure"></a>nx_tcp_socket_transmit_configure

**Ícone** ![ T C P tomada transmitir ícone de configuração](./media/user-guide/netx-events/image148.png)

**Descrição**

Este evento representa a configuração das opções de transmissão de uma tomada através de nx_tcp_socket_transmit_configure.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Field 3: Transmitir profundidade de fila
- Info Field 4: Valor de tempo limite

### <a name="tcp-socket-window-update-notify-set"></a>Atualização da janela da tomada TCP notificar conjunto 

#### <a name="nx_tcp_window_update_notify_set"></a>nx_tcp_window_update_notify_set

**Ícone** ![ Atualização da janela da tomada T C P notifica o ícone do conjunto](./media/user-guide/netx-events/image149.png)

**Descrição**

Este evento representa uma tomada TCP recebendo a notificação de um aumento na janela de receção do anfitrião remoto através de nx_tcp_window_update_notify_set.

**Campos de Informação** 

- Info Field 1: Ponteiro para tomada TCP
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="udp-enable"></a>Ativação uDP 

#### <a name="nx_udp_enable"></a>nx_udp_enable

**Ícone** ![ U D P ativar ícone](./media/user-guide/netx-events/image150.png)

**Descrição**

Este evento representa permitir a UDP através de nx_udp_enable.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="udp-free-port-find"></a>Descoberta de porto livre da UDP 

#### <a name="nx_udp_free_port_find"></a>nx_udp_free_port_find

**Ícone** ![ U D P porta livre encontrar ícone](./media/user-guide/netx-events/image151.png)

**Descrição**

Este evento representa encontrar uma porta UDP gratuita através de nx_udp_free_port_find.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Iniciar portas para pesquisar a partir de
- Info Field 3: Porta gratuita
- Info Field 4: Não utilizado

### <a name="udp-information-get"></a>Informações da UDP Obtêm 

#### <a name="nx_udp_info_get"></a>nx_udp_info_get

**Ícone** ![ U D P informações obter ícone](./media/user-guide/netx-events/image152.png)

**Descrição**

Este evento representa a obtenção de informação através de nx_udp_info_get.

**Campos de Informação** 

- Info Field 1: Pointer to IP instance
- Info Field 2: Bytes UDP enviados
- Info Field 3: Bytes UDP recebidos
- Info Field 4: Pacotes inválidos

### <a name="udp-socket-bind"></a>Ligação de tomada uDP 

#### <a name="nx_udp_socket_bind"></a>nx_udp_socket_bind

**Ícone** ![ Ícone de ligação da tomada de U D P](./media/user-guide/netx-events/image153.png)

**Descrição**

Este evento representa a ligação de uma tomada UDP a uma porta através de nx_udp_socket_bind.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Campo 3: Número de porta
- Info Field 4: Opção de espera

### <a name="udp-socket-bytes-available"></a>Bytes de tomada uDP disponíveis 

#### <a name="nx_udp_socket_bytes_available"></a>nx_udp_socket_bytes_available

**Ícone** ![ U D P tomada bytes disponíveis ícone](./media/user-guide/netx-events/image154.png)

**Descrição**

Este evento representa o número atual de bytes recebidos na tomada UDP via nx_udp_socket_bytes_available.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Field 3: Bytes recebidos na tomada
- Info Field 4: Não utilizado

### <a name="udp-socket-checksum-disable"></a>Desativação do checkum da tomada UDP 

#### <a name="nx_udp_socket_checksum_disable"></a>nx_udp_socket_checksum_disable

**Ícone** ![ Ícone de desativação da tomada de U D P](./media/user-guide/netx-events/image155.png)

**Descrição**

Este evento representa a desativação da data de verificação de dados numa tomada UDP através de nx_udp_socket_checksum_disable.

**Campos de Informação** 

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="udp-socket-checksum-enable"></a>Ativação do checkum de verificação da tomada UDP 

#### <a name="nx_udp_socket_checksum_enable"></a>nx_udp_socket_checksum_enable

**Ícone** ![ U D P socket checkum enable icon](./media/user-guide/netx-events/image156.png)

**Descrição**

Este evento representa permitir o processamento de checkum numa tomada através de nx_udp_socket_checksum_enable.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="udp-socket-create"></a>Criação de tomada uDP 

#### <a name="nx_udp_socket_create"></a>nx_udp_socket_create

**Ícone** ![ Tomada U D P criar ícone](./media/user-guide/netx-events/image157.png)

**Descrição**

Este evento representa a criação de uma tomada UDP através de nx_udp_socket_create.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Field 3: Tipo de serviço
- Info Field 4: Fila máxima de receção

### <a name="udp-socket-delete-event"></a>Evento de eliminação de tomadas UDP 

#### <a name="nx_udp_socket_delete-event"></a>evento nx_udp_socket_delete

**Ícone** ![ Tomada U D P apagar ícone do evento](./media/user-guide/netx-events/image158.png)

**Descrição**

Este evento representa a eliminação de uma tomada UDP através de nx_udp_socket_delete.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="udp-socket-information-get-event"></a>Informações da Tomada de UDP Obtêm Evento 

#### <a name="nx_udp_socket_info_get-event"></a>evento nx_udp_socket_info_get

**Ícone** ![ Informações de tomada U D P obtenham ícone de evento](./media/user-guide/netx-events/image159.png)

**Descrição**

Este evento representa obter informações sobre uma tomada UDP através de nx_udp_socket_info_get.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Field 3: Bytes enviados através da tomada
- Info Field 4: Bytes recebidos através da tomada

### <a name="udp-socket-interface-set"></a>Conjunto de interface de tomada de UDP 

#### <a name="nx_udp_socket_interface_set-event"></a>evento nx_udp_socket_interface_set

**Ícone** ![ Ícone de conjunto de conjunto de interface de tomada de U D P](./media/user-guide/netx-events/image160.png)

**Descrição**

Este evento representa a definição da interface de saída da tomada UDP especificada com a interface especificada através nx_udp_socket_interface_set.

**Campos de Informação**

- Info Field 1: Ponteiro para tomada UDP
- Info Field 2: Índice correspondente à interface para a tomada
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="udp-socket-port-get"></a>Porta de tomada uDP obter 

#### <a name="nx_udp_socket_port_get"></a>nx_udp_socket_port_get

**Ícone** ![ Porta de tomada U D P obter ícone](./media/user-guide/netx-events/image161.png)

**Descrição**

Este evento representa a recuperação da porta UDP a tomada UDP especificada é obrigada a através de nx_udp_socket_port_get.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada UDP
- Info Campo 3: Número de porta
- Info Field 4: Não utilizado

### <a name="udp-socket-receive"></a>Receber tomada UDP 

#### <a name="nx_udp_socket_receive"></a>nx_udp_socket_receive

**Ícone** ![ Tomada U D P receber ícone](./media/user-guide/netx-events/image162.png)

**Descrição**

Este evento representa a receção de dados sobre a tomada de UDP especificada através de nx_udp_socket_receive.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada UDP
- Info Field 3: Ponteiro para receber pacote
- Info Field 4: Tamanho do pacote recebido

### <a name="udp-socket-receive-notify"></a>Notificação de tomada de UDP 

#### <a name="nx_udp_socket_receive_notify"></a>nx_udp_socket_receive_notify

**Ícone** ![ Tomada U D P receber notificação ](./media/user-guide/netx-events/image163.png) ícone **descrição**

Este evento representa registar uma chamada de notificação de receção através de nx_udp_socket_receive_notify.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Field 3: Ponteiro para receber notificação função Info Campo 4: Não utilizado

### <a name="udp-socket-send"></a>Tomada UDP Enviar 

#### <a name="nx_udp_socket_send"></a>nx_udp_socket_send

**Ícone** ![ Tomada U D P enviar ícone](./media/user-guide/netx-events/image164.png)

**Descrição**

Este evento representa o envio de dados através de uma tomada UDP através de nx_udp_socket_send.

**Campos de Informação**

- Info Field 1: Ponteiro para tomada
- Info Field 2: Ponteiro para pacote
- Info Field 3: Comprimento do pacote
- Info Field 4: Endereço IP de destino

### <a name="udp-socket-unbind"></a>Tomada UDP Unbind 

#### <a name="nx_udp_socket_unbind"></a>nx_udp_socket_unbind

**Ícone** ![ Ícone unbind da tomada de U D P](./media/user-guide/netx-events/image165.png)

**Descrição**

Este evento representa a desvinão de uma porta UDP com uma tomada via nx_udp_socket_unbind.

**Campos de Informação**

- Info Field 1: Pointer to IP instance
- Info Field 2: Ponteiro para tomada
- Info Campo 3: Número de porta
- Info Field 4: Não utilizado

### <a name="udp-source-extract"></a>Extrato de origem UDP 

#### <a name="nx_udp_socket_create"></a>nx_udp_socket_create

**Ícone** ![ Ícone de extrato de fonte de U D P](./media/user-guide/netx-events/image166.png)

**Descrição**

Este evento representa obter o endereço IP e o número de porta de um pacote UDP recebido através de nx_udp_source_extract.

**Campos de Informação**

- Info Field 1: Ponteiro para pacote
- Info Field 2: Endereço IP do Remetente
- Info Field 3: Número da porta do remetente
- Info Field 4: Não utilizado