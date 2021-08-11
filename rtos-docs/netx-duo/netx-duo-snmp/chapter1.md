---
title: Capítulo 1 - Introdução ao Azure RTOS NetX Duo SNMP
description: A implementação do SNMP da NetX Duo é a de um Agente SNMP. Um agente é responsável por responder aos comandos do SNMP Manager e enviar armadilhas conduzidas por eventos.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6bf18efacc5ff7773e038a5140fc886e978ebd1ca59cc9b861139b3ce2d9ada6
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797874"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-snmp"></a>Capítulo 1 - Introdução ao Azure RTOS NetX Duo SNMP

O Simple Network Management Protocol (SNMP) é um protocolo concebido para gerir dispositivos na internet. O SNMP é um protocolo que utiliza os serviços do Protocolo de Datagramgram do Utilizador sem Ligação (UDP) para desempenhar a sua função de gestão. A implementação do Azure RTOS NetX Duo SNMP é a de um Agente SNMP. Um agente é responsável por responder aos comandos do SNMP Manager e enviar armadilhas conduzidas por eventos. 

O NetX Duo SNMP suporta a comunicação IPv4 e IPv6 com os Gestores SNMP. As aplicações NetX SNMP devem compilar e executar no NetX Duo SNMP. No entanto, o desenvolvedor é encorajado a apresentar aplicações SNMP existentes para usar os serviços equivalentes de "duo". Por exemplo, ao enviar mensagens de armadilha SNMP, os seguintes serviços de 'duo' devem substituir o seu equivalente NetX:

*nxd_snmp_object_trap_send*

*nxd_snmp_object_trapv2_send*

*nxd_snmp_object_trapv3_send*

Para mais detalhes, consulte **descrição dos Serviços de Agentes da SNMP** em outros lugares neste Manual do Utilizador para obter mais detalhes.

## <a name="netx-duo-snmp-agent-requirements"></a>Requisitos do agente SNMP da NetX Duo

O pacote NetX Duo SNMP requer que já tenha sido criada uma instância IP. Além disso, a UDP deve ser ativada nessa mesma instância DEP.

O Agente SNMP da NetX Duo tem vários requisitos adicionais. Em primeiro lugar, requer acesso ao porto 161 para lidar com todos os pedidos do gestor do SNMP. Também requer acesso à porta 162 para o envio de mensagens de armadilha para o Gestor.

Para utilizar o Agente SNMP NetX Duo com mais de IPv6 e para obter objetos IPv6, o IPv6 deve ser ativado no NetX Duo. Consulte o Guia de ***Utilizador netX Duo*** para obter mais informações sobre como ativar a instância IP para os serviços IPv6.

## <a name="netx-duo-snmp-constraints"></a>Restrições SNMP da NetX Duo

O protocolo NetX Duo SNMP implementa as versões 1, 2 e 3 da SNMP. A implementação do SNMPv3 suporta a autenticação MD5 e SHA e a encriptação DES. Esta versão do Agente SNMP Da NetX Duo tem os seguintes constrangimentos:

1. Um agente SNMP por Instância IP NetX
2. Sem apoio para a RMON
3. SNMP v3 Inform mensagens não são suportadas
4. Os tipos de dados opacos e NSAP não são suportados
5. Os endereços IPv6 são definidos como cordas de octeto, e a verificação de formato é deixada para a aplicação.

## <a name="snmp-object-names"></a>Nomes de objetos SNMP

O protocolo SNMP foi concebido para gerir dispositivos na internet. Para isso, cada dispositivo gerido pelo SNMP tem um conjunto de objetos que são definidos pela Estrutura de Informação de Gestão (SMI) conforme definido pelo RFC 1155. A estrutura é um tipo hierárquico de estrutura que se parece com o seguinte:

![Diagrama da Estrutura de Informação de Gestão.](media/image3.png)

Cada nó na árvore é um objeto. O objeto "dod" na árvore é identificado pela notação 1.3.6, enquanto o objeto "internet" na árvore é identificado pela notação 1.3.6.1. Todos os nomes dos objetos SNMP começam com a notação 1.3.6.

Um Gestor SNMP utiliza esta notação de objetos para especificar que objeto no dispositivo deseja obter ou definir. O Agente SNMP da NetX Duo interpreta tais pedidos de gerente e fornece mecanismos para a aplicação para realizar a operação solicitada.

## <a name="snmp-manager-requests"></a>Pedidos do Gerente SNMP

O SNMP tem um mecanismo simples de gestão de dispositivos. Existe um conjunto de comandos SNMP padrão que são emitidos pelo SNMP Manager para o dispositivo SNMP na *porta 161*. O seguinte mostra alguns dos comandos básicos do SNMP Manager:

| Comando SNMP | Significado                                                        |
|--------------|----------------------------------------------------------------|
| GET          | *Obtenha o objeto especificado*                                       |
| GETNEXT      | *Obtenha o próximo objeto lógico após o ID do objeto especificado*      |
| GETBULK      | *Obtenha os múltiplos objetos lógicos após o ID do objeto especificado* |
| SET          | *Desajei o objeto especificado*                                       |

Estes comandos estão codificados no formato Notação De Sintaxe Abstrata Um (ASN.1) e residem na carga útil do pacote UDP enviado pelo SNMP Manager. O Agente SNMP NetX Duo processa o pedido e, em seguida, chama a rotina de manuseamento correspondente especificada na chamada ***nx_snmp_agent_create.***

## <a name="netx-duo-snmp-agent-traps"></a>Armadilhas de agente SNMP netx duo

O Agente SNMP da NetX Duo fornece a capacidade de alertar também um Gestor de Eventos SNMP de forma assíncronea. Isto é feito através de um comando de armadilha SNMP. Existe uma API única para cada versão do SNMP para o envio de armadilhas para um Gestor SNMP. Por predefinição, as armadilhas são enviadas para o SNMP Manager na porta 162.

O Agente SNMP NetX Duo fornece chaves de segurança separadas para mensagens de armadilha SNMPv3. Para tal, a aplicação SNMP deve criar um conjunto separado de chaves das que são aplicadas às respostas aos pedidos do Gestor. A segurança do trap permite ao Agente SNMP utilizar as mesmas palavras-passe ou senhas diferentes para autenticação e privacidade. Para obter mais informações sobre a criação de chaves de segurança, consulte **a Autenticação e Encriptação SNMP do NetX Duo** na secção seguinte.

Uma lista de variáveis de armadilha snmp padrão é enumerada no topo de *nxd_snmp.h:*

| Variáveis                                 | Valor  |
|-------------------------------------------|---|
| #define NX_SNMP_TRAP_COLDSTART            | 0 |
| #define NX_SNMP_TRAP_WARMSTART            | 1 |
| #define NX_SNMP_TRAP_LINKDOWN             | 2 |
| #define NX_SNMP_TRAP_LINKUP               | 3 |
| #define NX_SNMP_TRAP_AUTHENTICATE_FAILURE | 4 |
| #define NX_SNMP_TRAP_EGPNEIGHBORLOSS      | 5 |
| #define NX_SNMP_TRAP_ENTERPRISESPECIFIC   | 6 |

Para incluir estas variáveis na mensagem de armadilha, o argumento de entrada trap_type em *nx_snmp_agent_trapv2_send* (SNMPv2) ou *nx_snmp_agent_trapv3_send* (SNMPv3) é definido para o valor enumerado destas variáveis. Um exemplo é mostrado abaixo para o SNMPv2 notificar o Gerente SNMP de um evento de arranque a frio:

```c
UINT trap_type = NX_SNMP_TRAP_COLDSTART;

status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                  (UCHAR *)"public", trap_type,
                                  tx_time_get(), NX_NULL);

```

Para incluir variáveis proprietárias na mensagem de armadilha, o argumento de entrada trap_type é definido para NX_SNMP_TRAP_CUSTOM e o argumento de entrada da lista de armadilhas contém os dados proprietários. Note que a mensagem da armadilha conterá como o tempo de subida do sistema (1.3.6.1.6.3.1.1.4.1.0). Um exemplo é mostrado abaixo para SNMPv2:

```c
NX_SNMP_TRAP_OBJECT trap_list[3];
NX_SNMP_OBJECT_DATA trap_data0;

    /* Load the data into the OBJECT. */
    nx_snmp_object_id_get((void*)"1.3.6.1.4.1.7428.1.3.2.0", &trap_data0);

    /* Update the Trap Object with the object and OID. */
    trap_list[0].nx_snmp_object_string_ptr = (UCHAR *)"1.3.6.1.6.3.1.1.4.0";
    trap_list[0].nx_snmp_object_data  = &trap_data0;

    /* Null terminate the trap list. */
    trap_list[1].nx_snmp_object_string_ptr = NX_NULL;

    status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                      (UCHAR *)"trapduo",
                                      NX_SNMP_TRAP_CUSTOM,
                                      tx_time_get(), trap_list);
```

## <a name="netx-duo-snmp-authentication-and-encryption"></a>Autenticação e Encriptação SNMP do Duo NetX

Existem dois sabores de autenticação, nomeadamente *básicos* e *digeridos.* A autenticação básica equivale a uma simples autenticação de *nome de utilizador* de texto simples encontrada em muitos protocolos. Na autenticação básica do SNMP, o utilizador limita-se a verificar se o nome de utilizador fornecido é válido para a realização de operações do SNMP. A autenticação básica é a única opção para as versões SNMP 1 e 2.

A principal desvantagem da autenticação básica é que o nome de utilizador é transmitido em texto simples. A autenticação digestiva SNMPv3 aborda este problema nunca transmitindo o nome de utilizador em texto simples. Em vez disso, um algoritmo é usado para obter uma 'digestão' de 96 bits a partir do nome de utilizador, motor de contexto e outras informações. O Agente SNMP NetX Duo suporta algoritmos MD5 e SHA digest.

Para ativar a autenticação, o Agente SNMP deve definir o seu ID do motor de contexto utilizando o serviço *nx_snmp_agent_context_engine_set.* O ID do motor de contexto é utilizado na criação da chave de autenticação.

A encriptação dos dados SNMPv3 está disponível usando o algoritmo DES. A encriptação requer que a autenticação seja ativada (não se pode encriptar dados sem definir os parâmetros de autenticação).

Para criar chaves de autenticação e privacidade, são utilizadas as seguintes API:

```c
UINT  _nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)

UINT  _nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)
```

Em seguida, o agente SNMP deve ser configurado para utilizar estas chaves. Para registar uma chave com o agente SNMP, são utilizadas as seguintes API:

```c
UINT  _nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr,
                                          NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr,
                                    NX_SNMP_SECURITY_KEY *key)
```

Podem ser criadas teclas separadas para mensagens de armadilha. Para aplicar chaves para mensagens de armadilha, estão disponíveis a seguinte API:

```c
UINT  _nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)
```

Para desativar a autenticação ou encriptação para mensagens de resposta e envio de armadilhas, utilize estes serviços com a entrada do ponteiro chave definida para NU.

## <a name="netx-duo-snmp-community-strings"></a>Cordas comunitárias NetX Duo SNMP

O Agente SNMP NetX Duo suporta cordas da comunidade pública e privada. A corda pública está definida com o serviço *nx_snmp_agent _public_string_set.* A cadeia privada NetX Duo SNMP Agent está definida utilizando o serviço *nx_snmp_agent_private_string_set.*

## <a name="netx-duo-snmp-username-callback"></a>Retenção de nome de utilizador SNMP da NetX Duo SNMP

O pacote NetX Duo SNMP Agent permite que a aplicação especifique (através da chamada ***nx_snmp_agent_create)*** uma chamada de nome de utilizador que é chamada no início do tratamento de cada pedido do Cliente SNMP.

A rotina de retorno fornece ao Agente SNMP NetX Duo com o nome de utilizador. Se o nome de utilizador fornecido for válido ou se não for necessária qualquer verificação do nome de utilizador para responder ao pedido, a chamada com o nome de utilizador deve devolver o valor de **NX_SUCCESS**. Caso contrário, a rotina deve voltar **NX_SNMP_ERROR** para indicar que o nome de utilizador especificado é inválido.

O formato da rotina de chamada de nome de utilizador da aplicação é definido abaixo:

```c
UINT nx_snmp_agent_username_process(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *username);
```

Os parâmetros de entrada são definidos da seguinte forma:

| Parâmetro | Significado                                              |
|-----------|------------------------------------------------------|
| *agent_ptr* | Ponteiro para chamar agente do SNMP                        |
| nome de utilizador  | Destino para o ponteiro para o nome de utilizador necessário |

Para as sessões SNMPvv1 e SNMPv2/v2C, a aplicação irá querer examinar a cadeia comunitária num pedido do SNMP para determinar se o pedido do SNMP tem uma cadeia comunitária válida. Existem vários serviços para a aplicação do SNMP para o fazer.

A aplicação SNMP pode inquirir se o atual pedido do SNMP Manager é um GET (por exemplo, GET, GETNEXT ou GETBULK) ou tipo de pedido SET utilizando este serviço:

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

Se o pedido for um tipo GET, a aplicação irá querer comparar a cadeia comunitária de entrada com a cadeia pública do Agente SNMP:

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr,
                                      UCHAR *username,
                                      UINT *is_public);
```

Da mesma forma, se o pedido for um tipo SET, a aplicação irá querer comparar a cadeia comunitária de entrada com a cadeia privada do Agente SNMP:

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr,
                                       UCHAR *username,
                                       UINT *is_private);
```

Os valores de retorno is_public e is_private indicam, respectivamente, se a cadeia comunitária de entrada é uma cadeia comunitária pública ou privada válida.

O valor de devolução da rotina de chamada do nome de utilizador indica se o nome de utilizador é válido. O valor **NX_SUCCESS** é devolvido se o nome de utilizador for válido ou **NX_SNMP_ERROR** se o nome de utilizador for inválido.

## <a name="netx-duo-snmp-agent-get-callback"></a>NetX Duo SNMP Agent GET Callback

A aplicação deve definir uma rotina de retorno para lidar com pedidos de objetos GET do SNMP Manager. O retorno recupera o valor do objeto especificado no pedido.

A rotina de chamada de pedido GET da aplicação é definida abaixo:

```c
UINT nx_snmp_agent_get_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

Os parâmetros de entrada são definidos da seguinte forma:

| Parâmetro        | Significado |
|------------------|----------------------------------|
| *agent_ptr*        | Ponteiro para chamar agente do SNMP |
| object_requested | Cadeia ASCII que representa o ID do objeto para a operação GET é para. |
| object_data      | Estrutura de dados para manter o valor recuperado pela chamada. Isto pode ser definido com uma série de API SNMP SNMP da NetX descrito abaixo. |

> [!NOTE]
> *Para as cordas de octeto, o objeto deve ser atribuído o comprimento de modo a que a função interna saiba quanto tempo o comprimento é, uma vez que a própria chamada não tem um argumento de comprimento:*

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

Uma vez que o tipo de dados não é conhecido da chamada GET, não há necessidade de verificar o tipo de dados. O comprimento não terá qualquer efeito sobre tipos ou cordas numéricas que sejam delimitadas nulas.

Em seguida, chame a função interna:

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

Se a função de retorno não encontrar o objeto solicitado, o código de erro **NX_SNMP_ERROR_NOSUCHNAME** deve ser devolvido. Se for detetado qualquer outro erro, o **NX_SNMP_ERROR** deve ser devolvido.

## <a name="netx-duo-snmp-agent-getnext-callback"></a>NetX Duo SNMP Agent GETNEXT Callback

A aplicação também deve definir a rotina de retorno para pedidos de objeto GETNEXT do Gerente SNMP. A chamada GETNEXT recupera o valor do próximo objeto especificado pelo pedido.

A rotina de chamada de pedido GETNEXT da aplicação é definida abaixo:

```c
UINT nx_snmp_agent_getnext_process(NX_SNMP_AGENT *agent_ptr,
                                   UCHAR *object_requested,
                                   NX_SNMP_OBJECT_DATA *object_data);
```

Os parâmetros de entrada são definidos da seguinte forma:

| Parâmetro        | Significado |
|------------------|-------------------------------------------|
| *agent_ptr*        | Ponteiro para chamar agente do SNMP |
| object_requested | Cadeia ASCII que representa o objeto ID a operação GETNEXT é para. |
| object_data      | Estrutura de dados para manter o valor recuperado pela chamada. Isto pode ser definido com uma série de API SNMP SNMP da NetX descrito abaixo. |

O mesmo que é verdade para as chamadas GET, os objetos com dados de cadeia de octeto devem ser atribuídos ao comprimento para que a função interna saiba quanto tempo o comprimento é, uma vez que a própria chamada não tem um argumento de comprimento:

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

Uma vez que o tipo de dados não é conhecido da chamada GET, não há necessidade de verificar o tipo de dados. O comprimento não terá qualquer efeito sobre tipos ou cordas numéricas que sejam delimitadas nulas.

Em seguida, chame a função interna:

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

Se a função de retorno não encontrar o objeto solicitado, o código de erro **NX_SNMP_ERROR_NOSUCHNAME** deve ser devolvido. Se for detetado qualquer outro erro, o **NX_SNMP_ERROR** deve ser devolvido.

## <a name="netx-duo-snmp-agent-set-callback"></a>NetX Duo SNMP Agent SET Callback

A aplicação deve definir a rotina de retorno para o tratamento dos pedidos de objetos SET do SNMP. A chamada SET define o valor do objeto especificado pelo pedido.

A rotina de chamada de pedido de pedido de candidatura set é definida abaixo:

```c
UINT nx_snmp_agent_set_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

Os parâmetros de entrada são definidos da seguinte forma:

| Parâmetro        | Significado |
|------------------|-------- |
| *agent_ptr*      | Ponteiro para chamar agente do SNMP |
| object_requested | Cadeia ASCII que representa o ID do objeto para a operação SET é para. |
| object_data      | Estrutura de dados que contém o novo valor para o objeto especificado. A operação real pode ser feita utilizando o API da API do SNMP Da NetX Duo descrito abaixo. |

Note que para as cordas de octeto, o retorno SET deve atualizar a tabela MIB com o comprimento dos dados uma vez que o Agente SNMP analisou os dados e sabe o tipo e comprimento:

```c
if (object_data -> nx_snmp_object_data_type ==
                           NX_SNMP_ANS1_OCTET_STRING)
{
    mib2_mib[i].length =
        object_data -> nx_snmp_object_octet_string_size;
}

object_data -> nx_snmp_object_octet_string_size =
                                 mib2_mib[i].length;
```

Se a função de retorno não encontrar o objeto solicitado, o código de erro **NX_SNMP_ERROR_NOSUCHNAME** deve ser devolvido.

Se o anfitrião NetX Duo SNMP criou cordas comunitárias privadas, e o remetente SNMP do pedido SET não tiver a cadeia privada correspondente, poderá devolver um erro **de NX_SNMP_ERROR_NOACCESS.** Se for detetado qualquer outro erro, o **NX_SNMP_ERROR** deve ser devolvido.

> [!NOTE]
> *Embora o Agente SNMP Da NetX Duo forneça uma base de dados SNMP MIB com a distribuição, destina-se principalmente a fins de teste e desenvolvimento. O desenvolvedor provavelmente exigirá uma base de dados de MIB proprietária para uma aplicação profissional do SNMP.*

## <a name="changing-snmp-version-at-run-time"></a>Alterar a versão SNMP no tempo de execução

O anfitrião do Agente SNMP pode alterar a versão SNMP para cada uma das três versões em execução utilizando o serviço *nx_snmp_agent_set_version.* O Agente SNMP está habilitado por padrão para as três versões quando o Agente SNMP é criado em *nx_snmp_agent_create*. No entanto, a aplicação pode limitar isso a um subconjunto de todas as versões.

> [!NOTE]
> *Se as opções de configuração NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 e/ou NX_SNMP_DISABLE_V3 forem definidas, esta função não terá qualquer efeito que permita as versões efetuadas.*

O Agente SNMP pode recuperar a versão SNMP do mais recente pacote SNMP recebido através do serviço *nx_snmp_agent_get_current_version.*

## <a name="snmpv3-discovery"></a>Descoberta SNMPv3

O Agente SNMP, se estiver habilitado para o SNMPv3, responderá aos pedidos de descoberta do Gestor do SNMP. Tal pedido contém dados de parâmetros de segurança com valores nulos para ID do motor autoritário, nome de utilizador, contagem de botas e tempo de arranque. Os parâmetros de autenticação não são aplicados à mensagem DISCOVERY. A lista de encadernação variável no pedido está vazia (contém zero itens). O agente SNMP responde com um tempo e contagem zero de arranque, e a lista de encadernação variável contendo 1 item, *usmStatsUnknownEngineIDs,* que é a contagem de pedidos recebidos com um ID de motor desconhecido (nulo). No pedido getneXT subsequente do Browser/Manager, os dados de arranque e os parâmetros de segurança só são preenchidos se a segurança estiver ativada. Em caso afirmativo, também enviará uma atualização de dados NotInTime no PDU. Os parâmetros de segurança, por exemplo, a autenticação comprovam a identidade do Agente ao Gestor.

Informações mais detalhadas sobre a autenticação do SNMPv3 estão disponíveis no RFC 3414 "Modelo de Segurança Baseado no Utilizador (USM) para a versão 3 do Protocolo de Gestão de Redes Simples (SNMPv3)".

## <a name="netx-duo-snmp-rfcs"></a>NetX Duo SNMP RFCs

NetX Duo SNMP está em conformidade com RFC1155, RFC1157, RFC1215, RFC1901, RFC1905, RFC1906, RFC1907, RFC1908, RFC2571, RFC2572, RFC2574, RFC2574, RFC2575, RFC2575, RFC2575, RFC2575, RFC2575, RFC2575, RFC2575, RFC2575, RFC2575, RFC 3414 e relacionados.
