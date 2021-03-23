---
title: Rozdział 2 — Instalowanie i używanie klienta DHCPv6 usługi Azure RTO NetX Duo
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika klienta DHCPv6 platformy Azure RTO NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a154dbeb91b46a2c8bd5f4585e168a6b62d042ff
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821997"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-dhcpv6-client"></a>Rozdział 2 — Instalowanie i używanie klienta DHCPv6 usługi Azure RTO NetX Duo

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika klienta DHCPv6 platformy Azure RTO NetX Duo.

## <a name="product-distribution"></a>Dystrybucja produktu

Klient DHCPv6 NetX Duo jest dostępny pod adresem [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Pakiet zawiera dwa pliki źródłowe i plik PDF, który zawiera ten dokument, w następujący sposób:

- **nxd_dhcpv6_client. h** Plik nagłówka dla klienta NetX DuoDHCPv6

- **nxd_dhcpv6_client. c** Plik kodu źródłowego dla klienta DHCPv6 NetX Duo

- **demo_netxduo_dhcpv6_client. c** Przykładowy program demonstrujący konfigurację klienta DHCPv6 NetX Duo

- **nxd_dhcpv6_client.pdf** Opis pliku PDF klienta DHCPv6 NetX Duo

## <a name="netx-duo-dhcpv6-client-installation"></a>Instalacja klienta DHCPv6 NetX Duo

Aby użyć interfejsu API klienta protokołu DHCPv6 NetX Duo, cała wymieniona wyżej dystrybucja może zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX Duo. Na przykład jeśli NetX Duo jest zainstalowana w katalogu "*\threadx\arm7\green*", wówczas pliki *nxd_dhcpv6_client. h* i *nxd_dhpcv6_client. c* można skopiować do tego katalogu.

## <a name="using-the-netx-duo-dhcpv6-client"></a>Korzystanie z klienta DHCPv6 NetX Duo

Kod aplikacji musi zawierać *nxd_dhcpv6_client. h* , który zawiera *tx_api. h* i *nx_api. h*, aby używać odpowiednio usług klienta DHCPv6, ThreadX i NetX Duo. *nxd_dhcpv6_client. c* musi być skompilowany w projekcie w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone wraz z plikami aplikacji.

### <a name="span-classunderlineclient-dhcp-unique-identifier-duidspan"></a><span class="underline">Unikatowy identyfikator DHCP klienta (DUID)</span>

Identyfikator DUID klienta jednoznacznie definiuje każdego klienta w sieci. Aplikacja musi utworzyć identyfikator DUID klienta przed zażądaniem adresu IPv6 z serwera. Identyfikator DUID klienta jest automatycznie uwzględniany we wszystkich komunikatach na serwerze. Aby utworzyć identyfikator DUID, aplikacja wywołuje *nx_dhcpv6_create_client_duid usługi:*
```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT duid_type, 
                                  UINT hardware_type, ULONG time);
```

Aplikacja wywołuje tę usługę i określa Typ identyfikatora DUID (tylko warstwy linku lub warstwy linku + Time). W przypadku warstwy linku i DUIDs czasu ta usługa zapewni pole czasu, jeśli nie określono czasu wejścia.

W przypadku urządzeń, które są ponownie uruchamiane i chcą korzystać z wcześniej przypisanej dzierżawy adresów IPv6, aplikacja musi utworzyć identyfikator DUID klienta jako ten, który został użyty podczas przypisywania adresu IPv6. Adres warstwy linku jest wymagany do utworzenia identyfikatora DUID klienta warstwy linku. Nie wymaga to wcześniejszego magazynu pamięci nietrwałej, jeśli urządzenie ma dostęp do adresu warstwy linku. W przypadku DUIDs typu Time aplikacja musi mieć dostęp do tych samych danych czasu, które są używane podczas poprzedniego tworzenia identyfikatora DUID, co wymaga nietrwałej pamięci. Klienci, którzy nie mają żadnego stabilnego magazynu, nie mogą używać DUIDs typu Time.

### <a name="span-classunderlineclient-identity-association-for-non-temporary-addresses-ianaspan"></a><span class="underline">Skojarzenie tożsamości klienta dla adresów innych niż tymczasowe (IANA)</span>

Aplikacja musi utworzyć organizację IANA i opcjonalnie jeden lub więcej adresów IA przed zażądaniem adresu IPv6. W tym celu aplikacja wywoła usługę *nx_dhcpv6_create_client_iana* . Aby utworzyć opcję adresu IA, aplikacja wywołuje usługę *nx_dhcpv6_add_client_ia* z żądanym adresem IPv6 i wartością okresu istnienia jako wskazówką do serwera.

Organizacja IANA i jej MSR łącznie definiują parametry przypisywania adresów IPv6 klienta:

Przed uruchomieniem klienta DHCPv6 aplikacja kliencka DHCPv6 tworzy organizację IANA przy użyciu usługi *nx_dhcpv6_create_client_iana* :

```C
UINT    nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                     UINT IA_ident, ULONG T1, ULONG T2);
```

Przed uruchomieniem klienta DHCPv6 należy utworzyć co najmniej jeden serwer IAs przy użyciu usługi *nx_dhcpv6_create_client_ia* i żądanych adresów IPv6.

```C
UINT    nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                                NXD_ADDRESS *ipv6_address, 
                                ULONG preferred_lifetime, 
                                ULONG valid_lifetime);
```

> [!NOTE]
> Liczba adresów IA tworzonych przez aplikację nie może przekroczyć NX_DHCPV6_MAX_IA_ADDRESS parametru, którego wartość domyślna to 1.

Klient DHCPv6 NetX Duo obsługuje *nx_dhcpv6_create_client_ia* dla starszych aplikacji klienckich protokołu DHCPv6 i który jest identyczny z *nx_dhcpv6_add_client_ia* , ale deweloperzy są zachęcani do korzystania z usługi *nx_dhcpv6_add_client_ia* .

Te usługi zostały przedstawione w "małym przykładowym systemie" w innym miejscu w tym rozdziale.

### <a name="span-classunderlinenon-volatile-memory-considerations-to-reuse-ianas-and-iasspan"></a><span class="underline">Nielotne zagadnienia dotyczące ponownego użycia organizacji IANA i IAs</span>

Aplikacja musi zapisać parametry organizacji T1, T2 i IANA w nieulotnej pamięci, jeśli chcą używać tych samych adresów przy ponownym uruchomieniu. Aplikacja musi również zapisać swoją IA, która uwzględnia adres IPv6 w pamięci nieulotnej.

W przypadku zamknięcia aplikacji należy również przechować czas, który upłynął od przypisanych do nich dzierżaw adresów IPv6 do pamięci nieulotnej. Robi to przez wywołanie usługi *nx_dhcpv6_get_time_accrued* przed zatrzymaniem klienta DHCPv6.

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, 
                                ULONG *time_accrued);
```

Przy założeniu, że aplikacja ma niezależny zegar do śledzenia przedziału czasu, od momentu zatrzymania i ponownego uruchomienia klienta DHCPv6 po ponownym uruchomieniu, zostaje dodany do tego czasu, który upłynął do czasu naliczania dzierżawy IPv6 przed zatrzymaniem. Teraz uruchamia zadanie wątku klienta z łącznym czasem, który upłynął, w ramach dzierżawy IPv6, jako nv_time dane wejściowe poniżej:

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr, ULONG nv_time);
```

Od tego momentu zadanie wątku klienta DHCPv6 przejdzie do monitorowania czasu naliczonego przez dzierżawę IPv6 w przypadku odnowienia dzierżawy.

### <a name="span-classunderlinesetting-dhcpv6-option-dataspan"></a><span class="underline">Ustawianie danych opcji protokołu DHCPv6</span>

Przed zażądaniem dzierżawy IPv6 aplikacja może zażądać innych danych parametrów sieciowych, takich jak serwer DNS i serwer czasu. Niektóre z tych parametrów mają określone usługi. Poniżej przedstawiono kilka poniżej:

```C
UINT  nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT enable)

UINT  nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr, 
                                           UINT enable);
```

### <a name="span-classunderlineinitiating-the-ipv6-address-requestspan"></a><span class="underline">Inicjowanie żądania adresu IPv6</span>

Aplikacja uruchamia wątek klienta DHCPv6 przez wywołanie usługi *nx_dhcpv6_start* z danymi wejściowymi o zerowej godzinie. Aby zainicjować protokół DHCPv6 w celu zażądania adresu IPv6, aplikacja wywołuje *nx_dhcpv6_request_solicit.*

Jeśli aplikacja chce użyć przypisanej wcześniej dzierżawy IPv6, wywołuje *nx_dhcpv6_start* z niezerowym wejściem w czasie. Nie należy wywoływać *nx_dhcpv6_request_solicit*.

Następnie aplikacja nie musi nic więcej i klient DHCPv6 będzie automatycznie monitorować czas odnowienia lub ponownego powiązania adresu IPv6.

## <a name="small-example-system"></a>Mały przykładowy system

Przykładem łatwego użycia klienta DHCPv6 NetX Duo jest opisana w małym przykładzie poniżej przy użyciu klienta DHCPv6 i wirtualnego sterownika "RAM". W tej wersji demonstracyjnej założono, że urządzenie ma tylko jeden fizyczny interfejs sieciowy.

*tx_application_define* tworzy pulę pakietów dla klienta DHCPv6 do wysyłania komunikatów DHCPv6. Tworzy również wątek aplikacji i wystąpienie IP. Następnie włącza protokół UDP i ICMP na adresie IP w wierszach 130-148. Następnie klient DHCPv6 zostanie utworzony przy użyciu funkcji wywołania zwrotnego stanu (*dhcpv6_state_change_notify* ) i błędu serwera (*dhcpv6_server_error_handler*) w line151.

W funkcji wpis wątku klienta *thread_client_entry*, adres IP klienta jest ustawiany z adresem lokalnym linku i włączony dla usług IPv6 i ICMPv6 w wierszach 202-217. Przed uruchomieniem klienta DHCPv6 aplikacja tworzy identyfikator DUID klienta, opcję IANA i opcję adresu IA na lines219-303. Opcja adres IA jest opcjonalna, jeśli klient chce zażądać adresu IPv6 oraz prawidłowych i preferowanych okresów istnienia z serwera. Serwer może lub nie przydzielić żądanych adresów IPv6 lub czasu dzierżawy. Aplikacja może dodać więcej opcji IA (do NX_DHCPV6_MAX_IA_ADDRESS), aby przypisać wiele adresów globalnych.

Na koniec aplikacja ustawia różne opcje, aby zażądać parametrów sieci w swoich komunikatach do serwera DHCPv6. Zadanie klienta DHCPv6 jest uruchamiane przez wywołanie *nx_dhcpv6_start* w line306, a rzeczywisty protokół DHCPv6 jest uruchamiany w stanie żądanie z wywołaniem do *nx_dhcpv6_request_solicit* w wierszu 317. Klient DHCPv6 automatycznie obsługuje promocję stanu klienta za pomocą protokołu DHCPv6, dopóki nie zostanie on powiązany z adresem lub wystąpi błąd. W tym czasie aplikacja czeka na zakończenie tego protokołu, a także wykrywanie zduplikowanego adresu (tata), aby zakończyć, jeśli wystąpienie adresu IP jest skonfigurowane dla DAD (jest to konfiguracja domyślna).

Po wywołaniu tx_thread_sleep aplikacja sprawdza parametry globalne ustawione w wywołaniu zmiany stanu, aby określić powodzenie zadania klienta DHCPv6 do przydzielenia dzierżawy IPv6, a jeśli tak, to w przypadku zaistnienia nieprawidłowej kontroli. Odbywa się to przy użyciu liczników skonfigurowanych w funkcjach wywołania zwrotne zmiany stanu i błąd serwera. Aplikacja sonduje dla niezerowych liczników address_not_assigned, address_expired i server_errors dla przypisywania adresów zakończonych niepowodzeniem. Jeśli liczba bound_addresses jest różna od zera (co najmniej jeden adres został pomyślnie przypisany), sprawdza, czy nie ma address_failed_dad niezerowego dla niepowodzenia. Wyjaśnienie zmiany stanu i wywołania zwrotnego błędów serwera:

Wywołanie zwrotne zmiany stanu, *dhcpv6_state_change_notify*, poprzedni i bieżący stan klienta DHCPv6 aby określić, czy klient otrzymał prawidłowe odpowiedzi serwera:

  - *dhcpv6_state_change_notify* sprawdza przejścia bezpośrednio z żądania do init, a więc zwiększa licznik dla klienta DHCPv6 nie otrzymuje odpowiedzi z serwera.

Następna *dhcpv6_state_change_notify* sprawdza, czy klient został przypisany (powiązany) do co najmniej jednego adresu IPv6:

  - Jeśli nowy stan jest powiązany, zwiększa on licznik adresów powiązanych z klientem.
    
*Dhcpv6_state_change_notify* sprawdza także, czy nie zakończyło się niepowodzeniem:

  - W przypadku przejścia stanu z odrzucania do INICJACJi klient DHCPv6 nie zakończył niepowodzenia sprawdzenia na jednym z przypisanych adresów i zwiększa liczbę przypisań adresów zakończonych niepowodzeniem.
    
Ostatnim sprawdzaniem przez *dhcpv6_state_change_notify* w tym przykładzie jest dla pomyślnie przypisanego adresu, który przeszedł do niepowodzenia odnowienia lub ponownego powiązania niepowodzeniem:

  - Jeśli stan zmieni się z rebind na INIT, klient nie otrzymał żadnych odpowiedzi na żądania ODNOWIENIa lub ponownego powiązania, a *dhcpv6_state_change_notify* zwiększa liczbę wygasłych adresów.

*Dhcpv6_server_error_handler* w przypadku powiadomienia przez zadanie klienta DHCPv6 o stanie błędu otrzymanego z serwera zwiększa liczbę błędów serwera.

Przy założeniu, że wszystko przebiega prawidłowo, aplikacja wysyła zapytanie do klienta DHCPv6 o dane adresowe, w tym czasy dzierżawy. Pobiera liczbę prawidłowych adresów (przypisanych pomyślnie) przez wywołanie usługi *nx_dhcpv6_get_valid_ip_address_count* i czasu odnowienia w organizacji IANA (dotyczy wszystkich przypisanych adresów IA) przez wywołanie *nx_dhcpv6_get_iana_lease_time* w wierszach 372-392. Następnie wysyła zapytanie do klienta DHCPv6 dla każdej z opcji IA dla adresów IPv6 i czas dzierżawy według indeksu adresu.

Niektóre usługi klienta DHCPv6 (*nx_dhcpv6_get_lease_time_data, nx_dhcpv6_get_IP_address*) nie wymagają indeksu adresu jako danych wejściowych i zwracają parametry protokołu DHCPv6 dla globalnego adresu klienta. Jest to odpowiednie dla klientów z jednym globalnym adresem IPv6, gdy wywołuje *nx_dhcpv6_get_valid_ip_address_lease_time* w wierszu 384.

Konfiguracja klienta DHCPv6 NX_DHCPV6_CLIENT_RESTORE_STATE, t umożliwia systemowi przywrócenie wcześniej utworzonego klienta DHCPv6 w stanie związanym między ponownym uruchomieniem systemu. Wywołanie *nx_dhcpv6_client_get_record* , aby uzyskać rekord klienta DHCPv6 między ponownymi uruchomieniami systemu w wierszu 434, wywołując *nx_dhcpv6_client_restore_record* do przechowywania rekordu klienta DHCPv6 po włączeniu systemu w wierszu 525.

Następnie aplikacja zwalnia przypisane adresy przy użyciu usługi *nx_dhcpv6_request_release* w wierszu 552. Aby ponownie uruchomić aplikację, program zatrzyma klienta DHCPv6 z usługą *nx_dhcpv6_client_stop* w wierszu 567 i czyści wszystkie adresy IPv6 zarejestrowane z wystąpieniem IP skonfigurowanym Throughthe klienta DHCPv6. Robi to przez wywołanie *nx_dhcpv6_reinitialize* w wierszu 578. Następnie ponownie uruchamia zadanie klienta DHCPv6 z usługami *nx_dhcpv6_start* i *nx_dhcpv6_request_solicit* tak jak wcześniej.

Klient DHCPv6 został usunięty z wywołaniem *nx_dhcpv6_delete* w line626. Należy pamiętać, że nie usuwa tej puli pakietów *e* utworzonej dla klienta DHCPv6, ponieważ ta pula pakietów jest również używana przez wystąpienie protokołu IP. W przeciwnym razie należy usunąć pulę pakietów, jeśli nie będzie ona już używana do korzystania z usługi NetX Duo *nx_packet_pool_delete* .

```C
/* This is a small demo of the NetX Duo DHCPv6 Client for the high-performance NetX Duo stack. */

#include    <stdio.h>
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcpv6_client.h"

#ifdef FEATURE_NX_IPV6
#define     DEMO_STACK_SIZE         2048

/* Set the client address, and request these address from DHCPv6 Server. */
/*
#define     NX_DHCPV6_REQUEST_IA_ADDRESS
*/

/* Set the list of DHCPv6 option data (timezone, DNS server, timer server, domain name)to get from the DHCPv6 server. */

#define     NX_DHCPV6_REQUEST_OPTION


/* Add the fully qualified domain name to request whether the DHCPv6 server SHOULD or SHOULD NOT perform the AAAA RR or DNS updates. */

#define     NX_DHCPV6_REQUEST_FQDN_OPTION


/* Define the ThreadX and NetX object control blocks... */

NX_PACKET_POOL          pool_0;
TX_THREAD               thread_client;
NX_IP                   client_ip;

/* Define the Client and Server instances. */

NX_DHCPV6               dhcp_client;

/* Define the error counter used in the demo application... */
ULONG                   error_counter;
CHAR                    *pointer;

/* Define thread prototypes. */
void    thread_client_entry(ULONG thread_input);

/***** Substitute your ethernet driver entry function here *********/
extern VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Declare DHCPv6 Client callbacks */
VOID dhcpv6_state_change_notify(NX_DHCPV6 *dhcpv6_ptr, UINT old_state, UINT new_state);
VOID dhcpv6_server_error_handler(NX_DHCPV6 *dhcpv6_ptr, UINT op_code, UINT status_code, UINT message_type);

/* Set up globals for tracking changes to DHCPv6 Client from callback services. */
UINT state_changes = 0;
UINT address_expired = 0;
UINT address_failed_dad = 0;
UINT bound_addresses = 0;
UINT address_not_assigned = 0;
UINT server_errors = 0;

/* Define some DHCPv6 parameters. */

#define DHCPV6_IANA_ID      0xC0DEDBAD
#define DHCPV6_T1           NX_DHCPV6_INFINITE_LEASE
#define DHCPV6_T2           NX_DHCPV6_INFINITE_LEASE
#define DHCPV6_RENEW_TIME   NX_DHCPV6_INFINITE_LEASE
#define DHCPV6_REBIND_TIME  NX_DHCPV6_INFINITE_LEASE
#define PACKET_PAYLOAD      500
#define PACKET_POOL_SIZE    (5*PACKET_PAYLOAD)

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}


/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

UINT    status;

    /* Setup the working pointer. */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the Client thread. */
    status = tx_thread_create(&thread_client, "Client thread", thread_client_entry, 0,
                              pointer, DEMO_STACK_SIZE, 8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Check for IP create errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1024,  pointer, PACKET_POOL_SIZE);

    pointer = pointer + PACKET_POOL_SIZE;

    /* Check for pool creation error. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Create a Client IP instance. */
    status = nx_ip_create(&client_ip, "Client IP", IP_ADDRESS(0, 0, 0, 0),
                          0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                          pointer, 2048, 1);

    pointer =  pointer + 2048;

    /* Check for IP create errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Enable UDP traffic for sending DHCPv6 messages. */
    status =  nx_udp_enable(&client_ip);

    /* Check for UDP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Enable ICMP. */
    status =  nx_icmp_enable(&client_ip);

    /* Check for ICMP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Create the DHCPv6 Client. */
    status =  nx_dhcpv6_client_create(&dhcp_client, &client_ip, "DHCPv6 Client",
                                      &pool_0, pointer, 2048, dhcpv6_state_change_notify,
                                      dhcpv6_server_error_handler);

    /* Check for errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Update the stack pointer because we need it again. */
    pointer = pointer + 2048;

    /* Yield control to DHCPv6 threads and ThreadX. */
    return;
}


/* Define the Client host application thread. */

void    thread_client_entry(ULONG thread_input)
{

UINT        status;
ULONG       T1, T2;
UINT        address_count;
UINT        address_index = 0;
NXD_ADDRESS valid_ipv6_address;
ULONG       preferred_lifetime;
ULONG       valid_lifetime;
UINT        ia_count = 1;

#ifdef NX_DHCPV6_REQUEST_IA_ADDRESS
NXD_ADDRESS ipv6_address;
#endif

#ifdef NX_DHCPV6_REQUEST_OPTION
UCHAR       buffer[200];
NXD_ADDRESS dns_server;
#endif

#ifdef NX_DHCPV6_CLIENT_RESTORE_STATE
ULONG       current_time;
ULONG       elapsed_time;
NX_DHCPV6_CLIENT_RECORD dhcpv6_client_record;
#endif


    state_changes = 0;

    /* Establish the link local address for the host. The RAM driver creates
       a virtual MAC address of 0x1122334456. */
    status = nxd_ipv6_address_set(&client_ip, 0, NX_NULL, 10, NULL);

    if (status)
    {
        error_counter++;
        return;
    }

    /* Let NetX Duo get initialized. */
    tx_thread_sleep(50);

    /* Enable the Client IP for IPv6 and ICMPv6 services. */
    nxd_ipv6_enable(&client_ip);
    nxd_icmp_enable(&client_ip);

    /* Create a Link Layer Plus Time DUID for the DHCPv6 Client. Set time ID field
       to NULL; the DHCPv6 Client API will supply one. */
    status = nx_dhcpv6_create_client_duid(&dhcp_client, NX_DHCPV6_DUID_TYPE_LINK_TIME,
                                          NX_DHCPV6_HW_TYPE_IEEE_802, 0);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Create the DHCPv6 client's Identity Association (IA-NA) now.

       Note that if this host had already been assigned in IPv6 lease, it
       would have to use the assigned T1 and T2 values in loading the DHCPv6
       client with an IANA block.
    */
    status = nx_dhcpv6_create_client_iana(&dhcp_client, DHCPV6_IANA_ID, DHCPV6_T1,  DHCPV6_T2);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

#ifdef NX_DHCPV6_REQUEST_IA_ADDRESS
    memset(&ipv6_address,0x0, sizeof(NXD_ADDRESS));
    ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
    ipv6_address.nxd_ip_address.v6[0] = 0x3ffe0501;
    ipv6_address.nxd_ip_address.v6[1] = 0xffff0100;
    ipv6_address.nxd_ip_address.v6[2] = 0x00000000;
    ipv6_address.nxd_ip_address.v6[3] = 0x0000abcd;

    /* Create an IA address option.
        Note that if this host had already been assigned in IPv6 lease, it
        would have to use the assigned IPv6 address, preferred and valid lifetime
        values in loading the DHCPv6 Client with an IA block.
    */
    status = nx_dhcpv6_add_client_ia(&dhcp_client, &ipv6_address,DHCPV6_RENEW_TIME, DHCPV6_REBIND_TIME);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* If the DHCPv6 Client is configured for a maximum number of IA addresses
       greater than 1, we can add another IA address if the device requires
       multiple global IPv6 addresses. */
    if(NX_DHCPV6_MAX_IA_ADDRESS >= 2)
    {
        memset(&ipv6_address,0x0, sizeof(NXD_ADDRESS));
        ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
        ipv6_address.nxd_ip_address.v6[0] = 0x3ffe0501;
        ipv6_address.nxd_ip_address.v6[1] = 0xffff0100;
        ipv6_address.nxd_ip_address.v6[2] = 0x00000000;
        ipv6_address.nxd_ip_address.v6[3] = 0x00001234;

        /* Add another  IA address option. */
        status = nx_dhcpv6_add_client_ia(&dhcp_client, &ipv6_address, DHCPV6_RENEW_TIME, DHCPV6_REBIND_TIME);

        if (status != NX_SUCCESS)
        {
            error_counter++;
            return;
        }
    }
#endif /* NX_DHCPV6_REQUEST_IA_ADDRESS  */

#ifdef NX_DHCPV6_REQUEST_OPTION
    /* Set the list of DHCPv6 option data to get from the DHCPv6 server if needed. */
    nx_dhcpv6_request_option_timezone(&dhcp_client, NX_TRUE);
    nx_dhcpv6_request_option_DNS_server(&dhcp_client, NX_TRUE);
    nx_dhcpv6_request_option_time_server(&dhcp_client, NX_TRUE);
    nx_dhcpv6_request_option_domain_name(&dhcp_client, NX_TRUE);
#endif /* NX_DHCPV6_REQUEST_OPTION */


#ifdef NX_DHCPV6_REQUEST_FQDN_OPTION
    /* Set the DHCPv6 Client FQDN option.
       operation: NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR         DHCPv6 Client choose to updating the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the client.
                  NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE   DHCPv6 Client choose to updating the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the client to the server.
                  NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE   DHCPv6 Client choose to request that the server perform no DNS updatest on its behalf. */
    nx_dhcpv6_request_option_FQDN(&dhcp_client, "DHCPv6-Client", NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR);
#endif /* NX_DHCPV6_REQUEST_FQDN_OPTION */

    /* Start up the NetX DHCPv6 Client thread task. */
    status =  nx_dhcpv6_start(&dhcp_client);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Start the DHCPv6 by sending a Solicit message out on the network. */
    status = nx_dhcpv6_request_solicit(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Is the DHCPv6 Client request for address assignment successfully started? */
    if (status == NX_SUCCESS)
    {

        /* If Duplicate Address Detection (DAD) is enabled in NetX Duo, e.g. #NXDUO_DISABLE_DAD
           not defined, allow time for NetX Duo to verify the address is unique on our network.
         */
        tx_thread_sleep(500);

        /* Check the bound address. */
        if (bound_addresses != ia_count)
        {

            /* Attempt to find out why DHCPv6 failed, where...*/

            if (server_errors > 0)
            {
                /* Actually you would compare server_error count with number of IA's added
                   to determine if any addresses were assigned. */
                printf("Server error, not all address assigned\n");
            }

            if (address_not_assigned > 0)
            {
                /* Actually you would compare address not assigned count with number of IA's added
                   to determine if any addresses were assigned. */

                printf("No servers responded to some or all of our IAs\n");
            }

        }

        /* Regardless if the DHCPv6 Client achieved a bound state, check for DAD
           failures. */
        if (address_failed_dad > 0)
        {
            /* Actually you would compare failed dad count with number of IA's added
               to determine if any addresses were assigned. */

            printf("Some or all of our IAs failed DAD\n");

        }

        /* Successfully assigned IPv6 addresses! */

        /* Get the count of valid IPv6 address obtained by DHCPv6. */
        status = nx_dhcpv6_get_valid_ip_address_count(&dhcp_client, &address_count);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Get the IPv6 address and related lifetimes by address index. This index is the
           index into the DHCPv6 Client address table. Not to be confused with the IP
           instance address table! */
        status = nx_dhcpv6_get_valid_ip_address_lease_time(&dhcp_client, address_index,
                                                           &valid_ipv6_address, 
                                                               &preferred_lifetime,
                                                           &valid_lifetime);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Get the IANA options for when to start renew/rebind requests. These time
           parameters are the same for all IPv6 addresses assigned in the Client
           e.g. IANA returned from Server. */
        status = nx_dhcpv6_get_iana_lease_time(&dhcp_client, &T1, &T2);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /*****************************************************************************/
        /* These are 'legacy' DHCPv6 services and are for the most part identical to the services
           above except they default to the primary global IPv6 address regardless if the
           Client was assigned more than one global IPv6 address. */

        /* Now check the assigned lease times. */
        status = nx_dhcpv6_get_lease_time_data(&dhcp_client, &T1, &T2,
                                               &preferred_lifetime, &valid_lifetime);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Get the IP address. */
        status = nx_dhcpv6_get_IP_address(&dhcp_client, &valid_ipv6_address);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Bound state. */

#ifdef NX_DHCPV6_CLIENT_RESTORE_STATE

        /* Get the DHCPv6 Client record. */
        nx_dhcpv6_client_get_record(&dhcp_client, &dhcpv6_client_record);

        /* Delete DHCPv6 instance. */
        nx_dhcpv6_client_delete(&dhcp_client);

        /* Delete IP instance. */
        status = nx_ip_delete(&client_ip);

        /* Check for error. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Create a Client IP instance. */
        status = nx_ip_create(&client_ip, "Client IP", IP_ADDRESS(0, 0, 0, 0),
                              0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                              pointer, 2048, 1);

        pointer =  pointer + 2048;

        /* Check for IP create errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Enable UDP traffic for sending DHCPv6 messages. */
        status =  nx_udp_enable(&client_ip);

        /* Check for UDP enable errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Enable ICMP. */
        status =  nx_icmp_enable(&client_ip);

        /* Check for ICMP enable errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Enable the Client IP for IPv6 and ICMPv6 services. */
        status = nxd_ipv6_enable(&client_ip);
        status += nxd_icmp_enable(&client_ip);

        /* Check for IPv6 and ICMPv6 enable errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Establish the link local address for the host. The RAM driver creates
           a virtual MAC address of 0x1122334456. */
        status = nxd_ipv6_address_set(&client_ip, 0, NX_NULL, 10, NULL);

        if (status)
        {
            error_counter++;
            return;
        }

        /* If Duplicate Address Detection (DAD) is enabled in NetX Duo, e.g. #NXDUO_DISABLE_DAD
           not defined, allow time for NetX Duo to verify the address is unique on our network.
         */
        tx_thread_sleep(500);

        /* Create the DHCPv6 Client. */
        status =  nx_dhcpv6_client_create(&dhcp_client, &client_ip, "DHCPv6 Client",
                                          &pool_0, pointer, 2048, dhcpv6_state_change_notify,
                                          dhcpv6_server_error_handler);

        /* Check for errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Update the stack pointer because we need it again. */
        pointer = pointer + 2048;

        /* Restore the DHCPv6 record. */
        nx_dhcpv6_client_restore_record(&dhcp_client, &dhcpv6_client_record, 5);

        /* Resume the DHCPv6 service. */
        nx_dhcpv6_resume(&dhcp_client);
#endif


#ifdef NX_DHCPV6_REQUEST_OPTION

        /* Get the DNS Server address. */
        nx_dhcpv6_get_DNS_server_address(&dhcp_client, 0, &dns_server);

        /* Get the domain name. */
        memset(buffer, 0, sizeof(buffer));

        nx_dhcpv6_get_other_option_data(&dhcp_client, NX_DHCPV6_DOMAIN_NAME_OPTION, buffer, 200); // Try to get DNS info got from DHCPv6 Server

        /* Get the domain name. */
        memset(buffer, 0, sizeof(buffer));

        /* Get the time zone. */
        nx_dhcpv6_get_other_option_data(&dhcp_client, NX_DHCPV6_NEW_POSIX_TIMEZONE_OPTION, buffer, 200); // Try to get DNS info got from DHCPv6 Server
#endif

        /* At some point, we may wish to release the IPv6 address lease e.g. the device
           is leaving the network or powering down. In that case we inform the
           DHCPv6 Server that we are releasing the address lease. */
        status = nx_dhcpv6_request_release(&dhcp_client);

        /* Check status. */
        if (status != NX_SUCCESS)
        {

            error_counter++;
            return;
        }

        /* Send the release message. */
        tx_thread_sleep(100);
    }

    /* Stopping the Client task. */
    status = nx_dhcpv6_stop(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Clear the previously assigned IPv6 addresses from the Client and IP address table. */
    status = nx_dhcpv6_reinitialize(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Start up the Client task again. */
    status = nx_dhcpv6_start(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Begin the request process by sending a Solicit message with the IA created above
       with our preferred IPv6 address. */
    status = nx_dhcpv6_request_solicit(&dhcp_client);
    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Wait a bit before releasing the IP address and terminating the client. */
    tx_thread_sleep(500);

    /* Ok, lets stop the application. Again we DO NOT plan
       to keep the IPv6 address we were assigned and need to release it
       back to the DHCPv6 server. */
    status = nx_dhcpv6_request_release(&dhcp_client);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    /* Now delete the DHCPv6 client and release ThreadX and
       NetX Duo resources back to the system. */
    nx_dhcpv6_client_delete(&dhcp_client);


    return;

}


/* This is the notification from the DHCPv6 Client task that it has changed
   state in the DHCPv6 protocol, for example getting assigned an IPv6 lease and
   achieving the bound state or an IPv6 lease expires and being reset to
   the init state.
*/
VOID dhcpv6_state_change_notify(NX_DHCPV6 *dhcpv6_ptr, UINT old_state, UINT new_state)
{


    /* Increment state change counter. */
    state_changes++;

    /* Check if the Client attempted to request an IPv6 lease but no servers
       responded. */
    if ((old_state == NX_DHCPV6_STATE_SENDING_SOLICIT) && (new_state == NX_DHCPV6_STATE_INIT))
    {

        /* Indication that either DAD failed or IP lease expired. */
        address_not_assigned++;
    }

    /* Check if the Client has been assigned an IPv6 lease. */
    if (new_state == NX_DHCPV6_STATE_BOUND_TO_ADDRESS)
    {
        bound_addresses++;
    }

   /* Check if the Client was bound, but failed the uniqueness check
       (Duplicate Address Detection) and was reset to the INIT state. */
    if ((old_state == NX_DHCPV6_STATE_SENDING_DECLINE) && (new_state == NX_DHCPV6_STATE_INIT))
    {

        /* Indication that DAD failed on Client IA. */
        address_failed_dad++;
    }

    /* Check if the Client was bound, attempted renew the lease but the
       IPv6 address renewal/rebinding failed. */
    if ((old_state == NX_DHCPV6_STATE_SENDING_REBIND) && (new_state == NX_DHCPV6_STATE_INIT))
    {

        /* Indication that the IP lease expired. */
        address_expired++;
    }



    /* Other checks are possible. */

}

/* This is the notification from the DHCPv6 Client task that it received an error
   from the server (status code) in response to the Client's last DHCPv6 message.
*/

VOID dhcpv6_server_error_handler(NX_DHCPV6 *dhcpv6_ptr, UINT op_code, UINT status_code, UINT message_type)
{

    /* Increment the server error count. */
    server_errors++;

    /* This should distinguish between receiving a server error and no server
       available to assign the Client an IPv6 address if the Client fails
       to get assigned an address. */
}

#endif /* FEATURE_NX_IPV6 */
```
