---
title: Capítulo 2 - Instalação e utilização do Azure RTOS NetX AutoIP
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NetX AutoIP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9bc5ce189980dbceaf12a2f2e8429d9267e7d37f559c88d10c54e399d01ec259
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796893"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-autoip"></a>Capítulo 2 - Instalação e utilização do Azure RTOS NetX AutoIP

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NetX AutoIP.

## <a name="product-distribution"></a>Distribuição de Produtos

O AutoIP para NetX está disponível em [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) . O pacote inclui três ficheiros de origem, um inclui ficheiros e um ficheiro PDF que contém este documento, da seguinte forma:

- **nx_auto_ip.h**: Ficheiro de cabeçalho para NetX AutoIP
- **nx_auto_ip.c**: Ficheiro C Fonte para NetX AutoIP
- **demo_netx_auto_ip.c**: Ficheiro C Fonte para demonstração de NetX AutoIP
- **nx_auto_ip.pdf**: Descrição em PDF do NetX AutoIP

## <a name="autoip-installation"></a>Instalação AutoIP

Para utilizar o NetX AutoIP, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX está instalado. Por exemplo, se o NetX for instalado no diretório "*\threadx\arm7\green*" então o *nx_auto_ip.h*, *nx_auto_ip.c*, e *demo_netx_auto_ip.c* ficheiros devem ser copiados para este diretório.

## <a name="using-autoip"></a>Utilização de AutoIP

A utilização do NetX AutoIP é fácil. Basicamente, o código de aplicação deve incluir *nx_auto_ip.h* depois de incluir *tx_api.h* e *nx_api.h,* para utilizar o ThreadX e o NetX. Uma vez incluído *nx_auto_ip.h,* o código de aplicação é então capaz de fazer as chamadas de função AutoIP especificadas mais tarde neste guia. O pedido também deve incluir *nx_auto_ip.c* no processo de construção. Estes ficheiros devem ser compilados da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação. Isto é tudo o que é necessário para usar o NetX AutoIP.

> [!NOTE]
> Uma vez que o AutoIP utiliza os serviços ARP netx, o ARP deve ser ativado com a chamada *nx_arp_enable* antes de utilizar o AutoIP.

## <a name="small-example-system"></a>Sistema de Pequenos Exemplos

Um exemplo de como é fácil utilizar o NetX AutoIP é descrito na Figura 1.1, que aparece abaixo. Neste exemplo, o AutoIP inclui ficheiro *nx_auto_ip.h* é trazido na linha 002. Em seguida, a instância NetX AutoIP é criada em "*tx_application_define*" na linha 090. Note que o bloco de controlo NetX AutoIP "auto_ip_0" foi definido anteriormente como uma variável global na linha 015. Após a criação bem sucedida, um NetX AutoIP é iniciado na linha 098. O processamento da função de retorno de alteração de endereço IP começa na linha 105, que é usada para lidar com conflitos subsequentes ou possível resolução de endereços DHCP.

> [!NOTE]
> O exemplo abaixo pressupõe que o dispositivo hospedeiro é um dispositivo de uma única casa. Para um dispositivo multihomed, a aplicação de anfitrião pode utilizar o serviço NetX AutoIP *nx_auto_ip_interface_* definido para especificar uma interface de rede secundária para sondar para um endereço IP. Consulte o Guia do **Utilizador NetX** para obter mais detalhes sobre a configuração de aplicações multihomed. Note ainda que a aplicação de anfitrião deve utilizar o *nx_status_ip_interface_check* netx API para verificar se o AutoIP obteve um endereço IP.

## <a name="example-of-autoip-use-with-netx"></a>Exemplo de utilização automática com NetX

```c
000 #include "tx_api.h"
001 #include "nx_api.h"
002 #include "nx_auto_ip.h"
003
004 #define         DEMO_STACK_SIZE         4096
005
006 /* Define the ThreadX and NetX object control blocks... */
007
008 TX_THREAD         thread_0;
009 NX_PACKET_POOL    pool_0;
010 NX_IP             ip_0;
011
012
013 /* Define the AUTO IP structures for the IP instance. */
014
015 NX_AUTO_IP         auto_ip_0;
016
017
018 /* Define the counters used in the demo application... */
019
020 ULONG             thread_0_counter;
021 ULONG             address_changes;
022 ULONG             error_counter;
023
024
025 /* Define thread prototypes. */
026
027 void     thread_0_entry(ULONG thread_input);
028 void     ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address);
029 void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
030
031
032 /* Define main entry point. */
033
034 int main()
035 {
036
037     /* Enter the ThreadX kernel. */
038     tx_kernel_enter();
039 }
040
041
042 /* Define what the initial system looks like. */
043
044 void     tx_application_define(void *first_unused_memory)
045 {
046
047 CHAR     *pointer;
048 UINT     status;
049
050
051     /* Setup the working pointer. */
052     pointer = (CHAR *) first_unused_memory;
053
054     /* Create the main thread. */
055     tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
056                     pointer, DEMO_STACK_SIZE,
057                     16, 16, 1, TX_AUTO_START);
058
059     pointer = pointer + DEMO_STACK_SIZE;
060
061     /* Initialize the NetX system. */
062     nx_system_initialize();
063
064     /* Create a packet pool. */
065     status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 128,
066                                     pointer, 4096);
067                                     pointer = pointer + 4096;
068
069     if (status)
070         error_counter++;
071
072     /* Create an IP instance. */
073     status = nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(0, 0, 0, 0),
074                             0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
075                             pointer, 4096, 1);
076                             pointer = pointer + 4096;
077
078     if (status)
079         error_counter++;
080
081     /* Enable ARP and supply ARP cache memory for IP Instance 0. */
082     status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
083     pointer = pointer + 1024;
084
085     /* Check ARP enable status. */
086     if (status)
087         error_counter++;
088
089     /* Create the AutoIP instance for IP Instance 0. */
090     status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);
091     pointer = pointer + 4096;
092
093     /* Check AutoIP create status. */
094     if (status)
095         error_counter++;
096
097     /* Start AutoIP instances. */
098     status = nx_auto_ip_start(&auto_ip_0, 0 /*IP_ADDRESS(169,254,254,255)*/);
099
100     /* Check AutoIP start status. */
101     if (status)
102         error_counter++;
103
104     /* Register an IP address change function for IP Instance 0. */
105     status = nx_ip_address_change_notify(&ip_0, ip_address_changed,
106                                         (void *) &auto_ip_0);
107
108     /* Check IP address change notify status. */
109     if (status)
110         error_counter++;
111     }
112
113
114     /* Define the test thread. */
115
116     void thread_0_entry(ULONG thread_input)
117     {
118
119     UINT      status;
120     ULONG     actual_status;
121
122
123          /* Wait for IP address to be resolved. */
124         do
125         {
126
127             /* Call IP status check routine. */
128             status = nx_ip_status_check(&ip_0, NX_IP_ADDRESS_RESOLVED,
129                                         &actual_status, 10000);
130
131         } while (status != NX_SUCCESS);
132
133         /* Since the IP address is resolved at this point, the application
134         can now fully utilize NetX! */
135
136         while(1)
137         {
138
139
140
141             /* Increment thread 0's counter. */
142             thread_0_counter++;
143
144             /* Sleep... */
145             tx_thread_sleep(10);
146         }
147     }
148
149
150     void ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address)
151     {
152
153     ULONG         ip_address;
154     ULONG         network_mask;
155     NX_AUTO_IP    *auto_ip_ptr;
156
157
158     /* Setup pointer to auto IP instance. */
159     auto_ip_ptr = (NX_AUTO_IP *) auto_ip_address;
160
161     /* Pickup the current IP address. */
162     nx_ip_address_get(ip_ptr, &ip_address, &network_mask);
163
164     /* Determine if the IP address has changed back to zero. If so,
165     make sure the AutoIP instance is started. */
166     if (ip_address == 0)
167     {
168
169         /* Get the last AutoIP address for this node. */
170         nx_auto_ip_get_address(auto_ip_ptr, &ip_address);
171
172         /* Start this AutoIP instance. */
173         nx_auto_ip_start(auto_ip_ptr, ip_address);
174     }
175
176     /* Determine if IP address has transitioned to a non local IP address. */
177     else if ((ip_address & 0xFFFF0000UL) != IP_ADDRESS(169, 254, 0, 0))
178     {
179
180         /* Stop the AutoIP processing. */
181         nx_auto_ip_stop(auto_ip_ptr);
182     }
183
184     /* Increment a counter. */
185     address_changes++;
186 }
```

## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração para a construção do NetX AutoIP. Segue-se uma lista de todas as opções, onde cada uma é descrita em detalhe:

- **NX_DISABLE_ERROR_CHECKING**: Definida, esta opção remove a verificação básica de erros autoIP. É normalmente usado após a depurada aplicação.
- **NX_AUTO_IP_PROBE_WAIT**: O número de segundos a esperar antes de enviar a primeira sonda. Por predefinição, este valor é definido como 1.
- **NX_AUTO_IP_PROBE_NUM**: O número de sondas ARP a enviar. Por predefinição, este valor é definido como 3.
- **NX_AUTO_IP_PROBE_MIN**: O número mínimo de segundos para esperar entre o envio de sondas. Por predefinição, este valor é definido como 1.
- **NX_AUTO_IP_PROBE_MAX**: O número máximo de segundos para esperar entre o envio de sondas. Por predefinição, este valor é definido como 2.
- **NX_AUTO_IP_MAX_CONFLICTS**: O número de conflitos autoip antes de aumentar os atrasos de processamento. Por predefinição, este valor é definido como 10.
- **NX_AUTO_IP_RATE_LIMIT_INTERVAL**: O número de segundos para prolongar o período de espera quando o número total de conflitos for ultrapassado. Por predefinição, este valor é definido como 60.
- **NX_AUTO_IP_ANNOUNCE_WAIT**: O número de segundos a esperar antes de enviar o anúncio. Por predefinição, este valor é definido como 2.
- **NX_AUTO_IP_ANNOUNCE_NUM**: O número de ARP anuncia enviar. Por predefinição, este valor é definido como 2.
- **NX_AUTO_IP_ANNOUNCE_INTERVAL**: O número de segundos a esperar entre o envio de anúncios. Por predefinição, este valor é definido como 2.
- **NX_AUTO_IP_DEFEND_INTERVAL:** O número de segundos a esperar entre a defesa anuncia. Por predefinição, este valor é definido como 10.