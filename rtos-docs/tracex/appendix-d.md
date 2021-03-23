---
title: Apêndice D - Dumping e tampão de vestígios
description: Despejar o tampão de traços criado pela Azure RTOS ThreadX num ficheiro no computador anfitrião é feito através de comandos e/ou utilitários fornecidos pela ferramenta de desenvolvimento específica que está a ser utilizada.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 30f6b5e329feeb2dca37dda391fd738aba587c9a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827722"
---
# <a name="appendix-d---dumping-and-trace-buffer"></a>Apêndice D - Dumping e tampão de vestígios

Despejar o tampão de traços criado pela Azure RTOS ThreadX num ficheiro no computador anfitrião é feito através de comandos e/ou utilitários fornecidos pela ferramenta de desenvolvimento específica que está a ser utilizada. Este apêndice contém exemplos de despejo de um tampão de traços para um ficheiro de hospedeiro em algumas das ferramentas de desenvolvimento mais populares usadas com a ThreadX. 

## <a name="benchx-tools"></a>Ferramentas BenchX

O tampão de rastreio pode ser despejado facilmente num ficheiro de anfitrião com as ferramentas BenchX selecionando o botão ***Store Memory To File** _ dentro do _* Memory _View_**, como mostrado abaixo:

![Screenshot da Vista de Memória nas ferramentas BenchX.](./media/user-guide/image642.jpg)

Neste ponto, especifique o endereço do tampão de rastreamento, tamanho, nome do ficheiro de destino (incluindo o caminho) e selecione o botão ***Guardar*** como mostrado abaixo. Isto criará o ficheiro binário de rastreio para visualização dentro do TraceX.

![Screenshot das ferramentas BenchX economize o diálogo.](./media/user-guide/image643.jpg)

## <a name="realview-tools"></a>Ferramentas RealView

O tampão de rastreio pode ser despejado facilmente num ficheiro de anfitrião com as ferramentas ARM RealView, introduzindo o seguinte comando na linha de comando em RealView:

```c 
> WRITEFILE,raw trace_file.trx=0x6860..0xE560
```

Após a conclusão, o ficheiro ***trace_file.trx*** conterá o tampão de traço que está localizado a partir do endereço 0x6860 e vai até endereçar 0xE560. Este ficheiro está pronto para ser visualizado pela TraceX.

## <a name="iar-tools"></a>Ferramentas IAR

O tampão de rastreio pode ser despejado facilmente num ficheiro de anfitrião com as ferramentas IAR clicando simplesmente na vista de memória e selecionando o ***Memory Save...*** opção, como mostrado abaixo.

![Screenshot da opção Memória Guardar nas ferramentas IAR.](./media/user-guide/image0_311.jpg)

Isto resulta no diálogo ***Memory Save** _ a ser apresentado. Introduza o endereço inicial e final e o nome do ficheiro de rastreio e, em seguida, selecione o botão _*_Guardar._*_ No exemplo apresentado abaixo, as ferramentas IAR guardam o tampão de traço especificado nos registos intel HEX no ficheiro _*_trace_file.hex_**.

![Screenshot das ferramentas IAR Memória Guardar o diálogo.](./media/user-guide/image648.jpg)

Neste momento, temos o tampão de vestígios guardado no ficheiro ***trace_file.hex*** no hospedeiro e está pronto para ser visualizado com o TraceX.

## <a name="codewarrior-tools"></a>Ferramentas CodeWarrior

O tampão de vestígios pode ser despejado facilmente num ficheiro de hospedeiro com as ferramentas CodeWarrior, introduzindo o comando ***save** _ na Janela de Comando. O seguinte exemplo _ *_save_** comando assume que o tampão de traços começa em 0x102200 e termina em 0x109F00:

```c
> save –b p:0x102200..0x109F00 trace_file.trx -a 32bit
```

Isto resulta na guarda do tampão de vestígios no ficheiro ***trace_file.trx*** no hospedeiro.

## <a name="mplab-tools"></a>Ferramentas MPLAB

O MPLAB pode criar um ficheiro de traços compatíveis com o TraceX através do seu utilitário de Tabela de Exportação, que permite a exportação de qualquer gama de memória para um ficheiro de anfitrião. Para utilizar este utilitário para criar um ficheiro de rastreio para a TraceX, proceda da seguinte forma:

**Passo 1** Abra uma janela de memória selecionando a Memória de >.

![Screenshot da Memória selecionada no menu Ver.](./media/user-guide/image0_316.jpg)

**Passo 2** Clique com o botão direito dentro da **Visualização de Memória** para mostrar uma lista de opções. Especifique **o formato do display -1 Byte** para selecionar o byte display..

![Screenshot da visualização da memória com a opção 'Display' Format selecionada.](./media/user-guide/image650.png)

![Screenshot do diálogo Go To.](./media/user-guide/image651.jpg)

**Passo 3** Clique novamente no botão direito dentro da Janela **visualização** da memória e selecione **Go To**, que abre uma caixa de diálogo que lhe permite especificar o endereço do tampão do evento. Este exemplo mostra **_event_buffer_** a ser exibido.

![Screenshot da visualização da memória com a opção Go To selecionada.](./media/user-guide/image0_312.jpg)

![Screenshot de um exemplo que mostra o event_buffer a ser exibido.](./media/user-guide/image653.png)

**Passo 4** Isto destaca o conteúdo da primeira localização do tampão de traço, que é sempre a cadeia BTXT....

![Screenshot da primeira localização do tampão de vestígios.](./media/user-guide/image0_313.jpg)

**Passo 5** Agora, clique com o botão direito novamente para trazer o menu de opções e selecione **Tabela de Exportação**.

![Screenshot da Vista de Memória com a opção Tabela de Exportação selecionada.](./media/user-guide/image0_314.jpg)

**Passo 6** Isto eleva o diálogo da tabela de **exportação,** como mostra. Especifique a gama de endereços para exportação. Para um tampão de traço de 8K, como é o caso neste exemplo, especifique o alcance 0xA00006AC para 0xA00026AC e introduza um nome para o ficheiro anfitrião a ser criado (demo_threadx.trx neste exemplo).

! [[Screenshot do Export As dialog.](./media/user-guide/image656.jpg)

**Passo 7** Um ficheiro chamado **demo_threadx.trx** será criado no anfitrião, e este ficheiro pode ser aberto pela TraceX.

## <a name="ghs-tools"></a>Ferramentas GHS

O tampão de rastreio pode ser despejado facilmente num ficheiro de hospedeiro com as ferramentas GHS, introduzindo o seguinte comando na linha de comando na janela de comando do depurg:

```c
memdump raw c:releasethreadxdemo_threadx.trx event_buffer 32768
```

Após a conclusão, o ficheiro **demo_threadx.trx** conterá o tampão de vestígios localizado no event_buffer com um tamanho de 32.768 bytes e está pronto para ser visualizado pela TraceX.

## <a name="renesas-hew"></a>Renesas HEW

O tampão de rastreio pode ser despejado facilmente num ficheiro de hospedeiro com as ferramentas HEW da Renasas seguindo os três passos (e subpassos) abaixo:

**Passo 1** Abrir a janela de memória.

! [[Screenshot da Janela de Memória.](./media/user-guide/image657.jpg)

**Passo 2** Coloque o cursor dentro da janela da memória e clique à direita.

![Screenshot da Janela memória com a opção Guardar selecionada.](./media/user-guide/image0_315.jpg)

**Passo 3** Selecione Guardar e, em seguida, na Memória Guardar Como janela fazer o seguinte:

- Selecione formato de ficheiro: Binário.
- Especificar o nome de ficheiro: Como Desejado
- Especificar endereço de início: trace_buffer
- Especificar endereço final: (trace_buffer+tamanho)
- Especificar tamanho de acesso: 1
- Clicar em Guardar

![Screenshot do Save Memory Como diálogo.](./media/user-guide/image659.jpg)