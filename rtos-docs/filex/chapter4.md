---
title: Capítulo 4- Descrição dos serviços Azure RTOS FileX
description: Este capítulo contém uma descrição de todos os serviços Azure RTOS FileX por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 948adff65a080649db0870e35bc75ee774775cb7
ms.sourcegitcommit: 4cbe92b337e82124bb5a86d319b787eb05b4ea76
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/27/2021
ms.locfileid: "108067017"
---
# <a name="chapter-4--description-of-azure-rtos-filex-services"></a>Capítulo 4- Descrição dos serviços Azure RTOS FileX

Este capítulo contém uma descrição de todos os serviços Azure RTOS FileX por ordem alfabética. Os nomes de serviço são projetados para que todos os serviços similares sejam agrupados.

## <a name="fx_directory_attributes_read"></a>fx_directory_attributes_read

Lê atributos de diretório

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_attributes_read ( 
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes_ptr);
```

### <a name="description"></a>Description

Este serviço lê os atributos do diretório a partir dos meios de comunicação especificados.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.
- **directory_name**: Ponteiro para o nome do diretório solicitado (o percurso do diretório é opcional).
- **atributos** _ptr: Ponteiro para o destino para os atributos do diretório a serem colocados. Os atributos do diretório são devolvidos num formato de mapa bit com as seguintes definições possíveis:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_VOLUME (0x08)
  - FX_DIRECTORY (0x10)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Atributos de diretório de sucesso lidos
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos
- **FX _NOT FOUND** (0x04) Diretório especificado não foi encontrado nos meios de comunicação
- **FX_NOT_DIRECTORY** (0x0E) A entrada não é um diretório
- **erro de** FX_IO_ERROR (0x90) do condutor I/O
- **FX_FILE_CORRUPT** 0x08) Arquivo é corrompido
- **FX_SECTOR_INVALID** (0x89) Sector inválido
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada da FAT
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação
- **FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos
- **FX_PTR_ERROR** (0x18) Ponteiro de meios inválidos
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA     my_media;
UINT     status;
/* Retrieve the attributes of "mydir" from the specified media.*/
status = fx_directory_attributes_read(&my_media, "mydir", &attributes);
/* If status equals FX_SUCCESS, "attributes" contains the directory attributes of "mydir". */
```

### <a name="see-also"></a>Consulte também

- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_attributes_set"></a>fx_directory_attributes_set

Define atributos de diretório

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes);
```

### <a name="description"></a>Description

Este serviço define os atributos do diretório aos especificados pelo autor da chamada.

> [!WARNING]
> *Esta aplicação só é permitida para modificar um subconjunto dos atributos do diretório com este serviço. Qualquer tentativa de definir atributos adicionais resultará num erro.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.
- **directory_name**: Ponteiro para o nome do diretório solicitado (o percurso do diretório é opcional).
- **atributos**: Os novos atributos a este diretório. Os atributos de diretório válidos são definidos da seguinte forma:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Conjunto de atributos de sucesso
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos
- **FX_NOT_FOUND** (0x04) Diretório especificado não foi encontrado nos meios de comunicação
- **FX_NOT_DIRECTORY** (0x0E) A entrada não é um diretório
- **erro de** FX_IO_ERROR (0x90) do condutor I/O
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito
- **FX_FILE_CORRUPT** (0x08) File é corrompido
- **FX_SECTOR_INVALID** (0x89) Sector inválido
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada da FAT
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação
- **FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas neste diretório
- **FX_PTR_ERROR** (0x18) Ponteiro de meios inválidos
- **FX_INVALID_ATTR** (0x19) Atributos inválidos selecionados.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA             my_media;
UINT                 status;
status = fx_directory_attributes_set(&my_media, "mydir", FX_READ_ONLY);
/*Set the attributes of "mydir" to read-only. */
/* If status equals FX_SUCCESS, the directory "mydir" is read-only. */
```

### <a name="see-also"></a>Consulte também

- fx_directory_attributes_read
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_create"></a>fx_directory_create

Cria subdireção

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_create(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```
### <a name="description"></a>Description

Este serviço cria uma subdiretório no diretório predefinido atual ou no caminho fornecido no nome do diretório. Ao contrário do diretório de raiz, as subdiretórios não têm um limite para o número de ficheiros que podem reter. O diretório de raiz só pode conter o número de entradas determinadas pelo registo de arranque.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.
- **directory_name**: Pontear o nome do diretório para criar (o caminho do diretório é opcional).

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Diretório de sucesso criar.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos
- **FX_NOT_FOUND** (0x04) Diretório especificado não foi encontrado nos meios de comunicação
- **FX_NOT_DIRECTORY** (0x0E) A entrada não é um diretório
- **erro de** FX_IO_ERROR (0x90) do condutor I/O
- **FX_FILE _CORRUPT** (0x08) File é corrompido
- **FX_SECTOR_INVALID** (0x89) Sector inválido
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada da FAT
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação
- **FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas neste diretório
- **FX_PTR_ERROR** (0x18) Ponteiro de meios inválidos
- **FX_INVALID_ATTR** (0x19) Atributos inválidos selecionados.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA             my_media;
UINT                 status;
/* Create a subdirectory called "temp" in the current default directory. */

status = fx_directory_create(&my_media, "temp");

/* If status equals FX_SUCCESS, the new subdirectory "temp" has been created. */
```

### <a name="see-also"></a>Consulte também

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_default_get"></a>fx_directory_default_get

Obtém o último diretório predefinido

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_default_get(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a>Description

Este serviço devolve o ponteiro ao caminho definido pela ***última vez por fx_directory_default_set***. Se o diretório predefinido não tiver sido definido ou se o diretório predefinido atual for o diretório de raiz, é devolvido um valor de FX_NULL.

> [!IMPORTANT]
> *O tamanho padrão da cadeia de caminho interno é de 256 caracteres; pode ser alterado modificando **FX_MAXIMUM_PATH** em **fx_api.h** e reconstruindo toda a biblioteca Do FicheiroX. O caminho da corda do personagem é mantido para a aplicação e não é usado internamente pelo FileX.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.
- **return_path_name**: Pontear o destino para a última cadeia de diretório predefinido. Um valor de FX_NULL é devolvido se a configuração atual do diretório predefinido for a raiz. Quando o meio de comunicação é aberto, a raiz é o padrão.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Diretório padrão de sucesso obter
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos
- **FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiro de destino.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA my_media;
CHAR *current_default_dir;
UINT status;
/* Retrieve the current default directory. */
status = fx_directory_default_get(&my_media, &current_default_dir);
/* If status equals FX_SUCCESS, "current_default_dir" 
    contains a pointer to the current default directory).*/
```

### <a name="see-also"></a>Consulte também

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_default_set"></a>fx_directory_default_set

Define diretório predefinido

### <a name="prototype"></a>Prototype

```c

UINT fx_directory_default_set(
    FX_MEDIA *media_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a>Description

Este serviço define o diretório predefinido dos meios de comunicação. Se for fornecido um valor de FX_NULL, o diretório predefinido é definido para o diretório de raiz dos meios de comunicação. Todas as operações de ficheiro subsequentes que não especificam explicitamente um caminho por defeito a este diretório.

> [!IMPORTANT]
> *O tamanho padrão da cadeia de caminho interno é de 256 caracteres; pode ser alterado modificando **FX_MAXIMUM_PATH** em **fx_api.h** e reconstruindo toda a biblioteca Do FicheiroX. O caminho da corda do personagem é mantido para a aplicação e não é usado internamente pelo FileX.*

> [!IMPORTANT]
> *Para os nomes fornecidos pela aplicação, o FileX suporta caracteres backslash \\ (/ ) e barras para a frente (/) para diretórios separados, subdiretórios e nomes de ficheiros. No entanto, o FileX utiliza apenas o carácter backslash nos caminhos devolvidos à aplicação.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.
- **new_path_name**: Ponteiro para novo nome de diretório predefinido. Se for fornecido um valor de FX_NULL, o diretório predefinido dos meios de comunicação é definido para o diretório de raiz dos meios de comunicação.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Conjunto de diretório padrão de sucesso
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos
- **FX_INVALID_PATH** (0x0D) Novo diretório não foi encontrado
- **FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_default_set(&my_media, "\\abc\\def\\ghi");
/* If status equals FX_SUCCESS, the default directory for this media is \abc\def\ghi. All subsequent file operations that do not explicitly specify a path will default to this directory. Note that the character "\" serves as an escape character in a string. To represent the character "\", use the construct "\\". This is done because of the C language- only one "\" is really present in the string. */
```

### <a name="see-also"></a>Consulte também

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_delete"></a>fx_directory_delete

Elimina subdireção

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_delete(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a>Description

Este serviço elimina o diretório especificado. Note que o diretório deve estar vazio para eliminá-lo.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.
- **directory_name**: Ponteiro para o nome do diretório para apagar (o caminho do diretório é opcional).

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Diretório de sucesso
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos
- **FX_NOT_FOUND** (0x04) Não foi encontrado diretório especificado
- **FX_DIR_NOT_EMPTY** (0x10) Diretório especificado não está vazio
- **erro de** FX_IO_ERROR (0x90) do condutor I/O
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito
- **FX_FILE_CORRUPT** (0x08) File é corrompido
- **FX_SECTOR_INVALID** (0x89) Sector inválido
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada da FAT
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação
- **FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas neste diretório
- **FX_NOT_DIRECTORY** (0x0E) Não uma entrada de diretório
- **FX_PTR_ERROR** (0x18) Ponteiro de meios inválidos
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo
```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_delete(&my_media, "abc");
/* Delete the subdirectory "abc." */
/* If status equals FX_SUCCESS, the subdirectory "abc" was deleted. */
```

### <a name="see-also"></a>Consulte também

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_first_entry_find"></a>fx_directory_first_entry_find

Obtém a primeira entrada no diretório

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_first_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a>Description

Este serviço recupera o primeiro nome de entrada no diretório predefinido e copia-o para o destino especificado.

> [!WARNING]
> *O destino especificado deve ser grande o suficiente para conter o nome FileX de tamanho máximo, tal como definido por **FX_MAX_LONG_NAME_LEN.***

> [!WARNING]
> *Se utilizar um caminho não local, é importante evitar (com um semáforo ThreadX, mutex ou mudança de nível prioritário) que outros fios de aplicação mudem este diretório enquanto está a decorrer um diretório. Caso contrário, podem ser obtidos resultados inválidos.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.
- **return_entry_name**: Ponteiro para o destino para o primeiro nome de entrada no diretório predefinido.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Primeira entrada de diretório bem sucedida
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas neste diretório
- **erro de** FX_IO_ERROR (0x90) do condutor I/O
- **FX_FILE_CORRUPT** (0x08) File é corrompido
- **FX_SECTOR_INVALID** (0x89) Sector inválido
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada da FAT
- **FX_PTR_ERROR** (0x18) Meios inválidos ou ponteiro de destino
- **FX_CALLER_ERROR** (0x20) Caller não é um fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA         my_media;
UINT             status;
CHAR             entry[FX_MAX_LONG_NAME_LEN];
/* Retrieve the first directory entry in the current directory. */
status = fx_directory_first_entry_find(&my_media, entry);
/* If status equals FX_SUCCESS, the entry in the directory is the "entry" string. */
```

### <a name="see-also"></a>Consulte também

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_first_full_entry_find"></a>fx_directory_first_full_entry_find

Obtém a primeira entrada no diretório com informação completa

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.
- **directory_name**: Ponte para o destino para o nome de uma entrada de diretório. Deve ser pelo menos tão grande quanto FX_MAX_LONG_NAME_LEN.
- **atributos**: Se não for nulo, ponteiro para o destino para os atributos da entrada a colocar. Os atributos são devolvidos num formato de mapa bit com as seguintes definições possíveis:
  - **FX_READ_ONLY** (0x01)
  - **FX_HIDDEN** (0x02)
  - **FX_SYSTEM** (0x04)
  - **FX_VOLUME** (0x08)
  - **FX_DIRECTORY** (0x10)
  - **FX_ARCHIVE** (0x20)
- **tamanho**: Se não foruso, ponteiro para o destino para o tamanho da entrada em bytes.
- **ano**: Se não for nulo, pontia o destino para o ano de modificação da entrada.
- **mês**: Se não for nulo, ponteiu o destino para o mês de modificação da entrada.
- **dia**: Se não for nulo, ponteiu o destino para o dia de modificação da entrada.
- **hora**: Se não for nulo, ponteiu o destino para a hora de modificação da entrada.
- **minuto**: Se não for nulo, ponteiu o destino para o minuto de modificação da entrada.
- **segundo**: Se não for nulo, ponteiu o destino para a segunda modificação da entrada.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Primeira entrada de diretório bem sucedida
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas neste diretório
- **erro de** FX_IO_ERROR (0x90) do condutor I/O
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito
- **FX_FILE _CORRUPT** (0x08) File é corrompido
- **FX_SECTOR_INVALID** (0x89) Sector inválido
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada da FAT
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação
- **FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos
- **FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiro de destino.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA     my_media;
UINT         status;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
UINT         attributes;
ULONG        size;
UINT         year;
UINT         month;
UINT         day;
UINT         hour;
UINT         minute;
UINT         second;
/* Get the first directory entry in the default directory with full information. */
status = fx_directory_first_full_entry_find(&my_media, entry_name,
    &attributes, &size, &year, &month, &day, &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a>Consulte também

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_information_get"></a>fx_directory_information_get:

Obtém informações de entrada de diretórios

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.
- **directory_name**: Ponteiro para o nome da entrada do diretório.
- **atributos**: Ponteiro para o destino para os atributos.
- **tamanho**: Ponteiro para o destino para o tamanho.
- **ano**: Ponteiro para o destino do ano.
- **mês**: Ponteiro para o destino do mês.
- **dia**: Ponteiro para o destino do dia.
- **hora**: Ponteiro para o destino durante a hora.
- **minuto**: Ponteiro para o destino por um minuto.
- **segundo**: Ponter para o destino para o segundo.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Primeira entrada de diretório bem sucedida
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos
- **FX_NOT_FOUND** (0x04) Diretório especificado não foi encontrado nos meios de comunicação
- **erro de** FX_IO_ERROR (0x90) do condutor I/O
- **FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos
- **FX_FILE _CORRUPT** (0x08) File é corrompido
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada da FAT
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação
- **FX_SECTOR_INVALID** (0x89) Sector inválido
- **FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiro de destino.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA     my_media;
UINT         status; attributes; year; month; day;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
ULONG        size;
UINT         hour; minute; second;
/* Retrieve information about the directory entry "myfile.txt".*/
status = fx_directory_information_get(&my_media, "myfile.txt", &attributes, &size,
                                      &year, &month, &day,
                                      &hour, &minute, &second);
/* If status equals FX_SUCCESS, the directory entry information is available in the local variables. */
```

### <a name="see-also"></a>Consulte também

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_clear"></a>fx_directory_local_path_clear:

Limpa o caminho local padrão

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_local_path_clear(FX_MEDIA *media_ptr);
```

### <a name="description"></a>Description

Este serviço limpa o caminho local anterior configurado para o fio de chamada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para um meio de comunicação previamente aberto.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Caminho local bem sucedido.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos atualmente
- **FX_NO_LCOAL_PATH FX_NOT_IMPLEMENTED** (0x22) é definido
- **FX_PTR_ERROR** (0x18) Ponteiro de meios inválidos

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA             my_media;
UINT                 status;
/* Clear the previously setup local path for this media. */
status = fx_directory_local_path_clear(&my_media);
/* If status equals FX_SUCCESS the local path is cleared. */
```

### <a name="see-also"></a>Consulte também

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_get"></a>fx_directory_local_path_get:

Obtém a cadeia de caminho local atual

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_local_path_clear(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a>Description

Este serviço devolve o ponteiro de percurso local dos meios de comunicação especificados. Se não houver um caminho local definido, um NU É devolvido ao chamador.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.
- **return_path_name**: Ponter para o ponteiro de corda de destino para que a cadeia de caminho local seja armazenada.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Caminho local bem sucedido.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos atualmente
- **NX_NO_LCOAL_PATH FX_NOT_IMPLEMENTED** (0x22)
- **FX_PTR_ERROR** (0x18) Ponteiro de meios inválidos


### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA         my_media;
CHAR             *my_path;
UINT             status;
/* Retrieve the current local path string. */
status = fx_directory_local_path_get(&my_media, &my_path);
/* If status equals FX_SUCCESS, "my_path" points to the local path string. */
```

### <a name="see-also"></a>Consulte também

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_restore"></a>fx_directory_local_path_restore:

Restaura o caminho local anterior

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_local_path_restore(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr);
```

### <a name="description"></a>Description

Este serviço restaura um caminho local previamente definido. A posição de pesquisa de diretórios feita neste caminho local também é restaurada, o que torna esta rotina útil em diretórios recursivos pela aplicação.

> [!IMPORTANT]
> *Cada caminho local contém uma cadeia de caminhos local de **FX_MAXIMUM_PATH** em tamanho, que por padrão é de 256 caracteres. Esta cadeia de caminhos interno não é utilizada pelo FileX e é fornecida apenas para a utilização da aplicação. Se **FX_LOCAL_PATH** vai ser declarado como uma variável local, os utilizadores devem ter cuidado com a pilha que cresce pelo tamanho desta estrutura. Os utilizadores são bem-vindos a reduzir o tamanho de **FX_MAXIMUM_PATH** e a reconstruir a fonte da biblioteca FileX.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.
- **local_path_ptr**: Ponte rumo ao caminho local previamente definido. É muito importante garantir que este ponteiro realmente aponta para um caminho local usado e ainda intacto.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Restaurar o caminho local bem sucedido.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão atualmente abertos.
- **FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH é definido.
- **FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiro de percurso local.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA                  my_media;
FX_LOCAL_PATH             my_previous_local_path;
UINT                      status;
/* Restore the previous local path. */
status = fx_directory_local_path_restore(&my_media, &my_previous_local_path);
/* If status equals FX_SUCCESS, the previous local path has been restored. */
```

### <a name="see-also"></a>Consulte também

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_set"></a>fx_directory_local_path_set

Cria um caminho local específico de linha

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_local_path_set(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a>Description

Este serviço estabelece um caminho específico de fio, conforme especificado pela ***new_path_string** _. Após a conclusão com sucesso desta rotina, as informações locais armazenadas em _ *_local_path_ptr_** terão precedência sobre o caminho global dos meios de comunicação para todas as operações de arquivo e diretório feitas por este fio. Isto não terá qualquer impacto em qualquer outro fio no sistema 
> [!IMPORTANT]
> *O tamanho padrão da cadeia de caminho local é de 256 caracteres; pode ser alterado modificando **FX_MAXIMUM_PATH** em **fx_api.h** e reconstruindo toda a biblioteca Do FicheiroX. O caminho da corda do personagem é mantido para a aplicação e não é usado internamente pelo FileX.*

> [!IMPORTANT]
> *Para os nomes fornecidos pela aplicação, o FileX suporta caracteres backslash \\ (/ ) e barras para a frente (/) para diretórios separados, subdiretórios e nomes de ficheiros. No entanto, o FileX utiliza apenas o carácter backslash nos caminhos devolvidos à aplicação.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponte para o meio de comunicação anteriormente aberto.
- **local_path_ptr**: Destino para a detenção das informações do percurso local específicas do fio. O endereço desta estrutura pode ser fornecido para a função de restauro do caminho local no futuro.
- **new_path_name**: Especifica o caminho local para a configuração.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Conjunto de diretório padrão bem sucedido.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_NOT_IMPLEMENTED** (0x22) **FX_NO_LCOAL_PATH
- **FX_INVALID_PATH** (0x0D) Não foi possível encontrar novos diretórios.
- **FX_NOT_IMPLEMENTED** (0x22)- **FX_NO_LOCAL_PATH é definido.
- **FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiro de percurso local.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA         my_media;
UINT             status;
FX_LOCAL_PATH     my_previous_local_path;
/* Set the local path to \abc\def\ghi. */
status = fx_directory_local_path_set (&my_media,&local_path,"\\abc\\def\\ghi");

/* If status equals FX_SUCCESS, the default directory for this thread
is \abc\def\ghi. All subsequent file operations that do not explicitly
specify a path will default to this directory. Note that the character
"\" serves as an escape character in a string. To represent the
character "\", use the construct "\\".*/
```

### <a name="see-also"></a>Consulte também

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_long_name_get"></a>fx_directory_long_name_get:

Obtém um nome longo de nome curto

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_long_name_get(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name);
```

### <a name="description"></a>Description

Este serviço recupera o nome longo (se houver) associado ao nome fornecido curto (formato 8.3). O nome curto pode ser um nome de ficheiro ou um nome de diretório.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.
- **short_name**: Ponteiro para o nome curto de origem (formato 8.3).
- **long_name**: Ponte para destino para o nome longo. Se não houver um nome comprido, o nome curto é devolvido. Note que o destino para o nome longo deve ser grande o suficiente para manter FX_MAX_LONG_NAME_LEN caracteres.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Nome longo bem sucedido obter
- **FX_NOT_FOUND** (0x04) Nome curto não foi encontrado
- **erro de** FX_IO_ERROR (0x90) do condutor I/O
- **FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos
- **FX_FILE_CORRUPT** (0x08) File é corrompido
- **FX_SECTOR_INVALID** (0x89) Sector inválido
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada da FAT
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação
- **FX_PTR_ERROR** (0x18) Meios inválidos ou ponteiros de nome
- **FX_CALLER_ERROR** (0x20) Caller não é um fio

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA            my_media;
UCHAR               my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */
status = fx_directory_long_name_get(&my_media, "TEXT~01.TXT", my_long_name);
/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_long_name_get_extended"></a>fx_directory_long_name_get_extended

Obtém um nome longo de nome curto

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_long_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name,
    UINT long_file_name_buffer_length);
```

### <a name="description"></a>Description

Este serviço recupera o nome longo (se houver) associado ao nome fornecido curto (formato 8.3). O nome curto pode ser um nome de ficheiro ou um nome de diretório.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.
- **short_name**: Ponteiro para o nome curto de origem (formato 8.3).
- **long_name**: Ponte para destino para o nome longo. Se não houver um nome comprido, o nome curto é devolvido. Nota: O destino para o nome longo deve ser grande o suficiente para manter **FX_MAX_LONG_NAME_LEN** caracteres.
- **long_file_name_buffer_length**: Comprimento do tampão de nome comprido.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Nome longo bem sucedido obtém.
- **FX_NOT_FOUND** (0x04) Nome curto não foi encontrado.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação.
- **FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiros de nome.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA        my_media;
UCHAR            my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */

status = fx_directory_long_name_get_extended(&my_media,
    "TEXT~01.TXT", my_long_name), sizeof(my_long_name));

/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_name_test"></a>fx_directory_name_test

Ensaios para diretório

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_name_test(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a>Description

Este serviço testa se o nome fornecido é ou não um diretório. Em caso afirmativo, um FX_SUCCESS é devolvido.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.
- **directory_name**: Ponteiro para o nome da entrada do diretório.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) O nome fornecido é um diretório.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos
- **FX_NOT_FOUND** (0x04) não foi encontrado o diretório.
- **FX_NOT_DIRECTORY** (0x0E) A entrada não é um diretório
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação.
- **FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiros de nome.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA        my_media;
UNIT             status;
/* Check to see if the name "abc" is directory */

status = fx_directory_name_test(&my_media, "abc");

/* If status equals FX_SUCCESS "abc" is a directory. */
```

### <a name="see-also"></a>Consulte também

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create

## <a name="fx_directory_next_entry_find"></a>fx_directory_next_entry_find:

Apanha a próxima entrada de diretório

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_next_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a>Description

Este serviço devolve o próximo nome de entrada no diretório padrão atual.

> [!WARNING]
> *Se utilizar um caminho não local, também é importante evitar (com um semáforo ThreadX ou nível prioritário de thread) que outros fios de aplicação mudem este diretório enquanto está a decorrer um diretório. Caso contrário, podem ser obtidos resultados inválidos.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.
- **return_entry_name**: Ponteiro para o destino para o próximo nome de entrada no diretório predefinido. O tampão a que este ponteiro aponta deve ser suficientemente grande para manter o tamanho máximo do nome FileX, definido por **_FX_MAX_LONG_NAME_LEN_**.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Sucesso próxima entrada encontrar
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais inscrições neste diretório.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.
- **FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA        my_media;
CHAR            next_name[FX_MAX_LONG_NAME_LEN];
UINT            status;

/* Retrieve the next entry in the default directory. */

status = fx_directory_next_entry_find(&my_media, next_name);

/* If status equals TX_SUCCESS, the name of the next directory entry is in "next_name". */
```

### <a name="see-also"></a>Consulte também

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_next_full_entry_find"></a>fx_directory_next_full_entry_find:

Obtém a próxima entrada de diretório com informação completa

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_next_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes, 
    ULONG *size,
    UINT *year, 
    UINT *month, 
    UINT *day,
    UINT *hour, 
    UINT *minute, 
    UINT *second);
```

### <a name="description"></a>Description

Este serviço recupera o próximo nome de entrada no diretório predefinido e copia-o para o destino especificado. Também devolve informações completas sobre a entrada, conforme especificado pelos parâmetros de entrada adicionais.

> [!WARNING]
> *O destino especificado deve ser grande o suficiente para manter o nome FileX de tamanho máximo, tal como definido por ***FX_MAX_LONG_NAME_LEN****

> [!WARNING]
> *Se utilizar um caminho não local, é importante evitar (com um semáforo ThreadX, mutex ou mudança de nível prioritário) que outros fios de aplicação mudem este diretório enquanto está a decorrer um diretório. Caso contrário, podem ser obtidos resultados inválidos.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.
- **directory_name**: Ponte para o destino para o nome de uma entrada de diretório. Deve ter pelo menos o tamanho **FX_MAX_LONG_NAME_LEN.**
- **atributos**: Se não for nulo, ponteiro para o destino para os atributos da entrada a colocar. Os atributos são devolvidos num formato de mapa bit com as seguintes definições possíveis:
  - **FX_READ_ONLY** (0x01)
  - **FX_HIDDEN** (0x02)
  - **FX_SYSTEM** (0x04)
  - **FX_VOLUME** (0x08)
  - **FX_DIRECTORY** (0x10)
  - **FX_ARCHIVE** (0x20)
- **tamanho**: Se não foruso, ponteiro para o destino para o tamanho da entrada em bytes.
- **mês**: Se não for nulo, ponteiu o destino para o mês de modificação da entrada.
- **ano**: Se não for nulo, pontia o destino para o ano de modificação da entrada.
- **dia**: Se não for nulo, ponteiu o destino para o dia de modificação da entrada.
- **hora**: Se não for nulo, ponteiu o destino para a hora de modificação da entrada.
- **minuto**: Se não for nulo, ponteiu o destino para o minuto de modificação da entrada.
- **segundo**: Se não for nulo, ponteiu o destino para a segunda modificação da entrada.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) O diretório de sucesso da próxima entrada.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais inscrições neste diretório.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação.
- **FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos.
- **FX_PTR_ERROR** (0x18) O ponteiro de mídia inválido ou todos os parâmetros de entrada são NULOS.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA    my_media;
UINT        status;
CHAR        entry_name[FX_MAX_LONG_NAME_LEN];
UINT        attributes;
ULONG       size;
UINT        year;
UINT        month;
UINT        day;
UINT        hour;
UINT        minute;
UINT        second;

/* Get the next directory entry in the default directory with full information. */
status = fx_directory_next_full_entry_find(&my_media, entry_name, &attributes, &size,
                                           &year, &month, &day,
                                           &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a>Consulte também

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_rename"></a>fx_directory_rename

Renomeia diretório

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_directory_name,
    CHAR *new_directory_name);
```

### <a name="description"></a>Description

Este serviço altera o nome do diretório para o novo nome especificado do diretório. O renomeamento também é feito em relação ao caminho especificado ou ao caminho padrão. Se um caminho for especificado no novo nome do diretório, o diretório renomeado é efetivamente movido para o caminho especificado. Se não for especificado nenhum caminho, o diretório renomeado é colocado na trajetória predefinida atual.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.
- **old_directory_name**: Ponteiro para o nome atual do diretório.
- **new_directory_name**: Ponteiro para o novo nome do diretório.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Nomeador de diretório de sucesso.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_NOT_FOUND** (0x04) não foi encontrado o diretório.
- **FX_NOT_DIRECTORY** (0x0E) A entrada não é um diretório.
- **FX_INVALID_NAME** (0x0C) O novo nome do diretório é inválido.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação.
- **FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos.
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais inscrições neste diretório.
- **FX_INVALID_PATH** (0x0D) Caminho inválido fornecido com nome de diretório.
- **FX_ALREADY_CREATED** (0x0B) Já foi criado o diretório especificado.
- **FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA         my_media;
UINT             status;

/* Change the directory "abc" to "def". */
status = fx_directory_rename(&my_media, "abc", "def");

/* If status equals FX_SUCCESS, the directory was changed to "def". */
```

### <a name="see-also"></a>Consulte também

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_short_name_get"></a>fx_directory_short_name_get:

Obtém um nome curto de um nome comprido

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_short_name_get(
    FX_MEDIA *media_ptr,
    CHAR *long_name, 
    CHAR *short_name);
```

### <a name="description"></a>Description

Este serviço recupera o nome curto (formato 8.3) associado ao nome longo fornecido. O nome longo pode ser um nome de arquivo ou um nome de diretório.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.
- **long_name**: Ponteiro para fonte de nome longo.
- **short_name**: Ponteiro para o nome curto de destino (formato 8.3). Note que o destino para o nome curto deve ser grande o suficiente para conter 14 caracteres.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Nome curto bem sucedido obtém.
- **FX_NOT_FOUND** (0x04) Nome longo não foi encontrado.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação
- **FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos.
- **FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiros de nome.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA         my_media;
UCHAR             my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get(&my_media,
    "my_really_long_name", my_short_name);

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_short_name_get_extended"></a>fx_directory_short_name_get_extended

Obtém um nome curto de um nome comprido

### <a name="prototype"></a>Prototype

```csharp
UINT fx_directory_short_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *long_name,
    CHAR *short_name,
    UINT short_file_name_length);
```

### <a name="description"></a>Description

Este serviço recupera o nome curto (formato 8.3) associado ao nome longo fornecido. O nome longo pode ser um nome de arquivo ou um nome de diretório.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.
- **long_name**: Ponteiro para fonte de nome longo.
- **short_name**: Ponteiro para o nome curto de destino (formato 8.3). Nota: O destino do nome curto deve ser grande o suficiente para conter 14 caracteres.
- **short_file_name_length**: Comprimento do tampão de nome curto.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Nome curto bem sucedido obtém.
- **FX_NOT_FOUND** (0x04) Nome longo não foi encontrado.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação
- **FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos.
- **FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiros de nome.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA        my_media;
UCHAR            my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get_extended(&my_media,
    "my_really_long_name", my_short_name, sizeof(my_short_name));

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_fault_tolerant_enable"></a>fx_fault_tolerant_enable

Permite o serviço tolerante a falhas

### <a name="prototype"></a>Prototype

```csharp
UINT fx_fault_tolerant_enable(
    FX_MEDIA *media_ptr,
    VOID *memory_buffer,
    UINT memory_size);
```

### <a name="description"></a>Description

Este serviço permite o módulo tolerante a falhas. Ao iniciar, o módulo tolerante a falhas deteta se o sistema de ficheiros está ou não sob proteção tolerante a falhas do FileX. Caso contrário, o serviço encontra setores disponíveis no sistema de ficheiros para armazenar registos em transações do sistema de ficheiros. Se o sistema de ficheiros estiver sob proteção tolerante a falhas do FileX, aplica os registos no sistema de ficheiros para manter a sua integridade.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.
- **memory_ptr**: Ponteie para um bloco de memória utilizado pelo módulo tolerante de avaria como memória de risco.
- **memory_size:** O tamanho da memória do arranhão. Para que as falhas tolerantes funcionem corretamente, o tamanho da memória de risco deve ser de, pelo menos, 3072 bytes, e deve ser múltiplo do tamanho do sector.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) com sucesso permitiu tolerante a falhas.
- **FX_NOT_ENOUGH_MEMORY** (0x91) tamanho da memória demasiado pequeno.
- **FX_BOOT_ERROR** (0x01) Erro do sector do arranque.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais cluster gratuito disponível.
- **FX_NO_MORE_SPACE** (0x0A) Os meios de comunicação associados a este ficheiro não dispõem de clusters suficientes.
- Sector **FX_SECTOR_INVALID** (0x89) é inválido
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c

/* Declare memory space used for fault tolerant. */

ULONG fault tolerant_memory[3072 / sizeof(ULONG)];

/* Enable fault tolerant. */

fx_fault_tolerant_enable(media_ptr, fault_tolerant_memory, sizeof(fault_tolerant_memory));

```

### <a name="see-also"></a>Consulte também

- fx_system_initialize
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write

## <a name="fx_file_allocate"></a>fx_file_allocate

Aloca espaço para um ficheiro

### <a name="prototype"></a>Prototype

```csharp
UINT fx_file_allocate(
    FX_FILE *file_ptr, 
    ULONG size);
```
### <a name="description"></a>Description

Este serviço atribui e liga um ou mais aglomerados contíguos ao fim do ficheiro especificado. O FileX determina o número de clusters necessários dividindo o tamanho solicitado pelo número de bytes por cluster. O resultado é então arredondado para todo o cluster seguinte.

Para alocar espaço para além de 4GB, a aplicação utilizará o serviço *fx_file_extended_allocate*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **file_ptr**: Ponter para um ficheiro previamente aberto.
- **tamanho**: Número de bytes a atribuir para o ficheiro.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Atribuição de ficheiros bem sucedidos.
- **FX_ACCESS_ERROR** (0x06) O ficheiro especificado não está aberto para escrita.
- **FX_FAT_READ_ERROR** (0x03) Não leu a entrada de FAT.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_NOT_OPEN** ficheiro especificado (0x07) não está aberto.
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais cluster gratuito disponível.
- **FX_NO_MORE_SPACE** (0x0A) Os meios de comunicação associados a este ficheiro não dispõem de clusters suficientes.
- Sector **FX_SECTOR_INVALID** (0x89) é inválido
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.
- **FX_PTR_ERROR** (0x18) Ponteiro de ficheiros inválido.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c

FX_FILE            my_file;
UINT            status;

/* Allocate 1024 bytes to the end of my_file. */

status = fx_file_allocate(&my_file, 1024);

/* If status equals FX_SUCCESS the file now has one or more
    contiguous cluster(s) that can accommodate at least 1024 bytes of user data. */
```

### <a name="see-also"></a>Consulte também

- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open fx_file_read
- fx_file_relative_seek
- fx_file_rename fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_attributes_read"></a>fx_file_attributes_read

Lê atributos de ficheiros

### <a name="prototype"></a>Prototype

```c
    UINT fx_file_attributes_read(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT *attributes_ptr);
```
### <a name="description"></a>Description

Este serviço lê os atributos do ficheiro a partir dos meios de comunicação especificados.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.
- **file_name**: Pontear o nome do ficheiro solicitado (o caminho do diretório é opcional).
- **attributes_ptr**: Ponter para o destino para que os atributos do ficheiro sejam colocados. Os atributos do ficheiro são devolvidos num formato de mapa bit com as seguintes definições possíveis:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_VOLUME (0x08)
  - FX_DIRECTORY (0x10)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Leitura de atributos bem sucedidos.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_NOT_FOUND** ficheiro especificado (0x04) não foi encontrado nos meios de comunicação.
- **FX_NOT_A_FILE** (0x05) Ficheiro especificado é um diretório.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou atributos.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c

FX_MEDIA         my_media;
UINT             status;
UINT             attributes;

/* Retrieve the attributes of "myfile.txt" from the specified media. */

status = fx_file_attributes_read(&my_media, "myfile.txt", &attributes);

/* If status equals FX_SUCCESS, "attributes"
    contains the file attributes for "myfile.txt". */

```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_attributes_set"></a>fx_file_attributes_set

Define atributos de ficheiros

### <a name="prototype"></a>Prototype

```c
UINT fx_file_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT attributes);
```
### <a name="description"></a>Description

Este serviço define os atributos do ficheiro aos especificados pelo autor da chamada.

> [!WARNING]
> *A aplicação só é permitida para modificar um subconjunto dos atributos do ficheiro com este serviço. Qualquer tentativa de definir atributos adicionais resultará num erro.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.
- **file_name**: Ponteiro para o nome do ficheiro solicitado** (o caminho do diretório é opcional).
- **atributos**: Os novos atributos para o ficheiro. Os atributos de ficheiro válidos são definidos da seguinte forma:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Conjunto de atributos bem sucedidos.
- **FX_ACCESS_ERROR** ficheiro (0x06) está aberto e não pode ter os seus atributos definidos.
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas na tabela FAT ou no mapa do cluster exFAT.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação.
- **FX_NOT_FOUND** ficheiro especificado (0x04) não foi encontrado nos meios de comunicação.
- **FX_NOT_A_FILE** (0x05) Ficheiro especificado é um diretório.
- Sector **FX_SECTOR_INVALID** (0x89) é inválido
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.
- **FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos.
- **FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido.
- **FX_INVALID_ATTR** (0x19) Atributos inválidos selecionados.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c

FX_MEDIA         my_media;
UINT             status;

/* Set the attributes of "myfile.txt" to read-only. */

status = fx_file_attributes_set(&my_media, "myfile.txt", FX_READ_ONLY);

/* If status equals FX_SUCCESS, the file is now read-only. */

```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_best_effort_allocate"></a>fx_file_best_effort_allocate

Melhor esforço para alocar espaço para um arquivo

### <a name="prototype"></a>Prototype

```c
UINT fx_file_best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG size,
    ULONG *actual_size_allocated);
```
### <a name="description"></a>Description

Este serviço atribui e liga um ou mais aglomerados contíguos ao fim do ficheiro especificado. O FileX determina o número de clusters necessários dividindo o tamanho solicitado pelo número de bytes por cluster. O resultado é então arredondado para todo o cluster seguinte. Se não houver aglomerados consecutivos suficientes disponíveis nos meios de comunicação, este serviço liga o maior bloco disponível de clusters consecutivos ao ficheiro. A quantidade de espaço efetivamente alocada ao ficheiro é devolvida ao autor da chamada.

Para alocar espaço para além de 4GB, a aplicação utilizará o serviço *fx_file_extended_best_effort_allocate*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **file_ptr**: Ponter para um ficheiro previamente aberto.
- **tamanho**: Número de bytes a atribuir para o ficheiro.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Alocação de ficheiros de melhor esforço bem sucedida.
- **FX_ACCESS_ERROR** (0x06) O ficheiro especificado não está aberto para escrita.
- **FX_NOT_OPEN** ficheiro especificado (0x07) não está aberto.
- **FX_NO_MORE_SPACE** (0x0A) Os meios de comunicação associados a este ficheiro não dispõem de clusters suficientes.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.
- **FX_PTR_ERROR** (0x18) Ponteiro ou destino de ficheiros inválidos.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c

FX_FILE         my_file;
UINT             status;
ULONG             actual_allocation;

/* Attempt to allocate 1024 bytes to the end of my_file. */

status = fx_file_best_effort_allocate(&my_file, 1024, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */

```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_close"></a>fx_file_close

Arquivo de fechos

### <a name="prototype"></a>Prototype

```c
UINT fx_file_close(FX_FILE *file_ptr);
```
### <a name="description"></a>Description

Este serviço fecha o ficheiro especificado. Se o ficheiro estiver aberto para escrita e se foi modificado, este serviço completa o processo de modificação do ficheiro atualizando a sua entrada no diretório com o novo tamanho e a hora e data do sistema atuais.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **file_ptr**: Ponter para um ficheiro previamente aberto.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Arquivo bem sucedido perto.
- **FX_NOT_OPEN** (0x07) Ficheiro especificado não está aberto.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou atributos.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c

FX_FILE        my_file;
UINT        status;

/* Close the previously opened file "my_file". */
status = fx_file_close(&my_file);

/* If status equals FX_SUCCESS, the file was closed successfully. */
```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_create"></a>fx_file_create

Cria ficheiro

### <a name="prototype"></a>Prototype

```c
UINT fx_file_create(
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```
### <a name="description"></a>Description

Este serviço cria o ficheiro especificado no diretório predefinido ou no caminho do diretório fornecido com o nome do ficheiro.

> [!WARNING]
> *Este serviço cria um ficheiro de comprimento zero, ou seja, sem aglomerados atribuídos. A atribuição será feita automaticamente em posteriores escritas de ficheiros ou pode ser feita com antecedência com o serviço fx_file_allocate ou fx_file_extended_allocate para o espaço além de 4GB).*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.
- **file_name**: Pontear o nome do ficheiro para criar (o caminho do diretório é opcional).

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Criação de ficheiros bem sucedidos.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_ALREADY_CREATED** (0x0B) Já foi criado o ficheiro especificado.
- **FX_NO_MORE_SPACE** (0x0A) Ou não há mais entradas no diretório de raiz ou não há mais clusters disponíveis.
- **FX_INVALID_PATH** (0x0D) Caminho inválido fornecido com nome de ficheiro.
- **FX_INVALID_NAME** (0x0C) O nome do ficheiro é inválido.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação
- **FX_MEDIA_INVALID** (0x02)Meios inválidos.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação subjacentes estão protegidos.
- **FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiro de nome de ficheiro.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c

FX_MEDIA         my_media;
UINT             status;

/* Create a file called "myfile.txt" in the
    root or the default directory of the media. */

status = fx_file_create(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, a zero sized file named "myfile.txt". */
```

### <a name="see-also"></a>Consulte também
- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_date_time_set"></a>fx_file_date_time_set

### <a name="sets-file-date-and-time"></a>Define data e hora do arquivo

Definição data e hora do arquivo

### <a name="prototype"></a>Prototype

```c
UINT fx_file_date_time_set(
    FX_MEDIA *media_ptr, 
    CHAR *file_name,
    UINT year, 
    UINT month, 
    UINT day,
    UINT hour, 
    UINT minute, 
    UINT second);
```
### <a name="description"></a>Description

Este serviço define a data e a hora do ficheiro especificado.

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.
- **file_name**: Ponteiro para o nome do ficheiro.
- **ano**: Valor do ano (1980-2107 inclusive).
- **mês**: Valor do mês (1-12 inclusive).
- **dia**: Valor do dia (1-31 inclusive).
- **hora**: Valor da hora (0-23 inclusive).
- **minuto**: Valor do minuto (0-59 inclusive).
- **segundo**: Valor do segundo (0-59 inclusive).

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Data/hora de sucesso.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_NOT_FOUND** ficheiro (0x04) não foi encontrado.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.
- **FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiros de nome.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.
- **FX_INVALID_YEAR** (0x12) Ano é inválido.
- **FX_INVALID_MONTH** (0x13) Mês é inválido.
- **FX_INVALID_DAY** (0x14) Dia é inválido.
- **FX_INVALID_HOUR** (0x15) Hora é inválida.
- **FX_INVALID_MINUTE** (0x16) O minuto é inválido.
- **FX_INVALID_SECOND** (0x17) O segundo é inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_delete"></a>fx_file_delete

### <a name="deletes-file"></a>Elimina ficheiro

Eliminação de Ficheiros

### <a name="prototype"></a>Prototype

```c
UINT fx_file_delete(
    FX_MEDIA *media_ptr, 
    CHAR *file_name);
```
### <a name="description"></a>Description

Este serviço elimina o ficheiro especificado.


### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.
- **file_name**: Pontear o nome do ficheiro para apagar (o caminho do diretório é opcional).

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Ficheiros bem sucedidos apagam..
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_NOT_FOUND** (0x04) Ficheiro especificado não foi encontrado.
- **FX_NOT_A_FILE** (0x05) Nome de ficheiro especificado era um diretório ou volume.
- **FX_ACCESS_ERROR** ficheiro especificado (0x06) está atualmente aberto.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.
- **FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos.
- **FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c

FX_MEDIA            my_media;
UINT                 status;
/* Delete the file "myfile.txt". */

status = fx_file_delete(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, "myfile.txt" has been deleted. */
```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_allocate"></a>fx_file_extended_allocate

Aloca espaço para um ficheiro

### <a name="prototype"></a>Prototype

```c
UINT fx_file_extended_allocate(
    FX_FILE *file_ptr, 
    ULONG64 size);
```
### <a name="description"></a>Description

Este serviço atribui e liga um ou mais aglomerados contíguos ao fim do ficheiro especificado. O FileX determina o número de clusters necessários dividindo o tamanho solicitado pelo número de bytes por cluster. O resultado é então arredondado para todo o cluster seguinte.

Este serviço foi concebido para exFAT. O parâmetro *de tamanho* tem um valor inteiro de 64 bits, o que permite ao chamador pré-alocar o espaço para além da gama de 4GB.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **file_ptr**: Ponter para um ficheiro previamente aberto.
- **tamanho**: Número de bytes a atribuir para o ficheiro.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Atribuição de ficheiros bem sucedidos.
- **FX_ACCESS_ERROR** (0x06) O ficheiro especificado não está aberto para escrita.
- **FX_NOT_OPEN** ficheiro especificado (0x07) não está aberto.
- **FX_NO_MORE_SPACE** (0x0A) Os meios de comunicação associados a este ficheiro não dispõem de clusters suficientes.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.
- **FX_PTR_ERROR** (0x18) Ponteiro de ficheiros inválido.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c

FX_FILE            my_file;
UINT            status;
/* Allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_allocate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS the file now has
    one or more contiguous cluster(s) that can accommodate at least
    1024 bytes of user data. */
```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_best_effort_allocate"></a>fx_file_extended_best_effort_allocate

Melhor esforço para alocar espaço para um arquivo

### <a name="prototype"></a>Prototype

```c
UINT fx_file_extended best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG64 size,
    ULONG64 *actual_size_allocated);
```
### <a name="description"></a>Description

Este serviço atribui e liga um ou mais aglomerados contíguos ao fim do ficheiro especificado. O FileX determina o número de clusters necessários dividindo o tamanho solicitado pelo número de bytes por cluster. O resultado é então arredondado para todo o cluster seguinte. Se não houver aglomerados consecutivos suficientes disponíveis nos meios de comunicação, este serviço liga o maior bloco disponível de clusters consecutivos ao ficheiro. A quantidade de espaço efetivamente alocada ao ficheiro é devolvida ao autor da chamada.

Este serviço foi concebido para exFAT. O parâmetro *de tamanho* tem um valor inteiro de 64 bits, o que permite ao chamador pré-alocar o espaço para além da gama de 4GB.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **file_ptr**: Ponter para um ficheiro previamente aberto.
- **tamanho**: Número de bytes a atribuir para o ficheiro.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Atribuição de ficheiros bem sucedidos.
- **FX_ACCESS_ERROR** (0x06) O ficheiro especificado não está aberto para escrita.
- **FX_NOT_OPEN** ficheiro especificado (0x07) não está aberto.
- **FX_NO_MORE_SPACE** (0x0A) Os meios de comunicação associados a este ficheiro não dispõem de clusters suficientes.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.
- **FX_PTR_ERROR** (0x18) Ponteiro de ficheiros inválido.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c

FX_FILE my_file;
UINT             status;
ULONG64         actual_allocation;

/* Attempt to allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_best_effort_allocate(&my_file,
    0x100000000, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */
```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_relative_seek"></a>fx_file_extended_relative_seek

Posições para um byte relativo offset

### <a name="prototype"></a>Prototype

```c
UINT fx_file_extended_relative_seek(
    FX_FILE *file_ptr,
    ULONG64 byte_offset,
    UINT seek_from);
```
### <a name="description"></a>Description

Este serviço posiciona o ponteiro interno de leitura/escrita para o byte relativo especificado. Qualquer pedido de leitura ou escrita subsequente começará neste local no ficheiro.

Este serviço foi concebido para exFAT. O parâmetro *byte_offset* tem um valor inteiro de 64bit, o que permite ao ouvinte reposicionar o ponteiro de leitura/escrita para além da gama de 4GB.

> [!IMPORTANT]
> *Se a operação de procura tentar passar o fim do ficheiro, o ponteiro de leitura/escrita do ficheiro é posicionado até ao fim do ficheiro. Inversamente, se a operação de procura tentar posicionar-se após o início do ficheiro, o ponteiro de leitura/escrita do ficheiro é posicionado para o início do ficheiro.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **file_ptr**: Ponter para um ficheiro previamente aberto.
- **byte_offset**: Byte relativo desejado compensado em ficheiro.
- **seek_from**: A direção e o local de onde realizar o parente procuram. As opções de procura válidas são definidas da seguinte forma:
  - FX_SEEK_BEGIN (0x00)
  - FX_SEEK_END (0x01)
  - FX_SEEK_FORWARD (0x02)
  - FX_SEEK_BACK (0x03) Se FX_SEEK_BEGIN for especificada, a operação seek é realizada desde o início do processo. Se FX_SEEK_END for especificado, a operação seek é efetuada para trás a partir da extremidade do ficheiro. Se FX_SEEK_FORWARD for especificado, a operação seek é executada para a frente a partir da posição atual do ficheiro. Se FX_SEEK_BACK for especificado, a operação seek é efetuada para trás a partir da posição atual do ficheiro.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Procura de arquivos bem sucedidos.
- **FX_NOT_OPEN** ficheiro especificado (0x07) não está aberto.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_PTR_ERROR** (0x18) Ponteiro de ficheiros inválido.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to seek forward 0x100000000 bytes in "my_file". */

status = fx_file_extended_relative_seek(&my_file, 0x100000000, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write
    pointers are positioned 0x100000000 bytes forward. */
```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_seek"></a>fx_file_extended_seek

Posições para byte offset

### <a name="prototype"></a>Prototype

```c
UINT fx_file_extended_seek(
    FX_FILE *file_ptr, 
    ULONG64 byte_offset);
```
### <a name="description"></a>Description

Este serviço posiciona o ponteiro interno de leitura/escrita para o byte especificado. Qualquer pedido de leitura ou escrita subsequente começará neste local no ficheiro.

Este serviço foi concebido para exFAT. O parâmetro *byte_offset* tem um valor inteiro de 64bit, o que permite ao ouvinte reposicionar o ponteiro de leitura/escrita para além da gama de 4GB.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **file_ptr**: Ponter para o bloco de controlo de ficheiros.
- **byte_offset**: Byte byte offset em ficheiro. Um valor de zero posicionará o ponteiro de leitura/escrita no início do ficheiro, enquanto um valor superior ao tamanho do ficheiro posicionará o ponteiro de leitura/escrita no final do ficheiro.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Procura de ficheiros bem sucedidos.
- **FX_NOT_OPEN** (0x07) Ficheiro especificado não está aberto.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_PTR_ERROR** (0x18) Ponteiro de ficheiros inválido.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_FILE         my_file;
UINT             status;
/* Seek to position 0x100000000 of "my_file." */

status = fx_file_extended_seek(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned 0x100000000 bytes from the beginning of the file. */
```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_truncate"></a>fx_file_extended_truncate

Arquivo truncates

### <a name="prototype"></a>Prototype

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG64 size);
```
### <a name="description"></a>Description

Este serviço trunca o tamanho do ficheiro para o tamanho especificado. Se o tamanho fornecido for maior do que o tamanho real do ficheiro, este serviço não faz nada. Nenhum dos clusters de meios associados ao ficheiro é libertado.

> [!WARNING]
> *Tenha cuidado com os ficheiros truncados que também podem estar abertos simultaneamente para leitura. Truncar um ficheiro também aberto para leitura pode resultar na leitura de dados inválidos.*

Este serviço foi concebido para exFAT. O parâmetro *de tamanho* tem um valor inteiro de 64 bits, o que permite que o chamador opere além da faixa de 4GB.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **file_ptr**: Ponter para o bloco de controlo de ficheiros.
- **tamanho**: Novo tamanho do ficheiro. Bytes passado este novo tamanho de arquivo são descartados.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Truncado de ficheiros bem sucedidos.
- **FX_NOT_OPEN** (0x07) Ficheiro especificado não está aberto.
- **FX_ACCESS_ERROR** (0x06) O ficheiro especificado não está aberto para escrita.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação subjacentes estão protegidos.
- **FX_PTR_ERROR** (0x18) Ponteiro de ficheiros inválido.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_FILE            my_file;
UINT            status;
/* Truncate "my_file" to 0x100000000 bytes. */

status = fx_file_extended_truncate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, "my_file" contains 0x100000000 or fewer bytes. */
```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_truncate_release"></a>fx_file_extended_truncate_release

Truncates arquivo e liberta cluster(s)

### <a name="prototype"></a>Prototype

```c
UINT fx_file_extended_truncate_release(
    FX_FILE *file_ptr, 
    ULONG64 size);
```

### <a name="description"></a>Description

Este serviço trunca o tamanho do ficheiro para o tamanho especificado. Se o tamanho fornecido for maior do que o tamanho real do ficheiro, este serviço não faz nada. Ao contrário do ***serviço fx_file_extended_truncate,*** este serviço liberta quaisquer clusters não-reutilizados.

> [!WARNING]
> *Tenha cuidado com os ficheiros truncados que também podem estar abertos simultaneamente para leitura. Truncar um ficheiro também aberto para leitura pode resultar na leitura de dados inválidos.*

Este serviço foi concebido para exFAT. O parâmetro *de tamanho* tem um valor inteiro de 64 bits, o que permite que o chamador opere além da faixa de 4GB.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **file_ptr**: Ponter para um ficheiro previamente aberto.
- **tamanho**: Novo tamanho do ficheiro. Bytes passado este novo tamanho de arquivo são descartados.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Truncado de ficheiros bem sucedidos.
- **FX_ACCESS_ERROR** (0x06) O ficheiro especificado não está aberto para escrita.
- **FX_NOT_OPEN** ficheiro especificado (0x07) não está aberto.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.
- **FX_PTR_ERROR** (0x18) Ponteiro de ficheiros inválido.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_FILE            my_file;
UINT            status;
/* Attempt to truncate everything after the first 0x100000000 bytes of "my_file". */

status = fx_file_extended_truncate_release(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file is now 0x100000000
    bytes or fewer and all unused clusters have been released. */
```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_open"></a>fx_file_open

Abre o ficheiro

### <a name="prototype"></a>Prototype

```c
UINT fx_file_open(
    FX_MEDIA *media_ptr,
    FX_FILE *file_ptr,
    CHAR *file_name,
    UINT open_type);
```
### <a name="description"></a>Description

Este serviço abre o ficheiro especificado para leitura ou escrita. Um ficheiro pode ser aberto para leitura várias vezes, enquanto um ficheiro só pode ser aberto para escrita uma vez até que o escritor feche o ficheiro.

> [!IMPORTANT]
> *Deve ter-se cuidado se um ficheiro estiver simultaneamente aberto para leitura e escrita. A escrita de ficheiros executada quando um ficheiro é aberto simultaneamente para leitura pode não ser visto pelo leitor, a menos que o leitor feche e reabra o ficheiro para leitura. Da mesma forma, o autor do ficheiro deve ter cuidado ao utilizar os serviços de truncato de ficheiros. Se um ficheiro for truncado pelo escritor, os leitores do mesmo ficheiro podem devolver dados inválidos.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.
- **file_ptr**: Ponter para o bloco de controlo de ficheiros.
- **file_name**: Pontear o nome do ficheiro a abrir (o caminho do diretório é opcional).
- **open_type:** Tipo de ficheiro aberto. As opções de tipo aberto válido são:
  - FX_OPEN_FOR_READ (0x00)
  - FX_OPEN_FOR_WRITE (0x01)
  - FX_OPEN_FOR_READ_FAST (0x02)

Abrir ficheiros com FX_OPEN_FOR_READ e FX_OPEN_FOR_READ_FAST é semelhante:

- FX_OPEN_FOR_READ inclui a verificação de que a lista ligada de clusters que compõem o ficheiro está intacta, e FX_OPEN_FOR_READ_FAST não efetua esta verificação, o que o torna mais rápido.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Arquivo bem sucedido aberto.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_NOT_FOUND** (0x04) Ficheiro especificado não foi encontrado.
- **FX_NOT_A_FILE** (0x05) Nome de ficheiro especificado era um diretório ou volume.
- **FX_FILE_CORRUPT** (0x08) Ficheiro especificado é corrupto e o ficheiro aberto falhou.
- **FX_ACCESS_ERROR** (0x06) O ficheiro especificado já está aberto ou o tipo aberto é inválido.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos.
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação subjacentes estão protegidos.
- **FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiro de ficheiros.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA     my_media;
FX_FILE     my_file;
UINT         status;

/* Open the file "myfile.txt" for reading. */

status = fx_file_open(&my_media, &my_file, "myfile.txt", FX_OPEN_FOR_READ);

/* If status equals FX_SUCCESS, file "myfile.txt" is now
    open and may be accessed now with the my_file pointer. */
```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_read"></a>fx_file_read

Lê bytes a partir de arquivo

### <a name="prototype"></a>Prototype

```c
UINT fx_file_read(
    FX_FILE *file_ptr, 
    VOID *buffer_ptr,
    ULONG request_size, 
    ULONG *actual_size);
```
### <a name="description"></a>Description

Este serviço lê bytes do ficheiro e armazena-os no tampão fornecido. Depois de concluída a leitura, o ponteiro de leitura interno do ficheiro é ajustado para apontar para o byte seguinte no ficheiro. Se houver menos bytes restantes no pedido, apenas os bytes restantes são armazenados no tampão. Em todo o caso, o número total de bytes colocados no tampão é devolvido ao chamador.

> [!WARNING]
> *O pedido deve assegurar que o tampão fornecido seja capaz de armazenar o número especificado de bytes solicitados.*

> [!WARNING]
> *O desempenho mais rápido é alcançado se o tampão de destino estiver num limite de palavras longas e o tamanho solicitado for uniformemente divisível por tamanhos de **(ULONG).***

### <a name="input-parameters"></a>Parâmetros de Entrada

- **file_ptr**: Ponter para o bloco de controlo de ficheiros.
- **buffer_ptr**: Ponter para o tampão de destino para a leitura.
- **request_size**: Número máximo de bytes para ler.
- **atual_size**: Pontear para a variável para manter o número real de bytes lidos no tampão fornecido.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Leitura de ficheiro bem sucedida.
- **FX_NOT_OPEN** (0x07) Ficheiro especificado não está aberto.
- **FX_FILE_CORRUPT** ficheiro especificado (0x08) é corrupto e a leitura falhou.
- **FX_END_OF_FILE** (0x09) O fim do ficheiro foi alcançado.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_PTR_ERROR** (0x18) Ficheiro inválido ou ponteiro tampão.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_FILE                 my_file;
unsigned char           my_buffer[1024];
ULONG                   actual_bytes;
UINT                    status;

/* Read up to 1024 bytes into "my_buffer." */
status = fx_file_read(&my_file, my_buffer, 1024, &actual_bytes);

/* If status equals FX_SUCCESS, "my_buffer" contains the bytes
    read from the file. The total number of bytes read is in "actual_bytes." */
```
### <a name="see-also"></a>Consulte também

- fx_file_allocate,
- fx_file_attributes_read,
- fx_file_attributes_set,
- fx_file_best_effort_allocate,
- fx_file_close,
- fx_file_create,
- fx_file_date_time_set,
- fx_file_delete,
- fx_file_extended_allocate,
- fx_file_extended_best_effort_allocate,
- fx_file_extended_relative_seek,
- fx_file_extended_seek,
- fx_file_extended_truncate,
- fx_file_extended_truncate_release,
- fx_file_open,
- fx_file_relative_seek,
- fx_file_rename,
- fx_file_seek,
- fx_file_truncate,
- fx_file_truncate_release,
- fx_file_write,
- fx_file_write_notify_set,
- fx_unicode_file_create,
- fx_unicode_file_rename,
- fx_unicode_name_get,
- fx_unicode_short_name_get

## <a name="fx_file_relative_seek"></a>fx_file_relative_seek

Posições para um byte relativo offset

### <a name="prototype"></a>Prototype

```c
UINT fx_file_relative_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset,
    UINT seek_from);
```
### <a name="description"></a>Description

Este serviço posiciona o ponteiro interno de leitura/escrita para o byte relativo especificado. Qualquer pedido de leitura ou escrita subsequente começará neste local no ficheiro.

> [!IMPORTANT]
> *Se a operação de procura tentar passar o fim do ficheiro, o ponteiro de leitura/escrita do ficheiro é posicionado até ao fim do ficheiro. Inversamente, se a operação de procura tentar posicionar-se após o início do ficheiro, o ponteiro de leitura/escrita do ficheiro é posicionado para o início do ficheiro.*

Para procurar com um valor compensado para além de 4GB, a aplicação utilizará o serviço *fx_file_extended_relative_seek*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **file_ptr**: Ponter para um ficheiro previamente aberto.
- **byte_offset**: Byte relativo desejado compensado em ficheiro.
- **seek_from**: A direção e o local de onde realizar o parente procuram. As opções de procura válidas são definidas da seguinte forma:
  - FX_SEEK_BEGIN (0x00)
  - FX_SEEK_END (0x01)
  - FX_SEEK_FORWARD (0x02)
  - FX_SEEK_BACK (0x03)

Se FX_SEEK_BEGIN for especificada, a operação seek é realizada desde o início do ficheiro. Se FX_SEEK_END for especificado, a operação seek é efetuada para trás a partir da extremidade do ficheiro. Se FX_SEEK_FORWARD for especificado, a operação seek é executada para a frente a partir da posição atual do ficheiro. Se FX_SEEK_BACK for especificado, a operação seek é efetuada para trás a partir da posição atual do ficheiro.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Procura de arquivos bem sucedidos.
- **FX_NOT_OPEN** ficheiro especificado (0x07) não está aberto.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.
- **FX_PTR_ERROR** (0x18) Ponteiro de ficheiros inválido.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to move 10 bytes forward in "my_file". */

status = fx_file_relative_seek(&my_file, 10, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write pointers
    are positioned 10 bytes forward. */
```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_rename"></a>fx_file_rename

Arquivo de renomes

### <a name="prototype"></a>Prototype

```c
UINT fx_file_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_file_name,
    CHAR *new_file_name);
```
### <a name="description"></a>Description

Este serviço altera o nome do ficheiro especificado por *old_file_name*. O renomeamento também é feito em relação ao caminho especificado ou ao caminho padrão. Se um caminho for especificado no nome do novo ficheiro, o ficheiro renomeado é efetivamente movido para o caminho especificado. Se não for especificado nenhum caminho, o ficheiro renomeado é colocado na trajetória predefinida atual.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.
- **old_file_name**: Ponter o nome do ficheiro para renomear (o caminho do diretório é opcional).
- **new_file_name**: Ponter para o novo nome do ficheiro. O caminho do diretório não é permitido.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Rebatizador de ficheiros bem sucedidos.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_NOT_FOUND** (0x04) Ficheiro especificado não foi encontrado.
- **FX_NOT_A_FILE** (0x05) Ficheiro especificado é um diretório.
- **FX_ACCESS_ERROR** (0x06) O ficheiro especificado já está aberto.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.
- **FX_INVALID_NAME** (0x0C) O nome de novo ficheiro especificado não é um nome de ficheiro válido.
- **FX_INVALID_PATH** caminho (0x0D) é inválido.
- **FX_ALREADY_CREATED** (0x0B) O novo nome do ficheiro é utilizado.
- **FX_MEDIA_INVALID** (0x02) Os meios de comunicação são inválidos.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a tabela FAT.
- **FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA         my_media;
UINT             status;

/* Rename "myfile1.txt" to "myfile2.txt" in the default directory of the media. */

status = fx_file_rename(&my_media, "myfile1.txt", "myfile2.txt");

/* If status equals FX_SUCCESS, the file was successfully renamed. */
```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_seek"></a>fx_file_seek

Posições para byte offset

### <a name="prototype"></a>Prototype

```c
UINT fx_file_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset);
```
### <a name="description"></a>Description

Este serviço posiciona o ponteiro interno de leitura/escrita para o byte especificado. Qualquer pedido de leitura ou escrita subsequente começará neste local no ficheiro.

Para procurar com um valor compensado para além de 4GB, a aplicação utilizará o serviço *fx_file_extended_seek*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **file_ptr**: Ponter para o bloco de controlo de ficheiros.
- **byte_offset**: Byte byte offset em ficheiro. Um valor de zero posicionará o ponteiro de leitura/escrita no início do ficheiro, enquanto um valor superior ao tamanho do ficheiro posicionará o ponteiro de leitura/escrita no final do ficheiro.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Procura de ficheiros bem sucedidos.
- **FX_NOT_OPEN** (0x07) Ficheiro especificado não está aberto.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação
- **FX_PTR_ERROR** (0x18) Ponteiro de ficheiros inválido.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_FILE            my_file;
UINT            status;
/* Seek to the beginning of "my_file." */
status = fx_file_seek(&my_file, 0);
/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned to the beginning of the file. */
```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_truncate"></a>fx_file_truncate

Arquivo truncates

### <a name="prototype"></a>Prototype

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```

### <a name="description"></a>Description

Este serviço trunca o tamanho do ficheiro para o tamanho especificado. Se o tamanho fornecido for maior do que o tamanho real do ficheiro, este serviço não faz nada. Nenhum dos clusters de meios associados ao ficheiro é libertado.

> [!WARNING]
> *Tenha cuidado com os ficheiros truncados que também podem estar abertos simultaneamente para leitura. Truncar um ficheiro também aberto para leitura pode resultar na leitura de dados inválidos.*

Para operar além de 4GB, a aplicação deve utilizar o serviço *fx_file_extended_truncate*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **file_ptr**: Ponter para o bloco de controlo de ficheiros.
- **tamanho**: Novo tamanho do ficheiro. Bytes passado este novo tamanho de arquivo são descartados.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Truncado de ficheiros bem sucedidos.
- **FX_NOT_OPEN** (0x07) Ficheiro especificado não está aberto.
- **FX_ACCESS_ERROR** (0x06) O ficheiro especificado não está aberto para escrita.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação
- **FX_PTR_ERROR** (0x18) Ponteiro de ficheiros inválido.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_FILE                my_file;
UINT                status;
/* Truncate "my_file" to 100 bytes. */

status = fx_file_truncate(&my_file, 100);

/* If status equals FX_SUCCESS, "my_file" contains 100 or fewer bytes. */
```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_truncate_release"></a>fx_file_truncate_release

Truncates arquivo e liberta cluster(s)

### <a name="prototype"></a>Prototype

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```
### <a name="description"></a>Description

Este serviço trunca o tamanho do ficheiro para o tamanho especificado. Se o tamanho fornecido for maior do que o tamanho real do ficheiro, este serviço não faz nada. Ao contrário do ***serviço fx_file_truncate,*** este serviço liberta quaisquer clusters não-reutilizados.

> [!WARNING]
> *Tenha cuidado com os ficheiros truncados que também podem estar abertos simultaneamente para leitura. Truncar um ficheiro também aberto para leitura pode resultar na leitura de dados inválidos.*

Para operar além de 4GB, a aplicação deve utilizar o serviço *fx_file_extended_truncate_release*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **file_ptr**: Ponter para um ficheiro previamente aberto.
- **tamanho**: Novo tamanho do ficheiro. Bytes passado este novo tamanho de arquivo são descartados.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Truncado de ficheiros bem sucedidos.
- **FX_ACCESS_ERROR** (0x06) O ficheiro especificado não está aberto para escrita.
- **FX_NOT_OPEN** ficheiro especificado (0x07) não está aberto.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação subjacentes estão protegidos.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação.
- **FX_PTR_ERROR** (0x18) Ponteiro de ficheiros inválido.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_FILE         my_file;
UINT             status;

/* Attempt to truncate everything after the first 100 bytes of "my_file". */

status = fx_file_truncate_release(&my_file, 100);

/* If status equals FX_SUCCESS, the file is now 100 bytes
    or fewer and all unused clusters have been released. */
```
### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_write"></a>fx_file_write

Escreve bytes para arquivar

### <a name="prototype"></a>Prototype

```c
UINT fx_file_write(
    FX_FILE *file_ptr,
    VOID *buffer_ptr,
    ULONG size);
```
### <a name="description"></a>Description

Este serviço escreve bytes a partir do tampão especificado a partir da posição atual do ficheiro. Após a gravação estar concluída, o ponteiro de leitura interna do ficheiro é ajustado para apontar para o byte seguinte no ficheiro.

> [!WARNING]
> *O desempenho mais rápido é alcançado se o tampão de origem estiver num limite de palavras longas e o tamanho solicitado for uniformemente divisível por tamanhos de **(ULONG).***

### <a name="input-parameters"></a>Parâmetros de Entrada

- **file_ptr**: Ponter para o bloco de controlo de ficheiros.
- **buffer_ptr**: Ponter para o tampão de origem para a escrita.
- **tamanho**: Número de bytes para escrever.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Escrita de ficheiro bem sucedida.
- **FX_NOT_OPEN** (0x07) Ficheiro especificado não está aberto.
- **FX_ACCESS_ERROR** (0x06) O ficheiro especificado não está aberto para escrita.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço disponível nos meios de comunicação para realizar esta escrita.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.
- **FX_PTR_ERROR** (0x18) Ficheiro inválido ou ponteiro tampão.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_FILE            my_file;
UINT            status;
/* Write a 10 character buffer to "my_file." */

status = fx_file_write(&my_file, "1234567890", 10);

/* If status equals FX_SUCCESS, the small text string was written out to the file. */
```

### <a name="see-also"></a>Consulte também

- fx_file_allocate,
- fx_file_attributes_read,
- fx_file_attributes_set,
- fx_file_best_effort_allocate,
- fx_file_close,
- fx_file_create,
- fx_file_date_time_set,
- fx_file_delete,
- fx_file_extended_allocate,
- fx_file_extended_best_effort_allocate,
- fx_file_extended_relative_seek,
- fx_file_extended_seek,
- fx_file_extended_truncate,
- fx_file_extended_truncate_release,
- fx_file_open,
- fx_file_read,
- fx_file_relative_seek,
- fx_file_rename,
- fx_file_seek,
- fx_file_truncate,
- fx_file_truncate_release,
- fx_file_write_notify_set,
- fx_unicode_file_create,
- fx_unicode_file_rename,
- fx_unicode_name_get,
- fx_unicode_short_name_get

## <a name="fx_file_write_notify_set"></a>fx_file_write_notify_set

Define a função de notificação de escrita de ficheiro

### <a name="prototype"></a>Prototype

```c
UINT fx_file_write_notify_set(
    FX_FILE *file_ptr,
    VOID (*file_write_notify)(FX_FILE*));
```
### <a name="description"></a>Description

Este serviço instala a função de retorno que é invocada após uma operação de escrita de ficheiros bem sucedida.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **file_ptr**: Ponter para o bloco de controlo de ficheiros.
- **file_write_notify**: Função de reversão de gravação de ficheiro a instalar. Desativar a função de retorno para NUS desativa a função de retorno.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) instalou com sucesso a função de retorno.
- **file_ptr FX_PTR_ERROR** (0x18) é NU.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
fx_file_write_notify_set(file_ptr, my_file_close_callback);

```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_media_abort"></a>fx_media_abort

Aborta atividades mediáticas

### <a name="prototype"></a>Prototype

```c
UINT fx_media_abort(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Description

Este serviço aborta todas as atividades atuais associadas aos meios de comunicação, incluindo o encerramento de todos os ficheiros abertos, o envio de um pedido de abortar ao motorista associado e a colocação dos meios de comunicação em estado abortado. Este serviço é normalmente chamado quando são detetados erros de E/S.

> [!WARNING]
> *Os meios de comunicação devem ser reabertos para o utilizar novamente após a operação de aborto.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Os meios de comunicação de sucesso abortam.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA    my_media;
UINT        status;
/* Abort all activity associated with "my_media". */

status = fx_media_abort(&my_media);

/* If status equals FX_SUCCESS, all activity
    associated with the media has been aborted. */

```

### <a name="see-also"></a>Consulte também

- fx_fault_tolerant_enable
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_cache_invalidate"></a>fx_media_cache_invalidate

Invalida cache do sector lógico

### <a name="prototype"></a>Prototype

```c
UINT fx_media_cache_invalidate(FX_MEDIA *media_ptr);
```

### <a name="description"></a>Description

Este serviço elimina todos os sectores sujos da cache e, em seguida, invalida toda a cache do sector lógico.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponteiro para o bloco de controlo dos meios de comunicação

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Cache de mídia bem sucedida invalida.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_PTR_ERROR** (0x18) Media inválidos ou ponteiro de risco.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA     my_media;

/* Invalidate the cache of the media. */
status = fx_media_cache_invalidate(&my_media);

/* If status is FX_SUCCESS the cache in the media
    was successfully flushed and invalidated. */

```

### <a name="see-also"></a>Consulte também

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_check"></a>fx_media_check

Verifica os erros dos meios de comunicação social

### <a name="prototype"></a>Prototype

```c
UINT fx_media_check(
    FX_MEDIA *media_ptr,
    UCHAR *scratch_memory_ptr,
    ULONG scratch_memory_size,
    ULONG error_correction_option,
    ULONG *errors_detected_ptr);
```
### <a name="description"></a>Description

Este serviço verifica os meios de comunicação especificados para erros estruturais básicos, incluindo ligação cruzada de ficheiros/diretórios, cadeias de GORDURA inválidas e aglomerados perdidos. Este serviço também fornece a capacidade de corrigir erros detetados.

O serviço fx_media_check requer memória de risco para a sua primeira análise de resumos e ficheiros nos meios de comunicação. Especificamente, a memória de risco fornecida ao serviço de verificação de meios de comunicação deve ser suficientemente grande para conter várias entradas de diretório, uma estrutura de dados para "empilhar" a posição de entrada do diretório atual antes de entrar em subdiretas e, finalmente, o mapa lógico fat bit. A memória de risco deve ser pelo menos 512-1024 bytes mais memória para o mapa lógico fat bit, que requer tantos bits quanto há aglomerados nos meios de comunicação. Por exemplo, um dispositivo com 8000 clusters exigiria 1000 bytes para representar e, assim, exigiria uma área de risco total na ordem dos bytes de 2048.

> [!WARNING]
> *Este serviço só deve ser chamado imediatamente após fx_media_open e sem qualquer outra atividade do sistema de ficheiros.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.
- **scratch_memory_ptr**: Ponteiro para o início da memória de risco.
- **scratch_memory_size:** Tamanho da memória de risco em bytes.
- **error_correction_option**: As bits de opção de correção de erro, quando a broca está definida, é efetuada uma correção de erros. As bits de correção de erros são definidas da seguinte forma:
  - FX_FAT_CHAIN_ERROR (0x01)
  - FX_DIRECTORY_ERROR (0x02)
  - FX_LOST_CLUSTER_ERROR (0x04) Simplesmente OU em conjunto as opções de correção de erros necessárias. Se não for necessária uma correção de erros, deve ser fornecido um valor de 0.
- **errors_detected_ptr**: Destino para bits de deteção de erros, conforme definido abaixo:
  - FX_FAT_CHAIN_ERROR (0x01)
  - FX_LOST_CLUSTER_ERROR FX_DIRECTORY_ERROR (0x02) (0x04)
  - FX_FILE_SIZE_ERROR (0x08)

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Verificação bem sucedida dos meios de comunicação social, veja os erros detetados no destino para obter mais detalhes.
- **FX_ACCESS_ERROR** (0x06) Não é possível efetuar a verificação com ficheiros abertos.
- **FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais espaço nos meios de comunicação.
- **FX_NOT_ENOUGH_MEMORY** (0x91) A memória de risco fornecida não é suficientemente grande.
- **FX_ERROR_NOT_FIXED** (0x93) Corrupção de diretório de raiz FAT32 que não foi possível fixar.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_SECTOR_INVALID** sector (0x89) é inválido.
- **FX_PTR_ERROR** (0x18) Media inválidos ou ponteiro de risco.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.


### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA         my_media;
ULONG             detected_errors;
UCHAR             sratch_memory[4096];

/* Check the media and correct all errors. */

status = fx_media_check(&my_media, sratch_memory, 4096,
                        FX_FAT_CHAIN_ERROR |
                        FX_DIRECTORY_ERROR |
                        FX_LOST_CLUSTER_ERROR, &detected_errors);

/* If status is FX_SUCCESS and detected_errors is 0,
    the media was successfully checked and found to be error free. */

```

### <a name="see-also"></a>Consulte também

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_close"></a>fx_media_close

Fecha os meios de comunicação

### <a name="prototype"></a>Prototype

```c
UINT fx_media_close(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Description

Este serviço fecha os meios de comunicação especificados. No processo de fecho dos meios de comunicação, todos os ficheiros abertos estão fechados e os restantes tampão são lavados para os meios físicos.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Meios de comunicação bem sucedidos.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido.
- **FX_CALLER_ERROR**    (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA    my_media;
UINT        status;
/* Close "my_media". */

status = fx_media_close(&my_media);

/* If status equals FX_SUCCESS, "my_media" is closed. */

```

### <a name="see-also"></a>Consulte também

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_close_notify_set"></a>fx_media_close_notify_set

Define a função de notificação de mídia próxima

### <a name="prototype"></a>Prototype

```c
UINT fx_media_close_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_close_notify)(FX_MEDIA*));
```

### <a name="description"></a>Description

Este serviço define uma função de chamada de notificação que será invocada após o encerramento de um meio de comunicação com sucesso.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.
- **media_close_notify**: Os meios de comunicação estão perto notificam a função de chamada a instalar. Passar NUDIS como a função de retorno desativa a chamada de fecho dos meios de comunicação.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) instalou com sucesso a função de retorno.
- **FX_PTR_ERROR** (0x18) media_ptr é NU.
- **FX_CALLER_ERROR**    (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
fx_media_close_notify_set(media_ptr, my_media_close_callback);

```
### <a name="see-also"></a>Consulte também

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_exfat_format"></a>fx_media_exFAT_format

Meios de forma formatos

### <a name="prototype"></a>Prototype

```c
UINT fx_media_exFAT_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr, 
    UCHAR *memory_ptr,
    UINT memory_size, 
    CHAR *volume_name,
    UINT number_of_fats,
    ULONG64 hidden_sectors, 
    ULONG64 total_sectors,
    UINT bytes_per_sector, 
    UINT sectors_per_cluster,
    UINT volume_serial_number, 
    UINT boundary_unit);
```
### <a name="description"></a>Description

Este serviço forma os meios fornecidos de forma exFAT compatível com base nos parâmetros fornecidos. Este serviço deve ser chamado antes da abertura dos meios de comunicação.

> [!WARNING]
> *A formatação de um meio de comunicação já formatado apaga efetivamente todos os ficheiros e diretórios nos meios de comunicação.*

> [!IMPORTANT]
> *O tamanho do volume exFAT deve corresponder ao tamanho da partição (se houver um layout MBR ou GPT), ou o tamanho de todo o dispositivo se não houver disposição de partição (sem MBR ou GPT). Existe uma limitação no Windows de que o disco exFAT não será recoginado se forformado com alguns valores de sectores totais que são menos do que sectores avialáveis*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação. Isto é utilizado apenas para fornecer algumas informações básicas necessárias para o condutor operar.
- **condutor**: Pontear o controlador de I/S para este meio de comunicação. Este será normalmente o mesmo condutor fornecido à chamada fx_media_open subsequente.
- **driver_info_ptr**: Pontear para informações opcionais que o condutor de E/S pode utilizar.
- **memory_ptr**: Ponte para a memória de trabalho para os meios de comunicação. memory_size Especifica o tamanho da memória dos meios de comunicação. O tamanho deve ser pelo menos tão grande quanto o tamanho do sector dos meios de comunicação social.
- **volume_name**: Pontear para a cadeia de nomes de volume, que é um máximo de 11 caracteres.
- **number_of_fats**: Número de FATs nos meios de comunicação. A implementação atual suporta uma FAT nos meios de comunicação social.
- **hidden_sectors**: Número de sectores escondidos antes do sector de arranque destes meios de comunicação social. Isto é típico quando várias divisórias estão presentes.
- **total_sectors**: Número total de sectores nos meios de comunicação social.
- **bytes_per_sector**: Número de bytes por sector, que é tipicamente 512. FileX requer que este seja um múltiplo de 32.
- **sectors_per_cluster**: Número de sectores em cada cluster. O cluster é a unidade de atribuição mínima num sistema de ficheiros FAT.
- **volumne_serial_number:** Número de série a utilizar para este volume.
- **boundary_unit**: Dimensão do alinhamento da área dos dados físicos, em número de sectores.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Formato de mídia bem sucedido.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_PTR_ERROR** (0x18) Meios de comunicação, controlador ou ponteiro de memória inválidos.
- **FX_CALLER_ERROR**    (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA             sd_card;
UCHAR                 media_memory[512];

/* Format a 64GB SD card with exFAT file system. The media has
    been properly partitioned, with the partition starts from sector 32768.
    For 64GB, there are total of 120913920 sectors, each sector 512 bytes. */

status = fx_media_exFAT_format(&sd_card, _fx_sd_driver,
                                driver_information, media_memory,
                                sizeof(media_memory),
                                "exFAT_DISK" /* Volume Name */,
                                1 /* Number of FATs */,
                                32768 /* Hidden sectors */,
                                120913920 /* Total sectors */,
                                512 /* Sector size */,
                                256 /* Sectors per cluster */,
                                12345 /* Volume ID */,
                                8192 /* Boundary unit */);

/* If status is FX_SUCCESS, the media was successfully formatted. */

```

### <a name="see-also"></a>Consulte também

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_extended_space_available"></a>fx_media_extended_space_available

Devolve espaço de mídia disponível

### <a name="prototype"></a>Prototype

```c
UINT fx_media_extended_space_available(
    FX_MEDIA *media_ptr,
    ULONG64 *available_bytes_ptr);
```
### <a name="description"></a>Description

Este serviço devolve o número de bytes disponíveis nos meios de comunicação.

Este serviço foi concebido para exFAT. O ponteiro para *available_bytes* parâmetro tem um valor inteiro de 64 bits, o que permite ao ouvinte trabalhar com meios para além da gama de 4GB.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para um meio de comunicação previamente aberto.
- **available_bytes_ptr**: Bytes disponíveis deixados nos meios de comunicação.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) recuperou com sucesso o espaço disponível nos meios de comunicação.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido ou ponteiro bytes disponível é NU.
- **FX_CALLER_ERROR**    (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA        my_media;
ULONG64            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_extended_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a>Consulte também

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_flush"></a>fx_media_flush

Flushes dados para meios físicos

### <a name="prototype"></a>Prototype

```c
UINT fx_media_flush(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Description

Este serviço elimina todos os sectores em cache e entradas de diretórios de quaisquer ficheiros modificados para os meios físicos.

> [!WARNING]
> *Esta rotina pode ser chamada periodicamente pelo pedido para reduzir o risco de corrupção de ficheiros e/ou perda de dados em caso de perda súbita de poder no alvo.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Flush de mídia bem sucedida.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_FILE_CORRUPT**    ficheiro (0x08) é corrompido.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.
- **FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido.
- **FX_CALLER_ERROR**    (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA         my_media;
UINT             status;

/* Flush all cached sectors and modified file entries to the physical media. */

status = fx_media_flush(&my_media);

/* If status equals FX_SUCCESS, the physical media is completely up-to-date. */

```

### <a name="see-also"></a>Consulte também

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_format"></a>fx_media_format

Meios de forma formatos

### <a name="prototype"></a>Prototype

```c
UINT fx_media_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr,
    UCHAR *memory_ptr, 
    UINT memory_size,
    CHAR *volume_name, 
    UINT number_of_fats,
    UINT directory_entries, 
    UINT hidden_sectors,
    ULONG total_sectors, 
    UINT bytes_per_sector,
    UINT sectors_per_cluster,
    UINT heads,
    UINT sectors_per_track);
```
### <a name="description"></a>Description

Este serviço forma o meio fornecido de forma compatível COM FAT 12/16/32 com base nos parâmetros fornecidos. Este serviço deve ser chamado antes da abertura dos meios de comunicação.

> [!WARNING]
> *A formatação de um meio de comunicação já formatado apaga efetivamente todos os ficheiros e diretórios nos meios de comunicação.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação. Isto é utilizado apenas para fornecer algumas informações básicas necessárias para o condutor operar.
- **condutor**: Pontear o controlador de I/S para este meio de comunicação. Este será normalmente o mesmo condutor fornecido à chamada fx_media_open subsequente.
- **driver_info_ptr**: Pontear para informações opcionais que o condutor de E/S pode utilizar.
- **memory_ptr**: Ponte para a memória de trabalho para os meios de comunicação.
- **memory_size**: Especifica o tamanho da memória dos meios de comunicação. O tamanho deve ser pelo menos tão grande quanto o tamanho do sector dos meios de comunicação social.
- **volume_name**: Pontear para a cadeia de nomes de volume, que é um máximo de 11 caracteres.
- **number_of_fats**: Número de FATs nos meios de comunicação. O valor mínimo é 1 para a FAT primária. Valores superiores a 1 resultam na manutenção de cópias FAT adicionais no tempo de execução.
- **directory_entries**: Número de entradas de diretório no diretório de raiz.
- **hidden_sectors**: Número de sectores escondidos antes do sector de arranque destes meios de comunicação social. Isto é típico quando várias divisórias estão presentes.
- **total_sectors**: Número total de sectores nos meios de comunicação social.
- **bytes_per_sector**: Número de bytes por sector, que é tipicamente 512. FileX requer que este seja um múltiplo de 32.
- **sectors_per_cluster**: Número de sectores em cada cluster. O cluster é a unidade de atribuição mínima num sistema de ficheiros FAT.
- **cabeças**: Número de cabeças físicas.
- **sectors_per_track**: Número de sectores por via.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Formato de mídia bem sucedido.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_PTR_ERROR** (0x18) Meios de comunicação, controlador ou ponteiro de memória inválidos.
- **FX_CALLER_ERROR**    (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA         ram_disk;
UCHAR             media_memory[512];
UCHAR             ram_disk_memory[32768];

/* Format a RAM disk with 32768 bytes and 512 bytes per sector. */

status = fx_media_format(&ram_disk, _fx_ram_driver,
                         ram_disk_memory, media_memory,
                         sizeof(media_memory),
                         "MY_RAM_DISK" /* Volume Name */,
                         1 /* Number of FATs */,
                         32 /* Directory Entries */,
                         0 /* Hidden sectors */,
                         64 /* Total sectors */,
                         512 /* Sector size */,
                         1 /* Sectors per cluster */,
                         1 /* Heads */,
                         1 /* Sectors per track */);

/* If status is FX_SUCCESS, the media was successfully formatted
    and can now be opened with the following call: */

```

### <a name="see-also"></a>Consulte também

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_open"></a>fx_media_open

Abre os meios de comunicação para acesso a ficheiros

### <a name="prototype"></a>Prototype

```c
UINT fx_media_open(
    FX_MEDIA *media_ptr, 
    CHAR *media_name,
    VOID(*media_driver)(FX_MEDIA *),
    VOID *driver_info_ptr,
    VOID *memory_ptr, 
    ULONG memory_size);
```
### <a name="description"></a>Description

Este serviço abre um meio de acesso a ficheiros utilizando o controlador de E/S fornecido.

> [!WARNING]
> *A memória fornecida a este serviço é utilizada para implementar uma cache do sector lógico interno, daí que mais memória fornecida, mais física é reduzida a I/O. O FileX requer uma cache de pelo menos um sector lógico (bytes por sector dos meios de comunicação).*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.
- **media_name**: Ponteiro para o nome dos meios de comunicação.
- **media_driver**: Ponteiro para o controlador de I/O para este meio de comunicação. O controlador de E/S deve estar em conformidade com os requisitos do controlador FileX definidos no capítulo 5.
- **driver_info_ptr**: Pontear para informações opcionais que o controlador de E/S fornecido pode utilizar.
- **memory_ptr**: Ponte para a memória de trabalho para os meios de comunicação.
- **memory_size**: Especifica o tamanho da memória dos meios de comunicação. O tamanho deve ser tão grande quanto o tamanho do sector dos meios de comunicação (normalmente 512 bytes).

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Meios de comunicação bem sucedidos abertos.
- **FX_BOOT_ERROR** (0x01) Erro de leitura do sector de arranque dos meios de comunicação.
- **FX_MEDIA_INVALID** (0x02) O sector de arranque especificado dos meios de comunicação é corrupto ou inválido. Além disso, este código de devolução é utilizado para indicar que o tamanho da cache do sector lógico ou o tamanho da entrada FAT não é uma potência de 2.
- **FX_FAT_READ_ERROR** (0x03) Erro de leitura do meio de comunicação FAT.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_PTR_ERROR** (0x18) Um ou mais ponteiros são NUOS.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA         ram_disk,
UINT             status;
UCHAR             buffer[128];
/* Open a 32KByte RAM disk starting at the fixed address of 0x800000.
    Note that the total 32KByte media size and 128-byte sector size is defined inside of the driver. */

status = fx_media_open(&ram_disk, "RAM DISK", fx_ram_driver, 0, &buffer[0], sizeof(buffer));

/* If status equals FX_SUCCESS, the RAM disk has been successfully setup and is ready for file access! */

```

### <a name="see-also"></a>Consulte também

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_open_notify_set"></a>fx_media_open_notify_set

Define a função de notificação aberta dos meios de comunicação

### <a name="prototype"></a>Prototype

```c
UINT fx_media_open_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_open_notify)(FX_MEDIA*));
```
### <a name="description"></a>Description

Este serviço define uma função de chamada de notificação que será invocada após a abertura de um meio de comunicação com sucesso.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.
- **media_open_notify**: Os meios de comunicação estão abertos a notificar a função de retorno a instalar. Passar NUDIS como a função de retorno desativa o retorno aberto dos meios de comunicação.

### <a name="return-values"></a>Valores de devolução


- **FX_SUCCESS** (0x00) A função de retorno com sucesso instalou a função de retorno.
- **FX_PTR_ERROR** (0x18) media_ptr é NU.
- **FX_CALLER_ERROR**    (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
fx_media_open_notify_set(media_ptr, my_media_open_callback);

```

### <a name="see-also"></a>Consulte também

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_read"></a>fx_media_read

Lê o setor lógico dos meios de comunicação

### <a name="prototype"></a>Prototype

```c
UINT fx_media_read(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector, 
    VOID *buffer_ptr);
```
### <a name="description"></a>Description

Este serviço lê um sector lógico dos meios de comunicação social e coloca-o no tampão fornecido.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para um meio de comunicação previamente aberto.
- **logical_sector**: Sector lógico para ler.
- **buffer_ptr**: Ponte para o destino para o sector lógico ler.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Leitura bem sucedida dos meios de comunicação social.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiro tampão.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA         my_media;
UCHAR             my_buffer[128];
UINT            STATUS;
/* Read logical sector 22 into "my_buffer" assuming the
    physical media has a sector size of 128. */
status = fx_media_read(&my_media, 22, my_buffer);
/* If status equals FX_SUCCESS, the contents of logical sector 22 are in "my_buffer". */
```

### <a name="see-also"></a>Consulte também

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_space_available"></a>fx_media_space_available

Devolve espaço de mídia disponível

### <a name="prototype"></a>Prototype

```c
UINT fx_media_space_available(
    FX_MEDIA *media_ptr,
    ULONG *available_bytes_ptr);
```

### <a name="description"></a>Description

Este serviço devolve o número de bytes disponíveis nos meios de comunicação.

Para trabalhar com os meios de comunicação superiores a 4GB, a aplicação deve utilizar o serviço *fx_media_extended_space_available*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para um meio de comunicação previamente aberto.
- **available_bytes_ptr**: Bytes disponíveis deixados nos meios de comunicação.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) devolveu com sucesso o espaço disponível nos meios de comunicação.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido ou ponteiro bytes disponível é NU.
- **FX_CALLER_ERROR**    (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA        my_media;
ULONG            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a>Consulte também

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_volume_get"></a>fx_media_volume_get

Obtém o nome do volume dos meios de comunicação

### <a name="prototype"></a>Prototype

```c
UINT fx_media_volume_get(
    FX_MEDIA *media_ptr,
    CHAR *volume_name,
    UINT volume_source);
```
### <a name="description"></a>Description

Este serviço recupera o nome de volume do meio de comunicação anteriormente aberto.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.
- **volume_name**: Ponter para o destino para o nome do volume. Note que o destino deve ser pelo menos grande o suficiente para ter 12 caracteres.
- **volume_source**: Designa onde recuperar o nome, quer do sector do arranque, quer do diretório de raiz. Os valores válidos para este parâmetro são:
  - FX_BOOT_SECTOR
  - FX_DIRECTORY_SECTOR

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Volume de mídia bem sucedido obtém.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **volume FX_NOT_FOUND** (0x04) não encontrado.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiro de destino de volume.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA        ram_disk;
UCHAR             volume_name[12];
/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name), FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */

```

### <a name="see-also"></a>Consulte também

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_volume_get_extended"></a>fx_media_volume_get_extended

Obtém o nome do volume de mídia de meios de comunicação anteriormente abertos

### <a name="prototype"></a>Prototype

```c
UINT fx_media_volume_get_extended(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name,
    UINT volume_name_buffer_length,
    UINT volume_source);
```
### <a name="description"></a>Description

Este serviço recupera o nome de volume do meio de comunicação anteriormente aberto.

> [!IMPORTANT]
> Este serviço é idêntico a ***fx_media_volume_get()** _ exceto que o chamador passa no tamanho do tampão _ *volume_name** .

### <a name="input-parameters"></a>Parâmetros de Entrada


- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.
- **volume_name**: Ponter para o destino para o nome do volume. Note que o destino deve ser pelo menos grande o suficiente para ter 12 caracteres.
- **volume_name_buffer_length**: Tamanho do tampão de volume_name.
- **volume_source**: Designa onde recuperar o nome, quer do sector do arranque, quer do diretório de raiz. Os valores válidos para este parâmetro são:
  - FX_BOOT_SECTOR
  - FX_DIRECTORY_SECTOR

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Volume de mídia bem sucedido obtém.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **volume FX_NOT_FOUND** (0x04) não encontrado.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiro de destino de volume.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA         ram_disk;
UCHAR             volume_name[12];

/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name),
                                      FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_volume_set"></a>fx_media_volume_set

Define o nome do volume dos meios de comunicação

### <a name="prototype"></a>Prototype

```c
UINT fx_media_volume_set(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name);
```
### <a name="description"></a>Description

Este serviço define o nome de volume do meio de comunicação anteriormente aberto.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.
- **volume_name**: Ponteiro para o nome do volume.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Conjunto de volume de mídia bem sucedido.
- **FX_INVALID_NAME** (0x0C) Volume_name é inválida.
- **FX_MEDIA_INVALID** (0x02) Incapaz de definir o nome do volume.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.
- **FX_PTR_ERROR** (0x18) Media inválido ou ponteiro de nome de volume.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA ram_disk;

/* Set the volume name to "MY_VOLUME". */

status = fx_media_volume_set(&ram_disk, "MY_VOLUME");

/* If status is FX_SUCCESS, the volume name was successfully set. */
```

### <a name="see-also"></a>Consulte também

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_write
- fx_system_initialize

## <a name="fx_media_write"></a>fx_media_write

Escreve o setor lógico

### <a name="prototype"></a>Prototype

```c
UINT fx_media_write(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector,
    VOID *buffer_ptr);
```
### <a name="description"></a>Description

Este serviço escreve o tampão fornecido para o sector lógico especificado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para um meio de comunicação previamente aberto.
- **logical_sector**: Sector lógico para escrever.
- **buffer_ptr**: Ponteiro para a fonte para o setor lógico escrever.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Os meios de comunicação de sucesso escrevem.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.
- **FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido.
- **FX_CALLER_ERROR**    (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA             my_media;
UCHAR                 my_buffer[128];
UINT                 status;

/* Write logical sector 22 from "my_buffer" assuming
    the physical media has a sector size of 128. */

status = fx_media_write(&my_media, 22, my_buffer);

/* If status equals FX_SUCCESS, the contents of logical
    sector 22 are now the same as "my_buffer." */
```

### <a name="see-also"></a>Consulte também

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_system_initialize

## <a name="fx_system_date_get"></a>fx_system_date_get

Obtém a data do sistema de ficheiros

### <a name="prototype"></a>Prototype

```c
UINT fx_system_date_get(
    UINT *year, 
    UINT *month, 
    UINT *day);
```
### <a name="description"></a>Description

Este serviço devolve a data atual do sistema.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ano**: Ponteiro para destino para o ano.
- **mês**: Ponteiro para destino para o mês.
- **dia**: Ponteiro para destino para o dia.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Recuperação de datas bem sucedidas.
- **FX_PTR_ERROR** (0x18) Um ou mais dos parâmetros de entrada são NUOS.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
UINT            status;
UINT            year;
UINT            month;
UINT            day;
/* Retrieve the current system date. */

status = fx_system_date_get(&year, &month, &day);

/* If status equals FX_SUCCESS, the year, month,
    and day parameters now have meaningful information. */
```

### <a name="see-also"></a>Consulte também

- fx_system_date_set
- fx_system_initialize
- fx_system_time_get
- fx_system_time_set

## <a name="fx_system_date_set"></a>fx_system_date_set

Define a data do sistema

### <a name="prototype"></a>Prototype

```c
UINT fx_system_date_set(
    UINT year, 
    UINT month, 
    UINT day);
```

### <a name="description"></a>Description

Este serviço define a data do sistema conforme especificado.

> [!WARNING]
> *Este serviço deve ser chamado pouco depois **fx_system_initialize** para definir a data inicial do sistema. Por predefinição, a data do sistema é a da última versão genérica do FileX.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ano**: Ano Novo. A gama válida é de 1980 até ao ano 2107.
- **mês**: Mês Novo. O intervalo válido é de 1 a 12.
- **dia**: Novo dia. O intervalo válido é de 1 a 31, dependendo das condições do mês e do ano bissexto.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Definição de data de sucesso.
- **FX_INVALID_YEAR** (0x12) Ano inválido especificado.
- **FX_INVALID_MONTH** (0x13) mês inválido especificado.
- **FX_INVALID_DAY** (0x14) Dia inválido especificado.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
 UINT             status;

/* Set the system date to December 12, 2005. */

status = fx_system_date_set(2005, 12, 12);

/* If status equals FX_SUCCESS, the file system date is now
    12-12-2005. */
```

### <a name="see-also"></a>Consulte também

- fx_system_date_get
- fx_system_initialize
- fx_system_time_get
- fx_system_time_set

## <a name="fx_system_initialize"></a>fx_system_initialize

Inicializa todo o sistema

### <a name="prototype"></a>Prototype

```c
VOID fx_system_initialize(void);
```

### <a name="description"></a>Description

Este serviço inicializa todas as principais estruturas de dados do FileX. Deve ser chamado em ***tx_application_define*** ou possivelmente a partir de um fio de inicialização e deve ser chamado antes de usar qualquer outro serviço FileX.

> [!WARNING]
> *Uma vez inicializado por esta chamada, a aplicação deve chamar ***fx_system_date_set** _ e _ *fx_system_time_set** para começar com uma data e hora precisas do sistema.*

### <a name="input-parameters"></a>Parâmetros de Entrada

Nenhum

### <a name="return-values"></a>Valores de devolução

Nenhum.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
void tx_application_define(VOID *free_memory)
{
    UINT status;
    /* Initialize the FileX system. */
    fx_system_initialize();
    /* Set the file system date. */
    fx_system_date_set(my_year, my_month, my_day);

    /* Set the file system time. */
    fx_system_time_set(my_hour, my_minute, my_second);

    /* Now perform all other initialization and possibly FileX media
        open calls if the corresponding driver does not block on the boot sector read. */

    ...

}
```

### <a name="see-also"></a>Consulte também

- fx_system_date_get
- fx_system_date_set
- fx_system_time_get
- fx_system_time_set

## <a name="fx_system_time_get"></a>fx_system_time_get

Obtém tempo atual do sistema

### <a name="prototype"></a>Prototype

```c
UINT fx_system_time_get(
    UINT *hour,
    UINT *minute,
    UINT *second);
```

### <a name="description"></a>Description

Este serviço recupera o tempo atual do sistema.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **hora**: Ponteiro para destino por hora.
- **minuto**: Ponteiro para destino por um minuto.
- **segundo**: Ponteiro para destino para o segundo.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Recuperação de tempo bem sucedida do sistema.
- **FX_PTR_ERROR** (0x18) Um ou mais dos parâmetros de entrada

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
UINT             status;
UINT             hour;
UINT             minute;
UINT             second;

/* Retrieve the current system time. */

status = fx_system_time_get(&hour, &minute, &second);

/* If status equals FX_SUCCESS, the current system time
    is in the hour, minute, and second variables. */
```

### <a name="see-also"></a>Consulte também

- fx_system_date_get
- fx_system_date_set
- fx_system_initialize
- fx_system_time_set

## <a name="fx_system_time_set"></a>fx_system_time_set

Define o tempo atual do sistema

### <a name="prototype"></a>Prototype

```c
UINT fx_system_time_set(UINT hour, UINT minute, UINT second);
```

### <a name="description"></a>Description

Este serviço define o tempo atual do sistema para o especificado pelos parâmetros de entrada.

> [!WARNING]
> *Este serviço deve ser chamado pouco depois **fx_system_initialize** para definir o tempo inicial do sistema. Por padrão, o tempo do sistema é 0:0:0.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **hora:** Hora nova (0-23).
- **minuto**: Novo minuto (0-59).
- **segundo**: Novo segundo (0-59).

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Recuperação de tempo bem sucedida do sistema.
- **FX_INVALID_HOUR**    (0x15) A hora nova é inválida.
- **FX_INVALID_MINUTE** (0x16) Novo minuto é inválido.
- **FX_INVALID_SECOND** (0x17) O segundo novo é inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
 UINT status;

/* Set the current system time to hour 23, minute 21, and second 20. */

status = fx_system_time_set(23, 21, 20);

/* If status is FX_SUCCESS, the current system time has been set. */
```

### <a name="see-also"></a>Consulte também

- fx_system_date_get
- fx_system_date_set
- fx_system_initialize
- fx_system_time_get

## <a name="fx_unicode_directory_create"></a>fx_unicode_directory_create

Cria um diretório Unicode

### <a name="prototype"></a>Prototype

```c
UINT fx_unicode_directory_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```
### <a name="description"></a>Description

Este serviço cria um subdiretório nomeado Unicode no diretório predefinido atual — nenhuma informação de caminho é permitida no parâmetro de nome de origem Unicode. Se for bem sucedido, o nome curto (formato 8.3) da recém-criada subdirectory Unicode é devolvido pelo serviço.

> [!WARNING]
> *Todas as operações no subdiretório Unicode (tornando-o o caminho padrão, eliminação, etc.) devem ser efetuadas fornecendo o nome curto devolvido (formato 8.3) aos serviços de diretório padrão do FileX.*

> [!IMPORTANT]
> *Este serviço não é suportado em meios exFAT.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.
- **source_unicode_name**: Pontear o nome Unicode para o novo subdiretório.
- **source_unicode_length**: Comprimento do nome Unicode.
- **short_name**: Ponter para o destino para nome curto (formato 8.3) para o novo subdiretório Unicode.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Diretório de sucesso Unicode criar.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_ALREADY_CREATED** (0x0B) Diretório especificado já existe.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais clusters disponíveis nos meios de comunicação para a entrada do novo diretório.
- **FX_NOT_IMPLEMENTED** (0x22) Serviço não implementado para o sistema de ficheiros exFAT.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.
- **FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiros de nome.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.
- **FX_IO_ERROR (0x90)** Erro de I/O do condutor.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA             ram_disk;
UCHAR                 my_short_name[13];
UCHAR                 my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                         0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                         0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                         0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                         0x63,0x00, 0x00,0x00};

/* Create a Unicode subdirectory with the name contained in "my_unicode_name". */

length = fx_unicode_directory_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode subdirectory is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a>Consulte também

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_rename

## <a name="fx_unicode_directory_rename"></a>fx_unicode_directory_rename

Rebatiza diretório usando a cadeia Unicode

### <a name="prototype"></a>Prototype

```c
UINT fx_unicode_directory_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length,
    CHAR *new_short_name);
```
### <a name="description"></a>Description

Este serviço altera uma subdiretório nomeada pelo Unicode para o novo nome Unicode especificado no diretório de trabalho atual. Os parâmetros do nome Unicode não devem ter informações sobre o caminho.

> [!IMPORTANT]
> *Este serviço não é suportado em meios exFAT.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.
- **old_unicode_name**: Pontear o nome Unicode para o ficheiro atual.
- **old_unicode_name_length**: Comprimento do nome atual do Unicode.
- **new_unicode_name**: Pontear o novo nome do ficheiro Unicode.
- **old_unicode_name_length**: Comprimento do novo nome Unicode.
- **new_short_name**: Ponteiro para destino para nome curto (formato 8.3) para o rebatizado ficheiro Unicode. Diretório de renomeação com Unicode

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Meios de comunicação bem sucedidos abertos.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_ALREADY_CREATED** (0x0B) Nome de diretório especificado já existe.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_PTR_ERROR** (0x18) Um ou mais ponteiros são NUOS.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados estão protegidos por escrito.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_directory_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the directory was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a>Consulte também

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create

## <a name="fx_unicode_file_create"></a>fx_unicode_file_create

Cria um ficheiro Unicode

### <a name="prototype"></a>Prototype

```c
UINT fx_unicode_file_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```

### <a name="description"></a>Description

Este serviço cria um ficheiro nomeado pelo Unicode no diretório predefinido atual — nenhuma informação de caminho é permitida no parâmetro de nome de origem Unicode. Se for bem sucedido, o nome curto (formato 8.3) do ficheiro Unicode recém-criado é devolvido pelo serviço.

> [!WARNING]
> *Todas as operações no ficheiro Unicode (abertura, escrita, leitura, fecho, etc.) devem ser efetuadas fornecendo o nome curto devolvido (formato 8.3) aos serviços de ficheiros FileX padrão.*

### <a name="input-parameters"></a>Parâmetros de Entrada


- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.
- **source_unicode_name**: Ponter o nome Unicode para o novo ficheiro.
- **source_unicode_length**: Comprimento do nome Unicode.
- **short_name**: Ponteiro para destino para nome curto (formato 8.3) para o novo ficheiro Unicode.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Criação de ficheiros bem sucedidos.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_ALREADY_CREATED** (0x0B) Ficheiro especificado já existe.
- **FX_NO_MORE_SPACE** (0x0A) Não há mais clusters disponíveis nos meios de comunicação para a entrada do novo ficheiro.
- **FX_NOT_IMPLEMENTED** (0x22) Serviço não implementado para o sistema de ficheiros exFAT.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.
- **FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiros de nome.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Create a Unicode file with the name contained in "my_unicode_name". */

length = fx_unicode_file_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode file is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_file_rename"></a>fx_unicode_file_rename

Renomea um ficheiro usando uma cadeia unicode

### <a name="prototype"></a>Prototype

```c
UINT fx_unicode_file_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length, 
    CHAR *new_short_name);
```

### <a name="description"></a>Description

Este serviço altera um nome de ficheiro nomeado Unicode para o novo nome Unicode especificado no diretório predefinido atual. Os parâmetros do nome Unicode não devem ter informações sobre o caminho.

> [!IMPORTANT]
> *Este serviço não é suportado em meios exFAT.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.
- **old_unicode_name**: Pontear o nome Unicode para o ficheiro atual.
- **old_unicode_name_length**: Comprimento do nome atual do Unicode.
- **new_unicode_name**: Pontear o novo nome do ficheiro Unicode.
- **new_unicode_name_length**: Comprimento do novo nome Unicode.
- **new_short_name**: Ponteiro para destino para nome curto (formato 8.3) para o rebatizado ficheiro Unicode.

### <a name="return-values"></a>Valores de devolução


- **FX_SUCCESS** (0x00) Meios de comunicação bem sucedidos abertos.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_ALREADY_CREATED** (0x0B) Nome de ficheiro especificado já existe.
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_PTR_ERROR** (0x18) Um ou mais ponteiros são NUOS.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.
- **FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados estão protegidos por escrito.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_file_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the file name was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_length_get"></a>fx_unicode_length_get

Obtém comprimento do nome Unicode

### <a name="prototype"></a>Prototype

```c
ULONG fx_unicode_length_get(UCHAR *unicode_name);
```
### <a name="description"></a>Description

Este serviço determina o comprimento do nome Unicode fornecido. Um caracteres Unicode é representado por dois bytes. Um nome Unicode é uma série de dois caracteres Unicode byte terminados por dois bytes NULL (dois bytes de 0 valor).

### <a name="input-parameters"></a>Parâmetros de Entrada

**unicode_name**: Ponteiro para o nome Unicode.

### <a name="return-values"></a>Valores de devolução

**comprimento**: Comprimento do nome Unicode (número de caracteres Unicode no nome).

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
UCHAR     my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                           0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                           0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                           0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                           0x63,0x00, 0x00,0x00};

UINT     length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get(my_unicode_name);

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_length_get_extended"></a>fx_unicode_length_get_extended

Obtém comprimento do nome Unicode

### <a name="prototype"></a>Prototype

```c
UINT fx_unicode_length_get_extended(
    UCHAR *unicode_name,
    UINT buffer_length);
```
### <a name="description"></a>Description

Este serviço obtém o comprimento do nome Unicode fornecido. Um caracteres Unicode é representado por dois bytes. Um nome Unicode é uma série de caracteres Unicode de doisbytes terminados por dois bytes NULL (dois bytes de 0 valor).

> [!IMPORTANT]
> *Este serviço é idêntico ao **fx_unicode_length_get()** exceto que o chamador passa no tamanho do tampão **unicode_name,** incluindo os dois caracteres NU.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **unicode_name**: Ponteiro para o nome Unicode.
- **buffer_length**: Tamanho do tampão de nome Unicode.

### <a name="return-values"></a>Valores de devolução

**comprimento**: Comprimento do nome Unicode (número de caracteres Unicode no nome).

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
UCHAR         my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                 0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                 0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                 0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                 0x63,0x00, 0x00,0x00};

UINT         length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get_extended(my_unicode_name, sizeof(my_unicode_name));

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_name_get"></a>fx_unicode_name_get

Obtém o nome Unicode de nome curto

### <a name="prototype"></a>Prototype

```c
UINT fx_unicode_name_get(
    FX_MEDIA *media_ptr, 
    CHAR *source_short_name,
    UCHAR *destination_unicode_name, 
    ULONG *destination_unicode_length);
```

### <a name="description"></a>Description

Este serviço recupera o nome Unicode associado ao nome curto fornecido (formato 8.3) dentro do diretório predefinido atual — nenhuma informação sobre o caminho é permitida no parâmetro de nome curto. Se for bem sucedido, o nome Unicode associado ao nome curto é devolvido pelo serviço.

> [!IMPORTANT]
> *Este serviço pode ser utilizado para obter nomes unicode para ambos os ficheiros e subdireções.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.
- **short_name** Ponteiro para nome curto (formato 8.3).
- **destination_unicode_name**: Ponter para o destino do nome Unicode associado ao nome curto fornecido.
- **destination_unicode_length**: Ponteiro para devolver o comprimento do nome Unicode.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Recuperação de nomes unicode bem sucedidos.
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a tabela FAT.
- **FX_FILE_CORRUPT** (0x08) File é corrompido
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_NOT_FOUND** (0x04) Não foi encontrado nome curto ou o tamanho do destino Unicode é demasiado pequeno.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiros de nome.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA             ram_disk;
UCHAR                 my_unicode_name[256*2];
ULONG                 unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the
    number of maximum characters in the name. */

length = fx_unicode_name_get(&ram_disk, "ABC0~111.TXT", my_unicode_name, unicode_name_length);

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_short_name_get

## <a name="fx_unicode_name_get_extended"></a>fx_unicode_name_get_extended

Obtém o nome Unicode de nome curto

### <a name="prototype"></a>Prototype

```c
UINT fx_unicode_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *source_short_name,
    UCHAR *destination_unicode_name,
    ULONG *destination_unicode_length,
    ULONG unicode_name_buffer_length);
```
### <a name="description"></a>Description

Este serviço recupera o nome Unicode associado ao nome curto fornecido (formato 8.3) dentro do diretório predefinido atual — nenhuma informação sobre o caminho é permitida no parâmetro de nome curto. Se for bem sucedido, o nome Unicode associado ao nome curto é devolvido pelo serviço.

> [!IMPORTANT]
> *Este serviço é idêntico a ***fx_unicode_name_get,**_exceto que o chamador fornece o tamanho do tampão Unicode de destino como argumento de entrada. Isto permite que o serviço garanta que não substituirá o destino Unicode buffer_

> [!IMPORTANT]
> *Este serviço pode ser utilizado para obter nomes unicode para ambos os ficheiros e subdireções.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.
- **short_name**: Ponteiro para nome curto (formato 8.3).
- **destination_unicode_name**: Ponter para o destino do nome Unicode associado ao nome curto fornecido.
- **destination_unicode_length**: Ponteiro para devolver o comprimento do nome Unicode.
- **unicode_name_buffer_length**: Tamanho do tampão de nome Unicode. Nota: É necessário um exterminador NULO, o que faz um byte extra.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Recuperação de nomes unicode bem sucedidos.
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a tabela FAT.
- **FX_FILE_CORRUPT** (0x08) File é corrompido
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_NOT_FOUND** (0x04) Não foi encontrado nome curto ou o tamanho do destino Unicode é demasiado pequeno.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiros de nome.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA         ram_disk;
UCHAR             my_unicode_name[256*2];
ULONG             unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the number of maximum characters in the name. */

length = fx_unicode_name_get_extended(&ram_disk, "ABC0~111.TXT",
    my_unicode_name,&unicode_name_length, sizeof(ny_unicode_name));

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_short_name_get

## <a name="fx_unicode_short_name_get"></a>fx_unicode_short_name_get

Obtém nome curto do nome Unicode

### <a name="prototype"></a>Prototype

```c
UINT fx_unicode_short_name_get(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length,
    CHAR *destination_short_name);
```

Este serviço recupera o nome curto (formato 8.3) associado ao nome Unicode dentro do diretório predefinido atual — nenhuma informação de caminho é permitida no parâmetro nome Unicode. Se for bem sucedido, o nome curto associado ao nome Unicode é devolvido pelo serviço.

> [!IMPORTANT]
> *Este serviço pode ser utilizado para obter nomes curtos para ficheiros e subdireções.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.
- **source_unicode_name**: Ponteiro para o nome Unicode.
- **source_unicode_length**: Comprimento do nome Unicode.
- **destination_short_name**: Ponter para o destino para o nome curto (formato 8.3). Isto deve ter pelo menos 13 bytes de tamanho.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Recuperação de nomes curtos bem-sucedidos.
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a tabela FAT.
- **FX_FILE_CORRUPT** (0x08) File é corrompido
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_NOT_FOUND** (0x04) Não foi encontrado o nome unicode.
- **FX_NOT_IMPLEMENTED** (0x22) Serviço não implementado para o sistema de ficheiros exFAT.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiros de nome.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get

## <a name="fx_unicode_short_name_get_extended"></a>fx_unicode_short_name_get_extended

Obtém nome curto do nome Unicode

### <a name="prototype"></a>Prototype

```c
UINT fx_unicode_short_name_get_extended(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *destination_short_name,
    ULONG short_name_buffer_length);
```

### <a name="description"></a>Description

Este serviço recupera o nome curto (formato 8.3) associado ao nome Unicode dentro do diretório predefinido atual — nenhuma informação de caminho é permitida no parâmetro nome Unicode. Se for bem sucedido, o nome curto associado ao nome Unicode é devolvido pelo serviço.

> [!IMPORTANT]
> *Este serviço é idêntico ao **fx_unicode_short_name_get()**, exceto que o chamador fornece o tamanho do tampão de destino como argumento de entrada. Isto permite que o serviço garanta que o nome curto não exceda o tampão de destino.*

*Este serviço pode ser usado para obter nomes curtos para ambos os ficheiros e subdireções*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.
- **source_unicode_name**: Ponteiro para o nome Unicode.
- **source_unicode_length**: Comprimento do nome Unicode.
- **destination_short_name**: Ponter para o destino para o nome curto (formato 8.3). Isto deve ter pelo menos 13 bytes de tamanho.
- **short_name_buffer_length**: Tamanho do tampão de destino. O tamanho do tampão deve ser de, pelo menos, 14 bytes.

### <a name="return-values"></a>Valores de devolução

- **FX_SUCCESS** (0x00) Recuperação de nomes curtos bem-sucedidos.
- **FX_FAT_READ_ERROR** (0x03) Incapaz de ler a tabela FAT.
- **FX_FILE_CORRUPT** (0x08) File é corrompido
- **FX_IO_ERROR** (0x90) Erro de I/O do condutor.
- **FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.
- **FX_NOT_FOUND** (0x04) Não foi encontrado o nome unicode.
- **FX_NOT_IMPLEMENTED** (0x22) Serviço não implementado para o sistema de ficheiros exFAT.
- **FX_SECTOR_INVALID** (0x89) Sector inválido.
- **FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiros de nome.
- **FX_CALLER_ERROR** (0x20) Caller não é um fio.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
#define         SHORT_NAME_BUFFER_SIZE 13
FX_MEDIA         ram_disk;
UCHAR             my_short_name[SHORT_NAME_BUFFER_SIZE];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get_extended(&ram_disk,
    my_unicode_name, 17, my_short_name,SHORT_NAME_BUFFER_SIZE);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a>Consulte também

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get
