---
title: Capítulo 2 - Instalação e utilização do agente SNMP Azure RTOS NetX Duo
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente netx duo SNMP Agent.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f011b73217c7f413dd19c555e9c2d40dace305ee
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825765"
---
# <a name="chapter-2---installation-and-use-of-the-azure-rtos-netx-duo-snmp-agent"></a><span data-ttu-id="91670-103">Capítulo 2 - Instalação e utilização do agente SNMP Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="91670-103">Chapter 2 - Installation and use of the Azure RTOS NetX Duo SNMP agent</span></span>

<span data-ttu-id="91670-104">Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente de agente SNMP Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="91670-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo SNMP agent component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="91670-105">Distribuição de Produtos</span><span class="sxs-lookup"><span data-stu-id="91670-105">Product Distribution</span></span>

<span data-ttu-id="91670-106">O Agente SNMP para o NetX Duo está disponível em [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) .</span><span class="sxs-lookup"><span data-stu-id="91670-106">SNMP Agent for NetX Duo is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="91670-107">O pacote inclui quatro ficheiros de origem, um incluindo ficheiro e um ficheiro PDF que contém este documento, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="91670-107">The package includes four source files, one include file, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="91670-108">**nxd_snmp.h** Arquivo de cabeçalho para SNMP para NetX Duo</span><span class="sxs-lookup"><span data-stu-id="91670-108">**nxd_snmp.h** Header file for SNMP for NetX Duo</span></span>
- <span data-ttu-id="91670-109">**demo_snmp_helper.h** Ficheiro de cabeçalho para dados do MIB do SNMP</span><span class="sxs-lookup"><span data-stu-id="91670-109">**demo_snmp_helper.h** Header file for SNMP MIB data</span></span>
- <span data-ttu-id="91670-110">**nxd_snmp.c** C Arquivo de origem para Agente SNMP para NetX Duo</span><span class="sxs-lookup"><span data-stu-id="91670-110">**nxd_snmp.c** C Source file for SNMP Agent for NetX Duo</span></span>
- <span data-ttu-id="91670-111">**nx_md5.c** Algoritmos de digestão MD5</span><span class="sxs-lookup"><span data-stu-id="91670-111">**nx_md5.c** MD5 digest algorithms</span></span>
- <span data-ttu-id="91670-112">**nx_sha.c** Algoritmos de digestão SHA</span><span class="sxs-lookup"><span data-stu-id="91670-112">**nx_sha.c** SHA digest algorithms</span></span>
- <span data-ttu-id="91670-113">**nx_des.c** Algoritmos de encriptação DES</span><span class="sxs-lookup"><span data-stu-id="91670-113">**nx_des.c** DES encryption algorithms</span></span>
- <span data-ttu-id="91670-114">**nxd_snmp.pdf** Guia de utilizador para agente SNMP para NetX Duo</span><span class="sxs-lookup"><span data-stu-id="91670-114">**nxd_snmp.pdf** User Guide for SNMP Agent for NetX Duo</span></span>
- <span data-ttu-id="91670-115">**demo_netxduo_snmp.c** Demonstração SNMP simples</span><span class="sxs-lookup"><span data-stu-id="91670-115">**demo_netxduo_snmp.c** Simple SNMP demonstration</span></span>
- <span data-ttu-id="91670-116">**demo_netxduo_mib2.c** Demonstração simples do MIB2 (MIB tem elementos de endereço IPv6)</span><span class="sxs-lookup"><span data-stu-id="91670-116">**demo_netxduo_mib2.c** Simple MIB2 demonstration (MIB has IPv6 address elements)</span></span>
- <span data-ttu-id="91670-117">**demo_snmp_helper.h** Ficheiro de cabeçalho que define elementos do MIB</span><span class="sxs-lookup"><span data-stu-id="91670-117">**demo_snmp_helper.h** Header file defining MIB elements</span></span>

## <a name="netx-duo-snmp-agent-installation"></a><span data-ttu-id="91670-118">Instalação do agente SNMP da NetX Duo</span><span class="sxs-lookup"><span data-stu-id="91670-118">NetX Duo SNMP Agent Installation</span></span>

<span data-ttu-id="91670-119">Para utilizar o NetX Duo SNMP, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX Duo está instalado.</span><span class="sxs-lookup"><span data-stu-id="91670-119">In order to use NetX Duo SNMP, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="91670-120">Por exemplo, se o NetX Duo for instalado no diretório "*\threadx\arm7\green*" então os *ficheiros nxd_snmp.h,* *nxd_snmp.c*, *nx_md5.c, nx_sha.c* e nx_ *des.c* os ficheiros devem ser copiados para este diretório.</span><span class="sxs-lookup"><span data-stu-id="91670-120">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nxd_snmp.h*, *nxd_snmp.c*, *nx_md5.c, nx_sha.c* and nx_ *des.c* files should be copied into this directory.</span></span>

## <a name="using-the-netx-duo-snmp-agent"></a><span data-ttu-id="91670-121">Utilizando o Agente SNMP da NetX Duo</span><span class="sxs-lookup"><span data-stu-id="91670-121">Using the NetX Duo SNMP Agent</span></span>

<span data-ttu-id="91670-122">A candidatura deve ter *nxd_snmp.c*, *nx_md5.c, nx_sha.c*- e *nx_des.c* no projeto de construção.</span><span class="sxs-lookup"><span data-stu-id="91670-122">The application must have *nxd_snmp.c*, *nx_md5.c, nx_sha.c*, and *nx_des.c* in the build project.</span></span> <span data-ttu-id="91670-123">O código de aplicação também deve incluir *nxd_snmp.h* depois de incluir *nx_api.h para* poder invocar serviços SNMP.</span><span class="sxs-lookup"><span data-stu-id="91670-123">The application code must also include *nxd_snmp.h* after it includes *nx_api.h to be* able to invoke SNMP services.</span></span> <span data-ttu-id="91670-124">Estes ficheiros devem ser compilados da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada à biblioteca NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="91670-124">These files must be compiled in the same manner as other application files and its object form must be linked to the NetX Duo library.</span></span> <span data-ttu-id="91670-125">Isto é tudo o que é necessário para usar o NetX Duo SNMP.</span><span class="sxs-lookup"><span data-stu-id="91670-125">This is all that is required to use NetX Duo SNMP.</span></span>

> [!NOTE]
> <span data-ttu-id="91670-126">*Se **NX_SNMP_NO_SECURITY** for especificado no processo de construção, os ficheiros nx_md5.c, nx_sha.c e nx_des.c não são necessários.*</span><span class="sxs-lookup"><span data-stu-id="91670-126">*If **NX_SNMP_NO_SECURITY** is specified in the build process, the nx_md5.c, nx_sha.c, and nx_des.c files are not needed.*</span></span>

> [!NOTE]
> <span data-ttu-id="91670-127">Uma vez que o NetX Duo SNMP utiliza os serviços UDP, a UDP deve ser ativada com a *chamada nx_udp_enable* antes da utilização do SNMP.</span><span class="sxs-lookup"><span data-stu-id="91670-127">That since NetX Duo SNMP utilizes UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using SNMP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="91670-128">Sistema de Pequenos Exemplos</span><span class="sxs-lookup"><span data-stu-id="91670-128">Small Example System</span></span>

<span data-ttu-id="91670-129">Um exemplo de como utilizar o Agente SNMP da NetX Duo é descrito na Figura 1.0 que aparece abaixo.</span><span class="sxs-lookup"><span data-stu-id="91670-129">An example of how to use NetX Duo SNMP Agent is described in Figure 1.0 that appears below.</span></span> <span data-ttu-id="91670-130">Neste exemplo, o SNMP inclui ficheiro *nxd_snmp.h* é trazido na linha 6.</span><span class="sxs-lookup"><span data-stu-id="91670-130">In this example, the SNMP include file *nxd_snmp.h* is brought in at line 6.</span></span> <span data-ttu-id="91670-131">O ficheiro de cabeçalho que define os elementos da base de dados do MIB, *demo_snmp_helper.h,* é trazido na linha 8.</span><span class="sxs-lookup"><span data-stu-id="91670-131">The header file that defines the MIB database elements, *demo_snmp_helper.h,* is brought in at line 8.</span></span> <span data-ttu-id="91670-132">O MIB é definido a partir da linha 32.</span><span class="sxs-lookup"><span data-stu-id="91670-132">The MIB is defined starting on line 32.</span></span> <span data-ttu-id="91670-133">Em seguida, o Agente SNMP é criado em "*tx_application_define*" na linha 129.</span><span class="sxs-lookup"><span data-stu-id="91670-133">Next, the SNMP Agent is created in “*tx_application_define*” at line 129.</span></span> <span data-ttu-id="91670-134">Note que o bloco de controlo do agente SNMP "*my_agent*" foi definido como uma variável global na linha 18 anteriormente.</span><span class="sxs-lookup"><span data-stu-id="91670-134">Note that the SNMP Agent control block “*my_agent*” was defined as a global variable at line 18 previously.</span></span> <span data-ttu-id="91670-135">Se o IPv6 estiver ativado, os endereços IPv6 estão registados na instância IP nas linhas 166-223.</span><span class="sxs-lookup"><span data-stu-id="91670-135">If IPv6 is enabled, the IPv6 addresses are registered with the IP instance in lines 166-223.</span></span> <span data-ttu-id="91670-136">O Agente SNMP é iniciado na linha 229.</span><span class="sxs-lookup"><span data-stu-id="91670-136">SNMP Agent is started at line 229.</span></span> <span data-ttu-id="91670-137">As definições de retorno de objeto SNMP para pedidos de get, GETNEXT e SET do gestor SNMP, bem como pedidos de username e MIB, são processadas a partir da linha 250.</span><span class="sxs-lookup"><span data-stu-id="91670-137">SNMP object callback definitions for SNMP manager GET, GETNEXT and SET requests, as well as username and MIB update requests, are processed starting at line 250.</span></span> <span data-ttu-id="91670-138">Para este exemplo, não é realizado qualquer autenticação.</span><span class="sxs-lookup"><span data-stu-id="91670-138">For this example, no authenticate is performed.</span></span>

> [!NOTE]
> <span data-ttu-id="91670-139">*A tabela MIB2 apresentada abaixo é simplesmente um exemplo. A aplicação pode utilizar um MIB diferente e incluí-lo em ficheiros separados, bem como definir o processamento GET, GETNEXT ou SET de acordo com os seus requisitos de aplicação.*</span><span class="sxs-lookup"><span data-stu-id="91670-139">*The MIB2 table shown below is simply an example. The application may use a different MIB and include it in separate files, as well as define GET, GETNEXT, or SET processing as per their application requirements.*</span></span>

```c
/* This is a small demo of the NetX SNMP Agent on the high-performance NetX TCP/IP  
   stack. This demo relies on ThreadX and NetX to show simple SNMP the SNMP
   GET/GETNEXT/SET requests on MIB-2 objects.  */

#include  "tx_api.h"
#include  "nx_api.h"
#include  "nxd_snmp.h"
#include  "demo_snmp_helper.h"

#define     DEMO_STACK_SIZE         4096
#define     AGENT_PRIMARY_ADDRESS   IP_ADDRESS(192, 2, 2, 66)

/* Define the ThreadX and NetX object control blocks...  */

TX_THREAD               thread_0;
NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;
NX_SNMP_AGENT           my_agent;


/* Indicate if using IPv6 to communicate with SNMP servers. Note that
   IPv6 must be enabled in the NetX Duo library first. Further, IPv6
   and ICMPv6 services are enabled before starting the SNMP agent. */
#define USE_IPV6


/* Define authentication and privacy keys.  */

#ifdef AUTHENTICATION_REQUIRED
NX_SNMP_SECURITY_KEY    my_authentication_key;
#endif

#ifdef PRIVACY_REQUIRED
NX_SNMP_SECURITY_KEY    my_privacy_key;
#endif

/* Define an error counter variable. */
UINT error_counter = 0;

/* This binds a secondary interfaces to the primary IP network interface 
   if SNMP is required for required for that interface. */
/* #define  MULTI_HOMED_DEVICE */

/* Define function prototypes.  A generic ram driver is used in this demo.  However
   to properly run an SNMP agent demo, a real driver should be substituted. */

VOID    thread_agent_entry(ULONG thread_input);
VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);
UINT    mib2_get_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data);
UINT    mib2_getnext_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data);
UINT    mib2_set_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data);
UINT    mib2_username_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *username);
VOID    mib2_variable_update(NX_IP *ip_ptr, NX_SNMP_AGENT *agent_ptr);


UCHAR context_engine_id[] = {0x80, 0x00, 0x0d, 0xfe, 0x03, 0x00, 0x11, 0x23, 0x23, 
                             0x44, 0x55};
UINT  context_engine_size = 11;
UCHAR context_name[] = {0x69, 0x6e, 0x69, 0x74, 0x69, 0x61, 0x6c};
UINT  context_name_size = 7;

/* Define main entry point.  */

int main()
{

   /* Enter the ThreadX kernel.  */
   tx_kernel_enter();
}


/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

UCHAR   *pointer;
UINT    status;


   /* Setup the working pointer.  */
   pointer =  (UCHAR *) first_unused_memory;

   status = tx_thread_create(&thread_0, "agent thread", thread_agent_entry, 0,  
            pointer, DEMO_STACK_SIZE, 
            4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
   if (status != NX_SUCCESS)
   {
      return;
   }

   pointer =  pointer + DEMO_STACK_SIZE;


   /* Initialize the NetX system.  */
   nx_system_initialize();

   /* Create packet pool.  */
   status = nx_packet_pool_create(&pool_0, "NetX Packet Pool 0", 2048, 
                                   pointer, 20000);

   if (status != NX_SUCCESS)
   {
      return;
   }
  
   pointer = pointer + 20000;
  
   /* Create an IP instance.  */
   status = nx_ip_create(&ip_0, "SNMP Agent IP Instance", AGENT_PRIMARY_ADDRESS, 
                        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                        pointer, 4096, 1);

   if (status != NX_SUCCESS)
   {
      return;
   }
  
   pointer =  pointer + 4096;
  
   /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
   nx_arp_enable(&ip_0, (void *) pointer, 1024);
   pointer = pointer + 1024;

   /* Enable UPD processing for IP instance.  */
   nx_udp_enable(&ip_0);
  
   /* Enable ICMP for ping.  */
   nx_icmp_enable(&ip_0);
  
   /* Create an SNMP agent instance.  */
   status = nx_snmp_agent_create(&my_agent, "SNMP Agent", &ip_0, pointer, 4096, 
                                 &pool_0, 
                                 mib2_username_processing, mib2_get_processing, 
                                 mib2_getnext_processing, 
                                 mib2_set_processing);


  
   if (status != NX_SUCCESS)
   {
      return;
   }
  
   pointer =  pointer + 4096;
  
   status = nx_snmp_agent_context_engine_set(&my_agent, context_engine_id, 
                                             context_engine_size);
  
   if (status != NX_SUCCESS)
   {
      error_counter++;
   }
  
   return;
}
  
VOID thread_agent_entry(ULONG thread_input)
{
  
#ifdef USE_IPV6
UINT        iface_index, address_index;
UINT        status;
NXD_ADDRESS agent_ipv6_address;
#endif
  
  
      /* Allow NetX time to get initialized. */
      tx_thread_sleep(100);
  
      /* If using IPv6, enable IPv6 and ICMPv6 services and get IPv6 addresses 
         registered with NetX Dou. */
  
#ifdef USE_IPV6
  
      /* Enable IPv6 on the IP instance. */
      status = nxd_ipv6_enable(&ip_0);
   
      /* Check for enable errors.  */
      if (status)
      {
  
         error_counter++;
         return;
      }
      /* Enable ICMPv6 on the IP instance. */
      status = nxd_icmp_enable(&ip_0);
  
      /* Check for enable errors.  */
      if (status)
      {
  
         error_counter++;
         return;
      }
  
      agent_ipv6_address.nxd_ip_address.v6[3] = 0x101;
      agent_ipv6_address.nxd_ip_address.v6[2] = 0x0;
      agent_ipv6_address.nxd_ip_address.v6[1] = 0x0000f101;
      agent_ipv6_address.nxd_ip_address.v6[0] = 0x20010db8;
      agent_ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
  
      /* Set the primary interface for our DNS IPv6 addresses. */
      iface_index = 0;
  
      /* This assumes we are using the primary network interface (index 0). */
      status = nxd_ipv6_address_set(&ip_0, iface_index, NX_NULL, 10, &address_index);
  
      /* Check for link local address set error.  */
      if (status) 
      {
  
         error_counter++;
         return;
      }
  
      /* Set the host global IP address. We are assuming a 64 
         bit prefix here but this can be any value (< 128). */
      status = nxd_ipv6_address_set(&ip_0, iface_index, &agent_ipv6_address, 64, 
                                    &address_index);
  
      /* Check for global address set error.  */
      if (status) 
      {
  
         error_counter++;
         return;
      }

      /* Wait while NetX Duo validates the link local and global address. */
      tx_thread_sleep(500);
#endif
  
#ifdef AUTHENTICATION_REQUIRED

      /* Create an authentication key.  */
      nx_snmp_agent_md5_key_create(&my_agent, "authpassword", &my_authentication_key);
  
      /* Use the authentication key.  */
      nx_snmp_agent_authenticate_key_use(&my_agent, &my_authentication_key);
#endif
  
#ifdef PRIVACY_REQUIRED
  
      /* Create a privacy key.  */
      nx_snmp_agent_md5_key_create(&my_agent, "privpassword", &my_privacy_key);
  
      /* Use the privacy key.  */
      nx_snmp_agent_privacy_key_use(&my_agent, &my_privacy_key);
#endif
  
      /* Start the SNMP instance.  */
      nx_snmp_agent_start(&my_agent);
  
}
  
/* Define the application's GET processing routine.  */
  
UINT    mib2_get_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data)
{
  
UINT    i;
UINT    status;
  
  
      printf("SNMP Manager GET Request For:  %s", object_requested);
  
      /* Loop through the sample MIB to see if we have information for the supplied 
         variable.  */
      i =  0;
      status =  NX_SNMP_ERROR;
      while (mib2_mib[i].object_name)
      {
  
         /* See if we have found the matching entry.  */
         status =  nx_snmp_object_compare(object_requested, mib2_mib[i].object_name);
  
         /* Was it found?  */
         if (status == NX_SUCCESS)
         {
  
            /* Yes it was found.  */
            break;
         }
  
         /* Move to the next index.  */
         i++;
      }
  
      /* Determine if a not found condition is present.  */
      if (status != NX_SUCCESS)
      {
  
         printf(" NO SUCH NAME!\n");
  
         /* The object was not found - return an error.  */
         return(NX_SNMP_ERROR_NOSUCHNAME);
      }
  
      /* Determine if the entry has a get function.  */
      if (mib2_mib[i].object_get_callback)
      {
  
         /* Yes, call the get function.  */
         status =  (mib2_mib[i].object_get_callback)(mib2_mib[i].object_value_ptr, 
                                                     object_data);
      }
      else
      {
  
         printf(" NO GET FUNCTION!");
  
         /* No get function, return no access.  */
         status =  NX_SNMP_ERROR_NOACCESS;
      }
  
      printf("\n");

      /* Return the status.  */
      return(status);
}
  
  
/* Define the application's GETNEXT processing routine.  */
  
UINT    mib2_getnext_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                                NX_SNMP_OBJECT_DATA *object_data)
{
  
UINT    i;
UINT    status;
  
  
   printf("SNMP Manager GETNEXT Request For:  %s", object_requested);
  
   /* Loop through the sample MIB to see if we have information for the supplied 
      variable.  */
      i =  0;
      status =  NX_SNMP_ERROR;
      while (mib2_mib[i].object_name)
      {
  
         /* See if we have found the next entry.  */
         status =  nx_snmp_object_compare(object_requested, mib2_mib[i].object_name);
  
         /* Is the next entry the mib greater?  */
         if (status == NX_SNMP_NEXT_ENTRY)
         {
  
            /* Yes it was found.  */
            break;
         }
  
         /* Move to the next index.  */
         i++;
      }
  
      /* Determine if a not found condition is present.  */
      if (status != NX_SNMP_NEXT_ENTRY)
      {
  
         printf(" NO SUCH NAME!\n");
  
         /* The object was not found - return an error.  */
         return(NX_SNMP_ERROR_NOSUCHNAME);
      }
  
  
      /* Copy the new name into the object.  */
      nx_snmp_object_copy(mib2_mib[i].object_name, object_requested);
  
      printf(" Next Name is: %s", object_requested);
  
      /* Determine if the entry has a get function.  */
      if (mib2_mib[i].object_get_callback)
      {
  
         /* Yes, call the get function.  */
         status =  (mib2_mib[i].object_get_callback)(mib2_mib[i].object_value_ptr, 
                                                     object_data);
  
         /* Determine if the object data indicates an end-of-mib condition.  */
         if (object_data -> nx_snmp_object_data_type == NX_SNMP_END_OF_MIB_VIEW)
         {
  
            /* Copy the name supplied in the mib table.  */
            nx_snmp_object_copy(mib2_mib[i].object_value_ptr, object_requested);
         }
      }
      else
      {
  
         printf(" NO GET FUNCTION!");
  
         /* No get function, return no access.  */
         status =  NX_SNMP_ERROR_NOACCESS;
      }
  
      printf("\n");

      /* Return the status.  */
      return(status);
}
  
  
/* Define the application's SET processing routine.  */
  
UINT    mib2_set_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data)
{
  
UINT    i;
UINT    status;
  
  
   printf("SNMP Manager SET Request For:  %s", object_requested);
  
   /* Loop through the sample MIB to see if we have information for the supplied variable.  */
      i =  0;
      status =  NX_SNMP_ERROR;
      while (mib2_mib[i].object_name)
      {
  
         /* See if we have found the matching entry.  */
         status =  nx_snmp_object_compare(object_requested, mib2_mib[i].object_name);
  
         /* Was it found?  */
         if (status == NX_SUCCESS)
         {
  
            /* Yes it was found.  */
            break;
         }
  
         /* Move to the next index.  */
         i++;
      }
  
      /* Determine if a not found condition is present.  */
      if (status != NX_SUCCESS)
      {
  
         printf(" NO SUCH NAME!\n");
  
         /* The object was not found - return an error.  */
         return(NX_SNMP_ERROR_NOSUCHNAME);
      }
  
  
      /* Determine if the entry has a set function.  */
      if (mib2_mib[i].object_set_callback)
      {
  
         /* Yes, call the set function.  */
         status =  (mib2_mib[i].object_set_callback)(mib2_mib[i].object_value_ptr, 
                                                     object_data);
      }
      else
      {
  
         printf(" NO SET FUNCTION!");
  
         /* No get function, return no access.  */
         status =  NX_SNMP_ERROR_NOACCESS;
      }
  
      printf("\n");

      /* Return the status.  */
      return(status);
}
  
  
/* Define the application's authentication routine.  */
  
UINT  mib2_username_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *username)
{
  
      printf("Username is:  %s\n", username);
  
      /* Update MIB-2 objects. In this example, it is only the SNMP objects.  */
      mib2_variable_update(&ip_0, &my_agent);
  
      /* No authentication is done, just return success!  */
      return(NX_SUCCESS);
}
  
  
/* Define the application's update routine.  */ 
  
VOID  mib2_variable_update(NX_IP *ip_ptr, NX_SNMP_AGENT *agent_ptr)
{
  
      /* Update the snmp parameters.  */
      snmpInPkts =                agent_ptr -> nx_snmp_agent_packets_received;
      snmpOutPkts =               agent_ptr -> nx_snmp_agent_packets_sent;
      snmpInBadVersions =         agent_ptr -> nx_snmp_agent_invalid_version;
      snmpInBadCommunityNames =   agent_ptr -> nx_snmp_agent_authentication_errors;
      snmpInBadCommunityUsers =   agent_ptr -> nx_snmp_agent_username_errors; 
      snmpInASNParseErrs =        agent_ptr -> nx_snmp_agent_internal_errors;
      snmpInTotalReqVars =        agent_ptr -> nx_snmp_agent_total_get_variables;
      snmpInTotalSetVars =        agent_ptr -> nx_snmp_agent_total_set_variables;
      snmpInGetRequests =         agent_ptr -> nx_snmp_agent_get_requests;
      snmpInGetNexts =            agent_ptr -> nx_snmp_agent_getnext_requests;
      snmpInSetRequests =         agent_ptr -> nx_snmp_agent_set_requests;
      snmpOutTooBigs =            agent_ptr -> nx_snmp_agent_too_big_errors;
      snmpOutNoSuchNames =        agent_ptr -> nx_snmp_agent_no_such_name_errors;
      snmpOutBadValues =          agent_ptr -> nx_snmp_agent_bad_value_errors;
      snmpOutGenErrs =            agent_ptr -> nx_snmp_agent_general_errors;
      snmpOutTraps =              agent_ptr -> nx_snmp_agent_traps_sent;
}   
```
<span data-ttu-id="91670-140">Figura 1.0 Exemplo da utilização do agente SNMP com a NetX Duo</span><span class="sxs-lookup"><span data-stu-id="91670-140">Figure 1.0 Example of SNMP Agent use with NetX Duo</span></span>

## <a name="configuration-options"></a><span data-ttu-id="91670-141">Opções de configuração</span><span class="sxs-lookup"><span data-stu-id="91670-141">Configuration Options</span></span>

<span data-ttu-id="91670-142">Existem várias opções de configuração para a construção do SNMP para o NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="91670-142">There are several configuration options for building SNMP for NetX Duo.</span></span> <span data-ttu-id="91670-143">Segue-se uma lista de todas as opções, onde cada uma é descrita em detalhe:</span><span class="sxs-lookup"><span data-stu-id="91670-143">Following is a list of all options, where each is described in detail:</span></span>  
  
| <span data-ttu-id="91670-144">Definir</span><span class="sxs-lookup"><span data-stu-id="91670-144">Define</span></span>                     | <span data-ttu-id="91670-145">Significado</span><span class="sxs-lookup"><span data-stu-id="91670-145">Meaning</span></span>                                                                                                                                                                                                                                                                        |
|----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="91670-146">**NX_SNMP_AGENT_PRIORITY**</span><span class="sxs-lookup"><span data-stu-id="91670-146">**NX_SNMP_AGENT_PRIORITY**</span></span>     | <span data-ttu-id="91670-147">A prioridade da linha SNMP AGENT.</span><span class="sxs-lookup"><span data-stu-id="91670-147">The priority of the SNMP AGENT thread.</span></span> <span data-ttu-id="91670-148">Por predefinição, este valor é definido como 16 para especificar a prioridade 16.</span><span class="sxs-lookup"><span data-stu-id="91670-148">By default, this value is defined as 16 to specify priority 16.</span></span>                                                                                                                                                                         |
| <span data-ttu-id="91670-149">**NX_SNMP_TYPE_OF_SERVICE**</span><span class="sxs-lookup"><span data-stu-id="91670-149">**NX_SNMP_TYPE_OF_SERVICE**</span></span>    | <span data-ttu-id="91670-150">Tipo de serviço necessário para as respostas UDP SNMP.</span><span class="sxs-lookup"><span data-stu-id="91670-150">Type of service required for the SNMP UDP responses.</span></span> <span data-ttu-id="91670-151">Por predefinição, este valor é definido como NX_IP_NORMAL para indicar o serviço normal de pacotes IP.</span><span class="sxs-lookup"><span data-stu-id="91670-151">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span> <span data-ttu-id="91670-152">Esta definição pode ser definida pela aplicação antes da inclusão do *nxd_snmp.h.*</span><span class="sxs-lookup"><span data-stu-id="91670-152">This define can be set by the application prior to inclusion of *nxd_snmp.h.*</span></span>                                                       |
| <span data-ttu-id="91670-153">**NX_SNMP_FRAGMENT_OPTION**</span><span class="sxs-lookup"><span data-stu-id="91670-153">**NX_SNMP_FRAGMENT_OPTION**</span></span>    | <span data-ttu-id="91670-154">Fragmento ativar os pedidos de UDP SNMP.</span><span class="sxs-lookup"><span data-stu-id="91670-154">Fragment enable for SNMP UDP requests.</span></span> <span data-ttu-id="91670-155">Por padrão, este valor é NX_DONT_FRAGMENT para desativar a fragmentação do UDP SNMP.</span><span class="sxs-lookup"><span data-stu-id="91670-155">By default, this value is NX_DONT_FRAGMENT to disable SNMP UDP fragmenting.</span></span> <span data-ttu-id="91670-156">Esta definição pode ser definida pela aplicação antes da inclusão do *nxd_snmp.h.*</span><span class="sxs-lookup"><span data-stu-id="91670-156">This define can be set by the application prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                 |
| <span data-ttu-id="91670-157">**NX_SNMP_TIME_TO_LIVE**</span><span class="sxs-lookup"><span data-stu-id="91670-157">**NX_SNMP_TIME_TO_LIVE**</span></span>       | <span data-ttu-id="91670-158">Especifica o tempo de vida antes de expirar.</span><span class="sxs-lookup"><span data-stu-id="91670-158">Specifies the time to live before it expires.</span></span> <span data-ttu-id="91670-159">O valor predefinido é definido para 0x80, mas pode ser redefinido antes da inclusão de *nxd_snmp.h.*</span><span class="sxs-lookup"><span data-stu-id="91670-159">The default value is set to 0x80, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                                                         |
| <span data-ttu-id="91670-160">**NX_SNMP_AGENT_TIMEOUT**</span><span class="sxs-lookup"><span data-stu-id="91670-160">**NX_SNMP_AGENT_TIMEOUT**</span></span>      | <span data-ttu-id="91670-161">Especifica o número de carraças ThreadX que os serviços internos vão suspender.</span><span class="sxs-lookup"><span data-stu-id="91670-161">Specifies the number of ThreadX ticks that internal services will suspend for.</span></span> <span data-ttu-id="91670-162">O valor predefinido é definido para 100, mas pode ser redefinido antes da inclusão de *nxd_snmp.h.*</span><span class="sxs-lookup"><span data-stu-id="91670-162">The default value is set to 100, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                         |
| <span data-ttu-id="91670-163">**NX_SNMP_MAX_OCTET_STRING**</span><span class="sxs-lookup"><span data-stu-id="91670-163">**NX_SNMP_MAX_OCTET_STRING**</span></span>   | <span data-ttu-id="91670-164">Especifica o número máximo de bytes permitidos numa cadeia de octetos no Agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="91670-164">Specifies the maximum number of bytes allowed in an octet string in the SNMP Agent.</span></span> <span data-ttu-id="91670-165">O valor predefinido é definido para 255, mas pode ser redefinido antes da inclusão de *nxd_snmp.h.*</span><span class="sxs-lookup"><span data-stu-id="91670-165">The default value is set to 255, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                    |
| <span data-ttu-id="91670-166">**NX_SNMP_MAX_CONTEXT_STRING**</span><span class="sxs-lookup"><span data-stu-id="91670-166">**NX_SNMP_MAX_CONTEXT_STRING**</span></span> | <span data-ttu-id="91670-167">Especifica o número máximo de bytes para uma cadeia de motor de contexto no Agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="91670-167">Specifies the maximum number of bytes for a context engine string in the SNMP Agent.</span></span> <span data-ttu-id="91670-168">O valor predefinido é definido para 32, mas pode ser redefinido antes da inclusão de *nxd_snmp.h.*</span><span class="sxs-lookup"><span data-stu-id="91670-168">The default value is set to 32, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                    |
| <span data-ttu-id="91670-169">**NX_SNMP_MAX_USER_NAME**</span><span class="sxs-lookup"><span data-stu-id="91670-169">**NX_SNMP_MAX_USER_NAME**</span></span>      | <span data-ttu-id="91670-170">Especifica o número máximo de bytes num nome de utilizador (incluindo cordas comunitárias).</span><span class="sxs-lookup"><span data-stu-id="91670-170">Specifies the maximum number of bytes in a username (including community strings).</span></span> <span data-ttu-id="91670-171">O valor predefinido é definido para 64, mas pode ser redefinido antes da inclusão de *nxd_snmp.h.*</span><span class="sxs-lookup"><span data-stu-id="91670-171">The default value is set to 64, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                      |
| <span data-ttu-id="91670-172">**NX_SNMP_MAX_SECURITY_KEY**</span><span class="sxs-lookup"><span data-stu-id="91670-172">**NX_SNMP_MAX_SECURITY_KEY**</span></span>   | <span data-ttu-id="91670-173">Especifica o número de bytes permitidos numa corda de chave de segurança.</span><span class="sxs-lookup"><span data-stu-id="91670-173">Specifies the number of bytes allowed in a security key string.</span></span> <span data-ttu-id="91670-174">O valor predefinido é definido para 64, mas pode ser redefinido antes da exclusão de *nxd_snmp.h.*</span><span class="sxs-lookup"><span data-stu-id="91670-174">The default value is set to 64, but can be redefined prior to nclusion of *nxd_snmp.h.*</span></span>                                                                                                                          |
| <span data-ttu-id="91670-175">**NX_SNMP_PACKET_SIZE**</span><span class="sxs-lookup"><span data-stu-id="91670-175">**NX_SNMP_PACKET_SIZE**</span></span>        | <span data-ttu-id="91670-176">Especifica o tamanho mínimo dos pacotes na piscina especificado na criação do Agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="91670-176">Specifies the minimum size of the packets in the pool specified at SNMP Agent creation.</span></span> <span data-ttu-id="91670-177">O tamanho mínimo é necessário para garantir que a carga útil completa do SNMP possa ser contida num pacote.</span><span class="sxs-lookup"><span data-stu-id="91670-177">The minimum size is needed to ensure the complete SNMP payload can be contained in one packet.</span></span> <span data-ttu-id="91670-178">O valor predefinido é definido para 560, mas pode ser redefinido antes da inclusão de *nxd_snmp.h.*</span><span class="sxs-lookup"><span data-stu-id="91670-178">The default value is set to 560, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span> |
| <span data-ttu-id="91670-179">**NX_SNMP_AGENT_PORT**</span><span class="sxs-lookup"><span data-stu-id="91670-179">**NX_SNMP_AGENT_PORT**</span></span>         | <span data-ttu-id="91670-180">Especifica a porta UDP para fazer os pedidos do SNMP Manager.</span><span class="sxs-lookup"><span data-stu-id="91670-180">Specifies the UDP port to field SNMP Manager requests on.</span></span> <span data-ttu-id="91670-181">A porta padrão é a porta UDP 161, mas pode ser redefinida antes da inclusão do *nxd_snmp.h.*</span><span class="sxs-lookup"><span data-stu-id="91670-181">The default port is UDP port 161, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                                             |
| <span data-ttu-id="91670-182">**NX_SNMP_MANAGER_TRAP_PORT**</span><span class="sxs-lookup"><span data-stu-id="91670-182">**NX_SNMP_MANAGER_TRAP_PORT**</span></span>  | <span data-ttu-id="91670-183">Especifica a porta UDP para enviar pedidos de armadilha de agente SNMP para.</span><span class="sxs-lookup"><span data-stu-id="91670-183">Specifies the UDP port to send SNMP Agent trap requests to.</span></span> <span data-ttu-id="91670-184">A porta padrão é a porta UDP 162, mas pode ser redefinida antes da inclusão do *nxd_snmp.h.*</span><span class="sxs-lookup"><span data-stu-id="91670-184">The default port is UDP port 162, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                                           |
| <span data-ttu-id="91670-185">**NX_SNMP_MAX_TRAP_NAME**</span><span class="sxs-lookup"><span data-stu-id="91670-185">**NX_SNMP_MAX_TRAP_NAME**</span></span>      | <span data-ttu-id="91670-186">Especifica o tamanho da matriz para segurar o nome de utilizador enviado com mensagens de armadilha.</span><span class="sxs-lookup"><span data-stu-id="91670-186">Specifies the size of the array to hold the username sent with trap messages.</span></span> <span data-ttu-id="91670-187">O valor predefinido é 64.</span><span class="sxs-lookup"><span data-stu-id="91670-187">The default value is 64.</span></span>                                                                                                                                                                         |
| <span data-ttu-id="91670-188">**NX_SNMP_MAX_TRAP_KEY**</span><span class="sxs-lookup"><span data-stu-id="91670-188">**NX_SNMP_MAX_TRAP_KEY**</span></span>       | <span data-ttu-id="91670-189">Especifica o tamanho das chaves de autenticação e privacidade para mensagens de armadilha.</span><span class="sxs-lookup"><span data-stu-id="91670-189">Specifies the size of the authentication and privacy keys for trap messages.</span></span> <span data-ttu-id="91670-190">O valor predefinido é 64.</span><span class="sxs-lookup"><span data-stu-id="91670-190">The default value is 64.</span></span>                                                                                                                                                                          |
| <span data-ttu-id="91670-191">**NX_SNMP_TIME_INTERVAL**</span><span class="sxs-lookup"><span data-stu-id="91670-191">**NX_SNMP_TIME_INTERVAL**</span></span>      | <span data-ttu-id="91670-192">Isto determina o intervalo de sono nos carraças temporizadores tomadas pela tarefa de linha SNMP entre os pacotes SNMP recebidos.</span><span class="sxs-lookup"><span data-stu-id="91670-192">This determines the sleep interval in timer ticks taken by the SNMP thread task between processing received SNMP packets.</span></span> <span data-ttu-id="91670-193">O valor predefinido é 100.</span><span class="sxs-lookup"><span data-stu-id="91670-193">The default value is 100.</span></span> <span data-ttu-id="91670-194">Durante este intervalo de sono, a aplicação de anfitrião tem acesso aos serviços da API SNMP.</span><span class="sxs-lookup"><span data-stu-id="91670-194">During this sleep interval the host application has access to SNMP API services.</span></span>                                           |
| <span data-ttu-id="91670-195">**NX_SNMP_DISABLE_V1**</span><span class="sxs-lookup"><span data-stu-id="91670-195">**NX_SNMP_DISABLE_V1**</span></span>         | <span data-ttu-id="91670-196">Definido, isto remove todo o processamento da Versão 1 do SNMP em *nxd_snmp.c.*</span><span class="sxs-lookup"><span data-stu-id="91670-196">Defined, this removes all the SNMP Version 1 processing in *nxd_snmp.c.*</span></span> <span data-ttu-id="91670-197">Por defeito, isto não está definido.</span><span class="sxs-lookup"><span data-stu-id="91670-197">By default this is not defined.</span></span>                                                                                                                                                                         |
| <span data-ttu-id="91670-198">**NX_SNMP_DISABLE_V2**</span><span class="sxs-lookup"><span data-stu-id="91670-198">**NX_SNMP_DISABLE_V2**</span></span>         | <span data-ttu-id="91670-199">Definido, isto remove todo o processamento da Versão 2 do SNMP em *nxd_snmp.c.*</span><span class="sxs-lookup"><span data-stu-id="91670-199">Defined, this removes all the SNMP Version 2 processing in *nxd_snmp.c.*</span></span> <span data-ttu-id="91670-200">Por defeito, isto não está definido.</span><span class="sxs-lookup"><span data-stu-id="91670-200">By default this is not defined.</span></span>                                                                                                                                                                         |
| <span data-ttu-id="91670-201">**NX_SNMP_DISABLE_V3**</span><span class="sxs-lookup"><span data-stu-id="91670-201">**NX_SNMP_DISABLE_V3**</span></span>         | <span data-ttu-id="91670-202">Definido, isto remove todo o processamento SNMPv3 em *nxd_snmp.c.*</span><span class="sxs-lookup"><span data-stu-id="91670-202">Defined, this removes all the SNMPv3 processing in *nxd_snmp.c.*</span></span> <span data-ttu-id="91670-203">Por defeito, isto não está definido.</span><span class="sxs-lookup"><span data-stu-id="91670-203">By default this is not defined.</span></span>                                                                                                                                                                                 |