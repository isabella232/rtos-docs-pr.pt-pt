---
title: Compreenda O Azure RTOS Filex
description: O Azure RTOS FileX é um sistema de ficheiros compatível com ficheiros de alto desempenho (FAT)que está totalmente integrado com o Azure RTOS ThreadX e está disponível para todos os processadores suportados. Tal como o Azure RTOS ThreadX, o Azure RTOS FileX foi concebido para ter uma pequena pegada e alto desempenho, tornando-o ideal para as aplicações profundamente incorporadas que requerem operações de gestão de ficheiros. O FileX suporta a maioria dos meios físicos, incluindo RAM, Azure RTOS USBX, SD CARD e NAND/NOR memórias flash via Azure RTOS LevelX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0a54f160c96fb3e90c2295ae72020c121d367a12
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171358"
---
# <a name="overview-of-azure-rtos-filex"></a>Visão geral do Azure RTOS FileX

O sistema de ficheiros incorporado Azure RTOS FileX é a solução avançada e industrial da Azure RTOS para formatos de ficheiros Microsoft FAT, projetado especificamente para aplicações profundamente incorporadas, em tempo real e IoT. O Azure RTOS FileX suporta todos os formatos de ficheiros da Microsoft, incluindo FAT12, FAT16, FAT32 e exFAT. O FileX também oferece tolerância opcional de falhas e nivelamento de desgaste FLASH através de um produto addon chamado [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/). Tudo isto combinado com uma pequena pegada, execução rápida e facilidade superior de utilização, fazem do Azure RTOS FileX a escolha ideal para as aplicações IoT incorporadas mais exigentes.

## <a name="api-protocols"></a>Protocolos da API

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
