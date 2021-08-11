---
title: Apêndice C - Utilitários de linha de comando DOS
description: Existem três utilitários de linha de comando DOS encontrados na instalação Azure RTOS TraceX sob a subdiretório Utilities.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 1a89f8be7e21e416659b904f0ec5b2a3a8f666cdb9a861786e652a38564db48f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791555"
---
# <a name="appendix-c---dos-command-line-utilities"></a>Apêndice C - Utilitários de linha de comando DOS

Existem três utilitários de linha de comando DOS encontrados na instalação TraceX sob a subdiretório ***Utilities.***

Os utilitários fornecidos estão listados abaixo:

| **Utilitário**                              | **Objetivo**                               | **Definições de linha de comando** |
| -------------------------------- | ----------------------------------------- | ---------------------------- |
| **ea2tracex.exe**                | Converte o trace file ea2tracex gerado pela ThreadX em original_file associação com as ferramentas GHS converted_file ao formato trace-file TraceX. O ThreadX para ferramentas GHS produz um formato de traço diferente do ThreadX para ferramentas não GHS, razão pela qual este utilitário de conversão é necessário. | ``` > eatracex original_file converted_file <cr> ``` | 
**hex2tracex.exe** | Converte um ficheiro de traços gerado pela ThreadX mas despejado da ferramenta de desenvolvimento no formato Intel HEX para o formato binário de ficheiro trace TraceX. O TraceX V5 e acima podem abrir ficheiros HEX sem os converter. | ``` hex2tracex hex_file converted_file <cr> ``` | 
**mot2tracex.exe** | Converte um ficheiro de traços gerado pela ThreadX mas despejado da ferramenta de desenvolvimento no formato Motorola S-Record para o formato binário de ficheiro trace TraceX. O TraceX V5 e acima podem abrir ficheiros S-Record sem os converter. | ``` > mot2tracex mot_file converted_file <cr> ```|