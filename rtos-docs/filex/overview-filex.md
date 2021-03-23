---
title: Compreenda O Azure RTOS Filex
description: O Azure RTOS FileX é um sistema de ficheiros compatível com ficheiros de alto desempenho (FAT)que está totalmente integrado com o Azure RTOS ThreadX e está disponível para todos os processadores suportados. Tal como o Azure RTOS ThreadX, o Azure RTOS FileX foi concebido para ter uma pequena pegada e alto desempenho, tornando-o ideal para as aplicações profundamente incorporadas que requerem operações de gestão de ficheiros. O FileX suporta a maioria dos meios físicos, incluindo RAM, Azure RTOS USBX, SD CARD e NAND/NOR memórias flash via Azure RTOS LevelX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: a3a20c8ced3426399ceedf6994c872ce7aec93c3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827320"
---
# <a name="overview-of-azure-rtos-filex"></a>Visão geral do Azure RTOS FileX

O sistema de ficheiros incorporado Azure RTOS FileX é a solução avançada e industrial da Azure RTOS para formatos de ficheiros Microsoft FAT, projetado especificamente para aplicações profundamente incorporadas, em tempo real e IoT. O Azure RTOS FileX suporta todos os formatos de ficheiros da Microsoft, incluindo FAT12, FAT16, FAT32 e exFAT. O FileX também oferece tolerância opcional de falhas e nivelamento de desgaste FLASH através de um produto addon chamado [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/). Tudo isto combinado com uma pequena pegada, execução rápida e facilidade superior de utilização, fazem do Azure RTOS FileX a escolha ideal para as aplicações IoT incorporadas mais exigentes.

## <a name="api-protocols"></a>Protocolos da API

### <a name="azure-rtos-filex-api"></a>Azure RTOS FileX API

- API intuitiva e consistente
- Convenção de nomeação de substantivos
- Todas as APIs têm *fx_* a identificar facilmente como FileX
- ApIs de bloqueio têm tempo limite opcional de fio
- Chamadas opcionais de notificação do utilizador para meios de comunicação e operações de ficheiros
- Consulte o Guia de [Utilizador Azure RTOS FileX](about-this-guide.md) para mais detalhes

### <a name="media-services"></a>Serviços de Multimédia

- SUPORTE FAT 12/16/32 e exFAT
- Flash mínimo de 6KB, RAM de 2,5KB
- Serviços completos de acesso aos meios de comunicação
- Número ilimitado de instâncias mediáticas
- Interface de condutor do sector de leitura/escrita simples
- Suporte de partição múltipla
- Cache do sector lógico
- Cache de entrada de GORDURA
- Suporte opcional de tolerância à falha
- Atualização de FAT Secundária Diferida
- Traço de nível do sistema via Azure RTOS TraceX
- APIs de acesso a meios de comunicação intuitivos, incluindo:
  - fx_media_open
  - fx_media_close
  - fx_media_format
  - fx_media_space_available

### <a name="directory-services"></a>Serviços de Diretório

- Até 256 byte caminhos
- Nomes de diretório longos e 8,3 apoiados
- Diretório criar & excluir
- Navegação diretório e traversal
- Gestão de atributos de diretório
- Traço de nível do sistema via Azure RTOS TraceX
- APIs de acesso a diretórios intuitivos, incluindo:
  - fx_directory_create
  - fx_directory_delete
  - fx_directory_attributes_set
  - fx_directory_attributes_read
  - fx_directory_first_entry_find
  - fx_directory_next_entry_find

### <a name="file-services"></a>Serviços de Ficheiros

- Flash mínimo de 3.3KB
- Ficheiros abertos ilimitados
- Os ficheiros apenas de leitura podem ser abertos várias vezes
- Nomes de diretório longos e 8,3 apoiados
- Suporte de ficheiros contíguos
- Lógica de procura rápida
- Pré-atribuição de clusters
- Criar, excluir e renomear ficheiros
- Arquivar ler, escrever e ver
- Gestão de atributos de ficheiros
- Traço de nível do sistema via Azure RTOS TraceX
- APIs de acesso a ficheiros intuitivos, incluindo:
  - fx_file_create
  - fx_file_delete
  - fx_file_attributes_set
  - fx_file_attributes_read
  - fx_file_read
  - fx_file_seek
  - fx_file_write

## <a name="small-footprint"></a>Pequena pegada

O sistema de ficheiros incorporado Azure RTOS FileX tem uma pegada mínima notável de 8,6 KB a 12 KB para suporte básico de leitura/escrita de ficheiros. O uso mínimo de Azure RTOS FileX RAM está na ordem de 1.8 KB para uma instância de mídia e com apenas uma cache lógico de 512 byte sectores. Tal como o Azure RTOS ThreadX, o tamanho do Azure RTOS FileX escala automaticamente com base nos serviços utilizados pela aplicação. Isto praticamente elimina a necessidade de configuração complicada e constrói parâmetros, tornando as coisas mais fáceis para o desenvolvedor.

## <a name="fast-execution"></a>Execução rápida

O Azure RTOS FileX fornece uma cache lógico do sector, bem como uma cache de entrada FAT. Os tamanhos de ambos estão sob controlo direto da aplicação. Além disso, o Azure RTOS FileX fornece alocação contígua de cluster e leitura e escrita diretas consecutivas de cluster. Os pedidos de leitura/escrita de sectores inteiros são feitos diretamente entre o tampão de aplicação e os meios de comunicação – ou seja, não é feito nenhum tampão intermédio. Tudo isto e uma filosofia geral de design orientada para o desempenho ajuda o Azure RTOS FileX a alcançar o desempenho mais rápido possível.

## <a name="advanced-technology"></a>Tecnologia avançada

Azure RTOS FileX é uma tecnologia avançada, incluindo as seguintes.

- SUPORTE FAT 12/16/32 e exFAT
- Suporte de partição múltipla
- Dimensionamento automático
- Endian neutro
- Nome de arquivo longo e suporte 8.3
- Suporte opcional de tolerância à falha
- Cache do sector lógico
- Cache de entrada de GORDURA
- Pré-atribuição de clusters
- Suporte de ficheiros contíguos
- Métricas de desempenho opcionais
- Suporte de análise do sistema Azure RTOS TraceX

## <a name="nornand-wear-leveling-azure-rtos-levelx"></a>Nivelamento de desgaste NOR/NAND (Azure RTOS LevelX)

Azure RTOS LevelX é o produto de nivelamento de desgaste NOR/NAND FLASH da Microsoft. O Azure RTOS LevelX pode ser usado em conjunto com o FileX ou como uma biblioteca do sector FLASH de leitura/escrita autónoma para a aplicação.

## <a name="fastest-time-to-market"></a>O tempo de venda mais rápido

O Azure RTOS FileX é fácil de instalar, aprender, usar, depurar, verificar, certificar e manter. Como resultado, o Azure RTOS FileX é um dos sistemas de ficheiros FAT mais populares para dispositivos IoT incorporados. Seguem-se algumas razões para a nossa vantagem consistente no mercado:

- Documentação de Qualidade – por favor, reveja [o nosso Guia de Utilizador Azure RTOS FileX](about-this-guide.md) e consulte por si mesmo!
- Disponibilidade completa do Código Fonte
- API de fácil utilização
- Conjunto de recursos abrangente e avançado

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a>Pré-certificada pela TUV e UL para muitas normas de segurança

![SGS-TUV Saar](./media/overview-filex/partener-logo-sgs-tuv-saar-2.png)

O Azure RTOS FileX foi certificado pela SGS-TUV Saar para utilização em sistemas críticos de segurança, de acordo com o IEC-61508 SIL 4, IEC-62304 SW Safety Class C, ISO 26262 ASIL D e EN 50128. A certificação confirma que o FileX pode ser utilizado no desenvolvimento de software relacionado com a segurança para os mais elevados níveis de integridade de segurança da IEC-61508, IEC-62304, ISO 26262 e EN 50128 para a "Segurança Funcional dos sistemas eletrónicos, eletrónicos e programáveis relacionados com a segurança electrónica". A SGS-TUV Saar, formada através de uma joint venture da SGS-Group alemã e tuv Saarland, tornou-se a principal empresa acreditada e independente para testes, auditorias, verificação e certificação de software incorporado para sistemas relacionados com a segurança em todo o mundo. A norma de segurança industrial IEC 61508, e todas as normas que dela derivam, incluindo a IEC-62304, a ISO 26262 e a EN 50128, são utilizadas para garantir a segurança funcional de dispositivos médicos elétricos, eletrónicos e programáveis relacionados com a segurança electrónica, sistemas de controlo de processos, máquinas industriais, automóveis e sistemas de controlo ferroviário.

:::image type="content" source="media/overview-filex/cru-logo-certification.png" alt-text="Certificação CRU UL":::

O Azure RTOS FileX foi reconhecido pela UL pelo cumprimento do anexo H da UL 60730-1, do CSA E60730-1 Anexo H, do IEC 60730-1 anexo H, ul 60335-1 anexo R, do IEC 60335-1 Anexo R, da UL e das normas de segurança 1998 para as normas de segurança em componentes programáveis. A UL é uma empresa global, independente e de ciência da segurança, com mais de um século de experiência em soluções de segurança inovadoras, que vão desde a adoção pública de eletricidade até avanços na sustentabilidade, energias renováveis e nanotecnologia.

Estão à venda artefactos (Certificado, Manual de Segurança, Relatório de Teste, etc.) associados às certificações TUV e UL.

Nos casos em que a aplicação necessita de certificação adicional, está disponível um serviço de certificação através da Microsoft para fornecer certificação chave-na-curva a vários padrões utilizando a plataforma de hardware real e até mesmo cobrindo o código de aplicação.

## <a name="one-simple-license"></a>Uma licença simples

Não há qualquer custo para usar e testar o código fonte e nenhum custo para licenças de produção quando implementados em dispositivos pré-licenciados, todos os outros dispositivos precisam de uma licença anual simples.

## <a name="full-highest-quality-source-code"></a>Código fonte completo e de alta qualidade

Ao longo dos anos, o código fonte FileX definiu a barra em qualidade e facilidade de compreensão. Além disso, a convenção de ter uma função por ficheiro prevê uma fácil navegação de origem.

## <a name="supports-most-popular-architectures"></a>Apoia as arquiteturas mais populares

O Azure RTOS FileX funciona em microprocessadores de 32/64 bits mais populares, fora da caixa, totalmente testados e totalmente suportados, incluindo os seguintes:

**Dispositivos Analógicos**: SHARC, Blackfin, CM4xx

**Núcleo de Andes**: RISC-V

**Ambiqmicro**: Apollo MCUs

**BRAÇO**: ARM7, ARM9, ARM11, Córtex-M0/M3/M4/M7/A15/A5/A7/A8/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M

**Cadência**: Xtensa, Diamante

**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WiCED WiFi

**Cipreste**: RISC-V

**EnSilica**: eSi-RISC

**Infineon**: XMC1000, XMC4000, TriCore

**Intel;** **Intel FPGA**: x36/Pentium, XScale, NIOS II, Ciclone, Arria 10

**Microchip**: AVR32, ARM7, ARM9, Córtex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32

**Microsemi**: RISC-V

**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4

**Renesas**: SH, HS, V850, RX, RZ, Sinergia

**Silício** Laboratórios: EFM32

**Sinopses**: ARC 600, 700, ARC EM, ARC HS

**ST**: STM32, ARM7, ARM9, Córtex-M3/M4/M7

**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C

**Computação de ondas**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, Classe M

**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

*Todos os valores de tempo e tamanho listados são estimativas e podem ser diferentes na sua plataforma de desenvolvimento.*
