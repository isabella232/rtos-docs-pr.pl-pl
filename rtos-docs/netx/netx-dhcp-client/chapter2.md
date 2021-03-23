---
title: Rozdział 2 — Instalowanie i używanie klienta DHCP usługi Azure RTO NetX
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika klienta DHCP usługi Azure RTO NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9224a4df70b8199032066e30108250a3baeb65f5
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822704"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-dhcp-client"></a>Rozdział 2 — Instalowanie i używanie klienta DHCP usługi Azure RTO NetX

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika DHCP usługi Azure RTO NetX.

## <a name="product-distribution"></a>Dystrybucja produktu

Usługa DHCP dla NetX jest dostępna pod adresem [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) . Pakiet zawiera dwa pliki źródłowe i plik PDF, który zawiera ten dokument, w następujący sposób:

- **nx_dhcp. h** Plik nagłówka dla protokołu DHCP dla NetX

- **nx_dhcp. c** Plik źródłowy języka C dla usługi DHCP dla NetX

- **nx_dhcp.pdf** Opis pliku PDF protokołu DHCP dla usługi NetX

- **demo_netx_dhcp. c** Demonstracja usługi NetX DHCP

- **demo_netx_multihome_dhcp_client. c** NetX klienta DHCP — Demonstracja DHCP na wielu interfejsach

## <a name="dhcp-installation"></a>Instalacja DHCP

Aby można było używać protokołu DHCP do NetX, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX. Na przykład jeśli NetX jest zainstalowana w katalogu "*\threadx\arm7\green*", wówczas pliki *nx_dhcp. h* i *nx_dhcp. c* powinny zostać skopiowane do tego katalogu.

## <a name="using-dhcp"></a>Korzystanie z protokołu DHCP

Korzystanie z protokołu DHCP dla NetX jest proste. W zasadzie kod aplikacji musi zawierać *nx_dhcp. h* po zawiera *tx_api. h* i *nx_api. h*, aby użyć odpowiednio ThreadX i NetX. Po dołączeniu *nx_dhcp. h* kod aplikacji będzie następnie mógł określić wywołania funkcji DHCP w dalszej części tego przewodnika. Aplikacja musi również zawierać *nx_dhcp. c* w procesie kompilacji. Ten plik musi być skompilowany w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone wraz z plikami aplikacji. To wszystko, co jest wymagane do korzystania z protokołu DHCP NetX.

Należy pamiętać, że ponieważ protokół DHCP korzysta z usług NetX UDP, należy włączyć protokół UDP przy użyciu wywołania *nx_udp_enable* przed użyciem protokołu DHCP.

Aby uzyskać przypisany wcześniej adres IP, klient DHCP może zainicjować proces DHCP z komunikatem żądania i opcją 50 "żądany adres IP" na serwerze DHCP. Serwer DHCP odpowie komunikatem ACK, jeśli adres IP jest przydzielany klientowi lub NACK w przypadku odmowy. W tym drugim przypadku klient DHCP uruchamia ponownie proces DHCP w stanie init z komunikatem odnajdowania i nie ma żądanego adresu IP. Aplikacja hosta najpierw tworzy klienta DHCP, a następnie wywołuje usługę API *nx_dhcp_request_client_ip* , aby ustawić żądany adres IP przed rozpoczęciem procesu DHCP z *nx_dhcp_start*. Przykładowa aplikacja DHCP została udostępniona w innym miejscu w tym dokumencie, aby uzyskać więcej szczegółów.

## <a name="in-the-bound-state"></a>W stanie związanym

Gdy klient DHCP jest w stanie powiązanym, wątek klienta DHCP przetwarza stan klienta raz na interwał (określony przez NX_DHCP_TIME_INTERVAL) i zmniejsza pozostały czas w dzierżawie IP przypisanym do klienta. Po upływie czasu odnowienia stan klienta DHCP zostanie zaktualizowany do stanu ODNOWIENIa, gdy klient zażąda odnowienia z serwera DHCP.


## <a name="sending-dhcp-messages-to-the-server"></a>Wysyłanie komunikatów DHCP do serwera

Klient DHCP ma usługi interfejsu API, które umożliwiają aplikacji hosta wysyłanie komunikatów do serwera DHCP. Zwróć uwagę, że te usługi nie są przeznaczone dla aplikacji hosta, aby ręcznie uruchomić protokół klienta DHCP, ponieważ przede wszystkim wysyła komunikat bez konieczności aktualizowania stanu wewnętrznego klienta DHCP.

  - *nx_dhcp_release*: wysyła komunikat o zwolnieniu do serwera, gdy aplikacja hosta opuszcza sieć lub potrzebuje jej adresu IP.

  - *nx_dhcp_decline*: wysyła komunikat o odrzuceniu do serwera, jeśli aplikacja hosta określi niezależnie od klienta DHCP, że jego adres IP jest już używany.

  - *nx_dhcp_forcerenew*: wysyła komunikat Forcerenew do serwera

  - *nx_dhcp_send_request*: przyjmuje jako argument typ komunikatu DHCP określony w *nx_dhcp. h* i wysyła komunikat do serwera. Jest to przeznaczone głównie do wysyłania komunikatu o błędzie protokołu DHCP.

Aby uzyskać więcej informacji na temat tych usług w innym miejscu w tym dokumencie, zobacz "*Opis usług DHCP*".

## <a name="starting-and-stopping-the-dhcp-client"></a>Uruchamianie i zatrzymywanie klienta DHCP

Aby zatrzymać klienta DHCP, niezależnie od tego, czy osiągnie on stan związany, aplikacja hosta wywołuje *nx_dhcp_stop*.

Aby ponownie uruchomić klienta DHCP, aplikacja hosta musi najpierw zatrzymać klienta DHCP przy użyciu usługi *nx_dhcp_stop* opisanej powyżej. Następnie host może wywoływać *nx_dhcp_start* , aby wznowić działanie klienta DHCP. Jeśli aplikacja hosta chce wyczyścić poprzedni profil klienta DHCP, na przykład jeden uzyskany przez poprzedni serwer DHCP w innej sieci, aplikacja hosta powinna wywołać *nx_dhcp_reinitialize* , aby wykonać to zadanie wewnętrznie przed wywołaniem nx_dhcp_start.

Typową sekwencją może być:

```C
nx_dhcp_stop(&my_dhcp);

nx_dhcp_reinitialize(&my_dhcp);

nx_dhcp_start(&my_dhcp);
```

W przypadku aplikacji DHCP uruchamianych tylko na jednym interfejsie DHCP zatrzymanie klienta DHCP powoduje także dezaktywację czasomierza klienta DHCP. W rezultacie nie jest już śledzony czas pozostały w dzierżawie IP. Zatrzymanie klienta DHCP w określonym interfejsie nie spowoduje dezaktywacji czasomierza klienta DHCP, ale spowoduje zatrzymanie aktualizacji czasomierza do czasu pozostałej w dzierżawie IP w tym interfejsie.

W związku z tym zatrzymanie klienta DHCP nie jest zalecane, chyba że aplikacja hosta wymaga ponownego uruchomienia lub przełączenia sieci.

## <a name="using-the-dhcp-client-with-auto-ip"></a>Korzystanie z klienta DHCP z opcją AutoIP

Klient DHCP NetX działa równolegle z protokołem AutoIP w aplikacjach, w których DHCP i AutoIP gwarantują adres, w którym serwer DHCP nie ma gwarancji, że jest dostępny lub nie odpowiada. Jeśli jednak host nie może wykryć serwera lub uzyskać przypisanego adresu IP, może przełączyć się do protokołu automatyczne IP dla lokalnego adresu IP. Jednak przed wykonaniem tej czynności zaleca się tymczasowe zatrzymanie klienta DHCP w ramach etapów "sondy" i "Obrona". Po przypisaniu automatycznie adresu IP do hosta klient DHCP może zostać ponownie uruchomiony, a jeśli serwer DHCP stanie się dostępny, adres IP hosta może akceptować adres IP oferowany przez serwer DHCP, gdy aplikacja jest uruchomiona.

NetX automatycznie IP ma powiadomienie o zmianie adresu dla hosta, aby monitorować jego działania w przypadku zmiany adresu IP.

## <a name="small-example-system"></a>Mały przykładowy system

Przykład sposobu użycia NetX został opisany na rysunku 1,1 poniżej. Klient DHCP jest tworzony "*my_thread_entry*" w wierszu 101. Po pomyślnym utworzeniu proces DHCP zostanie zainicjowany przy wywołaniu *nx_dhcp_start* w wierszu 108. W tym momencie próby klienta DHCP są inicjowane w celu skontaktowania się z serwerem DHCP. W trakcie tego procesu kod aplikacji czeka na zarejestrowanie prawidłowego adresu IP w wystąpieniu IP przy użyciu usługi *nx_ip_status_check* (lub *nx_ip_interface_status_check* dla interfejsu pomocniczego), zaczynając od wiersza 95. Jest to bardziej często wykonywane w pętli z krótszą opcją oczekiwania.

Po wierszu 127 usługa DHCP odebrała prawidłowy adres IP, a następnie może działać, wykorzystując NetX usługi TCP/IP.

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

Rysunek 1,1 przykład użycia protokołu DHCP z NetX

## <a name="multi-server-environments"></a>Środowiska z obsługą wielu serwerów

W sieciach, w których istnieje więcej niż jeden serwer DHCP, klient DHCP akceptuje pierwszy odebrany komunikat oferty serwera DHCP, postępuje zgodnie ze stanem żądania i ignoruje wszelkie inne odebrane oferty.

## <a name="arp-probes"></a>Sondy protokołu ARP

Klienta DHCP można skonfigurować tak, aby wysyłał co najmniej jedną sondę protokołu ARP po przypisaniu adresu IP z serwera DHCP w celu sprawdzenia, czy adres IP nie jest jeszcze używany. Krok sondowania ARP jest zalecany przez RFC 2131 i jest szczególnie istotny w środowiskach z więcej niż jednym serwerem DHCP. Jeśli aplikacja hosta włącza opcję NX_DHCP_CLIENT_SEND_ARP_PROBE (zobacz **Opcje konfiguracji** w rozdziale dwa w przypadku dodatkowych opcji sondowania ARP), klient DHCP wyśle sondę ARP "z własnymi żądaniami" i poczeka przez określony czas na odpowiedź. Jeśli żaden nie zostanie odebrany, klient DHCP postępuje ze stanem związanym. W przypadku odebrania odpowiedzi klient DHCP zakłada, że adres jest już używany. Automatycznie wysyła komunikat odrzucania do serwera i ponownie inicjuje klienta, aby ponownie uruchomić sondy DHCP ze stanu INIT. Spowoduje to ponowne uruchomienie komputera stanu DHCP, a klient wysyła do serwera inny komunikat ODNAJDOWAnia.

## <a name="bootp-protocol"></a>Protokół BOOTP

Klient DHCP obsługuje również protokół BOOTP. Aby włączyć tę opcję i użyć protokołu BOOTP zamiast DHCP, aplikacja hosta musi ustawić opcję konfiguracji NX_DHCP_BOOTP_ENABLE. Aplikacja hosta może nadal żądać określonych adresów IP w protokole BOOTP. Klient DHCP nie obsługuje jednak ładowania systemu operacyjnego hosta, ponieważ protokół BOOTP jest czasami używany do wykonania.

## <a name="dhcp-on-a-secondary-interface"></a>Protokół DHCP w interfejsie pomocniczym

Klienta DHCP NetX można uruchomić na interfejsach pomocniczych, a nie w domyślnym interfejsie głównym.

Aby uruchomić NetX klienta DHCP w dodatkowym interfejsie sieciowym, aplikacja hosta musi ustawić indeks interfejsu klienta DHCP na pomocniczy interfejs przy użyciu usługi interfejsu API *nx_dhcp_set_interface_index* . Interfejs musi być już dołączony do podstawowego interfejsu sieciowego przy użyciu usługi *nx_ip_interface_attach* . Więcej informacji na temat dołączania interfejsów pomocniczych można znaleźć w podręczniku użytkownika NetX.

1,2 poniżej przedstawiono przykładowy system, w którym aplikacja hosta nawiązuje połączenie z serwerem DHCP w interfejsie pomocniczym. W wierszu 65 pomocniczy interfejs jest dołączany do zadania IP z adresem IP o wartości null. W wierszu 104 po utworzeniu wystąpienia klienta DHCP indeks interfejsu klienta DHCP jest ustawiony na 1 (np. przesunięcie od podstawowego interfejsu, który sam jest indeksem 0) przez wywołanie *nx_dhcp_set_interface_index*. Następnie klient DHCP jest gotowy do uruchomienia w wierszu 108.

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

Rysunek 1,2 przykład protokołu DHCP dla NetX z obsługą wielostrony

## <a name="dhcp-client-on-multiple-interfaces-simultaneously"></a>Klient DHCP w wielu interfejsach jednocześnie

Aby uruchomić klienta DHCP na wielu interfejsach, NX_MAX_PHYSICAL_INTERFACES w *nx_api. h* musi być ustawiona na liczbę fizycznych interfejsów podłączonych do urządzenia. Domyślnie ta wartość jest równa 1 (np. podstawowy interfejs). Aby zarejestrować dodatkowy interfejs w wystąpieniu protokołu IP, Użyj usługi *nx_ip_interface_attach* . Więcej informacji na temat dołączania interfejsów pomocniczych można znaleźć w podręczniku użytkownika NetX.

Następnym krokiem jest ustawienie NX_DHCP_CLIENT_MAX_RECORDS w *nx_dhcp. h* na maksymalną liczbę interfejsów oczekiwanych na równoczesne uruchomienie protokołu DHCP. Należy pamiętać, że NX_DHCP_CLIENT_MAX_RECORDS nie muszą być równe NX_MAX_PHYSICAL_INTERFACES. Na przykład NX_MAX_PHYSICAL_INTERFACES może mieć wartość 3 i NX_DHCP_CLIENT_MAX_RECORDS równe 2. W tej konfiguracji tylko dwa interfejsy (i mogą być dowolne dwa z trzech interfejsów fizycznych w dowolnym momencie) spośród trzech interfejsów fizycznych można w dowolnym momencie uruchomić usługę DHCP. Rekordy klienta DHCP nie mają mapowania jeden do jednego do interfejsów sieciowych, np. rekord klienta 1 nie jest automatycznie skorelowany z indeksem interfejsu fizycznego 1.

NX_DHCP_CLIENT_MAX_RECORDS można również ustawić na wartość większą niż NX_MAX_PHYSICAL_INTERFACES, ale spowoduje to utworzenie nieużywanych rekordów klienta i niewydajne użycie pamięci.

Aby można było uruchomić protokół DHCP w dowolnym interfejsie, aplikacja musi włączyć te interfejsy, wywołując *nx_dhcp_interface_enable*. Należy zauważyć, że wyjątek jest interfejsem podstawowym, który jest automatycznie włączany w wywołaniu *nx_dhcp_create* (i które można wyłączyć za pomocą usługi *nx_dhcp_interface_disable* opisanej poniżej).

W dowolnym momencie można wyłączyć interfejs DHCP lub można zatrzymać protokół DHCP niezależnie od innych interfejsów z uruchomionym protokołem DHCP.

Jak wspomniano powyżej, aby włączyć określony interfejs dla usługi DHCP, należy użyć usługi *nx_dhcp_interface_enable* i określić indeks interfejsu fizycznego w argumencie wejściowym. Można włączyć do NX_DHCP_CLIENT_MAX_RECORDS interfejsów z jedynym ograniczeniem, że argument wejściowy indeksu interfejsu jest krótszy niż NX_MAX_PHYSICAL_INTERFACES.

Aby uruchomić protokół DHCP w określonym interfejsie, Użyj usługi *nx_dhcp_interface_start* . Aby uruchomić protokół DHCP we wszystkich włączonych interfejsach, Użyj usługi *nx_dhcp_start* . (Interfejsy, które już uruchomiły protokół DHCP, nie będą miały wpływ na *nx_dhcp_start*).

Aby zatrzymać usługę DHCP w interfejsie, Użyj usługi *nx_dhcp_interface_stop* . Protokół DHCP musi już być uruchomiony w tym interfejsie lub zwracany jest stan błędu. Aby zatrzymać protokół DHCP we wszystkich włączonych interfejsach, Użyj usługi *nx_dhcp_stop* . Protokół DHCP można zatrzymać niezależnie od innych interfejsów w dowolnym momencie.

Większość istniejących usług klienta DHCP ma odpowiednik "Interface", np. *nx_dhcp_interface_release* jest odpowiednikiem określonego interfejsu *nx_dhcp_release.* Jeśli klient DHCP jest skonfigurowany dla jednego interfejsu, wykonuje tę samą akcję.

Należy pamiętać, że usługi klienta DHCP niezwiązane z interfejsem zwykle mają zastosowanie do wszystkich interfejsów, ale nie wszystkich. W tym drugim przypadku usługa niezależna od interfejsu dotyczy pierwszego interfejsu z włączonym protokołem DHCP, który znajduje się w przeszukiwaniu listy klientów DHCP. Zobacz **Opis usług** w rozdziale trzeci, w jaki sposób usługa niezależna od interfejsu jest wykonywana w przypadku włączenia wielu interfejsów dla protokołu DHCP.

W przykładowej sekwencji poniżej wystąpienie protokołu IP ma dwa interfejsy sieciowe i najpierw uruchamia DHCP w interfejsie pomocniczym. W pewnym momencie później zostanie uruchomiony protokół DHCP w interfejsie podstawowym. Następnie zwalnia adres IP w interfejsie podstawowym i ponownie uruchamia DHCP w interfejsie głównym:

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

Aby uzyskać pełną listę specyficznych dla interfejsu usług, zobacz **Opis usług** w rozdziale 3.

## <a name="configuration-options"></a>Opcje konfiguracji

Użytkownik konfigurowalny opcje DHCP w *nx_dhcp. h* zezwala aplikacji hosta na precyzyjne dopasowanie klienta DHCP do określonych wymagań. Poniżej znajduje się lista tych parametrów:  
  
- **NX_DHCP_ENABLE_BOOTP** Zdefiniowana, ta opcja włącza protokół BOOTP zamiast DHCP. Domyślnie ta opcja jest wyłączona.

- **NX_DHCP_CLIENT_RESTORE_STATE** Jeśli ta wartość jest zdefiniowana, umożliwia klientowi DHCP zapisanie bieżącej licencji klienta DHCP, w tym czasu pozostałej w dzierżawie, i przywrócenie tego stanu między ponownymi uruchomieniami aplikacji klienta DHCP. Wartość domyślna jest wyłączona.

- **NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL** W przypadku wybrania tej opcji klient DHCP nie będzie tworzyć własnej puli pakietów. Aplikacja hosta musi używać usługi nx_dhcp_packet_pool_set, aby ustawić pulę pakietów klienta DHCP. Wartość domyślna jest wyłączona.

- **NX_DHCP_CLIENT_SEND_ARP_PROBE** Zdefiniowane, umożliwia klientowi DHCP wysyłanie sondy ARP po przypisaniu adresów IP w celu sprawdzenia, czy przypisany adres DHCP nie jest własnością innego hosta. Domyślnie ta opcja jest wyłączona.

- **NX_DHCP_ARP_PROBE_WAIT** Określa czas oczekiwania przez klienta DHCP na odpowiedź po wysłaniu sondy ARP. Wartość domyślna to jedna sekunda (1 * NX_IP_PERIODIC_RATE)

- **NX_DHCP_ARP_PROBE_MIN** Określa minimalną zmianę interwału między wysłaniem sond protokołu ARP. Wartość jest domyślnie równa 1 sekunda.

- **NX_DHCP_ARP_PROBE_MAX** Definiuje maksymalną zmianę interwału między wysłaniem sond ARP. Wartość jest domyślnie równa 2 sekund.

- **NX_DHCP_ARP_PROBE_NUM** Określa liczbę sond protokołu ARP wysyłanych do określenia, czy adres IP przypisany przez serwer DHCP jest już używany. Wartość jest domyślnie równa 3 sondy.

- **NX_DHCP_RESTART_WAIT** Określa czas, przez który klient DHCP może ponownie uruchomić usługę DHCP, jeśli adres IP przypisany do klienta DHCP jest już używany. Wartość jest domyślnie równa 10 sekund.

- **NX_DHCP_CLIENT_MAX_RECORDS** Określa maksymalną liczbę rekordów interfejsów do zapisania w wystąpieniu klienta DHCP. Rekord interfejsu klienta DHCP jest rekordem klienta DHCP działającego w określonym interfejsie. Wartość domyślna jest ustawiana jako liczba interfejsów fizycznych (NX_MAX_PHYSICAL_INTERFACES).

- **NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION** Zdefiniowane, dzięki temu Klient DHCP może wysyłać maksymalny rozmiar komunikatu DHCP. Domyślnie ta opcja jest wyłączona.

- **NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK** Zdefiniowane, umożliwia klientowi DHCP sprawdzenie nazwy wejściowego hosta w wywołaniu nx_dhcp_create w przypadku nieprawidłowych znaków lub długości. Domyślnie ta opcja jest wyłączona.

- **NX_DHCP_THREAD_PRIORITY** Priorytet wątku DHCP. Domyślnie ta wartość określa, że wątek DHCP działa z priorytetem 3.

- **NX_DHCP_THREAD_STACK_SIZE** Rozmiar stosu wątków DHCP. Domyślnie rozmiar to 2048 bajtów.

- **NX_DHCP_TIME_INTERVAL** Interwał (w sekundach), po którym jest wykonywana funkcja wygaśnięcia czasomierza klienta DHCP. Ta funkcja aktualizuje wszystkie limity czasu w procesie DHCP, np. w przypadku, gdy komunikaty powinny być ponownie przesyłane lub stan klienta DHCP uległy zmianie. Domyślnie ta wartość jest równa 1 sekunda.

- **NX_DHCP_OPTIONS_BUFFER_SIZE** Rozmiar buforu opcji DHCP. Wartość domyślna to 312.

- **NX_DHCP_PACKET_PAYLOAD** Określa rozmiar w bajtach ładunku pakietu klienta DHCP. Wartość domyślna to NX_DHCP_MINIMUM_IP_DATAGRAM + rozmiar nagłówka fizycznego. Rozmiar nagłówka fizycznego w sieci wireline jest zwykle rozmiarem ramki sieci Ethernet.

- **NX_DHCP_PACKET_POOL_SIZE** Określa rozmiar puli pakietów klienta DHCP. Wartość domyślna to (5 * NX_DHCP_PACKET_PAYLOAD), która zapewni cztery pakiety Plus pomieszczenie dla obciążenia wewnętrznej puli pakietów.

- **NX_DHCP_MIN_RETRANS_TIMEOUT** Określa minimalną opcję oczekiwania na odebranie odpowiedzi serwera DHCP na komunikat klienta przed ponownym przesłaniem wiadomości. Wartość domyślna to RFC 2131 zalecane 4 sekundy.

- **NX_DHCP_MAX_RETRANS_TIMEOUT** Określa maksymalną opcję oczekiwania na odebranie odpowiedzi serwera DHCP na komunikat klienta przed ponownym przesłaniem wiadomości. Wartość domyślna to RFC 2131 zalecane 64 s.

- **NX_DHCP_MIN_RENEW_TIMEOUT** Określa minimalną opcję oczekiwania na odebranie komunikatu serwera DHCP i wysłanie żądania odnowienia po powiązaniu klienta DHCP z adresem IP. Wartość domyślna to 60 sekund. Jednak klient DHCP używa odnawiania i ponownego powiązania czasu wygaśnięcia z komunikatów serwera DHCP przed ustawieniem minimalny limit czasu odnawiania.

- **NX_DHCP_TYPE_OF_SERVICE** Typ usługi wymaganej przez żądania UDP protokołu DHCP. Domyślnie ta wartość jest definiowana jako NX_IP_NORMAL w celu wskazania normalnej usługi pakietów IP.

- **NX_DHCP_FRAGMENT_OPTION** Włączono fragment dla żądań UDP protokołu DHCP. Domyślnie ta wartość jest NX_DONT_FRAGMENT, aby wyłączyć fragmentację protokołu UDP protokołu DHCP.

- **NX_DHCP_TIME_TO_LIVE** Określa liczbę routerów, które ten pakiet może przekazać, zanim zostanie odrzucony. Wartość domyślna to 0x80.

- **NX_DHCP_QUEUE_DEPTH** Określa maksymalną głębokość kolejki odbioru. Wartość domyślna to 4.
