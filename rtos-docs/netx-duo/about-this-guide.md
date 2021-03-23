---
title: Sobre o Azure RTOS NetX Duo User Guide
description: Este guia contém informações completas sobre o Azure RTOS NetX Duo, a pilha de rede dupla IPv4/IPv6 de alto desempenho da Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b1eef5bfa28f13d7a6b627792f96039b252f2355
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826239"
---
# <a name="about-the-azure-rtos-netx-duo-user-guide"></a><span data-ttu-id="a99f6-103">Sobre o Azure RTOS NetX Duo User Guide</span><span class="sxs-lookup"><span data-stu-id="a99f6-103">About The Azure RTOS NetX Duo User Guide</span></span>

<span data-ttu-id="a99f6-104">Este guia contém informações completas sobre o Azure RTOS NetX Duo, a pilha de rede dupla IPv4/IPv6 de alto desempenho da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a99f6-104">This guide contains comprehensive information about Azure RTOS NetX Duo, the Microsoft high-performance IPv4/IPv6 dual network stack.</span></span> 

<span data-ttu-id="a99f6-105">Destina-se a desenvolvedores de software em tempo real familiarizados com conceitos básicos de rede, Azure RTOS ThreadX e a linguagem de programação C.</span><span class="sxs-lookup"><span data-stu-id="a99f6-105">It is intended for embedded real-time software developers familiar with basic networking concepts, Azure RTOS ThreadX, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="a99f6-106">Organização</span><span class="sxs-lookup"><span data-stu-id="a99f6-106">Organization</span></span>

<span data-ttu-id="a99f6-107">[Capítulo 1](chapter1.md) - Introduz Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="a99f6-107">[Chapter 1](chapter1.md) - Introduces Azure RTOS NetX Duo</span></span>

<span data-ttu-id="a99f6-108">[Capítulo 2](chapter2.md) - Dá os passos básicos para instalar e utilizar o Azure RTOS NetX Duo com a sua aplicação ThreadX</span><span class="sxs-lookup"><span data-stu-id="a99f6-108">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS NetX Duo with your ThreadX application</span></span>

<span data-ttu-id="a99f6-109">[Capítulo 3](chapter3.md) - Fornece uma visão geral funcional do sistema Azure RTOS NetX Duo e informações básicas sobre as normas de rede TCP/IP</span><span class="sxs-lookup"><span data-stu-id="a99f6-109">[Chapter 3](chapter3.md) - Provides a functional overview of the Azure RTOS NetX Duo system and basic information about the TCP/IP networking standards</span></span>

<span data-ttu-id="a99f6-110">[Capítulo 4](chapter4.md) - Detalha a interface da aplicação com o Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="a99f6-110">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS NetX Duo</span></span>

<span data-ttu-id="a99f6-111">[Capítulo 5](chapter5.md) - Descreve os controladores de rede para Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="a99f6-111">[Chapter 5](chapter5.md) - Describes network drivers for Azure RTOS NetX Duo</span></span>

<span data-ttu-id="a99f6-112">[Apêndice A](appendix-a.md) - Azure RTOS NetX Duo Services</span><span class="sxs-lookup"><span data-stu-id="a99f6-112">[Appendix A](appendix-a.md) - Azure RTOS NetX Duo Services</span></span>

<span data-ttu-id="a99f6-113">[Apêndice B](appendix-b.md) - Azure RTOS NetX Duo Constants</span><span class="sxs-lookup"><span data-stu-id="a99f6-113">[Appendix B](appendix-b.md) - Azure RTOS NetX Duo Constants</span></span>

<span data-ttu-id="a99f6-114">[Apêndice C](appendix-c.md) - Azure RTOS NetX Duo Data Types</span><span class="sxs-lookup"><span data-stu-id="a99f6-114">[Appendix C](appendix-c.md) - Azure RTOS NetX Duo Data Types</span></span>

<span data-ttu-id="a99f6-115">[Apêndice D](appendix-d.md) - API de tomada BSD-Compatible</span><span class="sxs-lookup"><span data-stu-id="a99f6-115">[Appendix D](appendix-d.md) - BSD-Compatible Socket API</span></span>

<span data-ttu-id="a99f6-116">[Apêndice E](appendix-e.md) - Gráfico ASCII</span><span class="sxs-lookup"><span data-stu-id="a99f6-116">[Appendix E](appendix-e.md) - ASCII Chart</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="a99f6-117">Convenções-Guia</span><span class="sxs-lookup"><span data-stu-id="a99f6-117">Guide Conventions</span></span>

<span data-ttu-id="a99f6-118">Itálico - O tipo de letra denota títulos de livro, enfatiza palavras importantes e indica variáveis.</span><span class="sxs-lookup"><span data-stu-id="a99f6-118">Italics - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="a99f6-119">**Boldface** - Typeface denota nomes de ficheiros, palavras-chave, e enfatiza ainda palavras e variáveis importantes.</span><span class="sxs-lookup"><span data-stu-id="a99f6-119">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a99f6-120">Os símbolos de informação chamam a atenção para informações importantes ou adicionais que possam afetar o desempenho ou a função.</span><span class="sxs-lookup"><span data-stu-id="a99f6-120">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>
 
> [!WARNING]
> <span data-ttu-id="a99f6-121">Os símbolos de aviso chamam a atenção para situações que os desenvolvedores devem evitar porque podem causar erros fatais.</span><span class="sxs-lookup"><span data-stu-id="a99f6-121">Warning symbols draw attention to situations that developers should avoid because they could cause fatal errors.</span></span>

## <a name="azure-rtos-netx-duo-data-types"></a><span data-ttu-id="a99f6-122">Azure RTOS NetX Duo Data Types</span><span class="sxs-lookup"><span data-stu-id="a99f6-122">Azure RTOS NetX Duo Data Types</span></span>

<span data-ttu-id="a99f6-123">Além dos tipos de dados personalizados da estrutura de controlo Azure RTOS NetX Duo, existem vários tipos de dados especiais que são utilizados nas interfaces de chamada de serviço Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="a99f6-123">In addition to the custom Azure RTOS NetX Duo control structure data types, there are several special data types that are used in Azure RTOS NetX Duo service call interfaces.</span></span> <span data-ttu-id="a99f6-124">Estes tipos especiais de dados mapeiam diretamente para os tipos de dados do compilador C subjacente.</span><span class="sxs-lookup"><span data-stu-id="a99f6-124">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="a99f6-125">Isto é feito para garantir a portabilidade entre diferentes compiladores C.</span><span class="sxs-lookup"><span data-stu-id="a99f6-125">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="a99f6-126">A implementação exata é herdada da ThreadX e pode ser encontrada no ficheiro ***tx_port.h*** incluído na distribuição ThreadX.</span><span class="sxs-lookup"><span data-stu-id="a99f6-126">The exact implementation is inherited from ThreadX and can be found in the ***tx_port.h*** file included in the ThreadX distribution.</span></span>

<span data-ttu-id="a99f6-127">Segue-se uma lista dos tipos de dados de chamada de chamada de serviço Azure RTOS NetX Duo e os seus significados associados:</span><span class="sxs-lookup"><span data-stu-id="a99f6-127">The following is a list of Azure RTOS NetX Duo service call data types and their associated meanings:</span></span>

<span data-ttu-id="a99f6-128">**UINT**: Número inteiro básico não assinado.</span><span class="sxs-lookup"><span data-stu-id="a99f6-128">**UINT**: Basic unsigned integer.</span></span> <span data-ttu-id="a99f6-129">Este tipo deve suportar dados não assinados de 32 bits; no entanto, é mapeado para o mais conveniente tipo de dados não assinado.</span><span class="sxs-lookup"><span data-stu-id="a99f6-129">This type must support 32-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span>  
<span data-ttu-id="a99f6-130">**ULONG**: Tipo longo não assinado.</span><span class="sxs-lookup"><span data-stu-id="a99f6-130">**ULONG**: Unsigned long type.</span></span> <span data-ttu-id="a99f6-131">Este tipo deve suportar dados não assinados de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="a99f6-131">This type must support 32-bit unsigned  data.</span></span>
<span data-ttu-id="a99f6-132">**VOID**: Quase sempre equivalente ao tipo de vazio do compilador.</span><span class="sxs-lookup"><span data-stu-id="a99f6-132">**VOID**: Almost always equivalent to the compiler's void type.</span></span>  
<span data-ttu-id="a99f6-133">**CHAR**: Na maioria das vezes um tipo de caracteres padrão de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="a99f6-133">**CHAR**: Most often a standard 8-bit character type.</span></span>  

<span data-ttu-id="a99f6-134">Tipos de dados adicionais são utilizados dentro da fonte Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="a99f6-134">Additional data types are used within the Azure RTOS NetX Duo source.</span></span> <span data-ttu-id="a99f6-135">Estão localizados nos ficheiros ***tx_port.h_** ou _ *_nx_port.h*_*</span><span class="sxs-lookup"><span data-stu-id="a99f6-135">They are located in either the ***tx_port.h** _ or _ *_nx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="a99f6-136">Centro de Apoio ao Cliente</span><span class="sxs-lookup"><span data-stu-id="a99f6-136">Customer Support Center</span></span>

<span data-ttu-id="a99f6-137">Por favor envie um bilhete de apoio através do Portal Azure para perguntas ou ajuda a usar os passos aqui.</span><span class="sxs-lookup"><span data-stu-id="a99f6-137">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="a99f6-138">Por favor, forneça-nos as seguintes informações numa mensagem de correio eletrónico para que possamos resolver de forma mais eficiente o seu pedido de apoio:</span><span class="sxs-lookup"><span data-stu-id="a99f6-138">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="a99f6-139">Uma descrição pormenorizada do problema, incluindo a frequência da ocorrência e se pode ser reproduzida de forma fiável.</span><span class="sxs-lookup"><span data-stu-id="a99f6-139">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="a99f6-140">Uma descrição detalhada de quaisquer alterações à aplicação e/ou Azure RTOS NetX Duo que precederam o problema.</span><span class="sxs-lookup"><span data-stu-id="a99f6-140">A detailed description of any changes to the application and/or Azure RTOS NetX Duo that preceded the problem.</span></span>
3. <span data-ttu-id="a99f6-141">O conteúdo das cordas _tx_version_id e _nx_version_id encontrado nos ficheiros tx_port.h e nx_port.h da sua distribuição.</span><span class="sxs-lookup"><span data-stu-id="a99f6-141">The contents of the _tx_version_id and _nx_version_id strings found in the tx_port.h and nx_port.h files of your distribution.</span></span> <span data-ttu-id="a99f6-142">Estas cordas fornecer-nos-ão informações valiosas sobre o seu ambiente de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a99f6-142">These strings will provide us valuable information regarding your run- time environment.</span></span>
4. <span data-ttu-id="a99f6-143">O conteúdo em RAM das seguintes variáveis ULONG:</span><span class="sxs-lookup"><span data-stu-id="a99f6-143">The contents in RAM of the following ULONG variables:</span></span>

    <span data-ttu-id="a99f6-144">**_tx_build_options**</span><span class="sxs-lookup"><span data-stu-id="a99f6-144">**_tx_build_options**</span></span>

    <span data-ttu-id="a99f6-145">**_nx_system_build_options1**</span><span class="sxs-lookup"><span data-stu-id="a99f6-145">**_nx_system_build_options1**</span></span>

    <span data-ttu-id="a99f6-146">**_nx_system_build_options2**</span><span class="sxs-lookup"><span data-stu-id="a99f6-146">**_nx_system_build_options2**</span></span>

    <span data-ttu-id="a99f6-147">**_nx_system_build_options3**</span><span class="sxs-lookup"><span data-stu-id="a99f6-147">**_nx_system_build_options3**</span></span>

    <span data-ttu-id="a99f6-148">**_nx_system_build_options4**</span><span class="sxs-lookup"><span data-stu-id="a99f6-148">**_nx_system_build_options4**</span></span>

    <span data-ttu-id="a99f6-149">**_nx_system_build_options5**</span><span class="sxs-lookup"><span data-stu-id="a99f6-149">**_nx_system_build_options5**</span></span>

    <span data-ttu-id="a99f6-150">Estas variáveis dar-nos-ão informações sobre como as suas bibliotecas Azure RTOS ThreadX e Azure RTOS NetX Duo foram construídas.</span><span class="sxs-lookup"><span data-stu-id="a99f6-150">These variables will give us information on how your Azure RTOS ThreadX and Azure RTOS NetX Duo libraries were built.</span></span>

5. <span data-ttu-id="a99f6-151">Um tampão de vestígio capturado imediatamente após o problema ter sido detetado.</span><span class="sxs-lookup"><span data-stu-id="a99f6-151">A trace buffer captured immediately after the problem was detected.</span></span> <span data-ttu-id="a99f6-152">Isto é conseguido construindo as bibliotecas Azure RTOS ThreadX e Azure RTOS NetX Duo com TX_ENABLE_EVENT_TRACE e chamando tx_trace_enable com a informação do tampão de traços.</span><span class="sxs-lookup"><span data-stu-id="a99f6-152">This is accomplished by building the Azure RTOS ThreadX and Azure RTOS NetX Duo libraries with TX_ENABLE_EVENT_TRACE and calling tx_trace_enable with the trace buffer information.</span></span>
