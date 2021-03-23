---
title: Rozdział 1 — wprowadzenie do translacji adresów sieciowych
description: Translacja adresów sieciowych IP (NAT) została pierwotnie opracowana w celu rozwiązania problemu ograniczonej liczby internetowych adresów IPv4.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3d01aa6f68e21ea82f65a59a19c4f5c7958a6b92
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821774"
---
# <a name="chapter-1---an-introduction-to-network-address-translation"></a>Rozdział 1 — wprowadzenie do translacji adresów sieciowych

## <a name="the-need-for-network-address-translation"></a>Potrzeba translacji adresów sieciowych

Translacja adresów sieciowych IP (NAT) została pierwotnie opracowana w celu rozwiązania problemu ograniczonej liczby internetowych adresów IPv4. Konieczność translatora adresów sieciowych występuje, gdy wiele urządzeń musi uzyskać dostęp do Internetu, ale tylko jeden adres internetowy IPv4 jest przypisywany przez usługodawcę internetowego.

Istnieją również inne korzyści wynikające z używania translatora adresów sieciowych. Topologia sieci poza domeną lokalną może ulec zmianie na wiele sposobów. Klienci mogą zmieniać dostawców, firmowych kości lub mogą być scalane lub dzielone. Za każdym razem, gdy zewnętrzna zmiana topologii, przydziały adresów dla hostów w domenie lokalnej muszą także ulec zmianie, aby odzwierciedlały te zmiany zewnętrzne. Zmiany tego typu mogą być ukryte dla użytkowników w domenie przez scentralizowanie zmian w pojedynczym routerze translacji adresów. Translator adresów sieciowych umożliwia dostęp do publicznej sieci Internet i chroni je przed bezpośrednim dostępem z zewnątrz. Organizacje z konfiguracją sieci głównie do użytku wewnętrznego, którzy potrzebują okazjonalnego dostępu do zewnątrz, są dobrymi kandydatami do tego schematu.

## <a name="basic-nat-and-network-address-port-translation"></a>Podstawowe translacja adresów sieciowych i portów adresów sieciowych

Router z obsługą translatora adresów sieciowych jest instalowany między siecią publiczną a siecią prywatną. Rola routera z obsługą translatora adresów sieciowych jest tłumaczona między wewnętrznymi prywatnymi adresami IPv4 i przypisanym publicznym adresem IPv4, więc wszystkie urządzenia w sieci prywatnej mogą współużytkować ten sam publiczny adres IPv4.

W podstawowej implementacji TRANSLATORa adresów sieciowych router translatora adresów sieciowych ma jeden lub więcej adresów IP zarejestrowanych globalnie, które różnią się od własnego adresu IP. Te adresy globalne są dostępne do przypisania do hostów w sieci prywatnej statycznie lub dynamicznie. NAPT lub translacja portów adresów sieciowych jest odmianą podstawowego NAT, gdzie translacja adresów sieciowych jest rozszerzona w celu uwzględnienia identyfikatora "transport". Zwykle jest to numer portu dla pakietów TCP i UDP oraz identyfikator zapytania dla pakietów ICMP.

Połączenia między granicami translatora adresów sieciowych są zwykle inicjowane przez hosty w sieci prywatnej wysyłające pakiety wychodzące do hosta zewnętrznego. Te hosty mają zwykle przypisane *dynamiczne* (tymczasowe) adresy IP do tego celu. Istnieje również możliwość, że połączenia są inicjowane w odwrotnym kierunku, jeśli sieć prywatna ma serwery HTTP lub FTP, które będą akceptować żądania klientów z sieci zewnętrznej. Translator adresów sieciowych zazwyczaj przypisze te hosty jako *statyczny* (stały) adres IP: port.

## <a name="how-network-address-translation-works"></a>Jak działa translacja adresów sieciowych

Typową konfigurację sieci przy użyciu routera z obsługą translatora adresów sieciowych przedstawiono na rysunku 1.

![Typowa konfiguracja sieci przy użyciu routera z obsługą translatora adresów sieciowych](media/image2.png)

**Rysunek 1. Typowa konfiguracja sieci przy użyciu routera z obsługą translatora adresów sieciowych**

Router z obsługą translatora adresów sieciowych ma zazwyczaj dwa interfejsy sieciowe. Jeden interfejs jest połączony z publicznym Internetem. druga jest połączona z siecią prywatną. Typowy router w tej konfiguracji jest odpowiedzialny za Routing datagramów IP między siecią prywatną a siecią publiczną na podstawie docelowego adresu IP. Router z obsługą translatora adresów sieciowych Wykonuje translację adresów przed kierowaniem datagramu protokołu IPv4 między publicznym i prywatnym interfejsem. Dla każdej sesji TCP lub UDP jest ustanawiane tłumaczenie, na podstawie wewnętrznego adresu źródłowego, numeru portu źródłowego i zewnętrznego adresu docelowego i numeru portu docelowego. W przypadku żądań echa ICMP i datagram odpowiedzi zamiast numeru portu jest używany identyfikator zapytania protokołu ICMP.

Aby zilustrować typową implementację translacji adresów sieciowych, należy rozważyć konfigurację sieci na rysunku 2.

![Typowa implementacja translatora adresów sieciowych](media/image3.png)

**Rysunek 2. typowa implementacja translatora adresów sieciowych**

W tym scenariuszu router NAT łączy sieć prywatną z lewej strony i sieć publiczną z prawej strony. Załóżmy, że po stronie publicznej sieci adres IP interfejsu routera translatora adresów sieciowych to 202.151.25.14; w interfejsie sieci prywatnej router translatora adresów sieciowych używa adresu IP 192.168.1.254. Węzeł w sieci prywatnej inicjuje połączenie TCP z serwerem sieci Web w Internecie.

Rysunek 3 przedstawia widok wysokiego poziomu procesu translacji adresów sieciowych.

![Ogólny widok procesu translacji adresów sieciowych](media/image4.png)

**Rysunek 3 — ogólny widok procesu translacji adresów sieciowych**

1. Klient przesyła komunikat SYN protokołu TCP do serwera sieci Web. Adres nadawcy to 192.168.1.15, numer portu 6732; adres docelowy to 128.15.54.3, numer portu 80.
1. Pakiet z klienta jest odbierany przez router NAT w interfejsie sieci prywatnej. Reguła ruchu wychodzącego ma zastosowanie do pakietu: adres nadawcy (klienta) jest tłumaczony na publiczny adres IP routera NAT 202.15.25.14, a numer portu źródłowego nadawcy (klienta) jest tłumaczony na numer portu TCP 2015 w interfejsie publicznym.
1. Pakiet jest następnie przesyłany przez Internet i ostatecznie osiągnie swój 128.15.54.3 hosta docelowego. Zwróć uwagę na to, że po stronie odbiorczej na podstawie adresu źródłowego i numeru portu warstwy IP pakiet prawdopodobnie pochodzi z 202.151.24.14, numer portu 2015.
   Rysunek 4 przedstawia proces NAT na ścieżce zwracanej.

   ![Proces NAT na ścieżce zwracanej](media/image5.png)

   **Rysunek 4. proces NAT na ścieżce zwracanej**
1. W tym scenariuszu 128.15.54.3 hosta internetowego wysyła pakiet odpowiedzi z adresem internetowym routera NAT jako miejsce docelowe.
1. Pakiet dociera do routera NAT. Ponieważ jest to pakiet powiązany, stosowane są powiązane z nią reguły Tłumaczenia: adres docelowy został zmieniony z powrotem na adres IP oryginalnego nadawcy: 192.168.1.15, numer portu docelowego 6732.
1. Pakiet jest następnie przekazywany do klienta za pomocą interfejsu, który jest połączony z siecią wewnętrzną.

W ten sposób adres sieci Internet i numer portu nadawcy nie są ujawniane innym hostom w publicznym Internecie.

## <a name="netx-duo-nat-features"></a>Funkcje translatora adresów sieciowych NetX Duo

Gdy wystąpienie translatora adresów sieciowych zostanie utworzone przy użyciu wywołania *nx_nat_create* , tabela translacji NAT zostanie utworzona.

```C
UINT nx_nat_create(NX_NAT_DEVICE *nat_ptr, NX_IP *ip_ptr,
    UINT global_interface_index,
    VOID *dynamic_cache_memory,
    UINT dynamic_cache_size);
```

Aby śledzić tłumaczenia adresów sieciowych dla wszystkich aktywnych połączeń między sieciami lokalnymi i zewnętrznymi, router z obsługą translatora adresów sieciowych NetX Duo utrzymuje tabelę translacji z informacjami o każdym połączeniu z prywatnym hostem, który zawiera źródłowy i docelowy adres IP i numer portu.

Lokalizacja tej tabeli translacji ("Cache") jest ustawiana za pomocą wskaźnika dynamic_cache_memory. Ten obszar musi zawierać 4-bajtowe miejsce w buforze. Rozmiar tabeli (lub liczby wpisów) jest określany przez podzielenie rozmiaru pamięci podręcznej dynamic_cache_size przez rozmiar wpisu tabeli NAT. Tabela musi być wystarczająco duża dla minimalnej liczby wpisów określonych przez **NX_NAT_MIN_ENTRY_COUNT, która jest zdefiniowana w *nx_nat. h*. Wartość domyślna to 3.**

Limit czasu dla wszystkich wpisów dynamicznych w tabeli translacji NAT NetX Duo jest inicjowany do NX_NAT_ENTRY_RESPONSE_TIMEOUT, który jest zdefiniowany w *nx_nat. h*. Wartość domyślna to 4 minuty (lub 240 cykle systemu dla procesora 100 mHz) zgodnie z zaleceniami RFC 2663. Za każdym razem, gdy NetX Duo, odbierze lub wyśle pakiet pasujący do wpisu dynamicznego w tabeli, resetuje limit czasu tego wpisu do NX_NAT_ENTRY_RESPONSE_TIMEOUT. Podczas wyszukiwania w tabeli NetX Duo translator adresów sieciowych również sprawdza, czy w tabeli znajdują się wygasłe wpisy i usuwać je.

Aby utworzyć wpisy przychodzące jako statyczne w tabeli, np. w przypadku serwerów w sieci lokalnej, NetX Duo translator adresów sieciowych udostępnia usługę *nx_nat_inbound_entry_create* . Jeśli wpis tabeli definiuje połączenie hosta lokalnego jako static, nigdy nie wygasa.

```C
UINT nx_nat_inbound_entry_create(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *entry_ptr,
    ULONG local_ip_address, USHORT external_port,
    USHORT local_port, UCHAR protocol);
```

Ta usługa została szczegółowo opisana w [rozdziale 4 — Opis usług](chapter4.md)

W czasie wykonywania, jeśli tabela translacji jest pełna i nie można dodać kolejnych wpisów, NetX Duo translator adresów sieciowych będzie powiadamiać aplikację NAT z pełnym wywołaniem zwrotnym pamięci podręcznej, jeśli jest on zarejestrowany w wystąpieniu NAT. W tym celu należy użyć usługi *nx_nat_cache_notify_set* :

```C
UINT nx_nat_cache_notify_set(NX_NAT_DEVICE *nat_ptr,
    VOID (*cache_full_notify_cb)(NX_NAT_DEVICE *nat_ptr));
```

Zobacz [rozdział 4 — Opis usług,](chapter4.md) Aby uzyskać więcej informacji na temat tej usługi.

## <a name="nat-packet-processing-in-netx-duo"></a>Przetwarzanie pakietów NAT w NetX Duo

NetX Duo translator adresów sieciowych jest przeznaczony do użycia na routerze IPv4. Aby translator adresów sieciowych działał prawidłowo, NetX Duo musi być skonfigurowany do przekazywania pakietów do serwera NAT. Aby dowiedzieć się, jak to zrobić, zobacz rozdział 2 dotyczący instalacji NAT NetX Duo. Serwer NAT wskazuje, czy będzie "zużywać" (próbuje przesłać dalej) pakiet do hosta w jednej z jego sieci. Jeśli pakiet nie zostanie zużyty, pakiet jest "zwrócony" do NetX Duo, aby przetworzyć pakiet w miarę jak zwykle.

Gdy serwer NAT odbiera pakiet do przesyłania dalej z NetX Duo, określa, czy pakiet jest przychodzący czy wychodzący.

W przypadku pakietów wychodzących serwer NAT sprawdza adres i port źródła nagłówka IP pakietu. Jeśli tabela translacji nie zawiera wpisu dla pakietu, który został wcześniej Wysłany przez ten host dla tego samego miejsca docelowego, translator adresów sieciowych utworzy nowy wpis, który będzie zawierał unikatowy globalny źródłowy adres IP: port dla połączenia, i zmodyfikuje nagłówki pakietów przy użyciu tego nowego adresu IP: Port przed wysłaniem go do sieci zewnętrznej.

W przypadku pakietów przychodzących serwer NAT szuka poprzedniego wpisu w swojej tabeli translacji z zewnętrznym adresem IP: Port pasujący do docelowego adresu IP pakietu: port. Jeśli nie zostanie znalezione żadne dopasowanie, odrzuci pakiet, chyba że adres docelowy: port jest adresem zewnętrznym serwera w sieci lokalnej. W przypadku znalezienia dopasowania zostanie on zastąpiony zewnętrzny docelowy adres IP nagłówka pakietu: port z prywatnym adresem IP: port i wysłać pakiet do sieci lokalnej do zamierzonego hosta prywatnego.

NetX Duo translator adresów sieciowych używa zakresu portów TCP, UDP i ICMP do tworzenia unikatowego adresu lokalnego: połączenia portów dla hostów lokalnych łączących się z hostami zewnętrznymi. Następujące konfigurowalne opcje zdefiniowane w *nx_nat. h* definiują zakres dla każdego protokołu:

```C
NX_NAT_START_TCP_PORT

NX_NAT_END_TCP_PORT

NX_NAT_START_UDP_PORT

NX_NAT_END_UDP_PORT

NX_NAT_START_ICMP_QUERY_ID

NX_NAT_END_ICMP_QUERY_ID
```

## <a name="nat-requirements-and-constraints"></a>Wymagania i ograniczenia dotyczące translatora adresów sieciowych

NetX Duo translator adresów sieciowych wymaga NetX Duo 5,8 lub nowszego. Aplikacja NAT wymaga utworzenia jednego wystąpienia IP i interfejsu do wewnętrznej i zewnętrznej sieci fizycznej.

Powiązanych

- NetX Duo translator adresów sieciowych obsługuje protokoły TCP, UDP i ICMP. Protokół IGMP nie jest obsługiwany.
- Translator adresów sieciowych NetX Duo nie obsługuje adresowania IPv6.
- Translator adresów sieciowych NetX Duo nie obejmuje usług DNS ani DHCP, chociaż NetX Duo translator adresów sieciowych może zintegrować te usługi z ich operacjami NAT.

## <a name="rfcs-supported-by-netx-duo-nat"></a>Specyfikacje RFC obsługiwane przez NetX Duo translator adresów sieciowych

Implementacja translatora adresów sieciowych NetX Duo jest oparta na informacjach przedstawionych w następujących dokumentach RFC:

- RFC 2663: Terminologia i zagadnienia dotyczące translatora adresów sieciowych IP
- RFC 3022: netowrk (tradycyjny NAT) translator adresów IP
- RFC 4787: wymagania dotyczące zachowania translacji adresów sieciowych (NAT) dla protokołu UDP emisji pojedynczej
