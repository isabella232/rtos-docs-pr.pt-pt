---
title: Capítulo 2 - Instalação do suporte da ThreadX para ARMv8-M
description: Este capítulo explica como instalar e utilizar o código fonte ThreadX para a arquitetura ARMv8-M.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 085310acd5262226e9ff3af440a5f05268c7799e78eda81334a13b736222b95c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801959"
---
#  <a name="chapter-2--installing-threadx-support-for-armv8-m"></a>Capítulo 2 Instalação do suporte da ThreadX para ARMv8-M

Existem ficheiros de código fonte ThreadX adicionais para suportar a arquitetura ARMv8-M.

Se o ThreadX for executado em modo seguro, estes ficheiros adicionais e APIs não são necessários. Para executar o ThreadX em modo seguro, defina o símbolo **TX_SECURE_EXECUTION** na parte superior do **_tx_port.h_*_ ou na linha de comando ou nas definições do projeto. Certifique-se de que a TX_SECURE_EXECUTION*** está definida para todos os ficheiros c e de montagem. A ThreadX e a aplicação do utilizador serão executadas em modo seguro.

Para executar o ThreadX e a aplicação do utilizador em modo não seguro e suportar funções seguras de segurança, por favor, faça o seguinte.

O ficheiro ***tx_thread_secure_stack.c*** deve ser adicionado à aplicação segura.

Os seguintes ficheiros devem ser adicionados à biblioteca ThreadX.

- ***tx_secure_interface.h***
- ***txe_thread_secure_stack_allocate.c***
- ***txe_thread_secure_stack_free.c***
- ***tx_thread_secure_stack_allocate.s.***
- ***tx_thread_secure_stack_free.s.***

Os dois ficheiros seguintes substituem os ficheiros genéricos na biblioteca ThreadX.

- ***tx_thread_stack_error_handler.c***
- ***tx_thread_stack_error_notify.c***

## <a name="additional-threadx-sources-for-armv8-m"></a>Fontes adicionais da ThreadX para ARMv8-M

Os ficheiros ThreadX adicionais para a arquitetura ARMv8-M TrustZone são descritos abaixo.

  | **Nome do arquivo**                            | **Conteúdos**                                                        |
  |------------------------------------------|---------------------------------------------------------------------|
  | ***tx_secure_interface.h***              | Inclua o ficheiro que define as funções de chamada não seguras threadX. |
  | ***txe_thread_secure_stack_allocate.c*** |  Ficheiro de verificação de erros para a pilha segura alocar API. |
  | ***txe_thread_secure_stack_free.c***     |  Ficheiro de verificação de erros para a API de pilha segura. |
  | ***tx_thread_secure_stack_allocate.s.***  |  Revestimento não seguro para o serviço de atribuição de pilhas seguras. |
  | ***tx_thread_secure_stack_free.s.***      |  Revestimento não seguro para o serviço gratuito de pilha segura. |
  | ***tx_thread_stack_error_handler.c***    |  Manipulador para erros de pilha de fios. |
  | ***tx_thread_stack_error_notify.c***     |  Registar a chamada de notificação para lidar com erros de pilha de fios. |
