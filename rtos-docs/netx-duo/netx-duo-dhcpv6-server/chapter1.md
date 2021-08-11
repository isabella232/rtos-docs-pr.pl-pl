---
title: Rozdział 1 — Wprowadzenie do Azure RTOS NetX Duo DHCPv6
description: W tym dokumencie wyjaśniono szczegółowo, jak serwer NetX Duo DHCPv6 przypisuje adresy IPv6 do klientów DHCPv6.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 14a9d76731d949e3556a019756caf38b4ef440abfa4cfb927c47607e5712d9ac
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783660"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-dhcpv6-server"></a>Rozdział 1 — Wprowadzenie do Azure RTOS NetX Duo DHCPv6

W sieciach IPv6 protokół DHCPv6is jest wymagany, aby klienci uzyskiwali adresy IPv6. Nie zastępuje protokołu DHCP, który jest ograniczony do protokołu IPv4w tym, że nie oferuje adresów IPv4. Protokół DHCPv6 ma podobne funkcje jak protokół DHCP, a także wiele ulepszeń. Klient, który nie korzysta lub nie może używać automatycznej konfiguracji bez stanu adresu IPv6, może użyć protokołu DHCPv6 do przypisania unikatowego globalnego adresu IPv6 z serwera DHCPv6.

NetX Duo opracowano w celu obsługi aplikacji sieciowych opartych na protokole IPv6 i protokołów sieciowych, takich jak DHCPv6. W tym dokumencie wyjaśniono szczegółowo, jak serwer NetX Duo DHCPv6 przypisuje adresy IPv6 do klientów DHCPv6.

## <a name="dhcpv6-communication"></a>Komunikacja DHCPv6

**Struktura komunikatów DHCPv6**

Zawartość komunikatu jest zasadniczo nagłówkiem komunikatu, po którym następuje co najmniej jeden blok opcji (zazwyczaj więcej). Poniżej przedstawiono podstawową strukturę, w której każdy blok reprezentuje jeden bajt:

![Diagram przedstawiający strukturę bloku komunikatów i opcji DHCPv6.](media/image2.jpg)

**Rysunek 1. Struktura bloku komunikatów i opcji DHCPv6**

1-bajtowe Msg-Type wskazuje typ komunikatu DHCPv6. 3-bajtowe pole Transaction-ID jest ustawiane przez klienta. Może to być dowolna sekwencja znaków, ale musi być unikatowa dla każdego komunikatu klienta wysyłanego do serwera (zachowana w zduplikowanych komunikatach wysyłanych przez klienta). Serwer używa tego identyfikatora transakcji dla każdej odpowiedzi do klienta, aby umożliwić klientowi dopasowanie komunikatów serwera w przypadku pakietów, które są opóźnione lub porzucone w sieci. Po polu Transaction-ID (Identyfikator transakcji) znajduje się co najmniej jedna opcja protokołu DHCPv6, która służy do wskazywania żądań klienta.

Struktura opcji DHCPv6 składa się z kodu opcji, pola długości opcji, które nie zawiera pola długości ani kodu, a na koniec danych opcji, które są co najmniej jednym 2-bajtowym polem kodu opcji dla danych żądanych przez klienta.

Niektóre bloki opcji mają zagnieżdżone opcje. Na przykład opcja *Identity Association for Non Temporary Address (IANA) zawiera* co najmniej jedną opcję skojarzenia tożsamości *(IA)* w celu żądania adresów IPv6. Opcja *IANA* zwrócona w komunikacie odpowiedzi serwera zawiera te same opcje *IA* z adresami IPv6 i czasami dzierżawy przyznanymi przez serwer, *a* także opcję Stan wskazującą, czy wystąpił błąd w żądaniu adresu klienta.

Lista wszystkich bloków opcji i ich opis znajduje się w **dodatku A**.

**Typy komunikatów DHCPv6**

Mimo że protokół DHCPv6 znacznie zwiększa funkcjonalność protokołu DHCP, używa tej samej liczby komunikatów co protokół DHCP i obsługuje te same opcje dostawcy co protokół DHCP. Lista komunikatów DHCPv6 jest następująca:

- SOLICT (1) (wysyłane przez klienta)
- ANONSOWANIE (2) (wysyłane przez serwer)
- REQUEST (3) (wysyłane przez klienta)
- REPLY (7) (wysyłane przez serwer)
- POTWIERDŹ (4) (wysyłane przez klienta)
- RENEW (5) (wysyłane przez klienta)
- REBIND (6) (wysyłane przez klienta)
- RELEASE (8) (wysyłane przez klienta)
- DECLINE (9) (wysyłane przez klienta)
- INFORM_REQUEST (11) (wysyłane przez klienta)
- RECONFIGURE* (10) (wysyłane przez serwer)

*Funkcja RECONFIGURE nie jest obsługiwana przez serwer NetX Duo DHCPv6.

Podstawowa sekwencja żądań DHCPv6 z równoważnym typem komunikatu DHCPv4 w nawiasie jest następująca:

Klient ***Żądanie** _ (_Discovery ) Anons serwera *(oferta)**Żądanie klienta (żądanie)* Odpowiedź serwera *(DHCPAck*)*

Odpowiedź **serwera** odnów **klienta** *(DHCPAck)*

## <a name="dhcpv6-message-validation"></a>Walidacja komunikatu DHCPv6

Identyfikator transakcji: klient musi wygenerować identyfikator transakcji dla każdego komunikatu wysyłanego do serwera. Serwer DHCPv6 odrzuci każdy komunikat od klienta, który nie pasuje do tego identyfikatora transakcji. Serwer z kolei musi używać tego samego identyfikatora transakcji w odpowiedziach z powrotem do klienta.

**Unikatowe identyfikatory DHCPv6 (DUID)**

Wszystkie komunikaty serwera muszą również zawierać unikatowy identyfikator DHCPv6 (DUID) w każdym komunikacie lub klient DHCPv6 nie powinien go akceptować. Link Layer (LL) DUID to blok sterujący zawierający adres MAC klienta, typ sprzętu i typ DUID. Identyfikator DUID czasu warstwy łącza (LLT) dodatkowo zawiera pole czasu, które zmniejsza prawdopodobieństwo, że identyfikator DUID nie będzie unikatowy w sieci hosta. Z tego powodu RFC 3315 zaleca IDENTYFIKATORY DUID LLT za pośrednictwem identyfikatorów DUID LL. Jeśli aplikacja hosta nie utworzy własnej unikatowej wartości czasu, netX Duo DHCPv6 udostępni wartość domyślną. Trzecim typem identyfikatora DUID jest identyfikator DUID usługi Enterprise (przypisany przez dostawcę), który zawiera zarejestrowany identyfikator Enterprise (tak jak w przypadku rejestracji WANA) i dane prywatne o zmiennym typie i długości, na przykład na podstawie rozmiaru pamięci, typu systemu operacyjnego innej konfiguracji sprzętu. Zapoznaj się z listą opcji konfiguracji w innym miejscu tego dokumentu, aby skonfigurować wartości identyfikatora prywatnego i przypisanego dostawcy serwera.

Klient musi również uwzględnić swój duid w swoich komunikatach do serwera z wyjątkiem INFORM_REQUEST, w przypadku gdy serwer je odrzuci.

**Sesje serwera klienta DHCPv6**

Klienci i serwery DHCPv6 wymieniają komunikaty za pośrednictwem protokołu UDP. Klient używa portu 546 do wysyłania i odbierania komunikatów DHCPv6, a serwer używa portu 547. Klient początkowo używa adresu lokalnego linku do przesyłania i odbierania komunikatów DHCPv6. Wysyła wszystkie komunikaty do serwerów DHCPv6 przy użyciu zastrzeżonego adresu multiemisji o zakresie łącza znanego jako adres multiemisji *All_DHCP_Relay_Agents_and_Servers* *(FF02::01:02).*

W przypadku żądań przypisania adresu IPv6 serwer DHCPv6 nasłuchuje komunikatów *na* żądanie *wysyłanych* All_DHCP_Relay_Agents_and_Servers adres. W *żądaniu na żądanie* klient może zażądać przypisania określonego adresu IPv6 lub pozwolić serwerowi wybrać jeden z nich. Może również zażądać innych informacji o konfiguracji sieci z serwera.

Jeśli serwer DHCPv6Server wyodrębnia prawidłowy komunikat na żądanie i może przypisać adres IPv6 do klienta, odpowiada komunikatem anonsowania zawierającym adres IPv6, który zostanie przydzielony klientowi, czas dzierżawy adresu IPv6 i wszelkie dodatkowe informacje żądane przez klienta.   Jeśli klient zaakceptuje ofertę serwera,  odpowie komunikatem Żądanie informujący serwer o tym, że zaakceptuje adres IPv6. Serwer potwierdza, że klient jest powiązany z adresem IPv6 za pomocą komunikatu *Odpowiedzi.*

Jeśli komunikat protokołu DHCPv6 klienta jest nieprawidłowy, serwer odrzuci komunikat w trybie dyskretnym. Jeśli serwer nie może udzielić żądania,  wyśle komunikat Odpowiedź ze wskazaniem problemu w polu stanu opcji IANA adresu IP. Jeśli zostaną odebrane zduplikowane żądania klienta, serwer ponownie wysyła swoją poprzednią odpowiedź DHCPv6, zakładając, że klient po prostu nie odebrał pakietu.

Klient musi sprawdzić, czy przypisany adres IPv6 z serwera nie jest przypisany do innego hosta w systemie przy użyciu różnych protokołów IPv6, takich jak wykrywanie zduplikowanych adresów. Jeśli adres nie jest unikatowy, klient wyśle serwer komunikat *o odmówienie.* Serwer aktualizuje tabelę dzierżawy adresów IP przy użyciu tych informacji, rejestrując, że adres jest już przypisany. W międzyczasie klient musi ponownie uruchomić proces żądania DHCPv6 przy użyciu innego *komunikatu na żądanie.*

Oprócz adresu IPv6 klient prawdopodobnie będzie również musiał znać serwer DNS i prawdopodobnie inne informacje sieciowe, takie jak nazwa domeny sieciowej. Protokół DHCPv6 umożliwia zażądanie tych informacji przy użyciu żądań opcji  w komunikatach *Żądanie* i Żądanie albo oddzielnie w komunikatach żądania *informacji.* Opcje protokołu DHCPv6 zostały opisane w dalszej części tego rozdziału.

**Czas trwania dzierżawy IPv6**

Gdy serwer udziela klientowi adresu IPv6, przypisuje również czas trwania dzierżawy (okres istnienia) w opcji IANA dla programu , gdy zaleca klientowi rozpoczęcie odnawiania  (T1) lub ponownego wiązania adresu IPv6 przy użyciu komunikatów Odnów i Powiązywanie.  Różnica między nimi polega na tym, że klient kieruje komunikat Odnawianie do serwera przez uwzględnienia wartości DUID serwera w *żądaniu Odnawianie.*  Jednak nie określa żadnego serwera, a tym samym nie zawiera duid serwera, w komunikat o *ponownego* pomięcie All_DHCP_Relay_Agents_and_Servers *adresu.* Opcja IA zawierająca rzeczywisty adres IPv6 udzielany klientowi przez serwer zawiera również preferowane i prawidłowe okresy istnienia, gdy dzierżawiony adres IPv6 staje się przestarzały lub przestarzały (nieprawidłowy).

Serwer NetX Duo DHCPv6 utrzymuje limit czasu sesji dla każdego klienta, aby śledzić czas między komunikatami klienta. Jest to konieczne w przypadku utraty łączności przez hosta klienta lub utraty łączności z siecią. Po upłynie limit czasu sesji zakłada się, że klient nie jest już zainteresowany lub może wysyłać żądania DHCPv6 serwera. Serwer usuwa rekord Client i zwraca wszystkie wstępnie przypisanego adresu IPv6 z powrotem do dostępnej puli. Opcja oczekiwania limitu czasu sesji jest opcją konfigurowacyjną przez użytkownika.

Jeśli klient chce zwolnić swój adres IPv6 lub wykrywa, że adres IPv6 przypisany do niego przez serwer DHCPv6 jest już w użyciu, wysyła odpowiednio komunikat o wydaniu lub odrzuć.   W przypadku komunikatu o *wydaniu* serwer zwraca stan adresu IPv6 z powrotem do dostępnej puli. W przypadku komunikatu  Odrzuć aktualizuje tabelę dzierżawy adresów IP, aby wskazać, że ten adres IPv6 jest niedostępny (należący do innej jednostki w sieci).

**Dzierżawa IPv6 i dane rekordów klienta**

Gdy serwer DHCPv6 zacznie akceptować żądania klientów, zachowuje listę aktywnych klientów, którzy żądają lub mają przypisane adresy IPv6. Serwer sprawdza wygaśnięcie dzierżawy IP za pomocą czasomierza dzierżawy, który okresowo aktualizuje czas trwania dzierżawy klienta. Gdy czas trwania przekracza prawidłowy okres istnienia, serwer wyczyści rekord Klienta i zwróci jego adres IPv6 z powrotem do dostępnej puli. Klient musi rozpocząć proces odnawiania/ponownego wiązania, zanim tak się stanie.

Tabela rekordów klienta serwera NetX Duo DHCPv6 zawiera informacje służące do identyfikowania klientów oraz informacje o stanie służące do sprawdzania poprawności żądań klientów DHCPv6 oraz przypisywania lub ponownego przypisywania adresów IPv6. Takie informacje obejmują:

- Unikatowy identyfikator KLIENTA DHCPv6 (DUID), który unikatowo definiuje każdego hosta klienta w sieci. Klient musi zawsze używać tego samego identyfikator DUID dla wszystkich swoich komunikatów DHCPv6.

- Skojarzenie tożsamości klienta dla adresów innych niż tymczasowe (IANA) i adres IPv6 skojarzenia tożsamości (IA) łącznie definiujące parametry przypisania adresu IPv6 klienta.

- Żądania opcji klienta (serwer DNS, nazwa domeny itp.).

- Adres źródłowy IPv6 klienta (jeśli jest ustawiony) i adres docelowy (jeśli nie multiemisja) najnowszego żądania DHCPv6.

- Najnowszy typ komunikatu klienta i "stan" protokołu DHCPv6.

## <a name="netx-duo-dhcpv6-server-requirements-and-constraints"></a>NetX Duo DHCPv6 Server Requirements and Constraints

Interfejs API serwera NetX Duo DHCPv6 wymaga wersji ThreadX 5.1 lub nowszej oraz NetX Duo 5.5 lub nowszej.

**Wymagania**

***Konfiguracja zadania wątku IP***

Serwer NetX Duo DHCPv6 wymaga utworzenia wystąpienia adresu IP do wysyłania i odbierania komunikatów do protokołu DHCPv6 przy jego linku sieciowym. Odbywa się to przy użyciu *nx_ip_create* usługi. Należy utworzyć sam serwer DHCPv6 NetX Duo. Odbywa się to przy użyciu *nx_dhcpv6_server_create* usługi.

Protokół DHCPv6 korzysta z netx duo, protokołu ICMPv6 i protokołu UDP. W związku z tym protokół IPv6 należy najpierw włączyć przed użyciem serwera DHCPv6 przez wywołanie następujących usług NetX Duo:

- *nx_udp_enable*
- *nxd_ipv6_enable*
- *nxd_icmp_enable*

Ponadto przed rozpoczęciem pracy serwera DHCPv6 należy skonfigurować kilka zadań do wykonania:

- Utwórz i zweryfikuj jego adresy lokalne i globalne IPv6. Sprawdzanie poprawności adresów jest wykonywane automatycznie przez program NetX Duo przy użyciu funkcji wykrywania zduplikowanych adresów, jeśli jest włączona. Szczegółowe informacje na *temat walidacji lokalnego* i globalnego adresu IP można znaleźć w podręczniku użytkownika aplikacji NetX Duo.

- Ustaw indeks interfejsu sieciowego dla interfejsu DHCPv6.

- Utwórz zakres adresów IP dla przypisywalnych adresów IPv6. Jeśli dane istnieją z poprzedniej sesji protokołu DHCPv6 serwera, tabela dzierżaw IPv6 i rekordy klientów z tej sesji muszą zostać przekazane z pamięci trwałej do serwera DHCPv6. Mały przykładowy system w innym miejscu tego dokumentu zademonstruje usługi serwera DHCPv6 w celu spełnienia tego wymagania.

- Ustaw wartość DUID serwera. Jeśli serwer utworzył swój duid w poprzedniej sesji musi użyć tych samych danych, aby utworzyć ten sam duid dla komunikatów do swoich klientów. Mały przykładowy system w innym miejscu tego dokumentu pokazuje, jak to wymaganie jest realizowane.

W tym momencie serwer DHCPv6 jest gotowy do uruchomienia. Wewnętrznie serwer NetX Duo DHCPv6 utworzy gniazdo UDP powiązane z portem 547 i rozpocznie nasłuchiwanie żądań klienta.

***Wymagania dotyczące puli pakietów***

Serwer NetX Duo DHCPv6 wymaga puli pakietów do wysyłania komunikatów DHCPv6. Rozmiar puli pakietów pod względem ładunku pakietów i liczby dostępnych pakietów jest konfigurowalny przez użytkownika i zależy od przewidywanej ilości komunikatów DHCPv6 i innych transmisji, które będzie wysyłać aplikacja hosta.

Typowy komunikat DHCPv6 to około 200–300 bajtów w zależności od liczby dodatkowych opcji żądanych przez klienta i informacji dostępnych na serwerze.

***Ustawianie interfejsu serwera DHCPv6***

Serwer DHCPv6 domyślnie przyjmuje podstawowy interfejs sieciowy jako interfejs, na którym będą akceptowane żądania klienta. Jednak aplikacja hosta musi nadal ustawiać globalny indeks adresów, którego użyła do utworzenia globalnego adresu serwera. Indeks interfejsu DHCPv6 i globalny indeks adresów są ustawiane przy użyciu *nx_dhcpv6_server_interface_set* usługi. Okazano to również w "małym przykładzie" w tym dokumencie.

***Zapisywanie identyfikatorów DUID protokołu DHCPv6 między ponownymi uruchomieniami serwera***

Protokół DHCPv6 wymaga, aby serwer używał tego samego identyfikatorów DUID podczas wielu ponownych uruchomień. W związku z tym wszystkie dane użyte do utworzenia duidu muszą być przechowywane i pobierane z pamięci nieulotnej. W przypadku hostów, które korzystają z warstwy łącza plus duid czasu, który wymaga dostępu do zegara w czasie rzeczywistym. Aplikacja hosta NetX Duo DHCPv6 powinna zawierać dostęp do danych w czasie rzeczywistym w celu wygenerowania wartości czasu dla początkowego tworzenia identyfikatorów DUID serwera i przechowywania tych danych do ponownego użycia w kolejnych sesjach serwera. Następnie *nx_dhcpv6_set_server_duid* dane DUID jako argumenty, a także opcje konfiguracji w zależności od typu DUID, aby utworzyć (lub odtworzyć) własny duid.

***Tworzenie listy adresów IPv6 do przypisania***

Po utworzeniu serwera DHCPv6 aplikacja hosta serwera musi utworzyć zakres przypisywanych adresów globalnych IPv6, jeśli nie ma żadnych wcześniej przechowywanych danych listy adresów IP. Odbywa się to przy *użyciu usługi nx_dhcpv6_create_ip_address_range,* która przyjmuje jako dane wejściowe początkowy i końcowy adres IPv6.

***Zapisywanie przypisanego adresu DHCPv6 i danych klienta***

Protokół DHCPv6 wymaga, aby serwer DHCPv6 zapisywał dane klientów i adresów IPv6 w magazynie nieulotnym w przypadku ponownego uruchomienia serwera. Serwer NetX Duo DHCPv6 ma kilka interfejsów API do przekazywania i pobierania danych klientów i adresów IPv6 odpowiednio do i z serwera DHCPv6:

*nx_dhcpv6_add_client_record*

*nx_dhcpv6_add_ip_address_lease*

*nx_dhcpv6_retrieve_client_record*

*nx_dhcpv6_retrieve_ip_address_lease*

Przed ponownym uruchomieniem serwera należy przekazać dane na serwer. Pobieranie danych powinno odbywać się dopiero po zatrzymaniu (lub wstrzymaniu) serwera DHCPv6. Usługi do tego celu zostały szczegółowo opisane w dalszej części tego dokumentu. Jednak protokół DHCPv6 NetX Duo nie definiuje dostępu do magazynu nieulotnego. Musi to być obsługiwane przez aplikację hosta. W małym przykładzie pokazano, jak robi to aplikacja hosta.

***Unikatowy identyfikator DHCP serwera (DUID)***

Identyfikator DUID serwera jednoznacznie definiuje hosta serwera DHCPv6 w sieci. Jeśli serwer nie utworzył wcześniej jego duid, może użyć *nx_dhcpv6_server_set_duid,* aby go utworzyć. Zgodnie z dokumentem RFC 3315 serwer DHCPv6 musi zapisać ten identyfikator DUID w pamięci nieulotnej, aby można było go pobrać po ponownym uruchomieniu serwera. Serwer DHCPv6 obsługuje typy DUID Warstwa łącza, Czas warstwy łącza Enterprise (przypisany przez dostawcę). Należy pamiętać, że klient musi wysyłać bezpośrednio w typie dostawcy DUID. Opcja identyfikatorów DUID typu dostawcy (17) nie jest bezpośrednio obsługiwana przez serwer NetX Duo DHPv6.

Aplikacja hosta serwera DHCPv6 ma wartości domyślne przypisywania adresów IPv6, w tym limit czasu dzierżawy. Zobacz Opcje konfigurowalne w dalszej części tego dokumentu, aby dowiedzieć się, jak ustawić te opcje. :

Blok *sterowania IANA* zawiera pola T1 i T2. Blok *IA w* bloku sterowania *IANA* zawiera pola preferowanego i prawidłowego okresu istnienia. Aplikacja hosta ma konfigurowalne opcje zdefiniowane w innym miejscu tego dokumentu w celu ustawienia tych opcji. Są one przypisywane do wszystkich żądań adresów IPv6 klienta.

Te parametry dzierżawy ADRESU IP protokołu DHCPv6 są zdefiniowane poniżej.

T1 — czas w sekundach, gdy klient musi rozpocząć odnawianie adresu IPv6 z serwera, który go przypisał.

T2 — czas w sekundach, gdy klient musi rozpocząć ponowne powiązanie adresu IPv6, jeśli odnawianie nie powiodło się, z dowolnym serwerem w jego linku.

Preferowany okres istnienia — czas w sekundach, gdy adres klienta staje się przestarzały, jeśli klient nie został odnowiony lub nie został ponownie nawiązany. Klient nadal może używać tego adresu.

Prawidłowy okres istnienia — czas w sekundach, gdy adres IP klienta wygasł i NIE MOŻE używać tego adresu w jego transmisji sieciowych.

W dokumencie RFC zalecane są czasy T1 i T2, odpowiednio 0,5 i 0,8 preferowanego okresu istnienia w opcji *IANA* klienta. Jeśli serwer nie ma preferencji, należy ustawić te czasy na zero. Jeśli odpowiedź serwera zawiera wartości T1 i T2 ustawione na zero, klient może ustawić własne czasy T1 i T2.

**Ograniczenia**

Serwer NetX Duo DHCPv6 nie obsługuje następujących opcji protokołu DHCPv6:

  - Opcja szybkiego zatwierdzania, która optymalizuje proces żądania adresu DHCPv6 tylko do wymiany komunikatów na żądanie i odpowiedzi

  - Skonfiguruj ponownie opcję, która umożliwia serwerowi inicjowanie zmian stanu adresu IP klienta.

  - Opcja emisji pojedynczej; Wszystkie komunikaty klienta muszą być wysyłane na adres *All_DHCP_Relay_Agents_and_Servers* multiemisji, a nie bezpośrednio do serwera DHCPv6.

  - Skojarzenie tożsamości dla opcji Temporary Addresses(IA_TA), która jest tymczasowym adresem IP udzielonym klientowi.

  - Wiele opcji IA (adresów IPv6) na żądanie klienta

  - Host przekazywania między klientem DHCPv6 i serwerem, np. Klient i serwer muszą znajdować się w tej samej sieci.

  - Protokoły IPSec i uwierzytelnianie nie są obsługiwane w przypadku obsługi komunikatów DHCPv6. Jednak wystąpienie adresu IP może mieć włączoną obsługę protokołu IPSec w zależności od wersji oprogramowania NetX Duo w użyciu.

  - Serwer NetX Duo DHCPv6 bezpośrednio obsługuje tylko żądanie opcji serwera DNS. Może to ulec zmianie w przyszłych wersjach.

  - Opcja Delegowanie prefiksu nie jest obsługiwana.

  - Uwierzytelnianie komunikatów DHCPv6, chociaż protokół IPSec można włączyć w bazowym środowisku NetX Duo. Serwer DHCPv6 NetX Duo nie obsługuje również przekazywania połączeń z klientami. Zakłada się, że wszystkie żądania klienta pochodzą z hostów w sieci serwera.

## <a name="netx-duo-dhcpv6-server-callback-functions"></a>Funkcje wywołania zwrotnego serwera NetX Duo DHCPv6

*nx_dhcpv6_IP_address_declined_handler*

Gdy klient DHCPv6 wysyła komunikat o odmówień, serwer NetX Duo DHCPv6 oznacza adres jako niedostępny w tabelach adresów IPv6. Aby można było dostosować obsługę serwera dla tego komunikatu, nx_dhcpv6_IP_address_declined_handler *jest* dostarczany *.* Jednak to wywołanie zwrotne nie jest obecnie zaimplementowane.

*nx_dhcpv6_server_option_request_handler*

Gdy komunikat klienta DHCPv6 zawiera dane żądania opcji, serwer NetX Duo DHCPv6 przekazuje kod opcji żądania każdej opcji do tego wywołania zwrotnego użytkownika, jeśli został zdefiniowany. Dzięki temu serwer NetX Duo Server może pozwolić zdefiniowanej przez użytkownika funkcji wywołania zwrotnego na wypełnianie danych. Jednak ta funkcja nie jest obecnie zaimplementowana.

## <a name="supported-dhcpv6-rfcs"></a>Obsługiwane RFC DHCPv6

Protokół DHCPv6 NetX Duo jest zgodny ze specyfikacjami RFC3315, RFC3646 i powiązanymi RFC.