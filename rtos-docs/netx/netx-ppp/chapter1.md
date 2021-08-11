---
title: Capítulo 1 - Introdução ao Protocolo Azure RTOS NetX Ponto-a-Ponto (PPP)
description: Normalmente, as aplicações NetX ligam-se à rede física real através do Ethernet.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4027d79f80928804a757e5801c74865389ab1d0237510e63348945ebe2b30045
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801976"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-point-to-point-protocol-ppp"></a>Capítulo 1 - Introdução ao Protocolo Azure RTOS NetX Ponto-a-Ponto (PPP)

Normalmente, as aplicações NetX ligam-se à rede física real através do Ethernet. Isto proporciona acesso à rede que é rápido e eficiente. No entanto, existem situações em que a aplicação não tem acesso ao Ethernet. Nesses casos, a aplicação pode ainda ligar-se à rede através de uma interface em série ligada diretamente a outro membro da rede. O protocolo de software mais comum utilizado para gerir tal ligação é o Protocolo Ponto-a-Ponto (PPP).

Embora a comunicação em série seja relativamente simples, a PPP é um pouco complexa. A PPP é efetivamente composta por vários protocolos, tais como o Protocolo de Controlo de Ligações (LCP), o Protocolo de Controlo de Protocolos de Internet (IPCP), o Protocolo de Autenticação de Palavras-Passe (PAP) e o Protocolo de Autenticação Challenge-Handshake (CHAP). O LCP é o protocolo principal para pPP. É aqui que os componentes básicos da ligação são negociados dinamicamente de forma par-a-par. Uma vez negociadas com sucesso as características básicas do link, o PAP e/ou CHAP são utilizados para garantir que um par ligado seja válido. Se ambos os pares forem válidos, o IPCP é então utilizado para negociar os endereços IP utilizados pelos pares. Uma vez concluído o IPCP, as PPP podem então enviar e receber pacotes IP.

NetX vê a PPP principalmente como um controlador de dispositivos. A função *nx_ppp_driver* é fornecida à função de criação do NetX IP, *nx_ip_create*. Caso contrário, a NetX não tem qualquer conhecimento direto de PPP.

## <a name="ppp-serial-communication"></a>Comunicação em série de PPP

O pacote de PPP NetX requer a aplicação para fornecer um controlador de comunicação em série. O controlador deve suportar caracteres de 8 bits e também empregar controlo de fluxo de software. É da responsabilidade da aplicação inicializar o condutor, o que deve ser feito antes da criação da instância PPP.

Para enviar pacotes de PPP, deve ser fornecida uma rotina de byte de saída do controlador em série às PPP (especificadas na função *nx_ppp_create).* Esta rotina de saída byte do controlador em série será chamada repetidamente para transmitir todo o pacote de PPP. É da responsabilidade do condutor em série tamponar a saída. Do lado da receção, o controlador em série da aplicação deve chamar a PPP *nx_ppp_byte_receive* função sempre que um novo byte chegar. Isto é normalmente feito no contexto de uma Rotina de Serviço de Interrupção (ISR). A função *nx_ppp_byte_receive* coloca o byte de entrada num tampão circular e alerta que as PPP recebem o fio da sua presença.

## <a name="ppp-over-ethernet-communication"></a>PPP sobre comunicação Ethernet

A PPP NetX também pode transmitir mensagem de PPP através do Ethernet, nesta situação, o pacote de PPP NetX requer a aplicação para fornecer um controlador de comunicação Ethernet.

Para enviar pacotes de PPP através do Ethernet, deve ser fornecida uma rotina de saída às PPP (especificadas na função *nx_ppp_packet_send_set).* Esta rotina de saída será chamada repetidamente para transmitir todo o pacote de PPP. Do lado da receção, o recetor da aplicação deve ligar para a função PPP *nx_ppp_packet_receive* sempre que um novo pacote chegar.

## <a name="ppp-packet"></a>Pacote PPP

PPP utiliza o enquadramento AHDLC (um subconjunto de HDLC) para encapsular todos os controlos do protocolo de PPP e dados do utilizador. Uma moldura AHDLC parece o seguinte:

|**Sinalizador**|**Addr**|**Ctrl**|**Informações**|**CRC**|**Sinalizador**|
|--------|--------|--------|---------------|-------|--------|
|7E |FF|03|[0-1502 bytes]|2 byte| 7E|

Cada quadro de PPP tem esta aparência geral. Os dois primeiros bytes do campo de informação contêm o tipo de protocolo PPP. Os valores válidos são definidos da seguinte forma:

- C021: LCP
- 8021: IPCP
- C023: PAP
- C223: CHAP
- 0021: Pacote de dados IP

Se o tipo de protocolo 0x0021 estiver presente, o pacote IP segue imediatamente. Caso contrário, se um dos outros protocolos estiver presente, os seguintes bytes correspondem a esse protocolo específico.

De forma a garantir 0x7E únicos marcadores de início/fim de quadro e para suportar o controlo do fluxo de software, a AHDLC utiliza sequências de escape para representar vários valores byte. O valor 0x7D especifica que o personagem seguinte é codificado, que é basicamente o personagem original exclusivo ORed com 0x20. Por exemplo, o valor 0x03 para o campo Ctrl no cabeçalho é representado pela sequência de dois byte: 7D 23. Por predefinição, valores inferiores 0x20 são convertidos numa sequência de fuga, bem como 0x7E e valores 0x7D encontrados no campo Informação. Note que as sequências de fuga também se aplicam ao campo CRC.

## <a name="link-control-protocol-lcp"></a>Protocolo de Controlo de Ligação (LCP)

O LCP é o protocolo primário de PPP e é o primeiro protocolo a ser executado. A LCP é responsável pela negociação de vários parâmetros de PPP, incluindo a Unidade de Receção Máxima (MRU) e o Protocolo de Autenticação (PAP, CHAP, ou nenhum) para utilizar. Uma vez que ambos os lados do LCP concordam com os parâmetros de PPP, os protocolos de autenticação - se houver - começam a funcionar.

## <a name="password-authentication-protocol-pap"></a>Protocolo de Autenticação de Password (PAP)

O PAP é um protocolo relativamente simples que se baseia num nome e senha que é fornecido por um lado da ligação (conforme negociado durante o LCP). O outro lado verifica então esta informação. Se estiver correta, uma mensagem de aceitação é devolvida ao remetente e as PPP podem então dirigir-se à máquina estatal IPCP. Caso contrário, se o nome ou a palavra-passe estiverem incorretos, a ligação é rejeitada.

>[!NOTE]
> Ambos os lados da interface podem solicitar PAP, mas pap é normalmente usado em apenas uma direção.

## <a name="challenge-handshake-authentication-protocol-chap"></a>Protocolo de Autenticação Challenge-Handshake (CHAP)

O CHAP é um protocolo de autenticação mais complexo do que o PAP. O autenticador CHAP fornece ao seu par um nome e um valor. O par usa então o nome fornecido para encontrar um "segredo" partilhado entre as duas entidades. Um cálculo é então feito sobre a ID, valor, e o "segredo". O resultado deste cálculo é devolvido na resposta. Se estiver correta, as PPP podem então dirigir-se à máquina estatal IPCP. Caso contrário, se o resultado estiver incorreto, a ligação é rejeitada.

Outro aspeto interessante do CHAP é que pode ocorrer em intervalos aleatórios após a criação de uma ligação. Isto é usado para evitar que uma ligação seja sequestrada – depois de ter sido autenticada. Se um desafio falhar num destes momentos aleatórios, a ligação é imediatamente terminada.

>[!NOTE]
> Ambos os lados da interface podem solicitar CHAP, mas CHAP é normalmente usado em apenas uma direção.

## <a name="internet-protocol-control-protocol-ipcp"></a>Protocolo de Controlo de Protocolos de Internet (IPCP)

O IPCP é o último protocolo a ser executado antes da comunicação PPP estar disponível para transferência de dados IP NetX. O principal objetivo deste protocolo é que um colega informe o outro do seu endereço IP. Uma vez configurado o endereço IP, a transferência de dados do NetX IP está ativada.

## <a name="data-transfer"></a>Transferência de Dados

Como mencionado anteriormente, os pacotes de dados do NetX IP residem em quadros de PPP com um ID de protocolo de 0x0021. Todos os pacotes de dados recebidos são colocados em uma ou mais estruturas NX_PACKET e transferidos para o tratamento de receção NetX. Na transmissão, o conteúdo do pacote NetX é colocado numa moldura AHDLC e transmitido.

## <a name="ppp-rfcs"></a>PPP RFCs

O NetX PPP está em conformidade com o RFC1332, RFC1334, RFC1661, RFC1994 e RFCs relacionados.