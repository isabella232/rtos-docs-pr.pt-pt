---
title: Capítulo 2 - Instalação e Utilização do Cliente Azure RTOS NetX PPPoE
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NETX PPPoE Client.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 17d910647db7b207280b3fbd9e90c468293a8e67
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826636"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pppoe-client"></a><span data-ttu-id="edfbf-103">Capítulo 2 - Instalação e Utilização do Cliente Azure RTOS NetX PPPoE</span><span class="sxs-lookup"><span data-stu-id="edfbf-103">Chapter 2 - Installation and Use of Azure RTOS NetX PPPoE Client</span></span>

<span data-ttu-id="edfbf-104">Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NETX PPPoE Client.</span><span class="sxs-lookup"><span data-stu-id="edfbf-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX PPPoE Client component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="edfbf-105">Distribuição de Produtos</span><span class="sxs-lookup"><span data-stu-id="edfbf-105">Product Distribution</span></span>

<span data-ttu-id="edfbf-106">O Cliente PPPoE da NetX está disponível em [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) .</span><span class="sxs-lookup"><span data-stu-id="edfbf-106">The PPPoE Client for NetX is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="edfbf-107">O pacote inclui os seguintes ficheiros:</span><span class="sxs-lookup"><span data-stu-id="edfbf-107">The package includes the following files:</span></span>

 - <span data-ttu-id="edfbf-108">**nx_pppoe_client.h** Ficheiro de cabeçalho para cliente PPPoE para NetX</span><span class="sxs-lookup"><span data-stu-id="edfbf-108">**nx_pppoe_client.h** Header file for PPPoE Client for NetX</span></span>
 - <span data-ttu-id="edfbf-109">**nx_pppoe_client.c** C Arquivo de origem para cliente PPPoE para NetX</span><span class="sxs-lookup"><span data-stu-id="edfbf-109">**nx_pppoe_client.c** C Source file for PPPoE Client for NetX</span></span>
 - <span data-ttu-id="edfbf-110">**nx_pppoe_client.pdf** Descrição em PDF do PpPoE Client para NetX</span><span class="sxs-lookup"><span data-stu-id="edfbf-110">**nx_pppoe_client.pdf** PDF description of PPPoE Client for NetX</span></span>
 - <span data-ttu-id="edfbf-111">**demo_netx_pppoe_client.c** Demonstração do Cliente Do NetX PPPoE</span><span class="sxs-lookup"><span data-stu-id="edfbf-111">**demo_netx_pppoe_client.c** NetX PPPoE Client demonstration</span></span>

## <a name="pppoe-client-installation"></a><span data-ttu-id="edfbf-112">Instalação do cliente PPPoe</span><span class="sxs-lookup"><span data-stu-id="edfbf-112">PPPoE Client Installation</span></span>

<span data-ttu-id="edfbf-113">Para utilizar o PpPoE Client para o NetX, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX está instalado.</span><span class="sxs-lookup"><span data-stu-id="edfbf-113">In order to use PPPoE Client for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="edfbf-114">Por exemplo, se o NetX estiver instalado no diretório *"\threadx\arm7\green"* então os ficheiros *nx_pppoe_client.h* e *nx_pppoe_client.c* devem ser copiados para este diretório.</span><span class="sxs-lookup"><span data-stu-id="edfbf-114">For example, if NetX is installed in the directory *“\threadx\arm7\green”* then the *nx_pppoe_client.h* and *nx_pppoe_client.c* files should be copied into this directory.</span></span>

## <a name="using-pppoe-client"></a><span data-ttu-id="edfbf-115">Usando o cliente PPPoe</span><span class="sxs-lookup"><span data-stu-id="edfbf-115">Using PPPoE Client</span></span>

<span data-ttu-id="edfbf-116">A utilização do Cliente PPPoE para netx é fácil.</span><span class="sxs-lookup"><span data-stu-id="edfbf-116">Using PPPoE Client for NetX is easy.</span></span> <span data-ttu-id="edfbf-117">Basicamente, o código de aplicação deve incluir *nx_pppoe_client.h* depois de incluir *tx_api.h* e *nx_api.h,* para utilizar o ThreadX e o NetX, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="edfbf-117">Basically, the application code must include *nx_pppoe_client.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="edfbf-118">Uma vez *incluído nx_pppoe_client.h,* o código de aplicação é então capaz de fazer as chamadas de cliente PPPoE especificadas mais tarde neste guia.</span><span class="sxs-lookup"><span data-stu-id="edfbf-118">Once *nx_pppoe_client.h* is included, the application code is then able to make the PPPoE Client function calls specified later in this guide.</span></span> <span data-ttu-id="edfbf-119">O pedido também deve incluir *nx_pppoe_client.c* no processo de construção.</span><span class="sxs-lookup"><span data-stu-id="edfbf-119">The application must also include *nx_pppoe_client.c* in the build process.</span></span> <span data-ttu-id="edfbf-120">Este ficheiro deve ser compilado da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação.</span><span class="sxs-lookup"><span data-stu-id="edfbf-120">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="edfbf-121">Isto é tudo o que é necessário para usar o Cliente PPPoE NetX.</span><span class="sxs-lookup"><span data-stu-id="edfbf-121">This is all that is required to use NetX PPPoE Client.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="edfbf-122">Sistema de Pequenos Exemplos</span><span class="sxs-lookup"><span data-stu-id="edfbf-122">Small Example System</span></span>

<span data-ttu-id="edfbf-123">Segue-se um exemplo que ilustra como utilizar o Cliente PPPoE do NetX na Figura 1.1.</span><span class="sxs-lookup"><span data-stu-id="edfbf-123">The following is an example that illustrates how to use NetX PPPoE Client is described in Figure 1.1.</span></span> <span data-ttu-id="edfbf-124">Neste exemplo, o Cliente PPPoE inclui ficheiro *nx_pppoe_client.h* é trazido na linha 50.</span><span class="sxs-lookup"><span data-stu-id="edfbf-124">In this example, the PPPoE Client include file *nx_pppoe_client.h* is brought in at line 50.</span></span> <span data-ttu-id="edfbf-125">Em seguida, o PPPoE Client é criado em *"thread_0_entry"* na linha 238.</span><span class="sxs-lookup"><span data-stu-id="edfbf-125">Next, PPPoE Client is created in *”thread_0_entry”* at line 238.</span></span> <span data-ttu-id="edfbf-126">Note que o Cliente PPPoE deve ser criado após a criação da instância IP.</span><span class="sxs-lookup"><span data-stu-id="edfbf-126">Note that PPPoE Client should be created after create the IP instance.</span></span> <span data-ttu-id="edfbf-127">A instância IP e a instância PPP são criadas e inicializada linha142-220.</span><span class="sxs-lookup"><span data-stu-id="edfbf-127">The IP instance and PPP instance are created and initialized line142-220.</span></span> <span data-ttu-id="edfbf-128">O bloco de controlo do cliente PPPoE *"pppoe_client"* foi definido como uma variável global na linha 75 anteriormente.</span><span class="sxs-lookup"><span data-stu-id="edfbf-128">The PPPoE Client control block *“pppoe_client”* was defined as a global variable at line 75 previously.</span></span> <span data-ttu-id="edfbf-129">As funções de envio e receção estão definidas na linha 238.</span><span class="sxs-lookup"><span data-stu-id="edfbf-129">The send and receive functions are set at line 238.</span></span>

<span data-ttu-id="edfbf-130">Em geral, o módulo PPPoE deve ser utilizado com módulo PPP.</span><span class="sxs-lookup"><span data-stu-id="edfbf-130">In general, PPPoE module should be used with PPP module.</span></span> <span data-ttu-id="edfbf-131">Neste exemplo, o Cliente PPP inclui ficheiro *nx_ppp.h* é trazido na linha 49.</span><span class="sxs-lookup"><span data-stu-id="edfbf-131">In this example, the PPP Client include file *nx_ppp.h* is brought in at line 49.</span></span> <span data-ttu-id="edfbf-132">Em seguida, O Cliente PPP é criado na linha 164.</span><span class="sxs-lookup"><span data-stu-id="edfbf-132">Next, PPP Client is created at line 164.</span></span> <span data-ttu-id="edfbf-133">A linha 172 configura a função para enviar o pacote de PPP.</span><span class="sxs-lookup"><span data-stu-id="edfbf-133">Line 172 setup the function to send PPP packet.</span></span> <span data-ttu-id="edfbf-134">A linha 179-190 configura os endereços IP e define o protocolo pap.</span><span class="sxs-lookup"><span data-stu-id="edfbf-134">Line 179-190 setup the IP addresses and define the pap protocol.</span></span> <span data-ttu-id="edfbf-135">A linha 104-129 configura o nome de utilizador e a palavra-passe para o protocolo pap.</span><span class="sxs-lookup"><span data-stu-id="edfbf-135">Line 104-129 setup the user name and password for pap protocol.</span></span>

<span data-ttu-id="edfbf-136">Após a sessão do PPPoE.</span><span class="sxs-lookup"><span data-stu-id="edfbf-136">After the PPPoE session established.</span></span> <span data-ttu-id="edfbf-137">A aplicação pode ligar *nx_pppoe_client_session_get* para obter as informações da sessão (endereço MAC do servidor e id de sessão) na linha 264.</span><span class="sxs-lookup"><span data-stu-id="edfbf-137">The application can call *nx_pppoe_client_session_get* to get the session information (server MAC address and session id) at line 264.</span></span> <span data-ttu-id="edfbf-138">PPP ou Aplicação pode ligar *nx_pppoe_client_session_packet_send* para enviar o pacote PPPoE na linha 283.</span><span class="sxs-lookup"><span data-stu-id="edfbf-138">PPP or Application can call *nx_pppoe_client_session_packet_send* to send PPPoE packet at line 283.</span></span>

<span data-ttu-id="edfbf-139">Quando a aplicação deixar de processar o tráfego de PPP, a aplicação pode chamar *nx_pppoe_client_session_terminate* para encerrar a sessão ppPoE.</span><span class="sxs-lookup"><span data-stu-id="edfbf-139">When the application no longer process PPP traffic, the application can call *nx_pppoe_client_session_terminate* to terminate the PPPoE session.</span></span>

<span data-ttu-id="edfbf-140">Note- neste exemplo, o PpPoE Client trabalha com a pilha IP normal ao mesmo tempo, e compartilha um controlador Ethernet.</span><span class="sxs-lookup"><span data-stu-id="edfbf-140">Note, in this example, PPPoE Client work with normal IP stack at the same time, and share one Ethernet driver.</span></span> <span data-ttu-id="edfbf-141">Passe o mesmo controlador Ethernet para a instância IP normal na linha 155 e ppPoE Client instância na linha 298.</span><span class="sxs-lookup"><span data-stu-id="edfbf-141">Pass the same Ethernet driver for normal IP instance at line 155 and PPPoE Client instance at line 298.</span></span>

> [!NOTE]
> <span data-ttu-id="edfbf-142">Redefina **NX_PHYSICAL_HEADER** a 24 para garantir espaço suficiente para preencher o cabeçalho físico.</span><span class="sxs-lookup"><span data-stu-id="edfbf-142">Redefine **NX_PHYSICAL_HEADER** to 24 to ensure enough space for filling in physical header.</span></span> <span data-ttu-id="edfbf-143">Cabeçalho físico:14 (Cabeçalho Ethernet) + 6 (cabeçalho PPPoE) + 2 (cabeçalho PPP) + 2 (alinhamento de quatro bytes).</span><span class="sxs-lookup"><span data-stu-id="edfbf-143">Physical header:14(Ethernet header) + 6(PPPoE header) + 2(PPP header) + 2(four-byte alignment).</span></span>

```c
  1 /**************************************************************************/
  2 /**************************************************************************/
  3 /**                                                                       */
  4 /** NetX PPPoE Client stack Component                                     */
  5 /**                                                                       */
  6 /**   This is a small demo of the high-performance NetX PPPoE Client      */
  7 /**   stack. This demo includes IP instance, PPPoE Client and PPP Client  */
  8 /**   stack. Create one IP instance includes two interfaces to support    */
  9 /**   for normal IP stack and PPPoE Client, PPPoE Client can use the      */
 10 /**   mutex of IP instance to send PPPoE message when share one Ethernet  */
 11 /**   driver. PPPoE Client work with normal IP instance at the same time. */
 12 /**                                                                       */
 13 /**   Note1: Substitute your Ethernet driver instead of                   */
 14 /**   _nx_ram_network_driver before run this demo                         */
 15 /**                                                                       */
 16 /**   Note2: Prerequisite for using PPPoE.                                */
 17 /**   Redefine NX_PHYSICAL_HEADER to 24 to ensure enough space for filling*/
 18 /**   in physical header. Physical header:14(Ethernet header)             */
 19 /**    + 6(PPPoE header) + 2(PPP header) + 2(four-byte aligment)          */
 20 /**                                                                       */
 21 /**************************************************************************/
 22 /**************************************************************************/
 23
 24
 25       /*****************************************************************/
 26       /*                          NetX Stack                           */
 27       /*****************************************************************/
 28
 29                                             /***************************/
 30                                             /*        PPP Client       */
 31                                             /***************************/
 32
 33                                             /***************************/
 34                                             /*       PPPoE Client      */
 35                                             /***************************/
 36       /***************************/         /***************************/
 37       /*    Normal Ethernet Type */         /*    PPPoE Ethernet Type  */
 38       /***************************/         /***************************/
 39       /***************************/         /***************************/
 40       /*       Interface 0       */         /*       Interface 1       */
 41       /***************************/         /***************************/
 42
 43       /*****************************************************************/
 44       /*                       Ethernet Dirver                         */
 45       /*****************************************************************/
 46
 47 #include   "tx_api.h"
 48 #include   "nx_api.h"
 49 #include   "nx_ppp.h"
 50 #include   "nx_pppoe_client.h"
 51
 52 /* Defined NX_PPP_PPPOE_ENABLE if use Express Logic's PPP, since PPP module has been modified
       to match PPPoE moduler under this definition.  */
 53 #ifdef NX_PPP_PPPOE_ENABLE
 54
 55 /* If the driver is not initialized in other module, define NX_PPPOE_CLIENT_INITIALIZE_DRIVER_ENABLE
       to initialize the driver in PPPoE module .
 56    In this demo, the driver has been initialized in IP module.  */
 57 #ifndef NX_PPPOE_CLIENT_INITIALIZE_DRIVER_ENABLE
 58
 59 /* Define the block size.  */
 60 #define     NX_PACKET_POOL_SIZE     ((1536 + sizeof(NX_PACKET)) * 30)
 61 #define     DEMO_STACK_SIZE         2048
 62 #define     PPPOE_THREAD_SIZE       2048
 63
 64 /* Define the ThreadX and NetX object control blocks...  */
 65 TX_THREAD               thread_0;
 66
 67 /* Define the packet pool and IP instance for normal IP instnace.  */
 68 NX_PACKET_POOL          pool_0;
 69 NX_IP                   ip_0;
 70
71 /* Define the PPP Client instance.  */
 72 NX_PPP                  ppp_client;
 73
 74 /* Define the PPPoE Client instance.  */
 75 NX_PPPOE_CLIENT         pppoe_client;
 76
 77 /* Define the counters.  */
 78 CHAR                    *pointer;
 79 ULONG                   error_counter;
 80
 81 /* Define thread prototypes.  */
 82 void    thread_0_entry(ULONG thread_input);
 83
 84 /***** Substitute your PPP driver entry function here *********/
 85 extern void    _nx_ppp_driver(NX_IP_DRIVER *driver_req_ptr);
 86
 87 /***** Substitute your Ethernet driver entry function here *********/
 88 extern void    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);
 89
 90 /* Define the porting layer function for Express Logic's PPP to simulate TTP's PPP.
 91    Functions to be provided by PPP for calling by the PPPoE Stack.  */
 92 void    ppp_client_packet_send(NX_PACKET *packet_ptr);
 93 void    pppoe_client_packet_receive(NX_PACKET *packet_ptr);
 94
 95 /* Define main entry point.  */
 96
 97 int main()
 98 {
 99
100     /* Enter the ThreadX kernel.  */
101     tx_kernel_enter();
102 }
103
104 UINT generate_login(CHAR *name, CHAR *password)
105 {
106
107     /* Make a name and password, called "myname" and "mypassword".  */
108     name[0] = 'm';
109     name[1] = 'y';
110     name[2] = 'n';
111     name[3] = 'a';
112     name[4] = 'm';
113     name[5] = 'e';
114     name[6] = (CHAR) 0;
115
116     password[0] = 'm';
117     password[1] = 'y';
118     password[2] = 'p';
119     password[3] = 'a';
120     password[4] = 's';
121     password[5] = 's';
122     password[6] = 'w';
123     password[7] = 'o';
124     password[8] = 'r';
125     password[9] = 'd';
126     password[10] = (CHAR) 0;
127
128     return(NX_SUCCESS);
129 }
130
131 /* Define what the initial system looks like.  */
132
133 void    tx_application_define(void *first_unused_memory)
134 {
135
136 UINT    status;
137
138     /* Setup the working pointer.  */
139     pointer =  (CHAR *) first_unused_memory;
140
141     /* Initialize the NetX system.  */
142     nx_system_initialize();
143
144     /* Create a packet pool for normal IP instance.  */
145     status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool",
146                                    (1536 + sizeof(NX_PACKET)),
147                                    pointer, NX_PACKET_POOL_SIZE);
148     pointer = pointer + NX_PACKET_POOL_SIZE;
149
150     /* Check for error.  */
151     if (status)
152         error_counter++;
153
154     /* Create an normal IP instance.  */
155     status = nx_ip_create(&ip_0, "NetX IP Instance", IP_ADDRESS(192, 168, 100, 44), 0xFFFFFF00UL,
156                           &pool_0, _nx_ram_network_driver, pointer, 2048, 1);
157     pointer = pointer + 2048;
158
159     /* Check for error.  */
160     if (status)
161         error_counter++;
162
163     /* Create the PPP instance.  */
164     status = nx_ppp_create(&ppp_client, "PPP Instance", &ip_0, pointer, 2048, 1,
165                            &pool_0, NX_NULL, NX_NULL); pointer = pointer + 2048;
166
167     /* Check for PPP create error.   */
168     if (status)
169         error_counter++;
170
171     /* Set the PPP packet send function.  */
172     status = nx_ppp_packet_send_set(&ppp_client, ppp_client_packet_send);
173
174     /* Check for PPP packet send function set error.   */
175     if (status)
176         error_counter++;
177
178     /* Define IP address. This PPP instance is effectively the client since it doesn't have
           any IP addresses. */
179     status = nx_ppp_ip_address_assign(&ppp_client, IP_ADDRESS(0, 0, 0, 0), IP_ADDRESS(0, 0, 0, 0));
180
181     /* Check for PPP IP address assign error.   */
182     if (status)
183         error_counter++;
184
185     /* Setup PAP, this PPP instance is effectively the since it generates the name and password
           for the peer..  */
186     status = nx_ppp_pap_enable(&ppp_client, generate_login, NX_NULL);
187
188     /* Check for PPP PAP enable error.  */
189     if (status)
190         error_counter++;
191
192     /* Attach an interface for PPP.  */
193     status = nx_ip_interface_attach(&ip_0, "Second Interface For PPP", IP_ADDRESS(0, 0, 0, 0), 0,
                                        nx_ppp_driver);
194
195     /* Check for error.  */
196     if (status)
197         error_counter++;
198
199     /* Enable ARP and supply ARP cache memory for Normal IP Instance.  */
200     status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
201     pointer = pointer + 1024;
202
203     /* Check for ARP enable errors.  */
204     if (status)
205         error_counter++;
206
207     /* Enable ICMP */
208     status = nx_icmp_enable(&ip_0);
209     if(status)
210         error_counter++;
211
212     /* Enable UDP traffic.  */
213     status =  nx_udp_enable(&ip_0);
214     if (status)
215         error_counter++;
216
217     /* Enable TCP traffic.  */
218     status =  nx_tcp_enable(&ip_0);
219     if (status)
220         error_counter++;
221
222     /* Create the main thread.  */
223     tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
224                      pointer, DEMO_STACK_SIZE,
225                      4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
226     pointer =  pointer + DEMO_STACK_SIZE;
227
228 }
229
230 /* Define the test threads.  */
231
232 void    thread_0_entry(ULONG thread_input)
233 {
234 UINT    status;
235 ULONG   ip_status;
236
237     /* Create the PPPoE instance.  */
238     status =  nx_pppoe_client_create(&pppoe_client, (UCHAR *)"PPPoE Client",  &ip_0,  0,
        &pool_0, pointer, PPPOE_THREAD_SIZE, 4, _nx_ram_network_driver, pppoe_client_packet_receive);
239     pointer = pointer + PPPOE_THREAD_SIZE;
240     if (status)
241     {
242         error_counter++;
243         return;
244     }
245
246     /* Establish PPPoE Client sessione.  */
247     status = nx_pppoe_client_session_connect(&pppoe_client, NX_WAIT_FOREVER);
248     if (status)
249     {
250         error_counter++;
251         return;
252     }
253
254     /* Wait for the link to come up.  */
255     status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_ADDRESS_RESOLVED,
                                              &ip_status, NX_WAIT_FOREVER);
256     if (status)
257     {
258         error_counter++;
259         return;
260     }
261
262     /* Get the PPPoE Server physical address and Session ID after establish PPPoE Session.  */
263     /*
264     status = nx_pppoe_client_session_get(&pppoe_client, &server_mac_msw,
                                             &server_mac_lsw, &session_id);
265     if (status)
266         error_counter++;
267     */
268 }
269
270 /* PPPoE Client receive function.  */
271 void    pppoe_client_packet_receive(NX_PACKET *packet_ptr)
272 {
273
274     /* Call PPP Client to receive the PPP data fame.  */
275     nx_ppp_packet_receive(&ppp_client, packet_ptr);
276 }
277
278 /* PPP Client send function.  */
279 void    ppp_client_packet_send(NX_PACKET *packet_ptr)
280 {
281
282     /* Directly Call PPPoE send function to send out the data through PPPoE module.  */
283     nx_pppoe_client_session_packet_send(&pppoe_client, packet_ptr);
284 }
285 #endif /* NX_PPPOE_CLIENT_INITIALIZE_DRIVER_ENABLE  */
286
287 #endif /* NX_PPP_PPPOE_ENABLE  */
```

<span data-ttu-id="edfbf-144">**Figura 1.1 Exemplo da utilização do cliente PPPoE com NetX**</span><span class="sxs-lookup"><span data-stu-id="edfbf-144">**Figure 1.1 Example of PPPoE Client use with NetX**</span></span>

## <a name="configuration-options"></a><span data-ttu-id="edfbf-145">Opções de configuração</span><span class="sxs-lookup"><span data-stu-id="edfbf-145">Configuration Options</span></span>

<span data-ttu-id="edfbf-146">Existem várias opções de configuração para a construção do PpPoE Client para NetX.</span><span class="sxs-lookup"><span data-stu-id="edfbf-146">There are several configuration options for building PPPoE Client for NetX.</span></span> <span data-ttu-id="edfbf-147">A seguinte lista descreve cada uma em detalhe:</span><span class="sxs-lookup"><span data-stu-id="edfbf-147">The following list describes each in detail:</span></span>

- <span data-ttu-id="edfbf-148">**NX_DISABLE_ERROR_CHECKING** Definida, esta opção remove a verificação básica de erro do Cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="edfbf-148">**NX_DISABLE_ERROR_CHECKING** Defined, this option removes the basic PPPoE Client error checking.</span></span> <span data-ttu-id="edfbf-149">É normalmente usado após a depurada aplicação.</span><span class="sxs-lookup"><span data-stu-id="edfbf-149">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="edfbf-150">**NX_PPPOE_CLIENT_INITIALIZE_DRIVER_ENABLE** Se definido, permite que a funcionalidade inicialize o controlador Ethernet no módulo PPPoE.</span><span class="sxs-lookup"><span data-stu-id="edfbf-150">**NX_PPPOE_CLIENT_INITIALIZE_DRIVER_ENABLE** If defined, enables the feature to initialize the Ethernet driver in PPPoE module.</span></span> <span data-ttu-id="edfbf-151">Desativa por defeito.</span><span class="sxs-lookup"><span data-stu-id="edfbf-151">It disables by default.</span></span>
- <span data-ttu-id="edfbf-152">**NX_PPPOE_CLIENT_THREAD_TIME_SLICE** Opção de corte de tempo para o fio ppPoe Cliente.</span><span class="sxs-lookup"><span data-stu-id="edfbf-152">**NX_PPPOE_CLIENT_THREAD_TIME_SLICE** Time-slice option for PPPoE Client thread.</span></span> <span data-ttu-id="edfbf-153">Por padrão, este valor é TX_NO_TIME_SLICE.</span><span class="sxs-lookup"><span data-stu-id="edfbf-153">By default, this value is TX_NO_TIME_SLICE.</span></span>
- <span data-ttu-id="edfbf-154">**NX_PPPOE_CLIENT_PADI_INIT_TIMEOUT** Isto define a poção de espera para os pacotes PADI de retransmissão inicial.</span><span class="sxs-lookup"><span data-stu-id="edfbf-154">**NX_PPPOE_CLIENT_PADI_INIT_TIMEOUT** This defines the wait potion for initial retransmitting PADI packets.</span></span> <span data-ttu-id="edfbf-155">Por padrão, este valor é de 1 segundo.</span><span class="sxs-lookup"><span data-stu-id="edfbf-155">By default, this value is 1 second.</span></span>
- <span data-ttu-id="edfbf-156">**NX_PPPOE_CLIENT_PADI_COUNT** Isto define quantos padi transmitem aposentados são permitidos antes da ligação ser considerada quebrada.</span><span class="sxs-lookup"><span data-stu-id="edfbf-156">**NX_PPPOE_CLIENT_PADI_COUNT** This defines how many PADI transmit retires are allowed before the connection is deemed broken.</span></span> <span data-ttu-id="edfbf-157">Por predefinição, este valor é 4.</span><span class="sxs-lookup"><span data-stu-id="edfbf-157">By default, this value is 4.</span></span>
- <span data-ttu-id="edfbf-158">**NX_PPPOE_CLIENT_PADR_INIT_TIMEOUT** Isto define a poção de espera para os pacotes padr de retransmissão inicial.</span><span class="sxs-lookup"><span data-stu-id="edfbf-158">**NX_PPPOE_CLIENT_PADR_INIT_TIMEOUT** This defines the wait potion for initial retransmitting PADR packets.</span></span> <span data-ttu-id="edfbf-159">Por padrão, este valor é de 1 segundo.</span><span class="sxs-lookup"><span data-stu-id="edfbf-159">By default, this value is 1 second.</span></span>
- <span data-ttu-id="edfbf-160">**NX_PPPOE_CLIENT_PADR_COUNT** Isto define quantos aposentados de transmissão PADR são permitidos antes da ligação ser considerada quebrada.</span><span class="sxs-lookup"><span data-stu-id="edfbf-160">**NX_PPPOE_CLIENT_PADR_COUNT** This defines how many PADR transmit retires are allowed before the connection is deemed broken.</span></span> <span data-ttu-id="edfbf-161">Por predefinição, este valor é 4.</span><span class="sxs-lookup"><span data-stu-id="edfbf-161">By default, this value is 4.</span></span>
- <span data-ttu-id="edfbf-162">**NX_PPPOE_CLIENT_MAX_AC_NAME_SIZE** Isto define o tamanho máximo do nome AC.</span><span class="sxs-lookup"><span data-stu-id="edfbf-162">**NX_PPPOE_CLIENT_MAX_AC_NAME_SIZE** This defines the max size of AC-Name.</span></span> <span data-ttu-id="edfbf-163">Por padrão, este valor é de 32.</span><span class="sxs-lookup"><span data-stu-id="edfbf-163">By default, this value is 32.</span></span>
- <span data-ttu-id="edfbf-164">**NX_PPPOE_CLIENT_MAX_AC_COOKIE_SIZE** Isto define o tamanho máximo de AC-Cookie.</span><span class="sxs-lookup"><span data-stu-id="edfbf-164">**NX_PPPOE_CLIENT_MAX_AC_COOKIE_SIZE** This defines the max size of AC-Cookie.</span></span> <span data-ttu-id="edfbf-165">Por padrão, este valor é de 32.</span><span class="sxs-lookup"><span data-stu-id="edfbf-165">By default, this value is 32.</span></span>
- <span data-ttu-id="edfbf-166">**NX_PPPOE_CLIENT_MAX_RELAY_SESSION_ID_SIZE** Isto define o tamanho máximo de Relay-Session-Id. Por padrão, este valor é 12.</span><span class="sxs-lookup"><span data-stu-id="edfbf-166">**NX_PPPOE_CLIENT_MAX_RELAY_SESSION_ID_SIZE** This defines the max size of Relay-Session-Id. By default, this value is 12.</span></span>
- <span data-ttu-id="edfbf-167">**NX_PPPOE_CLIENT_MIN_PACKET_PAYLOAD_SIZE** Especifica o tamanho mínimo de carga útil do pacote para o Cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="edfbf-167">**NX_PPPOE_CLIENT_MIN_PACKET_PAYLOAD_SIZE** Specifies the Minimum packet payload size for PPPoE Client.</span></span> <span data-ttu-id="edfbf-168">Se o tamanho da carga útil do pacote for maior do que este valor, pode evitar o pacote acorrentado.</span><span class="sxs-lookup"><span data-stu-id="edfbf-168">If the packet payload size is greater than this value, can avoid packet chained.</span></span> <span data-ttu-id="edfbf-169">Por predefinição, este valor é de 1520 (Tamanho máximo de carga útil do Ethernet 1500, Cabeçalho Ethernet 14, CRC 2 e alinhamento de quatro bytes 4).</span><span class="sxs-lookup"><span data-stu-id="edfbf-169">By default, this value is 1520 (Maximum Payload Size of Ethernet 1500, Ethernet Header 14, CRC 2 and Four-byte alignment 4).</span></span>
