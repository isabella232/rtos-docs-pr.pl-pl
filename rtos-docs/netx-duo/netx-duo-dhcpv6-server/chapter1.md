---
title: Rozdział 1 — wprowadzenie do serwera DHCPv6 usługi Azure RTO NetX Duo
description: W tym dokumencie opisano szczegółowo, w jaki sposób serwer DHCPv6 NetX Duo przypisuje adresy IPv6 klientom DHCPv6.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6cf7baa91b1804876b97b1d75d1872d1120ad028
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821948"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-dhcpv6-server"></a>Rozdział 1 — wprowadzenie do serwera DHCPv6 usługi Azure RTO NetX Duo

W przypadku sieci IPv6 do uzyskiwania adresów IPv6 klienci muszą mieć protokół DHCPv6. Nie zastępuje protokołu DHCP, który jest ograniczony do protokołu IPv4, ponieważ nie oferuje on adresów IPv4. Protokół DHCPv6 ma podobne funkcje do protokołu DHCP, a także wiele ulepszeń. Klient, który nie ma lub nie może użyć automatycznej konfiguracji adresu IPv6, może używać protokołu DHCPv6 do przypisywania unikatowego globalnego adresu IPv6 z serwera DHCPv6.

NetX Duo został opracowany z myślą o obsłudze aplikacji opartych na sieci IPv6 i protokołów sieciowych, takich jak DHCPv6. W tym dokumencie opisano szczegółowo, w jaki sposób serwer DHCPv6 NetX Duo przypisuje adresy IPv6 klientom DHCPv6.

## <a name="dhcpv6-communication"></a>Komunikacja DHCPv6

**Struktura komunikatu protokołu DHCPv6**

Zawartość komunikatu jest zasadniczo nagłówkiem komunikatu, po którym następuje co najmniej jeden blok opcji (zwykle więcej). Poniżej znajduje się podstawowa struktura, w której każdy blok reprezentuje jeden bajt:

![Diagram przedstawiający strukturę bloku komunikatów i opcji.](media/image2.jpg)

**Rysunek 1. Struktura bloku komunikatów i opcji komunikatu protokołu DHCPv6**

Pole 1-bajtowe Msg-Type wskazuje typ komunikatu protokołu DHCPv6. 3-bajtowe pole identyfikatora transakcji jest ustawiane przez klienta. Może on mieć dowolną sekwencję znaków, ale musi być unikatowy dla każdego komunikatu klienta na serwerze (jest on obsługiwany przez zduplikowane komunikaty wysyłane przez klienta). Serwer używa tego identyfikatora transakcji dla każdej odpowiedzi dla klienta, aby umożliwić klientowi dopasowanie komunikatów serwera w przypadku pakietów, które są opóźnione lub opuszczone w sieci. Następujące opcje protokołu DHCPv6 są używane do wskazywania, do czego klient żąda.

Struktura opcji protokołu DHCPv6 składa się z kodu opcji, pola długości opcji, które nie zawiera pól Długość lub kod i na koniec danych opcji, które są co najmniej jednym polem kodu opcji 2 bajty dla danych, których żąda klient.

Niektóre bloki opcji mają opcje zagnieżdżone. Na przykład *skojarzenie tożsamości dla opcji nietymczasowy adres (IANA)* zawiera jedną lub więcej opcji *SKOJARZENIA tożsamości (IA)* , aby zażądać adresów IPv6. Opcja programu *Iana* zwrócona w komunikacie odpowiedzi serwera zawiera te same opcje *IA* z adresem IPv6 i czasami dzierżawy przyznanymi przez serwer, a także opcję *stanu* wskazującą, czy wystąpił błąd żądania adresu klienta.

Lista wszystkich bloków opcji wraz z ich opisem znajduje się w **dodatku A**.

**Typy komunikatów protokołu DHCPv6**

Mimo że protokół DHCPv6 znacznie rozszerza funkcjonalność protokołu DHCP, używa tej samej liczby komunikatów co serwer DHCP i obsługuje te same opcje dostawcy co serwer DHCP. Lista komunikatów protokołu DHCPv6 jest następująca:

- SOLICT (1) (wysłane przez klienta)
- ANONSowanie (2) (wysyłane przez serwer)
- ŻĄDANIE (3) (wysłane przez klienta)
- ODPOWIEDŹ (7) (wysłana przez serwer)
- POTWIERDZENIE (4) (wysłane przez klienta)
- Odnów (5) (Wysłany przez klienta)
- Rebind (6) (wysłane przez klienta)
- WYDANIE (8) (wysyłane przez klienta)
- Odrzuć (9) (Wysłany przez klienta)
- INFORM_REQUEST (11) (wysyłane przez klienta)
- Zmień konfigurację * (10) (wysyłanych przez serwer)

* Ponowne konfigurowanie nie jest obsługiwane przez serwer DHCPv6 NetX Duo.

Podstawowa sekwencja żądań DHCPv6 z odpowiednikiem typu komunikatu protokołu DHCPv4 w nawiasie jest następująca:

Klient ***żądanie** _ (_Discovery *) **anons** serwera*(Oferta *) **żądanie** klienta (* żądanie *) **odpowiedź** serwera (* DHCPACK *)

**Odnowienie** klienta (ta sama) **odpowiedź** z serwera (*DHCPACK*)

## <a name="dhcpv6-message-validation"></a>Sprawdzanie poprawności komunikatu protokołu DHCPv6

Identyfikator transakcji: Klient musi wygenerować identyfikator transakcji dla każdej wysyłanej wiadomości na serwer. Serwer DHCPv6 odrzuci komunikat od klienta, który nie pasuje do tego identyfikatora transakcji. Serwer z kolei musi używać tego samego identyfikatora transakcji w odpowiedzi z powrotem do klienta.

**Unikatowe identyfikatory protokołu DHCPv6 (DUIDs)**

Wszystkie komunikaty serwera muszą zawierać również unikatowy identyfikator protokołu DHCPv6 (DUID) w każdym komunikacie lub klient DHCPv6 nie powinien akceptować wiadomości. Identyfikator DUID warstwy łączy to blok sterowania zawierający adres MAC klienta, typ sprzętu i Typ identyfikatora DUID. Identyfikator DUID czasu warstwy linku (LLT) dodatkowo zawiera pole czasu, które zmniejsza prawdopodobieństwo, że identyfikator DUID nie będzie unikatowy w sieci hosta. Z tego powodu Specyfikacja RFC 3315 zaleca LLT DUIDs przez wszystkie DUIDs. Jeśli aplikacja hosta nie utworzy własnej unikatowej wartości czasu, NetX Duo DHCPv6 udostępni domyślny. Trzeci Typ identyfikatora DUID to numer DUID przedsiębiorstwa (przypisany przez dostawcę), który zawiera zarejestrowany Identyfikator przedsiębiorstwa (jako zarejestrowany w organizacji IANA) i dane prywatne, które są zmienne w typie i długości, na przykład na podstawie rozmiaru pamięci, typu systemu operacyjnego innej konfiguracji sprzętowej. Zapoznaj się z listą opcji konfiguracji w innym miejscu w tym dokumencie, aby skonfigurować przypisane wartości dostawcy serwera i identyfikator prywatny.

Klient musi również uwzględnić jego identyfikator DUID w swoich komunikatach na serwerze z wyjątkiem INFORM_REQUEST lub serwer odrzuci je.

**Sesje serwera klienta DHCPv6**

Klienci i serwery programu DHCPv6 wymieniają komunikaty za pośrednictwem protokołu UDP. Klient używa portu 546 do wysyłania i odbierania komunikatów DHCPv6, a serwer używa portu 547. Klient początkowo używa swojego adresu lokalnego łącza do przesyłania i otrzymywania komunikatów DHCPv6. Wysyła wszystkie komunikaty do serwerów DHCPv6 przy użyciu zastrzeżonego, w zakresie linku adresu multiemisji znanego jako *All_DHCP_Relay_Agents_and_Servers* adres multiemisji *(FF02:: 01:02)*.

Żądania przypisywania adresów ForIPv6, serwer DHCPv6 nasłuchuje komunikatów *żądania* wysyłanych do adresu *All_DHCP_Relay_Agents_and_Servers* . *W żądaniu żądania* klient może zażądać przypisania określonego adresu IPv6 lub pozwolić serwerowi na wybranie jednego z nich. Może również zażądać innych informacji o konfiguracji sieci z serwera.

Jeśli DHCPv6Server wyodrębnia prawidłowy komunikat *żądania* i może przypisać do klienta adres IPv6, reaguje na wiadomość *anonsu* zawierającą adres IPv6, który zostanie udzielony klientowi, czas dzierżawy adresu IPv6 i wszelkie dodatkowe informacje wymagane przez klienta. Jeśli klient zaakceptuje ofertę serwera, reaguje na komunikat *żądania* , co pozwoli serwerowi, że zaakceptuje adres IPv6. Serwer potwierdza, że klient jest powiązany z adresem IPv6 z komunikatem *odpowiedzi* .

Jeśli komunikat protokołu DHCPv6 klienta jest nieprawidłowy, serwer odrzuci komunikat w trybie dyskretnym. Jeśli serwer nie jest w stanie udzielić żądania, wyśle komunikat *odpowiedzi* z informacją o problemie w polu stan w programie Iana adresów IP. Jeśli otrzymano zduplikowane żądania klienta, serwer ponownie wyśle poprzednią odpowiedź DHCPv6, zakładając, że klient po prostu nie otrzymał tego pakietu.

Klient sprawdza, czy przypisany do niego adres IPv6 z serwera nie jest przypisany do innego hosta w systemie przy użyciu różnych protokołów IPv6, takich jak wykrywanie zduplikowanych adresów. Jeśli adres nie jest unikatowy, klient wyśle komunikat o *odrzuceniu* serwera. Serwer aktualizuje swoją tabelę dzierżaw IP przy użyciu tych informacji, co spowoduje nagranie przypisanego adresu. W międzyczasie klient musi ponownie uruchomić proces żądania protokołu DHCPv6 z innym komunikatem *żądania* .

Oprócz adresu IPv6 klient może również znać serwer DNS i inne informacje o sieci, takie jak nazwa domeny sieciowej. Protokół DHCPv6 udostępnia środki do żądania tych informacji przy użyciu żądań opcji w komunikatach *żądania i* *żądań* lub oddzielnie w komunikatach z *żądaniem informacji* . Opcje protokołu DHCPv6 zostały omówione w dalszej części tego rozdziału.

**Czas trwania dzierżawy protokołu IPv6**

Gdy serwer przypisze klientowi adres IPv6, przypisuje mu również czas trwania dzierżawy (okres istnienia) w obszarze IANA, w którym klient ma rozpocząć odnawianie (T1) lub ponowne wiązanie (T2) jego adresu IPv6 przy użyciu funkcji *Odnów* i ponownie *powiązać* komunikaty. Różnica między nimi polega na tym, że klient kieruje komunikat *odnowienia* do serwera przez uwzględnienie identyfikatora DUID serwera w żądaniu *odnowienia* . Nie określa jednak żadnego serwera, w związku z czym nie zawiera identyfikatora DUID serwera w komunikacie *rebind* do adresu *All_DHCP_Relay_Agents_and_Servers* . Opcja IA, która zawiera rzeczywisty adres IPv6, który serwer przydaje klientowi, zawiera również preferowane i prawidłowe okresy istnienia, gdy dzierżawiony adres IPv6 staje się przestarzały lub przestarzały (nieprawidłowy).

Serwer DHCPv6 NetX Duo utrzymuje limit czasu sesji dla każdego klienta, aby śledzić czas między komunikatami klienta. Jest to konieczne w przypadku, gdy host klienta utraci łączność lub sieć nie działa. Po upływie limitu czasu sesji zakłada się, że klient nie jest już zainteresowany ani nie może wykonywać żądań protokołu DHCPv6 serwera. Serwer usuwa rekord klienta i zwraca dowolny wstępnie przypisany adres IPv6 z powrotem do dostępnej puli. Czas oczekiwania sesji to konfigurowalna opcja użytkownika.

Jeśli klient chce zwolnić adres IPv6 lub odnajduje, że adres IPv6 przypisany do niego przez serwer DHCPv6 jest już używany, wysyła odpowiednio komunikat *Release* lub *Odrzuć* . W przypadku komunikatu o *wersji* serwer zwraca stan adresu IPv6 z powrotem do dostępnej puli. W przypadku komunikatu o *odrzuceniu* aktualizuje on tabelę dzierżaw IP, aby wskazać, że ten adres IPv6 nie jest dostępny (własnością innej jednostki w innym miejscu w sieci).

**Dane rekordu dzierżawy IPv6 i klienta**

Gdy serwer DHCPv6 rozpocznie akceptowanie żądań klienta, zachowuje listę aktywnych klientów, którzy żądają lub mają przypisane adresy IPv6. Serwer sprawdza wygaśnięcie dzierżawy adresów IP za pomocą czasomierza dzierżawy, który okresowo aktualizuje czas trwania dzierżawy klienta. Gdy czas trwania przekroczy prawidłowy okres istnienia, serwer wyczyści rekord klienta i zwróci jego adres IPv6 z powrotem do dostępnej puli. Klient może rozpocząć proces odnawiania/ponownego wiązania, aby to zrobić.

Tabela rekordu klienta serwera DHCPv6 NetX Duo zawiera informacje identyfikujące klientów i informacje o stanie dotyczące sprawdzania poprawności żądań klientów DHCPv6 oraz przypisywania lub ponownego przypisywania adresów IPv6. Takie informacje obejmują:

- Unikatowy identyfikator protokołu DHCPv6 klienta (DUID), który jednoznacznie definiuje każdy host klienta w sieci. Klient musi zawsze używać tego samego identyfikatora DUID dla wszystkich komunikatów protokołu DHCPv6.

- Skojarzenie tożsamości klienta dla adresów innych niż adresy tymczasowe (IANA) i adres IPv6 skojarzenia tożsamości (IA) łącznie, które definiują parametry przypisania adresu IPv6 klienta.

- Żądania opcji klienta (serwer DNS, nazwa domeny itp.).

- Adres źródłowy IPv6 klienta (jeśli jest ustawiony) i adres docelowy (jeśli nie multiemisji) ostatniego żądania protokołu DHCPv6.

- Klient jest ostatnim typem komunikatów i stanem DHCPv6.

## <a name="netx-duo-dhcpv6-server-requirements-and-constraints"></a>Wymagania i ograniczenia dotyczące serwera DHCPv6 NetX Duo

Interfejs API serwera DHCPv6 NetX Duo wymaga ThreadX 5,1 lub nowszego, a NetX Duo 5,5 lub nowszego.

**Wymagania**

***Konfiguracja zadania wątku IP***

Serwer DHCPv6 NetX Duo wymaga utworzenia wystąpienia IP na potrzeby wysyłania i otrzymywania komunikatów do protokołu DHCPv6 w jego łączech sieciowych. Odbywa się to za pomocą usługi *nx_ip_create* . Należy utworzyć sam serwer DHCPv6 NetX Duo. Odbywa się to za pomocą usługi *nx_dhcpv6_server_create* .

Protokół DHCPv6 wykorzystuje NetX Duo, ICMPv6 i UDP. W związku z tym przed użyciem serwera DHCPv6 należy najpierw włączyć protokół IPv6, wywołując następujące usługi NetX Duo:

- *nx_udp_enable*
- *nxd_ipv6_enable*
- *nxd_icmp_enable*

Ponadto, aby można było uruchomić serwer DHCPv6, będzie on miał kilka zadań konfiguracji do wykonania:

- Utwórz i sprawdź poprawność swoich linków lokalnych i adresów globalnych IPv6. Sprawdzanie poprawności adresu jest wykonywane automatycznie przez NetX Duo przy użyciu wykrywania duplikatów adresów, jeśli jest włączone. Zobacz *Podręcznik użytkownika programu NetX Duo* , aby uzyskać szczegółowe informacje na temat weryfikacji lokalnych i globalnych adresów IP.

- Ustaw indeks interfejsu sieciowego dla jego interfejsu DHCPv6.

- Utwórz zakres adresów IP dla adresów IPv6, które można przypisać. Lub jeśli dane istnieją z poprzedniej sesji protokołu DHCPv6 serwera, tabela dzierżawy IPv6 i rekordy klienta z tej sesji muszą zostać przekazane z nietrwałej pamięci do serwera DHCPv6. Mały przykładowy system w innym miejscu w tym dokumencie przedstawia usługi serwera DHCPv6 do realizacji tego wymagania.

- Ustaw identyfikator DUID serwera. Jeśli serwer utworzył swój identyfikator DUID w poprzedniej sesji, musi użyć tych samych danych do utworzenia tego samego identyfikatora DUID dla komunikatów dla klientów. Mały przykładowy system w innym miejscu w tym dokumencie pokazuje, jak to wymaganie jest spełnione.

W tym momencie serwer DHCPv6 jest gotowy do uruchomienia. Wewnętrznie serwer DHCPv6 NetX Duo utworzy gniazdo UDP powiązane z portem 547 i zacznie nasłuchiwanie żądań klientów.

***Wymagania dotyczące puli pakietów***

Serwer DHCPv6 NetX Duo wymaga puli pakietów do wysyłania komunikatów protokołu DHCPv6. Rozmiar puli pakietów pod względem ładunku pakietu i liczby dostępnych pakietów jest konfigurowany przez użytkownika i zależy od przewidywanej ilości komunikatów protokołu DHCPv6 i innych przesyłania aplikacji hosta.

Typowy komunikat protokołu DHCPv6 to około 200-300 bajtów w zależności od liczby dodatkowych opcji zażądanych przez klienta oraz informacji dostępnych na serwerze.

***Ustawianie interfejsu serwera DHCPv6***

Serwer DHCPv6 domyślnie przyjmuje podstawowy interfejs sieciowy jako interfejs, na którym będą akceptowane żądania klientów. Jednak aplikacja hosta musi nadal ustawić indeks adresów globalnych, który został użyty do utworzenia adresu globalnego serwera. Indeks interfejsu protokołu DHCPv6 i globalny indeks adresów są ustawiane za pomocą usługi *nx_dhcpv6_server_interface_set* . Przedstawiono to również w "małych przykładach" w tym dokumencie.

***Zapisywanie identyfikatora DUID protokołu DHCPv6 między ponownymi uruchomieniami serwera***

Protokół DHCPv6 wymaga, aby serwer używał tego samego identyfikatora DUID dla wielu ponownych uruchomień. Wszystkie dane używane do tworzenia identyfikatora DUID muszą być przechowywane i pobierane z pamięci nieulotnej na potrzeby tego wymagania. Dla hostów, które używają warstwy linku i identyfikatora DUID czasu, który wymaga dostępu do zegara w czasie rzeczywistym. Aplikacja hosta DHCPv6 NetX Duo powinna obejmować dostęp do danych w czasie rzeczywistym w celu wygenerowania wartości czasu dla początkowego tworzenia identyfikatora DUID serwera i przechowywania tych danych do ponownego użycia na kolejnych sesjach serwera. *Nx_dhcpv6_set_server_duid* następnie pobiera dane identyfikatora DUID jako ich argumenty, a także opcje konfiguracji, w zależności od typu identyfikatora DUID, do produkcji (lub odtworzenia) własnego identyfikatora DUID.

***Tworzenie listy adresów IPv6 do przypisania***

Po utworzeniu serwera DHCPv6 aplikacja hosta serwera musi utworzyć zakres możliwych do przypisania adresów IPv6, jeśli nie ma wcześniej przechowywanych danych listy adresów IP. Jest to realizowane za pomocą usługi *nx_dhcpv6_create_ip_address_range*, która przyjmuje jako wejściowy i końcowy adres IPv6.

***Zapisywanie danych o adresie i kliencie przypisanych do protokołu DHCPv6***

Protokół DHCPv6 wymaga, aby serwer DHCPv6 zapisywał dane klienta i adresu IPv6 w magazynie nietrwałym w przypadku ponownego rozruchu serwera. Serwer DHCPv6 NetX Duo zawiera kilka interfejsów API do przekazywania i pobierania danych adresów klienta i IPv6 do i z serwera DHCPv6 odpowiednio:

*nx_dhcpv6_add_client_record*

*nx_dhcpv6_add_ip_address_lease*

*nx_dhcpv6_retrieve_client_record*

*nx_dhcpv6_retrieve_ip_address_lease*

Przed ponownym uruchomieniem serwera należy wykonać przekazywanie danych na serwer. Pobieranie danych należy wykonać tylko po zatrzymaniu lub wstrzymaniu serwera DHCPv6. Usługi do wykonania te zostały szczegółowo opisane w dalszej części tego dokumentu. Jednak protokół DHCPv6 NetX Duo nie określa dostępu do magazynu nietrwałego. Ta wartość musi być obsługiwana przez aplikację hosta. Niewielki przykład pokazuje, jak działa aplikacja hosta.

***Unikatowy identyfikator DHCP serwera (DUID)***

Identyfikator DUID serwera jednoznacznie definiuje hosta serwera DHCPv6 w sieci. Jeśli serwer nie utworzył wcześniej identyfikatora DUID, można go utworzyć przy użyciu *nx_dhcpv6_server_set_duid* . Zgodnie z dokumentem RFC 3315 serwer DHCPv6 musi zapisać ten identyfikator DUID w pamięci nieulotnej, aby mógł go pobrać po ponownym uruchomieniu serwera. Serwer DHCPv6 obsługuje warstwy linków, łącznego czasu warstwy i jednostki (przypisane przez dostawcę). Należy pamiętać, że klient musi bezpośrednio wysłać w typie DUID dostawcy. Opcja dla typu dostawcy DUIDs (17) nie jest bezpośrednio obsługiwana przez serwer NetX Duo DHPv6.

Aplikacja hosta serwera DHCPv6 ma domyślne wartości przypisywania adresów IPv6, w tym limit czasu dzierżawy. Zobacz sekcję konfigurowalne opcje w dalszej części tego dokumentu, aby dowiedzieć się, jak ustawić te opcje. :

Blok sterowania *Iana* zawiera pola T1 i T2. Blok *IA* w bloku sterowania *Iana* zawiera pola preferowany i prawidłowy okres istnienia. Aplikacja hosta ma konfigurowalne opcje zdefiniowane w innym miejscu w tym dokumencie, aby ustawić te opcje. Są one przypisane do wszystkich żądań adresów IPv6 klienta.

Te parametry dzierżawy adresów IP protokołu DHCPv6 są zdefiniowane poniżej.

T1 — czas w sekundach, po którym klient musi rozpocząć Odnawianie adresu IPv6 z serwera, który go przypisał.

T2 — czas w sekundach, po którym klient musi rozpocząć ponowne wiązanie adresu IPv6, jeśli odnowienie nie powiodło się, z dowolnym serwerem w jego łączu.

Preferowany okres istnienia — czas w sekundach, po którym adres klienta staje się przestarzały, jeśli klient nie zostanie odnowiony ani odwiązany. Klient nadal może używać tego adresu.

Prawidłowy okres istnienia — czas w sekundach, po upływie którego wygasł adres IP klienta i nie może używać tego adresu w transmisjach sieciowych.

Specyfikacja RFC zaleca użycie czasu T1 i T2 odpowiednio 0,5 i 0,8 z preferowanym okresem istnienia w opcji programu Client *Iana* . Jeśli serwer nie ma preferencji, należy ustawić te czasy na zero. Jeśli odpowiedź serwera zawiera czas T1 i T2 ustawiony na zero, pozwala klientowi ustawić własne czasy T1 i T2.

**Ograniczenia**

Serwer DHCPv6 NetX Duo nie obsługuje następujących opcji protokołu DHCPv6:

  - Opcja szybkiego zatwierdzania, która optymalizuje proces żądania adresu DHCPv6 tylko do wymiany wiadomości na żądanie i odpowiedź

  - Opcja Zmień konfigurację, która pozwala serwerowi inicjować zmiany stanu adresu IP klienta.

  - Opcja emisji pojedynczej; wszystkie komunikaty klienta muszą być wysyłane na adres *All_DHCP_Relay_Agents_and_Servers* multiemisji, a nie bezpośrednio do serwera DHCPv6.

  - Skojarzenie tożsamości dla opcji adresy tymczasowe (IA_TA), która jest tymczasowym adresem IP przyznanym klientowi.

  - Wiele opcji IA (IPv6 addresss) na żądanie klienta

  - Host przekazywania między klientem i serwerem DHCPv6, np. klientem i serwerem, musi znajdować się w tej samej sieci.

  - Protokół IPSec i uwierzytelnianie nie są obsługiwane w komunikatach protokołu DHCPv6. Jednak wystąpienie protokołu IP może być włączone IPSec w zależności od używanej wersji programu NetX Duo.

  - Serwer DHCPv6 NetX Duo bezpośrednio obsługuje tylko żądanie opcji serwera DNS. Może to ulec zmianie w przyszłych wersjach.

  - Opcja delegowania prefiksu nie jest obsługiwana.

  - Uwierzytelnianie komunikatów protokołu DHCPv6, chociaż można je włączyć w źródłowym środowisku NetX Duo. Serwer DHCPv6 NetX Duo nie obsługuje połączeń przekaźników z klientami. Przyjmuje się, że wszystkie żądania klientów pochodzą z hostów w sieci serwerów.

## <a name="netx-duo-dhcpv6-server-callback-functions"></a>Funkcje wywołania zwrotnego serwera DHCPv6 NetX Duo

*nx_dhcpv6_IP_address_declined_handler*

Gdy klient DHCPv6 wyśle komunikat o odrzuceniu, serwer DHCPv6 NetX Duo oznaczy adres jako niedostępny w swoich tabelach adresów IPv6. Aby można było dostosować obsługę serwera w tym komunikacie, zostanie udostępniona *nx_dhcpv6_IP_address_declined_handler* *.* Jednak to wywołanie zwrotne nie jest obecnie zaimplementowane.

*nx_dhcpv6_server_option_request_handler*

Gdy komunikat klienta DHCPv6 zawiera dane żądania opcji, serwer DHCPv6 NetX Duo przekazuje każdy kod opcji żądania do tego wywołania zwrotnego użytkownika, jeśli jest zdefiniowany. Dzięki temu serwer NetX Duo może umożliwić użytkownikowi wypełnienie danych za pomocą wywołania zwrotnego zdefiniowanego przez użytkownika. Jednak ta funkcja nie jest obecnie zaimplementowana.

## <a name="supported-dhcpv6-rfcs"></a>Obsługiwane specyfikacje RFC protokołu DHCPv6

Protokół DHCPv6 NetX Duo jest zgodny z RFC3315, RFC3646 i powiązanymi specyfikacjami RFC.