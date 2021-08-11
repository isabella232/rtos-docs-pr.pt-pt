---
title: Apêndice D - Azure RTOS NetX Duo BSD-Compatible Socket API
description: Saiba mais sobre o BSD-Compatible Socket API para IPv4 e IPv6.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cd43c3efa18dd76f6eb996c84091024f48ad65aa5839958066161080dc02127e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116789753"
---
# <a name="appendix-d---azure-rtos-netx-duo-bsd-compatible-socket-api"></a>Apêndice D - Azure RTOS NetX Duo BSD-Compatible Socket API

## <a name="bsd-compatible-socket-api"></a>API de tomada de BSD-Compatible 
A API de tomada de BSD-Compatible suporta um subconjunto das chamadas API de tomadas BSD (com algumas limitações) utilizando primitivos NetX Duo &reg; por baixo. Os protocolos IPv6 e IPv4 e o endereçamento da rede são suportados. Esta camada API de tomadas de BSD-Compatible deve funcionar tão rápida ou ligeiramente mais rápida do que as implementações típicas de BSD, porque esta API utiliza primitivos internos do NetX Duo e contorna a verificação de erros do NetX desnecessários.  

As opções configuráveis permitem à aplicação do anfitrião definir o número máximo de tomadas, o tamanho máximo da janela TCP e a profundidade da fila de escuta.

Devido a restrições de desempenho e arquitetura, esta BSD-Compatible API de tomadas não suporta todas as chamadas de Tomadas BSD. Além disso, nem todas as opções de BSD estão disponíveis para os serviços BSD, especificamente as seguintes:

  - ***selecione** _ trabalhos de chamada apenas com \_ fd_set readfds, outros argumentos nesta chamada por exemplo, writefds, excetfds não são suportados.
  - O argumento "int flags" não é suportado para ***enviar** _, _*_recv,_*_ _*_sendto,_*_ e _ *_recvfrom_** chamadas. 
  - A API de tomada de BSD-Compatible suporta apenas um conjunto limitado de chamadas de tomadas BSD.

O código fonte foi concebido para a simplicidade e é composto por apenas dois ficheiros, ***nxd_bsd.c** _ e _*_nxd_bsd.h_*_. A instalação requer a adição destes dois ficheiros ao projeto de construção (não à biblioteca NetX) e a criação da aplicação de anfitrião que utilizará chamadas de serviço de tomada BSD. O ficheiro _ *_nxd_bsd.h*_* também deve ser incluído na sua fonte de aplicação. Os ficheiros de demonstração de amostras para aplicações baseadas em IPv4 e IPv6 estão incluídos na distribuição que está livremente disponível com o NetX Duo. Mais detalhes estão disponíveis nos ficheiros de ajuda e Readme agregados com o pacote API da Tomada API da Tomada BSDCompatible.

A API de tomadas de BSD-Compatible suporta as seguintes chamadas API de tomadas BSD:

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