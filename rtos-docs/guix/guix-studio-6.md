---
title: Código gerado pelo estúdio GUIX
description: Quando termina a edição dos seus ecrãs e recursos, o GUIX Studio produz um conjunto de ficheiros de saída que podem ser incorporados na sua aplicação incorporada.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 78b1ec1eea3ec2fcae48c64ad15931f44f34538c876dc8a267c2b1a84234320a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785707"
---
# <a name="chapter-6-guix-studio-generated-code"></a>Capítulo 6: Código Gerado pelo estúdio GUIX

Quando termina a edição dos seus ecrãs e recursos, o GUIX Studio produz um conjunto de ficheiros de saída que podem ser incorporados na sua aplicação incorporada. Os ficheiros de saída são gerados selecionando ***Gerar Ficheiros de Recursos** _ e _ Gerar *_Especificações_** a partir do item do menu Project. Os ficheiros de código de origem linguística 'c' gerados pelo GUIX Studio destinam-se a ser compilados e ligados ao código fonte de aplicação incorporado. Se for produzido um ficheiro de recurso de formato binário, este ficheiro deve ser programado para uma área de armazenamento não volátil no alvo e a função API GUIX gx_binres_theme_install deve ser utilizada para instalar os recursos binários em tempo de execução.

O código de aplicação incorporado do utilizador faz referências ao código gerado pelo GUIX Studio. Além disso, o código gerado pelo GUIX Studio espera que todas as funções de desenho de widgets personalizados, manuseamento de eventos e alocação de memória especificadas no projeto sejam definidas no código de aplicação incorporado do utilizador. Caso contrário, estarão presentes erros de ligação na construção da aplicação.

> [!NOTE]
> O utilizador nunca deverá ter de modificar o código gerado pelo GUIX Studio e deve resistir a fazê-lo. Todas as modificações de UI devem ser feitas no projeto associado do GUIX Studio. Isto manterá o projeto sincronizado com a aplicação incorporada.

## <a name="generating-resource-files"></a>Gerar ficheiros de recursos

Os ficheiros de recursos gerados pelo GUIX Studio contêm estruturas de dados predefinidas que definem todos os recursos do GUIX Studio (cores, fontes, pixelmaps e cordas), que é efetivamente todos os recursos definidos na ***Visão*** de Recursos do projeto. Estes ficheiros de recursos podem ser gerados em código fonte ou formas binárias.

Por predefinição, existem dois ficheiros gerados, um ficheiro é um ficheiro de código fonte C padrão e o outro é um ficheiro de cabeçalho C que fornece referências e constantes externas que são necessárias para que o código de aplicação aceda aos recursos GUIX definidos no projeto. Os nomes dos ficheiros são do formulário:

**{*nome do projeto*}_resources.h**

**{*nome do projeto*}_resources.c**

Por exemplo, os ficheiros de recursos criados para o projeto "***simples***" GUIX Studio são:

**simple_resources.h**

**simple_resources.c**

Gerar os ficheiros de Recursos é realizado selecionando ***Gerar ficheiros de recursos** _ opção na opção _*_menu Project._*_ O destino dos ficheiros de recursos é especificado no diálogo _*_configurar Project,_*_ que é acessível através da opção _*_Configurar Project/Displays_*_ no item do menu _ *_Configure*_*.

Para os recursos pixelmap e Font, pode especificar um nome de ficheiro de saída personalizado para cada pixelmap e fonte nos diálogos de edição de recursos associados. Esta funcionalidade permite-lhe colocar recursos muito grandes em ficheiros distintos, em vez de colocar todos os recursos num ficheiro de saída comum. Se não especificar um nome de ficheiro overridden para um recurso de tipo de letra ou pixelmap, esses recursos são escritos no ficheiro de recursos comuns.

Se preferir utilizar recursos binários, pode especificar o formato de saída s-record cru ou padrão. Os recursos binários não são compilados ou ligados ao código de aplicação, mas são carregados em tempo de execução utilizando a API gx_binres_them_load(). Este serviço API constrói tabelas de recursos que apontam para os seus recursos armazenados em memória não volátil. Em seguida, pode instalar estes recursos com um determinado ecrã utilizando gx_display_theme_install();

## <a name="generating-specification-code"></a>Código de Especificação Gerador

Os ficheiros Especificação gerados pelo GUIX Studio contêm todo o código C para criar o UI projetado no GUIX Studio. Este código também faz referência aos ficheiros de Recursos gerados para este projeto. O código de aplicação do utilizador fará chamadas para este código para realmente criar os objetos de UI definidos no projeto. Além disso, o código de aplicação do utilizador contém todas as funções de desenho de widgets personalizados, manuseamento de eventos e atribuição de memórias especificadas no projeto. Por predefinição, existem dois ficheiros gerados, um ficheiro é um ficheiro de código fonte C padrão e o outro é um ficheiro de cabeçalho C que fornece referências e constantes externas que são necessárias para que o código de aplicação aceda às Especificações do Estúdio GUIX. Os nomes dos ficheiros são do formulário:

**{*nome do projeto*}_specifications.h**

**{*nome do projeto*}_specifications.c**

Por exemplo, os ficheiros especificação criados para o projeto "***simples***" GUIX Studio são:

**simple_specifications.h**

**simple_specifications.c**

Gerar os ficheiros Especificação é realizado selecionando ***Gerar ficheiros de especificação** _ opção na opção _*_menu Project._*_ O destino dos ficheiros Especificação é especificado no diálogo _*_configurar Project,_*_ que é acessível através da opção _*_Configurar Project/Displays_*_ no item do menu _ *_Configure*_*.

## <a name="integrating-with-user-code"></a>Integração com Código do Utilizador

A integração dos ficheiros de recursos e especificações gerados pelo GUIX Studio é simples, basta seguir estes passos:

1. Ou copia ou torna os ficheiros de recursos e especificações acessíveis através de definições de caminhos para o ambiente de construção incorporado
2. Adicione todos os ficheiros de Recursos e Especificações ao projeto IDE incorporado ou ao ficheiro de fazer
3. Certifique-se de que o código incorporado da aplicação chama as funções necessárias para inicializar e criar o UI contido nos ficheiros de Recursos e Especificações
4. Certifique-se de que o código incorporado da aplicação contém todas as funções de desenho de widgets personalizados necessários, manuseamento de eventos e atribuição de memória
5. Construa a aplicação (compilar e ligar)
6. Execute a aplicação!