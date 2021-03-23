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
# <a name="chapter-2---installation-and-use-of-the-azure-rtos-netx-duo-snmp-agent"></a>Rozdział 2 — Instalowanie i korzystanie z agenta SNMP usługi Azure RTO NetX Duo

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika agenta SNMP usługi Azure RTO NetX Duo.

## <a name="product-distribution"></a>Dystrybucja produktu

Agent SNMP dla NetX Duo jest dostępny pod adresem [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Pakiet zawiera cztery pliki źródłowe, jeden plik dołączany i plik PDF, który zawiera ten dokument, w następujący sposób:

- **nxd_snmp. h** Plik nagłówkowy dla protokołu SNMP dla NetX Duo
- **demo_snmp_helper. h** Plik nagłówkowy dla danych SNMP MIB
- **nxd_snmp. c** Plik źródłowy języka C dla agenta SNMP dla NetX Duo
- **nx_md5. c** Algorytmy Digest MD5
- **nx_sha. c** Algorytmy szyfrowania SHA
- **nx_des. c** Algorytmy szyfrowania DES
- **nxd_snmp.pdf** Podręcznik użytkownika dla agenta SNMP dla NetX Duo
- **demo_netxduo_snmp. c** Prosta Prezentacja SNMP
- **demo_netxduo_mib2. c** Prosta Demonstracja MIB2 (MIB zawiera elementy adresów IPv6)
- **demo_snmp_helper. h** Plik nagłówkowy definiujący elementy MIB

## <a name="netx-duo-snmp-agent-installation"></a>Instalacja agenta SNMP NetX Duo

Aby można było korzystać z protokołu SNMP NetX Duo, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX Duo. Na przykład jeśli NetX Duo jest zainstalowana w katalogu "*\threadx\arm7\green*", wówczas pliki *nxd_snmp. h*, *nxd_snmp. c*, *nx_md5. c, nx_sha. c* i nx_ *des. c* powinny zostać skopiowane do tego katalogu.

## <a name="using-the-netx-duo-snmp-agent"></a>Korzystanie z agenta SNMP NetX Duo

Aplikacja musi mieć *nxd_snmp. c*, *nx_md5. c, nx_sha. c* i *nx_des. c* w projekcie kompilacji. Kod aplikacji musi również zawierać *nxd_snmp. h* po uwzględnieniu *nx_api. h, aby można* było wywołać usługi SNMP. Te pliki muszą być kompilowane w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone z biblioteką NetX Duo. To wszystko, co jest wymagane do korzystania z protokołu SNMP NetX Duo.

> [!NOTE]
> *Jeśli **NX_SNMP_NO_SECURITY** jest określony w procesie kompilacji, pliki nx_md5. c, nx_sha. c i nx_des. c nie są zbędne.*

> [!NOTE]
> Ponieważ NetX Duo SNMP korzysta z usług UDP, należy włączyć protokół UDP przy użyciu wywołania *nx_udp_enable* przed użyciem protokołu SNMP.

## <a name="small-example-system"></a>Mały przykładowy system

Przykład użycia agenta SNMP NetX Duo został opisany na rysunku 1,0, który pojawia się poniżej. W tym przykładzie plik dołączany SNMP *nxd_snmp. h* jest umieszczony w wierszu 6. Plik nagłówkowy, który definiuje elementy bazy danych MIB, *demo_snmp_helper. h,* został wprowadzony w wierszu 8. Definicja MIB jest definiowana od wiersza 32. Następnie Agent SNMP jest tworzony w lokalizacji "*tx_application_define*" w wierszu 129. Należy zauważyć, że blok sterowania agenta SNMP "*my_agent*" został zdefiniowany jako zmienna globalna w wierszu 18 wcześniej. W przypadku włączenia protokołu IPv6 adresy IPv6 są rejestrowane przy użyciu wystąpienia adresu IP w wierszach 166-223. Agent SNMP został uruchomiony w wierszu 229. Definicje wywołania zwrotnego obiektów SNMP dla menedżera SNMP żądania GET, GetNext i SET, a także żądania aktualizacji nazwy użytkownika i MIB, są przetwarzane począwszy od wiersza 250. W tym przykładzie nie jest wykonywane uwierzytelnianie.

> [!NOTE]
> *Tabela MIB2 pokazana poniżej jest po prostu przykładem. Aplikacja może korzystać z innej bazy MIB i zawierać ją w oddzielnych plikach, a także definiować procesy GET, GetNext i SET, zgodnie z ich wymaganiami dotyczącymi aplikacji.*

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
Rysunek 1,0 przykład użycia agenta SNMP z NetX Duo

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji dla kompilowania protokołu SNMP dla NetX Duo. Poniżej znajduje się lista wszystkich opcji, w których szczegóły są szczegółowo opisane:  
  
| Zdefiniować                     | Znaczenie                                                                                                                                                                                                                                                                        |
|----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **NX_SNMP_AGENT_PRIORITY**     | Priorytet wątku agenta SNMP. Domyślnie ta wartość jest definiowana jako 16, aby określić priorytet 16.                                                                                                                                                                         |
| **NX_SNMP_TYPE_OF_SERVICE**    | Typ usługi wymaganej przez protokół SNMP odpowiedzi. Domyślnie ta wartość jest definiowana jako NX_IP_NORMAL w celu wskazania normalnej usługi pakietów IP. Ta definicja może być ustawiana przez aplikację przed włączeniem *nxd_snmp. h.*                                                       |
| **NX_SNMP_FRAGMENT_OPTION**    | Włączono fragment dla żądań protokołu SNMP UDP. Domyślnie ta wartość jest NX_DONT_FRAGMENT, aby wyłączyć funkcję fragmentacji protokołu UDP protokołu SNMP. Ta definicja może być ustawiana przez aplikację przed włączeniem *nxd_snmp. h.*                                                                                 |
| **NX_SNMP_TIME_TO_LIVE**       | Określa czas wygaśnięcia przed jego wygaśnięciem. Wartość domyślna to 0x80, ale można ją zdefiniować ponownie przed włączeniem *nxd_snmp. h.*                                                                                                                                         |
| **NX_SNMP_AGENT_TIMEOUT**      | Określa liczbę ThreadXych taktów, dla których będą zawieszane usługi wewnętrzne. Wartość domyślna to 100, ale można ją zdefiniować ponownie przed włączeniem *nxd_snmp. h.*                                                                                                         |
| **NX_SNMP_MAX_OCTET_STRING**   | Określa maksymalną dozwoloną liczbę bajtów w ciągu oktetu w agencie SNMP. Wartość domyślna to 255, ale można ją zdefiniować ponownie przed włączeniem *nxd_snmp. h.*                                                                                                    |
| **NX_SNMP_MAX_CONTEXT_STRING** | Określa maksymalną liczbę bajtów ciągu aparatu kontekstu w agencie SNMP. Wartość domyślna to 32, ale można ją zdefiniować ponownie przed włączeniem *nxd_snmp. h.*                                                                                                    |
| **NX_SNMP_MAX_USER_NAME**      | Określa maksymalną liczbę bajtów w nazwie użytkownika (w tym ciągi społeczności). Wartość domyślna to 64, ale można ją zdefiniować ponownie przed włączeniem *nxd_snmp. h.*                                                                                                      |
| **NX_SNMP_MAX_SECURITY_KEY**   | Określa liczbę bajtów dozwolonych w ciągu klucza zabezpieczeń. Wartość domyślna to 64, ale można ją zdefiniować ponownie przed *nxd_snmp nclusion. h.*                                                                                                                          |
| **NX_SNMP_PACKET_SIZE**        | Określa minimalny rozmiar pakietów w puli określony podczas tworzenia agenta SNMP. Minimalny rozmiar jest wymagany w celu zapewnienia, że kompletny ładunek SNMP może być zawarty w jednym pakiecie. Wartość domyślna to 560, ale można ją zdefiniować ponownie przed włączeniem *nxd_snmp. h.* |
| **NX_SNMP_AGENT_PORT**         | Określa port UDP do pola żądania menedżera SNMP. Domyślnym portem jest port UDP 161, ale można go ponownie zdefiniować przed włączeniem *nxd_snmp. h.*                                                                                                                             |
| **NX_SNMP_MANAGER_TRAP_PORT**  | Określa port UDP, do którego mają być wysyłane żądania pułapki agenta SNMP. Domyślnym portem jest port UDP 162, ale można go ponownie zdefiniować przed włączeniem *nxd_snmp. h.*                                                                                                                           |
| **NX_SNMP_MAX_TRAP_NAME**      | Określa rozmiar tablicy do przechowywania nazwy użytkownika wysyłanej przy użyciu komunikatów pułapki. Wartość domyślna to 64.                                                                                                                                                                         |
| **NX_SNMP_MAX_TRAP_KEY**       | Określa rozmiar kluczy uwierzytelniania i prywatności dla komunikatów pułapki. Wartość domyślna to 64.                                                                                                                                                                          |
| **NX_SNMP_TIME_INTERVAL**      | Określa interwał uśpienia w taktach czasomierza podjętych przez zadanie wątku SNMP między przetwarzaniem odebranych pakietów SNMP. Wartość domyślna to 100. W trakcie tego interwału uśpienia aplikacja hosta ma dostęp do usług interfejsu API protokołu SNMP.                                           |
| **NX_SNMP_DISABLE_V1**         | Zdefiniowane, spowoduje to usunięcie wszystkich operacji przetwarzania protokołu SNMP w wersji 1 w *nxd_snmp. c.* Domyślnie to nie jest zdefiniowane.                                                                                                                                                                         |
| **NX_SNMP_DISABLE_V2**         | Zdefiniowane, spowoduje to usunięcie wszystkich operacji przetwarzania protokołu SNMP w wersji 2 w *nxd_snmp. c.* Domyślnie to nie jest zdefiniowane.                                                                                                                                                                         |
| **NX_SNMP_DISABLE_V3**         | Zdefiniowane, spowoduje to usunięcie wszystkich procesów przetwarzania SNMPv3 w *nxd_snmp. c.* Domyślnie to nie jest zdefiniowane.                                                                                                                                                                                 |