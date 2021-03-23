---
title: Capítulo 2 - Instalação e utilização do Cliente Azure RTOS NetX DHCP
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente cliente Azure RTOS NetX DHCP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9224a4df70b8199032066e30108250a3baeb65f5
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826798"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-dhcp-client"></a>Capítulo 2 - Instalação e utilização do Cliente Azure RTOS NetX DHCP

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NetX DHCP.

## <a name="product-distribution"></a>Distribuição de Produtos

DHCP para NetX está disponível em [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) . O pacote inclui dois ficheiros de origem e um ficheiro PDF que contém este documento, da seguinte forma:

- **nx_dhcp.h** Arquivo de cabeçalho para DHCP para NetX

- **nx_dhcp.c** C Arquivo de origem para DHCP para NetX

- **nx_dhcp.pdf** Descrição em PDF do DHCP para o NetX

- **demo_netx_dhcp.c** Demonstração do NetX DHCP

- **demo_netx_multihome_dhcp_client.c** Demonstração do cliente NetX DHCP de DHCP em várias interfaces

## <a name="dhcp-installation"></a>Instalação DHCP

Para utilizar o DHCP para o NetX, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX está instalado. Por exemplo, se o NetX for instalado no diretório "*\threadx\arm7\green*" então os ficheiros *nx_dhcp.h* e *nx_dhcp.c* devem ser copiados para este diretório.

## <a name="using-dhcp"></a>Utilização do DHCP

A utilização do DHCP para o NetX é fácil. Basicamente, o código de aplicação deve incluir *nx_dhcp.h* depois de incluir *tx_api.h* e *nx_api.h,* para utilizar o ThreadX e o NetX, respectivamente. Uma vez *incluído nx_dhcp.h,* o código de aplicação é então capaz de fazer as chamadas de função DHCP especificadas mais tarde neste guia. O pedido também deve incluir *nx_dhcp.c* no processo de construção. Este ficheiro deve ser compilado da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação. Isto é tudo o que é necessário para usar o NetX DHCP.

Note que uma vez que o DHCP utiliza os serviços de UDP NetX, o UDP deve ser ativado com a *chamada nx_udp_enable* antes de utilizar o DHCP.

Para obter um endereço IP previamente atribuído, o Cliente DHCP pode iniciar o processo DHCP com a mensagem Request e o Option 50 "Endereço IP Solicitado" para o Servidor DHCP. O Servidor DHCP responderá com uma mensagem ACK se conceder o endereço IP ao Cliente ou a um NACK se recusar. Neste último caso, o Cliente DHCP reinicia o processo DHCP no estado do Init com uma mensagem Discover e sem endereço IP solicitado. A aplicação de anfitrião cria primeiro o Cliente DHCP, depois liga para o serviço API *nx_dhcp_request_client_ip* para definir o endereço IP solicitado antes de iniciar o processo DHCP com *nx_dhcp_start*. Um exemplo de pedido dhCP é fornecido em outros lugares neste documento para mais detalhes.

## <a name="in-the-bound-state"></a>No Estado Vinculado

Enquanto o Cliente DHCP se encontra no estado vinculado, o fio do Cliente DHCP processa o Estado cliente uma vez por intervalo (conforme especificado por NX_DHCP_TIME_INTERVAL) e decrementa o tempo restante no contrato de arrendamento IP atribuído ao Cliente. Quando o tempo de renovação tiver decorrido, o estado do Cliente DHCP é atualizado para o estado DE RENOVAÇÃO onde o Cliente solicitará uma renovação do Servidor DHCP.


## <a name="sending-dhcp-messages-to-the-server"></a>Envio de mensagens DHCP para o servidor

O Cliente DHCP dispõe de serviços API que permitem ao anfitrião enviar uma mensagem para o Servidor DHCP. Note que estes serviços NÃO se destinam à aplicação de anfitrião para executar manualmente o protocolo do Cliente DHCP, uma vez que enviam a mensagem principalmente sem atualizar necessariamente o estado interno do Cliente DHCP.

  - *nx_dhcp_release:* isto envia uma mensagem RELEASE para o Servidor quando a aplicação do anfitrião está a sair da rede ou precisa de abdicar do seu endereço IP.

  - *nx_dhcp_decline:* isto envia uma mensagem DECLINAR para o Servidor se a aplicação do anfitrião determinar independentemente do Cliente DHCP que o seu endereço IP já está a ser utilizado.

  - *nx_dhcp_forcerenew:* isto envia uma mensagem FORCERENEW para o Servidor

  - *nx_dhcp_send_request*: Isto requer como argumento um tipo de mensagem DHCP, conforme especificado em *nx_dhcp.h*, e envia a mensagem para o Servidor. Esta posição destina-se principalmente ao envio da mensagem DHCP INFORM.

Consulte "*Descrição dos Serviços DHCP*" para obter mais informações sobre estes serviços em outros lugares deste documento.

## <a name="starting-and-stopping-the-dhcp-client"></a>Iniciar e Parar o Cliente DHCP

Para parar o Cliente DHCP, independentemente de ter alcançado um estado vinculado, a aplicação de anfitrião chama *nx_dhcp_stop*.

Para reiniciar um cliente DHCP, a aplicação de anfitrião deve primeiro parar o Cliente DHCP usando o serviço *nx_dhcp_stop* acima descrito. Em seguida, o anfitrião pode *chamá nx_dhcp_start* para retomar o Cliente DHCP. Se a aplicação anfitriã pretender limpar um perfil de Cliente DHCP anterior, por exemplo, um obtido a partir de um servidor DHCP anterior em outra rede, a aplicação do anfitrião deve ligar *para nx_dhcp_reinitialize* para executar esta tarefa internamente antes de ligar nx_dhcp_start.

Uma sequência típica pode ser:

```C
nx_dhcp_stop(&my_dhcp);

nx_dhcp_reinitialize(&my_dhcp);

nx_dhcp_start(&my_dhcp);
```

Para aplicações DHCP em execução apenas numa única interface DHCP, parar o Cliente DHCP também inativa o temporizador DHCP CLIENT. Assim, já não está a acompanhar o tempo que resta no arrendamento IP. Parar o Cliente DHCP numa determinada interface não irá inativar o temporizador do Cliente DHCP, mas irá parar as atualizações do temporizador para o tempo restante no aluguer IP nessa interface.

Portanto, parar o Cliente DHCP não é aconselhável a menos que a aplicação de anfitrião exija reiniciar ou mudar de rede.

## <a name="using-the-dhcp-client-with-auto-ip"></a>Utilização do Cliente DHCP com IP automático

O Cliente NetX DHCP trabalha em simultâneo com o protocolo AUTO IP em aplicações onde DHCP e Auto IP garantem um endereço onde um Servidor DHCP não está garantido para estar disponível ou responder. No entanto, se o anfitrião não conseguir detetar um Servidor ou obter um endereço IP atribuído, pode mudar para o protocolo IP automático para um endereço IP local. No entanto, antes de o fazer, é aconselhável parar temporariamente o Cliente DHCP enquanto o AUTO IP passa pelas fases de "sonda" e "defesa". Uma vez atribuído um endereço IP automático ao anfitrião, o Cliente DHCP pode ser reiniciado e se um Servidor DHCP ficar disponível, o endereço IP do anfitrião pode aceitar o endereço IP oferecido pelo Servidor DHCP enquanto a aplicação estiver em execução.

O NetX Auto IP tem uma notificação de alteração de endereço para o anfitrião monitorizar as suas atividades em caso de alteração de endereço IP.

## <a name="small-example-system"></a>Sistema de Pequenos Exemplos

Um exemplo de como a utilização do NetX é descrita na Figura 1.1 abaixo. O Cliente DHCP é criado "*my_thread_entry*" na linha 101. Após a criação bem sucedida, o processo DHCP é iniciado na chamada para *nx_dhcp_start* na linha 108. Neste momento, inicia-se a tentativa do Cliente DHCP de contactar o servidor DHCP. Durante este processo, o código de aplicação aguarda que um endereço IP válido seja registado na instância IP utilizando o serviço *nx_ip_status_check* (ou *nx_ip_interface_status_check* para uma interface secundária) a partir da linha 95. Isto é mais comumente feito em loop com uma opção de espera mais curta.

Após a linha 127, o DHCP recebeu um endereço IP válido e a aplicação pode então prosseguir, utilizando os serviços NetX TCP/IP conforme pretendido.

```C
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nx_dhcp.h"

#define   DEMO_STACK_SIZE     4096
TX_THREAD        my_thread;
NX_PACKET_POOL     my_pool;
NX_IP          my_ip;
NX_DHCP         my_dhcp;

/* Define function prototypes. */

void  my_thread_entry(ULONG thread_input);
void  my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
{

  /* Enter the ThreadX kernel. */
  tx_kernel_enter();
}


/* Define what the initial system looks like. */

void  tx_application_define(void *first_unused_memory)
{

CHAR  *pointer;
UINT  status;

  
  /* Setup the working pointer. */
  pointer = (CHAR *) first_unused_memory;

  /* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0, 
            pointer, DEMO_STACK_SIZE, 
            2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Initialize the NetX system. */
  nx_system_initialize();

  /* Create a packet pool. */
  status = nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                     1024, pointer, 64000);
  pointer = pointer + 64000;

  /* Check for pool creation error. */
  if (status)
    error_counter++;

  /* Create an IP instance without an IP address. */
  status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
      0xFFFFFF00, &my_pool, my_netx_driver, pointer, 
      DEMO_STACK_SIZE, 1);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Check for IP create errors. */
  if (status)
    error_counter++;

  /* Enable ARP and supply ARP cache memory for my IP Instance. */
  status = nx_arp_enable(&my_ip, (void *) pointer, 1024);
  pointer = pointer + 1024;

  /* Check for ARP enable errors. */
  if (status)
    error_counter++;

  /* Enable UDP. */
  status = nx_udp_enable(&my_ip);
  if (status)
    error_counter++;
}


/* Define my thread. */

void  my_thread_entry(ULONG thread_input)
{

UINT    status;
ULONG    actual_status;
NX_PACKET  *my_packet;

  /* Wait for the link to come up. */
  do
  {

    /* Get the link status. */
    status = nx_ip_status_check(&my_ip, NX_IP_LINK_ENABLED, 
                            &actual_status, 100);

  } while (status != NX_SUCCESS);

  /* Create a DHCP instance. */
  status = nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

  /* Check for DHCP create error. */
  if (status)
    error_counter++;

  /* Start DHCP. */
  nx_dhcp_start(&my_dhcp);

  /* Check for DHCP start error. */
  if (status)
    error_counter++;

  /* Wait for IP address to be resolved through DHCP. */
  nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                        (ULONG *) &status, 100000);

  /* Check to see if we have a valid IP address. */
  if (status)
  {
    error_counter++;
    return;
  }
  else
  {

        /* Yes, a valid IP address is now on lease… All NetX
      services are available.
  }
}
```

Figura 1.1 Exemplo da utilização do DHCP com o NetX

## <a name="multi-server-environments"></a>Ambientes multi-servidores

Nas redes onde existe mais de um Servidor DHCP, o Cliente DHCP aceita a primeira mensagem de Oferta de Servidor DHCP recebida, avança para o estado de Pedido e ignora quaisquer outras ofertas recebidas.

## <a name="arp-probes"></a>Sondas ARP

O Cliente DHCP pode ser configurado para enviar uma ou mais sondas ARP após a atribuição de endereços IP do Servidor DHCP para verificar se o endereço IP ainda não está a ser utilizado. O passo da sonda ARP é recomendado pelo RFC 2131 e é particularmente importante em ambientes com mais de um Servidor DHCP. Se a aplicação de anfitrião permitir a opção NX_DHCP_CLIENT_SEND_ARP_PROBE (ver **Opções de Configuração** no Capítulo Dois para opções adicionais de sonda ARP), o Cliente DHCP enviará uma sonda ARP 'auto-endereçada' e aguardará o tempo especificado para uma resposta. Se nenhum for recebido, o Cliente DHCP avança para o estado de Bound. Se uma resposta for recebida, o Cliente DHCP assume que o endereço já está em uso. Envia automaticamente uma mensagem DECLINar para o Servidor e reinicia o Cliente para reiniciar as sondas DHCP novamente a partir do estado INIT. Isto reinicia a máquina estatal DHCP e o Cliente envia outra mensagem DISCOVER para o Servidor.

## <a name="bootp-protocol"></a>Protocolo BOOTP

O Cliente DHCP também suporta o protocolo BOOTP, bem como o protocolo DHCP. Para ativar esta opção e utilizar o BOOTP em vez de DHCP, a aplicação do anfitrião deve definir a opção de configuração NX_DHCP_BOOTP_ENABLE. A aplicação de anfitrião ainda pode solicitar endereços IP específicos no protocolo BOOTP. No entanto, o Cliente DHCP não suporta o carregamento do sistema operativo anfitrião, uma vez que o BOOTP é por vezes utilizado para o fazer.

## <a name="dhcp-on-a-secondary-interface"></a>DHCP em uma interface secundária

O Cliente DHCP NetX pode funcionar em interfaces secundárias em vez da interface primária predefinido.

Para executar o Cliente NetX DHCP numa interface de rede secundária, a aplicação de anfitrião deve definir o índice de interface do Cliente DHCP para a interface secundária utilizando o serviço API *nx_dhcp_set_interface_index.* A interface já deve estar ligada à interface de rede primária utilizando o serviço *nx_ip_interface_attach.* Consulte o Guia do Utilizador NetX para obter mais detalhes sobre a fixação de interfaces secundárias.

Abaixo na Figura 1.2 encontra-se um sistema de exemplo no qual a aplicação do anfitrião se conecta ao servidor DHCP na sua interface secundária. Na linha 65, a interface secundária é anexada à tarefa IP com um endereço IP nulo. Na linha 104, após a criação da instância do Cliente DHCP, o índice de interface do cliente DHCP é definido para 1 (por exemplo, a compensação da interface primária que por si só é índice 0) chamando *nx_dhcp_set_interface_index*. Então o Cliente DHCP está pronto para ser iniciado na linha 108.

```C
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nx_dhcp.h"

#define   DEMO_STACK_SIZE     4096
TX_THREAD        my_thread;
NX_PACKET_POOL     my_pool;
NX_IP          my_ip;
NX_DHCP         my_dhcp;

/* Define function prototypes. */

void  my_thread_entry(ULONG thread_input);
void  my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
{

  /* Enter the ThreadX kernel. */
  tx_kernel_enter();
}


/* Define what the initial system looks like. */

void  tx_application_define(void *first_unused_memory)
{

CHAR  *pointer;
UINT  status;

  
  /* Setup the working pointer. */
  pointer = (CHAR *) first_unused_memory;

  /* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0, 
            pointer, DEMO_STACK_SIZE, 
            2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Initialize the NetX system. */
  nx_system_initialize();

  /* Create a packet pool. */
  status = nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                     1024, pointer, 64000);
  pointer = pointer + 64000;

  /* Check for pool creation error. */
  if (status)
    error_counter++;

  /* Create an IP instance without an IP address. */
  status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
       0xFFFFFF00, &my_pool, my_netx_driver, pointer, STACK_SIZE, 1);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Check for IP create errors. */
  if (status)
    error_counter++;

  status = _nx_ip_interface_attach(&ip_0, "port_2", IP_ADDRESS(0, 0, 0,0), 
                            0xFFFFFF00UL, my_netx_driver);
                            
  /* Enable ARP and supply ARP cache memory for my IP Instance. */
  status = nx_arp_enable(&my_ip, (void *) pointer, 1024);
  pointer = pointer + 1024;

  /* Check for ARP enable errors. */
  if (status)
    error_counter++;

  /* Enable UDP. */
  status = nx_udp_enable(&my_ip);
  if (status)
    error_counter++;
}


void  my_thread_entry(ULONG thread_input)
{

UINT    status;
ULONG    status;
NX_PACKET  *my_packet;

  /* Wait for the link to come up. */
  do
  {

    /* Get the link status. */
    status = nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,& status,100);
  } while (status != NX_SUCCESS);

  /* Create a DHCP instance. */
  status = nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

  /* Check for DHCP create error. */
  if (status)
    error_counter++;

  /* Set the DHCP client interface to the secondary interface. 
    status = nx_dhcp_set_interface_index(&my_dhcp, 1);


  /* Start DHCP. */
  nx_dhcp_start(&my_dhcp);

  /* Check for DHCP start error. */
  if (status)
    error_counter++;

  /* Wait for IP address to be resolved through DHCP. */
  nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                        (ULONG *) &status, 100000);

  /* Check to see if we have a valid IP address. */
  if (status)
  {
    error_counter++;
    return;
  }
  else
  {

        /* Yes, a valid IP address is now on lease… All NetX
      services are available.
  }
}
```

Figura 1.2 Exemplo de DHCP para NetX com suporte multihome

## <a name="dhcp-client-on-multiple-interfaces-simultaneously"></a>Cliente DHCP em múltiplas interfaces simultaneamente

Para executar o Cliente DHCP em várias interfaces, NX_MAX_PHYSICAL_INTERFACES em *nx_api.h* devem ser definidos para o número de interfaces físicas ligadas ao dispositivo. Por predefinição, este valor é 1 (por exemplo, a interface primária). Para registar uma interface adicional para a instância IP, utilize o serviço *nx_ip_interface_attach.* Consulte o Guia do Utilizador NetX para obter mais detalhes sobre a fixação de interfaces secundárias.

O próximo passo é definir o NX_DHCP_CLIENT_MAX_RECORDS em *nx_dhcp.h* para o número máximo de interfaces que se espera que sejam executadas em simultâneo. Note que NX_DHCP_CLIENT_MAX_RECORDS não tem que ser igual a NX_MAX_PHYSICAL_INTERFACES. Por exemplo, NX_MAX_PHYSICAL_INTERFACES pode ser 3 e NX_DHCP_CLIENT_MAX_RECORDS igual a 2. Nesta configuração, apenas duas interfaces (e podem ser qualquer uma das três interfaces físicas a qualquer momento) das três interfaces físicas podem executar DHCP a qualquer momento. A DHCP Client Records não tem um mapeamento de um a um para interfaces de rede, por exemplo, o Registo do Cliente 1 não se correlaciona automaticamente com o índice de interface física 1.

NX_DHCP_CLIENT_MAX_RECORDS também podem ser definidos para maiores do que NX_MAX_PHYSICAL_INTERFACES mas isso criaria registos de clientes não utilizados e seria um uso ineficiente da memória.

Antes de iniciar o DHCP em qualquer interface, a aplicação deve permitir essas interfaces chamando *nx_dhcp_interface_enable*. Note que a exceção é a interface primária que é automaticamente ativada na chamada *nx_dhcp_create* (e que pode ser desativada usando o serviço *nx_dhcp_interface_disable* discutido abaixo).

A qualquer momento, uma interface pode ser desativada para DHCP ou DHCP pode ser interrompida nessa interface independentemente de outras interfaces que executam o DHCP.

Como mencionado acima, para permitir uma interface específica para DHCP, use o serviço *nx_dhcp_interface_enable* e especifique o índice de interface física no argumento de entrada. Até NX_DHCP_CLIENT_MAX_RECORDS interfaces podem ser ativadas com a única limitação de que o argumento de entrada do índice de interface seja inferior a NX_MAX_PHYSICAL_INTERFACES.

Para iniciar o DHCP numa interface específica, utilize o serviço *nx_dhcp_interface_start.* Para iniciar o DHCP em todas as interfaces ativadas, utilize o serviço *nx_dhcp_start.* (As interfaces que já iniciaram o DHCP não serão afetadas pela *nx_dhcp_start*.)

Para parar o DHCP numa interface, utilize o serviço *nx_dhcp_interface_stop.* O DHCP já deve ter começado nessa interface ou é devolvido um estado de erro. Para parar o DHCP em todas as interfaces ativadas, utilize o serviço *nx_dhcp_stop.* O DHCP pode ser parado independentemente de outras interfaces a qualquer momento.

A maioria dos serviços existentes do DhCP Client têm um equivalente de interface, por *exemplo, nx_dhcp_interface_release* é o equivalente específico da interface de *nx_dhcp_release.* Se o Cliente DHCP estiver configurado para uma única interface, realizam a mesma ação.

Note que os serviços específicos do DHCP normalmente se aplicam a todas as interfaces, mas não a todas. Neste último caso, o serviço específico de não interface aplica-se à primeira interface ativada pelo DHCP encontrada na pesquisa da lista de registos de interface do Cliente DHCP. Consulte **a Descrição dos Serviços** no Capítulo Três para saber como um serviço específico não-interface funciona quando várias interfaces estão ativadas para DHCP.

Na sequência de exemplo abaixo, a instância IP tem duas interfaces de rede e executa primeiro o DHCP na interface secundária. Em algum momento depois, começa o DHCP na interface primária. Em seguida, lança o endereço IP na interface primária e reinicia o DHCP na interface primária:

```C
nx_dhcp_create(&my_dhcp_client);
/* By default this enables primary interface for DHCP. */

nx_dhcp_interface_enable(&my_dhcp_client, 1); 
/* Secondary interface is enabled. */

nx_dhcp_interface_start(&my_dhcp_client, 1); 
/* DHCP is started on secondary interface. */

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); 
/* DHCP is started on primary interface. */

nx_dhcp_interface_release(&my_dhcp_client, 0); 

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); 
/* DHCP is restarted on primary interface. */
```

Para obter uma lista completa de serviços específicos da interface consulte **descrição dos serviços** no capítulo três.

## <a name="configuration-options"></a>Opções de configuração

As opções DHCP configuráveis do utilizador em *nx_dhcp.h* permitem que a aplicação do anfitrião afina o Cliente DHCP para os seus requisitos específicos. Segue-se uma lista destes parâmetros:  
  
- **NX_DHCP_ENABLE_BOOTP** Definida, esta opção permite o protocolo BOOTP em vez de DHCP. Por predefinição, esta opção é desativada.

- **NX_DHCP_CLIENT_RESTORE_STATE** Se definido, isto permite ao Cliente DHCP guardar a sua licença de cliente DHCP atual 'estado' incluindo o tempo restante no arrendamento, e restaurar este estado entre reinicializações de aplicação do Cliente DHCP. O valor predefinido é desativado.

- **NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL** Se estiver definido, o Cliente DHCP não criará a sua própria piscina de pacotes. A aplicação de anfitrião deve utilizar o serviço nx_dhcp_packet_pool_set para definir o conjunto de pacotes do Cliente DHCP. O valor predefinido é desativado.

- **NX_DHCP_CLIENT_SEND_ARP_PROBE** Definido, isto permite ao Cliente DHCP enviar uma sonda ARP após a atribuição de endereço IP para verificar se o endereço DHCP atribuído não é propriedade de outro anfitrião. Por predefinição, esta opção é desativada.

- **NX_DHCP_ARP_PROBE_WAIT** Define o tempo que o Cliente DHCP espera por uma resposta após o envio de uma sonda ARP. O valor predefinido é de um segundo (1 * NX_IP_PERIODIC_RATE)

- **NX_DHCP_ARP_PROBE_MIN** Define a variação mínima no intervalo entre o envio de sondas ARP. O valor é de incumprimento para 1 segundo.

- **NX_DHCP_ARP_PROBE_MAX** Define a variação máxima no intervalo entre o envio de sondas ARP. O valor está em incumprimento de 2 segundos.

- **NX_DHCP_ARP_PROBE_NUM** Define o número de sondas ARP enviadas para determinar se o endereço IP atribuído pelo servidor DHCP já está em uso. O valor é desafinado em 3 sondas.

- **NX_DHCP_RESTART_WAIT** Define o tempo que o Cliente DHCP espera para reiniciar o DHCP se o endereço IP atribuído ao Cliente DHCP já estiver em uso. O valor está em incumprimento de 10 segundos.

- **NX_DHCP_CLIENT_MAX_RECORDS** Especifica o número máximo de registos de interface para guardar para a instância do Cliente DHCP. Um registo de interface do Cliente DHCP é um registo do Cliente DHCP em execução numa interface específica. O valor predefinido é definido à medida que as interfaces físicas contam(NX_MAX_PHYSICAL_INTERFACES).

- **NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION** Definido, isto permite ao Cliente DHCP enviar a opção máxima de tamanho de mensagem DHCP. Por predefinição, esta opção é desativada.

- **NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK** Definido, isto permite ao Cliente DHCP verificar o nome do anfitrião de entrada no nx_dhcp_create chamada para caracteres ou comprimento inválidos. Por predefinição, esta opção é desativada.

- **NX_DHCP_THREAD_PRIORITY** Prioridade do fio DHCP. Por predefinição, este valor especifica que o fio DHCP funciona na prioridade 3.

- **NX_DHCP_THREAD_STACK_SIZE** Tamanho da pilha de fios DHCP. Por padrão, o tamanho é 2048 bytes.

- **NX_DHCP_TIME_INTERVAL** Intervalo em segundos quando a função de expiração do temporizador do cliente DHCP executa. Esta função atualiza todos os intervalos de tempo no processo DHCP, por exemplo, se as mensagens devem ser retransmitidas ou o estado do Cliente DHCP alterado. Por padrão, este valor é de 1 segundo.

- **NX_DHCP_OPTIONS_BUFFER_SIZE** Tamanho do tampão de opções DHCP. Por padrão, este valor é 312.

- **NX_DHCP_PACKET_PAYLOAD** Especifica o tamanho dos bytes da carga útil do pacote do cliente DHCP. O valor predefinido é NX_DHCP_MINIMUM_IP_DATAGRAM + tamanho do cabeçalho físico. O tamanho do cabeçalho físico numa rede de fios é geralmente o tamanho da moldura Ethernet.

- **NX_DHCP_PACKET_POOL_SIZE** Especifica o tamanho da piscina de pacotes do Cliente DHCP. O valor predefinido é (5*NX_DHCP_PACKET_PAYLOAD) que fornecerá quatro pacotes mais espaço para a cobertura interna do pacote.

- **NX_DHCP_MIN_RETRANS_TIMEOUT** Especifica a opção de espera mínima para receber uma resposta do Servidor DHCP à mensagem do cliente antes de retransmissão da mensagem. O valor predefinido é o RFC 2131 recomendado 4 segundos.

- **NX_DHCP_MAX_RETRANS_TIMEOUT** Especifica a opção de espera máxima para receber uma resposta do Servidor DHCP à mensagem do cliente antes de retransmissão da mensagem. O valor predefinido é o RFC 2131 recomendado 64 segundos.

- **NX_DHCP_MIN_RENEW_TIMEOUT** Especifica a opção mínima de espera para receber uma mensagem do Servidor DHCP e enviar um pedido de renovação após o Cliente DHCP estar ligado a um endereço IP. O valor predefinido é de 60 segundos. No entanto, o Cliente DHCP utiliza os tempos de validade de Renovação e Rebind a partir da mensagem do servidor DHCP antes de incumprimento ao tempo limite mínimo de renovação.

- **NX_DHCP_TYPE_OF_SERVICE** Tipo de serviço necessário para os pedidos da DHCP UDP. Por predefinição, este valor é definido como NX_IP_NORMAL para indicar o serviço normal de pacotes IP.

- **NX_DHCP_FRAGMENT_OPTION** Ativar fragmentos para pedidos de UDP DHCP. Por padrão, este valor é NX_DONT_FRAGMENT para desativar a fragmentação da DHCP UDP.

- **NX_DHCP_TIME_TO_LIVE** Especifica o número de routers que este pacote pode passar antes de ser descartado. O valor predefinido é definido para 0x80.

- **NX_DHCP_QUEUE_DEPTH** Especifica o número de profundidade máxima da fila de receção. O valor predefinido é definido para 4.
