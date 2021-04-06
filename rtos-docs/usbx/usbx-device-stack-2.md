---
title: Capítulo 2 - Instalação de pilha de dispositivos USBX Azure RTOS
description: Saiba como instalar a pilha de dispositivos USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 62f036af27c5da29baf9cba58b5b26631167c3a1
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377157"
---
# <a name="chapter-2---azure-rtos-usbx-device-stack-installation"></a><span data-ttu-id="0cfbe-103">Capítulo 2 - Instalação de pilha de dispositivos USBX Azure RTOS</span><span class="sxs-lookup"><span data-stu-id="0cfbe-103">Chapter 2 - Azure RTOS USBX Device Stack Installation</span></span>

## <a name="host-considerations"></a><span data-ttu-id="0cfbe-104">Considerações de Anfitrião</span><span class="sxs-lookup"><span data-stu-id="0cfbe-104">Host Considerations</span></span>

### <a name="computer-type"></a><span data-ttu-id="0cfbe-105">Tipo de computador</span><span class="sxs-lookup"><span data-stu-id="0cfbe-105">Computer Type</span></span>

<span data-ttu-id="0cfbe-106">O desenvolvimento incorporado é geralmente realizado em computadores anfitriões Windows PC ou Unix.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-106">Embedded development is usually performed on Windows PC or Unix host computers.</span></span> <span data-ttu-id="0cfbe-107">Após a compilação da aplicação, ligada e localizada no anfitrião, é descarregada para o hardware alvo para execução.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-107">After the application is compiled, linked, and located on the host, it is downloaded to the target hardware for execution.</span></span>

### <a name="download-interfaces"></a><span data-ttu-id="0cfbe-108">Baixar Interfaces</span><span class="sxs-lookup"><span data-stu-id="0cfbe-108">Download Interfaces</span></span>

<span data-ttu-id="0cfbe-109">Normalmente, o download do alvo é feito através de uma interface de série RS-232, embora interfaces paralelas, USB e Ethernet estejam a tornar-se mais populares.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-109">Usually the target download is done over an RS-232 serial interface, although parallel interfaces, USB, and Ethernet are becoming more popular.</span></span> <span data-ttu-id="0cfbe-110">Consulte a documentação da ferramenta de desenvolvimento para obter as opções disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-110">See the development tool documentation for available options.</span></span>

### <a name="debugging-tools"></a><span data-ttu-id="0cfbe-111">Ferramentas de depurar</span><span class="sxs-lookup"><span data-stu-id="0cfbe-111">Debugging Tools</span></span>

<span data-ttu-id="0cfbe-112">Depurar é feito normalmente sobre o mesmo link que o download de imagem do programa.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-112">Debugging is done typically over the same link as the program image download.</span></span> <span data-ttu-id="0cfbe-113">Existe uma variedade de depuradores, desde pequenos programas de monitor que correm no alvo através do Background Debug Monitor (BDM) e In-Circuit ferramentas emuladoras (ICE).</span><span class="sxs-lookup"><span data-stu-id="0cfbe-113">A variety of debuggers exist, ranging from small monitor programs running on the target through Background Debug Monitor (BDM) and In-Circuit Emulator (ICE) tools.</span></span> <span data-ttu-id="0cfbe-114">A ferramenta ICE fornece a depuragem mais robusta do hardware alvo real.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-114">The ICE tool provides the most robust debugging of actual target hardware.</span></span>

### <a name="required-hard-disk-space"></a><span data-ttu-id="0cfbe-115">Espaço de disco rígido necessário</span><span class="sxs-lookup"><span data-stu-id="0cfbe-115">Required Hard Disk Space</span></span>

<span data-ttu-id="0cfbe-116">O código-fonte do USBX é entregue em formato ASCII e requer aproximadamente 500 KBytes de espaço no disco rígido do computador anfitrião.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-116">The source code for USBX is delivered in ASCII format and requires approximately 500 KBytes of space on the host computer's hard disk.</span></span>

### <a name="target-considerations"></a><span data-ttu-id="0cfbe-117">Considerações-alvo</span><span class="sxs-lookup"><span data-stu-id="0cfbe-117">Target Considerations</span></span>

<span data-ttu-id="0cfbe-118">USBX requer entre 24 KBytes e 64 KBytes de Read Only Memory (ROM) no alvo no modo anfitrião.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-118">USBX requires between 24 KBytes and 64 KBytes of Read Only Memory (ROM) on the target in host mode.</span></span> <span data-ttu-id="0cfbe-119">A quantidade de memória necessária depende do tipo de controlador utilizado e das classes USB ligadas ao USBX.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-119">The amount of memory required is dependent on the type of controller used and the USB classes linked to USBX.</span></span> <span data-ttu-id="0cfbe-120">Outros 32 KBytes da Memória de Acesso Aleatório (RAM) do alvo são necessários para estruturas de dados globais USBX e piscina de memória.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-120">Another 32 KBytes of the target's Random Access Memory (RAM) are required for USBX global data structures and memory pool.</span></span> <span data-ttu-id="0cfbe-121">Este conjunto de memórias também pode ser ajustado dependendo do número esperado de dispositivos no USB e do tipo de controlador USB.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-121">This memory pool can also be adjusted depending on the expected number of devices on the USB and the type of USB controller.</span></span> <span data-ttu-id="0cfbe-122">O lado do dispositivo USBX requer aproximadamente 10-12 K de ROM dependendo do tipo de controlador do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-122">The USBX device side requires roughly 10-12 K of ROM depending on the type of device controller.</span></span> <span data-ttu-id="0cfbe-123">O uso da memória RAM depende do tipo de classe emulsionada pelo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-123">The RAM memory usage depends on the type of class emulated by the device.</span></span>

<span data-ttu-id="0cfbe-124">A USBX também conta com semáforos ThreadX, mutexes e fios para proteção de múltiplos fios, e suspensão de I/O e processamento periódico para monitorizar a topologia do autocarro USB.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-124">USBX also relies on ThreadX semaphores, mutexes, and threads for multiple thread protection, and I/O suspension and periodic processing for monitoring the USB bus topology.</span></span>

### <a name="product-distribution"></a><span data-ttu-id="0cfbe-125">Distribuição de Produtos</span><span class="sxs-lookup"><span data-stu-id="0cfbe-125">Product Distribution</span></span>

<span data-ttu-id="0cfbe-126">O Azure RTOS USBX pode ser obtido a partir do nosso repositório de código de fonte pública em <https://github.com/azure-rtos/usbx/> .</span><span class="sxs-lookup"><span data-stu-id="0cfbe-126">Azure RTOS USBX can be obtained from our public source code repository at <https://github.com/azure-rtos/usbx/>.</span></span>

<span data-ttu-id="0cfbe-127">Segue-se uma lista de vários ficheiros importantes no repositório.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-127">The following is a list of several important files in the repository.</span></span>

* <span data-ttu-id="0cfbe-128">***ux_api.h:*** Este ficheiro de cabeçalho C contém todos os equacionares do sistema, estruturas de dados e protótipos de serviço.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-128">***ux_api.h***: This C header file contains all system equates, data structures, and service prototypes.</span></span>
* <span data-ttu-id="0cfbe-129">***ux_port.h:*** Este ficheiro de cabeçalho C contém todas as definições e estruturas específicas da ferramenta de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-129">***ux_port.h***: This C header file contains all development-tool-specific data definitions and structures.</span></span>
* <span data-ttu-id="0cfbe-130">***ux.lib***: Esta é a versão binária da biblioteca USBX C.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-130">***ux.lib***:  This is the binary version of the USBX C library.</span></span> <span data-ttu-id="0cfbe-131">É distribuído com o pacote padrão.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-131">It is distributed with the standard package.</span></span>
* <span data-ttu-id="0cfbe-132">***demo_usbx.c***: O ficheiro C que contém uma demonstração USBX simples</span><span class="sxs-lookup"><span data-stu-id="0cfbe-132">***demo_usbx.c***: The C file containing a simple USBX demo</span></span>

<span data-ttu-id="0cfbe-133">Todos os ficheiros estão em minúsculas.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-133">All filenames are in lower-case.</span></span> <span data-ttu-id="0cfbe-134">Esta convenção de nomeação facilita a conversão dos comandos para plataformas de desenvolvimento Unix.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-134">This naming convention makes it easier to convert the commands to Unix development platforms.</span></span>

## <a name="usbx-installation"></a><span data-ttu-id="0cfbe-135">Instalação USBX</span><span class="sxs-lookup"><span data-stu-id="0cfbe-135">USBX Installation</span></span>

<span data-ttu-id="0cfbe-136">O USBX é instalado através da clonagem do repositório GitHub à sua máquina local.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-136">USBX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="0cfbe-137">O seguinte é a sintaxe típica para criar um clone do repositório USBX no seu PC:</span><span class="sxs-lookup"><span data-stu-id="0cfbe-137">The following is typical syntax for creating a clone of the USBX repository on your PC:</span></span>

```c
    git clone https://github.com/azure-rtos/usbx
```

<span data-ttu-id="0cfbe-138">Em alternativa, pode descarregar uma cópia do repositório utilizando o botão de descarregamento na página principal do GitHub.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-138">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="0cfbe-139">Também encontrará instruções para a construção da biblioteca USBX na primeira página do repositório online.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-139">You will also find instructions for building the USBX library on the front page of the online repository.</span></span>

<span data-ttu-id="0cfbe-140">As seguintes instruções gerais aplicam-se a praticamente qualquer instalação:</span><span class="sxs-lookup"><span data-stu-id="0cfbe-140">The following general instructions apply to virtually any installation:</span></span>

1. <span data-ttu-id="0cfbe-141">Utilize o mesmo diretório em que instalou anteriormente o ThreadX no disco rígido do hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-141">Use the same directory in which you previously installed ThreadX on the host hard drive.</span></span> <span data-ttu-id="0cfbe-142">Todos os nomes USBX são únicos e não interferirão com a instalação USBX anterior.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-142">All USBX names are unique and will not interfere with the previous USBX installation.</span></span>
1. <span data-ttu-id="0cfbe-143">Adicione uma chamada a ***ux_system_initialize** _ no ou perto do início de _*_tx_application_define_\*\*.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-143">Add a call to ***ux_system_initialize** _ at or near the beginning of _*_tx_application_define_\*\*.</span></span> <span data-ttu-id="0cfbe-144">É aqui que os recursos USBX são inicializados.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-144">This is where the USBX resources are initialized.</span></span>
1. <span data-ttu-id="0cfbe-145">Adicione uma chamada para \***ux_device_stack_initialize\*.**</span><span class="sxs-lookup"><span data-stu-id="0cfbe-145">Add a call to \***ux_device_stack_initialize\*.**</span></span>
1. <span data-ttu-id="0cfbe-146">Adicione uma ou mais chamadas para inicializar as classes USBX necessárias (aulas de anfitrião e/ou dispositivos)</span><span class="sxs-lookup"><span data-stu-id="0cfbe-146">Add one or more calls to initialize the required USBX classes (either host and/or devices classes)</span></span>
1. <span data-ttu-id="0cfbe-147">Adicione uma ou mais chamadas para inicializar o controlador do dispositivo disponível no sistema.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-147">Add one or more calls to initialize the device controller available in the system.</span></span>
1. <span data-ttu-id="0cfbe-148">Pode ser necessário modificar o ficheiro tx_low_level_initialize.c para adicionar inicialização de hardware de baixo nível e interromper o encaminhamento do vetor.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-148">It may be required to modify the tx_low_level_initialize.c file to add low-level hardware initialization and interrupt vector routing.</span></span> <span data-ttu-id="0cfbe-149">Isto é específico da plataforma de hardware e não será discutido aqui.|</span><span class="sxs-lookup"><span data-stu-id="0cfbe-149">This is specific to the hardware platform and will not be discussed here.|</span></span>
1. <span data-ttu-id="0cfbe-150">Compilar o código-fonte da aplicação e ligar-se às bibliotecas de tempo de funcionamento USBX e ThreadX (FileX e/ou Netx também podem ser necessários se a classe de armazenamento USB e/ou as classes de rede USB forem compiladas em), ux.a (ou ux.lib) e tx.a (ou tx.lib).</span><span class="sxs-lookup"><span data-stu-id="0cfbe-150">Compile application source code and link with the USBX and ThreadX run time libraries (FileX and/or Netx may also be required if the USB storage class and/or USB network classes are to be compiled in), ux.a (or ux.lib) and tx.a (or tx.lib).</span></span> <span data-ttu-id="0cfbe-151">O resultado pode ser descarregado para o alvo e executado!</span><span class="sxs-lookup"><span data-stu-id="0cfbe-151">The resulting can be downloaded to the target and executed!</span></span>

## <a name="configuration-options"></a><span data-ttu-id="0cfbe-152">Opções de configuração</span><span class="sxs-lookup"><span data-stu-id="0cfbe-152">Configuration Options</span></span>

<span data-ttu-id="0cfbe-153">Existem várias opções de configuração para a construção da biblioteca USBX.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-153">There are several configuration options for building the USBX library.</span></span> <span data-ttu-id="0cfbe-154">Todas as opções estão localizadas no ***ux_user.h***.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-154">All options are located in the ***ux_user.h***.</span></span>

<span data-ttu-id="0cfbe-155">A lista abaixo detalha cada opção de configuração.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-155">The list below details each configuration option.</span></span>

| <span data-ttu-id="0cfbe-156">Opção de configuração &nbsp;</span><span class="sxs-lookup"><span data-stu-id="0cfbe-156">Configuration&nbsp;Option</span></span> | <span data-ttu-id="0cfbe-157">Descrição</span><span class="sxs-lookup"><span data-stu-id="0cfbe-157">Description</span></span> |
| --- | --- |
| <span data-ttu-id="0cfbe-158">**UX_PERIODIC_RATE**</span><span class="sxs-lookup"><span data-stu-id="0cfbe-158">**UX_PERIODIC_RATE**</span></span> | <span data-ttu-id="0cfbe-159">Este valor representa quantos tiques por segundo para uma plataforma de hardware específica.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-159">This value represents how many ticks per seconds for a specific hardware platform.</span></span> <span data-ttu-id="0cfbe-160">O padrão é 1000 indicando 1 carrapato por milissegundo.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-160">The default is 1000 indicating 1 tick per millisecond.</span></span> |
| <span data-ttu-id="0cfbe-161">**UX_THREAD_STACK_SIZE**</span><span class="sxs-lookup"><span data-stu-id="0cfbe-161">**UX_THREAD_STACK_SIZE**</span></span> | <span data-ttu-id="0cfbe-162">Este valor é o tamanho da stack in bytes para os fios USBX.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-162">This value is the size of the stack in bytes for the USBX threads.</span></span> <span data-ttu-id="0cfbe-163">Pode ser normalmente 1024 bytes ou bytes de 2048 dependendo do processador utilizado e do controlador anfitrião.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-163">It can be typically 1024 bytes or 2048 bytes depending on the processor used and the host controller.</span></span> |
| <span data-ttu-id="0cfbe-164">**UX_THREAD_PRIORITY_ENUM**</span><span class="sxs-lookup"><span data-stu-id="0cfbe-164">**UX_THREAD_PRIORITY_ENUM**</span></span> | <span data-ttu-id="0cfbe-165">Este é o valor prioritário da ThreadX para os fios de enumeração USBX que monitorizam a topologia do autocarro.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-165">This is the ThreadX priority value for the USBX enumeration threads that monitors the bus topology.</span></span> |
| <span data-ttu-id="0cfbe-166">**UX_THREAD_PRIORITY_CLASS**</span><span class="sxs-lookup"><span data-stu-id="0cfbe-166">**UX_THREAD_PRIORITY_CLASS**</span></span> | <span data-ttu-id="0cfbe-167">Este é o valor prioritário threadX para os fios USBX padrão.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-167">This is the ThreadX priority value for the standard USBX threads.</span></span> |
| <span data-ttu-id="0cfbe-168">**UX_THREAD_PRIORITY_KEYBOARD**</span><span class="sxs-lookup"><span data-stu-id="0cfbe-168">**UX_THREAD_PRIORITY_KEYBOARD**</span></span> | <span data-ttu-id="0cfbe-169">Este é o valor prioritário threadX para a classe de teclado USBX HID.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-169">This is the ThreadX priority value for the USBX HID keyboard class.</span></span> |
| <span data-ttu-id="0cfbe-170">**UX_THREAD_PRIORITY_DCD**</span><span class="sxs-lookup"><span data-stu-id="0cfbe-170">**UX_THREAD_PRIORITY_DCD**</span></span> | <span data-ttu-id="0cfbe-171">Este é o valor prioritário threadX para o fio do controlador do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-171">This is the ThreadX priority value for the device controller thread.</span></span> |
| <span data-ttu-id="0cfbe-172">**UX_NO_TIME_SLICE**</span><span class="sxs-lookup"><span data-stu-id="0cfbe-172">**UX_NO_TIME_SLICE**</span></span> | <span data-ttu-id="0cfbe-173">Este valor define realmente a fatia de tempo que será usada para fios.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-173">This value actually defines the time slice that will be used for threads.</span></span> <span data-ttu-id="0cfbe-174">Por exemplo, se definido para 0, a porta-alvo ThreadX não utiliza fatias de tempo.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-174">For example, if defined to 0, the ThreadX target port does not use time slices.</span></span> |
| <span data-ttu-id="0cfbe-175">**UX_MAX_SLAVE_CLASS_DRIVER**</span><span class="sxs-lookup"><span data-stu-id="0cfbe-175">**UX_MAX_SLAVE_CLASS_DRIVER**</span></span> | <span data-ttu-id="0cfbe-176">Este é o número máximo de classes USBX que podem ser registadas através de ux_device_stack_class_register.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-176">This is the maximum number of USBX classes that can be registered via ux_device_stack_class_register.</span></span> |
| <span data-ttu-id="0cfbe-177">**UX_MAX_SLAVE_LUN**</span><span class="sxs-lookup"><span data-stu-id="0cfbe-177">**UX_MAX_SLAVE_LUN**</span></span> | <span data-ttu-id="0cfbe-178">Este valor representa o número atual de unidades lógicas SCSI representadas no controlador da classe de armazenamento do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-178">This value represents the current number of SCSI logical units represented in the device storage class driver.</span></span> |
| <span data-ttu-id="0cfbe-179">**UX_SLAVE_CLASS_STORAGE_INCLUDE_MMC**</span><span class="sxs-lookup"><span data-stu-id="0cfbe-179">**UX_SLAVE_CLASS_STORAGE_INCLUDE_MMC**</span></span> | <span data-ttu-id="0cfbe-180">Se definido, a classe de armazenamento irá lidar com comandos multimédia (MMC) ou seja, DVD-ROM.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-180">If defined, the storage class will handle Multi-Media Commands (MMC) that is, DVD-ROM.</span></span> |
| <span data-ttu-id="0cfbe-181">**UX_DEVICE_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**</span><span class="sxs-lookup"><span data-stu-id="0cfbe-181">**UX_DEVICE_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**</span></span> | <span data-ttu-id="0cfbe-182">Este valor representa o número de pacotes NetX na piscina de pacotes da classe CDC-ECM.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-182">This value represents the number of NetX packets in the CDC-ECM class' packet pool.</span></span> <span data-ttu-id="0cfbe-183">O padrão é 16.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-183">The default is 16.</span></span> |
| <span data-ttu-id="0cfbe-184">**UX_SLAVE_REQUEST_CONTROL_MAX_LENGTH**</span><span class="sxs-lookup"><span data-stu-id="0cfbe-184">**UX_SLAVE_REQUEST_CONTROL_MAX_LENGTH**</span></span> | <span data-ttu-id="0cfbe-185">Este valor representa o número máximo de bytes recebidos num ponto final de controlo na pilha do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-185">This value represents the maximum number of bytes received on a control endpoint in the device stack.</span></span> <span data-ttu-id="0cfbe-186">O padrão é de 256 bytes, mas pode ser reduzido em ambientes de restrição de memória.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-186">The default is 256 bytes but can be reduced in memory constraint environments.</span></span> |
| <span data-ttu-id="0cfbe-187">**UX_DEVICE_CLASS_HID_EVENT_BUFFER_LENGTH**</span><span class="sxs-lookup"><span data-stu-id="0cfbe-187">**UX_DEVICE_CLASS_HID_EVENT_BUFFER_LENGTH**</span></span> | <span data-ttu-id="0cfbe-188">Este valor representa o comprimento máximo em bytes de um relatório HID.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-188">This value represents the maximum length in bytes of a HID report.</span></span> |
| <span data-ttu-id="0cfbe-189">**UX_DEVICE_CLASS_HID_MAX_EVENTS_QUEUE**</span><span class="sxs-lookup"><span data-stu-id="0cfbe-189">**UX_DEVICE_CLASS_HID_MAX_EVENTS_QUEUE**</span></span> | <span data-ttu-id="0cfbe-190">Este valor representa o número máximo de relatórios HID que podem ser feito em fila imediatamente.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-190">This value represents the maximum number of HID reports that can be queued at once.</span></span> |
| <span data-ttu-id="0cfbe-191">**UX_SLAVE_REQUEST_DATA_MAX_LENGTH**</span><span class="sxs-lookup"><span data-stu-id="0cfbe-191">**UX_SLAVE_REQUEST_DATA_MAX_LENGTH**</span></span> | <span data-ttu-id="0cfbe-192">Este valor representa o número máximo de bytes recebidos num ponto final a granel na pilha do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-192">This value represents the maximum number of bytes received on a bulk endpoint in the device stack.</span></span> <span data-ttu-id="0cfbe-193">O padrão é 4096 bytes, mas pode ser reduzido em ambientes de restrição de memória.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-193">The default is 4096 bytes but can be reduced in memory constraint environments.</span></span> |

## <a name="source-code-tree"></a><span data-ttu-id="0cfbe-194">Árvore-código fonte</span><span class="sxs-lookup"><span data-stu-id="0cfbe-194">Source Code Tree</span></span>

<span data-ttu-id="0cfbe-195">Os ficheiros USBX são fornecidos em vários diretórios.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-195">The USBX files are provided in several directories.</span></span>

![Árvore-código fonte](media/usbx-device-stack/source-code-tree.png)

<span data-ttu-id="0cfbe-197">A fim de tornar os ficheiros reconhecíveis pelos seus nomes, foi adotada a seguinte convenção:</span><span class="sxs-lookup"><span data-stu-id="0cfbe-197">In order to make the files recognizable by their names, the following convention has been adopted:</span></span>

| <span data-ttu-id="0cfbe-198">Nome do sufixo de arquivo</span><span class="sxs-lookup"><span data-stu-id="0cfbe-198">File Suffix Name</span></span>  | <span data-ttu-id="0cfbe-199">Descrição do arquivo</span><span class="sxs-lookup"><span data-stu-id="0cfbe-199">File description</span></span>                          |
| ----------------- | ----------------------------------------- |
| <span data-ttu-id="0cfbe-200">ux_host_stack</span><span class="sxs-lookup"><span data-stu-id="0cfbe-200">ux_host_stack</span></span>   | <span data-ttu-id="0cfbe-201">usbx host stack ficheiros de núcleo</span><span class="sxs-lookup"><span data-stu-id="0cfbe-201">usbx host stack core files</span></span>                |
| <span data-ttu-id="0cfbe-202">ux_host_class</span><span class="sxs-lookup"><span data-stu-id="0cfbe-202">ux_host_class</span></span>   | <span data-ttu-id="0cfbe-203">usbx host stack classes arquivos</span><span class="sxs-lookup"><span data-stu-id="0cfbe-203">usbx host stack classes files</span></span>             |
| <span data-ttu-id="0cfbe-204">ux_hcd</span><span class="sxs-lookup"><span data-stu-id="0cfbe-204">ux_hcd</span></span>           | <span data-ttu-id="0cfbe-205">usbx host stack controladore de controladores</span><span class="sxs-lookup"><span data-stu-id="0cfbe-205">usbx host stack controller driver files</span></span>   |
| <span data-ttu-id="0cfbe-206">ux_device_stack</span><span class="sxs-lookup"><span data-stu-id="0cfbe-206">ux_device_stack</span></span> | <span data-ttu-id="0cfbe-207">usbx dispositivo stack ficheiros de núcleo</span><span class="sxs-lookup"><span data-stu-id="0cfbe-207">usbx device stack core files</span></span>              |
| <span data-ttu-id="0cfbe-208">ux_device_class</span><span class="sxs-lookup"><span data-stu-id="0cfbe-208">ux_device_class</span></span> | <span data-ttu-id="0cfbe-209">usbx pilha de ficheiros classes</span><span class="sxs-lookup"><span data-stu-id="0cfbe-209">usbx device stack classes files</span></span>           |
| <span data-ttu-id="0cfbe-210">ux_dcd</span><span class="sxs-lookup"><span data-stu-id="0cfbe-210">ux_dcd</span></span>           | <span data-ttu-id="0cfbe-211">usbx dispositivo stack controladore de controladores</span><span class="sxs-lookup"><span data-stu-id="0cfbe-211">usbx device stack controller driver files</span></span> |
| <span data-ttu-id="0cfbe-212">ux_otg</span><span class="sxs-lookup"><span data-stu-id="0cfbe-212">ux_otg</span></span>           | <span data-ttu-id="0cfbe-213">usbx otg controladore ficheiros relacionados com o controlador</span><span class="sxs-lookup"><span data-stu-id="0cfbe-213">usbx otg controller driver related files</span></span>  |
| <span data-ttu-id="0cfbe-214">ux_pictbridge</span><span class="sxs-lookup"><span data-stu-id="0cfbe-214">ux_pictbridge</span></span>    | <span data-ttu-id="0cfbe-215">usbx pictbridge arquivos</span><span class="sxs-lookup"><span data-stu-id="0cfbe-215">usbx pictbridge files</span></span>                     |
| <span data-ttu-id="0cfbe-216">ux_utility</span><span class="sxs-lookup"><span data-stu-id="0cfbe-216">ux_utility</span></span>       | <span data-ttu-id="0cfbe-217">funções de utilidade usbx</span><span class="sxs-lookup"><span data-stu-id="0cfbe-217">usbx utility functions</span></span>                    |
| <span data-ttu-id="0cfbe-218">demo_usbx</span><span class="sxs-lookup"><span data-stu-id="0cfbe-218">demo_usbx</span></span>        | <span data-ttu-id="0cfbe-219">ficheiros de demonstração para USBX</span><span class="sxs-lookup"><span data-stu-id="0cfbe-219">demonstration files for USBX</span></span>              |

## <a name="initialization-of-usbx-resources"></a><span data-ttu-id="0cfbe-220">Inicialização dos recursos USBX</span><span class="sxs-lookup"><span data-stu-id="0cfbe-220">Initialization of USBX resources</span></span>

<span data-ttu-id="0cfbe-221">A USBX tem o seu próprio gestor de memória.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-221">USBX has its own memory manager.</span></span> <span data-ttu-id="0cfbe-222">A memória precisa de ser atribuída ao USBX antes da inicialação do lado do anfitrião ou do dispositivo do USBX.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-222">The memory needs to be allocated to USBX before the host or device side of USBX is initialized.</span></span> <span data-ttu-id="0cfbe-223">O gestor de memória USBX pode acomodar sistemas onde a memória pode ser em cache.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-223">USBX memory manager can accommodate systems where memory can be cached.</span></span>

<span data-ttu-id="0cfbe-224">A seguinte função inicializa os recursos de memória USBX com 128 K de memória regular e nenhuma piscina separada para a memória segura da cache:</span><span class="sxs-lookup"><span data-stu-id="0cfbe-224">The following function initializes USBX memory resources with 128 K of regular memory and no separate pool for cache safe memory:</span></span>

```c
/* Initialize USBX Memory */
ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

<span data-ttu-id="0cfbe-225">O protótipo para a ux_system_initialize é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0cfbe-225">The prototype for the ux_system_initialize is as follows:</span></span>

```c
UINT ux_system_initialize(VOID *regular_memory_pool_start,
        ULONG regular_memory_size,
        VOID *cache_safe_memory_pool_start,
        ULONG cache_safe_memory_size);
```

<span data-ttu-id="0cfbe-226">Parâmetros de entrada:</span><span class="sxs-lookup"><span data-stu-id="0cfbe-226">Input parameters:</span></span>

| <span data-ttu-id="0cfbe-227">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="0cfbe-227">Parameter</span></span>                          | <span data-ttu-id="0cfbe-228">Descrição</span><span class="sxs-lookup"><span data-stu-id="0cfbe-228">Description</span></span>                             |
| ---------------------------------- | --------------------------------------- |
| <span data-ttu-id="0cfbe-229">VOID \*regular_memory_pool_start</span><span class="sxs-lookup"><span data-stu-id="0cfbe-229">VOID \*regular_memory_pool_start</span></span>    | <span data-ttu-id="0cfbe-230">Início da piscina de memória regular</span><span class="sxs-lookup"><span data-stu-id="0cfbe-230">Beginning of the regular memory pool</span></span>    |
| <span data-ttu-id="0cfbe-231">regular_memory_size da ULONG</span><span class="sxs-lookup"><span data-stu-id="0cfbe-231">ULONG regular_memory_size</span></span>          | <span data-ttu-id="0cfbe-232">Tamanho da piscina de memória regular</span><span class="sxs-lookup"><span data-stu-id="0cfbe-232">Size of the regular memory pool</span></span>         |
| <span data-ttu-id="0cfbe-233">VOID \*cache_safe_memory_pool_start</span><span class="sxs-lookup"><span data-stu-id="0cfbe-233">VOID \*cache_safe_memory_pool_start</span></span> | <span data-ttu-id="0cfbe-234">Início da piscina de memória segura da cache</span><span class="sxs-lookup"><span data-stu-id="0cfbe-234">Beginning of the cache safe memory pool</span></span> |
| <span data-ttu-id="0cfbe-235">cache_safe_memory_size da ULONG</span><span class="sxs-lookup"><span data-stu-id="0cfbe-235">ULONG cache_safe_memory_size</span></span>       | <span data-ttu-id="0cfbe-236">Tamanho da piscina de memória segura cache</span><span class="sxs-lookup"><span data-stu-id="0cfbe-236">Size of the cache safe memory pool</span></span>      |

<span data-ttu-id="0cfbe-237">Nem todos os sistemas requerem a definição de memória segura da cache.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-237">Not all systems require the definition of cache safe memory.</span></span> <span data-ttu-id="0cfbe-238">Neste sistema, os valores passados durante a inicialização do ponteiro de memória serão definidos para UX_NULL e o tamanho da piscina para 0.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-238">In such a system, the values passed during the initialization for the memory pointer will be set to UX_NULL and the size of the pool to 0.</span></span> <span data-ttu-id="0cfbe-239">A USBX utilizará então o pool de memória regular em vez da piscina segura da cache.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-239">USBX will then use the regular memory pool in lieu of the cache safe pool.</span></span>

<span data-ttu-id="0cfbe-240">Num sistema em que a memória regular não é segura em cache e um controlador requer que execute a memória DMA é necessário definir um conjunto de memórias numa zona segura de cache.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-240">In a system where the regular memory is not cache safe and a controller requires to perform DMA memory it is necessary to define a memory pool in a cache safe zone.</span></span>

## <a name="uninitialization-of-usbx-resources"></a><span data-ttu-id="0cfbe-241">Uniinialização dos recursos USBX</span><span class="sxs-lookup"><span data-stu-id="0cfbe-241">Uninitialization of USBX resources</span></span>

<span data-ttu-id="0cfbe-242">O USBX pode ser encerrado libertando os seus recursos.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-242">USBX can be terminated by releasing its resources.</span></span> <span data-ttu-id="0cfbe-243">Antes de terminar a usbx, todas as classes e recursos controladores devem ser encerrados corretamente.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-243">Prior to terminating usbx, all classes and controller resources need to be terminated properly.</span></span> <span data-ttu-id="0cfbe-244">A seguinte função não iniializa os recursos de memória USBX:</span><span class="sxs-lookup"><span data-stu-id="0cfbe-244">The following function uninitializes USBX memory resources:</span></span>

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

<span data-ttu-id="0cfbe-245">O protótipo para a ux_system_initialize é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0cfbe-245">The prototype for the ux_system_initialize is as follows:</span></span>

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-device-controller"></a><span data-ttu-id="0cfbe-246">Definição de controlador de dispositivos USB</span><span class="sxs-lookup"><span data-stu-id="0cfbe-246">Definition of USB Device Controller</span></span>

<span data-ttu-id="0cfbe-247">Apenas um controlador de dispositivo USB pode ser definido a qualquer momento para funcionar no modo de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-247">Only one USB device controller can be defined at any time to operate in device mode.</span></span> <span data-ttu-id="0cfbe-248">O ficheiro de inicialização da aplicação deve conter esta definição.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-248">The application initialization file should contain this definition.</span></span> <span data-ttu-id="0cfbe-249">A seguinte linha executa a definição de um controlador usb genérico:</span><span class="sxs-lookup"><span data-stu-id="0cfbe-249">The following line performs the definition of a generic usb controller:</span></span>

```c
ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);
```

<span data-ttu-id="0cfbe-250">A inicialização do dispositivo USB tem o seguinte protótipo:</span><span class="sxs-lookup"><span data-stu-id="0cfbe-250">The USB device initialization has the following prototype:</span></span>

```c
UINT ux_dcd_controller_initialize(ULONG dcd_io,
    ULONG dcd_irq, ULONG dcd_vbus_address);
```

<span data-ttu-id="0cfbe-251">com os seguintes parâmetros:</span><span class="sxs-lookup"><span data-stu-id="0cfbe-251">with the following parameters:</span></span>

| <span data-ttu-id="0cfbe-252">Pararmeter</span><span class="sxs-lookup"><span data-stu-id="0cfbe-252">Pararmeter</span></span>               | <span data-ttu-id="0cfbe-253">Descrição</span><span class="sxs-lookup"><span data-stu-id="0cfbe-253">Description</span></span>                      |
| ------------------------ | -------------------------------- |
| <span data-ttu-id="0cfbe-254">dcd_io ULONG</span><span class="sxs-lookup"><span data-stu-id="0cfbe-254">ULONG dcd_io</span></span>            | <span data-ttu-id="0cfbe-255">Endereço do controlador IO</span><span class="sxs-lookup"><span data-stu-id="0cfbe-255">Address of the controller IO</span></span>     |
| <span data-ttu-id="0cfbe-256">dcd_irq ULONG</span><span class="sxs-lookup"><span data-stu-id="0cfbe-256">ULONG dcd_irq</span></span>           | <span data-ttu-id="0cfbe-257">Interrupção utilizada pelo controlador</span><span class="sxs-lookup"><span data-stu-id="0cfbe-257">Interrupt used by the controller</span></span> |
| <span data-ttu-id="0cfbe-258">dcd_vbus_address da ULONG</span><span class="sxs-lookup"><span data-stu-id="0cfbe-258">ULONG dcd_vbus_address</span></span> | <span data-ttu-id="0cfbe-259">Endereço do GPIO VBUS</span><span class="sxs-lookup"><span data-stu-id="0cfbe-259">Address of the VBUS GPIO</span></span>         |

<span data-ttu-id="0cfbe-260">Segue-se a inicialização do USBX no modo dispositivo com a classe do dispositivo de armazenamento e um controlador genérico:</span><span class="sxs-lookup"><span data-stu-id="0cfbe-260">The following example is the initialization of USBX in device mode with the storage device class and a generic controller:</span></span>

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024), 0, 0);

/* The code below is required for installing the device portion of USBX */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, installation was successful. */

/* Store the number of LUN in this device storage instance: single LUN. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 1;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x1e6bfe;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read = tx_demo_thread_flash_media_read;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write = tx_demo_thread_flash_media_write;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status = tx_demo_thread_flash_media_status;

/* Initialize the device storage class. The class is connected with interface 0 */
status = ux_device_stack_class_register(ux_system_slave_class_storage_name ux_device_class_storage_entry,
    ux_device_class_storage_thread,0, (VOID *)&storage_parameter);

/* Register the device controllers available in this system */
status = ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);

/* If status equals UX_SUCCESS, registration was successful. */
```

## <a name="troubleshooting"></a><span data-ttu-id="0cfbe-261">Resolução de problemas</span><span class="sxs-lookup"><span data-stu-id="0cfbe-261">Troubleshooting</span></span>

<span data-ttu-id="0cfbe-262">USBX é entregue com um ficheiro de demonstração e um ambiente de simulação.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-262">USBX is delivered with a demonstration file and a simulation environment.</span></span> <span data-ttu-id="0cfbe-263">É sempre uma boa ideia pôr a plataforma de demonstração em primeiro lugar - seja no hardware-alvo ou numa plataforma de demonstração específica.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-263">It is always a good idea to get the demonstration platform running first—either on the target hardware or a specific demonstration platform.</span></span>

## <a name="usbx-version-id"></a><span data-ttu-id="0cfbe-264">ID da versão USBX</span><span class="sxs-lookup"><span data-stu-id="0cfbe-264">USBX Version ID</span></span>

<span data-ttu-id="0cfbe-265">A versão atual do USBX está disponível tanto para o utilizador como para o software da aplicação durante o tempo de funcionamento.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-265">The current version of USBX is available both to the user and the application software during run-time.</span></span> <span data-ttu-id="0cfbe-266">O programador pode obter a versão USBX a partir do exame do ficheiro \***ux_port.h** _</span><span class="sxs-lookup"><span data-stu-id="0cfbe-266">The programmer can obtain the USBX version from examination of the \***ux_port.h** _ file.</span></span> <span data-ttu-id="0cfbe-267">Além disso, este ficheiro também contém um histórico de versão da porta correspondente.</span><span class="sxs-lookup"><span data-stu-id="0cfbe-267">In addition, this file also contains a version history of the corresponding port.</span></span> <span data-ttu-id="0cfbe-268">O software de aplicação pode obter a versão USBX examinando a cadeia global *_ __ ux_version_id_* _, que é definida em _\*_ux_port.h\*\*._</span><span class="sxs-lookup"><span data-stu-id="0cfbe-268">Application software can obtain the USBX version by examining the global string _ *_ _ux_version_id_* _, which is defined in _\*_ux_port.h_\*\*.</span></span>
