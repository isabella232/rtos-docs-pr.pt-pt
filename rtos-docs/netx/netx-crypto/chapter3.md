---
title: Capítulo 3 - Descrição funcional do Azure RTOS NetX Crypto
description: Este capítulo contém uma descrição funcional do NetX Crypto.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4ecdbfe99daa000d109908f834b139dcaf321491
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825592"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-crypto"></a>Capítulo 3 - Descrição funcional do Azure RTOS NetX Crypto

## <a name="execution-overview"></a>Visão geral da execução

Este capítulo contém uma descrição funcional de Azure RTOS NetX Crypto. Existem dois tipos primários de execução de programas numa aplicação NetX Crypto: inicialização e interface de aplicação.

*NetX Crypto pode ser usado como uma biblioteca criptográfica autónoma, ou pode ser usado com ThreadX, NetX e/ou NetX Secure.*

## <a name="aes"></a>AES

- **Algoritmo Standard:**: NetX Crypto implementa AES de acordo com o NIST FIPS 197, que pode ser encontrado em: [http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf)
- **Comprimentos-chave Suportados:** 128, 192, 256
- **Modos Suportados:**
  - CBC, CTR, (Comprimento da chave 128-, 192-, 256-bit)
  - XCBC (comprimento da chave apenas 128 bits),
  - CCM8 (comprimento da chave apenas 128 bits)
- **Requisitos de memória**: A aplicação especifica o tampão de entrada e o tampão de saída e uma estrutura de controlo AES. A estrutura de controlo da AES mantém o estado do algoritmo AES entre chamadas para a API. O tampão de entrada contém dados para serem encriptados ou desencriptados, e pode ser de tamanho arbitrário. O tampão de saída é utilizado pela AES para armazenar dados que estão a ser tratados pela AES. O tamanho do tampão de saída não deve ser menor do que o tamanho do tampão de entrada, e deve ser um múltiplo de 16 bytes, o tamanho do bloco AES. Os amortecedores de entrada e saída devem ser memória contíguas e não se sobrepor, exceto no caso especial de encriptação no local (utilizando a mesma memória para entrada e saída). Ao encriptar no local, o tampão de saída começa exatamente no mesmo local que o tampão de entrada, e não deve ser menor do que o tampão de entrada. Quando a encriptação AES funciona no local, não é necessária nenhuma memória de risco extra.

## <a name="3des"></a>3DES

- **Algoritmo Standard**: NetX Crypto implementa Tripple DES (TDES, também conhecido como 3DES) de acordo com a Publicação Especial NIST 800-67 rev 2: *"Recomendação para o Algoritmo de Encriptação de Dados Triplos (TDES) Block Cipher",* que pode ser encontrado em: [https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final](https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final)
- **Comprimento da chave suportado**: 64 * 3 = 192
- **Requreiment memória:**: Nenhum

Na NetX Crypto, o termo "3DES" é usado alternadamente com "TDES".

## <a name="md5"></a>MD5

- **Algoritmo Standard**: NetX Crypto implementa MD5 de acordo com RFC 1321: *"O Algoritmo de Message-Digest MD5"*
- **Requisito de memória**: A aplicação deve fornecer uma estrutura de bloco de controlo MD5, utilizada para manter o estado entre as operações MD5.

## <a name="sha1-sha256512"></a>SHA1, SHA256/512

- **Algoritmo Padrão:** NetX Crypto implementa SHA1/256/512 de acordo com a publicação NIST FIPS 180-4: "*Secure Hash Standard*", que pode ser encontrado em: [http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf)
- **Tamanho do bloco de haxixe:**
  - SHA1: 160 bits de valor de haxixe
  - SHA 224: 224 bits de valor de haxixe
  - SHA 256: 256 bits de valor de haxixe
  - SHA 384: 384 bits de valor de haxixe
  - SHA 512: 512 bits de valor de haxixe
  - SHA 512/224: 224 bits de valor de haxixe
  - SHA 512/256: 256 bits de valor de haxixe

  Na NetX Crypto, as rotinas SHA256 são usadas para ter SHA256 e SHA224. As rotinas SHA512 são usadas para entregar SHA512, SHA384, SHA512/224 e SHA512/256.
- **Requisito de memória:** O pedido deve fornecer uma estrutura de bloco de controlo SHA para manter o estado entre as operações.

## <a name="rsa"></a>RSA

- **Norma:** NetX Crypto implementa RSA de acordo com a norma "*PKCS #1 v2.2: RSA Cryptography Standard*", que é publicado como RFC 8017 e também pode ser encontrado em: [https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf](https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf)
- **Requisito de memória:** A aplicação deve fornecer uma estrutura de bloco de controlo RSA para manter o estado entre as operações e para fornecer espaço tampão "scratch" necessário para cálculos intermédios.

## <a name="hmac"></a>HMAC

- **Norma:** NetX Crypto implementa HMAC de acordo com FIPS PUB 198-1: "*O Código de Autenticação de Mensagens Keyed-Hash (HMAC)*", que pode ser encontrado em: [https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf](https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf)
- **Requisito de memória:** O pedido deve fornecer uma estrutura de bloco de controlo HMAC para manter o estado entre as operações. O bloco de controlo efetivo fornecido depende da operação de haxixe subjacente desejada (por exemplo, SHA1, MD5).

## <a name="elliptic-curve"></a>Curva elíptica

- **Norma:** NetX Crypto implementa Curva Elíptica. As curvas com nome suportado são (apenas no campo primário):
  - P-192
  - P-224
  - P-256
  - P-384
  - P-521

   > [!TIP]
   > O formato não comprimido é suportado. Consulte as secções 2.3.3 e 2.3.4 da SEC1-v1: [http://www.secg.org/sec1-v2.pdf](http://www.secg.org/sec1-v2.pdf)

- **Requisito de memória:** Nenhum.

## <a name="ecdsa"></a>ECDSA

- **Norma:** NetX Crypto implementa ECDSA de acordo com FIPS PUB 186-4: "*Digital Signature Standard (DSS)*", que pode ser encontrado em: [https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf](https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf)
- **Requisito de memória:** O pedido deve fornecer uma estrutura de bloco de controlo ECDSA para manter o estado entre as operações.

## <a name="ecdh"></a>ECDH

> [!IMPORTANT]
> No Azure RTOS 6.0, as rotinas do ECDH só devem ser utilizadas para a criptografia ECDHE, uma vez que o ECDH com uma chave privada estática requer que a validação do ponto de entrada seja segura.

- **Norma:** NetX Crypto implementa ECDH de acordo com FIPS PUB 800-56Ar2: "Recomendação para Pair-Wise principais sistemas de estabelecimento usando criptografia de logaritm discreta", que pode ser encontrada em: [https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf](https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf)
- **Requisito de memória:** O pedido deve fornecer uma estrutura de bloco de controlo do ECDH para manter o estado entre as operações.

## <a name="drbg"></a>DRBG

- **Norma:** NetX Crypto implementa DRBG de acordo com FIPS PUB 800-90Ar1: "Recomendação para geração aleatória de números usando geradores de bits aleatórios determinísticos", que pode ser encontrada em: [https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf)
- **Requisito de memória:** O pedido deve fornecer uma estrutura de bloco de controlo DRBG para manter o estado entre as operações.

## <a name="fips-compliant"></a>FIPS-Compliant

NetX Crypto FIPS 140-2