---
title: Capítulo 1 - Introdução ao Azure RTOS NetX Secure DTLS
description: Azure RTOS NetX Secure DTLS é uma implementação em tempo real do protocolo de Segurança da Camada de Transporte de Datagram projetado para aplicações incorporadas baseadas em ThreadX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: dbd81082524f50787765dfacf494248dda740fd6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826977"
---
# <a name="chapter-1-introduction-to-azure-rtos-netx-secure-dtls"></a>Capítulo 1: Introdução ao Azure RTOS NetX Secure DTLS

Azure RTOS NetX Secure DTLS é uma implementação em tempo real de alto desempenho do protocolo de Segurança da Camada de Transporte de Datagram projetado exclusivamente para aplicações incorporadas baseadas em ThreadX. Este capítulo contém uma introdução ao DTLS NetX Secure e uma descrição das suas aplicações e benefícios.

## <a name="netx-secure-unique-features"></a>Recursos exclusivos da NetX Secure

Ao contrário da maioria das outras implementações TLS/DTLS, o NetX Secure foi projetado do zero para suportar uma grande variedade de plataformas e escalas de hardware incorporadas facilmente, desde pequenas aplicações de microcontrolador até aos mais poderosos processadores incorporados disponíveis. O código é escrito com os recursos limitados dos sistemas incorporados em mente, e fornece uma série de opções de configuração para reduzir a pegada de memória necessária para fornecer comunicações de rede seguras sobre TLS ou DTLS.

## <a name="rfcs-supported-by-netx-secure"></a>RFCs Suportados por NetX Secure

O NetX Secure suporta os seguintes protocolos relacionados com TLS e DTLS. A lista não é necessariamente abrangente, uma vez que existem numerosos RFCs relativos a TLS/DTLS e criptografia. O NetX Secure segue todas as recomendações gerais e requisitos básicos dentro dos limites de um sistema operativo em tempo real com pequena pegada de memória e execução eficiente.


| RFC | Descrição |
| --- | ----------- |
| RFC 6347 | Versão de segurança da camada de transporte de datagram 1.2. |
| RFC 2246 | O Protocolo TLS Versão 1.0|
| RFC 4346 | Protocolo de Segurança da Camada de Transporte (TLS) Versão 1.1 |
| RFC 5246 | Protocolo de Segurança da Camada de Transporte (TLS) Versão 1.2 |
| RFC 5280 | Certificados X.509 PKI (v3) |
| RFC 3268 | Cifrasuites avançadas da Padrão de Encriptação (AES) para segurança da camada de transporte (TLS) |
| RFC 3447 | Public-Key Padrões de Criptografia (PKCS) #1: RSA Cryptography Specifications Version 2.1 |
| RFC 2104 | HMAC: Keyed-Hashing para autenticação de mensagens |
| RFC 6234 | Us Secure Hash Algorithms (SHA e SHA-based HMAC e HKDF) |
| RFC 4279 | Cifrasuites de chaves pré-partilhadas para TLS |

## <a name="netx-secure-dtls-requirements"></a>Requisitos de DTLS seguros netX

Para funcionar corretamente, a biblioteca de tempo de execução NetX Secure requer que já tenha sido criada uma instância IP NetX. Além disso, e dependendo da aplicação, serão necessários um ou mais Certificados Digitais X.509 codificados pela DER, quer para identificar uma instância TLS/DTLS, quer para verificar certificados provenientes de um hospedeiro remoto. O pacote NetX Secure não tem mais requisitos.

## <a name="netx-secure-dtls-constraints"></a>Restrições de DTLS de segurança NetX

O protocolo DTLS Seguro NetX implementa os requisitos do RFC 6347 Standard(s) para DTLS 1.2. No entanto, existem os seguintes constrangimentos:

1. Devido à natureza dos dispositivos incorporados, algumas aplicações podem não ter recursos para suportar o tamanho máximo de registo TLS/DTLS de 16KB. O NetX Secure pode lidar com registos de 16KB em dispositivos com recursos suficientes.
2. Verificação mínima do certificado. O NetX Secure efetuará a verificação básica da cadeia X.509 num certificado para garantir que o certificado é válido e assinado por uma Autoridade de Certificados de confiança, e pode fornecer o certificado Nome Comum para o pedido de comparação com o Top-Level Nome de Domínio do anfitrião remoto. No entanto, a verificação das extensões de certificados e outros dados é da responsabilidade do implementador de aplicações.
3. A criptografia baseada em software é intensiva em processador. As rotinas criptográficas baseadas em software NetX Secure foram otimizadas para o desempenho, mas dependendo da potência do processador-alvo, esse desempenho pode resultar em operações muito longas. Quando a criptografia baseada em hardware estiver disponível, deve ser usada para um desempenho ideal do DTLS NetX Secure.
