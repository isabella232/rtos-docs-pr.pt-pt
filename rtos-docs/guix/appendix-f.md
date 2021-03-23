---
title: Apêndice F - SERVIÇOS DE Encadernação RTOS GUIX
description: Saiba mais sobre os serviços de encadernação DO GUIX RTOS.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1d94dbb9d7d53ec3e1900188142974cc981dfea9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827271"
---
# <a name="appendix-f---guix-rtos-binding-services"></a>Apêndice F - SERVIÇOS DE Encadernação RTOS GUIX

O GUIX requer serviços de thread ou tasking, mutex, fila de eventos e serviços de cronometragem prestados pelo RTOS subjacente. Por predefinição, o GUIX está configurado para utilizar o sistema operativo ThreadX em tempo real para fornecer estes serviços. Para colocar o GUIX noutro sistema operativo, o desenvolvedor deve # definir a diretiva pré-processador GX_DISABLE_THREADX_BINDING e reconstruir a biblioteca GUIX para remover as dependências do ThreadX. Além disso, o desenvolvedor terá de fornecer as seguintes definições macro e funções de suporte. Exemplos destas definições macro e funções de suporte podem ser encontrados nos ficheiros gx_system_rtos_bind.h e gx_system_rtos_bind.c, que fornecem um exemplo de integração genérica de rtos.

Macros de Integração do Sistema:

**GX_RTOS_BINDING_INITIALIZE**

Esta macro é invocada durante a inicialização do sistema. O macro deve ser definido para chamar qualquer função necessária para preparar os seus serviços de sistema rtos ou recursos rtos antes da utilização. Esta é a oportunidade da encadernação para preparar os recursos rtos que o GUIX irá utilizar.

**GX_SYSTEM_THREAD_START**

Esta macro é invocada quando a tarefa ou fio GUIX deve começar a executar. Este macro deve ser definido para chamar uma função que iniciará o fio GUIX em funcionamento. O ponto de entrada do fio GUIX é passado para a função chamada. A assinatura da chamada função deve ser

**function_name *UINT*(VOID (thread_entry_point)(VOID));**

Esta função deve voltar GX_SUCCESS se o fio for iniciado com sucesso ou GX_FAILURE.

**GX_EVENT_PUSH**

Esta macro é invocada para empurrar um evento para a fila de eventos FIFO usada pelo GUIX. Ao apresentar um novo rtos, é da sua responsabilidade implementar esta fila de eventos de forma segura. GX_EVENT estruturas devem ser copiadas para esta fila e copiadas para fora desta fila, ou seja, uma fila de ponteiros GX_EVENT não funcionará, uma vez que os eventos GUIX podem ser variáveis automáticas do ponto de vista do produtor do evento. A assinatura da função chamada por esta macro deve ser:

**UINT *function_name* (event_ptr *GX_EVENT);**

Esta função deve voltar GX_SUCCESS se o evento for empurrado para a fila do evento, caso contrário deverá voltar GX_FAILURE.

**GX_EVENT_POP**

Esta macro é invocada para remover o evento da cabeça (mais antiga) da fila do evento GUIX e copiá-lo para o local solicitado. Esta função deve ser capaz de bloquear opcionalmente ou esperar por um evento se não houver eventos na fila do evento. A assinatura da função invocada por esta macro deve ser

UINT function_name(GX_EVENT *put_event, GX_BOOL espera)

Se o parâmetro de espera == GX_TRUE, a função não deve voltar até que um evento seja fornecido. Se o parâmetro de espera for GX_FALSE, a função deve regressar imediatamente com ou sem evento.

Se um evento for recuperado da fila, deve ser copiado para o local put_event e o estado de retorno é GX_SUCCESS. Caso contrário, o estado de devolução deve ser GX_FAILURE.

**GX_EVENT_FOLD**

Esta macro é invocada pelo GUIX para dobrar um evento na fila do evento FIFO. Dobrar um evento significa que se um evento do mesmo tipo já existe na fila, essa entrada é atualizada para conter a carga útil do novo evento. Se um evento existente do mesmo tipo não for encontrado na fila, um novo evento é empurrado para a fila. 

Para encadernações que não podem implementar a função de dobra do evento, é aceitável simplesmente invocar o GX_EVENT_PUSH.

**GX_TIMER_START**

Esta macro é invocada quando o GUIX precisa de receber entrada de temporizador periódico. Esta macro deve invocar um serviço que inicie o serviço de temporizador periódico RTOS de baixo nível. Se o serviço de temporizador RTOS não puder ser facilmente interrompido e iniciado, é aceitável, mas menos eficiente, deixar este serviço sempre em funcionamento.

Quando o serviço de temporizador RTOS de baixo nível expirar periodicamente, a ligação deve chamar a função do sistema GUIX _gx_system_timer_expiration(0); Chamar esta função periodicamente é o que impulsiona os serviços de temporizador de temporizador GUIX de alto nível.

**GX_TIMER_STOP**

Esta macro é invocada quando o GUIX já não necessita de um temporizador periódico (ou seja, não existem temporizadores GUIX ativos em funcionamento). Se o serviço de temporizador RTOS não puder ser facilmente interrompido e iniciado, é aceitável, mas menos eficiente, deixar este serviço em funcionamento e definir este macro para não fazer nada.

**GX_SYSTEM_MUTEX_LOCK**

Esta macro é invocada pelo GUIX durante secções de código críticas para evitar que outra tarefa impeça e modifique estruturas de dados comuns, potencialmente causando corrupção. Esta macro deve chamar uma função que implementa o serviço adequado de bloqueio de recursos RTOS.

Se nunca utilizar quaisquer serviços de API GUIX fora da linha GUIX, pode definir esta macro para não fazer nada.

**GX_SYSTEM_MUTEX_UNLOCK**

Esta macro é invocada no final das secções de código crítico, e deve desbloquear o recurso GUIX utilizando o serviço RTOS subjacente adequado. Se nunca utilizar quaisquer serviços de API GUIX fora da linha GUIX, pode definir esta macro para não fazer nada.

**GX_SYSTEM_TIME_GET**

Este macro deve chamar uma função que devolve o tempo atual do sistema é "ticks do sistema", que é geralmente o número de interrupções de temporizador de baixo nível que ocorreram desde o arranque do sistema. Este serviço é utilizado para calcular a velocidade da caneta touch event para gestos de entrada de toque. A assinatura da função invocada por esta macro deve ser:

**function_name *ULONG*(VOID);**

**GX_CURRENT_THREAD**

Esta macro é invocada para identificar o fio atualmente executado. O serviço chamado por esta macro deve devolver um vazio *, o que significa que o tipo de dados utilizado pelo seu sistema operativo para identificar o fio de execução atual deve ser lançado para um vazio * para ser devolvido ao GUX.

Um exemplo completo de uma ligação genérica de RTOS é implementado no gx_system_rtos_bind.h e gx_system_rtos_bind.c