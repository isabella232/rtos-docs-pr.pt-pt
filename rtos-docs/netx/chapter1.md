---
title: Capítulo 1 - Introdução ao Azure RTOS NetX
description: Este capítulo contém uma introdução ao Azure RTOS NetX e uma descrição das suas aplicações e benefícios.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 207aaec18f020e8cc3534a9ef55ed338df487fd95b22b5021f691ea63ba62b8b
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782867"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx"></a>Capítulo 1 - Introdução ao Azure RTOS NetX

Azure RTOS NetX é uma implementação em tempo real de alto desempenho das normas TCP/IP projetadas exclusivamente para aplicações incorporadas baseadas em ThreadX. Este capítulo contém uma introdução ao NetX e uma descrição das suas aplicações e benefícios.

## <a name="netx-unique-features"></a>Recursos Exclusivos da NetX

Ao contrário de outras implementações TCP/IP, o NetX foi concebido para ser versátil — facilmente escalando de pequenas aplicações baseadas em microcontroladores para aquelas que usam poderosos processadores RISC e DSP. Isto contrasta fortemente com o domínio público ou outras implementações comerciais originalmente destinadas a ambientes de estações de trabalho, mas depois espremidas em desenhos incorporados.

### <a name="piconettrade-architecture"></a>Arquitetura Piconet &trade;

Subjacente à escalabilidade superior e desempenho do NetX está *o Piconet,* uma arquitetura de software especialmente concebida para sistemas incorporados. A arquitetura Piconet maximiza a escalabilidade implementando os serviços NetX como uma biblioteca C. Desta forma, apenas os serviços realmente utilizados pela aplicação são trazidos para a imagem final do tempo de execução. Assim, o tamanho real do NetX é completamente determinado pela aplicação. Para a maioria das aplicações, os requisitos de tamanho de imagem do NetX variam entre 5 KBytes e 30 KBytes de tamanho.

O NetX obtém um desempenho de rede superior através da camada de camadas de funções de componente interno apenas quando é absolutamente necessário. Além disso, grande parte do processamento do NetX é feito diretamente em linha, resultando em excelentes vantagens de desempenho sobre o software de rede de estações de trabalho que era frequentemente usado em designs incorporados no passado.</th>

### <a name="zero-copy-implementation"></a>Implementação de cópia zero

A NetX fornece uma implementação baseada em pacotes *e cópia zero* de TCP/IP. A cópia zero significa que os dados no tampão do pacote da aplicação nunca são copiados dentro do NetX. Isto melhora consideravelmente o desempenho e liberta ciclos de processador valiosos para a aplicação, o que é extremamente importante em aplicações incorporadas.

### <a name="udp-fast-pathtrade-technology"></a>Tecnologia UDP Fast Path &trade;

Com *a UDP Fast Path Technology,* a NetX fornece o processamento UDP mais rápido possível. Do lado do envio, o processamento de UDP - incluindo a unidade de verificação opcional do UDP - está completamente contido no serviço ***nx_udp_socket_send.*** Não são efetuadas chamadas de função adicionais até que o pacote esteja pronto para ser enviado através da rotina interna de envio de IP NetX. Esta rotina também é plana (ou seja, a sua função de nidificação de chamada é mínima) pelo que o pacote é rapidamente despachado para o controlador de rede da aplicação. Quando o pacote UDP é recebido, o processamento de receção de pacotes NetX coloca o pacote diretamente na fila de receção da tomada UDP apropriada ou dá-o ao primeiro fio suspenso à espera de um pacote de receção da fila de receção da tomada UDP. Não são necessários comutadores de contexto ThreadX adicionais.

### <a name="ansi-c-source-code"></a>Código Fonte ANSI C

O NetX está escrito completamente em ANSI C e é portátil imediatamente para praticamente qualquer arquitetura de processador que tenha um compilador ANSI C e suporte ThreadX.

### <a name="not-a-black-box"></a>Não uma caixa preta

A maioria das distribuições do NetX incluem o código fonte C completo. Isto elimina os problemas da "caixa preta" que ocorrem com muitas pilhas de rede comercial. Ao utilizar o NetX, os desenvolvedores de aplicações podem ver exatamente o que a stack de rede está a fazer - não existem mistérios!
  
Ter o código fonte também permite modificações específicas da aplicação. Apesar de não ser recomendado, é certamente benéfico ter a capacidade de modificar a pilha de rede se for necessário.  

Estas funcionalidades são especialmente reconfortantes para os desenvolvedores habituados a trabalhar com pilhas de rede de domínio interno ou público. Esperam ter código fonte e a capacidade de modificá-lo. O NetX é o software de rede final para estes desenvolvedores.

### <a name="bsd-compatible-socket-api"></a>API de tomada de BSD-Compatible

Para aplicações antigas, o NetX fornece uma interface de tomada compatível com BSD que faz chamadas para a API NetX de alto desempenho por baixo. Isto ajuda na migração do código de aplicação de rede existente para o NetX.

## <a name="rfcs-supported-by-netx"></a>RFCs Suportados por NetX

O suporte netX de RFCs que descrevem protocolos básicos de rede inclui, mas não se limita aos seguintes protocolos de rede. A NetX segue todas as recomendações gerais e requisitos básicos dentro dos limites de um sistema operativo em tempo real com pequena pegada de memória e execução eficiente.

| RFC      | Description                                            |
|----------|--------------------------------------------------------|
| RFC 1112 | Extensões de anfitrião para Multicasting IP (IGMPv1)           |
| RFC 1122 | Requisitos para anfitriões de Internet - Camadas de Comunicação |
| RFC 2236 | Protocolo de Gestão do Grupo internet, versão 2          |
| RFC 768  | Protocolo de Datagrama do Utilizador (UDP)                           |
| RFC 791  | Protocolo de Internet (IP)                                 |
| RFC 792  | Protocolo de mensagem de controlo da Internet (ICMP)               |
| RFC 793  | Protocolo de Controlo de Transmissão (TCP)                    |
| RFC 826  | Protocolo de Resolução de Endereços Ethernet (ARP)             |
| RFC 903  | Protocolo de Resolução de Endereços Reversos (RARP)             |
|          |                                                        |

## <a name="embedded-network-applications"></a>Aplicações de rede incorporadas

As aplicações de rede incorporadas são aplicações que precisam de acesso à rede e executam em microprocessadores escondidos dentro de produtos como telemóveis, equipamentos de comunicação, motores automóveis, impressoras a laser, dispositivos médicos, etc. Tais aplicações têm quase sempre algumas restrições de memória e desempenho. Outra distinção das aplicações de rede incorporadas é que o seu software e hardware têm um propósito dedicado.

### <a name="real-time-network-software"></a>Software de rede em tempo real  

Basicamente, o software de rede que deve realizar o seu processamento dentro de um período exato é chamado de software de *rede* *em tempo real,* e quando as restrições de tempo são impostas em aplicações de rede, são classificadas como aplicações em tempo real. As aplicações de rede incorporadas são quase sempre em tempo real devido à sua interação inerente com o mundo externo.

## <a name="netx-benefits"></a>Benefícios NetX

Os principais benefícios da utilização do NetX para aplicações incorporadas são a conectividade de alta velocidade na Internet e os requisitos de memória muito pequenos. O NetX também está completamente integrado com o sistema operativo ThreadX de alto desempenho e multitarefas em tempo real.

### <a name="improved-responsiveness"></a>Melhor capacidade de resposta  

A stack de protocolo NetX de alto desempenho permite que aplicações de rede incorporadas respondam mais rapidamente do que nunca. Isto é especialmente importante para aplicações incorporadas que possuam um volume significativo de tráfego de rede ou requisitos de processamento rigorosos num único pacote.

### <a name="software-maintenance"></a>Manutenção de Software

A utilização do NetX permite que os desenvolvedores partilhem facilmente os aspetos de rede da sua aplicação incorporada. Esta partição torna todo o processo de desenvolvimento fácil e aumenta significativamente a manutenção futura do software.

### <a name="increased-throughput"></a>Aumento da produção

A NetX fornece a rede de maior desempenho disponível, o que é conseguido através de uma sobrecarga mínima de processamento de pacotes. Isto também permite um aumento da produção.

### <a name="processor-isolation"></a>Isolamento do processador

O NetX fornece uma interface robusta e independente entre a aplicação e o processador subjacente e hardware de rede. Isto permite que os desenvolvedores se concentrem nos aspetos de rede da aplicação em vez de gastar tempo extra a lidar com problemas de hardware que afetam diretamente a rede.

### <a name="ease-of-use"></a>Facilidade de utilização

O NetX foi concebido tendo em mente o desenvolvedor de aplicações. A arquitetura NetX e a interface de chamada de serviço são fáceis de entender. Como resultado, os desenvolvedores netX podem usar rapidamente as suas funcionalidades avançadas.

### <a name="improve-time-to-market"></a>Melhorar o tempo para o mercado

As poderosas funcionalidades da NetX aceleram o processo de desenvolvimento de software. NetX abstrata a maioria dos problemas de processador e hardware de rede, removendo assim estas preocupações de uma maioria de áreas específicas da rede de aplicações. Isto, aliado à facilidade de utilização e ao conjunto de funcionalidades avançadas, resulta num tempo mais rápido de mercado.

### <a name="protecting-the-software-investment"></a>Proteger o Investimento em Software

O NetX é escrito exclusivamente em ANSI C e está totalmente integrado com o sistema operativo ThreadX em tempo real. Isto significa que as aplicações NetX são instantaneamente portáteis para todos os processadores suportados pela ThreadX. Melhor ainda, uma arquitetura de processador completamente nova pode ser suportada com a ThreadX em questão de semanas. Como resultado, a utilização do NetX garante a trajetória de migração da aplicação e protege o investimento original de desenvolvimento.
