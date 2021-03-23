---
title: Capítulo 2 - Instalação e utilização do Azure RTOS FileX
description: Este capítulo contém uma introdução ao Azure RTOS FileX e uma descrição das condições de instalação, procedimentos e utilização, incluindo os seguintes
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6703b10d8e0895984bb92d74d5dff809dca1a7f8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825508"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-filex"></a>Capítulo 2 - Instalação e utilização do Azure RTOS FileX

Este capítulo contém uma introdução ao Azure RTOS FileX e uma descrição das condições de instalação, procedimentos e utilização. 

## <a name="host-considerations"></a>Considerações de Anfitrião

### <a name="computer-type"></a>Tipo de computador

O desenvolvimento incorporado é geralmente realizado em computadores anfitriões Windows ou Linux (Unix). Após a compilação da aplicação, ligada e localizada no anfitrião, é descarregada para o hardware alvo para execução.

### <a name="download-interfaces"></a>Baixar Interfaces

Normalmente, o download do alvo é feito a partir do depurar da ferramenta de desenvolvimento. Após o download, o depurante é responsável por fornecer controlo de execução de alvos (ir, parar, quebrar, etc.) bem como aceder aos registos de memória e processador.

### <a name="debugging-tools"></a>Ferramentas de depurar

A maioria dos depurares de ferramentas de desenvolvimento comunicam com o hardware-alvo através de ligações de depuro on-chip (TOC), tais como JTAG (IEEE 1149.1) e Modo de Depuramento de Fundo (BDM). Os debuggers também comunicam com o hardware alvo através de ligações In-Circuit Emulation (ICE). As ligações OCD e ICE fornecem soluções robustas com uma intrusão mínima no software residente alvo.

### <a name="required-hard-disk-space"></a>Espaço de disco rígido necessário

O código-fonte do FileX é entregue em formato ASCII e requer aproximadamente 500 KBytes de espaço no disco rígido do computador anfitrião

## <a name="target-considerations"></a>Considerações-alvo

O FileX requer entre 6 KBytes e 30 KBytes de memória Read-Only (ROM) no alvo. São necessários mais 100 bytes da Memória de Acesso Aleatório (RAM) do alvo para estruturas globais de dados do FileX. Cada mídia aberta também requer 1,5 KBytes de RAM para o bloco de controlo, além de RAM para armazenar dados para um sector (normalmente 512 bytes).

Para a estampagem de data/hora funcionar corretamente, o FileX baseia-se nas instalações do temporizador ThreadX. Isto é implementado criando um temporizador específico do FileX durante a inicialização do FileX. O FileX também conta com semáforos ThreadX para proteção de múltiplos fios e suspensão de E/S.

## <a name="product-distribution"></a>Distribuição de Produtos

O Azure RTOS FileX pode ser obtido a partir do nosso repositório de código de fonte pública em <https://github.com/azure-rtos/filex/> .

Segue-se uma lista de vários ficheiros importantes no repositório:

- ***fx_api.h*** : Este ficheiro de cabeçalho C contém todos os equacionões do sistema, estruturas de dados e protótipos de serviço.
- ***fx_port.h*** : Este ficheiro de cabeçalho C contém todas as definições e estruturas específicas da ferramenta de desenvolvimento.
- ***demo_filex.c*** : Este ficheiro C contém uma pequena aplicação de demonstração.
- ***fx.a (ou fx.lib)*** : Esta é a versão binária da biblioteca FileX C. É distribuído com o pacote padrão.

> [!IMPORTANT]
> *Todos os nomes dos ficheiros estão em minúsculas. Esta convenção de nomeação facilita a conversão dos comandos para plataformas de desenvolvimento Linux (Unix).*

## <a name="filex-installation"></a>Instalação FileX

O FileX é instalado clonando o repositório GitHub à sua máquina local. O seguinte é a sintaxe típica para criar um clone do repositório FileX no seu PC:

```c
    git clone https://github.com/azure-rtos/filex
```

Em alternativa, pode descarregar uma cópia do repositório utilizando o botão de descarregamento na página principal do GitHub.

Também encontrará instruções para a construção da biblioteca FileX na primeira página do repositório online.

> [!IMPORTANT]
> O software de aplicação precisa de acesso ao ficheiro da biblioteca FileX (normalmente chamado***fx.a** _ ou _*_fx.lib_*_) _and o C incluem ficheiros **fx_api.h** e **fx_port.h**. Isto é conseguido quer estabelecendo o caminho adequado para as ferramentas de desenvolvimento, quer copiando estes ficheiros para a área de desenvolvimento de aplicações.

## <a name="using-filex"></a>Utilização de Filex

A utilização do FileX é fácil. Basicamente, o código de aplicação deve incluir ***fx_api.h** _ durante a compilação e ligação com a biblioteca de tempo de execução FileX _*_fx.a_*_ (ou _*_fx.lib)._*_ É claro que os ficheiros ThreadX, nomeadamente _*_tx_api.h_*_ e _*_tx.a_*_ (ou _*_tx.lib)_,*_*_ também são necessários.

> [!IMPORTANT]
> Ao utilizar o FileX no modo Autónomo **(FX_STANDALONE_ENABLE** deve ser definido), não são necessários ficheiros/bibliotecas ThreadX.

Assumindo que já está a utilizar o ThreadX, são necessários quatro passos para a construção de uma aplicação FileX:

1. Inclua o ficheiro ***fx_api.h*** em todos os ficheiros de aplicações que utilizam serviços FileX ou estruturas de dados.
1. Inicialize o sistema FileX chamando ***fx_system_initialize** _ da função _ *_tx_application_define_** ou de um fio de aplicação.

    > [!IMPORTANT]
    > Ao utilizar o FileX no modo Autónomo, ***fx_system_initialize*** devem ser chamados diretamente do código de aplicação.

1. Adicione uma ou mais chamadas para ***fx_media_open*** para configurar os meios de comunicação FileX. Esta chamada deve ser feita a partir do contexto de um fio de aplicação.

    > [!IMPORTANT]
    > *Lembre-se que a **chamada fx_media_open** requer RAM suficiente para armazenar dados para um setor.*

1. Compilar a fonte de aplicação e ligar-se com as bibliotecas de tempo de execução FileX e ThreadX, ***fx.a** _ (ou _*_fx.lib)_*_ e _*_tx.a_*_ (ou _*_tx.lib_**). A imagem resultante pode ser descarregada para o alvo e executada!

## <a name="troubleshooting"></a>Resolução de problemas

Cada porta FileX é entregue com uma aplicação de demonstração. É sempre uma boa ideia pôr o sistema de demonstração em primeiro lugar - seja no hardware-alvo ou num ambiente específico de demonstração.

Se o sistema de demonstração não funcionar, tente as seguintes coisas para reduzir o problema:

1. Determina quanto da demonstração está a decorrer.
1. Aumente os tamanhos das pilhas (isto é mais importante no código de aplicação real do que na demonstração).
1. Certifique-se de que existe RAM suficiente para o tamanho padrão do disco RAM 32KBytes. O sistema básico funcionará em muito menos RAM; no entanto, à medida que mais do disco RAM é usado, os problemas surgirão se não houver memória suficiente.
1. Contornar temporariamente quaisquer alterações recentes para ver se o problema desaparece ou muda. Estas informações devem revelar-se úteis aos engenheiros de suporte da Microsoft. Siga os procedimentos descritos no "Centro de Apoio ao Cliente" para enviar as informações recolhidas a partir das etapas de resolução de problemas.

## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração ao construir a biblioteca FileX e a aplicação utilizando o FileX. As opções abaixo podem ser definidas na fonte de aplicação, na linha de comando ou dentro do ***ficheiro fx_user.h.***

> [!IMPORTANT]
> *As opções definidas em **fx_user.h** só são aplicadas se a aplicação e a biblioteca ThreadX forem construídas com **_FX_INCLUDE_USER_DEFINE_FILE_*_ defined._ Quando utilizar o FileX no modo Autónomo (FX_STANDALONE_ENABLE**** deve ser definido), não são necessários ficheiros/bibliotecas ThreadX.

A lista a seguir descreve cada opção de configuração em detalhe:

|Definir|Significado|
|----------    |-----------|
|FX_MAX_LAST_NAME_LEN        |Este valor define o comprimento máximo do nome do ficheiro, que inclui o nome do caminho completo. Por padrão, este valor é de 256.|
|FX_DONT_UPDATE_OPEN_FILES    |Definido, o FileX não atualiza ficheiros já abertos.|
|FX_MEDIA_DISABLE_SEARCH_CACHE    |Definido, a otimização da cache de pesquisa de ficheiros é desativada.|
|FX_MEDIA_DISABLE_SEARCH_CACHE    |Definido, a otimização da cache de pesquisa de ficheiros é desativada.|
|FX_DISABLE_DIRECT_DATA_READ_CACHE_FILL |Definida, a atualização do sector de leitura direta da cache é desativada.|
|FX_MEDIA_STATISTICS_DISABLE |Definida, a recolha de estatísticas dos meios de comunicação é desativada.|
|FX_SINGLE_OPEN_LEGACY |Definida, a lógica aberta única do legado para o mesmo ficheiro está ativada.|
|FX_RENAME_PATH_INHERIT    |Definido, renomear herda informação do caminho.|
|FX_DISABLE_ERROR_CHECKING    |Remove o erro básico do FileX que verifica a API e resulta num melhor desempenho (até 30%) e menor tamanho de código.|
|FX_MAX_LONG_NAME_LEN    |Especifica o tamanho máximo do nome do ficheiro para FileX. O valor predefinido é de 256, mas este pode ser ultrapassado com uma definição de linha de comando. Os valores legais variam entre 13 e 256.|
|FX_MAX_SECTOR_CACHE|Especifica o número máximo de sectores lógicos que podem ser cached por FileX. O número real de sectores que podem ser em cache é menor desta constante e quantos sectores podem caber na quantidade de memória fornecida a fx_media_open. O valor predefinido é de 256. Todos os valores devem ser um poder de 2.|
|FX_FAT_MAP_SIZE    |Especifica o número de sectores que podem ser representados no mapa de atualização fat. O valor predefinido é de 256, mas este pode ser ultrapassado com uma definição de linha de comando. Valores maiores ajudam a reduzir as atualizações não precisadas dos sectores secundários da FAT.|
|FX_MAX_FAT_CACHE    |Especifica o número de entradas na cache DE FAT interna. O valor predefinido é de 16, mas este pode ser ultrapassado com uma definição de linha de comando. Todos os valores devem ser um poder de 2.|
|FX_FAULT_TOLERANT    |Quando definido, o FileX passa imediatamente a escrever pedidos de todos os sectores do sistema (setores de arranque, FAT e diretório) ao condutor dos meios de comunicação. Isto potencialmente diminui o desempenho, mas ajuda a limitar a corrupção a aglomerados perdidos. Note que ativar esta função não ativa automaticamente o Módulo Tolerante com Falhas de FileX, que é ativado pela definição|
|FX_FAULT_TOLERANT_DATA    |Quando definido, o FileX transmite imediatamente todos os pedidos de escrita de dados de ficheiros ao controlador do meio de comunicação. Isto potencialmente diminui o desempenho, mas ajuda a limitar os dados de ficheiros perdidos. Note que ativar esta função não ativa automaticamente o Módulo Tolerante com Falhas de FicheiroX, que é ativado definindo ***FX_ENABLE_FAULT_TOLERANT***|
|FX_NO_LOCAL_PATH|Remove a lógica do caminho local do FileX, resultando em tamanho de código menor.|
|FX_NO_TIMER|Elimina a configuração do temporizador ThreadX para atualizar a hora e a data do sistema FileX. Ao fazê-lo, a hora e a data por defeito serão colocadas em todas as operações de ficheiro.|
|FX_UPDATE_RATE_IN_SECONDS    |Especifica a taxa em que o tempo do sistema no FileX é ajustado. Por predefinição, o valor é de 10, especificando que o tempo do sistema FileX é atualizado a cada 10 segundos.|
|FX_ENABLE_EXFAT| Quando definido, a lógica de manuseamento do sistema de ficheiros exFAT está ativada no FileX. Por padrão, este símbolo não está definido.| 
|FX_UPDATE_RATE_IN_TICKS| Especifica a mesma taxa ***que FX_UPDATE_RATE_IN_SECONDS*** (ver acima), exceto em termos da frequência do temporizador ThreadX subjacente. O padrão é de 1000, que pressupõe uma taxa de temporizador ThreadX de 10ms e um intervalo de 10 segundos.|
|FX_SINGLE_THREAD|Elimina a lógica de proteção ThreadX da fonte FileX. Deve ser utilizado se o FileX estiver a ser utilizado apenas a partir de uma linha ou se o FileX estiver a ser utilizado sem o ThreadX.|
|FX_DRIVER_USE_64BIT_LBA|Quando definido, permite endereços sectoriais de 64 bits utilizados no controlador de E/S. Por padrão esta opção não está definida.|
|FX_ENABLE_FAULT_TOLERANT| Quando definido, ativa o Módulo Tolerante com Falhas de FicheiroX. Ativar o Tolerante de Falhas define automaticamente o símbolo ***FX_FAULT_TOLERANT** _ e _*_FX_FAULT_TOLERANT_DATA_**. Por padrão esta opção não está definida.|
|FX_FAULT_TOLERANT_BOOT_INDEX|Define byte offset no sector do arranque onde está o cluster para o tronco tolerante de falhas. Por padrão, este valor é de 116. Este campo leva 4 bytes. Os bytes 116 a 119 são escolhidos porque são marcados como reservados pela especificação FAT 12/16/32/exFAT.|
|FX_FAULT_TOLERANT_MINIMAL_CLUSTER|Este símbolo é precedido. Já não está a ser utilizado pela FileX Fault Tolerant.|
|FX_STANDALONE_ENABLE|Definido, permite que o FileX seja utilizado em modo autónomo (sem Azure RTOS). Por padrão, este símbolo não está definido.|

> [!IMPORTANT]
> Quando **FX_STANDALONE_ENABLE** é definida, a lógica do caminho local e a configuração do temporizador ThreadX são desativadas.

## <a name="filex-version-id"></a>ID da versão filex

A versão atual do FileX está disponível tanto para o utilizador como para o software da aplicação durante o tempo de funcionamento. O programador pode obter a versão FileX a partir do exame do ficheiro **fx_port.h.** Além disso, este ficheiro também contém um histórico de versão da porta correspondente. O software de aplicação pode obter a versão FileX examinando a cadeia global **_ _fx_version_id_**.
