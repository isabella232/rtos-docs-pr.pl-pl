---
title: Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX Duo BSD
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika systemu Azure RTO NetX Duo BSD.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 582661bc66c51341fc098de9ff7b6fa2a7d746de
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822057"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-bsd"></a>Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX Duo BSD

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika systemu Azure RTO NetX Duo BSD.

## <a name="product-distribution"></a>Dystrybucja produktu

Usługę Azure RTO NetX Duo BSD można uzyskać z naszego publicznego repozytorium kodu źródłowego w lokalizacji [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) . Pakiet zawiera dwa pliki źródłowe i plik PDF, który zawiera ten dokument, w następujący sposób:

- **nxd_bsd. h**: plik nagłówkowy dla NetX Duo BSD
- plik źródłowy **nxd_bsd. c**: c dla NetX Duo BSD
- **nxd_bsd.pdf**: Podręcznik użytkownika dotyczący NetX Duo BSD

Pliki demonstracyjne:

- **bsd_demo_udp. c**
- **bsd_demo_tcp. c**
- **bsd_demo_raw. c**

## <a name="netx-duo-bsd-installation"></a>Instalacja BSD NetX Duo

Aby można było użyć NetX Duo BSD, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX Duo. Na przykład jeśli NetX Duo jest zainstalowana w katalogu "*\threadx\arm7\green*", wówczas pliki *nxd_bsd. h* i *nxd_bsd. c* powinny zostać skopiowane do tego katalogu.

## <a name="building-the-threadx-and-netx-duo-components-of-a-bsd-application"></a>Kompilowanie składników ThreadX i NetX Duo aplikacji BSD

### <a name="threadx"></a>ThreadX

Biblioteka ThreadX musi definiować `bsd_errno` w lokalnym magazynie wątków. Zalecamy wykonanie następującej procedury:

1. W *tx_port. h* Ustaw jeden z TX_THREAD_EXTENSION makr w następujący sposób:
   - `#define TX_THREAD_EXTENSION_3     int bsd_errno`

1. Skompiluj ponownie bibliotekę ThreadX.

> [!NOTE]
> Jeśli TX_THREAD_EXTENSION_3 jest już używany, użytkownik może korzystać z jednego z innych TX_THREAD_EXTENSION makr.

### <a name="netx-duo"></a>NetX Duo

Przed rozpoczęciem korzystania z usług BSD NetX Duo należy skompilować bibliotekę NetX Duo przy użyciu zdefiniowanych NX_ENABLE_EXTENDED_NOTIFY_SUPPORT. Domyślnie nie jest on zdefiniowany. Jeśli wykorzystano gniazda BSD RAW, biblioteka NetX Duo musi być skompilowana przy użyciu zdefiniowanych NX_ENABLE_IP_RAW_PACKET_FILTER.

## <a name="using-netx-duo-bsd"></a>Korzystanie z NetX Duo BSD

Projekt aplikacji BSD NetX Duo musi zawierać *nxd_bsd. h* , który zawiera *tx_api. h* i *nx_api. h* , aby można było korzystać z usług BSD określonych w dalszej części tego przewodnika. Aplikacja musi również zawierać *nxd_bsd. c* w procesie kompilacji. Ten plik musi być skompilowany w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone wraz z plikami aplikacji. To wszystko, co jest wymagane do korzystania z NetX Duo BSD.

Aby można było korzystać z usług NetX Duo BSD, aplikacja musi utworzyć wystąpienie IP, utworzyć pulę pakietów dla warstwy BSD do przydzielania pakietów z, przydzielić miejsce na pamięć dla wewnętrznego stosu wątków BSD i określić priorytet wewnętrznego wątku BSD. Warstwa BSD jest inicjowana przez wywołanie *bsd_initialize* i przekazanie parametrów. Przedstawiono to w "małych przykładach" w dalszej części tego dokumentu, ale prototyp jest przedstawiony poniżej:

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                    *CHAR *bsd_thread_stack_area,
                    *ULONG bsd_thread_stack_size,
                    *UINT bsd_thread_priority*);
```

Default_ip jest wystąpieniem IP, na którym działa warstwa BSD. Default_pool jest używany przez usługi firmy BSD do przydzielania pakietów z programu. Poniższe dwa parametry: bsd_thread_stack_area, bsd_thread_stack_size definiuje obszar stosu używany przez wewnętrzny wątek BSD, a ostatni parametr, bsd_thread_priority, ustawia priorytet wątku.

## <a name="netx-duo-bsd-raw-socket-support"></a>Obsługa NetX Duo BSD RAW Socket

NetX Duo BSD obsługuje również niesformatowane gniazda. Aby można było używać gniazd surowych w NetX Duo BSD, biblioteka NetX Duo musi być skompilowana przy użyciu zdefiniowanej NX_ENABLE_IP_RAW_PACKET_FILTER. Domyślnie nie jest on zdefiniowany. Aplikacja musi następnie włączyć przetwarzanie nieprzetworzonego gniazda dla utworzonego wcześniej wystąpienia adresu IP przez wywołanie *nx_ip_raw_packet_enable.*

Aby utworzyć nieprzetworzony gniazdo w NetX Duo BSD, aplikacja używa gniazda Create Service *Socket* i określa rodzinę protokołów, typ gniazda i protokół:

```c
sock_1 = socket(INT protocolFamily, INT socket_type, INT protocol)
```

protocolFamily jest AF_INET dla gniazd IPv4 lub AF_INET6 dla gniazd IPv6, przy założeniu, że w wystąpieniu IP jest włączony protokół IPv6. Socket_type musi być ustawiona na SOCK_RAW. Protokół jest specyficzny dla aplikacji.

Aby wysyłać i odbierać pakiety pierwotne oraz zamykać niesformatowane gniazdo, aplikacja zwykle używa tych samych usług BSD jak dla protokołu UDP, np. *SendTo, recvfrom, Select* i *soc_close*. Gniazda RAW nie obsługują *akceptowania* ani *nasłuchiwania* usług BSD.

- Domyślnie odebrane dane pierwotne IPv4 zawierają nagłówek IPv4.  Z drugiej strony odebrane dane pierwotne IPv6 nie obejmują nagłówka IPv6.

- Domyślnie podczas wysyłania pierwotnych pakietów IPv6 lub IPv4 warstwa otoki BSD dodaje nagłówek IPv6 lub IPv4 przed wysłaniem danych.

NetX Duo BSD obsługuje dodatkowe niesformatowane Opcje gniazda, w tym IP_RAW_RX_NO_HEADER, IP_HDRINCL i IP_RAW_IPV6_HDRINCL.

Jeśli ustawiono IP_RAW_RX_NO_HEADER, nagłówek IPv4 zostanie usunięty, tak że odebrane dane nie zawierają nagłówka IPv4, a raportowana długość komunikatu nie zawiera nagłówka IPv4.  W przypadku usługi IPv6 Sockets domyślnie nieprzetworzony dostęp do gniazda nie zawiera nagłówka IPv6, równoważne z ustawioną opcją IP_RAW_RX_NO_HEADER. Aplikacja może użyć usługi *SetSockOpt* do wyczyszczenia opcji IP_RAW_RX_NO_HEADER, gdy opcja IP_RAW_RX_NO_HEADER zostanie wyczyszczona, odebrane dane pierwotne IPv6 będą zawierać nagłówek IPv6, a raportowana długość komunikatu zawiera nagłówek IPv6.

Ta opcja nie ma wpływu na dane przesyłane przez protokół IPv4 lub IPv6.

Jeśli ustawiono IP_HDRINCL, aplikacja zawiera nagłówek IPv4 podczas wysyłania danych.  Ta opcja nie ma wpływu na przesyłanie IPv6 i nie jest domyślnie zdefiniowana. Jeśli ustawiono IP_RAW_IPV6_HDRINCL, aplikacja zawiera nagłówek IPv6 podczas wysyłania danych.  Ta opcja nie ma wpływu na transmisję IPv4 i nie jest domyślnie zdefiniowana.

IP_HDRINCL i IP_RAW_IPV6_HDRINCL nie mają wpływu na odbieranie protokołu IPv4 lub IPv6.

> [!NOTE]
> Specyfikacja gniazda BSD 4,3 określa, że jądro musi skopiować pakiet pierwotny do każdego buforu odbioru gniazda. Jednak w NetX Duo BSD, jeśli utworzono wiele gniazd współużytkujących ten sam protokół, zachowanie jest niezdefiniowane.

## <a name="netx-duo-bsd-raw-packet-support"></a>Obsługa pakietów NetX Duo BSD RAW

Aby włączyć obsługę pakietów nieprzetworzonych dla protokołu PPPoE, NetX Duo BSD muszą zostać skompilowane z włączonym NX_BSD_RAW_PPPOE_SUPPORT.

Następujące polecenie tworzy gniazdo BSD do obsługi pierwotnych pakietów PPPoE:

```c
Sockfd = socket(AF_PACKET, SOCK_RAW, protocol);
```

Bieżąca implementacja BSD obsługuje tylko dwa typy protokołów w rodzinie AF_PACKET

- `ETHERTYPE_PPPOE_DISC`: Pakiety odnajdywania PPPoE. W ramce danych MAC pakiety odnajdywania mają typ ramki Ethernet 0x8863.

- `ETHERTYPE_PPPOE_SESS`: Pakiety sesji PPP. W ramce danych MAC pakiety sesji mają typ ramki Ethernet 0x8864.

Struktura `sockaddr_ll` służy do określania parametrów podczas wysyłania lub otrzymywania ramek PPPoE.

`struct sockaddr_ll` jest zadeklarowany jako:

```c
struct sockaddr_ll
{
    USHORT  sll_family;     /* Must be AF_PACKET */
    USHORT  sll_protocol;   /* LL frame type */
    INT     sll_ifindex;    /* Interface Index. */
    USHORT  sll_hatype;     /* Header type */
    UCHAR   sll_pkttype;    /* Packet type */
    UCHAR   sll_halen;      /* Length of address */
    UCHAR   sll_addr[8];    /* Physical layer address */
};
```

> [!NOTE]
> Nie każde pole w strukturze jest używane przez `sendto()` lub `recvfrom()` . Zapoznaj się z opisem poniżej, jak skonfigurować na `sockaddr_ll` potrzeby wysyłania i otrzymywania pakietów PPPoE.

Gniazda utworzonego w ramach rodziny AF_PACKET mogą być używane do wysyłania pakietów odnajdywania PPPoE lub pakietów sesji PPP, niezależnie od określonego protokołu. Podczas przesyłania pakietu PPPoE aplikacja musi przygotować bufor zawierający prawidłowo sformatowaną ramkę PPPoE, w tym nagłówki MAC (docelowy adres MAC, źródłowy adres MAC i typ ramki). Rozmiar buforu zawiera 14-bajtowy nagłówek Ethernet.

`sockaddr_ll`Struktura `sll_ifindex` jest używana do wskazania interfejsu fizycznego, który ma być używany do wysyłania tego pakietu. Pozostałe pola w strukturze nie są używane. Wartości ustawione na nieużywane pola są ignorowane przez proces wewnętrzny BSD.

Poniższy blok kodu ilustruje, jak przesłać pakiet PPPoE:

```c
struct sockaddr_ll peer_addr;

/* Transmit a PPPoE frame using the primary network interface. */
peer_addr.sll_ifindex = 0;
n = sendto(sockfd, frame, frame_size, 0, (struct
        sockaddr*)&peer_addr, sizeof(peer_addr));
```

Wartość zwracana wskazuje liczbę przesłanych bajtów. Ponieważ pakiety PPPoE są oparte na komunikatach, w przypadku pomyślnej transmisji liczba wysłanych bajtów jest zgodna z rozmiarem pakietu, łącznie z 14-bajtowym nagłówkiem Ethernet.

Pakiety PPPoE można odbierać przy użyciu polecenia `recvfrom()` . Bufor odbioru musi być wystarczająco duży, aby pomieścić komunikat o rozmiarze MTU sieci Ethernet. Odebrany pakiet PPPoE zawiera 14-bajtowy nagłówek Ethernet. W przypadku odbierania pakietów PPPoE pakiety odnajdywania PPPoE mogą być odbierane tylko przez gniazdo utworzone za pomocą protokołu `ETHERTYPE_PPPOE_DISC` . Podobnie pakiety sesji PPP mogą być odbierane tylko przez gniazdo utworzone za pomocą protokołu `ETHERTYPE_PPPOE_SESS` . Jeśli dla tego samego typu protokołu utworzono wiele gniazd, przychodzące pakiety PPPoE są przekazywane do gniazda utworzonego jako pierwsze. Jeśli pierwsze gniazdo utworzone dla protokołu jest zamknięte, do otrzymywania tych pakietów jest używane następne gniazdo w kolejności tworzenia.

Po odebraniu pakietu PPPoE następujące pola w `sockaddr_ll` strukturze są prawidłowe:
- **sll_family**: Ustaw przez wewnętrzną wartość właściwości BSD do AF_PACKET
- **sll_ifindex**: wskazuje interfejs, z którego został odebrany pakiet
- **sll_protocol**: Ustaw typ odebranego pakietu: `ETHERTYPE_PPPOE_DISC` lub `ETHERTYPE_PPPOE_SESS`

## <a name="eliminating-internal-bsd-thread"></a>Eliminowanie wewnętrznego wątku BSD

Domyślnie firma BSD używa wewnętrznego wątku do wykonywania niektórych operacji przetwarzania. W systemach z ograniczeniami pamięci, BSD można skompilować przy użyciu zdefiniowanych NX_BSD_TIMEOUT_PROCESS_IN_TIMER, co eliminuje wewnętrzny wątek BSD, a zamiast tego używa wewnętrznego czasomierza do przeprowadzenia tego samego przetwarzania. Eliminuje to pamięć wymaganą dla wewnętrznego bloku sterowania i stosu kontrolki wątku BSD. Jednak znacznie zwiększono przetwarzanie czasomierza, a przetwarzanie BSD może być wykonywane z wyższym priorytetem niż trzeba.

Aby skonfigurować gniazda BSD do uruchamiania w kontekście czasomierza ThreadX, zdefiniuj NX_BSD_TIMEOUT_PROCESS_IN_TIMER w *nxd_bsd. h*. Jeśli warstwa BSD jest skonfigurowana do wykonywania zadań BSD w kontekście czasomierza, w wywołaniu *bsd_initialize*, następujące trzy parametry są ignorowane i powinny mieć wartość null:

- **bsd_thread_stack_area**
- **bsd_thread_stack_size**
- **bsd_thread_priority**

## <a name="netx-duo-bsd-with-dns-support"></a>NetX Duo BSD z obsługą systemu DNS

Jeśli NX_BSD_ENABLE_DNS jest zdefiniowany, NetX Duo BSD może wysyłać zapytania DNS w celu uzyskania informacji o nazwie hosta lub adresie IP hosta. Ta funkcja wymaga, aby klient NetX DNS był wcześniej tworzony przy użyciu usługi *nx_dns_create* . Co najmniej jeden znany adres IP serwera DNS musi być zarejestrowany w wystąpieniu usługi DNS przy użyciu usługi *nx_dns_server_add* do dodawania adresów serwera IPv4 lub przy użyciu usługi *nxd_dns_server_add* do dodawania adresów IPv4 lub IPv6.

Usługi systemu DNS i alokacja pamięci są używane przez usługi *Getaddrinfo* i *getnameinfo* :

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
        const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
        char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

Gdy aplikacja BSD wywołuje *Getaddrinfo* z nazwą hosta, NetX BSD wywoła następujące usługi, aby uzyskać adres IP:

- **nx_dns_ipv4_address_by_name_get**
- **nxd_dns_ipv6_address_by_name_get**
- **nx_dns_cname_get**

W przypadku *nx_dns_ipv4_address_by_name_get* i *NXD_DNS_IPV6_ADDRESS_BY_NAME_GET*, NetX BSD używa odpowiednio ipv4_addr_buffer i ipv6_addr_buffer obszarów pamięci. Rozmiar tych buforów jest definiowany odpowiednio przez (NX_BSD_IPV4_ADDR_PER_HOST * 4) i (NX_BSD_IPV6_ADDR_PER_HOST * 16).

W przypadku zwracania informacji o adresie z *Getaddrinfo*, NetX BSD używa tabeli pamięci blokowej ThreadX nx_bsd_addrinfo_pool_memory, której obszar pamięci jest zdefiniowany przez inny zestaw konfigurowalnych opcji, NX_BSD_IPV4_ADDR_MAX_NUM i NX_BSD_IPV6_ADDR_MAX_NUM.

Aby uzyskać szczegółowe informacje na temat powyższych opcji konfiguracji, zobacz **Ogólne opcje konfiguracji** .

Ponadto jeśli NX_DNS_ENABLE_EXTENDED_RR_TYPES jest zdefiniowana, a dane wejściowe hosta są nazwą kanoniczną, NetX Duo BSD przydzieli pamięć dynamicznie z wcześniej utworzonej puli blokowej "_nx_bsd_cname_block_pool

> [!NOTE]
> Po wywołaniu *Getaddrinfo* aplikacja BSD jest odpowiedzialna za zwolnienie pamięci wskazywanej przez argument res z powrotem do tabeli blokowej przy użyciu usługi *freeaddrinfo* .

## <a name="netx-duo-bsd-limitations"></a>Ograniczenia BSD NetX Duo

Ze względu na problemy z wydajnością i architekturą NetX Duo BSD nie obsługuje wszystkich funkcji gniazda BSD 4,3:

Flagi INT nie są obsługiwane dla wywołań *send, recv, SendTo* i *recvfrom* .

## <a name="general-configuration-options"></a>Ogólne opcje konfiguracji

Opcje konfigurowalne przez użytkownika w *nxd_bsd. h* pozwalają aplikacji dostroić NetX Duo dla określonych wymagań aplikacji.

Poniżej znajduje się lista konfigurowalnych opcji ustawionych w czasie kompilacji:

- **NX_BSD_TCP_WINDOW**: używany w wywołaniach tworzenia gniazda TCP. 64 KB to typowy rozmiar okna dla sieci Ethernet 100 MB. Wartość domyślna to 65535.

- **NX_BSD_SOCKFD_START**: jest to logiczny indeks dla wartości początkowej deskryptora pliku gniazda BSD. Domyślnie ta opcja to 32.

- **NX_BSD_MAX_SOCKETS**: określa maksymalną liczbę gniazd dostępnych w warstwie BSD i musi być wielokrotnością 32. Wartość domyślna to 32.

- **NX_BSD_SOCKET_QUEUE_MAX**: określa maksymalną liczbę pakietów UDP przechowywanych w kolejce odbierania. Wartość jest domyślnie równa 5.

- **NX_BSD_MAX_LISTEN_BACKLOG**: Określa rozmiar kolejki nasłuchu ("zaległości") dla gniazd TCP BSD. Wartość domyślna to 5.

- **NX_MICROSECOND_PER_CPU_TICK**: określa liczbę mikrosekund na cykl czasomierza harmonogramu.

- **NX_BSD_TIMEOUT**: określa limit czasu w taktach czasomierza dla wywołań wewnętrznych NetX Duo wymaganych przez BSD. Wartość domyślna to (20 * NX_IP_PERIODIC_RATE).

- **NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: określa limit czasu w taktach czasomierza dla wywołania rozłączenia NetX Duo. Wartość domyślna to 1.

- **NX_BSD_PRINT_ERRORS**: w przypadku ustawienia zwracany stan błędu funkcji BSD zwraca numer wiersza i typ błędu, np. NX_SOC_ERROR wystąpienia błędu. Wymaga to od deweloperów aplikacji zdefiniowania danych wyjściowych debugowania. Ustawienie domyślne jest wyłączone i nie określono danych wyjściowych debugowania w *nxd_bsd. h*.

- **NX_BSD_TIMER_RATE**: interwał, po którym uruchamiane jest zadanie okresowego czasomierza BSD. Wartość domyślna to 1 sekunda (1 * NX_IP_PERIODIC_RATE).

- **NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: w przypadku ustawienia ta opcja umożliwia wykonanie procesu limitu czasu BSD w kontekście czasomierza systemu. Zachowanie domyślne jest wyłączone. Ta funkcja została szczegółowo opisana w rozdziale 2 "Instalacja i korzystanie z NetX Duo BSD".

- **NX_BSD_RAW_PPPOE_SUPPORT**: Włącz obsługę pakietów pierwotnych PPPoE. Domyślnie ta opcja nie jest włączona.

- **NX_BSD_ENABLE_DNS**: Jeśli ta funkcja jest włączona, NetX Duo BSD wyśle zapytanie DNS dla nazwy hosta lub adresu IP hosta. Wymaga wcześniejszego utworzenia i uruchomienia wystąpienia klienta DNS. Domyślnie nie jest włączona.

- **NX_BSD_SOCKET_RAW_PROTOCOL_TABLE_SIZE**: Określa rozmiar nieprzetworzonej tabeli gniazda. Wartość musi być potęgą liczby dwa. NetX BSD tworzy tablicę gniazd typu NX_BSD_SOCKETS do wysyłania i otrzymywania pakietów raw. Należy włączyć NX_ENABLE_IP_RAW_PACKET_FILTER. Domyślnie jest to 32.

- **NX_BSD_IPV4_ADDR_MAX_NUM**: Maksymalna liczba adresów IPv4 zwróconych przez *Getaddrinfo*. Dzięki NX_BSD_IPV6_ADDR_MAX_NUM definiuje rozmiar puli bloku NetX BSD nx_bsd_addrinfo_block_pool do dynamicznego przydzielania pamięci do przechowywania informacji w *Getaddrinfo*. Wartość domyślna to 5.

- **NX_BSD_IPV6_ADDR_MAX_NUM**: Maksymalna liczba adresów IPv6 zwróconych przez *Getaddrinfo*. Dzięki NX_BSD_IPV4_ADDR_MAX_NUM definiuje rozmiar puli bloku NetX BSD nx_bsd_addrinfo_block_pool do dynamicznego przydzielania pamięci do przechowywania informacji w *Getaddrinfo*.

- **NX_BSD_IPV4_ADDR_PER_HOST**: określa maksymalną liczbę adresów IPv4 przechowywanych dla kwerendy DNS. Wartość domyślna to 5.

- **NX_BSD_IPV6_ADDR_PER_HOST**: określa maksymalne adresy IPv6 przechowywane dla kwerendy DNS. Wartość domyślna to 2.

## <a name="bsd-socket-options"></a>Opcje gniazda BSD

Poniższa lista opcji gniazda BSD NetX Duo można włączyć (lub wyłączyć) w czasie wykonywania dla poszczególnych gniazd przy użyciu usługi *SetSockOpt* :

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, 
                const void *option_value, INT option_length);
```

Istnieją dwa różne ustawienia dla option_level.

Pierwszy typ opcji gniazda czasu wykonywania jest SOL_SOCKET dla opcji poziomu gniazda. Aby włączyć opcję poziomu gniazda, należy wywołać *setsockopt* option_level z ustawionym na SOL_SOCKET, a option_name ustawić dla konkretnej opcji, np. SO_BROADCAST *.* Aby pobrać ustawienie opcji, wywołaj *getsockopt* dla option_name z option_level ponownie ustawiona na SOL_SOCKET.

Zostanie wyświetlona lista opcji poziomu gniazda w czasie wykonywania poniżej.

- **SO_BROADCAST**: ustawienie umożliwia wysyłanie i otrzymywanie pakietów emisji z gniazd NetX. Jest to domyślne zachowanie dla NetX Duo. Wszystkie gniazda mają tę możliwość.

- **SO_ERROR**: służy do uzyskiwania stanu gniazda dla operacji poprzedniej gniazda określonego gniazda przy użyciu usługi *getsockopt* . Wszystkie gniazda mają tę możliwość.

- **SO_KEEPALIVE**: ustawienie powoduje włączenie funkcji utrzymywania aktywności protokołu TCP. Wymaga to, aby Biblioteka NetX Duo była skompilowana przy użyciu NX_TCP_ENABLE_KEEPALIVE zdefiniowanej w *nx_user. h*. Domyślnie ta funkcja jest wyłączona.

- **SO_RCVTIMEO**: ustawia opcję oczekiwania w sekundach dla pakietów odbieranych w NetX Duo BSD Sockets. Wartość domyślna to NX_WAIT_FOREVER (0xFFFFFFFF) lub, jeśli jest włączony bez blokowania, NX_NO_WAIT (0x0).

- **SO_RCVBUF**: Określa rozmiar okna gniazda TCP. Wartość domyślna NX_BSD_TCP_WINDOW jest ustawiona na 64 KB w przypadku pakietów BSD TCP Sockets. Aby ustawić rozmiar ponad 65535 wymaga skompilowania biblioteki NetX Duo z NX_TCP_ENABLE_WINDOW_SCALING być zdefiniowana.

- **SO_REUSEADDR**: ustawienie umożliwia zmapowanie wielu gniazd na jeden port. Typowy sposób użycia dotyczy gniazda serwera TCP. Jest to domyślne zachowanie NetX Duo.

Drugim typem opcji gniazda czasu wykonywania jest poziom opcji IP. Aby włączyć opcję poziomu IP, należy wywołać *setsockopt* option_level z ustawionym na IP_PROTO, a option_name ustawić opcję na np. IP_MULTICAST_TTL *.* Aby pobrać ustawienie opcji, wywołaj *getsockopt* dla option_name z option_level ponownie ustawiona na IP_PROTO.

Zostanie wyświetlona lista opcji poziomu adresu IP czasu wykonywania poniżej.

- **IP_MULTICAST_TTL**: służy do ustawiania czasu wygaśnięcia dla gniazd UDP. Wartość domyślna to NX_IP_TIME_TO_LIVE (0x80) podczas tworzenia gniazda. Tę wartość można zastąpić, wywołując *SetSockOpt* z tą opcją gniazda.

- **IP_RAW_IPV6_HDRINCL**: Jeśli ta opcja jest ustawiona, aplikacja wywołująca musi dołączyć nagłówek IPv6 i opcjonalne nagłówki aplikacji do danych przesyłanych w przypadku nieprzetworzonych gniazd IPv6 utworzonych przez BSD. Aby można było użyć tej opcji, w zadaniu adresu IP musi być włączone przetwarzanie nieprzetworzonego gniazda.

- **IP_ADD_MEMBERSHIP**: Jeśli ta opcja jest ustawiona, w celu przyłączenia do określonej grupy IGMP gniazdo BSD (dotyczy tylko gniazd UDP).

- **IP_DROP_MEMBERSHIP**: w przypadku ustawienia, ta opcja włącza gniazdo BSD (dotyczy tylko gniazd UDP), aby opuścić określoną grupę IGMP.

- **IP_HDRINCL**: Jeśli ta opcja jest ustawiona, aplikacja wywołująca musi dołączyć nagłówek IP i opcjonalne nagłówki aplikacji do danych przesyłanych w przypadku nieprzetworzonych gniazd IPv4 utworzonych w programie BSD. Aby można było użyć tej opcji, w zadaniu adresu IP musi być włączone przetwarzanie nieprzetworzonego gniazda.

- **IP_RAW_RX_NO_HEADER**: Jeśli zostanie wyczyszczony, nagłówek IPv6 zostanie dołączony do odebranych danych dla nieprzetworzonych gniazd protokołu IPv6 utworzonych w systemie BSD. Nagłówki IPv6 są domyślnie usuwane w gniazdach BSD RAW IPv6 Sockets, a długość pakietu nie obejmuje nagłówka IPv6.

W przypadku ustawienia nagłówek IPv4 zostanie usunięty z odbierania danych w gniazdach BSD RAW typu IPv4. Nagłówki IPv4 są domyślnie uwzględniane w przypadku gniazd BSD RAW IPv4 i długość pakietu obejmuje nagłówek IPv4.

Ta opcja nie ma wpływu na dane transmisji IPv4 lub IPv6.

## <a name="small-ipv4-example"></a>Przykład małych adresów IPv4

Poniżej opisano przykład korzystania z usług BSD NetX Duo dla sieci IPv4. W tym przykładzie plik dołączany *nxd_bsd. h* jest wprowadzany w wierszu 8. Następnie *bsd_pool* *bsd_ip* wystąpienia adresu IP i puli pakietów są tworzone jako zmienne globalne w wierszu 20 i 21. Należy zauważyć, że w tej wersji demonstracyjnej jest wykorzystywany sterownik sieciowy pamięci RAM (wirtualnej)*_nx_ram_network_driver*. Klient i serwer będą współużytkować ten sam adres IP na pojedynczym wystąpieniu IP w tym przykładzie.

Wątki klienta i serwera są tworzone w wierszach 62 i 68. Pula pakietów BSD do przesyłania pakietów jest tworzona w wierszu 78 i używana w tworzeniu wystąpienia IP w wierszu 87. Zwróć uwagę, że zadanie wątku IP ma określony priorytet 1 w wywołaniu *nx_ip_create* . Ten wątek powinien być zadaniem o najwyższym priorytecie zdefiniowanym w programie w celu uzyskania optymalnej wydajności NetX.

Wystąpienie protokołu IP jest włączone dla usług ARP i TCP w wierszach 88 i 110. Ostatnim wymaganiem przed użyciem usług BSD jest wywołanie *bsd_initialize* w wierszu 120 w celu skonfigurowania wszystkich struktur danych i zasobów NetX i ThreadX wymaganych przez BSD.

Funkcja wprowadzania wątku serwera jest zdefiniowana dalej. Gniazdo TCP BSD jest tworzone w wierszu 149. Adres IP serwera i port są ustawiane w wierszach 160-163. Zwróć uwagę na użycie makr w kolejności bajtów sieci *htonl* i *htons* zastosowanych do adresu IP i portu. Jest to zgodne ze specyfikacją gniazda BSD, że dane wielobajtowe są przesyłane do usług BSD w kolejności bajtów sieciowych.

Następnie główne gniazdo serwera jest powiązane z portem przy użyciu usługi *bind* w wierszu 166. Jest to gniazdo nasłuchiwania dla żądań połączeń TCP korzystających z usługi *Listen* w wierszu 180. W tym miejscu funkcja wątek serwera *thread_server_entry*, pętle służące do sprawdzania odbierania zdarzeń przy użyciu wywołania *select* w wierszu 202. Jeśli zdarzenie Odbierz jest żądaniem połączenia, które jest określane przez porównanie listy gotowość do odczytu, wywołuje metodę *Accept* w wierszu 213. Podrzędne gniazdo serwera jest przypisane do obsługi żądania połączenia i dodawane do głównej listy gniazd serwera TCP podłączonych do klienta w wierszu 223. Jeśli nie ma nowych żądań połączeń, wątek serwera sprawdza wszystkie aktualnie połączone gniazda dla zdarzeń odbioru w pętli for, rozpoczynając od wiersza 236. W przypadku wykrycia zdarzenia odbierania, wywołuje on funkcję *send* i *Odbierz* dla tego gniazda, dopóki nie zostaną odebrane żadne dane (połączenie zamknięte po drugiej stronie), a gniazdo zostanie zamknięte przy użyciu usługi *soc_close* w wierszu 277.

Po skonfigurowaniu wątku serwera funkcja wprowadzania wątku klienta *thread_client_entry* tworzy gniazdo w wierszu 326 i łączy się z gniazdem serwera TCP przy użyciu połączenia *połączenia* w wierszu 337. Następnie tworzy pętlę, aby wysyłać i odbierać pakiety  przy użyciu *odpowiednio usług wysyłania i odbierania.* Gdy nie otrzymasz więcej danych, program zamknie gniazdo w wierszu 398 przy użyciu usługi *soc_close* . Po rozłączeniu funkcja wprowadzania wątku klienta tworzy nowe gniazdo TCP i wysyła kolejne żądanie połączenia w pętli while uruchomione w wierszu 321.

```c
/* This is a small demo of BSD Wrapper for the high-performance NetX Duo
TCP/IP stack which uses standard BSD services for TCP connection, sending,
and receiving using a simulated Ethernet driver. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nxd_bsd.h"
#include     <string.h>
#include     <stdlib.h>

#define     DEMO_STACK_SIZE     (16*1024)
#define     SERVER_PORT         87
#define     CLIENT_PORT         77

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_server;
TX_THREAD         thread_client;
NX_PACKET_POOL    bsd_pool;
NX_IP             bsd_ip;

/* Define some global data. */
CHAR     *msg0 = "Client 1:
    ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQR
    STUVWXYZ<>END";

INT     maxfd;

/* Define the counters used in the demo application... */

ULONG     error_counter;

/* Define fd_sets for the BSD server socket. */
fd_set     master_list, read_ready;

/* Define thread prototypes. */

VOID     thread_server_entry(ULONG thread_input);
VOID     thread_client_entry(ULONG thread_input);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */
int     main()
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

    /* Create a server thread. */
    tx_thread_create(&thread_server, "Server", thread_server_entry, 0,
                    pointer, DEMO_STACK_SIZE, 8, 8, TX_NO_TIME_SLICE,
                    TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Create a Client thread. */
    tx_thread_create(&thread_client, "Client", thread_client_entry, 0,
                    pointer, DEMO_STACK_SIZE, 16, 16, TX_NO_TIME_SLICE,
                    TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a BSD packet pool. */
    status = nx_packet_pool_create(&bsd_pool, "NetX BSD Packet Pool", 128,
                                pointer, 16384);

    pointer = pointer + 16384;
    if (status)
    {
        error_counter++;
        printf("Error in creating BSD packet pool\n!");
    }

    /* Create an IP instance for BSD. */
    status = nx_ip_create(&bsd_ip, "BSD IP Instance", IP_ADDRESS(1,2,3,4),
                    0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                    pointer, 2048, 1);
                    pointer = pointer + 2048;

    if (status)
    {
        error_counter++;
        printf("Error creating BSD IP instance\n!");
    }

    /* Enable ARP and supply ARP cache memory for BSD IP Instance */
    status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable ARP \n");
    }

    /* Enable TCP processing for BSD IP instances. */
    status = nx_tcp_enable(&bsd_ip);

    /* Check TCP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable TCP \n");
    }

    /* Now initialize BSD Scoket Wrapper */
    status = bsd_initialize (&bsd_ip, &bsd_pool,pointer, 2048, 2);
}

/* Define the Server thread. */
CHAR     Server_Rcv_Buffer[100];

VOID     thread_server_entry(ULONG thread_input)
{

INT       status, sock, sock_tcp_server;
ULONG     actual_status;
INT       Clientlen;
INT       i;
UINT      is_set = NX_FALSE;
struct    sockaddr_in serverAddr;
struct    sockaddr_in ClientAddr;

    tx_thread_sleep(100);

    status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE,
        &actual_status, 100);

    /* Check status... */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Create BSD TCP Socket */
    sock_tcp_server = socket(AF_INET, SOCK_STREAM, 0);

    if (sock_tcp_server == -1)
    {
        printf("Error on Server socket %d create \n", sock_tcp_server);
        return;
    }

    printf("Server socket %d created\n", sock_tcp_server);

    /* Set the server port and IP address */
    memset(&serverAddr, 0, sizeof(serverAddr));
    serverAddr.sin_family = AF_INET;
    serverAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    serverAddr.sin_port = htons(SERVER_PORT);

    /* Bind this server socket */
    status = bind (sock_tcp_server, (struct sockaddr *) &serverAddr,
                sizeof(serverAddr));

    if (status < 0)
    {
        printf("Error on Server Socket %d Bind \n", sock_tcp_server);
        return;
    }

    FD_ZERO(&master_list);
    FD_ZERO(&read_ready);
    FD_SET(sock_tcp_server,&master_list);
    maxfd = sock_tcp_server;

    /* Now listen for any client connections for this server socket */
    status = listen (sock_tcp_server, 5);
    if (status < 0)
    {
        printf("Error on Server Socket %d Listen\n", sock_tcp_server);
        return;
    }
    else
        printf("Server socket %d listen complete\n", sock_tcp_server);

    /* All set to accept client connections */

    /* Loop to create and establish server connections. */
    while(1)
    {

        printf("\n");

        read_ready = master_list;

        tx_thread_sleep(20); /* Allow some time to other threads too */

        /* Let the underlying TCP stack determine the timeout. */
        status = select(maxfd + 1, &read_ready, 0, 0, 0);

        if ((status == 0xFFFFFFFF) || (status == 0))
        {

            printf("Error with select. Status 0x%x\n", status);

            continue;
        }

        /* Check for a connection request. */
        is_set = FD_ISSET(sock_tcp_server, &read_ready);

        if(is_set)
        {

            Clientlen = sizeof(ClientAddr);

            sock = accept(sock_tcp_server,(struct sockaddr*)&ClientAddr,
                        &Clientlen);

            /* Add this new connection to our master list */
            FD_SET(sock, &master_list);

            if ( sock \maxfd)
            {

                maxfd = sock;
            }

            continue;
        }

        /* Check the set of 'ready' sockets, e.g connected to remote host and
        waiting for notice of packets received. */
        for (i = NX_BSD_SOCKFD_START; i < (maxfd+1+NX_BSD_SOCKFD_START); i++)
        {

            if ((i != sock_tcp_server) &&
                (FD_ISSET(i , &master_list)) &&
                (FD_ISSET(i , &read_ready)))
            {

                while(1)
                {

                    status = recv(i, (VOID *)Server_Rcv_Buffer, 100, 0);

                    if (status == 0)
                    {
                        printf("(Server received no data from Client on
                            socket %d)\n", i);
                        break;
                    }
                    else if (status == NX_SOC_ERROR)
                    {
                        printf("Error on Server receiving data from Client on
                            socket %d\n", i);
                        break;
                    }
                    if(status == SERVER_RCV_BUFFER_SIZE) status--;
                    Server_Rcv_Buffer[status] = 0;
                    printf("Server socket %d received %d bytes: %s\n ",
                            i, (ULONG)status, Server_Rcv_Buffer);

                    status = send(i, "Hello\n", sizeof("Hello\n"), 0);

                    if (status == NX_SOC_ERROR)
                    {
                        printf("Error on Server socket %d sending data to
                        Client\n", i);
                    }
                    else
                    {
                        printf("Server socket %d message sent to Client:
                        Hello\n", i);
                    }
                }

                /* Close this socket */
                status = soc_close(i);

                if (status != NX_SOC_ERROR)
                {
                    printf("Server socket %d closed \n", i);
                }
                else
                {
                    printf("Error on closing Server socket %d \n", i);
                }
            }
        }

    /* Loop back to check any next client connection */
    }
}

CHAR     Client_Rcv_Buffer[100];

VOID     thread_client_entry(ULONG thread_input)
{

INT        status;
INT        sock_tcp_client, length;
struct     sockaddr_in echoServAddr;
struct     sockaddr_in localAddr; /

    /* Let the server side get set up. */
    tx_thread_sleep(200);

    /* Set local port for displaying IP address and port. */
    memset(&localAddr, 0, sizeof(localAddr));
    localAddr.sin_family = AF_INET;
    localAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    localAddr.sin_port = htons(CLIENT_PORT);

    /* Set server port and IP address which we need to connect. */
    memset(&echoServAddr, 0, sizeof(echoServAddr));
    echoServAddr.sin_family = AF_INET;
    echoServAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    echoServAddr.sin_port = htons(SERVER_PORT);

    /* Now make client connections with the server. */
    while (1)
    {

        printf("\n");

        /* Create BSD TCP Socket */
        sock_tcp_client = socket( AF_INET, SOCK_STREAM, 0);

        if (sock_tcp_client == -1)
        {
            printf("Error on Client socket %d create \n", sock_tcp_client);
            return;
        }

        printf("Client socket %d created\n", sock_tcp_client);

        /* Now connect this client to the server */
        status = connect(sock_tcp_client, (struct sockaddr *)&echoServAddr,
                        sizeof(echoServAddr));

        /* Check for error. */
        if (status != OK)
        {
            printf("Error on Client socket %d connect\n", sock_tcp_client);
                    soc_close(sock_tcp_client);
            return;
        }

        /* Get and print source and destination information */
        printf("Client socket %d connected \n", sock_tcp_client);

        status = getsockname(sock_tcp_client, (struct sockaddr *)&localAddr,
                            &length);

        printf("Client port = %lu , Client = 0x%x,",
            htonl(localAddr.sin_port), htonl(localAddr.sin_addr.s_addr));

        length = sizeof(struct sockaddr_in);

        status = getpeername( sock_tcp_client, (struct sockaddr *)
                            &echoServAddr, &length);

        printf("Remote port = %lu, Remote IP = 0x%x \n",
                htonl(echoServAddr.sin_port),
                htonl(echoServAddr.sin_addr.s_addr));

        /* Now receive the echoed packet from the server */
        while(1)
        {

            printf("Client sock %d sending packet to server\n",
            sock_tcp_client);

            status = send(sock_tcp_client, "Hello", (sizeof("Hello")), 0);

            if (status == ERROR)
            {
                printf("Error: Client Socket (%d) send \n", sock_tcp_client);
            }
            else
            {
                printf("Client socket %d sent message Hello\n",
                        sock_tcp_client);
            }

            status = recv(sock_tcp_client, (VOID *)Client_Rcv_Buffer,100,0);

            if (status <= 0)
            {

                if (status < 0)
                {
                    380 printf("Error on Client receiving on socket %d \n",
                            sock_tcp_client);
                }
                else
                {
                    printf("Nothing received by Client on socket %d\n",
                            sock_tcp_client);
                }

                break;
            }
            else
            {
                printf("Client socket %d received %d bytes: %s\n",
                        sock_tcp_client,
                        status, Client_Rcv_Buffer);
            }

        }

        /* close this client socket */
        status = soc_close(sock_tcp_client);

        if (status != ERROR)
        {
            printf("Client Socket %d closed\n", sock_tcp_client);
        }
        else
        {
            printf("Error on Client Socket %d on close \n", sock_tcp_client);
        }

        /* Make another Client connection...*/

    }
}
```

## <a name="small-ipv6-example-system"></a>Mały system przykładowych adresów IPv6

Przykład sposobu korzystania z usług BSD NetX Duo dla sieci IPv6 jest opisany w programie poniżej. Ten przykład jest bardzo podobny do programu demonstracyjnego protokołu IPv4, który został wcześniej opisany przy użyciu kilku ważnych różnic.

Wątki klienta i serwera, Pula pakietów BSD, wystąpienie protokołu IP i Inicjowanie BSD odbywają się tak, jak w przypadku protokołu IPv4 BSD.

W funkcji wprowadzania wątku serwera *thread_server_entry* definiuje kilka zmiennych IPv6 przy użyciu *sockaddr_in6* i *NXD_ADDRESS* typów danych w wierszach 145-148. Typ danych NXD_ADDRESS może w rzeczywistości przechowywać typy adresów IPv4 i IPv6.

Następnie wątek serwera włącza protokół IPv6 i ICMPv6 w wystąpieniu IP przy użyciu usług *nxd_ipv6_enable* i *nxd_icmpv6_enable* odpowiednio w wierszu 161 i 169. Następnie lokalne i globalne adresy IP są rejestrowane przy użyciu wystąpienia adresu IP. Odbywa się to za pomocą usługi *nxd_ipv6_address_set* w wierszach 180 i 195. Następnie w trybie uśpienia jest wystarczająco dużo miejsca, aby zadanie wątku IP zakończyło protokół wykrywania zduplikowanych adresów i zarejestrować te adresy jako prawidłowe adresy w *tx_thread_sleep* wywołaniu w wierszu 201.

Następnie gniazdo serwera TCP jest tworzone z argumentem wejściowym typu gniazdo AF_INET6 w wierszu 204. Adres IPv6 i port gniazda są ustawiane w wierszach 216-221, a następnie w przypadku używania makr *htonl* i *htons* do umieszczania danych w kolejności bajtów sieciowych dla usług BSD Sockets. W tym miejscu funkcja wprowadzania wątku serwera jest niemal identyczna z przykładem IPv4.

Funkcja wprowadzania wątku klienta, *thread_client_entry*, została zdefiniowana dalej. Należy zauważyć, że ponieważ klient TCP w tym przykładzie współużytkuje to samo wystąpienie IP i adres IPv6 co serwer TCP, nie musi ponownie włączać usług IPv6 ani ICMPv6 w wystąpieniu IP. Ponadto adres IPv6 jest już zarejestrowany w wystąpieniu adresu IP. Zamiast tego funkcja wprowadzania wątku klienta po prostu czeka na wiersz 368, aby skonfigurować serwer. Adres serwera i port są ustawiane, przy użyciu makr hosta do kolejności bajtów sieciowych w wierszach 387-392, a następnie klient może połączyć się z serwerem TCP w wierszu 412. Należy pamiętać, że typy danych lokalnego adresu IP w wierszach 378-383 są używane tylko w celu przedstawienia usług *getsockname* i *getpeername* w wierszach 425 i 434 odpowiednio. Ze względu na to, że dane pochodzą z sieci, w sieci można hostować makra kolejności bajtów używane w wierszach 378-383.

Kolejna funkcja wprowadzania wątku klienta wprowadza pętlę, w której tworzony jest gniazdo TCP, sprawia, że połączenie TCP i wysyła i odbiera dane z serwerem TCP, dopóki nie zostanie odebrane praktycznie więcej danych, jak w przypadku przykładu IPv4. Następnie zamyka gniazdo w wierszu 483, wstrzymuje się krótko i tworzy kolejne gniazdo TCP i żąda połączenia z serwerem TCP.

Jedną z ważnych różnic przy użyciu protokołu IPv4 jest to, że wywołania *gniazda* określają gniazdo IPv6 przy użyciu argumentu AF_INET6 Input. Kolejną istotną różnicą jest to, że wywołanie *połączenia* klienta TCP pobiera *sockaddr_in6* typ danych, a argument długości ma ustawioną wartość *sockaddr_in6* typu danych.

```c
/* This is a small demo of BSD Wrapper for the high-performance NetX Duo
TCP/IP stack which uses standard BSD services for TCP connection,
disconnection, sending, and receiving using a simulated Ethernet driver. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nxd_bsd.h"
#include     <string.h>
#include     <stdlib.h>

#define     DEMO_STACK_SIZE     (16*1024)
#define     SERVER_PORT         87
#define     CLIENT_PORT         77

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_server;
TX_THREAD         thread_client;
NX_PACKET_POOL    bsd_pool;
NX_IP             bsd_ip;

/* Define some global data. */
CHAR     *msg0 = "Client 1:
    ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>END";

INT     maxfd;

/* Define the counters used in the demo application... */
ULONG     error_counter;

/* Define fd_sets for the BSD server socket. */
fd_set     master_list, read_ready;

/* Define thread prototypes. */
VOID     thread_server_entry(ULONG thread_input);
VOID     thread_client_entry(ULONG thread_input);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

int     main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void tx_application_define(void *first_unused_memory)
{
CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create a server thread. */
    tx_thread_create(&thread_server, "Server", thread_server_entry, 0,
                    pointer, DEMO_STACK_SIZE, 8, 8,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Create a Client thread. */
    tx_thread_create(&thread_client, "Client", thread_client_entry, 0,
                    pointer, DEMO_STACK_SIZE, 16, 16,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a BSD packet pool. */
    status = nx_packet_pool_create(&bsd_pool, "NetX BSD Packet Pool",
    128, pointer, 16384);

    pointer = pointer + 16384;

    if (status)
    {
        error_counter++;
        printf("Error in creating BSD packet pool\n!");
    }

    /* Create an IP instance for BSD. */
    status = nx_ip_create(&bsd_ip, "BSD IP Instance", IP_ADDRESS(1,2,3,4),
                        0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                        pointer, 2048, 1);
                        pointer = pointer + 2048;

    if (status)
    {
        error_counter++;
        printf("Error creating BSD IP instance\n!");
    }

    /* Enable ARP and supply ARP cache memory for BSD IP Instance */
    status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in enable ARP on BSD IP instance\n");
    }

    /* Enable TCP processing for BSD IP instances. */
    status = nx_tcp_enable(&bsd_ip);

    /* Check TCP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable TCP \n");
    }

    /* Now initialize BSD Scoket Wrapper */
    status = bsd_initialize(&bsd_ip, &bsd_pool,pointer, 2048, 2);

    /* Check BSD initialize status. */
    if (status)
    {
        error_counter++;
        printf("Error in BSD initialize \n");
    }

    pointer = pointer + 2048;
}

/* Define the Server thread. */
CHAR     Server_Rcv_Buffer[100];

VOID     thread_server_entry(ULONG thread_input)
{

INT             status, sock, sock_tcp_server;
ULONG           actual_status;
INT             Clientlen;
INT             i;
UINT            is_set = NX_FALSE;
NXD_ADDRESS     ip_address;
struct          sockaddr_in6 serverAddr;
struct          sockaddr_in6 ClientAddr;
UINT            iface_index, address_index;

    status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE,
            &actual_status, 100);

    /* Check status... */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable IPv6 */
    status = nxd_ipv6_enable(&bsd_ip);
    if((status != NX_SUCCESS) && (status != NX_ALREADY_ENABLED))
    {
        printf("Error with IPv6 enable 0x%x\n", status);
        return;
    }

    /* Enable ICMPv6 */
    status = nxd_icmp_enable(&bsd_ip);

    if(status)
    {
        printf("Error with ECMPv6 enable 0x%x\n", status);
        return;
    }

    /* Set the primary interface for our DNS IPv6 addresses. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&bsd_ip, iface_index, NX_NULL, 10,
                                &address_index);

    if (status)
        return;

    /* Set ip_0 interface address. */
    ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    ip_address.nxd_ip_address.v6[0] = htonl(0x20010db8);
    ip_address.nxd_ip_address.v6[1] = htonl(0x0000f101);
    ip_address.nxd_ip_address.v6[2] = 0;
    ip_address.nxd_ip_address.v6[3] = htonl(0x101);

    /* Set the host global IP address. We are assuming a 64
    bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&bsd_ip, iface_index, &ip_address, 64,
                                &address_index);

    if (status)
        return;

    /* Wait for IPv6 stack to finish DAD process. */
    tx_thread_sleep(400);

    /* Create BSD TCP Socket */
    sock_tcp_server = socket(AF_INET6, SOCK_STREAM, 0);

    if (sock_tcp_server == -1)
    {
        printf("\nError: BSD TCP Server socket create \n");
        return;
    }

    printf("\nBSD TCP Server socket created %lu \n", sock_tcp_server);

    /* Set the server port and IP address */
    memset(&serverAddr, 0, sizeof(serverAddr));
    serverAddr.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    serverAddr.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    serverAddr.sin6_addr._S6_un._S6_u32[2] = 0x0;
    serverAddr.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    serverAddr.sin6_port = htons(SERVER_PORT);
    serverAddr.sin6_family = AF_INET6;

    /* Bind this server socket */
    status = bind(sock_tcp_server, (struct sockaddr *) &serverAddr,
                    sizeof(serverAddr));

    if (status < 0)
    {
        printf("Error: Server Socket Bind \n");
        return;
    }

    FD_ZERO(&master_list);
    FD_ZERO(&read_ready);
    FD_SET(sock_tcp_server,&master_list);
    maxfd = sock_tcp_server;

    /* Now listen for any client connections for this server socket */
    status = listen(sock_tcp_server, 5);
    if (status < 0)
    {
        printf("Error: Server Socket Listen\n");
        return;
    }
    else
        printf("Server Listen complete\n");

    /* All set to accept client connections */
    printf("Now accepting client connections\n");

    /* Loop to create and establish server connections. */
    while(1)
    {

        printf("\n");

        read_ready = master_list;

        tx_thread_sleep(20); /* Allow some time to other threads too */

        /* Let the underlying TCP stack determine the timeout. */
        status = select(maxfd + 1, &read_ready, 0, 0, 0);

        if ( (status == 0xFFFFFFFF) || (status == 0) )
        {
            printf("Error with select? Status 0x%x. Try again\n", status);

            continue;
        }

        /* Detected a connection request. */
        is_set = FD_ISSET(sock_tcp_server,&read_ready);

        if(is_set)
        {

            Clientlen = sizeof(ClientAddr);

            sock = accept(sock_tcp_server,
            (struct sockaddr*)&ClientAddr,
            &Clientlen);

            /* Add this new connection to our master list */
            FD_SET(sock, &master_list);

            if ( sock \maxfd)
            {
                printf("New connection %d\n", sock);

                maxfd = sock;
            }

            continue;
        }

        /* Check the set of 'ready' sockets, e.g connected to remote host and
        waiting for notice of packets received. */
        for (i = NX_BSD_SOCKFD_START; i < (maxfd+1+NX_BSD_SOCKFD_START); i++)
        {

            if ((i != sock_tcp_server) &&
                (FD_ISSET(i, &master_list)) &&
                (FD_ISSET(i, &read_ready)))
            {

                while(1)
                {

                    status = recv(i, (VOID *)Server_Rcv_Buffer, 100, 0);

                    if (status == 0)
                    {
                        printf("(Server socket %d received no data from
                                Client)\n", i);

                        break;
                    }
                    else if (status == 0xFFFFFFFF)
                    {
                        printf("Error on Server socket %d receiving data from
                                Client\n", i);

                        break;
                    }

                    printf("Server socket %d received from Client %lu bytes:
                            %s\n ", i, (ULONG)status,
                            Server_Rcv_Buffer);

                    status = send(i, "Hello\n", sizeof("Hello\n"), 0);

                    if (status == ERROR)
                    {
                        printf("Error on Server socket %d sending data to
                                Client \n", i);
                    }
                    else
                    {
                        printf("Server socket %d message sent to Client:
                                Hello\n", i);
                    }
                }

                /* Close this socket */
                status = soc_close(i);

                if (status != ERROR)
                {
                    printf("Server socket %d closing\n", i);
                }
                else
                {

                    printf("Error on Server socket %d closing\n", i);
                }
            }
        }

        /* Loop back to check any next client connection */
    }
}

#define     CLIENT_BUFFER_SIZE 100
CHAR        Client_Rcv_Buffer[CLIENT_BUFFER_SIZE];

VOID        thread_client_entry(ULONG thread_input)
{

INT         status;
INT         sock_tcp_client, length;
struct      sockaddr_in6 echoServAddr6;
struct      sockaddr_in6 localAddr6; address */

    /* Wait for the server side to get set up, including the DAD process. */
    tx_thread_sleep(500);

    /* ICMPv6 and IPv6 should already be enabled on the IP instance
    by the server thread entry function. */

    /* Further the IPv6 address is already established with the IP instance.
    so no need to wait for DAD completion. */

    /* Set local port and IP address (used only for getsockname call). */
    memset(&localAddr6, 0, sizeof(localAddr6));
    localAddr6.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    localAddr6.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    localAddr6.sin6_addr._S6_un._S6_u32[2] = 0x0;
    localAddr6.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    localAddr6.sin6_port = htons(CLIENT_PORT);
    localAddr6.sin6_family = AF_INET6;

    /* Set Server port and IP address to connect to the TCP server. */
    memset(&echoServAddr6, 0, sizeof(echoServAddr6));
    echoServAddr6.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    echoServAddr6.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    echoServAddr6.sin6_addr._S6_un._S6_u32[2] = 0x0;
    echoServAddr6.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    echoServAddr6.sin6_port = htons(SERVER_PORT);
    echoServAddr6.sin6_family = AF_INET6;

    /* Now make client connections with the server. */
    while (1)
    {
        printf("\n");

        /* Create BSD TCP Socket */

        sock_tcp_client = socket(AF_INET6, SOCK_STREAM, 0);

        if (sock_tcp_client == -1)
        {
            printf("Error on Client socket %d create \n");
            return;
        }

        printf("Client socket %d created \n", sock_tcp_client);

        /* Now connect this client to the server */
        status = connect(sock_tcp_client, (struct sockaddr *)&echoServAddr6,
                sizeof(echoServAddr6));

        /* Check for error. */
        if (status != NX_SOC_OK)
        {
            printf("Error on Client socket %d connect\n");
            soc_close(sock_tcp_client);
            return;

        }

        /* Get and print source and destination information */
        printf("Client socket %d connected \n", sock_tcp_client);

        status = getsockname(sock_tcp_client, (struct sockaddr *)&localAddr6,
        &length);

        printf("Client port = %lu , Client = 0x%x 0x%x 0x%x 0x%x,",
                ntohs(localAddr6.sin6_port),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[0]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[1]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[2]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[3]));

        length = sizeof(struct sockaddr_in6);

        status = getpeername(sock_tcp_client, (struct sockaddr *)
                            &echoServAddr6, &length);

        printf("Remote port = %lu, Remote IP = 0x%x 0x%x 0x%x 0x%x \n",
                ntohs(echoServAddr6.sin6_port),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[0]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[1]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[2]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[3]));

        /* Now receive the echoed packet from the server */
        while(1)
        {

            printf("Client sock %d sending packet to server\n",
                sock_tcp_client);

            status = send(sock_tcp_client, "Hello", sizeof("Hello"), 0);

            if (status == NX_SOC_ERROR)
            {
                printf("Error on Client Socket (%d) send \n",
                        sock_tcp_client);
            }
            else
            {
                printf("Client socket %d sent message: Hello\n",
                        sock_tcp_client);
            }

            status = recv(sock_tcp_client, (VOID *)Client_Rcv_Buffer,
                        CLIENT_BUFFER_SIZE, 0);

            if (status <= 0)
            {

                if (status < 0)
                {
                    printf("Error on Client receiving on socket %d \n",
                            sock_tcp_client);
                }
                else
                {
                    printf("Client received no data on socket %d\n",
                            sock_tcp_client);
                }

            break;
            }
            else
            {
                printf("Client socket %d received %d bytes and this message:
                        %s\n", sock_tcp_client, status,
                        Client_Rcv_Buffer);
            }

        }

        /* close this client socket */
        status = oc_close(sock_tcp_client);

        if (status != NX_SOC_ERROR)
        {
            printf("Client Socket %d closed\n", sock_tcp_client);
        }
        else
        {
            printf("Error on Client Socket %d on close \n", sock_tcp_client);
        }

        /* Make another Client connection...*/

    }
}
```
