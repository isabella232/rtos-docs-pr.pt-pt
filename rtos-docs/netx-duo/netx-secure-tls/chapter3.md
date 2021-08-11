---
title: Capítulo 3 - Descrição funcional do Azure RTOS NetX Secure
description: Este capítulo contém uma descrição funcional do NetX Secure TLS.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 711195e60771ebd467c69df49ef7665f32e13a17c21ca839404e829449cf1401
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797980"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-secure"></a>Capítulo 3 - Descrição funcional do Azure RTOS NetX Secure

## <a name="execution-overview"></a>Visão geral da execução

Este capítulo contém uma descrição funcional de Azure RTOS NetX Secure TLS. Existem dois tipos primários de execução de programas numa aplicação NetX Secure TLS: inicialização e chamadas de interface de aplicação. 

*NetX Secure assume a existência de ThreadX e NetX/NetXDuo. Da ThreadX, requer execução de fios, suspensão, temporizadores periódicos e instalações de exclusão mútua. A partir da NetX/NetXDuo requer as instalações de rede TCP/IP e os controladores.*

## <a name="transport-layer-security-tls-and-secure-sockets-layer-ssl"></a>Segurança da camada de transporte (TLS) e camada de tomadas seguras (SSL)

O componente de protocolo de rede seguro do NetX secure é uma implementação do protocolo de Segurança da Camada de Transporte (TLS), tal como descrito nos RFCs 2246 (versão 1.0), 4346 (versão 1.1), 5246 (versão 1.2) e 8446 (versão 1.3). Também estão incluídas as rotinas de suporte para X.509 básico (RFC 5280).

NetX Secure TLS suporta as versões TLS 1.2 e 1.3. As implementações estão previstas para os TLS 1.0 e TLS 1.1 agora prectados, mas devem ser explicitamente inicializadas e não são recomendadas para utilização em novos produtos.

*Secure Sockets Layer* (SSL) foi o nome original de TLS antes de se tornar um padrão em RFC 2246 e "SSL" é frequentemente usado como um nome genérico para os protocolos TLS. A última versão do SSL foi 3.0, e tLS 1.0 é por vezes referida como versão SSL 3.1. Todas as versões do protocolo oficial "SSL" são consideradas obsoletas e inseguras e atualmente o NetX Secure não fornece uma implementação SSL.

O TLS especifica um protocolo para gerar *teclas* de sessão que são criadas durante o *aperto de mão* TLS entre um cliente TLS e servidor e essas teclas são usadas para encriptar dados enviados pela aplicação durante a sessão TLS. 

Os dados TLS são divididos em *registos* equivalentes em conceito a um pacote TCP. Cada registo TLS tem um cabeçalho, e os registos encriptados TLS também têm um rodapé (hash de sistema de verificação). Os registos de aperto de mão TLS têm um cabeçalho adicional encapsulado dentro do registo TLS maior. O registo TLS é encapsulado pelo protocolo de rede de camadas de transporte da mesma forma que um pacote TCP é encapsulado por um pacote IP.

### <a name="tls-13"></a>TLS 1.3

Em agosto de 2018, a especificação TLS 1.3 foi finalizada. A nova versão do protocolo é uma atualização bastante significativa que altera alguns aspetos fundamentais da segurança e desempenho subjacentes do TLS. No entanto, estas alterações são em grande parte invisíveis para o utilizador típico do TLS, uma vez que se aplicam principalmente à máquina de aperto de mão TLS e à geração chave de sessão. Foram também adicionadas algumas funcionalidades e extensões opcionais. Segue-se um resumo das alterações e como impactam a funcionalidade TLS.

- A máquina de aperto de mão foi otimizada removendo uma troca completa de mensagens pelo servidor.
- A geração chave foi atualizada para usar uma rotina padronizada chamada HKDF (Função de Derivação de Chaves baseada em HMAC) e liga as teclas de sessão a todas as mensagens de aperto de mão (em vez de alguns parâmetros selecionados).
- Todos os TLS 1.2 e cifrasuites anteriores são precários e são incompatíveis com TLS 1.3. Da mesma forma, todas as cifrasuites TLS 1.3 são inutilizáveis com versões anteriores.
- Todos os TLS 1.3 cifrasuites fornecem sigilo perfeito para a frente (PFS) usando chaves efémeras<sup>6</sup> 
- TLS 1.3 remove o "código de autenticação de mensagem" (MAC) em cada registo a favor da utilização de 7 cifras AEAD<sup>7</sup>
- Foram adicionadas algumas funcionalidades opcionais adicionais, incluindo 0-RTT (Zero Round Trip Time) que permite que os dados da aplicação sejam enviados durante o aperto de mão. 0-RTT é puramente opcional e não é atualmente suportado em Azure RTOS TLS.

O TLS 1.3 não afeta significativamente as aplicações dos utilizadores. A API permanece exatamente a mesma entre versões, e os cifrasuites são marcados para que uma única tabela cifrassuite possa ser usada.

Para utilizar o TLS 1.3, o NX_SECURE_TLS_ENABLE_TLS_1_3 macro deve ser definido globalmente. TLS 1.3 é desativado por padrão em Azure RTOS TLS.

6. As teclas "efémeras" são pares de chaves assimétricos que são gerados durante o aperto de mão TLS e usados para a troca de segredos apenas por essa sessão. O par-chave é descartado após a utilização – isto impede que um intruso possa aceder a dados encriptados numa sessão de TLS gravada, mesmo que uma chave privada de certificado seja comprometida a qualquer momento no futuro – daí o "Perfeito Segredo para a Frente".

7. Encriptação Autenticada com Dados Associados – um modo para cifras como a AES que combina encriptação e verificação de integridade numa única operação, eliminando a necessidade de um haxixe separado dos dados para verificação de integridade.

### <a name="tls-record-header"></a>Cabeçalho de registo TLS

Qualquer registo TLS válido deve ter um cabeçalho TLS, como mostrado no Erro! Fonte de referência não encontrada.

![Diagrama de um cabeçalho de registo TLS.](media/image2.png)

Figura 1 - Cabeçalho de registo TLS

Os campos do cabeçalho de registo TLS são definidos da seguinte forma:

| Campo de cabeçalho TLS | Objetivo     |
| ---------------- | ------------- |
| **Tipo de mensagem de 8 bits** | Este campo contém o tipo de registo TLS enviado. Os tipos válidos são os seguintes:<br />- ChangeCipherSpec<sup>8</sup>: 0x14<br />- Alerta: 0x15<br />- Aperto de mão: 0x16<br />- Dados da aplicação: 0x17 |
| **Versão do protocolo de 16 bits** | Este campo contém a versão do protocolo TLS. Os valores válidos são os seguintes:<br />- SSL 3.0: 0x0300<br />- TLS 1.0: 0x0301<br />- TLS 1.1: 0x0302<br />- TLS 1.2: 0x0303<br />- **TLS 1.3 <sup>9</sup>**: **0x0303** |
| **Comprimento de 16 bits** | Este campo contém o comprimento dos dados encapsulados no registo TLS. |

8. No TLS 1.3 a mensagem ChangeCipherSpec já não é utilizada, embora ainda possa ser enviada por razões de compatibilidade, caso em que a mensagem é ignorada.

9. O TLS 1.3 teria tecnicamente um valor de 0x0304 se este regime fosse continuado, mas o protocolo foi alterado para ter a versão do protocolo real numa extensão, pelo que todos os registos TLS 1.3 utilizam 0x0303 nos campos da versão protocolar para retrocompatibilidade.

### <a name="tls-handshake-record-header"></a>Cabeçalho de recorde de aperto de mão TLS

Qualquer registo de aperto de mão válido do TLS deve ter um cabeçalho de aperto de mão TLS, como mostra a Figura 2.

![Diagrama de um cabeçalho de recorde de aperto de mão TLS.](media/image3.png)

Figura 2 - Cabeçalho recorde de aperto de mão TLS

Os campos do cabeçalho de registo do aperto de mão TLS são definidos da seguinte forma:

| Campo de cabeçalho TLS | Objetivo |
| ---------------- |----------------------- |
| **Tipo de mensagem de 8 bits** | Este campo contém o tipo de registo TLS enviado. Os tipos válidos são os seguintes:<br />- ChangeCipherSpec<sup>10</sup>: 0x14<br />- Alerta: 0x15<br />- Aperto de mão: 0x16<br />- Dados da aplicação: 0x17 |
| **Versão do protocolo de 16 bits** | Este campo contém a versão do protocolo TLS. Os valores válidos são os seguintes:<br />- SSL 3.0: 0x0300<br />- TLS 1.0: 0x0301<br />- TLS 1.1: 0x0302<br />- TLS 1.2: 0x0303<br />- **TLS 1.3 <sup>11</sup>**: **0x0303** |
| **Comprimento de 16 bits**    | Este campo contém o comprimento dos dados encapsulados no registo TLS. |
| **Tipo de aperto de mão de 8 bits** | Este campo contém o tipo de mensagem de aperto de mão. Os valores válidos são os seguintes (*as mensagens em **negrito** foram adicionadas em TLS 1.3):<br />- HelloRequest: 0x00<br />- ClientHello: 0x01<br />- ServerHello: 0x02<br />- **HelloVerifyRequest**: **0x03**<br />- **NewSessionTicket**: **0x04**<br />- **EndOfEarlyData**: **0x05**<br />- **CriptografadasTensions**: **0x08**<br />- Certificado: 0x0B<br />- ServerKeyExchange: 0x0C<br />- CertificadoRequest: 0x0D<br />- ServerHelloDone: 0x0E<br />- CertificaçãoVerifical: 0x0F<br />- ClientKeyExchange: 0x10<br />- Acabado: 0x14<br />- **KeyUpdate**: **0x18**<br />- **MessageHash**: **0xFE** |
| **Comprimento de 24 bits**    | Este campo contém o comprimento dos dados da mensagem de aperto de mão. |

10. No TLS 1.3 a mensagem ChangeCipherSpec já não é utilizada, embora ainda possa ser enviada por razões de compatibilidade, caso em que a mensagem é ignorada.

11. O TLS 1.3 teria tecnicamente um valor de 0x0304 se este regime fosse continuado, mas o protocolo foi alterado para ter a versão do protocolo real numa extensão, pelo que todos os registos TLS 1.3 utilizam 0x0303 nos campos da versão protocolar para retrocompatibilidade.

### <a name="the-tls-handshake-and-tls-session"></a>O aperto de mão tls e sessão TLS

Um aperto de mão TLS típico (versões 1.0-1.2) é mostrado na Figura 3. Um aperto de mão TLS começa quando o Cliente TLS envia uma mensagem *ClientHello* para um servidor TLS, indicando o seu desejo de iniciar uma sessão de TLS. A mensagem contém informações sobre a encriptação que o cliente gostaria de usar para a sessão, juntamente com as informações usadas para gerar as teclas de sessão mais tarde no aperto de mão. Até que as teclas de sessão sejam geradas, todas as mensagens no aperto de mão TLS não são encriptadas. O TLS 1.3 altera um pouco o aperto de mão – os detalhes são apresentados na secção seguinte.

O Servidor TLS responde ao ClientHello com uma mensagem ServerHello, indicando uma seleção das opções de encriptação fornecidas pelo cliente. O ServerHello é seguido por uma mensagem de Certificado, na qual o servidor fornece um certificado digital para autenticar a sua identidade ao cliente. Finalmente, o servidor envia uma mensagem ServerHelloDone para indicar que não tem mais mensagens para enviar. O servidor pode enviar opcionalmente outras mensagens seguindo o ServerHello e em alguns casos pode não enviar uma mensagem de Certificado, daí a necessidade da mensagem ServerHelloDone.

Uma vez que o cliente tenha recebido todas as mensagens do servidor, tem informações suficientes para gerar as teclas de sessão. O TLS faz isso criando uma parte partilhada de dados aleatórios *chamados Pre-Master Secret*, que é um tamanho fixo e é usado como uma semente para gerar todas as teclas necessárias uma vez que a encriptação é ativada. O Segredo Pré-Mestre é encriptado utilizando o algoritmo de chave pública (por exemplo, RSA) especificado nas mensagens Hello (ver abaixo para obter informações sobre algoritmos de chaves públicas) e a chave pública fornecida pelo servidor no seu certificado. Uma funcionalidade opcional de TLS chamada Chaves Pré-Partilhadas (PSK) permite cifrasuites que não usam um certificado, mas em vez disso usam um valor secreto partilhado entre os anfitriões (geralmente através de transferência física ou outro método seguro). O segredo partilhado é usado para gerar o Segredo Pré-Mestre em vez de usar uma mensagem encriptada para enviar o Segredo Pré-Mestre. Veja a secção em Chaves Pré-Partilhadas abaixo.

O Pre-Master Secret encriptado é enviado para o servidor na mensagem ClientKeyExchange. O servidor, ao receber a mensagem ClientKeyExchange, desencripta o Segredo Pré-Mestre usando a sua chave privada e procede à geração das teclas de sessão em paralelo com o cliente TLS.

Uma vez geradas as teclas de sessão, todas as mensagens adicionais podem ser encriptadas utilizando o algoritmo de tecla privada (por exemplo, AES) selecionado nas mensagens Hello. Uma última mensagem não encriptada chamada ChangeCipherSpec é enviada pelo cliente e pelo servidor para indicar que todas as mensagens adicionais serão encriptadas.

A primeira mensagem encriptada enviada pelo cliente e pelo servidor é também a mensagem final de aperto de mão TLS, chamada Finished. Esta mensagem contém um haxixe de todas as mensagens de aperto de mão recebidas e enviadas. Este haxixe é utilizado para verificar se nenhuma das mensagens no aperto de mão foi adulterada ou corrompida (indicando uma possível violação da segurança).

Uma vez recebidas as mensagens Acabadas e verificadas as hashes de aperto de mão, a sessão TLS começa e a aplicação começa a enviar e receber dados. Todos os dados enviados por ambos os lados durante a sessão TLS são primeiro hashed usando o algoritmo de haxixe escolhido nas mensagens Hello (para fornecer integridade da mensagem) e encriptado usando o algoritmo de chave privada escolhido com as teclas de sessão geradas.

Finalmente, uma sessão TLS só pode ser terminada com sucesso se o Cliente ou o Servidor optarem por fazê-lo. Uma sessão truncada é considerada uma falha de segurança (uma vez que um intruso pode estar a tentar evitar que todos os dados sejam enviados) pelo que é enviada uma notificação especial quando ambos os lados querem terminar a sessão, chamado alerta CloseNotify. Tanto o cliente como o servidor devem enviar e processar um alerta CloseNotify para uma paragem de sessão bem sucedida.

![Diagrama de um aperto de mão típico do TLS.](media/image4.png)

Figura 3- Aperto de mão típico do TLS

### <a name="tls-13-handshake"></a>TLS 1.3 Aperto de Mão

O TLS 1.3 é uma revisão bastante importante do protocolo TLS. A grande maioria das alterações foram feitas ao aperto de mão para aumentar a segurança e o desempenho. Um aperto de mão típico TLS 1.3 é mostrado na Figura 4. A diferença primária pode ser observada no número de trocas entre o servidor e o cliente.

No TLS 1.2 e mais cedo, o servidor enviaria dois voos<sup>12</sup> de mensagens – primeiro o ServerHello e depois uma mensagem ChangeCipherSpec antes de enviar a mensagem terminada encriptada que termina o aperto de mão. No TLS 1.3, o servidor envia tudo no primeiro voo – ServerHello, extensões, certificado e Terminado. A mensagem ChangeCipherSpec foi eliminada e o servidor gera as suas teclas de sessão e começa a encriptar mensagens de aperto de mão imediatamente após o ServerHello.

O novo acordo significa que mais do aperto de mão TLS está protegido por encriptação, limitando a quantidade de dados de texto simples a que um intruso pode aceder. Além disso, a remoção do segundo voo do servidor (que era apenas um ChangeCipherSpec seguido de um Terminado) significa que um cliente TLS já não precisa de esperar para começar a transmitir dados da aplicação – assim que o cliente envia a sua própria mensagem Terminada, a sessão é iniciada.

12. Um voo é simplesmente uma coleção de mensagens TLS enviadas simultaneamente em grupo.

![Diagrama de um Aperto de Mão TLS 1.3.](media/image5.png)

Figura 4 - TLS 1.3 Aperto de mão

> [!NOTE]
> *O TLS 1.3 também introduziu a noção de "Dados Antecipados" e 0-RTT (Tempo de Viagem Redonda Zero), o que significa que alguns dados da aplicação podem ser enviados no primeiro voo de mensagens. Esta funcionalidade opcional foi adicionada principalmente como uma otimização para a capacidade de resposta do navegador web (por exemplo, para enviar cabeçalhos HTTP precoces para começar a renderizar uma página). A partir de Azure RTOS 6.0 esta funcionalidade NÃO é suportada.*

### <a name="initialization"></a>Inicialização

A pilha NetX ou NetXDuo TCP/IP deve ser inicializada antes da utilização do NetX Secure TLS. Consulte o Guia de Utilizador NetX ou NetXDuo para obter informações sobre como inicializar corretamente a pilha TCP/IP.

Uma vez iniciada a stack NetX TCP/IP, o TLS pode ser ativado. Internamente, todo o tráfego e processamento da rede TLS é tratado pela pilha NetX/NetXDuo sem necessidade de intervenção do utilizador. No entanto, o TLS tem alguns requisitos específicos que devem ser tratados separadamente da pilha de rede subjacente. Estes parâmetros são atribuídos ao bloco de controlo TLS chamado ***NX_SECURE_TLS_SESSION** _ utilizando o serviço _ *_nx_secure_tls_session_create_** .

O TLS tem dois modos, Server e Cliente, qualquer um dos quais pode ser ativado numa aplicação (mas apenas um modo por tomada NetX), e cada um tem os seus próprios requisitos específicos, detalhados abaixo.

Em ambos os modos, o NetX Secure TLS requer a criação e configuração de uma tomada TCP (***NX_TCP_SOCKET** _) para comunicações TCP com o anfitrião remoto. A tomada TCP é atribuída a uma instância de sessão TLS com o serviço _ *_nx_secure_tls_session_start*_* detalhado abaixo.

### <a name="initialization--tls-server"></a>Inicialização - Servidor TLS

Além de uma tomada TCP, o modo NetX Secure TLS Server requer um *Certificado Digital*, que é um documento utilizado para identificar o servidor TLS ao cliente TLS de ligação, e os certificados correspondentes *Private Key*, normalmente para o algoritmo de encriptação RSA. A norma International Telecommunications Union X.509 especifica o formato de certificado utilizado pela TLS e existem inúmeros utilitários para a criação de certificados digitais X.509.

Para o NetX Secure TLS, o certificado X.509 deve ser codificado bináriamente utilizando o formato Distinguished Encoding Rules (DER) de ASN.1. DER é o formato binário padrão TLS over-the-wire para certificados.

A chave privada associada ao certificado fornecido deve estar em DER-Encoded formato PKCS#1. A chave privada é utilizada apenas no dispositivo e nunca será transmitida através do fio. Mantenha as chaves privadas seguras, pois fornecem a segurança das comunicações TLS!

Para inicializar o certificado do Servidor TLS, a aplicação deve fornecer um ponteiro a um tampão contendo o certificado X.509 codificado pelo DER e dados chave privados opcionais de PKCS#1 RSA utilizando o serviço ***nx_secure_x509_certificate_intialize** _ que povoa a estrutura _ *NX_SECURE_X509_CERT** com os dados de certificado adequados para utilização por TLS.

Uma vez inicializado o certificado do servidor, este deve ser adicionado ao bloco de controlo TLS utilizando o serviço ***nx_secure_tls_local_certificate_add.***

Uma vez adicionado o certificado do servidor ao bloco de controlo TLS, a tomada pode ser utilizada para estabelecer uma ligação segura do Servidor TLS.

### <a name="initialization--tls-client"></a>Inicialização - Cliente TLS

O modo cliente NetX Secure TLS requer uma Loja de *Certificados Fidedignas,* que é uma coleção de certificados digitais codificados X.509 das Autoridades de Certificados Fidedignas (CA's). Estes certificados são assumidos pelo protocolo TLS como "confiáveis" e servem de base para autenticar certificados fornecidos por entidades de servidores TLS ao Cliente NetX Secure TLS.

Um certificado de CA fidedigno pode ser *auto-assinado* ou assinado por outra AC, caso em que esse certificado é chamado de *Ac Intermediário* (ICA). Numa aplicação típica de TLS, o servidor fornece os certificados ICA juntamente com o seu certificado de servidor, mas o único requisito para a autenticação bem sucedida é que uma cadeia de emitentes (certificados usados para assinar outros certificados) pode ser rastreada do certificado do servidor de volta para um certificado de CA fidedigno na Loja de Certificados Fidedignos. Esta cadeia é conhecida como uma *cadeia de fiéis* ou cadeia de *certificados.*

Para inicializar um certificado ca ou ica fidedigno, o pedido deve fornecer um ponteiro a um tampão contendo o certificado X.509 codificado pelo DER utilizando o serviço ***nx_secure_x509_certificate_intialize** _ que povoa a estrutura _ *NX_SECURE_X509_CERT** com os dados de certificado adequados para utilização pela TLS.

Os certificados fidedignos que foram inicializados são adicionados ao bloco de controlo TLS utilizando o serviço ***nx_secure_tls_trusted_certificate_add.*** A não adição de um certificado fará com que a sessão do Cliente TLS falhe, uma vez que não haverá forma de o protocolo TLS autenticar os anfitriões remotos do servidor TLS.

O Cliente TLS também precisa de espaço para que o certificado do servidor de entrada seja atribuído (assumindo que não está a ser utilizado um modo chave pré-partilhado). A partir do NetX Secure TLS 5.12, já não é necessário que a aplicação aloque espaço para certificado remoto. No entanto, a opção de atribuição de espaço para um certificado de servidor ainda se encontra disponível e os certificados atribuídos pelo utilizador serão utilizados antes da otimização do tampão de certificado interno <sup>13</sup> – consulte o serviço ***de nx_secure_tls_remote_certificate_allocate*** para obter mais informações.

Uma vez criada a Loja de Certificados Fidedignos e alocado espaço para o certificado do servidor, a tomada poderá ser utilizada para estabelecer uma ligação segura ao Cliente TLS.

13. A otimização utiliza o "tampão de pacote" fornecido pela aplicação do utilizador para a sessão de tls utilizando *nx_secure_tls_session_packet_buffer_set* para alocar as estruturas de análise X.509 em vez de utilizar as estruturas fornecidas pelo utilizador utilizadas em versões anteriores do NetX Secure TLS. Existe uma possibilidade improvável de encontrar uma cadeia de certificados que exceda o tamanho do tampão do pacote, caso em que o tamanho do tampão do pacote pode ser aumentado ou *nx_secure_tls _remote_certificate_allocate* pode ser utilizado para alocar mais espaço para a cadeia de certificados.

### <a name="application-interface-calls"></a>Chamadas de Interface de Aplicação

As aplicações NetX Secure TLS normalmente fazem chamadas de função a partir de linhas de aplicação que funcionam sob o ThreadX RTOS. Alguma inicialização, nomeadamente para os protocolos de comunicações de rede subjacentes (por exemplo, TCP e IP) pode ser chamada a partir de ***tx_application_define*.** Consulte o Guia do Utilizador NetX/NetXDuo para obter mais informações sobre a inicialização das comunicações de rede.

O TLS utiliza fortemente as rotinas de encriptação que são operações intensivas de processador. Geralmente, estas operações serão realizadas no contexto da linha de chamada.

### <a name="tls-session-start"></a>Início da sessão TLS

O TLS requer um protocolo de rede de camadas de transporte subjacente para funcionar. O protocolo normalmente utilizado é TCP. Para estabelecer uma sessão NetX Secure TLS, deve ser estabelecida uma ligação TCP utilizando a API NetX/NetXDuo TCP. Deve ser criada uma **NX_TCP_SOCKET** e uma ligação estabelecida utilizando os **serviços _nx_tcp_server_socket_listen_ _ *e _*_nx_tcp_server_socket_accept_*_ (para o Servidor TLS) ou o* serviço de _nx_tcp_client_socket_connect_ _(para** o Cliente TLS).

Uma vez estabelecida uma ligação TCP, a tomada TCP é então passada para o ***serviço nx_secure_tls_session_start.***

### <a name="tls-packet-allocation"></a>Alocação de pacotes TLS

O NetX Secure TLS utiliza a mesma estrutura de pacotes que o NetX/NetXDuo TCP (***NX_PACKET** _) exceto que, em vez de ligar para o serviço _*_nx_packet_allocate,_*_ o serviço _ *_nx_secure_tls_packet_allocate_** deve ser chamado para que o espaço para o cabeçalho TLS possa ser devidamente atribuído.

### <a name="tls-session-send"></a>TLS Sessão Enviar

Uma vez iniciada a sessão TLS, a aplicação poderá enviar dados utilizando o serviço ***nx_secure_tls_session_send** _ . O serviço de envio é idêntico em uso ao serviço _*_nx_tcp_socket_send,_*_ tomando uma estrutura de dados _*_NX_PACKET_*_ contendo os dados enviados, apenas que os dados serão encriptados pela pilha NX Secure TLS antes de serem enviados, e o pacote deve ser atribuído usando _*_nx_secure_tls_packet_allocate_**.

### <a name="tls-session-receive"></a>Sessão TLS receber

Uma vez iniciada a sessão TLS, a aplicação pode começar a receber dados utilizando o serviço ***nx_secure_tls_session_receive** _ . Tal como o envio da Sessão TLS, este serviço é idêntico em uso para _*_nx_tcp_socket_receive_**, exceto que os dados de entrada são desencriptados e verificados pela pilha TLS antes de serem devolvidos na estrutura do pacote.

### <a name="tls-session-close"></a>Sessão TLS fechar

Uma vez concluída uma sessão TLS, tanto o cliente TLS como o servidor devem enviar um alerta CloseNotify para o outro lado para encerrar a sessão. Ambas as partes devem receber e processar o alerta para garantir uma paragem de sessão bem sucedida.

Se o anfitrião remoto enviar um alerta CloseNotify, qualquer chamada para o serviço ***nx_secure_tls_session_receive** _ processará o alerta, enviará o alerta correspondente de volta para o hospedeiro remoto e devolverá um valor de _*_NX_SECURE_TLS_SESSION_CLOSED_**. Uma vez encerrada a sessão, quaisquer outras tentativas de enviar ou receber dados com essa sessão TLS falharão.

Se a aplicação pretender encerrar a sessão TLS, o serviço ***nx_secure_tls_session_end** _ deve ser chamado. O serviço enviará o alerta CloseNotify e processará a resposta CloseNotify. Se a resposta não for recebida, será devolvido um erro de _ *_NX_SECURE_TLS_SESSION_CLOSE_FAIL_** indicando que a sessão TLS não foi completamente encerrada, uma possível falha de segurança.

### <a name="tls-alerts"></a>Alertas TLS

TLS é projetado para fornecer a máxima segurança, por isso qualquer comportamento errante no protocolo é considerado uma potencial falha de segurança. Por esta razão, quaisquer erros no processamento de mensagens ou encriptação/desencriptação são considerados erros fatais que terminam o aperto de mão ou a sessão imediatamente.

Embora os erros de manuseamento de uma aplicação local sejam relativamente simples, o anfitrião remoto precisa de saber que ocorreu um erro para lidar adequadamente com a situação e evitar eventuais possíveis falhas de segurança. Por esta razão, o TLS enviará uma mensagem *de alerta* ao anfitrião remoto em qualquer erro.

Os alertas são tratados da mesma forma que qualquer outra mensagem TLS e são encriptados durante a sessão para impedir que um intruso recolha informações do tipo de alerta fornecido. Durante o aperto de mão, os alertas enviados são limitados no âmbito para limitar a quantidade de informação que poderia ser obtida por um potencial atacante.

O alerta CloseNotify, usado para encerrar a sessão TLS, é o único alerta não fatal. Embora seja considerado um alerta e enviado como uma mensagem de alerta, um CloseNotify é diferente de outros alertas na medida em que não indica que tenha ocorrido um erro.

O valor de alerta e "nível" (os níveis são "alerta" e "fatais" – a maioria dos alertas TLS são "fatais") são definidos nos RFCs TLS e indicam o tipo de erro que ocorreu. A maioria dos alertas TLS para além do CloseNotify pode ser considerado uma indicação de um potencial problema de segurança e resultará na abortar a sessão TLS ou o aperto de mão. Se qualquer chamada da API TLS **voltar NX_SECURE_TLS_ALERT_RECEIVED** (0x114), o serviço API **_nx_secure_tls_session_alert_value_get_** (novo na versão 5.12 da NetX Secure TLS) pode ser utilizado para recuperar o valor e o nível de alerta TLS para que a aplicação utilize para quaisquer decisões relativas a respostas a questões de segurança. Na maioria dos casos, qualquer alerta recebido do hospedeiro remoto que não o CloseNotify deve ser considerado um erro fatal, embora existam algumas excptions – consulte os RFCs TLS para obter mais informações.

### <a name="tls-session-renegotiation"></a>TLS Sessão renegociação

O TLS apoia a noção de "renegociação" que é simplesmente uma renegociação dos parâmetros da sessão TLS no contexto de uma sessão TLS existente. Na prática, isto significa que as novas mensagens de aperto de mão são encriptadas e autenticadas utilizando a sessão existente. A renegociação é utilizada quando um anfitrião TLS quer gerar novos parâmetros de sessão (por exemplo, gerar novas teclas de sessão TLS) sem ter de completar a sessão existente. Por exemplo, a renegociação pode ser desejável quando as políticas de segurança para uma aplicação ditam que as chaves de sessão são usadas apenas por um tempo limitado, mas uma sessão TLS permanece ativa para além desse tempo.

Um problema com a renegociação da sessão é que torna o TLS vulnerável a um ataque específico do Man-in-the-Middle onde um intruso pode convencer um servidor a iniciar uma renegociação com novos parâmetros, permitindo assim ao intruso sequestrar a sessão de TLS. Para atenuar este problema, foi introduzida a extensão de Indicação de Renegociação Segura (ver erro de **secção! Fonte de referência não encontrada.** secção).

NetX Secure TLS suporta completamente a renegociação da sessão e a extensão de indicação de renegociação segura.

Ao receber dados de um hospedeiro remoto, as renegotações (e a extensão) são tratadas automaticamente sem interação da aplicação. Se for desejada notificação sobre renegociações de sessão, poderá ser fornecida uma chamada de renegociação com o serviço *nx_secure_tls_session_renegotiate_callback_set.* O retorno será invocado sempre que uma renegociação for solicitada pelo anfitrião remoto, permitindo que o pedido tome medidas se desejar.

Para iniciar uma renegociação a partir de uma sessão de TLS ativa, basta invocar o serviço *de nx_secure_tls_session_renegotiate* na sessão TLS desejada.

### <a name="tls-session-resumption"></a>Retoma da Sessão TLS

O reinício da sessão TLS não deve ser confundido com a renegociação da sessão, apesar de algumas semelhanças. Onde a *renegociação* da sessão envolve iniciar um novo aperto de mão dentro de uma sessão TLS existente, *o recomeço da* sessão é uma característica puramente opcional que envolve reiniciar uma sessão de TLS fechada sem realizar um aperto de mão TLS completo. Para tal, uma implementação TLS pode cache os parâmetros e teclas da sessão, associando-os a um *ID de sessão,* um identificador único fornecido no aperto de mão original. Ao fornecer um ID de sessão a um servidor TLS, um cliente indica que uma sessão anterior de TLS entre os anfitriões existiu e completou algum tempo no passado, e que o cliente ainda possui o estado para restabelecer a sessão com um aperto de mão reduzido. Uma vez que as teclas de sessão são teoricamente ainda secretas e só são conhecidas pelos dois anfitriões comunicantes, o servidor pode iniciar uma nova sessão de TLS e contornar a maioria do aperto de mão normal.

O reinício da sessão pode ser útil para evitar as operações potencialmente dispendiosas de chaves públicas usadas para partilhar o segredo principal de geração chave e verificar assinaturas de certificados, mas também requer que os parâmetros da sessão, chaves e estado cripotgráfico sejam mantidos na memória para todas as sessões possíveis (pelo menos para uma janela de tempo configurável).

A versão atual do NetX Secure TLS não suporta o reinício da sessão – o ID da sessão é simplesmente ignorado pelos servidores TLS e os clientes TLS fornecem sempre um ID de sessão NU, o que leva o servidor a realizar um aperto de mão completo. A falta de retoma da sessão não deverá causar problemas de interoperabilidade, uma vez que é uma característica completamente opcional e todas as implementações de TLS devem estar por defeito num aperto de mão completo se o ID da sessão for NULO ou não reconhecido.

### <a name="protocol-layering"></a>Camada de protocolo

O protocolo TLS enquadra-se na pilha de rede entre a camada de transporte (por exemplo, TCP) e a camada de aplicação. O TLS é por vezes considerado um protocolo de camada de transporte (daí a Segurança *da Camada de Transporte),* mas porque atua como uma aplicação no que diz respeito aos protocolos de rede subjacentes (como o TCP) é por vezes agrupado na camada de aplicação.

O TLS requer um protocolo de camada de transporte que suporte a entrega em ordem e sem perdas, como o TCP. Devido a este requisito, o TLS não pode funcionar em cima da UDP, uma vez que a UDP não garante a entrega de datagramas. Um protocolo separado chamado *DTLS,* que é uma versão modificada do TLS, é usado para aplicações que precisam da segurança de TLS sobre um protocolo de datagrama como uDP. NetX Secure suporta DTLS, mas a documentação para DTLS é separada deste documento.

![Diagrama de camadas de protocolo TCP/IP e TLS.](media/image6.png)

Figura 5- TCP/IP e camadas de protocolo TLS

## <a name="network-communications-security"></a>Segurança de Comunicações de Rede

A segurança das comunicações através das redes públicas e da Internet é um tema de extrema importância e tema de um vasto número de livros, artigos e soluções. O tema é incrivelmente complexo, mas pode ser reduzido a uma ideia simples: enviar informação por uma rede para que apenas o alvo pretendido possa aceder ou alterar essa informação. Isto divide-se em três conceitos importantes: sigilo, integridade e autenticação. O protocolo TLS fornece soluções para os três.

### <a name="secrecy"></a>Sigilo

Ao enviar dados através de uma rede, é muitas vezes importante que os dados não possam ser obtidos por uma entidade maliciosa. Se os dados forem enviados através de uma ligação TCP/IP, qualquer pessoa com acesso à rede poderá ler esses dados utilizando ferramentas de rede facilmente disponíveis. Para evitar que esses dados sejam obtidos, deve ser codificado de modo a que não possa ser lido a não ser pelo alvo pretendido – isto é *sigilo.* No TLS, algoritmos de encriptação como RSA e AES fornecem sigilo.

### <a name="integrity"></a>Integridade

Por vezes, o sigilo não é suficiente para proteger os dados que viajam sobre uma rede. Em alguns casos, pode ser possível para uma entidade maliciosa alterar o conteúdo de um pacote TCP sem precisar de saber o que esse pacote contém. Os dados encriptados podem ser alterados, tornando a desencriptação inválida ou alterando os parâmetros da mensagem que conduza a qualquer resultado que o intruso possa estar interessado em alcançar. Na rede, não podemos impedir que um intruso altere os dados em trânsito, mas podemos fornecer um mecanismo para saber se os dados foram alterados ou não. Quando os dados são alterados em trânsito, serão conhecidos e os dados podem ser rejeitados. Este conceito é *integridade.* Em TLS, a integridade é fornecida por uma classe de rotinas criptográficas conhecidas como *funções de haxixe*. Alguns exemplos de funções de haxixe são MD5 e SHA-1.

### <a name="authentication"></a>Autenticação

O terceiro conceito importante na segurança das comunicações em rede é a ideia de que os dados só devem ser comunicados ao objetivo pretendido. Um intruso pode tentar fazer-se passar por uma entidade legítima para receber dados destinados a outro hospedeiro. Mesmo que os dados estejam a ser enviados com mecanismos de sigilo e integridade em vigor, o intruso pode ainda ser capaz de alcançar o resultado desejado (um compromisso de comunicações seguras) através deste engano. Para evitar isto, é necessário um mecanismo para provar a identidade de um hospedeiro remoto antes de qualquer dado sensível ser enviado. O processo de provar a identidade de um hospedeiro remoto é *a autenticação.* No TLS, a autenticação é fornecida usando certificados digitais, funções de haxixe e um mecanismo chamado *assinaturas digitais* que utiliza uma propriedade de encriptação de chaves públicas (descrito abaixo). Uma forma limitada mas útil de autenticação também pode ser fornecida com uma *chave pré-partilhada* (PSK).

## <a name="tls-encryption"></a>Encriptação TLS

O protocolo TLS é um quadro para fornecer comunicações seguras de rede através da Internet utilizando encriptação. A encriptação é geralmente definida como o processo de codificação de dados de forma a que a obtenção dos dados originais (ou informação sobre esses dados) seja extremamente difícil sem uma *chave*. Nos sistemas informáticos, a encriptação baseia-se em matemáticas complexas, como campos finitos, e pode ser classificada em dois tipos: *chave privada* (ou *encriptação simétrica)* e *chave pública* (ou *encriptação assimétrica).* Exemplos de encriptação de chaves privadas são AES (Advanced Encryption Standard) e RC4 (Rivest Cipher 4). Exemplos de encriptação de chaves públicas são o RSA (Rivest, Shamir, Adleson) e Diffie-Hellman cifras.

O protocolo TLS utiliza as rotinas de encriptação chave privada e pública para proporcionar um equilíbrio de desempenho, segurança e flexibilidade.

### <a name="private-key-encryption"></a>Encriptação Private-Key

A encriptação de chaves privadas está em uso há milhares de anos. As cifras básicas de substituição (em que uma letra ou palavra é substituída por outra letra ou palavra não relacionada) são os primeiros exemplos conhecidos de encriptação, mas com o advento da idade da informação a encriptação privada da chave melhorou significativamente.

Uma cifra de chave privada usa uma "chave" que é simplesmente um valor (que pode ser uma palavra, frase ou número no caso geral) que é usada para de alguma forma codificar alguns dados para que apenas uma entidade que tivesse acesso a essa chave pudesse descodificar os dados de uma forma significativa. A chave é utilizada tanto para encriptação como desencriptação dos dados, daí a *encriptação simétrica* de outro nome.

As cifras-chave privadas são geralmente rápidas e bastante simples de implementar, mesmo que a matemática envolvida sejam extremamente complexas. Por esta razão, o TLS utiliza cifras de chaves privadas para a maior parte das comunicações seguras.

No entanto, a encriptação de chaves privadas tem um problema quando tentamos aplicá-la às comunicações gerais da rede informática: a chave deve ser partilhada entre ambas as máquinas que tentam comunicar. No caso geral, é impraticável e muitas vezes impossível comunicar uma chave privada de forma segura entre duas máquinas na Internet, uma vez que se pode presumir que o tráfego de rede pode ser obtido por qualquer número de entidades nos vários saltos que os dados demoram quando são encaminhados através da Internet. Se a chave for obtida por uma entidade maliciosa, todos os dados encriptados utilizando essa chave estão comprometidos. Como a maioria das máquinas na Internet tem apenas uma ligação de rede e não outro canal seguro para comunicações, o envio de chaves através da rede equivale a enviar os dados desencriptados – não fornece segurança.

Por esta razão, a encriptação de chaves privadas não é suficiente para implementar um protocolo de segurança de comunicações de rede para fins gerais. É aqui que a encriptação da Chave Pública pode ajudar.

NetX Secure TLS suporta encriptação de chave privada AES.

### <a name="public-key-encryption"></a>Encriptação Public-Key

Ao contrário da encriptação de chaves privadas, a encriptação de chaves públicas é um conceito bastante novo, tendo sido desenvolvido na década de 1970. Usando um conceito conhecido como "funções de alçapão" em matemática, descobriu-se que havia uma maneira de partilhar uma chave sobre uma rede sem comprometer a segurança de dados então encriptados.

A forma como a encriptação chave pública funciona é que a chave (no sentido de encriptação de chave privada acima descrito) é dividida em duas partes, uma *chave privada* e uma *chave pública*, de onde a encriptação chave pública obtém o seu nome. O conceito é que uma destas teclas (tipicamente a chave pública) é usada para encriptação, enquanto a outra é usada para desencriptação. Esta assimetria das chaves é a razão para o outro nome para encriptação de chaves públicas: *encriptação assimétrica*.

A matemática por trás da encriptação de chaves públicas é bastante complexa, mas a ideia é que a chave pública *só* pode ser usada para encriptação, e obter essa chave não permite a obtenção de dados encriptados. A chave privada, por sua vez, é a única forma de desencriptar dados encriptados usando a chave pública. Assim, mantendo o segredo chave privado, quem quiser comunicar de forma segura com o proprietário dessa chave privada só precisa de encriptar os seus dados com a chave pública correspondente, sabendo que apenas alguém na posse dessa chave privada pode obter os dados seguros.

NetX Secure TLS suporta encriptação de chave pública RSA.

> [!IMPORTANT] 
> *A RSA é uma operação muito intensiva de processador se a implementação do software RSA for utilizada. Tamanhos de chave maiores aumentam a potência de processamento necessária por um fator quadrado – 4X mais lento para um aumento de 2X no tamanho da chave.*

### <a name="public-key-authentication"></a>Autenticação Public-Key

Um efeito colateral interessante do conceito de encriptação de chaves públicas é que ele pode ser usado para fornecer autenticação, bem como encriptação, fazendo a operação em sentido inverso: encriptar usando a chave *privada* e desencriptar usando a chave *pública.* O mecanismo real para o fazer depende da utilização do algoritmo chave público, mas o conceito é o mesmo.

Para autenticar a autenticação de chave pública, o proprietário de uma chave privada encripta alguns dados (normalmente um haxixe criptográfico dos dados a autenticar) utilizando essa chave privada. Em seguida, alguém que pretenda autenticar que os dados vieram do proprietário da chave privada utiliza a chave pública associada para desencriptar os dados – se a desencriptação for bem sucedida, e assumindo que o utilizador confiou na validade dessa chave pública, então o utilizador pode ter a certeza de que os dados vieram do proprietário da chave privada.

No TLS, a autenticação de chaves públicas é utilizada para verificar a validade de um certificado digital fornecido por um servidor TLS (e opcionalmente o cliente TLS) utilizando chaves públicas da loja de certificados fidedigna. O certificado é verificado com uma chave pública na loja e os dados no certificado são utilizados para verificar a identidade do servidor.

NetX Secure TLS suporta a autenticação RSA.

### <a name="cryptographic-hashing"></a>Hashing criptográfico

A encriptação não é a única operação criptográfica usada no TLS. Para fornecer integridade da mensagem durante uma sessão de TLS, é necessário um checkum para garantir que o conteúdo da mensagem não foi adulterado. No entanto, uma simples parte de verificação (como é utilizada em TCP) é insuficiente para garantir um nível de integridade aceitável, uma vez que pode ser facilmente subvertida por um intruso experiente. O mecanismo utilizado pelo TLS para fornecer integridade da mensagem é conhecido como um *haxixe criptográfico*.

A encriptação é uma codificação 1:1 – ou seja, a totalidade dos dados originais pode ser obtida a partir dos dados encriptados. No entanto, um haxixe mapeia uma quantidade arbitrária de dados num valor de tamanho fixo, tal como uma função de verificação. Ao contrário de uma simples função de verificação, um haxixe é especificamente concebido para reduzir *colisões, onde diferentes dados* de entrada resultam na mesma saída. Numa simples parte de verificação, se um pouco é virado de 1 para 0 e outro de 0 para 1, a parte de verificação é a mesma. Com um haxixe criptográfico, a saída diferia significativamente, dificultando a alteração dos dados de haxixe por parte de um intruso e a operação de haxixe nos dados alterados, resultando assim no mesmo valor (e, portanto, verificando falsamente a integridade desses dados).

O TLS utiliza uma série de algoritmos de haxixe diferentes para fornecer integridade para mensagens, mensagens de aplicação e mensagens de controlo TLS. Estes incluem MD5, SHA-1 e SHA-256.

NetX Secure TLS suporta hashing MD5, SHA-1 e SHA-256.

## <a name="tls-extensions"></a>Extensões TLS

O TLS fornece uma série de extensões que fornecem funcionalidades adicionais para determinadas aplicações. Estas extensões são normalmente enviadas como parte das mensagens ClientHello ou ServerHello, indicando a um anfitrião remoto o desejo de usar uma extensão ou fornecer detalhes adicionais para uso no estabelecimento da sessão TLS segura.

Em geral, as extensões fornecem parâmetros opcionais ao TLS no início do aperto de mão que orientam as operações em curso. Algumas extensões requerem entrada de aplicação ou tomada de decisão, enquanto outras são tratadas automaticamente.

O quadro seguinte descreve as extensões TLS atualmente suportadas pelo NetX Secure TLS:

| **Nome de extensão**              | **Descrição**              |
| ------------------------------- |----------------------------- |
| Indicação de renegociação segura | Esta extensão atenua uma vulnerabilidade de ataque Man-in-the-Middle que pode ocorrer durante um aperto de mão de renegociação.|
| Indicação de nome do servidor          | Esta extensão permite que um Cliente TLS forneça um nome DNS específico a um Servidor TLS, permitindo ao servidor selecionar as credenciais corretas (assume que o servidor tem vários certificados de identidade e pontos de entrada na rede). |
| Algoritmos de assinatura            | Esta extensão permite que um Cliente TLS forneça uma lista de algoritmos de assinatura e haxixe aceitáveis para um Servidor TLS. |

Visão geral das extensões TLS suportadas

### <a name="secure-renegotiation-indication"></a>Indicação de renegociação segura

O TLS suporta a noção de realizar um aperto de mão dentro de uma sessão TLS existente, utilizando assim a sessão estabelecida para encriptar as mensagens de aperto de mão. Este processo permite que as teclas de sessão criptográfica sejam restabelecidas sem terminar a sessão TLS (ver secção "TLS Session Renegociação").

Infelizmente, depois de o TLS ter usado a renegociação há algum tempo, descobriu-se que havia uma vulnerabilidade a um ataque man-in-the-middle que explorava o recurso de renegociação. Para colmatar a vulnerabilidade, foi introduzida a extensão da Indicação de Renegociação Segura. Essencialmente, a extensão de Renegociação Segura utiliza o hash de mensagem acabado a partir da conexão estabelecida para verificar se os anfitriões originais estão a participar no aperto de mão de renegociação – essencialmente o haxixe é usado como um símbolo de verificação sob o pressuposto de que um intruso não seria capaz de forjar o haxixe (o que exigiria acesso às teclas de sessão).

O NetX Secure TLS lida com a renegociação automaticamente e utiliza a Extensão de Renegociação Segura por padrão. Não é necessária qualquer interação de aplicação.

### <a name="server-name-indication"></a>Indicação de nome do servidor

Durante o aperto de mão TLS, um Cliente TLS espera que um servidor remoto forneça um certificado de identidade para que o cliente possa autenticar o servidor. No entanto, pode haver alguns casos em que um servidor irá fornecer vários serviços diferentes com diferentes servidores "virtuais" cada um com identidades únicas. No caso de um único servidor com múltiplas identidades, um cliente TLS pode fornecer um nome DNS específico que o servidor utilizará para selecionar as credenciais adequadas – o mecanismo para fornecer este nome é a extensão de Indicação de Nome do Servidor (SNI).

Para uma aplicação utilizando a extensão SNI, é necessária alguma interação. Para os Clientes TLS, a aplicação deve fornecer um nome DNS para ser enviado para o servidor remoto. Para os Servidores TLS, a aplicação deve ler o nome DNS a partir da extensão e selecionar um certificado apropriado para enviar de volta para o cliente.

As seguintes secções fornecem mais detalhes sobre como utilizar a extensão SNI em NetX Secure TLS.

### <a name="sni-extension--tls-client"></a>Extensão SNI – Cliente TLS

Um Cliente NetX Secure TLS que pretenda utilizar a extensão SNI deve fornecer um nome DNS ao TLS para ser fornecido durante o aperto de mão. Este nome deve ser inicializado e fornecido antes de iniciar uma sessão de TLS uma vez que a extensão é enviada na mensagem ClientHello que inicia o processo de aperto de mão.

O seguinte corte de código ilustra a utilização da extensão. Primeiro, um objeto NX_SECURE_X509_DNS_NAME é inicializado com o nome do servidor pretendido. Em seguida, antes de iniciar a sessão TLS, o nome é fornecido ao TLS usando a API de extensão SNI. Uma vez definido o nome, não é necessária mais nenhuma ação. Consulte a referência da API no Capítulo 4  
  
Descrição dos Serviços De Segurança NetX para mais informações sobre as funções individuais.

```C
/* The dns_name variable will contain our desired server name. */
UINT status;
NX_SECURE_X509_DNS_NAME dns_name;

/* Initialize the server DNS name. */
status = nx_secure_x509_dns_name_initialize(&dns_name, "www.example.com", 
                                            strlen("www.example.com"));


/* Initialize SNI extension in previously-initialized TLS Session. */
status = nx_secure_tls_session_sni_extension_set(&client_tls_session, &dns_name);

/* Now start the TLS session, starting with establishing the TCP connection – if 
   TLS is started before initializing the SNI extension, the extension will not be 
   sent in the ClientHello message! */
status = nx_tcp_client_socket_connect(&client_socket, IP_ADDRESS(1, 2, 3, 4), 443, 
                                      5 * NX_IP_PERIODIC_RATE);

status = nx_secure_tls_session_start(&client_tls_session, &client_socket, 
                                     NX_WAIT_FOREVER);
```
### <a name="sni-extension--tls-server"></a>Extensão SNI – Servidor TLS

Do lado do Servidor TLS, a extensão SNI pode ser processada pela aplicação de forma a selecionar credenciais adequadas (por exemplo, certificado) para fornecer ao cliente remoto durante o aperto de mão. Para isso, a aplicação deve fornecer uma chamada de sessão que é invocada após a receção de uma mensagem ClientHello.

O código de exemplo para a API nx_secure_tls_session_server_callback_set (ver página 122) ilustra a análise de uma extensão SNI recebida utilizando uma chamada de servidor. Essencialmente, o Servidor TLS recebe um ClientHello e invoca a chamada. Em seguida, a aplicação utiliza o *nx_secure_tls_session_sni_extension_parse* API para analisar os dados de extensão fornecidos à chamada para encontrar a extensão SNI e devolver o nome DNS fornecido (note que a extensão suporta apenas um único nome DNS). Uma vez obtido o nome, a aplicação utiliza-o para encontrar e enviar o certificado de identidade do servidor apropriado (e cadeia de emitentes, se aplicável).

### <a name="signature-algorithms-extension"></a>Extensão de algoritmos de assinatura

Esta extensão é específica do TLS 1.2 e permite que um Cliente TLS forneça uma lista de pares de algoritmos de assinatura e haxixe aceitáveis que sejam aceitáveis para uso na geração e verificação de assinaturas digitais. A lista é gerada automaticamente pelo NetX Secure TLS para clientes TLS utilizando a tabela de cifra fornecida à *nx_secure_tls_session_create*. Não é necessária qualquer interação de aplicação.

## <a name="authentication-methods"></a>Métodos de Autenticação

O TLS fornece o enquadramento para estabelecer uma ligação segura entre dois dispositivos através de uma rede insegura, mas parte do problema é saber a identidade do dispositivo na outra extremidade dessa ligação. Sem um mecanismo para autenticar a identidade dos anfitriões remotos, torna-se uma operação trivial para um intruso fazer-se passar por um dispositivo de confiança.

Inicialmente, pode parecer que a utilização de endereços IP, endereços MAC de hardware ou DNS forneceria um nível de confiança relativamente elevado para identificar os anfitriões numa rede, mas dada a natureza da tecnologia TCP/IP e a facilidade com que os endereços podem ser falsificados e as entradas de DNS corrompidas (por exemplo, através do envenenamento por cache DNS), torna-se claro que o TLS precisa de uma camada adicional de proteção contra identidades fraudulentas.

Existem vários mecanismos que podem fornecer esta camada extra de autenticação para TLS, mas o mais comum é o *certificado digital.* Outros mecanismos incluem chaves pré-partilhadas (PSK) e esquemas de senha.

### <a name="digital-cerificates"></a>Cerifas digitais

Os certificados digitais são o método mais comum para autenticar um hospedeiro remoto em TLS. Essencialmente, um certificado digital é um documento com formatação específica que fornece informações de identidade para um dispositivo numa rede de computador.

O TLS normalmente usa um formato chamado X.509, uma norma desenvolvida pela União Internacional de Telecomunicações, embora outros formatos de certificados possam ser usados se os anfitriões TLS puderem concordar com o formato que está a ser utilizado. X.509 define um formato específico para certificados e várias codificações que podem ser usadas para produzir um documento digital. A maioria dos certificados X.509 utilizados com TLS são codificados usando uma variante de ASN.1, outra norma de telecomunicações. Dentro da ASN.1 existem várias codificações digitais, mas a codificação mais comum para certificados TLS é a norma Distinguished Encoding Rules (DER). O DER é um subconjunto simplificado das Regras Básicas de Codificação (BER) as ASN.1 que são concebidas para ser inequívocas, facilitando a análise. Por cima do fio, os certificados TLS são geralmente codificados em DER binário, e este é o formato que o NetX Secure espera para os certificados X.509.

Embora os certificados binários formatados pelo DER sejam utilizados no protocolo TLS real, podem ser gerados e armazenados em várias codificações diferentes, com extensões de ficheiros tais como .pem, .crt e .p12. As diferentes variantes são usadas por diferentes aplicações de diferentes fabricantes, mas geralmente todas podem ser convertidas em DER usando ferramentas amplamente disponíveis.

A mais comum das codificações de certificados alternativos é o PEM. O formato PEM (a partir do Privacy-Enhanced Mail) é uma versão codificada base-64 da codificação DER que é frequentemente utilizada porque a codificação resulta em texto imprimível que pode ser facilmente enviado usando protocolos de e-mail ou web.

Gerar um certificado para a sua aplicação NetX Secure está geralmente fora do âmbito deste manual, mas a ferramenta de linha de comando OpenSSL[(www.openssl.org)](http://www.openssl.org)está amplamente disponível e pode converter entre a maioria dos formatos.

Dependendo da sua aplicação, poderá gerar os seus próprios certificados, ser fornecido certificados por um fabricante ou organização governamental, ou adquirir certificados a uma autoridade de certificados comerciais.

Para utilizar um certificado digital na sua aplicação NetX Secure, tem primeiro de converter o seu certificado num formato binário DER e, opcionalmente, converter a chave privada associada (o "expoente privado" para rSA, por exemplo) num formato binário, tipicamente uma chave RSA codificada por PKCS#1 ou uma chave ECC codificada por DER. Uma vez concluída a conversão, cabe-lhe a si carregar o certificado e a chave privada no dispositivo. As opções possíveis incluem a utilização de um sistema de ficheiros baseado em flash ou a geração de um conjunto C a partir dos dados (utilizando uma ferramenta como "xxd" do Linux) e a compilação do certificado e chave na sua aplicação como dados constantes.

Uma vez que o seu certificado é carregado no dispositivo, a API TLS pode ser usada para associar o seu certificado a uma sessão de TLS.

Para mais detalhes e exemplos sobre como utilizar certificados X.509 com NetX Secure TLS, consulte a secção "Importar certificados X.509 em NetX Secure".

Consulte os seguintes serviços TLS na referência API para obter mais informações:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_local_certificate_remove
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_trusted_certificate_add
- nx_secure_trusted_certificate_remove

### <a name="tls-client-certificate-specifics"></a>Especificidades do Certificado de Cliente TLS

As implementações do Cliente TLS geralmente não requerem que um certificado "local"<sup>14</sup> seja carregado no dispositivo. A exceção a isso é quando a Autenticação do Certificado de Cliente está ativada, mas isso é muito menos comum.

Um Cliente TLS requer que seja carregado pelo menos um certificado "fidedigno"<sup>15</sup> (mais pode ser carregado se necessário) e espaço para a atribuição de um certificado "remoto"<sup>16.</sup>

Para obter mais informações sobre a adição de certificados fidedignos e a atribuição de espaço para certificados remotos, consulte a referência TLS API para os seguintes serviços: nx_secure_tls_remote_certificate_allocate, nx_secure_tls_trusted_certificate_add.

14. Um certificado "local" é um certificado que identifica o dispositivo local – ou seja, fornece informações de identidade para o dispositivo sobre o qual a aplicação TLS é carregada.

15. Um certificado "fidedigno" é um certificado que fornece uma base de confiança e autenticação do dispositivo remoto, quer diretamente quer através de uma Infraestrutura de Chave Pública (PKI). A raiz da cadeia de confiança é geralmente chamada de "Autoridade de Certificação" ou certificado de CA.

16. Um certificado "remoto" refere-se ao certificado enviado pelo anfitrião remoto durante o aperto de mão TLS. Fornece identidade para o hospedeiro remoto e é autenticado comparando-o com um certificado "fidedigno" no dispositivo local.

### <a name="tls-server-certificate-specifics"></a>Especificidades do certificado do servidor TLS

As implementações do Servidor TLS geralmente não requerem certificados "fidedignos" para serem carregados no dispositivo ou certificados remotos a serem atribuídos. A exceção a este ser quando a autenticação do Certificado de Cliente está ativada (isto é menos comum).

Um Servidor TLS requer que seja carregado um certificado "local" para que o servidor o possa fornecer ao cliente remoto durante o aperto de mão TLS para autenticar o servidor ao cliente.

Para obter mais informações sobre o carregamento de certificados locais para utilização com aplicações de servidor NetX TLS, consulte a referência API para os seguintes serviços: 
- nx_secure_tls_local_certificate_add, 
- nx_secure_tls_local_certificate_remove.

### <a name="pre-shared-keys-psk"></a>Chaves pré-partilhadas (PSK)

Um mecanismo alternativo para fornecer autenticação de identificação em TLS é a noção de Chaves Pré-Partilhadas (PSK). A utilização de um cifrasuite PSK remove a necessidade de fazer as operações de encriptação intensivas de chaves públicas do processador, um bónus para dispositivos incorporados com recursos limitados. O PSK substitui o certificado no aperto de mão TLS e é usado no lugar da geração de chave de sessão pré-master encriptada para a geração de chaves de sessão TLS.

As cifrasuites psk são limitadas no sentido de que um segredo partilhado deve estar presente em ambos os dispositivos antes de uma sessão de TLS ser estabelecida. Isto significa que os dispositivos devem ter sido carregados com esse segredo usando alguns meios seguros que não uma ligação PSK TLS - os PSKs podem ser atualizados através de uma ligação PSK TLS, mas o dispositivo deve necessariamente começar com uma PSK que é carregada através de algum outro mecanismo. Por exemplo, um dispositivo sensor e o seu dispositivo gateway poderiam ser carregados com PSKs na fábrica antes do envio, ou uma ligação TLS padrão (com um certificado) poderia ser usada para carregar o PSK.

Os cifrasuites PSK vêm em algumas formas, descritas no RFC 4279. A primeira utiliza teclas RSA ou Diffie-Hellman que são utilizadas da mesma forma que as chaves públicas transmitidas no certificado nos apertos de mão TLS padrão. O segundo formulário, que é mais utilizado num ambiente restrito a recursos, utiliza uma PSK que é usada para gerar diretamente as teclas de sessão (para utilização pela AES, por exemplo), evitando a utilização das operações de RSA ou Diffie-Hellman caras.

O NetX Secure suporta a segunda forma de cifrasuites PSK, permitindo que as aplicações removam todo o código de criptografia e utilização da memória de chaves públicas. O PSK em si não é uma chave AES, mas pode ser considerado como sendo mais uma palavra-passe a partir da qual as chaves reais são geradas. Existem poucas restrições sobre o valor psk, embora valores mais longos forneçam mais segurança (o mesmo que com as palavras-passe).

Para utilizar o PSK com a sua aplicação NetX Secure, tem primeiro de definir a macro global **NX_SECURE_ENABLE_PSK_CIPHERSUITES**. Isto é geralmente feito através das definições do seu compilador, mas a definição também pode ser colocada no ficheiro de cabeçalho nx_secure_tls.h. Com o suporte de cifrasumita PSK definido, o suporte cifrasuite PSK será compilado na sua aplicação NetX Secure TLS.

Com o suporte psk ativado, pode então utilizar a API TLS para configurar PSKs para a sua aplicação. Cada PSK exigirá um valor PSK (a "chave" secreta real – mantenha este valor seguro), um valor de "identidade" usado para identificar o PSK específico, e uma "dica de identidade" que é usada por um servidor TLS para escolher um determinado valor PSK.

O próprio PSK pode ser qualquer valor binário, uma vez que nunca é enviado por uma ligação de rede. O PSK pode ter qualquer valor até 64 bytes de comprimento.

A identidade e a sugestão devem ser cordas de caracteres imprimíveis formatadas usando UTF-8. Os valores de identidade e sugestão podem ter até 128 bytes.

A identidade e o PSK formam um par único que é carregado em todos os dispositivos da rede que precisam de comunicar uns com os outros.

A "dica" é usada principalmente para definir perfis de aplicação específicos para grupo de PSKs por função ou serviço. Estes valores devem ser acordados antecipadamente e dependem da aplicação. Como exemplo, a aplicação do servidor da linha de comando OpenSSL (com o PSK ativado) utiliza a cadeia padrão "Client_identity", que deve ser fornecida por um cliente TLS para continuar com o aperto de mão TLS.

Para obter mais informações sobre psks, consulte a referência NetX Secure API para os seguintes serviços: nx_secure_tls_client_psk_set, nx_secure_tls_psk_add.

## <a name="importing-x509-certificates-into-netx-secure"></a>Importar certificados X.509 para o NetX Secure

São necessários certificados digitais para a maioria das ligações TLS na Internet. Os certificados fornecem um método para autenticar anfitriões anteriormente desconhecidos através da Internet através da utilização de intermediários de confiança, normalmente *chamados Autoridades de Certificados* ou CAs. Para ligar o seu dispositivo NetX Secure a um serviço de nuvem comercial (como a Amazon Web Services), terá de importar certificados para a sua aplicação carregando-os no seu dispositivo.

Juntamente com os certificados, você também vai precisar de uma *chave privada* que está associada ao seu certificado. Em algumas aplicações (como o Cliente TLS quando a Autenticação do Certificado de Cliente não estiver a ser utilizada) o certificado por si só será suficiente, mas se o seu certificado estiver a ser utilizado para identificar o seu dispositivo, necessitará de uma chave privada. As chaves privadas são normalmente geradas quando cria o seu certificado e são armazenadas num ficheiro separado, muitas vezes encriptado com uma palavra-passe.

### <a name="certificate-types"></a>Tipos de Certificado

Os certificados digitais são geralmente utilizados para identificar entidades numa rede, mas dependendo da sua aplicação terão propriedades ligeiramente diferentes.

### <a name="local-certificates"></a>Certificados Locais

Para efeitos desta documentação, referir-nos-emos aos "certificados locais" como os certificados que fornecem uma identidade para o nosso dispositivo local (outro nome possível poderia ser "certificado de dispositivo"). Estes certificados serão fornecidos a um anfitrião remoto quando o anfitrião remoto desejar autenticar o dispositivo local.

### <a name="remote-certificates"></a>Certificados Remotos

Nesta documentação, "certificados remotos" refere-se aos certificados fornecidos por um anfitrião remoto durante o aperto de mão TLS quando aplicável. O espaço para estes certificados deve ser atribuído ou o NetX Secure não poderá analisá-los e completar o aperto de mão TLS.

### <a name="signing-certificates"></a>Certificados de Assinatura

Um "certificado de assinatura" é utilizado para assinar digitalmente outros certificados ou dados para efeitos de autenticação. Estes certificados podem ser certificados intermédios ou de raiz dentro de uma Infraestrutura de Chave Pública (PKI) e geralmente não são utilizados para identificar dispositivos ou hospedeiros individuais.

### <a name="root-ca-certificates"></a>Certificados Root CA

Os "certificados Root CA" são certificados de assinatura que fornecem a base de um PKI e são auto-assinados, em vez de serem assinados por outro certificado de assinatura. Normalmente, pelo menos um certificado Root CA é normalmente necessário para que um Cliente TLS verifique servidores remotos.

### <a name="certificate-formats"></a>Formatos de certificado

Os certificados digitais são simplesmente ficheiros que contêm dados estruturados codificados utilizando a sintaxe ASN.1. No entanto, existem vários formatos em que os certificados podem ser armazenados e é importante ter o formato certo antes de carregar um certificado numa aplicação NetX Secure.

Os formatos mais comuns para certificados são DER e PEM. DER (para *Distinguished Encoding Rules*, um formato ASN.1) é o formato binário utilizado pela TLS na realização do aperto de mão inicial. PEM (do *Privacy Enhanced Mail)* é uma versão codificada base-64 do formato DER que é adequada para enviar e-mail ou enviar HTTP na web. Diferentes fornecedores utilizam diferentes extensões de nome de ficheiros para certificados, tais como ".pem" ou ".crt" para certificados PEM, e ".der" para certificados DER. Se tiver um certificado e não for claro qual o formato utilizado, a abertura do ficheiro num editor de texto permitir-lhe-á determinar o tipo uma vez que os ficheiros DER são binários codificados, e os ficheiros PEM são texto ASCII regular que começam com o cabeçalho "-----BEGIN CERTIFICATE-----".

O NetX Secure requer que o seu certificado esteja em formato DER binário, pelo que terá de converter o seu certificado em formato DER antes de importar. Isto pode ser feito com ferramentas prontamente disponíveis, como o OpenSSL.

Se necessitar de uma chave privada para a sua aplicação, o ficheiro chave será codificado utilizando PEM ou DER num formato específico (PKCS#1 para RSA, RFC 5915 para ECC). O ficheiro chave privado terá de ser convertido em DER antes de ser importado.

Os seguintes comandos OpenSSL são dados como exemplo para converter certificados e ficheiros de chaves RSA no formato DER exigido pelo NetX Secure (ECC é semelhante – consulte a documentação OpenSSL).

```C
openssl x509 -inform PEM -in <certificate> -outform DER -out cert.der
openssl x509 -inform PEM -in <root CA cert> -outform DER -out CA_cert.der
openssl rsa -inform PEM -in <private key> -outform DER -out private.key
```
### <a name="private-keys-and-certificates"></a>Chaves e Certificados Privados

Para os certificados que identifiquem um dispositivo, a chave privada associada deve ser carregada juntamente com o certificado. A chave privada (que pode ser para um dos algoritmos de chave pública como RSA, Diffie-Hellman ou Elliptic-Curve Cryptography) é usada por um servidor TLS para desencriptar o material chave de entrada (o "segredo pré-mestre") de um cliente TLS, autenticando-se assim ao cliente. Para um Cliente TLS, se for fornecido um certificado de identidade (um certificado com a sua chave privada associada) e um servidor solicitar um certificado de cliente, a chave privada é utilizada para autenticar o cliente – no caso da RSA o cliente encripta um símbolo utilizando a chave privada que o servidor então desencripta utilizando a chave pública do cliente,  fornecida no certificado de cliente (a autenticação Diffie-Hellman e ECC acontece de forma semelhante, mas os detalhes são um pouco diferentes).

Na Segurança NetX, o *nx_secure_x509_certificate_initialize* de serviço é utilizado para rubricar um certificado X.509 (ver secção "Carregar certificados no seu dispositivo" para obter mais informações) e associar opcionalmente uma chave privada a esse certificado.

Se for fornecida uma chave privada, o certificado é marcado como sendo o certificado de "identidade" utilizado para identificar o dispositivo. A chave é passada como uma bolha binária contígua e um comprimento, com um tipo de chave associado. O tipo de chave depende do tipo de chave (por exemplo, RSA, ECC, etc.) e do formato (por exemplo, PKCS#1 DER). Se não for fornecida nenhuma chave, o valor NX_SECURE_X509_KEY_TYPE_NONE (valor 0x0) pode ser passado para indicar que não está a ser fornecida nenhuma chave (um comprimento de 0 e um ponteiro NX_NULL para o parâmetro de dados obterá o mesmo efeito).

A tabela seguinte mostra os tipos-chave conhecidos pelo NetX Secure e o identificador de tipo associado a ser passado para *nx_secure_x509_certificate_initialize*. Serão adicionados tipos de chaves adicionais à medida que mais algoritmos de encriptação forem adicionados ao NetX Secure.

| Identificador                              | Algoritmo | Formato   | Encoding | Valor |
| --------------------------------------- | --------- | -------- | -------- | ----- |
| NX_SECURE_X509_KEY_TYPE_NONE            | Nenhuma      | N/D      | N/D      | 0x0   |
| NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER   | RSA       | PKCs #1   | DER      | 0x1   |
| NX_SECURE_X509_KEY_TYPE_EC_DER          | ECDSA     | RFC 5915 | DER      | 0x2   |

### <a name="user-defined-private-key-types"></a>Tipos de chaves privadas definidos pelo utilizador

Os valores dos identificadores-chave para o serviço *nx_secure_x509_certificate_initialize* regem as ações tomadas quando a chave privada é fornecida. Para tipos conhecidos, os valores estão na gama 0x0000 0000 – 0x0000 FFFF (16 bits inferiores de um inteiro não assinado de 32 bits). Para plataformas com tipos de chave personalizados<sup>17</sup> (como é o caso de alguns motores de encriptação baseados em hardware), um tipo de chave definido pelo utilizador na gama 0x0000 FF FF 1000-0xFFFF (top 16 bits não zero) pode ser passado como o tipo chave. Se alguma das 16 bits superiores do tipo chave estiver definida, os dados da chave privada são transmitidos diretamente para a rotina criptográfica adequada (por exemplo, RSA) fornecida na tabela de cifrasumita TLS. Os tipos de chaves definidos pelo utilizador não são analisados ou processados de outra forma antes de serem passados para a rotina criptográfica. Além disso, o tipo de chave definida pelo utilizador também será passado para a rotina criptográfica para que qualquer processamento adequado possa ser manuseado a esse nível.

Note que os tipos de chaves definidos pelo utilizador são geralmente utilizados para plataformas de hardware específicas que utilizam dados de chaves personalizados (possivelmente encriptados). Geralmente, isto implica que os dados-chave são gerados ou codificados usando um mecanismo específico desse fornecedor de hardware (ou no caso de um padrão como PKCS#11, uma padrão específica). Consulte a documentação da sua plataforma de hardware para obter mais informações.

17. Os tipos de chaves definidos pelo utilizador requerem uma rotina criptográfica personalizada correspondente para lidar com o formato de chave personalizada. A rotina criptográfica deve ter um algoritmo correspondente (por exemplo, RSA) e ser transmitida para TLS na tabela cifrasuite. 

### <a name="loading-certificates-onto-your-device"></a>A carregar certificados no seu dispositivo

Qualquer método para carregar um ficheiro no seu dispositivo será suficiente para importar os seus certificados.

O método mais simples para carregar um certificado é converter os dados binários codificados pelo DER numa matriz C e compilá-lo na sua aplicação como uma constante. Isto pode ser facilmente feito com ferramentas como "xxd" em Linux (com a opção "-i").

Em alternativa, pode carregar o seu certificado num sistema de ficheiros flash ou outras opções de armazenamento, desde que possa passar um ponteiro para os dados do certificado na API NetX Secure.

### <a name="certificate-files-needed-for-netx-secure"></a>Ficheiros de certificados necessários para o NetX Secure

Os ficheiros de certificado que terá de importar dependem da sua aplicação. Em geral, os Servidores TLS requerem um certificado para identificar o dispositivo, e os Clientes TLS exigem um ou mais *Certificados Fidedignos* para autenticar servidores remotos. A tabela a seguir ilustra os certificados necessários para algumas aplicações TLS diferentes.

| **Funcionalidade/opções TLS**                     | **Certificados/chaves necessários (mínimo)**              |
| ------------------------------------------------- | --------------------------------------------------- |
| Cliente TLS                                        | Certificado root CA                                 |
| Servidor TLS                                        | Certificado local, chave privada para esse certificado |
| Servidor TLS com autenticação de certificado de cliente | Certificado local, chave privada, Root CA             |
| Cliente TLS com Autenticação de Certificado de Cliente | Certificado local, chave privada, Root CA             |
| Cliente ou Servidor TLS apenas com chaves pré-partilhadas    | Nenhum (PSK utilizado em vez de certificados)             |

Os serviços relevantes para os certificados de carregamento são os seguintes:

| **Nome API**                                   | **Objetivo**                                            |
| ---------------------------------------------- |------------------------------------------------------- |
| nx_secure_x509_certificate_initialize      | Deve ser solicitado que todos os certificados povoem a estrutura NX_SECURE_X509_CERT com os seus dados de certificado e chave privada. |
| nx_secure_tls_local_certificate_add       | Adicione um certificado local a uma sessão de TLS para identificar o seu dispositivo.                                                                |
| nx_secure_tls_local_certificate_remove    | Remova um certificado local de uma sessão de TLS.                                                                                   |
| nx_secure_tls_remote_certificate_allocate | Alocar espaço para um certificado remoto (chamado com um NX_SECURE_X509_CERT não-iniciado).                                   |
| nx_secure_tls_trusted_certificate_add     | Adicione um certificado a uma Sessão TLS como um Certificado fidedigno para autenticar anfitriões remotos.                                     |
| nx_secure_tls_trusted_certificate_remove  | Remova um certificado de confiança de uma Sessão TLS.                                                                                 |

### <a name="working-with-aws-iot-certificates"></a>Trabalhar com certificados AWS IoT

Na interface IoT da Amazon Web Services, selecione "Security" no menu da barra lateral e selecione "Certificados". Crie um novo certificado e siga as instruções para descarregar o seu novo certificado de dispositivo.

Uma vez descarregado os seus certificados, terá de os converter em formato DER utilizando o OpenSSL ou um utilitário similar.

NOTA: A AWS também fornecerá um ficheiro de chave pública. A chave pública está contida no certificado de dispositivo local, pelo que não precisa de ser importada para a sua aplicação.

Como exemplo, aqui estão os comandos para converter o certificado de dispositivo local e a sua chave privada em formato DER para utilização com NetX Secure:

```C
openssl x509 -inform PEM -in <certificate> -outform DER -out cert.der
openssl x509 -inform PEM -in <root CA cert> -outform DER -out CA_cert.der
openssl rsa -inform PEM -in <private key> -outform DER -out private.key
```
Os ficheiros convertidos podem ser importados para a sua aplicação seguindo as instruções acima.

## <a name="x509-certificate-validation-in-netx-secure"></a>Validação de certificado X.509 em NetX Secure 

Ao utilizar o TLS com certificados X.509 para identificação e verificação do anfitrião, é importante entender como esses certificados são realmente validados. Embora a especificação TLS não forneça instruções detalhadas sobre como validar um certificado, refere-se à especificação X.509 (RFC 5280). Em geral, espera-se que o TLS efetue pelo menos uma validação básica nos certificados de entrada (os certificados fornecidos pelo anfitrião remoto durante o aperto de mão TLS) e o NetX Secure TLS não é diferente.

### <a name="basic-x509-validation"></a>Validação Básica X.509

Para qualquer certificado de entrada, o NetX Secure TLS realizará a validação básica do caminho X.509. O processo consiste em verificar a assinatura digital de cada certificado com o seu certificado emitente, que pode ser fornecido pelo anfitrião remoto ou estar localizado na loja de certificados fidedignas (ver secção "Importar certificados X.509 no NetX Secure" para obter mais informações sobre a importação de certificados fidedignos). O processo de validação é repetido repetidamente nos certificados emitentes até que um certificado de confiança seja atingido ou o fim da cadeia (com um certificado auto-assinado ou um certificado emitente em falta). Se for alcançado um certificado de confiança, o certificado é verificado, caso contrário será rejeitado. Adicionalmente, em cada fase do processo de verificação, a data de validade de cada certificado é verificada em função do tempo de envio da aplicação (consulte o serviço "nx_secure_tls_session_time_function_set" para obter mais informações).

A especificação X.509 também fornece um algoritmo para apoiar "políticas", que são identificadores que estão presentes numa extensão X.509 que pode ser verificada durante a validação do caminho. O NetX Secure trata atualmente os certificados X.509 como se a opção "anyPolicy" fosse definida – ou seja, todas as políticas são aceitáveis e a verificação de políticas opcional não é realizada. A implementação NetX Secure X.509 pode ser aumentada com esta funcionalidade numa futura versão. Por enquanto, a extensão da apólice pode ser obtida a partir de um certificado utilizando a *API nx_secure_x509_extension_find.*

Uma vez concluída a validação do percurso básico, a TLS invocará a chamada de verificação do certificado fornecida pela aplicação utilizando a API *nx_secure_tls_session_certificate_callback_set.* Se não for fornecida nenhuma chamada, considera-se que o certificado é de confiança na sequência de uma validação bem sucedida do caminho. Se for fornecida uma chamada, a chamada realizará qualquer validação adicional do certificado exigido pelo pedido. O valor de retorno da chamada é usado para determinar se continua com o aperto de mão TLS ou abortar o aperto de mão devido a uma falha de validação.

A chamada é invocada com um ponteiro para a sessão TLS relevante e um ponteiro NX_SECURE_X509_CERT para o certificado a validar. Entre a sessão TLS e o certificado, o pedido tem todos os dados de que necessita da TLS para efetuar verificações adicionais de verificação.

Para ajudar na validação adicional, o NetX Secure fornece rotinas X.509 para algumas operações de validação comuns, incluindo validação de DNS e verificação da Lista de Revogação de Certificados. Todas estas rotinas são adequadas para utilização dentro da chamada de verificação do certificado, mas também podem ser usadas para efetuar a verificação off-line dos certificados X.509.

A tabela seguinte resume as funções de ajudante disponíveis para o processamento de certificados X.509. Explicações mais pormenorizadas para as operações podem ser encontradas nas secções seguintes e na referência da API no capítulo 4  
  
A descrição dos Serviços Seguros NetX fornece detalhes adicionais sobre as rotinas específicas.

| **Nome API**                             | **Descrição**                               |
| ---------------------------------------- | -------------------------------------- |
| nx_secure_x509_common_name_dns_check               | Verifique o nome comum e o nome de assunto X.509 com o nome de DNS esperados |
| nx_secure_x509_crl_revocation_check                 | Verifique se há um certificado revogado numa Lista de Revogação de Certificados X.509 (CRL)       |
| nx_secure_x509_extended_key_usage_extension_parse | Parse e encontre um OID específico de chave estendida num certificado                   |
| nx_secure_x509_key_usage_extension_parse           | Parse e devolva o bitfield de utilização chave em um certificado                            |
| nx_secure_x509_extension_find                        | Encontre e devolva os dados ASN.1 codificados em bruto para uma extensão específica.            |

Funções de ajudante X.509 para utilização na chamada de verificação de certificados

### <a name="x509-extensions"></a>Extensões X.509

A especificação X.509 descreve uma série de "extensões" que podem ser usadas para fornecer informações adicionais que podem ser utilizadas na verificação de certificados. Na maior parte das vezes, estas extensões são opcionais e não são necessárias para validação segura de um certificado digital contra um certificado de raiz fidedigno. No entanto, o NetX Secure suporta algumas extensões básicas. O suporte a extensões adicionais pode ser adicionado em futuras versões.

As extensões atualmente suportadas estão listadas no quadro seguinte:

| Nome de extensão           | Description                                                                   | API relevante                                             |
| ------------------------ | ----------------------------------------------------------------------------- | -------------------------------------------------------- |
| Utilização de Chaves                | Fornece usos aceitáveis para a chave pública de um certificado em um campo de bits         | nx_secure_x509_key_usage_extension_parse           |
| Utilização Alargada da Chave       | Fornece utilizações aceitáveis adicionais para a chave pública de um certificado utilizando OIDs | nx_secure_x509_extended_key_usage_extension_parse |
| Nome Alternativo do Requerente | Fornece nomes DNS alternativos que também são representados pelo certificado   | nx_secure_x509_common_name_dns_check               |

### <a name="unsupported-x509-extensions"></a>Extensões X.509 não suportadas

A implemenação X.509 da NetX Secure fornece um serviço para extrair extensões não apoiadas também: *nx_secure_x509_extension_find*. Esta API destina-se a utilizadores avançados, uma vez que requer conhecimentos de ASN.1 codificados pelo DER, a fim de analisar os dados devolvidos. Utilizou-se internamente para extrair extensões suportadas, mas é fornecido por conveniência no desenvolvimento de suporte personalizado para extensões X.509.

Para utilizar nx_secure_x509_extension_find, é passado um NX_SECURE_X509_EXTENSION, juntamente com o certificado e um ID de extensão, que é uma representação mais longa da cadeia OID de comprimento variável para um tipo de extensão conhecido. Uma lista completa de OIDs suportados para extensões X.509 está fornecida na referência API para nx_secure_x509_extension_find na página 178.

A estrutura NX_SECURE_X509_EXTENSION é definida da seguinte forma:

```C
typedef struct NX_SECURE_X509_EXTENSION_STRUCT
{
    /* Identifier (maps to OID) for this extension. */
    USHORT nx_secure_x509_extension_id;

    /* Critical flag - boolean value. */
    USHORT nx_secure_x509_extension_critical;

    /* Pointer to DER-encoded extension data. */
    const UCHAR *nx_secure_x509_extension_data;
    ULONG        nx_secure_x509_extension_data_length;
} NX_SECURE_X509_EXTENSION;
```
Quando o serviço regressar com sucesso, a estrutura será povoada com os dados relevantes do certificado. O campo nx_secure_x509_extension_id é geralmente utilizado para fins internos, mas será povoado com a representação de inteiros OID relevante. O campo nx_secure_x509_extension_critical expõe o valor crítico da bandeira de extensão X.509 (Boolean). Os campos nx_secure_x509_extension_data e nx_secure_x509_extension_data_length contêm um ponteiro para os dados ASN.1 codificados pelo DER para a extensão e o comprimento desses dados, respectivamente.

A análise real dos dados da extensão ASN.1 está fora do âmbito deste documento, mas se tiver acesso à fonte NetX Secure TLS pode ver como a análise é feita onde quer que nx_secure_x509_extension_find seja chamada para extensões apoiadas.

### <a name="x509-dns-validation"></a>Validação de DNS X.509

Uma operação comum de validação de certificados em TLS envolve verificar o nome Top-Level Domínio (TLD) de um hospedeiro remoto contra o certificado X.509 fornecido por esse anfitrião durante o aperto de mão TLS. Esta operação ajuda a garantir que o certificado corresponde de facto ao servidor anfitrião que o forneceu, assumindo que a procura de DNS é de confiança. No NetX Secure TLS, esta funcionalidade é fornecida pelo **nx_secure_x509_common_name_dns_check** de serviço , que recebe o certificado e uma cadeia contendo a parte TLD do URL utilizado para aceder ao anfitrião. O TLD é comparado com o campo nome comum do certificado e, se corresponder, NX_SUCCESS é devolvido. Se o Nome Comum não corresponder, a rotina também verificará a existência do *sujeito* de extensão de certificado X.509AltName . Se estiver presente um assuntoAltName, quaisquer entradas dnsname na extensão também são verificadas contra o TLD fornecido. Mais uma vez, se houver qualquer jogo, NX_SUCCESS é devolvido. Se não for encontrado qualquer correspondência, é devolvido um erro adequado para a devolução da chamada de validação do certificado.

### <a name="x509-key-usage-and-extended-key-usage-extensions"></a>Utilização da chave X.509 e extensões de utilização de chaves estendidas

As extensões de utilização da chave X.509 e extensões de utilização de chaves estendidas fornecem informações sobre como a chave pública de um certificado pode ser usada ao autenticar esse certificado. A utilização da chave é fornecida pelo emitente do certificado quando o certificado é assinado e emitido. A utilização da chave pode ser utilizada por um anfitrião TLS para verificar se o certificado está autorizado a ser utilizado para autenticar um anfitrião TLS remoto e realizar outras operações.

A extensão de utilização da chave consiste num simples bitfield onde cada um dos bits representa uma utilização específica da chave. Uma lista completa destes valores é fornecida na referência da API para *nx_secure_x509_key_usage_extension_parse* na página 183. Para uma descrição mais completa das partes-chave de utilização e dos seus significados, consulte o RFC 5280, secção 4.2.1.3.

A extensão de utilização da chave estendida, tal como a extensão de utilização da chave, fornece informações aceitáveis sobre o uso da chave. No entanto, para suportar utilizações arbitrárias, a extensão de utilização da chave estendida utiliza OIDs em vez de um bitfield. Ao analisar uma extensão de Utilização de Chave Estendida no NetX Secure X.509, um inteiro que representa o OID é fornecido pela aplicação – o serviço *nx_secure_x509_extended_key_usage_extension_parse* irá então devolver se o OID está presente. Uma lista completa de OIDs suportados para utilização de chave estendida é fornecida na referência API para *nx_secure_x509_extended_key_usage_extension_parse* na página 175. Para uma descrição mais completa dos OIDs e seus significados, consulte RFC 5280, secção 4.2.1.12.

### <a name="x509-crl-revocation-status-checking"></a>Verificação do estado de revogação de X.509 CRL

A X.509 fornece um mecanismo chamado *Lista de Revogação* de Certificados (CRL) que permite a uma autoridade de assinatura de certificado digital revogar a validade dos certificados que assinou. Qualquer pedido que precise de verificar os certificados de uma autoridade de assinatura pode obter um CRL e comparar quaisquer certificados assinados por essa autoridade (emitente) contra o CRL para ver se tiveram o seu estatuto revogado por alguma razão (como chave privada comprometida). Desta forma, o pedido pode evitar a utilização de certificados potencialmente perigosos que passam outros controlos de validação de certificados.

A obtenção de um CRL é feita através de uma aplicação, descarregando a lista codificada de DER a partir de um servidor pré-definido ou através de outros meios. A configuração real varia de emitente para emitente, pelo que o NetX Secure não fornece um mecanismo para a obtenção de CRLs, mas fornece uma rotina para verificar um certificado contra um CRL, **nx_secure_x509_crl_revocation_check**.

A API leva um CRL codificado pelo DER, uma loja de certificados (como a de uma sessão de TLS) para verificar e o certificado a ser verificado. A rotina primeiro valida o próprio CRL contra a loja fidedigna (parte da loja de certificados fornecida pela aplicação). Isto é importante para proteger contra os CRLs fraudulentos que estão a ser utilizados para ataques de negação de serviço e estabelece que o CRL é, na verdade, do emitente adequado. Após a validação do CRL, o emitente é verificado – se o emitente do CRL não corresponder ao emitente do certificado, então o CRL não é válido para esse certificado e um erro é devolvido. Cabe à aplicação determinar se o aperto de mão TLS pode continuar neste momento. Se os emitentes corresponderem, então o CRL é procurado pelo número de série do certificado que está a ser validado. Se o número de série estiver presente na lista, é devolvido um erro que indique que o certificado foi revogado. Se não for encontrado fósforo, NX_SUCCESS é devolvido.

## <a name="client-certificate-authentication-in-netx-secure-tls"></a>Autenticação de Certificado de Cliente em NetX Secure TLS

Ao utilizar a autenticação do certificado X.509, o protocolo TLS exige que a instância do Servidor TLS forneça um certificado de identificação, mas por padrão a instância do Cliente TLS não necessita de fornecer um certificado de autenticação, utilizando outra forma de autenticação em vez disso (por exemplo, um nome de utilizador/combinação de palavra-passe). Isto corresponde ao uso mais comum de TLS na Internet para web sites. Por exemplo, um site de retalho online deve provar a um potencial cliente usando um navegador web que o servidor é legítimo, mas o utilizador usará um login/senha para aceder a uma conta específica.

No entanto, o caso padrão nem sempre é desejável, pelo que o TLS permite opcionalmente que a instância do Servidor TLS solicite um certificado ao Cliente remoto. Quando esta funcionalidade estiver ativada, o Servidor TLS enviará uma mensagem CertificateRequest ao Cliente TLS durante o aperto de mão. O Cliente deve responder com um certificado próprio e uma mensagem CertificateVerify que contenha um símbolo criptográfico que comprove que o Cliente é dono da chave privada correspondente associada a esse certificado. Se a verificação falhar ou o certificado não estiver ligado a um certificado de confiança no Servidor, o aperto de mão TLS falha.

Existem dois casos distintos de Autenticação de Certificado de Cliente em TLS – as seguintes secções cobrem ambos os casos.

### <a name="client-certificate-authentication-for-tls-clients"></a>Autenticação de Certificado de Cliente para Clientes TLS

Um Cliente TLS pode tentar uma ligação a um servidor que solicite um certificado para autenticação do cliente. Neste caso, o Cliente deve fornecer um certificado ao servidor e verificar se é dono da chave privada correspondente ou o Servidor terminará o aperto de mão TLS.

No NetX Secure TLS, não existe uma configuração especial para suportar esta funcionalidade, mas a aplicação terá de fornecer um certificado de identificação local para a instância do Cliente TLS utilizando o serviço *nx_secure_tls_local_certificate_add.* Se nenhum certificado for fornecido pela aplicação, mas o servidor remoto estiver a utilizar a Autenticação do Certificado de Cliente e solicitar um certificado, o aperto de mão TLS falhará. O certificado fornecido à Sessão TLS com *nx_secure_tls_local_certificate_add* deve ser reconhecido pelo servidor remoto para completar o aperto de mão TLS.

### <a name="client-certificate-authentication-for-tls-servers"></a>Autenticação de Certificado de Cliente para Servidores TLS

O caso do Servidor TLS para autenticação de certificado de cliente é ligeiramente mais complexo do que o caso do Cliente TLS devido à funcionalidade ser opcional. Neste caso, o Servidor TLS precisa de solicitar especificamente um certificado ao cliente TLS remoto, em seguida, processar a mensagem CertificateVerify para verificar se o Cliente remoto possui a chave privada correspondente, e então o Servidor deve verificar se o certificado fornecido pelo Cliente pode ser rastreado a um certificado na loja de certificados de confiança local.

Nas instâncias do Servidor NetX Secure TLS, a autenticação do certificado de cliente é controlada por <br>
o *cliente de sessão de <span class="underline"> _</span> sessão <span class="underline">_</span><span class="underline"> _</span> nx secure <span class="underline">_</span>tls <span class="underline"> _</span> verificar <span class="underline">_</span>ativar* e<br>
*nx <span class="underline"> _</span> <span class="underline">_ secure</span>tls <span class="underline"> _</span> cliente <span class="underline">_</span><span class="underline"> _</span> verificar <span class="underline">_</span>serviços de desativação.*

Para ativar a Autenticação do Certificado de Cliente, uma aplicação deve ligar<br>
*NX <span class="underline"> _</span> <span class="underline">_ secure</span>tls <span class="underline"> _</span> cliente <span class="underline">_</span><span class="underline"> _</span> verifique <span class="underline">_</span>ativar* com a instância de sessão do TLS Server antes de ligar *nx_secure_tls_session_start*. Note que ligar para este serviço numa Sessão TLS que é usada para ligações ao cliente TLS não terá qualquer efeito.

Quando a autenticação do Certificado de Cliente estiver ativada, o Servidor TLS solicitará um certificado ao cliente TLS remoto durante o aperto de mão TLS. No NetX Secure TLS Server, o certificado Cliente é verificado contra a loja de certificados fidedignos criados com *nx <span class="underline"> _</span> secure_tls <span class="underline">_</span><span class="underline"> _</span> adicionar certificado <span class="underline">_</span>fidedignos* após a cadeia de emitentes X.509. O Cliente remoto deve fornecer uma cadeia que ligue o seu certificado de identidade a um certificado na loja fidedigna ou o aperto de mão TLS falhará. Além disso, se o processamento de mensagem CertificateVerify falhar, o aperto de mão TLS também falhará.

Os métodos de assinatura utilizados para o método CertificadoVerify são fixados para a versão 1.0 e TLS da versão 1.1 e são especificados pelo Servidor TLS na versão 1.2 do TLS. Para o TLS 1.2, os métodos de assinatura suportados geralmente seguem os métodos relevantes fornecidos na tabela do método criptográfico, mas tipicamente RSA com SHA-256 (ver a secção "Criptografia em NetX Secure TLS" para obter mais informações sobre a inicialização de TLS com métodos criptográficos).

## <a name="cryptography-in-netx-secure-tls"></a>Criptografia em NetX Secure TLS

O TLS define um protocolo no qual a criptografia pode ser usada para garantir comunicações de rede. Como tal, deixa a criptografia real a ser usada bastante aberta para os utilizadores de TLS. A especificação requer apenas uma única cifrasuita a ser implementada – no caso do TLS 1.2, essa cifrasuite é TLS_RSA_WITH_AES_128_CBC_SHA, indicando a utilização de RSA para operações de chave pública, AES no modo CBC com teclas de 128 bits para encriptação de sessão, e SHA-1 para a autenticação de mensagens.

Sendo TLS 1.2 conforme, o NetX Secure permite a TLS_RSA_WITH_AES_128_CBC_SHA cifra por padrão, mas dado o número de possíveis implementações para cada um dos métodos criptográficos devido a capacidades de hardware e outras considerações, o NetX Secure fornece uma API criptográfica genérica que permite ao utilizador especificar quais os métodos criptográficos a utilizar com TLS.

NOTA: O mecanismo genérico de API criptográfico também permite que os utilizadores implementem os seus próprios cifrasuites, mas isso é recomendado para utilizadores avançados que estejam familiarizados com os cifrasuites e extensões TLS. Por favor contacte o seu representante da Express Logic se estiver interessado em apoiar os seus próprios cifrasuites.

### <a name="cryptographic-methods"></a>Métodos Criptográficos

NetX Secure TLS implementa DES, 3DES, AES, MD5, HMAC-MD5, SHA-1, HMAC-SHA1, SHA-256, HMAC-SHA256, RSA e ECC (curvas selecionadas) em software com controladores de hardware para determinadas plataformas de hardware. Uma aplicação pode utilizar as rotinas criptográficas fornecidas com o NetX Secure, ou utilizar rotinas personalizadas fornecidas pelo utilizador final ou terceiros.

O *NX_CRYPTO_METHOD* é um bloco de controlo projetado para uma aplicação para descrever uma implementação particular de um algoritmo criptográfico a ser usado com NetX Secure TLS. Com o *NX_CRYPTO_METHOD,* uma aplicação pode facilmente integrar a sua própria implementação de cripto no NetX Secure. A estrutura *NX_CRYPTO_METHOD* é declarada como:

```C
typedef struct NX_CRYPTO_METHOD_STRUCT
{
    /* Symbolic name of the algorithm. */
    USHORT nx_crypto_algorithm;

    /* Size of the key, in bits. */
    USHORT nx_crypto_key_size_in_bits;

    /* Size of the IV block, in bits, used for encryption. */
    USHORT nx_crypto_IV_size_in_bits;

    /* Size of the ICV block, in bits, used for authentication. */
    USHORT nx_crypto_ICV_size_in_bits;

    /* Size of the crypto block, in bytes. */
    ULONG nx_crypto_block_size_in_bytes;

    /* Size of the metadata area. */
    ULONG nx_crypto_metadata_size;

    /* nx_crypto_init function initializes the crypto method with the
        "secret key" or other state  information. The initialization 
        routine should return a handle to the caller.  This handle is 
        used in subsequent crypto operations to identify the session.  
        */

    UINT (*nx_crypto_init) (NX_CRYPTO_METHOD     *method,
                            UCHAR               *key, 
                            NX_CRYPTO_KEY_SIZE   key_size_in_bits,
                            VOID               **handler,
                            VOID                *crypto_metadata,
                            VOID                 crypto_metadata_size);

    /* NetX Secure calls the nx_crypto_cleanup routine when a TLS
       session is to be deleted (or updated).  Resources allocated 
       during the crypto operation should be released in this routine.  
       */
    UINT (*nx_crypto_cleanup) (VOID *handler);

    /* nx_crypto_operation is the actual crypto or hash operation. Note 
       that both input and output buffers are prepared by the caller. 
       For encryption or decryption operations, the crypto operation 
       routine uses the output buffer for encrypted or decrypted data. 
       For authentication operations, the authentication routine shall 
       use the output buffer for the digest. */
    UINT (*nx_crypto_operation)(UINT  op, 
                  VOID              *handler, 
                  NX_CRYPTO_METHOD  *method,
                  UCHAR             *key,
                  NX_CRYPTO_KEY_SIZE key_size_in_bits,
                  UCHAR             *input,
                  ULONG              input_length_in_byte,
                  UCHAR             *iv_ptr,
                  UCHAR             *output,
                  ULONG              output_length_in_byte,
                  VOID              *crypto_metadata,
                  VOID               crypto_metadata_size,
                  NX_PACKET*         packet_ptr,
                  VOID (*nx_crypto_hw_process_callback(NX_PACKET 
                                                       *packet_ptr, 
                                                        UINT status);
} NX_CRYPTO_METHOD;
```

Abaixo está a descrição de cada elemento na estrutura *NX_CRYPTO_METHOD:*

- nx_crypto_algorithm: Este campo identifica o algoritmo descrito no *método* variável Alguns valores válidos para NetX Secure TLS são os seguintes (consulte nx_crypto_const.h para valores específicos):
    
  - NX_CRYPTO_NONE    
  - NX_CRYPTO_ENCRYPTION_NULL    
  - NX_CRYPTO_ENCRYPTION_AES_CBC    
  - NX_CRYPTO_AUTHENTICATION_NONE    
  - TLS_HASH_SHA_1    
  - TLS_HASH_SHA_256    
  - TLS_HASH_MD5    
  - TLS_CIPHER_RSA    
  - TLS_CIPHER_NULL

- nx_crypto_key_size_in_bits: este campo especifica o tamanho da chave secreta utilizada pelo método.

- nx_crypto_IV_size_in_bits: este campo especifica o tamanho do Vetor de Inicialização (IV). Note que na maioria dos casos o bloco IV é usado apenas para algoritmos de encriptação/desencriptação. Os algoritmos de autenticação e verificação raramente utilizam este campo.

- nx_crypto_ICV_size_in_bits: este campo especifica o tamanho do bloco Integrity Check Value (ICV). NOTA: Este bloco destina-se à utilização do IPsec e não é utilizado em TLS. Consulte o NetX Duo IPsec para obter mais informações.

- nx_crypto_block_size_in_bytes: este campo especifica o tamanho do bloco de algoritmo criptográfico para cifras baseadas em blocos, em bytes. Na maioria dos casos, este é usado por rotinas de encriptação e raramente por rotinas de autenticação.

- nx_crypto_metadata_area_size: este campo especifica o tamanho da área de metadados que este método requer. Cada implementação pode exigir que determinada memória armazene as suas informações estatais, ou para armazenar dados intermédios (como material de transformação chave), ou para usar como uma área de risco. A quantidade de espaço exigida por uma implementação é especificada neste campo. A aplicação fornece o espaço de memória ao criar uma sessão TLS. A função criptográfica é responsável pela gestão desta área de metadados.

- nx_crypto_init: Esta é a função de inicialização para o algoritmo criptográfico. Para uma implementação que não necessita de uma rotina de inicialização, este campo pode ser definido para NX_NULL. Um uso típico de uma função de inicialização é inicializar a estrutura interna de dados para o algoritmo. O NetX Secure TLS lidará com a inicialização da rotina criptográfica, chamando esta função internamente.

O protótipo para a função de inicialização é:

```C
UINT crypto_init_function(NX_CRYPTO_METHOD *method, 
                          UCHAR *key, 
                          UINT  key_size_in_bits, 
                          VOID  **handle, 
                          VOID  *crypto_metadata_area, 
                          ULONG crypto_metadata_area_size);
```

  - método é um ponteiro para o bloco de controlo do método cripto.

  - chave é a chave secreta para o processamento dos pacotes de dados.

  - key_size_in_bits define o tamanho da chave secreta, em pedaços.

  - handle é um item definido pela implementação que identifica uma sessão de cripto particular. O valor é gerado pela rotina de inicialização, e é passado de volta para o chamador. A operação de cripto subsequente ou a limpeza da rotina utilizam esta pega para identificar a sessão.

  - crypto_metadata é um ponteiro para a área de metadados necessária pela implementação deste algoritmo. Para algoritmos que não necessitam de uma área de metadados, este campo está definido para NX_NULL e a rotina de inicialização não deve aceder à área dos metadados.

  - crypto_metadata_size especifica o tamanho da área dos metadados. Para sas criados sem área de metadados, este campo está definido para zero, e a rotina de inicialização não deve aceder à área dos metadados.

  - Esta rotina regressará *NX_SUCCESS* se o processo de inicialização for bem sucedido. O chamador trata qualquer outro valor de retorno como falha.

- nx_crypto_cleanup: Esta é a rotina de limpeza definida para a implementação de um algoritmo cripto. É invocado quando uma sessão de TLS é eliminada ou reiniciada.

O protótipo para a função de limpeza é:

```C
UINT crypto_cleanup_function(VOID *handle);
```
- o cabo é passado para a função de limpeza pelo chamador. O cabo é inicializado pela rotina de inicialização criptográfica e usado para identificar o estado do algoritmo criptográfico.

- Esta rotina deve voltar *NX_SUCCESS* se o processo de limpeza for bem sucedido. O chamador trata qualquer outro valor de retorno como falha.

- nx_crypto_operation: Esta é a rotina que executa os serviços reais de encriptação, desencriptação e autenticação. O protótipo de função da rotina de funcionamento é:

```C
UINT crypto_operation_function(UINT   op,
          VOID  *handle,  
          NX_CRYPTO_METHOD* method,
          UCHAR *key,
          UCHAR  key_size_in_bits,
          UCHAR* input,
          ULONG  input_length_in_byte,
          UCHAR* iv_ptr,
          UCHAR* output,
          ULONG  output_length_in_byte,
          VOID *crypto_metadata,
          ULONG crypto_metadata_size,
          NX_PACKET *packet_ptr,
          VOID (*nx_crypto_hw_process_callback)(NX_PACKET 
                          *packet_ptr, UINT status));
```

- op indica o tipo de operação que esta rotina deve ser realizada. Valores válidos são:
    
    - NX_CRYPTO_ENCRYPT
    - NX_CRYPTO_DECRYPT
    - NX_CRYPTO_AUTHENTICATE
    - NX_CRYPTO_VERIFY

- a pega é passada para a função de funcionamento pelo chamador. É gerado pela rotina de inicialização cripto.
- método aponta para o bloco de controlo do método cripto
- pontos-chave para a chave secreta usada para esta operação
- key_size_in_bits é o tamanho da chave secreta em pedaços
- a entrada é um ponteiro para o início da mensagem a operar.
- input_length_in_byte é passado pelo chamador para indicar o tamanho da mensagem a ser operada.
- iv_ptr é configurado pelo chamador para apontar para o início de um bloco IV. Note que a memória do bloco IV é fornecida pelo autor da chamada. Para encriptação, a função de funcionamento deve escrever as informações IV neste bloco de memória; para a desencriptação, a função de funcionamento deve recuperar a informação IV deste bloco de memória. Os algoritmos para a operação de autenticação e verificação normalmente não utilizam o vetor de inicialização.
- a saída é configurada pelo chamador para apontar para um tampão de saída. Note que a memória do tampão de saída é fornecida pelo autor da chamada. Para encriptação, a função de funcionamento deve escrever o texto da cifra no tampão de saída; para a desencriptação, a operação deve escrever o texto decifrado (texto claro) para o tampão de saída; para a autenticação, o valor do haxixe deve ser escrito ao tampão de saída. Para verificação, o tampão de saída é utilizado para armazenar informações sobre haxixe.
- output_length_in_byte indica o tamanho do tampão de saída
- crypto_metadata aponta para a área de metadados a utilizar por esta operação cripto. A área dos metodos criptografados é tipicamente inicializada por crypto_init_function.
- crypto_metadata_size indica o tamanho da área dos metadados.
- Esta rotina deve voltar *NX_SUCCESS* se o processo de funcionamento for bem sucedido. O chamador trata qualquer outro valor de retorno como falha.
- packet_ptr: O pacote que contém os dados que estão a ser tratados. NOTA: Este parâmetro não é utilizado pelo TLS e deve ser definido para NX_NULL.
- nx_crypto_hw_process_callback: Uma função de retorno fornecida pelo método de encriptação. Isto é usado se a função cripto é fornecida por hardware e requer uma rotina de retorno.

O NetX Secure TLS fornece os seguintes métodos de encriptação:

- *AES*  
- *RSA*  
- *NULO*

NetX Secure TLS fornece os seguintes métodos de autenticação:

- *HMAC-MD5*  
- *HMAC-SHA1*  
- *HMAC-SHA256*

Os exemplos a seguir ilustram como configurar a estrutura *NX_CRYPTO_METHOD* para utilizar os métodos de encriptação e autenticação fornecidos pelo NetX Duo IPsec.

***AES:***

```C
/* AES-CBC 128. */
NX_CRYPTO_METHOD crypto_method_aes_cbc_128 = 
{
    /* AES crypto algorithm                             */
    NX_CRYPTO_ENCRYPTION_AES_CBC,                       

    /* Key size in bits. For AES-128 this value is 128  */
    NX_CRYPTO_AES_128_KEY_LEN_IN_BITS,              
   
    /* IV size in bits.  For AES-128 this value is 128  */
    NX_CRYPTO_AES_IV_LEN_IN_BITS,

    /* ICV size in bits, not used.                      */
    0,                                              

    /* Block size in bytes.  For AES this value is 16   */
    (NX_CRYPTO_AES_BLOCK_SIZE_IN_BITS >> 3),        

    /* Metadata size in bytes, for AES this value is 262*/
    sizeof(NX_CRYPTO_AES),              

    /* AES-CBC initialization routine.                  */
    _nx_secure_crypto_method_aes_init,               

    /* AES-CBC cleanup routine, not used.               */
    NX_NULL,                                        

    /* AES-CBC operation                                */
    _nx_secure_crypto_method_aes_operation           
};

/* RSA. */
NX_CRYPTO_METHOD crypto_method_rsa = 
{
    /* RSA crypto algorithm                             */
    TLS_CIPHER_RSA,                       

    /* Key size. RSA key sizes vary, so set to 0.         */
    0,              
   
    /* IV size in bits.  RSA does not use an IV.         */
    0,

    /* ICV size in bits, not used.                      */
    0,                                              

    /* Block size in bytes.  RSA does not have a block size. */
    0,        

    /* Metadata size in bytes, for RSA use the control block. */
    sizeof(NX_CRYPTO_RSA),              

    /* RSA initialization routine.                  */
    _nx_secure_crypto_method_rsa_init,               

    /* Cleanup routine, not used.                    */
    NX_NULL,                                        

    /* RSA operation                                */
    _nx_secure_crypto_method_rsa_operation           

};
```
***NULO***

```C
/* NULL encryption method. */
NX_CRYPTO_METHOD crypto_method_null = 
{
    NX_CRYPTO_ENCRYPTION_NULL,/* Name of the crypto algorithm  */
    0,                        /* Key size in bits, not used    */
    0,                        /* IV size in bits, not used     */
    0,                        /* ICV size in bits, not used    */
    4,                        /* Block size in bytes           */
    0,                        /* Metadata size in bytes        */
    NX_NULL,                  /* Initialization routine,unused */
    NX_NULL,                  /* Cleanup routine, not used     */
    _nx_secure_crypto_method_null_operation  /* NULL operation  
*/
}; 
```
***HMAC-SHA1***
```C
NX_CRYPTO_METHOD crypto_method_hmac_sha1 = 
{
    /* HMAC SHA1 algorithm                               */
    TLS_HASH_SHA1,            


    /* Key size in bits. For HMAC-SHA1 this value is 160 */ 
    NX_CRYPTO_HMAC_SHA1_KEY_LEN_IN_BITS,              

    /* IV size in bits, not used                         */
    0,                                            

    /* Transmitted ICV size in bits. Unused.             */
    0, 

    /* Block size in bytes, not used                     */
    0,                                            

    /* Metadata size in bytes                            */
    sizeof(NX_SHA1_HMAC),                                            

    /* Initialization routine, not used                  */
    NX_NULL,                                      

    /* Cleanup routine, not used                         */
    NX_NULL,                                          

    /* HMAC SHA1 operation                               */
    _nx_secure_crypto_method_hmac_sha1_operation   
};
```
***NENHUMA***

Um método especial **NX_CRYPTO_NONE** é utilizado para sinalizar o módulo IPsec de que a encriptação ou o serviço de autenticação não são necessários. Está configurado da seguinte forma:

```C
/* NX_CRYPTO_NONE means encryption or authentication
   method is not needed.  */
NX_CRYPTO_METHOD crypto_method_none = 
{
    NX_CRYPTO_NONE,       /* Name of the crypto algorithm */
    0,                    /* Key size in bits, not used   */
    0,                    /* IV size in bits, not used    */
    0,                    /* ICV size in bits, not used   */
    0,                    /* Block size in bytes          */
    0,                    /* Metadata size in bytes       */
    NX_NULL,              /* Initialization routine, not used */
    NX_NULL,              /* Cleanup routine, not used    */
    NX_NULL               /* NULL operation               */
};                                               
```
### <a name="initializing-tls-with-cryptographic-methods"></a>Inicialização de TLS com Métodos Criptográficos

Depois de ter criado as suas rotinas criptográficas em conformidade com as assinaturas do método criptográfico descritas na secção anterior, terá de as passar para o TLS quando rubricar um NX_SECURE_TLS_SESSION bloco de controlo. Isto é feito no serviço TLS nx_secure_tls_session_create:

```C
UINT  nx_secure_tls_session_create(
              NX_SECURE_TLS_SESSION*     session_ptr,
              const NX_SECURE_TLS_CRYPTO*    tls_cipher_table,
              VOID*                encryption_metadata_area,
              ULONG                 encryption_metadata_size
);
```
- session_pointer é um ponteiro para o seu NX_SECURE_TLS_SESSION bloco de controlo.
- tls_cipher_table é um ponteiro para um bloco de controlo NX_SECURE_TLS_CRYPTO, descrito abaixo.
- encryption_metadata_area aponta para o espaço utilizado pelas rotinas criptográficas em TLS.
- encryption_metadata_size é o tamanho da área de metadados em bytes.

### <a name="elliptic-curve-cryptography-ecc-in-netx-secure-tls"></a>Criptografia da curva elíptica (ECC) em NetX Secure TLS

A Criptografia da Curva Elíptica (ECC) fornece um esquema de criptografia de chave pública que pode ser usado em vez de RSA. O ECC é tipicamente mais rápido e utiliza chaves menores do que a RSA para que possa ser uma opção valiosa para TLS incorporado. Nas versões X-Ware antes do Azure RTOS 6.0, o ECC foi enviado como um complemento, exigindo a instalação do código fonte ECC no seu projeto. Azure RTOS 6.0 integrado ECC na base de código principal para que a instalação dos ficheiros ECC não seja mais necessária. No entanto, o ECC ainda requer a mesma inicialização que as versões anteriores.

### <a name="supported-ecc-curves"></a>Curvas ECC suportadas

O NetX Secure implementa partes das curvas de acordo com <http://www.secg.org/sec2-v2.pdf> . As curvas de acontenção são suportadas<sup>18</sup>:

  - secp256r1 
  - secp384r1 
  - secp521r1 

Se forem utilizadas outras curvas ECC, a rotina *de nx_secure_tls_session_start()* devolverá o erro NX_SECURE_TLS_NO_SUPPORTED_CIPHERS indicando que foram utilizadas curvas não apoiadas.

Note que a cadeia de certificados TLS também pode ser encriptada por algoritmos ECC. Mesmo que as curvas fornecidas pelo Cliente TLS sejam suportadas, é possível que a curva ECC utilizada na cadeia de certificados não seja suportada. Neste caso, *nx_secure_tls_session_start* rotina regressa NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER.

Um exemplo de tabela cifrassuita padrão para ECC é fornecido em nx_crypto_generic_ciphersuites.c. Consulte a secção "Tabela de Cifra Criptográfica TLS" para obter mais informações sobre tabelas de cifrasuite.

18. Note-se que as implementações para as curvas secp192r1 e secp224r1 também estão previstas para aplicações antigas. No entanto, estas curvas são agora consideradas fracas e NÃO DEVEM ser utilizadas para o desenvolvimento de novas aplicações.

### <a name="crypto-methods-for-ecc"></a>Métodos Cripto para ECC

Métodos cripto para grupos de curvas elípticas:

- NX_CRYPTO_METHOD crypto_method_ec_secp192<sup>15;</sup>  
- NX_CRYPTO_METHOD crypto_method_ec_secp224<sup>15;</sup>  
- NX_CRYPTO_METHOD crypto_method_ec_secp256;  
- NX_CRYPTO_METHOD crypto_method_ec_secp384;  
- NX_CRYPTO_METHOD crypto_method_ec_secp521;

Os métodos cripto para curvas ECC são definidos em nx_crypto_generic_ciphersuites.c.

Método cripto para ECDHE:

- NX_CRYPTO_METHOD crypto_method_ecdhe;

Método cripto para ECDSA:

- NX_CRYPTO_METHOD crypto_method_ecdsa;

Os métodos cripto ECDSA e ECDHE são definidos em nx_crypto_generic_ciphersuites.c.

Combinados com outros métodos cripto como RSA, SHA, AES, podem ser usados como blocos de construção para a mesa de procuração cifrasuite.

### <a name="enabling-ecc-support-for-tls"></a>Habilitar o suporte do ECC para o TLS

O ECC é ativado por padrão para TLS. Para desativar o suporte do ECC, o símbolo NX_SECURE_DISABLE_ECC_CIPHERSUITE deve ser definido.

Para que a alteração produza efeitos, terá de reconstruir a Biblioteca NetX Secure e todas as aplicações que utilizem essa biblioteca.

No código de aplicação, a API n *x_secure_tls_ecc_initialize()* deve ser chamada após a criação da sessão TLS. Esta API notifica a sessão TLS do tipo de curvas a utilizar para operações de troca de chaves TLS e verificação de certificados. Durante a fase de aperto de mão TLS, se um algoritmo ECC for selecionado, o cliente e o servidor trocam parâmetros relacionados com a curva ECC para decidir qual a curva a utilizar.

O seguinte segmento de código ilustra como utilizar a API. Note que os argumentos *(nx_crypto_ecc_supported_groups, nx_crypto_ecc_supported_groups_size e nx_crypto_ecc_curves)* são todos definidos em *nx_crypto_generic_ciphersuites.c*. Portanto, estes símbolos podem ser utilizados diretamente.

```C
status = nx_secure_tls_ecc_initialize(&tls_session,     
                    nx_crypto_ecc_supported_groups,      
                    nx_crypto_ecc_supported_groups_size,     
                    nx_crypto_ecc_curves);
```
A configuração do exemplo no nx_crypto_generic_ciphersuites.c contém uma tabela de procuração cifrasuita ECC que é usada quando o ECC está ativado. Para utilizar o ECC, basta passar nx_crypto_tls_ciphers_ecc como parâmetro de tabela cifrasuite ao criar sessões de TLS com nx_secure_tls_session_create. A tabela de exemplos contém cifrasuites ECC e não-ECC.

### <a name="tls-cryptographic-cipher-table"></a>TLS Tabela de Cifra Criptográfica

A estrutura NX_SECURE_TLS_CRYPTO é definida como:

```C
typedef struct NX_SECURE_METHODS_STRUCT
{
    /* Table that maps ciphersuites to crypto methods. */
    NX_SECURE_TLS_CIPHERSUITE_INFO* nx_secure_tls_ciphersuite_lookup_table;
    USHORT nx_secure_tls_ciphersuite_lookup_table_size;

    /* Table that maps X.509 cipher identifiers to crypto methods. */
    NX_SECURE_X509_CRYPTO *nx_secure_tls_x509_cipher_table;
    USHORT nx_secure_tls_x509_cipher_table_size;

    /* Specific routines needed for specific TLS versions. */
#if (NX_SECURE_TLS_TLS_1_0_ENABLED || NX_SECURE_TLS_TLS_1_1_ENABLED)
    NX_CRYPTO_METHOD *nx_secure_tls_handshake_hash_md5_method;
    NX_CRYPTO_METHOD *nx_secure_tls_handshake_hash_sha1_method;
    NX_CRYPTO_METHOD *nx_secure_tls_prf_1_method;
#endif

#if (NX_SECURE_TLS_TLS_1_2_ENABLED)
    NX_CRYPTO_METHOD *nx_secure_tls_handshake_hash_sha256_method;
    NX_CRYPTO_METHOD *nx_secure_tls_prf_sha256_method;
#endif

#if (NX_SECURE_TLS_TLS_1_3_ENABLED)
    const NX_CRYPTO_METHOD *nx_secure_tls_hkdf_method;
    const NX_CRYPTO_METHOD *nx_secure_tls_hmac_method;
    const NX_CRYPTO_METHOD *nx_secure_tls_ecdhe_method;
#endif

} NX_SECURE_TLS_CRYPTO;
```
A tabela é criada preenchendo as entradas para esta estrutura numa constante estática localizada dentro do projeto NetX Secure TLS, normalmente localizado com as rotinas criptográficas e módulos.

Como exemplo, a biblioteca criptográfica apenas de software ("genérico") fornecida com NetX Secure contém a seguinte definição de tabela (para suporte cifrasuita não-ECC<sup>19</sup>):

```C
/* Define the cipher table object we can pass into TLS. */
const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers =
{
    /* TLS Ciphersuite lookup table and size. */
    _nx_crypto_ciphersuite_lookup_table,
    sizeof(_nx_crypto_ciphersuite_lookup_table) / 
    sizeof(NX_SECURE_TLS_CIPHERSUITE_INFO),

    /* X.509 certificate cipher table and size. */
    _nx_crypto_x509_cipher_lookup_table,
    sizeof(_nx_crypto_x509_cipher_lookup_table) / sizeof(NX_SECURE_X509_CRYPTO),

    /* TLS version-specific methods. */
#if (NX_SECURE_TLS_TLS_1_0_ENABLED || NX_SECURE_TLS_TLS_1_1_ENABLED)
    &crypto_method_md5,
    &crypto_method_sha1,
    &crypto_method_tls_prf_1,
#endif

#if (NX_SECURE_TLS_TLS_1_2_ENABLED)
    &crypto_method_sha256,
    &crypto_method_tls_prf_sha_256
#endif

#if (NX_SECURE_TLS_TLS_1_3_ENABLED)
    &crypto_method_hkdf,
    &crypto_method_hmac,
    &crypto_method_ecdhe,
#endif
};
```
Na estrutura, a primeira entrada é a tabela cifrasumita TLS. A estrutura NX_SECURE_TLS_CIPHERSUITE_INFO mapeia rotinas criptográficas (sob a forma de ponteiros de NX_CRYPTO_METHOD) a cifrasuites específicos, tal como definidos nas especificações do TLS. O segundo valor é o número de entradas na tabela apontadas para o primeiro campo.

O campo seguinte aponta para uma tabela de rotinas usadas por X.509 ao processar certificados digitais e a estrutura NX_SECURE_X509_CRYPTO é semelhante em forma a NX_SECURE_TLS_CIPHERSUITE_INFO. O seguinte campo é o número de entradas na tabela.

Após a tabela de procura são várias rotinas necessárias para versões específicas de TLS. Por exemplo, antes da versão 1.2 do TLS, as rotinas de geração chave e de hashing do aperto de mão foram fixadas para utilizar uma combinação de SHA-1 e MD5 – os métodos para estas rotinas são chamados especificamente na estrutura da cifra, uma vez que não estão ligados a cifrasuites específicas. Na versão TLS 1.2, as rotinas de geração chave e hashing são escolhidas pela cifrasuite, mas para cifrasuites que não especificam as rotinas a utilizar, o método de haxixe SHA-256 é usado, e a estrutura da cifra chama essa rotina especificamente.

TLS 1.3 requer algumas cifras específicas extra para várias operações.

19. Note que o suporte TLS 1.3 requer ECC – utilize nx_crypto_tls_ciphers_ecc se o TLS 1.3 estiver ativado.

### <a name="tls-ciphersuite-lookup-table"></a>Tabela de olhar cifrasumita TLS

Para preencher a tabela de cifras para TLS, também terá de criar uma tabela de procuração cifrasuita que mapeia rotinas criptográficas para identificadores de cifrasuite específicos. Os identificadores são valores registados em IANA que são universais. Consulte os RFCs TLS para obter mais informações. As rotinas representam os 5 métodos separados utilizados em cada cifrasuite (alguns cifrasuites não podem utilizar todos os 5): cifra pública, autenticação de chave pública, cifra de sessão, rotina de haxixe de sessão e Função de Pseudo-Random TLS (PRF). A tabela a seguir explica cada um dos 5 métodos:

| **Categoria de rotina**      | **Descrição**                                                                                       | **Algoritmos de exemplo**                                            |
| ------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| Cifra pública             | Usado para trocar chaves durante o aperto de mão TLS                                                        | RSA, Diffie-Hellman, ECC                                          |
| Autenticação de chaves públicas | Usado para autenticar ou assinar dados durante o aperto de mão TLS                                            | RSA, DSS                                                          |
| Cifra de sessão            | Algoritmo de chave simétrica usado para encriptar dados de aplicações durante a sessão TLS                       | AES                                                          |
| Haxixe de sessão              | Utilizado para preservar a integridade das mensagens durante a sessão TLS (garante que os dados não mudaram) | SHA-1, SHA-256                                                    |
| TLS PRF                   | Usado para gerar material chave e no haxixe de aperto de mão no aperto de mão TLS                          | O PRF baseia-se em rotinas de haxixe - SHA-1 + MD5, SHA-256, SHA-512 |

A estrutura NX_SECURE_TLS_CIPHERSUITE_INFO é definida da seguinte forma:

```C
typedef struct NX_SECURE_TLS_CIPHERSUITE_INFO_struct
{
    /* The IANA value of the ciphersuite as defined by the TLS spec.*/
    USHORT nx_secure_tls_ciphersuite;

    /* The Public Key operation in this suite - RSA or DH. */
    NX_CRYPTO_METHOD *nx_secure_tls_public_cipher;

    /* The Public Authentication method used for signing data. */
    NX_CRYPTO_METHOD *nx_secure_tls_public_auth;

    /* The session cipher being used - AES, RC4, etc. */
    NX_CRYPTO_METHOD *nx_secure_tls_session_cipher;

    /* The size of the initialization vectors for the session cipher (bytes).*/
    USHORT nx_secure_tls_iv_size;

    /* The key size for the session cipher (bytes). */
    UCHAR nx_secure_tls_session_key_size;

    /* The hash being used - MD5, SHA-1, SHA-256, etc. */
    NX_CRYPTO_METHOD *nx_secure_tls_hash;

    /* The size of the hash being used. SHA-1 is 20 bytes, MD5 is 16 bytes.*/
    USHORT nx_secure_tls_hash_size;

    /* The TLS PRF being used – this is only for TLSv1.2. */
    NX_CRYPTO_METHOD *nx_secure_tls_prf;

} NX_SECURE_TLS_CIPHERSUITE_INFO;
```
O campo nx_secure_tls_ciphersuite contém o valor cifrasuita IANA, e os ponteiros NX_CRYPTO_METHOD representam os 5 métodos utilizados por essa cifrasuite. Os valores de escala (nx_secure_tls_iv_size, nx_secure_tls_key_size e nx_secure_tls_hash_size) são informativos, fornecendo informações que podem não estar disponíveis nas entradas NX_CRYPTO_METHOD.

Como exemplo, vamos analisar a cifrasumita padrão para TLS, TLS_RSA_WITH_AES_128_CBC_SHA, que especifica a utilização de RSA, AES-CBC com teclas de 128 bits e SHA-1 para hashing de sessão. Não é especificado nenhum PRF TLS para esta cifrasuite, pelo que no modo TLSv1.2, utilizará o PRF SHA-256 predefinido. Note que todos os cifrasuites utilizam o PRF SHA-1+MD5 em TLS 1.0 e 1.1, independentemente do PRF especificado na tabela.

A entrada na tabela NX_SECURE_TLS_CIPHERSUITE_INFO na biblioteca criptográfica genérica é definida da seguinte forma:

```C
{ 
  TLS_RSA_WITH_AES_128_CBC_SHA,     /* Ciphersuite identifier */
  &crypto_method_rsa,               /* Public-key cipher (NX_CRYPTO_METHOD)*/
  &crypto_method_rsa,               /* Authentication method(NX_CRYPTO_METHOD)*/
  &crypto_method_aes_cbc_128,       /* Session cipher method(NX_CRYPTO_METHOD)*/
  16,                               /* Session cipher IV size in bytes */
  16,                               /* Session cipher key size in bytes */
  &crypto_method_hmac_sha1,         /* Session hash routine(NX_CRYPTO_METHOD) */
  20,                               /* Session hash output size in bytes */
  &crypto_method_tls_prf_sha_256    /* TLSv1.2 PRF */
},
```

Note que para a cifra da sessão o tamanho da chave é determinado pela cifrasuite, mas para os métodos de chave pública o tamanho da chave não é conhecido até que o aperto de mão TLS esteja em andamento uma vez que as chaves públicas estão contidas nos certificados digitais trocados durante o aperto de mão.

### <a name="x509-cipher-lookup-table"></a>X.509 Cipher Lookup Table

Tal como a tabela NX_SECURE_TLS_CIPHERSUITE_INFO, a estrutura NX_SECURE_X509_CRYPTO mapeia rotinas criptográficas a valores conhecidos. No caso de X.509, os identificadores são na verdade OIDs definidos por X.509 e registados nos organismos de normas ISO e UTA. Os OIDs são valores de vários bytes de comprimento variável projetados para identificar de forma única várias informações em várias normas de telecomunicações, incluindo rotinas criptográficas usadas em certificados digitais. Devido ao facto de os OIDs serem de comprimento variável, o NetX Secure TLS mapeia os valores oficiais de OID para constantes de comprimento fixo que são utilizados internamente (ver nx_secure_x509.h). Estas constantes são utilizadas na estrutura NX_SECURE_X509_CRYPTO, que é definida da seguinte forma:

```C
/* Structure to hold X.509 cryptographic routine information. */
typedef struct NX_SECURE_X509_CRYPTO_struct
{
    /* Internal NetX Secure identifier for certificate "ciphersuite" which consists
       of a hash and a public key operation. These can be mapped to OIDs in X.509.
        */
    USHORT nx_secure_x509_crypto_identifier;

    /* Public-Key Cryptographic method used by certificates. */
    NX_CRYPTO_METHOD *nx_secure_x509_public_cipher_method;

    /* Hash method used by certificates. */
    NX_CRYPTO_METHOD *nx_secure_x509_hash_method;
} NX_SECURE_X509_CRYPTO;
```

O primeiro campo, *nx_secure_x509_crypto_identifier,* é a representação OID interna utilizada pelo NetX Secure.

O segundo e terceiro campos apontam para NX_CRYPTO_METHOD objetos que representam os métodos criptográficos identificados pelo OID, uma operação de chave pública emparelhada com uma rotina de haxixe. Note que cada certificado digital pode ter mais de um OID para rotinas criptográficas.

A tabela de métodos para X.509 é construída da mesma forma que a tabela de procuração cifrasuita. Como exemplo, vamos olhar para o OID para RSA_SHA1. O OID real para RSA_SHA1 é o seguinte:

```C
{iso(1) member-body(2) us(840) rsadsi(113549) pkcs(1) pkcs-1(1) sha1-with-rsa-
signature(5)}
```
O OID está representado na sintaxe ASN.1 e tem um valor numérico de 1.2.840.113549.1.1.5. Este valor é então codificado em formato binário, criando os seguintes bytes:

```C
UCHAR RSA_SHA1_OID = { 0x2A, 0x86, 0x48, 0x86, 0xF7, 0x0D, 0x01, 0x01, 0x05 };
```
A conversão real de ASN.1 para o formato binário está fora do âmbito deste documento. Procure codificações ASN.1 para obter mais informações. A representação binária dos OIDs suportados pelo NetX Secure pode ser encontrada no ficheiro *nx_secure_x509.c*.

Uma vez que temos um mapeamento do OID real para uma constante reconhecida internamente, podemos criar uma entrada para RSA_SHA1 na tabela NX_SECURE_X509_CRYPTO:

```C
{ 
    NX_SECURE_TLS_X509_TYPE_RSA_SHA_1,    /* Internal OID constant. */
    &crypto_method_rsa,                   /* RSA method (NX_CRYPTO_METHOD). */ 
    &crypto_method_sha1                   /* SHA-1 method (NX_CRYPTO_METHOD). */
}, 
```
### <a name="default-tls-routines"></a>Rotinas TLS padrão

Como mencionado acima, o TLS requer algumas rotinas padrão para a geração de chaves e verificação de mensagens durante o aperto de mão. A rotina principal é a Função Pseudo-Random TLS, ou PRF. O PRF baseia-se em rotinas de haxixe e pode ser usado para gerar uma quantidade arbitrária de dados pseudoaleatórios<sup>20</sup> para geração chave ou outros fins.

Além do PRF, cada versão do TLS utiliza rotinas de haxixe padrão que também precisam de ser fornecidas. Para as versões TLS 1.0 e 1.1, essas rotinas de haxixe são MD5 e SHA-1. A versão 1.2 do TLS requer apenas SHA-256.

Na estrutura NX_SECURE_TLS_CRYPTO, existem NX_CRYPTO_METHOD ponteiros para MD5, SHA-1, SHA-256, a versão TLS 1.0/1.1 PRF e o TLS padrão TLS 1.2 PRF.

O suporte TLS 1.3 adiciona campos para HKDF (geração-chave), HMAC (para operações específicas de hashing utilizadas durante o aperto de mão) e ECDHE (necessário para a funcionalidade TLS 1.3).

Fornecidas na biblioteca de criptografia de software genérico estão versões de software do TLS PRF. Para TLS 1.0/1.1, esta função chama-se *nx_crypto_tls_prf_1*. Para TLS 1.2, a função chama-se *nx_secure_tls_prf_sha256*. O sufixo "1" representa o legado TLS 1.0 PRF, e o sufixo "sha256" refere-se ao facto de o PRF padrão TLS 1.2 se basear em SHA-256. Quando o suporte para outras rotinas de PRF é necessário, o sufixo para essas rotinas refletirá o método do haxixe utilizado. Uma vez que as rotinas prf são baseadas em métodos de haxixe, as rotinas de haxixe subjacentes podem ser aceleradas independentemente em diferentes plataformas-alvo.

Além das tabelas de cifrasumita tLS e X.509, com as rotinas predefinidas de PRF e haxixe preenchidas na estrutura NX_SECURE_TLS_CRYPTO podem ser povoadas e usadas para inicializar uma sessão de TLS.

20. "Pseudoaleatório" refere-se ao facto de o PRF ser determinista, o que significa que produzirá sempre a mesma saída dada a mesma entrada, mas aleatória no facto de a saída não ser previsível. TLS usa esta propriedade do PRF para gerar as chaves de sessão de vários dados públicos combinados com o segredo mestre trocado durante o aperto de mão usando uma cifra de chave pública como RSA.

### <a name="cryptographic-metadata"></a>Metadados criptográficos

Antes de podermos rubricar a sessão TLS com a tabela NX_SECURE_TLS_CRYPTO, precisamos de alocar espaço tampão para os metadados de rotina criptográfico. Os metadados são utilizados para armazenar todo o estado associado a uma determinada rotina, representada pelo seu bloco de controlo. O campo *nx_crypto_metadata_area_size* de cada NX_CRYPTO_METHOD deve ser definido para o tamanho da estrutura de controlo associada a essa rotina ou a inicialização TLS não terá de prestar contas adequadas ao espaço necessário, possivelmente causando problemas de ultrapassagem do tampão.

Antes da sessão TLS ser criada, o tampão de metadados deve ser atribuído. O tampão é automaticamente dividido por nx_secure_tls_session_create e o espaço é reservado para cada uma das rotinas que são fornecidas na tabela de métodos criptográficos. Note que uma vez que apenas uma cifrasuite está ativa de cada vez numa sessão de TLS, o número de cifrasuites suportados não afeta o espaço de metadados necessário – o espaço é reservado para cada uma das 5 rotinas cifrasuitas utilizando o tamanho máximo do bloco de controlo para essa categoria na tabela de procuração de cifrasuitas.

De forma a facilitar o cálculo do tamanho do tampão de metadados, o serviço *nx_secure_metadata_size_calculate* executa os mesmos cálculos que nx_secure_tls_session_create mas simplesmente devolve o tamanho total do tampão de metadados necessário em bytes.

### <a name="initializing-the-tls-session"></a>Inicialização da sessão TLS

Uma vez criados os objetos NX_CRYPTO_METHOD e NX_SECURE_TLS_CRYPTO e reservados os metadados, podemos rubricar uma sessão de TLS da seguinte forma (valores retirados dos exemplos acima):

```C
/* Pointer to the platform-specific cipher table. */
extern nx_crypto_tls_ciphers;

/* Cryptographic routine metadata buffer. Size is determined by calling 
nx_secure_tls_metadata_size_calculate with the nx_crypto_tls_ciphers table referenced 
above. */
UCHAR crypto_metadata[4500];

/* Initialize our TLS session using our cipher table and metadata area. Note that we can 
use sizeof for the metadata array because the size parameter expects the size in bytes.*/

nx_secure_tls_session_create(
    &tls_session,            /* Pointer to TLS session.      */
    &nx_crypto_tls_ciphers,  /* Pointer to cipher table.     */
    crypto_metadata,         /* Cryptography metadata buffer.*/
    sizeof(crypto_metadata), /* Size of metadata buffer.     */
);
```
