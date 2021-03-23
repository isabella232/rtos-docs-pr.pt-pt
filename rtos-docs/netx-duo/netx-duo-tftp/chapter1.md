---
title: Capítulo 1 - Introdução ao Azure RTOS NetX Duo TFTP
description: O Trivial File Transfer Protocol (TFTP) é um protocolo leve concebido para transferências de ficheiros.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4431b23e143d05214090547e7f179a6f5def8217
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825711"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-tftp"></a>Capítulo 1 - Introdução ao Azure RTOS NetX Duo TFTP 

O Trivial File Transfer Protocol (TFTP) é um protocolo leve concebido para transferências de ficheiros. Ao contrário de protocolos mais robustos, o TFTP não realiza uma verificação extensiva de erros e também pode ter um desempenho limitado porque é um protocolo de paragem e espera. Depois de um pacote de dados TFTP ser enviado, o remetente espera que um ACK seja devolvido pelo destinatário. Embora isto seja simples, limita a produção total de TFTP. O pacote TFTP permite que os anfitriões utilizem o protocolo TFTP em redes IP.

## <a name="tftp-requirements"></a>Requisitos TFTP

Para funcionar corretamente, a parte dos Clientes TFTP do pacote NetX Duo TFTP requer que já tenha sido criada uma instância IP. Além disso, a UDP deve ser ativada nessa mesma instância DEP. A parte cliente do pacote NetX Duo TFTP não tem requisitos adicionais.

A parte do Servidor TFTP do pacote NetX Duo TFTP tem vários requisitos adicionais. Em primeiro lugar, requer acesso total à UDP *bem conhecida porta 69* para lidar com todos os pedidos de TFTP do cliente. O Servidor TFTP também foi concebido para ser utilizado com o sistema de ficheiros incorporado FileX. Se o FileX não estiver disponível, o utilizador pode apresentar as porções do FileX utilizadas para o seu próprio ambiente. Isto é discutido em secções posteriores deste guia.

## <a name="tftp-file-names"></a>Nomes de ficheiros TFTP 

Os nomes dos ficheiros TFTP devem estar no formato do sistema de ficheiros-alvo. Devem ser nulas terminadas as cordas ASCII, com informações completas sobre o percurso, se necessário. Não existe um limite especificado no tamanho dos nomes de ficheiros TFTP na implementação do NetX Duo TFTP.

## <a name="tftp-messages"></a>Mensagens TFTP

O TFTP tem um mecanismo muito simples de abertura, leitura, escrita e fecho de ficheiros. Há basicamente 2-4 bytes de cabeçalho TFTP por baixo do cabeçalho da UDP. A definição das mensagens abertas do ficheiro TFTP tem o seguinte formato:

**oooof... f0OCTET0**

Em que:

- **oooo** campo opcode de 2 byte  
0x0001 -> Aberto para leitura  
0x0002 -> Open para escrita

- **f... f** n-byte Campo de nome filename

- 0 1 byte anular o carácter de rescisão

- **OCTET** ASCII "OCTET" para especificar transferência binária

- 0 1 byte anular o carácter de rescisão

A definição da escrita TFTP, ACK, e as mensagens de erro são ligeiramente diferentes e são definidas da seguinte forma:

**oooobbbbd... d**

Em que:

- **oooo** campo opcode de 2 byte  
Pacote de dados 0x0003 ->  
0x0004 -> ACK para a última leitura  
0x0005 -> Condição de erro  

- **bbbb** 2-byte Bloco Número (1-n)

- **d... d** n-byte Campo de dados


- 0x0001 (ler) Nome do arquivo 0 OCTET 0

- 0x0002 (escrever) Nome do arquivo 0 OCTET 0

## <a name="tftp-communication"></a>Comunicação TFTP

Os Servidores TFTP utilizam a conhecida porta UDP 69 para ouvir os pedidos do Cliente. As tomadas do cliente TFTP podem ligar-se a qualquer porta UDP disponível. A carga útil do pacote de dados que contém o ficheiro para carregar ou descarregar é enviada em 512 bytes, até que o último pacote contendo < 512 bytes. Portanto, um pacote contendo menos de 512 bytes sinaliza o fim do ficheiro. A sequência geral dos acontecimentos é a seguinte:

Pedidos de ficheiros de leitura TFTP:

1.  O Cliente emite um pedido de "Open For Read" com o nome do ficheiro e aguarda uma resposta do Servidor.

2.  O Servidor envia os primeiros 512 bytes do ficheiro ou menos se o tamanho do ficheiro for inferior a 512 bytes.

3.  O Cliente recebe dados, envia um ACK e aguarda o próximo pacote do Servidor por ficheiros que contenham mais de 512 bytes.

4.  A sequência termina quando o Cliente recebe um pacote contendo menos de 512 bytes.

Pedidos de escrita TFTP:

1.  O Cliente emite um pedido "Aberto para Escrever" com o nome do ficheiro e aguarda um ACK com um número de bloco de 0 do Servidor.

2.  Quando o Servidor está pronto para escrever o ficheiro, envia um ACK com um número de bloco de zero.

3.  O Cliente envia os primeiros 512 bytes do ficheiro (ou menos para ficheiros inferiores a 512 bytes) para o Servidor e espera por um ACK de volta.

4.  O Servidor envia um ACK após a escrita dos bytes.

5.  A sequência termina quando o Cliente termina a escrita de um pacote contendo menos de 512 bytes.
 

## <a name="tftp-server-session-timer"></a>Temporizador de sessão do servidor TFTP

O Servidor TFTP tem um número limitado de slots de pedido de cliente. Se uma sessão de clientes parecer ter caído, essa ranhura não pode estar disponível para reutilização. No entanto, se a opção NX_TFTP_SERVER_RETRANSMIT_ENABLE estiver ativada, o NetX Duo TFTP Server cria um temporizador de sessão que monitoriza o tempo limite de cada uma das suas sessões de clientes. Quando um tempo limite de sessão expira, é encerrado e quaisquer ficheiros abertos são fechados. Assim, o 'slot' fica disponível para outro pedido do Cliente TFTP.

Para definir o tempo limite, ajuste a opção de configuração NX_TFTP_SERVER_RETRANSMIT_TIMEOUT que por predefinição são 200 carraças temporais. O intervalo entre os intervalos de sessão é definido pela NX_TFTP_SERVER_TIMEOUT_PERIOD que é 20 tiques temporais por predefinição.

Quando o Cliente TFTP tiver enviado ficheiros (escritos) para o meio de dados TFTP FileX, os meios de comunicação precisam de ser lavados para que os dados possam ser escritos a partir do disco de ram do servidor TFTP para os meios subjacentes (memória do disco do Cliente TFTP). Isto pode ser feito utilizando o serviço fx_media_flush se a aplicação não pretender fechar o Servidor TFTP.

No entanto, depois de fechar o servidor TFTP, a aplicação deve, se não tiver mais qualquer utilização para os meios de ficheiros, então fechar os meios de comunicação utilizando o serviço fx_media_close. Isto irá reboscar os dados do ficheiro para o disco do Cliente TFTP, fechar ficheiros abertos e atualizar as informações do diretório para os meios de comunicação.

A secção "Pequeno Exemplo" deste capítulo demonstra-o.

Uma terceira opção para atualizar os meios de ficheiros é compilar a biblioteca FileX com as opções FX_FAULT_TOLERANT ou FX_FAULT_TOLERANT_DATA em vez de utilizar explicitamente os serviços FileX. Se definido, o FileX passa automaticamente pedidos de escrita ao controlador de mídia. Estas opções podem limitar o desempenho, mas oferecem uma maior proteção contra dados de ficheiros perdidos ou aglomerados perdidos. Para obter mais informações sobre este e o FileX em geral, consulte o Guia do Utilizador Express Logic FileX.

## <a name="tftp-multi-thread-support"></a>Suporte multi-rosca TFTP

Os serviços do Cliente NetX Duo TFTP podem ser chamados a partir de várias linhas simultaneamente. No entanto, ler ou escrever pedidos para uma determinada instância do Cliente TFTP deve ser feito em sequência a partir do mesmo fio.

## <a name="tftp-rfcs"></a>TFTP RFCs

NetX Duo TFTP está em conformidade com RFC1350 e RFCs relacionados.

