---
title: Capítulo 4 - Descrição dos Serviços GUIX
description: Este capítulo contém uma descrição de todos os serviços GUIX (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7a17ab0d2500d021bb9397dbf673427362c45173
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826450"
---
# <a name="chapter-4---description-of-guix-services"></a>Capítulo 4 - Descrição dos Serviços GUIX

Este capítulo contém uma descrição de todos os serviços GUIX (listados abaixo) por ordem alfabética.  

Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **GX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos. 

| **Serviço GUIX**                      | **Descrição**                                                                             |
| -------------------------------------- | -------------------------------------------------------------------------------------------- |
| gx_accordion_menu_create            | Criar menu de acordeão                                                                        |
| gx_accordion_menu_draw              | Desenhe o menu de acordeão                                                                          |
| gx_accordion_menu_event_process    | Evento do menu de acordeão de processo                                                                 |
| gx_accordion_menu_position          | Posicione os itens do menu                                                                          |
| gx_animation_canvas_define          | Forneça memória a um controlador de animação para que uma tela seja usada para animações subsequentes. |
| gx_animation_create                  | Criar um controlador de animação                                                               |
| gx_animation_delete                  | Excluir um controlador de animação                                                               |
| gx_animation_drag_disable           | Desativar o gancho de animação de arrasto de tela                                                           |
| gx_animation_drag_enable            | Ativar o gancho de animação de arrasto de tela                                                            |
| gx_animation_landing_speed_set     | Definir velocidade de aterragem para a animação de drag de tela                                                  |
| gx_animation_start                   | Iniciar uma sequência de animação                                                               |
| gx_animation_stop                    | Suspender uma sequência de animação                                                                |
| gx_binres_language_count_get      |  Recuperar a contagem de idiomas de um ficheiro de recursos binários                                          |
| gx_binres_language_info_load      |  Leia o nome da língua e as informações de tamanho a partir do ficheiro de recursos binários.                           |
| gx_binres_language_table_load      | (precotado) Carregue uma tabela linguística a partir do tampão de dados de recursos binários                          |
| gx_binres_language_table_load_ext | Carregue uma tabela linguística a partir do tampão de dados de recursos binários                                       |
| gx_binres_theme_load                | Carregue um tema a partir do tampão de dados de recursos binários                                                |
| gx_brush_default                     | Inicialize a escova de corrente para os predefinidos                                                         |
| gx_brush_define                      | Definir pincel                                                                                 |
| gx_button_background_draw           | Desenhe o fundo do botão                                                                       |
| gx_button_create                     | Botão Criar                                                                                |
| gx_button_deselect                   | Botão de desmarcação                                                                              |
| gx_button_draw                       | Desenhe botão                                                                                  |
| gx_button_event_process            | Evento de botão de processo                              |
| gx_button_select                    | Selecione botão                                     |
| gx_canvas_alpha_set                | Definir valor alfa-blend para tela                  |
| gx_canvas_arc_draw                 | Desenhar arco de círculo                                   |
| gx_canvas_block_move               | Bloco de movimento                                        |
| gx_canvas_circle_draw              | Desenhar círculo                                       |
| gx_canvas_create                    | Criar uma tela                                   |
| gx_canvas_delete                    | Apagar uma tela                                   |
| gx_canvas_drawing_complete         | Desenho completo de tela                           |
| gx_canvas_drawing_initiate         | Iniciar o desenho sobre tela                        |
| gx_canvas_ellipse_draw             | Desenhe uma elipse                                   |
| gx_canvas_hardware_layer_bind     | Ligue a tela à camada gráfica                     |
| gx_canvas_hide                      | Tornar uma tela invisível                           |
| gx_canvas_line_draw                | Linha de desenho                                         |
| gx_canvas_memory_define            | Atribuir endereço de memória de tela                      |
| gx_canvas_offset_set               | Atribuir a lona x,y despensar o ecrã                  |
| gx_canvas_pie_draw                 | Desenhe uma forma de torta (cunha)                          |
| gx_canvas_pixel_draw               | Desenhe um único pixel                               |
| gx_canvas_pixelmap_blend           | Misture um mapa de pixel com fundo                  |
| gx_canvas_pixelmap_get             | Obtenha um pixelmap apontando para dados de tela            |
| gx_canvas_pixelmap_draw            | Desenhar pixelmap                                     |
| gx_canvas_pixelmap_rotate          | Pixelmap rotativo                                   |
| gx_canvas_pixelmap_tile            | Pixelmap de azulejos                                     |
| gx_canvas_polygon_draw             | Desenhar polígono                                      |
| gx_canvas_rectangle_draw           | Desenhar retângulo                                    |
| gx_canvas_rotated_text_draw       | (precotado) Desenhar texto rotativo sobre o ponto central |
| gx_canvas_rotated_text_draw_ext  | Desenhar texto rotativo sobre o ponto central              |
| gx_canvas_shift                     | Tela de turno por x,y                               |
| gx_canvas_show                      | Faça uma tela visível                             |
| gx_canvas_text_draw                | (precotado) Desenhar texto                            |
| gx_canvas_text_draw_ext           | Desenhar texto                                         |
| gx_checkbox_create                  | Criar uma caixa de verificação                                 |
| gx_checkbox_draw                    | Desenhe uma caixa de verificação                                   |
| gx_checkbox_event_process          | Função de processo de evento de caixa de verificação                   |
| gx_checkbox_pixelmap_set           | Atribuir pixelmap de caixa de verificação                          |
| gx_checkbox_select                  | Selecione caixa de verificação                                   |
| gx_circular_gauge_angle_get       | Recuperar ângulo de agulha de widget de bitola                |
| gx_circular_gauge_angle_set       | Atribuir ângulo de agulha de widget de bitola                  |
| gx_circular_gauge_animation_set   | Definir animação de bitola circular                   |
| gx_circular_gauge_background_draw | Desenhe o fundo do bitola circular                    |
| gx_circular_gauge_create           | Criar um widget de bitola circular                    |
| gx_circular_gauge_draw             | Desenhe um widget de bitola circular                      |
| gx_circular_gauge_event_process   | Evento de bitola circular do processo                      |
| gx_context_brush_default            | Desave o pincel do contexto atual                                      |
| gx_context_brush_define             | Definir pincel do contexto atual                                       |
| gx_context_brush_get                | Obtenha pincel do contexto atual                                          |
| gx_context_brush_pattern_set       | Definir padrão da escova do contexto atual                           |
| gx_context_brush_set                | Conjunto pincel de contexto atual                                          |
| gx_context_brush_style_set         | Definir estilo de pincel de contexto atual                                    |
| gx_context_brush_width_set         | Definir largura da escova de corrente ontext                                     |
| gx_context_color_get                | Resolva um ID de cor para o valor da cor                                     |
| gx_context_fill_color_set          | Definir a cor do preenchimento do contexto atual                                     |
| gx_context_font_get                 | Resolva um ID de fonte para o valor do ponteiro de fonte                               |
| gx_context_font_set                 | Definir fonte de contexto atual                                           |
| gx_context_line_color_set          | Definir a cor da linha do contexto atual                                     |
| gx_context_pixelmap_get             | Resolva um ID pixelmap para o valor do ponteiro pixelmap                       |
| gx_context_pixelmap_set             | Atribuir pixelmap de escova, utilizado para enchimentos de área                            |
| gx_context_raw_brush_define        | Definir pincel cru do contexto atual                                   |
| gx_context_raw_fill_color_set     | Definir a cor de enchimento bruto do contexto atual                                 |
| gx_context_raw_line_color_set     | Definir a cor da linha bruta do contexto atual                                 |
| gx_context_string_get               | Obter corda associada ao contexto de desenho atual (depreciada). |
| gx_context_string_get_ext          | Obter corda associada ao contexto de desenho atual (depreciada). |
| gx_display_active_language_set     | Atribuir linguagem ativa                                                |
| gx_display_color_set                | Substitua um valor de cor na tabela de cores do display.                       |
| gx_display_color_table_set         | Atribua a tabela de cores utilizada por um ecrã                              |
| gx_display_create                    | Criar exibição                                                        |
| gx_display_delete                    | Eliminar exibição                                                        |
| gx_display_font_table_set          | Atribua a tabela de fontes utilizada por um visor                               |
| gx_display_language_table_get      | Recupere a tabela linguística associada a um visor (precotado)    |
| gx_display_language_table_get_ext | Recupere a tabela linguística associada a um visor                 |
| gx_display_language_table_set      | Atribua a tabela linguística ao visor indicado (precotado)           |
| gx_display_language_table_set_ext | Atribua a tabela linguística ao visor indicado.                       |
| gx_display_pixelmap_table_set      | Atribua a tabela pixelmap utilizada por um visor                           |
| gx_display_string_get               | Obter corda associada ao ID da corda (depreciada)                |
| gx_display_string_get_ext          | Obter corda associada com ID de corda                             |
| gx_display_string_table_get             | Recupere a tabela de cordas associada ao visor indicado (depreciado). |
| gx_display_string_table_get_ext        | Recupere a tabela de cordas associada ao visor indicado               |
| gx_display_theme_install                 | Instale temas no visor especificado                               |
| gx_drop_list_close                       | Feche a lista de lançamentos                                                       |
| gx_drop_list_create                      | Criar lista de drop                                                      |
| gx_drop_list_event_process               | Processamento de eventos de lista de lançamento                                            |
| gx_drop_list_open                        | Lista de lançamentos abertos                                                        |
| gx_drop_list_pixelmap_set               | Definir pixelmap para deixar cair lista                                             |
| gx_drop_list_popup_set                  | Definir popup para deixar cair lista                                                |
| gx_horizontal_list_children_position    | Posicione os widgets das crianças na lista horizontal                          |
| gx_horizontal_list_create                | Criar lista horizontal                                                |
| gx_horizontal_list_event_process        | Evento de processo na lista horizontal                                      |
| gx_horizontal_list_page_index_set      | Atribuir índice de página de lista horizontal                                     |
| gx_horizontal_list_selected_index_get  | Obtenha o índice de item selecionado                                           |
| gx_horizontal_list_selected_widget_get | Obtenha o widget de item selecionado                                          |
| gx_horizontal_list_selected_set         | Definir o item selecionado                                                 |
| gx_horizontal_list_total_columns_set   | Alterar número de colunas de lista após a criação                          |
| gx_horizontal_scrollbar_create           | Criar barra de deslocação horizontal                                           |
| gx_icon_button_create                    | Criar botão de ícone                                                    |
| gx_icon_button_draw                      | Desenhe um botão de ícone                                                   |
| gx_icon_button_pixelmap_set             | Definir pixelmap no botão ícone                                           |
| gx_icon_background_draw                  | Desenhar fundo de ícone                                                  |
| gx_icon_create                            | ícone Criar                                                           |
| gx_icon_draw                              | Desenhar ícone                                                             |
| gx_icon_event_process                    | Função de processamento de evento de ícone                                        |
| gx_icon_pixelmap_set                     | Definir pixelmap para ícone                                                 |
| gx_image_reader_create                   | Criar exemplo de módulo de leitor de imagem                                   |
| gx_image_reader_palette_set             | Definir paleta de leitor de imagem                                           |
| gx_image_reader_start                    | Inicie o processo de descompressão e conversão                           |
| gx_line_chart_axis_draw                 | Desenhar gráfico de linha x,y eixo                                              |
| gx_line_chart_create                     | Criar GX_LINE_CHART instância                                       |
| gx_line_chart_data_draw                 | Linha de dados de gráfico de linha                                             |
| gx_line_chart_draw                       | Desenho de gráfico de linha padrão                                            |
| gx_line_chart_update                     | Atualização de força dos dados do gráfico de linha                                       |
| gx_line_chart_y_scale_calculate        | Calcular a escala dos valores de dados do eixo y para as coordenadas de pixel.           |
| gx_menu_create                            | Criar menu                                                           |
| gx_menu_draw                              | Menu de desenho                                                             |
| gx_menu_event_process                     | Evento do menu do processo                                                    |
| gx_menu_insert                                | Inserir um novo item                                                               |
| gx_menu_remove                                | Remover um item                                                                  |
| gx_menu_text_draw                            | Desenhar texto do menu                                                                  |
| gx_menu_text_offset_set                     | Definir design de texto de texto offset                                                       |
| gx_multi_line_text_button_create           | Criar botão de texto multi-linha                                                   |
| gx_multi_line_text_button_draw             | Desenhar botão de texto multi-linha                                                     |
| gx_multi_line_text_button_event_process   | Definir fonte para botão de texto multi-linha                                             |
| gx_multi_line_text_button_text_draw       | Porção de desenho de texto do desenho                                                 |
| gx_multi_line_text_button_text_id_set    | Definir a cadeia do sistema para o botão de texto                                                |
| gx_multi_line_text_button_text_set        | Atribuir a cadeia definida pelo utilizador ao botão de texto (precotado)                          |
| gx_multi_line_text_button_text_set_ext   | Atribua a cadeia definida pelo utilizador ao botão de texto                                       |
| gx_multi_line_text_input_backspace         | Elimine o carácter antes da posição do cursor de entrada de texto multi-linha               |
| gx_multi_line_text_input_buffer_get       | Recupera informações tampão do widget de entrada de texto                               |
| gx_multi_line_text_input_buffer_clear     | Elimina todos os caracteres do tampão de entrada de texto                               |
| gx_multi_line_text_input_char_insert      | Insira a cadeia de formato UTF8 na posição do cursor de entrada de texto multi-linha (precotado) |
| gx_multi_line_text_input_char_insert_ext | Insira a cadeia de formato UTF8 na posição do cursor de entrada de texto multi-linha              |
| gx_multi_line_text_input_create            | Criar entrada de texto multi-linha                                                    |
| gx_multi_line_text_input_cursor_pos_get  | Recupere a posição do cursor de entrada de texto multi-linha                                  |
| gx_multi_line_text_input_delete            | Elimine o personagem após a posição do cursor de entrada de texto multiline                 |
| gx_multi_line_text_input_down_arrow       | Mova o cursor de entrada de texto multi-linha para a linha seguinte                              |
| gx_multi_line_text_input_end               | Mova o cursor de entrada de texto multi-linha para o fim da linha atual                |
| gx_multi_line_text_input_event_process    | Processar texto de entrada de texto multi-linha                                              |
| gx_multi_line_text_input_fill_color_set  | Definir cores de preenchimento para entrada de texto de várias linhas                                       |
| gx_multi_line_text_input_home              | Mova o cursor de entrada de texto multi-linha para o início da linha atual              |
| gx_multi_line_text_input_left_arrow       | Mover cursor de entrada de texto multi-linha deixado por um personagem                         |
| gx_multi_line_text_input_right_arrow      | Mover cursor de entrada de texto multi-linha direito por um personagem                        |
| gx_multi_line_text_input_style_add        | Adicione bandeiras de estilo de texto multi-linha                                                 |
| gx_multi_line_text_input_style_remove     | Remova bandeiras de estilo de texto multi-linha                                              |
| gx_multi_line_text_input_style_set        | Atribuir bandeiras de estilo de texto multi-linha                                              |
| gx_multi_line_text_input_text_color_set  | Atribua cores de texto para entrada de texto multi linha                                    |
| gx_multi_line_text_input_text_select      | Selecione texto de entrada de texto de várias linhas                                               |
| gx_multi_line_text_input_text_set         | Atribuir texto à entrada de texto de várias linhas (precotado)                               |
| gx_multi_line_text_input_text_set_ext          | Atribuir texto à entrada de texto de várias linhas                         |
| gx_multi_line_text_input_up_arrow               | Mova o cursor de entrada de texto de várias linhas para a linha anterior       |
| gx_multi_line_text_view_create                   | Criar vista de texto multi-linha                                  |
| gx_multi_line_text_view_event_process           | Evento de visualização de texto multi-linha de processo                           |
| gx_multi_line_text_view_font_set                | Definir fonte usada na vista de texto de várias linhas                        |
| gx_multi_line_text_view_line_space_set         | Definir espaço de linha de vista de texto multi-linha                          |
| gx_multi_line_text_view_scroll_info_get        | Obtenha informações de pergaminho de visão de texto multi-linha                         |
| gx_multi_line_text_view_text_color_set         | Definir a cor do texto na vista de texto da linha de mulit                       |
| gx_multi_line_text_view_text_id_set            | Definir cadeia de texto do sistema na vista de texto de várias linhas               |
| gx_multi_line_text_view_text_set                | Definir a cadeia definida pelo utilizador para a vista de texto de várias linhas (depreciada) |
| gx_multi_line_text_view_text_set_ext           | Definir a cadeia definida pelo utilizador para a visão de texto de várias linhas              |
| gx_multi_line_text_view_whitespace_set          | Definir visão de texto multi-linhas espaço em branco                          |
| gx_numeric_pixelmap_prompt_create                 | Criar pedido de pixelmap numérico                               |
| gx_numeric_pixelmap_prompt_format_ function_set | Função de formato de substituição do pixelmap numérico          |
| gx_numeric_pixelmap_prompt_value_set             | Definir valor de solicitação numérica                                     |
| gx_numeric_prompt_create                           | Criar um pedido numérico                                        |
| gx_numeric_prompt_format_function_set            | Função de formato de substituição de solicitação numérica                   |
| gx_numeric_prompt_value_set                       | Definir valor de solicitação numérica                                     |
| gx_numeric_scroll_wheel_create                    | Criar widget de roda de pergaminho numérico                           |
| gx_numeric_scroll_wheel_range_set                | Atribuir gama de valor da roda de deslocação                              |
| gx_pixelmap_button_create                          | Criar botão pixelmap                                       |
| gx_pixelmap_button_draw                            | Desenhe o botão pixelmap                                         |
| gx_pixelmap_button_event_process                  | Processamento de eventos de botão Pixelmap                             |
| gx_pixelmap_button_pixelmap_set                   | Definir pixelmap no botão pixelmap                              |
| gx_pixelmap_prompt_create                          | Criar pixelmap                                       |
| gx_pixelmap_prompt_draw                            | Desenhe o pixelmap                                         |
| gx_pixelmap_prompt_pixelmap_set                   | Definir pixelmap em pixelmap prompt                              |
| gx_pixelmap_slider_create                          | Criar slider de mapas de pixel                                       |
| gx_pixelmap_slider_draw                            | Desenhe o slider do pixelmap                                         |
| gx_pixelmap_slider_event_process        | Processamento de eventos de slider Pixelmap       |
| gx_pixelmap_slider_pixelmap_set         | Definir pixelmap no slider pixelmap        |
| gx_progress_bar_background_draw         | Desenhar fundo de barra de progresso           |
| gx_progress_bar_create                   | Criar uma barra de progresso                  |
| gx_progress_bar_draw                     | Desenhar uma barra de progresso                    |
| gx_progress_bar_event_process           | Processar um evento de barras de progresso           |
| gx_progress_bar_font_set                | Fonte de conjunto de texto de barra de progresso          |
| gx_progress_bar_info_set                | Definir estrutura de informação de barra de progresso |
| gx_progress_bar_pixelmap_set            | Definir pixelmap usado para desenhar barra de progresso |
| gx_progress_bar_range_set               | Gama de valor definido da barra de progresso        |
| gx_progress_bar_text_color_set         | Definir a cor do texto da barra de progresso            |
| gx_progress_bar_text_draw               | Desenhar texto de barra de progresso                 |
| gx_progress_bar_value_set               | Definir valor da barra de progresso                 |
| gx_prompt_create                          | Criar o pedido                          |
| gx_prompt_draw                            | Desenhe o pedido de sorteio                            |
| gx_prompt_event_process                   | Evento de solicitação de processo                   |
| gx_prompt_font_set                       | Definir fonte de origem                        |
| gx_prompt_text_color_set                | Definir a cor do texto do pedido de aviso                  |
| gx_prompt_text_draw                      | Porção de desenho de texto do sorteio rápido    |
| gx_prompt_text_get                       | Obtenha texto rápido (precotado)           |
| gx_prompt_text_get_ext                  | Obtenha texto rápido                        |
| gx_prompt_text_id_set                   | Definir o pedido com a cadeia de texto do sistema     |
| gx_prompt_text_set                       | Definir texto de solicitação (precotado)           |
| gx_prompt_text_set_ext                  | Definir texto de solicitação                        |
| gx_radial_progress_bar_anchor_set      | Definir ângulo de partida                     |
| gx_radial_progress_bar_background_draw | Desenhar fundo de barra de progresso radial    |
| gx_radial_progress_bar_create           | Criar uma barra de progresso radial           |
| gx_radial_progress_bar_draw             | Desenhe uma barra de progresso radial             |
| gx_radial_progress_bar_event_process   | Evento de barra de progresso radial de processo      |
| gx_radial_progress_bar_font_set        | Definir fonte de barra de progresso radial           |
| gx_radial_progress_bar_info_set        | Definir informações de barras de progresso radial    |
| gx_radial_progress_bar_text_color_set | Definir cor de texto de barra de progresso radial     |
| gx_radial_progress_bar_text_draw       | Desenhar texto de barra de progresso radial          |
| gx_radial_progress_bar_value_set       | Definir valor da barra de progresso radial          |
| gx_radio_button_create                   | Criar botão de rádio                    |
| gx_radio_button_draw                     | Desenhe botão de rádio                      |
| gx_radio_button_pixelmap_set            | Definir pixelmap no botão de rádio           |
| gx_radial_slider_anchor_angles_set     | Definir lista de ângulo de âncora de slider radial    |
| gx_radial_slider_angle_set              | Definir ângulo de slider radial                |
| gx_radial_slider_animation_set          | Definir informações de animação de slider radial       |
| gx_radial_slider_animation_start               | Definir ângulo de slider radial com animação                      |
| gx_radial_slider_create                         | Criar um deslizador radial                                      |
| gx_radial_slider_draw                           | Desenhe um deslizador radial                                        |
| gx_radial_slider_event_process                 | Processar um evento de slider radial                               |
| gx_radial_slider_info_get                      | Recuperar o ponteiro de informação do slider radial                  |
| gx_radial_slider_info_set                      | Definir informações de slider radial                               |
| gx_radial_slider_pixelmap_set                  | Definir pixelmaps de slider radial                                 |
| gx_rich_text_view_create                       | Criar uma rica vista de texto                                     |
| gx_rich_text_view_draw                         | Desenhar vista de texto rica                                         |
| gx_rich_text_view_set_fonts                    | Definir fontes de vista de texto ricas                                    |
| gx_rich_text_view_text_draw                    | Desenhar texto de vista de texto rico                                    |
| gx_screen_stack_create                          | Crie o bloco de controlo da pilha de ecrã GUIX e a área da memória. |
| gx_screen_stack_pop                             | Coloque o ecrã superior da pilha de ecrã.                   |
| gx_screen_stack_push                            | Empurre o ecrã atual para a pilha de ecrã.                |
| gx_screen_stack_reset                           | Redefinir a pilha de ecrã                                      |
| gx_scroll_wheel_create                          | Criar widget de roda de roda de deslocação base                             |
| gx_scroll_wheel_event_process                  | Processamento de eventos de roda de deslocação                               |
| gx_scroll_wheel_gradient_alpha_set            | Modificar o gradiente de sobreposição da roda de deslocação                        |
| gx_scroll_wheel_row_height_set                | Atribuir a altura da linha da roda do pergaminho                              |
| gx_scroll_wheel_selected_background_set       | Atribuir imagem de fundo para linha selecionada                    |
| gx_scroll_wheel_selected_get                   | Recuperar índice de linha selecionado                                 |
| gx_scroll_wheel_selected_set                   | Atribuir índice de linha selecionado                                   |
| gx_scroll_wheel_speed_set                      | Atribuir velocidade de deslocamento                                      |
| gx_scroll_wheel_total_rows_set                | Atribuir o número total de linhas disponíveis                       |
| gx_scrollbar_draw                                | Desenhar barra de deslocal                                              |
| gx_scrollbar_event_process                      | Evento de barra de pergaminho de processo                                     |
| gx_scrollbar_limit_check                        | Verifique o limite da barra de deslocação                                       |
| gx_scrollbar_reset                               | Barra de deslocamento de reset                                             |
| gx_scrollbar_value_set                          | Atribuir valor da barra de deslocação                                      |
| gx_single_line_text_input_backspace           | Lidar com o personagem do backspace                                  |
| gx_single_line_text_input_buffer_clear       | Limpe o tampão de caráter                                  |
| gx_single_line_text_input_buffer_get         | Recuperar ponteiro tampão                                     |
| gx_single_line_text_input_character_delete   | Eliminar o carácter                                            |
| gx_single_line_text_input_character_insert   | Inserir caráter                                            |
| gx_single_line_text_input_create              | Criar entrada de texto de linha única                               |
| gx_single_line_text_input_draw                | Desenhe o widget de entrada de texto de linha única                          |
| gx_single_line_text_input_draw_position_get | Recuperar a posição de início do desenho de texto                           |
| gx_single_line_text_input_end                 | Mover cursor para terminar                                          |
| gx_single_line_text_input_event_process      | Processamento de eventos de entrada de texto                                 |
| gx_single_line_text_input_fill_color_set    | Definir cores de preenchimento para entrada de texto de linha única                  |
| gx_single_line_text_input_home                | Mover cursor para casa                                         |
| gx_single_line_text_input_left_arrow         | Cabo chave de seta esquerda                                       |
| gx_single_line_text_input_position_get       | Obter posição de cursor                                         |
| gx_single_line_text_input_right_arrow        | Cabo chave de seta direita                                      |
| gx_single_line_text_input_style_add          | Adicionar bandeiras de estilo                                             |
| gx_single_line_text_input_style_remove       | Remover bandeiras de estilo                                          |
| gx_single_line_text_input_style_set          | Atribuir bandeiras de estilo                                          |
| gx_single_line_text_input_text_color_set  | Definir cores de texto para entrada de texto de linha única                      |
| gx_single_line_text_input_text_select     | Selecione texto de entrada de texto de linha única                              |
| gx_single_line_text_input_text_set        | Definir texto de entrada de texto de linha única (precotado)                    |
| gx_single_line_text_input_text_set_ext    | Definir texto de entrada de texto de linha única                                 |
| gx_slider_create                          | Criar slider                                                   |
| gx_slider_draw                            | Desenhe o slider                                                     |
| gx_slider_event_process                   | Evento de slider de processo                                            |
| gx_slider_info_set                        | Definir bloco de informações de slider                                    |
| gx_slider_needle_draw                     | Desenhe a agulha de slider                                              |
| gx_slider_needle_position_get             | Obtenha a posição da agulha deslizante                                      |
| gx_slider_tickmarks_draw                  | Desenhe marcas de carraças de slider                                           |
| gx_slider_travel_get                      | Obtenha viagens de slider                                               |
| gx_slider_value_calculate                 | Calcular o valor do slider                                          |
| gx_slider_value_set                       | Definir valor de slider                                                |
| gx_sprite_create                          | Criar widget GX_SPRITE                                         |
| gx_sprite_current_frame_set               | Atribua quadro de exibição de corrente para widget sprite                  |
| gx_sprite_frame_list_set                  | Atribuir ou modificar uma lista de quadros sprite                            |
| gx_sprite_start                           | Inicie uma sequência de sprite                                         |
| gx_sprite_stop                            | Pare uma sequência de sprite                                          |
| gx_string_scroll_wheel_create             | Criar `GX_STRING_SCROLL_WHEEL` widget                          |
| gx_string_scroll_wheel_event_process      | Evento de roda de roda de cadeia de processo                               |
| gx_string_scroll_wheel_string_id_list_set | Atribuir matriz de IDs de cordas                                      |
| gx_string_scroll_wheel_string_list_set    | Modificar a matriz de cordas exibida                                   |
| gx_string_scroll_wheel_text_get           | Recuperar texto para a linha da roda de deslocação                              |
| gx_studio_widget_create                   | Criar widget definido dentro do Estúdio                             |
| gx_studio_named_widget_create             | Criar ecrã definido dentro do Estúdio                             |
| gx_studio_display_configure               | Criar e `GX_DISPLAY` `GX_CANVAS` inicializar, e `GX_WINDOW_ROOT` |
| gx_system_active_language_set             | Atribuir iD de linguagem ativa                                       |
| gx_system_canvas_refresh                  | Atualização de força (desenho) de telas sujas                       |
| gx_system_dirty_mark                      | Área de marca suja                                                 |
| gx_system_dirty_partial_add               | Marque área parcial suja                                         |
| gx_system_draw_context_get                | Obtenha contexto de desenho                                             |
| gx_system_event_fold                      | Evento Dobrável                                                       |
| gx_system_event_send                      | Enviar evento                                                      |
| gx_system_focus_claim                     | Foco de reclamação                                                     |
| gx_system_initialize                      | Inicializar GUIX                                                 |
| gx_system_language_table_get              | Recuperar tabela linguística                                         |
| gx_system_language_table_set              | Atribuir tabela linguística                                           |
| gx_system_memory_allocator_set            | Atribuir alocador de memória/desatributor                            |
| gx_system_pen_configure                  | Configuração da caneta definida                                  |
| gx_system_screen_stack_create           | Criar controlo de pilha de ecrã                            |
| gx_system_screen_stack_get              | Recuperar ponteiros de pilha de tela                         |
| gx_system_screen_stack_pop              | Pop ecrã superior da pilha de tela                       |
| gx_system_screen_stack_push             | Empurre o ecrã indicado para a pilha de ecrã              |
| gx_system_screen_stack_reset            | Redefinir a pilha de ecrã                                 |
| gx_system_scroll_appearance_get         | Obtenha aparência de pergaminho                                  |
| gx_system_scroll_appearance_set         | Definir aparência de pergaminho                                  |
| gx_system_start                           | Iniciar GUIX                                             |
| gx_system_string_get                     | Obter corda                                             |
| gx_system_string_table_get              | Obter mesa de cordas                                       |
| gx_system_string_table_set              | Definir tabela de cordas                                       |
| gx_system_string_width_get              | Obtenha a largura da corda (depreciada)                          |
| gx_system_string_width_get_ext         | Obtenha largura de corda                                       |
| gx_system_theme_install                  | Instalar tabelas de fonte/cor/pixelmap                     |
| gx_system_timer_start                    | Temporizador de início                                            |
| gx_system_timer_stop                     | Parar o temporizador                                             |
| gx_system_version_string_get            | Obter a cadeia de versão da biblioteca GUIX (depreciada)      |
| gx_system_version_string_get_ext       | Recuperar a versão da biblioteca GUIX                   |
| gx_system_widget_find                    | Encontre widget                                            |
| gx_text_button_create                    | Criar botão de texto                                     |
| gx_text_button_draw                      | Desenhe botão de texto                                       |
| gx_text_button_event_process             | Evento de botão de texto do processo                              |
| gx_text_button_font_set                 | Definir fonte para botão de texto                               |
| gx_text_button_text_color_set          | Definir cor de botão de texto                                  |
| gx_text_button_text_draw                | Porção de desenho de texto do desenho do botão                 |
| gx_text_button_text_get                 | Obtenha texto utilizado no botão de texto (precotado)              |
| gx_text_button_text_get_ext            | Obter texto usado no botão de texto                           |
| gx_text_button_text_id_set             | Atribuir cadeia de sistema ao botão de texto                    |
| gx_text_button_text_set                 | Atribuir a cadeia definida pelo utilizador ao botão de texto (precotado) |
| gx_text_button_text_set_ext            | Atribua a cadeia definida pelo utilizador ao botão de texto              |
| gx_text_scroll_wheel_callback_set      | Atribuir a chamada de recuperação de cordas (depreciada)          |
| gx_text_scroll_wheel_callback_set_ext | Atribuir chamada de recuperação de cordas                       |
| gx_text_scroll_wheel_create             | Criar roda de pergaminho de texto base                          |
| gx_text_scroll_wheel_draw               | Função de desenho da roda de rolo textual                  |
| gx_text_scroll_wheel_event_process      | Evento de roda de pergaminho de texto do processo                        |
| gx_text_scroll_wheel_font_set          | Atribuir fontes de roda de deslocação de texto                         |
| gx_text_scroll_wheel_text_color_set   | Atribuir cores de texto de roda de rolo de texto de texto de texto                   |
| gx_tree_view_create                    | Cretae uma vista de árvore                          |
| gx_tree_view_draw                      | Desenhar vista de árvore                              |
| gx_tree_view_event_process            | Evento de visão de árvore de processo                     |
| gx_tree view_indentation_set           | Conjunto de recuo da vista da árvore                   |
| gx_tree_view_position                  | Posicione os itens de vista da árvore                    |
| gx_tree_view_root_line_color_set    | Definir cor de linha de raiz de vista de árvore               |
| gx_tree_view_root_pixelmap_set       | Pixelmaps de raiz de raiz de árvore definido                |
| gx_tree_view_selected_get             | Recuperar item selecionado                      |
| gx_tree_view_selected_set             | Definir item selecionado                           |
| gx_utility_canvas_to_bmp              | Converter memória de lona para formato bitmap      |
| gx_utility_circle_point_get           | Ponto de cálculo num círculo               |
| gx_utility_gradient_create             | Criar um mapa de pixel gradiente                  |
| gx_utility_gradient_delete              | Eliminar um pixelmap gradiente                  |
| gx_utility_ltoa                         | Converter inteiros longos para ASCII               |
| gx_utility_math_acos                   | Cosine do arco compute                          |
| gx_utility_math_asin                   | Sine arco compute                             |
| gx_utility_math_cos                    | Cosine computacional                              |
| gx_utility_math_sin                    | Seno computacional                                |
| gx_utility_math_sqrt                   | Raiz quadrada computacional                         |
| gx_utility_bidi_paragraph_reorder         | Reencomendar o texto BiDi na sua ordem de exibição|
| gx_utility_bidi_resolved_text_info_delete | Eliminar texto BiDi reordenado               |
| gx_utility_pixelmap_resize             | Redimensionar pixelmap                             |
| gx_utility_pixelmap_rotate             | Rode o pixelmap por ângulo arbitrário          |
| gx_utility_pixelmap_simple_rotate      | Rode o pixelmap em 90, 180, 270 graus     |
| gx_utility_rectangle_center            | Retângulo central dentro de outro retângulo   |
| gx_utility_rectangle_center_find      | Encontre o centro do retângulo                    |
| gx_utility_rectangle_combine           | Combine dois retângulos em primeiro           |
| gx_utility_rectangle_compare           | Compare dois retângulos                      |
| gx_utility_rectangle_define            | Definir retângulo                            |
| gx_utility_rectangle_resize            | Redimensionar resize o retângulo                            |
| gx_utility_rectangle_overlap_detect   | Detetar sobreposição de retângulos                |
| gx_utility_rectangle_point_detect     | Detetar se o ponto reside no retângulo        |
| gx_utility_rectangle_shift             | Retângulo de mudança                             |
| gx_utility_string_to_alphamap         | Renderizar a cadeia de texto à alfamap (precotado) |
| gx_utility_string_to_alphamap_ext    | Renderizar a cadeia de texto para alfamap              |
| gx_vertical_list_children_position    | Posicione as crianças na lista vertical          |
| gx_vertical_list_create                | Criar lista vertical                        |
| gx_vertical_list_event_process        | Evento de lista vertical de processo                 |
| gx_vertical_list_selected_index_get  | Obtenha o índice de item selecionado                     |
| gx_vertical_list_selected_widget_get | Obtenha widget selecionado                         |
| gx_vertical_list_selected_set         | Definir entrada na lista vertical                  |
| gx_vertical_list_total_rows_set      | Alterar número de filas de listas após a criação   |
| gx_vertical_scrollbar_create           | Criar barra de deslocação vertical                   |
| gx_widget_allocate                      | Alocar dinamicamente um widget               |
| gx_widget_attach                        | Anexar widget ao progenitor                     |
| gx_widget_background_draw              | Desenhe o fundo do widget                      |
| gx_widget_back_attach                  | Anexar widget nas traseiras                       |
| gx_widget_back_move                    | Mova o widget para trás                         |
| gx_widget_block_move                   | Bloco de movimento de pixels                        |
| gx_widget_border_draw                  | Desenhar a fronteira do widget                          |
| gx_widget_border_style_set            | Definir estilo de fronteira widget                     |
| gx_widget_border_width_get            | Definir largura de fronteira widget                     |
| gx_widget_canvas_get               | Obtenha tela widget                                                         |
| gx_widget_child_detect             | Detetar criança widget                                                       |
| gx_widget_children_draw            | Desenhe crianças widget                                                      |
| gx_widget_client_get               | Obtenha a área do cliente widget                                                    |
| gx_widget_color_get                | Resolva o ID de cor ao valor de cor para um widget visível                      |
| gx_widget_create                    | Criar widget                                                             |
| gx_widget_created_test             | Teste se widget criado                                                    |
| gx_widget_delete                    | Eliminar widget                                                             |
| gx_widget_detach                    | Widget detach do progenitor                                                 |
| gx_widget_draw                      | Desenhar widget                                                               |
| gx_widget_draw_set                 | Definir função de desenho do widget                                               |
| gx_widget_event_generate           | Gerar evento widget                                                     |
| gx_widget_event_process            | Evento widget de processo                                                      |
| gx_widget_event_process_set       | Definir função de processamento de eventos de widget                                   |
| gx_widget_event_to_parent         | Enviar evento para o pai do Widget                                             |
| gx_widget_fill_color_set          | Atribuir a cor do preenchimento de widget                                                  |
| gx_widget_find                      | Encontre widget                                                               |
| gx_widget_first_child_get         | Devolva o ponteiro ao primeiro filho                                             |
| gx_widget_focus_next               | Mova o foco de entrada para o próximo widget                                           |
| gx_widget_focus_previous           | Mova o foco de entrada para o widget anterior                                       |
| gx_widget_font_get                 | Resolva o ID do tipo de letra a um ponteiro de fonte para um widget visível                    |
| gx_widget_free                      | Memória gratuita do bloco de controlo widget                                          |
| gx_widget_front_move               | Mova o widget para a frente                                                      |
| gx_widget_height_get               | Obtenha a altura do widget                                                         |
| gx_widget_hide                      | Ocultar widget                                                               |
| gx_widget_last_child_get          | Ponteiro de volta para o último filho                                              |
| gx_widget_next_sibling_get        | Devolva o ponteiro para o próximo irmão                                            |
| gx_widget_parent_get               | Devolva o ponteiro ao widget dos pais                                           |
| gx_widget_pixelmap_get             | Resolva o ID pixelmap a um ponteiro pixelmap para um widget visível            |
| gx_widget_previous_sibling_get    | Ponteiro de retorno para irmão anterior                                        |
| gx_widget_resize                    | Redimensionar widget                                                             |
| gx_widget_shift                     | Widget de turno                                                              |
| gx_widget_show                      | Mostrar widget                                                               |
| gx_widget_status_add               | Adicionar o estado do widget                                                         |
| gx_widget_status_get               | Recupere as bandeiras do estado do widget                                              |
| gx_widget_status_remove            | Remover o estado do widget                                                      |
| gx_widget_string_get               | Obter corda associada ao ID da corda para widget visível (precotado) |
| gx_widget_string_get_ext          | Recupere a corda associada ao ID da corda para widget visível.             |
| gx_widget_status_test              | Estado do widget de teste                                                        |
| gx_widget_style_add                | Adicione estilo widget                                                          |
| gx_widget_style_get                | Recupere bandeiras de estilo widget                                               |
| gx_widget_style_remove             | Remova o estilo widget                                                       |
| gx_widget_style_set                | Definir estilo widget                                                          |
| gx_widget_text_blend               | Renderizar texto misturado sobre widget (preced)                              |
| gx_widget_text_blend_ext          | Renderizar texto misturado sobre widget                                           |
| gx_widget_text_draw                | Renderizar texto sobre widget (preced)                                      |
| gx_widget_text_draw_ext           | Renderizar texto sobre widget                                            |
| gx_widget_text_id_draw            | Render texto identificado por ID de cadeia sobre widget                           |
| gx_widget_top_visible_child_find | Devolva o ponteiro à criança visível que é desenhada no topo da ordem Z   |
| gx_widget_type_find                | Encontre o tipo de widget                                                          |
| gx_widget_width_get                | Obtenha largura de widget                                                          |
| gx_window_canvas_set               | Definir tela de janela                                                         |
| gx_window_client_height_get       | Obtenha a altura do cliente da janela                                                  |
| gx_window_client_scroll            | Percorra clientes da janela                                                     |
| gx_window_client_width_get        | Obtenha a largura do cliente da janela                                                   |
| gx_window_close                     | Terminar a execução da janela modal                                          |
| gx_window_create                    | Criar janela                                                             |
| gx_window_draw                      | Desenhar janela                                                               |
| gx_window_event_process            | Evento de janela de processo                                                      |
| gx_window_execute                   | Execução de janelas modais                                                    |
| gx_window_root_create              | Criar janela de raiz                                                        |
| gx_window_root_delete              | Destrua a janela da raiz                                                       |
| gx_window_root_event_process      | Evento de processo para janela de raiz                                             |
| gx_window_root_find                | Encontre a janela da raiz                                                          |
| gx_window_scroll_info_get         | Obtenha informações de pergaminho de janela                                                    |
| gx_window_scrollbar_find           | Encontre a barra de pergaminho da janela                                                     |
| gx_window_wallpaper_get            | Obter papel de parede da janela                                                      |
| gx_window_wallpaper_set            | Definir papel de parede da janela                                                      |

## <a name="gx_accordion_menu_create"></a>gx_accordion_menu_create

Criar um menu de acordeão

### <a name="prototype"></a>Prototype

```C
UINT gx_accordion_menu_create(
    GX_ACCORDION_MENU *accordion,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    ULONG style ,
    USHORT accordion_menu_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria um menu de acordeão conforme especificado e anexa o menu de acordeão ao widget dos pais fornecido. Um menu de acordeão é um widget de visualização do menu anexpanding/collapsing. Aceita todos os tipos de widget como os seus itens de menu infantil. Os menus de acordeão podem ser aninhados, o que significa que vários níveis de profundidade do menu podem ser criados.

Para inserir um item infantil num widget de item de menu, é recomendado usar GX_MENU tipo widget como um item do menu dos pais.

Dicas para criar um menu de acordeão de nível único:

1.  Crie um menu de acordeão.

2.  Fixe GX_MENU widgets de tipo ao menu de acordeão.

3.  Ligue os widgets das crianças ao GX_MENU tipo de progenitor. O tipo de artigo de criança pode ser qualquer tipo de widget GUIX.

Dicas para criar menu de acordeão de vários níveis:

1.  Crie um menu de acordeão.

2.  Fixe GX_MENU widgets de tipo ao menu de acordeão.

3.  Fixe GX_ACCORDION_MENU widget do tipo ao progenitor do tipo GX_MENU.

4.  Anexe os itens do menu ao GX_ACCORDION_MENU tipo de pai, conforme descrito na criação do menu de acordeão de nível único.

### <a name="parameters"></a>Parâmetros

- **acordeão** Ponteiro para bloco de controlo do menu de acordeão
- **nome** Nome do menu de acordeão
- **pai** Ponteiro para widget dos pais
- **estilo** Estilo do widget. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **accordion_menu_id** ID definido pela aplicação do menu de acordeão
- **tamanho** Tamanho do menu de acordeão

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Criação de menu de acordeão bem-sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_ACCORDION_MENU my_accordion;
GX_MENU menu_1;
GX_MENU item_1;
GX_RECTANGLE size;

gx_utility_rectangle_define(&size, 100, 100, 300, 150);

status = gx_accordion_menu_create(&my_accordion, “my_accordion”,
                                  parent, GX_STYLE_ENABLED,
                                  MY_ACCORDION_ID, &size);

gx_menu_create(&menu_1, “menu_1”, &my_accordion,
               GX_STRING_ID_MENU_1, GX_ID_NONE,
               GX_STYLE_ENABLED | GX_TYLE_BORDER_THIN, 0, &size);

gx_menu_create(&item_1, “item_1”, &my_accordion,
               GX_STRING_ID_ITEM_1, GX_ID_NONE,
               GX_STYLE_ENABLED | GX_STYLE_BORDER_THIN, 0, &size);

gx_text_offset_set(&item_1, 30, 0);

gx_menu_insert(&menu_1, &item_1);

/* If status is GX_SUCCESS the accordion menu was successfully created. */

```

A aplicação de demonstração demo_guix_widget_types, fornecida como parte da instalação do GUIX Studio, fornece um exemplo completo de utilização do widget do menu de acordeão.

### <a name="see-also"></a>Consulte também

- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_accordion_menu_draw"></a>gx_accordion_menu_draw

Desenhe o menu de acordeão

### <a name="prototype"></a>Prototype

```C
VOID gx_accordion_menu_draw(GX_ACCORDION_MENU *accordion);
```

### <a name="description"></a>Descrição

Este serviço desenha o menu de acordeão especificado. Este serviço é normalmente chamado internamente pelo mecanismo de atualização de lona GUIX, mas está exposto à aplicação para ajudar na implementação de funções de desenho personalizado para widgets personalizados do menu de acordeão.

### <a name="parameters"></a>Parâmetros

- **acordeão** Ponteiro para bloco de controlo do menu de acordeão

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Define a custom accordion menu draw function */

VOID my_accordion_menu_draw(GX_ACCORDION_MENU *accordion)
{
    /* Call default accordion menu draw. */
    gx_accordion_menu_draw(accordion);

    /* Add custom drawing here. */
}

```

### <a name="see-also"></a>Consulte também

- gx_accordion_menu_create
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_accordion_menu_event_process"></a>gx_accordion_menu_event_process

Evento do menu de acordeão de processo

### <a name="prototype"></a>Prototype

```C
UINT gx_accordion_menu_event_process(
    GX_ACCORDION_MENU *accordion, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Descrição

Este serviço processa um evento para o menu de acordeão especificado. Este serviço deve ser chamado como o manipulador de eventos predefinido por quaisquer funções de processamento de eventos de acordeão personalizado.

Este serviço lida com eventos GX_EVENT_PEN_DOWN e GX_EVENT_PEN_UP para expandir/colapsar um item de menu.

### <a name="parameters"></a>Parâmetros

- **acordeão** Ponteiro para bloco de controlo do menu de acordeão
- **event_ptr** Ponteiro para o evento para processar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Processo de evento do menu de acordeão bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Call generic accordion menu event processing as part of custom event processing function. */

UINT custom_accordion_event_process( 
    GX_ACCORDION_MENU *accordion,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default accordion menu
            event processing */
        status =
        gx_accordion_menu_event_process(accordion, event);
        break;
    }
    return status;
}

```

### <a name="see-also"></a>Consulte também

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_accordion_menu_position"></a>gx_accordion_menu_position

Posicione os itens do menu

### <a name="prototype"></a>Prototype

```C
UINT gx_accordion_menu_position(GX_ACCORDION_MENU *accordion);
```

### <a name="description"></a>Descrição

Este serviço posiciona os itens de menu para o menu de acordeão. Esta função é normalmente chamada internamente quando o menu de acordeão está a tornar-se visível. Se pretender inserir/remover itens de/para um menu de acordeão ou alterar os estilos de expansão do item da criança, esta função deve ser chamada para reposicionar os itens da criança.

### <a name="parameters"></a>Parâmetros

- **acordeão** Ponteiro para bloco de controlo do menu de acordeão

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Posição do menu de acordeão bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Position menu items in the accordion menu “my_accordion” */
status = gx_accordion_menu_position (&my_accordion);

/* If status is GX_SUCCESS the children in the accordion menu
“my_accordion” are positioned. */

```

### <a name="see-also"></a>Consulte também

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_animation_canvas_define"></a>gx_animation_canvas_define

Fornecer memória de tela a um controlador de animação

### <a name="prototype"></a>Prototype

```C
UINT gx_animation_canvas_define(
    GX_ANIMATION *animation, 
    GX_CANVAS *canvas);
```

### <a name="description"></a>Descrição

Este serviço fornece uma tela de memória a um controlador de animação usado para implementar a sequência de animação. Esta tela fornecida deve ser grande o suficiente para manter o widget alvo de animação.

Quando uma tela de animação é definida, o widget alvo é desenhado uma vez para esta tela de animação, e o efeito de deslizamento ou desvanecimento do ecrã é realizado modificando o valor alfa de lona e/ou lona alfa. Quando o suporte de hardware para várias camadas gráficas é fornecido, definir uma tela de animação que está ligada a uma camada de sobreposição de gráficos de hardware pode melhorar ***muito*** o desempenho de animações de slide e fade.

O gestor de animação requer uma tela de animação para executar tipos de animação desvanecimento e desvanecimento se correr a profundidade de cor inferior a 16 bpp.

### <a name="parameters"></a>Parâmetros

- **animação** Ponteiro para bloco de controlo de animação
- **tela** Tela de memória usada para implementar a animação de tradução.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Tela de animação definida com sucesso
- **GX_INVALID_STATUS** (0x10) Estado de animação inválida
- **GX_INVALID_MEMORY_SIZE** (0x29) O bloco de memória fornecido não é grande o suficiente para criar a tela
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_ANIMATION animation;
GX_CANVAS animation_canvas;
GX_ROOT_WINDOW animation_root;
/* Create animation canvas. */
status = gx_canvas_create(
        &animation_canvas, /* Canvas control block. */
        “animation_canvas”, /* Name of canvas. */
        display, /* Display control block. */
        GX_ANIMATION_MANAGED, /* Type of canvas. */
        width, /* Width of canvas. */
        height, /* Height of canvas. */
        memory_area, /* Memory area of canvas. */
        memory_size /* Size of canvas memory. */
        );
if (status == GX_SUCCESS)
{
    /* Create the root window for the canvas. */
    status = gx_window_root_create(
        &animation_root, /* Root window control block. */
        “animation_root”, /* Name of root window. */
        &animation_canvas, /* Canvas of the root window. */ GX_STYLE_NONE, /* Style of the window. */
        GX_ID_NONE, /* Root window ID. */
        &root_size /* Window size. */
        );
}
if (status == GX_SUCCESS)
{
    /* Define canvas for the animation. */
    status = gx_animation_canvas_define(&animation,
                &animation_canvas);
}
/* If status is GX_SUCCESS the new canvas was successfully set to the animation manager. */

```

### <a name="see-also"></a>Consulte também

- gx_animation_create,
- gx_animation_delete
- gx_animation_drag_disable,
- gx_animation_drag_enable
- gx_animation_landing_speed_set,
- gx_animation_start
- gx_animation_stop

## <a name="gx_animation_create"></a>gx_animation_create

Criar um controlador de animação

### <a name="prototype"></a>Prototype

```C
UINT gx_animation_create(GX_ANIMATION *animation);
```

### <a name="description"></a>Descrição

Este serviço cria um controlador de animação. O controlador é inicializado para o estado ocioso. Não se pode começar uma animação a menos que esteja no estado de IDLE. O ponteiro do bloco de controlo GX_ANIMATION pode ser obtido com gx_system_animation_get ou pode ser um bloco de controlo estático.

### <a name="parameters"></a>Parâmetros

- **animação** Ponteiro para bloco de controlo de animação


### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) criou com sucesso o controlador de animação
- **GX_ALREADY_CREATED** (0x13) Bloco de controlo já inicializado
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_ANIMATION *animation;

/* Allocate an animaton control from system pool */
gx_system_animation_get(&animation);

/* Initialize the control block */

if (animation)
{
    status = gx_animation_create(&animation);
}

/* If status is GX_SUCCESS the new animation controller was successfully created and initialized. */

```

### <a name="see-also"></a>Consulte também

- gx_animation_canvas_define,
- gx_animation_delete
- gx_animation_drag_disable,
- gx_animation_drag_enable
- gx_animation_start
- gx_animation_landing_speed_set,
- gx_animation_stop
- gx_system_animation_get
- gx_system_animation_free

## <a name="gx_animation_drag_disable"></a>gx_animation_drag_disable

Desativar o gancho de animação de arrasto de tela

### <a name="prototype"></a>Prototype

```C
UINT gx_animation_drag_disable(
    GX_ANIMATION *animation, 
    GX_WIDGET *widget);
```

### <a name="description"></a>Descrição

Este serviço remove o procedimento do gancho de animação de arrasto do ecrã da função de processo de evento padrão do widget e para a sequência de animação. O procedimento do gancho de animação de arrasto de tela lida com eventos para uma animação de arrasto de tela.

### <a name="parameters"></a>Parâmetros

- **animação** Ponteiro para bloco de controlo de animação
- **widget** Ponteiro para o bloco de controlo do widget

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Bem sucedido
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_CALLER_ERROR** (0x11) Inválido desta função

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_ANIMATION animation;
GX_WIDGET *animation_parent;

/* Disable screen drag animation of “animation_parent”. */
status = gx_animation_drag_disable(&animation, animation_parent);

/* If status is GX_SUCCESS the screen drag hook has been removed
    from the event process of “animation_parent”. */

```

### <a name="see-also"></a>Consulte também

- gx_animation_canvas_define,
- gx__animation_create
- gx_animation_drag_enable
- gx_animation_landing_speed_set,
- gx__animation_start
- gx_animation_stop
- gx_system_animation_get,
- gx__system_animation_free

## <a name="gx_animation_drag_enable"></a>gx_animation_drag_enable

Ativar o gancho de animação de arrasto de tela

### <a name="prototype"></a>Prototype

```C
UINT gx_animation_drag_enable(
    GX_ANIMATION *animation,
    GX_WIDGET *widget, 
    GX_ANIMATION_INFO *info);
```

### <a name="description"></a>Descrição

Este serviço define a função de processo de evento de animação de arrasto de arrasto definida internamente como um procedimento de gancho da função de processo de evento padrão de um widget. A função de processo de evento de animação de arrasto de tela lida com eventos para uma animação de arrasto de ecrã.

O procedimento do gancho de arrasto do ecrã torna-se o manipulador predefinido para eventos de entrada de caneta enviados para o widget alvo. A função original de processamento de eventos widget é chamada de forma de cadeia de margarida depois de verificar se existem tipos de eventos de entrada de arrasto de ecrã.

### <a name="parameters"></a>Parâmetros

- **animação** Ponteiro para bloco de controlo de animação
- **widget** Ponteiro para o bloco de controlo do widget
- **informação** Informação de animação

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Bem sucedido
- **GX_INVALID_STATUS** (0x26) Estado de animação inválida
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_VALUE** (0x22) Valor inválido
- **GX_INVALID_WIDGET** (0x12) Lista de tela de diapositivos não é fornecida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_ANIMATION animation;
GX_ANIMATION_INFO info;
GX_WIDGET *animation_parent;
GX_WIDGET *screen_list[] = {
    screen_1,
    screen_2,
    screen_3,
    GX_NULL
}

memset(&info, 0, sizeof(GX_ANIMATION_INFO);
info.gx_animation_parent = animation_parent;

/* If GX_STYLE_ANIMATION_WRAP is set, the screen list will wrap itself. */
info.gx_animation_style = GX_ANIMATION_SCREEN_DRAG |
                          GX_ANIMATION_HORIZONTAL |
                          GX_STYLE_ANIMATION_WRAP;
info.gx_animation_frame_interval = 1;
info.gx_animation_slide_screen_list = screen_list;

status = gx_animation_drag_enable(&animation, animation_parent,
                                  info);

/* If status is GX_SUCCESS the screen slide animinatin event
    process function has been set as a hook procedure of
    “animation_parent”. */
```

### <a name="see-also"></a>Consulte também

- gx_animation_canvas_define,
- gx__animation_create
- gx_animation_drag_disable,
- gx__animation_landing_speed_set
- gx_animation_start,
- gx__animation_stop,
- gx__system_animation_get
- gx_system_animation_free

## <a name="gx_animation_landing_speed_set"></a>gx_animation_landing_speed_set

Definir velocidade de aterragem para a animação de drag de tela

### <a name="prototype"></a>Prototype

```C
UINT gx_animation_landing_speed_set(
    GX_ANIMATION *animation, 
    USHORT shift_per_step);
```

### <a name="description"></a>Descrição

Este serviço define a velocidade de aterragem para a animação de arrasto de ecrã.

### <a name="parameters"></a>Parâmetros

- **animação** Ponteiro para bloco de controlo de animação
- **shift_per_step** Distância de mudança para cada passo

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Bem sucedido
- **GX_INVALID_VALUE** (0x22) Parâmetro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set landing speed of “my_animation” to 20. */
status = gx_animation_landing_peed_set(&my_animation, 20);

/* If status is GX_SUCCESS the landing speed is successfully set to 20. */
```

### <a name="see-also"></a>Consulte também

- gx_animation_canvas_define,
- gx__animation_create
- gx_animation_slide_disable,
- gx__animation_slide_enable
- gx_animation_start,
- gx__animation_stop,
- gx__system_animation_get
- gx_system_animation_free

## <a name="gx_animation_start"></a>gx_animation_start

Inicie uma animação orientada pelo temporizador

### <a name="prototype"></a>Prototype

```C
UINT gx_animation_start(
    GX_ANIMATION *animation, 
    GX_ANIMATION_INFO *params);
```

### <a name="description"></a>Descrição

Este serviço inicia uma sequência de animação usando uma instância de animação previamente criada e um novo conjunto de parâmetros de animação. Esta função faz uma cópia local dos parâmetros, o que significa que a estrutura do parâmetro não precisa de ser definida estáticamente.

A estrutura de controlo GX_ANIMATION pode ser definida estáticamente pela aplicação, ou pode ser obtida através da API gx_system_animation_get().

A estrutura GX_ANIMATION_INFO define os parâmetros da animação a executar. Para uma descrição completa desta estrutura e o significado de cada campo, consulte a secção de Componente de Animação GUIX no Capítulo 3 deste manual.

### <a name="parameters"></a>Parâmetros

- **animação** Ponteiro para bloco de controlo de animação
- **params** Ponteiro para a estrutura do parâmetro

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Bem sucedido
- **GX_INVALID_VALUE** (0x22) Parâmetro inválido
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_WIDGET** (0x12) Alvo de animação inválida
- **GX_INVALID_STATUS** (0x26) Estado de animação inválida
- **GX_INVALID_CANVAS** (0x20) Tela de animação inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_ANIMATION_INFO params;
GX_ANIMATION *animation;

/* obtain an animation control block pointer */
gx_system_animation_get(&animation);
if (animation)
{
    /* define a slide down and to the right */
    params.gx_animation_start_position.gx_point_x = 0;
    params.gx_animation_start_position.gx_point_y = 0;
    params.gx_animation_end_position.gx_point_x = 100;
    params.gx_animation_end_position.gx_point_y = 200;
    params.gx_animation_style= GX_ANIMATION_TRANSLATE;
    params.gx_animation_target = &my_window;
    params.gx_animation_parent = root_window;
    params.gx_animation_start_alpha = 255;
    params.gx_animation_end_alpha = 255;

    params.gx_animation_delay_before = 0;
    params.gx_animation_steps = 10;
    params.gx_animation_tick_rate = 2;

    status = gx_animation_start(&animation, &params);
}

/* If status is GX_SUCCESS the animation is initiated. */
```

### <a name="see-also"></a>Consulte também

- gx_animation_canvas_define,
- gx__animation_create
- gx_animation_slide_disable,
- gx__animation_slide_enable
- gx_animation_landing_speed_set,
- gx__animation_stop
- gx_system_animation_get,
- gx__system_animation_free

## <a name="gx_animation_stop"></a>gx_animation_stop

Pare uma animação ativa orientada pelo temporizador

### <a name="prototype"></a>Prototype

```C
UINT gx_animation_stop(GX_ANIMATION *animation);
```

### <a name="description"></a>Descrição

Pare uma animação iniciada anteriormente. Se o ponteiro do bloco de controlo de animação foi atribuído utilizando gx_system_animation_get, a aplicação pode reutilizar o bloco de controlo ou devolvê-lo ao pool do sistema utilizando gx_system_animation_free).

### <a name="parameters"></a>Parâmetros

- **animação** Ponteiro para bloco de controlo de animação

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Ponteiro inválido de GX_PTR_ERROR (0x07)
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_INVALID_STATUS** (0x26) Estado do controlador inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_ANIMATION animation;

status = gx_animation_stop(&animation);

/* If status is GX_SUCCESS the animation is stopped */

```

### <a name="see-also"></a>Consulte também

- gx_animation_canvas_define,
- gx__animation_create
- gx_animation_drag_disable,
- gx__animation_drag_enable
- gx_animation_start,
- gx__system_animation_get
- gx_system_animation_free

## <a name="gx_binres_language_count_get"></a>gx_binres_language_count_get

Devolva o número de idiomas presentes em dados binários de recursos

### <a name="prototype"></a>Prototype

```C
UINT gx_binres_language_count_get(
    GX_UBYTE *root_address, 
    GX_VALUE *returned_count);
```

### <a name="description"></a>Descrição

Este serviço analisa um cabeçalho de dados de recursos binários para devolver o número de idiomas contidos nos dados binários. Isto é útil para aplicações que devem apresentar uma lista de seleção ao utilizador, permitindo ao utilizador selecionar a partir de uma escolha de idiomas.

### <a name="parameters"></a>Parâmetros

- **root_address** Endereço de dados binários de recursos na memória
- **return_count** Localização para armazenar contagem de idiomas devolvidas

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Bem sucedido
- **GX_INVALID_FORMAT** (0x24) Recurso binário inválido
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_VALUE language_count = 0;

/* Specify address that binary resource data is located. */
GX_UBYTE    *root_address = 0x60000000;

status = gx_binres_language_count_get(root_address,
    &language_count);

/* If status is GX_SUCCESS, the language table was successfully loaded. */

```

### <a name="see-also"></a>Consulte também

- gx_binres_language_info_load

## <a name="gx_binres_language_info_load"></a>gx_binres_language_info_load

Informação de tabela de linguagem de carga

### <a name="prototype"></a>Prototype

```C
UINT gx_binres_language_info_load(
    GX_UBYTE *root_address, 
    GX_LANGUAGE_HEDAER *put_info);
```

### <a name="description"></a>Descrição

Este serviço analisa uma bolha binária de dados de recursos para povoar uma série de estruturas GX_LANGUAGE_HEADER, informando a aplicação dos nomes linguísticos e tamanho da tabela de cordas de cada idioma contida nos dados binários. A aplicação deve primeiro ligar gx_binres_language_count_get para determinar o número de línguas dentro dos dados binários, e garantir que o ponteiro put_info passou para esta função aponta para um conjunto de estruturas language_count GX_LANGUAGE_HEADER.

Este serviço é utilizado por aplicação para determinar em tempo de execução o conteúdo de um pedaço de dados de recursos binários.

A estrutura GX_LANGUAGE_HEADER é definida como:

```c
typedef struct GX_LANGUAGE_HEADER_STRUCT{
    USHORT gx_language_header_magic_number;
    USHORT gx_language_header_index;
    UCHAR gx_language_header_name[GX_LANGUAGE_HEADER_NAME_SIZE];
    ULONG  gx_language_header_data_size;
} GX_LANGUAGE_HEADER;
```

- O *campo magic_number* é utilizado para validação interna do formato de dados binários de recursos.
- O *campo header_index* indica a ordem pela qual as línguas são definidas nos dados binários.
- O *campo header_name* contém o nome da língua.
- O campo *header_data_size* contém o tamanho dos dados da tabela de cordas linguística.

### <a name="parameters"></a>Parâmetros

- **root_address** Endereço de dados binários de recursos na memória
- **put_info** Ponteiro para conjunto de estruturas GX_LANGUAGE_HEADER

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Bem sucedido
- **GX_INVALID_FORMAT** (0x24) Recurso binário inválido
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_LANGUAGE_HEADER language_info[4];

/* Specify address that binary resource data is located. */
GX_UBYTE    *root_address = 0x60000000;

status = gx_binres_language_info_load(root_address,
    language_info);
/* If status is GX_SUCCESS, the language table was successfully loaded. */

```

### <a name="see-also"></a>Consulte também

- gx_binres_language_count_get

## <a name="gx_binres_language_table_load"></a>gx_binres_language_table_load

Recurso de tabela de linguagem de carga (precotado)

### <a name="prototype"></a>Prototype

```C
UINT gx_binres_language_table_load(
    GX_UBYTE *root_address, 
    GX_UBYTE **returned_language_table);
```

### <a name="description"></a>Descrição

Esta API precotado permite que as aplicações carreguem dados de tabelas de cordas a partir de ficheiros de dados binários de recursos binários mais antigos (antes de lançar 5.6).

As novas aplicações devem ser utilizadas gx_binres_language_table_load_ext).

Este serviço constrói uma estrutura de mesa linguística contendo ponteiros para apresentar recursos, as estruturas de dados geradas apontam para os dados de recursos "em vigor", não copia os dados dos recursos. Os dados dos recursos devem ser colocados num local geral de memória de acesso, e o endereço base deste local de memória é passado para esta API.

Este serviço requer um bloco de memória repartido suficientemente grande para manter a estrutura da mesa linguística, pelo que a gx_system_memory_allocator_set API deve ser invocada uma vez antes deste serviço ser solicitado.

A tabela linguística devolvida define uma ou mais tabelas de cordas, cada tabela de cordas contendo ponteiros para prender recursos na memória de dados de recursos.

### <a name="parameters"></a>Parâmetros

- **root_address** Endereço de dados binários de recursos na memória
- **devolveu _language_table** Ponteiro para tabela de linguagem carregada

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Bem sucedido
- **GX_INVALID_FORMAT** (0x24) Recurso binário inválido
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_SYSTEM_MEMPRY_ERROR** (0x30) O alocador de memória ou função gratuita não está definido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_UBYTE ***language_table = GX_NULL;

/* Specify address that binary resource data is located. */
GX_UBYTE *root_address = 0x60000000;

status = gx_binres_language_table_load(root_address,
                                        &language_table);

/* If status is GX_SUCCESS, the language table was successfully loaded. */

```

### <a name="see-also"></a>Consulte também

- gx_binres_language_table_load_ext

## <a name="gx_binres_language_table_load_ext"></a>gx_binres_language_table_load_ext

Recurso de tabela de linguagem de carga

### <a name="prototype"></a>Prototype

```C
UINT gx_binres_language_table_load_ext(
    GX_UBYTE *root_address, 
    GX_STRING **returned_language_table);
```

### <a name="description"></a>Descrição

Este serviço constrói uma estrutura de mesa linguística contendo ponteiros para apresentar recursos, as estruturas de dados geradas apontam para os dados de recursos "em vigor", não copia os dados dos recursos. Os dados dos recursos devem ser colocados num local geral de memória de acesso, e o endereço base deste local de memória é passado para esta API.

Este serviço requer um bloco de memória repartido suficientemente grande para manter a estrutura da mesa linguística, pelo que a gx_system_memory_allocator_set API deve ser invocada uma vez antes deste serviço ser solicitado.

A tabela linguística devolvida define uma ou mais tabelas de cordas, cada tabela de cordas contendo ponteiros para prender recursos na memória de dados de recursos.

### <a name="parameters"></a>Parâmetros

- **root_address** Endereço de dados binários de recursos na memória
- **devolveu _language_table** Ponteiro para tabela de linguagem carregada

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Bem sucedido
- **GX_INVALID_FORMAT** (0x24) Recurso binário inválido
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_SYSTEM_MEMPRY_ERROR** (0x30) O alocador de memória ou função gratuita não está definido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_STRING **language_table = GX_NULL;

/* Specify address that binary resource data is located. */
GX_UBYTE *root_address = 0x60000000;

status = gx_binres_language_table_load_ext(root_address,
                                            &language_table);

/* If status is GX_SUCCESS, the language table was successfully loaded. */

```

### <a name="see-also"></a>Consulte também

- gx_binres_theme_load

## <a name="gx_binres_theme_load"></a>gx_binres_theme_load

Recurso temático de carga

### <a name="prototype"></a>Prototype

```C
UINT gx_binres_theme_load(
    GX_UBYTE *root_address, 
    INT theme_id, GX_THEME **returned_theme);
```

### <a name="description"></a>Descrição

Este serviço constrói uma estrutura GX_THEME contendo ponteiros para as tabelas de recursos para o tema solicitado. As estruturas de dados geradas apontam para os dados de recursos "no lugar", não copiam os dados dos recursos. Assim, os dados de recursos devem ser colocados num local geral de memória de acesso, e o endereço base deste local de memória é passado para esta API.

Este serviço requer um bloco de memória alocado suficientemente para manter a estrutura temática da mesa, pelo que a gx_system_memory_allocator_set API deve ser invocada uma vez antes deste serviço ser solicitado.

### <a name="parameters"></a>Parâmetros

- **root_address** Endereço de dados binários de recursos na memória
- **theme_id** O identificador do tema
- **returned_theme** Ponteiro para o tema carregado

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Bem sucedido
- **GX_INVALID_FORMAT** (0x24) Recurso binário inválido
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **ID** tema GX_INVALID_VALUE (0x22) Inválido
- **GX_SYSTEM_MEMORY_ERROR** (0x30) O alocador de memória ou função gratuita não está definido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_CHAR *theme = GX_NULL;
GX_UBYTE *root_address = 0x60000000;
INT theme_id = 0;

status = gx_binres_theme_load(root_address, theme_id, &theme);

/* If status is GX_SUCCESS, the theme was successfully loaded. */
```

### <a name="see-also"></a>Consulte também

- gx_binres_language_table_read

## <a name="gx_brush_default"></a>gx_brush_default
Desavele a escova predefinida

### <a name="prototype"></a>Prototype

```C
UINT gx_brush_default(GX_BRUSH *brush);
```

### <a name="description"></a>Descrição

Este serviço define a escova para o contexto atual ao valor predefinido do sistema.

### <a name="parameters"></a>Parâmetros
- **pincel** Ponteiro para o bloco de controlo da escova.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Definição de pincel bem sucedida
- **GX_PTR_ERROR** (0x07) Ponteiro de escova inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/*Reset the brush to its default value. */
status = gx_brush_default(&my_brush);

/* If status is GX_SUCCESS the brush was successfully reset to its default value. */

```

### <a name="see-also"></a>Consulte também

- gx_brush_define


## <a name="gx_brush_define"></a>gx_brush_define
Definir pincel

### <a name="prototype"></a>Prototype

```C
UINT gx_brush_define(
    GX_BRUSH *brush, 
    GX_COLOR line_color, 
    GX_COLOR fill_color, 
    UINT style);
```

### <a name="description"></a>Descrição

Este serviço define um pincel com a cor de linha especificada, preencha a cor e o estilo.

### <a name="parameters"></a>Parâmetros

- **pincel** Ponteiro para bloco de controlo de escova
- **line_color** Cor da linha de pincel. **O apêndice A** contém cores pré-definidas. Note que a aplicação também pode adicionar cores personalizadas.
- **fill_color** Cor do enchimento de escova. **O apêndice A** contém cores pré-definidas. Note que a aplicação também pode adicionar cores personalizadas.
- **estilo** Estilo pincel. **O apêndice D** descreve os estilos de escova suportados. Os estilos de escova podem ser combinados numa variável utilizando uma operação bitwise OR.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Definição de pincel bem sucedida
- **GX_PTR_ERROR** (0x07) Ponteiro de escova inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Define a brush. */
status = gx_brush_define(&my_brush, GX_COLOR_BLACK, GX_COLOR_BLACK,
                         GX_STYLE_BORDER_NONE);

/* If status is GX_SUCCESS the brush was successfully created. */
```

### <a name="see-also"></a>Consulte também

- gx_brush_default

## <a name="gx_button_background_draw"></a>gx_button_background_draw

 Desenhe o fundo do botão

###<a name="prototype"></a>Prototype

```C
VOID gx_button_background_draw(GX_BUTTON *button);
```

### <a name="description"></a>Descrição

Este serviço desenha o fundo do botão. Esta função é normalmente chamada internamente pela função gx_button_draw, mas está exposta à aplicação para ajudar a escrever funções de desenho personalizado.

### <a name="parameters"></a>Parâmetros

- **botão** Ponteiro para bloco de controlo de botões

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
VOID custom_button_draw(GX_BUTTON *button)
{
    /* Draw button background. */
    gx_button_background_draw(button);

    /* Add custom drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)button);
}
```

### <a name="see-also"></a>Consulte também

- gx_button_create,
- gx__button_deselect,
- gx__button_draw
- gx_button_event_process,
- gx__button_select
- gx_icon_button_create,
- gx__pixelmap_button_create
- gx_pixelmap_button_draw,
- gx__radio_button_create
- gx_radio_button_draw,
- gx__text_button_create
- gx_text_button_color_set,
- gx__text_button_draw

## <a name="gx_button_create"></a>gx_button_create

Botão Criar

### <a name="prototype"></a>Prototype

```C
UINT gx_button_create(
    GX_BUTTON *button, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    ULONG style, 
    USHORT button_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria um botão conforme especificado e associa o botão ao widget dos pais fornecido.

### <a name="parameters"></a>Parâmetros

- **botão** Ponteiro para bloco de controlo de botões
- **nome** Nome lógico do botão
- **pai** Ponteiro para o widget dos pais do botão
- **estilo** Estilo botão. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **button_id** ID definido pela aplicação do botão
- **tamanho** Tamanho do botão

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Criação de botões bem sucedidos
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_BUTTON my_top_button;

/* Create a stop button. */
status = gx_button_create(&my_stop_button, "my stop button",
                            &my_parent_window,
                            GX_STYLE_BUTTON_TOGGLE,
                            MY_STOP_BUTTON_ID, &size);

/* If status is GX_SUCCESS the stop button was successfully created. */
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw,
- gx_button_deselect,
- gx_button_draw
- gx_button_event_process,
- gx_button_select
- gx_radio_button_create,
- gx_radio_button_draw
- gx_icon_button_create,
- gx_pixelmap_button_create
- gx_pixelmap_button_draw,
- gx_text_button_create
- gx_text_button_color_set,
- gx_text_button_draw

## <a name="gx_button_deselect"></a>gx_button_deselect


Botão de desmarcação

### <a name="prototype"></a>Prototype

```C
UINT gx_button_deselect(
    GX_BUTTON *button, 
    GX_BOOL gen_event);
```

### <a name="description"></a>Descrição

Este serviço desmarca o botão especificado e gera um evento de sinal dependendo dos estilos dos botões.


| Estilo de botão              | Sinal                     |
|---------------------------|----------------------------|
| Nenhum                      | GX_EVENT_CLICKED         |
| GX_STYLE_BUTTON_RADIO  | GX_EVENT_RADIO_DESELECT |
| GX_STYLE_BUTTON_TOGGLE | GX_EVENT_TOGGLE_OFF     |



### <a name="parameters"></a>Parâmetros

- **botão** Ponteiro para bloco de controlo de botões
- **gen_event** Se GX_TRUE, o botão gerará um evento GX_EVENT_CLICKED, GX_EVENT_DESELECT ou GX_EVENT_TOGGLE_OFFSET dependendo do estilo do botão. Se GX_FALSE, o botão não gerará qualquer evento de nível superior, mesmo que normalmente o faça.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Deseselecção de botão de sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Deselect button. */
status = gx_button_deselect(&my_stop_button, GX_TRUE);

/* If status is GX_SUCCESS the stop button was successfully deselected. */
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw,
- gx_button_create,
- gx_button_draw
- gx_button_event_process,
- gx_button_select
- gx_radio_button_create,
- gx_radio_button_draw
- gx_icon_button_create,
- gx_pixelmap_button_create
- gx_pixelmap_button_draw,
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_button_draw"></a>gx_button_draw

Desenhe botão

### <a name="prototype"></a>Prototype

```C
VOID gx_button_draw(GX_BUTTON *button);
```

### <a name="description"></a>Descrição

Este serviço desenha o botão especificado. Esta função é normalmente chamada internamente pelo mecanismo de atualização de lona GUIX, mas está exposta à aplicação para ajudar na implementação de funções de desenho personalizado para widgets de botões personalizados.

### <a name="parameters"></a>Parâmetros

- **botão** Ponteiro para bloco de controlo de botões

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom button draw function. */
VOID custom_button_draw(GX_BUTTON *button)
{
    /* Call default button draw. */
    gx_button_draw(button);

    /* Add custom drawing here. */
}

```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw,
- gx_button_create
- gx_button_deselect,
- gx_button_event_process,
- gx_button_select
- gx_radio_button_create,
- gx_radio_button_draw
- gx_icon_button_create,
- gx_pixelmap_button_create
- gx_pixelmap_button_draw,
- gx_text_button_create
- gx_text_button_color_set,
- gx_text_button_draw

## <a name="gx_button_event_process"></a>gx_button_event_process


Evento de botão de processo

### <a name="prototype"></a>Prototype

```C
UINT gx_button_event_process(
    GX_BUTTON *button, 
    GX_EVENT *event);
```

### <a name="description"></a>Descrição

Este serviço processa um evento para o botão especificado.

### <a name="parameters"></a>Parâmetros

- **botão** Ponteiro para bloco de controlo de botões
- **event_ptr** Ponteiro para o evento para processar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Processo de evento de botão de sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Call generic button event processing as part of custom event processing function. */

UINT custom_button_event_process(GX_BUTTON *button,
                                 GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default button
            event processing */
        status = gx_button_event_process(button, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw,
- gx_button_create
- gx_button_deselect,
- gx_button_draw,
- gx_button_select
- gx_radio_button_create,
- gx_radio_button_draw
- gx_icon_button_create,
- gx_pixelmap_button_create
- gx_pixelmap_button_draw,
- gx_text_button_create
- gx_text_button_color_set,
- gx_text_button_draw

## <a name="gx_button_select"></a>gx_button_select

Selecione botão

### <a name="prototype"></a>Prototype

```C
UINT gx_button_select(GX_BUTTON *button);
```

### <a name="description"></a>Descrição

Este serviço seleciona o botão especificado e gera um evento de sinal dependendo dos estilos dos botões.

Deselelects os irmãos para um grupo de botões de rádio.

| Estilo de botão                       | Sinal                   |
|------------------------------------|--------------------------|
| GX_STYLE_BUTTON_RADIO           | GX_EVENT_RADIO_SELECT |
| GX_STYLE_BUTTON_EVENT_ON_PUSH | GX_EVENT_CLICKED       |
| GX_STYLE_BUTTON_TOGGLE          | GX_EVENT_TOGGLE_ON    |


### <a name="parameters"></a>Parâmetros

- **botão** Ponteiro para bloco de controlo de botões

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Seleciona botão de sucesso
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Select button. */
status = gx_button_select(&my_stop_button);

/* If status is GX_SUCCESS the stop button was successfully selected. */
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw,
- gx_button_create
- gx_button_deselect,
- gx_button_draw,
- gx_button_event_process
- gx_radio_button_create,
- gx_radio_button_draw
- gx_icon_button_create,
- gx_pixelmap_button_create
- gx_pixelmap_button_draw,
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_canvas_alpha_set"></a>gx_canvas_alpha_set

Definir valor alfa-blend para tela

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_alpha_set(
    GX_CANVAS *canvas, 
    GX_UBYTE alpha);
```

### <a name="description"></a>Descrição

Este serviço define o valor de mistura alfa para a tela especificada. Os valores alfa de lona podem variar de 0 (transparente) a 255 (totalmente opaco).

A mistura de telas sobrepostas requer suporte de camada de gráficos de hardware ou suporte ao software através da criação de uma tela composta.

O suporte de hardware para a mistura de tela é ativado invocando a API gx_canvas_hardware_layer_bind() API antes de definir o valor alfa de tela. Quando uma tela está ligada a uma camada de gráficos de hardware, chamando a gx_canvas_alpha_set() API invoca diretamente os serviços de mistura de camadas de gráficos de hardware.

Para utilizar o suporte ao software para a mistura de tela, a aplicação deve criar uma tela com GX_CANVAS_COMPOSITE estilo, no qual todas as outras telas geridas são compostas antes do visor final. O suporte ao software para a mistura de lona só é fornecido quando funciona com um controlador de ecrã de 16 bpp ou profundidade de cor superior.

### <a name="parameters"></a>Parâmetros

- **tela** Ponteiro para bloco de controlo de lona
- **alfa** Valor alfa-blend, variam de 0 (transparente) a 255 (opaco).

### <a name="return--values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de valor de mistura alfa-blend bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_ERROR** (0x20) Tela inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the alpha-blend value of “my_canvas”. */
status = gx_canvas_alpha_set(&my_canvas, GX_ALPHA_VALUE_OPAQUE);

/* If status is GX_SUCCESS the alpha-blend value was successfully set. */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_create,
- gx_canvas_drawing_complete
- gx_canvas_drawing_initiate,
- gx_canvas_offset_set
- gx_canvas_shift,
- gx_canvas_hardware_layer_bind,
- gx_canvas_show
- gx_canvas_hide

## <a name="gx_canvas_arc_draw"></a>gx_canvas_arc_draw

Desenhar arco

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_arc_draw(
    INT xcenter, 
    INT ycenter, 
    UINT r,
    INT start_angle, 
    INT end_angle);
```

### <a name="description"></a>Descrição

Este serviço desenha um arco de círculo na tela utilizando a escova atual. O arco do círculo é cortado à região inválida de lona. Este serviço requer GX_ARC_DRAWING_SUPPORT para ser definido.

### <a name="parameters"></a>Parâmetros

- **xcenter** x-posição do centro do arco círculo
- **ycenter** y-position do centro do arco círculo
- **r** Raio do arco do círculo
- **start_angle** Ângulo inicial do arco do círculo
- **end_angle** Ângulo final do arco do círculo

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Sorteio de arco bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_INVALID_VALUE** (0x22) Valor inválido
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho aberto

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Draw a circle arc from 0 degree to 90 degree in clockwise. */
status = gx_canvas_arc_draw(100, 100, 50, 0, 90);

/* If status is GX_SUCCESS the arc has been drawn on “my_canvas”. */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_block_move,
- gx_canvas_circle_draw
- gx_display_create,
- gx_canvas_ellipse_draw
- gx_canvas_line_draw,
- gx_canvas_pie_draw
- gx_canvas_pixelmap_draw,
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw,
- gx_canvas_text_draw

## <a name="gx_canvas_block_move"></a>gx_canvas_block_move

Mova bloco de pixels de lona

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_block_move(GX_RECTANGLE *block,
    GX_VALUE x_shift, GX_VALUE y_shift, GX_RECTANGLE *dirty);
```

### <a name="description"></a>Descrição

Este serviço move um bloco de dados de pixel de tela na direção especificada. Este serviço é utilizado internamente pelo GUIX para realizar deslocamento rápido, mas também pode ser utilizado pelo software da aplicação.

### <a name="parameters"></a>Parâmetros

- **bloco** Coordenadas de área para mover
- **x_shift** Número de pixels para deslocar no eixo x
- **y_shift** Número de pixels para deslocar no eixo y
- **sujo** Se o movimento do bloco for bem sucedido, esta função devolve a parte do retângulo de origem que ainda está suja ao chamador neste parâmetro.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Movimento de bloco bem sucedido
- **GX_FAILURE** (0x10) Movimento de bloco falhado
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
GX_RECTANGLE invalid;
GX_RECTANGLE move;

/* define 100 x 100 pixel rectangle */
gx_utility_rectangle_define(&move, 0, 0, 99, 99);

/* Move this rectangle 10 pixels to the right”. */
status = gx_canvas_block_move(&move, 10, 0, &invalid);

/* If status is GX_SUCCESS, then ‘invalid’ marks the area that needs to be redrawn after the block move. */

```

### <a name="see-also"></a>Consulte também

- gx_canvas_arc_draw,
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile,
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw,
- gx_canvas_text_draw

## <a name="gx_canvas_circle_draw"></a>gx_canvas_circle_draw

Desenhar círculo

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_circle_draw(
    INT xcenter, 
    INT ycenter, 
    UINT r);
```

### <a name="description"></a>Descrição

Este serviço desenha um círculo sobre a tela utilizando a escova atual. O círculo é cortado à região inválida de lona. Este serviço requer GX_ARC_DRAWING_SUPPORT para ser definido.

### <a name="parameters"></a>Parâmetros

- **xcenter** x-coord do centro do círculo
- **ycenter** y-coord do centro da cirlce
- **r** Raio do círculo

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Sorteio de círculo bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_INVALID_VALUE** (0x22) Raio de círculo inválido
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho aberto

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C

/* Draw a circle of radius 10 centered at (100, 100). */
status = gx_canvas_circle_draw(100, 100, 50);

/* If status is GX_SUCCESS the circle has been drawn on “my_canvas”. */

```

### <a name="see-also"></a>Consulte também

- gx_canvas_arc_draw,
- gx_canvas_block_move,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_darw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile,
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw,
- gx_canvas_text_draw


## <a name="gx_canvas_create"></a>gx_canvas_create

Criar tela

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_create(
    GX_CANVAS *canvas, 
    GX_CONST GX_CHAR *name,
    GX_DISPLAY *display, 
    UINT type, 
    UINT width, 
    UINT height,
    GX_COLOR *memory_area, 
    ULONG memory_size);
```

### <a name="description"></a>Descrição

Este serviço cria a tela com as propriedades especificadas e memória associada.

### <a name="parameters"></a>Parâmetros

- **tela** Ponteiro para bloco de controlo de lona
- **nome** Nome lógico para a tela
- **exibir** Ponteiro para exibição previamente criada
- **tipo** Tipo de telaOs tipos de lona incluem:
- **GX_CANVAS_SIMPLE:** Uma tela de memória que é usada para desenhar fora do ecrã.
- **GX_CANVAS_MANAGED:** Uma tela que automaticamente se despejou para o visor ativo, quer como parte do processo de construção composta, quer como parte do funcionamento do tampão para arquiteturas de tela única.
- **GX_CANVAS_VISIBLE:** Esta bandeira pode ser usada para ligar e sair de uma tela, sem perder o conteúdo de desenho de tela.
- **GX_CANVAS_MODIFIED:** Reservado para uso futuro.
- **GX_CANVAS_COMPOSITE:** Esta bandeira é utilizada pela aplicação ao configurar um sistema de múltiplas telas que compôs várias telas geridas na tela composta, e o composto é o acionado para o tampão de quadro de hardware.
- **largura** Largura em pixels
- **altura** Altura em pixels
- **memory_area** Área de memória para tela. Este valor pode
- **GX_NULL** no momento da criação de tela
- **e** posteriormente inicializada usando gx_canvas_memory_define
- **memory_size** Tamanho da área da memória em bytes, ou 0 se a memória de tela será definida após a criação da tela.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Cria lona bem sucedida
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_CANVAS_SIZE** (0x1C) Tamanho do bloco de controlo de lona inválido
- **GX_INVALID_TYPE** (0x1B) Tipo de lona inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Define global canvas memory area. */
GX_COLOR my_canvas_memory[272*480];

…

/* Create “my_canvas”. */
status = gx_canvas_create(&my_canvas, "my canvas", &my_display,
                    (GX_CANVAS_MANAGED | GX_CANVAS_VISIBLE),
                    272, 480,
                    my_canvas_memory,
                    sizeof(default_canvas_memory));

/* If status is GX_SUCCESS the 272 x 480 canvas was successfully created. */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_delete,
- gx_canvas_hardware_layer_bind
- gx_canvas_memory_define

## <a name="gx_canvas_delete"></a>gx_canvas_delete

Apagar tela

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_delete(GX_CANVAS *canvas);
```

### <a name="description"></a>Descrição

Este serviço elimina a tela. A tela é removida da lista interna ligada de lona mantida pelo GUIX.

### <a name="parameters"></a>Parâmetros

- **tela** Ponteiro para bloco de controlo de lona

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Cria lona bem sucedida
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_CANVAS** (0x20) Tela inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Delete “my_canvas”. */
status = gx_canvas_delete (&my_canvas);

/* If status is GX_SUCCESS my_canvas was deleted. */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_alpha_set,
- gx_canvas_drawing_complete
- gx_canvas_create,
- gx_canvas_drawing_initiate
- gx_canvas_offset_set,
- gx_canvas_shift

## <a name="gx_canvas_drawing_complete"></a>gx_canvas_drawing_complete

Desenho completo de tela

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_drawing_complete(
    GX_CANVAS *canvas, 
    GX_BOOL flush);
```

### <a name="description"></a>Descrição

Este serviço permite ao GUIX saber que o desenho da aplicação na tela especificada está completo.

A aplicação pode usar este serviço para forçar o desenho imediato a uma tela. Isto coloca a tela no tampão visível do quadro e/ou desencadeia um funcionamento do interruptor, dependendo da arquitetura da memória do sistema.

Este serviço só deve ser chamado pela aplicação para encerrar uma sequência de desenho iniciada com gx_canvas_drawing_initiate().

### <a name="parameters"></a>Parâmetros

- **tela** Ponteiro para bloco de controlo de lona
- **flush** Se **_GX_TRUE,_** as alterações de lona são lavadas no visor

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conclusão de desenho bem sucedida
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Complete drawing on “my_canvas” and flush to display. */
status = gx_canvas_drawing_complete(&my_canvas, GX_TRUE);

/* If status is GX_SUCCESS the canvas drawing was successfully completed. */
```


### <a name="see-also"></a>Consulte também

- gx_canvas_alpha_set,
- gx_canvas_create
- gx_canvas_drawing_initiate,
- gx_canvas_offset_set
- gx_canvas_shift

## <a name="gx_canvas_drawing_initiate"></a>gx_canvas_drawing_initiate

Iniciar desenho de tela

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_drawing_initiate(
    GX_CANVAS *canvas,
    GX_WIDGET *who, 
    GX_RECTANGLE *dirty_area);
```

### <a name="description"></a>Descrição

Este serviço inicia a sua base na tela especificada. Este serviço é chamado internamente como parte da operação de desenho diferido realizada automaticamente pelo GUIX quando uma tela precisa de ser atualizada. No entanto, a aplicação é permitida para contornar o algoritmo de desenho diferido GUIX e executar o desenho imediato e direto sobre uma tela, chamando primeiro gx_canvas_drawing_inititate, depois chamando as funções de desenho desejadas, chamando depois gx_canvas_drawing_complete().

### <a name="parameters"></a>Parâmetros

- **tela** Ponteiro para bloco de controlo de lona
- **que** Ponteiro para o bloco de controlo widget do chamador. Este parâmetro é utilizado para inicializar os parâmetros de corte e visualização de desenho para as operações de desenho subsequentes.
- **dirty_area** Área para desenhar dentro. Este parâmetro é passado pelo chamador para indicar a área à qual o chamador quer todas as operações de desenho cortadas. Esta é geralmente a área previamente marcada como suja, mas o chamador é livre para expandir ou contrair a área de clipping.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Iniciação de desenho bem sucedida
- **GX_DRAW_NESTING_EXCEEDED** (0x05) Exceda a contagem máxima de nidificação
- **GX_NO_VIEW** (0x03) Sem visualizações para quem o chamador
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_CANVAS** (0x20) Tela inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Initiate drawing on “my_canvas”, my_widget.gx_widget_size
specify the area the application wants GUIX to redraw. */
status = gx_canvas_drawing_initiate(&my_canvas, &my_widget,
    &my_widget.gx_widget_size);

/* If status is GX_SUCCESS the canvas drawing was successfully initiated. */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_alpha_set,
- gx_canvas_create
- gx_canvas_drawing_complete,
- gx_canvas_offset_set
- gx_canvas_shift


## <a name="gx_canvas_ellipse_draw"></a>gx_canvas_ellipse_draw

Desenhar elipse

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_ellipse_draw(
    INT xcenter, 
    INT ycenter, 
    INT a, 
    dINT b);
```

### <a name="description"></a>Descrição

Este serviço desenha uma elipse na tela utilizando a escova atual. A elipse é cortada à região inválida de lona. Este serviço requer GX_ARC_DRAWING_SUPPORT para ser definido.

### <a name="parameters"></a>Parâmetros

- **xcenter** x-coord do centro da elipse
- **ycenter** y-coord do centro da elipse
- **um** comprimento do eixo semi-major
- **b** Comprimento do eixo semi-menor

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Sorteio de círculo bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_INVALID_VALUE** (0x22) Valor inválido
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho aberto

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Draw an ellipse of semi-major radius 100, semi-minor radius 50
    and centered at (200, 200). */
status = gx_canvas_ellipse_draw(200, 200, 100, 50);

/* If status is GX_SUCCESS the ellipse has been drawn on
    “my_canvas”. */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create,
- gx_canvas_line_darw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile,
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw,
- gx_canvas_text_draw

## <a name="gx_canvas_hardware_layer_bind"></a>gx_canvas_hardware_layer_bind

Ligue a tela à camada de gráficos de hardware

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_hardware_layer_bind(
    GX_CANVAS *canvas, 
    INT layer);
```

### <a name="description"></a>Descrição

Este serviço liga uma tela de desenho GUIX a uma camada gráfica de hardware. Este serviço só é necessário para dispositivos de hardware que suportem várias camadas de gráficos de hardware.

A ligação de uma tela a uma camada de gráficos de hardware resulta na gx_canvas_show(), gx_canvas_hide(), gx_canvas_alpha_set() e gx_canvas_offset_set() APIs sendo implementadas diretamente pelos serviços do controlador de ecrã de hardware.

Se o controlador de visualização de hardware não suportar várias camadas gráficas, este serviço falhará em voltar GX_INVALID_DISPLAY.

### <a name="parameters"></a>Parâmetros

- **tela** de tela para ser implementado em hardware
- **camada** de gráficos de hardware de camada

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Vinculação bem sucedida
- **GX_INVALID_DISPLAY** (0x1D) O serviço de camada de exibição não está definido
- **GX_PTR_ERROR** (0x17) Ponteiros inválidos
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_INVALID_CANVAS** (0x20) Tela inválida
- **GX_NOT_SUPPORTED** (0x28) Não apoiado

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Binds the canvas to the hardware graphics layer 1. */
status = gx_canvas_hardware_layer_bind(&my_canvas, 1);

/* If status is GX_SUCCESS, the drawing canvas is bound to the
    hardware graphics. */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_create,
- gx_canvas_memory_define

## <a name="gx_canvas_hide"></a>gx_canvas_hide

Esconda uma tela, tornando-a invisível

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_hide(GX_CANVAS *canvas);
```

### <a name="description"></a>Descrição

Este serviço esconde uma tela GUIX. Se a tela tiver sido ligada a uma camada de gráficos de hardware utilizando gx_canvas_hardware_layer_bind,, este serviço é implementado com suporte a hardware.

### <a name="parameters"></a>Parâmetros

- **tela** de tela a ser escondida

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Esconderijo bem sucedido
- **GX_INVALID_CANVAS** (0x20) Tela inválida
- **GX_PTR_ERROR** (0x17) Ponteiros inválidos
- **GX_CALLER_ERROR** (0x11) Inválido desta função

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Make my_canvas invisible. */
status = gx_canvas_hide(&my_canvas);

/* If status is GX_SUCCESS, the canvas has been hidden. */

```

### <a name="see-also"></a>Consulte também

- gx_canvas_create,
- gx_canvas_drawing_complete
- gx_canvas_drawing_initiate,
- gx_canvas_offset_set
- gx_canvas_shift,
- gx_canvas_hardware_layer_bind,
- gx_canvas_show
- gx_canvas_hide

## <a name="gx_canvas_line_draw"></a>gx_canvas_line_draw

Linha de desenho

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_line_draw(
    GX_VALUE x_start, 
    GX_VALUE y_start,
    GX_VALUE x_end, 
    GX_VALUE y_end);
```

### <a name="description"></a>Descrição

Este serviço traça uma linha sobre a tela utilizando a escova atual. A linha é cortada à região inválida de lona.

### <a name="parameters"></a>Parâmetros

- **x_start** Início da posição x da linha
- **y_end** Início da posição y da linha
- **x_start** Terminando a posição x da linha
- **y_end** Fim da posição y da linha

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Sorteio de linha bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho aberto
- **GX_INVALID_WIDTH** (0x1E) Largura da escova inválida

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Draw line on canvas. */
status = gx_canvas_line_draw(0, 1, 320, 480);

/* If status is GX_SUCCESS, the line has been drawn to canvas. */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_pie_draw
- gx_canvas_pixelmap_draw,
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw,
- gx_canvas_rectangle_draw
- gx_canvas_text_draw

## <a name="gx_canvas_memory_define"></a>gx_canvas_memory_define

Definir memória de tela

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_memory_define(
    GX_CANVAS *canvas, 
    GX_COLOR *memory,
    ULONG memsize);
```

### <a name="description"></a>Descrição

Este serviço pode ser utilizado para atribuir o endereço de memória de tela após a criação da tela.

### <a name="parameters"></a>Parâmetros

- **tela** Ponteiro para tela previamente criada
- **memória** Endereço de memória de tela
- **memsize** Tamanho do bloco de memória de tela em bytes

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Atribuição de sucesso
- **GX_INVALID_CANVAS** (0x20) Bloco de controlo inválido
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Assign canvas memory block. */
status = gx_canvas_memory_define(canvas,
    (GX_COLOR *) DRAM_MEMORY,
    (640 * 480 * 2));

/* If status is GX_SUCCESS, the canvas memory pointer has be
reassigned. */

```

### <a name="see-also"></a>Consulte também

- gx_canvas_create,
- gx_canvas_hardware_layer_bind

## <a name="gx_canvas_mouse_define"></a>gx_canvas_mouse_define

Defina a imagem do cursor do rato

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_mouse_define(GX_CANVAS *canvas,
    GX_MOUSE_CURSOR_INFO *info);
```

### <a name="description"></a>Descrição

Este serviço define as informações do rato para a tela especificada. Este serviço requer GX_MOUSE_SUPPORT para ser definido.

### <a name="parameters"></a>Parâmetros

- **tela** Ponteiro para bloco de controlo de lona
- **informação** Informação do cursor do rato. **O apêndice I** contém definição para GX_MOUSE_CURSOR_INFO estrutura.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de informações de rato bem sucedido
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_CALLER_ERROR** (0x11) Inválido desta função

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set mouse cursor info. */
GX_MOUSE_CURSOR_INFO mouse_cursor;
mouse_cursor.gx_mouse_cursor_image_id = GX_PIXELMAP_ID_MOUSE;
mouse_cursor.gx_mouse_cursor_hotspot_x = 0;
mouse_cursor.gx_mouse_cursor_hotspot_y = 0;

status = gx_canvas_mouse_define(&my_canvas, &mouse_cursor);

/* If status is GX_SUCCESS the mouse info of “my_canvas” has been
set successfully. */

```

### <a name="see-also"></a>Consulte também

- gx_canvas_mouse_show,
- gx_canvas_mouse_hide

## <a name="gx_canvas_mouse_hide"></a>gx_canvas_mouse_hide


Desligue o cursor do rato

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_mouse_hide(GX_CANVAS *canvas);
```

### <a name="description"></a>Descrição

Este serviço torna o cursor do rato escondido da tela especificada. Este serviço requer GX_MOUSE_SUPPORT para ser definido.

### <a name="parameters"></a>Parâmetros

- **tela** Ponteiro para bloco de controlo de lona

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Pele de cursor de rato bem sucedido
- **GX_FAILURE** (0X10) Pele de cursor de rato falhado
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_CALLER_ERROR** (0x11) Inválido desta função


### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Hide the mouse cursor. */
status = gx_canvas_mouse_hide(&my_canvas);

/* If status is GX_SUCCESS the mouse cursor of “my_canvas” has been
hidden successfully. */

```

### <a name="see-also"></a>Consulte também

- gx_canvas_mouse_show,
- gx_canvas_mouse_define

## <a name="gx_canvas_mouse_show"></a>gx_canvas_mouse_show


Ligue o cursor do rato

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_mouse_show(GX_CANVAS *canvas);
```

### <a name="description"></a>Descrição

Este serviço torna o cursor do rato visível para a tela especificada. Este serviço requer GX_MOUSE_SUPPORT para ser definido. A API gx_canvas_mouse_define deve ser invocada para definir a imagem do cursor do rato antes de este serviço ser solicitado.

### <a name="parameters"></a>Parâmetros

- **tela** Ponteiro para bloco de controlo de lona

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de informações de rato bem sucedido
- **GX_FAILURE** (0X10) Show de cursor de rato falhado
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_CALLER_ERROR** (0x11) Inválido desta função

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Make mouse cursor hidden ”. */
status = gx_canvas_mouse_show(&my_canvas);

/* If status is GX_SUCCESS the mouse of “my_canvas” has been
hidden successfully. */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_mouse_show,
- gx_canvas_mouse_define

## <a name="gx_canvas_offset_set"></a>gx_canvas_offset_set


Atribuir a lona x,y despensar o ecrã

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_offset_set(
    GX_CANVAS *canvas,
    GX_VALUE x, 
    GX_VALUE y);
```

### <a name="description"></a>Descrição

Este serviço atribui uma compensação de visualização x,y para a tela especificada. Isto controla a posição em que a tela é composta no tampão visível da moldura, e é frequentemente usada quando a tela é menor do que o visor físico.

Se a tela tiver sido ligada a uma camada de gráficos de hardware utilizando a API gx_canvas_hardware_layer_bind,,o serviço gx_canvas_offset_set é implementado diretamente usando suporte de hardware.

### <a name="parameters"></a>Parâmetros

- **tela** Ponteiro para bloco de controlo de lona
- **x** X coordenada de offset
- **y Y** coordenada de offset

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Atribuição bem sucedida de compensação
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_CANVAS** (0x20) Tela inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set display offset for “my_canvas”. */
status = gx_canvas_offset_set(&my_canvas, 20, 30);

/* If status is GX_SUCCESS the canvas drawing is now offset from
position 20,30. */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_alpha_set,
- gx_canvas_create
- gx_canvas_drawing_complete,
- gx_canvas_initiate,
- gx_canvas_shift
- gx_canvas_show,
- gx_canvas_hide,
- gx_canvas_hardware_layer_bind

## <a name="gx_canvas_pie_draw"></a>gx_canvas_pie_draw


Desenhe a tarte

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_pie_draw(
    INT xcenter, 
    INT ycenter,
    UINT r, 
    INT start_angle, 
    INT end_angle);
```

### <a name="description"></a>Descrição

Este serviço atrai uma tarte na tela usando a escova de contexto de desenho atual. A tarte é cortada à região inválida de lona. Este serviço requer que a opção de configuração GX_ARC_DRAWING_SUPPORT ser definida.

### <a name="parameters"></a>Parâmetros

- **xcenter** x-posição do centro da tarte
- **ycenter** y-position do centro da tarte
- **r** Raio da tarte
- **start_angle** Ângulo inicial da tarte
- **end_angle** Ângulo final da tarte

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Sorteio de arco bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_INVALID_VALUE** (0x22) Valor inválido
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho aberto

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Draw a pie from 0 degree to 90 degree in clockwise. */
status = gx_canvas_pie_draw(100, 100, 50, 0, 90);

/* If status is GX_SUCCESS the pie has been drawn to canvas. */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pixelmap_draw,
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw,
- gx_canvas_rectangle_draw
- gx_canvas_text_draw

## <a name="gx_canvas_pixel_draw"></a>gx_canvas_pixel_draw


Desenhar pixel

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_pixel_draw(GX_POINT position);
```

### <a name="description"></a>Descrição

Este serviço desenha um pixel na tela usando a cor da linha da escova de contexto de desenho atual. Se a opção de configuração GX_BRUSH_ALPHA_SUPPORT for definida, misture o pixel com o contrário, desenhe o pixel como totalmente opaco.

- **ponto** x,y posição de pixel para desenhar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Sorteio de pixelmap bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho aberto

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_POINT point; /* the x,y position you want to draw to */
GX_RECTANGLE drawto; /* the rectangle bounding your drawing */
GX_CANVAS *mycanvas; /* the canvas you want to draw to */

/* calculate 1x1 pixel drawing area: */
gx_utility_rectangle_define(&drawto,
    point.gx_point_x, point.gx_point_y,
    point.gx_point_x, point.gx_point_y);

/* get my canvas: */
gx_widget_canvas_get(win, &mycanvas);

/* open my canvas for drawing: */
gx_canvas_drawing_initiate(mycanvas, win, &drawto);

/* setup my brush colors. Use any color ID in your resources: */
gx_context_line_color_set(GX_COLOR_ID_WINDOW_BORDER);

/* draw a pixel: */
status = gx_canvas_pixel_draw(point);

/* close the canvas: */
gx_canvas_drawing_complete(mycanvas, GX_TRUE);

/* If status is GX_SUCCESS, the pixel was successfully drawn to mycanvas. */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_block_move,
- gx_canvas_pixelmap_tile
- gx_canvas_pixelmap_blend

## <a name="gx_canvas_pixelmap_blend"></a>gx_canvas_pixelmap_blend

Misturar pixelmap

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_pixelmap_blend(
    GX_VALUE x_position,
    GX_VALUE y_position, 
    GX_PIXELMAP *pixelmap, 
    GX_UBYTE alpha);
```

### <a name="description"></a>Descrição

Este serviço combina um mapa pixel com o fundo de lona. A relação de mistura é especificada pelo chamador. O valor alfa pode variar de 0 (totalmente transparente) a 255 (totalmente opaco). O mapa de pixels também pode incluir um canal alfa interno, que é combinado com o valor de mistura de entrada. Este serviço só é suportado por controladores de exibição que estão a funcionar a uma profundidade de cor de 16 bpp e superior.

### <a name="parameters"></a>Parâmetros

- **x_start** Início da posição x do pixelmap
- **y_end** Posição inicial do pixelmap
- **pixelmap** Ponteiro para pixelmap

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Sorteio de pixelmap bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_NOT_SUPPORTED** (0x28) Não apoiado
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho aberto

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Draw pixelmap on active canvas */

GX_PIXELMAP *map;
gx_system_pixelmap_get(ID_MY_PIXELMAP, &map);

status = gx_canvas_pixelmap_blend(10, 20, map, 128);

/* If status is GX_SUCCESS the pixelmap has been blended onto the current canvas. */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_block_move,
- gx_canvas_pixelmap_get
- gx_canvas_pixelmap_tile
- gx_canvas_pixelmap_draw

## <a name="gx_canvas_pixelmap_draw"></a>gx_canvas_pixelmap_draw

Desenhar pixelmap

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_pixelmap_draw(
    GX_VALUE x_position, 
    GX_VALUE y_position,
    GX_PIXELMAP *pixelmap);
```

### <a name="description"></a>Descrição

Este serviço desenha um mapa de pixels sobre a tela.

### <a name="parameters"></a>Parâmetros

- **x_start** Início da posição x do pixelmap
- **y_end** Posição inicial do pixelmap
- **pixelmap** Ponteiro para pixelmap

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Sorteio de pixelmap bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho aberto

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Draw pixelmap on canvas. */
status = gx_canvas_pixelmap_draw(10, 20, &my_pixelmap);

/* If status is GX_SUCCESS the pixelmap “my_pixelmap” has been drawn. */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_block_move,
- gx_canvas_pixelmap_get
- gx_canvas_pixelmap_tile
- gx_canvas_pixelmap_blend

## <a name="gx_canvas_pixelmap_get"></a>gx_canvas_pixelmap_get

Obter mapa de tela pixelmap

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_pixelmap_get(GX_PIXELMAP *pixelmap);
```

### <a name="description"></a>Descrição

Este serviço devolve uma estrutura GX_PIXELMAP que aponta para os dados de tela. O formato pixelmap está definido para o formato de cor do ecrã atual.

### <a name="parameters"></a>Parâmetros

- **pixelmap** Pixelmap devolvido

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Pixelmap de sucesso obter
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Draw pixelmap on active canvas */

GX_PIXELMAP *map;

status = gx_canvas_pixelmap_get(map);

/* If status is GX_SUCCESS the pixelmap has been retrieved. */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_pixelmap_blend,
- gx_canvas_pixelmap_tile
- gx_canvas_pixelmap_draw

## <a name="gx_canvas_pixelmap_rotate"></a>gx_canvas_pixelmap_rotate


Desenhe o pixelmap rotativo

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_pixelmap_rotate(
    GX_VALUE x_position, 
    GX_VALUE y_position,
    GX_PIXELMAP *pixelmap, 
    INT angle,
    INT rot_cx, 
    INT rot_cy);
```

### <a name="description"></a>Descrição

Este serviço gira um mapa pixel no ângulo especificado e torna o mapa de pixels diretamente à medida que a rotação é realizada. Este serviço difere de gx_utility_pixelmap_rotate na medida em que a saída da rotação é diretamente entregue à memória de tela, e o mapa de pixels rotativo não é devolvido ao chamador.

A vantagem deste serviço ao longo de gx_utility_pixelmap_rotate é que não é necessária nenhuma memória adicional para manter o pixelmap rotativo. A desvantagem é que o código de rotação deve ser executado cada vez que o mapa de pixels é desenhado.

A validação de recortes e visualizações são aplicadas durante a renderização do pixelmap rotativo.

### <a name="parameters"></a>Parâmetros

- **x_position** Início da posição x do pixelmap
- **y_position** Posição inicial do pixelmap
- **pixelmap** Ponteiro para pixelmap
- **ângulo** Ângulo para rodar
- **rot_cx** X-coord do centro de rotação. Se este valor for definido para -1, o centro da imagem é usado como centro de rotação.
- **rot_cy** Y-coord do centro de rotação. Se este valor for definido para -1, o centro da imagem é usado como o centro de rotação.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Sorteio de pixelmap bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho aberto

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* rotate “src_pixelmap” by 30 degree in clockwise direction and draw in on canvas. */
status = gx_canvas_pixelmap_rotate(10, 20, &my_pixelmap, 30,
    -1, -1);

/* If status is GX_SUCCESS the rotated pixelmap “my_pixelmap” has been drawn. */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_block_move,
- gx_canvas_pixelmap_get
- gx_canvas_pixelmap_tile,
- gx_canvas_pixelmap_blend

## <a name="gx_canvas_pixelmap_tile"></a>gx_canvas_pixelmap_tile

Pixelmap de azulejos

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_pixelmap_tile(
    GX_RECTANGLE *fill,
    GX_PIXELMAP *pixelmap);
```

### <a name="description"></a>Descrição

Este serviço preenche um retângulo dentro de uma tela com o mapa pixel solicitado.

### <a name="parameters"></a>Parâmetros

- **encher** Área para azulejo com pixelmap
- **pixelmap** Ponteiro para pixelmap

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Azulejo de pixelmap bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho aberto
- **GX_INVALID_VALUE** (0x22) Tamanho de enchimento inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Tile pixelmap on canvas */
status = gx_canvas_pixelmap_tile(&tile_area, &my_pixelmap);

/* If status is GX_SUCCESS the pixelmap “my_pixelmap” has been tiled on canvas */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_block_move,
- gx_canvas_pixelmap_get
- gx_canvas_pixelmap_blend,
- gx_canvas_pixelmap_draw

## <a name="gx_canvas_polygon_draw"></a>gx_canvas_polygon_draw


Desenhar polígono

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_polygon_draw(
    GX_POINT *point_array,
    INT number_of_points);
```

### <a name="description"></a>Descrição

Este serviço desenha um polígono sobre a tela utilizando a escova de contexto de desenho atual.

### <a name="parameters"></a>Parâmetros

- **point_array** Matriz de pontos do polígono
- **number_of_points** Número de pontos de polígono

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Sorteio de polígono bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho aberto

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_POINT my_polygon[4] =
{
    { 208, 63 },
    { 274, 63 },
    { 274, 163 },
    { 208, 163 }
};

/* Draw polygon “my_polygon” on canvas. */
status = gx_canvas_polygon_draw(&my_polygon, 4);

/* If status is GX_SUCCESS the polygon “my_polygon” has been drawn. */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile,
- gx_canvas_rectangle_draw
- gx_canvas_text_draw

## <a name="gx_canvas_rectangle_draw"></a>gx_canvas_rectangle_draw


Desenhar retângulo

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_rectangle_draw(GX_RECTANGLE *rectangle);
```

### <a name="description"></a>Descrição

Este serviço desenha um retângulo sobre a tela.

### <a name="parameters"></a>Parâmetros

- **retângulo** Retângulo para desenhar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Sorteio de retângulo bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho aberto

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Draw rectangle “my_rectangle” on canvas. */
status = gx_canvas_rectangle_draw(&my_rectangle);

/* If status is GX_SUCCESS the rectangle “my_rectangle” has been drawn. */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile,
- gx_canvas_polygon_draw
- gx_canvas_text_draw

## <a name="gx_canvas_rotated_text_draw"></a>gx_canvas_rotated_text_draw


Desenhar texto rotativo sobre um ponto central (precedido)

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_rotated_text_draw(
    const GX_CHAR *text,
    GX_VALUE xCenter, 
    GX_VALUE yCenter, 
    INT angle);
```

### <a name="description"></a>Descrição

Esta API foi depreciada a favor ou gx_canvas_rotated_text_draw_ext(). Apesar de ainda apoiadas, as novas aplicações não devem utilizar esta API e devem, em vez disso, utilizar gx_canvas_rotated_text_draw_ext).).

Este serviço atrai texto para a tela. O texto é desenhado rotativamente sobre o ponto central solicitado. A fonte de contexto de desenho atual e a cor da linha de contexto de desenho são usadas para tornar o texto.

Este serviço utiliza a função gx_utility_string_to_alphamap para tornar o fio de texto num mapa de pixels de 8bpp temporário contendo apenas valor alfa. Em seguida, o serviço roda o mapa alfa utilizando a função gx_utility_pixelmap_rotate. Após a substituição alfa final para a tela, este serviço liberta o mapa alfa temporário e a memória associada.

Uma vez que é necessário um mapa alfa temporário para fazer texto rotativo, o pedido deve configurar o gx_system_memory_allocator pela chamada gx_system_memory_allocator_set() API antes de tentar desenhar texto rotativo.

Este serviço só deve ser utilizado para tornar o texto rotativo "uma vez". Se a mesma cadeia de texto for desenhada várias vezes em diferentes locais ou ângulos de rotação diferentes, é mais eficiente utilizar a função de utilidade gx_utility_string_to_alphamap gx_utility_string_to_alphamap para criar o mapa alfa do texto uma vez, em seguida, usar gx_utility_pixelmap_rotate várias vezes para rodar o mapa alfa resultante repetidamente.

### <a name="parameters"></a>Parâmetros

- **texto** Cadeia de texto a ser desenhada
- **xCenter** Posicione central em torno do texto será rodado.
- **yCenter** Posição central em torno do texto será rodado.
- **ângulo** O ângulo de rotação de texto desejado, em graus.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Renderização de texto bem sucedida
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_SYSTEM_MEMORY_ERROR** (0x30) Não foi atribuída memória suficiente ou gx_system_memory_allocator
- **GX_INVALID_STRING_LENGTH** (0x34) Comprimento da corda inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
void my_window_draw(GX_WINDOW *window)
{

    GX_VALUE xpos = 100;
    GX_VALUE ypos = 100;
    INT dynamic_count = 1234567;
    GX_CHAR dynamic_text[10];

    /* Call default window draw routine. */
    gx_window_draw(window);

    /* Set font. */
    gx_context_font_set(GX_FONT_ID_SMALL_BOLD);

    /* Convert int value to string. */
    gx_utility_ltoa(dynamic_count, dynamic_text, 20);

    /* Draw rotate text. */
    gx_canvas_rotated_text_draw(dynamic_text, xpos, ypos, 45);
}
```

### <a name="see-also"></a>Consulte também

- gx_canvas_alpha_set,
- gx_canvas_drawing_complete
- gx_canvas_create,
- gx_canvas_drawing_initiate
- gx_canvas_offset_set,
- gx_canvas_shift

## <a name="gx_canvas_rotated_text_draw_ext"></a>gx_canvas_rotated_text_draw_ext


Desenhar texto rotativo sobre um ponto central

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_rotated_text_draw_ext(
    GX_CONST GX_STRING *text,
    GX_VALUE xCenter, 
    GX_VALUE yCenter, 
    INT angle);
```

### <a name="description"></a>Descrição

Este serviço atrai texto para a tela. O texto é desenhado rotativamente sobre o ponto central solicitado. A fonte de contexto de desenho atual e a cor da linha de contexto de desenho são usadas para tornar o texto.

Este serviço utiliza a função gx_utility_string_to_alphamap para tornar o fio de texto num mapa de pixels de 8bpp temporário contendo apenas valor alfa. Em seguida, o serviço roda o mapa alfa utilizando a função gx_utility_pixelmap_rotate. Após a substituição alfa final para a tela, este serviço liberta o mapa alfa temporário e a memória associada.

Uma vez que é necessário um mapa alfa temporário para fazer texto rotativo, o pedido deve configurar o gx_system_memory_allocator pela chamada ***gx_system_memory_allocator_set*** API antes de tentar desenhar texto rotativo.

Este serviço só deve ser utilizado para tornar o texto rotativo "uma vez". Se a mesma cadeia de texto for desenhada várias vezes em diferentes locais ou ângulos de rotação diferentes, é mais eficiente utilizar a função de utilidade gx_utility_string_to_alphamap gx_utility_string_to_alphamap para criar o mapa alfa do texto uma vez, em seguida, usar gx_utility_pixelmap_rotate várias vezes para rodar o mapa alfa resultante repetidamente.

### <a name="parameters"></a>Parâmetros

- **texto** Cadeia de texto a ser desenhada
- **xCenter** Posicione central em torno do texto será rodado.
- **yCenter** Posição central em torno do texto será rodado.
- **ângulo** O ângulo de rotação de texto desejado, em graus.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Renderização de texto bem sucedida
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_INVALID_CONTEXT** (0x06) Contexto de sorteio inválido
- **GX_SYSTEM_MEMORY_ERROR** (0x30) Não foi atribuída memória suficiente ou gx_system_memory_allocator.
- **GX_INVALID_STRING_LENGTH** (0x34) Comprimento da corda inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
void my_window_draw(GX_WINDOW *window)
{

    GX_VALUE xpos = 100;
    GX_VALUE ypos = 100;
    INT dynamic_count = 1234567;
    GX_CHAR dynamic_text[10];
    GX_STRING string;

    /* Call default window draw routine. */
    gx_window_draw(window);

    /* Set font. */
    gx_context_font_set(GX_FONT_ID_SMALL_BOLD);

    /* Convert int value to string. */
    gx_utility_ltoa(dynamic_count, dynamic_text, 20);

    string.gx_string_ptr = dynamic_text;
    string.gx_string_length = strlen(dynamic_text);

    /* Draw rotate text. */
    gx_canvas_rotated_text_draw_ext(&string, xpos, ypos, 45);
}
```

### <a name="see-also"></a>Consulte também

- gx_canvas_alpha_set,
- gx_canvas_drawing_complete
- gx_canvas_create,
- gx_canvas_drawing_initiate
- gx_canvas_offset_set,
- gx_canvas_shift

## <a name="gx_canvas_shift"></a>gx_canvas_shift


Tela de turno por x,y

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_shift(
    GX_CANVAS *canvas, 
    GX_VALUE x, GX_VALUE y);
```

### <a name="description"></a>Descrição

Este serviço desloca a lona especificada compensada pela quantidade especificada. Isto afeta a posição em que a tela é renderizada dentro do tampão visível da armação.

### <a name="parameters"></a>Parâmetros

- **tela** Ponteiro para bloco de controlo de lona
- **x** Pixels para mudar no eixo X
- **y** Pixels para mudar no eixo Y

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Turno de lona bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_CANVAS** (0x20) Tela inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Shift canvas “my_canvas”. */
status = gx_canvas_shift(&my_canvas, 10, 15);

/* If status is GX_SUCCESS the canvas has been shifted by 10 pixels
    on the X axis and 15 on the Y axis. */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_drawing_complete,
- gx_canvas_initiate
- gx_canvas_alpha_set,
- gx_canvas_create
- gx_canvas_offset_set

## <a name="gx_canvas_show"></a>gx_canvas_show


Faça uma tela visível

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_show(GX_CANVAS *canvas);
```

### <a name="description"></a>Descrição

Este serviço torna visível uma tela. Se a tela tiver sido previamente ligada a uma camada gráfica de hardware utilizando a API gx_canvas_hardware_layer_bind,,o serviço gx_canvas_show() é implementado diretamente usando suporte de hardware.

### <a name="parameters"></a>Parâmetros

- **tela** Ponteiro para bloco de controlo de lona

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Atribuição bem sucedida de compensação
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_CANVAS** (0x20) Tela inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Make this canvas visible. */
status = gx_canvas_show(&my_canvas);

/* If status is GX_SUCCESS the canvas drawing is now visible */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_alpha_set,
- gx_canvas_create
- gx_canvas_drawing_complete,
- gx_canvas_initiate,
- gx_canvas_shift,
- gx_canvas_hide,
- gx_canvas_hardware_layer_bind

## <a name="gx_canvas_text_draw"></a>gx_canvas_text_draw

Desenhar texto (precotado)

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_text_draw(
    GX_VALUE x_start, 
    GX_VALUE y_start,
    GX_CONST GX_CHAR *string, 
    INT length);
```

### <a name="description"></a>Descrição

Este serviço desenha texto na tela. Esta API, apesar de ainda apoiada, é depreciada e as novas aplicações devem, em vez disso, utilizar gx_canvas_text_draw_ext().

### <a name="parameters"></a>Parâmetros

- **x_start** Início da coordenada x para texto
- **y_start** Início da coordenada y para texto
- **cadeia** Ponteiro para corda para desenhar
- **comprimento** Se o comprimento >= 0, limita o número de caracteres atraídos para o comprimento. Se o comprimento < 0, toda a corda até que o exterminador NULL seja puxado.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Sorteio de texto bem sucedido
- **GX_FAILURE** (0x1E) Sorteio de texto falhado
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho aberto
- **GX_INVALID_STRING_LENGTH** (0x34) Comprimento da corda inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Draw text “example” on current canvas”. */
status = gx_canvas_text_draw(10, 20, “example”, 7);

/* Draw all of a string of unknown length on the current canvas */
status = gx_canvas_text_draw(10, 40, string_ptr, -1);

/* If status is GX_SUCCESS the text “example” has been drawn. */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw,
- gx_canvas_rectangle_draw

## <a name="gx_canvas_text_draw_ext"></a>gx_canvas_text_draw_ext


Desenhar texto

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_text_draw_ext(
    GX_VALUE x_start, 
    GX_VALUE y_start,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Descrição

Este serviço desenha texto na tela.

### <a name="parameters"></a>Parâmetros

- **x_start** Início da coordenada x para texto
- **y_start** Início da coordenada y para texto
- **cadeia** Ponteiro para corda para desenhar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Sorteio de texto bem sucedido
- **GX_FAILURE** (0x1E) Sorteio de texto falhado
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho aberto
- **GX_INVALID_STRING_LENGTH** (0x34) Comprimento da corda inválida
- **GX_INVALID_FONT** (0x16) Fonte inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_STRING string;
string.gx_string_ptr = “example”;
string.gx_string_length = 7;

/* Draw text “example” on current canvas”. */
status = gx_canvas_text_draw_ext(10, 20, &string);

/* If status is GX_SUCCESS the text “example” has been drawn. */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw,
- gx_canvas_rectangle_draw

## <a name="gx_checkbox_create"></a>gx_checkbox_create


Criar caixa de verificação

### <a name="prototype"></a>Prototype

```C
UINT gx_checkbox_create(
    GX_CHECKBOX *checkbox, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    GX_RESOURCE_ID text_id,
    ULONG style, 
    USHORT checkbox_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria um widget de caixa de verificação com as propriedades especificadas. GX_CHECKBOX é derivado de GX_TEXT_BUTTON, e todos os serviços gx_text_button podem ser usados com widgets GX_CHECKBOX.

### <a name="parameters"></a>Parâmetros

- **caixa de verificação** Ponteiro para o nome do bloco de controlo da caixa de verificação Nome lógico do widget da caixa de verificação
- **pai** Ponteiro para o widget dos pais
- **text_id** ID de recurso do texto da caixa de verificação
- **estilo** Estilo de caixa de verificação. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **checkbox_id** ID definido pela aplicação da caixa de verificação
- **tamanho** Dimensões da caixa de verificação

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Cria caixa de verificação com sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Create “my_checkbox”. */
status = gx_checkbox_create(&my_checkbox, “my_checkbox”,
    &my_parent,
    MY_CHECKBOX_TEXT_RESOURCE_ID, GX_STYLE_BORDER_RAISED,
    MY_CHECKBOX_ID,
    &size);

/* If status is GX_SUCCESS the checkbox “my_checkbox” has been created. */
```
### <a name="see-also"></a>Consulte também

- gx_checkbox_draw,
- gx_checkbox_event_process,
- gx_checkbox_select

## <a name="gx_checkbox_draw"></a>gx_checkbox_draw

Desenhar caixa de verificação

### <a name="prototype"></a>Prototype

```C
VOID gx_checkbox_draw(GX_CHECKBOX *checkbox);
```

### <a name="description"></a>Descrição

Este serviço desenha a caixa de verificação especificada. Esta função é normalmente chamada internamente pelo mecanismo de atualização de lona GUIX, mas está exposta à aplicação para ajudar na implementação de funções de desenho personalizado para widgets de caixa de verificação personalizados.

### <a name="parameters"></a>Parâmetros

- **caixa de verificação** Ponteiro para bloco de controlo da caixa de verificação

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom checkbox draw function. */
VOID custom_checkbox_draw(GX_CHECKBOX *checkbox)
{
    /* Call default checkbox draw. */
    gx_checkbox_draw(checkbox);

    /* Add custom drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_checkbox_create,
- gx_checkbox_event_process,
- gx_checkbox_select

## <a name="gx_checkbox_event_process"></a>gx_checkbox_event_process


Evento de caixa de verificação de processo

### <a name="prototype"></a>Prototype

```C
UINT gx_checkbox_event_process(
    GX_CHECKBOX *checkbox, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Descrição

Este serviço processa um evento para a caixa de verificação especificada. Este serviço deve ser chamado como o manipulador de eventos predefinido por quaisquer funções de processamento de eventos de caixa de verificação personalizadas.

### <a name="parameters"></a>Parâmetros

- **caixa de verificação** Ponteiro para bloco de controlo da caixa de verificação
- **event_ptr** Ponteiro para o evento para processar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Processo de evento de caixa de verificação bem-sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Call generic checkbox event processing as part of custom event processing function. */

UINT custom_checkbox_event_process(GX_CHECKBOX *checkbox,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default checkbox
            event processing */
        status = gx_checkbox_event_process(checkbox, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Consulte também

- gx_checkbox_create,
- gx_checkbox_draw,
- gx_checkbox_select

## <a name="gx_checkbox_pixelmap_set"></a>gx_checkbox_pixelmap_set


Definir pixelmap para caixa de verificação

### <a name="prototype"></a>Prototype

```C
UINT gx_checkbox_pixelmap_set(
    GX_CHECKBOX *checkbox,
    GX_RESOURCE_ID unchecked_id, 
    GX_RESOURCE_ID checked_id,
    GX_RESOURCE_ID unchecked_disabled_id, 
    GX_RESOURCE_ID checked_disabled_id);
```

### <a name="description"></a>Descrição

Este serviço atribui as pixelmaps a serem apresentadas pela caixa de verificação especificada para cada estado da caixa de verificação. Os IDs de recursos podem ser duplicados.

### <a name="parameters"></a>Parâmetros

- **caixa de verificação** Ponteiro para bloco de controlo da caixa de verificação
- **unchecked_id** Pixelmap utilizado para estado não controlado
- **checked_id** Pixelmap utilizado para estado verificado
- **unchecked_disabled_id** Pixelmap utilizado para uma caixa de verificação desativada e não verificada
- **checked_disabled_id** Pixelmap usado para uma caixa de verificação desativada e verificada

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Selecionado caixa de verificação com sucesso
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Select “my_checkbox”. */
status = gx_checkbox_pixelmap_set(&my_checkbox,
    PIXELMAP_UNCHECKED_ID,
    PIXELMAP_CHECKED_ID, PIXELMAP_UNCHECKED_DISABLED_ID,
    PIXELMAP_CHECKED_SIABLED_ID));

/* If status is GX_SUCCESS the pixelmaps are assigned to the checkbox “my_checkbox” */
```

### <a name="see-also"></a>Consulte também

- gx_checkbox_create,
- gx_checkbox_draw,
- gx_checkbox_event_process

## <a name="gx_checkbox_select"></a>gx_checkbox_select


Selecione caixa de verificação

### <a name="prototype"></a>Prototype

```C
UINT gx_checkbox_select(GX_CHECKBOX *checkbox);
```

### <a name="description"></a>Descrição

Este serviço força uma caixa de verificação para o estado selecionado.

### <a name="parameters"></a>Parâmetros

- **caixa de verificação** Ponteiro para bloco de controlo da caixa de verificação

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Selecionado caixa de verificação com sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Select “my_checkbox”. */
status = gx_checkbox_select(&my_checkbox);

/* If status is GX_SUCCESS the checkbox “my_checkbox” has been toggled. */
```

### <a name="see-also"></a>Consulte também

- gx_checkbox_create,
- gx_checkbox_draw,
- gx_checkbox_event_process

## <a name="gx_circular_gauge_angle_get"></a>gx_circular_gauge_angle_get


Obtenha o ângulo de corrente

### <a name="prototype"></a>Prototype

```C
UINT gx_circular_gauge_angle_get(
    GX_CIRCULAR_GAUGE *gauge, 
    INT *angle);
```

### <a name="description"></a>Descrição

Este serviço recupera o ângulo de agulha atual do widget de bitola circular.

### <a name="parameters"></a>Parâmetros

- **bitola** Ponteiro para bloco de controlo de bitola circular
- **ângulo** Ângulo de agulha atual a ser recuperado

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Ângulo de bitola circular bem sucedido obter
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
INT current_angle;

/* Retrieve the current needle angle of “my_gauge”. */
status = gx_circular_gauge_angle_get(&my_gauge, &current_angle);

/* If status is GX_SUCCESS the current needle angle of “my_gauge” has been retrieved. */
```

### <a name="see-also"></a>Consulte também

- gx_circular_gauge_angle_set,
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw,
- gx_circular_gauge_create
- gx_circular_gauge_draw,
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_angle_set"></a>gx_circular_gauge_angle_set


Definir ângulo de alvo

### <a name="prototype"></a>Prototype

```C
UINT gx_circular_gauge_angle_set(
    GX_CIRCULAR_GAUGE *gauge,
    INT angle);
```

### <a name="description"></a>Descrição

Este serviço define o ângulo alvo de um widget de bitola circular.

### <a name="parameters"></a>Parâmetros

- **bitola** Ponteiro para bloco de controlo de bitola circular
- **ângulo** Ângulo da agulha alvo

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de ângulos de sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set target angle of “my_gauge” to 180. */
status = gx_circular_gauge_angle_set(&my_gauge, 180);

/* If status is GX_SUCCESS the circular gauge of “my_gauge” has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_circular_gauge_angle_get,
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw,
- gx_circular_gauge_create
- gx_circular_gauge_draw,
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_animation_set"></a>gx_circular_gauge_animation_set


Definir parâmetros de animação

### <a name="prototype"></a>Prototype

```C
UINT gx_circular_gauge_animation_set(
    GX_CIRCULAR_GAUGE *gauge,
    INT steps, 
    INT delay);
```

### <a name="description"></a>Descrição

Este serviço define passos de animação e atrasa o tempo para um widget de bitola circular.

### <a name="parameters"></a>Parâmetros

- **bitola** Ponteiro para bloco de controlo de bitola circular
- **passos** Passos totais para uma rotação
- **atraso** Atraso do tempo para cada passo

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Selecionado caixa de verificação com sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_VALUE** (0x22) Valor inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set animation steps and delay time of circular gauge “my_gauge”
    to 30 and 1, the needle of “my_gauge” will rotate from
    current angle to target angle by 30 steps with 1 tick delay between every step. */
status = gx_circular_gauge_animation_set(&my_gauge, 30, 1);

/* If status is GX_SUCCESS the steps and delay time of “my_gauge” has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_circular_gauge_angle_get,
- gx_circular_gauge_angle_set
- gx_circular_gauge_background_draw,
- gx_circular_gauge_create
- gx_circular_gauge_draw,
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_background_draw"></a>gx_circular_gauge_background_draw


Desenhe o fundo do bitola circular

### <a name="prototype"></a>Prototype

```C
VOID gx_circular_gauge_background_draw(GX_CIRCULAR_GAUGE *gauge);
```

### <a name="description"></a>Descrição

Este serviço desenha o fundo do bitola circular especificado. Este serviço é normalmente chamado internamente pela função gx_circular_gauge_draw, mas está exposto à aplicação para ajudar a escrever funções de desenho personalizado.

### <a name="parameters"></a>Parâmetros

- **bitola** Ponteiro para bloco de controlo de bitola circular

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Draw circular gauge background. */
gx_circular_gauge_background_draw(&my_circular_gauge);
```

### <a name="see-also"></a>Consulte também

- gx_circular_gauge_angle_get,
- gx_circular_gauge_angle_set
- gx_circular_gauge_animation_set,
- gx_circular_gauge_create
- gx_circular_gauge_draw,
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_create"></a>gx_circular_gauge_create


Criar bitola circular

### <a name="prototype"></a>Prototype

```C
UINT gx_circular_gauge_create(
    GX_CIRCULAR_GAUGE *gauge,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_CIRCULAR_GAUGE_INFO *info,
    GX_RESOURCE_ID background_id,
    ULONG style,
    USHORT circular_gauge_id,
    GX_VALUE xpos,
    GX_VALUE ypos);
```

### <a name="description"></a>Descrição

Este serviço cria um widget de bitola circular com as propriedades especificadas.

### <a name="parameters"></a>Parâmetros

- **bitola** Ponteiro para bloco de controlo de bitola circular
- **nome** Nome lógico do widget de bitola circular
- **pai** Ponteiro para o widget dos pais
- **informação** Ponteiro para a estrutura de informação do medidor. **Apêndice I** contém definição para GX_CIRCULAR_GAUGE_INFO estrutura
- **background_id** ID de recurso do pixelmap de fundo de bitola circular
- **estilo** Estilo de bitola circular. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **circular_gauge_id** ID definido pela aplicação do bitola circular
- **xpos** Posição de coordenada x bitola
- **ypos** Posição de coordenada y de bitola

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Selecionado caixa de verificação com sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_CIRCULAR_GAUGE gauge_info;

gauge_info.gx_circular_gauge_info_animation_steps = 30;
gauge_info.gx_circular_gauge_info_animation_delay = 1;
gauge_info.gx_circular_gauge_info_needle_xpos = 140;
gauge_info.gx_circular_gauge_info_needle_ypos = 140;
gauge_info.gx_circular_gauge_info_neelde_xcor = 20;
gauge_info.gx_circular_gauge_info_neelde_ycor = 88;
gauge_info.gx_circular_gauge_info_needle_pixelmap = GX_PIXELMAP_ID_NEEDLE;

/* Create “my_gauge”. */
status = gx_circular_gauge_create(&my_gauge, “my_gauge”,
            &my_parent,
            &gauge_info, MY_PIXELMAP_RESOURCE_ID, GX_NULL,
            MY_ICON_ID, 5, 30);

/* If status is GX_SUCCESS the circular gauge “my_gauge” has been created. */
```

### <a name="see-also"></a>Consulte também

- gx_circular_gauge_angle_get,
- gx_circular_gauge_angle_set
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw,
- gx_circular_gauge_draw
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_draw"></a>gx_circular_gauge_draw

Desenhe o calibre circular

### <a name="prototype"></a>Prototype

```C
VOID gx_circular_gauge_draw(GX_CIRCULAR_GAUGE *gauge);
```

### <a name="description"></a>Descrição

Este serviço desenha o medidor circular especificado. Esta função é normalmente chamada internamente pelo mecanismo de atualização de lona GUIX, mas está exposta à aplicação para ajudar na implementação de funções de desenho personalizado para widgets de bitola personalizada.

### <a name="parameters"></a>Parâmetros

- **bitola** Ponteiro para bloco de controlo de bitola circular

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom circular gauge draw function. */
VOID custom_gauge_draw(GX_CIRCULAR_GAUGE *gauge)
{
    /* Call default circular gauge draw. */
    gx_circular_gauge_draw(gauge);

    /* Add custom drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_circular_gauge_angle_get,
- gx_circular_gauge_angle_set
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw
- gx_circular_gauge_create,
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_event_process"></a>gx_circular_gauge_event_process


Evento de bitola circular do processo

### <a name="prototype"></a>Prototype

```C
UINT gx_circular_gauge_event_process(
    GX_CIRCULAR_GAUGE *gauge,
    GX_EVENT *event);
```

### <a name="description"></a>Descrição

Este serviço processa um evento para o bitola circular especificado.

### <a name="parameters"></a>Parâmetros

- **bitola** Ponteiro para medir bloco de controlo
- **event_ptr** Ponteiro para o evento para processar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Processo de evento de bitola bem-sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Call generic circular gauge event processing as part of custom event processing function. */
UINT custom_gauge_event_process(GX_CIRCULAR_GAUGE *gauge,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default circular gauge
             event processing */
        status = gx_circular_gauge_event_process(gauge, event);
        break;
}
return status;
```

### <a name="see-also"></a>Consulte também

- gx_circular_gauge_angle_get,
- gx_circular_gauge_angle_set
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw,
- gx_circular_gauge_create
- gx_circular_gauge_draw

## <a name="gx_context_brush_default"></a>gx_context_brush_default


Conjunto pincel do contexto de desenho atual

### <a name="prototype"></a>Prototype

```C
UINT gx_context_brush_default(GX_DRAW_CONTEXT *context);
```

### <a name="description"></a>Descrição

Este serviço define a escova do contexto de desenho especificado para predefinido.

### <a name="parameters"></a>Parâmetros

- **contexto** Ponteiro para bloco de controlo de contexto

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Criação bem sucedida
- **GX_PTR_ERROR** (0x07) Ponteiro de contexto inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the brush of “my_context” to default. */
status = gx_context_brush_default(&my_context);

/* If status is GX_SUCCESS the brush of “my_context” has been set to default. */

```

### <a name="see-also"></a>Consulte também

- gx_context_brush_define,
- gx_context_brush_get
- gx_context_brush_set,
- gx_context_brush_style_set
- gx_context_brush_pattern_set,
- gx_context_brush_width_set
- gx_context_fill_color_set,
- gx_context_font_set
- gx_context_line_color_set,
- gx_context_pixelmap_set
- gx_context_raw_brush_define,
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_brush_define"></a>gx_context_brush_define


Definir pincel do contexto de desenho atual

### <a name="prototype"></a>Prototype

```C
UINT gx_context_brush_define(
    GX_RESOURCE_ID line_color_id,
    GX_RESOURCE_ID fill_color_id, 
    UINT style);
```

### <a name="description"></a>Descrição

Este serviço define a escova do contexto de desenho atual.

### <a name="parameters"></a>Parâmetros

- **line_color_id** Identificação de recursos da cor da linha. **O apêndice B** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.
- **fill_color_id** Identificação de recursos da cor de preenchimento. **O apêndice B** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.
- **estilo** Estilo de pincel. **O apêndice D** descreve os estilos de escova suportados. Os estilos de escova podem ser combinados numa variável utilizando uma operação bitwise OR.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Definição de pincel de contexto bem sucedido
- **ID** de recursos inválidos de GX_INVALID_RESOURCE_ID (0x33)
- **GX_INVALID_CONTEXT** (0x06) Nenhum contexto de desenho ativo define
- **ID** de recursos inválidos de GX_INVALID_RESOURCE_ID (0x33)
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho ativo

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Define the brush of the current context. */
status = gx_context_brush_define(GX_COLOR_BLACK_ID,
    GX_COLOR_BLACK_ID,
    GX_STYLE_BORDER_NONE);

/* If status is GX_SUCCESS the brush of the current context has been defined. */
```

### <a name="see-also"></a>Consulte também

- gx_context_brush_default,
- gx_context_brush_get
- gx_context_brush_set,
- gx_context_brush_pattern_set
- gx_context_brush_style_set,
- gx_context_brush_width_set
- gx_context_fill_color_set,
- gx_context_font_set
- gx_context_line_color_set,
- gx_context_pixelmap_set
- gx_context_raw_brush_define,
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_brush_get"></a>gx_context_brush_get


Obtenha pincel do contexto de desenho atual

### <a name="prototype"></a>Prototype

```C
UINT gx_context_brush_get(GX_BRUSH **return_brush);
```

### <a name="description"></a>Descrição

Este serviço devolve um ponteiro à escova ativa no contexto de desenho atual. Se não houver um contexto de desenho ativo, o serviço falha e devolve um ponteiro NULO.

### <a name="parameters"></a>Parâmetros

- **return_brush** Ponteiro para destino para escova.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) escova de contexto recuperada com sucesso
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho ativo
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_BRUSH *my_brush;

/* Get the brush of the current context. */
status = gx_context_brush_get(&my_brush);

/* If status is GX_SUCCESS the brush of the current context has been retrieved. */
```

### <a name="see-also"></a>Consulte também

- gx_context_brush_set,
- gx_context_brush_style_set
- gx_context_brush_default,
- gx_context_brush_define
- gx_context_brush_pattern_set,
- gx_context_brush_width_set
- gx_context_fill_color_set,
- gx_context_font_set
- gx_context_line_color_set,
- gx_context_pixelmap_set
- gx_context_raw_brush_define,
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_brush_pattern_set"></a>gx_context_brush_pattern_set


Definir padrão de pincel do contexto de desenho atual

### <a name="prototype"></a>Prototype

```C
UINT gx_context_brush_pattern_set(ULONG pattern);
```

### <a name="description"></a>Descrição

Este serviço define o padrão de escova do contexto de desenho atual.

O padrão da escova é utilizado para desenhar linhas verticais horizontais e tracejadas. Quando o gx_canvas_line_draw é chamado, e a linha é horizontal ou vertical, e o campo de brush.gx_brush_line_pattern não é zero, uma linha de padrão é desenhada.

A máscara de padrão da escova é atualmente suportada apenas para linhas horizontais e verticais.

### <a name="parameters"></a>Parâmetros

- **padrão** Padrão para ser usado para a escova. Este é um simples padrão hexadécimal ligado/desligado para ser usado para desenho de linha de padrão.

### <a name="return-values"></a>Valores de devolução

- **conjunto** de pincel de GX_SUCCESS (0x00) de sucesso
- **GX_INVALID_CONTEXT** (0x06) Contexto de desenho inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the brush pattern for the current contex. */
status = gx_context_brush_pattern_set(0x80808080);

/* If status is GX_SUCCESS the brush pattern of the current context
has been set to the specified pattern. */
```

### <a name="see-also"></a>Consulte também

- gx_context_brush_default,
- gx_context_brush_define
- gx_context_brush_get,
- gx_context_brush_style_set
- gx_context_brush_width_set,
- gx_context_fill_color_set
- gx_context_font_set,
- gx_context_line_color_set
- gx_context_pixelmap_set,
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set,
- gx_context_raw_line_color_set

## <a name="gx_context_brush_set"></a>gx_context_brush_set


Conjunto pincel do contexto de desenho atual

### <a name="prototype"></a>Prototype

```C
UINT gx_context_brush_set(GX_BRUSH *brush);
```

### <a name="description"></a>Descrição

Este serviço define a escova do contexto de desenho atual.

### <a name="parameters"></a>Parâmetros

- **pincel** Ponteiro para escovar para o contexto atual.

### <a name="return-values"></a>Valores de devolução

- **conjunto** de pincel de GX_SUCCESS (0x00) de sucesso
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho ativo
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_BRSUH my_brush;
GX_FONT *font;
GX_COLOR fill_color;
GX_COLOR line_color;

/* Retrieve the font that associated with the specified font ID. */
gx_context_font_get(MY_FONT_ID, &font);

/* Retrieve the color that associated with the specified color ID. */
gx_context_color_get(MY_FILL_COLOR_ID, &fill_color);
gx_context_color_get(MY_LINE_COLOR, &line_color);

my_brush.gx_brush_pixelmap = MY_PIXELMAP_ID;
my_brush.gx_brush_font = font;
my_brush.gx_brush_line_pattern = 0x80808080;
my_brush.gx_brush_pattern_mask = 0x80000000;
my_brush.gx_brush_fill_color = fill_color;
my_brush.gx_brush_line_color = line_color;
my_brush.gx_brush_style = GX_BRSUH_SOLID_FILL | GX_BRUSH_ALIAS |
                          GX_BRUSH_PIXELMAP_FILL | GX_BRUSH_ROUND
my_brush.gx_brush_width = 2;
my_brush.gx_brush_alpha = 255;

/* Set the brush of the current context. */
status = gx_context_brush_set(my_brush);

/* If status is GX_SUCCESS the brush of the current context has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_context_brush_default,
- gx_context_brush_define
- gx_context_brush_get,
- gx_context_brush_pattern_set
- gx_context_brush_style_set,
- gx_context_brush_width_set
- gx_context_fill_color_set,
- gx_context_font_set
- gx_context_line_color_set,
- gx_context_pixelmap_set
- gx_context_raw_brush_define,
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_brush_style_set"></a>gx_context_brush_style_set


Definir estilo pincel do contexto de desenho atual

### <a name="prototype"></a>Prototype

```C
UINT gx_context_brush_style_set(UINT style);
```

### <a name="description"></a>Descrição

Este serviço define o estilo de pincel do contexto de desenho atual.

### <a name="parameters"></a>Parâmetros

- **estilo** Estilo pincel do contexto atual. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) conjunto de estilo de pincel de contexto bem sucedido
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho ativo

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the brush style of the current context. */
status = gx_context_brush_style_set(GX_BRUSH_ALIAS);

/* If status is GX_SUCCESS the brush style of the current context has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_context_brush_default,
- gx_context_brush_define
- gx_context_brush_get,
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_width_set,
- gx_context_fill_color_set
- gx_context_font_set,
- gx_context_line_color_set
- gx_context_pixelmap_set,
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set,
- gx_context_raw_line_color_set

## <a name="gx_context_brush_width_set"></a>gx_context_brush_width_set


Definir largura da escova do contexto de desenho atual

### <a name="prototype"></a>Prototype

```C
UINT gx_context_brush_width_set(UINT width);
```

### <a name="description"></a>Descrição

Este serviço define a largura da escova ativa no contexto de desenho atual.

### <a name="parameters"></a>Parâmetros

**largura** Largura da escova em pixels do contexto atual

### <a name="return-values"></a>Valores de devolução

**GX_SUCCESS** (0x00) Conjunto de largura de pincel de contexto bem sucedido

**GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho ativo

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the brush width of the current context to 10 pixels. */
status = gx_context_brush_width_set(10); /*

If status is GX_SUCCESS the brush width of the current context has been set to 10. */
```

### <a name="see-also"></a>Consulte também

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_color_get"></a>gx_context_color_get


Obtenha valor de cor associado com iD de cor no contexto de desenho atual

### <a name="prototype"></a>Prototype

```C
UINT gx_context_color_get(
    GX_RESOURCE_ID color_id,
    GX_COLOR *return_color);
```

### <a name="description"></a>Descrição

Este serviço recupera o valor de cor associado ao ID de cor indicado. O valor da cor é devolvido no formato de cor do ecrã de contexto ativo. Este serviço só deve ser chamado a partir de uma operação de desenho ativo.

### <a name="parameters"></a>Parâmetros

**color_id** Identificação de recursos de cor solicitada.

**return_color** Endereço de variável para manter o valor de cor devolvido.

### <a name="return-values"></a>Valores de devolução

**GX_SUCCESS** (0x00) Valor de cor bem sucedido obtém

**ID** de recursos inválidos de GX_INVALID_RESOURCE_ID (0x33)

**GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho ativo

**GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_COLOR color_value;

/* Get the color vaue. */
status = gx_context_color_get(MY_BLACK_COLOR_ID, &color_value);
```

### <a name="see-also"></a>Consulte também

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_fill_color_set"></a>gx_context_fill_color_set

Definir a cor do preenchimento do contexto de desenho atual

### <a name="prototype"></a>Prototype

```C
UINT gx_context_fill_color_set(GX_RESOURCE_ID fill_color_id);
```

### <a name="description"></a>Descrição

Este serviço define a cor de preenchimento da escova ativa no contexto de desenho atual.

### <a name="parameters"></a>Parâmetros

- **fill_color_id** ID de recurso da cor de preenchimento do contexto atual. **O apêndice B** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de cores de preenchimento de contexto bem sucedido
- **ID** de recursos inválidos de GX_INVALID_RESOURCE_ID (0x33)
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho ativo

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the fill color of the current context to black. */
status = gx_context_fill_color_set(MY_BLACK_COLOR_ID);

/* If status is GX_SUCCESS the fill color of the current context has been set to black. */
```

### <a name="see-also"></a>Consulte também

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_font_get"></a>gx_context_font_get

Obtenha o tipo de letra associado com iD de fonte no contexto de sorteio atual

### <a name="prototype"></a>Prototype

```C
UINT gx_context_font_get(
    GX_RESOURCE_ID font_id,
    GX_FONT **return_font);
```

### <a name="description"></a>Descrição

Este serviço recupera o ponteiro de fonte associado ao ID de fonte indicado. Este serviço só deve ser chamado a partir de uma operação de desenho ativo.

### <a name="parameters"></a>Parâmetros

- **font_id** Identificação de recursos de fonte solicitada.
- **return_font** Endereço de variável para segurar ponteiro de fonte devolvido.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Fonte recuperada com sucesso
- **ID** de recursos inválidos de GX_INVALID_RESOURCE_ID (0x33)
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho ativo
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_FONT *my_font;

/* Get the font pointer. */
status = gx_context_font_get(MY_MIDSIZE_FONT, &my_font);

/* If status is GX_SUCCESS, the font that indicated with MY_MIDSIZE_FONT has been successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_font_set"></a>gx_context_font_set

Fonte definida do contexto de desenho atual

### <a name="prototype"></a>Prototype

```C
UINT gx_context_font_set(GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Descrição

Este serviço define a fonte na escova ativa do contexto de desenho atual.

### <a name="parameters"></a>Parâmetros

- **font_id** ID de recurso de fonte do contexto atual

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de fontes de contexto bem sucedido
- **ID** de recursos inválidos de GX_INVALID_RESOURCE_ID (0x33)
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho ativo

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the font of the current context to MY_FONT_ID. */
status = gx_context_font_set(MY_FONT_ID);

/* If status is GX_SUCCESS the font of the current context has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_line_color_set"></a>gx_context_line_color_set

Definir a cor da linha do contexto de desenho atual

### <a name="prototype"></a>Prototype

```C
UINT gx_context_line_color_set(GX_RESOURCE_ID line_color_id);
```

### <a name="description"></a>Descrição

Este serviço define a cor de linha da escova ativa no contexto de desenho atual.

### <a name="parameters"></a>Parâmetros

- **line_color_id** Cor de linha do contexto atual. **O apêndice B** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de cores de linha de contexto bem sucedido
- **ID** de recursos inválidos de GX_INVALID_RESOURCE_ID (0x33)
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho ativo

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the line color of the current context to black. */
status = gx_context_line_color_set(GX_COLOR_BLACK_ID);

/* If status is GX_SUCCESS the line color of the current context has been set to black. */
```

### <a name="see-also"></a>Consulte também

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_pixelmap_get"></a>gx_context_pixelmap_get

Obtenha pixelmap associado com ID pixelmap no contexto de sorteio atual

### <a name="prototype"></a>Prototype

```C
UINT gx_context_pixelmap_get(
    GX_RESOURCE_ID pixelmap_id,
    GX_PIXELMAP **return_map);
```

### <a name="description"></a>Descrição

Este serviço recupera o ponteiro pixelmap associado ao ID do pixelmap indicado.

### <a name="parameters"></a>Parâmetros

- **pixelmap_id** Identificação de recursos do pixelmap solicitado.
- **return_map** Endereço de variável para manter o endereço de pixelmap devolvido.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) recuperou com sucesso o pixelmap
- **ID** de recursos inválidos de GX_INVALID_RESOURCE_ID (0x33)
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho ativo
- **GX_PTR_ERROR** (0x07) Ponteiro de pixels inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_PIXELMAP *map;

/* Get the pixelmap pointer. */
status = gx_context_pixelmap_get(MY_PIXELMAP_ID, &map);

/* If status is GX_SUCCESS, the pixelmap was successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_pixelmap_set"></a>gx_context_pixelmap_set

Definir pixelmap do contexto de sorteio atual

### <a name="prototype"></a>Prototype

```C
UINT gx_context_pixelmap_set(GX_RESOURCE_ID pixelmap_id);
```

### <a name="description"></a>Descrição

Este serviço atribui o mapa pixel da escova ativa no contexto de desenho atual.

### <a name="parameters"></a>Parâmetros

- **pixelmap_id** ID de recursos Pixelmap para usar para o contexto atual

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de pixels de contexto bem sucedido
- **ID** de recursos inválidos de GX_INVALID_RESOURCE_ID (0x33)
- **GX_INVLAID_CONTEXT** (0x06) Contexto inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set pixelmap of the current context to MY_PIXELMAP_ID. */
status = gx_context_pixelmap_set(MY_PIXELMAP_ID);

/* If status is GX_SUCCESS the pixelmap of the current context has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_raw_brush_define"></a>gx_context_raw_brush_define

Defina pincel cru do contexto de desenho atual

### <a name="prototype"></a>Prototype

```C
UINT gx_context_raw_brush_define(
    GX_COLOR line_color,
    GX_COLOR fill_color, 
    UINT style);
```

### <a name="description"></a>Descrição

Este serviço define a escova crua do contexto atual do ecrã. Definições brutas são usadas quando os valores de cor ARGB de 32 bits devem ser passados para a escova em vez de IDs de cor. As definições de cor bruta são úteis quando a cor desejada não está presente na tabela de cores do sistema atual ou quando o valor da cor RGB é calculado no tempo de execução.

### <a name="parameters"></a>Parâmetros

- **line_color** Cor da linha em formato de cor ARGB cru de 32 bits. **O apêndice A** contém cores pré-definidas. Note que a aplicação também pode adicionar cores personalizadas.
- **fill_color** Cor de preenchimento em formato de cor ARGB cru de 32 bits. **O apêndice A** contém cores pré-definidas. Note que a aplicação também pode adicionar cores personalizadas.
- **estilo** Estilo de pincel. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Definição de pincel cru de contexto bem sucedido
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho ativo

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Define the raw brush of the current context. */
status = gx_context_raw_brush_define(GX_COLOR_BLACK,
    GX_COLOR_BLACK, GX_STYLE_BORDER_NONE);

/* If status is GX_SUCCESS the raw brush of the current context has been defined. */
```

### <a name="see-also"></a>Consulte também

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_raw_fill_color_set"></a>gx_context_raw_fill_color_set

Definir a cor de preenchimento bruto do contexto de desenho atual

### <a name="prototype"></a>Prototype

```C
UINT gx_context_raw_fill_color_set(GX_COLOR line_color);
```

### <a name="description"></a>Descrição

Este serviço define a cor de enchimento bruto do contexto atual do ecrã. O parâmetro line_color é um valor de cor bruta de formato ARGB de 32 bits, em vez de um valor de ID de cor. As definições de cor bruta são úteis quando a cor desejada não está presente na tabela de cores do sistema atual ou quando o valor da cor RGB é calculado no tempo de execução.

### <a name="parameters"></a>Parâmetros

- **line_color** Cor da linha. **O apêndice A** contém cores pré-definidas. Note que a aplicação também pode adicionar cores personalizadas.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de cores de preenchimento bruto de contexto bem sucedido
- **GX_INVALID_CONTEXT** (0x06) Sem contexto de desenho ativo

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the raw fill color of the current context. */
status = gx_context_raw_fill_color_set(GX_COLOR_BLACK);

/* If status is GX_SUCCESS the raw fill color of the current context has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_line_color_set

## <a name="gx_context_raw_line_color_set"></a>gx_context_raw_line_color_set

Definir a cor da linha bruta do contexto de desenho atual

### <a name="prototype"></a>Prototype

```C
UINT gx_context_raw_line_color_set(GX_COLOR line_color);
```

### <a name="description"></a>Descrição

Este serviço define a cor de linha da escova ativa no contexto de desenho atual. O parâmetro line_color é um valor de cor bruta de formato ARGB de 32 bits, em vez de um valor de ID de cor. As definições de cor bruta são úteis quando a cor desejada não está presente na tabela de cores do sistema atual ou quando o valor da cor RGB é calculado no tempo de execução.

### <a name="parameters"></a>Parâmetros

- **line_color** Cor do valor da linha. **O apêndice A** contém cores pré-definidas. Note que a aplicação também pode adicionar cores personalizadas.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de cores de linha crua de contexto bem sucedido
- **GX_INVALID_CONTEXT** (0X06) Sem contexto de desenho ativo

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

```C
/* Set the raw line color of the current context. */
status = gx_context_raw_line_color_set(GX_COLOR_BLACK);

/* If status is GX_SUCCESS the raw line color of the current context has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set

## <a name="gx_context_string_get"></a>gx_context_string_get

Obter corda associada ao ID de corda (precotado)

### <a name="prototype"></a>Prototype

```C
UINT gx_context_string_get(GX_RESOURCE_ID string_id,
    GX_CONST GX_CHAR **return_string);
```

### <a name="description"></a>Descrição

Esta API prevadizada devolve a cadeia associada ao ID de cadeia dado. As novas aplicações devem ser utilizadas gx_context_string_get_ext( ).

### <a name="parameters"></a>Parâmetros

- **string_id** ID de corda gerado pela aplicação GUIX Studio.
- **return_string** Endereço de variável para devolver ponteiro de corda.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de cores de linha crua de contexto bem sucedido
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_INVALID_CONTEXT** (0X06) Sem contexto de desenho ativo

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_CHAR *text;

status = gx_context_string_get(GX_ID_ERROR, &text);

/* If status is GX_SUCCESS the string pointer has been returned. */
```

### <a name="see-also"></a>Consulte também

- gx_context_string_get_ext

## <a name="gx_context_string_get_ext"></a>gx_context_string_get_ext

Recupere a corda associada ao ID da corda dada.

### <a name="prototype"></a>Prototype

```C
UINT gx_context_string_get_ext(
    GX_RESOURCE_ID string_id, 
    GX_STRING *return_string);
```

### <a name="description"></a>Descrição

Este serviço devolve a cadeia associada a um dado ID de cadeia. Este serviço só pode ser invocado quando existe um contexto de desenho ativo, ou seja, a partir da função de desenho de um widget. Este serviço identifica a tela e o visor ativo e recupera a corda da placa de exibição localizada.

### <a name="parameters"></a>Parâmetros

- **string_id** O String ID foi utilizado para identificar a cadeia, tal como gerado pelo GUIX Studio no ficheiro de cabeçalho de recursos de aplicação.
- **return_string** Endereço de GX_STRING variável em que o ponteiro de corda e o comprimento da corda serão devolvidos.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de cores de linha crua de contexto bem sucedido
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_INVALID_CONTEXT** (0X06) Sem contexto de desenho ativo

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo


```C
GX_STRING string;

/* Set the raw line color of the current context. */
status = gx_context_string_get_ext(ID_ERROR, &string);

/* If status is GX_SUCCESS the string.gx_string_ptr and
string.gx_string_length values have been returned. */
```

### <a name="see-also"></a>Consulte também

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set

## <a name="gx_display_active_language_set"></a>gx_display_active_language_set

Atribua o idioma ativo do ecrã

### <a name="prototype"></a>Prototype

```C
UINT gx_display_active_language_set(
    GX_DISPLAY *display, 
    GX_UBYTE language);
```

### <a name="description"></a>Descrição

Este serviço atribui o idioma ativo atualmente para o visor indicado. O índice linguístico corresponde às línguas definidas na tabela de linguagem de exibição, e não é um identificador de língua ANSI.

Diferentes ecrãs num sistema multi-ecrã podem executar diferentes idiomas ativos. A tabela de idiomas de visualização deve ser atribuída antes da utilização desta API. Quando um visor é inicializado usando gx_studio_display_configure, a tabela de idiomas é automaticamente instalada e a aplicação passa no índice de linguagem ativa.

### <a name="parameters"></a>Parâmetros

- **exibir** Ponteiro para exibir bloco de controlo
- **língua** Índice de linguagem ativa

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Designação de linguagem de sucesso
- **GX_PTR_ERROR** (0x07) Ponteiro de exibição inválido
- **GX_INVALID_VALUE** (0x22) Índice linguístico inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Change value of color MY_COLOR_ID. */
status = gx_display_active_language_set(&my_display,
    LANGUAGE_ENGLISH);

/* If status is GX_SUCCESS the active language has been assigned. */
```

### <a name="see-also"></a>Consulte também

- gx_display_language_table_set
- gx_studio_display_configure

## <a name="gx_display_color_set"></a>gx_display_color_set

Reatribuir um valor de cor

### <a name="prototype"></a>Prototype

```C
UINT gx_display_color_set(
    GX_DISPLAY *display,
    GX_RESOURCE_ID color_id, 
    GX_COLOR new_color);
```

### <a name="description"></a>Descrição

Este serviço reatribui o valor de cor associado ao ID de cor especificado. Isto pode ser usado para modificar a tabela de cores de um ecrã sem fornecer uma mesa de cores inteiramente nova. O valor de cor fornecido deve estar no formato nativo suportado pelo visor.

### <a name="parameters"></a>Parâmetros

- **exibir** Ponteiro para exibir bloco de controlo
- **color_id** ID de cor para reatribuir
- **new_color** Valor de cor para atribuir a esta ranhura de color_id

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Reatribuição de cor bem sucedida
- **ID** de cor inválida GX_INVALID_RESOURCE_ID (0x33)
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_INVALID_DISPLAY** (0x1D) Exibição inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Change value of color MY_COLOR_ID. */
status = gx_display_color_set(&my_display, MY_COLOR_ID, 0x5454);

/* If status is GX_SUCCESS the color has been reassigned. */
```

### <a name="see-also"></a>Consulte também

- gx_display_color_table_set

## <a name="gx_display_color_table_set"></a>gx_display_color_table_set

Atribuir tabela de cores de exibição

### <a name="prototype"></a>Prototype

```C
UINT gx_display_color_table_set(
    GX_DISPLAY *display,
    GX_COLOR *color_table, 
    INT color_count);
```

### <a name="description"></a>Descrição

Este serviço reatribui a tabela de cores a utilizar pelo visor. Este serviço é normalmente invocado pela função de configuração gerada pelo GUIX Studio, mas também pode ser chamado pelo software de aplicação.

### <a name="parameters"></a>Parâmetros

- **exibir** Ponteiro para exibir bloco de controlo
- **color_table** Matriz de valores de cor no formato nativo de exibição.
- **color_count** Indica o número de entradas na tabela de cores

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de mesa de cores bem-sucedido
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_INVALID_DISPLAY** (0x1D) Exibição inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_COLOR default_table[32] = { … };

/* Change the color table */
status = gx_display_color_table_set(&my_display, default_table, 32);

/* If status is GX_SUCCESS the color table has been reassigned. */
```

### <a name="see-also"></a>Consulte também

- gx_display_color_set

## <a name="gx_display_create"></a>gx_display_create

Criar exibição

### <a name="prototype"></a>Prototype

```C
UINT gx_display_create(
    GX_DISPLAY *display, 
    GX_CONST CHAR *name,
    UINT (*display_driver_setup)(GX_DISPLAY *),
    GX_VALUE width, 
    GX_VALUE height);
```

### <a name="description"></a>Descrição

Este serviço cria um visor e chama a função de configuração do controlador de exibição. O GUIX pega neste ecrã e adiciona-o à sua lista interna de visualizações.

### <a name="parameters"></a>Parâmetros

- **exibir** Ponteiro para exibir bloco de controlo
- **nome** Nome do visor
- **display_driver_setup** Ponteiro para exibir função de configuração do controlador
- **optional_driver_info** Ponteiro para informações opcionais do condutor
- **color_format** Formato de cor, tal como definido no **Apêndice C**
- **largura** Número de pixels no eixo x
- **altura** Número de pixels no eixo y

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Criação de exibição bem sucedida
- **GX_SYSTEM_ERROR** (0xFE) Não conseguir configurar o ecrã
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_SIZE** (0x23) Tamanho do bloco de controlo de exibição inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_DISPLAY my_display;

UINT my_driver_setup_callback(GX_DISPLAY *display)
{
    …
}

/* Create screen “my_display”. */
status = gx_display_create(&my_display, “my display”,
    my_driver_setup_callback, 320, 480);

/* If status is GX_SUCCESS, the screen “my_display” has been created. */
```

### <a name="see-also"></a>Consulte também

- gx_display_delete

## <a name="gx_display_delete"></a>gx_display_delete


Destrua a exibição

### <a name="prototype"></a>Prototype

```C
UINT gx_display_delete(
    GX_DISPLAY *display,
    VOID (*display_driver_cleanup)(GX_DISPLAY *));
```

### <a name="description"></a>Descrição

Este serviço encerra um ecrã e limpa os recursos atribuídos.

### <a name="parameters"></a>Parâmetros

- **exibir** Ponteiro para exibir bloco de controlo
- **display_driver_cleanup** Ponteiro para exibir função de limpeza do controlador

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Exibição bem sucedida
- **GX_FAILURE** (0x10) Lista de visualização criada é NU
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
VOID driver_cleanup_callback(GX_DISPLAY *display)
{
    …
}

/* Delete a display “my_display”. */
status = gx_display_delete(&my_display, driver_cleanup_callback);

/* If status is GX_SUCCESS the screen “my_display” has been destroyed. */
```

### <a name="see-also"></a>Consulte também

- gx_canvas_block_move
- gx_canvas_line_draw
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw
- gx_canvas_text_draw
- gx_display_create

## <a name="gx_display_font_table_set"></a>gx_display_font_table_set

Atribuir tabela de fontes de exibição

### <a name="prototype"></a>Prototype

```C
UINT gx_display_font_table_set(
    GX_DISPLAY *display,
    GX_FONT **font_table, 
    INT table_size);
```

### <a name="description"></a>Descrição

Este serviço reatribui a tabela de fontes a utilizar pelo visor. Este serviço é normalmente invocado pela função de configuração gerada pelo GUIX Studio, mas também pode ser chamado pelo software de aplicação.

### <a name="parameters"></a>Parâmetros

- **exibir** Ponteiro para exibir bloco de controlo
- **font_table** Conjunto de GX_FONT ponteiros.
- **table_size** Número de fontes na tabela

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de tabelas de fontes bem sucedidas
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_FONT *font_table[32] = { … };

/* Assign font table */
status = gx_display_font_table_set(&my_display, font_table, 32);

/* If status is GX_SUCCESS, the font table has been reassigned. */
```

### <a name="see-also"></a>Consulte também

- gx_display_color_set
- gx_display_color_table_set
- gx_display_pixelmap_table_set

## <a name="gx_display_language_table_get"></a>gx_display_language_table_get

Recupere a tabela linguística do visor (depreciada)

### <a name="prototype"></a>Prototype

```C
UINT gx_display_language_table_get(
    GX_DISPLAY *display,
    GX_CHAR **table, 
    GX_UBYTE *language_count,
    UINT *string_table_size);
```

### <a name="description"></a>Descrição

Este serviço recupera a tabela linguística do visor indicado. Este serviço pode ser utilizado por uma aplicação para modificar a tabela de linguagem de exibição, em tempo de execução, utilizando cordas dinâmicas definidas.

Esta API é depreciada e suportada apenas para aplicações usando a antiga tabela de linguagem de estilo (ou seja, o ficheiro de recursos gerados pelo Studio é gerado para a versão da biblioteca antes da versão 5.6). As novas aplicações devem ser utilizadas gx_display_language_table_get_ext).

### <a name="parameters"></a>Parâmetros

- **exibir** Ponteiro para exibir bloco de controlo
- **tabela** Endereço para receber ponteiro de mesa
- **language_count** Endereço para receber contagem de idiomas
- **string_table_size** Endereço para receber o tamanho da tabela de cordas

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de tabelas de fontes bem sucedidas
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_CHAR **language_table;
GX_UBYTE language_count;
UINT string_count;

/* Retrieve language table */
status = gx_display_language_table_get(&my_display,
        &language_table, &language_count, &string_count);

/* If status is GX_SUCCESS, the language table has been retrieved.
```

### <a name="see-also"></a>Consulte também

- gx_display_language_table_set
- gx_display_active_langauge_set
- gx_display_string_get
- gx_display_language_table_get_ext

## <a name="gx_display_language_table_get_ext"></a>gx_display_language_table_get_ext

Recupere a tabela de linguagem de exibição

### <a name="prototype"></a>Prototype

```C
UINT gx_display_language_table_get_ext(
    GX_DISPLAY *display,
    GX_STRING **table, 
    GX_UBYTE *language_count, 
    UINT *string_table_size);
```

### <a name="description"></a>Descrição

Este serviço recupera a tabela linguística do visor indicado. Este serviço pode ser utilizado por uma aplicação para modificar a tabela de linguagem de exibição, em tempo de execução, utilizando cordas dinâmicas definidas.

### <a name="parameters"></a>Parâmetros

- **exibir** Ponteiro para exibir bloco de controlo
- **tabela** Endereço para receber ponteiro de mesa
- **language_count** Endereço para receber contagem de idiomas
- **string_table_size** Endereço para receber o tamanho da tabela de cordas

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de tabelas de fontes bem sucedidas
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_STRING **language_table;
GX_UBYTE language_count;
UINT string_count;

/* Retrieve language table */
status = gx_display_language_table_get_ext(&my_display,
    &language_table, &language_count, &string_count);

/* If status is GX_SUCCESS, the language table has been retrieved. */
```

### <a name="see-also"></a>Consulte também

- gx_display_language_table_set_ext
- gx_display_active_langauge_set
- gx_display_string_get_ext

## <a name="gx_display_language_table_set"></a>gx_display_language_table_set

Atribuir tabela de linguagem de exibição (precotado)

### <a name="prototype"></a>Prototype

```C
UINT gx_display_language_table_set(
    GX_DISPLAY *display,
    GX_CHAR **table, 
    GX_UBYTE number_of_languages, 
    UINT number_of_strings);
```

### <a name="description"></a>Descrição

Este serviço é precotado e as novas aplicações devem ser utilizadas gx_display_language_table_set_ext. Este serviço é suportado apenas para compatibilidade com os ficheiros de recursos gerados pelo Studio que visam versões da biblioteca antes da versão 5.6.

Este serviço atribui a tabela linguística a ser utilizada pelo visor. Este serviço é normalmente invocado pelo GUIX Studio gerado função gx_studio_display_configure, mas também pode ser chamado pelo software de aplicação.

### <a name="parameters"></a>Parâmetros

- **exibir** Ponteiro para exibir bloco de controlo
- **tabela** Tabela linguística
- **number_of_languages** Número de colunas na tabela fornecida
- **number_of_strings** Número de cordas em cada coluna de tabela

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de tabelas de fontes bem sucedidas
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_CHAR ***language_table= my_app_language_table;

/* Assign language table */
status = gx_display_language_table_set(&my_display, language_table,
5, 232);

/* If status is GX_SUCCESS, the language table has been reassigned. */
```

### <a name="see-also"></a>Consulte também

- gx_display_active_language_set
- gx_display_string_get

## <a name="gx_display_language_table_set_ext"></a>gx_display_language_table_set_ext

Atribuir tabela de linguagem de exibição

### <a name="prototype"></a>Prototype

```C
UINT gx_display_language_table_set_ext(
    GX_DISPLAY *display,
    GX_STRING **table, 
    GX_UBYTE number_of_languages,
    UINT number_of_strings);
```

### <a name="description"></a>Descrição

Este serviço atribui a tabela linguística a ser utilizada pelo visor. Este serviço é normalmente invocado pelo GUIX Studio gerado função gx_studio_display_configure, mas também pode ser chamado pelo software de aplicação.

A atribuição da tabela de linguagem de tempo de execução é geralmente feita quando as línguas são carregadas a partir de um ficheiro de recursos binários usando gx_binres_language_table_load().

### <a name="parameters"></a>Parâmetros

- **exibir** Ponteiro para exibir bloco de controlo
- **tabela** Tabela linguística
- **number_of_languages** Número de colunas na tabela fornecida
- **number_of_strings** Número de cordas em cada coluna de tabela

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de tabelas de fontes bem sucedidas
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_STRING_LENGTH** (0x34) Comprimento da corda inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_STRING **language_table = my_app_language_table;

/* Assign the language table */
status = gx_display_language_table_set_ext(&my_display,
    language_table, 5, 132);

/* If status is GX_SUCCESS, the language table has been reassigned. */
```

### <a name="see-also"></a>Consulte também

- gx_display_active_language_set
- gx_display_string_get

## <a name="gx_display_pixelmap_table_set"></a>gx_display_pixelmap_table_set

Atribuir tabela de fontes de exibição

### <a name="prototype"></a>Prototype

```C
UINT gx_display_pixelmap_table_set(
    GX_DISPLAY *display,
    GX_PIXELMAP **pixelmap_table, 
    INT table_size);
```

### <a name="description"></a>Descrição

Este serviço reatribui a tabela pixelmap para ser utilizada pelo visor. Este serviço é normalmente invocado pela função de configuração gerada pelo Estúdio, mas também pode ser chamado pelo software da aplicação.

### <a name="parameters"></a>Parâmetros

- **exibir** Ponteiro para exibir bloco de controlo
- **pixelmap_table** Conjunto de GX_PIXELMAP ponteiros.
- **table_size** Número de pixelmaps na tabela

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Tabela de pixels de conjunto bem sucedida
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_PIXELMAP *pixelmap_table[32] = { … };

/* Assign pixelmap table */
status = gx_display_pixelmap_table_set(&my_display, pixelmap_table, 32);

/* If status is GX_SUCCESS the pixelmap table has been reassigned. */
```

### <a name="see-also"></a>Consulte também

- gx_display_color_set
- gx_display_color_table_set
- gx_display_font_table_set

## <a name="gx_display_string_get"></a>gx_display_string_get

Recupere uma corda da tabela de cordas ativa (depreciada)

### <a name="prototype"></a>Prototype

```C
UINT gx_display_string_get(
    GX_DISPLAY *display,
    GX_RESOURCE_ID string_id, 
    GX_CONST GX_CHAR **string);
```

### <a name="description"></a>Descrição

Este serviço é precotado a favor de gx_display_string_get_ext().

Este serviço recupera uma corda da tabela de cordas ativa para o visor indicado. O idioma ativo é utilizado para selecionar a cadeia da tabela linguística atribuída ao visor.

Os IDs de cordas são gerados pelo GUIX Studio e encontram-se no ficheiro de cabeçalho recursos de aplicação.h.

### <a name="parameters"></a>Parâmetros

- **exibir** Ponteiro para exibir bloco de controlo
- **string_id** ID de corda, gerado pelo GUIX Studio.
- **cadeia** Endereço da variável do ponteiro de cordas

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Recuperação de cordas bem sucedida
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_INVALID_RESOURCE_ID** (0X33) Id de cadeia inválida
- **GX_PTR_ERROR** (0x07) Ponteiro de exibição inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_CHAR *string;

/* Retrieve string value */
status = gx_display_string_get(&my_display,
    GX_STRING_ID_MONDAY, &string);

/* If status is GX_SUCCESS, the string has been retrieved. */
```


### <a name="see-also"></a>Consulte também

- gx_display_active_language_set
- gx_display_language_table_set

## <a name="gx_display_string_get_ext"></a>gx_display_string_get_ext

Recupere uma corda da mesa de cordas ativa

### <a name="prototype"></a>Prototype

```C
UINT gx_display_string_get_ext(
    GX_DISPLAY *display,
    GX_RESOURCE_ID string_id,
    GX_STRING *string);
```

### <a name="description"></a>Descrição

Este serviço recupera uma corda da tabela de cordas ativa para o visor indicado. O idioma ativo é utilizado para selecionar a cadeia da tabela linguística atribuída ao visor.

Os IDs de cordas são gerados pelo GUIX Studio e encontram-se no ficheiro de cabeçalho recursos de aplicação.h.

### <a name="parameters"></a>Parâmetros

- **exibir** Ponteiro para exibir bloco de controlo
- **string_id** ID de corda, gerado pelo GUIX Studio.
- **cadeia** Endereço de GX_STRING variável em
- **que** string.gx_string_ptr e
- **string.gx_string_length** será devolvido.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Recuperação de cordas bem sucedida
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_INVALID_RESOURCE_ID** (0X33) Id de cadeia inválida
- **GX_PTR_ERROR** (0x07) Ponteiro de exibição inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_STRING string;

/* Retrieve string value */
status = gx_display_string_get_ext(&my_display,
    GX_STRING_ID_MONDAY, &string);

/* If status is GX_SUCCESS, the string has been retrieved. */
```

### <a name="see-also"></a>Consulte também

- gx_display_active_language_set
- gx_display_language_table_set


## <a name="gx_display_string_table_get"></a>gx_display_string_table_get


Recupere a tabela de cordas ativa (depreciada)

### <a name="prototype"></a>Prototype

```C
UINT gx_display_string_table_get(
    GX_DISPLAY *display,
    GX_UBYTE language, 
    GX_CHAR ***table,
    UINT *table_size);
```

### <a name="description"></a>Descrição

Este serviço é precotado e substituído por gx_display_string_table_get_ext().

Este serviço recupera a tabela de cordas associada à linguagem ativa. Este serviço não é frequentemente utilizado, mas é fornecido para a completude para as aplicações que podem precisar de fazer modificações de tempo de execução na tabela de cordas.

### <a name="parameters"></a>Parâmetros

- **exibir** Ponteiro para exibir bloco de controlo
- **língua** Coluna de mesa para recuperar.
- **tabela** Endereço de variável para ponter de retorno.
- **table_size** Endereço de variável para devolver tamanho da tabela

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de tabelas de fontes bem sucedidas
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_NOT_FOUND** (0x09) Índice linguístico inválido
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_CHAR **string_table;
UINT table_size;

/* Retrieve string table */
status = gx_display_string_table_get(&my_display, LANGUAGE_ENGLISH,
    &string_table, &table_size);

/* If status is GX_SUCCESS, the string table has been retrieved. */
```

### <a name="see-also"></a>Consulte também

- gx_display_color_set
- gx_display_color_table_set
- gx_display_pixelmap_table_set

## <a name="gx_display_string_table_get_ext"></a>gx_display_string_table_get_ext


Recupere a tabela de cordas ativa

### <a name="prototype"></a>Prototype

```C
UINT gx_display_string_table_get(
    GX_DISPLAY *display,
    GX_UBYTE language, 
    GX_STRING **table, 
    UINT *table_size);
```

### <a name="description"></a>Descrição

Este serviço recupera a tabela de cordas associada à linguagem ativa. Este serviço não é frequentemente utilizado, mas é fornecido para a completude para as aplicações que podem precisar de fazer modificações de tempo de execução na tabela de cordas.

### <a name="parameters"></a>Parâmetros

- **exibir** Ponteiro para exibir bloco de controlo
- **língua** Coluna de mesa para recuperar.
- **tabela** Endereço de variável para ponter de retorno.
- **table_size** Endereço de variável para devolver tamanho da tabela

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de tabelas de fontes bem sucedidas
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_NOT_FOUND** (0x09) Índice linguístico inválido
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_STRING *string_table;
UINT table_size;

/* Retrieve string table */
status = gx_display_string_table_get_ext(&my_display,
    LANGUAGE_ENGLISH, &string_table, &table_size);

/* If status is GX_SUCCESS, the string table has been retrieved. */
```

### <a name="see-also"></a>Consulte também

- gx_display_color_set
- gx_display_color_table_set
- gx_display_pixelmap_table_set

## <a name="gx_display_theme_install"></a>gx_display_theme_install


Instale temas no visor especificado

### <a name="prototype"></a>Prototype

```C
UINT gx_display_theme_install(
    GX_DISPLAY *display, 
    GX_THEME *theme_table);
```

### <a name="description"></a>Descrição

Este serviço instala temas para o visor especificado. Este serviço é normalmente invocado pela função de configuração gerada pelo Estúdio, mas também pode ser chamado pelo software da aplicação.

### <a name="parameters"></a>Parâmetros

- **exibir** Ponteiro para exibir bloco de controlo
- **theme_table** Tabela temática a instalar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Tabela temática instalada com sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro de tabela temática inválida
- **GX_INVALID_DISPLAY** (0x1D) Exibição inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_THEME theme_1;

&theme_table[1] = {
    &theme_1,
    …
}

/* Define resource tables. */
GX_COLOR color_table[32] = {…};
GX_FONT *font_table[32] = {…};
GX_PIXELMAP *pixelmap_table[32] = { … };

/* Define scroll appearance. */
GX_SCROLLBAR_APPEARANCE scroll_appearance;

memset(&scroll_appearance, 0, sizeof(GX_SCROLLBAR_APPEARANCE));

scroll_appearance.gx_scroll_width = 20;
scroll_appearance.gx_scroll_thumb_width = 18;
scroll_appearance.gx_scroll_thumb_color =
    GX_COLOR_ID_SCROLL_BUTTON;
scroll_appearance.gx_scroll_thumb_border_color =
    GX_COLOR_ID_SCROLL_BUTTON;
scroll_appearance.gx_scroll_button_color =
    GX_COLOR_ID_SCROLL_BUTTON;
scroll_appearance.gx_scroll_thumb_travel_min = 20;
scroll_appearance.gx_scroll_thumb_travel_max = 20;
scroll appearance.gx_scroll_thumb_border_style =
    GX_STYLE_BORDER_THIN;

theme_1.theme_color_table = color_table;
theme_1.theme_font_table = font_table;
theme_1.theme_pixlemap_table = pixelmap_table;
theme_1.theme_palette = GX_NULL;
theme_1.theme_vertical_scrollbar_appearance = scroll_appearance;
theme_1.theme_horizontal_scrollbar_appearance = scroll_appearance;
theme_1.theme_vertical_scroll_style = GX_SCROLLBAR_RELATIVE_THUMB;
theme_1.theme_horizontal_scroll_style =
    GX_SCROLLBAR_RELATIVE_THUMB;
theme_1.theme_color_table_size = 32;
theme_1.theme_font_table_size = 32;
theme_1.theme_pixelmap_table_size = 32;
theme_1.theme_palette_size = 0;

/* Install theme table. */
status = gx_display_theme_install(&my_display, theme_table);

/* If status is GX_SUCCESS the theme table has been installed. */
```

### <a name="see-also"></a>Consulte também

- gx_display_color_set
- gx_display_color_table_set
- gx_display_font_table_set

## <a name="gx_drop_list_close"></a>gx_drop_list_close


Feche uma lista de entrega

### <a name="prototype"></a>Prototype

```C
UINT gx_drop_list_close(GX_DROP_LIST *drop_list);
```

### <a name="description"></a>Descrição

Este serviço fecha a lista popup da lista de lançamentos especificada.

### <a name="parameters"></a>Parâmetros

- **drop_list** Ponteiro para o bloco de controlo da lista de lançamento

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Com sucesso fechou a lista de entrega
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Close a drop list. */
status = gx_drop_list_close(&drop_list);

/* If status is GX_SUCCESS, the drop list is closed. */
```

### <a name="see-also"></a>Consulte também

- gx_drop_list_create
- gx_drop_list_event_process
- gx_drop_list_open

gx_drop_list_pixelmap_set, gx_drop_list_popup_get

## <a name="gx_drop_list_create"></a>gx_drop_list_create


Criar uma lista de lançamentos

### <a name="prototype"></a>Prototype

```C
UINT gx_drop_list_create(
    GX_DROP_LIST *drop_list, 
    GX_CONST
    GX_CHAR *name, 
    GX_WIDGET *parent,
    INT total_rows, 
    INT open_height,
    VOID (*callback)(GX_VERTICAL_LIST *, 
    GX_WIDGET *, INT),
    ULONG style, 
    USHORT drop_list_id,
    GX_CONST GX_RECTANGLE *size)
```

### <a name="description"></a>Descrição

Este serviço cria uma lista de entrega. Uma lista de drop é uma combinação do widget da lista de lançamento, e uma lista vertical pop-up que é exibida quando a lista de lançamento é aberta. A lista vertical popup é criada automaticamente quando o widget da lista de lançamento é criado, e exibido ou escondido quando o widget da lista de lançamento é aberto ou fechado, respectivamente.

O widget da lista de lançamento suporta dois pixelmaps associados. O primeiro, descrito como "List Wallpaper" na vista de propriedades do Estúdio, é o mapa de pixels de papel de parede opcional que é apresentado como o fundo da lista vertical que é exibido quando o widget da lista de lançamento é aberto. O segundo pixelmap, descrito como "Background Image" na vista de propriedades do Estúdio, é uma imagem opcional exibida como o fundo da própria lista de lançamentos.

Um widget de lista de lançamento pode ter (mas não é necessário ter) um widget para crianças que é usado para abrir e fechar a lista de drop. Este é habitualmente um widget de ícone ou botão, mas até mesmo um widget personalizado poderia ser usado como o toggle aberto/próximo para a lista de drop dos pais. A definição de chave que faz com que este widget infantil opere a lista de gotas é que este widget infantil deve ter o widget id pré-definido ID_DROP_LIST_BUTTON.

Para definir um widget para crianças que abrirá e fechará a lista de entrega, primeiro-ad e widget infantil para a lista de gotas, e posicionar esta criança dentro da lista de entregas como desejado:

![Screenshot da lista de lançamentos.](./media/guix/image6.jpg)

Em seguida, use a vista propriedades do Estúdio para atribuir a este widget o valor de ID ID_DROP_LIST_BUTTON, que é um valor de ID definido internamente reconhecido pela lista de drop dos pais:

![Screenshot da vista das propriedades do Estúdio.](./media/guix/image7.jpg)

### <a name="parameters"></a>Parâmetros
- **drop_list** Ponteiro para o bloco de controlo da lista de lançamento
- **nome** Nome da lista de entrega
- **pai** Ponteiro para o widget dos pais
- **total_rows** Número total de linhas na lista de lançamentos
- **open_height** A altura da lista vertical apresentada quando a lista de lançamentos é aberta.
- **callback** Função chamada pela lista vertical quando a lista é deslocalizada. Consulte a documentação da GX_VERTICAL_LIST para obter mais informações.
- **estilo** O estilo de fronteira da lista de drop-down.
- **drop_list_id** ID definido pela aplicação da lista de entrega
- **tamanho** Dimensões da lista de lançamentos

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Lista de lançamentos bem sucedidas criar
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_DROP_LIST my_drop_list;
VOID list_row_create(GX_VERTICAL_LIST *list,
                     GX_WIDGET *row, INT index);
{
    …
}

GX_RECTANGLE size;

gx_utility_rectangle_define(&size, 10, 10, 80, 40);

status = gx_drop_list_create(&my_drop_list,
    "my drop list", GX_NULL,
    10, 100, list_row_create,
    GX_STYLE_BORDER_RECESSED | GX_STYLE_ENABLED,
    ID_DROP_LIST, &size)

/* Is status is GX_SUCCESS, the drop list was successfully created. */
```

### <a name="see-also"></a>Consulte também:

- gx_drop_list_close
- gx_drop_list_event_process
- gx_drop_list_open
- gx_drop_list_pixelmap_set
- gx_drop_list_popup_get

## <a name="gx_drop_list_event_process"></a>gx_drop_list_event_process


Evento de lista de drop de processo

### <a name="prototype"></a>Prototype

```C
UINT gx_drop_list_event_process(
    GX_DROP_LIST *list, 
    GX_EVENT *event);
```

### <a name="description"></a>Descrição

Este serviço processa um evento para a lista de entrega.

### <a name="parameters"></a>Parâmetros

- **drop_list** Bloco de controlo widget de lista de lançamento
- **evento** Ponteiro para o evento para processar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) evento de lista de entrega processado com sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Call generic drop list event processing as part of custom event processing function. */

UINT custom_drop_list_event_process(GX_DROP_LIST *drop_list,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default drop list
            event processing */
        status = gx_drop_list_event_process(drop_list, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Consulte também

- gx_drop_list_close
- gx_drop_list_create
- gx_drop_list_open
- gx_drop_list_pixelmap_set
- gx_drop_list_popup_get

## <a name="gx_drop_list_open"></a>gx_drop_list_open


Abrir uma lista de lançamentos

### <a name="prototype"></a>Prototype

```C
UINT gx_drop_list_open(GX_DROP_LIST *drop_list);
```

### <a name="description"></a>Descrição

Este serviço abre uma lista de drop previamente criada.

### <a name="parameters"></a>Parâmetros

- **drop_list** Ponteiro para o bloco de controlo da lista de lançamento

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Lista de lançamentos bem sucedidas criar
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_DROP_LIST mylist;

/* Open the popup list of “mylist”. */
status = gx_drop_list_open(&mylist);

/* If status == GX_SUCCESS, the popup list of “mylist” has been displayed. */
```

### <a name="see-also"></a>Consulte também

- gx_drop_list_close
- gx_drop_list_create
- gx_drop_list_event_process
- gx_drop_list_pixelmap_set
- gx_drop_list_popup_get

## <a name="gx_drop_list_pixelmap_set"></a>gx_drop_list_pixelmap_set


Atribua uma imagem de fundo à lista de lançamentos

### <a name="prototype"></a>Prototype

```C
UINT gx_drop_list_pixelmap_set(
    GX_DROP_LIST *drop_list,
    GX_RESOURCE_ID id);
```

### <a name="description"></a>Descrição

Atribua uma imagem de fundo à lista de lançamentos. Este pixelmap é usado como pano de fundo para o próprio widget da lista de lançamento, e não para a lista vertical popup que é apresentada quando a lista é aberta. Para atribuir um pixelmap ao pop-up da lista de lançamento, você precisaria primeiro ligar para gx_drop_list_popup_get para recuperar um ponteiro para a lista pop-up e, em seguida, usar gx_window_wallpaper_set() para atribuir um pixelmap a esta lista pop-up.

### <a name="parameters"></a>Parâmetros

- **drop_list** Ponteiro para o bloco de controlo da lista de lançamento
- **ID** ID para o pixlemap

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de pixelmaps de lista de lançamento bem-sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_RESOURCE_ID** (0x33) ID pixlemap inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_DROP_LIST mylist;

/* create the drop list here */

/* Assign a pixelmap id, which will turn on the list button */
status = gx_drop_list_pixelmap_set(&mylist,
    GX_PIXELMAP_ID_DROP_LIST_BACKGROND);

/* If status is GX_SUCCESS, the pixelmap was successfully set. */
```

### <a name="see-also"></a>Consulte também:

- gx_drop_list_close
- gx_drop_list_create
- gx_drop_list_event_process
- gx_drop_list_open
- gx_drop_list_popup_get

## <a name="gx_drop_list_popup_get"></a>gx_drop_list_popup_get


Recupere o ponteiro para a lista vertical popup

### <a name="prototype"></a>Prototype

```C
UINT gx_drop_list_popup_get(
    GX_DROP_LIST *drop_list,
    GX_VERTICAL_LIST **return_list);
```

### <a name="description"></a>Descrição

Um widget drop-list é composto pelo widget drop-list em si, e uma lista vertical pop-up que é mostrada quando o widget da lista de lançamento é aberto. Este serviço recupera um ponteiro para o componente de lista vertical da lista de entrega, permitindo que a aplicação invoque serviços API diretamente nesta lista vertical.

### <a name="parameters"></a>Parâmetros

- **drop_list** Ponteiro para o bloco de controlo da lista de lançamento
- **return_list** Ponteiro para a lista vertical armazenada na lista de entrega

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) recuperou com sucesso a lista vertical pop-up
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_DROP_LIST drop_list;
GX_VERTICAL_LIST *vertical_list;

/* Retrieve the popup list of “drop_list”. */
status = gx_drop_list_popup_get(&drop_list, &vertical_list)

/* If status is GX_SUCCESS, the popup list was successfully retrieved. */
```

### <a name="see-also"></a>Consulte também:

- gx_drop_list_close
- gx_drop_list_create
- gx_drop_list_open
- gx_drop_list_pixelmap_set

## <a name="gx_horizontal_list_children_position"></a>gx_horizontal_list_children_position


Posicione as crianças para a lista horizontal

### <a name="prototype"></a>Prototype

```C
UINT gx_horizontal_list_children_position(GX_HORIZONTAL_LIST *horizontal_list);
```

### <a name="description"></a>Descrição

Esta função posiciona as crianças para a lista horizontal. Esta função é chamada automaticamente quando a lista recebe o evento GX_EVENT_SHOW, mas deve ser chamada diretamente se a lista for modificada depois de ter sido tornada visível.

### <a name="parameters"></a>Parâmetros

- **horizontal_list** Ponteiro para o bloco de controlo da lista horizontal

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Bem-sucedido posicionou as crianças para a lista horizontal
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Position children in the horizontal list */
status = gx_horizontal_list_children_position (&horizontal_list);

/* If status is GX_SUCCESS the children in the horizontal list are positioned. */
```

### <a name="see-also"></a>Consulte também

- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_create"></a>gx_horizontal_list_create


Criar lista horizontal

### <a name="prototype"></a>Prototype

```C
UINT gx_horizontal_list_create(
    GX_HORIZONTAL_LIST *horizontal_list,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent,
    INT total_columns,
    VOID (*callback)(GX_HORIZONTAL_LIST *, 
    GX_WIDGET *, INT),
    ULONG style, 
    USHORT horizontal_list_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria uma lista horizontal.

### <a name="parameters"></a>Parâmetros

- **horizontal_list** Bloco de controlo widget de lista horizontal
- **nome** Nome da lista horizontal
- **pai** Ponteiro para widget dos pais
- **total_columns** Número total de comum na lista horizontal
- **callback** Este é um ponteiro para uma função de retorno fornecido pela aplicação. A função de retorno é invocada quando a lista horizontal é deslocalizada, para criar os itens de lista recém-visíveis. Desta forma, a lista horizontal pode apresentar qualquer tipo de widget definido pelo utilizador como os itens da lista.
- **estilo** Estilo de widget de barra de rolo. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **horizontal_list_id** ID definido pela aplicação da lista horizontal
- **tamanho** Dimensões da lista horitzonal

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) criou com sucesso a lista horizontal
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido
- **GX_INVALID_VALUE** (0x22) Número de colunas não válidas

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Create horizontal list “my_list” with 5 columns. */
status = gx_horizontal_list_create(&my_list, “my_list”, &my_parent,
    5, callback, GX_STYLE_WRAP, MY_LIST_ID, &size);

/* If status is GX_SUCCESS the horizontal list “my_list” has been created. */
```

### <a name="see-also"></a>Consulte também

- gx_horizontal_list_children_position
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_event_process"></a>gx_horizontal_list_event_process


Evento de lista horizontal de processo

### <a name="prototype"></a>Prototype

```C
UINT gx_horizontal_list_event_process(
    GX_HORIZONTAL_LIST *list,
    GX_EVENT *event);
```

### <a name="description"></a>Descrição

Este serviço processa um evento para a lista horizontal.

### <a name="parameters"></a>Parâmetros

- **lista** Bloco de controlo widget de lista horizontal
- **evento** Ponteiro para o evento para processar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Evento de lista horizontal processada com sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Call generic horizontal list event processing as part of custom event processing function. */

UINT custom_list_event_process(
    GX_HORIZONTAL_LIST *list,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default horizontal
        list event processing */
        status =
        gx_horizontal_list_event_process(list, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Consulte também

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_page_index_set"></a>gx_horizontal_list_page_index_set


Definir índice de página inicial

### <a name="prototype"></a>Prototype

```C
UINT gx_horizontal_list_page_index_set(
    GX_HORIZONTAL_LIST *list,
    INT *index);
```

### <a name="description"></a>Descrição

Este serviço define o índice inicial para a lista horizontal.

### <a name="parameters"></a>Parâmetros

- **lista** Bloco de controlo widget de lista horizontal
- **índice** O novo índice superior

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso o índice de página inicial para a lista horizontal
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_VALUE** (0x22) Valor inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Sets the starting page index of horizontal list “my_list” as 1. */
status = gx_horizontal_list_page_index_set(&my_list, 1);

/* If status is GX_SUCCESS the starting page index of “my_list” has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_selected_index_get"></a>gx_horizontal_list_selected_index_get


Obtenha o índice de entrada selecionado da lista horizontal

### <a name="prototype"></a>Prototype

```C
UINT gx_horizontal_list_selected_index_get(
    GX_horizobntal_LIST *horizontal_list,
    INT *return_index);
```

### <a name="description"></a>Descrição

Este serviço devolve o índice de inscrição da lista selecionada da lista horizontal.

### <a name="parameters"></a>Parâmetros

- **horizontal_list** Bloco de controlo widget de lista horizontal
- **return_index** Destino para índice de lista de devolução

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Com sucesso obteve a entrada na lista horizontal
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
INT current_index_entry;

/* Get the list entry at the current index of horizontal list “my_list”. */
status = gx_horizontal_list_selected_index_get(&my_list,
    &current_index_entry);

/* If status is GX_SUCCESS, “current_index_entry” contains the current list selection index. */
```

### <a name="see-also"></a>Consulte também

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_selected_set"></a>gx_horizontal_list_selected_set


Atribuir a entrada selecionada numa lista horizontal

### <a name="prototype"></a>Prototype

```C
UINT gx_horizontal_list_selected_set(
    GX_HORIZONATAL_LIST *horizontal_list,
    INT index);
```

### <a name="description"></a>Descrição

Este serviço atribui a entrada selecionada numa lista horizontal. Se necessário, a lista horizontal deslocar-se-á para tornar visível a entrada selecionada.

### <a name="parameters"></a>Parâmetros

- **horizontal_list** Bloco de controlo widget de lista horizontal
- **índice** Posição baseada no índice da entrada de nova lista

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso a entrada da lista horizontal
- **GX_FAILURE** (0x10) Index não está na gama inválida
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the list entry of “my_list” to the child in line 12. */
status = gx_horizontal_list_selected_set(&my_list, 12);

/* If status is GX_SUCCESS, the list entry of “my_list” has been successfully set to 12. */
```

### <a name="see-also"></a>Consulte também

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_selected_widget_get"></a>gx_horizontal_list_selected_widget_get


Obtenha a entrada selecionada da lista horizontal

### <a name="prototype"></a>Prototype

```C
UINT gx_horizontal_list_selected_widget_get(
    GX_horizobntal_LIST *horizontal_list,
    GX_WIDGET **return_list_entry);
```

### <a name="description"></a>Descrição

Este serviço devolve a inscrição da lista selecionada da lista horizontal. Note que se a lista horizontal tiver mais linhas do que widgets infantis, e a entrada selecionada tiver sido deslocada da vista, esta API voltará GX_NULL porque os widgets para crianças são reutilizados à medida que o conteúdo da lista é deslocalizado. A função gx_horizontal_list_selected_index_get devolverá de forma fiável o índice do item selecionado, mesmo que esse item tenha sido deslocalizado da vista.

### <a name="parameters"></a>Parâmetros

- **horizontal_list** Bloco de controlo widget de lista horizontal
- **return_list_entry** Destino para widget de entrada na lista de devolução

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Com sucesso obteve a entrada na lista horizontal
- **GX_FAILURE** (0x10) O widget selecionado foi percalizado de vista numa lista com mais linhas do que crianças clientes.
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Get the list entry at the current index of horizontal list “my_list”. */
status = gx_horizontal_list_selected_widget_get(&my_list, &current_list_entry);

/* If status is GX_SUCCESS, “current_list_entry” contains a pointer to the currently selected widget. */

    
```

### <a name="see-also"></a>Consulte também

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_total_columns_set"></a>gx_horizontal_list_total_columns_set


Atribuir o número total de colunas de listas

### <a name="prototype"></a>Prototype

```C
UINT gx_horizontal_list_total_columns_set(
    GX_HORIZONTAL_LIST *horizontal_list,
    INT count);
```

### <a name="description"></a>Descrição

Este serviço atribui o número total de colunas a visualizar pela lista horizontal.

### <a name="parameters"></a>Parâmetros

- **horizontal_list** Bloco de controlo widget de lista horizontal
- **contar** Número de colunas para exibir

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Contagem de colunas atribuídas com sucesso
- **GX_CALLER_ERROR** (0x10) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_VALUE** (0x22) Valor da contagem inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Tell my list to display 20 total columns. */
status = gx_horizontal_list_total_columns_set(&my_list, 20);

/* If status is GX_SUCCESS, the total colums of “my_list” was successfully set to 20. */
```

### <a name="see-also"></a>Consulte também

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set

## <a name="gx_horizontal_scrollbar_create"></a>gx_horizontal_scrollbar_create


Criar barra de deslocação horizontal

### <a name="prototype"></a>Prototype

```C
UINT gx_horizontal_scrollbar_create(
    GX_SCROLLBAR *scrollbar,
    GX_CONST GX_CHAR *name,
    GX_WINDOW *parent,
    GX_SCROLLBAR_APPEARANCE *appearance ULONG style);
```

### <a name="description"></a>Descrição

Este serviço cria uma barra de deslocação horizontal. O ID para uma barra de deslocamento horizontal é pré-definido (porque uma janela tem de saber como apanhar eventos a partir dele), e o tamanho é automático (porque tem de preencher a largura do cliente da janela dos pais). Se decidirmos permitir as barras de deslocamento da área do cliente, teremos de adicionar outra função de criação com os parâmetros de id e tamanho.

### <a name="parameters"></a>Parâmetros

- **barra de scroll** Bloco de controlo widget de barra de rolo
- **nome** Nome da barra de pergaminho
- **pai** Ponteiro para widget dos pais
- **aparência** A estrutura de aparência define o aparecimento da barra de pergaminho. Se este valor for GX_NULL, a barra de deslocação utilizará a aparência padrão da barra de deslocação definida por gx_system_scroll_appearance_get. Consulte o **Apêndice I** para a definição da estrutura GX_SCROLLBAR_APPEARANCE.
- **Estilo** Estilo de widget de barra de rolo. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Barra de deslocação horizontal bem sucedida criar
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Create horizontal scrollbar “my_scrollbar”. */
status = gx_horizontal_scrollbar_create(&my_scrollbar,
    “my_horizontal_scrollbar”, &my_parent, GX_NULL,
    GX_STYLE_SCROLLBAR_END_BUTTONS);

/* If status is GX_SUCCESS the horizontal scrollbar “my_scrollbar” has been created. */
```

### <a name="see-also"></a>Consulte também

- gx_scrollbar_draw
- gx_scrollbar_event_process
- gx_scrollbar_limit_check
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_icon_button_create"></a>gx_icon_button_create


Criar botão de ícone

### <a name="prototype"></a>Prototype

```C
UINT gx_icon_button_create(
    GX_ICON_BUTTON *button,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent,
    GX_RESOURCE_ID icon_id,
    ULONG style,
    USHORT icon_button_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria o widget de botão de ícone especificado.

GX_ICON_BUTTON é derivado de GX_BUTTON e suporta todos os gx_button serviços da API.

### <a name="parameters"></a>Parâmetros

- **botão** Ponteiro para bloco de controlo de botões de ícone
- **nome** Nome lógico do widget do botão do ícone
- **pai** Ponteiro para o widget dos pais
- **icon_id** ID de recurso do ícone
- **estilo** Estilo de ícone. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **icon_button_id** ID definido pela aplicação do botão de ícone
- **tamanho** Dimensões do botão de ícone

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) criou com sucesso o botão de ícone
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Create “my_icon_button”. */
status = gx_icon_button_create(&my_icon_button, “my_icon_button”,
    &my_parent,
    MY_ICON_RESOURCE_ID, GX_STYLE_BORDER_RAISED, MY_ICON_BUTTON_ID,
    &size);

/* If status is GX_SUCCESS the icon button “my_icon_button” has been created. */
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_create
- gx_icon_draw
- gx_icon_pixelmap_set
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_radio_button_create
- gx_radio_button_draw gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_icon_button_draw"></a>gx_icon_button_draw


Desenhe um botão de ícone

### <a name="prototype"></a>Prototype

```C
VOID gx_icon_button_draw(GX_ICON_BUTTON *button);
```

### <a name="description"></a>Descrição

Este serviço desenha o botão de ícone. Esta função é normalmente chamada internamente pelo GUIX como parte de uma operação de atualização de tela, mas também exposta à aplicação que pode querer fornecer uma função de desenho personalizado e invocar o desenho do botão de ícone padrão como base de desenho personalizado.

### <a name="parameters"></a>Parâmetros

- **botão** Ponteiro para bloco de controlo de botões de ícone

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom icon draw function. */
void MyIconButtonDraw(GX_ICON_BUTTON *button)
{
    /* Do the normal drawing first */
    gx_icon_button_draw(button);

    /* Add custom drawing here */
}
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_create
- gx_icon_draw
- gx_icon_pixelmap_set
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_radio_button_create
- gx_radio_button_draw gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_icon_button_pixelmap_set"></a>gx_icon_button_pixelmap_set


Desajuste do pixelmap ao widget do botão do ícone

### <a name="prototype"></a>Prototype

```C
UINT gx_icon_button_pixelmap_set(
    GX_ICON_BUTTON *button,
    GX_RESOURCE_ID icon_id);
```

### <a name="description"></a>Descrição

Este serviço atribui um novo pixelmap ao widget do botão de ícone.

### <a name="parameters"></a>Parâmetros

- **botão** Ponteiro para bloco de controlo de botões de ícone
- **icon_id** ID de recursos de pixelmap

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso o pixelmap do botão do ícone
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set pixelmap for “my_icon_button”. */
status = gx_icon_button_pixelmap_set(&my_icon_button,
    GX_PIXELMAP_ID_ICON);

/* If status is GX_SUCCESS, the pixelmap of the icon button “my_icon_button” has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_create
- gx_icon_draw
- gx_icon_pixelmap_set
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_radio_button_create
- gx_radio_button_draw gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_icon_background_draw"></a>gx_icon_background_draw


Desenhar fundo de ícone

### <a name="prototype"></a>Prototype

```C
VOID gx_icon_background_draw(GX_ICON *icon);
```

### <a name="description"></a>Descrição

Este serviço desenha o fundo do widget de ícone especificado. Este serviço é normalmente chamado internamente pela função gx_icon_button_draw, mas está exposto à aplicação para ajudar a escrever funções de desenho personalizado.

### <a name="parameters"></a>Parâmetros

- **ícone** Ponteiro para bloco de controlo widget de ícone

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Write a custom icon draw function. */
void MyIconButtonDraw(GX_ICON *icon)
{
    /* Call icon background draw. */
    gx_icon_background_draw(icon);

    /* Add custom drawing here */

    /* Draw child widgets. */
    gx_widget_children_draw(icon);
}
```

### <a name="see-also"></a>Consulte também

- gx_icon_create
- gx_icon_draw
- gx_icon_event_process
- gx_icon_pixelmap_set

## <a name="gx_icon_create"></a>gx_icon_create


ícone Criar

### <a name="prototype"></a>Prototype

```C
UINT gx_icon_create(
    GX_ICON *icon, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID pixelmap_id, 
    ULONG style,
    USHORT icon_id, 
    GX_VALUE x, 
    GX_VALUE y);
```

### <a name="description"></a>Descrição

Este serviço cria o widget de ícone especificado.

### <a name="parameters"></a>Parâmetros

- **ícone** Ponteiro para bloco de controlo de ícones
- **nome** Nome lógico do widget de ícone
- **pai** Ponteiro para o widget dos pais
- **pixelmap_id** ID de recursos de pixelmap
- **estilo** Estilo de ícone
- **icon_id** ID definido pela aplicação do ícone
- **x** Posição de coordenação x inicial
- **y posição** de arranque y-coordenada

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Ícone de sucesso criar
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Create “my_icon”. */
status = gx_icon_create(&my_icon, “my_icon”, &my_parent,
    MY_PIXELMAP_RESOURCE_ID, GX_STYLE_BORDER_RAISED, MY_ICON_ID,
    5, 30);

/* If status is GX_SUCCESS the icon “my_icon” has been created. */
```

### <a name="see-also"></a>Consulte também

- gx_icon_button_create
- gx_icon_draw
- gx_icon_pixelmap_set

## <a name="gx_icon_draw"></a>gx_icon_draw


Desenhar ícone

### <a name="prototype"></a>Prototype

```C
VOID gx_icon_draw(GX_ICON *icon);
```

### <a name="description"></a>Descrição

Este serviço desenha o widget de ícone especificado. Este serviço é normalmente chamado internamente pelo GUIX como parte de uma operação de atualização de tela, mas também exposto à aplicação que pode querer fornecer uma função de desenho personalizado e invocar o desenho de ícone padrão como base de desenho personalizado.

### <a name="parameters"></a>Parâmetros

- **ícone** Ponteiro para bloco de controlo widget de ícone

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom icon drawing function. */

VOID my_icon_draw(GX_MENU *menu)
{
    /* Call default icon draw. */
    gx_icon_draw(menu);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_icon_button_create
- gx_icon_create
- gx_icon_pixelmap_set

## <a name="gx_icon_event_process"></a>gx_icon_event_process

Processamento de eventos de widget de ícone

### <a name="prototype"></a>Prototype

```C
UINT gx_icon_event_process(
    GX_ICON *icon, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Descrição

Este serviço trata dos eventos enviados para um widget GX_ICON.

### <a name="parameters"></a>Parâmetros

- **ícone** Ponteiro para bloco de controlo widget de ícone
- **event_ptr** Ponteiro para GX_EVENT estrutura

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Evento de ícone processado bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
switch(event_ptr->gx_event_type)
{
case GX_EVENT_SHOW:
    /* Do default handling. */
    status = gx_icon_event_process(icon, event_ptr);

    /* add your own handling here */
    break;
}
```

### <a name="see-also"></a>Consulte também

- gx_icon_button_create
- gx_icon_create
- gx_icon_pixelmap_set

## <a name="gx_icon_pixelmap_set"></a>gx_icon_pixelmap_set


Definir pixelmap para ícone

### <a name="prototype"></a>Prototype

```C
UINT gx_icon_pixelmap_set(
    GX_ICON *icon, 
    GX_RESOURCE_ID normal_id,
    GX_RESOURCE_ID selected_id);
```

### <a name="description"></a>Descrição

Este serviço define o mapa de pixels para o widget de ícone especificado.

### <a name="parameters"></a>Parâmetros

- **ícone** Ponteiro para bloco de controlo widget de ícone
- **normal_id** ID de recursos do estado normal
- **selected_id** ID de recursos do estado selecionado

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de pixels de ícone de sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set pixelmap for “my_icon”. */
status = gx_icon_pixelmap_set(&my_icon,
    MY_NOT_SELECTED_RESOURCE_ID,
    MY_SELECTED_ID);

/* If status is GX_SUCCESS, the icon “my_icon” has a pixelmap set. */
```

### <a name="see-also"></a>Consulte também

- gx_icon_button_create
- gx_icon_create
- gx_icon_draw

## <a name="gx_image_reader_create"></a>gx_image_reader_create


Criar exemplo de módulo de leitor de imagem

### <a name="prototype"></a>Prototype

```C
UINT gx_image_reader_create(
    GX_IMAGE_READER *image_reader,
    GX_CONST GX_UBYTE *data, 
    INT data_size,
    GX_UBYTE color_format, 
    GX_UBYTE mode);
```

### <a name="description"></a>Descrição

Esta função cria um leitor de imagem/descodificador de imagem em bruto. Atualmente apenas os tipos de imagem em bruto jpeg e png são suportados. Este serviço requer GX_SOFTWARE_DECODER_SUPPORT para ser definido.

### <a name="parameters"></a>Parâmetros

- **image_reader** Bloco de controlo do leitor de imagem
- **dados** Ponteiro para dados de entrada bruta.
- **data_size** Tamanho dos dados brutos de entrada.
- **color_format** O formato de cor de saída solicitado.
- **modo** Compress, dither e alfa modes bandeiras.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Leitor de imagem bem sucedido cria
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_VALUE** (0x22) Tamanho dos dados inválidos

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e Threads

### <a name="example"></a>Exemplo

```C
GX_IMAGE_READER my_image_reader;

“color format” could be set to:
    GX_COLOR_FORMAT_32ARGB
    GX_COLOR_FORMAT_24RGB
    GX_COLOR_FORMAT_565RGB
    GX_COLOR_FORMAT_8BIT_PALETTE

/* Create image reader “my_image_reader”. */
status = gx_image_reader_create(&my_image_reader, decoder_data,
    decoder_data_size,
    GX_COLOR_FORMAT_32ARGB,
    GX_IMAGE_READER_MODE_COMPRESS)

/* If status is GX_SUCCESS, “my_image_reader” has been successfully created. */
```

### <a name="see-also"></a>Consulte também

- gx_image_reader_start
- gx_image_reader_palette_set

## <a name="gx_image_reader_palette_set"></a>gx_image_reader_palette_set


Definir paleta de leitor de imagem

### <a name="prototype"></a>Prototype

```C
UINT gx_image_reader_palette_set(
    GX_IMAGE_READER *image_reader,
    GX_COLOR *pal,
    UINT palsize);
```

### <a name="description"></a>Descrição

Este serviço define paleta para o bloco de controlo do leitor de imagem. Este serviço requer GX_SOFTWARE_DECODER_SUPPORT para ser definido.

### <a name="parameters"></a>Parâmetros

- **image_reader** Bloco de controlo do leitor de imagem
- **amigo** Ponteiro para paleta
- **palesize** O tamanho da paleta

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de paleta de leitor de imagem bem-sucedida
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_VALUE** (0x22) Tamanho da paleta inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e Threads

### <a name="example"></a>Exemplo

```C
/* Set “my_palette” as the palette of “my_image_reader”. */
status = gx_image_reader_palette_set(&my_image_reader, my_palette,
    my_palette_size);

/* If status is GX_SUCCESS the palette of “my_image_reader” has been set to “my_palette”. */
```

### <a name="see-also"></a>Consulte também

- gx_image_reader_create
- gx_image_reader_start

## <a name="gx_image_reader_start"></a>gx_image_reader_start

Inicie o processo de descompressão e conversão

### <a name="prototype"></a>Prototype

```C
UINT gx_image_reader_start(
    GX_IMAGE_READER *image_reader, 
    GX_PIXELMAP *outmap);
```

### <a name="description"></a>Descrição

Este serviço descodifica uma imagem em bruto para um formato de cor especificado. Atualmente apenas os tipos de imagem em bruto jpeg e png são suportados. Isto requer que GX_SOFTWARE_DECODER_SUPPORT sejam definidos.

### <a name="parameters"></a>Parâmetros

- **image_reader** Bloco de controlo do leitor de imagem
- **pixelmap** Pixelmap de saída

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Descodição de imagem bem sucedida
- **GX_SYSTEM_MEMORY_ERROR** (0x30) O alocador de memória não está definido ou a atribuição de memória falhou
- **GX_NOT_SUPPORTED** (0x28) O tipo de imagem de entrada ou o formato de cor de saída não são suportados
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e Threads

### <a name="example"></a>Exemplo

```C
GX_IMAGE_READER my_image_reader;
GX_PIXELMAP output_map;

/* Create my_image_reader here. */

/* Decoding a raw image according to the settings of “my_image_reader”. */
status = gx_image_reader_start(&my_image_reader, output_map)

/* If status is GX_SUCCESS “output_map” have been loaded with the requested pixelmap. */
```

### <a name="see-also"></a>Consulte também

- gx_image_reader_create
- gx_image_reader_palette_set

## <a name="gx_line_chart_axis_draw"></a>gx_line_chart_axis_draw


Desenhar gráfico de linha x,y eixo

### <a name="prototype"></a>Prototype

```C
VOID gx_line_chart_axis_draw(GX_LINE_CHART *chart);
```

### <a name="description"></a>Descrição

Este serviço desenha o eixo x,y de um gráfico de linha. As cores do eixo e os parâmetros de largura da linha são recuperados a partir da estrutura de informação do gráfico de linha.

Este serviço é normalmente chamado internamente pela função gx_line_chart_draw, mas está exposto à aplicação para ajudar a escrever funções de desenho personalizado.

### <a name="parameters"></a>Parâmetros

- **gráfico** Bloco de controlo de gráficos de linha.

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom chart drawing function. */

VOID my_chart_draw(GX_LINE_CHART *chart)
{
    /* Call default window draw. */
    gx_window_draw((GX_WINDOW *)chart);

    /* Draw the line chart axis. */
    gx_line_chart_axis_draw(&chart->gx_line_chart_info);

    /* Draw the data line */
    gx_line_chart_data_draw(&chart->gx_line_chart_info);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_line_chart_create
- gx_line_chart_data_draw
- gx_line_chart_draw
- gx_line_chart_update
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_create"></a>gx_line_chart_create


Criar widget GX_LINE_CHART

### <a name="prototype"></a>Prototype

```C
UINT gx_line_chart_create(
    GX_LINE_CHART *chart,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_LINE_CHART_INFO *info,
    ULONG style,
    USHORT chart_id, GX_RECTANGLE *size)
```

### <a name="description"></a>Descrição

Este serviço cria uma janela de gráfico de linha. Os parâmetros de desenho do gráfico e os dados do gráfico são transmitidos através da estrutura GX_LINE_CHART_INFO.

GX_LINE_CHART baseia-se em GX_WINDOW e apoia todas as APIs GX_WINDOW.

### <a name="parameters"></a>Parâmetros

- **gráfico** Ponteiro para o GX_LINE_CHART bloco de controlo.
- **nome** Nome de gráfico de linha opcional
- **pai** Widget dos pais, ou GX_NULL
- **informação** Estrutura definindo parâmetros de desenho de gráfico de linha. **O apêndice I** contém definição para GX_LINE_CHART_INFO estrutura.
- **estilo** Bandeiras de estilo Widget
- **chart_id** Valor de ID lógico gráfico
- **tamanho** Retângulo de encadernamento de janela de gráfico

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Gráfico de linha bem sucedido criar
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Create a line chart */
GX_LINE_CHART chart;
GX_RECTANGLE chart_size;
GX_LINE_CHART_INFO gx_chart_info;
GX_WINDOW_ROOT *root_window;

chart_size = root_window->gx_widget_size;

/* Initialize params for the GUIX base chart. */
gx_chart_info.gx_line_chart_min_val = DATA_MIN_VAL;
gx_chart_info.gx_line_chart_max_val = DATA_MAX_VAL;
gx_chart_info.gx_line_chart_max_data_count = MAX_DATA_COUNT;
gx_chart_info.gx_line_chart_active_data_count = 0;
gx_chart_info.gx_line_chart_axis_line_width = AXIS_LINE_WIDTH;
gx_chart_info.gx_line_chart_data_line_width = DATA_LINE_WIDTH;
gx_chart_info.gx_line_chart_data = chart_data;
gx_chart_info.gx_line_chart_line_color = GX_COLOR_ID_DATA_LINE;
gx_chart_info.gx_line_chart_axis_color = GX_COLOR_ID_AXIS_LINE;

/* Leave room for labels on bottom and right. */
gx_chart_info.gx_line_chart_left_margin = 0;
gx_chart_info.gx_line_chart_top_margin = 0;
gx_chart_info.gx_line_chart_right_margin = 80;
gx_chart_info.gx_line_chart_bottom_margin = 32;

status = gx_line_chart_create(&chart, “Line Chart”, root_window,
    &gx_chart_info, GX_STYLE_NONE, &chart_size);

/* If status is GX_SUCCESS, the “chart” has been successfully created. */
```

### <a name="see-also"></a>Consulte também

- gx_line_chart_create
- gx_line_chart_data_draw
- gx_line_chart_draw
- gx_line_chart_update
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_data_draw"></a>gx_line_chart_data_draw


Linha de dados de gráfico de linha

### <a name="prototype"></a>Prototype

```C
VOID gx_line_chart_data_draw(GX_LINE_CHART *chart);
```

### <a name="description"></a>Descrição

Este serviço traça a linha de dados do gráfico de linha. As cores da linha e os parâmetros de largura da linha são recuperados a partir da estrutura de informação do gráfico de linha.

Este serviço é normalmente chamado internamente pela função gx_line_chart_draw, mas está exposto à aplicação para ajudar a escrever funções de desenho personalizado.

### <a name="parameters"></a>Parâmetros

- **gráfico** Bloco de controlo de gráfico de linha

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom chart drawing function. */

VOID my_chart_draw(GX_LINE_CHART *chart)
{
    /* Call default window draw. */
    gx_window_draw((GX_WINDOW *)chart);

    /* Draw the line chart axis. */
    gx_line_chart_axis_draw(chart);

    /* Draw the data line. */
    gx_line_chart_data_draw(chart);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_line_chart_create
- gx_line_chart_draw
- gx_line_chart_update
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_draw"></a>gx_line_chart_draw


Desenhe o gráfico de linha

### <a name="prototype"></a>Prototype

```C
UINT gx_line_chart_draw(GX_LINE_CHART *chart);
```

### <a name="description"></a>Descrição

Esta é a função de desenho de gráfico de linha padrão, que desenha o eixo do gráfico e a linha de dados. As aplicações geralmente fornecem uma função de desenho personalizado para substituir o desenho padrão para adicionar coisas como marcas de cócegas, escala ou outras informações ao eixo do gráfico e linha de dados desenhada pelo widget de gráfico de linha base.

### <a name="parameters"></a>Parâmetros

- **gráfico** Ponteiro para o bloco de controlo de gráficos de linha.

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom chart drawing function. */

VOID my_chart_draw(GX_LINE_CHART *chart)
{
    /* Call default line chart draw. */
    gx_line_chart_draw(chart);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_line_chart_create
- gx_line_chart_draw
- gx_line_chart_update
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_update"></a>gx_line_chart_update


Atualizar linha de dados de gráfico de linha

### <a name="prototype"></a>Prototype

```C
UINT gx_line_chart_update(
    GX_LINE_CHART *chart, 
    INT *data,
    INT data_count)
```

### <a name="description"></a>Descrição

Este serviço atualiza a matriz de dados traçada pela janela do gráfico de linha, e força a janela a redesenhar.

### <a name="parameters"></a>Parâmetros

- **gráfico** Bloco de controlo de gráfico de linha
- **dados** Matriz de dados a ser traçada
- **data_count** Tamanho da matriz de dados

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Botão de texto bem sucedido criar
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
INT chart_data[100];
GX_LINE_CHART chart;

/* Update the data array associated with “chart”. */
status = gx_line_chart_update(&chart, chart_data, 100);

/* If status is GX_SUCCESS, the line chart data has been updated. */
```

### <a name="see-also"></a>Consulte também

- gx_line_chart_create
- gx_line_chart_data_draw
- gx_line_chart_draw
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_y_scale_calculate"></a>gx_line_chart_y_scale_calculate


Calcular o valor de escala do eixo de ponto fixo y

### <a name="prototype"></a>Prototype

```C
UINT gx_line_chart_y_scale_calculate(
    GX_LINE_CHART *chart,
    INT *return_val);
```

### <a name="description"></a>Descrição

Este serviço calcula o valor de escala de ponto fixo utilizado para traçar valores de dados no eixo Y do gráfico. Os parâmetros chart_info e o retângulo de delimitação de gráficos são usados para calcular este valor de escala.

### <a name="parameters"></a>Parâmetros

- **gráfico** Bloco de controlo de gráfico de linha
- **return_val** Endereço de valor para manter o valor de retorno de ponto fixo.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Calcular valor de escala de y bem sucedido
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_LINE_CHART chart;
INT y_scale;

/* Caluclate y scale value of “chart”. */
status = gx_line_chart_y_scale_calculate(&chart, &y_scale);

/* If status is GX_SUCCESS, y scale value of “chart” has been calculated. */
```

### <a name="see-also"></a>Consulte também

- gx_line_chart_create
- gx_line_chart_data_draw
- gx_line_chart_draw
- gx_line_chart_update

## <a name="gx_menu_create"></a>gx_menu_create


Criar um menu

### <a name="prototype"></a>Prototype

```C
UINT gx_menu_create(
    GX_MENU *menu,GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    GX_RESOURCE_ID text_id,
    GX_RESOURCE_ID fill_id, 
    ULONG style, 
    USHORT menu_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria um menu conforme especificado e associa o menu ao widget dos pais fornecidos. Aceita todos os tipos de widget como item do menu infantil. Para inserir um widget como um item de menu infantil, ligue **para gx_menu_insert**.

GX_MENU é derivado de GX_PIXELMAP_PROMPT e suporta todos os serviços gx_pixelmap_prompt API.

### <a name="parameters"></a>Parâmetros

- **menu** Ponteiro para bloco de controlo do menu
- **nome** Nome do menu
- **pai** Ponteiro para widget dos pais
- **text_id** ID de recursos de texto
- **fill_id** ID de recursos de preenchimento
- **estilo** Estilo do widget. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **menu_id** ID definido pela aplicação do menu
- **tamanho** Tamanho do menu

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Criação de menu bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_MENU my_menu;

/* Create “my_menu”. */
status = gx_menu_create(&my_menu, “my_menu”, parent, MY_TEXT_ID,
    MY_FILL_ID, GX_STYLE_ENABLED, MY_MENU_ID,
    &size);

/* If status is GX_SUCCESS, the menu was successfully created. */
```

### <a name="see-also"></a>Consulte também

- gx_accordion_meu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_draw
- gx_menu_event_process
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_draw"></a>gx_menu_draw


Menu de desenho

### <a name="prototype"></a>Prototype

```C
VOID gx_menu_draw(GX_MENU *menu);
```

### <a name="description"></a>Descrição

Este serviço desenha o menu especificado. Esta função é normalmente chamada internamente pelo mecanismo de atualização de lona GUIX, mas está exposta à aplicação para ajudar na implementação de funções de desenho personalizado para widgets de menu personalizados.

### <a name="parameters"></a>Parâmetros

- **menu** Ponteiro para bloco de controlo do menu

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom menu drawing function. */

VOID my_menu_draw(GX_MENU *menu)
{
    /* Call default menu draw. */
    gx_menu_draw(menu);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_event_process
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_event_process"></a>gx_menu_event_process

Evento do menu do processo

### <a name="prototype"></a>Prototype

```C
UINT gx_menu_event_process(GX_MENU *menu, GX_EVENT *event_ptr);
```

### <a name="description"></a>Descrição

Este serviço processa um evento para o menu especificado. Este serviço deve ser chamado como o manipulador de eventos predefinido por quaisquer funções de processamento de eventos de menu personalizado.

### <a name="parameters"></a>Parâmetros

- **menu** Ponteiro para bloco de controlo do menu
- **event_ptr** Ponteiro para o evento para processar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Processo de evento de menu bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x23) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Call generic menu event processing as part of custom event processing function. */

UINT custom_menu_event_process(GX_MENU *menu, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */

        /* Call default event process if this is a system event such as GX_EVENT_SHOW. */
        status = gx_menu_event_process(menu, event);
        break;

    default:
        /* Pass all other events to the default menu
           event processing */
        status = gx_menu_event_process(menu, event);
        break;
    }
    return status;
}

```

### <a name="see-also"></a>Consulte também

- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_insert"></a>gx_menu_insert


Inserir um novo item

### <a name="prototype"></a>Prototype

```C
UINT gx_menu_insert(
    GX_MENU *menu, 
    GX_WIDGET *insert);
```

### <a name="description"></a>Descrição

Este serviço insere um novo item no menu.

### <a name="parameters"></a>Parâmetros

- **menu** Ponteiro para bloco de controlo do menu
- **widget** Ponteiro para o widget para inserir

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Inseriu com sucesso novo item no menu
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Insert new item “my_widget” to the menu “my_menu”. */
status = gx_menu_insert(&my_menu, &my_widget);

/* If status is GX_SUCCESS the new item “my_widget” has been inserted to the menu “my_menu”. */
```

### <a name="see-also"></a>Consulte também

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_event_process
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_remove"></a>gx_menu_remove


Remover um item

### <a name="prototype"></a>Prototype

```C
UINT gx_menu_remvoe(
    GX_MENU *menu, 
    GX_WIDGET *widget);
```

### <a name="description"></a>Descrição

Este serviço remove um item do menu.

### <a name="parameters"></a>Parâmetros

- **menu** Ponteiro para bloco de controlo do menu
- **widget** Ponteiro para widget para remover

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Produto do menu removido com sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Remove item “my_widget” from menu “my_menu” */
status = gx_menu_remove(&my_menu, &my_widget);

/* If status is GX_SUCCESS the item “my_widget” has been removed from menu “my_menu”. */
```

### <a name="see-also"></a>Consulte também

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_event_process
- gx_menu_insert
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_text_draw"></a>gx_menu_text_draw


Desenhar texto do menu

### <a name="prototype"></a>Prototype

```C
VOID gx_menu_text_draw(GX_MENU *menu);
```

### <a name="description"></a>Descrição

Este serviço desenha o texto de um menu. Esta função é normalmente chamada internamente pelo mecanismo de atualização de lona GUIX, mas está exposta à aplicação para ajudar na implementação de funções de desenho personalizado para widgets de menu personalizados.

### <a name="parameters"></a>Parâmetros

- **menu** Ponteiro para bloco de controlo do menu

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom menu drawing function. */

VOID my_menu_draw(GX_MENU *menu)
{
    /* Call default menu background draw. */
    gx_pixelmap_prompt_background_draw(
                            (GX_PIXELMAP_PROMPT *)menu);

    /* Draw menu text. */
    gx_menu_text_draw(menu);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_event_process
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_offset_set

## <a name="gx_menu_text_offset_set"></a>gx_menu_text_offset_set


Definir design de texto de texto offset

### <a name="prototype"></a>Prototype

```C
UINT gx_menu_text_offset_set(
    GX_MENU *menu, 
    GX_VALUE x_offset,
    GX_VALUE y_offset);
```

### <a name="description"></a>Descrição

Este serviço define x, y display offset para o texto do menu.

### <a name="parameters"></a>Parâmetros

- **menu** Ponteiro para bloco de controlo do menu
- **x_offset** X coordenada de offset
- **y_offset** Y coordenada de offset

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Design de texto conjunto bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set text draw offset of menu “my_menu” to (20, 10). */
status = gx_menu_text_offset_set(&my_menu, 20, 10);

/* If status is GX_SUCCESS the text draw offset of menu “my_menu” has been set to (20, 10). */
```

### <a name="see-also"></a>Consulte também

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_event_process
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw

## <a name="gx_multi_line_text_button_create"></a>gx_multi_line_text_button_create


Criar botão de texto de várias linhas

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_button_create(
    GX_MULTI_LINE_TEXT_BUTTON *text_button,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id,
    ULONG style,
    USHORT text_button_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria um widget de botão de texto multi-linha. Um botão de texto multi-linha exibe o texto do botão sobre linhas de 1-n. O número máximo de linhas é definido pela GX_MULTI_LINE_TEXT_BUTTON_MAX_LINES constante, que não chega a 4. As quebras de linha são definidas por retorno de transporte e/ou retorno de transporte + pares de alimentação de linha dentro da cadeia de texto atribuída ao botão de texto multi-linha.

GX_MULTI_LINE_TEXT_BUTTON é derivado de GX_TEXT_BUTTON e suporta todos os gx_text_button serviços da API.

### <a name="parameters"></a>Parâmetros

- **text_button** Ponteiro para bloco de controlo de botões de texto
- **nome** Nome lógico do botão de texto
- **pai** Ponteiro para o widget dos pais do botão
- **text_id** ID de recursos de texto
- **estilo** Estilo de botão de texto. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **text_button_id** ID definido pela aplicação do botão de texto
- **tamanho** Tamanho do botão

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Botão de texto multi-linha bem sucedido criar
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Create multi-line text button “my_text_button”. */
status = gx_multi_line_text_button_create(&my_text_button, "my text button",
    &my_parent_window, MY_TEXT_RESOURCE_ID,
    GX_STYLE_BUTTON_TOGGLE, MY_TEXT_BUTTON_ID,
    &size);

/* If status is GX_SUCCESS, the multi-line text button “my_text_button” was created. */
```

### <a name="see-also"></a>Consulte também

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_draw"></a>gx_multi_line_text_button_draw


Desenhar botão de texto multi-linha

### <a name="prototype"></a>Prototype

```C
VOID gx_multi_line_text_button_draw(GX_MULTI_LINE_TEXT_BUTTON *button);
```

### <a name="description"></a>Descrição

Este serviço desenha o botão de texto multi-linha. Esta função é normalmente chamada internamente pelo GUIX como parte de uma operação de atualização de tela, mas também exposta à aplicação que pode querer fornecer uma função de desenho personalizado e invocar o desenho de botão de texto multi-linha padrão como base de desenho personalizado.

### <a name="parameters"></a>Parâmetros

- **botão** Ponteiro para bloco de controlo de botões de texto

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Draw the text button “my_text_button”. */
void MyButtonDraw(GX_MULTI_LINE_TEXT_BUTTON *button)
{
    /* Do the normal drawing first */
    gx_multi_line_text_button_draw(&my_text_button);

    /* Add custom drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_event_process"></a>gx_multi_line_text_button_event_process


Tratamento de evento predefinido para botão de texto multi-linha

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_button_event_process(
    GX_MULTI_LINE_TEXT_BUTTON *button,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Descrição

Este serviço é a função de tratamento de eventos predefinido para o widget de botão de texto multi linha. Esta função é tornada acessível a aplicações que pretendam fornecer o manuseamento personalizado de eventos para um widget de botão de texto.

### <a name="parameters"></a>Parâmetros

- **botão** Ponteiro para bloco de controlo de botões de texto
- **event_ptr** Evento a ser processado

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) com sucesso do evento
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
UINT MyEventHandler(GX_MULTI_LINE_TEXT_BUTTON *button,
    GX_EVENT *event_ptr)
{
    switch(event->gx_event_type)
    {
    case GX_EVENT_SHOW:
        gx_multi_line_text_button_event_process(button, event_ptr);
        /* add custom actions here */
        break;
    default:
        gx_multi_line_text_button_event_process(button, event_ptr);
        break;
    }
    return GX_SUCCESS;
}
```

### <a name="see-also"></a>Consulte também

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_text_draw"></a>gx_multi_line_text_button_text_draw


Função de suporte de desenho

### <a name="prototype"></a>Prototype

```C
VOID gx_multi_line_text_button_text_draw(GX_MULTI_LINE_TEXT_BUTTON *text_button);
```

### <a name="description"></a>Descrição

Esta função de suporte desenha a parte de texto de um botão de texto multi-linha. Esta função é chamada internamente por gx_multi_line_text_button_draw(), e é fornecida como uma API separada como uma conveniência para aplicações que definem uma função de desenho de botão de texto multi-linha personalizada. As aplicações que pretendem personalizar o desenho de fundo do botão podem fornecer a sua função de desenho personalizado e invocar o serviço de multi_line_text_button_text_draw como parte do seu desenho personalizado para desenhar o texto do botão sobre o fundo.

### <a name="parameters"></a>Parâmetros

- **text_button** Ponteiro para bloco de controlo de botões de texto

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Define a custom drawing function */
VOID my_button_draw(GX_MULTI_LINE_TEXT_BUTTON *button)
{
    /* insert code here to draw button background */

    /* call support function to do text drawing */
    gx_multi_line_text_button_text_draw();

    /* draw child widgets */
    gx_widget_children_draw((GX_WIDGET *) button);
}
```

### <a name="see-also"></a>Consulte também

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set


## <a name="gx_multi_line_text_button_text_id_set"></a>gx_multi_line_text_button_text_id_set


Definir iD de recursos de texto para o botão de texto

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_button_text_id_set(
    GX_MULTI_LINE_TEXT_BUTTON *text_button,
    RESOURCE_ID string_id)
```

### <a name="description"></a>Descrição

Este serviço define o ID de recurso de cadeia especificado para o botão de texto. A cadeia pode conter caracteres newline que atuam para exibir o texto em várias linhas dentro da área do botão.

### <a name="parameters"></a>Parâmetros

- **text_button** Ponteiro para bloco de controlo de botões de texto
- **string_id** ID de recurso da cadeia

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso o ID do recurso de corda para o botão de texto
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the string ID ”MY_STRING_ID” to the text button “my_text_button”. */
status = gx_multi_line_text_button_text_id_set(
    &my_text_button, MY_STRING_ID);

/* If status is GX_SUCCESS, the string ID MY_STRING_ID was set to “my_text_button”. */
```

### <a name="see-also"></a>Consulte também

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_text_set"></a>gx_multi_line_text_button_text_set


Atribuir texto ao botão de texto (precotado)

### <a name="prototype"></a>Prototype

```C
UINT gx_mult_line_text_button_text_set(
    GX_MULTI_LINE_TEXT_BUTTON *text_button,
    GX_CHAR *text);
```

### <a name="description"></a>Descrição

Este serviço é precotado a favor de gx_multi_line_text_button_text_set_ext().

Este serviço atribui a cadeia especificada ao botão de texto. Se o widget text_button foi criado com GX_STYLE_TEXT_COPY de estilo, o widget cria uma cópia privada da cadeia de texto atribuída, pelo que a API gx_system_memmory_allocate_set deve ser invocada uma vez antes deste serviço ser solicitado. Se GX_STYLE_TEXT_COPY não estiver ativa, o widget não faz uma cópia privada da cadeia de entrada, pelo que a cadeia deve ser atribuída estática ou globalmente, ou seja, pode não ser uma variável automática ou temporária.

### <a name="parameters"></a>Parâmetros

- **text_button** Ponteiro para bloco de controlo de botões de texto
- ponteiro de **texto** para a cadeia terminada NU

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir o texto com sucesso para o botão
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_MEMORY_ERROR** (0x30) Alocador de memória não está definido
- **GX_INVALID_STRING_LENGTH** (0x34) Comprimento da corda inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
static GX_CHAR text[] = “myrstring”;

/* Set text to the text button “my_text_button”. */
status = gx_multi_line_text_button_text_set(&my_text_button, text);

/* If status is GX_SUCCESS, the text of “my_text_button” was set. */
```

### <a name="see-also"></a>Consulte também

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_text_set_ext"></a>gx_multi_line_text_button_text_set_ext


Atribuir texto ao botão de texto

### <a name="prototype"></a>Prototype

```C
UINT gx_mult_line_text_button_text_set_ext(
    GX_MULTI_LINE_TEXT_BUTTON *text_button,
    GX_STRING *string)
```

### <a name="description"></a>Descrição

Este serviço atribui a cadeia especificada ao botão de texto. Se o widget text_button foi criado com GX_STYLE_TEXT_COPY de estilo, o widget cria uma cópia privada da cadeia de texto atribuída, pelo que a API gx_system_memmory_allocate_set deve ser invocada uma vez antes deste serviço ser solicitado. Se GX_STYLE_TEXT_COPY não estiver ativa, o widget não faz uma cópia privada da cadeia de entrada, pelo que a cadeia deve ser atribuída estática ou globalmente, ou seja, pode não ser uma variável automática ou temporária.

### <a name="parameters"></a>Parâmetros

- **text_button** Ponteiro para bloco de controlo de botões de texto
- ponteiro **de cordas** para GX_STRING variável

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir o texto com sucesso para o botão
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_MEMORY_ERROR** (0x30) Alocador de memória não está definido
- **GX_INVALID_STRING_LENGTH** (0x34) Comprimento da corda inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
static GX_CHAR text[] = “myrstring”;
GX_STRING string;

string.gx_string_ptr = text;
string.gx_string_length = strlen(text);

/* Set text to the text button “my_text_button”. */
status = gx_multi_line_text_button_text_set_ext(&my_text_button, string);

/* If status is GX_SUCCESS, the text of “my_text_button” was set. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_input_backspace"></a>gx_multi_line_text_input_backspace


Elimine um personagem antes da posição do cursor de entrada de texto de várias linhas

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_backspace(
    GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Descrição

Este serviço elimina o carácter antes da posição do cursor de entrada de texto de várias linhas. Este serviço é chamado internamente quando um evento de chave de backspace para baixo é recebido, mas também pode ser invocado pela aplicação.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto multi-line

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Backspace de entrada de texto multi-linha bem sucedida
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x23) não é válido
- **GX_FAILURE** (0x10) Fonte inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Delete a character before the cursor of “my_text_input”. */
status = gx_multi_line_text_input_backspace(&my_text_input);

/* If status is GX_SUCCESS the character before the cursor has been deleted. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_buffer_clear"></a>gx_multi_line_text_input_buffer_clear


Elimina todos os caracteres do tampão de entrada de texto

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_buffer_clear(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Descrição

Este serviço elimina todos os caracteres do tampão de entrada de texto.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto multi-line

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Tampão de entrada de texto multi-linha bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* clear input buffer of “my_text_input”. */
status = gx_multi_line_text_input_clear(&my_text_input);

/* If status is GX_SUCCESS the text input widget has emptied its input buffer. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_buffer_get"></a>gx_multi_line_text_input_buffer_get


Recupera informações tampão do widget de entrada de texto

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_buffer_get(
    GX_MULTI_LINE_TEXT_INPUT *text_input, 
    GX_CHAR **buffer_address,
    UINT *content_size, 
    UINT *buffer_size);
```

### <a name="description"></a>Descrição

Este serviço obtém informações tampão de um widget de entrada de texto de várias linhas.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto multi-line
- **buffer_address** O endereço do tampão de entrada
- **content_size** A contagem byte dos dados de entrada
- **buffer_size** O tamanho do tampão de entrada

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Texto multi-linha bem sucedido obter
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_CHAR *buffer_address;
UINT context_size;
UINT buffer_size;

/* Retrieves buffer information of “my_text_input” widget. */
status = gx_multi_line_text_input_buffer_get(&my_text_input,
    &buffer_address, &string_size,
    &buffer_size);

/* If status is GX_SUCCESS the value of buffer_address, string_size and buffer_size has been retrieved. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_char_insert"></a>gx_multi_line_text_input_char_insert


Insira uma cadeia de caracteres na posição atual do cursor de entrada de texto multi linha (precotado)

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_char_insert(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_UBYTE *insert_str,
    UINT insert_size);
```

### <a name="description"></a>Descrição

Esta API é depreciada e substituída por gx_multi_line_text_input_char_insert_ext().

Este serviço insere uma cadeia de caracteres no tampão de cadeia de entrada de texto multi linha na posição atual do cursor. Este serviço é chamado internamente quando o evento chave para baixo específico é recebido, mas também pode ser invocado pela aplicação.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto multi-line
- **insert_str** Cadeia de caracteres de formato UTF-8 a ser inserida
- **insert_size** Contagem de byte a ser inserida

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Inseriu com sucesso a cadeia de caracteres
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido
- **GX_INVALID_VALUE** (0x22) Tamanho da corda inválida
- **GX_FAILURE** (0x10) Fonte inválida ou fora do tamanho do tampão

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Insert characters at current cursor position. */
GX_CHAR insert_text[10] = “insert”;
status = gx_multi_line_text_input_char_insert(&my_text_input,
    insert_text,
    GX_STRLEN(insert_text));

/* If status is GX_SUCCESS the multi line text input widget has successfully insert the string. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_char_insert_ext

## <a name="gx_multi_line_text_input_char_insert_ext"></a>gx_multi_line_text_input_char_insert_ext


Insira uma cadeia de caracteres na posição atual do cursor de entrada de texto multi linha (precotado)

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_char_insert_ext(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Descrição

Este serviço insere uma cadeia de caracteres no tampão de cadeia de entrada de texto multi linha na posição atual do cursor. Este serviço é chamado internamente quando eventos específicos de down são recebidos, mas também pode ser invocado pela aplicação.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto multi-line
- **cadeia** Cadeia de caracteres codificada UTF-8 a ser inserida

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Inseriu com sucesso a cadeia de caracteres
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido
- **GX_INVALID_VALUE** (0x22) Tamanho da corda inválida
- **GX_FAILURE** (0x10) Fonte inválida ou fora do tamanho do tampão
- **GX_INVALID_STRING_LENGTH** (0x34) Comprimento da corda inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Insert characters at current cursor position. */
GX_CHAR insert_text[10] = “insert”;
GX_STRING string;

string.gx_string_ptr = insert_text;
string.gx_string_length = strlen(insert_text);

status = gx_multi_line_text_input_char_insert_ext(&my_text_input, &string);

/* If status is GX_SUCCESS the multi line text input widget has successfully inserted the string. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_create"></a>gx_multi_line_text_input_create


Criar entrada de texto multi-linha

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_create(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_CHAR *name, GX_WINDOW *parent,
    GX_CHAR *input_buffer, UINT buffer_size,
    ULONG style, USHORT text_input_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria um widget de entrada de texto multi-line.

GX_MULTI_LINE_TEXT_INPUT é derivado de GX_MULTI_LINE_TEXT_VIEW e apoia todos os serviços gx_multi_line_text_view.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto multi-line
- **nome** Nome do widget de entrada de texto
- **pai** Ponteiro para widget dos pais
- **input_buffer** Ponteiro para tampão de entrada de texto
- **buffer_size** Tamanho do tampão de entrada de texto em bytes
- **estilo** Estilo de widget de entrada de texto. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **text_input_id** ID definido pela aplicação da entrada de texto
- **tamanho** Dimensões do widget de entrada de texto

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Entrada de texto multi-linha bem sucedida cria
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_WIDGET** (0x12) Widget dos pais não é válido
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_MULTI_LINE_TEXT_INPUT my_text_input;
GX_CHAR my_buffer[100];
GX_RECTANGLE size;

/* Define widget size. */
gx_utility_rectangle_define(&size, 10, 10, 100, 200);

/* Create multi-line text input widget “my_text_input”. */
status = gx_multi_line_text_input_create(&my_text_input,
    “my_text_input”, &my_parent,
    my_buffer, 100, GX_STYLE_BORDER_RAISED,
    MY_TEXT_INPUT_ID, &size);

/* If status is GX_SUCCESS, the text input “my_text_input” has been created. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_cursor_pos_get"></a>gx_multi_line_text_input_cursor_pos_get


Recupere a posição do cursor de entrada de texto de várias linhas

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_cursor_pos_get(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_POINT cursor_pos);
```

### <a name="description"></a>Descrição

Este serviço recupera a posição do cursor de entrada de texto de linha de mult.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto multi-line
- **cursor_pos** Posição do cursor recuperado

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) recuperou com sucesso a posição do cursor
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Retrieve the cursor position of “my_text_input”. */
GX_POINT cursor_pos;
status = gx_multi_line_text_input_cursor_pos_get(&my_text_input,
    &cursor_pos);

/* If status is GX_SUCCESS the cursor position has been retrieved. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_delete"></a>gx_multi_line_text_input_delete


Elimine o carácter na posição do cursor de entrada de texto multi linha

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_delete(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Descrição

Este serviço elimina o carácter após a posição do cursor de entrada de texto multi linha. Este serviço é chamado internamente quando um evento de eliminação de chave para baixo é recebido, mas também pode ser invocado pela aplicação.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto multi-line

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) elimine com sucesso um personagem após o cursor
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido
- **GX_FAILURE** (0x10) Fonte inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Delete the character after the cursor of “my_text_input”. */
status = gx_multi_line_text_input_delete(&my_text_input);

/* If status is GX_SUCCESS the character after the cursor has been deleted. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_down_arrow"></a>gx_multi_line_text_input_down_arrow


Mova o cursor de entrada de texto de várias linhas para a linha seguinte

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_down_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Descrição

Este serviço posiciona o cursor de widget de entrada de texto multi linha para a linha seguinte. Este serviço é chamado internamente quando um evento de tecla de seta para baixo é recebido, mas também pode ser invocado pela aplicação.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto multi-line

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) moveu com sucesso o cursor de entrada de texto para a linha seguinte
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido
- **GX_FAILURE** (0x10) Fonte inválida ou altura da linha

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Move input cursor to the next line. */
status = gx_multi_line_text_input_down_arrow(&my_text_input);

/* If status is GX_SUCCESS, text text input cursor has been moved to the next line. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_end"></a>gx_multi_line_text_input_end


Mova o cursor de entrada de texto de várias linhas para o fim da linha atual

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_end(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Descrição

Este serviço posiciona o cursor de widget de entrada de texto multi linha até ao fim da linha de corda atual. Este serviço é chamado internamente quando um evento de chave final para baixo é recebido, mas também pode ser invocado pela aplicação.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto multi-line

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) moveu com sucesso o cursor de entrada de texto para o fim da linha atual
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Move input cursor to the end of current line. */
status = gx_multi_line_text_input_end(&my_text_input);

/* If status is GX_SUCCESS, the multi line text input cursor has been moved to the end of the current line. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_event_process"></a>gx_multi_line_text_input_event_process


Tratamento de eventos predefinidos para entrada de texto multi-linha

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_event_process(
    GX_MULTI_LINE_TEXT_INPUT *input,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Descrição

Este serviço é a função de tratamento de eventos predefinido para o widget de entrada de texto de várias linhas. Esta função é disponibilizada a aplicações que pretendam fornecer o manuseamento personalizado de eventos para um widget de entrada de texto de várias linhas.

### <a name="parameters"></a>Parâmetros

- **botão** Ponteiro para bloco de controlo de entrada de texto de várias linhas
- **event_ptr** Evento a ser processado

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) com sucesso do evento
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_WIDGET** (0x12) Widget dos pais não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
UINT MyEventHandler(GX_MULTI_LINE_TEXT_INPUT *input,
    GX_EVENT *event_ptr)
{
    switch(event->gx_event_type)
    {
    case xyz:
        /* insert custom event handling here */
        break;
    default:
        /* pass all other events to the generic multi line text
            input event processing */
        gx_multi_line_text_input_event_process(input, event_ptr);
        break;
    }
    return GX_SUCCESS;
}
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_fill_color_set"></a>gx_multi_line_text_input_fill_color_set


Definir a cor de fundo de fundo de entrada de texto multi linha

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_fill_color_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_fill_color_id,
    GX_RESOURCE_ID selected_fill_color_id,
    GX_RESOURCE_ID disabled_fill_color_id,
    GX_RESOURCE_ID readonly_fill_color_id);
```

### <a name="description"></a>Descrição

Este serviço atribui cores de preenchimento para o widget de entrada de texto multi-linha.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto multi-line
- **normal_fill_color_id** ID de recurso da cor de preenchimento normal que foi usada em estado normal
- **selected_fill_color_id** ID de recurso da cor de preenchimento selecionada que usou quando o widget ganha o foco
- **disabled_fill_color_id** ID de recursos da cor de preenchimento desativado que foi usado quando GX_STYLE_ENABLED não está ativo
- **readonly_fill_color_id** ID de recurso da leitura apenas preencha a cor que é usada quando GX_STYLE_ENABLED e GX_STYLE_INPUT_READONLY estão ativas.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso cores para a entrada de texto multi-linha
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set fill colors for the multi-line text input widget “my_text_input”. */

status = gx_multi_line_text_input_fill_color_set(&my_text_input,
    GX_COLOR_ID_NORMAL_FILL,
    GX_COLOR_ID_SELECTED_FILL,
    GX_COLOR_ID_DISABLED_FILL,
    GX_COLOR_ID_READONLY_FILL);

/* If status is GX_SUCCESS, the fill color of “my_text_input” has been successfully set. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_home"></a>gx_multi_line_text_input_home


Mova o cursor de entrada de texto para o início da linha atual

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_home(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Descrição

Este serviço move a posição do cursor de entrada de texto para o início da linha atual. Este serviço é chamado internamente quando um evento de home key down é recebido, mas também pode ser invocado pela aplicação.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto multi-line

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) moveu com sucesso o cursor para o início da linha atual
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Move cursor to the start of the current line. */
status = gx_multi_line_text_input_home(&my_text_input);

/* If status is GX_SUCCESS the cursor has been moved to the start of the current line. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_left_arrow"></a>gx_multi_line_text_input_left_arrow


Mover cursor de entrada de texto multi linha um personagem para a esquerda

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_left_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Descrição

Este serviço move o cursor de entrada de texto de várias linhas um caracter para a esquerda. Este serviço é chamado internamente quando um evento de chave esquerda para baixo é recebido, mas também pode ser invocado pela aplicação.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto de linha única

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) moveu com sucesso o cursor para a esquerda
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido
- **GX_FAILURE** (0x10) Fonte inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Move the cursor one character to the left. */
status = gx_multi_line_text_input_left_arrow(&my_text_input);

/* If status is GX_SUCCESS the multi line text input cursor has been moved one character to the left. */

```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_right_arrow"></a>gx_multi_line_text_input_right_arrow


Mover cursor de entrada de texto de linha de mult um personagem para a direita

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_right_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Descrição

Este serviço move o cursor de entrada de texto de várias linhas um caracter para a direita. Este serviço é chamado internamente quando um evento de chave direita para baixo é recebido, mas também pode ser invocado pela aplicação.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto multi-line

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) moveu com sucesso o cursor para a direita
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Move cursor one character to the right. */
status = gx_multi_line_text_input_right_arrow(&my_text_input);

/* If status is GX_SUCCESS the text input cursor has been moved one character to the right. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_style_add"></a>gx_multi_line_text_input_style_add


Adicionar estilos de entrada de texto multi-linha

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_style_add(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    ULONG style);
```

### <a name="description"></a>Descrição

Este serviço adiciona estilos a um widget de entrada de texto multi-line.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto multi-line
- **estilo** Estilos a adicionar. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Bem sucedido estilo de entrada de texto multi-linha adicionar
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Add style GX_STYTLE_CURSOR_ALWAYS to multi-line text input widget “my_text_input”. */
status = gx_multi_line_text_input_style_add(&my_text_input,
    GX_STYLE_CURSOR_ALWAYS);

/* If status is GX_SUCCESS the style GX_STYLE_CURSOR_ALWAYS has been successfully added. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_style_remove"></a>gx_multi_line_text_input_style_remove


Remover estilos

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_remove(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    ULONG style);
```

### <a name="description"></a>Descrição

Este serviço remove os estilos especificados do widget de entrada de texto multi-line.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto multi-line
- **estilo** Estilos para remover. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Entrada de texto multi-linha bem sucedida cria
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Remove style GX_STYLE_CURSOR_ALWAYS from text input widget “my_text_input”. */
status = gx_multi_line_text_input_style_remove(&my_text_input,
    GX_STYLE_CURSOR_ALWAYS);

/* If status is GX_SUCCESS, the style GX_STYLE_CURSOR_ALWAYS has been successfully removed. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_style_set"></a>gx_multi_line_text_input_style_set

Definir estilos de entrada de texto multi-linha

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_style_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input, 
    ULONG style);
```

### <a name="description"></a>Descrição

Este serviço define os estilos para um widget de entrada de texto multi-line.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto multi-line
- **estilo** Estilos para definir. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de estilo de entrada de texto multi-linha bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set style GX_STYLE_CURSOR_ALWAYS for text input widget “my_text_input”. */
status = gx_multi_line_text_input_style_set(&my_text_input,
    GX_STYLE_CURSOR_ALWAYS);

/* If status is GX_SUCCESS the text input style has been set */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_text_color_set"></a>gx_multi_line_text_input_text_color_set


Definir a cor do texto de entrada de texto de texto de várias linhas

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_text_color_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCE_ID disabled_text_color_id,
    GX_RESOURCE_ID readonly_text_color_id);
```

### <a name="description"></a>Descrição

Este serviço atribui cores de texto para o widget de entrada de texto multi-linha.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto multi-line
- **normal_fill_color_id** ID de recurso da cor de texto normal que foi usado em estado normal
- **selected_text_color_id** ID de recurso da cor de texto selecionada que usou quando o widget ganha o foco
- **disabled_text_color_id** ID de recursos da cor de texto desativada que foi utilizada quando GX_STYLE_ENABLED não está ativa
- **readonly_text_color_id** ID de recurso da cor de texto de leitura única que usada quando tanto GX_STYLE_ENABLED como GX_STYLE_TEXT_INPUT_READONLY estão ativas

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso cores para a entrada de texto multi-linha
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set text colors for the multi-line text input widget “my_text_input”. */
status = gx_multi_line_text_input_text_color_set(&my_text_input,
    GX_COLOR_ID_NORMAL_TEXT,
    GX_COLOR_ID_SELECTED_TEXT,
    GX_COLOR_ID_DISABLED_TEXT,
    GX_COLOR_ID_READONLY_TEXT);

/* If status is GX_SUCCESS, the fill colors of “my_text_view” has been successfully set. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_text_select"></a>gx_multi_line_text_input_text_select


Selecione texto

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_text_select(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    UINT start_index, UINT end_index);
```

### <a name="description"></a>Descrição

Este serviço seleciona o texto de entrada de texto de várias linhas com o índice de marca de início e de marca final especificado e destaca o texto selecionado com as cores de preenchimento e texto selecionados.

### <a name="parameters"></a>Parâmetros

- **text_input** Ponteiro para bloco de controlo de entrada de texto de várias linhas
- **start_index** Índice do primeiro caráter selecionado
- **end_index** Índice do último caráter selecionado

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Seleção de texto de entrada de texto multi-linha bem sucedida
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido
- **GX_INVALID_VALUE** (0x22) Valor do índice não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Select text between index [0, 9]. */
status = gx_multi_line_text_input_text_select(&my_text_input,
    0,9);

/* If status is GX_SUCCESS, the text between 
    index [0, 9] “my_text_input” was selected. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_text_set"></a>gx_multi_line_text_input_text_set


Atribuir texto à entrada de texto (precotado)

### <a name="prototype"></a>Prototype

```C
UINT gx_mult_line_text_input_text_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CHAR *text);
```

### <a name="description"></a>Descrição

Esta API é depreciada e substitua por gx_multi_line_text_input_text_set_ext().

Este serviço atribui o fio especificado à entrada de texto de várias linhas. Se o tamanho do tampão de entrada do widget multi_line_text_input for menor do que o comprimento da corda, a corda será truncada.

### <a name="parameters"></a>Parâmetros

- **text_input** Ponteiro para bloco de controlo de entrada de texto de várias linhas
- ponteiro de **texto** para a cadeia terminada NU

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir o texto com sucesso para a entrada de texto multi-linha
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_STRING_LENGTH** (0x34) Comprimento da corda inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the string “my string” to the text button “my_text_input”. */
status = gx_multi_line_text_input_text_set(&my_text_input,
    “myrstring”);

/* If status is GX_SUCCESS, the content of “my_text_input” bas been reset. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_text_set_ext

## <a name="gx_multi_line_text_input_text_set_ext"></a>gx_multi_line_text_input_text_set_ext


Atribuir texto à entrada de texto

### <a name="prototype"></a>Prototype

```C
UINT gx_mult_line_text_input_text_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Descrição

Este serviço atribui o fio especificado à entrada de texto de várias linhas. Se o tamanho do tampão de entrada do widget multi_line_text_input for menor do que o comprimento da corda, a corda será truncada.

### <a name="parameters"></a>Parâmetros

- **text_input** Ponteiro para bloco de controlo de entrada de texto de várias linhas
- ponteiro **de cordas** para GX_STRING para atribuir

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir o texto com sucesso para a entrada de texto multi-linha
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_STRING_LENGTH** (0x34) Comprimento da corda inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the string “my string” to the text button “my_text_input”. */
GX_STRING string;
string.gx_string_ptr = “myrstring”;
string.gx_string_length = strlen(string.gx_string_ptr);

status = gx_multi_line_text_input_text_set_ext(&my_text_input,
    &string);

/* If status is GX_SUCCESS, the content of “my_text_input” bas been reset. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_up_arrow"></a>gx_multi_line_text_input_up_arrow


Mova o cursor de entrada de texto de várias linhas para a linha anterior

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_up_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Descrição

Este serviço move o cursor de entrada de texto de várias linhas para a linha de texto anterior. Este serviço é chamado internamente quando um evento de tecla de seta para cima é recebido, mas também pode ser invocado pela aplicação.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto de linha única

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) mudou com sucesso o cursor para a linha anterior
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Move the cursor to the previous line. */
status = gx_multi_line_text_input_up_arrow(&my_text_input);

/* If status is GX_SUCCESS the multi line text input cursor has been moved to the previous line. */

```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_create"></a>gx_multi_line_text_view_create


Criar vista de texto multi-linha

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_view_create(
    GX_MULTI_LINE_TEXT_VIEW *text_view,
    GX_CONST GX_CHAR *name, 
    GX_WINDOW *parent, 
    GX_RESOURCE_ID text_id,
    ULONG style, 
    USHORT text_view_id, 
    GX_CONST GX_RECTANGLE *size);

```

### <a name="description"></a>Descrição

Este serviço cria um widget GX_MULTI_LINE_TEXT_VIEW. Este tipo de widget é derivado de GX_WINDOW, e, portanto, todos os gx_window serviços de API também podem ser utilizados com este tipo de widget.

### <a name="parameters"></a>Parâmetros

- **text_view** Bloco de controlo widget de visualização de texto multi-line
- **nome** Nome do widget de visualização de texto
- **pai** Ponteiro para widget dos pais
- **text_id** ID de recurso da cadeia de texto
- **estilo** Estilo de widget de vista de texto. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **text_view_id** ID definido pela aplicação da visão de texto
- **tamanho** Dimensões do widget de visualização de texto

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) criou com sucesso widget de visualização de texto multi-linha
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Create multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_create(&my_text_view,
    “my_text_view”, &my_parent,
    TEXT_STRING_ID, GX_STYLE_BORDER_RAISED,
    MY_TEXT_VIEW_ID, &size);

/* If status is GX_SUCCESS the text view “my_text_view” has been successfully created. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_draw"></a>gx_multi_line_text_view_draw


Desenhe um widget de visualização de texto de várias linhas

### <a name="prototype"></a>Prototype

```C
VOID gx_multi_line_text_view_draw(GX_MULTI_LINE_TEXT_VIEW * text_view);
```

### <a name="description"></a>Descrição

Este serviço desenha um widget de visualização de texto de várias linhas. Este serviço é normalmente chamado internamente durante a atualização de tela, mas também pode ser chamado de funções de desenho de visão de texto multi-linha personalizadas.

### <a name="parameters"></a>Parâmetros

- **text_view** Bloco de controlo widget de visualização de texto multi-line

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Write a custom multi line text view drawing function. */

VOID my_multi_line_text_view_draw(GX_MULTI_LINE_TEXT_VIEW *view)
{
    /* Call default multi line text view draw. */
    gx_multi_line_text_view_draw(view);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_event_process"></a>gx_multi_line_text_view_event_process


Evento de visualização de texto multi-linha de processo

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_view_event_process(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_EVENT *event);
```

### <a name="description"></a>Descrição

Este serviço processa um evento para um widget de visualização de texto multi-line.

### <a name="parameters"></a>Parâmetros

- **text_view** Bloco de controlo widget de visualização de texto multi-line
- **evento** Ponteiro para o evento para processar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Processo de evento de visualização de texto multi-linha bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom event handler. */
UINT my_event_handler(GX_MULTI_LINE_TEXT_VIEW *view, GX_EVENT *event_ptr)
{
    switch(event->gx_event_type)
    {
    case GX_EVENT_SHOW:
        gx_multi_line_text_view_event_process(view, event_ptr);
        /* Add custom actions here. */
        break;
    default:
        gx_multi_line_text_view_event_process (view, event_ptr);
        break;
    }
    return GX_SUCCESS;
}
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_font_set"></a>gx_multi_line_text_view_font_set


Definir fonte usada na vista de texto multi-linha

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_view_text_id_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Descrição

Este serviço define a fonte de um widget de visualização de texto multi-linha.

### <a name="parameters"></a>Parâmetros

- **text_view** Bloco de controlo widget de visualização de texto multi-line
- **font_id** ID de recurso para o tipo de letra

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Definir com sucesso a fonte para a vista de texto multi-linha
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set font ID FONT_ID to the multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_font_set(&my_text_view, FONT_ID);

/* If status is GX_SUCCESS, the text view “my_text_view” will use the specified font to display its text. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_line_space_set"></a>gx_multi_line_text_view_line_space_set


Definir espaço de linha de vista de texto multi-linha

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_view_line_space_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_BYTE line_space);
```

### <a name="description"></a>Descrição

Este serviço define o espaçamento entre linhas de texto para o widget de visualização de texto multi-linha.

### <a name="parameters"></a>Parâmetros

- **ver** Bloco de controlo widget de visualização de texto multi-line
- **line_space** Valor a definir

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso o valor do espaço da linha para a vista de texto multi-linha
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

```C
/* Set line space of “my_text_view” to 2. */
status = gx_multi_line_text_view_line_space_set(&my_text_view, 2);

/* If status is GX_SUCCESS, the line space of “my_text_view” has been successfully set to 2. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_scroll_info_get"></a>gx_multi_line_text_view_scroll_info_get

Obtenha informações de pergaminho de visão de texto multi-linha


### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_view_scroll_info_get(
    GX_MULTI_LINE_TEXT_VIEW *text_view, ULONG style,
    GX_SCROLL_INFO *info);
```

### <a name="description"></a>Descrição

Este serviço obtém a informação de visualização de texto multi-linha.

### <a name="parameters"></a>Parâmetros

- **text_view** Bloco de controlo widget de visualização de texto multi-line
- **Estilo** GX_SCROLLBAR_HORIZONTAL ou GX_SCROLLBAR_VERTICAL
- **Informação** Ponteiro para destino para informações de pergaminho. **O apêndice I** contém definição para GX_SCROLL_INFO estrutura.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) recuperou com sucesso a informação do pergaminho da vista de texto
- **GX_FAILURE** (0x10) Widget não é visível ou o id de fonte de vista de texto não é válido
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_SCROLL_INFO scroll_info;

/* Get scroll information for multi-line text view “my_text_view”. */
status = gx_multi_line_text_view_scroll_info_get(&my_text_view,
    &scroll_info);

/* If status is GX_SUCCESS the “scroll_info” contains the scroll information for multi-line text view “my_text_view”. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_text_color_set"></a>gx_multi_line_text_view_text_color_set


Desafase a cor do texto para a vista de texto multi linha

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_view_text_color_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCe_ID disabled_text_color_id);
```

### <a name="description"></a>Descrição

Este serviço atribui a cor de texto ao widget de visualização de texto multi-linha.

### <a name="parameters"></a>Parâmetros

- **text_view** Bloco de controlo widget de visualização de texto multi-line
- **normal_text_color_id** ID de recurso da cor de texto normal que foi usado em estado normal
- **selected_text_color_id** ID de recurso da cor de texto selecionada que usou quando o widget ganha o foco
- **disabled_text_color_id** ID de recursos da cor de texto desativada que usou GX_STYLE_ENABLED não está ativo

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso cores para a vista de texto multi-linha
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set text colors for the multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_text_color_set(&my_text_view,
    GX_COLOR_ID_NORMAL_TEXT,
    GX_COLOR_ID_SELECTED_TEXT,
    GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS the text color of “my_text_view” has been successfully set. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_text_id_set"></a>gx_multi_line_text_view_text_id_set


Definir cadeia de texto do sistema na vista de texto de várias linhas

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_view_text_id_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_RESOURCE_ID text_id);
```

### <a name="description"></a>Descrição

Este serviço define o ID de recurso de uma cadeia para o widget de visualização de texto multi-line.

### <a name="parameters"></a>Parâmetros

- **text_view** Bloco de controlo widget de visualização de texto multi-line
- **text_id** ID de recurso para a cadeia de texto

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Definir com sucesso o id de corda para a vista de texto multi-linha
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **ID** de recursos inválidos de GX_INVALID_RESOURCE_ID (0x33)

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set string ID STRING_ID to the multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_text_id_set(&my_text_view, STRING_ID);

/* If status is GX_SUCCESS the text id of “my_text_view” has been successfully set. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_text_set"></a>gx_multi_line_text_view_text_set


Definir a cadeia definida pelo utilizador na vista de texto de várias linhas

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_view_text_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_CONST GX_CHAR *text);
```

### <a name="description"></a>Descrição

Este serviço atribui uma cadeia de texto ao widget de visualização de texto multi-linha. Se o widget text_view foi criado com GX_STYLE_TEXT_COPY de estilo, o widget cria uma cópia privada da cadeia de texto atribuída, pelo que a API gx_system_memory_allocate_set deve ser invocada uma vez antes deste serviço ser solicitado. Se GX_STYLE_TEXT_COPY não estiver ativa, o widget não faz uma cópia privada da cadeia de entrada, pelo que a cadeia atribuída deve ser estática ou globalmente atribuída, ou seja, pode não ser uma variável automática ou temporária.

### <a name="parameters"></a>Parâmetros

- **text_view** Bloco de controlo widget de visualização de texto multi-line
- **texto** Cadeia de texto terminada nulo

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Definir com sucesso a cadeia para a vista de texto multi-linha
- **GX_SYSTEM_MEMORY_ERROR** (0x30) O alocador de memória não está definido ou a atribuição de memória falhou
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set string “my string” to the multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_text_set(&my_text_view, “my string”);

/* If status is GX_SUCCESS the text of “my_text_view” has been successfully set. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_whitespace_set"></a>gx_multi_line_text_view_whitespace_set


Definir visão de texto multi-linhas espaço em branco

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_view_whitespace_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_UBYTE whitespace);
```

### <a name="description"></a>Descrição

Este serviço define o espaçamento entre os contornos do widget e a área do cliente para um widget de visualização de texto multi-line.

### <a name="parameters"></a>Parâmetros

- **text_view** Bloco de controlo widget de visualização de texto multi-line
- **espaço branco** Largura de margem entre text_view widget e o texto apresentado, em pixels.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso o espaço em branco para a vista de texto multi-linha
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set whitespace of “my_text_view” to 2. */
status = gx_multi_line_text_view_whitespace_set(&my_text_view, 2);

/* If status is GX_SUCCESS the whitespace of “my_text_view” has been successfully set to 2. */
```

### <a name="see-also"></a>Consulte também

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set

## <a name="gx_numeric_pixelmap_prompt_create"></a>gx_numeric_pixelmap_prompt_create


Criar pedido de pixelmap numérico

### <a name="prototype"></a>Prototype

```C
UINT gx_numeric_pixelmap_prompt_create(
    GX_NUMERIC_PIXELMAP_PROMPT *prompt,
    GX_CONST GX_CHAR name, GX_WIDGET *parent,
    GX_RESOURCE_ID text_id, GX_RESOURCE_ID fill_id,
    ULONG style, USHORT pixelmap_prompt_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria um widget de pixelmap numérico. Um numeric_pixelmap_prompt é apenas um pixelmap_prompt que mantém o seu próprio tampão e fornece uma API gx_numeric_pixelmap_prompt_value_set(INT), o tamanho do tampão é definido pelo GX_NUMERIC_PROMPT_BUFFER_SIZE constante, que não chega a 16.

GX_NUMERIC_PIXELMAP_PROMPT é derivado de GX_PIXELMAP_PROMPT e suporta todos os gx_pixelmap_prompt serviços da API.

### <a name="parameters"></a>Parâmetros

- **rápido** Bloco de controlo de solicitação de pixelmap numérico
- **nome** Nome da solicitação
- **pai** Bloco de controlo widget dos pais
- **text_id** Id de cadeia de recursos
- **fill_id** Pixelmap id para área de enchimento
- **estilo** Estilo de pixelmap numérico, **o apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **pixelmap_prompt_id** ID definido pela aplicação de solicitação
- **tamanho** Dimensões do pedido de pixelmap numérico

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Crie com sucesso uma pixlemap numérica
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Create “my_numeric_pix_prompt”. */
status = gx_numeric_pixelmap_prompt_create(&my_numeric_pix_prompt,
    “my_numeric_pix_prompt”, &my_parent,
    MY_TEXT_RESOURCE_ID, MY_FEEL_RESOURCE_ID,
    GX_STYLE_BORDER_RAISED, MY_NUMERIC_PIXELMAP_PROMPT_ID,
    &size);

/* If status is GX_SUCCESS the numeric pixelmap prompt “my_numeric_pix_prompt” has been created. */
```

### <a name="see-also"></a>Consulte também

- gx_numeric_pixelmap_format_function_set
- gx_numeric_pixelmap_prompt_value_set

## <a name="gx_numeric_pixelmap_prompt_format_function_set"></a>gx_numeric_pixelmap_prompt_format_function_set


Função de formato de substituição do pixelmap numérico

### <a name="prototype"></a>Prototype

```C
UINT gx_numeric_pixelmap_format_function_set(
    GX_NUMERIC_PIXELMAP_PROMPT *prompt,
    OID (*format_func)(GX_NUMERIC_PIXELMAP_PROMPT *, INT));
```

### <a name="description"></a>Descrição

Este serviço substitui a função de formato predefinido do widget de pixlemap numérico. A função de formato predefinido converte o valor de pedido de pixelmap numérico para uma cadeia e armazena-o no tampão privado do widget. Este serviço permite que a aplicação defina a sua própria função de formato e armazene o valor de solicitação numérica do pixelmap no tampão privado do widget.

### <a name="parameters"></a>Parâmetros

- **rápido** Bloco de controlo de solicitação de pixelmap numérico
- **format_func** Função de formato a definir

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso a função de formato de pixlemap numérico
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Define my numeric pixelmap format function. */
VOID my_format_function(GX_NUMERIC_PIXELMAP_PROMPT *prompt,
    INT value)
{
    /* If the value is “1234”, the new format will be “12.34”. */

    INT length;
    gx_utility_ltoa(value / 100,
        prompt->gx_numeric_pixelmap_prompt_buffer,
        GX_NUMERIC_PROMPT_ BUFFER_SIZE);
    Length = GX_STRLEN(prompt->gx_numeric_pixelmap_prompt_buffer);
    prompt->gx_numeric_pixelmap_prompt_buffer[length++] = ‘.’;
    gx_utility_ltoa(value % 100,
        prompt->gx_numeric_pixelmap_prompt_buffer + length,
        GX_NUMERIC_PROMPT_BUFFER_SIZE - length);
}

/* Override default format function of “my_numeric_pix_prompt”. */
status = gx_numeric_pixelmap_prompt_format_function_set(
    &my_numeric_pix_prompt,
    my_format_function);

/* If status is GX_SUCCESS the format function of “my_numeric_pix_prompt” has been override. */
```

### <a name="see-also"></a>Consulte também

- gx_numeric_pixelmap_prompt_create
- gx_numeric_pixelmap_prompt_value_set

## <a name="gx_numeric_pixelmap_prompt_value_set"></a>gx_numeric_pixelmap_prompt_value_set


Definir valor rápido numérico de pixlemap

### <a name="prototype"></a>Prototype

```C
UINT gx_numeric_pixelmap_prompt_value_set(
    GX_NUMERIC_PIXELMAP_PROMPT *prompt,
    INT value);
```

### <a name="description"></a>Descrição

Este serviço tem um valor inteiro para um pedido de pixelmap numérico.

### <a name="parameters"></a>Parâmetros

- **rápido** Bloco de controlo de solicitação de pixelmap numérico
- **valor** Valor inteiro a definir

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso o valor de solicitação de pixelmap numérico
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set a value to “my_numeric_pix_prompt”. */
status = gx_numeric_pixelmap_prompt_value_set(&my_numeric_pix_prompt, 1000);

/* If status is GX_SUCCESS the value of the numeric pixelmap prompt “my_numeric_pix_prompt” has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_numeric_pixelmap_prompt_create
- gx_numeric_pixelmap_format_function_set

## <a name="gx_numeric_prompt_create"></a>gx_numeric_prompt_create


Criar um pedido numérico

### <a name="prototype"></a>Prototype

```C
UINT gx_numeric_prompt_create( 
    GX_NUMERIC_PROMPT *prompt,
    GX_CONST GX_CHAR name, GX_WIDGET *parent,
    GX_RESOURCE_ID text_id,
    ULONG style, USHORT prompt_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria um widget numérico. Um numeric_ é apenas uma solicitação que mantém o seu próprio tampão e fornece uma API gx_numeric_ prompt_value_set(INT), o tamanho do tampão é definido pela GX_NUMERIC_PROMPT_BUFFER_SIZE constante, que não chega a 16.

GX_NUMERIC_PROMPT é derivado de GX_PROMPT e suporta todos os gx_prompt serviços da API.

### <a name="parameters"></a>Parâmetros

- **rápido** Bloco de controlo de solicitação numérica
- **nome** Nome da solicitação
- **pai** Bloco de controlo widget dos pais
- **text_id** Id de cadeia de recursos
- **estilo** Estilo de solicitação numérica, **o Apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **prompt_id** ID definido pela aplicação de solicitação
- **tamanho** Dimensões da solicitação numérica

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Com sucesso creat numérico
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Create “my_numeric _prompt”. */
status = gx_numeric_prompt_create(&my_numeric_prompt,
    “my_numeric_prompt”, &my_parent,
    MY_TEXT_RESOURCE_ID, GX_STYLE_BORDER_RAISED, MY_NUMERIC_PROMPT_ID,
    &size);

/* If status is GX_SUCCESS the numeric prompt “my_numeric_prompt” has been created. */
```

### <a name="see-also"></a>Consulte também

- gx_numeric_format_function_set
- gx_numeric_prompt_value_set

## <a name="gx_numeric_prompt_format_function_set"></a>gx_numeric_prompt_format_function_set


Função de formato de substituição de solicitação numérica

### <a name="prototype"></a>Prototype

```C
UINT gx_numeric_format_function_set(
    GX_NUMERIC_PROMPT *prompt,
    VOID (*format_func)(GX_NUMERIC_PROMPT *, INT));
```

### <a name="description"></a>Descrição

Este serviço substitui a função de formato predefinido de um widget numérico. A função de formato predefinido converte o valor de solicitação numérica a uma corda e armazena-a no tampão privado do widget. Este serviço permite que a aplicação defina a sua própria função de formato para formato e armazenar o valor numérico de solicitação no tampão privado do widget.

### <a name="parameters"></a>Parâmetros

- **rápido** Bloco de controlo de solicitação numérica
- **format_func** Função de formato a definir

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso a função de formato de solicitação numérica
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Define my numeric format function. */
VOID my_format_function(GX_NUMERIC_PROMPT *prompt, INT value)
{
    /* If the value is “1234”, the new format will be “12.34”. */

    INT length;
    gx_utility_ltoa(value / 100, prompt->gx_numeric_prompt_buffer,
        GX_NUMERIC_PROMPT_ BUFFER_SIZE);
    Length = GX_STRLEN(prompt->gx_numeric_prompt_buffer);
    prompt->gx_numeric_prompt_buffer[length++] = ‘.’;
    gx_utility_ltoa(value % 100,
        prompt->gx_numeric_prompt_buffer + length,
        GX_NUMERIC_PROMPT_BUFFER_SIZE - length);
}

/* Override the default format function of “my_numeric_prompt”. */
status = gx_numeric_prompt_format_function_set(&my_numeric_prompt,
    my_format_function);

/* If status is GX_SUCCESS, the format function of “my_numeric_prompt” has been override. */
```

### <a name="see-also"></a>Consulte também

- gx_numeric_prompt_create
- gx_numeric_prompt_value_set

## <a name="gx_numeric_prompt_value_set"></a>gx_numeric_prompt_value_set


Definir valor de solicitação numérica

### <a name="prototype"></a>Prototype

```C
UINT gx_numeric_prompt_value_set(
    GX_NUMERIC_PROMPT *prompt, 
    INT value);
```

### <a name="description"></a>Descrição

Este serviço define um valor inteiro para um pedido numérico.

### <a name="parameters"></a>Parâmetros

- **rápido** Bloco de controlo de solicitação numérica
- **valor** Valor inteiro a definir

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso o valor de origem numérica
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set a value to “my_numeric_prompt”. */
status = gx_numeric_prompt_value_set(&my_numeric_prompt, 1000);

/* If status is GX_SUCCESS the value of the numeric prompt “my_numeric_prompt” has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_numeric_prompt_create
- gx_numeric_format_function_set

## <a name="gx_numeric_scroll_wheel_create"></a>gx_numeric_scroll_wheel_create


Criar roda de pergaminho numérico

### <a name="prototype"></a>Prototype


UINT gx_numeric_scroll_wheel_create, GX_NUMERIC_SCROLL_WHEEL *roda, GX_CONST GX_CHAR *nome, GX_WIDGET *pai, INT start_val, INT end_val, estilo ULONG, USHORT wheel_id, GX_CONST GX_RECTANGLE *tamanho);

### <a name="description"></a>Descrição

Este serviço cria um widget de roda de deslocal numérico.

Uma roda de deslocamento numérico é um tipo de widget de roda de deslocamento que é especificamente utilizado para exibir uma gama de números. Outros tipos de widgets de roda de deslocação também estão disponíveis. Consulte a API gx_scroll_wheel_create para obter mais informações sobre a hierarquia do widget da roda de deslocação, os tipos de widgets e a derivação do widget.

GX_NUMERIC_SCROLL_WHEEL é derivado de GX_TEXT_SCROLL_WHEEL e apoia todos os serviços gx_text_scroll_wheel e gx_scroll_wheel.

Todos os tipos de rodas de deslocação geram eventos GX_EVENT_LIST_SELECT para os seus pais quando a roda de deslocação é deslocalizada.

Uma roda de deslocação numérica não terá abdominais (end_val – start_val) + 1 linhas. Por outras palavras, a roda de deslocação mostrará todos os valores entre start_val e end_val, incrementando ou diminuindo por 1 a cada linha. Note que start_val pode ser maior ou inferior a end_val, dependendo da forma como a aplicação quer que o intervalo apareça.

Se a aplicação quiser alterar o incremento da linha, pode fazê-lo chamando gx_scroll_wheel_total_rows_set() depois de criar a roda de deslocamento numérico. Por exemplo, uma aplicação que pretenda criar uma roda de deslocação que apresente os valores anos 1980-2020, incrementando por 5, pode fazê-lo:

```C
gx_numeric_scroll_wheel_create(&wheel, GX_NULL, parent, 1980,
    2020, style, id, &size);

/* the years 1980 through 2020, inclusive, incrementing by 5 years,
yields 9 total rows */

gx_scroll_wheel_total_rows_set(&wheel, 9);
```

### <a name="parameters"></a>Parâmetros

- **roda** Ponteiro para bloco de controlo da roda de deslocação numérica
- **nome** Nome lógico do widget do botão pixelmap
- **pai** Ponteiro para o widget dos pais
- **start_val** Valor numérico inicial
- **end_val** Fim do valor numérico
- **estilo** Estilo de caixa de verificação. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **wheel_id** ID definido pela aplicação da roda de pergaminho
- **tamanho** Dimensões do widget da roda de pergaminho

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) criou com sucesso uma roda de pergaminho numérico
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Create “year_wheel”. */
status = gx_numeric_scroll_wheel_create(&year_wheel,
    “year_selector””, &parent,
    1980, 2040,
    GX_STYLE_ENABLED | GX_STYLE_TEXT_CENTER |
    GX_STYLE_TRANSPARENT | GX_STYLE_WRAP |
    GX_STYLE_TEXT_SCROLL_WHEEL_ROUND,
    YEAR_WHEEL_ID,
    &size);

/* If status is GX_SUCCESS the scroll wheel “year_wheel” has been created. */
```

### <a name="see-also"></a>Consulte também

- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_text_get

## <a name="gx_numeric_scroll_wheel_range_set"></a>gx_numeric_scroll_wheel_range_set


Atribua gama de valor da roda de pergaminho numérico

### <a name="prototype"></a>Prototype

```C
UINT
gx_numeric_scroll_wheel_range_set(
    GX_NUMERIC_SCROLL_WHEEL *wheel,
    INT start_val, INT end_val);
```

### <a name="description"></a>Descrição

Este serviço modifica a gama de valores permitidos e exibidos por um widget de roda de deslocação numérica.

Uma roda de deslocamento numérico é um tipo de widget de roda de deslocamento que é especificamente utilizado para exibir uma gama de números. Outros tipos de widgets de roda de deslocação também estão disponíveis. Consulte a API gx_scroll_wheel_create para obter mais informações sobre a hierarquia do widget da roda de deslocação, os tipos de widgets e a derivação do widget.

Invocando esta API, a roda de deslocação volta a abdómen (end_val – start_val) + 1, o que significa que a roda de deslocação irá aumentar em 1 para cada linha. Para alterar isto, a aplicação pode chamar gx_scroll_wheel_total_rows_set() para alterar o número total de linhas, alterando efetivamente o incremento de valor entre linhas.

### <a name="parameters"></a>Parâmetros

- **roda** Ponteiro para bloco de controlo da roda de deslocação numérica
- **start_val** Valor numérico inicial 
- **end_val** Fim do valor numérico

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso a gama de rodas de deslocal numérico
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_CALLER_ERROR** (0x11) Inválido desta função

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios 

### <a name="example"></a>Exemplo

```C
/* Change range of “rate” scroll wheel. */

status = gx_numeric_scroll_wheel_range_set(&year_wheel, 0, 200);

/* If status is GX_SUCCESS the scroll wheel range has been modified. */
```

### <a name="see-also"></a>Consulte também

- gx_numeric_scroll_wheel_create
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_pixelmap_button_create"></a>gx_pixelmap_button_create


Criar botão pixelmap

### <a name="prototype"></a>Prototype

```C
UINT gx_pixelmap_button_create(
    GX_PIXELMAP_BUTTON *button,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID normal_id,
    GX_RESOURCE_ID selected_id,
    GX_RESOURCE_ID disabled_id,
    ULONG style,
    USHORT pixelmap_button_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria um widget de botão pixelmap.

GX_PIXELMAP_BUTTON é derivado de GX_BUTTON e apoia todos os serviços gx_button.

### <a name="parameters"></a>Parâmetros

- **botão** Ponteiro para bloco de controlo de botões pixelmap
- **nome** Nome lógico do widget do botão pixelmap
- **pai** Ponteiro para o widget dos pais
- **normal_id** ID de recursos do estado normal
- **selected_id** ID de recursos do estado selecionado
- **disabled_id** ID de recursos do estado desativado
- **estilo** Estilo de caixa de verificação. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **pixelmap_button_id** ID definido pela aplicação do botão pixelmap
- **tamanho** Dimensões do botão pixelmap

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) criou com sucesso o botão pixelmap
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Create “my_pixelmap_button”. */
status = gx_pixelmap_button_create(&my_pixelmap_button,
    “my_pixelmap_button”, &my_parent,
    MY_NORMAL_RESOURCE_ID, MY_SELECTED_RESOURCE_ID,
    MY_DESELECTED_RESOURCE_ID, GX_STYLE_BORDER_RAISED,
    MY_PIXELMAP_BUTTON_ID,
    &size);

/* If status is GX_SUCCESS the pixelmap button “my_pixelmap_button” has been created. */
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_draw
- gx_pixelmap_button_pxielmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_button_draw"></a>gx_pixelmap_button_draw


Desenhe o botão pixelmap

### <a name="prototype"></a>Prototype

```C
VOID gx_pixelmap_button_draw(GX_PIXELMAP_BUTTON *button);
```

### <a name="description"></a>Descrição

Este serviço desenha um widget de botão pixelmap. Esta função é normalmente chamada internamente pelo mecanismo de atualização de lona GUIX, mas está exposta à aplicação para ajudar na implementação de funções de desenho personalizado para widgets de botões pixelmap personalizados.

### <a name="parameters"></a>Parâmetros

- **botão** Ponteiro para bloco de controlo de botões pixelmap

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom pixelmap button drawing function. */

VOID my_pixelmap_button_draw(GX_PIXELMAP_BUTTON *button)
{
    /* Call default pixelmap button draw. */
    gx_pixelmap_button_draw(button);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_pxielmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_button_event_process"></a>gx_pixelmap_button_event_process


Processamento de eventos de botão Pixelmap

### <a name="prototype"></a>Prototype

```C
UINT gx_pixelmap_button_event_process(
    GX_PIXELMAP_BUTTON *button,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Descrição

Este serviço fornece o manuseamento predefinido do evento para o tipo de widget de botão pixelmap.

### <a name="parameters"></a>Parâmetros

- **botão** Ponteiro para bloco de controlo de botões pixelmap
- **event_ptr** Ponteiro para GX_EVENT estrutura

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Sorteio bem sucedido do botão pixelmap
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
switch(event_ptr->gx_event_type)
{
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_pixelmap_button_event_process(icon, event_ptr);
    
        /* add my own handling here */
        break;
}
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_pxielmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_button_pixelmap_set"></a>gx_pixelmap_button_pixelmap_set


Atribuir pixelmaps ao botão

### <a name="prototype"></a>Prototype

```C
UINT gx_pixelmap_button_pixelmap_set(
    GX_PIXELMAP_BUTTON *button, 
    GX_RESOURCE_ID normal_id,
    GX_RESOURCE_ID selected_id, 
    GX_RESOURCE_ID disabled_id);
```

### <a name="description"></a>Descrição

Este serviço define pixelmaps para o botão pixelmap.

### <a name="parameters"></a>Parâmetros

- **botão** Ponteiro para bloco de controlo de botões pixelmap
- **normal_id** ID de recursos do pixelmap para ser usado como estado normal
- **selected_id** ID de recursos do pixelmap a ser usado quando o botão é selecionado
- **disabled_id** ID de recursos do pixelmap a ser usado quando o botão é desativado

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) O sucesso define o pixelmap para o botão
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Draw “my_pixelmap_button”. */
status = gx_pixelmap_button_pixelmap_set (&my_pixelmap_button,
    NORMAL_ID, SELECTED_ID,
    DISABLED_ID);

/* If status is GX_SUCCESS the pixelmap button is properly configured with the specified pixelmaps. */
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_prompt_create"></a>gx_pixelmap_prompt_create


Criar pixelmap

### <a name="prototype"></a>Prototype

```C
UINT gx_pixelmap_prompt_create(
    GX_PIXELMAP_PROMPT *prompt,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id,
    GX_RESOURCE_ID fill_pixelmap_id,
    ULONG style,
    USHORT pixelmap_prompt_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria um widget de solicitação pixelmap. Uma solicitação de pixelmap difere de um GX_PROMPT padrão na medida em que pinta o fundo da solicitação usando pixelmaps. A função de criação aceita um id pixelmap, o mapa de pixels de preenchimento de estado normal. Até seis pixelmaps podem ser atribuídos à solicitação pixelmap.

### <a name="parameters"></a>Parâmetros

- **rápido** Ponteiro para bloco de controlo de solicitação pixelmap
- **nome** Nome lógico do widget de solicitação pixelmap
- **pai** Ponteiro para o widget dos pais
- **text_id** ID de recursos de texto
- **fill_id** ID de recursos de preenchimento
- **estilo** Estilo de caixa de verificação. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **pixelmap_prompt_id** ID definido pela aplicação do pixelmap
- **tamanho** Dimensões do pixelmap prompt

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Criação de pedido de pixelmap bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Create “my_pixelmap_prompt”. */
status = gx_pixelmap_prompt_create(&my_pixelmap_prompt,
    “my_pixelmap_prompt”, &my_parent,
    MY_TEXT_RESOURCE_ID, MY_LEFT_RESOURCE_ID,
    MY_FILL_RESOURCE_ID, MY_RIGHT_RESOURCE_ID,
    GX_STYLE_BORDER_RAISED, MY_PIXELMAP_PROMPT_ID,
    &size);

/* If status is GX_SUCCESS the pixelmap prompt “my_pixelmap_prompt” has been created. */
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_set

## <a name="gx_pixelmap_prompt_draw"></a>gx_pixelmap_prompt_draw


Desenhe o pixelmap

### <a name="prototype"></a>Prototype

```C
VOID gx_pixelmap_prompt_draw(GX_PIXELMAP_PROMPT *prompt);
```

### <a name="description"></a>Descrição

Este serviço desenha um widget de solicitação pixelmap. Esta função é normalmente chamada internamente pelo mecanismo de atualização de lona GUIX, mas está exposta à aplicação para ajudar na implementação de funções de desenho personalizado para widgets de pixelmap personalizados.

### <a name="parameters"></a>Parâmetros

- **rápido** Ponteiro para bloco de controlo de solicitação pixelmap

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Write a custom pixelmap prompt drawing function. */

VOID my_pixelmap_button_draw(GX_PIXELMAP_PROMPT *prompt)
{
    /* Call default pixelmap prompt draw. */
    gx_pixelmap_prompt_draw(prompt);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_set

## <a name="gx_pixelmap_prompt_pixelmap_set"></a>gx_pixelmap_prompt_pixelmap_set


Atribuir pixelmaps para solicitar

### <a name="prototype"></a>Prototype

```C
UINT gx_pixelmap_prompt_pixelmap_set(
    GX_PIXELMAP_PROMPT *prompt,
    GX_RESOURCE_ID normal_left_pixelmap,
    GX_RESOURCE_ID normal_fill_pixelmap,
    GX_RESOURCE_ID normal_right_pixelmap,
    GX_RESOURCE_ID selected_left_pixelmap,
    GX_RESOURCE_ID selected_fill_pixelmap,
    GX_RESOURCE_ID selected_right_pixelmap);
```

### <a name="description"></a>Descrição

Este serviço atribui ids pixelmap à solicitação pixelmap. Os ids pixelmap esquerdo, preenchido e direito são usados para permitir que a aplicação use um conjunto de pixelmaps para solicitações de várias larguras, mas uma altura comum para economizar nos requisitos de armazenamento. Se os IDs esquerdo e direito não forem utilizados, devem ser definidos para 0. Se a solicitação se desenergem de forma diferente quando ganha o foco de entrada, os ids pixelmap selecionados são utilizados para o efeito. Se os ids selecionados não forem utilizados ou forem os mesmos que os ids normais, desa coloca-os em 0.

### <a name="parameters"></a>Parâmetros

- **rápido** Ponteiro para bloco de controlo de solicitação pixelmap
- **normal_left_id** ID de recursos do pixelmap a ser usado no lado esquerdo no estado normal
- **normal_fill_id** ID de recursos do mapa de pixels para ser usado como um enchimento de azulejos no estado normal
- **normal_right_id** ID de recursos do pixelmap a ser usado no lado direito no estado normal
- **selected_left_id** ID de recursos do pixelmap a ser usado no lado esquerdo no estado selecionado
- **selected_fill_id** ID de recursos do pixelmap para ser usado como um preenchimento de azulejos no estado selecionado
- **selected_right_id** ID de recursos do pixelmap a ser usado no lado direito no estado selecionado

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) O sucesso define o pixelmap ao pedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **ID** de recursos GX_INVALID_RESOURCE_ID (0x33) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Assign pixelmap IDs to “my_prompt”. Only the normal state pixelmaps are used in this case */
status = gx_pixelmap_prompt_pixelmap_set (&my_prompt,
    normal_left_id, normal_fill_id,
    normal_right_id, 0, 0, 0);

/* If status is GX_SUCCESS the pixelmap prompt is properly configured with pixelmaps. */
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_slider_create"></a>gx_pixelmap_slider_create


Criar slider de mapas de pixel

### <a name="prototype"></a>Prototype

```C
UINT gx_pixelmap_slider_create(
    GX_PIXELMAP_SLIDER *slider,
    GX_CONST GX_CHAR *name, GX_WIDGET *parent,
    GX_SLIDER_INFO *info,
    GX_PIXELMAP_SLIDER_INFO *pixelmap_info, ULONG style,
    USHORT pixelmap_slider_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria um widget de slider pixelmap.

### <a name="parameters"></a>Parâmetros

- **slider** Ponteiro para bloco de controlo do slider pixelmap
- **nome** Nome lógico do widget de slider pixelmap
- **pai** Ponteiro para o widget dos pais
- **informação** Ponteiro para uma estrutura GX_SLIDER_INFO que contenha valores que definam o valor mínimo do deslizador, o valor máximo, o valor atual e os limites da agulha. **O apêndice I** contém definição para GX_SLIDER_INFO estrutura.
- **pixelmap_info** Ponteiro para uma estrutura GX_PIXELMAP_SLIDER_INFO que define as pixelmaps utilizadas para desenhar o fundo e a agulha deslizantes. **O apêndice I** contém definição para GX_PIXELMAP_SLIDER_INFO estrutura. O fundo do slider pode usar uma ou duas pixelmaps. Se um, o fundo não muda à medida que a agulha se move. Se forem definidos dois fundos, o fundo antes da agulha usa o primeiro mapa de pixels de fundo, e o fundo após a agulha usa o segundo pixelmap de fundo.
- **estilo** Estilo de slider. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **pixelmap_slider_id** ID definido pela aplicação do slider pixelmap
- **tamanho** Dimensões do pixelmap prompt

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) criou com sucesso o slider pixelmap
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_SLIDER_INFO info;
GX_PIXELMAP_SLIDER_INFO pixelmap_info;

/* Initiate slider information structure. */
info.gx_slider_info_min_val = 0;
info.gx_slider_info_max_val = 100;
info.gx_slider_info_current_val = 50;
info.gx_slider_info_min_travel = 10;
info.gx_slider_info_max_tralvel = 10;
info.gx_slider_info_needle_width = 5;
info.gx_slider_info_needle_height = 10;
info.gx_slider_info_needle_inset = 5;
info.gx_slider_info_needle_hotspot_offset;

/* Initiate pixelmap slider information structure. */
pixelmap_info.gx_pixelmap_slider_info_lower_background_pixelmap =
                                        GX_PIXELMAP_ID_ORANGE;
pixelmap_info.gx_pixelmap_slider_info_upper_background_pixelmap =
                                        GX_PIXELMAP_ID_EMPTY;
pixelmap_info.gx_pixelmap_slider_info_needle_pixelmap =
                                        GX_PIXELMAP_ID_NEEDLE;

/* Create “my_pixelmap_slider”. */
status = gx_pixelmap_slider_create(&my_pixelmap_slider,
                            “my_pixelmap_slider”, &my_parent,
                            &info, &pixelmap_info,
                            GX_STYLE_BORDER_RAISED,
                            MY_PIXELMAP_SLIDER_ID, &size);

/* If status is GX_SUCCESS the pixelmap slider “my_pixelmap_slider” has been created. */
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_pixelmap_slider_draw"></a>gx_pixelmap_slider_draw


Desenhe o slider do pixelmap

### <a name="prototype"></a>Prototype

```C
VOID gx_pixelmap_slider_draw(GX_PIXELMAP_SLIDER *slider);
```

### <a name="description"></a>Descrição

Este serviço desenha um widget de slider pixelmap. Esta função é normalmente chamada internamente pelo mecanismo de atualização de lona GUIX, mas está exposta à aplicação para ajudar na implementação de funções de desenho personalizado para widgets de slider de pixelmap personalizados.

### <a name="parameters"></a>Parâmetros

- **slider** Ponteiro para bloco de controlo do slider pixelmap

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom pixelmap slider drawing function. */

VOID my_pixelmap_slider_draw(GX_PIXELMAP_SLIDER *pixelmap_slider)
{
    /* Call default pixelmap slider draw. */
    gx_pixelmap_slider_draw(pixelmap_slider);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_pixelmap_slider_event_process"></a>gx_pixelmap_slider_event_process


Evento de slider de pixelmap de processo

### <a name="prototype"></a>Prototype

```C
UINT gx_pixelmap_slider_event_process(
    GX_PIXELMAP_SLIDER *slider,
    GX_EVENT *event);
```

### <a name="description"></a>Descrição

Este serviço processa um evento para o widget de slider pixelmap especificado.

### <a name="parameters"></a>Parâmetros

- **slider** Ponteiro para pixelmap
- **slider** controlo evento ponto para evento para processar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Processo de evento de slider de pixelmap bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Write a custom event processing function. */
UINT my_event_hanlder(GX_PIXELMAP_SLIDER *pixelmap_slider, GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_pixelmap_slider_event_process(pixelmap_slider,
                                                    event_ptr);

        /* add my own handling here */
        break;
    default:
        status = gx_pixelmap_slider_event_process(pixelmap_slider,
                                                  event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_pixelmap_slider_pixelmap_set"></a>gx_pixelmap_slider_pixelmap_set


Atribuir pixelmaps para slider

### <a name="prototype"></a>Prototype

```C
UINT gx_pixelmap_slider_pixelmap_set(
    GX_PIXELMAP_SLIDER *slider,
    GX_PIXELMAP_SLIDER_INFO *pixinfo);
```

### <a name="description"></a>Descrição

Este serviço define pixelmaps para o slider pixelmap.

### <a name="parameters"></a>Parâmetros

- **slider** Ponteiro para bloco de controlo do slider pixelmap
- **pixinfo** Ponteiro para uma estrutura GX_PIXELMAP_SLIDER_INFO que define as pixelmaps utilizadas para desenhar o fundo e a agulha deslizantes. **O apêndice I** contém definição para GX_PIXELMAP_SLIDER_INFO estrutura. O fundo do slider pode usar uma ou duas pixelmaps. Se um, o fundo não muda à medida que a agulha se move. Se forem definidos dois fundos, o fundo antes da agulha usa o primeiro mapa de pixels de fundo, e o fundo após a agulha usa o segundo pixelmap de fundo.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) O sucesso define o pixelmap para o slider
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_PIXELMAP_SLIDER_INFO pixelmap_info;

/* Initiate pixelmap slider information structure. */
pixelmap_info.gx_pixelmap_slider_info_lower_background_pixelmap =
                                        GX_PIXELMAP_ID_ORANGE;
pixelmap_info.gx_pixelmap_slider_info_upper_background_pixelmap =
                                        GX_PIXELMAP_ID_EMPTY;
pixelmap_info.gx_pixelmap_slider_info_needle_pixelmap =
                                        GX_PIXELMAP_ID_NEEDLE;

/* Draw “my_pixelmap_button”. */
status = gx_pixelmap_slider _pixelmap_set (&my_pixelmap_slider,
                                &pixelmap_info);

/* If status is GX_SUCCESS the pixelmap slider is properly configured with “pixelmap_info”. */
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_progress_bar_background_draw"></a>gx_progress_bar_background_draw


Desenhar fundo de barra de progresso

### <a name="prototype"></a>Prototype

```C
VOID gx_progress_bar_background_draw(GX_PROGRESS_BAR *progress_bar)
```

### <a name="description"></a>Descrição

Este serviço desenha o pano de fundo da barra de progresso especificada. Esta função é chamada internamente como parte do gx_progress_bar_draw,, mas está exposta à aplicação de suporte aos casos em que a aplicação define uma função de desenho de barra de progresso personalizada.

### <a name="parameters"></a>Parâmetros

- **barra de progresso** Ponteiro para o bloco de controlo da barra de progresso

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom progress bar drawing function. */

VOID my_progress_bar_draw(GX_PROGRESS_BAR *progress_bar)
{
    /* Call default progress bar background draw. */
    gx_progress_bar_background_draw(progress_bar);

    /* Call default progress bar text draw. */
    gx_progress_bar_text_draw(progress_bar);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_progress_bar_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_value_set

## <a name="gx_progress_bar_create"></a>gx_progress_bar_create


Criar uma barra de progresso

### <a name="prototype"></a>Prototype

```C
UINT gx_progress_bar_create(
    GX_PROGRESS_BAR *progress_bar,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_PROGRESS_BAR_INFO *progress_bar_info,
    ULONG style, 
    USHORT progress_bar_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria um widget de barra de progresso.

### <a name="parameters"></a>Parâmetros

- **progress_bar** Bloco de controlo da barra de progresso
- **nome** Nome lógico
- **pai** Ponteiro para o widget dos pais
- **progress_bar_info** Ponteiro para uma estrutura GX_PROGRESS_BAR_INFO. **O apêndice I** contém definição para GX_PROGRESS_BAR_INFO estrutura.
- **estilo** Estilo de barra de progresso. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **progress_bar_id** ID definido pela aplicação da barra de progresso
- **tamanho** Dimensões da barra de progresso

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Barra de progresso bem sucedida criar
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido
- **GX_INVALID_WIDGET** (0x12) Widget dos pais não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_PROGRESS_BAR_INFO info;
GX_RECTANGLE size;

info.gx_progress_bar_info_min_val = 0;
info.gx_progress_bar_info_max_val = 100;
info.gx_progress_bar_info_current_val = 0;
info.gx_progress_bar_font_id = GX_FONT_ID_SYSTEM_FONT;
info.gx_progress_bar_normal_text_color = GX_COLOR_ID_WHITE;
info.gx_progress_bar_selected_text_color = GX_COLOR_ID_BLUE;
info.gx_progress_bar_fill_pixelmap = 0;

size.gx_rectangle_left = 10;
size.gx_rectangle_top = 10;
size.gx_rectangle_right = 110;
size.gx_rectangle_bottom = 140;

/* Create a progress bar with the specified information. */
status = gx_progress_bar_create(&my_progress_bar, GX_NULL, GX_NULL,
                        &info, GX_STYLE_BORDER_THIN,
                        0, &size);

/* If status is GX_SUCSESS the progress bar “my_progress_bar” has been successfully created. */
```

### <a name="see-also"></a>Consulte também

- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_draw"></a>gx_progress_bar_draw


Desenhar uma barra de progresso

### <a name="prototype"></a>Prototype

```C
VOID gx_progress_bar_draw(GX_PROGRESS_BAR *progress_bar);
```

### <a name="description"></a>Descrição

Este serviço desenha um widget de barra de progresso. Esta função é normalmente chamada internamente pelo mecanismo de atualização de lona GUIX, mas está exposta à aplicação para ajudar na implementação de funções de desenho personalizado para widgets de barras de progresso personalizados.

### <a name="parameters"></a>Parâmetros

- **progress_bar** Bloco de controlo da barra de progresso

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom progress bar drawing function. */

VOID my_progress_bar_draw(GX_PROGRESS_BAR *progress_bar)
{
    /* Call default progress bar draw. */
    gx_progress_bar_draw(progress_bar);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_progress_bar_create
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_event_process"></a>gx_progress_bar_event_process


Progredir num evento de barras de progresso

### <a name="prototype"></a>Prototype

```C
UINT gx_progress_bar_event_process(
    GX_PROGRESS_BAR *progress_bar,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Descrição

Este serviço processa um evento de barras de progresso.

### <a name="parameters"></a>Parâmetros

- **progress_bar** Bloco de controlo da barra de progresso
- **event_ptr** Ponteiro para GX_EVENT estrutura

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Criação rápida bem sucedida
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **widget** GX_INVALID_WIDGET (0x12) Inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Write a custom event processing function. */

UINT my_event_process (GX_PROGRESS_BAR *progress_bar, GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_progress_bar_event_process(progress_bar,
                                                event_ptr);
        /* add my own handling here */
        break;
    default:
        status = gx_progress_bar_event_process(progress_bar,
                                                event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Consulte também

- gx_progress_bar_create
- gx_progress_bar_event_draw
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_font_set"></a>gx_progress_bar_font_set


Fonte de conjunto de texto de barra de progresso

### <a name="prototype"></a>Prototype

```C
UINT gx_progress_bar_font_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Descrição

Este serviço define a fonte de um widget de barra de progresso.

### <a name="parameters"></a>Parâmetros

- **progress_bar** Bloco de controlo da barra de progresso
- **font_id** Id de recursos de fonte

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de fontes de barra de progresso bem sucedida
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
UINT status = gx_progress_bar_font_set(&progress_bar,
                                        GX_FONT_ID_MEDIUM);

/* if status is GX_SUCCESS, the font was successfully assigned. */
```

### <a name="see-also"></a>Consulte também

- gx_progress_bar_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_info_set"></a>gx_progress_bar_info_set


Definir estrutura de informação de barra de progresso

### <a name="prototype"></a>Prototype

```C
UINT gx_progress_bar_info_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_PROGRESS_BAR_INFO *info);
```

### <a name="description"></a>Descrição

Este serviço repõe a estrutura de informação de um widget de barra de progresso.

### <a name="parameters"></a>Parâmetros

- **progress_bar** Bloco de controlo da barra de progresso
- **informação** Ponteiro para uma estrutura GX_PROGRESS_BAR_INFO. **O apêndice I** contém definição para GX_PROGRESS_BAR_INFO estrutura.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) reiniciam com sucesso a informação da barra de progresso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_PROGRESS_BAR_INFO info;

info.gx_progress_bar_info_min_val = 0;
info.gx_progress_bar_info_max_val = 100;
info.gx_progress_bar_info_current_val = 0;
info.gx_progress_bar_font_id = GX_FONT_ID_SYSTEM_FONT;
info.gx_progress_bar_normal_text_color = GX_COLOR_ID_WHITE;
info.gx_progress_bar_selected_text_color = GX_COLOR_ID_BLUE;
info.gx_progress_bar_fill_pixelmap = 0;

status = gx_progress_bar_info_set(&progress_bar, &info);

/* if status == GX_SUCCESS the progress bar info was re-assigned. */
```

### <a name="see-also"></a>Consulte também

- gx_progress_bar_info_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_pixelmap_set"></a>gx_progress_bar_pixelmap_set


Definir pixelmap usado para desenhar barra de progresso

### <a name="prototype"></a>Prototype

```C
UINT gx_progress_bar_pixelmap_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID pixelmap_id);
```

### <a name="description"></a>Descrição

Este serviço define o pixelmap utilizado para preencher o fundo da barra de progresso.

### <a name="parameters"></a>Parâmetros

- **progress_bar** Bloco de controlo da barra de progresso
- **pixelmap_id** Id de recursos Pixelmap

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de pixelmap de barras de progresso bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
UINT status = gx_progress_bar_pixelmap_set(&progress_bar,
                                GX_PIXELMAP_ID_PROGRESS_FILL);

/* if status is GX_SUCCESS, the pixelmap was successfully assigned. */
```

### <a name="see-also"></a>Consulte também

- gx_progress_bar_pielmap_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_range_set"></a>gx_progress_bar_range_set


Definir intervalo de valor de uma barra de progresso

### <a name="prototype"></a>Prototype

```C
UINT gx_progress_bar_range_set(
    GX_PROGRESS_BAR *progress_bar,
    INT min_value, 
    INT max_value);
```

### <a name="description"></a>Descrição

Este serviço define a gama de valor da barra de progresso.

### <a name="parameters"></a>Parâmetros

- **progress_bar** Bloco de controlo da barra de progresso
- **min_value** Valor mínimo da barra de progresso
- **max_value** Valor máximo da barra de progresso

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de gama de barras de progresso bem-sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
UINT status = gx_progress_bar_range_set(progress_bar, 0, 100);

/* if status is GX_SUCCESS, the progress bar range was successfully assigned. */
```

### <a name="see-also"></a>Consulte também

- gx_progress_bar_range_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_text_color_set"></a>gx_progress_bar_text_color_set


Definir a cor de texto de uma barra de progresso

### <a name="prototype"></a>Prototype

```C
UINT gx_progress_bar_text_color_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID normal_text_color,
    GX_RESOURCE_ID selected_text_color,
    GX_RESOURCE_ID disabled_text_color);
```

### <a name="description"></a>Descrição

Este serviço define a cor de texto de um widget de barra de progresso.

### <a name="parameters"></a>Parâmetros

- **progress_bar** Bloco de controlo da barra de progresso
- **normal_text_color** ID de recurso da cor de texto normal que usado em estado normal
- **selected_text_color** ID de recurso da cor de texto selecionada que usou quando o widget ganha o foco
- **disabled_text_color** ID de recursos da cor de texto desativada que foi usada quando GX_STYLE_ENABLED não está ativa

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de cores de texto de barra de progresso bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set text colors for the progress bar “my_progress_bar”*/
UINT status = gx_progress_bar_text_color_set(&my_progress_bar,
                        GX_COLOR_ID_NORMAL_TEXT,
                        GX_COLOR_ID_SELECTED_TEXT,
                        GX_COLOR_ID_DISABLED_TEXT);

/* if status is GX_SUCCESS, the progress bar text colors were successfully assigned. */
```

### <a name="see-also"></a>Consulte também

- gx_progress_bar_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_text_draw"></a>gx_progress_bar_text_draw


Desenhar texto de barra de progresso

### <a name="prototype"></a>Prototype

```C
VOID gx_progress_bar_text_draw(GX_PROGRESS_BAR *progress_bar)
```

### <a name="description"></a>Descrição

Este serviço desenha o texto da barra de progresso especificada. Esta função é chamada internamente como parte do gx_progress_bar_draw,, mas está exposta à aplicação de suporte aos casos em que a aplicação define uma função de desenho de barra de progresso personalizada.

### <a name="parameters"></a>Parâmetros

- **barra de progresso** Ponteiro para o bloco de controlo da barra de progresso

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom progress bar drawing function. */

VOID my_progress_bar_draw(GX_PROGRESS_BAR *progress_bar)
{
    /* Call default progress bar background draw. */
    gx_progress_bar_background_draw(progress_bar);

    /* Call default progress bar text draw. */
    gx_progress_bar_text_draw(progress_bar);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_progress_bar_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_value_set

## <a name="gx_progress_bar_value_set"></a>gx_progress_bar_value_set


Definir o valor atual de uma barra de progresso

### <a name="prototype"></a>Prototype

```C
UINT gx_progress_bar_value_set(
    GX_PROGRESS_BAR *progress_bar,
    INT value);
```

### <a name="description"></a>Descrição

Este serviço atribui o valor atual da barra de progresso. O widget da barra de progresso invalida-se automaticamente e redesenhar-se-á quando o valor da barra de progresso for alterado.

### <a name="parameters"></a>Parâmetros

- **progress_bar** Bloco de controlo da barra de progresso
- **valor** Valor atual da barra de progresso

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto bem sucedido o valor da barra de progresso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
UINT status = gx_progress_bar_value_set(progress_bar, 50);

/* if status == GX_SUCCESS the progress bar value was successfully assigned. */
```

### <a name="see-also"></a>Consulte também

- gx_progress_bar_value_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw

## <a name="gx_prompt_create"></a>gx_prompt_create


Criar o pedido

### <a name="prototype"></a>Prototype

```C
UINT gx_prompt_create(
    GX_PROMPT *prompt, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    GX_RESOURCE_ID text_id,
    ULONG style, 
    USHORT prompt_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria um widget rápido.

GX_PROMPT é derivado de GX_WIDGET e apoia todos os serviços gx_widget.

### <a name="parameters"></a>Parâmetros

- **Ponteiro** para o widget dos pais
- **text_id** ID de recursos de texto rápido
- **estilo** Estilo de rapidão. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **prompt_id** ID definido pela aplicação de solicitação
- **tamanho** Dimensões da rapidão

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Criação rápida bem sucedida
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Create “my_prompt”. */
status = gx_prompt_create(&my_prompt, “my_promPt”, &my_parent,
                    MY_PROMPT_TEXT_RESOURCE_ID,
                    GX_STYLE_BORDER_RAISED, MY_PROPMT_ID, &size);

/* If status is GX_SUCCESS the prompt “my_prompt” has been created. */
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_draw"></a>gx_prompt_draw


Desenhe o pedido de sorteio

### <a name="prototype"></a>Prototype

```C
VOID gx_prompt_draw(GX_PROMPT *prompt);
```

### <a name="description"></a>Descrição

Este serviço desenha um widget rápido. Este serviço é chamado internamente pelo GUIX durante a atualização de lona, mas também pode ser chamado por funções de desenho personalizado.

### <a name="parameters"></a>Parâmetros

- **rápido** Ponteiro para o bloqueio de controlo de widgets

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom prompt drawing function. */

VOID my_prompt_draw(GX_PROMPT *prompt)
{
    /* Call default prompt draw. */
    gx_prompt_draw(prompt);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_event_process"></a>gx_prompt_event_process


Evento de solicitação de processo

### <a name="prototype"></a>Prototype

```C
UINT gx_prompt_event_process(GX_PROMPT *prompt, GX_EVENT *event_ptr);
```

### <a name="description"></a>Descrição

Este serviço processa um evento para a solicitação especificada. Este serviço deve ser chamado como o manipulador de eventos predefinido por quaisquer funções de processamento de eventos de solicitação personalizadas.

### <a name="parameters"></a>Parâmetros

- **rápido** Ponteiro para bloquear o controlo rápido
- **event_ptr** Ponteiro para o evento para processar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Processo de evento rápido de sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Call generic prompt event processing as part of custom event processing function. */

UINT custom_prompt_event_process(GX_PROMPT *prompt, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default prompt event processing */
        status = gx_prompt_event_process(prompt, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_font_set"></a>gx_prompt_font_set


Definir fonte de origem

### <a name="prototype"></a>Prototype

```C
UINT gx_prompt_font_set(
    GX_PROMPT *prompt, 
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Descrição

Este serviço define a fonte de um widget rápido.

### <a name="parameters"></a>Parâmetros

- **rápido** Ponteiro para o bloqueio de controlo de widgets
- **font_id** ID de recurso de fonte

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de fontes de origem com sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the font of “my_prompt”. */
status = gx_prompt_font_set(&my_prompt, MY_PROMPT_FONT_ID);

/* If status is GX_SUCCESS the font for prompt “my_prompt” has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_color_set"></a>gx_prompt_text_color_set


Definir a cor do texto do pedido de aviso

### <a name="prototype"></a>Prototype

```C
UINT gx_prompt_text_color_set(
    GX_PROMPT *prompt,
    GX_RESOURCE_ID normal_color,
    GX_RESOURCE_ID selected_color,
    GX_RESOURCE_ID disabled_color);
```

### <a name="description"></a>Descrição

Este serviço define a cor de texto de um widget rápido.

### <a name="parameters"></a>Parâmetros

- **rápido** Ponteiro para o bloqueio de controlo de widgets
- **normal_color** Identificação de recursos de cor para texto normal. **O apêndice A** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.
- **selected_color** ID de cor de recurso para texto selecionado, usado quando o widget ganha foco. **O apêndice A** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.
- **disabled_color** ID de cor de recurso para texto desativado, utilizado quando GX_STYLE_ENABLED não está ativo. **O apêndice A** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de cores de texto de pronta pronta bem-sucedida
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_WIDGET_SIZE** (0x14) Tamanho do widget inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the text color of “my_prompt”. */
status = gx_prompt_text_color_set(&my_prompt,
                    GX_COLOR_ID_BLACK,
                    GX_COLOR_ID_LIGHTGRAY,
                    GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS the text color for prompt “my_prompt” has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_draw"></a>gx_prompt_text_draw


Função de suporte de desenho

### <a name="prototype"></a>Prototype

```C
VOID gx_prompt_text_draw(GX_PROMPT *prompt);
```

### <a name="description"></a>Descrição

Esta função de suporte desenha a parte de texto de um pedido. Esta função é chamada internamente por gx_prompt_draw(), e é fornecida como uma API separada como uma conveniência para aplicações que definem uma função de desenho rápido personalizado. As aplicações que pretendam personalizar o desenho de fundo rápido podem fornecer a sua função de desenho personalizado, e invocar o serviço de gx_prompt_text_draw como parte do seu desenho personalizado para desenhar o texto rápido sobre o fundo.

### <a name="parameters"></a>Parâmetros

- **rápido** Ponteiro para o bloco de controlo de solicitação

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Define a custom drawing function */
VOID my_prompt_draw(GX_PROMPT *prompt)
{
    /* insert code here to draw prompt background */

    /* call support function to do text drawing */
    gx_prompt_text_draw();

    /* draw child widgets */
    gx_widget_children_draw((GX_WIDGET *) prompt);
}
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_get"></a>gx_prompt_text_get


Obtenha texto rápido (precotado)

### <a name="prototype"></a>Prototype

```C
UINT gx_prompt_text_get(
    GX_PROMPT *prompt, 
    GX_CHAR **return_text);
```

### <a name="description"></a>Descrição

Este serviço é prevadido a favor de gx_prompt_text_get_ext().

Este serviço obtém o texto de um widget rápido.

### <a name="parameters"></a>Parâmetros

- **rápido** Ponteiro para o bloqueio de controlo de widgets
- **return_text** Ponteiro para destino para texto

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Texto rápido bem sucedido obter
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_PROMPT my_prompt;
GX_CHAR *my_prompt_text;

/* Get the text of “my_prompt”. */
status = gx_prompt_text_get(&my_prompt, &my_prompt_text);

/* If status is GX_SUCCESS the pointer “my_prompt_text” points to the text displayed by “my_prompt”. */
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_get_ext"></a>gx_prompt_text_get_ext


Obtenha texto rápido

### <a name="prototype"></a>Prototype

```C
UINT gx_prompt_text_get(
    GX_PROMPT *prompt, 
    GX_STRING *return_string);
```

### <a name="description"></a>Descrição

Este serviço obtém a sequência de um widget rápido.

### <a name="parameters"></a>Parâmetros

- **rápido** Ponteiro para o bloqueio de controlo de widgets
- **return_string** Ponteiro para destino para corda

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Texto rápido bem sucedido obter
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_PROMPT my_prompt;
GX_STRING my_prompt_string;

/* Get the text of “my_prompt”. */
status = gx_prompt_text_get_ext(&my_prompt, &my_prompt_string);

/* If status is GX_SUCCESS then my_prompt_string has been initialize to hold a copy of the prompt string. */
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_id_set"></a>gx_prompt_text_id_set


Definir iD de texto de solicitação

### <a name="prototype"></a>Prototype

```C
UINT gx_prompt_text_id_set(
    GX_PROMPT *prompt, 
    GX_RESOURCE_ID string_id);
```

### <a name="description"></a>Descrição

Este serviço define o ID de cadeia para o widget de texto.

### <a name="parameters"></a>Parâmetros

- **rápido** Ponteiro para o bloqueio de controlo de widgets
- **string_id** ID de recurso da cadeia

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de ID de texto de solicitação de sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **ID** de recursos inválidos de GX_INVALID_RESOURCE_ID (0x33)
- **GX_SYSTEM_MEMORY_ERROR** (0x30) A função de livre de memória não está definida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the string ID of “my_prompt”. */
status = gx_prompt_text_id_set(&my_prompt, MY_STRING_ID);

/* If status is GX_SUCCESS the text ID for prompt “my_prompt” has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_get
- gx_prompt_text_set

## <a name="gx_prompt_text_set"></a>gx_prompt_text_set


Definir texto de solicitação (precotado)

### <a name="prototype"></a>Prototype

```C
UINT gx_prompt_text_set(
    GX_PROMPT *prompt, 
    GX_CHAR *text);
```

### <a name="description"></a>Descrição

Este serviço foi prevadido a favor de gx_prompt_text_set_ext().

Este serviço define o texto de um widget rápido. Se o widget rápido foi criado com GX_STYLE_TEXT_COPY de estilo, o widget cria uma cópia privada da cadeia de texto atribuída. Se GX_STYLE_TEXT_COPY não estiver ativa, o widget não faz uma cópia privada da cadeia de entrada, pelo que a cadeia deve ser atribuída estática ou globalmente, ou seja, pode não ser uma variável automática ou temporária.

GX_PROMPT é derivado de GX_WIDGET e, portanto, todos os serviços gx_widget API podem ser utilizados com GX_PROMPT.

### <a name="parameters"></a>Parâmetros

- **rápido** Ponteiro para o bloqueio de controlo de widgets
- **texto** Ponteiro para texto

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de texto rápido de sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_SYSTEM_MEMORY_ERROR** (0x30) A função de atribuição de memória não está definida
- **GX_INVALID_STRING_LENGTH** (0x34) Comprimento da corda inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the text of “my_prompt” to “my_text”. */
status = gx_prompt_text_set(&my_prompt, “my_text”);

/* If status is GX_SUCCESS the text for “my_prompt” has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_get

## <a name="gx_prompt_text_set_ext"></a>gx_prompt_text_set_ext

Definir texto de solicitação

### <a name="prototype"></a>Prototype

```C
UINT gx_prompt_text_set_ext(
    GX_PROMPT *prompt,
    GX_STRING *string);
```

### <a name="description"></a>Descrição

Este serviço define o texto de um widget rápido. Se o widget rápido foi criado com GX_STYLE_TEXT_COPY de estilo, o widget cria uma cópia privada da cadeia de texto atribuída. Se GX_STYLE_TEXT_COPY não estiver ativa, o widget não faz uma cópia privada da cadeia de entrada, pelo que a cadeia deve ser atribuída estática ou globalmente, ou seja, pode não ser uma variável automática ou temporária.

GX_PROMPT é derivado de GX_WIDGET e, portanto, todos os serviços gx_widget API podem ser utilizados com GX_PROMPT.

### <a name="parameters"></a>Parâmetros

- **rápido** Ponteiro para o bloqueio de controlo de widgets
- **texto** Ponteiro para texto

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de texto rápido de sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_SYSTEM_MEMORY_ERROR** (0x30) A função de atribuição de memória não está definida
- **GX_INVALID_STRING_LENGTH** (0x34) Comprimento da corda inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_STRING new_string;
new_string.gx_string_ptr = “my_text”;
new_string.gx_string_length = strlen(new_string.gx_string_ptr);

/* Set the text of “my_prompt” to “new_string”. */
status = gx_prompt_text_set(&my_prompt, &new_string);

/* If status is GX_SUCCESS the text for “my_prompt” has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_get

## <a name="gx_radial_progress_bar_anchor_set"></a>gx_radial_progress_bar_anchor_set


Definir ângulo de partida

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_progress_bar_anchor_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar, 
    GX_VALUE angle);
```

### <a name="description"></a>Descrição

Este serviço define o ângulo de partida para a barra de progresso radial.

### <a name="parameters"></a>Parâmetros

- **barra de progresso** Ponteiro para bloco de controlo de barra de progresso radial
- **ângulo** Ângulo inicial do arco circular

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de âncora de barra de progresso radial bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **widget** GX_INVALID_WIDGET (0x12) Inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_VALUE start_angle = 90;

/* Set the start angle of “my_progress_bar” to 90 degree. */
status = gx_radial_progress_bar_anchor_set(&my_progress_bar, start_angle);

/* If status is GX_SUCCESS the anchor value of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_background_draw"></a>gx_radial_progress_bar_background_draw


Desenhar fundo

### <a name="prototype"></a>Prototype

```C
VOID gx_radial_progress_bar_background_draw(GX_RADIAL_PROGRESS_BAR *progress_bar);
```

### <a name="description"></a>Descrição

Este serviço desenha um fundo de barra de progresso radial. Este serviço é referenciado internamente pela função gx_radial_progress_bar_draw, mas está exposto para utilização pela aplicação nos casos em que a aplicação define uma função de desenho de barra de progresso radial personalizado

### <a name="parameters"></a>Parâmetros

- **barra de progresso** Ponteiro para bloco de controlo de barras de progresso radial

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom radial progress bar drawing function. */

VOID my_radial_progress_bar_draw(GX_RADIAL_PROGRESS_BAR *radial_progress)
{
    /* Call default radial progress bar background draw. */
    gx_radial_progress_bar_background_draw(radial_progress);

    /* Add your own drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)radial_progress);
}
```
### <a name="see-also"></a>Consulte também

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_create"></a>gx_radial_progress_bar_create


Criar barra de progresso radial

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_progress_bar_create(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RADIAL_PROGRESS_BAR_INFO *info,
    ULONG style
    USHORT id);
```

### <a name="description"></a>Descrição

Este serviço cria uma barra de progresso radial.

Se o estilo widget GX_STYLE_ENABLED for aplicado na barra de progresso, a barra de progresso aceitará pen_down, pen_drag e pen_up entrada para modificar o valor atual da barra de progresso.

O estilo widget GX_STYLE_PROGRESS_TEXT_DRAW pode ser usado para permitir desenhar o valor da barra de progresso como texto dentro da área da barra de progresso. Se este estilo for utilizado em combinação com o estilo GX_STYLE_PROGRESS_PERCENT, o valor da barra de progresso é apresentado em percentagem. Caso contrário, o valor da barra de progresso é apresentado como o valor angular atual.

### <a name="parameters"></a>Parâmetros

- **barra de progresso** Ponteiro para o controlo da barra de progresso radial
- **barra de progresso** Ponteiro para bloco de controlo de barra de progresso radial
- **nome** Nome da barra de progresso radial
- **pai** Ponteiro para widget dos pais
- **informação** Ponteiro para uma estrutura GX_RADIAL_PROGRESS_BAR. **O apêndice I** contém definição para GX_RADIAL_PROGRESS_BAR estrutura.
- **estilo** Estilo da barra de progresso radial
- **Id ID** definido aplicação de barra de progresso

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Barra de progresso radial bem sucedida criar
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_WIDGET** (0x12) Widget parental inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_RAIDAL_PROGRESS_BAR_INFO info;

info.gx_radial_progress_bar_info_xcenter = 200;
info.gx_radial_progress_bar_info_ycenter = 200;
info.gx_radial_progress_bar_info_radius = 100;
info.gx_radial_progress_bar_info_current_angle = 180;
info.gx_radial_progress_bar_info_anchor_val = -180;
info.gx_radial_progress_bar_info_font_id = GX_FONT_ID_SYSTEM;
info.gx_raidal_progress_bar_info_normal_text_color =
                                        GX_COLOR_ID_TEXT;
info.gx_radial_progress_bar_info_selected_text_color =
                                        GX_COLOR_ID_TEXT;
info.gx_radial_progress_bar_info_disabled_text_color =
                                        GX_COLOR_ID_DISABLED_TEXT;
info.gx_radial_progress_bar_info_normal_brush_width = 20;
info.gx_raidal_progress_bar_info_selected_brush_width = 16;
info.gx_radial_progress_bar_info_normal_brush_color =
                                        GX_COLOR_ID_WIDGET_FILL;
info.gx_radial_progress_bar_info_selected_brush_color =
                                        GX_COLOR_ID_SELECTED_FILL;

/* Create a radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_create(&my_progress_bar,
                    “my_progress_bar”, parent, &info,
                    GX_STYLE_ENABLED | GX_STYLE_TRANSPARENT |
                    GX_STYLE_PROGRESS_TEXT_DRAW,
                    ID_MY_RADIAL_PROGRESS);

/* If status is GX_SUCCESS the radial progress bar “my_progress_bar” has been created. */
```

### <a name="see-also"></a>Consulte também

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_draw"></a>gx_radial_progress_bar_draw


Desenhe uma barra de progresso radial

### <a name="prototype"></a>Prototype

```C
VOID gx_radial_progress_bar_draw(GX_RADIAL_PROGRESS_BAR *progress_bar);
```

### <a name="description"></a>Descrição

Este serviço desenha uma barra de progresso radial. Este serviço é utilizado internamente referenciado pela função gx_radial_progress_bar_create, mas está exposto para utilização pela aplicação nos casos em que a aplicação define uma função de desenho de barra de progresso radial personalizada.

### <a name="parameters"></a>Parâmetros

- **barra de progresso** Ponteiro para bloco de controlo de barras de progresso radial

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom radial progress bar drawing function. */

VOID my_radial_progress_bar_draw(GX_RADIAL_PROGRESS_BAR *radial_progress)
{
    /* Call default radial progress bar draw. */
    gx_radial_progress_bar_draw(radial_progress);

    /* Add your own drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)radial_progress);
}
```

### <a name="see-also"></a>Consulte também

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_size_calculate
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_event_process"></a>gx_radial_progress_bar_event_process


Evento de barra de progresso radial de processo

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_progress_bar_event_process(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Descrição

Este serviço processa um evento radial progress bar. Esta função é referenciada internamente pela função gx_radial_progress_bar_create, mas está exposta para utilização pela aplicação nos casos em que a aplicação define uma função de processamento de eventos de progresso radial personalizado.

### <a name="parameters"></a>Parâmetros

- **barra de progresso** Ponteiro para bloco de controlo de barra de progresso radial
- **event_ptr** Ponteiro para o evento para processar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Processo de evento de barras de progresso radial bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **widget** GX_INVALID_WIDGET (0x12) Inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Write a custom event processing function. */

UINT my_event_process (GX_RADIAL_PROGRESS_BAR *radial_progress, GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
        case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_radial_progress_bar_event_process(
                            radial_progress, event_ptr);
        /* add my own handling here */
        break;
    default:
        status = gx_radial_progress_bar_event_process(
                            radial_progress, event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Consulte também

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_font_set"></a>gx_radial_progress_bar_font_set


Definir fonte de barra de progresso radial

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_progress_bar_font_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Descrição

Este serviço define a fonte de um widget de barra de progresso radial. Este parâmetro não tem efeito se o estilo widget GX_STYLE_PROGRESS_TEXT_DRAW não estiver definido.

### <a name="parameters"></a>Parâmetros

- **barra de progresso** Ponteiro para bloco de controlo de barra de progresso radial
- **font_id** ID de recurso de fonte

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de fontes de barra de progresso radial bem-sucedida
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **widget** GX_INVALID_WIDGET (0x12) Inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set font for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_font_set(&my_progress_bar, font);

/* If status is GX_SUCCESS the font of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_info_set"></a>gx_radial_progress_bar_info_set


Definir informações de barras de progresso radial

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_progress_bar_info_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_RADIAL_PROGRESS_BAR_INFO *info);
```

### <a name="description"></a>Descrição

Este serviço repõe os parâmetros de informação atribuídos à barra de progresso radial.

### <a name="parameters"></a>Parâmetros

- **barra de progresso** Ponteiro para bloco de controlo de barra de progresso radial
- **informação** Ponteiro para estrutura de informação de barras de progresso radial. **O apêndice I** contém definição para GX_RADIAL_PROGRESS_BAR_INFO estrutura.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de informações de barras de progresso radial bem-sucedida
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **widget** GX_INVALID_WIDGET (0x12) Inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_RAIDAL_PROGRESS_BAR_INFO info;

info.gx_radial_progress_bar_info_xcenter = 200;
info.gx_radial_progress_bar_info_ycenter = 200;
info.gx_radial_progress_bar_info_radius = 100;
info.gx_radial_progress_bar_info_current_angle = 180;
info.gx_radial_progress_bar_info_anchor_val = -180;
info.gx_radial_progress_bar_info_font_id = GX_FONT_ID_SYSTEM;
info.gx_raidal_progress_bar_info_normal_text_color =
                                GX_COLOR_ID_TEXT;
info.gx_radial_progress_bar_info_selected_text_color =
                                GX_COLOR_ID_TEXT;
info.gx_radial_progress_bar_info_disabled_text_color =
                                GX_COLOR_ID_DISABLED_TEXT;
info.gx_radial_progress_bar_info_normal_brush_width = 20;
info.gx_raidal_progress_bar_info_selected_brush_width = 16;
info.gx_radial_progress_bar_info_normal_brush_color =
                                GX_COLOR_ID_WIDGET_FILL;
info.gx_radial_progress_bar_info_selected_brush_color =
                                GX_COLOR_ID_SELECTED_FILL;

/* Set appearance information for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_info_set(&my_progress_bar, &info);

/* If status is GX_SUCCESS the appearance information of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_text_color_set"></a>gx_radial_progress_bar_text_color_set


Definir cor de texto de barra de progresso radial

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_progress_bar_text_color_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID normal_text_color,
    GX_RESOURCE_ID selected_text_color,
    GX_RESOURCE_ID disabled_text_color);
```

### <a name="description"></a>Descrição

Este serviço define a cor de texto da barra de progresso radial. Este valor só é utilizado se o estilo GX_STYLE_PROGRESS_TEXT_DRAW estiver definido.

### <a name="parameters"></a>Parâmetros

- **barra de progresso** Ponteiro para bloco de controlo de barra de progresso radial
- **normal_color** Identificação de recurso da cor do texto em estado normal. **O apêndice A** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.
- **selected_color** ID de recurso da cor do texto quando o widget ganha foco. **O apêndice A** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.
- **disabled_color** ID de recurso de cor de texto quando o estilo GX_STYLE_ENABLED não está definido. **O apêndice A** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de cores de texto de barra de barras de progresso radial bem-sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_WIDGET** (0x12) Verificação de widgets inválidos

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set text color for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_text_color_set(&my_progress_bar,
                            GX_COLOR_ID_NORMAL_TEXT,
                            GX_COLOR_ID_SELECTED_TEXT,
                            GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS the text color of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_text_draw"></a>gx_radial_progress_bar_text_draw


Desenhar texto de barra de progresso radial

### <a name="prototype"></a>Prototype

```C
VOID gx_radial_progress_bar_text_draw(GX_RADIAL_PROGRESS_BAR *progress_bar);
```

### <a name="description"></a>Descrição

Este serviço desenha o texto da barra de progresso radial especificada. Esta função é chamada internamente como parte do gx_radial_progress_bar_draw,, mas está exposta à aplicação de suporte aos casos em que a aplicação define uma função de desenho de barra de progresso personalizada.

### <a name="parameters"></a>Parâmetros

- **barra de progresso** Ponteiro para bloco de controlo de barras de progresso radial

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e Threads

### <a name="example"></a>Exemplo

```C
/* Draw text for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_text_draw (&my_progress_bar);

/* If status is GX_SUCCESS the text of “my_progress_bar” has been drawn. */

/* Write a custom radial progress bar drawing function. */
VOID my_radial_progress_bar_draw(GX_RADIAL_PROGRESS_BAR *radial_progress)
{
    /* Add your own background draw here. */

    /* Call default radial progress bar text draw. */
    gx_radial_progress_bar_text_draw(radial_progress);

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)radial_progress);
}
```

### <a name="see-also"></a>Consulte também

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_value_set"></a>gx_radial_progress_bar_value_set


Definir valor da barra de progresso radial

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_progress_bar_value_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar, 
    GX_VALUE value);
```

### <a name="description"></a>Descrição

Este serviço define o valor da barra de progresso radial. O valor atribuído limita-se ao intervalo [-360, 360], definindo a possível gama de valores angulares para a localização atual da barra de progresso. A aplicação deve escalar o valor real indicado para atribuir um valor angular ao widget da barra de progresso.

A barra de progresso é desenhada de modo a que o valor atual indique o delta angular entre a posição da âncora e o ponto final do arco superior. Os valores negativos fazem com que o arco seja desenhado no sentido dos ponteiros do relógio, a partir da posição de ancoragem. O valor de corrente positivo faz com que o arco seja desenhado no sentido contrário ao dos ponteiros do relógio, a partir da posição de âncora.

Por exemplo, desenhar um arco a partir do topo do arco (posição das 12 horas) e terminar à direita (posição das três horas), atribua um valor de âncora de 90 graus e um valor atual de -90 graus.

### <a name="parameters"></a>Parâmetros

- **barra de progresso** Ponteiro para bloco de controlo de barra de progresso radial
- **valor** Novo valor da barra de progresso

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de valor da barra de progresso radial bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiros inválidos
- **widget** GX_INVALID_WIDGET (0x12) Inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_VALUE new_value = 180;

/* Set value for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_value_set(&my_progress_bar,
                                        new_value);

/* If status is GX_SUCCESS the value of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw

## <a name="gx_radio_button_create"></a>gx_radio_button_create


Criar botão de rádio

### <a name="prototype"></a>Prototype

```C
UINT gx_radio_button_create(
    GX_RADIO_BUTTON *button,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id, ULONG style,
    USHORT radio_button_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria um widget de botão de rádio. GX_RADIO_BUTTON é derivado de GX_TEXT_BUTTON, pelo que todos os serviços gx_text_button também são suportados por este tipo de widget.

### <a name="parameters"></a>Parâmetros

- **botão** Ponteiro para bloco de controlo de botões de rádio
- **nome** Nome lógico do widget de botão de rádio
- **pai** Ponteiro para o widget dos pais
- **text_id** ID de recurso do botão de rádio
- **estilo** Estilo de botão de rádio. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **radio_button_id** ID definido pela aplicação do botão de rádio
- **tamanho** Dimensões do botão de rádio

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Botão de rádio bem sucedido criar
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_** TAMANHO (0x19) Tamanho do bloco de controlo de widget inválido
- **ID** de recursos inválidos de GX_INVALID_RESOURCE_ID (0x33)
- **widget** GX_INVALID_WIDGET (0x12) Inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Create “my_radio_button”. */
status = gx_radio_button_create(&my_radio_button, “my_radio_button”, &my_parent,
                    MY_RADIO_BUTTON_TEXT_RESOURCE_ID,
                    GX_STYLE_BORDER_RAISED, MY_RADIO_BUTTON_ID, &size);

/* If status is GX_SUCCESS the radio button “my_radio_button” has been created. */
```
### <a name="see-also"></a>Consulte também

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw
- gx_radio_button_draw

## <a name="gx_radio_button_draw"></a>gx_radio_button_draw


Desenhe botão de rádio

### <a name="prototype"></a>Prototype

```C
VOID gx_radio_button_draw(GX_RADIO_BUTTON *button);
```

### <a name="description"></a>Descrição

Este serviço desenha um widget de botão de rádio. Este serviço é chamado internamente pela atualização de tela GUIX, mas também pode ser chamado por funções de desenho overridden.

### <a name="parameters"></a>Parâmetros

- **botão** Ponteiro para o bloco de controlo widget de botão de rádio

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom radio button drawing function. */

VOID my_radio_button_draw(GX_RADIO_BUTTON *radio_button)
{
    /* Call default radio button draw. */
    gx_radio_button_draw(radio_button);

    /* Add your own drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)radio_button);
}
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw
- gx_radio_button_create

## <a name="gx_radio_button_pixelmap_set"></a>gx_radio_button_pixelmap_set


Definir pixelmaps para botão de rádio

### <a name="prototype"></a>Prototype

```C
UINT gx_radio_button_pixelmap_set(
    GX_RADIO_BUTTON *button,
    GX_RESOURCE_ID off_id,
    GX_RESOURCE_ID on_id,
    GX_RESOURCE_ID off_disabled_id,
    GX_RESOURCE_ID on_disabled_id);
```

### <a name="description"></a>Descrição

Este serviço atribui as pixelmaps a serem exibidas pelo botão de rádio especificado para cada estado de botão. Os IDs de recursos podem ser duplicados.

### <a name="parameters"></a>Parâmetros

- **off_id** Pixelmap usado para botão de rádio fora do estado
- **on_id** Pixelmap usado para botão de rádio no estado
- **off_disabled_id** Pixelmap usado para botão de rádio desativado e fora do estado
- **on_disabled_id** Pixelmap utilizado para botão de rádio desativado e no estado

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de pixelmaps de botão de rádio bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **widget** GX_INVALID_WIDGET (0x12) Inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set pixelmap for “my_radio_button”. */
status = gx_radio_button_pixelmap_set(&my_radio_button,
                                MY_OFF_PIXELMAP,
                                MY_ON_PIXELMAP,
                                MY_OFF_DISABLED_PIXELMAP,
                                MY_ON_DISABLED_PIXELMAP);

/* If status is GX_SUCCESS the pixelmaps for radio button “my_radio_button” has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw
- gx_radio_button_create

## <a name="gx_radial_slider_anchor_angles_set"></a>gx_radial_slider_anchor_angles_set


Definir lista de âncora de slider radial

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_slider_anchor_angles_set(
    GX_RADIAL_SLIDER *slider,
    GX_VALUE *anchor_angles, 
    USHORT anchor_count);
```

### <a name="description"></a>Descrição

Este serviço define ângulos de ancoragem para o deslizador radial. Se a lista de ângulos de ancoragem estiver definida, o ângulo do deslizador radial será um dos ângulos de ancoragem definidos.

### <a name="parameters"></a>Parâmetros

- **slider** Bloco de controlo do deslizador radial
- **anchor_angles** Lista de ângulo para definir
- **anchor_count** Contagem dos ângulos de âncora

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de ângulos de âncora bem sucedidos
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **widget** GX_INVALID_WIDGET (0x12) Inválido
- **lista de** âncora inválida GX_INVALID_VALUE (0x22)

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_VALUE anchor_angles[]={0, 30, 60, 90, 120, 150, 180};
USHORT anchor_count = 7;

/* Set anchor angles for radial slider. */
status = gx_radial_slider_anchor_angles_set(&my_radial_slider,
                                anchor_angles, anchor_count);

/* If status is GX_SUCCESS the anchor angles have been set for “my_radial_slider”. */

/* Set anchor angles for radial slider. */
status = gx_radial_slider_anchor_angles_set(&my_radial_slider,
                                GX_NULL, 0);

/* If status is GX_SUCCESS the anchor angles have been removed from “my_radial_slider”. */
```

### <a name="see-also"></a>Consulte também

- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_angle_set"></a>gx_radial_slider_angle_set

Definir ângulo de slider radial

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_slider_angle_set(
    GX_RADIAL_SLIDER *slider,
    GX_VALUE new_angle);
```

### <a name="description"></a>Descrição

Este serviço define um novo valor de ângulo para o deslizador radial.

### <a name="parameters"></a>Parâmetros

- **slider** Ponteiro para bloco de controlo de deslizador radial
- **new_angle** Novo valor de ângulo a definir

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de ângulo de deslizamento radial bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **widget** GX_INVALID_WIDGET (0x12) Inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set “my_radial_slider” angle to 0 degree(3 o’clock position). */
status = gx_radial_slider_angle_set(&my_radial_slider, 0);

/* If status is GX_SUCCESS the value of “my_radial_slider” has been set to 0 degree. */
```

### <a name="see-also"></a>Consulte também

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_animation_set"></a>gx_radial_slider_animation_set


Criar informações de animação de slider radial

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_slider_animation_set(
    GX_RADIAL_SLIDER *slider,
    USHORT steps, USHORT delay, 
    USHORT animation_style,
    VOID (*animation_update_callback)(GX_RADIAL_SLIDER *slider));
```

### <a name="description"></a>Descrição

Este serviço define passos de animação, tempo de atraso e estilos de animação para animação de agulha de slider radial.

### <a name="parameters"></a>Parâmetros

- **slider** Ponteiro para bloco de controlo de deslizador radial
- **passos** Passos totais para uma animação
- **atraso** Atraso no tempo para cada passo de animação
- **animation_style** Tipo de função de flexibilização, inclui:
  - GX_ANIMATION_BACK_EASE_IN
  - GX_ANIMATION_BACK_EASE_OUT
  - GX_ANIMATION_BACK_EASE_IN_OUT
  - GX_ANIMATION_BOUNCE_EASE_IN
  - GX_ANIMATION_BOUNCE_EASE_OUT
  - GX_ANIMATION_BOUNCE_EASE_IN_OUT
  - GX_ANIMATION_CIRC_EASE_IN
  - GX_ANIMATION_CIRC_EASE_OUT
  - GX_ANIMATION_CIRC_EASE_IN_OUT
  - GX_ANIMATION_CUBIC_EASE_IN
  - GX_ANIMATION_CUBIC_EASE_OUT
  - GX_ANIMATION_CUBIC_EASE_IN_OUT
  - GX_ANIMATION_ELASTIC_EASE_IN
  - GX_ANIMATION_ELASTIC_EASE_OUT
  - GX_ANIMATION_ELASTIC_EASE_IN_OUT
  - GX_ANIMATION_EXPO_EASE_IN
  - GX_ANIMATION_EXPO_EASE_OUT
  - GX_ANIMATION_EXPO_EASE_IN_OUT
  - GX_ANIMATION_QUAD_EASE_IN
  - GX_ANIMATION_QUAD_EASE_OUT
  - GX_ANIMATION_QUAD_EASE_IN_OUT
  - GX_ANIMATION_QUART_EASE_IN
  - GX_ANIMATION_QUART_EASE_OUT
  - GX_ANIMATION_QUART_EASE_IN_OUT
  - GX_ANIMATION_QUINT_EASE_IN
  - GX_ANIMATION_QUINT_EASE_OUT
  - GX_ANIMATION_QUINT_EASE_IN_OUT
  - GX_ANIMATION_SINE_EASE_IN
  - GX_ANIMATION_SINE_EASE_OUT
  - GX_ANIMATION_SINE_EASE_IN_OUT
- **animation_update_callback** Função de retorno definida pelo utilizador que será chamada após cada passo de animação

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de animação de slider radial bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **widget** GX_INVALID_WIDGET (0x12) Inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
VOID animation_callback(GX_RADIAL_SLIDER *slider)
{
    /* This function will be called after each animation step,
    add custom code here. */
}

/* Set animation info for “my_radial_slider”. */
status = gx_radial_slider_animation_set(&my_radial_slider, 15, 2,
                                GX_ANIMATION_CIRC_EASE_IN_OUT,
                                animation_callback);

/* If status is GX_SUCCESS the radial slider needle will move with specified animation. */

/* Disable animation for “my_radial_slider”. */
status = gx_radial_slider_animation_set(&my_radial_slider, 0, 0,
                                        0, 0);

/* If status is GX_SUCCESS the radial slider needle will move without animation. */
```

### <a name="see-also"></a>Consulte também

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_animation_start"></a>gx_radial_slider_animation_start


Definir novo valor de slider radial com animação

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_slider_animation_start(
    GX_RADIAL_SLIDER *slider,
    GX_VALUE target_angle);
```

### <a name="description"></a>Descrição

Este serviço inicia uma animação para mover a agulha de slider da posição atual para a posição especificada.

### <a name="parameters"></a>Parâmetros

- **slider** Ponteiro para bloco de controlo de deslizador radial
- **target_angle** Valor do ângulo do alvo

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Início de animação radial de slider bem-sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **widget** GX_INVALID_WIDGET (0x12) Inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Start an animation to move radial slider needle from
current position to 90 degree position. */
status = gx_radial_slider_animation_start(&my_radial_slider, 90);

/* If status is GX_SUCCESS the radial slider needle animation has been started. */
```

### <a name="see-also"></a>Consulte também

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_create"></a>gx_radial_slider_create


Criar slider radial

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_slider_create(
    GX_RADIAL_SLIDER *slider,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RADIAL_SLIDER_INFO *info,
    ULONG style,
    USHORT slider_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria um widget de slider radial.

### <a name="parameters"></a>Parâmetros

- **slider** Ponteiro para bloco de controlo de deslizador radial
- **nome** Nome lógico do widget de slider radial
- **pai** Ponteiro para o widget dos pais
- **informação** Definição de aparência de slider radial, **apêndice I** contém definição para GX_RADIAL_SLIDER_INFO.
- **estilo** Estilo de botão de rádio. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **radio_button_id** ID definido pela aplicação do deslizador radial
- **tamanho** Dimensões do deslizador radial

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Slider radial de sucesso criar
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_** TAMANHO (0x19) Tamanho do bloco de controlo de widget inválido
- **GX_INVALID_WIDGET** (0x12) Widget parental inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_RADIAL_SLIDER_INFO info;
GX_RECTANGLE size;

/* Distance from left side of widget to rotating center. */
info.gx_radial_slider_info_xcenter = 100;

/* Distance from top size of widget to rotating center. */
info.gx_radial_slider_info_ycenter = 100;

/* Radius of rotating circle. */
info.gx_radial_slider_info_radius = 100;

/* Widget of rotating track. */
info.gx_radial_slider_info_track_width = 40;

/* Current angle value. */
info.gx_radial_slider_info_current_angle = 0;

/* Minimum angle value. */
info.gx_radial_slider_min_anlge = -60;

/* Maximum angle value. */
info.gx_radial_slider_max_angle = 240;

/* Anchor value list. */
info.gx_radial_slider_angle_list = GX_NULL;

/* Anchor value count. */
info.gx_radial_slider_list_count = 0;

/* Resource ID of background pixelmap. */
info.gx_radial_slider_background_pixelmap = GX_PIXELMAP_ID_BKGRD;

/* Resource ID of needle pixelmap. */
info.gx_radial_slider_needle_pixelmap = GX_PIXELMAP_ID_NEEDLE;

/* Define widget size. */
gx_utility_rectangle_define(&size, 0, 0, 200, 200);

/* Create “my_radial_slider”. */
status = gx_radial_slider_create(&my_radial_slider,
                                “my_radial_slider”, &my_parent,
                                &info, GX_STYLE_ENABLED,
                                MY_RADIAL_SLIDER_ID, &size);

/* If status is GX_SUCCESS the radial slider “my_radial_slider” has been created. */
```

### <a name="see-also"></a>Consulte também

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_draw"></a>gx_radial_slider_draw


Desenhe o slider radial

### <a name="prototype"></a>Prototype

```C
VOID gx_radial_slider_draw(GX_RADIAL_SLIDER *slider);
```

### <a name="description"></a>Descrição

Este serviço desenha um deslize radial. Este serviço é chamado internamente pela atualização de tela GUIX, mas também pode ser chamado por funções de desenho overridden.

### <a name="parameters"></a>Parâmetros

- **slider** Ponteiro para bloco de controlo de deslizador radial

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom radio button drawing function. */

VOID my_radial_slider_draw(GX_RADIAL_SLIDER *radial_slider)
{
    /* Call default radial slider draw. */
    gx_radio_slider_draw(radial_slider);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_event_process"></a>gx_radial_slider_event_process


Evento de slider radial de processo

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_slider_event_process(
    GX_RADIAL_SLIDER *slider,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Descrição

Este serviço processa um evento de slider radial. Este serviço deve ser chamado como o manipulador de eventos predefinido por quaisquer funções de processamento de eventos de slider radiais personalizados.

### <a name="parameters"></a>Parâmetros

- **slider** Ponteiro para bloco de controlo de deslizador radial
- **event_ptr** Ponteiro para o evento para processar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Processo de evento de deslizamento radial bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **widget** GX_INVALID_WIDGET (0x12) Inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Write a custom event processing function. */

UINT my_event_process(GX_RADIAL_SLIDER *slider,
                    GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_radial_slider_event_process(slider, event_ptr);

        /* add my own handling here */
        break;
    default:
        status = gx_radial_slider_event_process(slider, event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Consulte também

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_info_get"></a>gx_radial_slider_info_get


Recuperar informações de slider radial

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_slider_info_get(
    GX_RADIAL_SLIDER *slider,
    GX_RADIAL_SLIDER_INFO **info);
```

### <a name="description"></a>Descrição

Este serviço recupera o ponteiro de informação do deslizador radial.

### <a name="parameters"></a>Parâmetros

- **slider** Ponteiro para bloco de controlo de deslizador radial
- **informação** Ponteiro de informação de deslizamento radial recuperado

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Informação de slider radial bem sucedida
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **widget** GX_INVALID_WIDGET (0x12) Inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_RADIAL_SLIDER_INFO *info;

/* Retrive radial slider information structure. */
status = gx_radial_slider_info_get(&my_radial_slider,
                                    “my_radial_slider”, &info);

/* If status is GX_SUCCESS the radial slider information pointer of “my_radial_slider” has been retrieved. */
```

### <a name="see-also"></a>Consulte também

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_info_set"></a>gx_radial_slider_info_set


Definir informações de slider radial

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_slider_info_set(
    GX_RADIAL_SLIDER *slider,
    GX_RADIAL_SLIDER_INFO *info);
```

### <a name="description"></a>Descrição

Este serviço define informações de deslizamento radial.

### <a name="parameters"></a>Parâmetros

- **slider** Ponteiro para bloco de controlo de deslizador radial
- **informação** Informação de slider radial para definir

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de informações de slider radial bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **widget** GX_INVALID_WIDGET (0x12) Inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_RADIAL_SLIDER_INFO info;

/* Distance from left side of widget to rotating center. */
info.gx_radial_slider_info_xcenter = 100;

/* Distance from top size of widget to rotating center. */
info.gx_radial_slider_info_ycenter = 100;

/* Radius of rotating circle. */
info.gx_radial_slider_info_radius = 100;

/* Widget of rotating track. */
info.gx_radial_slider_info_track_width = 40;

/* Current angle value. */
info.gx_radial_slider_info_current_angle = 0;

/* Minimum angle value. */
info.gx_radial_slider_min_anlge = -60;

/* Maximum angle value. */
info.gx_radial_slider_max_angle = 240;

/* Anchor value list. */
info.gx_radial_slider_angle_list = GX_NULL;

/* Anchor value count. */
info.gx_radial_slider_list_count = 0;

/* Resource ID of background pixelmap. */
info.gx_radial_slider_background_pixelmap = GX_PIXELMAP_ID_BKGRD;

/* Resource ID of needle pixelmap. */
info.gx_radial_slider_needle_pixelmap = GX_PIXELMAP_ID_NEEDLE;

/* Reset radial slider info for “my_radial_slider”. */
status = gx_radial_slider_info_set(&my_radial_slider, &info);

/* If status is GX_SUCCESS the radial slider info of “my_radial_slider” has been reset. */
```

### <a name="see-also"></a>Consulte também

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_pixelmap_set"></a>gx_radial_slider_pixelmap_set


Definir pixelmaps de slider radial

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_slider_pixelmap_set(
    GX_RADIAL_SLIDER *slider,
    GX_RESOURCE_ID background_pixemap,
    GX_REOUSRCE_ID needle_pixelmap);
```

### <a name="description"></a>Descrição

Este serviço define o fundo do slider radial e as pixelmaps da agulha.

### <a name="parameters"></a>Parâmetros

- **slider** Ponteiro para bloco de controlo de deslizador radial
- **background_pixelmap** ID de recursos de pixelmap de fundo
- **needle_pixelmap** ID de recurso do pixelmap da agulha

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de pixelmap de deslizamento radial de sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **widget** GX_INVALID_WIDGET (0x12) Inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Create “my_radio_button”. */
status = gx_radial_slider_pixelmap_set(&my_radial_slider, GX_PIXELMAP_ID_BG, GX_PIXELMAP_ID_NEEDLE);

/* If status is GX_SUCCESS the background and needle pixelmap of “my_radial_slider” has been reset. */
```

### <a name="see-also"></a>Consulte também

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set

## <a name="gx_rich_text_view_create"></a>gx_rich_text_view_create

Criar uma rica vista de texto

### <a name="prototype"></a>Prototype

```C
UINT gx_rich_text_view_create(
    GX_RICH_TEXT_VIEW *text_view,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id,
    GX_RICH_TEXT_FONTS *fonts,
    USHORT id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria uma visão de texto rica como especificado.


**As etiquetas de formatação são utilizadas para exibir tipos especiais para texto:**

- **\<b>\</b>** Definir fonte de texto com id de fonte em negrito especificado pelo utilizador
- **\<i>\</i>** Definir fonte de texto com id de fonte itálica especificado do utilizador
- **\<u>\</u>** Permitir o sublinhado de texto
- **\<f GX_FONT_ID>\</f>** Definir fonte de texto com id de fonte especificado
- **\<c GX_COLOR_ID>\</c>** Definir fonte de texto com id de cor especificado
- **\<hc GX_COLOR_ID>\</hc>** Definir texto realçar a cor especificada id de cor
- **\<align left/right/center>\</align>** Definir alinhamento de texto

**Exemplos de utilização da etiqueta de formatação:**

- \<b>Este é um texto arrojado<\b>
- \<i>Este é o texto itálico<\i>
- \<u>Este é um texto com sublinhado<\u>
- \<f 0>Este id de fonte de texto está definido para 0<\f>
- \<c 1>Este id de cor de texto está definido para 1<\c>
- \<hc 2>Este id de cor de destaque de texto está definido para 2<\hc>
- \<align left> Este texto é deixado alinhado<\alinhar>

### <a name="parameters"></a>Parâmetros

- **text_view** Ponteiro para bloco de controlo de vista de texto rico
- **nome** Nome da rica vista de texto
- **pai** Ponteiro para widget dos pais
- **text_id** ID de recurso da cadeia de texto
- **fontes** Ponteiro para a informação de fonte de vista de texto rico. **Apendix I** contém definição para GX_RICH_TEXT_FONTS estrutura.
- **estilo** Estilo do widget. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **ID ID** definido por aplicação da vista de texto rico
- **tamanho** Tamanho da rica vista de texto

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Criação de visão de texto rica e bem sucedida
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_RICH_TEXT_VIEW rich_view;
GX_RCIH_TEXT_FONTS fonts;
GX_RECTANGLE size;

/* Defined widget size. */
gx_utility_rectangle_define(&size, 100, 100, 300, 150);

/* Define font information. */
fonts.gx_rich_text_fonts_normal_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_bold_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_italic_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_bold_italic_id = GX_FONT_ID_SYSTEM;

/* Create rich text view widget. */
status = gx_rich_text_view_create(&rich_view, “my_rich_view”,
                                  parent, GX_STRING_ID_TEST_STRING,
                                  &fonts,
                                  GX_STYLE_ENABLED,
                                  MY_RICH_VIEW_ID, &size);

/* If status is GX_SUCCESS the rich text view was successfully created. */

```

A aplicação de demonstração demo_guix_widget_types, fornecida como parte da instalação do GUIX Studio, fornece um exemplo completo de utilização do widget de visualização de texto rico.

### <a name="see-also"></a>Consulte também

- gx_rich_text_view_draw
- gx_rich_text_view_fonts_set
- gx_rich_text_view_text_draw

## <a name="gx_rich_text_view_draw"></a>gx_rich_text_view_draw


Desenhar vista de texto rica

### <a name="prototype"></a>Prototype

```C
VOID gx_rich_text_view_draw(GX_RICH_TEXT_VIEW *text_view);
```

### <a name="description"></a>Descrição

Este serviço desenha o widget de visualização de texto rico especificado. Este serviço é normalmente chamado internamente pelo GUIX como parte de uma operação de atualização de tela, mas também exposto à aplicação que pode querer fornecer uma função de desenho personalizado e invocar o desenho de visão de texto rico padrão como base de desenho personalizado.

### <a name="parameters"></a>Parâmetros

- **text_view** Ponteiro para bloco de controlo widget de vista de texto rico

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom rich text view drawing function. */

VOID my_rich_text_view_draw(GX_RICH_TEXT_VIEW *text_view)
{
    /* Call default rich text view draw. */
    gx_rich_text_view_draw(text_view);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_rich_text_view_create
- gx_rich_text_view_fonts_set
- gx_rich_text_view_text_draw

## <a name="gx_rich_text_view_fonts_set"></a>gx_rich_text_view_fonts_set

Definir fontes de vista de texto ricas

### <a name="prototype"></a>Prototype

```C
UINT gx_rich_text_view_fonts_set(GX_RICH_TEXT_VIEW *text_view, GX_RICH_TEXT_FONTS *fonts);
```

### <a name="description"></a>Descrição

Este serviço define as fontes de um widget de visualização de texto rico.

### <a name="parameters"></a>Parâmetros

- **text_view** Ponteiro para bloco de controlo widget de vista de texto rico
- **fontes** Ponteiro para informações de fonte de vista de texto rico. **Apendix I** contém definições para GX_RICH_TEXT_FONTS estrutura.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de fontes de visualização de texto rico bem-sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_RICH_TEXT_FONTS fonts;

/* Replace the font ids as needed. */
fonts.gx_rich_text_fonts_normal_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_bold_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_italic_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_bold_italic_id = GX_FONT_ID_SYSTEM;

/* Set the font of “my_rich_view”. */
status = gx_rich_text_view_fonts_set(&my_rich_view, &fonts);

/* If status is GX_SUCCESS the font for rich text view “my_rich_view” has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_rich_text_view_create
- gx_rich_text_view_draw
- gx_rich_text_view_text_draw

## <a name="gx_rich_text_view_text_draw"></a>gx_rich_text_view_text_draw


Desenhar texto de vista de texto rico

### <a name="prototype"></a>Prototype

```C
VOID gx_rich_text_view_text_draw(GX_RICH_TEXT_VIEW *text_view);
```

### <a name="description"></a>Descrição

Esta função de suporte desenha a parte de texto de uma visão de texto rica. Esta função é chamada internamente por gx_rich_text_view_draw(), e é fornecida como uma API separada como uma conveniência para aplicações que definem uma função de desenho de visão de texto rico personalizado. As aplicações que pretendem personalizar o desenho de fundo de vista de texto rico podem fornecer a sua função de desenho personalizado, e invocar o serviço de gx_rich_text_view_text_draw como parte do seu desenho personalizado para desenhar o rico texto de vista de texto sobre o fundo.

### <a name="parameters"></a>Parâmetros

- **text_view** Ponteiro para bloco de controlo widget de vista de texto rico

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom rich text view drawing function. */

VOID my_rich_text_view_draw(GX_RICH_TEXT_VIEW *text_view)
{
    /* Insert code here to draw rich text view background. */

    /* Call support function to do text drawing. */
    gx_rich_text_view_text_draw();

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *) rich_text_view);
}
```

### <a name="see-also"></a>Consulte também

- gx_rich_text_view_create
- gx_rich_text_view_draw
- gx_rich_text_view_fonts_set

## <a name="gx_screen_stack_create"></a>gx_screen_stack_create


Inicialize uma pilha de tela

### <a name="prototype"></a>Prototype

```C
UINT gx_screen_stack_create(
    GX_SCREEN_STACK_CONTROL *control,
    GX_WIDGET **memory_buffer, 
    INT buffer_size);
```

### <a name="description"></a>Descrição

Este serviço inicializa uma pilha de ecrã. A aplicação deve definir o bloco de memória e o tamanho do tampão utilizados para implementar a função de pilha de ecrã.

> [!NOTE]
> *Esta API é obsoleta e é substituída por gx_system_screen_stack_create(). Esta versão está prevista apenas para retrocompatibilidade com versões anteriores da biblioteca..*

### <a name="parameters"></a>Parâmetros

- **controlo** Bloco de controlo de pilha de tela
- **memory_buffer** Ponteiro para um tampão de memória que usado como uma pilha de tela
- **buffer_size** Tamanho da memória em bytes

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Pilha de ecrã bem sucedida criar
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_VALUE** (0x22) Tamanho do tampão inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
#define SCREEN_STACK_SIZE 10

GX_SCREEN_STACK_CONTROL my_stack_control;
GX_WIDGET *screen_stack[SCREEN_STACK_SIZE];

/* Initialize “my_stack_control”. */
status = gx_screen_stack_create(&my_stack_control, screen_stack,
                        SCREEN_STACK_SIZE * sizeof(GX_WIDGET *));

/* If status is GX_SUCCESS the screen control block “my_stack control” has been initialized. */
```

### <a name="see-also"></a>Consulte também

- gx_screen_stack_push
- gx_screen_stack_pop
- gx_screen_stack_reset

## <a name="gx_screen_stack_pop"></a>gx_screen_stack_pop


Remova a entrada mais alta da pilha de ecrã

### <a name="prototype"></a>Prototype

```C
UINT gx_screen_stack_pop(GX_SCREEN_STACK_CONTROL *control);
```

### <a name="description"></a>Descrição

Este serviço remove a entrada mais alta da pilha de ecrã e liga o ecrã estalado ao seu progenitor anterior. Esta API também separa quaisquer crianças existentes do progenitor.

> [!NOTE]
> *Esta API é obsoleta e é substituída por gx_system_screen_stack_pop(). Esta versão está prevista apenas para retrocompatibilidade com versões anteriores da biblioteca..*

### <a name="parameters"></a>Parâmetros

- **controlo** Bloco de controlo de pilha de tela

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Pop de pilha de ecrã bem-sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Remove the topmost entry from the screen stack. */
status = gx_screen_stack_pop(&my_stack_control);

/* If status is GX_SUCCESS the topmost entry has been removed from the screen stack, 
    and the popped screen has been attached to its parent. */
```

### <a name="see-also"></a>Consulte também

- gx_screen_stack_create
- gx_screen_stack_push
- gx_screen_stack_reset

## <a name="gx_screen_stack_push"></a>gx_screen_stack_push


Push screen e seus pais para empilhar

### <a name="prototype"></a>Prototype

```C
UINT gx_screen_stack_push(
    GX_SCREEN_STACK_CONTROL *control,
    GX_WIDGET *screen,
    GX_WIDGET *new_screen);
```

### <a name="description"></a>Descrição

Este serviço separa o ecrã do seu progenitor e empurra o ponteiro do ecrã e o ponteiro dos pais para a pilha de ecrã. O novo ponteiro de ecrã é então ligado ao progenitor.


> [!NOTE]
> *Esta API é obsoleta e é substituída por gx_system_screen_stack_pop(). Esta versão está prevista apenas para retrocompatibilidade com versões anteriores da biblioteca..*

### <a name="parameters"></a>Parâmetros

- **controlo** Bloco de controlo de pilha de tela
- **tela** Ponteiro de tela para empurrar
- **new_screen** Ponteiro do novo ecrã

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Push de pilha de tela bem sucedida
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Push “screen” and its parent to screen stack, Dettach “screen” from its parent, and attach “new screen” to the parent. */
status = gx_screen_stack_push(&my_stack_control,
                                screen, new_screen);

/* If status is GX_SUCCESS the widget “screen” and its parent have been pushed to screen stack, “screen” has been detached from its parent, “new_screen” has been attached to the parent. */
```

### <a name="see-also"></a>Consulte também

- gx_screen_stack_create
- gx_screen_stack_push
- gx_screen_stack_reset

## <a name="gx_screen_stack_reset"></a>gx_screen_stack_reset


Remove todas as entradas da pilha de ecrã

### <a name="prototype"></a>Prototype

```C
UINT gx_screen_stack_reset(GX_SCREEN_STACK_CONTROL *control);
```

### <a name="description"></a>Descrição

Este serviço remove todas as entradas da pilha de ecrã.

> [!NOTE]
> *Esta API é obsoleta e é substituída por gx_system_screen_stack_pop(). Esta versão está prevista apenas para retrocompatibilidade com versões anteriores da biblioteca..*

### <a name="parameters"></a>Parâmetros

- **controlo** Bloco de controlo de pilha de tela

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Cria o polegar de pergaminho bem sucedido
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Remove all enteries from the screen stack. */
status = gx_screen_stack_reset(&my_stack_control);

/* If status is GX_SUCCESS all entries of screen stack has been removed. */
```

### <a name="see-also"></a>Consulte também

- gx_screen_stack_create
- gx_screen_stack_push
- gx_screen_stack_pop

## <a name="gx_scroll_thumb_create"></a>gx_scroll_thumb_create


Criar polegar de pergaminho

### <a name="prototype"></a>Prototype

```C
UINT gx_scroll_thumb_create(
    GX_SCROLL_THUMB *scroll_thumb,
    GX_SCROLLBAR *parent, ULONG style);
```

### <a name="description"></a>Descrição

Este serviço cria uma roda de polegar de deslocal. Este serviço é normalmente chamado internamente quando um GX_SCROLLBAR é criado, mas é tornado público de forma a permitir implementações personalizadas de barra de deslocamento.

### <a name="parameters"></a>Parâmetros

- **scroll_thumb** Bloqueie o bloco de controlo do widget do polegar do polegar
- **pai** Ponteiro para a barra de pergaminho dos pais
- **estilo** Estilo de widget de barra de rolo. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Cria o polegar de pergaminho bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido
- **GX_INVALID_WIDGET** (0x12) Widget dos pais não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_SCROLL_THUMB my_scroll_thumb;

/* Create scroll thumb “my_scroll_thumb”. */
status = gx_scroll_thumb_create(&my_scroll_thumb, &my_scrollbar,
                                GX_STYLE_NONE);

/* If status is GX_SUCCESS the scroll thumb “my_scroll_thumb” has been created. */
```

### <a name="see-also"></a>Consulte também

- gx_scroll_thumb_draw
- gx_scroll_thumb_event_process

## <a name="gx_scroll_thumb_draw"></a>gx_scroll_thumb_draw


Desenhe o polegar do pergaminho

### <a name="prototype"></a>Prototype

```C
VOID gx_scroll_thumb_draw(GX_SCROLL_THUMB *scroll_thumb);
```

### <a name="description"></a>Descrição

Este serviço desenha uma roda de polegar de deslocal. Este serviço é chamado internamente pela atualização de tela GUIX, mas também pode ser chamado por funções de desenho overridden.

### <a name="parameters"></a>Parâmetros

- **scroll_thumb** Bloqueie o bloco de controlo do widget do polegar do polegar

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom scroll thumb drawing function. */

VOID my_scroll_thumb_draw(GX_SCROLL_THUMB *thumb)
{
    /* Call default scroll thumb draw. */
    gx_scroll_thumb_draw(thumb);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_scroll_thumb_create
- gx_scroll_thumb_event_process

## <a name="gx_scroll_thumb_event_process"></a>gx_scroll_thumb_event_process


Evento de polegar de pergaminho de processo

### <a name="prototype"></a>Prototype

```C
UINT gx_scroll_thumb_event_process(
    GX_SCROLL_THUMB *scroll_thumb,
    GX_EVENT *event);
```

### <a name="description"></a>Descrição

Este serviço trata dos eventos enviados para uma roda de polegar de uma barra de deslocação. Este serviço é normalmente utilizado internamente pelo GUIX, mas é tornado público para ajudar na implementação de comportamentos personalizados da barra de deslocamento.

### <a name="parameters"></a>Parâmetros

- **scroll_thumb** Bloqueie o bloco de controlo do widget do polegar do polegar
- **evento** Ponteiro para o evento para processar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Processo de evento de polegar de pergaminho bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Write a custom event processing function. */

UINT my_event_process (GX_SCROLL_THUMB *thumb, GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_scroll_thumb_event_process(thumb, event_ptr);

        /* add my own handling here */
        break;
    default:
        status = gx_scroll_thumb_event_process(thumb, event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Consulte também

- gx_scroll_thumb_create
- gx_scroll_thumb_draw

## <a name="gx_scroll_wheel_create"></a>gx_scroll_wheel_create


Criar um widget de roda de rolo base

### <a name="prototype"></a>Prototype

```C
UINT gx_scroll_wheel_create( 
    GX_SCROLL_WHEEL *wheel, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    INT total_rows, 
    ULONG style,
    USHORT id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria um widget genérico de roda de deslocação.

Uma roda de deslocação genérica é o widget base para todos os tipos de widgets de roda de deslocação, incluindo o *gx_text_scroll_wheel*** que é a base para widgets *gx_numeric_scroll_wheel*** e *gx_string_ scroll_wheel**.* O widget da roda de deslocação base fornece manuseamento de eventos, animação de deslocação e cálculo de linha selecionado para todos os tipos de widgets de roda de deslocamento.

As aplicações normalmente não criariam um exemplo de um widget genérico da roda de deslocação, uma vez que este tipo de widget não fornece nenhuma função de desenho. No entanto, o acesso a esta API é fornecido para ajudar aplicações que precisam de criar um tipo de widget de roda de deslocação personalizado.

GX_SCROLL_WHEEL baseia-se em GX_WINDOW e, portanto, todas as APIs GX_WINDOW podem ser utilizadas com GX_SCROLL_WHEEL e widgets derivados de GX_SCROLL_WHEEL.

### <a name="parameters"></a>Parâmetros

- **roda** Ponteiro para bloco de controlo genérico da roda de deslocamento
- **nome** Nome do widget atribuído à aplicação
- **pai** Widget dos pais, ou GX_NULL
- **total_rows** Total de linhas disponíveis
- **estilo** Bandeiras de estilo Widget
- **Id** Aplicação atribuída widget ID
- **tamanho** Retângulo definindo o tamanho inicial do widget.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) criou com sucesso a roda de pergaminho
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo inválido
- Widget **GX_ALREADY_CREATED** (0x13) criado
- **GX_INVALID_WIDGET** (0x12) Widget dos pais não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Call generic create function during custom widget createl. */

UINT custom_scroll_wheel_create(CUSTOM_SCROLL_WHEEL *wheel,
                    GX_CONST GX_CHAR *name,
                    GX_WIDGET *parent,
                    INT total_rows, ULONG style,
                    USHORT id,
                    GX_CONST GX_RECTANGLE *size)
{
    /* create base widget as part of custom create */
    status = gx_scroll_wheel_create(wheel, name, parent,
                            total_rows, style, id, size);

    /* If status is GX_SUCCESS the base scroll wheel has been created. */
}
```

### <a name="see-also"></a>Consulte também

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_event_process"></a>gx_scroll_wheel_event_process


Função de processamento de eventos para widget de roda de deslocamento genérico

### <a name="prototype"></a>Prototype

```C
UINT gx_scroll_wheel_event_process(
    GX_SCROLL_WHEEL *wheel,
    GX_EVENT *event);
```

### <a name="description"></a>Descrição

Este serviço fornece o manuseamento básico do evento de entrada para todos os tipos de widgets de roda de deslocação.

Esta função está exposta ao software de aplicação para ajudar com aplicações que precisam de criar um tipo de widget de roda de deslocação personalizada. As aplicações muitas vezes forneceriam a sua própria função de processamento de eventos, mas invocam o processamento genérico de eventos para widgets de rodas para eventos que não precisam de personalizar.

### <a name="parameters"></a>Parâmetros

- **roda** Ponteiro para bloco de controlo genérico da roda de deslocamento
- **evento** ponteiro GX_EVENT

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Processo de evento de roda de deslocação com sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Call generic scroll wheel event processing 
    as part of custom event processing function. */

UINT custom_scroll_wheel_event_process(CUSTOM_SCROLL_WHEEL *wheel,
                    GX_EVENT *event)
{
    switch(event->gx_event_type)
    {
    case xyz:
        /* insert custom event handling here */
        break;

    default:
        /* pass all other events to the generic scroll wheel
            event processing */
        gx_scroll_wheel_event_process(wheel, event);
        break;
    }
}
```


### <a name="see-also"></a>Consulte também

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_gradient_alpha_set"></a>gx_scroll_wheel_gradient_alpha_set


Atribuir valores alfa de gradiente para gradiente de sobreposição opcional

### <a name="prototype"></a>Prototype

```C
UINT gx_scroll_wheel_gradient_alpha_set(
    GX_SCROLL_WHEEL *wheel,
    GX_UBYTE start_alpha,
    GX_UBYTE end_alpha);
```

### <a name="description"></a>Descrição

Este serviço define os valores alfa inicial e final para uma sobreposição opcional do gradiente do widget da roda de deslocamento.

Todos os widgets da roda de deslocação suportam um efeito "desvanecimento" das linhas das rodas de deslocamento, à medida que as filas se aproximam da borda superior e inferior do widget da roda de deslocamento. Este efeito de desvanecimento é conseguido desenhando um pixelmap gradiente sobre as linhas das rodas de deslocamento, que fazem com que as linhas pareçam desaparecer à medida que as linhas são desenhadas perto da parte superior e inferior do widget da roda de deslocamento.

Este serviço API permite que a aplicação modifique a intensidade do efeito de desvanecimento, ou desative totalmente este efeito, definindo os valores alfa de início e fim para 0.

O mapa de pixels gradiente é criado em tempo de execução quando a roda de deslocação se torna inicialmente visível. Isto requer que tenha sido definido um serviço de atribuição de memória em tempo de execução utilizando _gx_system_memory_allocator_set(). Se não tiver sido definida nenhuma função de alocador de memória, a imagem de gradiente não será criada e nenhum efeito de desvanecimento estará disponível.

### <a name="parameters"></a>Parâmetros

- **roda** Ponteiro para bloco de controlo genérico da roda de deslocamento
- **start_alpha** O gradiente sobreposto que inicia o valor alfa.
- **end_alpha** O gradiente sobreposto que termina o valor alfa.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso o alfa de gradiente de roda de roda de deslocação
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
status = gx_scroll_wheel_gradient_alpha_set(&wheel, 240, 0);
/* if status == GX_SUCCESS the wheel gradient alpha values were
Successfully assigned. */
```

### <a name="see-also"></a>Consulte também

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_row_height_set"></a>gx_scroll_wheel_row_height_set


Atribua a altura da linha para cada linha de roda

### <a name="prototype"></a>Prototype

```C
UINT gx_scroll_wheel_row_height_set(
    GX_SCROLL_WHEEL *wheel,
    GX_VALUE row_height);
```

### <a name="description"></a>Descrição

Este serviço atribui a altura da linha para cada linha da roda de deslocação. Note que se a roda de deslocação tiver GX_STYLE_TEXT_SCROLL_WHEEL_ROUND de estilo, a altura da linha passa através de uma transformação que reduz eficazmente a altura da linha à medida que a linha se aproxima da borda superior ou inferior da roda.

### <a name="parameters"></a>Parâmetros

- **roda** Ponteiro para bloco de controlo genérico da roda de deslocamento
- **row_height** Valor da altura da linha, em pixels.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso a altura da roda do pergaminho
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
status = gx_scroll_wheel_row_height_set(&wheel, 40);

/* if status == GX_SUCCESS the wheel row height has been set to 40
pixels. */
```

### <a name="see-also"></a>Consulte também

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_gradient_alpha_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_selected_background_set"></a>gx_scroll_wheel_selected_background_set


Atribuir imagem de fundo para a linha selecionada da roda

### <a name="prototype"></a>Prototype

```C
UINT gx_scroll_wheel_selected_background_set(
    GX_SCROLL_WHEEL*wheel, 
    GX_RESOURCE_ID image_id);
```

### <a name="description"></a>Descrição

Este serviço atribui um ID de pixelmap opcional que é desenhado atrás da linha selecionada da roda de deslocação. Isto pode ser usado para destacar a linha selecionada para que o utilizador possa facilmente distinguir qual a linha da roda de deslocação selecionada.

### <a name="parameters"></a>Parâmetros

- **roda** Ponteiro para bloco de controlo genérico da roda de deslocamento
- **image_id** Pixelmap ID para usar como a imagem de fundo de linha selecionada.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso o fundo da roda do pergaminho
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
status = gx_scroll_wheel_selected_background_set(&wheel,
GX_PIXELMAP_ID_SELECTED_ROW);

/* if status == GX_SUCCESS the background image has been
assigned. */
```

### <a name="see-also"></a>Consulte também

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_selected_get"></a>gx_scroll_wheel_selected_get


Recupere a linha de rodas atualmente selecionada

### <a name="prototype"></a>Prototype

```C
UINT gx_scroll_wheel_selected_get(
    GX_SCROLL_WHEEL *wheel,
    INT *row);
```

### <a name="description"></a>Descrição

Este serviço irá consultar a roda de deslocação para recuperar a linha atualmente selecionada. O chamador deve passar o local para devolver o índice de linha selecionado como o segundo parâmetro para esta função.

### <a name="parameters"></a>Parâmetros

- **roda** Ponteiro para bloco de controlo genérico da roda de deslocamento
- **linha** Local no qual o valor de linha selecionado será devolvido.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) recuperou com sucesso a linha de rodas selecionada
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x19) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
INT row;
status = gx_scroll_wheel_selected_get(&wheel, &row);

/* if status == GX_SUCCESS the selected row has been returned in
the row variable. */
```

### <a name="see-also"></a>Consulte também

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_selected_set"></a>gx_scroll_wheel_selected_set


Atribuir linha de roda de deslocação selecionada

### <a name="prototype"></a>Prototype

```C
UINT gx_scroll_wheel_selected_set(
    GX_SCROLL_WHEEL *wheel,
    INT row);
```

### <a name="description"></a>Descrição

Este serviço atribui a linha de roda de deslocal já selecionada.

### <a name="parameters"></a>Parâmetros

- **roda** Ponteiro para bloco de controlo genérico da roda de deslocamento
- **linha** Linha da roda de deslocação a selecionar.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso a linha de rodas selecionada
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
status = gx_scroll_wheel_selected_set(&wheel, 20);

/* if status == GX_SUCCESS the scroll wheel has been set to select
row 20 */
```

### <a name="see-also"></a>Consulte também

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_speed_set"></a>gx_scroll_wheel_speed_set


Atribuir velocidade de deslocamento

### <a name="prototype"></a>Prototype

```C
UINT gx_scroll_wheel_speed_set(
    GX_SCROLL_WHEEL *wheel,
    GX_FIXED_VAL start_speed_rate,
    GX_FIXED_VAL end_speed_rate,
    GX_VALUE max_steps,
    GX_VALUE delay);
```

### <a name="description"></a>Descrição

Este serviço atribui a velocidade de deslocação para o widget da roda de deslocamento.

### <a name="parameters"></a>Parâmetros

- **roda** Ponteiro para bloco de controlo genérico da roda de deslocamento
- **start_speed_rate** A velocidade de deslocamento da velocidade de início para a velocidade do movimento.
- **end_speed_rate** A velocidade de roer velocidade final para a velocidade do movimento
- **max_steps** Passos max para rolar.
- **atraso** Atrase o tempo de cada passo.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso a velocidade da roda
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido
- **GX_INVALID_VALUE** (0x22) Valor inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
status = gx_scroll_wheel_speed_set(&wheel, GX_FIXED_VAL_MAKE(2),
                                GX_FIXED_VAL_MAKE(1) / 2, 10, 2);

/* if status == GX_SUCCESS the scroll wheel speed has been
successfully set. */
```

### <a name="see-also"></a>Consulte também

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_total_rows_set"></a>gx_scroll_wheel_total_rows_set


Atribua o total de linhas de roda de deslocação disponíveis

### <a name="prototype"></a>Prototype

```C
UINT gx_scroll_wheel_total_rows_set(
    GX_SCROLL_WHEEL *wheel,
    INT total_rows);
```

### <a name="description"></a>Descrição

Este serviço atribui o número de linhas disponíveis na roda de deslocação indicada. O widget da roda de deslocação geralmente recebe o conteúdo da linha da aplicação sob a forma de uma matriz de cordas ou dados de cadeia fornecidos pelo utilizador. Esta API informa a roda de deslocação do número total de linhas que devem ser apresentadas ao utilizador.

### <a name="parameters"></a>Parâmetros

- **roda** Ponteiro para bloco de controlo genérico da roda de deslocamento
- **total_rows** Número total de linhas de roda para apresentar ao utilizador.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso a roda de deslocalismo linha total
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido
- **GX_INVALID_VALUE** (0x22) Valor inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
status = gx_scroll_wheel_total_rows_set(&wheel, 100);

/* if status == GX_SUCCESS the scroll wheel has been changed to
display 100 total rows */
```
### <a name="see-also"></a>Consulte também

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scrollbar_draw"></a>gx_scrollbar_draw


Desenhar barra de deslocal

### <a name="prototype"></a>Prototype

```C
VOID gx_scrollbar_draw(GX_SCROLLBAR *scrollbar);
```

### <a name="description"></a>Descrição

Este serviço desenha uma barra de deslocação. Uma função de desenho comum é utilizada para widgets verticais e horizontais da barra de deslocamento. Este serviço é chamado internamente pela atualização de tela GUIX, mas também pode ser chamado por funções de desenho overridden.

### <a name="parameters"></a>Parâmetros

- **barra de scroll** Widget de barra de rolo para desenhar

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom scrollbar drawing function. */

VOID my_scrollbar_draw(GX_SCROLLBAR *scrollbar)
{
    /* Call default scrollbar draw. */
    gx_scrollbar_draw(thumb);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_ horizontal_scrollbar_create
- gx_scrollbar_event_process
- gx_scrollbar_limit_check
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_scrollbar_event_process"></a>gx_scrollbar_event_process


Evento de barra de pergaminho de processo

### <a name="prototype"></a>Prototype

```C
UINT gx_scrollbar_event_process(
    GX_SCROLLBAR *scrollbar,
    GX_EVENT *event);
```

### <a name="description"></a>Descrição

Este serviço processa um evento de barra de deslocamento. Uma função comum de manuseamento de eventos utilizada para widgets verticais e horizontais da barra de deslocamento.

### <a name="parameters"></a>Parâmetros

- **barra de scroll** Bloco de controlo widget de barra de rolo
- **evento** Ponteiro para o evento para processar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Processo de evento de scrollbar bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
Call generic scrollbar event processing as part of custom event processing function. */

UINT custom_scrollbar_event_process(GX_SCROLLBAR *scrollbar,
                                    GX_EVENT *event)
{
    switch(event->gx_event_type)
    {
    case xyz:
        /* insert custom event handling here */
        break;
    default:
        /* pass all other events to the generic scrollbar
            event processing */
        gx_scrollbar_event_process(scrollbar, event);
        break;
    }
}
```

### <a name="see-also"></a>Consulte também

- gx_ horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_limit_check
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_scrollbar_limit_check"></a>gx_scrollbar_limit_check


Verifique o limite da barra de deslocação

### <a name="prototype"></a>Prototype

```C
UINT gx_scrollbar_limit_check(GX_SCROLLBAR *scrollbar);
```

### <a name="description"></a>Descrição

Este serviço verifica o limite da barra de deslocação e impede que a roda do polegar da barra de deslocação viaje para além dos limites predefinidos.

### <a name="parameters"></a>Parâmetros

- **barra de scroll** Bloco de controlo widget de barra de rolo

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Verificação de limites de barra de deslocação bem sucedida
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Check scrollbar limit of “my_scrollbar”. */
status = gx_scrollbar_limit_check(&my_scrollbar);

/* If status is GX_SUCCESS the limit of scrollbar “my_scrollbar” has been checked. */
```

### <a name="see-also"></a>Consulte também

- gx_horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_event_process
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_scrollbar_reset"></a>gx_scrollbar_reset


Barra de deslocamento de reset

### <a name="prototype"></a>Prototype

```C
UINT gx_scrollbar_reset(
    GX_SCROLLBAR *scrollbar,
    GX_SCROLL_INFO *info);
```

### <a name="description"></a>Descrição

Este serviço reinicia a barra de deslocação.

### <a name="parameters"></a>Parâmetros

- **barra de scroll** Bloco de controlo widget de barra de rolo
- **informação** Ponteiro para GX_SCROLL_INFO estrutura que define os limites da barra de deslocamento, valor atual e passo ou incremento. **O apêndice I** contém definição para GX_SCROLL_INFO estrutura.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Reset da barra de deslocamento bem sucedida
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido
- **GX_INVALID_VALUE** (0x22) Informações de deslocação não válidas

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Reset scrollbar “my_scrollbar”. */

GX_SCROLL_INFO my_info;

my_info.gx_scroll_value = 0;
my_info.gx_scroll_minimum = 0;
my_info.gx_scroll_maximum = 100;
my_info.gx_scroll_visible = 10;
my_info.gx_scroll_increment = 1;

status = gx_scrollbar_reset(&my_scrollbar, &my_info);

/* If status is GX_SUCCESS the scrollbar “my_scrollbar” has been reset. */
```

### <a name="see-also"></a>Consulte também

- gx_horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_event_process
- gx_scrollbar_limit_check
- gx_vertical_scrollbar_create

## <a name="gx_scrollbar_value_set"></a>gx_scrollbar_value_set


Atribuir valor da barra de deslocação

### <a name="prototype"></a>Prototype

```C
UINT gx_scrollbar_value_set(
    GX_SCROLLBAR *scrollbar,
    INT value);
```

### <a name="description"></a>Descrição

Este serviço atribui o valor atual da barra de deslocação. Um evento GX_EVENT_VERTICAL_SCROLL ou GX_EVENT_HORIZONTAL_SCROLL será gerado para a janela dos pais.

### <a name="parameters"></a>Parâmetros

- **barra de scroll** Bloco de controlo widget de barra de rolo
- **valor** Novo valor da barra de deslocação

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Processo de evento de scrollbar bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido
- **GX_INVALID_VALUE** (0x22) O valor do pergaminho não é válido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Assign new value for scrollbar “my_scrollbar”. */

status = gx_scrollbar_value_set(&my_scrollbar, 0);

/* If status is GX_SUCCESS the current position of scrollbar “my_scrollbar” has been set. */

```

### <a name="see-also"></a>Consulte também

- gx_horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_limit_check
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_single_line_text_input_backspace"></a>gx_single_line_text_input_backspace


Processar um personagem de backspace no widget de entrada de texto

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_backspace(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Descrição

Este serviço elimina o carácter antes da posição do cursor de entrada de texto. Este serviço é chamado internamente quando um evento de chave de backspace para baixo é recebido, mas também pode ser invocado pela aplicação.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto de linha única

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Entrada de texto de linha única bem sucedida cria
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x23) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Delete a character before the cursor of “my_text_input”. */
status = gx_single_line_text_input_backspace(&my_text_input);

/* If status is GX_SUCCESS the character before the cursor has been deleted. */
```

### <a name="see-also"></a>Consulte também

- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_buffer_clear"></a>gx_single_line_text_input_buffer_clear


Elimina todos os caracteres do tampão de entrada de texto

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_buffer_clear(
    GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Descrição

Este serviço elimina todos os caracteres do tampão de entrada de texto.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto de linha única

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) limpou com sucesso o tampão de entrada de texto de linha única
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* clear input buffer of “my_text_input”. */
status = gx_single_line_text_input_clear(&my_text_input);

/* If status is GX_SUCCESS the text input widget has emptied its input buffer. */
```

### <a name="see-also"></a>Consulte também

- gx_single_line_text_input_buffer_backspace
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_buffer_get"></a>gx_single_line_text_input_buffer_get


Recupera informações tampão do widget de entrada de texto

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_buffer_get(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CHAR **buffer_address, 
    UINT *content_size, 
    UINT *buffer_size);
```

### <a name="description"></a>Descrição

Este serviço obtém informações tampão do widget de entrada de texto.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto de linha única
- **buffer_address** O endereço do tampão de entrada
- **content_size** A contagem byte dos dados de entrada
- **buffer_size** O tamanho do tampão de entrada

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) recuperou com sucesso informações sobre tampão
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_CHAR *buffer_address;
UINT buffer_size;
UINT content_size;

/* Retrieve buffer information of “my_text_input” widget. */
status = gx_single_line_text_input_buffer_get(&my_text_input,
                    &buffer_address, &string_size, &buffer_size);

/* If status is GX_SUCCESS the value of buffer_address, string_size and buffer_size has been retrieved. */
```

### <a name="see-also"></a>Consulte também

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_character_delete"></a>gx_single_line_text_input_character_delete


Elimine o carácter na posição atual do cursor

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_character_delete(
    GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Descrição

Este serviço elimina o carácter após a posição do cursor de entrada de texto. Este serviço é chamado internamente quando um evento de eliminação de chave para baixo é recebido, mas também pode ser invocado pela aplicação.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto de linha única

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) elimine com sucesso um personagem após o cursor
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Delete the character after the cursor of “my_text_input”. */
status = gx_single_line_text_input_character_delete(&my_text_input);

/* If status is GX_SUCCESS the character after the cursor has been deleted. */
```

### <a name="see-also"></a>Consulte também

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_multi_line_text_input_create
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_character_insert"></a>gx_single_line_text_input_character_insert


Insira uma cadeia de caracteres na posição atual do cursor

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_character_insert(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_UBYTE *insert_str,
    UINT insert_size);
```

### <a name="description"></a>Descrição

Este serviço insere uma cadeia de caracteres no tampão de cadeia de entrada de texto na posição atual do cursor.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto de linha única
- **insert_str** Cadeia de caracteres a ser inserida
- **insert_size** Contagem de byte a ser inserida

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Inseriu com sucesso o personagem
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Insert characters at current cursor position. */

GX_CHAR insert_text[10] = “insert”;
status = gx_single_line_text_input_character_insert(&my_text_input,
                                            insert_text,
                                            GX_STRLEN(insert_text));

/* If status is GX_SUCCESS the text input widget has successfully insert the string. */
```

### <a name="see-also"></a>Consulte também

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_create"></a>gx_single_line_text_input_create


Criar um widget de entrada de texto

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_create(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_CHAR *name, GX_WIDGET *parent,
    GX_CHAR *input_buffer, UINT buffer_size,
    UINT style, USHORT text_input_id, GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria um widget de entrada de texto. O chamador deve fornecer armazenamento para a cadeia de entrada e indicar o comprimento máximo da corda.

GX_SINGLE_LINE_TEXT_INPUT é derivado de GX_PROMPT e, portanto, todos os serviços gx_prompt podem ser utilizados com widgets GX_SINGLE_LINE_TEXT_INPUT.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto de linha única
- **nome** Nome lógico de widget opcional
- **pai** Widget parental opcional
- **input_buffer** Armazenamento para cadeia de entrada
- **buffer_size** Tamanho da área de armazenamento de cordas de entrada, em bytes.
- **estilo** Bandeiras de estilo de entrada de texto
- **text_input_id** ID opcional do widget de entrada
- **tamanho** Retângulo definindo o tamanho inicial do widget

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Entrada de texto de linha única bem sucedida cria
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_SINGLE_LINE_TEXT_INPUT my_text_input;
static GX_CHAR           text_input_buffer[100];
GX_RECTANGLE             size;

/* Define widget size. */
gx_utility_rectangle_define(&size, 10, 10, 110, 40);

/* Create single-line text input widget “my_text_input”. */
status = gx_single_line_text_input_create(&my_text_input,
                        “text_input”, GX_NULL, text_input_buffer, 100,
                        GX_STYLE_ENABLED, 0, &size);

/* If status is GX_SUCCESS, the text input widget has been created. */
```

### <a name="see-also"></a>Consulte também

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_draw"></a>gx_single_line_text_input_draw


Desenhe um widget de entrada de texto

### <a name="prototype"></a>Prototype

```C
VOID gx_single_line_text_input_draw(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Descrição

Este serviço desenha um widget de entrada de texto. Este serviço é normalmente chamado internamente durante a atualização de lona, mas também pode ser chamado de funções de desenho de entrada de texto personalizado.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto de linha única

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom single line text input draw function. */

VOID my_sl_text_input_draw(GX_SINGLE_LINE_TEXT_INPUT *input)
{
    /* Call default single line text input draw. */
    gx_single_line_text_input_draw(input);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_draw_position_get"></a>gx_single_line_text_input_draw_position_get


Recuperar a posição de início do desenho de texto

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_draw_position_get(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_VALUE *xpos, GX_VALUE *ypos);
```

### <a name="description"></a>Descrição

Este serviço recupera a posição inicial de desenho do texto de entrada de texto.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto de linha única
- **xpos** Recuperado posição de início de sorteio em x coordenada
- **ypos** Recuperado posição de início de sorteio em y coordenada

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) movimente com sucesso o cursor de entrada de texto para o fim
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Write a custom single line text input draw function. */

VOID my_sl_text_input_draw(GX_SINGLE_LINE_TEXT_INPUT *input)
{
GX_VALUE xpos;
GX_VALUE ypos;

    /* Draw background. */
    gx_widget_border_draw(input, border_color, upper_fill_color,
                          lower_fill_color, GX_TRUE);

    /* Retrieve text draw start position. */
    gx_single_line_text_input_draw_position_get(input, xpos,
                                                ypos);

    /* Add your text drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_end"></a>gx_single_line_text_input_end


Mova o cursor de entrada de texto para a extremidade da corda

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_end(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Descrição

Este serviço posiciona o cursor widget de entrada de texto na extremidade da cadeia de entrada. Este serviço é chamado internamente quando um evento de chave final para baixo é recebido, mas também pode ser invocado pela aplicação.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto de linha única

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) movimente com sucesso o cursor de entrada de texto para o fim
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Move input cursor to end. */
status = gx_single_line_text_input_end(&my_text_input);

/* If status is GX_SUCCESS, text text input cursor has been moved to end. */
```

### <a name="see-also"></a>Consulte também

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_event_process"></a>gx_single_line_text_input_event_process


Função de processamento de evento widget de entrada de texto

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_event_process(
    GX_SINGLE_LINE_TEXT_INPUT *text_input, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Descrição

Este serviço processa um evento de entrada de texto de uma única linha. Esta função é referenciada internamente pela função gx_single_line_text_input_create, mas está exposta para utilização pela aplicação nos casos em que a aplicação define uma função de processamento de evento de entrada de texto de linha única personalizada.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto de linha única
- **event_ptr** Ponteiro para GX_EVENT estrutura

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Evento de entrada de texto processado com sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Call generic single line text input event processing as part of custom event processing function. */

UINT custom_sl_text_input_event_process(
                                GX_SINGLE_LINE_TEXT_INPUT *input,
                                GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default single line
            text input event processing */
        status =
        gx_single_line_text_input_event_process(input, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Consulte também

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_fill_color_set"></a>gx_single_line_text_input_fill_color_set


Definir cor de fundo de fundo de entrada de texto de linha única

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_fill_color_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_fill_color_id,
    GX_RESOURCE_ID selected_fill_color_id,
    GX_RESOURCE_ID disabled_fill_color_id,
    GX_RESOURCE_ID readonly_fill_color_id);
```

### <a name="description"></a>Descrição

Este serviço define a cor de preenchimento da entrada de texto de linha única.

### <a name="parameters"></a>Parâmetros

- **text_input** Ponteiro para bloco de controlo de entrada de texto de linha única
- **normal_fill_color_id** Identificação de recursos do widget preencha a cor em estado normal. **O apêndice A** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.
- **selected_fill_color_id** ID de recurso da cor de preenchimento do widget quando o widget ganhar foco. **O apêndice A** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.
- **disabled_fill_color_id** ID de recurso da cor de preenchimento do widget quando o estilo GX_STYLE_ENABLED não está definido. **O apêndice A** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.
- **readonly_fill_color_id** ID de recurso da cor de preenchimento do widget quando ambos os GX_STYLE_ENABLED de estilo e GX_STYLE_TEXT_INPUT_READYONLY estão definidos. **O apêndice A** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de cores de preenchimento de texto de linha única bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set fill colors for single line text input “my_text_input”. */
status = gx_single_line_text_input_fill_color_set(&my_text_input,
                    GX_COLOR_ID_NORMAL_FILL,
                    GX_COLOR_ID_SELECTED_FILL,
                    GX_COLOR_ID_DISABLED_FILL,
                    GX_COLOR_ID_READONLY_FILL);

/* If status is GX_SUCCESS, the fill color of “my_text_input” was
set. */
```

### <a name="see-also"></a>Consulte também

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_home"></a>gx_single_line_text_input_home


Mova o cursor de entrada de texto para a posição de casa

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_home(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Descrição

Este serviço move a posição do cursor de entrada de texto para o início da cadeia de entrada. Este serviço é chamado internamente quando um evento de home key down é recebido, mas também pode ser invocado pela aplicação.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto de linha única

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) mudou com sucesso cursor para a posição da casa
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Move cursor to the start of the input text. */
status = gx_single_line_text_input_home(&my_text_input);

/* If status is GX_SUCCESS the cursor has been moved to the home position */
```

### <a name="see-also"></a>Consulte também
- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_left_arrow"></a>gx_single_line_text_input_left_arrow


Mover cursor de entrada um personagem para a esquerda

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_left_arrow(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Descrição

Este serviço move o cursor de entrada de texto um caracter para a esquerda. Este serviço é chamado internamente quando um evento de chave esquerda para baixo é recebido, mas também pode ser invocado pela aplicação.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto de linha única

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) moveu com sucesso o cursor para a esquerda
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Move the cursor one character to the left. */
status = gx_single_line_text_input_left_arrow(&my_text_input);

/* If status is GX_SUCCESS the text input cursor has been moved one character to the left. */
```

### <a name="see-also"></a>Consulte também

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_position_get"></a>gx_single_line_text_input_position_get

Mover cursor para a posição de pixel

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_position_get(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    INT pixel_position);
```

### <a name="description"></a>Descrição

Este serviço posiciona o cursor de entrada de texto com base na posição de pixel solicitado. O índice de cursor de entrada de texto será calculado com base no valor x da posição do pixel. Este serviço é chamado internamente quando um evento pen down é recebido, mas também pode ser invocado pela aplicação.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto de linha única
- **pixel_position** Valor X da posição do pixel

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso o cursor para a posição solicitada
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **widget** GX_INVALID_WIDGET (0x12) Inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set cursor to requested position. */
status = gx_single_line_text_input_position_get(&my_text_input,
                                                100);

/* If status is GX_SUCCESS the text input widget cursor has been positioned */
```

### <a name="see-also"></a>Consulte também

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_right_arrow"></a>gx_single_line_text_input_right_arrow


Mover cursor de entrada um personagem para a direita

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_right_arrow(
    GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Descrição

Este serviço move o cursor de entrada de texto de um personagem para a direita. Este serviço é chamado internamente quando um evento de chave direita para baixo é recebido, mas também pode ser invocado pela aplicação.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto de linha única

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) moveu com sucesso o cursor para a direita
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Move cursor one character to the right. */
status = gx_single_line_text_input_right_arrow(&my_text_input);

/* If status is GX_SUCCESS the text input cursor has been moved one character to the right. */
```

### <a name="see-also"></a>Consulte também

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_position_get
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_style_add"></a>gx_single_line_text_input_style_add


Adicionar estilos

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_style_add(
    GX_SINGLE_LINE_TEXT_INPUT *text_input, 
    ULONG style);
```

### <a name="description"></a>Descrição

Este serviço adiciona o(s) estilo especificado ao widget de entrada de texto de linha única.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto de linha única
- **estilo** Novo estilo para adicionar. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) adicionou com sucesso o estilo ao widget
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Add a new style to “my_text_input”. */
status = gx_single_line_text_input_style_add(&my_text_input,
GX_STYLE_CURSOR_AWAYS);

/* If status is GX_SUCCESS the GX_STYLE_CUSROSR_SHOR have been successfully added. */
```

### <a name="see-also"></a>Consulte também

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gax_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_style_remove"></a>gx_single_line_text_input_style_remove

Remover estilos

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_style_remove(
    GX_SINGLE_LINE_TEXT_INPUT *text_input, 
    ULONG style);
```

### <a name="description"></a>Descrição

Este serviço remove o(s) estilo especificado(s) do widget de entrada de texto de linha única.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto de linha única
- **estilo** Estilo para remover. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Estilos removidos com sucesso do widget
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Remove cursor blink style from “my_text_input”. */
status = gx_single_line_text_input_style_remove(&my_text_input,
GX_STYLE_CURSOR_BLINK);

/* If status is GX_SUCCESS the GX_STYLE_CURSOR_BLINK style has been successfully removed. */
```

### <a name="see-also"></a>Consulte também

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_home
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_style_set"></a>gx_single_line_text_input_style_set


Definir estilos de entrada de texto

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_style_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input, 
    ULONG style);
```

### <a name="description"></a>Descrição

Este serviço define o(s) estilo especificado para o widget de entrada de texto de linha única.

### <a name="parameters"></a>Parâmetros

- **text_input** Bloco de controlo widget de entrada de texto de linha única
- bandeiras **de** estilo estilo para atribuir

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso o estilo de entrada de texto
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set style for “my_text_input”. */
status = gx_single_line_text_input_style_set(&my_text_input,
                    GX_STYLE_ENABLED | GX_STYLE_CURSOR_BLINK);

/* If status is GX_SUCCESS the text input style has been successfully set to the specified styles. */
```

### <a name="see-also"></a>Consulte também

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_signle_line_text_input_event_process
- gx_single_line_text_input_home
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_text_color_set"></a>gx_single_line_text_input_text_color_set


Definir a cor do texto de entrada de texto de linha única

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_text_color_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCE_ID disabled_text_color_id,
    GX_RESOURCE_ID readonly_text_color_id);
```

### <a name="description"></a>Descrição

Este serviço define a cor de texto da entrada de texto de linha única.

### <a name="parameters"></a>Parâmetros

- **text_input** Ponteiro para bloco de controlo de entrada de texto de linha única
- **normal_text_color_id** Identificação de recursos da cor do texto em estado normal. **O apêndice A** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.
- **selected_text_color_id** ID de recurso da cor do texto quando o widget ganhar foco. **O apêndice A** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.
- **disabled_text_color_id** ID de recurso da cor do texto quando o estilo GX_STYLE_ENABLED não está definido. **O apêndice A** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.
- **readonly_text_color_id** ID de recurso da cor do texto quando ambos os GX_STYLE_ENABLED de estilo e GX_STYLE_TEXT_INPUT_READONLY são definidos. **O apêndice A** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de cores de texto de entrada de texto de linha única bem-sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set text colors for single line text input “my_text_input”. */
status = gx_single_line_text_input_text_color_set(&my_text_input,
                                        GX_COLOR_ID_NORMAL_TEXT,
                                        GX_COLOR_ID_SELECTED_TEXT,
                                        GX_COLOR_ID_DISABLED_TEXT,
                                        GX_COLOR_ID_READONLY_TEXT);

/* If status is GX_SUCCESS, the text color “my_text_input” was set. */
```

### <a name="see-also"></a>Consulte também

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_text_select"></a>gx_single_line_text_input_text_select

Selecione texto

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_text_color_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    UINT start_index, UINT end_index);
```

### <a name="description"></a>Descrição

Este serviço seleciona texto com índice de marca de início e de marca final especificado e destaca o texto selecionado com as cores de preenchimento e texto selecionados.

### <a name="parameters"></a>Parâmetros

- **text_input** Ponteiro para bloco de controlo de entrada de texto de linha única
- **start_index** Índice do primeiro caráter selecionado
- **end_index** Índice do último caráter selecionado

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Seleção de texto de entrada de texto de linha única bem sucedida
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido
- **GX_INVALID_VALUE** (0x22) Valor do índice não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Select text between index [0, 9]. */
status = gx_single_line_text_input_text_select(&my_text_input,
                                                0,9);

/* If status is GX_SUCCESS, the text between index [0, 9] “my_text_input” was selected. */
```

### <a name="see-also"></a>Consulte também

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_text_set"></a>gx_single_line_text_input_text_set


Definir texto de entrada de texto de linha única (precotado)

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_text_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_CHAR *text);
```

### <a name="description"></a>Descrição

Este serviço foi precotado a favor de gx_single_line_text_input_text_set_ext()

Este serviço define o texto da entrada de texto de linha única.

### <a name="parameters"></a>Parâmetros

- **text_input** Ponteiro para bloco de controlo de entrada de texto de linha única
- **texto** Cadeia de texto terminada nulo

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de cores de texto de entrada de texto de linha única bem-sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido
- **GX_INVALID_STRING_LENGTH** (0x34) Comprimento da corda inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_CONST GX_CHAR new_text = “Set Single Line Text Input Text”;

/* Set text for single line text input “my_text_input”. */
status = gx_single_line_text_input_text_set(&my_text_input,
                                        new_text);

/* If status is GX_SUCCESS, the text of “my_text_input” was set. */
```

### <a name="see-also"></a>Consulte também

- gx_single_line_text_input_text_set_ext

## <a name="gx_single_line_text_input_text_set_ext"></a>gx_single_line_text_input_text_set_ext


Definir texto de entrada de texto de linha única

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_text_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Descrição

Este serviço define o texto da entrada de texto de linha única.

### <a name="parameters"></a>Parâmetros

- **text_input** Ponteiro para bloco de controlo de entrada de texto de linha única
- **cadeia** variável GX_STRING

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de cores de texto de entrada de texto de linha única bem-sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido
- **GX_INVALID_STRING_LENGTH** (0x34) Comprimento da corda inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_STRING new_string;
new_string.gx_string_ptr = “Set Single Line Text Input Text”;
new_string.gx_string_length = strlen(new_string.gx_string_ptr);

/* Set text for single line text input “my_text_input”. */
status = gx_single_line_text_input_text_set_ext(&my_text_input,
                                        &new_string);

/* If status is GX_SUCCESS, the string has been assigned to my_text_input. */
```

### <a name="see-also"></a>Consulte também

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_set_ext


## <a name="gx_slider_create"></a>gx_slider_create

Criar slider

### <a name="prototype"></a>Prototype

```C
UINT gx_slider_create(
    GX_SLIDER *slider, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, INT tick_count,
    GX_SLIDER_INFO *slider_info,
    ULONG style, USHORT slider_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria um widget de slider.

GX_SLIDER é derivado de GX_WIDGET, pelo que todos os serviços gx_widget API podem ser utilizados com widgets GX_SLIDER tipo.

### <a name="parameters"></a>Parâmetros

- **slider**: Bloco de controlo de widget slider
- **nome**: Nome do deslizante
- **pai**: Ponteiro para widget dos pais
- **tick_count**: Número de carraças deslizantes
- **slider_info**: Ponteiro para deslizar informação que é uma estrutura usada para passar os limites de valor do deslizador, o tamanho e posição da agulha deslizante e outros parâmetros de slider. **O apêndice I** contém definição para GX_SLIDER_INFO estrutura.
- **estilo**: Estilo de slider. **O apêndice D** contém estilos gerais predefinidos para todos os widgets, bem como estilos específicos do widget.
- **slider_id**: ID definido por aplicação de slider
- **tamanho**: Dimensões do deslizante

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Criação de slider bem sucedido
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_ALREADY_CREATED**: (0x13) Widget já criado
- **GX_INVALID_SIZE**: (0x19) Tamanho do bloco de controlo de widget inválido
- **GX_INVALID_WIDGET**: (0x12) Widget parental não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Create slider “my_slider”. */

GX_SLIDER my_slider;
GX_SLIDER_INFO info;

info.gx_slider_info_min_val = 0;
info.gx_slider_info_max_val = 100;
info.gx_slider_info_current_val = 50;
info.gx_slider_info_increment = 1;
info.gx_slider_info_min_travel = 20;
info.gx_slider_info_max_travel = 20;
info.gx_slider_info_needle_width = 10;
info.gx_slider_info_needle_height = 10;
info.gx_slider_info_needle_inset = 5;
info.gx_slider_info_needle_hotspot_offset = 5;

status = gx_slider_create(&my_slider, “my_slider”,
    &my_parent, 10, info, GX_STYLE_ENABLED, ID_MY_SLIDER, &size);

/* If status is GX_SUCCESS the slider “my_slider” has been created. */
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_draw"></a>gx_slider_draw

Desenhe o slider

### <a name="prototype"></a>Prototype

```C
VOID gx_slider_draw(GX_SLIDER *slider);
```

### <a name="description"></a>Descrição

Este serviço desenha um slider. Este serviço é utilizado internamente pela função gx_slider_create, mas também é exposto para utilização pela aplicação nesses casos quando é definida uma função de desenho de slider personalizado.

### <a name="parameters"></a>Parâmetros

- **slider**: Bloco de controlo de widget slider

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom slider draw function. */
VOID my_slider_draw(GX_SLIDER *slider)
{
    /* Call default slider draw. */
    gx_slider_draw(slider);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_event_process"></a>gx_slider_event_process

Evento de slider de processo

### <a name="prototype"></a>Prototype

```C
UINT gx_slider_event_process(
    GX_SLIDER *slider, 
    GX_EVENT *event);
```

### <a name="description"></a>Descrição

Este serviço processa um evento de slider. Esta função é referenciada internamente pela função gx_slider_create, mas está exposta para utilização pela aplicação nos casos em que a aplicação define uma função de processamento de eventos de slider personalizado.

### <a name="parameters"></a>Parâmetros

- **slider**: Bloco de controlo de widget slider
- **evento**: Ponteiro para evento para processar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Processo de evento de slider bem sucedido
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Call generic slider event processing as part of custom event processing function. */

UINT custom_slider_event_process(GX_SLIDER *slider,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;
    switch(event->gx_event_type)
    {
        case xyz:
            /* Insert custom event handling here */
            break;
        default:
            /* Pass all other events to the default slider event processing */
            status = gx_slider_event_process(slider, event);
            break;
    }
    return status;
}
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_info_set"></a>gx_slider_info_set

Definir bloco de informações de slider

### <a name="prototype"></a>Prototype

```C
UINT gx_slider_info_set(
    GX_SLIDER *slider, 
    GX_SLIDER_INFO *info);
```

### <a name="description"></a>Descrição

Este serviço atribui as informações de slider especificadas, tais como o mínimo de slider, o máximo de deslizamento e o valor de corrente do slider para o deslizador indicado. O slider atualizará a posição da agulha e redesenhará com base nas novas informações de slider.

### <a name="parameters"></a>Parâmetros

- **slider**: Bloco de controlo de widget slider
- **informação**: Ponteiro para a estrutura de informação do slider. **O apêndice I** contém definição para GX_SLIDER_INFO estrutura.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Definir com sucesso informações de slider
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_SLIDER_INFO my_slider_info;
my_slider_info.gx_slider_info_min_val = 0;
my_slider_info.gx_slider_info_max_val = 100;
my_slider_info.gx_slider_info_current_val = 50;
my_slider_info.gx_slider_info_increment = 1;
my_slider_info.gx_slider_info_min_travel = 20;
my_slider_info.gx_slider_info_max_travel = 20;
my_slider_info.gx_slider_info_needle_width = 10;
my_slider_info.gx_slider_info_needle_height = 10;
my_slider_info.gx_slider_info_needle_inset = 5;

my_slider_info.gx_slider_info_needle_hotspot_offset = 5;

/* Set slider information for slider “my_slider”. */
status = gx_slider_info_set (&my_slider, &my_slider_info);

/* If status is GX_SUCCESS the “my_slider” is configured with my_slider_info. */
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_needle_draw"></a>gx_slider_needle_draw

Desenhe a agulha de slider

### <a name="prototype"></a>Prototype

```C
VOID gx_slider_needle_draw(GX_SLIDER *slider);
```

### <a name="description"></a>Descrição

Este serviço desenha uma agulha deslizante. Este serviço é automaticamente chamado pela função gx_slider_draw, mas também pode ser invocado pela aplicação como parte de uma função de desenho de slider personalizado.

### <a name="parameters"></a>Parâmetros

- **slider**: Bloco de controlo de widget slider

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom slider draw function. */
VOID my_slider_draw(GX_SLIDER *slider)
{
    /* Add your own background draw here. */

    /* Call default tickmarks draw. */
    gx_slider_tickmarks_draw(slider);

    /* Call default slider needle draw. */
    gx_slider_needle_draw(slider);
}
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_needle_position_get"></a>gx_slider_needle_position_get

Obtenha a posição da agulha deslizante

### <a name="prototype"></a>Prototype

```C
UINT gx_slider_needle_position_get(
    GX_SLIDER *slider,
    GX_SLIDER_INFO *slider_info,
    GX_RECTANGLE *return_position);
```

### <a name="description"></a>Descrição

Este serviço calcula a posição da agulha deslizante com base no valor atual do slider.

### <a name="parameters"></a>Parâmetros

- **slider**: Bloco de controlo de widget slider
- **slider_info**: Ponteiro para deslizar estrutura de informação que define os limites do deslizador, tamanho da agulha e offset, e outros parâmetros de slider. **O apêndice I** contém definição para GX_SLIDER_INFO estrutura.
- **return_position**: Ponter para o destino para a posição da agulha

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Posição de agulha de slider bem sucedida obter
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido
- **GX_INVALID_VALUE:**(0x22) Informações de slider não válidas

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_RECTANGLE needle_position;

/* Get the needle position for slider “my_slider”. */
status = gx_slider_needle_posistion_get(&my_slider, &slider_info,
    &needle_position);

/* If status is GX_SUCCESS the needle position for slider “my_slider” has been retrieved. */
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_tickmarks_draw"></a>gx_slider_tickmarks_draw

Desenhe marcas de carraças de slider

### <a name="prototype"></a>Prototype

```C
VOID gx_slider_tickmarks_draw(GX_SLIDER *slider);
```

### <a name="description"></a>Descrição

Este serviço desenha as marcas de carraças deslizantes. Esta função é chamada internamente pela função gx_slider_draw, mas é exposta para utilização por aplicações que podem implementar uma função de desenho de slider personalizado.

### <a name="parameters"></a>Parâmetros

- **slider**: Bloco de controlo de widget slider

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom slider draw function. */
VOID my_slider_draw(GX_SLIDER *slider)
{
    /* Add your own background draw here. */

    /* Call default tickmarks draw. */
    gx_slider_tickmarks_draw(slider);

    /* Call default slider needle draw. */
    gx_slider_needle_draw(slider);
}
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_travel_get"></a>gx_slider_travel_get

Obtenha viagens de slider

### <a name="prototype"></a>Prototype

```C
UINT gx_slider_travel_get(
    GX_SLIDER *widget,
    GX_SLIDER_INFO *info,
    INT *return_min_travel, 
    INT *return_max_travel);
```

### <a name="description"></a>Descrição

Este serviço faz com que o slider viaje.

### <a name="parameters"></a>Parâmetros

- **slider**: Bloco de controlo de widget slider
- **informação**: Ponteiro para slider estrutura de informação. **O apêndice I** contém definição para GX_SLIDER_INFO estrutura.
- **return_min_travel**: Ponter para destino para o valor mínimo da viagem</td>
- **return_max_travell**: Ponter para o destino para o valor máximo da viagem</td>

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Viagem de slider bem sucedida obter
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido
- **GX_INVALID_VALUE:**(0x22) Informações de slider não válidas

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Get travel information for for slider “my_slider”. */
status = gx_slider_travel_get(&my_slider, &info,
    &my_min_travel, &my_max_travel);

/* If status is GX_SUCCESS the travel max/min values for slider “my_slider” have been retrieved. */
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_value_calculate"></a>gx_slider_value_calculate

Calcular o valor do slider

### <a name="prototype"></a>Prototype

```C
UINT gx_slider_value_calculate(
    GX_SLIDER *slider, 
    GX_SLIDER_INFO *info,
    INT new_position);
```

### <a name="description"></a>Descrição

Este serviço calcula o valor do deslizador com base na posição da agulha deslizante. Esta função é chamada internamente pelo GUIX quando o utilizador move a agulha de slider, mas também pode ser invocada pela aplicação ao implementar um widget de slider personalizado.

### <a name="parameters"></a>Parâmetros

- **slider**: Bloco de controlo de widget slider
- **informações**: Ponteiro para informação de slider. **O apêndice I** contém definição para GX_LISDER_INFO estrutura.
- **new_position**: Nova posição de slider

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS:**(0x00) Calcular o valor do slider bem sucedido
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido
- **GX_INVALID_VALUE:**(0x22) Informações de slider não válidas

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Calculate new value for slider “my_slider”. */
status = gx_slider_value_calculate(&my_slider,
    &my_slider.gx_slider_info, new_slider_position);

/* If status is GX_SUCCESS the slider value of “my_slider” has been calculated. */

```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_set

## <a name="gx_slider_value_set"></a>gx_slider_value_set

Definir valor de slider

### <a name="prototype"></a>Prototype

```C
UINT gx_slider_value_set(
    GX_SLIDER *slider,
    GX_SLIDER_INFO *info, 
    INT new_value);
```

### <a name="description"></a>Descrição

Este serviço define o valor do slider. Esta API pode ser chamada pela aplicação para mover uma agulha de slider sob controlo do programa, ignorando a necessidade de entrada do utilizador para arrastar a agulha deslizante.

### <a name="parameters"></a>Parâmetros

- **slider**: Bloco de controlo de widget slider
- **informação**: Ponteiro para slider estrutura de informação. **Apêndice I** contém definição para GX_SLIDER_INFO estrutura
- **new_value**: Novo valor de slider

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Conjunto de valor de slider bem sucedido
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set new value for slider “my_slider”. */
status = gx_slider_value_set(&my_slider,
    &my_slider.gx_slider_info, new_value);

/* If status is GX_SUCCESS the new value has been set for slider “my_slider”. */
```

### <a name="see-also"></a>Consulte também

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate

##  <a name="gx_sprite_create"></a>gx_sprite_create

Criar um widget sprite

### <a name="prototype"></a>Prototype

```C
UINT gx_sprite_create(
    GX_SPRITE *sprite, GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_SPRITE_FRAME *frame_list,
    USHORT frame_count,
    ULONG style, USHORT sprite_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria um widget GX_SPRITE. Um sprite é usado para exibir uma sequência de pixelmaps como em uma animação, ou pode ser usado como um widget de exibição de pixelmap multi-estado.

GX_SPRITE é derivado de GX_WIDGET e suporta todos os gx_widget serviços da API.

O widget GX_SPRITE requer uma variedade de estruturas GX_SPRITE_FRAME para definir a animação sprite. **O apêndice I** contém definição para GX_PRITE_FRAME estrutura.

### <a name="parameters"></a>Parâmetros

- **sprite**: Bloco de controlo de widget sprite
- **nome**: Nome de sprite opcional
- **pai**: Ponteiro para widget dos pais
- **frame_list**: Uma variedade de estruturas GX_SPRITE_FRAME
- **frame_count**: especifica o número de entradas na matriz da lista de quadros
- **estilo**: Estilo de sprite. **O apêndice D** contém estilos gerais predefinidos para todos os widgets, bem como estilos específicos do widget.
- **sprite_id**: ID definido pela aplicação de sprite
- **tamanho**: Dimensões do sprite

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS:**(0x00) Criação de sprite bem sucedida
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_ALREADY_CREATED**: (0x13) Widget já criado
- **GX_INVALID_WIDGET**: (0x12) Widget parental não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Create sprite “my_sprite”. */

status = gx_sprite_create(&my_sprite, “my_sprite”,
    &my_parent,
    sprite_frame_list, frame_count,
    GX_STYLE_SPRITE_AUTO|GX_STYLE_SPRITE_LOOP,
    ID_MY_SPRITE, &size);

/* If status is GX_SUCCESS the sprite “my_sprite” has been created. */
```

### <a name="see-also"></a>Consulte também

- gx_sprite_start
- gx_sprite_stop
- gx_sprite_current_frame_set
- gx_sprite_frame_list_set

## <a name="gx_sprite_current_frame_set"></a>gx_sprite_current_frame_set

Atribuir quadro sprite

### <a name="prototype"></a>Prototype

```C
UINT gx_sprite_current_frame_set(
    GX_SPRITE *sprite, 
    USHORT frame);
```

### <a name="description"></a>Descrição

Este serviço atribui a estrutura de sprite atual. Se um widget GX_SPRITE não estiver a funcionar automaticamente, pode ser utilizado como uma luz de estado controlada por programa, exibindo o mapa pixelmap de quadro comandado.

### <a name="parameters"></a>Parâmetros

- **sprite**: Bloco de controlo de widget sprite
- **quadro**: Quadro sprite para exibir

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS:**(0x00) Bem sucedido
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Assign frame number 3 as the current sprite frame */
status = gx_sprite_current_frame_set(&my_sprite, 3);

/* If status is GX_SUCCESS the sprite “my_sprite” will display frame index 3. */
```

### <a name="see-also"></a>Consulte também

- gx_sprite_start
- gx_sprite_stop
- gx_sprite_create
- gx_sprite_frame_list_set

## <a name="gx_sprite_frame_list_set"></a>gx_sprite_frame_list_set

Atribuir ou alterar uma lista de quadros de sprite

### <a name="prototype"></a>Prototype

```C
UINT gx_sprite_frame_list_set(
    GX_SPRITE *sprite,
    GX_SPRITE_FRAME *frame_list,
    USHORT frame_count);
```

### <a name="description"></a>Descrição

Este serviço pode ser usado para atribuir ou reatribuir a lista de quadros utilizada por um widget sprite após a criação do widget sprite. Para obter informações sobre o conteúdo de uma lista de quadros de sprite, consulte a documentação gx_sprite_create API.

### <a name="parameters"></a>Parâmetros

- **sprite**: Bloco de controlo de widget sprite
- **frame_list**: Conjunto de estruturas de GX_SPRITE_FRAME ou GX_NULL se não houver lista de quadros.
- **frame_count**: Número de quadros na matriz da lista de quadros

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Conjunto de quadros de sprite bem sucedido
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Assign framelist_1, which has 10 frames, to my_sprite */
status = gx_sprite_frame_list_set(&my_sprite, framelist_1, 10);

/* If status is GX_SUCCESS the new frame list is now associated with this sprite */
```

### <a name="see-also"></a>Consulte também

- gx_sprite_current_frame_set
- gx_sprite_stop
- gx_sprite_create
- gx_sprite_create

## <a name="gx_sprite_start"></a>gx_sprite_start

Inicie uma sequência de corrida sprite

### <a name="prototype"></a>Prototype

```C
UINT gx_sprite_start(
    GX_SPRITE *sprite, 
    USHORT frame);
```

### <a name="description"></a>Descrição

Este serviço inicia uma sequência de funcionação automática. O widget sprite irá pedalar através dos quadros do sprite até que o último quadro seja atingido, ou funcionará continuamente se o estilo GX_SPRITE_LOOP estiver definido.

### <a name="parameters"></a>Parâmetros

- **sprite**: Bloco de controlo de widget sprite
- **quadro**: Quadro inicial de sprite para exibir, geralmente quadro 0

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Começou com sucesso a corrida de sprite
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Start the sprite “my_sprite” */
status = gx_sprite_start(&my_sprite, 0);

/* If status is GX_SUCCESS the sprite “my_sprite” will start running */
```

### <a name="see-also"></a>Consulte também

- gx_sprite_current_frame_set
- gx_sprite_stop
- gx_sprite_create
- gx_sprite_frame_list_set

## <a name="gx_sprite_stop"></a>gx_sprite_stop

Pare uma sequência de corrida sprite

### <a name="prototype"></a>Prototype

```C
UINT gx_sprite_stop(GX_SPRITE *sprite);
```

### <a name="description"></a>Descrição

Este serviço para uma sequência de funcionação automática.

### <a name="parameters"></a>Parâmetros

- **sprite**: Bloco de controlo de widget sprite

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Com sucesso parou a corrida de sprite
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Stop the sprite sequence */
status = gx_sprite_stop(&my_sprite);

/* If status is GX_SUCCESS the sprite “my_sprite” is stopped. */
```

### <a name="see-also"></a>Consulte também

- gx_sprite_current_frame_set
- gx_sprite_start
- gx_sprite_create
- gx_sprite_frame_list_set

## <a name="gx_string_scroll_wheel_create"></a>gx_string_scroll_wheel_create

Criar uma roda de pergaminho tipo de corda

### <a name="prototype"></a>Prototype

```C
UINT gx_string_scroll_wheel_create(
    GX_STRING_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent, 
    INT total_rows,
    GX_CONST GX_CHAR **string_list, 
    ULONG style,
    USHORT Id, 
    GX_CONST GX_RECTANGLE *size)
```

### <a name="description"></a>Descrição

Este serviço cria uma roda de deslocação tipo de corda.

GX_STRING_SCROLL_WHEEL é derivado de GX_TEXT_SCROLL_WHEEL, e, portanto, todas as funções gx_text_scroll_wheel API talvez sejam usadas com widgets GX_STRING_SCROLL_WHEEL.

A aplicação pode passar numa simples matriz de cordas para a função de criar que define as cordas que serão exibidas pela roda de deslocação, ou a aplicação pode passar GX_NULL como parâmetro string_list e chamar a `gx_string_scroll_wheel_string_id_list_set()` API para fornecer uma matriz de IDs de corda. Se este último método for utilizado, a roda de deslocação de cordas mudará automaticamente as cordas visualizadas se o idioma de aplicação ativo for modificado.

Como alternativa, se as cordas a exibir não estiverem estáticas definidas ou não souberem no momento em que a roda de deslocação é criada, a aplicação pode passar GX_NULL como parâmetro da lista de cordas, e chamar a função API gx_text_scroll_wheel_callback_set() para definir uma função de retorno que fornecerá as cordas a serem exibidas em tempo real como necessário..

### <a name="parameters"></a>Parâmetros

- **roda**: Endereço do bloco de controlo da roda de roda de roda de fio
- **nome**: Nome de widget definido por aplicação
- **pai**: Mãe da roda ou GX_NULL
- **total_rows**: Filas totais a apresentar ao utilizador
- **string_list**: Array de cordas estáticamente definido, ou GX_NULL
- **estilo**: Bandeiras de estilo desejadas
- **Id**: Aplicação definida bandeiras de estilo roda
- **tamanho**: Tamanho inicial da roda de deslocação

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Roda de pergaminho de corda criada com sucesso
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR (0x07)**: Ponteiro inválido
- **GX_ALREADY_CREATED**: (0x13) Widget já criado
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_CONST GX_CHAR *days[] = {
    “Sunday”,
    “Monday”,
    “Tuesday”,
    “Wednesday”,
    “Thursday”,
    “Friday”,
    “Saturday”
};

GX_STRING_SCROLL_WHEEL wheel;

/* Create the string scroll wheel. */

status = gx_string_scroll_wheel_create(&wheel, “Day Wheel”,
    root, 7, days,
    GX_STYLE_ENABLED|GX_STYLE_TEXT_CENTER|GX_STYLE_TRANSPARENT|
    GX_STYLE_WRAP|GX_STYLE_TEXT_SCROLL_WHEEL_ROUND,
    ID_SCROLL_WHEEL_DAY, &size);

/* If status is GX_SUCCESS the string scroll wheel has been created. */
```

### <a name="see-also"></a>Consulte também

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_string_id_list_set
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_string_scroll_wheel_event_process"></a>gx_string_scroll_wheel_event_process


Evento de roda de roda de cadeia de processo

### <a name="prototype"></a>Prototype

```C
UINT gx_string_scroll_wheel_string_id_list_set(
    GX_STRING_SCROLL_WHEEL *wheel,
    GX_CONST GX_RESOURCE_ID *string_id_list, 
    INT id_count);
```

### <a name="description"></a>Descrição

Este serviço processa um evento para a roda de deslocação de cordas especificada. Este serviço deve ser chamado como o manipulador de eventos predefinido por quaisquer funções de processamento de eventos de roda de roda de roda de fio personalizadas.

### <a name="parameters"></a>Parâmetros

- **roda** Ponteiro para bloco de controlo da roda de roda de roda de roda de cadeia
- **event_ptr** Ponteiro para o evento para processar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Processo de evento de roda de roda de roda de roda de corda bem sucedida
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Call generic string scroll wheel event processing as part of custom event processing function. */

UINT custom_string_scroll_wheel_event_process(GX_STRING_SCROLL_WHEEL *wheel, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default string scroll wheel event processing */
        status = gx_string_scroll_wheel_event_process(wheel, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Consulte também

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_string_id_list_set
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_string_scroll_wheel_string_id_list_set"></a>gx_string_scroll_wheel_string_id_list_set

Atribuir matriz de IDs de corda

### <a name="prototype"></a>Prototype

```C
UINT gx_string_scroll_wheel_string_id_list_set(
    GX_STRING_SCROLL_WHEEL *wheel,
    GX_CONST GX_RESOURCE_ID *string_id_list, INT id_count);
```

### <a name="description"></a>Descrição

Este serviço atribui uma variedade de IDs de corda a um widget de roda de roda de roda de fio. Este método de atribuição de cordas a uma roda de deslocamento de cordas é recomendado se as cordas estiverem estáticas definidas e o widget funcionar em várias línguas. Se esta API for utilizada, o widget da roda de deslocação deve ser criado primeiro com uma lista de cordas GX_NULL.

### <a name="parameters"></a>Parâmetros

- **roda**: Endereço do bloco de controlo da roda de roda de roda de fio
- **string_id_list**: Matriz de IDs de cordas
- **id_count:** Tamanho da lista de identificação.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) definir com sucesso a matriz de ID de corda
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido
- **GX_INVALID_VALUE**: 0x22) Tamanho da lista de ID inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_CONST RESOURCE_ID wheel_ids[] = {
    GX_STRING_ID_SUNDAY,
    GX_STRING_ID_MONDAY,
    GX_STRING_ID_TUESDAY,
    GX_STRING_ID_WEDNESDAY,
    GX_STRING_ID_THURSDAY,
    GX_STRING_ID_FRIDAY,
    GX_STRING_ID_SATURDAY
};

GX_STRING_SCROLL_WHEEL wheel;

/* Stop the sprite sequence */

status = gx_string_scroll_wheel_string_id_list_set(&wheel, wheel_ids, 7);

/* If status is GX_SUCCESS the ID list has been assigned. */
```

### <a name="see-also"></a>Consulte também

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_string_scroll_wheel_string_list_set"></a>gx_string_scroll_wheel_string_list_set

Atribuir matriz de cordas

### <a name="prototype"></a>Prototype

```C
UINT gx_string_scroll_wheel_string_list_set(
    GX_STRING_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *string_list, 
    INT string_count);
```

### <a name="description"></a>Descrição

Isto atribui uma variedade de cordas a um widget de roda de roda de roda de roda de fio. Isto pode ser usado para modificar as cordas apresentadas após a criação do widget inicialmente.

Note que string_scroll_wheel não suporta GX_STYLE_TEXT_COPY, pelo que a matriz de cordas passadas nesta função deve ser definida estáticamente pela aplicação.

### <a name="parameters"></a>Parâmetros

- **roda**: Endereço do bloco de controlo da roda de roda de roda de fio
- **string_list**: Conjunto de ponteiros de cordas
- **string_count:** Tamanho da matriz de cordas.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Mudou com sucesso as cordas para roda de deslocação
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido
- **GX_INVALID_VALUE**: (0x22) Tamanho da lista de cordas inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_CONST GX_CHAR *days[] = {
    “Sunday”,
    “Monday”,
    “Tuesday”,
    “Wednesday”,
    “Thursday”,
    “Friday”,
    “Saturday”
};

GX_STRING_SCROLL_WHEEL wheel;

/* Set the array of strings to the scroll wheel. */

status = gx_string_scroll_wheel_string_list_set(&wheel, days, 7);

/* If status is GX_SUCCESS the string array has been assigned. */
```

### <a name="see-also"></a>Consulte também

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_studio_widget_create"></a>gx_studio_widget_create

Criar widget definido no arquivo de especificações gerados pelo Studio

### <a name="prototype"></a>Prototype

```C
GX_WIDGET *gx_studio_widget_create(
    GX_BYTE *control,
    GX_CONST GX_STUDIO_WIDGET *definition, 
    GX_WIDGET *parent);
```

### <a name="description"></a>Descrição

Este serviço cria um widget e os filhos do widget usando uma especificação widget definida dentro do ficheiro de especificações geradas pelo ESTÚDIO GUIX. Esta função evita o aspeto "por nome" da função semelhante `gx_studio_named_widget_create()` .

A estrutura GX_STUDIO_WIDGET é definida no ficheiro cabeçalho de especificações de aplicação gerado pelo GUIX Studio.

Para widgets atribuídos estáticamente, o bloco de controlo widget é definido nas especificações geradas.c ficheiro, e dado o nome widget definido dentro do GUIX Studio. Para widgets dinamicamente atribuídos, a aplicação deve passar GX_NULL como o endereço do bloco de controlo widget e a função tentará alocar dinamicamente o bloco de controlo widget utilizando a `gx_system_memory_allocate()` função, que também é definida e fornecida pela aplicação.

Para uma aplicação para referenciar diretamente a definição widget do GUIX Studio dentro do ficheiro de especificações geradas, é necessário seguir a convenção de nomeação utilizada pelo gerador de código GUI Studio. A estrutura GX_STUDIO_WIDGET gerada dentro das especificações.c ficheiro é sempre nomeado de acordo com esta convenção: <widget_name>_define, onde o campo <widget_name> pode ser repetido várias vezes se o widget for filho de um widget infantil.

### <a name="parameters"></a>Parâmetros

- **controlo** Ponteiro para o bloco de controlo do widget, ou GX_NULL se for atribuído de forma dinâmica.
- **definição** Estrutura de definição de widget gerada por estúdio
- **ponteiro dos pais** para o progenitor widget, se houver

### <a name="return-values"></a>Valores de devolução

O ponteiro para o bloco de controlo widget criado, ou GX_NULL se a criação não foi bem sucedida.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Create the widget “playlist_screen”, which is statically allocated. */

widget = gx_studio_widget_create(&playlist_screen,
    &playlist_screen_define,
    root_window);

/* If widget != GX_NULL the widget was created. */

/* create the widget “songs_screen”, which is dynamically allocated */

widget = gx_studio_widget_create(GX_NULL,
    &songs_screen_define, root_window);
```

### <a name="see-also"></a>Consulte também

- gx_studio_named_widget_create

## <a name="gx_studio_named_widget_create"></a>gx_studio_named_widget_create

Criar widget definido no arquivo de especificações gerados pelo Studio

### <a name="prototype"></a>Prototype

```C
UINT *gx_studio_named_widget_create(
    char *name, 
    GX_WIDGET *parent,
    GX_WIDGET **new_widget);
```

### <a name="description"></a>Descrição

Este serviço cria um widget e os filhos do widget usando uma especificação widget definida dentro do ficheiro de especificações geradas pelo ESTÚDIO GUIX.

Esta função API é utilizada para criar ecrãs de alto nível utilizando o nome do ecrã especificado na aplicação GUIX Studio como identificador de definição de widget.

### <a name="parameters"></a>Parâmetros

- **nome**: Nome do ecrã definido na aplicação GUIX Studio.
- **pai**: ponteiro para o progenitor widget, se houver
- **new_widget:** localização para devolver o ponteiro widget criado

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS:**(0x00) Bem sucedido
- **GX_FAILURE**: (0x11) Widget nomeado não foi encontrado

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Create the widget named “child_popup”,
   which is a child of the top-level screen “main_screen”. */

GX_WIDGET *menu_screen;

status = gx_studio_named_widget_create(“main_menu”,
    &root_window, &menu_screen);

/* If status == GX_SUCCESS the screen was created
   and linked to the root window. */
```

### <a name="see-also"></a>Consulte também

- gx_studio_widget_create

## <a name="gx_studio_display_configure"></a>gx_studio_display_configure

Configure exposição definida no projeto GUIX Studio

### <a name="prototype"></a>Prototype

```C
UINT *gx_studio_display_configure(
    USHORT display,
    UINT (*driver)(GX_DISPLAY *),
    USHORT language, 
    USHORT theme,
    GX_WINDOW_ROOT **return_root);
```

### <a name="description"></a>Descrição

Este serviço inicializa uma GX_DISPLAY para que esteja pronto a ser utilizado. Esta função consolida as funções para inicializar um bloco de controlo GX_DISPLAY, criar uma tela para encaixar no visor e criar uma janela de raiz para a tela. Esta função também instala o tema do idioma e recurso solicitado após a inicial do visor.

Esta função consolida o esforço de programação mais necessário para preparar um visor para utilização. A função invoca as funções gx_display_create(), gx_display_color_table_set, gx_display_font_table_set, gx_display_pixelmap_table_set, gx_system_language_table_set, gx_system_ative_language_set, gx_system_scroll_appearance_set, gx_canvas_create e gx_window_root_create funções, todas ou algumas das quais seriam exigidas pelo programa de candidatura.

### <a name="parameters"></a>Parâmetros

- **display**: Índice na tabela de exibição, que corresponde às definições de visualização no ficheiro do projeto Studio.
- **controlador**: ponteiro para visualizar a função de inicialização do controlador. Esta função é invocada para inicializar os ponteiros de função indireta do bloco de controlo GX_DISPLAY, bem como executar qualquer configuração de hardware necessária.
- **linguagem**: índice de tabela de linguagem inicial
- **linguagem**: índice temático inicial
- **raiz**: ponteiro para variável em que devolver o endereço da janela raiz, ou GX_NULL.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS:**(0x00) Bem sucedido
- **GX_FAILURE**: (0x11) O ecrã não pôde ser inicializado

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Create the widget named “child_popup”, which is a child of the
   top-level screen “main_screen”. */

GX_WIDGET *menu_screen;

status = gx_studio_display_configure(MAIN_DISPLAY,
    my_driver_setup, LANGUAGE_ENGLISH, DEFAULT_THEME, GX_NULL);

/* If status == GX_SUCCESS the display was initialized, a canvas was
created for the display, a root window was created for the canvas, and
the requested language and theme have been installed.
*/
```

### <a name="see-also"></a>Consulte também

- gx_display_create
- gx_display_color_table_set
- gx_display_font_table_set
- gx_display_pixelmap_table_set
- gx_system_language_table_set
- gx_system_active_language_set
- gx_system_scroll_appearance_set
- gx_canvas_create
- gx_window_root_create

## <a name="gx_system_active_language_set"></a>gx_system_active_language_set

Definir linguagem ativa

### <a name="prototype"></a>Prototype

```C
UINT gx_system_active_language_set(GX_UBYTE language);
```

### <a name="description"></a>Descrição

Este serviço define o idioma atual. O índice linguístico deve ser inferior ao número de colunas na tabela de cordas de aplicação. Esta função foi depreciada a favor de gx_display_ative_language_set. Todas as novas aplicações devem ser utilizadas gx_display_ative_langauge_set.

### <a name="parameters"></a>Parâmetros

- **linguagem**: Índice de linguagem, definido no ficheiro cabeçalho de recursos.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Definir com sucesso a linguagem ativa
- **GX_CALLER_ERROR:**** (0x11) Inválido desta função
- **GX_PTR_ERROR:**** (0x07) Ponteiro inválido
- **GX_INVALID_VALUE:**** (0x22) Índice linguístico inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set active language and mark widget canvas as dirty. */
status = gx_system_active_language_set(ID_LANGUAGE_ENGLISH);

/* If status is GX_SUCCESS the active language has been assigned. */
```

### <a name="see-also"></a>Consulte também

- gx_display_language_table_set
- gx_display_active_langauge_set
- gx_display_string_get

## <a name="gx_system_animation_get"></a>gx_system_animation_get

Obtenha o bloco de controlo de animação a partir da piscina do sistema

### <a name="prototype"></a>Prototype

```C
UINT gx_system_animation_get(GX_ANIMATION **animation);
```

### <a name="description"></a>Descrição

Este serviço pode ser utilizado para obter um bloco de controlo de animação a partir de um conjunto de tais blocos de controlo mantidos pelo componente gx_system. O conjunto de blocos de controlo de animação e os serviços API relacionados só são fornecidos se o GX_ANIMATION_POOL_SIZE constante for definido com um valor 0. A definição padrão para este valor é 6, o que significa que o conjunto de blocos de controlo de animação do sistema contém tamanho GX_ANIMATION bloco de controlo.

Um bloco de controlo de animação atribuído usando esta API é automaticamente devolvido à piscina gratuita se a animação correr até ao fim. Se a animação for interrompida usando gx_animation_stop, ou não for iniciada devido a algum erro devolvido, o bloco de controlo de animação deve ser devolvido à piscina gratuita pela aplicação utilizando gx_system_animation_free.

### <a name="parameters"></a>Parâmetros

- **animação**: Endereço do ponteiro para receber GX_ANIMATION ponteiro.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Bloco de controlo de animação obtido com sucesso
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR**: (0x07) Ponteiro de animação inválido
- **GX_OUT_OF_ANIMATIONS**: (0x31) Piscina de animação do sistema esgotada

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_ANIMATION *animation;

UINT status = gx_system_animation_get(&animation);

if (status == GX_SUCCESS)
{
    gx_animation_start(animation, animation_info);
}
```

### <a name="see-also"></a>Consulte também

- gx_animation_create
- gx_animation_start
- gx_animation_stop
- gx_system_animation_free

## <a name="gx_system_animation_free"></a>gx_system_animation_free

Devolva um bloco de controlo de animação à piscina do sistema

### <a name="prototype"></a>Prototype

```C
UINT gx_system_animation_free(GX_ANIMATION *animation);
```

### <a name="description"></a>Descrição

Este serviço pode ser utilizado para devolver um bloco de controlo de animação à piscina do sistema. O conjunto de blocos de controlo de animação e os serviços API relacionados só são fornecidos se o GX_ANIMATION_POOL_SIZE constante for definido com um valor 0. A definição padrão para este valor é 6, o que significa que o conjunto de blocos de controlo de animação do sistema contém tamanho GX_ANIMATION bloco de controlo.

Um bloco de controlo de animação atribuído com gx_system_animation_get() é automaticamente devolvido à piscina gratuita se a animação correr até ao fim. Tentar devolver um bloco de controlo de animação à piscina gratuita que já foi devolvida à piscina gratuita não tem efeito.

Se a animação for interrompida com gx_animation_stop, ou não for iniciada devido a algum erro devolvido, o bloco de controlo de animação obtido com gx_system_animation_get() deve ser devolvido à piscina gratuita pela aplicação utilizando gx_system_animation_free).

Uma animação deve estar no estado de IDLE antes de poder ser devolvida à piscina gratuita. Uma animação está no estado de OCIO quando não foi iniciada, quando é interrompida, ou quando termina.

### <a name="parameters"></a>Parâmetros

- **animação**: Ponteiro para o GX_ANIMATION bloco de controlo.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) bloco de animação lançado com sucesso
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR**: (0x07) Ponteiro de animação inválido
- **GX_INVALID_ANIMATION:**(0x32) A animação não é OCD, ou não foi atribuída a partir do pool do sistema

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_ANIMATION *animation;

UINT status = gx_system_animation_get(&animation);

if (status == GX_SUCCESS)
{
    status = gx_animation_start(animation, animation_info);

    if (status != GX_SUCCESS)
    {
        /* animation did not start, return it to the free pool */
        gx_system_animation_free(animation);
    }
}
```

### <a name="see-also"></a>Consulte também

- gx_animation_create
- gx_animation_start
- gx_animation_stop
- gx_system_animation_get

## <a name="gx_system_bidi_text_disable"></a>gx_system_bidi_text_disable

Desativar suporte de texto bidirecional dinâmico

### <a name="prototype"></a>Prototype

```C
UINT gx_system_bidi_text_disable(VOID);
```

### <a name="description"></a>Descrição

Este serviço desativa suporte dinâmico de texto bidirecional. Este serviço requer GX_DYNAMIC_BIDI_TEXT_SUPPORT a ser definido na construção da biblioteca GUIX, e só é necessário se for necessário reordenar os dados de cadeias BiDi. A maioria das aplicações utiliza o GUIX Studio para produzir cordas de texto BiDi reordenada corretamente.

### <a name="parameters"></a>Parâmetros

**Nenhuma**

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Suporte de texto bidi com sucesso

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* GX_DYNAMIC_BIDI_TEXT_SUPPORT is defined. */

/* Diable bidi text support. */
status = gx_system_bidi_text_disable();

/* If status is GX_SUCCESS, bidi text support was disabled. */
```

### <a name="see-also"></a>Consulte também

- gx_system_bidi_text_enable

## <a name="gx_system_bidi_text_enable"></a>gx_system_bidi_text_enable

Ativar suporte dinâmico de texto bidi

### <a name="prototype"></a>Prototype

```C
UINT gx_system_bidi_text_enable(VOID);
```

### <a name="description"></a>Descrição

Este serviço permite suporte dinâmico de texto bidis. Este serviço requer GX_DYNAMIC_BIDI_TEXT_SUPPORT a ser definido na construção da biblioteca GUIX, e só é necessário se for necessário reordenar os dados de cadeias BiDi. A maioria das aplicações utiliza o GUIX Studio para produzir cordas de texto BiDi corretamente reordenadas.

### <a name="parameters"></a>Parâmetros

**Nenhuma**

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Suporte de texto bidi com sucesso

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* GX_DYNAMIC_BIDI_TEXT_SUPPORT is defined. */

/* Enable bidi text support. */
status = gx_system_bidi_text_enable();

/* If status is GX_SUCCESS, bidi text support was enabled. */
```

### <a name="see-also"></a>Consulte também

- gx_system_bidi_text_disable

## <a name="gx_system_canvas_refresh"></a>gx_system_canvas_refresh

Refresque todas as telas sujas

### <a name="prototype"></a>Prototype

```C
UINT gx_system_canvas_refresh(VOID);
```

### <a name="description"></a>Descrição

Este serviço força uma redeensar imediata de todos os widgets sujos e telas. Este serviço é normalmente invocado internamente pelo componente do sistema GUIX, mas pode ser chamado pela aplicação para forçar uma operação de redesenhar o sistema imediato.

### <a name="parameters"></a>Parâmetros

**Nenhuma**

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Bloco de animação lançado com sucesso
- **GX_INVALID_CANVAS**: (0x20) Nenhuma tela criada
- **GX_CALLER_ERROR:**(0x11) Inválido desta função

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Force immediate redraw operation. */
status = gx_system_canvas_refresh();

/* If status is GX_SUCCESS, canvas has been redraw. */
```

### <a name="see-also"></a>Consulte também

- gx_system_active_language_set
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_dirty_mark"></a>gx_system_dirty_mark

Área de marca suja

### <a name="prototype"></a>Prototype

```C
UINT gx_system_dirty_mark(GX_WIDGET *widget);
```

### <a name="description"></a>Descrição

Este serviço marca a área deste widget como sujo. Isto faz fila efetivamente com o widget para redesenhar quando o processamento do evento do sistema estiver concluído.

### <a name="parameters"></a>Parâmetros

- **widget**: Ponteiro para o bloco de controlo widget

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Widget com sucesso marcado sujo
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Mark widget “my_widget” as dirty. */
status = gx_system_dirty_mark(&my_widget);

/* If status is GX_SUCCESS the area associated
   with “my_widget” has been marked as dirty. */
```

### <a name="see-also"></a>Consulte também

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_dirty_partial_add"></a>gx_system_dirty_partial_add

Marque área parcial suja

### <a name="prototype"></a>Prototype

```C
UINT gx_system_dirty_partial_add(
    GX_WIDGET *widget,
    GX_RECTANGLE *dirty_area);
```

### <a name="description"></a>Descrição

Este serviço marca a área parcial deste widget como sujo. Isto faz fila com o widget para redesenhar a operação de atualização de lona GUIX quando o processamento do evento do sistema estiver concluído.

### <a name="parameters"></a>Parâmetros

- **widget**: Ponteiro para o bloco de controlo widget
- **dirty_area**: Área suja de widget para marcar sujo

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Marca de área parcial suja parcial bem sucedida
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido
- **GX_INVALID_SIZE:**(0x19) Tamanho inválido de área suja

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Mark widget “my_widget” partial area as dirty. */

status = gx_system_dirty_partial_add(&my_widget,
    &partial_area);

/* If status is GX_SUCCESS the partial area “partial_area”
associated with “my_widget” has been marked as dirty. */
```

### <a name="see-also"></a>Consulte também

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_draw_context_get"></a>gx_system_draw_context_get

Obtenha contexto de desenho

### <a name="prototype"></a>Prototype

```C
UINT gx_system_draw_context_get(GX_DRAW_CONTEXT **current_context);
```

### <a name="description"></a>Descrição

Este serviço devolve um ponteiro ao contexto de desenho atual.

### <a name="parameters"></a>Parâmetros

- **current_context**: Ponteiro para destino para ponteiro de contexto de desenho atual

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) O contexto atual bem sucedido obtém
- **GX_PTR_ERROR**:0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_DRAW_CONTEXT *current_context;

/* Get current drawing context. */

status = gx_system_draw_context_get(&current_context);

/* If status is GX_SUCCESS the current drawing context
   is contained in “current_context”. */
```

### <a name="see-also"></a>Consulte também

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_event_fold"></a>gx_system_event_fold

Enviar evento

### <a name="prototype"></a>Prototype

```C
UINT gx_system_event_fold(GX_EVENT *event);
```

### <a name="description"></a>Descrição

Este serviço procura a fila do evento GUIX para um evento do mesmo tipo. Se existir um evento do mesmo tipo, a carga útil do evento é atualizada para corresponder ao novo evento. Se não for encontrado nenhum evento correspondente, a função gx_system_event_send é chamada para adicionar o novo evento ao final da fila do evento.

Esta função é comumente utilizada por controladores de entrada de toque rápido para evitar que preencha a fila do evento com vários eventos PEN_DRAG. Esta função também pode ser chamada pela aplicação para evitar que vários eventos do mesmo tipo sejam adicionados à fila do evento GUIX.

### <a name="parameters"></a>Parâmetros

- **evento**: Ponteiro para o evento

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS:**(0x00) Envio de eventos de sucesso
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_EVENT my_event;

memset(&my_event, 0, sizeof(GX_EVENT));

my_event.gx_event_type = GX_EVENT_PEN_DOWN;

my_event.gx_event_payload.gx_event_pointdata.gx_point_x = 100;
my_event.gx_event_payload.gx_event_pointdata.gx_point_y = 200;

/* Send “my_event” for processing. */
status = gx_system_event_fold(&my_event);

/* If status is GX_SUCCESS the event has been sent for processing. */
```

### <a name="see-also"></a>Consulte também

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_event_send"></a>gx_system_event_send

Enviar evento

### <a name="prototype"></a>Prototype

```C
UINT gx_system_event_send(GX_EVENT *event);
```

### <a name="description"></a>Descrição

Este serviço envia o evento especificado para a fila de eventos do sistema GUIX. O novo evento é colocado no final da fila.

### <a name="parameters"></a>Parâmetros

- **evento**: Ponteiro para o evento

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS:**(0x00) Envio de eventos de sucesso
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Send “new_event” for processing. */

GX_EVENT new_event;

new_event.gx_event_target = widget ->gx_widget_parent;
new_event.gx_event_type = MY_EVENT_TYPE;

/* Set optional param. */
new_event.gx_event_payload.xxxx = yyyy
new_event.gx_event_sender = widget->gx_widget_id;

/* Push the event to event pool. */
status = gx_system_event_send(&new_event);

/* If status is GX_SUCCESS the event has been sent for processing. */
```

### <a name="see-also"></a>Consulte também

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_focus_claim"></a>gx_system_focus_claim

Foco de reclamação

### <a name="prototype"></a>Prototype

```C
UINT gx_system_focus_claim(GX_WIDGET *widget);
```

### <a name="description"></a>Descrição

Este serviço reivindica o foco para o widget especificado. Se o widget não tiver tido foco anteriormente, receberá um evento GX_EVENT_FOCUS_GAINED.

### <a name="parameters"></a>Parâmetros

- **widget**: Ponteiro para widget control block para reivindicar foco

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Reivindicação de foco bem sucedido
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_NO_CHANGE**: (0x08) Widget já detém o foco
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_INVALID_WIDGET:**(0x12 Widget não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Claim focus for widget “my_widget”. */
status = gx_system_claim_focus(&my_widget);

/* If status is GX_SUCCESS the focus has been claimed for
   “my_widget”. */
```

### <a name="see-also"></a>Consulte também

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_initialize"></a>gx_system_initialize

Inicializar GUIX

### <a name="prototype"></a>Prototype

```C
UINT gx_system_initialize(VOID);
```

### <a name="description"></a>Descrição

Este serviço inicializa o GUIX. Este serviço deve ser invocado antes de qualquer outro serviço API GUIX, e só deve ser invocado uma vez no arranque do sistema.

### <a name="parameters"></a>Parâmetros

- **Nenhuma**

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Inicialização do sistema de sucesso
- **GX_SYSTEM_ERROR**: (0xFE) O tamanho do bloco de controlo GX_EVENT inválido ou a fila de eventos/mutex/thread criaram falhas.
- **GX_CALLER_ERROR:**(0x11) Inválido desta função

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Initialize GUIX. */
status = gx_system_initialize();

/* If status is GX_SUCCESS, GUIX has been initialized. */
```

### <a name="see-also"></a>Consulte também

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_language_table_get"></a>gx_system_language_table_get

Recuperar tabela de linguagem ativa

### <a name="prototype"></a>Prototype

```C
UINT gx_system_language_table_get( 
    GX_CHAR ****language_table,
    GX_UBYTE *languages_count, 
    UINT *string_count);
```

### <a name="description"></a>Descrição

Este serviço recupera a tabela de linguagem ativa. Esta função é depreciada a favor de gx_display_language_table_get. Todas as novas aplicações devem ser utilizadas gx_display_language_table_get.

### <a name="parameters"></a>Parâmetros

- **language_table**: Endereço do ponteiro para a mesa de devolução da língua.
- **languages_count**: Endereço de variável para devolver colunas de tabela.
- **string_count**: Endereço do ponteiro para retornar as filas de tabelas.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) recuperou com sucesso a tabela de linguagem ativa
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_CHAR ***language_table;

GX_UBYTE language_count;

UINT string_count;

/* Retrieve the language table */

status = gx_system_language_table_get(&language_table,
    &language_count, &string_count);
```

### <a name="see-also"></a>Consulte também

- gx_display_language_table_get
- gx_display_language_table_set

## <a name="gx_system_language_table_set"></a>gx_system_language_table_set

Atribuir tabela de linguagem ativa

### <a name="prototype"></a>Prototype

```C
UINT gx_system_language_table_set(
    GX_CHAR ***language_table,
    GX_UBYTE languages_count, 
    UINT string_count);
```

### <a name="description"></a>Descrição

Este serviço instala a tabela de linguagem ativa. Esta função foi depreciada a favor de gx_display_language_table_set. Todas as novas aplicações devem ser utilizadas gx_display_language_table_set.

### <a name="parameters"></a>Parâmetros

- **language_table**: Ponteiro para a mesa de idiomas.
- **languages_count**: Número de línguas em tabela.
- **string_count**: Número de filas de mesa de cordas.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Definir com sucesso a tabela linguística
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Retrieve the language table */

status = gx_system_language_table_set(language_table,
    language_count, string_count);
```

### <a name="see-also"></a>Consulte também

- gx_display_language_table_set
- gx_display_language_table_get
- gx_display_active_language_set

## <a name="gx_system_memory_allocator_set"></a>gx_system_memory_allocator_set

Atribuir funções para alocação de memória, desalocação

### <a name="prototype"></a>Prototype

```C
UINT gx_system_memory_allocator_set(VOID *(allocate)(ULONG size),
    VOID(*release)(VOID *));
```

### <a name="description"></a>Descrição

Este serviço atribui a função de retorno fornecido à aplicação para alocação dinâmica de memória e desalocação.

Se não for necessário um serviço GUIX que utilize uma alocação dinâmica de memória, este serviço não precisa de ser chamado.

Se utilizado, este serviço deve ser chamado após gx_system_initialize() que limpa os ponteiros de serviço GUIX, e antes de qualquer serviço GUIX que exija a utilização de uma alocação dinâmica de memória.

Os serviços GUIX que requerem uma atribuição de memória em tempo de execução e um serviço de desatribuição incluem:

- Carregamento de recursos binários do armazenamento externo para o ambiente de tempo de execução GUIX.
- O software executar o descodificador de imagem JPEG.
- O descodificador de imagem de png de execução de software.
- Utilizar widgets de texto com GX_STYLE_TEXT_COPY.
- Funcionamento pixemap redimensionar e rotação funções de utilidade.
- Tela de execução e alocação de bloco de controlo widget.

### <a name="parameters"></a>Parâmetros

- **alocador**: Função de alocador de memória
- **lançamento**: Função sem memória

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS:**(0x00) Função de atribuição de memória com sucesso
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

O exemplo a seguir utiliza um pool de byte ThreadX para implementar um serviço de alocação de memória dinâmica threadsafe e de desatribuição de memória.

```C
TX_BYTE_POOL memory_pool;

#define SCRATCHPAD_SIZE (1024 * 4)

ULONG scratchpad[SCRATCHPAD_SIZE];

/* define memory allocation service */

VOID *memory_allocate(ULONG size)
{
    VOID *memptr;

    if (tx_byte_allocate(&memory_pool, &memptr, size, TX_NO_WAIT) == TX_SUCCESS)
    {
        return memptr;
    }
    return NULL;
}

/* define memory de-allocation service */
void memory_free(VOID *mem)
{
    tx_byte_release(mem);
}

/* create byte pool and install our dynamic memory services with GUIX
*/

VOID tx_application_define(void *first_unused_memory)
{
    /* create byte pool for GUIX to use */
    tx_byte_pool_create(&memory_pool, "scratchpad", scratchpad,
        SCRATCHPAD_SIZE * sizeof(ULONG));

    guix_setup();

    /* install our memory allocator and de-allocator */
    gx_system_memory_allocator_set(memory_allocate, memory_free);
}
```

### <a name="see-also"></a>Consulte também

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_pen_configure"></a>gx_system_pen_configure

Configuração da caneta definida

### <a name="prototype"></a>Prototype

```C
UINT gx_system_pen_configure(GX_PEN_CONFIGURATION *pen_configuration);
```

### <a name="description"></a>Descrição

Este serviço define a configuração da caneta para controlar os parâmetros de velocidade e distância da caneta utilizados para desencadear a geração de GX_EVENT_FLICK tipos de eventos.

O gx_pen_configuration_min_drag_dist membro da GX_PEN_CONFIGURATION é um tipo de dados de ponto fixo, e deve usar GX_FIXED_VAL_MAKE(valor) para converter de INT para GX_FIXED_VAL. Por exemplo, se pretender definir a distância mínima de arrasto para 0,5 pixels por carrapato, tem de definir o gx_pen_configuration_min_drag_dist para `GX_FIXED_VAL_MAKE(1) / 2` .

Nos lançamentos GUIX 5.4.0 ou mais, o membro gx_pen_configuration_min_drag_dist do GX_PEN_CONFIGURATION era do tipo (INT << 8) em vez de GX_FIXED_VAL tipo. Se o seu projeto com a versão 5.4.0 da biblioteca GUIX estiver a utilizar esta API, terá de modificar o parâmetro min_drag_dist ou #define GUIX_5_4_0_COMPATIBILITY ao construir a biblioteca GUIX.

### <a name="parameters"></a>Parâmetros

- **pen_configuration** Ponteiro para a estrutura de configuração da caneta. **Apêndice I** contém definição para GX_PEN_CONFIGURATION estrutura

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Configuração da caneta com sucesso
- **GX_CALLER_ERROR:**(0x11) Inválido desta função

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Define pen configuration, set minimum drag distance to 0.5 pixel
per tick, maximum pen speed to 10 ticks. That means GUIX will trigger
a vertical or horizontal flick event if the drag time is smaller than
10 ticks and the drag distance is bigger than 0.5 * drag_ticks. */

GX_PEN_CONFIGURATION pen_configuration;

#if defined(GUIX_5_4_0_COMPATIBILITY)
Pen_configuration.gx_pen_configuration_min_drag_dist = (1 << 8)/ 2;
#else
pen_configuration.gx_pen_configuration_min_drag_dist = GX_FIXED_VAL_MAKE(1) / 2;
#endif

pen_configuration.gx_pen_configuration_max_pen_speed_ticks = 10;

/* Set the pen configuration. */
status = gx_system_pen_configure(&pen_configuration);

/* If status is GX_SUCCESS the touch configure has been set. */
```

## <a name="gx_system_screen_stack_create"></a>gx_system_screen_stack_create

Criar e inicializar a pilha de ecrã do sistema

### <a name="prototype"></a>Prototype

```C
UINT gx_system_screen_stack_create(
    GX_WIDGET **memory, 
    INT size);
```

### <a name="description"></a>Descrição

Este serviço define um conjunto de memórias para ser usado para a pilha de ecrã do sistema. A pilha de ecrã do sistema é uma funcionalidade opcional que pode ser usada pela aplicação para gerir a aparência do fluxo de ecrã de aplicação.

Se a aplicação pretender utilizar os serviços de pilha de ecrã, a função gx_system_screen_stack_create deve ser chamada primeiro para configurar a região de memória da pilha de ecrã.

### <a name="parameters"></a>Parâmetros

- **memória**: Ponteiro para o bloco de memória reservado.
- **tamanho,** em bytes, do bloco de memória reservado.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Criação com sucesso
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
#define SCREEN_STACK_DEPTH 8
GX_WIDGET *screen_stack[SCREEN_STACK_DEPTH * 2];

UINT status;

/* Get the scrollbar appearance. */

status = gx_system_screen_stack_create(screen_stack,
    sizeof(GX_WIDGET *) * SCREEN_STACK_DEPTH * 2);

/* If status is GX_SUCCESS the system screen stack is initialized
and ready for use. */
```

### <a name="see-also"></a>Consulte também

- gx_system_screen_stack_get
- gx_system_screen_stack_pop
- gx_system_screen_stack_push
- gx_system_screen_stack_reset

## <a name="gx_system_screen_stack_get"></a>gx_system_screen_stack_get

Coloque os ponteiros mais altos da pilha de ecrã

### <a name="prototype"></a>Prototype

```C
UINT gx_system_screen_stack_get(
    GX_WIDGET **popped_parent,
    GX_WIDGET **popped_screen);
```

### <a name="description"></a>Descrição

Esta função coloca os ponteiros mais altos da pilha de ecrã e devolve esses ponteiros ao ouvinte. Esta função difere de gx_system_screen_stack_pop na medida em que o ecrã estalado não é automaticamente religado ao progenitor anterior. Em vez disso, os ponteiros são retirados da pilha e devolvidos ao autor da chamada, permitindo que o chamador anexe o ecrã ou descarte o ecrã devolvido conforme desejado.

### <a name="parameters"></a>Parâmetros

- **popped_parent**: Localização para armazenar o ponteiro widget dos pais.
- **popped_screen**: Localização para armazenar o ponteiro do ecrã estalado.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Recuperação com sucesso dos ponteiros da pilha de ecrã
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_FAILURE:**(0x10) Pilha de tela inválida ou vazia

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
UINT status;

GX_WIDGET *parent_screen;

GX_WIDGET *popped_screen;

/* Pop a screen stack entry. */
status = gx_system_screen_stack_get(&parent_screen, &popped_screen);

/* If status is GX_SUCCESS, parent_screen and
popped_screen hold the topmost screen stack pointers. */
```

### <a name="see-also"></a>Consulte também

- gx_system_screen_stack_create
- gx_system_screen_stack_pop
- gx_system_screen_stack_push
- gx_system_screen_stack_reset

## <a name="gx_system_screen_stack_pop"></a>gx_system_screen_stack_pop

Pop a entrada mais alta da pilha de ecrã do sistema

### <a name="prototype"></a>Prototype

```C
UINT gx_system_screen_stack_pop();
```

### <a name="description"></a>Descrição

Esta função coloca a entrada mais alta na pilha de ecrã e liga automaticamente o ecrã estalado ao widget dos pais.

### <a name="parameters"></a>Parâmetros

**nenhum**

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Recuperação bem sucedida dos ponteiros da pilha de ecrã
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_FAILURE:**(0x10) Pilha de tela inválida ou vazia

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
UINT status;

/* Pop a screen stack entry. */
status = gx_system_screen_stack_pop();

/* If status is GX_SUCCESS, the topmost screen stack entry has been
popped from the stack and re-attached to the previous parent. */
```

### <a name="see-also"></a>Consulte também

- gx_system_screen_stack_get
- gx_system_screen_stack_create
- gx_system_screen_stack_push
- gx_system_screen_stack_reset

## <a name="gx_system_screen_stack_push"></a>gx_system_screen_stack_push

Empurre um widget e um ponteiro dos pais para a pilha de ecrã

### <a name="prototype"></a>Prototype

```C
UINT gx_system_screen_stack_push(GX_WIDGET *screen)
```

### <a name="description"></a>Descrição

Este serviço coloca um ponteiro para o widget indicado, que normalmente é um ecrã de nível superior, na pilha de ecrã. Se o widget tem um pai, é separado do progenitor. O ponteiro widget dos pais também é empurrado para a pilha de ecrã. O widget principal pode ser NU, o que significa que um ecrã que não seja visível ou ligado a qualquer progenitor pode ser empurrado para a pilha de ecrã. Se um widget sem pai for empurrado para a pilha de ecrã, a API de screen_stack_get() deve ser usada para recuperar o ponteiro de ecrã empurrado, em vez de utilizar a API screen_stack_pop,que tenta recolocar o widget estalado ao seu progenitor anterior.

### <a name="parameters"></a>Parâmetros

- **ecrã**: Ponteiro para o widget a ser empurrado para a pilha de ecrã.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Obter com sucesso a aparência da barra de scroll
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Get the scrollbar appearance. */
status = gx_system_screen_stack_push(window);

/* If status is GX_SUCCESS, the widget pointed to by “window” has
been pushed to the screen stack, along with the widget’s parent
ponter. */
```

### <a name="see-also"></a>Consulte também

- gx_system_screen_stack_get
- gx_system_screen_stack_pop
- gx_system_screen_stack_create
- gx_system_screen_stack_reset

## <a name="gx_system_screen_stack_reset"></a>gx_system_screen_stack_reset

Redefinir a pilha de ecrã do sistema

### <a name="prototype"></a>Prototype

```C
UINT gx_system_screen_stack_reset();
```

### <a name="description"></a>Descrição

Esta função remove todas as entradas da pilha de ecrã do sistema. Se os ecrãs saltarem da pilha tiverem blocos de controlo atribuídos dinamicamente atribuídos pelo GUIX Studio, a memória desses blocos de controlo é libertada.

### <a name="parameters"></a>Parâmetros

**nenhum**

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Obter com sucesso a aparência da barra de scroll
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Get the scrollbar appearance. */
status = gx_system_screen_stack_reset();

/* If status is GX_SUCCESS the system screen stack has been cleared
of entries. */
```

### <a name="see-also"></a>Consulte também

- gx_system_screen_stack_get
- gx_system_screen_stack_pop
- gx_system_screen_stack_push
- gx_system_screen_stack_create

## <a name="gx_system_scroll_appearance_get"></a>gx_system_scroll_appearance_get

Obtenha aparência de pergaminho

### <a name="prototype"></a>Prototype

```C
UINT gx_system_scroll_appearance_get(
    ULONG style,
    GX_SCROLLBAR_APPEARANCE *return_appearance);
```

### <a name="description"></a>Descrição

Este serviço obtém a aparência da barra de pergaminho.

### <a name="parameters"></a>Parâmetros

- **estilo**: Estilo barra de rolo: `GX_SCROLLBAR_HORIZONTAL` ou `GX_SCROLLBAR_VERTICAL`
- **return_appearance**: Ponteiro para destino para a aparência. **O apêndice I** contém definição para GX_SCROLLBAR_APPERANCE

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Obter com sucesso a aparência da barra de scroll
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_SCROLLBAR_APPEARANCE my_appearance;

/* Get the scrollbar appearance. */

status = gx_system_scroll_appearance_get(style, &my_appearance);

/* If status is GX_SUCCESS “my_appearance” now contains the scroll
appearance. */
```

### <a name="see-also"></a>Consulte também

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_set
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_scroll_appearance_set"></a>gx_system_scroll_appearance_set

Definir aparência de pergaminho

### <a name="prototype"></a>Prototype

```C
UINT gx_system_scroll_appearance_set(
    ULONG style,
    GX_SCROLLBAR_APPEARANCE *appearance);
```

### <a name="description"></a>Descrição

Este serviço define a aparência de pergaminho predefinido. Quando um pergaminho é criado, esta estrutura de aparência é usada a menos que a aplicação forneça uma versão personalizada.

### <a name="parameters"></a>Parâmetros

- **estilo**: Estilo de `GX_SCROLLBAR_HORIZONTAL` deslocalidade ou `GX_SCROLLBAR_VERTICAL`
- **aparência**: Ponteiro para a estrutura de aparência inicializada com vários atributos de aparência scrollbar. Consulte o **Apêndice I** para a definição da estrutura GX_SCROLLBAR_APPEARANCE.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) definir com sucesso o conjunto de aparência do pergaminho
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_SCROLLBAR_APPEARANCE my_appearance;

memset(&my_appearance, 0, sizeof(GX_SCROLLBAR_APPEARANCE));

my_appearance.gx_scroll_width = 20;
my_appearance.gx_scroll_thumb_width = 18;

my_appearance.gx_scroll_thumb_color = GX_COLOR_ID_SCROLL_BUTTON;
my_appearance.gx_scroll_thumb_border_color = GX_COLOR_ID_SCROLL_BUTTON;
my_appearance.gx_scroll_button_color = GX_COLOR_ID_SCROLL_BUTTON;
my_appearance.gx_scroll_thumb_travel_min = 20;
my_appearance.gx_scroll_thumb_travel_max = 20;
my_appearance.gx_scroll_thumb_border_style = GX_STYLE_BORDER_THIN;

/* Set the scroll appearance. */

status = gx_system_scroll_appearance_set(GX_SCROLLBAR_VERTICAL, &my_appearance);

/* If status is GX_SUCCESS the scroll appearance has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_start"></a>gx_system_start

Iniciar GUIX

### <a name="prototype"></a>Prototype

```C
UINT gx_system_start(VOID);
```

### <a name="description"></a>Descrição

Este serviço inicia o processamento DO GUIX. Em circunstâncias normais, esta função nunca volta, mas em vez disso começa a processar a fila do evento GUIX. Quando a fila do evento GUIX está vazia, este serviço suspende o fio de chamada até que novos eventos cheguem na fila do evento GUIX.

### <a name="parameters"></a>Parâmetros

- **Nenhuma**

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Início do sistema de sucesso
- **GX_CALLER_ERROR:**(0x11) Inválido desta função

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Start GUIX. */
status = gx_system_start();

/* If status is GX_SUCCESS . GUIX has been started. */
```

### <a name="see-also"></a>Consulte também

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_string_get"></a>gx_system_string_get

Obter corda

### <a name="prototype"></a>Prototype

```C
UINT gx_system_string_get(
    GX_RESOURCE_ID string_id,
    GX_CHAR **return_string);
```

### <a name="description"></a>Descrição

Este serviço obtém a cadeia para o ID de recursos especificado, utilizando o primeiro visor definido e o idioma atualmente ativo. Esta função foi depreciada a favor de gx_display_string_get. Todas as novas aplicações devem ser utilizadas gx_display_string_get.

### <a name="parameters"></a>Parâmetros

- **string_id**: ID de recursos de corda
- **return_string**: Ponteiro para ponteiro de destino de cordas

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Cadeia de sucesso obter
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR (0x07)**: Ponteiro inválido
- **GX_INVALID_RESOURCE_ID:**(0x33) ID de recurso inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Get the string associated with MY_STRING_ID. */

status = gx_system_string_get(MY_STRING_RESOURCE_ID, &my_string);

/* If status is GX_SUCCESS the string is contained in “my_string”.
*/
```

### <a name="see-also"></a>Consulte também

- gx_display_string_get
- gx_display_string_table_get
- gx_display_language_table_set

## <a name="gx_system_string_table_get"></a>gx_system_string_table_get

Recupera a mesa de cordas

### <a name="prototype"></a>Prototype

```C
UINT gx_system_string_table_get(
    GX_UBYTE language,
    GX_CHAR ***string_table,
    UINT *get_size);
```

### <a name="description"></a>Descrição

Este serviço recupera a tabela de cordas para o idioma solicitado a partir do primeiro visor. Esta função foi depreciada a favor de gx_display_string_table_get. Todas as novas aplicações devem ser utilizadas gx_display_string_table_get.

### <a name="parameters"></a>Parâmetros

- **linguagem**: Índice de línguas
- **string_table**: Ponter para o espaço de armazenamento do ponteiro da mesa de cordas, ou NULO se o chamador não precisar de levar o ponteiro para a mesa de cordas.
- **get_size**: Pontear para o armazenamento para o número de cordas na mesa de cordas, ou NULO se o chamador não precisar de obter o número de cordas na tabela de cordas.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Tabela de cordas bem sucedida obter
- **GX_CALLER_ERROR:**(0x11) Inválido desta função

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Get the string table. */

CHAR **my_string_table; UINT table_size;

status = gx_system_string_table_get(LANGUAGE_ID_ENGLISH,
    &my_string_table, &table_size);

/* If status is GX_SUCCESS . the pointer to the string table has
been obtained. */
```

### <a name="see-also"></a>Consulte também

- gx_display_string_table_get
- gx_display_string_get
- gx_display_active_language_set
- gx_display_language_table_set

## <a name="gx_system_string_width_get"></a>gx_system_string_width_get

Obtenha a largura da corda (depreciada)

### <a name="prototype"></a>Prototype

```C
UINT gx_system_string_width_get(
    GX_FONT *font, GX_CHAR *string,
    INT string_length,
    GX_VALUE *return_width);
```

### <a name="description"></a>Descrição

Este serviço é precotado a favor de gx_system_string_width_get_ext().

Este serviço calcula a largura de visualização da cadeia fornecida em pixels utilizando o tipo de letra especificado. Se o parâmetro string_length for >= 0, apenas a contagem de pedidos de caracteres está incluída no cálculo. Se o parâmetro string_length for -1, toda a cadeia até ao exterminador NUR é utilizada no cálculo.

### <a name="parameters"></a>Parâmetros

- **fonte**: Ponteiro para o tipo de letra da corda
- **string**: Ponteiro para corda
- **string_length**: Comprimento da corda
- **return_width**: Destino para largura de corda

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Largura de corda bem sucedida obter
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_INVALID_FONT:**(0x16) Fonte inválida
- **GX_INVALID_STRING_LENGTH:**(0x34) Comprimento da corda inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Get the string width of “my_string”. */

status = gx_system_string_width_get(&my_font, &my_string,
    strlen(my_string), &my_width);

/* If status is GX_SUCCESS . “my_width” contains the string width.
*/
```

### <a name="see-also"></a>Consulte também

- gx_system_string_width_get_ext

## <a name="gx_system_string_width_get_ext"></a>gx_system_string_width_get_ext

Obtenha largura de corda

### <a name="prototype"></a>Prototype

```C
UINT gx_system_string_width_get_ext(
    GX_FONT *font,
    GX_STRING *string,
    GX_VALUE *return_width);
```

### <a name="description"></a>Descrição

Este serviço calcula a largura de visualização da cadeia fornecida em pixels utilizando o tipo de letra especificado.

### <a name="parameters"></a>Parâmetros

- **fonte**: Ponteiro para o tipo de letra da corda
- **string**: Ponteiro para corda
- **return_width**: Destino para largura de corda

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Largura de corda bem sucedida obter
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_CALLER_ERROR**: 0x11) Inválido desta função
- **GX_INVALID_FONT:**(0x16) Fonte inválida
- **GX_INVALID_STRING_LENGTH:**(0x34) Comprimento da corda inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_STRING my_string; my_string.gx_string_ptr = “Monday”;

my_string.gx_string_length = strlen(my_string.gx_string_ptr);

/* Get the string width of “my_string”. */

status = gx_system_string_width_get_ext(&my_font,
    &my_string, &my_width);

/* If status is GX_SUCCESS . “my_width” contains the string width.
*/
```

### <a name="see-also"></a>Consulte também

- gx_system_event_fold
- gx_system_focus_claim
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_timer_start"></a>gx_system_timer_start

Temporizador de início

### <a name="prototype"></a>Prototype

```C
UINT gx_system_timer_start(
    GX_WIDGET *owner, 
    UINT timer_id,
    UINT initial_ticks,
    UINT reschedule_ticks);
```

### <a name="description"></a>Descrição

Este serviço inicia um temporizador para o widget especificado. Os GX_MAX_ATIVE_TIMERS constantes definiram os temporizadores máximos ativos suportados. A definição predefinida para este valor é de 32.

### <a name="parameters"></a>Parâmetros

- **proprietário**: Ponteiro para o bloco de controlo widget
- **timer_id**: ID do temporizador
- **initial_ticks:** tiques de expiração iniciais
- **reschedule_ticks**: Tiques de expiração periódica

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Início do temporizador de sucesso
- **GX_OUT_OF_TIMERS**: (0x04) Sem mais temporizadores
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_INVALID_WIDGET:**(0x12) Widget não válido
- **GX_INVALID_VALUE**: (0x22) Valor do temporizador não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Start a periodic timer for the widget “my_widget”. */
status = gx_system_timer_start(&my_widget, MY_TIMER_ID, 10, 20);

/* If status is GX_SUCCESS . the timer for “my_widget” has been
started. */
```

### <a name="see-also"></a>Consulte também

- gx_system_event_fold
- gx_system_focus_claim
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_timer_stop"></a>gx_system_timer_stop

Parar o temporizador

### <a name="prototype"></a>Prototype

```C
UINT gx_system_timer_stop(
    GW_WIDGET *owner, 
    UINT timer_id);
```

### <a name="description"></a>Descrição

Este serviço para o temporizador com o timer_id especificado associado ao widget de chamada. Para parar todos os temporizadores ligados a um widget específico, a aplicação pode passar o valor timer_id de 0.

### <a name="parameters"></a>Parâmetros

- **proprietário**: Ponteiro para o bloco de controlo widget
- **timer_id**: ID do temporizador, ou 0 para todos os temporizadores

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Paragem do temporizador de sucesso
- **GX_NOT_FOUND**: (0x09) ID do temporizador não encontrado
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Stop the periodic timer for the widget “my_widget”. */
status = gx_system_timer_stop(&my_widget, MY_TIMER_ID);

/* If status is GX_SUCCESS . the timer for “my_widget” has been
stopped. */
```

### <a name="see-also"></a>Consulte também

- gx_system_event_fold
- gx_system_focus_claim
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_version_string_get"></a>gx_system_version_string_get

Obter a cadeia de versão da biblioteca GUIX (depreciada)

### <a name="prototype"></a>Prototype

```C
UINT gx_system_version_string_get(GX_CHAR **version);
```

### <a name="description"></a>Descrição

Este serviço é prevadido a favor de gx_system_version_string_get_ext().

Este serviço recupera a cadeia de versão da biblioteca GUIX.

### <a name="parameters"></a>Parâmetros

- **versão**: Ponteiro para devolver o valor da cadeia.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Corda de versão recuperada com sucesso
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_CHAR *version;

/* get the library version string. */

status = gx_system_verrsion_string_get(&version);
```

### <a name="see-also"></a>Consulte também

- gx_system_version_string_get_ext()

## <a name="gx_system_version_string_get_ext"></a>gx_system_version_string_get_ext

Recuperar a versão da biblioteca GUIX

### <a name="prototype"></a>Prototype

```C
UINT gx_system_version_string_get(GX_STRING *version);
```

### <a name="description"></a>Descrição

Este serviço recupera a cadeia de versão da biblioteca GUIX.

### <a name="parameters"></a>Parâmetros

- **versão**: Ponteiro para devolver o valor da cadeia.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Corda de versão recuperada com sucesso
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_STRING_LENGTH:**(0x34) Comprimento da corda inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_STRING version;

/* get the library version string. */

status = gx_system_version_string_get_ext(&version);
```

### <a name="see-also"></a>Consulte também

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_widget_find

## <a name="gx_system_widget_find"></a>gx_system_widget_find

Encontre widget

### <a name="prototype"></a>Prototype

```C
UINT gx_system_widget_find(
    USHORT widget_id,
    INT search_level, 
    GX_WIDGET **return_search_result);
```

### <a name="description"></a>Descrição

Este serviço procura o ID widget especificado. Ao contrário gx_widget_find(), esta função procura as crianças de todas as janelas de raiz definidas no sistema, o que significa que esta é uma pesquisa exaustiva de todos os widgets visíveis. Se conhece o progenitor do widget que procura, use gx_widget_find() em vez disso.

### <a name="parameters"></a>Parâmetros

- **widget_id**: Widget ID para procurar
- **search_level**: Define o nível de nidificação recursivo em que os widgets infantis são pesquisados. Se este valor for 0, apenas crianças imediatas de cada janela raiz são revistadas. Se este valor for GX_SEARCH_DEPTH_INFINITE, a função se enquadra em todas as crianças que procuram o widget ID solicitado. Para qualquer outro valor > 0, o nível de pesquisa define o quão profundamente aninhada esta função irá procurar o ID widget solicitado.
- **return_search_result**: Ponteiro para destino para widget encontrado

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Pesquisa de widgets bem sucedida
- **GX_NOT_FOUND**: (0x09) Widget ID não encontrado
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Search recursively from the top level widget for the widget with
ID of MY_WIDGET_ID. */

status = gx_system_widget_find(MY_WIDGET_ID,
    GX_SEARCH_DEPTH_INFINITE,
    &my_widget);

/* If status is GX_SUCCESS . the search was successful and
“my_widget” contains the pointer to the widget. */
```

### <a name="see-also"></a>Consulte também

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get

## <a name="gx_text_button_create"></a>gx_text_button_create

Criar botão de texto

### <a name="prototype"></a>Prototype

```C
UINT gx_text_button_create(
    GX_TEXT_BUTTON *text_button,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id, 
    ULONG style,
    USHORT text_button_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria um widget de botão de texto.

GX_TEXT_BUTTON é derivado de GX_BUTTON e suporta todos os gx_button serviços da API.

### <a name="parameters"></a>Parâmetros

- **text_button**: Ponteiro para o bloco de controlo de botões de texto
- **nome**: Nome lógico do botão de texto
- **pai**: Ponteiro para o widget dos pais do botão
- **text_id**: ID de recursos de texto
- **estilo**: Estilo de botão de texto. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **text_button_id**: ID definido por aplicação do botão de texto
- **tamanho**: Tamanho do botão

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Cria um botão de texto bem sucedido
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_ALREADY_CREATED**: (0x13) Widget já criado
- **GX_INVALID_SIZE**: (0x19) Tamanho do bloco de controlo de widget inválido
- **GX_INVALID_WIDGET**: (0x12) Widget parental não válido


### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_TEXT_BUTTON my_text_button;

GX_RECTANGLE size;

/* Define widget size. */

gx_utility_rectangle_define(&size, 0, 0, 100, 100);

/* Create text button “my_text_button”. */

status = gx_text_button_create(&my_text_button, "my text button",
    &my_parent_window, MY_TEXT_RESOURCE_ID,
    GX_STYLE_BUTTON_TOGGLE, MY_TEXT_BUTTON_ID, &size);

/* If status is GX_SUCCESS, the text button “my_text_button” was
created. */
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_color_set
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_draw"></a>gx_text_button_draw

Desenhe botão de texto

### <a name="prototype"></a>Prototype

```C
VOID gx_text_button_draw(GX_TEXT_BUTTON *button);
```

### <a name="description"></a>Descrição

Este serviço desenha o botão de texto. Este serviço é normalmente chamado internamente durante a atualização de lona, mas também pode ser chamado de funções de desenho de botões de texto personalizados.

### <a name="parameters"></a>Parâmetros

- **botão**: Ponteiro para bloco de controlo de botões de texto

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom text button draw function. */

VOID my_text_button_draw(GX_TEXT_BUTTON *text_button)
{
    /* Call default text button draw. */
    gx_text_button_draw(text_button);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_event_process
- gx_text_button_color_set
- gx_text_button_font_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_event_process"></a>gx_text_button_event_process


Evento de botão de texto do processo

### <a name="prototype"></a>Prototype

```C
UINT gx_text_button_event_process(GX_TEXT_BUTTON *text_button, GX_EVENT *event_ptr);
```

### <a name="description"></a>Descrição

Este serviço processa um evento para o botão de texto especificado. Este serviço deve ser chamado como o manipulador de eventos predefinido por quaisquer funções de processamento de eventos de botão de texto personalizado.

### <a name="parameters"></a>Parâmetros

- **text_button** Ponteiro para bloco de controlo de botões de texto
- **event_ptr** Ponteiro para o evento para processar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Processo de evento de botão de texto bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Call generic text button event processing as part of custom event processing function. */

UINT custom_text_button_event_process(GX_TEXT_BUTTON *text_button, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default text button event processing */
        status = gx_text_button_event_process(wheel, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_color_set
- gx_text_button_font_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_font_set"></a>gx_text_button_font_set

Desa estação de fonte para botão de texto

### <a name="prototype"></a>Prototype

```C
UINT gx_text_button_font_set(
    GX_TEXT_BUTTON *button,
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Descrição

Este serviço atribui um tipo de letra ao botão especificado.

### <a name="parameters"></a>Parâmetros

- **botão**: Ponteiro para bloco de controlo de botões de texto
- **font_id**: ID de recursos fo a fonte

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Definir com sucesso a fonte
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the text button with the font ID MY_FONT. */
status = gx_text_button_font_set(&my_text_button, MY_FONT);

/* If status is GX_SUCCESS, the font of the text button
“my_text_button” was set to MY_FONT. */
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_color_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_text_color_set"></a>gx_text_button_text_color_set

Definir cor de botão de texto

### <a name="prototype"></a>Prototype

```C
UINT gx_text_button_text_color_set(
    GX_TEXT_BUTTON *text_button,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCE_ID disabled_text_color_id);
```

### <a name="description"></a>Descrição

Este serviço define a cor do botão de texto.

### <a name="parameters"></a>Parâmetros

- **text_button**: Ponteiro para o bloco de controlo de botões de texto
- **normal_text_color_id**: Identificação de recursos do texto normal. **O apêndice A** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.
- **selected_text_color_id**: ID de recursos de texto selecionado. **O apêndice A** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.
- **disabled_text_color_id**: ID de cor de recurso para texto desativado. **O apêndice A** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Conjunto de cores de botão de texto bem sucedido
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the color of the text button “my_text_button”. */
status = gx_text_button_text_color_set(&my_text_button,
    GX_COLOR_ID_NORMAL_TEXT,
    GX_COLOR_ID_SELECTED_TEXT,
    GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS, the text color of “my_text_button” was
set. */
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_text_draw"></a>gx_text_button_text_draw

Função de suporte para desenhar texto de botão

### <a name="prototype"></a>Prototype

```C
VOID gx_text_button_text_draw(GX_TEXT_BUTTON *text_button);
```

### <a name="description"></a>Descrição

Esta função de suporte desenha a parte de texto de um botão de texto. Esta função é chamada internamente por gx_text_button_draw, e é fornecida como uma API separada como uma conveniência para aplicações que definem uma função de desenho de botão personalizado. As aplicações que pretendem personalizar o desenho de fundo do botão podem fornecer a sua função de desenho personalizado e invocar o serviço de gx_text_button_text_draw como parte do seu desenho personalizado para desenhar o texto do botão sobre o fundo.

### <a name="parameters"></a>Parâmetros

- **text_button**: Ponteiro para o bloco de controlo de botões de texto

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Define a custom drawing function */

VOID my_button_draw(GX_TEXT_BUTTON *button)
{
    /* Insert code here to draw button background */

    /* Call support function to do text drawing */
    gx_text_button_text_draw(button);

    /* Draw child widgets */
    gx_widget_children_draw((GX_WIDGET *) button);
}
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_text_get"></a>gx_text_button_text_get

Obtenha texto do botão de texto (precotado)

### <a name="prototype"></a>Prototype

```C
UINT gx_text_button_text_get(
    GX_TEXT_BUTTON *text_button,
    GX_CHAR **return_text);
```

### <a name="description"></a>Descrição

Este serviço é prevadido a favor de gx_text_button_text_get_ext().

Este serviço recupera a cadeia especificada do botão de texto.

### <a name="parameters"></a>Parâmetros

- **text_button**: Ponteiro para o bloco de controlo de botões de texto
- **return_text**: Ponteiro para a corda recuperada do botão de texto

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Obtenha com sucesso o texto do botão
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_CHAR *string;

/* Get the string from the text button “my_text_button”. */
status = gx_text_button_text_get(&my_text_button, &string);

/* If status is GX_SUCCESS, the string pointer from
“my_text_button” is retrieved and stored in string. */
```

### <a name="see-also"></a>Consulte também

- gx_text_button_text_get_ext

## <a name="gx_text_button_text_get_ext"></a>gx_text_button_text_get_ext

Obtenha texto do botão de texto

### <a name="prototype"></a>Prototype

```C
UINT gx_text_button_text_get_ext(
    GX_TEXT_BUTTON *text_button,
    GX_STRING *return_string);
```

### <a name="description"></a>Descrição

Este serviço recupera a cadeia especificada do botão de texto.

### <a name="parameters"></a>Parâmetros

- **text_button**: Ponteiro para o bloco de controlo de botões de texto
- **return_string**: Ponteiro para a corda recuperada do botão de texto

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Obtenha com sucesso o texto do botão
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_STRING string;

/* Get the string from the text button “my_text_button”. */
status = gx_text_button_text_get_ext(&my_text_button, &string);

/* If status is GX_SUCCESS, the string pointer and length from
“my_text_button” is retrieved and stored in string. */
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_text_id_set"></a>gx_text_button_text_id_set

Definir iD de recursos de texto para o botão de texto

### <a name="prototype"></a>Prototype

```C
UINT gx_text_button_text_id_set(
    GX_TEXT_BUTTON *text_button,
    RESOURCE_ID string_id);
```

### <a name="description"></a>Descrição

Este serviço define o ID de recurso de cadeia especificado para o botão de texto.

### <a name="parameters"></a>Parâmetros

- **text_button**: Ponteiro para o bloco de controlo de botões de texto
- **string_id**: ID de recursos da cadeia

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) definir com sucesso o ID do recurso de corda para o botão de texto
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido
- **GX_INVALID_RESOURCE_ID:**(0x33) ID de corda não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the string ID ”MY_STRING_ID” to the text button
“my_text_button”. */

status = gx_text_button_text_id_set(&my_text_button,
    MY_STRING_ID);

/* If status is GX_SUCCESS, the string ID MY_STRING_ID was set to
“my_text_button”. */
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_get

## <a name="gx_text_button_text_set"></a>gx_text_button_text_set

Atribuir texto ao botão de texto (precotado)

### <a name="prototype"></a>Prototype

```C
UINT gx_text_button_text_set(
    GX_TEXT_BUTTON *text_button,
    GX_CHAR *text);
```

### <a name="description"></a>Descrição

Este serviço é precotado a favor de gx_text_button_text_set_ext().

Este serviço atribui a cadeia especificada ao botão de texto. Se o widget text_button foi criado com GX_STYLE_TEXT_COPY de estilo, o widget cria uma cópia privada da cadeia de texto atribuída. Se GX_STYLE_TEXT_COPY não estiver ativa, o widget não faz uma cópia privada da cadeia de entrada, pelo que a cadeia deve ser atribuída estática ou globalmente, ou seja, pode não ser uma variável automática ou temporária.

### <a name="parameters"></a>Parâmetros

- **text_button**: Ponteiro para o bloco de controlo de botões de texto
- **texto**: ponteiro para a cadeia terminada nulo

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) definir o texto com sucesso para o botão
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) O alocador de memória não definido ou a atribuição de memória falhou
- **GX_INVALID_STRING_LENGTH:**(0x34) Comprimento da corda inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the string “my string” to the text button “my_text_button”.
*/

status = gx_text_button_text_set(&my_text_button, “my string”);

/* If status is GX_SUCCESS, the string “my_text_button” was set.
*/
```

### <a name="see-also"></a>Consulte também

- gx_text_button_event_process
- gx_text_button_text_set_ext
- gx_text_button_text_id_set

## <a name="gx_text_button_text_set_ext"></a>gx_text_button_text_set_ext

Atribuir texto ao botão de texto

### <a name="prototype"></a>Prototype

```C
UINT gx_text_button_text_set_ext(
    GX_TEXT_BUTTON *text_button,
    GX_STRING *string);
```

### <a name="description"></a>Descrição

Este serviço atribui a cadeia especificada ao botão de texto. Se o widget text_button foi criado com GX_STYLE_TEXT_COPY de estilo, o widget cria uma cópia privada da cadeia de texto atribuída. Se GX_STYLE_TEXT_COPY não estiver ativa, o widget não faz uma cópia privada da cadeia de entrada, pelo que a cadeia deve ser atribuída estática ou globalmente, ou seja, pode não ser uma variável automática ou temporária.

### <a name="parameters"></a>Parâmetros

- **text_button**: Ponteiro para o bloco de controlo de botões de texto
- **corda:** ponteiro para a variável GX_STRING

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) definir o texto com sucesso para o botão
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) O alocador de memória não definido ou a atribuição de memória falhou
- **GX_INVALID_STRING_LENGTH:**(0x34) Comprimento da corda inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_STRING new_string; new_string.gx_string_ptr = “Monday”;

new_string.gx_string_length = strlen(new_string.gx_string_ptr);

/* Assign the string “new_string” to the text button
“my_text_button”. */

status = gx_text_button_text_set_ext(&my_text_button, &new_string);

/* If status is GX_SUCCESS, the string “my_text_button” was set.
*/
```

### <a name="see-also"></a>Consulte também

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_get
- gx_text_button_text_id_set

## <a name="gx_text_input_cursor_blink_interval_set"></a>gx_text_input_cursor_blink_interval_set

Definir intervalo de piscar cursor

### <a name="prototype"></a>Prototype

```C
UINT gx_text_input_cursor_blink_interval_set(
    GX_TEXT_INPUT_CURSOR *cursor_input,
    GX_UBYTE blink_interval);
```

### <a name="description"></a>Descrição

Este serviço define o valor do intervalo intermitente do cursor.

### <a name="parameters"></a>Parâmetros

- **cursor_input** Bloco de controlo do cursor
- **blink_interval** Valor a definir

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Definir com sucesso o intervalo de piscar do cursor
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_VALUE:**(0x22) Valor de intervalo intermitente não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_TEXT_INPUT_CURSOR *input_cursor;

/* Pointer the input cursor to the cursor instance of single/multi
line text input widget. */

input_cursor = &sl_input.gx_single_line_text_input_cursor_instance;

/* Set the blink interval value of “input_cursor” to 2. */
status = gx_text_input_cursor_blink_interval_set(input_cursor, 2);

/* If status is GX_SUCCESS, the blink interval value of
“input_cursor” has been successfully set to 2. */
```

### <a name="see-also"></a>Consulte também

- gx_text_input_cursor_height_set
- gx_text_input_cursor_width_set

## <a name="gx_text_input_cursor_height_set"></a>gx_text_input_cursor_height_set

Definir altura do cursor

### <a name="prototype"></a>Prototype

```C
UINT gx_text_input_cursor_height_set(
    GX_TEXT_INPUT_CURSOR *cursor_input,
    GX_UBYTE height);
```

### <a name="description"></a>Descrição

Este serviço define a altura do cursor.

### <a name="parameters"></a>Parâmetros

- **cursor_input**: Bloco de controlo cursor
- **altura** Valor a definir

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Definir com sucesso a altura do cursor
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_VALUE:**(0x22) Valor de altura não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_TEXT_INPUT_CURSOR *input_cursor;

/* Pointer the input cursor to the cursor instance of single/multi
line text input widget. */

input_cursor = &sl_input.gx_single_line_text_input_cursor_instance;

/* Set height value of “input_cursor”. */
status = gx_text_input_cursor_height_set(&input_cursor, 15);

/* If status is GX_SUCCESS, the height value of “input_curosr” has
been successfully set to 15. */
```

### <a name="see-also"></a>Consulte também

- gx_text_input_cursor_blink_interval_set
- gx_text_input_cursor_width_set

## <a name="gx_text_input_cursor_width_set"></a>gx_text_input_cursor_width_set

Definir largura do cursor

### <a name="prototype"></a>Prototype

```C
UINT gx_text_input_cursor_blink_width_set(
    GX_TEXT_INPUT_CURSOR *cursor_input,
    GX_UBYTE *width);
```

### <a name="description"></a>Descrição

Este serviço define a largura do cursor.

### <a name="parameters"></a>Parâmetros

- **cursor_input**: Bloco de controlo cursor
- **largura**: Valor a definir

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Definir com sucesso a largura do cursor
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_VALUE:**(0x22) Valor de largura não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_TEXT_INPUT_CURSOR *input_cursor;

/* Pointer the input cursor to the cursor instance of single/multi
line text input widget. */

input_cursor = &sl_input.gx_single_line_text_input_cursor_instance;

/* Set width of “input_curosr” to 2. */

status = gx_text_input_cursor_blink_width_set(&input_cursor, 2);

/* If status is GX_SUCCESS, the width of “input_cursor” has been
successfully set to 2. */
```

### <a name="see-also"></a>Consulte também

- gx_text_input_cursor_blink_interval_set
- gx_text_input_cursor_height_set

## <a name="gx_text_scroll_wheel_callback_set"></a>gx_text_scroll_wheel_callback_set

Atribuir a função de retorno da roda de deslocamento do tipo de texto (precotado)

### <a name="prototype"></a>Prototype

```C
UINT gx_text_scroll_wheel_callback_set(
    GX_TEXT_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *(*callback)(GX_TEXT_SCROLL_WHEEL *, int));
```

### <a name="description"></a>Descrição

Este serviço é prevadido a favor de gx_text_scroll_wheel_callback_set_ext().

Este serviço atribui a função de retorno que uma roda de deslocação do tipo de texto invocará para determinar o fio de texto a ser apresentado em cada linha da roda de deslocação.

Para GX_NUMERIC_SCROLL_WHEEL e GX_STRING_SCROLL_WHEEL, são fornecidas funções de retorno predefinidos e a aplicação não precisa de fazer quaisquer alterações para utilizar estas implementações padrão.

Esta API é fornecida para permitir que a aplicação personalize a formatação ou outros parâmetros da cadeia que é exibida em cada linha do widget da roda de deslocamento.

A função de retorno receberá como entrada um ponteiro para o bloco de controlo da roda de deslocação e o número de linha que está sendo apresentado. A função deve devolver um ponteiro a uma cadeia de texto.

### <a name="parameters"></a>Parâmetros

- **roda** Endereço do bloco de controlo da roda de roda de roda de cadeia
- **callback** Função de retorno do ponteiro

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Configurar com sucesso o retorno
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_TEXT_SCROLL_WHEEL wheel;

GX_CHAR string_buffer[20];

GX_CHAR *my_wheel_callback(GX_TEXT_SCROLL_WHEEL *wheel, int row)
{
    /* Just for an example, return row number as string for rows
    >= 0, and return text “Invalid” otherwise */
    if (row >= 0)
    {
        gx_utility_ltoa(row, string_buffer, 20);
    }
    else
    {
        return(“Invalid”);
    }
}

gx_text_scroll_wheel_create(&wheel, “my wheel”, root, 10,
    GX_STYLE_ENABLED|GX_STYLE_TEXT_CENTER|GX_STYLE_TRANSPARENT|
    GX_STYLE_WRAP|ID_MY_WHEEL, &size);

status = gx_text_scroll_wheel_callback_set(&wheel,
    my_wheel_callback);

/* If status is GX_SUCCESS, the scroll whell callback function has
been set. */
```

### <a name="see-also"></a>Consulte também

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_callback_set_ext"></a>gx_text_scroll_wheel_callback_set_ext

Atribua a função de retorno da roda de deslocamento do tipo de texto

### <a name="prototype"></a>Prototype

```C
UINT gx_text_scroll_wheel_callback_set_ext(
    GX_TEXT_SCROLL_WHEEL *wheel,
    UINT *(*callback)(GX_TEXT_SCROLL_WHEEL *, int, GX_STRING *));
```

### <a name="description"></a>Descrição

Este serviço atribui a função de retorno que uma roda de deslocação do tipo de texto invocará para determinar o fio de texto a ser apresentado em cada linha da roda de deslocação.

Para GX_NUMERIC_SCROLL_WHEEL e GX_STRING_SCROLL_WHEEL, são fornecidas funções de retorno predefinidos e a aplicação não precisa de fazer quaisquer alterações para utilizar estas implementações padrão.

Esta API é fornecida para permitir que a aplicação personalize a formatação ou outros parâmetros da cadeia que é exibida em cada linha do widget da roda de deslocamento.

A função de retorno receberá como entrada um ponteiro para o bloco de controlo da roda de deslocação e o número de linha que está sendo apresentado. A função deve devolver um ponteiro a uma cadeia de texto.

### <a name="parameters"></a>Parâmetros

- **roda** Endereço do bloco de controlo da roda de roda de roda de cadeia
- **callback** Função de retorno do ponteiro

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Configurar com sucesso o retorno
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_TEXT_SCROLL_WHEEL wheel;

GX_CHAR string_buffer[20];

UINT *my_wheel_callback(GX_TEXT_SCROLL_WHEEL *wheel, int row,
    GX_STRING *return_string)
{
    /* Just for an example, return row number as string for rows
    >= 0, and return text “Invalid” otherwise */
    if (row >= 0)
    {
        gx_utility_ltoa(row, string_buffer, 20);
        return_string->gx_string_ptr = string_buffer;
        return_string->gx_string_length = strlen(string_buffer);
    }
    else
    {
        return_string->gx_string_ptr = “Invalid”;
        return_string->gx_string_length = strlen(“Invalid”);
    }

    return GX_SUCCESS;
}

gx_text_scroll_wheel_create(&wheel, “my wheel”, root, 10,
    GX_STYLE_ENABLED|GX_STYLE_TEXT_CENTER|GX_STYLE_TRANSPARENT|
    GX_STYLE_WRAP|ID_MY_WHEEL, &size);

status = gx_text_scroll_wheel_callback_set_ext(&wheel,
    my_wheel_callback);

/* If status is GX_SUCCESS, the scroll whell callback function has
been set. */
```

### <a name="see-also"></a>Consulte também

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_create"></a>gx_text_scroll_wheel_create

Criar uma roda de pergaminho de texto

### <a name="prototype"></a>Prototype

```C
UINT gx_text_scroll_wheel_create(
    GX_TEXT_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent, 
    INT total_rows,
    ULONG style, 
    USHORT Id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria uma roda de deslocação de texto. A roda de deslocação de texto é um widget base para os widgets GX_STRING_SCROLL_WHEEL e GX_NUMERIC_SCROLL_WHEEL tipo. Esta função é chamada internamente por gx_string_scroll_wheel_create e gx_numeric_scroll_wheel_create, e é fornecida como uma API separada como uma conveniência para aplicações que definem um widget de roda de deslocal personalizado.

### <a name="parameters"></a>Parâmetros

- **roda**: Endereço do bloco de controlo da roda de deslocação de texto
- **nome**: Nome de widget definido por aplicação
- **pai**: Mãe da roda ou GX_NULL
- **total_rows**: Filas totais a apresentar ao utilizador
- **estilo**: Bandeiras de estilo desejadas
- **Id**: Aplicação definida bandeiras de estilo roda
- **tamanho**: Tamanho inicial da roda de deslocação

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Roda de pergaminho de texto criada com sucesso
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_ALREADY_CREATED**: (0x13) Widget já criado
- **GX_INVALID_WIDGET:**(0x12) Widget não válido


### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Define a custom scroll wheel widget. */
typedef MY_SCROLL_WHEEL_STRUCT
{
    GX_TEXT_SCROLL_WHEEL text_scroll_wheel;

    /* Add custom members here. */

} MY_SCROLL_WHEEL;

MY_SCROLL_WHEEL my_scroll_wheel;

UINT my_scroll_wheel_create(MY_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *name, GX_WIDGET *parent,
    INT total_rows, ULONG style, USHORT Id,
    GX_CONST GX_RECTANGLE *size)
{
    /* Call base creation. */
    status = gx_text_scroll_wheel_create(
        &wheel.text_scroll_wheel,
        ”my_text_scroll_wheel”, GX_NULL, 7,
        GX_STYLE_ENABLED, ID_MY_SCROLL_WHEEL, &size);

    if (status == GX_SUCCESS)
    {
        /* Add custom initialization here. */
        if(parent)
        {
            gx_widget_link(parent, (GX_WIDGET *)wheel);
        }
    }
}
```

### <a name="see-also"></a>Consulte também

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_string_id_list_set
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_draw"></a>gx_text_scroll_wheel_draw

Desenhe uma roda de rolo de texto

### <a name="prototype"></a>Prototype

```C
VOID gx_text_scroll_wheel_draw(GX_TEXT_SCROLL_WHEEL *wheel);
```

### <a name="description"></a>Descrição

Esta é a função de desenho predefinido para todos os tipos de rodas com base em GX_TEXT_SCROLL_WHEEL. Esta função pode ser ultrapassada por aplicações que requerem a personalização da aparência de desenho da roda de rolo de texto.

GX_STRING_SCROLL_WHEEL e GX_NUMERIC_SCROLL_WHEEL são baseados ou derivados de GX_TEXT_SCROLL_WHEEL.

### <a name="parameters"></a>Parâmetros

- **roda**: Endereço do bloco de controlo da roda de roda de roda de fio

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Write a custom wheel draw function. */
UINT my_wheel_draw(GX_TEXT_SCROLL_WHEEL *wheel)
{
    /* Perform default drawing */
    gx_text_scroll_wheel_draw(wheel);

    /* Add custom drawing here */
}
```

### <a name="see-also"></a>Consulte também

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_event_process"></a>gx_text_scroll_wheel_event_process


Evento de roda de pergaminho de texto do processo

### <a name="prototype"></a>Prototype

```C
UINT gx_text_scroll_wheel_event_process(GX_TEXT_SCROLL_WHEEL *wheel, GX_EVENT *event_ptr);
```

### <a name="description"></a>Descrição

Este serviço processa um evento para a roda de deslocação de texto especificada. Este serviço deve ser chamado como o manipulador de eventos predefinido por quaisquer funções de processamento de eventos de roda de rolo de texto personalizado.

### <a name="parameters"></a>Parâmetros

- **roda** Ponteiro para bloco de controlo da roda de deslocação de texto
- **event_ptr** Ponteiro para o evento para processar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Processo de evento de roda de rolo de texto bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Call generic text scroll wheel event processing as part of custom event processing function. */

UINT custom_text_scroll_wheel_event_process(GX_TEXT_SCROLL_WHEEL *wheel, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default text scroll wheel event processing */
        status = gx_text_scroll_wheel_event_process(wheel, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Consulte também

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_font_set"></a>gx_text_scroll_wheel_font_set

Atribuir fontes usadas para desenhar linhas de roda de deslocação

### <a name="prototype"></a>Prototype

```C
UINT gx_text_scroll_font_set(
    GX_TEXT_SCROLL_WHEEL *wheel,
    GX_RESOURCE_ID normal_font, 
    GX_RESOURCE_ID selected_font);
```

### <a name="description"></a>Descrição

Atribua o uso dos tipos de letra para desenhar o texto de um widget baseado na roda de texto.

### <a name="parameters"></a>Parâmetros

- **roda**: Endereço do bloco de controlo da roda de roda de roda de fio

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Fonte de roda atribuída com sucesso
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_NUMERIC_SCROLL_WHEEL wheel;

status = gx_text_scroll_wheel_font_set(&wheel,
    GX_FONT_ID_WHEEL_NORMAL,
    GX_FONT_ID_WHEEL_SELECTED);

/* If status is GX_SUCCESS, the scroll wheel fonts have been assigned. */
```

### <a name="see-also"></a>Consulte também

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_text_color_set"></a>gx_text_scroll_wheel_text_color_set

Atribuir cores usadas para desenhar linhas de roda de deslocação

### <a name="prototype"></a>Prototype

```C
UINT gx_text_scroll_wheel_text_color_set(
    GX_TEXT_SCROLL_WHEEL *wheel,
    GX_RESOURCE_ID normal_text_color,
    GX_RESOURCE_ID selected_text_color,
    GX_RESOURCe_ID disabled_text_color);
```

### <a name="description"></a>Descrição

Esta função atribui as cores de texto utilizadas para desenhar uma linha de roda de deslocamento baseada em texto.

### <a name="parameters"></a>Parâmetros

- **roda**: Endereço do bloco de controlo da roda de roda de roda de fio
- **normal_text_color**: Cor usada para desenhar linhas não selecionadas
- **selected_text_color**: Cor utilizada para desenhar linha selecionada.
- **disabled_text_color**: Cor utilizada para desenhar texto para widget desativado.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Cor de texto da roda de deslocal
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_STRING_SCROLL_WHEEL wheel;

UINT status = gx_text_scroll_wheel_text_color_set(&wheel,
    GX_COLOR_ID_NORMAL_TEXT,
    GX_COLOR_ID_SELECTED_TEXT,
    GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS, the colors used to draw the wheel text have been assigned. */
```

### <a name="see-also"></a>Consulte também

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_font_set

## <a name="gx_tree_view_create"></a>gx_tree_view_create

Criar uma vista de árvore

### <a name="prototype"></a>Prototype

```C
UINT gx_tree_view_create(
    GX_TREE_VIEW *tree,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent,
    ULONG style, 
    USHORT tree_view_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria uma vista de árvore conforme especificado e associa a vista da árvore com o widget progenitor fornecido. Aceita todos os tipos de widget como item do menu infantil. Recomenda-se a utilização de GX_MENU widget tipo como item do menu infantil.

GX_TREE_VIEW é derivado de GX_WINDOW e suporta todos os gx_window serviços da API.

### <a name="parameters"></a>Parâmetros

- **árvore**: Ponteiro para bloco de controlo da vista da árvore
- **nome**: Nome da vista para a árvore
- **pai**: Ponteiro para widget dos pais
- **estilo**: Estilo do widget. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **menu_id**: ID definido pela aplicação da vista da árvore
- **tamanho** da vista da árvore

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Criação de visão de árvore bem sucedida
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_ALREADY_CREATED**: (0x13) Widget já criado
- **GX_INVALID_SIZE**: (0x19) Tamanho do bloco de controlo de widget inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
status = gx_tree_view_create(&my_tree_view,
    “my_tree_view”, parent,
    GX_STYLE_ENABLED, MY_TREE_VIEW_ID,
    &size);

/* If status is GX_SUCCESS the tree view was successfully created. */
```

### <a name="see-also"></a>Consulte também

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_draw"></a>gx_tree_view_draw

Desenhar vista de árvore

### <a name="prototype"></a>Prototype

```C
VOID gx_tree_view_draw(GX_TREE_VIEW *tree);
```

### <a name="description"></a>Descrição

Este serviço desenha a vista de árvores especificada. Esta função é normalmente chamada internamente pelo mecanismo de atualização de lona GUIX, mas está exposta à aplicação para ajudar na implementação de funções de desenho personalizado para widgets de vista personalizados para a visão de árvore.

### <a name="parameters"></a>Parâmetros

- **árvore** Ponteiro para bloco de controlo da vista da árvore

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom tree view draw function. */
UINT my_tree_view_draw(GX_TREE_VIEW *tree_view)
{
    /* Perform default drawing */
    gx_tree_view_draw(tree_view);

    /* Add custom drawing here */
}
```

### <a name="see-also"></a>Consulte também

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_event_process"></a>gx_tree_view_event_process

Evento de visão de árvore de processo

### <a name="prototype"></a>Prototype

```C
UINT gx_tree_view_event_process(
    GX_TREE_VIEW *tree, 
    GX_EVENT event_ptr);
```

### <a name="description"></a>Descrição

Este serviço processa um evento para a vista de árvores especificada. Este serviço deve ser chamado como o manipulador de eventos predefinido por quaisquer funções de processamento de eventos de visualização de árvores personalizadas.

### <a name="parameters"></a>Parâmetros

- **árvore**: Ponteiro para bloco de controlo da vista da árvore
- **event_ptr**: Ponteiro para o evento para processar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Evento de visualização de árvores de processo bem sucedido
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Call generic tree view event processing as part of custom event
    processing function. */

UINT custom_tree_view_event_process(GX_TREE_VIEW *tree_view,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
        case xyz:
            /* Insert custom event handling here */
            break;
        default:
            /* Pass all other events to the default tree view
                event processing */
            status = gx_tree_view_event_process(tree_view, event);
            break;
    }
}
return status;
```

### <a name="see-also"></a>Consulte também

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_indentation_set"></a>gx_tree_view_indentation_set

Conjunto de recuo da vista da árvore

### <a name="prototype"></a>Prototype

```C
UINT gx_tree_view_indentation_set(
    GX_TREE_VIEW *tree,
    GX_VALUE indentation);
```

### <a name="description"></a>Descrição

Este serviço define o entalhe para a vista da árvore.

### <a name="parameters"></a>Parâmetros

- **árvore**: Ponteiro para bloco de controlo da vista da árvore
- **Recuo**: Recuo a definir

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Marcação da vista da árvore com sucesso
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set tree view “my_tree” indentation to 10. */
status = gx_tree_view_indentation_set(&my_tree, 10);

/* If status is GX_SUCCESS the indentation of tree view “my_tree”
has been set to 10. */
```

### <a name="see-also"></a>Consulte também

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixemlap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_position"></a>gx_tree_view_position

Posicione os itens de vista da árvore

### <a name="prototype"></a>Prototype

```C
UINT gx_tree_view_position(GX_TREE_VIEW *tree);
```

### <a name="description"></a>Descrição

Este serviço posiciona os itens de vista para a árvore.

### <a name="parameters"></a>Parâmetros

- **árvore**: Ponteiro para bloco de controlo da vista da árvore

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Itens de vista de árvores bem posicionados
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Position tree view “my_tree” items. */
status = gx_tree_view_position(&my_tree);

/* If status is GX_SUCCESS the items of tree view “my_tree” has
been positioned. */
```

### <a name="see-also"></a>Consulte também

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_root_line_color_set"></a>gx_tree_view_root_line_color_set

Definir cor de linha de raiz de vista de árvore

### <a name="prototype"></a>Prototype

```C
UINT gx_tree_view_root_line_color_set(
    GX_TREE_VIEW *tree,
    GX_RESOURCE_ID color_id);
```

### <a name="description"></a>Descrição

Este serviço atribui a cor da linha de raiz para a vista da árvore.

### <a name="parameters"></a>Parâmetros

- **árvore**: Ponteiro para bloco de controlo da vista da árvore
- **color_id**: Id de recursos da cor da linha raiz

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Cor de linha de raiz definida com sucesso
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set root line color for tree view “my_tree”. */

status = gx_tree_view_root_line_color_set(&my_tree,
    MY_ROOT LINE_COLOR_ID);

/* If status is GX_SUCCESS the root line color of the tree view
“my_tree” has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_root_pixelmap_set"></a>gx_tree_view_root_pixelmap_set

Definir pixelmap raiz de raiz de árvore

### <a name="prototype"></a>Prototype

```C
UINT gx_tree_view_root_pixelmap_set(
    GX_TREE_VIEW *tree,
    GX_RESOURCE_ID expand_map_id,
    GX_RESOURCE_ID collapse_map_id);
```

### <a name="description"></a>Descrição

Este serviço atribui mapa de pixels de expansão e colapso para a vista da árvore.

### <a name="parameters"></a>Parâmetros

- **árvore**: Ponteiro para bloco de controlo da vista da árvore
- **expand_map_id**: Id de recursos de expansão do pixelmap
- **collapse_map_id**: Id de recursos do pixelmap de colapso

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) definir com sucesso o pixelmap raiz
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set root pixelmaps for tree view “my_tree”. */

status = gx_tree_view_root_pixelmap_set(&my_tree,
    MY_EXPAND_MAP_ID,
    MY_COLLAPSE_MAP_ID);

/* If status is GX_SUCCESS the root pixelmaps of tree view
“my_tree” has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_selected_get"></a>gx_tree_view_selected_get

Obtenha o item selecionado

### <a name="prototype"></a>Prototype

```C
UINT gx_tree_view_selected_get(
    GX_TREE_VIEW *tree,
    GX_WIDGET **selected);
```

### <a name="description"></a>Descrição

Este serviço recupera o item atual selecionado da vista da árvore.

### <a name="parameters"></a>Parâmetros

- **árvore**: Ponteiro para bloco de controlo da vista da árvore
- **selecionado**: Ponteiro para ponteiro widget selecionado

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) itens selecionados com sucesso
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Retrieve selected item of tree view “my_tree”. */

GX_WIDGET *selected;

status = gx_tree_view_selected_get(&my_tree, &selected);

/* If status is GX_SUCCESS the selected item of tree view “my_tree”
has been retrieved. */
```

### <a name="see-also"></a>Consulte também

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_set

## <a name="gx_tree_view_selected_set"></a>gx_tree_view_selected_set

Definir item selecionado

### <a name="prototype"></a>Prototype

```C
UINT gx_tree_view_selected_set(
    GX_TREE_VIEW *tree,
    GX_WIDGET *selected);
```

### <a name="description"></a>Descrição

Este serviço define o item selecionado para a vista para a árvore.

### <a name="parameters"></a>Parâmetros

- **árvore**: Ponteiro para bloco de controlo da vista da árvore
- **selecionado**: Ponteiro para o novo item selecionado

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Menu de sorteio bem sucedido
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR:**(0x07) Ponteiro inválido
- **GX_INVALID_WIDGET:**(0x12) Widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set selected item of tree view “my_tree” to “tree_view_item’. */
status = gx_tree_view_selected_set(&my_tree, &tree_view_item);

/* If status is GX_SUCCESS selected item of tree view “my_menu” has
been set to “tree_view_item”. */
```

### <a name="see-also"></a>Consulte também

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get

## <a name="gx_utility_canvas_to_bmp"></a>gx_utility_canvas_to_bmp

Converter memorando de lona em bitmap

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_canvas_to_bmp(
    GX_CANVAS *canvas, 
    GX_RECTANGLE *rect,
    UINT (*write_data)(GX_UBYTE *byte_data, UINT data_count));
```

### <a name="description"></a>Descrição

Este serviço converte a memória de tela em ficheiro bitmap.

### <a name="parameters"></a>Parâmetros

- **tela**: Ponteiro do bloco de controlo de lona
- **rect**: Retângulo para converter
- **write_data**: Ponteiro da função Callback para escrever dados para

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Valor inteiro convertido com sucesso em corda
- **GX_PTR_ERROR:**(0x07) Ponteiro tampão de retorno inválido
- **GX_INVALID_SIZE:**(0x19) Tamanho do tampão de retorno inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
FILE *fp = GX_NULL;

/* define call back function of how to write the data read from
canvas memory. */

UINT write_data_callback(GX_UBYTE *byte_data, UINT data_count)
{
    if (fp)
    {
        fwrite(byte_data, 1, data_count, fp);
    }
    return GX_SUCCESS;
}

VOID scroll_wheel_screen_draw(GX_WINDOW *window)
{
    UINT status;

    GX_RECTANGLE size = {31,31,610,450};
    gx_window_draw(window);
    if (screenshot)
    {
        fp = fopen("../screenshot.bmp", "wb");
        /* Convert canvas memory to bitmap format.
           Status GX_SUCCESS means operation succeed. */
        status = gx_utility_canvas_to_bmp(root->gx_window_root_canvas,
            &size, write_data_callback);

        fclose(fp);
    }
}
```

### <a name="see-also"></a>Consulte também

- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_circle_point_get"></a>gx_utility_circle_point_get

Calcular ponto num círculo

### <a name="prototype"></a>Prototype

```C
INT gx_utility_circle_point_get(
    INT xCenter, 
    INT yCenter,
    UINT radius, 
    INT angle, 
    GX_POINT *point);
```

### <a name="description"></a>Descrição

Este serviço calcula o ponto num círculo dado o centro do círculo, raio e ângulo.

### <a name="parameters"></a>Parâmetros

- **xCenter**: x coordenada do centro do círculo
- **yCenter**: y coordenada do centro de círculos
- **raio**: Raio de círculo
- **ângulo**: Ângulo para calcular o ponto do perímetro do círculo, em graus
- **ponto**: Endereço de GX_POINT variável para armazenar a coordenada x,y calculada
- **end_alpha**: Fim do valor alfa

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS:**(0x00) Gradiente foi criado
- **GX_PTR_ERROR:**(0x07) Endereço de ponto de retorno inválido
- **GX_INVALID_VALUE:**(0x22) Parâmetro de raio inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_POINT point;
    UINT status;

        status = gx_utility_circle_point_get(100, 100,
20, 45,
&point);

/* If status is GX_SUCCESS the value of point is the x,y coordinate of a point on the circle perimeter at an angle of 45 degrees, where the circle is centered at (100, 100), has a radius of 20 pixels */

```

### <a name="see-also"></a>Consulte também

- gx_utility_ltoa
- gx_utility_math_asin
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_gradient_create"></a>gx_utility_gradient_create

Criar um mapa de pixel gradiente

### <a name="prototype"></a>Prototype

```C
INT gx_utility_gradient_create(
    GX_GRADIENT *gradient,
    GX_VALUE width, 
    GX_VALUE height,
    UCHAR type, 
    GX_UBYTE start_alpha, 
    GX_UBYTE end_alpha);
```

### <a name="description"></a>Descrição

Este serviço cria um mapa de pixels gradiente no tempo de funcionação. Uma imagem de gradiente pode ser usada para realizar efeitos de desvanecimento e outras mudanças visuais interessantes.

A largura e a altura do gradiente solicitado não podem ser inferiores a 2x2 pixels.

O GUIX mantém internamente uma lista de gradientes criados, e esta função procurará primeiro a lista de gradientes para encontrar um pixelmap de gradiente correspondente antes de criar um novo pixelmap. Por outras palavras, o mesmo pixelmap gradiente é necessário várias vezes, apenas um pixelmap é realmente criado, e cada gradiente que requer este pixelmap partilha o pixelmap criado.

Esta API requer que seja definida a função gx_system_memory_allocator para permitir a atribuição de memória em tempo de execução.

As bandeiras do tipo gradiente incluem GX_GRADIENT_TYPE_ALPHA e GX_GRADIENT_TYPE_MIRROR. Apenas GX_GRADIENT_TYPE_ALPHA gradientes do tipo estão atualmente suportados (isto é, esta bandeira do tipo deve ser definida). A bandeira GX_GRADIENT_TYPE_MORROR é opcional, e quando definida instrui a lógica de criação de gradiente para criar um gradiente que muda de start_alpha para end_alpha e de volta para start_alpha. Caso contrário, é criado um gradiente linear.

### <a name="parameters"></a>Parâmetros

- **gradiente**: Ponteiro para estrutura do bloco de controlo de gradiente
- **largura**: Largura de pixelmap solicitada
- **altura**: Altura de pixelmap solicitada
- **tipo**: Tipo de gradiente solicitado
- **start_alpha**: Valor alfa inicial
- **end_alpha**: Fim do valor alfa

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS:**(0x00) Gradiente foi criado
- **GX_INVALID_SIZE**: (0x19) Gradiente não é pelo menos 2x2 pixels
- **GX_NOT_SUPPORTED:**(0x28) Gradiente não é do tipo GX_GRADIENT_TYPE_ALPHA
- **GX_FAILURE**: (0x10) O alocador de memória não está definido ou a atribuição de memória é falhada
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR**: (0x07) Ponteiro gradiente não válido<
- **GX_INVALID_VALUE:**(0x22) O valor de largura e altura não é válido
- **GX_INVALID_TYPE:**(0x1B) Tipo gradiente não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_GRADIENT gradient;

UINT status;

status = gx_utiity_gradient_create(&gradient, 3, 40,
    GX_GRADIENT_TYPE_ALPHA, 240, 0);

/* If status == GX_SUCCESS the gradient pixelmap has been created */
```

### <a name="see-also"></a>Consulte também

- gx_utility_ltoa
- gx_utility_math_asin
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_gradient_delete"></a>gx_utility_gradient_delete

Eliminar um gradiente previamente criado

### <a name="prototype"></a>Prototype

```C
INT gx_utility_gradient_delete(GX_GRADIENT *gradient);
```

### <a name="description"></a>Descrição

Este serviço elimina um gradiente previamente criado. Se o pixelmap associado a este gradiente não for utilizado por outros gradientes, os dados do pixelmap também serão eliminados.

### <a name="parameters"></a>Parâmetros

- **gradiente**: Ponteiro para bloco de controlo de gradiente

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS:**(0x00) Gradiente foi eliminado
- **GX_CALLER_ERROR:**(0x11) Inválido desta função
- **GX_PTR_ERROR**: (0x07) O ponteiro gradiente não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_GRADIENT gradient;

UINT status;

/* Delete previously created gradient. */
status = gx_utility_gradient_delete(&gradient);

/* If status == GX_SUCCESS, the gradient has been deleted. */
```

### <a name="see-also"></a>Consulte também

- gx_utility_ltoa
- gx_utility_math_asin
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_ltoa"></a>gx_utility_ltoa

Converter inteiros longos para ASCII

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_itoa(
    LONG value, 
    GX_CHAR *return_buffer,
    UINT seturn_buffer_size);
```

### <a name="description"></a>Descrição

Este serviço converte um valor inteiro longo numa cadeia ASCII.

### <a name="parameters"></a>Parâmetros

- **valor**: Valor inteiro longo para converter
- **return_buffer**: Tampão de destino para a corda ASCII
- **return_buffer_size**: Tamanho do tampão de destino

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Valor inteiro convertido com sucesso em corda
- **GX_PTR_ERROR:**(0x07) Ponteiro tampão de retorno inválido
- **GX_INVALID_SIZE:**(0x19) Tamanho do tampão de retorno inválido

### <a name="allowed-from"></a>Permitido a partir de

Todos

### <a name="example"></a>Exemplo

```C
INT my_value = 200;

GX_CHAR string_buffer[10];

UINT status;

/* Convert “my_value” into an ASCII string. */
status = gx_utility_ltoa(my_value, string_buffer, 10);

/* If status is GX_SUCCESS, “string_buffer” contains the ASCII
representation of “my_value”. */
```

### <a name="see-also"></a>Consulte também

- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_acos"></a>gx_utility_math_acos

Cosine do arco compute

### <a name="prototype"></a>Prototype

```C
INT gx_utility_math_acos(GX_FIXED_VAL x);
```

### <a name="description"></a>Descrição

Este serviço calcula o valor angular do arco cosine x.

O valor de entrada é um tipo de dado de ponto fixo, chamada GX_FIXED_VAL_MAKE para converter de INT para GX_FIXED_VAL tipo. Por exemplo, se quiser calcular o cosseto de arco de 0,5, faça a entrada como GX_FIXED_VAL_MAKE(1) / 2.

Na versão 5.4.0 ou versão inferior GUIX, o tipo de valor de entrada desta função é INT, e o valor é limitado ao intervalo [-256, 256]. A aplicação deve escalar o valor de intervalo [-1, 1] para intervalo [-256, 256] antes de invocar este serviço. Se o seu projeto com versão GUIX igual ou inferior a 5.4.0 tiver referência a esta API, e pretende atualizar o seu projeto com a mais recente biblioteca guix. Tem duas opções.

1. Corrija o valor de entrada desta chamada API para utilizar GX_FIXED_VAL valor do tipo de dados.
1. Defina GUIX_5_4_0_COMPATIBILITY.

### <a name="parameters"></a>Parâmetros

- **x**: Valor cujo arco cosine é calculado

### <a name="return-values"></a>Valores de devolução

- **ângulo**: Valor angular do arco cosine x

### <a name="allowed-from"></a>Permitido a partir de

Todos

### <a name="example"></a>Exemplo

```C
/* Compute the angle value of arc cosine of “0.5”. */

#if defined(GUIX_5_4_0_COMPATIBILITY)
    x = 256 / 2;
#else
    x = GX_FIXED_VAL_MAKE(1) / 2;
#endif

angle = gx_utility_math_acos(x);

/* “angle” contains the angle value of arc cosine “x”. */
```

### <a name="see-also"></a>Consulte também

- gx_utility_ltoa
- gx_utility_math_asin
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_asin"></a>gx_utility_math_asin

Sine arco compute

### <a name="prototype"></a>Prototype

```C
INT gx_utility_math_asin(GX_FIXED_VAL x);
```

### <a name="description"></a>Descrição

Este serviço calcula o valor angular do arco sine x.

O valor de entrada é um tipo de dado de ponto fixo, chamada GX_FIXED_VAL_MAKE para converter de INT para GX_FIXED_VAL tipo. Por exemplo, se quiser calcular o pecado do arco de 0,5, faça a entrada como GX_FIXED_VAL_MAKE(1) / 2.

Na versão 5.4.0 ou versão inferior GUIX, o tipo de valor de entrada desta função é INT, e o valor é limitado ao intervalo [-256, 256]. A aplicação deve escalar o valor de intervalo [-1, 1] para intervalo [-256, 256] antes de invocar este serviço. Se o seu projeto com versão GUIX for igual ou inferior a 5.4.0, e quiser atualizar o seu projeto com a mais recente biblioteca guix. Tem duas opções.

1. Corrija o valor de entrada desta chamada API para utilizar GX_FIXED_VAL valor do tipo de dados.
1. Defina GUIX_5_4_0_COMPATIBILITY.

### <a name="parameters"></a>Parâmetros

- **x**: Valor cujo arco sine é calculado

### <a name="return-values"></a>Valores de devolução

- **ângulo**: Valor angular do arco sine x

### <a name="allowed-from"></a>Permitido a partir de

Todos

### <a name="example"></a>Exemplo

```C
/* Compute the angle value of arc sine of “x”. */

#if defined GUIX_5_4_0_COMPATIBILITY
    x = 256 / 2;
#else
    X = GX_FIXED_VAL_MAKE(1) / 2;
#endif

angle = gx_utility_math_asin(x);

/* “angle” contains the angle value of arc sine “x”. */
```

### <a name="see-also"></a>Consulte também

- gx_utility_ltoa
- gx_utility_math_acos
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_cos"></a>gx_utility_math_cos

Cosine computacional

### <a name="prototype"></a>Prototype

```C
GX_FIXED_VAL gx_utility_math_cos(GX_FIXED_VAL angle);
```

### <a name="description"></a>Descrição

Este serviço calcula o cosine do ângulo fornecido.

O valor de entrada é um tipo de dado de ponto fixo, chamada GX_FIXED_VAL_MAKE para converter de INT para GX_FIXED_VAL. Por exemplo, se quiser calcular o cosseno de 90 graus, faça a entrada como GX_FIXED_VAL_MAKE(90).

O valor de devolução é um tipo de dado de ponto fixo, chamada GX_FIXED_VAL_TO_INT para converter de GX_FIXED_VAL para INT.

Na versão GUIX da versão 5.4.0 ou versão inferior, o valor de entrada e o valor de retorno deste serviço é INT, o valor de entrada e o valor de retorno são ampliados em 256. E, portanto, a aplicação deve escalar o valor do ângulo em 256 antes de invocar este serviço. Se o seu projeto com versão GUIX for igual ou inferior a 5.4.0, e quiser atualizar o seu projeto com a mais recente biblioteca guix, tem duas opções.

1. Fixar o valor de entrada e o manuseamento ao valor de retorno desta chamada API para utilizar GX_FIXED_VAL valor do tipo data.
1. Defina GUIX_5_4_0_COMPATIBILITY.

### <a name="parameters"></a>Parâmetros

- **ângulo**: Ângulo para calcular o cosseno de

### <a name="return-values"></a>Valores de devolução

- **cosina**: Cosine de ângulo fornecido

### <a name="allowed-from"></a>Permitido a partir de

Todos

### <a name="example"></a>Exemplo

```C
/* Compute cosine of 90 degree. */

INT angle = 90;

#if defined (GUIX_5_4_0_COMPATIBILITY)
    INT scaled_angle = angle << 8;
#else
    GX_FIXED_VAL scaled_angle = GX_FIXED_VAL_MAKE(angle);
#endif

my_angle_cosine = gx_utility_math_cos(scaled_angle);

/* “my_angle_cosine” contains the cosine of “my_angle”. */
```

### <a name="see-also"></a>Consulte também

- gx_utility_ltoa
- gx_utility_math_acos
- gx_utility_math_asin
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_sin"></a>gx_utility_math_sin

Seno computacional

### <a name="prototype"></a>Prototype

```C
GX_FIXED_VAL gx_utility_math_sin(GX_FIXED_VAL angle);
```

### <a name="description"></a>Descrição

Este serviço calcula o seno do ângulo fornecido.

O valor de entrada é um tipo de dado de ponto fixo, chamada GX_FIXED_VAL_MAKE para converter de INT para GX_FIXED_VAL. Por exemplo, se quiser calcular a seno de 90 graus, faça a entrada como GX_FIXED_VAL_MAKE(90). 

O valor de devolução é um tipo de dado de ponto fixo, chamada GX_FIXED_VAL_TO_INT para converter de GX_FIXED_VAL para INT.

Na versão 5.4.0 ou menor GUIX, o valor de entrada e o valor de retorno é INT, o valor de entrada e o valor de retorno são ampliados em 256. E, portanto, a aplicação deve escalar o valor do ângulo em 256 antes de invocar este serviço. Se o seu projeto com versão GUIX for igual ou inferior a 5.4.0, e quiser atualizar o seu projeto com a mais recente biblioteca guix, tem duas opções.

1. Fixar o valor de entrada e a entrega ao valor de retorno desta chamada API para utilizar GX_FIXED_VAL valor do tipo de dados.
1. Defina GUIX_5_4_0_COMPATIBILITY.

### <a name="parameters"></a>Parâmetros

- **ângulo**: Ângulo para calcular sena de

### <a name="return-values"></a>Valores de devolução

- **sine**: Sine de ângulo fornecido

### <a name="allowed-from"></a>Permitido a partir de

Todos

### <a name="example"></a>Exemplo

```C
INT my_angle = 80;

/* Compute sine of “my_angle”. */

#if defined(GUIX_5_4_0_COMPATIBILITY)
    INT scaled_angle = my_angle << 8;
#else
    GX_FIXED_VAL = GX_FIXED_VAL_MAKE(my_angle);
#endif

my_angle_sine = gx_utility_math_sin(scaled_angle);

/* “my_angle_sine” contains the sine of “my_angle”. */
```

### <a name="see-also"></a>Consulte também

- gx_utility_ltoa
- gx_utility_math_acos
- gx_utility_asin
- gx_utility_math_cos
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_sqrt"></a>gx_utility_math_sqrt

Raiz quadrada computacional

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_math_sqrt(UINT value);
```

### <a name="description"></a>Descrição

Este serviço calcula a raiz quadrada do valor fornecido.

### <a name="parameters"></a>Parâmetros

- **valor**: Valor para calcular raiz quadrada de

### <a name="return-values"></a>Valores de devolução

- **raiz quadrada**: Raiz quadrada do valor fornecido

### <a name="allowed-from"></a>Permitido a partir de

Todos

### <a name="example"></a>Exemplo

```C
/* Compute square root of “my_value”. */
my_square_root = gx_utility_math_sqrt(my_value);

/* “my_square_root” contains the square root of “my_value”. */
```

### <a name="see-also"></a>Consulte também

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_bidi_paragraph_reorder"></a>gx_utility_bidi_paragraph_reorder

Reencomendar o texto BiDi na sua ordem de exibição

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_bidi_paragraph_reorder(GX_BIDI_TEXT_INFO *input_info, 
                                       GX_BIDI_RESOLVED_TEXT_INFO **resolved_info_head)
```

### <a name="description"></a>Descrição

Este serviço reencomenda o texto BiDi na sua ordem de exibição. Se o tipo de letra de desenho de texto e a largura do visor forem fornecidos, a rutura da linha será aplicada primeiro, o processo de reordenamento será aplicado com base em cada linha. Se o texto fornecido contiver mais de um parágrafo, o serviço quebrará o texto em parágrafos, o resultado de rutura e reordenamento de cada parágrafo será ligado como uma lista.

### <a name="parameters"></a>Parâmetros

- **input_info**: Ponteir para as informações para quebra de linhas e reordenamento de texto
- **resolved_info_head**: Ponteiro para a lista ligada que contém resultados de rutura de linha e reordenamento de cada parágrafo do texto fornecido

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Reencomenda de textos bidi bem sucedido
- **GX_PTR_ERROR:**(0x07) Ponteiros de entrada inválidos
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) O alocador de memória não está definido ou a atribuição de memória é falhada

### <a name="allowed-from"></a>Permitido a partir de

Todos

### <a name="example"></a>Exemplo
#### <a name="draw-single-line-bidi-text-to-canvas"></a>Desenhe texto bidi de linha única para tela
```C
VOID custom_widget_draw(GX_WIDGET *widget)
{
    GX_BIDI_TEXT_INFO input_info;
    GX_BIDI_RESOLVED_TEXT_INFO *resolved_info;
    GX_CHAR bidi_text[] = "Single Line String";
    
    input_info.gx_bidi_text_info_text.gx_string_ptr = bidi_text;
    input_info.gx_bidi_text_info_text.gx_string_length = sizeof(bidi_text) - 1;
    input_info.gx_bidi_text_info_font = GX_NULL;
    input_info.gx_bidi_text_info_display_width = -1;
    
    /* Reordering BiDi text. */
    status = gx_utility_bidi_paragraph_reorder(&input_info, &resolved_info);
    
    if(status == GX_SUCCESS)
    {
        /* Draw reordered bidi text to canvas. */
        gx_canvas_text_draw_ext(widget->gx_widget_size.gx_rectangle_left,
                                widget->gx_widget_size.gx_rectangle_top,
                                resolved_info.gx_bidi_resolved_text_info_text);

        /* Delete resolved information list. */
        gx_utility_bidi_resolved_text_info_delete(&resolved_info);
    }
}
```
#### <a name="draw-multi-line-bidi-text-to-canvas"></a>Desenhe texto bidi de várias linhas para tela
```C
VOID custom_widget_draw(GX_WIDGET *widget)
{
    GX_BIDI_TEXT_INFO input_info;
    GX_BIDI_RESOLVED_TEXT_INFO *resolved_info;
    GX_CHAR bidi_text[] = "Multi Line BiDi Text Display Example";
    GX_FONT *font;
    GX_RECTANGLE client;
    GX_VALUE display_width;
    INT index;
    GX_VALUE xpos;
    GX_VALUE ypos;
    
    /* Pickup the font. */
    gx_context_font_get(font_id, &font);
    gx_widget_client_get(widget, 2, &client);
    
    display_width = (GX_VALUE)(client.gx_rectangle_right - client.gx_rectangle_left + 1);
    
    input_info.gx_bidi_text_info_text.gx_string_ptr = bidi_text;
    input_info.gx_bidi_text_info_text.gx_string_length = sizeof(bidi_text) - 1;
    input_info.gx_bidi_text_info_font = font;
    input_info.gx_bidi_text_info_display_width = display_width;
    
    /* Reordering BiDi text. */
    status = gx_utility_bidi_paragraph_reorder(&input_info, &resolved_info);
    
    if(status == GX_SUCCESS)
    {
        xpos = client.gx_rectangle_left;
        ypos = client.gx_rectangle_top;
        
        /* Draw reordered bidi text to canvas. */
        for(index = 0; index < resolved_info.gx_bidi_resolved_text_info_total_lines; index++)
        {
            gx_canvas_text_draw_ext(xpos, ypos, &resolved_info.gx_bidi_resolved_text_info_text[index]);
        
            ypos += font->gx_font_line_height;
        }
        
        /* Delete resolved information list. */
        gx_utility_bidi_resolved_text_info_delete(&resolved_info);
    }
}
```

#### <a name="draw-multi-paragraph-bidi-text-to-canvas"></a>Desenhe texto bidi de vários parágrafos para tela
```C
VOID custom_widget_draw(GX_WIDGET *widget)
{
    GX_BIDI_TEXT_INFO input_info;
    GX_BIDI_RESOLVED_TEXT_INFO *resolved_info;
    GX_BIDI_RESOLVED_TEXT_INFO *next;
    GX_CHAR bidi_text[] = "Multi Paragraph\r BiDi Text Display Example";
    GX_FONT *font;
    GX_RECTANGLE client;
    GX_VALUE display_width;
    INT index;
    GX_VALUE xpos;
    GX_VALUE ypos;
    
    /* Pickup the font. */
    gx_context_font_get(font_id, &font);
    gx_widget_client_get(widget, 2, &client);
    
    display_width = (GX_VALUE)(client.gx_rectangle_right - client.gx_rectangle_left + 1);
    
    
    input_info.gx_bidi_text_info_text.gx_string_ptr = bidi_text;
    input_info.gx_bidi_text_info_text.gx_string_length = sizeof(bidi_text) - 1;
    input_info.gx_bidi_text_info_font = font;
    input_info.gx_bidi_text_info_display_width = display_width;
    
    /* Reordering BiDi text. */
    status = gx_utility_bidi_paragraph_reorder(&input_info, &resolved_info);
    
    if(status == GX_SUCCESS)
    {
        xpos = client.gx_rectangle_left;
        ypos = client.gx_rectangle_top;
        
        next = resolved_info;
        
        /* Draw reordered bidi text to canvas. */
        while(next)
        {
            for(index = 0; index < next.gx_bidi_resolved_text_info_total_lines; index++)
            {
                gx_canvas_text_draw_ext(xpos, ypos, &next.gx_bidi_resolved_text_info_text[index]);
            
                ypos += font->gx_font_line_height;
            }
            
            next = next->gx_bidi_resolved_text_info_next;
        }
        
        /* Delete resolved information list. */
        gx_utility_bidi_resolved_text_info_delete(&resolved_info);
    }
}
```

### <a name="see-also"></a>Consulte também

- gx_utility_bidi_resolved_text_info_delete

## <a name="gx_utility_bidi_resolved_text_info_delete"></a>gx_utility_bidi_resolved_text_info_delete

Eliminar lista de informações de texto BiDi resolvidas

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_bidi_resolved_text_info_delete(GX_BIDI_RESOLVED_TEXT_INFO **resolved_info_head)
```

### <a name="description"></a>Descrição

Este serviço elimina a lista de informações resolvidas que foram devolvidas por gx_utility_bidi_paragraph_reorder.

### <a name="parameters"></a>Parâmetros

- **resolved_info_head**: Ponteiro para a lista de informações de texto biDi resolvidas

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Eliminar texto resolvido com sucesso
- **GX_PTR_ERROR:**(0x07) Ponteiros de entrada inválidos
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) O alocador de memória não está definido ou a atribuição de memória é falhada

### <a name="allowed-from"></a>Permitido a partir de

Todos

### <a name="example"></a>Exemplo
```C
VOID custom_widget_draw(GX_WIDGET *widget)
{
    GX_BIDI_TEXT_INFO input_info;
    GX_BIDI_RESOLVED_TEXT_INFO *resolved_info;
    GX_CHAR bidi_text[] = "Single Line String";
    
    input_info.gx_bidi_text_info_text.gx_string_ptr = bidi_text;
    input_info.gx_bidi_text_info_text.gx_string_length = sizeof(bidi_text) - 1;
    input_info.gx_bidi_text_info_font = GX_NULL;
    input_info.gx_bidi_text_info_display_width = -1;
    
    /* Reordering BiDi text. */
    status = gx_utility_bidi_paragraph_reorder(&input_info, &resolved_info);
    
    if(status == GX_SUCCESS)
    {
        /* Draw reordered bidi text to canvas. */
        gx_canvas_text_draw_ext(widget->gx_widget_size.gx_rectangle_left,
                                widget->gx_widget_size.gx_rectangle_top,
                                resolved_info.gx_bidi_resolved_text_info_text);

        /* Delete resolved information list. */
        gx_utility_bidi_resolved_text_info_delete(&resolved_info);
    }
}
```

### <a name="see-also"></a>Consulte também

- gx_utility_bidi_paragraph_reorder

## <a name="gx_utility_pixelmap_resize"></a>gx_utility_pixelmap_resize

Redimensionar pixelmap

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_pixelmap_resize(
    GX_PIXELMAP *src,
    GX_PIXELMAP *destination, 
    INT width, 
    INT height);
```

### <a name="description"></a>Descrição

Este serviço redimensiona um mapa pixel e devolve um ponteiro a um novo mapa pixel, que é o resultado do redimensionar o pixelmap.

Este serviço requer a utilização prévia de gx_system_memory_allocator_set, para permitir a atribuição de memória para reter os dados de pixelmap redimensionados.

### <a name="parameters"></a>Parâmetros

- **src**: Ponter para o mapa de pixels para redimensionar
- **destino**: Tampão de destino para o pixelmap resultante
- **largura**: Largura do mapa pixel resultante, em pixels
- **altura**: Hieght do mapa pixel resultante, em pixels

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Redimensionar o pixelmap com sucesso
- **GX_PTR_ERROR:**(0x07) Ponteiro de pixelmap de origem ou destino inválido
- **GX_INVALID_VALUE:**(0x22) Largura ou valor de altura não válidos
- **GX_NOT_SUPPORTED**: (0x28) O pixelmap de origem é um formato comprimido
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) O alocador de memória não está definido ou a atribuição de memória é falhada

### <a name="allowed-from"></a>Permitido a partir de

Todos

### <a name="example"></a>Exemplo

```C
GX_PIXLEMAP *des_pixelmap;

/* Resize “src_pixelmap” with specifiy width and height. */
status = gx_utility_pixelmap_resize(src_pixelmap,
    &des_pixelmap, 100, 200);

/* If status is GX_SUCCESS. “des_pixelmap” successfully load the
resulting pixelmap of resize. */
```

### <a name="see-also"></a>Consulte também

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift
- gx_canvas_pixelmap_rotate

## <a name="gx_utility_pixelmap_rotate"></a>gx_utility_pixelmap_rotate

Pixelmap rotativo

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_pixelmap_rotate(
    GX_PIXELMAP *src, INT angle,
    GX_PIXELMAP *destination,
    UINT *rot_cx, 
    UINT *rot_cy);
```

### <a name="description"></a>Descrição

Este serviço gira um pixelmap e devolve um ponteiro a um novo mapa pixel, que é o resultado da rotação do pixelmap. Para rodar um mapa de pixels diretamente para a tela, utilize gx_canvas_pixelmap_rotate).).

Este serviço requer a utilização prévia de gx_system_memory_allocator_set, para permitir a atribuição de memória para conter os dados de pixelmap rotativos.

### <a name="parameters"></a>Parâmetros

- **src**: O mapa de pixels para rodar
- **ângulo**: Ângulo de rotação em graus
- **destino**: Tampão de destino para o pixelmap resultante
- **rot_cx**: Recuperado x coordenada do centro de rotação no que diz respeito ao pixelmap de destino. Deve ser iniciado com a coordenada x do centro de rotação no que diz respeito ao pixelmap de origem. Se rot_cx for GX_NULL, o valor não será recuperado.
- **rot_cy**: Recuperado y coordenada do centro de rotação no que diz respeito ao pixelmap de destino. Deve ser iniciado com a coordenada y do centro de rotação no que diz respeito ao pixelmap de origem. Se rot_cy for GX_NULL, o valor não será recuperado.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Rotação de pixels bem sucedido
- **GX_PTR_ERROR:**(0x07) Ponteiro de pixelmap de origem ou destino inválido
- **GX_INVALID_VALUE:**(0x22) O valor do ângulo é 0
- **GX_INVALID_FORMAT**: (0x28) O pixelmap de origem é um formato comprimido, que não é suportado
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) O alocador de memória não está definido ou a atribuição de memória é falhada

### <a name="allowed-from"></a>Permitido a partir de

Todos

### <a name="example"></a>Exemplo

```C
rot_cx = source_rotate_center_x;
rot_cy = source_rotate_center_y;

/* rotate “src_pixelmap” by 30 degree in clockwise direction. */
status = gx_utility_pixelmap_rotate(src_pixelmap, 30,
    &des_pixelmap, &rot_cx, &rot_cy);

/* If status is GX_SUCCESS. “des_pixelmap” successfully load the
resulting pixelmap of rotation. */
```

### <a name="see-also"></a>Consulte também

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift
- gx_canvas_pixelmap_rotate

## <a name="gx_utility_pixelmap_simple_rotate"></a>gx_utility_pixelmap_simple_rotate

Pixelmap rotativo

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_pixelmap_simple_rotate(
    GX_PIXELMAP *src,
    INT angle,
    GX_PIXELMAP *destination,
    UINT *rot_cx,
    UINT *rot_cy);
```

### <a name="description"></a>Descrição

Este serviço gira um mapa de pixels em 90 graus, 180 graus ou 270 graus.

### <a name="parameters"></a>Parâmetros

- **src**: O mapa de pixels para rodar
- **ângulo**: Ângulo de rotação em graus
- **destino**: Tampão de destino para o pixelmap resultante
- **rot_cx**: Recuperado x coordenada do centro de rotação no que diz respeito ao pixelmap de destino. Deve ser iniciado com a coordenada x do centro de rotação no que diz respeito ao pixelmap de origem. Se rot_cx for GX_NULL, o valor não será recuperado.
**rot_cy**: Recuperado y coordenada do centro de rotação no que diz respeito ao pixelmap de destino. Deve ser iniciado com a coordenada y do centro de rotação no que diz respeito ao pixelmap de origem. Se rot_cy for GX_NULL, o valor não será recuperado.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Rotação de pixels bem sucedido
- **GX_PTR_ERROR:**(0x07) Ponteiro de pixelmap de origem ou destino inválido
- **GX_INVALID_VALUE:**(0x22) O valor do ângulo é 0 ou não um ângulo simples como 90, 180, 270
- **GX_INVALID_FORMAT**: (0x28) O pixelmap de origem é um formato comprimido, que não é suportado
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) O alocador de memória não está definido ou a atribuição de memória é falhada

### <a name="allowed-from"></a>Permitido a partir de

Todos

### <a name="example"></a>Exemplo

```C
rot_cx = source_rotate_center_x;
rot_cy = source_rotate_center_y;

/* rotate “src_pixelmap” by 90 degree in clockwise direction. */
status = gx_utility_pixelmap_simple_rotate(src_pixelmap, 90,
    &des_pixelmap,
    &rot_cx, &rot_cy);

/* If status is GX_SUCCESS. “des_pixelmap” successfully load the
resulting pixelmap of rotation. */
```

### <a name="see-also"></a>Consulte também

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_center"></a>gx_utility_rectangle_center

Retângulo central dentro de outro retângulo

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_rectangle_center(
    GX_RECTANGLE *rectangle,
    GX_RECTANGLE *within_rectangle);
```

### <a name="description"></a>Descrição

Este serviço centra o retângulo dentro de outro retângulo.

### <a name="parameters"></a>Parâmetros

- **retângulo**: Retângulo ao centro
- **within_rectangle**: Retângulo para o centro

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Centrado com sucesso no retângulo
- **GX_PTR_ERROR**: (0x07) Ponteiro de retângulo de entrada inválido
- **GX_INVALID_SIZE:**(0x19) Tamanho do retângulo inválido

### <a name="allowed-from"></a>Permitido a partir de

Todos

### <a name="example"></a>Exemplo

```C
UINT status;

/* Center “my_inner_rectangle” inside of “my_outer_rectangle”.*/
status = gx_utility_rectangle_center(&my_inner_rectangle,
    &my_outer_rectangle);

/* Is status is GX_SUCCESS, “my_inner_rectangle” is centered
within “my_other_rectangle”. */
```

### <a name="see-also"></a>Consulte também

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_center_find"></a>gx_utility_rectangle_center_find

Encontre o centro do retângulo

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_rectangle_center_find(
    GX_RECTANGLE *rectangle,
    GX_POINT *return_center);
```

### <a name="description"></a>Descrição

Este serviço encontra o centro do retângulo.

### <a name="parameters"></a>Parâmetros

- **retângulo**: Retângulo
- **return_center**: Ponte para o centro

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS:**(0x00) Encontrou com sucesso o centro do retângulo
- **GX_PTR_ERROR:**(0x07) Ponteiro de entrada inválido
- **GX_INVALID_SIZE:**(0x19) Tamanho do retângulo inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
UINT status;

GX_RECTANGLE my_rectangle;

GX_POINT my_center_point;

gx_utility_define(&my_rectangle, 0, 0, 100, 100);

/* Find center of “my_rectangle””. */

status = gx_utility_rectangle_center_find(&my_rectangle,
    &my_center_point);

/* If status is GX_SUCCESS, “my_center_point” is the center point
of “my_rectangle” (50, 50). */
```

### <a name="see-also"></a>Consulte também

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_combine"></a>gx_utility_rectangle_combine

Combine dois retângulos em primeiro

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_rectangle_combine(
    GX_RECTANGLE *first_rectangle,
    GX_RECTANGLE *second_rectangle);
```

### <a name="description"></a>Descrição

Este serviço combina o primeiro e o segundo retângulo no primeiro retângulo. O primeiro retângulo é expandido para incluir o segundo.

### <a name="parameters"></a>Parâmetros

- **first_rectangle**: Primeiro retângulo e retângulo combinado
- **second_rectangle**: Segundo retângulo

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS:**(0x00) Combinou com sucesso dois retângulos
- **GX_PTR_ERROR:**(0x07) Ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
UINT status;

GX_RECTANGLE rect_a;

GX_RECTANGLE rect_b;

gx_utility_rectangle_define(&rect_a, 0, 0, 100, 100);
gx_utility_rectangle_define(&rect_b, 50, 50, 200, 200);

/* Combine “my_rectangle_a” to “my_rectangle_b”. */
status = gx_utility_rectangle_combine(&rect_a, &rect_b);

/* If status is GX_SUCCESS, “rect_a” is (0, 0, 200, 200) the merger
of the original “rect_a” and “rect_b”. */
```

### <a name="see-also"></a>Consulte também

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_compare"></a>gx_utility_rectangle_compare

Compare dois retângulos

### <a name="prototype"></a>Prototype

```C
GX_BOOL gx_utility_rectangle_compare( 
    GX_RECTANGLE *first_rectangle,
    GX_RECTANGLE *second_rectangle);
```

### <a name="description"></a>Descrição

Este serviço compara o primeiro e o segundo retângulo. Se forem iguais, o valor da GX_TRUE é devolvido.

### <a name="parameters"></a>Parâmetros

- **first_rectangle**: Primeiro retângulo
- **second_rectangle**: Segundo retângulo

### <a name="return-values"></a>Valores de devolução

- **resultado**: GX_TRUE se os retângulos forem iguais, caso contrário GX_FALSE é devolvido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Compare “my_rectangle_a” to “my_rectangle_b”. */
result = gx_utility_rectangle_compare(&my_rectangle_a,
    &my_rectangle_b);

/* If result is GX_TRUE, the two rectangles are equal. */
```

### <a name="see-also"></a>Consulte também

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_define"></a>gx_utility_rectangle_define

Defina um retângulo

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_rectangle_define(
    GX_RECTANGLE *rectangle,
    GX_VALUE left,
    GX_VALUE top, 
    GX_VALUE right, 
    GX_VALUE bottom);
```

### <a name="description"></a>Descrição

Este serviço define um retângulo conforme especificado.

### <a name="parameters"></a>Parâmetros

- **retângulo**: Bloco de controlo do retângulo
- **esquerda**: Esquerda mais coordenada
- **top**: Top mais coordenada
- **direito**: A maioria das coordenadas da direita
- **fundo**: Parte inferior da coordenada

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS:**(0x00) Definiu com sucesso um retângulo
- **GX_PTR_ERROR:**(0x07) Ponteiro de retângulo inválido

### <a name="allowed-from"></a>Permitido a partir de

Todos

### <a name="example"></a>Exemplo

```C
UINT status;

GX_RECTANGLE my_rect;

/* Define “my_rect”. */

status = gx_utility_rectangle_define(&my_rect, 10, 5, 200, 100);

/* If status is GX_SUCCESS, “my_rect” is defined. */
```

### <a name="see-also"></a>Consulte também

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_overlap_detect"></a>gx_utility_rectangle_overlap_detect

Detetar sobreposição de retângulos

### <a name="prototype"></a>Prototype

```C
GX_BOOL gx_utility_rectangle_overlap_detect(
    GX_RECTANGLE *first_rectangle,
    GX_RECTANGLE *second_rectangle,
    GX_RECTANGLE *return_overlap_area);
```

### <a name="description"></a>Descrição

Este serviço deteta qualquer sobreposição dos retângulos fornecidos. Se for encontrada sobreposição, o serviço devolve GX_TRUE e o retângulo sobreposto.

### <a name="parameters"></a>Parâmetros

- **first_rectangle**: Primeiro retângulo
- **second_rectangle**: Segundo retângulo
- **return_overlap_area**: Área de retângulo sobreposto

### <a name="return-values"></a>Valores de devolução

- **resultado**: GX_TRUE se os retângulos se sobrepõem, caso contrário GX_FALSE.

### <a name="allowed-from"></a>Permitido a partir de

Todos

### <a name="example"></a>Exemplo

```C
/* Detect overlap of “my_rectangle_a” and “my_rectangle_b”. */
result = gx_utility_rectangle_overlap_detect(&my_rectangle_a,
    &my_rectangle_b,
    &my_overlap_area);

/* If result is GX_TRUE, “my_overlap_area” specifies the area the
rectangles overlap. */
```

### <a name="see-also"></a>Consulte também

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_point_detect"></a>gx_utility_rectangle_point_detect

Detetar se o ponto reside no retângulo

### <a name="prototype"></a>Prototype

```C
GX_BOOL gx_utility_rectangle_point_detect(
    GX_RECTANGLE *rectangle,
    GX_POINT point);
```

### <a name="description"></a>Descrição

Este serviço deteta se o ponto especificado reside no retângulo. Se o ponto residir no retângulo, o serviço devolve-GX_TRUE.

### <a name="parameters"></a>Parâmetros

- **retângulo**: Retângulo
- **ponto**: Ponto

### <a name="return-values"></a>Valores de devolução

- **resultado**: GX_TRUE se o ponto residir no retângulo, caso contrário GX_FALSE

### <a name="allowed-from"></a>Permitido a partir de

Todos

### <a name="example"></a>Exemplo

```c
GX_RECTANGLE my_rectangle;

GX_POINT my_point;

gx_utility_rectangle_define(&my_rectangle, 0, 0, 100, 100);

my_point.gx_point_x = 20; my_point.gx_point_y = 20;

/* Detect if point “my_point” is within “my_rectangle””. */
result = gx_utility_rectangle_point_detect(&my_rectangle,
    &my_point);

/* If result is GX_TRUE, “my_point” resides in the rectangle. */
```

### <a name="see-also"></a>Consulte também

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_resize"></a>gx_utility_rectangle_resize

Crescer retângulo

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_rectangle_resize(
    GX_RECTANGLE *rectangle,
    GX_VALUE adjust);
```

### <a name="description"></a>Descrição

Este serviço aumenta o tamanho do retângulo conforme especificado.

### <a name="parameters"></a>Parâmetros

- **retângulo**: Ponteiro para retângulo
- **ajustar**: Montante para ajustar o retângulo

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Redimensionou com sucesso o retângulo
- **GX_PTR_ERROR**: (0x07) Ponteiro de retângulo de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Todos

### <a name="example"></a>Exemplo

```C
UINT status;

/* Adjust “my_rectangle” by increasing 20 pixels on four sides */
status = gx_utility_rectangle_resize(&my_rectangle, 20);

/* If status is GX_SUCCESS, “my_rectangle” is 20 pixels larger. */
```

### <a name="see-also"></a>Consulte também

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_shift"></a>gx_utility_rectangle_shift

Retângulo de mudança

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_rectangle_shift(
    GX_RECTANGLE *rectangle,
    GX_VALUE x_shift,
    GX_VALUE y_shift);
```

### <a name="description"></a>Descrição

Este serviço desloca o retângulo pelos valores especificados.

### <a name="parameters"></a>Parâmetros

- **retângulo**: Retângulo para deslocar
- **x_shif**: Número de pixéis a deslocar-se no eixo x
- **y_shift**: Número de pixéis a deslocar-se no eixo y

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Deslocou com sucesso o retângulo
- **GX_PTR_ERROR**: (0x07) Ponteiro de retângulo de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Todos

### <a name="example"></a>Exemplo

```C
UINT status;

/* Shift “my_rectangle”. */

status = gx_utility_rectangle_shift(&my_rectangle, 10, 20);

/* If status is GX_SUCCESS, “my_rectangle” has been shifted. */
```

### <a name="see-also"></a>Consulte também

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect

## <a name="gx_utility_string_to_alphamap"></a>gx_utility_string_to_alphamap

Renderização de cadeia a um pixelmap do tipo alfamap de 8bpp (precotado)

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_string_to_alphamap(
    const GX_CHAR *text, const
    GX_FONT *font, 
    GX_PIXELMAP *return_map);
```

### <a name="description"></a>Descrição

Este serviço foi prevadido a favor de gx_utility_string_to_alphamap_ext().

Este serviço torna uma cadeia de texto para um mapa alfa, que é uma forma especial de pixelmap de 8bpp contendo apenas valores alfa. Este serviço é normalmente utilizado juntamente com gx_utility_pixelmap_rotate e gx_canvas_pixelmap_draw para desenhar texto rotativo para a tela.

Este serviço calcula o tamanho da memória necessária para o mapa alfa resultante e invoca a função gx_system_memory_allocator definida pela aplicação para alocar dinamicamente a memória. A aplicação deve ligar para gx_system_memory_allocator_set() em algum momento, geralmente durante o arranque do programa, antes de usar este serviço.

Se uma cadeia de texto for rodada e atraída para a tela apenas uma vez, o serviço gx_canvas_rotated_text_draw() é fornecido como um suplente. gx_canvas_rotated_text_draw() chamará gx_utility_string_to_alphamap gx_utility_pixelmap_rotate e gx_canvas_pixelmap_draw() para tornar o texto rotativo numa única operação. No entanto, se o mesmo texto for desenhado várias vezes rodado em vários ângulos, é mais eficiente criar o mapa alfa uma vez que utilize a API gx_utility_string_to_alphmap e, em seguida, rode o mapa alfa resultante várias vezes conforme necessário.

### <a name="parameters"></a>Parâmetros

- **texto**: Cadeia de texto para renderizar à alfamap
- **fonte**: O tipo de letra a ser para renderizar o texto
- **return_map**: Ponter para o GX_PIXELMAP ser devolvido ao chamador.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Com sucesso, tornou uma cadeia de texto num mapa alfa
- **GX_PTR_ERROR:**(0x07) Ponteiro de entrada inválido
- **GX_SYSTEM_MEMORY_ERROR:**(0x30) A atribuição de memória/função livre não está definida
- **GX_INVALID_STRING_LENGTH:**(0x34) Comprimento da corda inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_PIXELMAP alphamap;

GX_PIXELMAP rotated_text;

INT xpos;

INT ypos;

gx_widget_font_get(widget, GX_FONT_ID_SCREEN_LABEL, &font);

/* render string to alphamap once */

gx_utility_string_to_alphamap("Hello World", font, &alphamap);

/* rotate and render the alphmap at multiple angles */

gx_utility_pixelmap_rotate(&alphamap, 45, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(10, 10, &rotated_text);

gx_utility_pixelmap_rotate(&alphamap, 135, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(100, 100, &rotated_text);

gx_utility_pixelmap_rotate(&alphamap, 300, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(200, 200, &rotated_text);
```

### <a name="see-also"></a>Consulte também

- gx_utility_string_to_alphamap_ext

## <a name="gx_utility_string_to_alphamap_ext"></a>gx_utility_string_to_alphamap_ext

Rendereia a corda a um pixelmap do tipo alfamap de 8bpp

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_string_to_alphamap_ext(
    GX_CONST GX_STRING *string,
    GX_CONST GX_FONT *font, 
    GX_PIXELMAP *return_map);
```

### <a name="description"></a>Descrição

Este serviço torna uma cadeia de texto para um mapa alfa, que é uma forma especial de pixelmap de 8bpp contendo apenas valores alfa. Este serviço é normalmente utilizado juntamente com gx_utility_pixelmap_rotate e gx_canvas_pixelmap_draw para desenhar texto rotativo para a tela.

Este serviço calcula o tamanho da memória necessária para o mapa alfa resultante e invoca a função gx_system_memory_allocator definida pela aplicação para alocar dinamicamente a memória. A aplicação deve ligar para gx_system_memory_allocator_set() em algum momento, geralmente durante o arranque do programa, antes de usar este serviço.

Se uma cadeia de texto for rodada e atraída para a tela apenas uma vez, o serviço gx_canvas_rotated_text_draw() é fornecido como um suplente. gx_canvas_rotated_text_draw() chamará gx_utility_string_to_alphamap gx_utility_pixelmap_rotate e gx_canvas_pixelmap_draw() para tornar o texto rotativo numa única operação. No entanto, se o mesmo texto for desenhado várias vezes rodado em vários ângulos, é mais eficiente criar o mapa alfa uma vez que utilize a API gx_utility_string_to_alphmap e, em seguida, rode o mapa alfa resultante várias vezes conforme necessário.

### <a name="parameters"></a>Parâmetros

- **string**: Cadeia de texto para renderizar para alfamap
- **fonte**: O tipo de letra a ser para renderizar o texto
- **return_map**: Ponter para o GX_PIXELMAP ser devolvido ao chamador.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS**: (0x00) Com sucesso, tornou uma cadeia de texto num mapa alfa
- **GX_PTR_ERROR:**(0x07) Ponteiro de entrada inválido
- **GX_SYSTEM_MEMORY_ERROR:**(0x30) A atribuição de memória/função livre não está definida
- **GX_INVALID_STRING_LENGTH:**(0x34) Comprimento da corda inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_STRING string;

GX_PIXELMAP alphamap;

GX_PIXELMAP rotated_text;

INT xpos;

INT ypos;

gx_widget_font_get(widget, GX_FONT_ID_SCREEN_LABEL, &font);

string.gx_string_ptr = “Hello World”;

string.gx_string_length = strlen(string.gx_string_ptr);

/* render string to alphamap once */
gx_utility_string_to_alphamap_ext(&string, font, &alphamap);

/* rotate and render the alphmap at multiple angles */
gx_utility_pixelmap_rotate(&alphamap, 45, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(10, 10, &rotated_text);

gx_utility_pixelmap_rotate(&alphamap, 135, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(100, 100, &rotated_text);

gx_utility_pixelmap_rotate(&alphamap, 300, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(200, 200, &rotated_text);
```

### <a name="see-also"></a>Consulte também

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect

## <a name="gx_vertical_list_children_position"></a>gx_vertical_list_children_position
### <a name="position-children-for-the-vertical-list"></a>Posicione as crianças para a lista vertical

### <a name="prototype"></a>Prototype

```C
UINT gx_vertical_list_children_position(
    GX_VERTICAL_LIST *vertical_list)
```

### <a name="description"></a>Descrição

Esta função posiciona as crianças para a lista vertical.

### <a name="parameters"></a>Parâmetros

- **vertical_list** Ponteiro para o bloco de controlo da lista vertical

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) posicionou com sucesso as crianças para a lista vertical
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Position children in the vertical list */
status = gx_vertical_list_children_position (&vertical_list);

/* If status is GX_SUCCESS the children in the vertical list are positioned.. */
```

### <a name="see-also"></a>Consulte também

- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selecgted_widget_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_create"></a>gx_vertical_list_create
### <a name="create-vertical-list"></a>Criar lista vertical

### <a name="prototype"></a>Prototype

```C
UINT gx_vertical_list_create(
    GX_VERTICAL_LIST *vertical_list,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent, 
    INT total_rows,
    VOID (*callback)(GX_VERTICAL_LIST *, GX_WIDGET *, INT),
    ULONG style, USHORT vertical_list_id,
    GX_CONST GX_RECTANGLE *size);
```
### <a name="description"></a>Descrição

Este serviço cria uma lista vertical.

GX_VERTICAL_LIST é derivado de GX_WINDOW e suporta todos os serviços gx_window API.

### <a name="parameters"></a>Parâmetros

- **vertical_list** Bloco de controlo widget de lista vertical
- **nome** Nome da lista vertical
- **pai** Ponteiro para widget dos pais
- **total_rows** Número total de linhas na lista vertical
- **callback** Uma função que será chamada pela lista vertical quando a lista for percorrida. O chamador deve inicialmente criar GX_WIDGET crianças suficientes para preencher as filas de listas visíveis. À medida que a lista é percorrida, esta função é chamada a recriar a lista de crianças correspondentes ao índice de lista fornecido
- **estilo** Estilo de widget de barra de rolo. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **vertical_list_id** ID definido pela aplicação da lista vertical
- **tamanho** Dimensões da lista vertical

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) criou com sucesso a lista vertical
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido
- **GX_INVALID_VALUE** (0x22) Número de linhas não válidas
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Create vertical list “my_list” with 20 rows. */
status = gx_vertical_list_create(&my_list, “my_list”, &my_parent,
                    20, callback, GX_STYLE_WRAP, MY_LIST_ID,
                    &size);

/* If status is GX_SUCCESS the vertical list “my_list” has been created. */
```

### <a name="see-also"></a>Consulte também

- gx_vertical_list_children_position
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_event_process"></a>gx_vertical_list_event_process
### <a name="process-vertical-list-event"></a>Evento de lista vertical de processo

### <a name="prototype"></a>Prototype

```C
UINT gx_vertical_list_event_process(GX_VERTICAL_LIST *list,
                                                      GX_EVENT *event);
```

### <a name="description"></a>Descrição

Este serviço processa um evento para a lista vertical.

### <a name="parameters"></a>Parâmetros

- **lista** Bloco de controlo widget de lista vertical
- **evento** Ponteiro para o evento para processar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) processou com sucesso o evento da lista vertical
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Process “my_event” for vertical list “my_list”. */
status = gx_vertical_list_event_process(&my_list, &my_event);

/* If status is GX_SUCCESS the event for vertical list “my_list” has been processed. */
```

### <a name="see-also"></a>Consulte também

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_selected_set

## <a name="gx_vertical_list_page_index_set"></a>gx_vertical_list_page_index_set
### <a name="set-starting-page-index"></a>Definir índice de página inicial

### <a name="prototype"></a>Prototype

```C
UINT gx_vertical_list_page_index_set(
    GX_VERTICAL_LIST *list,
    INT index);
```
### <a name="description"></a>Descrição

Este serviço define o índice inicial para a lista vertical.

### <a name="parameters"></a>Parâmetros

- **lista** Bloco de controlo widget de lista vertical
- **índice** O novo índice superior

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso o índice de página inicial para a lista vertical
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro widget inválido
- **GX_INVALID_VALUE** (0x22) Valor do índice inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the starting page index of vertical list “my_list” to 4. */
status = gx_vertical_list_page_index_set(&my_list, 4);

/* If status is GX_SUCCESS the starting page index of “my_list” has
been set to 4. */
```
### <a name="see-also"></a>Consulte também

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_selected_index_get"></a>gx_vertical_list_selected_index_get
### <a name="get-selected-index-from-vertical-list"></a>Obtenha o índice selecionado da lista vertical

### <a name="prototype"></a>Prototype

```C
UINT gx_vertical_list_selected_index_get(
    GX_VERTICAL_LIST *vertical_list,
    INT *return_index);
```
### <a name="description"></a>Descrição

Este serviço devolve o índice selecionado da lista vertical

### <a name="parameters"></a>Parâmetros

- **vertical_list** Bloco de controlo widget de lista vertical
- **return_index** Destino para devolução do índice selecionado

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) obtenha com sucesso a entrada na lista vertical
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
INT current_selected_index;

/* Get the list entry at the current index of vertical list “my_list”. */
status = gx_vertical_list_selected_index_get(&my_list, &current_selected_index);

/* If status is GX_SUCCESS, “current_list_index” contains the index of the selected list item. */
```
### <a name="see-also"></a>Consulte também

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_selected_set"></a>gx_vertical_list_selected_set
### <a name="assign-the-selected-entry-in-a-vertical-list"></a>Atribua a entrada selecionada numa lista vertical

### <a name="prototype"></a>Prototype

```C
UINT gx_vertical_list_selected_set(
    GX_VERTICAL_LIST *vertical_list,
    INT index);
```

### <a name="description"></a>Descrição

Este serviço atribui a inscrição selecionada numa lista vertical. Se necessário, a lista vertical deslocar-se-á para tornar visível a entrada selecionada.

### <a name="parameters"></a>Parâmetros

- **vertical_list** Bloco de controlo widget de lista vertical
- **índice** Posição baseada no índice da entrada de nova lista

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso a entrada da lista vertical
- **GX_FAILURE** (0x10) Índice de entrada não encontrado na lista
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_WIDGET** (0x12) Lista vertical ou widget de entrada de lista não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the list entry of “my_list” to the child in line 12. */
status = gx_vertical_list_selected_set(&my_list, 12);

/* If status is GX_SUCCESS, the list entry of “my_list” has been successfully set to 12. */
```
### <a name="see-also"></a>Consulte também

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_get
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_selected_widget_get"></a>gx_vertical_list_selected_widget_get
### <a name="get-selected-widget-from-vertical-list"></a>Obtenha widget selecionado da lista vertical

### <a name="prototype"></a>Prototype

```C
UINT gx_vertical_list_selected_widget_get(
    GX_VERTICAL_LIST *vertical_list,
    GX_WIDGET **return_list_entry);
```
### <a name="description"></a>Descrição

Este serviço devolve o widget selecionado da lista vertical. Note que se a lista contiver mais linhas do que widgets infantis, e o widget para crianças selecionados tiver sido deslocalizado da vista, esta função voltará GX_NULL como ponteiro GX_WIDGET, uma vez que o widget foi reutilizado para apresentar uma nova entrada de lista.

### <a name="parameters"></a>Parâmetros

- **vertical_list** Bloco de controlo widget de lista vertical
- **return_list_entry** Destino para widget de entrada na lista de devolução

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) obtenha com sucesso a entrada na lista vertical
- **GX_FAILURE** (0x10) O widget selecionado foi deslocalizado da vista.
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_WIDGET *current_selected_widget;

/* Get the list entry at the current index of vertical list “my_list”. */
status = gx_vertical_list_selected_widget_get(&my_list, &current_selected_widget);

/* If status is GX_SUCCESS, “current_list_entry” contains a pointer to the currently selected widget. */
```

### <a name="see-also"></a>Consulte também

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_total_rows_set"></a>gx_vertical_list_total_rows_set
### <a name="set-total-number-of-vertical-list-rows"></a>Definir número total de linhas de listas verticais

### <a name="prototype"></a>Prototype

```C
UINT gx_vertical_list_total_rows_set(
    GX_VERTICAL_LIST *vertical_list,
    INT count);
```
### <a name="description"></a>Descrição

Este serviço atribui ou altera o número total de linhas de lista.

### <a name="parameters"></a>Parâmetros

- **vertical_list** Bloco de controlo widget de lista vertical
- **contar** Contagem de linhas de nova lista

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso a contagem de filas de listas verticais
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido
- **GX_INVALID_VALUE** (0x22) Valor da contagem de linha não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set the list row count to 20 items. */
status = gx_vertical_list_total_rows_set(&my_list, 20);

/* If status is GX_SUCCESS, the total rows of “my_list” has been set to 20. */
```
### <a name="see-also"></a>Consulte também

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set

## <a name="gx_vertical_scrollbar_create"></a>gx_vertical_scrollbar_create
### <a name="create-vertical-scrollbar"></a>Criar barra de deslocação vertical

### <a name="prototype"></a>Prototype

```C
UINT gx_vertical_scrollbar_create(
    GX_SCROLLBAR *scrollbar,
    GX_CONST GX_CHAR *name, 
    GX_WINDOW *parent,
    GX_SCROLLBAR_APPEARANCE *appearance,
    ULONG style);
```
### <a name="description"></a>Descrição

Este serviço cria uma barra de deslocação vertical.

### <a name="parameters"></a>Parâmetros

- **barra de scroll** Bloco de controlo widget de barra de rolo
- **nome** Nome da barra de pergaminho
- **pai** Ponteiro para widget dos pais
- **aparência** Aparência do widget vertical da barra de rolo.
- **estilo** Estilo da barra de pergaminho.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Barra de deslocação vertical bem sucedida criar
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido
- **GX_INVALID_WIDGET** (0x12) Widget dos pais não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Create vertical scrollbar “my_scrollbar”. */
status = gx_vertical_scrollbar_create(&my_scrollbar,
                          “my_vertical_scrollbar”,
                          &my_parent, &scrollbar_appearance,
                          GX_STYLE_ENABLED);

/* If status is GX_SUCCESS the vertical scrollbar “my_scrollbar” has been created. */
```
### <a name="see-also"></a>Consulte também

- gx_horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_event_process
- gx_scrollbar_limit_check
- gx_scrollbar_reset

## <a name="gx_widget_allocate"></a>gx_widget_allocate
### <a name="allocate-a-widget-control-block"></a>Alocar um bloco de controlo widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_allocate(
    GX_WIDGET **control_block,
    ULONG memsize);
```
### <a name="description"></a>Descrição

Este serviço atribui dinamicamente um bloco de controlo widget, chamando a função de atribuição de memória definida pela aplicação. Este serviço é usado principalmente pelas funções geradas pelo GUIX Studio para alocar dinamicamente o bloco de controlo quando a propriedade "Dynamic Allocation" é selecionada na vista de propriedades do GUIX Studio.

### <a name="parameters"></a>Parâmetros

- **control_block** Ponteiro para devolver ponteiro do bloco de controlo
- **memsize** Tamanho do bloco de controlo, em bytes

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Alocado widget bem sucedido
- **GX_SYSTEM_MEMORY_ERROR** (0x30) O alocador de memória não está definido ou a atribuição de memória falhou
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_MEMORY_SIZE** (0x29) Tamanho da memória não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_TEXT_BUTTON *button;

/* Attach “my_widget” to “my_parent”. */
status = gx_widget_allocate(&button, sizeof(GX_TEXT_BUTTON));

/* If status is GX_SUCCESS the button widget control block is allocated. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_attach"></a>gx_widget_attach
### <a name="attach-widget-to-its-parent"></a>Anexar widget ao seu progenitor

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_attach(
    GX_WIDGET *parent, 
    GX_WIDGET *widget);
```
### <a name="description"></a>Descrição

Este serviço anexa o widget ao progenitor especificado. Se o widget já estiver ligado a outro progenitor, é primeiro destacado. Se o widget já estiver ligado ao mesmo progenitor, a função não faz nada.

O widget torna-se o filho mais frontal do seu progenitor em termos de pedidos de z. Se os widgets irmãos se sobrepõem, este widget é desenhado em cima de irmãos. Para colocar o novo widget na parte de trás da ordem z, use gx_widget_back_attach ou gx_widget_back_move.

### <a name="parameters"></a>Parâmetros

- **pai** Ponteiro para widget dos pais
- **widget** Ponteiro para widget infantil

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Widget attach
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_WIDGET** (0x12) Pai ou widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Attach “my_widget” to “my_parent”. */
status = gx_widget_attach(&my_parent, &my_widget);

/* If status is GX_SUCCESS the widget “my_widget” is attached to “my_parent”. */
```

### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_background_draw"></a>gx_widget_background_draw
### <a name="draw-a-widget-background"></a>Desenhe um fundo widget

### <a name="prototype"></a>Prototype

```C
VOID gx_widget_background_draw(GX_WIDGET *widget);
```
### <a name="description"></a>Descrição

Este serviço executa um preenchimento de cor sólida de um fundo widget. Este serviço é automaticamente chamado pela função gx_widget_draw, mas também pode ser invocado pela aplicação como parte de uma função de desenho de widget personalizado.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget a ser desenhado

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom widget draw function. */

VOID my_widget_draw(GX_WIDGET * widget)
{
    /* Call default widget background draw. */
    gx_widget_background_draw(widget);

    /* Add your own drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw(widget);
}
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_back_attach"></a>gx_widget_back_attach
### <a name="attach-widget-to-its-parent"></a>Anexar widget ao seu progenitor

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_back_attach(
    GX_WIDGET *parent, 
    GX_WIDGET *widget);
```
### <a name="description"></a>Descrição

Este serviço anexa o widget ao progenitor especificado. Se o widget já estiver ligado a outro progenitor, é primeiro destacado. Se o widget já estiver ligado ao mesmo progenitor, a função não faz nada.

O widget torna-se o filho mais atrasado do seu progenitor em termos de pedidos de z. Se os widgets irmãos se sobrepõem, este widget é desenhado atrás desses irmãos. Para colocar o novo widget na frente da ordem z, use gx_widget_attach ou gx_widget_front_move.

### <a name="parameters"></a>Parâmetros

- **pai** Ponteiro para widget dos pais
- **widget** Ponteiro para widget infantil

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Widget attach
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_WIDGET** (0x12) Pai ou widget não válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Attach “my_widget” to “my_parent”. */
status = gx_widget_back_attach(&my_parent, &my_widget);

/* If status is GX_SUCCESS the widget “my_widget” is attached to “my_parent”. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_back_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_back_move"></a>gx_widget_back_move
### <a name="move-widget-to-back"></a>Mova o widget para trás

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_back_move(
    GX_WIDGET *widget,
    GX_BOOL *return_widget_moved);
```
### <a name="description"></a>Descrição

Este serviço move o widget para trás na ordem Z dos widgets infantis dos pais.

### <a name="parameters"></a>Parâmetros

- **pai** Ponteiro para widget dos pais
- **return_widget_moved** Ponteiro para destino para bandeira indicando que o widget foi movido

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Widget bem sucedido move-se para trás
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_NO_CHANGE** (0x08) Não são aplicadas alterações
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Move “my_widget” to the back. */
status = gx_widget_back_move(&my_widget, &moved_flag);

/* If status is GX_SUCCESS and “moved_flag” is GX_TRUE, the widget “my_widget” was moved to the back. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_block_move"></a>gx_widget_block_move
### <a name="move-a-rectangular-block-of-pixels"></a>Mova um bloco retangular de pixéis

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_block_move(
    GX_WIDGET *widget,
    GX_RECTANGLE *block,
    INT xshift, INT yshift);
```

### <a name="description"></a>Descrição

Este serviço move um bloco retangular de pixéis. Este serviço é mais utilizado para implementar deslocamento rápido.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget solicitando movimento de bloco
- **bloco** Bloco de delimitação de retângulos para se mover
- **xshift** A quantidade de x mudança em pixels
- **yshift** A quantidade de mudança y em pixels

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Widget bem sucedido move-se para trás
- **GX_INVALID_CANVAS** (0x20) tela widget não encontrada
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Move a block of pixels 20 pixels to the right. */
status = gx_widget_block_move(&my_widget, &size, 20, 0);

/* If status is GX_SUCCESS the block of pixels was moved. */
```

### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_border_draw"></a>gx_widget_border_draw
### <a name="draw-widget-border"></a>Desenhar a fronteira do widget

### <a name="prototype"></a>Prototype

```C
VOID gx_widget_border_draw(
    GX_WIDGET *widget,
    GX_COLOR border_color,
    GX_COLOR upper_fill, 
    GX_COLOR lower_fill, 
    GX_BOOL fill);
```

### <a name="description"></a>Descrição

Este serviço traça a fronteira widget. Este serviço é normalmente invocado como parte de uma função de desenho widget. Este serviço interpreta as bandeiras de estilo fronteiriço widget para não desenhar nenhuma fronteira, uma fronteira fina, uma fronteira elevada, uma fronteira embutida, ou uma fronteira espessa.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **border_color** Cor da borda. **O apêndice A** contém cores pré-definidas. Note que a aplicação também pode adicionar cores personalizadas.
- **upper_fill** Cor de preenchimento superior. **O apêndice A** contém cores pré-definidas. Note que a aplicação também pode adicionar cores personalizadas.
- **lower_fill** Cor de preenchimento inferior. **O apêndice A** contém cores pré-definidas. Note que a aplicação também pode adicionar cores personalizadas.
- **encher** Esta bandeira booleana indica se a área do widget deve ou não ser preenchida com as cores de enchimento fornecidas. Se este valor for GX_FALSE, apenas a fronteira widget é desenhada.

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom widget draw function. */

VOID my_widget_draw(GX_WIDGET * widget)
{
      /* Call widget border draw. */
      gx_widget_border_draw(widget, GX_COLOR_BLACK,
                            GX_COLOR_GREEN, GX_COLOR_BLUE,
                            GX_TRUE);

      /* Add your own drawing here. */

      /* Draw child widgets. */
      Gx_widget_children_draw(widget);
}
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_border_style_set"></a>gx_widget_border_style_set
### <a name="set-widget-border-style"></a>Definir estilo de fronteira widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_border_style_set(
    GX_WIDGET *widget, 
    ULONG style);
```

### <a name="description"></a>Descrição

Este serviço define o estilo de fronteira widget.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **estilo** Estilo de fronteira. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de estilo de fronteira widget bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set border style of “my_widget”. */
status = gx_widget_border_style_set(&my_widget,
                                    GX_STYLE_BORDER_RAISED);

/* If status is GX_SUCCESS the widget “my_widget” border style has been set. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_border_width_get"></a>gx_widget_border_width_get
### <a name="get-widget-border-width"></a>Obtenha largura de fronteira widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_border_width_get(
    GX_WIDGET *widget,
    GX_VALUE *return_width);
```

### <a name="description"></a>Descrição

Este serviço obtém a largura da fronteira widget.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **return_width** Ponteiro para destino para largura de fronteira widget

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) recuperou com sucesso a largura da fronteira
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_VALUE my_width;

/* Get border width of “my_widget”. */
status = gx_widget_border_width_get(&my_widget, &my_width);

/* If status is GX_SUCCESS, “my_width” contains the border width of the widget “my_widget”. */
```

### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_canvas_get"></a>gx_widget_canvas_get
### <a name="get-widget-canvas"></a>Obtenha tela widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_canvas_get(
    GX_WIDGET *widget,
    GX_CANVAS **return_canvas)
```
### <a name="description"></a>Descrição

Este serviço devolve um ponteiro à tela sobre a qual este widget é renderizado.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **return_canvas** Ponteiro para destino para tela widget

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Lona widget bem sucedida obter
- **GX_FAILURE** (0x10) tela widget não encontrada
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Get canvas associated with “my_widget”. */
status = gx_widget_canvas_get(&my_widget, &my_canvas);

/* If status is GX_SUCCESS, “my_canvas” contains the canvas of the widget “my_widget”. */
```

### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_child_detect"></a>gx_widget_child_detect
### <a name="detect-widget-child"></a>Detetar criança widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_child_detect(
    GX_WIDGET *parent, 
    GX_WIDGET *child,
    GX_BOOL *return_detect);
```

### <a name="description"></a>Descrição

Este serviço deteta se o widget é uma criança do widget dos pais. Este serviço nidifica para procurar crianças de crianças, e retorna TRUE se o widget dos pais estiver em qualquer nível um ancestral do widget da criança.

### <a name="parameters"></a>Parâmetros

- **pai** Ponteiro para widget dos pais
- **criança** Ponteiro para widget infantil
- **return_detect** Ponteiro para destino para deteção

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Deteção bem sucedida de crianças widget
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_WIDGET** (0x12) Widget parental ou infantil não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_BOOL detected;

/* Determine if “my_child” is a child of “my_widget”. */
status = gx_widget_child_detect(&my_widget, &my_child, &detected);

/* If status is GX_SUCCESS and “detected” is GX_TRUE, “my_child” is a child of widget “my_widget”. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_children_draw"></a>gx_widget_children_draw
### <a name="draw-widget-children"></a>Desenhe crianças widget

### <a name="prototype"></a>Prototype

```C
VOID gx_widget_children_draw(GX_WIDGET *widget);
```

### <a name="description"></a>Descrição

Este serviço atrai todas as crianças do widget dos pais. Este serviço é normalmente invocado por todas as funções padrão de desenho de widgets para desenhar quaisquer widgets infantis existentes, e deve ser invocado por quaisquer funções de desenho personalizado para permitir que widgets infantis sejam ligados ao seu tipo de widget parental personalizado.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom widget draw function. */

VOID my_widget_draw(GX_WIDGET * widget)
{
        /* Call default widget background draw. */
        gx_widget_background_draw(widget);

        /* Add your own drawing here. */

        /* Draw child widgets. */
        gx_widget_children_draw(widget);
}
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_client_get"></a>gx_widget_client_get
### <a name="get-widget-client-area"></a>Obtenha a área do cliente widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_client_get(
    GX_WIDGET *widget,
    GX_VALUE border_width,
    GX_RECTANGLE *return_client_area);
```
### <a name="description"></a>Descrição

Este serviço calcula a área do widget ao subtrair a largura da fronteira widget do tamanho geral do widget.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **border_width** Largura da borda widget
- **return_client_area** Destino para a área de cliente de regresso

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Área de cliente widget bem sucedida obter
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido
- **GX_INVALID_VALUE** (0x22) fronteira widget não é válida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_RECTANGLE client_area
/* Get client area of widget “my_widget”. */
status = gx_widget_client_get(&my_widget, my_widget_width,
                              &client_area);

/* If status is GX_SUCCESS, the “client_area” is the client area of “my_widget”. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_color_get"></a>gx_widget_color_get
### <a name="get-color"></a>Obter cor

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_color_get(
    GX_WIDGET *widget,
    GX_RESOURCE_ID resource_id,
    GX_COLOR *return_color);
```

### <a name="description"></a>Descrição

Este serviço obtém a cor associada ao ID de recursos fornecido. Este serviço só deve ser chamado por widgets visíveis.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para o bloco de controlo do widget
- **resource_id** Identificação de recursos de cor. **O apêndice B** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.
- **return_color** Ponteiro para destino para a cor. **O apêndice A** contém cores pré-definidas. Note que a aplicação também pode adicionar cores personalizadas.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Cor de sucesso obter
- **ID** de recursos inválidos de GX_INVALID_RESOURCE_ID (0x33)
- **GX_INVALID_CANVAS** (0x20) tela widget não válida ou widget é invisível
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_COLOR actual_color;

/* Get color for resource ID MY_FIRST_COLOR_ID. */
status = gx_widget_color_get(my_widget, MY_FIRST_COLOR_RESOURCE_ID,
                            &actual_color);

/* If status is GX_SUCCESS the actual color is contained in “actual_color”. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_font_get
- gx_widget_pixelmap_get

## <a name="gx_widget_create"></a>gx_widget_create
### <a name="create-widget"></a>Criar widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_create(
    GX_WIDGET *widget, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    ULONG style, 
    USHORT widget_id,
    GX_CONST GX_RECTANGLE *size);
```
### <a name="description"></a>Descrição

Este serviço cria um widget.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **nome** Nome lógico do widget
- **pai** Ponteiro para widget dos pais
- **estilo** Estilo, estilo. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **widget_id** ID definido pela aplicação do widget
- **tamanho** Tamanho do widget

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Widget de sucesso criar
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido
- **GX_INVALID_WIDGET** (0x12) Widget dos pais não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_WIDGET my_widget;
GX_RECTANGLE size;

gx_utility_rectangle_define(&size, 0, 0, 100, 100);

/* Get client area of widget “my_widget”. */
status = gx_widget_create(&my_widget, "my widget",
                          &my_parent_window, GX_STYLE_BORDER_RAISED, MY_WIDGET_ID, &size);

/* If status is GX_SUCCESS, the widget “my_widget” has been created. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_created_test"></a>gx_widget_created_test
### <a name="test-if-widget-created"></a>Teste se widget criado

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_created_test(
    GX_WIDGET *widget,
    GX_BOOL *return_test);
```
### <a name="description"></a>Descrição

Este serviço testa para determinar se o widget foi previamente criado. Se não forem encontrados erros, esta função volta GX_SUCCESS, independentemente de o widget ser criado ainda ou não. O resultado do teste está no ponteiro return_test.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **return_test** Destino para o resultado do teste

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conclusão do teste com sucesso
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_BOOL was_created;

/* Test to see if widget “my_widget” is created. */
status = gx_widget_created_test(&my_widget, &was_created);

/* If status is GX_SUCCESS, no error occurred. If “was_created” is
GX_TRUE, the widget “my_widget” has been created. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_delete"></a>gx_widget_delete
### <a name="delete-widget"></a>Eliminar widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_delete(GX_WIDGET *widget);
```

### <a name="description"></a>Descrição

Este serviço elimina o widget. Se o bloco de controlo widget for atribuído dinamicamente, o serviço gx_system_memory_free é invocado para armazenamento gratuito e dinamicamente atribuído.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Widget bem sucedido eliminar GX_CALLER_ERROR (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido
- **GX_SYSTEM_MEMORY_ERROR** (0x30) A função de livre de memória não está definida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Delete widget “my_widget”. */
status = gx_widget_delete(&my_widget);

/* If status is GX_SUCCESS the widget “my_widget” has been deleted. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_detach"></a>gx_widget_detach
### <a name="detach-widget-from-parent"></a>Widget detach do progenitor

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_detach(GX_WIDGET *widget);
```

### <a name="description"></a>Descrição

Este serviço separa o widget do seu progenitor.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Widget desprender GX_CALLER_ERROR (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Detach widget “my_widget” from its parent. */
status = gx_widget_detach(&my_widget);

/* If status is GX_SUCCESS the widget “my_widget” has been detached. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_draw"></a>gx_widget_draw
### <a name="draw-widget"></a>Desenhar widget

### <a name="prototype"></a>Prototype

```C
VOID gx_widget_draw(GX_WIDGET *widget);
```

### <a name="description"></a>Descrição

Este serviço desenha o widget. Esta função é normalmente chamada internamente pelo mecanismo de atualização de lona GUIX, mas está exposta à aplicação para ajudar na implementação de funções de desenho personalizado.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom widget draw function. */

VOID my_custom_widget_draw(GX_WIDGET *widget)
{
      /* Call default widget draw. */
      gx_widget_draw(widget);

      /* Add your own drawing here. */
}
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_draw_set"></a>gx_widget_draw_set
### <a name="assign-the-widget-drawing-function"></a>Atribua a função de desenho widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_draw_set(
    GX_WIDGET *widget,
    VOID (*drawing_function) (GX_WIDGET *));
```

### <a name="description"></a>Descrição

Este serviço substitui a função de desenho predefinido do widget.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **drawing_function** Ponteiro para a função de desenho

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Substituição da função de desenho de widgets bem sucedida
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Define a custom drawing function. */
VOID my_drawing_function(GX_WIDGET *widget)
{
      /* Add your own drawing here. */
}

/* Set the drawing function of widget “my_widget” to “my_drawing_function”. */
status = gx_widget_draw_set(&my_widget, my_drawing_function);

/* If status is GX_SUCCESS the widget “my_widget” has the drawning function “my_drawing_function”. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_event_generate"></a>gx_widget_event_generate
### <a name="generate-widget-event"></a>Gerar evento widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_event_generate(
    GX_WIDGET *widget, 
    USHORT event_type, LONG value);
```

### <a name="description"></a>Descrição

Este serviço gera um tipo GX_SIGNAL de evento, que é um tipo ou classe particular de GX_EVENT. gx_widget_event_generate() codifica o ID widget de 16 bits, juntamente com o passado em event_type, em um único valor de 32 bits GX_EVENT.gx_event_type. O parâmetro de valor é codificado no gx_event gerado. gx_event_payload.gx_event_longdata.

O campo gerado event.gx_event_target é sempre carregado com o progenitor do widget chamando, o que significa que o evento gerado é sempre enviado primeiro para o progenitor do widget gerador.

Note que gx_widget_event_generate só devem ser utilizados para enviar GX_SIGNAL tipos de eventos de gama. Para todos os outros tipos de eventos, incluindo os tipos de eventos definidos pelo utilizador, utilize a API gx_system_event_send() API, que concede o controlo total sobre todos os campos do evento empurrados na fila do evento GUIX.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **event_type** Tipo de evento. **O apêndice E** contém eventos GUIX pré-definidos. Eventos adicionais podem ser adicionados pela aplicação.
- **valor** Informações adicionais sobre eventos

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Geração de eventos widgets bem sucedidos
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Generate a redraw event for widget “my_widget”. */
status = gx_widget_event_generate(&my_widget, GX_EVENT_REDRAW, 0);

/* If status is GX_SUCCESS the redraw event for widget “my_widget” has been generated. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get
- gx_system_event_send

## <a name="gx_widget_event_process"></a>gx_widget_event_process
### <a name="process-widget-event"></a>Evento widget de processo

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_event_process(
    GX_WIDGET *widget, 
    GX_EVENT *event);
```

### <a name="description"></a>Descrição

Esta é a função de processamento de eventos predefinido para todos os widgets. Quando uma função de processamento de eventos personalizado é escrita, a ação padrão para qualquer tipo de evento deve ser sempre passar o evento para o tipo de widget em que se baseia um widget. Widgets que são baseados na utilização mais básica do GX_WIDGET tipo de passe gx_widget_event_process como função de processamento de eventos predefinido.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **evento** Ponteiro para o evento para processar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Processamento de eventos widgets com sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Process event “my_event” for widget “my_widget”. */
status = gx_widget_event_process(&my_widget, &my_event);

/* If status is GX_SUCCESS the event “my_event” for widget “my_widget” has been processed. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_event_process_set"></a>gx_widget_event_process_set
### <a name="set-event-processing-function-of-widget"></a>Definir função de processamento de eventos de widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_event_process_set(
    GX_WIDGET *widget,
    UINT (*event_processing) (GX_WIDGET *, GX_EVENT *));
```

### <a name="description"></a>Descrição

Este serviço substitui a função de processamento de eventos do widget.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **event_processing** Ponteiro para nova função de processamento de eventos

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Processamento de eventos widgets com sucesso sobrepõem-se
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
UINT my_event_process(GX_TREE_VIEW *tree_view,
                      GX_EVENT *event)
{
      UINT status = GX_SUCCESS;

      switch(event->gx_event_type)
      {
      case xyz:
            /* Insert custom event handling here */
            break;

      default:
            /* Pass all other events to the default tree view
               event processing */
            status = gx_tree_view_event_process(tree_view, event);
            break;
      }
      return status;
}

/* Use “my_event_process” to process events for widget “my_tree_view”. */
status = gx_widget_event_process_set((GX_WIDGET *)&my_tree_view,
                    (VOID (*)(GX_WIDGET *))my_event_process);

/* If status is GX_SUCCESS all event processing for widget “my_tree_view” is handled by “my_event_process”. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_event_to_parent"></a>gx_widget_event_to_parent
### <a name="send-event-to-widgets-parent"></a>Enviar evento para o pai do Widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_event_to_parent(
    GX_WIDGET *widget,
    GX_EVENT *event);
```
### <a name="description"></a>Descrição

Este serviço envia um evento para o pai do widget.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **evento** Ponteiro para o evento

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) enviou com sucesso evento para o pai do widget
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Send my_event to the widget’s parent */
status = gx_widget_event_to_parent(&my_widget, my_event);

/* If status is GX_SUCCESS the event has been delivered to the parent of my_widget. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_fill_color_set"></a>gx_widget_fill_color_set
### <a name="set-widget-background-color"></a>Definir cor de fundo widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_fill_color_set(
    GX_WIDGET *widget,
    GX_RESOURCE_ID normal_color_id,
    GX_RESOURCE_ID selected_color_id,
    GX_RESOURCE_ID disabled_color_id);
```
### <a name="description"></a>Descrição

Este serviço define as cores de fundo do widget.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **normal_color_id** Identificação de recursos da cor de preenchimento em estado normal. **O apêndice A** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.
- **selected_color_id** ID de recurso da cor de preenchimento quando o widget ganhar foco. **O apêndice A** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.
- **disabled_color_id** ID de recurso da cor de preenchimento quando o estilo GX_STYLE_ENABLED não está definido. **O apêndice A** contém IDs de recursos de cor pré-definidos. Note que a aplicação pode adicionar IDs de recursos de cor personalizados também.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) definir com sucesso a cor de preenchimento de widget
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set background of “my_widget”. */
status = gx_widget_fill_color_set(&my_widget,
                    GX_COLOR_ID_NORMAL_FILL,
                    GX_COLOR_ID_SELECTED_FILL,
                    GX_COLOR_ID_DISABLED_FILL);

/* If status is GX_SUCCESS the widget “my_widget” background has been set. */
```

### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_find"></a>gx_widget_find
### <a name="find-child-widget-of-parent-widget"></a>Encontre widget infantil do widget dos pais

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_find(
    GX_WIDGET *parent, 
    USHORT widget_id,
    INT search_depth, 
    GX_WIDGET **return_widget);
```
### <a name="description"></a>Descrição

Este serviço procura através das crianças do progenitor especificado à procura de um widget com o valor de ID solicitado.

### <a name="parameters"></a>Parâmetros

- **pai** Ponteiro para widget dos pais a partir do qual a pesquisa é iniciada
- **widget_id** Widget ID para procurar
- **search_depth** Define o nível de nidificação recursivo no qual a função procurará widgets infantis. Se este valor for <= 0, apenas são pesquisados os filhos imediatos do widget dos pais. Se este valor for GX_SEARCH_DEPTH_INFINITE, todas as crianças de todos os widgets infantis são exaustivamente revistadas. Para qualquer outro valor > 0, este valor limita o quão profundamente aninhado esta função irá pesquisar através de widgets infantis procurados para o widget ID solicitado.
- **return_widget** Ponteiro para destino para widget encontrado

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Widget de sucesso
- **widget GX_NOT_FOUND** (0x09) não fount
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_WIDGET *widget_found;

/* Find widget “my_widget”. */
status = gx_widget_find(&my_widget, GX_SEARCH_DEPTH_INFINITE
                        MY_WIDGET_ID, &widget_found);

/* If status is GX_SUCCESS, the pointer “widget_found” contains the pointer to the widget found. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_first_child_get"></a>gx_widget_first_child_get
### <a name="return-pointer-to-first-child-widget"></a>Devolva o ponteiro ao widget primeiro para crianças

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_first_child_get(
    GX_WIDGET *parent,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>Descrição

O GUIX mantém uma lista estruturada de widgets de pais e filhos. Este serviço devolve um ponteiro ao primeiro widget infantil do progenitor.

### <a name="parameters"></a>Parâmetros

- **pai** Ponteiro para widget dos pais
- **widget_return** Ponteiro para devolver ponteiro widget

### <a name="return-values"></a>Valores de devolução

- **Ponteiro GX_SUCCESS** (0x00) devolvido
- **GX_PTR_ERROR** (0x07) Ponteiro widget inválido
- **widget** GX_INVALID_WIDGET (0x12) Inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Retrieve child widget pointer. */

GX_WIDGET *get_child_widget(GX_WIDGET *parent)
{
      GX_WIDGET *child;
      UINT status;

      status = gx_widget_first_child_get(parent, &child);
      if (status == GX_SUCCESS)
      {
            return child;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>Consulte também

- gx_widget_last_child_get
- gx_widget_next_sibling_get
- gx_widget_parent_get
- gx_widget_previous_sibling_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_focus_next"></a>gx_widget_focus_next
### <a name="move-focus-to-next-widget-in-navigation-order"></a>Mova o foco para o próximo widget na ordem de navegação

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_focus_next(GX_WIDGET *widget);
```

### <a name="description"></a>Descrição

Este serviço move o foco para o próximo widget irmão na lista de widgets ligados que aceitam o foco.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para o bloco de controlo do widget

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) foco foi movido
- **GX_FAILURE** (0x00) não se moveu
- **GX_PTR_ERROR** (0x07) Ponteiro widget inválido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **widget** GX_INVALID_WIDGET (0x12) Inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Move focus to next widget in navigation order. */ status =
gx_widget_focus_next(&my_widget);

/* If status is GX_SUCCESS the focus has been moved to the next
widget in the navigation order */
```
### <a name="see-also"></a>Consulte também

- gx_widget_focus_previous

## <a name="gx_widget_focus_previous"></a>gx_widget_focus_previous
### <a name="move-focus-to-previous-widget-in-navigation-order"></a>Mova o foco para widget anterior na ordem de navegação

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_focus_previous(GX_WIDGET *widget);
```

### <a name="description"></a>Descrição

Este serviço move o foco para o widget anterior na ordem de navegação.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget que a corrente tem foco de entrada.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) foco foi movido
- **GX_FAILURE** (0x00) não se moveu

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Move focus to previuos widget in navigation order. */ status =
gx_widget_focus_previous(&my_widget);

/* If status is GX_SUCCESS the input focus has been moved to the
previous widget. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_focus_next

## <a name="gx_widget_font_get"></a>gx_widget_font_get
### <a name="get-font-for-specified-resource-id"></a>Obtenha o tipo de letra para iD de recursos especificados

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_font_get(
    GX_WIDGETG *widget,
    GX_RESOURCE_ID resource_id,
    GX_FONT **return_font);
```
### <a name="description"></a>Descrição

Este serviço recupera o tipo de letra associado ao ID de recursos especificado a partir da tabela de fontes do visor em que este widget é visível. Esta função só deve ser chamada por um widget visível.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para o bloco de controlo do widget
- **resource_id** ID de recurso de fonte
- **return_font** Ponteiro para destino para ponteiro de fonte

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Fonte recuperada com sucesso
- **ID** de recursos inválidos de GX_INVALID_RESOURCE_ID (0x33)
- **GX_INVALID_CANVAS** (0x20) tela widget não válida ou widget é invisível
- **GX_PTR_ERROR** (0x07) Ponteiro widget inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_FONT *my_font;
/* Get font for MY_FONT_ID. */
status = gx_widget_font_get(widget, MY_FONT_RESOURCE_ID, &my_font);
/* If status is GX_SUCCESS the font pointer has been retrieved in “my_font”. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_color_get
- gx_widget_pixelmap_get

## <a name="gx_widget_free"></a>gx_widget_free
### <a name="release-memory-associated-with-a-widget"></a>Liberte a memória associada a um widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_free(GX_WIDGETG *widget);
```

### <a name="description"></a>Descrição

Este serviço liberta a memória associada a um bloco de controlo widget.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para o bloco de controlo do widget
- **resource_id** ID de recurso de fonte
- **return_font** Ponteiro para destino para ponteiro de fonte

### <a name="return-values"></a>Valores de devolução

- **widget GX_SUCCESS** (0x00) libertado com sucesso
- **GX_SYSTEM_MEMPRY_ERROR** (0x30) A função de livre de memória não está definida
- **GX_PTR_ERROR** (0x07) Ponteiro widget inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_WIDGET widget;
UINT status;

status = gx_widget_allocate(&widget, sizeof(GX_WIDGET))

/* Free a runtime allocated widget. */
if (status == GX_SUCCESS)
{
      status = gx_widget_free(widget);
}

/* If status is GX_SUCCESS the memory that allocated to the widget has been released. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_front_move"></a>gx_widget_front_move
### <a name="move-widget-to-front"></a>Mova o widget para a frente

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_front_move(
    GX_WIDGET *widget, 
    GX_BOOL *return_moved);
```

### <a name="description"></a>Descrição

Este serviço move o widget para a frente na lista de pedidos de Z dos widgets infantis.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget para mover
- **return_moved** Ponteiro para destino para indicação widget foi movido

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Widget bem sucedido move-se para a frente
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_NO_CHANGE** (0x08) já na frente
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_BOOL widget_moved;

/* Move widget “my_widget” to the front. */
status = gx_widget_front_move(&my_widget, &widget_moved);

/* If status is GX_SUCCESS and “widget_moved” is GX_TRUE, the
widget “my_widget” was moved to the front . */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_height_get"></a>gx_widget_height_get
### <a name="get-widget-height"></a>Obtenha a altura do widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_height_get(
    GX_WIDGET *widget,
    UINT *return_height);
```

### <a name="description"></a>Descrição

Este serviço obtém a altura do widget.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **return_height** Ponteiro para destino para altura widget

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Altura de widget bem sucedida obter
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_VALUE widget_height;

/* Get height for widget “my_widget”. */
status = gx_widget_height_get(&my_widget, &widget_height);

/* If status is GX_SUCCESS the height of the widget is contained in
“widget_height” . */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_hide"></a>gx_widget_hide
### <a name="hide-widget"></a>Ocultar widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_hide(GX_WIDGET *widget);
```

### <a name="description"></a>Descrição

Este serviço esconde o widget. Este widget ainda está ligado ao seu progenitor, mas não é permitido desenhar na tela.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Widget hide bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```c
/* Hide widget “my_widget”. */
status = gx_widget_hide(&my_widget);

/* If status is GX_SUCCESS the widget “my_widget” is hidden. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_style_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_last_child_get"></a>gx_widget_last_child_get
### <a name="return-pointer-to-last-child-widget"></a>Ponteiro de retorno para o último widget infantil

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_last_child_get(
    GX_WIDGET *parent,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>Descrição

O GUIX mantém uma lista estruturada de widgets de pais e filhos. Este serviço devolve um ponteiro ao último widget infantil do progenitor.

### <a name="parameters"></a>Parâmetros

- **pai** Ponteiro para widget dos pais
- **widget_return** Ponteiro para devolver ponteiro widget

### <a name="return-values"></a>Valores de devolução

- **Ponteiro GX_SUCCESS** (0x00) devolvido
- **GX_PTR_ERROR** (0x07) Ponteiro widget inválido
- **widget** GX_INVALID_WIDGET (0x12) Inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Retrieve child widget pointer. */

GX_WIDGET *get_last_child_widget(GX_WIDGET *parent)
{

      GX_WIDGET *child;
      UINT status;

      status = gx_widget_last_child_get(parent, &child);
      if (status == GX_SUCCESS)
      {
              return child;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>Consulte também

- gx_widget_first_child_get
- gx_widget_next_sibling_get
- gx_widget_parent_get
- gx_widget_previous_sibling_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_next_sibling_get"></a>gx_widget_next_sibling_get
### <a name="return-pointer-to-next-sibling-of-current-widget"></a>Devolva o ponteiro ao próximo irmão do widget atual

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_next_sibling_get(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>Descrição

O GUIX mantém uma lista estruturada de widgets de pais e filhos. Este serviço devolve um ponteiro ao próximo irmão do widget atual.

### <a name="parameters"></a>Parâmetros

- **corrente** Ponteiro para widget atual
- **widget_return** Ponteiro para devolver ponteiro widget

### <a name="return-values"></a>Valores de devolução

- **Ponteiro GX_SUCCESS** (0x00) devolvido
- **GX_PTR_ERROR** (0x07) Ponteiro widget inválido
- **widget** GX_INVALID_WIDGET (0x12) Inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Retrieve next sibling widget pointer. */

GX_WIDGET *get_next(GX_WIDGET *current)
{
      GX_WIDGET *sibling;
      UINT status;

      status = gx_widget_next_sibling_get(current, &sibling);
      if (status == GX_SUCCESS)
      {
            return sibling;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>Consulte também

- gx_widget_first_child_get
- gx_widget_last_child_get
- gx_widget_parent_get
- gx_widget_previous_sibling_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_parent_get"></a>gx_widget_parent_get
### <a name="return-pointer-to-parent-of-current-widget"></a>Ponteiro de retorno para o progenitor do widget atual

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_parent_get(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>Descrição

O GUIX mantém uma lista estruturada de widgets de pais e filhos. Este serviço devolve um ponteiro ao progenitor do widget atual.

### <a name="parameters"></a>Parâmetros

- **corrente** Ponteiro para widget atual
- **widget_return** Ponteiro para devolver ponteiro widget

### <a name="return-values"></a>Valores de devolução

- **Ponteiro GX_SUCCESS** (0x00) devolvido
- **GX_PTR_ERROR** (0x07) Ponteiro widget inválido
- **widget** GX_INVALID_WIDGET (0x12) Inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Retrieve parent widget */

GX_WIDGET *get_parent(GX_WIDGET *current)
{
      GX_WIDGET *parent;
      UINT status;

      status = gx_widget_parent_get(current, &parent);
      if (status == GX_SUCCESS)
      {
            return parent;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>Consulte também

- gx_widget_first_child_get
- gx_widget_last_child_get
- gx_widget_next_sibling_get
- gx_widget_previous_sibling_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_pixelmap_get"></a>gx_widget_pixelmap_get
### <a name="get-pixelmap"></a>Obter pixelmap

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_pixelmap_get(
    GX_WIDGET *widget,
    GX_RESOURCE_ID resource_id,
    GX_PIXELMAP **return_pixelmap);
```

### <a name="description"></a>Descrição

Este serviço obtém o pixelmap associado ao ID de recursos fornecido. Este serviço só deve ser solicitado para widgets visíveis.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para o bloco de controlo do widget
- **pixelmap_id** ID de recursos Pixelmap
- **return_pixelmap** Ponteiro para o ponteiro de destino pixelmap

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Pixelmap de sucesso obter
- **ID** de recursos inválidos de GX_INVALID_RESOURCE_ID (0x33)
- **GX_INVALID_CANVAS** (0x20) tela widget não válida ou widget é invisível
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```c
GX_PIXELMAP *my_pixelmap;

/* Get the pixelmap associated with MY_PIXELMAP_ID. */
status = gx_widget_pixelmap_get(widget, MY_PIXELMAP_RESOURCE_ID,
                                &my_pixelmap);

/* If status is GX_SUCCESS, “my_pixelmap” contains the pixemap pointer. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_color_get
- gx_widget_font_get

## <a name="gx_widget_previous_sibling_get"></a>gx_widget_previous_sibling_get
### <a name="return-pointer-to-previous-sibling-of-the-current-widget"></a>Devolva o ponteiro ao irmão anterior do widget atual

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_previous_sibling_get(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```

### <a name="description"></a>Descrição

O GUIX mantém uma lista estruturada de widgets de pais e filhos. Este serviço devolve um ponteiro ao irmão anterior do widget atual.

### <a name="parameters"></a>Parâmetros

- **corrente** Ponteiro para widget atual
- **widget_return** Ponteiro para devolver ponteiro widget

### <a name="return-values"></a>Valores de devolução

- **Ponteiro GX_SUCCESS** (0x00) devolvido
- **GX_PTR_ERROR** (0x07) Ponteiro widget inválido
- **widget** GX_INVALID_WIDGET (0x12) Inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Retrieve previous sibling widget */

GX_WIDGET *get_previous(GX_WIDGET *current)
{
      GX_WIDGET *sibling;
      UINT status;

      status = gx_widget_previous_sibling_get(current, &sibling);
      if (status == GX_SUCCESS)
      {
          return sibling;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>Consulte também

- gx_widget_first_child_get
- gx_widget_last_child_get
- gx_widget_next_sibling_get
- gx_widget_parent_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_resize"></a>gx_widget_resize
### <a name="resize-widget"></a>Redimensionar widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_resize(
    GX_WIDGET *widget, 
    GX_RECTANGLE *new_size);
```
### <a name="description"></a>Descrição

Este serviço redimensiona o widget. Se o widget estiver visível, é automaticamente invalidado e em fila para redesenhar.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **new_size** Novo tamanho do widget

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Redimensionar widget com sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_RECTANGLE new_size;

gx_utility_rectangle_define(&new_size, 0, 0, 100, 100);

/* Resize widget “my_widget”. */
status = gx_widget_resize(&my_widget, &new_size);

/* If status is GX_SUCCESS the widget “my_widget” has been resized. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_shift"></a>gx_widget_shift
### <a name="shift-widget"></a>Widget de turno

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_shift(
    GX_WIDGET *widget, 
    GX_VALUE x_shift,
    GX_VALUE y_shift, 
    GX_BOOL mark_dirty);
```

### <a name="description"></a>Descrição

Este serviço desloca o widget e, opcionalmente, marca-o como sujo.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **x_shift** Número de pixels para deslocar no eixo x
- **y_shift** Número de pixels para deslocar no eixo y
- **mark_dirty** GX_TRUE para indicar sujo, caso contrário, GX_FALSE

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Mudança de widget bem sucedida GX_CALLER_ERROR (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Shift widget “my_widget”. */
status = gx_widget_shift(&my_widget, 10, 20, GX_FALSE);

/* If status is GX_SUCCESS the widget “my_widget” has been shifted. */
```

### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_show"></a>gx_widget_show
### <a name="show-widget"></a>Mostrar widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_show(GX_WIDGET *widget);
```

### <a name="description"></a>Descrição

Este serviço mostra o widget. O widget só se tornará visível se estiver ligado a um progenitor e o widget dos pais também for visível.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Widget de sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Show widget “my_widget”. */
status = gx_widget_show(&my_widget);

/* If status is GX_SUCCESS the widget “my_widget” has been shown. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_status_add"></a>gx_widget_status_add
### <a name="add-widget-status"></a>Adicionar o estado do widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_status_add(
    GX_WIDGET *widget, 
    ULONG status)
```

### <a name="description"></a>Descrição

Este serviço adiciona qualquer combinação de bandeiras de estado ao widget especificado.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **estado** Estado a adicionar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Estado do widget bem sucedido adicionar
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Add status to widget “my_widget”. */
status = gx_widget_status_add(&my_widget, status_to_add);

/* If status is GX_SUCCESS the widget “my_widget” status was. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_status_get"></a>gx_widget_status_get
### <a name="get-widget-status"></a>Obtenha o estado do widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_status_get(
    GX_WIDGET *widget,
    ULONG *return_status)
```

### <a name="description"></a>Descrição

Este serviço recupera bandeiras de estado do widget.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **return_status** Ponteiro para o estado que está a ser devolvido

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Estado widget bem sucedido obter
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
ULONT get_status;

/* Retrieve status flag from widget “my_widget”. */ status =
gx_widget_status_get(&my_widget, &get_status);

/* If status is GX_SUCCESS the status from widget “my_widget” is
saved to “get_status”. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_status_remove"></a>gx_widget_status_remove
### <a name="remove-widget-status"></a>Remover o estado do widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_status_remove(
    GX_WIDGET *widget, 
    ULONG status)
```

### <a name="description"></a>Descrição

Este serviço remove as bandeiras de estado especificadas da variável de estado interno dos widgets.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **estado** Estado a remover

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Remoção do estado do widget bem sucedido
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Remove status of widget “my_widget”. */
status = gx_widget_status_remove(&my_widget, status_to_remove);

/* If status is GX_SUCCESS, the status flags are removed from the
widget “my_widget”. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_status_test"></a>gx_widget_status_test
### <a name="test-widget-status"></a>Estado do widget de teste

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_status_test(
    GX_WIDGET *widget, 
    ULONG status,
    GX_BOOL *return_test);
```
### <a name="description"></a>Descrição

Este serviço testa as bandeiras de estado do widget especificado e armazena o resultado na memória apontada por "return_test".

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **estado** Estado a testar
- **return_status** Ponteiro para destino para o resultado do teste

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Teste de estado widget bem sucedido
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_BOOL test_result;

/* Test status of widget “my_widget”. */
status = gx_widget_status_test(&my_widget, status_to_test,
                              &test_result);

/* If status is GX_SUCCESS the widget “my_widget” status was tested
and the result in “test_result”. */
```
### <a name="see-also"></a>Consulte também

- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set

## <a name="gx_widget_string_get"></a>gx_widget_string_get
### <a name="retrieve-string-associated-with-a-visible-widget-and-string-id-deprecated"></a>Obter corda associada a um widget visível e iD de corda (depreciado)

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_string_get(
    GX_WIDGET *widget,
    GX_RESOURCE_ID string_id,
    GX_CONST GX_CHAR **string);
```

### <a name="description"></a>Descrição

Este serviço é prevadido a favor de gx_widget_string_get_ext().

Este serviço devolve a entrada da tabela de cordas para o valor de ID de cadeia dado. Este serviço é semelhante ao gx_display_string_get, exceto que o visor ativo é determinado automaticamente em vez de ser transmitido pelo chamador. Este serviço só pode ser utilizado para widgets visíveis, ou seja, o visor associado a este widget é conhecido.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **string_id** Valor de ID de cadeia do cabeçalho de recursos
- **cadeia** Endereço de variável para cadeia de retorno

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Teste de estado widget bem sucedido
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_CONST GX_CHAR *string;

/* Test status of widget “my_widget”. */
status = gx_widget_string_get(&my_widget, GX_STRING_ID_SHUTDOWN,
      &string);

/* If status is GX_SUCCESS the string has been retrieved */
```
### <a name="see-also"></a>Consulte também

- gx_display_string_get
- gx_display_active_langauge_set

## <a name="gx_widget_string_get_ext"></a>gx_widget_string_get_ext
### <a name="retrieve-string-associated-with-a-visible-widget-and-string-id"></a>Obter corda associada a um widget visível e iD de corda

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_string_get(
    GX_WIDGET *widget,
    GX_RESOURCE_ID string_id,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Descrição

Este serviço devolve a entrada da tabela de cordas para o valor de ID de cadeia dado. Este serviço é semelhante ao gx_display_string_get, exceto que o visor ativo é determinado automaticamente em vez de ser transmitido pelo chamador. Este serviço só pode ser utilizado para widgets visíveis, ou seja, o visor associado a este widget é conhecido.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **string_id** Valor de ID de cadeia do cabeçalho de recursos
- **cadeia** Endereço de variável para cadeia de retorno

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Teste de estado widget bem sucedido
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_STRING string;

/* Test status of widget “my_widget”. */

status = gx_widget_string_get_ext(&my_widget,
                          GX_STRING_ID_SHUTDOWN, &string);

/* If status is GX_SUCCESS the string has been retrieved */
```

### <a name="see-also"></a>Consulte também

- gx_display_string_get
- gx_display_active_langauge_set

## <a name="gx_widget_style_add"></a>gx_widget_style_add
### <a name="add-widget-style"></a>Adicione estilo widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_style_add(
    GX_WIDGET *widget, 
    ULONG style)
```

### <a name="description"></a>Descrição

Este serviço adiciona um estilo ao widget. Além disso, são tomadas as seguintes ações.

Se o estilo adicionado for GX_STYLE_TRANSPARENT, GX_STATUS_TRANSPARENT de estatuto serão adicionados.

Se o estilo adicionado for GX_STYLE_ENABLED, GX_STATUS_SELECTABLE de estatuto serão adicionados.

Se o widget estiver visível, é automaticamente invalidado e em fila para redesenhar.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **estilo** Novo estilo para adicionar. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Sucesso estilo widget adicionar
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Add style to widget “my_widget”. */
status = gx_widget_style_add(&my_widget, GX_STYLE_BORDER_RAISED);

/* If status is GX_SUCCESS, the style was successfully applied to the widget “my_widget”. */
```

### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_style_get"></a>gx_widget_style_get
### <a name="get-widget-style"></a>Obtenha estilo widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_style_get(
    GX_WIDGET *widget, 
    ULONG *return_style)
```

### <a name="description"></a>Descrição

Este serviço recupera a bandeira de estilo do widget.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **return_style** Ponteiro para o estilo que está sendo devolvido.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) recuperou com sucesso o estilo widget
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios


### <a name="example"></a>Exemplo

```C
/* Retrieve style from widget into “style”. */
status = gx_widget_style_get(&my_widget, &style);

/* If status is GX_SUCCESS the style flag from widget is saved in “style”. */
```

### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_remove
- gx_widget_style_add
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_style_remove"></a>gx_widget_style_remove
### <a name="remove-widget-style"></a>Remova o estilo widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_style_remove(
    GX_WIDGET *widget, 
    ULONG style)
```

### <a name="description"></a>Descrição

Este serviço remove um estilo do widget. Além disso, são tomadas as seguintes ações.

Se o estilo removido for GX_STYLE_TRANSPARENT, GX_STATUS_TRANSPARENT de estado serão removidos.

Se o estilo removido for GX_STYLE_ENABLED, GX_STATUS_SELECTABLE de estado serão removidos.

Se o widget estiver visível, é automaticamente invalidado e em fila para redesenhar.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **estilo** Estilo para remover. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Estilo widget bem sucedido remover
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Remove style from widget “my_widget”. */
status = gx_widget_style_remove(&my_widget,
                                GX_STYLE_BORDER_RAISED);

/* If status is GX_SUCCESS the GX_STYLE_BORDER_RAISED style was removed from the widget “my_widget”.*/
```

### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_style_set"></a>gx_widget_style_set
### <a name="set-widget-style"></a>Definir estilo widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_style_set(
    GX_WIDGET *widget, 
    ULONG style)
```

### <a name="description"></a>Descrição

Este serviço define um estilo para o widget.

Se o estilo definido incluir GX_STYLE_TRANSPARENT, o estado GX_STATUS_TRANSPARENT será adicionado, caso contrário o estado será removido.

Se o estilo definido incluir GX_STYLE_ENABLED, o estado GX_STATUS_SELECTABLE será adicionado, caso contrário o estado será removido.

Se o widget estiver visível, é automaticamente invalidado e em fila para redesenhar.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **estilo** Estilo para definir. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de estilo widget bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set style GX_STYLE_TRANSPARENT to the widget “my_widget”. */
status = gx_widget_style_set(&my_widget, GX_STYLE_TRANSPARENT);

/* If status is GX_SUCCESS the widget “my_widget” style is set to GX_STYLE_TRANSPARENT. */
```

### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_text_blend"></a>gx_widget_text_blend
### <a name="blend-text-assigned-to-widget-deprecated"></a>Misturar texto atribuído ao widget (precedido)

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_text_blend(
    GX_WIDGET *widget, 
    UINT *tColor,
    UINT font_id, 
    GX_CHAR *string,
    INT x_offset, 
    INT y_offset, 
    UCHAR alpha)
```

### <a name="description"></a>Descrição

Este serviço é prevadido a favor de gx_widget_text_blend_ext().

Este serviço mistura o texto especificado sobre um widget utilizando o alinhamento de texto e escova de corrente.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **tColor** Cor de texto
- **font_id** ID de fonte
- **cadeia** Corda de desenho
- **x_offset** Ajuste da posição de desenho
- **y_offset** Ajuste da posição de desenho
- **alfa** Valor de mistura 0-255

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Largura de widget bem sucedida obter
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido
- **GX_INVALID_STRING_LENGTH** (0x34) Comprimento da corda inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Blend “my_string” over “my_widget” given alpha value 120. */
status = gx_widget_text_blend(&my_widget, my_text_color, my_font_id,
                              &my_string, xoffset, yoffset, 120);

/* If status is GX_SUCCESS “my_string” has been blend to “my_widget”. */
```

### <a name="see-also"></a>Consulte também

- gx_widget_text_blend_ext

## <a name="gx_widget_text_blend_ext"></a>gx_widget_text_blend_ext
### <a name="blend-text-assigned-to-widget"></a>Misturar texto atribuído ao widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_text_blend(
    GX_WIDGET *widget, 
    UINT *tColor,
    UINT font_id, 
    GX_CONST GX_STRING *string,
    INT x_offset, 
    INT y_offset, 
    UCHAR alpha)
```

### <a name="description"></a>Descrição

Este serviço é prevadido a favor de gx_widget_text_blend_ext().

Este serviço torna uma cadeia sobre o widget especificado usando o alinhamento de escova e texto atual e a cor, fonte e x,y offset especificados.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **tColor** Cor de texto
- **font_id** ID de fonte
- **cadeia** Corda de desenho
- **x_offset** Ajuste da posição de desenho
- **y_offset** Ajuste da posição de desenho
- **alfa** Valor de mistura 0-255

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Largura de widget bem sucedida obter
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido
- **GX_INVALID_STRING_LENGTH** (0x34) Comprimento da corda inválida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
gx_string render_string;
render_string.gx_string_ptr = “Hello”;
render_string.gx_string_length =
    strlen(render_string.gx_string_ptr);

/* Blend “my_string” over “my_widget” given alpha value 120. */
status = gx_widget_text_blend_ext(&my_widget,
        my_text_color,
        my_font_id,
        &render_string, xoffset, yoffset, 120);

/* If status is GX_SUCCESS “my_string” has been blend to “my_widget”. */
```

### <a name="see-also"></a>Consulte também

- gx_widget_text_draw_ext

## <a name="gx_widget_text_draw"></a>gx_widget_text_draw
### <a name="draw-text-assigned-to-widget-deprecated"></a>Desenhar texto atribuído ao widget (precedido)

### <a name="prototype"></a>Prototype

```C
VOID gx_widget_text_draw(
    GX_WIDGET *widget, 
    UINT *tColor,
    UINT font_id, 
    GX_CHAR *string,
    INT x_offset, 
    INT y_offset)
```

### <a name="description"></a>Descrição

Este serviço é prevadido a favor de gx_widget_text_draw_ext().

Este serviço desenha o texto especificado sobre um widget utilizando o alinhamento de texto e escova de texto.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **tColor** Cor de texto
- **font_id** ID de fonte
- **cadeia** Corda de desenho
- **x_offset** Ajuste da posição de desenho
- **y_offset** Ajuste da posição de desenho

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom widget draw function. */

VOID my_custom_widget_draw(GX_WIDGET *widget)
{
    /* Add your own background raw here. */

    /* Call widget text draw. */
    gx_widget_text_draw(widget, my_text_color, my_font_id
                        &my_string, xoffset, yoffset);
}
```

### <a name="see-also"></a>Consulte também

- gx_widget_text_blend
- gx_widget_text_id_draw

## <a name="gx_widget_text_draw_ext"></a>gx_widget_text_draw_ext
### <a name="draw-text-assigned-to-widget"></a>Desenhar texto atribuído ao widget

### <a name="prototype"></a>Prototype

```C
VOID gx_widget_text_draw(
    GX_WIDGET *widget,
    UINT *tColor,
    UINT font_id, 
    GX_CONST GX_STRING *string,
    INT x_offset,
    INT y_offset)
```

### <a name="description"></a>Descrição

Este serviço desenha o texto especificado sobre um widget utilizando o alinhamento de texto e escova de texto.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **tColor** Cor de texto
- **font_id** ID de fonte
- **text_id** ID de texto
- **x_offset** Ajuste da posição de desenho
- **y_offset** Ajuste da posição de desenho

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
gx_string render_string;
render_string.gx_string_ptr = “Hello”;
render_string.gx_string_length =
    strlen(render_string.gx_string_ptr);

/* Write a custom widget draw function. */
VOID my_custom_widget_draw(GX_WIDGET *widget)
{
    /* Add your own background draw here. */

    /* Call widget text draw. */
    gx_widget_text_draw_ext(widget, my_text_color, my_font_id
                        &render_string, xoffset, yoffset);
}
```

### <a name="see-also"></a>Consulte também

- gx_widget_text_blend
- gx_widget_text_id_draw

## <a name="gx_widget_text_id_draw"></a>gx_widget_text_id_draw
### <a name="draw-text-assigned-to-widget"></a>Desenhar texto atribuído ao widget

### <a name="prototype"></a>Prototype

```C
VOID gx_widget_text_id_draw(
    GX_WIDGET *widget, 
    UINT *tColor,
    UINT font_id, 
    UINT text_id,
    INT x_offset, 
    INT y_offse)
```

### <a name="description"></a>Descrição

Este serviço desenha texto sobre um widget dado um id de texto.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **tColor** Cor de texto
- **font_id** ID de fonte
- **text_id** ID de texto
- **x_offset** Ajuste da posição de desenho
- **y_offset** Ajuste da posição de desenho

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Write a custom widget draw function. */

VOID my_custom_widget_draw(GX_WIDGET *widget)
{
    /* Add your own background raw here. */

    /* Call widget text id draw. */
    gx_widget_text_id_draw(widget, my_text_color, my_font_id
                            &my_string_id, xoffset, yoffset);
}
```

### <a name="see-also"></a>Consulte também

- gx_widget_text_blend
- gx_widget_text_draw

## <a name="gx_widget_top_visible_child_find"></a>gx_widget_top_visible_child_find
### <a name="return-pointer-to-visible-child-that-is-top-of-z-order"></a>Devolva o ponteiro para a criança visível que está no topo da ordem Z

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_top_visible_child_find(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```

### <a name="description"></a>Descrição

O GUIX mantém uma lista estruturada de widgets de pais e filhos.
Este serviço devolve um ponteiro à criança mais visível do widget atual.

### <a name="parameters"></a>Parâmetros

- **corrente** Ponteiro para widget atual
- **widget_return** Ponteiro para devolver ponteiro widget

### <a name="return-values"></a>Valores de devolução

- **Ponteiro GX_SUCCESS** (0x00) devolvido
- **GX_PTR_ERROR** (0x07) Ponteiro widget inválido
- **widget** GX_INVALID_WIDGET (0x12) Inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Retrieve topmost visible widget on the display */

GX_WIDGET *get_top_window(GX_WINDOW_ROOT *root)
{
    GX_WIDGET *top_window;
    UINT status;

    status = gx_widget_top_visible_child_find(root, &top_window);
    if (status == GX_SUCCESS)
    {
        return top_window;
    }
    return GX_NULL;
}
```

### <a name="see-also"></a>Consulte também

- gx_widget_first_child_get,
- gx_widget_last_child_get,
- gx_widget_next_sibling_get,
- gx_widget_parent_get,
- gx_widget_previous_sibling_get

## <a name="gx_widget_type_find"></a>gx_widget_type_find
### <a name="search-for-a-widget-of-the-requested-type"></a>Procurar um widget do tipo solicitado

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_type_find(
    GX_WIDGET *parent, 
    USHORT widget_id,
    GX_WIDGET **return_widget)
```

### <a name="description"></a>Descrição

Este serviço procura um widget do tipo solicitado.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **return_width** Ponteiro para destino para largura widget

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Largura de widget bem sucedida obter
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_WIDGET *retrieved_widget;

/* Find horizontal scrollbar under “parent_widget”. */
status = gx_widget_type_find(&parent_widget,
                GX_TYPE_HORIZONTAL_SCROLL_BAR, &retrieved_widget);

/* If status is GX_SUCCESS, the horizontal scrollbar widget is retrieved. */
```

### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set

## <a name="gx_widget_width_get"></a>gx_widget_width_get
### <a name="get-widget-width"></a>Obtenha largura de widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_width_get(
    GX_WIDGET *widget,
    GX_VALUE *return_width)
```

### <a name="description"></a>Descrição

Este serviço obtém a largura do widget.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para widget
- **return_width** Ponteiro para destino para largura widget

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Largura de widget bem sucedida obter
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_VALUE my_widget_width;

/* Get width of widget “my_widget”. */
status = gx_widget_width_get(&my_widget, &my_widget_width);

/* If status is GX_SUCCESS the width of widget “my_widget” is in “my_widget_width”. */
```

### <a name="see-also"></a>Consulte também

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set

## <a name="gx_window_client_height_get"></a>gx_window_client_height_get
### <a name="get-window-client-height"></a>Obtenha a altura do cliente da janela

### <a name="prototype"></a>Prototype

```C
UINT gx_window_client_height_get(
    GX_WINDOW *window,
    GX_VALUE *return_height);
```

### <a name="description"></a>Descrição

Este serviço tem a altura do cliente da janela.

### <a name="parameters"></a>Parâmetros

- **janela** Ponteiro para janela
- **return_height** Ponteiro para destino para a altura do cliente

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Altura do cliente da janela bem sucedida obter
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_RECTANGLE my_client_height;

/* Get client height of “my_window”. */
status = gx_window_client_height_get(&my_window,
                                     &my_client_height);

/* If status is GX_SUCCESS the window “my_window” client height is contained in “my_client_height”. */
```

### <a name="see-also"></a>Consulte também

- gx_window_canvas_set
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- x_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_client_scroll"></a>gx_window_client_scroll
### <a name="scroll-window-clients"></a>Percorra clientes da janela

### <a name="prototype"></a>Prototype

```C
UINT gx_window_client_scroll(
    GX_WINDOW *window, 
    GX_VALUE x_scroll,
    GX_VALUE y_scroll);
```

### <a name="description"></a>Descrição

Este serviço desloca os clientes da janela pelo valor especificado.

### <a name="parameters"></a>Parâmetros

- **janela** Ponteiro para janela
- **x_scroll** Montante para deslocar no eixo x
- **y_scroll** Montante para rolar no eixo y

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Pergaminho de cliente de janela bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido
- **GX_INVALID_VALUE** (0x22) O valor do pergaminho não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Scroll clients of “my_window”. */
status = gx_window_client_scroll(&my_window, 10, 0);

/* If status is GX_SUCCESS the clients of window “my_window” have been scrolled. */
```

### <a name="see-also"></a>Consulte também

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_client_width_get"></a>gx_window_client_width_get
### <a name="get-window-client-width"></a>Obtenha a largura do cliente da janela

### <a name="prototype"></a>Prototype

```C
UINT gx_window_client_width_get(
    GX_WINDOW *window,
    GX_VALUE *return_width);
```

### <a name="description"></a>Descrição

Este serviço obtém a largura do cliente da janela especificada.

### <a name="parameters"></a>Parâmetros

- **janela** Ponteiro para janela
- **return_height** Ponteiro para destino para a largura do cliente

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Largura do cliente da janela bem sucedida obter
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_VALUE my_client_widthl

/* Get client width of “my_window”. */
status = gx_window_client_width_get(&my_window, &my_client_width);

/* If status is GX_SUCCESS “my_client_width” contains the client width of window “my_window”. */
```

### <a name="see-also"></a>Consulte também

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_close"></a>gx_window_close
### <a name="close-modal-window"></a>Feche a janela modal

### <a name="prototype"></a>Prototype

```C
UINT gx_window_close(GX_WINDOW *window);
```

### <a name="description"></a>Descrição

Este serviço obriga uma janela modal a separar-se do seu progenitor e a regressar do ciclo de execução modal.

### <a name="parameters"></a>Parâmetros

- **janela** Ponteiro para bloco de controlo de janela

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Janela fechada com sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Close window “my_window”. */
status = gx_window_close(&my_window);

/* If status is GX_SUCCESS window “my_window” has been closed. */
```

### <a name="see-also"></a>Consulte também

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_create"></a>gx_window_create
### <a name="create-window"></a>Criar janela

### <a name="prototype"></a>Prototype

```C
UINT gx_window_create(
    GX_WINDOW *window, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    ULONG style,
    USHORT window_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Descrição

Este serviço cria uma janela.

GX_WINDOW é derivado de GX_WIDGET e suporta todos os gx_widget serviços da API.

### <a name="parameters"></a>Parâmetros

- **janela** Ponteiro para bloco de controlo de janela
- **nome** Nome lógico da janela
- **pai** Ponteiro para widget dos pais
- **estilo** Estilo de janela. **O apêndice D** contém estilos gerais pré-definidos para todos os widgets, bem como estilos específicos de widget.
- **window_id** ID definido pela aplicação da janela
- **tamanho** Tamanho da janela

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Janela de sucesso criar
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_WINDOW my_window;

/* Create window “my_window”. */
status = gx_window_create(&my_window, "my window",
                          &my_parent_window, GX_STYLE_BORDER_RAISED,
                          MY_WINDOW_ID, &size);

/* If status is GX_SUCCESS window “my_window” has been created. */
```

### <a name="see-also"></a>Consulte também

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_draw"></a>gx_window_draw
### <a name="draw-window"></a>Desenhar janela

### <a name="prototype"></a>Prototype

```C
VOID gx_window_draw(GX_WINDOW *window);
```

### <a name="description"></a>Descrição

Este serviço desenha uma janela. Este serviço é normalmente chamado internamente durante a atualização de lona, mas também pode ser chamado de funções de desenho de janelas personalizadas.

### <a name="parameters"></a>Parâmetros

- **janela** Ponteiro para bloco de controlo de janela

### <a name="return-values"></a>Valores de devolução

- **Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a custom window draw function. */

VOID my_custom_window_draw(GX_WINDOW *window)
{
    /* Call default window draw. */
    gx_window_draw(window);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Consulte também

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_event_process"></a>gx_window_event_process
### <a name="process-window-event"></a>Evento de janela de processo

### <a name="prototype"></a>Prototype

```C
UINT gx_window_event_process(
    GX_WINDOW *window, 
    GX_EVENT *event);
```

### <a name="description"></a>Descrição

Este serviço processa um evento para esta janela.

### <a name="parameters"></a>Parâmetros

- **janela** Ponteiro para bloco de controlo de janela
- **evento** Ponteiro para o evento para processar

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Processamento bem sucedido de eventos de janela
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Call generic window event processing as part of custom event processing function. */

UINT custom_window_event_process(GX_WINDOW *window,
                                 GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
        case xyz:
            /* Insert custom event handling here */
            break;
        default:
            /* Pass all other events to the default window
            event processing */
            status = gx_window_event_process(window, event);
            break;
        }
        return status;
}
```

### <a name="see-also"></a>Consulte também

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_execute"></a>gx_window_execute
### <a name="modally-execute-a-window"></a>Modally executar uma janela

### <a name="prototype"></a>Prototype

```C
UINT gx_window_execute(
    GX_WINDOW *window,
    ULONG *return_ptr)
```

### <a name="description"></a>Descrição

Este serviço executa modally uma janela. Qualquer entrada do utilizador (eventos de caneta, etc.) fora da área do cliente da janela será ignorada. Note que esta função introduz um ciclo de execução de bloqueio contínuo e não volta ao chamador até que a execução do modelo seja terminada.

A execução modal termina quando o processamento do evento para qualquer evento recebido devolve um valor de estado não zero, ou quando a função API gx_window_close é invocada. O código de devolução de processamento de eventos não zero é devolvido ao chamador através do return_ptr passado para esta API

### <a name="parameters"></a>Parâmetros

- **janela** Ponteiro para bloco de controlo de janela
- **return_ptr** Localização para salvar o estado de saída da execução modal. Pode ser GX_NULL.

### <a name="return-values"></a>Valores de devolução

- **execução** bem sucedida GX_SUCCESS (0x00)
- **GX_SYSTEM_EVENT_RECEIVE_ERROR(0x05)** Evento de recolha da fila do evento falhou
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Execute a modal window. */
status = gx_window_execute(&my_window, &return_code);

/* If status is GX_SUCCESS the window was executed, and return_code holds the execution return code. */
```

### <a name="see-also"></a>Consulte também

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_root_create"></a>gx_window_root_create
### <a name="create-a-root-window"></a>Criar uma janela de raiz

### <a name="prototype"></a>Prototype

```C
UINT gx_window_root_create(
    GX_WINDOW_ROOT *root_window,
    GX_CONST GX_CHAR *name,
    GX_CANVAS *canvas, 
    ULONG style,
    USHORT id,
    GX_CONST GX_RECTANGLE *size)
```

### <a name="description"></a>Descrição

Este serviço cria uma janela de raiz.

### <a name="parameters"></a>Parâmetros

- **root_window** Ponteiro para bloco de controlo da janela raiz

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) criou com sucesso a janela de raiz
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- **GX_INVALID_SIZE** (0x19) Tamanho do bloco de controlo de widget inválido
- Widget **GX_ALREADY_CREATED** (0x13) já criado

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_ROOT_WINDOW root_window;
GX_CANVAS canvas;

/* Create canvas here. */

/* Create a root window */
status = gx_window_root_create(&root_window, “root”, &canvas,
GX_STYLE_BORDER_NONE, GX_NULL, &size);

/* If status is GX_SUCCESS, the “root_window” is successfully created. */
```

### <a name="see-also"></a>Consulte também

- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find

## <a name="gx_window_root_delete"></a>gx_window_root_delete
### <a name="destroy-a-root-window"></a>Destrua uma janela de raiz

### <a name="prototype"></a>Prototype

```C
UINT gx_window_root_delete(GX_WINDOW_ROOT *root_window)
```

### <a name="description"></a>Descrição

Este serviço elimina uma janela de raiz.

### <a name="parameters"></a>Parâmetros

- **root_window** Ponteiro para bloco de controlo da janela raiz

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) eliminada com sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido
- **GX_SYSTEM_MEMORY_ERROR** (0x30) A função de livre de memória não está definida

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Delete a root window */
status = gx_window_root_delete(&root_window);

/* If status is GX_SUCCESS the “root_window” is destroyed. */
```

### <a name="see-also"></a>Consulte também

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_root_event_process"></a>gx_window_root_event_process
### <a name="process-event-for-the-root-window"></a>Evento de processo para a janela raiz

### <a name="prototype"></a>Prototype

```C
UINT gx_window_root_create(
    GX_WINDOW_ROOT *root_window,
    GX_EVENT *event)
```

### <a name="description"></a>Descrição

Este serviço processa eventos para a janela de raiz especificada.

### <a name="parameters"></a>Parâmetros

- **root_window** Ponteiro para bloco de controlo da janela raiz
- **evento** Ponteiro para o evento a ser processado

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Evento de janela de raiz processado com sucesso
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Call generic root window event processing as part of custom event processing function. */

UINT custom_root_window_event_process(GX_ROOT_WINDOW *root,
                                      GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default root window
            event processing */
        status = gx_window_root_event_process(root, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Consulte também

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_root_find"></a>gx_window_root_find
### <a name="find-root-window"></a>Encontre a janela da raiz

### <a name="prototype"></a>Prototype

```C
UINT gx_window_root_find(
    GX_WIDGET *widget,
    GX_WINDOW_ROOT **return_root_window);
```

### <a name="description"></a>Descrição

Este serviço encontra a janela raiz para o widget especificado.

### <a name="parameters"></a>Parâmetros

- **widget** Ponteiro para o bloco de controlo do widget
- **return_root_window** Ponteiro para destino para janela de raiz encontrada

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Descoberta de janela de raiz bem sucedida
- **GX_FAILURE** (0x00) Janela de raiz não existe
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Find root window associated with window “my_window”. */
status = gx_window_root_find(&my_window, &root_window);

/* If status is GX_SUCCESS the “root_window” contains the root window for window “my_window”. */
```

### <a name="see-also"></a>Consulte também

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_scroll_info_get"></a>gx_window_scroll_info_get
### <a name="get-window-scroll-info"></a>Obtenha informações de pergaminho de janela

### <a name="prototype"></a>Prototype

```C
UINT gx_window_scroll_info_get(
    GX_WINDOW *window, 
    ULONG style,
    GX_SCROLL_INFO *return_scroll_info);
```

### <a name="description"></a>Descrição

Este serviço obtém a informação do pergaminho da janela.

### <a name="parameters"></a>Parâmetros

- **janela** Ponteiro para janela
- **estilo** GX_SCROLLBAR_HORIZONTAL ou GX_SCROLLBAR_VERTICAL
- **return_scroll_info** Ponteiro para destino para informações de pergaminho. A janela dos pais inicializa esta estrutura para informar a barra de deslocamento do tamanho total da janela dos pais, área visível e incremento de deslocamento e limites. A implementação padrão utiliza a área do cliente do Windows como área visível e pergaminhos por pixels, mas a implementação personalizada da janela pode utilizar os parâmetros do pergaminho. **O apêndice I** contém a definição da estrutura GX_SCROLL_INFO

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Informações de pergaminho de janela bem sucedidas obtêm
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido
- **GX_INVALID_TYPE** (0x1B) Tipo inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_SCROLL_INFO scroll_info;

/* Get scroll information for window “my_window”. */
status = gx_window_scroll_info_get(&my_window,
                    GX_SCROLLBAR_HORIZONTAL, &scroll_info);

/* If status is GX_SUCCESS the “scroll_info” contains the scroll information for window “my_window”. */
```
### <a name="see-also"></a>Consulte também

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_scrollbar_find"></a>gx_window_scrollbar_find
### <a name="find-window-scrollbar"></a>Encontre a barra de pergaminho da janela

### <a name="prototype"></a>Prototype

```C
UINT gx_window_scrollbar_find(
    GX_WINDOW *window, 
    USHORT type,
    GX_SCROLLBAR **return_scrollbar);
```

### <a name="description"></a>Descrição

Este serviço encontra a barra de deslocação para a janela especificada.

### <a name="parameters"></a>Parâmetros

- **janela** Ponteiro para janela
- **tipo** GX_TYPE_VERTICAL_SCROLL ou GX_TYPE_HORIZONTAL_SCROLL
- **return_scrollbar** Ponteiro para destino para barra de deslocamento

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Encontrar barra de pergaminho de janela bem sucedida
- **barra de** GX_NOT_FOUND (0x09) não encontrada
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido
- **GX_INVALID_TYPE** (0x1B) Tipo inválido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Find horizontal scrollbar for window “my_window”. */
status = gx_window_scrollbar_find(&my_window,
                 GX_SCROLLBAR_HORIZONTAL, &my_scrollbar);

/* If status is GX_SUCCESS the “my_scrollbar” contains the horizontal scrollbar for window “my_window”. */
```

### <a name="see-also"></a>Consulte também

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_wallpaper_get"></a>gx_window_wallpaper_get
### <a name="get-window-wallpaper"></a>Obter papel de parede da janela

### <a name="prototype"></a>Prototype

```C
UINT gx_window_wallpaper_get(
    GX_WINDOW *window,
    GX_RESOURCE_ID *return_wallpaper_id);
```

### <a name="description"></a>Descrição

Este serviço obtém o papel de parede para a janela especificada.

### <a name="parameters"></a>Parâmetros

- **janela** Ponteiro para janela
- **return_wallpaper_id** Ponteiro para destino para iD de recursos de papel de parede

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Papel de parede de janela bem sucedido obter
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
GX_RESOURCE_ID my_window_wallpaper;

/* Get wallpaper for window “my_window”. */
status = gx_window_wallpaper_get(&my_window, &my_window_wallpaper);

/* If status is GX_SUCCESS the “my_window_wallpaper” contains the wallpaper resource ID for window “my_window”. */
```

### <a name="see-also"></a>Consulte também

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_set

## <a name="gx_window_wallpaper_set"></a>gx_window_wallpaper_set
### <a name="set-window-wallpaper"></a>Definir papel de parede da janela

### <a name="prototype"></a>Prototype

```C
UINT gx_window_wallpaper_set(
    GX_WINDOW *window,
    GX_RESOURCE_ID wallpaper_id,
    GX_BOOL tile);
```

### <a name="description"></a>Descrição

Este serviço define o papel de parede para a janela especificada.

### <a name="parameters"></a>Parâmetros

- **janela** Ponteiro para janela
- **wallpaper_id** ID de recursos de papel de parede para usar
- **azulejo** Papel de parede é em azulejo se GX_TRUE, caso contrário o papel de parede não é azulejo

### <a name="return-values"></a>Valores de devolução

- **GX_SUCCESS** (0x00) Conjunto de papel de parede de janela bem sucedido
- **GX_CALLER_ERROR** (0x11) Inválido desta função
- **GX_PTR_ERROR** (0x07) Ponteiro inválido
- Widget **GX_INVALID_WIDGET** (0x12) não é válido

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="example"></a>Exemplo

```C
/* Set wallpaper for window “my_window”. */
status = gx_window_wallpaper_set(&my_window,
                                 MY_WALLPAPER_RESOURCE_ID,
                                 GX_TRUE);

/* If status is GX_SUCCESS the wallpaper for window “my_window” is set. */
```

### <a name="see-also"></a>Consulte também

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
-  gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
