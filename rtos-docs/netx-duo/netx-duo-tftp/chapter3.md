---
title: Capítulo 3 - Descrição dos serviços Azure RTOS NetX Duo TFTP
description: Este capítulo contém uma descrição de todos os serviços NetX Duo TFTP (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 56f0d8edb991fff6ae30b6411e375ace58c544f7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825706"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-tftp-services"></a>Capítulo 3 - Descrição dos serviços Azure RTOS NetX Duo TFTP

Este capítulo contém uma descrição de todos os serviços NetX Duo TFTP (listados abaixo) por ordem alfabética. Salvo especificação em contrário, todos os serviços suportam comunicações IPv6 e IPv4.

Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

- **nxd_tftp_client_file_open**: *Abrir ficheiro de cliente TFTP*

- **nxd_tftp_client_create**: *Criar uma instância de cliente TFTP*

- **nxd_tftp_client_delete**: *Eliminar uma instância do cliente TFTP*

- **nxd_tftp_client_error_info_get**: *Obtenha informações sobre erros do cliente*

- **nxd_tftp_client_file_close**: *Arquivo de clientes próximo*

- **nxd_tftp_client_file_open**: *Arquivo de cliente aberto*

- **nxd_tftp_client_file_read**: *Leia um bloco do ficheiro do cliente*

- **nxd_tftp_client_file_write**: *Escreva bloco para ficheiro de cliente*

- **nxd_tftp_client_packet_allocate**: *Atribuir pacote para escrita de ficheiros de clientes*

- **nxd_tftp_client_set_interface**: *Definir a interface física para pedidos de TFTP*

- **nxd_tftp_server_create**: *Criar servidor TFTP*

- **nxd_tftp_server_delete**: *Eliminar o servidor TFTP*

- **nxd_tftp_server_start**: *Iniciar o servidor TFTP*

- **nxd_tftp_server_stop**: *Parar o servidor TFTP*

> [!NOTE] 
> Os equivalentes IPv4 de todos os serviços acima listados estão disponíveis no NetX Duo TFTP Client and Server, por *exemplo, nx_tftp_server_create* e *nx_tftp_client_file_open*. Apenas as descrições da API 'Duo', por exemplo, serviços a partir *de nxd_,* são fornecidas nas páginas seguintes. Quando uma entrada NXD_ADDRESS \* é especificada, a API equivalente IPv4 requer a entrada ULONG. Caso contrário, não há diferença na utilização da API.

## <a name="nxd_tftp_client_create"></a>nxd_tftp_client_create

Criar uma instância de cliente TFTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_create(NX_TFTP_CLIENT *tftp_client_ptr,  
     CHAR *tftp_client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Descrição

Este serviço cria uma instância do Cliente TFTP para a instância IP previamente criada.

> [!IMPORTANT]
> A aplicação deve certificar-se de que o IP fornecido e o pool de pacotes já estão criados. Além disso, a UDP deve ser ativada para a instância IP antes de ligar para este serviço.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **tftp_client_ptr** Ponteiro para o bloco de controlo do cliente TFTP.

- **tftp_client_name** Nome desta instância do cliente TFTP

- **ip_ptr** Ponteiro para instância IP previamente criada.

- **pool_ptr** Ponteiro para pacote piscina TFTP Caso do cliente.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**(0x00) TFTP bem sucedido criar.

- **NX_TFTP_INVALID_IP_VERSION** (0x0C) Versão IP inválida ou não suportada

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Endereço IP do Servidor Inválido recebido

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) Servidor ACK não recebido

- NX_PTR_ERROR (0x16) Inválido IP, pool ou ponteiro TFTP.

- NX_INVALID_PARAMETERS (0x4D) Entrada inválida sem ponteiro

- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e Threads

### <a name="example"></a>Exemplo

```C
/* Create a TFTP Client instance. */
status =  nxd_tftp_client_create(&my_tftp_client, “My TFTP Client”, 
                                                    &my_ip, &pool_ptr);

/* If status is NX_SUCCESS a TFTP Client instance was successfully
   created. */
```

## <a name="nxd_tftp_client_delete"></a>nxd_tftp_client_delete

Eliminar uma instância do cliente TFTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_delete(NX_TFTP_CLIENT *tftp_client_ptr);
```

### <a name="description"></a>Descrição

Este serviço elimina uma instância do Cliente TFTP previamente criada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **tftp_client_ptr** Ponteiro para a instância do cliente TFTP previamente criada.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Cliente TFTP bem sucedido apagar.

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.

- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Delete a TFTP Client instance. */
status =  nxd_tftp_client_delete(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP Client instance was successfully
   deleted. */
```

## <a name="nxd_tftp_client_error_info_get"></a>nxd_tftp_client_error_info_get

Obtenha informações de erro do cliente

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_error_info_get(NX_TFTP_CLIENT *tftp_client_ptr,
                        UINT *error_code, CHAR **error_string);
```

### <a name="description"></a>Descrição

Este serviço devolve o último código de erro recebido e define o ponteiro para a cadeia de erro interna do cliente. Em condições de erro, o utilizador pode visualizar o último erro enviado pelo servidor. Uma cadeia de erro nulo indica que não existe qualquer erro.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **tftp_client_ptr** Ponteiro para a instância do cliente TFTP anteriormente criada.

- **error_code** Ponteiro para a área de destino para código de erro

- **error_string** Ponteiro para destino para cadeia de erro

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Informações de erro de sucesso da TFTP obtêm.  

- NX_PTR_ERROR (0x16) Ponteiro do Cliente TFTP inválido.

- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Get error information for client. */
status =  nxd_tftp_client_error_info_get(&my_tftp_client, &error_code,
                    &error_string_ptr);

/* If status is NX_SUCCESS the error code and error string are available. */
```

## <a name="nxd_tftp_client_file_close"></a>nxd_tftp_client_file_close

Arquivar ficheiro de cliente

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_file_close(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT ip_type);
```

### <a name="description"></a>Descrição

Este serviço encerra o ficheiro previamente aberto por esta instância do Cliente TFTP. Uma instância do Cliente TFTP é permitida a ter apenas um ficheiro aberto de cada vez.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **tftp_client_ptr** Ponteiro para a instância do cliente TFTP anteriormente criada.

- **ip_type** Indicar qual o protocolo IP a utilizar. As opções válidas são IPv4 (4) ou IPv6 (6).

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) TFTP bem sucedido fechar.

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.

- NX_CALLER_ERROR (0x11) Inválido deste serviço.

- NX_INVALID_PARAMETERS (0x4D) Entrada inválida sem ponte.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Close the previously opened file associated with “my_client”. */
status =  nxd_tftp_client_file_close(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP file is closed. */
```

## <a name="nx_tftp_client_file_open"></a>nx_tftp_client_file_open

Abrir ficheiro de cliente TFTP

### <a name="prototype"></a>Prototype

```C
UINT nx_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr, 
            CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
            open_type, ULONG wait_option);
```

### <a name="description"></a>Descrição

Este serviço tenta abrir o ficheiro especificado no Servidor TFTP no endereço IP especificado. O ficheiro será aberto para leitura ou escrita. 

> [!NOTE] 
> Isto está limitado apenas a pacotes IPv4, e destina-se a apoiar aplicações NetX TFTP. Os desenvolvedores são encorajados a apresentar as suas aplicações para usar o serviço equivalente "duo" *nxd_tftp_client_file_open.*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **tftp_client_ptr** Ponteiro para o bloco de controlo TFTP.

- **file_name** Nome do ficheiro ASCII, nulo e com informações de percurso adequadas.

- **server_ip_address** Endereço TFTP do servidor.

- **open_type** Tipo de pedido aberto, também:

  **NX_TFTP_OPEN_FOR_READ** (0x01)

  **NX_TFTP_OPEN_FOR_WRITE** (0x02)

- **wait_option** Define quanto tempo o serviço vai esperar pelo ficheiro do Cliente TFTP aberto. As opções de espera são definidas da seguinte forma:

  **valor de tempo limite** (0x00000001 através de 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF) 
  
  A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que um Servidor TFTP responda ao pedido. 
  
  Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaque para permanecer suspenso enquanto se aguarda a resposta do servidor TFTP.

- **ip_type** Indicar qual o protocolo IP a utilizar. As opções válidas são IPv4 (4) ou IPv6 (6).

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Ficheiro de cliente bem sucedido aberto

- **cliente NX_TFTP_NOT_CLOSED** (0xC3) já tem ficheiro aberto

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Endereço de servidor inválido recebido

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) Nenhum ACK recebido do servidor

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP recebido

- **NX_TFTP_CODE_ERROR** (0x05) Código de erro recebido

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.

- NX_CALLER_ERROR (0x11) Inválido deste serviço

- NX_IP_ADDRESS_ERROR (0x21) Endereço IP do servidor inválido

- NX_OPTION_ERROR (0x0A) Tipo aberto inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
        & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_open"></a>nxd_tftp_client_file_open

Abrir ficheiro de cliente TFTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr,
        CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
        open_type, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a>Descrição

Este serviço tenta abrir o ficheiro especificado no Servidor TFTP no endereço IPv6 especificado. O ficheiro será aberto para leitura ou escrita.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **tftp_client_ptr** Ponteiro para o bloco de controlo TFTP.

- **file_name** Nome do ficheiro ASCII, nulo e com informações de percurso adequadas.

- **server_ip_address** Endereço TFTP do servidor.

- **open_type** Tipo de pedido aberto, também:

  **NX_TFTP_OPEN_FOR_READ** (0x01)

  **NX_TFTP_OPEN_FOR_WRITE** (0x02)

- **wait_option** Define quanto tempo o serviço vai esperar pelo ficheiro do Cliente TFTP aberto. As opções de espera são definidas da seguinte forma:

  **valor de tempo limite** (0x00000001 através de 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que um Servidor TFTP responda ao pedido.

  Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaque para permanecer suspenso enquanto se aguarda a resposta do servidor TFTP.

- **ip_type** Indicar qual o protocolo IP a utilizar. As opções válidas são IPv4 (4) ou IPv6 (6).

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Ficheiro de cliente bem sucedido aberto

- **cliente NX_TFTP_NOT_CLOSED** (0xC3) já tem ficheiro aberto

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Endereço de servidor inválido recebido

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) Nenhum ACK recebido do servidor

- **versão IP** NX_TFTP_INVALID_IP_VERSION (0x0C) Inválida

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP recebido

- **NX_TFTP_CODE_ERROR** (0x05) Código de erro recebido

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.

- NX_CALLER_ERROR (0x11) Inválido deste serviço

- NX_IP_ADDRESS_ERROR (0x21) Endereço IP do servidor inválido

- NX_OPTION_ERROR (0x0A) Tipo aberto inválido

- NX_INVALID_PARAMETERS (0x4D) Entrada inválida sem ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
                & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_read"></a>nxd_tftp_client_file_read

Leia um bloco a partir do ficheiro do cliente

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_file_read(NX_TFTP_CLIENT *tftp_client_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a>Descrição

Este serviço lê um bloco de 512 bytes do ficheiro do Cliente TFTP previamente aberto. Um bloco contendo menos de 512 bytes sinaliza o fim do ficheiro.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **tftp_client_ptr** Ponteiro para o bloco de controlo do cliente TFTP.

- **packet_ptr** Destino para pacote que contenha o bloco lido a partir do ficheiro.

- **wait_option** Define quanto tempo o serviço esperará que a leitura esteja concluída. As opções de espera são definidas da seguinte forma:

  **valor de tempo limite** (0x00000001 através de 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor TFTP responda ao pedido.

  A seleção de um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaque para permanecer suspenso enquanto espera que o servidor TFTP envie um bloco do ficheiro.

- **ip_type** Indicar qual o protocolo IP a utilizar. As opções válidas são IPv4 (4) ou IPv6 (6).

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Leitura de bloco de clientes bem sucedido

- **NX_TFTP_NOT_OPEN** (0xC3) Ficheiro cliente especificado não está aberto para leitura

- **NX_NO_PACKET** (0x01) Nenhum pacote recebido do Servidor.

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Endereço de servidor inválido recebido

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) Nenhum ACK recebido do Servidor

- **NX_TFTP_END_OF_FILE** (0xC5) Fim do ficheiro detetado (não um erro).

- **versão IP** NX_TFTP_INVALID_IP_VERSION (0x0C) Inválida

- **NX_TFTP_CODE_ERROR** (0x05) Código de erro recebido

- **NX_TFTP_FAILED** (0xC2) Código TFTP desconhecido recebido

- **NX_TFTP_INVALID_BLOCK_NUMBER** (0x0A) Número de bloco inválido recebido

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.

- NX_CALLER_ERROR (0x11) Inválido deste serviço

- NX_INVALID_PARAMETERS (0x4D) Entrada inválida sem ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Read a block from a previously opened file of “my_client”. */
status =  nxd_tftp_client_file_read(&my_tftp_client, &return_packet_ptr, 200);

/* If status is NX_SUCCESS a block of the TFTP file is in the payload of
   “return_packet_ptr”. */
```

## <a name="nxd_tftp_client_file_write"></a>nxd_tftp_client_file_write

Escreva um bloco para o ficheiro cliente

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_file_write(NX_TFTP_CLIENT *tftp_client_ptr,
            NX_PACKET *packet_ptr, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a>Descrição

Este serviço escreve um bloco de 512 bytes para o ficheiro do Cliente TFTP previamente aberto. Especificar um bloco que contenha menos de 512 bytes sinaliza o fim do ficheiro.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **tftp_client_ptr** Ponteiro para o bloco de controlo do cliente TFTP.

- **packet_ptr** Pacote contendo o bloco para escrever para o arquivo.

- **wait_option** Define quanto tempo o serviço esperará que a escrita esteja concluída. As opções de espera são definidas da seguinte forma:

  **valor de tempo limite** (0x00000001 através de 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor TFTP responda ao pedido.
 
  Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto espera que o servidor TFTP envie um ACK para o pedido de escrita.

- **ip_type** Indicar qual o protocolo IP a utilizar. As opções válidas são IPv4 (4) ou IPv6 (6).

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Escrita de bloco de cliente bem sucedido

- **NX_TFTP_NOT_OPEN** (0xC3) Ficheiro cliente especificado não está aberto para escrita

- **NX_TFTP_TIMEOUT** (0xC1) Tempo limite à espera do Servidor ACK

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Endereço de servidor inválido recebido

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) Nenhum ACK recebido do servidor

- **versão IP** NX_TFTP_INVALID_IP_VERSION (0x0C) Inválida

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Endereço de servidor inválido recebido

- **NX_TFTP_CODE_ERROR** (0x05) Código de erro recebido

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.

- NX_CALLER_ERROR (0x11) Inválido deste serviço

- NX_INVALID_PARAMETERS (0x4D) Entrada inválida sem ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write a block to the previously opened file of “my_client”. */
status =  nxd_tftp_client_file_write(&my_tftp_client, packet_ptr, 200);

/* If status is NX_SUCCESS the block in the payload of “packet_ptr” was 
   written to the TFTP file opened by “my_client”. */
```

## <a name="nxd_tftp_client_packet_allocate"></a>nxd_tftp_client_packet_allocate

Pacote de atribuição para escrita de ficheiros do Cliente

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_packet_allocate(NX_PACKET_POOL *pool_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a>Descrição

Este serviço atribui um pacote UDP da piscina de pacotes especificado e abre espaço para o cabeçalho TFTP de 4 bytes antes de o pacote ser devolvido ao chamador. O chamador pode então construir um tampão para escrever para um ficheiro de cliente.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **pool_ptr** Ponteiro para a piscina de pacotes.

- **packet_ptr** Destino para ponteiro para pacote atribuído.

- **wait_option** Define quanto tempo o serviço esperará que o pacote alocado esteja concluído. As opções de espera são definidas da seguinte forma:

  **valor de tempo limite** (0x00000001 através de 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que a atribuição termine.

  A seleção de um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a atribuição do pacote.

- **ip_type** Indicar qual o protocolo IP a utilizar. As opções válidas são IPv4 (4) ou IPv6 (6).

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Atribuição de pacotes bem sucedidos

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.

- NX_CALLER_ERROR (0x11) Inválido deste serviço

- NX_INVALID_PARAMETERS (0x4D) Entrada inválida sem ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Allocate a packet for TFTP file write. */
status =  nxd_tftp_client_packet_allocate(&my_pool, &packet_ptr, 200);

/* If status is NX_SUCCESS “packet_ptr” contains the new packet. */
```

## <a name="nxd_tftp_client_set_interface"></a>nxd_tftp_client_set_interface

Definir interface física para pedidos de TFTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_client_set_interface(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT if_index);
```

### <a name="description"></a>Descrição

Este serviço utiliza o índice de interface de entrada para definir a interface física para o Cliente TFTP enviar e receber pacotes TFTP. O valor predefinido é zero, para a interface primária.

> [!NOTE]
> A NetX Duo deve suportar a endereçamento multihome (v5.6 ou posterior) para utilizar este serviço.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **tftp_client_ptr** Ponteiro para a instância do cliente TFTP

- **if_index** Índice de interface física a utilizar

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Inserir interface inválida (0x0B)

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.

- NX_CALLER_ERROR (0x11) Inválido deste serviço

- NX_TFTP_INVALID_INTERFACE (0x0B) Entrada de interface inválida

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Specify the primary interface for TFTP requests. */
status =  nxd_tftp_client_set_interface(&client, 0);

/* If status is NX_SUCCESS the primary interface will be use for TFTP communications. */
```

## <a name="nxd_tftp_server_create"></a>nxd_tftp_server_create

Criar servidor TFTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_server_create(NX_TFTP_SERVER *tftp_server_ptr,
            CHAR *tftp_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr, 
            VOID *stack_ptr, ULONG stack_size,
            NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Descrição

Este serviço cria um Servidor TFTP que responde aos pedidos do Cliente TFTP na porta 69. O Servidor deve ser iniciado por uma chamada subsequente para *nxd_tftp_server_start*.

> [!IMPORTANT]
> A aplicação deve certificar-se de que a instância IP fornecida, o pool de pacotes e a instância de mídia FileX já estão criados. Além disso, a UDP deve ser ativada para a instância IP antes de ligar para este serviço.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **tftp_server_ptr** Ponteiro para o bloco de controlo do servidor TFTP.

- **tftp_server_name** Nome desta instância do Servidor TFTP

- **ip_ptr** Ponteiro para instância IP previamente criada.

- **media_ptr** Pointer para a instância de media FileX.

- **stack_ptr** Ponteiro para a área da pilha do servidor TFTP.

- **stack_size** Número de bytes na pilha do servidor TFTP.

- **pool_ptr** Ponteiro para a piscina de pacotes TFTP. 

> [!NOTE]
> A piscina fornecida deve ter cargas de pacote de pelo menos 580 bytes de tamanho. <sup>1</sup>

<sup>1</sup> A porção de dados de um pacote é exatamente 512 bytes, mas o tamanho da carga útil do pacote deve ser de pelo menos 572 bytes. Os bytes restantes são utilizados para os cabeçalhos UDP, IPv6 e Ethernet e potenciais bytes de trailing exigidos pelo condutor para o alinhamento.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Servidor de sucesso criar

- **NX_TFTP_POOL_ERROR** (0xC6) Piscina de pacotes tem tamanho de pacote inferior a 560 bytes

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```C
/* Create a TFTP Server called “my_server”. */
status =  nxd_tftp_server_create(&my_server, “My TFTP Server”, &server_ip, 
                &ram_disk, stack_ptr, 2048, pool_ptr);

/* If status is NX_SUCCESS the TFTP Server is created. */
```

## <a name="nxd_tftp_server_delete"></a>nxd_tftp_server_delete

Excluir o Servidor TFTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_server_delete(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>Descrição

Este serviço elimina um Servidor TFTP previamente criado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **tftp_server_ptr** Ponteiro para o bloco de controlo do servidor TFTP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Servidor de sucesso

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.

- NX_CALLER_ERROR (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Delete the TFTP Server called “my_server”. */
status =  nxd_tftp_server_delete(&my_server);

/* If status is NX_SUCCESS the TFTP Server is deleted. */
```

## <a name="nxd_tftp_server_start"></a>nxd_tftp_server_start

Iniciar o servidor TFTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_server_start(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>Descrição

Este serviço inicia o Servidor TFTP anteriormente criado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **tftp_server_ptr** Ponteiro para o bloco de controlo do servidor TFTP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Início do servidor de sucesso

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro .
 
### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```C
/* Start the TFTP Server called “my_server”. */
status =  nxd_tftp_server_start(&my_server);

/* If status is NX_SUCCESS the TFTP Server is started. */
```

## <a name="nxd_tftp_server_stop"></a>nxd_tftp_server_stop

Parar o servidor TFTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_tftp_server_stop(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>Descrição

Este serviço para o Servidor TFTP anteriormente criado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **tftp_server_ptr** Ponteiro para o bloco de controlo do servidor TFTP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) paragem do servidor de sucesso

- NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.

- NX_CALLER_ERROR (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Stop the TFTP Server called “my_server”. */
status =  nxd_tftp_server_stop(&my_server);

/* If status is NX_SUCCESS the TFTP Server is stopped. */
```