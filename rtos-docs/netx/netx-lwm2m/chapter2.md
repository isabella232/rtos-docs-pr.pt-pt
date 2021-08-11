---
title: Capítulo 2 - Instalação e utilização do Azure RTOS NetX LWM2M
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NetX LWM2M.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3ad8963c342e907201074559929f3a7a2d70c9f13e135cd95c9a2e9b224e17cf
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791232"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-lwm2m"></a>Capítulo 2 - Instalação e utilização do Azure RTOS NetX LWM2M

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NetX LWM2M.

## <a name="product-distribution"></a>Distribuição de Produtos

NetX LWM2M está disponível em [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) . O pacote inclui três ficheiros de origem, um inclui ficheiros e um ficheiro PDF que contém este documento, da seguinte forma:

- **nx_lwm2m_client.h:** Ficheiro de cabeçalho para o Cliente NetX LWM2M

- **nx_lwm2m_*.c/h:** Ficheiros C/H Source para NetX LWM2M

- **demo_netx_lwm2m_client.c**: Ficheiro C Fonte para demonstração de clientes NetX LWM2M

- **NetX_LWM2M_User_Guide.pdf**: Descrição em PDF do produto NetX LWM2M

## <a name="netx-lwm2m-installation"></a>Instalação NetX LWM2M

Para utilizar o NetX LWM2M, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX está instalado. Por exemplo, se o NetX for instalado no diretório "*\\ threadx \\ arm7 \\ green*" então os *ficheiros nx_lwm2m&#42;.&#42;* devem ser copiados para este diretório.

## <a name="using-netx-lwm2m"></a>Utilização do NetX LWM2M

A utilização do NetX LWM2M é fácil. Basicamente, o código de aplicação deve incluir *nx_lwm2m_client.h* depois de incluir *tx_api.h* e *nx_api.h,* para utilizar o ThreadX e o NetX. Uma vez *incluído nx_lwm2m_client.h,* o código de aplicação é então capaz de fazer as chamadas de função NetX LWM2M especificadas mais tarde neste guia. O pedido também deve importar os *ficheiros nx_lwm2m&#42;.&#42;* para a biblioteca NetX.

## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração ao construir a biblioteca LWM2M Client e a aplicação utilizando o Cliente LWM2M. As opções de configuração podem ser definidas na fonte de aplicação, na linha de comando, salvo especificação em contrário.

### <a name="nx_lwm2m_client_disable_error_checking"></a>NX_LWM2M_CLIENT_DISABLE_ERROR_CHECKING

Definido, remove o erro básico do Cliente LWM2M verificando a API e melhora o desempenho. Os códigos de devolução da API não afetados pela verificação de erros incapacitantes estão listados em tipo de letra arrojado na definição API.

### <a name="nx_lwm2m_client_disable_float"></a>NX_LWM2M_CLIENT_DISABLE_FLOAT

Definido, remove o suporte dos valores dos números dos pontos flutuantes. Quando desativado, o Cliente LWM2M não pode suportar Recursos com tipo de dados Float.

### <a name="nx_lwm2m_client_disable_float64"></a>NX_LWM2M_CLIENT_DISABLE_FLOAT64

Definido, remove o suporte de valores de ponto flutuante de 64 bits. O Cliente LWM2M ainda pode receber mensagens TLV contendo números flutuantes de 64 bits, mas os valores são convertidos para ponto flutuante de 32 bits para processamento.

### <a name="nx_lwm2m_client_priority"></a>NX_LWM2M_CLIENT_PRIORITY

Especifica a prioridade da linha do Cliente LWM2M. Por predefinição, este valor é definido como 16 para especificar a prioridade 16.

### <a name="nx_lwm2m_client_max_device_errors"></a>NX_LWM2M_CLIENT_MAX_DEVICE_ERRORS

Especifica o número máximo de códigos de erro armazenados pelo Objeto do Dispositivo. O valor predefinido é 8.

### <a name="nx_lwm2m_client_max_security_instances"></a>NX_LWM2M_CLIENT_MAX_SECURITY_INSTANCES

Especifica o número máximo de instâncias de objetos de segurança. O valor predefinido é 2 para suportar um Servidor Bootstrap e um Servidor padrão.

### <a name="nx_lwm2m_client_max_server_instances"></a>NX_LWM2M_CLIENT_MAX_SERVER_INSTANCES

Especifica o número máximo de instâncias de objetos de servidor. O valor predefinido é 1 para suportar um único Servidor padrão.

### <a name="nx_lwm2m_client_max_server_uri"></a>NX_LWM2M_CLIENT_MAX_SERVER_URI

Especifica o comprimento máximo de um URI do servidor, incluindo o carácter nulo. O valor predefinido é de 128.

### <a name="nx_lwm2m_client_max_access_control_instances"></a>NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_INSTANCES

Especifica o número máximo de instâncias de controlo de acesso. O valor predefinido é 0, que desativa o controlo de acesso. Se a aplicação suportar mais de um Servidor LWM2M, o número máximo de Instâncias de Controlo de Acesso deve ser definido para o número máximo de instâncias de objeto que o Cliente LWM2M irá suportar, uma vez que uma Instância de Controlo de Acesso deve ser criada para cada Instância de Objeto (exceto para as Instâncias de Objeto de Segurança).

### <a name="nx_lwm2m_client_max_access_control_acls"></a>NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_ACLS

Especifica o número máximo de recursos ACL por Instância de Controlo de Acesso. O valor predefinido é 4.

### <a name="nx_lwm2m_client_max_notifications"></a>NX_LWM2M_CLIENT_MAX_NOTIFICATIONS

Especifica o número máximo de notificações que o Cliente LWM2M irá suportar. Um Servidor LWM2M pode definir notificações em Objetos, Instâncias de Objetos e Recursos. O valor predefinido é 8.

### <a name="nx_lwm2m_client_max_resources"></a>NX_LWM2M_CLIENT_MAX_RESOURCES

Especifica o número máximo de Recursos por Objeto. O valor predefinido é 32.

### <a name="nx_lwm2m_client_bootstrap_idle_timer"></a>NX_LWM2M_CLIENT_BOOTSTRAP_IDLE_TIMER

Especifica o tempo máximo para esperar pelos pedidos do servidor bootstrap quando a sessão de bootstrap é iniciada antes de abortar a sessão. O valor predefinido é de 60 segundos.

### <a name="nx_lwm2m_client_dtls_start_timeout"></a>NX_LWM2M_CLIENT_DTLS_START_TIMEOUT

Especifica o tempo máximo para esperar pela conclusão do aperto de mão DTLS. O valor predefinido é de 30 segundos.

### <a name="nx_lwm2m_client_dtls_end_timeout"></a>NX_LWM2M_CLIENT_DTLS_END_TIMEOUT

Especifica o tempo máximo para esperar pela conclusão do encerramento do DTLS. O valor predefinido é de 5 segundos.
