---
title: Capítulo 2 - Instalação e Utilização do Azure RTOS NetX BSD
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente BSD Azure RTOS NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c04175ec18dff160faf853d675c9c85c9a0c6fbc5e834c410a7cb97a739c69f8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796706"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-bsd"></a>Capítulo 2 - Instalação e Utilização do Azure RTOS NetX BSD

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente BSD Azure RTOS NetX.

## <a name="product-distribution"></a>Distribuição de Produtos

O Azure RTOS NetX BSD pode ser obtido a partir do nosso repositório de código fonte pública em [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) . O pacote inclui dois ficheiros de origem e um ficheiro PDF que contém este documento, da seguinte forma:

- **nx_bsd.h:** Ficheiro de cabeçalho para NetX BSD
- **nx_bsd.c**: Ficheiro C Fonte para NetX BSD
- **nx_bsd.pdf**: Guia do Utilizador para NetX BSD

Ficheiros de demonstração:
- **bsd_demo_tcp.c**
- **bsd_demo_udp.c**

## <a name="netx-bsd-installation"></a>Instalação NetX BSD

Para utilizar o NetX BSD, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX está instalado. Por exemplo, se o NetX for instalado no diretório "*\threadx\arm7\green*", então os ficheiros *nx_bsd.h* e *nx_bsd.c* devem ser copiados para este diretório.

## <a name="building-the-threadx-and-netx-components-of-a-bsd-application"></a>Construção dos componentes ThreadX e NetX de uma aplicação BSD

### <a name="threadx"></a>ThreadX

A biblioteca ThreadX deve definir *bsd_errno* no armazenamento local do fio. Recomendamos o seguinte procedimento:

1. Em *tx_port.h,* definir uma das macros TX_THREAD_EXTENSION da seguinte forma:

  ```c
  #define TX_THREAD_EXTENSION_3     int bsd_errno
  ```

2. Reconstruir a biblioteca ThreadX.

> [!NOTE]
> Se TX_THREAD_EXTENSION_3 já estiver utilizado, o utilizador é livre de utilizar uma das outras macros TX_THREAD_EXTENSION.

### <a name="netx"></a>NetX

Antes de utilizar os Serviços BSD NetX, a biblioteca NetX deve ser construída com NX_ENABLE_EXTENDED_NOTIFY_SUPPORT definida (por exemplo, em *nx_user.h*). Por defeito não está definido.

## <a name="using-netx-bsd"></a>Utilização do NetX BSD

A utilização de BSD para NetX é fácil. Basicamente, o código de aplicação deve incluir *nx_bsd.h* depois de incluir *tx_api.h* e *nx_api.h,* para utilizar o ThreadX e o NetX, respectivamente. Uma vez *incluído nx_bsd.h,* o código de aplicação pode então utilizar os serviços BSD especificados mais tarde neste guia. O pedido também deve incluir *nx_bsd.c* no processo de construção. Este ficheiro deve ser compilado da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação. Isto é tudo o que é necessário para usar o NetX BSD.

Para utilizar os serviços NetX BSD, a aplicação deve criar uma instância IP, um pool de pacotes e inicializar os serviços BSD chamando *bsd_initialize.* Isto é demonstrado na secção "Pequeno Exemplo" mais tarde neste guia. O protótipo é mostrado abaixo:

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                  CHAR *free_memory_ptr, ULONG bsd_thread_stack_size,
                  UINT bsd_thread_priority);
```

Os últimos três parâmetros são usados para criar um fio para executar tarefas periódicas, tais como verificar eventos de TCP e definir o espaço da pilha de fios.

> [!NOTE]
> Em contraste com as tomadas BSD, que funcionam em ordem de bye de rede, a NetX trabalha na ordem byte do anfitrião do processador anfitrião. Por razões de compatibilidade de origem, os macros htons(), ntohs(), htonl(), ntohl () foram definidos, mas não modificam o argumento aprovado.

## <a name="netx-bsd-limitations"></a>Limitações BSD NetX

Devido a problemas de desempenho e arquitetura, o NetX BSD não suporta todas as características da tomada BSD 4.3:

As bandeiras do INT não são suportadas para *envio, recv, envio* e *recv de* chamadas.

## <a name="netx-bsd-with-dns-support"></a>NetX BSD com Suporte DNS

Se NX_BSD_ENABLE_DNS estiver definido, o NetX BSD pode enviar consultas dns para obter o nome de anfitrião ou informações IP do anfitrião. Esta funcionalidade requer que um Cliente DSNS NetX seja previamente criado utilizando o serviço *nx_dns_create.* Um ou mais endereços IP do servidor DNS conhecidos devem ser registados na instância DNS utilizando o *nx_dns_server_add* para adicionar endereços de servidor.

Os serviços DNS e a atribuição de memória são utilizados pelos serviços *getaddrinfo* e *getnameinfo:*

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
              const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
              char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

Quando a aplicação BSD ligar para *o getaddrinfo* com um nome de anfitrião, o NetX BSD ligará para qualquer um dos serviços abaixo para obter o endereço IP:

- nx_dns_ipv4_address_by_name_get
- nx_dns_cname_get

Para *nx_dns_ipv4_address_by_name_get,* o NetX BSD utiliza as áreas de memória ipv4_addr_buffer. O tamanho destes tampão é definido por ( `NX_BSD_IPV4_ADDR_PER_HOST * 4` ).

Para obter informações de endereços do *getaddrinfo,* o NetX BSD utiliza a tabela de memórias do bloco ThreadX *nx_bsd_addrinfo_pool_memory,* cuja área de memória é definida por outro conjunto de opções configuráveis, *NX_BSD_IPV4_ADDR_MAX_NUM*.

Consulte **opções de configuração** para obter mais detalhes sobre as opções de configuração acima.

Além disso, se NX_DNS_ENABLE_EXTENDED_RR_TYPES for definida, e a entrada do anfitrião for um nome canónico, o NetX BSD irá alocar a memória dinamicamente a partir de um conjunto de blocos previamente criado *_nx_bsd_cname_block_pool*

> [!NOTE]
> Depois de chamar *getaddrinfo,* a aplicação BSD é responsável por libertar a memória apontada pelo argumento res de volta à mesa de blocos usando o serviço *freeaddrinfo.*

## <a name="configuration-options"></a>Opções de configuração

As opções configuráveis do utilizador em *nx_bsd.h* permitem que a aplicação afina as tomadas BSD NetX para os seus requisitos específicos. Segue-se uma lista destes parâmetros:

- **NX_BSD_TCP_WINDOW**: Utilizado na tomada TCP cria chamadas. 65535 é um tamanho de janela típico para 100Mb Ethernet. O valor predefinido é 65535.
- **NX_BSD_SOCKFD_START** Este é o índice lógico para o valor de partida do ficheiro de tomada BSD. Por padrão, esta opção é 32.
- **NX_BSD_MAX_SOCKETS** Especifica o número máximo de tomadas totais disponíveis na camada BSD e deve ser um múltiplo de 32.O valor está em incumprimento a 32.
- **NX_BSD_SOCKET_QUEUE_MAX** Especifica o número máximo de pacotes UDP armazenados na fila da tomada de receção. O valor está em incumprimento a 5.
- **NX_BSD_MAX_LISTEN_BACKLOG** Isto especifica o tamanho da fila de escuta ('backlog') para as tomadas BSD TCP. O valor predefinido é 5.
- **NX_MICROSECOND_PER_CPU_TICK** Especifica o número de microsegundos por interrupção do temporizador
- **NX_BSD_TIMEOUT** Especifica o tempo limite nos tiques temporais nas chamadas internas netX exigidas pela BSD. O valor predefinido é de 20*NX_IP_PERIODIC_RATE.
- **NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: Especifica o tempo limite nos tiques de tempo na chamada de desconexão NetX. O valor predefinido é 1.
- **NX_BSD_PRINT_ERRORS** Se for definido, a devolução do estado de erro de uma função BSD devolve um número de linha e um tipo de erro, por exemplo, NX_SOC_ERROR onde ocorre o erro. Isto requer que o desenvolvedor de aplicações defina a saída de depurar. A definição predefinida é desativada e nenhuma saída de depuração é especificada em *nx_bsd.h*
- **NX_BSD_TIMER_RATE** Intervalo após o qual a tarefa do temporizador periódico BSD é executado. O valor predefinido é de 1 segundo (1 * NX_IP_PERIODIC_RATE).
- **NX_BSD_TIMEOUT_PROCESS_IN_TIMER** Se for definida, esta opção permite que o processo de tempo limite de BSD seja executado no contexto do temporizador do sistema. O comportamento predefinido é desativado. Esta característica é descrita mais detalhadamente no capítulo 2 "Instalação e Utilização do NetX BSD".
- **NX_BSD_ENABLE_DNS** Se estiver ativado, o NetX BSD enviará uma consulta DNS para um nome de anfitrião ou endereço IP anfitrião. Requer que uma instância do Cliente DNS seja previamente criada e iniciada. Por predefinição, não está ativado.
- **NX_BSD_IPV4_ADDR_MAX_NUM** Número máximo de endereços IPv4 devolvidos por *getaddrinfo*. Isto juntamente com NX_BSD_IPV4_ADDR_MAX_NUM define o tamanho do conjunto de blocos BSD NetX nx_bsd_addrinfo_block_pool para alocar a memória dinamicamente para endereçar o armazenamento de informação em *getaddrinfo*. O valor predefinido é 5.
- **NX_BSD_IPV4_ADDR_PER_HOST**: Define os endereços IPv4 máximos armazenados por consulta DNS. O valor predefinido é 5.

## <a name="bsd-socket-options"></a>Opções de tomada BSD

A seguinte lista de opções de tomada bSD NetX pode ser ativada (ou desativada) no tempo de execução numa base por tomada utilizando o serviço *setsockopt:*

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, const
                void *option_value, INT option_length);
```

Existem duas configurações diferentes para *option_level*.

O primeiro tipo de opções de tomada de tempo de funcionamento é SOL_SOCKET para opções de nível de tomada. Para ativar uma opção de nível de tomada, ligue *para option_level* definido para SOL_SOCKET e option_name definido para a opção específica, por exemplo, SO_BROADCAST. Para recuperar uma definição de opção, *ligue* para o option_name com option_level novamente definido para SOL_SOCKET.

A lista das opções de nível de tomada de tempo de funcionamento é mostrada abaixo.

- **SO_BROADCAST**: Se estiver definido, isto permite o envio e receção de pacotes de transmissão a partir de tomadas Netx. Este é o comportamento padrão para o NetX. Todas as tomadas têm esta capacidade.
- **SO_ERROR**: Utilizado para obter o estado da tomada no funcionamento anterior da tomada da tomada especificada, utilizando o serviço *getsockopt.* Todas as tomadas têm esta capacidade.
- **SO_KEEPALIVE**: Se estiver definido, isto permite a funcionalidade TCP Keep Alive. Isto requer que a biblioteca NetX seja construída com NX_TCP_ENABLE_KEEPALIVE definida em *nx_user.h*. Por predefinição, esta função está desativada.
- **SO_RCVTIMEO**: Isto define a opção de espera em segundos para receber pacotes em tomadas NetX BSD. O valor predefinido é o NX_WAIT_FOREVER (0xFFFFFFFF) ou, se não estiver ativado o não bloqueio, NX_NO_WAIT (0x0).
- **SO_RCVBUF**: Isto define o tamanho da janela da tomada TCP. O valor predefinido, NX_BSD_TCP_WINDOW, está definido para 64k para tomadas BSD TCP. Para definir o tamanho acima de 65535 requer que a biblioteca NetX seja construída com o NX_TCP_ENABLE_WINDOW_SCALING ser definida.
- **SO_REUSEADDR**: Se estiver definido, isto permite que várias tomadas sejam mapeadas para uma porta. A utilização típica é para a tomada do Servidor TCP. Este é o comportamento padrão das tomadas NetX.

O segundo tipo de opções de tomada de tempo de funcionamento é o nível de opção IP. Para ativar uma opção de nível IP, ligue *para option_level* definido para IP_PROTO e option_name definido para a opção, por exemplo, IP_MULTICAST_TTL. Para recuperar uma definição de opção, *ligue* para o option_name com option_level novamente definido para IP_PROTO.

A lista de opções de nível IP de tempo de execução é mostrada abaixo.

- **IP_MULTICAST_TTL**: Este define o tempo de viver para tomadas UDP. O valor predefinido é NX_IP_TIME_TO_LIVE (0x80) quando a tomada é criada. Este valor pode ser ultrapassado chamando *setsockopt* com esta opção de tomada.
- **IP_ADD_MEMBERSHIP**: Se estiver definido, esta opção permite que a tomada BSD (se aplica apenas às tomadas UDP) se junte ao grupo IGMP especificado.
- **IP_DROP_MEMBERSHIP**: Se estiver definido, esta opção permite que a tomada BSD (se aplica apenas às tomadas UDP) saia do grupo IGMP especificado.

## <a name="small-example-system"></a>Sistema de Pequenos Exemplos

Um exemplo de como utilizar o NetX BSD é mostrado na Figura 1.0 abaixo. Neste exemplo, o ficheiro incluído *nx_bsd.h* é trazido na linha 7. Em seguida, a instância IP *bsd_ip* e *pacotes bsd_pool* são criados como variáveis globais nas linhas 20 e 21. Note que esta demonstração utiliza um controlador de rede ram (virtual) (linha 41). O cliente e o servidor partilharão o mesmo endereço IP numa única instância IP neste exemplo.

As linhas de cliente e servidor são criadas na linha 303 e 309 em *tx_application_define* que configura a aplicação e é definida nas linhas 293-361. Após a criação bem sucedida de ip na linha 327, a instância IP está ativada para os serviços TCP na linha 350. O último requisito antes de os serviços BSD poderem ser utilizados é chamar *bsd_initialize* on line 360 para configurar todas as estruturas de dados e NetX, e recursos ThreadX necessários pela BSD.

Na função de entrada de fio do servidor, *thread_1_entry,* que é definida nas linhas 381-397, a aplicação aguarda que o controlador inicialize o NetX com parâmetros de rede. Uma vez feito isto, chama *tcpServer,* definido nas linhas 146-253, para lidar com os detalhes da configuração da tomada do servidor TCP.

*O tcpServer* cria a tomada principal ligando o serviço de *tomada* na linha 159 e liga-a à tomada de escuta utilizando a chamada *de ligação* na linha 176. Em seguida, é configurado para ouvir pedidos de ligação na linha 191. Note que a tomada principal não aceita um pedido de ligação. Funciona num ciclo contínuo que liga *selecionar* cada vez para detetar pedidos de ligação. Uma tomada BSD secundária escolhida a partir de um conjunto de tomadas BSD é atribuída o pedido de ligação depois de ligar para o serviço *de aceitação* na linha 218.

Do lado do Cliente, a função de entrada de linha do cliente, *thread_0_entry,* definida nas linhas 366-377, também deve aguardar que o NetX seja inicializado pelo condutor. Aqui esperamos que o lado do servidor o faça. Em seguida, chama *tcpClient* definido na linha 54-142, para lidar com os detalhes da configuração da tomada do cliente TCP e solicitando uma ligação TCP.

A tomada do cliente TCP é criada na linha 68. A tomada está ligada ao endereço IP especificado e tenta ligar-se ao servidor TCP ligando *a* linha 84. Está agora pronto para começar a enviar e receber pacotes.

```c
1 /*  This is a small demo of BSD Wrapper for the high-performance NetX TCP/IP stack.
2     This demo demonstrate TCP connection, disconnection, sending, and receiving using
3     ARP and a simulated Ethernet driver. */
4
5 #include     "tx_api.h"
6 #include     "nx_api.h"
7 #include     "nx_bsd.h"
8 #include     <string.h>
9 #include     <stdlib.h>
10
11 #define         DEMO_STACK_SIZE         (16*1024)
12
13
14 /* Define the ThreadX and NetX object control blocks... */
15
16 TX_THREAD       thread_0;
17 TX_THREAD       thread_1;
18
19
20 NX_PACKET_POOL  bsd_pool;
21 NX_IP           bsd_ip;
22
23
24 /* Define the counters used in the demo application... */
25
26 ULONG           error_counter;
27
28 /* Define fd_set for select call */
29 fd_set          master_list,read_ready,read_ready1;
30
31
32 /* Define thread prototypes. */
33
34 VOID            thread_0_entry(ULONG thread_input);
35 VOID            thread_1_entry(ULONG thread_input);
36
37 VOID            tcpClient(CHAR *msg0);
38 VOID            tcpServer(VOID);
39 INT             HandleClient(INT sock);
40
41 VOID            _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
42
43
44 /* Define main entry point. */
45
46 int main()
47 {
48
49     /* Enter the ThreadX kernel. */
50     tx_kernel_enter();
51 }
52
53
54 VOID tcpClient(CHAR *msg0)
55 {
56
57 INT     status,status1,send_counter;
58 INT     sock_tcp_1,length,length1;
59 struct  sockaddr_in echoServAddr;       /* Echo server address */
60 struct  sockaddr_in localAddr;          /* Local address */
61 struct  sockaddr_in remoteAddr;         /* Remote address */
62
63 UINT    echoServPort; /* Echo Server Port */
64 CHAR    rcvBuffer1[32]
65
66
67     /* Create BSD TCP Socket */
68     sock_tcp_1 = **socket**( PF_INET, SOCK_STREAM, IPPROTO_TCP);
69     if (sock_tcp_1 == -1)
70     {
71         printf("\nError: BSD TCP Client socket create \n");
72         return;
73     }
74
75     printf("\nBSD TCP Client socket created %lu \n", sock_tcp_1);
76     /* Fill destination port and IP address */
77     echoServPort = 12;
78     memset(&echoServAddr, 0, sizeof(echoServAddr));
79     echoServAddr.sin_family = PF_INET;
80     echoServAddr.sin_addr.s_addr = htonl(0x01020304);
81     echoServAddr.sin_port = echoServPort;
82
83     /* Now connect this client the server */
84     status1 = connect(sock_tcp_1, (struct sockaddr *)&echoServAddr, sizeof(echoServAddr));
85     /* Check for error. */
86     if (status1 != OK)
87     {
88         printf("\nError: BSD TCP Client socket Connect, %d \n",sock_tcp_1);
89         status = soc_close(sock_tcp_1);
90         if (status != ERROR)
91             printf("\nConnect ERROR so BSD Client Socket Closed: %d\n",sock_tcp_1);
92         else
93             printf("\nError: BSD Client Socket close %d\n",sock_tcp_1);
94         return;
95     }
96     /* Get and print source and destination information */
97     printf("\nBSD TCP Client socket: %d connected \n", sock_tcp_1);
98
99     status = getsockname(sock_tcp_1, (struct sockaddr *)&localAddr, &length);
100    printf("Client port = %lu , Client = %lu,", 
            localAddr.sin_port, localAddr.sin_addr.s_addr);
101    status = getpeername( sock_tcp_1, (struct sockaddr *) &remoteAddr, &length1);
102    printf("Remote port = %lu, Remote IP = %lu \n", 
            remoteAddr.sin_port remoteAddr.sin_addr.s_addr);
103
104    send_counter = 1;
105
106    /* Now receive the echoed packet from the server */
107    while(1)
108    {
109        tx_thread_sleep(2);
110
111        printf("\nClient sock: %d Sending packet No: %d to
                server\n",sock_tcp_1,send_counter);
112        status = send(sock_tcp_1,msg0, sizeof(msg0), 0);
113        if (status == ERROR)
114            printf("Error: BSD Client Socket send %d\n",sock_tcp_1);
115        else
116        {
117            printf("\nMessage sent: %s\n",msg0);
118            send_counter++;
119        }
120
121        status = recv(sock_tcp_1, (VOID *)rcvBuffer1, 31,0);
122        if (status == 0)
123            break;
124
125        rcvBuffer1[status] = 0;
126
127        if (status != ERROR)
128            printf("\nBSD Client Socket: %d received %lu bytes: %s ", 
                        sock_tcp_1,(ULONG)status,rcvBuffer1);
129        else
130            printf("\nError: BSD Client Socket receive %d \n",sock_tcp_1);
131
132    }
133
134    /* close this client socket */
135    status = soc_close(sock_tcp_1);
136    if (status != ERROR)
137        printf("\nBSD Client Socket Closed %d\n",sock_tcp_1);
138    else
139        printf("\nError: BSD Client Socket close %d \n",sock_tcp_1);
140
141    /* End */
142 }
143
144
145
146 void tcpServer(void)
147 {
148
149 INT         status,status1,sock,sock_tcp_2,i;
150 struct      sockaddr_in echoServAddr; /* Echo server address */
151 struct      sockaddr_in ClientAddr;
152
153 INT         Clientlen;
154 UINT        echoServPort; /* Echo Server Port */
155
156 INT         maxfd;
157
158 /* Create BSD TCP Server Socket */
159     sock_tcp_2 = socket( PF_INET, SOCK_STREAM, IPPROTO_TCP);
160     if (sock_tcp_2 == -1)
161     {
162         printf("Error: BSD TCP Server socket create\n");
163         return;
164     }
165     else
166         printf("BSD TCP Server socket created \n");
167
168     /* Now fill server side information */
169     echoServPort = 12;
170     memset(&echoServAddr, 0, sizeof(echoServAddr));
171     echoServAddr.sin_family = PF_INET;
172     echoServAddr.sin_addr.s_addr = htonl(0x01020304);
173     echoServAddr.sin_port = echoServPort;
174
175     /* Bind this server socket */
176         status = bind(sock_tcp_2, (struct sockaddr *) &echoServAddr, sizeof(echoServAddr));
177     if (status < 0)
178     {
179         printf("Error: BSD TCP Server Socket Bind \n");
180         return;
181     }
182     else
183         printf("BSD TCP Server Socket bound \n");
184
185     FD_ZERO(&master_list);
186     FD_ZERO(&read_ready);
187     FD_SET(sock_tcp_2,&master_list);
188     maxfd = sock_tcp_2;
189
190     /* Now listen for any client connections for this server socket */
191     status = listen(sock_tcp_2,5);
192     if (status < 0)
193     {
194         printf("Error: BSD TCP Server Socket Listen\n");
195         return;
196     }
197     else
198         printf("BSD TCP Server Socket Listen complete, ");
199
200     /* All set to accept client connections */
201     printf("Now accepting client connections\n");
202
203     /* Loop to create and establish server connections. */
204     while(1)
205     {
206
207         read_ready = master_list;
208         tx_thread_sleep(2); /* Allow some time to other threads too */
209         status = select(maxfd+1,&read_ready,0,0,0);
210         if (status == ERROR)
211         {
212             continue;
213         }
214
215         status = FD_ISSET(sock_tcp_2,&read_ready);
216         if(status)
217         {
218             sock = accept(sock_tcp_2,(struct sockaddr*)&ClientAddr, &Clientlen);
219
220             /* Add this new connection to our master list */
221             FD_SET(sock,&master_list);
222             if ( sock \maxfd)
223             {
224                 maxfd = sock;
225             }
226
227             continue;
228         }
229         for (i = 0; i < (maxfd+1); i++)
230         {
231             if (( i != sock_tcp_2) && (FD_ISSET(i,&master_list)) && 
                    (FD_ISSET(i,&read_ready)))
232             {
233                 status1 = HandleClient(i);
234                 if (status1 == 0)
235                 {
236                     status1 = soc_close(i);
237                     if (status1 == OK)
238                     {
239                         FD_CLR(i,&master_list);
240                         printf("\nBSD Server Socket:%d closed\n",i);
241                     }
242                     else
243                         printf("\nError:BSD Server Socket:%d close\n",i);
244                 }
245
246             }
247         }
248
249         /* Loop back to check any next client connection */
250
251     } /* While(1) ends */
252
253 }
254
255 CHAR     rcvBuffer[128];
256
257 INT     HandleClient(INT sock)
258 {
259
260 INT     status;
261
262
263     status = recv(sock, (VOID *)rcvBuffer, 128,0);
264     if (status == ERROR )
265     {
266         printf("\n BSD Server Socket:%d receive \n",sock);
267         return(ERROR);
268     }
269
270     /* a zero return from a recv() call indicates client is terminated! */
271     if (status == 0)
272     {
273         /* Done with this client , close this secondary server socket */
274         return(status);
275     }
276
277     /* print data received from the client */
278     printf("\nBSD Server Socket:%d received %lu bytes: %s \n", sock, (ULONG)status,rcvBuffer);
279
280     /* And echo the same data to the client */
281     status = send(sock,rcvBuffer, status + 1, 0);
282     if (status == ERROR )
283     {
284         printf("\nError: BSD Server Socket:%d send \n",sock);
285         return(ERROR);
286     }
287     return(status);
288 }
289
290
291 /* Define what the initial system looks like. */
292
293 void     tx_application_define(void *first_unused_memory)
294 {
295
296 CHAR     *pointer;
297 UINT     status;
298
299     /* Setup the working pointer. */
300     pointer = (CHAR *) first_unused_memory;
301
302     /* Create a client thread. */
303     tx_thread_create(&thread_0, "Client1", thread_0_entry, 0,
304         pointer, DEMO_STACK_SIZE, 2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
305
306     pointer = pointer + DEMO_STACK_SIZE;
307
308     /* Create a server thread. */
309     tx_thread_create(&thread_1, "Server", thread_1_entry, 0,
310         pointer, DEMO_STACK_SIZE,1,1, TX_NO_TIME_SLICE, TX_AUTO_START);
311
312     pointer = pointer + DEMO_STACK_SIZE;
313
314     /* Initialize the NetX system. */
315     nx_system_initialize();
316
317     /* Create a BSD packet pool. */
318     status = nx_packet_pool_create(&bsd_pool,"NetX BSD Packet Pool", 128
                                        pointer, 16384);
319     pointer = pointer + 16384;
320     if (status)
321     {
322         error_counter++;
323         printf("Error in creating BSD packet pool\n!");
324     }
325
326     /* Create an IP instance for BSD. */
327     status = nx_ip_create(&bsd_ip, "NetX IP Instance 2", IP_ADDRESS(1, 2, 3, 4),
                              0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                              pointer, 2048, 1);
328
329     pointer = pointer + 2048;
330
331     if (status)
332     {
333         error_counter++;
334         printf("Error creating BSD IP instance\n!");
335     }
336
337     /* Enable ARP and supply ARP cache memory for BSD IP Instance */
338     status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
339     pointer = pointer + 1024;
340
341     /* Check ARP enable status. */
342     if (status)
343     {
344         error_counter++;
345         printf("Error in Enable ARP and supply ARP cache memory to BSD IP instance\n");
346     }
347
348     /* Enable TCP processing for BSD IP instances. */
349
350     status = nx_tcp_enable(&bsd_ip);
351
352     /* Check TCP enable status. */
353     if (status)
354     {
355         error_counter++;
356         printf("Error in Enable TCP \n");
357     }
358
359     /* Now initialize BSD Scoket Wrapper */
360     status = bsd_initialize(&bsd_ip, &bsd_pool,pointer, 2048, 1);
361 }
362
363
364 /* Define the test threads. */
365
366 void     thread_0_entry)ULONG thread_input)
367 {
368
369 CHAR     *msg0 = "Client 1:
                     "ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<> \
                     "ABCDEFGHIJKLMNOPQRSTUVWXYZ<>END";
370
371     /* Wait till Server side is all set */
372     tx_thread_sleep(2);
373     while (1)
374     {
375         tcpClient(msg0);
376         tx_thread_sleep(1);
377     }
378 }
379
380 /* Define the server thread entry function. */
381 void     thread_1_entry(ULONG thread_input)
382 {
383
384 UINT     status;
385 ULONG    actual_status;
386
387 /* Ensure the IP instance has been initialized. */
388 status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE, &actual_status, 100);
389
390 /* Check status... */
391 if (status != NX_SUCCESS)
392 {
393     error_counter++;
394     return;
395 }
396 /* Start a TCP Server */
397 tcpServer();
398 }
399
```
