---
title: Guia de utilizador do estúdio GUIX
description: Este guia fornece informações completas sobre o GUIX Studio, o ambiente de desenvolvimento rápido de UI baseado no Microsoft, especificamente concebido para a biblioteca de tempo de execução GUIX da Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 6a5d628581d4c6b44ff093bac45790d6e2755349
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827170"
---
# <a name="chapter-1-introduction-to-azure-rtos-guix-studio"></a>Capítulo 1: Introdução ao Azure RTOS GUIX Studio

Azure RTOS GUIX Studio é um ambiente de desenvolvimento rápido de UI baseado no Microsoft, especificamente concebido para a biblioteca de tempo de execução GUIX da Microsoft.

Os Desenvolvedores de UI incorporados podem utilizar o designer de ecrã GUIX Studio WYSIWYG para criar e atualizar rapidamente a sua UI incorporada utilizando o ambiente de tempo de execução GUIX. Os designs do GUIX Studio são guardados e mantidos num ficheiro de projeto guix Studio, que tem a extensão .gxp. Quando o seu design está pronto para ser executado no alvo, o GUIX Studio gera código C que contém todas as informações e códigos de UI necessários.

## <a name="guix-studio-requirements"></a>Requisitos do estúdio GUIX

Para funcionar corretamente, o ESTÚDIO GUIX da Microsoft requer *o Windows XP* (ou acima). O sistema deve ter um mínimo de 200MB de RAM, 2GB de espaço em disco rígido disponível e um ecrã mínimo de 1024x768 com 256 cores. Além disso, a aplicação incorporada deve estar em execução no *ThreadX/GUIX V6.0* ou mais tarde.

Se quiser ser capaz de construir e executar a aplicação de UI incorporada como um Microsoft Windows autónomo executável, também precisará de um compilador ou criar um ambiente capaz de compilar código fonte C para produzir um Microsoft Windows executável. O pacote de avaliação incluído no GUIX Studio também inclui ficheiros de projeto compatíveis com o Visual Studio 2019 e soluções para cada uma das aplicações de exemplo fornecidas. Se estiver a utilizar um compilador diferente, terá de criar os seus próprios ficheiros de projeto ou de fazer ficheiros para efeitos de construção das suas aplicações de exemplo ou suporte de contacto em https://aka.ms/azrtos-support .

## <a name="guix-studio-constraints"></a>Restrições do estúdio GUIX

A ferramenta de design GUIX Studio UI tem vários constrangimentos, da seguinte forma:

- Um máximo de 4 exposições por projeto.
- Um máximo de 100.000 widgets por projeto GUIX Studio.
- Um máximo de 100.000 recursos distintos, por exemplo, cores, fontes, pixelmaps, cordas, etc.