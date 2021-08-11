---
title: Capítulo 7 - Azure RTOS FileX trace eventos
description: Este capítulo contém uma descrição dos eventos Azure RTOS FileX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 8668f0867e205afdeab112dfedd257998a5f5b7ff256f27298072dde3e9019b0
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116803303"
---
# <a name="chapter-7---azure-rtos-filex-trace-events"></a>Capítulo 7 - Azure RTOS FileX trace eventos

Este capítulo contém uma descrição dos eventos Azure RTOS FileX. 

## <a name="list-of-events-and-icons"></a>Lista de eventos e ícones

**Segue-se uma lista de eventos FileX apresentados pela TraceX.**

O seguinte descreve cada evento:

| **Ícone**                         | **Significado**                               |
| -------------------------------- | ----------------------------------------- |
| ![Ícone de miss cache do setor lógico interno](./media/user-guide/fx-events/image1.png)    | Falha cache do sector lógico interno |
| ![Ícone de Cache Miss do Diretório Interno](./media/user-guide/fx-events/image2.png)    | Diretório Interno Cache Miss |
| ![Ícone de descarga de mídia interna](./media/user-guide/fx-events/image3.png)    | Flush de mídia interna |
| ![Ícone de leitura de entrada de diretório interno](./media/user-guide/fx-events/image4.png)    | Leitura de Entrada no Diretório Interno |
| ![Ícone de escrita de entrada de diretório interno](./media/user-guide/fx-events/image5.png)    | Escrita de entrada no diretório interno |
| ![Ícone de leitura interna I / O Motorista](./media/user-guide/fx-events/image6.png)    | Leitura interna do controlador de I/O |
| ![Ícone de escrita interna I / O Motorista](./media/user-guide/fx-events/image7.png)    | Escrita interna do condutor de I/O |
| ![Ícone interno de flush de i / o motorista](./media/user-guide/fx-events/image8.png)    | Flush de controlador de I/O interno |
| ![Ícone interno de abortar i / O motorista](./media/user-guide/fx-events/image9.png)    | Aborto interno do condutor de I/O |
| ![Ícone de inicialização do condutor interno I / O](./media/user-guide/fx-events/image10.png)    | Inicialização interna do controlador de I/O |
| ![Ícone de leitura de bota de i / o motorista interno](./media/user-guide/fx-events/image11.png)    | Leitura interna da bota de motorista de I/O |
| ![Ícone de setores de libertação de motorista internos I / O](./media/user-guide/fx-events/image12.png)    | Sectores internos de libertação de condutores de I/O |
| ![Ícone de escrita de bota de i / o motorista interno](./media/user-guide/fx-events/image13.png)    | Escrita interna da bota de motorista de I/O |
| ![Ícone interno I / O Condutor de condutor Des-initialize ícone](./media/user-guide/fx-events/image14.png)    | Condutor interno I / O Condutor Des-initialize |
| ![Ícone de leitura de atributos de diretório](./media/user-guide/fx-events/image15.png)    | **Leitura de Atributos de Diretório** *(fx_directory_attributes_read)* |
| ![Ícone de conjunto de atributos de diretório](./media/user-guide/fx-events/image16.png)    | **Conjunto de atributos de diretório** *(fx_directory_attributes_set)* |
| ![Diretório Criar ícone](./media/user-guide/fx-events/image17.png)    | **Diretório Criar** *(fx_directory_create)* |
| ![Diretório Padrão Obter ícone](./media/user-guide/fx-events/image18.png)    | **Diretório Padrão Obter** *(fx_directory_default_get*) |
| ![Ícone de conjunto de padrão de diretório](./media/user-guide/fx-events/image19.png)    | **Conjunto de predefinição do diretório** *(fx_directory_default_set*) |
| ![Ícone de exclusão de diretório](./media/user-guide/fx-events/image20.png)    | **Diretório Delete** *(fx_directory_delete)* |
| ![Ícone de primeira entrada do diretório](./media/user-guide/fx-events/image21.png)    | **Descoberta de Primeira Entrada** *(fx_directory_first_entry_find)* |
| ![Ícone de primeira entrada completa do diretório](./media/user-guide/fx-events/image22.png)    | **Diretório Primeiro Achado de Entrada Completa** *(fx_directory_first_full_entry_find)* |
| ![Informação do diretório Obter ícone](./media/user-guide/fx-events/image23.png)    | **Informação do Diretório Obter** *(fx_directory_information_get)* |
| ![Ícone de distância local do diretório](./media/user-guide/fx-events/image24.png)    | **Diretório Caminho Local Claro** *(fx_directory_local_path_clear)* |
| ![Diretório caminho local obter ícone](./media/user-guide/fx-events/image25.png)    | **Diretório Caminho Local Obter** *(fx_directory_local_path_get)* |
| ![Ícone de restauro do caminho local do diretório](./media/user-guide/fx-events/image26.png)    | **Diretório Local Path Restore** *(fx_directory_local_path_restore)* |
| ![Ícone do conjunto de caminhos locais do diretório](./media/user-guide/fx-events/image27.png)    | **Conjunto de caminhos locais do diretório** *(fx_directory_local_path_set)* |
| ![Diretório longo nome obter ícone](./media/user-guide/fx-events/image28.png)    | **Diretório De Longo Nome Get** *(fx_directory_long_name_get)* |
| ![Ícone de teste de nome de diretório](./media/user-guide/fx-events/image29.png)    | **Teste de nome do diretório** *(fx_directory_name_test)* |
| ![Diretório Próximo Entrada Encontrar ícone](./media/user-guide/fx-events/image30.png)    | **Diretório Próximo Achado de Entrada** *(fx_directory_next_entry_find)* |
| ![Diretório Próximo Ícone de entrada completa](./media/user-guide/fx-events/image31.png)    | **Diretório Next Full Entry Find** *(fx_directory_next_full_entry_find)* |
| ![Ícone de renome de diretório](./media/user-guide/fx-events/image32.png)    | **Diretório Renome** *(fx_directory_rename)* |
| ![Diretório Nome Curto Obter ícone](./media/user-guide/fx-events/image33.png)    | **Diretório Nome Curto Obter** *(fx_directory_short_name_get)* |
| ![Ícone de atribuição de ficheiros](./media/user-guide/fx-events/image34.png)    | **Atribuição de ficheiros** *(fx_file_allocate)* |
| ![Atributos de arquivo Ler ícone](./media/user-guide/fx-events/image35.png)    | **Leitura de atributos de** arquivo *(fx_file_attributes_read)* |
| ![Ícone de conjunto de atributos de arquivo](./media/user-guide/fx-events/image36.png)    | **Conjunto de atributos de** ficheiro *(fx_file_attributes_set)* |
| ![Ícone de alocação de melhor esforço de arquivo](./media/user-guide/fx-events/image37.png)    | **Alocação de melhor esforço do arquivo** *(fx_file_best_effort_allocate)* |
| ![Ícone de fecho de arquivo](./media/user-guide/fx-events/image38.png)    | **Fecho de Ficheiros** *(fx_file_close)* |
| ![Ícone de criar ficheiro](./media/user-guide/fx-events/image39.png)    | **Criação de Ficheiros** *(fx_file_create)* |
| ![Ícone de definição de tempo de data de arquivo](./media/user-guide/fx-events/image40.png)    | **Definição de hora de data de** arquivo *(fx_file_date_time_set*) |
| ![Ícone de exclusão de ficheiro](./media/user-guide/fx-events/image41.png)    | **Excluir ficheiros** *(fx_file_delete)* |
| ![Ícone de abertura de arquivo](./media/user-guide/fx-events/image42.png)    | **Arquivo Aberto** *(fx_file_open)* |
| ![Ícone de leitura de arquivo](./media/user-guide/fx-events/image43.png)    | **Leitura de Arquivo** *(fx_file_read)* |
| ![Ícone de procura relativa de arquivo](./media/user-guide/fx-events/image44.png)    | **Procura relativa de arquivo** *(fx_file_relative_seek)* |
| ![Ícone de renome de arquivo](./media/user-guide/fx-events/image45.png)    | **Renomear o Ficheiro** *(fx_file_rename)* |
| ![Ícone de procura de arquivo](./media/user-guide/fx-events/image46.png)    | **Procura de Ficheiros** *(fx_file_seek)* |
| ![Ícone de Truncate de arquivo](./media/user-guide/fx-events/image47.png)    | **File Truncate** *(fx_file_truncate)* |
| ![Ícone de lançamento de truncato de arquivo](./media/user-guide/fx-events/image48.png)    | **Lançamento do Truncato de Ficheiros** *(fx_file_truncate_release)* |
| ![Ícone de escrita de arquivo](./media/user-guide/fx-events/image49.png)    | **Escrita de Ficheiros** *(fx_file_write)* |
| ![Ícone de aborto de mídia](./media/user-guide/fx-events/image50.png)    | **Media Abort** *(fx_media_abort)* |
| ![Ícone invalidado de cache de mídia](./media/user-guide/fx-events/image51.png)    | **Media Cache Invalidado** *(fx_media_cache_invalidate)* |
| ![Ícone de verificação de mídia](./media/user-guide/fx-events/image52.png)    | **Verificação de meios** de *comunicação (fx_media_check)* |
| ![*Ícone de close de mídia](./media/user-guide/fx-events/image53.png)    | **Media Close** (*fx_media_close)* |
| ![Ícone de descarga de mídia](./media/user-guide/fx-events/image54.png)    | **Media Flush** *(fx_media_flush)* |
| ![Ícone de formato de mídia](./media/user-guide/fx-events/image55.png)    | **Formato de Mídia** *(fx_media_format)* |
| ![Ícone do Media Open](./media/user-guide/fx-events/image56.png)    | **Media Open** *(fx_media_open)* |
| ![Ícone de leitura de mídia](./media/user-guide/fx-events/image57.png)    | **Media Read** *(fx_media_read)* |
| ![Ícone disponível do espaço de mídia](./media/user-guide/fx-events/image58.png)    | **Espaço de Mídia Disponível** *(fx_media_space_available)* |
| ![Ícone de volume de mídia Obter](./media/user-guide/fx-events/image59.png)    | **Volume de Mídia Get** *(fx_media_volume_get)* |
| ![Ícone de conjunto de volume de mídia](./media/user-guide/fx-events/image60.png)    | **Conjunto de volume de mídia** *(fx_media_volume_set)* |
| ![Ícone de escrita de mídia](./media/user-guide/fx-events/image61.png)    | **Media Write** *(fx_media_write)* |
| ![Ícone de data do sistema](./media/user-guide/fx-events/image62.png)    | **Data do Sistema Obter** *(fx_system_date_get)* |
| ![Ícone de definição de data do sistema](./media/user-guide/fx-events/image63.png)    | **Definição da data do sistema** *(fx_system_date_set)* |
| ![Ícone inicialize o sistema](./media/user-guide/fx-events/image64.png)    | **Inicialização do Sistema** *(fx_system_initialize)* |
| ![Ícone de tempo de sistema obter](./media/user-guide/fx-events/image65.png)    | **System Time Get** *(fx_system_time_get)* |
| ![Ícone de definição de tempo do sistema](./media/user-guide/fx-events/image66.png)    | **Conjunto de tempo do sistema** *(fx_system_time_set)* |
| ![Diretório unicodisco criar ícone](./media/user-guide/fx-events/image67.png)    | **Unicode Directory Create** *(fx_unicode_directory_create)* |
| ![Ícone de renomeação do diretório unicode](./media/user-guide/fx-events/image68.png)    | **Unicode Directory Rename** *(fx_unicode_directory_rename)* |
| ![Ícone de coleção de ficheiro unicode](./media/user-guide/fx-events/image69.png)    | **Unicode File Create** *(fx_unicode_file_create)* |
| ![Ícone de renomeação de ficheiro unicode](./media/user-guide/fx-events/image70.png)    | **Unicode File Rename** *(fx_unicode_file_rename)* |
| ![Unicode Lenght Obter ícone](./media/user-guide/fx-events/image71.png)    | **Unicode Lenght Get** *(fx_unicode_length_get)* |
| ![Unicode Name Get icon](./media/user-guide/fx-events/image72.png)    | **Unicode Name Get** *(fx_unicode_name_get)* |
| ![Unicode Nome Curto Obter ícone](./media/user-guide/fx-events/image73.png)    | **Unicode Short Name Get** *(fx_unicode_short_name_get)* |

## <a name="event-descriptions"></a>Descrições do evento

O seguinte descreve cada evento individual.

### <a name="internal-logical-sector-cache-miss"></a>Falha cache do sector lógico interno 

#### <a name="internal-logical-sector-cache-miss"></a>Falha de cache do setor lógico interno

**Ícone** ![ Cache de setor lógico interno falha ícone](./media/user-guide/fx-events/image1.png)

**Descrição**

Este evento representa uma falha interna do sector lógico do FileX.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Sector.
- Info Field 3: Total de falhas.
- Info Field 4: Tamanho cache.

### <a name="internal-directory-cache-miss"></a>Diretório Interno Cache Miss

#### <a name="internal-directory-cache-miss"></a>Falha de cache de diretório interno

**Ícone** ![ Ícone de falta de cache de diretório interno](./media/user-guide/fx-events/image2.png)

**Descrição** 

Este evento representa uma falha interna do diretório do FileX.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Total de falhas.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="internal-media-flush"></a>Flush de mídia interna 

#### <a name="internal-media-flush"></a>Flush de mídia interna

**Ícone** ![ Ícone de descarga de mídia interna](./media/user-guide/fx-events/image3.png)

**Descrição**

Este evento representa um flush interno de media FileX.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Número de sectores sujos.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.


### <a name="internal-directory-entry-read"></a>Leitura de Entrada no Diretório Interno 

#### <a name="internal-directory-entry-read"></a>Leitura de entrada de diretório interno

**Ícone** ![ Ícone de leitura de diretório interno](./media/user-guide/fx-events/image4.png)

**Descrição**

Este evento representa um evento interno de leitura de diretório filex.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="internal-directory-entry-write"></a>Escrita de entrada no diretório interno

#### <a name="internal-directory-entry-write"></a>Escrita de entrada de diretório interno

**Ícone** ![ Ícone de escrita de diretório interno](./media/user-guide/fx-events/image5.png)

**Descrição**

Este evento representa um evento interno de escrita de diretório filex.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="internal-io-driver-read"></a>Leitura interna do controlador de I/O 

#### <a name="internal-io-driver-read"></a>Leitura interna do controlador de I/O 

**Ícone** ![ Ícone de leitura de i/o interno](./media/user-guide/fx-events/image6.png)

**Descrição** 

Este evento representa um evento interno de leitura de controlador FileX I/O.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Sector.
- Info Campo 3: Número de sectores.
- Info Field 4: Ponteiro tampão.

### <a name="internal-io-driver-write"></a>Escrita interna do condutor de I/O 

#### <a name="internal-io-driver-write"></a>O condutor de I/O interno escreve 

**Ícone** ![ Ícone de escrita interna I/O](./media/user-guide/fx-events/image7.png)

**Descrição** 

Este evento representa um evento interno de escrita do controlador FileX I/O.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Sector.
- Info Campo 3: Número de sectores.
- Info Field 4: Ponteiro tampão.

### <a name="internal-io-driver-flush"></a>Flush de controlador de I/O interno 

#### <a name="internal-io-driver-flush"></a>Flush do condutor de I/O interno 

**Ícone** ![ Ícone de descarga do controlador interno I /O](./media/user-guide/fx-events/image8.png)

**Descrição** 

Este evento representa um evento interno de flush do controlador FileX I/O.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="internal-io-driver-abort"></a>Aborto interno do condutor de I/O 

#### <a name="internal-io-dirver-abort"></a>I/O interno dirver abortar

**Ícone** ![ Ícone de aborto de motorista interno I/O](./media/user-guide/fx-events/image9.png)

**Descrição**

Este evento representa um evento interno de abortar o controlador FileX I/O.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="internal-io-driver-initialize"></a>Inicialização interna do controlador de I/O 

#### <a name="internal-io-driver-initialize"></a>Inicialização do controlador de I/S interno 

**Ícone** ![ Ícone inicializo do condutor interno I/O](./media/user-guide/fx-events/image10.png)

**Descrição** 

Este evento representa um evento de inicialização do controlador FileX I/O interno.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="internal-io-driver-boot-sector-read"></a>Leitura interna do setor de arranque de i/o 

#### <a name="internal-io-driver-boot-sector-read"></a>O setor de arranque de i/S interno lido 

**Ícone** ![ Setor de botas de motorista interno I /O ler ícone](./media/user-guide/fx-events/image11.png)

**Descrição** 

Este evento representa um evento interno do sector de arranque do filex I/O.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro tampão.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="internal-io-driver-release-sectors"></a>Sectores internos de libertação de condutores de I/O 

#### <a name="internal-io-driver-release-sectors"></a>Sectores internos de libertação de condutores de I/O 

**Ícone** ![ Ícone de setores de libertação de motorista interno i/O](./media/user-guide/fx-events/image12.png)

**Descrição** 

Este evento representa um evento interno de lançamento de controlador filex I/O.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Sector.
- Info Campo 3: Número de sectores.
- Info Field 4: Não utilizado.

### <a name="internal-io-driver-boot-sector-write"></a>E/O Setor de Arranque de Motorista Interno Escrever

#### <a name="internal-io-driver-boot-sector-write"></a>O setor de arranque de i/S interno escreve 

**Ícone** ![ Interior I / O setor de botas de motorista escrever ícone](./media/user-guide/fx-events/image13.png)

**Descrição** 

Este evento representa um evento interno do sector de arranque do filex I/O.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro tampão.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="internal-io-driver-un-initialize"></a>Condutor interno de I/O Des-initialize 

#### <a name="internal-io-driver-un-initialize"></a>Condutor interno de I/O desa inicializar 

**Ícone** ![ Ícone interno I / O do condutor des-initialize](./media/user-guide/fx-events/image14.png)

**Descrição** 

Este evento representa um evento interno de des-initialize do controlador FileX I/O.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.
</blockquote></td>

### <a name="directory-attributes-read"></a>Leitura de atributos de diretório 

#### <a name="fx_directory_attributes_read"></a>fx_directory_attributes_read 

**Ícone** ![ Ícone de leitura de atributos de diretório](./media/user-guide/fx-events/image15.png)

**Descrição** 

Este evento representa um evento de atributos de diretório.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para o nome do diretório.
- Info Field 3: Atributos mapa bit:

  | Atributo                         | Valor        |
  |---------------------------------- | --------|
  |  Só de Leitura                        | (0x01)  |
  |  Oculto                           | (0x02)  |
  |  Sistema                           | (0x04)  |
  |  Volume                           | (0x08)  |
  |  Diretório                        | (0x10)  |
  |  Arquivo                          | (0x20)  |
- Info Field 4: Não utilizado.

### <a name="directory-attributes-set"></a>Conjunto de atributos de diretório 

#### <a name="fx_directory_attributes_set"></a>fx_directory_attributes_set 

**Ícone** ![ Ícone de conjunto de atributos](./media/user-guide/fx-events/image16.png)

**Descrição** 

Este evento representa um diretório de um evento de atributos de diretório.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para o nome do diretório.
- Info Field 3: Atributos mapa bit:

  |  Atributo                        | Valor        |
  |---------------------------------- | --------|
  |  Só de Leitura                        | (0x01)  |
  |  Oculto                           | (0x02)  |
  |  Sistema                           | (0x04)  |
  |  Arquivo                          | (0x20)  |
- Info Field 4: Não utilizado.

### <a name="directory-create"></a>Criar Diretório 

#### <a name="fx_directory_create"></a>fx_directory_create

**Ícone** ![ Diretório criar ícone](./media/user-guide/fx-events/image17.png)

**Descrição** 

Este evento representa um evento de criação de diretório.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para o nome do diretório.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="directory-default-get"></a>Diretório Predefinido Obter 

#### <a name="fx_directory_default_get"></a>fx_directory_default_get 

**Ícone** ![ Diretório padrão obter ícone](./media/user-guide/fx-events/image18.png)

**Descrição** 

Este evento representa um evento definido por padrão de diretório.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para devolver o nome do caminho.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="directory-default-set"></a>Conjunto de predefinição do diretório 

#### <a name="fx_directory_default_set"></a>fx_directory_default_set 

**Ícone** ![ Ícone de conjunto de padrão de diretório](./media/user-guide/fx-events/image19.png)

**Descrição** 

Este evento representa um evento definido por padrão de diretório.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para novo nome do caminho predefinido.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="directory-delete"></a>Diretório Delete 

#### <a name="fx_directory_delete"></a>fx_directory_delete

**Ícone** ![ Ícone de exclusão de diretório](./media/user-guide/fx-events/image20.png)

**Descrição** 

Este evento representa um evento de exclusão de diretório.

**Campos de Informação**
- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para o nome do diretório.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="directory-first-entry-find"></a>Descoberta de primeira entrada do diretório 

#### <a name="fx_directory_first_entry_find"></a>fx_directory_first_entry_find

**Ícone** ![ Primeiro diretório encontrar ícone](./media/user-guide/fx-events/image21.png)

**Descrição** 

Este evento representa um evento de primeira entrada.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para o nome do diretório.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="directory-first-full-entry-find"></a>Primeira descoberta de entrada completa do diretório 

#### <a name="fx_directory_first_full_entry_find"></a>fx_directory_first_full_entry_find

**Ícone** ![ Primeiro diretório de entrada completa encontrar ícone](./media/user-guide/fx-events/image22.png)

**Descrição** 

Este evento representa um evento de primeira entrada completa.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para o nome do diretório.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="directory-information-get"></a>Informação do Diretório Obter 

#### <a name="fx_directory_information_get"></a>fx_directory_information_get

**Ícone** ![ Informação de diretório obter ícone](./media/user-guide/fx-events/image23.png)

**Descrição** 

Este evento representa um evento de informação de diretório.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para o nome do diretório.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="directory-local-path-clear"></a>Diretório Caminho Local Claro 

#### <a name="fx_directory_local_path_clear"></a>fx_directory_local_path_clear

**Ícone** ![ Ícone claro do caminho local do diretório](./media/user-guide/fx-events/image24.png)

**Descrição** 

Este evento representa um diretório local evento claro.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="directory-local-path-get"></a>Diretório Caminho Local Obter 

#### <a name="fx_directory_local_path_get"></a>fx_directory_local_path_get

**Ícone** ![ Diretório caminho local obter ícone](./media/user-guide/fx-events/image25.png)

**Descrição** 

Este evento representa um diretório local obter evento.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para devolver o nome do caminho.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="directory-local-path-restore"></a>Restauração do Caminho Local do Diretório 

#### <a name="fx_directory_local_path_restore"></a>fx_directory_local_path_restore

**Ícone** ![ Ícone de restauro do caminho local do diretório](./media/user-guide/fx-events/image26.png)

**Descrição** 

Este evento representa um evento de restauração do percurso local.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para a estrutura do caminho local.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="directory-local-path-set"></a>Conjunto de caminhos locais do diretório 

#### <a name="fx_directory_local_path_set"></a>fx_directory_local_path_set

**Ícone** ![ Ícone de conjunto de caminho local diretório](./media/user-guide/fx-events/image27.png)

**Descrição** 

Este evento representa um evento de diretório local.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para a estrutura do caminho local.
- Info Field 3: Ponteiro para novo nome do caminho.
- Info Field 4: Não utilizado.

### <a name="directory-long-name-get"></a>Diretório Longo Nome Obter 

#### <a name="fx_directory_long_name_get"></a>fx_directory_long_name_get

**Ícone** ![ Diretório longo nome obter ícone](./media/user-guide/fx-events/image28.png)

**Descrição** 

Este evento representa um evento de nome longo do diretório.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para nome de ficheiro curto.
- Info Field 3: Ponteiro para o nome do ficheiro longo.
- Info Field 4: Não utilizado.

### <a name="directory-name-test"></a>Teste de nome de diretório 

#### <a name="fx_directory_name_test"></a>fx_directory_name_test

**Ícone** ![ Ícone de teste de nome de diretório](./media/user-guide/fx-events/image29.png)

**Descrição** 

Este evento representa um evento de teste de nome de diretório.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para o nome do diretório.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="directory-next-entry-find"></a>Diretório Próximo Encontro de Entrada 

#### <a name="fx_directory_next_entry_find"></a>fx_directory_next_entry_find

**Ícone** ![ Diretório próxima entrada encontrar ícone](./media/user-guide/fx-events/image30.png)

**Descrição** 

Este evento representa um evento de entrada seguinte.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para o nome do diretório.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="directory-next-full-entry-find"></a>Diretório Próximo Encontro de Entrada Completa 

#### <a name="fx_directory_next_full_entry_find"></a>fx_directory_next_full_entry_find

**Ícone** ![ Diretório próxima entrada completa encontrar ícone](./media/user-guide/fx-events/image31.png)

**Descrição**

Este evento representa um evento de entrada completa no próximo diretório.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para o nome do diretório.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="directory-rename"></a>Renomeador de Diretório 

#### <a name="fx_directory_rename-event"></a>evento fx_directory_rename

**Ícone** ![ Ícone de renome de diretório](./media/user-guide/fx-events/image32.png)

**Descrição**

Este evento representa um evento de renomeação de diretório.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para o nome do diretório antigo.
- Info Field 3: Ponteiro para novo nome do diretório.
- Info Field 4: Não utilizado.

### <a name="directory-short-name-get"></a>Diretório Nome Curto Obter 

#### <a name="fx_directory_short_name_get"></a>fx_directory_short_name_get

**Ícone** ![ Diretório nome curto obter ícone](./media/user-guide/fx-events/image33.png)

**Descrição**

Este evento representa um evento de nome curto de diretório.

**Campos de Informação** 

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para o nome do ficheiro longo.
- Info Field 3: Ponteiro para nome de ficheiro curto.
- Info Field 4: Não utilizado.

### <a name="file-allocate"></a>Atribuição de ficheiros 

#### <a name="fx_file_allocate"></a>fx_file_allocate

**Ícone** ![ Ícone de atribuição de arquivo](./media/user-guide/fx-events/image34.png)

**Descrição**

Este evento representa um evento de atribuição de ficheiros.

**Campos de Informação**

- Info Field 1: Ponteiro para o ficheiro.
- Info Field 2: Tamanho solicitado.
- Info Field 3: Tamanho atual.
- Info Field 4: Novo tamanho.

### <a name="file-attributes-read"></a>Leitura de atributos de arquivo 

#### <a name="fx_file_attributes_read"></a>fx_file_attributes_read

**Ícone** ![ Ícone de leitura de atributos de arquivo](./media/user-guide/fx-events/image35.png)

**Descrição**

Este evento representa um evento de leitura de atributos de ficheiro.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação. 
- Info Field 2: Atributos mapa bit:

  |  Atributo                         | Valor        |
  |---------------------------------- | --------|
  |  Só de Leitura                        | (0x01)  |
  |  Oculto                           | (0x02)  |
  |  Sistema                           | (0x04)  |
  |  Volume                           | (0x08)  |
  |  Diretório                        | (0x10)  |
  |  Arquivo                          | (0x20)  |
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="file-attributes-set"></a>Conjunto de atributos de arquivo 

#### <a name="fx_file_attributes_set"></a>fx_file_attributes_set

**Ícone** ![ Ícone de conjunto de atributos de arquivo](./media/user-guide/fx-events/image36.png)

**Descrição** 

Este evento representa um evento de conjunto de atributos de ficheiro.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para o nome do ficheiro. 
- Info Field 3: Atributos mapa bit:

  | Atributo                         | Valor        |
  |---------------------------------- | --------|
  |  Só de Leitura                        | (0x01)  |
  |  Oculto                           | (0x02)  |
  |  Sistema                           | (0x04)  |
  |  Arquivo                          | (0x20)  |
- Info Field 4: Não utilizado.

### <a name="file-best-effort-allocate"></a>Alocação de melhor esforço do arquivo 

#### <a name="fx_file_best_effort_allocate"></a>fx_file_best_effort_allocate

**Ícone** ![ Arquivo melhor esforço alocar ícone](./media/user-guide/fx-events/image37.png)

**Descrição** 

Este evento representa um evento de melhor esforço de arquivo.

**Campos de Informação**

- Info Field 1: Ponteiro para o ficheiro.
- Info Field 2: Tamanho solicitado.
- Info Field 3: Tamanho real atribuído.
- Info Field 4: Não utilizado.

### <a name="file-close"></a>Arquivo Fechar 

#### <a name="fx_file_close"></a>fx_file_close

**Ícone** ![ Ícone de fecho de arquivo](./media/user-guide/fx-events/image38.png)

**Descrição** 

Este evento representa um evento de encerramento de ficheiros.

**Campos de Informação**

- Info Field 1: Ponteiro para o ficheiro.
- Info Field 2: Tamanho do ficheiro.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="file-create"></a>Criar ficheiros

#### <a name="fx_file_create"></a>fx_file_create

**Ícone** ![ Ícone de criação de arquivo](./media/user-guide/fx-events/image39.png)

**Descrição**

Este evento representa um evento de criação de ficheiros.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para o nome do ficheiro.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="file-date-time-set"></a>Conjunto de tempo de data de arquivo 

#### <a name="fx_file_date_time_set"></a>fx_file_date_time_set

**Ícone** ![ Ícone de definição de hora de data de arquivo](./media/user-guide/fx-events/image40.png)

**Descrição**

Este evento representa um evento de data/hora de arquivo.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para o nome do ficheiro.
- Campo de Informações 3: Ano.
- Info Field 4: Mês.

### <a name="file-delete"></a>Apagar ficheiros 

#### <a name="fx_file_delete"></a>fx_file_delete

**Ícone** ![ Ícone de exclusão de ficheiro](./media/user-guide/fx-events/image41.png)

**Descrição**

Este evento representa um evento de eliminação de ficheiros.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para o nome do ficheiro.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="file-open"></a>Arquivo Aberto 

#### <a name="fx_file_open"></a>fx_file_open

**Ícone** ![ Ícone aberto de arquivo](./media/user-guide/fx-events/image42.png)

**Descrição**

Este evento representa um evento aberto de arquivos.

**Campos de Informação** 

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para o bloco de controlo de ficheiros.
- Info Field 3: Ponteiro para o nome do ficheiro.
- Info Field 4: Tipo aberto:

  |  Tipo aberto                        | Valor        |
  |---------------------------------- | --------|
  |  Aberto para Ler                    | (0x00)  |
  |  Aberto para Escrita                   | (0x01)  |
  |  Open rápido para leitura               | (0x02)  |

### <a name="file-read"></a>Leitura de Arquivos 

#### <a name="fx_file_read"></a>fx_file_read

**Ícone** ![ Ícone de leitura de arquivo](./media/user-guide/fx-events/image43.png)

**Descrição**

Este evento representa um evento de leitura de ficheiros.

**Campos de Informação**

- Info Field 1: Ponteiro para o ficheiro.
- Info Field 2: Ponteiro tampão.
- Info Campo 3: Tamanho do pedido.
- Info Field 4: Leitura do tamanho real.

### <a name="file-relative-seek"></a>Procura relativa de arquivo 

#### <a name="fx_file_relative_seek"></a>fx_file_relative_seek

**Ícone** ![ Ícone de procura relativa de arquivo](./media/user-guide/fx-events/image44.png)

**Descrição**

Este evento representa um evento de procura de arquivo relativo.

**Campos de Informação**

- Info Field 1: Ponteiro para o ficheiro.
- Info Field 2: Byte offset.
- Info Field 3: Procurar a partir de:

  | Evento                             | Valor        |
  |---------------------------------- | --------|
  |  Desde o início                   | (0x00)  |
  |  De Fim                         | (0x01)  | 
  |  a frente                          | (0x02)  |
  |  para trás                         | (0x03)  |
- Info Field 4: Offset anterior.

### <a name="file-rename"></a>Renomear o Ficheiro 

#### <a name="fx_file_rename"></a>fx_file_rename

**Ícone** ![ Ícone de renome de arquivo](./media/user-guide/fx-events/image45.png)

**Descrição**

Este evento representa um evento de renome de ficheiro.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para o nome do ficheiro antigo.
- Info Field 3: Ponteiro para novo nome do ficheiro.
- Info Field 4: Não utilizado.

### <a name="file-seek"></a>Procura de Arquivos 

#### <a name="fx_file_seek"></a>fx_file_seek

**Ícone** ![ Ícone de procura de arquivo](./media/user-guide/fx-events/image46.png)

**Descrição**

Este evento representa um evento de procura de ficheiros.

**Campos de Informação** 

- Info Field 1: Ponteiro para o ficheiro.
- Info Field 2: Byte offset.
- Info Field 3: Offset anterior.
- Info Field 4: Não utilizado.

### <a name="file-truncate"></a>Arquivo Truncate 

#### <a name="fx_file_truncate"></a>fx_file_truncate

**Ícone** ![ Ícone truncado de arquivo](./media/user-guide/fx-events/image47.png)

**Descrição**

Este evento representa um evento truncado de arquivo.

**Campos de Informação**

- Info Field 1: Ponteiro para o ficheiro.
- Info Field 2: Tamanho solicitado.
- Info Field 3: Tamanho anterior.
- Info Field 4: Novo tamanho.

### <a name="file-truncate-release"></a>Lançamento do Truncato de Ficheiros 

#### <a name="fx_file_truncate_release"></a>fx_file_truncate_release 

**Ícone** ![ Ícone de libertação de truncato de arquivo](./media/user-guide/fx-events/image48.png)

**Descrição**

Este evento representa um evento de lançamento truncado de ficheiros.

**Campos de Informação**

- Info Field 1: Ponteiro para o ficheiro.
- Info Field 2: Tamanho solicitado.
- Info Field 3: Tamanho anterior.
- Info Field 4: Novo tamanho.

### <a name="file-write"></a>Escrita de Arquivo 

#### <a name="fx_file_write"></a>fx_file_write 

**Ícone** ![ Ícone de escrita de arquivo](./media/user-guide/fx-events/image49.png)

**Descrição**

Este evento representa um evento de escrita de ficheiros.

**Campos de Informação**

- Info Field 1: Ponteiro para o ficheiro.
- Info Field 2: Ponteiro tampão.
- Info Campo 3: Tamanho do pedido.
- Info Field 4: Tamanho real escrito.

### <a name="media-abort"></a>Aborto dos meios de comunicação 

#### <a name="fx_media_abort"></a>fx_media_abort 

**Ícone** ![ Ícone de aborto de mídia](./media/user-guide/fx-events/image50.png)

**Descrição**

Este evento representa um evento de aborto mediático.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="media-cache-invalidate"></a>Cache de media invalidado

#### <a name="fx_media_cache_invalidate"></a>fx_media_cache_invalidate

**Ícone** ![ Ícone invalidado de cache de mídia](./media/user-guide/fx-events/image51.png)

**Descrição**

Este evento representa um evento invalidado de cache de mídia.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="media-check"></a>Verificação de meios de comunicação 

#### <a name="fx_media_check"></a>fx_media_check

**Ícone** ![ Ícone de verificação de mídia](./media/user-guide/fx-events/image52.png)

**Descrição**

Este evento representa um evento de verificação de mídia.

**Campos de Informação** 

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro de memória de risco.
- Info Field 3: Riscar o tamanho da memória.
- Info Field 4: Mapa de bits de erros:

  | Tipo de erro                        | Valor        |
  |---------------------------------- | --------|
  |  Erro da cadeia fat                  | (0x01)  |
  |  Erro do Diretório                  | (0x02)  |
  |  Erro de cluster perdido               | (0x04)  |
  |  Erro do tamanho do ficheiro                  | (0x08)  |

### <a name="media-close"></a>Media Close 

#### <a name="fx_media_close"></a>fx_media_close

**Ícone** ![ Ícone de close de mídia](./media/user-guide/fx-events/image53.png)

**Descrição**

Este evento representa um evento mediático.

**Campos de Informação** 

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="media-flush"></a>Media Flush 

#### <a name="fx_media_flush"></a>fx_media_flush

**Ícone** ![ Ícone de descarga de mídia](./media/user-guide/fx-events/image54.png)

**Descrição**

Este evento representa um evento de media flush.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="media-format"></a>Formato de mídia 

#### <a name="fx_media_format"></a>fx_media_format

**Ícone** ![ Ícone de formato de mídia](./media/user-guide/fx-events/image55.png)

**Descrição**

Este evento representa um evento de formato mediático.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Campo 2: Número de entradas de raiz.
- Info Field 3: Sectores.
- Info Field 4: Sectores por cluster.

### <a name="media-open"></a>Media Open 

#### <a name="fx_media_open"></a>fx_media_open

**Ícone** ![ Ícone aberto de mídia](./media/user-guide/fx-events/image56.png)

**Descrição**

Este evento representa um evento aberto à comunicação social.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para a entrada do controlador de mídia.
- Info Campo 3: Ponteiro de memória.
- Info Campo 4: Tamanho da memória.

### <a name="media-read-media-read"></a>Leitura de Mídia 

#### <a name="fx_media_read"></a>fx_media_read

**Ícone** ![ Ícone de leitura de mídia](./media/user-guide/fx-events/image57.png)

**Descrição**

Este evento representa um evento de leitura mediática.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Sector lógico.
- Info Field 3: Ponteiro tampão.
- Info Field 4: Bytes read.

### <a name="media-space-available"></a>Espaço de Mídia Disponível 

#### <a name="fx_media_space_available"></a>fx_media_space_available

**Ícone** ![ Ícone disponível do espaço dos media](./media/user-guide/fx-events/image58.png)

**Descrição**

Este evento representa um evento de espaço de comunicação disponível.

**Campos de Informação** 

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro bytes disponível.
- Info Campo 3: Número de aglomerados gratuitos.
- Info Field 4: Não utilizado.

### <a name="media-volume-get"></a>Volume de mídia Obter 

#### <a name="fx_media_volume_get"></a>fx_media_volume_get

**Ícone** ![ Ícone de obter volume de mídia](./media/user-guide/fx-events/image59.png)

**Descrição**

Este evento representa um evento de volume mediático.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Campo 2: Ponteiro para o nome do volume.
- Info Field 3: Fonte de volume.
- Info Field 4: Não utilizado.

### <a name="media-volume-set"></a>Conjunto de volume de mídia 

#### <a name="fx_media_volume_set"></a>fx_media_volume_set

**Ícone** ![ Ícone de conjunto de volume de mídia](./media/user-guide/fx-events/image60.png)

**Descrição**

Este evento representa um evento de volume mediático.

**Campos de Informação** 
- Info Field 1: Ponte para os meios de comunicação.
- Info Campo 2: Ponteiro para o nome do volume.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="media-write"></a>Escrita de mídia 

#### <a name="fx_media_write"></a>fx_media_write

**Ícone** ![ Ícone de escrita de mídia](./media/user-guide/fx-events/image61.png)

**Descrição**

Este evento representa um evento de escrita mediática.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Sector lógico.
- Info Field 3: Ponteiro tampão.
- Info Field 4: Bytes escritos.

### <a name="system-date-get"></a>Data do Sistema Obter 

#### <a name="fx_system_date_get"></a>fx_system_date_get 

**Ícone** ![ Data do sistema obter ícone](./media/user-guide/fx-events/image62.png)

**Descrição**

Este evento representa um evento de data do sistema.

**Campos de Informação**

- Campo de Informações 1: Ano.
- Info Field 2: Mês.
- Info Field 3: Dia.
- Info Field 4: Não utilizado.

### <a name="system-date-set"></a>Conjunto de datas do sistema 

#### <a name="fx_system_date_set"></a>fx_system_date_set 

**Ícone** ![ Ícone de definição de data do sistema](./media/user-guide/fx-events/image63.png)

**Descrição**

Este evento representa um evento de data definida para o sistema.

**Campos de Informação**

- Campo de Informações 1: Ano.
- Info Field 2: Mês.
- Info Field 3: Dia.
- Info Field 4: Não utilizado.

### <a name="system-initialize"></a>Inicialização do sistema 

#### <a name="fx_system_initialize"></a>fx_system_initialize 

**Ícone** ![ Ícone inicializando o sistema](./media/user-guide/fx-events/image64.png)

**Descrição**

Este evento representa um evento inicialização do sistema.

**Campos de Informação**

- Info Field 1: Não utilizado.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="system-time-get"></a>Tempo do sistema obter 

#### <a name="fx_system_time_get"></a>fx_system_time_get 

**Ícone** ![ Tempo do sistema obter ícone](./media/user-guide/fx-events/image65.png)

**Descrição**

Este evento representa um evento de tempo do sistema.

**Campos de Informação** 

- Info Field 1: Hora.
- Info Field 2: Minuto.
- Info Field 3: Segundo.
- Info Field 4: Não utilizado.

### <a name="system-time-set"></a>Conjunto de tempo do sistema 

#### <a name="fx_system_time_set"></a>fx_system_time_set 

**Ícone** ![ Ícone de definição de tempo do sistema](./media/user-guide/fx-events/image66.png)

**Descrição**

Este evento representa um evento de tempo definido pelo sistema.

**Campos de Informação**

- Info Field 1: Hora.
- Info Field 2: Minuto.
- Info Field 3: Segundo.
- Info Field 4: Não utilizado.

### <a name="unicode-directory-create"></a>Unicode Directy Criar 

#### <a name="fx_unicode_directory_create"></a>fx_unicode_directory_create 

**Ícone** ![ Diretório unicode criar ícone](./media/user-guide/fx-events/image67.png)

**Descrição**

Este evento representa um evento de criação de diretório Unicode.

**Campos de Informação** 

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para o nome Unicode.
- Info Field 3: Tamanho do nome Unicode.
- Info Field 4: Ponteiro para nome curto.

### <a name="unicode-directory-rename"></a>Nomeão de Unicode 

#### <a name="fx_unicode_directory_rename"></a>fx_unicode_directory_rename

**Ícone** ![ Ícone de renome de diretório unicode](./media/user-guide/fx-events/image68.png)

**Descrição**

Este evento representa um evento de renomeação do Unicode.

**Campos de Informação** 

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para o nome Unicode.
- Info Field 3: Tamanho do nome Unicode.
- Info Field 4: Ponteiro para nome curto.

### <a name="unicode-file-create"></a>Unicode File Create 

#### <a name="fx_unicode_file_create"></a>fx_unicode_file_create

**Ícone** ![ Ícone de criação de ficheiro unicode](./media/user-guide/fx-events/image69.png)

**Descrição**

Este evento representa um evento de criação de ficheiros Unicode.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para o nome Unicode.
- Info Field 3: Tamanho do nome Unicode.
- Info Field 4: Ponteiro para nome curto.

### <a name="unicode-file-rename"></a>Renomear ficheiro Unicode 

#### <a name="fx_unicode_file_rename"></a>fx_unicode_file_rename

**Ícone** ![ Ícone de renome de ficheiro unicode](./media/user-guide/fx-events/image70.png)

**Descrição**

Este evento representa um evento de renomeação de ficheiros Unicode.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para o nome Unicode.
- Info Field 3: Tamanho do nome Unicode.
- Info Field 4: Ponteiro para nome curto.

### <a name="unicode-length-get"></a>Unicode Length Get 

#### <a name="fx_unicode_length_get"></a>fx_unicode_length_get

**Ícone** ![ Unicode comprimento obter ícone](./media/user-guide/fx-events/image71.png)

**Descrição**

Este evento representa um evento unicode length get.

**Campos de Informação**

- Info Field 1: Ponteiro para o nome Unicode.
- Info Field 2: Comprimento.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="unicode-name-get"></a>Nome Unicode Obter 

#### <a name="fx_unicode_name_get"></a>fx_unicode_name_get

**Ícone** ![ Unicode nome obter ícone](./media/user-guide/fx-events/image72.png)

**Descrição**

Este evento representa um evento de nome Unicode.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Nome curto de origem.
- Info Field 3: Destino Unicode nome pointer.
- Info Field 4: Destino Unicode comprimento do nome.

### <a name="unicode-short-name-get"></a>Unicode Short Name Get 

#### <a name="fx_unicode_short_name_get"></a>fx_unicode_short_name_get

**Ícone** ![ Unicode nome curto obter ícone](./media/user-guide/fx-events/image73.png)

**Descrição**

Este evento representa um evento de nome curto Unicode.

**Campos de Informação**

- Info Field 1: Ponte para os meios de comunicação.
- Info Field 2: Ponteiro para fonte Nome Unicode.
- Info Field 3: Comprimento do nome Unicode.
- Info Field 4: Ponteiro para nome curto.