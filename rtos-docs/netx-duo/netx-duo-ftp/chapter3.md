---
title: Capítulo 3 - Descrição dos serviços FTP
description: Este capítulo contém uma descrição de todos os serviços NetX FTP (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d08d3c07f7be016ece68ff2f58b9ac5ba93ded780105bce362674ed36b5b885d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792371"
---
# <a name="chapter-3---description-of-ftp-services"></a>Capítulo 3 - Descrição dos serviços FTP

Este capítulo contém uma descrição de todos os serviços NetX FTP (listados abaixo) por ordem alfabética (exceto nos casos em que os equivalentes IPv4 e IPv6 do mesmo serviço são emparelhados).

> [!NOTE]
> Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

## <a name="nx_ftp_client_connect"></a>nx_ftp_client_connect

Ligação a um servidor FTP sobre o IPv4

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG server_ip, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço liga a instância do Cliente NetX FTP previamente criada ao Servidor FTP no endereço IP fornecido.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.
- **server_ip** Endereço IP do FTP Server.
- **nome de utilizador** Nome de utilizador do cliente para autenticação.
- **senha** Senha do cliente para autenticação.
- **wait_option** Define quanto tempo o serviço irá esperar pela ligação ftp cliente. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Ligação FTP bem sucedida.
- **NX_TFTP_EXPECTED_22X_CODE** (0xDB) Não conseguiu uma resposta de 22X (ok)
- **NX_FTP_EXPECTED_23X_CODE** (0xDC) Não conseguiu uma resposta 23X (ok)
- **NX_FTP_EXPECTED_33X_CODE** (0xDE) Não conseguiu uma resposta 33X (ok)
- **NX_FTP_NOT_DISCONNECTED** cliente (0xD4) já está ligado.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro.
- NX_CALLER_ERROR (0x11) Inválido deste serviço.
- NX_IP_ADDRESS_ERROR (0x21) Endereço IP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Connect the FTP Client instance “my_client” to the FTP Server at

IP address 1.2.3.4. */

status = nx_ftp_client_connect(&my_client, IP_ADDRESS(1,2,3,4), NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
    connected to the FTP Server. */
```

### <a name="see-also"></a>Consulte também

nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect nxd_ftp_client_connect

## <a name="nxd_ftp_client_connect"></a>nxd_ftp_client_connect

Ligação a um servidor FTP com suporte IPv6

### <a name="prototype"></a>Prototype

```C
UINT nxd_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    NXD_ADDRESS *server_ipduo, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço liga a instância do cliente NetX Duo FTP previamente criada ao Servidor FTP no endereço IP fornecido. As redes IPv4 e IPv6 são suportadas.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.
- **server_ipduo** Endereço IP do Servidor FTP.
- **nome de utilizador** Nome de utilizador do cliente para autenticação.
- **senha** Senha do cliente para autenticação.
- **wait_option** Define quanto tempo o serviço irá esperar pela ligação ftp cliente. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Ligação FTP bem sucedida.
- **NX_TFTP_EXPECTED_22X_CODE** (0xDB) Não conseguiu uma resposta de 22X (ok)
- **NX_FTP_EXPECTED_23X_CODE** (0xDC) Não conseguiu uma resposta 23X (ok)
- **NX_FTP_EXPECTED_33X_CODE** (0xDE) Não conseguiu uma resposta 33X (ok)
- **NX_FTP_NOT_DISCONNECTED** (0xD4) Cliente já está ligado
- NX_PTR_ERROR (0x07) Inválido do ponteiro.
- NX_CALLER_ERROR (0x11) Inválido deste serviço.
- NX_IP_ADDRESS_ERROR (0x21) Endereço IP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Connect an FTP Client instance to the FTP Server. */

/* Set up an IPv6 address for the server here.
    Note this could also be an IPv4 address as well*/

server_ip_addr.nxd_ip_address.v6[3] = 0x106;
server_ip_addr.nxd_ip_address.v6[2] = 0x0;
server_ip_addr.nxd_ip_address.v6[1] = 0x0000f101;
server_ip_addr.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V6;

status = nxd_ftp_client_connect(&my_client, server_ip_addr, NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
    connected to the FTP Server. */
```

### <a name="see-also"></a>Consulte também

nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect nx_ftp_client_connect

## <a name="nx_ftp_client_create"></a>nx_ftp_client_create

Criar uma instância de cliente FTP

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Description

Este serviço cria uma instância de cliente FTP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.
- **ftp_client_name** Nome do Cliente FTP.
- **ip_ptr** Ponteiro para instância IP previamente criada.
- **window_size** Tamanho da janela anunciado para tomadas TCP deste Cliente FTP.
- **pool_ptr** Ponteiro para a piscina de pacotes predefinidos para este Cliente FTP. Note que a carga útil mínima do pacote deve ser suficientemente grande para manter o caminho completo e o ficheiro ou o nome do diretório.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Cliente FTP bem sucedido criar.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e Threads

### <a name="example"></a>Exemplo

```C
/* Create the FTP Client instance “my_client.” */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
    2000, &client_pool);
/* If status is NX_SUCCESS the FTP Client instance was successfully created. */
```

## <a name="nx_ftp_client_delete"></a>nx_ftp_client_delete

Excluir uma instância de cliente FTP

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a>Description

Este serviço elimina uma instância do Cliente FTP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Cliente FTP bem sucedido apagar.
- **NX_FTP_NOT_DISCONNECTED** (0xD4) cliente FTP não desligado
- NX_PTR_ERROR (0x07) Ponteiro FTP inválido.
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Delete the FTP Client instance “my_client.” */

status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a>nx_ftp_client_directory_create

Criar um diretório no FTP Server

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço cria o diretório especificado no Servidor FTP que está ligado ao Cliente FTP especificado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.
- **directory_name** Nome do diretório para criar.
- **wait_option** Define quanto tempo o serviço vai esperar pela criação do diretório FTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Diretório FTP bem sucedido criar.
- **NX_FTP_NOT_CONNECTED** (0xD3) O Cliente FTP não está ligado.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) Não conseguiu uma resposta 2XX (ok)
- NX_PTR_ERROR (0x07) Ponteiro FTP inválido.
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Create the directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_create(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” was successfully created. */
```

## <a name="nx_ftp_client_directory_default_set"></a>nx_ftp_client_directory_default_set

Definir diretório predefinido no Servidor FTP

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço define o diretório predefinido no Servidor FTP que está ligado ao Cliente FTP especificado. Este diretório predefinido aplica-se apenas à ligação deste cliente.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.
- **directory_path** Nome do caminho do diretório para definir.
- **wait_option** Define quanto tempo o serviço irá esperar pelo conjunto de diretório padrão FTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Conjunto padrão FTP bem sucedido.
- **NX_FTP_NOT_CONNECTED** (0xD3) O Cliente FTP não está ligado.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) Não conseguiu uma resposta 2XX (ok)
- NX_PTR_ERROR (0x07) Ponteiro FTP inválido.
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Set the default directory to “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_default_set(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a>nx_ftp_client_directory_delete

Eliminar diretório no FTP Server

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço elimina o diretório especificado no Servidor FTP que está ligado ao Cliente FTP especificado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.
- **directory_name** Nome do diretório para apagar.
- **wait_option** Define quanto tempo o serviço esperará pela eliminação do diretório FTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Diretório FTP bem sucedido.
- **NX_FTP_NOT_CONNECTED** (0xD3) O Cliente FTP não está ligado.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) Não conseguiu uma resposta 2XX (ok)
- NX_PTR_ERROR (0x07) Ponteiro FTP inválido.
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Delete directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_delete(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a>nx_ftp_client_directory_listing_get

Obtenha listagem de diretório no FTP Server

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço obtém o conteúdo do diretório especificado no Servidor FTP que está ligado ao Cliente FTP especificado. O ponteiro do pacote fornecido conterá uma ou mais entradas de diretório. Cada entrada é separada por uma \<cr/lf\> combinação. O ***nx_ftp_client_directory_listing_continue*** deve ser chamado para concluir a operação do diretório.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.
- **directory_name** Nome do diretório para obter conteúdo de.
- **packet_ptr** Ponteiro para o ponteiro do pacote de destino. Se for bem sucedido, a carga útil do pacote conterá uma ou mais entradas de diretório.
- **wait_option** Define quanto tempo o serviço vai esperar pela lista geminada FTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Lista de diretórios FTP bem sucedidos.
- **NX_FTP_NOT_CONNECTED** (0xD3) O Cliente FTP não está ligado.
- **serviço NX_NOT_ENABLED** (0x14) (IPv6) não habilitado
- **NX_FTP_EXPECTED_1XX_CODE** (0xD9) Não conseguiu uma resposta de 1XX (ok)
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) Não conseguiu uma resposta 2XX (ok)
- NX_PTR_ERROR (0x07) Ponteiro FTP inválido.
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Get the contents of directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_listing_get(&my_client, “my_dir”, &my_packet,
    200);

/* If status is NX_SUCCESS, one or more entries of the directory “my_dir”
    can be found in “my_packet”. */
```

## <a name="nx_ftp_client_directory_listing_continue"></a>nx_ftp_client_directory_listing_continue

Continue a listar de diretórios do FTP Server

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço continua a obter o conteúdo do diretório especificado no Servidor FTP que está ligado ao Cliente FTP especificado. Deveria ter sido imediatamente precedido por uma chamada para ***nx_ftp_client_directory_listing_get***. Se for bem sucedido, o ponteiro do pacote fornecido conterá uma ou mais entradas de diretório. Esta rotina deve ser chamada até que um estado de NX_FTP_END_OF_LISTING seja recebido.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.
- **packet_ptr** Ponteiro para o ponteiro do pacote de destino. Se for bem sucedido, a carga útil do pacote conterá uma ou mais entradas de diretório, separadas por um <cr/7 se>.
- **wait_option** Define quanto tempo o serviço vai esperar pela lista geminada FTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Lista de diretórios FTP bem sucedidos.
- **NX_FTP_END_OF_LISTING** (0xD8) Não há mais inscrições neste diretório.
- **NX_FTP_NOT_CONNECTED** (0xD3) O Cliente FTP não está ligado.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) Não conseguiu uma resposta 2XX (ok)
- NX_PTR_ERROR (0x07) Ponteiro FTP inválido.
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Continue getting the contents of directory “my_dir” on the FTP Server
    connected to the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_listing_continue(&my_client, &my_packet,
    200);

/* If status is NX_SUCCESS, one or more entries of the directory “my_dir”
    can be found in “my_packet”. */
```

## <a name="nx_ftp_client_disconnect"></a>nx_ftp_client_disconnect

Desligar do Servidor FTP

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço desliga uma ligação ftp server previamente estabelecida com o cliente FTP especificado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.
- **wait_option** Define quanto tempo o serviço irá esperar pela desconexão do Cliente FTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Desconexão FTP bem sucedida.
- **NX_FTP_NOT_CONNECTED** (0xD3) O Cliente FTP não está ligado.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) Não conseguiu uma resposta 2XX (ok)
- NX_PTR_ERROR (0x07) Ponteiro FTP inválido.
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Disconnect “my_client” from the FTP Server. */

status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, “my_client” has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a>nx_ftp_client_file_close

Arquivar ficheiro do Cliente

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço fecha um ficheiro previamente aberto no Servidor FTP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.
- **wait_option** Define quanto tempo o serviço irá esperar pelo fecho do ficheiro do Cliente FTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Arquivo FTP bem sucedido.
- **NX_FTP_NOT_CONNECTED** (0xD3) O Cliente FTP não está ligado.
- **NX_FTP_NOT_OPEN (0xD5)** Arquivo não aberto; não pode fechá-lo
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) Não conseguiu uma resposta 2XX (ok)
- NX_PTR_ERROR (0x07) Ponteiro FTP inválido.
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Close previously opened file of client “my_client” on the FTP Server. */

status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the “my_client” FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a>nx_ftp_client_file_delete

Eliminar ficheiro no FTP Server

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço elimina o ficheiro especificado no Servidor FTP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.
- **file_name** Nome do ficheiro para apagar.
- **wait_option** Define quanto tempo o serviço irá esperar pela eliminação do ficheiro FTP Client. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Ficheiro FTP bem sucedido.
- **NX_FTP_NOT_CONNECTED** (0xD3) O Cliente FTP não está ligado.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) Não conseguiu uma resposta 2XX (ok)
- NX_PTR_ERROR (0x07) Ponteiro FTP inválido.
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Delete the file “my_file.txt” on the FTP Server using the previously
    connected client “my_client.” */

status = nx_ftp_client_file_delete(&my_client, “my_file.txt”, 200);

/* If status is NX_SUCCESS, the file “my_file.txt” on the FTP Server is
    deleted. */
```

## <a name="nx_ftp_client_file_open"></a>nx_ftp_client_file_open

Abre o ficheiro no FTP Server

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_file_open(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *file_name, UINT open_type, ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço abre o ficheiro especificado – para leitura ou escrita – no Servidor FTP anteriormente ligado à instância de Cliente especificada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.
- **file_name** Nome do arquivo para abrir.
- **open_type** Quer **NX_FTP_OPEN_FOR_READ** ou **NX_FTP_OPEN_FOR_WRITE.**
- **wait_option** Define quanto tempo o serviço vai esperar pelo ficheiro FTP Client aberto. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Ficheiro FTP bem sucedido aberto.
- **NX_OPTION_ERROR** (0x0A) Tipo aberto inválido.
- **NX_FTP_NOT_CONNECTED** (0xD3) O Cliente FTP não está ligado.
- **NX_FTP_NOT_CLOSED** (0xD6) Cliente FTP já está aberto.
- **NX_NO_FREE_PORTS** (0x45) Não há portas TCP disponíveis para atribuir
- NX_PTR_ERROR (0x07) Ponteiro FTP inválido.
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Open the file “my_file.txt” for reading on the FTP Server using the previously
    connected client “my_client.” */

status = nx_ftp_client_file_open(&my_client, “my_file.txt”, NX_FTP_OPEN_FOR_READ,
    200);

/* If status is NX_SUCCESS, the file “my_file.txt” on the FTP Server is
    open for reading. */
```

## <a name="nx_ftp_client_file_read"></a>nx_ftp_client_file_read

Ler a partir de arquivo

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_file_read(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço lê um pacote de um ficheiro previamente aberto. Deve ser chamado repetidamente até que um estatuto de NX_FTP_END_OF_FILE seja recebido.

Note que o autor da chamada não atribui um pacote para este serviço.  Só precisa fornecer um ponteiro para um ponteiro de pacote. Este serviço atualizará o ponteiro do pacote para apontar para um pacote recuperado da fila de receção da tomada.  Se um estado de sucesso for devolvido, isso significa que havia um pacote disponível, e é da responsabilidade do ouvinte libertar o pacote quando este é feito com ele.

Se for devolvido um estado não zero (ou um estado de erro ou NX_FTP_END_OF_FILE) não libertar o pacote. Caso contrário, gera-se um erro quando o ponteiro do pacote é NU.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.
- **packet_ptr** Ponteiro para o destino para o ponteiro do pacote de dados a ser armazenado. Se for bem sucedido, o pacote um pouco ou todos os contém do ficheiro.
- **wait_option** Define quanto tempo o serviço irá esperar pela leitura do ficheiro FTP Client. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Leitura de ficheiro FTP bem sucedido.
- **NX_FTP_NOT_OPEN** (0xD5) Cliente FTP não está aberto.
- **NX_FTP_END_OF_FILE** (0xD7) Fim da condição do ficheiro.
- NX_PTR_ERROR (0x07) Ponteiro FTP inválido.
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
NX_PACKET   *my_packet;

/* Read a packet of data from the file “my_file.txt” that was previously opened
    from the client “my_client.” */

status = nx_ftp_client_file_read(&my_client, &my_packet, 200);

/* Check status.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else
{
    /* Release packet when done with it. */
    nx_packet_release(my_packet);
}

/* If status is NX_SUCCESS, the packet pointer, “my_packet” points to the packet
    that contains the next bytes from the file. If the file is completely
    downloaded, an NX_FTP_END_OF_FILE status is returned (no packet retrieved). */
```

## <a name="nx_ftp_client_file_rename"></a>nx_ftp_client_file_rename

Rebatize o ficheiro no FTP Server

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
    CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço renomea um ficheiro no Servidor FTP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.
- **nome de arquivo** Nome atual do arquivo.
- **new_filename** Novo nome para arquivo.
- **wait_option** Define quanto tempo o serviço irá esperar pelo nome do ficheiro FTP Client. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Com sucesso do ficheiro FTP.
- **NX_FTP_NOT_CONNECTED** (0xD3) O Cliente FTP não está ligado.
- **NX_FTP_EXPECTED_3XX_CODE** (0XDD) Não recebeu resposta 3XX (ok)
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) Não conseguiu uma resposta 2XX (ok)
- NX_PTR_ERROR (0x07) Ponteiro FTP inválido.
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Rename file “my_file.txt” to “new_file.txt” on the previously connected
    Client instance “my_client.” */

status = nx_ftp_client_file_rename(&my_client, “my_file.txt”, “new_file.txt”,
    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a>nx_ftp_client_file_write

Escrever para arquivar

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço escreve um pacote de dados para o ficheiro previamente aberto no Servidor FTP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.
- **packet_ptr** Ponteiro do pacote contendo dados para escrever.
- **wait_option** Define quanto tempo o serviço irá esperar pela escrita do ficheiro FTP Client. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Escrita de ficheiro FTP bem sucedida.
- **NX_FTP_NOT_OPEN** (0xD5) Cliente FTP não está aberto.
- NX_PTR_ERROR (0x07) Ponteiro FTP inválido.
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Write the data contained in “my_packet” to the previously opened file
    “my_file.txt”. */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a>nx_ftp_client_passive_mode_set

Ativar ou desativar o modo de transferência passiva

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
    UINT passive_mode_enabled);
```

### <a name="description"></a>Description

Este serviço permite o modo de transferência passiva se a entrada passive_mode_enabled estiver definida para NX_TRUE numa instância ftp do Cliente previamente criada, de modo a que as chamadas subsequentes para ler ou escrever ficheiros (RETR, STOR) ou descarregue uma lista de diretórios (NLST) sejam feitas em modo de transferência. Para desativar a transferência do modo passivo e voltar ao comportamento predefinido do modo de transferência ativo, ligue para esta função com o passive_mode_enabled conjunto de entrada para NX_FALSE.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.
- **passive_mode_enabled** Se estiver definido para NX_TRUE, o modo passivo está ativado.<br />Se estiver definido para NX_FALSE, o modo passivo é desativado.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Conjunto de modo passivo bem sucedido.
- NX_PTR_ERROR (0x07) Ponteiro FTP inválido.
- NX_INVALID_PARAMETERS (0x4D) Entrada inválida sem ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a>nx_ftp_server_create

Criar servidor FTP

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
    CHAR *ftp_server_name, NX_IP *ip_ptr,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*ftp_login)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        ULONG client_ip_address,
        UINT client_port, CHAR *name, CHAR *password,
        CHAR *extra_info),
    UINT (*ftp_logout)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        ULONG client_ip_address, UINT client_port,
         CHAR *name, CHAR *password, CHAR *extra_info));
```

### <a name="description"></a>Description

Este serviço cria uma instância FTP Server na instância IP do NetX especificada e previamente criada. Note que o Servidor FTP precisa de ser iniciado com uma chamada para ***nx_ftp_server_start*** para que comece a funcionar.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ftp_server_ptr** Ponteiro para o bloco de controlo do servidor FTP.
- **ftp_server_name** Nome do FtP Server.
- **ip_ptr** Ponteiro para a instância IP do NetX associado. Note que só pode haver um Servidor FTP para uma instância IP.
- **media_ptr** Ponteiro para a instância de mídia filex associada.
- **stack_ptr** Ponteiro para a memória para a área interna da pilha do servidor FTP.
- **stack_size** Tamanho da área de pilhas especificada por *stack_ptr*.
- **pool_ptr** Ponteiro para piscina de pacotes NetX predefinido. Note que o tamanho da carga útil dos pacotes na piscina deve ser grande o suficiente para acomodar o maior nome/caminho de arquivo.
- **ftp_login** Função ponteiro para a função de login da aplicação. Esta função é fornecida o nome de utilizador e a palavra-passe do Cliente solicitando uma ligação, e o endereço cliente no tipo de dados ULONG. Se isto for válido, a função de login da aplicação deve voltar NX_SUCCESS.
- **ftp_logout** Função ponteiro para a função de logout da aplicação. Esta função é fornecida com o nome de utilizador e palavra-passe do Cliente solicitando uma desconexão, e o endereço Cliente no tipo de dados ULONG. Se isto for válido, a função de login da aplicação deve voltar NX_SUCCESS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Servidor FTP bem sucedido.
- NX_PTR_ERROR (0x07) Ponteiro FTP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e Threads

### <a name="example"></a>Exemplo

```C
/* Create the FTP Server “my_server” on the IP instance “ip_0” using the
    “ram_disk” media. */

status = nx_ftp_server_create(&my_server, “My Server Name”, &ip_0, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_login, my_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nxd_ftp_server_create"></a>nxd_ftp_server_create

Criar servidor FTP com suporte IPv4 e IPv6

### <a name="prototype"></a>Prototype

```C
UINT nxd_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
    CHAR *ftp_server_name, NX_IP *ip_ptr,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*ftp_login_duo)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        NXD_ADDRESS *client_ip_address, UINT client_port, CHAR *name,
        CHAR *password, CHAR *extra_info),
    UINT (*ftp_logout_duo)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        NXD_ADDRESS *client_ip_address, UINT client_port, CHAR *name,
        CHAR *password, CHAR *extra_info));
```

### <a name="description"></a>Description

Este serviço cria uma instância FTP Server na instância IP do NetX especificada e previamente criada. Note que o Servidor FTP ainda precisa de ser iniciado com uma chamada para ***nx_ftp_server_start*** para que comece a funcionar após a criação do Servidor.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ftp_server_ptr** Ponteiro para o bloco de controlo do servidor FTP.
- **ftp_server_name** Nome do FtP Server.
- **ip_ptr** Ponteiro para a instância IP do NetX associado. Note que só pode haver um Servidor FTP para uma instância IP.
- **media_ptr** Ponteiro para a instância de mídia filex associada.
- **stack_ptr** Ponteiro para a memória para a área interna da pilha do servidor FTP.
- **stack_size** Tamanho da área de pilhas especificada por *stack_ptr*.
- **pool_ptr** Ponteiro para piscina de pacotes NetX predefinido. Note que o tamanho da carga útil dos pacotes na piscina deve ser grande o suficiente para acomodar o maior nome/caminho de arquivo.
- **ftp_login_duo** Função ponteiro para a função de login da aplicação. Esta função é fornecida o nome de utilizador e a palavra-passe do Cliente solicitando uma ligação, e um ponteiro para o endereço Cliente no NXD_ADDRESS tipo de dados. Se isto for válido, a função de login da aplicação deve voltar NX_SUCCESS.
- **ftp_logout_duo** Função ponteiro para a função de logout da aplicação. Esta função é fornecida com o nome de utilizador e palavra-passe do Cliente solicitando uma desconexão, e um ponteiro para o endereço Cliente no tipo de dados NXD_ADDRESS. Se isto for válido, a função de login da aplicação deve voltar NX_SUCCESS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Servidor FTP bem sucedido.
- NX_PTR_ERROR (0x07) Ponteiro FTP inválido.
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e Threads

### <a name="example"></a>Exemplo

```C
/* Create the FTP Server “my_server” on the IP instance “ip_0” using the
    “ram_disk” media. */

status = nxd_ftp_server_create(&my_server, “My Server Name”, &ip_0, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_duo_login, my_duo_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nx_ftp_server_delete"></a>nx_ftp_server_delete

Excluir servidor FTP

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Description

Este serviço elimina uma instância ftp server previamente criada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ftp_server_ptr** Ponteiro para o bloco de controlo do servidor FTP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Servidor FTP com sucesso.
- NX_PTR_ERROR (0x07) Ponteiro FTP inválido.
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Delete the FTP Server “my_server”. */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a>nx_ftp_server_start

Iniciar servidor FTP

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Description

Este serviço inicia uma instância ftp server previamente criada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ftp_server_ptr** Ponteiro para o bloco de controlo do servidor FTP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Início do servidor FTP bem sucedido.
- NX_PTR_ERROR (0x07) Ponteiro FTP inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Start the FTP Server “my_server”. */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a>nx_ftp_server_stop

Parar o servidor FTP

### <a name="prototype"></a>Prototype

```C
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Description

Este serviço para uma instância ftp server previamente criada e iniciada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **ftp_server_ptr** Ponteiro para o bloco de controlo do servidor FTP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Paragem do servidor FTP bem sucedida.
- NX_PTR_ERROR (0x07) Ponteiro FTP inválido.
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Stop the FTP Server “my_server”. */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
