---
title: Guia de utilizador Azure RTOS FileX
description: Este guia contém informações completas sobre o Azure RTOS FileX, o sistema de ficheiros em tempo real de alto desempenho da Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0ebcebdd2b227ed8d9ccf8b3078b716f90f35bef
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825561"
---
# <a name="about-this-filex-user-guide"></a><span data-ttu-id="96be3-103">Sobre este Guia de Utilizador FileX</span><span class="sxs-lookup"><span data-stu-id="96be3-103">About This FileX User Guide</span></span>

<span data-ttu-id="96be3-104">Este guia contém informações completas sobre o Azure RTOS FileX, o sistema de ficheiros incorporado em tempo real de alto desempenho da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="96be3-104">This guide contains comprehensive information about Azure RTOS FileX, the high-performance, real-time embedded file system from Microsoft.</span></span> <span data-ttu-id="96be3-105">Para obter o máximo deste guia, deve estar familiarizado com as funções padrão do sistema operativo em tempo real, os serviços do sistema de ficheiros FAT e a linguagem de programação C.</span><span class="sxs-lookup"><span data-stu-id="96be3-105">To gain the most from this guide, you should be familiar with standard real-time operating system functions, FAT file system services, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="96be3-106">Organização</span><span class="sxs-lookup"><span data-stu-id="96be3-106">Organization</span></span>

<span data-ttu-id="96be3-107">[Capítulo 1](chapter1.md) - Introduz Azure RTOS FileX</span><span class="sxs-lookup"><span data-stu-id="96be3-107">[Chapter 1](chapter1.md) - Introduces Azure RTOS FileX</span></span>

<span data-ttu-id="96be3-108">[Capítulo 2](chapter2.md) - Dá os passos básicos para instalar e utilizar o Azure RTOS FileX com a sua aplicação Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="96be3-108">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS FileX with your Azure RTOS ThreadX application</span></span>

<span data-ttu-id="96be3-109">[Capítulo 3](chapter3.md) - Fornece uma visão geral funcional do sistema Azure RTOS FileX e informações básicas sobre formatos de sistema de ficheiros FAT</span><span class="sxs-lookup"><span data-stu-id="96be3-109">[Chapter 3](chapter3.md) - Provides a functional overview of the Azure RTOS FileX system and basic information about FAT file system formats</span></span>

<span data-ttu-id="96be3-110">[Capítulo 4](chapter4.md) - Detalha a interface da aplicação com o Azure RTOS FileX</span><span class="sxs-lookup"><span data-stu-id="96be3-110">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS FileX</span></span>

<span data-ttu-id="96be3-111">[Capítulo 5](chapter5.md) - Descreve o controlador RAM Azure RTOS FileX fornecido e como escrever os seus próprios controladores Azure RTOS FileX</span><span class="sxs-lookup"><span data-stu-id="96be3-111">[Chapter 5](chapter5.md) - Describes the supplied Azure RTOS FileX RAM driver and how to write your own custom Azure RTOS FileX drivers</span></span>

<span data-ttu-id="96be3-112">[Capítulo 6](chapter6.md) - Descreve o Módulo Tolerante com Falhas de Falhas de FicheiroS RTOS Azure</span><span class="sxs-lookup"><span data-stu-id="96be3-112">[Chapter 6](chapter6.md) - Describes the Azure RTOS FileX Fault Tolerant Module</span></span>

<span data-ttu-id="96be3-113">[Apêndice A](appendix-a.md) - Serviços de Arquivo RTOS Azure</span><span class="sxs-lookup"><span data-stu-id="96be3-113">[Appendix A](appendix-a.md) - Azure RTOS FileX Services</span></span>

<span data-ttu-id="96be3-114">[Apêndice B](appendix-b.md) - Azure RTOS FileX Constants</span><span class="sxs-lookup"><span data-stu-id="96be3-114">[Appendix B](appendix-b.md) - Azure RTOS FileX Constants</span></span>

<span data-ttu-id="96be3-115">[Apêndice C](appendix-c.md) - Azure RTOS FileX Data Types</span><span class="sxs-lookup"><span data-stu-id="96be3-115">[Appendix C](appendix-c.md) - Azure RTOS FileX Data Types</span></span>

<span data-ttu-id="96be3-116">[Apêndice D](appendix-d.md) - Gráfico ASCII</span><span class="sxs-lookup"><span data-stu-id="96be3-116">[Appendix D](appendix-d.md) - ASCII Chart</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="96be3-117">Convenções-Guia</span><span class="sxs-lookup"><span data-stu-id="96be3-117">Guide Conventions</span></span>

<span data-ttu-id="96be3-118">*Itálico* - O tipo de letra denota títulos de livro, enfatiza palavras importantes e indica variáveis.</span><span class="sxs-lookup"><span data-stu-id="96be3-118">*Italics* - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="96be3-119">**Boldface** - Typeface denota nomes de ficheiros, palavras-chave, e enfatiza ainda palavras e variáveis importantes.</span><span class="sxs-lookup"><span data-stu-id="96be3-119">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!NOTE]
> <span data-ttu-id="96be3-120">Os símbolos de informação chamam a atenção para informações importantes ou adicionais que possam afetar o desempenho ou a função.</span><span class="sxs-lookup"><span data-stu-id="96be3-120">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="96be3-121">Os símbolos de aviso chamam a atenção para situações que os desenvolvedores devem evitar porque podem causar erros fatais.</span><span class="sxs-lookup"><span data-stu-id="96be3-121">Warning symbols draw attention to situations that developers should avoid because they could cause fatal errors.</span></span>

## <a name="filex-data-types"></a><span data-ttu-id="96be3-122">Tipos de dados filex</span><span class="sxs-lookup"><span data-stu-id="96be3-122">FileX Data Types</span></span>

<span data-ttu-id="96be3-123">Além dos tipos de dados personalizados da estrutura de controlo Azure RTOS FileX, existe uma série de tipos especiais de dados que são utilizados nas interfaces de chamada de serviço Azure RTOS FileX.</span><span class="sxs-lookup"><span data-stu-id="96be3-123">In addition to the custom Azure RTOS FileX control structure data types, there is a series of special data types that are used in Azure RTOS FileX service call interfaces.</span></span> <span data-ttu-id="96be3-124">Estes tipos especiais de dados mapeiam diretamente para os tipos de dados do compilador C subjacente.</span><span class="sxs-lookup"><span data-stu-id="96be3-124">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="96be3-125">Isto é feito para garantir a portabilidade entre diferentes compiladores C.</span><span class="sxs-lookup"><span data-stu-id="96be3-125">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="96be3-126">A implementação exata é herdada da Azure RTOS ThreadX e pode ser encontrada no ficheiro tx_port.h incluído na distribuição Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="96be3-126">The exact implementation is inherited from Azure RTOS ThreadX and can be found in the tx_port.h file included in the Azure RTOS ThreadX distribution.</span></span>

<span data-ttu-id="96be3-127">Segue-se uma lista dos tipos de dados de chamada de chamada de serviço Azure RTOS FileX e os seus significados associados.</span><span class="sxs-lookup"><span data-stu-id="96be3-127">The following is a list of Azure RTOS FileX service call data types and their associated meanings.</span></span>
| <span data-ttu-id="96be3-128">Tipo</span><span class="sxs-lookup"><span data-stu-id="96be3-128">Type</span></span>  | <span data-ttu-id="96be3-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="96be3-129">Description</span></span>  |
|---|---|
| <span data-ttu-id="96be3-130">**UINT**</span><span class="sxs-lookup"><span data-stu-id="96be3-130">**UINT**</span></span> | <span data-ttu-id="96be3-131">Número inteiro básico não assinado.</span><span class="sxs-lookup"><span data-stu-id="96be3-131">Basic unsigned integer.</span></span> <span data-ttu-id="96be3-132">Este tipo deve suportar dados não assinados de 8 bits; no entanto, é mapeado para o mais conveniente tipo de dados não assinado.</span><span class="sxs-lookup"><span data-stu-id="96be3-132">This type must support 8-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="96be3-133">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="96be3-133">**ULONG**</span></span> | <span data-ttu-id="96be3-134">Tipo longo não assinado.</span><span class="sxs-lookup"><span data-stu-id="96be3-134">Unsigned long type.</span></span> <span data-ttu-id="96be3-135">Este tipo deve suportar dados não assinados de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="96be3-135">This type must support 32-bit unsigned data.</span></span> |
| <span data-ttu-id="96be3-136">**VAZIO**</span><span class="sxs-lookup"><span data-stu-id="96be3-136">**VOID**</span></span> | <span data-ttu-id="96be3-137">Quase sempre equivalente ao tipo vazio do compilador.</span><span class="sxs-lookup"><span data-stu-id="96be3-137">Almost always equivalent to the compiler’s void type.</span></span> |
| <span data-ttu-id="96be3-138">**CHAR**</span><span class="sxs-lookup"><span data-stu-id="96be3-138">**CHAR**</span></span> | <span data-ttu-id="96be3-139">Na maioria das vezes, um tipo de caracteres padrão de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="96be3-139">Most often a standard 8-bit character type.</span></span> |
| <span data-ttu-id="96be3-140">**ULONG64**</span><span class="sxs-lookup"><span data-stu-id="96be3-140">**ULONG64**</span></span> | <span data-ttu-id="96be3-141">Tipo de dados inteiros não assinados de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="96be3-141">64-bit unsigned integer data type.</span></span> |

<span data-ttu-id="96be3-142">Tipos de dados adicionais são utilizados dentro da fonte FileX.</span><span class="sxs-lookup"><span data-stu-id="96be3-142">Additional data types are used within the FileX source.</span></span> <span data-ttu-id="96be3-143">Estão localizados nos ficheiros ***tx_port.h_** ou _ *_fx_port.h*_*</span><span class="sxs-lookup"><span data-stu-id="96be3-143">They are located in either the ***tx_port.h** _ or _ *_fx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="96be3-144">Centro de Apoio ao Cliente</span><span class="sxs-lookup"><span data-stu-id="96be3-144">Customer Support Center</span></span>

<span data-ttu-id="96be3-145">Por favor envie um bilhete de apoio através do Portal Azure para perguntas ou ajuda a usar os passos aqui.</span><span class="sxs-lookup"><span data-stu-id="96be3-145">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="96be3-146">Por favor, forneça-nos as seguintes informações numa mensagem de correio eletrónico para que possamos resolver de forma mais eficiente o seu pedido de apoio.</span><span class="sxs-lookup"><span data-stu-id="96be3-146">Please supply us with the following information in an email message so we can more efficiently resolve your support request.</span></span>

1. <span data-ttu-id="96be3-147">Uma descrição pormenorizada do problema, incluindo a frequência da ocorrência e se pode ser reproduzida de forma fiável.</span><span class="sxs-lookup"><span data-stu-id="96be3-147">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="96be3-148">Uma descrição detalhada de quaisquer alterações à aplicação e/ou FileX que precederam o problema.</span><span class="sxs-lookup"><span data-stu-id="96be3-148">A detailed description of any changes to the application and/or FileX that preceded the problem.</span></span>
3. <span data-ttu-id="96be3-149">O conteúdo das cordas _tx_version_id e _fx_version_id encontrado nos ficheiros \***tx_port.h**_ e _ *_fx_port.h*_\* da sua distribuição.</span><span class="sxs-lookup"><span data-stu-id="96be3-149">The contents of the _tx_version_id and _fx_version_id strings found in the \***tx_port.h**_ and _ *_fx_port.h_*\* files of your distribution.</span></span> <span data-ttu-id="96be3-150">Estas cordas fornecer-nos-ão informações valiosas sobre o seu ambiente de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="96be3-150">These strings will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="96be3-151">O conteúdo em RAM das seguintes variáveis **ULONG.**</span><span class="sxs-lookup"><span data-stu-id="96be3-151">The contents in RAM of the following **ULONG** variables.</span></span> <span data-ttu-id="96be3-152">Estas variáveis dar-nos-ão informações sobre como as suas bibliotecas ThreadX e FileX foram construídas:</span><span class="sxs-lookup"><span data-stu-id="96be3-152">These variables will give us information on how your ThreadX and FileX libraries were built:</span></span>

    <span data-ttu-id="96be3-153">**_tx_build_options**</span><span class="sxs-lookup"><span data-stu-id="96be3-153">**_tx_build_options**</span></span>

    <span data-ttu-id="96be3-154">**_fx_system_build_options1**</span><span class="sxs-lookup"><span data-stu-id="96be3-154">**_fx_system_build_options1**</span></span>

    <span data-ttu-id="96be3-155">**_fx_system_build_options2**</span><span class="sxs-lookup"><span data-stu-id="96be3-155">**_fx_system_build_options2**</span></span>

    <span data-ttu-id="96be3-156">**_fx_system_build_options3**</span><span class="sxs-lookup"><span data-stu-id="96be3-156">**_fx_system_build_options3**</span></span>
