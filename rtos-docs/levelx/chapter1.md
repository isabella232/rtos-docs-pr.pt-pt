---
title: Capítulo 1 - Visão geral do Azure RTOS LevelX
description: O Azure RTOS LevelX fornece instalações de nivelamento de desgaste NAND e NOR flash para aplicações incorporadas.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 73c06d48b98081291d83635e049e6cf8641714c87efe815f9399f3fbab3a6211
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790603"
---
# <a name="chapter-1---overview-of-azure-rtos-levelx"></a>Capítulo 1 - Visão geral do Azure RTOS LevelX

O Azure RTOS LevelX fornece instalações de nivelamento de desgaste NAND e NOR flash para aplicações incorporadas. Uma vez que tanto a memória flash NAND como a NOR só podem ser apagadas um número finito de vezes, é fundamental distribuir o uso da memória flash uniformemente. Isto é tipicamente chamado de "nivelamento de desgaste" e é o propósito por trás do LevelX.

O algoritmo que escolhe qual o bloco flash para reutilizar baseia-se principalmente na contagem de apagamento, mas não inteiramente. O bloco com a contagem de apagamento mais baixa pode não ser escolhido se houver outro bloco que tenha uma contagem de apagamento dentro de um delta aceitável da contagem mínima de apagamento e que tenha um maior número de mapeamentos obsoletos. Nesses casos, o bloco com o maior número de mapeamentos obsoletos será apagado e reutilizado, poupando assim a sobrecarga na movimentação de entradas de mapeamento válidos.

O LevelX suporta múltiplas instâncias de peças NAND e/ou NOR, ou seja, a aplicação pode utilizar instâncias separadas do LevelX dentro da mesma aplicação. Cada instância requer o seu próprio bloco de controlo fornecido pela aplicação, bem como o seu próprio flash driver.

O LevelX apresenta ao utilizador uma série de sectores lógicos que são mapeados para a memória flash física dentro do LevelX. Para melhorar o desempenho, o LevelX também fornece uma cache dos mais recentes mapeamentos do setor lógico. O tamanho desta cache é definido pelo programador. As aplicações podem utilizar o LevelX em conjunto com o FileX ou podem ler/escrever diretamente sectores lógicos. O LevelX não tem dependência do FileX e muito pouca dependência da ThreadX (apenas são utilizados tipos de dados primitivos da ThreadX).

O LevelX foi concebido para a tolerância à falha. As atualizações flash são executadas num processo de várias etapas que pode ser interrompido em cada passo. O LevelX recupera automaticamente para o estado ideal durante a próxima operação.

O LevelX requer um flash driver para acesso físico à memória flash subjacente. Exemplo, os condutores simulados NAND e NOR são fornecidos e podem ser usados como um bom ponto de partida para a implementação de condutores atuais do LevelX. Além disso, os requisitos do condutor são detalhados mais tarde nesta documentação.

Os capítulos seguintes descrevem a operação funcional para o suporte NAND e NOR LevelX.
