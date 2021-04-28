---
title: Compreenda O Azure RTOS Filex
description: O Azure RTOS FileX é um sistema de ficheiros compatível com ficheiros de alto desempenho (FAT)que está totalmente integrado com o Azure RTOS ThreadX e está disponível para todos os processadores suportados. Tal como o Azure RTOS ThreadX, o Azure RTOS FileX foi concebido para ter uma pequena pegada e alto desempenho, tornando-o ideal para as aplicações profundamente incorporadas que requerem operações de gestão de ficheiros. O FileX suporta a maioria dos meios físicos, incluindo RAM, Azure RTOS USBX, SD CARD e NAND/NOR memórias flash via Azure RTOS LevelX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0a54f160c96fb3e90c2295ae72020c121d367a12
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171358"
---
# <a name="overview-of-azure-rtos-filex"></a><span data-ttu-id="0cb50-105">Visão geral do Azure RTOS FileX</span><span class="sxs-lookup"><span data-stu-id="0cb50-105">Overview of Azure RTOS FileX</span></span>

<span data-ttu-id="0cb50-106">O sistema de ficheiros incorporado Azure RTOS FileX é a solução avançada e industrial da Azure RTOS para formatos de ficheiros Microsoft FAT, projetado especificamente para aplicações profundamente incorporadas, em tempo real e IoT.</span><span class="sxs-lookup"><span data-stu-id="0cb50-106">Azure RTOS FileX embedded file system is Azure RTOS's advanced, industrial grade solution for Microsoft FAT file formats, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="0cb50-107">O Azure RTOS FileX suporta todos os formatos de ficheiros da Microsoft, incluindo FAT12, FAT16, FAT32 e exFAT.</span><span class="sxs-lookup"><span data-stu-id="0cb50-107">Azure RTOS FileX supports all of Microsoft’s file formats, including FAT12, FAT16, FAT32, and exFAT.</span></span> <span data-ttu-id="0cb50-108">O FileX também oferece tolerância opcional de falhas e nivelamento de desgaste FLASH através de um produto addon chamado [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/).</span><span class="sxs-lookup"><span data-stu-id="0cb50-108">FileX also offers optional fault tolerance and FLASH wear leveling via an add-on product called [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/).</span></span> <span data-ttu-id="0cb50-109">Tudo isto combinado com uma pequena pegada, execução rápida e facilidade superior de utilização, fazem do Azure RTOS FileX a escolha ideal para as aplicações IoT incorporadas mais exigentes.</span><span class="sxs-lookup"><span data-stu-id="0cb50-109">All of this combined with a small footprint, fast execution, and superior ease-of-use, make Azure RTOS FileX the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="0cb50-110">Protocolos da API</span><span class="sxs-lookup"><span data-stu-id="0cb50-110">API protocols</span></span>

### <a name="media-services"></a><span data-ttu-id="0cb50-111">Serviços de Multimédia</span><span class="sxs-lookup"><span data-stu-id="0cb50-111">Media Services</span></span>

- <span data-ttu-id="0cb50-112">SUPORTE FAT 12/16/32 e exFAT</span><span class="sxs-lookup"><span data-stu-id="0cb50-112">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="0cb50-113">Flash mínimo de 6KB, RAM de 2,5KB</span><span class="sxs-lookup"><span data-stu-id="0cb50-113">Minimal 6KB FLASH, 2.5KB RAM</span></span>
- <span data-ttu-id="0cb50-114">Serviços completos de acesso aos meios de comunicação</span><span class="sxs-lookup"><span data-stu-id="0cb50-114">Complete media access services</span></span>
- <span data-ttu-id="0cb50-115">Número ilimitado de instâncias mediáticas</span><span class="sxs-lookup"><span data-stu-id="0cb50-115">Unlimited number of media instance</span></span>
- <span data-ttu-id="0cb50-116">Interface de condutor do sector de leitura/escrita simples</span><span class="sxs-lookup"><span data-stu-id="0cb50-116">Simple read/write logical sector driver interface</span></span>
- <span data-ttu-id="0cb50-117">Suporte de partição múltipla</span><span class="sxs-lookup"><span data-stu-id="0cb50-117">Multiple partition support</span></span>
- <span data-ttu-id="0cb50-118">Cache do sector lógico</span><span class="sxs-lookup"><span data-stu-id="0cb50-118">Logical sector cache</span></span>
- <span data-ttu-id="0cb50-119">Cache de entrada de GORDURA</span><span class="sxs-lookup"><span data-stu-id="0cb50-119">FAT entry cache</span></span>
- <span data-ttu-id="0cb50-120">Suporte opcional de tolerância à falha</span><span class="sxs-lookup"><span data-stu-id="0cb50-120">Optional fault tolerance support</span></span>
- <span data-ttu-id="0cb50-121">Atualização de FAT Secundária Diferida</span><span class="sxs-lookup"><span data-stu-id="0cb50-121">Deferred Secondary FAT update</span></span>
- <span data-ttu-id="0cb50-122">Traço de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="0cb50-122">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="0cb50-123">APIs de acesso a meios de comunicação intuitivos, incluindo:</span><span class="sxs-lookup"><span data-stu-id="0cb50-123">Intuitive media access APIs, including:</span></span>
  - <span data-ttu-id="0cb50-124">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="0cb50-124">fx_media_open</span></span>
  - <span data-ttu-id="0cb50-125">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="0cb50-125">fx_media_close</span></span>
  - <span data-ttu-id="0cb50-126">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="0cb50-126">fx_media_format</span></span>
  - <span data-ttu-id="0cb50-127">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="0cb50-127">fx_media_space_available</span></span>

### <a name="directory-services"></a><span data-ttu-id="0cb50-128">Serviços de Diretório</span><span class="sxs-lookup"><span data-stu-id="0cb50-128">Directory Services</span></span>

- <span data-ttu-id="0cb50-129">Até 256 byte caminhos</span><span class="sxs-lookup"><span data-stu-id="0cb50-129">Up to 256 byte paths</span></span>
- <span data-ttu-id="0cb50-130">Nomes de diretório longos e 8,3 apoiados</span><span class="sxs-lookup"><span data-stu-id="0cb50-130">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="0cb50-131">Diretório criar & excluir</span><span class="sxs-lookup"><span data-stu-id="0cb50-131">Directory create & delete</span></span>
- <span data-ttu-id="0cb50-132">Navegação diretório e traversal</span><span class="sxs-lookup"><span data-stu-id="0cb50-132">Directory navigation and traversal</span></span>
- <span data-ttu-id="0cb50-133">Gestão de atributos de diretório</span><span class="sxs-lookup"><span data-stu-id="0cb50-133">Directory attributes management</span></span>
- <span data-ttu-id="0cb50-134">Traço de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="0cb50-134">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="0cb50-135">APIs de acesso a diretórios intuitivos, incluindo:</span><span class="sxs-lookup"><span data-stu-id="0cb50-135">Intuitive directory access APIs, including:</span></span>
  - <span data-ttu-id="0cb50-136">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="0cb50-136">fx_directory_create</span></span>
  - <span data-ttu-id="0cb50-137">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="0cb50-137">fx_directory_delete</span></span>
  - <span data-ttu-id="0cb50-138">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="0cb50-138">fx_directory_attributes_set</span></span>
  - <span data-ttu-id="0cb50-139">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="0cb50-139">fx_directory_attributes_read</span></span>
  - <span data-ttu-id="0cb50-140">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="0cb50-140">fx_directory_first_entry_find</span></span>
  - <span data-ttu-id="0cb50-141">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="0cb50-141">fx_directory_next_entry_find</span></span>

### <a name="file-services"></a><span data-ttu-id="0cb50-142">Serviços de Ficheiros</span><span class="sxs-lookup"><span data-stu-id="0cb50-142">File Services</span></span>

- <span data-ttu-id="0cb50-143">Flash mínimo de 3.3KB</span><span class="sxs-lookup"><span data-stu-id="0cb50-143">Minimal 3.3KB FLASH</span></span>
- <span data-ttu-id="0cb50-144">Ficheiros abertos ilimitados</span><span class="sxs-lookup"><span data-stu-id="0cb50-144">Unlimited open files</span></span>
- <span data-ttu-id="0cb50-145">Os ficheiros apenas de leitura podem ser abertos várias vezes</span><span class="sxs-lookup"><span data-stu-id="0cb50-145">Read-only files can be opened multiple times</span></span>
- <span data-ttu-id="0cb50-146">Nomes de diretório longos e 8,3 apoiados</span><span class="sxs-lookup"><span data-stu-id="0cb50-146">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="0cb50-147">Suporte de ficheiros contíguos</span><span class="sxs-lookup"><span data-stu-id="0cb50-147">Contiguous file support</span></span>
- <span data-ttu-id="0cb50-148">Lógica de procura rápida</span><span class="sxs-lookup"><span data-stu-id="0cb50-148">Fast seek logic</span></span>
- <span data-ttu-id="0cb50-149">Pré-atribuição de clusters</span><span class="sxs-lookup"><span data-stu-id="0cb50-149">Pre-allocation of clusters</span></span>
- <span data-ttu-id="0cb50-150">Criar, excluir e renomear ficheiros</span><span class="sxs-lookup"><span data-stu-id="0cb50-150">File create, delete, and rename</span></span>
- <span data-ttu-id="0cb50-151">Arquivar ler, escrever e ver</span><span class="sxs-lookup"><span data-stu-id="0cb50-151">File read, write, and see</span></span>
- <span data-ttu-id="0cb50-152">Gestão de atributos de ficheiros</span><span class="sxs-lookup"><span data-stu-id="0cb50-152">File attributes management</span></span>
- <span data-ttu-id="0cb50-153">Traço de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="0cb50-153">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="0cb50-154">APIs de acesso a ficheiros intuitivos, incluindo:</span><span class="sxs-lookup"><span data-stu-id="0cb50-154">Intuitive file access APIs, including:</span></span>
  - <span data-ttu-id="0cb50-155">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="0cb50-155">fx_file_create</span></span>
  - <span data-ttu-id="0cb50-156">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="0cb50-156">fx_file_delete</span></span>
  - <span data-ttu-id="0cb50-157">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="0cb50-157">fx_file_attributes_set</span></span>
  - <span data-ttu-id="0cb50-158">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="0cb50-158">fx_file_attributes_read</span></span>
  - <span data-ttu-id="0cb50-159">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="0cb50-159">fx_file_read</span></span>
  - <span data-ttu-id="0cb50-160">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="0cb50-160">fx_file_seek</span></span>
  - <span data-ttu-id="0cb50-161">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="0cb50-161">fx_file_write</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="0cb50-162">Tecnologia avançada</span><span class="sxs-lookup"><span data-stu-id="0cb50-162">Advanced technology</span></span>

<span data-ttu-id="0cb50-163">Azure RTOS FileX é uma tecnologia avançada, incluindo as seguintes.</span><span class="sxs-lookup"><span data-stu-id="0cb50-163">Azure RTOS FileX is advanced technology, including the following.</span></span>

- <span data-ttu-id="0cb50-164">SUPORTE FAT 12/16/32 e exFAT</span><span class="sxs-lookup"><span data-stu-id="0cb50-164">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="0cb50-165">Suporte de partição múltipla</span><span class="sxs-lookup"><span data-stu-id="0cb50-165">Multiple partition support</span></span>
- <span data-ttu-id="0cb50-166">Dimensionamento automático</span><span class="sxs-lookup"><span data-stu-id="0cb50-166">Automatic scaling</span></span>
- <span data-ttu-id="0cb50-167">Endian neutro</span><span class="sxs-lookup"><span data-stu-id="0cb50-167">Endian neutral</span></span>
- <span data-ttu-id="0cb50-168">Nome de arquivo longo e suporte 8.3</span><span class="sxs-lookup"><span data-stu-id="0cb50-168">Long file name and 8.3 support</span></span>
- <span data-ttu-id="0cb50-169">Suporte opcional de tolerância à falha</span><span class="sxs-lookup"><span data-stu-id="0cb50-169">Optional fault tolerance support</span></span>
- <span data-ttu-id="0cb50-170">Cache do sector lógico</span><span class="sxs-lookup"><span data-stu-id="0cb50-170">Logical sector cache</span></span>
- <span data-ttu-id="0cb50-171">Cache de entrada de GORDURA</span><span class="sxs-lookup"><span data-stu-id="0cb50-171">FAT entry cache</span></span>
- <span data-ttu-id="0cb50-172">Pré-atribuição de clusters</span><span class="sxs-lookup"><span data-stu-id="0cb50-172">Pre-allocation of clusters</span></span>
- <span data-ttu-id="0cb50-173">Suporte de ficheiros contíguos</span><span class="sxs-lookup"><span data-stu-id="0cb50-173">Contiguous file support</span></span>
- <span data-ttu-id="0cb50-174">Métricas de desempenho opcionais</span><span class="sxs-lookup"><span data-stu-id="0cb50-174">Optional performance metrics</span></span>
- <span data-ttu-id="0cb50-175">Suporte de análise do sistema Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="0cb50-175">Azure RTOS TraceX system analysis support</span></span>

## <a name="nornand-wear-leveling-azure-rtos-levelx"></a><span data-ttu-id="0cb50-176">Nivelamento de desgaste NOR/NAND (Azure RTOS LevelX)</span><span class="sxs-lookup"><span data-stu-id="0cb50-176">NOR/NAND Wear Leveling (Azure RTOS LevelX)</span></span>

<span data-ttu-id="0cb50-177">Azure RTOS LevelX é o produto de nivelamento de desgaste NOR/NAND FLASH da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0cb50-177">Azure RTOS LevelX is Microsoft’s NOR/NAND FLASH wear leveling product.</span></span> <span data-ttu-id="0cb50-178">O Azure RTOS LevelX pode ser usado em conjunto com o FileX ou como uma biblioteca do sector FLASH de leitura/escrita autónoma para a aplicação.</span><span class="sxs-lookup"><span data-stu-id="0cb50-178">Azure RTOS LevelX can be used in conjunction with FileX or as a stand-alone, direct read/write FLASH sector library for the application.</span></span>
