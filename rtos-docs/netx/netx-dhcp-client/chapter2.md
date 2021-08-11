---
title: Rozdział 2 — Instalowanie i używanie klienta DHCP Azure RTOS NetX
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem Azure RTOS klienta DHCP NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: da27039694c90f74a8b13dc556a367802f66c0ba7dd337f3e31ebab05641a9b1
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788783"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-dhcp-client"></a>Rozdział 2 — Instalowanie i używanie klienta DHCP Azure RTOS NetX

Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem Azure RTOS DHCP NetX.

## <a name="product-distribution"></a>Dystrybucja produktów

Protokół DHCP dla NetX jest dostępny na stronie [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) . Pakiet zawiera dwa pliki źródłowe i plik PDF zawierający ten dokument w następujący sposób:

- **nx_dhcp.h** Plik nagłówkowy dla protokołu DHCP dla NetX

- **nx_dhcp.c** Plik źródłowy języka C dla protokołu DHCP dla NetX

- **nx_dhcp.pdf** Opis protokołu DHCP dla NetX w formacie PDF

- **demo_netx_dhcp.c** Pokaz protokołu DHCP NetX

- **demo_netx_multihome_dhcp_client.c** Pokaz klienta DHCP NetX dla protokołu DHCP w wielu interfejsach

## <a name="dhcp-installation"></a>Instalacja protokołu DHCP

Aby użyć protokołu DHCP dla NetX, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano platformę NetX. Jeśli na przykład netx jest zainstalowany w katalogu *"\threadx\arm7\green",* do tego katalogu powinny zostać skopiowane pliki *nx_dhcp.h* i *nx_dhcp.c.*

## <a name="using-dhcp"></a>Korzystanie z protokołu DHCP

Korzystanie z protokołu DHCP dla NetX jest łatwe. Zasadniczo kod aplikacji musi zawierać kod *nx_dhcp.h* po dojecheniu do niego plików *tx_api.h* i *nx_api.h*, aby można było używać odpowiednio ThreadX i NetX. Po *nx_dhcp.h* kod aplikacji może następnie wykonać wywołania funkcji DHCP określone w dalszej części tego przewodnika. Aplikacja musi również zawierać *nx_dhcp.c* w procesie kompilacji. Ten plik musi zostać skompilowany w taki sam sposób, jak inne pliki aplikacji, a jego formularz obiektu musi być połączony z plikami aplikacji. To wszystko, co jest wymagane do korzystania z protokołu NETX DHCP.

Należy pamiętać, że ponieważ protokół DHCP korzysta z usług NetX UDP, należy włączyć protokół UDP przy *użyciu nx_udp_enable* przed użyciem protokołu DHCP.

Aby uzyskać wcześniej przypisany adres IP, klient DHCP może zainicjować proces DHCP z komunikatem Żądanie i opcją 50 "Żądany adres IP" do serwera DHCP. Serwer DHCP odpowie komunikatem ACK, jeśli przysła adres IP klientowi, lub naCK, jeśli odmówi. W drugim przypadku klient DHCP ponownie uruchamia proces DHCP w stanie Init z komunikatem Odnajdowanie i bez żądanego adresu IP. Aplikacja hosta najpierw tworzy klienta DHCP, *a* następnie wywołuje usługę interfejsu API nx_dhcp_request_client_ip, aby ustawić żądany adres IP przed rozpoczęciem procesu DHCP przy *użyciu nx_dhcp_start*. Przykładowa aplikacja DHCP znajduje się w innym miejscu tego dokumentu, aby uzyskać więcej szczegółów.

## <a name="in-the-bound-state"></a>W stanie powiązana

Gdy klient DHCP jest w stanie powiązanym, wątek klienta DHCP przetwarza stan klienta raz na interwał (zgodnie z NX_DHCP_TIME_INTERVAL) i zmniejsza czas pozostały w dzierżawie IP przypisanej do klienta. Po upływie czasu odnowienia stan klienta DHCP jest aktualizowany do stanu ODNÓW, w którym klient będzie żądał odnowienia z serwera DHCP.


## <a name="sending-dhcp-messages-to-the-server"></a>Wysyłanie komunikatów DHCP do serwera

Klient DHCP ma usługi interfejsu API, które umożliwiają aplikacji hosta wysyłanie komunikatów do serwera DHCP. Należy pamiętać, że te usługi NIE są przeznaczone dla aplikacji hosta do ręcznego uruchamiania protokołu klienta DHCP, ponieważ wysyłają one przede wszystkim komunikat bez konieczności aktualizowania stanu wewnętrznego klienta DHCP.

  - *nx_dhcp_release:* powoduje wysłanie komunikatu RELEASE (WYDANIE) do serwera, gdy aplikacja hosta opuszcza sieć lub wymaga podania adresu IP.

  - *nx_dhcp_decline:* wysyła komunikat ODRZUĆ do serwera, jeśli aplikacja hosta ustali niezależnie od klienta DHCP, że jego adres IP jest już w użyciu.

  - *nx_dhcp_forcerenew:* powoduje wysłanie komunikatu FORCERENEW do serwera

  - *nx_dhcp_send_request:* przyjmuje jako argument typ komunikatu DHCP, jak określono w pliku *nx_dhcp.h*, i wysyła komunikat do serwera. Jest on przeznaczony głównie do wysyłania komunikatu INFORM protokołu DHCP.

Zobacz "*Opis usług DHCP*", aby uzyskać więcej informacji o tych usługach w innym miejscu tego dokumentu.

## <a name="starting-and-stopping-the-dhcp-client"></a>Uruchamianie i zatrzymywanie klienta DHCP

Aby zatrzymać klienta DHCP, niezależnie od tego, czy został osiągnięty stan powiązany, aplikacja hosta wywołuje *nx_dhcp_stop*.

Aby ponownie uruchomić klienta DHCP, aplikacja hosta musi najpierw zatrzymać klienta DHCP przy użyciu *usługi nx_dhcp_stop* opisanej powyżej. Następnie host może wywołać *nx_dhcp_start,* aby wznowić działanie klienta DHCP. Jeśli aplikacja hosta chce wyczyścić poprzedni profil klienta DHCP, na przykład uzyskany z poprzedniego serwera DHCP w innej sieci, aplikacja hosta powinna wywołać usługę *nx_dhcp_reinitialize,* aby wykonać to zadanie wewnętrznie przed wywołaniem nx_dhcp_start.

Typowa sekwencja może być:

```C
nx_dhcp_stop(&my_dhcp);

nx_dhcp_reinitialize(&my_dhcp);

nx_dhcp_start(&my_dhcp);
```

W przypadku aplikacji DHCP działających tylko na jednym interfejsie DHCP zatrzymanie klienta DHCP inaktywuje również czasomierz klienta DHCP. W związku z tym nie jest już śledzone czas pozostały do dzierżawy adresu IP. Zatrzymanie klienta DHCP na określonym interfejsie nie spowoduje uaktywnienia czasomierza klienta DHCP, ale zatrzyma aktualizacje czasomierza do czasu pozostałego w dzierżawie IP tego interfejsu.

Dlatego zatrzymanie klienta DHCP nie jest zalecane, chyba że aplikacja hosta wymaga ponownego uruchomienia lub przełączenia sieci.

## <a name="using-the-dhcp-client-with-auto-ip"></a>Używanie klienta DHCP z automatycznym adresem IP

Klient DHCP NetX działa współbieżnie z protokołem Automatycznego adresu IP w aplikacjach, w których protokół DHCP i automatyczny adres IP gwarantują, że adres serwera DHCP nie będzie dostępny ani odpowiadać. Jeśli jednak host nie może wykryć serwera lub uzyskać przypisanego adresu IP, może przełączyć się do protokołu automatycznego adresu IP dla lokalnego adresu IP. Jednak przed wykonaniem tej opcji zaleca się tymczasowe zatrzymanie klienta DHCP, gdy automatyczny adres IP przechodzi przez etapy "sondowania" i "ochrony". Po przypisaniu do hosta automatycznego adresu IP można ponownie uruchomić klienta DHCP, a jeśli serwer DHCP stanie się dostępny, adres IP hosta może zaakceptować adres IP oferowany przez serwer DHCP, gdy aplikacja jest uruchomiona.

Automatyczny adres IP NetX ma powiadomienie o zmianie adresu dla hosta w celu monitorowania jego działań w przypadku zmiany adresu IP.

## <a name="small-example-system"></a>Mały przykładowy system

Przykład sposobu używania netx został opisany na rysunku 1.1 poniżej. Klient DHCP jest tworzony "*my_thread_entry*" w wierszu 101. Po pomyślnym utworzeniu proces DHCP jest inicjowany przy wywołaniu polecenia *nx_dhcp_start* wierszu 108. W tym momencie inicjowane są próby skontaktowania się klienta DHCP z serwerem DHCP. W trakcie tego procesu kod aplikacji czeka na zarejestrowanie prawidłowego adresu IP w wystąpieniu  adresu IP przy użyciu usługi *nx_ip_status_check* (lub nx_ip_interface_status_check dla interfejsu pomocniczego) począwszy od wiersza 95. Najczęściej jest to wykonywane w pętli z opcją krótszego oczekiwania.

Po wierszu 127 protokół DHCP odebrał prawidłowy adres IP i aplikacja może kontynuować, korzystając z usług TCP/IP NetX zgodnie z potrzebami.

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

Rysunek 1.1 Przykład użycia protokołu DHCP z netx

## <a name="multi-server-environments"></a>Środowiska z wieloma serwerami

W sieciach, w których istnieje więcej niż jeden serwer DHCP, klient DHCP akceptuje pierwszy odebrany komunikat oferty serwera DHCP, przejść do stanu żądania i ignoruje wszystkie inne odebrane oferty.

## <a name="arp-probes"></a>Sondy ARP

Klienta DHCP można skonfigurować do wysyłania co najmniej jednej sondy ARP po przypisaniu adresu IP z serwera DHCP w celu sprawdzenia, czy adres IP nie jest jeszcze w użyciu. Krok sondowania ARP jest zalecany przez środowisko RFC 2131 i jest szczególnie ważny w środowiskach z więcej niż jednym serwerem DHCP. Jeśli aplikacja hosta włącza opcję NX_DHCP_CLIENT_SEND_ARP_PROBE (zobacz Opcje konfiguracji w rozdziale 2, aby uzyskać dodatkowe opcje sondowania ARP), klient DHCP wyśle "samoadresowane" sondę ARP i zaczeka na określony czas odpowiedzi.  Jeśli żadna nie zostanie odebrana, klient DHCP przesunie się do stanu powiązanego. Jeśli zostanie odebrana odpowiedź, klient DHCP zakłada, że adres jest już w użyciu. Automatycznie wysyła komunikat ODRZUĆ do serwera i ponownie inicjalizuje klienta, aby ponownie uruchomić sondy DHCP ze stanu INIT. Powoduje to ponowne uruchomienie komputera stanu DHCP, a klient wysyła kolejny komunikat DISCOVER do serwera.

## <a name="bootp-protocol"></a>Protokół BOOTP

Klient DHCP obsługuje również protokół BOOTP, a także protokół DHCP. Aby włączyć tę opcję i używać rozruchu zamiast protokołu DHCP, aplikacja hosta musi ustawić NX_DHCP_BOOTP_ENABLE konfiguracji. Aplikacja hosta może nadal żądać określonych adresów IP w protokole BOOTP. Klient DHCP nie obsługuje jednak ładowania systemu operacyjnego hosta, ponieważ czasami jest używany rozruch.

## <a name="dhcp-on-a-secondary-interface"></a>Protokół DHCP w interfejsie pomocniczym

Klient DHCP NetX może działać w interfejsach pomocniczych, a nie w domyślnym interfejsie podstawowym.

Aby uruchomić klienta DHCP NetX w pomocniczym interfejsie sieciowym, aplikacja hosta musi ustawić indeks interfejsu klienta DHCP na interfejs pomocniczy przy użyciu usługi *nx_dhcp_set_interface_index* API. Interfejs musi być już dołączony do podstawowego interfejsu sieciowego przy użyciu *nx_ip_interface_attach* usługi. Aby uzyskać więcej informacji na temat dołączania interfejsów pomocniczych, zobacz NetX User Guide (Podręcznik użytkownika netX).

Poniżej na rysunku 1.2 przedstawiono przykładowy system, w którym aplikacja hosta łączy się z serwerem DHCP w interfejsie pomocniczym. W wierszu 65 interfejs pomocniczy jest dołączany do zadania IP z pustym adresem IP. W wierszu 104 po utworzeniu wystąpienia klienta DHCP indeks interfejsu klienta DHCP jest ustawiany na wartość 1 (np. przesunięcie od interfejsu podstawowego, który sam jest indeksem 0), wywołując nx_dhcp_set_interface_index *.* Następnie klient DHCP jest gotowy do rozpoczęcia w wierszu 108.

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

Rysunek 1.2 Przykład protokołu DHCP dla netx z obsługą wielunadresowych

## <a name="dhcp-client-on-multiple-interfaces-simultaneously"></a>Klient DHCP na wielu interfejsach jednocześnie

Aby można było uruchomić klienta DHCP na wielu interfejsach, NX_MAX_PHYSICAL_INTERFACES w programie *nx_api.h* musi być ustawiona na liczbę interfejsów fizycznych podłączonych do urządzenia. Domyślnie ta wartość to 1 (np. interfejs podstawowy). Aby zarejestrować dodatkowy interfejs w wystąpieniu adresu IP, użyj *nx_ip_interface_attach* usługi. Aby uzyskać więcej informacji na temat dołączania interfejsów pomocniczych, zobacz NetX User Guide (Podręcznik użytkownika netX).

Następnym krokiem jest ustawienie dla NX_DHCP_CLIENT_MAX_RECORDS w programie *nx_dhcp.h* maksymalnej liczby interfejsów oczekiwanych do jednoczesnego uruchamiania protokołu DHCP. Należy pamiętać NX_DHCP_CLIENT_MAX_RECORDS że NX_MAX_PHYSICAL_INTERFACES nie musi być NX_MAX_PHYSICAL_INTERFACES. Na przykład NX_MAX_PHYSICAL_INTERFACES 3, a NX_DHCP_CLIENT_MAX_RECORDS równe 2. W tej konfiguracji tylko dwa interfejsy (i mogą być dowolnymi z trzech interfejsów fizycznych w dowolnym momencie) z trzech interfejsów fizycznych mogą uruchamiać protokół DHCP w dowolnym momencie. Rekordy klienta DHCP nie mają mapowania jeden do jednego do interfejsów sieciowych, np. Rekord klienta 1 nie jest automatycznie skorelowany z indeksem interfejsu fizycznego 1.

NX_DHCP_CLIENT_MAX_RECORDS można również ustawić na wartość większą niż NX_MAX_PHYSICAL_INTERFACES, ale będzie to tworzyć nieużywane rekordy klienta i być nieefektywnym użyciem pamięci.

Aby można było uruchomić protokół DHCP na dowolnym interfejsie, aplikacja musi włączyć te interfejsy, wywołując *nx_dhcp_interface_enable*. Należy pamiętać, że wyjątek jest interfejsem podstawowym, który jest automatycznie włączany w wywołaniu *nx_dhcp_create* (i który można wyłączyć przy użyciu usługi *nx_dhcp_interface_disable* omówiono poniżej).

W dowolnym momencie interfejs można wyłączyć dla protokołu DHCP lub DHCP można zatrzymać na tym interfejsie niezależnie od innych interfejsów z systemem DHCP.

Jak wspomniano powyżej, aby włączyć określony interfejs dla protokołu DHCP, użyj usługi *nx_dhcp_interface_enable* i określ indeks interfejsu fizycznego w argumentze wejściowym. Maksymalnie NX_DHCP_CLIENT_MAX_RECORDS można włączyć z jedynym ograniczeniem, że argument wejściowy indeksu interfejsu jest mniejszy niż NX_MAX_PHYSICAL_INTERFACES.

Aby uruchomić protokół DHCP na określonym interfejsie, użyj *nx_dhcp_interface_start* usługi. Aby uruchomić protokół DHCP we wszystkich włączonych interfejsach, użyj *nx_dhcp_start* usługi. (Interfejsy, które już uruchomiły protokół DHCP, nie będą mieć wpływu *nx_dhcp_start*).

Aby zatrzymać protokół DHCP na interfejsie, użyj *nx_dhcp_interface_stop* usługi. Protokół DHCP musi już zostać uruchomiony w tym interfejsie lub zostanie zwrócony stan błędu. Aby zatrzymać protokół DHCP na wszystkich włączonych interfejsach, użyj *nx_dhcp_stop* usługi. Protokół DHCP można w dowolnym momencie zatrzymać niezależnie od innych interfejsów.

Większość istniejących usług klienta DHCP ma odpowiednik "interfejsu", np. *nx_dhcp_interface_release* jest odpowiednikiem interfejsu *nx_dhcp_release.* Jeśli klient DHCP jest skonfigurowany dla jednego interfejsu, wykonują tę samą akcję.

Należy pamiętać, że usługi klienta DHCP inne niż specyficzne dla interfejsu zwykle mają zastosowanie do wszystkich interfejsów, ale nie wszystkich. W drugim przypadku usługa specyficzna dla interfejsu nie dotyczy pierwszego interfejsu z włączoną obsługą protokołu DHCP, który znajduje się w wyszukiwaniu listy rekordów interfejsu klienta DHCP. Zobacz **Opis usług w rozdziale** 3, aby dowiedzieć się, jak działa usługa nieopisywna dla interfejsu, gdy dla protokołu DHCP jest włączonych wiele interfejsów.

W poniższej przykładowej sekwencji wystąpienie adresu IP ma dwa interfejsy sieciowe i najpierw uruchamia protokół DHCP w interfejsie pomocniczym. W pewnym momencie protokół DHCP zostanie uruchomiony w interfejsie podstawowym. Następnie zwalnia adres IP w interfejsie podstawowym i ponownie uruchamia protokół DHCP w interfejsie podstawowym:

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

Aby uzyskać pełną listę usług specyficznych dla interfejsu, **zobacz Opis usług w** rozdziale 3.

## <a name="configuration-options"></a>Opcje konfiguracji

Konfigurowane przez użytkownika opcje DHCP w *pliku nx_dhcp.h* umożliwiają aplikacji hosta dostosowanie klienta DHCP do określonych wymagań. Poniżej znajduje się lista tych parametrów:  
  
- **NX_DHCP_ENABLE_BOOTP** Zdefiniowano, ta opcja włącza protokół BOOTP zamiast DHCP. Domyślnie ta opcja jest wyłączona.

- **NX_DHCP_CLIENT_RESTORE_STATE** Jeśli ta funkcja jest zdefiniowana, umożliwia klientowi DHCP zapisanie bieżącej "stanu" licencji klienta DHCP, w tym czasu pozostałego do dzierżawy, i przywrócenie tego stanu między ponownym uruchomieniem aplikacji klienckiej DHCP. Wartość domyślna jest wyłączona.

- **NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL** Jeśli to ustawienie zostanie ustawione, klient DHCP nie utworzy własnej puli pakietów. Aplikacja hosta musi używać usługi nx_dhcp_packet_pool_set, aby ustawić pulę pakietów klienta DHCP. Wartość domyślna jest wyłączona.

- **NX_DHCP_CLIENT_SEND_ARP_PROBE** Zdefiniowane, umożliwia klientowi DHCP wysyłanie sondy ARP po przypisaniu adresu IP w celu sprawdzenia, czy przypisany adres DHCP nie jest własnością innego hosta. Domyślnie ta opcja jest wyłączona.

- **NX_DHCP_ARP_PROBE_WAIT** Określa czas oczekiwania klienta DHCP na odpowiedź po wysłaniu sondy ARP. Wartość domyślna to jedna sekunda (1 * NX_IP_PERIODIC_RATE)

- **NX_DHCP_ARP_PROBE_MIN** Definiuje minimalną zmienność interwału między wysyłaniem sond ARP. Wartość domyślna to 1 sekunda.

- **NX_DHCP_ARP_PROBE_MAX** Definiuje maksymalną zmienność interwału między wysyłaniem sond ARP. Wartość domyślna to 2 sekundy.

- **NX_DHCP_ARP_PROBE_NUM** Definiuje liczbę sond ARP wysłanych w celu określenia, czy adres IP przypisany przez serwer DHCP jest już w użyciu. Wartość domyślna to 3 sondy.

- **NX_DHCP_RESTART_WAIT** Określa czas oczekiwania klienta DHCP na ponowne uruchomienie protokołu DHCP, jeśli adres IP przypisany do klienta DHCP jest już w użyciu. Wartość domyślna to 10 sekund.

- **NX_DHCP_CLIENT_MAX_RECORDS** Określa maksymalną liczbę rekordów interfejsu do zapisania w wystąpieniu klienta DHCP. Rekord interfejsu klienta DHCP jest rekordem klienta DHCP uruchomionego na określonym interfejsie. Wartość domyślna jest ustawiana jako liczba interfejsów fizycznych (NX_MAX_PHYSICAL_INTERFACES).

- **NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION** Zdefiniowane umożliwia klientowi DHCP wysyłanie opcji maksymalnego rozmiaru komunikatu DHCP. Domyślnie ta opcja jest wyłączona.

- **NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK** Zdefiniowane, umożliwia klientowi DHCP sprawdzanie nazwy hosta wejściowego w wywołaniu nx_dhcp_create nieprawidłowych znaków lub długości. Domyślnie ta opcja jest wyłączona.

- **NX_DHCP_THREAD_PRIORITY** Priorytet wątku DHCP. Domyślnie ta wartość określa, że wątek DHCP jest uruchamiany z priorytetem 3.

- **NX_DHCP_THREAD_STACK_SIZE** Rozmiar stosu wątku DHCP. Domyślnie rozmiar to 2048 bajtów.

- **NX_DHCP_TIME_INTERVAL** Interwał w sekundach po wykonaniu funkcji wygaśnięcia czasomierza klienta DHCP. Ta funkcja aktualizuje wszystkie limity czasu w procesie DHCP, np. jeśli komunikaty powinny być ponownie emitowane lub stan klienta DHCP został zmieniony. Domyślnie ta wartość to 1 sekunda.

- **NX_DHCP_OPTIONS_BUFFER_SIZE** Rozmiar buforu opcji DHCP. Domyślnie ta wartość to 312.

- **NX_DHCP_PACKET_PAYLOAD** Określa rozmiar w bajtach ładunku pakietu klienta DHCP. Wartość domyślna to NX_DHCP_MINIMUM_IP_DATAGRAM + rozmiar nagłówka fizycznego. Rozmiar nagłówka fizycznego w sieci przewodowej to zazwyczaj rozmiar ramki Ethernet.

- **NX_DHCP_PACKET_POOL_SIZE** Określa rozmiar puli pakietów klienta DHCP. Wartość domyślna to (5 *NX_DHCP_PACKET_PAYLOAD), która zapewnia cztery pakiety i miejsce na wewnętrzne obciążenie puli pakietów.

- **NX_DHCP_MIN_RETRANS_TIMEOUT** Określa minimalną opcję oczekiwania na odebranie komunikatu serwera DHCP na komunikat klienta przed jego ponownym przesłaniem. Wartość domyślna to zalecane 4 sekundy dla specyfikacji RFC 2131.

- **NX_DHCP_MAX_RETRANS_TIMEOUT** Określa maksymalną opcję oczekiwania na odebranie odpowiedzi serwera DHCP na komunikat klienta przed jego ponownym przesłaniem. Wartość domyślna to zalecane 64 sekundy dla specyfikacji RFC 2131.

- **NX_DHCP_MIN_RENEW_TIMEOUT** Określa minimalną opcję oczekiwania na odebranie komunikatu serwera DHCP i wysłanie żądania odnowienia po powiązyniu klienta DHCP z adresem IP. Wartość domyślna to 60 sekund. Klient DHCP używa jednak opcji Odnów i Pobinuj czas wygaśnięcia z komunikatu serwera DHCP przed ustawieniem wartości domyślnej minimalnego limitu czasu odnowienia.

- **NX_DHCP_TYPE_OF_SERVICE** Typ usługi wymagany dla żądań protokołu UDP protokołu DHCP. Domyślnie ta wartość jest definiowana jako NX_IP_NORMAL, aby wskazać normalną usługę pakietów IP.

- **NX_DHCP_FRAGMENT_OPTION** Włączanie fragmentu dla żądań protokołu UDP protokołu DHCP. Domyślnie ta wartość jest NX_DONT_FRAGMENT, aby wyłączyć fragmentowanie protokołu UDP protokołu DHCP.

- **NX_DHCP_TIME_TO_LIVE** Określa liczbę routerów, które pakiet może przekazać, zanim zostanie odrzucony. Wartość domyślna to 0x80.

- **NX_DHCP_QUEUE_DEPTH** Określa maksymalną głębokość kolejki odbierania. Wartość domyślna to 4.
