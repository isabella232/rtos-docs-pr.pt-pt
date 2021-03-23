---
title: Capítulo 2 - Instalação e Utilização do Cliente RTOS NetX Duo LWM2M
description: Este capítulo explica como instalar e utilizar o RtOS NetX Duo LWM2M Client.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 536225de30f54356157c222917fc904c6aa039fe
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825951"
---
# <a name="chapter-2--installation-and-use-of-lwm2m-client"></a>Capítulo 2 Instalação e Utilização do Cliente LWM2M

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente LWM2M Client.

## <a name="product-distribution"></a>Distribuição de Produtos

Cliente Azure RTOS LWM2M pode ser obtido a partir do nosso repositório de código fonte pública em [https://github.com/azure-rtos/netxduo/tree/master/addons/lwm2m](https://github.com/azure-rtos/netxduo/tree/master/addons/lwm2m/) . O pacote inclui três ficheiros de origem, um inclui ficheiros, da seguinte forma.

* **nx \_ lwm2m \_ cliente.h** Arquivo de cabeçalho para o Cliente LWM2M

* **\_ nx lwm2m \_ cliente.c** ficheiros C Source para Cliente LWM2M

* **demo \_ netx \_ lwm2m \_ cliente.c** ficheiro C Source para demonstração de cliente LWM2M

## <a name="lwm2m-client-installation"></a>Instalação do cliente LWM2M

O Cliente LWM2M faz parte da NetX Duo. Assim, após a clonagem do NetX Duo do repositório GitHub, a fonte de cliente LWM2M pode ser encontrada em ***netxduo/addons/lwm2m***.

## <a name="using-lwm2m_client"></a>Utilização de Cliente LWM2M \_

A utilização do Cliente LWM2M é simples. Basicamente, o código de aplicação deve incluir ***nx \_ lwm2m \_ client.h**_ depois de incluir _*_tx \_ api.h_*_ e _*_nx \_ api.h_*_, a fim de usar ThreadX e NetX. Uma vez incluído _*_nx \_ lwm2m \_ client.h_*_ é incluído, o código de aplicação é então capaz de fazer as chamadas de função LWM2M Cliente especificadas mais tarde neste guia. O pedido também deve importar os ficheiros _* _nx \_ cliente lwm2m \_ \_ para \**** a biblioteca NetX.

## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração ao construir a biblioteca LWM2M Client e a aplicação utilizando o Cliente LWM2M. As opções de configuração podem ser definidas na fonte de aplicação, na linha de comando, salvo especificação em contrário.

| Opção de configuração &nbsp; | Descrição |
| --- | --- |
| **CLIENTE NX \_ LWM2M \_ \_ MTU** | Especifica o tamanho máximo de uma mensagem CoAP, incluindo cabeçalhos IP e UDP. O valor predefinido é de 1280. |
| **TOS DE TOMADA DE CLIENTE NX \_ LWM2M \_ \_ \_** | Tipo de serviço necessário para o UDP LwM2M. Por predefinição, este valor é definido como NX \_ IP NORMAL para indicar o serviço normal de \_ pacotes IP. |
| **TTL DE TOMADA DE CLIENTE NX \_ LWM2M \_ \_ \_** | Especifica o número de routers que este pacote pode passar antes de ser descartado. O valor predefinido é definido para 0x80. |
| **FILA DE TOMADA DE CLIENTE NX \_ LWM2M \_ \_ \_ \_ MAX** | Especifica o número de profundidades máximas da fila de receção. O valor predefinido é definido para 4. |
| **NX \_ LWM2M \_ CLIENTE MAX \_ \_ COAP \_ URI \_ PATH** | Especifica o número de comprimentos máximos da opção coAP Uri-Path. O valor predefinido é definido para 32. |
| **ERROS DO DISPOSITIVO MAX DO CLIENTE NX \_ LWM2M \_ \_ \_ \_** | Especifica o número máximo de códigos de erro armazenados pelo Objeto do Dispositivo. O valor predefinido é 8. |
| **\_NX LWM2M \_ CLIENTE MAX SECURITY \_ \_ \_ INSTANCES** | Especifica o número máximo de instâncias de objetos de segurança. O valor predefinido é 2 para suportar um Servidor Bootstrap e um Servidor padrão. |
| **NX \_ LWM2M \_ CLIENT \_ MAX \_ SERVER \_ INSTANCES** | Especifica o número máximo de instâncias de objetos de servidor. O valor predefinido é 1 para suportar um único Servidor padrão. |
| **NX \_ LWM2M \_ CLIENTE MAX ACESSO A \_ \_ \_ INSTÂNCIAS DE CONTROLO DE ACESSO \_** | Especifica o número máximo de instâncias de controlo de acesso. O valor predefinido é 0, que desativa o controlo de acesso. Se a aplicação suportar mais de um Servidor LWM2M, o número máximo de Instâncias de Controlo de Acesso deve ser definido para o número máximo de instâncias de objeto que o Cliente LWM2M irá suportar, uma vez que uma Instância de Controlo de Acesso deve ser criada para cada Instância de Objeto (exceto para as Instâncias de Objeto de Segurança). |
| **NX \_ LWM2M \_ CLIENTE MAX ACCESS CONTROL \_ \_ \_ \_ ACLS** | Especifica o número máximo de recursos ACL por Instância de Controlo de Acesso. O valor predefinido é 4. |
| **NOTIFICAÇÕES MAX DO CLIENTE NX \_ LWM2M \_ \_ \_** | Especifica o número máximo de notificações que o Cliente LWM2M irá suportar. Um Servidor LWM2M pode definir notificações em Objetos, Instâncias de Objetos e Recursos. O valor predefinido é 8. |
| **RECURSOS MAX DO CLIENTE NX \_ LWM2M \_ \_ \_** | Especifica o número máximo de Recursos por Objeto. O valor predefinido é 32. |
| **CLIENTE NX \_ LWM2M \_ \_ MAX MÚLTIPLOS \_ \_ RECURSOS** | Especifica o número máximo de casos de Recursos para vários recursos. O valor predefinido é 8. |
| **CLIENTE NX \_ LWM2M \_ \_ BOOTSTRAP \_ \_ TEMPORIZADOR INATIVO** | Especifica o tempo máximo para esperar pelos pedidos do servidor bootstrap quando a sessão de bootstrap é iniciada antes de abortar a sessão. O valor predefinido é de 60 segundos. |
| **NX \_ LWM2M \_ CLIENTE \_ DTLS \_ INICIAR \_ TEMPO** | Especifica o tempo máximo para esperar pela conclusão do aperto de mão DTLS. O valor predefinido é de 30 segundos. |
| **CLIENTE NX \_ LWM2M \_ \_ DTLS \_ TERMINA \_ TIMEOUT** | Especifica o tempo máximo para esperar pela conclusão do encerramento do DTLS. O valor predefinido é de 5 segundos. |
| **SEGURANÇA DO CLIENTE NX \_ LWM2M \_ \_ MAX SERVER \_ \_ \_ URI** | Especifica o comprimento máximo de um URI do servidor, incluindo o fim do carácter nulo. O valor predefinido é de 128. |
| **SEGURANÇA DO CLIENTE NX \_ LWM2M \_ MAX CHAVE OU \_ \_ \_ \_ \_ \_ IDENTIDADE PÚBLICA** | Especifica o comprimento máximo da chave pública ou identidade para DTLS. O valor predefinido é de 128. |
| **CHAVE PÚBLICA DO SERVIDOR MAX DO SERVIDOR MAX DE SEGURANÇA DO CLIENTE NX \_ LWM2M \_ \_ \_ \_ \_ \_** | Especifica o comprimento máximo da chave pública do servidor para DTLS. O valor predefinido é de 128. |
| **CHAVE SECRETA DE SEGURANÇA DO CLIENTE NX \_ LWM2M \_ \_ \_ \_ \_** | Especifica o comprimento máximo da chave secreta para DTLS. O valor predefinido é de 128. |
| **CLIENTE NX \_ LWM2M \_ \_ \_ ESPERA** | Especifica o número de segundos a esperar antes de iniciar a armadilha de botas. O valor predefinido é 1 segundo. |
| **TEMPO DE VIDA DO CLIENTE NX \_ LWM2M \_ \_ \_** | Especifica o número de segundos para o tempo de vida útil do registo. O valor predefinido é 600 segundos. |
