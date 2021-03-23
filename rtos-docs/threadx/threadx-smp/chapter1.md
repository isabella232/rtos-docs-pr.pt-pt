---
title: Capítulo 1 - Introdução ao Azure RTOS ThreadX SMP
description: Este capítulo contém uma introdução ao produto e uma descrição das suas aplicações e benefícios.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 67bdb9076272fa3671ec9321baec609b291c04b8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826570"
---
# <a name="chapter-1-introduction-to-azure-rtos-threadx-smp"></a>Capítulo 1: Introdução ao Azure RTOS ThreadX SMP

Azure RTOS ThreadX SMP é um kernel SMP em tempo real de alto desempenho projetado especificamente para aplicações incorporadas. Este capítulo contém uma introdução ao produto e uma descrição das suas aplicações e benefícios.

## <a name="threadx-smp-unique-features"></a>Funcionalidades únicas da ThreadX SMP

A ThreadX SMP traz a tecnologia symmetric multi-processing (SMP) para aplicações incorporadas. Os fios de aplicação ThreadX SMP (de prioridade variável) que estão "PRONTO" a ser executados são dinamicamente atribuídos aos núcleos de processador disponíveis durante o agendamento. Isto resulta num verdadeiro processamento de SMP, incluindo o equilíbrio automático de carga da execução do fio de aplicação em todos os núcleos do processador disponíveis.

Ao contrário de outros núcleos em tempo real, o ThreadX SMP foi concebido para ser versátil — facilmente escalando entre pequenas aplicações baseadas em microcontrolador através daquelas que utilizam poderosos processadores CISC, RISC e DSP.

A ThreadX SMP é escalável com base na sua arquitetura subjacente. Como os serviços da ThreadX SMP são implementados como uma biblioteca C, apenas os serviços realmente utilizados pela aplicação são trazidos para a imagem de tempo de execução. Assim, o tamanho real do ThreadX SMP é completamente determinado pela aplicação. Para a maioria das aplicações, a imagem de instrução do ThreadX SMP varia entre 5 KBytes e 20 KBytes de tamanho.

### <a name="picokernel-architecture"></a>Arquitetura picokernel™ 
Em vez de camadas de núcleos em cima uns dos outros como as arquiteturas tradicionais *de microkernel,* os serviços Da ThreadX SMP ligam-se diretamente ao seu núcleo. Isto resulta no desempenho mais rápido possível de comutação de contexto e chamada de serviço. Chamamos a este design não-matador uma arquitetura *picokernel.*

### <a name="ansi-c-source-code"></a>Código Fonte ANSI C 
ThreadX SMP é escrito principalmente em ANSI C. É necessária uma pequena quantidade de linguagem de montagem para adaptar o núcleo ao processador-alvo subjacente. Este design permite colocar a ThreadX SMP numa nova família de processadores num curto espaço de tempo , normalmente dentro de semanas!

### <a name="advanced-technology"></a>Tecnologia Avançada 
Seguem-se os destaques da tecnologia avançada ThreadX SMP:

  - Arquitetura *picokernel* simples
  - Equilíbrio automático da carga
  - Exclusão do processador por thread
  - Escala automática (pequena pegada)
  - Processamento determinístico
  - Desempenho rápido em tempo real
  - Agendamento preventivo e cooperativo
  - Suporte prioritário de fio flexível (32-1024)
  - Criação dinâmica de objetos de sistema
  - Número ilimitado de objetos do sistema
  - Tratamento de interrupção otimizado
  - Limiar de preempção™
  - Herança prioritária
  - Acorrentamento de eventos™
  - Temporizadores de software rápido
  - Gestão da memória em tempo de execução
  - Monitorização do desempenho em tempo de execução
  - Análise de pilha de tempo de execução
  - Vestígios de sistema incorporado
  - Grande suporte ao processador
  - Vasto suporte de ferramenta de desenvolvimento
  - Completamente endiano neutro

### <a name="not-a-black-box"></a>Não uma caixa preta
A maioria das distribuições de ThreadX SMP incluem o código fonte C completo, bem como o idioma de montagem específico do processador. Isto elimina os problemas da "caixa preta" que ocorrem com muitos núcleos comerciais. Com a ThreadX SMP, os desenvolvedores de aplicações podem ver exatamente o que o kernel está a fazer - não há mistérios!

O código fonte também permite modificações específicas da aplicação. Embora não recomendado, é certamente benéfico ter a capacidade de modificar o núcleo se for absolutamente necessário.

Estas características são especialmente reconfortantes para os desenvolvedores habituados a trabalhar com os seus *próprios núcleos de casa.* Esperam ter código fonte e a capacidade de modificar o núcleo. A ThreadX SMP é o núcleo final para estes desenvolvedores.

### <a name="the-rtos-standard"></a>A Norma RTOS
Devido à sua versatilidade, arquitetura *picokernel* de alto desempenho, tecnologia avançada e portabilidade demonstrada, a ThreadX SMP está implantada em mais de dois mil milhões de dispositivos hoje em dia. Isto faz da ThreadX SMP a norma RTOS para aplicações profundamente incorporadas.

## <a name="safety-certifications"></a>Certificações de Segurança

### <a name="tv-certification"></a>Certificação TÜV  
A ThreadX SMP foi certificada pela SGS-TÜV Saar para utilização em sistemas críticos de segurança, de acordo com o IEC61508 e o IEC-62304. A certificação confirma que a ThreadX SMP pode ser utilizada no desenvolvimento de software relacionado com a segurança para os mais elevados níveis de integridade de segurança da Comissão Eletrotécnica Internacional (IEC) 61508 e IEC 62304, para a "Segurança Funcional dos sistemas eletrónicos de segurança elétricas, eletrónicos e programáveis relacionados com a segurança". A SGS-TÜV Saar, formada através de uma joint venture da SGS-Group alemã e da TÜV Saarland, tornou-se a principal empresa acreditada e independente para testar, auditar, verificar e certificar software incorporado para sistemas relacionados com a segurança em todo o mundo. A norma de segurança industrial IEC 61508, bem como todas as normas que dela derivam, incluindo o IEC 62304, são utilizadas para garantir a segurança funcional de dispositivos médicos eletrónicos elétricos, eletrónicos e programáveis relacionados com a segurança, sistemas de controlo de processos, máquinas industriais e sistemas de controlo ferroviário.

A SGS-TÜV Saar certificou a ThreadX SMP para ser utilizada em sistemas automóveis críticos de segurança, de acordo com a norma ISO 26262. Além disso, a ThreadX SMP é certificada para o Automotive Safety Integrity Level (ASIL) D, que representa o mais alto nível de certificação ISO 26262.

Além disso, a SGS-TÜV Saar certificou a ThreadX SMP para ser utilizada em aplicações ferroviárias críticas de segurança, cumprindo a norma EN 50128 até à SW-SIL 4.

![Certificação TÜV](media/image2.png)

IEC 61508 até SIL 4  
IEC 62304 até à classe de segurança SW Classe C  
ISO 26262 ASIL D  
EN 50128 SW-SIL 4  

> [!IMPORTANT]
> Contacte [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) para mais informações sobre quais as versões(s) da ThreadX SMP certificadas pela TÜV ou para a disponibilidade de relatórios de teste, certificados e documentação associada.

### <a name="misra-c-compliant"></a>Conformidade MISRA C 
MISRA C é um conjunto de diretrizes de programação para sistemas críticos utilizando a linguagem de programação C. As diretrizes originais do MISRA C destinavam-se principalmente a aplicações para automóveis; no entanto, o MISRA C é hoje amplamente reconhecido como sendo aplicável a qualquer aplicação crítica de segurança. A ThreadX SMP está em conformidade com todas as regras "obrigatórias" e "obrigatórias" da MISRA-C:2004 e da MISRA C:2012. A ThreadX SMP também está em conformidade com todas as regras de "aconselhamento". Consulte o documento ***ThreadX_MISRA_Compliance.pdf*** para obter mais detalhes.

### <a name="ul-certification"></a>Certificação UL 
A ThreadX SMP foi certificada pela UL para o cumprimento do anexo H da UL 60730-1, do anexo CSA E607301, do IEC 60730-1 Anexo H, ul 60335-1 anexo R, do IEC 60335-1 Anexo R e das normas de segurança UL 1998 para o software em componentes programáveis. Juntamente com iEC/UL 60730-1, que tem requisitos para "Controlos de Software utilizando" no seu anexo H, a norma IEC 60335-1 descreve os requisitos relativos aos "Circuitos Eletrónicos Programáveis" no seu anexo R. IEC 60730 Anexo H e IEC 60335-1 Anexo R aborda a segurança do hardware e software MCU utilizados em aparelhos como máquinas de lavar roupa, máquinas de lavar louça, secadores, frigoríficos, congeladores, congeladores e fornos.

![Certificação UL](media/image3.png) 

*UL/IEC 60730, UL/IEC 60335, UL 1998*

> [!IMPORTANT]
> Contacte [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) para mais informações sobre quais as versões(s) da ThreadX SMP certificadas pela TÜV ou para a disponibilidade de relatórios de teste, certificados e documentação associada.

### <a name="certification-pack"></a>Pacote de Certificação

O ThreadX SMP Certification Pack™ é um pacote 100% completo, chave-na-mão, específico da indústria, autónomo que fornece todas as provas SMP da ThreadX necessárias para certificar ou submeter com sucesso o produto baseado em ThreadX SMP aos mais altos níveis de fiabilidade e crítica exigidos para sistemas de aviação, médico e industrial críticos de segurança. As certificações suportadas incluem DO-178B, ED-12B, DO-278, FDA510(k), IEC-62304, IEC-60601, ISO- 14971, UL-1998, IEC-61508, CENELEC EN50128, BS50128 e 49CFR236. Entre em contato com sales@expresslogic.com mais informações sobre o Pacote de Certificação.

## <a name="embedded-applications"></a>Aplicações Incorporadas

Aplicações incorporadas executam em microprocessadores enterrados em produtos como dispositivos de comunicação sem fios, motores de automóveis, impressoras a laser, dispositivos médicos, etc. Outra distinção de aplicações incorporadas é que o seu software e hardware têm um propósito dedicado.

### <a name="real-time-software"></a>Software em tempo real 
Quando as restrições de tempo são impostas ao software da aplicação, é chamado de software *em tempo real.* Basicamente, o software que deve realizar o seu processamento dentro de um período exato de tempo é chamado de software *em tempo real.* As aplicações incorporadas são quase sempre em tempo real devido à sua interação inerente com eventos externos.

### <a name="multitasking"></a>Multitasking  
Como mencionado, as aplicações incorporadas têm um propósito dedicado. Para cumprir este fim, o software deve executar uma variedade de *tarefas*. Uma tarefa é uma parte semi-independente do pedido que executa um dever específico. É também o caso de algumas tarefas serem mais importantes do que outras. Uma das maiores dificuldades numa aplicação incorporada é a atribuição do processador entre as várias tarefas de aplicação. Esta atribuição de processamento entre tarefas concorrentes é o principal objetivo da ThreadX SMP.

### <a name="tasks-vs-threads"></a>Tarefas vs. Threads 
Há que fazer outra distinção sobre as tarefas. O termo tarefa é usado de várias maneiras. Às vezes significa um programa de carga separada. Em outros casos, pode referir-se a um segmento de programa interno.

Na discussão do sistema operativo contemporâneo, existem dois termos que substituem mais ou menos o uso da tarefa: *processo* e *linha*. Um *processo* é um programa completamente independente que tem o seu próprio espaço de endereço, enquanto um *fio* é um segmento de programa semi-independente que executa dentro de um processo. Os fios partilham o mesmo espaço de endereço de processo. A sobrecarga associada à gestão de fios é mínima.

A maioria das aplicações incorporadas não pode pagar a sobrecarga (memória e desempenho) associada a um sistema operativo orientado para o processo. Além disso, microprocessadores mais pequenos não têm a arquitetura de hardware para suportar um verdadeiro sistema operativo orientado para o processo. Por estas razões, a ThreadX SMP implementa um modelo de linha, que é simultaneamente extremamente eficiente e prático para a maioria das aplicações incorporadas em tempo real.

Para evitar confusões, a ThreadX SMP não utiliza a *tarefa* do termo . Em vez disso, o *fio* de nome mais descritivo e contemporâneo é usado.

## <a name="threadx-smp-benefits"></a>Benefícios da ThreadX SMP

A utilização da ThreadX SMP proporciona muitos benefícios às aplicações incorporadas. É claro que o benefício primário assenta na forma como os fios de aplicação incorporados são atribuídos ao tempo de processamento.

### <a name="automatic-load-balancing"></a>Equilíbrio automático de carga  
A ThreadX SMP proporciona um equilíbrio automático de carga (execução de fios através dos núcleos disponíveis), o que torna a utilização de processadores multicore o mais fácil possível. 

### <a name="improved-responsiveness"></a>Melhor capacidade de resposta  
Antes de núcleos em tempo real como o ThreadX SMP, a maioria das aplicações incorporadas atribuiu tempo de processamento com um simples loop de controlo, normalmente a partir da função *principal* C. Esta abordagem ainda é utilizada em aplicações muito pequenas ou simples. No entanto, em aplicações grandes ou complexas, não é prático porque o tempo de resposta a qualquer evento é uma função do pior tempo de processamento de uma passagem através do circuito de controlo.

Piorando as coisas, as características de tempo da aplicação mudam sempre que são feitas modificações no ciclo de controlo. Isto torna a aplicação inerentemente instável e difícil de manter e melhorar.

A ThreadX SMP fornece tempos de resposta rápidos e determinísticos a eventos externos importantes. A ThreadX SMP consegue-o através do seu algoritmo de agendamento preventivo e baseado em prioridades, que permite que um fio de maior prioridade impeça uma linha de menor prioridade de execução. Como resultado, o pior tempo de resposta aproxima-se do tempo necessário para realizar um interruptor de contexto. Isto não é apenas determinístico, mas também extremamente rápido.

### <a name="software-maintenance"></a>Manutenção de Software  
O kernel ThreadX SMP permite que os desenvolvedores de aplicações se concentrem em requisitos específicos das suas linhas de aplicação sem terem de se preocupar em alterar o tempo de outras áreas da aplicação. Esta funcionalidade também facilita muito a reparação ou a valorização de uma aplicação que utiliza o ThreadX SMP.

### <a name="increased-throughput"></a>Aumento da produção  
Uma possível formação em torno do problema do tempo de resposta do ciclo de controlo é adicionar mais sondagens. Isto melhora a capacidade de resposta, mas ainda não garante um tempo de resposta constante no pior dos casos e não faz nada para melhorar a modificação futura da aplicação. Além disso, o processador está agora a realizar um processamento ainda mais desnecessário por causa das sondagens extra. Todo este processamento desnecessário reduz a produção global do sistema.

Um ponto interessante em relação a sobrecargas é que muitos desenvolvedores assumem que ambientes multi-lis como ThreadX SMP aumentam a sobrecarga e têm um impacto negativo na produção total do sistema. Mas, em alguns casos, a multi-leitura reduz efetivamente as despesas gerais eliminando todas as sondagens redundantes que ocorrem em ambientes de ciclo de controlo. A sobrecarga associada a núcleos multi-leituras é tipicamente uma função do tempo necessário para a comutação de contexto. Se o tempo de comutação de contexto for inferior ao processo de votação, a ThreadX SMP fornece uma solução com o potencial de menor sobrecarga e mais produção. Isto faz da ThreadX SMP uma escolha óbvia para aplicações que têm qualquer grau de complexidade ou tamanho.

### <a name="processor-isolation"></a>Isolamento do processador  
A ThreadX SMP proporciona uma interface robusta entre a aplicação e o processador subjacente. Isto permite que os desenvolvedores se concentrem na aplicação em vez de gastar uma quantidade significativa de tempo aprendendo detalhes de hardware. 

### <a name="dividing-the-application"></a>Dividir a aplicação  
Nas aplicações baseadas em loops de controlo, cada desenvolvedor deve ter um conhecimento íntimo de todo o comportamento e requisitos de tempo de execução da aplicação. Isto porque a lógica de atribuição do processador está dispersa por toda a aplicação. À medida que uma aplicação aumenta de tamanho ou complexidade, torna-se impossível para todos os desenvolvedores lembrar os requisitos precisos de processamento de toda a aplicação.

A ThreadX SMP liberta cada desenvolvedor das preocupações associadas à atribuição do processador e permite-lhes concentrarem-se na sua peça específica da aplicação incorporada. Além disso, a ThreadX SMP obriga a que a aplicação seja dividida em fios claramente definidos. Por si só, esta divisão da aplicação em threads torna o desenvolvimento muito mais simples.

### <a name="ease-of-use"></a>Facilidade de utilização  
A ThreadX SMP foi concebida tendo em mente o desenvolvedor de aplicações. A interface de chamada de arquitetura e serviço ThreadX SMP foi concebida para ser facilmente compreendida. Como resultado, os desenvolvedores da ThreadX SMP podem utilizar rapidamente as suas funcionalidades avançadas.  

### <a name="improve-time-to-market"></a>Melhorar o tempo para o mercado  
Todos os benefícios da ThreadX SMP aceleram o processo de desenvolvimento de software. A ThreadX SMP cuida da maioria dos problemas do processador e das certificações de segurança mais comuns, retirando assim este esforço do calendário de desenvolvimento. Tudo isto resulta num momento mais rápido para o mercado!  

### <a name="protecting-the-software-investment"></a>Proteger o Investimento em Software  
Devido à sua arquitetura, a ThreadX SMP é facilmente apromedida a novos ambientes de ferramentas de processador e/ou desenvolvimento. Isto, juntamente com o facto de a ThreadX SMP isolar as aplicações dos detalhes dos processadores subjacentes, torna as aplicações SMP da ThreadX altamente portáteis. Como resultado, a trajetória de migração da aplicação está garantida e o investimento de desenvolvimento original está protegido.