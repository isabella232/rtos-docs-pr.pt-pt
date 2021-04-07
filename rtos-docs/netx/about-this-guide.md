---
title: Sobre o Guia de Utilizador Azure RTOS NetX
description: Este guia contém informações completas sobre o Azure RTOS NetX, a pilha de rede de alto desempenho da Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 01077e3315e87b918cdfd47423d8e0c1b6bbdbbd
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550274"
---
# <a name="about-the-azure-rtos-netx-user-guide"></a><span data-ttu-id="d68cc-103">Sobre o Guia de Utilizador Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="d68cc-103">About The Azure RTOS NetX User Guide</span></span>

<span data-ttu-id="d68cc-104">Este guia contém informações completas sobre o Azure RTOS NetX, a pilha de rede de alto desempenho da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d68cc-104">This guide contains comprehensive information about Azure RTOS NetX, the Microsoft high-performance network stack.</span></span>

<span data-ttu-id="d68cc-105">Destina-se a desenvolvedores de software em tempo real familiarizados com conceitos básicos de rede, Azure RTOS ThreadX e a linguagem de programação C.</span><span class="sxs-lookup"><span data-stu-id="d68cc-105">It is intended for embedded real-time software developers familiar with basic networking concepts, Azure RTOS ThreadX, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="d68cc-106">Organização</span><span class="sxs-lookup"><span data-stu-id="d68cc-106">Organization</span></span>

<span data-ttu-id="d68cc-107">[Capítulo 1](chapter1.md) - Introduz Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="d68cc-107">[Chapter 1](chapter1.md) - Introduces Azure RTOS NetX</span></span>

<span data-ttu-id="d68cc-108">[Capítulo 2](chapter2.md) - Dá os passos básicos para instalar e utilizar o Azure RTOS NetX com a sua aplicação ThreadX.</span><span class="sxs-lookup"><span data-stu-id="d68cc-108">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS NetX with your ThreadX application.</span></span>

<span data-ttu-id="d68cc-109">[Capítulo 3](chapter3.md) - Fornece uma visão geral funcional do sistema Azure RTOS NetX e informações básicas sobre as normas de rede TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="d68cc-109">[Chapter 3](chapter3.md) - Provides a functional overview of the Azure RTOS NetX system and basic information about the TCP/IP networking standards.</span></span>

<span data-ttu-id="d68cc-110">[Capítulo 4](chapter4.md) - Detalha a interface da aplicação com o Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="d68cc-110">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS NetX.</span></span>

<span data-ttu-id="d68cc-111">[Capítulo 5](chapter5.md) - Descreve os controladores de rede para o Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="d68cc-111">[Chapter 5](chapter5.md) - Describes network drivers for Azure RTOS NetX.</span></span>

<span data-ttu-id="d68cc-112">[Apêndice A](appendix-a.md) - Azure RTOS NetX Services</span><span class="sxs-lookup"><span data-stu-id="d68cc-112">[Appendix A](appendix-a.md) - Azure RTOS NetX Services</span></span>

<span data-ttu-id="d68cc-113">[Apêndice B](appendix-b.md) - Azure RTOS NetX Constants</span><span class="sxs-lookup"><span data-stu-id="d68cc-113">[Appendix B](appendix-b.md) - Azure RTOS NetX Constants</span></span>

<span data-ttu-id="d68cc-114">[Apêndice C](appendix-c.md) - Azure RTOS NetX Data Types</span><span class="sxs-lookup"><span data-stu-id="d68cc-114">[Appendix C](appendix-c.md) - Azure RTOS NetX Data Types</span></span>

<span data-ttu-id="d68cc-115">[Apêndice D](appendix-d.md) - API de tomada BSD-Compatible</span><span class="sxs-lookup"><span data-stu-id="d68cc-115">[Appendix D](appendix-d.md) - BSD-Compatible Socket API</span></span>

<span data-ttu-id="d68cc-116">[Apêndice E](appendix-e.md) - Gráfico ASCII</span><span class="sxs-lookup"><span data-stu-id="d68cc-116">[Appendix E](appendix-e.md) - ASCII Chart</span></span>

## <a name="azure-rtos-netx-data-types"></a><span data-ttu-id="d68cc-117">Tipos de dados Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="d68cc-117">Azure RTOS NetX Data Types</span></span>

<span data-ttu-id="d68cc-118">Além dos tipos de dados personalizados da estrutura de controlo Azure RTOS NetX, existem vários tipos de dados especiais que são utilizados nas interfaces de chamada de serviço Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="d68cc-118">In addition to the custom Azure RTOS NetX control structure data types, there are several special data types that are used in Azure RTOS NetX service call interfaces.</span></span> <span data-ttu-id="d68cc-119">Estes tipos especiais de dados mapeiam diretamente para os tipos de dados do compilador C subjacente.</span><span class="sxs-lookup"><span data-stu-id="d68cc-119">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="d68cc-120">Isto é feito para garantir a portabilidade entre diferentes compiladores C.</span><span class="sxs-lookup"><span data-stu-id="d68cc-120">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="d68cc-121">A implementação exata é herdada da ThreadX e pode ser encontrada no ficheiro ***tx_port.h*** incluído na distribuição ThreadX.</span><span class="sxs-lookup"><span data-stu-id="d68cc-121">The exact implementation is inherited from ThreadX and can be found in the ***tx_port.h*** file included in the ThreadX distribution.</span></span>

<span data-ttu-id="d68cc-122">Segue-se uma lista dos tipos de dados de chamada de chamada de serviço Azure RTOS NetX e os seus significados associados:</span><span class="sxs-lookup"><span data-stu-id="d68cc-122">The following is a list of Azure RTOS NetX service call data types and their associated meanings:</span></span>

| <span data-ttu-id="d68cc-123">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="d68cc-123">Data Types</span></span> | <span data-ttu-id="d68cc-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="d68cc-124">Description</span></span>  |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="d68cc-125">**UINT**</span><span class="sxs-lookup"><span data-stu-id="d68cc-125">**UINT**</span></span>  | <span data-ttu-id="d68cc-126">Número inteiro básico não assinado.</span><span class="sxs-lookup"><span data-stu-id="d68cc-126">Basic unsigned integer.</span></span> <span data-ttu-id="d68cc-127">Este tipo deve suportar dados não assinados de 32 bits; no entanto, é mapeado para o mais conveniente tipo de dados não assinado.</span><span class="sxs-lookup"><span data-stu-id="d68cc-127">This type must support 32-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="d68cc-128">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="d68cc-128">**ULONG**</span></span> | <span data-ttu-id="d68cc-129">Tipo longo não assinado.</span><span class="sxs-lookup"><span data-stu-id="d68cc-129">Unsigned long type.</span></span> <span data-ttu-id="d68cc-130">Este tipo deve suportar dados não assinados de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="d68cc-130">This type must support 32-bit unsigned data.</span></span>                                                                      |
| <span data-ttu-id="d68cc-131">**VAZIO**</span><span class="sxs-lookup"><span data-stu-id="d68cc-131">**VOID**</span></span>  | <span data-ttu-id="d68cc-132">Quase sempre equivalente ao tipo vazio do compilador.</span><span class="sxs-lookup"><span data-stu-id="d68cc-132">Almost always equivalent to the compiler's void type.</span></span>                                                                                 |
| <span data-ttu-id="d68cc-133">**CHAR**</span><span class="sxs-lookup"><span data-stu-id="d68cc-133">**CHAR**</span></span>  | <span data-ttu-id="d68cc-134">Na maioria das vezes, um tipo de caracteres padrão de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="d68cc-134">Most often a standard 8-bit character type.</span></span>                                                                                           |

<span data-ttu-id="d68cc-135">Tipos de dados adicionais são utilizados dentro da fonte Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="d68cc-135">Additional data types are used within the Azure RTOS NetX source.</span></span> <span data-ttu-id="d68cc-136">Estão localizados nos ficheiros ***tx_port.h_** ou _ *_nx_port.h*_*</span><span class="sxs-lookup"><span data-stu-id="d68cc-136">They are located in either the ***tx_port.h** _ or _ *_nx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="d68cc-137">Centro de Apoio ao Cliente</span><span class="sxs-lookup"><span data-stu-id="d68cc-137">Customer Support Center</span></span>

<span data-ttu-id="d68cc-138">Por favor envie um bilhete de apoio através do Portal Azure para perguntas ou ajuda a usar os passos aqui.</span><span class="sxs-lookup"><span data-stu-id="d68cc-138">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="d68cc-139">Por favor, forneça-nos as seguintes informações numa mensagem de correio eletrónico para que possamos resolver de forma mais eficiente o seu pedido de apoio:</span><span class="sxs-lookup"><span data-stu-id="d68cc-139">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="d68cc-140">Uma descrição pormenorizada do problema, incluindo a frequência da ocorrência e se pode ser reproduzida de forma fiável.</span><span class="sxs-lookup"><span data-stu-id="d68cc-140">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>

2. <span data-ttu-id="d68cc-141">Uma descrição detalhada de quaisquer alterações à aplicação e/ou Azure RTOS NetX que precederam o problema.</span><span class="sxs-lookup"><span data-stu-id="d68cc-141">A detailed description of any changes to the application and/or Azure RTOS NetX that preceded the problem.</span></span>

3. <span data-ttu-id="d68cc-142">O conteúdo das cordas **_tx_version_id** e **_nx_version_id** encontrados nos ficheiros **_tx_port.h_*_ e _*_nx_port.h_** da sua distribuição.</span><span class="sxs-lookup"><span data-stu-id="d68cc-142">The contents of the **_tx_version_id** and **_nx_version_id** strings found in the **_tx_port.h_*_ and _*_nx_port.h_** files of your distribution.</span></span> <span data-ttu-id="d68cc-143">Estas cordas fornecer-nos-ão informações valiosas sobre o seu ambiente de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d68cc-143">These strings will provide us valuable information regarding your run-time environment.</span></span>

4. <span data-ttu-id="d68cc-144">O conteúdo em RAM das seguintes variáveis **ULONG:**</span><span class="sxs-lookup"><span data-stu-id="d68cc-144">The contents in RAM of the following **ULONG** variables:</span></span>

    <span data-ttu-id="d68cc-145">**_tx_build_options**</span><span class="sxs-lookup"><span data-stu-id="d68cc-145">**_tx_build_options**</span></span>

    <span data-ttu-id="d68cc-146">**_nx_system_build_options1**</span><span class="sxs-lookup"><span data-stu-id="d68cc-146">**_nx_system_build_options1**</span></span>

    <span data-ttu-id="d68cc-147">**_nx_system_build_options2**</span><span class="sxs-lookup"><span data-stu-id="d68cc-147">**_nx_system_build_options2**</span></span>

    <span data-ttu-id="d68cc-148">**_nx_system_build_options3**</span><span class="sxs-lookup"><span data-stu-id="d68cc-148">**_nx_system_build_options3**</span></span>

    <span data-ttu-id="d68cc-149">**_nx_system_build_options4**</span><span class="sxs-lookup"><span data-stu-id="d68cc-149">**_nx_system_build_options4**</span></span>

    <span data-ttu-id="d68cc-150">**_nx_system_build_options5**</span><span class="sxs-lookup"><span data-stu-id="d68cc-150">**_nx_system_build_options5**</span></span>

    <span data-ttu-id="d68cc-151">Estas variáveis dar-nos-ão informações sobre como as suas bibliotecas Azure RTOS ThreadX e Azure RTOS NetX foram construídas.</span><span class="sxs-lookup"><span data-stu-id="d68cc-151">These variables will give us information on how your Azure RTOS ThreadX and Azure RTOS NetX libraries were built.</span></span>

5. <span data-ttu-id="d68cc-152">Um tampão de vestígio capturado imediatamente após o problema ter sido detetado.</span><span class="sxs-lookup"><span data-stu-id="d68cc-152">A trace buffer captured immediately after the problem was detected.</span></span> <span data-ttu-id="d68cc-153">Isto é conseguido construindo as bibliotecas Azure RTOS ThreadX e Azure RTOS NetX com **TX_ENABLE_EVENT_TRACE** e chamando **tx_trace_enable** com a informação do tampão de traços.</span><span class="sxs-lookup"><span data-stu-id="d68cc-153">This is accomplished by building the Azure RTOS ThreadX and Azure RTOS NetX libraries with **TX_ENABLE_EVENT_TRACE** and calling **tx_trace_enable** with the trace buffer information.</span></span> <span data-ttu-id="d68cc-154">Consulte o Guia do Utilizador Azure RTOS TraceX para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="d68cc-154">Refer to the Azure RTOS TraceX User Guide for details.</span></span>
