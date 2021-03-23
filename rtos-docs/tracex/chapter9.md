---
title: Capítulo 9 - Azure RTOS USBX trace eventos
description: Este capítulo contém uma descrição dos eventos Azure RTOS USBX exibidos pela TraceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 98561fe1d131e1d1b0893b7d89eb720881a82ac8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828351"
---
# <a name="chapter-9---azure-rtos-usbx-trace-events"></a><span data-ttu-id="4e4bd-103">Capítulo 9 - Azure RTOS USBX trace eventos</span><span class="sxs-lookup"><span data-stu-id="4e4bd-103">Chapter 9 - Azure RTOS USBX trace events</span></span>

<span data-ttu-id="4e4bd-104">Este capítulo contém uma descrição dos eventos Azure RTOS USBX exibidos pela TraceX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-104">This chapter contains a description of the Azure RTOS USBX events displayed by TraceX.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="4e4bd-105">Lista de eventos e ícones</span><span class="sxs-lookup"><span data-stu-id="4e4bd-105">List of Events and Icons</span></span>

<span data-ttu-id="4e4bd-106">Segue-se uma lista de eventos USBX apresentados pela TraceX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-106">The following is a list of USBX events displayed by TraceX.</span></span>

| <span data-ttu-id="4e4bd-107">Ícone</span><span class="sxs-lookup"><span data-stu-id="4e4bd-107">Icon</span></span>                             | <span data-ttu-id="4e4bd-108">Significado</span><span class="sxs-lookup"><span data-stu-id="4e4bd-108">Meaning</span></span>                               |
| -------------------------------- | ------------------------------------- |
| ![Ícone ativar classe C D C C do dispositivo](./media/user-guide/usbx-events/image1.png)    | <span data-ttu-id="4e4bd-110">**Dispositivo Classe Cdc Ativar** *(ux_device_class_cdc_activate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-110">**Device Class Cdc Activate** *(ux_device_class_cdc_activate)*</span></span> |
| ![Ícone desativado classe C D C C](./media/user-guide/usbx-events/image2.png)    | <span data-ttu-id="4e4bd-112">**Desativar o CDC classe de dispositivo** *(ux_device_class_cdc_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-112">**Device Class Cdc Deactivate** *(ux_device_class_cdc_deactivate)*</span></span> |
| ![Ícone de leitura classe C D C do dispositivo](./media/user-guide/usbx-events/image3.png)    | <span data-ttu-id="4e4bd-114">**Leitura do cdc classe do dispositivo** *(ux_device_class_cdc_read)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-114">**Device Class Cdc Read** *(ux_device_class_cdc_read)*</span></span> |
| ![Ícone de escrita classe C D C do dispositivo](./media/user-guide/usbx-events/image4.png)    | <span data-ttu-id="4e4bd-116">**Escrita do Cdc classe de dispositivo** *(ux_device_class_cdc_write)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-116">**Device Class Cdc Write** *(ux_device_class_cdc_write)*</span></span> |
| ![Ícone ativar classe de dispositivo](./media/user-guide/usbx-events/image5.png)    | <span data-ttu-id="4e4bd-118">**Dispositivo Classe Dpump Ativar** *(ux_device_class_dpump_activate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-118">**Device Class Dpump Activate** *(ux_device_class_dpump_activate)*</span></span> |
| ![Ícone de desativado da classe de dispositivo Dpump](./media/user-guide/usbx-events/image6.png)    | <span data-ttu-id="4e4bd-120">**Desativar a classe do dispositivo Dpump** *(ux_device_class_dpump_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-120">**Device Class Dpump Deactivate** *(ux_device_class_dpump_deactivate)*</span></span> |
| ![Ícone de leitura de classe de dispositivo](./media/user-guide/usbx-events/image7.png)    | <span data-ttu-id="4e4bd-122">**Leitura de Dpump classe de dispositivo** *(ux_device_class_dpump_read)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-122">**Device Class Dpump Read** *(ux_device_class_dpump_read)*</span></span> |
| ![Ícone de escrita de classe de dispositivo](./media/user-guide/usbx-events/image8.png)    | <span data-ttu-id="4e4bd-124">**Escrita de Classe de Dispositivo** *(ux_device_class_dpump_write)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-124">**Device Class Dpump Write** *(ux_device_class_dpump_write)*</span></span> |
| ![Ícone ativar classe de dispositivo Hid](./media/user-guide/usbx-events/image9.png)    | <span data-ttu-id="4e4bd-126">**Classe de dispositivo Hid Ativado** *(ux_device_class_hid_activate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-126">**Device Class Hid Activate** *(ux_device_class_hid_activate)*</span></span> |
| ![Ícone de desativado classe de dispositivo Hid](./media/user-guide/usbx-events/image10.png)    | <span data-ttu-id="4e4bd-128">**Classe de dispositivo Hid Desativado** *(ux_device_class_hid_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-128">**Device Class Hid Deactivate** *(ux_device_class_hid_deactivate)*</span></span> |
| ![Classe de dispositivo hiddscriptor Enviar ícone](./media/user-guide/usbx-events/image11.png)    | <span data-ttu-id="4e4bd-130">**Classe de dispositivo Hid Descriptor Enviar** *(ux_device_class_hid_descriptor_send)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-130">**Device Class Hid Descriptor Send** *(ux_device_class_hid_descriptor_send)*</span></span> |
| ![Classe de dispositivo hid evento obter ícone](./media/user-guide/usbx-events/image12.png)    | <span data-ttu-id="4e4bd-132">**Evento hid de classe de dispositivo** *(ux_device_class_hid_event_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-132">**Device Class Hid Event Get** *(ux_device_class_hid_event_get)*</span></span> |
| ![Ícone de conjunto de evento de classe de dispositivo hid](./media/user-guide/usbx-events/image13.png)    | <span data-ttu-id="4e4bd-134">**Conjunto de eventos de classe de dispositivo** *(ux_device_class_hid_event_set)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-134">**Device Class Hid Event Set** *(ux_device_class_hid_event_set)*</span></span> |
| ![Relatório hid classe de dispositivo obter ícone](./media/user-guide/usbx-events/image14.png)    | <span data-ttu-id="4e4bd-136">**Relatório hid da classe do dispositivo obter** *(ux_device_class_hid_report_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-136">**Device Class Hid Report Get** *(ux_device_class_hid_report_get)*</span></span> |
| ![Ícone de conjunto de relatório de classe de dispositivo hid](./media/user-guide/usbx-events/image15.png)    | <span data-ttu-id="4e4bd-138">**Conjunto de relatórios de hid classe de dispositivo** *(ux_device_class_hid_report_set)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-138">**Device Class Hid Report Set** *(ux_device_class_hid_report_set)*</span></span> |
| ![Ícone de ativação classe de dispositivo Pima](./media/user-guide/usbx-events/image16.png)    | <span data-ttu-id="4e4bd-140">**Classe de dispositivo Pima Ativar** *(ux_device_class_pima_activate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-140">**Device Class Pima Activate** *(ux_device_class_pima_activate)*</span></span> |
| ![Ícone de desativado classe de dispositivo Pima](./media/user-guide/usbx-events/image17.png)    | <span data-ttu-id="4e4bd-142">**Classe de dispositivo Pima Desativado** *(ux_device_class_pima_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-142">**Device Class Pima Deactivate** *(ux_device_class_pima_deactivate)*</span></span> |
| ![Informação de envio de dispositivo classe de dispositivo Pima classe de dispositivo](./media/user-guide/usbx-events/image18.png)    | <span data-ttu-id="4e4bd-144">**Informação do dispositivo classe Pima Enviar** *(ux_device_class_pima_device_info_send)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-144">**Device Class Pima Device Info Send** *(ux_device_class_pima_device_info_send)*</span></span> |
| ![Evento Pima classe de dispositivo Obter ícone](./media/user-guide/usbx-events/image19.png)    | <span data-ttu-id="4e4bd-146">**Evento Pima classe de dispositivo** *(ux_device_class_pima_event_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-146">**Device Class Pima Event Get** *(ux_device_class_pima_event_get)*</span></span> |
| ![Ícone de conjunto de evento classe de dispositivo Pima](./media/user-guide/usbx-events/image20.png)    | <span data-ttu-id="4e4bd-148">**Conjunto de eventos classe de dispositivo Pima** *(ux_device_class_pima_event_set)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-148">**Device Class Pima Event Set** *(ux_device_class_pima_event_set)*</span></span> |
| ![Ícone de adicionar objeto classe de dispositivo Pima](./media/user-guide/usbx-events/image21.png)    | <span data-ttu-id="4e4bd-150">**Adicionar objeto classe de dispositivo Pima** *(ux_device_class_pima_object_add)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-150">**Device Class Pima Object Add** *(ux_device_class_pima_object_add)*</span></span> |
| ![Dados de objeto de classe de dispositivo Pima Obter ícone](./media/user-guide/usbx-events/image22.png)    | <span data-ttu-id="4e4bd-152">**Dados de objetos de classe de dispositivo Pima obtêm** *(ux_device_class_pima_object_data_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-152">**Device Class Pima Object Data Get** *(ux_device_class_pima_object_data_get)*</span></span> |
| ![Dados de objeto de classe de dispositivo Pima Enviar ícone](./media/user-guide/usbx-events/image23.png)    | <span data-ttu-id="4e4bd-154">**Dados de objetos de classe de dispositivo Pima envio** *(ux_device_class_pima_object_data_send)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-154">**Device Class Pima Object Data Send** *(ux_device_class_pima_object_data_send)*</span></span> |
| ![Ícone de eliminação de objeto de classe de dispositivo Pima](./media/user-guide/usbx-events/image24.png)    | <span data-ttu-id="4e4bd-156">**Eliminação de objetos classe de dispositivo Pima** *(ux_device_class_pima_object_delete)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-156">**Device Class Pima Object Delete** *(ux_device_class_pima_object_delete)*</span></span> |
| ![Alças de objeto classe de dispositivo Pima Enviar ícone](./media/user-guide/usbx-events/image25.png)    | <span data-ttu-id="4e4bd-158">**Dispositivo Classe Pima Objeto Handles Enviar** *(ux_device_class_pima_object_handles_send)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-158">**Device Class Pima Object Handles Send** *(ux_device_class_pima_object_handles_send)*</span></span> |
| ![Classe de dispositivo Pima Objeto Info Obter ícone](./media/user-guide/usbx-events/image26.png)    | <span data-ttu-id="4e4bd-160">**Informações de objetos Pima classe de dispositivo** *(ux_device_class_pima_object_info_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-160">**Device Class Pima Object Info Get** *(ux_device_class_pima_object_info_get)*</span></span> |
| ![Classe de dispositivo Pima Objeto Info Enviar ícone](./media/user-guide/usbx-events/image27.png)    | <span data-ttu-id="4e4bd-162">**Informações de objetos de classe de dispositivo Pima Enviar** *(ux_device_class_pima_object_info_send)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-162">**Device Class Pima Object Info Send** *(ux_device_class_pima_object_info_send)*</span></span> |
| ![Número de objetos de classe de dispositivo Pima Enviar ícone](./media/user-guide/usbx-events/image28.png)    | <span data-ttu-id="4e4bd-164">**Número de objetos classe de dispositivo Pima Enviar** *(ux_device_class_pima_objects_number_send)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-164">**Device Class Pima Objects Number Send** *(ux_device_class_pima_objects_number_send)*</span></span> |
| ![Classe de dispositivo Pima Objeto Parcial Objeto Dados Obter ícone](./media/user-guide/usbx-events/image29.png)    | <span data-ttu-id="4e4bd-166">**Dados de objetos parciais da classe do dispositivo Pima obtêm** *(ux_device_class_pima_partial_object_data_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-166">**Device Class Pima Partial Object Data Get** *(ux_device_class_pima_partial_object_data_get)*</span></span> |
| ![Ícone de resposta pima classe de dispositivo](./media/user-guide/usbx-events/image30.png)    | <span data-ttu-id="4e4bd-168">**Envio de resposta classe de dispositivo Pima** *(ux_device_class_pima_response_send)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-168">**Device Class Pima Response Send** *(ux_device_class_pima_response_send)*</span></span>|
| ![Classe de dispositivo Pima Armazenamento I D Enviar ícone](./media/user-guide/usbx-events/image31.png)    | <span data-ttu-id="4e4bd-170">**Envio de Id de armazenamento classe de dispositivo Pima** *(ux_device_class_pima_storage_id_send)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-170">**Device Class Pima Storage Id Send** *(ux_device_class_pima_storage_id_send)*</span></span> |
| ![Classe de dispositivo Pima Storage Info Enviar ícone](./media/user-guide/usbx-events/image32.png)    | <span data-ttu-id="4e4bd-172">**Informações de armazenamento classe de dispositivo Pima Enviar** *(ux_device_class_pima_storage_info_send)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-172">**Device Class Pima Storage Info Send** *(ux_device_class_pima_storage_info_send)*</span></span> |
| ![Ícone ativar classe de dispositivo R N D I S](./media/user-guide/usbx-events/image33.png)    | <span data-ttu-id="4e4bd-174">**Dispositivo Classe Rndis Ativar** *(ux_device_class_rndis_activate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-174">**Device Class Rndis Activate** *(ux_device_class_rndis_activate)*</span></span> |
| ![Ícone de desativado classe de dispositivo R N D I S](./media/user-guide/usbx-events/image34.png)    | <span data-ttu-id="4e4bd-176">**Classe dispositivo Rndis Desativado** *(ux_device_class_rndis_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-176">**Device Class Rndis Deactivate** *(ux_device_class_rndis_deactivate)*</span></span> |
| ![Classe de dispositivo R N D I S Mensagem Manter Aliveicon](./media/user-guide/usbx-events/image35.png)    | <span data-ttu-id="4e4bd-178">**Mensagem Rndis classe dispositivo Manter vivo** *(ux_device_class_rndis_msg_keep_alive)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-178">**Device Class Rndis Message Keep Alive** *(ux_device_class_rndis_msg_keep_alive)*</span></span> |
| ![Ícone de consulta de mensagem classe de dispositivo R N D I S](./media/user-guide/usbx-events/image36.png)    | <span data-ttu-id="4e4bd-180">**Consulta de mensagem classe de dispositivo Rndis** *(ux_device_class_rndis_msg_query)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-180">**Device Class Rndis Message Query** *(ux_device_class_rndis_msg_query)*</span></span> |
| ![Ícone de reset de mensagem classe de dispositivo R N D I S](./media/user-guide/usbx-events/image37.png)    | <span data-ttu-id="4e4bd-182">**Reset de mensagem classe de dispositivo Rndis** *(ux_device_class_rndis_msg_reset)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-182">**Device Class Rndis Message Reset** *(ux_device_class_rndis_msg_reset)*</span></span> |
| ![Ícone de conjunto de mensagem classe de dispositivo R N D I S](./media/user-guide/usbx-events/image38.png)    | <span data-ttu-id="4e4bd-184">**Conjunto de mensagens Rndis classe de dispositivo** *(ux_device_class_rndis_msg_set)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-184">**Device Class Rndis Message Set** *(ux_device_class_rndis_msg_set)*</span></span> |
| ![Ícone de receção de pacote classe de dispositivo R N D I S](./media/user-guide/usbx-events/image39.png)    | <span data-ttu-id="4e4bd-186">**Pacote classe de dispositivo Rndis** *(ux_device_class_rndis_packet_receive)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-186">**Device Class Rndis Packet Receive** *(ux_device_class_rndis_packet_receive)*</span></span> |
| ![Ícone de transmissão de pacote de pacote classe R N D I I S](./media/user-guide/usbx-events/image40.png)    | <span data-ttu-id="4e4bd-188">**Dispositivo Classe Rndis Packet Transmit** *(ux_device_class_rndis_packet_transmit)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-188">**Device Class Rndis Packet Transmit** *(ux_device_class_rndis_packet_transmit)*</span></span> |
| ![Ícone ativar o armazenamento da classe do dispositivo](./media/user-guide/usbx-events/image41.png)    | <span data-ttu-id="4e4bd-190">**Ativar o armazenamento da classe do dispositivo** *(ux_device_class_storage_activate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-190">**Device Class Storage Activate** *(ux_device_class_storage_activate)*</span></span> |
| ![Ícone de desativação de classe de dispositivo](./media/user-guide/usbx-events/image42.png)    | <span data-ttu-id="4e4bd-192">**Desativação do armazenamento da classe do dispositivo** *(ux_device_class_storage_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-192">**Device Class Storage Deactivate** *(ux_device_class_storage_deactivate)*</span></span> |
| ![Ícone de formato de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image43.png)    | <span data-ttu-id="4e4bd-194">**Formato de armazenamento de classe de dispositivo** *(ux_device_class_storage_format)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-194">**Device Class Storage Format** *(ux_device_class_storage_format)*</span></span> |
| ![Ícone de inquérito de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image44.png)    | <span data-ttu-id="4e4bd-196">**Inquérito de armazenamento da classe do dispositivo** *(ux_device_class_storage_inquiry)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-196">**Device Class Storage Inquiry** *(ux_device_class_storage_inquiry)*</span></span> |
| ![Modo de armazenamento de classe de dispositivo Selecionar ícone](./media/user-guide/usbx-events/image45.png)    | <span data-ttu-id="4e4bd-198">**Selecione o modo de armazenamento da classe do dispositivo** *(ux_device_class_storage_mode_select)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-198">**Device Class Storage Mode Select** *(ux_device_class_storage_mode_select)*</span></span> |
| ![Ícone de sentido de modo de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image46.png)    | <span data-ttu-id="4e4bd-200">**Sentido do modo de armazenamento da classe do dispositivo** *(ux_device_class_storage_mode_sense)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-200">**Device Class Storage Mode Sense** *(ux_device_class_storage_mode_sense)*</span></span> |
| ![Armazenamento de classe de dispositivo Previne permitir ícone de remoção de mídia](./media/user-guide/usbx-events/image47.png)    | <span data-ttu-id="4e4bd-202">**Armazenamento da classe do dispositivo Previne a remoção dos meios** de comunicação *(ux_device_class_storage_prevent_allow_media_removal)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-202">**Device Class Storage Prevent Allow Media Removal** *(ux_device_class_storage_prevent_allow_media_removal)*</span></span> |
| ![Ícone de leitura de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image48.png)    | <span data-ttu-id="4e4bd-204">**Leitura de armazenamento da classe do dispositivo** *(ux_device_class_storage_read)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-204">**Device Class Storage Read** *(ux_device_class_storage_read)*</span></span> |
| ![Ícone de capacidade de leitura de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image49.png)    | <span data-ttu-id="4e4bd-206">**Capacidade de leitura de armazenamento de classe do dispositivo** *(ux_device_class_storage_read_capacity)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-206">**Device Class Storage Read Capacity** *(ux_device_class_storage_read_capacity)*</span></span> |
| ![Ícone de capacidade de leitura de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image50.png)    | <span data-ttu-id="4e4bd-208">**Capacidade de leitura do formato de leitura da classe do dispositivo** *(ux_device_class_storage_read_format_capacity)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-208">**Device Class Storage Read Format Capacity** *(ux_device_class_storage_read_format_capacity)*</span></span> |
| ![Armazenamento de classe de dispositivo Leia o ícone TOC](./media/user-guide/usbx-events/image51.png)    | <span data-ttu-id="4e4bd-210">**Armazenamento da classe do dispositivo Leia TOC** *(ux_device_class_storage_read_toc)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-210">**Device Class Storage Read TOC** *(ux_device_class_storage_read_toc)*</span></span> |
| ![Ícone de pedido de pedido de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image52.png)    | <span data-ttu-id="4e4bd-212">**Sentido do pedido de armazenamento da classe do dispositivo** *(ux_device_class_storage_request_sense)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-212">**Device Class Storage Request Sense** *(ux_device_class_storage_request_sense)*</span></span> |
| ![Ícone de início de paragem de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image53.png)    | <span data-ttu-id="4e4bd-214">**Paragem de início de armazenamento da classe do dispositivo** *(ux_device_class_storage_start_stop)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-214">**Device Class Storage Start Stop** *(ux_device_class_storage_start_stop)*</span></span> |
| ![Ícone de teste de armazenamento de classe de dispositivo pronto](./media/user-guide/usbx-events/image54.png)    | <span data-ttu-id="4e4bd-216">**Teste de armazenamento da classe do dispositivo pronto** *(ux_device_class_storage_test_ready)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-216">**Device Class Storage Test Ready** *(ux_device_class_storage_test_ready)*</span></span> |
| ![Ícone de verificação de classe de dispositivo](./media/user-guide/usbx-events/image55.png)    | <span data-ttu-id="4e4bd-218">**Verificação da classe do dispositivo** *(ux_device_class_storage_verify)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-218">**Device Class Storage Verify** *(ux_device_class_storage_verify)*</span></span> |
| ![Ícone de escrita de classe de dispositivo](./media/user-guide/usbx-events/image56.png)    | <span data-ttu-id="4e4bd-220">**Escrita de armazenamento de classe de dispositivo** *(ux_device_class_storage_write)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-220">**Device Class Storage Write** *(ux_device_class_storage_write)*</span></span> |
| ![Configuração alternativa de pilha de dispositivo Obter ícone](./media/user-guide/usbx-events/image57.png)    | <span data-ttu-id="4e4bd-222">**Configuração alternativa de pilha de dispositivo** *(ux_device_stack_alternate_setting_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-222">**Device Stack Alternate Setting Get** *(ux_device_stack_alternate_setting_get)*</span></span> |
| ![Ícone de definição alternativa de configuração de pilha de dispositivo](./media/user-guide/usbx-events/image58.png)    | <span data-ttu-id="4e4bd-224">**Conjunto de definição alternativa** de pilha de *dispositivo (ux_device_stack_alternate_setting_set)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-224">**Device Stack Alternate Setting Set** *(ux_device_stack_alternate_setting_set)*</span></span> |
| ![Ícone de registo de classe de pilha de dispositivo](./media/user-guide/usbx-events/image59.png)    | <span data-ttu-id="4e4bd-226">**Registo de classe de pilha de dispositivos** *(ux_device_stack_class_register)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-226">**Device Stack Class Register** *(ux_device_stack_class_register)*</span></span> |
| ![Ícone de funcionalidade de limpação de pilha de dispositivo](./media/user-guide/usbx-events/image60.png)    | <span data-ttu-id="4e4bd-228">**Recurso de segurança da pilha de dispositivo** *(ux_device_stack_clear_feature)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-228">**Device Stack Clear Feature** *(ux_device_stack_clear_feature)*</span></span> |
| ![Configuração de pilha de dispositivo Obter ícone](./media/user-guide/usbx-events/image61.png)    | <span data-ttu-id="4e4bd-230">**Configuração de pilha de dispositivo obter** *(ux_device_stack_configuration_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-230">**Device Stack Configuration Get** *(ux_device_stack_configuration_get)*</span></span> |
| ![Ícone de conjunto de configuração de pilha de dispositivo](./media/user-guide/usbx-events/image62.png)    | <span data-ttu-id="4e4bd-232">**Conjunto de configuração da pilha de** *dispositivo (ux_device_stack_configuration_set)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-232">**Device Stack Configuration Set** *(ux_device_stack_configuration_set)*</span></span> |
| ![Ícone de conexão de pilha de dispositivo](./media/user-guide/usbx-events/image63.png)    | <span data-ttu-id="4e4bd-234">**Ligação da pilha de dispositivos** *(ux_device_stack_connect)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-234">**Device Stack Connect** *(ux_device_stack_connect)*</span></span> |
| ![Descritor de pilha de dispositivo Enviar ícone](./media/user-guide/usbx-events/image64.png)    | <span data-ttu-id="4e4bd-236">**Envio de descritor de pilha de dispositivo** *(ux_device_stack_descriptor_send)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-236">**Device Stack Descriptor Send** *(ux_device_stack_descriptor_send)*</span></span> |
| ![Ícone de desconexão de pilha de dispositivo](./media/user-guide/usbx-events/image65.png)    | <span data-ttu-id="4e4bd-238">**Desconexão da pilha de dispositivos** *(ux_device_stack_disconnect)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-238">**Device Stack Disconnect** *(ux_device_stack_disconnect)*</span></span> |
| ![Ícone de ponto final de pilha de dispositivo](./media/user-guide/usbx-events/image66.png)    | <span data-ttu-id="4e4bd-240">**Dispositivo Stack Endpoint Stall** *(ux_device_stack_endpoint_stall)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-240">**Device Stack Endpoint Stall** *(ux_device_stack_endpoint_stall)*</span></span> |
| ![Ícone de estado da pilha de dispositivo](./media/user-guide/usbx-events/image67.png)    | <span data-ttu-id="4e4bd-242">**Estado de obter pilha de dispositivos** *(ux_device_stack_get_status)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-242">**Device Stack Get Status** *(ux_device_stack_get_status)*</span></span> |
| ![Ícone de wakeup do anfitrião do dispositivo stack](./media/user-guide/usbx-events/image68.png)    | <span data-ttu-id="4e4bd-244">**Wakeup do anfitrião do dispositivo** *stack (ux_device_stack_host_wakeup)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-244">**Device Stack Host Wakeup** *(ux_device_stack_host_wakeup)*</span></span> |
| ![Ícone inicialize da pilha de dispositivo](./media/user-guide/usbx-events/image69.png)    | <span data-ttu-id="4e4bd-246">**Stack de dispositivo Inicialize** *(ux_device_stack_initialize)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-246">**Device Stack Initialize** *(ux_device_stack_initialize)*</span></span> |
| ![Ícone de eliminação da interface da pilha de dispositivo](./media/user-guide/usbx-events/image70.png)    | <span data-ttu-id="4e4bd-248">**Eliminação da interface da pilha de dispositivos** *(ux_device_stack_interface_delete)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-248">**Device Stack Interface Delete** *(ux_device_stack_interface_delete)*</span></span> |
| ![Interface de pilha de dispositivo Obter ícone](./media/user-guide/usbx-events/image71.png)    | <span data-ttu-id="4e4bd-250">**Interface de pilha de dispositivo obter** *(ux_device_stack_interface_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-250">**Device Stack Interface Get** *(ux_device_stack_interface_get)*</span></span> |
| ![Ícone de conjunto de interface de pilha de dispositivo](./media/user-guide/usbx-events/image72.png)    | <span data-ttu-id="4e4bd-252">**Conjunto de interface de pilha de dispositivo** *(ux_device_stack_interface_set)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-252">**Device Stack Interface Set** *(ux_device_stack_interface_set)*</span></span> |
| ![Ícone de funcionalidade de conjunto de pilha de dispositivo](./media/user-guide/usbx-events/image73.png)    | <span data-ttu-id="4e4bd-254">**Função de conjunto de pilha de dispositivo** *(ux_device_stack_set_feature)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-254">**Device Stack Set Feature** *(ux_device_stack_set_feature)*</span></span> |
| ![Ícone de aborto de transferência de pilha de dispositivo](./media/user-guide/usbx-events/image74.png)    | <span data-ttu-id="4e4bd-256">**Abortar a transferência da pilha de dispositivos** *(ux_device_stack_transfer_abort)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-256">**Device Stack Transfer Abort** *(ux_device_stack_transfer_abort)*</span></span> |
| ![\*Transferência de pilha de dispositivo todo o ícone de abortar pedido](./media/user-guide/usbx-events/image75.png)    | <span data-ttu-id="4e4bd-258">**Transferência de pilha de dispositivos Todos os pedidos abortar** *(ux_device_stack_transfer_all_request_abort)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-258">**Device Stack Transfer All Request Abort** *(ux_device_stack_transfer_all_request_abort)*</span></span> |
| ![Ícone de pedido de transferência de pilha de dispositivo](./media/user-guide/usbx-events/image76.png)    | <span data-ttu-id="4e4bd-260">**Pedido de transferência de pilha de dispositivo** *(ux_device_stack_transfer_request)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-260">**Device Stack Transfer Request** *(ux_device_stack_transfer_request)*</span></span> |
| ![Ícone de ativação classe de anfitrião Asix](./media/user-guide/usbx-events/image77.png)    | <span data-ttu-id="4e4bd-262">**Classe de anfitrião Asix Ativar** *(ux_host_class_asix_activate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-262">**Host Class Asix Activate** *(ux_host_class_asix_activate)*</span></span> |
| ![Ícone de desativado classe anfitrião Asix](./media/user-guide/usbx-events/image78.png)    | <span data-ttu-id="4e4bd-264">**Classe hospedeira Desativado Asix** *(ux_host_class_asix_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-264">**Host Class Asix Deactivate** *(ux_host_class_asix_deactivate)*</span></span> |
| ![Ícone de notificação de interrupção de classe de anfitrião Asix](./media/user-guide/usbx-events/image79.png)    | <span data-ttu-id="4e4bd-266">**Aviso de interrupção da classe anfitrião Asix** *(ux_host_class_asix_interrupt_notification)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-266">**Host Class Asix Interrupt Notification** *(ux_host_class_asix_interrupt_notification)*</span></span> |
| ![Ícone de leitura de classe de anfitrião](./media/user-guide/usbx-events/image80.png)    | <span data-ttu-id="4e4bd-268">**Classe de anfitrião Asix Read** *(ux_host_class_asix_read)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-268">**Host Class Asix Read** *(ux_host_class_asix_read)*</span></span> |
| ![Ícone de escrita de classe de anfitrião Asix](./media/user-guide/usbx-events/image81.png)    | <span data-ttu-id="4e4bd-270">**Classe de anfitrião Asix Write** *(ux_host_class_asix_write)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-270">**Host Class Asix Write** *(ux_host_class_asix_write)*</span></span> |
| ![Ícone ativar áudio classe anfitrião](./media/user-guide/usbx-events/image82.png)    | <span data-ttu-id="4e4bd-272">**Ativação áudio da classe do anfitrião** *(ux_host_class_audio_activate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-272">**Host Class Audio Activate** *(ux_host_class_audio_activate)*</span></span> |
| ![Valor de controlo de áudio da classe do anfitrião Obter ícone](./media/user-guide/usbx-events/image83.png)    | <span data-ttu-id="4e4bd-274">**Valor de controlo de áudio da classe do anfitrião obter** *(ux_host_class_audio_control_value_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-274">**Host Class Audio Control Value Get** *(ux_host_class_audio_control_value_get)*</span></span> |
| ![Ícone do conjunto de conjunto de valor de controlo de áudio da classe do anfitrião](./media/user-guide/usbx-events/image84.png)    | <span data-ttu-id="4e4bd-276">**Conjunto de valor de controlo de áudio da classe do anfitrião** *(ux_host_class_audio_control_value_set)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-276">**Host Class Audio Control Value Set** *(ux_host_class_audio_control_value_set)*</span></span> |
| ![Ícone de desativado de áudio classe anfitrião](./media/user-guide/usbx-events/image85.png)    | <span data-ttu-id="4e4bd-278">**Desativar áudio da classe hospedeira** *(ux_host_class_audio_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-278">**Host Class Audio Deactivate** *(ux_host_class_audio_deactivate)*</span></span> |
| ![Ícone de leitura de áudio de classe de anfitrião](./media/user-guide/usbx-events/image86.png)    | <span data-ttu-id="4e4bd-280">**Leitura áudio da classe do anfitrião** *(ux_host_class_audio_read)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-280">**Host Class Audio Read** *(ux_host_class_audio_read)*</span></span> |
| ![Amostragem de streaming de áudio de classe de anfitrião Obter ícone](./media/user-guide/usbx-events/image87.png)    | <span data-ttu-id="4e4bd-282">**Amostragem de streaming de áudio de classe de anfitrião obter** *(ux_host_class_audio_streaming_sampling_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-282">**Host Class Audio Streaming Sampling Get** *(ux_host_class_audio_streaming_sampling_get)*</span></span> |
| ![Ícone do conjunto de amostragem de streaming de áudio da classe do anfitrião](./media/user-guide/usbx-events/image88.png)    | <span data-ttu-id="4e4bd-284">**Conjunto de amostragem de streaming de áudio de classe de anfitrião** *(ux_host_class_audio_streaming_sampling_set)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-284">**Host Class Audio Streaming Sampling Set** *(ux_host_class_audio_streaming_sampling_set)*</span></span> |
| ![Ícone de escrita de áudio de classe de anfitrião](./media/user-guide/usbx-events/image89.png)    | <span data-ttu-id="4e4bd-286">**Escrita áudio da classe hospedeira** *(ux_host_class_audio_write)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-286">**Host Class Audio Write** *(ux_host_class_audio_write)*</span></span> |
| ![Classe anfitrião C D C A C M Ícone ativado](./media/user-guide/usbx-events/image90.png)    | <span data-ttu-id="4e4bd-288">**Classe de anfitrião Cdc Acm Ativar** *(ux_host_class_cdc_acm_activate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-288">**Host Class Cdc Acm Activate** *(ux_host_class_cdc_acm_activate)*</span></span> |
| ![Ícone desativado classe C D C A C M](./media/user-guide/usbx-events/image91.png)    | <span data-ttu-id="4e4bd-290">**Classe anfitriã Cdc Acm Desativado** *(ux_host_class_cdc_acm_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-290">**Host Class Cdc Acm Deactivate** *(ux_host_class_cdc_acm_deactivate)*</span></span> |
| ![Classe anfitriã C D C A C M I O C T L No ícone do tubo](./media/user-guide/usbx-events/image92.png)    | <span data-ttu-id="4e4bd-292">**Classe de anfitrião Cdc Acm Ioctl Abortar em Tubo** *(ux_host_class_cdc_acm_ioctl_abort_in_pipe)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-292">**Host Class Cdc Acm Ioctl Abort In Pipe** *(ux_host_class_cdc_acm_ioctl_abort_in_pipe)*</span></span> |
| ![Classe anfitriã C D C A C M I O C T L AbortAr Ícone do Tubo](./media/user-guide/usbx-events/image93.png)    | <span data-ttu-id="4e4bd-294">**Classe anfitriã Cdc Acm Ioctl AbortAr Tubo** *(ux_host_class_cdc_acm_ioctl_abort_out_pipe)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-294">**Host Class Cdc Acm Ioctl Abort Out Pipe** *(ux_host_class_cdc_acm_ioctl_abort_out_pipe)*</span></span> |
| ![Classe hospedeira C D C A C M I O C T L Obter Ícone de Estado do Dispositivo](./media/user-guide/usbx-events/image94.png)    | <span data-ttu-id="4e4bd-296">**Classe de anfitrião Cdc Acm Ioctl Obter Estado do Dispositivo** *(ux_host_class_cdc_acm_ioctl_get_device_status)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-296">**Host Class Cdc Acm Ioctl Get Device Status** *(ux_host_class_cdc_acm_ioctl_get_device_status)*</span></span> |
| ![Classe anfitriã C D C A C M I O C T L Get Line Codificação](./media/user-guide/usbx-events/image95.png)    | <span data-ttu-id="4e4bd-298">**Classe de anfitrião Cdc Acm Ioctl Obter Codificação de Linha** *(ux_host_class_cdc_acm_ioctl_get_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-298">**Host Class Cdc Acm Ioctl Get Line Coding** *(ux_host_class_cdc_acm_ioctl_get_line_coding)*</span></span> |
| ![Classe anfitriã C D C A C M I O C T L Notification Callback](./media/user-guide/usbx-events/image96.png)    | <span data-ttu-id="4e4bd-300">**Chamada de notificação cdc Acm ioctl classe anfitrião** *(ux_host_class_cdc_acm_ioctl_notification_callback)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-300">**Host Class Cdc Acm Ioctl Notification Callback** *(ux_host_class_cdc_acm_ioctl_notification_callback)*</span></span> |
| ![Classe anfitriã C D C A C M I O C T L Enviar Ícone de rutura](./media/user-guide/usbx-events/image97.png)    | <span data-ttu-id="4e4bd-302">**Classe anfitriã Cdc Acm Ioctl Send Break** *(ux_host_class_cdc_acm_ioctl_send_break)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-302">**Host Class Cdc Acm Ioctl Send Break** *(ux_host_class_cdc_acm_ioctl_send_break)*</span></span> |
| ![Classe anfitriã C D C A C M I O C T L Definir Ícone de codificação](./media/user-guide/usbx-events/image98.png)    | <span data-ttu-id="4e4bd-304">**Classe de anfitrião Cdc Acm Ioctl set Line Code Codificação** *(ux_host_class_cdc_acm_ioctl_set_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-304">**Host Class Cdc Acm Ioctl Set Line Coding** *(ux_host_class_cdc_acm_ioctl_set_line_coding)*</span></span> |
| ![Classe anfitriã C D C A C A C M I O C T L set Line State ícone](./media/user-guide/usbx-events/image99.png)    | <span data-ttu-id="4e4bd-306">**Classe anfitrião Cdc Acm Ioctl set Line State** *(ux_host_class_cdc_acm_ioctl_set_line_state)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-306">**Host Class Cdc Acm Ioctl Set Line State** *(ux_host_class_cdc_acm_ioctl_set_line_state)*</span></span> |
| ![Ícone de leitura classe C D C A C M](./media/user-guide/usbx-events/image100.png)    | <span data-ttu-id="4e4bd-308">**Classe de anfitrião Cdc Acm Read** *(ux_host_class_cdc_acm_read)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-308">**Host Class Cdc Acm Read** *(ux_host_class_cdc_acm_read)*</span></span> |
| ![Classe anfitrião C D C A C M Receção Ícone de início](./media/user-guide/usbx-events/image101.png)    | <span data-ttu-id="4e4bd-310">**Início de receção cdc Acm classe anfitrião** *(ux_host_class_cdc_acm_reception_start)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-310">**Host Class Cdc Acm Reception Start** *(ux_host_class_cdc_acm_reception_start)*</span></span> |
| ![Classe anfitrião C D C A C C M Ícone de paragem de receção](./media/user-guide/usbx-events/image102.png)    | <span data-ttu-id="4e4bd-312">**Paragem de receção cdc Acm classe anfitrião** *(ux_host_class_cdc_acm_reception_stop)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-312">**Host Class Cdc Acm Reception Stop** *(ux_host_class_cdc_acm_reception_stop)*</span></span> |
| ![Ícone de escrita classe de anfitrião C D C A C M](./media/user-guide/usbx-events/image103.png)    | <span data-ttu-id="4e4bd-314">**Classe anfitriã Cdc Acm Write** *(ux_host_class_cdc_acm_write)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-314">**Host Class Cdc Acm Write** *(ux_host_class_cdc_acm_write)*</span></span> |
| ![Ícone ativar classe de anfitrião](./media/user-guide/usbx-events/image104.png)    | <span data-ttu-id="4e4bd-316">**Classe de anfitrião Dpump Ativar** *(ux_host_class_dpump_activate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-316">**Host Class Dpump Activate** *(ux_host_class_dpump_activate)*</span></span> |
| ![Ícone de desativado classe de anfitrião Dpump](./media/user-guide/usbx-events/image105.png)    | <span data-ttu-id="4e4bd-318">**Classe anfitriã Dpump Desativado** *(ux_host_class_dpump_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-318">**Host Class Dpump Deactivate** *(ux_host_class_dpump_deactivate)*</span></span> |
| ![Ícone de leitura de classe de anfitrião](./media/user-guide/usbx-events/image106.png)    | <span data-ttu-id="4e4bd-320">**Leitura de Dpump de Classe anfitriã** *(ux_host_class_dpump_read)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-320">**Host Class Dpump Read** *(ux_host_class_dpump_read)*</span></span> |
| ![Ícone de escrita de classe de anfitrião](./media/user-guide/usbx-events/image107.png)    | <span data-ttu-id="4e4bd-322">**Escrita de Classe Anfitriã Dpump** *(ux_host_class_dpump_write)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-322">**Host Class Dpump Write** *(ux_host_class_dpump_write)*</span></span> |
| ![Ícone ativar classe de anfitrião Hid](./media/user-guide/usbx-events/image108.png)    | <span data-ttu-id="4e4bd-324">**Classe de anfitrião Hid Activate** *(ux_host_class_hid_activate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-324">**Host Class Hid Activate** *(ux_host_class_hid_activate)*</span></span> |
| ![Ícone de registo de clientes de classe de anfitrião](./media/user-guide/usbx-events/image109.png)    | <span data-ttu-id="4e4bd-326">**Registo de clientes hid da classe de anfitrião** *(ux_host_class_hid_client_register)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-326">**Host Class Hid Client Register** *(ux_host_class_hid_client_register)*</span></span> |
| ![Ícone de desativado classe de anfitrião Hid](./media/user-guide/usbx-events/image110.png)    | <span data-ttu-id="4e4bd-328">**Classe de anfitrião Hid Desativado** *(ux_host_class_hid_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-328">**Host Class Hid Deactivate** *(ux_host_class_hid_deactivate)*</span></span> |
| ![Classe de anfitrião Hid Idle Obter ícone](./media/user-guide/usbx-events/image111.png)    | <span data-ttu-id="4e4bd-330">**Classe de anfitrião Hid Idle Get** *(ux_host_class_hid_idle_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-330">**Host Class Hid Idle Get** *(ux_host_class_hid_idle_get)*</span></span> |
| ![Ícone de conjunto de conjunto de classe de anfitrião hid ocioso](./media/user-guide/usbx-events/image112.png)    | <span data-ttu-id="4e4bd-332">**Conjunto de idle de classe de anfitrião** *(ux_host_class_hid_idle_set)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-332">**Host Class Hid Idle Set** *(ux_host_class_hid_idle_set)*</span></span> |
| ![Ícone ativar teclado de classe de anfitrião](./media/user-guide/usbx-events/image113.png)    | <span data-ttu-id="4e4bd-334">**Classe de anfitrião Hid Keyboard Activate** *(ux_host_class_hid_keyboard_activate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-334">**Host Class Hid Keyboard Activate** *(ux_host_class_hid_keyboard_activate)*</span></span> |
| ![Ícone de desativado do teclado da classe anfitrião Hid](./media/user-guide/usbx-events/image114.png)    | <span data-ttu-id="4e4bd-336">**Classe de anfitrião Hid Keyboard Desativado** *(ux_host_class_hid_keyboard_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-336">**Host Class Hid Keyboard Deactivate** *(ux_host_class_hid_keyboard_deactivate)*</span></span> |
| ![Ícone ativar rato de classe de anfitrião](./media/user-guide/usbx-events/image115.png)    | <span data-ttu-id="4e4bd-338">**Classe de anfitrião Hid Mouse Activate** *(ux_host_class_hid_mouse_activate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-338">**Host Class Hid Mouse Activate** *(ux_host_class_hid_mouse_activate)*</span></span> |
| ![Ícone de desativado do rato da classe do anfitrião](./media/user-guide/usbx-events/image116.png)    | <span data-ttu-id="4e4bd-340">**Classe de anfitrião Hid Mouse Desativado** *(ux_host_class_hid_mouse_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-340">**Host Class Hid Mouse Deactivate** *(ux_host_class_hid_mouse_deactivate)*</span></span> |
| ![Classe de anfitrião hid remote controle ícone ativar](./media/user-guide/usbx-events/image117.png)    | <span data-ttu-id="4e4bd-342">**Classe de anfitrião Hid Controlo Remoto Ativado** *(ux_host_class_hid_remote_control_activate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-342">**Host Class Hid Remote Control Activate** *(ux_host_class_hid_remote_control_activate)*</span></span> |
| ![Classe de anfitrião hid remote control desativado ícone](./media/user-guide/usbx-events/image118.png)    | <span data-ttu-id="4e4bd-344">**Classe de anfitrião Hid Controlo Remoto Desativado** *(ux_host_class_hid_remote_control_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-344">**Host Class Hid Remote Control Deactivate** *(ux_host_class_hid_remote_control_deactivate)*</span></span> |
| ![Relatório hid classe anfitrião Obter ícone](./media/user-guide/usbx-events/image119.png)    | <span data-ttu-id="4e4bd-346">**Relatório hid da classe de anfitrião obter** *(ux_host_class_hid_report_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-346">**Host Class Hid Report Get** *(ux_host_class_hid_report_get)*</span></span> |
| ![Ícone de conjunto de relatório de classe de anfitrião hid](./media/user-guide/usbx-events/image120.png)    | <span data-ttu-id="4e4bd-348">**Conjunto de relatórios de classe de anfitrião** *(ux_host_class_hid_report_set)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-348">**Host Class Hid Report Set** *(ux_host_class_hid_report_set)*</span></span> |
| ![Ícone ativar o centro de classe do anfitrião](./media/user-guide/usbx-events/image121.png)    | <span data-ttu-id="4e4bd-350">**Centro de classe de anfitrião Ativado** *(ux_host_class_hub_activate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-350">**Host Class Hub Activate** *(ux_host_class_hub_activate)*</span></span> |
| ![Ícone de deteção de mudança de centro de classe de anfitrião](./media/user-guide/usbx-events/image122.png)    | <span data-ttu-id="4e4bd-352">**Deteção de mudança de centro de classe de anfitrião** *(ux_host_class_hub_change_detect)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-352">**Host Class Hub Change Detect** *(ux_host_class_hub_change_detect)*</span></span> |
| ![\*Ícone de desativar o hub da classe anfitrião](./media/user-guide/usbx-events/image123.png)    | <span data-ttu-id="4e4bd-354">**Desativar o Hub de Classe hospedeira** *(ux_host_class_hub_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-354">**Host Class Hub Deactivate** *(ux_host_class_hub_deactivate)*</span></span> |
| ![Ícone do processo de mudança de ligação do hub da classe do anfitrião](./media/user-guide/usbx-events/image124.png)    | <span data-ttu-id="4e4bd-356">**Processo de mudança de porta do hub de classe do anfitrião** *(ux_host_class_hub_port_change_connection_process)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-356">**Host Class Hub Port Change Connection Process** *(ux_host_class_hub_port_change_connection_process)*</span></span> |
| ![Ícone de mudança de carro do hub de classe de anfitrião](./media/user-guide/usbx-events/image125.png)    | <span data-ttu-id="4e4bd-358">**Processo de ativação de mudança de porta do hub de classe de anfitrião** *(ux_host_class_hub_port_change_enable_process)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-358">**Host Class Hub Port Change Enable Process** *(ux_host_class_hub_port_change_enable_process)*</span></span> |
| ![Mudança de porta do hub do anfitrião sobre o ícone do processo atual](./media/user-guide/usbx-events/image126.png)    | <span data-ttu-id="4e4bd-360">**Mudança de porta do hub de classe de anfitrião sobre o processo atual** *(ux_host_class_hub_port_change_over_current_process)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-360">**Host Class Hub Port Change Over Current Process** *(ux_host_class_hub_port_change_over_current_process)*</span></span> |
| ![Ícone do processo de reposição do processo de mudança de porta do hub da classe do anfitrião](./media/user-guide/usbx-events/image127.png)    | <span data-ttu-id="4e4bd-362">Processo de reset da **parte do centro da parte do anfitrião** *(ux_host_class_hub_port_change_reset_process)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-362">**Host Class Hub Port Change Reset Process** *(ux_host_class_hub_port_change_reset_process)*</span></span> |
| ![Ícone de processo de suspensão de mudança de porta do hub de classe de anfitrião](./media/user-guide/usbx-events/image128.png)    | <span data-ttu-id="4e4bd-364">**Processo de suspensão da suspensão do porto do hub da classe de anfitrião** *(ux_host_class_hub_port_change_suspend_process)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-364">**Host Class Hub Port Change Suspend Process** *(ux_host_class_hub_port_change_suspend_process)*</span></span> |
| ![Ícone de ativação classe de anfitrião Pima](./media/user-guide/usbx-events/image129.png)    | <span data-ttu-id="4e4bd-366">**Classe de anfitrião Pima Ativar** *(ux_host_class_prima_activate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-366">**Host Class Pima Activate** *(ux_host_class_prima_activate)*</span></span> |
| ![Ícone de desativado classe de anfitrião Pima](./media/user-guide/usbx-events/image130.png)    | <span data-ttu-id="4e4bd-368">**Classe anfitriã Pima Desativado** *(ux_host_class_pima_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-368">**Host Class Pima Deactivate** *(ux_host_class_pima_deactivate)*</span></span> |
| ![Classe anfitrião Pima Device Info Obter ícone](./media/user-guide/usbx-events/image131.png)    | <span data-ttu-id="4e4bd-370">**Informações do dispositivo Pima da classe anfitriã** *(ux_host_class_pima_device_info_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-370">**Host Class Pima Device Info Get** *(ux_host_class_pima_device_info_get)*</span></span> |
| ![Ícone de reset do dispositivo Pima da classe anfitrião](./media/user-guide/usbx-events/image132.png)    | <span data-ttu-id="4e4bd-372">**Reset do dispositivo Pima da classe de anfitrião** *(ux_host_class_pima_device_reset)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-372">**Host Class Pima Device Reset** *(ux_host_class_pima_device_reset)*</span></span> |
| ![Ícone de notificação Pima classe anfitrião](./media/user-guide/usbx-events/image133.png)    | <span data-ttu-id="4e4bd-374">**Notificação Pima classe anfitrião** *(ux_host_class_pima_notification)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-374">**Host Class Pima Notification** *(ux_host_class_pima_notification)*</span></span> |
| ![Objetos de número pima classe anfitrião obter ícone](./media/user-guide/usbx-events/image134.png)    | <span data-ttu-id="4e4bd-376">**Objetos de número pima classe anfitrião obtêm** *(ux_host_class_pima_num_objects_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-376">**Host Class Pima Number Objects Get** *(ux_host_class_pima_num_objects_get)*</span></span> |
| ![Ícone de fecho de objeto pima classe anfitrião](./media/user-guide/usbx-events/image135.png)    | <span data-ttu-id="4e4bd-378">**Classe anfitrião Pima Objeto Perto** *(ux_host_class_pima_object_close)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-378">**Host Class Pima Object Close** *(ux_host_class_pima_object_close)*</span></span> |
| ![Ícone de cópia de objeto de classe de anfitrião Pima](./media/user-guide/usbx-events/image136.png)    | <span data-ttu-id="4e4bd-380">**Cópia do objeto Pima da classe anfitriã** *(ux_host_class_pima_object_copy)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-380">**Host Class Pima Object Copy** *(ux_host_class_pima_object_copy)*</span></span> |
| ![Ícone de exclusão de objeto pima classe anfitrião](./media/user-guide/usbx-events/image137.png)    | <span data-ttu-id="4e4bd-382">**Classe anfitrião Pima Object Delete** *(ux_host_class_pima_object_delete)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-382">**Host Class Pima Object Delete** *(ux_host_class_pima_object_delete)*</span></span> |
| ![Classe anfitrião Pima Objeto Obter ícone](./media/user-guide/usbx-events/image138.png)    | <span data-ttu-id="4e4bd-384">**Anfitrião Classe Pima Objeto Obter** *(ux_host_class_pima_object_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-384">**Host Class Pima Object Get** *(ux_host_class_pima_object_get)*</span></span> |
| ![Classe anfitrião Pima Objeto Info Obter ícone](./media/user-guide/usbx-events/image139.png)    | <span data-ttu-id="4e4bd-386">**Host Class Pima Object Info Get** *(ux_host_class_pima_object_info_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-386">**Host Class Pima Object Info Get** *(ux_host_class_pima_object_info_get)*</span></span> |
| ![Classe anfitrião Pima Objeto Info Enviar ícone](./media/user-guide/usbx-events/image140.png)    | <span data-ttu-id="4e4bd-388">**Informações de objeto pima classe anfitrião Enviar** *(ux_host_class_pima_object_info_send)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-388">**Host Class Pima Object Info Send** *(ux_host_class_pima_object_info_send)*</span></span> |
| ![Ícone de movimento de objeto de classe de anfitrião Pima](./media/user-guide/usbx-events/image141.png)    | <span data-ttu-id="4e4bd-390">**Movimento de objeto classe anfitrião Pima** *(ux_host_class_pima_object_move)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-390">**Host Class Pima Object Move** *(ux_host_class_pima_object_move)*</span></span> |
| ![Ícone de envio de objeto pima classe anfitrião](./media/user-guide/usbx-events/image142.png)    | <span data-ttu-id="4e4bd-392">**Envio de objeto classe de anfitrião Pima** *(ux_host_class_pima_object_send)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-392">**Host Class Pima Object Send** *(ux_host_class_pima_object_send)*</span></span> |
| ![Ícone de aborto de transferência de objeto de classe Pima de anfitrião](./media/user-guide/usbx-events/image143.png)    | <span data-ttu-id="4e4bd-394">**Aborto de transferência de objetos Pima classe anfitrião** *(ux_host_class_object_transfer_abort)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-394">**Host Class Pima Object Transfer Abort** *(ux_host_class_object_transfer_abort)*</span></span> |
| ![Ícone de leitura de classe de anfitrião Pima](./media/user-guide/usbx-events/image144.png)    | <span data-ttu-id="4e4bd-396">**Classe de Anfitrião Pima Read** *(ux_host_class_pima_read)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-396">**Host Class Pima Read** *(ux_host_class_pima_read)*</span></span> |
| ![Classe anfitrião Pima Request Cancel ícone](./media/user-guide/usbx-events/image145.png)    | <span data-ttu-id="4e4bd-398">**Cancelamento de pedido de classe de anfitrião Pima** *(ux_host_class_pima_request_cancel)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-398">**Host Class Pima Request Cancel** *(ux_host_class_pima_request_cancel)*</span></span> |
| ![Ícone de fecho de sessão pima de classe de anfitrião](./media/user-guide/usbx-events/image146.png)    | <span data-ttu-id="4e4bd-400">**Sessão Pima de anfitrião** *(ux_host_class_pima_session_close)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-400">**Host Class Pima Session Close** *(ux_host_class_pima_session_close)*</span></span> |
| ![Ícone do open da sessão pima de classe de anfitrião](./media/user-guide/usbx-events/image147.png)    | <span data-ttu-id="4e4bd-402">**Host Class Pima Session Open** *(ux_host_class_pima_session_open)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-402">**Host Class Pima Session Open** *(ux_host_class_pima_session_open)*</span></span> |
| ![Classe anfitrião Pima Storage Ids Obter ícone](./media/user-guide/usbx-events/image148.png)    | <span data-ttu-id="4e4bd-404">**Anfitriões Classe Pima Storage Ids Get** *(ux_host_class_pima_storage_ids_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-404">**Host Class Pima Storage Ids Get** *(ux_host_class_pima_storage_ids_get)*</span></span> |
| ![Classe anfitrião Pima Storage Info Obter ícone](./media/user-guide/usbx-events/image149.png)    | <span data-ttu-id="4e4bd-406">**Informações de armazenamento Pima da classe anfitriã** *(ux_host_class_pima_storage_info_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-406">**Host Class Pima Storage Info Get** *(ux_host_class_pima_storage_info_get)*</span></span> |
| ![Ícone de polegar Pima de classe de anfitrião](./media/user-guide/usbx-events/image150.png)    | <span data-ttu-id="4e4bd-408">**Classe anfitrião Pima Polegar Get** *(ux_host_class_pima_thumb_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-408">**Host Class Pima Thumb Get** *(ux_host_class_pima_thumb_get)*</span></span> |
| ![Ícone de escrita classe de anfitrião Pima](./media/user-guide/usbx-events/image151.png)    | <span data-ttu-id="4e4bd-410">**Classe anfitriã Pima Write** *(ux_host_class_pima_write)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-410">**Host Class Pima Write** *(ux_host_class_pima_write)*</span></span> |
| ![Ícone ativar impressora de classe de anfitrião](./media/user-guide/usbx-events/image152.png)    | <span data-ttu-id="4e4bd-412">**Impressora de classe de anfitrião Ativada** *(ux_host_class_printer_activate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-412">**Host Class Printer Activate** *(ux_host_class_printer_activate)*</span></span> |
| ![Ícone de desativar impressora de classe de anfitrião](./media/user-guide/usbx-events/image153.png)    | <span data-ttu-id="4e4bd-414">**Impressora de classe de anfitrião desativar** *(ux_host_class_printer_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-414">**Host Class Printer Deactivate** *(ux_host_class_printer_deactivate)*</span></span> |
| ![Nome da impressora de classe anfitrião obter ícone](./media/user-guide/usbx-events/image154.png)    | <span data-ttu-id="4e4bd-416">**Nome da impressora de classe de anfitrião obter** *(ux_host_class_printer_name_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-416">**Host Class Printer Name Get** *(ux_host_class_printer_name_get)*</span></span> |
| ![Ícone de leitura de impressora de classe de anfitrião](./media/user-guide/usbx-events/image155.png)    |  <span data-ttu-id="4e4bd-418">**Leitura da impressora da classe do anfitrião** *(ux_host_class_printer_read)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-418">**Host Class Printer Read** *(ux_host_class_printer_read)*</span></span> |
| ![Ícone de reset suave da impressora de classe de anfitrião](./media/user-guide/usbx-events/image156.png)    | <span data-ttu-id="4e4bd-420">**Reset suave da impressora de classe de anfitrião** *(ux_host_class_printer_soft_reset)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-420">**Host Class Printer Soft Reset** *(ux_host_class_printer_soft_reset)*</span></span> |
| ![Estado da impressora de classe de anfitrião Obter ícone](./media/user-guide/usbx-events/image157.png)    | <span data-ttu-id="4e4bd-422">**Estado da impressora de classe de anfitrião obter** *(ux_host_class_printer_status_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-422">**Host Class Printer Status Get** *(ux_host_class_printer_status_get)*</span></span> |
| ![Ícone de escrita de impressora de classe de anfitrião](./media/user-guide/usbx-events/image158.png)    | <span data-ttu-id="4e4bd-424">**Escrita de impressora de classe de anfitrião** *(ux_host_class_printer_write)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-424">**Host Class Printer Write** *(ux_host_class_printer_write)*</span></span> |
| ![Ícone de ativação prolific de classe de anfitrião](./media/user-guide/usbx-events/image159.png)    | <span data-ttu-id="4e4bd-426">**Ativação Prolific classe de anfitrião** *(ux_host_class_prolific_activate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-426">**Host Class Prolific Activate** *(ux_host_class_prolific_activate)*</span></span> |
| ![Ícone prolífico da classe de anfitrião](./media/user-guide/usbx-events/image160.png)    | <span data-ttu-id="4e4bd-428">**Classe de anfitrião Prolific Desativado** *(ux_host_class_prolific_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-428">**Host Class Prolific Deactivate** *(ux_host_class_prolific_deactivate)*</span></span> |
| ![Classe de anfitrião Prolific I O C T T L Abortar no ícone do tubo](./media/user-guide/usbx-events/image161.png)    | <span data-ttu-id="4e4bd-430">**Classe de anfitrião Prolific Ioctl Abort in Pipe** *(ux_host_class_prolific_ioctl_abort_in_pipe)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-430">**Host Class Prolific Ioctl Abort In Pipe** *(ux_host_class_prolific_ioctl_abort_in_pipe)*</span></span> |
| ![Classe de anfitrião Prolific I O C T L AbortAr Ícone do Tubo](./media/user-guide/usbx-events/image162.png)    | <span data-ttu-id="4e4bd-432">**Classe de anfitrião Prolific Ioctl AbortAr Tubo** *(ux_host_class_prolific_ioctl_abort_out_pipe)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-432">**Host Class Prolific Ioctl Abort Out Pipe** *(ux_host_class_prolific_ioctl_abort_out_pipe)*</span></span> |
| ![Classe de anfitrião Prolific I O C T L Obter Ícone de Estado do Dispositivo](./media/user-guide/usbx-events/image163.png)    | <span data-ttu-id="4e4bd-434">**Classe de anfitrião Prolific Ioctl Obter Estado do Dispositivo** *(ux_host_class_prolific_ioctl_get_device_status)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-434">**Host Class Prolific Ioctl Get Device Status** *(ux_host_class_prolific_ioctl_get_device_status)*</span></span> |
| ![Classe de anfitrião Prolific I O C T L Obter Ícone de codificação de linha](./media/user-guide/usbx-events/image164.png)    | <span data-ttu-id="4e4bd-436">**Classe de anfitrião Prolific Ioctl Get Line Coding** *(ux_host_class_prolific_ioctl_get_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-436">**Host Class Prolific Ioctl Get Line Coding** *(ux_host_class_prolific_ioctl_get_line_coding)*</span></span> |
| ![Ícone de purga de classe de anfitrião I O C T L](./media/user-guide/usbx-events/image165.png)    | <span data-ttu-id="4e4bd-438">**Classe de anfitrião Prolific Ioctl Purga** *(ux_host_class_prolific_ioctl_purge)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-438">**Host Class Prolific Ioctl Purge** *(ux_host_class_prolific_ioctl_purge)*</span></span> |
| ![Ícone de alteração de estado do dispositivo de mudança de dispositivo de classe de anfitrião I O C T L](./media/user-guide/usbx-events/image166.png)    | <span data-ttu-id="4e4bd-440">Mudança de estado do dispositivo de **relatório prolific da classe de anfitrião** *(ux_host_class_prolific_ioctl_report_device_status_change)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-440">**Host Class Prolific Ioctl Report Device Status Change** *(ux_host_class_prolific_ioctl_report_device_status_change)*</span></span> |
| ![Classe de anfitrião Prolific I O C T L Enviar Ícone de rutura](./media/user-guide/usbx-events/image167.png)    | <span data-ttu-id="4e4bd-442">**Classe de anfitrião Prolific Ioctl Send Break** *(ux_host_class_prolific_ioctl_send_break)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-442">**Host Class Prolific Ioctl Send Break** *(ux_host_class_prolific_ioctl_send_break)*</span></span> |
| ![Ícone de codificação de linha de classe de anfitrião I O C T L](./media/user-guide/usbx-events/image168.png)    | <span data-ttu-id="4e4bd-444">**Codificação de linha de conjunto de conjunto prolific da classe de anfitrião** *(ux_host_class_prolific_ioctl_set_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-444">**Host Class Prolific Ioctl Set Line Coding** *(ux_host_class_prolific_ioctl_set_line_coding)*</span></span> |
| ![Classe de anfitrião Prolific I O C T L set Line State ícone](./media/user-guide/usbx-events/image169.png)    | <span data-ttu-id="4e4bd-446">**Classe de anfitrião Prolific Ioctl set Line State** *(ux_host_class_prolific_ioctl_set_line_state)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-446">**Host Class Prolific Ioctl Set Line State** *(ux_host_class_prolific_ioctl_set_line_state)*</span></span> |
| ![Ícone de leitura prolífica de classe de anfitrião](./media/user-guide/usbx-events/image170.png)    | <span data-ttu-id="4e4bd-448">**Leitura Prolífica da Classe anfitriã** *(ux_host_class_prolific_read)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-448">**Host Class Prolific Read** *(ux_host_class_prolific_read)*</span></span> |
| ![Ícone de início de receção prolific de classe de anfitrião](./media/user-guide/usbx-events/image171.png)    | <span data-ttu-id="4e4bd-450">**Início de receção prolific da classe anfitriã** *(ux_host_class_prolific_reception_start)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-450">**Host Class Prolific Reception Start** *(ux_host_class_prolific_reception_start)*</span></span> |
| ![Ícone de paragem de receção prolific de classe de anfitrião](./media/user-guide/usbx-events/image172.png)    | <span data-ttu-id="4e4bd-452">**Paragem de receção prolific da classe anfitriã** *(ux_host_class_prolific_reception_stop)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-452">**Host Class Prolific Reception Stop** *(ux_host_class_prolific_reception_stop)*</span></span> |
| ![Ícone de escrita prolific classe de anfitrião](./media/user-guide/usbx-events/image173.png)    | <span data-ttu-id="4e4bd-454">**Escrita Prolific classe de anfitrião** *(ux_host_class_prolific_write)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-454">**Host Class Prolific Write** *(ux_host_class_prolific_write)*</span></span> |
| ![Ícone ativar o armazenamento da classe do anfitrião](./media/user-guide/usbx-events/image174.png)    | <span data-ttu-id="4e4bd-456">**Ativar o armazenamento da classe do anfitrião** *(ux_host_class_storage_activate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-456">**Host Class Storage Activate** *(ux_host_class_storage_activate)*</span></span> |
| ![Ícone de desativação de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image175.png)    | <span data-ttu-id="4e4bd-458">**Desativação do armazenamento da classe hospedeira** *(ux_host_class_storage_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-458">**Host Class Storage Deactivate** (*ux_host_class_storage_deactivate)*</span></span> |
| ![Classe anfitrião armazenamento capacidade de mídia obter ícone](./media/user-guide/usbx-events/image176.png)    | <span data-ttu-id="4e4bd-460">**Capacidade de mídia de armazenamento de classe de anfitrião obter** *(ux_host_class_storage_media_capacity_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-460">**Host Class Storage Media Capacity Get** *(ux_host_class_storage_media_capacity_get)*</span></span> |
| ![Grupo de anfitrião armazenamento de armazenamento de capacidade obter ícone](./media/user-guide/usbx-events/image177.png)    | <span data-ttu-id="4e4bd-462">**Capacidade de formato de mídia de armazenamento de classe de anfitrião obter** *(ux_host_class_storage_media_format_capacity_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-462">**Host Class Storage Media Format Capacity Get** *(ux_host_class_storage_media_format_capacity_get)*</span></span> |
| ![Ícone de montagem de mídia de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image178.png)    | <span data-ttu-id="4e4bd-464">**Montagem de mídia de armazenamento de classe de anfitrião** (ux_host_class_storage_media_mount)\*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-464">**Host Class Storage Media Mount** (ux_host_class_storage_media_mount)\*</span></span> |
| ![Ícone de mídia de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image179.png)    | <span data-ttu-id="4e4bd-466">**Classe de anfitrião Armazenamento Media Open** *(ux_host_class_storage_media_open)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-466">**Host Class Storage Media Open** *(ux_host_class_storage_media_open)*</span></span> |
| ![Ícone de leitura de mídia de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image180.png)    | <span data-ttu-id="4e4bd-468">**Leitura de mídia de armazenamento de classe de anfitrião** *(ux_host_class_storage_media_read)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-468">**Host Class Storage Media Read** *(ux_host_class_storage_media_read)*</span></span> |
| ![Ícone de mídia de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image181.png)    | <span data-ttu-id="4e4bd-470">**Escrita de mídia de armazenamento de classe de anfitrião** *(ux_host_class_storage_media_write)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-470">**Host Class Storage Media Write** *(ux_host_class_storage_media_write)*</span></span> |
| ![Ícone de pedido de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image182.png)    | <span data-ttu-id="4e4bd-472">**Sentido do pedido de armazenamento da classe de anfitrião** *(ux_host_class_storage_request_sense)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-472">**Host Class Storage Request Sense** *(ux_host_class_storage_request_sense)*</span></span> |
| ![Ícone de paragem de início de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image183.png)    | <span data-ttu-id="4e4bd-474">**Paragem de início de armazenamento de classe de anfitrião** *(ux_host_class_storage_start_stop)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-474">**Host Class Storage Start Stop** *(ux_host_class_storage_start_stop)*</span></span> |
| ![Ícone de teste pronto da unidade de armazenamento da classe do anfitrião](./media/user-guide/usbx-events/image184.png)    | <span data-ttu-id="4e4bd-476">**Teste pronto da unidade de armazenamento da unidade de armazenamento da classe de anfitrião** *(ux_host_class_storage_activate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-476">**Host Class Storage Unit Ready Test** *(ux_host_class_storage_activate)*</span></span> |
| ![Série de anfitrião exemplo criar ícone](./media/user-guide/usbx-events/image185.png)    | <span data-ttu-id="4e4bd-478">**Série de anfitrião Classe De Exemplo Criar** *(ux_host_stack_class_instance_create)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-478">**Host Stack Class Instance Create** *(ux_host_stack_class_instance_create)*</span></span> |
| ![Ícone de destruição de classe de classe de pilha de anfitrião](./media/user-guide/usbx-events/image186.png)    | <span data-ttu-id="4e4bd-480">**Exemplo de classe de pilha de anfitrião destruir** *(ux_host_stack_class_instance_destroy)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-480">**Host Stack Class Instance Destroy** *(ux_host_stack_class_instance_destroy)*</span></span> |
| ![Ícone de configuração de pilha de anfitrião Eliminar](./media/user-guide/usbx-events/image187.png)    | <span data-ttu-id="4e4bd-482">**Configuração de pilha de anfitrião Eliminar** *(ux_host_stack_configuration_delete)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-482">**Host Stack Configuration Delete** *(ux_host_stack_configuration_delete)*</span></span> |
| ![Ícone de enumeração de configuração de pilha de anfitrião](./media/user-guide/usbx-events/image188.png)    | <span data-ttu-id="4e4bd-484">**Enumeração de configuração da pilha de anfitrião** *(ux_host_stack_configuration_enumerate)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-484">**Host Stack Configuration Enumerate** *(ux_host_stack_configuration_enumerate)*</span></span> |
| ![Exemplo de configuração de pilha de anfitrião Criar ícone](./media/user-guide/usbx-events/image189.png)    | <span data-ttu-id="4e4bd-486">**Série de configuração do anfitrião Criar** *(ux_host_stack_configuration_instance_create)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-486">**Host Stack Configuration Instance Create** *(ux_host_stack_configuration_instance_create)*</span></span> |
| ![Exemplo de configuração de pilha de anfitrião Eliminar ícone](./media/user-guide/usbx-events/image190.png)    | <span data-ttu-id="4e4bd-488">**Exemplo de configuração da pilha de anfitrião Eliminar** *(ux_host_stack_configuration_instance_delete)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-488">**Host Stack Configuration Instance Delete** *(ux_host_stack_configuration_instance_delete)*</span></span> |
| ![Ícone de conjunto de configuração de pilha de anfitrião](./media/user-guide/usbx-events/image191.png)    | <span data-ttu-id="4e4bd-490">**Conjunto de configuração da pilha de** *anfitrião (ux_host_stack_configuration_set)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-490">**Host Stack Configuration Set** *(ux_host_stack_configuration_set)*</span></span> |
| ![Ícone de conjunto de endereço de dispositivo de pilha de anfitrião](./media/user-guide/usbx-events/image192.png)    | <span data-ttu-id="4e4bd-492">**Conjunto de endereços do dispositivo de pilha de anfitrião** *(ux_host_stack_device_set)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-492">**Host Stack Device Address Set** *(ux_host_stack_device_set)*</span></span> |
| ![Configuração do dispositivo de pilha de anfitrião Obter ícone](./media/user-guide/usbx-events/image193.png)    | <span data-ttu-id="4e4bd-494">**Configuração do dispositivo de pilha de anfitrião obter** *(ux_host_stack_device_configuration_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-494">**Host Stack Device Configuration Get** *(ux_host_stack_device_configuration_get)*</span></span> |
| ![Ícone de configuração do dispositivo de pilha de anfitrião](./media/user-guide/usbx-events/image194.png)    | <span data-ttu-id="4e4bd-496">**Seleção de configuração do dispositivo de pilha de anfitrião** *(ux_host_stack_device_configuration_select)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-496">**Host Stack Device Configuration Select** *(ux_host_stack_device_configuration_select)*</span></span> |
| ![Ícone de leitura de dispositivo de pilha de anfitrião](./media/user-guide/usbx-events/image195.png)    | <span data-ttu-id="4e4bd-498">**Leitura do descritor do dispositivo** de pilha de *anfitrião (ux_host_stack_device_descriptor_read)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-498">**Host Stack Device Descriptor Read** *(ux_host_stack_device_descriptor_read)*</span></span> |
| ![Dispositivo de pilha de anfitrião obter ícone](./media/user-guide/usbx-events/image196.png)    | <span data-ttu-id="4e4bd-500">**Dispositivo de pilha de anfitrião obter** (ux_host_stack_device_get)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-500">**Host Stack Device Get** (ux_host_stack_device_get)</span></span> |
| ![Ícone de remover dispositivo de pilha de anfitrião](./media/user-guide/usbx-events/image197.png)    | <span data-ttu-id="4e4bd-502">**Remover dispositivo de pilha de anfitrião** (ux_host_stack_device_get)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-502">**Host Stack Device Remove** (ux_host_stack_device_get)</span></span> |
| ![Ícone livre de recursos do dispositivo de pilha de anfitrião](./media/user-guide/usbx-events/image198.png)    | <span data-ttu-id="4e4bd-504">**Dispositivo de pilha de anfitrião livre** (ux_host_stack_device_resource_free)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-504">**Host Stack Device Resource Free** (ux_host_stack_device_resource_free)</span></span> |
| ![Exemplo de ponto final de pilha de anfitrião Criar ícone](./media/user-guide/usbx-events/image199.png)    | <span data-ttu-id="4e4bd-506">**Host Stack Endpoint Instance Create** (ux_host_stack_endpoint_instance_create)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-506">**Host Stack Endpoint Instance Create** (ux_host_stack_endpoint_instance_create)</span></span> |
| ![Exemplo de endpoint de pilha de anfitrião Eliminar ícone](./media/user-guide/usbx-events/image200.png)    | <span data-ttu-id="4e4bd-508">**Série de anfitrião Endpoint Instance Delete** (ux_host_stack_endpoint_instance_delete)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-508">**Host Stack Endpoint Instance Delete** (ux_host_stack_endpoint_instance_delete)</span></span> |
| ![Ícone de reset do ponto final do host Stack](./media/user-guide/usbx-events/image201.png)    | <span data-ttu-id="4e4bd-510">**Reset do ponto final da pilha de anfitrião** (ux_host_stack_endpoint_reset)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-510">**Host Stack Endpoint Reset** (ux_host_stack_endpoint_reset)</span></span> |
| ![Ícone de aborto de transferência de ponto final de pilha de anfitrião](./media/user-guide/usbx-events/image202.png)    | <span data-ttu-id="4e4bd-512">**Abortar a transferência de ponto final do host Stack** (ux_host_stack_endpoint_transfer_abort)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-512">**Host Stack Endpoint Transfer Abort** (ux_host_stack_endpoint_transfer_abort)</span></span> |
| ![Ícone do controlador do anfitrião do anfitrião do anfitrião](./media/user-guide/usbx-events/image203.png)    | <span data-ttu-id="4e4bd-514">**Registo do controlador do anfitrião** host stack *(ux_host_stack_hcd_register)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-514">**Host Stack Host Controller Register** *(ux_host_stack_hcd_register)*</span></span> |
| ![Ícone inicialize da pilha de anfitrião](./media/user-guide/usbx-events/image204.png)    | <span data-ttu-id="4e4bd-516">**Inicialize da pilha de anfitriões** *(ux_host_stack_initialize)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-516">**Host Stack Initialize** *(ux_host_stack_initialize)*</span></span> |
| ![Anfitrião Stack Interface Endpoint Obter ícone](./media/user-guide/usbx-events/image205.png)    | <span data-ttu-id="4e4bd-518">**Host Stack Interface Endpoint Get** *(ux_host_stack_interface_endpoint_get)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-518">**Host Stack Interface Endpoint Get** *(ux_host_stack_interface_endpoint_get)*</span></span> |
| ![Exemplo de interface de pilha de anfitrião Criar ícone](./media/user-guide/usbx-events/image206.png)    | <span data-ttu-id="4e4bd-520">**Série de série de anfitriões Criar** *(ux_host_stack_interface_instance_create)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-520">**Host Stack Interface Instance Create** *(ux_host_stack_interface_instance_create)*</span></span> |
| ![Exemplo de interface de pilha de anfitrião Eliminar ícone](./media/user-guide/usbx-events/image207.png)    | <span data-ttu-id="4e4bd-522">**Excluir a interface da interface da pilha de anfitrião** *(ux_host_stack_interface_instance_delete)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-522">**Host Stack Interface Instance Delete** *(ux_host_stack_interface_instance_delete)*</span></span> |
| ![Ícone de conjunto de interface de pilha de anfitrião](./media/user-guide/usbx-events/image208.png)    | <span data-ttu-id="4e4bd-524">**Conjunto de interface de pilha de anfitrião** *(ux_host_stack_interface_set)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-524">**Host Stack Interface Set** *(ux_host_stack_interface_set)*</span></span> |
| ![Configuração de configuração da interface de pilha de anfitrião Selecionar ícone](./media/user-guide/usbx-events/image209.png)    | <span data-ttu-id="4e4bd-526">**Seleção de definição de interface de pilha de anfitrião** *(ux_host_stack_interface_setting_select)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-526">**Host Stack Interface Setting Select** *(ux_host_stack_interface_setting_select)*</span></span> |
| ![Host Stack Nova Configuração Criar ícone](./media/user-guide/usbx-events/image210.png)    | <span data-ttu-id="4e4bd-528">**Host Stack Nova Configuração Criar** *(ux_host_stack_new_configuration_create)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-528">**Host Stack New Configuration Create** *(ux_host_stack_new_configuration_create)*</span></span> |
| ![Host Stack novo dispositivo criar ícone](./media/user-guide/usbx-events/image211.png)    | <span data-ttu-id="4e4bd-530">**Host Stack Novo Dispositivo Criar** *(ux_host_stack_new_device_create)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-530">**Host Stack New Device Create** *(ux_host_stack_new_device_create)*</span></span> |
| ![Host Stack Novo Ponto Final Criar ícone](./media/user-guide/usbx-events/image212.png)    | <span data-ttu-id="4e4bd-532">**Host Stack New Endpoint Create** *(ux_host_stack_new_endpoint_create)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-532">**Host Stack New Endpoint Create** *(ux_host_stack_new_endpoint_create)*</span></span> |
| ![Ícone de mudança de fundo de raiz de pilha de anfitrião](./media/user-guide/usbx-events/image213.png)    | <span data-ttu-id="4e4bd-534">**Processo de mudança do hub de raiz da pilha de anfitrião** *(ux_host_stack_rh_change_process)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-534">**Host Stack Root Hub Change Process** *(ux_host_stack_rh_change_process)*</span></span> |
| ![Ícone de extração de dispositivo de raiz de pilha de anfitrião](./media/user-guide/usbx-events/image214.png)    | <span data-ttu-id="4e4bd-536">**Hospedar stack raiz de raiz de extração do dispositivo** *(ux_host_stack_rh_device_extraction)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-536">**Host Stack Root Hub Device Extraction** *(ux_host_stack_rh_device_extraction)*</span></span> |
| ![Ícone de inserção do dispositivo de inserção do hub de raiz da pilha de anfitrião](./media/user-guide/usbx-events/image215.png)    | <span data-ttu-id="4e4bd-538">**Inserção do dispositivo do cubo de raiz** do bloco de *pilhas de anfitrião (ux_host_stack_rh_device_insertion)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-538">**Host Stack Root Hub Device Insertion** *(ux_host_stack_rh_device_insertion)*</span></span> |
| ![Ícone de pedido de transferência de pilha de anfitrião](./media/user-guide/usbx-events/image216.png)    | <span data-ttu-id="4e4bd-540">**Pedido de transferência de pilha de anfitrião** *(ux_host_stack_transfer_request)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-540">**Host Stack Transfer Request** *(ux_host_stack_transfer_request)*</span></span> |
| ![Ícone de aborto de pedido de transferência de pilha de anfitrião](./media/user-guide/usbx-events/image217.png)    | <span data-ttu-id="4e4bd-542">**Pedido de transferência de pilha de anfitrião Abortar** *(ux_host_stack_transfer_request_abort)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-542">**Host Stack Transfer Request Abort** *(ux_host_stack_transfer_request_abort)*</span></span> |
| ![Ícone de erro U S B X](./media/user-guide/usbx-events/image218.png)    | <span data-ttu-id="4e4bd-544">**Erro USBX** *(ux_error)*</span><span class="sxs-lookup"><span data-stu-id="4e4bd-544">**USBX Error** *(ux_error)*</span></span> |

## <a name="event-descriptions"></a><span data-ttu-id="4e4bd-545">Descrições do evento</span><span class="sxs-lookup"><span data-stu-id="4e4bd-545">Event Descriptions</span></span>

<span data-ttu-id="4e4bd-546">As páginas seguintes descrevem os eventos usbx trace.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-546">The following pages describe the USBX Trace Events.</span></span>

### <a name="device-class-cdc-activate"></a><span data-ttu-id="4e4bd-547">Dispositivo Classe Cdc Ativar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-547">Device Class Cdc Activate</span></span> 

#### <a name="ux_device_class_cdc_activate"></a><span data-ttu-id="4e4bd-548">ux_device_class_cdc_activate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-548">ux_device_class_cdc_activate</span></span>

<span data-ttu-id="4e4bd-549">**Ícone** ![ Ícone ativar classe C D C C do dispositivo](./media/user-guide/usbx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-549">**Icon** ![Device Class C D C Activate icon](./media/user-guide/usbx-events/image1.png)</span></span>

<span data-ttu-id="4e4bd-550">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-550">**Description**</span></span>

<span data-ttu-id="4e4bd-551">Este evento representa um evento usbx device Class Cdc Activate Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-551">This event represents a USBX Device Class Cdc Activate Event.</span></span>

<span data-ttu-id="4e4bd-552">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-552">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-553">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-553">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-554">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-554">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-555">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-555">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-556">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-556">Info Field 4: Not used.</span></span>

### <a name="device-class-cdc-deactivate"></a><span data-ttu-id="4e4bd-557">Desativar a classe de dispositivos CDC</span><span class="sxs-lookup"><span data-stu-id="4e4bd-557">Device Class Cdc Deactivate</span></span> 

#### <a name="ux_device_class_cdc_deactivate"></a><span data-ttu-id="4e4bd-558">ux_device_class_cdc_deactivate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-558">ux_device_class_cdc_deactivate</span></span>

<span data-ttu-id="4e4bd-559">**Ícone** ![ Ícone desativado classe C D C C](./media/user-guide/usbx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-559">**Icon** ![Device Class C D C Deactivate icon](./media/user-guide/usbx-events/image2.png)</span></span>

<span data-ttu-id="4e4bd-560">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-560">**Description**</span></span>

<span data-ttu-id="4e4bd-561">Este evento representa um CDC desativado da classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-561">This event represents a USBX Device Class Cdc Deactivate.</span></span>

<span data-ttu-id="4e4bd-562">Campos de Informação</span><span class="sxs-lookup"><span data-stu-id="4e4bd-562">Information Fields</span></span> 

- <span data-ttu-id="4e4bd-563">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-563">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-564">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-564">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-565">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-565">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-566">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-566">Info Field 4: Not used.</span></span>

### <a name="device-class-cdc-read"></a><span data-ttu-id="4e4bd-567">Leitura do Cdc classe de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-567">Device Class Cdc Read</span></span> 

#### <a name="ux_device_class_cdc_read"></a><span data-ttu-id="4e4bd-568">ux_device_class_cdc_read</span><span class="sxs-lookup"><span data-stu-id="4e4bd-568">ux_device_class_cdc_read</span></span>

<span data-ttu-id="4e4bd-569">**Ícone** ![ Ícone de leitura classe C D C do dispositivo](./media/user-guide/usbx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-569">**Icon** ![Device Class C D C Read icon](./media/user-guide/usbx-events/image3.png)</span></span>

<span data-ttu-id="4e4bd-570">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-570">**Description**</span></span>

<span data-ttu-id="4e4bd-571">Este evento representa um Evento de Leitura cdc classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-571">This event represents a USBX Device Class Cdc Read Event.</span></span>

<span data-ttu-id="4e4bd-572">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-572">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-573">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-573">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-574">Info Field 2: Ponteiro de dados.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-574">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4e4bd-575">Info Field 3: Comprimento solicitado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-575">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4e4bd-576">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-576">Info Field 4: Not used.</span></span>

### <a name="device-class-cdc-write"></a><span data-ttu-id="4e4bd-577">Escrita de cdc classe de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-577">Device Class Cdc Write</span></span> 

#### <a name="ux_device_class_cdc_write"></a><span data-ttu-id="4e4bd-578">ux_device_class_cdc_write</span><span class="sxs-lookup"><span data-stu-id="4e4bd-578">ux_device_class_cdc_write</span></span>

<span data-ttu-id="4e4bd-579">**Ícone** ![ Ícone de escrita classe C D C do dispositivo](./media/user-guide/usbx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-579">**Icon** ![Device Class C D C Write icon](./media/user-guide/usbx-events/image4.png)</span></span>

<span data-ttu-id="4e4bd-580">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-580">**Description**</span></span>

<span data-ttu-id="4e4bd-581">Este evento representa um evento de escrita cdc classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-581">This event represents a USBX Device Class Cdc Write Event.</span></span>

<span data-ttu-id="4e4bd-582">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-582">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-583">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-583">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-584">Info Field 2: Ponteiro de dados.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-584">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4e4bd-585">Info Field 3: Comprimento solicitado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-585">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4e4bd-586">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-586">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-activate"></a><span data-ttu-id="4e4bd-587">Ativar classe de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-587">Device Class Dpump Activate</span></span> 

#### <a name="ux_device_class_dpump_activate"></a><span data-ttu-id="4e4bd-588">ux_device_class_dpump_activate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-588">ux_device_class_dpump_activate</span></span>

<span data-ttu-id="4e4bd-589">**Ícone** ![ Ícone ativar classe de dispositivo](./media/user-guide/usbx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-589">**Icon** ![Device Class Dpump Activate icon](./media/user-guide/usbx-events/image5.png)</span></span>

<span data-ttu-id="4e4bd-590">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-590">**Description**</span></span>

<span data-ttu-id="4e4bd-591">Este evento representa um evento ativado da classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-591">This event represents a USBX Device Class Dpump Activate Event.</span></span>

<span data-ttu-id="4e4bd-592">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-592">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-593">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-593">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-594">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-594">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-595">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-595">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-596">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-596">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-deactivate"></a><span data-ttu-id="4e4bd-597">Classe de dispositivo Dpump Desativar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-597">Device Class Dpump Deactivate</span></span> 

#### <a name="ux_device_class_dpump_deactivate"></a><span data-ttu-id="4e4bd-598">ux_device_class_dpump_deactivate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-598">ux_device_class_dpump_deactivate</span></span>

<span data-ttu-id="4e4bd-599">**Ícone** ![ Ícone de desativado da classe de dispositivo Dpump](./media/user-guide/usbx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-599">**Icon** ![Device Class Dpump Deactivate icon](./media/user-guide/usbx-events/image6.png)</span></span>

<span data-ttu-id="4e4bd-600">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-600">**Description**</span></span>

<span data-ttu-id="4e4bd-601">Este evento representa um evento de desativado da classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-601">This event represents a USBX Device Class Dpump Deactivate Event.</span></span>

<span data-ttu-id="4e4bd-602">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-602">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-603">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-603">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-604">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-604">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-605">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-605">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-606">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-606">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-read"></a><span data-ttu-id="4e4bd-607">Leitura de Classe de Dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-607">Device Class Dpump Read</span></span> 

#### <a name="ux_device_class_dpump_read"></a><span data-ttu-id="4e4bd-608">ux_device_class_dpump_read</span><span class="sxs-lookup"><span data-stu-id="4e4bd-608">ux_device_class_dpump_read</span></span>

<span data-ttu-id="4e4bd-609">**Ícone** ![ Ícone de leitura de classe de dispositivo](./media/user-guide/usbx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-609">**Icon** ![Device Class Dpump Read icon](./media/user-guide/usbx-events/image7.png)</span></span>

<span data-ttu-id="4e4bd-610">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-610">**Description**</span></span>

<span data-ttu-id="4e4bd-611">Este evento representa um Evento de Leitura de Dpump da Classe dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-611">This event represents a USBX Device Class Dpump Read Event.</span></span>

<span data-ttu-id="4e4bd-612">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-612">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-613">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-613">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-614">Info Field 2: Buffer.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-614">Info Field 2: Buffer.</span></span>
- <span data-ttu-id="4e4bd-615">Info Field 3: Comprimento solicitado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-615">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4e4bd-616">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-616">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-write"></a><span data-ttu-id="4e4bd-617">Escrita de Classe de Dispositivo Dpump</span><span class="sxs-lookup"><span data-stu-id="4e4bd-617">Device Class Dpump Write</span></span> 

#### <a name="ux_device_class_dpump_write"></a><span data-ttu-id="4e4bd-618">ux_device_class_dpump_write</span><span class="sxs-lookup"><span data-stu-id="4e4bd-618">ux_device_class_dpump_write</span></span>

<span data-ttu-id="4e4bd-619">**Ícone** ![ Ícone de escrita de classe de dispositivo](./media/user-guide/usbx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-619">**Icon** ![Device Class Dpump Write icon](./media/user-guide/usbx-events/image8.png)</span></span>

<span data-ttu-id="4e4bd-620">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-620">**Description**</span></span>

<span data-ttu-id="4e4bd-621">Este evento representa um evento de escrita classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-621">This event represents a USBX Device Class Dpump Write Event.</span></span>

<span data-ttu-id="4e4bd-622">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-622">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-623">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-623">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-624">Info Field 2: Ponteiro de dados.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-624">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4e4bd-625">Info Field 3: Comprimento solicitado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-625">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4e4bd-626">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-626">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-activate"></a><span data-ttu-id="4e4bd-627">Classe de dispositivo Hid Ativar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-627">Device Class Hid Activate</span></span> 

#### <a name="ux_device_class_hid_activate"></a><span data-ttu-id="4e4bd-628">ux_device_class_hid_activate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-628">ux_device_class_hid_activate</span></span>

<span data-ttu-id="4e4bd-629">**Ícone** ![ Ícone ativar classe de dispositivo Hid](./media/user-guide/usbx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-629">**Icon** ![Device Class Hid Activate icon](./media/user-guide/usbx-events/image9.png)</span></span>

<span data-ttu-id="4e4bd-630">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-630">**Description**</span></span>

<span data-ttu-id="4e4bd-631">Este evento representa um evento USBX Device Class Hid Activate Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-631">This event represents a USBX Device Class Hid Activate Event.</span></span>

<span data-ttu-id="4e4bd-632">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-632">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-633">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-633">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-634">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-634">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-635">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-635">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-636">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-636">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-deactivate"></a><span data-ttu-id="4e4bd-637">Classe de dispositivo Hid Desativado</span><span class="sxs-lookup"><span data-stu-id="4e4bd-637">Device Class Hid Deactivate</span></span> 

#### <a name="ux_device_class_hid_deactivate"></a><span data-ttu-id="4e4bd-638">ux_device_class_hid_deactivate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-638">ux_device_class_hid_deactivate</span></span>

<span data-ttu-id="4e4bd-639">**Ícone** ![ Ícone de desativado classe de dispositivo Hid](./media/user-guide/usbx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-639">**Icon** ![Device Class Hid Deactivate icon](./media/user-guide/usbx-events/image10.png)</span></span>

<span data-ttu-id="4e4bd-640">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-640">**Description**</span></span>

<span data-ttu-id="4e4bd-641">Este evento representa um evento de desativado da classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-641">This event represents a USBX Device Class Hid Deactivate Event.</span></span>

<span data-ttu-id="4e4bd-642">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-642">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-643">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-643">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-644">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-644">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-645">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-645">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-646">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-646">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-descriptor-send"></a><span data-ttu-id="4e4bd-647">Classe de dispositivo Hid Descriptor Enviar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-647">Device Class Hid Descriptor Send</span></span> 

#### <a name="ux_device_class_hid_descritpor_send"></a><span data-ttu-id="4e4bd-648">ux_device_class_hid_descritpor_send</span><span class="sxs-lookup"><span data-stu-id="4e4bd-648">ux_device_class_hid_descritpor_send</span></span>

<span data-ttu-id="4e4bd-649">**Ícone** ![ Classe de dispositivo hiddscriptor Enviar ícone](./media/user-guide/usbx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-649">**Icon** ![Device Class Hid Descriptor Send icon](./media/user-guide/usbx-events/image11.png)</span></span>

<span data-ttu-id="4e4bd-650">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-650">**Description**</span></span>

<span data-ttu-id="4e4bd-651">Este evento representa um evento de envio de dispositivo USBX Classe Oculta.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-651">This event represents a USBX Device Class Hid Descriptor Send Event.</span></span>

<span data-ttu-id="4e4bd-652">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-652">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-653">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-653">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-654">Info Field 2: Tipo de descritor.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-654">Info Field 2: Descriptor type.</span></span>
- <span data-ttu-id="4e4bd-655">Info Field 3: Índice de pedido.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-655">Info Field 3: Request index.</span></span>
- <span data-ttu-id="4e4bd-656">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-656">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-event-get"></a><span data-ttu-id="4e4bd-657">Evento de classe de dispositivo Hid Obter</span><span class="sxs-lookup"><span data-stu-id="4e4bd-657">Device Class Hid Event Get</span></span> 

#### <a name="ux_device_class_hid_event_get"></a><span data-ttu-id="4e4bd-658">ux_device_class_hid_event_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-658">ux_device_class_hid_event_get</span></span>

<span data-ttu-id="4e4bd-659">**Ícone** ![ Classe de dispositivo hid evento obter ícone](./media/user-guide/usbx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-659">**Icon** ![Device Class Hid Event Get icon](./media/user-guide/usbx-events/image12.png)</span></span>

<span data-ttu-id="4e4bd-660">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-660">**Description**</span></span>

<span data-ttu-id="4e4bd-661">Este evento representa um evento usbx device class hid event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-661">This event represents a USBX Device Class Hid Event Get Event.</span></span>

<span data-ttu-id="4e4bd-662">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-662">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-663">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-663">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-664">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-664">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-665">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-665">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-666">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-666">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-event-set"></a><span data-ttu-id="4e4bd-667">Conjunto de eventos de classe de dispositivos hid</span><span class="sxs-lookup"><span data-stu-id="4e4bd-667">Device Class Hid Event Set</span></span> 

#### <a name="ux_device_class_hid_event_set"></a><span data-ttu-id="4e4bd-668">ux_device_class_hid_event_set</span><span class="sxs-lookup"><span data-stu-id="4e4bd-668">ux_device_class_hid_event_set</span></span>

<span data-ttu-id="4e4bd-669">**Ícone** ![ Ícone de conjunto de evento de classe de dispositivo hid](./media/user-guide/usbx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-669">**Icon** ![Device Class Hid Event Set icon](./media/user-guide/usbx-events/image13.png)</span></span>

<span data-ttu-id="4e4bd-670">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-670">**Description**</span></span>

<span data-ttu-id="4e4bd-671">Este evento representa um conjunto de eventos hid classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-671">This event represents a USBX Device Class Hid Event Set.</span></span>

<span data-ttu-id="4e4bd-672">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-672">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-673">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-673">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-674">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-674">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-675">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-675">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-676">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-676">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-report-get"></a><span data-ttu-id="4e4bd-677">Relatório hid da classe do dispositivo obter</span><span class="sxs-lookup"><span data-stu-id="4e4bd-677">Device Class Hid Report Get</span></span> 

#### <a name="ux_device_class_hid_report_get"></a><span data-ttu-id="4e4bd-678">ux_device_class_hid_report_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-678">ux_device_class_hid_report_get</span></span>

<span data-ttu-id="4e4bd-679">**Ícone** ![ Relatório hid classe de dispositivo obter ícone](./media/user-guide/usbx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-679">**Icon** ![Device Class Hid Report Get icon](./media/user-guide/usbx-events/image14.png)</span></span>

<span data-ttu-id="4e4bd-680">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-680">**Description**</span></span>

<span data-ttu-id="4e4bd-681">Este evento representa um evento usbx device class hid report.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-681">This event represents a USBX Device Class Hid Report Get Event.</span></span>

<span data-ttu-id="4e4bd-682">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-682">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-683">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-683">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-684">Info Field 2: Tipo de descritor.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-684">Info Field 2: Descriptor type.</span></span>
- <span data-ttu-id="4e4bd-685">Info Field 3: Índice de pedido.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-685">Info Field 3: Request index.</span></span>
- <span data-ttu-id="4e4bd-686">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-686">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-report-set"></a><span data-ttu-id="4e4bd-687">Conjunto de relatório de hid classe de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-687">Device Class Hid Report Set</span></span> 

#### <a name="ux_device_class_hid_report_set"></a><span data-ttu-id="4e4bd-688">ux_device_class_hid_report_set</span><span class="sxs-lookup"><span data-stu-id="4e4bd-688">ux_device_class_hid_report_set</span></span>

<span data-ttu-id="4e4bd-689">**Ícone** ![ Ícone de conjunto de relatório de classe de dispositivo hid](./media/user-guide/usbx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-689">**Icon** ![Device Class Hid Report Set icon](./media/user-guide/usbx-events/image15.png)</span></span>

<span data-ttu-id="4e4bd-690">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-690">**Description**</span></span>

<span data-ttu-id="4e4bd-691">Este evento representa um evento usbx device Class Hid Report Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-691">This event represents a USBX Device Class Hid Report Set Event.</span></span>

<span data-ttu-id="4e4bd-692">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-692">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-693">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-693">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-694">Info Field 2: Tipo de descritor.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-694">Info Field 2: Descriptor type.</span></span>
- <span data-ttu-id="4e4bd-695">Info Field 3: Índice de pedido.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-695">Info Field 3: Request index.</span></span>
- <span data-ttu-id="4e4bd-696">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-696">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-activate"></a><span data-ttu-id="4e4bd-697">Classe de dispositivo Pima Ativar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-697">Device Class Pima Activate</span></span>

#### <a name="ux_device_class_pima_activate"></a><span data-ttu-id="4e4bd-698">ux_device_class_pima_activate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-698">ux_device_class_pima_activate</span></span>

<span data-ttu-id="4e4bd-699">**Ícone** ![ Ícone de ativação classe de dispositivo Pima](./media/user-guide/usbx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-699">**Icon** ![Device Class Pima Activate icon](./media/user-guide/usbx-events/image16.png)</span></span>

<span data-ttu-id="4e4bd-700">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-700">**Description**</span></span>

<span data-ttu-id="4e4bd-701">Este evento representa um evento de ativação Pima da classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-701">This event represents a USBX Device Class Pima Activate Event.</span></span>

<span data-ttu-id="4e4bd-702">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-702">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-703">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-703">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-704">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-704">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-705">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-705">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-706">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-706">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-deactivate"></a><span data-ttu-id="4e4bd-707">Classe de dispositivo Pima Desativar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-707">Device Class Pima Deactivate</span></span> 

#### <a name="ux_device_class_pima_deactivate"></a><span data-ttu-id="4e4bd-708">ux_device_class_pima_deactivate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-708">ux_device_class_pima_deactivate</span></span>

<span data-ttu-id="4e4bd-709">**Ícone** ![ Ícone de desativado classe de dispositivo Pima](./media/user-guide/usbx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-709">**Icon** ![Device Class Pima Deactivate icon](./media/user-guide/usbx-events/image17.png)</span></span>

<span data-ttu-id="4e4bd-710">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-710">**Description**</span></span>

<span data-ttu-id="4e4bd-711">Este evento representa um evento de desativado Pima da classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-711">This event represents a USBX Device Class Pima Deactivate Event.</span></span>

<span data-ttu-id="4e4bd-712">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-712">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-713">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-713">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-714">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-714">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-715">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-715">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-716">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-716">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-device-info-send"></a><span data-ttu-id="4e4bd-717">Informações de dispositivo classe de dispositivo Pima enviar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-717">Device Class Pima Device Info Send</span></span> 

#### <a name="ux_device_class_pima_device_info_send"></a><span data-ttu-id="4e4bd-718">ux_device_class_pima_device_info_send</span><span class="sxs-lookup"><span data-stu-id="4e4bd-718">ux_device_class_pima_device_info_send</span></span>

<span data-ttu-id="4e4bd-719">**Ícone** ![ Informação de envio de dispositivo classe de dispositivo Pima classe de dispositivo](./media/user-guide/usbx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-719">**Icon** ![Device Class Pima Device Info Send icon](./media/user-guide/usbx-events/image18.png)</span></span>

<span data-ttu-id="4e4bd-720">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-720">**Description**</span></span>

<span data-ttu-id="4e4bd-721">Este evento representa um evento de envio de info dispositivo pima classe USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-721">This event represents a USBX Device Class Pima Device Info Send Event.</span></span>

<span data-ttu-id="4e4bd-722">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-722">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-723">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-723">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-724">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-724">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-725">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-725">Info Field 3: Not used.</span></span>

### <a name="device-class-pima-event-get"></a><span data-ttu-id="4e4bd-726">Evento Pima classe de dispositivo obter</span><span class="sxs-lookup"><span data-stu-id="4e4bd-726">Device Class Pima Event Get</span></span> 

#### <a name="ux_device_class_pima_event_get"></a><span data-ttu-id="4e4bd-727">ux_device_class_pima_event_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-727">ux_device_class_pima_event_get</span></span>

<span data-ttu-id="4e4bd-728">**Ícone** ![ Evento Pima classe de dispositivo Obter ícone](./media/user-guide/usbx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-728">**Icon** ![Device Class Pima Event Get icon](./media/user-guide/usbx-events/image19.png)</span></span>

<span data-ttu-id="4e4bd-729">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-729">**Description**</span></span>

<span data-ttu-id="4e4bd-730">Este evento representa um evento de evento Pima classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-730">This event represents a USBX Device Class Pima Event Get Event.</span></span>

<span data-ttu-id="4e4bd-731">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-731">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-732">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-732">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-733">Info Field 2: Evento Pima.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-733">Info Field 2: Pima event.</span></span>
- <span data-ttu-id="4e4bd-734">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-734">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-735">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-735">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-event-set"></a><span data-ttu-id="4e4bd-736">Conjunto de eventos classe de dispositivo Pima</span><span class="sxs-lookup"><span data-stu-id="4e4bd-736">Device Class Pima Event Set</span></span> 

#### <a name="ux_device_class_pima_event_set"></a><span data-ttu-id="4e4bd-737">ux_device_class_pima_event_set</span><span class="sxs-lookup"><span data-stu-id="4e4bd-737">ux_device_class_pima_event_set</span></span>

<span data-ttu-id="4e4bd-738">**Ícone** ![ Ícone de conjunto de evento classe de dispositivo Pima](./media/user-guide/usbx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-738">**Icon** ![Device Class Pima Event Set icon](./media/user-guide/usbx-events/image20.png)</span></span>

<span data-ttu-id="4e4bd-739">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-739">**Description**</span></span>

<span data-ttu-id="4e4bd-740">Este evento representa um evento de conjunto de eventos Pima classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-740">This event represents a USBX Device Class Pima Event Set Event.</span></span>

<span data-ttu-id="4e4bd-741">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-741">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-742">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-742">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-743">Info Field 2: Evento Pima.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-743">Info Field 2: Pima event.</span></span>
- <span data-ttu-id="4e4bd-744">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-744">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-745">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-745">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-add"></a><span data-ttu-id="4e4bd-746">Adicionar objeto pima classe de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-746">Device Class Pima Object Add</span></span> 

#### <a name="ux_device_class_pima_object_add"></a><span data-ttu-id="4e4bd-747">ux_device_class_pima_object_add</span><span class="sxs-lookup"><span data-stu-id="4e4bd-747">ux_device_class_pima_object_add</span></span>

<span data-ttu-id="4e4bd-748">**Ícone** ![ Ícone de adicionar objeto classe de dispositivo Pima](./media/user-guide/usbx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-748">**Icon** ![Device Class Pima Object Add icon](./media/user-guide/usbx-events/image21.png)</span></span>

<span data-ttu-id="4e4bd-749">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-749">**Description**</span></span>

<span data-ttu-id="4e4bd-750">Este evento representa um evento de adição de objetos Pima da classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-750">This event represents a USBX Device Class Pima Object Add Event.</span></span>

<span data-ttu-id="4e4bd-751">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-751">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-752">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-752">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-753">Info Field 2: Pega do objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-753">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4e4bd-754">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-754">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-755">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-755">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-data-get"></a><span data-ttu-id="4e4bd-756">Dados de objetos de classe de dispositivo Pima obtêm</span><span class="sxs-lookup"><span data-stu-id="4e4bd-756">Device Class Pima Object Data Get</span></span> 

#### <a name="ux_device_class_pima_object_data_get"></a><span data-ttu-id="4e4bd-757">ux_device_class_pima_object_data_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-757">ux_device_class_pima_object_data_get</span></span>

<span data-ttu-id="4e4bd-758">**Ícone** ![ Dados de objeto de classe de dispositivo Pima Obter ícone](./media/user-guide/usbx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-758">**Icon** ![Device Class Pima Object Data Get icon](./media/user-guide/usbx-events/image22.png)</span></span>

<span data-ttu-id="4e4bd-759">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-759">**Description**</span></span>

<span data-ttu-id="4e4bd-760">Este evento representa um evento de dados de objetos Pima da classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-760">This event represents a USBX Device Class Pima Object Data Get Event.</span></span>

<span data-ttu-id="4e4bd-761">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-761">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-762">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-762">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-763">Info Field 2: Pega do objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-763">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4e4bd-764">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-764">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-765">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-765">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-data-send"></a><span data-ttu-id="4e4bd-766">Dados de objetos de classe de dispositivo Pima enviar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-766">Device Class Pima Object Data Send</span></span> 

#### <a name="ux_device_class_pima_object_data_send"></a><span data-ttu-id="4e4bd-767">ux_device_class_pima_object_data_send</span><span class="sxs-lookup"><span data-stu-id="4e4bd-767">ux_device_class_pima_object_data_send</span></span>

<span data-ttu-id="4e4bd-768">**Ícone** ![ Dados de objeto de classe de dispositivo Pima Enviar ícone](./media/user-guide/usbx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-768">**Icon** ![Device Class Pima Object Data Send icon](./media/user-guide/usbx-events/image23.png)</span></span>

<span data-ttu-id="4e4bd-769">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-769">**Description**</span></span>

<span data-ttu-id="4e4bd-770">Este evento representa um evento de envio de dados de objetos de dispositivo USBX Pima.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-770">This event represents a USBX Device Class Pima Object Data Send Event.</span></span>

<span data-ttu-id="4e4bd-771">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-771">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-772">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-772">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-773">Info Field 2: Pega do objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-773">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4e4bd-774">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-774">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-775">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-775">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-delete"></a><span data-ttu-id="4e4bd-776">Classificação de dispositivo Pima Objeto Delete</span><span class="sxs-lookup"><span data-stu-id="4e4bd-776">Device Class Pima Object Delete</span></span> 

#### <a name="ux_device_class_pima_object_delete"></a><span data-ttu-id="4e4bd-777">ux_device_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="4e4bd-777">ux_device_class_pima_object_delete</span></span>

<span data-ttu-id="4e4bd-778">**Ícone** ![ Ícone de eliminação de objeto de classe de dispositivo Pima](./media/user-guide/usbx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-778">**Icon** ![Device Class Pima Object Delete icon](./media/user-guide/usbx-events/image24.png)</span></span>

<span data-ttu-id="4e4bd-779">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-779">**Description**</span></span>

<span data-ttu-id="4e4bd-780">Este evento representa um evento de eliminação de objetos Pima da classe usbx.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-780">This event represents a USBX Device Class Pima Object Delete Event.</span></span>

<span data-ttu-id="4e4bd-781">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-781">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-782">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-782">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-783">Info Field 2: Pega do objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-783">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4e4bd-784">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-784">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-785">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-785">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-handles-send"></a><span data-ttu-id="4e4bd-786">Dispositivo classe Pima objeto handles enviar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-786">Device Class Pima Object Handles Send</span></span> 

#### <a name="ux_device_class_pima_object_handles_send"></a><span data-ttu-id="4e4bd-787">ux_device_class_pima_object_handles_send</span><span class="sxs-lookup"><span data-stu-id="4e4bd-787">ux_device_class_pima_object_handles_send</span></span>

<span data-ttu-id="4e4bd-788">**Ícone** ![ Alças de objeto classe de dispositivo Pima Enviar ícone](./media/user-guide/usbx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-788">**Icon** ![Device Class Pima Object Handles Send icon](./media/user-guide/usbx-events/image25.png)</span></span>

<span data-ttu-id="4e4bd-789">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-789">**Description**</span></span>

<span data-ttu-id="4e4bd-790">Este evento representa um evento de envio de objetos de dispositivo USBX Classe Pima.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-790">This event represents a USBX Device Class Pima Object Handles Send Event.</span></span>

<span data-ttu-id="4e4bd-791">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-791">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-792">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-792">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-793">Info Field 2: ID de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-793">Info Field 2: Storage ID.</span></span>
- <span data-ttu-id="4e4bd-794">Info Field 3: Código de formato de objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-794">Info Field 3: Object format code.</span></span>
- <span data-ttu-id="4e4bd-795">Info Field 4: Associação de objetos.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-795">Info Field 4: Object association.</span></span>

### <a name="device-class-pima-object-info-get"></a><span data-ttu-id="4e4bd-796">Informações de objeto pima classe de dispositivo obter</span><span class="sxs-lookup"><span data-stu-id="4e4bd-796">Device Class Pima Object Info Get</span></span> 

#### <a name="ux_device_class_pima_object_info_send"></a><span data-ttu-id="4e4bd-797">ux_device_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="4e4bd-797">ux_device_class_pima_object_info_send</span></span>

<span data-ttu-id="4e4bd-798">**Ícone** ![ Classe de dispositivo Pima Objeto Info Obter ícone](./media/user-guide/usbx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-798">**Icon** ![Device Class Pima Object Info Get icon](./media/user-guide/usbx-events/image26.png)</span></span>

<span data-ttu-id="4e4bd-799">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-799">**Description**</span></span>

<span data-ttu-id="4e4bd-800">Este evento representa um evento USBX Device Class Pima Object Info Get.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-800">This event represents a USBX Device Class Pima Object Info Get Event.</span></span>

<span data-ttu-id="4e4bd-801">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-801">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-802">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-802">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-803">Info Field 2: Pega do objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-803">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4e4bd-804">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-804">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-805">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-805">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-info-send"></a><span data-ttu-id="4e4bd-806">Informações de objetos de classe de dispositivo Pima enviar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-806">Device Class Pima Object Info Send</span></span> 

#### <a name="ux_device_class_pima_object_info_send"></a><span data-ttu-id="4e4bd-807">ux_device_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="4e4bd-807">ux_device_class_pima_object_info_send</span></span>

<span data-ttu-id="4e4bd-808">**Ícone** ![ Classe de dispositivo Pima Objeto Info Enviar ícone](./media/user-guide/usbx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-808">**Icon** ![Device Class Pima Object Info Send icon](./media/user-guide/usbx-events/image27.png)</span></span>

<span data-ttu-id="4e4bd-809">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-809">**Description**</span></span>

<span data-ttu-id="4e4bd-810">Este evento representa um evento de envio de informação de objeto pima classe USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-810">This event represents a USBX Device Class Pima Object Info Send Event.</span></span>

<span data-ttu-id="4e4bd-811">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-811">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-812">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-812">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-813">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-813">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-814">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-814">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-815">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-815">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-objects-number-send"></a><span data-ttu-id="4e4bd-816">Número de objetos de classe de dispositivo Pima Enviar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-816">Device Class Pima Objects Number Send</span></span> 

#### <a name="ux_device_class_pima_object_number_send"></a><span data-ttu-id="4e4bd-817">ux_device_class_pima_object_number_send</span><span class="sxs-lookup"><span data-stu-id="4e4bd-817">ux_device_class_pima_object_number_send</span></span>

<span data-ttu-id="4e4bd-818">**Ícone** ![ Número de objetos de classe de dispositivo Pima Enviar ícone](./media/user-guide/usbx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-818">**Icon** ![Device Class Pima Objects Number Send icon](./media/user-guide/usbx-events/image28.png)</span></span>

<span data-ttu-id="4e4bd-819">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-819">**Description**</span></span>

<span data-ttu-id="4e4bd-820">Este evento representa um evento usbx device Class Pima Object Send.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-820">This event represents a USBX Device Class Pima Object Number Send event.</span></span>

<span data-ttu-id="4e4bd-821">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-821">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-822">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-822">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-823">Info Field 2: ID de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-823">Info Field 2: Storage ID.</span></span>
- <span data-ttu-id="4e4bd-824">Info Field 3: Código de formato de objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-824">Info Field 3: Object format code.</span></span>
- <span data-ttu-id="4e4bd-825">Info Field 4: Associado de objetos.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-825">Info Field 4: Object associate.</span></span>

### <a name="device-class-pima-partial-object-data-get"></a><span data-ttu-id="4e4bd-826">Dados de objeto parcial classe de dispositivo Pima obter</span><span class="sxs-lookup"><span data-stu-id="4e4bd-826">Device Class Pima Partial Object Data Get</span></span>

#### <a name="ux_device_class_pima_partial_object_data_get"></a><span data-ttu-id="4e4bd-827">ux_device_class_pima_partial_object_data_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-827">ux_device_class_pima_partial_object_data_get</span></span>

<span data-ttu-id="4e4bd-828">**Ícone** ![ Classe de dispositivo Pima Objeto Parcial Objeto Dados Obter ícone](./media/user-guide/usbx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-828">**Icon** ![Device Class Pima Partial Object Data Get icon](./media/user-guide/usbx-events/image29.png)</span></span>

<span data-ttu-id="4e4bd-829">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-829">**Description**</span></span>

<span data-ttu-id="4e4bd-830">Este evento representa um evento de dados de objeto parcial da classe USBX Pima.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-830">This event represents a USBX Device Class Pima Partial Object Data Get Event.</span></span>

<span data-ttu-id="4e4bd-831">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-831">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-832">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-832">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-833">Info Field 2: Pega do objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-833">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4e4bd-834">Info Field 3: Offset solicitado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-834">Info Field 3: Offset requested.</span></span>
- <span data-ttu-id="4e4bd-835">Info Field 4: Comprimento solicitado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-835">Info Field 4: Length requested.</span></span>

### <a name="device-class-pima-response-send"></a><span data-ttu-id="4e4bd-836">Envio de resposta classe de dispositivo Pima</span><span class="sxs-lookup"><span data-stu-id="4e4bd-836">Device Class Pima Response Send</span></span> 

#### <a name="ux_device_class_pima_response_send"></a><span data-ttu-id="4e4bd-837">ux_device_class_pima_response_send</span><span class="sxs-lookup"><span data-stu-id="4e4bd-837">ux_device_class_pima_response_send</span></span>

<span data-ttu-id="4e4bd-838">**Ícone** ![ Ícone de resposta pima classe de dispositivo](./media/user-guide/usbx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-838">**Icon** ![Device Class Pima Response Send icon](./media/user-guide/usbx-events/image30.png)</span></span>

<span data-ttu-id="4e4bd-839">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-839">**Description**</span></span>

<span data-ttu-id="4e4bd-840">Este evento representa um evento de envio de resposta Pima classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-840">This event represents a USBX Device Class Pima Response Send Event.</span></span>

<span data-ttu-id="4e4bd-841">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-841">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-842">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-842">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-843">Info Campo 2: Código de resposta.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-843">Info Field 2: Response code.</span></span>
- <span data-ttu-id="4e4bd-844">Info Campo 3: Parâmetro de número.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-844">Info Field 3: Number parameter.</span></span>
- <span data-ttu-id="4e4bd-845">Info Campo 4: Parâmetro Pima 1.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-845">Info Field 4: Pima parameter 1.</span></span>

### <a name="device-class-pima-storage-id-send"></a><span data-ttu-id="4e4bd-846">Envio de armazenamento classe de dispositivo Pima</span><span class="sxs-lookup"><span data-stu-id="4e4bd-846">Device Class Pima Storage Id Send</span></span> 

#### <a name="ux_device_class_pima_storage_id_send"></a><span data-ttu-id="4e4bd-847">ux_device_class_pima_storage_id_send</span><span class="sxs-lookup"><span data-stu-id="4e4bd-847">ux_device_class_pima_storage_id_send</span></span>

<span data-ttu-id="4e4bd-848">**Ícone** ![ Id de armazenamento classe de dispositivo Pima Enviar ícone](./media/user-guide/usbx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-848">**Icon** ![Device Class Pima Storage Id Send icon](./media/user-guide/usbx-events/image31.png)</span></span>

<span data-ttu-id="4e4bd-849">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-849">**Description**</span></span>

<span data-ttu-id="4e4bd-850">Este evento representa um evento de envio de Id de armazenamento Pima classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-850">This event represents a USBX Device Class Pima Storage Id Send Event.</span></span>

<span data-ttu-id="4e4bd-851">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-851">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-852">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-852">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-853">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-853">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-854">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-854">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-855">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-855">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-storage-info-send"></a><span data-ttu-id="4e4bd-856">Informações de armazenamento classe de dispositivo Pima enviar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-856">Device Class Pima Storage Info Send</span></span> 

#### <a name="ux_device_class_pima_storage_info_send"></a><span data-ttu-id="4e4bd-857">ux_device_class_pima_storage_info_send</span><span class="sxs-lookup"><span data-stu-id="4e4bd-857">ux_device_class_pima_storage_info_send</span></span>

<span data-ttu-id="4e4bd-858">**Ícone** ![ Classe de dispositivo Pima Storage Info Enviar ícone](./media/user-guide/usbx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-858">**Icon** ![Device Class Pima Storage Info Send icon](./media/user-guide/usbx-events/image32.png)</span></span>

<span data-ttu-id="4e4bd-859">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-859">**Description**</span></span>

<span data-ttu-id="4e4bd-860">Este evento representa um evento de envio de info de armazenamento Pima classe usbx.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-860">This event represents a USBX Device Class Pima Storage Info Send Event.</span></span>

<span data-ttu-id="4e4bd-861">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-861">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-862">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-862">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-863">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-863">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-864">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-864">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-865">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-865">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-activate"></a><span data-ttu-id="4e4bd-866">Dispositivo Classe Rndis Ativar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-866">Device Class Rndis Activate</span></span> 

#### <a name="ux_device_class_rndis_activate"></a><span data-ttu-id="4e4bd-867">ux_device_class_rndis_activate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-867">ux_device_class_rndis_activate</span></span>

<span data-ttu-id="4e4bd-868">**Ícone** ![ Ícone de ativação classe de dispositivo Rndis](./media/user-guide/usbx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-868">**Icon** ![Device Class Rndis Activate icon](./media/user-guide/usbx-events/image33.png)</span></span>

<span data-ttu-id="4e4bd-869">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-869">**Description**</span></span>

<span data-ttu-id="4e4bd-870">Este evento representa um evento ativado da classe de dispositivo USBX Rndis.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-870">This event represents a USBX Device Class Rndis Activate Event.</span></span>

<span data-ttu-id="4e4bd-871">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-871">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-872">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-872">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-873">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-873">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-874">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-874">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-875">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-875">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-deactivate"></a><span data-ttu-id="4e4bd-876">Classe de dispositivo Rndis Desativar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-876">Device Class Rndis Deactivate</span></span> 

#### <a name="ux_device_class_rndis_deactivate"></a><span data-ttu-id="4e4bd-877">ux_device_class_rndis_deactivate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-877">ux_device_class_rndis_deactivate</span></span>

<span data-ttu-id="4e4bd-878">**Ícone** ![ Ícone de desativado classe de dispositivo Rndis](./media/user-guide/usbx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-878">**Icon** ![Device Class Rndis Deactivate icon](./media/user-guide/usbx-events/image34.png)</span></span>

<span data-ttu-id="4e4bd-879">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-879">**Description**</span></span>

<span data-ttu-id="4e4bd-880">Este evento representa um evento de desativado da classe de dispositivo USBX Rndis.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-880">This event represents a USBX Device Class Rndis Deactivate Event.</span></span>

<span data-ttu-id="4e4bd-881">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-881">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-882">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-882">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-883">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-883">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-884">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-884">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-885">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-885">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-message-keep-alive"></a><span data-ttu-id="4e4bd-886">Mensagem Rndis classe de dispositivo manter vivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-886">Device Class Rndis Message Keep Alive</span></span> 

#### <a name="ux_device_class_rndis_msg_keep_alive"></a><span data-ttu-id="4e4bd-887">ux_device_class_rndis_msg_keep_alive</span><span class="sxs-lookup"><span data-stu-id="4e4bd-887">ux_device_class_rndis_msg_keep_alive</span></span>

<span data-ttu-id="4e4bd-888">**Ícone** ![ Ícone de mensagem Rndis classe de dispositivo Manter vivo](./media/user-guide/usbx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-888">**Icon** ![Device Class Rndis Message Keep Alive icon](./media/user-guide/usbx-events/image35.png)</span></span>

<span data-ttu-id="4e4bd-889">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-889">**Description**</span></span>

<span data-ttu-id="4e4bd-890">Este evento representa um evento de mensagem Rndis da classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-890">This event represents a USBX Device Class Rndis Message Keep Alive Event.</span></span>

<span data-ttu-id="4e4bd-891">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-891">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-892">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-892">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-893">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-893">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-894">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-894">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-895">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-895">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-message-query"></a><span data-ttu-id="4e4bd-896">Consulta de mensagens classe de dispositivo Rndis</span><span class="sxs-lookup"><span data-stu-id="4e4bd-896">Device Class Rndis Message Query</span></span> 

#### <a name="ux_device_class_rndis_msg_keep_query"></a><span data-ttu-id="4e4bd-897">ux_device_class_rndis_msg_keep_query</span><span class="sxs-lookup"><span data-stu-id="4e4bd-897">ux_device_class_rndis_msg_keep_query</span></span>

<span data-ttu-id="4e4bd-898">**Ícone** ![ Ícone de consulta de mensagem classe de dispositivo Rndis](./media/user-guide/usbx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-898">**Icon** ![Device Class Rndis Message Query icon](./media/user-guide/usbx-events/image36.png)</span></span>

<span data-ttu-id="4e4bd-899">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-899">**Description**</span></span>

<span data-ttu-id="4e4bd-900">Este evento representa um evento de consulta de mensagens classe DE dispositivo USBX Rndis.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-900">This event represents a USBX Device Class Rndis Message Query Event.</span></span>

<span data-ttu-id="4e4bd-901">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-901">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-902">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-902">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-903">Info Field 2: Rndis OID.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-903">Info Field 2: Rndis OID.</span></span>
- <span data-ttu-id="4e4bd-904">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-904">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-905">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-905">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-message-reset"></a><span data-ttu-id="4e4bd-906">Reset da mensagem Rndis da classe do dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-906">Device Class Rndis Message Reset</span></span> 

#### <a name="ux_device_class_rndis_msg_reset"></a><span data-ttu-id="4e4bd-907">ux_device_class_rndis_msg_reset</span><span class="sxs-lookup"><span data-stu-id="4e4bd-907">ux_device_class_rndis_msg_reset</span></span>

<span data-ttu-id="4e4bd-908">**Ícone** ![ Ícone de reset de mensagem de classe de dispositivo Rndis](./media/user-guide/usbx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-908">**Icon** ![Device Class Rndis Message Reset icon](./media/user-guide/usbx-events/image37.png)</span></span>

<span data-ttu-id="4e4bd-909">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-909">**Description**</span></span>

<span data-ttu-id="4e4bd-910">Este evento representa um evento de reset de mensagens da classe de dispositivo USBX Rndis.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-910">This event represents a USBX Device Class Rndis Message Reset Event.</span></span>

<span data-ttu-id="4e4bd-911">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-911">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-912">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-912">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-913">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-913">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-914">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-914">Info Field 3: Not used.</span></span>

### <a name="device-class-rndis-message-set"></a><span data-ttu-id="4e4bd-915">Conjunto de mensagens Rndis classe de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-915">Device Class Rndis Message Set</span></span> 

#### <a name="ux_device_class_rndis_msg_set"></a><span data-ttu-id="4e4bd-916">ux_device_class_rndis_msg_set</span><span class="sxs-lookup"><span data-stu-id="4e4bd-916">ux_device_class_rndis_msg_set</span></span>

<span data-ttu-id="4e4bd-917">**Ícone** ![ Ícone de conjunto de mensagem de classe de dispositivo Rndis](./media/user-guide/usbx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-917">**Icon** ![Device Class Rndis Message Set icon](./media/user-guide/usbx-events/image38.png)</span></span>

<span data-ttu-id="4e4bd-918">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-918">**Description**</span></span>

<span data-ttu-id="4e4bd-919">Este evento representa um evento usbx device Class Rndis Message set Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-919">This event represents a USBX Device Class Rndis Message Set Event.</span></span>

<span data-ttu-id="4e4bd-920">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-920">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-921">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-921">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-922">Info Field 2: Rndis OID.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-922">Info Field 2: Rndis OID.</span></span>
- <span data-ttu-id="4e4bd-923">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-923">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-924">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-924">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-packet-receive"></a><span data-ttu-id="4e4bd-925">Pacote classe de dispositivo Rndis Receber</span><span class="sxs-lookup"><span data-stu-id="4e4bd-925">Device Class Rndis Packet Receive</span></span> 

#### <a name="ux_device_class_rndis_packet_receive"></a><span data-ttu-id="4e4bd-926">ux_device_class_rndis_packet_receive</span><span class="sxs-lookup"><span data-stu-id="4e4bd-926">ux_device_class_rndis_packet_receive</span></span>

<span data-ttu-id="4e4bd-927">**Ícone** ![ Ícone de receção de pacote classe de dispositivo Rndis](./media/user-guide/usbx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-927">**Icon** ![Device Class Rndis Packet Receive icon](./media/user-guide/usbx-events/image39.png)</span></span>

<span data-ttu-id="4e4bd-928">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-928">**Description**</span></span>

<span data-ttu-id="4e4bd-929">Este evento representa um evento de receção de pacote de pacote classe USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-929">This event represents a USBX Device Class Rndis Packet Receive Event.</span></span>

<span data-ttu-id="4e4bd-930">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-930">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-931">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-931">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-932">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-932">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-933">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-933">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-934">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-934">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-packet-transmit"></a><span data-ttu-id="4e4bd-935">Transmitir pacote de pacote classe de dispositivo Rndis</span><span class="sxs-lookup"><span data-stu-id="4e4bd-935">Device Class Rndis Packet Transmit</span></span> 

#### <a name="ux_device_class_rndis_packet_transmit"></a><span data-ttu-id="4e4bd-936">ux_device_class_rndis_packet_transmit</span><span class="sxs-lookup"><span data-stu-id="4e4bd-936">ux_device_class_rndis_packet_transmit</span></span>

<span data-ttu-id="4e4bd-937">**Ícone** ![ Ícone de transmissão de pacote de pacote classe de dispositivo Rndis](./media/user-guide/usbx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-937">**Icon** ![Device Class Rndis Packet Transmit icon](./media/user-guide/usbx-events/image40.png)</span></span>

<span data-ttu-id="4e4bd-938">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-938">**Description**</span></span>

<span data-ttu-id="4e4bd-939">Este evento representa um evento de transmissão de pacotes de pacotes usbx classe Rndis.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-939">This event represents a USBX Device Class Rndis Packet Transmit Event.</span></span>

<span data-ttu-id="4e4bd-940">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-940">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-941">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-941">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-942">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-942">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-943">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-943">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-944">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-944">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-activate"></a><span data-ttu-id="4e4bd-945">Ativação de armazenamento de classe de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-945">Device Class Storage Activate</span></span> 

#### <a name="ux_device_class_storage_activate"></a><span data-ttu-id="4e4bd-946">ux_device_class_storage_activate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-946">ux_device_class_storage_activate</span></span>

<span data-ttu-id="4e4bd-947">**Ícone** ![ Ícone ativar o armazenamento da classe do dispositivo](./media/user-guide/usbx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-947">**Icon** ![Device Class Storage Activate icon](./media/user-guide/usbx-events/image41.png)</span></span>

<span data-ttu-id="4e4bd-948">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-948">**Description**</span></span>

<span data-ttu-id="4e4bd-949">Este evento representa um evento usbx device class storage activate Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-949">This event represents a USBX Device Class Storage Activate Event.</span></span>

<span data-ttu-id="4e4bd-950">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-950">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-951">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-951">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-952">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-952">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-953">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-953">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-954">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-954">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-deactivate"></a><span data-ttu-id="4e4bd-955">Armazenamento de classe de dispositivo desativado</span><span class="sxs-lookup"><span data-stu-id="4e4bd-955">Device Class Storage Deactivate</span></span> 

#### <a name="ux_device_class_storage_deactivate"></a><span data-ttu-id="4e4bd-956">ux_device_class_storage_deactivate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-956">ux_device_class_storage_deactivate</span></span>

<span data-ttu-id="4e4bd-957">**Ícone** ![ Ícone de desativação de classe de dispositivo](./media/user-guide/usbx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-957">**Icon** ![Device Class Storage Deactivate icon](./media/user-guide/usbx-events/image42.png)</span></span>

<span data-ttu-id="4e4bd-958">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-958">**Description**</span></span>

<span data-ttu-id="4e4bd-959">Este evento representa um evento de desativação da classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-959">This event represents a USBX Device Class Storage Deactivate Event.</span></span>

<span data-ttu-id="4e4bd-960">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-960">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-961">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-961">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-962">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-962">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-963">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-963">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-964">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-964">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-format"></a><span data-ttu-id="4e4bd-965">Formato de armazenamento de classe de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-965">Device Class Storage Format</span></span> 

#### <a name="ux_device_class_storage_format"></a><span data-ttu-id="4e4bd-966">ux_device_class_storage_format</span><span class="sxs-lookup"><span data-stu-id="4e4bd-966">ux_device_class_storage_format</span></span>

<span data-ttu-id="4e4bd-967">**Ícone** ![ Ícone de formato de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-967">**Icon** ![Device Class Storage Format icon](./media/user-guide/usbx-events/image43.png)</span></span>

<span data-ttu-id="4e4bd-968">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-968">**Description**</span></span>

<span data-ttu-id="4e4bd-969">Este evento representa um evento de formato de armazenamento de classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-969">This event represents a USBX Device Class Storage Format Event.</span></span>

<span data-ttu-id="4e4bd-970">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-970">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-971">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-971">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-972">Info Field 2: Lun.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-972">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4e4bd-973">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-973">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-974">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-974">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-inquiry"></a><span data-ttu-id="4e4bd-975">Inquérito de armazenamento de classe de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-975">Device Class Storage Inquiry</span></span> 

#### <a name="ux_device_class_storage_inquiry"></a><span data-ttu-id="4e4bd-976">ux_device_class_storage_inquiry</span><span class="sxs-lookup"><span data-stu-id="4e4bd-976">ux_device_class_storage_inquiry</span></span>

<span data-ttu-id="4e4bd-977">**Ícone** ![ Ícone de inquérito de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-977">**Icon** ![Device Class Storage Inquiry icon](./media/user-guide/usbx-events/image44.png)</span></span>

<span data-ttu-id="4e4bd-978">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-978">**Description**</span></span>

<span data-ttu-id="4e4bd-979">Este evento representa um evento de investigação de armazenamento de classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-979">This event represents a USBX Device Class Storage Inquiry Event.</span></span>

<span data-ttu-id="4e4bd-980">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-980">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-981">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-981">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-982">Info Field 2: Lun.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-982">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4e4bd-983">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-983">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-984">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-984">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-mode-select"></a><span data-ttu-id="4e4bd-985">Selecione o modo de armazenamento da classe do dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-985">Device Class Storage Mode Select</span></span>

#### <a name="ux_device_class_storage_mode_select"></a><span data-ttu-id="4e4bd-986">ux_device_class_storage_mode_select</span><span class="sxs-lookup"><span data-stu-id="4e4bd-986">ux_device_class_storage_mode_select</span></span>

<span data-ttu-id="4e4bd-987">**Ícone** ![ Modo de armazenamento de classe de dispositivo Selecionar ícone](./media/user-guide/usbx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-987">**Icon** ![Device Class Storage Mode Select icon](./media/user-guide/usbx-events/image45.png)</span></span>

<span data-ttu-id="4e4bd-988">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-988">**Description**</span></span>

<span data-ttu-id="4e4bd-989">Este evento representa um evento de seleção do modo de armazenamento da classe do dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-989">This event represents a USBX Device Class Storage Mode Select Event.</span></span>

<span data-ttu-id="4e4bd-990">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-990">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-991">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-991">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-992">Info Field 2: Lun.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-992">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4e4bd-993">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-993">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-994">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-994">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-mode-sense"></a><span data-ttu-id="4e4bd-995">Sentido do modo de armazenamento da classe do dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-995">Device Class Storage Mode Sense</span></span> 

#### <a name="ux_device_class_storage_mode_sense"></a><span data-ttu-id="4e4bd-996">ux_device_class_storage_mode_sense</span><span class="sxs-lookup"><span data-stu-id="4e4bd-996">ux_device_class_storage_mode_sense</span></span>

<span data-ttu-id="4e4bd-997">**Ícone** ![ Ícone de sentido de modo de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-997">**Icon** ![Device Class Storage Mode Sense icon](./media/user-guide/usbx-events/image46.png)</span></span>

<span data-ttu-id="4e4bd-998">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-998">**Description**</span></span>

<span data-ttu-id="4e4bd-999">Este evento representa um evento de modo de armazenamento de classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-999">This event represents a USBX Device Class Storage Mode Sense Event.</span></span>

<span data-ttu-id="4e4bd-1000">Campos de Informação</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1000">Information Fields</span></span> 

- <span data-ttu-id="4e4bd-1001">nfo Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1001">nfo Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-1002">Info Field 2: Lun.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1002">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4e4bd-1003">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1003">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1004">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1004">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-prevent-allow-media-removal"></a><span data-ttu-id="4e4bd-1005">Armazenamento de classe de dispositivo impede a remoção dos meios de comunicação</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1005">Device Class Storage Prevent Allow Media Removal</span></span> 

#### <a name="ux_device_class_storage_prevent_allow_media_removal"></a><span data-ttu-id="4e4bd-1006">ux_device_class_storage_prevent_allow_media_removal</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1006">ux_device_class_storage_prevent_allow_media_removal</span></span>

<span data-ttu-id="4e4bd-1007">**Ícone** ![ Armazenamento de classe de dispositivo Previne permitir ícone de remoção de mídia](./media/user-guide/usbx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1007">**Icon** ![Device Class Storage Prevent Allow Media Removal icon](./media/user-guide/usbx-events/image47.png)</span></span>

<span data-ttu-id="4e4bd-1008">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1008">**Description**</span></span>

<span data-ttu-id="4e4bd-1009">Este evento representa um armazenamento da classe do dispositivo USBX Prevent Allow Media Removal Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1009">This event represents a USBX Device Class Storage Prevent Allow Media Removal Event.</span></span>

<span data-ttu-id="4e4bd-1010">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1010">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1011">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1011">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-1012">Info Field 2: Lun.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1012">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4e4bd-1013">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1013">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1014">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1014">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-read"></a><span data-ttu-id="4e4bd-1015">Leitura de armazenamento de classe de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1015">Device Class Storage Read</span></span> 

#### <a name="ux_device_class_storage_read"></a><span data-ttu-id="4e4bd-1016">ux_device_class_storage_read</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1016">ux_device_class_storage_read</span></span>

<span data-ttu-id="4e4bd-1017">**Ícone** ![ Ícone de leitura de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1017">**Icon** ![Device Class Storage Read icon](./media/user-guide/usbx-events/image48.png)</span></span>

<span data-ttu-id="4e4bd-1018">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1018">**Description**</span></span>

<span data-ttu-id="4e4bd-1019">Este evento representa um evento de leitura de armazenamento de classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1019">This event represents a USBX Device Class Storage Read Event.</span></span>

<span data-ttu-id="4e4bd-1020">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1020">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1021">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1021">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-1022">Info Field 2: Lun.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1022">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4e4bd-1023">Campo de Informação 3: Sector.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1023">Info Field 3: Sector.</span></span>
- <span data-ttu-id="4e4bd-1024">Info Field 4: Sectores numerais.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1024">Info Field 4: Number sectors.</span></span>

### <a name="device-class-storage-read-capacity"></a><span data-ttu-id="4e4bd-1025">Capacidade de leitura de armazenamento de classe de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1025">Device Class Storage Read Capacity</span></span> 

#### <a name="ux_device_class_storage_read_capacity"></a><span data-ttu-id="4e4bd-1026">ux_device_class_storage_read_capacity</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1026">ux_device_class_storage_read_capacity</span></span>

<span data-ttu-id="4e4bd-1027">**Ícone** ![ Ícone de capacidade de leitura de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1027">**Icon** ![Device Class Storage Read Capacity icon](./media/user-guide/usbx-events/image49.png)</span></span>

<span data-ttu-id="4e4bd-1028">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1028">**Description**</span></span>

<span data-ttu-id="4e4bd-1029">Este evento representa um evento de capacidade de leitura de armazenamento de classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1029">This event represents a USBX Device Class Storage Read Capacity Event.</span></span>

<span data-ttu-id="4e4bd-1030">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1030">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1031">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1031">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-1032">Info Field 2: Lun.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1032">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4e4bd-1033">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1033">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1034">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1034">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-read-format-capacity"></a><span data-ttu-id="4e4bd-1035">Capacidade de leitura de formato de leitura de classe de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1035">Device Class Storage Read Format Capacity</span></span> 

#### <a name="ux_device_class_storage_read_format_capacity"></a><span data-ttu-id="4e4bd-1036">ux_device_class_storage_read_format_capacity</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1036">ux_device_class_storage_read_format_capacity</span></span>

<span data-ttu-id="4e4bd-1037">**Ícone** ![ Ícone de capacidade de leitura de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1037">**Icon** ![Device Class Storage Read Format Capacity icon](./media/user-guide/usbx-events/image50.png)</span></span>

<span data-ttu-id="4e4bd-1038">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1038">**Description**</span></span>

<span data-ttu-id="4e4bd-1039">Este evento representa um evento de capacidade de leitura de armazenamento de classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1039">This event represents a USBX Device Class Storage Read Format Capacity Event.</span></span>

<span data-ttu-id="4e4bd-1040">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1040">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1041">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1041">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-1042">Info Field 2: Lun.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1042">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4e4bd-1043">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1043">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1044">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1044">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-read-toc"></a><span data-ttu-id="4e4bd-1045">Armazenamento de classe de dispositivo Leia TOC</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1045">Device Class Storage Read TOC</span></span> 

#### <a name="ux_device_class_storage_read_toc"></a><span data-ttu-id="4e4bd-1046">ux_device_class_storage_read_toc</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1046">ux_device_class_storage_read_toc</span></span>

<span data-ttu-id="4e4bd-1047">**Ícone** ![ Armazenamento de classe de dispositivo Leia o ícone TOC](./media/user-guide/usbx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1047">**Icon** ![Device Class Storage Read TOC icon](./media/user-guide/usbx-events/image51.png)</span></span>

<span data-ttu-id="4e4bd-1048">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1048">**Description**</span></span>

<span data-ttu-id="4e4bd-1049">Este evento representa um evento DE ARMAZENAMENTO DE CLASSE USBX De Dispositivo Leia O EVENTO TOC.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1049">This event represents a USBX Device Class Storage Read TOC Event.</span></span>

<span data-ttu-id="4e4bd-1050">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1050">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1051">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1051">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-1052">Info Field 2: Lun.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1052">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4e4bd-1053">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1053">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1054">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1054">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-request-sense"></a><span data-ttu-id="4e4bd-1055">Sentido do pedido de armazenamento de classe de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1055">Device Class Storage Request Sense</span></span> 

#### <a name="ux_device_class_storage_request_sense"></a><span data-ttu-id="4e4bd-1056">ux_device_class_storage_request_sense</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1056">ux_device_class_storage_request_sense</span></span>

<span data-ttu-id="4e4bd-1057">**Ícone** ![ Ícone de pedido de pedido de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1057">**Icon** ![Device Class Storage Request Sense icon](./media/user-guide/usbx-events/image52.png)</span></span>

<span data-ttu-id="4e4bd-1058">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1058">**Description**</span></span>

<span data-ttu-id="4e4bd-1059">Este evento representa um evento de pedido de armazenamento de classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1059">This event represents a USBX Device Class Storage Request Sense Event.</span></span>

<span data-ttu-id="4e4bd-1060">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1060">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1061">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1061">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-1062">Info Field 2: Lun.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1062">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4e4bd-1063">Info Field 3: Chave de sentido.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1063">Info Field 3: Sense key.</span></span>
- <span data-ttu-id="4e4bd-1064">Info Field 4: Código.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1064">Info Field 4: Code.</span></span>

### <a name="device-class-storage-start-stop"></a><span data-ttu-id="4e4bd-1065">Paragem de início de armazenamento de classe de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1065">Device Class Storage Start Stop</span></span> 

#### <a name="ux_device_class_storage_start_stop"></a><span data-ttu-id="4e4bd-1066">ux_device_class_storage_start_stop</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1066">ux_device_class_storage_start_stop</span></span>

<span data-ttu-id="4e4bd-1067">**Ícone** ![ Ícone de início de paragem de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1067">**Icon** ![Device Class Storage Start Stop icon](./media/user-guide/usbx-events/image53.png)</span></span>

<span data-ttu-id="4e4bd-1068">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1068">**Description**</span></span>

<span data-ttu-id="4e4bd-1069">Este evento representa um evento de paragem de início de armazenamento da classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1069">This event represents a USBX Device Class Storage Start Stop Event.</span></span>

<span data-ttu-id="4e4bd-1070">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1070">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1071">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1071">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-1072">Info Field 2: Lun.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1072">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4e4bd-1073">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1073">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1074">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1074">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-test-ready"></a><span data-ttu-id="4e4bd-1075">Teste de armazenamento de classe de dispositivo pronto</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1075">Device Class Storage Test Ready</span></span> 

#### <a name="ux_device_class_storage_test_ready"></a><span data-ttu-id="4e4bd-1076">ux_device_class_storage_test_ready</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1076">ux_device_class_storage_test_ready</span></span>

<span data-ttu-id="4e4bd-1077">**Ícone** ![ Ícone de teste de armazenamento de classe de dispositivo pronto](./media/user-guide/usbx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1077">**Icon** ![Device Class Storage Test Ready icon](./media/user-guide/usbx-events/image54.png)</span></span>

<span data-ttu-id="4e4bd-1078">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1078">**Description**</span></span>

<span data-ttu-id="4e4bd-1079">Este evento representa um evento pronto para o teste de armazenamento da classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1079">This event represents a USBX Device Class Storage Test Ready Event.</span></span>

<span data-ttu-id="4e4bd-1080">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1080">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1081">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1081">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-1082">Info Field 2: Lun.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1082">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4e4bd-1083">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1083">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1084">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1084">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-verify"></a><span data-ttu-id="4e4bd-1085">Armazenamento de classe de dispositivo Verificar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1085">Device Class Storage Verify</span></span> 

#### <a name="ux_device_class_storage_verify"></a><span data-ttu-id="4e4bd-1086">ux_device_class_storage_verify</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1086">ux_device_class_storage_verify</span></span>

<span data-ttu-id="4e4bd-1087">**Ícone** ![ Ícone de verificação de classe de dispositivo](./media/user-guide/usbx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1087">**Icon** ![Device Class Storage Verify icon](./media/user-guide/usbx-events/image55.png)</span></span>

<span data-ttu-id="4e4bd-1088">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1088">**Description**</span></span>

<span data-ttu-id="4e4bd-1089">Este evento representa um evento de verificação da classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1089">This event represents a USBX Device Class Storage Verify Event.</span></span>

<span data-ttu-id="4e4bd-1090">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1090">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1091">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1091">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-1092">Info Field 2: Lun.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1092">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4e4bd-1093">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1093">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1094">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1094">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-write"></a><span data-ttu-id="4e4bd-1095">Escrita de armazenamento de classe de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1095">Device Class Storage Write</span></span> 

#### <a name="ux_device_class_storage_write"></a><span data-ttu-id="4e4bd-1096">ux_device_class_storage_write</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1096">ux_device_class_storage_write</span></span>

<span data-ttu-id="4e4bd-1097">**Ícone** ![ Ícone de escrita de classe de dispositivo](./media/user-guide/usbx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1097">**Icon** ![Device Class Storage Write icon](./media/user-guide/usbx-events/image56.png)</span></span>

<span data-ttu-id="4e4bd-1098">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1098">**Description**</span></span>

<span data-ttu-id="4e4bd-1099">Este evento representa um evento de escrita de classe de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1099">This event represents a USBX Device Class Storage Write Event.</span></span>

<span data-ttu-id="4e4bd-1100">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1100">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1101">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1101">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-1102">Info Field 2: Lun.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1102">Info Field 2: Lun.</span></span>
- <span data-ttu-id="4e4bd-1103">Campo de Informação 3: Sector.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1103">Info Field 3: Sector.</span></span>
- <span data-ttu-id="4e4bd-1104">Info Field 4: Sectores numerais.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1104">Info Field 4: Number sectors.</span></span>

### <a name="device-stack-alternate-setting-get"></a><span data-ttu-id="4e4bd-1105">Configuração alternativa de pilha de dispositivo obter</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1105">Device Stack Alternate Setting Get</span></span> 

#### <a name="ux_device_class_alternate_setting_get"></a><span data-ttu-id="4e4bd-1106">ux_device_class_alternate_setting_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1106">ux_device_class_alternate_setting_get</span></span>

<span data-ttu-id="4e4bd-1107">**Ícone** ![ Configuração alternativa de pilha de dispositivo Obter ícone](./media/user-guide/usbx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1107">**Icon** ![Device Stack Alternate Setting Get icon](./media/user-guide/usbx-events/image57.png)</span></span>

<span data-ttu-id="4e4bd-1108">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1108">**Description**</span></span>

<span data-ttu-id="4e4bd-1109">Este evento representa um evento de configuração alternativa de configuração alternativa de pilha de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1109">This event represents a USBX Device Stack Alternate Setting Get Event.</span></span>

<span data-ttu-id="4e4bd-1110">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1110">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1111">Info Field 1: Valor da interface.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1111">Info Field 1: Interface value.</span></span>
- <span data-ttu-id="4e4bd-1112">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1112">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1113">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1113">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1114">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1114">Info Field 4: Not used.</span></span>

### <a name="device-stack-alternate-setting-set"></a><span data-ttu-id="4e4bd-1115">Conjunto de definição alternativa de pilha de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1115">Device Stack Alternate Setting Set</span></span> 

#### <a name="ux_device_class_alternate_setting_set"></a><span data-ttu-id="4e4bd-1116">ux_device_class_alternate_setting_set</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1116">ux_device_class_alternate_setting_set</span></span>

<span data-ttu-id="4e4bd-1117">**Ícone** ![ Ícone de definição alternativa de configuração de pilha de dispositivo](./media/user-guide/usbx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1117">**Icon** ![Device Stack Alternate Setting Set icon](./media/user-guide/usbx-events/image58.png)</span></span>

<span data-ttu-id="4e4bd-1118">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1118">**Description**</span></span>

<span data-ttu-id="4e4bd-1119">Este evento representa um evento de definição alternativa de pilha de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1119">This event represents a USBX Device Stack Alternate Setting Set Event.</span></span>

<span data-ttu-id="4e4bd-1120">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1120">**Information Fields**</span></span>
- <span data-ttu-id="4e4bd-1121">Info Field 1: Valor da interface.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1121">Info Field 1: Interface value.</span></span>
- <span data-ttu-id="4e4bd-1122">Info Field 2: Valor de definição alternativo.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1122">Info Field 2: Alternate setting value.</span></span>
- <span data-ttu-id="4e4bd-1123">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1123">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1124">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1124">Info Field 4: Not used.</span></span>

### <a name="device-stack-class-register"></a><span data-ttu-id="4e4bd-1125">Registo de classe de pilha de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1125">Device Stack Class Register</span></span> 

#### <a name="ux_device_stack_class_register"></a><span data-ttu-id="4e4bd-1126">ux_device_stack_class_register</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1126">ux_device_stack_class_register</span></span>

<span data-ttu-id="4e4bd-1127">**Ícone** ![ Ícone de registo de classe de pilha de dispositivo](./media/user-guide/usbx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1127">**Icon** ![Device Stack Class Register icon](./media/user-guide/usbx-events/image59.png)</span></span>

<span data-ttu-id="4e4bd-1128">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1128">**Description**</span></span>

<span data-ttu-id="4e4bd-1129">Este evento representa um evento usbx device stack class register Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1129">This event represents a USBX Device Stack Class Register Event.</span></span>

<span data-ttu-id="4e4bd-1130">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1130">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1131">Info Field 1: Nome da classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1131">Info Field 1: Class name.</span></span>
- <span data-ttu-id="4e4bd-1132">Info Field 2: Número de interface.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1132">Info Field 2: Interface number.</span></span>
- <span data-ttu-id="4e4bd-1133">Info Field 3: Parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1133">Info Field 3: Parameter.</span></span>
- <span data-ttu-id="4e4bd-1134">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1134">Info Field 4: Not used.</span></span>

### <a name="device-stack-clear-feature"></a><span data-ttu-id="4e4bd-1135">Recurso de limpar a pilha de dispositivos</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1135">Device Stack Clear Feature</span></span> 

#### <a name="ux_device_stack_clear_feature"></a><span data-ttu-id="4e4bd-1136">ux_device_stack_clear_feature</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1136">ux_device_stack_clear_feature</span></span>

<span data-ttu-id="4e4bd-1137">**Ícone** ![ Ícone de funcionalidade de limpação de pilha de dispositivo](./media/user-guide/usbx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1137">**Icon** ![Device Stack Clear Feature icon](./media/user-guide/usbx-events/image60.png)</span></span>

<span data-ttu-id="4e4bd-1138">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1138">**Description**</span></span>

<span data-ttu-id="4e4bd-1139">Este evento representa um evento de funcionalidade limpa de pilha de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1139">This event represents a USBX Device Stack Clear Feature Event.</span></span>

<span data-ttu-id="4e4bd-1140">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1140">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1141">Informação Campo 1: Tipo de pedido.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1141">Info Field 1: Request type.</span></span>
- <span data-ttu-id="4e4bd-1142">Informação Campo 2: Valor de pedido.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1142">Info Field 2: Request value.</span></span> <span data-ttu-id="4e4bd-1143">Info Field 3: Índice de pedido.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1143">Info Field 3: Request index.</span></span>
- <span data-ttu-id="4e4bd-1144">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1144">Info Field 4: Not used.</span></span>

### <a name="device-stack-configuration-get"></a><span data-ttu-id="4e4bd-1145">Configuração de pilha de dispositivo obter</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1145">Device Stack Configuration Get</span></span> 

#### <a name="ux_device_stack_configuration_get-t"></a><span data-ttu-id="4e4bd-1146">ux_device_stack_configuration_get t</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1146">ux_device_stack_configuration_get t</span></span>

<span data-ttu-id="4e4bd-1147">**Ícone** ![ Configuração de pilha de dispositivo Obter ícone](./media/user-guide/usbx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1147">**Icon** ![Device Stack Configuration Get icon](./media/user-guide/usbx-events/image61.png)</span></span>

<span data-ttu-id="4e4bd-1148">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1148">**Description**</span></span>

<span data-ttu-id="4e4bd-1149">Este evento representa um evento de configuração de pilha de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1149">This event represents a USBX Device Stack Configuration Get Event.</span></span>

<span data-ttu-id="4e4bd-1150">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1150">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1151">Info Field 1: Valor de configuração.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1151">Info Field 1: Configuration value.</span></span>
- <span data-ttu-id="4e4bd-1152">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1152">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1153">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1153">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1154">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1154">Info Field 4: Not used.</span></span>

### <a name="device-stack-configuration-set"></a><span data-ttu-id="4e4bd-1155">Conjunto de configuração de pilha de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1155">Device Stack Configuration Set</span></span> 

#### <a name="ux_device_stack_configuration_set"></a><span data-ttu-id="4e4bd-1156">ux_device_stack_configuration_set</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1156">ux_device_stack_configuration_set</span></span>

<span data-ttu-id="4e4bd-1157">**Ícone** ![ Ícone de conjunto de configuração de pilha de dispositivo](./media/user-guide/usbx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1157">**Icon** ![Device Stack Configuration Set icon](./media/user-guide/usbx-events/image62.png)</span></span>

<span data-ttu-id="4e4bd-1158">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1158">**Description**</span></span>

<span data-ttu-id="4e4bd-1159">Este evento representa um evento de configuração de configuração de pilha de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1159">This event represents a USBX Device Stack Configuration Set Event.</span></span>

<span data-ttu-id="4e4bd-1160">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1160">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1161">Info Field 1: Valor de configuração.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1161">Info Field 1: Configuration value.</span></span>
- <span data-ttu-id="4e4bd-1162">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1162">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1163">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1163">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1164">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1164">Info Field 4: Not used.</span></span>

### <a name="device-stack-connect"></a><span data-ttu-id="4e4bd-1165">Ligação de pilha de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1165">Device Stack Connect</span></span> 

#### <a name="ux_device_stack_connect"></a><span data-ttu-id="4e4bd-1166">ux_device_stack_connect</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1166">ux_device_stack_connect</span></span>

<span data-ttu-id="4e4bd-1167">**Ícone** ![ Ícone de conexão de pilha de dispositivo](./media/user-guide/usbx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1167">**Icon** ![Device Stack Connect icon](./media/user-guide/usbx-events/image63.png)</span></span>

<span data-ttu-id="4e4bd-1168">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1168">**Description**</span></span>

<span data-ttu-id="4e4bd-1169">Este evento representa um evento de envio de pilha de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1169">This event represents a USBX Device Stack Descriptor Send Event.</span></span>

<span data-ttu-id="4e4bd-1170">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1170">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1171">Info Field 1: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1171">Info Field 1: Not used.</span></span>
- <span data-ttu-id="4e4bd-1172">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1172">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1173">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1173">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1174">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1174">Info Field 4: Not used.</span></span>

### <a name="device-stack-descriptor-send"></a><span data-ttu-id="4e4bd-1175">Envio de descritor de pilha de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1175">Device Stack Descriptor Send</span></span> 

#### <a name="ux_device_stack_descriptor_send"></a><span data-ttu-id="4e4bd-1176">ux_device_stack_descriptor_send</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1176">ux_device_stack_descriptor_send</span></span>

<span data-ttu-id="4e4bd-1177">**Ícone** ![ Descritor de pilha de dispositivo Enviar ícone](./media/user-guide/usbx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1177">**Icon** ![Device Stack Descriptor Send icon](./media/user-guide/usbx-events/image64.png)</span></span>

<span data-ttu-id="4e4bd-1178">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1178">**Description**</span></span>

<span data-ttu-id="4e4bd-1179">Este evento representa um evento de envio de pilha de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1179">This event represents a USBX Device Stack Descriptor Send Event.</span></span>

<span data-ttu-id="4e4bd-1180">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1180">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1181">Info Field 1: Tipo de descritor.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1181">Info Field 1: Descriptor type.</span></span>
- <span data-ttu-id="4e4bd-1182">Info Field 2: Índice de pedido.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1182">Info Field 2: Request index.</span></span>
- <span data-ttu-id="4e4bd-1183">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1183">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1184">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1184">Info Field 4: Not used.</span></span>

### <a name="device-stack-disconnect"></a><span data-ttu-id="4e4bd-1185">Desconexão da pilha de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1185">Device Stack Disconnect</span></span> 

#### <a name="ux_device_stack_disconnect"></a><span data-ttu-id="4e4bd-1186">ux_device_stack_disconnect</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1186">ux_device_stack_disconnect</span></span>

<span data-ttu-id="4e4bd-1187">**Ícone** ![ Ícone de desconexão de pilha de dispositivo](./media/user-guide/usbx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1187">**Icon** ![Device Stack Disconnect icon](./media/user-guide/usbx-events/image65.png)</span></span>

<span data-ttu-id="4e4bd-1188">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1188">**Description**</span></span>

<span data-ttu-id="4e4bd-1189">Este evento representa um evento de desconexão de pilhas de dispositivos USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1189">This event represents a USBX Device Stack Disconnect Event.</span></span>

<span data-ttu-id="4e4bd-1190">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1190">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1191">Info Field 1: Dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1191">Info Field 1: Device.</span></span>
- <span data-ttu-id="4e4bd-1192">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1192">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1193">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1193">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1194">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1194">Info Field 4: Not used.</span></span>

### <a name="device-stack-endpoint-stall"></a><span data-ttu-id="4e4bd-1195">Dispositivo Stack Endpoint Stall</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1195">Device Stack Endpoint Stall</span></span> 

#### <a name="ux_device_stack_endpoint_stall"></a><span data-ttu-id="4e4bd-1196">ux_device_stack_endpoint_stall</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1196">ux_device_stack_endpoint_stall</span></span>

<span data-ttu-id="4e4bd-1197">**Ícone** ![ Ícone de ponto final de pilha de dispositivo](./media/user-guide/usbx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1197">**Icon** ![Device Stack Endpoint Stall icon](./media/user-guide/usbx-events/image66.png)</span></span>

<span data-ttu-id="4e4bd-1198">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1198">**Description**</span></span>

<span data-ttu-id="4e4bd-1199">Este evento representa um evento de final de dispositivo USBX Stack.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1199">This event represents a USBX Device Stack Endpoint Stall Event.</span></span>

<span data-ttu-id="4e4bd-1200">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1200">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1201">Info Field 1: Ponto final.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1201">Info Field 1: Endpoint.</span></span>
- <span data-ttu-id="4e4bd-1202">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1202">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1203">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1203">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1204">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1204">Info Field 4: Not used.</span></span>

### <a name="device-stack-get-status"></a><span data-ttu-id="4e4bd-1205">Estado da pilha de dispositivos</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1205">Device Stack Get Status</span></span> 

#### <a name="ux_device_stack_get_status"></a><span data-ttu-id="4e4bd-1206">ux_device_stack_get_status</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1206">ux_device_stack_get_status</span></span>

<span data-ttu-id="4e4bd-1207">**Ícone** ![ Ícone de estado da pilha de dispositivo](./media/user-guide/usbx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1207">**Icon** ![Device Stack Get Status icon](./media/user-guide/usbx-events/image67.png)</span></span>

<span data-ttu-id="4e4bd-1208">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1208">**Description**</span></span>

<span data-ttu-id="4e4bd-1209">Este evento representa um evento usbx device stack get status event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1209">This event represents a USBX Device Stack Get Status Event.</span></span>

<span data-ttu-id="4e4bd-1210">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1210">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1211">Info Field 1: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1211">Info Field 1: Not used.</span></span>
- <span data-ttu-id="4e4bd-1212">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1212">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1213">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1213">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1214">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1214">Info Field 4: Not used.</span></span>

### <a name="device-stack-host-wakeup"></a><span data-ttu-id="4e4bd-1215">Wakeup do anfitrião do dispositivo stack</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1215">Device Stack Host Wakeup</span></span> 

#### <a name="ux_device_stack_host_wakeup"></a><span data-ttu-id="4e4bd-1216">ux_device_stack_host_wakeup</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1216">ux_device_stack_host_wakeup</span></span>

<span data-ttu-id="4e4bd-1217">**Ícone** ![ Ícone de wakeup do anfitrião do dispositivo stack](./media/user-guide/usbx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1217">**Icon** ![Device Stack Host Wakeup icon](./media/user-guide/usbx-events/image68.png)</span></span>

<span data-ttu-id="4e4bd-1218">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1218">**Description**</span></span>

<span data-ttu-id="4e4bd-1219">Este evento representa um evento de wakeup anfitrião usbx device stack.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1219">This event represents a USBX Device Stack Host Wakeup Event.</span></span>

<span data-ttu-id="4e4bd-1220">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1220">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1221">Info Field 1: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1221">Info Field 1: Not used.</span></span>
- <span data-ttu-id="4e4bd-1222">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1222">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1223">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1223">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1224">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1224">Info Field 4: Not used.</span></span>

### <a name="device-stack-initialize"></a><span data-ttu-id="4e4bd-1225">Stack de dispositivo Inicialize</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1225">Device Stack Initialize</span></span> 

#### <a name="ux_device_stack_initialize"></a><span data-ttu-id="4e4bd-1226">ux_device_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1226">ux_device_stack_initialize</span></span>

<span data-ttu-id="4e4bd-1227">**Ícone** ![ Ícone inicialize da pilha de dispositivo](./media/user-guide/usbx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1227">**Icon** ![Device Stack Initialize icon](./media/user-guide/usbx-events/image69.png)</span></span>

<span data-ttu-id="4e4bd-1228">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1228">**Description**</span></span>

<span data-ttu-id="4e4bd-1229">Este evento representa um evento de stack de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1229">This event represents a USBX Device Stack Initialize Event.</span></span>

<span data-ttu-id="4e4bd-1230">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1230">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1231">Info Field 1: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1231">Info Field 1: Not used.</span></span>
- <span data-ttu-id="4e4bd-1232">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1232">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1233">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1233">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1234">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1234">Info Field 4: Not used.</span></span>

### <a name="device-stack-interface-delete"></a><span data-ttu-id="4e4bd-1235">Interface de pilha de dispositivos Eliminar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1235">Device Stack Interface Delete</span></span> 

#### <a name="ux_device_stack_interface_delete"></a><span data-ttu-id="4e4bd-1236">ux_device_stack_interface_delete</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1236">ux_device_stack_interface_delete</span></span>

<span data-ttu-id="4e4bd-1237">**Ícone** ![ Ícone de eliminação da interface da pilha de dispositivo](./media/user-guide/usbx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1237">**Icon** ![Device Stack Interface Delete icon](./media/user-guide/usbx-events/image70.png)</span></span>

<span data-ttu-id="4e4bd-1238">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1238">**Description**</span></span>

<span data-ttu-id="4e4bd-1239">Este evento representa um evento de eliminação da interface da stack de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1239">This event represents a USBX Device Stack Interface Delete Event.</span></span>

<span data-ttu-id="4e4bd-1240">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1240">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1241">Info Field 1: Interface.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1241">Info Field 1: Interface.</span></span>
- <span data-ttu-id="4e4bd-1242">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1242">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1243">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1243">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1244">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1244">Info Field 4: Not used.</span></span>

### <a name="device-stack-interface-get"></a><span data-ttu-id="4e4bd-1245">Interface de stack de dispositivo obter</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1245">Device Stack Interface Get</span></span> 

#### <a name="ux_device_stack_interface_get"></a><span data-ttu-id="4e4bd-1246">ux_device_stack_interface_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1246">ux_device_stack_interface_get</span></span>

<span data-ttu-id="4e4bd-1247">**Ícone** ![ Interface de pilha de dispositivo Obter ícone](./media/user-guide/usbx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1247">**Icon** ![Device Stack Interface Get icon](./media/user-guide/usbx-events/image71.png)</span></span>

<span data-ttu-id="4e4bd-1248">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1248">**Description**</span></span>

<span data-ttu-id="4e4bd-1249">Este evento representa um evento de interface de stack de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1249">This event represents a USBX Device Stack Interface Get Event.</span></span>

<span data-ttu-id="4e4bd-1250">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1250">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1251">Info Field 1: Valor da interface.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1251">Info Field 1: Interface value.</span></span>
- <span data-ttu-id="4e4bd-1252">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1252">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1253">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1253">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1254">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1254">Info Field 4: Not used.</span></span>

### <a name="device-stack-interface-set"></a><span data-ttu-id="4e4bd-1255">Conjunto de interface de pilha de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1255">Device Stack Interface Set</span></span> 

#### <a name="ux_device_stack_interface_set"></a><span data-ttu-id="4e4bd-1256">ux_device_stack_interface_set</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1256">ux_device_stack_interface_set</span></span>

<span data-ttu-id="4e4bd-1257">**Ícone** ![ Ícone de conjunto de interface de pilha de dispositivo](./media/user-guide/usbx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1257">**Icon** ![Device Stack Interface Set icon](./media/user-guide/usbx-events/image72.png)</span></span>

<span data-ttu-id="4e4bd-1258">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1258">**Description**</span></span>

<span data-ttu-id="4e4bd-1259">Este evento representa um evento usbx device stack interface set.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1259">This event represents a USBX Device Stack Interface Set Event.</span></span>

<span data-ttu-id="4e4bd-1260">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1260">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1261">Informação Campo 1: Valor de pedido.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1261">Info Field 1: Request value.</span></span> <span data-ttu-id="4e4bd-1262">Info Field 2: Índice de pedido.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1262">Info Field 2: Request index.</span></span>
- <span data-ttu-id="4e4bd-1263">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1263">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1264">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1264">Info Field 4: Not used.</span></span>

### <a name="device-stack-set-feature"></a><span data-ttu-id="4e4bd-1265">Função de conjunto de pilha de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1265">Device Stack Set Feature</span></span> 

#### <a name="ux_device_stack_set_feature"></a><span data-ttu-id="4e4bd-1266">ux_device_stack_set_feature</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1266">ux_device_stack_set_feature</span></span>

<span data-ttu-id="4e4bd-1267">**Ícone** ![ Ícone de funcionalidade de conjunto de pilha de dispositivo](./media/user-guide/usbx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1267">**Icon** ![Device Stack Set Feature icon](./media/user-guide/usbx-events/image73.png)</span></span>

<span data-ttu-id="4e4bd-1268">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1268">**Description**</span></span>

<span data-ttu-id="4e4bd-1269">Este evento representa um evento de funcionalidade de conjunto de dispositivos USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1269">This event represents a USBX Device Stack Set Feature Event.</span></span>

<span data-ttu-id="4e4bd-1270">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1270">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1271">Informação Campo 1: Valor de pedido.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1271">Info Field 1: Request value.</span></span> <span data-ttu-id="4e4bd-1272">Info Field 2: Índice de pedido.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1272">Info Field 2: Request index.</span></span>
- <span data-ttu-id="4e4bd-1273">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1273">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1274">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1274">Info Field 4: Not used.</span></span>

### <a name="device-stack-transfer-abort"></a><span data-ttu-id="4e4bd-1275">Abortar transferência de pilha de dispositivos</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1275">Device Stack Transfer Abort</span></span> 

#### <a name="ux_device_stack_transfer_abort"></a><span data-ttu-id="4e4bd-1276">ux_device_stack_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1276">ux_device_stack_transfer_abort</span></span>

<span data-ttu-id="4e4bd-1277">**Ícone** ![ Ícone de aborto de transferência de pilha de dispositivo](./media/user-guide/usbx-events/image74.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1277">**Icon** ![Device Stack Transfer Abort icon](./media/user-guide/usbx-events/image74.png)</span></span>

<span data-ttu-id="4e4bd-1278">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1278">**Description**</span></span>

<span data-ttu-id="4e4bd-1279">Este evento representa um evento de transferência de pilha de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1279">This event represents a USBX Device Stack Transfer Abort Event.</span></span>

<span data-ttu-id="4e4bd-1280">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1280">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1281">Info Field 1: Pedido de transferência.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1281">Info Field 1: Transfer request.</span></span>
- <span data-ttu-id="4e4bd-1282">Info Field 2: Código de conclusão.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1282">Info Field 2: Completion code.</span></span>
- <span data-ttu-id="4e4bd-1283">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1283">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1284">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1284">Info Field 4: Not used.</span></span>

### <a name="device-stack-transfer-all-request-abort"></a><span data-ttu-id="4e4bd-1285">Transferência de pilha de dispositivos todos os pedidos abortar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1285">Device Stack Transfer All Request Abort</span></span> 

#### <a name="ux_device_stack_transfer_all_request_abort"></a><span data-ttu-id="4e4bd-1286">ux_device_stack_transfer_all_request_abort</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1286">ux_device_stack_transfer_all_request_abort</span></span>

<span data-ttu-id="4e4bd-1287">**Ícone** ![ Transferência de pilha de dispositivo todo o ícone de abortar pedido](./media/user-guide/usbx-events/image75.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1287">**Icon** ![Device Stack Transfer All Request Abort icon](./media/user-guide/usbx-events/image75.png)</span></span>

<span data-ttu-id="4e4bd-1288">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1288">**Description**</span></span>

<span data-ttu-id="4e4bd-1289">Este evento representa uma transferência de pilha de dispositivo USBX todos os eventos de abortar pedido.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1289">This event represents a USBX Device Stack Transfer All Request Abort Event.</span></span>

<span data-ttu-id="4e4bd-1290">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1290">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1291">Info Field 1: Ponto final.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1291">Info Field 1: Endpoint.</span></span>
- <span data-ttu-id="4e4bd-1292">Info Field 2: Código de conclusão.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1292">Info Field 2: Completion code.</span></span>
- <span data-ttu-id="4e4bd-1293">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1293">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1294">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1294">Info Field 4: Not used.</span></span>

### <a name="device-stack-transfer-request"></a><span data-ttu-id="4e4bd-1295">Pedido de transferência de pilha de dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1295">Device Stack Transfer Request</span></span> 

#### <a name="ux_device_stack_transfer_request"></a><span data-ttu-id="4e4bd-1296">ux_device_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1296">ux_device_stack_transfer_request</span></span>

<span data-ttu-id="4e4bd-1297">**Ícone** ![ Ícone de pedido de transferência de pilha de dispositivo](./media/user-guide/usbx-events/image76.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1297">**Icon** ![Device Stack Transfer Request icon](./media/user-guide/usbx-events/image76.png)</span></span>

<span data-ttu-id="4e4bd-1298">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1298">**Description**</span></span>

<span data-ttu-id="4e4bd-1299">Este evento representa um Evento de Pedido de Transferência de Pilha de Dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1299">This event represents a USBX Device Stack Transfer Request Event.</span></span>

<span data-ttu-id="4e4bd-1300">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1300">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1301">Info Field 1: Pedido de transferência.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1301">Info Field 1: Transfer request.</span></span>
- <span data-ttu-id="4e4bd-1302">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1302">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1303">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1303">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1304">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1304">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-activate"></a><span data-ttu-id="4e4bd-1305">Classe de anfitrião Asix Ativar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1305">Host Class Asix Activate</span></span> 

#### <a name="ux_host_class_asix_activate"></a><span data-ttu-id="4e4bd-1306">ux_host_class_asix_activate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1306">ux_host_class_asix_activate</span></span>

<span data-ttu-id="4e4bd-1307">**Ícone** ![ Ícone de ativação classe de anfitrião Asix](./media/user-guide/usbx-events/image77.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1307">**Icon** ![Host Class Asix Activate icon](./media/user-guide/usbx-events/image77.png)</span></span>

<span data-ttu-id="4e4bd-1308">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1308">**Description**</span></span>

<span data-ttu-id="4e4bd-1309">Este evento representa uma classe de anfitrião USBX Asix Activate.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1309">This event represents a USBX Host Class Asix Activate.</span></span>

<span data-ttu-id="4e4bd-1310">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1310">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1311">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1311">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-1312">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1312">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1313">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1313">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1314">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1314">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-deactivate"></a><span data-ttu-id="4e4bd-1315">Classe hospedeira Asix Desativado</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1315">Host Class Asix Deactivate</span></span> 

#### <a name="ux_host_class_asix_deactivate"></a><span data-ttu-id="4e4bd-1316">ux_host_class_asix_deactivate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1316">ux_host_class_asix_deactivate</span></span>

<span data-ttu-id="4e4bd-1317">**Ícone** ![ Ícone de desativado classe anfitrião Asix](./media/user-guide/usbx-events/image78.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1317">**Icon** ![Host Class Asix Deactivate icon](./media/user-guide/usbx-events/image78.png)</span></span>

<span data-ttu-id="4e4bd-1318">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1318">**Description**</span></span>

<span data-ttu-id="4e4bd-1319">Este evento representa um evento de desativado da classe USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1319">This event represents a USBX Host Class Asix Deactivate Event.</span></span>

<span data-ttu-id="4e4bd-1320">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1320">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1321">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1321">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-1322">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1322">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1323">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1323">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1324">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1324">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-interrupt-notification"></a><span data-ttu-id="4e4bd-1325">Classificação de interrupção da classe anfitrião Asix</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1325">Host Class Asix Interrupt Notification</span></span> 

#### <a name="ux_host_class_asix_interrupt_notification"></a><span data-ttu-id="4e4bd-1326">ux_host_class_asix_interrupt_notification</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1326">ux_host_class_asix_interrupt_notification</span></span>

<span data-ttu-id="4e4bd-1327">**Ícone** ![ Ícone de notificação de interrupção de classe de anfitrião Asix](./media/user-guide/usbx-events/image79.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1327">**Icon** ![Host Class Asix Interrupt Notification icon](./media/user-guide/usbx-events/image79.png)</span></span>

<span data-ttu-id="4e4bd-1328">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1328">**Description**</span></span>

<span data-ttu-id="4e4bd-1329">Este evento representa um evento de notificação de interrupção da classe USBX Asix.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1329">This event represents a USBX Host Class Asix Interrupt Notification Event.</span></span>

<span data-ttu-id="4e4bd-1330">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1330">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1331">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1331">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-1332">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1332">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1333">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1333">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1334">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1334">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-read"></a><span data-ttu-id="4e4bd-1335">Classe anfitrião Asix Read</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1335">Host Class Asix Read</span></span> 

#### <a name="ux_host_class_asix_read"></a><span data-ttu-id="4e4bd-1336">ux_host_class_asix_read</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1336">ux_host_class_asix_read</span></span>

<span data-ttu-id="4e4bd-1337">**Ícone** ![ Ícone de leitura de classe de anfitrião](./media/user-guide/usbx-events/image80.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1337">**Icon** ![Host Class Asix Read icon](./media/user-guide/usbx-events/image80.png)</span></span>

<span data-ttu-id="4e4bd-1338">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1338">**Description**</span></span>

<span data-ttu-id="4e4bd-1339">Este evento representa um evento de leitura da classe anfitrião USBX Asix.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1339">This event represents a USBX Host Class Asix Read Event.</span></span>

<span data-ttu-id="4e4bd-1340">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1340">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1341">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1341">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1342">Info Field 2: Ponteiro de dados.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1342">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4e4bd-1343">Info Field 3: Comprimento solicitado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1343">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4e4bd-1344">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1344">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-write"></a><span data-ttu-id="4e4bd-1345">Classe anfitriã Asix Escrever</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1345">Host Class Asix Write</span></span> 

#### <a name="ux_host_class_asix_write"></a><span data-ttu-id="4e4bd-1346">ux_host_class_asix_write</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1346">ux_host_class_asix_write</span></span>

<span data-ttu-id="4e4bd-1347">**Ícone** ![ Ícone de escrita de classe de anfitrião Asix](./media/user-guide/usbx-events/image81.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1347">**Icon** ![Host Class Asix Write icon](./media/user-guide/usbx-events/image81.png)</span></span>

<span data-ttu-id="4e4bd-1348">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1348">**Description**</span></span>

<span data-ttu-id="4e4bd-1349">Este evento representa um evento de escrita da classe anfitrião USBX Asix.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1349">This event represents a USBX Host Class Asix Write Event.</span></span>

<span data-ttu-id="4e4bd-1350">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1350">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1351">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1351">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1352">Info Field 2: Ponteiro de dados.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1352">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4e4bd-1353">Info Field 3: Comprimento solicitado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1353">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4e4bd-1354">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1354">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-activate"></a><span data-ttu-id="4e4bd-1355">Ativação de áudio da classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1355">Host Class Audio Activate</span></span> 

#### <a name="ux_host_class_audio_activate"></a><span data-ttu-id="4e4bd-1356">ux_host_class_audio_activate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1356">ux_host_class_audio_activate</span></span>

<span data-ttu-id="4e4bd-1357">**Ícone** ![ Ícone ativar áudio classe anfitrião](./media/user-guide/usbx-events/image82.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1357">**Icon** ![Host Class Audio Activate icon](./media/user-guide/usbx-events/image82.png)</span></span>

<span data-ttu-id="4e4bd-1358">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1358">**Description**</span></span>

<span data-ttu-id="4e4bd-1359">Este evento representa um evento USBX Host Class Audio Activate.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1359">This event represents a USBX Host Class Audio Activate Event.</span></span>

<span data-ttu-id="4e4bd-1360">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1360">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1361">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1361">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1362">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1362">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1363">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1363">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1364">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1364">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-control-value-get"></a><span data-ttu-id="4e4bd-1365">Valor de controlo de áudio da classe do anfitrião obter</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1365">Host Class Audio Control Value Get</span></span> 

#### <a name="ux_host_class_audio_control_value_get"></a><span data-ttu-id="4e4bd-1366">ux_host_class_audio_control_value_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1366">ux_host_class_audio_control_value_get</span></span>

<span data-ttu-id="4e4bd-1367">**Ícone** ![ Valor de controlo de áudio da classe do anfitrião Obter ícone](./media/user-guide/usbx-events/image83.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1367">**Icon** ![Host Class Audio Control Value Get icon](./media/user-guide/usbx-events/image83.png)</span></span>

<span data-ttu-id="4e4bd-1368">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1368">**Description**</span></span>

<span data-ttu-id="4e4bd-1369">Este evento representa um evento USBX Host Class Audio Control Value Get.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1369">This event represents a USBX Host Class Audio Control Value Get Event.</span></span>

<span data-ttu-id="4e4bd-1370">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1370">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1371">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1371">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1372">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1372">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1373">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1373">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1374">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1374">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-control-value-set"></a><span data-ttu-id="4e4bd-1375">Conjunto de valor de controlo de áudio da classe do anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1375">Host Class Audio Control Value Set</span></span> 

#### <a name="ux_host_class_audio_control_value_set"></a><span data-ttu-id="4e4bd-1376">ux_host_class_audio_control_value_set</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1376">ux_host_class_audio_control_value_set</span></span>

<span data-ttu-id="4e4bd-1377">**Ícone** ![ Ícone do conjunto de conjunto de valor de controlo de áudio da classe do anfitrião](./media/user-guide/usbx-events/image84.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1377">**Icon** ![Host Class Audio Control Value Set icon](./media/user-guide/usbx-events/image84.png)</span></span>

<span data-ttu-id="4e4bd-1378">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1378">**Description**</span></span>

<span data-ttu-id="4e4bd-1379">Este evento representa um evento interno de processamento diferido do piloto NetX I/O.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1379">This event represents an internal NetX I/O driver deferred processing event.</span></span>

<span data-ttu-id="4e4bd-1380">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1380">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1381">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1381">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1382">Info Field 2: Controlo de áudio.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1382">Info Field 2: Audio control.</span></span>
- <span data-ttu-id="4e4bd-1383">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1383">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1384">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1384">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-deactivate"></a><span data-ttu-id="4e4bd-1385">Desativar áudio da classe hospedeira</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1385">Host Class Audio Deactivate</span></span> 

#### <a name="ux_host_class_audio_deactivate"></a><span data-ttu-id="4e4bd-1386">ux_host_class_audio_deactivate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1386">ux_host_class_audio_deactivate</span></span>

<span data-ttu-id="4e4bd-1387">**Ícone** ![ Ícone de desativado de áudio classe anfitrião](./media/user-guide/usbx-events/image85.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1387">**Icon** ![Host Class Audio Deactivate icon](./media/user-guide/usbx-events/image85.png)</span></span>

<span data-ttu-id="4e4bd-1388">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1388">**Description**</span></span>

<span data-ttu-id="4e4bd-1389">Este evento representa um evento de desativado áudio da classe USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1389">This event represents a USBX Host Class Audio Deactivate Event.</span></span>

<span data-ttu-id="4e4bd-1390">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1390">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1391">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1391">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1392">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1392">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1393">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1393">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1394">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1394">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-read"></a><span data-ttu-id="4e4bd-1395">Leitura áudio da classe anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1395">Host Class Audio Read</span></span> 

#### <a name="ux_host_class_audio_read"></a><span data-ttu-id="4e4bd-1396">ux_host_class_audio_read</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1396">ux_host_class_audio_read</span></span>

<span data-ttu-id="4e4bd-1397">**Ícone** ![ Ícone de leitura de áudio de classe de anfitrião](./media/user-guide/usbx-events/image86.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1397">**Icon** ![Host Class Audio Read icon](./media/user-guide/usbx-events/image86.png)</span></span>

<span data-ttu-id="4e4bd-1398">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1398">**Description**</span></span>

<span data-ttu-id="4e4bd-1399">Este evento representa um evento de leitura áudio da classe usbx.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1399">This event represents a USBX Host Class Audio Read Event.</span></span>

- <span data-ttu-id="4e4bd-1400">Campos de Informação</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1400">Information Fields</span></span> 
- <span data-ttu-id="4e4bd-1401">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1401">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1402">Info Field 2: Ponteiro de dados.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1402">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4e4bd-1403">Info Field 3: Comprimento solicitado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1403">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4e4bd-1404">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1404">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-streaming-sampling-get"></a><span data-ttu-id="4e4bd-1405">Amostragem de streaming de áudio de classe de anfitrião obter</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1405">Host Class Audio Streaming Sampling Get</span></span> 

#### <a name="ux_host_class_audio_streaming_sampling_get"></a><span data-ttu-id="4e4bd-1406">ux_host_class_audio_streaming_sampling_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1406">ux_host_class_audio_streaming_sampling_get</span></span>

<span data-ttu-id="4e4bd-1407">**Ícone** ![ Amostragem de streaming de áudio de classe de anfitrião Obter ícone](./media/user-guide/usbx-events/image87.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1407">**Icon** ![Host Class Audio Streaming Sampling Get icon](./media/user-guide/usbx-events/image87.png)</span></span>

<span data-ttu-id="4e4bd-1408">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1408">**Description**</span></span>

<span data-ttu-id="4e4bd-1409">Este evento representa um evento de streaming de áudio da classe USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1409">This event represents a USBX Host Class Audio Streaming Sampling Get Event.</span></span>

<span data-ttu-id="4e4bd-1410">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1410">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1411">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1411">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1412">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1412">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1413">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1413">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1414">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1414">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-streaming-sampling-set"></a><span data-ttu-id="4e4bd-1415">Conjunto de amostragem de streaming de áudio de classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1415">Host Class Audio Streaming Sampling Set</span></span> 

#### <a name="ux_host_class_audio_streaming_sampling_set"></a><span data-ttu-id="4e4bd-1416">ux_host_class_audio_streaming_sampling_set</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1416">ux_host_class_audio_streaming_sampling_set</span></span>

<span data-ttu-id="4e4bd-1417">**Ícone** ![ Ícone do conjunto de amostragem de streaming de áudio da classe do anfitrião](./media/user-guide/usbx-events/image88.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1417">**Icon** ![Host Class Audio Streaming Sampling Set icon](./media/user-guide/usbx-events/image88.png)</span></span>

<span data-ttu-id="4e4bd-1418">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1418">**Description**</span></span>

<span data-ttu-id="4e4bd-1419">Este evento representa um evento USBX Host Class Audio Streaming Sampling set.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1419">This event represents a USBX Host Class Audio Streaming Sampling Set Event.</span></span>

<span data-ttu-id="4e4bd-1420">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1420">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1421">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1421">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1422">Info Field 2: Amostragem de áudio.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1422">Info Field 2: Audio Sampling.</span></span>
- <span data-ttu-id="4e4bd-1423">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1423">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1424">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1424">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-write"></a><span data-ttu-id="4e4bd-1425">Escrita áudio da classe hospedeira</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1425">Host Class Audio Write</span></span> 

#### <a name="ux_host_class_audio_write"></a><span data-ttu-id="4e4bd-1426">ux_host_class_audio_write</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1426">ux_host_class_audio_write</span></span>

<span data-ttu-id="4e4bd-1427">**Ícone** ![ Ícone de escrita de áudio de classe de anfitrião](./media/user-guide/usbx-events/image89.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1427">**Icon** ![Host Class Audio Write icon](./media/user-guide/usbx-events/image89.png)</span></span>

<span data-ttu-id="4e4bd-1428">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1428">**Description**</span></span>

<span data-ttu-id="4e4bd-1429">Este evento representa um evento de escrita áudio da classe usbx.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1429">This event represents a USBX Host Class Audio Write Event.</span></span>

<span data-ttu-id="4e4bd-1430">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1430">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1431">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1431">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1432">Info Field 2: Ponteiro de dados.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1432">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4e4bd-1433">Info Field 3: Comprimento solicitado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1433">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4e4bd-1434">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1434">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-activate"></a><span data-ttu-id="4e4bd-1435">Classe de anfitrião CDC Acm Ativar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1435">Host Class Cdc Acm Activate</span></span> 

#### <a name="ux_host_class_cdc_acm_activate"></a><span data-ttu-id="4e4bd-1436">ux_host_class_cdc_acm_activate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1436">ux_host_class_cdc_acm_activate</span></span>

<span data-ttu-id="4e4bd-1437">**Ícone** ![ Classe anfitrião C D C A C M Ícone ativado](./media/user-guide/usbx-events/image90.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1437">**Icon** ![Host Class C D C A C M Activate icon](./media/user-guide/usbx-events/image90.png)</span></span>

<span data-ttu-id="4e4bd-1438">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1438">**Description**</span></span>

<span data-ttu-id="4e4bd-1439">Este evento representa um evento USBX Host Class Cdc Acm Activate Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1439">This event represents a USBX Host Class Cdc Acm Activate Event.</span></span>

<span data-ttu-id="4e4bd-1440">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1440">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1441">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1441">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1442">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1442">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1443">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1443">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1444">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1444">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-deactivate"></a><span data-ttu-id="4e4bd-1445">Classe de anfitrião CDC Acm Desativar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1445">Host Class Cdc Acm Deactivate</span></span> 

#### <a name="ux_host_class_cdc_acm_deactivate"></a><span data-ttu-id="4e4bd-1446">ux_host_class_cdc_acm_deactivate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1446">ux_host_class_cdc_acm_deactivate</span></span>

<span data-ttu-id="4e4bd-1447">**Ícone** ![ Ícone desativado classe C D C A C M](./media/user-guide/usbx-events/image91.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1447">**Icon** ![Host Class C D C A C M Deactivate icon](./media/user-guide/usbx-events/image91.png)</span></span>

<span data-ttu-id="4e4bd-1448">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1448">**Description**</span></span>

<span data-ttu-id="4e4bd-1449">Este evento representa um evento de desativado da classe USBX Cdc Acm.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1449">This event represents a USBX Host Class Cdc Acm Deactivate Event.</span></span>

<span data-ttu-id="4e4bd-1450">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1450">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1451">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1451">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1452">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1452">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1453">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1453">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1454">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1454">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-abort-in-pipe"></a><span data-ttu-id="4e4bd-1455">Classe anfitriã Cdc Acm Ioctl Abortar em tubo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1455">Host Class Cdc Acm Ioctl Abort In Pipe</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_abort_in_pipe"></a><span data-ttu-id="4e4bd-1456">ux_host_class_cdc_acm_ioctl_abort_in_pipe</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1456">ux_host_class_cdc_acm_ioctl_abort_in_pipe</span></span>

<span data-ttu-id="4e4bd-1457">**Ícone** ![ Classe hospedeira C D C A C M I O C T T Abort no ícone do tubo](./media/user-guide/usbx-events/image92.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1457">**Icon** ![Host Class C D C A C M I O C T L Abort In Pipe icon](./media/user-guide/usbx-events/image92.png)</span></span>

<span data-ttu-id="4e4bd-1458">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1458">**Description**</span></span>

<span data-ttu-id="4e4bd-1459">Este evento representa um CDC Acm Ioctl Abort in Pipe Event da classe USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1459">This event represents a USBX Host Class Cdc Acm Ioctl Abort In Pipe Event.</span></span>

<span data-ttu-id="4e4bd-1460">Campos de Informação</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1460">Information Fields</span></span> 

- <span data-ttu-id="4e4bd-1461">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1461">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1462">Info Field 2: Ponto final.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1462">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4e4bd-1463">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1463">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1464">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1464">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-abort-out-pipe"></a><span data-ttu-id="4e4bd-1465">Classe anfitriã Cdc Acm Ioctl AbortAr Tubo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1465">Host Class Cdc Acm Ioctl Abort Out Pipe</span></span> 

#### <a name="ux_host_class_cdc_acm_ioct_abort_out_pipe"></a><span data-ttu-id="4e4bd-1466">ux_host_class_cdc_acm_ioct_abort_out_pipe</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1466">ux_host_class_cdc_acm_ioct_abort_out_pipe</span></span>

<span data-ttu-id="4e4bd-1467">**Ícone!** [[Classe anfitriã C D C A C A C M I O C T L AbortAr Ícone de Tubo](./media/user-guide/usbx-events/image93.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1467">**Icon** ![[Host Class C D C A C M I O C T L Abort Out Pipe icon](./media/user-guide/usbx-events/image93.png)</span></span>

<span data-ttu-id="4e4bd-1468">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1468">**Description**</span></span>

<span data-ttu-id="4e4bd-1469">Este evento representa um evento usbx host Class Cdc Acm Ioctl Abort out Pipe Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1469">This event represents a USBX Host Class Cdc Acm Ioctl Abort Out Pipe Event.</span></span>

<span data-ttu-id="4e4bd-1470">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1470">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1471">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1471">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1472">Info Field 2: Ponto final.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1472">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4e4bd-1473">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1473">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1474">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1474">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-get-device-status"></a><span data-ttu-id="4e4bd-1475">Classe anfitrião Cdc Acm Ioctl Obter Estado do Dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1475">Host Class Cdc Acm Ioctl Get Device Status</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_get_device_status"></a><span data-ttu-id="4e4bd-1476">ux_host_class_cdc_acm_ioctl_get_device_status</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1476">ux_host_class_cdc_acm_ioctl_get_device_status</span></span>

<span data-ttu-id="4e4bd-1477">**Ícone** ![ Classe hospedeira C D C A C M I O C T L Obter Ícone de Estado do Dispositivo](./media/user-guide/usbx-events/image94.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1477">**Icon** ![Host Class C D C A C M I O C T L Get Device Status icon](./media/user-guide/usbx-events/image94.png)</span></span>

<span data-ttu-id="4e4bd-1478">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1478">**Description**</span></span>

<span data-ttu-id="4e4bd-1479">Este evento representa um evento de estado do dispositivo da classe USBX Host Cdc Acm Ioctl Get Device.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1479">This event represents a USBX Host Class Cdc Acm Ioctl Get Device Status Event.</span></span>

<span data-ttu-id="4e4bd-1480">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1480">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1481">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1481">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1482">Info Field 2: Estado do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1482">Info Field 2: Device status.</span></span>
- <span data-ttu-id="4e4bd-1483">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1483">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1484">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1484">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-get-line-coding"></a><span data-ttu-id="4e4bd-1485">Classe anfitriã CDC Acm Ioctl Obter Codificação de Linha</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1485">Host Class Cdc Acm Ioctl Get Line Coding</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_get_line_coding"></a><span data-ttu-id="4e4bd-1486">ux_host_class_cdc_acm_ioctl_get_line_coding</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1486">ux_host_class_cdc_acm_ioctl_get_line_coding</span></span>

<span data-ttu-id="4e4bd-1487">**Ícone** ![ Classe anfitriã C D C A C M I O C T L Get Line Codificação](./media/user-guide/usbx-events/image95.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1487">**Icon** ![Host Class C D C A C M I O C T L Get Line Coding icon](./media/user-guide/usbx-events/image95.png)</span></span>

<span data-ttu-id="4e4bd-1488">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1488">**Description**</span></span>

<span data-ttu-id="4e4bd-1489">Este evento representa um evento de codificação usbx host Class CDC Acm Ioctl Get Line Coding.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1489">This event represents a USBX Host Class Cdc Acm Ioctl Get Line Coding Event.</span></span>

<span data-ttu-id="4e4bd-1490">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1490">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1491">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1491">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1492">Info Field 2: Parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1492">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4e4bd-1493">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1493">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1494">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1494">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-notification-callback"></a><span data-ttu-id="4e4bd-1495">Chamada de notificação do cdc Acm ioctl da classe anfitriã</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1495">Host Class Cdc Acm Ioctl Notification Callback</span></span>

#### <a name="ux_host_class_cdc_acm_ioctl_notification_callback"></a><span data-ttu-id="4e4bd-1496">ux_host_class_cdc_acm_ioctl_notification_callback</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1496">ux_host_class_cdc_acm_ioctl_notification_callback</span></span>

<span data-ttu-id="4e4bd-1497">**Ícone** ![ Classe anfitriã C D C A C M I O C T L Notification Callback](./media/user-guide/usbx-events/image96.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1497">**Icon** ![Host Class C D C A C M I O C T L Notification Callback icon](./media/user-guide/usbx-events/image96.png)</span></span>

<span data-ttu-id="4e4bd-1498">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1498">**Description**</span></span>

<span data-ttu-id="4e4bd-1499">Este evento representa um evento de chamada de chamada de notificação DA Classe USBX CDC Acm Ioctl.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1499">This event represents a USBX Host Class Cdc Acm Ioctl Notification Callback Event.</span></span>

<span data-ttu-id="4e4bd-1500">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1500">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1501">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1501">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1502">Info Field 2: Parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1502">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4e4bd-1503">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1503">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1504">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1504">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-send-break"></a><span data-ttu-id="4e4bd-1505">Classe anfitriã Cdc Acm Ioctl Enviar Pausa</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1505">Host Class Cdc Acm Ioctl Send Break</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_send_break"></a><span data-ttu-id="4e4bd-1506">ux_host_class_cdc_acm_ioctl_send_break</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1506">ux_host_class_cdc_acm_ioctl_send_break</span></span>

<span data-ttu-id="4e4bd-1507">**Ícone** ![ Classe anfitriã C D C A C M I O C T L Enviar Ícone de rutura](./media/user-guide/usbx-events/image97.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1507">**Icon** ![Host Class C D C A C M I O C T L Send Break icon](./media/user-guide/usbx-events/image97.png)</span></span>

<span data-ttu-id="4e4bd-1508">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1508">**Description**</span></span>

<span data-ttu-id="4e4bd-1509">Este evento representa um evento de intervalo de envio da classe USBX Cdc Acm Ioctl.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1509">This event represents a USBX Host Class Cdc Acm Ioctl Send Break Event.</span></span>

<span data-ttu-id="4e4bd-1510">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1510">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1511">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1511">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1512">Info Field 2: Parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1512">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4e4bd-1513">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1513">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1514">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1514">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-set-line-coding"></a><span data-ttu-id="4e4bd-1515">Classe anfitrião CDC Acm Ioctl set Line Codificação</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1515">Host Class Cdc Acm Ioctl Set Line Coding</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_coding"></a><span data-ttu-id="4e4bd-1516">ux_host_class_cdc_acm_ioctl_set_line_coding</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1516">ux_host_class_cdc_acm_ioctl_set_line_coding</span></span>

<span data-ttu-id="4e4bd-1517">**Ícone** ![ Ícone de codificação da linha de codificação da classe anfitriã C D C C A C M I O C T L Line ](./media/user-guide/usbx-events/image97.png) Codeing](./media/user-guide/usbx-events/image98.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1517">**Icon** ![The Host Class C D C A C M I O C T L Set Line Coding icon](./media/user-guide/usbx-events/image97.png) icon](./media/user-guide/usbx-events/image98.png)</span></span>

<span data-ttu-id="4e4bd-1518">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1518">**Description**</span></span>

<span data-ttu-id="4e4bd-1519">Este evento representa um evento de codificação de linha set set da classe USBX CDC Acm Ioctl.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1519">This event represents a USBX Host Class Cdc Acm Ioctl Set Line Coding Event.</span></span>

<span data-ttu-id="4e4bd-1520">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1520">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1521">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1521">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1522">Info Field 2: Parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1522">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4e4bd-1523">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1523">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1524">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1524">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-set-line-state"></a><span data-ttu-id="4e4bd-1525">Classe anfitrião Cdc Acm Ioctl set Line State</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1525">Host Class Cdc Acm Ioctl Set Line State</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_state"></a><span data-ttu-id="4e4bd-1526">ux_host_class_cdc_acm_ioctl_set_line_state</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1526">ux_host_class_cdc_acm_ioctl_set_line_state</span></span>

<span data-ttu-id="4e4bd-1527">**Ícone** ![ Classe anfitriã C D C A C A C M I O C T L set Line State ícone](./media/user-guide/usbx-events/image99.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1527">**Icon** ![Host Class C D C A C M I O C T L Set Line State icon](./media/user-guide/usbx-events/image99.png)</span></span>

<span data-ttu-id="4e4bd-1528">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1528">**Description**</span></span>

<span data-ttu-id="4e4bd-1529">Este evento representa um evento de estado de set line set da classe USBX CDC Acm Ioctl.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1529">This event represents a USBX Host Class Cdc Acm Ioctl Set Line State Event.</span></span>

<span data-ttu-id="4e4bd-1530">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1530">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1531">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1531">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1532">Info Field 2: Parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1532">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4e4bd-1533">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1533">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1534">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1534">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-read"></a><span data-ttu-id="4e4bd-1535">Classe anfitrião CDC Acm Read</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1535">Host Class Cdc Acm Read</span></span> 

#### <a name="ux_host_class_cdc_acm_read"></a><span data-ttu-id="4e4bd-1536">ux_host_class_cdc_acm_read</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1536">ux_host_class_cdc_acm_read</span></span>

<span data-ttu-id="4e4bd-1537">**Ícone** ![ Ícone de leitura classe C D C A C M](./media/user-guide/usbx-events/image100.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1537">**Icon** ![Host Class C D C A C M Read icon](./media/user-guide/usbx-events/image100.png)</span></span>

<span data-ttu-id="4e4bd-1538">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1538">**Description**</span></span>

<span data-ttu-id="4e4bd-1539">Este evento representa um evento de leitura da classe de anfitrião USBX CDC Acm.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1539">This event represents a USBX Host Class Cdc Acm Read Event.</span></span>

<span data-ttu-id="4e4bd-1540">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1540">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1541">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1541">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1542">Info Field 2: Ponteiro de dados.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1542">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4e4bd-1543">Info Field 3: Comprimento Solicitado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1543">Info Field 3: Requested Length.</span></span>
- <span data-ttu-id="4e4bd-1544">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1544">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-reception-start"></a><span data-ttu-id="4e4bd-1545">Início da receção da classe anfitriã CDC Acm</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1545">Host Class Cdc Acm Reception Start</span></span> 

#### <a name="ux_host_class_cdc_acm_reception_start"></a><span data-ttu-id="4e4bd-1546">ux_host_class_cdc_acm_reception_start</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1546">ux_host_class_cdc_acm_reception_start</span></span>

<span data-ttu-id="4e4bd-1547">**Ícone** ![ Classe anfitrião C D C A C M Receção Ícone de início](./media/user-guide/usbx-events/image101.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1547">**Icon** ![Host Class C D C A C M Reception Start icon](./media/user-guide/usbx-events/image101.png)</span></span>

<span data-ttu-id="4e4bd-1548">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1548">**Description**</span></span>

<span data-ttu-id="4e4bd-1549">Este evento representa um evento de receção USBX Host Class Cdc Acm Reception Start.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1549">This event represents a USBX Host Class Cdc Acm Reception Start Event.</span></span>

<span data-ttu-id="4e4bd-1550">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1550">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1551">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1551">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1552">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1552">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1553">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1553">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1554">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1554">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-reception-stop"></a><span data-ttu-id="4e4bd-1555">Paragem de receção cdc Acm classe anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1555">Host Class Cdc Acm Reception Stop</span></span> 

#### <a name="ux_host_class_cdc_acm_reception_stop"></a><span data-ttu-id="4e4bd-1556">ux_host_class_cdc_acm_reception_stop</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1556">ux_host_class_cdc_acm_reception_stop</span></span>

<span data-ttu-id="4e4bd-1557">**Ícone** ![ Classe anfitrião C D C A C C M Ícone de paragem de receção](./media/user-guide/usbx-events/image102.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1557">**Icon** ![Host Class C D C A C M Reception Stop icon](./media/user-guide/usbx-events/image102.png)</span></span>

<span data-ttu-id="4e4bd-1558">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1558">**Description**</span></span>

<span data-ttu-id="4e4bd-1559">Este evento representa um evento de paragem de receção USBX Host Class CDC Acm.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1559">This event represents a USBX Host Class Cdc Acm Reception Stop Event.</span></span>

<span data-ttu-id="4e4bd-1560">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1560">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1561">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1561">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1562">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1562">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1563">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1563">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-write"></a><span data-ttu-id="4e4bd-1564">Classe anfitriã CDC Acm Write</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1564">Host Class Cdc Acm Write</span></span> 

#### <a name="ux_host_class_acm_write"></a><span data-ttu-id="4e4bd-1565">ux_host_class_acm_write</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1565">ux_host_class_acm_write</span></span>

<span data-ttu-id="4e4bd-1566">**Ícone** ![ Ícone de escrita classe de anfitrião C D C A C M](./media/user-guide/usbx-events/image103.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1566">**Icon** ![Host Class C D C A C M Write icon](./media/user-guide/usbx-events/image103.png)</span></span>

<span data-ttu-id="4e4bd-1567">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1567">**Description**</span></span>

<span data-ttu-id="4e4bd-1568">Este evento representa um evento de escrita DA Classe Anfitrião USBX CDC Acm.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1568">This event represents a USBX Host Class Cdc Acm Write Event.</span></span>

<span data-ttu-id="4e4bd-1569">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1569">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1570">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1570">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1571">Info Field 2: Ponteiro de dados.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1571">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4e4bd-1572">Info Field 3: Comprimento Solicitado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1572">Info Field 3: Requested Length.</span></span>
- <span data-ttu-id="4e4bd-1573">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1573">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-activate"></a><span data-ttu-id="4e4bd-1574">Ativar classe de anfitrião Dpump</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1574">Host Class Dpump Activate</span></span> 

#### <a name="ux_host_class_dpump_activate"></a><span data-ttu-id="4e4bd-1575">ux_host_class_dpump_activate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1575">ux_host_class_dpump_activate</span></span>

<span data-ttu-id="4e4bd-1576">**Ícone** ![ Ícone ativar classe de anfitrião](./media/user-guide/usbx-events/image104.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1576">**Icon** ![Host Class Dpump Activate icon](./media/user-guide/usbx-events/image104.png)</span></span>

<span data-ttu-id="4e4bd-1577">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1577">**Description**</span></span>

<span data-ttu-id="4e4bd-1578">Este evento representa um Evento Ativado da Classe USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1578">This event represents a USBX Host Class Dpump Activate Event.</span></span>

<span data-ttu-id="4e4bd-1579">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1579">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1580">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1580">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1581">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1581">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1582">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1582">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1583">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1583">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-deactivate"></a><span data-ttu-id="4e4bd-1584">Classe anfitriã Dpump Desativar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1584">Host Class Dpump Deactivate</span></span> 

#### <a name="ux_host_class_dpump_deactivate"></a><span data-ttu-id="4e4bd-1585">ux_host_class_dpump_deactivate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1585">ux_host_class_dpump_deactivate</span></span>

<span data-ttu-id="4e4bd-1586">**Ícone** ![ Ícone de desativado classe de anfitrião Dpump](./media/user-guide/usbx-events/image105.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1586">**Icon** ![Host Class Dpump Deactivate icon](./media/user-guide/usbx-events/image105.png)</span></span>

<span data-ttu-id="4e4bd-1587">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1587">**Description**</span></span>

<span data-ttu-id="4e4bd-1588">Este evento representa um evento de desativado da classe USBX Dpump.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1588">This event represents a USBX Host Class Dpump Deactivate Event.</span></span>

<span data-ttu-id="4e4bd-1589">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1589">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1590">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1590">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1591">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1591">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1592">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1592">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1593">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1593">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-read"></a><span data-ttu-id="4e4bd-1594">Leitura de Dpump de Classe Anfitriã</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1594">Host Class Dpump Read</span></span> 

#### <a name="ux_host_class_dpump_read"></a><span data-ttu-id="4e4bd-1595">ux_host_class_dpump_read</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1595">ux_host_class_dpump_read</span></span>

<span data-ttu-id="4e4bd-1596">**Ícone** ![ Ícone de leitura de classe de anfitrião](./media/user-guide/usbx-events/image106.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1596">**Icon** ![Host Class Dpump Read icon](./media/user-guide/usbx-events/image106.png)</span></span>

<span data-ttu-id="4e4bd-1597">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1597">**Description**</span></span>

<span data-ttu-id="4e4bd-1598">Este evento representa um Evento de Leitura de Dpump da Classe Anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1598">This event represents a USBX Host Class Dpump Read Event.</span></span>

<span data-ttu-id="4e4bd-1599">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1599">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1600">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1600">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1601">Info Field 2: Ponteiro de dados.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1601">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4e4bd-1602">Info Field 3: Comprimento solicitado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1602">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4e4bd-1603">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1603">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-write"></a><span data-ttu-id="4e4bd-1604">Escrita de Classe Anfitriã Dpump</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1604">Host Class Dpump Write</span></span> 

#### <a name="ux_host_class_dpump_write"></a><span data-ttu-id="4e4bd-1605">ux_host_class_dpump_write</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1605">ux_host_class_dpump_write</span></span>

<span data-ttu-id="4e4bd-1606">**Ícone** ![ Ícone de escrita de classe de anfitrião](./media/user-guide/usbx-events/image107.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1606">**Icon** ![Host Class Dpump Write icon](./media/user-guide/usbx-events/image107.png)</span></span>

<span data-ttu-id="4e4bd-1607">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1607">**Description**</span></span>

<span data-ttu-id="4e4bd-1608">Este evento representa um evento de escrita de classe de anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1608">This event represents a USBX Host Class Dpump Write Event.</span></span>

<span data-ttu-id="4e4bd-1609">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1609">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1610">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1610">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1611">Info Field 2: Ponteiro de dados.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1611">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4e4bd-1612">Info Field 3: Comprimento solicitado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1612">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4e4bd-1613">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1613">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-activate"></a><span data-ttu-id="4e4bd-1614">Classe de anfitrião Hid Ativado</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1614">Host Class Hid Activate</span></span> 

#### <a name="ux_host_class_hid_activate"></a><span data-ttu-id="4e4bd-1615">ux_host_class_hid_activate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1615">ux_host_class_hid_activate</span></span>

<span data-ttu-id="4e4bd-1616">**Ícone** ![ Ícone ativar classe de anfitrião Hid](./media/user-guide/usbx-events/image108.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1616">**Icon** ![Host Class Hid Activate icon](./media/user-guide/usbx-events/image108.png)</span></span>

<span data-ttu-id="4e4bd-1617">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1617">**Description**</span></span>

<span data-ttu-id="4e4bd-1618">Este evento representa um evento USBX Host Class Hid Activate Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1618">This event represents a USBX Host Class Hid Activate Event.</span></span>

<span data-ttu-id="4e4bd-1619">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1619">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1620">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1620">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1621">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1621">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1622">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1622">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1623">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1623">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-client-register"></a><span data-ttu-id="4e4bd-1624">Registo de clientes hid de classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1624">Host Class Hid Client Register</span></span> 

#### <a name="ux_host_class_hid_client_register"></a><span data-ttu-id="4e4bd-1625">ux_host_class_hid_client_register</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1625">ux_host_class_hid_client_register</span></span>

<span data-ttu-id="4e4bd-1626">**Ícone** ![ Ícone de registo de clientes de classe de anfitrião](./media/user-guide/usbx-events/image109.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1626">**Icon** ![Host Class Hid Client Register icon](./media/user-guide/usbx-events/image109.png)</span></span>

<span data-ttu-id="4e4bd-1627">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1627">**Description**</span></span>

<span data-ttu-id="4e4bd-1628">Este evento representa um evento USBX Host Class Hid Client Register.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1628">This event represents a USBX Host Class Hid Client Register Event.</span></span>

<span data-ttu-id="4e4bd-1629">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1629">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1630">Info Field 1: Nome do cliente escondido.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1630">Info Field 1: Hid client name.</span></span>
- <span data-ttu-id="4e4bd-1631">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1631">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1632">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1632">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1633">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1633">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-deactivate"></a><span data-ttu-id="4e4bd-1634">Classe de anfitrião Hid Desativado</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1634">Host Class Hid Deactivate</span></span> 

#### <a name="ux_host_class_hid_deactivate"></a><span data-ttu-id="4e4bd-1635">ux_host_class_hid_deactivate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1635">ux_host_class_hid_deactivate</span></span>

<span data-ttu-id="4e4bd-1636">**Ícone** ![ Ícone de desativado classe de anfitrião Hid](./media/user-guide/usbx-events/image110.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1636">**Icon** ![Host Class Hid Deactivate icon](./media/user-guide/usbx-events/image110.png)</span></span>

<span data-ttu-id="4e4bd-1637">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1637">**Description**</span></span>

<span data-ttu-id="4e4bd-1638">Este evento representa um evento de desativado da classe usbx.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1638">This event represents a USBX Host Class Hid Deactivate Event.</span></span>

<span data-ttu-id="4e4bd-1639">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1639">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1640">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1640">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1641">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1641">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1642">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1642">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1643">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1643">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-idle-get"></a><span data-ttu-id="4e4bd-1644">Classe anfitriã Hid Idle Get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1644">Host Class Hid Idle Get</span></span> 

#### <a name="ux_host_class_hid_idle_get"></a><span data-ttu-id="4e4bd-1645">ux_host_class_hid_idle_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1645">ux_host_class_hid_idle_get</span></span>

<span data-ttu-id="4e4bd-1646">**Ícone** ![ Classe de anfitrião Hid Idle Obter ícone](./media/user-guide/usbx-events/image111.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1646">**Icon** ![Host Class Hid Idle Get icon](./media/user-guide/usbx-events/image111.png)</span></span>

<span data-ttu-id="4e4bd-1647">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1647">**Description**</span></span>

<span data-ttu-id="4e4bd-1648">Este evento representa um evento USBX Host Class Hid Idle Get.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1648">This event represents a USBX Host Class Hid Idle Get Event.</span></span>

<span data-ttu-id="4e4bd-1649">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1649">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1650">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1650">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1651">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1651">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1652">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1652">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1653">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1653">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-idle-set"></a><span data-ttu-id="4e4bd-1654">Conjunto de idle de classe de anfitrião hid</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1654">Host Class Hid Idle Set</span></span> 

#### <a name="ux_host_class_hid_idle_set"></a><span data-ttu-id="4e4bd-1655">ux_host_class_hid_idle_set</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1655">ux_host_class_hid_idle_set</span></span>

<span data-ttu-id="4e4bd-1656">**Ícone** ![ Ícone de conjunto de conjunto de classe de anfitrião hid ocioso](./media/user-guide/usbx-events/image112.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1656">**Icon** ![Host Class Hid Idle Set icon](./media/user-guide/usbx-events/image112.png)</span></span>

<span data-ttu-id="4e4bd-1657">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1657">**Description**</span></span>

<span data-ttu-id="4e4bd-1658">Este evento representa um evento USBX Host Class Hid Idle set Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1658">This event represents a USBX Host Class Hid Idle Set Event.</span></span>

<span data-ttu-id="4e4bd-1659">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1659">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1660">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1660">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1661">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1661">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1662">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1662">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1663">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1663">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-keyboard-activate"></a><span data-ttu-id="4e4bd-1664">Classe de anfitrião Hid Teclado Ativado</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1664">Host Class Hid Keyboard Activate</span></span> 

#### <a name="ux_host_class_hid_keyboard_activate"></a><span data-ttu-id="4e4bd-1665">ux_host_class_hid_keyboard_activate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1665">ux_host_class_hid_keyboard_activate</span></span>

<span data-ttu-id="4e4bd-1666">**Ícone** ![ Ícone ativar teclado de classe de anfitrião](./media/user-guide/usbx-events/image113.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1666">**Icon** ![Host Class Hid Keyboard Activate icon](./media/user-guide/usbx-events/image113.png)</span></span>

<span data-ttu-id="4e4bd-1667">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1667">**Description**</span></span>

<span data-ttu-id="4e4bd-1668">Este evento representa um evento usbx host class Hid Keyboard Activate Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1668">This event represents a USBX Host Class Hid Keyboard Activate Event.</span></span>

<span data-ttu-id="4e4bd-1669">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1669">**Information Fields**</span></span>
<p><span data-ttu-id="4e4bd-1670">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1670">Info Field 1: Class instance.</span></span>
<p><span data-ttu-id="4e4bd-1671">Info Field 2: Identificação do cliente escondida.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1671">Info Field 2: Hid client instance.</span></span>
<p><span data-ttu-id="4e4bd-1672">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1672">Info Field 3: Not used.</span></span>
<p><span data-ttu-id="4e4bd-1673">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1673">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-keyboard-deactivate"></a><span data-ttu-id="4e4bd-1674">Classe de anfitrião Hid Keyboard Desativado</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1674">Host Class Hid Keyboard Deactivate</span></span> 

#### <a name="ux_host_class_hid_keyboard_deactivate"></a><span data-ttu-id="4e4bd-1675">ux_host_class_hid_keyboard_deactivate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1675">ux_host_class_hid_keyboard_deactivate</span></span>

<span data-ttu-id="4e4bd-1676">**Ícone** ![ Ícone de desativado do teclado da classe anfitrião Hid](./media/user-guide/usbx-events/image114.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1676">**Icon** ![Host Class Hid Keyboard Deactivate icon](./media/user-guide/usbx-events/image114.png)</span></span>

<span data-ttu-id="4e4bd-1677">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1677">**Description**</span></span>

<span data-ttu-id="4e4bd-1678">Este evento representa um evento de desativado do teclado USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1678">This event represents a USBX Host Class Hid Keyboard Deactivate Event.</span></span>

<span data-ttu-id="4e4bd-1679">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1679">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1680">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1680">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1681">Info Field 2: Identificação do cliente escondida.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1681">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="4e4bd-1682">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1682">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1683">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1683">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-mouse-activate"></a><span data-ttu-id="4e4bd-1684">Classe de anfitrião Hid Rato Ativado</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1684">Host Class Hid Mouse Activate</span></span> 

#### <a name="ux_host_class_hid_mouse_activate"></a><span data-ttu-id="4e4bd-1685">ux_host_class_hid_mouse_activate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1685">ux_host_class_hid_mouse_activate</span></span>

<span data-ttu-id="4e4bd-1686">**Ícone** ![ Ícone ativar rato de classe de anfitrião](./media/user-guide/usbx-events/image115.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1686">**Icon** ![Host Class Hid Mouse Activate icon](./media/user-guide/usbx-events/image115.png)</span></span>

<span data-ttu-id="4e4bd-1687">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1687">**Description**</span></span>

<span data-ttu-id="4e4bd-1688">Este evento representa um evento USBX Host Class Hid Mouse Activate Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1688">This event represents a USBX Host Class Hid Mouse Activate Event.</span></span>

<span data-ttu-id="4e4bd-1689">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1689">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1690">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1690">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1691">Info Field 2: Identificação do cliente escondida.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1691">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="4e4bd-1692">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1692">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1693">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1693">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-mouse-deactivate"></a><span data-ttu-id="4e4bd-1694">Classe de anfitrião Hid Rato Desativado</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1694">Host Class Hid Mouse Deactivate</span></span> 

#### <a name="ux_host_class_hid_mouse_deactivate"></a><span data-ttu-id="4e4bd-1695">ux_host_class_hid_mouse_deactivate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1695">ux_host_class_hid_mouse_deactivate</span></span>

<span data-ttu-id="4e4bd-1696">**Ícone** ![ Ícone de desativado do rato da classe do anfitrião](./media/user-guide/usbx-events/image116.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1696">**Icon** ![Host Class Hid Mouse Deactivate icon](./media/user-guide/usbx-events/image116.png)</span></span>

<span data-ttu-id="4e4bd-1697">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1697">**Description**</span></span>

- <span data-ttu-id="4e4bd-1698">Este evento representa um evento de desativado da classe USBX Da Classe Hid Mouse.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1698">This event represents a USBX Host Class Hid Mouse Deactivate Event.</span></span>

<span data-ttu-id="4e4bd-1699">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1699">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1700">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1700">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1701">Info Field 2: Identificação do cliente escondida.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1701">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="4e4bd-1702">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1702">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1703">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1703">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-remote-control-activate"></a><span data-ttu-id="4e4bd-1704">Classe de anfitrião hid controlo remoto ativado</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1704">Host Class Hid Remote Control Activate</span></span> 

#### <a name="ux_host_class_hid_remote_control_activate"></a><span data-ttu-id="4e4bd-1705">ux_host_class_hid_remote_control_activate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1705">ux_host_class_hid_remote_control_activate</span></span>

<span data-ttu-id="4e4bd-1706">**Ícone** ![ Classe de anfitrião hid remote controle ícone ativar](./media/user-guide/usbx-events/image117.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1706">**Icon** ![Host Class Hid Remote Control Activate icon](./media/user-guide/usbx-events/image117.png)</span></span>

<span data-ttu-id="4e4bd-1707">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1707">**Description**</span></span>

<span data-ttu-id="4e4bd-1708">Este evento representa um evento usbx host class Hid Remote Control Activate Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1708">This event represents a USBX Host Class Hid Remote Control Activate Event.</span></span>

<span data-ttu-id="4e4bd-1709">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1709">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1710">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1710">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1711">Info Field 2: Identificação do cliente escondida.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1711">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="4e4bd-1712">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1712">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1713">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1713">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-remote-control-deactivate"></a><span data-ttu-id="4e4bd-1714">Classe de anfitrião hid remote control desativado</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1714">Host Class Hid Remote Control Deactivate</span></span> 

#### <a name="ux_host_class_hid_remote_control_deactivate"></a><span data-ttu-id="4e4bd-1715">ux_host_class_hid_remote_control_deactivate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1715">ux_host_class_hid_remote_control_deactivate</span></span>

<span data-ttu-id="4e4bd-1716">**Ícone** ![ Classe de anfitrião hid remote control desativado ícone](./media/user-guide/usbx-events/image118.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1716">**Icon** ![Host Class Hid Remote Control Deactivate icon](./media/user-guide/usbx-events/image118.png)</span></span>

<span data-ttu-id="4e4bd-1717">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1717">**Description**</span></span>

<span data-ttu-id="4e4bd-1718">Este evento representa um evento de desativado do controlo remoto USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1718">This event represents a USBX Host Class Hid Remote Control Deactivate Event.</span></span>

<span data-ttu-id="4e4bd-1719">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1719">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1720">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1720">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1721">Info Field 2: Identificação do cliente escondida.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1721">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="4e4bd-1722">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1722">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1723">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1723">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-report-get"></a><span data-ttu-id="4e4bd-1724">Relatório hid classe anfitrião obter</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1724">Host Class Hid Report Get</span></span> 

#### <a name="ux_host_class_hid_report_get"></a><span data-ttu-id="4e4bd-1725">ux_host_class_hid_report_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1725">ux_host_class_hid_report_get</span></span>

<span data-ttu-id="4e4bd-1726">**Ícone** ![ Relatório hid classe anfitrião Obter ícone](./media/user-guide/usbx-events/image119.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1726">**Icon** ![Host Class Hid Report Get icon](./media/user-guide/usbx-events/image119.png)</span></span>

<span data-ttu-id="4e4bd-1727">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1727">**Description**</span></span>

<span data-ttu-id="4e4bd-1728">Este evento representa um relatório hid de classe de anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1728">This event represents a USBX Host Class Hid Report Get.</span></span>

<span data-ttu-id="4e4bd-1729">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1729">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1730">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1730">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1731">Info Field 2: Relatório do cliente.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1731">Info Field 2: Client report.</span></span>
- <span data-ttu-id="4e4bd-1732">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1732">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1733">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1733">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-report-set"></a><span data-ttu-id="4e4bd-1734">Conjunto de relatório hid classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1734">Host Class Hid Report Set</span></span> 

#### <a name="ux_host_class_hid_report_set"></a><span data-ttu-id="4e4bd-1735">ux_host_class_hid_report_set</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1735">ux_host_class_hid_report_set</span></span>

<span data-ttu-id="4e4bd-1736">**Ícone** ![ Ícone de conjunto de relatório de classe de anfitrião hid](./media/user-guide/usbx-events/image120.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1736">**Icon** ![Host Class Hid Report Set icon](./media/user-guide/usbx-events/image120.png)</span></span>

<span data-ttu-id="4e4bd-1737">**Descrição** Este evento representa um conjunto de relatórios hid da classe de anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1737">**Description** This event represents a USBX Host Class Hid Report Set.</span></span>

<span data-ttu-id="4e4bd-1738">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1738">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1739">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1739">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1740">Info Field 2: Relatório do cliente.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1740">Info Field 2: Client report.</span></span>
- <span data-ttu-id="4e4bd-1741">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1741">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1742">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1742">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-activate"></a><span data-ttu-id="4e4bd-1743">Centro de classe de anfitrião Ativar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1743">Host Class Hub Activate</span></span> 

#### <a name="ux_host_class_hub_activate"></a><span data-ttu-id="4e4bd-1744">ux_host_class_hub_activate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1744">ux_host_class_hub_activate</span></span>

<span data-ttu-id="4e4bd-1745">**Ícone** ![ Ícone ativar o centro de classe do anfitrião](./media/user-guide/usbx-events/image121.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1745">**Icon** ![Host Class Hub Activate icon](./media/user-guide/usbx-events/image121.png)</span></span>

<span data-ttu-id="4e4bd-1746">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1746">**Description**</span></span>

<span data-ttu-id="4e4bd-1747">Este evento representa um evento USBX Host Class Hub Activate Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1747">This event represents a USBX Host Class Hub Activate Event.</span></span>

<span data-ttu-id="4e4bd-1748">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1748">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-1749">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1749">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1750">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1750">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1751">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1751">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1752">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1752">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-change-detect"></a><span data-ttu-id="4e4bd-1753">Deteção de mudança de centro de classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1753">Host Class Hub Change Detect</span></span> 

#### <a name="ux_host_class_hub_change_detect"></a><span data-ttu-id="4e4bd-1754">ux_host_class_hub_change_detect</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1754">ux_host_class_hub_change_detect</span></span>

<span data-ttu-id="4e4bd-1755">**Ícone** ![ Ícone de deteção de mudança de centro de classe de anfitrião](./media/user-guide/usbx-events/image122.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1755">**Icon** ![Host Class Hub Change Detect icon](./media/user-guide/usbx-events/image122.png)</span></span>

<span data-ttu-id="4e4bd-1756">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1756">**Description**</span></span>

<span data-ttu-id="4e4bd-1757">Este evento representa um evento usbx host Class Hub Change Detect.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1757">This event represents a USBX Host Class Hub Change Detect Event.</span></span>

<span data-ttu-id="4e4bd-1758">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1758">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1759">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1759">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1760">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1760">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1761">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1761">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1762">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1762">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-deactivate"></a><span data-ttu-id="4e4bd-1763">Centro de classe de anfitrião desativar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1763">Host Class Hub Deactivate</span></span> 

#### <a name="ux_host_class_hub_deactivate"></a><span data-ttu-id="4e4bd-1764">ux_host_class_hub_deactivate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1764">ux_host_class_hub_deactivate</span></span>

<span data-ttu-id="4e4bd-1765">**Ícone** ![ Ícone de desativado do hub de classe de anfitrião](./media/user-guide/usbx-events/image123.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1765">**Icon** ![Host Class Hub Deactivate icon](./media/user-guide/usbx-events/image123.png)</span></span>

<span data-ttu-id="4e4bd-1766">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1766">**Description**</span></span>

<span data-ttu-id="4e4bd-1767">Este evento representa um evento de desativado do Hub de Classe de Anfitriões USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1767">This event represents a USBX Host Class Hub Deactivate Event.</span></span>

<span data-ttu-id="4e4bd-1768">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1768">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1769">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1769">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1770">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1770">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1771">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1771">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1772">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1772">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-connection-process"></a><span data-ttu-id="4e4bd-1773">Processo de ligação de mudança de porta do hub de classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1773">Host Class Hub Port Change Connection Process</span></span> 

#### <a name="ux_host_class_hub_change_connection_process"></a><span data-ttu-id="4e4bd-1774">ux_host_class_hub_change_connection_process</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1774">ux_host_class_hub_change_connection_process</span></span>

<span data-ttu-id="4e4bd-1775">**Ícone** ![ Ícone do processo de mudança de ligação do hub da classe do anfitrião](./media/user-guide/usbx-events/image124.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1775">**Icon** ![Host Class Hub Port Change Connection Process icon](./media/user-guide/usbx-events/image124.png)</span></span>

<span data-ttu-id="4e4bd-1776">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1776">**Description**</span></span>

<span data-ttu-id="4e4bd-1777">Este evento representa um evento usbx host Class Hub Connection Process Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1777">This event represents a USBX Host Class Hub Port Change Connection Process Event.</span></span>

<span data-ttu-id="4e4bd-1778">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1778">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1779">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1779">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1780">Info Field 2: Porta.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1780">Info Field 2: Port.</span></span>
- <span data-ttu-id="4e4bd-1781">Info Field 3: Estado da porta.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1781">Info Field 3: Port status.</span></span>
- <span data-ttu-id="4e4bd-1782">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1782">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-enable-process"></a><span data-ttu-id="4e4bd-1783">Processo de alteração da porta do hub de classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1783">Host Class Hub Port Change Enable Process</span></span> 

#### <a name="ux_host_class_hub_port_change_enable_process"></a><span data-ttu-id="4e4bd-1784">ux_host_class_hub_port_change_enable_process</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1784">ux_host_class_hub_port_change_enable_process</span></span>

<span data-ttu-id="4e4bd-1785">**Ícone** ![ Ícone de mudança de carro do hub de classe de anfitrião](./media/user-guide/usbx-events/image125.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1785">**Icon** ![Host Class Hub Port Change Enable Process icon](./media/user-guide/usbx-events/image125.png)</span></span>

<span data-ttu-id="4e4bd-1786">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1786">**Description**</span></span>

<span data-ttu-id="4e4bd-1787">Este evento representa um evento usbx host Class Hub Enable Process Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1787">This event represents a USBX Host Class Hub Port Change Enable Process Event.</span></span>

<span data-ttu-id="4e4bd-1788">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1788">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1789">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1789">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1790">Info Field 2: Porta.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1790">Info Field 2: Port.</span></span>
- <span data-ttu-id="4e4bd-1791">Info Field 3: Estado da porta.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1791">Info Field 3: Port status.</span></span>
- <span data-ttu-id="4e4bd-1792">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1792">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-over-current-process"></a><span data-ttu-id="4e4bd-1793">Mudança de porta do hub de classe de anfitrião sobre o processo atual</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1793">Host Class Hub Port Change Over Current Process</span></span> 

#### <a name="ux_host_class_hub_port_change_over_current_process"></a><span data-ttu-id="4e4bd-1794">ux_host_class_hub_port_change_over_current_process</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1794">ux_host_class_hub_port_change_over_current_process</span></span>

<span data-ttu-id="4e4bd-1795">**Ícone** ![ Mudança de porta do hub do anfitrião sobre o ícone do processo atual](./media/user-guide/usbx-events/image126.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1795">**Icon** ![Host Class Hub Port Change Over Current Process icon](./media/user-guide/usbx-events/image126.png)</span></span>

<span data-ttu-id="4e4bd-1796">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1796">**Description**</span></span>

<span data-ttu-id="4e4bd-1797">Este evento representa a atribuição de um pacote através de nx_packet_allocate.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1797">This event represents allocating a packet via nx_packet_allocate.</span></span>

<span data-ttu-id="4e4bd-1798">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1798">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1799">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1799">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1800">Info Field 2: Porta.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1800">Info Field 2: Port.</span></span>
- <span data-ttu-id="4e4bd-1801">Info Field 3: Estado da porta.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1801">Info Field 3: Port status.</span></span>
- <span data-ttu-id="4e4bd-1802">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1802">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-reset-process"></a><span data-ttu-id="4e4bd-1803">Processo de reset de mudança de porta do hub de classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1803">Host Class Hub Port Change Reset Process</span></span> 

#### <a name="ux_host_class_hub_port_change_reset_process"></a><span data-ttu-id="4e4bd-1804">ux_host_class_hub_port_change_reset_process</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1804">ux_host_class_hub_port_change_reset_process</span></span>

<span data-ttu-id="4e4bd-1805">**Ícone** ![ Ícone do processo de reposição do processo de mudança de porta do hub da classe do anfitrião](./media/user-guide/usbx-events/image127.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1805">**Icon** ![Host Class Hub Port Change Reset Process icon](./media/user-guide/usbx-events/image127.png)</span></span>

<span data-ttu-id="4e4bd-1806">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1806">**Description**</span></span>

<span data-ttu-id="4e4bd-1807">Este evento representa um evento de reset de mudança de porta do hub de classe USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1807">This event represents a USBX Host Class Hub Port Change Reset Process Event.</span></span>

<span data-ttu-id="4e4bd-1808">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1808">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1809">Info Field 1: Hub.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1809">Info Field 1: Hub.</span></span> <span data-ttu-id="4e4bd-1810">Info Field 2: Porta.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1810">Info Field 2: Port.</span></span>
- <span data-ttu-id="4e4bd-1811">Info Field 3: Estado da porta.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1811">Info Field 3: Port status.</span></span>
- <span data-ttu-id="4e4bd-1812">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1812">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-suspend-process"></a><span data-ttu-id="4e4bd-1813">Processo de suspensão de alteração de mudança de porta do hub de classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1813">Host Class Hub Port Change Suspend Process</span></span> 

#### <a name="ux_host_class_hub_port_change_suspend_process"></a><span data-ttu-id="4e4bd-1814">ux_host_class_hub_port_change_suspend_process</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1814">ux_host_class_hub_port_change_suspend_process</span></span>

<span data-ttu-id="4e4bd-1815">**Ícone** ![ Ícone de processo de suspensão de mudança de porta do hub de classe de anfitrião](./media/user-guide/usbx-events/image128.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1815">**Icon** ![Host Class Hub Port Change Suspend Process icon](./media/user-guide/usbx-events/image128.png)</span></span>

<span data-ttu-id="4e4bd-1816">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1816">**Description**</span></span>

<span data-ttu-id="4e4bd-1817">Este evento representa um evento de suspensão de suspensão de alterações de portas do hub da classe USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1817">This event represents a USBX Host Class Hub Port Change Suspend Process Event.</span></span>

<span data-ttu-id="4e4bd-1818">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1818">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1819">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1819">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1820">Info Field 2: Porta.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1820">Info Field 2: Port.</span></span>
- <span data-ttu-id="4e4bd-1821">Info Field 3: Estado da porta.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1821">Info Field 3: Port status.</span></span>
- <span data-ttu-id="4e4bd-1822">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1822">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-activate"></a><span data-ttu-id="4e4bd-1823">Classe de anfitrião Pima Ativar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1823">Host Class Pima Activate</span></span> 

#### <a name="ux_host_class_pima_activate"></a><span data-ttu-id="4e4bd-1824">ux_host_class_pima_activate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1824">ux_host_class_pima_activate</span></span>

<span data-ttu-id="4e4bd-1825">**Ícone** ![ Ícone de ativação classe de anfitrião Pima](./media/user-guide/usbx-events/image129.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1825">**Icon** ![Host Class Pima Activate icon](./media/user-guide/usbx-events/image129.png)</span></span>

<span data-ttu-id="4e4bd-1826">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1826">**Description**</span></span>

<span data-ttu-id="4e4bd-1827">Este evento representa um Evento Pima Activate Classe de Anfitriões USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1827">This event represents a USBX Host Class Pima Activate Event.</span></span>

<span data-ttu-id="4e4bd-1828">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1828">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1829">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1829">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1830">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1830">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1831">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1831">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1832">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1832">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-deactivate"></a><span data-ttu-id="4e4bd-1833">Classe anfitriã Pima Desativado</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1833">Host Class Pima Deactivate</span></span> 

#### <a name="ux_host_class_pima_deactivate"></a><span data-ttu-id="4e4bd-1834">ux_host_class_pima_deactivate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1834">ux_host_class_pima_deactivate</span></span>

<span data-ttu-id="4e4bd-1835">**Ícone** ![ Ícone de desativado classe de anfitrião Pima](./media/user-guide/usbx-events/image130.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1835">**Icon** ![Host Class Pima Deactivate icon](./media/user-guide/usbx-events/image130.png)</span></span>

<span data-ttu-id="4e4bd-1836">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1836">**Description**</span></span>

<span data-ttu-id="4e4bd-1837">Este evento representa um Evento de Desativado Pima da Classe Pima da Classe Anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1837">This event represents a USBX Host Class Pima Deactivate Event.</span></span>

<span data-ttu-id="4e4bd-1838">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1838">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1839">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1839">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1840">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1840">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1841">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1841">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1842">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1842">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-device-info-get"></a><span data-ttu-id="4e4bd-1843">Informações de dispositivo pima classe anfitrião obter</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1843">Host Class Pima Device Info Get</span></span> 

#### <a name="ux_host_class_pima_device_info_get"></a><span data-ttu-id="4e4bd-1844">ux_host_class_pima_device_info_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1844">ux_host_class_pima_device_info_get</span></span>

<span data-ttu-id="4e4bd-1845">**Ícone** ![ Classe anfitrião Pima Device Info Obter ícone](./media/user-guide/usbx-events/image131.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1845">**Icon** ![Host Class Pima Device Info Get icon](./media/user-guide/usbx-events/image131.png)</span></span>

<span data-ttu-id="4e4bd-1846">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1846">**Description**</span></span>

<span data-ttu-id="4e4bd-1847">Este evento representa um evento de info get da classe Pima da classe usbx.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1847">This event represents a USBX Host Class Pima Device Info Get Event.</span></span>

<span data-ttu-id="4e4bd-1848">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1848">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1849">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1849">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1850">Info Field 2: Dispositivo Pima.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1850">Info Field 2: Pima device.</span></span>
- <span data-ttu-id="4e4bd-1851">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1851">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1852">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1852">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-device-reset"></a><span data-ttu-id="4e4bd-1853">Reset do dispositivo Pima da classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1853">Host Class Pima Device Reset</span></span> 

#### <a name="ux_host_class_pima_device_reset"></a><span data-ttu-id="4e4bd-1854">ux_host_class_pima_device_reset</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1854">ux_host_class_pima_device_reset</span></span>

<span data-ttu-id="4e4bd-1855">**Ícone** ![ Ícone de reset do dispositivo Pima da classe anfitrião](./media/user-guide/usbx-events/image132.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1855">**Icon** ![Host Class Pima Device Reset icon](./media/user-guide/usbx-events/image132.png)</span></span>

<span data-ttu-id="4e4bd-1856">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1856">**Description**</span></span>

<span data-ttu-id="4e4bd-1857">Este evento representa um evento de reset do dispositivo Pima da classe de anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1857">This event represents a USBX Host Class Pima Device Reset Event.</span></span>

<span data-ttu-id="4e4bd-1858">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1858">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1859">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1859">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1860">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1860">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1861">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1861">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1862">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1862">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-notification"></a><span data-ttu-id="4e4bd-1863">Notificação Pima classe anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1863">Host Class Pima Notification</span></span> 

#### <a name="ux_host_class_pima_notification"></a><span data-ttu-id="4e4bd-1864">ux_host_class_pima_notification</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1864">ux_host_class_pima_notification</span></span>

<span data-ttu-id="4e4bd-1865">**Ícone** ![ Ícone de notificação Pima classe anfitrião](./media/user-guide/usbx-events/image133.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1865">**Icon** ![Host Class Pima Notification icon](./media/user-guide/usbx-events/image133.png)</span></span>

<span data-ttu-id="4e4bd-1866">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1866">**Description**</span></span>

<span data-ttu-id="4e4bd-1867">Este evento representa um Evento de Notificação Pima da Classe Pima da classe de anfitriões USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1867">This event represents a USBX Host Class Pima Notification Event.</span></span>

<span data-ttu-id="4e4bd-1868">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1868">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1869">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1869">Info Field 1: Class instance.</span></span> <span data-ttu-id="4e4bd-1870">Info Field 2: Código de evento.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1870">Info Field 2: Event code.</span></span>
- <span data-ttu-id="4e4bd-1871">Info Field 3: ID de transação.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1871">Info Field 3: Transaction ID.</span></span>
- <span data-ttu-id="4e4bd-1872">Info Campo 4: Parâmetro1.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1872">Info Field 4: Parameter1.</span></span>

### <a name="host-class-pima-number-objects-get"></a><span data-ttu-id="4e4bd-1873">Objetos de número pima classe anfitrião obtêm</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1873">Host Class Pima Number Objects Get</span></span> 

#### <a name="ux_host_class_pima_number_objects_get"></a><span data-ttu-id="4e4bd-1874">ux_host_class_pima_number_objects_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1874">ux_host_class_pima_number_objects_get</span></span>

<span data-ttu-id="4e4bd-1875">**Ícone** ![ Objetos de número pima classe anfitrião obter ícone](./media/user-guide/usbx-events/image134.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1875">**Icon** ![Host Class Pima Number Objects Get icon](./media/user-guide/usbx-events/image134.png)</span></span>

<span data-ttu-id="4e4bd-1876">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1876">**Description**</span></span>

<span data-ttu-id="4e4bd-1877">Este evento representa um evento de objetos de número pima da classe usbx.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1877">This event represents a USBX Host Class Pima Number Objects Get Event.</span></span>

<span data-ttu-id="4e4bd-1878">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1878">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1879">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1879">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1880">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1880">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1881">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1881">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1882">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1882">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-close"></a><span data-ttu-id="4e4bd-1883">Objeto Pima classe anfitrião perto</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1883">Host Class Pima Object Close</span></span> 

#### <a name="ux_host_class_pima_object_close"></a><span data-ttu-id="4e4bd-1884">ux_host_class_pima_object_close</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1884">ux_host_class_pima_object_close</span></span>

<span data-ttu-id="4e4bd-1885">**Ícone** ![ Ícone de fecho de objeto pima classe anfitrião](./media/user-guide/usbx-events/image135.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1885">**Icon** ![Host Class Pima Object Close icon](./media/user-guide/usbx-events/image135.png)</span></span>

<span data-ttu-id="4e4bd-1886">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1886">**Description**</span></span>

<span data-ttu-id="4e4bd-1887">Este evento representa um evento usbx host Class Pima Object Close Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1887">This event represents a USBX Host Class Pima Object Close Event.</span></span>

<span data-ttu-id="4e4bd-1888">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1888">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1889">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1889">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1890">Info Field 2: Objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1890">Info Field 2: Object.</span></span>
- <span data-ttu-id="4e4bd-1891">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1891">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1892">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1892">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-copy"></a><span data-ttu-id="4e4bd-1893">Cópia do objeto Pima da classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1893">Host Class Pima Object Copy</span></span> 

#### <a name="ux_host_class_pima_object_copy"></a><span data-ttu-id="4e4bd-1894">ux_host_class_pima_object_copy</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1894">ux_host_class_pima_object_copy</span></span>

<span data-ttu-id="4e4bd-1895">**Ícone** ![ Ícone de cópia de objeto de classe de anfitrião Pima](./media/user-guide/usbx-events/image136.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1895">**Icon** ![Host Class Pima Object Copy icon](./media/user-guide/usbx-events/image136.png)</span></span>

<span data-ttu-id="4e4bd-1896">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1896">**Description**</span></span>

<span data-ttu-id="4e4bd-1897">Este evento representa um evento usbx host Class Pima Object Copy Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1897">This event represents a USBX Host Class Pima Object Copy Event.</span></span>

<span data-ttu-id="4e4bd-1898">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1898">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1899">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1899">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1900">Info Field 2: Pega do objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1900">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4e4bd-1901">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1901">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1902">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1902">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-delete"></a><span data-ttu-id="4e4bd-1903">Excluir objeto pima classe anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1903">Host Class Pima Object Delete</span></span> 

#### <a name="ux_host_class_pima_object_delete"></a><span data-ttu-id="4e4bd-1904">ux_host_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1904">ux_host_class_pima_object_delete</span></span>

<span data-ttu-id="4e4bd-1905">**Ícone** ![ Ícone de exclusão de objeto pima classe anfitrião](./media/user-guide/usbx-events/image137.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1905">**Icon** ![Host Class Pima Object Delete icon](./media/user-guide/usbx-events/image137.png)</span></span>

<span data-ttu-id="4e4bd-1906">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1906">**Description**</span></span>

<span data-ttu-id="4e4bd-1907">Este evento representa um evento de eliminação de objetos Pima da classe usbx.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1907">This event represents a USBX Host Class Pima Object Delete Event.</span></span>

<span data-ttu-id="4e4bd-1908">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1908">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1909">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1909">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1910">Info Field 2: Pega do objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1910">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4e4bd-1911">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1911">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1912">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1912">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-get"></a><span data-ttu-id="4e4bd-1913">Objeto Pima classe anfitrião obter</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1913">Host Class Pima Object Get</span></span> 

#### <a name="ux_host_class_pima_object_get"></a><span data-ttu-id="4e4bd-1914">ux_host_class_pima_object_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1914">ux_host_class_pima_object_get</span></span>

<span data-ttu-id="4e4bd-1915">**Ícone** ![ Classe anfitrião Pima Objeto Obter ícone](./media/user-guide/usbx-events/image138.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1915">**Icon** ![Host Class Pima Object Get icon](./media/user-guide/usbx-events/image138.png)</span></span>

<span data-ttu-id="4e4bd-1916">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1916">**Description**</span></span>

<span data-ttu-id="4e4bd-1917">Este evento representa obter informações da RARP através de nx_rarp_info_get.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1917">This event represents getting RARP information via nx_rarp_info_get.</span></span>

<span data-ttu-id="4e4bd-1918">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1918">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1919">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1919">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1920">Info Field 2: Pega do objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1920">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4e4bd-1921">Info Field 3: Objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1921">Info Field 3: Object.</span></span>
- <span data-ttu-id="4e4bd-1922">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1922">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-info-get"></a><span data-ttu-id="4e4bd-1923">Hospeda classe Pima Objeto Info Obter</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1923">Host Class Pima Object Info Get</span></span> 

#### <a name="ux_host_class_pima_object_info_get"></a><span data-ttu-id="4e4bd-1924">ux_host_class_pima_object_info_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1924">ux_host_class_pima_object_info_get</span></span>

<span data-ttu-id="4e4bd-1925">**Ícone** ![ Classe anfitrião Pima Objeto Info Obter ícone](./media/user-guide/usbx-events/image139.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1925">**Icon** ![Host Class Pima Object Info Get icon](./media/user-guide/usbx-events/image139.png)</span></span>

<span data-ttu-id="4e4bd-1926">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1926">**Description**</span></span>

<span data-ttu-id="4e4bd-1927">Este evento representa um evento USBX Host Class Pima Object Info Get.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1927">This event represents a USBX Host Class Pima Object Info Get Event.</span></span>

<span data-ttu-id="4e4bd-1928">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1928">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1929">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1929">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1930">Info Field 2: Pega do objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1930">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4e4bd-1931">Info Field 3: Objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1931">Info Field 3: Object.</span></span>
- <span data-ttu-id="4e4bd-1932">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1932">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-info-send"></a><span data-ttu-id="4e4bd-1933">Página de anfitrião Pima Object Info Enviar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1933">Host Class Pima Object Info Send</span></span> 

#### <a name="ux_host_class_pima_object_info_send"></a><span data-ttu-id="4e4bd-1934">ux_host_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1934">ux_host_class_pima_object_info_send</span></span>

<span data-ttu-id="4e4bd-1935">**Ícone** ![ Classe anfitrião Pima Objeto Info Enviar ícone](./media/user-guide/usbx-events/image140.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1935">**Icon** ![Host Class Pima Object Info Send icon](./media/user-guide/usbx-events/image140.png)</span></span>

<span data-ttu-id="4e4bd-1936">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1936">**Description**</span></span>

<span data-ttu-id="4e4bd-1937">Este evento representa um evento de envio de informação de objeto pima da classe USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1937">This event represents a USBX Host Class Pima Object Info Send Event.</span></span>

<span data-ttu-id="4e4bd-1938">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1938">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1939">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1939">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1940">Info Field 2: Objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1940">Info Field 2: Object.</span></span>
- <span data-ttu-id="4e4bd-1941">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1941">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1942">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1942">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-move"></a><span data-ttu-id="4e4bd-1943">Movimento de objeto classe de anfitrião Pima</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1943">Host Class Pima Object Move</span></span> 

#### <a name="ux_host_class_pima_object_move"></a><span data-ttu-id="4e4bd-1944">ux_host_class_pima_object_move</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1944">ux_host_class_pima_object_move</span></span>

<span data-ttu-id="4e4bd-1945">**Ícone** ![ Ícone de movimento de objeto de classe de anfitrião Pima](./media/user-guide/usbx-events/image141.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1945">**Icon** ![Host Class Pima Object Move icon](./media/user-guide/usbx-events/image141.png)</span></span>

<span data-ttu-id="4e4bd-1946">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1946">**Description**</span></span>

<span data-ttu-id="4e4bd-1947">Este evento representa um evento USBX Host Class Pima Object Move Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1947">This event reprThis event represents a USBX Host Class Pima Object Move Event.</span></span>

<span data-ttu-id="4e4bd-1948">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1948">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1949">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1949">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1950">Info Field 2: Pega do objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1950">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4e4bd-1951">Info Field 3: Objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1951">Info Field 3: Object.</span></span>
- <span data-ttu-id="4e4bd-1952">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1952">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-send"></a><span data-ttu-id="4e4bd-1953">Envio de objeto pima classe anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1953">Host Class Pima Object Send</span></span> 

#### <a name="ux_host_class_pima_object_move"></a><span data-ttu-id="4e4bd-1954">ux_host_class_pima_object_move</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1954">ux_host_class_pima_object_move</span></span>

<span data-ttu-id="4e4bd-1955">**Ícone** ![ Ícone de envio de objeto pima classe anfitrião](./media/user-guide/usbx-events/image142.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1955">**Icon** ![Host Class Pima Object Send icon](./media/user-guide/usbx-events/image142.png)</span></span>

<span data-ttu-id="4e4bd-1956">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1956">**Description**</span></span>

<span data-ttu-id="4e4bd-1957">Este evento representa um evento de envio de objetos Pima da classe usbx.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1957">This event represents a USBX Host Class Pima Object Send Event.</span></span>

<span data-ttu-id="4e4bd-1958">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1958">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1959">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1959">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1960">Info Field 2: Objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1960">Info Field 2: Object.</span></span>
- <span data-ttu-id="4e4bd-1961">Info Field 3: Tampão de objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1961">Info Field 3: Object buffer.</span></span>
- <span data-ttu-id="4e4bd-1962">Info Campo 4: Comprimento do objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1962">Info Field 4: Object length.</span></span>

### <a name="host-class-pima-object-transfer-abort"></a><span data-ttu-id="4e4bd-1963">Aborto de transferência de objeto pima classe anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1963">Host Class Pima Object Transfer Abort</span></span> 

#### <a name="ux_host_class_pima_object_transfer_abort"></a><span data-ttu-id="4e4bd-1964">ux_host_class_pima_object_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1964">ux_host_class_pima_object_transfer_abort</span></span>

<span data-ttu-id="4e4bd-1965">**Ícone** ![ Ícone de aborto de transferência de objeto de classe Pima de anfitrião](./media/user-guide/usbx-events/image143.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1965">**Icon** ![Host Class Pima Object Transfer Abort icon](./media/user-guide/usbx-events/image143.png)</span></span>

<span data-ttu-id="4e4bd-1966">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1966">**Description**</span></span>

<span data-ttu-id="4e4bd-1967">Este evento representa um evento USBX Host Class Pima Object Transfer Abort.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1967">This event represents a USBX Host Class Pima Object Transfer Abort Event.</span></span>

<span data-ttu-id="4e4bd-1968">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1968">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1969">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1969">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1970">Info Field 2: Pega do objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1970">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4e4bd-1971">Info Field 3: Objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1971">Info Field 3: Object.</span></span>
- <span data-ttu-id="4e4bd-1972">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1972">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-read"></a><span data-ttu-id="4e4bd-1973">Classe de anfitrião Pima Read</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1973">Host Class Pima Read</span></span> 

#### <a name="ux_host_class_pima_read"></a><span data-ttu-id="4e4bd-1974">ux_host_class_pima_read</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1974">ux_host_class_pima_read</span></span>

<span data-ttu-id="4e4bd-1975">**Ícone** ![ Ícone de leitura de classe de anfitrião Pima](./media/user-guide/usbx-events/image144.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1975">**Icon** ![Host Class Pima Read icon](./media/user-guide/usbx-events/image144.png)</span></span>

<span data-ttu-id="4e4bd-1976">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1976">**Description**</span></span>

<span data-ttu-id="4e4bd-1977">Este evento representa um Evento de Leitura Pima da Classe Pima da Classe Anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1977">This event represents a USBX Host Class Pima Read Event.</span></span>

<span data-ttu-id="4e4bd-1978">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1978">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1979">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1979">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1980">Info Field 2: Ponteiro de dados.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1980">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4e4bd-1981">Info Field 3: Comprimento dos dados.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1981">Info Field 3: Data length.</span></span>
- <span data-ttu-id="4e4bd-1982">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1982">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-request-cancel"></a><span data-ttu-id="4e4bd-1983">Cancelamento de pedido de convite da classe anfitriã Pima</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1983">Host Class Pima Request Cancel</span></span> 

#### <a name="ux_host_class_pima_request_cancel"></a><span data-ttu-id="4e4bd-1984">ux_host_class_pima_request_cancel</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1984">ux_host_class_pima_request_cancel</span></span>

<span data-ttu-id="4e4bd-1985">**Ícone** ![ Classe anfitrião Pima Request Cancel ícone](./media/user-guide/usbx-events/image145.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1985">**Icon** ![Host Class Pima Request Cancel icon](./media/user-guide/usbx-events/image145.png)</span></span>

<span data-ttu-id="4e4bd-1986">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1986">**Description**</span></span>

<span data-ttu-id="4e4bd-1987">Este evento representa um evento de cancelamento de pedido de pedido de anfitrião USBX Pima.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1987">This event represents a USBX Host Class Pima Request Cancel Event.</span></span>

<span data-ttu-id="4e4bd-1988">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1988">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1989">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1989">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-1990">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1990">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-1991">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1991">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-1992">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1992">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-session-close"></a><span data-ttu-id="4e4bd-1993">Sessão Pima de classe de anfitrião fechar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1993">Host Class Pima Session Close</span></span> 

#### <a name="ux_host_class_pima_session_close"></a><span data-ttu-id="4e4bd-1994">ux_host_class_pima_session_close</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1994">ux_host_class_pima_session_close</span></span>

<span data-ttu-id="4e4bd-1995">**Ícone** ![ Ícone de fecho de sessão pima de classe de anfitrião](./media/user-guide/usbx-events/image146.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1995">**Icon** ![Host Class Pima Session Close icon](./media/user-guide/usbx-events/image146.png)</span></span>

<span data-ttu-id="4e4bd-1996">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1996">**Description**</span></span>

<span data-ttu-id="4e4bd-1997">Este evento representa um evento de encerramento de sessão Pima da classe de anfitriões USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1997">This event represents a USBX Host Class Pima Session Close Event.</span></span>

<span data-ttu-id="4e4bd-1998">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1998">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-1999">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-1999">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2000">Info Field 2: Sessão Pima.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2000">Info Field 2: Pima session.</span></span>
- <span data-ttu-id="4e4bd-2001">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2001">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2002">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2002">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-session-open"></a><span data-ttu-id="4e4bd-2003">Sessão Pima de classe de anfitrião Aberta</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2003">Host Class Pima Session Open</span></span> 

#### <a name="ux_host_class_pima_session_open"></a><span data-ttu-id="4e4bd-2004">ux_host_class_pima_session_open</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2004">ux_host_class_pima_session_open</span></span>

<span data-ttu-id="4e4bd-2005">**Ícone** ![ Ícone do open da sessão pima de classe de anfitrião](./media/user-guide/usbx-events/image147.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2005">**Icon** ![Host Class Pima Session Open icon](./media/user-guide/usbx-events/image147.png)</span></span>

<span data-ttu-id="4e4bd-2006">**Descrição** Este evento representa um evento OPEN de Sessão Pima da Classe Pima da classe USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2006">**Description** This event represents a USBX Host Class Pima Session Open Event.</span></span>

<span data-ttu-id="4e4bd-2007">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2007">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2008">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2008">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2009">Info Field 2: Sessão Pima.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2009">Info Field 2: Pima session.</span></span>
- <span data-ttu-id="4e4bd-2010">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2010">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2011">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2011">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-storage-ids-get"></a><span data-ttu-id="4e4bd-2012">Classe anfitrião Pima Storage Ids Obter</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2012">Host Class Pima Storage Ids Get</span></span> 

#### <a name="ux_host_class_pima_session_ids_get"></a><span data-ttu-id="4e4bd-2013">ux_host_class_pima_session_ids_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2013">ux_host_class_pima_session_ids_get</span></span>

<span data-ttu-id="4e4bd-2014">**Ícone** ![ Classe anfitrião Pima Storage Ids Obter ícone](./media/user-guide/usbx-events/image148.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2014">**Icon** ![Host Class Pima Storage Ids Get icon](./media/user-guide/usbx-events/image148.png)</span></span>

<span data-ttu-id="4e4bd-2015">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2015">**Description**</span></span>

<span data-ttu-id="4e4bd-2016">Este evento representa um evento DE ARMAZENAMENTO Pima Da Classe Pima da Classe USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2016">This event represents a USBX Host Class Pima Storage Ids Get Event.</span></span>

<span data-ttu-id="4e4bd-2017">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2017">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2018">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2018">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2019">nfo Field 2: Array de ID de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2019">nfo Field 2: Storage ID array.</span></span>
- <span data-ttu-id="4e4bd-2020">Info Field 3: Comprimento do ID de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2020">Info Field 3: Storage ID length.</span></span>
<span data-ttu-id="4e4bd-2021">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2021">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-storage-info-get"></a><span data-ttu-id="4e4bd-2022">Informações de armazenamento Pima classe anfitrião obter</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2022">Host Class Pima Storage Info Get</span></span> 

#### <a name="ux_host_class_pima_storage_info_get"></a><span data-ttu-id="4e4bd-2023">ux_host_class_pima_storage_info_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2023">ux_host_class_pima_storage_info_get</span></span>

<span data-ttu-id="4e4bd-2024">**Ícone** ![ Classe anfitrião Pima Storage Info Obter ícone](./media/user-guide/usbx-events/image149.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2024">**Icon** ![Host Class Pima Storage Info Get icon](./media/user-guide/usbx-events/image149.png)</span></span>

<span data-ttu-id="4e4bd-2025">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2025">**Description**</span></span>

<span data-ttu-id="4e4bd-2026">Este evento representa um evento USBX Host Class Pima Storage Info Get.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2026">This event represents a USBX Host Class Pima Storage Info Get Event.</span></span>

<span data-ttu-id="4e4bd-2027">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2027">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2028">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2028">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2029">Info Field 2: ID de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2029">Info Field 2: Storage ID.</span></span>
- <span data-ttu-id="4e4bd-2030">Info Field 3: Armazenamento.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2030">Info Field 3: Storage.</span></span>
- <span data-ttu-id="4e4bd-2031">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2031">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-thumb-get"></a><span data-ttu-id="4e4bd-2032">Classe anfitrião Pima Polegar Get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2032">Host Class Pima Thumb Get</span></span> 

#### <a name="ux_host_class_pima_thumb_get"></a><span data-ttu-id="4e4bd-2033">ux_host_class_pima_thumb_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2033">ux_host_class_pima_thumb_get</span></span>

<span data-ttu-id="4e4bd-2034">**Ícone** ![ Ícone de polegar Pima de classe de anfitrião](./media/user-guide/usbx-events/image150.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2034">**Icon** ![Host Class Pima Thumb Get icon](./media/user-guide/usbx-events/image150.png)</span></span>

<span data-ttu-id="4e4bd-2035">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2035">**Description**</span></span>

<span data-ttu-id="4e4bd-2036">Este evento representa não aceitar uma ligação do servidor TCP através de nx_tcp_server_socket_unaccept.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2036">This event represents unaccepting a TCP server connection via nx_tcp_server_socket_unaccept.</span></span>

<span data-ttu-id="4e4bd-2037">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2037">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-2038">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2038">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2039">Info Field 2: Pega do objeto.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2039">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="4e4bd-2040">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2040">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2041">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2041">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-write"></a><span data-ttu-id="4e4bd-2042">Classe de anfitrião Pima Escrever</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2042">Host Class Pima Write</span></span> 

#### <a name="ux_host_class_pima_thumb_get"></a><span data-ttu-id="4e4bd-2043">ux_host_class_pima_thumb_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2043">ux_host_class_pima_thumb_get</span></span>

<span data-ttu-id="4e4bd-2044">**Ícone** ![ Ícone de escrita classe de anfitrião Pima](./media/user-guide/usbx-events/image151.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2044">**Icon** ![Host Class Pima Write icon](./media/user-guide/usbx-events/image151.png)</span></span>

<span data-ttu-id="4e4bd-2045">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2045">**Description**</span></span>

<span data-ttu-id="4e4bd-2046">Este evento representa uma classe de anfitrião USBX Pima Write.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2046">This event represents a USBX Host Class Pima Write.</span></span>

<span data-ttu-id="4e4bd-2047">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2047">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2048">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2048">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-2049">Info Field 2: Ponteiro de dados.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2049">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4e4bd-2050">Info Field 3: Comprimento dos dados.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2050">Info Field 3: Data length.</span></span>
- <span data-ttu-id="4e4bd-2051">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2051">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-activate"></a><span data-ttu-id="4e4bd-2052">Ativar impressora de classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2052">Host Class Printer Activate</span></span> 

#### <a name="ux_host_class_printer_activate"></a><span data-ttu-id="4e4bd-2053">ux_host_class_printer_activate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2053">ux_host_class_printer_activate</span></span>

<span data-ttu-id="4e4bd-2054">**Ícone** ![ Ícone ativar impressora de classe de anfitrião](./media/user-guide/usbx-events/image152.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2054">**Icon** ![Host Class Printer Activate icon](./media/user-guide/usbx-events/image152.png)</span></span>

<span data-ttu-id="4e4bd-2055">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2055">**Description**</span></span>

<span data-ttu-id="4e4bd-2056">Este evento representa um evento usbx host Class Printer Activate Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2056">This event represents a USBX Host Class Printer Activate Event.</span></span>

<span data-ttu-id="4e4bd-2057">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2057">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2058">Info Field 1: Ponteiro para a instância IP.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2058">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="4e4bd-2059">Info Campo 2: Ponteiro para tomada.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2059">Info Field 2: Pointer to socket.</span></span>
- <span data-ttu-id="4e4bd-2060">Info Campo 3: Tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2060">Info Field 3: Type of service.</span></span>
- <span data-ttu-id="4e4bd-2061">Info Campo 4: Receber o tamanho da janela.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2061">Info Field 4: Receive window size.</span></span>

### <a name="host-class-printer-deactivate"></a><span data-ttu-id="4e4bd-2062">Impressora de classe de anfitrião desativar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2062">Host Class Printer Deactivate</span></span> 

#### <a name="ux_host_class_printer_deactivate"></a><span data-ttu-id="4e4bd-2063">ux_host_class_printer_deactivate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2063">ux_host_class_printer_deactivate</span></span>

<span data-ttu-id="4e4bd-2064">**Ícone** ![ Ícone de desativar impressora de classe de anfitrião](./media/user-guide/usbx-events/image153.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2064">**Icon** ![Host Class Printer Deactivate icon](./media/user-guide/usbx-events/image153.png)</span></span>

<span data-ttu-id="4e4bd-2065">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2065">**Description**</span></span>

<span data-ttu-id="4e4bd-2066">Este evento representa um evento de desativado da impressora usbx da classe de anfitrião.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2066">This event represents a USBX Host Class Printer Deactivate Event.</span></span>

<span data-ttu-id="4e4bd-2067">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2067">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2068">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2068">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2069">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2069">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2070">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2070">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2071">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2071">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-name-get"></a><span data-ttu-id="4e4bd-2072">Nome da impressora de classe de anfitrião obter</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2072">Host Class Printer Name Get</span></span> 

#### <a name="ux_host_class_printer_name_get"></a><span data-ttu-id="4e4bd-2073">ux_host_class_printer_name_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2073">ux_host_class_printer_name_get</span></span>

<span data-ttu-id="4e4bd-2074">**Ícone** ![ Nome da impressora de classe anfitrião obter ícone](./media/user-guide/usbx-events/image154.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2074">**Icon** ![Host Class Printer Name Get icon](./media/user-guide/usbx-events/image154.png)</span></span>

<span data-ttu-id="4e4bd-2075">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2075">**Description**</span></span>

<span data-ttu-id="4e4bd-2076">Este evento representa um evento de nome de impressora de classe de anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2076">This event represents a USBX Host Class Printer Name Get Event.</span></span>

<span data-ttu-id="4e4bd-2077">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2077">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-2078">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2078">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2079">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2079">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2080">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2080">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2081">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2081">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-read"></a><span data-ttu-id="4e4bd-2082">Leitura de impressora de classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2082">Host Class Printer Read</span></span> 

#### <a name="ux_host_class_printer_read"></a><span data-ttu-id="4e4bd-2083">ux_host_class_printer_read</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2083">ux_host_class_printer_read</span></span>

<span data-ttu-id="4e4bd-2084">**Ícone** ![ Ícone de leitura de impressora de classe de anfitrião](./media/user-guide/usbx-events/image155.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2084">**Icon** ![Host Class Printer Read icon](./media/user-guide/usbx-events/image155.png)</span></span>

<span data-ttu-id="4e4bd-2085">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2085">**Description**</span></span>

<span data-ttu-id="4e4bd-2086">Este evento representa um evento de leitura de impressora de classe de anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2086">This event represents a USBX Host Class Printer Read Event.</span></span>

<span data-ttu-id="4e4bd-2087">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2087">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2088">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2088">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2089">Info Field 2: Ponteiro de dados.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2089">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4e4bd-2090">Info Field 3: Comprimento solicitado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2090">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4e4bd-2091">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2091">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-soft-reset"></a><span data-ttu-id="4e4bd-2092">Reset suave da impressora de classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2092">Host Class Printer Soft Reset</span></span> 

#### <a name="ux_host_class_printer_soft_reset"></a><span data-ttu-id="4e4bd-2093">ux_host_class_printer_soft_reset</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2093">ux_host_class_printer_soft_reset</span></span>

<span data-ttu-id="4e4bd-2094">**Ícone** ![ Ícone de reset suave da impressora de classe de anfitrião](./media/user-guide/usbx-events/image156.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2094">**Icon** ![Host Class Printer Soft Reset icon](./media/user-guide/usbx-events/image156.png)</span></span>

<span data-ttu-id="4e4bd-2095">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2095">**Description**</span></span>

<span data-ttu-id="4e4bd-2096">Este evento representa um evento de reset suave da impressora de classe USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2096">This event represents a USBX Host Class Printer Soft Reset Event.</span></span>

<span data-ttu-id="4e4bd-2097">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2097">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2098">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2098">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2099">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2099">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2100">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2100">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2101">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2101">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-status-get"></a><span data-ttu-id="4e4bd-2102">Estado da impressora de classe de anfitrião obter</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2102">Host Class Printer Status Get</span></span> 

#### <a name="ux_host_class_printer_status_get"></a><span data-ttu-id="4e4bd-2103">ux_host_class_printer_status_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2103">ux_host_class_printer_status_get</span></span>

<span data-ttu-id="4e4bd-2104">**Ícone** ![ Estado da impressora de classe de anfitrião Obter ícone](./media/user-guide/usbx-events/image157.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2104">**Icon** ![Host Class Printer Status Get icon](./media/user-guide/usbx-events/image157.png)</span></span>

<span data-ttu-id="4e4bd-2105">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2105">**Description**</span></span>

<span data-ttu-id="4e4bd-2106">Este evento representa um evento usbx host Class Printer Status Get Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2106">This event represents a USBX Host Class Printer Status Get Event.</span></span>

<span data-ttu-id="4e4bd-2107">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2107">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2108">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2108">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2109">Info Field 2: Estado da impressora.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2109">Info Field 2: Printer status.</span></span>
- <span data-ttu-id="4e4bd-2110">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2110">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2111">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2111">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-write"></a><span data-ttu-id="4e4bd-2112">Escrita de impressora de classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2112">Host Class Printer Write</span></span> 

#### <a name="ux_host_class_printer_write"></a><span data-ttu-id="4e4bd-2113">ux_host_class_printer_write</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2113">ux_host_class_printer_write</span></span>

<span data-ttu-id="4e4bd-2114">**Ícone** ![ Ícone de escrita de impressora de classe de anfitrião](./media/user-guide/usbx-events/image158.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2114">**Icon** ![Host Class Printer Write icon](./media/user-guide/usbx-events/image158.png)</span></span>

<span data-ttu-id="4e4bd-2115">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2115">**Description**</span></span>

<span data-ttu-id="4e4bd-2116">Este evento representa uma escrita de impressora de classe de anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2116">This event represents a USBX Host Class Printer Write.</span></span>

<span data-ttu-id="4e4bd-2117">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2117">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-2118">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2118">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2119">Info Field 2: Ponteiro de dados.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2119">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4e4bd-2120">Info Field 3: Comprimento solicitado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2120">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4e4bd-2121">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2121">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-activate"></a><span data-ttu-id="4e4bd-2122">Ativação prolific da classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2122">Host Class Prolific Activate</span></span> 

#### <a name="ux_host_class_prolific_activate"></a><span data-ttu-id="4e4bd-2123">ux_host_class_prolific_activate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2123">ux_host_class_prolific_activate</span></span> 

<span data-ttu-id="4e4bd-2124">**Ícone** ![ Ícone de ativação prolific de classe de anfitrião](./media/user-guide/usbx-events/image159.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2124">**Icon** ![Host Class Prolific Activate icon](./media/user-guide/usbx-events/image159.png)</span></span>

<span data-ttu-id="4e4bd-2125">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2125">**Description**</span></span>

<span data-ttu-id="4e4bd-2126">Este evento representa um evento de ativação da classe de anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2126">This event represents a USBX Host Class Prolific Activate Event.</span></span>

<span data-ttu-id="4e4bd-2127">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2127">**Information Fields**</span></span> 

- <span data-ttu-id="4e4bd-2128">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2128">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2129">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2129">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2130">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2130">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2131">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2131">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-deactivate"></a><span data-ttu-id="4e4bd-2132">Classe de anfitrião Prolific Desativado</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2132">Host Class Prolific Deactivate</span></span> 

#### <a name="ux_host_class_prolific_deactivate"></a><span data-ttu-id="4e4bd-2133">ux_host_class_prolific_deactivate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2133">ux_host_class_prolific_deactivate</span></span> 

<span data-ttu-id="4e4bd-2134">**Ícone** ![ Ícone prolífico da classe de anfitrião](./media/user-guide/usbx-events/image160.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2134">**Icon** ![Host Class Prolific Deactivate icon](./media/user-guide/usbx-events/image160.png)</span></span>

<span data-ttu-id="4e4bd-2135">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2135">**Description**</span></span>

<span data-ttu-id="4e4bd-2136">Este evento representa um evento de desativado da classe USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2136">This event represents a USBX Host Class Prolific Deactivate Event.</span></span>

<span data-ttu-id="4e4bd-2137">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2137">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2138">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2138">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2139">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2139">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2140">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2140">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2141">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2141">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-abort-in-pipe"></a><span data-ttu-id="4e4bd-2142">Classe de anfitrião Prolific Ioctl Abortar no tubo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2142">Host Class Prolific Ioctl Abort In Pipe</span></span> 

#### <a name="ux_host_class_prolific_ioctl_abort_in_pipe"></a><span data-ttu-id="4e4bd-2143">ux_host_class_prolific_ioctl_abort_in_pipe</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2143">ux_host_class_prolific_ioctl_abort_in_pipe</span></span>

<span data-ttu-id="4e4bd-2144">**Ícone** ![ Classe de anfitrião Prolific I O C T T L Abortar no ícone do tubo](./media/user-guide/usbx-events/image161.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2144">**Icon** ![Host Class Prolific I O C T L Abort In Pipe icon](./media/user-guide/usbx-events/image161.png)</span></span>

<span data-ttu-id="4e4bd-2145">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2145">**Description**</span></span>

<span data-ttu-id="4e4bd-2146">Este evento representa um evento de confirmação da classe de anfitriões USBX Prolific Ioctl Abort in Pipe Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2146">This event represents a USBX Host Class Prolific Ioctl Abort In Pipe Event.</span></span>

<span data-ttu-id="4e4bd-2147">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2147">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2148">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2148">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2149">Info Field 2: Ponto final.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2149">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4e4bd-2150">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2150">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2151">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2151">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-abort-out-pipe"></a><span data-ttu-id="4e4bd-2152">Classe de anfitrião Prolific Ioctl AbortAr Tubo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2152">Host Class Prolific Ioctl Abort Out Pipe</span></span> 

#### <a name="ux_host_class_prolific_ioctl_abort_out_pipe"></a><span data-ttu-id="4e4bd-2153">ux_host_class_prolific_ioctl_abort_out_pipe</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2153">ux_host_class_prolific_ioctl_abort_out_pipe</span></span>

<span data-ttu-id="4e4bd-2154">**Ícone** ![ Classe de anfitrião Prolific I O C T L AbortAr Ícone do Tubo](./media/user-guide/usbx-events/image162.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2154">**Icon** ![Host Class Prolific I O C T L Abort Out Pipe icon](./media/user-guide/usbx-events/image162.png)</span></span>

<span data-ttu-id="4e4bd-2155">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2155">**Description**</span></span>

<span data-ttu-id="4e4bd-2156">Este evento representa um evento de tubo de aborto da classe usbx da classe de anfitriões Prolific Ioctl.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2156">This event represents a USBX Host Class Prolific Ioctl Abort Out Pipe Event.</span></span>

<span data-ttu-id="4e4bd-2157">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2157">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2158">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2158">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2159">Info Field 2: Ponto final.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2159">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4e4bd-2160">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2160">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2161">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2161">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-get-device-status"></a><span data-ttu-id="4e4bd-2162">Classe de anfitrião Prolific Ioctl Obter Estado do Dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2162">Host Class Prolific Ioctl Get Device Status</span></span> 

#### <a name="ux_host_class_prolific_ioctl_get_device_status"></a><span data-ttu-id="4e4bd-2163">ux_host_class_prolific_ioctl_get_device_status</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2163">ux_host_class_prolific_ioctl_get_device_status</span></span>

<span data-ttu-id="4e4bd-2164">**Ícone** ![ Classe de anfitrião Prolific I O C T L Obter Ícone de Estado do Dispositivo](./media/user-guide/usbx-events/image163.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2164">**Icon** ![Host Class Prolific I O C T L Get Device Status icon](./media/user-guide/usbx-events/image163.png)</span></span>

<span data-ttu-id="4e4bd-2165">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2165">**Description**</span></span>

<span data-ttu-id="4e4bd-2166">Este evento representa um evento de estado do dispositivo da classe usbx prolífica do recetor.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2166">This event represents a USBX Host Class Prolific Ioctl Get Device Status Event.</span></span>

<span data-ttu-id="4e4bd-2167">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2167">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2168">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2168">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2169">Info Field 2: Estado do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2169">Info Field 2: Device status.</span></span>
- <span data-ttu-id="4e4bd-2170">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2170">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2171">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2171">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-get-line-coding"></a><span data-ttu-id="4e4bd-2172">Classe de anfitrião Prolific Ioctl Obter Codificação de Linha</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2172">Host Class Prolific Ioctl Get Line Coding</span></span> 

#### <a name="ux_host_class_prolific_ioctl_get_line_coding"></a><span data-ttu-id="4e4bd-2173">ux_host_class_prolific_ioctl_get_line_coding</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2173">ux_host_class_prolific_ioctl_get_line_coding</span></span>

<span data-ttu-id="4e4bd-2174">**Ícone** ![ Classe de anfitrião Prolific I O C T L Obter Ícone de codificação de linha](./media/user-guide/usbx-events/image164.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2174">**Icon** ![Host Class Prolific I O C T L Get Line Coding icon](./media/user-guide/usbx-events/image164.png)</span></span>

<span data-ttu-id="4e4bd-2175">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2175">**Description**</span></span>

<span data-ttu-id="4e4bd-2176">Este evento representa um evento de codificação de linha da classe usbx prolífica.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2176">This event represents a USBX Host Class Prolific Ioctl Get Line Coding Event.</span></span>

<span data-ttu-id="4e4bd-2177">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2177">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2178">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2178">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2179">Info Field 2: Parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2179">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4e4bd-2180">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2180">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2181">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2181">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-purge"></a><span data-ttu-id="4e4bd-2182">Classe de anfitrião Prolific Ioctl Purga</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2182">Host Class Prolific Ioctl Purge</span></span> 

#### <a name="ux_host_class_prolific_ioctl_purge"></a><span data-ttu-id="4e4bd-2183">ux_host_class_prolific_ioctl_purge</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2183">ux_host_class_prolific_ioctl_purge</span></span>

<span data-ttu-id="4e4bd-2184">**Ícone** ![ Ícone de purga prolifico de classe de anfitrião](./media/user-guide/usbx-events/image165.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2184">**Icon** ![Host Class Prolific Ioctl Purge icon](./media/user-guide/usbx-events/image165.png)</span></span>

<span data-ttu-id="4e4bd-2185">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2185">**Description**</span></span>

<span data-ttu-id="4e4bd-2186">Este evento representa um evento de purga prolifico da classe usbx.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2186">This event represents a USBX Host Class Prolific Ioctl Purge Event.</span></span>

<span data-ttu-id="4e4bd-2187">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2187">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2188">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2188">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2189">Info Field 2: Parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2189">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4e4bd-2190">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2190">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2191">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2191">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-report-device"></a><span data-ttu-id="4e4bd-2192">Dispositivo de relatório prolific da classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2192">Host Class Prolific Ioctl Report Device</span></span> 

#### <a name="ux_host_class_prolific_ioctl_report_device"></a><span data-ttu-id="4e4bd-2193">ux_host_class_prolific_ioctl_report_device</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2193">ux_host_class_prolific_ioctl_report_device</span></span>

<span data-ttu-id="4e4bd-2194">**Ícone** ![ Ícone do dispositivo de relatório de relatório da classe anfitrião I O C T L](./media/user-guide/usbx-events/image166.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2194">**Icon** ![Host Class Prolific I O C T L Report Device icon](./media/user-guide/usbx-events/image166.png)</span></span>

<span data-ttu-id="4e4bd-2195">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2195">**Description**</span></span>

<span data-ttu-id="4e4bd-2196">Este evento representa um evento de alteração do estado do dispositivo de relatório do relatório do relatório da classe USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2196">This event represents a USBX Host Class Prolific Ioctl Report Device Status Change Event.</span></span>

<span data-ttu-id="4e4bd-2197">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2197">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2198">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2198">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2199">Info Field 2: Parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2199">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4e4bd-2200">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2200">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2201">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2201">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-send-break"></a><span data-ttu-id="4e4bd-2202">Classe de anfitrião Prolific Ioctl Enviar Pausa</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2202">Host Class Prolific Ioctl Send Break</span></span> 

#### <a name="ux_host_class_prolific_ioctl_send_break"></a><span data-ttu-id="4e4bd-2203">ux_host_class_prolific_ioctl_send_break</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2203">ux_host_class_prolific_ioctl_send_break</span></span>

<span data-ttu-id="4e4bd-2204">**Ícone** ![ Classe de anfitrião Prolific I O C T L Enviar Ícone de rutura](./media/user-guide/usbx-events/image167.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2204">**Icon** ![Host Class Prolific I O C T L Send Break icon](./media/user-guide/usbx-events/image167.png)</span></span>

<span data-ttu-id="4e4bd-2205">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2205">**Description**</span></span>

<span data-ttu-id="4e4bd-2206">Este evento representa um evento de envio de interrupção da classe USBX Da Classe Prolífica do Ioctl.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2206">This event represents a USBX Host Class Prolific Ioctl Send Break Event.</span></span>

<span data-ttu-id="4e4bd-2207">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2207">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2208">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2208">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2209">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2209">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2210">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2210">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2211">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2211">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-set-line-coding"></a><span data-ttu-id="4e4bd-2212">Codificação de linha de linha de conjunto prolific da classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2212">Host Class Prolific Ioctl Set Line Coding</span></span> 

#### <a name="ux_host_class_prolific_ioctl_set_line_coding"></a><span data-ttu-id="4e4bd-2213">ux_host_class_prolific_ioctl_set_line_coding</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2213">ux_host_class_prolific_ioctl_set_line_coding</span></span>

<span data-ttu-id="4e4bd-2214">**Ícone** ![ Ícone de codificação de linha de classe de anfitrião I O C T L](./media/user-guide/usbx-events/image168.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2214">**Icon** ![Host Class Prolific I O C T L Set Line Coding icon](./media/user-guide/usbx-events/image168.png)</span></span>

<span data-ttu-id="4e4bd-2215">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2215">**Description**</span></span>

<span data-ttu-id="4e4bd-2216">Este evento representa um evento de codificação de linha de linha de conjunto da classe USBX Prolific.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2216">This event represents a USBX Host Class Prolific Ioctl Set Line Coding Event.</span></span>

<span data-ttu-id="4e4bd-2217">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2217">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2218">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2218">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2219">Info Field 2: Parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2219">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4e4bd-2220">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2220">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2221">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2221">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-set-line-state"></a><span data-ttu-id="4e4bd-2222">Estado da linha de linha do conjunto de conjunto prolific da classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2222">Host Class Prolific Ioctl Set Line State</span></span> 

#### <a name="ux_host_class_prolific_ioctl_set_line_state"></a><span data-ttu-id="4e4bd-2223">ux_host_class_prolific_ioctl_set_line_state</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2223">ux_host_class_prolific_ioctl_set_line_state</span></span>

<span data-ttu-id="4e4bd-2224">**Ícone** ![ Classe de anfitrião Prolific I O C T L set Line State ícone](./media/user-guide/usbx-events/image169.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2224">**Icon** ![Host Class Prolific I O C T L Set Line State icon](./media/user-guide/usbx-events/image169.png)</span></span>

<span data-ttu-id="4e4bd-2225">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2225">**Description**</span></span>

<span data-ttu-id="4e4bd-2226">Este evento representa um evento de estado de linha de set prolific da classe USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2226">This event represents a USBX Host Class Prolific Ioctl Set Line State Event.</span></span>

<span data-ttu-id="4e4bd-2227">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2227">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2228">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2228">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2229">Info Field 2: Parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2229">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="4e4bd-2230">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2230">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2231">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2231">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-read"></a><span data-ttu-id="4e4bd-2232">Leitura Prolífica da Classe anfitriã</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2232">Host Class Prolific Read</span></span> 

#### <a name="ux_host_class_prolific_read"></a><span data-ttu-id="4e4bd-2233">ux_host_class_prolific_read</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2233">ux_host_class_prolific_read</span></span>

<span data-ttu-id="4e4bd-2234">**Ícone** ![ Ícone de leitura prolífica de classe de anfitrião](./media/user-guide/usbx-events/image170.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2234">**Icon** ![Host Class Prolific Read icon](./media/user-guide/usbx-events/image170.png)</span></span>

<span data-ttu-id="4e4bd-2235">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2235">**Description**</span></span>

<span data-ttu-id="4e4bd-2236">Este evento representa um evento de leitura prolífica da classe USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2236">This event represents a USBX Host Class Prolific Read Event.</span></span>

<span data-ttu-id="4e4bd-2237">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2237">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2238">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2238">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2239">Info Field 2: Ponteiro de dados.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2239">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4e4bd-2240">Info Field 3: Comprimento solicitado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2240">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4e4bd-2241">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2241">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-reception-start"></a><span data-ttu-id="4e4bd-2242">Início de receção prolific classe anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2242">Host Class Prolific Reception Start</span></span> 

#### <a name="ux_host_class_prolific_reception_start"></a><span data-ttu-id="4e4bd-2243">ux_host_class_prolific_reception_start</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2243">ux_host_class_prolific_reception_start</span></span>

<span data-ttu-id="4e4bd-2244">**Ícone** ![ Ícone de início de receção prolific de classe de anfitrião](./media/user-guide/usbx-events/image171.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2244">**Icon** ![Host Class Prolific Reception Start icon](./media/user-guide/usbx-events/image171.png)</span></span>

<span data-ttu-id="4e4bd-2245">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2245">**Description**</span></span>

<span data-ttu-id="4e4bd-2246">Este evento representa um evento de receção prolific da classe usbx.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2246">This event represents a USBX Host Class Prolific Reception Start Event.</span></span>

<span data-ttu-id="4e4bd-2247">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2247">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2248">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2248">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2249">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2249">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2250">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2250">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2251">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2251">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-reception-stop"></a><span data-ttu-id="4e4bd-2252">Paragem de receção prolífica classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2252">Host Class Prolific Reception Stop</span></span> 

#### <a name="ux_host_class_prolific_reception_stop"></a><span data-ttu-id="4e4bd-2253">ux_host_class_prolific_reception_stop</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2253">ux_host_class_prolific_reception_stop</span></span>

<span data-ttu-id="4e4bd-2254">**Ícone** ![ Ícone de paragem de receção prolific de classe de anfitrião](./media/user-guide/usbx-events/image172.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2254">**Icon** ![Host Class Prolific Reception Stop icon](./media/user-guide/usbx-events/image172.png)</span></span>

<span data-ttu-id="4e4bd-2255">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2255">**Description**</span></span>

<span data-ttu-id="4e4bd-2256">Este evento representa um evento de paragem de receção prolific da classe USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2256">This event represents a USBX Host Class Prolific Reception Stop Event.</span></span>

<span data-ttu-id="4e4bd-2257">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2257">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2258">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2258">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2259">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2259">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2260">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2260">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2261">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2261">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-write"></a><span data-ttu-id="4e4bd-2262">Escrita Prolific classe anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2262">Host Class Prolific Write</span></span> 

#### <a name="ux_host_class_prolific_write"></a><span data-ttu-id="4e4bd-2263">ux_host_class_prolific_write</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2263">ux_host_class_prolific_write</span></span>

<span data-ttu-id="4e4bd-2264">**Ícone** ![ Ícone de escrita prolific classe de anfitrião](./media/user-guide/usbx-events/image173.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2264">**Icon** ![Host Class Prolific Write icon](./media/user-guide/usbx-events/image173.png)</span></span>

<span data-ttu-id="4e4bd-2265">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2265">**Description**</span></span>

<span data-ttu-id="4e4bd-2266">Este evento representa um evento de escrita prolific da classe usbx.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2266">This event represents a USBX Host Class Prolific Write Event.</span></span>

<span data-ttu-id="4e4bd-2267">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2267">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2268">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2268">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2269">Info Field 2: Ponteiro de dados.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2269">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="4e4bd-2270">Info Field 3: Comprimento solicitado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2270">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="4e4bd-2271">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2271">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-activate"></a><span data-ttu-id="4e4bd-2272">Ativar o armazenamento da classe do anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2272">Host Class Storage Activate</span></span> 

#### <a name="ux_host_class_storage_activate"></a><span data-ttu-id="4e4bd-2273">ux_host_class_storage_activate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2273">ux_host_class_storage_activate</span></span>

<span data-ttu-id="4e4bd-2274">**Ícone** ![ Ícone ativar o armazenamento da classe do anfitrião](./media/user-guide/usbx-events/image174.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2274">**Icon** ![Host Class Storage Activate icon](./media/user-guide/usbx-events/image174.png)</span></span>

<span data-ttu-id="4e4bd-2275">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2275">**Description**</span></span>

<span data-ttu-id="4e4bd-2276">Este evento representa um evento USBX Host Class Storage Activate.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2276">This event represents a USBX Host Class Storage Activate Event.</span></span>

<span data-ttu-id="4e4bd-2277">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2277">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2278">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2278">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2279">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2279">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2280">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2280">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2281">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2281">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-deactivate"></a><span data-ttu-id="4e4bd-2282">Armazenamento de classe de anfitrião desativado</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2282">Host Class Storage Deactivate</span></span> 

#### <a name="ux_host_class_storage_deactivate"></a><span data-ttu-id="4e4bd-2283">ux_host_class_storage_deactivate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2283">ux_host_class_storage_deactivate</span></span>

<span data-ttu-id="4e4bd-2284">**Ícone** ![ Ícone de desativação de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image175.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2284">**Icon** ![Host Class Storage Deactivate icon](./media/user-guide/usbx-events/image175.png)</span></span>

<span data-ttu-id="4e4bd-2285">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2285">**Description**</span></span>

<span data-ttu-id="4e4bd-2286">Este evento representa um evento de desativação da classe de anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2286">This event represents a USBX Host Class Storage Deactivate Event.</span></span>

<span data-ttu-id="4e4bd-2287">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2287">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2288">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2288">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2289">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2289">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2290">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2290">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2291">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2291">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-capacity-get"></a><span data-ttu-id="4e4bd-2292">Capacidade de mídia de armazenamento de classe de anfitrião obter</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2292">Host Class Storage Media Capacity Get</span></span> 

#### <a name="ux_host_class_storage_media_capacity_get"></a><span data-ttu-id="4e4bd-2293">ux_host_class_storage_media_capacity_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2293">ux_host_class_storage_media_capacity_get</span></span>

<span data-ttu-id="4e4bd-2294">**Ícone** ![ Classe anfitrião armazenamento capacidade de mídia obter ícone](./media/user-guide/usbx-events/image176.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2294">**Icon** ![Host Class Storage Media Capacity Get icon](./media/user-guide/usbx-events/image176.png)</span></span>

<span data-ttu-id="4e4bd-2295">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2295">**Description**</span></span>

<span data-ttu-id="4e4bd-2296">Este evento representa um evento USBX Host Class Storage Media Capacity Get.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2296">This event represents a USBX Host Class Storage Media Capacity Get Event.</span></span>

<span data-ttu-id="4e4bd-2297">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2297">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2298">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2298">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2299">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2299">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2300">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2300">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2301">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2301">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-format-capacity-get"></a><span data-ttu-id="4e4bd-2302">Capacidade de formato de mídia de armazenamento de classe de anfitrião obter</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2302">Host Class Storage Media Format Capacity Get</span></span>

#### <a name="ux_host_class_storage_media_format_capacity_get"></a><span data-ttu-id="4e4bd-2303">ux_host_class_storage_media_format_capacity_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2303">ux_host_class_storage_media_format_capacity_get</span></span>

<span data-ttu-id="4e4bd-2304">**Ícone** ![ Grupo de anfitrião armazenamento de armazenamento de capacidade obter ícone](./media/user-guide/usbx-events/image177.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2304">**Icon** ![Host Class Storage Media Format Capacity Get icon](./media/user-guide/usbx-events/image177.png)</span></span>

<span data-ttu-id="4e4bd-2305">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2305">**Description**</span></span>

<span data-ttu-id="4e4bd-2306">Este evento representa um evento USBX Host Class Storage Media Formato Capacity Get.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2306">This event represents a USBX Host Class Storage Media Format Capacity Get Event.</span></span>

<span data-ttu-id="4e4bd-2307">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2307">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2308">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2308">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2309">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2309">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2310">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2310">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2311">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2311">Info Field 4: Not used.</span></span>

#### <a name="host-class-storage-media-mount"></a><span data-ttu-id="4e4bd-2312">Montagem de mídia de armazenamento de classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2312">Host Class Storage Media Mount</span></span> 

#### <a name="ux_host_class_storage_media_mount"></a><span data-ttu-id="4e4bd-2313">ux_host_class_storage_media_mount</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2313">ux_host_class_storage_media_mount</span></span>

<span data-ttu-id="4e4bd-2314">**Ícone** ![ Ícone de montagem de mídia de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image178.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2314">**Icon** ![Host Class Storage Media Mount icon](./media/user-guide/usbx-events/image178.png)</span></span>

<span data-ttu-id="4e4bd-2315">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2315">**Description**</span></span>

<span data-ttu-id="4e4bd-2316">Este evento representa um evento USBX Host Class Storage Media Mount.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2316">This event represents a USBX Host Class Storage Media Mount Event.</span></span>

<span data-ttu-id="4e4bd-2317">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2317">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2318">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2318">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2319">Info Field 2: Sector.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2319">Info Field 2: Sector.</span></span>
- <span data-ttu-id="4e4bd-2320">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2320">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2321">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2321">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-open"></a><span data-ttu-id="4e4bd-2322">Classe de anfitrião armazenamento mídia aberta</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2322">Host Class Storage Media Open</span></span> 

#### <a name="ux_host_class_storage_media_open"></a><span data-ttu-id="4e4bd-2323">ux_host_class_storage_media_open</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2323">ux_host_class_storage_media_open</span></span>

<span data-ttu-id="4e4bd-2324">**Ícone** ![ Ícone de mídia de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image179.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2324">**Icon** ![Host Class Storage Media Open icon](./media/user-guide/usbx-events/image179.png)</span></span>

<span data-ttu-id="4e4bd-2325">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2325">**Description**</span></span>

<span data-ttu-id="4e4bd-2326">Este evento representa um evento USBX Host Class Storage Media Open.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2326">This event represents a USBX Host Class Storage Media Open Event.</span></span>

<span data-ttu-id="4e4bd-2327">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2327">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2328">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2328">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2329">Info Field 2: Media.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2329">Info Field 2: Media.</span></span>
- <span data-ttu-id="4e4bd-2330">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2330">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2331">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2331">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-read"></a><span data-ttu-id="4e4bd-2332">Leitura de mídia de armazenamento de classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2332">Host Class Storage Media Read</span></span> 

#### <a name="ux_host_class_storage_media_read"></a><span data-ttu-id="4e4bd-2333">ux_host_class_storage_media_read</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2333">ux_host_class_storage_media_read</span></span>

<span data-ttu-id="4e4bd-2334">**Ícone** ![ Ícone de leitura de mídia de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image180.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2334">**Icon** ![Host Class Storage Media Read icon](./media/user-guide/usbx-events/image180.png)</span></span>

<span data-ttu-id="4e4bd-2335">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2335">**Description**</span></span>

<span data-ttu-id="4e4bd-2336">Este evento representa um evento usbx host Class Storage Media Read.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2336">This event represents a USBX Host Class Storage Media Read Event.</span></span>

<span data-ttu-id="4e4bd-2337">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2337">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2338">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2338">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2339">Info Field 2: Início do sector.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2339">Info Field 2: Sector start.</span></span>
- <span data-ttu-id="4e4bd-2340">Info Field 3: Contagem de sector.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2340">Info Field 3: Sector count.</span></span>
- <span data-ttu-id="4e4bd-2341">Info Field 4: Ponteiro de dados.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2341">Info Field 4: Data pointer.</span></span>

### <a name="host-class-storage-media-write"></a><span data-ttu-id="4e4bd-2342">Escrita de mídia de armazenamento de classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2342">Host Class Storage Media Write</span></span> 

#### <a name="ux_host_class_storage_media_write"></a><span data-ttu-id="4e4bd-2343">ux_host_class_storage_media_write</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2343">ux_host_class_storage_media_write</span></span>

<span data-ttu-id="4e4bd-2344">**Ícone** ![ Ícone de mídia de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image181.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2344">**Icon** ![Host Class Storage Media Write icon](./media/user-guide/usbx-events/image181.png)</span></span>

<span data-ttu-id="4e4bd-2345">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2345">**Description**</span></span>

<span data-ttu-id="4e4bd-2346">Este evento representa um evento usbx host Class Storage Media Write.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2346">This event represents a USBX Host Class Storage Media Write Event.</span></span>

<span data-ttu-id="4e4bd-2347">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2347">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2348">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2348">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2349">Info Field 2: Início do sector.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2349">Info Field 2: Sector start.</span></span>
- <span data-ttu-id="4e4bd-2350">Info Field 3: Contagem de sector.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2350">Info Field 3: Sector count.</span></span>
- <span data-ttu-id="4e4bd-2351">Info Field 4: Ponteiro de dados.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2351">Info Field 4: Data pointer.</span></span>

### <a name="host-class-storage-request-sense"></a><span data-ttu-id="4e4bd-2352">Sentido do pedido de armazenamento de classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2352">Host Class Storage Request Sense</span></span> 

#### <a name="ux_host_class_storage_request_sense"></a><span data-ttu-id="4e4bd-2353">ux_host_class_storage_request_sense</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2353">ux_host_class_storage_request_sense</span></span>

<span data-ttu-id="4e4bd-2354">**Ícone** ![ Ícone de pedido de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image182.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2354">**Icon** ![Host Class Storage Request Sense icon](./media/user-guide/usbx-events/image182.png)</span></span>

<span data-ttu-id="4e4bd-2355">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2355">**Description**</span></span>

<span data-ttu-id="4e4bd-2356">Este evento representa um evento usbx host Class Storage Sense Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2356">This event represents a USBX Host Class Storage Request Sense Event.</span></span>

<span data-ttu-id="4e4bd-2357">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2357">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2358">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2358">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2359">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2359">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2360">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2360">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2361">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2361">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-start-stop"></a><span data-ttu-id="4e4bd-2362">Paragem de início de armazenamento de classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2362">Host Class Storage Start Stop</span></span> 

#### <a name="ux_host_class_storage_start_stop"></a><span data-ttu-id="4e4bd-2363">ux_host_class_storage_start_stop</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2363">ux_host_class_storage_start_stop</span></span>

<span data-ttu-id="4e4bd-2364">**Ícone** ![ Ícone de paragem de início de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image183.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2364">**Icon** ![Host Class Storage Start Stop icon](./media/user-guide/usbx-events/image183.png)</span></span>

<span data-ttu-id="4e4bd-2365">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2365">**Description**</span></span>

<span data-ttu-id="4e4bd-2366">Este evento representa um evento de paragem de início de armazenamento de classe usbx.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2366">This event represents a USBX Host Class Storage Start Stop Event.</span></span>

<span data-ttu-id="4e4bd-2367">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2367">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2368">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2368">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2369">Info Campo 2: Sinal de paragem de início.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2369">Info Field 2: Start stop signal.</span></span>
- <span data-ttu-id="4e4bd-2370">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2370">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2371">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2371">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-unit-ready-test"></a><span data-ttu-id="4e4bd-2372">Teste pronto da unidade de armazenamento da classe de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2372">Host Class Storage Unit Ready Test</span></span> 

#### <a name="ux_host_class_storage_unit_ready_test"></a><span data-ttu-id="4e4bd-2373">ux_host_class_storage_unit_ready_test</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2373">ux_host_class_storage_unit_ready_test</span></span>

<span data-ttu-id="4e4bd-2374">**Ícone** ![ Ícone de teste pronto da unidade de armazenamento da classe do anfitrião](./media/user-guide/usbx-events/image184.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2374">**Icon** ![Host Class Storage Unit Ready Test icon](./media/user-guide/usbx-events/image184.png)</span></span>

<span data-ttu-id="4e4bd-2375">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2375">**Description**</span></span>

<span data-ttu-id="4e4bd-2376">Este evento representa um evento de teste pronto da unidade de armazenamento da classe USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2376">This event represents a USBX Host Class Storage Unit Ready Test Event.</span></span>

<span data-ttu-id="4e4bd-2377">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2377">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2378">Info Field 1: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2378">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="4e4bd-2379">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2379">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2380">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2380">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2381">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2381">Info Field 4: Not used.</span></span>

### <a name="host-stack-class-instance-create"></a><span data-ttu-id="4e4bd-2382">Série de anfitrião classe de classe criar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2382">Host Stack Class Instance Create</span></span> 

#### <a name="ux_host_class_instance_create"></a><span data-ttu-id="4e4bd-2383">ux_host_class_instance_create</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2383">ux_host_class_instance_create</span></span>

<span data-ttu-id="4e4bd-2384">**Ícone** ![ Série de anfitrião exemplo criar ícone](./media/user-guide/usbx-events/image185.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2384">**Icon** ![Host Stack Class Instance Create icon](./media/user-guide/usbx-events/image185.png)</span></span>

<span data-ttu-id="4e4bd-2385">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2385">**Description**</span></span>

<span data-ttu-id="4e4bd-2386">Este evento representa um evento de série de série de anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2386">This event represents a USBX Host Stack Class Instance Create Event.</span></span>

<span data-ttu-id="4e4bd-2387">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2387">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2388">Info Field 1: Classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2388">Info Field 1: Class.</span></span>
- <span data-ttu-id="4e4bd-2389">Info Field 2: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2389">Info Field 2: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-2390">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2390">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2391">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2391">Info Field 4: Not used.</span></span>

### <a name="host-stack-class-instance-destroy"></a><span data-ttu-id="4e4bd-2392">Exemplo de classe de pilha de anfitrião destruir</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2392">Host Stack Class Instance Destroy</span></span> 

#### <a name="ux_host_class_instance_create"></a><span data-ttu-id="4e4bd-2393">ux_host_class_instance_create</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2393">ux_host_class_instance_create</span></span>

<span data-ttu-id="4e4bd-2394">**Ícone** ![ Ícone de destruição de classe de classe de pilha de anfitrião](./media/user-guide/usbx-events/image186.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2394">**Icon** ![Host Stack Class Instance Destroy icon](./media/user-guide/usbx-events/image186.png)</span></span>

<span data-ttu-id="4e4bd-2395">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2395">**Description**</span></span>

<span data-ttu-id="4e4bd-2396">Este evento representa um evento de destruição de classe de série de anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2396">This event represents a USBX Host Stack Class Instance Destroy Event.</span></span>

<span data-ttu-id="4e4bd-2397">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2397">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2398">Info Field 1: Classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2398">Info Field 1: Class.</span></span>
- <span data-ttu-id="4e4bd-2399">Info Field 2: Exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2399">Info Field 2: Class Instance.</span></span>
- <span data-ttu-id="4e4bd-2400">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2400">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2401">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2401">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-delete"></a><span data-ttu-id="4e4bd-2402">Configuração de pilha de anfitrião Eliminar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2402">Host Stack Configuration Delete</span></span> 

#### <a name="ux_host_class_configuration_delete"></a><span data-ttu-id="4e4bd-2403">ux_host_class_configuration_delete</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2403">ux_host_class_configuration_delete</span></span>

<span data-ttu-id="4e4bd-2404">**Ícone** ![ Ícone de configuração de pilha de anfitrião Eliminar](./media/user-guide/usbx-events/image187.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2404">**Icon** ![Host Stack Configuration Delete icon](./media/user-guide/usbx-events/image187.png)</span></span>

<span data-ttu-id="4e4bd-2405">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2405">**Description**</span></span>

<span data-ttu-id="4e4bd-2406">Este evento representa um evento de eliminação da configuração da pilha de anfitriões USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2406">This event represents a USBX Host Stack Configuration Delete Event.</span></span>

<span data-ttu-id="4e4bd-2407">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2407">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2408">Info Field 1: Configuração.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2408">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="4e4bd-2409">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2409">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2410">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2410">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2411">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2411">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-enumerate"></a><span data-ttu-id="4e4bd-2412">Enumerar a configuração da pilha de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2412">Host Stack Configuration Enumerate</span></span> 

#### <a name="ux_host_stack_configuration_enumerate"></a><span data-ttu-id="4e4bd-2413">ux_host_stack_configuration_enumerate</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2413">ux_host_stack_configuration_enumerate</span></span>

<span data-ttu-id="4e4bd-2414">**Ícone** ![ Ícone de enumeração de configuração de pilha de anfitrião](./media/user-guide/usbx-events/image188.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2414">**Icon** ![Host Stack Configuration Enumerate icon](./media/user-guide/usbx-events/image188.png)</span></span>

<span data-ttu-id="4e4bd-2415">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2415">**Description**</span></span>

<span data-ttu-id="4e4bd-2416">Este evento representa um evento de configuração de configuração de pilha de anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2416">This event represents a USBX Host Stack Configuration Enumerate Event.</span></span>

<span data-ttu-id="4e4bd-2417">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2417">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2418">Info Field 1: Dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2418">Info Field 1: Device.</span></span>
- <span data-ttu-id="4e4bd-2419">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2419">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2420">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2420">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2421">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2421">Info Field 4: Not used.</span></span>

### <a name="stack-configuration-instance-create"></a><span data-ttu-id="4e4bd-2422">Criar exemplos de configuração de pilha</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2422">Stack Configuration Instance Create</span></span> 

#### <a name="ux_host_stack_configuration_instance_create"></a><span data-ttu-id="4e4bd-2423">ux_host_stack_configuration_instance_create</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2423">ux_host_stack_configuration_instance_create</span></span>

<span data-ttu-id="4e4bd-2424">**Ícone** ![ Exemplo de configuração de pilha Criar ícone](./media/user-guide/usbx-events/image189.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2424">**Icon** ![Stack Configuration Instance Create icon](./media/user-guide/usbx-events/image189.png)</span></span>

<span data-ttu-id="4e4bd-2425">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2425">**Description**</span></span>

<span data-ttu-id="4e4bd-2426">Este evento representa um evento de configuração de configuração de pilha de anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2426">This event represents a USBX Host Stack Configuration Instance Create Event.</span></span>

<span data-ttu-id="4e4bd-2427">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2427">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2428">Info Field 1: Configuração.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2428">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="4e4bd-2429">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2429">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2430">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2430">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2431">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2431">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-instance-delete"></a><span data-ttu-id="4e4bd-2432">Excluir a configuração da configuração da pilha do anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2432">Host Stack Configuration Instance Delete</span></span> 

#### <a name="ux_host_stack_configuration_instance_delete"></a><span data-ttu-id="4e4bd-2433">ux_host_stack_configuration_instance_delete</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2433">ux_host_stack_configuration_instance_delete</span></span>

<span data-ttu-id="4e4bd-2434">**Ícone** ![ Exemplo de configuração de pilha de anfitrião Eliminar ícone](./media/user-guide/usbx-events/image190.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2434">**Icon** ![Host Stack Configuration Instance Delete icon](./media/user-guide/usbx-events/image190.png)</span></span>

<span data-ttu-id="4e4bd-2435">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2435">**Description**</span></span>

<span data-ttu-id="4e4bd-2436">Este evento representa um evento de configuração de configuração de pilha de anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2436">This event represents a USBX Host Stack Configuration Instance Delete Event.</span></span>

<span data-ttu-id="4e4bd-2437">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2437">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2438">Info Field 1: Configuração.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2438">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="4e4bd-2439">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2439">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2440">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2440">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2441">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2441">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-set"></a><span data-ttu-id="4e4bd-2442">Conjunto de configuração de pilha de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2442">Host Stack Configuration Set</span></span> 

#### <a name="ux_host_stack_configuration_set"></a><span data-ttu-id="4e4bd-2443">ux_host_stack_configuration_set</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2443">ux_host_stack_configuration_set</span></span>

<span data-ttu-id="4e4bd-2444">**Ícone** ![ Ícone de conjunto de configuração de pilha de anfitrião](./media/user-guide/usbx-events/image191.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2444">**Icon** ![Host Stack Configuration Set icon](./media/user-guide/usbx-events/image191.png)</span></span>

<span data-ttu-id="4e4bd-2445">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2445">**Description**</span></span>

<span data-ttu-id="4e4bd-2446">Este evento representa um evento usbx host Stack Configuration set Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2446">This event represents a USBX Host Stack Configuration Set Event.</span></span>

<span data-ttu-id="4e4bd-2447">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2447">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2448">Info Field 1: Configuração.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2448">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="4e4bd-2449">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2449">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2450">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2450">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2451">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2451">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-address-set"></a><span data-ttu-id="4e4bd-2452">Conjunto de endereço de dispositivo de pilha de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2452">Host Stack Device Address Set</span></span> 

#### <a name="ux_host_stack_device_address_set"></a><span data-ttu-id="4e4bd-2453">ux_host_stack_device_address_set</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2453">ux_host_stack_device_address_set</span></span>

<span data-ttu-id="4e4bd-2454">**Ícone** ![ Ícone de conjunto de endereço de dispositivo de pilha de anfitrião](./media/user-guide/usbx-events/image192.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2454">**Icon** ![Host Stack Device Address Set icon](./media/user-guide/usbx-events/image192.png)</span></span>

<span data-ttu-id="4e4bd-2455">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2455">**Description**</span></span>

<span data-ttu-id="4e4bd-2456">Este evento representa um evento usbx host Stack Device Address set.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2456">This event represents a USBX Host Stack Device Address Set Event.</span></span>

<span data-ttu-id="4e4bd-2457">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2457">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2458">Info Field 1: Dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2458">Info Field 1: Device.</span></span>
- <span data-ttu-id="4e4bd-2459">Info Field 2: Endereço do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2459">Info Field 2: Device Address.</span></span>
- <span data-ttu-id="4e4bd-2460">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2460">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2461">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2461">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-configuration-get"></a><span data-ttu-id="4e4bd-2462">Configuração do dispositivo de pilha de anfitrião obter</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2462">Host Stack Device Configuration Get</span></span> 

#### <a name="ux_host_stack_device_configuration_get"></a><span data-ttu-id="4e4bd-2463">ux_host_stack_device_configuration_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2463">ux_host_stack_device_configuration_get</span></span>

<span data-ttu-id="4e4bd-2464">**Ícone** ![ Configuração do dispositivo de pilha de anfitrião Obter ícone](./media/user-guide/usbx-events/image193.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2464">**Icon** ![Host Stack Device Configuration Get icon](./media/user-guide/usbx-events/image193.png)</span></span>

<span data-ttu-id="4e4bd-2465">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2465">**Description**</span></span>

<span data-ttu-id="4e4bd-2466">Este evento representa um evento de configuração do dispositivo de pilha de anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2466">This event represents a USBX Host Stack Device Configuration Get Event.</span></span>

<span data-ttu-id="4e4bd-2467">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2467">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2468">Info Field 1: Dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2468">Info Field 1: Device.</span></span>
- <span data-ttu-id="4e4bd-2469">nfo Field 2: Configuração.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2469">nfo Field 2: Configuration.</span></span>
- <span data-ttu-id="4e4bd-2470">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2470">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2471">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2471">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-configuration-select"></a><span data-ttu-id="4e4bd-2472">Selecione de configuração do dispositivo de pilha de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2472">Host Stack Device Configuration Select</span></span> 

#### <a name="ux_host_stack_device_configuration_select"></a><span data-ttu-id="4e4bd-2473">ux_host_stack_device_configuration_select</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2473">ux_host_stack_device_configuration_select</span></span>

<span data-ttu-id="4e4bd-2474">**Ícone** ![ Ícone de configuração do dispositivo de pilha de anfitrião](./media/user-guide/usbx-events/image194.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2474">**Icon** ![Host Stack Device Configuration Select icon](./media/user-guide/usbx-events/image194.png)</span></span>

<span data-ttu-id="4e4bd-2475">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2475">**Description**</span></span>

<span data-ttu-id="4e4bd-2476">Este evento representa um evento de configuração do dispositivo de pilha de anfitriões USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2476">This event represents a USBX Host Stack Device Configuration Select Event.</span></span>

<span data-ttu-id="4e4bd-2477">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2477">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2478">Info Field 1: Dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2478">Info Field 1: Device.</span></span>
- <span data-ttu-id="4e4bd-2479">Info Field 2: Configuração.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2479">Info Field 2: Configuration.</span></span>
- <span data-ttu-id="4e4bd-2480">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2480">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2481">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2481">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-descriptor-read"></a><span data-ttu-id="4e4bd-2482">Leitura do descritor do dispositivo de pilha de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2482">Host Stack Device Descriptor Read</span></span> 

#### <a name="ux_host_stack_device_descriptor_read"></a><span data-ttu-id="4e4bd-2483">ux_host_stack_device_descriptor_read</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2483">ux_host_stack_device_descriptor_read</span></span>

<span data-ttu-id="4e4bd-2484">**Ícone** ![ Ícone de leitura de dispositivo de pilha de anfitrião](./media/user-guide/usbx-events/image195.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2484">**Icon** ![Host Stack Device Descriptor Read icon](./media/user-guide/usbx-events/image195.png)</span></span>

<span data-ttu-id="4e4bd-2485">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2485">**Description**</span></span>

<span data-ttu-id="4e4bd-2486">Este evento representa um evento de leitura do dispositivo de pilha de anfitriões USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2486">This event represents a USBX Host Stack Device Descriptor Read Event.</span></span>

<span data-ttu-id="4e4bd-2487">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2487">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2488">Info Field 1: Dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2488">Info Field 1: Device.</span></span>
- <span data-ttu-id="4e4bd-2489">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2489">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2490">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2490">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2491">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2491">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-get"></a><span data-ttu-id="4e4bd-2492">Dispositivo de pilha de anfitrião obter</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2492">Host Stack Device Get</span></span> 

#### <a name="ux_host_stack_device_get"></a><span data-ttu-id="4e4bd-2493">ux_host_stack_device_get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2493">ux_host_stack_device_get</span></span>

<span data-ttu-id="4e4bd-2494">**Ícone** ![ Dispositivo de pilha de anfitrião obter ícone](./media/user-guide/usbx-events/image196.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2494">**Icon** ![Host Stack Device Get icon](./media/user-guide/usbx-events/image196.png)</span></span>

<span data-ttu-id="4e4bd-2495">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2495">**Description**</span></span>

<span data-ttu-id="4e4bd-2496">Este evento representa um evento usbx host Stack Device Get.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2496">This event represents a USBX Host Stack Device Get Event.</span></span>

<span data-ttu-id="4e4bd-2497">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2497">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2498">Info Field 1: Índice de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2498">Info Field 1: Device index.</span></span>
- <span data-ttu-id="4e4bd-2499">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2499">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2500">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2500">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2501">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2501">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-remove"></a><span data-ttu-id="4e4bd-2502">Remover dispositivo de pilha de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2502">Host Stack Device Remove</span></span> 

#### <a name="ux_host_stack_device_remove"></a><span data-ttu-id="4e4bd-2503">ux_host_stack_device_remove</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2503">ux_host_stack_device_remove</span></span>

<span data-ttu-id="4e4bd-2504">**Ícone** ![ Ícone de remover dispositivo de pilha de anfitrião](./media/user-guide/usbx-events/image197.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2504">**Icon** ![Host Stack Device Remove icon](./media/user-guide/usbx-events/image197.png)</span></span>

<span data-ttu-id="4e4bd-2505">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2505">**Description**</span></span>

<span data-ttu-id="4e4bd-2506">Este evento representa um evento de remoção do dispositivo de stack do anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2506">This event represents a USBX Host Stack Device Remove Event.</span></span>

<span data-ttu-id="4e4bd-2507">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2507">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2508">Info Field 1: Hcd.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2508">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="4e4bd-2509">Info Field 2: Pai.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2509">Info Field 2: Parent.</span></span>
- <span data-ttu-id="4e4bd-2510">Info Field 3: Índice de Porta.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2510">Info Field 3: Port Index.</span></span>
- <span data-ttu-id="4e4bd-2511">Info Field 4: Dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2511">Info Field 4: Device.</span></span>

### <a name="host-stack-device-resource-free"></a><span data-ttu-id="4e4bd-2512">Dispositivo de pilha de anfitrião livre</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2512">Host Stack Device Resource Free</span></span> 

#### <a name="ux_host_stack_device_resource_free"></a><span data-ttu-id="4e4bd-2513">ux_host_stack_device_resource_free</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2513">ux_host_stack_device_resource_free</span></span>

<span data-ttu-id="4e4bd-2514">**Ícone** ![ Ícone livre de recursos do dispositivo de pilha de anfitrião](./media/user-guide/usbx-events/image198.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2514">**Icon** ![Host Stack Device Resource Free icon](./media/user-guide/usbx-events/image198.png)</span></span>

<span data-ttu-id="4e4bd-2515">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2515">**Description**</span></span>

<span data-ttu-id="4e4bd-2516">Este evento representa um evento gratuito de recursos do dispositivo usbx host Stack.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2516">This event represents a USBX Host Stack Device Resource Free Event.</span></span>

<span data-ttu-id="4e4bd-2517">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2517">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2518">Info Field 1: Dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2518">Info Field 1: Device.</span></span>
- <span data-ttu-id="4e4bd-2519">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2519">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2520">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2520">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2521">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2521">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-instance-create"></a><span data-ttu-id="4e4bd-2522">Host Stack Endpoint Instance Create</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2522">Host Stack Endpoint Instance Create</span></span> 

#### <a name="ux_host_stack_endpoint_instance_create"></a><span data-ttu-id="4e4bd-2523">ux_host_stack_endpoint_instance_create</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2523">ux_host_stack_endpoint_instance_create</span></span>

<span data-ttu-id="4e4bd-2524">**Ícone** ![ Exemplo de ponto final de pilha de anfitrião Criar ícone](./media/user-guide/usbx-events/image199.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2524">**Icon** ![Host Stack Endpoint Instance Create icon](./media/user-guide/usbx-events/image199.png)</span></span>

<span data-ttu-id="4e4bd-2525">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2525">**Description**</span></span>

<span data-ttu-id="4e4bd-2526">Este evento representa um evento de endpoint de série de anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2526">This event represents a USBX Host Stack Endpoint Instance Create Event.</span></span>

<span data-ttu-id="4e4bd-2527">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2527">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2528">Info Field 1: Dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2528">Info Field 1: Device.</span></span>
- <span data-ttu-id="4e4bd-2529">Info Field 2: Ponto final.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2529">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4e4bd-2530">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2530">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2531">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2531">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-instance-delete"></a><span data-ttu-id="4e4bd-2532">Exemplo de ponto final de pilha de anfitrião Eliminar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2532">Host Stack Endpoint Instance Delete</span></span> 

#### <a name="ux_host_stack_endpoint_instance_delete"></a><span data-ttu-id="4e4bd-2533">ux_host_stack_endpoint_instance_delete</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2533">ux_host_stack_endpoint_instance_delete</span></span>

<span data-ttu-id="4e4bd-2534">**Ícone** ![ Exemplo de endpoint de pilha de anfitrião Eliminar ícone](./media/user-guide/usbx-events/image200.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2534">**Icon** ![Host Stack Endpoint Instance Delete icon](./media/user-guide/usbx-events/image200.png)</span></span>

<span data-ttu-id="4e4bd-2535">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2535">**Description**</span></span>

<span data-ttu-id="4e4bd-2536">Este evento representa um evento de eliminação de exemplo de série de anfitriões USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2536">This event represents a USBX Host Stack Endpoint Instance Delete Event.</span></span>

<span data-ttu-id="4e4bd-2537">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2537">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2538">Info Field 2: Ponto final.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2538">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4e4bd-2539">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2539">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2540">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2540">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-reset"></a><span data-ttu-id="4e4bd-2541">Reset do ponto final do ponto final da pilha de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2541">Host Stack Endpoint Reset</span></span> 

#### <a name="ux_host_stack_endpoint_reset"></a><span data-ttu-id="4e4bd-2542">ux_host_stack_endpoint_reset</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2542">ux_host_stack_endpoint_reset</span></span>

<span data-ttu-id="4e4bd-2543">**Ícone** ![ Ícone de reset do ponto final do host Stack](./media/user-guide/usbx-events/image201.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2543">**Icon** ![Host Stack Endpoint Reset icon](./media/user-guide/usbx-events/image201.png)</span></span>

<span data-ttu-id="4e4bd-2544">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2544">**Description**</span></span>

<span data-ttu-id="4e4bd-2545">Este evento representa um evento de reset do ponto final da stack do anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2545">This event represents a USBX Host Stack Endpoint Reset Event.</span></span>

<span data-ttu-id="4e4bd-2546">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2546">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2547">Info Field 1: Dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2547">Info Field 1: Device.</span></span>
- <span data-ttu-id="4e4bd-2548">Info Field 2: Ponto final.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2548">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4e4bd-2549">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2549">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2550">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2550">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-transfer-abort"></a><span data-ttu-id="4e4bd-2551">Abortar a transferência de ponto final do host Stack</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2551">Host Stack Endpoint Transfer Abort</span></span> 

#### <a name="ux_host_stack_endpoint_transfer_abort"></a><span data-ttu-id="4e4bd-2552">ux_host_stack_endpoint_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2552">ux_host_stack_endpoint_transfer_abort</span></span>

<span data-ttu-id="4e4bd-2553">**Ícone** ![ Ícone de aborto de transferência de ponto final de pilha de anfitrião](./media/user-guide/usbx-events/image202.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2553">**Icon** ![Host Stack Endpoint Transfer Abort icon](./media/user-guide/usbx-events/image202.png)</span></span>

<span data-ttu-id="4e4bd-2554">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2554">**Description**</span></span>

<span data-ttu-id="4e4bd-2555">Este evento representa um evento usbx host Stack Endpoint Transfer Abort.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2555">This event represents a USBX Host Stack Endpoint Transfer Abort Event.</span></span>

<span data-ttu-id="4e4bd-2556">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2556">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2557">Info Field 1: Ponto final.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2557">Info Field 1: Endpoint.</span></span>
- <span data-ttu-id="4e4bd-2558">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2558">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2559">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2559">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2560">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2560">Info Field 4: Not used.</span></span>

### <a name="host-stack-host-controller-register"></a><span data-ttu-id="4e4bd-2561">Registo do controlador do anfitrião do anfitrião da pilha</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2561">Host Stack Host Controller Register</span></span> 

#### <a name="ux_host_stack_hcd_register"></a><span data-ttu-id="4e4bd-2562">ux_host_stack_hcd_register</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2562">ux_host_stack_hcd_register</span></span>

<span data-ttu-id="4e4bd-2563">**Ícone** ![ Ícone do controlador do anfitrião do anfitrião do anfitrião](./media/user-guide/usbx-events/image203.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2563">**Icon** ![Host Stack Host Controller Register icon](./media/user-guide/usbx-events/image203.png)</span></span>

<span data-ttu-id="4e4bd-2564">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2564">**Description**</span></span>

<span data-ttu-id="4e4bd-2565">Este evento representa um registo do controlador anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2565">This event represents a USBX Host Stack Host Controller Register.</span></span>

<span data-ttu-id="4e4bd-2566">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2566">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2567">Info Field 1: Nome HCD.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2567">Info Field 1: Hcd Name.</span></span>
- <span data-ttu-id="4e4bd-2568">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2568">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2569">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2569">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2570">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2570">Info Field 4: Not used.</span></span>

### <a name="host-stack-initialize"></a><span data-ttu-id="4e4bd-2571">Inicialize da Pilha de Anfitriões</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2571">Host Stack Initialize</span></span> 

#### <a name="ux_host_stack_initialize"></a><span data-ttu-id="4e4bd-2572">ux_host_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2572">ux_host_stack_initialize</span></span>

<span data-ttu-id="4e4bd-2573">**Ícone** ![ Ícone inicialize da pilha de anfitrião](./media/user-guide/usbx-events/image204.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2573">**Icon** ![Host Stack Initialize icon](./media/user-guide/usbx-events/image204.png)</span></span>

<span data-ttu-id="4e4bd-2574">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2574">**Description**</span></span>

<span data-ttu-id="4e4bd-2575">Este evento representa um evento usbx host Stack Initialize Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2575">This event represents a USBX Host Stack Initialize Event.</span></span>

<span data-ttu-id="4e4bd-2576">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2576">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2577">Info Field 1: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2577">Info Field 1: Not used.</span></span>
- <span data-ttu-id="4e4bd-2578">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2578">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2579">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2579">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2580">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2580">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-endpoint-get"></a><span data-ttu-id="4e4bd-2581">Host Stack Interface Endpoint Get</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2581">Host Stack Interface Endpoint Get</span></span> 

#### <a name="interface_-tcp-retry-entry"></a><span data-ttu-id="4e4bd-2582">Interface_ TCP relemca a entrada</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2582">Interface_ TCP retry entry</span></span>

<span data-ttu-id="4e4bd-2583">**Ícone** ![ Anfitrião Stack Interface Endpoint Obter ícone](./media/user-guide/usbx-events/image205.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2583">**Icon** ![Host Stack Interface Endpoint Get icon](./media/user-guide/usbx-events/image205.png)</span></span>

<span data-ttu-id="4e4bd-2584">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2584">**Description**</span></span>

<span data-ttu-id="4e4bd-2585">Este evento representa um evento interno de relemistenção netx TCP.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2585">This event represents an internal NetX TCP retry event.</span></span>

<span data-ttu-id="4e4bd-2586">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2586">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2587">Info Field 1: Interface.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2587">Info Field 1: Interface.</span></span>
- <span data-ttu-id="4e4bd-2588">Info Field 2: Índice de ponto final.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2588">Info Field 2: Endpoint index.</span></span>
- <span data-ttu-id="4e4bd-2589">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2589">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2590">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2590">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-instance-create"></a><span data-ttu-id="4e4bd-2591">Série de série de anfitrião criar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2591">Host Stack Interface Instance Create</span></span> 

#### <a name="ux_host_stack_interface_instance_create"></a><span data-ttu-id="4e4bd-2592">ux_host_stack_interface_instance_create</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2592">ux_host_stack_interface_instance_create</span></span>

<span data-ttu-id="4e4bd-2593">**Ícone** ![ Exemplo de interface de pilha de anfitrião Criar ícone](./media/user-guide/usbx-events/image206.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2593">**Icon** ![Host Stack Interface Instance Create icon](./media/user-guide/usbx-events/image206.png)</span></span>

<span data-ttu-id="4e4bd-2594">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2594">**Description**</span></span>

<span data-ttu-id="4e4bd-2595">Este evento representa um evento de interface de série de anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2595">This event represents a USBX Host Stack Interface Instance Create Event.</span></span>

<span data-ttu-id="4e4bd-2596">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2596">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2597">Info Field 1: Interface.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2597">Info Field 1: Interface.</span></span>
- <span data-ttu-id="4e4bd-2598">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2598">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2599">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2599">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2600">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2600">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-instance-delete"></a><span data-ttu-id="4e4bd-2601">Excluir a interface da interface da pilha do anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2601">Host Stack Interface Instance Delete</span></span> 

#### <a name="ux_host_stack_interface_instance_delete"></a><span data-ttu-id="4e4bd-2602">ux_host_stack_interface_instance_delete</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2602">ux_host_stack_interface_instance_delete</span></span>

<span data-ttu-id="4e4bd-2603">**Ícone** ![ Exemplo de interface de pilha de anfitrião Eliminar ícone](./media/user-guide/usbx-events/image207.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2603">**Icon** ![Host Stack Interface Instance Delete icon](./media/user-guide/usbx-events/image207.png)</span></span>

<span data-ttu-id="4e4bd-2604">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2604">**Description**</span></span>

<span data-ttu-id="4e4bd-2605">Este evento representa um evento de eliminação de instância de interface de anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2605">This event represents a USBX Host Stack Interface Instance Delete Event.</span></span>

<span data-ttu-id="4e4bd-2606">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2606">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2607">Info Field 1: Interface.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2607">Info Field 1: Interface.</span></span>
- <span data-ttu-id="4e4bd-2608">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2608">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2609">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2609">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2610">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2610">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-set"></a><span data-ttu-id="4e4bd-2611">Conjunto de interface de pilha de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2611">Host Stack Interface Set</span></span> 

#### <a name="ux_host_stack_interface_set"></a><span data-ttu-id="4e4bd-2612">ux_host_stack_interface_set</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2612">ux_host_stack_interface_set</span></span>

<span data-ttu-id="4e4bd-2613">**Ícone** ![ Ícone de conjunto de interface de pilha de anfitrião](./media/user-guide/usbx-events/image208.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2613">**Icon** ![Host Stack Interface Set icon](./media/user-guide/usbx-events/image208.png)</span></span>

<span data-ttu-id="4e4bd-2614">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2614">**Description**</span></span>

<span data-ttu-id="4e4bd-2615">Este evento representa um evento USBX Host Stack Interface set.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2615">This event represents a USBX Host Stack Interface Set Event.</span></span>

<span data-ttu-id="4e4bd-2616">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2616">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2617">Info Field 1: Interface.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2617">Info Field 1: Interface.</span></span>
- <span data-ttu-id="4e4bd-2618">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2618">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2619">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2619">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2620">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2620">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-setting-select"></a><span data-ttu-id="4e4bd-2621">Selecione de definição de interface de pilha de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2621">Host Stack Interface Setting Select</span></span> 

#### <a name="ux_host_stack_interface_setting_select"></a><span data-ttu-id="4e4bd-2622">ux_host_stack_interface_setting_select</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2622">ux_host_stack_interface_setting_select</span></span>

<span data-ttu-id="4e4bd-2623">**Ícone** ![ Configuração de configuração da interface de pilha de anfitrião Selecionar ícone](./media/user-guide/usbx-events/image209.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2623">**Icon** ![Host Stack Interface Setting Select icon](./media/user-guide/usbx-events/image209.png)</span></span>

<span data-ttu-id="4e4bd-2624">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2624">**Description**</span></span>

<span data-ttu-id="4e4bd-2625">Este evento representa um evento de configuração de interface de anfitrião USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2625">This event represents a USBX Host Stack Interface Setting Select Event.</span></span>

<span data-ttu-id="4e4bd-2626">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2626">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2627">Info Field 1: Interface.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2627">Info Field 1: Interface.</span></span>
- <span data-ttu-id="4e4bd-2628">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2628">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2629">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2629">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2630">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2630">Info Field 4: Not used.</span></span>

### <a name="host-stack-new-configuration-create"></a><span data-ttu-id="4e4bd-2631">Host Stack Nova Configuração Criar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2631">Host Stack New Configuration Create</span></span> 

#### <a name="ux_host_stack_new_configuration_create"></a><span data-ttu-id="4e4bd-2632">ux_host_stack_new_configuration_create</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2632">ux_host_stack_new_configuration_create</span></span>

<span data-ttu-id="4e4bd-2633">**Ícone** ![ Host Stack Nova Configuração Criar ícone](./media/user-guide/usbx-events/image210.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2633">**Icon** ![Host Stack New Configuration Create icon](./media/user-guide/usbx-events/image210.png)</span></span>

<span data-ttu-id="4e4bd-2634">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2634">**Description**</span></span>
 
<span data-ttu-id="4e4bd-2635">Este evento representa um evento de configuração nova da pilha USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2635">This event represents a USBX Host Stack New Configuration Create Event.</span></span>

<span data-ttu-id="4e4bd-2636">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2636">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2637">Info Field 1: Dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2637">Info Field 1: Device.</span></span>
- <span data-ttu-id="4e4bd-2638">Info Field 2: Configuração.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2638">Info Field 2: Configuration.</span></span>
- <span data-ttu-id="4e4bd-2639">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2639">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2640">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2640">Info Field 4: Not used.</span></span>

### <a name="host-stack-new-device-create"></a><span data-ttu-id="4e4bd-2641">Host Stack Novo Dispositivo Criar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2641">Host Stack New Device Create</span></span> 

#### <a name="ux_host_stack_new_device_create"></a><span data-ttu-id="4e4bd-2642">ux_host_stack_new_device_create</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2642">ux_host_stack_new_device_create</span></span>

<span data-ttu-id="4e4bd-2643">**Ícone** ![ Host Stack novo dispositivo criar ícone](./media/user-guide/usbx-events/image211.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2643">**Icon** ![Host Stack New Device Create icon](./media/user-guide/usbx-events/image211.png)</span></span>

<span data-ttu-id="4e4bd-2644">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2644">**Description**</span></span>
 
 <span data-ttu-id="4e4bd-2645">Este evento representa um evento usbx host Stack New Device Create.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2645">This event represents a USBX Host Stack New Device Create Event.</span></span>

<span data-ttu-id="4e4bd-2646">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2646">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2647">Info Field 1: Hcd.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2647">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="4e4bd-2648">Info Field 2: Proprietário do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2648">Info Field 2: Device owner.</span></span>
- <span data-ttu-id="4e4bd-2649">Info Field 3: Índice de porta.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2649">Info Field 3: Port index.</span></span>
- <span data-ttu-id="4e4bd-2650">Info Field 4: Dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2650">Info Field 4: Device.</span></span>

### <a name="host-stack-new-endpoint-create"></a><span data-ttu-id="4e4bd-2651">Host Stack Novo Ponto Final Criar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2651">Host Stack New Endpoint Create</span></span> 

#### <a name="ux_host_stack_new_endpoint_create"></a><span data-ttu-id="4e4bd-2652">ux_host_stack_new_endpoint_create</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2652">ux_host_stack_new_endpoint_create</span></span>

<span data-ttu-id="4e4bd-2653">**Ícone** ![ Host Stack Novo Ponto Final Criar ícone](./media/user-guide/usbx-events/image212.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2653">**Icon** ![Host Stack New Endpoint Create icon](./media/user-guide/usbx-events/image212.png)</span></span>

<span data-ttu-id="4e4bd-2654">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2654">**Description**</span></span>
 
<span data-ttu-id="4e4bd-2655">Este evento representa um evento USBX Host Stack New Endpoint Create Event.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2655">This event represents a USBX Host Stack New Endpoint Create Event.</span></span>

<span data-ttu-id="4e4bd-2656">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2656">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2657">Info Field 1: Interface.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2657">Info Field 1: Interface.</span></span>
- <span data-ttu-id="4e4bd-2658">Info Field 2: Ponto final.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2658">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4e4bd-2659">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2659">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2660">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2660">Info Field 4: Not used.</span></span>

### <a name="host-stack-root-hub-change-process"></a><span data-ttu-id="4e4bd-2661">Processo de mudança do hub de raiz da pilha de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2661">Host Stack Root Hub Change Process</span></span> 

#### <a name="ux_host_stack_rh_change_process"></a><span data-ttu-id="4e4bd-2662">ux_host_stack_rh_change_process</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2662">ux_host_stack_rh_change_process</span></span>

<span data-ttu-id="4e4bd-2663">**Ícone** ![ Ícone de mudança de fundo de raiz de pilha de anfitrião](./media/user-guide/usbx-events/image213.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2663">**Icon** ![Host Stack Root Hub Change Process icon](./media/user-guide/usbx-events/image213.png)</span></span>

<span data-ttu-id="4e4bd-2664">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2664">**Description**</span></span>
 
<span data-ttu-id="4e4bd-2665">Este evento representa um processo de mudança de raiz do hub de raiz da stack usbx.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2665">This event represents a USBX Host Stack Root Hub Change Process.</span></span>

<span data-ttu-id="4e4bd-2666">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2666">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2667">Info Field 1: Índice de porta.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2667">Info Field 1: Port index.</span></span>
- <span data-ttu-id="4e4bd-2668">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2668">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4e4bd-2669">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2669">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2670">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2670">Info Field 4: Not used.</span></span>

### <a name="host-stack-root-hub-device-extraction"></a><span data-ttu-id="4e4bd-2671">Extração de dispositivo de plataforma de raiz de pilha de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2671">Host Stack Root Hub Device Extraction</span></span> 

#### <a name="ux_host_stack_rh_device_extraction"></a><span data-ttu-id="4e4bd-2672">ux_host_stack_rh_device_extraction</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2672">ux_host_stack_rh_device_extraction</span></span>

<span data-ttu-id="4e4bd-2673">**Ícone** ![ Ícone de extração de dispositivo de raiz de pilha de anfitrião](./media/user-guide/usbx-events/image214.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2673">**Icon** ![Host Stack Root Hub Device Extraction icon](./media/user-guide/usbx-events/image214.png)</span></span>

<span data-ttu-id="4e4bd-2674">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2674">**Description**</span></span>

<span data-ttu-id="4e4bd-2675">Este evento representa um evento de extração de dispositivos de raiz do hub de raiz da stack usbx.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2675">This event represents a USBX Host Stack Root Hub Device Extraction Event.</span></span>

<span data-ttu-id="4e4bd-2676">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2676">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2677">Info Field 1: Hcd.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2677">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="4e4bd-2678">Info Field 2: Índice de porta.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2678">Info Field 2: Port index.</span></span>
- <span data-ttu-id="4e4bd-2679">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2679">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2680">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2680">Info Field 4: Not used.</span></span>

### <a name="host-stack-root-hub-device-insertion"></a><span data-ttu-id="4e4bd-2681">Inserção do dispositivo do hub de raiz do anfitrião Stack</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2681">Host Stack Root Hub Device Insertion</span></span> 

#### <a name="ux_host_stack_rh_device_insertion"></a><span data-ttu-id="4e4bd-2682">ux_host_stack_rh_device_insertion</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2682">ux_host_stack_rh_device_insertion</span></span>

<span data-ttu-id="4e4bd-2683">**Ícone** ![ Ícone de inserção do dispositivo de inserção do hub de raiz da pilha de anfitrião](./media/user-guide/usbx-events/image215.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2683">**Icon** ![Host Stack Root Hub Device Insertion icon](./media/user-guide/usbx-events/image215.png)</span></span>

<span data-ttu-id="4e4bd-2684">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2684">**Description**</span></span>

<span data-ttu-id="4e4bd-2685">Este evento representa uma inserção do dispositivo de raiz do hub de raiz da stack usbx.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2685">This event represents a USBX Host Stack Root Hub Device Insertion.</span></span>

<span data-ttu-id="4e4bd-2686">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2686">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2687">Info Field 1: Hcd.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2687">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="4e4bd-2688">Info Field 2: Índice de porta.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2688">Info Field 2: Port index.</span></span>
- <span data-ttu-id="4e4bd-2689">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2689">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2690">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2690">Info Field 4: Not used.</span></span>

### <a name="host-stack-transfer-request"></a><span data-ttu-id="4e4bd-2691">Pedido de transferência de pilha de anfitrião</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2691">Host Stack Transfer Request</span></span> 

#### <a name="ux_host_stack_transfer_request"></a><span data-ttu-id="4e4bd-2692">ux_host_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2692">ux_host_stack_transfer_request</span></span>

<span data-ttu-id="4e4bd-2693">**Ícone** ![ Ícone de pedido de transferência de pilha de anfitrião](./media/user-guide/usbx-events/image216.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2693">**Icon** ![Host Stack Transfer Request icon](./media/user-guide/usbx-events/image216.png)</span></span>

<span data-ttu-id="4e4bd-2694">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2694">**Description**</span></span>

<span data-ttu-id="4e4bd-2695">Este evento representa um pedido de transferência usbx host stack.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2695">This event represents a USBX Host Stack Transfer Request.</span></span>

<span data-ttu-id="4e4bd-2696">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2696">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2697">Info Field 1: Dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2697">Info Field 1: Device.</span></span>
- <span data-ttu-id="4e4bd-2698">Info Field 2: Ponto final.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2698">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4e4bd-2699">Info Campo 3: Pedido de transferência.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2699">Info Field 3: Transfer request.</span></span>
- <span data-ttu-id="4e4bd-2700">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2700">Info Field 4: Not used.</span></span>

### <a name="host-stack-transfer-request-abort"></a><span data-ttu-id="4e4bd-2701">Pedido de transferência de pilha de anfitrião abortar</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2701">Host Stack Transfer Request Abort</span></span> 

#### <a name="internal-io-driver-get-status"></a><span data-ttu-id="4e4bd-2702">O controlador interno de I/O obtém o estado</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2702">Internal I/O driver get status</span></span>

<span data-ttu-id="4e4bd-2703">**Ícone** ![ Ícone de aborto de pedido de transferência de pilha de anfitrião](./media/user-guide/usbx-events/image217.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2703">**Icon** ![Host Stack Transfer Request Abort icon](./media/user-guide/usbx-events/image217.png)</span></span>

<span data-ttu-id="4e4bd-2704">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2704">**Description**</span></span>

<span data-ttu-id="4e4bd-2705">Este evento representa um pedido de transferência usbx host Stack Abort.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2705">This event represents a USBX Host Stack Transfer Request Abort.</span></span>

<span data-ttu-id="4e4bd-2706">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2706">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2707">Info Field 1: Dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2707">Info Field 1: Device.</span></span>
- <span data-ttu-id="4e4bd-2708">Info Field 2: Ponto final.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2708">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="4e4bd-2709">Info Campo 3: Pedido de transferência.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2709">Info Field 3: Transfer request.</span></span>
- <span data-ttu-id="4e4bd-2710">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2710">Info Field 4: Not used.</span></span>

### <a name="usbx-error"></a><span data-ttu-id="4e4bd-2711">Erro USBX</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2711">USBX Error</span></span> 

#### <a name="ux_error"></a><span data-ttu-id="4e4bd-2712">ux_error</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2712">ux_error</span></span>

<span data-ttu-id="4e4bd-2713">**Ícone** ![ Ícone de erro U S B X](./media/user-guide/usbx-events/image218.png)</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2713">**Icon** ![U S B X Error icon](./media/user-guide/usbx-events/image218.png)</span></span>

<span data-ttu-id="4e4bd-2714">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2714">**Description**</span></span>

<span data-ttu-id="4e4bd-2715">Este evento representa um Evento de Erro USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2715">This event represents a USBX Error Event.</span></span>

<span data-ttu-id="4e4bd-2716">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2716">**Information Fields**</span></span>

- <span data-ttu-id="4e4bd-2717">Info Field 1: erro USBX.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2717">Info Field 1: USBX error.</span></span>
- <span data-ttu-id="4e4bd-2718">Info Field 2: Nome de erro.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2718">Info Field 2: Error Name.</span></span>
- <span data-ttu-id="4e4bd-2719">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2719">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4e4bd-2720">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="4e4bd-2720">Info Field 4: Not used.</span></span>