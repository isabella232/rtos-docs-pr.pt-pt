---
title: Compreenda o Azure RTOS GUIX e o Azure RTOS RTOS GUIX Studio
description: O Azure RTOS GUIX é um pacote de qualidade profissional, criado para atender às necessidades dos desenvolvedores de sistemas incorporados.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 8f4a1578fcabdabfb213ced9c6593f6cffc964aa
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171408"
---
# <a name="overview-of-azure-rtos-guix-and-azure-rtos-guix-studio"></a>Visão geral do Azure RTOS GUIX e Azure RTOS GUIX Studio

Azure GUIX incorporado GUI é a solução GUI avançada e industrial da Microsoft projetada especificamente para aplicações profundamente incorporadas, em tempo real e IoT. A Microsoft também fornece uma ferramenta de design de ambiente de trabalho WYSIWYG totalmente apresentada chamada Azure RTOS GUIX Studio, que permite que os desenvolvedores desenhem o seu GUI no ambiente de trabalho e gerem o código GUI ID incorporado Azure RTOS GUIX que pode ser exportado para o alvo. O Azure RTOS GUIX está totalmente integrado com o Azure RTOS ThreadX RTOS e está disponível para muitos dos mesmos processadores suportados pela Azure RTOS ThreadX. Tudo isto combinado com uma pegada extremamente pequena, uma execução rápida e uma facilidade de utilização superior, fazem do Azure RTOS GUIX a escolha ideal para as aplicações IoT incorporadas mais exigentes que requerem uma interface de utilizador. 

## <a name="azure-rtos-guix-api"></a>Azure RTOS GUIX API

### <a name="powerful-apis"></a>APIs poderosos

* Suporte total para desenho de tela direta quando necessário
* Simples de interagir com O Azure RTOS GUIX Studio gerou código
* APIs para linha, retângulo, polígono, etc.
* APIs para círculo, arco, torta, acorde, elipse, etc.
* APIs para desenho de texto e posicionamento
* Anti-aliasing, preenchimentos de textura e enchimentos sólidos
* APIs para criar e modificar ecrãs e widgets

### <a name="azure-rtos-guix-studio-generated-files"></a>Arquivos gerados pelo estúdio Azure RTOS GUIX

* Ficheiros de origem ANSI C gerados automaticamente
* Isola o software de aplicação a partir de detalhes do layout
* Inclui fontes e imagens necessárias pelo design da UI
* Ficheiros gerados compilados com código de aplicação
* O layout do ecrã pode ser atualizado sem afetar a lógica da aplicação
* IDs de recursos criam independência linguística e temática
* Funções de desenho personalizado e processamento de eventos fornecidas pelo utilizador

### <a name="widget-library"></a>Biblioteca Widget

* Conjunto pré-definido mas personalizável de elementos de interface comuns
* Extremamente pequeno, compacto e eficiente
* Biblioteca inclui botão, bitola, lista, janela, pergaminho, slider, barra de progresso, prompt e muito mais
* Desenho e aparência totalmente personalizáveis
* Funcionamento totalmente personalizável e tratamento de eventos
* Apenas os widgets utilizados estão ligados ao software de aplicações

### <a name="math-and-utilities"></a>Matemática e utilidades

* Funções para o pecado, cos, arcsin, arccos, tangente, raiz quadrada
* Funções para manipular regiões de tela
* Configuração e arranque do sistema
* Definição de piscina de memória (opcional)
* Gestão do Temporizador
* Gestão de Animação
* Manutenção de listas sujas

### <a name="image-processing"></a>Processamento de imagens

* Funções para descodificar tempo de execução de imagens jpeg e png
* Aplicar dilatação e conversão de espaço de cor
* Rotação de imagem
* Dimensionamento de imagem
* Mistura de imagem

### <a name="event-processing"></a>Processamento de eventos

* Suspende automaticamente o fio Azure RTOS GUIX quando está inativo
* Modelo de programação orientado por eventos popular em design de UI
* Isola os condutores de entrada do fio de desenho Azure RTOS GUIX
* Funções para envio e receção de eventos
* Tipos de eventos pré-definidos para todos os tipos de widgetS Azure RTOS GUIX
* Eventos personalizados definidos pelo utilizador suportados

### <a name="canvas-processing"></a>Processamento de lona

* Manutenção de clipping e Z-Order
* Isola a biblioteca widget a partir de detalhes de hardware
* Isola a aplicação a partir de detalhes de hardware
* Renovação automática de fundo de áreas sujas
* Múltiplas telas com camadas e mistura suportadas
* Pode ser invocado diretamente pelo software de aplicação

### <a name="input-device-drivers"></a>Controlador de dispositivos de entrada

* Suporte específico para hardware, Azure RTOS GUIX e aplicação isolada de detalhes de hardware
* Toque resistivo, toque de boné e teclado suportado
* Eventos de entrada passados para a fila de eventos Azure RTOS GUIX

### <a name="display-drivers"></a>Controladores de exibição

* Suporte específico para hardware
* Condutores genéricos fornecidos para toda a profundidade e formatos de cor
* Personalizado para utilizar aceleradores gráficos disponíveis

### <a name="target-hardware"></a>Hardware-alvo

* Quase todo o hardware capaz de saída gráfica é compatível com GUIX
* Múltiplas exibições físicas suportadas
* Requisitos mínimos de RAM e Flash

## <a name="create-elegant-user-interfaces"></a>Criar interfaces de utilizador elegantes

Azure RTOS GUIX e Azure RTOS GUIX Studio fornecem todas as funcionalidades necessárias para criar interfaces de utilizador exclusivamente elegantes. O pacote padrão Azure RTOS GUIX inclui várias interfaces de utilizador de amostras, incluindo uma referência de dispositivo médico, uma referência de relógio inteligente, uma referência de domótica, uma referência de controlo industrial, uma referência automóvel, e vários exemplos de sprite e animação. Clique nos exemplos de referência apresentados abaixo.

### <a name="home-automation"></a>Domótica

<img alt="Screenshot of the GUIX home automation" class="img-responsive" src="./media/overview/guix_home_automation.png"/>

### <a name="medical"></a>Médico

<img alt="Screenshot of the GUIX medical device" class="img-responsive" src="./media/overview/demo_guix_medical.png"/>

### <a name="consumer"></a>Consumidor

<img alt="Screenshot of the GUIX Consumer smart watch" class="img-responsive" src="./media/overview/demo_guix_smart_watch.png"/>

### <a name="white-goods"></a>Bens Brancos

<img alt="Screenshot of the GUIX white goods exaample" class="img-responsive" src="./media/overview/demo_guix_white_goods.png"/>

### <a name="automotive"></a>Automóvel

<img alt="Screenshot of the GUIX automotive" class="img-responsive" src="./media/overview/demo_guix_infotainment.png"/>

### <a name="industrial"></a>Industrial

<img alt="Screenshot of the GUIX industrial control" class="img-responsive" src="./media/overview/demo_guix_industrial.png"/>

Cada referência Azure RTOS GUIX tem um projeto correspondente do Azure RTOS GUIX Studio que define todos os elementos gráficos do design de referência. Mudar um design de referência é fácil. Basta abrir o projeto Azure RTOS GUIX correspondente, fazer as alterações desejadas, salvar o projeto e, em seguida, selecionar *o Projeto*.

Gere todos os ficheiros de saída para gerar o código C para Azure RTOS GUIX. Em seguida, basta reconstruir a aplicação-alvo e correr para observar o design de referência modificado.

### <a name="memory-footprint"></a>Pegada de memória

O Azure RTOS GUIX tem uma pegada mínima notável de 13.2KB de FLASH e 4KB RAM para suporte básico, sem incluir a memória necessária para uma tela.

Para um visor com gram interno e tecnologia de auto-atualização, não é necessária memória de lona. No entanto, para melhorar o desempenho do desenho, ou para uma configuração do visor que não utilize o GRAM local para o visor, uma área de memória de tela é definida pela aplicação.

Os requisitos de memória de lona são uma função do tamanho da tela, bem como da profundidade de cor, e são definidos pela fórmula:

<i>RAM de lona (bytes) = (x * y * (bpp/8))</i>

Onde "x" e "y" são as dimensões da tela (display).

A maioria das aplicações também utiliza recursos gráficos, que não estão incluídos nos requisitos de armazenamento da biblioteca Azure RTOS GUIX. Estes recursos incluem fontes, ícones gráficos (pixelmaps) e cordas estáticas. Estes dados podem ser armazenados na secção de memória const (ou seja, FLASH).

O tamanho desta área de memória depende de uma série de fatores, incluindo o número e o tamanho de fontes únicas utilizadas, o número e o tamanho dos ícones gráficos utilizados, o formato de cor de saída, e se cada recurso está ou não a usar dados comprimidos, uma vez que o Azure RTOS GUIX suporta a compressão RLE tanto dos dados de fonte como de pixelmap. Os requisitos de armazenamento de cada recurso são apresentados dentro da aplicação Azure RTOS GUIX Studio, permitindo ao utilizador rastrear e monitorizar a quantidade de memória flash que será consumida pelos recursos da aplicação.

Tal como o Azure RTOS ThreadX, o tamanho do Azure RTOS GUIX escala automaticamente com base nos serviços realmente utilizados pela aplicação. Isto praticamente elimina a necessidade de configuração complicada e constrói parâmetros, tornando as coisas mais fáceis para o desenvolvedor.

#### <a name="simple-easy-to-use"></a>Simples e fácil de usar

O Azure RTOS GUIX é muito simples de usar e o Azure RTOS GUIX Studio torna ainda mais fácil, permitindo que os desenvolvedores desenhem visualmente no ambiente de trabalho e gerem código C que funciona no alvo real. As aplicações podem então adicionar as suas próprias funções personalizadas de manuseamento e desenho de eventos para completar o seu GUI.

A utilização da API AZURE RTOS GUIX é simples. A Azure RTOS GUIX API é simultaneamente intuitiva e altamente funcional. Os nomes da API são feitos de palavras reais e não da "sopa do alfabeto" e/ou dos nomes altamente abreviados que são tão comuns em outros produtos do sistema de ficheiros. Todas as APIs Azure RTOS GUIX têm uma *gx_* líder e seguem uma convenção de nomeação de substantivos. Além disso, existe uma consistência funcional em toda a API. Por exemplo, todas as APIs que inicializam um bloco de controlo widget são &lt; nomeadas widget_type &gt; _create, e os parâmetros de função de criação para cada tipo de widget são sempre definidos na mesma ordem.

### <a name="comprehensive-set-of-built-in-widgets"></a>Conjunto abrangente de widgets incorporados

* Azure RTOS GUIX fornece um rico conjunto de widgets incorporados, incluindo:
* Menu de Acordeão
* Botão
* Caixa de verificação
* Bitola Circular
* Lista de drop down
* Lista Horizontal
* Janela horizontal do travessa
* Ícone
* Botão de ícone
* Gráfico de linha
* Menu
* Botão de texto multi linha
* Entrada de texto multi linha
* Vista de texto multi linha
* Solicitação pixelmap numérica
* Solicitação numérica
* Roda de pergaminho numérica
* Botão Pixelmap
* Pixelmap Prompt
* Pixelmap Slider
* Pixelmap Sprite
* Barra de Progresso
* Prompt
* Barra de Progresso Radial
* Botão de rádio
* Roda de pergaminho
* Entrada de texto de linha única
* Slider
* Roda de pergaminho de corda
* Botão de texto
* Vista de Árvore
* Lista Vertical
* Barra de pergaminho vertical

É fácil para a aplicação criar os seus próprios widgets de cliente também.

### <a name="complete-low-level-drawing-api"></a>API de desenho de baixo nível completo

O Azure RTOS GUIX fornece uma API de desenho de tela robusta, permitindo que a aplicação torne formas gráficas complexas.

Todas as funções suportam anti-aliasing em alvos de alta profundidade de cores, e todas as formas podem ser preenchidas o nosso delineado, incluindo preenchimentos sólidos e pixelmap padrão. Todos os primitivos de desenho suportam a escova alfa quando correm a 16 bpp e a profundidade de cor mais alta. As funções de desenho incluem:

* Desenho de arco
* Desenho de círculo
* Desenho de linha
* Sorteio de Tortas
* Mistura pixelmap
* Azulejo pixelmap
* Desenho de Polígono
* Desenho de texto
* Desenho de acordes
* Desenho elipse
* Desenho de pixels
* Pixelmap Draw
* Rotação pixelmap
* Desenho de retângulo
* Mistura de texto

### <a name="default-free-fonts-and-easy-to-add-more"></a>Fontes gratuitas padrão e fácil de adicionar mais

Azure RTOS GUIX fornece um conjunto gratuito de fontes TrueType. Os desenvolvedores podem adicionar fontes TrueType adicionais conforme desejado.

O formato de fonte Azure RTOS GUIX suporta fontes anti-aliasing 8bpp, 4bpp anti-aliasing e 1bpp de fontes monocromáticas. Para as aplicações mais restritas a recursos, o Azure RTOS GUIX pré-torna as fontes TrueType num formato de bitmap comprimido utilizando a nossa ferramenta de desktop GUIX Studio.

### <a name="custom-jpg-and-png-decoder-implementation"></a>Implementação personalizada do descodificador JPG e PNG

Implementação personalizada de descodificador JPG e PNG descodificador de ficheiros JPG e PNG implementação. Esta implementação suporta a conversão de espaço de cores, dilatação e criação de tempo de execução de imagens de formato pixelmap compatíveis com Azure RTOS GUIX.

### <a name="extensive-display-and-touchscreen-support"></a>Extenso suporte de ecrã e ecrã tátil

Azure RTOS GUIX fornece controladores de exibição genéricos para quase todos os formatos de cores, incluindo monocromático de 1bpp, paleta de 8 bpp, formato 8 bpp 3:3:2,

Formato 16 bpp 565 rgb, 16 bpp 4:4:4:4, formato 32 bpp x:r:g:b e 32 bpp a:r:g:b. Além disso, o Azure RTOS GUIX está integrado com muitos dos controladores LCD mais populares e aceleradores de hardware (ST ChromeArt, Renesas Synergy, etc.).

O Azure RTOS GUIX suporta totalmente o ecrã tátil (incluindo suporte a gestos), caneta e dispositivos de entrada de teclado virtual.

### <a name="azure-rtos-guix-studio-desktop-wysiwyg-tool"></a>Ferramenta Azure RTOS GUIX Studio WYSIWYG

O Azure RTOS GUIX Studio fornece um ambiente completo de design de ecrã WYSIWYG que permite ao utilizador arrastar e largar elementos gráficos usados para construir os ecrãs GUI. O Azure RTOS GUIX Studio gera automaticamente código C compatível com a biblioteca Azure RTOS GUIX, pronta a ser compilada e executada no alvo. Os desenvolvedores podem produzir fontes pré-renderizadas para uso dentro de uma aplicação usando a ferramenta integrada de geração de fontes Azure RTOS GUIX Studio. As fontes podem ser geradas em formatos monocromáticos ou anti-aliased, e são otimizadas para economizar espaço no alvo. Os tipos de letra podem incluir qualquer conjunto de caracteres, incluindo caracteres Unicode para aplicações multilingues.

<img alt="Diagram of SGS-TUV Saar certification logo" class="alignnone size-full wp-image-1500" height="341" sizes="(max-width: 535px) 100vw, 535px" src="./media/overview/studio_screen_shot.png"/>

O Azure RTOS GUIX Studio facilita a importação de gráficos de ficheiros PNG ou JPG com conversão para Azure RTOS GUIX Pixelmaps para utilização no sistema-alvo. Muitos dos tipos de widgetS Azure RTOS GUIX são projetados para incorporar gráficos do utilizador para uma aparência e sensação personalizadas. Além disso, o Azure RTOS GUIX Studio permite personalizar as cores padrão e os estilos de desenho usados pelos widgets Azure RTOS GUIX, permitindo aos desenvolvedores sintonizar muito facilmente a aparência do Azure RTOS GUIX. Geração e manutenção de cadeias de aplicações é outra instalação incorporada do Azure RTOS GUIX Studio. Isto permite que os desenvolvedores desenhem uma aplicação usando uma língua para desenvolver, e de forma rápida e fácil adicionar suporte para idiomas adicionais após o lançamento do produto. Uma aplicação completa do Azure RTOS GUIX pode ser executada num ambiente de pc dentro do ambiente Azure RTOS GUIX Studio, permitindo uma geração rápida e fácil e demonstração de conceitos GUI, testes de fluxos de ecrã e observação de transições de ecrã e animações. Quando concluído, um design pode ser exportado como estruturas de dados C prontas para o alvo, prontas a ser compiladas e ligadas às bibliotecas Azure RTOS GUIX e Azure RTOS ThreadX.

Azure RTOS GUIX e Azure RTOS GUIX Studio suportam vários temas de recursos, permitindo que uma aplicação seja facilmente ressarsado em tempo de execução. Fontes, cores e pixelmaps podem ser alterados no tempo de execução com uma simples API.

Saiba mais sobre o GUIX Studio

### <a name="complete-win32-simulation"></a>Simulação completa do Win32

O Azure RTOS GUIX funciona num PC Windows, utilizando exatamente a mesma biblioteca de desenho que funciona no quadro-alvo. Com o Azure RTOS GUIX, pode construir e executar uma aplicação GUI no PC, e usar o mesmo código de aplicação no seu alvo para depuração rápida, prototipagem rápida, demonstração e operação alvo WYSIWYG.

### <a name="advanced-technology"></a>Tecnologia avançada

* A tecnologia avançada da Azure RTOS GUIX incorpora:
* Mistura alfa
* Anti-Aliasing
* Dimensionamento automático
* Compressão bitmap
* Mistura de lona
* Suporte widget personalizado
* Suporte de desenho diferido
* Apoio dithering
* Programação neutra endiana
* Suporte ao acelerador de hardware
* Suporte multilinguístico e codificação UTF-8
* Suporte de exibição e lona múltipla
* Recortes otimizados, desenho e manipulação de eventos
* Descodificador JPEG e PNG
* Esfolar e Temas
* Suporta monocromático através de 32 bits de cor verdadeira com formatos gráficos alfa
* Transições, Sprites e Suporte de Animação
* Simulação Win32
* Gestão de janelas, incluindo Viewports e manutenção de ordem Z
