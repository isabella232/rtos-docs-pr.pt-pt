---
title: Capítulo 2 - Instalação e utilização do Azure RTOS NetX Duo BSD
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente BSD Azure RTOS NetX Duo BSD.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 582661bc66c51341fc098de9ff7b6fa2a7d746de
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826155"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-bsd"></a><span data-ttu-id="55450-103">Capítulo 2 - Instalação e utilização do Azure RTOS NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="55450-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo BSD</span></span>

<span data-ttu-id="55450-104">Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente BSD Azure RTOS NetX Duo BSD.</span><span class="sxs-lookup"><span data-stu-id="55450-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo BSD component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="55450-105">Distribuição de Produtos</span><span class="sxs-lookup"><span data-stu-id="55450-105">Product Distribution</span></span>

<span data-ttu-id="55450-106">O Azure RTOS NetX Duo BSD pode ser obtido a partir do nosso repositório de código fonte pública em [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) .</span><span class="sxs-lookup"><span data-stu-id="55450-106">Azure RTOS NetX Duo BSD can be obtained from our public source code repository at [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span></span> <span data-ttu-id="55450-107">O pacote inclui dois ficheiros de origem e um ficheiro PDF que contém este documento, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="55450-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="55450-108">**nxd_bsd.h:** Arquivo de cabeçalho para NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="55450-108">**nxd_bsd.h**: Header file for NetX Duo BSD</span></span>
- <span data-ttu-id="55450-109">**nxd_bsd.c**: Ficheiro C Fonte para NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="55450-109">**nxd_bsd.c**: C Source file for NetX Duo BSD</span></span>
- <span data-ttu-id="55450-110">**nxd_bsd.pdf**: Guia do Utilizador para o Duo BSD da NetX</span><span class="sxs-lookup"><span data-stu-id="55450-110">**nxd_bsd.pdf**: User Guide for NetX Duo BSD</span></span>

<span data-ttu-id="55450-111">Ficheiros de demonstração:</span><span class="sxs-lookup"><span data-stu-id="55450-111">Demo files:</span></span>

- <span data-ttu-id="55450-112">**bsd_demo_udp.c**</span><span class="sxs-lookup"><span data-stu-id="55450-112">**bsd_demo_udp.c**</span></span>
- <span data-ttu-id="55450-113">**bsd_demo_tcp.c**</span><span class="sxs-lookup"><span data-stu-id="55450-113">**bsd_demo_tcp.c**</span></span>
- <span data-ttu-id="55450-114">**bsd_demo_raw.c**</span><span class="sxs-lookup"><span data-stu-id="55450-114">**bsd_demo_raw.c**</span></span>

## <a name="netx-duo-bsd-installation"></a><span data-ttu-id="55450-115">Instalação BSD netx duo</span><span class="sxs-lookup"><span data-stu-id="55450-115">NetX Duo BSD Installation</span></span>

<span data-ttu-id="55450-116">Para utilizar o NetX Duo BSD, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX Duo está instalado.</span><span class="sxs-lookup"><span data-stu-id="55450-116">In order to use NetX Duo BSD the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="55450-117">Por exemplo, se o NetX Duo for instalado no diretório "*\threadx\arm7\green*" então os ficheiros *nxd_bsd.h* e *nxd_bsd.c* devem ser copiados para este diretório.</span><span class="sxs-lookup"><span data-stu-id="55450-117">For example, if NetX Duo is installed in the directory "*\threadx\arm7\green*" then the *nxd_bsd.h* and *nxd_bsd.c* files should be copied into this directory.</span></span>

## <a name="building-the-threadx-and-netx-duo-components-of-a-bsd-application"></a><span data-ttu-id="55450-118">Construção dos componentes ThreadX e NetX Duo de uma aplicação BSD</span><span class="sxs-lookup"><span data-stu-id="55450-118">Building the ThreadX and NetX Duo components of a BSD Application</span></span>

### <a name="threadx"></a><span data-ttu-id="55450-119">ThreadX</span><span class="sxs-lookup"><span data-stu-id="55450-119">ThreadX</span></span>

<span data-ttu-id="55450-120">A biblioteca ThreadX deve definir `bsd_errno` no armazenamento local do fio.</span><span class="sxs-lookup"><span data-stu-id="55450-120">The ThreadX library must define `bsd_errno` in the thread local storage.</span></span> <span data-ttu-id="55450-121">Recomendamos o seguinte procedimento:</span><span class="sxs-lookup"><span data-stu-id="55450-121">We recommend the following procedure:</span></span>

1. <span data-ttu-id="55450-122">Em *tx_port.h,* definir uma das macros TX_THREAD_EXTENSION da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="55450-122">In *tx_port.h*, set one of the TX_THREAD_EXTENSION macros as follows:</span></span>
   - `#define TX_THREAD_EXTENSION_3     int bsd_errno`

1. <span data-ttu-id="55450-123">Reconstruir a biblioteca ThreadX.</span><span class="sxs-lookup"><span data-stu-id="55450-123">Rebuild the ThreadX library.</span></span>

> [!NOTE]
> <span data-ttu-id="55450-124">Se TX_THREAD_EXTENSION_3 já estiver utilizado, o utilizador é livre de utilizar uma das outras macros TX_THREAD_EXTENSION.</span><span class="sxs-lookup"><span data-stu-id="55450-124">If TX_THREAD_EXTENSION_3 is already used, the user is free to use one of the other TX_THREAD_EXTENSION macros.</span></span>

### <a name="netx-duo"></a><span data-ttu-id="55450-125">NetX Duo</span><span class="sxs-lookup"><span data-stu-id="55450-125">NetX Duo</span></span>

<span data-ttu-id="55450-126">Antes de utilizar os Serviços BSD NetX Duo, a biblioteca NetX Duo deve ser construída com NX_ENABLE_EXTENDED_NOTIFY_SUPPORT definida.</span><span class="sxs-lookup"><span data-stu-id="55450-126">Before using NetX Duo BSD Services, the NetX Duo library must be built with NX_ENABLE_EXTENDED_NOTIFY_SUPPORT defined.</span></span> <span data-ttu-id="55450-127">Por defeito não está definido.</span><span class="sxs-lookup"><span data-stu-id="55450-127">By default it is not defined.</span></span> <span data-ttu-id="55450-128">Se as tomadas em bruto BSD forem utilizadas, a biblioteca NetX Duo deve ser construída com NX_ENABLE_IP_RAW_PACKET_FILTER definidas.</span><span class="sxs-lookup"><span data-stu-id="55450-128">If the BSD raw sockets are to be used, the NetX Duo library must be built with NX_ENABLE_IP_RAW_PACKET_FILTER defined.</span></span>

## <a name="using-netx-duo-bsd"></a><span data-ttu-id="55450-129">Usando o Duo BSD netx</span><span class="sxs-lookup"><span data-stu-id="55450-129">Using NetX Duo BSD</span></span>

<span data-ttu-id="55450-130">Um projeto de aplicação NetX Duo BSD deve incluir *nxd_bsd.h* depois de incluir *tx_api.h* e *nx_api.h* para poder utilizar os serviços BSD especificados mais tarde neste guia.</span><span class="sxs-lookup"><span data-stu-id="55450-130">A NetX Duo BSD application project must include *nxd_bsd.h* after it includes *tx_api.h* and *nx_api.h* to be able to use BSD services specified later in this guide.</span></span> <span data-ttu-id="55450-131">O pedido também deve incluir *nxd_bsd.c* no processo de construção.</span><span class="sxs-lookup"><span data-stu-id="55450-131">The application must also include *nxd_bsd.c* in the build process.</span></span> <span data-ttu-id="55450-132">Este ficheiro deve ser compilado da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação.</span><span class="sxs-lookup"><span data-stu-id="55450-132">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="55450-133">Isto é tudo o que é necessário para usar NetX Duo BSD.</span><span class="sxs-lookup"><span data-stu-id="55450-133">This is all that is required to use NetX Duo BSD.</span></span>

<span data-ttu-id="55450-134">Para utilizar os serviços BSD NetX Duo, a aplicação deve criar uma instância IP, criar um conjunto de pacotes para a camada BSD para alocar pacotes a partir, alocar espaço de memória para a pilha interna de fios BSD, e especificar a prioridade do fio BSD interno.</span><span class="sxs-lookup"><span data-stu-id="55450-134">To utilize NetX Duo BSD services, the application must create an IP instance, create a packet pool for the BSD layer to allocate packets from, allocate memory space for the internal BSD thread stack, and specify the priority of the internal BSD thread.</span></span> <span data-ttu-id="55450-135">A camada de BSD é inicializada chamando *bsd_initialize* e passando nos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="55450-135">The BSD layer is initialized by calling *bsd_initialize* and passing in the parameters.</span></span> <span data-ttu-id="55450-136">Isto é demonstrado nos "Pequenos Exemplos" mais tarde neste documento, mas o protótipo é mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="55450-136">This is demonstrated in the "Small Examples" later in this document but the prototype is shown below:</span></span>

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                    *CHAR *bsd_thread_stack_area,
                    *ULONG bsd_thread_stack_size,
                    *UINT bsd_thread_priority*);
```

<span data-ttu-id="55450-137">O default_ip é a instância IP em que a camada de BSD funciona.</span><span class="sxs-lookup"><span data-stu-id="55450-137">The default_ip is the IP instance the BSD layer operates on.</span></span> <span data-ttu-id="55450-138">O default_pool é utilizado pelos serviços da BSD para alocar pacotes a partir de.</span><span class="sxs-lookup"><span data-stu-id="55450-138">The default_pool is used by the BSD services to allocate packets from.</span></span> <span data-ttu-id="55450-139">Os dois parâmetros seguintes: bsd_thread_stack_area, bsd_thread_stack_size define a área de pilha utilizada pelo fio BSD interno, e o último parâmetro, bsd_thread_priority, define a prioridade do fio.</span><span class="sxs-lookup"><span data-stu-id="55450-139">The next two parameters: bsd_thread_stack_area, bsd_thread_stack_size defines the stack area used by the internal BSD thread, and the last parameter, bsd_thread_priority, sets the priority of the thread.</span></span>

## <a name="netx-duo-bsd-raw-socket-support"></a><span data-ttu-id="55450-140">Suporte de tomada bruta netx duo BSD</span><span class="sxs-lookup"><span data-stu-id="55450-140">NetX Duo BSD Raw Socket Support</span></span>

<span data-ttu-id="55450-141">NetX Duo BSD também suporta tomadas brutas.</span><span class="sxs-lookup"><span data-stu-id="55450-141">NetX Duo BSD also supports raw sockets.</span></span> <span data-ttu-id="55450-142">Para utilizar tomadas brutas no NetX Duo BSD, a biblioteca NetX Duo deve ser compilada com NX_ENABLE_IP_RAW_PACKET_FILTER definida.</span><span class="sxs-lookup"><span data-stu-id="55450-142">To use raw sockets in NetX Duo BSD, the NetX Duo library must be compiled with NX_ENABLE_IP_RAW_PACKET_FILTER defined.</span></span> <span data-ttu-id="55450-143">Por defeito não está definido.</span><span class="sxs-lookup"><span data-stu-id="55450-143">By default it is not defined.</span></span> <span data-ttu-id="55450-144">A aplicação deve então permitir o processamento de tomadas em bruto para uma instância IP previamente criada, chamando *nx_ip_raw_packet_enable.*</span><span class="sxs-lookup"><span data-stu-id="55450-144">The application must then enable raw socket processing for a previously created IP instance by calling *nx_ip_raw_packet_enable.*</span></span>

<span data-ttu-id="55450-145">Para criar uma tomada em bruto no NetX Duo BSD, a aplicação utiliza a *tomada* de serviço e especifica a família protocolar, tipo de tomada e protocolo:</span><span class="sxs-lookup"><span data-stu-id="55450-145">To create a raw socket in NetX Duo BSD, the application uses the socket create service *socket* and specifies the protocol family, socket type and protocol:</span></span>

```c
sock_1 = socket(INT protocolFamily, INT socket_type, INT protocol)
```

<span data-ttu-id="55450-146">protocoloAmily é AF_INET para tomadas IPv4, ou AF_INET6 para tomadas IPv6, assumindo que o IPv6 está ativado na instância IP.</span><span class="sxs-lookup"><span data-stu-id="55450-146">protocolFamily is AF_INET for IPv4 sockets, or AF_INET6 for IPv6 sockets, assuming IPv6 is enabled on the IP instance.</span></span> <span data-ttu-id="55450-147">O socket_type tem de ser SOCK_RAW.</span><span class="sxs-lookup"><span data-stu-id="55450-147">The socket_type must be set to SOCK_RAW.</span></span> <span data-ttu-id="55450-148">protocolo é específico de aplicação.</span><span class="sxs-lookup"><span data-stu-id="55450-148">protocol is application specific.</span></span>

<span data-ttu-id="55450-149">Para enviar e receber pacotes crus, bem como fechar uma tomada em bruto, a aplicação normalmente utiliza os mesmos serviços BSD que para uDP, por *exemplo, sendto, recvfrom, select* e *soc_close*.</span><span class="sxs-lookup"><span data-stu-id="55450-149">To send and receive raw packets as well as close a raw socket, the application typically uses the same BSD services as for UDP e.g. *sendto, recvfrom, select* and *soc_close*.</span></span> <span data-ttu-id="55450-150">As tomadas brutas não *suportam* nem aceitam ou *ouvem* os serviços de BSD.</span><span class="sxs-lookup"><span data-stu-id="55450-150">Raw sockets do not support either *accept* or *listen* BSD services.</span></span>

- <span data-ttu-id="55450-151">Por predefinição, os dados brutos do IPv4 recebidos incluem o cabeçalho IPv4.</span><span class="sxs-lookup"><span data-stu-id="55450-151">By default, received IPv4 raw data includes the IPv4 header.</span></span>  <span data-ttu-id="55450-152">Inversamente, os dados brutos recebidos do IPv6 não incluem o cabeçalho IPv6.</span><span class="sxs-lookup"><span data-stu-id="55450-152">Conversely, received IPv6 raw data does not include the IPv6 header.</span></span>

- <span data-ttu-id="55450-153">Por predefinição, ao enviar pacotes IPv6 ou IPv4 brutos, a camada de invólucro BSD adiciona o cabeçalho IPv6 ou IPv4 antes de enviar os dados.</span><span class="sxs-lookup"><span data-stu-id="55450-153">By default, when sending either raw IPv6 or IPv4 packets, the BSD wrapper layer adds the IPv6 or IPv4 header before sending the data.</span></span>

<span data-ttu-id="55450-154">NetX Duo BSD suporta opções adicionais de tomada bruta, incluindo IP_RAW_RX_NO_HEADER, IP_HDRINCL e IP_RAW_IPV6_HDRINCL.</span><span class="sxs-lookup"><span data-stu-id="55450-154">NetX Duo BSD supports additional raw socket options, including IP_RAW_RX_NO_HEADER, IP_HDRINCL and IP_RAW_IPV6_HDRINCL.</span></span>

<span data-ttu-id="55450-155">Se IP_RAW_RX_NO_HEADER estiver definido, o cabeçalho IPv4 é removido de modo a que os dados recebidos não contenham o cabeçalho IPv4, e o comprimento da mensagem relatado não inclua o cabeçalho IPv4.</span><span class="sxs-lookup"><span data-stu-id="55450-155">If IP_RAW_RX_NO_HEADER is set, the IPv4 header is removed so that the received data does not contain the IPv4 header, and the reported message length does not include the IPv4 header.</span></span>  <span data-ttu-id="55450-156">Para as tomadas IPv6, por predefinição a tomada bruta recebe não inclui cabeçalho IPv6, equivalente a ter o IP_RAW_RX_NO_HEADER conjunto de opções.</span><span class="sxs-lookup"><span data-stu-id="55450-156">For IPv6 sockets, by default the raw socket receive does not include IPv6 header, equivalent to having the IP_RAW_RX_NO_HEADER option set.</span></span> <span data-ttu-id="55450-157">A aplicação pode utilizar o serviço *setockopt* para limpar a opção IP_RAW_RX_NO_HEADER, uma vez que a opção IP_RAW_RX_NO_HEADER seja apurada, os dados em bruto do IPv6 recebidos incluem o cabeçalho IPv6, e o comprimento da mensagem relatado inclui o cabeçalho IPv6.</span><span class="sxs-lookup"><span data-stu-id="55450-157">Application may use the *setsockopt* service to clear the IP_RAW_RX_NO_HEADER option, Once the IP_RAW_RX_NO_HEADER option is cleared, the received IPv6 raw data would include the IPv6 header, and the reported message length includes the IPv6 header.</span></span>

<span data-ttu-id="55450-158">Esta opção não tem qualquer efeito sobre os dados transmitidos pelo IPv4 ou IPv6.</span><span class="sxs-lookup"><span data-stu-id="55450-158">This option has no effect on IPv4 or IPv6 transmitted data.</span></span>

<span data-ttu-id="55450-159">Se IP_HDRINCL estiver definido, a aplicação inclui o cabeçalho IPv4 ao enviar dados.</span><span class="sxs-lookup"><span data-stu-id="55450-159">If IP_HDRINCL is set, the application includes the IPv4 header when sending data.</span></span>  <span data-ttu-id="55450-160">Esta opção não tem qualquer efeito na transmissão IPv6 e não é definida por padrão.</span><span class="sxs-lookup"><span data-stu-id="55450-160">This option has no effect on IPv6 transmission and is not defined by default.</span></span> <span data-ttu-id="55450-161">Se IP_RAW_IPV6_HDRINCL estiver definido, a aplicação inclui o cabeçalho IPv6 ao enviar dados.</span><span class="sxs-lookup"><span data-stu-id="55450-161">If IP_RAW_IPV6_HDRINCL is set, the application includes the IPv6 header when sending data.</span></span>  <span data-ttu-id="55450-162">Esta opção não tem qualquer efeito na transmissão IPv4 e não é definida por padrão.</span><span class="sxs-lookup"><span data-stu-id="55450-162">This option has no effect on IPv4 transmission and is not defined by default.</span></span>

<span data-ttu-id="55450-163">IP_HDRINCL e IP_RAW_IPV6_HDRINCL não têm qualquer efeito na receção IPv4 ou IPv6.</span><span class="sxs-lookup"><span data-stu-id="55450-163">IP_HDRINCL and IP_RAW_IPV6_HDRINCL have no effect on IPv4 or IPv6 reception.</span></span>

> [!NOTE]
> <span data-ttu-id="55450-164">A especificação da tomada BSD 4.3 especifica que o núcleo deve copiar o pacote cru para cada tomada receber tampão.</span><span class="sxs-lookup"><span data-stu-id="55450-164">The BSD 4.3 Socket specification specifies that the kernel must copy the raw packet to each socket receive buffer.</span></span> <span data-ttu-id="55450-165">No entanto, no NetX Duo BSD, se várias tomadas forem criadas partilhando o mesmo protocolo, o comportamento é indefinido.</span><span class="sxs-lookup"><span data-stu-id="55450-165">However in NetX Duo BSD, if multiple sockets are created sharing the same protocol, the behavior is undefined.</span></span>

## <a name="netx-duo-bsd-raw-packet-support"></a><span data-ttu-id="55450-166">Suporte ao pacote bruto da dupla Netx BSD</span><span class="sxs-lookup"><span data-stu-id="55450-166">NetX Duo BSD Raw Packet Support</span></span>

<span data-ttu-id="55450-167">Para permitir o suporte de pacotes brutos para PPPoE, o invólucro BSD NetX Duo precisa de ser construído com NX_BSD_RAW_PPPOE_SUPPORT ativado.</span><span class="sxs-lookup"><span data-stu-id="55450-167">To enable the raw packet support for PPPoE, NetX Duo BSD wrapper needs to be built with NX_BSD_RAW_PPPOE_SUPPORT enabled.</span></span>

<span data-ttu-id="55450-168">O seguinte comando cria uma tomada BSD para manusear pacotes crus PPPoE:</span><span class="sxs-lookup"><span data-stu-id="55450-168">The following command creates a BSD socket to handle PPPoE raw packets:</span></span>

```c
Sockfd = socket(AF_PACKET, SOCK_RAW, protocol);
```

<span data-ttu-id="55450-169">A atual implementação do BSD só suporta dois tipos de protocolos em AF_PACKET família</span><span class="sxs-lookup"><span data-stu-id="55450-169">The current BSD implementation only supports two protocol types in AF_PACKET family</span></span>

- <span data-ttu-id="55450-170">`ETHERTYPE_PPPOE_DISC`: Pacotes PPPoE Discovery.</span><span class="sxs-lookup"><span data-stu-id="55450-170">`ETHERTYPE_PPPOE_DISC`: PPPoE Discovery packets.</span></span> <span data-ttu-id="55450-171">No quadro de dados mac, os pacotes Discovery têm o tipo de quadro Ethernet 0x8863.</span><span class="sxs-lookup"><span data-stu-id="55450-171">In the MAC data frame, the Discovery packets have the Ethernet frame type 0x8863.</span></span>

- <span data-ttu-id="55450-172">`ETHERTYPE_PPPOE_SESS`: Pacotes de Sessão de PPP.</span><span class="sxs-lookup"><span data-stu-id="55450-172">`ETHERTYPE_PPPOE_SESS`: PPP Session packets.</span></span> <span data-ttu-id="55450-173">No quadro de dados mac, os pacotes session têm o tipo de quadro Ethernet 0x8864.</span><span class="sxs-lookup"><span data-stu-id="55450-173">In the MAC data frame, the Session packets have the Ethernet frame type 0x8864.</span></span>

<span data-ttu-id="55450-174">A estrutura `sockaddr_ll` é utilizada para especificar parâmetros ao enviar ou receber quadros PPPoE.</span><span class="sxs-lookup"><span data-stu-id="55450-174">The structure `sockaddr_ll` is used to specify parameters when sending or receiving PPPoE frames.</span></span>

<span data-ttu-id="55450-175">`struct sockaddr_ll` é declarado como:</span><span class="sxs-lookup"><span data-stu-id="55450-175">`struct sockaddr_ll` is declared as:</span></span>

```c
struct sockaddr_ll
{
    USHORT  sll_family;     /* Must be AF_PACKET */
    USHORT  sll_protocol;   /* LL frame type */
    INT     sll_ifindex;    /* Interface Index. */
    USHORT  sll_hatype;     /* Header type */
    UCHAR   sll_pkttype;    /* Packet type */
    UCHAR   sll_halen;      /* Length of address */
    UCHAR   sll_addr[8];    /* Physical layer address */
};
```

> [!NOTE]
> <span data-ttu-id="55450-176">Nem todos os campos da estrutura são utilizados por `sendto()` ou `recvfrom()` .</span><span class="sxs-lookup"><span data-stu-id="55450-176">Not every field in the structure is used by `sendto()` or `recvfrom()`.</span></span> <span data-ttu-id="55450-177">Veja a descrição abaixo sobre como configurar os `sockaddr_ll` pacotes PPPoE para envio e receção.</span><span class="sxs-lookup"><span data-stu-id="55450-177">See the description below on how to set up the `sockaddr_ll` for sending and receiving PPPoE packets.</span></span>

<span data-ttu-id="55450-178">A tomada criada no AF_PACKET família pode ser usada para enviar pacotes ppPoE Discovery ou pacotes de sessão de PPP, independentemente do protocolo especificado.</span><span class="sxs-lookup"><span data-stu-id="55450-178">Socket created in the AF_PACKET family can be used to send either PPPoE Discovery packets or PPP session packets, regardless of the protocol specified.</span></span> <span data-ttu-id="55450-179">Ao transmitir um pacote PPPoE, a aplicação deve preparar o tampão que inclui a moldura PPPoE devidamente formatada, incluindo os cabeçalhos MAC (endereço MAC de destino, endereço MAC de origem e tipo de quadro.) O tamanho do tampão inclui o cabeçalho Ethernet de 14 bytes.</span><span class="sxs-lookup"><span data-stu-id="55450-179">When transmitting a PPPoE packet, application must prepare the buffer that includes properly formatted PPPoE frame, including the MAC headers (Destination MAC address, source MAC address, and frame type.) The size of the buffer includes the 14-byte Ethernet header.</span></span>

<span data-ttu-id="55450-180">A `sockaddr_ll` estrutura, a `sll_ifindex` é usada para indicar a interface física a ser usada para o envio deste pacote.</span><span class="sxs-lookup"><span data-stu-id="55450-180">The `sockaddr_ll` struct, the `sll_ifindex` is used to indicate the physical interface to be used for sending this packet.</span></span> <span data-ttu-id="55450-181">O resto dos campos da estrutura não são usados.</span><span class="sxs-lookup"><span data-stu-id="55450-181">The rest of the fields in the structure are not used.</span></span> <span data-ttu-id="55450-182">Os valores definidos para os campos não reutilizados são ignorados pelo processo interno da BSD.</span><span class="sxs-lookup"><span data-stu-id="55450-182">Values set to the unused fields are ignored by the BSD internal process.</span></span>

<span data-ttu-id="55450-183">O seguinte bloco de código ilustra como transmitir um pacote PPPoE:</span><span class="sxs-lookup"><span data-stu-id="55450-183">The following code block illustrates how to transmit a PPPoE packet:</span></span>

```c
struct sockaddr_ll peer_addr;

/* Transmit a PPPoE frame using the primary network interface. */
peer_addr.sll_ifindex = 0;
n = sendto(sockfd, frame, frame_size, 0, (struct
        sockaddr*)&peer_addr, sizeof(peer_addr));
```

<span data-ttu-id="55450-184">O valor de devolução indica o número de bytes transmitidos.</span><span class="sxs-lookup"><span data-stu-id="55450-184">The return value indicates the number of bytes transmitted.</span></span> <span data-ttu-id="55450-185">Uma vez que os pacotes PPPoE são baseados em mensagens, numa transmissão bem sucedida, o número de bytes enviados corresponde ao tamanho do pacote, incluindo o cabeçalho Ethernet de 14 bytes.</span><span class="sxs-lookup"><span data-stu-id="55450-185">Since PPPoE packets are message-based, on a successful transmission, the number of bytes sent matches the size of the packet, including the 14-byte Ethernet header.</span></span>

<span data-ttu-id="55450-186">Os pacotes PPPoE podem ser recebidos utilizando `recvfrom()` .</span><span class="sxs-lookup"><span data-stu-id="55450-186">PPPoE packets can be received using `recvfrom()`.</span></span> <span data-ttu-id="55450-187">O tampão de receção deve ser grande o suficiente para acomodar a mensagem do tamanho Ethernet MTU.</span><span class="sxs-lookup"><span data-stu-id="55450-187">The receive buffer must be big enough to accommodate message of Ethernet MTU size.</span></span> <span data-ttu-id="55450-188">O pacote PPPoE recebido inclui cabeçalho Ethernet de 14 byte.</span><span class="sxs-lookup"><span data-stu-id="55450-188">The received PPPoE packet includes 14-byte Ethernet header.</span></span> <span data-ttu-id="55450-189">Ao receber pacotes PPPoE, os pacotes PPPoE Discovery só podem ser recebidos por tomada criada com protocolo `ETHERTYPE_PPPOE_DISC` .</span><span class="sxs-lookup"><span data-stu-id="55450-189">On receiving PPPoE packets, PPPoE Discovery packets can only be received by socket created with protocol `ETHERTYPE_PPPOE_DISC`.</span></span> <span data-ttu-id="55450-190">Da mesma forma, os pacotes de sessão de PPP só podem ser recebidos por tomada criada com protocolo `ETHERTYPE_PPPOE_SESS` .</span><span class="sxs-lookup"><span data-stu-id="55450-190">Similarly, PPP session packets can only be received by socket created with protocol `ETHERTYPE_PPPOE_SESS`.</span></span> <span data-ttu-id="55450-191">Se forem criadas várias tomadas para o mesmo tipo de protocolo, os pacotes PPPoE que chegam são encaminhados para a tomada criada primeiro.</span><span class="sxs-lookup"><span data-stu-id="55450-191">If multiple sockets are created for the same protocol type, arriving PPPoE packets are forwarded to the socket created first.</span></span> <span data-ttu-id="55450-192">Se a primeira tomada criada para o protocolo estiver fechada, a próxima tomada na ordem de criação é utilizada para receber estes pacotes.</span><span class="sxs-lookup"><span data-stu-id="55450-192">If the first socket created for the protocol is closed, the next socket in the order of creation is used for receiving these packets.</span></span>

<span data-ttu-id="55450-193">Após a ausição de um pacote PPPoE, os seguintes campos na `sockaddr_ll` estrutura são válidos:</span><span class="sxs-lookup"><span data-stu-id="55450-193">After a PPPoE packet is received, the following fields in the `sockaddr_ll` struct are valid:</span></span>
- <span data-ttu-id="55450-194">**sll_family**: Definido pelo BSD interno para ser AF_PACKET</span><span class="sxs-lookup"><span data-stu-id="55450-194">**sll_family**: Set by the BSD internal to be AF_PACKET</span></span>
- <span data-ttu-id="55450-195">**sll_ifindex**: Indica a interface a partir da qual o pacote é recebido</span><span class="sxs-lookup"><span data-stu-id="55450-195">**sll_ifindex**: Indicates the interface from which the packet is received</span></span>
- <span data-ttu-id="55450-196">**sll_protocol**: Definir para o tipo de pacote recebido: `ETHERTYPE_PPPOE_DISC` ou `ETHERTYPE_PPPOE_SESS`</span><span class="sxs-lookup"><span data-stu-id="55450-196">**sll_protocol**: Set to the type of packet received: `ETHERTYPE_PPPOE_DISC` or `ETHERTYPE_PPPOE_SESS`</span></span>

## <a name="eliminating-internal-bsd-thread"></a><span data-ttu-id="55450-197">Eliminação do fio interno da BSD</span><span class="sxs-lookup"><span data-stu-id="55450-197">Eliminating Internal BSD Thread</span></span>

<span data-ttu-id="55450-198">Por predefinição, a BSD utiliza um fio interno para executar parte do seu processamento.</span><span class="sxs-lookup"><span data-stu-id="55450-198">By default, BSD utilizes an internal thread to perform some of its processing.</span></span> <span data-ttu-id="55450-199">Em sistemas com restrições de memória apertadas, o BSD pode ser construído com NX_BSD_TIMEOUT_PROCESS_IN_TIMER definido, que elimina o fio BSD interno e, em vez disso, utiliza um temporizador interno para realizar o mesmo processamento.</span><span class="sxs-lookup"><span data-stu-id="55450-199">In systems with tight memory constraints, BSD can be built with NX_BSD_TIMEOUT_PROCESS_IN_TIMER defined, which eliminates the internal BSD thread and instead uses an internal timer to perform the same processing.</span></span> <span data-ttu-id="55450-200">Isto elimina a memória necessária para o bloco interno de controlo de rosca BSD e para a pilha.</span><span class="sxs-lookup"><span data-stu-id="55450-200">This eliminates the memory required for the internal BSD thread control block and stack.</span></span> <span data-ttu-id="55450-201">No entanto, o processamento global do temporizador é significativamente aumentado e o processamento de BSD também pode executar com uma prioridade mais elevada do que o necessário.</span><span class="sxs-lookup"><span data-stu-id="55450-201">However, overall timer processing is significantly increased and the BSD processing may also execute at a higher priority than needed.</span></span>

<span data-ttu-id="55450-202">Para configurar as tomadas BSD para funcionar no contexto do temporizador ThreadX, defina NX_BSD_TIMEOUT_PROCESS_IN_TIMER em *nxd_bsd.h*.</span><span class="sxs-lookup"><span data-stu-id="55450-202">To configure BSD sockets to run in the ThreadX timer context, define NX_BSD_TIMEOUT_PROCESS_IN_TIMER in *nxd_bsd.h*.</span></span> <span data-ttu-id="55450-203">Se a camada de BSD estiver configurada para executar as tarefas de BSD no contexto do temporizador, na chamada para *bsd_initialize*, os três parâmetros seguintes são ignorados e devem ser definidos como NU:</span><span class="sxs-lookup"><span data-stu-id="55450-203">If the BSD layer is configured to execute the BSD tasks in the timer context, in the call to *bsd_initialize*, the following three parameters are ignored, and should be set to NULL:</span></span>

- <span data-ttu-id="55450-204">**bsd_thread_stack_area**</span><span class="sxs-lookup"><span data-stu-id="55450-204">**bsd_thread_stack_area**</span></span>
- <span data-ttu-id="55450-205">**bsd_thread_stack_size**</span><span class="sxs-lookup"><span data-stu-id="55450-205">**bsd_thread_stack_size**</span></span>
- <span data-ttu-id="55450-206">**bsd_thread_priority**</span><span class="sxs-lookup"><span data-stu-id="55450-206">**bsd_thread_priority**</span></span>

## <a name="netx-duo-bsd-with-dns-support"></a><span data-ttu-id="55450-207">NetX Duo BSD com suporte dns</span><span class="sxs-lookup"><span data-stu-id="55450-207">NetX Duo BSD with DNS Support</span></span>

<span data-ttu-id="55450-208">Se NX_BSD_ENABLE_DNS estiver definido, o NetX Duo BSD pode enviar consultas DNS para obter o nome de anfitrião ou informações IP do anfitrião.</span><span class="sxs-lookup"><span data-stu-id="55450-208">If NX_BSD_ENABLE_DNS is defined, NetX Duo BSD can send DNS queries to obtain hostname or host IP information.</span></span> <span data-ttu-id="55450-209">Esta funcionalidade requer que um Cliente DSNS NetX seja previamente criado utilizando o serviço *nx_dns_create.*</span><span class="sxs-lookup"><span data-stu-id="55450-209">This feature requires a NetX DNS Client to be previously created using the *nx_dns_create* service.</span></span> <span data-ttu-id="55450-210">Um ou mais endereços IP do servidor DNS devem ser registados na instância DNS utilizando o serviço *de nx_dns_server_add* para adicionar endereços de servidor IPv4, ou utilizando o serviço *de nxd_dns_server_add* para adicionar endereços de servidor IPv4 ou IPv6.</span><span class="sxs-lookup"><span data-stu-id="55450-210">One or more known DNS server IP addresses must be registered with the DNS instance using the *nx_dns_server_add* service for adding IPv4 server addresses, or using the *nxd_dns_server_add* service for adding either IPv4 or IPv6 server addresses.</span></span>

<span data-ttu-id="55450-211">Os serviços DNS e a atribuição de memória são utilizados pelos serviços *getaddrinfo* e *getnameinfo:*</span><span class="sxs-lookup"><span data-stu-id="55450-211">DNS services and memory allocation are used by *getaddrinfo* and *getnameinfo* services:</span></span>

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
        const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
        char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

<span data-ttu-id="55450-212">Quando a aplicação BSD ligar para *o getaddrinfo* com um nome de anfitrião, o NetX BSD ligará para qualquer um dos serviços abaixo para obter o endereço IP:</span><span class="sxs-lookup"><span data-stu-id="55450-212">When the BSD application calls *getaddrinfo* with a hostname, NetX BSD will call any of the below services to obtain the IP address:</span></span>

- <span data-ttu-id="55450-213">**nx_dns_ipv4_address_by_name_get**</span><span class="sxs-lookup"><span data-stu-id="55450-213">**nx_dns_ipv4_address_by_name_get**</span></span>
- <span data-ttu-id="55450-214">**nxd_dns_ipv6_address_by_name_get**</span><span class="sxs-lookup"><span data-stu-id="55450-214">**nxd_dns_ipv6_address_by_name_get**</span></span>
- <span data-ttu-id="55450-215">**nx_dns_cname_get**</span><span class="sxs-lookup"><span data-stu-id="55450-215">**nx_dns_cname_get**</span></span>

<span data-ttu-id="55450-216">Para *nx_dns_ipv4_address_by_name_get* e *nxd_dns_ipv6_address_by_name_get,* o NetX BSD utiliza as áreas de memória ipv4_addr_buffer e ipv6_addr_buffer, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="55450-216">For *nx_dns_ipv4_address_by_name_get* and *nxd_dns_ipv6_address_by_name_get*, NetX BSD uses the ipv4_addr_buffer and ipv6_addr_buffer memory areas respectively.</span></span> <span data-ttu-id="55450-217">O tamanho destes tampão é definido por (NX_BSD_IPV4_ADDR_PER_HOST \* 4) e (NX_BSD_IPV6_ADDR_PER_HOST \* 16) respectivamente.</span><span class="sxs-lookup"><span data-stu-id="55450-217">The size of these buffers are defined by (NX_BSD_IPV4_ADDR_PER_HOST \* 4) and (NX_BSD_IPV6_ADDR_PER_HOST \* 16) respectively.</span></span>

<span data-ttu-id="55450-218">Para obter informações de endereços do *getaddrinfo,* o NetX BSD utiliza a tabela de memórias do bloco ThreadX nx_bsd_addrinfo_pool_memory, cuja área de memória é definida por outro conjunto de opções configuráveis, NX_BSD_IPV4_ADDR_MAX_NUM e NX_BSD_IPV6_ADDR_MAX_NUM.</span><span class="sxs-lookup"><span data-stu-id="55450-218">For returning address information from *getaddrinfo*, NetX BSD uses the ThreadX block memory table nx_bsd_addrinfo_pool_memory, whose memory area is defined by another set of configurable options, NX_BSD_IPV4_ADDR_MAX_NUM and NX_BSD_IPV6_ADDR_MAX_NUM.</span></span>

<span data-ttu-id="55450-219">Consulte **as Opções gerais de Configuração** para obter mais detalhes sobre as opções de configuração acima.</span><span class="sxs-lookup"><span data-stu-id="55450-219">See **General Configuration Options** for more details on the above configuration options.</span></span>

<span data-ttu-id="55450-220">Além disso, se NX_DNS_ENABLE_EXTENDED_RR_TYPES estiver definido, e a entrada do anfitrião for um nome canónico, o NetX Duo BSD irá alocar a memória dinamicamente a partir de um bloco de blocos anteriormente criado '_nx_bsd_cname_block_pool</span><span class="sxs-lookup"><span data-stu-id="55450-220">Additionally, if NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, and the host input is a canonical name, NetX Duo BSD will allocate memory dynamically from a previously created block pool \`_nx_bsd_cname_block_pool</span></span>

> [!NOTE]
> <span data-ttu-id="55450-221">Depois de chamar *getaddrinfo,* a aplicação BSD é responsável por libertar a memória apontada pelo argumento res de volta à mesa de blocos usando o serviço *freeaddrinfo.*</span><span class="sxs-lookup"><span data-stu-id="55450-221">After calling *getaddrinfo* the BSD application is responsible for releasing the memory pointed to by the res argument back to the block table using the *freeaddrinfo* service.</span></span>

## <a name="netx-duo-bsd-limitations"></a><span data-ttu-id="55450-222">NetX Duo BSD Limitações</span><span class="sxs-lookup"><span data-stu-id="55450-222">NetX Duo BSD Limitations</span></span>

<span data-ttu-id="55450-223">Devido a problemas de desempenho e arquitetura, o NetX Duo BSD não suporta todas as funcionalidades da tomada BSD 4.3:</span><span class="sxs-lookup"><span data-stu-id="55450-223">Due to performance and architecture issues, NetX Duo BSD does not support all the BSD 4.3 socket features:</span></span>

<span data-ttu-id="55450-224">As bandeiras do INT não são suportadas para *envio, recv, envio* e *recv de* chamadas.</span><span class="sxs-lookup"><span data-stu-id="55450-224">INT flags are not supported for *send, recv, sendto* and *recvfrom* calls.</span></span>

## <a name="general-configuration-options"></a><span data-ttu-id="55450-225">Opções de Configuração Geral</span><span class="sxs-lookup"><span data-stu-id="55450-225">General Configuration Options</span></span>

<span data-ttu-id="55450-226">As opções configuráveis do utilizador em *nxd_bsd.h* permitem que a aplicação afina as tomadas BSD NetX Duo para os seus requisitos específicos de aplicação.</span><span class="sxs-lookup"><span data-stu-id="55450-226">User configurable options in *nxd_bsd.h* allow the application to fine tune NetX Duo BSD sockets for its particular application requirements.</span></span>

<span data-ttu-id="55450-227">Segue-se a lista de opções configuráveis que são definidas no momento da compilação:</span><span class="sxs-lookup"><span data-stu-id="55450-227">The following is the list of configurable options that are set at compile time:</span></span>

- <span data-ttu-id="55450-228">**NX_BSD_TCP_WINDOW**: Utilizado na tomada TCP cria chamadas.</span><span class="sxs-lookup"><span data-stu-id="55450-228">**NX_BSD_TCP_WINDOW**: Used in TCP socket create calls.</span></span> <span data-ttu-id="55450-229">64k é o tamanho típico da janela para 100Mb Ethernet.</span><span class="sxs-lookup"><span data-stu-id="55450-229">64k is typical window size for 100Mb Ethernet.</span></span> <span data-ttu-id="55450-230">O valor predefinido é 65535.</span><span class="sxs-lookup"><span data-stu-id="55450-230">The default value is 65535.</span></span>

- <span data-ttu-id="55450-231">**NX_BSD_SOCKFD_START**: Este é o índice lógico para o valor de partida do ficheiro de ficha BSD.</span><span class="sxs-lookup"><span data-stu-id="55450-231">**NX_BSD_SOCKFD_START**: This is the logical index for the BSD socket file descriptor start value.</span></span> <span data-ttu-id="55450-232">Por padrão, esta opção é 32.</span><span class="sxs-lookup"><span data-stu-id="55450-232">By default this option is 32.</span></span>

- <span data-ttu-id="55450-233">**NX_BSD_MAX_SOCKETS**: Especifica o número máximo de tomadas totais disponíveis na camada BSD e deve ser um múltiplo de 32.</span><span class="sxs-lookup"><span data-stu-id="55450-233">**NX_BSD_MAX_SOCKETS**: Specifies the maximum number of total sockets available in the BSD layer and must be a multiple of 32.</span></span> <span data-ttu-id="55450-234">O valor está em incumprimento para 32.</span><span class="sxs-lookup"><span data-stu-id="55450-234">The value is defaulted to 32.</span></span>

- <span data-ttu-id="55450-235">**NX_BSD_SOCKET_QUEUE_MAX**: Especifica o número máximo de pacotes UDP armazenados na fila da tomada de receção.</span><span class="sxs-lookup"><span data-stu-id="55450-235">**NX_BSD_SOCKET_QUEUE_MAX**: Specifies the maximum number of UDP packets stored on the receive socket queue.</span></span> <span data-ttu-id="55450-236">O valor está em incumprimento a 5.</span><span class="sxs-lookup"><span data-stu-id="55450-236">The value is defaulted to 5.</span></span>

- <span data-ttu-id="55450-237">**NX_BSD_MAX_LISTEN_BACKLOG**: Isto especifica o tamanho da fila de escuta ('backlog') para as tomadas BSD TCP.</span><span class="sxs-lookup"><span data-stu-id="55450-237">**NX_BSD_MAX_LISTEN_BACKLOG**: This specifies the size of the listen queue ('backlog') for BSD TCP sockets.</span></span> <span data-ttu-id="55450-238">O valor predefinido é 5.</span><span class="sxs-lookup"><span data-stu-id="55450-238">The default value is 5.</span></span>

- <span data-ttu-id="55450-239">**NX_MICROSECOND_PER_CPU_TICK**: Especifica o número de microsegundos por cronoça do temporizador do programador.</span><span class="sxs-lookup"><span data-stu-id="55450-239">**NX_MICROSECOND_PER_CPU_TICK**: Specifies the number of microseconds per scheduler timer tick.</span></span>

- <span data-ttu-id="55450-240">**NX_BSD_TIMEOUT**: Especifica o tempo limite nos tiques temporais nas chamadas internas netx duo exigidas pela BSD.</span><span class="sxs-lookup"><span data-stu-id="55450-240">**NX_BSD_TIMEOUT**: Specifies the timeout in timer ticks on NetX Duo internal calls required by BSD.</span></span> <span data-ttu-id="55450-241">O valor predefinido é (20\* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="55450-241">The default value is (20 \* NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="55450-242">**NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: Especifica o tempo limite no temporizador na chamada de desconexão NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="55450-242">**NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: Specifies the timeout in timer ticks on NetX Duo disconnect call.</span></span> <span data-ttu-id="55450-243">O valor predefinido é 1.</span><span class="sxs-lookup"><span data-stu-id="55450-243">The default value is 1.</span></span>

- <span data-ttu-id="55450-244">**NX_BSD_PRINT_ERRORS**: Se for definido, a devolução do estado de erro de uma função BSD devolve um número de linha e um tipo de erro, por exemplo, NX_SOC_ERROR onde ocorre o erro.</span><span class="sxs-lookup"><span data-stu-id="55450-244">**NX_BSD_PRINT_ERRORS**: If set, the error status return of a BSD function returns a line number and type of error e.g. NX_SOC_ERROR where the error occurs.</span></span> <span data-ttu-id="55450-245">Isto requer que o desenvolvedor de aplicações defina a saída de depurar.</span><span class="sxs-lookup"><span data-stu-id="55450-245">This requires the application developer to define the debug output.</span></span> <span data-ttu-id="55450-246">A definição predefinida é desativada e nenhuma saída de depuração é especificada em *nxd_bsd.h*.</span><span class="sxs-lookup"><span data-stu-id="55450-246">The default setting is disabled and no debug output is specified in *nxd_bsd.h*.</span></span>

- <span data-ttu-id="55450-247">**NX_BSD_TIMER_RATE**: Intervalo após o qual a tarefa do temporizador periódico BSD é executado.</span><span class="sxs-lookup"><span data-stu-id="55450-247">**NX_BSD_TIMER_RATE**: Interval after which BSD periodic timer task runs.</span></span> <span data-ttu-id="55450-248">O valor predefinido é de 1 segundo (1 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="55450-248">The default value is 1 second (1 \* NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="55450-249">**NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: Se for definida, esta opção permite que o processo de tempo limite de BSD seja executado no contexto do temporizador do sistema.</span><span class="sxs-lookup"><span data-stu-id="55450-249">**NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: If set, this option allows the BSD timeout process to execute in the system timer context.</span></span> <span data-ttu-id="55450-250">O comportamento predefinido é desativado.</span><span class="sxs-lookup"><span data-stu-id="55450-250">The default behavior is disabled.</span></span> <span data-ttu-id="55450-251">Esta característica é descrita mais detalhadamente no capítulo 2 "Instalação e Utilização do Duo BSD NetX".</span><span class="sxs-lookup"><span data-stu-id="55450-251">This feature is described in more detail in Chapter 2 "Installation and Use of NetX Duo BSD".</span></span>

- <span data-ttu-id="55450-252">**NX_BSD_RAW_PPPOE_SUPPORT**: Ativar o suporte ao pacote cru ppPoE.</span><span class="sxs-lookup"><span data-stu-id="55450-252">**NX_BSD_RAW_PPPOE_SUPPORT**: Enable PPPoE raw packet support.</span></span> <span data-ttu-id="55450-253">Por padrão, esta opção não está ativada.</span><span class="sxs-lookup"><span data-stu-id="55450-253">By default this option is not enabled.</span></span>

- <span data-ttu-id="55450-254">**NX_BSD_ENABLE_DNS**: Se estiver ativado, o NetX Duo BSD enviará uma consulta DNS para um nome de anfitrião ou endereço IP anfitrião.</span><span class="sxs-lookup"><span data-stu-id="55450-254">**NX_BSD_ENABLE_DNS**: If enabled, NetX Duo BSD will send a DNS query for a hostname or host IP address.</span></span> <span data-ttu-id="55450-255">Requer que uma instância do Cliente DNS seja previamente criada e iniciada.</span><span class="sxs-lookup"><span data-stu-id="55450-255">Requires a DNS Client instance to be previously created and started.</span></span> <span data-ttu-id="55450-256">Por predefinição, não está ativado.</span><span class="sxs-lookup"><span data-stu-id="55450-256">By default it is not enabled.</span></span>

- <span data-ttu-id="55450-257">**NX_BSD_SOCKET_RAW_PROTOCOL_TABLE_SIZE**: Define o tamanho da tabela de tomadas em bruto.</span><span class="sxs-lookup"><span data-stu-id="55450-257">**NX_BSD_SOCKET_RAW_PROTOCOL_TABLE_SIZE**: Defines the size of the raw socket table.</span></span> <span data-ttu-id="55450-258">O valor deve ser um poder de dois.</span><span class="sxs-lookup"><span data-stu-id="55450-258">The value must be a power of two.</span></span> <span data-ttu-id="55450-259">NetX BSD cria uma série de tomadas de tipo NX_BSD_SOCKETS para envio e receção de pacotes crus.</span><span class="sxs-lookup"><span data-stu-id="55450-259">NetX BSD creates an array of sockets of type NX_BSD_SOCKETS for sending and receiving raw packets.</span></span> <span data-ttu-id="55450-260">NX_ENABLE_IP_RAW_PACKET_FILTER deve ser ativado.</span><span class="sxs-lookup"><span data-stu-id="55450-260">NX_ENABLE_IP_RAW_PACKET_FILTER must be enabled.</span></span> <span data-ttu-id="55450-261">Por defeito é 32.</span><span class="sxs-lookup"><span data-stu-id="55450-261">By default it is 32.</span></span>

- <span data-ttu-id="55450-262">**NX_BSD_IPV4_ADDR_MAX_NUM**: Número máximo de endereços IPv4 devolvidos por *getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="55450-262">**NX_BSD_IPV4_ADDR_MAX_NUM**: Maximum number of IPv4 addresses returned by *getaddrinfo*.</span></span> <span data-ttu-id="55450-263">Isto juntamente com NX_BSD_IPV6_ADDR_MAX_NUM define o tamanho do pool de blocos BSD NetX nx_bsd_addrinfo_block_pool para alocar a memória dinamicamente para endereçar o armazenamento de informação em *getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="55450-263">This along with NX_BSD_IPV6_ADDR_MAX_NUM defines the size of the NetX BSD block pool nx_bsd_addrinfo_block_pool for dynamically allocating memory to address information storage in *getaddrinfo*.</span></span> <span data-ttu-id="55450-264">O valor predefinido é 5.</span><span class="sxs-lookup"><span data-stu-id="55450-264">The default value is 5.</span></span>

- <span data-ttu-id="55450-265">**NX_BSD_IPV6_ADDR_MAX_NUM**: Número máximo de endereços IPv6 devolvidos por *getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="55450-265">**NX_BSD_IPV6_ADDR_MAX_NUM**: Maximum number of IPv6 addresses returned by *getaddrinfo*.</span></span> <span data-ttu-id="55450-266">Isto juntamente com NX_BSD_IPV4_ADDR_MAX_NUM define o tamanho do conjunto de blocos BSD NetX nx_bsd_addrinfo_block_pool para alocar a memória dinamicamente para endereçar o armazenamento de informação em *getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="55450-266">This along with NX_BSD_IPV4_ADDR_MAX_NUM defines the size of the NetX BSD block pool nx_bsd_addrinfo_block_pool for dynamically allocating memory to address information storage in *getaddrinfo*.</span></span>

- <span data-ttu-id="55450-267">**NX_BSD_IPV4_ADDR_PER_HOST**: Define os endereços IPv4 máximos armazenados por consulta DNS.</span><span class="sxs-lookup"><span data-stu-id="55450-267">**NX_BSD_IPV4_ADDR_PER_HOST**: Defines maximum IPv4 addresses stored per DNS query.</span></span> <span data-ttu-id="55450-268">O valor predefinido é 5.</span><span class="sxs-lookup"><span data-stu-id="55450-268">The default value is 5.</span></span>

- <span data-ttu-id="55450-269">**NX_BSD_IPV6_ADDR_PER_HOST**: Define os endereços IPv6 máximos armazenados por consulta DNS.</span><span class="sxs-lookup"><span data-stu-id="55450-269">**NX_BSD_IPV6_ADDR_PER_HOST**: Defines maximum IPv6 addresses stored per DNS query.</span></span> <span data-ttu-id="55450-270">O valor predefinido é 2.</span><span class="sxs-lookup"><span data-stu-id="55450-270">The default value is 2.</span></span>

## <a name="bsd-socket-options"></a><span data-ttu-id="55450-271">Opções de tomada BSD</span><span class="sxs-lookup"><span data-stu-id="55450-271">BSD Socket Options</span></span>

<span data-ttu-id="55450-272">A seguinte lista de opções de tomada BSD NetX Duo pode ser ativada (ou desativada) no tempo de execução numa base por tomada utilizando o serviço *setsockopt:*</span><span class="sxs-lookup"><span data-stu-id="55450-272">The following list of NetX Duo BSD socket options can be enabled (or disabled) at run time on a per socket basis using the *setsockopt* service:</span></span>

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, 
                const void *option_value, INT option_length);
```

<span data-ttu-id="55450-273">Há duas configurações diferentes para option_level.</span><span class="sxs-lookup"><span data-stu-id="55450-273">There are two different settings for option_level.</span></span>

<span data-ttu-id="55450-274">O primeiro tipo de opções de tomada de tempo de funcionamento é SOL_SOCKET para opções de nível de tomada.</span><span class="sxs-lookup"><span data-stu-id="55450-274">The first type of run time socket options is SOL_SOCKET for socket level options.</span></span> <span data-ttu-id="55450-275">Para ativar uma opção de nível de tomada, ligue *para option_level* definido para SOL_SOCKET e option_name definido para a opção específica, por exemplo, SO_BROADCAST *.*</span><span class="sxs-lookup"><span data-stu-id="55450-275">To enable a socket level option, call *setsockopt* with option_level set to SOL_SOCKET and option_name set to the specific option e.g. SO_BROADCAST *.*</span></span> <span data-ttu-id="55450-276">Para recuperar uma definição de opção, *ligue* para o option_name com option_level novamente definido para SOL_SOCKET.</span><span class="sxs-lookup"><span data-stu-id="55450-276">To retrieve an option setting, call *getsockopt* for the option_name with option_level again set to SOL_SOCKET.</span></span>

<span data-ttu-id="55450-277">A lista das opções de nível de tomada de tempo de funcionamento é mostrada abaixo.</span><span class="sxs-lookup"><span data-stu-id="55450-277">The list of run time socket level options is shown below.</span></span>

- <span data-ttu-id="55450-278">**SO_BROADCAST**: Se estiver definido, isto permite o envio e receção de pacotes de transmissão a partir de tomadas Netx.</span><span class="sxs-lookup"><span data-stu-id="55450-278">**SO_BROADCAST**:  If set, this enables sending and receiving broadcast packets from Netx sockets.</span></span> <span data-ttu-id="55450-279">Este é o comportamento padrão para o NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="55450-279">This is the default behavior for NetX Duo.</span></span> <span data-ttu-id="55450-280">Todas as tomadas têm esta capacidade.</span><span class="sxs-lookup"><span data-stu-id="55450-280">All sockets have this capability.</span></span>

- <span data-ttu-id="55450-281">**SO_ERROR**: Utilizado para obter o estado da tomada no funcionamento anterior da tomada da tomada especificada, utilizando o serviço *getsockopt.*</span><span class="sxs-lookup"><span data-stu-id="55450-281">**SO_ERROR**:  Used to obtain socket status on the previous socket operation of the specified socket, using the *getsockopt* service.</span></span> <span data-ttu-id="55450-282">Todas as tomadas têm esta capacidade.</span><span class="sxs-lookup"><span data-stu-id="55450-282">All sockets have this capability.</span></span>

- <span data-ttu-id="55450-283">**SO_KEEPALIVE**: Se estiver definido, isto permite a funcionalidade TCP Keep Alive.</span><span class="sxs-lookup"><span data-stu-id="55450-283">**SO_KEEPALIVE**:  If set, this enables the TCP Keep Alive feature.</span></span> <span data-ttu-id="55450-284">Isto requer que a biblioteca NetX Duo seja construída com NX_TCP_ENABLE_KEEPALIVE definida em *nx_user.h*.</span><span class="sxs-lookup"><span data-stu-id="55450-284">This requires the NetX Duo library to be built with NX_TCP_ENABLE_KEEPALIVE defined in *nx_user.h*.</span></span> <span data-ttu-id="55450-285">Por predefinição, esta função está desativada.</span><span class="sxs-lookup"><span data-stu-id="55450-285">By default this feature is disabled.</span></span>

- <span data-ttu-id="55450-286">**SO_RCVTIMEO**: Isto define a opção de espera em segundos para receber pacotes nas tomadas BSD NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="55450-286">**SO_RCVTIMEO**:  This sets the wait option in seconds for receiving packets on NetX Duo BSD sockets.</span></span> <span data-ttu-id="55450-287">O valor predefinido é o NX_WAIT_FOREVER (0xFFFFFFFF) ou, se não estiver ativado o não bloqueio, NX_NO_WAIT (0x0).</span><span class="sxs-lookup"><span data-stu-id="55450-287">The default value is the NX_WAIT_FOREVER (0xFFFFFFFF) or, if non-blocking is enabled, NX_NO_WAIT (0x0).</span></span>

- <span data-ttu-id="55450-288">**SO_RCVBUF**: Isto define o tamanho da janela da tomada TCP.</span><span class="sxs-lookup"><span data-stu-id="55450-288">**SO_RCVBUF**:  This sets the window size of the TCP socket.</span></span> <span data-ttu-id="55450-289">O valor predefinido, NX_BSD_TCP_WINDOW, está definido para 64k para tomadas BSD TCP.</span><span class="sxs-lookup"><span data-stu-id="55450-289">The default value, NX_BSD_TCP_WINDOW, is set to 64k for BSD TCP sockets.</span></span> <span data-ttu-id="55450-290">Para definir o tamanho acima de 65535 requer que a biblioteca NetX Duo seja construída com o NX_TCP_ENABLE_WINDOW_SCALING ser definida.</span><span class="sxs-lookup"><span data-stu-id="55450-290">To set the size over 65535 requires the NetX Duo library to be built with the NX_TCP_ENABLE_WINDOW_SCALING be defined.</span></span>

- <span data-ttu-id="55450-291">**SO_REUSEADDR**: Se estiver definido, isto permite que várias tomadas sejam mapeadas para uma porta.</span><span class="sxs-lookup"><span data-stu-id="55450-291">**SO_REUSEADDR**:  If set, this enables multiple sockets to be mapped to one port.</span></span> <span data-ttu-id="55450-292">A utilização típica é para a tomada do Servidor TCP.</span><span class="sxs-lookup"><span data-stu-id="55450-292">The typical usage is for the TCP Server socket.</span></span> <span data-ttu-id="55450-293">Este é o comportamento padrão das tomadas NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="55450-293">This is the default behavior of NetX Duo sockets.</span></span>

<span data-ttu-id="55450-294">O segundo tipo de opções de tomada de tempo de funcionamento é o nível de opção IP.</span><span class="sxs-lookup"><span data-stu-id="55450-294">The second type of run time socket options is the IP option level.</span></span> <span data-ttu-id="55450-295">Para ativar uma opção de nível IP, ligue *para os conjuntos* de chamadas com option_level definidos para IP_PROTO e option_name definidos para a opção, por exemplo, IP_MULTICAST_TTL *.*</span><span class="sxs-lookup"><span data-stu-id="55450-295">To enable an IP level option, call *setsockopt* with option_level set to IP_PROTO and option_name set to the option e.g. IP_MULTICAST_TTL *.*</span></span> <span data-ttu-id="55450-296">Para recuperar uma definição de opção, *ligue* para o option_name com option_level novamente definido para IP_PROTO.</span><span class="sxs-lookup"><span data-stu-id="55450-296">To retrieve an option setting, call *getsockopt* for the option_name with option_level again set to IP_PROTO.</span></span>

<span data-ttu-id="55450-297">A lista de opções de nível IP de tempo de execução é mostrada abaixo.</span><span class="sxs-lookup"><span data-stu-id="55450-297">The list of run time IP level options is shown below.</span></span>

- <span data-ttu-id="55450-298">**IP_MULTICAST_TTL**: Este define o tempo de viver para tomadas UDP.</span><span class="sxs-lookup"><span data-stu-id="55450-298">**IP_MULTICAST_TTL**:  This sets the time to live for UDP sockets.</span></span> <span data-ttu-id="55450-299">O valor predefinido é NX_IP_TIME_TO_LIVE (0x80) quando a tomada é criada.</span><span class="sxs-lookup"><span data-stu-id="55450-299">The default value is NX_IP_TIME_TO_LIVE (0x80) when the socket is created.</span></span> <span data-ttu-id="55450-300">Este valor pode ser ultrapassado chamando *setsockopt* com esta opção de tomada.</span><span class="sxs-lookup"><span data-stu-id="55450-300">This value can be overridden by calling *setsockopt* with this socket option.</span></span>

- <span data-ttu-id="55450-301">**IP_RAW_IPV6_HDRINCL**: Se esta opção for definida, o pedido de chamada deve anexar um cabeçalho IPv6 e opcionalmente cabeçalhos de aplicação aos dados transmitidos em tomadas IPv6 em bruto criadas pela BSD.</span><span class="sxs-lookup"><span data-stu-id="55450-301">**IP_RAW_IPV6_HDRINCL**:  If this option is set, the calling application must append an IPv6 header and optionally application headers to data being transmitted on raw IPv6 sockets created by BSD.</span></span> <span data-ttu-id="55450-302">Para utilizar esta opção, o processamento da tomada em bruto deve ser ativado na tarefa IP.</span><span class="sxs-lookup"><span data-stu-id="55450-302">To use this option, raw socket processing must be enabled on the IP task.</span></span>

- <span data-ttu-id="55450-303">**IP_ADD_MEMBERSHIP**: Se estiver definido, esta opção permite que a tomada BSD (se aplica apenas às tomadas UDP) se junte ao grupo IGMP especificado.</span><span class="sxs-lookup"><span data-stu-id="55450-303">**IP_ADD_MEMBERSHIP**:  If set, this options enables the BSD socket (applies only to UDP sockets) to join the specified IGMP group.</span></span>

- <span data-ttu-id="55450-304">**IP_DROP_MEMBERSHIP**: Se estiver definido, esta opção permite que a tomada BSD (se aplica apenas às tomadas UDP) saia do grupo IGMP especificado.</span><span class="sxs-lookup"><span data-stu-id="55450-304">**IP_DROP_MEMBERSHIP**:  If set, this options enables the BSD socket (applies only to UDP sockets) to leave the specified IGMP group.</span></span>

- <span data-ttu-id="55450-305">**IP_HDRINCL**: Se esta opção for definida, a aplicação de chamada deve anexar o cabeçalho IP e opcionalmente os cabeçalhos de aplicação aos dados transmitidos em tomadas IPv4 em bruto criadas em BSD.</span><span class="sxs-lookup"><span data-stu-id="55450-305">**IP_HDRINCL**:  If this option is set, the calling application must append the IP header and optionally application headers to data being transmitted on raw IPv4 sockets created in BSD.</span></span> <span data-ttu-id="55450-306">Para utilizar esta opção, o processamento da tomada em bruto deve ser ativado na tarefa IP.</span><span class="sxs-lookup"><span data-stu-id="55450-306">To use this option, raw socket processing must be enabled on the IP task.</span></span>

- <span data-ttu-id="55450-307">**IP_RAW_RX_NO_HEADER**: Se estiver limpo, o cabeçalho IPv6 é incluído com os dados recebidos para tomadas IPv6 em bruto criadas em BSD.</span><span class="sxs-lookup"><span data-stu-id="55450-307">**IP_RAW_RX_NO_HEADER**:  If cleared, the IPv6 header is included with the received data for raw IPv6 sockets created in BSD.</span></span> <span data-ttu-id="55450-308">Os cabeçalhos IPv6 são removidos por padrão em tomadas IPv6 em bruto BSD, e o comprimento do pacote não inclui o cabeçalho IPv6.</span><span class="sxs-lookup"><span data-stu-id="55450-308">IPv6 headers are removed by default in BSD raw IPv6 sockets, and the packet length does not include the IPv6 header.</span></span>

<span data-ttu-id="55450-309">Se for definido, o cabeçalho IPv4 é removido dos dados recebidos em tomadas em bruto de BSD do tipo IPv4.</span><span class="sxs-lookup"><span data-stu-id="55450-309">If set, the IPv4 header is removed from received data on BSD raw sockets of type IPv4.</span></span> <span data-ttu-id="55450-310">Os cabeçalhos IPv4 são incluídos por predefinição nas tomadas IPv4 em bruto da BSD e o comprimento do pacote inclui o cabeçalho IPv4.</span><span class="sxs-lookup"><span data-stu-id="55450-310">IPv4 headers are included by default in BSD raw IPv4 sockets and packet length includes the IPv4 header.</span></span>

<span data-ttu-id="55450-311">Esta opção não tem qualquer efeito nos dados de transmissão do IPv4 ou do IPv6.</span><span class="sxs-lookup"><span data-stu-id="55450-311">This option has no effect on either IPv4 or IPv6 transmission data.</span></span>

## <a name="small-ipv4-example"></a><span data-ttu-id="55450-312">Pequeno Exemplo IPv4</span><span class="sxs-lookup"><span data-stu-id="55450-312">Small IPv4 Example</span></span>

<span data-ttu-id="55450-313">Um exemplo de como utilizar os serviços BSD NetX Duo para redes IPv4 é descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="55450-313">An example of how to use NetX Duo BSD services for IPv4 networks is described below.</span></span> <span data-ttu-id="55450-314">Neste exemplo, o ficheiro incluído *nxd_bsd.h* é trazido na linha 8.</span><span class="sxs-lookup"><span data-stu-id="55450-314">In this example, the include file *nxd_bsd.h* is brought in at line 8.</span></span> <span data-ttu-id="55450-315">Em seguida, a instância IP *bsd_ip* e *pacotes bsd_pool* são criados como variáveis globais nas linhas 20 e 21.</span><span class="sxs-lookup"><span data-stu-id="55450-315">Next, the IP instance *bsd_ip* and packet pool *bsd_pool* are created as global variables at line 20 and 21.</span></span> <span data-ttu-id="55450-316">Note que esta demonstração utiliza um controlador de rede ram (virtual),*_nx_ram_network_driver*.</span><span class="sxs-lookup"><span data-stu-id="55450-316">Note that this demo uses a ram (virtual) network driver *, _nx_ram_network_driver*.</span></span> <span data-ttu-id="55450-317">O cliente e o servidor partilharão o mesmo endereço IP numa única instância IP neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="55450-317">The client and server will share the same IP address on single IP instance in this example.</span></span>

<span data-ttu-id="55450-318">Os fios do cliente e do servidor são criados nas linhas 62 e 68.</span><span class="sxs-lookup"><span data-stu-id="55450-318">The client and server threads are created on lines 62 and 68.</span></span> <span data-ttu-id="55450-319">O pacote BSD para transmissão de pacotes é criado na linha 78 e usado na criação de instância IP na linha 87.</span><span class="sxs-lookup"><span data-stu-id="55450-319">The BSD packet pool for transmitting packets is created on line 78 and used in the IP instance creation on line 87.</span></span> <span data-ttu-id="55450-320">Note que a tarefa de linha IP é dada prioridade 1 na *chamada nx_ip_create.*</span><span class="sxs-lookup"><span data-stu-id="55450-320">Note that the IP thread task is given priority 1 in the *nx_ip_create* call.</span></span> <span data-ttu-id="55450-321">Este fio deve ser a tarefa de maior prioridade definida no programa para um desempenho netx ideal.</span><span class="sxs-lookup"><span data-stu-id="55450-321">This thread should be the highest priority task defined in the program for optimal NetX performance.</span></span>

<span data-ttu-id="55450-322">A instância IP está ativada para os serviços ARP e TCP nas linhas 88 e 110, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="55450-322">The IP instance is enabled for ARP and TCP services on lines 88 and 110 respectively.</span></span> <span data-ttu-id="55450-323">O último requisito antes de os serviços BSD poderem ser utilizados é chamar *bsd_initialize* on line 120 para configurar todas as estruturas de dados e recursos NetX e ThreadX necessários pela BSD.</span><span class="sxs-lookup"><span data-stu-id="55450-323">The last requirement before BSD services can be used is to call *bsd_initialize* on line 120 to set up all data structures and NetX and ThreadX resources needed by BSD.</span></span>

<span data-ttu-id="55450-324">A função de entrada de fio do servidor é definida em seguida.</span><span class="sxs-lookup"><span data-stu-id="55450-324">The server thread entry function is defined next.</span></span> <span data-ttu-id="55450-325">A tomada BSD TCP é criada na linha 149.</span><span class="sxs-lookup"><span data-stu-id="55450-325">The BSD TCP socket is created on line 149.</span></span> <span data-ttu-id="55450-326">O endereço IP do servidor e a porta estão definidos nas linhas 160-163.</span><span class="sxs-lookup"><span data-stu-id="55450-326">The server IP address and port are set on lines 160-163.</span></span> <span data-ttu-id="55450-327">Note a utilização do hospedeiro para a rede byte macros *htonl* e *htons aplicados* no endereço IP e na porta.</span><span class="sxs-lookup"><span data-stu-id="55450-327">Note the use of host to network byte order macros *htonl* and *htons* applied to the IP address and port.</span></span> <span data-ttu-id="55450-328">Isto está em conformidade com a especificação da tomada BSD que os dados de múltiplos bytes são submetidos aos serviços BSD em ordem byte de rede.</span><span class="sxs-lookup"><span data-stu-id="55450-328">This is in compliance with BSD socket specification that multi byte data is submitted to the BSD services in network byte order.</span></span>

<span data-ttu-id="55450-329">Em seguida, a tomada do servidor principal está ligada à porta utilizando o serviço *de ligação* na linha 166.</span><span class="sxs-lookup"><span data-stu-id="55450-329">Next, the master server socket is bound to the port using the *bind* service on line 166.</span></span> <span data-ttu-id="55450-330">Esta é a tomada de audição para pedidos de ligação TCP utilizando o serviço *de escuta* na linha 180.</span><span class="sxs-lookup"><span data-stu-id="55450-330">This is the listening socket for TCP connection requests using the *listen* service on line 180.</span></span> <span data-ttu-id="55450-331">A partir daqui, a função de thread do servidor, *thread_server_entry,* loops para verificar se há eventos de receção utilizando a chamada *selecionada* na linha 202.</span><span class="sxs-lookup"><span data-stu-id="55450-331">From here the server thread function, *thread_server_entry*, loops to check for receive events using the *select* call on line 202.</span></span> <span data-ttu-id="55450-332">Se um evento de receção for um pedido de ligação, que é determinado comparando a lista de prontos de leitura, chama *aceitar* na linha 213.</span><span class="sxs-lookup"><span data-stu-id="55450-332">If a receive event is a connection request, which is determined by comparing the read ready list, it calls *accept* on line 213.</span></span> <span data-ttu-id="55450-333">Uma tomada do servidor de criança é designada para lidar com o pedido de ligação e adicionada à lista principal de tomadas de servidor TCP ligadas a um Cliente na linha 223.</span><span class="sxs-lookup"><span data-stu-id="55450-333">A child server socket is assigned to handle the connection request and added to the master list of TCP server sockets connected to a Client on line 223.</span></span> <span data-ttu-id="55450-334">Se não houver novos pedidos de ligação, o fio do servidor verifica todas as tomadas atualmente ligadas para receber eventos no loop a partir da linha 236.</span><span class="sxs-lookup"><span data-stu-id="55450-334">If there are no new connection requests, the server thread then checks all the currently connected sockets for receive events in the for loop starting on line 236.</span></span> <span data-ttu-id="55450-335">Quando é detetada uma espera de evento de receção, liga *para enviar* e *recv* na tomada até que não sejam recebidos dados (ligação fechada do outro lado) e a tomada é fechada utilizando o serviço *de soc_close* na linha 277.</span><span class="sxs-lookup"><span data-stu-id="55450-335">When a receive event waiting is detected, it calls *send* and *recv* on that socket until no data is received (connection closed on the other side) and the socket is closed using the *soc_close* service on line 277.</span></span>

<span data-ttu-id="55450-336">Após a instalação da linha do servidor, a função de entrada da linha de fio cliente, *thread_client_entry,* cria uma tomada na linha 326 e liga-se à tomada do servidor TCP utilizando a chamada *de ligação* na linha 337.</span><span class="sxs-lookup"><span data-stu-id="55450-336">After the server thread sets up, the Client thread entry function, *thread_client_entry,* creates a socket on line 326 and connects with the TCP server socket using the *connect* call on line 337.</span></span> <span data-ttu-id="55450-337">Em seguida, dá voltas para enviar e receber pacotes usando os serviços *de envio* e *recv,* respectivamente.</span><span class="sxs-lookup"><span data-stu-id="55450-337">It then loops to send and receive packets using the *send* and *recv* services respectively.</span></span> <span data-ttu-id="55450-338">Quando não são recebidos mais dados, fecha a tomada na linha 398 utilizando o serviço *soc_close.*</span><span class="sxs-lookup"><span data-stu-id="55450-338">When no more data is received, it closes the socket on line 398 using the *soc_close* service.</span></span> <span data-ttu-id="55450-339">Após a desconexão, a função de entrada de fio do cliente cria uma nova tomada TCP e faz outro pedido de ligação no ciclo de enquanto o loop começou na linha 321.</span><span class="sxs-lookup"><span data-stu-id="55450-339">After disconnection, the client thread entry function creates a new TCP socket and makes another connection request in the while loop started on line 321.</span></span>

```c
/* This is a small demo of BSD Wrapper for the high-performance NetX Duo
TCP/IP stack which uses standard BSD services for TCP connection, sending,
and receiving using a simulated Ethernet driver. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nxd_bsd.h"
#include     <string.h>
#include     <stdlib.h>

#define     DEMO_STACK_SIZE     (16*1024)
#define     SERVER_PORT         87
#define     CLIENT_PORT         77

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_server;
TX_THREAD         thread_client;
NX_PACKET_POOL    bsd_pool;
NX_IP             bsd_ip;

/* Define some global data. */
CHAR     *msg0 = "Client 1:
    ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQR
    STUVWXYZ<>END";

INT     maxfd;

/* Define the counters used in the demo application... */

ULONG     error_counter;

/* Define fd_sets for the BSD server socket. */
fd_set     master_list, read_ready;

/* Define thread prototypes. */

VOID     thread_server_entry(ULONG thread_input);
VOID     thread_client_entry(ULONG thread_input);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */
int     main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void     tx_application_define(void *first_unused_memory)
{
CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create a server thread. */
    tx_thread_create(&thread_server, "Server", thread_server_entry, 0,
                    pointer, DEMO_STACK_SIZE, 8, 8, TX_NO_TIME_SLICE,
                    TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Create a Client thread. */
    tx_thread_create(&thread_client, "Client", thread_client_entry, 0,
                    pointer, DEMO_STACK_SIZE, 16, 16, TX_NO_TIME_SLICE,
                    TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a BSD packet pool. */
    status = nx_packet_pool_create(&bsd_pool, "NetX BSD Packet Pool", 128,
                                pointer, 16384);

    pointer = pointer + 16384;
    if (status)
    {
        error_counter++;
        printf("Error in creating BSD packet pool\n!");
    }

    /* Create an IP instance for BSD. */
    status = nx_ip_create(&bsd_ip, "BSD IP Instance", IP_ADDRESS(1,2,3,4),
                    0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                    pointer, 2048, 1);
                    pointer = pointer + 2048;

    if (status)
    {
        error_counter++;
        printf("Error creating BSD IP instance\n!");
    }

    /* Enable ARP and supply ARP cache memory for BSD IP Instance */
    status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable ARP \n");
    }

    /* Enable TCP processing for BSD IP instances. */
    status = nx_tcp_enable(&bsd_ip);

    /* Check TCP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable TCP \n");
    }

    /* Now initialize BSD Scoket Wrapper */
    status = bsd_initialize (&bsd_ip, &bsd_pool,pointer, 2048, 2);
}

/* Define the Server thread. */
CHAR     Server_Rcv_Buffer[100];

VOID     thread_server_entry(ULONG thread_input)
{

INT       status, sock, sock_tcp_server;
ULONG     actual_status;
INT       Clientlen;
INT       i;
UINT      is_set = NX_FALSE;
struct    sockaddr_in serverAddr;
struct    sockaddr_in ClientAddr;

    tx_thread_sleep(100);

    status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE,
        &actual_status, 100);

    /* Check status... */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Create BSD TCP Socket */
    sock_tcp_server = socket(AF_INET, SOCK_STREAM, 0);

    if (sock_tcp_server == -1)
    {
        printf("Error on Server socket %d create \n", sock_tcp_server);
        return;
    }

    printf("Server socket %d created\n", sock_tcp_server);

    /* Set the server port and IP address */
    memset(&serverAddr, 0, sizeof(serverAddr));
    serverAddr.sin_family = AF_INET;
    serverAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    serverAddr.sin_port = htons(SERVER_PORT);

    /* Bind this server socket */
    status = bind (sock_tcp_server, (struct sockaddr *) &serverAddr,
                sizeof(serverAddr));

    if (status < 0)
    {
        printf("Error on Server Socket %d Bind \n", sock_tcp_server);
        return;
    }

    FD_ZERO(&master_list);
    FD_ZERO(&read_ready);
    FD_SET(sock_tcp_server,&master_list);
    maxfd = sock_tcp_server;

    /* Now listen for any client connections for this server socket */
    status = listen (sock_tcp_server, 5);
    if (status < 0)
    {
        printf("Error on Server Socket %d Listen\n", sock_tcp_server);
        return;
    }
    else
        printf("Server socket %d listen complete\n", sock_tcp_server);

    /* All set to accept client connections */

    /* Loop to create and establish server connections. */
    while(1)
    {

        printf("\n");

        read_ready = master_list;

        tx_thread_sleep(20); /* Allow some time to other threads too */

        /* Let the underlying TCP stack determine the timeout. */
        status = select(maxfd + 1, &read_ready, 0, 0, 0);

        if ((status == 0xFFFFFFFF) || (status == 0))
        {

            printf("Error with select. Status 0x%x\n", status);

            continue;
        }

        /* Check for a connection request. */
        is_set = FD_ISSET(sock_tcp_server, &read_ready);

        if(is_set)
        {

            Clientlen = sizeof(ClientAddr);

            sock = accept(sock_tcp_server,(struct sockaddr*)&ClientAddr,
                        &Clientlen);

            /* Add this new connection to our master list */
            FD_SET(sock, &master_list);

            if ( sock \maxfd)
            {

                maxfd = sock;
            }

            continue;
        }

        /* Check the set of 'ready' sockets, e.g connected to remote host and
        waiting for notice of packets received. */
        for (i = NX_BSD_SOCKFD_START; i < (maxfd+1+NX_BSD_SOCKFD_START); i++)
        {

            if ((i != sock_tcp_server) &&
                (FD_ISSET(i , &master_list)) &&
                (FD_ISSET(i , &read_ready)))
            {

                while(1)
                {

                    status = recv(i, (VOID *)Server_Rcv_Buffer, 100, 0);

                    if (status == 0)
                    {
                        printf("(Server received no data from Client on
                            socket %d)\n", i);
                        break;
                    }
                    else if (status == NX_SOC_ERROR)
                    {
                        printf("Error on Server receiving data from Client on
                            socket %d\n", i);
                        break;
                    }
                    if(status == SERVER_RCV_BUFFER_SIZE) status--;
                    Server_Rcv_Buffer[status] = 0;
                    printf("Server socket %d received %d bytes: %s\n ",
                            i, (ULONG)status, Server_Rcv_Buffer);

                    status = send(i, "Hello\n", sizeof("Hello\n"), 0);

                    if (status == NX_SOC_ERROR)
                    {
                        printf("Error on Server socket %d sending data to
                        Client\n", i);
                    }
                    else
                    {
                        printf("Server socket %d message sent to Client:
                        Hello\n", i);
                    }
                }

                /* Close this socket */
                status = soc_close(i);

                if (status != NX_SOC_ERROR)
                {
                    printf("Server socket %d closed \n", i);
                }
                else
                {
                    printf("Error on closing Server socket %d \n", i);
                }
            }
        }

    /* Loop back to check any next client connection */
    }
}

CHAR     Client_Rcv_Buffer[100];

VOID     thread_client_entry(ULONG thread_input)
{

INT        status;
INT        sock_tcp_client, length;
struct     sockaddr_in echoServAddr;
struct     sockaddr_in localAddr; /

    /* Let the server side get set up. */
    tx_thread_sleep(200);

    /* Set local port for displaying IP address and port. */
    memset(&localAddr, 0, sizeof(localAddr));
    localAddr.sin_family = AF_INET;
    localAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    localAddr.sin_port = htons(CLIENT_PORT);

    /* Set server port and IP address which we need to connect. */
    memset(&echoServAddr, 0, sizeof(echoServAddr));
    echoServAddr.sin_family = AF_INET;
    echoServAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    echoServAddr.sin_port = htons(SERVER_PORT);

    /* Now make client connections with the server. */
    while (1)
    {

        printf("\n");

        /* Create BSD TCP Socket */
        sock_tcp_client = socket( AF_INET, SOCK_STREAM, 0);

        if (sock_tcp_client == -1)
        {
            printf("Error on Client socket %d create \n", sock_tcp_client);
            return;
        }

        printf("Client socket %d created\n", sock_tcp_client);

        /* Now connect this client to the server */
        status = connect(sock_tcp_client, (struct sockaddr *)&echoServAddr,
                        sizeof(echoServAddr));

        /* Check for error. */
        if (status != OK)
        {
            printf("Error on Client socket %d connect\n", sock_tcp_client);
                    soc_close(sock_tcp_client);
            return;
        }

        /* Get and print source and destination information */
        printf("Client socket %d connected \n", sock_tcp_client);

        status = getsockname(sock_tcp_client, (struct sockaddr *)&localAddr,
                            &length);

        printf("Client port = %lu , Client = 0x%x,",
            htonl(localAddr.sin_port), htonl(localAddr.sin_addr.s_addr));

        length = sizeof(struct sockaddr_in);

        status = getpeername( sock_tcp_client, (struct sockaddr *)
                            &echoServAddr, &length);

        printf("Remote port = %lu, Remote IP = 0x%x \n",
                htonl(echoServAddr.sin_port),
                htonl(echoServAddr.sin_addr.s_addr));

        /* Now receive the echoed packet from the server */
        while(1)
        {

            printf("Client sock %d sending packet to server\n",
            sock_tcp_client);

            status = send(sock_tcp_client, "Hello", (sizeof("Hello")), 0);

            if (status == ERROR)
            {
                printf("Error: Client Socket (%d) send \n", sock_tcp_client);
            }
            else
            {
                printf("Client socket %d sent message Hello\n",
                        sock_tcp_client);
            }

            status = recv(sock_tcp_client, (VOID *)Client_Rcv_Buffer,100,0);

            if (status <= 0)
            {

                if (status < 0)
                {
                    380 printf("Error on Client receiving on socket %d \n",
                            sock_tcp_client);
                }
                else
                {
                    printf("Nothing received by Client on socket %d\n",
                            sock_tcp_client);
                }

                break;
            }
            else
            {
                printf("Client socket %d received %d bytes: %s\n",
                        sock_tcp_client,
                        status, Client_Rcv_Buffer);
            }

        }

        /* close this client socket */
        status = soc_close(sock_tcp_client);

        if (status != ERROR)
        {
            printf("Client Socket %d closed\n", sock_tcp_client);
        }
        else
        {
            printf("Error on Client Socket %d on close \n", sock_tcp_client);
        }

        /* Make another Client connection...*/

    }
}
```

## <a name="small-ipv6-example-system"></a><span data-ttu-id="55450-340">Sistema de exemplo ipv6 pequeno</span><span class="sxs-lookup"><span data-stu-id="55450-340">Small IPv6 Example System</span></span>

<span data-ttu-id="55450-341">Um exemplo de como utilizar os serviços BSD NetX Duo para redes IPv6 é descrito no programa abaixo.</span><span class="sxs-lookup"><span data-stu-id="55450-341">An example of how to use NetX Duo BSD services for IPv6 networks is described in the program below.</span></span> <span data-ttu-id="55450-342">Este exemplo é muito semelhante ao programa de demonstração IPv4 anteriormente descrito com algumas diferenças importantes.</span><span class="sxs-lookup"><span data-stu-id="55450-342">This example is very similar to the IPv4 demo program previously described with a few important differences.</span></span>

<span data-ttu-id="55450-343">As linhas de cliente e servidor, piscina de pacotes BSD, instância IP e inicialização BSD acontecem como acontece com as tomadas BSD IPv4.</span><span class="sxs-lookup"><span data-stu-id="55450-343">The client and server threads, BSD packet pool, IP instance and BSD initialization happens as it does for IPv4 BSD sockets.</span></span>

<span data-ttu-id="55450-344">Na função de entrada de fio do servidor, *thread_server_entry,* define um par de variáveis IPv6 utilizando *sockaddr_in6* e *NXD_ADDRESS* tipos de dados nas linhas 145-148.</span><span class="sxs-lookup"><span data-stu-id="55450-344">In the server thread entry function, *thread_server_entry*, defines a couple IPv6 variables using *sockaddr_in6* and *NXD_ADDRESS* data types on lines 145-148.</span></span> <span data-ttu-id="55450-345">O tipo de dados NXD_ADDRESS pode armazenar os tipos de endereços IPv4 e IPv6.</span><span class="sxs-lookup"><span data-stu-id="55450-345">The NXD_ADDRESS data type can actually store both IPv4 and IPv6 address types.</span></span>

<span data-ttu-id="55450-346">Em seguida, o fio do servidor permite iPv6 e ICMPv6 na instância IP utilizando o serviço *de nxd_ipv6_enable* e *nxd_icmpv6_enable,* respectivamente, nas linhas 161 e 169.</span><span class="sxs-lookup"><span data-stu-id="55450-346">Next, the server thread enables IPv6 and ICMPv6 on the IP instance using the *nxd_ipv6_enable* and *nxd_icmpv6_enable* service respectively on line 161 and 169.</span></span> <span data-ttu-id="55450-347">Em seguida, os endereços IP locais e globais do link estão registados na instância IP.</span><span class="sxs-lookup"><span data-stu-id="55450-347">Next, the link local and global IP addresses are registered with the IP instance.</span></span> <span data-ttu-id="55450-348">Isto é feito usando o serviço *nxd_ipv6_address_set* nas linhas 180 e 195.</span><span class="sxs-lookup"><span data-stu-id="55450-348">This is done using the *nxd_ipv6_address_set* service on lines 180 and 195.</span></span> <span data-ttu-id="55450-349">Em seguida, dorme o tempo suficiente para que a tarefa de thread IP complete o protocolo de Deteção de Endereços Duplicado e registe estes endereços como endereços válidos na *chamada tx_thread_sleep* on-line 201.</span><span class="sxs-lookup"><span data-stu-id="55450-349">It then sleeps long enough for the IP thread task to complete the Duplicate Address Detection protocol and register these addresses as valid addresses on the *tx_thread_sleep* call on line 201.</span></span>

<span data-ttu-id="55450-350">Em seguida, a tomada do servidor TCP é criada com o AF_INET6 argumento de entrada do tipo tomada na linha 204.</span><span class="sxs-lookup"><span data-stu-id="55450-350">Next, the TCP server socket is created with the AF_INET6 socket type input argument on line 204.</span></span> <span data-ttu-id="55450-351">O endereço e porta do IPv6 da tomada são definidos nas linhas 216-221, observando novamente a utilização de macros *htonl* e *htons* para colocar dados em ordem de byte de rede para serviços de tomada de BSD.</span><span class="sxs-lookup"><span data-stu-id="55450-351">The socket IPv6 address and port are set on lines 216-221, again noting the use of *htonl* and *htons* macros to put data in network byte order for BSD socket services.</span></span> <span data-ttu-id="55450-352">A partir de agora, a função de entrada de fio do servidor é praticamente idêntica ao exemplo IPv4.</span><span class="sxs-lookup"><span data-stu-id="55450-352">From here on, the server thread entry function is virtually identical to the IPv4 example.</span></span>

<span data-ttu-id="55450-353">A função de entrada de fio do cliente, *thread_client_entry,* é definida em seguida.</span><span class="sxs-lookup"><span data-stu-id="55450-353">The client thread entry function, *thread_client_entry*, is defined next.</span></span> <span data-ttu-id="55450-354">Note que, uma vez que o cliente TCP neste exemplo partilha a mesma instância IP e endereço IPv6 que o servidor TCP, não precisamos de ativar os serviços IPv6 ou ICMPv6 na instância IP novamente.</span><span class="sxs-lookup"><span data-stu-id="55450-354">Note that because the TCP client in this example shares the same IP instance and IPv6 address as the TCP server, we do not need to enable IPv6 or ICMPv6 services on the IP instance again.</span></span> <span data-ttu-id="55450-355">Além disso, o endereço IPv6 também já está registado na instância IP.</span><span class="sxs-lookup"><span data-stu-id="55450-355">Further, the IPv6 address is also already registered with the IP instance.</span></span> <span data-ttu-id="55450-356">Em vez disso, a função de entrada de fio do cliente simplesmente aguarda na linha 368 para que o servidor se instale.</span><span class="sxs-lookup"><span data-stu-id="55450-356">Instead, the client thread entry function simply waits on line 368 for the server to set up.</span></span> <span data-ttu-id="55450-357">O endereço e a porta do servidor estão definidos, utilizando o anfitrião para encomendar macros de encomenda de rede nas linhas 387-392, e então o Cliente pode ligar-se ao servidor TCP na linha 412.</span><span class="sxs-lookup"><span data-stu-id="55450-357">The server address and port are set, using the host to network byte order macros on lines 387-392, and then the Client can connect with the TCP server on line 412.</span></span> <span data-ttu-id="55450-358">Note que os tipos de dados de endereço IP locais nas linhas 378-383 são utilizados apenas para demonstrar o *nome getockname* e os serviços *de nome getpeerna* nas linhas 425 e 434, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="55450-358">Note that the local IP address data types in lines 378-383 are used only to demonstrate the *getsockname* and *getpeername* services on lines 425 and 434 respectively.</span></span> <span data-ttu-id="55450-359">Como os dados vêm da rede, a rede para hospedar byte macros como usado nas linhas 378-383.</span><span class="sxs-lookup"><span data-stu-id="55450-359">Because the data is coming from the network, the network to host byte order macros as used in lines 378-383.</span></span>

<span data-ttu-id="55450-360">Em seguida, a função de entrada de fio do cliente introduz um loop no qual cria uma tomada TCP, faz uma ligação TCP e envia e recebe dados com o servidor TCP até que nenhum dado seja recebido praticamente o mesmo que o exemplo IPv4.</span><span class="sxs-lookup"><span data-stu-id="55450-360">Next the client thread entry function enters a loop in which it creates a TCP socket, makes a TCP connection and sends and receives data with the TCP server until no more data is received virtually the same as the IPv4 example.</span></span> <span data-ttu-id="55450-361">Em seguida, fecha a tomada na linha 483, faz uma pausa breve e cria outra tomada TCP e solicita uma ligação do servidor TCP.</span><span class="sxs-lookup"><span data-stu-id="55450-361">It then closes the socket on line 483, pauses briefly and creates another TCP socket and requests a TCP server connection.</span></span>

<span data-ttu-id="55450-362">Uma diferença importante com o exemplo IPv4 é que as chamadas de *tomada* especificam uma tomada IPv6 utilizando o argumento de entrada AF_INET6.</span><span class="sxs-lookup"><span data-stu-id="55450-362">One important difference with the IPv4 example is the *socket* calls specify an IPv6 socket using the AF_INET6 input argument.</span></span> <span data-ttu-id="55450-363">Outra diferença importante é que a chamada *de ligação* do Cliente TCP requer um tipo *de dados sockaddr_in6* e um argumento de comprimento definido para o tamanho do tipo de dados *sockaddr_in6.*</span><span class="sxs-lookup"><span data-stu-id="55450-363">Another important difference is that the TCP Client *connect* call takes an *sockaddr_in6* data type and a length argument set to the size of the *sockaddr_in6* data type.</span></span>

```c
/* This is a small demo of BSD Wrapper for the high-performance NetX Duo
TCP/IP stack which uses standard BSD services for TCP connection,
disconnection, sending, and receiving using a simulated Ethernet driver. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nxd_bsd.h"
#include     <string.h>
#include     <stdlib.h>

#define     DEMO_STACK_SIZE     (16*1024)
#define     SERVER_PORT         87
#define     CLIENT_PORT         77

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_server;
TX_THREAD         thread_client;
NX_PACKET_POOL    bsd_pool;
NX_IP             bsd_ip;

/* Define some global data. */
CHAR     *msg0 = "Client 1:
    ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>END";

INT     maxfd;

/* Define the counters used in the demo application... */
ULONG     error_counter;

/* Define fd_sets for the BSD server socket. */
fd_set     master_list, read_ready;

/* Define thread prototypes. */
VOID     thread_server_entry(ULONG thread_input);
VOID     thread_client_entry(ULONG thread_input);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

int     main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void tx_application_define(void *first_unused_memory)
{
CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create a server thread. */
    tx_thread_create(&thread_server, "Server", thread_server_entry, 0,
                    pointer, DEMO_STACK_SIZE, 8, 8,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Create a Client thread. */
    tx_thread_create(&thread_client, "Client", thread_client_entry, 0,
                    pointer, DEMO_STACK_SIZE, 16, 16,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a BSD packet pool. */
    status = nx_packet_pool_create(&bsd_pool, "NetX BSD Packet Pool",
    128, pointer, 16384);

    pointer = pointer + 16384;

    if (status)
    {
        error_counter++;
        printf("Error in creating BSD packet pool\n!");
    }

    /* Create an IP instance for BSD. */
    status = nx_ip_create(&bsd_ip, "BSD IP Instance", IP_ADDRESS(1,2,3,4),
                        0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                        pointer, 2048, 1);
                        pointer = pointer + 2048;

    if (status)
    {
        error_counter++;
        printf("Error creating BSD IP instance\n!");
    }

    /* Enable ARP and supply ARP cache memory for BSD IP Instance */
    status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in enable ARP on BSD IP instance\n");
    }

    /* Enable TCP processing for BSD IP instances. */
    status = nx_tcp_enable(&bsd_ip);

    /* Check TCP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable TCP \n");
    }

    /* Now initialize BSD Scoket Wrapper */
    status = bsd_initialize(&bsd_ip, &bsd_pool,pointer, 2048, 2);

    /* Check BSD initialize status. */
    if (status)
    {
        error_counter++;
        printf("Error in BSD initialize \n");
    }

    pointer = pointer + 2048;
}

/* Define the Server thread. */
CHAR     Server_Rcv_Buffer[100];

VOID     thread_server_entry(ULONG thread_input)
{

INT             status, sock, sock_tcp_server;
ULONG           actual_status;
INT             Clientlen;
INT             i;
UINT            is_set = NX_FALSE;
NXD_ADDRESS     ip_address;
struct          sockaddr_in6 serverAddr;
struct          sockaddr_in6 ClientAddr;
UINT            iface_index, address_index;

    status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE,
            &actual_status, 100);

    /* Check status... */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable IPv6 */
    status = nxd_ipv6_enable(&bsd_ip);
    if((status != NX_SUCCESS) && (status != NX_ALREADY_ENABLED))
    {
        printf("Error with IPv6 enable 0x%x\n", status);
        return;
    }

    /* Enable ICMPv6 */
    status = nxd_icmp_enable(&bsd_ip);

    if(status)
    {
        printf("Error with ECMPv6 enable 0x%x\n", status);
        return;
    }

    /* Set the primary interface for our DNS IPv6 addresses. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&bsd_ip, iface_index, NX_NULL, 10,
                                &address_index);

    if (status)
        return;

    /* Set ip_0 interface address. */
    ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    ip_address.nxd_ip_address.v6[0] = htonl(0x20010db8);
    ip_address.nxd_ip_address.v6[1] = htonl(0x0000f101);
    ip_address.nxd_ip_address.v6[2] = 0;
    ip_address.nxd_ip_address.v6[3] = htonl(0x101);

    /* Set the host global IP address. We are assuming a 64
    bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&bsd_ip, iface_index, &ip_address, 64,
                                &address_index);

    if (status)
        return;

    /* Wait for IPv6 stack to finish DAD process. */
    tx_thread_sleep(400);

    /* Create BSD TCP Socket */
    sock_tcp_server = socket(AF_INET6, SOCK_STREAM, 0);

    if (sock_tcp_server == -1)
    {
        printf("\nError: BSD TCP Server socket create \n");
        return;
    }

    printf("\nBSD TCP Server socket created %lu \n", sock_tcp_server);

    /* Set the server port and IP address */
    memset(&serverAddr, 0, sizeof(serverAddr));
    serverAddr.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    serverAddr.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    serverAddr.sin6_addr._S6_un._S6_u32[2] = 0x0;
    serverAddr.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    serverAddr.sin6_port = htons(SERVER_PORT);
    serverAddr.sin6_family = AF_INET6;

    /* Bind this server socket */
    status = bind(sock_tcp_server, (struct sockaddr *) &serverAddr,
                    sizeof(serverAddr));

    if (status < 0)
    {
        printf("Error: Server Socket Bind \n");
        return;
    }

    FD_ZERO(&master_list);
    FD_ZERO(&read_ready);
    FD_SET(sock_tcp_server,&master_list);
    maxfd = sock_tcp_server;

    /* Now listen for any client connections for this server socket */
    status = listen(sock_tcp_server, 5);
    if (status < 0)
    {
        printf("Error: Server Socket Listen\n");
        return;
    }
    else
        printf("Server Listen complete\n");

    /* All set to accept client connections */
    printf("Now accepting client connections\n");

    /* Loop to create and establish server connections. */
    while(1)
    {

        printf("\n");

        read_ready = master_list;

        tx_thread_sleep(20); /* Allow some time to other threads too */

        /* Let the underlying TCP stack determine the timeout. */
        status = select(maxfd + 1, &read_ready, 0, 0, 0);

        if ( (status == 0xFFFFFFFF) || (status == 0) )
        {
            printf("Error with select? Status 0x%x. Try again\n", status);

            continue;
        }

        /* Detected a connection request. */
        is_set = FD_ISSET(sock_tcp_server,&read_ready);

        if(is_set)
        {

            Clientlen = sizeof(ClientAddr);

            sock = accept(sock_tcp_server,
            (struct sockaddr*)&ClientAddr,
            &Clientlen);

            /* Add this new connection to our master list */
            FD_SET(sock, &master_list);

            if ( sock \maxfd)
            {
                printf("New connection %d\n", sock);

                maxfd = sock;
            }

            continue;
        }

        /* Check the set of 'ready' sockets, e.g connected to remote host and
        waiting for notice of packets received. */
        for (i = NX_BSD_SOCKFD_START; i < (maxfd+1+NX_BSD_SOCKFD_START); i++)
        {

            if ((i != sock_tcp_server) &&
                (FD_ISSET(i, &master_list)) &&
                (FD_ISSET(i, &read_ready)))
            {

                while(1)
                {

                    status = recv(i, (VOID *)Server_Rcv_Buffer, 100, 0);

                    if (status == 0)
                    {
                        printf("(Server socket %d received no data from
                                Client)\n", i);

                        break;
                    }
                    else if (status == 0xFFFFFFFF)
                    {
                        printf("Error on Server socket %d receiving data from
                                Client\n", i);

                        break;
                    }

                    printf("Server socket %d received from Client %lu bytes:
                            %s\n ", i, (ULONG)status,
                            Server_Rcv_Buffer);

                    status = send(i, "Hello\n", sizeof("Hello\n"), 0);

                    if (status == ERROR)
                    {
                        printf("Error on Server socket %d sending data to
                                Client \n", i);
                    }
                    else
                    {
                        printf("Server socket %d message sent to Client:
                                Hello\n", i);
                    }
                }

                /* Close this socket */
                status = soc_close(i);

                if (status != ERROR)
                {
                    printf("Server socket %d closing\n", i);
                }
                else
                {

                    printf("Error on Server socket %d closing\n", i);
                }
            }
        }

        /* Loop back to check any next client connection */
    }
}

#define     CLIENT_BUFFER_SIZE 100
CHAR        Client_Rcv_Buffer[CLIENT_BUFFER_SIZE];

VOID        thread_client_entry(ULONG thread_input)
{

INT         status;
INT         sock_tcp_client, length;
struct      sockaddr_in6 echoServAddr6;
struct      sockaddr_in6 localAddr6; address */

    /* Wait for the server side to get set up, including the DAD process. */
    tx_thread_sleep(500);

    /* ICMPv6 and IPv6 should already be enabled on the IP instance
    by the server thread entry function. */

    /* Further the IPv6 address is already established with the IP instance.
    so no need to wait for DAD completion. */

    /* Set local port and IP address (used only for getsockname call). */
    memset(&localAddr6, 0, sizeof(localAddr6));
    localAddr6.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    localAddr6.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    localAddr6.sin6_addr._S6_un._S6_u32[2] = 0x0;
    localAddr6.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    localAddr6.sin6_port = htons(CLIENT_PORT);
    localAddr6.sin6_family = AF_INET6;

    /* Set Server port and IP address to connect to the TCP server. */
    memset(&echoServAddr6, 0, sizeof(echoServAddr6));
    echoServAddr6.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    echoServAddr6.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    echoServAddr6.sin6_addr._S6_un._S6_u32[2] = 0x0;
    echoServAddr6.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    echoServAddr6.sin6_port = htons(SERVER_PORT);
    echoServAddr6.sin6_family = AF_INET6;

    /* Now make client connections with the server. */
    while (1)
    {
        printf("\n");

        /* Create BSD TCP Socket */

        sock_tcp_client = socket(AF_INET6, SOCK_STREAM, 0);

        if (sock_tcp_client == -1)
        {
            printf("Error on Client socket %d create \n");
            return;
        }

        printf("Client socket %d created \n", sock_tcp_client);

        /* Now connect this client to the server */
        status = connect(sock_tcp_client, (struct sockaddr *)&echoServAddr6,
                sizeof(echoServAddr6));

        /* Check for error. */
        if (status != NX_SOC_OK)
        {
            printf("Error on Client socket %d connect\n");
            soc_close(sock_tcp_client);
            return;

        }

        /* Get and print source and destination information */
        printf("Client socket %d connected \n", sock_tcp_client);

        status = getsockname(sock_tcp_client, (struct sockaddr *)&localAddr6,
        &length);

        printf("Client port = %lu , Client = 0x%x 0x%x 0x%x 0x%x,",
                ntohs(localAddr6.sin6_port),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[0]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[1]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[2]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[3]));

        length = sizeof(struct sockaddr_in6);

        status = getpeername(sock_tcp_client, (struct sockaddr *)
                            &echoServAddr6, &length);

        printf("Remote port = %lu, Remote IP = 0x%x 0x%x 0x%x 0x%x \n",
                ntohs(echoServAddr6.sin6_port),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[0]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[1]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[2]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[3]));

        /* Now receive the echoed packet from the server */
        while(1)
        {

            printf("Client sock %d sending packet to server\n",
                sock_tcp_client);

            status = send(sock_tcp_client, "Hello", sizeof("Hello"), 0);

            if (status == NX_SOC_ERROR)
            {
                printf("Error on Client Socket (%d) send \n",
                        sock_tcp_client);
            }
            else
            {
                printf("Client socket %d sent message: Hello\n",
                        sock_tcp_client);
            }

            status = recv(sock_tcp_client, (VOID *)Client_Rcv_Buffer,
                        CLIENT_BUFFER_SIZE, 0);

            if (status <= 0)
            {

                if (status < 0)
                {
                    printf("Error on Client receiving on socket %d \n",
                            sock_tcp_client);
                }
                else
                {
                    printf("Client received no data on socket %d\n",
                            sock_tcp_client);
                }

            break;
            }
            else
            {
                printf("Client socket %d received %d bytes and this message:
                        %s\n", sock_tcp_client, status,
                        Client_Rcv_Buffer);
            }

        }

        /* close this client socket */
        status = oc_close(sock_tcp_client);

        if (status != NX_SOC_ERROR)
        {
            printf("Client Socket %d closed\n", sock_tcp_client);
        }
        else
        {
            printf("Error on Client Socket %d on close \n", sock_tcp_client);
        }

        /* Make another Client connection...*/

    }
}
```
