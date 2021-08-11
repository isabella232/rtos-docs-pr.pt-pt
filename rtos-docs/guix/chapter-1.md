---
title: Capítulo 1 - Introdução ao GUIX
description: GUIX é uma implementação em tempo real de alto desempenho de um (GUI) projetado exclusivamente para aplicações incorporadas baseadas em Azure RTOS ThreadX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e85aab43ba803212875f1fef3ba0bee8484c25b015e400d3b927d492177202b8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784122"
---
# <a name="chapter-1---introduction-to-azure-rtos-guix"></a>Capítulo 1 - Introdução ao Azure RTOS GUIX

Azure RTOS GUIX (GUIX) é uma implementação em tempo real de alto desempenho de uma estrutura de interface gráfica projetada exclusivamente para aplicações incorporadas baseadas em ThreadX. Este capítulo contém uma introdução ao GUIX e uma descrição das suas aplicações e benefícios.

## <a name="guix-feature-overview"></a>Visão geral do recurso GUIX

Ao contrário de muitas outras implementações do GUI, o GUIX foi concebido para ser versátil — facilmente dimensionando de pequenas aplicações baseadas em microcontrolador para aquelas que utilizam poderosos processadores RISC e DSP. Isto contrasta fortemente com o domínio público ou outras implementações comerciais originalmente destinadas a ambientes de estações de trabalho, mas depois espremidas em desenhos incorporados. Segue-se uma visão geral das funcionalidades do GUIX:

- Fácil de usar com ferramenta de design baseada em anfitrião GUIX Studio

- Win32 GUIX ambiente de tempo de execução para prototipagem completa hospedada

- Suporta a maioria dos processadores suportados pela ThreadX

- Escrito exclusivamente em ANSI C

- Endian neutro

- GUI mais pequeno e embelho embutido

- Tempo de execução configurável, número de objetos, tamanho do ecrã, etc.

- Fácil de escrever interface do controlador de exibição

- Cor (até 32 bpp profundidade de cor), monocromático e suporte à escala de cinza

- Suporte multilinguístico através da codificação de cordas UTF8 e recursos de cordas

- Fontes gratuitas padrão e fácil de adicionar novos tipos de letra

- Telas de desenho múltipla suportadas, de vários tamanhos

- Múltiplas exibições de diferentes tamanhos e profundidades de cor suportadas

- Suporte para a transição do ecrã (desvanecer-se, desvanecer-se, passar, etc.)

- Ecrã tátil, gesto e suporte virtual do teclado

- Compressão bitmap

- Suporte de mistura alfa

- Apoio dither

- Apoio Anti-Aliasing

- Esfolar e Temas

- Mistura de tela

- Gestão completa da janela

  - Relação pai/filho

  - Criação dinâmica, eliminação, redimensionamento, movimento
  - Manipulação e desenho de eventos separados 
  - Ordenação Z
  - Recortes e vistas

- Conjunto extensivo de widgets

  - Vários tipos de botões, sliders e mostradores

  - Lista de drop down
  
  - Prompt

  - Vista de texto multi-linha
  
  - Entrada de texto simples e multi-linha
  
  - Rodas de pergaminho numérico e textual
  
  - barras de Windows e pergaminhos
  
  - Barra de Progresso Radial
  
  - Sprite

### <a name="ansi-c-source-code"></a>Código Fonte ANSI C

GUIX é escrito completamente em ANSI C e é portátil imediatamente para praticamente qualquer arquitetura de processador que tenha um compilador ANSI C e suporte ThreadX. Embora escrito em ANSI C, GUIX usa um modelo e herança orientados para objetos.

### <a name="not-a-black-box"></a>Não uma caixa preta

A maioria das distribuições do GUIX incluem o código fonte C completo. Isto elimina os problemas da "caixa preta" que ocorrem com muitas implementações comerciais do GUI. Ao usar o GUIX, os desenvolvedores de aplicações podem ver exatamente o que o GUI está a fazer - não há mistérios!

Ter o código fonte também permite modificações específicas da aplicação. Embora não recomendado, é certamente benéfico ter a capacidade de modificar o GUI se for necessário. Estas funcionalidades são especialmente reconfortantes para os desenvolvedores habituados a trabalhar com produtos de domínio interno ou público. Esperam ter código fonte e a capacidade de modificá-lo. GUIX é o software GUI final para tais desenvolvedores.

## <a name="embedded-gui-applications"></a>Aplicações GUI incorporadas

As aplicações GUI incorporadas são aplicações que têm um requisito de interface de utilizador e executam em microprocessadores escondidos dentro de produtos como telemóveis, equipamentos de comunicação, motores automóveis, impressoras a laser, dispositivos médicos, etc. Tais aplicações têm quase sempre algumas restrições de memória e desempenho. Outra distinção do GUI incorporado é que o seu software e hardware têm um propósito dedicado.

### <a name="real-time-gui-software"></a>Software GUI em tempo real

Basicamente, o software GUI que deve realizar o seu processamento dentro de um período exato de tempo é chamado de software *GUI em tempo real,* e quando as restrições de tempo são impostas às aplicações GUI, são classificadas como aplicações em tempo real. As aplicações GUI incorporadas são quase sempre em tempo real devido à sua interação inerente com o mundo externo.

## <a name="guix-benefits"></a>Benefícios GUIX

Os principais benefícios da utilização do GUIX para aplicações incorporadas são os requisitos de alta performance, características ricas e muito pequenas necessidades de memória. O GUIX também está completamente integrado com o sistema operativo de alto desempenho, multitasking Azure RTOS ThreadX em tempo real.

### <a name="improved-responsiveness"></a>Melhor capacidade de resposta

O produto GUIX de alto desempenho permite que as aplicações respondam mais rapidamente do que nunca. Isto é especialmente importante para aplicações incorporadas que tenham um volume significativo de informações visuais ou requisitos rigorosos de tempo na exibição dessas informações.

### <a name="software-maintenance"></a>Manutenção de Software

A utilização do GUIX permite que os desenvolvedores partilhem facilmente os aspetos GUI da sua aplicação incorporada. Esta partição torna todo o processo de desenvolvimento fácil e aumenta significativamente a manutenção futura do software.

### <a name="increased-throughput"></a>Aumento da produção

O GUIX fornece o GUI de maior desempenho disponível, que transfere diretamente para a aplicação incorporada. As aplicações GUIX são capazes de processar informações de interface de utilizador mais rapidamente do que aplicações não GUIX!

### <a name="processor-isolation"></a>Isolamento do processador

O GUIX fornece uma interface robusta e independente entre a aplicação e o hardware de exibição e processador subjacente. Isto permite que os desenvolvedores se concentrem nos aspetos de alto nível da interface do utilizador em vez de gastarem tempo extra a lidar com problemas de hardware de exibição.

### <a name="ease-of-use"></a>Facilidade de utilização

O GUIX foi concebido tendo em mente o desenvolvedor de aplicações. A arquitetura GUIX e a interface de chamada de serviço são fáceis de entender. Como resultado, os desenvolvedores GUIX podem usar rapidamente as suas funcionalidades avançadas.

### <a name="improve-time-to-market"></a>Melhorar o tempo para o mercado

As poderosas características do GUIX aceleram o processo de desenvolvimento de software. O GUIX abstrata a maioria dos problemas de processador e de ecrã de hardware, removendo assim estas preocupações da maioria da implementação da interface do utilizador da aplicação. Esta funcionalidade, aliada à facilidade de utilização e ao conjunto de funcionalidades avançadas, resulta num tempo mais rápido para o mercado!

### <a name="protecting-the-software-investment"></a>Proteger o Investimento em Software

O GUIX é escrito exclusivamente em ANSI C e está totalmente integrado com o sistema operativo Azure RTOS ThreadX em tempo real. Isto significa que as aplicações GUIX são instantaneamente portáteis para todos os processadores suportados pela ThreadX. Melhor ainda, uma arquitetura de processador completamente nova pode ser suportada com a ThreadX em questão de semanas. Como resultado, a utilização do GUIX garante a trajetória de migração da aplicação e protege o investimento original de desenvolvimento.
