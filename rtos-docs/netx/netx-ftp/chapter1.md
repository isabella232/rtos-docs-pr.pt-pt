---
title: Capítulo 1 - Introdução ao Azure RTOS NetX FTP
description: O Protocolo de Transferência de Ficheiros (FTP) é um protocolo concebido para transferências de ficheiros. A FTP utiliza serviços fiáveis de Protocolo de Controlo de Transmissão (TCP) para executar a sua função de transferência de ficheiros.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 35a7487720578ce8da578c490d96aa3c444ee818167b1bbd10833556e34b3dce
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799477"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-ftp"></a>Capítulo 1 - Introdução ao Azure RTOS NetX FTP

O Protocolo de Transferência de Ficheiros (FTP) é um protocolo concebido para transferências de ficheiros. A FTP utiliza serviços fiáveis de Protocolo de Controlo de Transmissão (TCP) para executar a sua função de transferência de ficheiros. Por causa disso, a FTP é um protocolo de transferência de ficheiros altamente fiável. FTP também é de alto desempenho. A transferência de ficheiros FTP real é realizada numa ligação FTP dedicada.

## <a name="ftp-requirements"></a>Requisitos FTP

Para funcionar corretamente, o pacote Azure RTOS NetX FTP requer que já tenha sido criada uma instância IP NetX. Além disso, a TCP deve ser ativada nessa mesma instância de PI. A parte do cliente FTP do pacote NetX FTP não tem requisitos adicionais.

A parte ftp server do pacote NetX FTP tem vários requisitos adicionais. Em primeiro lugar, requer acesso completo à *conhecida porta 21* da TCP para lidar com todos os pedidos de comando ftp do Cliente e *porta 20 bem conhecida* para lidar com todas as transferências de dados FTP do Cliente. O FtP Server também foi concebido para ser utilizado com o sistema de ficheiros incorporado FileX. Se o FileX não estiver disponível, o utilizador pode apresentar as porções do FileX utilizadas para o seu próprio ambiente. Isto é discutido em secções posteriores deste guia.

## <a name="ftp-constraints"></a>Restrições FTP

A norma FTP tem muitas opções no que diz respeito à representação de dados de ficheiros. À semelhança das implementações da Unix, a NetX FTP assume as seguintes restrições ao formato de ficheiro:

- Tipo de ficheiro: **Binário**
- Formato de ficheiro: **Apenas impressão**
- Estrutura de arquivo: **Apenas estrutura de arquivo**
- Modo de transmissão: **Apenas modo de fluxo**

## <a name="ftp-file-names"></a>Nomes de ficheiros FTP

Os nomes dos ficheiros FTP devem estar no formato do sistema de ficheiros-alvo (normalmente FileX). Devem ser nulas terminadas as cordas ASCII, com informações completas sobre o percurso, se necessário. Não existe um limite especificado para o tamanho dos nomes de ficheiros FTP na implementação do NetX FTP. No entanto, o tamanho da carga útil da piscina deve ser capaz de acomodar o caminho máximo e/ou nome do ficheiro.

## <a name="ftp-client-commands"></a>Comandos de clientes FTP

O FTP tem um mecanismo simples para abrir ligações e realizar operações de arquivo e diretório. Existe basicamente um conjunto de comandos FTP padrão que são emitidos pelo Cliente depois de uma ligação ter sido estabelecida com sucesso na *porta 21 bem conhecida* da TCP . O seguinte mostra alguns dos comandos FTP básicos:

### <a name="ftp-command-and-meaning"></a>Comando FTP e Significado

- **Caminho CWD**: *Alterar diretório de trabalho*
- **Nome de ficheiro DELE**: *Eliminar nome de ficheiro especificado*
- **Lista de anúncios**: *Obtenha listagem de diretório*
- **Diretório MKD**: *Faça novo diretório*
- **Diretório NLST**: *Obter listagem de diretório*
- **NOOP**: *Sem operação, retorna o sucesso*
- **Passe palavra-passe**: *Forneça senha para iniciar sessão*
- **PASV**: *Solicite o modo de transferência passiva*
- **Percurso DO PWD**: *Caminho atual do diretório de recolha*
- **QUIT**: *Terminar a ligação com o Cliente*
- **NOME DE ARQUIVO RETR**: *Ler ficheiro especificado*
- **Diretório RMD**: *Eliminar diretório especificado*
- **RNFR oldfilename**: *Especifique o ficheiro para renomear*
- **RNTO newfilename**: *Rebatize o ficheiro para o nome do ficheiro fornecido*
- **Nome de ficheiro STOR**: *Escreva ficheiro especificado*
- **TIPO I**: *Selecione a imagem de ficheiro binário*
- **Nome de utilizador user:** *Forneça o nome de utilizador para iniciar sessão*
- **PORT ip_address,porta**: *Fornecer endereço IP e porta de dados do Cliente*

Estes comandos ASCII são utilizados internamente pelo software Do Cliente NetX FTP para executar operações FTP com o FtP Server.

## <a name="ftp-server-responses"></a>Respostas do servidor FTP

O FTP Server utiliza a *conhecida porta TCP 21* para fazer os pedidos de comando do Cliente. Uma vez que o Servidor FTP processa o comando do Cliente, devolve uma resposta numérica de 3 dígitos no ASCII seguida de uma cadeia ASCII opcional. A resposta numérica é utilizada pelo software FTP Client para determinar se a operação foi bem sucedida ou falhou. As seguintes listas são várias as respostas do Servidor FTP aos comandos do Cliente:

### <a name="first-numeric-field-and-meaning"></a>Primeiro Campo Numérico e Significado

- **1xx**: *Estatuto preliminar positivo – outra resposta a chegar*.
- **2xx**: *Estado de conclusão positivo*.
- **3xx**: *Estado preliminar positivo – deve ser enviado outro comando*.
- **4xx**: *Condição temporária de erro*.
- **5xx**: *Condição de erro.*

### <a name="second-numeric-field-and-meaning"></a>Segundo Campo Numérico e Significado

- **x0x**: Erro de sintaxe no comando.
- **x1x**: Mensagem informativa.
- **x2x**: Ligação relacionada.
- **x3x**: Autenticação relacionada.
- **x4x**: Não especificado.
- **x5x**: Sistema de ficheiros relacionado.

Por exemplo, um pedido do Cliente para desligar uma ligação FTP com o comando QUIT será normalmente respondido com um código "221" do Servidor – se a desconexão for bem sucedida.

## <a name="ftp-passive-transfer-mode"></a>Modo de Transferência Passiva FTP

Por predefinição, o Cliente FTP NetX utiliza o modo de transporte ativo para trocar dados sobre a tomada de dados com o servidor FTP. O problema com este arranjo é que requer que o Cliente FTP abra uma tomada de servidor TCP para que o Servidor FTP se conecte. Isto representa um possível risco de segurança e pode ser bloqueado pela firewall do Cliente. O modo de transferência passiva difere do modo de transporte ativo, fazendo com que o servidor FTP crie a tomada do servidor TCP na ligação de dados. Isto elimina o risco de segurança (para o Cliente FTP).

Para permitir a transferência passiva de dados, as chamadas de aplicação *nx_ftp_client_passive_mode_set* num Cliente FTP previamente criado com o segundo argumento definido para NX_TRUE. Posteriormente, todos os serviços subsequentes do Cliente NetX FTP para transferência de dados (NLST, RETR, STOR) são tentados no modo de transporte passivo.

O Cliente FTP envia primeiro o comando PASV (sem argumentos). Se o servidor FTP suportar este pedido, retornará a resposta "OK" 227. Em seguida, o Cliente envia o pedido, por exemplo, RETR. Se o servidor recusar o modo de transferência passiva, o serviço Cliente NetX FTP devolve um estado de erro.

Para desativar o modo de transporte passivo e voltar ao modo de transporte ativo, a aplicação chama *nx_ftp_client_passive_mode_set* com o segundo argumento definido para NX_FALSE.

## <a name="ftp-communication"></a>Comunicação FTP

O FTP Server utiliza a *conhecida porta TCP 21* para fazer os pedidos do Cliente. Os Clientes FTP podem utilizar qualquer porta TCP disponível. A sequência geral dos eventos FTP é a seguinte:

### <a name="ftp-read-file-requests"></a>Pedidos de arquivo de leitura FTP

1. O cliente emite ligação TCP à porta do Servidor 21.
1. O servidor envia resposta "220" para o sucesso do sinal.
1. O cliente envia mensagem "USER" com "username".
1. O servidor envia resposta "331" para o sucesso do sinal.
1. O cliente envia mensagem "PASS" com "password".
1. O servidor envia resposta "230" para o sucesso do sinal.
1. O cliente envia mensagem "TYPE I" para transferência binária.
1. O servidor envia uma resposta "200" para o sucesso do sinal.
1. O cliente envia mensagem "PORT" com endereço IP e porta.
1. O servidor envia uma resposta "200" para o sucesso do sinal.
1. O cliente envia mensagem "RETR" com nome de ficheiro para ler.
1. O servidor cria uma tomada de dados e conecta-se com a porta de dados do cliente especificada no comando "PORT".
1. O servidor envia a resposta "125" para a leitura do ficheiro de sinal.
1. O servidor envia conteúdo de ficheiro através da ligação de dados. Este processo continua até que o ficheiro seja completamente transferido.
1. Quando terminada, o Servidor desliga a ligação de dados.
1. O servidor envia resposta "250" para a leitura do ficheiro de sinal é bem sucedida.
1. Os clientes enviam "QUIT" para terminar a ligação FTP.
1. O servidor envia a resposta "221" para desligar o sinal é bem sucedida.
1. O servidor desliga a ligação FTP.

Como mencionado anteriormente, a única diferença entre FTP que passa por IPv4 e IPv6 é que o comando PORT é substituído pelo comando EPRT para IPv6

Se o Cliente FTP fizer um pedido de leitura no modo de transferência passiva, a sequência de comando é a seguinte (linhas **audazes** indicam um passo diferente do modo de transferência ativo):

1. O cliente emite ligação TCP à porta do Servidor 21.
1. O servidor envia resposta "220" para o sucesso do sinal.
1. O cliente envia mensagem "USER" com "username".
1. O servidor envia resposta "331" para o sucesso do sinal.
1. O cliente envia mensagem "PASS" com "password".
1. O servidor envia resposta "230" para o sucesso do sinal.
1. O cliente envia mensagem "TYPE I" para transferência binária.
1. O servidor envia uma resposta "200" para o sucesso do sinal.
1. **O cliente envia mensagem "PASV".**
1. **O servidor envia resposta "227" e endereço IP e porta para o Cliente se conectar, para sinalizar o sucesso.**
1. O cliente envia mensagem "RETR" com nome de ficheiro para ler.
1. **O servidor cria a tomada do servidor de dados e ouve o pedido de ligação do Cliente nesta tomada utilizando a porta especificada na resposta "227".**
1. **O servidor envia a resposta "150" na tomada de controlo para a leitura do ficheiro de sinal iniciada.**
1. O servidor envia conteúdo de ficheiro através da ligação de dados. Este processo continua até que o ficheiro seja completamente transferido.
1. Quando terminada, o Servidor desliga a ligação de dados.
1. **O servidor envia a resposta "226" na tomada de controlo para a leitura do ficheiro de sinal é bem sucedida.**
1. O cliente envia "QUIT" para terminar a ligação FTP.
1. O servidor envia a resposta "221" para desligar o sinal é bem sucedida.
1. O servidor desliga a ligação FTP.

### <a name="ftp-write-requests"></a>Pedidos de escrita FTP

1. O cliente emite ligação TCP à porta do Servidor 21.
1. O servidor envia resposta "220" para o sucesso do sinal.
1. O cliente envia mensagem "USER" com "username".
1. O servidor envia resposta "331" para o sucesso do sinal.
1. O cliente envia mensagem "PASS" com "password".
1. O servidor envia resposta "230" para o sucesso do sinal.
1. O cliente envia mensagem "TYPE I" para transferência binária.
1. O servidor envia uma resposta "200" para o sucesso do sinal.
1. O cliente envia mensagem "PORT" com endereço IP e porta.
1. O servidor envia uma resposta "200" para o sucesso do sinal.
1. O cliente envia mensagem "STOR" com nome de ficheiro para escrever.
1. O servidor cria uma tomada de dados e conecta-se com a porta de dados do cliente especificada no comando "PORT".
1. O servidor envia a resposta "125" para a escrita do ficheiro de sinal já começou.
1. O cliente envia conteúdo de ficheiro através da ligação de dados. Este processo continua até que o ficheiro seja completamente transferido.
1. Quando terminada, o Cliente desliga a ligação de dados.
1. O servidor envia resposta "250" para a escrita de ficheiros de sinal é bem sucedida.
1. Os clientes enviam "QUIT" para terminar a ligação FTP.
1. O servidor envia a resposta "221" para desligar o sinal é bem sucedida.
1. O servidor desliga a ligação FTP.

Se o Cliente FTP fizer um pedido de escrita no modo de transferência passiva, a sequência de comando é a seguinte (linhas **audazes** indicam um passo diferente do modo de transferência ativo):

1. O cliente emite ligação TCP à porta do Servidor 21.
1. O servidor envia resposta "220" para o sucesso do sinal.
1. O cliente envia mensagem "USER" com "username".
1. O servidor envia resposta "331" para o sucesso do sinal.
1. O cliente envia mensagem "PASS" com "password".
1. O servidor envia resposta "230" para o sucesso do sinal.
1. O cliente envia mensagem "TYPE I" para transferência binária.
1. O servidor envia uma resposta "200" para o sucesso do sinal.
1. **O cliente envia mensagem "PASV".**
1. **O servidor envia resposta "227" e endereço IP e porta para o Cliente se conectar, para sinalizar o sucesso.**
1. O cliente envia mensagem "STOR" com nome de ficheiro para escrever.
1. **O servidor cria a tomada do servidor de dados e ouve o pedido de ligação do Cliente nesta tomada utilizando a porta especificada na resposta "227".**
1. **O servidor envia a resposta "150" na tomada de controlo para a escrita do ficheiro de sinal já começou.**
1. O cliente envia conteúdo de ficheiro através da ligação de dados. Este processo continua até que o ficheiro seja completamente transferido.
1. Quando terminada, o Cliente desliga a ligação de dados.
1. **O servidor envia a resposta "226" na tomada de controlo para a escrita do ficheiro de sinal é bem sucedida.**
1. O cliente envia "QUIT" para terminar a ligação FTP.
1. O servidor envia a resposta "221" para desligar o sinal é bem sucedida.
1. O servidor desliga a ligação FTP.

## <a name="ftp-authentication"></a>Autenticação FTP

Sempre que uma ligação FTP ocorra, o Cliente deve fornecer ao Servidor um nome de *utilizador* e *senha*. Alguns sites FTP permitem o que é chamado *FTP Anónimo,* que permite o acesso ftp sem um nome de utilizador e senha específicos. Para este tipo de ligação, deve ser fornecido "anónimo" para o nome de utilizador e a palavra-passe deve ser um endereço de e-mail completo.

O utilizador é responsável pelo fornecimento de rotinas de autenticação de login e logout NetX. Estes são fornecidos durante a função ***nx_ftp_server_create** _ e chamados a partir do processamento da palavra-passe. Se a função _login* voltar NX_SUCCESS, a ligação é autenticada e são permitidas operações FTP. Caso contrário, se a função *de login* devolver algo diferente NX_SUCCESS, a tentativa de ligação é rejeitada.

## <a name="ftp-multi-thread-support"></a>Suporte multi-rosca FTP

Os serviços do Cliente NetX FTP podem ser chamados a partir de várias linhas simultaneamente. No entanto, ler ou escrever pedidos para uma determinada instância do Cliente FTP deve ser feito em sequência a partir do mesmo fio.

## <a name="ftp-rfcs"></a>FTP RFCs

O NetX FTP está em conformidade com o RFC959 e com os RFCs relacionados.