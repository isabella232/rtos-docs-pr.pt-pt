---
title: Capítulo 1 - Kit de Introdução ao Perfil de Execução
description: Este capítulo contém uma introdução ao Azure RTOS ThreadX Execution Profile Kit (EPK).
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7d30676437535229ad5bdbca10dcc9ca009d6e74
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377655"
---
# <a name="chapter-1--introduction-to-the-execution-profile-kit"></a>Capítulo 1 Introdução ao Kit de Perfil de Execução

O Kit de Perfil de Execução ThreadX (EPK) fornece uma infraestrutura para aplicações para acompanhar dinamicamente o tempo de execução dos fios, as rotinas de serviço de interrupção (ISRs) e as condições do sistema inativos. Isto é especialmente útil para otimizar e sintonizar a aplicação para o máximo desempenho. No entanto, trata-se também de uma valiosa ajuda ao depurg.

O EPK baseia-se em \" ganchos \" incorporados na lógica de agendamento ThreadX no código de montagem que são chamados na entrada de thread, saída de fio, entrada ISR e saída ISR. As rotinas EPK calculam o tempo entre tais eventos e armazenam o tempo delta em variáveis globais, bem como membros do bloco de controlo **TX_THREAD.**

> [!NOTE]
> *O desenvolvedor é livre de modificar ou mesmo substituir estas funções de gancho pela sua própria lógica para alternar pinos de I/O de modo a fornecer visibilidade de hardware a uma aplicação ThreadX em execução*.

## 

## <a name="epk-requirements"></a>Requisitos da EPK

O EPK requer threadX 6.0 (ou superior) para funcionar. O EPK também requer uma \" \" resolução razoável, aumentando a fonte de tempo de hardware. A resolução mais razoável seria normalmente algo numa escala de microssessesse segundo. Se a resolução for demasiado grande, os contadores EPK irão esgotar-se demasiado rapidamente. Pelo contrário, se a resolução for demasiado pequena, não é possível um calendário exato. A fonte de tempo de aplicação é definida em ***tx_execution_profile.h** _ pela macro _*TX_EXECUTION_TIME_SOURCE**.

O compilador C deve suportar o tipo \" não assinado por muito tempo para \" contadores totais não assinados de 64 bits. Além disso, o EPK assume que as variáveis globais são inicializadas pelo código de arranque do compilador de tempo de execução. Se não for esse o caso, as variáveis globais definidas em ***tx_execution_profile.c*** devem ser inicializadas para 0 pela aplicação.

## <a name="epk-installation"></a>Instalação EPK

Para instalar o ThreadX EPK, siga os passos abaixo e reconstrua toda a biblioteca e aplicação threadX.

1. Inclua os ficheiros de origem EPK (***tx_execution_profile.h** _ e _*_tx_execution_profile.c)_*_ no seu projeto de construção da biblioteca ThreadX. Estes ficheiros podem estar na [repo Azure RTOS ThreadX](<https://github.com/azure-rtos/threadx>) sob a pasta _ *_utilitário/Execution_Profile_**).

1. In ***tx_port.h** _, defina a macro _ *TX_THREAD_EXTENSION_3** da seguinte forma.
```
    #define TX_THREAD_EXTENSION_3 unsigned long long tx_thread_execution_time_total; \
    unsigned long tx_thread_execution_time_last_start;
```

3. Defina o **TX_EXECUTION_TIME_SOURCE** macro em **_tx_execution_profile.h_** para mapear para a sua fonte de tempo de hardware.

1. Certifique-se de que o ambiente de construção define **TX_ENABLE_EXECUTION_CHANGE_NOTIFY** de modo a que os ganchos de agendamento sejam chamados a partir do código de montagem ThreadX.

1. Se desejar utilizar uma fonte de tempo de 64 bits, por favor reveja o ficheiro ***tx_execution_profile.h*** para obter instruções sobre como o conseguir.

1. Reconstruir toda a biblioteca e aplicação para que todas estas opções sejam devidamente compiladas.

Está agora pronto a usar o EPK com a sua aplicação.

##  <a name="epk-example"></a>Exemplo da EPK 

Segue-se um exemplo de EPK a ser usado numa demonstração padrão da ThreadX, configurada com uma fonte de temporizador de 32 bits que incrementa 7,2 vezes por microsegundo. 

A **macro TX_EXECUTION_TIME_SOURCE** é definida para recolher o registo do temporizador mapeado pela memória em 0xE0001004, da seguinte forma.
```
(EXECUTION_TIME_SOURCE_TYPE) \*((ULONG \*) 0xE0001004)
```

Deixar a demonstração funcionar durante cinco segundos dá os seguintes resultados.

![Resultados de deixar a demonstração correr.](media/demo_results.png)

Uma vez que a demonstração padrão da ThreadX não tem tempo de marcha lenta (os fios 1 e 2 funcionam continuamente), o EPK reporta corretamente zero durante o tempo de marcha lenta. Os valores totais de tempo e rosca do ISR podem ser divididos por 7.2, a fim de obter os microsegundos para cada categoria de execução. O EPK também fornece APIs para aceder a estas informações (consulte por favor [o Capítulo 2](chapter2.md)).