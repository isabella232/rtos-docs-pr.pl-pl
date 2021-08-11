---
title: Rozdział 2 — Instalowanie i używanie Azure RTOS NetX Duo Point-to-Point Protocol (PPP)
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem składnika Azure RTOS NetX Duo Point-to-Point Protocol (PPP).
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 141197daa87b40ebe2ea34ff096a0b01b260e9296a33e3b678f11400d5d46ab6
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797164"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-point-to-point-protocol-ppp"></a>Rozdział 2 — Instalowanie i używanie Azure RTOS NetX Duo Point-to-Point Protocol (PPP)

Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem składnika Azure RTOS NetX Duo Point-to-Point Protocol (PPP).

## <a name="product-distribution"></a>Dystrybucja produktów

Pakiet Azure RTOS NetX Duo Point-to-Point Protocol (PPP) jest dostępny na stronie <https://github.com/azure-rtos/netxduo> . Pakiet zawiera następujące pliki:

- **nx_ppp.h:** Plik nagłówkowy dla PROTOKOŁU PPP dla NetX
- **nx_ppp.c:** plik źródłowy JĘZYKA C dla protokołu PPP dla NetX
- **nx_ppp.pdf:** opis PDF protokołu PPP dla NetX
- **demo_netx_ppp.c:** pokaz NETX PPP

## <a name="ppp-installation"></a>Instalacja PROTOKOŁU PPP

Aby można było używać protokołu PPP dla NetX, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano platformę NetX. Jeśli na przykład netx jest zainstalowany w katalogu *"\threadx\arm7\green",* do tego katalogu powinny zostać skopiowane pliki *nx_ppp.h* i *nx_ppp.c.*

## <a name="using-ppp"></a>Korzystanie z protokołu PPP

Korzystanie z protokołu PPP dla NetX jest łatwe. Zasadniczo kod aplikacji musi zawierać kod *nx_ppp.h* po dołączyć elementy *tx_api.h* i *nx_api.h*, aby można było używać odpowiednio threadX i NetX. Po *nx_ppp.h* kod aplikacji może następnie wykonać wywołania funkcji PPP określone w dalszej części tego przewodnika. Aplikacja musi również *uwzględniać nx_ppp.c* w procesie kompilacji. Ten plik musi zostać skompilowany w taki sam sposób, jak inne pliki aplikacji, a jego formularz obiektu musi być połączony z plikami aplikacji. To wszystko, co jest wymagane do korzystania z protokołu NETX PPP.

## <a name="using-modems"></a>Korzystanie z modemów

Jeśli modem jest wymagany do połączenia z Internetem, w celu korzystania z produktu NETX PPP należy wziąć pod uwagę pewne specjalne kwestie. Zasadniczo korzystanie z modemu wprowadza dodatkową logikę inicjowania i logikę utraty komunikacji. Ponadto większość dodatkowej logiki modemu jest wykonywana poza kontekstem protokołu NETX PPP. Podstawowy przepływ korzystania z protokołu NETX PPP z modemem wygląda podobnie do tego:

1. Inicjowanie modemu

1. Wybierz dostawcę usług internetowych (ISP)

1. Oczekiwanie na połączenie

1. Oczekiwanie na monit o identyfikator użytkownika

1. Uruchamianie protokołu NETX PPP [działanie protokołu PPP]

1. Utrata komunikacji

1. Zatrzymywanie protokołu NETX PPP (lub ponowne uruchamianie za pośrednictwem nx_ppp_restart)

### <a name="initialize-modem"></a>Inicjowanie modemu

Korzystając z procedury szeregowych danych wyjściowych niskiego poziomu aplikacji, modem jest inicjowania za pośrednictwem serii poleceń znaków ASCII (aby uzyskać więcej informacji, zobacz dokumentację modemu).

### <a name="dial-internet-service-provider"></a>Wybieranie dostawcy usług internetowych

Korzystając z procedury szeregowych danych wyjściowych niskiego poziomu aplikacji, modem jest instruowany, aby wybrać usługę ISP. Na przykład poniżej przedstawiono typowy ciąg ASCII używany do wybierania isp isp pod numerem 123-4567:

"ATDT123456\r"

### <a name="wait-for-connection"></a>Oczekiwanie na połączenie

W tym momencie aplikacja czeka na otrzymanie od modemu wskazania, że połączenie zostało nawiązane. Jest to realizowane przez szukanie znaków z procedury wprowadzania szeregowego niskiego poziomu aplikacji. Zwykle modemy zwracają ciąg ASCII "CONNECT" po nawiązaniu połączenia.

### <a name="wait-for-user-id-prompt"></a>Oczekiwanie na monit o identyfikator użytkownika

Po nawiązaniu połączenia aplikacja musi teraz poczekać na początkowe żądanie logowania od isp. Zazwyczaj ma ona postać ciągu ASCII, takiego jak "Logowanie?".

### <a name="start-netx-ppp"></a>Uruchamianie protokołu NETX PPP

W tym momencie można rozpocząć protokół PPP NetX. Jest to realizowane przez wywołanie usługi *nx_ppp_create,* a następnie nx_ip_create *usługi.* Mogą być również wymagane dodatkowe usługi do włączania protokołu PAP i konfigurowania adresów IP PROTOKOŁU PPP. Zapoznaj się z następującymi sekcjami tego przewodnika, aby uzyskać więcej informacji.

### <a name="loss-of-communication"></a>Utrata komunikacji

Po zakończeniu działania protokołu PPP wszystkie informacje inne niż PROTOKOŁU PPP są przekazywane do procedury "nieprawidłowej obsługi pakietów" określonej przez aplikację *nx_ppp_create* usługi. Zazwyczaj modemy wysyłają ciąg ASCII, taki jak "NO CARRIER", gdy komunikacja zostanie utracona z isp. Gdy aplikacja odbiera pakiet bez protokołu PPP z takimi informacjami, powinna przejść do zatrzymania wystąpienia protokołu PPP NetX lub ponownego uruchomienia maszyny stanu PROTOKOŁU PPP za pośrednictwem interfejsu *API* nx_ppp_restart API.

### <a name="stop-netx-ppp"></a>Zatrzymywanie protokołu NETX PPP

Zatrzymywanie protokołu PPP NetX jest dość proste. Zasadniczo wszystkie utworzone gniazda muszą być niepowiązane i usunięte. Następnie usuń wystąpienie adresu IP za pośrednictwem *nx_ip_delete* usługi. Po usunięciu wystąpienia adresu IP należy *nx_ppp_delete,* aby zakończyć proces zatrzymywania protokołu PPP. W tym momencie aplikacja może próbować ponownie nawiązać komunikację z isp.

## <a name="small-example-system"></a>Mały przykładowy system

Przykład, który ilustruje, jak łatwo można korzystać z protokołu NETX PPP, został opisany na rysunku 1.1, który znajduje się poniżej. W tym przykładzie plik dołączany przez protokół PPP *nx_ppp.h* jest dołączany w wierszu 3. Następnie protokół PPP jest tworzony w ciągu *"tx_application_define"* w wierszu 56. Blok sterowania PPP "*my_ppp*" został wcześniej zdefiniowany jako zmienna globalna w wierszu 9. 

>[!NOTE]
>Przed utworzeniem wystąpienia adresu IP należy utworzyć protokół PPP. Po pomyślnym utworzeniu protokołu PPP i ip wątek "*my_thread*" czeka, aż połączenie PPP stanie się aktywne w wierszu 98. W wierszu 104 zarówno protokół PPP, jak i NetX są w pełni operacyjne.

Jednym elementem, który nie jest pokazany w tym przykładzie, jest szeregowy bajt odbierany przez aplikację ISR. Musi on wywołać parametr *nx_ppp_byte_receive* z wartością *"my_ppp"* i bajtem odebranym jako parametry wejściowe.

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

Istnieje kilka opcji konfiguracji tworzenia protokołu PPP dla NetX. Na poniższej liście szczegółowo opisano poszczególne z nich:

- **NX_DISABLE_ERROR_CHECKING:** zdefiniowana, ta opcja usuwa podstawowe sprawdzanie błędów PROTOKOŁU PPP. Jest on zwykle używany po debugowaniu aplikacji.
- **NX_PPP_PPPOE_ENABLE:** Jeśli jest zdefiniowana, protokół PPP może przesyłać pakiety za pośrednictwem sieci Ethernet
- **NX_PPP_BASE_TIMEOUT:** Definiuje szybkość okresu (w taktach czasomierza), w którym zadanie wątku PPP jest wyzbujone w celu sprawdzenia zdarzeń PROTOKOŁU PPP. Wartość domyślna to 1*NX_IP_PERIODIC_RATE (100 takt).
- **NX_PPP_DISABLE_INFO:** Jeśli zdefiniowano, wewnętrzne zbieranie informacji PROTOKOŁU PPP jest wyłączone.
- **NX_PPP_DEBUG_LOG_ENABLE:** Jeśli jest zdefiniowany, wewnętrzny dziennik debugowania PROTOKOŁU PPP jest włączony.
- **NX_PPP_DEBUG_LOG_PRINT_ENABLE:** Jeśli zdefiniowano, wewnętrzny *printf* dziennika debugowania PROTOKOŁU PPP do *stdio* jest włączony. Ta opcja jest prawidłowa tylko wtedy, gdy dziennik debugowania jest również włączony.
- **NX_PPP_DEBUG_LOG_SIZE:** rozmiar dziennika debugowania (liczba wpisów w dzienniku debugowania). Po osiągnięciu ostatniego wpisu przechwycenie debugowania opakuje pierwszy wpis i zastąpi wszystkie wcześniej przechwycone dane. Wartość domyślna to 50.
- **NX_PPP_DEBUG_FRAME_SIZE:** maksymalna ilość danych przechwytywanych z odebranego ładunku pakietu i zapisywanych w danych wyjściowych debugowania. Wartość domyślna to 50.
- **NX_PPP_DISABLE_CHAP:** Jeśli jest zdefiniowana, wewnętrzna logika protokołu CHAP protokołu CHAP jest usuwana, łącznie z logiką skrótu MD5.
- **NX_PPP_DISABLE_PAP:** Jeśli została zdefiniowana, wewnętrzna logika PAP protokołu PPP jest usuwana.
- **NX_PPP_DNS_OPTION_DISABLE:** Jeśli zdefiniowano, opcja podstawowego serwera DNS jest wyłączona w odpowiedzi IPCP. Domyślnie ta opcja nie jest zdefiniowana.
- **NX_PPP_DNS_ADDRESS_MAX_RETRIES:** określa, ile razy host PPP zażąda adresu serwera DNS od elementu równorzędnego w stanie IPCP. Nie ma to wpływu, NX_PPP_DNS_OPTION_DISABLE jest zdefiniowany. Wartość domyślna to 2.
- **NX_PPP_HASHED_VALUE_SIZE:** określa rozmiar ciągów "wartości skrótu" używanych podczas uwierzytelniania protokołu CHAP. Wartość domyślna jest ustawiona na 16 bajtów, ale można ją ponownie zdefiniować przed dodaniem *nx_ppp.h.*
- **NX_PPP_MAX_LCP_PROTOCOL_RETRIES:** Określa maksymalną liczbę ponownych prób, jeśli przed wysłaniem kolejnego komunikatu żądania konfiguracji protokołu LCP użytą przez protokół PPP użytą wartość. Po osiągnięciu tej liczby uściślicie protokołu PPP zostanie przerwane, a stan połączenia będzie nieudany. Wartość domyślna to 20.
- **NX_PPP_MAX_PAP_PROTOCOL_RETRIES:** określa maksymalną liczbę ponownych prób, jeśli przed wysłaniem kolejnego komunikatu żądania uwierzytelnienia PAP zostanie uchyfy przez protokołu PPP. Po osiągnięciu tej liczby uściślicie protokołu PPP zostanie przerwane, a stan połączenia będzie nieudany. Wartość domyślna to 20.
- **NX_PPP_MAX_CHAP_PROTOCOL_RETRIES:** określa maksymalną liczbę ponownych prób, jeśli przed wysłaniem kolejnego komunikatu wyzwania protokołu CHAP zostanie użytą wartość maksymalną dla protokołu PPP. Po osiągnięciu tej liczby uściślicie protokołu PPP zostanie przerwane, a stan połączenia będzie nieudany. Wartość domyślna to 20.
- **NX_PPP_MAX_IPCP_PROTOCOL_RETRIES:** określa maksymalną liczbę ponownych prób, jeśli przed wysłaniem kolejnego komunikatu żądania konfiguracji protokołu IPCP zostanie użytą wartość maksymalną dla protokołu PPP. Po osiągnięciu tej liczby uściślicie protokołu PPP zostanie przerwane, a stan połączenia będzie nieudany. Wartość domyślna to 20.
- **NX_PPP_MRU:** określa maksymalną jednostkę odbioru (MRU) dla protokołu PPP. Domyślnie ta wartość to 1500 bajtów (wartość minimalna). Tę definicję można ustawić przez aplikację przed dodaniem *nx_ppp.h.*
- **NX_PPP_MINIMUM_MRU:** określa minimalną liczbę odebranych wartości MRU w komunikacie żądania konfiguracji LCP. Domyślnie ta wartość to 1500 bajtów (wartość minimalna). Tę definicję można ustawić przez aplikację przed dodaniem *nx_ppp.h.*
- **NX_PPP_NAME_SIZE:** określa rozmiar ciągów "name" używanych podczas uwierzytelniania. Wartość domyślna jest ustawiona na 32bytes, ale można ponownie zdefiniować przed dołączenia *nx_ppp.h.
- **NX_PPP_PASSWORD_SIZE:** określa rozmiar ciągów "password" używanych podczas uwierzytelniania. Wartość domyślna to 32 mb, ale można ją ponownie zdefiniować przed dodaniem *nx_ppp.h.*
- **NX_PPP_PROTOCOL_TIMEOUT:** Definiuje opcję oczekiwania (w sekundach), aby zadanie PPP odbierało odpowiedź na komunikat żądania protokołu PPP. Wartość domyślna to 4 sekundy.
- **NX_PPP_RECEIVE_TIMEOUTS:** Określa liczbę razy, gdy zadanie wątku PPP utknie w oczekiwaniu na otrzymanie następnego znaku w strumieniu komunikatów PPP. Następnie protokół PPP zwalnia pakiet i rozpoczyna oczekiwanie na otrzymanie następnego komunikatu PROTOKOŁU PPP. Wartość domyślna to 4.
- **NX_PPP_SERIAL_BUFFER_SIZE:** Określa rozmiar buforu szeregowego znaku odbierania. Domyślnie ta wartość to 3000 bajtów. Tę definicję można ustawić przez aplikację przed dodaniem *nx_ppp.h.*
- **NX_PPP_TIMEOUT:** definiuje opcję oczekiwania (w taktach czasomierza) na przydzielanie pakietów do przesyłania danych, a także buforowanie danych szeregowych PPP do pakietów do wysłania do warstwy IP. Wartość domyślna to 4*NX_IP_PERIODIC_RATE (400 takt).
- **NX_PPP_THREAD_TIME_SLICE:** Opcja wycinka czasu dla wątków PPP. Domyślnie ta wartość jest TX_NO_TIME_SLICE. Tę definicję można ustawić przez aplikację przed dodaniem *nx_ppp.h.*
- **NX_PPP_VALUE_SIZE:** określa rozmiar ciągów "value" używanych podczas uwierzytelniania protokołu CHAP. Wartość domyślna jest ustawiona na 32bytes, ale można ponownie zdefiniować przed dołączenia nx_ppp.h.