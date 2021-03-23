---
title: Capítulo 1 - Visão geral
author: philmea
description: Este artigo é uma visão geral dos Módulos Azure RTOS ThreadX
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0c9698086468d7bb41c33ebe9fa9d1ebb61b5f1f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825496"
---
# <a name="chapter-1-overview"></a>Capítulo 1: Visão geral

O componente Do Módulo ThreadX fornece uma infraestrutura para aplicações para carregar dinamicamente os módulos que são construídos separadamente da parte residente da aplicação. Isto é especialmente útil em situações em que o tamanho do código de aplicação excede a memória disponível. Também pode ajudar quando são necessárias novas funcionalidades após a implementação da imagem do núcleo. Além disso, podem ser utilizados módulos de carregamento dinâmico quando são necessárias atualizações parciais de firmware.

A proteção da memória do módulo carregado é opcional, com base nas propriedades especificadas no preâmbulo do módulo. Quando a proteção da memória é especificada, o hardware de gestão da memória do processador é configurado de modo a que todos os fios do módulo só tenham acesso ao código e à memória de dados do módulo. Qualquer acesso ou execução de memórias extraérida resultará numa falha de memória e o fio do módulo ofensivo será encerrado. Se a aplicação registar uma chamada de notificação por falha de memória, esta também será chamada para alertar a aplicação da falha de memória.

O componente do Módulo ThreadX baseia-se na aplicação para fornecer uma área de memória onde os módulos podem ser carregados. A área de instrução de cada módulo pode ser executada no lugar ou ser copiada para a área de memória do módulo RAM para execução. Em todos os casos, os requisitos de memória de dados do módulo são atribuídos a partir da área de memória do módulo.

Não existem limites no número de módulos que podem ser carregados ao mesmo tempo (além da quantidade de memória disponível), enquanto há apenas uma cópia do código do Gestor de Módulos residente. A Figura 1 ilustra a relação do Gestor de Módulos e dos próprios módulos.

![Relação de Gestor de Módulos e Módulos](media/image2.png)

**Figura 1** Gestor de Módulos e Módulos

Cada módulo deve ter a sua própria área de memória, que é da responsabilidade da aplicação definir. O Módulo e o Gestor de Módulos interagem através de uma função de despacho de software através de IDs de pedido pré-definidos que correspondem aos serviços ThreadX solicitados pelo módulo. Além disso, o módulo é necessário para fornecer um único ponto de entrada de fio, bem como o tamanho de pilha necessário, prioridade, ID do módulo, tamanho/prioridade da pilha de fio de retorno, etc. Esta informação é definida no preâmbulo de cada módulo.

O Gestor do Módulo é responsável pela criação do fio do módulo inicial e pela sua execução. Uma vez executada a linha inicial do módulo, o Gestor do Módulo é responsável por colocar em campo todos os pedidos de API da ThreadX feitos pelo módulo. Um módulo tem acesso total à API ThreadX, incluindo a capacidade de criar fios adicionais dentro do módulo.  
  
As convenções de nomeação do código fonte do módulo são simples: todos os ficheiros de origem do Gestor de Módulos são nomeados ***txm_module_manager_ \**** e todos os ficheiros associados exclusivamente ao módulo omitem a parte "**_manager_*_" do nome. O ficheiro principal inclui o ficheiro _*_txm_module.h_** é partilhado pelo código fonte do gestor e do módulo.
