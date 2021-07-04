---
title: Capítulo 2 - Instalação e utilização do Azure RTOS NetX Crypto
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente NetX Crypto.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3323af5eaf31ac9c167966522df6477c82e99fdc
ms.sourcegitcommit: c98e5360c9cedbe773af5a44f5163f563c85b570
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/24/2021
ms.locfileid: "110337011"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-crypto"></a>Capítulo 2 - Instalação e utilização do Azure RTOS NetX Crypto

Este capítulo descreve a instalação, configuração e utilização do componente Azure RTOS NetX Crypto.

## <a name="product-distribution"></a>Distribuição de Produtos

Azure RTOS NetX Crypto está disponível em [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . O pacote inclui ficheiros de origem, inclui ficheiros e um ficheiro PDF que contém este documento, da seguinte forma:

- **nx_crypto.h**: Arquivo de cabeçalho API público NetX Crypto módulo
- **nx_crypto_*.c/h:** Ficheiros C/H Source para NetX Crypto
- **nx_crypto_port.h**: Ficheiro de cabeçalho C contendo todas as ferramentas de desenvolvimento e definições e estruturas específicas de dados específicas.
- **NetX_Crypto_User_Guide.pdf**: Descrição EM PDF do Módulo Crypto NetX.

## <a name="netx-crypto-installation"></a>Instalação NetX Crypto

Toda a distribuição mencionada anteriormente está disponível no **diretório crypto_libraries,** presente ao nível raiz do repositório NetX Duo.

Para utilizar o NetX Crypto, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo nível de diretório onde o NetX está instalado. Por exemplo, se o NetX estiver instalado no diretório "\threadx\arm7\NetX" então o nx_crypto *.* os diretórios devem ser copiados em "\threadx\arm7\NetXCrypto".

Para que o NetX Crypto seja utilizado em modo autónomo, toda a distribuição mencionada anteriormente deve ser copiada para o projeto de aplicação. Por **exemplo, crypto_libraries** diretório deve ser copiado para o projeto de candidatura ou para um projeto de biblioteca com **crypto_libraries** diretório deve ser criado e ligado ao projeto de candidatura. 

## <a name="using-netx-crypto"></a>Usando o NetX Crypto

O código de aplicação deve incluir o *nx_crypto.h*.  Uma vez *incluído nx_crypto.h,* o código de aplicação é então capaz de fazer as chamadas de função NetX Crypto especificadas mais tarde neste guia.

## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração para a construção do NetX Crypto. Segue-se uma lista de todas as opções, onde cada uma é descrita em detalhe:

- **NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: Definida, esta opção dá o módulo RSA máximo esperado, em bits. O valor predefinido é de 4096 para um módulo de 4096 bits. Outros valores podem ser 3072, 2048 ou 1024 (não recomendado).
- **NX_CRYPTO_SELF_TEST**: Definido, permite auto-testes para o módulo Crypto NetX. **NX_CRYPTO_FIPS** símbolo é agora depreciado e renomeado para **NX_CRYPTO_SELF_TEST**
- **NX_CRYPTO_STANDALONE_ENABLE**: Definido permite que o NetX Crypto seja utilizado em modo autónomo (sem Azure RTOS). Por padrão, este símbolo não está definido.
