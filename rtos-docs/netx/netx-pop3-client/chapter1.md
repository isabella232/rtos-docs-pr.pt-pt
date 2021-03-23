---
title: Capítulo 1 - Introdução ao Cliente Azure RTOS NetX POP3
description: A Azure RTOS NETX POP3 Client API fornece um sistema de transporte de correio para pequenas estações de trabalho para aceder a gotas de correio do Cliente em Servidores POP3 para recuperar o correio do Cliente.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 135530f11f8f54acd6d093a05332056dbdc32be3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826671"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pop3-client"></a><span data-ttu-id="30b81-103">Capítulo 1 - Introdução ao Cliente Azure RTOS NetX POP3</span><span class="sxs-lookup"><span data-stu-id="30b81-103">Chapter 1 - Introduction to Azure RTOS NetX POP3 Client</span></span>

<span data-ttu-id="30b81-104">O Protocolo dos Correios Versão 3 (POP3) é um protocolo projetado para fornecer um sistema de transporte de correio para pequenas estações de trabalho para aceder a gotas de correio do Cliente em Servidores POP3 para recuperar o correio do Cliente.</span><span class="sxs-lookup"><span data-stu-id="30b81-104">The Post Office Protocol Version 3 (POP3) is a protocol designed to provide a mail transport system for small workstations to access Client maildrops on POP3 Servers for retrieving Client mail.</span></span> <span data-ttu-id="30b81-105">POP3 utiliza serviços de Protocolo de Controlo de Transmissão (TCP) para realizar transferência de correio.</span><span class="sxs-lookup"><span data-stu-id="30b81-105">POP3 utilizes Transmission Control Protocol (TCP) services to perform mail transfer.</span></span> <span data-ttu-id="30b81-106">Por causa disso, pop3 é um protocolo de transferência de conteúdo altamente confiável.</span><span class="sxs-lookup"><span data-stu-id="30b81-106">Because of this, POP3 is a highly reliable content transfer protocol.</span></span>

<span data-ttu-id="30b81-107">No entanto, o POP3 não fornece operações extensivas no manuseamento de correio.</span><span class="sxs-lookup"><span data-stu-id="30b81-107">However, POP3 is does not provide extensive operations on mail handling.</span></span> <span data-ttu-id="30b81-108">Normalmente, o correio é descarregado pelo Cliente e depois eliminado da gota de correio do Servidor.</span><span class="sxs-lookup"><span data-stu-id="30b81-108">Typically, mail is downloaded by the Client and then deleted from the Server's maildrop.</span></span>

## <a name="netx-pop3-client-requirements"></a><span data-ttu-id="30b81-109">Requisitos do cliente NetX POP3</span><span class="sxs-lookup"><span data-stu-id="30b81-109">NetX POP3 Client Requirements</span></span>

### <a name="client-requirements"></a><span data-ttu-id="30b81-110">Requisitos do cliente</span><span class="sxs-lookup"><span data-stu-id="30b81-110">Client Requirements</span></span>

<span data-ttu-id="30b81-111">A Azure RTOS NetX POP3 Client API requer uma instância IP NetX previamente criada usando *nx_ip_create* e um pool de pacotes NetX previamente criado usando *nx_packet_pool_create*.</span><span class="sxs-lookup"><span data-stu-id="30b81-111">The Azure RTOS NetX POP3 Client API requires a previously created NetX IP instance using *nx_ip_create* and a previously created NetX packet pool using *nx_packet_pool_create*.</span></span> <span data-ttu-id="30b81-112">Uma vez que o Cliente NetX POP3 utiliza serviços TCP, o TCP deve ser ativado com a *chamada nx_tcp_enable* antes de utilizar os serviços do Cliente NetX POP3 nessa mesma instância IP.</span><span class="sxs-lookup"><span data-stu-id="30b81-112">Because the NetX POP3 Client utilizes TCP services, TCP must be enabled with the *nx_tcp_enable* call prior to using the NetX POP3 Client services on that same IP instance.</span></span> <span data-ttu-id="30b81-113">O Cliente POP3 utiliza uma tomada TCP para ligar a um Servidor POP3 na porta POP3 do servidor.</span><span class="sxs-lookup"><span data-stu-id="30b81-113">The POP3 Client uses a TCP socket to connect to a POP3 Server on the Server's POP3 port.</span></span> <span data-ttu-id="30b81-114">Isto é normalmente definido na *conhecida porta 110, embora nem o Cliente POP3 nem o Server sejam obrigados a utilizar esta porta.*</span><span class="sxs-lookup"><span data-stu-id="30b81-114">This is typically set at the *well-known port 110, though neither POP3 Client nor Server is required to use this port.*</span></span>

<span data-ttu-id="30b81-115">O tamanho do pacote de pacotes utilizado na criação do Cliente POP3 é configurável pelo utilizador em termos de carga útil de pacotes e número de pacotes disponíveis.</span><span class="sxs-lookup"><span data-stu-id="30b81-115">The size of the packet pool used in creating the POP3 Client is user configurable in terms of packet payload and number of packets available.</span></span> <span data-ttu-id="30b81-116">Se o pacote for utilizado apenas no serviço pop3 Cliente criar, a carga útil do pacote não deve ser superior a 100-120 bytes dependendo do comprimento do nome de utilizador e da palavra-passe, ou a APOP digest.</span><span class="sxs-lookup"><span data-stu-id="30b81-116">If the packet is used only in the POP3 Client create service, the packet payload need not be more than 100-120 bytes depending on the length of username and password, or APOP digest.</span></span> <span data-ttu-id="30b81-117">O comando USER com o nome de utilizador do anfitrião local é provavelmente a maior mensagem enviada pelo Cliente POP3.</span><span class="sxs-lookup"><span data-stu-id="30b81-117">The USER command with the local host's user name is probably the largest message sent by the POP3 Client.</span></span> <span data-ttu-id="30b81-118">É possível partilhar o mesmo conjunto de pacotes no nx_ip_create (pacote de pacotes ip predefinido) uma vez que as operações internas de IP não requerem uma carga útil muito grande para o envio e receção de dados de controlo TCP.</span><span class="sxs-lookup"><span data-stu-id="30b81-118">It is possible to share the same packet pool in the nx_ip_create (IP default packet pool) since the IP internal operations do not require a very large packet payload for sending and receiving TCP control data.</span></span>

<span data-ttu-id="30b81-119">No entanto, pode não ser vantajoso para o controlador de rede usar a mesma piscina de pacotes que a piscina de pacotes do Cliente POP3.</span><span class="sxs-lookup"><span data-stu-id="30b81-119">However, it may not be advantageous for the network driver to use the same packet pool as the POP3 Client packet pool.</span></span> <span data-ttu-id="30b81-120">Geralmente, a carga útil da carga do pool de receber é definida a instância IP MTU (normalmente 1500 bytes) da interface de rede que é muito maior do que as mensagens pop3 Cliente.</span><span class="sxs-lookup"><span data-stu-id="30b81-120">Generally, the payload of the receive packet pool payload is set the IP instance MTU (typically 1500 bytes) of the network interface which is much larger than POP3 Client messages.</span></span> <span data-ttu-id="30b81-121">As mensagens POP3 recebidas normalmente seriam dados muito maiores do que mensagens pop3 de saída</span><span class="sxs-lookup"><span data-stu-id="30b81-121">Incoming POP3 messages would usually be much larger data then outgoing POP3 Client messages</span></span>

## <a name="netx-pop3-client-creation"></a><span data-ttu-id="30b81-122">Criação de clientes NetX POP3</span><span class="sxs-lookup"><span data-stu-id="30b81-122">NetX POP3 Client Creation</span></span>

<span data-ttu-id="30b81-123">O Cliente POP3 cria o serviço, *nx_pop3_client_create* criar a tomada TCP e ligar-se ao servidor POP3.</span><span class="sxs-lookup"><span data-stu-id="30b81-123">The POP3 Client create service, *nx_pop3_client_create* create the TCP socket and connect with the POP3 server.</span></span>

<span data-ttu-id="30b81-124">Depois de se ligar ao servidor POP3, a aplicação DO Cliente POP3 pode ligar *para nx_pop3_client _mail_items_get* para obter o número de itens de correio sentados na sua caixa de correio:</span><span class="sxs-lookup"><span data-stu-id="30b81-124">After connecting with the POP3 server, the POP3 Client application can call *nx_pop3_client _mail_items_get* to obtain the number of mail items sitting in its maildrop box:</span></span>

```c
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
                                UINT *number_mail_items,
                                ULONG *maildrop_total_size)
```

<span data-ttu-id="30b81-125">Se um ou mais itens estiverem na gota de correio do Cliente, a aplicação pode obter o tamanho de um item de correio específico, utilizando o serviço *nx_pop3_client_get_mail_item:*</span><span class="sxs-lookup"><span data-stu-id="30b81-125">If one or more items are in the Client maildrop, the application can obtain the size of a specific mail item, using the *nx_pop3_client_get_mail_item* service:</span></span>

```c
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
                                UINT mail_item,
                                ULONG *item_size)
```

<span data-ttu-id="30b81-126">O primeiro item de correio na gota de correio está no índice 1.</span><span class="sxs-lookup"><span data-stu-id="30b81-126">The first mail item in the maildrop is at index 1.</span></span>

<span data-ttu-id="30b81-127">Para obter a mensagem de correio real, o pedido pode ligar para o serviço *nx_pop3_client_mail_item_get_message_data* para recuperar os pacotes de mensagens de correio até que o serviço indique que o último pacote é recebido pelo argumento de entrada final_packet:</span><span class="sxs-lookup"><span data-stu-id="30b81-127">To get the actual mail message, the application can call the *nx_pop3_client_mail_item_get_message_data* service to retrieve the mail message packets until the service indicates the last packet is received by the final_packet input argument:</span></span>

```c
UINT nx_pop3_client_mail_item_message_get(
                        NX_POP3_CLIENT *client_ptr,
                        NX_PACKET **recv_packet_ptr,
                        ULONG *bytes_retrieved,
                        UINT *final_packet)
```

<span data-ttu-id="30b81-128">Para eliminar um item de correio específico, a aplicação chama *nx_pop3_client_mail_item_delete* com o mesmo índice utilizado na *chamada nx_pop3_client_get_mail_item* anterior.</span><span class="sxs-lookup"><span data-stu-id="30b81-128">To delete a specific mail item, the application calls *nx_pop3_client_mail_item_delete* with the same index as used in the preceding *nx_pop3_client_get_mail_item* call.</span></span>

<span data-ttu-id="30b81-129">O Cliente pode ser eliminado usando o serviço *nx_pop3_client_delete.*</span><span class="sxs-lookup"><span data-stu-id="30b81-129">The Client can be deleted using the *nx_pop3_client_delete* service.</span></span> <span data-ttu-id="30b81-130">Note que cabe à aplicação eliminar o pacote de pacotes POP3 Client usando o serviço *nx_packet_pool_delete* já não tem qualquer utilidade para o mesmo.</span><span class="sxs-lookup"><span data-stu-id="30b81-130">Note it is up to the application to delete the POP3 Client packet pool using the *nx_packet_pool_delete* service there is no longer has any use for it.</span></span>

## <a name="netx-pop3-client-constraints"></a><span data-ttu-id="30b81-131">Restrições de clientes NetX POP3</span><span class="sxs-lookup"><span data-stu-id="30b81-131">NetX POP3 Client Constraints</span></span>

<span data-ttu-id="30b81-132">Existem alguns constrangimentos na implementação do Cliente NetX POP3:</span><span class="sxs-lookup"><span data-stu-id="30b81-132">There are some constraints in the NetX POP3 Client implementation:</span></span>

1. <span data-ttu-id="30b81-133">O Cliente NetX POP3 não suporta o comando AUTH, embora implemente a autenticação APOP utilizando o DIGEST-MD5 para a troca de autenticação do Servidor cliente.</span><span class="sxs-lookup"><span data-stu-id="30b81-133">The NetX POP3 Client does not support the AUTH command although it does implement APOP authentication using DIGEST-MD5 for the Client Server authentication exchange.</span></span>

1. <span data-ttu-id="30b81-134">NetX POP3 O Cliente não implementa todos os comandos POP3 (por exemplo, os comandos TOP ou UIDL).</span><span class="sxs-lookup"><span data-stu-id="30b81-134">NetX POP3 Client does not implement all POP3 commands (e.g. the TOP or UIDL commands).</span></span> <span data-ttu-id="30b81-135">Abaixo está uma lista de comandos que suporta:</span><span class="sxs-lookup"><span data-stu-id="30b81-135">Below is a list of commands it does support:</span></span>
   - <span data-ttu-id="30b81-136">NOOP</span><span class="sxs-lookup"><span data-stu-id="30b81-136">NOOP</span></span>
   - <span data-ttu-id="30b81-137">RSET</span><span class="sxs-lookup"><span data-stu-id="30b81-137">RSET</span></span>

## <a name="netx-pop3-client-login"></a><span data-ttu-id="30b81-138">Login de clientes NetX POP3</span><span class="sxs-lookup"><span data-stu-id="30b81-138">NetX POP3 Client Login</span></span>

<span data-ttu-id="30b81-139">Um Cliente NetX POP3 deve autenticar-se (login) num Servidor POP3 para aceder a uma gota de correio.</span><span class="sxs-lookup"><span data-stu-id="30b81-139">A NetX POP3 Client must authenticate itself (login) to a POP3 Server to access a maildrop.</span></span> <span data-ttu-id="30b81-140">Pode fazê-lo utilizando os comandos USER/PASS e fornecendo um nome de utilizador e palavra-passe conhecidos pelo Servidor POP3, ou utilizando o comando APOP e a digestão MD5 descritas abaixo.</span><span class="sxs-lookup"><span data-stu-id="30b81-140">It can do so either by using the USER/PASS commands and providing a username and password known to the POP3 Server, or by using the APOP command and MD5 digest described below.</span></span>

<span data-ttu-id="30b81-141">O nome de utilizador é tipicamente um nome de domínio totalmente qualificado (contém uma parte local e um nome de domínio, separado por um caracter '@').</span><span class="sxs-lookup"><span data-stu-id="30b81-141">The username is typically a fully qualified domain name (contains a local-part and a domain name, separated by an '@' character).</span></span> <span data-ttu-id="30b81-142">Ao utilizar os comandos POP3 USER e PASS, o Cliente está a enviar o seu nome de utilizador e palavra-passe desencriptados pela Internet.</span><span class="sxs-lookup"><span data-stu-id="30b81-142">When using the POP3 commands USER and PASS, the Client is sending its username and password unencrypted over the Internet.</span></span>

<span data-ttu-id="30b81-143">Para evitar o risco de segurança de um nome de utilizador e palavra-passe claros de texto, o Cliente NetX POP3 pode ser configurado para utilizar a autenticação APOP, definindo o parâmetro *APOP_authentication* no serviço *nx_pop3_client_create:*</span><span class="sxs-lookup"><span data-stu-id="30b81-143">To avoid the security risk of clear texting username and password, the NetX POP3 Client can be configured to use APOP authentication by setting the *APOP_authentication* parameter in the *nx_pop3_client_create* service:</span></span>

```c
UINT  nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                            UINT APOP_authentication,
                            NX_IP *ip_ptr,
                            NX_PACKET_POOL *packet_pool_ptr,
                            NXD_ADDRESS *server_ip_address, ULONG server_port,
                            CHAR *client_name,
                            CHAR *client_password)
```

<span data-ttu-id="30b81-144">Ou apenas para aplicações IPv4, o *serviço nx_pop3_client_create:*</span><span class="sxs-lookup"><span data-stu-id="30b81-144">Or for IPv4 only applications, the *nx_pop3_client_create* service:</span></span>

```c
UINT  nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                            UINT APOP_authentication,
                            NX_IP *ip_ptr,
                            NX_PACKET_POOL *packet_pool_ptr,
                            ULONG server_ip_address,
                            ULONG server_port, CHAR *client_name,
                            CHAR *client_password)
```

<span data-ttu-id="30b81-145">Quando o Cliente envia o comando APOP, é necessário uma digestão MD5 contendo o domínio do servidor, a hora local e o ID do processo extraído da saudação do Servidor, além da palavra-passe do Cliente.</span><span class="sxs-lookup"><span data-stu-id="30b81-145">When the Client sends the APOP command, it takes an MD5 digest containing the server domain, local time and process ID extracted from the Server greeting, plus the Client password.</span></span> <span data-ttu-id="30b81-146">O Servidor POP3 criará uma digestão MD5 contendo as mesmas informações e se a sua digestão MD5 corresponder à digestão MD5 do Cliente, o Cliente é autenticado.</span><span class="sxs-lookup"><span data-stu-id="30b81-146">The POP3 Server will create an MD5 digest containing the same information and if its MD5 digest matches the Client's MD5 digest, the Client is authenticated.</span></span>

<span data-ttu-id="30b81-147">Se a autenticação APOP falhar, o Cliente NetX POP3 tentará a autenticação USER/PASS.</span><span class="sxs-lookup"><span data-stu-id="30b81-147">If APOP authentication fails, NetX POP3 Client will attempt USER/PASS authentication.</span></span>

## <a name="the-pop3-client-maildrop"></a><span data-ttu-id="30b81-148">A gota de correio do cliente POP3</span><span class="sxs-lookup"><span data-stu-id="30b81-148">The POP3 Client Maildrop</span></span>

<span data-ttu-id="30b81-149">O correio eletrónico do cliente é armazenado num Servidor POP3 numa caixa de correio ou "maildrop".</span><span class="sxs-lookup"><span data-stu-id="30b81-149">Client mail is stored on a POP3 Server in a mailbox or "maildrop."</span></span> <span data-ttu-id="30b81-150">Uma gota de correio do Cliente num Servidor POP3 é representada como uma lista baseada em 1 itens de correio.</span><span class="sxs-lookup"><span data-stu-id="30b81-150">A Client maildrop on a POP3 Server is represented as a 1 based list of mail items.</span></span> <span data-ttu-id="30b81-151">Ou seja, cada correio é referido pelo seu índice na lista de correio com o primeiro item de correio no índice 1 (não zero).</span><span class="sxs-lookup"><span data-stu-id="30b81-151">That is, each mail is referred to by its index in the maildrop list with the first mail item at index 1 (not zero).</span></span> <span data-ttu-id="30b81-152">Os comandos POP3 referem-se a itens de correio específicos pelo seu índice nesta lista.</span><span class="sxs-lookup"><span data-stu-id="30b81-152">POP3 commands refer to specific mail items by their index in this list.</span></span>

## <a name="the-pop3-protocol-state-machine"></a><span data-ttu-id="30b81-153">A máquina estatal do protocolo POP3</span><span class="sxs-lookup"><span data-stu-id="30b81-153">The POP3 Protocol State Machine</span></span>

<span data-ttu-id="30b81-154">O protocolo POP3 requer que tanto o Cliente como o Servidor mantenham o estado da sessão POP3.</span><span class="sxs-lookup"><span data-stu-id="30b81-154">The POP3 protocol requires that both Client and Server maintain the state of the POP3 session.</span></span> <span data-ttu-id="30b81-155">Primeiro, o Cliente tenta ligar-se ao Servidor POP3.</span><span class="sxs-lookup"><span data-stu-id="30b81-155">First, the Client attempts to connect to the POP3 Server.</span></span> <span data-ttu-id="30b81-156">Se for bem sucedido, entra no protocolo POP3 que tem três estados distintos definidos pelo RFC 1939.</span><span class="sxs-lookup"><span data-stu-id="30b81-156">If successful it enters into the POP3 protocol which has three distinct states defined by RFC 1939.</span></span> <span data-ttu-id="30b81-157">O estado inicial é o estado de autorização no qual deve identificar-se ao Servidor.</span><span class="sxs-lookup"><span data-stu-id="30b81-157">The initial state is the Authorization state in which it must identify itself to the Server.</span></span> <span data-ttu-id="30b81-158">No estado de Autorização, o Cliente POP3 só pode emitir comandos USER e PASS, e por essa ordem, ou o comando APOP.</span><span class="sxs-lookup"><span data-stu-id="30b81-158">In the Authorization state, the POP3 Client can only issue the USER and the PASS commands, and in that order, or the APOP command.</span></span>

<span data-ttu-id="30b81-159">Uma vez autenticado o Cliente POP3, a sessão de Cliente entra no estado de Transação.</span><span class="sxs-lookup"><span data-stu-id="30b81-159">Once the POP3 Client is authenticated, the Client session enters the Transaction state.</span></span> <span data-ttu-id="30b81-160">Neste estado, o Cliente pode descarregar e solicitar a eliminação de correio.</span><span class="sxs-lookup"><span data-stu-id="30b81-160">In this state, the Client can download and request mail deletion.</span></span> <span data-ttu-id="30b81-161">Os comandos permitidos no estado de Transação são LIST, STAT, RETR, DELE, RSET e QUIT.</span><span class="sxs-lookup"><span data-stu-id="30b81-161">The commands allowed in the Transaction state are LIST, STAT, RETR, DELE, RSET and QUIT.</span></span> <span data-ttu-id="30b81-162">Normalmente, o Cliente POP3 envia um comando STAT seguido de uma série de comandos RETR (um para cada item de correio na sua gota de correio).</span><span class="sxs-lookup"><span data-stu-id="30b81-162">Typically the POP3 Client sends a STAT command followed by a series of RETR commands (one for each mail item in its maildrop).</span></span>

<span data-ttu-id="30b81-163">Uma vez que o Cliente emite o comando QUIT, a sessão POP3 entra no estado de Atualização em que inicia a desconexão TCP do Servidor.</span><span class="sxs-lookup"><span data-stu-id="30b81-163">Once the Client issues the QUIT command, the POP3 session enters the Update state in which it initiates the TCP disconnect from the Server.</span></span> <span data-ttu-id="30b81-164">Para baixar o correio mais tarde, a aplicação do Cliente POP3 pode ligar `nx_pop3_client_mail_items_get` a qualquer momento para verificar se há novo correio na gota de correio.</span><span class="sxs-lookup"><span data-stu-id="30b81-164">To download mail later, the POP3 Client application may call `nx_pop3_client_mail_items_get` at any time to check for new mail in the maildrop.</span></span>

### <a name="pop3-server-reply-codes"></a><span data-ttu-id="30b81-165">Códigos de resposta do servidor POP3</span><span class="sxs-lookup"><span data-stu-id="30b81-165">POP3 Server Reply Codes</span></span>

- <span data-ttu-id="30b81-166">**+OK**: O Servidor utiliza esta resposta para aceitar um comando do Cliente.</span><span class="sxs-lookup"><span data-stu-id="30b81-166">**+OK**: The Server uses this reply to accept a Client command.</span></span> <span data-ttu-id="30b81-167">O Servidor pode incluir informações adicionais após o '+OK' mas não pode assumir que o Cliente irá processar esta informação, exceto no caso de descarregar dados de mensagens de correio ou os comandos LIST ou DELE.</span><span class="sxs-lookup"><span data-stu-id="30b81-167">The Server can include additional information after the '+OK' but cannot assume the Client will process this information, except in the case of downloading mail message data or the LIST or DELE commands.</span></span> <span data-ttu-id="30b81-168">Neste último caso, o 'argumento' após o comando refere o índice do item de correio na gota de correio do Cliente.</span><span class="sxs-lookup"><span data-stu-id="30b81-168">In the latter case, the 'argument' after the command references the index of the mail item in the Client maildrop.</span></span>

- <span data-ttu-id="30b81-169">**-ERR**: O Servidor utiliza esta resposta para rejeitar um comando do Cliente.</span><span class="sxs-lookup"><span data-stu-id="30b81-169">**-ERR**: The Server uses this reply to reject a Client command.</span></span> <span data-ttu-id="30b81-170">O Servidor pode enviar informações adicionais após o 'ERR' mas não pode assumir que o Cliente irá processar esta informação.</span><span class="sxs-lookup"><span data-stu-id="30b81-170">The Server may send additional information following the '-ERR' but cannot assume the Client will process this information.</span></span>

### <a name="sample-pop3-client---server-session"></a><span data-ttu-id="30b81-171">Amostra do cliente POP3 - Sessão de Servidor</span><span class="sxs-lookup"><span data-stu-id="30b81-171">Sample POP3 Client - Server Session</span></span>

<span data-ttu-id="30b81-172">**Exemplo pop3 básico utilizando USER/PASS:**</span><span class="sxs-lookup"><span data-stu-id="30b81-172">**Basic POP3 example using USER/PASS:**</span></span>

```c
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

<span data-ttu-id="30b81-173">**Exemplo pop3 básico usando APOP (e LIST em vez de STAT):**</span><span class="sxs-lookup"><span data-stu-id="30b81-173">**Basic POP3 example using APOP (and LIST instead of STAT):**</span></span>

```c
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

## <a name="rfcs-supported-by-netx-pop3-client"></a><span data-ttu-id="30b81-174">RFCs Suportados pelo Cliente NetX POP3</span><span class="sxs-lookup"><span data-stu-id="30b81-174">RFCs Supported by NetX POP3 Client</span></span>

<span data-ttu-id="30b81-175">O Cliente NetX POP3 está em conformidade com o RFC 1939.</span><span class="sxs-lookup"><span data-stu-id="30b81-175">NetX Client POP3 is compliant with RFC 1939.</span></span>
