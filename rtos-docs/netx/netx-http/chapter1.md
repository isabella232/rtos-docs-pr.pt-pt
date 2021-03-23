---
title: Capítulo 1 - Introdução ao NetX HTTP
description: Este documento explicará como o HTTP é um protocolo concebido para transferir conteúdo na Web.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6137cc0d8deb753d784be844d5abc7778dd62295
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826719"
---
# <a name="chapter-1---introduction-to-netx-http"></a><span data-ttu-id="6e83a-103">Capítulo 1 - Introdução ao NetX HTTP</span><span class="sxs-lookup"><span data-stu-id="6e83a-103">Chapter 1 - Introduction to NetX HTTP</span></span>

<span data-ttu-id="6e83a-104">O Protocolo de Transferência de Hipertextos (HTTP) é um protocolo concebido para transferir conteúdo na Web.</span><span class="sxs-lookup"><span data-stu-id="6e83a-104">The Hypertext Transfer Protocol (HTTP) is a protocol designed for transferring content on the Web.</span></span> <span data-ttu-id="6e83a-105">HTTP é um protocolo simples que utiliza serviços fiáveis de Protocolo de Controlo de Transmissão (TCP) para executar a sua função de transferência de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="6e83a-105">HTTP is a simple protocol that utilizes reliable Transmission Control Protocol (TCP) services to perform its content transfer function.</span></span> <span data-ttu-id="6e83a-106">Por isso, HTTP é um protocolo de transferência de conteúdo altamente fiável.</span><span class="sxs-lookup"><span data-stu-id="6e83a-106">Because of this, HTTP is a highly reliable content transfer protocol.</span></span> <span data-ttu-id="6e83a-107">HTTP é um dos protocolos de aplicação mais utilizados.</span><span class="sxs-lookup"><span data-stu-id="6e83a-107">HTTP is one of the most used application protocols.</span></span> <span data-ttu-id="6e83a-108">Todas as operações na Web utilizam o protocolo HTTP.</span><span class="sxs-lookup"><span data-stu-id="6e83a-108">All operations on the Web utilize the HTTP protocol.</span></span>

## <a name="http-requirements"></a><span data-ttu-id="6e83a-109">Requisitos HTTP</span><span class="sxs-lookup"><span data-stu-id="6e83a-109">HTTP Requirements</span></span>

<span data-ttu-id="6e83a-110">Para funcionar corretamente, o pacote NetX HTTP requer a instalação de um NetX (versão 5.2 ou posterior).</span><span class="sxs-lookup"><span data-stu-id="6e83a-110">In order to function properly, the NetX HTTP package requires that a NetX (version 5.2 or later) is installed.</span></span> <span data-ttu-id="6e83a-111">Além disso, já deve ser criada uma instância IP e a TCP deve ser ativada nessa mesma instância de PI.</span><span class="sxs-lookup"><span data-stu-id="6e83a-111">In addition, an IP instance must already be created and TCP must be enabled on that same IP instance.</span></span> <span data-ttu-id="6e83a-112">O ficheiro de demonstração na secção "Small Example System" **do Capítulo 2** demonstrará como isto é feito.</span><span class="sxs-lookup"><span data-stu-id="6e83a-112">The demo file in section “Small Example System” in **Chapter 2** will demonstrate how this is done.</span></span>

<span data-ttu-id="6e83a-113">A parte do cliente HTTP do pacote NetX HTTP não tem outros requisitos.</span><span class="sxs-lookup"><span data-stu-id="6e83a-113">The HTTP Client portion of the NetX HTTP package has no further requirements.</span></span>

<span data-ttu-id="6e83a-114">A parte do servidor HTTP do pacote NetX HTTP tem vários requisitos adicionais.</span><span class="sxs-lookup"><span data-stu-id="6e83a-114">The HTTP Server portion of the NetX HTTP package has several additional requirements.</span></span> <span data-ttu-id="6e83a-115">Em primeiro lugar, requer acesso completo à porta *80 bem conhecida* da TCP para o tratamento de todos os pedidos HTTP do Cliente.</span><span class="sxs-lookup"><span data-stu-id="6e83a-115">First, it requires complete access to TCP *well-known port 80* for handling all Client HTTP requests.</span></span> <span data-ttu-id="6e83a-116">O servidor HTTP também foi concebido para ser utilizado com o sistema de ficheiros incorporado FileX.</span><span class="sxs-lookup"><span data-stu-id="6e83a-116">The HTTP Server is also designed for use with the FileX embedded file system.</span></span> <span data-ttu-id="6e83a-117">Se o FileX não estiver disponível, o utilizador pode apresentar as porções do FileX utilizadas para o seu próprio ambiente.</span><span class="sxs-lookup"><span data-stu-id="6e83a-117">If FileX is not available, the user may port the portions of FileX used to their own environment.</span></span> <span data-ttu-id="6e83a-118">Isto é discutido em secções posteriores deste guia.</span><span class="sxs-lookup"><span data-stu-id="6e83a-118">This is discussed in later sections of this guide.</span></span>

## <a name="http-constraints"></a><span data-ttu-id="6e83a-119">Restrições HTTP</span><span class="sxs-lookup"><span data-stu-id="6e83a-119">HTTP Constraints</span></span> 

<span data-ttu-id="6e83a-120">O protocolo NetX HTTP implementa a norma HTTP 1.0.</span><span class="sxs-lookup"><span data-stu-id="6e83a-120">The NetX HTTP protocol implements the HTTP 1.0 standard.</span></span> <span data-ttu-id="6e83a-121">No entanto, existem os seguintes constrangimentos:</span><span class="sxs-lookup"><span data-stu-id="6e83a-121">However, there are following constraints:</span></span>

1.  <span data-ttu-id="6e83a-122">As ligações persistentes não são suportadas</span><span class="sxs-lookup"><span data-stu-id="6e83a-122">Persistent connections are not supported</span></span>

2.  <span data-ttu-id="6e83a-123">Solicitação de pipelining não é suportado</span><span class="sxs-lookup"><span data-stu-id="6e83a-123">Request pipelining is not supported</span></span>

3.  <span data-ttu-id="6e83a-124">O SERVIDOR HTTP suporta a autenticação básica e mD5, mas não mD5-sess.</span><span class="sxs-lookup"><span data-stu-id="6e83a-124">The HTTP Server supports both basic and MD5 digest authentication, but not MD5-sess.</span></span> <span data-ttu-id="6e83a-125">Atualmente, o Cliente HTTP suporta apenas a autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="6e83a-125">At present, the HTTP Client supports only basic authentication.</span></span>

4.  <span data-ttu-id="6e83a-126">Não é suportada qualquer compressão de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="6e83a-126">No content compression is supported.</span></span>

5.  <span data-ttu-id="6e83a-127">Os pedidos TRACE, OPTIONS e CONNECT não são suportados.</span><span class="sxs-lookup"><span data-stu-id="6e83a-127">TRACE, OPTIONS, and CONNECT requests are not supported.</span></span>

6.  <span data-ttu-id="6e83a-128">O conjunto de pacotes associado ao servidor http ou cliente deve ser grande o suficiente para segurar o cabeçalho HTTP completo.</span><span class="sxs-lookup"><span data-stu-id="6e83a-128">The packet pool associated with the HTTP Server or Client must be large enough to hold the complete HTTP header.</span></span>

7.  <span data-ttu-id="6e83a-129">HTTP Os serviços do cliente são apenas para transferência de conteúdos - não existem utilitários de exibição fornecidos neste pacote.</span><span class="sxs-lookup"><span data-stu-id="6e83a-129">HTTP Client services are for content transfer only—there are no display utilities provided in this package.</span></span>

## <a name="http-url-resource-names"></a><span data-ttu-id="6e83a-130">URL HTTP (Nomes de Recursos)</span><span class="sxs-lookup"><span data-stu-id="6e83a-130">HTTP URL (Resource Names)</span></span>

<span data-ttu-id="6e83a-131">O protocolo HTTP foi concebido para transferir conteúdo na Web.</span><span class="sxs-lookup"><span data-stu-id="6e83a-131">The HTTP protocol is designed to transfer content on Web.</span></span> <span data-ttu-id="6e83a-132">O conteúdo solicitado é especificado pelo Localizador de Recursos Universais (URL).</span><span class="sxs-lookup"><span data-stu-id="6e83a-132">The requested content is specified by the Universal Resource Locator (URL).</span></span> <span data-ttu-id="6e83a-133">Este é o componente principal de cada pedido HTTP.</span><span class="sxs-lookup"><span data-stu-id="6e83a-133">This is the primary component of every HTTP request.</span></span> <span data-ttu-id="6e83a-134">Os URLs começam sempre com um caracteres "/" e normalmente correspondem a ficheiros no servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="6e83a-134">URLs always start with a “/” character and typically correspond to files on the HTTP Server.</span></span> <span data-ttu-id="6e83a-135">As extensões de ficheiros HTTP comuns são apresentadas abaixo:</span><span class="sxs-lookup"><span data-stu-id="6e83a-135">Common HTTP file extensions are shown below:</span></span>

- <span data-ttu-id="6e83a-136">**.htm (ou .html)** Linguagem de marcação de hipertexto (HTML)</span><span class="sxs-lookup"><span data-stu-id="6e83a-136">**.htm (or .html)** Hypertext Markup Language (HTML)</span></span>
- <span data-ttu-id="6e83a-137">**.txt** Texto simples ASCII</span><span class="sxs-lookup"><span data-stu-id="6e83a-137">**.txt** Plain ASCII text</span></span>
- <span data-ttu-id="6e83a-138">**.gif** Imagem binária do GIF</span><span class="sxs-lookup"><span data-stu-id="6e83a-138">**.gif** Binary GIF image</span></span>
- <span data-ttu-id="6e83a-139">**.xbm** Imagem binária de Xbitmap</span><span class="sxs-lookup"><span data-stu-id="6e83a-139">**.xbm** Binary Xbitmap image</span></span>

## <a name="http-client-requests"></a><span data-ttu-id="6e83a-140">Pedidos de clientes HTTP</span><span class="sxs-lookup"><span data-stu-id="6e83a-140">HTTP Client Requests</span></span>

<span data-ttu-id="6e83a-141">O HTTP tem um mecanismo simples para solicitar conteúdo web.</span><span class="sxs-lookup"><span data-stu-id="6e83a-141">The HTTP has a simple mechanism for requesting Web content.</span></span> <span data-ttu-id="6e83a-142">Existe basicamente um conjunto de comandos HTTP padrão que são emitidos pelo Cliente depois de uma ligação ter sido estabelecida com sucesso na *porta 80 bem conhecida* da TCP .</span><span class="sxs-lookup"><span data-stu-id="6e83a-142">There is basically a set of standard HTTP commands that are issued by the Client after a connection has been successfully established on the TCP *well-known port 80*.</span></span> <span data-ttu-id="6e83a-143">O seguinte mostra alguns dos comandos HTTP básicos:</span><span class="sxs-lookup"><span data-stu-id="6e83a-143">The following shows some of the basic HTTP commands:</span></span>

- <span data-ttu-id="6e83a-144">Obter recurso HTTP/1.0 *Obtenha o recurso especificado*</span><span class="sxs-lookup"><span data-stu-id="6e83a-144">GET resource HTTP/1.0 *Get the specified resource*</span></span>
- <span data-ttu-id="6e83a-145">RECURSO POST HTTP/1.0 *Obtenha o recurso especificado e passe a entrada anexa ao Servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="6e83a-145">POST resource HTTP/1.0 *Get the specified resource and pass attached input to the HTTP Server*</span></span>
- <span data-ttu-id="6e83a-146">Recurso HEAD HTTP/1.0 *Tratado como um GET mas não conteúdo é devolvido pelo servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="6e83a-146">HEAD resource HTTP/1.0 *Treated like a GET but not content is returned by the HTTP Server*</span></span>
- <span data-ttu-id="6e83a-147">Colocar recurso HTTP/1.0 *Coloque o recurso no servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="6e83a-147">PUT resource HTTP/1.0 *Place resource on HTTP Server*</span></span>
- <span data-ttu-id="6e83a-148">EXCLUIR recurso HTTP/1.0 *Eliminar recurso no Servidor*</span><span class="sxs-lookup"><span data-stu-id="6e83a-148">DELETE resource HTTP/1.0 *Delete resource on the Server*</span></span>

<span data-ttu-id="6e83a-149">Estes comandos ASCII são gerados internamente pelos navegadores Web e pelos serviços do Cliente NetX HTTP para realizar operações HTTP com um Servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="6e83a-149">These ASCII commands are generated internally by Web browsers and the NetX HTTP Client services to perform HTTP operations with an HTTP Server.</span></span>

>[!NOTE] 
> <span data-ttu-id="6e83a-150">A aplicação http cliente padrão para a porta de ligação de 80.</span><span class="sxs-lookup"><span data-stu-id="6e83a-150">The HTTP Client application default to the connect port of 80.</span></span> <span data-ttu-id="6e83a-151">No entanto, pode alterar a porta de ligação para o servidor HTTP em tempo de execução utilizando o serviço *nx_http_client_set_connect_port.*</span><span class="sxs-lookup"><span data-stu-id="6e83a-151">However, it can change the connect port to the HTTP Server at runtime using the *nx_http_client_set_connect_port* service.</span></span> <span data-ttu-id="6e83a-152">Consulte o Capítulo 4 para mais detalhes sobre este serviço.</span><span class="sxs-lookup"><span data-stu-id="6e83a-152">See Chapter 4 for more details of this service.</span></span> <span data-ttu-id="6e83a-153">Isto é para acomodar servidores web que ocasionalmente usam portas alternativas para ligações ao Cliente.</span><span class="sxs-lookup"><span data-stu-id="6e83a-153">This is to accommodate web servers that occasionally use alternate ports for Client connections.</span></span>

## <a name="http-server-responses"></a><span data-ttu-id="6e83a-154">RESPOSTAS HTTP Servidor</span><span class="sxs-lookup"><span data-stu-id="6e83a-154">HTTP Server Responses</span></span>

<span data-ttu-id="6e83a-155">O Servidor HTTP utiliza a mesma *conhecida porta TCP 80* para enviar respostas de comando do Cliente.</span><span class="sxs-lookup"><span data-stu-id="6e83a-155">The HTTP Server utilizes the same *well-known TCP port 80* to send Client command responses.</span></span> <span data-ttu-id="6e83a-156">Uma vez que o servidor HTTP processa o comando do Cliente, retorna uma cadeia de resposta ASCII que inclui um código de estado numérico de 3 dígitos.</span><span class="sxs-lookup"><span data-stu-id="6e83a-156">Once the HTTP Server processes the Client command, it returns an ASCII response string that includes a 3-digit numeric status code.</span></span> <span data-ttu-id="6e83a-157">A resposta numérica é utilizada pelo software HTTP Client para determinar se a operação foi bem sucedida ou falhou.</span><span class="sxs-lookup"><span data-stu-id="6e83a-157">The numeric response is used by the HTTP Client software to determine whether the operation succeeded or failed.</span></span> <span data-ttu-id="6e83a-158">Segue-se uma lista de várias respostas do servidor HTTP aos comandos do Cliente:</span><span class="sxs-lookup"><span data-stu-id="6e83a-158">Following is a list of various HTTP Server responses to Client commands:</span></span>

- <span data-ttu-id="6e83a-159">200 *Pedido foi bem sucedido*</span><span class="sxs-lookup"><span data-stu-id="6e83a-159">200 *Request was successful*</span></span>
- <span data-ttu-id="6e83a-160">400 *Pedido não foi formado corretamente*</span><span class="sxs-lookup"><span data-stu-id="6e83a-160">400 *Request was not formed properly*</span></span>
- <span data-ttu-id="6e83a-161">401 *Pedido não autorizado, o cliente precisa enviar autenticação*</span><span class="sxs-lookup"><span data-stu-id="6e83a-161">401 *Unauthorized request, client needs to send authentication*</span></span>
- <span data-ttu-id="6e83a-162">404 *Não foi encontrado recurso especificado a pedido*</span><span class="sxs-lookup"><span data-stu-id="6e83a-162">404 *Specified resource in request was not found*</span></span>
- <span data-ttu-id="6e83a-163">500 *Erro interno do servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="6e83a-163">500 *Internal HTTP Server error*</span></span>
- <span data-ttu-id="6e83a-164">501 *Pedido não implementado pelo SERVIDOR HTTP*</span><span class="sxs-lookup"><span data-stu-id="6e83a-164">501 *Request not implemented by HTTP Server*</span></span>
- <span data-ttu-id="6e83a-165">Serviço 502 *não está disponível*</span><span class="sxs-lookup"><span data-stu-id="6e83a-165">502 *Service is not available*</span></span>

<span data-ttu-id="6e83a-166">Por exemplo, um pedido bem sucedido do Cliente para colocar o ficheiro "test.htm" é respondido com a mensagem "HTTP/1.0 200 OK".</span><span class="sxs-lookup"><span data-stu-id="6e83a-166">For example, a successful Client request to PUT the file “test.htm” is responded with the message “HTTP/1.0 200 OK.”</span></span>

## <a name="http-communication"></a><span data-ttu-id="6e83a-167">Comunicação HTTP</span><span class="sxs-lookup"><span data-stu-id="6e83a-167">HTTP Communication</span></span>

<span data-ttu-id="6e83a-168">Como mencionado anteriormente, o SERVIDOR HTTP utiliza a *conhecida porta TCP 80* para fazer os pedidos do Cliente em campo.</span><span class="sxs-lookup"><span data-stu-id="6e83a-168">As mentioned previously, the HTTP Server utilizes the *well-known TCP port 80* to field Client requests.</span></span> <span data-ttu-id="6e83a-169">HTTP Os clientes podem utilizar qualquer porta TCP disponível.</span><span class="sxs-lookup"><span data-stu-id="6e83a-169">HTTP Clients may use any available TCP port.</span></span> <span data-ttu-id="6e83a-170">A sequência geral dos eventos HTTP é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="6e83a-170">The general sequence of HTTP events is as follows:</span></span>

<span data-ttu-id="6e83a-171">**HTTP GET Request**:</span><span class="sxs-lookup"><span data-stu-id="6e83a-171">**HTTP GET Request**:</span></span>

1.  <span data-ttu-id="6e83a-172">O cliente emite A TCP liga-se à porta do Servidor 80.</span><span class="sxs-lookup"><span data-stu-id="6e83a-172">Client issues TCP connect to Server port 80.</span></span>

2.  <span data-ttu-id="6e83a-173">O cliente envia o pedido **de " GET resource HTTP/1.0**" (juntamente com outras informações do cabeçalho).</span><span class="sxs-lookup"><span data-stu-id="6e83a-173">Client sends “**GET resource HTTP/1.0**” request (along with other header information).</span></span>

3.  <span data-ttu-id="6e83a-174">O servidor constrói uma mensagem "**HTTP/1.0 200 OK**" com informações adicionais seguidas imediatamente pelo conteúdo do recurso (se houver).</span><span class="sxs-lookup"><span data-stu-id="6e83a-174">Server builds an “**HTTP/1.0 200 OK**” message with additional information followed immediately by the resource content (if any).</span></span>

4.  <span data-ttu-id="6e83a-175">O servidor executa uma desconexão.</span><span class="sxs-lookup"><span data-stu-id="6e83a-175">Server performs a disconnection.</span></span>

5.  <span data-ttu-id="6e83a-176">O cliente realiza uma desconexão.</span><span class="sxs-lookup"><span data-stu-id="6e83a-176">Client performs a disconnection.</span></span>

<span data-ttu-id="6e83a-177">**HTTP PUT Request**:</span><span class="sxs-lookup"><span data-stu-id="6e83a-177">**HTTP PUT Request**:</span></span>

1. <span data-ttu-id="6e83a-178">O cliente emite A TCP liga-se à porta do Servidor 80.</span><span class="sxs-lookup"><span data-stu-id="6e83a-178">Client issues TCP connect to Server port 80.</span></span>

2. <span data-ttu-id="6e83a-179">O cliente envia o pedido de "**PUT Resource HTTP/1.0**", juntamente com outras informações do cabeçalho, e seguido pelo conteúdo do recurso.</span><span class="sxs-lookup"><span data-stu-id="6e83a-179">Client sends “**PUT resource HTTP/1.0**” request, along with other header information, and followed by the resource content.</span></span>

3. <span data-ttu-id="6e83a-180">O servidor constrói uma mensagem "**HTTP/1.0 200 OK**" com informações adicionais seguidas imediatamente pelo conteúdo do recurso.</span><span class="sxs-lookup"><span data-stu-id="6e83a-180">Server builds an “**HTTP/1.0 200 OK**” message with additional information followed immediately by the resource content.</span></span>

4. <span data-ttu-id="6e83a-181">O servidor executa uma desconexão.</span><span class="sxs-lookup"><span data-stu-id="6e83a-181">Server performs a disconnection.</span></span>

5. <span data-ttu-id="6e83a-182">O cliente realiza uma desconexão.</span><span class="sxs-lookup"><span data-stu-id="6e83a-182">Client performs a disconnection.</span></span>

>[!NOTE] 
> <span data-ttu-id="6e83a-183">Como mencionado anteriormente, o Cliente HTTP pode alterar a porta de ligação padrão de 80 para outra porta usando o *nx_http_client_set_connect_port* para servidores web que usam portas alternativas para se conectarem aos clientes.</span><span class="sxs-lookup"><span data-stu-id="6e83a-183">As mentioned previously, the HTTP Client can change the default connect port from 80 to another port using the *nx_http_client_set_connect_port* for web servers that use alternate ports to connect to clients.</span></span>

## <a name="http-authentication"></a><span data-ttu-id="6e83a-184">Autenticação HTTP</span><span class="sxs-lookup"><span data-stu-id="6e83a-184">HTTP Authentication</span></span>

<span data-ttu-id="6e83a-185">A autenticação HTTP é opcional e não é necessária para todos os pedidos da Web.</span><span class="sxs-lookup"><span data-stu-id="6e83a-185">HTTP authentication is optional and isn’t required for all Web requests.</span></span> <span data-ttu-id="6e83a-186">Existem dois sabores de autenticação, nomeadamente *básicos* e *digeridos.*</span><span class="sxs-lookup"><span data-stu-id="6e83a-186">There are two flavors of authentication, namely *basic* and *digest*.</span></span> <span data-ttu-id="6e83a-187">A autenticação básica é equivalente ao *nome* e autenticação *de senha* encontrado em muitos protocolos.</span><span class="sxs-lookup"><span data-stu-id="6e83a-187">Basic authentication is equivalent to the *name* and *password* authentication found in many protocols.</span></span> <span data-ttu-id="6e83a-188">Na autenticação básica HTTP, o nome e as palavras-passe são concatenados e codificados no formato base64.</span><span class="sxs-lookup"><span data-stu-id="6e83a-188">In HTTP basic authentication, the name and passwords are concatenated and encoded in the base64 format.</span></span> <span data-ttu-id="6e83a-189">A principal desvantagem da autenticação básica é o nome e a palavra-passe são transmitidas abertamente no pedido.</span><span class="sxs-lookup"><span data-stu-id="6e83a-189">The main disadvantage of basic authentication is the name and password are transmitted openly in the request.</span></span> <span data-ttu-id="6e83a-190">Isto torna um pouco fácil para o nome e a senha serem roubados.</span><span class="sxs-lookup"><span data-stu-id="6e83a-190">This makes it somewhat easy for the name and password to be stolen.</span></span> <span data-ttu-id="6e83a-191">A autenticação digestiva aborda este problema nunca transmitindo o nome e a palavra-passe no pedido.</span><span class="sxs-lookup"><span data-stu-id="6e83a-191">Digest authentication addresses this problem by never transmitting the name and password in the request.</span></span> <span data-ttu-id="6e83a-192">Em vez disso, um algoritmo é usado para obter uma chave de 128 bits ou digerir a partir do nome, palavra-passe e outras informações.</span><span class="sxs-lookup"><span data-stu-id="6e83a-192">Instead, an algorithm is used to derive a 128-bit key or digest from the name, password, and other information.</span></span> <span data-ttu-id="6e83a-193">O Servidor NetX HTTP suporta o algoritmo padrão de digestão MD5.</span><span class="sxs-lookup"><span data-stu-id="6e83a-193">The NetX HTTP Server supports the standard MD5 digest algorithm.</span></span>

<span data-ttu-id="6e83a-194">Quando é necessária a autenticação?</span><span class="sxs-lookup"><span data-stu-id="6e83a-194">When is authentication required?</span></span> <span data-ttu-id="6e83a-195">Basicamente, o SERVIDOR HTTP decide se um recurso solicitado requer autenticação.</span><span class="sxs-lookup"><span data-stu-id="6e83a-195">Basically, the HTTP Server decides if a requested resource requires authentication.</span></span> <span data-ttu-id="6e83a-196">Se for necessária a autenticação e o pedido do Cliente não incluir a autenticação adequada, é enviada ao Cliente uma resposta "HTTP/1.0 401 Não Autorizada" com o tipo de autenticação necessária.</span><span class="sxs-lookup"><span data-stu-id="6e83a-196">If authentication is required and the Client request did not include the proper authentication, a “HTTP/1.0 401 Unauthorized” response with the type of authentication required is sent to the Client.</span></span> <span data-ttu-id="6e83a-197">Espera-se então que o Cliente forme um novo pedido com a autenticação adequada.</span><span class="sxs-lookup"><span data-stu-id="6e83a-197">The Client is then expected to form a new request with the proper authentication.</span></span>

## <a name="http-authentication-callback"></a><span data-ttu-id="6e83a-198">Chamada de autenticação HTTP</span><span class="sxs-lookup"><span data-stu-id="6e83a-198">HTTP Authentication Callback</span></span>

<span data-ttu-id="6e83a-199">Como mencionado anteriormente, a autenticação HTTP é opcional e não é necessária em todas as transferências web.</span><span class="sxs-lookup"><span data-stu-id="6e83a-199">As mentioned before, HTTP authentication is optional and isn’t required on all Web transfers.</span></span> <span data-ttu-id="6e83a-200">Além disso, a autenticação é normalmente dependente de recursos.</span><span class="sxs-lookup"><span data-stu-id="6e83a-200">In addition, authentication is typically resource dependent.</span></span> <span data-ttu-id="6e83a-201">O acesso de alguns recursos no Servidor requer autenticação, enquanto outros não.</span><span class="sxs-lookup"><span data-stu-id="6e83a-201">Access of some resources on the Server require authentication, while others do not.</span></span> <span data-ttu-id="6e83a-202">O pacote do Servidor NetX HTTP permite que a aplicação especifique (através da chamada ***nx_http_server_create)*** uma rotina de chamada de autenticação que é chamada no início do tratamento de cada pedido do Cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="6e83a-202">The NetX HTTP Server package allows the application to specify (via the ***nx_http_server_create*** call) an authentication callback routine that is called at the beginning of handling each HTTP Client request.</span></span>

<span data-ttu-id="6e83a-203">A rotina de retorno fornece ao Servidor HTTP NetX o nome de utilizador, palavra-passe e cadeias de reinos associadas ao recurso e devolve o tipo de autenticação necessária.</span><span class="sxs-lookup"><span data-stu-id="6e83a-203">The callback routine provides the NetX HTTP Server with the username, password, and realm strings associated with the resource and return the type of authentication necessary.</span></span> <span data-ttu-id="6e83a-204">Se não for necessária qualquer autenticação para o recurso, a chamada de autenticação deve devolver o valor de **NX_HTTP_DONT_AUTHENTICATE**.</span><span class="sxs-lookup"><span data-stu-id="6e83a-204">If no authentication is necessary for the resource, the authentication callback should return the value of **NX_HTTP_DONT_AUTHENTICATE**.</span></span> <span data-ttu-id="6e83a-205">Caso contrário, se for necessária uma autenticação básica para o recurso especificado, a rotina deve voltar **NX_HTTP_BASIC_AUTHENTICATE**.</span><span class="sxs-lookup"><span data-stu-id="6e83a-205">Otherwise, if basic authentication is required for the specified resource, the routine should return **NX_HTTP_BASIC_AUTHENTICATE**.</span></span> <span data-ttu-id="6e83a-206">E, finalmente, se a autenticação da digestão MD5 for necessária, a rotina de retorno deve voltar **NX_HTTP_DIGEST_AUTHENTICATE**.</span><span class="sxs-lookup"><span data-stu-id="6e83a-206">And finally, if MD5 digest authentication is required, the callback routine should return **NX_HTTP_DIGEST_AUTHENTICATE**.</span></span> <span data-ttu-id="6e83a-207">Se não for necessária qualquer autenticação para qualquer recurso fornecido pelo Servidor HTTP, a chamada não é necessária e um ponteiro NULO pode ser fornecido à chamada de criação do SERVIDOR HTTP.</span><span class="sxs-lookup"><span data-stu-id="6e83a-207">If no authentication is required for any resource provided by the HTTP Server, the callback is not needed and a NULL pointer can be provided to the HTTP Server create call.</span></span>

<span data-ttu-id="6e83a-208">O formato da rotina de chamada autenticada da aplicação é muito simples e é definido abaixo:</span><span class="sxs-lookup"><span data-stu-id="6e83a-208">The format of the application authenticate callback routine is very simple and is defined below:</span></span>

```c
UINT nx_http_server_authentication_check (NX_HTTP_SERVER *server_ptr,
                                         UINT request_type, CHAR *resource,
                                         CHAR **name, CHAR **password,
                                         CHAR **realm);
```

<span data-ttu-id="6e83a-209">Os parâmetros de entrada são definidos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="6e83a-209">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="6e83a-210">*request_type* Especifica o pedido do cliente HTTP, os pedidos válidos são definidos como:</span><span class="sxs-lookup"><span data-stu-id="6e83a-210">*request_type* Specifies the HTTP Client request, valid requests are defined as:</span></span>
  - <span data-ttu-id="6e83a-211">**NX_HTTP_SERVER_GET_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="6e83a-211">**NX_HTTP_SERVER_GET_REQUEST**</span></span>
  - <span data-ttu-id="6e83a-212">**NX_HTTP_SERVER_POST_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="6e83a-212">**NX_HTTP_SERVER_POST_REQUEST**</span></span>
  - <span data-ttu-id="6e83a-213">**NX_HTTP_SERVER_HEAD_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="6e83a-213">**NX_HTTP_SERVER_HEAD_REQUEST**</span></span>
  - <span data-ttu-id="6e83a-214">**NX_HTTP_SERVER_PUT_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="6e83a-214">**NX_HTTP_SERVER_PUT_REQUEST**</span></span>
  - <span data-ttu-id="6e83a-215">**NX_HTTP_SERVER_DELETE_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="6e83a-215">**NX_HTTP_SERVER_DELETE_REQUEST**</span></span>
- <span data-ttu-id="6e83a-216">*recurso* Recurso específico solicitado.</span><span class="sxs-lookup"><span data-stu-id="6e83a-216">*resource* Specific resource requested.</span></span>
- <span data-ttu-id="6e83a-217">*nome* Destino para o ponteiro para o nome de utilizador necessário.</span><span class="sxs-lookup"><span data-stu-id="6e83a-217">*name* Destination for the pointer to the required username.</span></span>
- <span data-ttu-id="6e83a-218">*senha* Destino para o ponteiro para a senha necessária.</span><span class="sxs-lookup"><span data-stu-id="6e83a-218">*password* Destination for the pointer to the required password.</span></span>
- <span data-ttu-id="6e83a-219">*reino* Destino para o ponteiro para o reino para esta autenticação.</span><span class="sxs-lookup"><span data-stu-id="6e83a-219">*realm* Destination for the pointer to the realm for this authentication.</span></span>

<span data-ttu-id="6e83a-220">O valor de devolução da rotina de autenticação especifica se for necessária autenticação.</span><span class="sxs-lookup"><span data-stu-id="6e83a-220">The return value of the authentication routine specifies if authentication is required.</span></span> <span data-ttu-id="6e83a-221">os ponteiros de nome, palavra-passe e de reino não são utilizados se **NX_HTTP_DONT_AUTHENTICATE** for devolvido pela rotina de chamada de autenticação.</span><span class="sxs-lookup"><span data-stu-id="6e83a-221">name, password, and realm pointers are not used if **NX_HTTP_DONT_AUTHENTICATE** is returned by the authentication callback routine.</span></span> <span data-ttu-id="6e83a-222">Caso contrário, o desenvolvedor do servidor HTTP deve garantir que **NX_HTTP_MAX_USERNAME** e **NX_HTTP_MAX_PASSWORD** definidos em *nx_http_server.h* sejam suficientemente grandes para o nome de utilizador e palavra-passe especificados na chamada de autenticação.</span><span class="sxs-lookup"><span data-stu-id="6e83a-222">Otherwise the HTTP server developer must ensure that **NX_HTTP_MAX_USERNAME** and **NX_HTTP_MAX_PASSWORD** defined in *nx_http_server.h* are large enough for the username and password specified in the authentication callback.</span></span> <span data-ttu-id="6e83a-223">Estes estão ambos em incumprimento do tamanho de 20 chars.</span><span class="sxs-lookup"><span data-stu-id="6e83a-223">These are both defaulted to size 20 chars.</span></span>

## <a name="http-invalid-usernamepassword-callback"></a><span data-ttu-id="6e83a-224">HTTP Nome de utilizador/password inválido</span><span class="sxs-lookup"><span data-stu-id="6e83a-224">HTTP Invalid Username/Password Callback</span></span>

<span data-ttu-id="6e83a-225">A chamada opcional de nome de utilizador/palavra-passe inválida no NetX HTTP Server é invocada se o servidor HTTP receber um nome de utilizador inválido e uma combinação de palavra-passe num pedido do Cliente.</span><span class="sxs-lookup"><span data-stu-id="6e83a-225">The optional invalid username/password callback in NetX HTTP Server is invoked if HTTP server receives an invalid username and password combination in a Client request.</span></span> <span data-ttu-id="6e83a-226">Se a aplicação do servidor HTTP registar uma chamada com o servidor HTTP, será invocada se a autenticação básica ou digestão falhar *nx_http_server_get_process*, em *nx_http_server_put_process ou* *em nx_http_server_delete_process.*</span><span class="sxs-lookup"><span data-stu-id="6e83a-226">If the HTTP server application registers a callback with HTTP server it will be invoked if either basic or digest authentication fails *in nx_http_server_get_process*, in *nx_http_server_put_process,* or *in nx_http_server_delete_process.*</span></span>

<span data-ttu-id="6e83a-227">Para registar uma chamada com o servidor HTTP, o seguinte serviço é definido no servidor HTTP NetX.</span><span class="sxs-lookup"><span data-stu-id="6e83a-227">To register a callback with the HTTP server, the following service is defined in NetX HTTP Server.</span></span>

```c
UINT nx_http_server_invalid_userpassword_notify_set (NX_HTTP_SERVER *http_server_ptr,
                                                    UINT *invalid_username_password_callback)
                                                    (CHAR *resource,
                                                    ULONG *client_nx_address,
                                                    UINT request_type));
```
<span data-ttu-id="6e83a-228">Os tipos de pedidos são definidos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="6e83a-228">The request types are defined as follows:</span></span>

- <span data-ttu-id="6e83a-229">**NX_HTTP_SERVER_GET_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="6e83a-229">**NX_HTTP_SERVER_GET_REQUEST**</span></span>
- <span data-ttu-id="6e83a-230">**NX_HTTP_SERVER_POST_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="6e83a-230">**NX_HTTP_SERVER_POST_REQUEST**</span></span>
- <span data-ttu-id="6e83a-231">**NX_HTTP_SERVER_HEAD_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="6e83a-231">**NX_HTTP_SERVER_HEAD_REQUEST**</span></span>
- <span data-ttu-id="6e83a-232">**NX_HTTP_SERVER_PUT_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="6e83a-232">**NX_HTTP_SERVER_PUT_REQUEST**</span></span>
- <span data-ttu-id="6e83a-233">**NX_HTTP_SERVER_DELETE_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="6e83a-233">**NX_HTTP_SERVER_DELETE_REQUEST**</span></span>

## <a name="http-insert-gmt-date-header-callback"></a><span data-ttu-id="6e83a-234">HTTP Insira a chamada do cabeçalho de data GMT</span><span class="sxs-lookup"><span data-stu-id="6e83a-234">HTTP Insert GMT Date Header Callback</span></span>

<span data-ttu-id="6e83a-235">Existe uma chamada opcional no NetX HTTP Server para inserir um cabeçalho de data nas suas mensagens de resposta.</span><span class="sxs-lookup"><span data-stu-id="6e83a-235">There is an optional callback in NetX HTTP Server to insert a date header in its response messages.</span></span> <span data-ttu-id="6e83a-236">Esta chamada é invocada quando o Servidor HTTP está a responder a um pedido de colocação ou de obter</span><span class="sxs-lookup"><span data-stu-id="6e83a-236">This callback is invoked when the HTTP Server is responding to a put or get request</span></span>

<span data-ttu-id="6e83a-237">Para registar uma chamada de data GMT com o servidor HTTP, o seguinte serviço é definido no servidor HTTP NetX.</span><span class="sxs-lookup"><span data-stu-id="6e83a-237">To register a GMT date callback with the HTTP server, the following service is defined in the NetX HTTP Server.</span></span>

```c
UINT _nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                                     VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

<span data-ttu-id="6e83a-238">O tipo de dados NX_HTTP_SERVER_DATE é definido da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="6e83a-238">The NX_HTTP_SERVER_DATE data type is defined as follows:</span></span>

```c
typedef struct NX_HTTP_SERVER_DATE_STRUCT
{
    USHORT     nx_http_server_year;         /* Year        */
    UCHAR      nx_http_server_month;        /* Month       */
    UCHAR      nx_http_server_day;          /* Day         */
    UCHAR      nx_http_server_hour;         /* Hour        */
    UCHAR      nx_http_server_minute;       /* Minute      */
    UCHAR      nx_http_server_second;       /* Second      */
    UCHAR      nx_http_server_weekday;      /* Weekday     */
} NX_HTTP_SERVER_DATE;
```

## <a name="http-cache-info-get-callback"></a><span data-ttu-id="6e83a-239">HTTP Cache Info Obter Callback</span><span class="sxs-lookup"><span data-stu-id="6e83a-239">HTTP Cache Info Get Callback</span></span>

<span data-ttu-id="6e83a-240">O SERVIDOR HTTP tem uma chamada de retorno para solicitar a idade máxima e data da aplicação HTTP para um recurso específico.</span><span class="sxs-lookup"><span data-stu-id="6e83a-240">The HTTP Server has a callback to request the max age and date from the HTTP application for a specific resource.</span></span> <span data-ttu-id="6e83a-241">Estas informações são utilizadas para determinar se o servidor HTTP envia toda a página em resposta a um pedido do Cliente Obter.</span><span class="sxs-lookup"><span data-stu-id="6e83a-241">This information is used to determine if the HTTP server sends the entire page in response to a Client Get request.</span></span> <span data-ttu-id="6e83a-242">Se o "se modificado desde" no pedido do Cliente não for encontrado ou não corresponder à data "última modificada" devolvida pela chamada de cache, toda a página é enviada.</span><span class="sxs-lookup"><span data-stu-id="6e83a-242">If the “if modified since” in the Client request is not found or does not match the “last modified” date returned by the get cache callback, the entire page is sent.</span></span>

<span data-ttu-id="6e83a-243">Para registar a chamada com o servidor HTTP é definido o seguinte serviço:</span><span class="sxs-lookup"><span data-stu-id="6e83a-243">To register the callback with the HTTP server the following service is defined:</span></span>

```c
UINT _nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                                            UINT (*cache_info_get)
                                            (CHAR *, UINT *, NX_HTTP_SERVER_DATE *));
```

## <a name="http-multipart-support"></a><span data-ttu-id="6e83a-244">APOIO HTTP Multipart</span><span class="sxs-lookup"><span data-stu-id="6e83a-244">HTTP Multipart Support</span></span>

<span data-ttu-id="6e83a-245">As extensões multiusos de correio de Internet (MIME) destinavam-se originalmente ao protocolo SMTP, mas a sua utilização espalhou-se para HTTP.</span><span class="sxs-lookup"><span data-stu-id="6e83a-245">Multipurpose Internet Mail Extensions (MIME) was originally intended for the SMTP protocol, but its use has spread to HTTP.</span></span> <span data-ttu-id="6e83a-246">O MIME permite que as mensagens contenham tipos de mensagens mistas (por exemplo, imagem/jpg e texto/planície) dentro da mesma mensagem.</span><span class="sxs-lookup"><span data-stu-id="6e83a-246">MIME allows messages to contain mixed message types (e.g. image/jpg and text/plain) within the same message.</span></span> <span data-ttu-id="6e83a-247">O NetX HTTP Server adicionou serviços para determinar o tipo de conteúdo em mensagens HTTP que contenham MIME do Cliente.</span><span class="sxs-lookup"><span data-stu-id="6e83a-247">NetX HTTP Server has added services to determine content type in HTTP messages containing MIME from the Client.</span></span> <span data-ttu-id="6e83a-248">Para permitir o suporte e utilização de http multipartes, a opção de configuração **NX_HTTP_MULTIPART_ENABLE** deve ser definida.</span><span class="sxs-lookup"><span data-stu-id="6e83a-248">To enable HTTP multipart support and use these services, the configuration option **NX_HTTP_MULTIPART_ENABLE** must be defined.</span></span>

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                     NX_PACKET **packet_pptr,
                                     UCHAR *entity_header_buffer,
                                     ULONG buffer_size);

UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      ULONG *available_offset,
                                      ULONG *available_length);
```

<span data-ttu-id="6e83a-249">Para obter mais informações sobre a utilização destes serviços, consulte a sua descrição no capítulo 3 "Descrição dos Serviços HTTP".</span><span class="sxs-lookup"><span data-stu-id="6e83a-249">For more details on the use of these services, see their description in Chapter 3 “Description of HTTP Services”.</span></span>

## <a name="http-multi-thread-support"></a><span data-ttu-id="6e83a-250">SUPORTE HTTP Multi-Thread</span><span class="sxs-lookup"><span data-stu-id="6e83a-250">HTTP Multi-Thread Support</span></span>

<span data-ttu-id="6e83a-251">Os serviços do Cliente NetX HTTP podem ser chamados a partir de várias linhas simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="6e83a-251">The NetX HTTP Client services can be called from multiple threads simultaneously.</span></span> <span data-ttu-id="6e83a-252">No entanto, ler ou escrever pedidos para uma determinada instância http cliente deve ser feito em sequência a partir do mesmo fio.</span><span class="sxs-lookup"><span data-stu-id="6e83a-252">However, read or write requests for a particular HTTP Client instance should be done in sequence from the same thread.</span></span>

## <a name="http-rfcs"></a><span data-ttu-id="6e83a-253">HTTP RFCs</span><span class="sxs-lookup"><span data-stu-id="6e83a-253">HTTP RFCs</span></span>

<span data-ttu-id="6e83a-254">O NetX HTTP está em conformidade com o RFC1945 "Hypertext Transfer Protocol/1.0", RFC 2581 "TCP Congestion Control", RFC 1122 "Requirements for Internet Hosts", e RFCs relacionados.</span><span class="sxs-lookup"><span data-stu-id="6e83a-254">NetX HTTP is compliant with RFC1945 “Hypertext Transfer Protocol/1.0”, RFC 2581 “TCP Congestion Control”, RFC 1122 “Requirements for Internet Hosts”, and related RFCs.</span></span>