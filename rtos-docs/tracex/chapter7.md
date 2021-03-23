---
title: Capítulo 7 - Azure RTOS FileX trace eventos
description: Este capítulo contém uma descrição dos eventos Azure RTOS FileX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: c3cbc945e33b87b6759c56ec1429d6bf57259bd9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827493"
---
# <a name="chapter-7---azure-rtos-filex-trace-events"></a><span data-ttu-id="025ee-103">Capítulo 7 - Azure RTOS FileX trace eventos</span><span class="sxs-lookup"><span data-stu-id="025ee-103">Chapter 7 - Azure RTOS FileX trace events</span></span>

<span data-ttu-id="025ee-104">Este capítulo contém uma descrição dos eventos Azure RTOS FileX.</span><span class="sxs-lookup"><span data-stu-id="025ee-104">This chapter contains a description of the Azure RTOS FileX events.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="025ee-105">Lista de eventos e ícones</span><span class="sxs-lookup"><span data-stu-id="025ee-105">List of Events and Icons</span></span>

<span data-ttu-id="025ee-106">**Segue-se uma lista de eventos FileX apresentados pela TraceX.**</span><span class="sxs-lookup"><span data-stu-id="025ee-106">**The following is a list of FileX events displayed by TraceX.**</span></span>

<span data-ttu-id="025ee-107">O seguinte descreve cada evento:</span><span class="sxs-lookup"><span data-stu-id="025ee-107">The following describes each event:</span></span>

| <span data-ttu-id="025ee-108">**Ícone**</span><span class="sxs-lookup"><span data-stu-id="025ee-108">**Icon**</span></span>                         | <span data-ttu-id="025ee-109">**Significado**</span><span class="sxs-lookup"><span data-stu-id="025ee-109">**Meaning**</span></span>                               |
| -------------------------------- | ----------------------------------------- |
| ![Ícone de miss cache do setor lógico interno](./media/user-guide/fx-events/image1.png)    | <span data-ttu-id="025ee-111">Falha cache do sector lógico interno</span><span class="sxs-lookup"><span data-stu-id="025ee-111">Internal Logical Sector Cache Miss</span></span> |
| ![Ícone de Cache Miss do Diretório Interno](./media/user-guide/fx-events/image2.png)    | <span data-ttu-id="025ee-113">Diretório Interno Cache Miss</span><span class="sxs-lookup"><span data-stu-id="025ee-113">Internal Directory Cache Miss</span></span> |
| ![Ícone de descarga de mídia interna](./media/user-guide/fx-events/image3.png)    | <span data-ttu-id="025ee-115">Flush de mídia interna</span><span class="sxs-lookup"><span data-stu-id="025ee-115">Internal Media Flush</span></span> |
| ![Ícone de leitura de entrada de diretório interno](./media/user-guide/fx-events/image4.png)    | <span data-ttu-id="025ee-117">Leitura de Entrada no Diretório Interno</span><span class="sxs-lookup"><span data-stu-id="025ee-117">Internal Directory Entry Read</span></span> |
| ![Ícone de escrita de entrada de diretório interno](./media/user-guide/fx-events/image5.png)    | <span data-ttu-id="025ee-119">Escrita de entrada no diretório interno</span><span class="sxs-lookup"><span data-stu-id="025ee-119">Internal Directory Entry Write</span></span> |
| ![Ícone de leitura interna I / O Motorista](./media/user-guide/fx-events/image6.png)    | <span data-ttu-id="025ee-121">Leitura interna do controlador de I/O</span><span class="sxs-lookup"><span data-stu-id="025ee-121">Internal I/O Driver Read</span></span> |
| ![Ícone de escrita interna I / O Motorista](./media/user-guide/fx-events/image7.png)    | <span data-ttu-id="025ee-123">Escrita interna do condutor de I/O</span><span class="sxs-lookup"><span data-stu-id="025ee-123">Internal I/O Driver Write</span></span> |
| ![Ícone interno de flush de i / o motorista](./media/user-guide/fx-events/image8.png)    | <span data-ttu-id="025ee-125">Flush de controlador de I/O interno</span><span class="sxs-lookup"><span data-stu-id="025ee-125">Internal I/O Driver Flush</span></span> |
| ![Ícone interno de abortar i / O motorista](./media/user-guide/fx-events/image9.png)    | <span data-ttu-id="025ee-127">Aborto interno do condutor de I/O</span><span class="sxs-lookup"><span data-stu-id="025ee-127">Internal I/O Driver Abort</span></span> |
| ![Ícone de inicialização do condutor interno I / O](./media/user-guide/fx-events/image10.png)    | <span data-ttu-id="025ee-129">Inicialização interna do controlador de I/O</span><span class="sxs-lookup"><span data-stu-id="025ee-129">Internal I/O Driver Initialize</span></span> |
| ![Ícone de leitura de bota de i / o motorista interno](./media/user-guide/fx-events/image11.png)    | <span data-ttu-id="025ee-131">Leitura interna da bota de motorista de I/O</span><span class="sxs-lookup"><span data-stu-id="025ee-131">Internal I/O Driver Boot Read</span></span> |
| ![Ícone de setores de libertação de motorista internos I / O](./media/user-guide/fx-events/image12.png)    | <span data-ttu-id="025ee-133">Sectores internos de libertação de condutores de I/O</span><span class="sxs-lookup"><span data-stu-id="025ee-133">Internal I/O Driver Release Sectors</span></span> |
| ![Ícone de escrita de bota de i / o motorista interno](./media/user-guide/fx-events/image13.png)    | <span data-ttu-id="025ee-135">Escrita interna da bota de motorista de I/O</span><span class="sxs-lookup"><span data-stu-id="025ee-135">Internal I/O Driver Boot Write</span></span> |
| ![Ícone interno I / O Condutor de condutor Des-initialize ícone](./media/user-guide/fx-events/image14.png)    | <span data-ttu-id="025ee-137">Condutor interno I / O Condutor Des-initialize</span><span class="sxs-lookup"><span data-stu-id="025ee-137">Internal I / O Driver Driver Un-initialize</span></span> |
| ![Ícone de leitura de atributos de diretório](./media/user-guide/fx-events/image15.png)    | <span data-ttu-id="025ee-139">**Leitura de Atributos de Diretório** *(fx_directory_attributes_read)*</span><span class="sxs-lookup"><span data-stu-id="025ee-139">**Directory Attributes Read** (*fx_directory_attributes_read*)</span></span> |
| ![Ícone de conjunto de atributos de diretório](./media/user-guide/fx-events/image16.png)    | <span data-ttu-id="025ee-141">**Conjunto de atributos de diretório** *(fx_directory_attributes_set)*</span><span class="sxs-lookup"><span data-stu-id="025ee-141">**Directory Attributes Set** (*fx_directory_attributes_set*)</span></span> |
| ![Diretório Criar ícone](./media/user-guide/fx-events/image17.png)    | <span data-ttu-id="025ee-143">**Diretório Criar** *(fx_directory_create)*</span><span class="sxs-lookup"><span data-stu-id="025ee-143">**Directory Create** (*fx_directory_create*)</span></span> |
| ![Diretório Padrão Obter ícone](./media/user-guide/fx-events/image18.png)    | <span data-ttu-id="025ee-145">**Diretório Padrão Obter** *(fx_directory_default_get*)</span><span class="sxs-lookup"><span data-stu-id="025ee-145">**Directory Default Get** (*fx_directory_default_get*)</span></span> |
| ![Ícone de conjunto de padrão de diretório](./media/user-guide/fx-events/image19.png)    | <span data-ttu-id="025ee-147">**Conjunto de predefinição do diretório** *(fx_directory_default_set*)</span><span class="sxs-lookup"><span data-stu-id="025ee-147">**Directory Default Set** (*fx_directory_default_set*)</span></span> |
| ![Ícone de exclusão de diretório](./media/user-guide/fx-events/image20.png)    | <span data-ttu-id="025ee-149">**Diretório Delete** *(fx_directory_delete)*</span><span class="sxs-lookup"><span data-stu-id="025ee-149">**Directory Delete** (*fx_directory_delete*)</span></span> |
| ![Ícone de primeira entrada do diretório](./media/user-guide/fx-events/image21.png)    | <span data-ttu-id="025ee-151">**Descoberta de Primeira Entrada** *(fx_directory_first_entry_find)*</span><span class="sxs-lookup"><span data-stu-id="025ee-151">**Directory First Entry Find** (*fx_directory_first_entry_find*)</span></span> |
| ![Ícone de primeira entrada completa do diretório](./media/user-guide/fx-events/image22.png)    | <span data-ttu-id="025ee-153">**Diretório Primeiro Achado de Entrada Completa** *(fx_directory_first_full_entry_find)*</span><span class="sxs-lookup"><span data-stu-id="025ee-153">**Directory First Full Entry Find** (*fx_directory_first_full_entry_find*)</span></span> |
| ![Informação do diretório Obter ícone](./media/user-guide/fx-events/image23.png)    | <span data-ttu-id="025ee-155">**Informação do Diretório Obter** *(fx_directory_information_get)*</span><span class="sxs-lookup"><span data-stu-id="025ee-155">**Directory Information Get** (*fx_directory_information_get*)</span></span> |
| ![Ícone de distância local do diretório](./media/user-guide/fx-events/image24.png)    | <span data-ttu-id="025ee-157">**Diretório Caminho Local Claro** *(fx_directory_local_path_clear)*</span><span class="sxs-lookup"><span data-stu-id="025ee-157">**Directory Local Path Clear** (*fx_directory_local_path_clear*)</span></span> |
| ![Diretório caminho local obter ícone](./media/user-guide/fx-events/image25.png)    | <span data-ttu-id="025ee-159">**Diretório Caminho Local Obter** *(fx_directory_local_path_get)*</span><span class="sxs-lookup"><span data-stu-id="025ee-159">**Directory Local Path Get** (*fx_directory_local_path_get*)</span></span> |
| ![Ícone de restauro do caminho local do diretório](./media/user-guide/fx-events/image26.png)    | <span data-ttu-id="025ee-161">**Diretório Local Path Restore** *(fx_directory_local_path_restore)*</span><span class="sxs-lookup"><span data-stu-id="025ee-161">**Directory Local Path Restore** (*fx_directory_local_path_restore*)</span></span> |
| ![Ícone do conjunto de caminhos locais do diretório](./media/user-guide/fx-events/image27.png)    | <span data-ttu-id="025ee-163">**Conjunto de caminhos locais do diretório** *(fx_directory_local_path_set)*</span><span class="sxs-lookup"><span data-stu-id="025ee-163">**Directory Local Path Set** (*fx_directory_local_path_set*)</span></span> |
| ![Diretório longo nome obter ícone](./media/user-guide/fx-events/image28.png)    | <span data-ttu-id="025ee-165">**Diretório De Longo Nome Get** *(fx_directory_long_name_get)*</span><span class="sxs-lookup"><span data-stu-id="025ee-165">**Directory Long Name Get** (*fx_directory_long_name_get*)</span></span> |
| ![Ícone de teste de nome de diretório](./media/user-guide/fx-events/image29.png)    | <span data-ttu-id="025ee-167">**Teste de nome do diretório** *(fx_directory_name_test)*</span><span class="sxs-lookup"><span data-stu-id="025ee-167">**Directory Name Test** (*fx_directory_name_test*)</span></span> |
| ![Diretório Próximo Entrada Encontrar ícone](./media/user-guide/fx-events/image30.png)    | <span data-ttu-id="025ee-169">**Diretório Próximo Achado de Entrada** *(fx_directory_next_entry_find)*</span><span class="sxs-lookup"><span data-stu-id="025ee-169">**Directory Next Entry Find** (*fx_directory_next_entry_find*)</span></span> |
| ![Diretório Próximo Ícone de entrada completa](./media/user-guide/fx-events/image31.png)    | <span data-ttu-id="025ee-171">**Diretório Next Full Entry Find** *(fx_directory_next_full_entry_find)*</span><span class="sxs-lookup"><span data-stu-id="025ee-171">**Directory Next Full Entry Find** (*fx_directory_next_full_entry_find*)</span></span> |
| ![Ícone de renome de diretório](./media/user-guide/fx-events/image32.png)    | <span data-ttu-id="025ee-173">**Diretório Renome** *(fx_directory_rename)*</span><span class="sxs-lookup"><span data-stu-id="025ee-173">**Directory Rename** (*fx_directory_rename*)</span></span> |
| ![Diretório Nome Curto Obter ícone](./media/user-guide/fx-events/image33.png)    | <span data-ttu-id="025ee-175">**Diretório Nome Curto Obter** *(fx_directory_short_name_get)*</span><span class="sxs-lookup"><span data-stu-id="025ee-175">**Directory Short Name Get** (*fx_directory_short_name_get*)</span></span> |
| ![Ícone de atribuição de ficheiros](./media/user-guide/fx-events/image34.png)    | <span data-ttu-id="025ee-177">**Atribuição de ficheiros** *(fx_file_allocate)*</span><span class="sxs-lookup"><span data-stu-id="025ee-177">**File Allocate** (*fx_file_allocate*)</span></span> |
| ![Atributos de arquivo Ler ícone](./media/user-guide/fx-events/image35.png)    | <span data-ttu-id="025ee-179">**Leitura de atributos de** arquivo *(fx_file_attributes_read)*</span><span class="sxs-lookup"><span data-stu-id="025ee-179">**File Attributes Read** (*fx_file_attributes_read*)</span></span> |
| ![Ícone de conjunto de atributos de arquivo](./media/user-guide/fx-events/image36.png)    | <span data-ttu-id="025ee-181">**Conjunto de atributos de** ficheiro *(fx_file_attributes_set)*</span><span class="sxs-lookup"><span data-stu-id="025ee-181">**File Attributes Set** (*fx_file_attributes_set*)</span></span> |
| ![Ícone de alocação de melhor esforço de arquivo](./media/user-guide/fx-events/image37.png)    | <span data-ttu-id="025ee-183">**Alocação de melhor esforço do arquivo** *(fx_file_best_effort_allocate)*</span><span class="sxs-lookup"><span data-stu-id="025ee-183">**File Best Effort Allocate** (*fx_file_best_effort_allocate*)</span></span> |
| ![Ícone de fecho de arquivo](./media/user-guide/fx-events/image38.png)    | <span data-ttu-id="025ee-185">**Fecho de Ficheiros** *(fx_file_close)*</span><span class="sxs-lookup"><span data-stu-id="025ee-185">**File Close** (*fx_file_close*)</span></span> |
| ![Ícone de criar ficheiro](./media/user-guide/fx-events/image39.png)    | <span data-ttu-id="025ee-187">**Criação de Ficheiros** *(fx_file_create)*</span><span class="sxs-lookup"><span data-stu-id="025ee-187">**File Create** (*fx_file_create*)</span></span> |
| ![Ícone de definição de tempo de data de arquivo](./media/user-guide/fx-events/image40.png)    | <span data-ttu-id="025ee-189">**Definição de hora de data de** arquivo *(fx_file_date_time_set*)</span><span class="sxs-lookup"><span data-stu-id="025ee-189">**File Date Time Set** (*fx_file_date_time_set*)</span></span> |
| ![Ícone de exclusão de ficheiro](./media/user-guide/fx-events/image41.png)    | <span data-ttu-id="025ee-191">**Excluir ficheiros** *(fx_file_delete)*</span><span class="sxs-lookup"><span data-stu-id="025ee-191">**File Delete** (*fx_file_delete*)</span></span> |
| ![Ícone de abertura de arquivo](./media/user-guide/fx-events/image42.png)    | <span data-ttu-id="025ee-193">**Arquivo Aberto** *(fx_file_open)*</span><span class="sxs-lookup"><span data-stu-id="025ee-193">**File Open** (*fx_file_open*)</span></span> |
| ![Ícone de leitura de arquivo](./media/user-guide/fx-events/image43.png)    | <span data-ttu-id="025ee-195">**Leitura de Arquivo** *(fx_file_read)*</span><span class="sxs-lookup"><span data-stu-id="025ee-195">**File Read** (*fx_file_read*)</span></span> |
| ![Ícone de procura relativa de arquivo](./media/user-guide/fx-events/image44.png)    | <span data-ttu-id="025ee-197">**Procura relativa de arquivo** *(fx_file_relative_seek)*</span><span class="sxs-lookup"><span data-stu-id="025ee-197">**File Relative Seek** (*fx_file_relative_seek*)</span></span> |
| ![Ícone de renome de arquivo](./media/user-guide/fx-events/image45.png)    | <span data-ttu-id="025ee-199">**Renomear o Ficheiro** *(fx_file_rename)*</span><span class="sxs-lookup"><span data-stu-id="025ee-199">**File Rename** (*fx_file_rename*)</span></span> |
| ![Ícone de procura de arquivo](./media/user-guide/fx-events/image46.png)    | <span data-ttu-id="025ee-201">**Procura de Ficheiros** *(fx_file_seek)*</span><span class="sxs-lookup"><span data-stu-id="025ee-201">**File Seek** (*fx_file_seek*)</span></span> |
| ![Ícone de Truncate de arquivo](./media/user-guide/fx-events/image47.png)    | <span data-ttu-id="025ee-203">**File Truncate** *(fx_file_truncate)*</span><span class="sxs-lookup"><span data-stu-id="025ee-203">**File Truncate** (*fx_file_truncate*)</span></span> |
| ![Ícone de lançamento de truncato de arquivo](./media/user-guide/fx-events/image48.png)    | <span data-ttu-id="025ee-205">**Lançamento do Truncato de Ficheiros** *(fx_file_truncate_release)*</span><span class="sxs-lookup"><span data-stu-id="025ee-205">**File Truncate Release** (*fx_file_truncate_release*)</span></span> |
| ![Ícone de escrita de arquivo](./media/user-guide/fx-events/image49.png)    | <span data-ttu-id="025ee-207">**Escrita de Ficheiros** *(fx_file_write)*</span><span class="sxs-lookup"><span data-stu-id="025ee-207">**File Write** (*fx_file_write*)</span></span> |
| ![Ícone de aborto de mídia](./media/user-guide/fx-events/image50.png)    | <span data-ttu-id="025ee-209">**Media Abort** *(fx_media_abort)*</span><span class="sxs-lookup"><span data-stu-id="025ee-209">**Media Abort** (*fx_media_abort*)</span></span> |
| ![Ícone invalidado de cache de mídia](./media/user-guide/fx-events/image51.png)    | <span data-ttu-id="025ee-211">**Media Cache Invalidado** *(fx_media_cache_invalidate)*</span><span class="sxs-lookup"><span data-stu-id="025ee-211">**Media Cache Invalidate** (*fx_media_cache_invalidate*)</span></span> |
| ![Ícone de verificação de mídia](./media/user-guide/fx-events/image52.png)    | <span data-ttu-id="025ee-213">**Verificação de meios** de *comunicação (fx_media_check)*</span><span class="sxs-lookup"><span data-stu-id="025ee-213">**Media Check** (*fx_media_check*)</span></span> |
| ![\*Ícone de close de mídia](./media/user-guide/fx-events/image53.png)    | <span data-ttu-id="025ee-215">**Media Close** (*fx_media_close)*</span><span class="sxs-lookup"><span data-stu-id="025ee-215">**Media Close** (*fx_media_close*)</span></span> |
| ![Ícone de descarga de mídia](./media/user-guide/fx-events/image54.png)    | <span data-ttu-id="025ee-217">**Media Flush** *(fx_media_flush)*</span><span class="sxs-lookup"><span data-stu-id="025ee-217">**Media Flush** (*fx_media_flush*)</span></span> |
| ![Ícone de formato de mídia](./media/user-guide/fx-events/image55.png)    | <span data-ttu-id="025ee-219">**Formato de Mídia** *(fx_media_format)*</span><span class="sxs-lookup"><span data-stu-id="025ee-219">**Media Format** (*fx_media_format*)</span></span> |
| ![Ícone do Media Open](./media/user-guide/fx-events/image56.png)    | <span data-ttu-id="025ee-221">**Media Open** *(fx_media_open)*</span><span class="sxs-lookup"><span data-stu-id="025ee-221">**Media Open** (*fx_media_open*)</span></span> |
| ![Ícone de leitura de mídia](./media/user-guide/fx-events/image57.png)    | <span data-ttu-id="025ee-223">**Media Read** *(fx_media_read)*</span><span class="sxs-lookup"><span data-stu-id="025ee-223">**Media Read** (*fx_media_read*)</span></span> |
| ![Ícone disponível do espaço de mídia](./media/user-guide/fx-events/image58.png)    | <span data-ttu-id="025ee-225">**Espaço de Mídia Disponível** *(fx_media_space_available)*</span><span class="sxs-lookup"><span data-stu-id="025ee-225">**Media Space Available** (*fx_media_space_available*)</span></span> |
| ![Ícone de volume de mídia Obter](./media/user-guide/fx-events/image59.png)    | <span data-ttu-id="025ee-227">**Volume de Mídia Get** *(fx_media_volume_get)*</span><span class="sxs-lookup"><span data-stu-id="025ee-227">**Media Volume Get** (*fx_media_volume_get*)</span></span> |
| ![Ícone de conjunto de volume de mídia](./media/user-guide/fx-events/image60.png)    | <span data-ttu-id="025ee-229">**Conjunto de volume de mídia** *(fx_media_volume_set)*</span><span class="sxs-lookup"><span data-stu-id="025ee-229">**Media Volume Set** (*fx_media_volume_set*)</span></span> |
| ![Ícone de escrita de mídia](./media/user-guide/fx-events/image61.png)    | <span data-ttu-id="025ee-231">**Media Write** *(fx_media_write)*</span><span class="sxs-lookup"><span data-stu-id="025ee-231">**Media Write** (*fx_media_write*)</span></span> |
| ![Ícone de data do sistema](./media/user-guide/fx-events/image62.png)    | <span data-ttu-id="025ee-233">**Data do Sistema Obter** *(fx_system_date_get)*</span><span class="sxs-lookup"><span data-stu-id="025ee-233">**System Date Get** (*fx_system_date_get*)</span></span> |
| ![Ícone de definição de data do sistema](./media/user-guide/fx-events/image63.png)    | <span data-ttu-id="025ee-235">**Definição da data do sistema** *(fx_system_date_set)*</span><span class="sxs-lookup"><span data-stu-id="025ee-235">**System Date Set** (*fx_system_date_set*)</span></span> |
| ![Ícone inicialize o sistema](./media/user-guide/fx-events/image64.png)    | <span data-ttu-id="025ee-237">**Inicialização do Sistema** *(fx_system_initialize)*</span><span class="sxs-lookup"><span data-stu-id="025ee-237">**System Initialize** (*fx_system_initialize*)</span></span> |
| ![Ícone de tempo de sistema obter](./media/user-guide/fx-events/image65.png)    | <span data-ttu-id="025ee-239">**System Time Get** *(fx_system_time_get)*</span><span class="sxs-lookup"><span data-stu-id="025ee-239">**System Time Get** (*fx_system_time_get*)</span></span> |
| ![Ícone de definição de tempo do sistema](./media/user-guide/fx-events/image66.png)    | <span data-ttu-id="025ee-241">**Conjunto de tempo do sistema** *(fx_system_time_set)*</span><span class="sxs-lookup"><span data-stu-id="025ee-241">**System Time Set** (*fx_system_time_set*)</span></span> |
| ![Diretório unicodisco criar ícone](./media/user-guide/fx-events/image67.png)    | <span data-ttu-id="025ee-243">**Unicode Directory Create** *(fx_unicode_directory_create)*</span><span class="sxs-lookup"><span data-stu-id="025ee-243">**Unicode Directory Create** (*fx_unicode_directory_create*)</span></span> |
| ![Ícone de renomeação do diretório unicode](./media/user-guide/fx-events/image68.png)    | <span data-ttu-id="025ee-245">**Unicode Directory Rename** *(fx_unicode_directory_rename)*</span><span class="sxs-lookup"><span data-stu-id="025ee-245">**Unicode Directory Rename** (*fx_unicode_directory_rename*)</span></span> |
| ![Ícone de coleção de ficheiro unicode](./media/user-guide/fx-events/image69.png)    | <span data-ttu-id="025ee-247">**Unicode File Create** *(fx_unicode_file_create)*</span><span class="sxs-lookup"><span data-stu-id="025ee-247">**Unicode File Create** (*fx_unicode_file_create*)</span></span> |
| ![Ícone de renomeação de ficheiro unicode](./media/user-guide/fx-events/image70.png)    | <span data-ttu-id="025ee-249">**Unicode File Rename** *(fx_unicode_file_rename)*</span><span class="sxs-lookup"><span data-stu-id="025ee-249">**Unicode File Rename** (*fx_unicode_file_rename*)</span></span> |
| ![Unicode Lenght Obter ícone](./media/user-guide/fx-events/image71.png)    | <span data-ttu-id="025ee-251">**Unicode Lenght Get** *(fx_unicode_length_get)*</span><span class="sxs-lookup"><span data-stu-id="025ee-251">**Unicode Lenght Get** (*fx_unicode_length_get*)</span></span> |
| ![Unicode Name Get icon](./media/user-guide/fx-events/image72.png)    | <span data-ttu-id="025ee-253">**Unicode Name Get** *(fx_unicode_name_get)*</span><span class="sxs-lookup"><span data-stu-id="025ee-253">**Unicode Name Get** (*fx_unicode_name_get*)</span></span> |
| ![Unicode Nome Curto Obter ícone](./media/user-guide/fx-events/image73.png)    | <span data-ttu-id="025ee-255">**Unicode Short Name Get** *(fx_unicode_short_name_get)*</span><span class="sxs-lookup"><span data-stu-id="025ee-255">**Unicode Short Name Get** (*fx_unicode_short_name_get*)</span></span> |

## <a name="event-descriptions"></a><span data-ttu-id="025ee-256">Descrições do evento</span><span class="sxs-lookup"><span data-stu-id="025ee-256">Event Descriptions</span></span>

<span data-ttu-id="025ee-257">O seguinte descreve cada evento individual.</span><span class="sxs-lookup"><span data-stu-id="025ee-257">The following describes each individual event.</span></span>

### <a name="internal-logical-sector-cache-miss"></a><span data-ttu-id="025ee-258">Falha cache do sector lógico interno</span><span class="sxs-lookup"><span data-stu-id="025ee-258">Internal Logical Sector Cache Miss</span></span> 

#### <a name="internal-logical-sector-cache-miss"></a><span data-ttu-id="025ee-259">Falha de cache do setor lógico interno</span><span class="sxs-lookup"><span data-stu-id="025ee-259">Internal logical sector cache miss</span></span>

<span data-ttu-id="025ee-260">**Ícone** ![ Cache de setor lógico interno falha ícone](./media/user-guide/fx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-260">**Icon** ![Internal logical sector cache miss icon](./media/user-guide/fx-events/image1.png)</span></span>

<span data-ttu-id="025ee-261">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-261">**Description**</span></span>

<span data-ttu-id="025ee-262">Este evento representa uma falha interna do sector lógico do FileX.</span><span class="sxs-lookup"><span data-stu-id="025ee-262">This event represents an internal FileX logical sector cache miss.</span></span>

<span data-ttu-id="025ee-263">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-263">**Information Fields**</span></span>

- <span data-ttu-id="025ee-264">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-264">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-265">Info Field 2: Sector.</span><span class="sxs-lookup"><span data-stu-id="025ee-265">Info Field 2: Sector.</span></span>
- <span data-ttu-id="025ee-266">Info Field 3: Total de falhas.</span><span class="sxs-lookup"><span data-stu-id="025ee-266">Info Field 3: Total misses.</span></span>
- <span data-ttu-id="025ee-267">Info Field 4: Tamanho cache.</span><span class="sxs-lookup"><span data-stu-id="025ee-267">Info Field 4: Cache size.</span></span>

### <a name="internal-directory-cache-miss"></a><span data-ttu-id="025ee-268">Diretório Interno Cache Miss</span><span class="sxs-lookup"><span data-stu-id="025ee-268">Internal Directory Cache Miss</span></span>

#### <a name="internal-directory-cache-miss"></a><span data-ttu-id="025ee-269">Falha de cache de diretório interno</span><span class="sxs-lookup"><span data-stu-id="025ee-269">Internal directory cache miss</span></span>

<span data-ttu-id="025ee-270">**Ícone** ![ Ícone de falta de cache de diretório interno](./media/user-guide/fx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-270">**Icon** ![Internal directory cache miss icon](./media/user-guide/fx-events/image2.png)</span></span>

<span data-ttu-id="025ee-271">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-271">**Description**</span></span> 

<span data-ttu-id="025ee-272">Este evento representa uma falha interna do diretório do FileX.</span><span class="sxs-lookup"><span data-stu-id="025ee-272">This event represents an internal FileX directory cache miss.</span></span>

<span data-ttu-id="025ee-273">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-273">**Information Fields**</span></span>

- <span data-ttu-id="025ee-274">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-274">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-275">Info Field 2: Total de falhas.</span><span class="sxs-lookup"><span data-stu-id="025ee-275">Info Field 2: Total misses.</span></span>
- <span data-ttu-id="025ee-276">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-276">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-277">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-277">Info Field 4: Not used.</span></span>

### <a name="internal-media-flush"></a><span data-ttu-id="025ee-278">Flush de mídia interna</span><span class="sxs-lookup"><span data-stu-id="025ee-278">Internal Media Flush</span></span> 

#### <a name="internal-media-flush"></a><span data-ttu-id="025ee-279">Flush de mídia interna</span><span class="sxs-lookup"><span data-stu-id="025ee-279">Internal media flush</span></span>

<span data-ttu-id="025ee-280">**Ícone** ![ Ícone de descarga de mídia interna](./media/user-guide/fx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-280">**Icon** ![Internal media flush icon](./media/user-guide/fx-events/image3.png)</span></span>

<span data-ttu-id="025ee-281">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-281">**Description**</span></span>

<span data-ttu-id="025ee-282">Este evento representa um flush interno de media FileX.</span><span class="sxs-lookup"><span data-stu-id="025ee-282">This event represents an internal FileX media flush.</span></span>

<span data-ttu-id="025ee-283">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-283">**Information Fields**</span></span>

- <span data-ttu-id="025ee-284">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-284">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-285">Info Field 2: Número de sectores sujos.</span><span class="sxs-lookup"><span data-stu-id="025ee-285">Info Field 2: Number of dirty sectors.</span></span>
- <span data-ttu-id="025ee-286">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-286">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-287">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-287">Info Field 4: Not used.</span></span>


### <a name="internal-directory-entry-read"></a><span data-ttu-id="025ee-288">Leitura de Entrada no Diretório Interno</span><span class="sxs-lookup"><span data-stu-id="025ee-288">Internal Directory Entry Read</span></span> 

#### <a name="internal-directory-entry-read"></a><span data-ttu-id="025ee-289">Leitura de entrada de diretório interno</span><span class="sxs-lookup"><span data-stu-id="025ee-289">Internal directory entry read</span></span>

<span data-ttu-id="025ee-290">**Ícone** ![ Ícone de leitura de diretório interno](./media/user-guide/fx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-290">**Icon** ![Internal directory entry read icon](./media/user-guide/fx-events/image4.png)</span></span>

<span data-ttu-id="025ee-291">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-291">**Description**</span></span>

<span data-ttu-id="025ee-292">Este evento representa um evento interno de leitura de diretório filex.</span><span class="sxs-lookup"><span data-stu-id="025ee-292">This event represents an internal FileX directory entry read event.</span></span>

<span data-ttu-id="025ee-293">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-293">**Information Fields**</span></span>

- <span data-ttu-id="025ee-294">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-294">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-295">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-295">Info Field 2: Not used.</span></span>
- <span data-ttu-id="025ee-296">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-296">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-297">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-297">Info Field 4: Not used.</span></span>

### <a name="internal-directory-entry-write"></a><span data-ttu-id="025ee-298">Escrita de entrada no diretório interno</span><span class="sxs-lookup"><span data-stu-id="025ee-298">Internal Directory Entry Write</span></span>

#### <a name="internal-directory-entry-write"></a><span data-ttu-id="025ee-299">Escrita de entrada de diretório interno</span><span class="sxs-lookup"><span data-stu-id="025ee-299">Internal directory entry write</span></span>

<span data-ttu-id="025ee-300">**Ícone** ![ Ícone de escrita de diretório interno](./media/user-guide/fx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-300">**Icon** ![Internal directory entry write icon](./media/user-guide/fx-events/image5.png)</span></span>

<span data-ttu-id="025ee-301">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-301">**Description**</span></span>

<span data-ttu-id="025ee-302">Este evento representa um evento interno de escrita de diretório filex.</span><span class="sxs-lookup"><span data-stu-id="025ee-302">This event represents an internal FileX directory entry write event.</span></span>

<span data-ttu-id="025ee-303">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-303">**Information Fields**</span></span>

- <span data-ttu-id="025ee-304">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-304">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-305">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-305">Info Field 2: Not used.</span></span>
- <span data-ttu-id="025ee-306">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-306">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-307">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-307">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-read"></a><span data-ttu-id="025ee-308">Leitura interna do controlador de I/O</span><span class="sxs-lookup"><span data-stu-id="025ee-308">Internal I/O Driver Read</span></span> 

#### <a name="internal-io-driver-read"></a><span data-ttu-id="025ee-309">Leitura interna do controlador de I/O</span><span class="sxs-lookup"><span data-stu-id="025ee-309">Internal I/O driver read</span></span> 

<span data-ttu-id="025ee-310">**Ícone** ![ Ícone de leitura de i/o interno](./media/user-guide/fx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-310">**Icon** ![Internal I / O driver read icon](./media/user-guide/fx-events/image6.png)</span></span>

<span data-ttu-id="025ee-311">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-311">**Description**</span></span> 

<span data-ttu-id="025ee-312">Este evento representa um evento interno de leitura de controlador FileX I/O.</span><span class="sxs-lookup"><span data-stu-id="025ee-312">This event represents an internal FileX I/O driver read event.</span></span>

<span data-ttu-id="025ee-313">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-313">**Information Fields**</span></span>

- <span data-ttu-id="025ee-314">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-314">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-315">Info Field 2: Sector.</span><span class="sxs-lookup"><span data-stu-id="025ee-315">Info Field 2: Sector.</span></span>
- <span data-ttu-id="025ee-316">Info Campo 3: Número de sectores.</span><span class="sxs-lookup"><span data-stu-id="025ee-316">Info Field 3: Number of sectors.</span></span>
- <span data-ttu-id="025ee-317">Info Field 4: Ponteiro tampão.</span><span class="sxs-lookup"><span data-stu-id="025ee-317">Info Field 4: Buffer pointer.</span></span>

### <a name="internal-io-driver-write"></a><span data-ttu-id="025ee-318">Escrita interna do condutor de I/O</span><span class="sxs-lookup"><span data-stu-id="025ee-318">Internal I/O Driver Write</span></span> 

#### <a name="internal-io-driver-write"></a><span data-ttu-id="025ee-319">O condutor de I/O interno escreve</span><span class="sxs-lookup"><span data-stu-id="025ee-319">Internal I/O driver write</span></span> 

<span data-ttu-id="025ee-320">**Ícone** ![ Ícone de escrita interna I/O](./media/user-guide/fx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-320">**Icon** ![Internal I / O driver write icon](./media/user-guide/fx-events/image7.png)</span></span>

<span data-ttu-id="025ee-321">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-321">**Description**</span></span> 

<span data-ttu-id="025ee-322">Este evento representa um evento interno de escrita do controlador FileX I/O.</span><span class="sxs-lookup"><span data-stu-id="025ee-322">This event represents an internal FileX I/O driver write event.</span></span>

<span data-ttu-id="025ee-323">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-323">**Information Fields**</span></span>

- <span data-ttu-id="025ee-324">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-324">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-325">Info Field 2: Sector.</span><span class="sxs-lookup"><span data-stu-id="025ee-325">Info Field 2: Sector.</span></span>
- <span data-ttu-id="025ee-326">Info Campo 3: Número de sectores.</span><span class="sxs-lookup"><span data-stu-id="025ee-326">Info Field 3: Number of sectors.</span></span>
- <span data-ttu-id="025ee-327">Info Field 4: Ponteiro tampão.</span><span class="sxs-lookup"><span data-stu-id="025ee-327">Info Field 4: Buffer pointer.</span></span>

### <a name="internal-io-driver-flush"></a><span data-ttu-id="025ee-328">Flush de controlador de I/O interno</span><span class="sxs-lookup"><span data-stu-id="025ee-328">Internal I/O Driver Flush</span></span> 

#### <a name="internal-io-driver-flush"></a><span data-ttu-id="025ee-329">Flush do condutor de I/O interno</span><span class="sxs-lookup"><span data-stu-id="025ee-329">Internal I/O driver flush</span></span> 

<span data-ttu-id="025ee-330">**Ícone** ![ Ícone de descarga do controlador interno I /O](./media/user-guide/fx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-330">**Icon** ![Internal I / O driver flush icon](./media/user-guide/fx-events/image8.png)</span></span>

<span data-ttu-id="025ee-331">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-331">**Description**</span></span> 

<span data-ttu-id="025ee-332">Este evento representa um evento interno de flush do controlador FileX I/O.</span><span class="sxs-lookup"><span data-stu-id="025ee-332">This event represents an internal FileX I/O driver flush event.</span></span>

<span data-ttu-id="025ee-333">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-333">**Information Fields**</span></span>

- <span data-ttu-id="025ee-334">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-334">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-335">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-335">Info Field 2: Not used.</span></span>
- <span data-ttu-id="025ee-336">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-336">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-337">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-337">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-abort"></a><span data-ttu-id="025ee-338">Aborto interno do condutor de I/O</span><span class="sxs-lookup"><span data-stu-id="025ee-338">Internal I/O Driver Abort</span></span> 

#### <a name="internal-io-dirver-abort"></a><span data-ttu-id="025ee-339">I/O interno dirver abortar</span><span class="sxs-lookup"><span data-stu-id="025ee-339">Internal I/O dirver abort</span></span>

<span data-ttu-id="025ee-340">**Ícone** ![ Ícone de aborto de motorista interno I/O](./media/user-guide/fx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-340">**Icon** ![Internal I / O driver abort icon](./media/user-guide/fx-events/image9.png)</span></span>

<span data-ttu-id="025ee-341">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-341">**Description**</span></span>

<span data-ttu-id="025ee-342">Este evento representa um evento interno de abortar o controlador FileX I/O.</span><span class="sxs-lookup"><span data-stu-id="025ee-342">This event represents an internal FileX I/O driver abort event.</span></span>

<span data-ttu-id="025ee-343">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-343">**Information Fields**</span></span>

- <span data-ttu-id="025ee-344">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-344">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-345">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-345">Info Field 2: Not used.</span></span>
- <span data-ttu-id="025ee-346">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-346">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-347">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-347">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-initialize"></a><span data-ttu-id="025ee-348">Inicialização interna do controlador de I/O</span><span class="sxs-lookup"><span data-stu-id="025ee-348">Internal I/O Driver Initialize</span></span> 

#### <a name="internal-io-driver-initialize"></a><span data-ttu-id="025ee-349">Inicialização do controlador de I/S interno</span><span class="sxs-lookup"><span data-stu-id="025ee-349">Internal I/O driver initialize</span></span> 

<span data-ttu-id="025ee-350">**Ícone** ![ Ícone inicializo do condutor interno I/O](./media/user-guide/fx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-350">**Icon** ![Internal I / O driver initialize icon](./media/user-guide/fx-events/image10.png)</span></span>

<span data-ttu-id="025ee-351">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-351">**Description**</span></span> 

<span data-ttu-id="025ee-352">Este evento representa um evento de inicialização do controlador FileX I/O interno.</span><span class="sxs-lookup"><span data-stu-id="025ee-352">This event represents an internal FileX I/O driver initialize event.</span></span>

<span data-ttu-id="025ee-353">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-353">**Information Fields**</span></span>

- <span data-ttu-id="025ee-354">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-354">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-355">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-355">Info Field 2: Not used.</span></span>
- <span data-ttu-id="025ee-356">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-356">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-357">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-357">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-boot-sector-read"></a><span data-ttu-id="025ee-358">Leitura interna do setor de arranque de i/o</span><span class="sxs-lookup"><span data-stu-id="025ee-358">Internal I/O Driver Boot Sector Read</span></span> 

#### <a name="internal-io-driver-boot-sector-read"></a><span data-ttu-id="025ee-359">O setor de arranque de i/S interno lido</span><span class="sxs-lookup"><span data-stu-id="025ee-359">Internal I/O driver boot sector read</span></span> 

<span data-ttu-id="025ee-360">**Ícone** ![ Setor de botas de motorista interno I /O ler ícone](./media/user-guide/fx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-360">**Icon** ![Internal I / O driver boot sector read icon](./media/user-guide/fx-events/image11.png)</span></span>

<span data-ttu-id="025ee-361">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-361">**Description**</span></span> 

<span data-ttu-id="025ee-362">Este evento representa um evento interno do sector de arranque do filex I/O.</span><span class="sxs-lookup"><span data-stu-id="025ee-362">This event represents an internal FileX I/O driver boot sector read event.</span></span>

<span data-ttu-id="025ee-363">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-363">**Information Fields**</span></span>

- <span data-ttu-id="025ee-364">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-364">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-365">Info Field 2: Ponteiro tampão.</span><span class="sxs-lookup"><span data-stu-id="025ee-365">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="025ee-366">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-366">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-367">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-367">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-release-sectors"></a><span data-ttu-id="025ee-368">Sectores internos de libertação de condutores de I/O</span><span class="sxs-lookup"><span data-stu-id="025ee-368">Internal I/O Driver Release Sectors</span></span> 

#### <a name="internal-io-driver-release-sectors"></a><span data-ttu-id="025ee-369">Sectores internos de libertação de condutores de I/O</span><span class="sxs-lookup"><span data-stu-id="025ee-369">Internal I/O driver release sectors</span></span> 

<span data-ttu-id="025ee-370">**Ícone** ![ Ícone de setores de libertação de motorista interno i/O](./media/user-guide/fx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-370">**Icon** ![Internal I / O driver release sectors icon](./media/user-guide/fx-events/image12.png)</span></span>

<span data-ttu-id="025ee-371">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-371">**Description**</span></span> 

<span data-ttu-id="025ee-372">Este evento representa um evento interno de lançamento de controlador filex I/O.</span><span class="sxs-lookup"><span data-stu-id="025ee-372">This event represents an internal FileX I/O driver release sectors event.</span></span>

<span data-ttu-id="025ee-373">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-373">**Information Fields**</span></span>

- <span data-ttu-id="025ee-374">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-374">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-375">Info Field 2: Sector.</span><span class="sxs-lookup"><span data-stu-id="025ee-375">Info Field 2: Sector.</span></span>
- <span data-ttu-id="025ee-376">Info Campo 3: Número de sectores.</span><span class="sxs-lookup"><span data-stu-id="025ee-376">Info Field 3: Number of sectors.</span></span>
- <span data-ttu-id="025ee-377">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-377">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-boot-sector-write"></a><span data-ttu-id="025ee-378">E/O Setor de Arranque de Motorista Interno Escrever</span><span class="sxs-lookup"><span data-stu-id="025ee-378">Internal I/O Driver Boot Sector Write</span></span>

#### <a name="internal-io-driver-boot-sector-write"></a><span data-ttu-id="025ee-379">O setor de arranque de i/S interno escreve</span><span class="sxs-lookup"><span data-stu-id="025ee-379">Internal I/O driver boot sector write</span></span> 

<span data-ttu-id="025ee-380">**Ícone** ![ Interior I / O setor de botas de motorista escrever ícone](./media/user-guide/fx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-380">**Icon** ![Internal I / O driver boot sector write icon](./media/user-guide/fx-events/image13.png)</span></span>

<span data-ttu-id="025ee-381">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-381">**Description**</span></span> 

<span data-ttu-id="025ee-382">Este evento representa um evento interno do sector de arranque do filex I/O.</span><span class="sxs-lookup"><span data-stu-id="025ee-382">This event represents an internal FileX I/O driver boot sector write event.</span></span>

<span data-ttu-id="025ee-383">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-383">**Information Fields**</span></span>

- <span data-ttu-id="025ee-384">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-384">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-385">Info Field 2: Ponteiro tampão.</span><span class="sxs-lookup"><span data-stu-id="025ee-385">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="025ee-386">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-386">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-387">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-387">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="025ee-388">Condutor interno de I/O Des-initialize</span><span class="sxs-lookup"><span data-stu-id="025ee-388">Internal I/O Driver Un-initialize</span></span> 

#### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="025ee-389">Condutor interno de I/O desa inicializar</span><span class="sxs-lookup"><span data-stu-id="025ee-389">Internal I/O driver un-initialize</span></span> 

<span data-ttu-id="025ee-390">**Ícone** ![ Ícone interno I / O do condutor des-initialize](./media/user-guide/fx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-390">**Icon** ![Internal I / O driver un-initialize icon](./media/user-guide/fx-events/image14.png)</span></span>

<span data-ttu-id="025ee-391">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-391">**Description**</span></span> 

<span data-ttu-id="025ee-392">Este evento representa um evento interno de des-initialize do controlador FileX I/O.</span><span class="sxs-lookup"><span data-stu-id="025ee-392">This event represents an internal FileX I/O driver un-initialize event.</span></span>

<span data-ttu-id="025ee-393">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-393">**Information Fields**</span></span>

- <span data-ttu-id="025ee-394">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-394">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-395">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-395">Info Field 2: Not used.</span></span>
- <span data-ttu-id="025ee-396">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-396">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-397">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-397">Info Field 4: Not used.</span></span>
</blockquote></td>

### <a name="directory-attributes-read"></a><span data-ttu-id="025ee-398">Leitura de atributos de diretório</span><span class="sxs-lookup"><span data-stu-id="025ee-398">Directory Attributes Read</span></span> 

#### <a name="fx_directory_attributes_read"></a><span data-ttu-id="025ee-399">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="025ee-399">fx_directory_attributes_read</span></span> 

<span data-ttu-id="025ee-400">**Ícone** ![ Ícone de leitura de atributos de diretório](./media/user-guide/fx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-400">**Icon** ![Directory attributes read icon](./media/user-guide/fx-events/image15.png)</span></span>

<span data-ttu-id="025ee-401">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-401">**Description**</span></span> 

<span data-ttu-id="025ee-402">Este evento representa um evento de atributos de diretório.</span><span class="sxs-lookup"><span data-stu-id="025ee-402">This event represents a directory attributes read event.</span></span>

<span data-ttu-id="025ee-403">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-403">**Information Fields**</span></span>

- <span data-ttu-id="025ee-404">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-404">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-405">Info Field 2: Ponteiro para o nome do diretório.</span><span class="sxs-lookup"><span data-stu-id="025ee-405">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="025ee-406">Info Field 3: Atributos mapa bit:</span><span class="sxs-lookup"><span data-stu-id="025ee-406">Info Field 3: Attributes bit map:</span></span>

  | <span data-ttu-id="025ee-407">Atributo</span><span class="sxs-lookup"><span data-stu-id="025ee-407">Attribute</span></span>                         | <span data-ttu-id="025ee-408">Valor</span><span class="sxs-lookup"><span data-stu-id="025ee-408">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="025ee-409">Só de Leitura</span><span class="sxs-lookup"><span data-stu-id="025ee-409">Read Only</span></span>                        | <span data-ttu-id="025ee-410">(0x01)</span><span class="sxs-lookup"><span data-stu-id="025ee-410">(0x01)</span></span>  |
  |  <span data-ttu-id="025ee-411">Oculto</span><span class="sxs-lookup"><span data-stu-id="025ee-411">Hidden</span></span>                           | <span data-ttu-id="025ee-412">(0x02)</span><span class="sxs-lookup"><span data-stu-id="025ee-412">(0x02)</span></span>  |
  |  <span data-ttu-id="025ee-413">Sistema</span><span class="sxs-lookup"><span data-stu-id="025ee-413">System</span></span>                           | <span data-ttu-id="025ee-414">(0x04)</span><span class="sxs-lookup"><span data-stu-id="025ee-414">(0x04)</span></span>  |
  |  <span data-ttu-id="025ee-415">Volume</span><span class="sxs-lookup"><span data-stu-id="025ee-415">Volume</span></span>                           | <span data-ttu-id="025ee-416">(0x08)</span><span class="sxs-lookup"><span data-stu-id="025ee-416">(0x08)</span></span>  |
  |  <span data-ttu-id="025ee-417">Diretório</span><span class="sxs-lookup"><span data-stu-id="025ee-417">Directory</span></span>                        | <span data-ttu-id="025ee-418">(0x10)</span><span class="sxs-lookup"><span data-stu-id="025ee-418">(0x10)</span></span>  |
  |  <span data-ttu-id="025ee-419">Arquivo</span><span class="sxs-lookup"><span data-stu-id="025ee-419">Archive</span></span>                          | <span data-ttu-id="025ee-420">(0x20)</span><span class="sxs-lookup"><span data-stu-id="025ee-420">(0x20)</span></span>  |
- <span data-ttu-id="025ee-421">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-421">Info Field 4: Not used.</span></span>

### <a name="directory-attributes-set"></a><span data-ttu-id="025ee-422">Conjunto de atributos de diretório</span><span class="sxs-lookup"><span data-stu-id="025ee-422">Directory Attributes Set</span></span> 

#### <a name="fx_directory_attributes_set"></a><span data-ttu-id="025ee-423">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="025ee-423">fx_directory_attributes_set</span></span> 

<span data-ttu-id="025ee-424">**Ícone** ![ Ícone de conjunto de atributos](./media/user-guide/fx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-424">**Icon** ![Attributes set icon](./media/user-guide/fx-events/image16.png)</span></span>

<span data-ttu-id="025ee-425">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-425">**Description**</span></span> 

<span data-ttu-id="025ee-426">Este evento representa um diretório de um evento de atributos de diretório.</span><span class="sxs-lookup"><span data-stu-id="025ee-426">This event represents a directory a directory attributes set event.</span></span>

<span data-ttu-id="025ee-427">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-427">**Information Fields**</span></span>

- <span data-ttu-id="025ee-428">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-428">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-429">Info Field 2: Ponteiro para o nome do diretório.</span><span class="sxs-lookup"><span data-stu-id="025ee-429">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="025ee-430">Info Field 3: Atributos mapa bit:</span><span class="sxs-lookup"><span data-stu-id="025ee-430">Info Field 3: Attributes bit map:</span></span>

  |  <span data-ttu-id="025ee-431">Atributo</span><span class="sxs-lookup"><span data-stu-id="025ee-431">Attribute</span></span>                        | <span data-ttu-id="025ee-432">Valor</span><span class="sxs-lookup"><span data-stu-id="025ee-432">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="025ee-433">Só de Leitura</span><span class="sxs-lookup"><span data-stu-id="025ee-433">Read Only</span></span>                        | <span data-ttu-id="025ee-434">(0x01)</span><span class="sxs-lookup"><span data-stu-id="025ee-434">(0x01)</span></span>  |
  |  <span data-ttu-id="025ee-435">Oculto</span><span class="sxs-lookup"><span data-stu-id="025ee-435">Hidden</span></span>                           | <span data-ttu-id="025ee-436">(0x02)</span><span class="sxs-lookup"><span data-stu-id="025ee-436">(0x02)</span></span>  |
  |  <span data-ttu-id="025ee-437">Sistema</span><span class="sxs-lookup"><span data-stu-id="025ee-437">System</span></span>                           | <span data-ttu-id="025ee-438">(0x04)</span><span class="sxs-lookup"><span data-stu-id="025ee-438">(0x04)</span></span>  |
  |  <span data-ttu-id="025ee-439">Arquivo</span><span class="sxs-lookup"><span data-stu-id="025ee-439">Archive</span></span>                          | <span data-ttu-id="025ee-440">(0x20)</span><span class="sxs-lookup"><span data-stu-id="025ee-440">(0x20)</span></span>  |
- <span data-ttu-id="025ee-441">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-441">Info Field 4: Not used.</span></span>

### <a name="directory-create"></a><span data-ttu-id="025ee-442">Criar Diretório</span><span class="sxs-lookup"><span data-stu-id="025ee-442">Directory Create</span></span> 

#### <a name="fx_directory_create"></a><span data-ttu-id="025ee-443">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="025ee-443">fx_directory_create</span></span>

<span data-ttu-id="025ee-444">**Ícone** ![ Diretório criar ícone](./media/user-guide/fx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-444">**Icon** ![Directory create icon](./media/user-guide/fx-events/image17.png)</span></span>

<span data-ttu-id="025ee-445">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-445">**Description**</span></span> 

<span data-ttu-id="025ee-446">Este evento representa um evento de criação de diretório.</span><span class="sxs-lookup"><span data-stu-id="025ee-446">This event represents a directory create event.</span></span>

<span data-ttu-id="025ee-447">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-447">**Information Fields**</span></span>

- <span data-ttu-id="025ee-448">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-448">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-449">Info Field 2: Ponteiro para o nome do diretório.</span><span class="sxs-lookup"><span data-stu-id="025ee-449">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="025ee-450">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-450">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-451">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-451">Info Field 4: Not used.</span></span>

### <a name="directory-default-get"></a><span data-ttu-id="025ee-452">Diretório Predefinido Obter</span><span class="sxs-lookup"><span data-stu-id="025ee-452">Directory Default Get</span></span> 

#### <a name="fx_directory_default_get"></a><span data-ttu-id="025ee-453">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="025ee-453">fx_directory_default_get</span></span> 

<span data-ttu-id="025ee-454">**Ícone** ![ Diretório padrão obter ícone](./media/user-guide/fx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-454">**Icon** ![Directory default get icon](./media/user-guide/fx-events/image18.png)</span></span>

<span data-ttu-id="025ee-455">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-455">**Description**</span></span> 

<span data-ttu-id="025ee-456">Este evento representa um evento definido por padrão de diretório.</span><span class="sxs-lookup"><span data-stu-id="025ee-456">This event represents a directory default set event.</span></span>

<span data-ttu-id="025ee-457">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-457">**Information Fields**</span></span>

- <span data-ttu-id="025ee-458">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-458">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-459">Info Field 2: Ponteiro para devolver o nome do caminho.</span><span class="sxs-lookup"><span data-stu-id="025ee-459">Info Field 2: Pointer to return path name.</span></span>
- <span data-ttu-id="025ee-460">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-460">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-461">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-461">Info Field 4: Not used.</span></span>

### <a name="directory-default-set"></a><span data-ttu-id="025ee-462">Conjunto de predefinição do diretório</span><span class="sxs-lookup"><span data-stu-id="025ee-462">Directory Default Set</span></span> 

#### <a name="fx_directory_default_set"></a><span data-ttu-id="025ee-463">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="025ee-463">fx_directory_default_set</span></span> 

<span data-ttu-id="025ee-464">**Ícone** ![ Ícone de conjunto de padrão de diretório](./media/user-guide/fx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-464">**Icon** ![Directory default set icon](./media/user-guide/fx-events/image19.png)</span></span>

<span data-ttu-id="025ee-465">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-465">**Description**</span></span> 

<span data-ttu-id="025ee-466">Este evento representa um evento definido por padrão de diretório.</span><span class="sxs-lookup"><span data-stu-id="025ee-466">This event represents a directory default set event.</span></span>

<span data-ttu-id="025ee-467">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-467">**Information Fields**</span></span>

- <span data-ttu-id="025ee-468">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-468">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-469">Info Field 2: Ponteiro para novo nome do caminho predefinido.</span><span class="sxs-lookup"><span data-stu-id="025ee-469">Info Field 2: Pointer to new default path name.</span></span>
- <span data-ttu-id="025ee-470">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-470">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-471">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-471">Info Field 4: Not used.</span></span>

### <a name="directory-delete"></a><span data-ttu-id="025ee-472">Diretório Delete</span><span class="sxs-lookup"><span data-stu-id="025ee-472">Directory Delete</span></span> 

#### <a name="fx_directory_delete"></a><span data-ttu-id="025ee-473">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="025ee-473">fx_directory_delete</span></span>

<span data-ttu-id="025ee-474">**Ícone** ![ Ícone de exclusão de diretório](./media/user-guide/fx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-474">**Icon** ![Directory delete icon](./media/user-guide/fx-events/image20.png)</span></span>

<span data-ttu-id="025ee-475">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-475">**Description**</span></span> 

<span data-ttu-id="025ee-476">Este evento representa um evento de exclusão de diretório.</span><span class="sxs-lookup"><span data-stu-id="025ee-476">This event represents a directory delete event.</span></span>

<span data-ttu-id="025ee-477">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-477">**Information Fields**</span></span>
- <span data-ttu-id="025ee-478">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-478">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-479">Info Field 2: Ponteiro para o nome do diretório.</span><span class="sxs-lookup"><span data-stu-id="025ee-479">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="025ee-480">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-480">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-481">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-481">Info Field 4: Not used.</span></span>

### <a name="directory-first-entry-find"></a><span data-ttu-id="025ee-482">Descoberta de primeira entrada do diretório</span><span class="sxs-lookup"><span data-stu-id="025ee-482">Directory First Entry Find</span></span> 

#### <a name="fx_directory_first_entry_find"></a><span data-ttu-id="025ee-483">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="025ee-483">fx_directory_first_entry_find</span></span>

<span data-ttu-id="025ee-484">**Ícone** ![ Primeiro diretório encontrar ícone](./media/user-guide/fx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-484">**Icon** ![Directory first entry find icon](./media/user-guide/fx-events/image21.png)</span></span>

<span data-ttu-id="025ee-485">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-485">**Description**</span></span> 

<span data-ttu-id="025ee-486">Este evento representa um evento de primeira entrada.</span><span class="sxs-lookup"><span data-stu-id="025ee-486">This event represents a directory first entry find event.</span></span>

<span data-ttu-id="025ee-487">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-487">**Information Fields**</span></span>

- <span data-ttu-id="025ee-488">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-488">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-489">Info Field 2: Ponteiro para o nome do diretório.</span><span class="sxs-lookup"><span data-stu-id="025ee-489">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="025ee-490">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-490">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-491">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-491">Info Field 4: Not used.</span></span>

### <a name="directory-first-full-entry-find"></a><span data-ttu-id="025ee-492">Primeira descoberta de entrada completa do diretório</span><span class="sxs-lookup"><span data-stu-id="025ee-492">Directory First Full Entry Find</span></span> 

#### <a name="fx_directory_first_full_entry_find"></a><span data-ttu-id="025ee-493">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="025ee-493">fx_directory_first_full_entry_find</span></span>

<span data-ttu-id="025ee-494">**Ícone** ![ Primeiro diretório de entrada completa encontrar ícone](./media/user-guide/fx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-494">**Icon** ![Directory first full entry find icon](./media/user-guide/fx-events/image22.png)</span></span>

<span data-ttu-id="025ee-495">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-495">**Description**</span></span> 

<span data-ttu-id="025ee-496">Este evento representa um evento de primeira entrada completa.</span><span class="sxs-lookup"><span data-stu-id="025ee-496">This event represents a directory first full entry find event.</span></span>

<span data-ttu-id="025ee-497">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-497">**Information Fields**</span></span>

- <span data-ttu-id="025ee-498">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-498">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-499">Info Field 2: Ponteiro para o nome do diretório.</span><span class="sxs-lookup"><span data-stu-id="025ee-499">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="025ee-500">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-500">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-501">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-501">Info Field 4: Not used.</span></span>

### <a name="directory-information-get"></a><span data-ttu-id="025ee-502">Informação do Diretório Obter</span><span class="sxs-lookup"><span data-stu-id="025ee-502">Directory Information Get</span></span> 

#### <a name="fx_directory_information_get"></a><span data-ttu-id="025ee-503">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="025ee-503">fx_directory_information_get</span></span>

<span data-ttu-id="025ee-504">**Ícone** ![ Informação de diretório obter ícone](./media/user-guide/fx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-504">**Icon** ![Directory information get icon](./media/user-guide/fx-events/image23.png)</span></span>

<span data-ttu-id="025ee-505">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-505">**Description**</span></span> 

<span data-ttu-id="025ee-506">Este evento representa um evento de informação de diretório.</span><span class="sxs-lookup"><span data-stu-id="025ee-506">This event represents a directory information get event.</span></span>

<span data-ttu-id="025ee-507">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-507">**Information Fields**</span></span>

- <span data-ttu-id="025ee-508">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-508">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-509">Info Field 2: Ponteiro para o nome do diretório.</span><span class="sxs-lookup"><span data-stu-id="025ee-509">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="025ee-510">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-510">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-511">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-511">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-clear"></a><span data-ttu-id="025ee-512">Diretório Caminho Local Claro</span><span class="sxs-lookup"><span data-stu-id="025ee-512">Directory Local Path Clear</span></span> 

#### <a name="fx_directory_local_path_clear"></a><span data-ttu-id="025ee-513">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="025ee-513">fx_directory_local_path_clear</span></span>

<span data-ttu-id="025ee-514">**Ícone** ![ Ícone claro do caminho local do diretório](./media/user-guide/fx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-514">**Icon** ![Directory local path clear icon](./media/user-guide/fx-events/image24.png)</span></span>

<span data-ttu-id="025ee-515">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-515">**Description**</span></span> 

<span data-ttu-id="025ee-516">Este evento representa um diretório local evento claro.</span><span class="sxs-lookup"><span data-stu-id="025ee-516">This event represents a directory local path clear event.</span></span>

<span data-ttu-id="025ee-517">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-517">**Information Fields**</span></span>

- <span data-ttu-id="025ee-518">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-518">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-519">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-519">Info Field 2: Not used.</span></span>
- <span data-ttu-id="025ee-520">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-520">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-521">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-521">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-get"></a><span data-ttu-id="025ee-522">Diretório Caminho Local Obter</span><span class="sxs-lookup"><span data-stu-id="025ee-522">Directory Local Path Get</span></span> 

#### <a name="fx_directory_local_path_get"></a><span data-ttu-id="025ee-523">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="025ee-523">fx_directory_local_path_get</span></span>

<span data-ttu-id="025ee-524">**Ícone** ![ Diretório caminho local obter ícone](./media/user-guide/fx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-524">**Icon** ![Directory local path get icon](./media/user-guide/fx-events/image25.png)</span></span>

<span data-ttu-id="025ee-525">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-525">**Description**</span></span> 

<span data-ttu-id="025ee-526">Este evento representa um diretório local obter evento.</span><span class="sxs-lookup"><span data-stu-id="025ee-526">This event represents a directory local path get event.</span></span>

<span data-ttu-id="025ee-527">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-527">**Information Fields**</span></span>

- <span data-ttu-id="025ee-528">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-528">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-529">Info Field 2: Ponteiro para devolver o nome do caminho.</span><span class="sxs-lookup"><span data-stu-id="025ee-529">Info Field 2: Pointer to return path name.</span></span>
- <span data-ttu-id="025ee-530">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-530">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-531">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-531">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-restore"></a><span data-ttu-id="025ee-532">Restauração do Caminho Local do Diretório</span><span class="sxs-lookup"><span data-stu-id="025ee-532">Directory Local Path Restore</span></span> 

#### <a name="fx_directory_local_path_restore"></a><span data-ttu-id="025ee-533">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="025ee-533">fx_directory_local_path_restore</span></span>

<span data-ttu-id="025ee-534">**Ícone** ![ Ícone de restauro do caminho local do diretório](./media/user-guide/fx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-534">**Icon** ![Directory local path restore icon](./media/user-guide/fx-events/image26.png)</span></span>

<span data-ttu-id="025ee-535">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-535">**Description**</span></span> 

<span data-ttu-id="025ee-536">Este evento representa um evento de restauração do percurso local.</span><span class="sxs-lookup"><span data-stu-id="025ee-536">This event represents a directory local path restore event.</span></span>

<span data-ttu-id="025ee-537">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-537">**Information Fields**</span></span>

- <span data-ttu-id="025ee-538">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-538">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-539">Info Field 2: Ponteiro para a estrutura do caminho local.</span><span class="sxs-lookup"><span data-stu-id="025ee-539">Info Field 2: Pointer to local path structure.</span></span>
- <span data-ttu-id="025ee-540">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-540">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-541">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-541">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-set"></a><span data-ttu-id="025ee-542">Conjunto de caminhos locais do diretório</span><span class="sxs-lookup"><span data-stu-id="025ee-542">Directory Local Path Set</span></span> 

#### <a name="fx_directory_local_path_set"></a><span data-ttu-id="025ee-543">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="025ee-543">fx_directory_local_path_set</span></span>

<span data-ttu-id="025ee-544">**Ícone** ![ Ícone de conjunto de caminho local diretório](./media/user-guide/fx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-544">**Icon** ![Directory local path set icon](./media/user-guide/fx-events/image27.png)</span></span>

<span data-ttu-id="025ee-545">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-545">**Description**</span></span> 

<span data-ttu-id="025ee-546">Este evento representa um evento de diretório local.</span><span class="sxs-lookup"><span data-stu-id="025ee-546">This event represents a directory local path set event.</span></span>

<span data-ttu-id="025ee-547">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-547">**Information Fields**</span></span>

- <span data-ttu-id="025ee-548">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-548">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-549">Info Field 2: Ponteiro para a estrutura do caminho local.</span><span class="sxs-lookup"><span data-stu-id="025ee-549">Info Field 2: Pointer to local path structure.</span></span>
- <span data-ttu-id="025ee-550">Info Field 3: Ponteiro para novo nome do caminho.</span><span class="sxs-lookup"><span data-stu-id="025ee-550">Info Field 3: Pointer to new path name.</span></span>
- <span data-ttu-id="025ee-551">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-551">Info Field 4: Not used.</span></span>

### <a name="directory-long-name-get"></a><span data-ttu-id="025ee-552">Diretório Longo Nome Obter</span><span class="sxs-lookup"><span data-stu-id="025ee-552">Directory Long Name Get</span></span> 

#### <a name="fx_directory_long_name_get"></a><span data-ttu-id="025ee-553">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="025ee-553">fx_directory_long_name_get</span></span>

<span data-ttu-id="025ee-554">**Ícone** ![ Diretório longo nome obter ícone](./media/user-guide/fx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-554">**Icon** ![Directory long name get icon](./media/user-guide/fx-events/image28.png)</span></span>

<span data-ttu-id="025ee-555">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-555">**Description**</span></span> 

<span data-ttu-id="025ee-556">Este evento representa um evento de nome longo do diretório.</span><span class="sxs-lookup"><span data-stu-id="025ee-556">This event represents a directory long name get event.</span></span>

<span data-ttu-id="025ee-557">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-557">**Information Fields**</span></span>

- <span data-ttu-id="025ee-558">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-558">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-559">Info Field 2: Ponteiro para nome de ficheiro curto.</span><span class="sxs-lookup"><span data-stu-id="025ee-559">Info Field 2: Pointer to short file name.</span></span>
- <span data-ttu-id="025ee-560">Info Field 3: Ponteiro para o nome do ficheiro longo.</span><span class="sxs-lookup"><span data-stu-id="025ee-560">Info Field 3: Pointer to long file name.</span></span>
- <span data-ttu-id="025ee-561">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-561">Info Field 4: Not used.</span></span>

### <a name="directory-name-test"></a><span data-ttu-id="025ee-562">Teste de nome de diretório</span><span class="sxs-lookup"><span data-stu-id="025ee-562">Directory Name Test</span></span> 

#### <a name="fx_directory_name_test"></a><span data-ttu-id="025ee-563">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="025ee-563">fx_directory_name_test</span></span>

<span data-ttu-id="025ee-564">**Ícone** ![ Ícone de teste de nome de diretório](./media/user-guide/fx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-564">**Icon** ![Directory name test icon](./media/user-guide/fx-events/image29.png)</span></span>

<span data-ttu-id="025ee-565">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-565">**Description**</span></span> 

<span data-ttu-id="025ee-566">Este evento representa um evento de teste de nome de diretório.</span><span class="sxs-lookup"><span data-stu-id="025ee-566">This event represents a directory name test event.</span></span>

<span data-ttu-id="025ee-567">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-567">**Information Fields**</span></span>

- <span data-ttu-id="025ee-568">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-568">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-569">Info Field 2: Ponteiro para o nome do diretório.</span><span class="sxs-lookup"><span data-stu-id="025ee-569">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="025ee-570">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-570">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-571">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-571">Info Field 4: Not used.</span></span>

### <a name="directory-next-entry-find"></a><span data-ttu-id="025ee-572">Diretório Próximo Encontro de Entrada</span><span class="sxs-lookup"><span data-stu-id="025ee-572">Directory Next Entry Find</span></span> 

#### <a name="fx_directory_next_entry_find"></a><span data-ttu-id="025ee-573">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="025ee-573">fx_directory_next_entry_find</span></span>

<span data-ttu-id="025ee-574">**Ícone** ![ Diretório próxima entrada encontrar ícone](./media/user-guide/fx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-574">**Icon** ![Directory next entry find icon](./media/user-guide/fx-events/image30.png)</span></span>

<span data-ttu-id="025ee-575">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-575">**Description**</span></span> 

<span data-ttu-id="025ee-576">Este evento representa um evento de entrada seguinte.</span><span class="sxs-lookup"><span data-stu-id="025ee-576">This event represents a directory next entry find event.</span></span>

<span data-ttu-id="025ee-577">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-577">**Information Fields**</span></span>

- <span data-ttu-id="025ee-578">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-578">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-579">Info Field 2: Ponteiro para o nome do diretório.</span><span class="sxs-lookup"><span data-stu-id="025ee-579">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="025ee-580">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-580">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-581">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-581">Info Field 4: Not used.</span></span>

### <a name="directory-next-full-entry-find"></a><span data-ttu-id="025ee-582">Diretório Próximo Encontro de Entrada Completa</span><span class="sxs-lookup"><span data-stu-id="025ee-582">Directory Next Full Entry Find</span></span> 

#### <a name="fx_directory_next_full_entry_find"></a><span data-ttu-id="025ee-583">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="025ee-583">fx_directory_next_full_entry_find</span></span>

<span data-ttu-id="025ee-584">**Ícone** ![ Diretório próxima entrada completa encontrar ícone](./media/user-guide/fx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-584">**Icon** ![Directory next full entry find icon](./media/user-guide/fx-events/image31.png)</span></span>

<span data-ttu-id="025ee-585">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-585">**Description**</span></span>

<span data-ttu-id="025ee-586">Este evento representa um evento de entrada completa no próximo diretório.</span><span class="sxs-lookup"><span data-stu-id="025ee-586">This event represents a directory next full entry find event.</span></span>

<span data-ttu-id="025ee-587">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-587">**Information Fields**</span></span>

- <span data-ttu-id="025ee-588">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-588">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-589">Info Field 2: Ponteiro para o nome do diretório.</span><span class="sxs-lookup"><span data-stu-id="025ee-589">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="025ee-590">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-590">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-591">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-591">Info Field 4: Not used.</span></span>

### <a name="directory-rename"></a><span data-ttu-id="025ee-592">Renomeador de Diretório</span><span class="sxs-lookup"><span data-stu-id="025ee-592">Directory Rename</span></span> 

#### <a name="fx_directory_rename-event"></a><span data-ttu-id="025ee-593">evento fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="025ee-593">fx_directory_rename event</span></span>

<span data-ttu-id="025ee-594">**Ícone** ![ Ícone de renome de diretório](./media/user-guide/fx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-594">**Icon** ![Directory rename icon](./media/user-guide/fx-events/image32.png)</span></span>

<span data-ttu-id="025ee-595">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-595">**Description**</span></span>

<span data-ttu-id="025ee-596">Este evento representa um evento de renomeação de diretório.</span><span class="sxs-lookup"><span data-stu-id="025ee-596">This event represents a directory rename event.</span></span>

<span data-ttu-id="025ee-597">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-597">**Information Fields**</span></span>

- <span data-ttu-id="025ee-598">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-598">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-599">Info Field 2: Ponteiro para o nome do diretório antigo.</span><span class="sxs-lookup"><span data-stu-id="025ee-599">Info Field 2: Pointer to old directory name.</span></span>
- <span data-ttu-id="025ee-600">Info Field 3: Ponteiro para novo nome do diretório.</span><span class="sxs-lookup"><span data-stu-id="025ee-600">Info Field 3: Pointer to new directory name.</span></span>
- <span data-ttu-id="025ee-601">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-601">Info Field 4: Not used.</span></span>

### <a name="directory-short-name-get"></a><span data-ttu-id="025ee-602">Diretório Nome Curto Obter</span><span class="sxs-lookup"><span data-stu-id="025ee-602">Directory Short Name Get</span></span> 

#### <a name="fx_directory_short_name_get"></a><span data-ttu-id="025ee-603">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="025ee-603">fx_directory_short_name_get</span></span>

<span data-ttu-id="025ee-604">**Ícone** ![ Diretório nome curto obter ícone](./media/user-guide/fx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-604">**Icon** ![Directory short name get icon](./media/user-guide/fx-events/image33.png)</span></span>

<span data-ttu-id="025ee-605">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-605">**Description**</span></span>

<span data-ttu-id="025ee-606">Este evento representa um evento de nome curto de diretório.</span><span class="sxs-lookup"><span data-stu-id="025ee-606">This event represents a directory short name get event.</span></span>

<span data-ttu-id="025ee-607">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-607">**Information Fields**</span></span> 

- <span data-ttu-id="025ee-608">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-608">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-609">Info Field 2: Ponteiro para o nome do ficheiro longo.</span><span class="sxs-lookup"><span data-stu-id="025ee-609">Info Field 2: Pointer to long file name.</span></span>
- <span data-ttu-id="025ee-610">Info Field 3: Ponteiro para nome de ficheiro curto.</span><span class="sxs-lookup"><span data-stu-id="025ee-610">Info Field 3: Pointer to short file name.</span></span>
- <span data-ttu-id="025ee-611">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-611">Info Field 4: Not used.</span></span>

### <a name="file-allocate"></a><span data-ttu-id="025ee-612">Atribuição de ficheiros</span><span class="sxs-lookup"><span data-stu-id="025ee-612">File Allocate</span></span> 

#### <a name="fx_file_allocate"></a><span data-ttu-id="025ee-613">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="025ee-613">fx_file_allocate</span></span>

<span data-ttu-id="025ee-614">**Ícone** ![ Ícone de atribuição de arquivo](./media/user-guide/fx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-614">**Icon** ![File allocate icon](./media/user-guide/fx-events/image34.png)</span></span>

<span data-ttu-id="025ee-615">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-615">**Description**</span></span>

<span data-ttu-id="025ee-616">Este evento representa um evento de atribuição de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="025ee-616">This event represents a file allocate event.</span></span>

<span data-ttu-id="025ee-617">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-617">**Information Fields**</span></span>

- <span data-ttu-id="025ee-618">Info Field 1: Ponteiro para o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="025ee-618">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="025ee-619">Info Field 2: Tamanho solicitado.</span><span class="sxs-lookup"><span data-stu-id="025ee-619">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="025ee-620">Info Field 3: Tamanho atual.</span><span class="sxs-lookup"><span data-stu-id="025ee-620">Info Field 3: Current size.</span></span>
- <span data-ttu-id="025ee-621">Info Field 4: Novo tamanho.</span><span class="sxs-lookup"><span data-stu-id="025ee-621">Info Field 4: New size.</span></span>

### <a name="file-attributes-read"></a><span data-ttu-id="025ee-622">Leitura de atributos de arquivo</span><span class="sxs-lookup"><span data-stu-id="025ee-622">File Attributes Read</span></span> 

#### <a name="fx_file_attributes_read"></a><span data-ttu-id="025ee-623">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="025ee-623">fx_file_attributes_read</span></span>

<span data-ttu-id="025ee-624">**Ícone** ![ Ícone de leitura de atributos de arquivo](./media/user-guide/fx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-624">**Icon** ![File attributes read icon](./media/user-guide/fx-events/image35.png)</span></span>

<span data-ttu-id="025ee-625">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-625">**Description**</span></span>

<span data-ttu-id="025ee-626">Este evento representa um evento de leitura de atributos de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="025ee-626">This event represents a file attributes read event.</span></span>

<span data-ttu-id="025ee-627">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-627">**Information Fields**</span></span>

- <span data-ttu-id="025ee-628">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-628">Info Field 1: Pointer to the media.</span></span> 
- <span data-ttu-id="025ee-629">Info Field 2: Atributos mapa bit:</span><span class="sxs-lookup"><span data-stu-id="025ee-629">Info Field 2: Attributes bit map:</span></span>

  |  <span data-ttu-id="025ee-630">Atributo</span><span class="sxs-lookup"><span data-stu-id="025ee-630">Attribut</span></span>                         | <span data-ttu-id="025ee-631">Valor</span><span class="sxs-lookup"><span data-stu-id="025ee-631">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="025ee-632">Só de Leitura</span><span class="sxs-lookup"><span data-stu-id="025ee-632">Read Only</span></span>                        | <span data-ttu-id="025ee-633">(0x01)</span><span class="sxs-lookup"><span data-stu-id="025ee-633">(0x01)</span></span>  |
  |  <span data-ttu-id="025ee-634">Oculto</span><span class="sxs-lookup"><span data-stu-id="025ee-634">Hidden</span></span>                           | <span data-ttu-id="025ee-635">(0x02)</span><span class="sxs-lookup"><span data-stu-id="025ee-635">(0x02)</span></span>  |
  |  <span data-ttu-id="025ee-636">Sistema</span><span class="sxs-lookup"><span data-stu-id="025ee-636">System</span></span>                           | <span data-ttu-id="025ee-637">(0x04)</span><span class="sxs-lookup"><span data-stu-id="025ee-637">(0x04)</span></span>  |
  |  <span data-ttu-id="025ee-638">Volume</span><span class="sxs-lookup"><span data-stu-id="025ee-638">Volume</span></span>                           | <span data-ttu-id="025ee-639">(0x08)</span><span class="sxs-lookup"><span data-stu-id="025ee-639">(0x08)</span></span>  |
  |  <span data-ttu-id="025ee-640">Diretório</span><span class="sxs-lookup"><span data-stu-id="025ee-640">Directory</span></span>                        | <span data-ttu-id="025ee-641">(0x10)</span><span class="sxs-lookup"><span data-stu-id="025ee-641">(0x10)</span></span>  |
  |  <span data-ttu-id="025ee-642">Arquivo</span><span class="sxs-lookup"><span data-stu-id="025ee-642">Archive</span></span>                          | <span data-ttu-id="025ee-643">(0x20)</span><span class="sxs-lookup"><span data-stu-id="025ee-643">(0x20)</span></span>  |
- <span data-ttu-id="025ee-644">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-644">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-645">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-645">Info Field 4: Not used.</span></span>

### <a name="file-attributes-set"></a><span data-ttu-id="025ee-646">Conjunto de atributos de arquivo</span><span class="sxs-lookup"><span data-stu-id="025ee-646">File Attributes Set</span></span> 

#### <a name="fx_file_attributes_set"></a><span data-ttu-id="025ee-647">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="025ee-647">fx_file_attributes_set</span></span>

<span data-ttu-id="025ee-648">**Ícone** ![ Ícone de conjunto de atributos de arquivo](./media/user-guide/fx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-648">**Icon** ![File attributes set icon](./media/user-guide/fx-events/image36.png)</span></span>

<span data-ttu-id="025ee-649">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-649">**Description**</span></span> 

<span data-ttu-id="025ee-650">Este evento representa um evento de conjunto de atributos de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="025ee-650">This event represents a file attributes set event.</span></span>

<span data-ttu-id="025ee-651">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-651">**Information Fields**</span></span>

- <span data-ttu-id="025ee-652">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-652">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-653">Info Field 2: Ponteiro para o nome do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="025ee-653">Info Field 2: Pointer to file name.</span></span> 
- <span data-ttu-id="025ee-654">Info Field 3: Atributos mapa bit:</span><span class="sxs-lookup"><span data-stu-id="025ee-654">Info Field 3: Attributes bit map:</span></span>

  | <span data-ttu-id="025ee-655">Atributo</span><span class="sxs-lookup"><span data-stu-id="025ee-655">Attribute</span></span>                         | <span data-ttu-id="025ee-656">Valor</span><span class="sxs-lookup"><span data-stu-id="025ee-656">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="025ee-657">Só de Leitura</span><span class="sxs-lookup"><span data-stu-id="025ee-657">Read Only</span></span>                        | <span data-ttu-id="025ee-658">(0x01)</span><span class="sxs-lookup"><span data-stu-id="025ee-658">(0x01)</span></span>  |
  |  <span data-ttu-id="025ee-659">Oculto</span><span class="sxs-lookup"><span data-stu-id="025ee-659">Hidden</span></span>                           | <span data-ttu-id="025ee-660">(0x02)</span><span class="sxs-lookup"><span data-stu-id="025ee-660">(0x02)</span></span>  |
  |  <span data-ttu-id="025ee-661">Sistema</span><span class="sxs-lookup"><span data-stu-id="025ee-661">System</span></span>                           | <span data-ttu-id="025ee-662">(0x04)</span><span class="sxs-lookup"><span data-stu-id="025ee-662">(0x04)</span></span>  |
  |  <span data-ttu-id="025ee-663">Arquivo</span><span class="sxs-lookup"><span data-stu-id="025ee-663">Archive</span></span>                          | <span data-ttu-id="025ee-664">(0x20)</span><span class="sxs-lookup"><span data-stu-id="025ee-664">(0x20)</span></span>  |
- <span data-ttu-id="025ee-665">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-665">Info Field 4: Not used.</span></span>

### <a name="file-best-effort-allocate"></a><span data-ttu-id="025ee-666">Alocação de melhor esforço do arquivo</span><span class="sxs-lookup"><span data-stu-id="025ee-666">File Best Effort Allocate</span></span> 

#### <a name="fx_file_best_effort_allocate"></a><span data-ttu-id="025ee-667">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="025ee-667">fx_file_best_effort_allocate</span></span>

<span data-ttu-id="025ee-668">**Ícone** ![ Arquivo melhor esforço alocar ícone](./media/user-guide/fx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-668">**Icon** ![File best effort allocate icon](./media/user-guide/fx-events/image37.png)</span></span>

<span data-ttu-id="025ee-669">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-669">**Description**</span></span> 

<span data-ttu-id="025ee-670">Este evento representa um evento de melhor esforço de arquivo.</span><span class="sxs-lookup"><span data-stu-id="025ee-670">This event represents a file best effort allocate event.</span></span>

<span data-ttu-id="025ee-671">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-671">**Information Fields**</span></span>

- <span data-ttu-id="025ee-672">Info Field 1: Ponteiro para o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="025ee-672">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="025ee-673">Info Field 2: Tamanho solicitado.</span><span class="sxs-lookup"><span data-stu-id="025ee-673">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="025ee-674">Info Field 3: Tamanho real atribuído.</span><span class="sxs-lookup"><span data-stu-id="025ee-674">Info Field 3: Actual size allocated.</span></span>
- <span data-ttu-id="025ee-675">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-675">Info Field 4: Not used.</span></span>

### <a name="file-close"></a><span data-ttu-id="025ee-676">Arquivo Fechar</span><span class="sxs-lookup"><span data-stu-id="025ee-676">File Close</span></span> 

#### <a name="fx_file_close"></a><span data-ttu-id="025ee-677">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="025ee-677">fx_file_close</span></span>

<span data-ttu-id="025ee-678">**Ícone** ![ Ícone de fecho de arquivo](./media/user-guide/fx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-678">**Icon** ![File close icon](./media/user-guide/fx-events/image38.png)</span></span>

<span data-ttu-id="025ee-679">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-679">**Description**</span></span> 

<span data-ttu-id="025ee-680">Este evento representa um evento de encerramento de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="025ee-680">This event represents a file close event.</span></span>

<span data-ttu-id="025ee-681">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-681">**Information Fields**</span></span>

- <span data-ttu-id="025ee-682">Info Field 1: Ponteiro para o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="025ee-682">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="025ee-683">Info Field 2: Tamanho do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="025ee-683">Info Field 2: File size.</span></span>
- <span data-ttu-id="025ee-684">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-684">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-685">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-685">Info Field 4: Not used.</span></span>

### <a name="file-create"></a><span data-ttu-id="025ee-686">Criar ficheiros</span><span class="sxs-lookup"><span data-stu-id="025ee-686">File Create</span></span>

#### <a name="fx_file_create"></a><span data-ttu-id="025ee-687">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="025ee-687">fx_file_create</span></span>

<span data-ttu-id="025ee-688">**Ícone** ![ Ícone de criação de arquivo](./media/user-guide/fx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-688">**Icon** ![File create icon](./media/user-guide/fx-events/image39.png)</span></span>

<span data-ttu-id="025ee-689">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-689">**Description**</span></span>

<span data-ttu-id="025ee-690">Este evento representa um evento de criação de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="025ee-690">This event represents a file create event.</span></span>

<span data-ttu-id="025ee-691">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-691">**Information Fields**</span></span>

- <span data-ttu-id="025ee-692">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-692">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-693">Info Field 2: Ponteiro para o nome do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="025ee-693">Info Field 2: Pointer to file name.</span></span>
- <span data-ttu-id="025ee-694">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-694">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-695">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-695">Info Field 4: Not used.</span></span>

### <a name="file-date-time-set"></a><span data-ttu-id="025ee-696">Conjunto de tempo de data de arquivo</span><span class="sxs-lookup"><span data-stu-id="025ee-696">File Date Time Set</span></span> 

#### <a name="fx_file_date_time_set"></a><span data-ttu-id="025ee-697">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="025ee-697">fx_file_date_time_set</span></span>

<span data-ttu-id="025ee-698">**Ícone** ![ Ícone de definição de hora de data de arquivo](./media/user-guide/fx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-698">**Icon** ![File date time set icon](./media/user-guide/fx-events/image40.png)</span></span>

<span data-ttu-id="025ee-699">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-699">**Description**</span></span>

<span data-ttu-id="025ee-700">Este evento representa um evento de data/hora de arquivo.</span><span class="sxs-lookup"><span data-stu-id="025ee-700">This event represents a file date/time set event.</span></span>

<span data-ttu-id="025ee-701">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-701">**Information Fields**</span></span>

- <span data-ttu-id="025ee-702">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-702">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-703">Info Field 2: Ponteiro para o nome do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="025ee-703">Info Field 2: Pointer to file name.</span></span>
- <span data-ttu-id="025ee-704">Campo de Informações 3: Ano.</span><span class="sxs-lookup"><span data-stu-id="025ee-704">Info Field 3: Year.</span></span>
- <span data-ttu-id="025ee-705">Info Field 4: Mês.</span><span class="sxs-lookup"><span data-stu-id="025ee-705">Info Field 4: Month.</span></span>

### <a name="file-delete"></a><span data-ttu-id="025ee-706">Apagar ficheiros</span><span class="sxs-lookup"><span data-stu-id="025ee-706">File Delete</span></span> 

#### <a name="fx_file_delete"></a><span data-ttu-id="025ee-707">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="025ee-707">fx_file_delete</span></span>

<span data-ttu-id="025ee-708">**Ícone** ![ Ícone de exclusão de ficheiro](./media/user-guide/fx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-708">**Icon** ![File delete icon](./media/user-guide/fx-events/image41.png)</span></span>

<span data-ttu-id="025ee-709">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-709">**Description**</span></span>

<span data-ttu-id="025ee-710">Este evento representa um evento de eliminação de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="025ee-710">This event represents a file delete event.</span></span>

<span data-ttu-id="025ee-711">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-711">**Information Fields**</span></span>

- <span data-ttu-id="025ee-712">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-712">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-713">Info Field 2: Ponteiro para o nome do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="025ee-713">Info Field 2: Pointer to file name.</span></span>
- <span data-ttu-id="025ee-714">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-714">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-715">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-715">Info Field 4: Not used.</span></span>

### <a name="file-open"></a><span data-ttu-id="025ee-716">Arquivo Aberto</span><span class="sxs-lookup"><span data-stu-id="025ee-716">File Open</span></span> 

#### <a name="fx_file_open"></a><span data-ttu-id="025ee-717">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="025ee-717">fx_file_open</span></span>

<span data-ttu-id="025ee-718">**Ícone** ![ Ícone aberto de arquivo](./media/user-guide/fx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-718">**Icon** ![File open icon](./media/user-guide/fx-events/image42.png)</span></span>

<span data-ttu-id="025ee-719">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-719">**Description**</span></span>

<span data-ttu-id="025ee-720">Este evento representa um evento aberto de arquivos.</span><span class="sxs-lookup"><span data-stu-id="025ee-720">This event represents a file open event.</span></span>

<span data-ttu-id="025ee-721">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-721">**Information Fields**</span></span> 

- <span data-ttu-id="025ee-722">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-722">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-723">Info Field 2: Ponteiro para o bloco de controlo de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="025ee-723">Info Field 2: Pointer to the file control block.</span></span>
- <span data-ttu-id="025ee-724">Info Field 3: Ponteiro para o nome do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="025ee-724">Info Field 3: Pointer to file name.</span></span>
- <span data-ttu-id="025ee-725">Info Field 4: Tipo aberto:</span><span class="sxs-lookup"><span data-stu-id="025ee-725">Info Field 4: Open type:</span></span>

  |  <span data-ttu-id="025ee-726">Tipo aberto</span><span class="sxs-lookup"><span data-stu-id="025ee-726">Open Type</span></span>                        | <span data-ttu-id="025ee-727">Valor</span><span class="sxs-lookup"><span data-stu-id="025ee-727">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="025ee-728">Aberto para Ler</span><span class="sxs-lookup"><span data-stu-id="025ee-728">Open for Read</span></span>                    | <span data-ttu-id="025ee-729">(0x00)</span><span class="sxs-lookup"><span data-stu-id="025ee-729">(0x00)</span></span>  |
  |  <span data-ttu-id="025ee-730">Aberto para Escrita</span><span class="sxs-lookup"><span data-stu-id="025ee-730">Open for Write</span></span>                   | <span data-ttu-id="025ee-731">(0x01)</span><span class="sxs-lookup"><span data-stu-id="025ee-731">(0x01)</span></span>  |
  |  <span data-ttu-id="025ee-732">Open rápido para leitura</span><span class="sxs-lookup"><span data-stu-id="025ee-732">Fast Open for Read</span></span>               | <span data-ttu-id="025ee-733">(0x02)</span><span class="sxs-lookup"><span data-stu-id="025ee-733">(0x02)</span></span>  |

### <a name="file-read"></a><span data-ttu-id="025ee-734">Leitura de Arquivos</span><span class="sxs-lookup"><span data-stu-id="025ee-734">File Read</span></span> 

#### <a name="fx_file_read"></a><span data-ttu-id="025ee-735">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="025ee-735">fx_file_read</span></span>

<span data-ttu-id="025ee-736">**Ícone** ![ Ícone de leitura de arquivo](./media/user-guide/fx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-736">**Icon** ![File read icon](./media/user-guide/fx-events/image43.png)</span></span>

<span data-ttu-id="025ee-737">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-737">**Description**</span></span>

<span data-ttu-id="025ee-738">Este evento representa um evento de leitura de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="025ee-738">This event represents a file read event.</span></span>

<span data-ttu-id="025ee-739">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-739">**Information Fields**</span></span>

- <span data-ttu-id="025ee-740">Info Field 1: Ponteiro para o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="025ee-740">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="025ee-741">Info Field 2: Ponteiro tampão.</span><span class="sxs-lookup"><span data-stu-id="025ee-741">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="025ee-742">Info Campo 3: Tamanho do pedido.</span><span class="sxs-lookup"><span data-stu-id="025ee-742">Info Field 3: Request size.</span></span>
- <span data-ttu-id="025ee-743">Info Field 4: Leitura do tamanho real.</span><span class="sxs-lookup"><span data-stu-id="025ee-743">Info Field 4: Actual size read.</span></span>

### <a name="file-relative-seek"></a><span data-ttu-id="025ee-744">Procura relativa de arquivo</span><span class="sxs-lookup"><span data-stu-id="025ee-744">File Relative Seek</span></span> 

#### <a name="fx_file_relative_seek"></a><span data-ttu-id="025ee-745">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="025ee-745">fx_file_relative_seek</span></span>

<span data-ttu-id="025ee-746">**Ícone** ![ Ícone de procura relativa de arquivo](./media/user-guide/fx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-746">**Icon** ![File relative seek icon](./media/user-guide/fx-events/image44.png)</span></span>

<span data-ttu-id="025ee-747">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-747">**Description**</span></span>

<span data-ttu-id="025ee-748">Este evento representa um evento de procura de arquivo relativo.</span><span class="sxs-lookup"><span data-stu-id="025ee-748">This event represents a file relative seek event.</span></span>

<span data-ttu-id="025ee-749">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-749">**Information Fields**</span></span>

- <span data-ttu-id="025ee-750">Info Field 1: Ponteiro para o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="025ee-750">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="025ee-751">Info Field 2: Byte offset.</span><span class="sxs-lookup"><span data-stu-id="025ee-751">Info Field 2: Byte offset.</span></span>
- <span data-ttu-id="025ee-752">Info Field 3: Procurar a partir de:</span><span class="sxs-lookup"><span data-stu-id="025ee-752">Info Field 3: Seek from:</span></span>

  | <span data-ttu-id="025ee-753">Evento</span><span class="sxs-lookup"><span data-stu-id="025ee-753">Event</span></span>                             | <span data-ttu-id="025ee-754">Valor</span><span class="sxs-lookup"><span data-stu-id="025ee-754">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="025ee-755">Desde o início</span><span class="sxs-lookup"><span data-stu-id="025ee-755">From Beginning</span></span>                   | <span data-ttu-id="025ee-756">(0x00)</span><span class="sxs-lookup"><span data-stu-id="025ee-756">(0x00)</span></span>  |
  |  <span data-ttu-id="025ee-757">De Fim</span><span class="sxs-lookup"><span data-stu-id="025ee-757">From End</span></span>                         | <span data-ttu-id="025ee-758">(0x01)</span><span class="sxs-lookup"><span data-stu-id="025ee-758">(0x01)</span></span>  | 
  |  <span data-ttu-id="025ee-759">a frente</span><span class="sxs-lookup"><span data-stu-id="025ee-759">Forward</span></span>                          | <span data-ttu-id="025ee-760">(0x02)</span><span class="sxs-lookup"><span data-stu-id="025ee-760">(0x02)</span></span>  |
  |  <span data-ttu-id="025ee-761">para trás</span><span class="sxs-lookup"><span data-stu-id="025ee-761">Backward</span></span>                         | <span data-ttu-id="025ee-762">(0x03)</span><span class="sxs-lookup"><span data-stu-id="025ee-762">(0x03)</span></span>  |
- <span data-ttu-id="025ee-763">Info Field 4: Offset anterior.</span><span class="sxs-lookup"><span data-stu-id="025ee-763">Info Field 4: Previous offset.</span></span>

### <a name="file-rename"></a><span data-ttu-id="025ee-764">Renomear o Ficheiro</span><span class="sxs-lookup"><span data-stu-id="025ee-764">File Rename</span></span> 

#### <a name="fx_file_rename"></a><span data-ttu-id="025ee-765">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="025ee-765">fx_file_rename</span></span>

<span data-ttu-id="025ee-766">**Ícone** ![ Ícone de renome de arquivo](./media/user-guide/fx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-766">**Icon** ![File rename icon](./media/user-guide/fx-events/image45.png)</span></span>

<span data-ttu-id="025ee-767">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-767">**Description**</span></span>

<span data-ttu-id="025ee-768">Este evento representa um evento de renome de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="025ee-768">This event represents a file rename event.</span></span>

<span data-ttu-id="025ee-769">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-769">**Information Fields**</span></span>

- <span data-ttu-id="025ee-770">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-770">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-771">Info Field 2: Ponteiro para o nome do ficheiro antigo.</span><span class="sxs-lookup"><span data-stu-id="025ee-771">Info Field 2: Pointer to old file name.</span></span>
- <span data-ttu-id="025ee-772">Info Field 3: Ponteiro para novo nome do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="025ee-772">Info Field 3: Pointer to new file name.</span></span>
- <span data-ttu-id="025ee-773">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-773">Info Field 4: Not used.</span></span>

### <a name="file-seek"></a><span data-ttu-id="025ee-774">Procura de Arquivos</span><span class="sxs-lookup"><span data-stu-id="025ee-774">File Seek</span></span> 

#### <a name="fx_file_seek"></a><span data-ttu-id="025ee-775">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="025ee-775">fx_file_seek</span></span>

<span data-ttu-id="025ee-776">**Ícone** ![ Ícone de procura de arquivo](./media/user-guide/fx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-776">**Icon** ![File seek icon](./media/user-guide/fx-events/image46.png)</span></span>

<span data-ttu-id="025ee-777">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-777">**Description**</span></span>

<span data-ttu-id="025ee-778">Este evento representa um evento de procura de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="025ee-778">This event represents a file seek event.</span></span>

<span data-ttu-id="025ee-779">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-779">**Information Fields**</span></span> 

- <span data-ttu-id="025ee-780">Info Field 1: Ponteiro para o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="025ee-780">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="025ee-781">Info Field 2: Byte offset.</span><span class="sxs-lookup"><span data-stu-id="025ee-781">Info Field 2: Byte offset.</span></span>
- <span data-ttu-id="025ee-782">Info Field 3: Offset anterior.</span><span class="sxs-lookup"><span data-stu-id="025ee-782">Info Field 3: Previous offset.</span></span>
- <span data-ttu-id="025ee-783">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-783">Info Field 4: Not used.</span></span>

### <a name="file-truncate"></a><span data-ttu-id="025ee-784">Arquivo Truncate</span><span class="sxs-lookup"><span data-stu-id="025ee-784">File Truncate</span></span> 

#### <a name="fx_file_truncate"></a><span data-ttu-id="025ee-785">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="025ee-785">fx_file_truncate</span></span>

<span data-ttu-id="025ee-786">**Ícone** ![ Ícone truncado de arquivo](./media/user-guide/fx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-786">**Icon** ![File truncate icon](./media/user-guide/fx-events/image47.png)</span></span>

<span data-ttu-id="025ee-787">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-787">**Description**</span></span>

<span data-ttu-id="025ee-788">Este evento representa um evento truncado de arquivo.</span><span class="sxs-lookup"><span data-stu-id="025ee-788">This event represents a file truncate event.</span></span>

<span data-ttu-id="025ee-789">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-789">**Information Fields**</span></span>

- <span data-ttu-id="025ee-790">Info Field 1: Ponteiro para o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="025ee-790">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="025ee-791">Info Field 2: Tamanho solicitado.</span><span class="sxs-lookup"><span data-stu-id="025ee-791">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="025ee-792">Info Field 3: Tamanho anterior.</span><span class="sxs-lookup"><span data-stu-id="025ee-792">Info Field 3: Previous size.</span></span>
- <span data-ttu-id="025ee-793">Info Field 4: Novo tamanho.</span><span class="sxs-lookup"><span data-stu-id="025ee-793">Info Field 4: New size.</span></span>

### <a name="file-truncate-release"></a><span data-ttu-id="025ee-794">Lançamento do Truncato de Ficheiros</span><span class="sxs-lookup"><span data-stu-id="025ee-794">File Truncate Release</span></span> 

#### <a name="fx_file_truncate_release"></a><span data-ttu-id="025ee-795">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="025ee-795">fx_file_truncate_release</span></span> 

<span data-ttu-id="025ee-796">**Ícone** ![ Ícone de libertação de truncato de arquivo](./media/user-guide/fx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-796">**Icon** ![File truncate release icon](./media/user-guide/fx-events/image48.png)</span></span>

<span data-ttu-id="025ee-797">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-797">**Description**</span></span>

<span data-ttu-id="025ee-798">Este evento representa um evento de lançamento truncado de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="025ee-798">This event represents a file truncate release event.</span></span>

<span data-ttu-id="025ee-799">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-799">**Information Fields**</span></span>

- <span data-ttu-id="025ee-800">Info Field 1: Ponteiro para o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="025ee-800">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="025ee-801">Info Field 2: Tamanho solicitado.</span><span class="sxs-lookup"><span data-stu-id="025ee-801">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="025ee-802">Info Field 3: Tamanho anterior.</span><span class="sxs-lookup"><span data-stu-id="025ee-802">Info Field 3: Previous size.</span></span>
- <span data-ttu-id="025ee-803">Info Field 4: Novo tamanho.</span><span class="sxs-lookup"><span data-stu-id="025ee-803">Info Field 4: New size.</span></span>

### <a name="file-write"></a><span data-ttu-id="025ee-804">Escrita de Arquivo</span><span class="sxs-lookup"><span data-stu-id="025ee-804">File Write</span></span> 

#### <a name="fx_file_write"></a><span data-ttu-id="025ee-805">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="025ee-805">fx_file_write</span></span> 

<span data-ttu-id="025ee-806">**Ícone** ![ Ícone de escrita de arquivo](./media/user-guide/fx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-806">**Icon** ![File write icon](./media/user-guide/fx-events/image49.png)</span></span>

<span data-ttu-id="025ee-807">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-807">**Description**</span></span>

<span data-ttu-id="025ee-808">Este evento representa um evento de escrita de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="025ee-808">This event represents a file write event.</span></span>

<span data-ttu-id="025ee-809">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-809">**Information Fields**</span></span>

- <span data-ttu-id="025ee-810">Info Field 1: Ponteiro para o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="025ee-810">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="025ee-811">Info Field 2: Ponteiro tampão.</span><span class="sxs-lookup"><span data-stu-id="025ee-811">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="025ee-812">Info Campo 3: Tamanho do pedido.</span><span class="sxs-lookup"><span data-stu-id="025ee-812">Info Field 3: Request size.</span></span>
- <span data-ttu-id="025ee-813">Info Field 4: Tamanho real escrito.</span><span class="sxs-lookup"><span data-stu-id="025ee-813">Info Field 4: Actual size written.</span></span>

### <a name="media-abort"></a><span data-ttu-id="025ee-814">Aborto dos meios de comunicação</span><span class="sxs-lookup"><span data-stu-id="025ee-814">Media Abort</span></span> 

#### <a name="fx_media_abort"></a><span data-ttu-id="025ee-815">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="025ee-815">fx_media_abort</span></span> 

<span data-ttu-id="025ee-816">**Ícone** ![ Ícone de aborto de mídia](./media/user-guide/fx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-816">**Icon** ![Media abort icon](./media/user-guide/fx-events/image50.png)</span></span>

<span data-ttu-id="025ee-817">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-817">**Description**</span></span>

<span data-ttu-id="025ee-818">Este evento representa um evento de aborto mediático.</span><span class="sxs-lookup"><span data-stu-id="025ee-818">This event represents a media abort event.</span></span>

<span data-ttu-id="025ee-819">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-819">**Information Fields**</span></span>

- <span data-ttu-id="025ee-820">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-820">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-821">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-821">Info Field 2: Not used.</span></span>
- <span data-ttu-id="025ee-822">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-822">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-823">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-823">Info Field 4: Not used.</span></span>

### <a name="media-cache-invalidate"></a><span data-ttu-id="025ee-824">Cache de media invalidado</span><span class="sxs-lookup"><span data-stu-id="025ee-824">Media Cache Invalidate</span></span>

#### <a name="fx_media_cache_invalidate"></a><span data-ttu-id="025ee-825">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="025ee-825">fx_media_cache_invalidate</span></span>

<span data-ttu-id="025ee-826">**Ícone** ![ Ícone invalidado de cache de mídia](./media/user-guide/fx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-826">**Icon** ![Media cache invalidate icon](./media/user-guide/fx-events/image51.png)</span></span>

<span data-ttu-id="025ee-827">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-827">**Description**</span></span>

<span data-ttu-id="025ee-828">Este evento representa um evento invalidado de cache de mídia.</span><span class="sxs-lookup"><span data-stu-id="025ee-828">This event represents a media cache invalidate event.</span></span>

<span data-ttu-id="025ee-829">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-829">**Information Fields**</span></span>

- <span data-ttu-id="025ee-830">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-830">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-831">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-831">Info Field 2: Not used.</span></span>
- <span data-ttu-id="025ee-832">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-832">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-833">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-833">Info Field 4: Not used.</span></span>

### <a name="media-check"></a><span data-ttu-id="025ee-834">Verificação de meios de comunicação</span><span class="sxs-lookup"><span data-stu-id="025ee-834">Media Check</span></span> 

#### <a name="fx_media_check"></a><span data-ttu-id="025ee-835">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="025ee-835">fx_media_check</span></span>

<span data-ttu-id="025ee-836">**Ícone** ![ Ícone de verificação de mídia](./media/user-guide/fx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-836">**Icon** ![Media check icon](./media/user-guide/fx-events/image52.png)</span></span>

<span data-ttu-id="025ee-837">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-837">**Description**</span></span>

<span data-ttu-id="025ee-838">Este evento representa um evento de verificação de mídia.</span><span class="sxs-lookup"><span data-stu-id="025ee-838">This event represents a media check event.</span></span>

<span data-ttu-id="025ee-839">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-839">**Information Fields**</span></span> 

- <span data-ttu-id="025ee-840">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-840">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-841">Info Field 2: Ponteiro de memória de risco.</span><span class="sxs-lookup"><span data-stu-id="025ee-841">Info Field 2: Scratch memory pointer.</span></span>
- <span data-ttu-id="025ee-842">Info Field 3: Riscar o tamanho da memória.</span><span class="sxs-lookup"><span data-stu-id="025ee-842">Info Field 3: Scratch memory size.</span></span>
- <span data-ttu-id="025ee-843">Info Field 4: Mapa de bits de erros:</span><span class="sxs-lookup"><span data-stu-id="025ee-843">Info Field 4: Errors bit map:</span></span>

  | <span data-ttu-id="025ee-844">Tipo de erro</span><span class="sxs-lookup"><span data-stu-id="025ee-844">Error type</span></span>                        | <span data-ttu-id="025ee-845">Valor</span><span class="sxs-lookup"><span data-stu-id="025ee-845">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="025ee-846">Erro da cadeia fat</span><span class="sxs-lookup"><span data-stu-id="025ee-846">FAT Chain Error</span></span>                  | <span data-ttu-id="025ee-847">(0x01)</span><span class="sxs-lookup"><span data-stu-id="025ee-847">(0x01)</span></span>  |
  |  <span data-ttu-id="025ee-848">Erro do Diretório</span><span class="sxs-lookup"><span data-stu-id="025ee-848">Directory Error</span></span>                  | <span data-ttu-id="025ee-849">(0x02)</span><span class="sxs-lookup"><span data-stu-id="025ee-849">(0x02)</span></span>  |
  |  <span data-ttu-id="025ee-850">Erro de cluster perdido</span><span class="sxs-lookup"><span data-stu-id="025ee-850">Lost Cluster Error</span></span>               | <span data-ttu-id="025ee-851">(0x04)</span><span class="sxs-lookup"><span data-stu-id="025ee-851">(0x04)</span></span>  |
  |  <span data-ttu-id="025ee-852">Erro do tamanho do ficheiro</span><span class="sxs-lookup"><span data-stu-id="025ee-852">File Size Error</span></span>                  | <span data-ttu-id="025ee-853">(0x08)</span><span class="sxs-lookup"><span data-stu-id="025ee-853">(0x08)</span></span>  |

### <a name="media-close"></a><span data-ttu-id="025ee-854">Media Close</span><span class="sxs-lookup"><span data-stu-id="025ee-854">Media Close</span></span> 

#### <a name="fx_media_close"></a><span data-ttu-id="025ee-855">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="025ee-855">fx_media_close</span></span>

<span data-ttu-id="025ee-856">**Ícone** ![ Ícone de close de mídia](./media/user-guide/fx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-856">**Icon** ![Media Close icon](./media/user-guide/fx-events/image53.png)</span></span>

<span data-ttu-id="025ee-857">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-857">**Description**</span></span>

<span data-ttu-id="025ee-858">Este evento representa um evento mediático.</span><span class="sxs-lookup"><span data-stu-id="025ee-858">This event represents a media close event.</span></span>

<span data-ttu-id="025ee-859">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-859">**Information Fields**</span></span> 

- <span data-ttu-id="025ee-860">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-860">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-861">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-861">Info Field 2: Not used.</span></span>
- <span data-ttu-id="025ee-862">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-862">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-863">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-863">Info Field 4: Not used.</span></span>

### <a name="media-flush"></a><span data-ttu-id="025ee-864">Media Flush</span><span class="sxs-lookup"><span data-stu-id="025ee-864">Media Flush</span></span> 

#### <a name="fx_media_flush"></a><span data-ttu-id="025ee-865">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="025ee-865">fx_media_flush</span></span>

<span data-ttu-id="025ee-866">**Ícone** ![ Ícone de descarga de mídia](./media/user-guide/fx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-866">**Icon** ![Media flush icon](./media/user-guide/fx-events/image54.png)</span></span>

<span data-ttu-id="025ee-867">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-867">**Description**</span></span>

<span data-ttu-id="025ee-868">Este evento representa um evento de media flush.</span><span class="sxs-lookup"><span data-stu-id="025ee-868">This event represents a media flush event.</span></span>

<span data-ttu-id="025ee-869">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-869">**Information Fields**</span></span>

- <span data-ttu-id="025ee-870">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-870">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-871">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-871">Info Field 2: Not used.</span></span>
- <span data-ttu-id="025ee-872">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-872">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-873">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-873">Info Field 4: Not used.</span></span>

### <a name="media-format"></a><span data-ttu-id="025ee-874">Formato de mídia</span><span class="sxs-lookup"><span data-stu-id="025ee-874">Media Format</span></span> 

#### <a name="fx_media_format"></a><span data-ttu-id="025ee-875">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="025ee-875">fx_media_format</span></span>

<span data-ttu-id="025ee-876">**Ícone** ![ Ícone de formato de mídia](./media/user-guide/fx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-876">**Icon** ![Media format icon](./media/user-guide/fx-events/image55.png)</span></span>

<span data-ttu-id="025ee-877">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-877">**Description**</span></span>

<span data-ttu-id="025ee-878">Este evento representa um evento de formato mediático.</span><span class="sxs-lookup"><span data-stu-id="025ee-878">This event represents a media format event.</span></span>

<span data-ttu-id="025ee-879">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-879">**Information Fields**</span></span>

- <span data-ttu-id="025ee-880">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-880">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-881">Info Campo 2: Número de entradas de raiz.</span><span class="sxs-lookup"><span data-stu-id="025ee-881">Info Field 2: Number of root entries.</span></span>
- <span data-ttu-id="025ee-882">Info Field 3: Sectores.</span><span class="sxs-lookup"><span data-stu-id="025ee-882">Info Field 3: Sectors.</span></span>
- <span data-ttu-id="025ee-883">Info Field 4: Sectores por cluster.</span><span class="sxs-lookup"><span data-stu-id="025ee-883">Info Field 4: Sectors per cluster.</span></span>

### <a name="media-open"></a><span data-ttu-id="025ee-884">Media Open</span><span class="sxs-lookup"><span data-stu-id="025ee-884">Media Open</span></span> 

#### <a name="fx_media_open"></a><span data-ttu-id="025ee-885">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="025ee-885">fx_media_open</span></span>

<span data-ttu-id="025ee-886">**Ícone** ![ Ícone aberto de mídia](./media/user-guide/fx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-886">**Icon** ![Media open icon](./media/user-guide/fx-events/image56.png)</span></span>

<span data-ttu-id="025ee-887">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-887">**Description**</span></span>

<span data-ttu-id="025ee-888">Este evento representa um evento aberto à comunicação social.</span><span class="sxs-lookup"><span data-stu-id="025ee-888">This event represents a media open event.</span></span>

<span data-ttu-id="025ee-889">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-889">**Information Fields**</span></span>

- <span data-ttu-id="025ee-890">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-890">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-891">Info Field 2: Ponteiro para a entrada do controlador de mídia.</span><span class="sxs-lookup"><span data-stu-id="025ee-891">Info Field 2: Pointer to media driver entry.</span></span>
- <span data-ttu-id="025ee-892">Info Campo 3: Ponteiro de memória.</span><span class="sxs-lookup"><span data-stu-id="025ee-892">Info Field 3: Memory pointer.</span></span>
- <span data-ttu-id="025ee-893">Info Campo 4: Tamanho da memória.</span><span class="sxs-lookup"><span data-stu-id="025ee-893">Info Field 4: Memory size.</span></span>

### <a name="media-read-media-read"></a><span data-ttu-id="025ee-894">Leitura de Mídia</span><span class="sxs-lookup"><span data-stu-id="025ee-894">Media Read Media Read</span></span> 

#### <a name="fx_media_read"></a><span data-ttu-id="025ee-895">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="025ee-895">fx_media_read</span></span>

<span data-ttu-id="025ee-896">**Ícone** ![ Ícone de leitura de mídia](./media/user-guide/fx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-896">**Icon** ![Media read icon](./media/user-guide/fx-events/image57.png)</span></span>

<span data-ttu-id="025ee-897">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-897">**Description**</span></span>

<span data-ttu-id="025ee-898">Este evento representa um evento de leitura mediática.</span><span class="sxs-lookup"><span data-stu-id="025ee-898">This event represents a media read event.</span></span>

<span data-ttu-id="025ee-899">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-899">**Information Fields**</span></span>

- <span data-ttu-id="025ee-900">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-900">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-901">Info Field 2: Sector lógico.</span><span class="sxs-lookup"><span data-stu-id="025ee-901">Info Field 2: Logical sector.</span></span>
- <span data-ttu-id="025ee-902">Info Field 3: Ponteiro tampão.</span><span class="sxs-lookup"><span data-stu-id="025ee-902">Info Field 3: Buffer pointer.</span></span>
- <span data-ttu-id="025ee-903">Info Field 4: Bytes read.</span><span class="sxs-lookup"><span data-stu-id="025ee-903">Info Field 4: Bytes read.</span></span>

### <a name="media-space-available"></a><span data-ttu-id="025ee-904">Espaço de Mídia Disponível</span><span class="sxs-lookup"><span data-stu-id="025ee-904">Media Space Available</span></span> 

#### <a name="fx_media_space_available"></a><span data-ttu-id="025ee-905">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="025ee-905">fx_media_space_available</span></span>

<span data-ttu-id="025ee-906">**Ícone** ![ Ícone disponível do espaço dos media](./media/user-guide/fx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-906">**Icon** ![Media space available icon](./media/user-guide/fx-events/image58.png)</span></span>

<span data-ttu-id="025ee-907">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-907">**Description**</span></span>

<span data-ttu-id="025ee-908">Este evento representa um evento de espaço de comunicação disponível.</span><span class="sxs-lookup"><span data-stu-id="025ee-908">This event represents a media space available event.</span></span>

<span data-ttu-id="025ee-909">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-909">**Information Fields**</span></span> 

- <span data-ttu-id="025ee-910">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-910">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-911">Info Field 2: Ponteiro bytes disponível.</span><span class="sxs-lookup"><span data-stu-id="025ee-911">Info Field 2: Available bytes pointer.</span></span>
- <span data-ttu-id="025ee-912">Info Campo 3: Número de aglomerados gratuitos.</span><span class="sxs-lookup"><span data-stu-id="025ee-912">Info Field 3: Number of free clusters.</span></span>
- <span data-ttu-id="025ee-913">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-913">Info Field 4: Not used.</span></span>

### <a name="media-volume-get"></a><span data-ttu-id="025ee-914">Volume de mídia Obter</span><span class="sxs-lookup"><span data-stu-id="025ee-914">Media Volume Get</span></span> 

#### <a name="fx_media_volume_get"></a><span data-ttu-id="025ee-915">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="025ee-915">fx_media_volume_get</span></span>

<span data-ttu-id="025ee-916">**Ícone** ![ Ícone de obter volume de mídia](./media/user-guide/fx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-916">**Icon** ![Media volume get icon](./media/user-guide/fx-events/image59.png)</span></span>

<span data-ttu-id="025ee-917">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-917">**Description**</span></span>

<span data-ttu-id="025ee-918">Este evento representa um evento de volume mediático.</span><span class="sxs-lookup"><span data-stu-id="025ee-918">This event represents a media volume get event.</span></span>

<span data-ttu-id="025ee-919">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-919">**Information Fields**</span></span>

- <span data-ttu-id="025ee-920">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-920">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-921">Info Campo 2: Ponteiro para o nome do volume.</span><span class="sxs-lookup"><span data-stu-id="025ee-921">Info Field 2: Pointer to volume name.</span></span>
- <span data-ttu-id="025ee-922">Info Field 3: Fonte de volume.</span><span class="sxs-lookup"><span data-stu-id="025ee-922">Info Field 3: Volume source.</span></span>
- <span data-ttu-id="025ee-923">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-923">Info Field 4: Not used.</span></span>

### <a name="media-volume-set"></a><span data-ttu-id="025ee-924">Conjunto de volume de mídia</span><span class="sxs-lookup"><span data-stu-id="025ee-924">Media Volume Set</span></span> 

#### <a name="fx_media_volume_set"></a><span data-ttu-id="025ee-925">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="025ee-925">fx_media_volume_set</span></span>

<span data-ttu-id="025ee-926">**Ícone** ![ Ícone de conjunto de volume de mídia](./media/user-guide/fx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-926">**Icon** ![Media volume set icon](./media/user-guide/fx-events/image60.png)</span></span>

<span data-ttu-id="025ee-927">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-927">**Description**</span></span>

<span data-ttu-id="025ee-928">Este evento representa um evento de volume mediático.</span><span class="sxs-lookup"><span data-stu-id="025ee-928">This event represents a media volume set event.</span></span>

<span data-ttu-id="025ee-929">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-929">**Information Fields**</span></span> 
- <span data-ttu-id="025ee-930">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-930">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-931">Info Campo 2: Ponteiro para o nome do volume.</span><span class="sxs-lookup"><span data-stu-id="025ee-931">Info Field 2: Pointer to volume name.</span></span>
- <span data-ttu-id="025ee-932">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-932">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-933">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-933">Info Field 4: Not used.</span></span>

### <a name="media-write"></a><span data-ttu-id="025ee-934">Escrita de mídia</span><span class="sxs-lookup"><span data-stu-id="025ee-934">Media Write</span></span> 

#### <a name="fx_media_write"></a><span data-ttu-id="025ee-935">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="025ee-935">fx_media_write</span></span>

<span data-ttu-id="025ee-936">**Ícone** ![ Ícone de escrita de mídia](./media/user-guide/fx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-936">**Icon** ![Media write icon](./media/user-guide/fx-events/image61.png)</span></span>

<span data-ttu-id="025ee-937">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-937">**Description**</span></span>

<span data-ttu-id="025ee-938">Este evento representa um evento de escrita mediática.</span><span class="sxs-lookup"><span data-stu-id="025ee-938">This event represents a media write event.</span></span>

<span data-ttu-id="025ee-939">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-939">**Information Fields**</span></span>

- <span data-ttu-id="025ee-940">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-940">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-941">Info Field 2: Sector lógico.</span><span class="sxs-lookup"><span data-stu-id="025ee-941">Info Field 2: Logical sector.</span></span>
- <span data-ttu-id="025ee-942">Info Field 3: Ponteiro tampão.</span><span class="sxs-lookup"><span data-stu-id="025ee-942">Info Field 3: Buffer pointer.</span></span>
- <span data-ttu-id="025ee-943">Info Field 4: Bytes escritos.</span><span class="sxs-lookup"><span data-stu-id="025ee-943">Info Field 4: Bytes written.</span></span>

### <a name="system-date-get"></a><span data-ttu-id="025ee-944">Data do Sistema Obter</span><span class="sxs-lookup"><span data-stu-id="025ee-944">System Date Get</span></span> 

#### <a name="fx_system_date_get"></a><span data-ttu-id="025ee-945">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="025ee-945">fx_system_date_get</span></span> 

<span data-ttu-id="025ee-946">**Ícone** ![ Data do sistema obter ícone](./media/user-guide/fx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-946">**Icon** ![System date get icon](./media/user-guide/fx-events/image62.png)</span></span>

<span data-ttu-id="025ee-947">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-947">**Description**</span></span>

<span data-ttu-id="025ee-948">Este evento representa um evento de data do sistema.</span><span class="sxs-lookup"><span data-stu-id="025ee-948">This event represents a system date get event.</span></span>

<span data-ttu-id="025ee-949">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-949">**Information Fields**</span></span>

- <span data-ttu-id="025ee-950">Campo de Informações 1: Ano.</span><span class="sxs-lookup"><span data-stu-id="025ee-950">Info Field 1: Year.</span></span>
- <span data-ttu-id="025ee-951">Info Field 2: Mês.</span><span class="sxs-lookup"><span data-stu-id="025ee-951">Info Field 2: Month.</span></span>
- <span data-ttu-id="025ee-952">Info Field 3: Dia.</span><span class="sxs-lookup"><span data-stu-id="025ee-952">Info Field 3: Day.</span></span>
- <span data-ttu-id="025ee-953">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-953">Info Field 4: Not used.</span></span>

### <a name="system-date-set"></a><span data-ttu-id="025ee-954">Conjunto de datas do sistema</span><span class="sxs-lookup"><span data-stu-id="025ee-954">System Date Set</span></span> 

#### <a name="fx_system_date_set"></a><span data-ttu-id="025ee-955">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="025ee-955">fx_system_date_set</span></span> 

<span data-ttu-id="025ee-956">**Ícone** ![ Ícone de definição de data do sistema](./media/user-guide/fx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-956">**Icon** ![System date set icon](./media/user-guide/fx-events/image63.png)</span></span>

<span data-ttu-id="025ee-957">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-957">**Description**</span></span>

<span data-ttu-id="025ee-958">Este evento representa um evento de data definida para o sistema.</span><span class="sxs-lookup"><span data-stu-id="025ee-958">This event represents a system date set event.</span></span>

<span data-ttu-id="025ee-959">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-959">**Information Fields**</span></span>

- <span data-ttu-id="025ee-960">Campo de Informações 1: Ano.</span><span class="sxs-lookup"><span data-stu-id="025ee-960">Info Field 1: Year.</span></span>
- <span data-ttu-id="025ee-961">Info Field 2: Mês.</span><span class="sxs-lookup"><span data-stu-id="025ee-961">Info Field 2: Month.</span></span>
- <span data-ttu-id="025ee-962">Info Field 3: Dia.</span><span class="sxs-lookup"><span data-stu-id="025ee-962">Info Field 3: Day.</span></span>
- <span data-ttu-id="025ee-963">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-963">Info Field 4: Not used.</span></span>

### <a name="system-initialize"></a><span data-ttu-id="025ee-964">Inicialização do sistema</span><span class="sxs-lookup"><span data-stu-id="025ee-964">System Initialize</span></span> 

#### <a name="fx_system_initialize"></a><span data-ttu-id="025ee-965">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="025ee-965">fx_system_initialize</span></span> 

<span data-ttu-id="025ee-966">**Ícone** ![ Ícone inicializando o sistema](./media/user-guide/fx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-966">**Icon** ![System initialize icon](./media/user-guide/fx-events/image64.png)</span></span>

<span data-ttu-id="025ee-967">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-967">**Description**</span></span>

<span data-ttu-id="025ee-968">Este evento representa um evento inicialização do sistema.</span><span class="sxs-lookup"><span data-stu-id="025ee-968">This event represents a system initialize event.</span></span>

<span data-ttu-id="025ee-969">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-969">**Information Fields**</span></span>

- <span data-ttu-id="025ee-970">Info Field 1: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-970">Info Field 1: Not used.</span></span>
- <span data-ttu-id="025ee-971">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-971">Info Field 2: Not used.</span></span>
- <span data-ttu-id="025ee-972">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-972">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-973">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-973">Info Field 4: Not used.</span></span>

### <a name="system-time-get"></a><span data-ttu-id="025ee-974">Tempo do sistema obter</span><span class="sxs-lookup"><span data-stu-id="025ee-974">System Time Get</span></span> 

#### <a name="fx_system_time_get"></a><span data-ttu-id="025ee-975">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="025ee-975">fx_system_time_get</span></span> 

<span data-ttu-id="025ee-976">**Ícone** ![ Tempo do sistema obter ícone](./media/user-guide/fx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-976">**Icon** ![System time get icon](./media/user-guide/fx-events/image65.png)</span></span>

<span data-ttu-id="025ee-977">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-977">**Description**</span></span>

<span data-ttu-id="025ee-978">Este evento representa um evento de tempo do sistema.</span><span class="sxs-lookup"><span data-stu-id="025ee-978">This event represents a system time get event.</span></span>

<span data-ttu-id="025ee-979">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-979">**Information Fields**</span></span> 

- <span data-ttu-id="025ee-980">Info Field 1: Hora.</span><span class="sxs-lookup"><span data-stu-id="025ee-980">Info Field 1: Hour.</span></span>
- <span data-ttu-id="025ee-981">Info Field 2: Minuto.</span><span class="sxs-lookup"><span data-stu-id="025ee-981">Info Field 2: Minute.</span></span>
- <span data-ttu-id="025ee-982">Info Field 3: Segundo.</span><span class="sxs-lookup"><span data-stu-id="025ee-982">Info Field 3: Second.</span></span>
- <span data-ttu-id="025ee-983">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-983">Info Field 4: Not used.</span></span>

### <a name="system-time-set"></a><span data-ttu-id="025ee-984">Conjunto de tempo do sistema</span><span class="sxs-lookup"><span data-stu-id="025ee-984">System Time Set</span></span> 

#### <a name="fx_system_time_set"></a><span data-ttu-id="025ee-985">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="025ee-985">fx_system_time_set</span></span> 

<span data-ttu-id="025ee-986">**Ícone** ![ Ícone de definição de tempo do sistema](./media/user-guide/fx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-986">**Icon** ![System time set icon](./media/user-guide/fx-events/image66.png)</span></span>

<span data-ttu-id="025ee-987">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-987">**Description**</span></span>

<span data-ttu-id="025ee-988">Este evento representa um evento de tempo definido pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="025ee-988">This event represents a system time set event.</span></span>

<span data-ttu-id="025ee-989">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-989">**Information Fields**</span></span>

- <span data-ttu-id="025ee-990">Info Field 1: Hora.</span><span class="sxs-lookup"><span data-stu-id="025ee-990">Info Field 1: Hour.</span></span>
- <span data-ttu-id="025ee-991">Info Field 2: Minuto.</span><span class="sxs-lookup"><span data-stu-id="025ee-991">Info Field 2: Minute.</span></span>
- <span data-ttu-id="025ee-992">Info Field 3: Segundo.</span><span class="sxs-lookup"><span data-stu-id="025ee-992">Info Field 3: Second.</span></span>
- <span data-ttu-id="025ee-993">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-993">Info Field 4: Not used.</span></span>

### <a name="unicode-directory-create"></a><span data-ttu-id="025ee-994">Unicode Directy Criar</span><span class="sxs-lookup"><span data-stu-id="025ee-994">Unicode Directory Create</span></span> 

#### <a name="fx_unicode_directory_create"></a><span data-ttu-id="025ee-995">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="025ee-995">fx_unicode_directory_create</span></span> 

<span data-ttu-id="025ee-996">**Ícone** ![ Diretório unicode criar ícone](./media/user-guide/fx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-996">**Icon** ![Unicode directory create icon](./media/user-guide/fx-events/image67.png)</span></span>

<span data-ttu-id="025ee-997">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-997">**Description**</span></span>

<span data-ttu-id="025ee-998">Este evento representa um evento de criação de diretório Unicode.</span><span class="sxs-lookup"><span data-stu-id="025ee-998">This event represents a Unicode directory create event.</span></span>

<span data-ttu-id="025ee-999">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-999">**Information Fields**</span></span> 

- <span data-ttu-id="025ee-1000">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-1000">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-1001">Info Field 2: Ponteiro para o nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="025ee-1001">Info Field 2: Pointer to Unicode name.</span></span>
- <span data-ttu-id="025ee-1002">Info Field 3: Tamanho do nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="025ee-1002">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="025ee-1003">Info Field 4: Ponteiro para nome curto.</span><span class="sxs-lookup"><span data-stu-id="025ee-1003">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-directory-rename"></a><span data-ttu-id="025ee-1004">Nomeão de Unicode</span><span class="sxs-lookup"><span data-stu-id="025ee-1004">Unicode Directory Rename</span></span> 

#### <a name="fx_unicode_directory_rename"></a><span data-ttu-id="025ee-1005">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="025ee-1005">fx_unicode_directory_rename</span></span>

<span data-ttu-id="025ee-1006">**Ícone** ![ Ícone de renome de diretório unicode](./media/user-guide/fx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-1006">**Icon** ![Unicode directory rename icon](./media/user-guide/fx-events/image68.png)</span></span>

<span data-ttu-id="025ee-1007">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-1007">**Description**</span></span>

<span data-ttu-id="025ee-1008">Este evento representa um evento de renomeação do Unicode.</span><span class="sxs-lookup"><span data-stu-id="025ee-1008">This event represents a Unicode directory rename event.</span></span>

<span data-ttu-id="025ee-1009">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-1009">**Information Fields**</span></span> 

- <span data-ttu-id="025ee-1010">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-1010">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-1011">Info Field 2: Ponteiro para o nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="025ee-1011">Info Field 2: Pointer to Unicode name.</span></span>
- <span data-ttu-id="025ee-1012">Info Field 3: Tamanho do nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="025ee-1012">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="025ee-1013">Info Field 4: Ponteiro para nome curto.</span><span class="sxs-lookup"><span data-stu-id="025ee-1013">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-file-create"></a><span data-ttu-id="025ee-1014">Unicode File Create</span><span class="sxs-lookup"><span data-stu-id="025ee-1014">Unicode File Create</span></span> 

#### <a name="fx_unicode_file_create"></a><span data-ttu-id="025ee-1015">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="025ee-1015">fx_unicode_file_create</span></span>

<span data-ttu-id="025ee-1016">**Ícone** ![ Ícone de criação de ficheiro unicode](./media/user-guide/fx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-1016">**Icon** ![Unicode file create icon](./media/user-guide/fx-events/image69.png)</span></span>

<span data-ttu-id="025ee-1017">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-1017">**Description**</span></span>

<span data-ttu-id="025ee-1018">Este evento representa um evento de criação de ficheiros Unicode.</span><span class="sxs-lookup"><span data-stu-id="025ee-1018">This event represents a Unicode file create event.</span></span>

<span data-ttu-id="025ee-1019">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-1019">**Information Fields**</span></span>

- <span data-ttu-id="025ee-1020">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-1020">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-1021">Info Field 2: Ponteiro para o nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="025ee-1021">Info Field 2: Pointer to the Unicode name.</span></span>
- <span data-ttu-id="025ee-1022">Info Field 3: Tamanho do nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="025ee-1022">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="025ee-1023">Info Field 4: Ponteiro para nome curto.</span><span class="sxs-lookup"><span data-stu-id="025ee-1023">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-file-rename"></a><span data-ttu-id="025ee-1024">Renomear ficheiro Unicode</span><span class="sxs-lookup"><span data-stu-id="025ee-1024">Unicode File Rename</span></span> 

#### <a name="fx_unicode_file_rename"></a><span data-ttu-id="025ee-1025">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="025ee-1025">fx_unicode_file_rename</span></span>

<span data-ttu-id="025ee-1026">**Ícone** ![ Ícone de renome de ficheiro unicode](./media/user-guide/fx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-1026">**Icon** ![Unicode file rename icon](./media/user-guide/fx-events/image70.png)</span></span>

<span data-ttu-id="025ee-1027">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-1027">**Description**</span></span>

<span data-ttu-id="025ee-1028">Este evento representa um evento de renomeação de ficheiros Unicode.</span><span class="sxs-lookup"><span data-stu-id="025ee-1028">This event represents a Unicode file rename event.</span></span>

<span data-ttu-id="025ee-1029">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-1029">**Information Fields**</span></span>

- <span data-ttu-id="025ee-1030">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-1030">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-1031">Info Field 2: Ponteiro para o nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="025ee-1031">Info Field 2: Pointer to Unicode name.</span></span>
- <span data-ttu-id="025ee-1032">Info Field 3: Tamanho do nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="025ee-1032">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="025ee-1033">Info Field 4: Ponteiro para nome curto.</span><span class="sxs-lookup"><span data-stu-id="025ee-1033">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-length-get"></a><span data-ttu-id="025ee-1034">Unicode Length Get</span><span class="sxs-lookup"><span data-stu-id="025ee-1034">Unicode Length Get</span></span> 

#### <a name="fx_unicode_length_get"></a><span data-ttu-id="025ee-1035">fx_unicode_length_get</span><span class="sxs-lookup"><span data-stu-id="025ee-1035">fx_unicode_length_get</span></span>

<span data-ttu-id="025ee-1036">**Ícone** ![ Unicode comprimento obter ícone](./media/user-guide/fx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-1036">**Icon** ![Unicode length get icon](./media/user-guide/fx-events/image71.png)</span></span>

<span data-ttu-id="025ee-1037">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-1037">**Description**</span></span>

<span data-ttu-id="025ee-1038">Este evento representa um evento unicode length get.</span><span class="sxs-lookup"><span data-stu-id="025ee-1038">This event represents a Unicode length get event.</span></span>

<span data-ttu-id="025ee-1039">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-1039">**Information Fields**</span></span>

- <span data-ttu-id="025ee-1040">Info Field 1: Ponteiro para o nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="025ee-1040">Info Field 1: Pointer to the Unicode name.</span></span>
- <span data-ttu-id="025ee-1041">Info Field 2: Comprimento.</span><span class="sxs-lookup"><span data-stu-id="025ee-1041">Info Field 2: Length.</span></span>
- <span data-ttu-id="025ee-1042">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-1042">Info Field 3: Not used.</span></span>
- <span data-ttu-id="025ee-1043">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="025ee-1043">Info Field 4: Not used.</span></span>

### <a name="unicode-name-get"></a><span data-ttu-id="025ee-1044">Nome Unicode Obter</span><span class="sxs-lookup"><span data-stu-id="025ee-1044">Unicode Name Get</span></span> 

#### <a name="fx_unicode_name_get"></a><span data-ttu-id="025ee-1045">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="025ee-1045">fx_unicode_name_get</span></span>

<span data-ttu-id="025ee-1046">**Ícone** ![ Unicode nome obter ícone](./media/user-guide/fx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-1046">**Icon** ![Unicode name get icon](./media/user-guide/fx-events/image72.png)</span></span>

<span data-ttu-id="025ee-1047">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-1047">**Description**</span></span>

<span data-ttu-id="025ee-1048">Este evento representa um evento de nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="025ee-1048">This event represents a Unicode name get event.</span></span>

<span data-ttu-id="025ee-1049">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-1049">**Information Fields**</span></span>

- <span data-ttu-id="025ee-1050">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-1050">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-1051">Info Field 2: Nome curto de origem.</span><span class="sxs-lookup"><span data-stu-id="025ee-1051">Info Field 2: Source short name.</span></span>
- <span data-ttu-id="025ee-1052">Info Field 3: Destino Unicode nome pointer.</span><span class="sxs-lookup"><span data-stu-id="025ee-1052">Info Field 3: Destination Unicode name pointer.</span></span>
- <span data-ttu-id="025ee-1053">Info Field 4: Destino Unicode comprimento do nome.</span><span class="sxs-lookup"><span data-stu-id="025ee-1053">Info Field 4: Destination Unicode name length.</span></span>

### <a name="unicode-short-name-get"></a><span data-ttu-id="025ee-1054">Unicode Short Name Get</span><span class="sxs-lookup"><span data-stu-id="025ee-1054">Unicode Short Name Get</span></span> 

#### <a name="fx_unicode_short_name_get"></a><span data-ttu-id="025ee-1055">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="025ee-1055">fx_unicode_short_name_get</span></span>

<span data-ttu-id="025ee-1056">**Ícone** ![ Unicode nome curto obter ícone](./media/user-guide/fx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="025ee-1056">**Icon** ![Unicode short name get icon](./media/user-guide/fx-events/image73.png)</span></span>

<span data-ttu-id="025ee-1057">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="025ee-1057">**Description**</span></span>

<span data-ttu-id="025ee-1058">Este evento representa um evento de nome curto Unicode.</span><span class="sxs-lookup"><span data-stu-id="025ee-1058">This event represents a Unicode short name get event.</span></span>

<span data-ttu-id="025ee-1059">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="025ee-1059">**Information Fields**</span></span>

- <span data-ttu-id="025ee-1060">Info Field 1: Ponte para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="025ee-1060">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="025ee-1061">Info Field 2: Ponteiro para fonte Nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="025ee-1061">Info Field 2: Pointer to source Unicode name.</span></span>
- <span data-ttu-id="025ee-1062">Info Field 3: Comprimento do nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="025ee-1062">Info Field 3: Length of Unicode name.</span></span>
- <span data-ttu-id="025ee-1063">Info Field 4: Ponteiro para nome curto.</span><span class="sxs-lookup"><span data-stu-id="025ee-1063">Info Field 4: Pointer to short name.</span></span>