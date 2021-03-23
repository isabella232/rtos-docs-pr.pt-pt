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
# <a name="appendix-d---azure-rtos-netx-bsd-compatible-socket-api"></a>Apêndice D - Azure RTOS NetX BSD-Compatible Socket API

## <a name="bsd-compatible-socket-api"></a>API de tomada de BSD-Compatible

A API de tomada de BSD-Compatible suporta um subconjunto das chamadas API de tomadas BSD (com algumas limitações) utilizando primitivos Azure RTOS NetX por baixo. Os protocolos IPv4 e a endereçamento da rede são suportados. Esta camada API de tomadas de BSD-Compatible deve funcionar tão rápido ou ligeiramente mais rápido do que as implementações típicas de BSD, porque esta API utiliza primitivos Internos netX e contorna a verificação de erros netx desnecessárias.

As opções configuráveis permitem à aplicação do anfitrião definir o número máximo de tomadas, o tamanho máximo da janela TCP e a profundidade da fila de escuta.

Devido a restrições de desempenho e arquitetura, esta BSD-Compatible API de tomadas não suporta todas as chamadas de Tomadas BSD. Além disso, nem todas as opções de BSD estão disponíveis para os serviços BSD, especificamente as seguintes:

- A função ***select** _ funciona apenas com _fd_set \* readfds*, outros argumentos nesta chamada por exemplo, *writefds,* *exceto os fds* não são suportados.
- O argumento *das bandeiras int* não é suportado para as funções ***enviar** _, _*_recv,_*_ _*_sendto_*_ e _ *_recv from_** funções. A API de tomada de BSD-Compatible suporta apenas um conjunto limitado de chamadas de tomadas BSD.

O código fonte foi concebido para a simplicidade e é composto por apenas dois ficheiros,***nx_bsd.c** _ e _*_nx_bsd.h_*_. A instalação requer a adição destes dois ficheiros ao projeto de construção (não à biblioteca NetX) e a criação da aplicação de anfitrião que utilizará chamadas de serviço de tomada BSD. O ficheiro _ *_nx_bsd.h*_* também deve ser incluído na sua fonte de aplicação. Os ficheiros de demonstração de amostras estão incluídos na distribuição que está livremente disponível com o NetX. Estão disponíveis mais detalhes na ajuda BSD-Compatible ficheiros API **417** e Readme agregados com o pacote API da tomada BSD-Compatible.

A API de tomadas de BSD-Compatible suporta as seguintes chamadas API de tomadas BSD:

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
