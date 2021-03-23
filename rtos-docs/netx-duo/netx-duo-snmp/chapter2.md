---
title: Rozdział 2 — Instalowanie i korzystanie z agenta SNMP usługi Azure RTO NetX Duo
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika agenta SNMP NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f011b73217c7f413dd19c555e9c2d40dace305ee
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821667"
---
# <a name="chapter-2---installation-and-use-of-the-azure-rtos-netx-duo-snmp-agent"></a><span data-ttu-id="bb5d7-103">Rozdział 2 — Instalowanie i korzystanie z agenta SNMP usługi Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="bb5d7-103">Chapter 2 - Installation and use of the Azure RTOS NetX Duo SNMP agent</span></span>

<span data-ttu-id="bb5d7-104">Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika agenta SNMP usługi Azure RTO NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo SNMP agent component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="bb5d7-105">Dystrybucja produktu</span><span class="sxs-lookup"><span data-stu-id="bb5d7-105">Product Distribution</span></span>

<span data-ttu-id="bb5d7-106">Agent SNMP dla NetX Duo jest dostępny pod adresem [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) .</span><span class="sxs-lookup"><span data-stu-id="bb5d7-106">SNMP Agent for NetX Duo is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="bb5d7-107">Pakiet zawiera cztery pliki źródłowe, jeden plik dołączany i plik PDF, który zawiera ten dokument, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="bb5d7-107">The package includes four source files, one include file, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="bb5d7-108">**nxd_snmp. h** Plik nagłówkowy dla protokołu SNMP dla NetX Duo</span><span class="sxs-lookup"><span data-stu-id="bb5d7-108">**nxd_snmp.h** Header file for SNMP for NetX Duo</span></span>
- <span data-ttu-id="bb5d7-109">**demo_snmp_helper. h** Plik nagłówkowy dla danych SNMP MIB</span><span class="sxs-lookup"><span data-stu-id="bb5d7-109">**demo_snmp_helper.h** Header file for SNMP MIB data</span></span>
- <span data-ttu-id="bb5d7-110">**nxd_snmp. c** Plik źródłowy języka C dla agenta SNMP dla NetX Duo</span><span class="sxs-lookup"><span data-stu-id="bb5d7-110">**nxd_snmp.c** C Source file for SNMP Agent for NetX Duo</span></span>
- <span data-ttu-id="bb5d7-111">**nx_md5. c** Algorytmy Digest MD5</span><span class="sxs-lookup"><span data-stu-id="bb5d7-111">**nx_md5.c** MD5 digest algorithms</span></span>
- <span data-ttu-id="bb5d7-112">**nx_sha. c** Algorytmy szyfrowania SHA</span><span class="sxs-lookup"><span data-stu-id="bb5d7-112">**nx_sha.c** SHA digest algorithms</span></span>
- <span data-ttu-id="bb5d7-113">**nx_des. c** Algorytmy szyfrowania DES</span><span class="sxs-lookup"><span data-stu-id="bb5d7-113">**nx_des.c** DES encryption algorithms</span></span>
- <span data-ttu-id="bb5d7-114">**nxd_snmp.pdf** Podręcznik użytkownika dla agenta SNMP dla NetX Duo</span><span class="sxs-lookup"><span data-stu-id="bb5d7-114">**nxd_snmp.pdf** User Guide for SNMP Agent for NetX Duo</span></span>
- <span data-ttu-id="bb5d7-115">**demo_netxduo_snmp. c** Prosta Prezentacja SNMP</span><span class="sxs-lookup"><span data-stu-id="bb5d7-115">**demo_netxduo_snmp.c** Simple SNMP demonstration</span></span>
- <span data-ttu-id="bb5d7-116">**demo_netxduo_mib2. c** Prosta Demonstracja MIB2 (MIB zawiera elementy adresów IPv6)</span><span class="sxs-lookup"><span data-stu-id="bb5d7-116">**demo_netxduo_mib2.c** Simple MIB2 demonstration (MIB has IPv6 address elements)</span></span>
- <span data-ttu-id="bb5d7-117">**demo_snmp_helper. h** Plik nagłówkowy definiujący elementy MIB</span><span class="sxs-lookup"><span data-stu-id="bb5d7-117">**demo_snmp_helper.h** Header file defining MIB elements</span></span>

## <a name="netx-duo-snmp-agent-installation"></a><span data-ttu-id="bb5d7-118">Instalacja agenta SNMP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="bb5d7-118">NetX Duo SNMP Agent Installation</span></span>

<span data-ttu-id="bb5d7-119">Aby można było korzystać z protokołu SNMP NetX Duo, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-119">In order to use NetX Duo SNMP, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="bb5d7-120">Na przykład jeśli NetX Duo jest zainstalowana w katalogu "*\threadx\arm7\green*", wówczas pliki *nxd_snmp. h*, *nxd_snmp. c*, *nx_md5. c, nx_sha. c* i nx_ *des. c* powinny zostać skopiowane do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-120">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nxd_snmp.h*, *nxd_snmp.c*, *nx_md5.c, nx_sha.c* and nx_ *des.c* files should be copied into this directory.</span></span>

## <a name="using-the-netx-duo-snmp-agent"></a><span data-ttu-id="bb5d7-121">Korzystanie z agenta SNMP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="bb5d7-121">Using the NetX Duo SNMP Agent</span></span>

<span data-ttu-id="bb5d7-122">Aplikacja musi mieć *nxd_snmp. c*, *nx_md5. c, nx_sha. c* i *nx_des. c* w projekcie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-122">The application must have *nxd_snmp.c*, *nx_md5.c, nx_sha.c*, and *nx_des.c* in the build project.</span></span> <span data-ttu-id="bb5d7-123">Kod aplikacji musi również zawierać *nxd_snmp. h* po uwzględnieniu *nx_api. h, aby można* było wywołać usługi SNMP.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-123">The application code must also include *nxd_snmp.h* after it includes *nx_api.h to be* able to invoke SNMP services.</span></span> <span data-ttu-id="bb5d7-124">Te pliki muszą być kompilowane w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone z biblioteką NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-124">These files must be compiled in the same manner as other application files and its object form must be linked to the NetX Duo library.</span></span> <span data-ttu-id="bb5d7-125">To wszystko, co jest wymagane do korzystania z protokołu SNMP NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-125">This is all that is required to use NetX Duo SNMP.</span></span>

> [!NOTE]
> <span data-ttu-id="bb5d7-126">*Jeśli **NX_SNMP_NO_SECURITY** jest określony w procesie kompilacji, pliki nx_md5. c, nx_sha. c i nx_des. c nie są zbędne.*</span><span class="sxs-lookup"><span data-stu-id="bb5d7-126">*If **NX_SNMP_NO_SECURITY** is specified in the build process, the nx_md5.c, nx_sha.c, and nx_des.c files are not needed.*</span></span>

> [!NOTE]
> <span data-ttu-id="bb5d7-127">Ponieważ NetX Duo SNMP korzysta z usług UDP, należy włączyć protokół UDP przy użyciu wywołania *nx_udp_enable* przed użyciem protokołu SNMP.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-127">That since NetX Duo SNMP utilizes UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using SNMP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="bb5d7-128">Mały przykładowy system</span><span class="sxs-lookup"><span data-stu-id="bb5d7-128">Small Example System</span></span>

<span data-ttu-id="bb5d7-129">Przykład użycia agenta SNMP NetX Duo został opisany na rysunku 1,0, który pojawia się poniżej.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-129">An example of how to use NetX Duo SNMP Agent is described in Figure 1.0 that appears below.</span></span> <span data-ttu-id="bb5d7-130">W tym przykładzie plik dołączany SNMP *nxd_snmp. h* jest umieszczony w wierszu 6.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-130">In this example, the SNMP include file *nxd_snmp.h* is brought in at line 6.</span></span> <span data-ttu-id="bb5d7-131">Plik nagłówkowy, który definiuje elementy bazy danych MIB, *demo_snmp_helper. h,* został wprowadzony w wierszu 8.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-131">The header file that defines the MIB database elements, *demo_snmp_helper.h,* is brought in at line 8.</span></span> <span data-ttu-id="bb5d7-132">Definicja MIB jest definiowana od wiersza 32.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-132">The MIB is defined starting on line 32.</span></span> <span data-ttu-id="bb5d7-133">Następnie Agent SNMP jest tworzony w lokalizacji "*tx_application_define*" w wierszu 129.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-133">Next, the SNMP Agent is created in “*tx_application_define*” at line 129.</span></span> <span data-ttu-id="bb5d7-134">Należy zauważyć, że blok sterowania agenta SNMP "*my_agent*" został zdefiniowany jako zmienna globalna w wierszu 18 wcześniej.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-134">Note that the SNMP Agent control block “*my_agent*” was defined as a global variable at line 18 previously.</span></span> <span data-ttu-id="bb5d7-135">W przypadku włączenia protokołu IPv6 adresy IPv6 są rejestrowane przy użyciu wystąpienia adresu IP w wierszach 166-223.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-135">If IPv6 is enabled, the IPv6 addresses are registered with the IP instance in lines 166-223.</span></span> <span data-ttu-id="bb5d7-136">Agent SNMP został uruchomiony w wierszu 229.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-136">SNMP Agent is started at line 229.</span></span> <span data-ttu-id="bb5d7-137">Definicje wywołania zwrotnego obiektów SNMP dla menedżera SNMP żądania GET, GetNext i SET, a także żądania aktualizacji nazwy użytkownika i MIB, są przetwarzane począwszy od wiersza 250.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-137">SNMP object callback definitions for SNMP manager GET, GETNEXT and SET requests, as well as username and MIB update requests, are processed starting at line 250.</span></span> <span data-ttu-id="bb5d7-138">W tym przykładzie nie jest wykonywane uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-138">For this example, no authenticate is performed.</span></span>

> [!NOTE]
> <span data-ttu-id="bb5d7-139">*Tabela MIB2 pokazana poniżej jest po prostu przykładem. Aplikacja może korzystać z innej bazy MIB i zawierać ją w oddzielnych plikach, a także definiować procesy GET, GetNext i SET, zgodnie z ich wymaganiami dotyczącymi aplikacji.*</span><span class="sxs-lookup"><span data-stu-id="bb5d7-139">*The MIB2 table shown below is simply an example. The application may use a different MIB and include it in separate files, as well as define GET, GETNEXT, or SET processing as per their application requirements.*</span></span>

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
<span data-ttu-id="bb5d7-140">Rysunek 1,0 przykład użycia agenta SNMP z NetX Duo</span><span class="sxs-lookup"><span data-stu-id="bb5d7-140">Figure 1.0 Example of SNMP Agent use with NetX Duo</span></span>

## <a name="configuration-options"></a><span data-ttu-id="bb5d7-141">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bb5d7-141">Configuration Options</span></span>

<span data-ttu-id="bb5d7-142">Istnieje kilka opcji konfiguracji dla kompilowania protokołu SNMP dla NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-142">There are several configuration options for building SNMP for NetX Duo.</span></span> <span data-ttu-id="bb5d7-143">Poniżej znajduje się lista wszystkich opcji, w których szczegóły są szczegółowo opisane:</span><span class="sxs-lookup"><span data-stu-id="bb5d7-143">Following is a list of all options, where each is described in detail:</span></span>  
  
| <span data-ttu-id="bb5d7-144">Zdefiniować</span><span class="sxs-lookup"><span data-stu-id="bb5d7-144">Define</span></span>                     | <span data-ttu-id="bb5d7-145">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="bb5d7-145">Meaning</span></span>                                                                                                                                                                                                                                                                        |
|----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="bb5d7-146">**NX_SNMP_AGENT_PRIORITY**</span><span class="sxs-lookup"><span data-stu-id="bb5d7-146">**NX_SNMP_AGENT_PRIORITY**</span></span>     | <span data-ttu-id="bb5d7-147">Priorytet wątku agenta SNMP.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-147">The priority of the SNMP AGENT thread.</span></span> <span data-ttu-id="bb5d7-148">Domyślnie ta wartość jest definiowana jako 16, aby określić priorytet 16.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-148">By default, this value is defined as 16 to specify priority 16.</span></span>                                                                                                                                                                         |
| <span data-ttu-id="bb5d7-149">**NX_SNMP_TYPE_OF_SERVICE**</span><span class="sxs-lookup"><span data-stu-id="bb5d7-149">**NX_SNMP_TYPE_OF_SERVICE**</span></span>    | <span data-ttu-id="bb5d7-150">Typ usługi wymaganej przez protokół SNMP odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-150">Type of service required for the SNMP UDP responses.</span></span> <span data-ttu-id="bb5d7-151">Domyślnie ta wartość jest definiowana jako NX_IP_NORMAL w celu wskazania normalnej usługi pakietów IP.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-151">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span> <span data-ttu-id="bb5d7-152">Ta definicja może być ustawiana przez aplikację przed włączeniem *nxd_snmp. h.*</span><span class="sxs-lookup"><span data-stu-id="bb5d7-152">This define can be set by the application prior to inclusion of *nxd_snmp.h.*</span></span>                                                       |
| <span data-ttu-id="bb5d7-153">**NX_SNMP_FRAGMENT_OPTION**</span><span class="sxs-lookup"><span data-stu-id="bb5d7-153">**NX_SNMP_FRAGMENT_OPTION**</span></span>    | <span data-ttu-id="bb5d7-154">Włączono fragment dla żądań protokołu SNMP UDP.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-154">Fragment enable for SNMP UDP requests.</span></span> <span data-ttu-id="bb5d7-155">Domyślnie ta wartość jest NX_DONT_FRAGMENT, aby wyłączyć funkcję fragmentacji protokołu UDP protokołu SNMP.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-155">By default, this value is NX_DONT_FRAGMENT to disable SNMP UDP fragmenting.</span></span> <span data-ttu-id="bb5d7-156">Ta definicja może być ustawiana przez aplikację przed włączeniem *nxd_snmp. h.*</span><span class="sxs-lookup"><span data-stu-id="bb5d7-156">This define can be set by the application prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                 |
| <span data-ttu-id="bb5d7-157">**NX_SNMP_TIME_TO_LIVE**</span><span class="sxs-lookup"><span data-stu-id="bb5d7-157">**NX_SNMP_TIME_TO_LIVE**</span></span>       | <span data-ttu-id="bb5d7-158">Określa czas wygaśnięcia przed jego wygaśnięciem.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-158">Specifies the time to live before it expires.</span></span> <span data-ttu-id="bb5d7-159">Wartość domyślna to 0x80, ale można ją zdefiniować ponownie przed włączeniem *nxd_snmp. h.*</span><span class="sxs-lookup"><span data-stu-id="bb5d7-159">The default value is set to 0x80, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                                                         |
| <span data-ttu-id="bb5d7-160">**NX_SNMP_AGENT_TIMEOUT**</span><span class="sxs-lookup"><span data-stu-id="bb5d7-160">**NX_SNMP_AGENT_TIMEOUT**</span></span>      | <span data-ttu-id="bb5d7-161">Określa liczbę ThreadXych taktów, dla których będą zawieszane usługi wewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-161">Specifies the number of ThreadX ticks that internal services will suspend for.</span></span> <span data-ttu-id="bb5d7-162">Wartość domyślna to 100, ale można ją zdefiniować ponownie przed włączeniem *nxd_snmp. h.*</span><span class="sxs-lookup"><span data-stu-id="bb5d7-162">The default value is set to 100, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                         |
| <span data-ttu-id="bb5d7-163">**NX_SNMP_MAX_OCTET_STRING**</span><span class="sxs-lookup"><span data-stu-id="bb5d7-163">**NX_SNMP_MAX_OCTET_STRING**</span></span>   | <span data-ttu-id="bb5d7-164">Określa maksymalną dozwoloną liczbę bajtów w ciągu oktetu w agencie SNMP.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-164">Specifies the maximum number of bytes allowed in an octet string in the SNMP Agent.</span></span> <span data-ttu-id="bb5d7-165">Wartość domyślna to 255, ale można ją zdefiniować ponownie przed włączeniem *nxd_snmp. h.*</span><span class="sxs-lookup"><span data-stu-id="bb5d7-165">The default value is set to 255, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                    |
| <span data-ttu-id="bb5d7-166">**NX_SNMP_MAX_CONTEXT_STRING**</span><span class="sxs-lookup"><span data-stu-id="bb5d7-166">**NX_SNMP_MAX_CONTEXT_STRING**</span></span> | <span data-ttu-id="bb5d7-167">Określa maksymalną liczbę bajtów ciągu aparatu kontekstu w agencie SNMP.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-167">Specifies the maximum number of bytes for a context engine string in the SNMP Agent.</span></span> <span data-ttu-id="bb5d7-168">Wartość domyślna to 32, ale można ją zdefiniować ponownie przed włączeniem *nxd_snmp. h.*</span><span class="sxs-lookup"><span data-stu-id="bb5d7-168">The default value is set to 32, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                    |
| <span data-ttu-id="bb5d7-169">**NX_SNMP_MAX_USER_NAME**</span><span class="sxs-lookup"><span data-stu-id="bb5d7-169">**NX_SNMP_MAX_USER_NAME**</span></span>      | <span data-ttu-id="bb5d7-170">Określa maksymalną liczbę bajtów w nazwie użytkownika (w tym ciągi społeczności).</span><span class="sxs-lookup"><span data-stu-id="bb5d7-170">Specifies the maximum number of bytes in a username (including community strings).</span></span> <span data-ttu-id="bb5d7-171">Wartość domyślna to 64, ale można ją zdefiniować ponownie przed włączeniem *nxd_snmp. h.*</span><span class="sxs-lookup"><span data-stu-id="bb5d7-171">The default value is set to 64, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                      |
| <span data-ttu-id="bb5d7-172">**NX_SNMP_MAX_SECURITY_KEY**</span><span class="sxs-lookup"><span data-stu-id="bb5d7-172">**NX_SNMP_MAX_SECURITY_KEY**</span></span>   | <span data-ttu-id="bb5d7-173">Określa liczbę bajtów dozwolonych w ciągu klucza zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-173">Specifies the number of bytes allowed in a security key string.</span></span> <span data-ttu-id="bb5d7-174">Wartość domyślna to 64, ale można ją zdefiniować ponownie przed *nxd_snmp nclusion. h.*</span><span class="sxs-lookup"><span data-stu-id="bb5d7-174">The default value is set to 64, but can be redefined prior to nclusion of *nxd_snmp.h.*</span></span>                                                                                                                          |
| <span data-ttu-id="bb5d7-175">**NX_SNMP_PACKET_SIZE**</span><span class="sxs-lookup"><span data-stu-id="bb5d7-175">**NX_SNMP_PACKET_SIZE**</span></span>        | <span data-ttu-id="bb5d7-176">Określa minimalny rozmiar pakietów w puli określony podczas tworzenia agenta SNMP.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-176">Specifies the minimum size of the packets in the pool specified at SNMP Agent creation.</span></span> <span data-ttu-id="bb5d7-177">Minimalny rozmiar jest wymagany w celu zapewnienia, że kompletny ładunek SNMP może być zawarty w jednym pakiecie.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-177">The minimum size is needed to ensure the complete SNMP payload can be contained in one packet.</span></span> <span data-ttu-id="bb5d7-178">Wartość domyślna to 560, ale można ją zdefiniować ponownie przed włączeniem *nxd_snmp. h.*</span><span class="sxs-lookup"><span data-stu-id="bb5d7-178">The default value is set to 560, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span> |
| <span data-ttu-id="bb5d7-179">**NX_SNMP_AGENT_PORT**</span><span class="sxs-lookup"><span data-stu-id="bb5d7-179">**NX_SNMP_AGENT_PORT**</span></span>         | <span data-ttu-id="bb5d7-180">Określa port UDP do pola żądania menedżera SNMP.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-180">Specifies the UDP port to field SNMP Manager requests on.</span></span> <span data-ttu-id="bb5d7-181">Domyślnym portem jest port UDP 161, ale można go ponownie zdefiniować przed włączeniem *nxd_snmp. h.*</span><span class="sxs-lookup"><span data-stu-id="bb5d7-181">The default port is UDP port 161, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                                             |
| <span data-ttu-id="bb5d7-182">**NX_SNMP_MANAGER_TRAP_PORT**</span><span class="sxs-lookup"><span data-stu-id="bb5d7-182">**NX_SNMP_MANAGER_TRAP_PORT**</span></span>  | <span data-ttu-id="bb5d7-183">Określa port UDP, do którego mają być wysyłane żądania pułapki agenta SNMP.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-183">Specifies the UDP port to send SNMP Agent trap requests to.</span></span> <span data-ttu-id="bb5d7-184">Domyślnym portem jest port UDP 162, ale można go ponownie zdefiniować przed włączeniem *nxd_snmp. h.*</span><span class="sxs-lookup"><span data-stu-id="bb5d7-184">The default port is UDP port 162, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                                           |
| <span data-ttu-id="bb5d7-185">**NX_SNMP_MAX_TRAP_NAME**</span><span class="sxs-lookup"><span data-stu-id="bb5d7-185">**NX_SNMP_MAX_TRAP_NAME**</span></span>      | <span data-ttu-id="bb5d7-186">Określa rozmiar tablicy do przechowywania nazwy użytkownika wysyłanej przy użyciu komunikatów pułapki.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-186">Specifies the size of the array to hold the username sent with trap messages.</span></span> <span data-ttu-id="bb5d7-187">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-187">The default value is 64.</span></span>                                                                                                                                                                         |
| <span data-ttu-id="bb5d7-188">**NX_SNMP_MAX_TRAP_KEY**</span><span class="sxs-lookup"><span data-stu-id="bb5d7-188">**NX_SNMP_MAX_TRAP_KEY**</span></span>       | <span data-ttu-id="bb5d7-189">Określa rozmiar kluczy uwierzytelniania i prywatności dla komunikatów pułapki.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-189">Specifies the size of the authentication and privacy keys for trap messages.</span></span> <span data-ttu-id="bb5d7-190">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-190">The default value is 64.</span></span>                                                                                                                                                                          |
| <span data-ttu-id="bb5d7-191">**NX_SNMP_TIME_INTERVAL**</span><span class="sxs-lookup"><span data-stu-id="bb5d7-191">**NX_SNMP_TIME_INTERVAL**</span></span>      | <span data-ttu-id="bb5d7-192">Określa interwał uśpienia w taktach czasomierza podjętych przez zadanie wątku SNMP między przetwarzaniem odebranych pakietów SNMP.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-192">This determines the sleep interval in timer ticks taken by the SNMP thread task between processing received SNMP packets.</span></span> <span data-ttu-id="bb5d7-193">Wartość domyślna to 100.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-193">The default value is 100.</span></span> <span data-ttu-id="bb5d7-194">W trakcie tego interwału uśpienia aplikacja hosta ma dostęp do usług interfejsu API protokołu SNMP.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-194">During this sleep interval the host application has access to SNMP API services.</span></span>                                           |
| <span data-ttu-id="bb5d7-195">**NX_SNMP_DISABLE_V1**</span><span class="sxs-lookup"><span data-stu-id="bb5d7-195">**NX_SNMP_DISABLE_V1**</span></span>         | <span data-ttu-id="bb5d7-196">Zdefiniowane, spowoduje to usunięcie wszystkich operacji przetwarzania protokołu SNMP w wersji 1 w *nxd_snmp. c.*</span><span class="sxs-lookup"><span data-stu-id="bb5d7-196">Defined, this removes all the SNMP Version 1 processing in *nxd_snmp.c.*</span></span> <span data-ttu-id="bb5d7-197">Domyślnie to nie jest zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-197">By default this is not defined.</span></span>                                                                                                                                                                         |
| <span data-ttu-id="bb5d7-198">**NX_SNMP_DISABLE_V2**</span><span class="sxs-lookup"><span data-stu-id="bb5d7-198">**NX_SNMP_DISABLE_V2**</span></span>         | <span data-ttu-id="bb5d7-199">Zdefiniowane, spowoduje to usunięcie wszystkich operacji przetwarzania protokołu SNMP w wersji 2 w *nxd_snmp. c.*</span><span class="sxs-lookup"><span data-stu-id="bb5d7-199">Defined, this removes all the SNMP Version 2 processing in *nxd_snmp.c.*</span></span> <span data-ttu-id="bb5d7-200">Domyślnie to nie jest zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-200">By default this is not defined.</span></span>                                                                                                                                                                         |
| <span data-ttu-id="bb5d7-201">**NX_SNMP_DISABLE_V3**</span><span class="sxs-lookup"><span data-stu-id="bb5d7-201">**NX_SNMP_DISABLE_V3**</span></span>         | <span data-ttu-id="bb5d7-202">Zdefiniowane, spowoduje to usunięcie wszystkich procesów przetwarzania SNMPv3 w *nxd_snmp. c.*</span><span class="sxs-lookup"><span data-stu-id="bb5d7-202">Defined, this removes all the SNMPv3 processing in *nxd_snmp.c.*</span></span> <span data-ttu-id="bb5d7-203">Domyślnie to nie jest zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="bb5d7-203">By default this is not defined.</span></span>                                                                                                                                                                                 |