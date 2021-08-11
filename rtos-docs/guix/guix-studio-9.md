---
title: Linha de Comando do Estúdio GUIX
description: O GUIX Studio fornece invocação de linha de comando que é útil para construir oleodutos que são necessários para atualizar os ficheiros de saída gerados pelo Estúdio.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: bd88054d974aabea30b50c6f4e10b4c5df9994db03ab84a4a5d8f9394b4d6ed8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785401"
---
# <a name="chapter-9-guix-studio-command-line"></a>Capítulo 9: Linha de Comando do Estúdio GUIX

O GUIX Studio suporta a invocação da linha de comando, que é útil para construir oleodutos que são necessários para atualizar os ficheiros de saída gerados pelo Estúdio.

## <a name="command-line-usage"></a>Command-Line Utilização

**Utilização:** argumento \[ de opção guix_studio \] \[\]

Abra o projeto *.gxp.*

Abra o projeto Studio e gere os ficheiros de saída desejados.


**Exemplos:**

`guix_studio demo.gxp`  
Projeto aberto "demo.gxp"


`guix_studio.exe –p demo.gxp`  
Projeto aberto "demo.gxp"


`guix_studio.exe –n –p demo.gxp`  
Gere todos os ficheiros de saída do projeto demo.gxp.

`guix_studio.exe –n –r –p demo.gxp`  
Gerar ficheiros de recursos do projeto demo.gxp


## <a name="command-line-options"></a>Opções Command-Line

```C
***-n --nogui***  
```

A opção "nogui". Diga ao GUIX Studio para funcionar sem iniciar a interface de UI de janela.

```C
***-o pathname***  
***--log***  
```

Iniciar sessão, especificar um ficheiro de registo.

```C
***-b***  
***--binary***  
```

Opção de recurso binário. Produz um ficheiro de recursos binários em vez de um ficheiro C.

```C
***-d display1, display2***  
***--display***  
```

A opção de apresentar nomes. Se esta opção for utilizada, apenas os nomes de visualização especificados estão incluídos em qualquer recurso ou ficheiros de especificações gerados. Se esta opção não for utilizada, todos os ecrãs estão incluídos.

```C
***-t theme1, theme2***  
***--theme***  
```

Opção nome(s) tema. Se esta opção for utilizada, apenas os nomes temáticos especificados estão incluídos em qualquer recurso ou ficheiros de especificações gerados. Se esta opção não for utilizada, todos os temas estão incluídos.

```C
***-l langage1, language2***  
***--language***  
```

Opção nome(s) nome de idioma. Se esta opção for utilizada, os nomes de idioma especificados estão incluídos nos ficheiros de recursos ou especificações gerados. Caso contrário, todos os nomes linguísticos estão incluídos.

```C
***-r [filename]***  
***--resource***  
```

A opção de recurso especifica que o Studio deve produzir um ficheiro de recursos para exibições previamente designadas, temas e idiomas.

```C
***-s [filename]***  
***--specification***  
```

A opção de especificação, especificar que o estúdio deve produzir um ficheiro de especificações para display(s) designados, temas e idiomas.

```C
***-p project_pathname***  
***--project***  
```

Project opção pathname, especifique o projeto exemplo a carregar.

```C
***-i [pathname]***  
***--import***  
```

Cadeia de importação de xliff ou ficheiro de formato csv.

***-big_endian***  
Gerar dados de recursos em formato de grande ponta.
