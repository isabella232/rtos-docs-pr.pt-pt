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
# <a name="chapter-9---azure-rtos-usbx-trace-events"></a>Capítulo 9 - Azure RTOS USBX trace eventos

Este capítulo contém uma descrição dos eventos Azure RTOS USBX exibidos pela TraceX. 

## <a name="list-of-events-and-icons"></a>Lista de eventos e ícones

Segue-se uma lista de eventos USBX apresentados pela TraceX.

| Ícone                             | Significado                               |
| -------------------------------- | ------------------------------------- |
| ![Ícone ativar classe C D C C do dispositivo](./media/user-guide/usbx-events/image1.png)    | **Dispositivo Classe Cdc Ativar** *(ux_device_class_cdc_activate)* |
| ![Ícone desativado classe C D C C](./media/user-guide/usbx-events/image2.png)    | **Desativar o CDC classe de dispositivo** *(ux_device_class_cdc_deactivate)* |
| ![Ícone de leitura classe C D C do dispositivo](./media/user-guide/usbx-events/image3.png)    | **Leitura do cdc classe do dispositivo** *(ux_device_class_cdc_read)* |
| ![Ícone de escrita classe C D C do dispositivo](./media/user-guide/usbx-events/image4.png)    | **Escrita do Cdc classe de dispositivo** *(ux_device_class_cdc_write)* |
| ![Ícone ativar classe de dispositivo](./media/user-guide/usbx-events/image5.png)    | **Dispositivo Classe Dpump Ativar** *(ux_device_class_dpump_activate)* |
| ![Ícone de desativado da classe de dispositivo Dpump](./media/user-guide/usbx-events/image6.png)    | **Desativar a classe do dispositivo Dpump** *(ux_device_class_dpump_deactivate)* |
| ![Ícone de leitura de classe de dispositivo](./media/user-guide/usbx-events/image7.png)    | **Leitura de Dpump classe de dispositivo** *(ux_device_class_dpump_read)* |
| ![Ícone de escrita de classe de dispositivo](./media/user-guide/usbx-events/image8.png)    | **Escrita de Classe de Dispositivo** *(ux_device_class_dpump_write)* |
| ![Ícone ativar classe de dispositivo Hid](./media/user-guide/usbx-events/image9.png)    | **Classe de dispositivo Hid Ativado** *(ux_device_class_hid_activate)* |
| ![Ícone de desativado classe de dispositivo Hid](./media/user-guide/usbx-events/image10.png)    | **Classe de dispositivo Hid Desativado** *(ux_device_class_hid_deactivate)* |
| ![Classe de dispositivo hiddscriptor Enviar ícone](./media/user-guide/usbx-events/image11.png)    | **Classe de dispositivo Hid Descriptor Enviar** *(ux_device_class_hid_descriptor_send)* |
| ![Classe de dispositivo hid evento obter ícone](./media/user-guide/usbx-events/image12.png)    | **Evento hid de classe de dispositivo** *(ux_device_class_hid_event_get)* |
| ![Ícone de conjunto de evento de classe de dispositivo hid](./media/user-guide/usbx-events/image13.png)    | **Conjunto de eventos de classe de dispositivo** *(ux_device_class_hid_event_set)* |
| ![Relatório hid classe de dispositivo obter ícone](./media/user-guide/usbx-events/image14.png)    | **Relatório hid da classe do dispositivo obter** *(ux_device_class_hid_report_get)* |
| ![Ícone de conjunto de relatório de classe de dispositivo hid](./media/user-guide/usbx-events/image15.png)    | **Conjunto de relatórios de hid classe de dispositivo** *(ux_device_class_hid_report_set)* |
| ![Ícone de ativação classe de dispositivo Pima](./media/user-guide/usbx-events/image16.png)    | **Classe de dispositivo Pima Ativar** *(ux_device_class_pima_activate)* |
| ![Ícone de desativado classe de dispositivo Pima](./media/user-guide/usbx-events/image17.png)    | **Classe de dispositivo Pima Desativado** *(ux_device_class_pima_deactivate)* |
| ![Informação de envio de dispositivo classe de dispositivo Pima classe de dispositivo](./media/user-guide/usbx-events/image18.png)    | **Informação do dispositivo classe Pima Enviar** *(ux_device_class_pima_device_info_send)* |
| ![Evento Pima classe de dispositivo Obter ícone](./media/user-guide/usbx-events/image19.png)    | **Evento Pima classe de dispositivo** *(ux_device_class_pima_event_get)* |
| ![Ícone de conjunto de evento classe de dispositivo Pima](./media/user-guide/usbx-events/image20.png)    | **Conjunto de eventos classe de dispositivo Pima** *(ux_device_class_pima_event_set)* |
| ![Ícone de adicionar objeto classe de dispositivo Pima](./media/user-guide/usbx-events/image21.png)    | **Adicionar objeto classe de dispositivo Pima** *(ux_device_class_pima_object_add)* |
| ![Dados de objeto de classe de dispositivo Pima Obter ícone](./media/user-guide/usbx-events/image22.png)    | **Dados de objetos de classe de dispositivo Pima obtêm** *(ux_device_class_pima_object_data_get)* |
| ![Dados de objeto de classe de dispositivo Pima Enviar ícone](./media/user-guide/usbx-events/image23.png)    | **Dados de objetos de classe de dispositivo Pima envio** *(ux_device_class_pima_object_data_send)* |
| ![Ícone de eliminação de objeto de classe de dispositivo Pima](./media/user-guide/usbx-events/image24.png)    | **Eliminação de objetos classe de dispositivo Pima** *(ux_device_class_pima_object_delete)* |
| ![Alças de objeto classe de dispositivo Pima Enviar ícone](./media/user-guide/usbx-events/image25.png)    | **Dispositivo Classe Pima Objeto Handles Enviar** *(ux_device_class_pima_object_handles_send)* |
| ![Classe de dispositivo Pima Objeto Info Obter ícone](./media/user-guide/usbx-events/image26.png)    | **Informações de objetos Pima classe de dispositivo** *(ux_device_class_pima_object_info_get)* |
| ![Classe de dispositivo Pima Objeto Info Enviar ícone](./media/user-guide/usbx-events/image27.png)    | **Informações de objetos de classe de dispositivo Pima Enviar** *(ux_device_class_pima_object_info_send)* |
| ![Número de objetos de classe de dispositivo Pima Enviar ícone](./media/user-guide/usbx-events/image28.png)    | **Número de objetos classe de dispositivo Pima Enviar** *(ux_device_class_pima_objects_number_send)* |
| ![Classe de dispositivo Pima Objeto Parcial Objeto Dados Obter ícone](./media/user-guide/usbx-events/image29.png)    | **Dados de objetos parciais da classe do dispositivo Pima obtêm** *(ux_device_class_pima_partial_object_data_get)* |
| ![Ícone de resposta pima classe de dispositivo](./media/user-guide/usbx-events/image30.png)    | **Envio de resposta classe de dispositivo Pima** *(ux_device_class_pima_response_send)*|
| ![Classe de dispositivo Pima Armazenamento I D Enviar ícone](./media/user-guide/usbx-events/image31.png)    | **Envio de Id de armazenamento classe de dispositivo Pima** *(ux_device_class_pima_storage_id_send)* |
| ![Classe de dispositivo Pima Storage Info Enviar ícone](./media/user-guide/usbx-events/image32.png)    | **Informações de armazenamento classe de dispositivo Pima Enviar** *(ux_device_class_pima_storage_info_send)* |
| ![Ícone ativar classe de dispositivo R N D I S](./media/user-guide/usbx-events/image33.png)    | **Dispositivo Classe Rndis Ativar** *(ux_device_class_rndis_activate)* |
| ![Ícone de desativado classe de dispositivo R N D I S](./media/user-guide/usbx-events/image34.png)    | **Classe dispositivo Rndis Desativado** *(ux_device_class_rndis_deactivate)* |
| ![Classe de dispositivo R N D I S Mensagem Manter Aliveicon](./media/user-guide/usbx-events/image35.png)    | **Mensagem Rndis classe dispositivo Manter vivo** *(ux_device_class_rndis_msg_keep_alive)* |
| ![Ícone de consulta de mensagem classe de dispositivo R N D I S](./media/user-guide/usbx-events/image36.png)    | **Consulta de mensagem classe de dispositivo Rndis** *(ux_device_class_rndis_msg_query)* |
| ![Ícone de reset de mensagem classe de dispositivo R N D I S](./media/user-guide/usbx-events/image37.png)    | **Reset de mensagem classe de dispositivo Rndis** *(ux_device_class_rndis_msg_reset)* |
| ![Ícone de conjunto de mensagem classe de dispositivo R N D I S](./media/user-guide/usbx-events/image38.png)    | **Conjunto de mensagens Rndis classe de dispositivo** *(ux_device_class_rndis_msg_set)* |
| ![Ícone de receção de pacote classe de dispositivo R N D I S](./media/user-guide/usbx-events/image39.png)    | **Pacote classe de dispositivo Rndis** *(ux_device_class_rndis_packet_receive)* |
| ![Ícone de transmissão de pacote de pacote classe R N D I I S](./media/user-guide/usbx-events/image40.png)    | **Dispositivo Classe Rndis Packet Transmit** *(ux_device_class_rndis_packet_transmit)* |
| ![Ícone ativar o armazenamento da classe do dispositivo](./media/user-guide/usbx-events/image41.png)    | **Ativar o armazenamento da classe do dispositivo** *(ux_device_class_storage_activate)* |
| ![Ícone de desativação de classe de dispositivo](./media/user-guide/usbx-events/image42.png)    | **Desativação do armazenamento da classe do dispositivo** *(ux_device_class_storage_deactivate)* |
| ![Ícone de formato de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image43.png)    | **Formato de armazenamento de classe de dispositivo** *(ux_device_class_storage_format)* |
| ![Ícone de inquérito de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image44.png)    | **Inquérito de armazenamento da classe do dispositivo** *(ux_device_class_storage_inquiry)* |
| ![Modo de armazenamento de classe de dispositivo Selecionar ícone](./media/user-guide/usbx-events/image45.png)    | **Selecione o modo de armazenamento da classe do dispositivo** *(ux_device_class_storage_mode_select)* |
| ![Ícone de sentido de modo de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image46.png)    | **Sentido do modo de armazenamento da classe do dispositivo** *(ux_device_class_storage_mode_sense)* |
| ![Armazenamento de classe de dispositivo Previne permitir ícone de remoção de mídia](./media/user-guide/usbx-events/image47.png)    | **Armazenamento da classe do dispositivo Previne a remoção dos meios** de comunicação *(ux_device_class_storage_prevent_allow_media_removal)* |
| ![Ícone de leitura de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image48.png)    | **Leitura de armazenamento da classe do dispositivo** *(ux_device_class_storage_read)* |
| ![Ícone de capacidade de leitura de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image49.png)    | **Capacidade de leitura de armazenamento de classe do dispositivo** *(ux_device_class_storage_read_capacity)* |
| ![Ícone de capacidade de leitura de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image50.png)    | **Capacidade de leitura do formato de leitura da classe do dispositivo** *(ux_device_class_storage_read_format_capacity)* |
| ![Armazenamento de classe de dispositivo Leia o ícone TOC](./media/user-guide/usbx-events/image51.png)    | **Armazenamento da classe do dispositivo Leia TOC** *(ux_device_class_storage_read_toc)* |
| ![Ícone de pedido de pedido de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image52.png)    | **Sentido do pedido de armazenamento da classe do dispositivo** *(ux_device_class_storage_request_sense)* |
| ![Ícone de início de paragem de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image53.png)    | **Paragem de início de armazenamento da classe do dispositivo** *(ux_device_class_storage_start_stop)* |
| ![Ícone de teste de armazenamento de classe de dispositivo pronto](./media/user-guide/usbx-events/image54.png)    | **Teste de armazenamento da classe do dispositivo pronto** *(ux_device_class_storage_test_ready)* |
| ![Ícone de verificação de classe de dispositivo](./media/user-guide/usbx-events/image55.png)    | **Verificação da classe do dispositivo** *(ux_device_class_storage_verify)* |
| ![Ícone de escrita de classe de dispositivo](./media/user-guide/usbx-events/image56.png)    | **Escrita de armazenamento de classe de dispositivo** *(ux_device_class_storage_write)* |
| ![Configuração alternativa de pilha de dispositivo Obter ícone](./media/user-guide/usbx-events/image57.png)    | **Configuração alternativa de pilha de dispositivo** *(ux_device_stack_alternate_setting_get)* |
| ![Ícone de definição alternativa de configuração de pilha de dispositivo](./media/user-guide/usbx-events/image58.png)    | **Conjunto de definição alternativa** de pilha de *dispositivo (ux_device_stack_alternate_setting_set)* |
| ![Ícone de registo de classe de pilha de dispositivo](./media/user-guide/usbx-events/image59.png)    | **Registo de classe de pilha de dispositivos** *(ux_device_stack_class_register)* |
| ![Ícone de funcionalidade de limpação de pilha de dispositivo](./media/user-guide/usbx-events/image60.png)    | **Recurso de segurança da pilha de dispositivo** *(ux_device_stack_clear_feature)* |
| ![Configuração de pilha de dispositivo Obter ícone](./media/user-guide/usbx-events/image61.png)    | **Configuração de pilha de dispositivo obter** *(ux_device_stack_configuration_get)* |
| ![Ícone de conjunto de configuração de pilha de dispositivo](./media/user-guide/usbx-events/image62.png)    | **Conjunto de configuração da pilha de** *dispositivo (ux_device_stack_configuration_set)* |
| ![Ícone de conexão de pilha de dispositivo](./media/user-guide/usbx-events/image63.png)    | **Ligação da pilha de dispositivos** *(ux_device_stack_connect)* |
| ![Descritor de pilha de dispositivo Enviar ícone](./media/user-guide/usbx-events/image64.png)    | **Envio de descritor de pilha de dispositivo** *(ux_device_stack_descriptor_send)* |
| ![Ícone de desconexão de pilha de dispositivo](./media/user-guide/usbx-events/image65.png)    | **Desconexão da pilha de dispositivos** *(ux_device_stack_disconnect)* |
| ![Ícone de ponto final de pilha de dispositivo](./media/user-guide/usbx-events/image66.png)    | **Dispositivo Stack Endpoint Stall** *(ux_device_stack_endpoint_stall)* |
| ![Ícone de estado da pilha de dispositivo](./media/user-guide/usbx-events/image67.png)    | **Estado de obter pilha de dispositivos** *(ux_device_stack_get_status)* |
| ![Ícone de wakeup do anfitrião do dispositivo stack](./media/user-guide/usbx-events/image68.png)    | **Wakeup do anfitrião do dispositivo** *stack (ux_device_stack_host_wakeup)* |
| ![Ícone inicialize da pilha de dispositivo](./media/user-guide/usbx-events/image69.png)    | **Stack de dispositivo Inicialize** *(ux_device_stack_initialize)* |
| ![Ícone de eliminação da interface da pilha de dispositivo](./media/user-guide/usbx-events/image70.png)    | **Eliminação da interface da pilha de dispositivos** *(ux_device_stack_interface_delete)* |
| ![Interface de pilha de dispositivo Obter ícone](./media/user-guide/usbx-events/image71.png)    | **Interface de pilha de dispositivo obter** *(ux_device_stack_interface_get)* |
| ![Ícone de conjunto de interface de pilha de dispositivo](./media/user-guide/usbx-events/image72.png)    | **Conjunto de interface de pilha de dispositivo** *(ux_device_stack_interface_set)* |
| ![Ícone de funcionalidade de conjunto de pilha de dispositivo](./media/user-guide/usbx-events/image73.png)    | **Função de conjunto de pilha de dispositivo** *(ux_device_stack_set_feature)* |
| ![Ícone de aborto de transferência de pilha de dispositivo](./media/user-guide/usbx-events/image74.png)    | **Abortar a transferência da pilha de dispositivos** *(ux_device_stack_transfer_abort)* |
| ![*Transferência de pilha de dispositivo todo o ícone de abortar pedido](./media/user-guide/usbx-events/image75.png)    | **Transferência de pilha de dispositivos Todos os pedidos abortar** *(ux_device_stack_transfer_all_request_abort)* |
| ![Ícone de pedido de transferência de pilha de dispositivo](./media/user-guide/usbx-events/image76.png)    | **Pedido de transferência de pilha de dispositivo** *(ux_device_stack_transfer_request)* |
| ![Ícone de ativação classe de anfitrião Asix](./media/user-guide/usbx-events/image77.png)    | **Classe de anfitrião Asix Ativar** *(ux_host_class_asix_activate)* |
| ![Ícone de desativado classe anfitrião Asix](./media/user-guide/usbx-events/image78.png)    | **Classe hospedeira Desativado Asix** *(ux_host_class_asix_deactivate)* |
| ![Ícone de notificação de interrupção de classe de anfitrião Asix](./media/user-guide/usbx-events/image79.png)    | **Aviso de interrupção da classe anfitrião Asix** *(ux_host_class_asix_interrupt_notification)* |
| ![Ícone de leitura de classe de anfitrião](./media/user-guide/usbx-events/image80.png)    | **Classe de anfitrião Asix Read** *(ux_host_class_asix_read)* |
| ![Ícone de escrita de classe de anfitrião Asix](./media/user-guide/usbx-events/image81.png)    | **Classe de anfitrião Asix Write** *(ux_host_class_asix_write)* |
| ![Ícone ativar áudio classe anfitrião](./media/user-guide/usbx-events/image82.png)    | **Ativação áudio da classe do anfitrião** *(ux_host_class_audio_activate)* |
| ![Valor de controlo de áudio da classe do anfitrião Obter ícone](./media/user-guide/usbx-events/image83.png)    | **Valor de controlo de áudio da classe do anfitrião obter** *(ux_host_class_audio_control_value_get)* |
| ![Ícone do conjunto de conjunto de valor de controlo de áudio da classe do anfitrião](./media/user-guide/usbx-events/image84.png)    | **Conjunto de valor de controlo de áudio da classe do anfitrião** *(ux_host_class_audio_control_value_set)* |
| ![Ícone de desativado de áudio classe anfitrião](./media/user-guide/usbx-events/image85.png)    | **Desativar áudio da classe hospedeira** *(ux_host_class_audio_deactivate)* |
| ![Ícone de leitura de áudio de classe de anfitrião](./media/user-guide/usbx-events/image86.png)    | **Leitura áudio da classe do anfitrião** *(ux_host_class_audio_read)* |
| ![Amostragem de streaming de áudio de classe de anfitrião Obter ícone](./media/user-guide/usbx-events/image87.png)    | **Amostragem de streaming de áudio de classe de anfitrião obter** *(ux_host_class_audio_streaming_sampling_get)* |
| ![Ícone do conjunto de amostragem de streaming de áudio da classe do anfitrião](./media/user-guide/usbx-events/image88.png)    | **Conjunto de amostragem de streaming de áudio de classe de anfitrião** *(ux_host_class_audio_streaming_sampling_set)* |
| ![Ícone de escrita de áudio de classe de anfitrião](./media/user-guide/usbx-events/image89.png)    | **Escrita áudio da classe hospedeira** *(ux_host_class_audio_write)* |
| ![Classe anfitrião C D C A C M Ícone ativado](./media/user-guide/usbx-events/image90.png)    | **Classe de anfitrião Cdc Acm Ativar** *(ux_host_class_cdc_acm_activate)* |
| ![Ícone desativado classe C D C A C M](./media/user-guide/usbx-events/image91.png)    | **Classe anfitriã Cdc Acm Desativado** *(ux_host_class_cdc_acm_deactivate)* |
| ![Classe anfitriã C D C A C M I O C T L No ícone do tubo](./media/user-guide/usbx-events/image92.png)    | **Classe de anfitrião Cdc Acm Ioctl Abortar em Tubo** *(ux_host_class_cdc_acm_ioctl_abort_in_pipe)* |
| ![Classe anfitriã C D C A C M I O C T L AbortAr Ícone do Tubo](./media/user-guide/usbx-events/image93.png)    | **Classe anfitriã Cdc Acm Ioctl AbortAr Tubo** *(ux_host_class_cdc_acm_ioctl_abort_out_pipe)* |
| ![Classe hospedeira C D C A C M I O C T L Obter Ícone de Estado do Dispositivo](./media/user-guide/usbx-events/image94.png)    | **Classe de anfitrião Cdc Acm Ioctl Obter Estado do Dispositivo** *(ux_host_class_cdc_acm_ioctl_get_device_status)* |
| ![Classe anfitriã C D C A C M I O C T L Get Line Codificação](./media/user-guide/usbx-events/image95.png)    | **Classe de anfitrião Cdc Acm Ioctl Obter Codificação de Linha** *(ux_host_class_cdc_acm_ioctl_get_line_coding)* |
| ![Classe anfitriã C D C A C M I O C T L Notification Callback](./media/user-guide/usbx-events/image96.png)    | **Chamada de notificação cdc Acm ioctl classe anfitrião** *(ux_host_class_cdc_acm_ioctl_notification_callback)* |
| ![Classe anfitriã C D C A C M I O C T L Enviar Ícone de rutura](./media/user-guide/usbx-events/image97.png)    | **Classe anfitriã Cdc Acm Ioctl Send Break** *(ux_host_class_cdc_acm_ioctl_send_break)* |
| ![Classe anfitriã C D C A C M I O C T L Definir Ícone de codificação](./media/user-guide/usbx-events/image98.png)    | **Classe de anfitrião Cdc Acm Ioctl set Line Code Codificação** *(ux_host_class_cdc_acm_ioctl_set_line_coding)* |
| ![Classe anfitriã C D C A C A C M I O C T L set Line State ícone](./media/user-guide/usbx-events/image99.png)    | **Classe anfitrião Cdc Acm Ioctl set Line State** *(ux_host_class_cdc_acm_ioctl_set_line_state)* |
| ![Ícone de leitura classe C D C A C M](./media/user-guide/usbx-events/image100.png)    | **Classe de anfitrião Cdc Acm Read** *(ux_host_class_cdc_acm_read)* |
| ![Classe anfitrião C D C A C M Receção Ícone de início](./media/user-guide/usbx-events/image101.png)    | **Início de receção cdc Acm classe anfitrião** *(ux_host_class_cdc_acm_reception_start)* |
| ![Classe anfitrião C D C A C C M Ícone de paragem de receção](./media/user-guide/usbx-events/image102.png)    | **Paragem de receção cdc Acm classe anfitrião** *(ux_host_class_cdc_acm_reception_stop)* |
| ![Ícone de escrita classe de anfitrião C D C A C M](./media/user-guide/usbx-events/image103.png)    | **Classe anfitriã Cdc Acm Write** *(ux_host_class_cdc_acm_write)* |
| ![Ícone ativar classe de anfitrião](./media/user-guide/usbx-events/image104.png)    | **Classe de anfitrião Dpump Ativar** *(ux_host_class_dpump_activate)* |
| ![Ícone de desativado classe de anfitrião Dpump](./media/user-guide/usbx-events/image105.png)    | **Classe anfitriã Dpump Desativado** *(ux_host_class_dpump_deactivate)* |
| ![Ícone de leitura de classe de anfitrião](./media/user-guide/usbx-events/image106.png)    | **Leitura de Dpump de Classe anfitriã** *(ux_host_class_dpump_read)* |
| ![Ícone de escrita de classe de anfitrião](./media/user-guide/usbx-events/image107.png)    | **Escrita de Classe Anfitriã Dpump** *(ux_host_class_dpump_write)* |
| ![Ícone ativar classe de anfitrião Hid](./media/user-guide/usbx-events/image108.png)    | **Classe de anfitrião Hid Activate** *(ux_host_class_hid_activate)* |
| ![Ícone de registo de clientes de classe de anfitrião](./media/user-guide/usbx-events/image109.png)    | **Registo de clientes hid da classe de anfitrião** *(ux_host_class_hid_client_register)* |
| ![Ícone de desativado classe de anfitrião Hid](./media/user-guide/usbx-events/image110.png)    | **Classe de anfitrião Hid Desativado** *(ux_host_class_hid_deactivate)* |
| ![Classe de anfitrião Hid Idle Obter ícone](./media/user-guide/usbx-events/image111.png)    | **Classe de anfitrião Hid Idle Get** *(ux_host_class_hid_idle_get)* |
| ![Ícone de conjunto de conjunto de classe de anfitrião hid ocioso](./media/user-guide/usbx-events/image112.png)    | **Conjunto de idle de classe de anfitrião** *(ux_host_class_hid_idle_set)* |
| ![Ícone ativar teclado de classe de anfitrião](./media/user-guide/usbx-events/image113.png)    | **Classe de anfitrião Hid Keyboard Activate** *(ux_host_class_hid_keyboard_activate)* |
| ![Ícone de desativado do teclado da classe anfitrião Hid](./media/user-guide/usbx-events/image114.png)    | **Classe de anfitrião Hid Keyboard Desativado** *(ux_host_class_hid_keyboard_deactivate)* |
| ![Ícone ativar rato de classe de anfitrião](./media/user-guide/usbx-events/image115.png)    | **Classe de anfitrião Hid Mouse Activate** *(ux_host_class_hid_mouse_activate)* |
| ![Ícone de desativado do rato da classe do anfitrião](./media/user-guide/usbx-events/image116.png)    | **Classe de anfitrião Hid Mouse Desativado** *(ux_host_class_hid_mouse_deactivate)* |
| ![Classe de anfitrião hid remote controle ícone ativar](./media/user-guide/usbx-events/image117.png)    | **Classe de anfitrião Hid Controlo Remoto Ativado** *(ux_host_class_hid_remote_control_activate)* |
| ![Classe de anfitrião hid remote control desativado ícone](./media/user-guide/usbx-events/image118.png)    | **Classe de anfitrião Hid Controlo Remoto Desativado** *(ux_host_class_hid_remote_control_deactivate)* |
| ![Relatório hid classe anfitrião Obter ícone](./media/user-guide/usbx-events/image119.png)    | **Relatório hid da classe de anfitrião obter** *(ux_host_class_hid_report_get)* |
| ![Ícone de conjunto de relatório de classe de anfitrião hid](./media/user-guide/usbx-events/image120.png)    | **Conjunto de relatórios de classe de anfitrião** *(ux_host_class_hid_report_set)* |
| ![Ícone ativar o centro de classe do anfitrião](./media/user-guide/usbx-events/image121.png)    | **Centro de classe de anfitrião Ativado** *(ux_host_class_hub_activate)* |
| ![Ícone de deteção de mudança de centro de classe de anfitrião](./media/user-guide/usbx-events/image122.png)    | **Deteção de mudança de centro de classe de anfitrião** *(ux_host_class_hub_change_detect)* |
| ![*Ícone de desativar o hub da classe anfitrião](./media/user-guide/usbx-events/image123.png)    | **Desativar o Hub de Classe hospedeira** *(ux_host_class_hub_deactivate)* |
| ![Ícone do processo de mudança de ligação do hub da classe do anfitrião](./media/user-guide/usbx-events/image124.png)    | **Processo de mudança de porta do hub de classe do anfitrião** *(ux_host_class_hub_port_change_connection_process)* |
| ![Ícone de mudança de carro do hub de classe de anfitrião](./media/user-guide/usbx-events/image125.png)    | **Processo de ativação de mudança de porta do hub de classe de anfitrião** *(ux_host_class_hub_port_change_enable_process)* |
| ![Mudança de porta do hub do anfitrião sobre o ícone do processo atual](./media/user-guide/usbx-events/image126.png)    | **Mudança de porta do hub de classe de anfitrião sobre o processo atual** *(ux_host_class_hub_port_change_over_current_process)* |
| ![Ícone do processo de reposição do processo de mudança de porta do hub da classe do anfitrião](./media/user-guide/usbx-events/image127.png)    | Processo de reset da **parte do centro da parte do anfitrião** *(ux_host_class_hub_port_change_reset_process)* |
| ![Ícone de processo de suspensão de mudança de porta do hub de classe de anfitrião](./media/user-guide/usbx-events/image128.png)    | **Processo de suspensão da suspensão do porto do hub da classe de anfitrião** *(ux_host_class_hub_port_change_suspend_process)* |
| ![Ícone de ativação classe de anfitrião Pima](./media/user-guide/usbx-events/image129.png)    | **Classe de anfitrião Pima Ativar** *(ux_host_class_prima_activate)* |
| ![Ícone de desativado classe de anfitrião Pima](./media/user-guide/usbx-events/image130.png)    | **Classe anfitriã Pima Desativado** *(ux_host_class_pima_deactivate)* |
| ![Classe anfitrião Pima Device Info Obter ícone](./media/user-guide/usbx-events/image131.png)    | **Informações do dispositivo Pima da classe anfitriã** *(ux_host_class_pima_device_info_get)* |
| ![Ícone de reset do dispositivo Pima da classe anfitrião](./media/user-guide/usbx-events/image132.png)    | **Reset do dispositivo Pima da classe de anfitrião** *(ux_host_class_pima_device_reset)* |
| ![Ícone de notificação Pima classe anfitrião](./media/user-guide/usbx-events/image133.png)    | **Notificação Pima classe anfitrião** *(ux_host_class_pima_notification)* |
| ![Objetos de número pima classe anfitrião obter ícone](./media/user-guide/usbx-events/image134.png)    | **Objetos de número pima classe anfitrião obtêm** *(ux_host_class_pima_num_objects_get)* |
| ![Ícone de fecho de objeto pima classe anfitrião](./media/user-guide/usbx-events/image135.png)    | **Classe anfitrião Pima Objeto Perto** *(ux_host_class_pima_object_close)* |
| ![Ícone de cópia de objeto de classe de anfitrião Pima](./media/user-guide/usbx-events/image136.png)    | **Cópia do objeto Pima da classe anfitriã** *(ux_host_class_pima_object_copy)* |
| ![Ícone de exclusão de objeto pima classe anfitrião](./media/user-guide/usbx-events/image137.png)    | **Classe anfitrião Pima Object Delete** *(ux_host_class_pima_object_delete)* |
| ![Classe anfitrião Pima Objeto Obter ícone](./media/user-guide/usbx-events/image138.png)    | **Anfitrião Classe Pima Objeto Obter** *(ux_host_class_pima_object_get)* |
| ![Classe anfitrião Pima Objeto Info Obter ícone](./media/user-guide/usbx-events/image139.png)    | **Host Class Pima Object Info Get** *(ux_host_class_pima_object_info_get)* |
| ![Classe anfitrião Pima Objeto Info Enviar ícone](./media/user-guide/usbx-events/image140.png)    | **Informações de objeto pima classe anfitrião Enviar** *(ux_host_class_pima_object_info_send)* |
| ![Ícone de movimento de objeto de classe de anfitrião Pima](./media/user-guide/usbx-events/image141.png)    | **Movimento de objeto classe anfitrião Pima** *(ux_host_class_pima_object_move)* |
| ![Ícone de envio de objeto pima classe anfitrião](./media/user-guide/usbx-events/image142.png)    | **Envio de objeto classe de anfitrião Pima** *(ux_host_class_pima_object_send)* |
| ![Ícone de aborto de transferência de objeto de classe Pima de anfitrião](./media/user-guide/usbx-events/image143.png)    | **Aborto de transferência de objetos Pima classe anfitrião** *(ux_host_class_object_transfer_abort)* |
| ![Ícone de leitura de classe de anfitrião Pima](./media/user-guide/usbx-events/image144.png)    | **Classe de Anfitrião Pima Read** *(ux_host_class_pima_read)* |
| ![Classe anfitrião Pima Request Cancel ícone](./media/user-guide/usbx-events/image145.png)    | **Cancelamento de pedido de classe de anfitrião Pima** *(ux_host_class_pima_request_cancel)* |
| ![Ícone de fecho de sessão pima de classe de anfitrião](./media/user-guide/usbx-events/image146.png)    | **Sessão Pima de anfitrião** *(ux_host_class_pima_session_close)* |
| ![Ícone do open da sessão pima de classe de anfitrião](./media/user-guide/usbx-events/image147.png)    | **Host Class Pima Session Open** *(ux_host_class_pima_session_open)* |
| ![Classe anfitrião Pima Storage Ids Obter ícone](./media/user-guide/usbx-events/image148.png)    | **Anfitriões Classe Pima Storage Ids Get** *(ux_host_class_pima_storage_ids_get)* |
| ![Classe anfitrião Pima Storage Info Obter ícone](./media/user-guide/usbx-events/image149.png)    | **Informações de armazenamento Pima da classe anfitriã** *(ux_host_class_pima_storage_info_get)* |
| ![Ícone de polegar Pima de classe de anfitrião](./media/user-guide/usbx-events/image150.png)    | **Classe anfitrião Pima Polegar Get** *(ux_host_class_pima_thumb_get)* |
| ![Ícone de escrita classe de anfitrião Pima](./media/user-guide/usbx-events/image151.png)    | **Classe anfitriã Pima Write** *(ux_host_class_pima_write)* |
| ![Ícone ativar impressora de classe de anfitrião](./media/user-guide/usbx-events/image152.png)    | **Impressora de classe de anfitrião Ativada** *(ux_host_class_printer_activate)* |
| ![Ícone de desativar impressora de classe de anfitrião](./media/user-guide/usbx-events/image153.png)    | **Impressora de classe de anfitrião desativar** *(ux_host_class_printer_deactivate)* |
| ![Nome da impressora de classe anfitrião obter ícone](./media/user-guide/usbx-events/image154.png)    | **Nome da impressora de classe de anfitrião obter** *(ux_host_class_printer_name_get)* |
| ![Ícone de leitura de impressora de classe de anfitrião](./media/user-guide/usbx-events/image155.png)    |  **Leitura da impressora da classe do anfitrião** *(ux_host_class_printer_read)* |
| ![Ícone de reset suave da impressora de classe de anfitrião](./media/user-guide/usbx-events/image156.png)    | **Reset suave da impressora de classe de anfitrião** *(ux_host_class_printer_soft_reset)* |
| ![Estado da impressora de classe de anfitrião Obter ícone](./media/user-guide/usbx-events/image157.png)    | **Estado da impressora de classe de anfitrião obter** *(ux_host_class_printer_status_get)* |
| ![Ícone de escrita de impressora de classe de anfitrião](./media/user-guide/usbx-events/image158.png)    | **Escrita de impressora de classe de anfitrião** *(ux_host_class_printer_write)* |
| ![Ícone de ativação prolific de classe de anfitrião](./media/user-guide/usbx-events/image159.png)    | **Ativação Prolific classe de anfitrião** *(ux_host_class_prolific_activate)* |
| ![Ícone prolífico da classe de anfitrião](./media/user-guide/usbx-events/image160.png)    | **Classe de anfitrião Prolific Desativado** *(ux_host_class_prolific_deactivate)* |
| ![Classe de anfitrião Prolific I O C T T L Abortar no ícone do tubo](./media/user-guide/usbx-events/image161.png)    | **Classe de anfitrião Prolific Ioctl Abort in Pipe** *(ux_host_class_prolific_ioctl_abort_in_pipe)* |
| ![Classe de anfitrião Prolific I O C T L AbortAr Ícone do Tubo](./media/user-guide/usbx-events/image162.png)    | **Classe de anfitrião Prolific Ioctl AbortAr Tubo** *(ux_host_class_prolific_ioctl_abort_out_pipe)* |
| ![Classe de anfitrião Prolific I O C T L Obter Ícone de Estado do Dispositivo](./media/user-guide/usbx-events/image163.png)    | **Classe de anfitrião Prolific Ioctl Obter Estado do Dispositivo** *(ux_host_class_prolific_ioctl_get_device_status)* |
| ![Classe de anfitrião Prolific I O C T L Obter Ícone de codificação de linha](./media/user-guide/usbx-events/image164.png)    | **Classe de anfitrião Prolific Ioctl Get Line Coding** *(ux_host_class_prolific_ioctl_get_line_coding)* |
| ![Ícone de purga de classe de anfitrião I O C T L](./media/user-guide/usbx-events/image165.png)    | **Classe de anfitrião Prolific Ioctl Purga** *(ux_host_class_prolific_ioctl_purge)* |
| ![Ícone de alteração de estado do dispositivo de mudança de dispositivo de classe de anfitrião I O C T L](./media/user-guide/usbx-events/image166.png)    | Mudança de estado do dispositivo de **relatório prolific da classe de anfitrião** *(ux_host_class_prolific_ioctl_report_device_status_change)* |
| ![Classe de anfitrião Prolific I O C T L Enviar Ícone de rutura](./media/user-guide/usbx-events/image167.png)    | **Classe de anfitrião Prolific Ioctl Send Break** *(ux_host_class_prolific_ioctl_send_break)* |
| ![Ícone de codificação de linha de classe de anfitrião I O C T L](./media/user-guide/usbx-events/image168.png)    | **Codificação de linha de conjunto de conjunto prolific da classe de anfitrião** *(ux_host_class_prolific_ioctl_set_line_coding)* |
| ![Classe de anfitrião Prolific I O C T L set Line State ícone](./media/user-guide/usbx-events/image169.png)    | **Classe de anfitrião Prolific Ioctl set Line State** *(ux_host_class_prolific_ioctl_set_line_state)* |
| ![Ícone de leitura prolífica de classe de anfitrião](./media/user-guide/usbx-events/image170.png)    | **Leitura Prolífica da Classe anfitriã** *(ux_host_class_prolific_read)* |
| ![Ícone de início de receção prolific de classe de anfitrião](./media/user-guide/usbx-events/image171.png)    | **Início de receção prolific da classe anfitriã** *(ux_host_class_prolific_reception_start)* |
| ![Ícone de paragem de receção prolific de classe de anfitrião](./media/user-guide/usbx-events/image172.png)    | **Paragem de receção prolific da classe anfitriã** *(ux_host_class_prolific_reception_stop)* |
| ![Ícone de escrita prolific classe de anfitrião](./media/user-guide/usbx-events/image173.png)    | **Escrita Prolific classe de anfitrião** *(ux_host_class_prolific_write)* |
| ![Ícone ativar o armazenamento da classe do anfitrião](./media/user-guide/usbx-events/image174.png)    | **Ativar o armazenamento da classe do anfitrião** *(ux_host_class_storage_activate)* |
| ![Ícone de desativação de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image175.png)    | **Desativação do armazenamento da classe hospedeira** *(ux_host_class_storage_deactivate)* |
| ![Classe anfitrião armazenamento capacidade de mídia obter ícone](./media/user-guide/usbx-events/image176.png)    | **Capacidade de mídia de armazenamento de classe de anfitrião obter** *(ux_host_class_storage_media_capacity_get)* |
| ![Grupo de anfitrião armazenamento de armazenamento de capacidade obter ícone](./media/user-guide/usbx-events/image177.png)    | **Capacidade de formato de mídia de armazenamento de classe de anfitrião obter** *(ux_host_class_storage_media_format_capacity_get)* |
| ![Ícone de montagem de mídia de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image178.png)    | **Montagem de mídia de armazenamento de classe de anfitrião** (ux_host_class_storage_media_mount)* |
| ![Ícone de mídia de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image179.png)    | **Classe de anfitrião Armazenamento Media Open** *(ux_host_class_storage_media_open)* |
| ![Ícone de leitura de mídia de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image180.png)    | **Leitura de mídia de armazenamento de classe de anfitrião** *(ux_host_class_storage_media_read)* |
| ![Ícone de mídia de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image181.png)    | **Escrita de mídia de armazenamento de classe de anfitrião** *(ux_host_class_storage_media_write)* |
| ![Ícone de pedido de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image182.png)    | **Sentido do pedido de armazenamento da classe de anfitrião** *(ux_host_class_storage_request_sense)* |
| ![Ícone de paragem de início de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image183.png)    | **Paragem de início de armazenamento de classe de anfitrião** *(ux_host_class_storage_start_stop)* |
| ![Ícone de teste pronto da unidade de armazenamento da classe do anfitrião](./media/user-guide/usbx-events/image184.png)    | **Teste pronto da unidade de armazenamento da unidade de armazenamento da classe de anfitrião** *(ux_host_class_storage_activate)* |
| ![Série de anfitrião exemplo criar ícone](./media/user-guide/usbx-events/image185.png)    | **Série de anfitrião Classe De Exemplo Criar** *(ux_host_stack_class_instance_create)* |
| ![Ícone de destruição de classe de classe de pilha de anfitrião](./media/user-guide/usbx-events/image186.png)    | **Exemplo de classe de pilha de anfitrião destruir** *(ux_host_stack_class_instance_destroy)* |
| ![Ícone de configuração de pilha de anfitrião Eliminar](./media/user-guide/usbx-events/image187.png)    | **Configuração de pilha de anfitrião Eliminar** *(ux_host_stack_configuration_delete)* |
| ![Ícone de enumeração de configuração de pilha de anfitrião](./media/user-guide/usbx-events/image188.png)    | **Enumeração de configuração da pilha de anfitrião** *(ux_host_stack_configuration_enumerate)* |
| ![Exemplo de configuração de pilha de anfitrião Criar ícone](./media/user-guide/usbx-events/image189.png)    | **Série de configuração do anfitrião Criar** *(ux_host_stack_configuration_instance_create)* |
| ![Exemplo de configuração de pilha de anfitrião Eliminar ícone](./media/user-guide/usbx-events/image190.png)    | **Exemplo de configuração da pilha de anfitrião Eliminar** *(ux_host_stack_configuration_instance_delete)* |
| ![Ícone de conjunto de configuração de pilha de anfitrião](./media/user-guide/usbx-events/image191.png)    | **Conjunto de configuração da pilha de** *anfitrião (ux_host_stack_configuration_set)* |
| ![Ícone de conjunto de endereço de dispositivo de pilha de anfitrião](./media/user-guide/usbx-events/image192.png)    | **Conjunto de endereços do dispositivo de pilha de anfitrião** *(ux_host_stack_device_set)* |
| ![Configuração do dispositivo de pilha de anfitrião Obter ícone](./media/user-guide/usbx-events/image193.png)    | **Configuração do dispositivo de pilha de anfitrião obter** *(ux_host_stack_device_configuration_get)* |
| ![Ícone de configuração do dispositivo de pilha de anfitrião](./media/user-guide/usbx-events/image194.png)    | **Seleção de configuração do dispositivo de pilha de anfitrião** *(ux_host_stack_device_configuration_select)* |
| ![Ícone de leitura de dispositivo de pilha de anfitrião](./media/user-guide/usbx-events/image195.png)    | **Leitura do descritor do dispositivo** de pilha de *anfitrião (ux_host_stack_device_descriptor_read)* |
| ![Dispositivo de pilha de anfitrião obter ícone](./media/user-guide/usbx-events/image196.png)    | **Dispositivo de pilha de anfitrião obter** (ux_host_stack_device_get) |
| ![Ícone de remover dispositivo de pilha de anfitrião](./media/user-guide/usbx-events/image197.png)    | **Remover dispositivo de pilha de anfitrião** (ux_host_stack_device_get) |
| ![Ícone livre de recursos do dispositivo de pilha de anfitrião](./media/user-guide/usbx-events/image198.png)    | **Dispositivo de pilha de anfitrião livre** (ux_host_stack_device_resource_free) |
| ![Exemplo de ponto final de pilha de anfitrião Criar ícone](./media/user-guide/usbx-events/image199.png)    | **Host Stack Endpoint Instance Create** (ux_host_stack_endpoint_instance_create) |
| ![Exemplo de endpoint de pilha de anfitrião Eliminar ícone](./media/user-guide/usbx-events/image200.png)    | **Série de anfitrião Endpoint Instance Delete** (ux_host_stack_endpoint_instance_delete) |
| ![Ícone de reset do ponto final do host Stack](./media/user-guide/usbx-events/image201.png)    | **Reset do ponto final da pilha de anfitrião** (ux_host_stack_endpoint_reset) |
| ![Ícone de aborto de transferência de ponto final de pilha de anfitrião](./media/user-guide/usbx-events/image202.png)    | **Abortar a transferência de ponto final do host Stack** (ux_host_stack_endpoint_transfer_abort) |
| ![Ícone do controlador do anfitrião do anfitrião do anfitrião](./media/user-guide/usbx-events/image203.png)    | **Registo do controlador do anfitrião** host stack *(ux_host_stack_hcd_register)* |
| ![Ícone inicialize da pilha de anfitrião](./media/user-guide/usbx-events/image204.png)    | **Inicialize da pilha de anfitriões** *(ux_host_stack_initialize)* |
| ![Anfitrião Stack Interface Endpoint Obter ícone](./media/user-guide/usbx-events/image205.png)    | **Host Stack Interface Endpoint Get** *(ux_host_stack_interface_endpoint_get)* |
| ![Exemplo de interface de pilha de anfitrião Criar ícone](./media/user-guide/usbx-events/image206.png)    | **Série de série de anfitriões Criar** *(ux_host_stack_interface_instance_create)* |
| ![Exemplo de interface de pilha de anfitrião Eliminar ícone](./media/user-guide/usbx-events/image207.png)    | **Excluir a interface da interface da pilha de anfitrião** *(ux_host_stack_interface_instance_delete)* |
| ![Ícone de conjunto de interface de pilha de anfitrião](./media/user-guide/usbx-events/image208.png)    | **Conjunto de interface de pilha de anfitrião** *(ux_host_stack_interface_set)* |
| ![Configuração de configuração da interface de pilha de anfitrião Selecionar ícone](./media/user-guide/usbx-events/image209.png)    | **Seleção de definição de interface de pilha de anfitrião** *(ux_host_stack_interface_setting_select)* |
| ![Host Stack Nova Configuração Criar ícone](./media/user-guide/usbx-events/image210.png)    | **Host Stack Nova Configuração Criar** *(ux_host_stack_new_configuration_create)* |
| ![Host Stack novo dispositivo criar ícone](./media/user-guide/usbx-events/image211.png)    | **Host Stack Novo Dispositivo Criar** *(ux_host_stack_new_device_create)* |
| ![Host Stack Novo Ponto Final Criar ícone](./media/user-guide/usbx-events/image212.png)    | **Host Stack New Endpoint Create** *(ux_host_stack_new_endpoint_create)* |
| ![Ícone de mudança de fundo de raiz de pilha de anfitrião](./media/user-guide/usbx-events/image213.png)    | **Processo de mudança do hub de raiz da pilha de anfitrião** *(ux_host_stack_rh_change_process)* |
| ![Ícone de extração de dispositivo de raiz de pilha de anfitrião](./media/user-guide/usbx-events/image214.png)    | **Hospedar stack raiz de raiz de extração do dispositivo** *(ux_host_stack_rh_device_extraction)* |
| ![Ícone de inserção do dispositivo de inserção do hub de raiz da pilha de anfitrião](./media/user-guide/usbx-events/image215.png)    | **Inserção do dispositivo do cubo de raiz** do bloco de *pilhas de anfitrião (ux_host_stack_rh_device_insertion)* |
| ![Ícone de pedido de transferência de pilha de anfitrião](./media/user-guide/usbx-events/image216.png)    | **Pedido de transferência de pilha de anfitrião** *(ux_host_stack_transfer_request)* |
| ![Ícone de aborto de pedido de transferência de pilha de anfitrião](./media/user-guide/usbx-events/image217.png)    | **Pedido de transferência de pilha de anfitrião Abortar** *(ux_host_stack_transfer_request_abort)* |
| ![Ícone de erro U S B X](./media/user-guide/usbx-events/image218.png)    | **Erro USBX** *(ux_error)* |

## <a name="event-descriptions"></a>Descrições do evento

As páginas seguintes descrevem os eventos usbx trace.

### <a name="device-class-cdc-activate"></a>Dispositivo Classe Cdc Ativar 

#### <a name="ux_device_class_cdc_activate"></a>ux_device_class_cdc_activate

**Ícone** ![ Ícone ativar classe C D C C do dispositivo](./media/user-guide/usbx-events/image1.png)

**Descrição**

Este evento representa um evento usbx device Class Cdc Activate Event.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-cdc-deactivate"></a>Desativar a classe de dispositivos CDC 

#### <a name="ux_device_class_cdc_deactivate"></a>ux_device_class_cdc_deactivate

**Ícone** ![ Ícone desativado classe C D C C](./media/user-guide/usbx-events/image2.png)

**Descrição**

Este evento representa um CDC desativado da classe de dispositivo USBX.

Campos de Informação 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-cdc-read"></a>Leitura do Cdc classe de dispositivo 

#### <a name="ux_device_class_cdc_read"></a>ux_device_class_cdc_read

**Ícone** ![ Ícone de leitura classe C D C do dispositivo](./media/user-guide/usbx-events/image3.png)

**Descrição**

Este evento representa um Evento de Leitura cdc classe de dispositivo USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Ponteiro de dados.
- Info Field 3: Comprimento solicitado.
- Info Field 4: Não utilizado.

### <a name="device-class-cdc-write"></a>Escrita de cdc classe de dispositivo 

#### <a name="ux_device_class_cdc_write"></a>ux_device_class_cdc_write

**Ícone** ![ Ícone de escrita classe C D C do dispositivo](./media/user-guide/usbx-events/image4.png)

**Descrição**

Este evento representa um evento de escrita cdc classe de dispositivo USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Ponteiro de dados.
- Info Field 3: Comprimento solicitado.
- Info Field 4: Não utilizado.

### <a name="device-class-dpump-activate"></a>Ativar classe de dispositivo 

#### <a name="ux_device_class_dpump_activate"></a>ux_device_class_dpump_activate

**Ícone** ![ Ícone ativar classe de dispositivo](./media/user-guide/usbx-events/image5.png)

**Descrição**

Este evento representa um evento ativado da classe de dispositivo USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-dpump-deactivate"></a>Classe de dispositivo Dpump Desativar 

#### <a name="ux_device_class_dpump_deactivate"></a>ux_device_class_dpump_deactivate

**Ícone** ![ Ícone de desativado da classe de dispositivo Dpump](./media/user-guide/usbx-events/image6.png)

**Descrição**

Este evento representa um evento de desativado da classe de dispositivo USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-dpump-read"></a>Leitura de Classe de Dispositivo 

#### <a name="ux_device_class_dpump_read"></a>ux_device_class_dpump_read

**Ícone** ![ Ícone de leitura de classe de dispositivo](./media/user-guide/usbx-events/image7.png)

**Descrição**

Este evento representa um Evento de Leitura de Dpump da Classe dispositivo USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Buffer.
- Info Field 3: Comprimento solicitado.
- Info Field 4: Não utilizado.

### <a name="device-class-dpump-write"></a>Escrita de Classe de Dispositivo Dpump 

#### <a name="ux_device_class_dpump_write"></a>ux_device_class_dpump_write

**Ícone** ![ Ícone de escrita de classe de dispositivo](./media/user-guide/usbx-events/image8.png)

**Descrição**

Este evento representa um evento de escrita classe de dispositivo USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Ponteiro de dados.
- Info Field 3: Comprimento solicitado.
- Info Field 4: Não utilizado.

### <a name="device-class-hid-activate"></a>Classe de dispositivo Hid Ativar 

#### <a name="ux_device_class_hid_activate"></a>ux_device_class_hid_activate

**Ícone** ![ Ícone ativar classe de dispositivo Hid](./media/user-guide/usbx-events/image9.png)

**Descrição**

Este evento representa um evento USBX Device Class Hid Activate Event.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-hid-deactivate"></a>Classe de dispositivo Hid Desativado 

#### <a name="ux_device_class_hid_deactivate"></a>ux_device_class_hid_deactivate

**Ícone** ![ Ícone de desativado classe de dispositivo Hid](./media/user-guide/usbx-events/image10.png)

**Descrição**

Este evento representa um evento de desativado da classe de dispositivo USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-hid-descriptor-send"></a>Classe de dispositivo Hid Descriptor Enviar 

#### <a name="ux_device_class_hid_descritpor_send"></a>ux_device_class_hid_descritpor_send

**Ícone** ![ Classe de dispositivo hiddscriptor Enviar ícone](./media/user-guide/usbx-events/image11.png)

**Descrição**

Este evento representa um evento de envio de dispositivo USBX Classe Oculta.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Tipo de descritor.
- Info Field 3: Índice de pedido.
- Info Field 4: Não utilizado.

### <a name="device-class-hid-event-get"></a>Evento de classe de dispositivo Hid Obter 

#### <a name="ux_device_class_hid_event_get"></a>ux_device_class_hid_event_get

**Ícone** ![ Classe de dispositivo hid evento obter ícone](./media/user-guide/usbx-events/image12.png)

**Descrição**

Este evento representa um evento usbx device class hid event.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-hid-event-set"></a>Conjunto de eventos de classe de dispositivos hid 

#### <a name="ux_device_class_hid_event_set"></a>ux_device_class_hid_event_set

**Ícone** ![ Ícone de conjunto de evento de classe de dispositivo hid](./media/user-guide/usbx-events/image13.png)

**Descrição**

Este evento representa um conjunto de eventos hid classe de dispositivo USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-hid-report-get"></a>Relatório hid da classe do dispositivo obter 

#### <a name="ux_device_class_hid_report_get"></a>ux_device_class_hid_report_get

**Ícone** ![ Relatório hid classe de dispositivo obter ícone](./media/user-guide/usbx-events/image14.png)

**Descrição**

Este evento representa um evento usbx device class hid report.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Tipo de descritor.
- Info Field 3: Índice de pedido.
- Info Field 4: Não utilizado.

### <a name="device-class-hid-report-set"></a>Conjunto de relatório de hid classe de dispositivo 

#### <a name="ux_device_class_hid_report_set"></a>ux_device_class_hid_report_set

**Ícone** ![ Ícone de conjunto de relatório de classe de dispositivo hid](./media/user-guide/usbx-events/image15.png)

**Descrição**

Este evento representa um evento usbx device Class Hid Report Event.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Tipo de descritor.
- Info Field 3: Índice de pedido.
- Info Field 4: Não utilizado.

### <a name="device-class-pima-activate"></a>Classe de dispositivo Pima Ativar

#### <a name="ux_device_class_pima_activate"></a>ux_device_class_pima_activate

**Ícone** ![ Ícone de ativação classe de dispositivo Pima](./media/user-guide/usbx-events/image16.png)

**Descrição**

Este evento representa um evento de ativação Pima da classe de dispositivo USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-pima-deactivate"></a>Classe de dispositivo Pima Desativar 

#### <a name="ux_device_class_pima_deactivate"></a>ux_device_class_pima_deactivate

**Ícone** ![ Ícone de desativado classe de dispositivo Pima](./media/user-guide/usbx-events/image17.png)

**Descrição**

Este evento representa um evento de desativado Pima da classe de dispositivo USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-pima-device-info-send"></a>Informações de dispositivo classe de dispositivo Pima enviar 

#### <a name="ux_device_class_pima_device_info_send"></a>ux_device_class_pima_device_info_send

**Ícone** ![ Informação de envio de dispositivo classe de dispositivo Pima classe de dispositivo](./media/user-guide/usbx-events/image18.png)

**Descrição**

Este evento representa um evento de envio de info dispositivo pima classe USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.

### <a name="device-class-pima-event-get"></a>Evento Pima classe de dispositivo obter 

#### <a name="ux_device_class_pima_event_get"></a>ux_device_class_pima_event_get

**Ícone** ![ Evento Pima classe de dispositivo Obter ícone](./media/user-guide/usbx-events/image19.png)

**Descrição**

Este evento representa um evento de evento Pima classe de dispositivo USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Evento Pima.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-pima-event-set"></a>Conjunto de eventos classe de dispositivo Pima 

#### <a name="ux_device_class_pima_event_set"></a>ux_device_class_pima_event_set

**Ícone** ![ Ícone de conjunto de evento classe de dispositivo Pima](./media/user-guide/usbx-events/image20.png)

**Descrição**

Este evento representa um evento de conjunto de eventos Pima classe de dispositivo USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Evento Pima.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-pima-object-add"></a>Adicionar objeto pima classe de dispositivo 

#### <a name="ux_device_class_pima_object_add"></a>ux_device_class_pima_object_add

**Ícone** ![ Ícone de adicionar objeto classe de dispositivo Pima](./media/user-guide/usbx-events/image21.png)

**Descrição**

Este evento representa um evento de adição de objetos Pima da classe de dispositivo USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Pega do objeto.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-pima-object-data-get"></a>Dados de objetos de classe de dispositivo Pima obtêm 

#### <a name="ux_device_class_pima_object_data_get"></a>ux_device_class_pima_object_data_get

**Ícone** ![ Dados de objeto de classe de dispositivo Pima Obter ícone](./media/user-guide/usbx-events/image22.png)

**Descrição**

Este evento representa um evento de dados de objetos Pima da classe de dispositivo USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Pega do objeto.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-pima-object-data-send"></a>Dados de objetos de classe de dispositivo Pima enviar 

#### <a name="ux_device_class_pima_object_data_send"></a>ux_device_class_pima_object_data_send

**Ícone** ![ Dados de objeto de classe de dispositivo Pima Enviar ícone](./media/user-guide/usbx-events/image23.png)

**Descrição**

Este evento representa um evento de envio de dados de objetos de dispositivo USBX Pima.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Pega do objeto.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-pima-object-delete"></a>Classificação de dispositivo Pima Objeto Delete 

#### <a name="ux_device_class_pima_object_delete"></a>ux_device_class_pima_object_delete

**Ícone** ![ Ícone de eliminação de objeto de classe de dispositivo Pima](./media/user-guide/usbx-events/image24.png)

**Descrição**

Este evento representa um evento de eliminação de objetos Pima da classe usbx.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Pega do objeto.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-pima-object-handles-send"></a>Dispositivo classe Pima objeto handles enviar 

#### <a name="ux_device_class_pima_object_handles_send"></a>ux_device_class_pima_object_handles_send

**Ícone** ![ Alças de objeto classe de dispositivo Pima Enviar ícone](./media/user-guide/usbx-events/image25.png)

**Descrição**

Este evento representa um evento de envio de objetos de dispositivo USBX Classe Pima.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: ID de armazenamento.
- Info Field 3: Código de formato de objeto.
- Info Field 4: Associação de objetos.

### <a name="device-class-pima-object-info-get"></a>Informações de objeto pima classe de dispositivo obter 

#### <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

**Ícone** ![ Classe de dispositivo Pima Objeto Info Obter ícone](./media/user-guide/usbx-events/image26.png)

**Descrição**

Este evento representa um evento USBX Device Class Pima Object Info Get.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Pega do objeto.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-pima-object-info-send"></a>Informações de objetos de classe de dispositivo Pima enviar 

#### <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

**Ícone** ![ Classe de dispositivo Pima Objeto Info Enviar ícone](./media/user-guide/usbx-events/image27.png)

**Descrição**

Este evento representa um evento de envio de informação de objeto pima classe USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-pima-objects-number-send"></a>Número de objetos de classe de dispositivo Pima Enviar 

#### <a name="ux_device_class_pima_object_number_send"></a>ux_device_class_pima_object_number_send

**Ícone** ![ Número de objetos de classe de dispositivo Pima Enviar ícone](./media/user-guide/usbx-events/image28.png)

**Descrição**

Este evento representa um evento usbx device Class Pima Object Send.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: ID de armazenamento.
- Info Field 3: Código de formato de objeto.
- Info Field 4: Associado de objetos.

### <a name="device-class-pima-partial-object-data-get"></a>Dados de objeto parcial classe de dispositivo Pima obter

#### <a name="ux_device_class_pima_partial_object_data_get"></a>ux_device_class_pima_partial_object_data_get

**Ícone** ![ Classe de dispositivo Pima Objeto Parcial Objeto Dados Obter ícone](./media/user-guide/usbx-events/image29.png)

**Descrição**

Este evento representa um evento de dados de objeto parcial da classe USBX Pima.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Pega do objeto.
- Info Field 3: Offset solicitado.
- Info Field 4: Comprimento solicitado.

### <a name="device-class-pima-response-send"></a>Envio de resposta classe de dispositivo Pima 

#### <a name="ux_device_class_pima_response_send"></a>ux_device_class_pima_response_send

**Ícone** ![ Ícone de resposta pima classe de dispositivo](./media/user-guide/usbx-events/image30.png)

**Descrição**

Este evento representa um evento de envio de resposta Pima classe de dispositivo USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Campo 2: Código de resposta.
- Info Campo 3: Parâmetro de número.
- Info Campo 4: Parâmetro Pima 1.

### <a name="device-class-pima-storage-id-send"></a>Envio de armazenamento classe de dispositivo Pima 

#### <a name="ux_device_class_pima_storage_id_send"></a>ux_device_class_pima_storage_id_send

**Ícone** ![ Id de armazenamento classe de dispositivo Pima Enviar ícone](./media/user-guide/usbx-events/image31.png)

**Descrição**

Este evento representa um evento de envio de Id de armazenamento Pima classe de dispositivo USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-pima-storage-info-send"></a>Informações de armazenamento classe de dispositivo Pima enviar 

#### <a name="ux_device_class_pima_storage_info_send"></a>ux_device_class_pima_storage_info_send

**Ícone** ![ Classe de dispositivo Pima Storage Info Enviar ícone](./media/user-guide/usbx-events/image32.png)

**Descrição**

Este evento representa um evento de envio de info de armazenamento Pima classe usbx.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-rndis-activate"></a>Dispositivo Classe Rndis Ativar 

#### <a name="ux_device_class_rndis_activate"></a>ux_device_class_rndis_activate

**Ícone** ![ Ícone de ativação classe de dispositivo Rndis](./media/user-guide/usbx-events/image33.png)

**Descrição**

Este evento representa um evento ativado da classe de dispositivo USBX Rndis.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-rndis-deactivate"></a>Classe de dispositivo Rndis Desativar 

#### <a name="ux_device_class_rndis_deactivate"></a>ux_device_class_rndis_deactivate

**Ícone** ![ Ícone de desativado classe de dispositivo Rndis](./media/user-guide/usbx-events/image34.png)

**Descrição**

Este evento representa um evento de desativado da classe de dispositivo USBX Rndis.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-rndis-message-keep-alive"></a>Mensagem Rndis classe de dispositivo manter vivo 

#### <a name="ux_device_class_rndis_msg_keep_alive"></a>ux_device_class_rndis_msg_keep_alive

**Ícone** ![ Ícone de mensagem Rndis classe de dispositivo Manter vivo](./media/user-guide/usbx-events/image35.png)

**Descrição**

Este evento representa um evento de mensagem Rndis da classe de dispositivo USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-rndis-message-query"></a>Consulta de mensagens classe de dispositivo Rndis 

#### <a name="ux_device_class_rndis_msg_keep_query"></a>ux_device_class_rndis_msg_keep_query

**Ícone** ![ Ícone de consulta de mensagem classe de dispositivo Rndis](./media/user-guide/usbx-events/image36.png)

**Descrição**

Este evento representa um evento de consulta de mensagens classe DE dispositivo USBX Rndis.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Rndis OID.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-rndis-message-reset"></a>Reset da mensagem Rndis da classe do dispositivo 

#### <a name="ux_device_class_rndis_msg_reset"></a>ux_device_class_rndis_msg_reset

**Ícone** ![ Ícone de reset de mensagem de classe de dispositivo Rndis](./media/user-guide/usbx-events/image37.png)

**Descrição**

Este evento representa um evento de reset de mensagens da classe de dispositivo USBX Rndis.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.

### <a name="device-class-rndis-message-set"></a>Conjunto de mensagens Rndis classe de dispositivo 

#### <a name="ux_device_class_rndis_msg_set"></a>ux_device_class_rndis_msg_set

**Ícone** ![ Ícone de conjunto de mensagem de classe de dispositivo Rndis](./media/user-guide/usbx-events/image38.png)

**Descrição**

Este evento representa um evento usbx device Class Rndis Message set Event.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Rndis OID.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-rndis-packet-receive"></a>Pacote classe de dispositivo Rndis Receber 

#### <a name="ux_device_class_rndis_packet_receive"></a>ux_device_class_rndis_packet_receive

**Ícone** ![ Ícone de receção de pacote classe de dispositivo Rndis](./media/user-guide/usbx-events/image39.png)

**Descrição**

Este evento representa um evento de receção de pacote de pacote classe USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-rndis-packet-transmit"></a>Transmitir pacote de pacote classe de dispositivo Rndis 

#### <a name="ux_device_class_rndis_packet_transmit"></a>ux_device_class_rndis_packet_transmit

**Ícone** ![ Ícone de transmissão de pacote de pacote classe de dispositivo Rndis](./media/user-guide/usbx-events/image40.png)

**Descrição**

Este evento representa um evento de transmissão de pacotes de pacotes usbx classe Rndis.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-storage-activate"></a>Ativação de armazenamento de classe de dispositivo 

#### <a name="ux_device_class_storage_activate"></a>ux_device_class_storage_activate

**Ícone** ![ Ícone ativar o armazenamento da classe do dispositivo](./media/user-guide/usbx-events/image41.png)

**Descrição**

Este evento representa um evento usbx device class storage activate Event.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-storage-deactivate"></a>Armazenamento de classe de dispositivo desativado 

#### <a name="ux_device_class_storage_deactivate"></a>ux_device_class_storage_deactivate

**Ícone** ![ Ícone de desativação de classe de dispositivo](./media/user-guide/usbx-events/image42.png)

**Descrição**

Este evento representa um evento de desativação da classe de dispositivo USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-storage-format"></a>Formato de armazenamento de classe de dispositivo 

#### <a name="ux_device_class_storage_format"></a>ux_device_class_storage_format

**Ícone** ![ Ícone de formato de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image43.png)

**Descrição**

Este evento representa um evento de formato de armazenamento de classe de dispositivo USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Lun.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-storage-inquiry"></a>Inquérito de armazenamento de classe de dispositivo 

#### <a name="ux_device_class_storage_inquiry"></a>ux_device_class_storage_inquiry

**Ícone** ![ Ícone de inquérito de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image44.png)

**Descrição**

Este evento representa um evento de investigação de armazenamento de classe de dispositivo USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Lun.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-storage-mode-select"></a>Selecione o modo de armazenamento da classe do dispositivo

#### <a name="ux_device_class_storage_mode_select"></a>ux_device_class_storage_mode_select

**Ícone** ![ Modo de armazenamento de classe de dispositivo Selecionar ícone](./media/user-guide/usbx-events/image45.png)

**Descrição**

Este evento representa um evento de seleção do modo de armazenamento da classe do dispositivo USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Lun.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-storage-mode-sense"></a>Sentido do modo de armazenamento da classe do dispositivo 

#### <a name="ux_device_class_storage_mode_sense"></a>ux_device_class_storage_mode_sense

**Ícone** ![ Ícone de sentido de modo de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image46.png)

**Descrição**

Este evento representa um evento de modo de armazenamento de classe de dispositivo USBX.

Campos de Informação 

- nfo Field 1: Exemplo de classe.
- Info Field 2: Lun.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-storage-prevent-allow-media-removal"></a>Armazenamento de classe de dispositivo impede a remoção dos meios de comunicação 

#### <a name="ux_device_class_storage_prevent_allow_media_removal"></a>ux_device_class_storage_prevent_allow_media_removal

**Ícone** ![ Armazenamento de classe de dispositivo Previne permitir ícone de remoção de mídia](./media/user-guide/usbx-events/image47.png)

**Descrição**

Este evento representa um armazenamento da classe do dispositivo USBX Prevent Allow Media Removal Event.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Lun.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-storage-read"></a>Leitura de armazenamento de classe de dispositivo 

#### <a name="ux_device_class_storage_read"></a>ux_device_class_storage_read

**Ícone** ![ Ícone de leitura de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image48.png)

**Descrição**

Este evento representa um evento de leitura de armazenamento de classe de dispositivo USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Lun.
- Campo de Informação 3: Sector.
- Info Field 4: Sectores numerais.

### <a name="device-class-storage-read-capacity"></a>Capacidade de leitura de armazenamento de classe de dispositivo 

#### <a name="ux_device_class_storage_read_capacity"></a>ux_device_class_storage_read_capacity

**Ícone** ![ Ícone de capacidade de leitura de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image49.png)

**Descrição**

Este evento representa um evento de capacidade de leitura de armazenamento de classe de dispositivo USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Lun.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-storage-read-format-capacity"></a>Capacidade de leitura de formato de leitura de classe de dispositivo 

#### <a name="ux_device_class_storage_read_format_capacity"></a>ux_device_class_storage_read_format_capacity

**Ícone** ![ Ícone de capacidade de leitura de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image50.png)

**Descrição**

Este evento representa um evento de capacidade de leitura de armazenamento de classe de dispositivo USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Lun.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-storage-read-toc"></a>Armazenamento de classe de dispositivo Leia TOC 

#### <a name="ux_device_class_storage_read_toc"></a>ux_device_class_storage_read_toc

**Ícone** ![ Armazenamento de classe de dispositivo Leia o ícone TOC](./media/user-guide/usbx-events/image51.png)

**Descrição**

Este evento representa um evento DE ARMAZENAMENTO DE CLASSE USBX De Dispositivo Leia O EVENTO TOC.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Lun.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-storage-request-sense"></a>Sentido do pedido de armazenamento de classe de dispositivo 

#### <a name="ux_device_class_storage_request_sense"></a>ux_device_class_storage_request_sense

**Ícone** ![ Ícone de pedido de pedido de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image52.png)

**Descrição**

Este evento representa um evento de pedido de armazenamento de classe de dispositivo USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Lun.
- Info Field 3: Chave de sentido.
- Info Field 4: Código.

### <a name="device-class-storage-start-stop"></a>Paragem de início de armazenamento de classe de dispositivo 

#### <a name="ux_device_class_storage_start_stop"></a>ux_device_class_storage_start_stop

**Ícone** ![ Ícone de início de paragem de armazenamento de classe de dispositivo](./media/user-guide/usbx-events/image53.png)

**Descrição**

Este evento representa um evento de paragem de início de armazenamento da classe de dispositivo USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Lun.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-storage-test-ready"></a>Teste de armazenamento de classe de dispositivo pronto 

#### <a name="ux_device_class_storage_test_ready"></a>ux_device_class_storage_test_ready

**Ícone** ![ Ícone de teste de armazenamento de classe de dispositivo pronto](./media/user-guide/usbx-events/image54.png)

**Descrição**

Este evento representa um evento pronto para o teste de armazenamento da classe de dispositivo USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Lun.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-storage-verify"></a>Armazenamento de classe de dispositivo Verificar 

#### <a name="ux_device_class_storage_verify"></a>ux_device_class_storage_verify

**Ícone** ![ Ícone de verificação de classe de dispositivo](./media/user-guide/usbx-events/image55.png)

**Descrição**

Este evento representa um evento de verificação da classe de dispositivo USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Lun.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-class-storage-write"></a>Escrita de armazenamento de classe de dispositivo 

#### <a name="ux_device_class_storage_write"></a>ux_device_class_storage_write

**Ícone** ![ Ícone de escrita de classe de dispositivo](./media/user-guide/usbx-events/image56.png)

**Descrição**

Este evento representa um evento de escrita de classe de dispositivo USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Lun.
- Campo de Informação 3: Sector.
- Info Field 4: Sectores numerais.

### <a name="device-stack-alternate-setting-get"></a>Configuração alternativa de pilha de dispositivo obter 

#### <a name="ux_device_class_alternate_setting_get"></a>ux_device_class_alternate_setting_get

**Ícone** ![ Configuração alternativa de pilha de dispositivo Obter ícone](./media/user-guide/usbx-events/image57.png)

**Descrição**

Este evento representa um evento de configuração alternativa de configuração alternativa de pilha de dispositivo USBX.

**Campos de Informação**

- Info Field 1: Valor da interface.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-stack-alternate-setting-set"></a>Conjunto de definição alternativa de pilha de dispositivo 

#### <a name="ux_device_class_alternate_setting_set"></a>ux_device_class_alternate_setting_set

**Ícone** ![ Ícone de definição alternativa de configuração de pilha de dispositivo](./media/user-guide/usbx-events/image58.png)

**Descrição**

Este evento representa um evento de definição alternativa de pilha de dispositivo USBX.

**Campos de Informação**
- Info Field 1: Valor da interface.
- Info Field 2: Valor de definição alternativo.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-stack-class-register"></a>Registo de classe de pilha de dispositivo 

#### <a name="ux_device_stack_class_register"></a>ux_device_stack_class_register

**Ícone** ![ Ícone de registo de classe de pilha de dispositivo](./media/user-guide/usbx-events/image59.png)

**Descrição**

Este evento representa um evento usbx device stack class register Event.

**Campos de Informação**

- Info Field 1: Nome da classe.
- Info Field 2: Número de interface.
- Info Field 3: Parâmetro.
- Info Field 4: Não utilizado.

### <a name="device-stack-clear-feature"></a>Recurso de limpar a pilha de dispositivos 

#### <a name="ux_device_stack_clear_feature"></a>ux_device_stack_clear_feature

**Ícone** ![ Ícone de funcionalidade de limpação de pilha de dispositivo](./media/user-guide/usbx-events/image60.png)

**Descrição**

Este evento representa um evento de funcionalidade limpa de pilha de dispositivo USBX.

**Campos de Informação**

- Informação Campo 1: Tipo de pedido.
- Informação Campo 2: Valor de pedido. Info Field 3: Índice de pedido.
- Info Field 4: Não utilizado.

### <a name="device-stack-configuration-get"></a>Configuração de pilha de dispositivo obter 

#### <a name="ux_device_stack_configuration_get-t"></a>ux_device_stack_configuration_get t

**Ícone** ![ Configuração de pilha de dispositivo Obter ícone](./media/user-guide/usbx-events/image61.png)

**Descrição**

Este evento representa um evento de configuração de pilha de dispositivo USBX.

**Campos de Informação** 

- Info Field 1: Valor de configuração.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-stack-configuration-set"></a>Conjunto de configuração de pilha de dispositivo 

#### <a name="ux_device_stack_configuration_set"></a>ux_device_stack_configuration_set

**Ícone** ![ Ícone de conjunto de configuração de pilha de dispositivo](./media/user-guide/usbx-events/image62.png)

**Descrição**

Este evento representa um evento de configuração de configuração de pilha de dispositivo USBX.

**Campos de Informação** 

- Info Field 1: Valor de configuração.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-stack-connect"></a>Ligação de pilha de dispositivo 

#### <a name="ux_device_stack_connect"></a>ux_device_stack_connect

**Ícone** ![ Ícone de conexão de pilha de dispositivo](./media/user-guide/usbx-events/image63.png)

**Descrição**

Este evento representa um evento de envio de pilha de dispositivo USBX.

**Campos de Informação**

- Info Field 1: Não utilizado.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-stack-descriptor-send"></a>Envio de descritor de pilha de dispositivo 

#### <a name="ux_device_stack_descriptor_send"></a>ux_device_stack_descriptor_send

**Ícone** ![ Descritor de pilha de dispositivo Enviar ícone](./media/user-guide/usbx-events/image64.png)

**Descrição**

Este evento representa um evento de envio de pilha de dispositivo USBX.

**Campos de Informação**

- Info Field 1: Tipo de descritor.
- Info Field 2: Índice de pedido.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-stack-disconnect"></a>Desconexão da pilha de dispositivo 

#### <a name="ux_device_stack_disconnect"></a>ux_device_stack_disconnect

**Ícone** ![ Ícone de desconexão de pilha de dispositivo](./media/user-guide/usbx-events/image65.png)

**Descrição**

Este evento representa um evento de desconexão de pilhas de dispositivos USBX.

**Campos de Informação**

- Info Field 1: Dispositivo.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-stack-endpoint-stall"></a>Dispositivo Stack Endpoint Stall 

#### <a name="ux_device_stack_endpoint_stall"></a>ux_device_stack_endpoint_stall

**Ícone** ![ Ícone de ponto final de pilha de dispositivo](./media/user-guide/usbx-events/image66.png)

**Descrição**

Este evento representa um evento de final de dispositivo USBX Stack.

**Campos de Informação** 

- Info Field 1: Ponto final.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-stack-get-status"></a>Estado da pilha de dispositivos 

#### <a name="ux_device_stack_get_status"></a>ux_device_stack_get_status

**Ícone** ![ Ícone de estado da pilha de dispositivo](./media/user-guide/usbx-events/image67.png)

**Descrição**

Este evento representa um evento usbx device stack get status event.

**Campos de Informação**

- Info Field 1: Não utilizado.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-stack-host-wakeup"></a>Wakeup do anfitrião do dispositivo stack 

#### <a name="ux_device_stack_host_wakeup"></a>ux_device_stack_host_wakeup

**Ícone** ![ Ícone de wakeup do anfitrião do dispositivo stack](./media/user-guide/usbx-events/image68.png)

**Descrição**

Este evento representa um evento de wakeup anfitrião usbx device stack.

**Campos de Informação** 

- Info Field 1: Não utilizado.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-stack-initialize"></a>Stack de dispositivo Inicialize 

#### <a name="ux_device_stack_initialize"></a>ux_device_stack_initialize

**Ícone** ![ Ícone inicialize da pilha de dispositivo](./media/user-guide/usbx-events/image69.png)

**Descrição**

Este evento representa um evento de stack de dispositivo USBX.

**Campos de Informação** 

- Info Field 1: Não utilizado.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-stack-interface-delete"></a>Interface de pilha de dispositivos Eliminar 

#### <a name="ux_device_stack_interface_delete"></a>ux_device_stack_interface_delete

**Ícone** ![ Ícone de eliminação da interface da pilha de dispositivo](./media/user-guide/usbx-events/image70.png)

**Descrição**

Este evento representa um evento de eliminação da interface da stack de dispositivo USBX.

**Campos de Informação**

- Info Field 1: Interface.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-stack-interface-get"></a>Interface de stack de dispositivo obter 

#### <a name="ux_device_stack_interface_get"></a>ux_device_stack_interface_get

**Ícone** ![ Interface de pilha de dispositivo Obter ícone](./media/user-guide/usbx-events/image71.png)

**Descrição**

Este evento representa um evento de interface de stack de dispositivo USBX.

**Campos de Informação** 

- Info Field 1: Valor da interface.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-stack-interface-set"></a>Conjunto de interface de pilha de dispositivo 

#### <a name="ux_device_stack_interface_set"></a>ux_device_stack_interface_set

**Ícone** ![ Ícone de conjunto de interface de pilha de dispositivo](./media/user-guide/usbx-events/image72.png)

**Descrição**

Este evento representa um evento usbx device stack interface set.

**Campos de Informação** 

- Informação Campo 1: Valor de pedido. Info Field 2: Índice de pedido.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-stack-set-feature"></a>Função de conjunto de pilha de dispositivo 

#### <a name="ux_device_stack_set_feature"></a>ux_device_stack_set_feature

**Ícone** ![ Ícone de funcionalidade de conjunto de pilha de dispositivo](./media/user-guide/usbx-events/image73.png)

**Descrição**

Este evento representa um evento de funcionalidade de conjunto de dispositivos USBX.

**Campos de Informação** 

- Informação Campo 1: Valor de pedido. Info Field 2: Índice de pedido.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-stack-transfer-abort"></a>Abortar transferência de pilha de dispositivos 

#### <a name="ux_device_stack_transfer_abort"></a>ux_device_stack_transfer_abort

**Ícone** ![ Ícone de aborto de transferência de pilha de dispositivo](./media/user-guide/usbx-events/image74.png)

**Descrição**

Este evento representa um evento de transferência de pilha de dispositivo USBX.

**Campos de Informação** 

- Info Field 1: Pedido de transferência.
- Info Field 2: Código de conclusão.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-stack-transfer-all-request-abort"></a>Transferência de pilha de dispositivos todos os pedidos abortar 

#### <a name="ux_device_stack_transfer_all_request_abort"></a>ux_device_stack_transfer_all_request_abort

**Ícone** ![ Transferência de pilha de dispositivo todo o ícone de abortar pedido](./media/user-guide/usbx-events/image75.png)

**Descrição**

Este evento representa uma transferência de pilha de dispositivo USBX todos os eventos de abortar pedido.

**Campos de Informação** 

- Info Field 1: Ponto final.
- Info Field 2: Código de conclusão.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="device-stack-transfer-request"></a>Pedido de transferência de pilha de dispositivo 

#### <a name="ux_device_stack_transfer_request"></a>ux_device_stack_transfer_request

**Ícone** ![ Ícone de pedido de transferência de pilha de dispositivo](./media/user-guide/usbx-events/image76.png)

**Descrição**

Este evento representa um Evento de Pedido de Transferência de Pilha de Dispositivo USBX.

**Campos de Informação**

- Info Field 1: Pedido de transferência.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-asix-activate"></a>Classe de anfitrião Asix Ativar 

#### <a name="ux_host_class_asix_activate"></a>ux_host_class_asix_activate

**Ícone** ![ Ícone de ativação classe de anfitrião Asix](./media/user-guide/usbx-events/image77.png)

**Descrição**

Este evento representa uma classe de anfitrião USBX Asix Activate.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-asix-deactivate"></a>Classe hospedeira Asix Desativado 

#### <a name="ux_host_class_asix_deactivate"></a>ux_host_class_asix_deactivate

**Ícone** ![ Ícone de desativado classe anfitrião Asix](./media/user-guide/usbx-events/image78.png)

**Descrição**

Este evento representa um evento de desativado da classe USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-asix-interrupt-notification"></a>Classificação de interrupção da classe anfitrião Asix 

#### <a name="ux_host_class_asix_interrupt_notification"></a>ux_host_class_asix_interrupt_notification

**Ícone** ![ Ícone de notificação de interrupção de classe de anfitrião Asix](./media/user-guide/usbx-events/image79.png)

**Descrição**

Este evento representa um evento de notificação de interrupção da classe USBX Asix.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-asix-read"></a>Classe anfitrião Asix Read 

#### <a name="ux_host_class_asix_read"></a>ux_host_class_asix_read

**Ícone** ![ Ícone de leitura de classe de anfitrião](./media/user-guide/usbx-events/image80.png)

**Descrição**

Este evento representa um evento de leitura da classe anfitrião USBX Asix.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Ponteiro de dados.
- Info Field 3: Comprimento solicitado.
- Info Field 4: Não utilizado.

### <a name="host-class-asix-write"></a>Classe anfitriã Asix Escrever 

#### <a name="ux_host_class_asix_write"></a>ux_host_class_asix_write

**Ícone** ![ Ícone de escrita de classe de anfitrião Asix](./media/user-guide/usbx-events/image81.png)

**Descrição**

Este evento representa um evento de escrita da classe anfitrião USBX Asix.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Ponteiro de dados.
- Info Field 3: Comprimento solicitado.
- Info Field 4: Não utilizado.

### <a name="host-class-audio-activate"></a>Ativação de áudio da classe de anfitrião 

#### <a name="ux_host_class_audio_activate"></a>ux_host_class_audio_activate

**Ícone** ![ Ícone ativar áudio classe anfitrião](./media/user-guide/usbx-events/image82.png)

**Descrição**

Este evento representa um evento USBX Host Class Audio Activate.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-audio-control-value-get"></a>Valor de controlo de áudio da classe do anfitrião obter 

#### <a name="ux_host_class_audio_control_value_get"></a>ux_host_class_audio_control_value_get

**Ícone** ![ Valor de controlo de áudio da classe do anfitrião Obter ícone](./media/user-guide/usbx-events/image83.png)

**Descrição**

Este evento representa um evento USBX Host Class Audio Control Value Get.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-audio-control-value-set"></a>Conjunto de valor de controlo de áudio da classe do anfitrião 

#### <a name="ux_host_class_audio_control_value_set"></a>ux_host_class_audio_control_value_set

**Ícone** ![ Ícone do conjunto de conjunto de valor de controlo de áudio da classe do anfitrião](./media/user-guide/usbx-events/image84.png)

**Descrição**

Este evento representa um evento interno de processamento diferido do piloto NetX I/O.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Controlo de áudio.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-audio-deactivate"></a>Desativar áudio da classe hospedeira 

#### <a name="ux_host_class_audio_deactivate"></a>ux_host_class_audio_deactivate

**Ícone** ![ Ícone de desativado de áudio classe anfitrião](./media/user-guide/usbx-events/image85.png)

**Descrição**

Este evento representa um evento de desativado áudio da classe USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-audio-read"></a>Leitura áudio da classe anfitrião 

#### <a name="ux_host_class_audio_read"></a>ux_host_class_audio_read

**Ícone** ![ Ícone de leitura de áudio de classe de anfitrião](./media/user-guide/usbx-events/image86.png)

**Descrição**

Este evento representa um evento de leitura áudio da classe usbx.

- Campos de Informação 
- Info Field 1: Exemplo de classe.
- Info Field 2: Ponteiro de dados.
- Info Field 3: Comprimento solicitado.
- Info Field 4: Não utilizado.

### <a name="host-class-audio-streaming-sampling-get"></a>Amostragem de streaming de áudio de classe de anfitrião obter 

#### <a name="ux_host_class_audio_streaming_sampling_get"></a>ux_host_class_audio_streaming_sampling_get

**Ícone** ![ Amostragem de streaming de áudio de classe de anfitrião Obter ícone](./media/user-guide/usbx-events/image87.png)

**Descrição**

Este evento representa um evento de streaming de áudio da classe USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-audio-streaming-sampling-set"></a>Conjunto de amostragem de streaming de áudio de classe de anfitrião 

#### <a name="ux_host_class_audio_streaming_sampling_set"></a>ux_host_class_audio_streaming_sampling_set

**Ícone** ![ Ícone do conjunto de amostragem de streaming de áudio da classe do anfitrião](./media/user-guide/usbx-events/image88.png)

**Descrição**

Este evento representa um evento USBX Host Class Audio Streaming Sampling set.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Amostragem de áudio.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-audio-write"></a>Escrita áudio da classe hospedeira 

#### <a name="ux_host_class_audio_write"></a>ux_host_class_audio_write

**Ícone** ![ Ícone de escrita de áudio de classe de anfitrião](./media/user-guide/usbx-events/image89.png)

**Descrição**

Este evento representa um evento de escrita áudio da classe usbx.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Ponteiro de dados.
- Info Field 3: Comprimento solicitado.
- Info Field 4: Não utilizado.

### <a name="host-class-cdc-acm-activate"></a>Classe de anfitrião CDC Acm Ativar 

#### <a name="ux_host_class_cdc_acm_activate"></a>ux_host_class_cdc_acm_activate

**Ícone** ![ Classe anfitrião C D C A C M Ícone ativado](./media/user-guide/usbx-events/image90.png)

**Descrição**

Este evento representa um evento USBX Host Class Cdc Acm Activate Event.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-cdc-acm-deactivate"></a>Classe de anfitrião CDC Acm Desativar 

#### <a name="ux_host_class_cdc_acm_deactivate"></a>ux_host_class_cdc_acm_deactivate

**Ícone** ![ Ícone desativado classe C D C A C M](./media/user-guide/usbx-events/image91.png)

**Descrição**

Este evento representa um evento de desativado da classe USBX Cdc Acm.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-cdc-acm-ioctl-abort-in-pipe"></a>Classe anfitriã Cdc Acm Ioctl Abortar em tubo 

#### <a name="ux_host_class_cdc_acm_ioctl_abort_in_pipe"></a>ux_host_class_cdc_acm_ioctl_abort_in_pipe

**Ícone** ![ Classe hospedeira C D C A C M I O C T T Abort no ícone do tubo](./media/user-guide/usbx-events/image92.png)

**Descrição**

Este evento representa um CDC Acm Ioctl Abort in Pipe Event da classe USBX.

Campos de Informação 

- Info Field 1: Exemplo de classe.
- Info Field 2: Ponto final.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-cdc-acm-ioctl-abort-out-pipe"></a>Classe anfitriã Cdc Acm Ioctl AbortAr Tubo 

#### <a name="ux_host_class_cdc_acm_ioct_abort_out_pipe"></a>ux_host_class_cdc_acm_ioct_abort_out_pipe

**Ícone!** [[Classe anfitriã C D C A C A C M I O C T L AbortAr Ícone de Tubo](./media/user-guide/usbx-events/image93.png)

**Descrição**

Este evento representa um evento usbx host Class Cdc Acm Ioctl Abort out Pipe Event.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Ponto final.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-cdc-acm-ioctl-get-device-status"></a>Classe anfitrião Cdc Acm Ioctl Obter Estado do Dispositivo 

#### <a name="ux_host_class_cdc_acm_ioctl_get_device_status"></a>ux_host_class_cdc_acm_ioctl_get_device_status

**Ícone** ![ Classe hospedeira C D C A C M I O C T L Obter Ícone de Estado do Dispositivo](./media/user-guide/usbx-events/image94.png)

**Descrição**

Este evento representa um evento de estado do dispositivo da classe USBX Host Cdc Acm Ioctl Get Device.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Estado do dispositivo.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-cdc-acm-ioctl-get-line-coding"></a>Classe anfitriã CDC Acm Ioctl Obter Codificação de Linha 

#### <a name="ux_host_class_cdc_acm_ioctl_get_line_coding"></a>ux_host_class_cdc_acm_ioctl_get_line_coding

**Ícone** ![ Classe anfitriã C D C A C M I O C T L Get Line Codificação](./media/user-guide/usbx-events/image95.png)

**Descrição**

Este evento representa um evento de codificação usbx host Class CDC Acm Ioctl Get Line Coding.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Parâmetro.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-cdc-acm-ioctl-notification-callback"></a>Chamada de notificação do cdc Acm ioctl da classe anfitriã

#### <a name="ux_host_class_cdc_acm_ioctl_notification_callback"></a>ux_host_class_cdc_acm_ioctl_notification_callback

**Ícone** ![ Classe anfitriã C D C A C M I O C T L Notification Callback](./media/user-guide/usbx-events/image96.png)

**Descrição**

Este evento representa um evento de chamada de chamada de notificação DA Classe USBX CDC Acm Ioctl.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Parâmetro.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-cdc-acm-ioctl-send-break"></a>Classe anfitriã Cdc Acm Ioctl Enviar Pausa 

#### <a name="ux_host_class_cdc_acm_ioctl_send_break"></a>ux_host_class_cdc_acm_ioctl_send_break

**Ícone** ![ Classe anfitriã C D C A C M I O C T L Enviar Ícone de rutura](./media/user-guide/usbx-events/image97.png)

**Descrição**

Este evento representa um evento de intervalo de envio da classe USBX Cdc Acm Ioctl.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Parâmetro.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-cdc-acm-ioctl-set-line-coding"></a>Classe anfitrião CDC Acm Ioctl set Line Codificação 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_coding"></a>ux_host_class_cdc_acm_ioctl_set_line_coding

**Ícone** ![ Ícone de codificação da linha de codificação da classe anfitriã C D C C A C M I O C T L Line ](./media/user-guide/usbx-events/image97.png) Codeing](./media/user-guide/usbx-events/image98.png)

**Descrição**

Este evento representa um evento de codificação de linha set set da classe USBX CDC Acm Ioctl.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Parâmetro.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-cdc-acm-ioctl-set-line-state"></a>Classe anfitrião Cdc Acm Ioctl set Line State 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_state"></a>ux_host_class_cdc_acm_ioctl_set_line_state

**Ícone** ![ Classe anfitriã C D C A C A C M I O C T L set Line State ícone](./media/user-guide/usbx-events/image99.png)

**Descrição**

Este evento representa um evento de estado de set line set da classe USBX CDC Acm Ioctl.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Parâmetro.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-cdc-acm-read"></a>Classe anfitrião CDC Acm Read 

#### <a name="ux_host_class_cdc_acm_read"></a>ux_host_class_cdc_acm_read

**Ícone** ![ Ícone de leitura classe C D C A C M](./media/user-guide/usbx-events/image100.png)

**Descrição**

Este evento representa um evento de leitura da classe de anfitrião USBX CDC Acm.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Ponteiro de dados.
- Info Field 3: Comprimento Solicitado.
- Info Field 4: Não utilizado.

### <a name="host-class-cdc-acm-reception-start"></a>Início da receção da classe anfitriã CDC Acm 

#### <a name="ux_host_class_cdc_acm_reception_start"></a>ux_host_class_cdc_acm_reception_start

**Ícone** ![ Classe anfitrião C D C A C M Receção Ícone de início](./media/user-guide/usbx-events/image101.png)

**Descrição**

Este evento representa um evento de receção USBX Host Class Cdc Acm Reception Start.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-cdc-acm-reception-stop"></a>Paragem de receção cdc Acm classe anfitrião 

#### <a name="ux_host_class_cdc_acm_reception_stop"></a>ux_host_class_cdc_acm_reception_stop

**Ícone** ![ Classe anfitrião C D C A C C M Ícone de paragem de receção](./media/user-guide/usbx-events/image102.png)

**Descrição**

Este evento representa um evento de paragem de receção USBX Host Class CDC Acm.

**Campos de Informação**

- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-cdc-acm-write"></a>Classe anfitriã CDC Acm Write 

#### <a name="ux_host_class_acm_write"></a>ux_host_class_acm_write

**Ícone** ![ Ícone de escrita classe de anfitrião C D C A C M](./media/user-guide/usbx-events/image103.png)

**Descrição**

Este evento representa um evento de escrita DA Classe Anfitrião USBX CDC Acm.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Ponteiro de dados.
- Info Field 3: Comprimento Solicitado.
- Info Field 4: Não utilizado.

### <a name="host-class-dpump-activate"></a>Ativar classe de anfitrião Dpump 

#### <a name="ux_host_class_dpump_activate"></a>ux_host_class_dpump_activate

**Ícone** ![ Ícone ativar classe de anfitrião](./media/user-guide/usbx-events/image104.png)

**Descrição**

Este evento representa um Evento Ativado da Classe USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-dpump-deactivate"></a>Classe anfitriã Dpump Desativar 

#### <a name="ux_host_class_dpump_deactivate"></a>ux_host_class_dpump_deactivate

**Ícone** ![ Ícone de desativado classe de anfitrião Dpump](./media/user-guide/usbx-events/image105.png)

**Descrição**

Este evento representa um evento de desativado da classe USBX Dpump.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-dpump-read"></a>Leitura de Dpump de Classe Anfitriã 

#### <a name="ux_host_class_dpump_read"></a>ux_host_class_dpump_read

**Ícone** ![ Ícone de leitura de classe de anfitrião](./media/user-guide/usbx-events/image106.png)

**Descrição**

Este evento representa um Evento de Leitura de Dpump da Classe Anfitrião USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Ponteiro de dados.
- Info Field 3: Comprimento solicitado.
- Info Field 4: Não utilizado.

### <a name="host-class-dpump-write"></a>Escrita de Classe Anfitriã Dpump 

#### <a name="ux_host_class_dpump_write"></a>ux_host_class_dpump_write

**Ícone** ![ Ícone de escrita de classe de anfitrião](./media/user-guide/usbx-events/image107.png)

**Descrição**

Este evento representa um evento de escrita de classe de anfitrião USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Ponteiro de dados.
- Info Field 3: Comprimento solicitado.
- Info Field 4: Não utilizado.

### <a name="host-class-hid-activate"></a>Classe de anfitrião Hid Ativado 

#### <a name="ux_host_class_hid_activate"></a>ux_host_class_hid_activate

**Ícone** ![ Ícone ativar classe de anfitrião Hid](./media/user-guide/usbx-events/image108.png)

**Descrição**

Este evento representa um evento USBX Host Class Hid Activate Event.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-hid-client-register"></a>Registo de clientes hid de classe de anfitrião 

#### <a name="ux_host_class_hid_client_register"></a>ux_host_class_hid_client_register

**Ícone** ![ Ícone de registo de clientes de classe de anfitrião](./media/user-guide/usbx-events/image109.png)

**Descrição**

Este evento representa um evento USBX Host Class Hid Client Register.

**Campos de Informação** 

- Info Field 1: Nome do cliente escondido.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-hid-deactivate"></a>Classe de anfitrião Hid Desativado 

#### <a name="ux_host_class_hid_deactivate"></a>ux_host_class_hid_deactivate

**Ícone** ![ Ícone de desativado classe de anfitrião Hid](./media/user-guide/usbx-events/image110.png)

**Descrição**

Este evento representa um evento de desativado da classe usbx.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-hid-idle-get"></a>Classe anfitriã Hid Idle Get 

#### <a name="ux_host_class_hid_idle_get"></a>ux_host_class_hid_idle_get

**Ícone** ![ Classe de anfitrião Hid Idle Obter ícone](./media/user-guide/usbx-events/image111.png)

**Descrição**

Este evento representa um evento USBX Host Class Hid Idle Get.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-hid-idle-set"></a>Conjunto de idle de classe de anfitrião hid 

#### <a name="ux_host_class_hid_idle_set"></a>ux_host_class_hid_idle_set

**Ícone** ![ Ícone de conjunto de conjunto de classe de anfitrião hid ocioso](./media/user-guide/usbx-events/image112.png)

**Descrição**

Este evento representa um evento USBX Host Class Hid Idle set Event.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-hid-keyboard-activate"></a>Classe de anfitrião Hid Teclado Ativado 

#### <a name="ux_host_class_hid_keyboard_activate"></a>ux_host_class_hid_keyboard_activate

**Ícone** ![ Ícone ativar teclado de classe de anfitrião](./media/user-guide/usbx-events/image113.png)

**Descrição**

Este evento representa um evento usbx host class Hid Keyboard Activate Event.

**Campos de Informação**
<p>Info Field 1: Exemplo de classe.
<p>Info Field 2: Identificação do cliente escondida.
<p>Info Field 3: Não utilizado.
<p>Info Field 4: Não utilizado.

### <a name="host-class-hid-keyboard-deactivate"></a>Classe de anfitrião Hid Keyboard Desativado 

#### <a name="ux_host_class_hid_keyboard_deactivate"></a>ux_host_class_hid_keyboard_deactivate

**Ícone** ![ Ícone de desativado do teclado da classe anfitrião Hid](./media/user-guide/usbx-events/image114.png)

**Descrição**

Este evento representa um evento de desativado do teclado USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Identificação do cliente escondida.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-hid-mouse-activate"></a>Classe de anfitrião Hid Rato Ativado 

#### <a name="ux_host_class_hid_mouse_activate"></a>ux_host_class_hid_mouse_activate

**Ícone** ![ Ícone ativar rato de classe de anfitrião](./media/user-guide/usbx-events/image115.png)

**Descrição**

Este evento representa um evento USBX Host Class Hid Mouse Activate Event.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Identificação do cliente escondida.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-hid-mouse-deactivate"></a>Classe de anfitrião Hid Rato Desativado 

#### <a name="ux_host_class_hid_mouse_deactivate"></a>ux_host_class_hid_mouse_deactivate

**Ícone** ![ Ícone de desativado do rato da classe do anfitrião](./media/user-guide/usbx-events/image116.png)

**Descrição**

- Este evento representa um evento de desativado da classe USBX Da Classe Hid Mouse.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Identificação do cliente escondida.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-hid-remote-control-activate"></a>Classe de anfitrião hid controlo remoto ativado 

#### <a name="ux_host_class_hid_remote_control_activate"></a>ux_host_class_hid_remote_control_activate

**Ícone** ![ Classe de anfitrião hid remote controle ícone ativar](./media/user-guide/usbx-events/image117.png)

**Descrição**

Este evento representa um evento usbx host class Hid Remote Control Activate Event.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Identificação do cliente escondida.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-hid-remote-control-deactivate"></a>Classe de anfitrião hid remote control desativado 

#### <a name="ux_host_class_hid_remote_control_deactivate"></a>ux_host_class_hid_remote_control_deactivate

**Ícone** ![ Classe de anfitrião hid remote control desativado ícone](./media/user-guide/usbx-events/image118.png)

**Descrição**

Este evento representa um evento de desativado do controlo remoto USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Identificação do cliente escondida.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-hid-report-get"></a>Relatório hid classe anfitrião obter 

#### <a name="ux_host_class_hid_report_get"></a>ux_host_class_hid_report_get

**Ícone** ![ Relatório hid classe anfitrião Obter ícone](./media/user-guide/usbx-events/image119.png)

**Descrição**

Este evento representa um relatório hid de classe de anfitrião USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Relatório do cliente.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-hid-report-set"></a>Conjunto de relatório hid classe de anfitrião 

#### <a name="ux_host_class_hid_report_set"></a>ux_host_class_hid_report_set

**Ícone** ![ Ícone de conjunto de relatório de classe de anfitrião hid](./media/user-guide/usbx-events/image120.png)

**Descrição** Este evento representa um conjunto de relatórios hid da classe de anfitrião USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Relatório do cliente.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-hub-activate"></a>Centro de classe de anfitrião Ativar 

#### <a name="ux_host_class_hub_activate"></a>ux_host_class_hub_activate

**Ícone** ![ Ícone ativar o centro de classe do anfitrião](./media/user-guide/usbx-events/image121.png)

**Descrição**

Este evento representa um evento USBX Host Class Hub Activate Event.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-hub-change-detect"></a>Deteção de mudança de centro de classe de anfitrião 

#### <a name="ux_host_class_hub_change_detect"></a>ux_host_class_hub_change_detect

**Ícone** ![ Ícone de deteção de mudança de centro de classe de anfitrião](./media/user-guide/usbx-events/image122.png)

**Descrição**

Este evento representa um evento usbx host Class Hub Change Detect.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-hub-deactivate"></a>Centro de classe de anfitrião desativar 

#### <a name="ux_host_class_hub_deactivate"></a>ux_host_class_hub_deactivate

**Ícone** ![ Ícone de desativado do hub de classe de anfitrião](./media/user-guide/usbx-events/image123.png)

**Descrição**

Este evento representa um evento de desativado do Hub de Classe de Anfitriões USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-hub-port-change-connection-process"></a>Processo de ligação de mudança de porta do hub de classe de anfitrião 

#### <a name="ux_host_class_hub_change_connection_process"></a>ux_host_class_hub_change_connection_process

**Ícone** ![ Ícone do processo de mudança de ligação do hub da classe do anfitrião](./media/user-guide/usbx-events/image124.png)

**Descrição**

Este evento representa um evento usbx host Class Hub Connection Process Event.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Porta.
- Info Field 3: Estado da porta.
- Info Field 4: Não utilizado.

### <a name="host-class-hub-port-change-enable-process"></a>Processo de alteração da porta do hub de classe de anfitrião 

#### <a name="ux_host_class_hub_port_change_enable_process"></a>ux_host_class_hub_port_change_enable_process

**Ícone** ![ Ícone de mudança de carro do hub de classe de anfitrião](./media/user-guide/usbx-events/image125.png)

**Descrição**

Este evento representa um evento usbx host Class Hub Enable Process Event.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Porta.
- Info Field 3: Estado da porta.
- Info Field 4: Não utilizado.

### <a name="host-class-hub-port-change-over-current-process"></a>Mudança de porta do hub de classe de anfitrião sobre o processo atual 

#### <a name="ux_host_class_hub_port_change_over_current_process"></a>ux_host_class_hub_port_change_over_current_process

**Ícone** ![ Mudança de porta do hub do anfitrião sobre o ícone do processo atual](./media/user-guide/usbx-events/image126.png)

**Descrição**

Este evento representa a atribuição de um pacote através de nx_packet_allocate.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Porta.
- Info Field 3: Estado da porta.
- Info Field 4: Não utilizado.

### <a name="host-class-hub-port-change-reset-process"></a>Processo de reset de mudança de porta do hub de classe de anfitrião 

#### <a name="ux_host_class_hub_port_change_reset_process"></a>ux_host_class_hub_port_change_reset_process

**Ícone** ![ Ícone do processo de reposição do processo de mudança de porta do hub da classe do anfitrião](./media/user-guide/usbx-events/image127.png)

**Descrição**

Este evento representa um evento de reset de mudança de porta do hub de classe USBX.

**Campos de Informação**

- Info Field 1: Hub. Info Field 2: Porta.
- Info Field 3: Estado da porta.
- Info Field 4: Não utilizado.

### <a name="host-class-hub-port-change-suspend-process"></a>Processo de suspensão de alteração de mudança de porta do hub de classe de anfitrião 

#### <a name="ux_host_class_hub_port_change_suspend_process"></a>ux_host_class_hub_port_change_suspend_process

**Ícone** ![ Ícone de processo de suspensão de mudança de porta do hub de classe de anfitrião](./media/user-guide/usbx-events/image128.png)

**Descrição**

Este evento representa um evento de suspensão de suspensão de alterações de portas do hub da classe USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Porta.
- Info Field 3: Estado da porta.
- Info Field 4: Não utilizado.

### <a name="host-class-pima-activate"></a>Classe de anfitrião Pima Ativar 

#### <a name="ux_host_class_pima_activate"></a>ux_host_class_pima_activate

**Ícone** ![ Ícone de ativação classe de anfitrião Pima](./media/user-guide/usbx-events/image129.png)

**Descrição**

Este evento representa um Evento Pima Activate Classe de Anfitriões USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-pima-deactivate"></a>Classe anfitriã Pima Desativado 

#### <a name="ux_host_class_pima_deactivate"></a>ux_host_class_pima_deactivate

**Ícone** ![ Ícone de desativado classe de anfitrião Pima](./media/user-guide/usbx-events/image130.png)

**Descrição**

Este evento representa um Evento de Desativado Pima da Classe Pima da Classe Anfitrião USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-pima-device-info-get"></a>Informações de dispositivo pima classe anfitrião obter 

#### <a name="ux_host_class_pima_device_info_get"></a>ux_host_class_pima_device_info_get

**Ícone** ![ Classe anfitrião Pima Device Info Obter ícone](./media/user-guide/usbx-events/image131.png)

**Descrição**

Este evento representa um evento de info get da classe Pima da classe usbx.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Dispositivo Pima.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-pima-device-reset"></a>Reset do dispositivo Pima da classe de anfitrião 

#### <a name="ux_host_class_pima_device_reset"></a>ux_host_class_pima_device_reset

**Ícone** ![ Ícone de reset do dispositivo Pima da classe anfitrião](./media/user-guide/usbx-events/image132.png)

**Descrição**

Este evento representa um evento de reset do dispositivo Pima da classe de anfitrião USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-pima-notification"></a>Notificação Pima classe anfitrião 

#### <a name="ux_host_class_pima_notification"></a>ux_host_class_pima_notification

**Ícone** ![ Ícone de notificação Pima classe anfitrião](./media/user-guide/usbx-events/image133.png)

**Descrição**

Este evento representa um Evento de Notificação Pima da Classe Pima da classe de anfitriões USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe. Info Field 2: Código de evento.
- Info Field 3: ID de transação.
- Info Campo 4: Parâmetro1.

### <a name="host-class-pima-number-objects-get"></a>Objetos de número pima classe anfitrião obtêm 

#### <a name="ux_host_class_pima_number_objects_get"></a>ux_host_class_pima_number_objects_get

**Ícone** ![ Objetos de número pima classe anfitrião obter ícone](./media/user-guide/usbx-events/image134.png)

**Descrição**

Este evento representa um evento de objetos de número pima da classe usbx.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-pima-object-close"></a>Objeto Pima classe anfitrião perto 

#### <a name="ux_host_class_pima_object_close"></a>ux_host_class_pima_object_close

**Ícone** ![ Ícone de fecho de objeto pima classe anfitrião](./media/user-guide/usbx-events/image135.png)

**Descrição**

Este evento representa um evento usbx host Class Pima Object Close Event.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Objeto.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-pima-object-copy"></a>Cópia do objeto Pima da classe de anfitrião 

#### <a name="ux_host_class_pima_object_copy"></a>ux_host_class_pima_object_copy

**Ícone** ![ Ícone de cópia de objeto de classe de anfitrião Pima](./media/user-guide/usbx-events/image136.png)

**Descrição**

Este evento representa um evento usbx host Class Pima Object Copy Event.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Pega do objeto.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-pima-object-delete"></a>Excluir objeto pima classe anfitrião 

#### <a name="ux_host_class_pima_object_delete"></a>ux_host_class_pima_object_delete

**Ícone** ![ Ícone de exclusão de objeto pima classe anfitrião](./media/user-guide/usbx-events/image137.png)

**Descrição**

Este evento representa um evento de eliminação de objetos Pima da classe usbx.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Pega do objeto.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-pima-object-get"></a>Objeto Pima classe anfitrião obter 

#### <a name="ux_host_class_pima_object_get"></a>ux_host_class_pima_object_get

**Ícone** ![ Classe anfitrião Pima Objeto Obter ícone](./media/user-guide/usbx-events/image138.png)

**Descrição**

Este evento representa obter informações da RARP através de nx_rarp_info_get.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Pega do objeto.
- Info Field 3: Objeto.
- Info Field 4: Não utilizado.

### <a name="host-class-pima-object-info-get"></a>Hospeda classe Pima Objeto Info Obter 

#### <a name="ux_host_class_pima_object_info_get"></a>ux_host_class_pima_object_info_get

**Ícone** ![ Classe anfitrião Pima Objeto Info Obter ícone](./media/user-guide/usbx-events/image139.png)

**Descrição**

Este evento representa um evento USBX Host Class Pima Object Info Get.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Pega do objeto.
- Info Field 3: Objeto.
- Info Field 4: Não utilizado.

### <a name="host-class-pima-object-info-send"></a>Página de anfitrião Pima Object Info Enviar 

#### <a name="ux_host_class_pima_object_info_send"></a>ux_host_class_pima_object_info_send

**Ícone** ![ Classe anfitrião Pima Objeto Info Enviar ícone](./media/user-guide/usbx-events/image140.png)

**Descrição**

Este evento representa um evento de envio de informação de objeto pima da classe USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Objeto.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-pima-object-move"></a>Movimento de objeto classe de anfitrião Pima 

#### <a name="ux_host_class_pima_object_move"></a>ux_host_class_pima_object_move

**Ícone** ![ Ícone de movimento de objeto de classe de anfitrião Pima](./media/user-guide/usbx-events/image141.png)

**Descrição**

Este evento representa um evento USBX Host Class Pima Object Move Event.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Pega do objeto.
- Info Field 3: Objeto.
- Info Field 4: Não utilizado.

### <a name="host-class-pima-object-send"></a>Envio de objeto pima classe anfitrião 

#### <a name="ux_host_class_pima_object_move"></a>ux_host_class_pima_object_move

**Ícone** ![ Ícone de envio de objeto pima classe anfitrião](./media/user-guide/usbx-events/image142.png)

**Descrição**

Este evento representa um evento de envio de objetos Pima da classe usbx.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Objeto.
- Info Field 3: Tampão de objeto.
- Info Campo 4: Comprimento do objeto.

### <a name="host-class-pima-object-transfer-abort"></a>Aborto de transferência de objeto pima classe anfitrião 

#### <a name="ux_host_class_pima_object_transfer_abort"></a>ux_host_class_pima_object_transfer_abort

**Ícone** ![ Ícone de aborto de transferência de objeto de classe Pima de anfitrião](./media/user-guide/usbx-events/image143.png)

**Descrição**

Este evento representa um evento USBX Host Class Pima Object Transfer Abort.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Pega do objeto.
- Info Field 3: Objeto.
- Info Field 4: Não utilizado.

### <a name="host-class-pima-read"></a>Classe de anfitrião Pima Read 

#### <a name="ux_host_class_pima_read"></a>ux_host_class_pima_read

**Ícone** ![ Ícone de leitura de classe de anfitrião Pima](./media/user-guide/usbx-events/image144.png)

**Descrição**

Este evento representa um Evento de Leitura Pima da Classe Pima da Classe Anfitrião USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Ponteiro de dados.
- Info Field 3: Comprimento dos dados.
- Info Field 4: Não utilizado.

### <a name="host-class-pima-request-cancel"></a>Cancelamento de pedido de convite da classe anfitriã Pima 

#### <a name="ux_host_class_pima_request_cancel"></a>ux_host_class_pima_request_cancel

**Ícone** ![ Classe anfitrião Pima Request Cancel ícone](./media/user-guide/usbx-events/image145.png)

**Descrição**

Este evento representa um evento de cancelamento de pedido de pedido de anfitrião USBX Pima.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-pima-session-close"></a>Sessão Pima de classe de anfitrião fechar 

#### <a name="ux_host_class_pima_session_close"></a>ux_host_class_pima_session_close

**Ícone** ![ Ícone de fecho de sessão pima de classe de anfitrião](./media/user-guide/usbx-events/image146.png)

**Descrição**

Este evento representa um evento de encerramento de sessão Pima da classe de anfitriões USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Sessão Pima.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-pima-session-open"></a>Sessão Pima de classe de anfitrião Aberta 

#### <a name="ux_host_class_pima_session_open"></a>ux_host_class_pima_session_open

**Ícone** ![ Ícone do open da sessão pima de classe de anfitrião](./media/user-guide/usbx-events/image147.png)

**Descrição** Este evento representa um evento OPEN de Sessão Pima da Classe Pima da classe USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Sessão Pima.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-pima-storage-ids-get"></a>Classe anfitrião Pima Storage Ids Obter 

#### <a name="ux_host_class_pima_session_ids_get"></a>ux_host_class_pima_session_ids_get

**Ícone** ![ Classe anfitrião Pima Storage Ids Obter ícone](./media/user-guide/usbx-events/image148.png)

**Descrição**

Este evento representa um evento DE ARMAZENAMENTO Pima Da Classe Pima da Classe USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- nfo Field 2: Array de ID de armazenamento.
- Info Field 3: Comprimento do ID de armazenamento.
Info Field 4: Não utilizado.

### <a name="host-class-pima-storage-info-get"></a>Informações de armazenamento Pima classe anfitrião obter 

#### <a name="ux_host_class_pima_storage_info_get"></a>ux_host_class_pima_storage_info_get

**Ícone** ![ Classe anfitrião Pima Storage Info Obter ícone](./media/user-guide/usbx-events/image149.png)

**Descrição**

Este evento representa um evento USBX Host Class Pima Storage Info Get.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: ID de armazenamento.
- Info Field 3: Armazenamento.
- Info Field 4: Não utilizado.

### <a name="host-class-pima-thumb-get"></a>Classe anfitrião Pima Polegar Get 

#### <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

**Ícone** ![ Ícone de polegar Pima de classe de anfitrião](./media/user-guide/usbx-events/image150.png)

**Descrição**

Este evento representa não aceitar uma ligação do servidor TCP através de nx_tcp_server_socket_unaccept.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Pega do objeto.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-pima-write"></a>Classe de anfitrião Pima Escrever 

#### <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

**Ícone** ![ Ícone de escrita classe de anfitrião Pima](./media/user-guide/usbx-events/image151.png)

**Descrição**

Este evento representa uma classe de anfitrião USBX Pima Write.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Ponteiro de dados.
- Info Field 3: Comprimento dos dados.
- Info Field 4: Não utilizado.

### <a name="host-class-printer-activate"></a>Ativar impressora de classe de anfitrião 

#### <a name="ux_host_class_printer_activate"></a>ux_host_class_printer_activate

**Ícone** ![ Ícone ativar impressora de classe de anfitrião](./media/user-guide/usbx-events/image152.png)

**Descrição**

Este evento representa um evento usbx host Class Printer Activate Event.

**Campos de Informação**

- Info Field 1: Ponteiro para a instância IP.
- Info Campo 2: Ponteiro para tomada.
- Info Campo 3: Tipo de serviço.
- Info Campo 4: Receber o tamanho da janela.

### <a name="host-class-printer-deactivate"></a>Impressora de classe de anfitrião desativar 

#### <a name="ux_host_class_printer_deactivate"></a>ux_host_class_printer_deactivate

**Ícone** ![ Ícone de desativar impressora de classe de anfitrião](./media/user-guide/usbx-events/image153.png)

**Descrição**

Este evento representa um evento de desativado da impressora usbx da classe de anfitrião.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-printer-name-get"></a>Nome da impressora de classe de anfitrião obter 

#### <a name="ux_host_class_printer_name_get"></a>ux_host_class_printer_name_get

**Ícone** ![ Nome da impressora de classe anfitrião obter ícone](./media/user-guide/usbx-events/image154.png)

**Descrição**

Este evento representa um evento de nome de impressora de classe de anfitrião USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-printer-read"></a>Leitura de impressora de classe de anfitrião 

#### <a name="ux_host_class_printer_read"></a>ux_host_class_printer_read

**Ícone** ![ Ícone de leitura de impressora de classe de anfitrião](./media/user-guide/usbx-events/image155.png)

**Descrição**

Este evento representa um evento de leitura de impressora de classe de anfitrião USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Ponteiro de dados.
- Info Field 3: Comprimento solicitado.
- Info Field 4: Não utilizado.

### <a name="host-class-printer-soft-reset"></a>Reset suave da impressora de classe de anfitrião 

#### <a name="ux_host_class_printer_soft_reset"></a>ux_host_class_printer_soft_reset

**Ícone** ![ Ícone de reset suave da impressora de classe de anfitrião](./media/user-guide/usbx-events/image156.png)

**Descrição**

Este evento representa um evento de reset suave da impressora de classe USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-printer-status-get"></a>Estado da impressora de classe de anfitrião obter 

#### <a name="ux_host_class_printer_status_get"></a>ux_host_class_printer_status_get

**Ícone** ![ Estado da impressora de classe de anfitrião Obter ícone](./media/user-guide/usbx-events/image157.png)

**Descrição**

Este evento representa um evento usbx host Class Printer Status Get Event.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Estado da impressora.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-printer-write"></a>Escrita de impressora de classe de anfitrião 

#### <a name="ux_host_class_printer_write"></a>ux_host_class_printer_write

**Ícone** ![ Ícone de escrita de impressora de classe de anfitrião](./media/user-guide/usbx-events/image158.png)

**Descrição**

Este evento representa uma escrita de impressora de classe de anfitrião USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Ponteiro de dados.
- Info Field 3: Comprimento solicitado.
- Info Field 4: Não utilizado.

### <a name="host-class-prolific-activate"></a>Ativação prolific da classe de anfitrião 

#### <a name="ux_host_class_prolific_activate"></a>ux_host_class_prolific_activate 

**Ícone** ![ Ícone de ativação prolific de classe de anfitrião](./media/user-guide/usbx-events/image159.png)

**Descrição**

Este evento representa um evento de ativação da classe de anfitrião USBX.

**Campos de Informação** 

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-prolific-deactivate"></a>Classe de anfitrião Prolific Desativado 

#### <a name="ux_host_class_prolific_deactivate"></a>ux_host_class_prolific_deactivate 

**Ícone** ![ Ícone prolífico da classe de anfitrião](./media/user-guide/usbx-events/image160.png)

**Descrição**

Este evento representa um evento de desativado da classe USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-prolific-ioctl-abort-in-pipe"></a>Classe de anfitrião Prolific Ioctl Abortar no tubo 

#### <a name="ux_host_class_prolific_ioctl_abort_in_pipe"></a>ux_host_class_prolific_ioctl_abort_in_pipe

**Ícone** ![ Classe de anfitrião Prolific I O C T T L Abortar no ícone do tubo](./media/user-guide/usbx-events/image161.png)

**Descrição**

Este evento representa um evento de confirmação da classe de anfitriões USBX Prolific Ioctl Abort in Pipe Event.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Ponto final.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-prolific-ioctl-abort-out-pipe"></a>Classe de anfitrião Prolific Ioctl AbortAr Tubo 

#### <a name="ux_host_class_prolific_ioctl_abort_out_pipe"></a>ux_host_class_prolific_ioctl_abort_out_pipe

**Ícone** ![ Classe de anfitrião Prolific I O C T L AbortAr Ícone do Tubo](./media/user-guide/usbx-events/image162.png)

**Descrição**

Este evento representa um evento de tubo de aborto da classe usbx da classe de anfitriões Prolific Ioctl.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Ponto final.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-prolific-ioctl-get-device-status"></a>Classe de anfitrião Prolific Ioctl Obter Estado do Dispositivo 

#### <a name="ux_host_class_prolific_ioctl_get_device_status"></a>ux_host_class_prolific_ioctl_get_device_status

**Ícone** ![ Classe de anfitrião Prolific I O C T L Obter Ícone de Estado do Dispositivo](./media/user-guide/usbx-events/image163.png)

**Descrição**

Este evento representa um evento de estado do dispositivo da classe usbx prolífica do recetor.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Estado do dispositivo.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-prolific-ioctl-get-line-coding"></a>Classe de anfitrião Prolific Ioctl Obter Codificação de Linha 

#### <a name="ux_host_class_prolific_ioctl_get_line_coding"></a>ux_host_class_prolific_ioctl_get_line_coding

**Ícone** ![ Classe de anfitrião Prolific I O C T L Obter Ícone de codificação de linha](./media/user-guide/usbx-events/image164.png)

**Descrição**

Este evento representa um evento de codificação de linha da classe usbx prolífica.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Parâmetro.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-prolific-ioctl-purge"></a>Classe de anfitrião Prolific Ioctl Purga 

#### <a name="ux_host_class_prolific_ioctl_purge"></a>ux_host_class_prolific_ioctl_purge

**Ícone** ![ Ícone de purga prolifico de classe de anfitrião](./media/user-guide/usbx-events/image165.png)

**Descrição**

Este evento representa um evento de purga prolifico da classe usbx.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Parâmetro.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-prolific-ioctl-report-device"></a>Dispositivo de relatório prolific da classe de anfitrião 

#### <a name="ux_host_class_prolific_ioctl_report_device"></a>ux_host_class_prolific_ioctl_report_device

**Ícone** ![ Ícone do dispositivo de relatório de relatório da classe anfitrião I O C T L](./media/user-guide/usbx-events/image166.png)

**Descrição**

Este evento representa um evento de alteração do estado do dispositivo de relatório do relatório do relatório da classe USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Parâmetro.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-prolific-ioctl-send-break"></a>Classe de anfitrião Prolific Ioctl Enviar Pausa 

#### <a name="ux_host_class_prolific_ioctl_send_break"></a>ux_host_class_prolific_ioctl_send_break

**Ícone** ![ Classe de anfitrião Prolific I O C T L Enviar Ícone de rutura](./media/user-guide/usbx-events/image167.png)

**Descrição**

Este evento representa um evento de envio de interrupção da classe USBX Da Classe Prolífica do Ioctl.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-prolific-ioctl-set-line-coding"></a>Codificação de linha de linha de conjunto prolific da classe de anfitrião 

#### <a name="ux_host_class_prolific_ioctl_set_line_coding"></a>ux_host_class_prolific_ioctl_set_line_coding

**Ícone** ![ Ícone de codificação de linha de classe de anfitrião I O C T L](./media/user-guide/usbx-events/image168.png)

**Descrição**

Este evento representa um evento de codificação de linha de linha de conjunto da classe USBX Prolific.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Parâmetro.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-prolific-ioctl-set-line-state"></a>Estado da linha de linha do conjunto de conjunto prolific da classe de anfitrião 

#### <a name="ux_host_class_prolific_ioctl_set_line_state"></a>ux_host_class_prolific_ioctl_set_line_state

**Ícone** ![ Classe de anfitrião Prolific I O C T L set Line State ícone](./media/user-guide/usbx-events/image169.png)

**Descrição**

Este evento representa um evento de estado de linha de set prolific da classe USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Parâmetro.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-prolific-read"></a>Leitura Prolífica da Classe anfitriã 

#### <a name="ux_host_class_prolific_read"></a>ux_host_class_prolific_read

**Ícone** ![ Ícone de leitura prolífica de classe de anfitrião](./media/user-guide/usbx-events/image170.png)

**Descrição**

Este evento representa um evento de leitura prolífica da classe USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Ponteiro de dados.
- Info Field 3: Comprimento solicitado.
- Info Field 4: Não utilizado.

### <a name="host-class-prolific-reception-start"></a>Início de receção prolific classe anfitrião 

#### <a name="ux_host_class_prolific_reception_start"></a>ux_host_class_prolific_reception_start

**Ícone** ![ Ícone de início de receção prolific de classe de anfitrião](./media/user-guide/usbx-events/image171.png)

**Descrição**

Este evento representa um evento de receção prolific da classe usbx.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-prolific-reception-stop"></a>Paragem de receção prolífica classe de anfitrião 

#### <a name="ux_host_class_prolific_reception_stop"></a>ux_host_class_prolific_reception_stop

**Ícone** ![ Ícone de paragem de receção prolific de classe de anfitrião](./media/user-guide/usbx-events/image172.png)

**Descrição**

Este evento representa um evento de paragem de receção prolific da classe USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-prolific-write"></a>Escrita Prolific classe anfitrião 

#### <a name="ux_host_class_prolific_write"></a>ux_host_class_prolific_write

**Ícone** ![ Ícone de escrita prolific classe de anfitrião](./media/user-guide/usbx-events/image173.png)

**Descrição**

Este evento representa um evento de escrita prolific da classe usbx.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Ponteiro de dados.
- Info Field 3: Comprimento solicitado.
- Info Field 4: Não utilizado.

### <a name="host-class-storage-activate"></a>Ativar o armazenamento da classe do anfitrião 

#### <a name="ux_host_class_storage_activate"></a>ux_host_class_storage_activate

**Ícone** ![ Ícone ativar o armazenamento da classe do anfitrião](./media/user-guide/usbx-events/image174.png)

**Descrição**

Este evento representa um evento USBX Host Class Storage Activate.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-storage-deactivate"></a>Armazenamento de classe de anfitrião desativado 

#### <a name="ux_host_class_storage_deactivate"></a>ux_host_class_storage_deactivate

**Ícone** ![ Ícone de desativação de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image175.png)

**Descrição**

Este evento representa um evento de desativação da classe de anfitrião USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-storage-media-capacity-get"></a>Capacidade de mídia de armazenamento de classe de anfitrião obter 

#### <a name="ux_host_class_storage_media_capacity_get"></a>ux_host_class_storage_media_capacity_get

**Ícone** ![ Classe anfitrião armazenamento capacidade de mídia obter ícone](./media/user-guide/usbx-events/image176.png)

**Descrição**

Este evento representa um evento USBX Host Class Storage Media Capacity Get.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-storage-media-format-capacity-get"></a>Capacidade de formato de mídia de armazenamento de classe de anfitrião obter

#### <a name="ux_host_class_storage_media_format_capacity_get"></a>ux_host_class_storage_media_format_capacity_get

**Ícone** ![ Grupo de anfitrião armazenamento de armazenamento de capacidade obter ícone](./media/user-guide/usbx-events/image177.png)

**Descrição**

Este evento representa um evento USBX Host Class Storage Media Formato Capacity Get.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

#### <a name="host-class-storage-media-mount"></a>Montagem de mídia de armazenamento de classe de anfitrião 

#### <a name="ux_host_class_storage_media_mount"></a>ux_host_class_storage_media_mount

**Ícone** ![ Ícone de montagem de mídia de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image178.png)

**Descrição**

Este evento representa um evento USBX Host Class Storage Media Mount.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Sector.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-storage-media-open"></a>Classe de anfitrião armazenamento mídia aberta 

#### <a name="ux_host_class_storage_media_open"></a>ux_host_class_storage_media_open

**Ícone** ![ Ícone de mídia de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image179.png)

**Descrição**

Este evento representa um evento USBX Host Class Storage Media Open.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Media.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-storage-media-read"></a>Leitura de mídia de armazenamento de classe de anfitrião 

#### <a name="ux_host_class_storage_media_read"></a>ux_host_class_storage_media_read

**Ícone** ![ Ícone de leitura de mídia de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image180.png)

**Descrição**

Este evento representa um evento usbx host Class Storage Media Read.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Início do sector.
- Info Field 3: Contagem de sector.
- Info Field 4: Ponteiro de dados.

### <a name="host-class-storage-media-write"></a>Escrita de mídia de armazenamento de classe de anfitrião 

#### <a name="ux_host_class_storage_media_write"></a>ux_host_class_storage_media_write

**Ícone** ![ Ícone de mídia de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image181.png)

**Descrição**

Este evento representa um evento usbx host Class Storage Media Write.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Início do sector.
- Info Field 3: Contagem de sector.
- Info Field 4: Ponteiro de dados.

### <a name="host-class-storage-request-sense"></a>Sentido do pedido de armazenamento de classe de anfitrião 

#### <a name="ux_host_class_storage_request_sense"></a>ux_host_class_storage_request_sense

**Ícone** ![ Ícone de pedido de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image182.png)

**Descrição**

Este evento representa um evento usbx host Class Storage Sense Event.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-storage-start-stop"></a>Paragem de início de armazenamento de classe de anfitrião 

#### <a name="ux_host_class_storage_start_stop"></a>ux_host_class_storage_start_stop

**Ícone** ![ Ícone de paragem de início de armazenamento de classe de anfitrião](./media/user-guide/usbx-events/image183.png)

**Descrição**

Este evento representa um evento de paragem de início de armazenamento de classe usbx.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Campo 2: Sinal de paragem de início.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-class-storage-unit-ready-test"></a>Teste pronto da unidade de armazenamento da classe de anfitrião 

#### <a name="ux_host_class_storage_unit_ready_test"></a>ux_host_class_storage_unit_ready_test

**Ícone** ![ Ícone de teste pronto da unidade de armazenamento da classe do anfitrião](./media/user-guide/usbx-events/image184.png)

**Descrição**

Este evento representa um evento de teste pronto da unidade de armazenamento da classe USBX.

**Campos de Informação**

- Info Field 1: Exemplo de classe.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-class-instance-create"></a>Série de anfitrião classe de classe criar 

#### <a name="ux_host_class_instance_create"></a>ux_host_class_instance_create

**Ícone** ![ Série de anfitrião exemplo criar ícone](./media/user-guide/usbx-events/image185.png)

**Descrição**

Este evento representa um evento de série de série de anfitrião USBX.

**Campos de Informação**

- Info Field 1: Classe.
- Info Field 2: Exemplo de classe.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-class-instance-destroy"></a>Exemplo de classe de pilha de anfitrião destruir 

#### <a name="ux_host_class_instance_create"></a>ux_host_class_instance_create

**Ícone** ![ Ícone de destruição de classe de classe de pilha de anfitrião](./media/user-guide/usbx-events/image186.png)

**Descrição**

Este evento representa um evento de destruição de classe de série de anfitrião USBX.

**Campos de Informação**

- Info Field 1: Classe.
- Info Field 2: Exemplo de classe.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-configuration-delete"></a>Configuração de pilha de anfitrião Eliminar 

#### <a name="ux_host_class_configuration_delete"></a>ux_host_class_configuration_delete

**Ícone** ![ Ícone de configuração de pilha de anfitrião Eliminar](./media/user-guide/usbx-events/image187.png)

**Descrição**

Este evento representa um evento de eliminação da configuração da pilha de anfitriões USBX.

**Campos de Informação**

- Info Field 1: Configuração.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-configuration-enumerate"></a>Enumerar a configuração da pilha de anfitrião 

#### <a name="ux_host_stack_configuration_enumerate"></a>ux_host_stack_configuration_enumerate

**Ícone** ![ Ícone de enumeração de configuração de pilha de anfitrião](./media/user-guide/usbx-events/image188.png)

**Descrição**

Este evento representa um evento de configuração de configuração de pilha de anfitrião USBX.

**Campos de Informação**

- Info Field 1: Dispositivo.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="stack-configuration-instance-create"></a>Criar exemplos de configuração de pilha 

#### <a name="ux_host_stack_configuration_instance_create"></a>ux_host_stack_configuration_instance_create

**Ícone** ![ Exemplo de configuração de pilha Criar ícone](./media/user-guide/usbx-events/image189.png)

**Descrição**

Este evento representa um evento de configuração de configuração de pilha de anfitrião USBX.

**Campos de Informação**

- Info Field 1: Configuração.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-configuration-instance-delete"></a>Excluir a configuração da configuração da pilha do anfitrião 

#### <a name="ux_host_stack_configuration_instance_delete"></a>ux_host_stack_configuration_instance_delete

**Ícone** ![ Exemplo de configuração de pilha de anfitrião Eliminar ícone](./media/user-guide/usbx-events/image190.png)

**Descrição**

Este evento representa um evento de configuração de configuração de pilha de anfitrião USBX.

**Campos de Informação**

- Info Field 1: Configuração.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-configuration-set"></a>Conjunto de configuração de pilha de anfitrião 

#### <a name="ux_host_stack_configuration_set"></a>ux_host_stack_configuration_set

**Ícone** ![ Ícone de conjunto de configuração de pilha de anfitrião](./media/user-guide/usbx-events/image191.png)

**Descrição**

Este evento representa um evento usbx host Stack Configuration set Event.

**Campos de Informação**

- Info Field 1: Configuração.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-device-address-set"></a>Conjunto de endereço de dispositivo de pilha de anfitrião 

#### <a name="ux_host_stack_device_address_set"></a>ux_host_stack_device_address_set

**Ícone** ![ Ícone de conjunto de endereço de dispositivo de pilha de anfitrião](./media/user-guide/usbx-events/image192.png)

**Descrição**

Este evento representa um evento usbx host Stack Device Address set.

**Campos de Informação**

- Info Field 1: Dispositivo.
- Info Field 2: Endereço do dispositivo.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-device-configuration-get"></a>Configuração do dispositivo de pilha de anfitrião obter 

#### <a name="ux_host_stack_device_configuration_get"></a>ux_host_stack_device_configuration_get

**Ícone** ![ Configuração do dispositivo de pilha de anfitrião Obter ícone](./media/user-guide/usbx-events/image193.png)

**Descrição**

Este evento representa um evento de configuração do dispositivo de pilha de anfitrião USBX.

**Campos de Informação**

- Info Field 1: Dispositivo.
- nfo Field 2: Configuração.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-device-configuration-select"></a>Selecione de configuração do dispositivo de pilha de anfitrião 

#### <a name="ux_host_stack_device_configuration_select"></a>ux_host_stack_device_configuration_select

**Ícone** ![ Ícone de configuração do dispositivo de pilha de anfitrião](./media/user-guide/usbx-events/image194.png)

**Descrição**

Este evento representa um evento de configuração do dispositivo de pilha de anfitriões USBX.

**Campos de Informação**

- Info Field 1: Dispositivo.
- Info Field 2: Configuração.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-device-descriptor-read"></a>Leitura do descritor do dispositivo de pilha de anfitrião 

#### <a name="ux_host_stack_device_descriptor_read"></a>ux_host_stack_device_descriptor_read

**Ícone** ![ Ícone de leitura de dispositivo de pilha de anfitrião](./media/user-guide/usbx-events/image195.png)

**Descrição**

Este evento representa um evento de leitura do dispositivo de pilha de anfitriões USBX.

**Campos de Informação**

- Info Field 1: Dispositivo.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-device-get"></a>Dispositivo de pilha de anfitrião obter 

#### <a name="ux_host_stack_device_get"></a>ux_host_stack_device_get

**Ícone** ![ Dispositivo de pilha de anfitrião obter ícone](./media/user-guide/usbx-events/image196.png)

**Descrição**

Este evento representa um evento usbx host Stack Device Get.

**Campos de Informação**

- Info Field 1: Índice de dispositivo.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-device-remove"></a>Remover dispositivo de pilha de anfitrião 

#### <a name="ux_host_stack_device_remove"></a>ux_host_stack_device_remove

**Ícone** ![ Ícone de remover dispositivo de pilha de anfitrião](./media/user-guide/usbx-events/image197.png)

**Descrição**

Este evento representa um evento de remoção do dispositivo de stack do anfitrião USBX.

**Campos de Informação**

- Info Field 1: Hcd.
- Info Field 2: Pai.
- Info Field 3: Índice de Porta.
- Info Field 4: Dispositivo.

### <a name="host-stack-device-resource-free"></a>Dispositivo de pilha de anfitrião livre 

#### <a name="ux_host_stack_device_resource_free"></a>ux_host_stack_device_resource_free

**Ícone** ![ Ícone livre de recursos do dispositivo de pilha de anfitrião](./media/user-guide/usbx-events/image198.png)

**Descrição**

Este evento representa um evento gratuito de recursos do dispositivo usbx host Stack.

**Campos de Informação**

- Info Field 1: Dispositivo.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-endpoint-instance-create"></a>Host Stack Endpoint Instance Create 

#### <a name="ux_host_stack_endpoint_instance_create"></a>ux_host_stack_endpoint_instance_create

**Ícone** ![ Exemplo de ponto final de pilha de anfitrião Criar ícone](./media/user-guide/usbx-events/image199.png)

**Descrição**

Este evento representa um evento de endpoint de série de anfitrião USBX.

**Campos de Informação**

- Info Field 1: Dispositivo.
- Info Field 2: Ponto final.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-endpoint-instance-delete"></a>Exemplo de ponto final de pilha de anfitrião Eliminar 

#### <a name="ux_host_stack_endpoint_instance_delete"></a>ux_host_stack_endpoint_instance_delete

**Ícone** ![ Exemplo de endpoint de pilha de anfitrião Eliminar ícone](./media/user-guide/usbx-events/image200.png)

**Descrição**

Este evento representa um evento de eliminação de exemplo de série de anfitriões USBX.

**Campos de Informação**

- Info Field 2: Ponto final.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-endpoint-reset"></a>Reset do ponto final do ponto final da pilha de anfitrião 

#### <a name="ux_host_stack_endpoint_reset"></a>ux_host_stack_endpoint_reset

**Ícone** ![ Ícone de reset do ponto final do host Stack](./media/user-guide/usbx-events/image201.png)

**Descrição**

Este evento representa um evento de reset do ponto final da stack do anfitrião USBX.

**Campos de Informação**

- Info Field 1: Dispositivo.
- Info Field 2: Ponto final.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-endpoint-transfer-abort"></a>Abortar a transferência de ponto final do host Stack 

#### <a name="ux_host_stack_endpoint_transfer_abort"></a>ux_host_stack_endpoint_transfer_abort

**Ícone** ![ Ícone de aborto de transferência de ponto final de pilha de anfitrião](./media/user-guide/usbx-events/image202.png)

**Descrição**

Este evento representa um evento usbx host Stack Endpoint Transfer Abort.

**Campos de Informação**

- Info Field 1: Ponto final.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-host-controller-register"></a>Registo do controlador do anfitrião do anfitrião da pilha 

#### <a name="ux_host_stack_hcd_register"></a>ux_host_stack_hcd_register

**Ícone** ![ Ícone do controlador do anfitrião do anfitrião do anfitrião](./media/user-guide/usbx-events/image203.png)

**Descrição**

Este evento representa um registo do controlador anfitrião USBX.

**Campos de Informação**

- Info Field 1: Nome HCD.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-initialize"></a>Inicialize da Pilha de Anfitriões 

#### <a name="ux_host_stack_initialize"></a>ux_host_stack_initialize

**Ícone** ![ Ícone inicialize da pilha de anfitrião](./media/user-guide/usbx-events/image204.png)

**Descrição**

Este evento representa um evento usbx host Stack Initialize Event.

**Campos de Informação**

- Info Field 1: Não utilizado.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-interface-endpoint-get"></a>Host Stack Interface Endpoint Get 

#### <a name="interface_-tcp-retry-entry"></a>Interface_ TCP relemca a entrada

**Ícone** ![ Anfitrião Stack Interface Endpoint Obter ícone](./media/user-guide/usbx-events/image205.png)

**Descrição**

Este evento representa um evento interno de relemistenção netx TCP.

**Campos de Informação**

- Info Field 1: Interface.
- Info Field 2: Índice de ponto final.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-interface-instance-create"></a>Série de série de anfitrião criar 

#### <a name="ux_host_stack_interface_instance_create"></a>ux_host_stack_interface_instance_create

**Ícone** ![ Exemplo de interface de pilha de anfitrião Criar ícone](./media/user-guide/usbx-events/image206.png)

**Descrição**

Este evento representa um evento de interface de série de anfitrião USBX.

**Campos de Informação**

- Info Field 1: Interface.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-interface-instance-delete"></a>Excluir a interface da interface da pilha do anfitrião 

#### <a name="ux_host_stack_interface_instance_delete"></a>ux_host_stack_interface_instance_delete

**Ícone** ![ Exemplo de interface de pilha de anfitrião Eliminar ícone](./media/user-guide/usbx-events/image207.png)

**Descrição**

Este evento representa um evento de eliminação de instância de interface de anfitrião USBX.

**Campos de Informação**

- Info Field 1: Interface.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-interface-set"></a>Conjunto de interface de pilha de anfitrião 

#### <a name="ux_host_stack_interface_set"></a>ux_host_stack_interface_set

**Ícone** ![ Ícone de conjunto de interface de pilha de anfitrião](./media/user-guide/usbx-events/image208.png)

**Descrição**

Este evento representa um evento USBX Host Stack Interface set.

**Campos de Informação**

- Info Field 1: Interface.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-interface-setting-select"></a>Selecione de definição de interface de pilha de anfitrião 

#### <a name="ux_host_stack_interface_setting_select"></a>ux_host_stack_interface_setting_select

**Ícone** ![ Configuração de configuração da interface de pilha de anfitrião Selecionar ícone](./media/user-guide/usbx-events/image209.png)

**Descrição**

Este evento representa um evento de configuração de interface de anfitrião USBX.

**Campos de Informação**

- Info Field 1: Interface.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-new-configuration-create"></a>Host Stack Nova Configuração Criar 

#### <a name="ux_host_stack_new_configuration_create"></a>ux_host_stack_new_configuration_create

**Ícone** ![ Host Stack Nova Configuração Criar ícone](./media/user-guide/usbx-events/image210.png)

**Descrição**
 
Este evento representa um evento de configuração nova da pilha USBX.

**Campos de Informação**

- Info Field 1: Dispositivo.
- Info Field 2: Configuração.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-new-device-create"></a>Host Stack Novo Dispositivo Criar 

#### <a name="ux_host_stack_new_device_create"></a>ux_host_stack_new_device_create

**Ícone** ![ Host Stack novo dispositivo criar ícone](./media/user-guide/usbx-events/image211.png)

**Descrição**
 
 Este evento representa um evento usbx host Stack New Device Create.

**Campos de Informação**

- Info Field 1: Hcd.
- Info Field 2: Proprietário do dispositivo.
- Info Field 3: Índice de porta.
- Info Field 4: Dispositivo.

### <a name="host-stack-new-endpoint-create"></a>Host Stack Novo Ponto Final Criar 

#### <a name="ux_host_stack_new_endpoint_create"></a>ux_host_stack_new_endpoint_create

**Ícone** ![ Host Stack Novo Ponto Final Criar ícone](./media/user-guide/usbx-events/image212.png)

**Descrição**
 
Este evento representa um evento USBX Host Stack New Endpoint Create Event.

**Campos de Informação**

- Info Field 1: Interface.
- Info Field 2: Ponto final.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-root-hub-change-process"></a>Processo de mudança do hub de raiz da pilha de anfitrião 

#### <a name="ux_host_stack_rh_change_process"></a>ux_host_stack_rh_change_process

**Ícone** ![ Ícone de mudança de fundo de raiz de pilha de anfitrião](./media/user-guide/usbx-events/image213.png)

**Descrição**
 
Este evento representa um processo de mudança de raiz do hub de raiz da stack usbx.

**Campos de Informação**

- Info Field 1: Índice de porta.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-root-hub-device-extraction"></a>Extração de dispositivo de plataforma de raiz de pilha de anfitrião 

#### <a name="ux_host_stack_rh_device_extraction"></a>ux_host_stack_rh_device_extraction

**Ícone** ![ Ícone de extração de dispositivo de raiz de pilha de anfitrião](./media/user-guide/usbx-events/image214.png)

**Descrição**

Este evento representa um evento de extração de dispositivos de raiz do hub de raiz da stack usbx.

**Campos de Informação**

- Info Field 1: Hcd.
- Info Field 2: Índice de porta.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-root-hub-device-insertion"></a>Inserção do dispositivo do hub de raiz do anfitrião Stack 

#### <a name="ux_host_stack_rh_device_insertion"></a>ux_host_stack_rh_device_insertion

**Ícone** ![ Ícone de inserção do dispositivo de inserção do hub de raiz da pilha de anfitrião](./media/user-guide/usbx-events/image215.png)

**Descrição**

Este evento representa uma inserção do dispositivo de raiz do hub de raiz da stack usbx.

**Campos de Informação**

- Info Field 1: Hcd.
- Info Field 2: Índice de porta.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="host-stack-transfer-request"></a>Pedido de transferência de pilha de anfitrião 

#### <a name="ux_host_stack_transfer_request"></a>ux_host_stack_transfer_request

**Ícone** ![ Ícone de pedido de transferência de pilha de anfitrião](./media/user-guide/usbx-events/image216.png)

**Descrição**

Este evento representa um pedido de transferência usbx host stack.

**Campos de Informação**

- Info Field 1: Dispositivo.
- Info Field 2: Ponto final.
- Info Campo 3: Pedido de transferência.
- Info Field 4: Não utilizado.

### <a name="host-stack-transfer-request-abort"></a>Pedido de transferência de pilha de anfitrião abortar 

#### <a name="internal-io-driver-get-status"></a>O controlador interno de I/O obtém o estado

**Ícone** ![ Ícone de aborto de pedido de transferência de pilha de anfitrião](./media/user-guide/usbx-events/image217.png)

**Descrição**

Este evento representa um pedido de transferência usbx host Stack Abort.

**Campos de Informação**

- Info Field 1: Dispositivo.
- Info Field 2: Ponto final.
- Info Campo 3: Pedido de transferência.
- Info Field 4: Não utilizado.

### <a name="usbx-error"></a>Erro USBX 

#### <a name="ux_error"></a>ux_error

**Ícone** ![ Ícone de erro U S B X](./media/user-guide/usbx-events/image218.png)

**Descrição**

Este evento representa um Evento de Erro USBX.

**Campos de Informação**

- Info Field 1: erro USBX.
- Info Field 2: Nome de erro.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.