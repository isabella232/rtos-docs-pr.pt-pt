---
title: Compreenda O Azure RTOS Filex
description: O Azure RTOS FileX é um sistema de ficheiros compatível com ficheiros de alto desempenho (FAT)que está totalmente integrado com o Azure RTOS ThreadX e está disponível para todos os processadores suportados. Tal como o Azure RTOS ThreadX, o Azure RTOS FileX foi concebido para ter uma pequena pegada e alto desempenho, tornando-o ideal para as aplicações profundamente incorporadas que requerem operações de gestão de ficheiros. O FileX suporta a maioria dos meios físicos, incluindo RAM, Azure RTOS USBX, SD CARD e NAND/NOR memórias flash via Azure RTOS LevelX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: a3a20c8ced3426399ceedf6994c872ce7aec93c3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827320"
---
# <a name="overview-of-azure-rtos-filex"></a><span data-ttu-id="5daf2-105">Visão geral do Azure RTOS FileX</span><span class="sxs-lookup"><span data-stu-id="5daf2-105">Overview of Azure RTOS FileX</span></span>

<span data-ttu-id="5daf2-106">O sistema de ficheiros incorporado Azure RTOS FileX é a solução avançada e industrial da Azure RTOS para formatos de ficheiros Microsoft FAT, projetado especificamente para aplicações profundamente incorporadas, em tempo real e IoT.</span><span class="sxs-lookup"><span data-stu-id="5daf2-106">Azure RTOS FileX embedded file system is Azure RTOS's advanced, industrial grade solution for Microsoft FAT file formats, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="5daf2-107">O Azure RTOS FileX suporta todos os formatos de ficheiros da Microsoft, incluindo FAT12, FAT16, FAT32 e exFAT.</span><span class="sxs-lookup"><span data-stu-id="5daf2-107">Azure RTOS FileX supports all of Microsoft’s file formats, including FAT12, FAT16, FAT32, and exFAT.</span></span> <span data-ttu-id="5daf2-108">O FileX também oferece tolerância opcional de falhas e nivelamento de desgaste FLASH através de um produto addon chamado [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/).</span><span class="sxs-lookup"><span data-stu-id="5daf2-108">FileX also offers optional fault tolerance and FLASH wear leveling via an add-on product called [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/).</span></span> <span data-ttu-id="5daf2-109">Tudo isto combinado com uma pequena pegada, execução rápida e facilidade superior de utilização, fazem do Azure RTOS FileX a escolha ideal para as aplicações IoT incorporadas mais exigentes.</span><span class="sxs-lookup"><span data-stu-id="5daf2-109">All of this combined with a small footprint, fast execution, and superior ease-of-use, make Azure RTOS FileX the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="5daf2-110">Protocolos da API</span><span class="sxs-lookup"><span data-stu-id="5daf2-110">API protocols</span></span>

### <a name="azure-rtos-filex-api"></a><span data-ttu-id="5daf2-111">Azure RTOS FileX API</span><span class="sxs-lookup"><span data-stu-id="5daf2-111">Azure RTOS FileX API</span></span>

- <span data-ttu-id="5daf2-112">API intuitiva e consistente</span><span class="sxs-lookup"><span data-stu-id="5daf2-112">Intuitive and consistent API</span></span>
- <span data-ttu-id="5daf2-113">Convenção de nomeação de substantivos</span><span class="sxs-lookup"><span data-stu-id="5daf2-113">Noun-verb naming convention</span></span>
- <span data-ttu-id="5daf2-114">Todas as APIs têm *fx_* a identificar facilmente como FileX</span><span class="sxs-lookup"><span data-stu-id="5daf2-114">All APIs have leading *fx_* to easily identify as FileX</span></span>
- <span data-ttu-id="5daf2-115">ApIs de bloqueio têm tempo limite opcional de fio</span><span class="sxs-lookup"><span data-stu-id="5daf2-115">Blocking APIs have optional thread timeout</span></span>
- <span data-ttu-id="5daf2-116">Chamadas opcionais de notificação do utilizador para meios de comunicação e operações de ficheiros</span><span class="sxs-lookup"><span data-stu-id="5daf2-116">Optional user-notification callbacks for media and file operations</span></span>
- <span data-ttu-id="5daf2-117">Consulte o Guia de [Utilizador Azure RTOS FileX](about-this-guide.md) para mais detalhes</span><span class="sxs-lookup"><span data-stu-id="5daf2-117">Please see [Azure RTOS FileX User Guide](about-this-guide.md) for more details</span></span>

### <a name="media-services"></a><span data-ttu-id="5daf2-118">Serviços de Multimédia</span><span class="sxs-lookup"><span data-stu-id="5daf2-118">Media Services</span></span>

- <span data-ttu-id="5daf2-119">SUPORTE FAT 12/16/32 e exFAT</span><span class="sxs-lookup"><span data-stu-id="5daf2-119">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="5daf2-120">Flash mínimo de 6KB, RAM de 2,5KB</span><span class="sxs-lookup"><span data-stu-id="5daf2-120">Minimal 6KB FLASH, 2.5KB RAM</span></span>
- <span data-ttu-id="5daf2-121">Serviços completos de acesso aos meios de comunicação</span><span class="sxs-lookup"><span data-stu-id="5daf2-121">Complete media access services</span></span>
- <span data-ttu-id="5daf2-122">Número ilimitado de instâncias mediáticas</span><span class="sxs-lookup"><span data-stu-id="5daf2-122">Unlimited number of media instance</span></span>
- <span data-ttu-id="5daf2-123">Interface de condutor do sector de leitura/escrita simples</span><span class="sxs-lookup"><span data-stu-id="5daf2-123">Simple read/write logical sector driver interface</span></span>
- <span data-ttu-id="5daf2-124">Suporte de partição múltipla</span><span class="sxs-lookup"><span data-stu-id="5daf2-124">Multiple partition support</span></span>
- <span data-ttu-id="5daf2-125">Cache do sector lógico</span><span class="sxs-lookup"><span data-stu-id="5daf2-125">Logical sector cache</span></span>
- <span data-ttu-id="5daf2-126">Cache de entrada de GORDURA</span><span class="sxs-lookup"><span data-stu-id="5daf2-126">FAT entry cache</span></span>
- <span data-ttu-id="5daf2-127">Suporte opcional de tolerância à falha</span><span class="sxs-lookup"><span data-stu-id="5daf2-127">Optional fault tolerance support</span></span>
- <span data-ttu-id="5daf2-128">Atualização de FAT Secundária Diferida</span><span class="sxs-lookup"><span data-stu-id="5daf2-128">Deferred Secondary FAT update</span></span>
- <span data-ttu-id="5daf2-129">Traço de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="5daf2-129">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="5daf2-130">APIs de acesso a meios de comunicação intuitivos, incluindo:</span><span class="sxs-lookup"><span data-stu-id="5daf2-130">Intuitive media access APIs, including:</span></span>
  - <span data-ttu-id="5daf2-131">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="5daf2-131">fx_media_open</span></span>
  - <span data-ttu-id="5daf2-132">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="5daf2-132">fx_media_close</span></span>
  - <span data-ttu-id="5daf2-133">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="5daf2-133">fx_media_format</span></span>
  - <span data-ttu-id="5daf2-134">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="5daf2-134">fx_media_space_available</span></span>

### <a name="directory-services"></a><span data-ttu-id="5daf2-135">Serviços de Diretório</span><span class="sxs-lookup"><span data-stu-id="5daf2-135">Directory Services</span></span>

- <span data-ttu-id="5daf2-136">Até 256 byte caminhos</span><span class="sxs-lookup"><span data-stu-id="5daf2-136">Up to 256 byte paths</span></span>
- <span data-ttu-id="5daf2-137">Nomes de diretório longos e 8,3 apoiados</span><span class="sxs-lookup"><span data-stu-id="5daf2-137">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="5daf2-138">Diretório criar & excluir</span><span class="sxs-lookup"><span data-stu-id="5daf2-138">Directory create & delete</span></span>
- <span data-ttu-id="5daf2-139">Navegação diretório e traversal</span><span class="sxs-lookup"><span data-stu-id="5daf2-139">Directory navigation and traversal</span></span>
- <span data-ttu-id="5daf2-140">Gestão de atributos de diretório</span><span class="sxs-lookup"><span data-stu-id="5daf2-140">Directory attributes management</span></span>
- <span data-ttu-id="5daf2-141">Traço de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="5daf2-141">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="5daf2-142">APIs de acesso a diretórios intuitivos, incluindo:</span><span class="sxs-lookup"><span data-stu-id="5daf2-142">Intuitive directory access APIs, including:</span></span>
  - <span data-ttu-id="5daf2-143">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="5daf2-143">fx_directory_create</span></span>
  - <span data-ttu-id="5daf2-144">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="5daf2-144">fx_directory_delete</span></span>
  - <span data-ttu-id="5daf2-145">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5daf2-145">fx_directory_attributes_set</span></span>
  - <span data-ttu-id="5daf2-146">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5daf2-146">fx_directory_attributes_read</span></span>
  - <span data-ttu-id="5daf2-147">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="5daf2-147">fx_directory_first_entry_find</span></span>
  - <span data-ttu-id="5daf2-148">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="5daf2-148">fx_directory_next_entry_find</span></span>

### <a name="file-services"></a><span data-ttu-id="5daf2-149">Serviços de Ficheiros</span><span class="sxs-lookup"><span data-stu-id="5daf2-149">File Services</span></span>

- <span data-ttu-id="5daf2-150">Flash mínimo de 3.3KB</span><span class="sxs-lookup"><span data-stu-id="5daf2-150">Minimal 3.3KB FLASH</span></span>
- <span data-ttu-id="5daf2-151">Ficheiros abertos ilimitados</span><span class="sxs-lookup"><span data-stu-id="5daf2-151">Unlimited open files</span></span>
- <span data-ttu-id="5daf2-152">Os ficheiros apenas de leitura podem ser abertos várias vezes</span><span class="sxs-lookup"><span data-stu-id="5daf2-152">Read-only files can be opened multiple times</span></span>
- <span data-ttu-id="5daf2-153">Nomes de diretório longos e 8,3 apoiados</span><span class="sxs-lookup"><span data-stu-id="5daf2-153">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="5daf2-154">Suporte de ficheiros contíguos</span><span class="sxs-lookup"><span data-stu-id="5daf2-154">Contiguous file support</span></span>
- <span data-ttu-id="5daf2-155">Lógica de procura rápida</span><span class="sxs-lookup"><span data-stu-id="5daf2-155">Fast seek logic</span></span>
- <span data-ttu-id="5daf2-156">Pré-atribuição de clusters</span><span class="sxs-lookup"><span data-stu-id="5daf2-156">Pre-allocation of clusters</span></span>
- <span data-ttu-id="5daf2-157">Criar, excluir e renomear ficheiros</span><span class="sxs-lookup"><span data-stu-id="5daf2-157">File create, delete, and rename</span></span>
- <span data-ttu-id="5daf2-158">Arquivar ler, escrever e ver</span><span class="sxs-lookup"><span data-stu-id="5daf2-158">File read, write, and see</span></span>
- <span data-ttu-id="5daf2-159">Gestão de atributos de ficheiros</span><span class="sxs-lookup"><span data-stu-id="5daf2-159">File attributes management</span></span>
- <span data-ttu-id="5daf2-160">Traço de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="5daf2-160">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="5daf2-161">APIs de acesso a ficheiros intuitivos, incluindo:</span><span class="sxs-lookup"><span data-stu-id="5daf2-161">Intuitive file access APIs, including:</span></span>
  - <span data-ttu-id="5daf2-162">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="5daf2-162">fx_file_create</span></span>
  - <span data-ttu-id="5daf2-163">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="5daf2-163">fx_file_delete</span></span>
  - <span data-ttu-id="5daf2-164">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="5daf2-164">fx_file_attributes_set</span></span>
  - <span data-ttu-id="5daf2-165">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="5daf2-165">fx_file_attributes_read</span></span>
  - <span data-ttu-id="5daf2-166">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="5daf2-166">fx_file_read</span></span>
  - <span data-ttu-id="5daf2-167">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="5daf2-167">fx_file_seek</span></span>
  - <span data-ttu-id="5daf2-168">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="5daf2-168">fx_file_write</span></span>

## <a name="small-footprint"></a><span data-ttu-id="5daf2-169">Pequena pegada</span><span class="sxs-lookup"><span data-stu-id="5daf2-169">Small-footprint</span></span>

<span data-ttu-id="5daf2-170">O sistema de ficheiros incorporado Azure RTOS FileX tem uma pegada mínima notável de 8,6 KB a 12 KB para suporte básico de leitura/escrita de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="5daf2-170">Azure RTOS FileX embedded file system has a remarkably small minimal footprint of 8.6 KB to 12 KB for basic file read/write support.</span></span> <span data-ttu-id="5daf2-171">O uso mínimo de Azure RTOS FileX RAM está na ordem de 1.8 KB para uma instância de mídia e com apenas uma cache lógico de 512 byte sectores.</span><span class="sxs-lookup"><span data-stu-id="5daf2-171">Minimal Azure RTOS FileX RAM usage is on the order of 1.8 KB for one media instance and with only a 512-byte logical sector cache.</span></span> <span data-ttu-id="5daf2-172">Tal como o Azure RTOS ThreadX, o tamanho do Azure RTOS FileX escala automaticamente com base nos serviços utilizados pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="5daf2-172">Like Azure RTOS ThreadX, the size of Azure RTOS FileX automatically scales based on the services used by the application.</span></span> <span data-ttu-id="5daf2-173">Isto praticamente elimina a necessidade de configuração complicada e constrói parâmetros, tornando as coisas mais fáceis para o desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="5daf2-173">This virtually eliminates the need for complicated configuration and builds parameters, making things easier for the developer.</span></span>

## <a name="fast-execution"></a><span data-ttu-id="5daf2-174">Execução rápida</span><span class="sxs-lookup"><span data-stu-id="5daf2-174">Fast execution</span></span>

<span data-ttu-id="5daf2-175">O Azure RTOS FileX fornece uma cache lógico do sector, bem como uma cache de entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="5daf2-175">Azure RTOS FileX provides a logical sector cache as well as a FAT entry cache.</span></span> <span data-ttu-id="5daf2-176">Os tamanhos de ambos estão sob controlo direto da aplicação.</span><span class="sxs-lookup"><span data-stu-id="5daf2-176">The sizes of both are under direct control of the application.</span></span> <span data-ttu-id="5daf2-177">Além disso, o Azure RTOS FileX fornece alocação contígua de cluster e leitura e escrita diretas consecutivas de cluster.</span><span class="sxs-lookup"><span data-stu-id="5daf2-177">In addition, Azure RTOS FileX provides contiguous cluster allocation and direct consecutive cluster reading and writing.</span></span> <span data-ttu-id="5daf2-178">Os pedidos de leitura/escrita de sectores inteiros são feitos diretamente entre o tampão de aplicação e os meios de comunicação – ou seja, não é feito nenhum tampão intermédio.</span><span class="sxs-lookup"><span data-stu-id="5daf2-178">Read/write requests of whole sectors are done directly between the application buffer and the media – that is, no intermediate buffering is done.</span></span> <span data-ttu-id="5daf2-179">Tudo isto e uma filosofia geral de design orientada para o desempenho ajuda o Azure RTOS FileX a alcançar o desempenho mais rápido possível.</span><span class="sxs-lookup"><span data-stu-id="5daf2-179">All of this and a general performance-oriented design philosophy helps Azure RTOS FileX achieve the fastest possible performance.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="5daf2-180">Tecnologia avançada</span><span class="sxs-lookup"><span data-stu-id="5daf2-180">Advanced technology</span></span>

<span data-ttu-id="5daf2-181">Azure RTOS FileX é uma tecnologia avançada, incluindo as seguintes.</span><span class="sxs-lookup"><span data-stu-id="5daf2-181">Azure RTOS FileX is advanced technology, including the following.</span></span>

- <span data-ttu-id="5daf2-182">SUPORTE FAT 12/16/32 e exFAT</span><span class="sxs-lookup"><span data-stu-id="5daf2-182">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="5daf2-183">Suporte de partição múltipla</span><span class="sxs-lookup"><span data-stu-id="5daf2-183">Multiple partition support</span></span>
- <span data-ttu-id="5daf2-184">Dimensionamento automático</span><span class="sxs-lookup"><span data-stu-id="5daf2-184">Automatic scaling</span></span>
- <span data-ttu-id="5daf2-185">Endian neutro</span><span class="sxs-lookup"><span data-stu-id="5daf2-185">Endian neutral</span></span>
- <span data-ttu-id="5daf2-186">Nome de arquivo longo e suporte 8.3</span><span class="sxs-lookup"><span data-stu-id="5daf2-186">Long file name and 8.3 support</span></span>
- <span data-ttu-id="5daf2-187">Suporte opcional de tolerância à falha</span><span class="sxs-lookup"><span data-stu-id="5daf2-187">Optional fault tolerance support</span></span>
- <span data-ttu-id="5daf2-188">Cache do sector lógico</span><span class="sxs-lookup"><span data-stu-id="5daf2-188">Logical sector cache</span></span>
- <span data-ttu-id="5daf2-189">Cache de entrada de GORDURA</span><span class="sxs-lookup"><span data-stu-id="5daf2-189">FAT entry cache</span></span>
- <span data-ttu-id="5daf2-190">Pré-atribuição de clusters</span><span class="sxs-lookup"><span data-stu-id="5daf2-190">Pre-allocation of clusters</span></span>
- <span data-ttu-id="5daf2-191">Suporte de ficheiros contíguos</span><span class="sxs-lookup"><span data-stu-id="5daf2-191">Contiguous file support</span></span>
- <span data-ttu-id="5daf2-192">Métricas de desempenho opcionais</span><span class="sxs-lookup"><span data-stu-id="5daf2-192">Optional performance metrics</span></span>
- <span data-ttu-id="5daf2-193">Suporte de análise do sistema Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="5daf2-193">Azure RTOS TraceX system analysis support</span></span>

## <a name="nornand-wear-leveling-azure-rtos-levelx"></a><span data-ttu-id="5daf2-194">Nivelamento de desgaste NOR/NAND (Azure RTOS LevelX)</span><span class="sxs-lookup"><span data-stu-id="5daf2-194">NOR/NAND Wear Leveling (Azure RTOS LevelX)</span></span>

<span data-ttu-id="5daf2-195">Azure RTOS LevelX é o produto de nivelamento de desgaste NOR/NAND FLASH da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5daf2-195">Azure RTOS LevelX is Microsoft’s NOR/NAND FLASH wear leveling product.</span></span> <span data-ttu-id="5daf2-196">O Azure RTOS LevelX pode ser usado em conjunto com o FileX ou como uma biblioteca do sector FLASH de leitura/escrita autónoma para a aplicação.</span><span class="sxs-lookup"><span data-stu-id="5daf2-196">Azure RTOS LevelX can be used in conjunction with FileX or as a stand-alone, direct read/write FLASH sector library for the application.</span></span>

## <a name="fastest-time-to-market"></a><span data-ttu-id="5daf2-197">O tempo de venda mais rápido</span><span class="sxs-lookup"><span data-stu-id="5daf2-197">Fastest time-to-market</span></span>

<span data-ttu-id="5daf2-198">O Azure RTOS FileX é fácil de instalar, aprender, usar, depurar, verificar, certificar e manter.</span><span class="sxs-lookup"><span data-stu-id="5daf2-198">Azure RTOS FileX is easy to install, learn, use, debug, verify, certify, and maintain.</span></span> <span data-ttu-id="5daf2-199">Como resultado, o Azure RTOS FileX é um dos sistemas de ficheiros FAT mais populares para dispositivos IoT incorporados.</span><span class="sxs-lookup"><span data-stu-id="5daf2-199">As a result, Azure RTOS FileX is one of the most popular FAT file systems for embedded IoT devices.</span></span> <span data-ttu-id="5daf2-200">Seguem-se algumas razões para a nossa vantagem consistente no mercado:</span><span class="sxs-lookup"><span data-stu-id="5daf2-200">The following are some reasons for our consistent time-to-market advantage:</span></span>

- <span data-ttu-id="5daf2-201">Documentação de Qualidade – por favor, reveja [o nosso Guia de Utilizador Azure RTOS FileX](about-this-guide.md) e consulte por si mesmo!</span><span class="sxs-lookup"><span data-stu-id="5daf2-201">Quality Documentation – please review our [Azure RTOS FileX User Guide](about-this-guide.md) and see for yourself!</span></span>
- <span data-ttu-id="5daf2-202">Disponibilidade completa do Código Fonte</span><span class="sxs-lookup"><span data-stu-id="5daf2-202">Complete Source Code Availability</span></span>
- <span data-ttu-id="5daf2-203">API de fácil utilização</span><span class="sxs-lookup"><span data-stu-id="5daf2-203">Easy-to-use API</span></span>
- <span data-ttu-id="5daf2-204">Conjunto de recursos abrangente e avançado</span><span class="sxs-lookup"><span data-stu-id="5daf2-204">Comprehensive and Advanced Feature Set</span></span>

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a><span data-ttu-id="5daf2-205">Pré-certificada pela TUV e UL para muitas normas de segurança</span><span class="sxs-lookup"><span data-stu-id="5daf2-205">Pre-certified  by TUV and UL to many safety standards</span></span>

![SGS-TUV Saar](./media/overview-filex/partener-logo-sgs-tuv-saar-2.png)

<span data-ttu-id="5daf2-207">O Azure RTOS FileX foi certificado pela SGS-TUV Saar para utilização em sistemas críticos de segurança, de acordo com o IEC-61508 SIL 4, IEC-62304 SW Safety Class C, ISO 26262 ASIL D e EN 50128.</span><span class="sxs-lookup"><span data-stu-id="5daf2-207">Azure RTOS FileX has been certified by SGS-TUV Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304  SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="5daf2-208">A certificação confirma que o FileX pode ser utilizado no desenvolvimento de software relacionado com a segurança para os mais elevados níveis de integridade de segurança da IEC-61508, IEC-62304, ISO 26262 e EN 50128 para a "Segurança Funcional dos sistemas eletrónicos, eletrónicos e programáveis relacionados com a segurança electrónica".</span><span class="sxs-lookup"><span data-stu-id="5daf2-208">The certification confirms that FileX can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="5daf2-209">A SGS-TUV Saar, formada através de uma joint venture da SGS-Group alemã e tuv Saarland, tornou-se a principal empresa acreditada e independente para testes, auditorias, verificação e certificação de software incorporado para sistemas relacionados com a segurança em todo o mundo.</span><span class="sxs-lookup"><span data-stu-id="5daf2-209">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying, and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="5daf2-210">A norma de segurança industrial IEC 61508, e todas as normas que dela derivam, incluindo a IEC-62304, a ISO 26262 e a EN 50128, são utilizadas para garantir a segurança funcional de dispositivos médicos elétricos, eletrónicos e programáveis relacionados com a segurança electrónica, sistemas de controlo de processos, máquinas industriais, automóveis e sistemas de controlo ferroviário.</span><span class="sxs-lookup"><span data-stu-id="5daf2-210">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to assure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles, and railway control systems.</span></span>

:::image type="content" source="media/overview-filex/cru-logo-certification.png" alt-text="Certificação CRU UL":::

<span data-ttu-id="5daf2-212">O Azure RTOS FileX foi reconhecido pela UL pelo cumprimento do anexo H da UL 60730-1, do CSA E60730-1 Anexo H, do IEC 60730-1 anexo H, ul 60335-1 anexo R, do IEC 60335-1 Anexo R, da UL e das normas de segurança 1998 para as normas de segurança em componentes programáveis.</span><span class="sxs-lookup"><span data-stu-id="5daf2-212">Azure RTOS FileX has been recognized by UL for compliance with UL 60730-1 Annex H, CSA E60730-1 Annex H, IEC 60730-1 Annex H, UL 60335-1 Annex R, IEC 60335-1 Annex R, and UL 1998 safety standards for software in programmable components.</span></span> <span data-ttu-id="5daf2-213">A UL é uma empresa global, independente e de ciência da segurança, com mais de um século de experiência em soluções de segurança inovadoras, que vão desde a adoção pública de eletricidade até avanços na sustentabilidade, energias renováveis e nanotecnologia.</span><span class="sxs-lookup"><span data-stu-id="5daf2-213">UL is a global, independent, safety-science company with more than a century of expertise innovating safety solutions, ranging from the public adoption of electricity to breakthroughs in sustainability, renewable energy, and nanotechnology.</span></span>

<span data-ttu-id="5daf2-214">Estão à venda artefactos (Certificado, Manual de Segurança, Relatório de Teste, etc.) associados às certificações TUV e UL.</span><span class="sxs-lookup"><span data-stu-id="5daf2-214">Artifacts (Certificate, Safety Manual, Test Report, etc.) associated with the TUV and UL certifications are available for sale.</span></span>

<span data-ttu-id="5daf2-215">Nos casos em que a aplicação necessita de certificação adicional, está disponível um serviço de certificação através da Microsoft para fornecer certificação chave-na-curva a vários padrões utilizando a plataforma de hardware real e até mesmo cobrindo o código de aplicação.</span><span class="sxs-lookup"><span data-stu-id="5daf2-215">In cases where the application needs additional certification, a certification service is available through Microsoft for providing turn-key certification to various standards using the actual hardware platform and even covering the application code.</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="5daf2-216">Uma licença simples</span><span class="sxs-lookup"><span data-stu-id="5daf2-216">One Simple License</span></span>

<span data-ttu-id="5daf2-217">Não há qualquer custo para usar e testar o código fonte e nenhum custo para licenças de produção quando implementados em dispositivos pré-licenciados, todos os outros dispositivos precisam de uma licença anual simples.</span><span class="sxs-lookup"><span data-stu-id="5daf2-217">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="5daf2-218">Código fonte completo e de alta qualidade</span><span class="sxs-lookup"><span data-stu-id="5daf2-218">Full, highest-quality source code</span></span>

<span data-ttu-id="5daf2-219">Ao longo dos anos, o código fonte FileX definiu a barra em qualidade e facilidade de compreensão.</span><span class="sxs-lookup"><span data-stu-id="5daf2-219">Throughout the years, FileX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="5daf2-220">Além disso, a convenção de ter uma função por ficheiro prevê uma fácil navegação de origem.</span><span class="sxs-lookup"><span data-stu-id="5daf2-220">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="5daf2-221">Apoia as arquiteturas mais populares</span><span class="sxs-lookup"><span data-stu-id="5daf2-221">Supports most popular architectures</span></span>

<span data-ttu-id="5daf2-222">O Azure RTOS FileX funciona em microprocessadores de 32/64 bits mais populares, fora da caixa, totalmente testados e totalmente suportados, incluindo os seguintes:</span><span class="sxs-lookup"><span data-stu-id="5daf2-222">Azure RTOS FileX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

<span data-ttu-id="5daf2-223">**Dispositivos Analógicos**: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="5daf2-223">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="5daf2-224">**Núcleo de Andes**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="5daf2-224">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="5daf2-225">**Ambiqmicro**: Apollo MCUs</span><span class="sxs-lookup"><span data-stu-id="5daf2-225">**Ambiqmicro**: Apollo MCUs</span></span>

<span data-ttu-id="5daf2-226">**BRAÇO**: ARM7, ARM9, ARM11, Córtex-M0/M3/M4/M7/A15/A5/A7/A8/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="5daf2-226">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="5daf2-227">**Cadência**: Xtensa, Diamante</span><span class="sxs-lookup"><span data-stu-id="5daf2-227">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="5daf2-228">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WiCED WiFi</span><span class="sxs-lookup"><span data-stu-id="5daf2-228">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="5daf2-229">**Cipreste**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="5daf2-229">**Cypress**: RISC-V</span></span>

<span data-ttu-id="5daf2-230">**EnSilica**: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="5daf2-230">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="5daf2-231">**Infineon**: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="5daf2-231">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="5daf2-232">**Intel;** **Intel FPGA**: x36/Pentium, XScale, NIOS II, Ciclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="5daf2-232">**Intel**; **Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="5daf2-233">**Microchip**: AVR32, ARM7, ARM9, Córtex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="5daf2-233">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="5daf2-234">**Microsemi**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="5daf2-234">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="5daf2-235">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="5daf2-235">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="5daf2-236">**Renesas**: SH, HS, V850, RX, RZ, Sinergia</span><span class="sxs-lookup"><span data-stu-id="5daf2-236">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="5daf2-237">**Silício** Laboratórios: EFM32</span><span class="sxs-lookup"><span data-stu-id="5daf2-237">**Silicon** Labs: EFM32</span></span>

<span data-ttu-id="5daf2-238">**Sinopses**: ARC 600, 700, ARC EM, ARC HS</span><span class="sxs-lookup"><span data-stu-id="5daf2-238">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="5daf2-239">**ST**: STM32, ARM7, ARM9, Córtex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="5daf2-239">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="5daf2-240">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span><span class="sxs-lookup"><span data-stu-id="5daf2-240">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="5daf2-241">**Computação de ondas**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, Classe M</span><span class="sxs-lookup"><span data-stu-id="5daf2-241">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="5daf2-242">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="5daf2-242">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

<span data-ttu-id="5daf2-243">*Todos os valores de tempo e tamanho listados são estimativas e podem ser diferentes na sua plataforma de desenvolvimento.*</span><span class="sxs-lookup"><span data-stu-id="5daf2-243">*All timing and size figures listed are estimates and may be different on your development platform.*</span></span>
