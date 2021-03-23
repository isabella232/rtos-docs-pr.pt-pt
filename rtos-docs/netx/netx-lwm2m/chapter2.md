---
title: Capítulo 2 - Instalação e utilização do Azure RTOS NetX LWM2M
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NetX LWM2M.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8c13d3b092d3a5b59bd0369f6ffc162509d02590
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826701"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-lwm2m"></a><span data-ttu-id="bfd80-103">Capítulo 2 - Instalação e utilização do Azure RTOS NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="bfd80-103">Chapter 2 - Installation and use of Azure RTOS NetX LWM2M</span></span>

<span data-ttu-id="bfd80-104">Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NetX LWM2M.</span><span class="sxs-lookup"><span data-stu-id="bfd80-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX LWM2M component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="bfd80-105">Distribuição de Produtos</span><span class="sxs-lookup"><span data-stu-id="bfd80-105">Product Distribution</span></span>

<span data-ttu-id="bfd80-106">NetX LWM2M está disponível em [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) .</span><span class="sxs-lookup"><span data-stu-id="bfd80-106">NetX LWM2M is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="bfd80-107">O pacote inclui três ficheiros de origem, um inclui ficheiros e um ficheiro PDF que contém este documento, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="bfd80-107">The package includes three source files, one include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="bfd80-108">**nx_lwm2m_client.h:** Ficheiro de cabeçalho para o Cliente NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="bfd80-108">**nx_lwm2m_client.h**: Header file for the NetX LWM2M Client</span></span>

- <span data-ttu-id="bfd80-109">**nx_lwm2m_\*.c/h:** Ficheiros C/H Source para NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="bfd80-109">**nx_lwm2m_\*.c/h**: C/H Source files for NetX LWM2M</span></span>

- <span data-ttu-id="bfd80-110">**demo_netx_lwm2m_client.c**: Ficheiro C Fonte para demonstração de clientes NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="bfd80-110">**demo_netx_lwm2m_client.c**: C Source file for NetX LWM2M Client Demo</span></span>

- <span data-ttu-id="bfd80-111">**NetX_LWM2M_User_Guide.pdf**: Descrição em PDF do produto NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="bfd80-111">**NetX_LWM2M_User_Guide.pdf**: PDF description of NetX LWM2M product</span></span>

## <a name="netx-lwm2m-installation"></a><span data-ttu-id="bfd80-112">Instalação NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="bfd80-112">NetX LWM2M Installation</span></span>

<span data-ttu-id="bfd80-113">Para utilizar o NetX LWM2M, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX está instalado.</span><span class="sxs-lookup"><span data-stu-id="bfd80-113">In order to use NetX LWM2M, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="bfd80-114">Por exemplo, se o NetX for instalado no diretório "*\\ threadx \\ arm7 \\ green*" então os *ficheiros nx_lwm2m&#42;.&#42;* devem ser copiados para este diretório.</span><span class="sxs-lookup"><span data-stu-id="bfd80-114">For example, if NetX is installed in the directory "*\\threadx\\arm7\\green*" then the *nx_lwm2m&#42;.&#42;* files should be copied into this directory.</span></span>

## <a name="using-netx-lwm2m"></a><span data-ttu-id="bfd80-115">Utilização do NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="bfd80-115">Using NetX LWM2M</span></span>

<span data-ttu-id="bfd80-116">A utilização do NetX LWM2M é fácil.</span><span class="sxs-lookup"><span data-stu-id="bfd80-116">Using NetX LWM2M is easy.</span></span> <span data-ttu-id="bfd80-117">Basicamente, o código de aplicação deve incluir *nx_lwm2m_client.h* depois de incluir *tx_api.h* e *nx_api.h,* para utilizar o ThreadX e o NetX.</span><span class="sxs-lookup"><span data-stu-id="bfd80-117">Basically, the application code must include *nx_lwm2m_client.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span> <span data-ttu-id="bfd80-118">Uma vez *incluído nx_lwm2m_client.h,* o código de aplicação é então capaz de fazer as chamadas de função NetX LWM2M especificadas mais tarde neste guia.</span><span class="sxs-lookup"><span data-stu-id="bfd80-118">Once *nx_lwm2m_client.h* is included, the application code is then able to make the NetX LWM2M function calls specified later in this guide.</span></span> <span data-ttu-id="bfd80-119">O pedido também deve importar os *ficheiros nx_lwm2m&#42;.&#42;* para a biblioteca NetX.</span><span class="sxs-lookup"><span data-stu-id="bfd80-119">The application must also import the *nx_lwm2m&#42;.&#42;* files into the NetX library.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="bfd80-120">Opções de configuração</span><span class="sxs-lookup"><span data-stu-id="bfd80-120">Configuration Options</span></span>

<span data-ttu-id="bfd80-121">Existem várias opções de configuração ao construir a biblioteca LWM2M Client e a aplicação utilizando o Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="bfd80-121">There are several configuration options when building the LWM2M Client library and the application using the LWM2M Client.</span></span> <span data-ttu-id="bfd80-122">As opções de configuração podem ser definidas na fonte de aplicação, na linha de comando, salvo especificação em contrário.</span><span class="sxs-lookup"><span data-stu-id="bfd80-122">The configuration options can be defined in the application source, on the command line, unless otherwise specified.</span></span>

### <a name="nx_lwm2m_client_disable_error_checking"></a><span data-ttu-id="bfd80-123">NX_LWM2M_CLIENT_DISABLE_ERROR_CHECKING</span><span class="sxs-lookup"><span data-stu-id="bfd80-123">NX_LWM2M_CLIENT_DISABLE_ERROR_CHECKING</span></span>

<span data-ttu-id="bfd80-124">Definido, remove o erro básico do Cliente LWM2M verificando a API e melhora o desempenho.</span><span class="sxs-lookup"><span data-stu-id="bfd80-124">Defined, removes the basic LWM2M Client error checking API and improves performance.</span></span> <span data-ttu-id="bfd80-125">Os códigos de devolução da API não afetados pela verificação de erros incapacitantes estão listados em tipo de letra arrojado na definição API.</span><span class="sxs-lookup"><span data-stu-id="bfd80-125">API return codes not affected by disabling error checking are listed in bold typeface in the API definition.</span></span>

### <a name="nx_lwm2m_client_disable_float"></a><span data-ttu-id="bfd80-126">NX_LWM2M_CLIENT_DISABLE_FLOAT</span><span class="sxs-lookup"><span data-stu-id="bfd80-126">NX_LWM2M_CLIENT_DISABLE_FLOAT</span></span>

<span data-ttu-id="bfd80-127">Definido, remove o suporte dos valores dos números dos pontos flutuantes.</span><span class="sxs-lookup"><span data-stu-id="bfd80-127">Defined, removes the support of floating point numbers values.</span></span> <span data-ttu-id="bfd80-128">Quando desativado, o Cliente LWM2M não pode suportar Recursos com tipo de dados Float.</span><span class="sxs-lookup"><span data-stu-id="bfd80-128">When disabled the LWM2M Client cannot support Resources with Float data type.</span></span>

### <a name="nx_lwm2m_client_disable_float64"></a><span data-ttu-id="bfd80-129">NX_LWM2M_CLIENT_DISABLE_FLOAT64</span><span class="sxs-lookup"><span data-stu-id="bfd80-129">NX_LWM2M_CLIENT_DISABLE_FLOAT64</span></span>

<span data-ttu-id="bfd80-130">Definido, remove o suporte de valores de ponto flutuante de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="bfd80-130">Defined, removes the support of 64-bit floating point numbers values.</span></span> <span data-ttu-id="bfd80-131">O Cliente LWM2M ainda pode receber mensagens TLV contendo números flutuantes de 64 bits, mas os valores são convertidos para ponto flutuante de 32 bits para processamento.</span><span class="sxs-lookup"><span data-stu-id="bfd80-131">The LWM2M Client can still receive TLV messages containing 64-bit floating numbers, but the values are converted to 32-bit floating point for processing.</span></span>

### <a name="nx_lwm2m_client_priority"></a><span data-ttu-id="bfd80-132">NX_LWM2M_CLIENT_PRIORITY</span><span class="sxs-lookup"><span data-stu-id="bfd80-132">NX_LWM2M_CLIENT_PRIORITY</span></span>

<span data-ttu-id="bfd80-133">Especifica a prioridade da linha do Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="bfd80-133">Specifies the priority of the LWM2M Client thread.</span></span> <span data-ttu-id="bfd80-134">Por predefinição, este valor é definido como 16 para especificar a prioridade 16.</span><span class="sxs-lookup"><span data-stu-id="bfd80-134">By default, this value is defined as 16 to specify priority 16.</span></span>

### <a name="nx_lwm2m_client_max_device_errors"></a><span data-ttu-id="bfd80-135">NX_LWM2M_CLIENT_MAX_DEVICE_ERRORS</span><span class="sxs-lookup"><span data-stu-id="bfd80-135">NX_LWM2M_CLIENT_MAX_DEVICE_ERRORS</span></span>

<span data-ttu-id="bfd80-136">Especifica o número máximo de códigos de erro armazenados pelo Objeto do Dispositivo.</span><span class="sxs-lookup"><span data-stu-id="bfd80-136">Specifies the maximum number of error codes stored by the Device Object.</span></span> <span data-ttu-id="bfd80-137">O valor predefinido é 8.</span><span class="sxs-lookup"><span data-stu-id="bfd80-137">The default value is 8.</span></span>

### <a name="nx_lwm2m_client_max_security_instances"></a><span data-ttu-id="bfd80-138">NX_LWM2M_CLIENT_MAX_SECURITY_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="bfd80-138">NX_LWM2M_CLIENT_MAX_SECURITY_INSTANCES</span></span>

<span data-ttu-id="bfd80-139">Especifica o número máximo de instâncias de objetos de segurança.</span><span class="sxs-lookup"><span data-stu-id="bfd80-139">Specifies the maximum number of Security Object Instances.</span></span> <span data-ttu-id="bfd80-140">O valor predefinido é 2 para suportar um Servidor Bootstrap e um Servidor padrão.</span><span class="sxs-lookup"><span data-stu-id="bfd80-140">The default value is 2 for supporting a Bootstrap Server and a standard Server.</span></span>

### <a name="nx_lwm2m_client_max_server_instances"></a><span data-ttu-id="bfd80-141">NX_LWM2M_CLIENT_MAX_SERVER_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="bfd80-141">NX_LWM2M_CLIENT_MAX_SERVER_INSTANCES</span></span>

<span data-ttu-id="bfd80-142">Especifica o número máximo de instâncias de objetos de servidor.</span><span class="sxs-lookup"><span data-stu-id="bfd80-142">Specifies the maximum number of Server Object Instances.</span></span> <span data-ttu-id="bfd80-143">O valor predefinido é 1 para suportar um único Servidor padrão.</span><span class="sxs-lookup"><span data-stu-id="bfd80-143">The default value is 1 for supporting a single standard Server.</span></span>

### <a name="nx_lwm2m_client_max_server_uri"></a><span data-ttu-id="bfd80-144">NX_LWM2M_CLIENT_MAX_SERVER_URI</span><span class="sxs-lookup"><span data-stu-id="bfd80-144">NX_LWM2M_CLIENT_MAX_SERVER_URI</span></span>

<span data-ttu-id="bfd80-145">Especifica o comprimento máximo de um URI do servidor, incluindo o carácter nulo.</span><span class="sxs-lookup"><span data-stu-id="bfd80-145">Specifies the maximum length of a server URI, including terminating nil character.</span></span> <span data-ttu-id="bfd80-146">O valor predefinido é de 128.</span><span class="sxs-lookup"><span data-stu-id="bfd80-146">The default value is 128.</span></span>

### <a name="nx_lwm2m_client_max_access_control_instances"></a><span data-ttu-id="bfd80-147">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="bfd80-147">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_INSTANCES</span></span>

<span data-ttu-id="bfd80-148">Especifica o número máximo de instâncias de controlo de acesso.</span><span class="sxs-lookup"><span data-stu-id="bfd80-148">Specifies the maximum number of Access Control Instances.</span></span> <span data-ttu-id="bfd80-149">O valor predefinido é 0, que desativa o controlo de acesso.</span><span class="sxs-lookup"><span data-stu-id="bfd80-149">The default value is 0, which disables access control.</span></span> <span data-ttu-id="bfd80-150">Se a aplicação suportar mais de um Servidor LWM2M, o número máximo de Instâncias de Controlo de Acesso deve ser definido para o número máximo de instâncias de objeto que o Cliente LWM2M irá suportar, uma vez que uma Instância de Controlo de Acesso deve ser criada para cada Instância de Objeto (exceto para as Instâncias de Objeto de Segurança).</span><span class="sxs-lookup"><span data-stu-id="bfd80-150">If the application supports more than one LWM2M Server, the maximum number of Access Control Instances must be set to the maximum number of Object Instances that the LWM2M Client will support, as one Access Control Instance must be created for each Object Instance (except for the Security Object Instances).</span></span>

### <a name="nx_lwm2m_client_max_access_control_acls"></a><span data-ttu-id="bfd80-151">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_ACLS</span><span class="sxs-lookup"><span data-stu-id="bfd80-151">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_ACLS</span></span>

<span data-ttu-id="bfd80-152">Especifica o número máximo de recursos ACL por Instância de Controlo de Acesso.</span><span class="sxs-lookup"><span data-stu-id="bfd80-152">Specifies the maximum number of ACL resources per Access Control Instance.</span></span> <span data-ttu-id="bfd80-153">O valor predefinido é 4.</span><span class="sxs-lookup"><span data-stu-id="bfd80-153">The default value is 4.</span></span>

### <a name="nx_lwm2m_client_max_notifications"></a><span data-ttu-id="bfd80-154">NX_LWM2M_CLIENT_MAX_NOTIFICATIONS</span><span class="sxs-lookup"><span data-stu-id="bfd80-154">NX_LWM2M_CLIENT_MAX_NOTIFICATIONS</span></span>

<span data-ttu-id="bfd80-155">Especifica o número máximo de notificações que o Cliente LWM2M irá suportar.</span><span class="sxs-lookup"><span data-stu-id="bfd80-155">Specifies the maximum number of notifications that the LWM2M Client will support.</span></span> <span data-ttu-id="bfd80-156">Um Servidor LWM2M pode definir notificações em Objetos, Instâncias de Objetos e Recursos.</span><span class="sxs-lookup"><span data-stu-id="bfd80-156">A LWM2M Server can set notifications on Objects, Object Instances, and Resources.</span></span> <span data-ttu-id="bfd80-157">O valor predefinido é 8.</span><span class="sxs-lookup"><span data-stu-id="bfd80-157">The default value is 8.</span></span>

### <a name="nx_lwm2m_client_max_resources"></a><span data-ttu-id="bfd80-158">NX_LWM2M_CLIENT_MAX_RESOURCES</span><span class="sxs-lookup"><span data-stu-id="bfd80-158">NX_LWM2M_CLIENT_MAX_RESOURCES</span></span>

<span data-ttu-id="bfd80-159">Especifica o número máximo de Recursos por Objeto.</span><span class="sxs-lookup"><span data-stu-id="bfd80-159">Specifies the maximum number of Resources per Object.</span></span> <span data-ttu-id="bfd80-160">O valor predefinido é 32.</span><span class="sxs-lookup"><span data-stu-id="bfd80-160">The default value is 32.</span></span>

### <a name="nx_lwm2m_client_bootstrap_idle_timer"></a><span data-ttu-id="bfd80-161">NX_LWM2M_CLIENT_BOOTSTRAP_IDLE_TIMER</span><span class="sxs-lookup"><span data-stu-id="bfd80-161">NX_LWM2M_CLIENT_BOOTSTRAP_IDLE_TIMER</span></span>

<span data-ttu-id="bfd80-162">Especifica o tempo máximo para esperar pelos pedidos do servidor bootstrap quando a sessão de bootstrap é iniciada antes de abortar a sessão.</span><span class="sxs-lookup"><span data-stu-id="bfd80-162">Specifies the maximum time to wait for bootstrap server requests when the bootstrap session is initiated before aborting the session.</span></span> <span data-ttu-id="bfd80-163">O valor predefinido é de 60 segundos.</span><span class="sxs-lookup"><span data-stu-id="bfd80-163">The default value is 60 seconds.</span></span>

### <a name="nx_lwm2m_client_dtls_start_timeout"></a><span data-ttu-id="bfd80-164">NX_LWM2M_CLIENT_DTLS_START_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bfd80-164">NX_LWM2M_CLIENT_DTLS_START_TIMEOUT</span></span>

<span data-ttu-id="bfd80-165">Especifica o tempo máximo para esperar pela conclusão do aperto de mão DTLS.</span><span class="sxs-lookup"><span data-stu-id="bfd80-165">Specifies the maximum time to wait for DTLS handshake completion.</span></span> <span data-ttu-id="bfd80-166">O valor predefinido é de 30 segundos.</span><span class="sxs-lookup"><span data-stu-id="bfd80-166">The default value is 30 seconds.</span></span>

### <a name="nx_lwm2m_client_dtls_end_timeout"></a><span data-ttu-id="bfd80-167">NX_LWM2M_CLIENT_DTLS_END_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bfd80-167">NX_LWM2M_CLIENT_DTLS_END_TIMEOUT</span></span>

<span data-ttu-id="bfd80-168">Especifica o tempo máximo para esperar pela conclusão do encerramento do DTLS.</span><span class="sxs-lookup"><span data-stu-id="bfd80-168">Specifies the maximum time to wait for DTLS shutdown completion.</span></span> <span data-ttu-id="bfd80-169">O valor predefinido é de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="bfd80-169">The default value is 5 seconds.</span></span>
