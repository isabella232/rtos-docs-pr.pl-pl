---
title: Rozdział 2 — Instalowanie i używanie serwera DHCP Azure RTOS NetX
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem Azure RTOS serwera DHCP NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 04cbf4c9529538c3b5db6f8045a28bbcad5861c6ce846a898fa3ba1c7d97b19f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799578"
---
# <a name="chapter-2---installation-and-use-of-the-azure-rtos-netx-dhcp-server"></a>Rozdział 2 — Instalowanie i używanie serwera DHCP Azure RTOS NetX

Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem Azure RTOS DHCP NetX.

## <a name="product-distribution"></a>Dystrybucja produktów

Azure RTOS serwera DHCP NetX można uzyskać z naszego publicznego repozytorium kodu źródłowego pod adresem [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) . Pakiet zawiera dwa pliki źródłowe i plik PDF zawierający ten dokument w następujący sposób:

- **nx_dhcp_server.h:** plik nagłówka dla serwera DHCP NetX
- **nx_dhcp_server.c:** plik źródłowy języka C dla serwera DHCP NetX
- **nx_dhcp_server.pdf:** opis w formacie PDF serwera DHCP NetX
- **demo_netx_dhcp_server.c:** pokaz serwera DHCP NetX

## <a name="dhcp-installation"></a>Instalacja protokołu DHCP

Aby można było korzystać z serwera DHCP NetX, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano program NetX. Jeśli na przykład netx jest zainstalowany w katalogu *"\threadx\arm7\green",* do tego katalogu powinny zostać skopiowane pliki *nx_dhcp_server.h* i *nx_dhpc_server.c.*

## <a name="using-netx-dhcp-server"></a>Korzystanie z serwera DHCP NetX

Korzystanie z serwera DHCP NetX jest łatwe. Zasadniczo kod aplikacji musi zawierać kod *nx_dhcp_server.h* po dojecheniu do plików *tx_api.h* *i nx_api.h,* aby można było używać odpowiednio threadX i NetX. Po *nx_dhcp_server.h* kod aplikacji może następnie wykonać wywołania funkcji DHCP określone w dalszej części tego przewodnika. Aplikacja musi również uwzględniać *nx_dhcp_server.c* w procesie kompilacji. Ten plik musi zostać skompilowany w taki sam sposób, jak inne pliki aplikacji, a jego formularz obiektu musi być połączony z plikami aplikacji. Aby uzyskać więcej informacji na temat korzystania z serwera DHCP NetX, zobacz następujące sekcje Wymagania dotyczące serwera [DHCP NetX](#requirements-of-the-netx-dhcp-server) i ograniczeń serwera [DHCP NetX.](#constraints-of-the-netx-dhcp-server)

> [!NOTE]
> Ponieważ protokół DHCP korzysta z usług NetX UDP, przed użyciem protokołu DHCP należy włączyć protokół UDP *nx_udp_enable* wywołaniu protokołu DHCP.

## <a name="requirements-of-the-netx-dhcp-server"></a>Wymagania dotyczące serwera DHCP NetX

Serwer DHCP NetX wymaga portu gniazda UDP przypisanego do dobrze znanego portu DHCP 67. Aby utworzyć serwer DHCP, aplikacja musi utworzyć pulę pakietów z ładunkiem pakietów o rozmiarze co najmniej 548 bajtów oraz nagłówkami adresów IP, UDP i Ethernet (które łącznie 44 bajty z wyrównaniem 4 bajtów).

Zakłada się, że zarówno serwer, jak i klient, korzysta z ustawień adresu sprzętowego sieci Ethernet:

- **Typ sprzętu:** 1
- **Długość sprzętu:** 6
- **Przeskoki:** 0

### <a name="multiple-client-sessions"></a>Wiele sesji klienta

Serwer DHCP NetX może obsługuje wiele sesji klientów, zachowując tabelę aktywnych klientów DHCP i "stan" klienta, np. INIT stanu DHCP, ROZRUCHU, WYBIERANIA, ŻĄDANIA, ODNAWIANIA itp. Jeśli upłynie czas sesji przed odebraniem następnego komunikatu klient, chyba że klient jest powiązany z dzierżawą ip, serwer wyczyści dane sesji klienta i zwróci przypisany adres IP z powrotem do dostępnej puli. Jeśli serwer odbiera wiele komunikatów ODNAJDYWANIA od tego samego klienta, serwer resetuje czas sesji i zachowuje adres IP zarezerwowany dla klienta do zaakceptowania w kolejnym komunikacie REQUEST.

Serwer DHCP NetX akceptuje również jedno stanowe żądanie DHCP klienta, na przykład klient wysyła tylko komunikat REQUEST. Przyjęto założenie, że klientowi wcześniej przypisano dzierżawę adresu IP z serwera DHCP.

### <a name="setting-interface-specific-network-parameters-server-responses"></a>Ustawianie odpowiedzi serwera parametrów sieci specyficznych dla interfejsu

Aplikacja może ustawić router, maskę podsieci i parametry serwera DNS dla każdego interfejsu, który obsługuje żądania klienta DHCP, przy *użyciu nx_dhcp_set_interface_network_parameters* usługi. W przeciwnym razie te parametry są domyślnie bramy IP w interfejsie podstawowym serwera, jego podsieci sieci DHCP i adres IP serwera DHCP, odpowiednio.

Serwer DHCP zawiera te parametry w danych opcji komunikatów DHCP wysyłanych do klientów DHCP.

### <a name="assigning-ip-addresses-to-the-client"></a>Przypisywanie adresów IP do klienta

Jeśli komunikat ODNAJDYWANIE klienta nie określa żądanego adresu IP, serwer DHCP może użyć go z własnej puli. Jeśli serwer nie ma dostępnych adresów IP, wyśle klientowi komunikat NACK.

Serwer DHCP NetX udzieli żądanego adresu IP w komunikacie ŻĄDANIE klienta, o ile adres IP jest dostępny i można go znaleźć w bazie danych adresów IP serwera. Aplikacja tworzy listę dostępnych adresów IP serwera na potrzeby przypisywania do klientów DHCP przy użyciu *nx_dhcp_create_server_ip_address_list* usługi. Jeśli serwer nie ma żądanych adresów IP lub zostanie przypisany do innego hosta, wyśle klientowi komunikat NACK.

Gdy serwer DHCP odbiera żądanie klienta, identyfikuje go jednoznacznie przy użyciu adresu MAC klienta w polu Adres MAC klienta w komunikacie DHCP. Jeśli klient zmieni adres MAC lub zostanie przeniesiony w innym miejscu do innej podsieci, powinien wysłać do serwera komunikat RELEASE w celu zwrócenia adresu IP z powrotem do dostępnej puli i zażądać nowego adresu IP w stanie INIT.

Aby uzyskać szczegółowe informacje, zobacz rysunek 1.1 w sekcji **Small Example System (Mały** przykładowy system). Liczba adresów IP zapisanych w wystąpieniu serwera DHCP jest ograniczona do rozmiaru tablicy adresów serwera w bloku sterowania serwera DHCP i definiowana przez konfigurowalna opcja NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE.

### <a name="ip-address-lease-times"></a>Czasy dzierżawy adresów IP

Serwer DHCP będzie również akceptował czas dzierżawy klienta żądania, jeśli czas dzierżawy jest krótszy niż domyślny czas dzierżawy serwera, który jest zdefiniowany w konfigurowalnej opcji NX_DHCP_DEFAULT_LEASE_TIME. Czasy odnawiania i ponownego wiązania przypisane do klienta to odpowiednio 50% i 85% czasu dzierżawy, chyba że czas dzierżawy to nieskończoność (0xFFFFFFFF), w którym to przypadku czas odnowienia i ponownego wiązania jest również ustawiony na nieskończoność.

### <a name="dhcp-server-timeouts"></a>Limity czasu serwera DHCP

Serwer DHCP ma konfigurowalny przez użytkownika limit czasu sesji NX_DHCP_CLIENT_SESSION_TIMEOUT do oczekiwania na następny komunikat klienta DHCP, chyba że sesja została ukończona. Ten czas jest resetowany, gdy serwer odbiera następny komunikat od klienta, niezależnie od tego, czy jest to ten sam komunikat, który został wcześniej wysłany.

### <a name="internal-error-handling"></a>Wewnętrzna obsługa błędów

Serwer DHCP odbiera i przetwarza pakiety klienta DHCP w nx_dhcp_listen_for_messages *funkcji.* Ta funkcja zakończy przetwarzanie bieżącego pakietu klienta DHCP, jeśli pakiet jest nieprawidłowy lub serwer DHCP napotka błąd wewnętrzny.n x_dhcp_listen_for_messages zwraca stan błędu. Wątek serwera DHCP relinquishes kontroli przez krótki czas harmonogramu ThreadX przed wywołaniem tej funkcji do odbierania następnego komunikatu klienta DHCP. W bieżącej wersji nie ma obsługi rejestrowania dla powrotu stanu błędu z *nx_dhcp_listen_for_messages.*

### <a name="option-55-parameter-request-list"></a>Opcja 55. Lista żądań parametrów

Serwer DHCP NetX musi być skonfigurowany z zestawem opcji ładowania do listy opcji żądania parametru (55) w komunikatach OFFER i DHCPACK, które są wysyłane z powrotem do klienta. Te opcje powinny zawierać dane konfiguracji o krytycznym znaczeniu dla sieci klienta i domyślnie są zdefiniowane jako adres IP routera, maska podsieci i serwer DNS. Lista opcji jest listą rozdzielonych spacjami i zdefiniowaną w konfigurowalnym przez użytkownika NX_DHCP_DEFAULT_SERVER_OPTION_LIST. Należy pamiętać, że liczba opcji określona na tej liście musi być równa NX_DHCP_DEFAULT_OPTION_LIST_SIZE która jest również zdefiniowana przez użytkownika.

## <a name="constraints-of-the-netx-dhcp-server"></a>Ograniczenia serwera DHCP NetX

### <a name="dhcp-messages"></a>Komunikaty DHCP

Serwer DHCP NetX nie weryfikuje, czy adres IP nie został przypisany w innym miejscu w sieci przed udzieleniem adresu IP klientowi. Jeśli istnieje wiele serwerów DHCP, może tak być w rzeczywistości. *Zgodnie z RFC 2131* klient jest odpowiedzialny za sprawdzenie, czy adres IP jest unikatowy w jego sieci (np. wyślij polecenie ping do adresu). Jeśli tak nie jest, serwer powinien otrzymać komunikat ODRZUĆ z adresem IP, aby zaktualizować swoją bazę danych z klienta.

Serwer DHCP NetX nie wysyła komunikatów FORCE_RENEW komunikatów. To klient DHCP musi odnowić dzierżawę adresu IP. Serwer DHCP monitoruje jednak czas pozostały na wszystkich przypisanych adresach IP w swojej bazie danych. Po wygaśnięciu dzierżawy adresu IP ten adres IP jest zwracany do puli dostępnych adresów IP. W związku z tym klient musi aktywnie odnowić/ponownie powiązyć swoją dzierżawę adresu IP.

Dane sesji są czyszowane natychmiast po przyznaeniu klientowi ("powiązanej") dzierżawy adresu IP (lub odnowieniu istniejącej dzierżawy). Jeśli pakiet klienta zostanie udowodniony lub klient utracą czas między odpowiedziami, dane sesji są czyszowane.

### <a name="saving-data-between-reboots"></a>Zapisywanie danych między ponownymi uruchomieniami

Serwer DHCP NetX zapisuje dane klienta, w tym parametry żądania DHCP w tabeli rekordów klienta. Ta tabela nie jest przechowywana w pamięci trwałej, więc jeśli host serwera DHCP musi ponownie uruchomić te informacje nie są zapisywane między ponownymi uruchomieniami.

Serwer DHCP NetX zapisuje dane dzierżawy adresów IP w tabeli adresów IP. Ta tabela nie jest przechowywana w pamięci trwałej, więc jeśli host serwera DHCP musi ponownie uruchomić te informacje nie są zapisywane między ponownymi uruchomieniami.

### <a name="relay-agents"></a>Agenci przekaźnika

Serwer DHCP NetX jest skonfigurowany z zerowym adresem IP dla pola "Agent przekazywania", ponieważ nie obsługuje żądań DHCP poza siecią.

## <a name="small-example-system"></a>Mały przykładowy system

Przykład łatwego korzystania z serwera DHCP NetX opisano na rysunku 1.1, który znajduje się poniżej. W tym przykładzie plik dołączania DHCP *nx_dhcp_server.h* jest dostępny w wierszu 5. Rozmiar stosu wątku serwera DHCP, rozmiar stosu wątku IP i rozmiar stosu wątku testowego są zdefiniowane w wierszach 7–13.

Najpierw za pomocą funkcji "*test_thread_entry"* w wierszu 57 jest tworzone opcjonalne zadanie wątku testowego służące do zatrzymywania, ponownego uruchamiania i ostatecznie usuwania serwera DHCP. Blok sterowania serwera DHCP "*dhcp_server*" jest zdefiniowany jako zmienna globalna w wierszu 20. Należy pamiętać, że pula pakietów serwera jest tworzona z pakietami o ładunku co najmniej tak dużym jak standardowy komunikat DHCP (548 bajtów plus bajty nagłówka IP i UDP). Po pomyślnym utworzeniu wystąpienia adresu IP dla serwera DHCP aplikacja tworzy serwer DHCP w wierszu 96. Następnie aplikacja umożliwia włączenie protokołu UDP dla wystąpienia adresu IP serwera. Przed uruchomieniem serwera DHCP lista dostępnych adresów IP jest tworzona w wierszu 137 przy użyciu *nx_dhcp_create_server_ip_address_list* usługi. Parametry konfiguracji sieci są ustawiane w poniższym wierszu 138 przy użyciu usługi *nx_dhcp_set_interface_network_parameters,*  usługi serwera DHCP stają się dostępne, gdy aplikacja wywołuje nx_dhcp_server_start wierszu 141. Zadanie wątku testowego demonstruje sposób zatrzymywania i ponownego uruchamiania serwera DHCP.

```c
/* This is a small demo of NetX DHCP Server for the high-performance NetX TCP/IP stack. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nx_dhcp_server.h"

#define     DEMO_TEST_STACK_SIZE       2048
#define     DEMO_SERVER_STACK_SIZE     2048
#define     SERVER_IP_ADDRESS_LIST     "192.168.2.10 192.168.2.11 192.168.2.12"
#define     PACKET_PAYLOAD             1000
#define     PACKET_POOL_SIZE           (PACKET_PAYLOAD * 10)
#define     SERVER_IP_THREAD_STACK     2048

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD          test_thread;
NX_PACKET_POOL     server_pool;
NX_IP              server_ip;
NX_DHCP_SERVER     dhcp_server;

/* Define the counters used in the demo application... */

ULONG             state_changes;

/* Define thread prototypes. */

void     test_thread_entry(ULONG thread_input);
void     nx_etherDriver_mcf5485(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void     tx_application_define(void *first_unused_memory)
{

CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create the test thread. */
    status = tx_thread_create(&test_thread, "test thread", test_thread_entry, 0,
                pointer, TEST_STACK_SIZE, 1, 1, TX_NO_TIME_SLICE, TX_DONT_START);

    if (status)
    {
        printf("Error with DHCP test thread create. Status 0x%x\r\n", status);
        return;
    }

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create the DHCP Server packet pool. */
    status = nx_packet_pool_create(&server_pool, "NetX Main Packet Pool",
                                PACKET_PAYLOAD, pointer, PACKET_POOL_SIZE);
                                pointer = pointer + PACKET_POOL_SIZE;

    /* Check for pool creation error. */
    if (status)
    {
        printf("Error with DHCP server packet pool create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server IP instance. */
    status = nx_ip_create(&server_ip, "NetX DHCP Server IP", NX_DHCP_SERVER_IP_ADDRESS,
                        0xFFFFFF00UL, &server_pool, nx_etherDriver_mcf5485, pointer,
                        SERVER_IP_THREAD_STACK, 1);

    pointer = pointer + DEMO_IP_THREAD_STACK;

    /* Check for IP create errors. */
    if (status)
    {
        printf("Error with DHCP server IP task create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server instance. */
    status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                    DEMO_SERVER_STACK_SIZE,"DHCP Server", &server_pool);

    if (status)
    {
        printf("Error with DHCP server create. Status 0x%x\r\n", status);
        return;
    }

    pointer = pointer + DEMO_SERVER_STACK_SIZE;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    status = nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors. */
    if (status)
    {
        printf("Error with ARP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable UDP traffic. */
    status = nx_udp_enable(&server_ip);

    /* Check for UDP enable errors. */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable ICMP to enable the ping utility. */
    status = nx_icmp_enable(&server_ip);

    /* Check for errors. */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
    }

    status = nx_dhcp_create_server_ip_address_list(&dhcp_server, iface_index,
                START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);
    status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                                        NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                                        IP_ADDRESS(10,0,0,1));

    /* Start the DHCP Server. */
    status = nx_dhcp_server_start(&dhcp_server);

    tx_thread_resume(&test_thread);
}

/* Define the test thread. */
void     test_thread_entry(ULONG thread_input)
{

UINT     status;
UINT     keep_spinning;

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
        printf("Error with DHPC server stop. Status 0x%x\r\n", status);
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
        printf("Error with DHPC server stop. Status 0x%x\r\n", status);
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

Rysunek 1.1 Przykładowa aplikacja serwera DHCP NetX

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji do tworzenia serwera DHCP NetX. Na poniższej liście szczegółowo opisano poszczególne z nich:  
  
- **NX_DISABLE_ERROR_CHECKING:** Ta opcja usuwa podstawowe sprawdzanie błędów PROTOKOŁU DHCP. Jest on zwykle używany po debugowaniu aplikacji.  
- **NX_DHCP_SERVER_THREAD_PRIORITY:** ta opcja określa priorytet wątku serwera DHCP. Domyślnie ta wartość określa, że wątek DHCP jest uruchamiany z priorytetem 2.
- **NX_DHCP_TYPE_OF_SERVICE:** ta opcja określa typ usługi wymagany dla żądań protokołu UDP protokołu DHCP. Domyślnie ta wartość jest zdefiniowana jako wartość NX_IP_NORMAL, aby wskazać normalną usługę pakietów IP.
- **NX_DHCP_FRAGMENT_OPTION:** włącz fragment dla żądań protokołu UDP protokołu DHCP. Domyślnie ta wartość jest ustawiona na wartość NX_DONT_FRAGMENT aby wyłączyć fragmentowanie UDP.
- **NX_DHCP_TIME_TO_LIVE:** określa liczbę routerów, które pakiet może przekazać, zanim zostanie odrzucony. Wartość domyślna to 0x80.
- **NX_DHCP_QUEUE_DEPTH** Określa liczbę pakietów, które gniazda serwera DHCP przechowuje przed opróżnienie kolejki. Wartość domyślna to 5.
- **NX_DHCP_PACKET_ALLOCATE_TIMEOUT:** określa limit czasu w taktowaniach czasomierza dla serwera DHCP NetX do oczekiwania na przydzielenie pakietu z puli pakietów. Wartość domyślna to NX_IP_PERIODIC_RATE.
- **NX_DHCP_SUBNET_MASK:** jest to maska podsieci, za pomocą których należy skonfigurować klienta DHCP. Wartość domyślna to 0xFFFFFF00.
- **NX_DHCP_FAST_PERIODIC_TIME_INTERVAL:** jest to limit czasu w taktach czasomierza dla serwera DHCP szybkiego czasomierza, aby sprawdzić pozostały czas sesji i obsługiwać sesje, które mają limit czasu.
- **NX_DHCP_SLOW_PERIODIC_TIME_INTERVAL:** jest to limit czasu w taktach czasomierza dla czasomierza powolnego serwera DHCP, aby sprawdzić pozostały czas dzierżawy adresu IP i obsłużyć dzierżawę, dla których udano limit czasu.
- **NX_DHCP_CLIENT_SESSION_TIMEOUT:** jest to limit czasu w taktach czasomierza serwer DHCP będzie czekać na otrzymanie następnego komunikatu klienta DHCP.
- **NX_DHCP_DEFAULT_LEASE_TIME:** jest to czas dzierżawy adresu IP (w sekundach) przypisany do klienta DHCP, a także podstawa do obliczania czasu odnowienia i ponownego wiązania przypisana do klienta. Wartość domyślna jest ustawiona na wartość 0xFFFFFFFF (nieskończoność).
- **NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE:** jest to rozmiar macierzy serwerów DHCP do przechowywania dostępnych adresów IP do przypisania do klienta. Wartość domyślna to 20.
- **NX_DHCP_CLIENT_RECORD_TABLE_SIZE:** jest to rozmiar tablicy serwerów DHCP do przechowywania rekordów klienta. Wartość domyślna to 50.
- **NX_DHCP_CLIENT_OPTIONS_MAX:** jest to rozmiar tablicy w wystąpieniu klienta DHCP do przechowywania wszystkich żądanych opcji na liście żądań parametrów w bieżącej sesji. Wartość domyślna to 12.
- **NX_DHCP_OPTIONAL_SERVER_OPTION_LIST:** jest to bufor, w którym znajduje się domyślna lista opcji serwera DHCP, które należy dostarczyć do bieżącego klienta DHCP na liście żądań parametrów. Wartość domyślna to "1 3 6".
- **NX_DHCP_OPTIONAL_SERVER_OPTION_SIZE:** jest to rozmiar tablicy do przechowywania domyślnej listy opcji serwera DHCP. Wartość domyślna to 3.
- **NX_DHCP_SERVER_HOSTNAME_MAX:** jest to rozmiar buforu do przechowywania nazwy hosta serwera. Wartość domyślna to 32.
- **NX_DHCP_CLIENT_HOSTNAME_MAX:** jest to rozmiar buforu do przechowywania nazwy hosta klienta w bieżącej sesji klienta serwera DHCP. Wartość domyślna to 32.
