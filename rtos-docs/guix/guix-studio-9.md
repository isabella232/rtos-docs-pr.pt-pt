---
title: Linha de Comando do Estúdio GUIX
description: O GUIX Studio fornece invocação de linha de comando que é útil para construir oleodutos que são necessários para atualizar os ficheiros de saída gerados pelo Estúdio.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 9f9bfc67c524a77b5bf736407bf2ca372ce98308
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826293"
---
# <a name="chapter-9-guix-studio-command-line"></a><span data-ttu-id="3a391-103">Capítulo 9: Linha de Comando do Estúdio GUIX</span><span class="sxs-lookup"><span data-stu-id="3a391-103">Chapter 9: GUIX Studio Command Line</span></span>

<span data-ttu-id="3a391-104">O GUIX Studio suporta a invocação da linha de comando, que é útil para construir oleodutos que são necessários para atualizar os ficheiros de saída gerados pelo Estúdio.</span><span class="sxs-lookup"><span data-stu-id="3a391-104">GUIX Studio supports command-line invocation,  which is useful for build pipelines that are required to update of the Studio-generated output files.</span></span>

## <a name="command-line-usage"></a><span data-ttu-id="3a391-105">Command-Line Utilização</span><span class="sxs-lookup"><span data-stu-id="3a391-105">Command-Line Usage</span></span>

<span data-ttu-id="3a391-106">**Utilização:** argumento \[ de opção guix_studio \] \[\]</span><span class="sxs-lookup"><span data-stu-id="3a391-106">**Usage:** guix_studio \[OPTION\] \[ARGUMENT\]</span></span>

<span data-ttu-id="3a391-107">Abra o projeto *.gxp.*</span><span class="sxs-lookup"><span data-stu-id="3a391-107">Open the *.gxp* project.</span></span>

<span data-ttu-id="3a391-108">Abra o projeto Studio e gere os ficheiros de saída desejados.</span><span class="sxs-lookup"><span data-stu-id="3a391-108">Open the Studio project and generate desired output files.</span></span>


<span data-ttu-id="3a391-109">**Exemplos:**</span><span class="sxs-lookup"><span data-stu-id="3a391-109">**Examples:**</span></span>

`guix_studio demo.gxp`  
<span data-ttu-id="3a391-110">Projeto aberto "demo.gxp"</span><span class="sxs-lookup"><span data-stu-id="3a391-110">Open "demo.gxp" project</span></span>


`guix_studio.exe –p demo.gxp`  
<span data-ttu-id="3a391-111">Projeto aberto "demo.gxp"</span><span class="sxs-lookup"><span data-stu-id="3a391-111">Open "demo.gxp" project</span></span>


`guix_studio.exe –n –p demo.gxp`  
<span data-ttu-id="3a391-112">Gere todos os ficheiros de saída do projeto demo.gxp.</span><span class="sxs-lookup"><span data-stu-id="3a391-112">Generate all output files of demo.gxp project.</span></span>

`guix_studio.exe –n –r –p demo.gxp`  
<span data-ttu-id="3a391-113">Gerar ficheiros de recursos do projeto demo.gxp</span><span class="sxs-lookup"><span data-stu-id="3a391-113">Generate resource files of demo.gxp project</span></span>


## <a name="command-line-options"></a><span data-ttu-id="3a391-114">Opções Command-Line</span><span class="sxs-lookup"><span data-stu-id="3a391-114">Command-Line Options</span></span>

```C
***-n --nogui***  
```

<span data-ttu-id="3a391-115">A opção "nogui".</span><span class="sxs-lookup"><span data-stu-id="3a391-115">The "nogui" option.</span></span> <span data-ttu-id="3a391-116">Diga ao GUIX Studio para funcionar sem iniciar a interface de UI de janela.</span><span class="sxs-lookup"><span data-stu-id="3a391-116">Tell GUIX Studio to run without starting the windowing UI interface.</span></span>

```C
***-o pathname***  
***--log***  
```

<span data-ttu-id="3a391-117">Iniciar sessão, especificar um ficheiro de registo.</span><span class="sxs-lookup"><span data-stu-id="3a391-117">Log option, specify a log file.</span></span>

```C
***-b***  
***--binary***  
```

<span data-ttu-id="3a391-118">Opção de recurso binário.</span><span class="sxs-lookup"><span data-stu-id="3a391-118">Binary resource option.</span></span> <span data-ttu-id="3a391-119">Produz um ficheiro de recursos binários em vez de um ficheiro C.</span><span class="sxs-lookup"><span data-stu-id="3a391-119">Produces a binary resource file rather than a C file.</span></span>

```C
***-d display1, display2***  
***--display***  
```

<span data-ttu-id="3a391-120">A opção de apresentar nomes.</span><span class="sxs-lookup"><span data-stu-id="3a391-120">Display names option.</span></span> <span data-ttu-id="3a391-121">Se esta opção for utilizada, apenas os nomes de visualização especificados estão incluídos em qualquer recurso ou ficheiros de especificações gerados.</span><span class="sxs-lookup"><span data-stu-id="3a391-121">If this option is used, then only the specified display names are included in any generated resource or specification files.</span></span> <span data-ttu-id="3a391-122">Se esta opção não for utilizada, todos os ecrãs estão incluídos.</span><span class="sxs-lookup"><span data-stu-id="3a391-122">If this option is not used,  all displays are included.</span></span>

```C
***-t theme1, theme2***  
***--theme***  
```

<span data-ttu-id="3a391-123">Opção nome(s) tema.</span><span class="sxs-lookup"><span data-stu-id="3a391-123">Theme name(s) option.</span></span> <span data-ttu-id="3a391-124">Se esta opção for utilizada, apenas os nomes temáticos especificados estão incluídos em qualquer recurso ou ficheiros de especificações gerados.</span><span class="sxs-lookup"><span data-stu-id="3a391-124">If this option is used, then only the specified theme names are included in any generated resource or specification files.</span></span> <span data-ttu-id="3a391-125">Se esta opção não for utilizada, todos os temas estão incluídos.</span><span class="sxs-lookup"><span data-stu-id="3a391-125">If this option is not used, all themes are included.</span></span>

```C
***-l langage1, language2***  
***--language***  
```

<span data-ttu-id="3a391-126">Opção nome(s) nome de idioma.</span><span class="sxs-lookup"><span data-stu-id="3a391-126">Language name(s) option.</span></span> <span data-ttu-id="3a391-127">Se esta opção for utilizada, os nomes de idioma especificados estão incluídos nos ficheiros de recursos ou especificações gerados.</span><span class="sxs-lookup"><span data-stu-id="3a391-127">If this option is used,  the specified language names are included in the generated resource or specification files.</span></span> <span data-ttu-id="3a391-128">Caso contrário, todos os nomes linguísticos estão incluídos.</span><span class="sxs-lookup"><span data-stu-id="3a391-128">Otherwise all language names are included.</span></span>

```C
***-r [filename]***  
***--resource***  
```

<span data-ttu-id="3a391-129">A opção de recurso especifica que o Studio deve produzir um ficheiro de recursos para exibições previamente designadas, temas e idiomas.</span><span class="sxs-lookup"><span data-stu-id="3a391-129">The resource option, specifies that Studio should produce a resource file for previously designated display(s), theme(s), and language(s).</span></span>

```C
***-s [filename]***  
***--specification***  
```

<span data-ttu-id="3a391-130">A opção de especificação, especificar que o estúdio deve produzir um ficheiro de especificações para display(s) designados, temas e idiomas.</span><span class="sxs-lookup"><span data-stu-id="3a391-130">The specification option, specify that studio should produce a specification file for designated display(s), theme(s), and language(s).</span></span>

```C
***-p project_pathname***  
***--project***  
```

<span data-ttu-id="3a391-131">Opção de nome de pathname do projeto, especifique o projeto exemplo a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="3a391-131">Project pathname option, specify the example project to be loaded.</span></span>

```C
***-i [pathname]***  
***--import***  
```

<span data-ttu-id="3a391-132">Cadeia de importação de xliff ou ficheiro de formato csv.</span><span class="sxs-lookup"><span data-stu-id="3a391-132">Import string from xliff or csv format file.</span></span>

<span data-ttu-id="3a391-133">***-big_endian***</span><span class="sxs-lookup"><span data-stu-id="3a391-133">***--big_endian***</span></span>  
<span data-ttu-id="3a391-134">Gerar dados de recursos em formato de grande ponta.</span><span class="sxs-lookup"><span data-stu-id="3a391-134">Generate resource data in big-endian format.</span></span>
