---
title: Capítulo 2 - Instalação e utilização do Servidor Azure RTOS NetX DHCP
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente do servidor Azure RTOS NetX DHCP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 034a4d74c566fbfe94981a42b7e06e7f2ee79d25
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826791"
---
# <a name="chapter-2---installation-and-use-of-the-azure-rtos-netx-dhcp-server"></a>Capítulo 2 - Instalação e utilização do Servidor Azure RTOS NetX DHCP

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NetX DHCP.

## <a name="product-distribution"></a>Distribuição de Produtos

O Azure RTOS NetX DHCP Server pode ser obtido a partir do nosso repositório de código fonte pública em [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) . O pacote inclui dois ficheiros de origem e um ficheiro PDF que contém este documento, da seguinte forma:

- **nx_dhcp_server.h:** Ficheiro de cabeçalho para o Servidor DHCP netX
- **nx_dhcp_server.c**: Ficheiro C Fonte para o Servidor DHCP netX
- **nx_dhcp_server.pdf**: Descrição em PDF do NetX DHCP Server
- **demo_netx_dhcp_server.c**: Demonstração do Servidor NetX DHCP

## <a name="dhcp-installation"></a>Instalação DHCP

Para utilizar o NetX DHCP Server, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX está instalado. Por exemplo, se o NetX for instalado no diretório "*\threadx\arm7\green*", então os ficheiros *nx_dhcp_server.h* e *nx_dhpc_server.c* devem ser copiados para este diretório.

## <a name="using-netx-dhcp-server"></a>Usando o servidor DHCP NetX

A utilização do NetX DHCP Server é fácil. Basicamente, o código de aplicação deve incluir *nx_dhcp_server.h* depois de incluir *tx_api.h* e *nx_api.h,* para utilizar o ThreadX e o NetX, respectivamente. Uma vez *incluído nx_dhcp_server.h,* o código de aplicação é então capaz de fazer as chamadas de função DHCP especificadas mais tarde neste guia. O pedido também deve incluir *nx_dhcp_server.c* no processo de construção. Este ficheiro deve ser compilado da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação. Para obter mais detalhes sobre a utilização do NetX DHCP Server, consulte as seguintes secções [Requisitos do NetX DHCPServer](#requirements-of-the-netx-dhcp-server) e [Restrições do Servidor DHCP NetX](#constraints-of-the-netx-dhcp-server).

> [!NOTE]
> Uma vez que o DHCP utiliza os serviços de UDP NetX, o UDP deve ser ativado com a chamada *nx_udp_enable* antes de utilizar o DHCP.

## <a name="requirements-of-the-netx-dhcp-server"></a>Requisitos do Servidor DhCP NetX

O NetX DHCP Server requer uma porta de tomada UDP atribuída à conhecida porta DHCP 67. Para criar o Servidor DHCP, a aplicação deve criar um conjunto de pacotes com carga útil de pacotes de pelo menos 548 bytes mais cabeçalhos IP, UDP e Ethernet (que totalizam 44 bytes com 4 bytes de alinhamento).

Presume-se que o Servidor e o Cliente estão ambos a utilizar as definições de endereço de hardware Ethernet:

- **Tipo de hardware**: 1
- **Comprimento do hardware**: 6
- **Lúpulo**: 0

### <a name="multiple-client-sessions"></a>Múltiplas Sessões de Clientes

O NetX DHCP Server pode lidar com várias sessões de Cliente mantendo uma tabela de clientes DHCP ativos e o que 'estado' o Cliente está em, por exemplo, estados DHCP INIT, BOOT, SELECTING, REQUESTING, RENOVAR etc. Se o tempo de sessão expirar antes de receber a próxima mensagem do Cliente, a menos que esse Cliente esteja ligado a uma locação IP, o Servidor limpará os dados da sessão do Cliente e devolverá o endereço IP atribuído ao pool disponível. Se o Servidor receber várias mensagens DISCOVER do mesmo Cliente, o Servidor reinicia o tempo de saída da sessão e mantém o endereço IP reservado para o Cliente aceitar numa mensagem REQUEST subsequente.

O NetX DHCP Server também aceita o pedido de DHCP do cliente único, por exemplo, o Cliente apenas envia uma mensagem REQUEST. Isto pressupõe que o Cliente foi previamente atribuído a um contrato de arrendamento IP do servidor DHCP.

### <a name="setting-interface-specific-network-parameters-server-responses"></a>Definição de interface respostas de servidor de parâmetros de rede específicas

A aplicação pode definir os parâmetros do router, da máscara de sub-rede e do servidor DNS para cada interface que lida com os pedidos do Cliente DHCP, utilizando o serviço *nx_dhcp_set_interface_network_parameters.* Caso contrário, estes parâmetros estão indefinidos no gateway IP da interface primária do Servidor, na sua sub-rede de rede DHCP e no endereço IP do Servidor DHCP, respectivamente.

O Servidor DHCP inclui estes parâmetros nos dados de opção das mensagens DHCP que envia aos clientes DHCP.

### <a name="assigning-ip-addresses-to-the-client"></a>Atribuição de endereços IP ao Cliente

Se a mensagem Do Cliente DISCOVER não especificar um endereço IP solicitado, o Servidor DHCP pode utilizar um a partir da sua própria piscina. Se o Servidor não tiver endereços IP disponíveis, enviará ao Cliente uma mensagem NACK.

O Servidor DHPC NetX concederá o endereço IP solicitado na mensagem Cliente REQUEST desde que o endereço IP esteja disponível e possa ser encontrado na base de dados de endereços IP do Servidor. A aplicação cria a lista de endereços IP disponíveis do Servidor para a atribuição a Clientes DHCP utilizando o serviço *nx_dhcp_create_server_ip_address_list.* Se o Servidor não tiver os endereços IP solicitados ou for atribuído a outro anfitrião, enviará ao Cliente uma mensagem NACK.

Quando o Servidor DHCP recebe um pedido de Cliente, identifica esse Cliente utilizando exclusivamente o endereço MAC do Cliente no campo de endereços MAC do Cliente na mensagem DHCP. Se o Cliente alterar o seu endereço MAC ou for transferido para outro sub-redes, deverá enviar uma mensagem RELEASE para o Servidor para devolver o endereço IP de volta ao pool disponível e solicitar um novo endereço IP no estado INIT.

Consulte a figura 1.1 da secção **Sistema de Pequenos Exemplos** para obter mais detalhes. O número de endereços IP guardados na instância do Servidor DHCP está limitado ao tamanho do conjunto de endereços do servidor no bloco de controlo do servidor DHCP e definido pela opção configurável NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE.

### <a name="ip-address-lease-times"></a>Tempos de locação de endereços IP

O Servidor DHCP também aceitará o tempo de locação do Cliente pedido se esse tempo de locação for inferior ao tempo de locação padrão do Servidor, que é definido em opção configurável NX_DHCP_DEFAULT_LEASE_TIME. Os tempos de renovação e reencadernação atribuídos ao Cliente são de 50% e 85% do tempo de arrendamento, respectivamente, a menos que o tempo de arrendamento seja infinito (0xFFFFFFFF), caso em que os tempos de renovação e reencadernação também são definidos para o infinito.

### <a name="dhcp-server-timeouts"></a>Intervalos de tempo do servidor DHCP

O Servidor DHCP tem um tempo limite de sessão configurável para o utilizador, NX_DHCP_CLIENT_SESSION_TIMEOUT, para esperar pela próxima mensagem do Cliente DHCP, a menos que a sessão esteja concluída. O tempo de ício é reiniciado quando o Servidor recebe a próxima mensagem do Cliente, independentemente de ser a mesma mensagem enviada anteriormente.

### <a name="internal-error-handling"></a>Tratamento interno de erros

O Servidor DHCP recebe e processa pacotes de clientes DHCP na função *nx_dhcp_listen_for_messages.* Esta função irá descontinuar o processamento do atual pacote do Cliente DHCP se o pacote for inválido, ou se o Servidor DHCP encontrar um erro interno.n *x_dhcp_listen_for_messages* retorne um estado de erro. A linha do Servidor DHCP renuncia ao controlo brevemente do programador ThreadX antes de ligar para esta função para receber a próxima mensagem do Cliente DHCP. Na versão atual não existe suporte para registo de retornas de estado de erro a partir de *nx_dhcp_listen_for_messages.*

### <a name="option-55-parameter-request-list"></a>Opção 55: Lista de Pedidos de Parâmetros

O Servidor NetX DHCP deve ser configurado com um conjunto de opções para carregar para a lista de pedidos de parâmetros (55) na lista DE OFERTA e DHCPACK que transmite de volta para o Cliente. Estas opções devem incluir dados de configuração crítica de rede para a rede cliente e por padrão é definido como endereço IP router, máscara de sub-rede e servidor DNS. A lista de opções é uma lista delimitada espacial e definida no NX_DHCP_DEFAULT_SERVER_OPTION_LIST configurável do utilizador. Note-se que o número de opções especificadas nesta lista deve ser igual NX_DHCP_DEFAULT_OPTION_LIST_SIZE que também é definido pelo utilizador.

## <a name="constraints-of-the-netx-dhcp-server"></a>Constrangimentos do Servidor DhCP NetX

### <a name="dhcp-messages"></a>Mensagens DHCP

O Servidor DHCP NetX não verifica se um endereço IP não foi atribuído em outro lugar da rede antes de conceder o endereço IP ao Cliente. Se existem vários servidores DHCP, este pode ser o caso. *De acordo com o RFC 2131, é da responsabilidade do Cliente verificar que o endereço IP é único na sua rede* (por exemplo, pingando o endereço). Caso contrário, o Servidor deverá receber uma mensagem DECLINar com o endereço IP para atualizar a sua base de dados a partir do Cliente.

O Servidor DHCP NetX não emite mensagens FORCE_RENEW. Cabe ao Cliente DHCP renovar o seu contrato de endereço IP. No entanto, o Servidor DHCP monitoriza o tempo restante em todos os endereços IP atribuídos na sua base de dados. Quando uma locação de endereço IP expira, esse endereço IP é devolvido ao pool de endereços IP disponíveis. Cabe, portanto, ao Cliente renovar/reencambido ativamente o seu contrato de endereço IP.

Os dados da sessão são apurados assim que o Cliente é concedido ("vinculado") a um contrato de arrendamento IP (ou um existente é renovado). Se um pacote de Cliente provar falso, ou o Cliente se apagar entre respostas, os dados da sessão são eliminados.

### <a name="saving-data-between-reboots"></a>Guardar dados entre reboots

O NetX DHCP Server guarda os dados do Cliente, incluindo os parâmetros de pedido do DHCP numa tabela de registos do Cliente. Esta tabela não é armazenada em memória não volátil, por isso, se o anfitrião do Servidor DHCP tiver de reiniciar, essa informação não é guardada entre reinicializações.

O Servidor DHCP NetX guarda dados de locação de endereços IP numa tabela de endereços IP. Esta tabela não é armazenada em memória não volátil, por isso, se o anfitrião do Servidor DHCP tiver de reiniciar, essa informação não é guardada entre reinicializações.

### <a name="relay-agents"></a>Agentes de retransmissão

O Servidor DHCP NetX está configurado com um endereço IP zero para o campo 'Relay agent' porque não suporta fora dos pedidos de DHCP da rede.

## <a name="small-example-system"></a>Sistema de Pequenos Exemplos

Um exemplo de como é fácil utilizar o Servidor DHCP NetX é descrito na Figura 1.1 que aparece abaixo. Neste exemplo, o DHCP inclui o ficheiro *nx_dhcp_server.h* é trazido na linha 5. O tamanho da pilha de fio do servidor DHCP, o tamanho da pilha de fio IP e o tamanho da pilha de fio de teste são todos definidos nas linhas 7-13.

Em primeiro lugar, é criada uma tarefa de fio de teste opcional para parar, reiniciar e eventualmente eliminar o servidor DHCP com a função "*test_thread_entry*" na linha 57. Um bloco de controlo do servidor DHCP "*dhcp_server*" é definido como uma variável global na linha 20. Note que o conjunto de pacotes do servidor é criado com pacotes com uma carga útil pelo menos tão grande quanto a mensagem DHCP padrão (548 bytes mais bytes ip e cabeçalho UDP). Depois de criar com sucesso uma instância IP para o Servidor DHCP, a aplicação cria o Servidor DHCP na linha 96. Em seguida, a aplicação permite que a instância IP do servidor seja ativada por UDP. Antes de iniciar o Servidor DHCP, a lista de endereços IP disponível é criada na linha 137 utilizando o serviço *nx_dhcp_create_server_ip_address_list.* Os parâmetros de configuração da rede são definidos na seguinte linha 138 utilizando o serviço *nx_dhcp_set_interface_network_parameters,* os serviços do Servidor DHCP ficam disponíveis quando a aplicação chama o *nx_dhcp_server_start* na linha 141. A tarefa do fio de teste demonstra a utilização de parar e reiniciar o servidor DHCP.

```c
/* This is a small demo of NetX DHCP Server for the high-performance NetX TCP/IP stack. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nx_dhcp_server.h"

#define     DEMO_TEST_STACK_SIZE       2048
#define     DEMO_SERVER_STACK_SIZE     2048
#define     SERVER_IP_ADDRESS_LIST     "192.168.2.10 192.168.2.11 192.168.2.12"
#define     PACKET_PAYLOAD             1000
#define     PACKET_POOL_SIZE           (PACKET_PAYLOAD * 10)
#define     SERVER_IP_THREAD_STACK     2048

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD          test_thread;
NX_PACKET_POOL     server_pool;
NX_IP              server_ip;
NX_DHCP_SERVER     dhcp_server;

/* Define the counters used in the demo application... */

ULONG             state_changes;

/* Define thread prototypes. */

void     test_thread_entry(ULONG thread_input);
void     nx_etherDriver_mcf5485(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void     tx_application_define(void *first_unused_memory)
{

CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create the test thread. */
    status = tx_thread_create(&test_thread, "test thread", test_thread_entry, 0,
                pointer, TEST_STACK_SIZE, 1, 1, TX_NO_TIME_SLICE, TX_DONT_START);

    if (status)
    {
        printf("Error with DHCP test thread create. Status 0x%x\r\n", status);
        return;
    }

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create the DHCP Server packet pool. */
    status = nx_packet_pool_create(&server_pool, "NetX Main Packet Pool",
                                PACKET_PAYLOAD, pointer, PACKET_POOL_SIZE);
                                pointer = pointer + PACKET_POOL_SIZE;

    /* Check for pool creation error. */
    if (status)
    {
        printf("Error with DHCP server packet pool create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server IP instance. */
    status = nx_ip_create(&server_ip, "NetX DHCP Server IP", NX_DHCP_SERVER_IP_ADDRESS,
                        0xFFFFFF00UL, &server_pool, nx_etherDriver_mcf5485, pointer,
                        SERVER_IP_THREAD_STACK, 1);

    pointer = pointer + DEMO_IP_THREAD_STACK;

    /* Check for IP create errors. */
    if (status)
    {
        printf("Error with DHCP server IP task create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server instance. */
    status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                    DEMO_SERVER_STACK_SIZE,"DHCP Server", &server_pool);

    if (status)
    {
        printf("Error with DHCP server create. Status 0x%x\r\n", status);
        return;
    }

    pointer = pointer + DEMO_SERVER_STACK_SIZE;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    status = nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors. */
    if (status)
    {
        printf("Error with ARP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable UDP traffic. */
    status = nx_udp_enable(&server_ip);

    /* Check for UDP enable errors. */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable ICMP to enable the ping utility. */
    status = nx_icmp_enable(&server_ip);

    /* Check for errors. */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
    }

    status = nx_dhcp_create_server_ip_address_list(&dhcp_server, iface_index,
                START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);
    status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                                        NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                                        IP_ADDRESS(10,0,0,1));

    /* Start the DHCP Server. */
    status = nx_dhcp_server_start(&dhcp_server);

    tx_thread_resume(&test_thread);
}

/* Define the test thread. */
void     test_thread_entry(ULONG thread_input)
{

UINT     status;
UINT     keep_spinning;

    /* Just let the test thread be idle till we're ready to shut things down. */
    keep_spinning = 1;
    while(keep_spinning)
    {
        tx_thread_sleep(300);
    }

    printf("Stopping the server...\n");
    status = nx_dhcp_server_stop(&dhcp_server);
    if (status)
    {
        printf("Error with DHPC server stop. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(500);

    printf("Starting the server...\n");
    status = nx_dhcp_server_start(&dhcp_server);
    if (status)
    {
        printf("Error with DHPC server start. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(600);

    printf("Stopping the server for good...\n");
    status = nx_dhcp_server_stop(&dhcp_server);
    if (status)
    {
        printf("Error with DHPC server stop. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(200);

    printf("Deleting the server...\n");
    status = nx_dhcp_server_delete(&dhcp_server);
    if (status)
    {
        printf("Error with DHCP server delete. Status 0x%x\r\n", status);
        return;
    }
}
```

Figura 1.1 Exemplo Aplicação do Servidor DHCP NetX

## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração para a construção do NetX DHCP Server. A seguinte lista descreve cada uma em detalhe:  
  
- **NX_DISABLE_ERROR_CHECKING**: Esta opção remove a verificação básica de erros dhcp. É normalmente usado após a depurada aplicação.  
- **NX_DHCP_SERVER_THREAD_PRIORITY**: Esta opção especifica a prioridade da linha do Servidor DHCP. Por predefinição, este valor especifica que o fio DHCP funciona na prioridade 2.
- **NX_DHCP_TYPE_OF_SERVICE**: Esta opção especifica o tipo de serviço necessário para os pedidos de UDP da DHCP. Por predefinição, este valor é definido como NX_IP_NORMAL para indicar o serviço normal de pacotes IP.
- **NX_DHCP_FRAGMENT_OPTION**: Ativar fragmentos para pedidos de UDP DHCP. Por padrão, este valor é definido para NX_DONT_FRAGMENT para desativar a fragmentação do UDP.
- **NX_DHCP_TIME_TO_LIVE**: Especifica o número de routers que o pacote pode passar antes de ser descartado. O valor predefinido é 0x80.
- **NX_DHCP_QUEUE_DEPTH** Especifica o número de pacotes que a tomada do Servidor DHCP mantém antes de descarregar a fila. O valor predefinido é 5.
- **NX_DHCP_PACKET_ALLOCATE_TIMEOUT**: Especifica o tempo limite nos tiques de tempo para o Servidor DhCP NetX aguardar a atribuição de um pacote a partir da sua piscina de pacotes. O valor predefinido é definido para NX_IP_PERIODIC_RATE.
- **NX_DHCP_SUBNET_MASK:** Esta é a máscara de sub-rede com a qual o Cliente DHCP deve ser configurado. O valor predefinido é definido para 0xFFFFFF00.
- **NX_DHCP_FAST_PERIODIC_TIME_INTERVAL**: Este é um período de tempo limite nos tiques temporizadores para o temporizador do Servidor DHCP para verificar o tempo restante da sessão e manusear sessões que tenham esgotado o tempo.
- **NX_DHCP_SLOW_PERIODIC_TIME_INTERVAL**: Este é um período de tempo limite nos tiques temporizadores para o temporizador lento do Servidor DHCP para verificar o tempo de locação do endereço IP restante e lidar com o arrendamento que tenha esgotado o tempo.
- **NX_DHCP_CLIENT_SESSION_TIMEOUT**: Este é um período de tempo limite no temporizador que o Servidor DHCP aguarda para receber a próxima mensagem do Cliente DHCP.
- **NX_DHCP_DEFAULT_LEASE_TIME**: Este é o tempo de locação ip address em segundos atribuídos ao Cliente DHCP, e a base para a computação dos tempos de renovação e reencadernação também atribuídos ao Cliente. O valor predefinido é definido para 0xFFFFFFFF (infinito).
- **NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE**: Este é o tamanho da matriz do Servidor DHCP para a posse de endereços IP disponíveis para a atribuição ao Cliente. O valor predefinido é de 20.
- **NX_DHCP_CLIENT_RECORD_TABLE_SIZE**: Este é o tamanho da matriz do Servidor DHCP para deter registos do Cliente. O valor predefinido é de 50.
- **NX_DHCP_CLIENT_OPTIONS_MAX**: Este é o tamanho da matriz na instância do Cliente DHCP para a realização de todas as opções solicitadas na lista de pedidos de parâmetros na sessão em curso. O valor predefinido é 12.
- **NX_DHCP_OPTIONAL_SERVER_OPTION_LIST**: Este é o tampão que detém a lista padrão do Servidor DHCP de opções a fornecer ao cliente DHCP atual na lista de pedidos de parâmetros. O padrão é "1 36".
- **NX_DHCP_OPTIONAL_SERVER_OPTION_SIZE**: Este é o tamanho da matriz para manter a lista padrão de opções do Servidor DHCP. O valor predefinido é 3.
- **NX_DHCP_SERVER_HOSTNAME_MAX**: Este é o tamanho do tampão para segurar o nome do anfitrião do Servidor. O valor predefinido é 32.
- **NX_DHCP_CLIENT_HOSTNAME_MAX**: Este é o tamanho do tampão para manter o nome de anfitrião do Cliente na sessão atual do Cliente do Servidor DHCP. O valor predefinido é 32.
