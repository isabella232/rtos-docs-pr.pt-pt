---
title: Capítulo 2 - Instalação e Utilização do Azure RTOS ThreadX
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do kernel Azure RTOS ThreadX de alto desempenho.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a88dc75c3b01e8054f72b3e1475791f064eac0ded02b22ccd18dd46da8c7200a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785044"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-threadx"></a>Capítulo 2 - Instalação e Utilização do Azure RTOS ThreadX

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do kernel Azure RTOS ThreadX de alto desempenho.

## <a name="host-considerations"></a>Considerações de Anfitrião

O software incorporado é geralmente desenvolvido em computadores de Windows ou Linux (Unix). Após a compilação da aplicação, ligada e localizada no anfitrião, é descarregada para o hardware alvo para execução.

Normalmente, o download do alvo é feito a partir do depurar da ferramenta de desenvolvimento. Após o download ter terminado, o depurante é responsável por fornecer controlo de execução de alvo (ir, parar, quebrar, etc.) bem como aceder aos registos de memória e processador.

A maioria dos depurares de ferramentas de desenvolvimento comunicam com o hardware-alvo através de ligações de depuro on-chip (TOC), tais como JTAG (IEEE 1149.1) e Modo de Depuramento de Fundo (BDM). Os debuggers também comunicam com o hardware alvo através de ligações In-Circuit Emulation (ICE). As ligações OCD e ICE fornecem soluções robustas com uma intrusão mínima no software residente alvo.

Quanto aos recursos utilizados no hospedeiro, o código fonte da ThreadX é entregue em formato ASCII e requer aproximadamente 1 MByte de espaço no disco rígido do computador anfitrião.

## <a name="target-considerations"></a>Considerações-alvo

A ThreadX requer entre 2 KBytes e 20 KBytes de Memória Apenas de Leitura (ROM) no alvo. Também requer mais 1 a 2 KBytes da Memória de Acesso Aleatório (RAM) do alvo para a pilha do sistema ThreadX e outras estruturas de dados globais.

Para funções relacionadas com temporizadores, como intervalos de chamada de serviço, corte de tempo e temporizadores de aplicação para funcionar, o hardware-alvo subjacente deve fornecer uma fonte de interrupção periódica. Se o processador tiver esta capacidade, é utilizado pela ThreadX. Caso contrário, se o processador-alvo não tiver a capacidade de gerar uma interrupção periódica, o hardware do utilizador deve forneca-lo. A configuração e configuração da interrupção do temporizador está tipicamente localizada no ficheiro de montagem ***tx_initialize_low_level*** na distribuição ThreadX.

> [!NOTE]
> *O ThreadX continua funcional mesmo que não exista uma fonte de interrupção periódica do temporizador disponível. No entanto, nenhum dos serviços relacionados com o temporizador está funcional.*

## <a name="product-distribution"></a>Distribuição de Produtos

A Azure RTOS ThreadX pode ser obtido a partir do nosso repositório de código de fonte pública em <https://github.com/azure-rtos/threadx/> .

Segue-se uma lista de vários ficheiros importantes no repositório.

| Nome de arquivo | Description |
|------------------- | ----------- |
| **tx_api.h**                      | Ficheiro de cabeçalho C contendo todos os equacionares do sistema, estruturas de dados e protótipos de serviço.                                                             |
| **tx_port.h**                     | Ficheiro de cabeçalho C contendo todas as definições e estruturas específicas de dados de desenvolvimento e de destino.                                                 |
| **demo_threadx.c**                | Ficheiro C contendo um pequeno pedido de demonstração.                                                                                                       |
| **tx.a (ou tx.lib)**              | Versão binária da biblioteca ThreadX C que é distribuída com o pacote *padrão.*                                                          |
|                                   |                                                                                                                                                   |

>[!NOTE]
>*Todos os nomes dos ficheiros estão em minúsculas. Esta convenção de nomeação facilita a conversão dos comandos para plataformas de desenvolvimento Linux (Unix).*

## <a name="threadx-installation"></a>Instalação ThreadX

A ThreadX é instalada clonando o repositório GitHub à sua máquina local. Segue-se a sintaxe típica para criar um clone do repositório ThreadX no seu PC.

```c
    git clone https://github.com/azure-rtos/threadx
```

Em alternativa, pode descarregar uma cópia do repositório utilizando o botão de descarregamento na página principal GitHub.

Também encontrará instruções para a construção da biblioteca ThreadX na primeira página do repositório online.

> [!NOTE]
> *O software de aplicação precisa de acesso ao ficheiro da biblioteca ThreadX (geralmente **tx.a** ou **tx.lib)** e o C inclui ficheiros **_tx_api.h_* _ e _*_tx_port.h_*_. Isto é conseguido quer estabelecendo o caminho adequado para as ferramentas de desenvolvimento, quer copiando estes ficheiros para o desenvolvimento da aplicação area._

## <a name="using-threadx"></a>Usando ThreadX

Para utilizar o ThreadX, o código de aplicação deve incluir ***tx_api.h** _ durante a compilação e ligação com a biblioteca de tempo de execução ThreadX _*_tx.a_*_ (ou _*_tx.lib_**).

São necessários quatro passos para a construção de uma aplicação ThreadX.

1. Inclua o ficheiro ***tx_api.h*** em todos os ficheiros de aplicações que utilizam serviços da ThreadX ou estruturas de dados.

1. Crie a função padrão C ***main** _ . Esta função deve eventualmente chamar _ *_tx_kernel_enter_** para iniciar a ThreadX. A inicialização específica da aplicação que não envolva o ThreadX pode ser adicionada antes de introduzir o núcleo.

      > [!IMPORTANT]
      > *A função de entrada ThreadX ***tx_kernel_enter** _ não volta. Por isso, certifique-se de que não escame quaisquer chamadas de processamento ou função após it._

1. Crie a função ***tx_application_define.*** É aqui que os recursos iniciais do sistema são criados. Exemplos de recursos do sistema incluem fios, filas, piscinas de memória, grupos de bandeiras de eventos, mutantes e semáforos.

1. Compile a fonte de aplicação e ligue-se à biblioteca de tempo de execução ThreadX ***tx.lib***. A imagem resultante pode ser descarregada para o alvo e executada!

## <a name="small-example-system"></a>Sistema de Pequenos Exemplos

O pequeno sistema de exemplo na Figura 1 mostra a criação de um único fio com uma prioridade de 3. O fio executa, incrementa um contador, em seguida, dorme por um tique-taque do relógio.
Este processo continua para sempre.

```c
#include "tx_api.h"
unsigned long my_thread_counter = 0;
TX_THREAD my_thread;
main( )
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter( );
}
void tx_application_define(void *first_unused_memory)
{
    /* Create my_thread! */
    tx_thread_create(&my_thread, "My Thread",
    my_thread_entry, 0x1234, first_unused_memory, 1024,
    3, 3, TX_NO_TIME_SLICE, TX_AUTO_START);
}
void my_thread_entry(ULONG thread_input)
{
    /* Enter into a forever loop. */
    while(1)
    {
        /* Increment thread counter. */
        my_thread_counter++;
        /* Sleep for 1 tick. */
        tx_thread_sleep(1);
    }
}
```

**FIGURA 1. Modelo para desenvolvimento de aplicações**

Embora este seja um exemplo simples, fornece um bom modelo para o desenvolvimento real de aplicações.

## <a name="troubleshooting"></a>Resolução de problemas

Cada porta ThreadX é entregue com uma aplicação de demonstração. É sempre uma boa ideia pôr o sistema de demonstração a funcionar primeiro - seja em hardware de alvo real ou em ambiente simulado.

Se o sistema de demonstração não funcionar corretamente, as seguintes são algumas dicas de resolução de problemas.

1. Determina quanto da demonstração está a decorrer.
1. Aumente os tamanhos das pilhas (isto é mais importante no código de aplicação real do que na demonstração).
1. Reconstruir a biblioteca ThreadX com TX_ENABLE_STACK_CHECKING definida. Isto permite a verificação da pilha threadx incorporada.
1. Contornar temporariamente quaisquer alterações recentes para ver se o problema desaparece ou muda. Estas informações devem ser úteis para apoiar os engenheiros.

Siga os procedimentos descritos no "[Centro de Apoio](about-this-guide.md#customer-support-center)ao Cliente " para enviar as informações recolhidas a partir das etapas de resolução de problemas.

## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração ao construir a biblioteca ThreadX e a aplicação utilizando o ThreadX. As opções abaixo podem ser definidas na fonte de aplicação, na linha de comando ou dentro do ***ficheiro tx_user.h.***

> [!IMPORTANT]
> *As opções definidas em ***tx_user.h** _ só são aplicadas se a aplicação e a biblioteca ThreadX forem construídas com _ *TX_INCLUDE_USER_DEFINE_FILE** definidas.*

### <a name="smallest-configuration"></a>Configuração mais pequena

Para o menor tamanho do código, devem ser consideradas as seguintes opções de configuração ThreadX (na ausência de todas as outras opções).

```c
TX_DISABLE_ERROR_CHECKING
TX_DISABLE_PREEMPTION_THRESHOLD
TX_DISABLE_NOTIFY_CALLBACKS
TX_DISABLE_REDUNDANT_CLEARING
TX_DISABLE_STACK_FILLING
TX_NOT_INTERRUPTABLE
TX_TIMER_PROCESS_IN_ISR
```

### <a name="fastest-configuration"></a>Configuração mais rápida

Para a execução mais rápida, as mesmas opções de configuração usadas para a Configuração Mais Pequena anteriormente, mas com estas opções também consideradas.

```c
TX_REACTIVATE_INLINE
TX_INLINE_THREAD_RESUME_SUSPEND
```

[São descritas opções de configuração detalhadas.](#detailed-configuration-options)

### <a name="global-time-source"></a>Fonte global do tempo

Para outros Microsoft Azure produtos RTOS (FileX, NetX, GUIX, USBX, etc.), a ThreadX define o número de carraças de temporizador ThreadX que representam um segundo. Outros derivam dos seus requisitos de tempo com base nesta constante. Por predefinição, o valor é de 100, assumindo uma interrupção periódica de 10ms. O utilizador pode sobrepor-se a este valor definindo TX_TIMER_TICKS_PER_SECOND com o valor pretendido em ***tx_port.h*** ou dentro do IDE ou linha de comando.

### <a name="detailed-configuration-options"></a>Opções de configuração detalhadas

**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**

Quando definida, esta opção permite a recolha de informações de desempenho em piscinas byte. Por padrão, esta opção não está definida.

**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**

Quando definida, esta opção permite a recolha de informações de desempenho em piscinas byte. Por padrão, esta opção não está definida.

**TX_DISABLE_ERROR_CHECKING**

Contorna a verificação básica de erros de chamada de serviço. Quando definido na fonte de aplicação, toda a verificação básica de erros de parâmetros é desativada. Isto pode melhorar o desempenho em até 30% e também reduzir o tamanho da imagem.

> [!NOTE]
> *Só é seguro desativar a verificação de erros se a aplicação pode garantir absolutamente que todos os parâmetros de entrada são sempre válidos em todas as circunstâncias, incluindo parâmetros de entrada derivados da entrada externa. Se a entrada inválida for fornecida à API com verificação de erros desativada, o comportamento resultante é indefinido e pode resultar em corrupção de memória ou falha no sistema.*

> [!NOTE]
> *Os valores de devolução da API threadX não afetados pela verificação de erros incapacitantes estão listados em negrito na secção "Valores de Retorno" de cada descrição da API no Capítulo 4. Os valores de devolução não-boles são nulos se a verificação de erros for desativada utilizando a opção TX_DISABLE_ERROR_CHECKING.*

**TX_DISABLE_NOTIFY_CALLBACKS**

Quando definido, desativa as chamadas de notificação de vários objetos ThreadX. A utilização desta opção reduz ligeiramente o tamanho do código e melhora o desempenho. Por padrão, esta opção não está definida.

**TX_DISABLE_PREEMPTION_THRESHOLD**

Quando definido, desativa a função limiar de pré-edição e reduz ligeiramente o tamanho do código e melhora o desempenho. É claro que as capacidades de limiar de pré-edição já não estão disponíveis. Por padrão, esta opção não está definida.

**TX_DISABLE_REDUNDANT_CLEARING**

Quando definido, remove a lógica para inicializar as estruturas globais de dados da ThreadX para zero. Isto só deve ser utilizado se o código de inicialização do compilador definir todos os dados globais C não inicializados para zero. A utilização desta opção reduz ligeiramente o tamanho do código e melhora o desempenho durante a inicialização. Por padrão, esta opção não está definida.

**TX_DISABLE_STACK_FILLING**

Quando definido, desativa a colocação do valor 0xEF em cada byte da pilha de cada fio quando criado. Por padrão, esta opção não está definida.

**TX_ENABLE_EVENT_TRACE**

Quando definido, o ThreadX permite o código de recolha do evento para a criação de um tampão de traço TraceX.

**TX_ENABLE_STACK_CHECKING**

Quando definido, permite a verificação da pilha de tempo de execução ThreadX, que inclui a análise da quantidade de pilhas utilizadas e o exame de "cercas" de padrão de dados antes e depois da área da pilha. Se for detetado um erro de pilha, o manipulador de erros da pilha de aplicação registado é chamado. Esta opção resulta num ligeiro aumento da sobrecarga e do tamanho do código. Reveja a função API ***tx_thread_stack_error_notify*** para obter mais informações. Por padrão, esta opção não está definida.

**TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO**

Quando definido, permite a recolha de informações de desempenho em grupos de bandeiras de eventos. Por padrão, esta opção não está definida.

**TX_INLINE_THREAD_RESUME_SUSPEND**

Quando definido, o ThreadX melhora as chamadas ***tx_thread_resume** _ e _ *_tx_thread_suspend_** aPI através de código em linha. Isto aumenta o tamanho do código, mas melhora o desempenho destas duas chamadas API.

**TX_MAX_PRIORITIES**

Define os níveis de prioridade para a ThreadX. Os valores legais variam entre 32 e 1024 (inclusive) e *devem* ser igualmente divisíveis até 32. O aumento do número de níveis prioritários apoiados aumenta o uso da RAM em 128 bytes para cada grupo de 32 prioridades. No entanto, existe apenas um efeito negligenciável no desempenho. Por padrão, este valor é definido para 32 níveis prioritários.

**TX_MINIMUM_STACK**

Define o tamanho mínimo da pilha (em bytes). É utilizado para verificação de erros quando os fios são criados. O valor predefinido é específico da porta e encontra-se em ***tx_port.h***.

**TX_MISRA_ENABLE**

Quando definido, a ThreadX utiliza convenções compatíveis com o MISRA C. Consulte  ***ThreadX_MISRA_Compliance.pdf*** para mais detalhes.

**TX_MUTEX_ENABLE_PERFORMANCE_INFO**

Quando definido, permite a recolha de informações de desempenho sobre mutações. Por padrão, esta opção não está definida.

**TX_NO_TIMER**

Quando definido, a lógica do temporizador ThreadX é completamente desativada. Isto é útil nos casos em que as funcionalidades do temporizador ThreadX (tempo de rosca, intervalos de tempo da API, corte de tempo e temporizadores de aplicação) não são utilizadas. Se **TX_NO_TIMER** for especificado, a opção **TX_TIMER_PROCESS_IN_ISR** também deve ser definida.

**TX_NOT_INTERRUPTABLE**

Quando definido, o ThreadX não tenta minimizar o tempo de bloqueio de interrupção. Isto resulta numa execução mais rápida, mas aumenta ligeiramente o tempo de bloqueio da interrupção.

**TX_QUEUE_ENABLE_PERFORMANCE_INFO**

Quando definido, permite a recolha de informações de desempenho nas filas. Por padrão, esta opção não está definida.

**TX_REACTIVATE_INLINE**

Quando definido, executa a reativação dos temporizadores ThreadX em linha em vez de utilizar uma chamada de função. Isto melhora o desempenho, mas aumenta ligeiramente o tamanho do código. Por padrão, esta opção não está definida.

**TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO**

Quando definido, permite a recolha de informações de desempenho sobre semáforos. Por padrão, esta opção não está definida.

**TX_THREAD_ENABLE_PERFORMANCE_INFO**

Quando definido, permite a recolha de informações de desempenho sobre fios. Por padrão, esta opção não está definida.

**TX_TIMER_ENABLE_PERFORMANCE_INFO**

Quando definido, permite a recolha de informações de desempenho nos temporizadores. Por padrão, esta opção não está definida.

**TX_TIMER_PROCESS_IN_ISR**

Quando definido, elimina o fio do temporizador interno do sistema para o ThreadX. Isto resulta numa melhoria do desempenho em eventos temporizadores e requisitos de RAM mais pequenos porque a pilha de temporizador e o bloco de controlo já não são necessários. No entanto, a utilização desta opção move todo o processamento de expiração do temporizador para o nível ISR do temporizador. Por padrão, esta opção não está definida.

> [!NOTE]
> *Os serviços autorizados a partir de temporizadores não podem ser permitidos a partir de ISRs, pelo que não podem ser permitidos na utilização desta opção.*

**TX_TIMER_THREAD_PRIORITY**

Define a prioridade do fio temporizador interno do sistema ThreadX. O valor predefinido é prioridade 0 — a maior prioridade na ThreadX. O valor predefinido é definido em ***tx_port.h***.

**TX_TIMER_THREAD_STACK_SIZE**

Define o tamanho da pilha (em bytes) do fio temporizador interno do sistema ThreadX. Este fio processa todos os pedidos de sono de linha, bem como todos os intervalos de chamada de serviço. Além disso, todas as rotinas de chamada do temporizador de aplicação são invocadas a partir deste contexto. O valor predefinido é específico da porta e encontra-se em ***tx_port.h***.

## <a name="threadx-version-id"></a>ID da versão ThreadX

O programador pode obter a versão ThreadX a partir do exame do ficheiro ***tx_port.h_** Além disso, este ficheiro também contém um histórico de versão da porta correspondente. O software de aplicação pode obter a versão ThreadX examinando a cadeia global _*_tx_version_id**.
