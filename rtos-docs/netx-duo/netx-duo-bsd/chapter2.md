---
title: Rozdział 2 — Instalowanie i używanie Azure RTOS NetX Duo BSD
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika Azure RTOS NetX Duo BSD.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 560621e528c8ce98013ce505ea1511f466317f4a087aa44cc0e70cb4d4b8ed1e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788511"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-bsd"></a>Rozdział 2 — Instalowanie i używanie Azure RTOS NetX Duo BSD

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika Azure RTOS NetX Duo BSD.

## <a name="product-distribution"></a>Dystrybucja produktów

Azure RTOS NetX Duo BSD można uzyskać z naszego publicznego repozytorium kodu źródłowego na stronie [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) . Pakiet zawiera dwa pliki źródłowe i plik PDF zawierający ten dokument w następujący sposób:

- **nxd_bsd.h:** plik nagłówka dla NetX Duo BSD
- **nxd_bsd.c:** plik źródłowy C dla NetX Duo BSD
- **nxd_bsd.pdf:** Podręcznik użytkownika aplikacji NetX Duo BSD

Pliki demonstracyjne:

- **bsd_demo_udp.c**
- **bsd_demo_tcp.c**
- **bsd_demo_raw.c**

## <a name="netx-duo-bsd-installation"></a>Instalacja zestawu NetX Duo BSD

Aby można było korzystać z programu NetX Duo BSD, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano program NetX Duo. Jeśli na przykład program NetX Duo jest zainstalowany w katalogu *"\threadx\arm7\green",* do tego katalogu powinny zostać skopiowane pliki *nxd_bsd.h* i *nxd_bsd.c.*

## <a name="building-the-threadx-and-netx-duo-components-of-a-bsd-application"></a>Tworzenie składników ThreadX i NetX Duo aplikacji BSD

### <a name="threadx"></a>ThreadX

Biblioteka ThreadX musi `bsd_errno` definiować w lokalnym magazynie wątku. Zalecamy następującą procedurę:

1. W *tx_port.h* ustaw jedno z TX_THREAD_EXTENSION w następujący sposób:
   - `#define TX_THREAD_EXTENSION_3     int bsd_errno`

1. Ponownie skompilować bibliotekę ThreadX.

> [!NOTE]
> Jeśli TX_THREAD_EXTENSION_3 jest już używany, użytkownik może używać jednego z innych makr TX_THREAD_EXTENSION danych.

### <a name="netx-duo"></a>NetX Duo

Przed rozpoczęciem korzystania z usług NetX Duo BSD bibliotekę NetX Duo należy sbudowaną z NX_ENABLE_EXTENDED_NOTIFY_SUPPORT zdefiniowane. Domyślnie nie jest zdefiniowana. Jeśli mają być używane nieprzetworzone gniazda BSD, biblioteka NetX Duo musi zostać s zbudowana z NX_ENABLE_IP_RAW_PACKET_FILTER zdefiniowanymi.

## <a name="using-netx-duo-bsd"></a>Korzystanie z netx duo BSD

Projekt aplikacji NetX Duo BSD musi zawierać plik *nxd_bsd.h,* jeśli zawiera on elementy *tx_api.h* i *nx_api.h,* aby móc korzystać z usług BSD określonych w dalszej części tego przewodnika. Aplikacja musi również *uwzględniać nxd_bsd.c* w procesie kompilacji. Ten plik musi zostać skompilowany w taki sam sposób, jak inne pliki aplikacji, a jego formularz obiektu musi być połączony z plikami aplikacji. To wszystko, co jest wymagane do korzystania z netx duo BSD.

Aby korzystać z usług NetX Duo BSD, aplikacja musi utworzyć wystąpienie adresu IP, utworzyć pulę pakietów dla warstwy BSD w celu przydzielenia pakietów, przydzielić miejsce do pamięci dla wewnętrznego stosu wątków BSD i określić priorytet wewnętrznego wątku BSD. Warstwa BSD jest inicjowana przez wywołanie *bsd_initialize* i przekazanie parametrów. Przedstawiono to w części "Małe przykłady" w dalszej części tego dokumentu, ale poniżej przedstawiono prototyp:

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                    *CHAR *bsd_thread_stack_area,
                    *ULONG bsd_thread_stack_size,
                    *UINT bsd_thread_priority*);
```

Adres default_ip to wystąpienie adresu IP, na którym działa warstwa BSD. Pakiet default_pool jest używany przez usługi BSD do przydzielania pakietów. Dwa następne parametry: bsd_thread_stack_area, bsd_thread_stack_size definiuje obszar stosu używany przez wewnętrzny wątek BSD, a ostatni parametr , bsd_thread_priority, ustawia priorytet wątku.

## <a name="netx-duo-bsd-raw-socket-support"></a>Obsługa nieprzetworzonych gniazd NetX Duo BSD

NetX Duo BSD obsługuje również nieprzetworzone gniazda. Aby używać nieprzetworzonych gniazd w netx duo BSD, biblioteka NetX Duo musi być skompilowana przy NX_ENABLE_IP_RAW_PACKET_FILTER zdefiniowane. Domyślnie nie jest zdefiniowana. Następnie aplikacja musi włączyć przetwarzanie nieprzetworzonych gniazd dla wcześniej utworzonego wystąpienia adresu IP, wywołując *nx_ip_raw_packet_enable.*

Aby utworzyć nieprzetworzone gniazdo w netx duo BSD, aplikacja używa gniazda create service *socket* i określa rodzinę protokołów, typ gniazda i protokół:

```c
sock_1 = socket(INT protocolFamily, INT socket_type, INT protocol)
```

ProtocolFamily jest AF_INET dla gniazd IPv4 lub AF_INET6 dla gniazd IPv6, przy założeniu, że protokół IPv6 jest włączony w wystąpieniu adresu IP. Wartość socket_type musi być ustawiona na SOCK_RAW. Protokół jest specyficzny dla aplikacji.

Aby wysyłać i odbierać nieprzetworzone pakiety, a także zamykać nieprzetworzone gniazda, aplikacja zwykle używa tych samych usług BSD, co w przypadku protokołu UDP, np. *sendto, recvfrom, select* i *soc_close*. Gniazda nieprzetworzone nie obsługują *akceptowania ani* *nasłuchiwać* usług BSD.

- Domyślnie odebrane dane pierwotne IPv4 zawierają nagłówek IPv4.  Z drugiej strony odebrane dane pierwotne IPv6 nie zawierają nagłówka IPv6.

- Domyślnie podczas wysyłania nieprzetworzonych pakietów IPv6 lub IPv4 warstwa otoki BSD dodaje nagłówek IPv6 lub IPv4 przed wysłaniem danych.

NetX Duo BSD obsługuje dodatkowe opcje gniazd pierwotnych, w tym IP_RAW_RX_NO_HEADER, IP_HDRINCL i IP_RAW_IPV6_HDRINCL.

Jeśli IP_RAW_RX_NO_HEADER, nagłówek IPv4 jest usuwany, dzięki czemu odebrane dane nie zawierają nagłówka IPv4, a zgłaszana długość komunikatu nie zawiera nagłówka IPv4.  W przypadku gniazd IPv6 domyślnie nieprzetworzone odbieranie gniazda nie zawiera nagłówka IPv6, co odpowiada IP_RAW_RX_NO_HEADER opcji. Aplikacja może użyć usługi *setsockopt* do wyczyszczenia opcji IP_RAW_RX_NO_HEADER. Po wyczyszczeniu opcji IP_RAW_RX_NO_HEADER odebrane dane pierwotne IPv6 będą zawierać nagłówek IPv6, a zgłaszana długość komunikatu będzie zawierać nagłówek IPv6.

Ta opcja nie ma wpływu na przesyłane dane protokołu IPv4 lub IPv6.

Jeśli IP_HDRINCL, podczas wysyłania danych aplikacja będzie zawierała nagłówek IPv4.  Ta opcja nie ma wpływu na transmisję IPv6 i nie jest zdefiniowana domyślnie. Jeśli IP_RAW_IPV6_HDRINCL jest ustawiona, aplikacja uwzględnia nagłówek IPv6 podczas wysyłania danych.  Ta opcja nie ma wpływu na transmisję IPv4 i nie jest zdefiniowana domyślnie.

IP_HDRINCL i IP_RAW_IPV6_HDRINCL nie mają wpływu na odbiór protokołu IPv4 lub IPv6.

> [!NOTE]
> Specyfikacja gniazda BSD 4.3 określa, że jądro musi skopiować nieprzetworzony pakiet do każdego buforu odbioru gniazda. Jednak w netx duo BSD, jeśli wiele gniazd są tworzone współużytkowanie tego samego protokołu, zachowanie jest niezdefiniowane.

## <a name="netx-duo-bsd-raw-packet-support"></a>Obsługa nieprzetworzonych pakietów NetX Duo BSD

Aby włączyć obsługę pakietów pierwotnych dla ppPoE, należy sbudowaną otokę NetX Duo BSD NX_BSD_RAW_PPPOE_SUPPORT włączone.

Następujące polecenie tworzy gniazdo BSD do obsługi nieprzetworzonych pakietów PPPoE:

```c
Sockfd = socket(AF_PACKET, SOCK_RAW, protocol);
```

Bieżąca implementacja BSD obsługuje tylko dwa typy protokołów z AF_PACKET rodziny

- `ETHERTYPE_PPPOE_DISC`: pakiety odnajdywania PPPoE. W ramce danych MAC pakiety odnajdywania mają typ ramki Ethernet 0x8863.

- `ETHERTYPE_PPPOE_SESS`: pakiety sesji PPP. W ramce danych MAC pakiety sesji mają typ ramki Ethernet 0x8864.

Struktura służy `sockaddr_ll` do określania parametrów podczas wysyłania lub odbierania ramek PPPoE.

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
> Nie każde pole w strukturze jest używane przez `sendto()` lub `recvfrom()` . Zapoznaj się z poniższym opisem, aby dowiedzieć się, jak skonfigurować program do wysyłania i odbierania `sockaddr_ll` pakietów PPPoE.

Gniazda utworzone w AF_PACKET można użyć do wysyłania pakietów odnajdywania PPPoE lub pakietów sesji PPP, niezależnie od określonego protokołu. Podczas przesyłania pakietu PPPoE aplikacja musi przygotować bufor, który zawiera prawidłowo sformatowaną ramkę PPPoE, w tym nagłówki MAC (docelowy adres MAC, źródłowy adres MAC i typ ramki). Rozmiar buforu zawiera 14-bajtowy nagłówek Ethernet.

Struktura `sockaddr_ll` , jest używana do `sll_ifindex` wskazywania interfejsu fizycznego, który ma być używany do wysyłania tego pakietu. Pozostałe pola w strukturze nie są używane. Wartości ustawione na nieużywane pola są ignorowane przez wewnętrzny proces BSD.

Poniższy blok kodu ilustruje sposób przesyłania pakietu PPPoE:

```c
struct sockaddr_ll peer_addr;

/* Transmit a PPPoE frame using the primary network interface. */
peer_addr.sll_ifindex = 0;
n = sendto(sockfd, frame, frame_size, 0, (struct
        sockaddr*)&peer_addr, sizeof(peer_addr));
```

Wartość zwracana wskazuje liczbę przesłanych bajtów. Ponieważ pakiety PPPoE są oparte na komunikatach, po pomyślnej transmisji liczba wysłanych bajtów odpowiada rozmiarowi pakietu, w tym nagłówkowi Ethernet o rozmiarze 14 bajtów.

Pakiety PPPoE można odbierać przy `recvfrom()` użyciu . Bufor odbierania musi być wystarczająco duży, aby pomieścić komunikat o rozmiarze jednostki MTU sieci Ethernet. Odebrany pakiet PPPoE zawiera 14-bajtowy nagłówek Ethernet. Po odebraniu pakietów PPPoE pakiety odnajdywania PPPoE mogą być odbierane tylko przez gniazdo utworzone za pomocą protokołu `ETHERTYPE_PPPOE_DISC` . Podobnie pakiety sesji PPP mogą być odbierane tylko przez gniazdo utworzone za pomocą protokołu `ETHERTYPE_PPPOE_SESS` . Jeśli utworzono wiele gniazd dla tego samego typu protokołu, przychodzące pakiety PPPoE są najpierw przekazywane do utworzonego gniazda. Jeśli pierwsze gniazdo utworzone dla protokołu zostanie zamknięte, kolejne gniazdo w kolejności tworzenia będzie używane do odbierania tych pakietów.

Po otrzymaniu pakietu PPPoE następujące pola w `sockaddr_ll` strukturze są prawidłowe:
- **sll_family:** ustawienie wewnętrznej usługi BSD w celu AF_PACKET
- **sll_ifindex:** wskazuje interfejs, z którego jest odbierany pakiet
- **sll_protocol:** ustaw typ odebranego pakietu: `ETHERTYPE_PPPOE_DISC` lub `ETHERTYPE_PPPOE_SESS`

## <a name="eliminating-internal-bsd-thread"></a>Eliminowanie wewnętrznego wątku BSD

Domyślnie BSD używa wątku wewnętrznego do wykonywania niektórych jego przetwarzania. W systemach ze ściśle określonymi ograniczeniami pamięci usługę BSD można utworzyć za pomocą zdefiniowanego NX_BSD_TIMEOUT_PROCESS_IN_TIMER, co eliminuje wewnętrzny wątek BSD, a zamiast tego używa wewnętrznego czasomierza do wykonania tego samego przetwarzania. Eliminuje to ilość pamięci wymaganej dla wewnętrznego stosu i bloku sterowania wątkami BSD. Jednak ogólne przetwarzanie czasomierza jest znacznie większe, a przetwarzanie BSD może również być wykonywane z wyższym priorytetem niż jest to konieczne.

Aby skonfigurować gniazda BSD do uruchamiania w kontekście czasomierza ThreadX, zdefiniuj NX_BSD_TIMEOUT_PROCESS_IN_TIMER w *nxd_bsd.h.* Jeśli warstwa BSD jest skonfigurowana do wykonywania zadań BSD w kontekście *czasomierza,* w wywołaniu funkcji bsd_initialize następujące trzy parametry są ignorowane i powinny mieć wartość NULL:

- **bsd_thread_stack_area**
- **bsd_thread_stack_size**
- **bsd_thread_priority**

## <a name="netx-duo-bsd-with-dns-support"></a>NetX Duo BSD z obsługą systemu DNS

Jeśli NX_BSD_ENABLE_DNS, usługa NetX Duo BSD może wysyłać zapytania DNS w celu uzyskania informacji o nazwie hosta lub adresie IP hosta. Ta funkcja wymaga, aby klient DNS NetX został wcześniej utworzony przy użyciu *nx_dns_create* usługi. Co najmniej jeden znany adres IP serwera DNS musi być zarejestrowany w wystąpieniu DNS przy użyciu usługi *nx_dns_server_add* do dodawania adresów serwerów IPv4 lub przy użyciu usługi *nxd_dns_server_add* do dodawania adresów serwerów IPv4 lub IPv6.

Usługi DNS i alokacja pamięci są używane przez *usługi getaddrinfo* *i getnameinfo:*

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
        const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
        char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

Gdy aplikacja BSD wywołuje *polecenie getaddrinfo* z nazwą hosta, netX BSD wywoła dowolną z poniższych usług, aby uzyskać adres IP:

- **nx_dns_ipv4_address_by_name_get**
- **nxd_dns_ipv6_address_by_name_get**
- **nx_dns_cname_get**

W *nx_dns_ipv4_address_by_name_get* i *nxd_dns_ipv6_address_by_name_get* netx BSD używa odpowiednio ipv4_addr_buffer i ipv6_addr_buffer pamięci. Rozmiar tych buforów jest definiowany przez (NX_BSD_IPV4_ADDR_PER_HOST * 4) i (NX_BSD_IPV6_ADDR_PER_HOST * 16).

W przypadku zwracania informacji o adresie z polecenia *getaddrinfo* program NetX BSD używa tabeli pamięci blokowej ThreadX nx_bsd_addrinfo_pool_memory, której obszar pamięci jest definiowany przez inny zestaw konfigurowalnych opcji, NX_BSD_IPV4_ADDR_MAX_NUM i NX_BSD_IPV6_ADDR_MAX_NUM.

Aby **uzyskać więcej informacji** na temat powyższych opcji konfiguracji, zobacz Ogólne opcje konfiguracji.

Ponadto jeśli NX_DNS_ENABLE_EXTENDED_RR_TYPES, a dane wejściowe hosta są nazwą kanoniczną, netX Duo BSD dynamicznie przydzieli pamięć z wcześniej utworzonej puli bloków "_nx_bsd_cname_block_pool

> [!NOTE]
> Po *wywołaniu getaddrinfo* aplikacja BSD jest odpowiedzialna za zwolnienie pamięci wskazywanej przez argument res z powrotem do tabeli blokowej przy użyciu *usługi freeaddrinfo.*

## <a name="netx-duo-bsd-limitations"></a>Ograniczenia usługi NetX Duo BSD

Ze względu na problemy z wydajnością i architekturą program NetX Duo BSD nie obsługuje wszystkich funkcji gniazd BSD 4.3:

Flagi INT nie są obsługiwane w przypadku *wywołań wysyłania, recv, sendto* *i recvom.*

## <a name="general-configuration-options"></a>Ogólne opcje konfiguracji

Opcje konfigurowalne przez użytkownika w *programie nxd_bsd.h* umożliwiają aplikacji dostosowanie gniazd NetX Duo BSD do konkretnych wymagań aplikacji.

Poniżej znajduje się lista konfigurowalnych opcji, które są ustawiane w czasie kompilacji:

- **NX_BSD_TCP_WINDOW:** używana w wywołaniach tworzenia gniazd TCP. 64k to typowy rozmiar okna dla sieci Ethernet 100 Mb. Wartość domyślna to 65535.

- **NX_BSD_SOCKFD_START:** jest to indeks logiczny dla wartości startowej deskryptora pliku gniazda BSD. Domyślnie ta opcja to 32.

- **NX_BSD_MAX_SOCKETS:** określa maksymalną liczbę gniazd dostępnych w warstwie BSD i musi być wielokrotnością 32. Wartość domyślna to 32.

- **NX_BSD_SOCKET_QUEUE_MAX:** określa maksymalną liczbę pakietów UDP przechowywanych w kolejce gniazd odbioru. Wartość domyślna to 5.

- **NX_BSD_MAX_LISTEN_BACKLOG:** określa rozmiar kolejki nasłuchiwać ("listy prac") dla gniazd TCP BSD. Wartość domyślna to 5.

- **NX_MICROSECOND_PER_CPU_TICK:** określa liczbę mikrosekund na takt czasomierz harmonogramu.

- **NX_BSD_TIMEOUT: określa** limit czasu w taktach czasomierza w wewnętrznych wywołaniach NetX Duo wymaganych przez BSD. Wartość domyślna to (20 * NX_IP_PERIODIC_RATE).

- **NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT:** określa limit czasu w taktach czasomierza w wywołaniu rozłączenia NetX Duo. Wartość domyślna to 1.

- **NX_BSD_PRINT_ERRORS:** jeśli to ustawienie zostanie ustawione, zwracany stan błędu funkcji BSD zwraca numer wiersza i typ błędu, np. NX_SOC_ERROR gdzie wystąpił błąd. Wymaga to zdefiniowania danych wyjściowych debugowania przez dewelopera aplikacji. Ustawienie domyślne jest wyłączone i w pliku *nxd_bsd.h nie określono żadnych danych wyjściowych debugowania.*

- **NX_BSD_TIMER_RATE:** interwał, po którym jest uruchamiane okresowe zadanie czasomierza BSD. Wartość domyślna to 1 sekunda (1 * NX_IP_PERIODIC_RATE).

- **NX_BSD_TIMEOUT_PROCESS_IN_TIMER:** jeśli to ustawienie jest ustawione, ta opcja umożliwia wykonanie procesu limitu czasu usługi BSD w kontekście czasomierza systemu. Domyślne zachowanie jest wyłączone. Ta funkcja została opisana bardziej szczegółowo w rozdziale 2 "Instalacja i używanie netx duo BSD".

- **NX_BSD_RAW_PPPOE_SUPPORT:** włącz obsługę nieprzetworzonych pakietów PPPoE. Domyślnie ta opcja nie jest włączona.

- **NX_BSD_ENABLE_DNS:** jeśli ta opcja jest włączona, usługa NetX Duo BSD wyśle zapytanie DNS dotyczące nazwy hosta lub adresu IP hosta. Wymaga, aby wystąpienie klienta DNS zostało wcześniej utworzone i uruchomione. Domyślnie nie jest on włączony.

- **NX_BSD_SOCKET_RAW_PROTOCOL_TABLE_SIZE:** definiuje rozmiar pierwotnej tabeli gniazd. Wartość musi być potęgą dwóch. NetX BSD tworzy tablicę gniazd typu NX_BSD_SOCKETS do wysyłania i odbierania nieprzetworzonych pakietów. NX_ENABLE_IP_RAW_PACKET_FILTER musi być włączona. Domyślnie jest to 32.

- **NX_BSD_IPV4_ADDR_MAX_NUM:** maksymalna liczba adresów IPv4 zwracanych przez *polecenie getaddrinfo.* Wraz z NX_BSD_IPV6_ADDR_MAX_NUM określa rozmiar puli bloków NetX BSD nx_bsd_addrinfo_block_pool dynamicznego przydzielania pamięci w celu adresowania magazynu informacji w pliku *getaddrinfo.* Wartość domyślna to 5.

- **NX_BSD_IPV6_ADDR_MAX_NUM:** maksymalna liczba adresów IPv6 zwracanych przez *polecenie getaddrinfo.* Wraz z NX_BSD_IPV4_ADDR_MAX_NUM określa rozmiar puli bloków NetX BSD nx_bsd_addrinfo_block_pool dynamicznego przydzielania pamięci w celu adresowania magazynu informacji w pliku *getaddrinfo.*

- **NX_BSD_IPV4_ADDR_PER_HOST:** definiuje maksymalną liczbę adresów IPv4 przechowywanych na zapytanie DNS. Wartość domyślna to 5.

- **NX_BSD_IPV6_ADDR_PER_HOST:** definiuje maksymalną liczbę adresów IPv6 przechowywanych na zapytanie DNS. Wartość domyślna to 2.

## <a name="bsd-socket-options"></a>Opcje gniazd BSD

Następującą listę opcji gniazd NetX Duo BSD można włączyć (lub wyłączyć) w czasie uruchamiania na podstawie gniazd przy użyciu *usługi setsockopt:*

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, 
                const void *option_value, INT option_length);
```

Istnieją dwa różne ustawienia dla option_level.

Pierwszy typ opcji gniazd czasu uruchamiania jest SOL_SOCKET dla opcji poziomu gniazda. Aby włączyć opcję poziomu gniazda, zestawy *wywołańsockopt* z option_level ustawioną na SOL_SOCKET i option_name ustawioną na konkretną opcję, np. SO_BROADCAST *.* Aby pobrać ustawienie opcji, wywołaj element *getsockopt* dla option_name z option_level ponownie ustawioną na SOL_SOCKET.

Poniżej przedstawiono listę opcji poziomu gniazd czasu uruchamiania.

- **SO_BROADCAST:** jeśli to ustawienie jest ustawione, umożliwia wysyłanie i odbieranie pakietów emisji z gniazd Netx. Jest to domyślne zachowanie netx duo. Wszystkie gniazda mają tę możliwość.

- **SO_ERROR:** służy do uzyskiwania stanu gniazda dla poprzedniej operacji gniazda określonego gniazda przy użyciu *usługi getsockopt.* Wszystkie gniazda mają tę możliwość.

- **SO_KEEPALIVE:** jeśli to ustawienie jest ustawione, włącza funkcję utrzymania aktywności protokołu TCP. Wymaga to, aby biblioteka NetX Duo była zbudowana przy użyciu NX_TCP_ENABLE_KEEPALIVE zdefiniowanej w *nx_user.h.* Domyślnie ta funkcja jest wyłączona.

- **SO_RCVTIMEO:** ustawia opcję oczekiwania w sekundach na odbieranie pakietów w gniazdach NetX Duo BSD. Wartość domyślna to NX_WAIT_FOREVER (0xFFFFFFFF) lub, jeśli włączono blokowanie, NX_NO_WAIT (0x0).

- **SO_RCVBUF:** określa rozmiar okna gniazda TCP. Wartość domyślna, NX_BSD_TCP_WINDOW, jest ustawiona na 64k dla gniazd TCP BSD. Aby ustawić rozmiar powyżej 65535, należy sfiniować bibliotekę NetX Duo z NX_TCP_ENABLE_WINDOW_SCALING.

- **SO_REUSEADDR:** jeśli to ustawienie jest ustawione, umożliwia mapować wiele gniazd na jeden port. Typowe użycie jest dla gniazda serwera TCP. Jest to domyślne zachowanie gniazd NetX Duo.

Drugi typ opcji gniazda czasu uruchamiania to poziom opcji adresu IP. Aby włączyć opcję poziomu adresu IP, zestawy *wywołańsockopt* z option_level ustawioną na IP_PROTO i option_name ustawioną na opcję, np.*IP_MULTICAST_TTL .* Aby pobrać ustawienie opcji, wywołaj element *getsockopt* dla option_name z option_level ponownie ustawioną na IP_PROTO.

Poniżej przedstawiono listę opcji poziomu adresów IP czasu uruchamiania.

- **IP_MULTICAST_TTL:** ustawia czas na żywo dla gniazd UDP. Wartość domyślna to NX_IP_TIME_TO_LIVE (0x80) podczas tworzenia gniazda. Tę wartość można przesłonić przez wywołanie *metody setsockopt z* tą opcją gniazda.

- **IP_RAW_IPV6_HDRINCL:** jeśli ta opcja jest ustawiona, aplikacja wywołująca musi dołączyć nagłówek IPv6 i opcjonalnie nagłówki aplikacji do danych przesyłanych na nieprzetworzonych gniazdach IPv6 utworzonych przez BSD. Aby użyć tej opcji, nieprzetworzone przetwarzanie gniazd musi być włączone w zadaniu adresu IP.

- **IP_ADD_MEMBERSHIP:** jeśli to ustawienie jest ustawione, ta opcja umożliwia dołączenie gniazda BSD (dotyczy tylko gniazd UDP) do określonej grupy IGMP.

- **IP_DROP_MEMBERSHIP:** jeśli to ustawienie jest ustawione, ta opcja umożliwia gniazdu BSD (dotyczy tylko gniazd UDP) pozostawienie określonej grupy IGMP.

- **IP_HDRINCL:** jeśli ta opcja jest ustawiona, aplikacja wywołująca musi dołączyć nagłówek IP i opcjonalnie nagłówki aplikacji do danych przesyłanych na nieprzetworzonych gniazdach IPv4 utworzonych w UŚCIB. Aby użyć tej opcji, nieprzetworzone przetwarzanie gniazd musi być włączone w zadaniu adresu IP.

- **IP_RAW_RX_NO_HEADER:** w przypadku wyczyszczenia nagłówka IPv6 jest dołączona do odebranych danych dla pierwotnych gniazd IPv6 utworzonych w BSD. Nagłówki IPv6 są domyślnie usuwane w pierwotnych gniazdach IPv6 usługi BSD, a długość pakietu nie zawiera nagłówka IPv6.

W przypadku ustawienia nagłówek IPv4 jest usuwany z odebranych danych na pierwotnych gniazdach BSD typu IPv4. Nagłówki IPv4 są domyślnie uwzględniane w pierwotnych gniazdach IPv4 BSD, a długość pakietu obejmuje nagłówek IPv4.

Ta opcja nie ma wpływu na dane transmisji IPv4 lub IPv6.

## <a name="small-ipv4-example"></a>Przykład małego adresu IPv4

Poniżej opisano przykład sposobu korzystania z usług NetX Duo BSD dla sieci IPv4. W tym przykładzie plik dołączania *nxd_bsd.h* jest przekierowyny w wierszu 8. Następnie wystąpienie adresu IP *bsd_ip* pulę pakietów *bsd_pool* jako zmienne globalne w wierszach 20 i 21. Należy pamiętać, że w tej wersji demonstracyjnej jest używany sterownik sieciowy pamięci RAM (wirtualny),*_nx_ram_network_driver*. W tym przykładzie klient i serwer będą współużytkowały ten sam adres IP w pojedynczym wystąpieniu adresu IP.

Wątki klienta i serwera są tworzone w wierszach 62 i 68. Pula pakietów BSD do przesyłania pakietów jest tworzona w wierszu 78 i używana podczas tworzenia wystąpienia adresu IP w wierszu 87. Należy pamiętać, że zadanie wątku IP ma priorytet 1 w *wywołaniu nx_ip_create* ip. Ten wątek powinien być zadaniem o najwyższym priorytecie zdefiniowanym w programie w celu uzyskania optymalnej wydajności NetX.

Wystąpienie adresu IP jest włączone dla usług ARP i TCP odpowiednio w wierszach 88 i 110. Ostatnim wymaganiem przed rozpoczęciem usług BSD jest wywołanie usługi *bsd_initialize* w wierszu 120 w celu skonfigurowania wszystkich struktur danych oraz zasobów NetX i ThreadX wymaganych przez usługę BSD.

Funkcja wpisu wątku serwera jest definiowana w następnej. Gniazdo TCP BSD jest tworzone w wierszu 149. Adres IP serwera i port są ustawione w wierszach 160–163. Zwróć uwagę na użycie makr kolejności bajtów hosta do sieci *htonl* i *htons* zastosowanych do adresu IP i portu. Jest to zgodne ze specyfikacją gniazda BSD, że dane wielo bajtowe są przesyłane do usług BSD w kolejności bajtów sieciowych.

Następnie gniazdo serwera głównego jest powiązane z portem przy użyciu usługi *powiązania* w wierszu 166. Jest to gniazdo nasłuchiwania żądań połączeń TCP przy użyciu usługi *nasłuchiwania* w wierszu 180. W tym miejscu funkcja wątku serwera, *thread_server_entry*, pętle do sprawdzania zdarzeń odbierania przy użyciu *wywołania select* w wierszu 202. Jeśli zdarzenie odbierania jest żądaniem połączenia, które jest określane przez porównanie listy gotowe do odczytu, wywołuje żądanie *accept w* wierszu 213. Podrzędne gniazdo serwera jest przypisywane do obsługi żądania połączenia i dodawane do głównej listy gniazd serwerów TCP połączonych z klientem w wierszu 223. Jeśli nie ma żadnych nowych żądań połączenia, wątek serwera sprawdza wszystkie aktualnie połączone gniazda pod potrzeby odbierania zdarzeń w pętli for rozpoczynającej się w wierszu 236. Po wykryciu zdarzenia odbierania,  które oczekuje, wywołuje wysyłanie i *recv* na tym gnieździe, dopóki nie zostaną odebrane żadne dane (połączenie zamknięte po drugiej stronie) i gniazdo zostanie zamknięte przy użyciu *usługi soc_close* w wierszu 277.

Po zakończeniu konfiguracji wątku serwera funkcja wpisu wątku klienta thread_client_entry *tworzy* gniazdo w wierszu 326 i  łączy się z gniazdem serwera TCP przy użyciu wywołania połączenia w wierszu 337. Następnie pętle wysyłają i odbierają pakiety przy *użyciu* odpowiednio usług wysyłania *i* odbierania. Gdy nie są odbierane żadne dane, zamyka gniazdo w wierszu 398 przy użyciu *soc_close* usługi. Po rozłączeniu funkcja wpisu wątku klienta tworzy nowe gniazdo TCP i wysyła kolejne żądanie połączenia w pętli while uruchomionej w wierszu 321.

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

## <a name="small-ipv6-example-system"></a>Mały przykładowy system IPv6

Przykład sposobu korzystania z usług NetX Duo BSD dla sieci IPv6 został opisany w poniższym programie. Ten przykład jest bardzo podobny do opisanego wcześniej programu demonstracyjnego IPv4 z kilkoma istotnymi różnicami.

Wątki klienta i serwera, pula pakietów BSD, wystąpienie adresu IP i inicjowanie BSD mają miejsce tak samo jak w przypadku gniazd BSD IPv4.

W funkcji wpisu wątku serwera *thread_server_entry* definiuje kilka zmiennych IPv6 przy użyciu typów danych *sockaddr_in6* i *NXD_ADDRESS* w wierszach 145-148. Typ NXD_ADDRESS może w rzeczywistości przechowywać zarówno typy adresów IPv4, jak i IPv6.

Następnie wątek serwera włącza protokół IPv6 i ICMPv6 w wystąpieniu adresu IP przy użyciu usługi *nxd_ipv6_enable* i *nxd_icmpv6_enable* odpowiednio w wierszu 161 i 169. Następnie lokalne i globalne adresy IP linku są rejestrowane w wystąpieniu adresu IP. Odbywa się to przy *użyciu usługi nxd_ipv6_address_set* w wierszach 180 i 195. Następnie jest ona uśpięty wystarczająco długo, aby zadanie wątku ip kończyło protokół wykrywania zduplikowanych adresów i rejestrowały te adresy jako prawidłowe adresy w wywołaniu *tx_thread_sleep* w wierszu 201.

Następnie gniazdo serwera TCP jest tworzone z argumentem wejściowym typu AF_INET6 gniazda w wierszu 204. Adres IPv6 gniazda i port są ustawione w wierszach 216-221, ponownie za pomocą *makr htonl* i *htons* umieścić dane w kolejności bajtów sieciowych dla usług gniazd BSD. W tym miejscu funkcja wątków serwera jest praktycznie taka sama jak w przykładzie protokołu IPv4.

Funkcja wpisu wątku klienta, *thread_client_entry*, jest definiowana jako następna. Należy pamiętać, że ponieważ klient TCP w tym przykładzie ma ten sam adres IP i adres IPv6 co serwer TCP, nie musimy ponownie włączać usług IPv6 ani ICMPv6 w wystąpieniu adresu IP. Ponadto adres IPv6 jest już zarejestrowany w wystąpieniu adresu IP. Zamiast tego funkcja wpisu wątku klienta po prostu czeka w wierszu 368 na skonfigurowanie serwera. Adres serwera i port są ustawione przy użyciu hosta do sieci bajtowych makr kolejności w wierszach 387-392, a następnie klient może połączyć się z serwerem TCP w wierszu 412. Należy pamiętać, że typy danych lokalnego adresu IP w wierszach 378-383 są używane tylko do zademonstrowania usług *getsockname* i *getpeername* odpowiednio w wierszach 425 i 434. Ponieważ dane pochodzą z sieci, sieć hostuje makra kolejności bajtów używane w wierszach 378–383.

Następnie funkcja wpisu wątku klienta wchodzi w pętlę, w której tworzy gniazdo TCP, nawiąże połączenie TCP oraz wyśle i odbierze dane z serwera TCP, dopóki nie zostanie odebranych praktycznie tak samo jak w przykładzie IPv4. Następnie zamyka gniazdo w wierszu 483, na krótko wstrzymuje i tworzy kolejne gniazdo TCP oraz żąda połączenia z serwerem TCP.

Jedną z istotnych różnic w przykładzie protokołu IPv4 jest to, że wywołania gniazd określają gniazdo IPv6 przy użyciu AF_INET6 wejściowego.  Inną istotną różnicą jest  to,  że wywołanie połączenia klienta TCP przyjmuje sockaddr_in6 typu danych i argument długości ustawiony na rozmiar sockaddr_in6 *typu* danych.

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
