---
title: Capítulo 2 - Instalação & Utilização do SMP Azure RTOS ThreadX
description: Este capítulo contém uma descrição de várias questões relacionadas com a instalação, configuração e utilização do kernel SMP Azure RTOS ThreadX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cc352ebd7965c84c341d25dfa7bff2671dfb5e66
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550257"
---
# <a name="chapter-2---installation--use-of-azure-rtos-threadx-smp"></a>Capítulo 2 - Instalação & Utilização do SMP Azure RTOS ThreadX

Este capítulo contém uma descrição de várias questões relacionadas com a instalação, configuração e utilização do kernel SMP Azure RTOS ThreadX.

## <a name="host-considerations"></a>Considerações de Anfitrião

O software incorporado é geralmente desenvolvido em computadores anfitriões Windows ou Linux (Unix). Após a compilação da aplicação, ligada e localizada no anfitrião, é descarregada para o hardware alvo para execução.

Normalmente, o download do alvo é feito a partir do depurar da ferramenta de desenvolvimento. Após o download, o depurante é responsável por fornecer controlo de execução de alvos (ir, parar, quebrar, etc.) bem como aceder aos registos de memória e processador.

A maioria dos depurares de ferramentas de desenvolvimento comunicam com o hardware-alvo através de ligações de depuro on-chip (TOC), tais como JTAG (IEEE 1149.1) e Modo de Depuramento de Fundo (BDM). Os debuggers também comunicam com o hardware alvo através de ligações In-Circuit Emulation (ICE). As ligações OCD e ICE fornecem soluções robustas com uma intrusão mínima no software residente alvo.

Quanto aos recursos utilizados no hospedeiro, o código fonte para ThreadX SMP é entregue em formato ASCII e requer aproximadamente 1 MBytes de espaço no disco rígido do computador anfitrião.

> [!IMPORTANT]
> Por favor, reveja o ficheiro **readme_threadx.txt** fornecido para obter considerações e opções adicionais do sistema de anfitriões.

## <a name="target-considerations"></a>Considerações-alvo

O ThreadX SMP requer entre 2 KBytes e 20 KBytes de Memória Única (ROM) no alvo. São necessários mais 1 a 2 KBytes da Memória de Acesso Aleatório (RAM) do alvo para a pilha de sistema SMP ThreadX e outras estruturas de dados globais.

Para funções relacionadas com temporizadores, como intervalos de chamada de serviço, corte de tempo e temporizadores de aplicação para funcionar, o hardware-alvo subjacente deve fornecer uma fonte de interrupção periódica. Se o processador tiver esta capacidade, é utilizado pela ThreadX SMP. Caso contrário, se o processador-alvo não tiver a capacidade de gerar uma interrupção periódica, o hardware do utilizador deve forneca-lo. A configuração e configuração da interrupção do temporizador está tipicamente localizada no ficheiro de montagem ***tx_initialize_low_level*** na distribuição ThreadX SMP.

> [!IMPORTANT]
> O ThreadX SMP continua funcional mesmo que não exista uma fonte de interrupção periódica do temporizador disponível. No entanto, nenhum dos serviços relacionados com o temporizador está funcional. Por favor, reveja o ficheiro **readme_threadx.txt** fornecido para quaisquer considerações e/ou opções adicionais do sistema de anfitriões.

## <a name="product-distribution"></a>Distribuição de Produtos

O conteúdo exato do disco de distribuição depende do processador-alvo, das ferramentas de desenvolvimento e do pacote SMP da ThreadX adquirido. No entanto, o seguinte é uma lista de vários ficheiros importantes que são comuns à maioria das distribuições de produtos:

### <a name="threadx_express_startuppdf"></a>ThreadX_Express_Startup.pdf

Este PDF fornece um procedimento simples e de quatro etapas para que o ThreadX SMP esteja a funcionar num processador/placa-alvo específico e em ferramentas de desenvolvimento específicas.

### <a name="readme_threadxtxt"></a>readme_threadx.txt

Ficheiro de texto contendo informações específicas sobre a porta ThreadX SMP, incluindo informações sobre o processador-alvo e as ferramentas de desenvolvimento.

| Ferramenta | Descrição |
| -------------- | ------------------------------------------------------------------------------------------------- |
| **tx_api.h**  | Ficheiro de cabeçalho C contendo todos os equacionares do sistema, estruturas de dados e protótipos de serviço.             |
| **tx_port.h** | Ficheiro de cabeçalho C contendo todas as definições e estruturas específicas de dados de desenvolvimento e de destino. |
|**demo_threadx.c**| Ficheiro C contendo um pequeno pedido de demonstração.|
|**tx.a (ou tx.lib)**| Versão binária da biblioteca ThreadX SMP C que é distribuída com o pacote *padrão.*|

> [!IMPORTANT]
> Todos os nomes dos ficheiros estão em minúsculas. Esta convenção de nomeação facilita a conversão dos comandos para plataformas de desenvolvimento Linux (Unix).

## <a name="threadx-smp-installation"></a>Instalação SMP ThreadX

A instalação do ThreadX SMP é simples. Consulte o ficheiro ***ThreadX_Express_Startup.pdf** _ e o ficheiro _ *_readme_threadx.txt_** para obter informações específicas sobre a instalação do ThreadX SMP para o seu ambiente específico.

> [!IMPORTANT]
> Certifique-se de que faz uma reserva do disco de distribuição ThreadX SMP e o armazena num local seguro.

> [!IMPORTANT]
> O software da aplicação precisa de acesso ao ficheiro da biblioteca ThreadX SMP (normalmente **tx.a** ou **tx.lib)** e o C inclui ficheiros **tx_api.h** e **tx_port.h**. Isto é conseguido quer estabelecendo o caminho adequado para as ferramentas de desenvolvimento, quer copiando estes ficheiros para a área de desenvolvimento de aplicações.

## <a name="using-threadx-smp"></a>Utilização de SMP ThreadX

A utilização de SMP ThreadX é fácil. Basicamente, o código de aplicação deve incluir ***tx_api.h** _ durante a compilação e ligação com a biblioteca de tempo de execução ThreadX SMP _*_tx.a_*_ (ou _*_tx.lib)_**.

São necessários quatro passos para a construção de uma aplicação SMP ThreadX:

Inclua o ficheiro ***tx_api.h*** em todos os ficheiros de aplicações que utilizam serviços SMP da ThreadX ou estruturas de dados.

Crie a função padrão C ***main** _ . Esta função deve eventualmente chamar _ *_tx_kernel_enter_** para iniciar o ThreadX SMP. A inicialização específica da aplicação que não envolva o ThreadX SMP pode ser adicionada antes de introduzir o núcleo.

> [!IMPORTANT]
> A função de entrada ThreadX SMP **tx_kernel_enter** não regressa. Por isso, certifique-se de que não escame quaisquer chamadas de processamento ou função após a sua.

Crie a função ***tx_application_define.*** É aqui que os recursos iniciais do sistema são criados. Exemplos de recursos do sistema incluem fios, filas, piscinas de memória, grupos de bandeiras de eventos, mutantes e semáforos.

Compile a fonte de aplicação e ligue-se à biblioteca de tempo de execução ThreadX SMP ***tx.lib***. A imagem resultante pode ser descarregada para o alvo e executada!

## <a name="small-example-system"></a>Sistema de Pequenos Exemplos

O pequeno sistema de exemplo na Figura 1 na página 28 mostra a criação de um único fio com uma prioridade de 3. O fio executa, incrementa um contador, em seguida, dorme por um tique-taque do relógio. Este processo continua para sempre.

```c
#include              "tx_api.h"

unsigned long         my_thread_counter = 0;
TX_THREAD             my_thread;

main( )
{
      /* Enter the ThreadX SMP kernel. */
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

Embora este seja um exemplo simples, fornece um bom modelo para o desenvolvimento real de aplicações. Mais uma vez, consulte o ***readme_threadx.txt*** arquivar para mais detalhes.

## <a name="troubleshooting"></a>Resolução de problemas

Cada porta SMP ThreadX é entregue com uma aplicação de demonstração. É sempre uma boa ideia pôr o sistema de demonstração a funcionar primeiro - seja em hardware de alvo real ou em ambiente simulado.

> [!IMPORTANT]
> Consulte o ficheiro **readme_threadx.txt** fornecido com a distribuição para obter mais detalhes sobre o sistema de demonstração.

Se o sistema de demonstração não funcionar corretamente, são algumas dicas de resolução de problemas:

  - Determina quanto da demonstração está a correr.

  - Aumente os tamanhos das pilhas (isto é mais importante no código de aplicação real do que na demonstração).

  - Reconstruir a biblioteca ThreadX SMP com TX_ENABLE_STACK_CHECKING definida. Isto permitirá a verificação da pilha SMP threadx incorporada.

  - Contornar temporariamente quaisquer alterações recentes para ver se o problema desaparece ou muda. Estas informações devem ser úteis para apoiar os engenheiros.

Siga os procedimentos descritos em "What We Need From You" na página 12 para enviar as informações recolhidas a partir das etapas de resolução de problemas.

## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração ao construir a biblioteca ThreadX SMP e a aplicação utilizando o ThreadX SMP. As opções abaixo podem ser definidas na fonte de aplicação, na linha de comando ou dentro do ***ficheiro tx_user.h.***

> [!IMPORTANT]
> As opções definidas em **tx_user.h** só são aplicadas se a aplicação e a biblioteca ThreadX SMP forem construídas com **TX_INCLUDE_USER_DEFINE_FILE** definidas.

### <a name="smallest-configuration"></a>Configuração mais pequena
Para o menor tamanho de código, devem ser consideradas as seguintes opções de configuração ThreadX SMP (na ausência de todas as outras opções):

- TX_DISABLE_ERROR_CHECKING
- TX_DISABLE_PREEMPTION_THRESHOLD
- TX_DISABLE_NOTIFY_CALLBACKS 
- TX_DISABLE_REDUNDANT_CLEARING 
- TX_DISABLE_STACK_FILLING 
- TX_NOT_INTERRUPTABLE 
- TX_TIMER_PROCESS_IN_ISR

### <a name="fastest-configuration"></a>Configuração mais rápida 
Para a execução mais rápida, as mesmas opções de configuração utilizadas para a Configuração Mais Pequena anteriormente, mas com esta opção também considerada:

- TX_REACTIVATE_INLINE

Reveja o ficheiro ***readme_threadx.txt*** para obter opções adicionais para a sua versão específica do ThreadX SMP. As opções de configuração detalhadas são descritas a partir da página 28.

### <a name="global-time-source"></a>Fonte global do tempo  
Para outros produtos Azure RTOS (FileX, NetX, GUIX, USBX, etc.), a ThreadX SMP define o número de carraças de temporizador ThreadX SMP que representam um segundo. Outros derivam dos seus requisitos de tempo com base nesta constante. Por predefinição, o valor é de 100, assumindo uma interrupção periódica de 10ms. O utilizador pode sobrepor-se a este valor definindo TX_TIMER_TICKS_PER_SECOND com o valor pretendido em ***tx_port.h*** ou dentro do IDE ou linha de comando.

### <a name="detailed-configuration-options"></a>Opções de configuração detalhadas

- **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** : Quando definido, permite a recolha de informações de desempenho em piscinas de blocos. Por padrão, esta opção não está definida.
- **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** : Quando definido, permite a recolha de informações de desempenho nas piscinas byte. Por padrão, esta opção não está definida.
- **TX_DISABLE_ERROR_CHECKING**: Contorna a verificação básica de erros de chamada de serviço. Quando definido na fonte de aplicação, toda a verificação básica de erros de parâmetros é desativada. Isto pode melhorar o desempenho em até 30% e também reduzir o tamanho da imagem.

> [!NOTE]
> *Só é seguro desativar a verificação de erros se a aplicação pode garantir absolutamente que todos os parâmetros de entrada são sempre válidos em todas as circunstâncias, incluindo parâmetros de entrada derivados da entrada externa. Se a entrada inválida for fornecida à API com verificação de erros desativada, o comportamento resultante é indefinido e pode resultar em corrupção de memória ou falha no sistema.*

> [!NOTE]
> *Os valores de retorno da API da ThreadX SMP não afetados pela verificação de erros incapacitantes são listados em negrito na secção "Valores de retorno" de cada descrição da API no Capítulo 4. Os valores de devolução não-boles são nulos se a verificação de erros for desativada utilizando a opção TX_DISABLE_ERROR_CHECKING.*
- **TX_DISABLE_NOTIFY_CALLBACKS** : Quando definido, desativa as chamadas de notificação de vários objetos SMP ThreadX. A utilização desta opção reduz ligeiramente o tamanho do código e melhora o desempenho. Por padrão, esta opção não está definida.
- **TX_DISABLE_PREEMPTION_THRESHOLD** : Quando definido, desativa a função limiar de pré-edição e reduz ligeiramente o tamanho do código e melhora o desempenho. É claro que as capacidades de retenção de prisões preventivas já não estão disponíveis. Por padrão, esta opção não está definida.
- **TX_DISABLE_REDUNDANT_CLEARING** : Quando definido, remove a lógica para rubricar as estruturas globais de dados da ThreadX SMP para zero. Isto só deve ser utilizado se o código de inicialização do compilador definir todos os dados globais C não inicializados para zero. A utilização desta opção reduz ligeiramente o tamanho do código e melhora o desempenho durante a inicialização. Por padrão, esta opção não está definida.
- **TX_DISABLE_STACK_FILLING** : Quando definido, desativa a colocação do valor 0xEF em cada byte da pilha de cada fio quando criado. Por padrão, esta opção não está definida.
- **TX_ENABLE_EVENT_TRACE** : Quando definido, o ThreadX SMP permite o código de recolha de eventos para a criação de um tampão de traço TraceX. Consulte o Manual do Utilizador TraceX para obter mais detalhes.
- **TX_ENABLE_STACK_CHECKING** : Quando definido, permite a verificação do tempo de execução da ThreadX SMP, que inclui a análise da quantidade de pilhas utilizadas e o exame das "cercas" do padrão de dados antes e depois da área da pilha. Se for detetado um erro de pilha, o manipulador de erros da pilha de aplicação registado é chamado. Esta opção resulta num ligeiro aumento da sobrecarga e do tamanho do código. Reveja o **_tx_- thread_stack_error_notify_** API para obter mais informações. Por padrão, esta opção não está definida.
- **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** : Quando definido, permite a recolha de informações de desempenho em grupos de bandeiras de eventos. Por padrão, esta opção não está definida.
- **TX_INLINE_THREAD_RESUME_SUSPEND** : Quando definido, o ThreadX SMP melhora as **_chamadas tx_thread_resume_*_ e _*_tx_thread_suspend_** API através de código de linha. Isto aumenta o tamanho do código, mas melhora o desempenho destas duas chamadas API.
- **TX_MAX_PRIORITIES** : Define os níveis prioritários para o ThreadX SMP. Os valores legais variam entre 32 e 1024 (inclusive) e devem ser igualmente divisíveis até 32. O aumento do número de níveis prioritários apoiados aumenta o uso da RAM em 128 bytes para cada grupo de 32 prioridades. No entanto, existe apenas um efeito negligenciável no desempenho. Por padrão, este valor é definido para 32 níveis prioritários.
- **TX_MINIMUM_STACK** : Define o tamanho mínimo da pilha (em bytes). É utilizado para verificação de erros quando os fios são criados. O valor predefinido é específico da porta e encontra-se em **_tx_port.h._**
- **TX_MISRA_ENABLE** : Quando definido, a ThreadX SMP utiliza convenções compatíveis com o MISRA C. Consulte a **_ThreadX_MISRA_Compliance.pdf_** para mais detalhes.
- **TX_MUTEX_ENABLE_PERFORMANCE_INFO** : Quando definido, permite a recolha de informações de desempenho sobre os mutantes. Por padrão, esta opção não está definida.
- **TX_NO_TIMER** : Quando definido, a lógica do temporizador ThreadX SMP está completamente desativada. Isto é útil nos casos em que as funcionalidades do temporizador ThreadX SMP (sono de rosca, intervalos de tempo da API, corte de tempo e temporizadores de aplicação) não são utilizadas.
- **TX_NOT_INTERRUPTABLE** : Quando definido, o ThreadX SMP não tenta minimizar o tempo de bloqueio de interrupção. Isto resulta numa execução mais rápida, mas aumenta ligeiramente o tempo de bloqueio da interrupção.
- **TX_QUEUE_ENABLE_PERFORMANCE_INFO** : Quando definido, permite a recolha de informações de desempenho nas filas. Por padrão, esta opção não está definida.
- **TX_REACTIVATE_INLINE** : Quando definido, executa a reativação dos temporizadores ThreadX SMP em linha em vez de utilizar uma chamada de função. Isto melhora o desempenho, mas aumenta ligeiramente o tamanho do código. Por padrão, esta opção não está definida.
- **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** : Quando definido, permite a recolha de informações de desempenho sobre semáforos. Por padrão, esta opção não está definida.
- **TX_THREAD_ENABLE_PERFORMANCE_INFO** : Quando definido, permite a recolha de informações de desempenho sobre fios. Por padrão, esta opção não está definida.
- **TX_THREAD_SMP_CORE_MASK** : Define a máscara do mapa bit para exclusão do CORE. Por exemplo, um ambiente de 4 núcleos tem um valor de 0xF para esta definição.
- **TX_THREAD_SMP_DEBUG_ENABLE** : Quando definido, a informação de depurar ThreadX SMP é guardada num tampão circular.
- **TX_THREAD_SMP_DYNAMIC_CORE_MAX** : Quando definido, permite o número máximo dinâmico de núcleos que podem ser ajustados no tempo de execução.
- **TX_THREAD_SMP_EQUAL_PRIORITY** : Quando definido, o ThreadX SMP apenas programa linhas de prioridade iguais em paralelo. Isto deve ser definido antes da construção da biblioteca ThreadX SMP.
- **TX_THREAD_SMP_INTER_CORE_INTERRUPT** : Quando definido, o ThreadX SMP gera interrupções inter-core.
- **TX_THREAD_SMP_MAX_CORES** : Define o número máximo de núcleos.
- **TX_THREAD_SMP_ONLY_CORE_0_DEFAULT** : Quando definido, o ThreadX SMP predefine todos os fios e temporizadores para executar apenas no núcleo 0 por predefinição. A aplicação pode anular esta questão chamando as APIs de exclusão de núcleo. Isto deve ser definido antes da construção da biblioteca ThreadX SMP.
- **TX_THREAD_SMP_WAKEUP_LOGIC** : Quando definido, invoca-se o macro de aplicação para despertar o núcleo "i". Isto deve ser definido antes da inclusão do **_tx_port.h._**
- **TX_THREAD_SMP_WAKEUP(i)** : Define um macro de aplicação para despertar o núcleo "i". Isto deve ser definido antes da inclusão do **_tx_port.h._**
- **TX_TIMER_ENABLE_PERFORMANCE_INFO** : Quando definido, permite a recolha de informações de desempenho nos temporizadores. Por padrão, esta opção não está definida.
- **TX_TIMER_PROCESS_IN_ISR** : Quando definido, elimina o fio do temporizador do sistema interno para ThreadX SMP. Isto resulta numa melhoria do desempenho em eventos temporizadores e requisitos de RAM mais pequenos porque a pilha de temporizador e o bloco de controlo já não são necessários. No entanto, a utilização desta opção move todo o processamento de expiração do temporizador para o nível ISR do temporizador. Por padrão, esta opção não está definida.

    > [!NOTE]
    > Estes serviços autorizados a partir de temporizadores não podem ser permitidos a partir de ISRs, pelo que não podem ser permitidos na utilização desta opção.

- **TX_TIMER_THREAD_PRIORITY** : Define a prioridade do fio temporizador interno do sistema ThreadX SMP. O valor predefinido é prioridade 0 — a maior prioridade em ThreadX SMP. O valor predefinido é definido em **_tx_port.h._**
- **TX_TIMER_THREAD_STACK_SIZE** : Define o tamanho da pilha (in bytes) do fio temporizador interno do sistema ThreadX SMP. Este fio processa todos os pedidos de sono de linha, bem como todos os intervalos de chamada de serviço. Além disso, todas as rotinas de chamada do temporizador de aplicação são invocadas a partir deste contexto. O valor predefinido é específico da porta e encontra-se em **_tx_port.h._**

## <a name="threadx-smp-version-id"></a>ID da versão SMP Threadx

O ID da versão ThreadX SMP pode ser encontrado no ficheiro ***readme_threadx.txt** _ . Este ficheiro também contém um histórico de versão da porta correspondente. O software de aplicação pode obter a versão ThreadX SMP examinando a cadeia global *_ _ _tx_version_id._**