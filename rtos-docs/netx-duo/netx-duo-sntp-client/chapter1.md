---
title: Capítulo 1 - Introdução ao Azure RTOS NetX Duo SNTP
description: O Azure RTOS NetX Simple Network Time Protocol (SNTP) é um protocolo concebido para sincronizar relógios através da Internet.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b3e1170197c6c4981060459104da80e354fac5db
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825753"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-sntp"></a>Capítulo 1 - Introdução ao Azure RTOS NetX Duo SNTP 

O Azure RTOS NetX Simple Network Time Protocol (SNTP) é um protocolo concebido para sincronizar relógios através da Internet. A Versão 4 da SNTP é um protocolo simplificado baseado no Protocolo de Tempo de Rede (NTP). Utiliza os serviços do Protocolo de Datagram do Utilizador (UDP) para executar atualizações de tempo num protocolo simples e apátrida. Embora não seja tão complexo como o NTP, o SNTP é altamente fiável e preciso. Na maioria dos locais da Internet de hoje, a SNTP fornece precisões de 1-50 milissegundos, dependendo das características da fonte de sincronização e dos caminhos de rede. A SNTP tem muitas opções para fornecer fiabilidade de receber atualizações de tempo. A capacidade de mudar para servidores alternativos, aplicar algoritmos de votação de volta e a descoberta automática de servidores de tempo são apenas alguns dos meios para um cliente SNTP lidar com um ambiente de serviço de tempo de Internet variável. O que lhe falta em precisão compensa na simplicidade e facilidade de implementação. A SNTP destina-se principalmente a fornecer mecanismos abrangentes para aceder aos serviços nacionais de divulgação de tempo e frequência (por exemplo, servidor NTP).

## <a name="netx-duo-sntp-client-requirements"></a>Requisitos do cliente NetX Duo SNTP

O Cliente SNTP Da Dupla NetX exige que já tenha sido criada uma instância IP. Além disso, a UDP deve ser ativada nesse mesmo caso IP e deve ter acesso à conhecida porta 123 para o envio *de* dados de tempo para um SNTP Server, embora as portas alternativas também funcionem. Os clientes de radiodifusão devem ligar a porta UDP que o seu servidor de transmissão está a enviar, normalmente 123. A aplicação do Cliente NetX Duo SNTP deve ter um ou mais endereços IP SNTP Server.

## <a name="netx-duo-sntp-client-limitations"></a>Limitações do cliente NetX Duo SNTP 

A precisão na representação do tempo local nas atualizações de tempo NTP tratadas pela API do Cliente SNTP limita-se à resolução milissegundo.

O Cliente SNTP só tem um único endereço SNTP Server a qualquer momento. Se esse Servidor parecer já não ser válido, a aplicação deve parar a tarefa do Cliente SNTP e reinitilizá-la com outro endereço de servidor SNTP, utilizando a comunicação SNTP transmitida ou unicast.

O Cliente SNTP não suporta muitos elencos.

O Cliente NetX Duo SNTP não suporta mecanismos de autenticação para verificar os dados dos pacotes recebidos.

## <a name="netx-duo-sntp-client-operation"></a>Operação cliente SNTP duo NetX

O RFC 4330 recomenda que os clientes SNTP operem apenas no estrato mais alto da sua rede local e de preferência em configurações em que nenhum cliente NTP ou SNTP os dependa para sincronização. O nível de estrato reflete a posição de anfitrião na hierarquia do tempo NTP, onde o estrato 1 é o nível mais alto (um servidor de tempo de raiz) e 15 é o nível mais baixo permitido (por exemplo, Cliente). O estrato mínimo do Cliente SNTP é 2.

O Cliente SNTP NetX Duo pode operar num dos dois modos básicos, unicast ou transmitido, para obter tempo através da Internet. No modo unicast, o Cliente sonda o seu Servidor SNTP em intervalos regulares e espera receber uma resposta desse Servidor. Quando um é recebido, o Cliente verifica que a resposta contém uma atualização de tempo válida aplicando um conjunto de 'verificações de sanidade' recomendadas pelo RFC 4330. O Cliente aplica então a diferença horária, se houver, com o relógio do Servidor ao relógio local. No modo de transmissão, o Cliente apenas ouve as transmissões de atualização de tempo e mantém o seu relógio local depois de aplicar um conjunto semelhante de verificações de sanidade para verificar os dados de tempo de atualização. Os controlos de sanidade são descritos em pormenor na secção **SNTP Sanity Checks** abaixo.

Antes de o Cliente poder funcionar em ambos os modos, deve estabelecer os seus parâmetros de funcionamento. Isto é feito chamando *nx_sntp_client_initialize_unicast* ou *nx_sntp_client_initialize_broadcast* para modos unicast ou de transmissão, respectivamente. Estes servem definir os intervalos de tempo para o lapso de tempo máximo sem uma atualização válida, o limite de atualizações inválidas consecutivas recebidas, um intervalo de votação para o modo unicast, modo de funcionamento, por exemplo, unicast vs. transmissão, e SNTP Server.

Se o lapso de tempo máximo ou as atualizações inválidas máximas recebidas forem ultrapassadas, o Cliente SNTP continua a funcionar, mas define o estado atual do SNTP Server para inválido. A aplicação pode sondar o Cliente SNTP usando o serviço *nx_sntp_client_receiving_updates* para verificar se o SNTP Server ainda está a enviar atualizações válidas. Caso contrário, deverá parar a linha do Cliente SNTP utilizando o serviço *nx_sntp_client_stop* e ligar para qualquer um dos dois serviços de inicialização para definir outro endereço SNTP Server. Para reiniciar o Cliente SNTP, a aplicação chama *nx_sntp_client_run_broadcast* ou *nx_sntp_client_run_unicast*. Note que a aplicação pode alterar o modo de funcionamento do Cliente SNTP na chamada inicial para mudar para unicast ou transmitir conforme desejado.

### <a name="local-clock-operation"></a>Operação Local do Relógio

O tempo SNTP baseado no número de segundos no relógio master NTP, ou número de segundos decorridos na primeira época NTP, por exemplo, de 1 de janeiro **1900 00:00:00 a** jan **1 1999 00:00:00**. O significado de 01-01-1999 foi quando ocorreu o último salto segundo. Este valor é definido da seguinte forma:

\#definir NTP_SECONDS_AT_01011999 0xBA368E80

Antes do Cliente SNTP ser executado, a aplicação pode opcionalmente inicializar o Cliente SNTP local para que o Cliente utilize como um tempo de base. Para tal, deve utilizar o *serviço nx_sntp_client_set_local_time.* Isto leva o tempo em formato NTP, segundos e fração, onde a fração é o milissegundo no tempo condensado NTP. Idealmente, a aplicação pode obter um tempo SNTP a partir de uma fonte independente. Não existe API para conversão de ano, mês, data e hora para uma hora NTP no NetX Duo SNTP Client. Para uma descrição do formato de tempo NTP, consulte a *versão 4 do RFC4330 "Simple Network Time Protocol (SNTP) para IPv4, IPv6 e OSI".*

Se não for fornecida nenhuma hora local base quando o Cliente SNTP começar, o Cliente SNTP aceitará as atualizações SNTP sem comparar com a sua hora local na primeira atualização. A partir daí, aplicará os valores máximos e mínimos de atualização do tempo para determinar se irá modificar a sua hora local.

Para obter o Cliente SNTP a tempo local, a aplicação pode utilizar o serviço *nx_sntp_client_get_local_time_extended.*

### <a name="sntp-sanity-checks"></a>Verificações de Sanidade SNTP 

O Cliente examina o pacote de entrada para os seguintes critérios:

  - O endereço IP de origem deve corresponder ao endereço IP do servidor atual.

  - A porta de origem do remetente deve coincidir com a porta de origem do servidor atual.

  - O comprimento do pacote deve ser o comprimento mínimo para segurar uma mensagem de tempo SNTP.

Em seguida, os dados de tempo são extraídos do tampão do pacote ao qual o Cliente aplica um conjunto de "verificações de sanidade" específicas:

  - O indicador de salto definido para 3 indica que o Servidor não está sincronizado. O Cliente deve tentar encontrar um servidor alternativo.

  - Um campo de estrato definido para zero é conhecido como um pacote de Beijo da Morte (KOD). O manipulador KOD do Cliente SMTP para esta situação é uma chamada definida pelo utilizador. O pequeno ficheiro de demonstração de exemplo contém um simples manipulador KOD para esta situação. O campo de identificação de referência contém opcionalmente um código que indica o motivo da resposta KOD. De qualquer forma, o manipulador KOD deve indicar como lidar com receber um beijo de morte do Servidor SNTP. Normalmente, vai querer reiniciar o Cliente SNTP com outro Servidor SNTP.

  - A versão SNTP do Servidor, o estrato e o modo de funcionamento devem ser compatíveis com o serviço Cliente.

  - Se o Cliente estiver configurado com um máximo de dispersão do relógio do servidor, o Cliente verifica a dispersão do relógio do servidor apenas na primeira atualização recebida e, se exceder o máximo de Cliente, o Cliente rejeita o Servidor.

  - Os campos de carimbo de tempo do Servidor também devem passar verificações específicas. Para o servidor unicast, todos os campos de tempo devem ser preenchidos e não podem ser NUOSos. O carimbo de tempo de origem deve ser igual ao carimbo de tempo transmito no pedido de mensagem de tempo SNTP do Cliente. Isto protege o Cliente de intrusos maliciosos e comportamento fraudulento do Servidor. O servidor de transmissão só precisa de preencher a carimbo de tempo transmit. Uma vez que não recebe nada do Cliente não tem campos de Receção ou Origem para preencher.

    Uma verificação de sanidade falhada marca uma atualização de tempo como uma atualização de tempo inválida. O serviço de verificação de sanidade do Cliente SNTP rastreia o número de atualizações de tempo inválidas consecutivas recebidas do mesmo Servidor.

Quando a tarefa de thread do Cliente SNTP verifica a validade de um pacote SNTP para se candidatar ao tempo de Cliente SNTP local, aumenta a contagem do Cliente SNTP Também devolve um estado de `nx_sntp_client_invalid_time_updates.` erro ao chamador, mas este é todo o processamento interno para que não seja imediatamente visível para a aplicação. A forma de detetar atualizações de tempo falhadas é consultar o valor do Cliente SNTP depois de `nx_sntp_client_invalid_time_updates` receber atualizações de tempo do SNTP Server.

Se a atualização do tempo do Servidor passar nas verificações de sanidade, o Cliente tenta então processar os dados de tempo para a sua hora local. Se o Cliente estiver configurado para cálculo de ida e volta, por exemplo, o tempo de envio de um pedido de atualização para a hora em que um é recebido, o tempo de viagem de ida e volta é calculado. Este valor é reduzido para metade e, em seguida, adicionado ao tempo do Servidor.

Em seguida, se esta for a primeira atualização recebida do atual Servidor SNTP, o Cliente SNTP determina se deve ignorar a diferença entre o Servidor e o Cliente local. Posteriormente, todas as atualizações do SNTP Server são avaliadas para a diferença com o Cliente local.

A diferença entre o tempo de Cliente e servidor é comparada com `NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT` . Se exceder este valor, os dados são deitados fora. Se a diferença for inferior `NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT` à diferença, considera-se demasiado pequena para exigir ajustamento.

Passando todas estas verificações, a atualização de tempo é então aplicada ao Cliente SNTP com algumas correções por atrasos no processamento interno do Cliente SNTP.

### <a name="sntp-asynchronous-unicast-requests"></a>Pedidos de Unicast Assíncronos SNTP Asynchronous 

O Cliente SNTP permite que a aplicação do anfitrião envie assincroticamente um pedido unicast para o tempo atual a partir do servidor NTP.

```C
UINT _nx_sntp_client_request_unicast_time(
NX_SNTP_CLIENT *client_ptr, 
UINT wait_option)
```

A opção de espera é a expiração para esperar por uma resposta.

Se o Servidor NTP responder, o pacote será submetido às mesmas verificações de processamento e sanidade descritas na secção anterior antes de atualizar o Cliente SNTP local.

Se a chamada retornar com sucesso, a aplicação pode ligar *para nx_sntp_client_utility_display_date_time* ou *nx_sntp_client_get_local_time_extended* para a hora local atualizada.

Estes pedidos unicast não interferem com o horário normal do Cliente SNTP para o envio do próximo pedido unicast, ou se em modo de transmissão, quando esperar a próxima transmissão NTP.

### <a name="periodic-local-time-updates"></a>Atualizações periódicas do tempo local

O ajuste máximo à hora local é definido na opção NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT (em milissegundos). O intervalo de atualização de sondagens para operações unicast SNTP Cliente é definido na opção NX_SNTP_CLIENT_UNICAST_POLL_INTERVAL (em segundos). Se o intervalo de votação for maior do que o ajuste máximo, então as atualizações subsequentes do servidor após a primeira atualização do servidor serão rejeitadas. Para evitar isto, o Cliente SNTP atualizará periodicamente o tempo local definido como NX_SNTP_UPDATE_TIMEOUT_INTERVAL. 

Se houver uma diferença de tempo entre o RTC a bordo e a hora do servidor (a que deve ser definida a hora local do Cliente SNTP), o RTC deve ser sincronizado com o tempo de Cliente SNTP (não demonstramos isso neste Manual do Utilizador).

Uma vez que as atualizações do servidor SNTP não devem ocorrer mais frequentemente do que uma vez por hora, não é útil inquirir o Cliente SNTP para atualizações de servidores ou estado do servidor com mais frequência do que isso. No entanto, o Cliente SNTP deve atualizar o seu relógio local com frequência suficiente para não cair mais do que o parâmetro de ajuste de tempo máximo NX_SNTP_CLIENT_MAX_TIME_LAPSE.

Em alternativa, o NX_SNTP_CLIENT_MAX_TIME_LAPSE de regulação máximo pode ser definido para maior do que a atualização de sondagens unicast (ou intervalos de transmissão previstos). Este último elimina a necessidade de um relógio independente em tempo real. No entanto, a intenção do protocolo SNTP é evitar a dependência total das atualizações locais de RTC ou de tempo de rede. Além disso, as atualizações do SNTP Server destinam-se a evitar derivas no relógio de tempo local.

## <a name="multiple-network-interfaces"></a>Múltiplas interfaces de rede

O Cliente SNTP NetX Duo pode ser configurado para funcionar em redes secundárias desde que essas redes estejam registadas com a instância IP. Consulte o NetX Duo ou o NetX User Guide para obter mais informações sobre como registar redes secundárias.

Na *chamada nx_sntp_client_create,* desave a terceira entrada, iface_index, para o índice da rede para o Cliente SNTP receber atualizações de tempo. A interface primária está sempre no índice 0. O Cliente SNTP NetX Duo não consegue suportar atualizações de tempo simultaneamente em múltiplas interfaces de rede.

## <a name="sntp-and-ntp-rfcs"></a>SNTP e NTP RFCs

O cliente NetX Duo SNTP está em conformidade com o RFC4330 "Simple Network Time Protocol (SNTP) Versão 4 para IPv4, IPv6 e OSI" e RFCs relacionados.