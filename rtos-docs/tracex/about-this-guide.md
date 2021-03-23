---
title: Guia de utilizador Azure RTOS TraceX
description: Este guia contém informações completas sobre o Azure RTOS TraceX, a ferramenta de análise de sistema baseada no Microsoft.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 92d886b19a0c67292cd4f6a5f8bd7f9d3106374b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827871"
---
# <a name="about-this-guide"></a><span data-ttu-id="f92d6-103">Acerca deste guia</span><span class="sxs-lookup"><span data-stu-id="f92d6-103">About this guide</span></span>

<span data-ttu-id="f92d6-104">Este guia contém informações completas sobre o Azure RTOS TraceX, a ferramenta de análise de sistema baseada no Microsoft Windows para o Microsoft Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="f92d6-104">This guide contains comprehensive information about Azure RTOS TraceX, the Microsoft Windows-based system analysis tool for Microsoft Azure RTOS.</span></span>

<span data-ttu-id="f92d6-105">Destina-se ao desenvolvedor de software incorporado em tempo real utilizando O Azure RTOS ThreadX Real-Time Sistema Operativo (RTOS) e componentes adicionais.</span><span class="sxs-lookup"><span data-stu-id="f92d6-105">It is intended for the embedded real-time software developer using Azure RTOS ThreadX Real-Time Operating System (RTOS) and add-on components.</span></span> <span data-ttu-id="f92d6-106">O desenvolvedor deve estar familiarizado com os conceitos padrão Azure RTOS ThreadX Azure RTOS FileX e Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="f92d6-106">The developer should be familiar with standard Azure RTOS ThreadX Azure RTOS FileX, and Azure RTOS NetX concepts.</span></span>

## <a name="organization"></a><span data-ttu-id="f92d6-107">Organização</span><span class="sxs-lookup"><span data-stu-id="f92d6-107">Organization</span></span>

- <span data-ttu-id="f92d6-108">[Capítulo 1](chapter1.md) - contém uma visão geral básica do Azure RTOS TraceX e descreve a sua relação com o desenvolvimento em tempo real.</span><span class="sxs-lookup"><span data-stu-id="f92d6-108">[Chapter 1](chapter1.md) - contains an basic overview of Azure RTOS TraceX and describes its relationship to real-time development.</span></span>
- <span data-ttu-id="f92d6-109">[Capítulo 2](chapter2.md) - dá os passos básicos para instalar e utilizar o Azure RTOS TraceX para analisar a sua aplicação fora da caixa.</span><span class="sxs-lookup"><span data-stu-id="f92d6-109">[Chapter 2](chapter2.md) - gives the basic steps to install and use Azure RTOS TraceX to analyze your application right out of the box.</span></span>
- <span data-ttu-id="f92d6-110">[Capítulo 3](chapter3.md) - descreve as principais características do Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="f92d6-110">[Chapter 3](chapter3.md) - describes the main features of Azure RTOS TraceX.</span></span>
- <span data-ttu-id="f92d6-111">[Capítulo 4](chapter4.md) - detalhes das características de análise de desempenho do Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="f92d6-111">[Chapter 4](chapter4.md) - details performance analysis features of Azure RTOS TraceX.</span></span>
- <span data-ttu-id="f92d6-112">[Capítulo 5](chapter5.md) - descreve como configurar Azure RTOS ThreadX, Azure RTOS FileX e Azure RTOS NetX para gerar um tampão de traço que seja visível por Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="f92d6-112">[Chapter 5](chapter5.md) - describes how to set up Azure RTOS ThreadX, Azure RTOS FileX, and Azure RTOS NetX in order to generate a trace buffer that is viewable by Azure RTOS TraceX.</span></span>
- <span data-ttu-id="f92d6-113">[Capítulo 6](chapter6.md) - descreve em detalhe os eventos Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="f92d6-113">[Chapter 6](chapter6.md) - describes Azure RTOS TraceX events in detail.</span></span>
- <span data-ttu-id="f92d6-114">[Capítulo 7](chapter7.md) - descreve em detalhe os eventos Azure RTOS FileX.</span><span class="sxs-lookup"><span data-stu-id="f92d6-114">[Chapter 7](chapter7.md) - describes Azure RTOS FileX events in detail.</span></span>
- <span data-ttu-id="f92d6-115">[Capítulo 8](chapter8.md) - descreve em detalhe os eventos Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="f92d6-115">[Chapter 8](chapter8.md) - describes Azure RTOS NetX events in detail.</span></span>
- <span data-ttu-id="f92d6-116">[Capítulo 9](chapter9.md) - descreve em detalhe os eventos Azure RTOS USBX.</span><span class="sxs-lookup"><span data-stu-id="f92d6-116">[Chapter 9](chapter9.md) - describes Azure RTOS USBX events in detail.</span></span>
- <span data-ttu-id="f92d6-117">[Capítulo 10](chapter10.md) - descreve a criação de eventos personalizados do utilizador em detalhe.</span><span class="sxs-lookup"><span data-stu-id="f92d6-117">[Chapter 10](chapter10.md) - describes creating custom user events in detail.</span></span>
- <span data-ttu-id="f92d6-118">[Capítulo 11](chapter11.md) - descreve o tampão de vestígios interno em detalhe.</span><span class="sxs-lookup"><span data-stu-id="f92d6-118">[Chapter 11](chapter11.md) - describes the internal trace buffer in detail.</span></span>
- <span data-ttu-id="f92d6-119">[Apêndice A](appendix-a.md) - Arquivo específico da porta Azure RTOS ThreadX com a sua fonte de carimbo de tempo para recolha de eventos de rastreio.</span><span class="sxs-lookup"><span data-stu-id="f92d6-119">[Appendix A](appendix-a.md) - Azure RTOS ThreadX port-specific file with its time-stamp source for gathering trace events.</span></span>
- <span data-ttu-id="f92d6-120">[Apêndice B](appendix-b.md) - Ficheiro Azure RTOS ThreadX *tx_trace.h* que mostra detalhes de implementação relativos ao tampão de rastreio do evento.</span><span class="sxs-lookup"><span data-stu-id="f92d6-120">[Appendix B](appendix-b.md) - Azure RTOS ThreadX *tx_trace.h* file that shows implementation details regarding the event trace buffer.</span></span>
- <span data-ttu-id="f92d6-121">[Apêndice C](appendix-c.md) - Resumo dos utilitários da linha de comando para converter vários formatos de ficheiros em ficheiros binários Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="f92d6-121">[Appendix C](appendix-c.md) - Summarizes command line utilities for converting various file formats into proper Azure RTOS TraceX binary files.</span></span>
- <span data-ttu-id="f92d6-122">[Apêndice D](appendix-d.md) - Exemplos de despejo de ficheiros de vestígios de várias ferramentas de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="f92d6-122">[Appendix D](appendix-d.md) - Examples of dumping trace files from various development tools.</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="f92d6-123">Convenções-Guia</span><span class="sxs-lookup"><span data-stu-id="f92d6-123">Guide Conventions</span></span>

<span data-ttu-id="f92d6-124">*Itálico* - O tipo de letra denota títulos de livro, enfatiza palavras importantes e indica variáveis.</span><span class="sxs-lookup"><span data-stu-id="f92d6-124">*Italics* - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="f92d6-125">**Boldface** - Typeface denota nomes de ficheiros, palavras-chave, e enfatiza ainda palavras e variáveis importantes.</span><span class="sxs-lookup"><span data-stu-id="f92d6-125">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!NOTE]
> <span data-ttu-id="f92d6-126">Indica informação de nota.</span><span class="sxs-lookup"><span data-stu-id="f92d6-126">Indicates information of note.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="f92d6-127">Centro de Apoio ao Cliente</span><span class="sxs-lookup"><span data-stu-id="f92d6-127">Customer Support Center</span></span>

<span data-ttu-id="f92d6-128">Por favor envie um bilhete de apoio através do Portal Azure para perguntas ou ajuda a usar os passos aqui.</span><span class="sxs-lookup"><span data-stu-id="f92d6-128">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="f92d6-129">Por favor, forneça-nos as seguintes informações numa mensagem de correio eletrónico para que possamos resolver de forma mais eficiente o seu pedido de apoio:</span><span class="sxs-lookup"><span data-stu-id="f92d6-129">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="f92d6-130">Uma descrição pormenorizada do problema, incluindo a frequência da ocorrência e se pode ser reproduzida de forma fiável.</span><span class="sxs-lookup"><span data-stu-id="f92d6-130">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="f92d6-131">Uma descrição detalhada de quaisquer alterações à aplicação e/ou Azure RTOS ThreadX que precederam o problema.</span><span class="sxs-lookup"><span data-stu-id="f92d6-131">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="f92d6-132">O conteúdo da cadeia *_tx_version_id* encontrado no ficheiro *tx_port.h* da sua distribuição.</span><span class="sxs-lookup"><span data-stu-id="f92d6-132">The contents of the *_tx_version_id* string found in the *tx_port.h* file of your distribution.</span></span> <span data-ttu-id="f92d6-133">Esta corda fornecer-nos-á informações valiosas sobre o seu ambiente de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f92d6-133">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="f92d6-134">O conteúdo em RAM da *_tx_build_options* variável ULONG.</span><span class="sxs-lookup"><span data-stu-id="f92d6-134">The contents in RAM of the *_tx_build_options* ULONG variable.</span></span> <span data-ttu-id="f92d6-135">Esta variável vai dar-nos informações sobre como a sua biblioteca Azure RTOS ThreadX foi construída.</span><span class="sxs-lookup"><span data-stu-id="f92d6-135">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
