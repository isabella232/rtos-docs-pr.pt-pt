---
title: Capítulo 1 - Introdução ao cliente SMTP Azure RTOS NetX Duo
description: O Simple Mail Transfer Protocol (SMTP) é um protocolo para a transferência de correio através das redes e da Internet.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f58a0c235f5c2cd108ba97afe676ffa9b66e715c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825795"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-smtp-client"></a>Capítulo 1 - Introdução ao cliente SMTP Azure RTOS NetX Duo

O Simple Mail Transfer Protocol (SMTP) é um protocolo para a transferência de correio através das redes e da Internet. Utiliza os serviços fiáveis do Protocolo de Controlo de Transmissão (TCP) para executar a sua função de transferência de conteúdo.

## <a name="netx-duo-smtp-client-requirements"></a>Requisitos do cliente NetX Duo SMTP

O Cliente SMTP NetX Duo requer a criação de uma instância IP NetX Duo e um pool de pacotes NetX Duo. O Cliente SMTP utiliza uma tomada TCP para ligar a um Servidor SMTP na *conhecida porta 25. Por conseguinte,* o TCP deve, em primeiro lugar, ser ativado através da chamada do serviço *nx_tcp_enable* numa instância IP previamente criada.

A chamada de criação do Cliente SMTP (nxd_smtp_client_create) requer um conjunto de pacotes previamente criado para transmitir comandos SMTP para o Servidor, bem como para o envio da mensagem de correio real. A carga útil do pacote depende do tamanho previsto do conteúdo do correio e deve permitir o cabeçalho TCP, IP e MAC. (Note que o cabeçalho IPv6 é de 40 bytes enquanto o cabeçalho IPv4 é de 20 bytes.)

Se toda a mensagem de correio não puder caber num único pacote, o Cliente SMTP atribui pacotes adicionais para conter o resto da mensagem.

## <a name="netx-duo-smtp-client-constraints"></a>Restrições de clientes NetX Duo SMTP

Enquanto o protocolo NetX Duo SMTP implementa as normas RFC 2821 e 2554, existem alguns constrangimentos:

1. O Cliente NetX Duo SMTP suporta apenas a autenticação LOGIN e PLAIN, mas não a autenticação da CRAM-MD5.
2. As mensagens do Cliente NetX Duo SMTP estão limitadas a um destinatário por item de correio e apenas uma mensagem de correio por ligação TCP com o servidor SMTP.
3. As opções VRFY, SEND, SOML, EXPN, SAML, ETRN, TURN e SIZE SMTP não são suportadas.
4. O Cliente SMTP não é o navegador de correio ("agente utilizador de correio") que é normalmente utilizado para criar a mensagem de correio. É apenas um "agente de transferência de correio". Fornecerá o processamento necessário do organismo de mensagens de correio para o transporte SMTP, conforme especificado no RFC 2821. Não verifica o conteúdo da sintaxe correta, por exemplo, o destinatário e a via inversa. Não existe qualquer restrição ao que está no tampão de correio, por exemplo, dados mime ou mensagens de texto claras. O formato de mensagem de correio, especificado no RFC 2822 para incluir cabeçalhos e corpo de mensagens está fora do âmbito da API do Cliente SMTP.

## <a name="commands-supported-by-netx-duo-smtp-client"></a>Comandos Suportados pelo Cliente SMTP Da NetX Duo

O Cliente SMTP NetX Duo usa os seguintes comandos durante uma sessão de correio com um Servidor SMTP.

- **EHLO** O Cliente gostaria de iniciar uma sessão que inclua alguns ou todos os serviços SMTP do protocolo de extensão disponíveis no SMTP Server. Esta é a predefinição.
- **HELO** O Cliente gostaria de iniciar uma sessão limitada aos serviços básicos de SMTP.
- **CORREIO** O Cliente gostaria que o Servidor recebesse o correio do Cliente.
- **Rio AUTH** O Cliente gostaria de iniciar a autenticação pelo Servidor.
- **RCPT** O Cliente gostaria de enviar uma caixa de correio de outro anfitrião para onde gostaria que o correio fosse entregue.
- **DADOS** O Cliente gostaria de iniciar o envio de dados de mensagens de correio para o Servidor.
- **DESISTE.** O Cliente gostaria de terminar a sessão.

## <a name="getting-started"></a>Introdução

A aplicação SMTP Client cria uma instância IP e permite que a TCP nessa instância IP. Em seguida, cria o Cliente SMTP utilizando o seguinte serviço:

```C
UINT nxd_smtp_client_create(NX_SMTP_CLIENT *client_ptr,
    NX_IP *ip_ptr, NX_PACKET_POOL
    *client_packet_pool_ptr,
    CHAR *username, CHAR *password,
    CHAR *from_address,
    CHAR *client_domain,
    UINT authentication_type,
    NXD_ADDRESS *server_address, UINT port);
```

O *client_packet_pool_ptr* é um ponteiro para um conjunto de pacotes previamente criado que o Cliente SMTP usará para enviar mensagens para o SMTP Server.

Note que uma aplicação deve fornecer um *from_address* para o dispositivo local e um endereço IP do servidor. Todos os endereços devem ser nomes de domínio totalmente qualificados. Um nome de domínio totalmente qualificado contém uma parte local e um nome de domínio, separado por um personagem '@'. Note que o Cliente SMTP não verifica a sintaxe do *from_address* ou do *recipient_address* no serviço nx_smtp_mail_send abaixo.

Após a criação do Cliente SMTP, a aplicação SMTP Client cria um item de correio com uma mensagem de correio SMTP devidamente formatada, e faz o pedido de envio de correio para o Cliente SMTP utilizando a seguinte API:

```C
UINT nx_smtp_mail_send(NX_SMTP_CLIENT *client_ptr,
    CHAR *recipient_address, UINT priority,
    CHAR *subject, CHAR *mail_body,
    UINT mail_body_length);
```

Não existe essencialmente nenhuma diferença na execução do Cliente SMTP sobre o IPv4 ou iPv6 do ponto de vista do utilizador. As diferenças entre os dois protocolos IP são tratadas na camada subjacente do Duo NetX.

Note que um pedido que pretenda enviar correio deve fornecer um endereço do destinatário na *chamada nx_smtp_client_mail.*

Para a autenticação, os nomes de utilizador podem ser nomes de domínio totalmente qualificados ou exibir nomes de utilizador. Isto depende da forma como o Servidor executa a autenticação.

A demonstração na secção Exemplo Pequeno mais tarde neste Manual do Utilizador mostra como a mensagem deve ser formatada. O estado se o artigo de correio tiver sido enviado com sucesso será NX_SUCCESS. Se ocorrer um erro, seja um erro interno, uma ligação TCP partida ou receber um código de erro de resposta do Servidor, *nx_smtp_mail_send* retornará um estado de erro não zero.

Ao enviar um item de correio, o NetX Duo SMTP Client cria uma nova ligação TCP com o servidor SMTP e inicia uma sessão SMTP. Nesta sessão, o Cliente envia uma série de comandos para o SMTP Server como parte do protocolo SMTP, culminando no envio da mensagem de correio real. A ligação TCP é então encerrada, independentemente do resultado da sessão SMTP.

Após a transmissão de correio, independentemente do sucesso ou da falha, o Cliente SMTP é devolvido ao estado 'inicial' e pode ser utilizado para outra sessão de transferência de correio.

## <a name="netx-duo-smtp-authentication"></a>Autenticação SMTP da NetX Duo

A autenticação é uma forma de os Clientes SMTP provarem a sua identidade ao SMTP Server e terem o seu correio entregue como utilizadores de confiança. A maioria dos servidores SMTP comerciais exigem que os Clientes sejam autenticados.

Normalmente, os dados de autenticação consistem no nome de utilizador e na palavra-passe do remetente. Durante um desafio de autenticação, o Servidor solicita esta informação e o Cliente responde enviando os dados solicitados em formato codificado. O Servidor descodifica os dados e tenta encontrar uma correspondência na sua base de dados de utilizadores. Se for encontrado, o Servidor indica que a autenticação é bem sucedida. A autenticação SMTP é definida no [RFC 2554](http://www.ietf.org/rfc/rfc2554.txt).

Existem dois sabores de autenticação, nomeadamente *básicos* e *digeridos.* A Digest não é suportada no atual Cliente SMTP da NetX Duo, e não será discutida aqui. A autenticação básica é equivalente ao *nome* e autenticação de *senha* acima descrito. Na autenticação básica SMTP, o nome e as palavras-passe estão codificados com base64. A vantagem da autenticação básica é a sua facilidade de implementação e uso generalizado. A principal desvantagem da autenticação básica é o nome e os dados da palavra-passe são transmitidos abertamente no pedido.

### <a name="plain-authentication"></a>Autenticação simples

O Cliente SMTP NetX Duo envia um comando AUTH com o parâmetro PLAIN. Se o SMTP Server NetX Duo suportar este tipo de autenticação, responderá com um código de resposta 334. O Cliente responde com um único nome de utilizador codificado de base64 e mensagem de senha para o Servidor. Se o Servidor determinar que a autenticação do Cliente é bem sucedida, responde com o código de sucesso 235.

### <a name="login-authentication"></a>Autenticação de login

O Cliente SMTP NetX Duo envia um comando AUTH com o parâmetro LOGIN. Se o NetX Duo SMTP Server suportar este tipo de autenticação, responderá com um código de resposta 334 como o início do 'desafio' de autenticação. Envia uma solicitação codificada base64 para o Cliente que é tipicamente "Nome de utilizador". O Cliente descodifica o pedido e responde com um nome de utilizador codificado de base64. Se o Servidor aceitar o nome de utilizador do Cliente, envia uma mensagem codificada base64 para a palavra-passe do Cliente. O Cliente responde com uma senha codificada base64. Se o Servidor determinar que a autenticação do Cliente é bem sucedida, responde com o código de sucesso 235.

### <a name="no-authentication"></a>Sem Autenticação

Alguns Servidores SMTP estão configurados sem autenticação. Em caso afirmativo, a sua resposta de 250 à mensagem EHLO do Cliente não listará nenhum tipo de autenticação. No entanto, nenhum tipo de autenticação listado não significa necessariamente que o Servidor não exija ou suporte a autenticação. Se o Cliente estiver configurado para autenticação DE PLAIN ou LOGIN nesta situação, a tarefa de thread do Cliente NetX Duo será por defeito para PLAIN. Se o Cliente estiver configurado para NENHUM, o passo de autenticação é ignorado e o estado SMTP avança para o estado do CORREIO.

Note que se o Cliente estiver configurado para não autenticação e o SMTP Server fizer a autenticação de suporte, o tipo de autenticação do Cliente é mudado para PLAIN.

## <a name="rfcs-supported-by-netx-duo-smtp-client"></a>RFCs Suportados pelo Cliente SMTP da NetX Duo

A API do Cliente SMTP NetX Duo está em conformidade com o RFC2821 "Simple Mail Transfer Protocol" e com o RFC 2554 "Extensão de Serviço SMTP para autenticação. “
