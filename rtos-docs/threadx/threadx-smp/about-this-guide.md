---
title: Sobre Este Manual
description: Este guia fornece informações completas sobre o Azure RTOS ThreadX SMP, o kernel de alto desempenho incorporado pela Microsoft em tempo real.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6a8758bff2f205b06448905634172c05dd7fe189cce9fbe3977f6080c51eb95d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784789"
---
# <a name="about-this-guide"></a>Sobre Este Manual

Este guia fornece informações completas sobre o Azure RTOS ThreadX SMP, o kernel de alto desempenho incorporado pela Microsoft em tempo real.

Destina-se ao desenvolvedor de software incorporado em tempo real. O desenvolvedor deve estar familiarizado com as funções padrão do sistema operativo em tempo real e com a linguagem de programação C.

## <a name="organization"></a>Organização

| Capítulo       | Descrição Geral                    |
| ------------- | ---------------------------------------------------------------------------------------------------------- |
| **Capítulo 1** | Fornece uma visão geral básica da ThreadX SMP e a sua relação com o desenvolvimento incorporado em tempo real.           |
| **Capítulo 2** | Dá os passos básicos para instalar e utilizar o ThreadX SMP na sua aplicação *logo a partir da caixa.*           |
| **Capítulo 3** | Descreve em detalhe o funcionamento da ThreadX SMP, o núcleo SMP em tempo real de alto desempenho.    |
| **Capítulo 4** | Detalha a interface da aplicação com a ThreadX SMP.                                                        |
| **Capítulo 5** | Descreve a escrita de controladores de E/S para aplicações SMP ThreadX.                                                |
| **Capítulo 6** | Descreve a aplicação de demonstração que é fornecida com todos os pacotes de suporte ao processador ThreadX SMP. |
| **Anexo A** | ThreadX SMP API        |
| **Apêndice B** | ThreadX SMP constantes  |
| **Apêndice C** | Tipos de dados ThreadX SMP |
| **Apêndice D** | Gráfico ASCII            |

## <a name="guide-conventions"></a>Convenções-Guia

- *Itálico*  -  *typeface denota títulos de livro, enfatiza palavras importantes, e indica variáveis.*
- **Negrito**  -  **o tipo de letra denota nomes de ficheiros, palavras-chave e enfatiza ainda palavras e variáveis importantes.**

> [!IMPORTANT]
> Os símbolos de informação chamam a atenção para informações importantes ou adicionais que possam afetar o desempenho ou a função.

> [!WARNING]
> Os símbolos de aviso chamam a atenção para situações em que os desenvolvedores devem ter o cuidado de evitar porque podem causar erros fatais.

## <a name="threadx-smp-data-types"></a>Tipos de dados SMP ThreadX

Além dos tipos de dados personalizados da estrutura de controlo ThreadX SMP, existem uma série de tipos especiais de dados que são utilizados nas interfaces de chamada de serviço ThreadX SMP. Estes tipos especiais de dados mapeiam diretamente para os tipos de dados do compilador C subjacente. Isto é feito para garantir a portabilidade entre diferentes compiladores C. A implementação exata pode ser encontrada no ficheiro ***tx_port.h*** incluído no disco de distribuição.

Segue-se uma lista dos tipos de dados de chamadas de serviço threadX SMP e os seus significados associados:

| Tipo de Dados          | Significado                                                          |
| --------- | --------------------------------------------------------- |
| **UINT**  | Número inteiro básico não assinado. Este tipo deve suportar dados não assinados de 8 bits; no entanto, é mapeado para o mais conveniente tipo de dados não assinado. |
| **ULONG** | Tipo longo não assinado. Este tipo deve suportar dados não assinados de 32 bits.                                                                     |
| **VAZIO**  | Quase sempre equivalente ao tipo vazio do compilador.                                                                                |
| **CHAR**  | Na maioria das vezes, um tipo de caracteres padrão de 8 bits.                                                                                          |

Tipos de dados adicionais são utilizados dentro da fonte SMP ThreadX. Também estão localizados no ficheiro ***tx_port.h.***

## <a name="customer-support-center"></a>Centro de Apoio ao Cliente

E-mail de suporte: [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) Página web: azure.com/rtos

### <a name="latest-product-information"></a>Últimas Informações sobre o Produto

Visite o site azure.com/rtos e selecione a opção de menu "Suporte" para encontrar as últimas informações de suporte on-line, incluindo informações sobre as mais recentes versões do produto ThreadX SMP.

### <a name="what-we-need-from-you"></a>O que precisamos de si

Por favor, forneça-nos as seguintes informações numa mensagem de correio eletrónico para que possamos resolver de forma mais eficiente o seu pedido de apoio:

1. Uma descrição pormenorizada do problema, incluindo a frequência da ocorrência e se pode ser reproduzida de forma fiável.
2. Uma descrição detalhada de quaisquer alterações à aplicação e/ou ThreadX SMP que precederam o problema.
3. O conteúdo da cadeia ***_tx_version_id** _ encontrada no ficheiro _ *_tx_port.h*_* da sua distribuição. Esta corda fornecer-nos-á informações valiosas sobre o seu ambiente de tempo de execução.
4. O conteúdo em RAM da ***_tx_build_options*** variável ULONG. Esta variável vai dar-nos informações sobre como a sua biblioteca ThreadX SMP foi construída.

### <a name="where-to-send-comments-about-this-guide"></a>Para onde enviar comentários sobre este guia

Envie por e-mail quaisquer comentários e sugestões para o Centro de Apoio ao Cliente [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) na Introdução "ThreadX SMP User Guide" na linha de assunto.
