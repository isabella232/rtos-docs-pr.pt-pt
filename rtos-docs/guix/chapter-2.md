---
title: Capítulo 2 - Instalação e Utilização do GUIX
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do produto de interface de utilizador de alta supervisão GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6527227062fc667b3f527a798d6621914c374c5c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826390"
---
# <a name="chapter-2---installation-and-use-of-guix"></a>Capítulo 2 - Instalação e Utilização do GUIX

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do produto de interface de utilizador de alta supervisão GUIX.  

## <a name="host-considerations"></a>Considerações de Anfitrião

O desenvolvimento incorporado é geralmente realizado em computadores anfitriões Windows ou Linux (Unix). Após a compilação da aplicação, ligada e o executável é gerado no anfitrião, é descarregado para o hardware alvo para execução.

Normalmente, o download do alvo é feito a partir do depurar da ferramenta de desenvolvimento. Após o download, o depurante é responsável por fornecer controlo de execução de alvos (ir, parar, quebrar, etc.) bem como aceder aos registos de memória e processador.

A maioria dos depurares de ferramentas de desenvolvimento comunicam com o hardware-alvo através de ligações de depuro on-chip (TOC), tais como JTAG (IEEE 1149.1) e Modo de Depuramento de Fundo (BDM). Os debuggers também comunicam com o hardware alvo através de ligações In-Circuit Emulation (ICE). As ligações OCD e ICE fornecem soluções robustas com uma intrusão mínima no software residente alvo.

Quanto aos recursos utilizados no hospedeiro, o código fonte do GUXI é entregue em formato ASCII e requer aproximadamente 30 Mbytes de espaço no disco rígido do computador anfitrião.

## <a name="target-considerations"></a>Considerações-alvo

O GUIX requer entre 5 KBytes e 80 Kbytes de memória Read-Only (ROM) no alvo. São necessários mais 5 a 10KBytes da Memória de Acesso Aleatório (RAM) do alvo para a pilha de fios GUIX e outras estruturas de dados globais.

Além disso, o GUIX requer a utilização de um temporizador ThreadX e de um objeto mutex ThreadX. Estas instalações são utilizadas para necessidades de processamento periódica e proteção de fios dentro do GUIX.

## <a name="product-distribution"></a>Distribuição de Produtos

O Azure RTOS GUIX pode ser obtido a partir do nosso repositório de código fonte pública em <https://github.com/azure-rtos/guix/> .

Segue-se uma lista dos ficheiros importantes comuns à maioria das distribuições de produtos:

| Nome de arquivo&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;| Descrição   |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| gx_api.h        | Este ficheiro de cabeçalho C contém todos os equacionares do sistema, estruturas de dados e protótipos de serviço. |
| gx_port.h       | Este ficheiro de cabeçalho C contém todas as definições e estruturas específicas de dados específicas do alvo e do desenvolvimento.                                                                                                                                         |
| gx.a (ou gx.lib) | Esta é a versão binária da biblioteca GUIX C. Isto é normalmente construído compilando e arquivando os ficheiros de origem da biblioteca GUIX fornecidos, no entanto esta biblioteca pode ser fornecida em forma pré-construída dependendo do seu alvo de hardware e tipo de licença. |
|

> [!IMPORTANT]
> *Todos os ficheiros estão em minúsculas, facilitando a conversão dos comandos para plataformas de desenvolvimento Linux (Unix).*

## <a name="guix-installation"></a>Instalação GUIX

O GUIX é instalado através da clonagem do repositório GitHub à sua máquina local. Segue-se a sintaxe típica para a criação de um clone do repositório GUIX no seu PC:

```c
    git clone https://github.com/azure-rtos/guix
```

Em alternativa, pode descarregar uma cópia do repositório utilizando o botão de descarregamento na página principal do GitHub.

Também encontrará instruções para a construção da biblioteca GUIX na primeira página do repositório online.

>[!NOTE]  
> *O software de aplicação precisa de acesso ao ficheiro da biblioteca GUIX, normalmente chamado **gx.a** (ou **gx.lib),** e o C inclui ficheiros **gx_api.h** e **gx_port.h**. Isto é conseguido quer estabelecendo o caminho adequado para as ferramentas de desenvolvimento, quer copiando estes ficheiros para a área de desenvolvimento de aplicações.*

## <a name="using-guix"></a>Usando GUIX

A utilização do GUIX é fácil. Basicamente, o código de aplicação deve incluir ***gx_api.h** _ durante a compilação e ligação com a biblioteca GUIX _*_gx.a_*_ (ou _ *_gx.lib)*._*

São necessários quatro passos fáceis para a construção de uma aplicação GUIX:

| Passos   | Descrição    |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Passo &nbsp; 1: | Inclua o ficheiro ***gx_api.h*** em todos os ficheiros de aplicações que utilizam serviços GUIX ou estruturas de dados.                                                               |
| Passo &nbsp; 2: | Inicialize o sistema GUIX chamando ***gx_system_initialize** _ da função _ *_tx_application_define_** ou de um fio de aplicação.                       |
| Passo &nbsp; 3: | Crie uma instância de visualização, crie uma tela para o visor e crie a janela raiz e quaisquer outras janelas ou widgets necessários.                                 |
| Passo &nbsp; 4: | Compilar fonte de aplicação e ligar-se com a biblioteca de tempo de execução GUIX ***gx.a** _ (ou _*_gx.lib_**). A imagem resultante pode ser descarregada para o alvo e executada! |

## <a name="troubleshooting"></a>Resolução de problemas

Cada porta GUIX é entregue com uma aplicação de demonstração que executa em hardware de exibição específico. A mesma demonstração básica é entregue com todas as versões do GUIX. É sempre uma boa ideia pôr o sistema de demonstração a funcionar primeiro.

Se o sistema de demonstração não funcionar corretamente, efetuar as seguintes operações para reduzir o problema:

1. Determina quanto da demonstração está a decorrer.

2. Aumente o tamanho da pilha do fio GUIX alterando a **GX_THREAD_STACK_SIZE** constante de tempo de compilação e recompilando a biblioteca GUIX

3. Recompilar a biblioteca GUIX com as opções de depurar apropriadas listadas na secção de opções de configuração.

4. Examine o estado de devolução de todas as chamadas da API.

5. Determinar se existe um erro interno do sistema ao definir um ponto de rutura na função ***_gx_system_error_process***. Há código de erro e o chamador deve dar pistas sobre o que pode estar a correr mal.

6. Contornar temporariamente quaisquer alterações recentes para ver se o problema desaparece ou muda. Estas informações devem revelar-se úteis aos engenheiros de suporte da Microsoft.

Siga os procedimentos descritos na secção intitulada "What We Need From You" para enviar as informações recolhidas a partir das etapas de resolução de problemas.

## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração ao construir a biblioteca GUIX e a aplicação usando o GUIX. Estas opções são usadas para sintonizar o tamanho da biblioteca e o conjunto de funcionalidades de forma a adequar-se melhor aos seus requisitos de aplicação. Por exemplo, se a sua aplicação tiver apenas um fio utilizando os serviços da API GUIX, a bandeira de configuração **GX_DISABLE_MULTITHREAD_SUPPORT** deve ser definida para eliminar a sobrecarga associada à proteção de secções de código crítico de antecipação por múltiplos fios. As várias bandeiras de configuração podem ser definidas na fonte de aplicação, na linha de comando ou no **_gx_user.h_** incluem ficheiro.

Sempre que as bandeiras de configuração da biblioteca GUIX forem modificadas, é necessário reconstruir tanto a biblioteca GUIX como os módulos de aplicação para que as alterações de configuração produzam efeitos.

A lista completa de bandeiras de configuração está documentada no Apêndice H: GUIX Build-Time As bandeiras de configuração.

## <a name="guix-version-id"></a>ID da versão GUIX

A versão atual do GUIX está disponível tanto para o utilizador como para o software da aplicação durante o tempo de funcionamento. O programador pode obter a versão GUIX a partir do exame do ficheiro ***gx_port.h** _ Além disso, este ficheiro também contém um histórico de versão do software de aplicação de porta correspondente pode obter a versão GUIX examinando a cadeia global *_ _ _gx_version_id_* _ em _*_gx_port.h**._

O software de aplicação também pode obter informações de libertação das constantes abaixo mostradas definidas em ***gx_api.h**.* Estas constantes identificam a versão atual do produto pelo nome e a versão maior e menor do produto.

```C
#define __PRODUCT_GUIX__

#define __GUIX_MAJOR_VERSION__

#define __GUIX_MINOR_VERSION__
```
