---
title: Capítulo 6 - Módulo tolerante a falhas Azure RTOS FileX
description: Este capítulo contém uma descrição do Módulo Tolerante a Falhas de Falhas Azure RTOS FileX que foi concebido para manter a integridade do sistema de ficheiros se os meios de comunicação perderem energia ou forem ejetados no meio de uma operação de escrita de ficheiros.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 66bffa2dbf52bc458bfaf124aa006a79e810100ac2e926c17444daf090519e66
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783753"
---
# <a name="chapter-6---azure-rtos-filex-fault-tolerant-module"></a>Capítulo 6 - Módulo tolerante a falhas Azure RTOS FileX

Este capítulo contém uma descrição do Módulo Tolerante a Falhas de Falhas Azure RTOS FileX que foi concebido para manter a integridade do sistema de ficheiros se os meios de comunicação perderem energia ou forem ejetados no meio de uma operação de escrita de ficheiros.

## <a name="filex-fault-tolerant-module-overview"></a>Visão geral do módulo tolerante com falhas de filex

Quando uma aplicação escreve dados num ficheiro, o FileX atualiza os clusters de dados e as informações do sistema. Estas atualizações devem ser concluídas como uma operação atómica para manter a informação no sistema de ficheiros coerente. Por exemplo, ao anexar dados a um ficheiro, o FileX precisa de encontrar um cluster disponível nos meios de comunicação, atualizar a cadeia FAT, atualizar o comprimento arquivado na entrada do diretório e, possivelmente, atualizar o número de agrupamento inicial na entrada do diretório. Uma falha de energia ou uma ejeção mediática podem interromper a sequência de atualizações, o que deixará o sistema de ficheiros num estado inconsistente. Se o estado inconsistente não for corrigido, os dados que estão a ser atualizados podem ser perdidos e, devido a danos nas informações do sistema, a operação subsequente do sistema de ficheiros pode danificar outros ficheiros ou diretórios nos meios de comunicação.

O Módulo Tolerante a Falhas FileX funciona através de etapas de diário necessárias para atualizar um ficheiro *antes* de estes passos serem aplicados no sistema de ficheiros. Se a atualização do ficheiro for bem sucedida, estas entradas de registo serão removidas. No entanto, se a atualização do ficheiro for interrompida, as entradas de registo são armazenadas no meio de comunicação. Da próxima vez que o suporte é montado, o FileX deteta estas entradas de registo da operação de escrita anterior (inacabada). Nesses casos, o FileX pode recuperar de uma falha, revendo as alterações já efetuadas no sistema de ficheiros, quer recandidatando as alterações necessárias para completar a operação anterior. Desta forma, o Módulo Tolerante a Falhas FileX mantém a integridade do sistema de ficheiros se os meios de comunicação perderem energia durante uma operação de atualização.

> [!IMPORTANT]
> *O Módulo Tolerante com Falhas FileX não foi concebido para prevenir a corrupção do sistema de ficheiros causada por corrupção física dos meios de comunicação com dados válidos no mesmo.*

> [!IMPORTANT]
> *Depois de o módulo tolerante a falhas FileX proteger um suporte, os meios de comunicação não devem ser montados por outra coisa que não o FileX com o Tolerante de Falha ativado. Ao fazê-lo, as entradas de registo no sistema de ficheiros são inconsistentes com as informações do sistema nos meios de comunicação. Se o módulo tolerante a falhas FileX tentar processar as entradas de registo após a atualização do sistema de ficheiros por outro sistema de ficheiros, o procedimento de recuperação poderá falhar, deixando todo o sistema de ficheiros num estado imprevisível.*

## <a name="use-of-the-fault-tolerant-module"></a>Utilização do Módulo Tolerante a Falhas

A função FileX Fault Tolerant está disponível para todos os sistemas de ficheiros FAT suportados pelo FileX, incluindo FAT12, FAT16, FAT32 e exFAT. Para ativar a função tolerante a falhas, o FileX deve ser construído com o símbolo **FX_ENABLE_FAULT_TOLERANT** definido. Na hora de execução, a aplicação inicia o serviço tolerante a falhas, ligando **_para fx_fault_tolerant_enable_*_ imediatamente após a chamada para _*_fx_media_open_**. Após a ativação do tolerante a falhas, todas as operações de escrita de ficheiros para os meios designados estão protegidas. Por predefinição, o módulo tolerante a falhas não está ativado.

> [!IMPORTANT]
> *A aplicação tem de se certificar de que o sistema de ficheiros não está a ser acedido antes de ***fx_fault_tolerant_enable** _ ser chamado. Se a aplicação escrever dados para o sistema de ficheiros antes de permitir a ativação tolerante a falhas, a operação de escrita poderá corromper os meios de comunicação se as operações de escrita prévia não forem concluídas e o sistema de ficheiros não tiver sido restaurado utilizando registo tolerante a falhas entries._

## <a name="filex-fault-tolerant-module-log"></a>Registo do módulo tolerante com falhas de FicheiroX

O registo tolerante a falhas filex ocupa um aglomerado lógico em flash. O índice para o número inicial do cluster desse cluster é registado no sector das arranques dos meios de comunicação social, com uma compensação especificada pelo símbolo **FX_FAULT_TOLERANT_BOOT_INDEX**. Por predefinição, este símbolo é definido como sendo 116. Esta localização é escolhida porque está marcada como reservada na especificação FAT12/ 16/32 e exFAT.

A figura 5, "Log Structure Layout", mostra o layout geral da estrutura do tronco. A estrutura de registo contém três secções: Cabeçalho de Registo, Corrente FAT e Entradas de Registo.

> [!IMPORTANT]
> *Todos os valores de vários bytes armazenados nas entradas de registo estão no formato Little Endian.*

![Layout da estrutura de registo](./media/user-guide/log-structure-layout.png)

**Figura 5. Layout da estrutura de registo**

A área do cabeçalho de registo contém informações que descrevem toda a estrutura do registo e explica cada campo em detalhe.

**MESA 8. Área do cabeçalho de registo**

|Campo|Tamanho (in bytes)|Description|
|-----|--------------|-----------|
|ID|4|Identifica uma estrutura de registo tolerante a falha de FicheiroX. A estrutura de registo é considerada inválida se o valor de ID não for 0x46544C52.|
|Tamanho total|2|Indica o tamanho total (em bytes) de toda a estrutura de log.|
|Checkum de cabeçalho|2|Checksum que converte a área do cabeçalho de registo. A estrutura de registo é considerada inválida se os campos do cabeçalho falharem na verificação da conta.|
|Número da Versão|2|Números de versão tolerantes a falhas filex e menores.|
|Reservado|2|Para a expansão futura.|

A área do cabeçalho de log é seguida pela área de log de corrente FAT. A figura 9 contém informações que descrevem como a cadeia FAT deve ser modificada. Esta área de registo contém informações sobre os clusters que estão a ser atribuídos a um ficheiro, os clusters a serem removidos de um ficheiro, e onde deve ser a inserção/eliminação e descreve cada campo na área do Registo de Corrente FAT.

**MESA 9. Área de log de cadeia de gordura**

|Campo|Tamanho (in bytes)|Description|
|-----|--------------|-----------|
|Cheques de registo de cadeia de gordura|2|Checkum de toda a área de log de corrente fat. A área de Log de corrente FAT é considerada inválida se falhar na verificação da parte de verificação.|
|Sinalizador|1|Os valores de bandeira válidos são:<br/>cadeia fat 0x01 válida<br />0x02 BITMAP está a ser usado|
|Reservado|1|Reservado para uso futuro|
|Ponto de inserção – Frente|4|O cluster (que pertence à cadeia fat original) onde a cadeia recém-criada vai ser anexada.|
|Aglomerado de cabeça da nova cadeia fat|4|O primeiro aglomerado da recém-criada Cadeia FAT|
|Aglomerado de cabeça da cadeia de gordura original|4|O primeiro aglomerado da parte da cadeia fat original que deve ser removido.|
|Ponto de inserção – Volta|4|O cluster original onde a recém-criada cadeia FAT se junta.|
|Próximo ponto de eliminação|4|Este campo ajuda o procedimento de limpeza da cadeia FAT.|

A Área de Entradas de Registo contém entradas de registo que descrevem as alterações necessárias para recuperar de uma falha. Existem três tipos de entrada de registo suportados no módulo tolerante a falhas FileX: ENTRADA DE Registo DE GORDURA; Entrada de Registo de Diretório; e Entrada de Registo bitmap.

As três figuras e três tabelas seguintes descrevem estas entradas de registo em detalhe.

![Entrada de registo fat](./media/user-guide/fat-log-entry.png)

**Figura 6. Entrada de registo fat**

**MESA 10. Entrada de registo fat**

|Campo|Tamanho (in bytes)|Descrição|
|-----|--------------|-----------|
Tipo|2|Tipo de Entrada, deve ser FX_FAULT_TOLERANT_FAT_LOG_TYPE|
|Tamanho|2|Tamanho desta entrada|
|Número de cluster|4|Número de cluster|
|Valor|4|Valor a ser escrito na entrada FAT|

![Entrada de registo de diretório](./media/user-guide/directory-log-entry.png)

**Figura 7. Entrada de registo de diretório**

**MESA 11. Entrada de registo de diretório**

|Campo|Tamanho (in bytes)|Descrição|
|-----|--------------|-----------|
|Tipo|2|Tipo de Entrada, deve ser FX_FAULT_TOLERANT_DIRECTORY_LOG_TYPE|
|Tamanho|2|Tamanho desta entrada|
|Compensação do Sector|4|Offset (in bytes) no sector onde este diretório está localizado.|
|Setor de Registos|4|O sector onde se situa a entrada no diretório|
|Dados de Registo|Variável|Conteúdo da entrada no diretório|

![Entrada de registo bitmap](./media/user-guide/bitmap-log-entry.png)

**Figura 8. Entrada de registo bitmap**

**MESA 12. Entrada de registo bitmap**

|Campo|Tamanho (in bytes)|Descrição|
|-----|--------------|-----------|
|Tipo|2|Tipo de Entrada, deve ser FX_FAULT_TOLERANT_BITMAP_LOG_TYPE|
|Tamanho|2|Tamanho desta entrada|
|Número de cluster|4|Número de cluster|
|Valor|4|Valor a ser escrito na entrada FAT|

## <a name="fault-tolerant-protection"></a>Proteção tolerante a falhas

Após o início do Módulo Tolerante a Falhas FileX, procura pela primeira vez um ficheiro de registo tolerante a falhas existente nos meios de comunicação. Se não for possível encontrar um ficheiro de registo válido, o FileX considera os meios de comunicação desprotegidos. Neste caso, o FileX criará um ficheiro de registo tolerante a falhas nos meios de comunicação.

> [!IMPORTANT]
> *O FileX não é capaz de proteger um sistema de ficheiros se foi corrompido antes do módulo tolerante de falha FileX começar. *

Se estiver localizado um ficheiro de registo tolerante a falhas, o FileX verifica as entradas de registo existentes. Um ficheiro de registo sem entrada de registo indica que a operação de ficheiro prévia foi bem sucedida e todas as entradas de registo foram removidas. Neste caso, a aplicação pode começar a utilizar o sistema de ficheiros com proteção tolerante a falhas.

No entanto, se as entradas de registo estiverem localizadas, o FileX precisa de completar a operação de ficheiros anteriores ou reverter as alterações já aplicadas no sistema de ficheiros, desfazendo efetivamente as alterações. Em qualquer dos casos, após a aplicação das entradas de registo no sistema de ficheiros, o sistema de ficheiros é restaurado num estado coerente, e a aplicação pode começar a utilizar novamente o sistema de ficheiros.

Para os meios de comunicação protegidos pelo FileX, durante a operação de atualização de ficheiros, a parte dos dados é escrita diretamente para os meios de comunicação. Como o FileX escreve dados, também regista quaisquer alterações necessárias para serem aplicadas às entradas de diretório, tabela FAT. Esta informação está registada nas entradas de registo tolerantes ao ficheiro. Esta abordagem garante que as atualizações para o sistema de ficheiros ocorrem após a escrita dos dados para os meios de comunicação. Se os meios de comunicação forem ejetados durante a fase de escrita de dados, as informações cruciais do sistema de ficheiros ainda não foram alteradas. Portanto, o sistema de ficheiros não é afetado pela interrupção.

Depois de todos os dados terem sido escritos com sucesso para os meios de comunicação, o FileX segue então as informações nas entradas de registo para aplicar as alterações à informação do sistema, uma entrada de cada vez. Depois de todas as informações do sistema serem comprometidas com os meios de comunicação, as entradas de registo são removidas do registo tolerante de avaria. Neste ponto, o FileX completa a operação de atualização de ficheiros.

Durante a operação de atualização de ficheiros, os ficheiros não são atualizados no local. O módulo tolerante a falhas atribui um sector para os dados para escrever os novos dados e, em seguida, remover o sector que contém os dados a serem substituídos, atualizando as entradas de FAT relacionadas para ligar o novo sector ao chian. Para situações em que os dados parciais num cluster precisam de ser modificados, o FileX atribui sempre novos clusters, escreve todos os dados dos antigos clusters com dados atualizados para os novos clusters e, em seguida, liberta os antigos clusters. Isto garante que, se a atualização do ficheiro for interrompida, o ficheiro original está intacto. A aplicação deve estar ciente de que, no âmbito da proteção tolerante a falhas do FileX, a atualização de dados num ficheiro requer que os meios de comunicação tenham espaço livre suficiente para reter novos dados antes de os setores com dados antigos poderem ser divulgados. Se os meios de comunicação não tiverem espaço suficiente para conter novos dados, a operação de atualização falha.
