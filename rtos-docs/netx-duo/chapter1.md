---
title: Capítulo 1 - Introdução ao Azure RTOS NetX Duo
description: Este capítulo contém uma introdução ao Azure RTOS NetX Duo e uma descrição das suas aplicações e benefícios.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c9b5e0ea82319bd369318cca753cf1db222ca29b0b4db3da150642ca007f1191
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116789870"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo"></a>Capítulo 1 - Introdução ao Azure RTOS NetX Duo

Azure RTOS NetX Duo é uma implementação em tempo real de alto desempenho das normas TCP/IP projetadas exclusivamente para aplicações incorporadas baseadas em Azure RTOS ThreadX. Este capítulo contém uma introdução ao NetX Duo e uma descrição das suas aplicações e benefícios. 

## <a name="netx-duo-unique-features"></a>Recursos Exclusivos da Dupla NetX

Ao contrário de outras implementações TCP/IP, o NetX Duo foi concebido para ser versátil — facilmente escalando de pequenas aplicações baseadas em microcontrolador para aquelas que usam poderosos processadores RISC e DSP. Isto contrasta fortemente com o domínio público ou outras implementações comerciais originalmente destinadas a ambientes de estações de trabalho, mas depois espremidas em desenhos incorporados.

### <a name="piconettrade-architecture"></a>Arquitetura Piconet &trade;

Subjacente à escalabilidade superior e desempenho do NetX Duo está <em>o Piconet,</em>uma arquitetura de software especialmente concebida para sistemas incorporados. A arquitetura Piconet maximiza a escalabilidade implementando os serviços NetX Duo como uma biblioteca C. Desta forma, apenas os serviços utilizados pela aplicação são trazidos para a imagem final do tempo de execução. Assim, o tamanho real do NetX Duo é determinado pela aplicação. Para a maioria das aplicações, os requisitos de imagem de instrução do NetX Duo variam entre 5 KBytes e 30 KBytes de tamanho. Com IPv6 e ICMPv6 habilitados para configuração de endereço iPv6 e protocolos de descoberta de vizinhos, netX Duo varia em tamanho de 30 kbytes a 45 kbytes.

O NetX Duo consegue um desempenho de rede superior através da camada de camadas de funções de componente interno apenas quando é necessário. Além disso, grande parte do processamento da NetX Duo é feito diretamente em linha, resultando em excelentes vantagens de desempenho sobre o software de rede de estações de trabalho usado em designs incorporados no passado.

### <a name="zero-copy-implementation"></a>Implementação de cópia zero

A NetX Duo fornece uma implementação baseada em pacotes e cópia zero de TCP/IP. A cópia zero significa que os dados no tampão do pacote da aplicação nunca são copiados dentro do NetX Duo. Isto melhora consideravelmente o desempenho e liberta ciclos valiosos de processadores para a aplicação, o que é importante em aplicações incorporadas.

### <a name="udp-fast-pathtrade-technology"></a>Tecnologia UDP Fast Path &trade;

Com <em>a UDP Fast Path Technology,</em>a NetX Duo fornece o processamento UDP mais rápido possível. Do lado do envio, o processamento de UDP - incluindo a unidade de verificação opcional do UDP - está contido no serviço <em>**nx_udp_socket_send.**</em> Não são efetuadas chamadas de função adicionais até que o pacote esteja pronto para ser enviado através da rotina interna de envio do NetX Duo IP. Esta rotina também é plana (ou seja, a sua função de nesting de chamada é mínima) pelo que o pacote é rapidamente despachado para o controlador de rede da aplicação. Quando o pacote UDP é recebido, o processamento de receção de pacotes NetX Duo coloca o pacote diretamente na fila de receção da tomada UDP apropriada ou dá-o ao primeiro fio suspenso à espera de um pacote de receção da fila de receção da tomada UDP. Não são necessários comutadores de contexto ThreadX adicionais.

### <a name="ansi-c-source-cod"></a>Ansi C Source Bacalhau

NetX Duo é escrito completamente em ANSI C e é portátil imediatamente para praticamente qualquer arquitetura de processador que tenha um compilador ANSI C e suporte ThreadX. 

### <a name="not-a-black-box"></a>Não uma caixa preta

A maioria das distribuições do NetX Duo incluem o código fonte C completo. Isto elimina os problemas da "caixa preta" que ocorrem com muitas pilhas de rede comercial. Ao utilizar o NetX Duo, os desenvolvedores de aplicações podem ver exatamente o que a stack de rede está a fazer - não existem mistérios!

Ter o código fonte também permite modificações específicas da aplicação. Embora não seja recomendado, é benéfico ter a capacidade de modificar a pilha de rede se for necessário.

Estas funcionalidades são especialmente reconfortantes para os desenvolvedores habituados a trabalhar com pilhas de rede de domínio interno ou público. Esperam ter código fonte e a capacidade de modificá-lo. NetX Duo é o software de rede final para tais desenvolvedores.

### <a name="bsd-compatible-socket-api"></a>API de tomada de BSD-Compatible

Para aplicações antigas, o NetX Duo também fornece uma interface de tomada compatível com BSD que faz chamadas para o NetX Duo API de alto desempenho por baixo. Isto ajuda na migração do código de aplicação de rede existente para o NetX Duo.

## <a name="rfcs-supported-by-netx-duo"></a>RFCs Suportados por NetX Duo

O suporte do NetX Duo de RFCs que descrevem protocolos básicos de rede inclui, mas não se limita aos seguintes protocolos de rede. A NetX Duo segue todas as recomendações gerais e requisitos básicos dentro dos limites de um sistema operativo em tempo real com pequena pegada de memória e execução eficiente.

| **RFC**  | **Descrição**                                        |
| -------- | ------------------------------------------------------ |
|RFC 1112 | Extensões de anfitrião para Multicasting IP (IGMPv1)           |
|RFC 1122 | Requisitos para anfitriões de Internet - Camadas de Comunicação |
|RFC 2236 | Protocolo de Gestão do Grupo internet, versão 2          |
|RFC 768  | Protocolo de Datagrama do Utilizador (UDP)                           |
|RFC 791  | Protocolo de Internet (IP)                                 |
|RFC 792  | Protocolo de mensagem de controlo da Internet (ICMP)               |
|RFC 793  | Protocolo de Controlo de Transmissão (TCP)                    |
|RFC 826  | Protocolo de Resolução de Endereços Ethernet (ARP) |
|RFC 903  | Protocolo de Resolução de Endereços Reversos (RARP) |
|RFC 5681 | Controlo de Congestionamento TCP                     |

Abaixo estão os RFCs relacionados com o IPv6 apoiados pela NetX Duo.

|**RFC** |**Descrição**|
-------- | ------------------------------------------ |
|RFC 1981 |Caminho MTU Discovery para protocolo de Internet v6 (IPv6)|
|RFC 2460 | Especificação do Protocolo de Internet v6 (IPv6)|
|RFC 2464 |Transmissão de pacotes IPv6 através de redes Ethernet|
|RFC 4291 |Protocolo de Internet v6 (IPv6) Abordando a Arquitetura|
|RFC 4443 |Protocolo de mensagem de controlo da Internet (ICMPv6) para o protocolo de Internet v6 (IPv6) Especificação|
|RFC 4861 |Neighbor Discovery for IP v6|
|RFC 4862 |Configuração automática de endereço apátrida IPv6|

## <a name="embedded-network-applications"></a>Aplicações de rede incorporadas

As aplicações de rede incorporadas são aplicações que precisam de acesso à rede e executam em microprocessadores escondidos dentro de produtos como telemóveis, equipamentos de comunicação, motores automóveis, impressoras a laser, dispositivos médicos, etc. Tais aplicações têm quase sempre algumas restrições de memória e desempenho. Outra distinção das aplicações de rede incorporadas é que o seu software e hardware têm um propósito dedicado.

O software de rede que deve realizar o seu processamento dentro de um período exato é chamado de software de *rede* *em tempo real,* e quando as restrições de tempo são impostas em aplicações de rede, são classificadas como aplicações em tempo real. As aplicações de rede incorporadas são quase sempre em tempo real devido à sua interação inerente com o mundo externo.

## <a name="netx-duo-benefits"></a>Benefícios da Dupla NetX

Os principais benefícios da utilização do NetX Duo para aplicações incorporadas são a conectividade de alta velocidade na Internet e os pequenos requisitos de memória. O NetX Duo também está integrado com o sistema operativo threadx de alto desempenho, multitarefas ThreadX em tempo real.

### <a name="improved-responsiveness"></a>Melhor capacidade de resposta

A stack de protocolo NetX Duo de alto desempenho permite que aplicações de rede incorporadas respondam mais rapidamente do que nunca. Isto é especialmente importante para aplicações incorporadas que possuam um volume significativo de tráfego de rede ou requisitos de processamento rigorosos num único pacote.

### <a name="software-maintenance"></a>Manutenção de Software

A utilização do NetX Duo permite que os desenvolvedores partilhem facilmente os aspetos de rede da sua aplicação incorporada. Esta partição torna todo o processo de desenvolvimento fácil e aumenta significativamente a manutenção futura do software.

### <a name="increased-throughput"></a>Aumento da produção

A NetX Duo fornece a rede de maior desempenho disponível, o que é conseguido através de uma sobrecarga mínima de processamento de pacotes. Isto também permite um aumento da produção.

### <a name="processor-isolation"></a>Isolamento do processador

O NetX Duo fornece uma interface robusta e independente entre a aplicação e o processador subjacente e hardware de rede. Isto permite que os desenvolvedores se concentrem nos aspetos de rede da aplicação em vez de gastar tempo extra a lidar com problemas de hardware que afetam diretamente a rede.

### <a name="ease-of-use"></a>Facilidade de utilização

NetX Duo é projetado com o desenvolvedor de aplicações em mente. A arquitetura netx duo e interface de chamada de serviço são fáceis de entender. Como resultado, os desenvolvedores da NetX Duo podem usar rapidamente as suas funcionalidades avançadas.

### <a name="improve-time-to-market"></a>Melhorar o tempo para o mercado

As poderosas características da NetX Duo aceleram o processo de desenvolvimento de software. NetX Duo abstrata a maioria dos problemas de processador e hardware de rede, removendo assim estas preocupações de uma maioria de áreas específicas da rede de aplicações. Isto, aliado à facilidade de utilização e ao conjunto de funcionalidades avançadas, resulta num tempo mais rápido de comercialização!

### <a name="protecting-the-software-investment"></a>Proteger o Investimento em Software

O NetX Duo é escrito exclusivamente em ANSI C e está totalmente integrado com o sistema operativo ThreadX em tempo real. Isto significa que as aplicações NetX Duo são instantaneamente portáteis para todos os processadores suportados pela ThreadX. Melhor ainda, uma nova arquitetura de processador pode ser suportada com a ThreadX em questão de semanas. Como resultado, a utilização do NetX Duo garante a trajetória de migração da aplicação e protege o investimento original de desenvolvimento.

## <a name="ipv6-ready-logo-certification"></a>Certificação iPv6 Ready Logo

A certificação NetX Duo "IPv6 Ready" foi obtida através do pacote "IPv6 Core Protocol (Fase 2) Self Test" disponível na IPv6 Ready Organization. Consulte os seguintes websites IPv6-Ready do projeto para obter mais informações sobre a plataforma de teste e os casos de teste:[**https://www.ipv6ready.org/**](https://www.ipv6ready.org/)

O Suíte de Auto-Teste do Protocolo Core IPv6 da Fase 2 valida que uma pilha IPv6 observa os requisitos estabelecidos nos seguintes RFCs com testes extensivos:  
Secção 1: RFC 2460  
Secção 2: RFC 4861  
Secção 3: RFC 4862  
Secção 4: RFC 1981  
Secção 5: RFC 4443  

## <a name="ixanvl-test"></a>Teste IxANVL

NetX Duo é testado com IxANVL da IXIA. IxANVL é o padrão da indústria para a validação automatizada de rede e protocolo. Mais informações sobre o IxANVL podem ser encontradas em: [**https://www.ixiacom.com/products/ixanvl**](https://www.ipv6ready.org/)

Em particular, os seguintes módulos NetX Duo são testados com IxANVL:

|**Módulo** | **Standard** |
| --------- | ------------ |
|IP | RFC791 </br> RFC1122 </br> RFC894|
|ICMP | RFC792 </br> RFC1122 </br> RFC1812|
|UDP | RFC768 </br> RFC1122|
|TCP-Core| RFC793 </br> RFC1122 </br> RFC2460|
|TCP-Advanced| RFC1981</br>RFC2001</br>RFC2385</br>RFC2463</br>RFC813</br>RFC896|
|TCP-Performance| RFC793</br>RFC1323</br>RFC2018|

## <a name="safety-certifications"></a>Certificações de Segurança

### <a name="tv-certification"></a>Certificação TÜV  

A NetX Duo foi certificada pela SGS-TÜV Saar para utilização em sistemas críticos de segurança, de acordo com o IEC61508 e o IEC-62304. A certificação confirma que o NetX Duo pode ser utilizado no desenvolvimento de software relacionado com a segurança para os mais elevados níveis de integridade de segurança da Comissão Eletrotécnica Internacional (IEC) 61508 e IEC 62304, para a "Segurança Funcional dos sistemas eletrónicos de segurança elétricos, eletrónicos e programáveis relacionados com a segurança". A SGS-TÜV Saar, formada através de uma joint venture do SGSGroup e da TÜV Saarland da Alemanha, tornou-se a principal empresa acreditada e independente para testar, auditar, verificar e certificar software incorporado para sistemas relacionados com a segurança em todo o mundo. A norma de segurança industrial IEC 61508, bem como todas as normas que dela derivam, incluindo o IEC 62304, são utilizadas para garantir a segurança funcional de dispositivos médicos eletrónicos elétricos, eletrónicos e programáveis relacionados com a segurança, sistemas de controlo de processos, máquinas industriais e sistemas de controlo ferroviário. 

A SGS-TÜV Saar certificou a NetX Duo para ser utilizada em sistemas automóveis críticos de segurança, de acordo com a norma ISO 26262. Além disso, a NetX Duo é certificada para o Automotive Safety Integrity Level (ASIL) D, que representa o mais alto nível de certificação ISO 26262. 

Além disso, a SGS-TÜV Saar certificou a NetX Duo para ser utilizada em aplicações ferroviárias críticas de segurança, cumprindo a norma EN 50128 até à SW-SIL 4.

![Diagrama do logotipo de certificação SGS-TÜV Saar.](./media/user-guide/sgs-tuv-saar-logo.png)

IEC 61508 até SIL 4  
IEC 62304 até à classe de segurança SW C ISO 26262 ASIL D EN 50128 SW-SIL 4

> [!IMPORTANT]
> *Entre em contato com a Microsoft para obter mais informações sobre quais as versões(s) do NetX Duo certificadas pela TÜV ou para a disponibilidade de relatórios de teste, certificados e documentação associada.*

### <a name="ul-certification"></a>Certificação UL

A NetX Duo foi certificada pela UL para o cumprimento do anexo H da UL 60730-1, do CSA E60730-1 Anexo H, do IEC 60730-1 Anexo H, ul 60335-1 anexo R, do IEC 60335-1 anexo R e das normas de segurança UL 1998 para o software em componentes programáveis. Juntamente com iEC/UL 60730-1, que tem requisitos para "Controlos de Software utilizando" no seu anexo H, a norma IEC 60335-1 descreve os requisitos relativos aos "Circuitos Eletrónicos Programáveis" no seu anexo R. IEC 60730 Anexo H e IEC 60335-1 Anexo R aborda a segurança do hardware e software MCU utilizados em aparelhos como máquinas de lavar roupa, máquinas de lavar louça, secadores, frigoríficos, congeladores, congeladores e fornos.

![Diagrama do logotipo da certificação UL.](./media/user-guide/c-ru-us-logo.png)

*UL/IEC 60730, UL/IEC 60335, UL 1998*

> [!IMPORTANT]  
> *Entre em contato com a Microsoft para obter mais informações sobre quais as versões(s) da NetX Duo certificadas pela UL ou para a disponibilidade de relatórios de teste, certificados e documentação associada.*