---
title: Apêndice D - Azure RTOS NetX BSD-Compatible Socket API
description: Saiba mais sobre a API de tomada de BSD-Compatible para iPv4.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9062e27d8f447ac8d36e7a09afee5ac14f86f8c3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826899"
---
# <a name="appendix-d---azure-rtos-netx-bsd-compatible-socket-api"></a><span data-ttu-id="a48d4-103">Apêndice D - Azure RTOS NetX BSD-Compatible Socket API</span><span class="sxs-lookup"><span data-stu-id="a48d4-103">Appendix D - Azure RTOS NetX BSD-Compatible Socket API</span></span>

## <a name="bsd-compatible-socket-api"></a><span data-ttu-id="a48d4-104">API de tomada de BSD-Compatible</span><span class="sxs-lookup"><span data-stu-id="a48d4-104">BSD-Compatible Socket API</span></span>

<span data-ttu-id="a48d4-105">A API de tomada de BSD-Compatible suporta um subconjunto das chamadas API de tomadas BSD (com algumas limitações) utilizando primitivos Azure RTOS NetX por baixo.</span><span class="sxs-lookup"><span data-stu-id="a48d4-105">The BSD-Compatible Socket API supports a subset of the BSD Sockets API calls (with some limitations) by utilizing Azure RTOS NetX primitives underneath.</span></span> <span data-ttu-id="a48d4-106">Os protocolos IPv4 e a endereçamento da rede são suportados.</span><span class="sxs-lookup"><span data-stu-id="a48d4-106">IPv4 protocols and network addressing are supported.</span></span> <span data-ttu-id="a48d4-107">Esta camada API de tomadas de BSD-Compatible deve funcionar tão rápido ou ligeiramente mais rápido do que as implementações típicas de BSD, porque esta API utiliza primitivos Internos netX e contorna a verificação de erros netx desnecessárias.</span><span class="sxs-lookup"><span data-stu-id="a48d4-107">This BSD-Compatible Sockets API layer should perform as fast or slightly faster than typical BSD implementations because this API utilizes internal NetX primitives and bypasses unnecessary NetX error checking.</span></span>

<span data-ttu-id="a48d4-108">As opções configuráveis permitem à aplicação do anfitrião definir o número máximo de tomadas, o tamanho máximo da janela TCP e a profundidade da fila de escuta.</span><span class="sxs-lookup"><span data-stu-id="a48d4-108">Configurable options allow the host application to define the maximum number of sockets, TCP maximum window size, and depth of listen queue.</span></span>

<span data-ttu-id="a48d4-109">Devido a restrições de desempenho e arquitetura, esta BSD-Compatible API de tomadas não suporta todas as chamadas de Tomadas BSD.</span><span class="sxs-lookup"><span data-stu-id="a48d4-109">Due to performance and architecture constraints, this BSD-Compatible Sockets API does not support all BSD Sockets calls.</span></span> <span data-ttu-id="a48d4-110">Além disso, nem todas as opções de BSD estão disponíveis para os serviços BSD, especificamente as seguintes:</span><span class="sxs-lookup"><span data-stu-id="a48d4-110">In addition, not all BSD options are available for the BSD services, specifically the following:</span></span>

- <span data-ttu-id="a48d4-111">A função ***select** _ funciona apenas com _fd_set \* readfds*, outros argumentos nesta chamada por exemplo, *writefds,* *exceto os fds* não são suportados.</span><span class="sxs-lookup"><span data-stu-id="a48d4-111">The ***select** _ function works with only _fd_set \*readfds*, other arguments in this call e.g., *writefds*, *exceptfds* are not supported.</span></span>
- <span data-ttu-id="a48d4-112">O argumento *das bandeiras int* não é suportado para as funções ***enviar** _, _*_recv,_*_ _*_sendto_*_ e _ *_recv from_** funções.</span><span class="sxs-lookup"><span data-stu-id="a48d4-112">The *int flags* argument is not supported for the ***send** _, _*_recv_*_, _*_sendto,_*_ and _ *_recvfrom_** functions.</span></span> <span data-ttu-id="a48d4-113">A API de tomada de BSD-Compatible suporta apenas um conjunto limitado de chamadas de tomadas BSD.</span><span class="sxs-lookup"><span data-stu-id="a48d4-113">The BSD-Compatible Socket API supports only limited set of BSD Sockets calls.</span></span>

<span data-ttu-id="a48d4-114">O código fonte foi concebido para a simplicidade e é composto por apenas dois ficheiros,***nx_bsd.c** _ e _*_nx_bsd.h_\*_.</span><span class="sxs-lookup"><span data-stu-id="a48d4-114">The source code is designed for simplicity and is comprised of only two files,***nx_bsd.c** _ and _*_nx_bsd.h_\*_.</span></span> <span data-ttu-id="a48d4-115">A instalação requer a adição destes dois ficheiros ao projeto de construção (não à biblioteca NetX) e a criação da aplicação de anfitrião que utilizará chamadas de serviço de tomada BSD.</span><span class="sxs-lookup"><span data-stu-id="a48d4-115">Installation requires adding these two files to the build project (not the NetX library) and creating the host application which will use BSD Socket service calls.</span></span> <span data-ttu-id="a48d4-116">O ficheiro _ *_nx_bsd.h*_\* também deve ser incluído na sua fonte de aplicação.</span><span class="sxs-lookup"><span data-stu-id="a48d4-116">The _ *_nx_bsd.h_*\* file must also be included in your application source.</span></span> <span data-ttu-id="a48d4-117">Os ficheiros de demonstração de amostras estão incluídos na distribuição que está livremente disponível com o NetX.</span><span class="sxs-lookup"><span data-stu-id="a48d4-117">Sample demo files are included with the distribution which is freely available with NetX.</span></span> <span data-ttu-id="a48d4-118">Estão disponíveis mais detalhes na ajuda BSD-Compatible ficheiros API **417** e Readme agregados com o pacote API da tomada BSD-Compatible.</span><span class="sxs-lookup"><span data-stu-id="a48d4-118">Further details are available in the help BSD-Compatible Socket API **417** and Readme files bundled with the BSD-Compatible Socket API package.</span></span>

<span data-ttu-id="a48d4-119">A API de tomadas de BSD-Compatible suporta as seguintes chamadas API de tomadas BSD:</span><span class="sxs-lookup"><span data-stu-id="a48d4-119">The BSD-Compatible Sockets API supports the following BSD Sockets API calls:</span></span>

```C
*INT bsd_initialize (NX_IP *default_ip, NX_PACKET_POOL *default_pool,
    CHAR *bsd_memory_not_used);*

*INT getpeername( INT sockID, struct sockaddr *remoteAddress, INT *addressLength);*

*INT getsockname( INT sockID, struct sockaddr *localAddress, INT *addressLength);*

*INT recvfrom(INT sockID, CHAR *buffer, INT buffersize,
    INT flags,struct sockaddr *fromAddr, INT *fromAddrLen);*

*INT recv(INT sockID, VOID *rcvBuffer, INT bufferLength, INT flags);*

*INT sendto(INT sockID, CHAR *msg, INT msgLength, INT flags,
    struct sockaddr *destAddr, INT destAddrLen);*

*INT send(INT sockID, const CHAR *msg, INT msgLength, INT flags);*

 *INT accept(INT sockID, struct sockaddr *ClientAddress, INT *addressLength);*

*INT listen(INT sockID, INT backlog);*

*INT bind (INT sockID, struct sockaddr *localAddress, INT addressLength);*

*INT connect(INT sockID, struct sockaddr *remoteAddress, INT addressLength);*

*INT socket( INT protocolFamily, INT type, INT protocol);*

*INT soc_close ( INT sockID);*

*INT select(INT nfds, fd_set *readfds, fd_set *writefds,
    fd_set *exceptfds, struct timeval *timeout);*

*VOID FD_SET(INT fd, fd_set *fdset);*

*VOID FD_CLR(INT fd, fd_set *fdset);*

*INT FD_ISSET(INT fd, fd_set *fdset);*

*VOID FD_ZERO(fd_set *fdset);*

```
