---
title: Capítulo 2 - Instalação e utilização do Protocolo Azure RTOS NetX Duo Ponto a Ponto (PPP)
description: Este capítulo contém uma descrição de várias questões relacionadas com a instalação, configuração e utilização do componente Azure RTOS NETX Duo Point-to-Point Protocol (PPP).
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 141197daa87b40ebe2ea34ff096a0b01b260e9296a33e3b678f11400d5d46ab6
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797165"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-point-to-point-protocol-ppp"></a>Capítulo 2 - Instalação e utilização do Protocolo Azure RTOS NetX Duo Ponto a Ponto (PPP)

Este capítulo contém uma descrição de várias questões relacionadas com a instalação, configuração e utilização do componente Azure RTOS NETX Duo Point-to-Point Protocol (PPP).

## <a name="product-distribution"></a>Distribuição de Produtos

O pacote Azure RTOS NetX Duo Point-to-Point Protocol (PPP) está disponível em <https://github.com/azure-rtos/netxduo> . O pacote inclui os seguintes ficheiros:

- **nx_ppp.h**: Ficheiro de cabeçalho para PPP para NetX
- **nx_ppp.c**: Ficheiro C Fonte de PPP para NetX
- **nx_ppp.pdf**: Descrição pdf de PPP para NetX
- **demo_netx_ppp.c**: Demonstração de PPP NetX

## <a name="ppp-installation"></a>Instalação PPP

Para utilizar pPP para netX, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX está instalado. Por exemplo, se o NetX for instalado no diretório "*\threadx\arm7\green*", então os ficheiros *nx_ppp.h* e *nx_ppp.c* devem ser copiados para este diretório.

## <a name="using-ppp"></a>Utilização de PPP

A utilização de PPP para NetX é fácil. Basicamente, o código de aplicação deve incluir *nx_ppp.h* depois de incluir *tx_api.h* e *nx_api.h,* para utilizar o ThreadX e o NetX, respectivamente. Uma vez *incluído nx_ppp.h,* o código de aplicação é então capaz de fazer as chamadas de função PPP especificadas mais tarde neste guia. O pedido também deve incluir *nx_ppp.c* no processo de construção. Este ficheiro deve ser compilado da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação. Isto é tudo o que é necessário para usar pPP NetX.

## <a name="using-modems"></a>Utilização de Modems

Se for necessário um modem para a ligação à internet, são necessárias algumas considerações especiais para utilizar o produto NetX PPP. Basicamente, a utilização de um modem introduz lógica de inicialização adicional e lógica para a perda de comunicação. Além disso, a maior parte da lógica adicional do modem é feita fora do contexto da PPP NetX. O fluxo básico de utilização do PPP NetX com um modem é mais ou menos assim:

1. Inicializar modem

1. Dial Internet Service Provider (ISP)

1. Aguarde por Conexão

1. Aguarde o pedido de userID

1. Iniciar a PPP netX [PPP em funcionamento]

1. Perda de comunicação

1. Parar pPP netx (ou reiniciar via nx_ppp_restart)

### <a name="initialize-modem"></a>Inicializar modem

Utilizando a rotina de saída em série de baixo nível da aplicação, o modem é inicializado através de uma série de comandos de caracteres ASCII (ver documentação do modem para mais detalhes).

### <a name="dial-internet-service-provider"></a>Ligue o Fornecedor de Serviços de Internet

Utilizando a rotina de saída em série de baixo nível da aplicação, o modem é instruído para marcar o ISP. Por exemplo, o seguinte é típico de uma cadeia ASCII usada para marcar um ISP no número 123-4567:

"ATDT123456\r"

### <a name="wait-for-connection"></a>Aguarde por Conexão

Neste momento, a aplicação aguarda para receber indicação do modem de que foi estabelecida uma ligação. Isto é conseguido procurando caracteres da rotina de entrada em série de baixo nível da aplicação. Normalmente, os modems devolvem uma cadeia ASCII "CONNECT" quando uma ligação foi estabelecida.

### <a name="wait-for-user-id-prompt"></a>Aguarde a solicitação de id do utilizador

Uma vez estabelecida a ligação, o pedido deve agora aguardar um pedido inicial de login do ISP. Isto normalmente assume a forma de uma cadeia ASCII como "Login?"

### <a name="start-netx-ppp"></a>Iniciar NetX PPP

Neste momento, o PPP NetX pode ser iniciado. Isto é conseguido através da chamada para o serviço *nx_ppp_create* seguido pelo serviço *nx_ip_create.* Podem também ser necessários serviços adicionais para permitir o PAP e configurar os endereços IP PPP. Para mais informações, por favor leia as seguintes secções.

### <a name="loss-of-communication"></a>Perda de comunicação

Uma vez iniciada a PPP, qualquer informação não PPP é transmitida para a rotina de "manuseamento de pacotes inválidos" a aplicação especificada para o serviço *nx_ppp_create.* Normalmente, os modems enviam uma cadeia ASCII como "NO CARRIER" quando a comunicação é perdida com o ISP. Quando a aplicação receber um pacote não PPP com tais informações, deve proceder para parar a instância de PPP NetX ou reiniciar a máquina estatal de PPP através da API *nx_ppp_restart.*

### <a name="stop-netx-ppp"></a>Parar o PPP netx

Parar a PPP NetX é bastante simples. Basicamente, todas as tomadas criadas devem ser desvinculados e apagadas. Em seguida, elimine a instância IP através do serviço *nx_ip_delete.* Uma vez eliminada a instância IP, o serviço *nx_ppp_delete* deve ser chamado para terminar o processo de paragem das PPP. Neste momento, o pedido pode agora tentar restabelecer a comunicação com o ISP.

## <a name="small-example-system"></a>Sistema de Pequenos Exemplos

Um exemplo que ilustra como é fácil utilizar pPP NetX é descrito na Figura 1.1 que aparece abaixo. Neste exemplo, as PPP incluem ficheiro *nx_ppp.h* é trazido na linha 3. Em seguida, pPP é criado em *"tx_application_define"* na linha 56. O bloco de controlo de PPP "*my_ppp*" foi definido como uma variável global na linha 9 anteriormente. 

>[!NOTE]
>As PPP devem ser criadas antes da criação da instância IP. Após a criação bem sucedida de PPP e IP, o fio "*my_thread*" espera que a ligação PPP se viva na linha 98. Na linha 104, tanto as PPP como a NetX estão totalmente operacionais.

O único item não mostrado neste exemplo é o byte em série da aplicação receber ISR. Terá de chamar *nx_ppp_byte_receive* com "*my_ppp*" e o byte recebido como parâmetros de entrada.

```c
0001 #include   "tx_api.h"
0002 #include   "nx_api.h"
0003 #include   "nx_ppp.h"
0004
#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_PPP                  my_ppp;

/* Define function prototypes. */

void    my_thread_entry(ULONG thread_input);
void    my_serial_driver_byte_output(UCHAR byte);
void    my_invalid_packet_handler(NX_PACKET *packet_ptr);
 
/* Define main entry point. */
intmain()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
 }


/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;

/* Setup the working pointer. */
pointer =  (CHAR *) first_unused_memory;

/* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                  pointer, DEMO_STACK_SIZE, 
                  2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                    1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error. */
    if (status)
        error_counter++;

    /* Create a PPP instance. */
    status = nx_ppp_create(&my_ppp, “My PPP”, &my_ip, pointer, 1024, 2, 
                           &my_pool, my_invalid_packet_handler, my_serial_driver_byte_output);
    pointer =  pointer + 1024;
    /* Check for PPP creation pool. */
    if (status)
        error_counter++;

    /* Create an IP instance with the PPP driver. */
    status = nx_ip_create(&my_ip,"My NetX IP Instance", 
                           IP_ADDRESS(216,2,3,1), 0xFFFFFF00, &my_pool, 
                           nx_ppp_driver, pointer, DEMO_STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors. */
    if (status)
        error_counter++;

    /* Enable ICMP for my IP Instance. */
    status =  nx_icmp_enable(&my_ip);

    /* Check for ICMP enable errors. */
    if (status)
        error_counter++;

    /* Enable UDP. */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
}

/* Define my thread. */
void    my_thread_entry(ULONG thread_input)
{

UINT        status;
ULONG       ip_status;
NX_PACKET   *my_packet;

/* Wait for the PPP link in my_ip to become enabled. */
    status =  nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,&ip_status,3000);

    /* Check for IP status error. */
    if (status) 
        return;

    /* Link is fully up and operational. All NetX activities 
    are now available. */

}
```
## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração para a construção de PPP para NetX. A seguinte lista descreve cada uma em detalhe:

- **NX_DISABLE_ERROR_CHECKING**: Definida, esta opção remove a verificação básica de erros de PPP. É normalmente usado após a depurada aplicação.
- **NX_PPP_PPPOE_ENABLE**: Se definido, pPP pode transmitir pacote sobre Ethernet
- **NX_PPP_BASE_TIMEOUT**: Isto define a taxa de período (em carraças tempor, que a tarefa de linha PPP é despertada para verificar se há eventos de PPP. O valor predefinido é de 1*NX_IP_PERIODIC_RATE (100 carraças).
- **NX_PPP_DISABLE_INFO**: Se definido, a recolha interna de informações sobre PPP é desativada.
- **NX_PPP_DEBUG_LOG_ENABLE**: Se definido, o registo interno de depurg de PPP está ativado.
- **NX_PPP_DEBUG_LOG_PRINT_ENABLE**:Se definido, a *impressão* interna de registo de PPP depurado para *stdio* está ativada. Isto só é válido se o registo de depurado também estiver ativado.
- **NX_PPP_DEBUG_LOG_SIZE**: Tamanho do registo de depurg (número de entradas no registo de depurg). Ao chegar à última entrada, a captura de depurges envolve-se à primeira entrada e substitui todos os dados previamente capturados. O valor predefinido é de 50.
- **NX_PPP_DEBUG_FRAME_SIZE**: Quantidade máxima de dados capturados a partir de uma carga útil de pacotes recebidos e guardados para depurar a saída. O valor predefinido é de 50.
- **NX_PPP_DISABLE_CHAP**: Se definido, a lógica interna de PPP CHAP é removida, incluindo a lógica de digestão MD5.
- **NX_PPP_DISABLE_PAP**: Se definido, a lógica interna do PPP PAP é removida.
- **NX_PPP_DNS_OPTION_DISABLE**: Se definido, a opção principal do servidor DNS é desativada na resposta IPCP. Por padrão esta opção não está definida.
- **NX_PPP_DNS_ADDRESS_MAX_RETRIES**: Isto especifica quantas vezes o anfitrião de PPP solicitará um endereço DNS Server do par no estado IPCP. Isto não tem efeito se NX_PPP_DNS_OPTION_DISABLE for definido. O valor predefinido é 2.
- **NX_PPP_HASHED_VALUE_SIZE**: Especifica o tamanho das cordas de "valor hashed" utilizadas na autenticação CHAP. O valor predefinido é definido para 16 bytes, mas pode ser redefinido antes da inclusão de *nx_ppp.h.*
- **NX_PPP_MAX_LCP_PROTOCOL_RETRIES**: Isto define o número máximo de retrações se as PPP esgotarem antes de enviar outra mensagem de pedido de configuração LCP. Quando este número é atingido, o aperto de mão de PPP é abortado e o estado do link está reduzido. O valor predefinido é de 20.
- **NX_PPP_MAX_PAP_PROTOCOL_RETRIES**: Isto define o número máximo de retrações se o PPP tiver esgotado antes de enviar outra mensagem de pedido de autenticação de PAP. Quando este número é atingido, o aperto de mão de PPP é abortado e o estado do link está reduzido. O valor predefinido é de 20.
- **NX_PPP_MAX_CHAP_PROTOCOL_RETRIES**: Isto define o número máximo de retrações se as PPP se esgotarem antes de enviarem outra mensagem de desafio CHAP. Quando este número é atingido, o aperto de mão de PPP é abortado e o estado do link está reduzido. O valor predefinido é de 20.
- **NX_PPP_MAX_IPCP_PROTOCOL_RETRIES**: Isto define o número máximo de retrações se as PPP esgotarem antes de enviar outra mensagem de pedido de configuração ipcp. Quando este número é atingido, o aperto de mão de PPP é abortado e o estado do link está reduzido. O valor predefinido é de 20.
- **NX_PPP_MRU**: Especifica a Unidade máxima de Receção (MRU) para PPP. Por predefinição, este valor é de 1.500 bytes (o valor mínimo). Esta definição pode ser definida pela aplicação antes da inclusão do *nx_ppp.h*.
- **NX_PPP_MINIMUM_MRU**: Especifica o mínimo de MRU recebido numa mensagem de pedido de configuração LCP. Por predefinição, este valor é de 1.500 bytes (o valor mínimo). Esta definição pode ser definida pela aplicação antes da inclusão do *nx_ppp.h*.
- **NX_PPP_NAME_SIZE**: Especifica o tamanho das cordas de "nome" utilizadas na autenticação. O valor predefinido é definido para 32bytes, mas pode ser redefinido antes da inclusão de *nx_ppp.h.
- **NX_PPP_PASSWORD_SIZE**: Especifica o tamanho das cordas "password" utilizadas na autenticação. O valor predefinido é definido para 32bytes, mas pode ser redefinido antes da inclusão de *nx_ppp.h.*
- **NX_PPP_PROTOCOL_TIMEOUT**: Isto define a opção de espera (em segundos) para que a tarefa de PPP receba uma resposta a uma mensagem de pedido de protocolo de PPP. O valor predefinido é de 4 segundos.
- **NX_PPP_RECEIVE_TIMEOUTS**: Isto define o número de vezes que o fio de PPP tempos de tarefa à espera de receber o próximo caracter num fluxo de mensagens PPP. A partir daí, a PPP lança o pacote e começa a esperar para receber a próxima mensagem de PPP. O valor predefinido é 4.
- **NX_PPP_SERIAL_BUFFER_SIZE**: Especifica o tamanho do tampão de série de caracteres de receção. Por padrão, este valor é de 3.000 bytes. Esta definição pode ser definida pela aplicação antes da inclusão do *nx_ppp.h*.
- **NX_PPP_TIMEOUT**: Isto define a opção de espera (em carraças tempor, para alocar pacotes para transmitir dados, bem como dados de série de PPP tampão em pacotes para enviar para a camada IP. O valor predefinido é de 4*NX_IP_PERIODIC_RATE (400 carraças).
- **NX_PPP_THREAD_TIME_SLICE**: Opção de corte de tempo para fios de PPP. Por padrão, este valor é TX_NO_TIME_SLICE. Esta definição pode ser definida pela aplicação antes da inclusão do *nx_ppp.h*.
- **NX_PPP_VALUE_SIZE**: Especifica o tamanho das cordas de "valor" utilizadas na autenticação CHAP. O valor predefinido é definido para 32bytes, mas pode ser redefinido antes da inclusão de nx_ppp.h.