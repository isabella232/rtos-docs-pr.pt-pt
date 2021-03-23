---
title: Capítulo 1 - Introdução ao Azure RTOS NetX Duo Telnet
description: O Azure RTOS NetX Duo Telnet é um protocolo concebido para transferir comandos e respostas entre dois nós na Internet.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d25f5ca4a7bf1ecf4c3d0c68ef6c8aeda7800098
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825735"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-telnet"></a>Capítulo 1 - Introdução ao Azure RTOS NetX Duo Telnet

O Azure RTOS NetX Duo Telnet é um protocolo concebido para transferir comandos e respostas entre dois nós na Internet. A Telnet é um protocolo simples que utiliza serviços fiáveis de Protocolo de Controlo de Transmissão (TCP) para executar a sua função de transferência. Por causa disso, a Telnet é um protocolo de transferência altamente fiável. Telnet é também um dos protocolos de aplicação mais utilizados.

## <a name="telnet-requirements"></a>Requisitos telnet

Para funcionar corretamente, o pacote NetX Duo Telnet requer que já tenha sido criada uma instância IP NetX. Além disso, a TCP deve ser ativada nessa mesma instância de PI. A parte do Cliente Telnet do pacote NetX Duo Telnet não tem requisitos adicionais.

A parte telnet Server do pacote NetX Duo Telnet tem um requisito adicional. Requer acesso total à *conhecida porta 23 da* TCP para lidar com todos os pedidos da Client Telnet.

## <a name="telnet-constraints"></a>Restrições telnet 

O protocolo NetX Duo Telnet implementa a norma Telnet. No entanto, a interpretação e resposta dos comandos Telnet, indicada por um byte com o valor de 255, é da responsabilidade da aplicação. Os vários comandos e parâmetros de comando da Telnet são definidos nos ficheiros *nxd_telnet_client.h e nxd_telnet_server.h.*

## <a name="telnet-communication"></a>Comunicação Telnet

Como mencionado anteriormente, o Telnet Server utiliza a *conhecida porta TCP 23* para fazer os pedidos do Cliente em campo. Os Clientes Telnet podem utilizar qualquer porta TCP disponível.

## <a name="telnet-authentication"></a>Autenticação Telnet

A autenticação telnet é da responsabilidade da função de retorno do Telnet Server da aplicação. A chamada "nova ligação" do Telnet Server da aplicação normalmente levaria o Cliente a obter nome e/ou senha. O Cliente seria então responsável pelo fornecimento da informação. O Servidor processaria então a informação na chamada "receber dados". É aqui que o código do Servidor de aplicação teria de autenticar as informações e decidir se é ou não válido.

## <a name="telnet-new-connection-callback"></a>Telnet New Connection Callback

O NetX Duo Telnet Server chama a função de chamada especificada da aplicação sempre que um novo pedido do Cliente Telnet é recebido. A aplicação especifica a função de retorno quando o Telnet Server é criado através da função ***nx_telnet_server_create.*** As ações típicas da chamada de "nova ligação" incluem o envio de um banner ou solicitação ao Cliente. Isto poderia muito bem incluir um pedido para informações de login.

### <a name="prototype"></a>Prototype

```c
void  telnet_new_connection(NX_TELNET_SERVER *server_ptr, 
                            UINT logical_connection);
```

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr**: Ponteiro para o chamado Telnet Server.
- **logical_connection**: A ligação lógica interna para o Servidor Telnet. Isto pode ser usado pela aplicação como um índice em tampãos e/ou estruturas de dados específicas para cada ligação do Cliente. O seu valor varia entre 0 e NX_TELNET_MAX_CLIENTS - 1.

## <a name="telnet-receive-data-callback"></a>Telnet Receber Chamada de Dados

O NetX Duo Telnet Server chama a função de chamada especificada da aplicação sempre que um novo dado do Cliente Telnet é recebido. A aplicação especifica a função de retorno quando o Telnet Server é criado através da função ***nx_telnet_server_create.*** As ações típicas da chamada de "nova ligação" incluem ecoar os dados de volta e/ou analisar os dados e fornecer dados como resultado da interpretação de um comando do cliente.

Note que esta rotina de retorno também deve libertar o pacote fornecido.

### <a name="prototype"></a>Prototype

```c
void  telnet_receive_data(NX_TELNET_SERVER *server_ptr, 
                          UINT logical_connection, NX_PACKET *packet_ptr);
```
### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr**: Ponteiro para o chamado Telnet Server.
- **logical_connection**: A ligação lógica interna para o Servidor Telnet. Isto pode ser usado pela aplicação como um índice em tampãos e/ou estruturas de dados específicas para cada ligação do Cliente. O seu valor varia entre 0 e NX_TELNET_MAX_CLIENTS - 1.
- **packet_ptr**: Ponteiro para pacote que contém os dados do Cliente.

## <a name="telnet-end-connection-callback"></a>Chamada de ligação telnet end

O NetX Duo Telnet Server chama a função de retorno especificado da aplicação sempre que um Cliente Telnet termina a ligação. A aplicação especifica a função de retorno quando o Telnet Server é criado através da função ***nx_telnet_server_create.*** As ações típicas da chamada de "ligação final" incluem a limpeza de quaisquer estruturas de dados específicas do Cliente associadas à ligação lógica.

### <a name="prototype"></a>Prototype
```c
void  telnet_end_connection(NX_TELNET_SERVER *server_ptr, 
                            UINT logical_connection);
```

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr** Ponteiro para o chamado Telnet Server.
- **logical_connection** A ligação lógica interna para o Servidor Telnet. Isto pode ser usado pela aplicação como um índice em tampãos e/ou estruturas de dados específicas para cada ligação do Cliente. O seu valor varia entre 0 e NX_TELNET_MAX_CLIENTS - 1.

## <a name="telnet-option-negotiation"></a>Negociação de Opção Telnet

O NetX Duo Telnet Server suporta um conjunto limitado de opções Telnet, Echo e Suppress Go Ahead.

Para ativar esta característica, o NX_TELNET_SERVER_OPTION_DISABLE não deve ser definido. Por defeito não está definido. O Telnet Server cria um pacote de pacotes no serviço *nx_telnet_server_create* a partir do qual atribui pacotes para envio de pedidos de opções telnet ao Cliente. Consulte "Opções de Configuração" para definir a carga útil do pacote (NX_TELNET_SERVER_PACKET_PAYLOAD) e o tamanho da piscina do pacote (NX_TELNET_SERVER_PACKET_POOL_SIZE) para este pacote. Eliminará este pacote quando o serviço *nx_telnet_server_delete* for chamado.

Ao estabelecer uma ligação com o Cliente Telnet, enviará este conjunto de opções telnet ao Cliente se não tiver recebido pedidos de opção do Cliente:

- vai ecoar
- não ecoar
- vai sga

Quando recebe dados telnet do Cliente, o Telnet Server verifica se o primeiro byte é o código "IAC". Em caso afirmativo, processará todas as opções no pacote Cliente. As opções que não constam da lista acima são ignoradas.

Por predefinição, o Telnet Server cria o seu próprio pool de pacotes internos se NX_TELNET_SERVER_OPTION_DISABLE não estiver definido e precisar de transmitir comandos de opção Telnet. A piscina de pacotes Telnet Server é definida por NX_TELNET_SERVER_PACKET_PAYLOAD e NX_TELNET_SERVER_PACKET_POOLSIZE. Se, no entanto, NX_TELNET_SERVER_USER_CREATE_PACKET_POOL for definida, a aplicação deve criar a piscina de pacotes telnet Server e defini-la como a piscina de pacotes do Telnet Server chamando *_nx_telnet_server_packet_pool_set*. Consulte o capítulo 3 "Descrição dos Serviços Telnet" para obter mais detalhes sobre esta função.

Ao contrário do NetX Duo Telnet Server, o fio de tarefa do Cliente Telnet Duo NetX não envia e responde automaticamente às opções recebidas do Servidor Telnet. Isto deve ser feito pela aplicação Do Cliente Telnet.

## <a name="telnet-multi-thread-support"></a>Suporte multi-thread Telnet

Os serviços do Cliente NetX Duo Telnet podem ser chamados a partir de várias linhas simultaneamente. No entanto, ler ou escrever pedidos para uma determinada instância do Cliente Telnet deve ser feito em sequência a partir do mesmo fio.

## <a name="telnet-rfcs"></a>Telnet RFCs

NetX Duo Telnet está em conformidade com RFC854 e RFCs relacionados.
