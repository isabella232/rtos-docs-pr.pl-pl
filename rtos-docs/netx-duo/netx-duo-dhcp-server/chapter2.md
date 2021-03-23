---
title: Rozdział 2 — Instalowanie i korzystanie z serwera DHCP usługi Azure RTO NetX Duo
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika DHCP NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 201e8b7e245539c1780ace4c3af4bc063a8485b3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822015"
---
# <a name="chapter-2---installation-and-use-of-the-azure-rtos-netx-duo-dhcp-server"></a>Rozdział 2 — Instalowanie i korzystanie z serwera DHCP usługi Azure RTO NetX Duo

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika DHCP NetX Duo.

## <a name="product-distribution"></a>Dystrybucja produktu

Serwer DHCP NetX Duo jest dostępny pod adresem [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . Pakiet zawiera dwa pliki źródłowe i plik PDF, który zawiera ten dokument, w następujący sposób:

- **nxd_dhcp_server. h** Plik nagłówkowy serwera DHCP z NetX Duo
- **nxd_dhcp_server. c** Plik źródłowy C dla serwera DHCP z NetX Duo
- **nxd_dhcp_server.pdf** Podręcznik użytkownika dla serwera DHCP NetX Duo
- **demo_netxduo_dhcp. c** Demonstracja serwera DHCP NetX Duo

## <a name="dhcp-installation"></a>Instalacja DHCP

Aby można było korzystać z serwera DHCP z systemem NetX Duo, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX Duo. Na przykład jeśli NetX Duo jest zainstalowana w katalogu "*\threadx\arm7\green*", wówczas pliki *nxd_dhcp_server. h* i *nxd_dhpc_server. c* powinny zostać skopiowane do tego katalogu.

## <a name="using-netx-duo-dhcp-server"></a>Korzystanie z serwera DHCP z NetX Duo

Korzystanie z serwera DHCP z NetX Duo jest proste. Zasadniczo kod aplikacji musi zawierać *nx_dhcp_server. h* , po uwzględnieniu *tx_api. h* i *nx_api. h*, aby użyć odpowiednio ThreadX i NetX Duo. Po dołączeniu *nxd_dhcp_server. h* kod aplikacji będzie następnie mógł określić wywołania funkcji DHCP w dalszej części tego przewodnika. Aplikacja musi również zawierać *nxd_dhcp_server. c* w procesie kompilacji. Ten plik musi być skompilowany w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone wraz z plikami aplikacji. Aby uzyskać więcej informacji na temat korzystania z serwera DHCP z systemem NetX Duo, zobacz poniższe sekcje wymagania dotyczące **serwera** DHCP **w systemie NetX Duo** i ograniczeń serwera DHCP z systemem **NetX Duo**.

Należy pamiętać, że ponieważ protokół DHCP korzysta z usług UDP NetX Duo, należy włączyć protokół UDP przy użyciu wywołania *nx_udp_enable* przed użyciem protokołu DHCP.

## <a name="requirements-of-the-netx-duo-dhcp-server"></a>Wymagania dotyczące serwera DHCP z NetX Duo

Serwer DHCP NetX Duo wymaga, aby port gniazda UDP został przypisany do dobrze znanego portu DHCP 67. Aby utworzyć serwer DHCP, aplikacja musi utworzyć pulę pakietów z ładunkiem pakietu o co najmniej 548 bajtach, a także nagłówkiem IP, UDP i Ethernet (łącznie 44 bajtów z 4 bajtem).

Przyjęto założenie, że serwer i klient używają ustawień adresu sprzętowego sieci Ethernet:

- Typ sprzętu 1
- Długość sprzętu 6
- Przeskoki 0

### <a name="multiple-client-sessions"></a>Wiele sesji klienta

Serwer DHCP z systemem NetX Duo może obsługiwać wiele sesji klientów, zachowując tabelę aktywnych klientów DHCP i jakie "Stany" klient znajduje się na liście. Stany DHCP INICJUJą, URUCHAMIAją, WYBIERAją, ŻĄDAją, ODNAWIAnia itp. Jeśli limit czasu sesji upływa przed odebraniem następnego komunikatu klienta, o ile ten klient nie jest powiązany z dzierżawą IP, serwer wyczyści dane sesji klienta i zwróci przypisany adres IP z powrotem do dostępnej puli. Jeśli serwer odbierze wiele komunikatów ODNAJDYWAnia z tego samego klienta, serwer resetuje limit czasu sesji i utrzymuje adres IP zarezerwowany dla klienta w kolejnych komunikatach żądania.

Serwer DHCP NetX Duo akceptuje również żądanie DHCP klienta pojedynczego stanu, np. klient wysyła tylko komunikat żądania. Przyjęto założenie, że klientowi przypisano wcześniej dzierżawę adresu IP z serwera DHCP.

### <a name="setting-interface-specific-network-parameters-server-responses"></a>Ustawianie specyficznych dla interfejsu parametrów sieciowych odpowiedzi serwera

Aplikacja może ustawić router, maskę podsieci i parametry serwera DNS dla każdego interfejsu, który obsługuje żądania klientów DHCP przy użyciu usługi *nx_dhcp_set_interface_network_parameters* . W przeciwnym razie te parametry są domyślnie przypisane do bramy IP w interfejsie głównym serwera, jego podsieci sieciowej DHCP i adresu IP serwera DHCP.

Serwer DHCP zawiera te parametry w danych opcji komunikatów DHCP wysyłanych do klientów DHCP.

### <a name="assigning-ip-addresses-to-the-client"></a>Przypisywanie adresów IP do klienta

Jeśli komunikat ODNAJDYWAnia klienta nie określa żądanego adresu IP, serwer DHCP może użyć jednego z jego własnej puli. Jeśli serwer nie ma dostępnych adresów IP, wyśle klientowi komunikat NACK.

Serwer DHCP NetX Duo przydzieli żądany adres IP w komunikacie żądania klienta, o ile adres IP jest dostępny i znajduje się w bazie danych adresów IP serwera. Aplikacja tworzy listę dostępnych adresów IP serwera na potrzeby przypisywania do klientów DHCP przy użyciu usługi *nx_dhcp_create_server_ip_address_list* . Jeśli serwer nie ma żądanych adresów IP lub jest przypisany do innego hosta, wyśle klientowi komunikat NACK.

Gdy serwer DHCP odbiera żądanie klienta, identyfikuje tego klienta w sposób unikatowy przy użyciu adresu MAC klienta w polu adres MAC klienta w komunikacie DHCP. Jeśli klient zmieni adres MAC lub zostanie przeniesiony w innym miejscu do innej podsieci, powinien wysłać komunikat o ZWOLNIeniu do serwera w celu zwrócenia adresu IP z powrotem do dostępnej puli i zażądać nowego adresu IP w stanie inicjowania.

Szczegóły można znaleźć na rysunku 1,1 w **małej sekcji systemowej** . Liczba adresów IP zapisanych w wystąpieniu serwera DHCP jest ograniczona do rozmiaru tablicy adresów serwera w bloku kontroli serwera DHCP i jest definiowana przez konfigurowalną NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE opcji.

### <a name="ip-address-lease-times"></a>Czasy dzierżawy adresów IP

Serwer DHCP również akceptuje czas dzierżawy klienta żądania, jeśli czas dzierżawy jest krótszy niż domyślny czas dzierżawy serwera, który jest zdefiniowany w opcji konfigurowalne NX_DHCP_DEFAULT_LEASE_TIME. Odnawianie i ponowne wiązanie czasów przypisanych do klienta wynosi odpowiednio 50% i 85% czasu dzierżawy, chyba że czas dzierżawy jest nieskończony (0xFFFFFFFF), w którym przypadku odnowienie i ponowne wiązanie czasu są również ustawione na nieskończoność.

### <a name="dhcp-server-timeouts"></a>Limity czasu serwera DHCP

Serwer DHCP ma konfigurowalny limit czasu sesji użytkownika, NX_DHCP_CLIENT_SESSION_TIMEOUT w celu oczekiwania na następny komunikat klienta DHCP, chyba że sesja zostanie ukończona. Limit czasu jest resetowany, gdy serwer odbierze następny komunikat od klienta, niezależnie od tego, czy wiadomość została wcześniej wysłana.

### <a name="internal-error-handling"></a>Wewnętrzna obsługa błędów

Serwer DHCP odbiera i przetwarza pakiety klienta DHCP w funkcji *nx_dhcp_listen_for_messages* . Ta funkcja nie będzie kontynuować przetwarzania bieżącego pakietu klienta DHCP, jeśli pakiet jest nieprawidłowy lub wystąpił błąd wewnętrzny serwera DHCP. n *x_dhcp_listen_for_messages* zwraca stanu błędu. Wątek serwera DHCP zrzeka się krótkiej kontroli harmonogramu ThreadX przed wywołaniem tej funkcji, aby otrzymać następny komunikat klienta DHCP. W bieżącej wersji nie ma obsługi rejestrowania dla stanu błędu zwraca z *nx_dhcp_listen_for_messages.*

### <a name="option-55-parameter-request-list"></a>Opcja 55: Lista żądań parametrów

Serwer DHCP NetX Duo musi być skonfigurowany z zestawem opcji do załadowania do parametru opcja żądania (55) w komunikatach oferta i DHCPACK przesyłanych z powrotem do klienta. Te opcje powinny obejmować dane konfiguracji krytycznej sieci dla sieci klienta i domyślnie zdefiniowane jako adres IP routera, maska podsieci i serwer DNS. Lista opcji jest listą rozdzielaną spacjami i zdefiniowaną w NX_DHCP_DEFAULT_SERVER_OPTION_LIST konfigurowanym przez użytkownika. Zwróć uwagę, że liczba opcji określona na tej liście musi być równa NX_DHCP_DEFAULT_OPTION_LIST_SIZE, która również jest zdefiniowana przez użytkownika.

## <a name="constraints-of-the-netx-duo-dhcp-server"></a>Ograniczenia serwera DHCP z NetX Duo

### <a name="dhcp-messages"></a>Komunikaty DHCP

Serwer DHCP NetX Duo nie sprawdza, czy adres IP nie został przypisany w innym miejscu w sieci przed przydzieleniem adresu IP klientowi. Jeśli istnieje wiele serwerów DHCP, może to być w rzeczywistości. *Zgodnie z dokumentem RFC 2131, jest odpowiedzialny za sprawdzenie, czy adres IP jest unikatowy w sieci* (np. pingowanie adresu). Jeśli tak nie jest, serwer powinien odebrać komunikat o ODRZUCENIu o adresie IP, aby zaktualizować jego bazę danych od klienta.

Serwer DHCP NetX Duo nie wydaje komunikatów FORCE_RENEW. Klient DHCP może odnowić dzierżawę adresów IP. Jednak serwer DHCP monitoruje pozostały czas dla wszystkich przypisanych adresów IP w swojej bazie danych. Gdy dzierżawa adresu IP wygaśnie, ten adres IP jest zwracany do puli dostępnych adresów IP. W związku z tym klient może aktywnie odnowić/ponownie powiązać dzierżawę adresów IP.

Dane sesji są wyczyszczone, gdy tylko klient zostanie przydzielony ("powiązany") do dzierżawy IP (lub jest odnawiany istniejący). Jeśli pakiet klienta pozostanie nieprawdziwy lub klient przekroczy limit czasu między odpowiedziami, dane sesji są usuwane.

### <a name="saving-data-between-reboots"></a>Zapisywanie danych między ponownymi uruchomieniami

Serwer DHCP NetX Duo zapisuje dane klienta, w tym parametry żądania DHCP w tabeli rekordu klienta. Ta tabela nie jest przechowywana w pamięci nieulotnej, dlatego jeśli Host serwera DHCP musi ponownie uruchomić te informacje nie zostaną zapisane między ponownymi uruchomieniami.

Serwer DHCP NetX Duo zapisuje dane dzierżawy adresów IP w tabeli adresów IP. Ta tabela nie jest przechowywana w pamięci nieulotnej, dlatego jeśli Host serwera DHCP musi ponownie uruchomić te informacje nie zostaną zapisane między ponownymi uruchomieniami.

### <a name="relay-agents"></a>Agenci przekazywania

Serwer DHCP NetX Duo jest skonfigurowany z zerowym adresem IP dla pola "Agent przekazywania", ponieważ nie obsługuje żądań DHCP w sieci.

## <a name="small-example-system"></a>Mały przykładowy system

Przykładem prostej metody korzystania z serwera DHCP z systemem NetX Duo jest opisany poniżej rysunek 1,1. W tym przykładzie plik dołączania DHCP *nxd_dhcp_server. h* jest wprowadzony w wierszu 5. Wszystkie linie są zdefiniowane w wierszach 7-13 dla rozmiaru stosu wątków serwera DHCP, rozmiaru stosu wątku IP i rozmiaru stosu wątku testu.

Pierwsze zadanie wątku testu opcjonalne do zatrzymywania, ponownego uruchamiania i ostatecznie usuwania serwera DHCP jest tworzone z użyciem funkcji "*test_thread_entry*" w wierszu 57. Blok kontroli serwera DHCP "*dhcp_server*" jest zdefiniowany jako zmienna globalna w wierszu 20. Należy zauważyć, że Pula pakietów serwera jest tworzona z pakietami o co najmniej tyle jak standardowy komunikat DHCP (548 bajtów Plus bajty nagłówka IP i UDP). Po pomyślnym utworzeniu wystąpienia IP dla serwera DHCP aplikacja utworzy serwer DHCP w wierszu 96. Następnie aplikacja włącza wystąpienie protokołu IP serwera do włączenia protokołu UDP. Przed uruchomieniem serwera DHCP, lista dostępnych adresów IP zostanie utworzona w wierszu 137 przy użyciu usługi **nx_dhcp_create_server_ip_address_list** . Parametry konfiguracji sieci są ustawiane w następującym wierszu 138 przy użyciu usługi **nx_dhcp_set_interface_network_parameters** . usługi serwera DHCP stają się dostępne, gdy aplikacja wywoła *nx_dhcp_server_start* w wierszu 141. Zadanie wątku testowego ilustruje użycie zatrzymywania i ponownego uruchamiania serwera DHCP.

```C
/* This is a small demo of NetX Duo DHCP Server for the high-performance NetX Duo TCP/IP stack.  */

#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcp_server.h"

#define     DEMO_TEST_STACK_SIZE         2048
#define     DEMO_SERVER_STACK_SIZE  2048
#define     SERVER_IP_ADDRESS_LIST  "192.168.2.10 192.168.2.11 192.168.2.12"
#define     PACKET_PAYLOAD          1000
#define     PACKET_POOL_SIZE        (PACKET_PAYLOAD * 10)
#define     SERVER_IP_THREAD_STACK    2048


/* Define the ThreadX and NetX Duo Duo object control blocks...  */

TX_THREAD test_thread;
NX_PACKET_POOL server_pool;
NX_IP server_ip;
NX_DHCP_SERVER dhcp_server;


/* Define the counters used in the demo application...  */

ULONG state_changes;


/* Define thread prototypes.  */

void test_thread_entry(ULONG thread_input);
void nx_etherDriver_mcf5485(struct NX_IP_DRIVER_STRUCT *driver_req);


/* Define main entry point.  */

int main()
{
    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
}


/* Define what the initial system looks like.  */

void    tx_application_define(void *first_unused_memory)
{
    CHAR    *pointer;
    UINT    status;


    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the test thread.  */
    status = tx_thread_create(&test_thread, "test thread", test_thread_entry, 0,
            pointer, TEST_STACK_SIZE,  1, 1, TX_NO_TIME_SLICE, TX_DONT_START);

    if (status)
    {
        printf("Error with DHCP test thread create. Status 0x%x\r\n", status);
        return;
    }

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX Duosystem.  */
    nx_system_initialize();

    /* Create the DHCP Server packet pool.  */
    status =  nx_packet_pool_create(&server_pool, "NetX Main Packet Pool", PACKET_PAYLOAD,
        pointer, PACKET_POOL_SIZE);
    pointer = pointer + PACKET_POOL_SIZE;

    /* Check for pool creation error.  */
    if (status)
    {
        printf("Error with DHCP server packet pool create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server IP instance.  */
    status = nx_ip_create(&server_ip, "NetX DHCP Server IP", NX_DHCP_SERVER_IP_ADDRESS,
        0xFFFFFF00UL,  &server_pool, nx_etherDriver_mcf5485, pointer,
        R_IP_THREAD_STACK, 1);

    pointer =  pointer + DEMO_IP_THREAD_STACK;

    /* Check for IP create errors.  */
    if (status)
    {
        printf("Error with DHCP server IP task create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server instance.  */
    status =  nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                                     DEMO_SERVER_STACK_SIZE,"DHCP Server", &server_pool);

    if (status)
    {
        printf("Error with DHCP server create. Status 0x%x\r\n", status);
        return;
    }

    pointer = pointer + DEMO_SERVER_STACK_SIZE;

    /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
    status =  nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors.  */
    if (status)
    {
        printf("Error with ARP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable UDP traffic.  */
    status =  nx_udp_enable(&server_ip);

    /* Check for UDP enable errors.  */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable ICMP to enable the ping utility.  */
    status =  nx_icmp_enable(&server_ip);

    /* Check for errors.  */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
    }

   status = nx_dhcp_create_server_ip_address_list(&dhcp_server, iface_index,
                                 START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

   status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                               NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                               IP_ADDRESS(10,0,0,1));

    /* Start the DHCP Server.  */
   status =  nx_dhcp_server_start(&dhcp_server);

    tx_thread_resume(&test_thread);
}

/* Define the test thread.  */
void    test_thread_entry(ULONG thread_input)
{
    UINT status;
    UINT keep_spinning;


    /* Just let the test thread be idle till we're ready to shut things down. */
    keep_spinning = 1;
    while(keep_spinning)
    {
        tx_thread_sleep(300);
    }

    printf("Stopping the server...\n");
    status = nx_dhcp_server_stop(&dhcp_server);
    if (status)
    {
        printf("Error with DHCP server stop. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(500);

    printf("Starting the server...\n");
    status = nx_dhcp_server_start(&dhcp_server);
    if (status)
    {
        printf("Error with DHPC server start. Status 0x%x\r\n", status);
        return;
    }


    tx_thread_sleep(600);

    printf("Stopping the server for good...\n");
    status = nx_dhcp_server_stop(&dhcp_server);
    if (status)
    {
        printf("Error with DHCP server stop. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(200);


    printf("Deleting the server...\n");
    status = nx_dhcp_server_delete(&dhcp_server);
    if (status)
    {
        printf("Error with DHCP server delete. Status 0x%x\r\n", status);
        return;
    }
}

```

**Rysunek 1,1 przykład aplikacji serwera DHCP NetX Duo**

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji do kompilowania serwera DHCP z NetX Duo. Poniższa lista zawiera szczegółowy opis:

- **NX_DISABLE_ERROR_CHECKING**: Ta opcja usuwa podstawowe sprawdzanie błędów serwera DHCP. Jest on zazwyczaj używany po debugowaniu aplikacji.
- **NX_DHCP_SERVER_THREAD_PRIORITY**: Ta opcja określa priorytet wątku serwera DHCP. Domyślnie ta wartość określa, że wątek DHCP działa z priorytetem 2.
- **NX_DHCP_TYPE_OF_SERVICE**: Ta opcja określa typ usługi wymaganej przez żądania UDP protokołu DHCP. Domyślnie ta wartość jest definiowana jako NX_IP_NORMAL w celu wskazania normalnej usługi pakietów IP.
- **NX_DHCP_FRAGMENT_OPTION**: włączono fragment dla żądań UDP protokołu DHCP. Domyślnie ta wartość jest ustawiona na NX_DONT_FRAGMENT, aby wyłączyć fragmentację protokołu UDP.
- **NX_DHCP_TIME_TO_LIVE**: określa liczbę routerów, które może przekazać pakiet, zanim zostanie on odrzucony. Wartość domyślna to 0x80.
- **NX_DHCP_QUEUE_DEPTH**: określa liczbę pakietów, które przechowuje gniazdo serwera DHCP przed przystąpieniem do opróżniania kolejki. Wartość domyślna to 5.
- **NX_DHCP_PACKET_ALLOCATE_TIMEOUT**: określa limit czasu w taktach czasomierza dla serwera DHCP NetX, aby oczekiwać na przydzielenie pakietu z jego puli pakietów. Wartość domyślna to NX_IP_PERIODIC_RATE.
- **NX_DHCP_SUBNET_MASK** Jest to maska podsieci, z którą klient DHCP powinien być skonfigurowany. Wartość domyślna to 0xFFFFFF00.
- **NX_DHCP_FAST_PERIODIC_TIME_INTERVAL**: ten limit czasu jest określany w taktach czasomierza dla szybkiego czasomierza serwera DHCP do sprawdzania pozostałego czasu sesji i obsługi sesji, które przekroczyły limit czasu.
- **NX_DHCP_SLOW_PERIODIC_TIME_INTERVAL**: ten limit czasu jest określany w taktach czasomierza serwera DHCP wolne czasomierz, aby sprawdzić pozostały czas dzierżawy adresu IP i obsłużyć dzierżawę, która przekroczyła limit czasu.
- **NX_DHCP_CLIENT_SESSION_TIMEOUT**: to jest limit czasu czasomierza w taktach, gdy serwer DHCP będzie czekać na następny komunikat klienta DHCP.
- **NX_DHCP_DEFAULT_LEASE_TIME**: jest to czas dzierżawy adresów IP (w sekundach) przypisany do klienta DHCP, a także podstawą obliczeń i czasów ponownego powiązania do klienta. Wartość domyślna to 0xFFFFFFFF (nieskończoność).
- **NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE**: rozmiar tablicy serwerów DHCP do przechowywania dostępnych adresów IP na potrzeby przypisywania do klienta. Wartość domyślna to 20.
- **NX_DHCP_CLIENT_RECORD_TABLE_SIZE**: rozmiar tablicy serwera DHCP do przechowywania rekordów klientów. Wartość domyślna to 50.
- **NX_DHCP_CLIENT_OPTIONS_MAX**: rozmiar tablicy w wystąpieniu klienta DHCP w celu przechowywania wszystkich żądanych opcji na liście żądań parametrów w bieżącej sesji. Wartość domyślna to 12.
- **NX_DHCP_OPTIONAL_SERVER_OPTION_LIST**: jest to bufor zawierający domyślną listę opcji do dostarczenia do bieżącego klienta DHCP na liście żądań parametrów. Wartość domyślna to "1 3 6".
- **NX_DHCP_OPTIONAL_SERVER_OPTION_SIZE**: jest to rozmiar tablicy przechowującej domyślną listę opcji serwera DHCP. Wartość domyślna to 3.
- **NX_DHCP_SERVER_HOSTNAME_MAX**: rozmiar buforu do przechowywania nazwy hosta serwera. Wartość domyślna to 32.
- **NX_DHCP_CLIENT_HOSTNAME_MAX**: rozmiar buforu do przechowywania nazwy hosta klienta w bieżącej sesji klienta serwera DHCP. Wartość domyślna to 32.
