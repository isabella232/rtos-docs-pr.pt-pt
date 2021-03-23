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
# <a name="chapter-1-introduction-to-azure-rtos-guix-studio"></a><span data-ttu-id="c10e7-103">Capítulo 1: Introdução ao Azure RTOS GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="c10e7-103">Chapter 1: Introduction to Azure RTOS GUIX Studio</span></span>

<span data-ttu-id="c10e7-104">Azure RTOS GUIX Studio é um ambiente de desenvolvimento rápido de UI baseado no Microsoft, especificamente concebido para a biblioteca de tempo de execução GUIX da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c10e7-104">Azure RTOS GUIX Studio is a Microsoft Windows-based rapid UI development environment specifically designed for the GUIX runtime library from Microsoft.</span></span>

<span data-ttu-id="c10e7-105">Os Desenvolvedores de UI incorporados podem utilizar o designer de ecrã GUIX Studio WYSIWYG para criar e atualizar rapidamente a sua UI incorporada utilizando o ambiente de tempo de execução GUIX.</span><span class="sxs-lookup"><span data-stu-id="c10e7-105">Embedded UI Developers can utilize the GUIX Studio WYSIWYG screen designer to quickly create and update their embedded UI using the GUIX run-time environment.</span></span> <span data-ttu-id="c10e7-106">Os designs do GUIX Studio são guardados e mantidos num ficheiro de projeto guix Studio, que tem a extensão .gxp.</span><span class="sxs-lookup"><span data-stu-id="c10e7-106">GUIX Studio designs are saved and maintained in a GUIX Studio project file, which has the extension .gxp.</span></span> <span data-ttu-id="c10e7-107">Quando o seu design está pronto para ser executado no alvo, o GUIX Studio gera código C que contém todas as informações e códigos de UI necessários.</span><span class="sxs-lookup"><span data-stu-id="c10e7-107">When your design is ready for execution on the target, GUIX Studio generates C code that contains all the necessary UI information and code.</span></span>

## <a name="guix-studio-requirements"></a><span data-ttu-id="c10e7-108">Requisitos do estúdio GUIX</span><span class="sxs-lookup"><span data-stu-id="c10e7-108">GUIX Studio Requirements</span></span>

<span data-ttu-id="c10e7-109">Para funcionar corretamente, o ESTÚDIO GUIX da Microsoft requer *o Windows XP* (ou acima).</span><span class="sxs-lookup"><span data-stu-id="c10e7-109">In order to function properly, Microsoft's GUIX Studio requires *Windows XP* (or above).</span></span> <span data-ttu-id="c10e7-110">O sistema deve ter um mínimo de 200MB de RAM, 2GB de espaço em disco rígido disponível e um ecrã mínimo de 1024x768 com 256 cores.</span><span class="sxs-lookup"><span data-stu-id="c10e7-110">The system should have a minimum of 200MB of RAM, 2GB of available hard-disk space, and a minimum display of 1024x768 with 256 colors.</span></span> <span data-ttu-id="c10e7-111">Além disso, a aplicação incorporada deve estar em execução no *ThreadX/GUIX V6.0* ou mais tarde.</span><span class="sxs-lookup"><span data-stu-id="c10e7-111">In addition, the embedded application must be running on *ThreadX/GUIX V6.0* or later.</span></span>

<span data-ttu-id="c10e7-112">Se quiser ser capaz de construir e executar a aplicação de UI incorporada como um Microsoft Windows autónomo executável, também precisará de um compilador ou criar um ambiente capaz de compilar código fonte C para produzir um Microsoft Windows executável.</span><span class="sxs-lookup"><span data-stu-id="c10e7-112">If you would like to be able to build and run the embedded UI application as a stand-alone Microsoft Windows executable, you will also need a compiler or build environment capable of compiling C source code to produce a Microsoft Windows executable.</span></span> <span data-ttu-id="c10e7-113">O pacote de avaliação incluído no GUIX Studio também inclui ficheiros de projeto compatíveis com o Visual Studio 2019 e soluções para cada uma das aplicações de exemplo fornecidas.</span><span class="sxs-lookup"><span data-stu-id="c10e7-113">The evaluation package included with GUIX Studio also includes Visual Studio 2019 compatible project files and solutions for each of the provided example applications.</span></span> <span data-ttu-id="c10e7-114">Se estiver a utilizar um compilador diferente, terá de criar os seus próprios ficheiros de projeto ou de fazer ficheiros para efeitos de construção das suas aplicações de exemplo ou suporte de contacto em https://aka.ms/azrtos-support .</span><span class="sxs-lookup"><span data-stu-id="c10e7-114">If you are using a different compiler, you will need to create your own project files or make files for the purposes of building your example applications, or contact support at https://aka.ms/azrtos-support.</span></span>

## <a name="guix-studio-constraints"></a><span data-ttu-id="c10e7-115">Restrições do estúdio GUIX</span><span class="sxs-lookup"><span data-stu-id="c10e7-115">GUIX Studio Constraints</span></span>

<span data-ttu-id="c10e7-116">A ferramenta de design GUIX Studio UI tem vários constrangimentos, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="c10e7-116">The GUIX Studio UI design tool has several constraints, as follows:</span></span>

- <span data-ttu-id="c10e7-117">Um máximo de 4 exposições por projeto.</span><span class="sxs-lookup"><span data-stu-id="c10e7-117">A maximum of 4 displays per project.</span></span>
- <span data-ttu-id="c10e7-118">Um máximo de 100.000 widgets por projeto GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="c10e7-118">A maximum of 100,000 widgets per GUIX Studio project.</span></span>
- <span data-ttu-id="c10e7-119">Um máximo de 100.000 recursos distintos, por exemplo, cores, fontes, pixelmaps, cordas, etc.</span><span class="sxs-lookup"><span data-stu-id="c10e7-119">A maximum of 100,000 distinct resources, e.g., colors, fonts, pixelmaps, strings, etc.</span></span>