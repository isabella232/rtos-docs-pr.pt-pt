---
title: Capítulo 1 - Introdução ao servidor Azure RTOS NetX Duo DHCPv6
description: Este documento explicará em detalhe como o NetX Duo DHCPv6 Server atribui endereços IPv6 aos Clientes DHCPv6.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6cf7baa91b1804876b97b1d75d1872d1120ad028
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826042"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-dhcpv6-server"></a>Capítulo 1 - Introdução ao servidor Azure RTOS NetX Duo DHCPv6

Nas redes IPv6, o DHCPv6 é necessário para que os Clientes obtenham endereços IPv6. Não substitui o DHCP, que se limita ao IPv4, que não oferece endereços IPv4. O DHCPv6 tem características semelhantes ao DHCP, bem como muitas melhorias. Um Cliente que não utilize ou não possa utilizar o endereço apátrida IPv6 pode usar o DHCPv6 para ser atribuído um endereço IPv6 global único a partir de um Servidor DHCPv6.

A NetX Duo foi desenvolvida para apoiar aplicações baseadas em rede IPv6 e protocolos de rede como o DHCPv6. Este documento explicará em detalhe como o NetX Duo DHCPv6 Server atribui endereços IPv6 aos Clientes DHCPv6.

## <a name="dhcpv6-communication"></a>Comunicação DHCPv6

**Estrutura de mensagem DHCPv6**

O conteúdo da mensagem é basicamente um cabeçalho de mensagem seguido por um ou mais blocos de opções (geralmente mais). Abaixo está a estrutura básica onde cada bloco representa um byte:

![Diagrama mostrando a mensagem DHCPv6 e a estrutura do bloco de opções.](media/image2.jpg)

**Figura 1. Estrutura de bloco de mensagem DHCPv6 e opções**

O campo de Msg-Type de 1 byte indica o tipo de mensagem DHCPv6. O campo de ID de transação de 3 bytes é definido pelo Cliente. Pode por qualquer sequência de caracteres, mas deve ser única para cada mensagem do Cliente para o Servidor (conservada através de mensagens duplicadas enviadas pelo Cliente). O Servidor utiliza esse ID de transação para cada resposta ao Cliente para permitir ao Cliente combinar mensagens do Servidor no caso de pacotes que sejam atrasados ou deixados cair na rede. Seguindo o campo de ID de transação, estão uma ou mais opções DHCPv6 usadas para indicar o que o Cliente está a solicitar.

A estrutura de opção DHCPv6 é composta por um código de opção, um campo de comprimento de opção, que não inclui os campos de comprimento ou código, e, finalmente, os dados de opção em si, que é um ou mais campos de código de opção byte 2 para os dados que o Cliente está solicitando.

Alguns blocos de opções têm opções aninhadas. Por exemplo, uma opção *de Associação de Identidade para Endereço Não Temporário (IANA)* contém uma ou mais opções da Associação de Identidade *(IA)* para solicitar endereços IPv6. A opção *IANA* devolvida na mensagem resposta do servidor contém a mesma opção *IA(s)* com o endereço IPv6 e os tempos de locação concedidos pelo Servidor, bem como uma opção de *Estado* indicando se existe um erro com o pedido de endereço do Cliente.

Uma lista de todos os blocos de opções e a sua descrição é fornecida no **apêndice A**.

**Tipos de mensagens DHCPv6**

Embora o DHCPv6 melhore consideravelmente a funcionalidade do DHCP, utiliza o mesmo número de mensagens que o DHCP e suporta as mesmas opções de fornecedor que o DHCP. A lista de mensagens DHCPv6 é a seguinte:

- SOLICT (1) (enviado pelo Cliente)
- PUBLICIDADE (2) (enviado por Servidor)
- PEDIDO (3) (enviado pelo Cliente)
- RESPOSTA (7) (enviado por Servidor)
- CONFIRMA (4) (enviado pelo Cliente)
- RENOVAÇÃO (5) (enviada pelo Cliente)
- REBIND (6) (enviado pelo Cliente)
- LIBERAÇÃO (8) (enviado pelo Cliente)
- DECLINO (9) (enviado pelo Cliente)
- INFORM_REQUEST (11) (enviado pelo Cliente)
- RECONFIGURE* (10) (enviado por Servidor)

*RECONFIGURE não é suportado pelo NetX Duo DHCPv6 Server.

A sequência básica de pedido DHCPv6, com o equivalente tipo de mensagem DHCPv4 em parênteses, é a seguinte:

Cliente ***Solicit** _ (_Discovery)***Anúncio** do Servidor (* Oferta )***Pedido** de Cliente (Pedido**) **Resposta** do servidor (DHCPAck*)*

**Renovação** do Cliente (mesmo) **Resposta** do Servidor *(DHCPAck)*

## <a name="dhcpv6-message-validation"></a>Validação de mensagens DHCPv6

ID de transação: O Cliente deve gerar um ID de transação para cada mensagem que envia para o Servidor. O Servidor DHCPv6 rejeitará qualquer mensagem do Cliente que não corresponda a este ID de transação. O Servidor, por sua vez, deve utilizar o mesmo ID de transação nas suas respostas de volta ao Cliente.

**Identificadores exclusivos DHCPv6 (DUIDs)**

Todas as mensagens do Servidor também devem incluir um identificador único DHCPv6 (DUID) em cada mensagem ou o Cliente DHCPv6 não deve aceitar a mensagem. Um DuID de Camada de Ligação (LL) é um bloco de controlo que contém endereço MAC do cliente, tipo de hardware e tipo DUID. Um DUID de tempo de ligação (LLT) contém ainda um campo de tempo que diminui as chances de o DUID não ser único na rede de anfitriões. Por esta razão, o RFC 3315 recomenda DUIDs LLT em vez de DUIDs LL. Se a aplicação do anfitrião não criar o seu próprio valor de tempo único, o NetX Duo DHCPv6 fornecerá um padrão. O terceiro tipo de DUID é o DUID da Enterprise (Fornecedor designado) que contém um ID da Empresa registado (como registado no IANA) e dados privados que são variáveis em tipo e comprimento, por exemplo, com base no tamanho da memória, tipo de sistema operativo de outra configuração de hardware. Consulte a lista de Opções de Configuração em outros lugares deste documento para configurar os valores de ID atribuídos e privados do fornecedor do Servidor.

O Cliente também deve incluir o seu DUID nas suas mensagens para o Servidor, exceto para INFORM_REQUEST, ou o Servidor irá rejeitá-los.

**Sessões de servidor de clientes DHCPv6**

DhCPv6 Clientes e Servidores trocam mensagens sobre a UDP. O Cliente utiliza a porta 546 para enviar e receber mensagens DHCPv6 e o Servidor utiliza a porta 547. O Cliente utiliza inicialmente o seu endereço link-local para transmitir e receber mensagens DHCPv6. Envia todas as mensagens para os servidores DHCPv6 utilizando um endereço multicast reservado e com alcance de ligação conhecido como o endereço multicast *All_DHCP_Relay_Agents_and_Servers* *(FF02:01:02)*.

Pedidos de atribuição de endereços ForIPv6, o Servidor DHCPv6 ouve mensagens *Solicit* enviadas para o endereço *All_DHCP_Relay_Agents_and_Servers.* No pedido *de Solicitação,* o Cliente pode solicitar a atribuição de um endereço IPv6 específico ou deixar o Servidor escolher um. Também pode solicitar outras informações de configuração de rede a partir do Servidor.

Se o DHCPv6Server extrair uma mensagem *solicitável* válida e puder atribuir um endereço IPv6 ao Cliente, responde com uma mensagem *de Anúncio* contendo o endereço IPv6 que concederá ao Cliente, o tempo de locação de endereços IPv6 e qualquer informação adicional solicitada pelo Cliente. Se o Cliente aceitar a oferta do Servidor, responde com uma mensagem *de Pedido,* informando o Servidor de que aceitará o endereço IPv6. O Servidor confirma que o Cliente está ligado ao endereço IPv6 com uma mensagem *de Resposta.*

Se a mensagem DHCPv6 do Cliente for inválida, o Servidor descartará a mensagem silenciosamente. Se o Servidor não conseguir conceder o pedido, enviará uma mensagem *de resposta* com uma indicação do problema no campo de estado da opção IP address IANA. Se forem recebidos pedidos duplicados do Cliente, o Servidor reensifica a resposta anterior do DHCPv6, assumindo que o Cliente simplesmente não recebeu o pacote.

Cabe ao Cliente verificar se o endereço IPv6 atribuído a partir do Servidor não é atribuído a outro anfitrião no sistema utilizando vários protocolos IPv6, como duplicado de deteção de endereços. Se o endereço não for único, o Cliente enviará ao Servidor uma mensagem *De declínio.* O Servidor atualiza a sua tabela de locação IP com esta informação, registando que o endereço já está atribuído. Entretanto, o Cliente deve reiniciar o processo de pedido dhcpv6 com outra mensagem *Solicit.*

Além de um endereço IPv6, um Cliente provavelmente também precisará de conhecer o servidor DNS e possivelmente outras informações de rede, como o nome de domínio da rede. O DHCPv6 fornece os meios para solicitar estas informações utilizando quer a utilização de Pedidos de Opção nas mensagens *Solicite* e *Solicite,* quer separadamente em mensagens *de Pedido de Informação.* As opções DHCPv6 são explicadas mais tarde neste capítulo.

**Duração do arrendamento IPv6**

Quando o Servidor concede um endereço IPv6 a um Cliente, também atribui a duração do arrendamento (vitalícia)na opção IANA para quando recomenda ao Cliente que comece a renovar (T1) ou a reencambinar (T2) o seu endereço IPv6 utilizando mensagens *Renovar* e *Rebind.* A diferença entre os dois é que o Cliente direciona a mensagem *Renovar* para o Servidor, incluindo o Servidor DUID no pedido *de Renovação.* No entanto, não especifica nenhum servidor e, portanto, não inclui um DUID do Servidor, na mensagem *Rebind* para o endereço *All_DHCP_Relay_Agents_and_Servers.* A opção IA que contém o endereço real IPv6 que o Servidor concede ao Cliente também contém as vidas preferidas e válidas quando o endereço IPv6 alugado se torna precotado ou obsoleto (inválido), respectivamente.

O NetX Duo DHCPv6 Server mantém um tempo limite de sessão para cada Cliente acompanhar o tempo entre as mensagens do Cliente. Isto é necessário no caso de um anfitrião do Cliente perder conectividade ou a rede a descer. Quando o tempo limite de sessão expira, presume-se que o Cliente já não está interessado ou pode fazer pedidos DHCPv6 do Servidor. O Servidor elimina o registo do Cliente e devolve qualquer endereço IPv6 atribuído provisoriamente ao pool disponível. A espera de tempo de sessão é uma opção configurável para o utilizador.

Se o Cliente pretender lançar o seu endereço IPv6, ou descobrir que o endereço IPv6 que lhe foi atribuído pelo Servidor DHCPv6 já está a ser utilizado, envia uma mensagem *de Lançamento* ou *Declínio,* respectivamente. No caso de uma mensagem de *desbloqueio,* o Servidor devolve o estado do endereço IPv6 ao pool disponível. No caso da mensagem *Declínio,* atualiza a sua tabela de locação IP para indicar que este endereço IPv6 não está disponível (propriedade de outra entidade em outros pontos da rede).

**Dados de Arrendamento IPv6 e Registo de Clientes**

Quando o Servidor DHCPv6 começa a aceitar pedidos de Cliente, mantém uma lista de Clientes ativos que estão a solicitar ou que foram atribuídos endereços IPv6. O Servidor verifica a expiração do arrendamento IP através de um temporizador de locação que atualiza periodicamente a duração do aluguer do Cliente. Quando a duração exceder a duração útil válida, o Servidor limpa o registo do Cliente e devolve o seu endereço IPv6 de volta ao pool disponível. Cabe ao Cliente iniciar o processo de renovação/reencadernação antes que isso aconteça!

A tabela de registos de clientes do NetX Duo DHCPv6 Server contém informações para identificar clientes e informações 'estatais' para validar pedidos de clientes DHCPv6 e atribuir ou reatribuir endereços IPv6. Tais informações incluem:

- O Client DHCPv6 Unique Identifier (DUID) que define exclusivamente cada anfitrião do Cliente numa rede. O Cliente deve sempre utilizar este mesmo DUID para todas as suas mensagens DHCPv6.

- A Associação de Identidade do Cliente para Endereços Não Temporários (IANA) e a Associação de Identidade IPv6 endereço IPv6 (IA) que definem cumulativamente os parâmetros de atribuição de endereços IPv6 do Cliente.

- Pedidos de opção do cliente (servidor DNS, nome de domínio, etc).

- O endereço de origem do Cliente IPv6 (se definido) e endereço de destino (se não multicast) do seu mais recente pedido DHCPv6.

- O mais recente tipo de mensagem do Cliente e o 'estado' do DHCPv6.

## <a name="netx-duo-dhcpv6-server-requirements-and-constraints"></a>Requisitos e constrangimentos do servidor NetX Duo DHCPv6

A API do Servidor DHPV6 netX requer ThreadX 5.1 ou mais tarde e NetX Duo 5.5 ou mais tarde.

**Requisitos**

***Configuração de tarefas ip thread***

O NetX Duo DHCPv6 Server requer a criação de uma instância IP para o envio e receção de mensagens para o DHCPv6 na sua ligação de rede. Isto é feito usando o serviço *nx_ip_create.* O próprio Servidor DHCPv6 duo NetX deve ser criado. Isto é feito usando o serviço *nx_dhcpv6_server_create.*

DHCPv6 utiliza NetX Duo, ICMPv6 e UDP. Portanto, o IPv6 deve ser ativado primeiro antes de utilizar o SERVIDOR DHCPv6, ligando para os seguintes serviços NetX Duo:

- *nx_udp_enable*
- *nxd_ipv6_enable*
- *nxd_icmp_enable*

Além disso, antes de o Servidor DHCPv6 poder ser iniciado, tem uma série de tarefas de configuração para executar:

- Crie e valide os seus endereços globais de ligação local e IPv6. A validação do endereço é realizada automaticamente pelo NetX Duo utilizando a Deteção de Endereços Duplicado se estiver ativada. Consulte o Manual do *Utilizador NetX Duo* para obter mais informações sobre a validação de endereços IP locais e globais.

- Dedibrar o índice de interface de rede para a sua interface DHCPv6.

- Crie um intervalo de endereços IP para endereços IPv6 atribuíveis. Ou, se os dados existirem de uma sessão anterior do Servidor DHCPv6, a tabela de locação IPv6 e os registos dos clientes dessa sessão devem ser enviados da memória não volátil para o Servidor DHCPv6. O pequeno sistema de exemplos em outros lugares deste documento irá demonstrar os serviços do Servidor DHCPv6 para a realização deste requisito.

- Desaprote o servidor DUID. Se o Servidor criou o seu DUID numa sessão anterior, deve utilizar os mesmos dados para criar o mesmo DUID para mensagens aos seus Clientes. O pequeno sistema de exemplos noutros locais deste documento demonstrará como este requisito é cumprido.

Neste ponto, o Servidor DHCPv6 está pronto para ser executado. Internamente, o NetX Duo DHCPv6 Server criará uma tomada UDP ligada à porta 547 e começa a ouvir os pedidos do Cliente.

***Requisitos de piscina de pacotes***

O NetX Duo DHCPv6 Server requer um pacote de pacotes para o envio de mensagens DHCPv6. O tamanho do pacote em termos de carga útil de pacotes e número de pacotes disponíveis é configurável pelo utilizador, e depende do volume antecipado de mensagens DHCPv6 e outras transmissões que a aplicação do anfitrião irá enviar.

Uma mensagem típica de DHCPv6 é de cerca de 200-300 bytes, dependendo do número de opções adicionais solicitadas pelo Cliente, e informações disponíveis no Servidor.

***Definição da interface do Servidor DHCPv6***

O Servidor DHCPv6 desrespuca da interface de rede primária, uma vez que a interface aceitará os pedidos do Cliente. No entanto, a aplicação do anfitrião deve ainda definir o índice de endereço global que utilizou para criar o endereço global do Servidor. O índice de interface DHCPv6 e o índice global de endereços são definidos usando o serviço *nx_dhcpv6_server_interface_set.* Isto também é demonstrado no "pequeno exemplo" deste documento.

***Salvar DHCPv6 DUID através de Reboots de Servidor***

O protocolo DHCPv6 requer que o Servidor utilize o mesmo DUID em várias reinicializações. Os dados utilizados para criar o DUID devem, portanto, ser armazenados e recuperados da memória nãovolárceda para este requisito. Para os anfitriões que usam o Link Layer Plus Time DUID que requer acesso a um relógio em tempo real. A aplicação de anfitrião NetX Duo DHCPv6 deve incluir o acesso de dados em tempo real para gerar um valor temporal para a criação inicial do Servidor DUID e armazenar esses dados para reutilização em sessões subsequentes do Servidor. O *nx_dhcpv6_set_server_duid* então toma os dados DUID como seus argumentos, bem como opções de configuração dependendo do tipo DUID, para produzir (ou reproduzir) o seu próprio DUID.

***Criação de lista de endereços IPv6 atribuível***

Após a criação do Servidor DHCPv6, a aplicação do anfitrião do Servidor deve criar uma gama de endereços globais IPv6 atribuíveis se não existirem dados da lista de endereços IP previamente armazenados. Isto é feito usando o serviço *nx_dhcpv6_create_ip_address_range* que toma como entrada um endereço IPv6 inicial e final.

***Guardar endereços e dados atribuíveis dhcpv6 e dados do cliente***

O protocolo DHCPv6 requer que o Servidor DHCPv6 guarde os dados de endereço do seu Cliente e IPv6 no armazenamento nãovolículo em caso de reinicialização do servidor. O NetX Duo DHCPv6 Server dispõe de várias API para o upload e descarregamento de dados de endereços do Cliente e do IPv6 de e para o Servidor DHCPv6, respectivamente:

*nx_dhcpv6_add_client_record*

*nx_dhcpv6_add_ip_address_lease*

*nx_dhcpv6_retrieve_client_record*

*nx_dhcpv6_retrieve_ip_address_lease*

O upload dos dados para o Servidor tem de ser feito antes de reiniciar o Servidor. O download dos dados só deve ser feito depois de o Servidor DHCPv6 ser interrompido (ou suspenso). Os serviços para o fazer são descritos em pormenor mais tarde neste documento. No entanto, o NetX Duo DHCPv6 fornece não define um acesso ao armazenamento nãovoláctico. Isto deve ser tratado pela aplicação do anfitrião. O pequeno exemplo demonstra como a aplicação do anfitrião faz isto.

***Identificador Exclusivo do Servidor DHCP (DUID)***

O Servidor DUID define exclusivamente o anfitrião do Servidor DHCPv6 na rede. Se um Servidor não tiver criado previamente o seu DUID, pode utilizar o *nx_dhcpv6_server_set_duid* para criar um. De acordo com o RFC 3315, o Servidor DHCPv6 deve guardar este DUID para memória nãovoláctica para poder recuperá-lo após o reboot do Servidor. O Servidor DHCPv6 suporta os tipos DUID da Camada de Ligação, do Tempo da Camada de Ligação e da Empresa (Fornecedor designado). Note que o Cliente deve enviar diretamente o tipo de Fornecedor DUID. A opção para DUIDs do tipo fornecedor (17) não é suportada diretamente pelo Servidor DHPv6 do Duo NetX.

A aplicação do anfitrião do servidor DHCPv6 tem valores predefinidos para a atribuição de endereços IPv6, incluindo o tempo de locação. Consulte opções configurais mais tarde neste documento para saber como definir estas opções. :

O bloco de controlo *IANA* contém os campos T1 e T2. O bloco *IA* no bloco de controlo *IANA* contém os campos de vida preferidos e válidos. A aplicação de anfitrião tem opções configuráveis definidas em outros lugares deste documento para definir estas opções. São atribuídos a todos os pedidos de endereço do Cliente IPv6.

Estes parâmetros de locação IP DHCPv6 são definidos abaixo.

T1 – tempo em segundos quando o Cliente deve começar a renovar o seu endereço IPv6 do Servidor que o atribuiu.

T2 – tempo em segundos quando o Cliente deve começar a religar o endereço IPv6, se a renovação falhar, com qualquer Servidor na sua ligação.

Vida útil preferida – tempo em segundos quando o endereço cliente for depreciado se o Cliente não o tiver renovado ou recuperado. O Cliente ainda pode usar este endereço.

Vida útil válida – tempo em segundos quando o endereço IP do Cliente estiver expirado e NÃO DEVE utilizar este endereço nas suas transmissões de rede.

O RFC recomenda T1 e T2 vezes que sejam 0,5 e 0,8, respectivamente, da vida útil preferida na opção Cliente *IANA.* Se o Servidor não tiver preferência, deverá definir estes tempos para zero. Se uma resposta do Servidor contiver T1 e T2 vezes definidas para zero, está a permitir que o Cliente desemalte as suas próprias T1 e T2 vezes.

**Restrições**

O NetX Duo DHCPv6 Server não suporta as seguintes opções DHCPv6:

  - Opção De Compromisso Rápido que otimiza o processo de pedido de endereço DHCPv6 apenas para a troca de mensagens Solicit and Answer

  - Reconfigurar a opção que permite ao Servidor pode iniciar alterações ao estado do endereço IP do Cliente.

  - Opção Unicast; todas as mensagens do Cliente devem ser enviadas para o *All_DHCP_Relay_Agents_and_Servers* endereço multicast e não diretamente para o Servidor DHCPv6.

  - Associação de Identidade para a Opção Endereços Temporários (IA_TA)que é um endereço IP temporário concedido a um Cliente.

  - Opções de IPv6 (endereços IPv6) por Pedido de Cliente

  - O anfitrião de retransmissão entre o Cliente DHCPv6 e o Servidor, por exemplo, o Cliente e o Servidor devem estar na mesma rede.

  - IPSec e Autenticação não são suportados em mensagens DHCPv6. No entanto, a instância IP pode ser ativada ipSec dependendo da versão do NetX Duo em uso.

  - O NetX Duo DHCPv6 Server suporta diretamente apenas o pedido de opção do servidor DNS. Isto pode mudar em futuras versões.

  - A opção de delegação prefixo não é apoiada.

  - Autenticação de mensagens DHCPv6 embora IPSec possa ser ativada no ambiente NetX Duo subjacente. Nem o NetX Duo DHCPv6 Server suporta ligações de retransmissão aos Clientes. Presume-se que todos os pedidos do Cliente são originários de anfitriões na rede server.

## <a name="netx-duo-dhcpv6-server-callback-functions"></a>Funções de callback do servidor NetX Duo DHCPv6

*nx_dhcpv6_IP_address_declined_handler*

Quando o Cliente DHCPv6 envia uma mensagem de Declínio, o Servidor DHCPV6 da NetX Marca o endereço como não disponível nas suas tabelas de endereços IPv6. Para ter a capacidade de personalizar o tratamento do Servidor desta mensagem, é fornecida a *nx_dhcpv6_IP_address_declined_handler* *.* No entanto, esta chamada não está atualmente implementada.

*nx_dhcpv6_server_option_request_handler*

Quando a mensagem do Cliente DHCPv6 contém dados de pedido de opção, o NetX Duo DHCPv6 Server reencaminho cada código de opção de pedido de opção para esta chamada de utilizador, se definido. Isto dá ao NetX Duo Server a capacidade de permitir que o utilizador definiu o revés preencha os dados. No entanto, esta funcionalidade não está atualmente implementada.

## <a name="supported-dhcpv6-rfcs"></a>DHCPv6 RFCs apoiados

NetX Duo DHCPv6 está em conformidade com RFC3315, RFC3646 e RFCs relacionados.