---
title: Capítulo 1 - Introdução ao Azure RTOS NetX POP3
description: A API do Cliente NetX Duo POP3 foi concebida para fornecer um sistema de transporte de correio eletrónico para pequenas estações de trabalho para aceder a gotas de correio do Cliente em Servidores POP3 para recuperar o correio do Cliente.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0143b142a39bbda28ae20d41adf08119b8b2f8f99d510a456743b4f447802833
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797233"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pop3"></a>Capítulo 1 - Introdução ao Azure RTOS NetX POP3

O Post Office Protocol Version 3 (POP3) é um protocolo concebido para fornecer um sistema de transporte de correio eletrónico para pequenas estações de trabalho para aceder a gotas de correio do Cliente em Servidores POP3 para recuperar o correio do Cliente. POP3 utiliza serviços de Protocolo de Controlo de Transmissão (TCP) para realizar transferência de correio. Por causa disso, pop3 é um protocolo de transferência de conteúdo altamente confiável.

No entanto, o POP3 não fornece operações extensivas no manuseamento de correio. Normalmente, o correio é descarregado pelo Cliente e depois eliminado da gota de correio do Servidor.

## <a name="netx-duo-pop3-client-requirements"></a>Requisitos do cliente NetX Duo POP3

### <a name="client-requirements"></a>Requisitos do cliente

A API do Cliente NetX POP3 requer uma instância IP netx anteriormente criada utilizando *nx_ip_create* e um pool de pacotes NetX previamente criado usando *nx_packet_pool_create*. Uma vez que o Cliente Pop3 da NetX Duo utiliza serviços TCP, o TCP deve ser ativado com a *chamada nx_tcp_enable* antes de utilizar a API do Cliente Pop3 do NetX Duo POP3 nessa mesma instância IP. O Cliente POP3 utiliza uma tomada TCP para ligar a um Servidor POP3 na porta POP3 do servidor. Isto é normalmente definido na *conhecida porta 110, embora nem o Cliente POP3 nem o Server sejam obrigados a utilizar esta porta.*

O tamanho do pacote de pacotes utilizado na criação do Cliente POP3 é configurável pelo utilizador em termos de carga útil de pacotes e número de pacotes disponíveis. Se o pacote for utilizado apenas no serviço pop3 Cliente criar, a carga útil do pacote não deve ser superior a 100-120 bytes dependendo do comprimento do nome de utilizador e da palavra-passe, ou a APOP digest. O comando USER com o nome de utilizador do anfitrião local é provavelmente a maior mensagem enviada pelo Cliente POP3. É possível partilhar o mesmo conjunto de pacotes no nx_ip_create (piscina de pacotes ip predefinidos) uma vez que a operatiosn interna de IP não requer uma carga útil de pacote muito grande para o envio e receção de dados de controlo TCP.

No entanto, geralmente não é vantajoso para o controlador Ethernet usar a mesma piscina de pacotes que a piscina de pacotes pop3 cliente. Geralmente, a carga útil da carga do pool de receber é definida a instância IP MTU (normalmente 1500 bytes) da interface de rede que é muito maior do que as mensagens pop3 Cliente. As mensagens POP3 recebidas normalmente seriam muito maiores do que mensagens pop3 de clientes de saída

## <a name="netx-duo-pop3-client-creation"></a>Criação de clientes NetX Duo POP3

Existem dois serviços para a criação do Cliente POP3. O serviço recomendado é *nxd_pop3_client_create* que requer um tipo de dados de endereço NXD_ADDRESS que aceita endereços IPv4 ou IPv6 para o servidor POP3. O outro cliente POP3 cria o serviço, *nx_pop3_client_create,* apenas aceita endereços IPv4 para o servidor POP3. Ambos os serviços ligam a porta da tomada TCP e ligam-se ao servidor POP3.

Depois de se ligar ao servidor POP3, a aplicação DO Cliente POP3 pode ligar *para nx_pop3_client _mail_items_get* para obter o número de itens de correio sentados na sua caixa de correio:

```C
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
    UINT *number_mail_items, ULONG *maildrop_total_size);
```

Se um ou mais itens estiverem na gota de correio do Cliente, a aplicação pode obter o tamanho de um item de correio específico, utilizando o serviço *nx_pop3_client_get_mail_item:*

```C
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *item_size);
```

O primeiro item de correio na gota de correio está no índice 1.

Para obter a mensagem de correio real, o pedido pode ligar para o serviço *nx_pop3_client_mail_item_get_message_data* para recuperar os pacotes de mensagens de correio até que o serviço indique que o último pacote é recebido pelo argumento de entrada final_packet:

```C
UINT nx_pop3_client_mail_item_message_get(
    NX_POP3_CLIENT *client_ptr,
    NX_PACKET **recv_packet_ptr,
    ULONG *bytes_retrieved,
    UINT *final_packet);
```

Para eliminar um item de correio específico, a aplicação chama *nx_pop3_client_mail_item_delete* com o mesmo índice utilizado na *chamada nx_pop3_client_get_mail_item* anterior.

O Cliente pode ser eliminado usando o serviço *nx_pop3_client_delete.* Note que cabe à aplicação eliminar o pacote de pacotes POP3 Client usando o serviço *nx_packet_pool_delete* já não tem qualquer utilidade para o mesmo.

## <a name="netx-duo-pop3-client-constraints"></a>Restrições de clientes NetX Duo POP3

Existem alguns constrangimentos na implementação do Cliente NetX Duo POP3:

1. O Cliente Pop3 do NetX Duo não suporta o comando AUTH, embora implemente a autenticação APOP utilizando o DIGEST-MD5 para a troca de autenticação do Servidor cliente.
2. O NetX Duo POP3 Client não implementa todos os comandos POP3 (por exemplo, os comandos TOP ou UIDL). Abaixo está uma lista de comandos que suporta:
   - NOOP
   - RSET

## <a name="netx-duo-pop3-client-login"></a>Login de clientes pop3 da NetX Duo POP3

Um Cliente Pop3 do NetX Duo deve autenticar-se (login) num Servidor POP3 para aceder a uma gota de correio. Pode fazê-lo utilizando os comandos USER/PASS e fornecendo um nome de utilizador e palavra-passe conhecidos pelo Servidor POP3, ou utilizando o comando APOP e a digestão MD5 descritas abaixo.

O nome de utilizador é tipicamente um nome de domínio totalmente qualificado (contém uma parte local e um nome de domínio, separado por um caracter '@'). Ao utilizar os comandos POP3 USER e PASS, o Cliente está a enviar o seu nome de utilizador e palavra-passe desencriptados pela Internet.

Para evitar o risco de segurança de um nome de utilizador e palavra-passe claros de texto, o Cliente Pop3 NetX Duo pode ser configurado para utilizar a autenticação APOP, definindo o parâmetro *APOP_authentication* no serviço *nxd_pop3_client_create:*

```C
UINT nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication,
    NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    NXD_ADDRESS *server_ip_address, ULONG server_port,
    CHAR *client_name,
    CHAR *client_password);
```

Ou apenas para aplicações IPv4, o *serviço nx_pop3_client_create:*

```C
UINT  nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    ULONG server_ip_address,
    ULONG server_port, CHAR *client_name,
    CHAR *client_password);
```

Quando o Cliente envia o comando APOP, assume como único argumento uma digestão MD5 contendo o domínio do servidor, a hora local e o ID do processo extraído da saudação do Servidor, além da palavra-passe do Cliente. O Servidor POP3 criará uma digestão MD5 contendo as mesmas informações e se a sua digestão MD5 corresponder à digestão MD5 do Cliente, o Cliente é autenticado.

Se a autenticação APOP falhar, o Cliente NetX Duo POP3 tentará a autenticação USER/PASS.

## <a name="the-pop3-client-maildrop"></a>A gota de correio do cliente POP3

O correio eletrónico do cliente é armazenado num Servidor POP3 numa caixa de correio ou "maildrop". Uma gota de correio do Cliente num Servidor POP3 é representada como uma lista baseada em 1 itens de correio. Ou seja, cada correio é referido pelo seu índice na lista de correio com o primeiro item de correio no índice 1 (não zero). Os comandos POP3 referem-se a itens de correio específicos pelo seu índice nesta lista.

## <a name="the-pop3-protocol-state-machine"></a>A máquina estatal do protocolo POP3

O protocolo POP3 requer que tanto o Cliente como o Servidor mantenham o estado da sessão POP3. Primeiro, o Cliente tenta ligar-se ao Servidor POP3. Se for bem sucedido, entra no protocolo POP3 que tem três estados distintos definidos pelo RFC 1939. O estado inicial é o estado de autorização no qual deve identificar-se ao Servidor. No estado de Autorização, o Cliente POP3 só pode emitir comandos USER e PASS, e por essa ordem, ou o comando APOP.

Uma vez autenticado o Cliente POP3, a sessão de Cliente entra no estado de Transação. Neste estado, o Cliente pode descarregar e solicitar a eliminação de correio. Os comandos permitidos no estado de Transação são LIST, STAT, RETR, DELE, RSET e QUIT. Normalmente, o Cliente POP3 envia um comando STAT seguido de uma série de comandos RETR (um para cada item de correio na sua gota de correio).

Uma vez que o Cliente emite o comando QUIT, a sessão POP3 entra no estado de Atualização em que inicia a desconexão TCP do Servidor. Para descarregar o correio em outra hora, a aplicação DO Cliente POP3 pode ligar para nx_pop3_client_mail_items_get para verificar se há novo correio na gota de correio.

### <a name="pop3-server-reply-codes"></a>Códigos de resposta do servidor POP3

- +OK O Servidor utiliza esta resposta para aceitar um comando do Cliente. O Servidor pode incluir informações adicionais após o '+OK' mas não pode assumir que o Cliente irá processar esta informação, exceto no caso de descarregar dados de mensagens de correio ou os comandos LIST ou DELE. Neste último caso, o 'argumento' após o comando refere o índice do item de correio na gota de correio do Cliente.
- -ERR O Servidor utiliza esta resposta para rejeitar um comando do Cliente. O Servidor pode enviar informações adicionais após o 'ERR' mas não pode assumir que o Cliente irá processar esta informação.

### <a name="sample-pop3-client---server-session"></a>Amostra do cliente POP3 - Sessão de Servidor

**Exemplo pop3 básico utilizando USER/PASS:**

```
S: <wait for connection on TCP port 110>
C: <open connection>
S: +OK POP3 server ready <1896.697170952@dbc.mtview.ca.us>
C: USER mrose
S: +OK mrose is valid
C: PASS mvan99
S: +OK mrose is logged in
C: STAT
S: +OK 2 320
C: RETR 1
S: +OK 120 octets
S: <the POP3 server sends message 1>
S: .
C: DELE 1
S: +OK message 1 deleted
C: RETR 2
S: +OK 200 octets
S: <the POP3 server sends message 2>
S: .
C: DELE 2
S: +OK message 2 deleted
C: QUIT
S: +OK POP3 server signing off (maildrop empty)
C: <close connection>
S: <wait for next connection>
```

**Exemplo pop3 básico usando APOP (e LIST em vez de STAT):**

```
S: <wait for connection on TCP port 110>
C: <open connection>
S: +OK POP3 server ready <1896.697170952@dbc.mtview.ca.us>
C: APOP mrose c4c9334bac560ecc979e58001b3e22fb
S: +OK mrose's maildrop has 2 messages (320 octets)
C: LIST
S: +OK 2 messages (320 octets)
S: 1 120
S: 2 200
S: .
C: RETR 1
S: +OK 120 octets
S: <the POP3 server sends message 1>
S: .
C: DELE 1
S: +OK message 1 deleted
C: RETR 2
S: +OK 200 octets
S: <the POP3 server sends message 2>
S: .
C: DELE 2
S: +OK message 2 deleted
C: QUIT
S: +OK dewey POP3 server signing off (maildrop empty)
C: <close connection>
S: <wait for next connection>
```

## <a name="rfcs-supported-by-netx-duo-pop3-client"></a>RFCs Suportados pelo Cliente POP3 da NetX Duo

NetX Duo Client POP3 está em conformidade com RFC 1939.
