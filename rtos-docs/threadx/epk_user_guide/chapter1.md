---
title: Capítulo 1 - Kit de Introdução ao Perfil de Execução
description: Este capítulo contém uma introdução ao Azure RTOS ThreadX Execution Profile Kit (EPK).
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7d30676437535229ad5bdbca10dcc9ca009d6e74
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377655"
---
# <a name="chapter-1--introduction-to-the-execution-profile-kit"></a><span data-ttu-id="9bd69-103">Capítulo 1 Introdução ao Kit de Perfil de Execução</span><span class="sxs-lookup"><span data-stu-id="9bd69-103">Chapter 1  Introduction to the Execution Profile Kit</span></span>

<span data-ttu-id="9bd69-104">O Kit de Perfil de Execução ThreadX (EPK) fornece uma infraestrutura para aplicações para acompanhar dinamicamente o tempo de execução dos fios, as rotinas de serviço de interrupção (ISRs) e as condições do sistema inativos.</span><span class="sxs-lookup"><span data-stu-id="9bd69-104">The ThreadX Execution Profile Kit (EPK) provides an infrastructure for applications to dynamically track execution time for threads, Interrupt Service Routines (ISRs), and idle system conditions.</span></span> <span data-ttu-id="9bd69-105">Isto é especialmente útil para otimizar e sintonizar a aplicação para o máximo desempenho.</span><span class="sxs-lookup"><span data-stu-id="9bd69-105">This is especially useful for optimization and tuning the application for maximum performance.</span></span> <span data-ttu-id="9bd69-106">No entanto, trata-se também de uma valiosa ajuda ao depurg.</span><span class="sxs-lookup"><span data-stu-id="9bd69-106">However, it is also a valuable debug aid.</span></span>

<span data-ttu-id="9bd69-107">O EPK baseia-se em \" ganchos \" incorporados na lógica de agendamento ThreadX no código de montagem que são chamados na entrada de thread, saída de fio, entrada ISR e saída ISR.</span><span class="sxs-lookup"><span data-stu-id="9bd69-107">The EPK relies on \"hooks\" built into the ThreadX scheduling logic in assembly code that are called on thread entry, thread exit, ISR entry, and ISR exit.</span></span> <span data-ttu-id="9bd69-108">As rotinas EPK calculam o tempo entre tais eventos e armazenam o tempo delta em variáveis globais, bem como membros do bloco de controlo **TX_THREAD.**</span><span class="sxs-lookup"><span data-stu-id="9bd69-108">The EPK routines calculate the time in between such events and store the delta time in global variables as well as members of the **TX_THREAD** control block.</span></span>

> [!NOTE]
> <span data-ttu-id="9bd69-109">*O desenvolvedor é livre de modificar ou mesmo substituir estas funções de gancho pela sua própria lógica para alternar pinos de I/O de modo a fornecer visibilidade de hardware a uma aplicação ThreadX em execução*.</span><span class="sxs-lookup"><span data-stu-id="9bd69-109">*The developer is free to modify or even replace these hook functions with their own logic to toggle I/O pins in order to provide hardware visibility to a running ThreadX application*.</span></span>

## 

## <a name="epk-requirements"></a><span data-ttu-id="9bd69-110">Requisitos da EPK</span><span class="sxs-lookup"><span data-stu-id="9bd69-110">EPK Requirements</span></span>

<span data-ttu-id="9bd69-111">O EPK requer threadX 6.0 (ou superior) para funcionar.</span><span class="sxs-lookup"><span data-stu-id="9bd69-111">The EPK requires ThreadX 6.0 (or above) in order to operate.</span></span> <span data-ttu-id="9bd69-112">O EPK também requer uma \" \" resolução razoável, aumentando a fonte de tempo de hardware.</span><span class="sxs-lookup"><span data-stu-id="9bd69-112">The EPK also requires a \"reasonable\" resolution, incrementing hardware time source.</span></span> <span data-ttu-id="9bd69-113">A resolução mais razoável seria normalmente algo numa escala de microssessesse segundo.</span><span class="sxs-lookup"><span data-stu-id="9bd69-113">The most reasonable resolution would typically be something on a microsecond scale.</span></span> <span data-ttu-id="9bd69-114">Se a resolução for demasiado grande, os contadores EPK irão esgotar-se demasiado rapidamente.</span><span class="sxs-lookup"><span data-stu-id="9bd69-114">If the resolution is too great, the EPK counters will max out too quickly.</span></span> <span data-ttu-id="9bd69-115">Pelo contrário, se a resolução for demasiado pequena, não é possível um calendário exato.</span><span class="sxs-lookup"><span data-stu-id="9bd69-115">Conversely, if the resolution is too small, accurate timing is not possible.</span></span> <span data-ttu-id="9bd69-116">A fonte de tempo de aplicação é definida em ***tx_execution_profile.h** _ pela macro _*TX_EXECUTION_TIME_SOURCE\*\*.</span><span class="sxs-lookup"><span data-stu-id="9bd69-116">The application time source is defined in ***tx_execution_profile.h** _ by the macro _*TX_EXECUTION_TIME_SOURCE\*\*.</span></span>

<span data-ttu-id="9bd69-117">O compilador C deve suportar o tipo \" não assinado por muito tempo para \" contadores totais não assinados de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="9bd69-117">The C compiler must support the type \"unsigned long long\" for unsigned 64-bit total counters.</span></span> <span data-ttu-id="9bd69-118">Além disso, o EPK assume que as variáveis globais são inicializadas pelo código de arranque do compilador de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9bd69-118">Furthermore, the EPK assumes the global variables are initialized by the compiler run-time startup code.</span></span> <span data-ttu-id="9bd69-119">Se não for esse o caso, as variáveis globais definidas em ***tx_execution_profile.c*** devem ser inicializadas para 0 pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="9bd69-119">If this is not the case, the global variables defined in ***tx_execution_profile.c*** must be initialized to 0 by the application.</span></span>

## <a name="epk-installation"></a><span data-ttu-id="9bd69-120">Instalação EPK</span><span class="sxs-lookup"><span data-stu-id="9bd69-120">EPK Installation</span></span>

<span data-ttu-id="9bd69-121">Para instalar o ThreadX EPK, siga os passos abaixo e reconstrua toda a biblioteca e aplicação threadX.</span><span class="sxs-lookup"><span data-stu-id="9bd69-121">To install the ThreadX EPK, follow the steps below and rebuild the entire ThreadX library and application.</span></span>

1. <span data-ttu-id="9bd69-122">Inclua os ficheiros de origem EPK (***tx_execution_profile.h** _ e _*_tx_execution_profile.c)_\*_ no seu projeto de construção da biblioteca ThreadX.</span><span class="sxs-lookup"><span data-stu-id="9bd69-122">Include the EPK source files (***tx_execution_profile.h** _ and _*_tx_execution_profile.c_\*_) in your ThreadX library build project.</span></span> <span data-ttu-id="9bd69-123">Estes ficheiros podem estar na [repo Azure RTOS ThreadX](<https://github.com/azure-rtos/threadx>) sob a pasta _ \*_utilitário/Execution_Profile_\*\*).</span><span class="sxs-lookup"><span data-stu-id="9bd69-123">These files can be in the [Azure RTOS ThreadX repo](<https://github.com/azure-rtos/threadx>) under the _ *_utility/Execution_Profile_*\* folder).</span></span>

1. <span data-ttu-id="9bd69-124">In ***tx_port.h** _, defina a macro _ *TX_THREAD_EXTENSION_3** da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="9bd69-124">In ***tx_port.h** _, define the _ *TX_THREAD_EXTENSION_3** macro as follows.</span></span>
```
    #define TX_THREAD_EXTENSION_3 unsigned long long tx_thread_execution_time_total; \
    unsigned long tx_thread_execution_time_last_start;
```

3. <span data-ttu-id="9bd69-125">Defina o **TX_EXECUTION_TIME_SOURCE** macro em **_tx_execution_profile.h_** para mapear para a sua fonte de tempo de hardware.</span><span class="sxs-lookup"><span data-stu-id="9bd69-125">Define the **TX_EXECUTION_TIME_SOURCE** macro in **_tx_execution_profile.h_** to map to your hardware time source.</span></span>

1. <span data-ttu-id="9bd69-126">Certifique-se de que o ambiente de construção define **TX_ENABLE_EXECUTION_CHANGE_NOTIFY** de modo a que os ganchos de agendamento sejam chamados a partir do código de montagem ThreadX.</span><span class="sxs-lookup"><span data-stu-id="9bd69-126">Ensure that the build environment defines **TX_ENABLE_EXECUTION_CHANGE_NOTIFY** so that the scheduling hooks are called from the ThreadX assembly code.</span></span>

1. <span data-ttu-id="9bd69-127">Se desejar utilizar uma fonte de tempo de 64 bits, por favor reveja o ficheiro ***tx_execution_profile.h*** para obter instruções sobre como o conseguir.</span><span class="sxs-lookup"><span data-stu-id="9bd69-127">If you wish to use 64-bit time source, please review the ***tx_execution_profile.h*** file for instructions on how to accomplish this.</span></span>

1. <span data-ttu-id="9bd69-128">Reconstruir toda a biblioteca e aplicação para que todas estas opções sejam devidamente compiladas.</span><span class="sxs-lookup"><span data-stu-id="9bd69-128">Rebuild the entire library and application so that all of these options are properly compiled-in.</span></span>

<span data-ttu-id="9bd69-129">Está agora pronto a usar o EPK com a sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="9bd69-129">You are now ready to use EPK with your application.</span></span>

##  <a name="epk-example"></a><span data-ttu-id="9bd69-130">Exemplo da EPK</span><span class="sxs-lookup"><span data-stu-id="9bd69-130">EPK Example</span></span> 

<span data-ttu-id="9bd69-131">Segue-se um exemplo de EPK a ser usado numa demonstração padrão da ThreadX, configurada com uma fonte de temporizador de 32 bits que incrementa 7,2 vezes por microsegundo.</span><span class="sxs-lookup"><span data-stu-id="9bd69-131">The following is an example of EPK being used on a standard ThreadX demonstration, configured with a 32-bit timer source that increments 7.2 times per microsecond.</span></span> 

<span data-ttu-id="9bd69-132">A **macro TX_EXECUTION_TIME_SOURCE** é definida para recolher o registo do temporizador mapeado pela memória em 0xE0001004, da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="9bd69-132">The **TX_EXECUTION_TIME_SOURCE** macro is defined to pick up the memory-mapped timer register at 0xE0001004, as follows.</span></span>
```
(EXECUTION_TIME_SOURCE_TYPE) \*((ULONG \*) 0xE0001004)
```

<span data-ttu-id="9bd69-133">Deixar a demonstração funcionar durante cinco segundos dá os seguintes resultados.</span><span class="sxs-lookup"><span data-stu-id="9bd69-133">Letting the demonstration run for five seconds yields the following results.</span></span>

![Resultados de deixar a demonstração correr.](media/demo_results.png)

<span data-ttu-id="9bd69-135">Uma vez que a demonstração padrão da ThreadX não tem tempo de marcha lenta (os fios 1 e 2 funcionam continuamente), o EPK reporta corretamente zero durante o tempo de marcha lenta.</span><span class="sxs-lookup"><span data-stu-id="9bd69-135">Since the standard ThreadX demonstration has no idle time (threads 1 and 2 run continuously), the EPK correctly reports zero for idle time.</span></span> <span data-ttu-id="9bd69-136">Os valores totais de tempo e rosca do ISR podem ser divididos por 7.2, a fim de obter os microsegundos para cada categoria de execução.</span><span class="sxs-lookup"><span data-stu-id="9bd69-136">The ISR total time and thread values may be divided by 7.2 in order to derive the microseconds for each execution category.</span></span> <span data-ttu-id="9bd69-137">O EPK também fornece APIs para aceder a estas informações (consulte por favor [o Capítulo 2](chapter2.md)).</span><span class="sxs-lookup"><span data-stu-id="9bd69-137">The EPK also provides APIs to access this information (please see please see [Chapter 2](chapter2.md)).</span></span>