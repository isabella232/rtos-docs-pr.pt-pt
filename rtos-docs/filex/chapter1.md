---
title: Capítulo 1 - Introdução ao Azure RTOS FileX
description: Azure RTOS FileX é um sistema completo de gestão de formato FAT e gestão de ficheiros para aplicações profundamente incorporadas.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 48fab21d78ede88e84db11a4f30574ce2061d145820b819ec7846203e297f42a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782977"
---
# <a name="chapter-1---introduction-to-azure-rtos-filex"></a>Capítulo 1 - Introdução ao Azure RTOS FileX

Azure RTOS FileX é um sistema completo de gestão de formato FAT e gestão de ficheiros para aplicações profundamente incorporadas. Este capítulo introduz o FileX, descrevendo as suas aplicações e benefícios.

## <a name="filex-unique-features"></a>Recursos exclusivos do FileX

O Azure RTOS FileX suporta um número ilimitado de dispositivos de mídia ao mesmo tempo, incluindo discos RAM, gestores FLASH e dispositivos físicos reais. Suporta formatos de tabela de atribuição de ficheiros de 12, 16 e 32 bits ( FAT), e também suporta a Tabela de Atribuição de Ficheiros Estendido (exFAT), a atribuição de ficheiros contíguos, e está altamente otimizada tanto para o tamanho como para o desempenho. O FileX também inclui suporte tolerante a falhas, meios de comunicação abertos/fechados e funções de reversão de ficheiros.

Projetado para responder à necessidade crescente de dispositivos FLASH, o FileX utiliza os mesmos métodos de design e codificação que o ThreadX. Como todos os produtos da Microsoft, o FileX é distribuído com código fonte ANSI C completo, e não tem royalties de tempo de execução.

### <a name="product-highlights"></a>Destaques do produto

- Suporte completo do processador ThreadX
- Sem royalties
- Complete o código fonte ANSI C
- Desempenho em tempo real
- Suporte técnico responsivo
- Objetos ilimitados de FileX (meios de comunicação, diretórios e ficheiros)
- Criação/eliminação de objetos FileX dinâmicos
- Uso flexível da memória
- Escalas de tamanho automaticamente
- Tamanho da área de instrução de pequena pegada (até 6 KBytes): 6-30K
- Integração completa com a ThreadX
- Endian neutro
- Controladores de E/S de FileX fáceis de implementar
- Suporte de 12, 16 e 32 bits de GORDURA
- suporte exFAT
- Suporte de nome de ficheiro longo
- Cache de entrada de GORDURA interna
- Suporte ao nome unicode
- Atribuição de ficheiros contíguos
- Leitura/escrita de agrupamentos e sectores consecutivos
- Cache do sector lógico interno
- Demonstração de disco RAM fica sem caixa
- Capacidade de formato de mídia
- Deteção e recuperação de erros
- Opções tolerantes a falhas
- Estatísticas de desempenho incorporadas
- Suporte autónomo (No Azure RTOS)

## <a name="safety-certifications"></a>Certificações de Segurança

### <a name="tv-certification"></a>Certificação TÜV

O FileX foi certificado pela SGS-TÜV Saar para utilização em sistemas críticos de segurança, de acordo com o IEC-61508 e o IEC-62304. A certificação confirma que o FileX pode ser utilizado no desenvolvimento de software relacionado com a segurança para os mais elevados níveis de integridade de segurança da Comissão Eletrotécnica Internacional (IEC) 61508 e IEC 62304, para a "Segurança Funcional dos sistemas eletrónicos de segurança elétricos, eletrónicos e programáveis relacionados com a segurança". A SGS-TÜV Saar, formada através de uma joint venture da SGS-Group alemã e da TÜV Saarland, tornou-se a principal empresa acreditada e independente para testar, auditar, verificar e certificar software incorporado para sistemas relacionados com a segurança em todo o mundo. A norma de segurança industrial IEC 61508, bem como todas as normas que dela derivam, incluindo o IEC 62304, são utilizadas para garantir a segurança funcional de dispositivos médicos eletrónicos elétricos, eletrónicos e programáveis relacionados com a segurança, sistemas de controlo de processos, máquinas industriais e sistemas de controlo ferroviário.

A SGS-TÜV Saar certificou o FileX para ser utilizado em sistemas automóveis críticos de segurança, de acordo com a norma ISO 26262. Além disso, o FileX é certificado para o Automotive Safety Integrity Level (ASIL) D, que representa o mais alto nível de certificação ISO 26262.

Além disso, a SGS-TÜV Saar certificou o FileX para ser utilizado em aplicações ferroviárias críticas de segurança, cumprindo a norma EN 50128 até à SW-SIL 4.

![Logotipo SGS TUV Saar](./media/user-guide/sgs-tuv-saar-logo.png)

- IEC 61508 até SIL 4
- IEC 62304 até à classe de segurança SW Classe C
- ISO 26262 ASIL D
- EN 50128 SW-SIL 4

> [!IMPORTANT]
> Entre em contato conosco para mais informações sobre quais as versões(s) do FileX foram certificadas pela TÜV ou para a disponibilidade de relatórios de teste, certificados e documentação associada.*

### <a name="ul-certification"></a>Certificação UL

O FileX foi certificado pela UL para o cumprimento do anexo H, do anexo CSA E60730-1, do IEC 60730-1, do anexo H, do ul 60335-1, do anexo IEC 603351 do anexo R e do UL 1998 para as normas de segurança para software em componentes programáveis. Juntamente com iEC/UL 60730-1, que tem requisitos para "Controlos de Software utilizando" no seu anexo H, a norma IEC 60335-1 descreve os requisitos relativos aos "Circuitos Eletrónicos Programáveis" no seu anexo R. IEC 60730 Anexo H e IEC 60335-1 Anexo R aborda a segurança do hardware e software MCU utilizados em aparelhos como máquinas de lavar roupa, máquinas de lavar louça, secadores, frigoríficos, congeladores, congeladores e fornos.

![C RU US 2](./media/user-guide/c-ru-us-logo.png)

*UL/IEC 60730, UL/IEC 60335, UL 1998*

> [!IMPORTANT]
>*Entre em contato conosco para mais informações sobre quais as versões(s) do FileX foram certificadas pela UL ou para a disponibilidade de relatórios de teste, certificados e documentação associada.*

## <a name="powerful-services-of-filex"></a>Serviços Poderosos do FileX

### <a name="multiple-media-management"></a>Gestão de Múltiplos Meios de Comunicação Social

O FileX pode suportar um número ilimitado de meios físicos. Cada instância mediática tem a sua própria área de memória distinta e o controlador associado especificado na ***chamada fx_media_open.*** A distribuição predefinitiva do FileX vem com um simples controlador de mídia RAM e um sistema de demonstração que utiliza este disco RAM.

### <a name="logical-sector-cache"></a>Cache do Sector Lógico

Ao reduzir o número de transferências sectoriais inteiras, tanto de e para os meios de comunicação, o cache do sector lógico FileX melhora significativamente o desempenho. O FileX mantém uma cache lógico do sector para cada meio aberto. A profundidade da cache do sector lógico é determinada pela quantidade de memória fornecida ao FileX com a ***chamada API fx_media_open.***

### <a name="contiguous-file-support"></a>Suporte ao Arquivo Contíguo

O FileX oferece suporte a ficheiros contíguos através do serviço API ***fx_file_allocate*** para melhorar e tornar determinístico o tempo de acesso ao ficheiro. Esta rotina requer a quantidade de memória solicitada e procura uma série de aglomerados adjacentes para satisfazer o pedido. Se esses agrupamentos forem encontrados, são pré-atribuídos, tornando-os parte da cadeia de aglomerados atribuídos do ficheiro. Ao mover os meios físicos, o suporte contíguo do ficheiro FileX resulta numa melhoria significativa do desempenho e torna o tempo de acesso determinístico.

### <a name="dynamic-creation"></a>Criação Dinâmica

O FileX permite-lhe criar recursos do sistema de forma dinâmica. Isto é especialmente importante se a sua aplicação tiver requisitos de configuração múltiplos ou dinâmicos. Além disso, não existem limites pré-determinados no número de recursos FileX que pode utilizar (meios de comunicação ou ficheiros). Além disso, o número de objetos do sistema não tem qualquer impacto no desempenho.

## <a name="easy-to-use-api"></a>API de fácil utilização

O FileX fornece a melhor tecnologia de sistema de ficheiros profundamente incorporada de uma forma fácil de entender e fácil de usar! A Interface de Programação de Aplicações FileX (API) torna os serviços intuitivos e consistentes. Não terá de decifrar serviços de "sopa de alfabeto" que são muito comuns com outros sistemas de ficheiros.

Para obter uma lista completa dos serviços da versão 5 do FileX, consulte [o apêndice A](appendix-a.md).

## <a name="exfat-support"></a>suporte exFAT

exFAT (Tabela de Atribuição de Ficheiros alargado) é um sistema de ficheiros concebido pela Microsoft para permitir que o tamanho do ficheiro exceda 2GB, um limite imposto pelos sistemas de ficheiros FAT32. É o sistema de ficheiros predefinido para cartões SD com capacidade superior a 32GB. Os cartões SD ou as unidades flash formatadas com o formato exFAT do FileX são compatíveis com Windows. exFAT suporta o tamanho do ficheiro até um Exabyte (EB), que é aproximadamente mil milhões de GB.

Os utilizadores que desejem utilizar o exFAT devem recompiler a biblioteca FileX com o símbolo ***FX_ENABLE_EXFAT** _ definido. Ao abrir os meios de comunicação, o FileX deteta o tipo de mídia. Se o meio for formatado com exFAT, o FileX lê e escreve o sistema de ficheiros seguindo a norma exFAT. Para formatar novos meios de comunicação com exFAT, utilize o serviço _*_fx_media_exFAT_format_**. Por predefinição, o exFAT não está ativado.

## <a name="fault-tolerant-support"></a>Suporte tolerante a falhas

O Módulo Tolerante a Falhas FileX foi concebido para prevenir a corrupção do sistema de ficheiros causada por interrupções durante o ficheiro ou atualização do diretório. Por exemplo, ao anexar dados a um ficheiro, o FileX precisa de atualizar o conteúdo do ficheiro, a entrada no diretório e, possivelmente, as entradas FAT. Se esta sequência de atualização for interrompida (como falha de energia, ou se os meios de comunicação forem ejetados no meio da atualização), o sistema de ficheiros encontra-se num estado inconsistente, o que pode afetar a integridade de todo o sistema de ficheiros, levando à corrupção de outros ficheiros.

O Módulo Tolerante a Falhas FileX funciona gravando todas as etapas necessárias para atualizar um ficheiro ou um diretório ao longo do caminho. Esta entrada de registo é armazenada nos meios de comunicação em sectores dedicados (blocos) que o FileX pode encontrar e aceder. A localização dos dados de registo pode ser acedida mesmo sem um sistema de ficheiros adequado. Portanto, no caso de o sistema de ficheiros ser corrompido, o FileX ainda é capaz de encontrar a entrada de registo e restaurar o sistema de ficheiros de volta para um bom estado.

À medida que o FileX atualiza o ficheiro ou o diretório, são criadas entradas de registo. Após a operação de atualização ser concluída com sucesso, as entradas de registo são removidas. Se as entradas de registo não foram corretamente removidas após uma atualização de ficheiros bem sucedida, se o processo de recuperação determinar que o conteúdo da entrada de registo corresponde ao sistema de ficheiros, nada precisa de ser feito e as entradas de registo podem ser limpas.

Caso a operação de atualização do sistema de ficheiros tenha sido interrompida, da próxima vez que o suporte for montado pelo FileX, o Módulo Tolerante de Falha analisa as entradas de registo. As informações contidas nas entradas de registo permitem que o FileX recue as alterações parciais já aplicadas no sistema de ficheiros (caso a falha o faça durante a fase inicial da operação de atualização do ficheiro), ou se as entradas de registo contiverem informações de re-realização, o FileX pode aplicar as alterações necessárias para terminar a operação anterior.

Esta função tolerante a falhas está disponível para todos os sistemas de ficheiros FAT suportados pelo FileX, incluindo FAT12, FAT16, FAT32 e exFAT. Por defeito, o tolerante por defeito não está ativado no FileX. Para ativar a função tolerante a falhas, o FileX deve ser construído com o símbolo  **FX_ENABLE_FAULT_TOLERANT** e **FX_FAULT_TOLERANT** definido. No tempo de execução, a aplicação inicia o serviço tolerante a falhas, chamando **_fx_fault_tolerant_enable_**.
Após o início do serviço, todas as operações de escrita de ficheiros e diretórios passam pelo Módulo Tolerante a Falhas.

À medida que o serviço tolerante a falhas começa, deteta primeiro se os meios de comunicação estão ou não protegidos sob o Módulo Tolerante de Falhas. Caso contrário, o FileX assume a integridade do sistema de ficheiros e inicia a proteção atribuindo blocos livres do sistema de ficheiros a serem utilizados para registar e caching. Se os registos do Módulo Tolerante de Falha forem encontrados no sistema de ficheiros, analisa as entradas de registo. O FileX reverte a operação anterior ou refaça a operação anterior, dependendo do conteúdo das entradas de registo. O sistema de ficheiros fica disponível depois de todas as entradas de registo prévio serem processadas. Isto garante que a FIleX parte de um bom estado conhecido.

Depois de um meio de comunicação ser protegido sob o Módulo Tolerante a Falhas filex, os meios de comunicação não serão atualizados com outro sistema de ficheiros. Ao fazê-lo, as entradas de registo no sistema de ficheiros seriam inconsistentes com o conteúdo da tabela FAT, a entrada do diretório. Se o meio de comunicação for atualizado por outro sistema de ficheiros antes de o transferir de volta para o FileX com o Módulo Tolerante de Falhas, o resultado é indefinido.

## <a name="callback-functions"></a>Funções de retorno

As três funções de retorno seguintes são adicionadas ao FileX:

- Media Open callback
- Media Close callback
- Chamada de escrita de ficheiro

Após a inscrição, estas funções notificarão o pedido quando tais eventos ocorrerem.

## <a name="easy-integration"></a>Integração Fácil

O FileX é facilmente integrado com praticamente qualquer flash ou dispositivo de mídia. Porting FileX é simples. Este guia descreve o processo em detalhe, e o condutor da RAM do sistema de demonstração faz com que seja um bom lugar para começar!
