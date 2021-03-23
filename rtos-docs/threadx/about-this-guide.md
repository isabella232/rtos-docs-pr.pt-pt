---
title: Sobre o Guia Azure RTOS ThreadX
description: Este guia fornece informações completas sobre o Azure RTOS ThreadX, o kernel em tempo real da Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ad9f782942bcdbb2dc49a9c841d865d97bcb1d4e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826593"
---
# <a name="about-the-azure-rtos-threadx-guide"></a><span data-ttu-id="b4e4a-103">Sobre o Guia Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="b4e4a-103">About the Azure RTOS ThreadX Guide</span></span>

<span data-ttu-id="b4e4a-104">Este guia fornece informações completas sobre o Azure RTOS ThreadX, o kernel de alto desempenho da Microsoft em tempo real.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-104">This guide provides comprehensive information about Azure RTOS ThreadX, the Microsoft high-performance real-time kernel.</span></span> 

<span data-ttu-id="b4e4a-105">Destina-se ao desenvolvedor de software incorporado em tempo real.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-105">It is intended for the embedded real-time software developer.</span></span> <span data-ttu-id="b4e4a-106">O desenvolvedor deve estar familiarizado com as funções padrão do sistema operativo em tempo real e com a linguagem de programação C.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-106">The developer should be familiar with standard real-time operating system functions and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="b4e4a-107">Organização</span><span class="sxs-lookup"><span data-stu-id="b4e4a-107">Organization</span></span>

<span data-ttu-id="b4e4a-108">[Capítulo 1](chapter1.md) - Fornece uma visão geral básica da Azure RTOS ThreadX e da sua relação com o desenvolvimento incorporado em tempo real</span><span class="sxs-lookup"><span data-stu-id="b4e4a-108">[Chapter 1](chapter1.md) - Provides a basic overview of Azure RTOS ThreadX and its relationship to real-time embedded development</span></span>

<span data-ttu-id="b4e4a-109">[Capítulo 2](chapter2.md) - Dá os passos básicos para instalar e utilizar o Azure RTOS ThreadX na sua aplicação *mesmo fora da caixa*</span><span class="sxs-lookup"><span data-stu-id="b4e4a-109">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS ThreadX in your application right *out of the box*</span></span>

<span data-ttu-id="b4e4a-110">[Capítulo 3](chapter3.md) - Descreve em detalhe o funcionamento do Azure RTOS ThreadX, o núcleo em tempo real de alto desempenho</span><span class="sxs-lookup"><span data-stu-id="b4e4a-110">[Chapter 3](chapter3.md) - Describes in detail the functional operation of Azure RTOS ThreadX, the high performance real-time kernel</span></span>

<span data-ttu-id="b4e4a-111">[Capítulo 4](chapter4.md) - Detalha a interface da aplicação com o Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="b4e4a-111">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS ThreadX</span></span>

<span data-ttu-id="b4e4a-112">[Capítulo 5](chapter5.md) - Descreve a escrita de controladores de I/O para aplicações Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="b4e4a-112">[Chapter 5](chapter5.md) - Describes writing I/O drivers for Azure RTOS ThreadX applications</span></span>

<span data-ttu-id="b4e4a-113">[Capítulo 6](chapter6.md) - Descreve a aplicação de demonstração que é fornecida com todos os pacotes de suporte ao processador Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="b4e4a-113">[Chapter 6](chapter6.md) - Describes the demonstration application that is supplied with every Azure RTOS ThreadX processor support package</span></span>

<span data-ttu-id="b4e4a-114">[Apêndice A](appendix-a.md) - Azure RTOS ThreadX API</span><span class="sxs-lookup"><span data-stu-id="b4e4a-114">[Appendix A](appendix-a.md) - Azure RTOS ThreadX API</span></span>

<span data-ttu-id="b4e4a-115">[Apêndice B](appendix-b.md) - Azure RTOS ThreadX constantes</span><span class="sxs-lookup"><span data-stu-id="b4e4a-115">[Appendix B](appendix-b.md) - Azure RTOS ThreadX constants</span></span>

<span data-ttu-id="b4e4a-116">[Apêndice C](appendix-c.md) - Azure RTOS ThreadX tipos de dados</span><span class="sxs-lookup"><span data-stu-id="b4e4a-116">[Appendix C](appendix-c.md) - Azure RTOS ThreadX data types</span></span>

<span data-ttu-id="b4e4a-117">[Apêndice D](appendix-d.md) - Gráfico ASCII</span><span class="sxs-lookup"><span data-stu-id="b4e4a-117">[Appendix D](appendix-d.md) - ASCII chart</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="b4e4a-118">Convenções-Guia</span><span class="sxs-lookup"><span data-stu-id="b4e4a-118">Guide Conventions</span></span>

<span data-ttu-id="b4e4a-119">*Itálico* - o tipo de letra denota títulos de livro, enfatiza palavras importantes e indica parâmetros.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-119">*Italics* - typeface denotes book titles, emphasizes important words, and indicates parameters.</span></span>

<span data-ttu-id="b4e4a-120">**Boldface** - o tipo de letra denota palavras-chave, constantes, nomes de tipo, elementos de interface de utilizador, nomes variáveis, e enfatiza ainda palavras importantes.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-120">**Boldface** - typeface denotes key words, constants, type names, user interface elements, variable names, and further emphasizes important words.</span></span>

<span data-ttu-id="b4e4a-121">***Itálico e Boldface*** - o tipo de letra denota nomes de ficheiros e nomes de funções.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-121">***Italics and Boldface*** - typeface denotes file names and function names.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b4e4a-122">Os símbolos de informação chamam a atenção para informações importantes ou adicionais que possam afetar o desempenho ou a função.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-122">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>

> [!WARNING]
> <span data-ttu-id="b4e4a-123">Os símbolos de aviso chamam a atenção para situações em que os desenvolvedores devem ter o cuidado de evitar porque podem causar erros fatais.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-123">Warning symbols draw attention to situations in which developers should take care to avoid because they could cause fatal errors.</span></span>

## <a name="azure-rtos-threadx-data-types"></a><span data-ttu-id="b4e4a-124">Tipos de dados Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="b4e4a-124">Azure RTOS ThreadX Data Types</span></span>

<span data-ttu-id="b4e4a-125">Além dos tipos de dados personalizados da estrutura de controlo Azure RTOS ThreadX, existem uma série de tipos especiais de dados que são utilizados nas interfaces de chamada de serviço Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-125">In addition to the custom Azure RTOS ThreadX control structure data types, there are a series of special data types that are used in Azure RTOS ThreadX service call interfaces.</span></span> <span data-ttu-id="b4e4a-126">Estes tipos especiais de dados mapeiam diretamente para os tipos de dados do compilador C subjacente.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-126">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="b4e4a-127">Isto é feito para garantir a portabilidade entre diferentes compiladores C.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-127">This is done to insure portability between different C compilers.</span></span> <span data-ttu-id="b4e4a-128">A implementação exata pode ser encontrada no ficheiro ***tx_port.h*** incluído na fonte.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-128">The exact implementation can be found in the ***tx_port.h*** file included with the source.</span></span>

<span data-ttu-id="b4e4a-129">Segue-se uma lista dos tipos de dados de chamada de chamada de serviço Azure RTOS ThreadX e os seus significados associados:</span><span class="sxs-lookup"><span data-stu-id="b4e4a-129">The following is a list of Azure RTOS ThreadX service call data types and their associated meanings:</span></span>

| <span data-ttu-id="b4e4a-130">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="b4e4a-130">Data type</span></span>  | <span data-ttu-id="b4e4a-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4e4a-131">Description</span></span> |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| <span data-ttu-id="b4e4a-132">**UINT**</span><span class="sxs-lookup"><span data-stu-id="b4e4a-132">**UINT**</span></span> | <span data-ttu-id="b4e4a-133">Número inteiro básico não assinado.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-133">Basic unsigned integer.</span></span> <span data-ttu-id="b4e4a-134">Este tipo deve suportar dados não assinados de 8 bits; no entanto, é mapeado para o mais conveniente tipo de dados não assinado.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-134">This type must support 8-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="b4e4a-135">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="b4e4a-135">**ULONG**</span></span> | <span data-ttu-id="b4e4a-136">Tipo longo não assinado.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-136">Unsigned long type.</span></span> <span data-ttu-id="b4e4a-137">Este tipo deve suportar dados não assinados de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-137">This type must support 32-bit unsigned data.</span></span> |
| <span data-ttu-id="b4e4a-138">**VAZIO**</span><span class="sxs-lookup"><span data-stu-id="b4e4a-138">**VOID**</span></span> | <span data-ttu-id="b4e4a-139">Quase sempre equivalente ao tipo vazio do compilador.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-139">Almost always equivalent to the compiler's void type.</span></span> |
| <span data-ttu-id="b4e4a-140">**CHAR**</span><span class="sxs-lookup"><span data-stu-id="b4e4a-140">**CHAR**</span></span> | <span data-ttu-id="b4e4a-141">Na maioria das vezes, um tipo de caracteres padrão de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-141">Most often a standard 8-bit character type.</span></span> |
|  |  |

<span data-ttu-id="b4e4a-142">Tipos de dados adicionais são utilizados dentro da fonte Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-142">Additional data types are used within the Azure RTOS ThreadX source.</span></span> <span data-ttu-id="b4e4a-143">Também estão localizados no ficheiro ***tx_port.h.***</span><span class="sxs-lookup"><span data-stu-id="b4e4a-143">They are also located in the ***tx_port.h*** file.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="b4e4a-144">Centro de Apoio ao Cliente</span><span class="sxs-lookup"><span data-stu-id="b4e4a-144">Customer Support Center</span></span>

<span data-ttu-id="b4e4a-145">Por favor envie um bilhete de apoio através do Portal Azure para perguntas ou ajuda a usar os passos aqui.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-145">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="b4e4a-146">Por favor, forneça-nos as seguintes informações numa mensagem de correio eletrónico para que possamos resolver de forma mais eficiente o seu pedido de apoio:</span><span class="sxs-lookup"><span data-stu-id="b4e4a-146">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="b4e4a-147">Uma descrição pormenorizada do problema, incluindo a frequência da ocorrência e se pode ser reproduzida de forma fiável.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-147">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="b4e4a-148">Uma descrição detalhada de quaisquer alterações à aplicação e/ou Azure RTOS ThreadX que precederam o problema.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-148">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="b4e4a-149">O conteúdo da cadeia *_tx_version_id* encontrado no ficheiro *tx_port.h* da sua distribuição.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-149">The contents of the *_tx_version_id* string found in the *tx_port.h* file of your distribution.</span></span> <span data-ttu-id="b4e4a-150">Esta corda fornecer-nos-á informações valiosas sobre o seu ambiente de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-150">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="b4e4a-151">O conteúdo em RAM da **_tx_build_options** variável **ULONG.**</span><span class="sxs-lookup"><span data-stu-id="b4e4a-151">The contents in RAM of the **_tx_build_options** **ULONG** variable.</span></span> <span data-ttu-id="b4e4a-152">Esta variável vai dar-nos informações sobre como a sua biblioteca Azure RTOS ThreadX foi construída.</span><span class="sxs-lookup"><span data-stu-id="b4e4a-152">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
