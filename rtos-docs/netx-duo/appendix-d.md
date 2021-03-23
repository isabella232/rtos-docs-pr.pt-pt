---
title: Apêndice D - Azure RTOS NetX Duo BSD-Compatible Socket API
description: Saiba mais sobre o BSD-Compatible Socket API para IPv4 e IPv6.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 82439184d9facb6ddcc08ce81bc51182d7f34429
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826233"
---
# <a name="appendix-d---azure-rtos-netx-duo-bsd-compatible-socket-api"></a><span data-ttu-id="bdba0-103">Apêndice D - Azure RTOS NetX Duo BSD-Compatible Socket API</span><span class="sxs-lookup"><span data-stu-id="bdba0-103">Appendix D - Azure RTOS NetX Duo BSD-Compatible Socket API</span></span>

## <a name="bsd-compatible-socket-api"></a><span data-ttu-id="bdba0-104">API de tomada de BSD-Compatible</span><span class="sxs-lookup"><span data-stu-id="bdba0-104">BSD-Compatible Socket API</span></span> 
<span data-ttu-id="bdba0-105">A API de tomada de BSD-Compatible suporta um subconjunto das chamadas API de tomadas BSD (com algumas limitações) utilizando primitivos NetX Duo &reg; por baixo.</span><span class="sxs-lookup"><span data-stu-id="bdba0-105">The BSD-Compatible Socket API supports a subset of the BSD Sockets API calls (with some limitations) by utilizing NetX Duo&reg; primitives underneath.</span></span> <span data-ttu-id="bdba0-106">Os protocolos IPv6 e IPv4 e o endereçamento da rede são suportados.</span><span class="sxs-lookup"><span data-stu-id="bdba0-106">Both IPv6 and IPv4 protocols and network addressing are supported.</span></span> <span data-ttu-id="bdba0-107">Esta camada API de tomadas de BSD-Compatible deve funcionar tão rápida ou ligeiramente mais rápida do que as implementações típicas de BSD, porque esta API utiliza primitivos internos do NetX Duo e contorna a verificação de erros do NetX desnecessários.</span><span class="sxs-lookup"><span data-stu-id="bdba0-107">This BSD-Compatible Sockets API layer should perform as fast or slightly faster than typical BSD implementations because this API utilizes internal NetX Duo primitives and bypasses unnecessary NetX error checking.</span></span>  

<span data-ttu-id="bdba0-108">As opções configuráveis permitem à aplicação do anfitrião definir o número máximo de tomadas, o tamanho máximo da janela TCP e a profundidade da fila de escuta.</span><span class="sxs-lookup"><span data-stu-id="bdba0-108">Configurable options allow the host application to define the maximum number of sockets, TCP maximum window size, and depth of listen queue.</span></span>

<span data-ttu-id="bdba0-109">Devido a restrições de desempenho e arquitetura, esta BSD-Compatible API de tomadas não suporta todas as chamadas de Tomadas BSD.</span><span class="sxs-lookup"><span data-stu-id="bdba0-109">Due to performance and architecture constraints, this BSD-Compatible Sockets API does not support all BSD Sockets calls.</span></span> <span data-ttu-id="bdba0-110">Além disso, nem todas as opções de BSD estão disponíveis para os serviços BSD, especificamente as seguintes:</span><span class="sxs-lookup"><span data-stu-id="bdba0-110">In addition, not all BSD options are available for the BSD services, specifically the following:</span></span>

  - <span data-ttu-id="bdba0-111">\***selecione** _ trabalhos de chamada apenas com \_ fd_set readfds, outros argumentos nesta chamada por exemplo, writefds, excetfds não são suportados.</span><span class="sxs-lookup"><span data-stu-id="bdba0-111">\***select** _ call works with only fd_set \_readfds, other arguments in this call e.g., writefds, exceptfds are not supported.</span></span>
  - <span data-ttu-id="bdba0-112">O argumento "int flags" não é suportado para ***enviar** _, _*_recv,_*_ _*_sendto,_*_ e _ *_recvfrom_** chamadas.</span><span class="sxs-lookup"><span data-stu-id="bdba0-112">The "int flags" argument is not supported for ***send** _, _*_recv_*_, _*_sendto,_*_ and _ *_recvfrom_** calls.</span></span> 
  - <span data-ttu-id="bdba0-113">A API de tomada de BSD-Compatible suporta apenas um conjunto limitado de chamadas de tomadas BSD.</span><span class="sxs-lookup"><span data-stu-id="bdba0-113">The BSD-Compatible Socket API supports only limited set of BSD Sockets calls.</span></span>

<span data-ttu-id="bdba0-114">O código fonte foi concebido para a simplicidade e é composto por apenas dois ficheiros, ***nxd_bsd.c** _ e _*_nxd_bsd.h_\*_.</span><span class="sxs-lookup"><span data-stu-id="bdba0-114">The source code is designed for simplicity and is comprised of only two files, ***nxd_bsd.c** _ and _*_nxd_bsd.h_\*_.</span></span> <span data-ttu-id="bdba0-115">A instalação requer a adição destes dois ficheiros ao projeto de construção (não à biblioteca NetX) e a criação da aplicação de anfitrião que utilizará chamadas de serviço de tomada BSD.</span><span class="sxs-lookup"><span data-stu-id="bdba0-115">Installation requires adding these two files to the build project (not the NetX library) and creating the host application which will use BSD Socket service calls.</span></span> <span data-ttu-id="bdba0-116">O ficheiro _ *_nxd_bsd.h*_\* também deve ser incluído na sua fonte de aplicação.</span><span class="sxs-lookup"><span data-stu-id="bdba0-116">The _ *_nxd_bsd.h_*\* file must also be included in your application source.</span></span> <span data-ttu-id="bdba0-117">Os ficheiros de demonstração de amostras para aplicações baseadas em IPv4 e IPv6 estão incluídos na distribuição que está livremente disponível com o NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="bdba0-117">Sample demo files for both IPv4 and IPv6  based applications are included with the distribution which is freely available with NetX Duo.</span></span> <span data-ttu-id="bdba0-118">Mais detalhes estão disponíveis nos ficheiros de ajuda e Readme agregados com o pacote API da Tomada API da Tomada BSDCompatible.</span><span class="sxs-lookup"><span data-stu-id="bdba0-118">Further details are available in the help and Readme files bundled with the BSDCompatible Socket API package.</span></span>

<span data-ttu-id="bdba0-119">A API de tomadas de BSD-Compatible suporta as seguintes chamadas API de tomadas BSD:</span><span class="sxs-lookup"><span data-stu-id="bdba0-119">The BSD-Compatible Sockets API supports the following BSD Sockets API calls:</span></span>

```c
INT     bsd_initialize (NX_IP *default_ip, NX_PACKET_POOL *default_pool, CHAR
        *bsd_memory_not_used);
```
```c
INT     getpeername( INT sockID, struct sockaddr *remoteAddress, INT
        *addressLength);
```
```c
INT     getsockname( INT sockID, struct sockaddr *localAddress, INT *addressLength);
```
```c
INT     recvfrom(INT sockID, CHAR *buffer, INT buffersize, INT flags,struct sockaddr
        *fromAddr, INT *fromAddrLen);
```
```c        
INT     recv(INT sockID, VOID *rcvBuffer, INT bufferLength, INT flags);
```
```c
INT     sendto(INT sockID, CHAR *msg, INT msgLength, INT flags, struct sockaddr
        *destAddr, INT destAddrLen);
```
```c        
INT     send(INT sockID, const CHAR *msg, INT msgLength, INT flags);
```
```c
INT     accept(INT sockID, struct sockaddr *ClientAddress, INT *addressLength);
```
```c
INT     listen(INT sockID, INT backlog);
```
```c
INT     bind (INT sockID, struct sockaddr *localAddress, INT addressLength);
```
```c
INT     connect(INT sockID, struct sockaddr *remoteAddress, INT addressLength);
```
```c
INT     socket( INT protocolFamily, INT type, INT protocol);
```
```c
INT     soc_close ( INT sockID);
```
```c
INT     select(INT nfds, fd_set *readfds, fd_set *writefds, fd_set *exceptfds, struct
        timeval *timeout);
```
```c
VOID    FD_SET(INT fd, fd_set *fdset);
```
```c
VOID    FD_CLR(INT fd, fd_set *fdset);
```
```c
INT     FD_ISSET(INT fd, fd_set *fdset);
```
```c
VOID    FD_ZERO(fd_set *fdset);
```