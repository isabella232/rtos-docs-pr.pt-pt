---
title: Exemplo simples Project
description: Este capítulo descreve como criar um projeto de exemplo no GUIX Studio e executar o exemplo no GUIX.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 8981bed62d2929703e4233d6a3ee31b692226c26d046875a235bf3aca32a7573
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116786656"
---
# <a name="chapter-10-example-project"></a>Capítulo 10: Exemplo Project

Este capítulo descreve como criar um projeto de exemplo no GUIX Studio e executar o exemplo no GUIX.

## <a name="create-new-project"></a>Criar Novo Projeto

O primeiro passo é criar um novo projeto e configurar os ecrãs e linguagens que o projeto irá apoiar. Quando iniciar o GUIX Studio, verá o ecrã de ***Projetos Recentes:***

![Screenshot do diálogo guix Studio Recent Projects.](./media/guix-studio/recent_projects.png)

**Figura 10.1**

Clique no ***Criar Nova Project** _... botão para iniciar um novo projeto. Você será apresentado com o diálogo _ *_New GUIX Project_** mostrado aqui:

![Screenshot do estúdio GUIX Criar novo diálogo de Project.](./media/guix-studio/create_new_project.png)

**Figura 10.2**

Digite o nome "***new_example***" como o nome do projeto. Project nomes devem usar regras de nomeação variáveis C padrão, isto é, nenhum caracteres especiais ou reservados. Digite o caminho para o local onde o projeto deve ser guardado. O caminho deve ser um diretório de sistema de ficheiros válido, ou seja, o GUIX Studio não criará o diretório se não existir. Clique em "OK" para criar o projeto.

O próximo ecrã mostrado é o ecrã de configuração Project, mostrado aqui:

![Screenshot do guix Studio Configure Project diálogo.](./media/guix-studio/config_new_project.png)

**Figura 10.3**

Este diálogo permite especificar quantos ecrãs o seu projeto irá suportar e dar um nome a cada visualização. Deve especificar o formato de cor suportado por cada ecrã e, opcionalmente, escrever um nome de pathname para os ficheiros de saída gerados pelo Studio para cada ecrã. O diretório predefinido para os ficheiros de saída é "***" ", \\*** o que significa que os ficheiros de saída C são escritos para o mesmo diretório que o próprio projeto.

Para este exemplo, deixe o número ***de visualizações** _ definido para "1", escreva o nome "_*_main_display_*_" no campo do nome do visor, e verifique "_*_alocar a memória_*_ de tela ". Deixe a resolução, o formato de cores e os campos de diretório nos seus valores predefinidos, e clique em _*_OK_**.

Deverá agora ver o seu projeto aberto com o Studio IDE, como mostra a figura 10.4:

![Screenshot de um projeto aberto com o Studio IDE.](./media/guix-studio/initial_screen.png)

**Figura 10.4**

Ao criar um novo projeto, o GUIX Studio cria automaticamente uma janela padrão como ponto de partida para o seu projeto. Esta caixa cinzenta é a janela padrão criada para si, centrada na *Vista Alvo*.

Se esta janela não for selecionada, clique na janela de modo a que a caixa de seleção tracejada seja desenhada à volta da janela. Agora na ***Visualização de Propriedades** _, altere o _*_Nome Widget,_*_ _*_Widget Id_*_, _*_Esquerda,_*_ _*_Topo,_*_ _*_Largura,_*_ _*_Altura_*_ e _ *_Fronteira_** para combinar com as definições mostradas abaixo. Ao efetuar estas alterações, deverá ver as suas alterações imediatamente a produzir efeito dentro da Vista Alvo.

![Screenshot do diálogo Properties View.](./media/guix-studio/initial_window_properties.png)

**Figura 10.5**

Em seguida, adicionaremos um recurso pixelmap para ser usado dentro de um widget ***GX_ICON** _ . Vários ícones são fornecidos com a sua distribuição guix Studio que funcionará bem para este exemplo. Expanda a sua Visualização de Recursos _*_Pixelmaps_*_ e clique no botão _ *_Add New Pixelmap_** :

![Screenshot do botão Add New Pixelmap.](./media/guix-studio/image74.jpg)

Navegue na sua pasta de instalação GUIX Studio e na pasta ***./graphics/icons** _ selecione o ficheiro nomeado _*_i_history_lg.png_*_. Clique _*_em Aberto_*_ para adicionar este recurso ao seu projeto. A sua _ *_Pixelmaps_** Resource View deve agora mostrar uma pré-visualização da imagem do ícone recém-adicionada:

![Screenshot da Visualização de Recursos pixelmaps.](./media/guix-studio/example_add_pixelmap.png)

**Figura 10.6**

Usaremos este novo recurso de imagem mais tarde como parte do nosso design de UI.

Similares à adição de um recurso pixelmap, adicionamos um novo recurso de fonte à nossa caixa de ferramentas para que possamos usar este tipo de letra mais tarde no nosso design. Expandir a ***Visualização de** recursos * e clicar no botão _*_Adicionar Nova Fonte._*_ Esta ação invocará o diálogo de fonte _*_add/Edit._*_ Em seguida, navegue para as fontes GUIX fornecidas na pasta de instalação do GUIX Studio, _*_ . \\ fontes \\ verasans_ *_, e selecione o ficheiro de fonte TrueType chamado _*_VeraIt.ttf_*_. Escreva o nome de fonte "_*_MEDIUM_ITALIC_" no campo de nome *_da fonte, e escreva "_*_30_**" no campo de altura. O seu diálogo deve agora ser assim:

![Screenshot do diálogo Edit Font.](./media/guix-studio/example_add_font.png)

**Figura 10.7**

Clique ***em OK*** para adicionar este tipo de letra ao seu projeto. Deverá agora ver o tipo de letra na sua Visão de Recursos:

![Screenshot das fontes na vista de recursos.](./media/guix-studio/example_font_added.png)

**Figura 10.8**

Usaremos este novo tipo de letra mais tarde no nosso design de UI.

Agora que temos novos recursos disponíveis, precisamos adicionar alguns widgets infantis ao nosso ecrã que possam utilizar estes recursos. Selecione a janela previamente criada denominada "***hello_world** _" clicando à direita na janela na Vista Alvo. No menu pop-up que agora é apresentado, selecione o comando do menu _*_Insira, Texto, Prompt_*_ para inserir um novo widget _ *_GX_PROMPT_** e fixe o widget à janela de fundo. Sua janela deve agora ser assim:

![Screenshot de um menu pop-up com a seleção Prompt](./media/guix-studio/image78.jpg)

**Figura 10.9**

Clique na fonte denominada "***MEDIUM_ITALIC** _" na _ *_Visualização_* de recursos * e arraste e deixe cair o tipo de letra no widget de solicitação. Em seguida, edite as propriedades prontas como mostrado na figura 10.10 para redimensionar o pedido, definir a transparência rápida e alterar o texto e o estilo rápidos:

![Screenshot da visualização do imóvel para o pedido.](./media/guix-studio/image79.jpg)

**Figura 10.10**

Pode ser necessário deslocar-se verticalmente na Visualização de Propriedades para ver cada uma destas definições dependendo da resolução do ecrã. Depois de es fazer estas alterações, a sua Visão alvo deve agora ser assim:

![Screenshot de um menu pop-up com a seleção Hello World.](./media/guix-studio/image80.jpg)

**Figura 10.11**

Em seguida, colocaremos um widget estilo Icon Button no ecrã. Selecione a janela de fundo clicando nela e use o menu de nível superior ou o menu pop-up de clique direito para selecionar ***Insira, Botão, Botão de Ícone** _ para adicionar um novo _*_GX_ICON_BUTTON_*_ à janela. Clique no Ícone nomeado _ *_I_HISTORY_LG_** que adicionamos anteriormente e arraste-o para o botão de ícone. Utilizando a vista de propriedades, ajuste a posição e o tamanho do ícone como mostra abaixo:

![Screenshot do View Properties para o widget estilo botão do ícone.](./media/guix-studio/image81.jpg)

**Figura 10.12**

O seu ecrã deve agora ser assim:

![Screenshot de um menu pop-up com o ícone Hello World e clipboard.](./media/guix-studio/image82.jpg)

**Figura 10.13**

Vamos chamar isto completo para o design de tela de exemplo simples. Os ecrãs de aplicações reais serão provavelmente muito mais sofisticados, mas isto é suficiente para lhe mostrar como usar o GUIX Studio para criar os seus próprios ecrãs de aplicações.

## <a name="generate-resource-and-application-code"></a>Gerar Código de Recursos e Aplicação

O próximo passo é gerar o ficheiro de recursos e o ficheiro de especificações que definem a UI embutida do TEMPO DE EXECUÇÃO GUIX. Para gerar os seus ficheiros de saída, necessitará de clicar no nó ***main_display** _ no Project View e selecionar o comando _ *_Gerar Ficheiros_* de Recursos * . Observará uma janela de informação que indica que os seus ficheiros de recursos foram gerados, como mostra a figura 10.14:

![Screenshot de um diálogo de notificação.](./media/guix-studio/image83.jpg)

**Figura 10.14**

Clique **em*** OK _ para rejeitar esta notificação e use o mesmo procedimento para clicar no nó _*_main_display_*_ e selecione o comando _ *_Gerar Ficheiros de Especificação_** . Deve observar uma janela de notificação semelhante. Agora gerou os seus ficheiros simples de aplicações uI.

## <a name="create-user-supplied-code"></a>Criar código fornecido pelo utilizador

O próximo passo é criar o seu próprio ficheiro de aplicação que irá invocar o design de ecrã gerado pelo GUIX Studio. Utilizando o seu editor preferido, crie um ficheiro de origem denominado ***new_example.c***, e introduza o seguinte código fonte neste ficheiro:

```C

/* This is an example of the GUIX graphics framework in Win32. */
/* Include system files. */

#include <stdio.h>
#include "tx_api.h"
#include "gx_api.h"

/* Include GUIX resource and specification files for example. */

#include "new_example_resources.h"
#include "new_example_specifications.h"

/* Define the new example thread control block and stack. */

TX_THREAD new_example_thread;
UCHAR new_example_thread_stack[4096];

/* Define the root window pointer. */

GX_WINDOW_ROOT *root_window;

/* Define function prototypes. */

VOID new_example_thread_entry(ULONG thread_input);
UINT win32_graphics_driver_setup_24bpp(GX_DISPLAY *display);

int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
    return(0);
}

VOID tx_application_define(void *first_unused_memory)
{
    /* Create the new example thread. */
    tx_thread_create(&new_example_thread, "GUIX New Example Thread", 
                      new_example_thread_entry, 0, 
                      new_example_thread_stack, sizeof(new_example_thread_stack),
                      1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
}

VOID new_example_thread_entry(ULONG thread_input)
{

    /* Initialize the GUIX library */
    gx_system_initialize();

    /* Configure the main display. */
    gx_studio_display_configure(MAIN_DISPLAY,                      /* Display to configure*/
                                win32_graphics_driver_setup_24bpp, /* Driver to use */
                                LANGUAGE_ENGLISH,                  /* Language to install */
                                MAIN_DISPLAY_DEFAULT_THEME,        /* Theme to install */
                                &root_window);                     /* Root window pointer */

    /* Create the screen - attached to root window. */

    gx_studio_named_widget_create("hello_world", (GX_WIDGET *) root_window, GX_NULL);

    /* Show the root window to make it visible. */
    gx_widget_show(root_window);

    /* Let GUIX run. */
    gx_system_start();

}
```

O código de origem acima cria um fio ThreadX típico nomeado `GUIX New Example Thread` com um tamanho de pilha de bytes 4K. O trabalho interessante começa na função denominada ***new_example_thread_entry.*** Esta função é onde o fio específico GUIX começa a funcionar.

A primeira chamada é para a função denominada ***gx_system_initialize***. Esta chamada é sempre necessária antes de serem invocadas quaisquer outras APIs GUIX para preparar a biblioteca GUIX para primeira utilização.

Em seguida, o exemplo chama a função ***gx_studio_display_configure***. Esta função cria a instância de visualização GUIX, instala o idioma solicitado da tabela de cordas de aplicação, instala o tema solicitado a partir dos recursos de exibição e devolve um ponteiro à janela raiz que foi criada para este visor. A janela raiz é usada como o pai de todos os ecrãs de nível superior que a nossa aplicação irá exibir.

Em seguida, o exemplo chama ***gx_studio_named_widget_create** _ para criar um exemplo do nosso ecrã _ *_hello_world*_* Esta função utiliza as estruturas de dados e os recursos produzidos pelo GUIX Studio para criar uma instância do ecrã tal como o definimos. Passamos o ponteiro da janela raiz como o segundo parâmetro para esta chamada de função, o que significa que queremos que o ecrã seja imediatamente ligado à janela da raiz. O último parâmetro é um ponteiro de retorno opcional que pode ser usado se quisermos manter um ponteiro para o ecrã criado.

Em **seguida*** gx_widget_show _ é chamado, o que torna visível a janela da raiz e todas as suas crianças, incluindo o ecrã _ *_hello_world_** .

Finalmente, o exemplo chama ***gx_system_start***. Esta função começa a executar o circuito de processamento de eventos do sistema GUIX.

## <a name="build-and-run-the-example"></a>Construir e Executar o Exemplo

Construir e executar o exemplo é específico para as suas ferramentas de construção e ambiente. No entanto, podemos definir o processo geral:

1. Criar um novo diretório e projeto de candidatura
1. Adicione estes ficheiros ao projeto:

    **new_example_resources.c**

    **new_example_specification.c**

    **new_example.c**

1. Adicione os ficheiros de suporte ao tempo de execução Win32 do caminho de instalação do GUIX Studio ***./win32_runtime***. Isto inclui o cabeçalho ThreadX e GUIX Win32 e os ficheiros da biblioteca de tempo de execução.
1. Adicione a biblioteca GUIX Win32 ***(gx.lib)*** ao projeto
1. Adicione a biblioteca ThreadX Win32 ***(tx.lib)*** ao projeto
1. Compilar, Ligar e Executar a aplicação!
