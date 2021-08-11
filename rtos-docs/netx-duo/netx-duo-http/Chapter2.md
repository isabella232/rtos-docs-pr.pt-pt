---
title: Capítulo 2 - Instalação e Utilização do Azure RTOS NetX Duo HTTP HTTP
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NetX Duo HTTP.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8739603d4a387ff3f3f42c979bd00fcebe4f08efaab42ecade462adf1fb4906a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783497"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-http"></a>Capítulo 2 - Instalação e Utilização do Azure RTOS NetX Duo HTTP HTTP

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NetX Duo HTTP.

## <a name="product-distribution"></a>Distribuição de Produtos

O Azure RTOS NetX Duo pode ser obtido a partir do nosso repositório de código fonte pública em [https://github.com/azure-rtos/netxduo/](https://github.com/azure-rtos/netxduo/) .

 - **nxd_http_client.h** Ficheiro de cabeçalho para cliente HTTP para NetX Duo
 - **nxd_http_server.h** Ficheiro de cabeçalho para SERVIDOR HTTP para NetX Duo
 - **nxd_http_client.c** C Arquivo de origem para cliente HTTP para NetX Duo
 - **nxd_http_server.c** C Ficheiro de origem para servidor HTTP para NetX Duo
 - **nx_md5.c** Algoritmos de digestão MD5
 - **filex_stub.h** Ficheiro de stub se o FileX não estiver presente
 - **nxd_http.pdf** Descrição de HTTP para NetX Duo
 - **demo_netxduo_http.c** Demonstração de NetX Duo HTTP

## <a name="http-installation"></a>Instalação HTTP

Para utilizar HTTP para o NetX Duo, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX Duo está instalado. Por exemplo, se o NetX Duo estiver instalado no diretório *"\threadx\arm7\green"* então o *nxd_http_client.h*  e *nxd_http_client.c* para aplicações do Cliente NetX Duo HTTP e *nxd_http_server.h* e *nxd_http_server.c* para aplicações do Servidor HTTP NetX Duo. *nx_md5.c* devem ser copiados para este diretório. Para a aplicação de demonstração 'ram driver' os ficheiros netx duo HTTP e servidor devem ser copiados para o mesmo diretório.

## <a name="using-http"></a>Utilizar HTTP

Utilizar HTTP para NetX Duo é fácil. Basicamente, o código de aplicação deve incluir *nxd_http_client.h* e/ou *nxd_http_server.h* depois de incluir *tx_api.h*, *fx_api.h*, e *nx_api.h*, para utilizar ThreadX, FileX e NetX Duo, respectivamente. Uma vez incluídos os ficheiros do cabeçalho HTTP, o código de aplicação pode então então fazer as chamadas de função HTTP especificadas posteriormente neste guia. O pedido deve também incluir *nxd_http_client.c*, *nxd_http_server.c* e *md5.c* no processo de construção. Estes ficheiros devem ser compilados da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação. Isto é tudo o que é necessário para usar o NetX Duo HTTP.

> [!NOTE]
> Se NX_HTTP_DIGEST_ENABLE não for especificado no processo de construção, o ficheiro .c md5 não precisa de ser adicionado ao pedido. Da mesma forma, se não forem necessárias capacidades do Cliente HTTP, o ficheiro *nxd_http_client.c* poderá ser omitido.

> [!NOTE]
> Uma vez que http utiliza os serviços NetX Duo TCP, o TCP deve ser ativado com a *chamada nx_tcp_enable* antes de utilizar HTTP.

## <a name="small-example-system"></a>Sistema de Pequenos Exemplos

Um exemplo de como é fácil utilizar o NetX Duo HTTP é descrito na Figura 1.1 que aparece abaixo. Este exemplo funciona com os serviços 'duo' disponíveis na colocação de #define USE_DUO em linha 23. Caso contrário, utiliza o legado NetX HTTP equivalente (limitado apenas ao IPv4). Os desenvolvedores são encorajados a migrar aplicações existentes para usar os serviços NetX Duo HTTP.

Para especificar a comunicação IPv6, a aplicação define IPTYPE para IPv6 na linha 24.

Neste exemplo, o HTTP inclui ficheiros *nxd_http_client.h* e *nxd_http_server.h* são trazidos nas linhas 8 e 9. Em seguida, o fio do servidor HTTP Server, o pacote de pacotes e a instância IP são criados nas linhas 89 - 112. A instância IP do servidor HTTP deve estar ativada em TCP, como visto na linha 137. O servidor HTTP é então criado na linha 159.

Em seguida, o Cliente HTTP é criado. Primeiro, o fio cliente é criado na linha 172, seguido de pacotes de pool e instância IP, semelhante ao SERVIDOR HTTP, nas linhas 186 - 200. Mais uma vez, a instância IP do cliente HTTP deve estar ativada (linha 217).

A linha HTTP Server é executado e a sua primeira tarefa é validar o seu endereço IP com o NetX Duo, o que faz nas linhas 423 - 450. Agora o servidor HTTP está pronto para receber pedidos.

A primeira tarefa do fio do cliente HTTP é criar e formatar os meios de comunicação FileX (linhas 236 e 260. Após a inicialção do suporte, o Cliente HTTP é criado na linha 271. Isto deve ser feito antes que o servidor HTTP possa servir pedidos HTTP. Em seguida, deve validar o seu endereço IP com o NetX Duo, que faz nas linhas 282 - 316. O Cliente HTTP cria e envia o ficheiro client_test.html para o Servidor HTTP, aguarda brevemente e tenta ler o ficheiro de volta a partir do Servidor HTTP.

> [!NOTE]
> A API do Cliente HTTP utiliza um serviço diferente se o IPv6 não estiver ativado *(nx_http_client_put_start* na linha 343 e *nx_http_client_get_start* na linha 399). Isto permite ao NetX Duo suportar as aplicações existentes do Cliente NetX HTTP.

> [!NOTE]
> As chamadas API do cliente HTTP são estórias com intervalos relativamente curtos. Pode ser necessário prolongar esses intervalos se um cliente HTTP estiver a comunicar com um servidor ocupado ou servidor remoto num processador mais lento.

```c
1    /* This is a small demo of the NetX Duo HTTP Client Server API running on a
2       high-performance NetX Duo TCP/IP stack. This demo is applicable for
3       either IPv4 or IPv6 enabled applications. */
4    
5    #include   "tx_api.h"
6    #include   "fx_api.h"
7    #include   "nx_api.h"
8    #include   "nxd_http_client.h"
9    #include   "nxd_http_server.h"
10   
11   #define     DEMO_STACK_SIZE         2048  
12   
13   /* Set up FileX and file memory resources. */
14   CHAR            *ram_disk_memory;
15   FX_MEDIA        ram_disk;
16   unsigned char   media_memory[512];
17      
18   /* Define device drivers. */
19   extern void _fx_ram_driver(FX_MEDIA *media_ptr);
20   VOID        _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);
22   
23   #define USE_DUO        /* Use the duo service (not legacy netx) */
24   #define IPTYPE   6       /* Send packets over IPv6 */
25
26   /* Set up the HTTP client. */
27   TX_THREAD       client_thread;
28   NX_PACKET_POOL  client_pool;
29   NX_HTTP_CLIENT  my_client;
30   NX_IP           client_ip;
31   #define         CLIENT_PACKET_SIZE  (NX_HTTP_SERVER_MIN_PACKET_SIZE * 2)
32   void            thread_client_entry(ULONG thread_input);
33   
34   #define HTTP_SERVER_ADDRESS  IP_ADDRESS(1,2,3,4)
35   #define HTTP_CLIENT_ADDRESS  IP_ADDRESS(1,2,3,5)
36   
37   /* Set up the HTTP server */
38   
39   NX_HTTP_SERVER  my_server;
40   NX_PACKET_POOL  server_pool;
41   TX_THREAD       server_thread;
42   NX_IP           server_ip;
43   #define         SERVER_PACKET_SIZE  (NX_HTTP_SERVER_MIN_PACKET_SIZE * 2)
44   
45   void            thread_server_entry(ULONG thread_input);
46   #ifdef FEATURE_NX_IPV6
47   NXD_ADDRESS     server_ip_address;
48   #endif
49   
50   
51   /* Define the application's authentication check. This is called by
52      the HTTP server whenever a new request is received. */
53   UINT  authentication_check(NX_HTTP_SERVER *server_ptr, UINT request_type,
54               CHAR *resource, CHAR **name, CHAR **password, CHAR **realm)
55   {
56   
57       /* Just use a simple name, password, and realm for all
58          requests and resources. */
59       *name =     "name";
60       *password = "password";
61       *realm =    "NetX Duo HTTP demo";
62   
63       /* Request basic authentication. */
64       return(NX_HTTP_BASIC_AUTHENTICATE);
65   }
66   
67   /* Define main entry point. */
68   
69   int main()
70   {
71   
72       /* Enter the ThreadX kernel. */
73       tx_kernel_enter();
74   }
75   
76   
77   /* Define what the initial system looks like. */
78   void    tx_application_define(void *first_unused_memory)
79   {
80   
81   CHAR    *pointer;
82   UINT    status;
83   
84       
85       /* Setup the working pointer. */
86       pointer =  (CHAR *) first_unused_memory;
87   
88       /* Create a helper thread for the server. */
89       tx_thread_create(&server_thread, "HTTP Server thread", thread_server_entry, 0,  
90                        pointer, DEMO_STACK_SIZE,
91                        1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
92   
93       pointer =  pointer + DEMO_STACK_SIZE;
94   
95       /* Initialize the NetX system. */
96       nx_system_initialize();
97   
98       /* Create the server packet pool. */
99       status =  nx_packet_pool_create(&server_pool, "HTTP Server Packet Pool",
        SERVER_PACKET_SIZE, pointer, SERVER_PACKET_SIZE*4);
100
101  
102      pointer = pointer + SERVER_PACKET_SIZE * 4;
103  
104      /* Check for pool creation error. */
105      if (status)
106      {
107  
108          return;
109      }
110  
111      /* Create an IP instance. */
112      status = nx_ip_create(&server_ip, "HTTP Server IP", HTTP_SERVER_ADDRESS,
113                            0xFFFFFF00UL, &server_pool, _nx_ram_network_driver,
114                            pointer, 4096, 1);
115  
116      pointer =  pointer + 4096;
117  
118      /* Check for IP create errors. */
119      if (status)
120      {
121          printf("nx_ip_create failed. Status 0x%x\n", status);
122          return;
123      }
124  
125      /* Enable ARP and supply ARP cache memory for the server IP instance. */
126      status = nx_arp_enable(&server_ip, (void *) pointer, 1024);
127  
128      /* Check for ARP enable errors. */
129      if (status)
130      {
131          return;
132      }
133  
134      pointer = pointer + 1024;
135  
136       /* Enable TCP traffic. */
137      status = nx_tcp_enable(&server_ip);
138  
139      if (status)
140      {
141          return;
142      }
143  
144  #if (IP_TYPE==6)
145  
146      /* Set up HTTPv6 server, but we have to wait till its address has been
147         validated before we can start the thread_server_entry thread. */
148  
149      /* Set up the server's IPv6 address here. */
150      server_ip_address.nxd_ip_address.v6[3] = 0x105;
151      server_ip_address.nxd_ip_address.v6[2] = 0x0;
152      server_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
153      server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
154      server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
155  
156  #endif
157  
158      /* Create the NetX HTTP Server. */
159      status = nx_http_server_create(&my_server, "My HTTP Server", &server_ip,
            &ram_disk, pointer, 2048, &server_pool, authentication_check,
            NX_NULL);
160
161      if (status)
162      {
163          return;
164      }
165  
166      pointer =  pointer + 2048;
167  
168      /* Save the memory pointer for the RAM disk. */
169      ram_disk_memory =  pointer;
170  
171      /* Create the HTTP client thread. */
172      status = tx_thread_create(&client_thread, "HTTP Client", thread_client_entry, 0,  
173                       pointer, DEMO_STACK_SIZE,
174                       2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
175  
176      pointer =  pointer + DEMO_STACK_SIZE;
177  
178      /* Check for thread create error. */
179      if (status)
180      {
181  
182          return;
183      }
184  
185      /* Create the Client packet pool. */
186      status =  nx_packet_pool_create(&client_pool, "HTTP Client Packet Pool",
 SERVER_PACKET_SIZE, pointer, SERVER_PACKET_SIZE*4);

187
188  
189      pointer = pointer + SERVER_PACKET_SIZE * 4;
190  
191      /* Check for pool creation error. */
192      if (status)
193      {
194  
195          return;
196      }
197  
198  
199      /* Create an IP instance. */
200      status = nx_ip_create(&client_ip, "HTTP Client IP", HTTP_CLIENT_ADDRESS,
201                            0xFFFFFF00UL, &client_pool, _nx_ram_network_driver,
202                            pointer, 2048, 1);
203  
204      pointer =  pointer + 2048;
205  
206      /* Check for IP create errors. */
207      if (status)
208      {
209          return;
210      }
211  
212      nx_arp_enable(&client_ip, (void *) pointer, 1024);
213  
214      pointer =  pointer + 2048;
215  
216       /* Enable TCP traffic. */
217      nx_tcp_enable(&client_ip);
218  
219      return;
220  }
221  
222  
223  VOID thread_client_entry(ULONG thread_input)
224  {
225  
226  UINT            status;
227  NX_PACKET       *my_packet;
228  #ifdef FEATURE_NX_IPV6
229  NXD_ADDRESS     client_ip_address;
230  UINT            address_index;
230  #endif
231  
232  
233      /* Format the RAM disk - the memory for the RAM disk was setup in
234        tx_application_define above. This must be set up before the client(s) start
235        sending requests. */
236      status = fx_media_format(&ram_disk,
237                              _fx_ram_driver,         // Driver entry
238                              ram_disk_memory,        // RAM disk memory pointer
239                              media_memory,           // Media buffer pointer
240                              sizeof(media_memory),   // Media buffer size
241                              "MY_RAM_DISK",          // Volume Name
242                              1,                      // Number of FATs
243                              32,                     // Directory Entries
244                              0,                      // Hidden sectors
245                              256,                    // Total sectors
246                              128,                    // Sector size   
247                              1,                      // Sectors per cluster
248                              1,                      // Heads
249                              1);                     // Sectors per track
250  
251      /* Check the media format status. */
252      if (status != FX_SUCCESS)
253      {
254  
255          /* Error, bail out. */
256          return ;
257      }
258  
259      /* Open the RAM disk. */
260      status =  fx_media_open(&ram_disk, "RAM DISK", _fx_ram_driver, ram_disk_memory,
                media_memory, sizeof(media_memory));
261  
262      /* Check the media open status. */
263      if (status != FX_SUCCESS)
264      {
265  
266          /* Error, bail out. */
267          return ;
268      }
269  
270      /* Create an HTTP client instance. */
271      status = nx_http_client_create(&my_client, "HTTP Client", &client_ip,
                    &client_pool, 600);
272  
273      /* Check status. */
274      if (status != NX_SUCCESS)
275      {
276          return;
277      }
278  
279      /* Attempt to upload a file to the HTTP server. */
280  
281  
282  #if (IPTYPE== 6)
283  
284      /* Relinquish control so the HTTP server can get set up...*/
285      tx_thread_relinquish();
286  
287      /* Set up the client's IPv6 address here. */
288      client_ip_address.nxd_ip_address.v6[3] = 0x101;
289      client_ip_address.nxd_ip_address.v6[2] = 0x0;
290      client_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
291      client_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
292      client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
293                 
294      /* Here's where we make the HTTP Client IPv6 enabled. */
295  
296      nxd_ipv6_enable(&client_ip);
298      nxd_icmp_enable(&client_ip);     
299      
300      /* Wait till the IP task thread has set the device MAC address. */
302      tx_thread_sleep(100);
303  
305      /* Now update NetX Duo the Client's link local and global IPv6 address. */
306      nxd_ipv6_address_set(&server_ip, 0, NX_NULL, 10, &address_index)
307      nxd_ipv6_ address_set(&server_ip, 0, &client_ip_address, 64, &address_index);
311
313      /* Then make sure NetX Duo has had time to validate the addresses. */
314      
316      tx_thread_sleep(400);
317  
321      /* Now upload an HTML file to the HTTPv6 server. */
322      status =  nxd_http_client_put_start(&my_client, &server_ip_address,
323         "/client_test.htm", "name", "password", 103, 500);
324
325
326      /* Check status. */
327      if (status != NX_SUCCESS)
328      {
329
330          return;
331      }
332      
333
334  #else
335  
336      /* Relinquish control so the HTTP server can get set up...*/
337      tx_thread_relinquish();
338  
339      do
340      {
341      
342          /* Attempt to upload to the HTTP IPv4 server. */
343          status =  nx_http_client_put_start(&my_client, HTTP_SERVER_ADDRESS,
            "/client_test.htm", "name", "password", 103, 500);
344
345  
346          /* Check status. */
347          if (status != NX_SUCCESS)
348          {
349              tx_thread_sleep(100);
350          }
351  
352      } while (status != NX_SUCCESS);
353  
354  
355  #endif  /* (IPTYPE== 6) */
356  
357  
358      /* Allocate a packet. */
359      status =  nx_packet_allocate(&client_pool, &my_packet, NX_TCP_PACKET,
                        NX_WAIT_FOREVER);
360  
361      /* Check status. */
362      if (status != NX_SUCCESS)
363      {
364          return;
365      }
366  
367      /* Build a simple 103-byte HTML page. */
368      nx_packet_data_append(my_packet, "<HTML>\r\n", 8,
369                          &client_pool, NX_WAIT_FOREVER);
370      nx_packet_data_append(my_packet,
371                   "<HEAD><TITLE>NetX HTTP Test</TITLE></HEAD>\r\n", 44,
372                          &client_pool, NX_WAIT_FOREVER);
373      nx_packet_data_append(my_packet, "<BODY>\r\n", 8,
374                          &client_pool, NX_WAIT_FOREVER);
375      nx_packet_data_append(my_packet, "<H1>Another NetX Test Page!</H1>\r\n", 25,
376                          &client_pool, NX_WAIT_FOREVER);
377      nx_packet_data_append(my_packet, "</BODY>\r\n", 9,
378                          &client_pool, NX_WAIT_FOREVER);
379      nx_packet_data_append(my_packet, "</HTML>\r\n", 9,
380                          &client_pool, NX_WAIT_FOREVER);
381  
382      /* Complete the PUT by writing the total length. */
383      status =  nx_http_client_put_packet(&my_client, my_packet, 50);
384  
385      /* Check status. */
386      if (status != NX_SUCCESS)
387      {
388          return;
389      }
390  
391      /* Now GET the test file  */
392  
393  #ifdef USE_DUO
394  
395      status =  nxd_http_client_get_start(&my_client, &server_ip_address,
396                     "/client_test.htm", NX_NULL, 0, "name", "password", 50);
397  #else
398  
399      status =  nx_http_client_get_start(&my_client, HTTP_SERVER_ADDRESS,
                 "/client_test.htm",  NX_NULL, 0, "name", "password", 50);
400
401  #endif
402  
403      /* Check status. */
404      if (status != NX_SUCCESS)
405      {
406          return;
407      }
408  
409      status = nx_http_client_delete(&my_client);
410  
411      return;
413  }
414  
416  /* Define the helper HTTP server thread. */
417  void    thread_server_entry(ULONG thread_input)
418  {
419  
420  UINT            status;
421  #if (IPTYPE == 6)
422  UINT            address_index
423  NXD_ADDRESS     ip_address
424  
425      /* Allow time for the IP task to initialize the driver. */
426      tx_thread_sleep(100);
427
428    ip_address.nxd_ip_version = NX_IP_VERSION_V6;
429    ip_address.nxd_ip_address.v6[0] = 0x20010000;
430    ip_address.nxd_ip_address.v6[1] = 0;
431    ip_address.nxd_ip_address.v6[2] = 0;
432    ip_address.nxd_ip_address.v6[3] = 4;
433  
434      /* Here's where we make the HTTP server IPv6 enabled. */
435      nxd_ipv6_enable(&server_ip);
436      nxd_icmp_enable(&server_ip);
437  
438      /* Wait till the IP task thread has set the device MAC address. */
439      while (server_ip.nx_ip_arp_physical_address_msw == 0 ||
440             server_ip.nx_ip_arp_physical_address_lsw == 0)
441      {
442          tx_thread_sleep(30);
443      }
444  
445      nxd_ipv6_address_set(&server_ip, 0, NX_NULL, 10, &address_index)
446      nxd_ipv6_ address_set(&server_ip, 0, &ip_address, 64, &address_index);
447  
448      /* Wait for NetX Duo to validate server address. */
449      tx_thread_sleep(400);
450  
451  #endif  /* (IPTYPE == 6) */
452  
453      /* OK to start the HTTPv6 Server. */
454      status = nx_http_server_start(&my_server);
455  
456      if (status != NX_SUCCESS)
457      {
458          return;
459      }
460  
461      /* HTTP server ready to take requests! */
462  
463      /* Let the IP threads execute. */
464      tx_thread_relinquish();
465  
466      return;
467  }
```

**Figura 1.1 Exemplo de utilização HTTP com o NetX Duo**

## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração para a construção HTTP para NetX Duo. Segue-se uma lista de todas as opções, onde cada uma é descrita em detalhe. Os valores predefinidos estão listados, mas podem ser redefinidos antes da inclusão de *nxd_http_client.h* e *nxd_http_server.h:*

 - **NX_DISABLE_ERROR_CHECKING** Definida, esta opção remove a verificação básica de erros HTTP. É normalmente usado após a aplicação ter sido depurada
 - **NX_HTTP_SERVER_PRIORITY** A prioridade da linha do servidor HTTP. Por predefinição, este valor é definido como 16 para especificar a prioridade 16.
 - **NX_HTTP_NO_FILEX** Definida, esta opção fornece um canhoto para dependências de FileX. O Cliente HTTP funcionará sem qualquer alteração se esta opção for definida. O Servidor HTTP terá de ser modificado ou o utilizador terá de criar um punhado de serviços FileX para funcionar corretamente.
 - **NX_HTTP_TYPE_OF_SERVICE** Tipo de serviço necessário para os pedidos HTTP TCP. Por predefinição, este valor é definido como NX_IP_NORMAL para indicar o serviço normal de pacotes IP.
  - **NX_HTTP_SERVER_THREAD_TIME_SLICE** O número de marcações de temporizador que o fio do Servidor é permitido funcionar antes de ceder a fios da mesma prioridade. O valor predefinido é 2.
 - **NX_HTTP_FRAGMENT_OPTION** Fragmento ativar pedidos HTTP TCP. Por predefinição, este valor é NX_DONT_FRAGMENT para desativar a fragmentação HTTP TCP.
 - **NX_HTTP_SERVER_WINDOW_SIZE**   Tamanho da janela da tomada do servidor. Por padrão, este valor é 2048 bytes
 - **NX_HTTP_TIME_TO_LIVE** Especifica o número de routers que este pacote pode passar antes de ser descartado. O valor predefinido é definido para 0x80.
 - **NX_HTTP_SERVER_TIMEOUT**   Especifica o número de carraças ThreadX que os serviços internos vão suspender. O valor predefinido é definido para 10 segundos (10 * NX_IP_PERIODIC_RATE).
 - **NX_HTTP_SERVER_TIMEOUT_ACCEPT** Especifica o número de carraças threadX que os serviços internos suspenderão em chamadas internas *nx_tcp_server_socket_accept.* O valor predefinido é definido para (10* NX_IP_PERIODIC_RATE).
 - **NX_HTTP_SERVER_TIMEOUT_DISCONNECT** Especifica o número de carraças threadX que os serviços internos suspenderão em chamadas internas *nx_tcp_socket_disconnect.* O valor predefinido é definido para 10 segundos (10 * NX_IP_PERIODIC_RATE).
 - **NX_HTTP_SERVER_TIMEOUT_RECEIVE** Especifica o número de carraças threadX que os serviços internos suspenderão em chamadas internas *nx_tcp_socket_receive.* O valor predefinido é definido para 10 segundos (10 * NX_IP_PERIODIC_RATE).
 - **NX_HTTP_SERVER_TIMEOUT_SEND** Especifica o número de carraças threadX que os serviços internos suspenderão em chamadas internas *nx_tcp_socket_send.* O valor predefinido é definido para 10 segundos (10 * NX_IP_PERIODIC_RATE).
 - **NX_HTTP_MAX_HEADER_FIELD** Especifica o tamanho máximo do campo de cabeçalho HTTP. O valor predefinido é de 256.
 - **NX_HTTP_MULTIPART_ENABLE** Se definido, permite que o SERVIDOR HTTP suporte pedidos HTTP multipart.
 - **NX_HTTP_SERVER_MAX_PENDING**   Especifica o número de ligações que podem ser na fila para o servidor HTTP. O valor predefinido é definido para 5.
 - **NX_HTTP_MAX_RESOURCE** Especifica o número de bytes permitidos num *nome de recurso* fornecido pelo cliente. O valor predefinido é definido para 40.
 - **NX_HTTP_MAX_NAME** Especifica o número de bytes permitidos num nome *de utilizador* fornecido pelo cliente . O valor predefinido é definido para 20.
 - **NX_HTTP_MAX_PASSWORD** Especifica o número de bytes permitidos numa *senha* fornecida pelo cliente. O valor predefinido é definido para 20.
 - **NX_HTTP_SERVER_MIN_PACKET_SIZE** Especifica o tamanho mínimo dos pacotes na piscina especificado na criação do Servidor. O tamanho mínimo é necessário para garantir que o cabeçalho HTTP completo pode ser contido num pacote. O valor predefinido é definido para 600.
 - **NX_HTTP_CLIENT_MIN_PACKET_SIZE** Especifica o tamanho mínimo dos pacotes na piscina especificado na criação do Cliente. O tamanho mínimo é necessário para garantir que o cabeçalho HTTP completo pode ser contido num pacote. O valor predefinido é definido para 300.
 - **NX_HTTP_SERVER_RETRY_SECONDS** Desajuste o tempo limite de retransmissão da tomada do servidor em segundos. O valor predefinido é definido para 2.
 - **NX_HTTP_SERVER_ RETRY_MAX** Isto define o número máximo de retransmissão na tomada do Servidor. O valor predefinido é definido para 10.
 - **NX_HTTP_SERVER_ RETRY_SHIFT** Este valor é utilizado para definir o próximo tempo limite de retransmissão. O tempo limite atual é multiplicado pelo número de retransmissão até agora, alterado pelo valor do intervalo de tempo da tomada. O valor predefinido é definido para 1 para duplicar o tempo limite.
 - **NX_HTTP_SERVER_TRANSMIT_QUEUE_DEPTH** Isto especifica o número máximo de pacotes que podem ser encadeados na fila de retransmissão da tomada do Servidor. Se o número de pacotes encadeados chegar a este número, não podem ser enviados mais pacotes até que um ou mais pacotes enqueados sejam libertados. O valor predefinido é definido para 20.
