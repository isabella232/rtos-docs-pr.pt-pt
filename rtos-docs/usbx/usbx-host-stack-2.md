---
title: Capítulo 2 - Instalação de pilha de anfitriões USBX Azure RTOS
description: Saiba como instalar a pilha de anfitriões USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 4c33f95b8ac268c557fd947a1303ec3af315a37e
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377089"
---
# <a name="chapter-2---azure-rtos-usbx-host-stack-installation"></a><span data-ttu-id="b5612-103">Capítulo 2 - Instalação de pilha de anfitriões USBX Azure RTOS</span><span class="sxs-lookup"><span data-stu-id="b5612-103">Chapter 2 - Azure RTOS USBX Host Stack Installation</span></span>

## <a name="host-considerations"></a><span data-ttu-id="b5612-104">Considerações de Anfitrião</span><span class="sxs-lookup"><span data-stu-id="b5612-104">Host Considerations</span></span>

### <a name="computer-type"></a><span data-ttu-id="b5612-105">Tipo de computador</span><span class="sxs-lookup"><span data-stu-id="b5612-105">Computer Type</span></span>

<span data-ttu-id="b5612-106">O desenvolvimento incorporado é geralmente realizado em computadores anfitriões Windows PC ou Unix.</span><span class="sxs-lookup"><span data-stu-id="b5612-106">Embedded development is usually performed on Windows PC or Unix host computers.</span></span> <span data-ttu-id="b5612-107">Após a compilação da aplicação, ligada e localizada no anfitrião, é descarregada para o hardware alvo para execução.</span><span class="sxs-lookup"><span data-stu-id="b5612-107">After the application is compiled, linked, and located on the host, it is downloaded to the target hardware for execution.</span></span>

### <a name="download-interfaces"></a><span data-ttu-id="b5612-108">Baixar Interfaces</span><span class="sxs-lookup"><span data-stu-id="b5612-108">Download Interfaces</span></span>

<span data-ttu-id="b5612-109">Normalmente, o download do alvo é feito através de uma interface de série RS-232, embora interfaces paralelas, USB e Ethernet estejam a tornar-se mais populares.</span><span class="sxs-lookup"><span data-stu-id="b5612-109">Usually, the target download is done over an RS-232 serial interface, although parallel interfaces, USB, and Ethernet are becoming more popular.</span></span> <span data-ttu-id="b5612-110">Consulte a documentação da ferramenta de desenvolvimento para obter as opções disponíveis.</span><span class="sxs-lookup"><span data-stu-id="b5612-110">See the development tool documentation for available options.</span></span>

### <a name="debugging-tools"></a><span data-ttu-id="b5612-111">Ferramentas de depurar</span><span class="sxs-lookup"><span data-stu-id="b5612-111">Debugging Tools</span></span>

<span data-ttu-id="b5612-112">Depurar é feito normalmente sobre o mesmo link que o download de imagem do programa.</span><span class="sxs-lookup"><span data-stu-id="b5612-112">Debugging is done typically over the same link as the program image download.</span></span> <span data-ttu-id="b5612-113">Existe uma variedade de depuradores, desde pequenos programas de monitor que correm no alvo através do Background Debug Monitor (BDM) e In-Circuit ferramentas emuladoras (ICE).</span><span class="sxs-lookup"><span data-stu-id="b5612-113">A variety of debuggers exist, ranging from small monitor programs running on the target through Background Debug Monitor (BDM) and In-Circuit Emulator (ICE) tools.</span></span> <span data-ttu-id="b5612-114">A ferramenta ICE fornece a depuragem mais robusta do hardware alvo real.</span><span class="sxs-lookup"><span data-stu-id="b5612-114">The ICE tool provides the most robust debugging of actual target hardware.</span></span>

### <a name="required-hard-disk-space"></a><span data-ttu-id="b5612-115">Espaço de disco rígido necessário</span><span class="sxs-lookup"><span data-stu-id="b5612-115">Required Hard Disk Space</span></span>

<span data-ttu-id="b5612-116">O código-fonte do USBX é entregue em formato ASCII e requer aproximadamente 500 KBytes de espaço no disco rígido do computador anfitrião.</span><span class="sxs-lookup"><span data-stu-id="b5612-116">The source code for USBX is delivered in ASCII format and requires approximately 500 KBytes of space on the host computer's hard disk.</span></span>

## <a name="target-considerations"></a><span data-ttu-id="b5612-117">Considerações-alvo</span><span class="sxs-lookup"><span data-stu-id="b5612-117">Target Considerations</span></span>

<span data-ttu-id="b5612-118">USBX requer entre 24 KBytes e 64 KBytes de Read Only Memory (ROM) no alvo no modo anfitrião.</span><span class="sxs-lookup"><span data-stu-id="b5612-118">USBX requires between 24 KBytes and 64 KBytes of Read Only Memory (ROM) on the target in host mode.</span></span> <span data-ttu-id="b5612-119">A quantidade de memória necessária depende do tipo de controlador utilizado e das classes USB ligadas ao USBX.</span><span class="sxs-lookup"><span data-stu-id="b5612-119">The amount of memory required is dependent on the type of controller used and the USB classes linked to USBX.</span></span> <span data-ttu-id="b5612-120">Outros 32 KBytes da Memória de Acesso Aleatório (RAM) do alvo são necessários para estruturas de dados globais USBX e piscina de memória.</span><span class="sxs-lookup"><span data-stu-id="b5612-120">Another 32 KBytes of the target's Random Access Memory (RAM) are required for USBX global data structures and memory pool.</span></span> <span data-ttu-id="b5612-121">Este conjunto de memórias também pode ser ajustado dependendo do número esperado de dispositivos no USB e do tipo de controlador USB.</span><span class="sxs-lookup"><span data-stu-id="b5612-121">This memory pool can also be adjusted depending on the expected number of devices on the USB and the type of USB controller.</span></span> <span data-ttu-id="b5612-122">O lado do dispositivo USBX requer aproximadamente 10-12 K de ROM dependendo do tipo de controlador do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b5612-122">The USBX device side requires roughly 10-12 K of ROM depending on the type of device controller.</span></span> <span data-ttu-id="b5612-123">O uso da memória RAM depende do tipo de classe emulsionada pelo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b5612-123">The RAM memory usage depends on the type of class emulated by the device.</span></span>

<span data-ttu-id="b5612-124">A USBX também conta com semáforos ThreadX, mutexes e fios para proteção de múltiplos fios, e suspensão de I/O e processamento periódico para monitorizar a topologia do autocarro USB.</span><span class="sxs-lookup"><span data-stu-id="b5612-124">USBX also relies on ThreadX semaphores, mutexes, and threads for multiple thread protection, and I/O suspension and periodic processing for monitoring the USB bus topology.</span></span>

### <a name="product-distribution"></a><span data-ttu-id="b5612-125">Distribuição de Produtos</span><span class="sxs-lookup"><span data-stu-id="b5612-125">Product Distribution</span></span>

<span data-ttu-id="b5612-126">O Azure RTOS USBX pode ser obtido a partir do nosso repositório de código de fonte pública em <https://github.com/azure-rtos/usbx/> .</span><span class="sxs-lookup"><span data-stu-id="b5612-126">Azure RTOS USBX can be obtained from our public source code repository at <https://github.com/azure-rtos/usbx/>.</span></span>

<span data-ttu-id="b5612-127">Segue-se uma lista de vários ficheiros importantes no repositório:</span><span class="sxs-lookup"><span data-stu-id="b5612-127">The following is a list of several important files in the repository:</span></span>

- <span data-ttu-id="b5612-128">***ux_api.h:*** Este ficheiro de cabeçalho C contém todos os equacionares do sistema, estruturas de dados e protótipos de serviço.</span><span class="sxs-lookup"><span data-stu-id="b5612-128">***ux_api.h***: This C header file contains all system equates, data structures, and service prototypes.</span></span>
- <span data-ttu-id="b5612-129">***ux_port.h:*** Este ficheiro de cabeçalho C contém todas as definições e estruturas específicas da ferramenta de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="b5612-129">***ux_port.h***: This C header file contains all development-tool-specific data definitions and structures.</span></span>
- <span data-ttu-id="b5612-130">***ux.lib***: Esta é a versão binária da biblioteca USBX C.</span><span class="sxs-lookup"><span data-stu-id="b5612-130">***ux.lib***: This is the binary version of the USBX C library.</span></span> <span data-ttu-id="b5612-131">É distribuído com o pacote padrão.</span><span class="sxs-lookup"><span data-stu-id="b5612-131">It is distributed with the standard package.</span></span>
- <span data-ttu-id="b5612-132">***demo_usbx.c***: O ficheiro C que contém uma demonstração USBX simples</span><span class="sxs-lookup"><span data-stu-id="b5612-132">***demo_usbx.c***: The C file containing a simple USBX demo</span></span>

<span data-ttu-id="b5612-133">Todos os ficheiros estão em minúsculas.</span><span class="sxs-lookup"><span data-stu-id="b5612-133">All filenames are in lower-case.</span></span> <span data-ttu-id="b5612-134">Esta convenção de nomeação facilita a conversão dos comandos para plataformas de desenvolvimento Unix.</span><span class="sxs-lookup"><span data-stu-id="b5612-134">This naming convention makes it easier to convert the commands to Unix development platforms.</span></span>

## <a name="usbx-installation"></a><span data-ttu-id="b5612-135">Instalação USBX</span><span class="sxs-lookup"><span data-stu-id="b5612-135">USBX Installation</span></span>

<span data-ttu-id="b5612-136">O USBX é instalado através da clonagem do repositório GitHub à sua máquina local.</span><span class="sxs-lookup"><span data-stu-id="b5612-136">USBX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="b5612-137">O seguinte é a sintaxe típica para criar um clone do repositório USBX no seu PC:</span><span class="sxs-lookup"><span data-stu-id="b5612-137">The following is typical syntax for creating a clone of the USBX repository on your PC:</span></span>

```powershell
    git clone https://github.com/azure-rtos/usbx
```

<span data-ttu-id="b5612-138">Em alternativa, pode descarregar uma cópia do repositório utilizando o botão de descarregamento na página principal do GitHub.</span><span class="sxs-lookup"><span data-stu-id="b5612-138">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="b5612-139">Também encontrará instruções para a construção da biblioteca USBX na primeira página do repositório online.</span><span class="sxs-lookup"><span data-stu-id="b5612-139">You will also find instructions for building the USBX library on the front page of the online repository.</span></span>

<span data-ttu-id="b5612-140">As seguintes instruções gerais aplicam-se a praticamente qualquer instalação:</span><span class="sxs-lookup"><span data-stu-id="b5612-140">The following general instructions apply to virtually any installation:</span></span>

1. <span data-ttu-id="b5612-141">Utilize o mesmo diretório em que instalou anteriormente o ThreadX no disco rígido do hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="b5612-141">Use the same directory in which you previously installed ThreadX on the host hard drive.</span></span> <span data-ttu-id="b5612-142">Todos os nomes USBX são únicos e não interferirão com a instalação USBX anterior.</span><span class="sxs-lookup"><span data-stu-id="b5612-142">All USBX names are unique and will not interfere with the previous USBX installation.</span></span>
2. <span data-ttu-id="b5612-143">Adicione uma chamada a \***ux_system_initialize** _ no início ou perto de _ *_tx_application_define_.* \* É aqui que os recursos USBX são inicializados.</span><span class="sxs-lookup"><span data-stu-id="b5612-143">Add a call to ***ux_system_initialize** _ at or near the beginning of _ *_tx_application_define_.** This is where the USBX resources are initialized.</span></span>
3. <span data-ttu-id="b5612-144">Adicione uma chamada para \***ux_host_stack_initialize\*.**</span><span class="sxs-lookup"><span data-stu-id="b5612-144">Add a call to \***ux_host_stack_initialize\*.**</span></span>
4. <span data-ttu-id="b5612-145">Adicione uma ou mais chamadas para inicializar o USBX necessário.</span><span class="sxs-lookup"><span data-stu-id="b5612-145">Add one or more calls to initialize the required USBX.</span></span>
5. <span data-ttu-id="b5612-146">Adicione uma ou mais chamadas para inicializar os controladores hospedeiros disponíveis no sistema.</span><span class="sxs-lookup"><span data-stu-id="b5612-146">Add one or more calls to initialize the host controllers available in the system.</span></span>
6. <span data-ttu-id="b5612-147">Pode ser necessário modificar o ficheiro tx_low_level_initialize.c para adicionar inicialização de hardware de baixo nível e interromper o encaminhamento do vetor.</span><span class="sxs-lookup"><span data-stu-id="b5612-147">It may be required to modify the tx_low_level_initialize.c file to add low-level hardware initialization and interrupt vector routing.</span></span> <span data-ttu-id="b5612-148">Isto é específico da plataforma de hardware e não será discutido aqui.</span><span class="sxs-lookup"><span data-stu-id="b5612-148">This is specific to the hardware platform and will not be discussed here.</span></span>
7. <span data-ttu-id="b5612-149">Compilar o código-fonte da aplicação e ligar-se às bibliotecas de tempo de funcionamento USBX e ThreadX (FileX e/ou Netx também podem ser necessários se a classe de armazenamento USB e/ou as classes de rede USB forem compiladas em), ux.a (ou ux.lib) e tx.a (ou tx.lib).</span><span class="sxs-lookup"><span data-stu-id="b5612-149">Compile application source code and link with the USBX and ThreadX run time libraries (FileX and/or Netx may also be required if the USB storage class and/or USB network classes are to be compiled in), ux.a (or ux.lib) and tx.a (or tx.lib).</span></span> <span data-ttu-id="b5612-150">O resultado pode ser descarregado para o alvo e executado.</span><span class="sxs-lookup"><span data-stu-id="b5612-150">The resulting can be downloaded to the target and executed.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="b5612-151">Opções de configuração</span><span class="sxs-lookup"><span data-stu-id="b5612-151">Configuration Options</span></span>

<span data-ttu-id="b5612-152">Existem várias opções de configuração para a construção da biblioteca USBX.</span><span class="sxs-lookup"><span data-stu-id="b5612-152">There are several configuration options for building the USBX library.</span></span> <span data-ttu-id="b5612-153">Todas as opções estão localizadas no ***ux_user.h***.</span><span class="sxs-lookup"><span data-stu-id="b5612-153">All options are located in the ***ux_user.h***.</span></span>

<span data-ttu-id="b5612-154">A lista abaixo detalha cada opção de configuração.</span><span class="sxs-lookup"><span data-stu-id="b5612-154">The list below details each configuration option.</span></span>


- <span data-ttu-id="b5612-155">**UX_PERIODIC_RATE**: Este valor representa quantos tiques por segundo para uma plataforma de hardware específica.</span><span class="sxs-lookup"><span data-stu-id="b5612-155">**UX_PERIODIC_RATE**: This value represents how many ticks per seconds for a specific hardware platform.</span></span> <span data-ttu-id="b5612-156">O padrão é 1000 indicando um carrapato por milissegundo.</span><span class="sxs-lookup"><span data-stu-id="b5612-156">The default is 1000 indicating one tick per millisecond.</span></span>
- <span data-ttu-id="b5612-157">**UX_MAX_CLASS_DRIVER**: Este valor é o número máximo de classes que podem ser carregadas por USBX.</span><span class="sxs-lookup"><span data-stu-id="b5612-157">**UX_MAX_CLASS_DRIVER**: This value is the maximum number of classes that can be loaded by USBX.</span></span> <span data-ttu-id="b5612-158">Este valor representa o recipiente de classe e não o número de casos de uma classe.</span><span class="sxs-lookup"><span data-stu-id="b5612-158">This value represents the class container and not the number of instances of a class.</span></span> <span data-ttu-id="b5612-159">Por exemplo, se uma determinada implementação do USBX necessitar da classe hub, da classe de impressora e da classe de armazenamento, então o valor UX_MAX_CLASS_DRIVER pode ser definido para 3, independentemente do número de dispositivos que pertencem a estas classes.</span><span class="sxs-lookup"><span data-stu-id="b5612-159">For instance, if a particular implementation of USBX needs the hub class, the printer class, and the storage class, then the UX_MAX_CLASS_DRIVER value can be set to 3 regardless of the number of devices that belong to these classes.</span></span>
- <span data-ttu-id="b5612-160">**UX_MAX_HCD**: Este valor representa o número de diferentes controladores de anfitrião disponíveis no sistema.</span><span class="sxs-lookup"><span data-stu-id="b5612-160">**UX_MAX_HCD**: This value represents the number of different host controllers that are available in the system.</span></span> <span data-ttu-id="b5612-161">Para suporte USB 1.1, este valor será principalmente 1.</span><span class="sxs-lookup"><span data-stu-id="b5612-161">For USB 1.1 support, this value will mostly be 1.</span></span> <span data-ttu-id="b5612-162">Para o suporte USB 2.0 este valor pode ser superior a 1.</span><span class="sxs-lookup"><span data-stu-id="b5612-162">For USB 2.0 support this value can be more than 1.</span></span> <span data-ttu-id="b5612-163">Este valor representa o número de controladores de anfitriões simultâneos em execução ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="b5612-163">This value represents the number of concurrent host controllers running at the same time.</span></span> <span data-ttu-id="b5612-164">Se, por exemplo, existirem dois casos de OHCI em funcionamento ou de um EHCI e de um controlador OHCI em funcionamento, o UX_MAX_HCD deve ser definido para 2.</span><span class="sxs-lookup"><span data-stu-id="b5612-164">If for instance, there are two instances of OHCI running or one EHCI and one OHCI controllers running, the UX_MAX_HCD should be set to 2.</span></span> 
- <span data-ttu-id="b5612-165">**UX_MAX_DEVICES**: Este valor representa o número máximo de dispositivos que podem ser ligados ao USB.</span><span class="sxs-lookup"><span data-stu-id="b5612-165">**UX_MAX_DEVICES**: This value represents the maximum number of devices that can be attached to the USB.</span></span> <span data-ttu-id="b5612-166">Normalmente, o número máximo teórico numa única USB é de 127 dispositivos.</span><span class="sxs-lookup"><span data-stu-id="b5612-166">Normally, the theoretical maximum number on a single USB is 127 devices.</span></span> <span data-ttu-id="b5612-167">Este valor pode ser reduzido para conservar a memória.</span><span class="sxs-lookup"><span data-stu-id="b5612-167">This value can be scaled down to conserve memory.</span></span> <span data-ttu-id="b5612-168">Note-se que este valor representa o número total de dispositivos, independentemente do número de autocarros USB no sistema.</span><span class="sxs-lookup"><span data-stu-id="b5612-168">It should be noted that this value represents the total number of devices regardless of the number of USB buses in the system.</span></span>
- <span data-ttu-id="b5612-169">**UX_MAX_ED**: Este valor representa o número máximo de EDs no conjunto do controlador.</span><span class="sxs-lookup"><span data-stu-id="b5612-169">**UX_MAX_ED**: This value represents the maximum number of EDs in the controller pool.</span></span> <span data-ttu-id="b5612-170">Este número é atribuído apenas a um controlador.</span><span class="sxs-lookup"><span data-stu-id="b5612-170">This number is assigned to one controller only.</span></span> <span data-ttu-id="b5612-171">Se estiverem presentes vários casos de controladores, este valor é utilizado por cada controlador individual.</span><span class="sxs-lookup"><span data-stu-id="b5612-171">If multiple instances of controllers are present, this value is used by each individual controller.</span></span>
- <span data-ttu-id="b5612-172">**UX_MAX_TD e UX_MAX_ISO_TD**: Este valor representa o número máximo de TDs regulares e isocronosos na piscina do controlador.</span><span class="sxs-lookup"><span data-stu-id="b5612-172">**UX_MAX_TD and UX_MAX_ISO_TD**: This value represents the maximum number of regular and isochronous TDs in the controller pool.</span></span> <span data-ttu-id="b5612-173">Este número é atribuído apenas a um controlador.</span><span class="sxs-lookup"><span data-stu-id="b5612-173">This number is assigned to one controller only.</span></span> <span data-ttu-id="b5612-174">Se estiverem presentes vários casos de controladores, este valor é utilizado por cada controlador individual.</span><span class="sxs-lookup"><span data-stu-id="b5612-174">If multiple instances of controllers are present, this value is used by each individual controller.</span></span>
- <span data-ttu-id="b5612-175">**UX_THREAD_STACK_SIZE**: Este valor é o tamanho da stack in bytes para os fios USBX.</span><span class="sxs-lookup"><span data-stu-id="b5612-175">**UX_THREAD_STACK_SIZE**: This value is the size of the stack in bytes for the USBX threads.</span></span> <span data-ttu-id="b5612-176">Pode ser normalmente 1024 bytes ou bytes de 2048 dependendo do processador utilizado e do controlador anfitrião.</span><span class="sxs-lookup"><span data-stu-id="b5612-176">It can be typically 1024 bytes or 2048 bytes depending on the processor used and the host controller.</span></span>
- <span data-ttu-id="b5612-177">**UX_HOST_ENUM_THREAD_STACK_SIZE**: Este valor é o tamanho da pilha do fio de enumeração do hospedeiro USB.</span><span class="sxs-lookup"><span data-stu-id="b5612-177">**UX_HOST_ENUM_THREAD_STACK_SIZE**: This value is the stack size of the USB host enumeration thread.</span></span> <span data-ttu-id="b5612-178">Se este símbolo não definir, o tamanho da pilha de linha de enumeração do anfitrião USBX está definido para **UX_THREAD_STACK_SIZE**.</span><span class="sxs-lookup"><span data-stu-id="b5612-178">If this symbol I not set, the USBX host enumeration thread stack size is set to **UX_THREAD_STACK_SIZE**.</span></span> 
- <span data-ttu-id="b5612-179">**UX_HOST_HCD_THREAD_STACK_SIZE**: Este valor é o tamanho da pilha do fio HCD do anfitrião USB.</span><span class="sxs-lookup"><span data-stu-id="b5612-179">**UX_HOST_HCD_THREAD_STACK_SIZE**: This value is the stack size of the USB host HCD thread.</span></span> <span data-ttu-id="b5612-180">Se este símbolo não definir, o tamanho da pilha de fio HCD do anfitrião USBX está definido para **UX_THREAD_STACK_SIZE**.</span><span class="sxs-lookup"><span data-stu-id="b5612-180">If this symbol I not set, the USBX host HCD thread stack size is set to **UX_THREAD_STACK_SIZE**.</span></span>
- <span data-ttu-id="b5612-181">**UX_THREAD_PRIORITY_ENUM**: Este é o valor prioritário da ThreadX para os fios de enumeração USBX que monitorizam a topologia do autocarro.</span><span class="sxs-lookup"><span data-stu-id="b5612-181">**UX_THREAD_PRIORITY_ENUM**: This is the ThreadX priority value for the USBX enumeration threads that monitors the bus topology.</span></span>
- <span data-ttu-id="b5612-182">**UX_THREAD_PRIORITY_CLASS**: Este é o valor prioritário da ThreadX para as linhas USBX padrão.</span><span class="sxs-lookup"><span data-stu-id="b5612-182">**UX_THREAD_PRIORITY_CLASS**: This is the ThreadX priority value for the standard USBX threads.</span></span>
- <span data-ttu-id="b5612-183">**UX_THREAD_PRIORITY_KEYBOARD**: Este é o valor prioritário da ThreadX para a classe de teclado USBX HID.</span><span class="sxs-lookup"><span data-stu-id="b5612-183">**UX_THREAD_PRIORITY_KEYBOARD**: This is the ThreadX priority value for the USBX HID keyboard class.</span></span>
- <span data-ttu-id="b5612-184">**UX_THREAD_PRIORITY_HCD**: Este é o valor prioritário threadX para o fio do controlador anfitrião.</span><span class="sxs-lookup"><span data-stu-id="b5612-184">**UX_THREAD_PRIORITY_HCD**: This is the ThreadX priority value for the host controller thread.</span></span>
- <span data-ttu-id="b5612-185">**UX_NO_TIME_SLICE**: Este valor define efetivamente a fatia de tempo que será utilizada para os fios.</span><span class="sxs-lookup"><span data-stu-id="b5612-185">**UX_NO_TIME_SLICE**: This value actually defines the time slice that will be used for threads.</span></span> <span data-ttu-id="b5612-186">Por exemplo, se definido para 0, a porta-alvo ThreadX não utiliza fatias de tempo.</span><span class="sxs-lookup"><span data-stu-id="b5612-186">For example, if defined to 0, the ThreadX target port does not use time slices.</span></span>
- <span data-ttu-id="b5612-187">**UX_MAX_HOST_LUN**: Este valor representa o número máximo de unidades lógicas SCSI representadas no condutor da classe de armazenamento de hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="b5612-187">**UX_MAX_HOST_LUN**: This value represents the maximum number of SCSI logical units represented in the host storage class driver.</span></span>
- <span data-ttu-id="b5612-188">**UX_HOST_CLASS_STORAGE_INCLUDE_LEGACY_PROTOCOL_SUPPORT**: Se definido, este valor inclui código para manusear dispositivos de armazenamento que utilizam o protocolo CB ou CBI (como discos disquetes).</span><span class="sxs-lookup"><span data-stu-id="b5612-188">**UX_HOST_CLASS_STORAGE_INCLUDE_LEGACY_PROTOCOL_SUPPORT**: If defined, this value includes code to handle storage devices that use the CB or CBI protocol (such as floppy disks).</span></span> <span data-ttu-id="b5612-189">Está desligado por padrão porque estes protocolos são obsoletos, sendo substituídos pelo Bulk Only Transport (protocolo BOT, que praticamente todos os dispositivos de armazenamento modernos usam.</span><span class="sxs-lookup"><span data-stu-id="b5612-189">It is off by default because these protocols are obsolete, being superseded by the Bulk Only Transport (BOT protocol, which virtually all modern storage devices use.</span></span>
- <span data-ttu-id="b5612-190">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**: Se definido, este valor faz com que ux_host_class_hid_keyboard_key_get reporte apenas alterações de teclas, ou seja, premias de teclas e versões de teclas.</span><span class="sxs-lookup"><span data-stu-id="b5612-190">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**: If defined, this value causes ux_host_class_hid_keyboard_key_get to only report key changes that is, key presses and key releases.</span></span> <span data-ttu-id="b5612-191">Por defeito, só reporta quando uma chave está em baixo.</span><span class="sxs-lookup"><span data-stu-id="b5612-191">By default, it only reports when a key is down.</span></span>
- <span data-ttu-id="b5612-192">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_KEY_DOWN_ONLY**: Só utilizado se **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** for definido.</span><span class="sxs-lookup"><span data-stu-id="b5612-192">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_KEY_DOWN_ONLY**: Only used if **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** is defined.</span></span> <span data-ttu-id="b5612-193">Se definido, faz com que ux_host_class_hid_keyboard_key_get apenas reporte alterações da tecla pressionada/para baixo; as alterações libertadas/up não são reportadas.</span><span class="sxs-lookup"><span data-stu-id="b5612-193">If defined, causes ux_host_class_hid_keyboard_key_get to only report key pressed/down changes; key released/up changes are not reported.</span></span>
- <span data-ttu-id="b5612-194">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_LOCK_KEYS**: Só utilizado se **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** for definido.</span><span class="sxs-lookup"><span data-stu-id="b5612-194">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_LOCK_KEYS**: Only used if **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** is defined.</span></span> <span data-ttu-id="b5612-195">Se definido, faz com que ux_host_class_hid_keyboard_key_get reporte alterações na tecla de bloqueio (CapsLock/NumLock/ScrollLock).</span><span class="sxs-lookup"><span data-stu-id="b5612-195">If defined, causes ux_host_class_hid_keyboard_key_get to report lock key (CapsLock/NumLock/ScrollLock) changes.</span></span>
- <span data-ttu-id="b5612-196">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_MODIFIER_KEYS**: Só utilizado se **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** estiver definido.</span><span class="sxs-lookup"><span data-stu-id="b5612-196">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_MODIFIER_KEYS**: Only used if **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** is defined.</span></span> <span data-ttu-id="b5612-197">Se definido, faz com que ux_host_class_hid_keyboard_key_get reporte alterações na chave modificadora (Ctrl/Alt/Shift/GUI).</span><span class="sxs-lookup"><span data-stu-id="b5612-197">If defined, causes ux_host_class_hid_keyboard_key_get to report modifier key (Ctrl/Alt/Shift/GUI) changes.</span></span>
- <span data-ttu-id="b5612-198">**UX_HOST_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**: Se definido, este valor representa o número de pacotes na classe de anfitrião CDC-ECM.</span><span class="sxs-lookup"><span data-stu-id="b5612-198">**UX_HOST_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**: If defined, this value represents the number of packets in the CDC-ECM host class.</span></span> <span data-ttu-id="b5612-199">O padrão é 16.</span><span class="sxs-lookup"><span data-stu-id="b5612-199">The default is 16.</span></span>

## <a name="source-code-tree"></a><span data-ttu-id="b5612-200">Árvore-código fonte</span><span class="sxs-lookup"><span data-stu-id="b5612-200">Source Code Tree</span></span>

<span data-ttu-id="b5612-201">Os ficheiros USBX são fornecidos em vários diretórios.</span><span class="sxs-lookup"><span data-stu-id="b5612-201">The USBX files are provided in several directories.</span></span>

![Árvore-código fonte](media/usbx-host-stack/source-code-tree.png)

<span data-ttu-id="b5612-203">A fim de tornar os ficheiros reconhecíveis pelos seus nomes, foi adotada a seguinte convenção:</span><span class="sxs-lookup"><span data-stu-id="b5612-203">In order to make the files recognizable by their names, the following convention has been adopted:</span></span>

| <span data-ttu-id="b5612-204">Nome do sufixo de arquivo</span><span class="sxs-lookup"><span data-stu-id="b5612-204">File Suffix Name</span></span> | <span data-ttu-id="b5612-205">Descrição do arquivo</span><span class="sxs-lookup"><span data-stu-id="b5612-205">File description</span></span>                          |
| ---------------- | ----------------------------------------- |
| <span data-ttu-id="b5612-206">ux_host_stack</span><span class="sxs-lookup"><span data-stu-id="b5612-206">ux_host_stack</span></span>    | <span data-ttu-id="b5612-207">usbx host stack ficheiros de núcleo</span><span class="sxs-lookup"><span data-stu-id="b5612-207">usbx host stack core files</span></span>                |
| <span data-ttu-id="b5612-208">ux_host_class</span><span class="sxs-lookup"><span data-stu-id="b5612-208">ux_host_class</span></span>    | <span data-ttu-id="b5612-209">usbx host stack classes arquivos</span><span class="sxs-lookup"><span data-stu-id="b5612-209">usbx host stack classes files</span></span>             |
| <span data-ttu-id="b5612-210">ux_hcd</span><span class="sxs-lookup"><span data-stu-id="b5612-210">ux_hcd</span></span>           | <span data-ttu-id="b5612-211">usbx host stack controladore de controladores</span><span class="sxs-lookup"><span data-stu-id="b5612-211">usbx host stack controller driver files</span></span>   |
| <span data-ttu-id="b5612-212">ux_device_stack</span><span class="sxs-lookup"><span data-stu-id="b5612-212">ux_device_stack</span></span>  | <span data-ttu-id="b5612-213">usbx dispositivo stack ficheiros de núcleo</span><span class="sxs-lookup"><span data-stu-id="b5612-213">usbx device stack core files</span></span>              |
| <span data-ttu-id="b5612-214">ux_device_class</span><span class="sxs-lookup"><span data-stu-id="b5612-214">ux_device_class</span></span>  | <span data-ttu-id="b5612-215">usbx pilha de ficheiros classes</span><span class="sxs-lookup"><span data-stu-id="b5612-215">usbx device stack classes files</span></span>           |
| <span data-ttu-id="b5612-216">ux_dcd</span><span class="sxs-lookup"><span data-stu-id="b5612-216">ux_dcd</span></span>           | <span data-ttu-id="b5612-217">usbx dispositivo stack controladore de controladores</span><span class="sxs-lookup"><span data-stu-id="b5612-217">usbx device stack controller driver files</span></span> |
| <span data-ttu-id="b5612-218">ux_otg</span><span class="sxs-lookup"><span data-stu-id="b5612-218">ux_otg</span></span>           | <span data-ttu-id="b5612-219">usbx otg controladore ficheiros relacionados com o controlador</span><span class="sxs-lookup"><span data-stu-id="b5612-219">usbx otg controller driver related files</span></span>  |
| <span data-ttu-id="b5612-220">ux_pictbridge</span><span class="sxs-lookup"><span data-stu-id="b5612-220">ux_pictbridge</span></span>    | <span data-ttu-id="b5612-221">usbx pictbridge arquivos</span><span class="sxs-lookup"><span data-stu-id="b5612-221">usbx pictbridge files</span></span>                     |
| <span data-ttu-id="b5612-222">ux_utility</span><span class="sxs-lookup"><span data-stu-id="b5612-222">ux_utility</span></span>       | <span data-ttu-id="b5612-223">funções de utilidade usbx</span><span class="sxs-lookup"><span data-stu-id="b5612-223">usbx utility functions</span></span>                    |
| <span data-ttu-id="b5612-224">demo_usbx</span><span class="sxs-lookup"><span data-stu-id="b5612-224">demo_usbx</span></span>        | <span data-ttu-id="b5612-225">ficheiros de demonstração para USBX</span><span class="sxs-lookup"><span data-stu-id="b5612-225">demonstration files for USBX</span></span>              |

## <a name="initialization-of-usbx-resources"></a><span data-ttu-id="b5612-226">Inicialização dos recursos USBX</span><span class="sxs-lookup"><span data-stu-id="b5612-226">Initialization of USBX resources</span></span>

<span data-ttu-id="b5612-227">A USBX tem o seu próprio gestor de memória.</span><span class="sxs-lookup"><span data-stu-id="b5612-227">USBX has its own memory manager.</span></span> <span data-ttu-id="b5612-228">A memória precisa de ser atribuída ao USBX antes da inicialação do lado do anfitrião ou do dispositivo do USBX.</span><span class="sxs-lookup"><span data-stu-id="b5612-228">The memory needs to be allocated to USBX before the host or device side of USBX is initialized.</span></span> <span data-ttu-id="b5612-229">O gestor de memória USBX pode acomodar sistemas onde a memória pode ser em cache.</span><span class="sxs-lookup"><span data-stu-id="b5612-229">USBX memory manager can accommodate systems where memory can be cached.</span></span>

<span data-ttu-id="b5612-230">A seguinte função inicializa os recursos de memória USBX com 128K de memória regular e nenhuma piscina separada para a memória segura da cache:</span><span class="sxs-lookup"><span data-stu-id="b5612-230">The following function initializes USBX memory resources with 128K of regular memory and no separate pool for cache safe memory:</span></span>

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

<span data-ttu-id="b5612-231">O protótipo para a ux_system_initialize é o seguinte.</span><span class="sxs-lookup"><span data-stu-id="b5612-231">The prototype for the ux_system_initialize is as follows.</span></span>

```c
UINT ux_system_initialize( 
    VOID *regular_memory_pool_start,
    ULONG regular_memory_size,
    VOID *cache_safe_memory_pool_start,
    ULONG cache_safe_memory_size);
```

### <a name="input-parameters"></a><span data-ttu-id="b5612-232">Parâmetros de entrada:</span><span class="sxs-lookup"><span data-stu-id="b5612-232">Input parameters:</span></span>

- <span data-ttu-id="b5612-233">**regular_memory_pool_start** Início da piscina de memórias regular.</span><span class="sxs-lookup"><span data-stu-id="b5612-233">**regular_memory_pool_start** Beginning of the regular memory pool.</span></span>
- <span data-ttu-id="b5612-234">**regular_memory_size** Tamanho da piscina de memória regular.</span><span class="sxs-lookup"><span data-stu-id="b5612-234">**regular_memory_size** Size of the regular memory pool.</span></span>
- <span data-ttu-id="b5612-235">**cache_safe_memory_pool_start** Início da piscina de memória segura da cache.</span><span class="sxs-lookup"><span data-stu-id="b5612-235">**cache_safe_memory_pool_start** Beginning of the cache safe memory pool.</span></span>
- <span data-ttu-id="b5612-236">**cache_safe_memory_size** Tamanho da piscina de memória segura cache.</span><span class="sxs-lookup"><span data-stu-id="b5612-236">**cache_safe_memory_size** Size of the cache safe memory pool.</span></span>    |

<span data-ttu-id="b5612-237">Nem todos os sistemas requerem a definição de memória segura da cache.</span><span class="sxs-lookup"><span data-stu-id="b5612-237">Not all systems require the definition of cache safe memory.</span></span> <span data-ttu-id="b5612-238">Neste sistema, os valores passados durante a inicialização do ponteiro de memória serão definidos para UX_NULL e o tamanho da piscina para 0.</span><span class="sxs-lookup"><span data-stu-id="b5612-238">In such a system, the values passed during the initialization for the memory pointer will be set to UX_NULL and the size of the pool to 0.</span></span> <span data-ttu-id="b5612-239">A USBX utilizará então o pool de memória regular em vez da piscina segura da cache.</span><span class="sxs-lookup"><span data-stu-id="b5612-239">USBX will then use the regular memory pool in lieu of the cache safe pool.</span></span>

<span data-ttu-id="b5612-240">Num sistema em que a memória regular não é segura em cache e um controlador requer a realização da memória DMA (como OHCI, controladores EHCI entre outros) é necessário definir um pool de memória numa zona segura de cache.</span><span class="sxs-lookup"><span data-stu-id="b5612-240">In a system where the regular memory is not cache safe and a controller requires to perform DMA memory (like OHCI, EHCI controllers amongst others) it is necessary to define a memory pool in a cache safe zone.</span></span>

## <a name="uninitialization-of-usbx-resources"></a><span data-ttu-id="b5612-241">Uniinialização dos recursos USBX</span><span class="sxs-lookup"><span data-stu-id="b5612-241">Uninitialization of USBX resources</span></span>

<span data-ttu-id="b5612-242">O USBX pode ser encerrado libertando os seus recursos.</span><span class="sxs-lookup"><span data-stu-id="b5612-242">USBX can be terminated by releasing its resources.</span></span> <span data-ttu-id="b5612-243">Antes de terminar a usbx, todas as classes e recursos controladores devem ser encerrados corretamente.</span><span class="sxs-lookup"><span data-stu-id="b5612-243">Prior to terminating usbx, all classes and controller resources need to be terminated properly.</span></span> <span data-ttu-id="b5612-244">A seguinte função não iniializa os recursos de memória USBX:</span><span class="sxs-lookup"><span data-stu-id="b5612-244">The following function uninitializes USBX memory resources :</span></span>

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

<span data-ttu-id="b5612-245">O protótipo para a ux_system_initialize é o seguinte.</span><span class="sxs-lookup"><span data-stu-id="b5612-245">The prototype for the ux_system_initialize is as follows.</span></span>

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-host-controllers"></a><span data-ttu-id="b5612-246">Definição de controladores de anfitriões USB</span><span class="sxs-lookup"><span data-stu-id="b5612-246">Definition of USB Host Controllers</span></span>

<span data-ttu-id="b5612-247">É necessário definir pelo menos um controlador usb para o USBX operar no modo de anfitrião.</span><span class="sxs-lookup"><span data-stu-id="b5612-247">It is required to define at least one USB host controller for USBX to operate in host mode.</span></span> <span data-ttu-id="b5612-248">O ficheiro de inicialização da aplicação deve conter esta definição.</span><span class="sxs-lookup"><span data-stu-id="b5612-248">The application initialization file should contain this definition.</span></span> <span data-ttu-id="b5612-249">A seguinte linha executa a definição de um controlador de hospedeiro genérico.</span><span class="sxs-lookup"><span data-stu-id="b5612-249">The following line performs the definition of a generic host controller.</span></span>

```c
ux_host_stack_hcd_register("ux_hcd_controller",
        ux_hcd_controller_initialize, 0xd0000, 0x0a);
```

<span data-ttu-id="b5612-250">O ux_host_stack_hcd_register tem o seguinte protótipo.</span><span class="sxs-lookup"><span data-stu-id="b5612-250">The ux_host_stack_hcd_register has the following prototype.</span></span>

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_initialize_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

<span data-ttu-id="b5612-251">A função ux_host_stack_hcd_register tem os seguintes parâmetros.</span><span class="sxs-lookup"><span data-stu-id="b5612-251">The ux_host_stack_hcd_register function has the following parameters.</span></span>

- <span data-ttu-id="b5612-252">**hcd_name**: cadeia do nome do controlador</span><span class="sxs-lookup"><span data-stu-id="b5612-252">**hcd_name**: string of the controller name</span></span>
- <span data-ttu-id="b5612-253">**hcd_initialize_function**: função de inicialização do controlador</span><span class="sxs-lookup"><span data-stu-id="b5612-253">**hcd_initialize_function**: initialization function of the controller</span></span>
- <span data-ttu-id="b5612-254">**hcd_param1:** normalmente o valor IO ou memória utilizado pelo controlador</span><span class="sxs-lookup"><span data-stu-id="b5612-254">**hcd_param1**: usually the IO value or Memory used by the controller</span></span>
- <span data-ttu-id="b5612-255">**hcd_param2:** normalmente o IRQ utilizado pelo controlador</span><span class="sxs-lookup"><span data-stu-id="b5612-255">**hcd_param2**: usually the IRQ used by the controller</span></span>

<span data-ttu-id="b5612-256">No nosso exemplo anterior:</span><span class="sxs-lookup"><span data-stu-id="b5612-256">In our previous example:</span></span>

- <span data-ttu-id="b5612-257">"ux_hcd_controller" é o nome do controlador</span><span class="sxs-lookup"><span data-stu-id="b5612-257">"ux_hcd_controller" is the name of the controller</span></span>
- <span data-ttu-id="b5612-258">"ux_hcd_controller_initialize" é a rotina de inicialização do controlador anfitrião</span><span class="sxs-lookup"><span data-stu-id="b5612-258">"ux_hcd_controller_initialize" is the initialization routine for the host controller</span></span>
- <span data-ttu-id="b5612-259">0xd0000 é o endereço em que os registos do controlador anfitrião são visíveis na memória</span><span class="sxs-lookup"><span data-stu-id="b5612-259">0xd0000 is the address at which the host controller registers are visible in memory</span></span>
- <span data-ttu-id="b5612-260">e 0x0a é o IRQ usado pelo controlador hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="b5612-260">and 0x0a is the IRQ used by the host controller.</span></span>

<span data-ttu-id="b5612-261">Segue-se um exemplo da inicialização do USBX no modo hospedeiro com um controlador de anfitrião e várias classes.</span><span class="sxs-lookup"><span data-stu-id="b5612-261">Following is an example of the initialization of USBX in host mode with one host controller and several classes.</span></span>

```c
UINT status;

/* Initialize USBX. */
ux_system_initialize(memory_ptr, (128*1024),0,0);

/* The code below is required for installing the USBX host stack. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, host stack has been initialized. */

/* Register all the host classes for this USBX implementation. */
status = ux_host_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_storage", ux_host_class_storage_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_printer", ux_host_class_printer_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_audio", ux_host_class_audio_entry);

/* If status equals UX_SUCCESS, host class has been registered. */

/* Register all the USB host controllers available in this system. */ 
status = ux_host_stack_hcd_register("ux_hcd_controller", ux_hcd_controller_initialize, 0x300000, 0x0a);

/* If status equals UX_SUCCESS, USB host controllers have been registered. */
```

## <a name="definition-of-host-classes"></a><span data-ttu-id="b5612-262">Definição de aulas de anfitrião</span><span class="sxs-lookup"><span data-stu-id="b5612-262">Definition of Host Classes</span></span>

<span data-ttu-id="b5612-263">É necessário definir uma ou mais classes de anfitriões com USBX.</span><span class="sxs-lookup"><span data-stu-id="b5612-263">It is required to define one or more host classes with USBX.</span></span> <span data-ttu-id="b5612-264">É necessária uma classe USB para conduzir um dispositivo USB depois de a pilha USB ter configurado o dispositivo USB.</span><span class="sxs-lookup"><span data-stu-id="b5612-264">A USB class is required to drive a USB device after the USB stack has configured the USB device.</span></span> <span data-ttu-id="b5612-265">Uma classe USB é específica do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b5612-265">A USB class is specific to the device.</span></span> <span data-ttu-id="b5612-266">Uma ou mais classes podem ser necessárias para conduzir um dispositivo USB dependendo do número de interfaces contidas nos descritores do dispositivo USB.</span><span class="sxs-lookup"><span data-stu-id="b5612-266">One or more classes may be required to drive a USB device depending on the number of interfaces contained in the USB device descriptors.</span></span>

<span data-ttu-id="b5612-267">Este é um exemplo do registo da classe HUB.</span><span class="sxs-lookup"><span data-stu-id="b5612-267">This is an example of the registration of the HUB class.</span></span>

```c
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);
```

<span data-ttu-id="b5612-268">A função ux_host_class_register tem o seguinte protótipo.</span><span class="sxs-lookup"><span data-stu-id="b5612-268">The function ux_host_class_register has the following prototype.</span></span>

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name, 
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

- <span data-ttu-id="b5612-269">**class_name** é o nome da classe</span><span class="sxs-lookup"><span data-stu-id="b5612-269">**class_name** is the name of the class</span></span>
- <span data-ttu-id="b5612-270">**class_entry_address** é o ponto de entrada da classe</span><span class="sxs-lookup"><span data-stu-id="b5612-270">**class_entry_address** is the entry point of the class</span></span>

<span data-ttu-id="b5612-271">No exemplo da inicialização da classe HUB:</span><span class="sxs-lookup"><span data-stu-id="b5612-271">In the example of the HUB class initialization:</span></span>

- <span data-ttu-id="b5612-272">"ux_host_class_hub" é o nome da classe hub</span><span class="sxs-lookup"><span data-stu-id="b5612-272">"ux_host_class_hub" is the name of the hub class</span></span>
- <span data-ttu-id="b5612-273">ux_host_class_hub_entry é o ponto de entrada da classe HUB.</span><span class="sxs-lookup"><span data-stu-id="b5612-273">ux_host_class_hub_entry is the entry point of the HUB class.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="b5612-274">Resolução de problemas</span><span class="sxs-lookup"><span data-stu-id="b5612-274">Troubleshooting</span></span>

<span data-ttu-id="b5612-275">USBX é entregue com um ficheiro de demonstração e um ambiente de simulação.</span><span class="sxs-lookup"><span data-stu-id="b5612-275">USBX is delivered with a demonstration file and a simulation environment.</span></span> <span data-ttu-id="b5612-276">É sempre uma boa ideia pôr a plataforma de demonstração em primeiro lugar - seja no hardware-alvo ou numa plataforma de demonstração específica.</span><span class="sxs-lookup"><span data-stu-id="b5612-276">It is always a good idea to get the demonstration platform running first—either on the target hardware or a specific demonstration platform.</span></span>

<span data-ttu-id="b5612-277">Se o sistema de demonstração não funcionar, tente as seguintes coisas para reduzir o problema.</span><span class="sxs-lookup"><span data-stu-id="b5612-277">If the demonstration system does not work, try the following things to narrow the problem.</span></span>

## <a name="usbx-version-id"></a><span data-ttu-id="b5612-278">ID da versão USBX</span><span class="sxs-lookup"><span data-stu-id="b5612-278">USBX Version ID</span></span>

<span data-ttu-id="b5612-279">A versão atual do USBX está disponível tanto para o utilizador como para o software da aplicação durante o tempo de funcionamento.</span><span class="sxs-lookup"><span data-stu-id="b5612-279">The current version of USBX is available both to the user and the application software during run-time.</span></span> <span data-ttu-id="b5612-280">O programador pode obter a versão USBX a partir do exame do ficheiro \***ux_port.h** _</span><span class="sxs-lookup"><span data-stu-id="b5612-280">The programmer can obtain the USBX version from examination of the \***ux_port.h** _ file.</span></span> <span data-ttu-id="b5612-281">Além disso, este ficheiro também contém um histórico de versão da porta correspondente.</span><span class="sxs-lookup"><span data-stu-id="b5612-281">In addition, this file also contains a version history of the corresponding port.</span></span> <span data-ttu-id="b5612-282">O software de aplicação pode obter a versão USBX examinando a cadeia global *_ __ ux_version_id_* _, que é definida em _\*_ux_port.h\*\*._</span><span class="sxs-lookup"><span data-stu-id="b5612-282">Application software can obtain the USBX version by examining the global string _ *_ _ux_version_id_* _, which is defined in _\*_ux_port.h_\*\*.</span></span>
