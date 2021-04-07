---
title: Capítulo 5 - Condutores de E/S para Azure RTOS FileX
description: Este capítulo contém uma descrição dos controladores de I/S para O Azure RTOS FileX e foi concebido para ajudar os desenvolvedores a escrever condutores específicos da aplicação.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8f2ef697f68a269b24a34147a4bc076b8a2b1660
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550087"
---
# <a name="chapter-5---io-drivers-for-azure-rtos-filex"></a>Capítulo 5 - Condutores de E/S para Azure RTOS FileX

Este capítulo contém uma descrição dos controladores de I/S para O Azure RTOS FileX e foi concebido para ajudar os desenvolvedores a escrever condutores específicos da aplicação.

## <a name="io-driver-introduction"></a>Introdução do condutor de I/O

O FileX suporta vários dispositivos de mídia. A estrutura FX_MEDIA define tudo o que é necessário para gerir um dispositivo de mídia. Esta estrutura contém todas as informações dos meios de comunicação, incluindo o controlador de I/O específico dos meios de comunicação e parâmetros associados para a passagem de informações e estado entre o controlador e o FileX. Na maioria dos sistemas, existe um controlador de E/S único para cada instância de media FileX.

## <a name="io-driver-entry"></a>Entrada do condutor I/O

Cada controlador FileX I/O tem uma única função de entrada definida pela chamada de serviço ***fx_media_open.*** A função de entrada do controlador tem o seguinte formato:

```c
void my_driver_entry(FX_MEDIA *media_ptr);
```

O FileX chama a função de entrada do controlador de I/S para solicitar todo o acesso aos meios físicos, incluindo a inicialização e a leitura do setor de arranque. Os pedidos feitos ao condutor são feitos sequencialmente; ou seja, o FileX aguarda que o pedido atual seja concluído antes de ser enviado outro pedido.

## <a name="io-driver-requests"></a>Pedidos de motorista de I/O

Como cada controlador de E/S tem uma única função de entrada, o FileX faz pedidos específicos através do bloco de controlo de mídia. Especificamente, o  **fx_media_driver_request** membro da **FX_MEDIA** é usado para especificar o pedido exato do condutor. O condutor de I/S comunica o sucesso ou insucesso do pedido através do **fx_media_driver_status** membro da **FX_MEDIA**. Se o pedido do condutor tiver sido bem sucedido, **FX_SUCCESS** é colocado neste campo antes do retorno do condutor. Caso contrário, se for detetado um erro, FX_IO_ERROR é colocado neste campo.

### <a name="driver-initialization"></a>Inicialização do condutor

Embora o processamento de inicialização do condutor real seja específico da aplicação, geralmente consiste na inicialização da estrutura de dados e possivelmente em alguma inicialização preliminar de hardware. Este pedido é o primeiro feito pelo FileX e é feito a partir do serviço fx_media_open.

Se for detetada proteção contra a escrita dos meios de comunicação, o condutor fx_media_driver_write_protect membro da FX_MEDIA deve ser definido para FX_TRUE.

São utilizados os seguintes membros FX_MEDIA para o pedido de inicialização do condutor de E/S:

|FX_MEDIA membro|Significado|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_INIT|

O FileX fornece um mecanismo para informar o controlador de aplicações quando os sectores já não estão a ser utilizados. Isto é especialmente útil para os gestores de memória FLASH que devem gerir todos os sectores lógicos em uso mapeados para o FLASH.

Se tal notificação dos sectores livres for necessária, o condutor da aplicação limita-se a definir o campo *fx_media_driver_free_sector_update* na estrutura **FX_MEDIA** associada para **FX_TRUE**. Depois de definido, o FileX faz uma **_chamada de_** controlador de I/S FX_DRIVER_RELEASE_SECTORS indicando quando um ou mais sectores consecutivos ficam livres.

### <a name="boot-sector-read"></a>Leitura do Setor de Arranque

Em vez de utilizar um pedido de leitura padrão, o FileX faz um pedido específico para ler o setor de arranque dos meios de comunicação. São utilizados os seguintes **membros FX_MEDIA** para o pedido de arranque do condutor:

|FX_MEDIA membro|Significado|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_BOOT_READ|
|fx_media_driver_buffer| Endereço de destino para o setor de arranque.|

### <a name="boot-sector-write"></a>Escrita do Setor de Arranque

Em vez de utilizar um pedido de escrita padrão, o FileX faz um pedido específico para escrever o setor de arranque dos meios de comunicação. São utilizados os seguintes **membros FX_MEDIA** para o pedido de escrita do sector do arranque do condutor:

|FX_MEDIA membro|Significado|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_BOOT_WRITE|
|fx_media_driver_buffer| Endereço de fonte para o sector de arranque.|

### <a name="sector-read"></a>Leitura do Sector

O FileX lê um ou mais sectores na memória ao emitir um pedido de leitura ao controlador de E/S. São utilizados os seguintes **membros FX_MEDIA** para o pedido de leitura do controlador de E/S:

|FX_MEDIA membro|Significado|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_READ|
|fx_media_driver_logical_sector|Setor lógico para ler|
|fx_media_driver_sectors|Número de sectores a ler|
|fx_media_driver_buffer|Tampão de destino para o(s) sectorial(s) lido|
|fx_media_driver_data_sector_read|Definido para FX_TRUE se um sector de dados de ficheiros for solicitado. Caso contrário, FX_FALSE se for solicitado um sector de sistema (FAT ou sector de diretório).|
|fx_media_driver_sector_type|Define o tipo explícito de sector solicitado, da seguinte forma:<br />FX_FAT_SECTOR (2)<br />FX_DIRECTORY_SECTOR (3)<br />FX_DATA_SECTOR (4)|

### <a name="sector-write"></a>Escrita sectorial

FileX escreve um ou mais sectores para os meios físicos, emitindo um pedido de escrita ao controlador de I/S. São utilizados os seguintes membros FX_MEDIA para o pedido de escrita do condutor de E/S:

|FX_MEDIA membro| Significado|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_WRITE|
|fx_media_driver_logical_sector|Setor lógico para escrever|
|fx_media_driver_sectors|Número de sectores a escrever|
|fx_media_driver_buffer|Tampão de origem para o sector(s) para escrever|
|fx_media_driver_system_write| Definido para FX_TRUE se for solicitado um sector do sistema (FAT ou sector do diretório). Caso contrário, FX_FALSE se for solicitado um sector de dados de ficheiros.|
|fx_media_driver_sector_type|Define o tipo explícito de sector solicitado, da seguinte forma:<br> <br>FX_FAT_SECTOR (2) <br> FX_DIRECTORY_SECTOR (3) <br>FX_DATA_SECTOR (4).|

### <a name="driver-flush"></a>Auto-descarga do condutor

O FileX descarrega todos os sectores atualmente na cache do sector do condutor para os meios físicos, emitindo um pedido de descarga ao condutor de I/O. Naturalmente, se o condutor não estiver a fazer caching sectores, este pedido não requer processamento de condutor. São utilizados os seguintes membros FX_MEDIA para o pedido de autoclismo do condutor:

|FX_MEDIA membro| Significado|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_FLUSH|

### <a name="driver-abort"></a>Aborto do motorista

A FileX informa o condutor a abortar toda a atividade física de E/S com os meios físicos, emitindo um pedido de abortar ao controlador de I/O. O condutor não deve voltar a efetuar qualquer E/S até ser re-inicializado. São utilizados os seguintes membros FX_MEDIA para o pedido de aborto do condutor de E/S:

|FX_MEDIA membro| Significado|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_ABORT|

### <a name="release-sectors"></a>Sectores de Libertação

Se previamente selecionado pelo controlador durante a inicialização, o FileX informa o controlador sempre que um ou mais sectores consecutivos ficam livres. Se o controlador for realmente um gestor FLASH, esta informação pode ser usada para dizer ao gestor flash que estes sectores já não são necessários. São utilizados os seguintes **membros FX_MEDIA** para o pedido dos sectores de libertação de E/O:

|FX_MEDIA membro| Significado|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_RELEASE_SECTORS|
|fx_media_driver_logical_sector|Início do setor livre|
|fx_media_driver_sectors|Número de sectores livres|

### <a name="driver-suspension"></a>Suspensão do condutor

Porque i/S com meios físicos pode levar algum tempo, suspender o fio de vocação é muitas vezes desejável. É claro que isto pressupõe que a conclusão da operação de E/S subjacente é interrompida. Em caso afirmativo, a suspensão do fio é facilmente implementada com um semáforo ThreadX. Após iniciar a operação de entrada ou saída, o controlador de I/S suspende o seu próprio semáforo de I/O interno (criado com uma contagem inicial de zero durante a inicialização do condutor). Como parte do processo de interrupção de conclusão do condutor, o mesmo semáforo de I/O está definido, o que por sua vez acorda o fio suspenso.

### <a name="sector-translation"></a>Tradução do Sector

Como o FileX vê os meios como sectores lógicos lineares, os pedidos de E/S feitos ao condutor de I/O são feitos com sectores lógicos. É da responsabilidade do condutor traduzir entre sectores lógicos e a geometria física dos meios de comunicação social, que podem incluir cabeças, pistas e sectores físicos. Para os meios de comunicação flash e RAM, os sectores lógicos normalmente mapeiam o diretório para sectores físicos. Em todo o caso, aqui estão as fórmulas típicas para executar o mapeamento lógico para o setor físico no condutor de E/S:

```c
media_ptr -> fx_media_driver_physical_sector =
    (media_ptr -> fx_media_driver_logical_sector % media_ptr -> fx_media_sectors_per_track) + 1;

media_ptr -> fx_media_driver_physical_head =
    (media_ptr -> fx_media_driver_logical_sector/ media_ptr ->
    fx_media_sectors_per_track) % media_ptr -> fx_media_heads;

media_ptr -> fx_media_driver_physical_track =(media_ptr ->
    fx_media_driver_logical_sector/ (media_ptr -> fx_media_sectors_per_track *
    media_ptr -> fx_media_heads)));
```

Note-se que os sectores físicos começam em um, enquanto os sectores lógicos começam a zero.

### <a name="hidden-sectors"></a>Sectores Ocultos

Os sectores ocultos residiam antes do recorde de arranque nos meios de comunicação. Por estarem realmente fora do âmbito do esquema do sistema de ficheiros FAT, devem ser contabilizados em cada operação do sector lógico que o condutor faz.

### <a name="media-write-protect"></a>Media Write Protect

O controlador FileX pode ligar a escrever proteger definindo o campo fx_media_driver_write_protect no bloco de controlo dos meios de comunicação. Isto causará a devolvição de um erro se alguma chamada do FileX for feita numa tentativa de escrever para os meios de comunicação.

## <a name="sample-ram-driver"></a>Condutor de RAM de amostra

O sistema de demonstração FileX é entregue com um pequeno controlador de disco RAM, que é definido no ficheiro fx_ram_driver.c. O condutor assume um espaço de memória de 32K e cria um recorde de arranque para 256 sectores de 128 bytes. Este ficheiro fornece um bom exemplo de como implementar controladores específicos do FileX I/O da aplicação.

```c
/*FUNCTION: _fx_ram_driver
RELEASE: PORTABLE C 5.7
AUTHOR: William E. Lamie, Microsoft, Inc.
DESCRIPTION: This function is the entry point to the generic
    RAM disk driver that is delivered with all versions of FileX.
    The format of the RAM disk is easily modified by calling fx_media_format prior to opening the media.

    This driver also serves as a template for developing FileX drivers
    for actual devices. Simply replace the read/write sector logic
    with calls to read/write from the appropriate physical device.

FileX RAM/FLASH structures look like the following:
Physical Sector             Contents
    0                         Boot record
    1                         FAT Area Start
    +FAT Sectors             Root Directory Start
    +Directory Sectors         Data Sector Start

INPUT: media_ptr Media control block pointer
OUTPUT: None
CALLS:     _fx_utility_memory_copy Copy sector memory
        _fx_utility_16_unsigned_read Read 16-bit unsigned
CALLED BY: FileX System Functions
RELEASE HISTORY:

    DATE         NAME         DESCRIPTION
    12-12-2005     William E.     Lamie Initial Version 5.0
    07-18-2007     William E.     Lamie Modified comment(s),
                                resulting in version 5.1
    03-01-2009     William E.     Lamie Modified comment(s),
                                resulting in version 5.2
    11-01-2015     William E.     Lamie Modified comment(s),
                                resulting in version 5.3
    04-15-2016     William E.     Lamie Modified comment(s),
                                resulting in version 5.4
    04-03-2017     William E.     Lamie Modified comment(s),
                                fixed compiler warnings,
                                resulting in version 5.5
    12-01-2018     William E.     Lamie Modified comment(s),
                                checked buffer overflow,
                                resulting in version 5.6
    08-15-2019     William E.     Lamie Modified comment(s),
                                resulting in version 5.7
*/

VOID _fx_ram_driver(FX_MEDIA *media_ptr) { UCHAR *source_buffer;
                                           UCHAR *destination_buffer;
                                           UINT bytes_per_sector;

    /* There are several useful/important pieces of information contained
        in the media structure, some of which are supplied by FileX and
        others are for the driver to setup. The following
        is a summary of the necessary FX_MEDIA structure members:
    FX_MEDIA Member                     Meaning

    fx_media_driver_request             FileX request type.
        Valid requests from FileX are as follows:
        FX_DRIVER_READ
        FX_DRIVER_WRITE
        FX_DRIVER_FLUSH
        FX_DRIVER_ABORT
        FX_DRIVER_INIT
        FX_DRIVER_BOOT_READ
        FX_DRIVER_RELEASE_SECTORS
        FX_DRIVER_BOOT_WRITE FX_DRIVER_UNINIT

    fx_media_driver_status              This value is RETURNED by the driver.
        If the operation is successful, this field should be set to FX_SUCCESS
        for before returning. Otherwise, if an error occurred, this field should be set to FX_IO_ERROR.

    fx_media_driver_buffer              Pointer to buffer to read or write sector data. This is supplied by FileX.

    fx_media_driver_logical_sector      Logical sector FileX is requesting.
    fx_media_driver_sectors             Number of sectors FileX is requesting.

    The following is a summary of the optional FX_MEDIA structure members: FX_MEDIA Member Meaning

    fx_media_driver_info                Pointer to any additional information or memory.
        This is optional for the driver use and is setup from the fx_media_open call.
        The RAM disk uses this pointer for the RAM disk memory itself.

    fx_media_driver_write_protect       The DRIVER sets this to FX_TRUE when media is write protected.
        This is typically done in initialization, but can be done anytime.

    fx_media_driver_free_sector_update  The DRIVER sets this to FX_TRUE when it needs
        to know when clusters are released. This is important for FLASH wear-leveling drivers.

    fx_media_driver_system_write        FileX sets this flag to FX_TRUE if the sector
        being written is a system sector, e.g., a boot, FAT, or directory sector.
        The driver may choose to use this to initiate error recovery logic for greater fault
        tolerance. fx_media_driver_data_sector_read FileX sets this flag to FX_TRUE
        if the sector(s) being read are file data sectors, i.e., NOT system sectors.

    fx_media_driver_sector_type         FileX sets this variable to the specific type of
        sector being read or written. The following sector types are identified:
            FX_UNKNOWN_SECTOR
            FX_BOOT_SECTOR
            FX_FAT_SECTOR
            FX_DIRECTORY_SECTOR
            FX_DATA_SECTOR */

    /* Process the driver request specified in the media control block. */

    switch (media_ptr -> fx_media_driver_request){

        case FX_DRIVER_READ: {

            /* Calculate the RAM disk sector offset. Note the RAM disk memory
            is pointed to by the fx_media_driver_info pointer, which is supplied
            by the application in the call to fx_media_open. */

            source_buffer = ((UCHAR *)media_ptr -> fx_media_driver_info) +
                ((media_ptr -> fx_media_driver_logical_sector +
                media_ptr -> fx_media_hidden_sectors) * media_ptr -> fx_media_bytes_per_sector);

            /* Copy the RAM sector into the destination. */

             _fx_utility_memory_copy(source_buffer,
                media_ptr -> fx_media_driver_buffer, media_ptr -> fx_media_driver_sectors *
                media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_WRITE: {

            /* Calculate the RAM disk sector offset. Note the RAM disk memory
                is pointed to by the fx_media_driver_info pointer, which is supplied
                by the application in the call to fx_media_open. */

            destination_buffer = ((UCHAR *)media_ptr -> fx_media_driver_info) +
                ((media_ptr -> fx_media_driver_logical_sector +
                media_ptr -> fx_media_hidden_sectors) * media_ptr -> fx_media_bytes_per_sector);

            /* Copy the source to the RAM sector. */

            _fx_utility_memory_copy(media_ptr -> fx_media_driver_buffer,
                destination_buffer, media_ptr -> fx_media_driver_sectors *
                media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_FLUSH: {
            /* Return driver success. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_ABORT: {
            /* Return driver success. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_INIT: {

            /* FLASH drivers are responsible for setting several fields
                in the media structure, as follows:
                media_ptr -> fx_media_driver_free_sector_update media_ptr ->
                fx_media_driver_write_protect
                The fx_media_driver_free_sector_update flag is used to instruct
                FileX to inform the driver whenever sectors are not being used.
                This is especially useful for FLASH managers so they don't have
                maintain mapping for sectors no longer in use.
                The fx_media_driver_write_protect flag can be set anytime by
                the driver to indicate the media is not writable. Write attempts
                made when this flag is set are returned as errors. */
            /* Perform basic initialization here... since the boot record is going
                to be read subsequently and again for volume name requests. */
            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

         case FX_DRIVER_UNINIT: {

            /* There is nothing to do in this case for the RAM driver.
                For actual devices some shutdown processing may be necessary. */

            /* Successful driver request. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_BOOT_READ: {
            /* Read the boot record and return to the caller. */

            /* Calculate the RAM disk boot sector offset, which is at the
                very beginning of the RAM disk. Note the RAM disk memory is pointed
                to by the fx_media_driver_info pointer, which is supplied by the
                application in the call to fx_media_open. */

            source_buffer = (UCHAR *)media_ptr -> fx_media_driver_info;

            /* For RAM driver, determine if the boot record is valid. */

            if ((source_buffer[0] != (UCHAR)0xEB) ||

            ((source_buffer[1] != (UCHAR)0x34) &&

            (source_buffer[1] != (UCHAR)0x76)) || /* exFAT jump code. */

            (source_buffer[2] != (UCHAR)0x90)) {

            /* Invalid boot record, return an error! */
            media_ptr -> fx_media_driver_status = FX_MEDIA_INVALID; return; }

            /* For RAM disk only, pickup the bytes per sector. */

            bytes_per_sector =
                _fx_utility_16_unsigned_read(&source_buffer[FX_BYTES_SECTOR]); #ifdef FX_ENABLE_EXFAT

            /* if byte per sector is zero, then treat it as exFAT volume. */

            if (bytes_per_sector == 0 && (source_buffer[1] == (UCHAR)0x76)) {

            /* Pickup the byte per sector shift, and calculate byte per sector. */ 
            bytes_per_sector = (UINT)(1 << source_buffer[FX_EF_BYTE_PER_SECTOR_SHIFT]);

            }

            #endif /* FX_ENABLE_EXFAT */

            /* Ensure this is less than the media memory size. */
            if (bytes_per_sector \media_ptr -> fx_media_memory_size) {

            media_ptr -> fx_media_driver_status = FX_BUFFER_ERROR; break; }

            /* Copy the RAM boot sector into the destination. */

            _fx_utility_memory_copy(source_buffer, media_ptr -> fx_media_driver_buffer, bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_BOOT_WRITE: {

            /* Write the boot record and return to the caller. */

            /* Calculate the RAM disk boot sector offset, which is at the
                very beginning of the RAM disk. Note the RAM disk memory is
                pointed to by the fx_media_driver_info pointer, which is supplied
                by the application in the call to fx_media_open. */ 
            destination_buffer = (UCHAR *)media_ptr -> fx_media_driver_info;

            /* Copy the RAM boot sector into the destination. */

            _fx_utility_memory_copy(media_ptr -> fx_media_driver_buffer,
                destination_buffer, media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        default: {
            /* Invalid driver request. */
            media_ptr -> fx_media_driver_status = FX_IO_ERROR; break;}
    }
}
```
