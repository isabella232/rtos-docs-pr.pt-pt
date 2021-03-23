---
title: Guia do Utilizador do Azure RTOS GUIX
description: Este guia contém informações completas sobre o Azure RTOS GUIX, o produto GUI de alto desempenho da Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: b7af0fba59b599c9c8db3ab80a3271eacfd11992
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827290"
---
# <a name="about-guix-user-guide"></a>Sobre o Guia do Utilizador GUIX

Este guia contém informações completas sobre o Azure RTOS GUIX, o produto GUI de alto desempenho da Microsoft. Destina-se a desenvolvedores de software embutidos em tempo real familiarizados com conceitos básicos de GUI, Azure RTOS ThreadX e a linguagem de programação C.

## <a name="organization"></a>Organização

[Capítulo 1 - Introdução ao Azure RTOS GUIX](chapter-1.md)

[Capítulo 2 - Instalação e utilização do Azure RTOS GUIX](chapter-2.md)

[Capítulo 3 - Visão geral funcional do Azure RTOS GUIX](chapter-3.md)

[Capítulo 4 - Descrição dos Serviços Azure RTOS GUIX](chapter-4.md)

[Capítulo 5 - Azure RTOS GUIX Display Drivers](chapter-5.md)  

[Exemplo Azure RTOS GUIX](guix-example.md)

[Apêndice A - Azure RTOS GUIX Definições de cor](appendix-a.md)

[Apêndice B - Azure RTOS GUIX Formais de cores](appendix-b.md)

[Apêndice C - Azure RTOS GUIX Widget Styles](appendix-c.md)

[Apêndice D - Azure RTOS GUIX Brush, Canvas and Gradient Atributos](appendix-d.md)

[Apêndice E - Descrição do evento Azure RTOS GUIX](appendix-e.md)

[Apêndice F - Azure RTOS GUIX RTOS Serviços de Ligação](appendix-f.md)

[Apêndice G - Estrutura de FonteS DE FONTE Azure RTOS GUIX](appendix-g.md)

[Apêndice H - Azure RTOS GUIX Build-Time Bandeiras de configuração](appendix-h.md)

[Apêndice I - Azure RTOS GUIX Estruturas de Informação](appendix-i.md)

## <a name="guide-conventions"></a>Convenções-Guia

*Itálico* - O tipo de letra denota títulos de livro, enfatiza palavras importantes e indica variáveis.

**Boldface** - Typeface denota nomes de ficheiros, palavras-chave, e enfatiza ainda palavras e variáveis importantes.

> [!IMPORTANT]
> Os símbolos de informação chamam a atenção para informações importantes ou adicionais que possam afetar o desempenho ou a função.

## <a name="azure-rtos-guix-data-types"></a>Tipos de dados Azure RTOS GUIX

Além dos tipos de dados personalizados da estrutura de controlo Azure RTOS GUIX, existem vários tipos de dados especiais que são utilizados nas interfaces de chamada de serviço Azure RTOS GUIX. Estes tipos especiais de dados mapeiam diretamente para os tipos de dados do compilador C subjacente. Isto é feito para garantir a portabilidade entre diferentes compiladores C. A implementação exata é herdada da ThreadX e pode ser encontrada no ficheiro ***tx_port.h*** incluído na distribuição ThreadX.

Segue-se uma lista dos tipos de dados de chamada de chamada de serviço Azure RTOS GUIX e os seus significados associados:

| <!-- --> | <!-- --> |
| --------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **UINT**             | Número inteiro básico não assinado. Este tipo é mapeado para o mais conveniente tipo de dados não assinado.                                |
| **INT**              | Inteiro assinado básico. Este tipo é mapeado para o tipo de dados assinado mais conveniente.                                    |
| **ULONG**            | Tipo longo não assinado. Este tipo deve suportar dados não assinados de 32 bits.                                                      |
| **VAZIO**             | Quase sempre equivalente ao tipo vazio do compilador.                                                                 |
| **GX_CHAR**         | Na maioria das vezes, dactilografado como o compilador definido tipo de char.                                                               |
| **GX_BYTE**          | Tipo assinado de 8 bits.                                                                                                    |
| **GX_UBYTE**         | Tipo não assinado de 8 bits.                                                                                                  |
| **GX_VALUE**        | Tipo assinado de 16 ou 32 bits. Definido como necessário para o melhor desempenho no sistema alvo.                                |
| **GX_FIXED_VAL**   | Tipo de dados numéricos de ponto fixo.                                                                                        |
| **GX_RESOURCE_ID** | Tipo longo não assinado.                                                                                                   |
| **GX_COLOR**        | Tipo longo não assinado.                                                                                                   |
| **GX_STRING**       | Estrutura que contém \* GX_CHAR gx_string_ptr e gx_string_length UINT.                                          |
| **GX_POINT**        | Estrutura que contém gx_point_x e gx_point_y.                                                                   |
| **GX_RECTANGLE**    | Estrutura que contém campos de gx_rectangle_left, gx_rectangle_top, gx_rectangle_right e gx_rectangle_bottom. |
| **GX_GLYPH**        | Estrutura que contém métricas de glifo.                                                                                   |
| **GX_FONT**         | Estrutura que contém métricas de fonte.                                                                                    |
| **GX_BRUSH**        | Estrutura que contém métricas de pincel.                                                                               |
**GX_PIXELMAP**       | Estrutura que contém métricas de pixelmap.

Tipos de dados adicionais são utilizados dentro da fonte Azure RTOS GUIX. Estão localizados nos ficheiros ***tx_port.h_** ou _ *_gx_port.h*_*

## <a name="customer-support-center"></a>Centro de Apoio ao Cliente

Por favor envie um bilhete de apoio através do Portal Azure para perguntas ou ajuda a usar os passos aqui. Por favor, forneça-nos as seguintes informações numa mensagem de correio eletrónico para que possamos resolver de forma mais eficiente o seu pedido de apoio:

1. Uma descrição pormenorizada do problema, incluindo a frequência da ocorrência e se pode ser reproduzida de forma fiável.

2. Uma descrição detalhada de quaisquer alterações à aplicação e/ou Azure RTOS GUIX que precederam o problema.

3. O conteúdo das cordas _tx_version_id e _gx_version_id encontradas nos ficheiros ***tx_port.h**_ e _ *_gx_port.h*_* da sua distribuição. Estas cordas fornecer-nos-ão informações valiosas sobre o seu ambiente de tempo de execução.

4. O conteúdo em RAM das seguintes variáveis ULONG:

    **_tx_build_options** **_gx_system_build_options**

    Estas variáveis dar-nos-ão informações sobre como as suas bibliotecas Azure RTOS ThreadX e Azure RTOS GUIX foram construídas.

5. O conteúdo em RAM das seguintes variáveis ULONG:

    **_gx_system_last_error** **_gx_system_error_count**

    Estas variáveis acompanham os erros internos do sistema no Azure RTOS GUIX. Se o _gx_system_error_count for maior do que um, por favor, desaponte um ponto de rutura na revolução da função na função _gx_system_error_process e forneça o valor de _gx_system_last_error neste ponto. Isto irá produzir o primeiro erro interno do sistema Azure RTOS GUIX.

6. Um tampão de vestígio capturado imediatamente após o problema ter sido detetado. Isto é conseguido construindo as bibliotecas Azure RTOS ThreadX e Azure RTOS GUIX com TX_ENABLE_EVENT_TRACE e chamando tx_trace_enable com a informação do tampão de traços.

7. O projeto Azure RTOS GUIX Studio que está a utilizar, se aplicável, ou no mínimo um pequeno projeto suficiente para demonstrar a deficiência que está a reportar.
