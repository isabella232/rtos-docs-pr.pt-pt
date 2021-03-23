---
title: Capítulo 1 - Introdução ao Azure RTOS NetX Crypto
description: NetX Crypto é uma implementação em tempo real de algoritmos criptográficos projetados para fornecer serviços de encriptação e autenticação de dados.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0bde9be472584308894cfd702ccd014578afe753
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825597"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-crypto"></a>Capítulo 1 - Introdução ao Azure RTOS NetX Crypto

Azure RTOS NetX Crypto é uma implementação em tempo real de algoritmos criptográficos projetados para fornecer serviços de encriptação e autenticação de dados. O NetX Crypto foi concebido para ligar para os módulos NetX Secure TLS, DTLS e IPsec. As aplicações também podem usar o NetX Crypto como um módulo autónomo fora da segurança da rede.

## <a name="netx-crypto-unique-features"></a>Recursos exclusivos da NetX Crypto

NetX Crypto é implementado na língua C padrão (C99), compatível com praticamente todos os compiladores C/C++. O seu design modular permite que uma aplicação apenas ligue nos algoritmos cripto que precisa de usar, conseguindo assim o tamanho mínimo do código. A implementação destina-se a funcionar com a maioria dos microprocessadores de 32 bits e utiliza apenas as operações básicas de matemática (adição, subtração, multiplicação, divisão, lógica E, OR, NOR e operações de mudança de bits). Todas estas operações são usadas com quantidades de 32 bits, tornando o NetX Crypto portátil na maioria dos microprocessadores de 32 bits. A implementação está especificamente otimizada para funcionar em microprocessadores restritos de recursos, direcionando aplicações profundamente incorporadas.

## <a name="algorithms-supported-by-netx-crypto"></a>Algoritmos suportados por NetX Crypto

NetX Crypto suporta os seguintes algoritmos criptográficos. A NetX Crypto segue todas as recomendações gerais e requisitos básicos dentro dos constrangimentos de um sistema operativo em tempo real e plataformas que requerem uma pequena pegada de memória e uma execução eficiente.

| Algoritmo       | Comprimento da chave (bits)      |
| --------------- | ---------------------- |
| AES (CBC, CTR)   | 128, 192, 256          |
| AES(XCBC)       | 128                    |
| AES-CCM 8       | 128                    |
| 3DES(CBC)       | 192                    |
| HMAC-SHA1       | Qualquer comprimento             |
| HMAC-SHA224     | Qualquer comprimento             |
| HMAC-SHA256     | Qualquer comprimento             |
| HMAC-SHA384     | Qualquer comprimento             |
| HMAC-SHA512     | Qualquer comprimento             |
| HMAC-SHA512/224 | Qualquer comprimento             |
| HMAC-SHA512/256 | Qualquer comprimento             |
| HMAC-MD5        | Qualquer comprimento             |
| RSA             | 1024, 2048, 3072, 4096 |

| Algoritmo       | Digestão comprimento (bits) | Tamanho do bloco (bits) |
| --------------- | -------------------- | ----------------- |
| SHA1            | 160                  | 512               |
| SHA224          | 224                  | 512               |
| SHA256          | 256                  | 512               |
| SHA384          | 384                  | 1024              |
| SHA512          | 512                  | 1024              |
| MD5             | 128                  | 512               |
| HMAC-SHA1       | 160                  | 512               |
| HMAC-SHA224     | 224                  | 512               |
| HMAC-SHA256     | 256                  | 512               |
| HMAC-SHA384     | 384                  | 1024              |
| HMAC-SHA512     | 512                  | 1024              |
| HMAC-SHA512/224 | 224                  | 1024              |
| HMAC-SHA512/256 | 256                  | 1024              |
| HMAC-MD5        | 128                  | 512               |
| Curva elíptica  | P192/224/256/384/521 |                   |

## <a name="netx-crypto-requirements"></a>Requisitos de Cripto NetX

TBD: Requisito de memória. Interromper/reentretar seguro? Precisa de discussão

## <a name="netx-crypto-constraints"></a>Restrições de Cripto NetX

Nenhum.
