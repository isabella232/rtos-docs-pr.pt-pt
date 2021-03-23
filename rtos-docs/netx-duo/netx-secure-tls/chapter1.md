---
title: Capítulo 1 - Introdução ao Azure RTOS NetX Secure
description: Este capítulo contém uma introdução ao Azure RTOS NetX Secure e uma descrição das suas aplicações e benefícios.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8f4c7a97564cd2f702f9887181b36297b42fa492
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825682"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-secure"></a>Capítulo 1 - Introdução ao Azure RTOS NetX Secure

Azure RTOS NetX Secure é uma implementação em tempo real de alto desempenho de padrões de segurança de rede criptográfica, incluindo TLS/SSL projetado exclusivamente para aplicações incorporadas baseadas em ThreadX. Este capítulo contém uma introdução ao NetX Secure e uma descrição das suas aplicações e benefícios.

## <a name="netx-secure-unique-features"></a>Recursos exclusivos da NetX Secure

Ao contrário da maioria das outras implementações do TLS, o NetX Secure foi projetado do zero para suportar uma grande variedade de plataformas e escalas de hardware incorporadas facilmente, desde pequenas aplicações de microcontrolador até aos processadores incorporados mais poderosos disponíveis. O código é escrito com os recursos limitados dos sistemas incorporados em mente, e fornece uma série de opções de configuração para reduzir a pegada de memória necessária para fornecer comunicações de rede seguras sobre TLS.

## <a name="rfcs-supported-by-netx-secure"></a>RFCs Suportados por NetX Secure 

O NetX Secure suporta os seguintes protocolos relacionados com o TLS. A lista não é necessariamente abrangente, uma vez que existem numerosos RFCs relativos ao TLS e à criptografia. O NetX Secure segue todas as recomendações gerais e requisitos básicos dentro dos limites de um sistema operativo em tempo real com pequena pegada de memória e execução eficiente.

| RFC      | Descrição                                                                                                 | Página |
|----------|-------------------------------------------------------------------------------------------------------------|------|
| RFC 2104 | HMAC: Keyed-Hashing para autenticação de mensagens                                                              | 33   |
| RFC 2246 | O Protocolo TLS Versão 1.0                                                                                | 19   |
| RFC 3268 | Cifrasuites avançadas da Padrão de Encriptação (AES) para segurança da camada de transporte (TLS)                          | 31   |
| RFC 3447 | Public-Key Padrões de Criptografia (PKCS) #1: RSA Cryptography Specifications Version 2.1                    | 32   |
| RFC 4279 | Cifrasuites de chaves pré-partilhadas para TLS                                                                         | 39   |
| RFC 4346 | Protocolo de Segurança da Camada de Transporte (TLS) Versão 1.1                                                     | 19   |
| RFC 5246 | Protocolo de Segurança da Camada de Transporte (TLS) Versão 1.2                                                     | 19   |
| RFC 5280 | Certificados X.509 PKI (v3)                                                                                 | 41   |
| RFC 5746 | Extensão de indicação de renegociação da extensão da indicação de renegociação da camada de transporte (TLS)                                           |      |
| RFC 5869 | Função de derivação da chave de extração e expansão baseada em HMAC (HKDF)                                                | 19   |
| RFC 6066<sup>1</sup> | Extensões de segurança da camada de transporte (TLS): Definições de extensão                                            | 19   |
| RFC 6234 | Us Secure Hash Algorithms (SHA e SHA-based HMAC e HKDF)                                                 | 33   |
| RFC 8443 | Criptografia da Curva Elíptica (ECC) Cipher Suites for Transport Layer Security (TLS) Versões 1.2 e Anterior |      |
| RFC 8446 | Protocolo de Segurança da Camada de Transporte (TLS) Versão 1.3                                                     | 19   |

1. A partir da versão 6.0 apenas a extensão de indicação de nome do servidor (SNI) do RFC 6066 está totalmente suportada.

## <a name="netx-secure-requirements"></a>Requisitos de segurança NetX

Para funcionar corretamente, a biblioteca de tempo de execução NetX Secure requer que já tenha sido criada uma instância IP NetX. Além disso, e dependendo da aplicação, serão necessários um ou mais Certificados Digitais X.509 codificados pela DER, quer para identificar uma instância TLS, quer para verificar certificados provenientes de um anfitrião remoto. O pacote NetX Secure não tem mais requisitos.

## <a name="netx-secure-constraints"></a>Restrições de segurança NetX

O protocolo NetX Secure implementa os requisitos do RFC 5246 Standard(s) para TLS 1.2 e RFC 8446 para TLS 1.3, bem como fornecer opcional (desativado por padrão) retrocompatibilidade com RFCs 4346 (TLS 1.1) e 2246 (TLS 1.0). No entanto, existem os seguintes constrangimentos:

- Apenas os cifrasuites que utilizam SHA-256 são suportados para TLS 1.2 e TLS 1.3. Nas versões anteriores ao TLS 1.2, o aperto de mão TLS utiliza uma rotina de hashing fixa para verificar se as mensagens de aperto de mão TLS não são adulteradas. Começando pela versão 1.2, o aperto de mão utiliza a rotina de haxixe fornecida com a cifrasuite. O TLS não sabe com antecedência qual a rotina de haxixe que será usada e deve cache as mensagens de aperto de mão. Ao fixar o hash a SHA-256, o NetX Secure TLS pode funcionar com uma pegada RAM menor do que outras implementações de TLS. Esta limitação será removida numa versão futura assim que a utilização da memória possa ser devidamente abordada. *NOTA IMPORTANTE: Esta limitação aplica-se **apenas** à escolha cifrassuita. As assinaturas de certificado X.509 não estão sujeitas à mesma limitação e qualquer uma das rotinas de haxixe suportadas pode ser utilizada.
- Devido à natureza dos dispositivos incorporados, algumas aplicações podem não ter recursos para suportar o tamanho máximo de registo de TLS de 16KB. O NetX Secure pode lidar com registos de 16KB em dispositivos com recursos suficientes. O tampão de remontagem TLS (ver referência API para *nx_secure_tls_session_packet_buffer_set*) **pode** ser definido para um tamanho inferior a 16KB em risco de problemas de interoperabilidade. Se for recebido um registo TLS válido que seja maior do que o tampão de remontagem, o NetX Secure TLS abortará a sessão de TLS com um erro. Em geral, o tampão deve ser sempre regulado para pelo menos 18KB (tamanho de registo 16KB TLS + 2KB para enchimento de encriptação) e apenas reduzido em configurações controladas (por exemplo, o hospedeiro remoto garante um tamanho máximo de registo TLS).
  > [!NOTE]
  > Em geral, o tampão de remontagem do pacote nunca deve ser menor do que o tamanho máximo de registo TLS. No entanto, se as características do hospedeiro remoto forem bem conhecidas (por exemplo, num sistema completamente fechado), o tamanho pode ser reduzido para recuperar algum espaço RAM.
- Verificação mínima do certificado. O NetX Secure efetuará a verificação básica da cadeia X.509 num certificado para garantir que o certificado é válido e assinado por uma Autoridade de Certificados de confiança, e pode fornecer o certificado Nome Comum para o pedido de comparação com o Top-Level Nome de Domínio do anfitrião remoto. Se estiver disponível um relógio em tempo real, pode ser utilizado para verificar a data de validade do certificado (ver API nx_secure_tls_session_time_function_set). No entanto, a verificação das extensões de certificados e outros dados é da responsabilidade do implementador de aplicações.
- A criptografia baseada em software é intensiva em processador. As rotinas criptográficas baseadas em software NetX Secure foram otimizadas para o desempenho, mas dependendo da potência do processador-alvo, esse desempenho pode resultar em operações muito longas. Quando a criptografia baseada em hardware estiver disponível, deve ser usada para um desempenho ideal do NetX Secure TLS.
- A fragmentação do TLS Handshake Record não é suportada. Se certas mensagens de gravação de aperto de mão TLS forem demasiado grandes, podem ser divididas em vários registos TLS – o NetX Secure TLS trata atualmente isto como um erro. Os requisitos de memória para sistemas incorporados significam que a mensagem de registo de aperto de mão maior provavelmente não pode ser manuseada de qualquer forma, mas a limitação pode levar a erros ao comunicar com certos anfitriões TLS que usam cadeias de certificados excessivamente grandes.
- O servidor TLS não suporta a seleção dinâmica de certificados quando existem vários certificados na loja local. 
- Não é observado o certificado X509 KeyUsage. 
- As cifrasuites baseadas no ECDH não são apoiadas. Use o ECDHE em vez disso.
