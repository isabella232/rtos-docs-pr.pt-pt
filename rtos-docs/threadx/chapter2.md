---
title: Capítulo 2 - Instalação e Utilização do Azure RTOS ThreadX
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do kernel Azure RTOS ThreadX de alto desempenho.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e1bf85d363b07c81f226d494107eae9ba18114a7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825454"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-threadx"></a><span data-ttu-id="14cd6-103">Capítulo 2 - Instalação e Utilização do Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="14cd6-103">Chapter 2 - Installation and Use of Azure RTOS ThreadX</span></span>

<span data-ttu-id="14cd6-104">Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do kernel Azure RTOS ThreadX de alto desempenho.</span><span class="sxs-lookup"><span data-stu-id="14cd6-104">This chapter contains a description of various issues related to installation, setup, and usage of the high-performance Azure RTOS ThreadX kernel.</span></span>

## <a name="host-considerations"></a><span data-ttu-id="14cd6-105">Considerações de Anfitrião</span><span class="sxs-lookup"><span data-stu-id="14cd6-105">Host Considerations</span></span>

<span data-ttu-id="14cd6-106">O software incorporado é geralmente desenvolvido em computadores anfitriões Windows ou Linux (Unix).</span><span class="sxs-lookup"><span data-stu-id="14cd6-106">Embedded software is usually developed on Windows or Linux (Unix) host computers.</span></span> <span data-ttu-id="14cd6-107">Após a compilação da aplicação, ligada e localizada no anfitrião, é descarregada para o hardware alvo para execução.</span><span class="sxs-lookup"><span data-stu-id="14cd6-107">After the application is compiled, linked, and located on the host, it is downloaded to the target hardware for execution.</span></span>

<span data-ttu-id="14cd6-108">Normalmente, o download do alvo é feito a partir do depurar da ferramenta de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="14cd6-108">Usually the target download is done from within the development tool debugger.</span></span> <span data-ttu-id="14cd6-109">Após o download ter terminado, o depurante é responsável por fornecer controlo de execução de alvo (ir, parar, quebrar, etc.) bem como aceder aos registos de memória e processador.</span><span class="sxs-lookup"><span data-stu-id="14cd6-109">After the download has completed, the debugger is responsible for providing target execution control (go, halt, breakpoint, etc.) as well as access to memory and processor registers.</span></span>

<span data-ttu-id="14cd6-110">A maioria dos depurares de ferramentas de desenvolvimento comunicam com o hardware-alvo através de ligações de depuro on-chip (TOC), tais como JTAG (IEEE 1149.1) e Modo de Depuramento de Fundo (BDM).</span><span class="sxs-lookup"><span data-stu-id="14cd6-110">Most development tool debuggers communicate with the target hardware via on-chip debug (OCD) connections such as JTAG (IEEE 1149.1) and Background Debug Mode (BDM).</span></span> <span data-ttu-id="14cd6-111">Os debuggers também comunicam com o hardware alvo através de ligações In-Circuit Emulation (ICE).</span><span class="sxs-lookup"><span data-stu-id="14cd6-111">Debuggers also communicate with target hardware through In-Circuit Emulation (ICE) connections.</span></span> <span data-ttu-id="14cd6-112">As ligações OCD e ICE fornecem soluções robustas com uma intrusão mínima no software residente alvo.</span><span class="sxs-lookup"><span data-stu-id="14cd6-112">Both OCD and ICE connections provide robust solutions with minimal intrusion on the target resident software.</span></span>

<span data-ttu-id="14cd6-113">Quanto aos recursos utilizados no hospedeiro, o código fonte da ThreadX é entregue em formato ASCII e requer aproximadamente 1 MByte de espaço no disco rígido do computador anfitrião.</span><span class="sxs-lookup"><span data-stu-id="14cd6-113">As for resources used on the host, the source code for ThreadX is delivered in ASCII format and requires approximately 1 MByte of space on the host computer's hard disk.</span></span>

## <a name="target-considerations"></a><span data-ttu-id="14cd6-114">Considerações-alvo</span><span class="sxs-lookup"><span data-stu-id="14cd6-114">Target Considerations</span></span>

<span data-ttu-id="14cd6-115">A ThreadX requer entre 2 KBytes e 20 KBytes de Memória Apenas de Leitura (ROM) no alvo.</span><span class="sxs-lookup"><span data-stu-id="14cd6-115">ThreadX requires between 2 KBytes and 20 KBytes of Read Only Memory (ROM) on the target.</span></span> <span data-ttu-id="14cd6-116">Também requer mais 1 a 2 KBytes da Memória de Acesso Aleatório (RAM) do alvo para a pilha do sistema ThreadX e outras estruturas de dados globais.</span><span class="sxs-lookup"><span data-stu-id="14cd6-116">It also requires another 1 to 2 KBytes of the target's Random Access Memory (RAM) for the ThreadX system stack and other global data structures.</span></span>

<span data-ttu-id="14cd6-117">Para funções relacionadas com temporizadores, como intervalos de chamada de serviço, corte de tempo e temporizadores de aplicação para funcionar, o hardware-alvo subjacente deve fornecer uma fonte de interrupção periódica.</span><span class="sxs-lookup"><span data-stu-id="14cd6-117">For timer-related functions like service call time-outs, time-slicing, and application timers to function, the underlying target hardware must provide a periodic interrupt source.</span></span> <span data-ttu-id="14cd6-118">Se o processador tiver esta capacidade, é utilizado pela ThreadX.</span><span class="sxs-lookup"><span data-stu-id="14cd6-118">If the processor has this capability, it is utilized by ThreadX.</span></span> <span data-ttu-id="14cd6-119">Caso contrário, se o processador-alvo não tiver a capacidade de gerar uma interrupção periódica, o hardware do utilizador deve forneca-lo.</span><span class="sxs-lookup"><span data-stu-id="14cd6-119">Otherwise, if the target processor does not have the ability to generate a periodic interrupt, the user's hardware must provide it.</span></span> <span data-ttu-id="14cd6-120">A configuração e configuração da interrupção do temporizador está tipicamente localizada no ficheiro de montagem ***tx_initialize_low_level*** na distribuição ThreadX.</span><span class="sxs-lookup"><span data-stu-id="14cd6-120">Setup and configuration of the timer interrupt is typically located in the ***tx_initialize_low_level*** assembly file in the ThreadX distribution.</span></span>

> [!NOTE]
> <span data-ttu-id="14cd6-121">*O ThreadX continua funcional mesmo que não exista uma fonte de interrupção periódica do temporizador disponível. No entanto, nenhum dos serviços relacionados com o temporizador está funcional.*</span><span class="sxs-lookup"><span data-stu-id="14cd6-121">*ThreadX is still functional even if no periodic timer interrupt source is available. However, none of the timer-related services are functional.*</span></span>

## <a name="product-distribution"></a><span data-ttu-id="14cd6-122">Distribuição de Produtos</span><span class="sxs-lookup"><span data-stu-id="14cd6-122">Product Distribution</span></span>

<span data-ttu-id="14cd6-123">A Azure RTOS ThreadX pode ser obtido a partir do nosso repositório de código de fonte pública em <https://github.com/azure-rtos/threadx/> .</span><span class="sxs-lookup"><span data-stu-id="14cd6-123">Azure RTOS ThreadX can be obtained from our public source code repository at <https://github.com/azure-rtos/threadx/>.</span></span>

<span data-ttu-id="14cd6-124">Segue-se uma lista de vários ficheiros importantes no repositório.</span><span class="sxs-lookup"><span data-stu-id="14cd6-124">The following is a list of several important files in the repository.</span></span>

| <span data-ttu-id="14cd6-125">Nome de arquivo</span><span class="sxs-lookup"><span data-stu-id="14cd6-125">Filename</span></span> | <span data-ttu-id="14cd6-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="14cd6-126">Description</span></span> |
|------------------- | ----------- |
| <span data-ttu-id="14cd6-127">**tx_api.h**</span><span class="sxs-lookup"><span data-stu-id="14cd6-127">**tx_api.h**</span></span>                      | <span data-ttu-id="14cd6-128">Ficheiro de cabeçalho C contendo todos os equacionares do sistema, estruturas de dados e protótipos de serviço.</span><span class="sxs-lookup"><span data-stu-id="14cd6-128">C header file containing all system equates, data structures, and service prototypes.</span></span>                                                             |
| <span data-ttu-id="14cd6-129">**tx_port.h**</span><span class="sxs-lookup"><span data-stu-id="14cd6-129">**tx_port.h**</span></span>                     | <span data-ttu-id="14cd6-130">Ficheiro de cabeçalho C contendo todas as definições e estruturas específicas de dados de desenvolvimento e de destino.</span><span class="sxs-lookup"><span data-stu-id="14cd6-130">C header file containing all development-tool and targetspecific data definitions and structures.</span></span>                                                 |
| <span data-ttu-id="14cd6-131">**demo_threadx.c**</span><span class="sxs-lookup"><span data-stu-id="14cd6-131">**demo_threadx.c**</span></span>                | <span data-ttu-id="14cd6-132">Ficheiro C contendo um pequeno pedido de demonstração.</span><span class="sxs-lookup"><span data-stu-id="14cd6-132">C file containing a small demo application.</span></span>                                                                                                       |
| <span data-ttu-id="14cd6-133">**tx.a (ou tx.lib)**</span><span class="sxs-lookup"><span data-stu-id="14cd6-133">**tx.a (or tx.lib)**</span></span>              | <span data-ttu-id="14cd6-134">Versão binária da biblioteca ThreadX C que é distribuída com o pacote *padrão.*</span><span class="sxs-lookup"><span data-stu-id="14cd6-134">Binary version of the ThreadX C library that is distributed with the *standard* package.</span></span>                                                          |
|                                   |                                                                                                                                                   |

>[!NOTE]
><span data-ttu-id="14cd6-135">*Todos os nomes dos ficheiros estão em minúsculas. Esta convenção de nomeação facilita a conversão dos comandos para plataformas de desenvolvimento Linux (Unix).*</span><span class="sxs-lookup"><span data-stu-id="14cd6-135">*All file names are in lower-case. This naming convention makes it easier to convert the commands to Linux (Unix) development platforms.*</span></span>

## <a name="threadx-installation"></a><span data-ttu-id="14cd6-136">Instalação ThreadX</span><span class="sxs-lookup"><span data-stu-id="14cd6-136">ThreadX Installation</span></span>

<span data-ttu-id="14cd6-137">A ThreadX é instalada através da clonagem do repositório GitHub à sua máquina local.</span><span class="sxs-lookup"><span data-stu-id="14cd6-137">ThreadX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="14cd6-138">Segue-se a sintaxe típica para criar um clone do repositório ThreadX no seu PC.</span><span class="sxs-lookup"><span data-stu-id="14cd6-138">The following is typical syntax for creating a clone of the ThreadX repository on your PC.</span></span>

```c
    git clone https://github.com/azure-rtos/threadx
```

<span data-ttu-id="14cd6-139">Em alternativa, pode descarregar uma cópia do repositório utilizando o botão de descarregamento na página principal do GitHub.</span><span class="sxs-lookup"><span data-stu-id="14cd6-139">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="14cd6-140">Também encontrará instruções para a construção da biblioteca ThreadX na primeira página do repositório online.</span><span class="sxs-lookup"><span data-stu-id="14cd6-140">You will also find instructions for building the ThreadX library on the front page of the online repository.</span></span>

> [!NOTE]
> <span data-ttu-id="14cd6-141">*O software de aplicação precisa de acesso ao ficheiro da biblioteca ThreadX (geralmente **tx.a** ou **tx.lib)** e o C inclui ficheiros **_tx_api.h_* _ e _*_tx_port.h_*_.</span><span class="sxs-lookup"><span data-stu-id="14cd6-141">*Application software needs access to the ThreadX library file (usually **tx.a** or **tx.lib**) and the C include files **_tx_api.h_* _ and _*_tx_port.h_*_.</span></span> <span data-ttu-id="14cd6-142">Isto é conseguido quer estabelecendo o caminho adequado para as ferramentas de desenvolvimento, quer copiando estes ficheiros para o desenvolvimento da aplicação area._</span><span class="sxs-lookup"><span data-stu-id="14cd6-142">This is accomplished either by setting the appropriate path for the development tools or by copying these files into the application development area._</span></span>

## <a name="using-threadx"></a><span data-ttu-id="14cd6-143">Usando ThreadX</span><span class="sxs-lookup"><span data-stu-id="14cd6-143">Using ThreadX</span></span>

<span data-ttu-id="14cd6-144">Para utilizar o ThreadX, o código de aplicação deve incluir ***tx_api.h** _ durante a compilação e ligação com a biblioteca de tempo de execução ThreadX _*_tx.a_*_ (ou _*_tx.lib_\*\*).</span><span class="sxs-lookup"><span data-stu-id="14cd6-144">To use ThreadX, the application code must include ***tx_api.h** _ during compilation and link with the ThreadX run-time library _*_tx.a_*_ (or _*_tx.lib_\*\*).</span></span>

<span data-ttu-id="14cd6-145">São necessários quatro passos para a construção de uma aplicação ThreadX.</span><span class="sxs-lookup"><span data-stu-id="14cd6-145">There are four steps required to build a ThreadX application.</span></span>

1. <span data-ttu-id="14cd6-146">Inclua o ficheiro ***tx_api.h*** em todos os ficheiros de aplicações que utilizam serviços da ThreadX ou estruturas de dados.</span><span class="sxs-lookup"><span data-stu-id="14cd6-146">Include the ***tx_api.h*** file in all application files that use ThreadX services or data structures.</span></span>

1. <span data-ttu-id="14cd6-147">Crie a função padrão C \***main** _ .</span><span class="sxs-lookup"><span data-stu-id="14cd6-147">Create the standard C \***main** _ function.</span></span> <span data-ttu-id="14cd6-148">Esta função deve eventualmente chamar _ *_tx_kernel_enter_*\* para iniciar a ThreadX.</span><span class="sxs-lookup"><span data-stu-id="14cd6-148">This function must eventually call _ *_tx_kernel_enter_*\* to start ThreadX.</span></span> <span data-ttu-id="14cd6-149">A inicialização específica da aplicação que não envolva o ThreadX pode ser adicionada antes de introduzir o núcleo.</span><span class="sxs-lookup"><span data-stu-id="14cd6-149">Application-specific initialization that does not involve ThreadX may be added prior to entering the kernel.</span></span>

      > [!IMPORTANT]
      > <span data-ttu-id="14cd6-150">\*A função de entrada ThreadX \***tx_kernel_enter** _ não volta.</span><span class="sxs-lookup"><span data-stu-id="14cd6-150">\*The ThreadX entry function \***tx_kernel_enter** _ does not return.</span></span> <span data-ttu-id="14cd6-151">Por isso, certifique-se de que não escame quaisquer chamadas de processamento ou função após it._</span><span class="sxs-lookup"><span data-stu-id="14cd6-151">So be sure not to place any processing or function calls after it._</span></span>

1. <span data-ttu-id="14cd6-152">Crie a função ***tx_application_define.***</span><span class="sxs-lookup"><span data-stu-id="14cd6-152">Create the ***tx_application_define*** function.</span></span> <span data-ttu-id="14cd6-153">É aqui que os recursos iniciais do sistema são criados.</span><span class="sxs-lookup"><span data-stu-id="14cd6-153">This is where the initial system resources are created.</span></span> <span data-ttu-id="14cd6-154">Exemplos de recursos do sistema incluem fios, filas, piscinas de memória, grupos de bandeiras de eventos, mutantes e semáforos.</span><span class="sxs-lookup"><span data-stu-id="14cd6-154">Examples of system resources include threads, queues, memory pools, event flags groups, mutexes, and semaphores.</span></span>

1. <span data-ttu-id="14cd6-155">Compile a fonte de aplicação e ligue-se à biblioteca de tempo de execução ThreadX ***tx.lib***.</span><span class="sxs-lookup"><span data-stu-id="14cd6-155">Compile application source and link with the ThreadX run-time library ***tx.lib***.</span></span> <span data-ttu-id="14cd6-156">A imagem resultante pode ser descarregada para o alvo e executada!</span><span class="sxs-lookup"><span data-stu-id="14cd6-156">The resulting image can be downloaded to the target and executed!</span></span>

## <a name="small-example-system"></a><span data-ttu-id="14cd6-157">Sistema de Pequenos Exemplos</span><span class="sxs-lookup"><span data-stu-id="14cd6-157">Small Example System</span></span>

<span data-ttu-id="14cd6-158">O pequeno sistema de exemplo na Figura 1 mostra a criação de um único fio com uma prioridade de 3.</span><span class="sxs-lookup"><span data-stu-id="14cd6-158">The small example system in Figure 1 shows the creation of a single thread with a priority of 3.</span></span> <span data-ttu-id="14cd6-159">O fio executa, incrementa um contador, em seguida, dorme por um tique-taque do relógio.</span><span class="sxs-lookup"><span data-stu-id="14cd6-159">The thread executes, increments a counter, then sleeps for one clock tick.</span></span>
<span data-ttu-id="14cd6-160">Este processo continua para sempre.</span><span class="sxs-lookup"><span data-stu-id="14cd6-160">This process continues forever.</span></span>

```c
#include "tx_api.h"
unsigned long my_thread_counter = 0;
TX_THREAD my_thread;
main( )
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter( );
}
void tx_application_define(void *first_unused_memory)
{
    /* Create my_thread! */
    tx_thread_create(&my_thread, "My Thread",
    my_thread_entry, 0x1234, first_unused_memory, 1024,
    3, 3, TX_NO_TIME_SLICE, TX_AUTO_START);
}
void my_thread_entry(ULONG thread_input)
{
    /* Enter into a forever loop. */
    while(1)
    {
        /* Increment thread counter. */
        my_thread_counter++;
        /* Sleep for 1 tick. */
        tx_thread_sleep(1);
    }
}
```

<span data-ttu-id="14cd6-161">**FIGURA 1. Modelo para desenvolvimento de aplicações**</span><span class="sxs-lookup"><span data-stu-id="14cd6-161">**FIGURE 1. Template for Application Development**</span></span>

<span data-ttu-id="14cd6-162">Embora este seja um exemplo simples, fornece um bom modelo para o desenvolvimento real de aplicações.</span><span class="sxs-lookup"><span data-stu-id="14cd6-162">Although this is a simple example, it provides a good template for real application development.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="14cd6-163">Resolução de problemas</span><span class="sxs-lookup"><span data-stu-id="14cd6-163">Troubleshooting</span></span>

<span data-ttu-id="14cd6-164">Cada porta ThreadX é entregue com uma aplicação de demonstração.</span><span class="sxs-lookup"><span data-stu-id="14cd6-164">Each ThreadX port is delivered with a demonstration application.</span></span> <span data-ttu-id="14cd6-165">É sempre uma boa ideia pôr o sistema de demonstração a funcionar primeiro - seja em hardware de alvo real ou em ambiente simulado.</span><span class="sxs-lookup"><span data-stu-id="14cd6-165">It is always a good idea to first get the demonstration system running—either on actual target hardware or simulated environment.</span></span>

<span data-ttu-id="14cd6-166">Se o sistema de demonstração não funcionar corretamente, as seguintes são algumas dicas de resolução de problemas.</span><span class="sxs-lookup"><span data-stu-id="14cd6-166">If the demonstration system does not execute properly, the following are some troubleshooting tips.</span></span>

1. <span data-ttu-id="14cd6-167">Determina quanto da demonstração está a decorrer.</span><span class="sxs-lookup"><span data-stu-id="14cd6-167">Determine how much of the demonstration is running.</span></span>
1. <span data-ttu-id="14cd6-168">Aumente os tamanhos das pilhas (isto é mais importante no código de aplicação real do que na demonstração).</span><span class="sxs-lookup"><span data-stu-id="14cd6-168">Increase stack sizes (this is more important in actual application code than it is for the demonstration).</span></span>
1. <span data-ttu-id="14cd6-169">Reconstruir a biblioteca ThreadX com TX_ENABLE_STACK_CHECKING definida.</span><span class="sxs-lookup"><span data-stu-id="14cd6-169">Rebuild the ThreadX library with TX_ENABLE_STACK_CHECKING defined.</span></span> <span data-ttu-id="14cd6-170">Isto permite a verificação da pilha threadx incorporada.</span><span class="sxs-lookup"><span data-stu-id="14cd6-170">This enables the built-in ThreadX stack checking.</span></span>
1. <span data-ttu-id="14cd6-171">Contornar temporariamente quaisquer alterações recentes para ver se o problema desaparece ou muda.</span><span class="sxs-lookup"><span data-stu-id="14cd6-171">Temporarily bypass any recent changes to see if the problem disappears or changes.</span></span> <span data-ttu-id="14cd6-172">Estas informações devem ser úteis para apoiar os engenheiros.</span><span class="sxs-lookup"><span data-stu-id="14cd6-172">Such information should prove useful to support engineers.</span></span>

<span data-ttu-id="14cd6-173">Siga os procedimentos descritos no "[Centro de Apoio](about-this-guide.md#customer-support-center)ao Cliente " para enviar as informações recolhidas a partir das etapas de resolução de problemas.</span><span class="sxs-lookup"><span data-stu-id="14cd6-173">Follow the procedures outlined in "[Customer Support Center](about-this-guide.md#customer-support-center)" to send the information gathered from the troubleshooting steps.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="14cd6-174">Opções de configuração</span><span class="sxs-lookup"><span data-stu-id="14cd6-174">Configuration Options</span></span>

<span data-ttu-id="14cd6-175">Existem várias opções de configuração ao construir a biblioteca ThreadX e a aplicação utilizando o ThreadX.</span><span class="sxs-lookup"><span data-stu-id="14cd6-175">There are several configuration options when building the ThreadX library and the application using ThreadX.</span></span> <span data-ttu-id="14cd6-176">As opções abaixo podem ser definidas na fonte de aplicação, na linha de comando ou dentro do ***ficheiro tx_user.h.***</span><span class="sxs-lookup"><span data-stu-id="14cd6-176">The options below can be defined in the application source, on the command line, or within the ***tx_user.h*** include file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="14cd6-177">*As opções definidas em ***tx_user.h** _ só são aplicadas se a aplicação e a biblioteca ThreadX forem construídas com _ *TX_INCLUDE_USER_DEFINE_FILE** definidas.*</span><span class="sxs-lookup"><span data-stu-id="14cd6-177">*Options defined in ***tx_user.h** _ are applied only if the application and ThreadX library are built with _ *TX_INCLUDE_USER_DEFINE_FILE** defined.*</span></span>

### <a name="smallest-configuration"></a><span data-ttu-id="14cd6-178">Configuração mais pequena</span><span class="sxs-lookup"><span data-stu-id="14cd6-178">Smallest Configuration</span></span>

<span data-ttu-id="14cd6-179">Para o menor tamanho do código, devem ser consideradas as seguintes opções de configuração ThreadX (na ausência de todas as outras opções).</span><span class="sxs-lookup"><span data-stu-id="14cd6-179">For the smallest code size, the following ThreadX configuration options should be considered (in absence of all other options).</span></span>

```c
TX_DISABLE_ERROR_CHECKING
TX_DISABLE_PREEMPTION_THRESHOLD
TX_DISABLE_NOTIFY_CALLBACKS
TX_DISABLE_REDUNDANT_CLEARING
TX_DISABLE_STACK_FILLING
TX_NOT_INTERRUPTABLE
TX_TIMER_PROCESS_IN_ISR
```

### <a name="fastest-configuration"></a><span data-ttu-id="14cd6-180">Configuração mais rápida</span><span class="sxs-lookup"><span data-stu-id="14cd6-180">Fastest Configuration</span></span>

<span data-ttu-id="14cd6-181">Para a execução mais rápida, as mesmas opções de configuração usadas para a Configuração Mais Pequena anteriormente, mas com estas opções também consideradas.</span><span class="sxs-lookup"><span data-stu-id="14cd6-181">For the fastest execution, the same configuration options used for the Smallest Configuration previously, but with these options also considered.</span></span>

```c
TX_REACTIVATE_INLINE
TX_INLINE_THREAD_RESUME_SUSPEND
```

<span data-ttu-id="14cd6-182">[São descritas opções de configuração detalhadas.](#detailed-configuration-options)</span><span class="sxs-lookup"><span data-stu-id="14cd6-182">[Detailed configuration options](#detailed-configuration-options) are described.</span></span>

### <a name="global-time-source"></a><span data-ttu-id="14cd6-183">Fonte global do tempo</span><span class="sxs-lookup"><span data-stu-id="14cd6-183">Global Time Source</span></span>

<span data-ttu-id="14cd6-184">Para outros produtos RTOS da Microsoft Azure (FileX, NetX, GUIX, USBX, etc.), a ThreadX define o número de carraças temporais ThreadX que representam um segundo.</span><span class="sxs-lookup"><span data-stu-id="14cd6-184">For other Microsoft Azure RTOS products (FileX, NetX, GUIX, USBX, etc.), ThreadX defines the number of ThreadX timer ticks that represents one second.</span></span> <span data-ttu-id="14cd6-185">Outros derivam dos seus requisitos de tempo com base nesta constante.</span><span class="sxs-lookup"><span data-stu-id="14cd6-185">Others derive their time requirements based on this constant.</span></span> <span data-ttu-id="14cd6-186">Por predefinição, o valor é de 100, assumindo uma interrupção periódica de 10ms.</span><span class="sxs-lookup"><span data-stu-id="14cd6-186">By default, the value is 100, assuming a 10ms periodic interrupt.</span></span> <span data-ttu-id="14cd6-187">O utilizador pode sobrepor-se a este valor definindo TX_TIMER_TICKS_PER_SECOND com o valor pretendido em ***tx_port.h*** ou dentro do IDE ou linha de comando.</span><span class="sxs-lookup"><span data-stu-id="14cd6-187">The user may override this value by defining TX_TIMER_TICKS_PER_SECOND with the desired value in ***tx_port.h*** or within the IDE or command line.</span></span>

### <a name="detailed-configuration-options"></a><span data-ttu-id="14cd6-188">Opções de configuração detalhadas</span><span class="sxs-lookup"><span data-stu-id="14cd6-188">Detailed Configuration Options</span></span>

<span data-ttu-id="14cd6-189">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="14cd6-189">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="14cd6-190">Quando definida, esta opção permite a recolha de informações de desempenho em piscinas byte.</span><span class="sxs-lookup"><span data-stu-id="14cd6-190">When defined, this option enables the gathering of performance information on byte pools.</span></span> <span data-ttu-id="14cd6-191">Por padrão, esta opção não está definida.</span><span class="sxs-lookup"><span data-stu-id="14cd6-191">By default, this option is not defined.</span></span>

<span data-ttu-id="14cd6-192">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="14cd6-192">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="14cd6-193">Quando definida, esta opção permite a recolha de informações de desempenho em piscinas byte.</span><span class="sxs-lookup"><span data-stu-id="14cd6-193">When defined, this option enables the gathering of performance information on byte pools.</span></span> <span data-ttu-id="14cd6-194">Por padrão, esta opção não está definida.</span><span class="sxs-lookup"><span data-stu-id="14cd6-194">By default, this option is not defined.</span></span>

<span data-ttu-id="14cd6-195">**TX_DISABLE_ERROR_CHECKING**</span><span class="sxs-lookup"><span data-stu-id="14cd6-195">**TX_DISABLE_ERROR_CHECKING**</span></span>

<span data-ttu-id="14cd6-196">Contorna a verificação básica de erros de chamada de serviço.</span><span class="sxs-lookup"><span data-stu-id="14cd6-196">Bypasses basic service call error checking.</span></span> <span data-ttu-id="14cd6-197">Quando definido na fonte de aplicação, toda a verificação básica de erros de parâmetros é desativada.</span><span class="sxs-lookup"><span data-stu-id="14cd6-197">When defined in the application source, all basic parameter error checking is disabled.</span></span> <span data-ttu-id="14cd6-198">Isto pode melhorar o desempenho em até 30% e também reduzir o tamanho da imagem.</span><span class="sxs-lookup"><span data-stu-id="14cd6-198">This may improve performance by as much as 30% and may also reduce the image size.</span></span>

> [!NOTE]
> <span data-ttu-id="14cd6-199">*Só é seguro desativar a verificação de erros se a aplicação pode garantir absolutamente que todos os parâmetros de entrada são sempre válidos em todas as circunstâncias, incluindo parâmetros de entrada derivados da entrada externa. Se a entrada inválida for fornecida à API com verificação de erros desativada, o comportamento resultante é indefinido e pode resultar em corrupção de memória ou falha no sistema.*</span><span class="sxs-lookup"><span data-stu-id="14cd6-199">*It is only safe to disable error checking if the application can absolutely guarantee all input parameters are always valid under all circumstances, including input parameters derived from external input. If invalid input is supplied to the API with error checking disabled, the resulting behavior is undefined and could result in memory corruption or system crash.*</span></span>

> [!NOTE]
> <span data-ttu-id="14cd6-200">*Os valores de devolução da API threadX não afetados pela verificação de erros incapacitantes estão listados em negrito na secção "Valores de Retorno" de cada descrição da API no Capítulo 4. Os valores de devolução não-boles são nulos se a verificação de erros for desativada utilizando a opção TX_DISABLE_ERROR_CHECKING.*</span><span class="sxs-lookup"><span data-stu-id="14cd6-200">*ThreadX API return values not affected by disabling error checking are listed in bold in the “Return Values” section of each API description in Chapter 4. The nonbold return values are void if error checking is disabled by using the TX_DISABLE_ERROR_CHECKING option.*</span></span>

<span data-ttu-id="14cd6-201">**TX_DISABLE_NOTIFY_CALLBACKS**</span><span class="sxs-lookup"><span data-stu-id="14cd6-201">**TX_DISABLE_NOTIFY_CALLBACKS**</span></span>

<span data-ttu-id="14cd6-202">Quando definido, desativa as chamadas de notificação de vários objetos ThreadX.</span><span class="sxs-lookup"><span data-stu-id="14cd6-202">When defined, disables the notify callbacks for various ThreadX objects.</span></span> <span data-ttu-id="14cd6-203">A utilização desta opção reduz ligeiramente o tamanho do código e melhora o desempenho.</span><span class="sxs-lookup"><span data-stu-id="14cd6-203">Using this option slightly reduces code size and improves performance.</span></span> <span data-ttu-id="14cd6-204">Por padrão, esta opção não está definida.</span><span class="sxs-lookup"><span data-stu-id="14cd6-204">By default, this option is not defined.</span></span>

<span data-ttu-id="14cd6-205">**TX_DISABLE_PREEMPTION_THRESHOLD**</span><span class="sxs-lookup"><span data-stu-id="14cd6-205">**TX_DISABLE_PREEMPTION_THRESHOLD**</span></span>

<span data-ttu-id="14cd6-206">Quando definido, desativa a função limiar de pré-edição e reduz ligeiramente o tamanho do código e melhora o desempenho.</span><span class="sxs-lookup"><span data-stu-id="14cd6-206">When defined, disables the preemption-threshold feature and slightly reduces code size and improves performance.</span></span> <span data-ttu-id="14cd6-207">É claro que as capacidades de limiar de pré-edição já não estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="14cd6-207">Of course, the preemption-threshold capabilities are no longer available.</span></span> <span data-ttu-id="14cd6-208">Por padrão, esta opção não está definida.</span><span class="sxs-lookup"><span data-stu-id="14cd6-208">By default, this option is not defined.</span></span>

<span data-ttu-id="14cd6-209">**TX_DISABLE_REDUNDANT_CLEARING**</span><span class="sxs-lookup"><span data-stu-id="14cd6-209">**TX_DISABLE_REDUNDANT_CLEARING**</span></span>

<span data-ttu-id="14cd6-210">Quando definido, remove a lógica para inicializar as estruturas globais de dados da ThreadX para zero.</span><span class="sxs-lookup"><span data-stu-id="14cd6-210">When defined, removes the logic for initializing ThreadX global C data structures to zero.</span></span> <span data-ttu-id="14cd6-211">Isto só deve ser utilizado se o código de inicialização do compilador definir todos os dados globais C não inicializados para zero.</span><span class="sxs-lookup"><span data-stu-id="14cd6-211">This should only be used if the compiler's initialization code sets all un-initialized C global data to zero.</span></span> <span data-ttu-id="14cd6-212">A utilização desta opção reduz ligeiramente o tamanho do código e melhora o desempenho durante a inicialização.</span><span class="sxs-lookup"><span data-stu-id="14cd6-212">Using this option slightly reduces code size and improves performance during initialization.</span></span> <span data-ttu-id="14cd6-213">Por padrão, esta opção não está definida.</span><span class="sxs-lookup"><span data-stu-id="14cd6-213">By default, this option is not defined.</span></span>

<span data-ttu-id="14cd6-214">**TX_DISABLE_STACK_FILLING**</span><span class="sxs-lookup"><span data-stu-id="14cd6-214">**TX_DISABLE_STACK_FILLING**</span></span>

<span data-ttu-id="14cd6-215">Quando definido, desativa a colocação do valor 0xEF em cada byte da pilha de cada fio quando criado.</span><span class="sxs-lookup"><span data-stu-id="14cd6-215">When defined, disables placing the 0xEF value in each byte of each thread's stack when created.</span></span> <span data-ttu-id="14cd6-216">Por padrão, esta opção não está definida.</span><span class="sxs-lookup"><span data-stu-id="14cd6-216">By default, this option is not defined.</span></span>

<span data-ttu-id="14cd6-217">**TX_ENABLE_EVENT_TRACE**</span><span class="sxs-lookup"><span data-stu-id="14cd6-217">**TX_ENABLE_EVENT_TRACE**</span></span>

<span data-ttu-id="14cd6-218">Quando definido, o ThreadX permite o código de recolha do evento para a criação de um tampão de traço TraceX.</span><span class="sxs-lookup"><span data-stu-id="14cd6-218">When defined, ThreadX enables the event gathering code for creating a TraceX trace buffer.</span></span>

<span data-ttu-id="14cd6-219">**TX_ENABLE_STACK_CHECKING**</span><span class="sxs-lookup"><span data-stu-id="14cd6-219">**TX_ENABLE_STACK_CHECKING**</span></span>

<span data-ttu-id="14cd6-220">Quando definido, permite a verificação da pilha de tempo de execução ThreadX, que inclui a análise da quantidade de pilhas utilizadas e o exame de "cercas" de padrão de dados antes e depois da área da pilha.</span><span class="sxs-lookup"><span data-stu-id="14cd6-220">When defined, enables ThreadX run-time stack checking, which includes analysis of how much stack has been used and examination of data pattern "fences" before and after the stack area.</span></span> <span data-ttu-id="14cd6-221">Se for detetado um erro de pilha, o manipulador de erros da pilha de aplicação registado é chamado.</span><span class="sxs-lookup"><span data-stu-id="14cd6-221">If a stack error is detected, the registered application stack error handler is called.</span></span> <span data-ttu-id="14cd6-222">Esta opção resulta num ligeiro aumento da sobrecarga e do tamanho do código.</span><span class="sxs-lookup"><span data-stu-id="14cd6-222">This option does result in slightly increased overhead and code size.</span></span> <span data-ttu-id="14cd6-223">Reveja a função API ***tx_thread_stack_error_notify*** para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="14cd6-223">Review the ***tx_thread_stack_error_notify*** API function for more information.</span></span> <span data-ttu-id="14cd6-224">Por padrão, esta opção não está definida.</span><span class="sxs-lookup"><span data-stu-id="14cd6-224">By default, this option is not defined.</span></span>

<span data-ttu-id="14cd6-225">**TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="14cd6-225">**TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="14cd6-226">Quando definido, permite a recolha de informações de desempenho em grupos de bandeiras de eventos.</span><span class="sxs-lookup"><span data-stu-id="14cd6-226">When defined, enables the gathering of performance information on event flags groups.</span></span> <span data-ttu-id="14cd6-227">Por padrão, esta opção não está definida.</span><span class="sxs-lookup"><span data-stu-id="14cd6-227">By default, this option is not defined.</span></span>

<span data-ttu-id="14cd6-228">**TX_INLINE_THREAD_RESUME_SUSPEND**</span><span class="sxs-lookup"><span data-stu-id="14cd6-228">**TX_INLINE_THREAD_RESUME_SUSPEND**</span></span>

<span data-ttu-id="14cd6-229">Quando definido, o ThreadX melhora as chamadas ***tx_thread_resume** _ e _ *_tx_thread_suspend_** aPI através de código em linha.</span><span class="sxs-lookup"><span data-stu-id="14cd6-229">When defined, ThreadX improves the ***tx_thread_resume** _ and _ *_tx_thread_suspend_** API calls via in-line code.</span></span> <span data-ttu-id="14cd6-230">Isto aumenta o tamanho do código, mas melhora o desempenho destas duas chamadas API.</span><span class="sxs-lookup"><span data-stu-id="14cd6-230">This increases code size but enhances performance of these two API calls.</span></span>

<span data-ttu-id="14cd6-231">**TX_MAX_PRIORITIES**</span><span class="sxs-lookup"><span data-stu-id="14cd6-231">**TX_MAX_PRIORITIES**</span></span>

<span data-ttu-id="14cd6-232">Define os níveis de prioridade para a ThreadX.</span><span class="sxs-lookup"><span data-stu-id="14cd6-232">Defines the priority levels for ThreadX.</span></span> <span data-ttu-id="14cd6-233">Os valores legais variam entre 32 e 1024 (inclusive) e *devem* ser igualmente divisíveis até 32.</span><span class="sxs-lookup"><span data-stu-id="14cd6-233">Legal values range from 32 through 1024 (inclusive) and *must* be evenly divisible by 32.</span></span> <span data-ttu-id="14cd6-234">O aumento do número de níveis prioritários apoiados aumenta o uso da RAM em 128 bytes para cada grupo de 32 prioridades.</span><span class="sxs-lookup"><span data-stu-id="14cd6-234">Increasing the number of priority levels supported increases the RAM usage by 128 bytes for every group of 32 priorities.</span></span> <span data-ttu-id="14cd6-235">No entanto, existe apenas um efeito negligenciável no desempenho.</span><span class="sxs-lookup"><span data-stu-id="14cd6-235">However, there is only a negligible effect on performance.</span></span> <span data-ttu-id="14cd6-236">Por padrão, este valor é definido para 32 níveis prioritários.</span><span class="sxs-lookup"><span data-stu-id="14cd6-236">By default, this value is set to 32 priority levels.</span></span>

<span data-ttu-id="14cd6-237">**TX_MINIMUM_STACK**</span><span class="sxs-lookup"><span data-stu-id="14cd6-237">**TX_MINIMUM_STACK**</span></span>

<span data-ttu-id="14cd6-238">Define o tamanho mínimo da pilha (em bytes).</span><span class="sxs-lookup"><span data-stu-id="14cd6-238">Defines the minimum stack size (in bytes).</span></span> <span data-ttu-id="14cd6-239">É utilizado para verificação de erros quando os fios são criados.</span><span class="sxs-lookup"><span data-stu-id="14cd6-239">It is used for error checking when threads are created.</span></span> <span data-ttu-id="14cd6-240">O valor predefinido é específico da porta e encontra-se em ***tx_port.h***.</span><span class="sxs-lookup"><span data-stu-id="14cd6-240">The default value is port-specific and is found in ***tx_port.h***.</span></span>

<span data-ttu-id="14cd6-241">**TX_MISRA_ENABLE**</span><span class="sxs-lookup"><span data-stu-id="14cd6-241">**TX_MISRA_ENABLE**</span></span>

<span data-ttu-id="14cd6-242">Quando definido, a ThreadX utiliza convenções compatíveis com o MISRA C.</span><span class="sxs-lookup"><span data-stu-id="14cd6-242">When defined, ThreadX utilizes MISRA C compliant conventions.</span></span> <span data-ttu-id="14cd6-243">Consulte  ***ThreadX_MISRA_Compliance.pdf*** para mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="14cd6-243">Refer to  ***ThreadX_MISRA_Compliance.pdf*** for details.</span></span>

<span data-ttu-id="14cd6-244">**TX_MUTEX_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="14cd6-244">**TX_MUTEX_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="14cd6-245">Quando definido, permite a recolha de informações de desempenho sobre mutações.</span><span class="sxs-lookup"><span data-stu-id="14cd6-245">When defined, enables the gathering of performance information on mutexes.</span></span> <span data-ttu-id="14cd6-246">Por padrão, esta opção não está definida.</span><span class="sxs-lookup"><span data-stu-id="14cd6-246">By default, this option is not defined.</span></span>

<span data-ttu-id="14cd6-247">**TX_NO_TIMER**</span><span class="sxs-lookup"><span data-stu-id="14cd6-247">**TX_NO_TIMER**</span></span>

<span data-ttu-id="14cd6-248">Quando definido, a lógica do temporizador ThreadX é completamente desativada.</span><span class="sxs-lookup"><span data-stu-id="14cd6-248">When defined, the ThreadX timer logic is completely disabled.</span></span> <span data-ttu-id="14cd6-249">Isto é útil nos casos em que as funcionalidades do temporizador ThreadX (tempo de rosca, intervalos de tempo da API, corte de tempo e temporizadores de aplicação) não são utilizadas.</span><span class="sxs-lookup"><span data-stu-id="14cd6-249">This is useful in cases where the ThreadX timer features (thread sleep, API timeouts, time-slicing, and application timers) are not utilized.</span></span> <span data-ttu-id="14cd6-250">Se **TX_NO_TIMER** for especificado, a opção **TX_TIMER_PROCESS_IN_ISR** também deve ser definida.</span><span class="sxs-lookup"><span data-stu-id="14cd6-250">If **TX_NO_TIMER** is specified, the option **TX_TIMER_PROCESS_IN_ISR** must also be defined.</span></span>

<span data-ttu-id="14cd6-251">**TX_NOT_INTERRUPTABLE**</span><span class="sxs-lookup"><span data-stu-id="14cd6-251">**TX_NOT_INTERRUPTABLE**</span></span>

<span data-ttu-id="14cd6-252">Quando definido, o ThreadX não tenta minimizar o tempo de bloqueio de interrupção.</span><span class="sxs-lookup"><span data-stu-id="14cd6-252">When defined, ThreadX does not attempt to minimize interrupt lockout time.</span></span> <span data-ttu-id="14cd6-253">Isto resulta numa execução mais rápida, mas aumenta ligeiramente o tempo de bloqueio da interrupção.</span><span class="sxs-lookup"><span data-stu-id="14cd6-253">This results in faster execution but does slightly increase interrupt lockout time.</span></span>

<span data-ttu-id="14cd6-254">**TX_QUEUE_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="14cd6-254">**TX_QUEUE_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="14cd6-255">Quando definido, permite a recolha de informações de desempenho nas filas.</span><span class="sxs-lookup"><span data-stu-id="14cd6-255">When defined, enables the gathering of performance information on queues.</span></span> <span data-ttu-id="14cd6-256">Por padrão, esta opção não está definida.</span><span class="sxs-lookup"><span data-stu-id="14cd6-256">By default, this option is not defined.</span></span>

<span data-ttu-id="14cd6-257">**TX_REACTIVATE_INLINE**</span><span class="sxs-lookup"><span data-stu-id="14cd6-257">**TX_REACTIVATE_INLINE**</span></span>

<span data-ttu-id="14cd6-258">Quando definido, executa a reativação dos temporizadores ThreadX em linha em vez de utilizar uma chamada de função.</span><span class="sxs-lookup"><span data-stu-id="14cd6-258">When defined, performs reactivation of ThreadX timers inline instead of using a function call.</span></span> <span data-ttu-id="14cd6-259">Isto melhora o desempenho, mas aumenta ligeiramente o tamanho do código.</span><span class="sxs-lookup"><span data-stu-id="14cd6-259">This improves performance but slightly increases code size.</span></span> <span data-ttu-id="14cd6-260">Por padrão, esta opção não está definida.</span><span class="sxs-lookup"><span data-stu-id="14cd6-260">By default, this option is not defined.</span></span>

<span data-ttu-id="14cd6-261">**TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="14cd6-261">**TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="14cd6-262">Quando definido, permite a recolha de informações de desempenho sobre semáforos.</span><span class="sxs-lookup"><span data-stu-id="14cd6-262">When defined, enables the gathering of performance information on semaphores.</span></span> <span data-ttu-id="14cd6-263">Por padrão, esta opção não está definida.</span><span class="sxs-lookup"><span data-stu-id="14cd6-263">By default, this option is not defined.</span></span>

<span data-ttu-id="14cd6-264">**TX_THREAD_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="14cd6-264">**TX_THREAD_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="14cd6-265">Quando definido, permite a recolha de informações de desempenho sobre fios.</span><span class="sxs-lookup"><span data-stu-id="14cd6-265">When defined, enables the gathering of performance information on threads.</span></span> <span data-ttu-id="14cd6-266">Por padrão, esta opção não está definida.</span><span class="sxs-lookup"><span data-stu-id="14cd6-266">By default, this option is not defined.</span></span>

<span data-ttu-id="14cd6-267">**TX_TIMER_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="14cd6-267">**TX_TIMER_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="14cd6-268">Quando definido, permite a recolha de informações de desempenho nos temporizadores.</span><span class="sxs-lookup"><span data-stu-id="14cd6-268">When defined, enables the gathering of performance information on timers.</span></span> <span data-ttu-id="14cd6-269">Por padrão, esta opção não está definida.</span><span class="sxs-lookup"><span data-stu-id="14cd6-269">By default, this option is not defined.</span></span>

<span data-ttu-id="14cd6-270">**TX_TIMER_PROCESS_IN_ISR**</span><span class="sxs-lookup"><span data-stu-id="14cd6-270">**TX_TIMER_PROCESS_IN_ISR**</span></span>

<span data-ttu-id="14cd6-271">Quando definido, elimina o fio do temporizador interno do sistema para o ThreadX.</span><span class="sxs-lookup"><span data-stu-id="14cd6-271">When defined, eliminates the internal system timer thread for ThreadX.</span></span> <span data-ttu-id="14cd6-272">Isto resulta numa melhoria do desempenho em eventos temporizadores e requisitos de RAM mais pequenos porque a pilha de temporizador e o bloco de controlo já não são necessários.</span><span class="sxs-lookup"><span data-stu-id="14cd6-272">This results in improved performance on timer events and smaller RAM requirements because the timer stack and control block are no longer needed.</span></span> <span data-ttu-id="14cd6-273">No entanto, a utilização desta opção move todo o processamento de expiração do temporizador para o nível ISR do temporizador.</span><span class="sxs-lookup"><span data-stu-id="14cd6-273">However, using this option moves all the timer expiration processing to the timer ISR level.</span></span> <span data-ttu-id="14cd6-274">Por padrão, esta opção não está definida.</span><span class="sxs-lookup"><span data-stu-id="14cd6-274">By default, this option is not defined.</span></span>

> [!NOTE]
> <span data-ttu-id="14cd6-275">*Os serviços autorizados a partir de temporizadores não podem ser permitidos a partir de ISRs, pelo que não podem ser permitidos na utilização desta opção.*</span><span class="sxs-lookup"><span data-stu-id="14cd6-275">*Services allowed from timers may not be allowed from ISRs and thus might not be allowed when using this option.*</span></span>

<span data-ttu-id="14cd6-276">**TX_TIMER_THREAD_PRIORITY**</span><span class="sxs-lookup"><span data-stu-id="14cd6-276">**TX_TIMER_THREAD_PRIORITY**</span></span>

<span data-ttu-id="14cd6-277">Define a prioridade do fio temporizador interno do sistema ThreadX.</span><span class="sxs-lookup"><span data-stu-id="14cd6-277">Defines the priority of the internal ThreadX system timer thread.</span></span> <span data-ttu-id="14cd6-278">O valor predefinido é prioridade 0 — a maior prioridade na ThreadX.</span><span class="sxs-lookup"><span data-stu-id="14cd6-278">The default value is priority 0—the highest priority in ThreadX.</span></span> <span data-ttu-id="14cd6-279">O valor predefinido é definido em ***tx_port.h***.</span><span class="sxs-lookup"><span data-stu-id="14cd6-279">The default value is defined in ***tx_port.h***.</span></span>

<span data-ttu-id="14cd6-280">**TX_TIMER_THREAD_STACK_SIZE**</span><span class="sxs-lookup"><span data-stu-id="14cd6-280">**TX_TIMER_THREAD_STACK_SIZE**</span></span>

<span data-ttu-id="14cd6-281">Define o tamanho da pilha (em bytes) do fio temporizador interno do sistema ThreadX.</span><span class="sxs-lookup"><span data-stu-id="14cd6-281">Defines the stack size (in bytes) of the internal ThreadX system timer thread.</span></span> <span data-ttu-id="14cd6-282">Este fio processa todos os pedidos de sono de linha, bem como todos os intervalos de chamada de serviço.</span><span class="sxs-lookup"><span data-stu-id="14cd6-282">This thread processes all thread sleep requests as well as all service call timeouts.</span></span> <span data-ttu-id="14cd6-283">Além disso, todas as rotinas de chamada do temporizador de aplicação são invocadas a partir deste contexto.</span><span class="sxs-lookup"><span data-stu-id="14cd6-283">In addition, all application timer callback routines are invoked from this context.</span></span> <span data-ttu-id="14cd6-284">O valor predefinido é específico da porta e encontra-se em ***tx_port.h***.</span><span class="sxs-lookup"><span data-stu-id="14cd6-284">The default value is port-specific and is found in ***tx_port.h***.</span></span>

## <a name="threadx-version-id"></a><span data-ttu-id="14cd6-285">ID da versão ThreadX</span><span class="sxs-lookup"><span data-stu-id="14cd6-285">ThreadX Version ID</span></span>

<span data-ttu-id="14cd6-286">O programador pode obter a versão ThreadX a partir do exame do ficheiro \***tx_port.h_**</span><span class="sxs-lookup"><span data-stu-id="14cd6-286">The programmer can obtain the ThreadX version from examination of the \***tx_port.h** _ file.</span></span> <span data-ttu-id="14cd6-287">Além disso, este ficheiro também contém um histórico de versão da porta correspondente.</span><span class="sxs-lookup"><span data-stu-id="14cd6-287">In addition, this file also contains a version history of the corresponding port.</span></span> <span data-ttu-id="14cd6-288">O software de aplicação pode obter a versão ThreadX examinando a cadeia global _\*_tx_version_id\*\*.</span><span class="sxs-lookup"><span data-stu-id="14cd6-288">Application software can obtain the ThreadX version by examining the global string _\*_tx_version_id\*\*.</span></span>
