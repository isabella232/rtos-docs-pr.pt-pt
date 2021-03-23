---
title: Capítulo 3 - Componentes funcionais do Azure RTOS FileX
description: Este capítulo contém uma descrição do sistema de ficheiros incorporado Azure RTOS FileX de alto desempenho de uma perspetiva funcional
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1e1e1a1dbd844d811c7ee3122113f28162639fb4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825532"
---
# <a name="chapter-3---functional-components-of-azure-rtos-filex"></a>Capítulo 3 - Componentes funcionais do Azure RTOS FileX

Este capítulo contém uma descrição do sistema de ficheiros incorporado Azure RTOS FileX de alto desempenho de uma perspetiva funcional.

## <a name="media-description"></a>Descrição dos meios de comunicação

FileX é um sistema de ficheiros incorporado de alto desempenho que está em conformidade com o formato do sistema de ficheiros FAT. FileX vê os meios físicos como uma variedade de sectores lógicos. A forma como estes sectores são mapeados para os meios físicos subjacentes é determinada pelo controlador de I/S ligado ao meio de ficheirox durante a ***chamada fx_media_open.***

### <a name="fat121632-logical-sectors"></a>FAT12/16/32 Sectores Lógicos

A organização exata dos sectores lógicos dos meios de comunicação é determinada pelo conteúdo do registo de arranque dos meios físicos. A disposição geral dos sectores lógicos dos meios de comunicação social é mostrada na Figura 1.

Os sectores lógicos da FileX começam no sector lógico 1, que aponta para o primeiro sector reservado dos meios de comunicação social. Os sectores reservados são opcionais, mas quando em uso normalmente contêm informações do sistema, como o código de arranque.

### <a name="fat121632-media-boot-record"></a>FAT12/16/32 Media Boot Record

A compensação exata do sector das outras áreas na visão do sector lógico dos meios de comunicação é derivada do conteúdo do registo de arranque dos meios de *comunicação social.* A localização do recorde de arranque é tipicamente no sector 0. No entanto, se os meios de comunicação social *tiverem sectores ocultos,* a contrapartida para o sector do arranque deve ser contabilizada (estão localizadas imediatamente ANTES do sector de arranque). O quadro 1 lista os componentes do registo de arranque dos meios de comunicação e os componentes são descritos nos parágrafos.

- **Instruções de salto** O campo *de instruções* de salto é um campo de três bytes que representa uma instrução da máquina Intel x86 para um salto de processador. Este é um campo antigo na maioria das situações.

  ![Vista lógica do sector dos media filex](./media/user-guide/filex-media-logical-sector-view.png)

  **FIGURA 1. Vista lógica do sector dos media filex**

- **Nome OEM** O *campo de nomeSO* está reservado para que os fabricantes coloquem o seu nome ou nome para o dispositivo.
- **Bytes por Setor** Os *bytes por sector* no registo de arranque dos media definem quantos bytes existem em cada sector - o elemento fundamental dos meios de comunicação.
- **Sectores por Cluster** Os *sectores por cluster* no registo de arranque dos meios de comunicação social definem o número de sectores afetados a um cluster. O cluster é o elemento fundamental de atribuição num sistema de ficheiros compatível com a FAT. Todas as informações e subdiretors de ficheiros são atribuídos a partir dos clusters disponíveis dos meios de comunicação, conforme determinado pela Tabela de Atribuição de Ficheiros (FAT).

    **MESA 1. Registo de boot de filex media**
    |Desvio  |Campo  |Número de Bytes|
    |----------|-----------|------------|
    |0x00|Instrução de salto (e9,xx,xx ou eb,xx,90)|3|
    |0x03|Nome OEM|8|
    |0x0B|Bytes por Setor|2|
    |0x0D|Sectores por Cluster|1|
    |0x0E|Número de Sectores Reservados|2|
    |0x10|Número de FATs|1|
    |0x11|Tamanho do Diretório de Raiz|2|
    |0x13|Número de Sectores FAT-12 &amp; FAT-16|2|
    |0x15|Tipo de Suporte|1|
    |0x16|Número de sectores por FAT|2|
    |0x18|Sectores por faixa|2|
    |0x1A|Número de Cabeças|2|
    |0x1C|Número de Sectores Ocultos|4|
    |0x20|Número de Sectores - FAT-32|4|
    |0x24|Sectores por FAT (FAT-32)|4|
    |0x2C|Cluster de Diretório de Raiz|4|
    |0x3E|Código de arranque do sistema|448
    |0x1FE|0x55AA|2|

- **Sectores Reservados** O campo *dos sectores reservados* no registo de arranque dos meios de comunicação social define o número de sectores reservados entre o registo de arranque e o primeiro sector da área FAT. Esta entrada é zero na maioria dos casos.
- **Número de FATs** O *número de FATs* no registo de arranque de mídia define o número de FATs nos meios de comunicação. Deve haver sempre pelo menos uma FAT nos meios de comunicação. As FATs adicionais são meramente cópias duplicadas da FAT primária (primeiro) e são normalmente utilizadas por software de diagnóstico ou recuperação.
- **Tamanho do diretório de raiz** A entrada do *tamanho do diretório* de raiz no registo de arranque de mídia define o número fixo de entradas no diretório de raiz dos meios de comunicação. Este campo não é aplicável às subdireções e ao diretório de raiz FAT-32, uma vez que ambos são atribuídos a partir dos clusters dos meios de comunicação.
- **Número de sectores FAT-12 & FAT-16** O *número de sectores* no sector do registo de arranque dos meios de comunicação social contém o número total de sectores nos meios de comunicação social. Se este campo for zero, então o número total de sectores está contido no número de sectores de campo *FAT-32* localizados mais tarde no registo de arranque.
- **Tipo de Mídia** O campo *do tipo de mídia* é utilizado para identificar o tipo de mídia presente ao controlador do dispositivo. Este é um campo antigo.
- **Sectores por FAT** Os *sectores por FAT arquivados* no registo de arranque dos meios de comunicação social contêm o número de sectores associados a cada FAT na área FAT. O número de sectores fat deve ser suficientemente grande para dar conta do número máximo possível de aglomerados que podem ser afetados nos meios de comunicação social.
- **Sectores por faixa** Os *sectores por campo* de atletismo no registo de arranque dos meios de comunicação social definem o número de sectores por via. Isto é tipicamente apenas pertinente para os meios de comunicação do tipo disco real. Os dispositivos FLASH não usam este mapeamento.
- **Número de Cabeças** O *número de cabeças* no registo de arranque dos meios de comunicação define o número de cabeças nos meios de comunicação social. Isto é tipicamente apenas pertinente para os meios de comunicação do tipo disco real. Os dispositivos FLASH não usam este mapeamento.
- **Sectores Ocultos** O campo *dos sectores ocultos* no registo de arranque dos meios de comunicação define o número de sectores antes do recorde de arranque. Este campo é mantido no FX_MEDIA bloco **de** controlo e deve ser contabilizado nos controladores filex I/O em todos os pedidos de leitura e escrita feitos pelo FileX.
- **Número de Sectores FAT-32** O *número de sectores* no sector do registo de arranque dos meios de comunicação social só é válido se o *número de sectores de* dois bytes for zero. Neste caso, este domínio de quatro bytes contém o número de sectores nos meios de comunicação social.
- **Sectores por FAT (FAT-32)** Os sectores por domínio *FAT (FAT-32)* são válidos apenas no formato FAT-32 e contêm o número de sectores atribuídos para cada FAT dos meios de comunicação social.
- **Cluster de Diretório de Raiz** O campo *de agrupamento de diretórios de raiz* é válido apenas no formato FAT-32 e contém o número inicial do agrupamento de raízes.
- **Código de Arranque do Sistema** O campo *de código de arranque do sistema* é uma área para armazenar uma pequena parte do código de arranque. Na maioria dos dispositivos de hoje, este é um campo legado.
- **0x55AA de assinatura** O campo *de assinatura* é um padrão de dados usado para identificar o registo de arranque. Se este campo não estiver presente, o registo de arranque não é válido.

### <a name="exfat"></a>exFAT

O tamanho máximo do ficheiro em FAT32 é de 4GB, o que limita a adoção alargada de ficheiros multimédia de alta definição. Por predefinição, o FAT32 suporta suportes de armazenamento até 32GB. Com o aumento da capacidade do flash e do cartão SD, o FAT32 torna-se menos eficiente na gestão de grandes volumes. exFAT é projetado para superar estas limitações. exFAT suporta o tamanho do ficheiro até um Exabyte (EB), que é aproximadamente mil milhões de GB. Outra diferença significativa entre o exFAT e o FAT32 é que o exFAT utiliza o bitmap para gerir o espaço disponível no volume, tornando o exFAT mais eficiente na procura de espaço disponível ao escrever dados para o ficheiro. Para ficheiros armazenados em aglomerados contíguos, o exFAT elimina a caminhada pela cadeia FAT para encontrar todos os clusters, tornando-o mais eficiente ao aceder a ficheiros grandes. exFAT é necessário para armazenamento flash e cartões SD maiores que 32GB.

### <a name="exfat-logical-sectors"></a>sectores lógicos exFAT

A disposição geral dos sectores lógicos dos meios de comunicação social no exFAT é ilustrada na Figura 2. No exFAT, o bloco de arranque e a área FAT pertencem à Área do Sistema. O resto dos clusters são Área do Utilizador. Embora não seja necessário, a norma exFAT recomenda que o Bitmap de atribuição esteja no início da Área do Utilizador, seguido da Tabela up-case e do diretório de raiz.

### <a name="exfat-media-boot-record"></a>exFAT Media Boot Record

O conteúdo do Media Boot Record em exFAT é diferente dos da FAT12/16/32. Estão listados na tabela 2. Para evitar confusões, a área entre 0x0B e 0x40, que contém vários parâmetros mediáticos em FAT12/16/32 está marcada como *Reservada* no exFAT. Esta área reservada deve ser programada com zeros, evitando qualquer interpretação errada do Registo de Arranque de Mídia.

![sectores lógicos exFAT](./media/user-guide/exfat-logical-sectors.png)

**FIGURA 2. sectores lógicos exFAT**

- **Instruções de salto** O campo *de instruções* de salto é um campo de três bytes que representa uma instrução da máquina Intel x86 para um salto de processador. Este é um campo antigo na maioria das situações.

    **MESA 2. exFAT Media Boot Record**

    |Desvio  |Campo  |Número de Bytes|
    |----------|-----------|------------|
    |0x00|Instruções de salto|3|
    |0x03|Nome do sistema de ficheiros|8|
    |0x0B|Reservado|53|
    |0x40|Compensação de partição|8|
    |0x48|Comprimento do volume|8|
    |0x50|Compensação de GORDURA|4|
    |0x54|Comprimento fat|4|
    |0x58|Compensação de pilha de cluster|4|
    |0x5C|Contagem de Cluster|4|
    |0x60|Primeiro Cluster de Diretório de Raízes|4|
    |0x64|Número de série de volume|4|
    |0x68|Revisão do sistema de ficheiros|2|
    |0x6A|Bandeiras de volume|2|
    |0x6C|Bytes por turno sectorial|1|
    |0x6D|Mudança de sector por cluster|1|
    |0x6E|Número de FATs|1|
    |0x6F|Seleção de unidade|1|
    |0x70|Por cento em Uso|7|
    |0x71|Reservado|1|
    |0x78|Código de Arranque|390|
    |0x1FE|Assinatura de arranque|2|

- **Nome do sistema de ficheiros** Para o exFAT, o campo *de nome do sistema de ficheiros* deve ser "EXFAT" seguido de três espaços brancos em fuga.
- **Reservado** O conteúdo do campo *reservado* deve ser zero. Esta região sobrepõe-se aos registos de arranque em FAT12/16/32. Fazer esta área zero evita que os sistemas de ficheiros interpretem mal este volume.
- **Compensação de partição** O campo *de compensação* da partição indica o início desta partição.
- **Comprimento do volume** O *campo de comprimento* de volume define a dimensão, em número de sectores, desta partição.
- **Compensação de GORDURA** O campo *de compensação FAT* define o número do sector inicial, relativamente ao início desta partição, da tabela FAT para esta partição.
- **Comprimento fat** O campo *de comprimento FAT* define o tamanho da tabela FAT, em número de sectores.
- **Compensação de pilha de cluster** O campo *de compensação* de pilhas de aglomerado define o número do sector inicial, em relação ao início da partição, da pilha de cluster. A pilha de agrupamento é a área onde as informações dos diretórios e os dados dos ficheiros são armazenados.
- **Contagem de Cluster** O campo de contagem de *clusters* define o número de aglomerados que esta divisória tem.
- **Primeiro Cluster de Diretório de Raízes** O primeiro aglomerado de campo *de diretório* de raiz define a localização inicial do diretório de raiz, que é recomendado para ser logo após o bitmap de atribuição e a tabela de casos.
- **Número de série de volume** O campo *de número de série* de volume define o número de série para esta partição.
- **Revisão do sistema de ficheiros** O campo *de revisão do sistema* de ficheiros define a versão principal e menor do exFAT.
- **Bandeiras de volume** O campo *de bandeiras* de volume contém bandeiras que indicam o estado deste volume.
- **Bytes por turno sectorial** O campo de deslocação de *bytes por sector* define o número de bytes por sector, em log2(n), onde n é o número de bytes por sector. Por exemplo, no cartão SD, o tamanho do sector é de 512 bytes. Portanto, este campo deve ser 9 (log2(512) = 9).
- **Sectores por mudança de cluster** Os *sectores por campo* de mudança de cluster definem o número de sectores num cluster, em log2(n) onde n é o número de sectores por cluster.
- **Número de FATs** O *número de FATs* define o número de tabelas FAT nesta partição. Para o exFAT, recomenda-se que o valor seja 1, para uma tabela FAT.
- **Seleção de unidade** O campo *de seleção* do controlador define o número de unidade INT 13h estendido.
- **Por cento em Uso** A percentagem no campo *de utilização* define a percentagem dos clusters na pilha de aglomerados que está a ser atribuída. Os valores válidos estão entre 0 e 100, inclusive.
- **Reservado** Este campo está reservado para uso futuro.
- **Código de Arranque** O campo *de código de arranque* é uma área para armazenar uma pequena parte do código de arranque. Na maioria dos dispositivos de hoje, este é um campo legado.
- **0x55AA de assinatura** O campo *de assinatura de arranque* é um padrão de dados usado para identificar o registo de arranque. Se este campo não estiver presente, o registo de arranque não é válido.

### <a name="file-allocation-table-fat"></a>Tabela de Atribuição de Ficheiros (FAT)

A *Tabela de Atribuição de Ficheiros (FAT)* começa após os sectores reservados nos meios de comunicação social. A área FAT é basicamente uma matriz de entradas de 12 bits, 16-bits ou 32 bits que determinam se esse cluster é atribuído ou parte de uma cadeia de clusters que inclui um subdiretório ou um ficheiro. O tamanho de cada entrada de FAT é determinado pelo número de aglomerados que precisam de ser representados. Se o número de clusters (derivados do total dos sectores divididos pelos sectores por cluster) for inferior ou igual a 4.086, são utilizadas entradas de 12 bits de FAT. Se o número total de aglomerados for superior a 4.086 e menos de 65.525, são utilizadas entradas de 16 bits de FAT. Caso contrário, se o número total de aglomerados for superior ou igual a 65.525, 32 bits de FAT ou exFAT são utilizados.

Para a FAT12/16/32, o quadro FAT não só mantém a cadeia de clusters, como também fornece informações sobre a atribuição de clusters: se existe ou não um cluster. No exFAT, a informação de atribuição de clusters é mantida por um Diretório Bitmap de atribuição. Cada divisória tem o seu próprio mapa de alocação. O tamanho do bitmap é grande o suficiente para cobrir todos os clusters disponíveis. Se um cluster estiver disponível para alocação, a parte correspondente no bitmap de atribuição é definida para 0. Caso contrário, a broca está definida para 1. Para um ficheiro que ocupa clusters consecutivos, o exFAT não requer uma cadeia FAT para acompanhar todos os clusters. No entanto, para um ficheiro que não ocupe aglomerados consecutivos, uma cadeia FAT ainda precisa de ser mantida.

### <a name="fat-entry-contents"></a>Conteúdo de entrada fat

As duas primeiras entradas na tabela FAT não são utilizadas e normalmente têm o seguinte conteúdo.

|Entrada fat |GORDURA de 12 bits|GORDURA de 16 bits|GORDURA de 32 bits| exFAT|
|----------|-----------|------------|-------|------|
|Entrada 0|0x0F0|0x00F0|0x000000F0|0xF8FFFFFF|
|Entrada 1|0xFFF|0xFFFF|0x0FFFFFFF|0xFFFFFFFF|

A entrada fat número 2 representa o primeiro cluster na área de dados dos meios de comunicação. O conteúdo de cada entrada de cluster determina se é ou não gratuito ou faz parte de uma lista ligada de clusters atribuídos para um ficheiro ou uma subdirectória. Se a entrada do cluster contiver outra entrada de cluster válida, então o cluster é atribuído e o seu valor aponta para o próximo cluster atribuído na cadeia de cluster.

As possíveis entradas de cluster são definidas da seguinte forma.
|Significado|GORDURA de 12 bits|GORDURA de 16 bits|GORDURA de 32 bits| exFAT|
|----------|-----------|------------|-------|------|
|Cluster Gratuito|0x000|0x0000|0x00000000|0x00000000|
|Não usado|0x001|0x0001|0x00000001|0x00000001|
|Reservado|0xFF0-FF6|0xFFF0-FFF6|0x0FFFFFF0-6|ClusterCounter +2 a 0xFFFFFFF6|
|Cluster Mau|0xFF7|0xFFF7|0x0FFFFFF7|0xFFFFFFF7|
|Reservado| - | - | - | 0xFFFFFFF8-E|
|Último Cluster| 0xFF8-FFF| 0xFFF8-FFFF| 0x0FFFFFF8-F| 0xFFFFFFFF|
|Ligação de Cluster| 0x002 0xFEF| 0x0002-FFEF| 0x2 0x0FFFFFEF | 0x2 - ClusterCount + 1|

O último cluster numa cadeia de aglomerados atribuídos contém o valor do Último Cluster (definido acima). O primeiro número de cluster encontra-se no ficheiro ou na entrada do diretório do subdiretório.

### <a name="internal-logical-cache"></a>Cache Lógico Interno

O FileX mantém uma cache do sector lógico *mais recentemente utilizado* para cada meio aberto. O tamanho máximo da cache do sector lógico é definido pela **FX_MAX_SECTOR_CACHE** constante e situa-se em **_fx_api.h_**. Este é o primeiro fator que determina a dimensão da cache do sector lógico interno.

O outro fator que determina o tamanho da cache do sector lógico é a quantidade de memória fornecida à chamada ***fx_media_open** _ pela aplicação. Deve haver memória suficiente para pelo menos um sector lógico. Se forem necessários mais de _ *FX_MAX_SECTOR_CACHE** sectores lógicos, a constante deve ser alterada em **_fx_api.h_** e toda a biblioteca FileX deve ser reconstruída.

> [!IMPORTANT]
> *Cada meio aberto no FileX pode ter um tamanho de cache diferente dependendo da memória fornecida durante a chamada aberta.*

### <a name="write-protect"></a>Escrever Proteger

O FileX fornece ao controlador de aplicações a capacidade de definir dinamicamente a proteção de escrita nos meios de comunicação. Se for necessária proteção contra a escrita, o condutor ajusta-se para FX_TRUE o campo *de fx_media_driver_write_protect* na estrutura FX_MEDIA associada. Quando definidos, todas as tentativas da aplicação de modificar os meios de comunicação são rejeitadas, bem como tentativas de abrir ficheiros para escrita. O controlador também pode desativar a proteção de escrita limpando este campo.

### <a name="free-sector-update"></a>Atualização do Setor Gratuito

O FileX fornece um mecanismo para informar o controlador de aplicações quando os sectores já não estão a ser utilizados. Isto é especialmente útil para gestores de memória FLASH que gerem todos os sectores lógicos que estão sendo usados pelo FileX.

Se for necessária a notificação dos sectores livres, o condutor da aplicação define-se para FX_TRUE o campo *fx_media_driver_free_sector_update* na estrutura FX_MEDIA associada. Esta atribuição é normalmente feita durante a inicialização do condutor.

Definindo este campo, o FileX faz uma **chamada FX_DRIVER_RELEASE_SECTORS** do controlador indicando quando um ou mais sectores consecutivos ficam livres.

### <a name="media-control-block-fx_media"></a>FX_MEDIA do Bloco de Controlo de Meios

As características de cada meio aberto no FileX estão contidas no bloco de controlo dos meios de comunicação. Esta estrutura é definida no ficheiro ***fx_api.h***.

O bloco de controlo dos meios de comunicação pode ser localizado em qualquer lugar da memória, mas é mais comum fazer do bloco de controlo uma estrutura global definindo-o fora do âmbito de qualquer função.

Localizar o bloco de controlo noutras áreas requer um pouco mais de cuidado, assim como toda a memória dinamicamente alocada. Se um bloco de controlo for alocado dentro de uma função C, a memória associada a ele faz parte da pilha do fio de chamada.

> [!WARNING]
>*Em geral, evite usar o armazenamento local para blocos de controlo porque após o retorno da função, todo o seu espaço de pilha variável local é libertado - independentemente de ainda estar em uso!*

## <a name="fat121632-directory-description"></a>**Descrição do diretório FAT12/16/32**

O FileX suporta os formatos de nome 8.3 e Windows Long File Name (LFN). Além do nome, cada entrada de diretório contém os atributos da entrada, a última hora e data modificadas, o índice de cluster inicial e o tamanho dos bytes da entrada. O quadro 3 mostra o conteúdo e o tamanho de uma entrada de diretório FileX 8.3.

- **Nome do diretório**

    O FileX suporta nomes de ficheiros que variam de 1 a 255 caracteres. Os nomes padrão de oito caracteres são representados numa única entrada de diretório nos meios de comunicação. São deixados justificados no campo do nome do diretório e são acolchoados em branco. Além disso, os caracteres ASCII que compõem o nome são sempre maiúsculas.

    Os Nomes de Ficheiros Longos (LFNs) são representados por entradas de diretórios consecutivos, em ordem inversa, seguidas imediatamente por um nome de ficheiro padrão 8.3. O nome 8.3 criado contém todas as informações significativas do diretório associadas ao nome. O quadro 4 mostra o conteúdo das entradas de diretório utilizadas para conter as informações sobre o Nome de Ficheiros Longos, e o Quadro 5 mostra um exemplo de um LFN de 39 caracteres que requer um total de quatro entradas de diretório.

> [!IMPORTANT]
> *O **FX_MAX_LONG_NAME_LEN** constante , definido em **fx_api.h**, contém o comprimento máximo suportado pelo FileX.*

- **Extensão do nome de arquivo do diretório**

    Para nomes de ficheiros padrão 8.3, o FileX também suporta a *extensão* opcional do nome de ficheiro de três caracteres . Tal como o nome do ficheiro de oito caracteres, as extensões de nome de ficheiro são deixadas justificadas no campo de extensão do nome de ficheiros do diretório, acolchoados em branco e sempre maiúsculas.

    **MESA 3. Entrada no diretório FileX 8.3**

    |Desvio|Campo|Número de Bytes|
    |------------|-----------|------------|
    |0x00|Nome de entrada do diretório|8|
    |0x08|Extensão do Diretório|3|
    |0x0B|Atributos|1|
    |0x0C|NT (introduzido pelo formato de nome de ficheiro longo e reservado para NT [sempre 0])|1|
    |0x0D|Tempo criado em milissegundos (introduzido pelo formato de nome de ficheiro longo e representa o número de milissegundos quando o ficheiro foi criado.)|1|
    |0x0E|Tempo criado em &amp; minutos (introduzido pelo formato de nome de ficheiro longo e representa a hora e minuto em que o ficheiro foi criado)|2|
    |0x10|Data Criada (introduzida pelo formato de nome de ficheiro longo e representa a data em que o ficheiro foi criado.)|2|
    |0x12|Última Data Acedida (introduzida pelo formato de nome de ficheiro longo e representa a data em que o ficheiro foi acedido pela última vez.)|2|
    |0x14|Cluster inicial (apenas 16 bits superiores FAT-32)|2|
    |0x16|Tempo modificado|2|
    |0x18|Data de Modificação|2|
    |0x1A|Cluster inicial (16 bits inferiores FAT-32 ou FAT-12 ou FAT-16)|2|
    |0x1C|Tamanho do Ficheiro|4|


- **Atributos do diretório**

    A entrada de campo *de atributos* de um byte contém uma série de bits que especificam várias propriedades da entrada do diretório. As definições de atributos do diretório são as seguintes:

    |Atributo Bit|Significado|
    |------------|-----------|
    |0x01|A entrada é só para leitura.|
    |0x02|A entrada está escondida.|
    |0x04|A entrada é uma entrada no sistema.|
    |0x08|A entrada é uma etiqueta de volume|
    |0x10|A entrada é um diretório.|
    |0x20|A entrada foi modificada.|

    Como todos os bits de atributos são mutuamente exclusivos, pode haver mais do que um atributo definido de cada vez.

- **Hora do Diretório**

    O campo de *tempo* de dois bytes contém as horas, minutos e segundos da última alteração à entrada de diretório especificado. Os pedaços 15 a 11 contêm as horas, os pedaços 10 embora 5 contenham os minutos, e os bits 4 embora 0 contenham os segundos. Os segundos reais são divididos por dois antes de serem escritos neste campo.

- **Data do Diretório**

    O campo de *datas* de dois byte contém o ano (compensado a partir de 1980), mês e dia da última alteração à entrada de diretório especificado. Os bits 15 a 9 contêm o desfasamento do ano, os bits 8 a 5 contêm o mês de compensação, e os bits 4 a 0 contêm o dia.

- **Agrupamento de partidas do Diretório**

    Este campo ocupa 2 bytes para FAT-12 e FAT-16. Para a FAT-32 este campo ocupa 4 bytes. Este campo contém o primeiro número de cluster atribuído à entrada (subdiretório ou ficheiro).

    > [!NOTE]
    > *Note que o FileX cria novos ficheiros sem um cluster inicial (campo de cluster inicial igual a zero) para permitir que os utilizadores atribuam opcionalmente um número contíguo de clusters para um ficheiro recém-criado. *

- **Tamanho do arquivo do diretório**

    O campo de tamanho *de* ficheiro de *quatro* bytes contém o número de bytes no ficheiro. Se a entrada for realmente uma subdireção, o campo de tamanho é zero.

### <a name="long-file-name-directory"></a>Diretório de Nome de Arquivo Longo

- **Ordinal**

    O campo *ordinal* de um byte que especifica o número da entrada LFN. Uma vez que as entradas LFN são posicionadas em ordem inversa, os valores ordinais das entradas de diretório LFN que incluem uma única diminuição de LFN por um. Além disso, o valor ordinal do LFN imediatamente antes do nome do ficheiro 8.3 deve ser um.

    **MESA 4. Entrada de diretório de nome de arquivo longo**

    |Desvio|Campo|Número de Bytes|
    |------------|-----------|------------|
    0x00|Campo Ordinal|1|
    0x01|Personagem Unicode 1|2|
    0x03|Personagem Unicode 2|2|
    0x05|Personagem Unicode 3|2|
    0x07|Personagem Unicode 4|2|
    0x09|Personagem Unicode 5|2|
    0x0B|Atributos LFN|1|
    0x0C|Tipo LFN (Reservado sempre 0)|1|
    0x0D|LFN Checksum|1|
    0x0E|Personagem Unicode 6|2|
    0x10|Personagem Unicode 7|2|
    0x12|Personagem Unicode 8|2|
    0x14|Personagem Unicode 9|2|
    0x16|Personagem Unicode 10|2|
    0x18|Personagem Unicode 11|2|
    0x1A|Cluster LFN (sempre não uused 0)|2|
    0x1C|Personagem Unicode 12|2|
    0x1E|Personagem unicódigo |13|2|

- **Personagem unicódigo**

    Os campos *unicode character* de dois bytes são projetados para apoiar caracteres de muitas línguas diferentes. Os caracteres ASCII padrão são representados com o carácter ASCII armazenado no primeiro byte do personagem Unicode seguido por um personagem espacial.

- **Atributos LFN**

    O campo *atributos LFN de* um byte contém atributos que identificam a entrada do diretório como uma entrada de diretório LFN. Isto é conseguido tendo os atributos apenas de leitura, sistema, oculto e volume todos definidos.

- **Tipo LFN**

    O campo *LFN Type* de um byte está reservado e é sempre 0.

- **LFN Checksum**

    O campo *de verificação LFN de* um byte representa uma parte de verificação dos 11 caracteres do nome de ficheiro MSDOS 8.3 associado. Esta caixa de verificação é armazenada em cada entrada LFN para ajudar a garantir que a entrada LFN corresponde ao nome de ficheiro 8.3 apropriado.

- **LFN Cluster**

    O campo de *cluster LFN* de dois bytes não é uused e é sempre 0.

    **MESA 5. Entradas de diretório Composta por um LFN de 39 caracteres**

    |Entrada|Significado|
    |------------|-----------|
    |1|Entrada LFN Diretório 3|
    |2|Entrada LFN Diretório 2|
    |3|Entrada LFN Diretório 1|
    |4|8.3 Entrada de Diretório (ttttt~n.xx)|

### <a name="exfat-directory-description"></a>descrição do diretório exFAT

exFAT sistema de ficheiros armazena entrada e nome de arquivo de forma diferente. A entrada no diretório contém os atributos da entrada, vários timetamps sobre quando a entrada foi criada, modificada e acedida. Outras informações, tais como o tamanho do ficheiro e o cluster inicial, são armazenadas na Entrada do Diretório de Extensão de Fluxo, que segue imediatamente a entrada do diretório primário. exFAT suporta apenas o formato de nome de ficheiro longo (LFN). que é armazenado no Diretório de Nome de Ficheiros Imediatamente segue a Entrada do Diretório de Extensão de Fluxo, como mostrado no quadro 2.

### <a name="exfat-file-directory-entry"></a>entrada de diretório de ficheiros exFAT

Uma descrição da entrada de diretório de ficheiros exFAT e do seu conteúdo está incluída na tabela e parágrafos seguintes.

- **Tipo de Entrada**

    O campo tipo de entrada indica o tipo desta entrada. Para a entrada do Diretório de Ficheiros, este campo deve ser 0x85.

- **Contagem de entrada secundária**

    O campo *de contagem de entradas secundárias* indica que o número de entradas secundárias segue imediatamente esta entrada primária. As entradas secundárias associadas à entrada do diretório de ficheiros incluem uma entrada de diretório de extensão de fluxo e uma ou mais entradas de diretório de nome de ficheiro.

    **MESA 6. entrada de diretório de ficheiros exFAT**

    |Desvio|Campo|Número de Bytes|
    |----|-----------|-|
    |0x00|Tipo de Entrada|1|
    |0x01|Entrada Secundária|1|
    |0x02|Soma de verificação|2|
    |0x04|Atributos do Ficheiro|2|
    |0x06|Reservado 1|2|
    |0x08|Criar Carimbo de Data/Hora|4|
    |0x0C|Última hora modificada|4|
    |0x10|Última hora de acesso|4|
    |0x14|Criar Incremento de 10ms|1|
    |0x15|Último Incremento modificado de 10ms|1|
    |0x16|Criar offset UTC|1|
    |0x17|Última compensação modificada da UTC|1|
    |0x18|Última compensação utc de acesso|1|
    |0x19|Reservado 2|7|

- **Checkum**

    O campo *checkum* contém o valor da função de verificação sobre todas as entradas no conjunto de entrada de diretório (a entrada do diretório de ficheiros e as suas entradas secundárias).

- **Atributos do Ficheiro**

    A entrada de campo de atributos one-byte contém uma série de bits que especificam várias propriedades da entrada do diretório. A definição da maioria dos atributos é idêntica à FAT 12/16/32. As definições de atributos do diretório são as seguintes:

    |Atributo Bit|Significado|
    |------------|-----------|
    |0x01| A entrada é apenas de leitura|
    |0x02|A entrada está escondida|
    |0x04|A entrada é uma entrada do sistema|
    |0x08|A entrada está reservada|
    |0x10|A entrada é um diretório|
    |0x20|A entrada foi modificada|
    |Todos os outros pedaços|Reservado|

- **Reservado1**

    Este campo deve ser zero.

- **Criar Carimbo de Data/Hora**

    O campo *de tempotamping* de criação, combinando informações a partir do campo *Incremento de 10ms,* descreve a data e hora locais que o ficheiro ou o diretório foram criados.

- **Última hora modificada**

    O último campo de *tempos modificado,* combinando informações do último campo *de incremento de 10ms modificado,* descreve a data local e a hora em que o ficheiro ou o diretório foram modificados pela última vez. Veja as notas abaixo sobre os tempos.

- **Última hora de acesso**

    O último campo *de tempos acedido* descreve a data e a hora locais em que o ficheiro ou o diretório foi acedido pela última vez. Veja as notas abaixo sobre os tempos.

- **Criar Incremento de 10ms**

    O campo *de incremento de 10ms* criar, combinando informações do campo *de tempotamp de criação,* descreve a data e a hora locais que o ficheiro ou o diretório foram criados. Veja as notas abaixo sobre os tempos.

- **Último Incremento modificado de 10ms**

    O último campo *de incremento modificado de 10ms,* combinando informações do último campo de *tempotampido modificado,* descreve a data local e a hora em que o ficheiro ou o diretório foi modificado pela última vez. Veja as notas abaixo sobre os tempos.

- **Criar offset UTC**

    O campo *de compensação da UTC de criação* descreve a diferença entre a hora local e a hora UTC, quando o ficheiro ou o diretório foram criados. Veja as notas abaixo sobre os tempos.

- **Última compensação modificada da UTC**

    O último campo *de compensação modificado da UTC* descreve a diferença entre a hora local e a hora UTC, quando o ficheiro ou o diretório foi modificado pela última vez. Veja as notas abaixo sobre os tempos.

- **Última compensação UTC acedida**

    O último campo *de compensação da UTC acessado* descreve a diferença entre a hora local e a hora UTC, quando o ficheiro ou o diretório foi acedido pela última vez. Veja as notas abaixo sobre os tempos.

- **Reservado2**

    Este campo deve ser zero.

### <a name="notes-on-timestamps"></a>Notas sobre os timestamps

- **Entrada de tempotampia** Os campos de tempotampadas são interpretados da seguinte forma:

- **Campos incrementais de 10ms** O valor no campo de incremento de 10ms proporciona uma granularidade mais fina ao valor do timetamp. Os valores válidos são entre 0 (0ms) e 199 (1990ms).

     ![Campos incrementais de 10ms](./media/user-guide/10ms-increment-fields.png)

- **Campo de compensação UTC**

     ![Campo de compensação UTC](./media/user-guide/utc-offset-field.png)

- **Valor de Compensação**

    O número inteiro assinado de 7 bits representa compensado do tempo UTC, em incrementos de 15 minutos.

- **Válido**

    Se o valor no campo de compensação é ou não válido. 0 indica que o valor no campo de valor de compensação é inválido. 1 indica que o valor é válido.

### <a name="stream-extension-directory-entry"></a>Entrada no diretório de extensão de fluxo

Uma descrição do Diretório de Extensão de Fluxo e o seu conteúdo está incluído na tabela seguinte.

**MESA 7. Entrada no diretório de extensão de fluxo**

|Desvio|Campo| Número de Bytes|
|------------|-----------|-------|
|0x00|Tipo de Entrada|1|
|0x01|Sinalizadores|1|
|0x02|Reservado 1|1|
|0x03|Comprimento do nome|1|
|0x04|Nome Hash|2|
|0x06|Reservado 2|2|
|0x08|Comprimento de dados válido|8|
|0x10|Reservado 3|4|
|0x14|Primeiro Cluster|4|
|0x18|Comprimento dos dados|8|

- **Tipo de Entrada**

    O campo *tipo de entrada* indica o tipo desta entrada. Para a extensão de streaming Entrada do Diretório, este campo deve ser 0xC0.

- **Sinalizadores**

    Este campo contém uma série de bits que especificam várias propriedades:
    |Bit de bandeira|Significado    |
    |-----------------|-----------|
    |0x01            |Este campo indica se a atribuição ou não de clusters é possível. Este campo deve ser 1.|
    |0x02            |Este campo indica se os aglomerados associados são ou não contíguos. Um valor 0 significa que a entrada FAT é válida e o FileX seguirá a cadeia FAT. Um valor 1 significa que a entrada FAT é inválida e os clusters são contíguos.|
    |Todos os outros pedaços    |Reservado|

- **Reservado 1**

    Este campo deve ser 0.

- **Comprimento do nome**

    O campo *de comprimento* do nome contém o comprimento da cadeia unicode nas entradas de diretório de nome de ficheiros que contêm colectivamente. As entradas de diretório de nome de ficheiro seguirão imediatamente esta entrada de diretório de extensão de fluxo.

- **Nome Hash**

    O *campo de haxixe* de nome é uma entrada de 2 bytes, contendo o valor hash do nome do ficheiro em cima. O valor do hash permite uma procura mais rápida de nome de ficheiro/diretório: se os valores do hash não corresponderem, o nome do ficheiro associado a esta entrada não é compatível.

- **Reservado 2**

    Este campo deve ser 0.

- **Comprimento de dados válido**

    O campo de comprimento de *dados válido* indica a quantidade de dados válidos no ficheiro.

- **Reservado 3**

    Este arquivo deve ser 0.

- **Primeiro Cluster**

    O primeiro campo *de cluster* contém índice do primeiro aglomerado do fluxo de dados.

- **Comprimento dos dados**

    O campo de comprimento de *dados* contém o número total de bytes nos clusters atribuídos. Este valor pode ser maior do que *o Comprimento de Dados Válido,* uma vez que o exFAT permite a pré-alocação de conjuntos de dados.

### <a name="root-directory"></a>Diretório de raiz

Nos formatos FAT 12 e 16-bits, o *diretório de raiz* está localizado imediatamente após todos os sectores FAT nos meios de comunicação e pode ser localizado examinando o ***fx_media_root_sector_start** _ em um bloco de controlo de *_ FX_MEDIA** aberto. O tamanho do diretório de raiz, em termos de número de entradas de diretório (cada 32 bytes de tamanho), é determinado pela correspondente entrada no registo de arranque do meio de comunicação.

O diretório de raiz em FAT-32 e exFAT pode ser localizado em qualquer lugar nos clusters disponíveis. A sua localização e tamanho são determinados a partir do registo de arranque quando o meio de comunicação é aberto. Após a abertura do meio de comunicação, o campo ***fx_media_root_sector_start*** pode ser utilizado para encontrar o cluster inicial do diretório raiz FAT-32 ou exFAT.

### <a name="subdirectories"></a>Subdirelídias

Há várias subdiretivas num sistema FAT. O nome do subdiretório reside numa entrada de diretório como um nome de ficheiro. No entanto, a especificação de atributos do diretório (0x10) está definida para indicar que a entrada é um subdiretório e o tamanho do ficheiro é sempre zero.
A figura 3 mostra como é uma estrutura subdiretória típica para um novo subdiretório singlecluster chamado ***SAMPLE. DIR** _ com um ficheiro chamado _*_FILE.TXT_**.
Na maioria das formas, as subdiretórios são muito semelhantes às entradas de ficheiros. O primeiro campo de cluster aponta para o primeiro aglomerado de uma lista ligada de aglomerados. Quando um subdiretório é criado, as duas primeiras entradas de diretório contêm diretórios predefinidos, nomeadamente o diretório "." e o diretório "." O diretório "." aponta para o próprio subdiretório, enquanto o diretório "."aponta para o diretório anterior ou para o diretório dos pais.

### <a name="global-default-path"></a>Caminho Padrão Global

O FileX fornece um caminho padrão global para os meios de comunicação. O caminho predefinido é utilizado em qualquer serviço de ficheiros ou diretórios que não especifique explicitamente um caminho completo.

Inicialmente, o diretório global de incumprimento está definido para o diretório de raiz dos meios de comunicação. Isto pode ser alterado pela aplicação chamando ***fx_directory_default_set***.

O atual caminho padrão para os meios de comunicação pode ser examinado chamando ***fx_directory_default_get** _. Esta rotina fornece um ponteiro de cordas para a cadeia de caminho padrão mantida dentro do bloco de controlo _ *FX_MEDIA**.

### <a name="local-default-path"></a>Caminho padrão local

O FileX também fornece um caminho padrão específico que permite que diferentes fios tenham caminhos únicos sem conflitos. A estrutura **FX_LOCAL_PATH** é fornecida pela aplicação durante as chamadas para **_fx_directory_local_path_set_*_ e _*_fx_directory_local_path_restore_** modificar o caminho local para o fio de chamada.

Se um caminho local estiver presente, o caminho local tem precedência sobre o caminho global dos meios de comunicação padrão. Se o caminho local não for configurado ou se for limpo com o serviço ***fx_directory_local_path_clear,*** o caminho padrão global dos meios de comunicação é novamente usado.

## <a name="file-description"></a>Descrição do arquivo

O FileX suporta nomes de caracteres padrão 8.3 e longos ficheiros com extensões de três caracteres. Além do nome ASCII, cada entrada de ficheiro contém os atributos da entrada, a última hora e data modificadas, o índice de cluster inicial e o tamanho dos bytes da entrada.

### <a name="file-allocation"></a>Atribuição de ficheiros

O FileX suporta o esquema padrão de atribuição de clusters do formato FAT. Além disso, o FileX suporta a atribuição pré-cluster de clusters contíguos. Para acomodar isto, cada ficheiro FileX é criado sem aglomerados atribuídos. Os agrupamentos são atribuídos em pedidos de escrita subsequentes ou em ***fx_file_allocate*** pedidos de pré-atribuição de agrupamentos contíguos.

A figura 4, "FileX FAT-16 File Example", mostra um ficheiro nomeado ***FILE.TXT*** com dois clusters sequenciais atribuídos a partir do cluster 101, um tamanho de 26, e o alfabeto como os dados no primeiro grupo de dados número 101 do ficheiro.

### <a name="file-access"></a>Acesso a ficheiros

Um ficheiro FileX pode ser aberto várias vezes simultaneamente para acesso de leitura. No entanto, um ficheiro só pode ser aberto uma vez para escrita. As informações utilizadas para apoiar o acesso ao ficheiro estão contidas no ***FX_FILE*** bloco de controlo de ficheiros.

> [!NOTE]
> *Note que o controlador de mídia pode definir dinamicamente a proteção de escrita. Se isso acontecer, todos os pedidos de escrita são rejeitados, bem como tentativas de abrir um ficheiro para escrita.*

### <a name="file-layout-in-exfat"></a>Layout de arquivo em exFAT

A conceção do exFAT não requer que a cadeia FAT seja mantida para um ficheiro se os dados forem armazenados em aglomerados contagiosos. A *bit NoFATChain* no Diretório de Extensão de Fluxo indica se a cadeia FAT deve ou não ser utilizada ao ler dados do ficheiro. Se o *NoFATChain* estiver definido, o FileX lê sequencialmente a partir do cluster indicado no campo *Primeiro Cluster* na Entrada do Diretório de Extensão de Fluxo.

Por outro lado, se o *NoFATChain* estiver livre, o FileX seguirá a cadeia FAT para atravessar todo o ficheiro, semelhante à cadeia FAT em FAT12/16/32.

A figura 3 mostra dois ficheiros de amostra, um não requer cadeia DE GORDURA, e o outro requer uma corrente FAT.

## <a name="system-information"></a>Informações do Sistema

As informações do sistema FileX consistem em acompanhar as instâncias de mídia aberta e manter a hora e a data do sistema globais.

![Arquivo com Clusters Contíguos vs. Arquivo que requer ligação FAT](./media/user-guide/system-information.png)

**FIGURA 3. Arquivo com Clusters Contíguos vs. Arquivo que requer ligação FAT**

Por predefinição, a data e hora do sistema estão definidas para a última data de lançamento do FileX. Para ter uma data e hora precisas do sistema, a aplicação deve ligar ***fx_system_time_set** _ e _ *_fx_system_date_set_** durante a inicialização.

### <a name="system-date"></a>Data do Sistema

A data do sistema FileX é mantida na variável ***global _fx_system_date.*** Os bits 15 a 9 contêm o ano de compensação de 1980, os bits 8 a 5 contêm o mês de compensação, e os bits 4 a 0 contêm o dia. |

### <a name="system-time"></a>Tempo do sistema

O tempo do sistema FileX é mantido na variável ***global _fx_system_time.*** Os pedaços 15 a 11 contêm as horas, os pedaços 10 embora 5 contenham os minutos, e os bits 4 embora 0 contenham os segundos.

### <a name="periodic-time-update"></a>Atualização periódica do tempo

Durante a inicialização do sistema, o FileX cria um temporizador de aplicação ThreadX para atualizar periodicamente a data e hora do sistema. A taxa a que a data e a atualização do sistema são determinadas por duas constantes utilizadas pela função ***_fx_system_initialize.***

As constantes **FX_UPDATE_RATE_IN_SECONDS** e **FX_UPDATE_RATE_IN_TICKS** representam o mesmo período de tempo. O **FX_UPDATE_RATE_IN_TICKS** constante é o número de carraças do temporizador ThreadX que representam o número de segundos especificados pela **FX_UPDATE_RATE_IN_SECONDS** constante . A **constante FX_UPDATE_RATE_IN_SECONDS** especifica quantos segundos entre cada atualização de tempo do FileX. Portanto, o tempo interno do FileX aumenta em intervalos de **FX_UPDATE_RATE_IN_SECONDS**. Estas constantes podem ser fornecidas durante a compilação de **_fx_system_initialize_*_, ou o desenvolvedor pode modificar os predefinidos encontrados no* ficheiro _ _fx_port.h_** da versão FileX.

O temporizador periódico FileX é utilizado apenas para atualizar a data e hora do sistema global, que é utilizado exclusivamente para a estampagem de tempo de ficheiro. Se não for necessária a marcação temporal, basta definir **FX_NO_TIMER** ao compilar **_fx_system_initialize.c_** eliminar a criação do temporizador periódico FileX.

![Exemplo de arquivo FILEX FAT-16](./media/user-guide/fat-16-file-example.png)

**FIGURA 4. Exemplo de arquivo FILEX FAT-16**
