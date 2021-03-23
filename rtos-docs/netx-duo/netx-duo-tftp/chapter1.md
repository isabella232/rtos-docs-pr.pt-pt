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
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-tftp"></a><span data-ttu-id="fde49-103">Capítulo 1 - Introdução ao Azure RTOS NetX Duo TFTP</span><span class="sxs-lookup"><span data-stu-id="fde49-103">Chapter 1 - Introduction to Azure RTOS NetX Duo TFTP</span></span> 

<span data-ttu-id="fde49-104">O Trivial File Transfer Protocol (TFTP) é um protocolo leve concebido para transferências de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="fde49-104">The Trivial File Transfer Protocol (TFTP) is a lightweight protocol designed for file transfers.</span></span> <span data-ttu-id="fde49-105">Ao contrário de protocolos mais robustos, o TFTP não realiza uma verificação extensiva de erros e também pode ter um desempenho limitado porque é um protocolo de paragem e espera.</span><span class="sxs-lookup"><span data-stu-id="fde49-105">Unlike more robust protocols, TFTP does not perform extensive error checking and can also have limited performance because it is a stop-and-wait protocol.</span></span> <span data-ttu-id="fde49-106">Depois de um pacote de dados TFTP ser enviado, o remetente espera que um ACK seja devolvido pelo destinatário.</span><span class="sxs-lookup"><span data-stu-id="fde49-106">After a TFTP data packet is sent, the sender waits for an ACK to be returned by the recipient.</span></span> <span data-ttu-id="fde49-107">Embora isto seja simples, limita a produção total de TFTP.</span><span class="sxs-lookup"><span data-stu-id="fde49-107">Although this is simple, it does limit the overall TFTP throughput.</span></span> <span data-ttu-id="fde49-108">O pacote TFTP permite que os anfitriões utilizem o protocolo TFTP em redes IP.</span><span class="sxs-lookup"><span data-stu-id="fde49-108">The TFTP package enables hosts to use the TFTP protocol over IP networks.</span></span>

## <a name="tftp-requirements"></a><span data-ttu-id="fde49-109">Requisitos TFTP</span><span class="sxs-lookup"><span data-stu-id="fde49-109">TFTP Requirements</span></span>

<span data-ttu-id="fde49-110">Para funcionar corretamente, a parte dos Clientes TFTP do pacote NetX Duo TFTP requer que já tenha sido criada uma instância IP.</span><span class="sxs-lookup"><span data-stu-id="fde49-110">In order to function properly, the TFTP Clients portion of the NetX Duo TFTP package requires that an IP instance has already been created.</span></span> <span data-ttu-id="fde49-111">Além disso, a UDP deve ser ativada nessa mesma instância DEP.</span><span class="sxs-lookup"><span data-stu-id="fde49-111">In addition, UDP must be enabled on that same IP instance.</span></span> <span data-ttu-id="fde49-112">A parte cliente do pacote NetX Duo TFTP não tem requisitos adicionais.</span><span class="sxs-lookup"><span data-stu-id="fde49-112">The Client portion of the NetX Duo TFTP package has no further requirements.</span></span>

<span data-ttu-id="fde49-113">A parte do Servidor TFTP do pacote NetX Duo TFTP tem vários requisitos adicionais.</span><span class="sxs-lookup"><span data-stu-id="fde49-113">The TFTP Server portion of the NetX Duo TFTP package has several additional requirements.</span></span> <span data-ttu-id="fde49-114">Em primeiro lugar, requer acesso total à UDP *bem conhecida porta 69* para lidar com todos os pedidos de TFTP do cliente.</span><span class="sxs-lookup"><span data-stu-id="fde49-114">First, it requires complete access to the UDP *well known port 69* for handling all client TFTP requests.</span></span> <span data-ttu-id="fde49-115">O Servidor TFTP também foi concebido para ser utilizado com o sistema de ficheiros incorporado FileX.</span><span class="sxs-lookup"><span data-stu-id="fde49-115">The TFTP Server is also designed for use with the FileX embedded file system.</span></span> <span data-ttu-id="fde49-116">Se o FileX não estiver disponível, o utilizador pode apresentar as porções do FileX utilizadas para o seu próprio ambiente.</span><span class="sxs-lookup"><span data-stu-id="fde49-116">If FileX is not available, the user may port the portions of FileX used to their own environment.</span></span> <span data-ttu-id="fde49-117">Isto é discutido em secções posteriores deste guia.</span><span class="sxs-lookup"><span data-stu-id="fde49-117">This is discussed in later sections of this guide.</span></span>

## <a name="tftp-file-names"></a><span data-ttu-id="fde49-118">Nomes de ficheiros TFTP</span><span class="sxs-lookup"><span data-stu-id="fde49-118">TFTP File Names</span></span> 

<span data-ttu-id="fde49-119">Os nomes dos ficheiros TFTP devem estar no formato do sistema de ficheiros-alvo.</span><span class="sxs-lookup"><span data-stu-id="fde49-119">TFTP file names should be in the format of the target file system.</span></span> <span data-ttu-id="fde49-120">Devem ser nulas terminadas as cordas ASCII, com informações completas sobre o percurso, se necessário.</span><span class="sxs-lookup"><span data-stu-id="fde49-120">They should be NULL terminated ASCII strings, with full path information if necessary.</span></span> <span data-ttu-id="fde49-121">Não existe um limite especificado no tamanho dos nomes de ficheiros TFTP na implementação do NetX Duo TFTP.</span><span class="sxs-lookup"><span data-stu-id="fde49-121">There is no specified limit in the size of TFTP file names in the NetX Duo TFTP implementation.</span></span>

## <a name="tftp-messages"></a><span data-ttu-id="fde49-122">Mensagens TFTP</span><span class="sxs-lookup"><span data-stu-id="fde49-122">TFTP Messages</span></span>

<span data-ttu-id="fde49-123">O TFTP tem um mecanismo muito simples de abertura, leitura, escrita e fecho de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="fde49-123">The TFTP has a very simple mechanism for opening, reading, writing, and closing files.</span></span> <span data-ttu-id="fde49-124">Há basicamente 2-4 bytes de cabeçalho TFTP por baixo do cabeçalho da UDP.</span><span class="sxs-lookup"><span data-stu-id="fde49-124">There are basically 2-4 bytes of TFTP header underneath the UDP header.</span></span> <span data-ttu-id="fde49-125">A definição das mensagens abertas do ficheiro TFTP tem o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="fde49-125">The definition of the TFTP file open messages has the following format:</span></span>

<span data-ttu-id="fde49-126">**oooof... f0OCTET0**</span><span class="sxs-lookup"><span data-stu-id="fde49-126">**oooof…f0OCTET0**</span></span>

<span data-ttu-id="fde49-127">Em que:</span><span class="sxs-lookup"><span data-stu-id="fde49-127">Where:</span></span>

- <span data-ttu-id="fde49-128">**oooo** campo opcode de 2 byte</span><span class="sxs-lookup"><span data-stu-id="fde49-128">**oooo** 2-byte Opcode field</span></span>  
<span data-ttu-id="fde49-129">0x0001 -> Aberto para leitura</span><span class="sxs-lookup"><span data-stu-id="fde49-129">0x0001 -> Open for read</span></span>  
<span data-ttu-id="fde49-130">0x0002 -> Open para escrita</span><span class="sxs-lookup"><span data-stu-id="fde49-130">0x0002 -> Open for write</span></span>

- <span data-ttu-id="fde49-131">**f... f** n-byte Campo de nome filename</span><span class="sxs-lookup"><span data-stu-id="fde49-131">**f…f** n-byte Filename field</span></span>

- <span data-ttu-id="fde49-132">0 1 byte anular o carácter de rescisão</span><span class="sxs-lookup"><span data-stu-id="fde49-132">0  1-byte NULL termination character</span></span>

- <span data-ttu-id="fde49-133">**OCTET** ASCII "OCTET" para especificar transferência binária</span><span class="sxs-lookup"><span data-stu-id="fde49-133">**OCTET** ASCII “OCTET” to specify binary transfer</span></span>

- <span data-ttu-id="fde49-134">0 1 byte anular o carácter de rescisão</span><span class="sxs-lookup"><span data-stu-id="fde49-134">0  1-byte NULL termination character</span></span>

<span data-ttu-id="fde49-135">A definição da escrita TFTP, ACK, e as mensagens de erro são ligeiramente diferentes e são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="fde49-135">The definition of the TFTP write, ACK, and error messages are slightly different and are defined as follows:</span></span>

<span data-ttu-id="fde49-136">**oooobbbbd... d**</span><span class="sxs-lookup"><span data-stu-id="fde49-136">**oooobbbbd…d**</span></span>

<span data-ttu-id="fde49-137">Em que:</span><span class="sxs-lookup"><span data-stu-id="fde49-137">Where:</span></span>

- <span data-ttu-id="fde49-138">**oooo** campo opcode de 2 byte</span><span class="sxs-lookup"><span data-stu-id="fde49-138">**oooo** 2-byte Opcode field</span></span>  
<span data-ttu-id="fde49-139">Pacote de dados 0x0003 -></span><span class="sxs-lookup"><span data-stu-id="fde49-139">0x0003 -> Data packet</span></span>  
<span data-ttu-id="fde49-140">0x0004 -> ACK para a última leitura</span><span class="sxs-lookup"><span data-stu-id="fde49-140">0x0004 -> ACK for last read</span></span>  
<span data-ttu-id="fde49-141">0x0005 -> Condição de erro</span><span class="sxs-lookup"><span data-stu-id="fde49-141">0x0005 -> Error condition</span></span>  

- <span data-ttu-id="fde49-142">**bbbb** 2-byte Bloco Número (1-n)</span><span class="sxs-lookup"><span data-stu-id="fde49-142">**bbbb** 2-byte Block Number field (1-n)</span></span>

- <span data-ttu-id="fde49-143">**d... d** n-byte Campo de dados</span><span class="sxs-lookup"><span data-stu-id="fde49-143">**d…d** n-byte Data field</span></span>


- <span data-ttu-id="fde49-144">0x0001 (ler) Nome do arquivo 0 OCTET 0</span><span class="sxs-lookup"><span data-stu-id="fde49-144">0x0001 (read) File Name 0 OCTET 0</span></span>

- <span data-ttu-id="fde49-145">0x0002 (escrever) Nome do arquivo 0 OCTET 0</span><span class="sxs-lookup"><span data-stu-id="fde49-145">0x0002 (write) File Name 0 OCTET 0</span></span>

## <a name="tftp-communication"></a><span data-ttu-id="fde49-146">Comunicação TFTP</span><span class="sxs-lookup"><span data-stu-id="fde49-146">TFTP Communication</span></span>

<span data-ttu-id="fde49-147">Os Servidores TFTP utilizam a conhecida porta UDP 69 para ouvir os pedidos do Cliente.</span><span class="sxs-lookup"><span data-stu-id="fde49-147">TFTP Servers utilize the well-known UDP port 69 to listen for Client requests.</span></span> <span data-ttu-id="fde49-148">As tomadas do cliente TFTP podem ligar-se a qualquer porta UDP disponível.</span><span class="sxs-lookup"><span data-stu-id="fde49-148">TFTP Client sockets may bind to any available UDP port.</span></span> <span data-ttu-id="fde49-149">A carga útil do pacote de dados que contém o ficheiro para carregar ou descarregar é enviada em 512 bytes, até que o último pacote contendo < 512 bytes.</span><span class="sxs-lookup"><span data-stu-id="fde49-149">Data packet payload containing the file to upload or download is sent in 512 byte chunks, until the last packet containing < 512 bytes.</span></span> <span data-ttu-id="fde49-150">Portanto, um pacote contendo menos de 512 bytes sinaliza o fim do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="fde49-150">Therefore a packet containing fewer than 512 bytes signals the end of file.</span></span> <span data-ttu-id="fde49-151">A sequência geral dos acontecimentos é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="fde49-151">The general sequence of events is as follows:</span></span>

<span data-ttu-id="fde49-152">Pedidos de ficheiros de leitura TFTP:</span><span class="sxs-lookup"><span data-stu-id="fde49-152">TFTP Read File Requests:</span></span>

1.  <span data-ttu-id="fde49-153">O Cliente emite um pedido de "Open For Read" com o nome do ficheiro e aguarda uma resposta do Servidor.</span><span class="sxs-lookup"><span data-stu-id="fde49-153">The Client issues an “Open For Read” request with the file name and waits for a reply from the Server.</span></span>

2.  <span data-ttu-id="fde49-154">O Servidor envia os primeiros 512 bytes do ficheiro ou menos se o tamanho do ficheiro for inferior a 512 bytes.</span><span class="sxs-lookup"><span data-stu-id="fde49-154">The Server sends the first 512 bytes of the file or less if the file size is less than 512 bytes.</span></span>

3.  <span data-ttu-id="fde49-155">O Cliente recebe dados, envia um ACK e aguarda o próximo pacote do Servidor por ficheiros que contenham mais de 512 bytes.</span><span class="sxs-lookup"><span data-stu-id="fde49-155">The Client receives data, sends an ACK, and waits for the next packet from the Server for files containing more than 512 bytes.</span></span>

4.  <span data-ttu-id="fde49-156">A sequência termina quando o Cliente recebe um pacote contendo menos de 512 bytes.</span><span class="sxs-lookup"><span data-stu-id="fde49-156">The sequence ends when the Client receives a packet containing fewer than 512 bytes.</span></span>

<span data-ttu-id="fde49-157">Pedidos de escrita TFTP:</span><span class="sxs-lookup"><span data-stu-id="fde49-157">TFTP Write Requests:</span></span>

1.  <span data-ttu-id="fde49-158">O Cliente emite um pedido "Aberto para Escrever" com o nome do ficheiro e aguarda um ACK com um número de bloco de 0 do Servidor.</span><span class="sxs-lookup"><span data-stu-id="fde49-158">The Client issues an “Open for Write” request with the file name and waits for an ACK with a block number of 0 from the Server.</span></span>

2.  <span data-ttu-id="fde49-159">Quando o Servidor está pronto para escrever o ficheiro, envia um ACK com um número de bloco de zero.</span><span class="sxs-lookup"><span data-stu-id="fde49-159">When the Server is ready to write the file, it sends an ACK with a block number of zero.</span></span>

3.  <span data-ttu-id="fde49-160">O Cliente envia os primeiros 512 bytes do ficheiro (ou menos para ficheiros inferiores a 512 bytes) para o Servidor e espera por um ACK de volta.</span><span class="sxs-lookup"><span data-stu-id="fde49-160">The Client sends the first 512 bytes of the file (or less for files less than 512 bytes) to the Server and waits for an ACK back.</span></span>

4.  <span data-ttu-id="fde49-161">O Servidor envia um ACK após a escrita dos bytes.</span><span class="sxs-lookup"><span data-stu-id="fde49-161">The Server sends an ACK after the bytes are written.</span></span>

5.  <span data-ttu-id="fde49-162">A sequência termina quando o Cliente termina a escrita de um pacote contendo menos de 512 bytes.</span><span class="sxs-lookup"><span data-stu-id="fde49-162">The sequence ends when the Client completes writing a packet containing fewer than 512 bytes.</span></span>
 

## <a name="tftp-server-session-timer"></a><span data-ttu-id="fde49-163">Temporizador de sessão do servidor TFTP</span><span class="sxs-lookup"><span data-stu-id="fde49-163">TFTP Server Session Timer</span></span>

<span data-ttu-id="fde49-164">O Servidor TFTP tem um número limitado de slots de pedido de cliente.</span><span class="sxs-lookup"><span data-stu-id="fde49-164">The TFTP Server has a limited number of client request slots.</span></span> <span data-ttu-id="fde49-165">Se uma sessão de clientes parecer ter caído, essa ranhura não pode estar disponível para reutilização.</span><span class="sxs-lookup"><span data-stu-id="fde49-165">If a client session appears to be dropped, that slot cannot be available for re-use.</span></span> <span data-ttu-id="fde49-166">No entanto, se a opção NX_TFTP_SERVER_RETRANSMIT_ENABLE estiver ativada, o NetX Duo TFTP Server cria um temporizador de sessão que monitoriza o tempo limite de cada uma das suas sessões de clientes.</span><span class="sxs-lookup"><span data-stu-id="fde49-166">However if the NX_TFTP_SERVER_RETRANSMIT_ENABLE option is enabled, the NetX Duo TFTP Server creates an session timer that monitors the timeout on each of its client sessions.</span></span> <span data-ttu-id="fde49-167">Quando um tempo limite de sessão expira, é encerrado e quaisquer ficheiros abertos são fechados.</span><span class="sxs-lookup"><span data-stu-id="fde49-167">When a session timeout expires it is terminated and any open files are closed.</span></span> <span data-ttu-id="fde49-168">Assim, o 'slot' fica disponível para outro pedido do Cliente TFTP.</span><span class="sxs-lookup"><span data-stu-id="fde49-168">Thus the ‘slot’ becomes available for another TFTP Client request.</span></span>

<span data-ttu-id="fde49-169">Para definir o tempo limite, ajuste a opção de configuração NX_TFTP_SERVER_RETRANSMIT_TIMEOUT que por predefinição são 200 carraças temporais.</span><span class="sxs-lookup"><span data-stu-id="fde49-169">To set the timeout, adjust the configuration option NX_TFTP_SERVER_RETRANSMIT_TIMEOUT which by default is 200 timer ticks.</span></span> <span data-ttu-id="fde49-170">O intervalo entre os intervalos de sessão é definido pela NX_TFTP_SERVER_TIMEOUT_PERIOD que é 20 tiques temporais por predefinição.</span><span class="sxs-lookup"><span data-stu-id="fde49-170">The interval between which session timeouts are checked is set by the NX_TFTP_SERVER_TIMEOUT_PERIOD which is 20 timer ticks by default.</span></span>

<span data-ttu-id="fde49-171">Quando o Cliente TFTP tiver enviado ficheiros (escritos) para o meio de dados TFTP FileX, os meios de comunicação precisam de ser lavados para que os dados possam ser escritos a partir do disco de ram do servidor TFTP para os meios subjacentes (memória do disco do Cliente TFTP).</span><span class="sxs-lookup"><span data-stu-id="fde49-171">When the TFTP Client has uploaded (written) files to the TFTP FileX media, the media needs to be flushed so that data can be written from the TFTP server ram disk to the underlying media (TFTP Client disk memory).</span></span> <span data-ttu-id="fde49-172">Isto pode ser feito utilizando o serviço fx_media_flush se a aplicação não pretender fechar o Servidor TFTP.</span><span class="sxs-lookup"><span data-stu-id="fde49-172">This can be done using the fx_media_flush service if the application does not wish to close the TFTP Server.</span></span>

<span data-ttu-id="fde49-173">No entanto, depois de fechar o servidor TFTP, a aplicação deve, se não tiver mais qualquer utilização para os meios de ficheiros, então fechar os meios de comunicação utilizando o serviço fx_media_close.</span><span class="sxs-lookup"><span data-stu-id="fde49-173">However, after closing the TFTP server, the application should, if it has no further use for the FileX media, then close the media using the fx_media_close service.</span></span> <span data-ttu-id="fde49-174">Isto irá reboscar os dados do ficheiro para o disco do Cliente TFTP, fechar ficheiros abertos e atualizar as informações do diretório para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="fde49-174">This will flush the file data back to the TFTP Client disk, close open files, and update the directory information to the media.</span></span>

<span data-ttu-id="fde49-175">A secção "Pequeno Exemplo" deste capítulo demonstra-o.</span><span class="sxs-lookup"><span data-stu-id="fde49-175">The “Small Example” section in this chapter demonstrates this.</span></span>

<span data-ttu-id="fde49-176">Uma terceira opção para atualizar os meios de ficheiros é compilar a biblioteca FileX com as opções FX_FAULT_TOLERANT ou FX_FAULT_TOLERANT_DATA em vez de utilizar explicitamente os serviços FileX.</span><span class="sxs-lookup"><span data-stu-id="fde49-176">A third option for updating the FileX media is to compile the FileX library with the FX_FAULT_TOLERANT or the FX_FAULT_TOLERANT_DATA options instead of using FileX services explicitly.</span></span> <span data-ttu-id="fde49-177">Se definido, o FileX passa automaticamente pedidos de escrita ao controlador de mídia.</span><span class="sxs-lookup"><span data-stu-id="fde49-177">If defined, FileX automatically passes write requests to the media driver.</span></span> <span data-ttu-id="fde49-178">Estas opções podem limitar o desempenho, mas oferecem uma maior proteção contra dados de ficheiros perdidos ou aglomerados perdidos.</span><span class="sxs-lookup"><span data-stu-id="fde49-178">These options may limit performance but offer greater protection from lost file data or lost clusters.</span></span> <span data-ttu-id="fde49-179">Para obter mais informações sobre este e o FileX em geral, consulte o Guia do Utilizador Express Logic FileX.</span><span class="sxs-lookup"><span data-stu-id="fde49-179">For more information about this and FileX in general, please see the Express Logic FileX User Guide.</span></span>

## <a name="tftp-multi-thread-support"></a><span data-ttu-id="fde49-180">Suporte multi-rosca TFTP</span><span class="sxs-lookup"><span data-stu-id="fde49-180">TFTP Multi-Thread Support</span></span>

<span data-ttu-id="fde49-181">Os serviços do Cliente NetX Duo TFTP podem ser chamados a partir de várias linhas simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="fde49-181">The NetX Duo TFTP Client services can be called from multiple threads simultaneously.</span></span> <span data-ttu-id="fde49-182">No entanto, ler ou escrever pedidos para uma determinada instância do Cliente TFTP deve ser feito em sequência a partir do mesmo fio.</span><span class="sxs-lookup"><span data-stu-id="fde49-182">However, read or write requests for a particular TFTP Client instance should be done in sequence from the same thread.</span></span>

## <a name="tftp-rfcs"></a><span data-ttu-id="fde49-183">TFTP RFCs</span><span class="sxs-lookup"><span data-stu-id="fde49-183">TFTP RFCs</span></span>

<span data-ttu-id="fde49-184">NetX Duo TFTP está em conformidade com RFC1350 e RFCs relacionados.</span><span class="sxs-lookup"><span data-stu-id="fde49-184">NetX Duo TFTP is compliant with RFC1350 and related RFCs.</span></span>

