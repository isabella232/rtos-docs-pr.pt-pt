---
title: Guia de utilizador Azure RTOS FileX
description: Este guia contém informações completas sobre o Azure RTOS FileX, o sistema de ficheiros em tempo real de alto desempenho da Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 640d9ed4c8037d3af6c5f45158c9496ad1258a3c
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550104"
---
# <a name="about-this-filex-user-guide"></a>Sobre este Guia de Utilizador FileX

Este guia contém informações completas sobre o Azure RTOS FileX, o sistema de ficheiros incorporado em tempo real de alto desempenho da Microsoft. Para obter o máximo deste guia, deve estar familiarizado com as funções padrão do sistema operativo em tempo real, os serviços do sistema de ficheiros FAT e a linguagem de programação C.

## <a name="organization"></a>Organização

[Capítulo 1](chapter1.md) - Introduz Azure RTOS FileX

[Capítulo 2](chapter2.md) - Dá os passos básicos para instalar e utilizar o Azure RTOS FileX com a sua aplicação Azure RTOS ThreadX

[Capítulo 3](chapter3.md) - Fornece uma visão geral funcional do sistema Azure RTOS FileX e informações básicas sobre formatos de sistema de ficheiros FAT

[Capítulo 4](chapter4.md) - Detalha a interface da aplicação com o Azure RTOS FileX

[Capítulo 5](chapter5.md) - Descreve o controlador RAM Azure RTOS FileX fornecido e como escrever os seus próprios controladores Azure RTOS FileX

[Capítulo 6](chapter6.md) - Descreve o Módulo Tolerante com Falhas de Falhas de FicheiroS RTOS Azure

[Apêndice A](appendix-a.md) - Serviços de Arquivo RTOS Azure

[Apêndice B](appendix-b.md) - Azure RTOS FileX Constants

[Apêndice C](appendix-c.md) - Azure RTOS FileX Data Types

[Apêndice D](appendix-d.md) - Gráfico ASCII

## <a name="guide-conventions"></a>Convenções-Guia

*Itálico* - O tipo de letra denota títulos de livro, enfatiza palavras importantes e indica variáveis.

**Boldface** - Typeface denota nomes de ficheiros, palavras-chave, e enfatiza ainda palavras e variáveis importantes.

> [!NOTE]
> Os símbolos de informação chamam a atenção para informações importantes ou adicionais que possam afetar o desempenho ou a função.

> [!IMPORTANT]
> Os símbolos de aviso chamam a atenção para situações que os desenvolvedores devem evitar porque podem causar erros fatais.

## <a name="filex-data-types"></a>Tipos de dados filex

Além dos tipos de dados personalizados da estrutura de controlo Azure RTOS FileX, existe uma série de tipos especiais de dados que são utilizados nas interfaces de chamada de serviço Azure RTOS FileX. Estes tipos especiais de dados mapeiam diretamente para os tipos de dados do compilador C subjacente. Isto é feito para garantir a portabilidade entre diferentes compiladores C. A implementação exata é herdada da Azure RTOS ThreadX e pode ser encontrada no ficheiro tx_port.h incluído na distribuição Azure RTOS ThreadX.

Segue-se uma lista dos tipos de dados de chamada de chamada de serviço Azure RTOS FileX e os seus significados associados.

| Tipo  | Descrição  |
|---|---|
| **UINT** | Número inteiro básico não assinado. Este tipo deve suportar dados não assinados de 8 bits; no entanto, é mapeado para o mais conveniente tipo de dados não assinado. |
| **ULONG** | Tipo longo não assinado. Este tipo deve suportar dados não assinados de 32 bits. |
| **VAZIO** | Quase sempre equivalente ao tipo vazio do compilador. |
| **CHAR** | Na maioria das vezes, um tipo de caracteres padrão de 8 bits. |
| **ULONG64** | Tipo de dados inteiros não assinados de 64 bits. |

Tipos de dados adicionais são utilizados dentro da fonte FileX. Estão localizados nos ficheiros ***tx_port.h_** ou _ *_fx_port.h*_*

## <a name="customer-support-center"></a>Centro de Apoio ao Cliente

Por favor envie um bilhete de apoio através do Portal Azure para perguntas ou ajuda a usar os passos aqui. Por favor, forneça-nos as seguintes informações numa mensagem de correio eletrónico para que possamos resolver de forma mais eficiente o seu pedido de apoio.

1. Uma descrição pormenorizada do problema, incluindo a frequência da ocorrência e se pode ser reproduzida de forma fiável.
2. Uma descrição detalhada de quaisquer alterações à aplicação e/ou FileX que precederam o problema.
3. O conteúdo das cordas _tx_version_id e _fx_version_id encontrado nos ficheiros ***tx_port.h**_ e _ *_fx_port.h*_* da sua distribuição. Estas cordas fornecer-nos-ão informações valiosas sobre o seu ambiente de tempo de execução.
4. O conteúdo em RAM das seguintes variáveis **ULONG.** Estas variáveis dar-nos-ão informações sobre como as suas bibliotecas ThreadX e FileX foram construídas:

    **_tx_build_options**

    **_fx_system_build_options1**

    **_fx_system_build_options2**

    **_fx_system_build_options3**
