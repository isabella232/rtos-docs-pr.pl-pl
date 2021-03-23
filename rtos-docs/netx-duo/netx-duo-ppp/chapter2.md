---
title: Rozdział 2 — Instalowanie i korzystanie z platformy Azure RTO NetX Duo Point-to-Point Protocol (PPP)
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika Azure RTO NetX Duo Point-to-Point Protocol (PPP).
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2270a2668884dbecc8368d4ee130e419afa92491
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821732"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-point-to-point-protocol-ppp"></a>Rozdział 2 — Instalowanie i korzystanie z platformy Azure RTO NetX Duo Point-to-Point Protocol (PPP)

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika Azure RTO NetX Duo Point-to-Point Protocol (PPP).

## <a name="product-distribution"></a>Dystrybucja produktu

Pakiet Azure RTO NetX Duo Point-to-Point Protocol (PPP) jest dostępny pod adresem <https://github.com/azure-rtos/netxduo> . Pakiet zawiera następujące pliki:

- **nx_ppp. h**: plik nagłówkowy dla protokołu PPP dla NetX
- plik źródłowy **nx_ppp. c**: c dla protokołu PPP dla NetX
- **nx_ppp.pdf**: Opis PDF dotyczący protokołu PPP dla NetX
- **demo_netx_ppp. c**: NetX PPP

## <a name="ppp-installation"></a>Instalacja protokołu PPP

Aby można było korzystać z protokołu PPP dla NetX, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX. Na przykład jeśli NetX jest zainstalowana w katalogu "*\threadx\arm7\green*", wówczas pliki *nx_ppp. h* i *nx_ppp. c* powinny zostać skopiowane do tego katalogu.

## <a name="using-ppp"></a>Korzystanie z protokołu PPP

Korzystanie z protokołu PPP dla NetX jest proste. W zasadzie kod aplikacji musi zawierać *nx_ppp. h* po zawiera *tx_api. h* i *nx_api. h*, aby użyć odpowiednio ThreadX i NetX. Po dołączeniu *nx_ppp. h* kod aplikacji może następnie wykonać wywołania funkcji PPP określone w dalszej części tego przewodnika. Aplikacja musi również zawierać *nx_ppp. c* w procesie kompilacji. Ten plik musi być skompilowany w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone wraz z plikami aplikacji. To wszystko, co jest wymagane do korzystania z protokołu PPP NetX.

## <a name="using-modems"></a>Korzystanie z modemów

Jeśli do nawiązania połączenia z Internetem wymagany jest modem, niektóre specjalne zagadnienia są wymagane do korzystania z produktu NetX PPP. Zasadniczo przy użyciu modemu wprowadzono dodatkową logikę inicjalizacji i logikę do utraty komunikacji. Ponadto większość dodatkowych logiki modemów jest wykonywana poza kontekstem protokołu PPP NetX. Podstawowy przepływ użycia protokołu PPP NetX z modemem wygląda następująco:

1. Zainicjuj modem

1. Wybierz usługodawcę internetowego (ISP)

1. Zaczekaj na połączenie

1. Poczekaj na monit o podanie identyfikatora użytkownika

1. Uruchamianie NetX PPP [PPP w operacji]

1. Utrata komunikacji

1. Zatrzymaj NetX PPP (lub Uruchom ponownie za pośrednictwem nx_ppp_restart)

### <a name="initialize-modem"></a>Zainicjuj modem

Korzystając z procedury wyjścia szeregowego niskiego poziomu aplikacji, modem jest inicjowany za pośrednictwem szeregu poleceń znaków ASCII (zobacz dokumentację modemu, aby uzyskać więcej informacji).

### <a name="dial-internet-service-provider"></a>Wybieranie dostawcy usług internetowych

Przy użyciu procedury wyjścia szeregowego niskiego poziomu aplikacji modem jest wybierany w celu wybrania usługodawcy internetowego. Na przykład poniżej przedstawiono typowy ciąg ASCII używany do wybierania usługodawcy internetowego o numerze 123-4567:

"ATDT123456\r"

### <a name="wait-for-connection"></a>Zaczekaj na połączenie

W tym momencie aplikacja czeka na otrzymanie wskazania od modemu, że połączenie zostało nawiązane. Jest to osiągane przez wyszukiwanie znaków z procedury wejściowej szeregu niskiego poziomu aplikacji. Zwykle modemy zwracają ciąg ASCII "CONNECT", gdy połączenie zostało nawiązane.

### <a name="wait-for-user-id-prompt"></a>Zaczekaj na monit o podanie identyfikatora użytkownika

Po nawiązaniu połączenia aplikacja musi teraz oczekiwać na początkowe żądanie logowania od usługodawcy internetowego. Zwykle przyjmuje postać ciągu ASCII, takiego jak "login?".

### <a name="start-netx-ppp"></a>Uruchom NetX PPP

W tym momencie można uruchomić NetX PPP. Jest to realizowane przez wywołanie usługi *nx_ppp_create* , a następnie usługi *nx_ip_create* . Mogą być również wymagane dodatkowe usługi umożliwiające włączenie protokołu PAP i skonfigurowanie adresów IP PPP. Aby uzyskać więcej informacji, zapoznaj się z poniższymi sekcjami tego przewodnika.

### <a name="loss-of-communication"></a>Utrata komunikacji

Po uruchomieniu protokołu PPP wszystkie informacje inne niż PPP są przekazywane do procedury "nieprawidłowa obsługa pakietów" aplikacji określonej dla usługi *nx_ppp_create* . Zwykle modemy wysyłają ciąg ASCII, taki jak "NO CARRIER", gdy komunikacja zostanie utracona w ramach usługodawcy internetowego. Gdy aplikacja odbiera pakiet bez protokołu PPP z takimi informacjami, powinien kontynuować zatrzymanie wystąpienia NetX PPP lub ponowne uruchomienie komputera stanu PPP za pośrednictwem interfejsu API *nx_ppp_restart* .

### <a name="stop-netx-ppp"></a>Zatrzymaj NetX PPP

Zatrzymywanie NetX PPP jest dość proste. W zasadzie wszystkie utworzone gniazda muszą być niepowiązane i usunięte. Następnie Usuń wystąpienie protokołu IP za pośrednictwem usługi *nx_ip_delete* . Po usunięciu wystąpienia adresu IP należy wywołać usługę *nx_ppp_delete* , aby zakończyć proces zatrzymywania protokołu PPP. W tym momencie aplikacja może teraz próbować ponownie ustanowić komunikację z usługodawcą internetowym.

## <a name="small-example-system"></a>Mały przykładowy system

Przykład, który ilustruje, jak łatwo jest używać NetX PPP jest opisany na rysunku 1,1 poniżej. W tym przykładzie plik dołączany PPP *nx_ppp. h* jest wprowadzany w wierszu 3. Następnie protokół PPP jest tworzony w lokalizacji *"tx_application_define*" w wierszu 56. Blok kontroli PPP "*my_ppp*" został wcześniej zdefiniowany jako zmienna globalna w wierszu 9. 

>[!NOTE]
>Przed utworzeniem wystąpienia adresu IP należy utworzyć protokół PPP. Po pomyślnym utworzeniu protokołu PPP i IP wątek "*my_thread*" czeka na połączenie protokołu PPP z wierszem 98. W wierszu 104 zarówno protokół PPP, jak i NetX są w pełni funkcjonalne.

Jeden z elementów niewidocznych w tym przykładzie jest bajtem szeregowym aplikacji, który odbiera ISR. Należy wywołać *nx_ppp_byte_receive* z "*my_ppp*" i bajt odebrany jako parametry wejściowe.

```c
0001 #include   "tx_api.h"
0002 #include   "nx_api.h"
0003 #include   "nx_ppp.h"
0004
#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_PPP                  my_ppp;

/* Define function prototypes. */

void    my_thread_entry(ULONG thread_input);
void    my_serial_driver_byte_output(UCHAR byte);
void    my_invalid_packet_handler(NX_PACKET *packet_ptr);
 
/* Define main entry point. */
intmain()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
 }


/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;

/* Setup the working pointer. */
pointer =  (CHAR *) first_unused_memory;

/* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                  pointer, DEMO_STACK_SIZE, 
                  2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                    1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error. */
    if (status)
        error_counter++;

    /* Create a PPP instance. */
    status = nx_ppp_create(&my_ppp, “My PPP”, &my_ip, pointer, 1024, 2, 
                           &my_pool, my_invalid_packet_handler, my_serial_driver_byte_output);
    pointer =  pointer + 1024;
    /* Check for PPP creation pool. */
    if (status)
        error_counter++;

    /* Create an IP instance with the PPP driver. */
    status = nx_ip_create(&my_ip,"My NetX IP Instance", 
                           IP_ADDRESS(216,2,3,1), 0xFFFFFF00, &my_pool, 
                           nx_ppp_driver, pointer, DEMO_STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors. */
    if (status)
        error_counter++;

    /* Enable ICMP for my IP Instance. */
    status =  nx_icmp_enable(&my_ip);

    /* Check for ICMP enable errors. */
    if (status)
        error_counter++;

    /* Enable UDP. */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
}

/* Define my thread. */
void    my_thread_entry(ULONG thread_input)
{

UINT        status;
ULONG       ip_status;
NX_PACKET   *my_packet;

/* Wait for the PPP link in my_ip to become enabled. */
    status =  nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,&ip_status,3000);

    /* Check for IP status error. */
    if (status) 
        return;

    /* Link is fully up and operational. All NetX activities 
    are now available. */

}
```
## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji dla tworzenia protokołu PPP dla NetX. Poniższa lista zawiera szczegółowy opis:

- **NX_DISABLE_ERROR_CHECKING**: zdefiniowane, ta opcja usuwa podstawowe sprawdzanie błędów PPP. Jest on zazwyczaj używany po debugowaniu aplikacji.
- **NX_PPP_PPPOE_ENABLE**: Jeśli jest zdefiniowany, protokół PPP może transmitować pakiet przez sieć Ethernet
- **NX_PPP_BASE_TIMEOUT**: określa współczynnik okresu (w taktach czasomierza), który zadanie wątku PPP jest wybudzany do sprawdzania zdarzeń PPP. Wartość domyślna to 1 * NX_IP_PERIODIC_RATE (100 Takty).
- **NX_PPP_DISABLE_INFO**: jeśli zdefiniowane, wewnętrzne zbieranie informacji PPP jest wyłączone.
- **NX_PPP_DEBUG_LOG_ENABLE**: Jeśli jest zdefiniowany, wewnętrzny Dziennik debugowania PPP jest włączony.
- **NX_PPP_DEBUG_LOG_PRINT_ENABLE**: Jeśli jest zdefiniowany, wewnętrzny Dziennik debugowania PPP *printf* do *stdio* jest włączony. Jest to prawidłowe tylko wtedy, gdy Dziennik debugowania jest włączony.
- **NX_PPP_DEBUG_LOG_SIZE**: rozmiar dziennika debugowania (liczba wpisów w dzienniku debugowania). Po osiągnięciu ostatniego wpisu przechwytywanie debugowania jest zawijane do pierwszego wpisu i zastępuje wszelkie przechwycone wcześniej dane. Wartość domyślna to 50.
- **NX_PPP_DEBUG_FRAME_SIZE**: Maksymalna ilość danych przechwyconych z odebranego ładunku pakietu i zapisanych w danych wyjściowych debugowania. Wartość domyślna to 50.
- **NX_PPP_DISABLE_CHAP**: Jeśli jest zdefiniowana, wewnętrzna LOGIKa CHAP protokołu PPP jest usuwana, w tym LOGIKI Digest MD5.
- **NX_PPP_DISABLE_PAP**: Jeśli jest zdefiniowany, wewnętrzna logika PAP protokołu PPP jest usuwana.
- **NX_PPP_DNS_OPTION_DISABLE**: w przypadku określenia opcji podstawowy serwer DNS jest wyłączona w odpowiedzi IPCP. Domyślnie ta opcja nie jest zdefiniowana.
- **NX_PPP_DNS_ADDRESS_MAX_RETRIES**: określa, ile razy Host PPP będzie żądał adresu serwera DNS od elementu równorzędnego w stanie IPCP. Nie ma to wpływu, jeśli NX_PPP_DNS_OPTION_DISABLE jest zdefiniowany. Wartość domyślna to 2.
- **NX_PPP_HASHED_VALUE_SIZE**: Określa rozmiar ciągów "wartość skrótu" używany w uwierzytelnianiu CHAP. Wartość domyślna to 16 bajtów, ale można ją zdefiniować ponownie przed włączeniem *nx_ppp. h.*
- **NX_PPP_MAX_LCP_PROTOCOL_RETRIES**: określa maksymalną liczbę ponownych prób w przypadku przekroczenia limitu czasu protokołu PPP przed wysłaniem kolejnego komunikatu żądania konfiguracji. Po osiągnięciu tej liczby uzgadnianie PPP jest przerywane, a stan łącza nie działa. Wartość domyślna to 20.
- **NX_PPP_MAX_PAP_PROTOCOL_RETRIES**: określa maksymalną liczbę ponownych prób w przypadku przekroczenia limitu czasu protokołu PPP przed wysłaniem innego komunikatu żądania uwierzytelnienia PAP. Po osiągnięciu tej liczby uzgadnianie PPP jest przerywane, a stan łącza nie działa. Wartość domyślna to 20.
- **NX_PPP_MAX_CHAP_PROTOCOL_RETRIES**: określa maksymalną liczbę ponownych prób w przypadku przekroczenia limitu czasu protokołu PPP przed wysłaniem kolejnego komunikatu wyzwania protokołu CHAP. Po osiągnięciu tej liczby uzgadnianie PPP jest przerywane, a stan łącza nie działa. Wartość domyślna to 20.
- **NX_PPP_MAX_IPCP_PROTOCOL_RETRIES**: określa maksymalną liczbę ponownych prób w przypadku przekroczenia limitu czasu PPP przed wysłaniem kolejnego komunikatu o żądaniu konfiguracji protokołu IPCP. Po osiągnięciu tej liczby uzgadnianie PPP jest przerywane, a stan łącza nie działa. Wartość domyślna to 20.
- **NX_PPP_MRU**: określa maksymalną jednostkę odbierania (MRU) dla protokołu PPP. Wartość domyślna to 1 500 bajtów (wartość minimalna). Ta definicja może być ustawiana przez aplikację przed włączeniem *nx_ppp. h*.
- **NX_PPP_MINIMUM_MRU**: Określa minimalną wartość MRU odebraną w komunikacie żądania konfiguracji LCP. Wartość domyślna to 1 500 bajtów (wartość minimalna). Ta definicja może być ustawiana przez aplikację przed włączeniem *nx_ppp. h*.
- **NX_PPP_NAME_SIZE**: Określa rozmiar ciągów "name" używanych w uwierzytelnianiu. Wartość domyślna to 32bytes, ale można ją ponownie zdefiniować przed włączeniem * nx_ppp. h.
- **NX_PPP_PASSWORD_SIZE**: Określa rozmiar ciągów "Password" używanych w uwierzytelnianiu. Wartość domyślna to 32bytes, ale można ją zdefiniować ponownie przed włączeniem *nx_ppp. h.*
- **NX_PPP_PROTOCOL_TIMEOUT**: definiuje opcję oczekiwania (w sekundach), przez jaką zadanie PPP odbiera odpowiedź na komunikat żądania protokołu PPP. Wartość domyślna to 4 sekundy.
- **NX_PPP_RECEIVE_TIMEOUTS**: określa, ile razy zadanie wątku PPP przekroczy czas oczekiwania na odebranie następnego znaku w strumieniu komunikatów PPP. Następnie protokół PPP zwalnia pakiet i rozpoczyna oczekiwanie na odebranie następnego komunikatu PPP. Wartość domyślna to 4.
- **NX_PPP_SERIAL_BUFFER_SIZE**: Określa rozmiar buforu szeregowego odbioru znaków. Wartość domyślna to 3 000 bajtów. Ta definicja może być ustawiana przez aplikację przed włączeniem *nx_ppp. h*.
- **NX_PPP_TIMEOUT**: definiuje opcję oczekiwania (w taktach czasomierza) na potrzeby przydzielania pakietów do przesyłania danych, a także do buforowania danych szeregowych PPP w pakietach w celu wysłania ich do warstwy adresów IP. Wartość domyślna to 4 * NX_IP_PERIODIC_RATE (400 Takty).
- **NX_PPP_THREAD_TIME_SLICE**: opcja wycinek czasu dla wątków PPP. Domyślnie ta wartość jest TX_NO_TIME_SLICE. Ta definicja może być ustawiana przez aplikację przed włączeniem *nx_ppp. h*.
- **NX_PPP_VALUE_SIZE**: Określa rozmiar ciągów "value" używanych w uwierzytelnianiu CHAP. Wartość domyślna to 32bytes, ale można ją zdefiniować ponownie przed włączeniem nx_ppp. h.