---
title: Capítulo 4 - Análise de desempenho do Azure RTOS TraceX
description: Este capítulo descreve a ferramenta de análise de desempenho Azure RTOS TraceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 719f27ef54091e2db9eefa982ce0c27561079b5b3a254d3fd09cc46d8f66f252
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788642"
---
# <a name="chapter-4---azure-rtos-tracex-performance-analysis"></a>Capítulo 4 - Análise de desempenho do Azure RTOS TraceX

Este capítulo descreve a ferramenta de análise de desempenho Azure RTOS TraceX:

## <a name="performance-analysis"></a>Análise de Desempenho

O TraceX fornece uma análise de desempenho incorporada de ficheiros de vestígios. Informações como o perfil de *execução,* *serviços populares,* *utilização de pilhas de fio,* e várias *estatísticas de desempenho,* incluindo as estatísticas do FileX e netX, estão prontamente disponíveis. Estas informações estão disponíveis através do item do menu ***Ver.*** 


## <a name="execution-profile"></a>Perfil de execução

Selecionando o **botão*** Generate Execution Profile _ ou _*_View -Execution Profile_*_ apresenta o perfil de execução TraceX para o ficheiro de traços atualmente carregado. O perfil de execução associado à amostra ThreadX é mostrado em _*Figura 19**.

![Screenshot do perfil de execução associado à amostra threadx traço de demonstração.](./media/user-guide/execution_profile.png)

**FIGURA 19**

O exemplo mostrado na **Figura 19** indica que quase 45% do tempo de processamento está dentro do **_fio 2_*_ e quase 51% do tempo de processamento está dentro do _* thread _1_** Isto é lógico, uma vez que a maior parte dos vestígios mostra estas linhas enviando e recebendo mensagens. Os restantes contextos de execução têm apenas um pequeno tempo de execução neste exemplo.

## <a name="popular-services"></a>Serviços Populares

Selecionando ***Ver ->Serviços Populares** _ apresenta os serviços populares no arquivo de traços atualmente carregado. Por padrão, esta informação é apresentada para todo o sistema. No entanto, os serviços populares para fios específicos também estão disponíveis. Os serviços populares na amostra ThreadX mostram vestígios de demonstração em _*Figura 20**.

![Screenshot dos serviços populares na amostra ThreadX traço de demonstração.](./media/user-guide/popular_services.png)

**FIGURA 20**

O exemplo mostrado na **Figura 20** indica que **_tx_queue_send_*_ e _*_tx_queue_receive_** são os dois serviços mais populares neste rastreio. Isto é consistente com o comportamento da demonstração padrão da ThreadX a partir da qual este vestígio foi capturado.

Os fios específicos podem ser selecionados para esta análise utilizando a lista de seleção drop-down no topo desta janela. **A figura 21** mostra esta análise para **_o fio 3_**.

![Screenshot da análise para um serviço popular TraceX.](./media/user-guide/popular_services_thread3.png)

**FIGURA 21**

## <a name="thread-stack-usage-analysis-for-thread-3"></a>Utilização da pilha de fio ![Análise para o fio 3.](./media/user-guide/screen_shot_17.png)

Selecionar o botão ***Generate Thread Stack Use** _ ou View _*_-> Thread Stack Usage_*_ apresenta o uso da pilha para cada fio no ficheiro de traços. Isto é realizado pela ThreadX, incluindo o ponteiro de pilha de fio atual em muitas das entradas de vestígios no ficheiro. Uma utilização de pilha de 100% indica que a pilha transbordou e deve ser corrigida na aplicação. Se não houver execução de fio dentro deste ficheiro de vestígios, a utilização da pilha para esse fio é mostrada a 0%. A utilização da pilha de fio na amostra ThreadX é mostrada em _*Figura 22**.

![Screenshot do uso da pilha de fio TraceX.](./media/user-guide/thread_stack_usage.png)

**FIGURA 22**

O exemplo mostrado na **Figura 22** indica que a maioria dos fios neste vestígio têm entre 9% e 12% de utilização da pilha.

## <a name="performance-statistics"></a>Estatísticas de Desempenho

Selecionar o botão ***Gerar Estatísticas de Desempenho** _ ou _ Ver *_-> Estatísticas_* de Desempenho * apresenta as estatísticas de desempenho do ficheiro de traços atualmente carregado. Por padrão, esta informação é apresentada para todo o sistema. No entanto, as estatísticas de desempenho também estão disponíveis para cada fio específico.

As estatísticas de desempenho da amostra ThreadX mostram os vestígios de demonstração da threadX na **figura 23**.

![Screenshot das estatísticas de desempenho do TraceX.](./media/user-guide/performance_statistics.png)

**FIGURA 23**

O exemplo mostrado na **Figura 23** indica que havia 18 interruptores de contexto neste ficheiro de traços, bem como cinco preemposições de fio, 16 suspensões de roscas, 19 reposições de roscas e três interrupções. Não foram encontradas inversões prioritárias neste ficheiro. Note que existem duas categorias de inversões prioritárias, nomeadamente, *determinísticas* e *não determinísticas.* Inversões prioritárias determinísticas são inversão prioritária em que um fio é bloqueado num mutex propriedade de um fio de menor prioridade. Uma inversão de prioridade não determinística é onde um fio de prioridade inferior diferente corre durante uma inversão de prioridade determinística. O posterior pode causar um comportamento de tempo imprevisto na aplicação e deve ser estudado cuidadosamente.

## <a name="filex-statistics"></a>Estatísticas do FileX

Selecionando ***Ver -> FileX Statistics** _ apresenta as estatísticas de desempenho do FileX do ficheiro de traços atualmente carregado. Esta informação é exibida para todo o sistema, em todos os abertos .. /objetos mediáticos. As estatísticas de desempenho do traço de demonstração filex da amostra são mostradas em _*Figura 24**.

![Screenshot das Estatísticas do FileX.](./media/user-guide/filex_statistics.png)

**FIGURA 24**

O exemplo mostrado na **Figura 27** indica que foram 19 .. /media abre, 19 .. /media fecha, 19 .. /media flushes, 18 leituras de diretório, 19 escritos de diretório, e 18 cache de diretório falha. As informações additonais podem ser vistas deslocando-se para baixo na janela de estatísticas.

## <a name="netx-statistics"></a>Estatísticas NetX

Selecionando ***Ver -NetX Statistics** _ apresenta as estatísticas de desempenho netX do ficheiro de traços atualmente carregado. Esta informação é exibida para todo o sistema. As estatísticas de desempenho da amostra do traço de demonstração netX são mostradas em _*Figura 25**.

![Screenshot das Estatísticas NetX.](./media/user-guide/netx_statistics.png)

**FIGURA 25**

O exemplo mostrado na **Figura 25** indica que não houve eventos ARP, Ping ou UDP, mas foram enviados 30 pacotes IP, 1.368 bytes IP enviados, 30 pacotes IP recebidos e 1.360 bytes IP recebidos.

## <a name="trace-file-information"></a>Informação de arquivo de traços

Selecionando ***Ver -> Trace File Information** _ apresenta algumas informações básicas sobre o ficheiro de rastreio aberto. Esta informação inclui a ordem byte do ficheiro, o tamanho da fonte de tempo, o número máximo de bytes para cada nome do objeto e o endereço base de todos os ponteiros de arquivo de traços. _ *Figura 26** mostra as informações do ficheiro de traços para o ficheiro de **_traços padrão demo_threadx.trx._**

![Screenshot da informação do ficheiro TraceX.](./media/user-guide/trace_file_info.png)

**FIGURA 26**

## <a name="raw-trace-dump"></a>Despejo de vestígios crus

Selecionando ***Ver -> Despejá-traços brutos** _ apresenta um diálogo para nomear o ficheiro que contém o despejo de vestígios brutos. Após a entrada do nome e caminho do ficheiro, o TraceX constrói o ficheiro de traços brutos em formato de texto e lança _*_notepad.exe_*_ para o exibir. _ *Figura 27** mostra o depósito de ficheiros de traços brutos para o ficheiro de **_traços de demo_threadx.trx_** padrão.

![Screenshot do depósito de vestígios brutos.](./media/user-guide/raw_trace_dump.png)

**FIGURA 27**
