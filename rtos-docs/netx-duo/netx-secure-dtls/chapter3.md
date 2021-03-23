---
title: Capítulo 3 - Descrição funcional do Azure RTOS NetX Secure DTLS
description: Este capítulo contém uma descrição funcional do Azure RTOS NetX Secure DTLS.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 468f1dc8a8334dc89064594b29dc8cfabd7d8fae
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826978"
---
# <a name="chapter-3-functional-description-of-azure-rtos-netx-secure-dtls"></a>Capítulo 3: Descrição funcional do Azure RTOS NetX Secure DTLS

## <a name="execution-overview"></a>Visão geral da execução

Este capítulo contém uma descrição funcional do Azure RTOS NetX Secure DTLS. Existem dois tipos primários de execução de programas numa aplicação DTLS NetX Secure: inicialização e interface de aplicação. 

NetX Secure assume a existência de ThreadX e NetX/NetXDuo. Da ThreadX, requer execução de fios, suspensão, temporizadores periódicos e instalações de exclusão mútua. A partir da NetX/NetXDuo requer as instalações de rede UDP e IP e os controladores.

## <a name="datagram-transport-layer-security-dtls-and-transport-layer-security-tls"></a>Segurança da camada de transporte de datagram (DTLS) e segurança da camada de transporte (TLS)

O NetX Secure DTLS implementa a versão 1.2 do protocolo de segurança da camada de transporte de dados 1.2 definida no RFC 6347. A versão 1.0 do DTLS foi definida no RFC 4347 e correspondeu à versão 1.1 da TLS. Devido ao DTLS ser essencialmente uma extensão ao TLS, foi decidido que a versão seguinte utilizaria o mesmo número de versão que a versão TLS correspondente. Assim, não existe a versão DTLS 1.1, uma vez que a versão 1.2 do DTLS corresponde à versão 1.2 do TLS.

> [!NOTE]
> NetX Secure suporta a versão DTLS 1.2. O DTLS 1.0 (RFC 4347) **não** está atualmente suportado.

*Secure Sockets Layer* (SSL) foi o nome original de TLS antes de se tornar um padrão em RFC 2246 e "SSL" é frequentemente usado como um nome genérico para os protocolos TLS. A última versão do SSL foi 3.0, e tLS 1.0 é por vezes referida como versão SSL 3.1. Todas as versões do protocolo oficial "SSL" são consideradas obsoletas e inseguras e atualmente o NetX Secure não fornece uma implementação SSL.

O TLS especifica um protocolo para gerar *teclas* de sessão que são criadas durante o *aperto de mão* TLS entre um cliente TLS e servidor e essas teclas são usadas para encriptar dados enviados pela aplicação durante a sessão TLS. 

O DTLS é intimamente associado ao TLS, uma vez que os mecansos de segurança subjacentes são partilhados entre os protocolos. No entanto, o TLS foi concebido para trabalhar ao longo de um protocolo de camada de transporte que fornece garantias sobre a entrega e encomenda de pacotes (quase sempre TCP na prática) e não funcionará sobre um protocolo pouco fiável como a UDP. Foi precisamente por causa da UDP que o DTLS foi introduzido: o DTLS foi concebido para lidar com a natureza pouco fiável da UDP e protocolos semelhantes. Fá-lo incluindo a lógica de encomenda e fiabilidade (por exemplo, retransmissão de dados abandonados) semelhante a protocolos fiáveis como o TCP.

Uma discussão completa sobre OTS está incluída no Capítulo 3 do Guia do Utilizador NetX Secure TLS, pelo que este documento irá focar-se nas diferenças entre TLS e DTLS.

### <a name="dtls-record-header"></a>Cabeçalho de registo DTLS

Qualquer registo DTLS válido deve ter um cabeçalho DTLS, como mostra a Figura 1. O cabeçalho é o mesmo que o TLS com a adição de dois novos campos: a época de 16 *bits* e o número de *sequência* de 48 bits, descrito abaixo.

![Diagrama de um cabeçalho de disco DTLS.](media/image2.png)

**Figura 1 - Cabeçalho de registo DTLS**

Os campos do cabeçalho de registo TLS são definidos da seguinte forma:

| Campo de cabeçalho TLS | Objetivo  |
| ---------------- | --------- |
| **Tipo de mensagem de 8 bits** | Este campo contém o tipo de registo DTLS enviado. Os tipos válidos são os seguintes:<br />- ChangeCipherSpec: 0x14<br />- Alerta: 0x15<br />- Aperto de mão: 0x16<br />- Dados da aplicação: 0x17<br /> |
| **Versão do protocolo de 16 bits** | Este campo contém a versão do protocolo DTLS. Os valores válidos são os seguintes:<br />- DTLS 1.1: 0xFEFD |
|  **Época de 16 bits** |  Este campo contém a "época" DTLS, que é um contador que é incrementado cada vez que o estado de encriptação é alterado (por exemplo, ao gerar novas teclas de sessão).  |
|  **Número de sequência de 48 bits** |  Este campo contém um número de sequência que identifica este registo em particular. É utilizado pela DTLS para manter a ordem de registo e verificar a necessidade de retransmissão. |
|  **Comprimento de 16 bits** |  Este campo contém o comprimento dos dados encapsulados no registo DTLS.  |

### <a name="dtls-handshake-record-header"></a>Cabeçalho do recorde de aperto de mão DTLS

Qualquer registo de aperto de mão DTLS válido deve ter um cabeçalho de aperto de mão DTLS, como mostra a Figura 2.

![Diagrama de um cabeçalho do Disco de Aperto de Aperto de Mão DTLS.](media/image3.png)

**Figura 2 - Cabeçalho de recorde de aperto de mão DTLS**

Os campos do cabeçalho de registo do aperto de mão DTLS são definidos da seguinte forma:

| Campo de cabeçalho TLS | Objetivo |
| ---------------- | ------------------------------------------------ |
| **Tipo de mensagem de 8 bits** | Este campo contém o tipo de registo DTLS enviado. Os tipos válidos são os seguintes:<br />- ChangeCipherSpec: 0x14<br />- Alerta: 0x15<br />- Aperto de mão: 0x16<br />- Dados da aplicação: 0x17 |
|  **Época de 16 bits** | Este campo contém a "época" DTLS, que é um contador que é incrementado cada vez que o estado de encriptação é alterado (por exemplo, ao gerar novas teclas de sessão). |
|  **Número de sequência de 48 bits** | Este campo contém um número de sequência que identifica este registo em particular. É utilizado pela DTLS para manter a ordem de registo e verificar a necessidade de retransmissão. |
|  **Versão do protocolo de 16 bits** | Este campo contém a versão do protocolo DTLS. Os valores válidos são os seguintes:<br />- DTLS 1.1: 0xFEFD |
| **Comprimento de 16 bits** | Este campo contém o comprimento dos dados encapsulados no registo DTLS. |
| **Tipo de aperto de mão de 8 bits** | Este campo contém o tipo de mensagem de aperto de mão. Os valores válidos são os seguintes:<br />- HelloRequest: 0x00<br />- ClientHello: 0x01<br />- ServerHello: 0x02<br />- Certificado: 0x0B<br />- ServerKeyExchange: 0x0C<br />- CertificadoRequest: 0x0D<br />- ServerHelloDone: 0x0E<br />- CertificaçãoVerifical: 0x0F<br />- ClientKeyExchange: 0x10<br />- Concluída | 0x14 |
| **Comprimento de 24 bits** | Este campo contém o comprimento dos dados da mensagem de aperto de mão. |
| **Número de sequência de 16 bits** | Este campo contém um número de sequência. |

### <a name="the-dtls-handshake-and-dtls-session"></a>O aperto de mão dTLS e a Sessão DTLS

Um aperto de mão típico do DTLS é mostrado na Figura 3. É quase idêntico ao típico aperto de mão TLS com uma diferença importante – quando a mensagem ClientHello é enviada pela primeira vez, o servidor responde com uma nova mensagem específica do DTLS, *HelloVerifyRequest* que contém um "cookie". O Cliente DTLS deve responder com uma segunda mensagem ClientHello contendo esse cookie antes que o aperto de mão possa prosseguir. Este mecanismo foi adicionado ao DTLS para evitar certos ataques de Negação de Serviço (DoS), uma vez que a UDP é um protocolo sem ligação (a TCP requer uma ligação/porta dedicada para que o TLS não sofra do mesmo problema).

Um aperto de mão DTLS começa quando o Cliente envia uma mensagem *ClientHello* para um servidor DTLS, indicando o seu desejo de iniciar uma sessão de DTLS. A mensagem contém informações sobre a encriptação que o cliente gostaria de usar para a sessão, juntamente com as informações usadas para gerar as teclas de sessão mais tarde no aperto de mão. Até que as teclas de sessão sejam geradas, todas as mensagens no aperto de mão DTLS não são encriptadas. Como mencionado acima, o DTLS Server pode enviar um HelloVerifyRequest em resposta ao ClientHello, forçando o cliente a responder com um segundo ClientHello atualizado.

Ao receber a segunda mensagem ClientHello, o DTLS Server verificará o cookie e, se estiver correto, responderá com uma mensagem ServerHello indicando uma seleção das opções de encriptação fornecidas pelo cliente. O ServerHello é seguido por uma mensagem de Certificado, na qual o servidor fornece um certificado digital para autenticar a sua identidade ao cliente (se for utilizada a verificação X.509). Finalmente, o servidor envia uma mensagem ServerHelloDone para indicar que não tem mais mensagens para enviar. O servidor pode enviar opcionalmente outras mensagens seguindo o ServerHello e, em alguns casos, pode não enviar uma mensagem de Certificado (como quando são utilizadas chaves pré-partilhadas), daí a necessidade da mensagem ServerHelloDone.

Uma vez que o cliente tenha recebido todas as mensagens do servidor, tem informações suficientes para gerar as teclas de sessão. O TLS/DTLS faz isso criando uma parte partilhada de dados aleatórios *chamados Pre-Master Secret*, que é um tamanho fixo e é usado como uma semente para gerar todas as chaves necessárias uma vez que a encriptação é ativada. O Segredo Pré-Mestre é encriptado utilizando o algoritmo de chave pública (por exemplo, RSA) especificado nas mensagens Hello (ver abaixo para obter informações sobre algoritmos de chaves públicas) e a chave pública fornecida pelo servidor no seu certificado. Uma funcionalidade opcional TLS/DTLS chamada Chaves Pré-Partilhadas (PSK) permite cifrasuites que não usam um certificado, mas em vez disso usam um valor secreto partilhado entre os anfitriões (geralmente através de transferência física ou outro método seguro). Quando o PSK está ativado, a chave secreta pré-partilhada é usada para gerar o Segredo Pré-Mestre. Consulte a secção em Chaves Pré-Partilhadas em "Métodos de Autenticação" abaixo.

Num habitual aperto de mão TLS/DTLS, o Pre-Master Secret encriptado é enviado para o servidor na mensagem ClientKeyExchange. O servidor, ao receber a mensagem ClientKeyExchange, desencripta o Segredo Pré-Mestre usando a sua chave privada e procede à geração das teclas de sessão em paralelo com o cliente TLS/DTLS.

Uma vez geradas as teclas de sessão, todas as mensagens adicionais podem ser encriptadas utilizando o algoritmo de tecla privada (por exemplo, AES) selecionado nas mensagens Hello. Uma última mensagem não encriptada chamada ChangeCipherSpec é enviada pelo cliente e pelo servidor para indicar que todas as mensagens adicionais serão encriptadas.

A primeira mensagem encriptada enviada pelo cliente e pelo servidor é também a mensagem final de aperto de mão TLS, chamada Finished. Esta mensagem contém um haxixe de todas as mensagens de aperto de mão recebidas e enviadas. Este haxixe é utilizado para verificar se nenhuma das mensagens no aperto de mão foi adulterada ou corrompida (indicando uma possível violação da segurança).

Uma vez recebidas as mensagens Acabadas e verificadas as hashes de aperto de mão, inicia-se a sessão TLS/DTLS e a aplicação começa a enviar e receber dados. Todos os dados enviados por ambos os lados durante a sessão TLS/DTLS são primeiro haxixe usando o algoritmo de haxixe escolhido nas mensagens Hello (para fornecer integridade da mensagem) e encriptado usando o algoritmo de chave privada escolhido com as teclas de sessão geradas.

Finalmente, uma sessão TLS/DTLS só pode ser terminada com sucesso se o Cliente ou o Servidor optarem por fazê-lo. Uma sessão truncada é considerada uma falha de segurança (uma vez que um intruso pode estar a tentar evitar que todos os dados sejam enviados) pelo que é enviada uma notificação especial quando ambos os lados querem terminar a sessão, chamado alerta CloseNotify. Tanto o cliente como o servidor devem enviar e processar um alerta CloseNotify para uma paragem de sessão bem sucedida.

![Diagrama de uma sessão típica de aperto de mão DTLS.](media/image4.png)

**Figura 3- Aperto de mão típico do DTLS**

### <a name="initialization"></a>Inicialização

A pilha NetX ou NetXDuo deve ser inicializada antes da utilização do DTLS NetX Secure. Consulte o Guia de Utilizador NetX ou NetXDuo para obter informações sobre como inicializar corretamente a pilha TCP/IP para a operação UDP.

Uma vez inicializado o NetX UDP, o DTLS pode ser ativado. Internamente, todo o tráfego e processamento da rede DTLS é tratado pela stack NetX/NetXDuo sem necessidade de intervenção do utilizador. No entanto, o DTLS tem alguns requisitos específicos que devem ser tratados separadamente da pilha de rede subjacente. A operação do Cliente DTLS estes parâmetros são atribuídos ao bloco de controlo DTLS chamado ***NX_SECURE_DTLS_SESSION** _. Para a operação do DTLS Server, o bloco de controlo chama-se _ *_NX_SECURE_DTLS_SERVER_** e contém a infraestrutura necessária para lidar com várias sessões de DTLS numa única porta UDP – note que esta é diferente da TLS onde cada sessão de TLS está ligada a uma única porta TCP.

Os dois modos DTLS, Server e Cliente, podem ser ativados numa aplicação (mas apenas um modo por tomada NetX), e cada um tem os seus próprios requisitos específicos, detalhados abaixo.

### <a name="initialization--dtls-server"></a>Inicialização – DTLS Server

O modo NetX Secure DTLS Server difere do modo TLS Server devido à utilização do UDP para o protocolo de transporte de rede subjacente. Com o TCP, a porta está ligada a um único hospedeiro remoto durante a sessão TLS. A UDP não tem noção de estado no que diz respeito ao hospedeiro remoto, pelo que os pedidos de DTLS de diferentes anfitriões serão todos recebidos na mesma interface UDP. Por conseguinte, o DTLS deve manter o estado da sessão em vez de depender da tomada como com tls e TCP. Por esta razão, o bloco de controlo do Servidor DTLS (NX_SECURE_DTLS_SERVER) mantém um mapeamento de informações remotas do anfitrião (endereço IP e porta) para sessões de DTLS. Todos os dados de entrada na tomada UDP atribuídos a um Servidor DTLS serão mapeados para uma sessão DTLS existente ou nova com base no anfitrião remoto. Por esta razão, a criação do servidor DTLS requer vários parâmetros adicionais para além do que o Cliente TLS e DTLS precisa.

Além do bloco de controlo do Servidor DTLS, cifrasuites TLS e tampão de scratchspace/metadados cifra, os Servidores DTLS exigem um tampão para manter as sessões de DTLS e um tampão de montagem de pacotes usado para desencriptar registos DTLS de entrada.

Além dos amortecedores de sessão, os Servidores DTLS requerem um *Certificado Digital*, que é um documento utilizado para identificar o servidor TLS ao cliente TLS de ligação, e os certificados correspondentes *Private Key*, normalmente para o algoritmo de encriptação RSA. A norma International Telecommunications Union X.509 especifica o formato de certificado utilizado pela TLS/DTLS e existem inúmeros utilitários para a criação de certificados digitais X.509.

Para o NetX Secure DTLS, o certificado X.509 deve ser codificado bináriamente utilizando o formato de Regras de Codificação (DER) distintos de ASN.1. DER é o formato binário padrão TLS over-the-wire para certificados.

A chave privada associada ao certificado fornecido deve estar em DER-Encoded formato PKCS#1. A chave privada é utilizada apenas no dispositivo e nunca será transmitida através do fio. Mantenha as chaves privadas seguras, pois fornecem a segurança das comunicações TLS/DTLS!

Para inicializar o certificado DTLS Server, a aplicação deve fornecer um ponteiro a um tampão contendo o certificado X.509 codificado pelo DER e dados chave privados opcionais de PKCS#1 RSA utilizando o serviço ***de nx_secure_x509_certificate_intialize,*** que povoa a estrutura **NX_SECURE_X509_CERT** com os dados de certificado apropriados para utilização por TLS.

Uma vez inicializado o certificado do servidor, este deve ser adicionado ao bloco de controlo TLS utilizando o serviço ***nx_secure_dtls_server_local_certificate_add.***

Uma vez adicionado o certificado do servidor ao bloco de controlo do Servidor DTLS, o servidor pode ser utilizado para comunicações DTLS seguras (ver exemplo acima).

### <a name="initialization--dtls-client"></a>Inicialização – Cliente DTLS

O modo de cliente NetX Secure DTLS é simples de funcionar em comparação com o servidor DTLS, uma vez que existe apenas uma única ligação de saída ao hospedeiro remoto sobre a tomada UDP.

Para configurar um Cliente DTLS, requer uma Loja de *Certificados Fidedignas,* que é uma coleção de certificados digitais codificados X.509 das Autoridades de Certificados Fidedignas (CA's). Estes certificados são assumidos pelo protocolo DTLS como "confiáveis" e servem de base para autenticar certificados fornecidos por entidades de servidores DTLS à aplicação do Cliente DTLS Seguro NetX.

Um certificado de CA fidedigno pode ser *auto-assinado* ou assinado por outra AC, caso em que esse certificado é chamado de *Ac Intermediário* (ICA). Numa aplicação típica de TLS/DTLS, o servidor fornece os certificados ICA juntamente com o seu certificado de servidor, mas o único requisito para a autenticação bem sucedida é que uma cadeia de emitentes (certificados usados para assinar outros certificados) pode ser rastreada do certificado de servidor de volta para um certificado de CA fidedigno na Loja de Certificados Fidedignos. Esta cadeia é conhecida como uma *cadeia de fiéis* ou cadeia de *certificados.*

Para inicializar um certificado ca ou ica fidedigno, o pedido deve fornecer um ponteiro a um tampão contendo o certificado X.509 codificado pelo DER utilizando o serviço ***nx_secure_x509_certificate_intialize** _ que povoa a estrutura _ *NX_SECURE_X509_CERT** com os dados de certificado adequados para utilização pela TLS.

O Cliente DTLS também precisa de espaço para que o certificado do servidor de entrada seja atribuído (assumindo que não está a ser utilizado um modo chave pré-partilhado) e um tampão para a montagem de pacotes em registos DTLS a serem desencriptados. Estes tampão são passados como parâmetros para o serviço ***nx_secure_dtls_session_create*** (ver referência API para mais informações).

Os certificados fidedignos que foram inicializados são adicionados ao bloco de controlo de sessão DTLS criado utilizando o serviço ***nx_secure_dtls_session_trusted_certificate_add.*** A não adição de um certificado fará com que a sessão do Cliente DTLS falhe, uma vez que não haverá forma de o protocolo DTLS autenticar os anfitriões de servidores remotos.

Uma vez criada a Loja de Certificados Fidedignos, a sessão poderá ser utilizada para estabelecer uma ligação segura ao Cliente TLS.

### <a name="application-interface-calls"></a>Chamadas de Interface de Aplicação

As aplicações DTLS NetX Secure normalmente farão chamadas de função a partir de fios de aplicação que funcionam sob o ThreadX RTOS. Alguma inicialização, nomeadamente para os protocolos de comunicações de rede subjacentes (por exemplo, UDP e IP) pode ser chamada de ***tx_application_define*.** Consulte o Guia do Utilizador NetX/NetXDuo para obter mais informações sobre a inicialização das comunicações de rede.

O DTLS faz uso pesado de rotinas de encriptação que são operações intensivas de processador. Geralmente, estas operações serão realizadas no contexto da linha de chamada.

### <a name="dtls-session-start"></a>Início da sessão DTLS

O DTLS requer um protocolo de rede de camadas de transporte subjacente para funcionar. O protocolo normalmente utilizado é TCP. Para estabelecer uma sessão NetX Secure TLS, **NX_UDP_SOCKET** deve ser criada e passada para o serviço **_de nx_secure_dtls_client_session_start_** para clientes DTLS.

Os Servidores DTLS funcionam de forma diferente. A tomada UDP utilizada para os pedidos do Cliente DTLS está contida no bloco de controlo NX_SECURE_DTLS_SERVER e é inicializada na chamada para ***nx_secure_dtls_server_create** _, que toma a porta UDP local como parâmetro. O _*_nx_secure_dtls_server_start_*_ de serviço é então utilizado para iniciar o DTLS Server para lidar com pedidos de entrada. Todos os pedidos de entrada são tratados em rotinas de retorno fornecidas a _nx_secure_dtls_server_create*: um para ligações e outro para receber notificações. Cabe ao pedido de decisão a partir da sessão DTLS quando for recebida uma notificação de ligação (a chamada de notificação de ligação é invocada pela DTLS) ligando ***nx_secure_dtls_server_session_start**_. A aplicação também deve tratar os dados de entrada quando a chamada de notificação recebida for invocada (que segue um aperto de mão DTLS completo) chamando _*_nx_secure_dtls_session_receive_**. Os pormenores deste facto são fornecidos no exemplo acima referido e na referência da API para cada um dos serviços acima mencionados.

### <a name="dtls-packet-allocation"></a>Alocação de pacotes DTLS

O NetX Secure DTLS utiliza a mesma estrutura de pacotes que o NetX/NetXDuo TCP (***NX_PACKET** _) exceto que, em vez de ligar para o serviço _*_nx_packet_allocate,_*_ o serviço _ *_nx_secure_dtls_packet_allocate_** deve ser chamado para que o espaço para o cabeçalho DTLS possa ser devidamente atribuído.

### <a name="dtls-session-send"></a>DTLS Sessão Enviar

Uma vez iniciada a sessão TLS, a aplicação poderá enviar dados utilizando o serviço ***nx_secure_dtls_session_send.*** O serviço de envio é idêntico em uso ao serviço ***nx_udp_socket_send** _, tomando uma estrutura de dados _ *_NX_PACKET_** contendo os dados enviados, um endereço IP alvo e uma porta UDP alvo.

> [!IMPORTANT]
> Ao enviar dados utilizando nx_secure_dtls_session_send, é importante utilizar o mesmo endereço IP e porta que foram utilizados para estabelecer a sessão DTLS, a menos que exista um mecanismo para mover a sessão para um novo endereço e porta UDP on-the-fly (isto não é comum).

Quaisquer dados enviados através do DTLS serão encriptados pela pilha NX Secure DTLS e pelas rotinas de encriptação configuradas antes de serem enviados.

### <a name="dtls-session-receive"></a>Sessão DTLS receber

Uma vez iniciada a sessão DTLS, a aplicação pode começar a receber dados utilizando o serviço ***nx_secure_Dtls_session_receive** _ . Tal como a Sessão DTLS envia, este serviço é idêntico em uso para _*_nx_udp_socket_receive_**, exceto que os dados de entrada são desencriptados e verificados pela pilha DTLS antes de serem devolvidos na estrutura do pacote.

### <a name="tls-session-close"></a>Sessão TLS fechar

Uma vez concluída uma sessão DTLS, tanto o cliente DTLS como o servidor devem enviar um alerta CloseNotify para o outro lado para encerrar a sessão. Ambas as partes devem receber e processar o alerta para garantir uma paragem de sessão bem sucedida.

Se o anfitrião remoto enviar um alerta CloseNotify, qualquer chamada para o serviço ***nx_secure_dtls_session_receive** _ processará o alerta, enviará o alerta correspondente de volta para o hospedeiro remoto e devolverá um valor de _*_NX_SECURE_TLS_SESSION_CLOSED_**. Uma vez encerrada a sessão, quaisquer outras tentativas de enviar ou receber dados com essa sessão DTLS falharão.

Se a aplicação pretender encerrar a sessão TLS, o serviço ***nx_secure_dtls_session_end** _ deve ser chamado. O serviço enviará o alerta CloseNotify e processará a resposta CloseNotify. Se a resposta não for recebida, será devolvido um valor de erro de _ *_NX_SECURE_TLS_SESSION_CLOSE_FAIL_** indicando que a sessão DTLS não foi totalmente encerrada, uma possível falha de segurança.

### <a name="tlsdtls-alerts"></a>Alertas TLS/DTLS

TLS/DTLS é projetado para fornecer a máxima segurança, por isso qualquer comportamento errante no protocolo é considerado uma potencial violação de segurança. Por esta razão, quaisquer erros no processamento de mensagens ou encriptação/desencriptação são considerados erros fatais que terminam o aperto de mão ou a sessão imediatamente.

Embora os erros de manuseamento de uma aplicação local sejam relativamente simples, o anfitrião remoto precisa de saber que ocorreu um erro para lidar adequadamente com a situação e evitar eventuais possíveis falhas de segurança. Por esta razão, o TLS/DTLS enviará uma mensagem *de alerta* ao anfitrião remoto em qualquer erro.

Os alertas são tratados da mesma forma que qualquer outra mensagem TLS/DTLS e são encriptados durante a sessão para impedir que um intruso recolha informações do tipo de alerta fornecido. Durante o aperto de mão, os alertas enviados são limitados no âmbito para limitar a quantidade de informação que poderia ser obtida por um potencial atacante.

O alerta CloseNotify, usado para encerrar a sessão TLS/DTLS, é o único alerta não fatal. Embora seja considerado um alerta e enviado como uma mensagem de alerta, um CloseNotify é diferente de outros alertas na medida em que não indica que tenha ocorrido um erro.

### <a name="tlsdtls-session-renegotiation-and-resumption"></a>TLS/DTLS Sessão renegociação e retoma

O TLS apoia a noção de "renegociação" que é simplesmente uma renegociação dos parâmetros da sessão TLS no contexto de uma sessão TLS existente.

O *reinício da* sessão TLS não deve ser confundido com *a renegociação* da sessão , apesar de algumas semelhanças. Onde a *renegociação* da sessão envolve iniciar um novo aperto de mão dentro de uma sessão TLS existente, *o recomeço da* sessão é uma característica puramente opcional que envolve reiniciar uma sessão de TLS fechada sem realizar um aperto de mão TLS completo.

O NX Secure DTLS lida com pedidos de renegociação de anfitriões remotos. **Não** suporta o reinício da sessão. Uma discussão mais completa destas funcionalidades pode ser encontrada no Capítulo 3 do Guia do Utilizador NetX Secure TLS.

### <a name="protocol-layering"></a>Camada de protocolo

O protocolo TLS (e, portanto, também dTLS) encaixa na pilha de rede entre a camada de transporte (por exemplo, TCP ou UDP) e a camada de aplicação. O TLS é por vezes considerado um protocolo de camada de transporte (daí a Segurança *da Camada de Transporte),* mas porque atua como uma aplicação no que diz respeito aos protocolos de rede subjacentes, é por vezes agrupado na camada de aplicação.

O TLS requer um protocolo de camada de transporte que suporte a entrega em ordem e sem perdas, como o TCP. Devido a este requisito, o TLS não pode funcionar em cima da UDP, uma vez que a UDP não garante a entrega de datagramas. *DTLS* é uma versão modificada do TLS, é usada para aplicações que precisam da segurança de TLS sobre um protocolo de datagrama como uDP.

![Diagrama de uma camada de protocolo TLS.](media/image6.png)

**Figura 4- TCP/IP, UDP e TLS/DTLS**

## <a name="network-communications-security-and-encryption"></a>Segurança e Encriptação de Comunicações de Rede

A segurança das comunicações através das redes públicas e da Internet é um tema de extrema importância e tema de um vasto número de livros, artigos e soluções. O tema é incrivelmente complexo, mas pode ser reduzido a uma ideia simples: enviar informação por uma rede para que apenas o alvo pretendido possa aceder ou alterar essa informação. Isto divide-se em três conceitos importantes: sigilo, integridade e autenticação. O protocolo TLS/DTLS fornece soluções para os três.

A encriptação é usada de diferentes formas para fornecer sigilo, integridade e autenticação dentro dos protocolos TLS e DTLS. A encriptação deve ser fornecida ao TLS ou DTLS após a criação de uma sessão ou instância de servidor, uma vez que o TLS fornece uma estrutura flexível para o uso da encriptação e não a encriptação em si. O NetX Secure DTLS fornece as rotinas de encriptação necessárias para a maioria das aplicações, pelo que não tem de se preocupar em encontrar encriptação adequada.

Uma descrição mais detalhada destes tópicos pode ser encontrada no capítulo 3 do Guia do Utilizador NetX Secure TLS.

## <a name="tls-and-dtls-extensions"></a>Extensões TLS e DTLS

O TLS (e, portanto, o DTLS) fornece uma série de extensões que fornecem funcionalidades adicionais para determinadas aplicações. Estas extensões são normalmente enviadas como parte das mensagens ClientHello ou ServerHello, indicando a um anfitrião remoto o desejo de usar uma extensão ou fornecer detalhes adicionais para uso no estabelecimento da sessão TLS segura.

O NetX Secure DTLS suporta todas as extensões encontradas no NetX Secure TLS, e uma descrição completa delas pode ser encontrada no Guia de Utilizador NetX Secure TLS, Capítulo 3.

## <a name="authentication-methods"></a>Métodos de Autenticação

O TLS e o DTLS fornecem o quadro para estabelecer uma ligação segura entre dois dispositivos através de uma rede insegura, mas parte do problema é saber a identidade do dispositivo na outra extremidade dessa ligação. Sem um mecanismo para autenticar a identidade dos anfitriões remotos, torna-se uma operação trivial para um intruso fazer-se passar por um dispositivo de confiança.

Inicialmente, pode parecer que a utilização de endereços IP, endereços MAC de hardware ou DNS forneceria um nível de confiança relativamente elevado para identificar os anfitriões numa rede, mas dada a natureza da tecnologia TCP/IP e a facilidade com que os endereços podem ser falsificados e as entradas de DNS corrompidas (por exemplo, através do envenenamento por cache DNS), torna-se claro que o TLS precisa de uma camada adicional de proteção contra identidades fraudulentas.

Existem vários mecanismos que podem fornecer esta camada extra de autenticação para TLS, mas o mais comum é o *certificado digital.* Outros mecanismos incluem chaves pré-partilhadas (PSK) e esquemas de senha.

### <a name="digital-cerificates"></a>Cerifas digitais

Os certificados digitais são o método mais comum para autenticar um hospedeiro remoto em TLS. Essencialmente, um certificado digital é um documento com formatação específica que fornece informações de identidade para um dispositivo numa rede de computador.

O TLS normalmente usa um formato chamado X.509, uma norma desenvolvida pela União Internacional de Telecomunicações, embora outros formatos de certificados possam ser usados se os anfitriões TLS puderem concordar com o formato que está a ser utilizado. X.509 define um formato específico para certificados e várias codificações que podem ser usadas para produzir um documento digital. A maioria dos certificados X.509 utilizados com TLS são codificados usando uma variante de ASN.1, outra norma de telecomunicações. Dentro da ASN.1 existem várias codificações digitais, mas a codificação mais comum para certificados TLS é a norma de codificação distinguida (DER). O DER é um subconjunto simplificado das Regras Básicas de Codificação (BER) as ASN.1 que são concebidas para ser inequívocas, facilitando a análise. Por cima do fio, os certificados TLS são geralmente codificados em DER binário, e este é o formato que o NetX Secure espera para os certificados X.509.

Embora os certificados binários formatados pelo DER sejam utilizados no protocolo TLS real, podem ser gerados e armazenados em várias codificações diferentes, com extensões de ficheiros tais como .pem, .crt e .p12. As diferentes variantes são usadas por diferentes aplicações de diferentes fabricantes, mas geralmente todas podem ser convertidas em DER usando ferramentas amplamente disponíveis.

A mais comum das codificações de certificados alternativos é o PEM. O formato PEM (a partir do Privacy-Enhanced Mail) é uma versão codificada base-64 da codificação DER que é frequentemente utilizada porque a codificação resulta em texto imprimível que pode ser facilmente enviado usando protocolos de e-mail ou web.

Gerar um certificado para a sua aplicação NetX Secure está geralmente fora do âmbito deste manual, mas a ferramenta de linha de comando OpenSSL[(www.openssl.org)](http://www.openssl.org)está amplamente disponível e pode converter entre a maioria dos formatos.

Dependendo da sua aplicação, poderá gerar os seus próprios certificados, ser fornecido certificados por um fabricante ou organização governamental, ou adquirir certificados a uma autoridade de certificados comerciais.

Para utilizar um certificado digital na sua aplicação NetX Secure, tem primeiro de converter o seu certificado num formato binário DER e, opcionalmente, converter a chave privada associada (o "expoente privado" para rSA, por exemplo) num formato binário, tipicamente uma chave RSA codificada por PKCS#1- der-codificada. Uma vez concluída a conversão, cabe-lhe a si carregar o certificado e a chave privada no dispositivo. As opções possíveis incluem a utilização de um sistema de ficheiros baseado em flash ou a geração de um conjunto C a partir dos dados (utilizando uma ferramenta como "xxd" do Linux) e a compilação do certificado e chave na sua aplicação como dados constantes.

Uma vez que o seu certificado é carregado no dispositivo, a API DTLS pode ser usada para associar o seu certificado a uma sessão ou servidor DTLS.

Para mais detalhes e exemplos sobre como utilizar certificados X.509 com DTLS NetX Secure, consulte a secção "Importar certificados X.509 em NetX Secure" no Guia de Utilizador NetX Secure TLS.

Consulte os seguintes serviços DTLS na referência API para obter mais informações:

- nx_secure_x509_certificate_initialize,
- nx_secure_dtls_session_local_certificate_add,
- nx_secure_dtls_server_local_certificate_add,
- nx_secure_dtls_session_local_certificate_remove,
- nx_secure_dtls_server_local_certificate_remove,
- nx_secure_dtls_session_trusted_certificate_add,
- nx_secure_dtls_server_trusted_certificate_add,
- nx_secure_dtls_session_trusted_certificate_remove
- nx_secure_dtls_server_trusted_certificate_remove

### <a name="tls-client-certificate-specifics"></a>Especificidades do Certificado de Cliente TLS

As implementações do Cliente DTLS geralmente não requerem que um certificado local seja carregado no dispositivo. Um certificado local é um certificado que identifica o dispositivo local. Especificamente, um certificado local fornece informações de identidade para o dispositivo sobre o qual a aplicação TLS/DTLS é carregada. A exceção a isso é quando a Autenticação do Certificado de Cliente está ativada, mas isso é menos comum.

Um Cliente DTLS requer que pelo menos um certificado de confiança seja carregado (mais pode ser carregado se necessário) e espaço para a atribuição de um certificado remoto. Um certificado de confiança é um certificado que fornece uma base de confiança e autenticação do dispositivo remoto, quer diretamente quer através de uma Infraestrutura de Chave Pública (PKI). A raiz da cadeia de confiança é geralmente chamada de Autoridade de Certificação ou certificado de CA. Um certificado remoto refere-se ao certificado enviado pelo anfitrião remoto durante o aperto de mão TLS. Fornece identidade para o hospedeiro remoto e é autenticado comparando-o com um certificado de confiança no dispositivo local.

Para obter mais informações sobre a adição de certificados fidedignos e a atribuição de espaço para certificados remotos, consulte a referência TLS API para os seguintes serviços: nx_secure_dtls_session_create, nx_secure_dtls_session_trusted_certificate_add.

### <a name="tlsdtls-server-certificate-specifics"></a>Especificidades do certificado do servidor TLS/DTLS

As implementações do DTLS Server geralmente não requerem certificados "fidedignos" para serem carregados no dispositivo ou certificados remotos a serem atribuídos. A exceção a este ser quando a Autenticação do Certificado de Cliente está ativada.

Um Servidor TLS requer que seja carregado um certificado "local" (ou "identidade") para que o servidor possa fornecá-lo ao cliente remoto durante o aperto de mão TLS para autenticar o servidor ao cliente.

Para obter mais informações sobre o carregamento de certificados locais para utilização com aplicações de servidor NetX TLS, consulte a referência API para os seguintes serviços: nx_secure_dtls_server_local_certificate_add, nx_secure_dtls_server_local_certificate_remove.


### <a name="pre-shared-keys-psk"></a>Chaves pré-partilhadas (PSK)

Um mecanismo alternativo para fornecer autenticação de identificação em TLS é a noção de Chaves Pré-Partilhadas (PSK). A utilização de um cifrasuite PSK remove a necessidade de fazer as operações de encriptação intensivas de chaves públicas do processador, um bónus para dispositivos incorporados com recursos limitados. O PSK substitui o certificado no aperto de mão TLS/DTLS e é utilizado no lugar da chave de chave de sessão pré-master encriptada para a geração de chaves de sessão TLS/DTLS.

As cifrasuites PSK são limitadas no sentido de que um segredo partilhado deve estar presente em ambos os dispositivos antes de uma sessão TLS/DTLS ser estabelecida. Isto significa que os dispositivos devem ter sido carregados com esse segredo usando alguns meios seguros que não uma ligação PSK TLS - os PSKs podem ser atualizados através de uma ligação PSK TLS, mas o dispositivo deve necessariamente começar com uma PSK que é carregada através de algum outro mecanismo. Por exemplo, um dispositivo sensor e o seu dispositivo gateway poderiam ser carregados com PSKs na fábrica antes do envio, ou uma ligação TLS padrão (com um certificado) poderia ser usada para carregar o PSK.

Os cifrasuites PSK vêm em algumas formas, descritas no RFC 4279. A primeira utiliza teclas RSA ou Diffie-Hellman que são utilizadas da mesma forma que as chaves públicas transmitidas no certificado nos apertos de mão TLS padrão. O segundo formulário, que é mais utilizado num ambiente restrito a recursos, utiliza uma PSK que é usada para gerar diretamente as teclas de sessão (para utilização pela AES, por exemplo), evitando a utilização das operações de RSA ou Diffie-Hellman caras.

O NetX Secure suporta a segunda forma de cifrasuites PSK, permitindo que as aplicações removam todo o código de criptografia e utilização da memória de chaves públicas. O PSK em si não é uma chave AES, mas pode ser considerado como sendo mais uma palavra-passe a partir da qual as chaves reais são geradas. Existem poucas restrições sobre o valor psk, embora valores mais longos forneçam mais segurança (o mesmo que com as palavras-passe).

Para utilizar o PSK com a sua aplicação NetX Secure, tem primeiro de definir a macro global **NX_SECURE_ENABLE_PSK_CIPHERSUITES**. Isto é geralmente feito através das definições do seu compilador, mas a definição também pode ser colocada no ficheiro de cabeçalho nx_secure_tls.h. Com o suporte de cifrasumita psk definido, o suporte cifrasuite PSK será compilado na sua aplicação DTLS NetX Secure.

Com o suporte psk ativado, pode então utilizar a API DTLS para configurar PSKs para a sua aplicação. Cada PSK exigirá um valor PSK (a "chave" secreta real – mantenha este valor seguro), um valor de "identidade" usado para identificar o PSK específico, e uma "dica de identidade" que é usada por um servidor TLS para escolher um determinado valor PSK.

O próprio PSK pode ser qualquer valor binário, uma vez que nunca é enviado por uma ligação de rede. O PSK pode ter qualquer valor até 64 bytes de comprimento.

A identidade e a sugestão devem ser cordas de caracteres imprimíveis formatadas usando UTF-8. Os valores de identidade e sugestão podem ter até 128 bytes.

A identidade e o PSK formam um par único que é carregado em todos os dispositivos da rede que precisam de comunicar uns com os outros.

A "dica" é usada principalmente para definir perfis de aplicação específicos para grupo de PSKs por função ou serviço. Estes valores devem ser acordados antecipadamente e dependem da aplicação. Como exemplo, a aplicação do servidor da linha de comando OpenSSL (com o PSK ativado) utiliza a cadeia padrão "Client_identity", que deve ser fornecida por um cliente TLS para continuar com o aperto de mão TLS.

Para obter mais informações sobre psks, consulte a referência NetX Secure API para os seguintes serviços: nx_secure_dtls_psk_add, nx_secure_dtls_server_psk_add.

## <a name="importing-x509-certificates-into-netx-secure"></a>Importar certificados X.509 para o NetX Secure

São necessários certificados digitais para a maioria das ligações TLS na Internet. Os certificados fornecem um método para autenticar anfitriões anteriormente desconhecidos através da Internet através da utilização de intermediários de confiança, normalmente *chamados Autoridades de Certificados* ou CAs. Para ligar o seu dispositivo NetX Secure a um serviço de nuvem comercial (como a Amazon Web Services), terá de importar certificados para a sua aplicação carregando-os no seu dispositivo.

Juntamente com os certificados, você também vai precisar de uma *chave privada* que está associada ao seu certificado. Em algumas aplicações (como o Cliente TLS quando a Autenticação do Certificado de Cliente não estiver a ser utilizada) o certificado por si só será suficiente, mas se o seu certificado estiver a ser utilizado para identificar o seu dispositivo, necessitará de uma chave privada. As chaves privadas são normalmente geradas quando cria o seu certificado e são armazenadas num ficheiro separado, muitas vezes encriptado com uma palavra-passe.

Para obter uma descrição detalhada dos certificados de importação em aplicações NetX Secure, consulte o Capítulo 3 no Guia de Utilizador NetX Secure TLS.

## <a name="client-certificate-authentication-in-netx-secure-tls"></a>Autenticação de Certificado de Cliente em NetX Secure TLS

Ao utilizar a autenticação do certificado X.509, o protocolo TLS/DTLS exige que a instância do DTLS Server forneça um certificado de identificação, mas por padrão a instância do Cliente DTLS não necessita de fornecer um certificado de autenticação, utilizando outra forma de autenticação em vez disso (por exemplo, um nome de utilizador/combinação de palavra-passe). Isto corresponde ao uso mais comum de TLS na Internet para web sites. Por exemplo, um site de retalho online deve provar a um potencial cliente usando um navegador web que o servidor é legítimo, mas o utilizador usará um login/senha para aceder a uma conta específica.

No entanto, o caso padrão nem sempre é desejável, pelo que o TLS/DTLS permite opcionalmente que a instância do DTLS Server solicite um certificado ao Cliente remoto. Quando esta funcionalidade estiver ativada, o Servidor DTLS enviará uma mensagem CertificateRequest ao Cliente DTLS durante o aperto de mão. O Cliente deve responder com um certificado próprio e uma mensagem CertificateVerify que contenha um símbolo criptográfico que comprove que o Cliente é dono da chave privada correspondente associada a esse certificado. Se a verificação falhar ou o certificado não estiver ligado a um certificado de confiança no Servidor, o aperto de mão TLS falha.

Existem dois casos distintos de Autenticação de Certificado de Cliente em TLS – as seguintes secções cobrem ambos os casos.

### <a name="client-certificate-authentication-for-dtls-clients"></a>Autenticação de Certificado de Cliente para Clientes DTLS

Um Cliente DTLS pode tentar uma ligação a um servidor que solicite um certificado para autenticação do cliente. Neste caso, o Cliente deve fornecer um certificado ao servidor e verificar se é dono da chave privada correspondente ou o Servidor terminará o aperto de mão DTLS.

No DTLS NetX Secure, não existe uma configuração especial para suportar esta funcionalidade, mas a aplicação terá de fornecer um certificado de identificação local para a instância do Cliente TLS utilizando o serviço *nx_secure_tls_session_local_certificate_add.* Se nenhum certificado for fornecido pela aplicação, mas o servidor remoto estiver a utilizar a Autenticação do Certificado de Cliente e solicitar um certificado, o aperto de mão DTLS falhará. O certificado fornecido à Sessão DTLS com *nx_secure_dtls_session_local_certificate_add* deve ser reconhecido pelo servidor remoto para completar o aperto de mão DTLS.

### <a name="client-certificate-authentication-for-tls-servers"></a>Autenticação de Certificado de Cliente para Servidores TLS

O caso do Servidor DTLS para autenticação de certificado de cliente é ligeiramente mais complexo do que o caso do Cliente DTLS devido à funcionalidade ser opcional. Neste caso, o Servidor TLS precisa de solicitar especificamente um certificado ao cliente TLS remoto, em seguida, processar a mensagem CertificateVerify para verificar se o Cliente remoto possui a chave privada correspondente, e então o Servidor deve verificar se o certificado fornecido pelo Cliente pode ser rastreado a um certificado na loja de certificados de confiança local.

Nas instâncias do NetX Secure TLS Server, a autenticação do certificado de cliente é controlada pelos serviços *de nx_secure_dtls_server_x509_client_verify_configure* e *nx_secure_dtls_server_x509_client_verify_disable.*

Para ativar a autenticação do certificado do cliente, uma aplicação deve ligar *para nx_secure_dtls_server_x509_client_verify_configure* com a instância de sessão do DTLS Server antes de ligar *para nx_secure_dtls_server_start*. A verificação requer espaço para a atribuição de certificados de cliente que são fornecidos como parâmetro para *nx_secure_dtls_server_x509_client_verify_configure.* Note que o tampão deve ser suficientemente grande para manter a cadeia de certificados de tamanho máximo fornecida por um cliente *vezes o número de sessões de servidores DTLS*. Cada sessão de servidor requer espaço que será atribuído a partir do único tampão fornecido. Certifique-se de que o tampão é grande o suficiente ou ocorrerá um erro se a cadeia de certificados do Cliente fornecido for demasiado grande.

Quando a autenticação do Certificado de Cliente estiver ativada, o Servidor DTLS solicitará um certificado ao Cliente DTLS remoto durante o aperto de mão DTLS. No NetX Secure DTLS Server, o certificado Cliente é verificado contra a loja de certificados fidedignos criados com *nx_secure_dtls_server_trusted_certificate_add* seguindo a cadeia de emissores X.509. O Cliente remoto deve fornecer uma cadeia que ligue o seu certificado de identidade a um certificado na loja fidedigna ou o aperto de mão DTLS falhará. Além disso, se o processamento de mensagem CertificadoVerificar falhar, o aperto de mão DTLS também falhará.

Os métodos de assinatura utilizados para o método CertificadoVerify são fixados para a versão 1.0 e TLS da versão 1.0 e TLS 1.1, e são especificados pelo Servidor TLS na versão 1.2 do TLS, sobre o qual se baseia o DTLS NetX Secure. Para o DTLS 1.2, os métodos de assinatura suportados geralmente seguem os métodos relevantes fornecidos na tabela do método criptográfico, mas tipicamente RSA com SHA-256 (ver a secção "Criptografia em NetX Secure TLS" para obter mais informações sobre a inicialização de TLS com métodos criptográficos).

## <a name="cryptography-in-netx-secure-tls"></a>Criptografia em NetX Secure TLS

O TLS define um protocolo no qual a criptografia pode ser usada para garantir comunicações de rede. Como tal, deixa a criptografia real a ser usada bastante aberta para os utilizadores de TLS. A especificação requer apenas uma única cifrasuita a ser implementada – no caso do TLS 1.2, essa cifrasuite é TLS_RSA_WITH_AES_128_CBC_SHA, indicando a utilização de RSA para operações de chave pública, AES no modo CBC com teclas de 128 bits para encriptação de sessão, e SHA-1 para a autenticação de mensagens.

Sendo TLS 1.2 conforme, o NetX Secure permite a TLS_RSA_WITH_AES_128_CBC_SHA cifra por padrão, mas dado o número de possíveis implementações para cada um dos métodos criptográficos devido a capacidades de hardware e outras considerações, o NetX Secure fornece uma API criptográfica genérica que permite ao utilizador especificar quais os métodos criptográficos a utilizar com TLS.

> [!NOTE]
> O mecanismo genérico de API criptográfico também permite que os utilizadores implementem os seus próprios cifrasuites, mas isso é recomendado para utilizadores avançados que estejam familiarizados com os cifrasuites e extensões TLS. Por favor contacte o seu representante da Express Logic se estiver interessado em apoiar os seus próprios cifrasuites.

Consulte o Guia de Utilizador NetX Secure TLS, Capítulo 3, para uma discussão detalhada sobre como configurar métodos criptográficos para DTLS. O mesmo processo aplica-se tanto ao TLS como ao DTLS.
