---
title: Rozdział 1 — Wprowadzenie do tłumaczenia adresów sieciowych
description: Translator adresów IP (NAT) został pierwotnie opracowany w celu rozwiązania problemu z ograniczoną liczbą internetowych adresów IPv4.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8639b87decd78f58a34fe6b8033a2427b560c872814abfdbbcb6057166412d0d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797469"
---
# <a name="chapter-1---an-introduction-to-network-address-translation"></a>Rozdział 1 — Wprowadzenie do tłumaczenia adresów sieciowych

## <a name="the-need-for-network-address-translation"></a>Potrzeba translacji adresów sieciowych

Translator adresów IP (NAT) został pierwotnie opracowany w celu rozwiązania problemu z ograniczoną liczbą internetowych adresów IPv4. Nat pojawia się, gdy wiele urządzeń musi mieć dostęp do Internetu, ale tylko jeden adres internetowy IPv4 jest przypisywany przez usługodawcę internetowego.

Korzystanie z naT ma również inne zalety. Topologia sieci poza domeną lokalną może ulec zmianie na wiele sposobów. Klienci mogą zmieniać dostawców, sieci szkieletowe firmy mogą być zreorganizowane lub dostawcy mogą scalać lub dzielić. Za każdym razem, gdy topologia zewnętrzna zmienia się, przypisania adresów dla hostów w domenie lokalnej muszą również ulec zmianie, aby odzwierciedlić te zmiany zewnętrzne. Zmiany tego typu mogą być ukryte przed użytkownikami w domenie przez scentralizowanie zmian do pojedynczego routera translacji adresów. NaT umożliwia dostęp hostów lokalnych do publicznego Internetu i chroni je przed bezpośrednim dostępem z zewnątrz. Organizacje z konfiguracją sieci głównie do użytku wewnętrznego, z potrzebą okazjonalnie dostępu zewnętrznego są dobrymi kandydatami dla tego schematu.

## <a name="basic-nat-and-network-address-port-translation"></a>Podstawowe translatora adresów sieciowych i translatora portów adresów sieciowych

Między siecią publiczną a siecią prywatną jest instalowany router z obsługą nat. Rolą routera z obsługą nat jest tłumaczenie między wewnętrznymi prywatnymi adresami IPv4 i przypisanym publicznym adresem IPv4, dzięki czemu wszystkie urządzenia w sieci prywatnej mogą współużytować ten sam publiczny adres IPv4.

W podstawowej implementacji nat router NAT "jest właścicielem" co najmniej jednego globalnie zarejestrowanego adresu IP innego niż jego własny adres IP. Te adresy globalne można przypisywać do hostów w sieci prywatnej statycznie lub dynamicznie. Translator adresów sieciowych (NAPT, Network Address Port Translation) to odmiana podstawowego translatora adresów sieciowych, w której translacja adresów sieciowych jest rozszerzana w celu dołączyć identyfikator "transport". Zazwyczaj jest to numer portu dla pakietów TCP i UDP oraz identyfikator zapytania dla pakietów ICMP.

Połączenia przez granicę nat są zwykle inicjowane przez hosty w sieci prywatnej wysyłające pakiety wychodzące do hosta zewnętrznego. Do tych hostów są zwykle *przypisywane* dynamiczne (tymczasowe) adresy IP. Istnieje jednak również możliwość zainicjowania połączeń w przeciwnym kierunku, jeśli sieć prywatna ma "serwery", np. serwery HTTP lub FTP, które będą akceptować żądania klienta z sieci zewnętrznej. NaT zazwyczaj przypisze tym hostom lokalnym *statyczny* (trwały) adres IP:port.

## <a name="how-network-address-translation-works"></a>Jak działa tłumaczenie adresów sieciowych

Typowa konfiguracja sieci z routerem z obsługą nat jest zilustrowana na rysunku 1.

![Typowa konfiguracja sieci z routerem z obsługą nat](media/image2.png)

**Rysunek 1. Typowa konfiguracja sieci z routerem z obsługą nat**

Router z obsługą nat ma zwykle dwa interfejsy sieciowe. Jeden interfejs jest połączony z publicznym Internetem; Drugi jest połączony z siecią prywatną. Typowy router w tej konfiguracji jest odpowiedzialny za routing datagramów adresów IP między siecią prywatną i siecią publiczną na podstawie docelowego adresu IP. Router z obsługą translatora adresów sieciowych wykonuje translowanie adresów przed routingiem datagramu IPv4 między interfejsem publicznym i prywatnym. Dla każdej sesji TCP lub UDP jest ustalane tłumaczenie na podstawie wewnętrznego adresu źródłowego, numeru portu źródłowego oraz zewnętrznego adresu docelowego i numeru portu docelowego. W przypadku datagramu żądania echa i odpowiedzi ICMP zamiast numeru portu jest używany identyfikator zapytania ICMP.

Aby zilustrować typową implementację tłumaczenia adresów sieciowych, rozważmy konfigurację sieci na rysunku 2.

![Typowa implementacja translacji adresów sieciowych](media/image3.png)

**Rysunek 2. Typowa implementacja translacji adresów sieciowych**

W tym scenariuszu router NAT łączy sieć prywatną z lewej, a sieć publiczną z prawej strony. Załóżmy, że po stronie sieci publicznej adres IP interfejsu routera nat to 202.151.25.14; W prywatnym interfejsie sieciowym router NAT używa adresu IP 192.168.1.254. Węzeł w sieci prywatnej inicjuje połączenie TCP z serwerem internetowym w Internecie.

Rysunek 3 przedstawia widok wysokiego poziomu procesu translacji adresów sieciowych.

![Widok wysokiego poziomu procesu translacji adresów sieciowych](media/image4.png)

**Rysunek 3. Widok wysokiego poziomu procesu translacji adresów sieciowych**

1. Klient przesyła komunikat TCP SYN do serwera internetowego. Adres nadawcy to 192.168.1.15, numer portu 6732; Adres docelowy to 128.15.54.3, numer portu 80.
1. Pakiet od klienta jest odbierany przez router NAT w prywatnym interfejsie sieciowym. Reguła ruchu wychodzącego ma zastosowanie do pakietu: adres nadawcy (klienta) jest tłumaczony na publiczny adres IP routera NAT 202.15.25.14, a numer portu źródłowego nadawcy (klienta) jest tłumaczony na numer portu TCP 2015 w interfejsie publicznym.
1. Pakiet jest następnie przesyłany przez Internet i ostatecznie dociera do jego hosta docelowego 128.15.54.3. Zwróć uwagę, że po stronie odbieracej, na podstawie adresu źródłowego warstwy IP i numeru portu warstwy TCP, pakiet wydaje się pochodzić z numeru portu 202.151.24.14 2015.
   Rysunek 4 przedstawia proces NAT na ścieżce powrotu.

   ![Proces NAT na ścieżce powrotnej](media/image5.png)

   **Rysunek 4. Proces nat na ścieżce powrotu**
1. W tym scenariuszu host internetowy 128.15.54.3 wysyła pakiet odpowiedzi z adresem internetowym routera nat jako miejscem docelowym.
1. Pakiet dociera do routera NAT. Ponieważ jest to pakiet powiązany, stosowane są reguły translacji w granicach: adres docelowy jest zmieniany z powrotem na oryginalny adres IP nadawcy (klienta): 192.168.1.15, numer portu docelowego 6732.
1. Pakiet jest następnie przesyłany dalej do klienta za pośrednictwem interfejsu połączonego z siecią wewnętrzną.

W ten sposób adres sieci internetowej i numer portu nadawcy nie są widoczne dla innych hostów w publicznym Internecie.

## <a name="netx-duo-nat-features"></a>Funkcje naT NetX Duo

Po utworzeniu wystąpienia translatora nat przy *użyciu nx_nat_create,* tworzona jest tabela translacji translatora translatora nat.

```C
UINT nx_nat_create(NX_NAT_DEVICE *nat_ptr, NX_IP *ip_ptr,
    UINT global_interface_index,
    VOID *dynamic_cache_memory,
    UINT dynamic_cache_size);
```

Aby śledzić translację adresów sieciowych dla wszystkich aktywnych połączeń między sieciami lokalnymi i zewnętrznymi, router z włączoną obsługą translatora adresów sieciowych NetX Duo utrzymuje tabelę translacji z informacjami na temat każdego połączenia prywatnego hosta, w tym źródłowym i docelowym adresem IP oraz numerem portu.

Lokalizacja tej tabeli tłumaczenia ("pamięć podręczna") jest ustawiana za pomocą dynamic_cache_memory tłumaczenia. Ten obszar musi być obszarem buforu wyrównanym o rozmiarze 4 bajtów. Rozmiar tabeli (lub liczba wpisów) jest określany przez podzielenie rozmiaru pamięci podręcznej dynamic_cache_size przez rozmiar wpisu tabeli NAT. Tabela musi być wystarczająco duża dla minimalnej liczby wpisów określonej przez NX_NAT_MIN_ENTRY_COUNT, która jest **zdefiniowana *w pliku nx_nat.h.* Wartość domyślna to 3.**

Limit czasu dla wszystkich wpisów dynamicznych w tabeli tłumaczenia translatora translatora nat NetX Duo jest inicjowania do NX_NAT_ENTRY_RESPONSE_TIMEOUT który jest zdefiniowany w *nx_nat.h.* Wartość domyślna to 4 minuty (lub 240 taktowania systemu dla procesora 100 mHz) zgodnie z zaleceniami RFC 2663. Za każdym razem, gdy NetX Duo NAT odbierze lub wyśle pakiet pasujący do dynamicznego wpisu w tabeli, resetuje on ten czas NX_NAT_ENTRY_RESPONSE_TIMEOUT. Podczas wyszukiwania w tabeli sieć NetX Duo NAT sprawdzi również, czy w tabeli nie ma wygasłych wpisów, i je usunie.

Aby utworzyć wpisy przychodzące jako statyczne w tabeli, np. dla serwerów w sieci lokalnej, NetX Duo NAT udostępnia *nx_nat_inbound_entry_create* usługi. Jeśli wpis tabeli definiuje połączenie hosta lokalnego jako statyczne, nigdy nie wygasa.

```C
UINT nx_nat_inbound_entry_create(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *entry_ptr,
    ULONG local_ip_address, USHORT external_port,
    USHORT local_port, UCHAR protocol);
```

Ta usługa jest opisana bardziej szczegółowo w [rozdziale 4 — opis usług](chapter4.md)

Jeśli w czasie wykonywania tabela tłumaczenia jest pełna i nie można dodać więcej wpisów, netx Duo NAT powiadomi aplikację TRANSLATORa o pełnym wywołaniu zwrotowym pamięci podręcznej, jeśli jest ona zarejestrowana w wystąpieniu translatora nat. Odbywa się to przy użyciu *nx_nat_cache_notify_set* usługi:

```C
UINT nx_nat_cache_notify_set(NX_NAT_DEVICE *nat_ptr,
    VOID (*cache_full_notify_cb)(NX_NAT_DEVICE *nat_ptr));
```

Aby uzyskać więcej informacji na temat tej usługi, zobacz [Rozdział 4](chapter4.md) — Opis usług.

## <a name="nat-packet-processing-in-netx-duo"></a>Przetwarzanie pakietów NAT w NetX Duo

NetX Duo NAT jest przeznaczony do użycia na routerze IPv4. Aby nat działało, należy skonfigurować netX Duo do przekazywania pakietów do serwera NAT. Aby dowiedzieć się, jak to zrobić, zobacz Rozdział 2 w instalacji systemu NetX Duo NAT. Następnie serwer NAT wskazuje, czy pakiet będzie "zużywał" (podejmować próbę przekazania go do hosta w jednej ze swoich sieci). Jeśli pakiet nie będzie zużywany, jest on "zwracany" do netx duo w celu przetwarzania pakietu w zwykły sposób.

Gdy serwer NAT odbiera pakiet do przekazania z netX Duo, określa, czy pakiet jest przychodzący, czy wychodzący.

W przypadku pakietów wychodzących serwer NAT sprawdza źródłowy adres i port nagłówka IP pakietu. Jeśli tabela translacji nie zawiera wpisu dla pakietu wcześniej wysłanego przez tego hosta dla tego samego miejsca docelowego, translator adresów sieciowych utworzy nowy wpis, który będzie zawierać unikatowy globalny źródłowy adres IP:port połączenia, i zmodyfikuje nagłówki pakietów przy użyciu tego nowego adresu IP:port przed wysłaniem do sieci zewnętrznej.

W przypadku pakietów przychodzących serwer NAT szuka poprzedniego wpisu w tabeli translacji z zewnętrznym adresem IP: portem zgodnym z docelowym adresem IP pakietu: portem. Jeśli dopasowanie nie zostanie znalezione, pakiet zostanie odrzucony, chyba że adres docelowy: port jest adresem zewnętrznym serwera w sieci lokalnej. Jeśli znajdzie dopasowanie, zastąpi zewnętrzny docelowy adres IP nagłówka pakietu: port prywatnym adresem IP: port i wyśle pakiet do sieci lokalnej do zamierzonego hosta prywatnego.

NetX Duo NAT używa zakresu portów translacji TCP, UDP i ICMP do tworzenia unikatowego adresu lokalnego: połączeń portów dla hostów lokalnych łączących się z hostami zewnętrznymi. Następujące opcje konfigurowalne przez użytkownika zdefiniowane *w nx_nat.h definiują* zakres dla każdego protokołu:

```C
NX_NAT_START_TCP_PORT

NX_NAT_END_TCP_PORT

NX_NAT_START_UDP_PORT

NX_NAT_END_UDP_PORT

NX_NAT_START_ICMP_QUERY_ID

NX_NAT_END_ICMP_QUERY_ID
```

## <a name="nat-requirements-and-constraints"></a>Wymagania i ograniczenia dotyczące naT

Sieć NetX Duo NAT wymaga netx duo 5.8 lub nowszej. Aplikacja NAT wymaga utworzenia pojedynczego wystąpienia adresu IP i interfejsu do wewnętrznej i zewnętrznej sieci fizycznej.

Ograniczenia:

- System NetX Duo NAT obsługuje protokoły TCP, UDP i ICMP. IGMP nie jest obsługiwany.
- Sieć NetX Duo NAT nie obsługuje adresowania IPv6.
- NetX Duo NAT nie obejmuje usług DNS ani DHCP, chociaż NetX Duo NAT może zintegrować te usługi z operacjami NAT.

## <a name="rfcs-supported-by-netx-duo-nat"></a>RFC obsługiwane przez NetX Duo NAT

Implementacja systemu NetX Duo NAT jest oparta na informacjach przedstawionych w następujących RFC:

- RFC 2663: Terminologia i zagadnienia dotyczące Translator adresów IP (NAT)
- RFC 3022: Tradycyjny adres IP Netowrk Translator (tradycyjny nat)
- RFC 4787: Wymagania dotyczące zachowania translatora adresów sieciowych (NAT) dla protokołu UDP emisji pojedynczej
