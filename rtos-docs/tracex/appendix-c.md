---
title: Apêndice C - Utilitários de linha de comando DOS
description: Existem três utilitários de linha de comando DOS encontrados na instalação Azure RTOS TraceX sob a subdiretório Utilities.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: e1ec852a97a6735a4a055706f55283950d3f8d6b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827823"
---
# <a name="appendix-c---dos-command-line-utilities"></a>Apêndice C - Utilitários de linha de comando DOS

Existem três utilitários de linha de comando DOS encontrados na instalação TraceX sob a subdiretório ***Utilities.***

Os utilitários fornecidos estão listados abaixo:

| **Utilitário**                              | **Objetivo**                               | **Definições de linha de comando** |
| -------------------------------- | ----------------------------------------- | ---------------------------- |
| **ea2tracex.exe**                | Converte o trace file ea2tracex gerado pela ThreadX em original_file associação com as ferramentas GHS converted_file ao formato trace-file TraceX. O ThreadX para ferramentas GHS produz um formato de traço diferente do ThreadX para ferramentas não GHS, razão pela qual este utilitário de conversão é necessário. | ``` > eatracex original_file converted_file <cr> ``` | 
**hex2tracex.exe** | Converte um ficheiro de traços gerado pela ThreadX mas despejado da ferramenta de desenvolvimento no formato Intel HEX para o formato binário de ficheiro trace TraceX. O TraceX V5 e acima podem abrir ficheiros HEX sem os converter. | ``` hex2tracex hex_file converted_file <cr> ``` | 
**mot2tracex.exe** | Converte um ficheiro de traços gerado pela ThreadX mas despejado da ferramenta de desenvolvimento no formato Motorola S-Record para o formato binário de ficheiro trace TraceX. O TraceX V5 e acima podem abrir ficheiros S-Record sem os converter. | ``` > mot2tracex mot_file converted_file <cr> ```|