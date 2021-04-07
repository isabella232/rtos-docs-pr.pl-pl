---
title: Rozdział 3 — Opis funkcjonalny usługi Azure RTO NetX Secure DTLS
description: Ten rozdział zawiera opis funkcjonalny usługi Azure RTO NetX Secure DTLS.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 347bd83fa8c72ced2e8678a92ec5c5f8393c136d
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550205"
---
# <a name="chapter-3-functional-description-of-azure-rtos-netx-secure-dtls"></a>Rozdział 3: Opis funkcjonalny usługi Azure RTO NetX Secure DTLS

## <a name="execution-overview"></a>Przegląd wykonywania

Ten rozdział zawiera opis funkcjonalny usługi Azure RTO NetX Secure DTLS. Istnieją dwa podstawowe typy wykonywania programu w aplikacji NetX Secure DTLS: inicjalizacje i wywołania interfejsu aplikacji. 

Zabezpieczenia NetX zakładają istnienie ThreadX i NetX/NetXDuo. Z ThreadX wymaga wykonania wątku, zawieszenia, okresowe czasomierze i wzajemnych wykluczeń. Z NetX/NetXDuo wymaga, aby urządzenia i sterowniki sieci UDP i IP były obsługiwane.

## <a name="datagram-transport-layer-security-dtls-and-transport-layer-security-tls"></a>Datagram Transport Layer Security (DTLS) i Transport Layer Security (TLS)

NetX Secure DTLS implementuje protokół datagram Transport Layer Security w wersji 1,2 zdefiniowanej w dokumencie RFC 6347. DTLS w wersji 1,0 została zdefiniowana w RFC 4347 i zgodna z wersją TLS 1,1. Ze względu na to, że DTLS jest zasadniczo rozszerzeniem protokołu TLS, zdecydowano, że następna wersja będzie używać tego samego numeru wersji, co w odpowiedniej wersji protokołu TLS. W takim przypadku nie istnieje DTLS wersja 1,1, ponieważ DTLS wersja 1,2 odpowiada wersji TLS 1,2.

> [!NOTE]
> NetX Secure obsługuje DTLS w wersji 1,2. DTLS 1,0 (RFC 4347) **nie** jest obecnie obsługiwany.

*Secure Sockets Layer* (SSL) była oryginalną nazwą protokołu TLS, zanim stała się standardem RFC 2246 i "SSL" jest często używana jako nazwa ogólna dla protokołów TLS. Ostatnia wersja protokołu SSL to 3,0, a protokół TLS 1,0 jest czasami określany jako wersja SSL 3,1. Wszystkie wersje oficjalnego protokołu "SSL" są uznawane za przestarzałe i niezabezpieczone, a obecnie NetX Secure nie zapewnia implementacji protokołu SSL.

TLS określa protokół do generowania *kluczy sesji* , które są tworzone podczas *uzgadniania* protokołu TLS między klientem i serwerem TLS, a te klucze są używane do szyfrowania danych wysyłanych przez aplikację podczas sesji TLS *.*

DTLS jest ściśle sprzężone z protokołem TLS, ponieważ podstawowe mechansims zabezpieczeń są współużytkowane przez protokoły. Protokół TLS jest jednak przeznaczony do pracy za pośrednictwem protokołu warstwy transportowej, który zapewnia gwarancje dotyczące dostarczania pakietów i ich kolejności (prawie zawsze protokół TCP w rzeczywistości) i nie będzie działać za pośrednictwem zawodnego protokołu, takiego jak UDP. Jest to dokładne z powodu protokołu UDP, który DTLS został wprowadzony: DTLS został zaprojektowany w celu obsługi niezawodnego charakteru protokołów UDP i podobnych. Robi to poprzez uwzględnienie logiki określania kolejności i niezawodności (np. retransmisje porzuconych danych) Podobnie jak w przypadku niezawodnych protokołów, takich jak TCP.

Pełne Omówienie protokołu TLS znajduje się w rozdziale 3 podręcznika użytkownika protokołu Secure TLS NetX, więc ten dokument koncentruje się na różnicach między protokołami TLS i DTLS.

### <a name="dtls-record-header"></a>DTLS — nagłówek rekordu

Każdy prawidłowy rekord DTLS musi mieć nagłówek DTLS, jak pokazano na rysunku 1. Nagłówek jest taka sama jak w przypadku protokołu TLS z dodaniem dwóch nowych pól: 16-bitowa *Epoka* i 48-bitowy *numer sekwencyjny* opisany poniżej.

![Diagram nagłówka rekordu DTLS.](media/image2.png)

**Rysunek 1 — nagłówek rekordu DTLS**

Pola nagłówka rekordu TLS są zdefiniowane w następujący sposób:

| Pole nagłówka TLS | Przeznaczenie  |
| ---------------- | --------- |
| **8-bitowy typ komunikatu** | To pole zawiera typ wysyłanego rekordu DTLS. Prawidłowe typy są następujące:<br />- ChangeCipherSpec: 0x14<br />-Alert: 0x15<br />-Uzgadnianie: 0x16<br />-Dane aplikacji: 0x17<br /> |
| **16-bitowa wersja protokołu** | To pole zawiera wersję protokołu DTLS. Prawidłowe wartości są następujące:<br />-DTLS 1,1:0xFEFD |
|  **16-bitowa Epoka** |  To pole zawiera DTLS "epoki", czyli licznik, który jest zwiększany za każdym razem, gdy stan szyfrowania zostanie zmieniony (na przykład podczas generowania nowych kluczy sesji).  |
|  **48-bitowy numer sekwencji** |  To pole zawiera numer sekwencyjny, który identyfikuje ten konkretny rekord. Jest on używany przez DTLS do zachowywania kolejności rekordów i sprawdzania, czy są wymagane retransmisje. |
|  **16-bitowa Długość** |  To pole zawiera długość danych hermetyzowanych w rekordzie DTLS.  |

### <a name="dtls-handshake-record-header"></a>Nagłówek rekordu uzgadniania DTLS

Każdy prawidłowy rekord uzgadniania DTLS musi mieć nagłówek uzgadniania DTLS, jak pokazano na rysunku 2.

![Diagram nagłówka rekordu uzgadniania DTLS.](media/image3.png)

**Rysunek 2 — nagłówek rekordu uzgadniania DTLS**

Pola nagłówka rekordu uzgadniania DTLS są zdefiniowane w następujący sposób:

| Pole nagłówka TLS | Przeznaczenie  |
| ---------------- | ------------------------------------------------ |
| **8-bitowy typ komunikatu** | To pole zawiera typ wysyłanego rekordu DTLS. Prawidłowe typy są następujące:<br />- ChangeCipherSpec: 0x14<br />-Alert: 0x15<br />-Uzgadnianie: 0x16<br />-Dane aplikacji: 0x17 |
|  **16-bitowa Epoka** | To pole zawiera DTLS "epoki", czyli licznik, który jest zwiększany za każdym razem, gdy stan szyfrowania zostanie zmieniony (na przykład podczas generowania nowych kluczy sesji). |
|  **48-bitowy numer sekwencji** | To pole zawiera numer sekwencyjny, który identyfikuje ten konkretny rekord. Jest on używany przez DTLS do zachowywania kolejności rekordów i sprawdzania, czy są wymagane retransmisje. |
|  **16-bitowa wersja protokołu** | To pole zawiera wersję protokołu DTLS. Prawidłowe wartości są następujące:<br />-DTLS 1,1:0xFEFD |
| **16-bitowa Długość** | To pole zawiera długość danych hermetyzowanych w rekordzie DTLS. |
| **Typ uzgadniania 8-bitowego** | To pole zawiera typ komunikatu uzgadniania. Prawidłowe wartości są następujące:<br />-HelloRequest: 0x00<br />-Komunikacie ClientHello: 0x01<br />-ServerHello: 0x02<br />-Certificate: 0x0B<br />- ServerKeyExchange: 0x0C<br />-CertificateRequest: 0x0D<br />- ServerHelloDone: 0x0E<br />- CertificateVerify: 0x0F<br />-ClientKeyExchange: 0x10<br />-Zakończono: 0x14 |
| **Długość 24-bitowa** | To pole zawiera długość danych komunikatu uzgadniania. |
| **16-bitowy numer sekwencji** | To pole zawiera numer sekwencyjny. |

### <a name="the-dtls-handshake-and-dtls-session"></a>Uzgadnianie DTLS i DTLS

Typowe uzgadnianie DTLS jest pokazane na rysunku 3. Jest niemal identyczna z typowym uzgadnianiem protokołu TLS z istotną różnicą — gdy wiadomość komunikacie ClientHello jest wysyłana po raz pierwszy, serwer odpowie przy użyciu nowego komunikatu DTLS, *HelloVerifyRequest* zawierającego plik cookie. Aby można było kontynuować uzgadnianie, klient programu DTLS musi odpowiedzieć na drugą wiadomość komunikacie ClientHello zawierającą ten plik cookie. Ten mechanizm został dodany do DTLS w celu zapobiegania określonym atakom typu "odmowa usługi" (DoS), ponieważ UDP jest protokołem bezpołączeni (protokół TCP wymaga dedykowanego połączenia/portu, tak aby protokół TLS nie odczuwał tego samego problemu).

Uzgadnianie DTLS rozpoczyna się, gdy klient wysyła komunikat *komunikacie ClientHello* do serwera DTLS, co wskazuje na to, że wolisz rozpocząć sesję DTLS. Komunikat zawiera informacje o szyfrowaniu, którego klient ma używać dla sesji, wraz z informacjami użytymi do wygenerowania kluczy sesji w dalszej części uzgadniania. Do momentu wygenerowania kluczy sesji wszystkie komunikaty w uzgadnianiu DTLS nie są szyfrowane. Jak wspomniano powyżej, serwer DTLS może wysłać HelloVerifyRequest w odpowiedzi na komunikacie ClientHello, wymuszając klientowi odpowiedź z drugim zaktualizowanym komunikacie ClientHello.

Po odebraniu drugiego komunikatu komunikacie ClientHello serwer DTLS sprawdzi plik cookie, a w przypadku poprawnego działania zostanie wyświetlony komunikat ServerHello wskazujący na wybór opcji szyfrowania dostarczonych przez klienta. ServerHello następuje komunikat certyfikatu, w którym serwer udostępnia certyfikat cyfrowy do uwierzytelniania tożsamości klienta (jeśli jest używana weryfikacja X. 509). Na koniec serwer wysyła komunikat ServerHelloDone, aby wskazać, że nie ma więcej komunikatów do wysłania. Serwer może opcjonalnie wysyłać inne komunikaty po ServerHello i w niektórych przypadkach może nie wysłać komunikatu certyfikatu (na przykład gdy używane są klucze wstępne), w związku z czym konieczność komunikatu ServerHelloDone.

Gdy klient otrzyma wszystkie komunikaty serwera, ma wystarczającą ilość informacji do wygenerowania kluczy sesji. Protokół TLS/DTLS polega na utworzeniu udostępnionego bitu danych losowych nazywanych *wstępnie głównym kluczem tajnym*, który jest stałym rozmiarem i jest używany jako inicjator do generowania wszystkich kluczy wymaganych po włączeniu szyfrowania. Wstępnie główny klucz tajny jest szyfrowany przy użyciu algorytmu klucza publicznego (np. RSA) określonego w komunikatach Hello (zobacz poniżej, aby uzyskać informacje o algorytmach klucza publicznego) i klucz publiczny dostarczony przez serwer w jego certyfikacie. Opcjonalna funkcja TLS/DTLS o nazwie klucze wstępne (PSK) umożliwia ciphersuites, które nie korzystają z certyfikatu, ale zamiast tego używają wartości tajnej udostępnianej między hostami (zwykle za pomocą fizycznego transferu lub innej zabezpieczonej metody). Po włączeniu klucza PSK klucz tajny jest używany do generowania wstępnie głównego wpisu tajnego. Zapoznaj się z sekcją dotyczącą kluczy wstępnych w sekcji "metody uwierzytelniania" poniżej.

W przypadku zwykłego uzgadniania protokołów TLS/DTLS zaszyfrowany wstępnie główny klucz tajny jest wysyłany do serwera w komunikacie ClientKeyExchange. Serwer, po odebraniu komunikatu ClientKeyExchange, odszyfrowuje wstępnie główny klucz tajny przy użyciu jego klucza prywatnego i kontynuuje generowanie kluczy sesji równolegle z klientem TLS/DTLS.

Po wygenerowaniu kluczy sesji wszystkie dalsze komunikaty mogą być szyfrowane przy użyciu algorytmu klucza prywatnego (np. AES) wybranego w komunikatach Hello. Jeden końcowy komunikat niezaszyfrowany o nazwie ChangeCipherSpec jest wysyłany przez klienta i serwer, aby wskazać, że wszystkie dalsze komunikaty będą szyfrowane.

Pierwszy szyfrowany komunikat Wysłany przez klienta i serwer jest również końcowym komunikatem uzgadniania protokołu TLS o nazwie zakończony. Ten komunikat zawiera skrót wszystkich odebranych i wysłanych komunikatów uzgadniania. Ten skrót służy do sprawdzania, czy żaden z komunikatów w uzgadnianiu nie został naruszony ani uszkodzony (ze wskazaniem potencjalnego naruszenia zabezpieczeń).

Po odebraniu ukończonych komunikatów i sprawdzeniu wartości skrótu uzgadniania rozpocznie się sesja TLS/DTLS, a aplikacja zacznie wysyłać i odbierać dane. Wszystkie dane wysyłane po obu stronach sesji TLS/DTLS są najpierw tworzone przy użyciu algorytmu wyznaczania wartości skrótu wybranego w komunikatach Hello (w celu zapewnienia integralności komunikatów) i zaszyfrowanego przy użyciu wybranego algorytmu klucza prywatnego z wygenerowanymi kluczami sesji.

Na koniec sesja TLS/DTLS może zostać zakończona pomyślnie tylko wtedy, gdy klient lub serwer wybierze tę opcję. Obcięta sesja jest uznawana za naruszenie zabezpieczeń (ponieważ osoba atakująca może próbować uniemożliwić odbieranie wszystkich danych), więc zostanie wysłane specjalne powiadomienie, gdy jedna strona chce zakończyć sesję, nazywaną alertem CloseNotify. Zarówno klient, jak i serwer muszą wysyłać i przetwarzać alert CloseNotify o pomyślnym zamknięciu sesji.

![Diagram typowej sesji uzgadniania DTLS.](media/image4.png)

**Rysunek 3 — typowe uzgadnianie DTLS**

### <a name="initialization"></a>Inicjalizacja

Stos NetX lub NetXDuo musi być zainicjowany przed użyciem NetX Secure DTLS. Informacje o tym, jak poprawnie zainicjować stos TCP/IP dla operacji UDP, można znaleźć w podręczniku użytkownika NetX lub NetXDuo.

Po zainicjowaniu protokołu UDP NetX można włączyć funkcję DTLS. Wewnętrznie cały ruch sieciowy i przetwarzanie DTLS są obsługiwane przez stos NetX/NetXDuo bez konieczności interwencji użytkownika. Jednak DTLS ma pewne konkretne wymagania, które muszą być obsługiwane niezależnie od bazowego stosu sieciowego. DTLS operacji klienta te parametry są przypisywane do bloku sterowania DTLS o nazwie ***NX_SECURE_DTLS_SESSION** _. W przypadku operacji serwera DTLS blok sterowania jest wywoływany _ *_NX_SECURE_DTLS_SERVER_** i zawiera infrastrukturę wymaganą do obsługi wielu sesji DTLS na jednym porcie UDP — należy zauważyć, że różni się to od protokołu TLS, gdzie każda sesja TLS jest powiązana z pojedynczym portem TCP.

Dwa tryby DTLS, serwer i klient mogą być włączone w aplikacji (ale tylko jeden tryb na gniazdo NetX), a każdy z nich ma własne określone wymagania, szczegółowo poniżej.

### <a name="initialization--dtls-server"></a>Inicjowanie — serwer DTLS

Tryb bezpiecznego serwera usługi NetX DTLS różni się od trybu serwera TLS ze względu na użycie protokołu UDP dla bazowego protokołu transportu sieciowego. W przypadku protokołu TCP port jest powiązany z pojedynczym hostem zdalnym na czas trwania sesji TLS. Protokół UDP nie ma pojęcia dotyczącego stanu w odniesieniu do hosta zdalnego, dlatego żądania DTLS z różnych hostów będą odbierane w tym samym interfejsie UDP. W związku z tym DTLS musi zachować stan sesji zamiast polegać na gnieździe tak jak w przypadku protokołów TLS i TCP. Z tego powodu blok sterowania serwerem DTLS (NX_SECURE_DTLS_SERVER) zachowuje mapowanie informacji o hoście zdalnym (adres IP i port) do sesji DTLS. Wszystkie dane przychodzące w gnieździe UDP przypisanym do serwera DTLS zostaną zmapowane do istniejącej lub nowej sesji DTLS na podstawie hosta zdalnego. Z tego powodu Tworzenie serwera DTLS wymaga kilku dodatkowych parametrów wykraczających poza potrzeb klientów TLS i DTLS.

Oprócz DTLS Server Control Block, TLS ciphersuites i cipher ScratchSpace/Metadata buffer, serwery DTLS wymagają buforu do obsługi sesji DTLS i bufora ponownego asemblowania pakietów używany do odszyfrowywania przychodzących rekordów DTLS.

Oprócz buforów sesji serwery DTLS wymagają *certyfikatu cyfrowego*, który jest dokumentem używanym do identyfikowania serwera TLS na potrzeby połączenia z klientem TLS i certyfikatami odpowiadającymi *kluczem prywatnym*, zazwyczaj dla algorytmu szyfrowania RSA. Międzynarodowy związek telekomunikacyjny X. 509 standard określa format certyfikatu używany przez protokół TLS/DTLS i istnieje wiele narzędzi do tworzenia certyfikatów cyfrowych X. 509.

W przypadku NetX Secure DTLS certyfikat X. 509 musi być zakodowany binarnie przy użyciu formatu Distinguished Encoding Rules (DER) z numerem ASN. 1. Algorytm DER to standardowy format binarny protokołu TLS dla certyfikatów.

Klucz prywatny skojarzony z podanym certyfikatem musi mieć format PKCS # 1 DER-Encoded. Klucz prywatny jest używany tylko na urządzeniu i nigdy nie będzie przesyłany przez sieć. Utrzymuj bezpieczeństwo kluczy prywatnych, ponieważ zapewniają one zabezpieczenia dotyczące komunikacji TLS/DTLS.

Aby można było zainicjować certyfikat serwera DTLS, aplikacja musi udostępnić wskaźnik do buforu zawierającego certyfikat X. 509 szyfrowany algorytmem DER oraz opcjonalne dane klucza prywatnego PKCS # 1 RSA z użyciem usługi ***nx_secure_x509_certificate_intialize*** , która wypełnia strukturę **NX_SECURE_X509_CERT** odpowiednimi danymi certyfikatu do użycia przez protokół TLS.

Po zainicjowaniu certyfikatu serwera należy go dodać do bloku kontroli protokołu TLS przy użyciu usługi ***nx_secure_dtls_server_local_certificate_add*** .

Po dodaniu certyfikatu serwera do bloku sterowania serwerem DTLS serwer może być używany do bezpiecznej komunikacji DTLS (Zobacz przykład powyżej).

### <a name="initialization--dtls-client"></a>Inicjowanie — klient DTLS

NetX bezpieczny tryb klienta DTLS jest prosty w porównaniu z serwerem DTLS, ponieważ istnieje tylko jedno połączenie wychodzące do hosta zdalnego za pośrednictwem gniazda UDP.

Aby skonfigurować klienta programu DTLS, wymagany jest *Magazyn zaufanych certyfikatów*, który jest kolekcją certyfikatów cyfrowych X. 509 szyfrowanych z zaufanych urzędów certyfikacji (CA). Te certyfikaty są zakładane przez protokół DTLS jako "zaufany" i stanowią podstawę do uwierzytelniania certyfikatów dostarczonych przez jednostki DTLS serwera do aplikacji klienta NetX Secure DTLS.

Certyfikat zaufanego urzędu certyfikacji może być *podpisany z podpisem własnym* lub podpisany przez inny urząd certyfikacji, w którym to przypadku certyfikat jest nazywany *POśrednim urzędem certyfikacji* (ICA). W typowej aplikacji TLS/DTLS serwer udostępnia certyfikaty usługi ICA wraz z certyfikatem serwera, ale Jedynym wymaganiem do pomyślnego uwierzytelnienia jest to, że łańcuch wystawców (certyfikaty służące do podpisywania innych certyfikatów) może być śledzony z certyfikatu serwera z powrotem do certyfikatu zaufanego urzędu certyfikacji w zaufanym magazynie certyfikatów. Ten łańcuch jest znany jako *łańcuch zaufania* lub *łańcuch certyfikatów*.

Aby zainicjować zaufany urząd certyfikacji lub certyfikat usługi ICA, aplikacja musi udostępnić wskaźnik do buforu zawierającego certyfikat X. 509 szyfrowany algorytmem DER przy użyciu usługi ***nx_secure_x509_certificate_intialize** _, która wypełnia strukturę _ *NX_SECURE_X509_CERT** z odpowiednimi danymi certyfikatu do użycia przez protokół TLS.

Klient DTLS potrzebuje również miejsca na przydzielenie certyfikatu serwera przychodzącego (przy założeniu, że tryb klucza wstępnego nie jest używany) i bufor do asemblera pakietów do rekordów DTLS do odszyfrowania. Te bufory są przesyłane jako parametry do usługi ***nx_secure_dtls_session_create*** (zobacz Dokumentacja interfejsu API, aby uzyskać więcej informacji).

Zaufane certyfikaty, które zostały zainicjowane, są następnie dodawane do utworzonego bloku sterowania sesją DTLS za pomocą usługi ***nx_secure_dtls_session_trusted_certificate_add*** . Niedodanie certyfikatu spowoduje niepowodzenie sesji klienta DTLS, ponieważ nie będzie można uwierzytelnić hostów serwera zdalnego przy użyciu protokołu DTLS.

Po utworzeniu magazynu zaufanych certyfikatów można użyć tej sesji w celu nawiązania bezpiecznego połączenia z klientem TLS.

### <a name="application-interface-calls"></a>Wywołania interfejsu aplikacji

NetX Secure DTLS aplikacje zazwyczaj będą wykonywać wywołania funkcji z poziomu wątków aplikacji działających w ramach RTO ThreadX. Niektóre inicjalizacje, szczególnie w przypadku źródłowych protokołów komunikacji sieciowej (np. UDP i IP), mogą być wywoływane z programu ***tx_application_define *.** Więcej informacji na temat inicjowania komunikacji sieciowej można znaleźć w podręczniku użytkownika NetX/NetXDuo.

DTLS intensywnie wykorzystuje procedury szyfrowania, które są operacjami wymagającymi użycia procesora. Zwykle te operacje będą wykonywane w kontekście wywołania wątku.

### <a name="dtls-session-start"></a>Rozpoczęcie sesji DTLS

DTLS wymaga podstawowego protokołu sieciowego transportu warstwowego do działania. Zazwyczaj używany jest protokół TCP. Aby ustanowić NetX bezpieczną sesję TLS, należy utworzyć **NX_UDP_SOCKET** i przesłać ją do usługi **_NX_SECURE_DTLS_CLIENT_SESSION_START_** dla klientów DTLS.

Serwery DTLS działają inaczej. Gniazdo UDP używane na potrzeby przychodzących żądań klienta DTLS jest zawarte w bloku sterowania NX_SECURE_DTLS_SERVER i jest inicjowane w wywołaniu ***nx_secure_dtls_server_create** _, które pobiera lokalny port UDP jako parametr. _*_Nx_secure_dtls_server_start_*_ usługi jest następnie używany do uruchomienia serwera DTLS do obsługi żądań przychodzących. Wszystkie żądania przychodzące są obsługiwane w procedurach wywołania zwrotnego dostarczonych do _nx_secure_dtls_server_create *: jeden dla połączeń i jeden do odbierania powiadomień. Jest to aplikacja do obsługi uruchamiania sesji DTLS po odebraniu powiadomienia o połączeniu (wywołanie zwrotne powiadomienia o nawiązaniu połączenia jest wywoływane przez DTLS) przez wywołanie ***nx_secure_dtls_server_session_start**_. Aplikacja musi również obsługiwać przychodzące dane po wywołaniu wywołania zwrotnego powiadomienia o odebraniu (które następuje po zakończeniu uzgadniania DTLS) przez wywołanie _ *_nx_secure_dtls_session_receive_* *. Szczegóły tego elementu są podane w powyższym przykładzie i w dokumentacji interfejsu API dla każdej z powyższych wymienionych usług.

### <a name="dtls-packet-allocation"></a>Alokacja pakietu DTLS

NetX Secure DTLS używa tej samej struktury pakietów co NetX/NetXDuo TCP (***NX_PACKET** _), z wyjątkiem tego, że zamiast wywoływania usługi _*_nx_packet_allocate_*_ , należy wywołać usługę _ *_nx_secure_dtls_packet_allocate_**, aby miejsce dla nagłówka DTLS mogło zostać prawidłowo przydzieloną.

### <a name="dtls-session-send"></a>Wysyłanie sesji DTLS

Po rozpoczęciu sesji TLS aplikacja może wysyłać dane przy użyciu usługi ***nx_secure_dtls_session_send*** . Usługa Send jest identyczna z użyciem do usługi ***nx_udp_socket_send** _, pobierając strukturę danych _ *_NX_PACKET_** zawierające przesyłane dane, docelowy adres IP i docelowy port UDP.

> [!IMPORTANT]
> Podczas wysyłania danych przy użyciu nx_secure_dtls_session_send należy używać tego samego adresu IP i portu, który został użyty do ustanowienia sesji DTLS, chyba że istnieje mechanizm przenoszenia sesji na nowy adres i port UDP na bieżąco (nie jest to typowe).

Wszystkie dane wysyłane za pośrednictwem DTLS będą szyfrowane przez stos Secure DTLS i skonfigurowane procedury szyfrowania przed wysłaniem.

### <a name="dtls-session-receive"></a>Odbieranie sesji DTLS

Po rozpoczęciu sesji DTLS aplikacja może zacząć odbierać dane przy użyciu usługi ***nx_secure_Dtls_session_receive** _. Podobnie jak w przypadku wysyłania sesji DTLS, ta usługa jest taka sama w użyciu do _ *_nx_udp_socket_receive_* *, z tą różnicą, że dane przychodzące są odszyfrowywane i weryfikowane przez stos DTLS przed zwróceniem w strukturze pakietów.

### <a name="tls-session-close"></a>Zamykanie sesji TLS

Po zakończeniu sesji DTLS zarówno klient, jak i serwer programu DTLS muszą wysłać Alert CloseNotify po drugiej stronie w celu zamknięcia sesji. Obie strony muszą odebrać i przetworzyć alert, aby upewnić się, że pomyślnie zamknięto sesję.

Jeśli host zdalny wyśle alert CloseNotify, wszystkie wywołania usługi ***nx_secure_dtls_session_receive** _ przetworzy alert, wyśle odpowiedni alert z powrotem do hosta zdalnego i zwróci wartość _ *_NX_SECURE_TLS_SESSION_CLOSED_* *. Po zamknięciu sesji wszelkie dalsze próby wysłania lub odebrania danych z tą sesją DTLS zakończą się niepowodzeniem.

Jeśli aplikacja chce zamknąć sesję TLS, należy wywołać usługę ***nx_secure_dtls_session_end** _. Usługa wyśle alert CloseNotify i przetworzy CloseNotify odpowiedzi. Jeśli odpowiedź nie zostanie odebrana, zostanie zwrócona wartość błędu _ *_NX_SECURE_TLS_SESSION_CLOSE_FAIL_**, co oznacza, że sesja DTLS nie została czysto ZAMKNIĘTA, możliwe naruszenie zabezpieczeń.

### <a name="tlsdtls-alerts"></a>Alerty TLS/DTLS

Protokół TLS/DTLS został zaprojektowany w celu zapewnienia maksymalnego poziomu zabezpieczeń, dlatego każde errant zachowanie w protokole jest uznawane za potencjalne naruszenie zabezpieczeń. Z tego powodu wszelkie błędy związane z przetwarzaniem komunikatów lub szyfrowaniem/odszyfrowywaniem są uznawane za błędy krytyczne, które natychmiast przerywają uzgadnianie lub sesję.

Podczas obsługi błędów w aplikacji lokalnej jest stosunkowo prosta, a host zdalny musi wiedzieć, że wystąpił błąd w celu prawidłowego obsłużenia tej sytuacji i zapobiegania wszelkim możliwym naruszeniom zabezpieczeń. Z tego powodu protokół TLS/DTLS wyśle komunikat o *alercie* do hosta zdalnego w przypadku jakiegokolwiek błędu.

Alerty są traktowane w taki sam sposób jak w przypadku innych komunikatów TLS/DTLS i są szyfrowane podczas sesji, co uniemożliwia osobie atakującej zbieranie informacji z typu dostarczonego alertu. W trakcie uzgadniania wysyłane alerty są ograniczone do zakresu, aby ograniczyć ilość informacji, które mogą zostać uzyskane przez potencjalną osobę atakującą.

Alert CloseNotify używany do zamykania sesji TLS/DTLS jest jedynym alertem niekrytycznym. Mimo że jest on traktowany jako alert i wysyłany jako komunikat alertu, CloseNotify jest w przeciwieństwie do innych alertów, w tym nie wskazuje, że wystąpił błąd.

### <a name="tlsdtls-session-renegotiation-and-resumption"></a>Ponowne negocjowanie i wznowienie sesji TLS/DTLS

Protokół TLS obsługuje pojęcie "renegocjacji", która jest po prostu ponowną negocjacją parametrów sesji TLS w kontekście istniejącej sesji TLS.

*Wznowienie* sesji protokołu TLS nie powinno być pomylone z ponowną *negocjacją* sesji pomimo pewnych podobieństw. Gdy ponowne *negocjowanie* sesji obejmuje rozpoczęcie nowego uzgadniania w istniejącej sesji protokołu TLS, *wznowienie* sesji jest funkcją opcjonalną, która polega na ponownym uruchomieniu zamkniętej sesji TLS bez wykonywania pełnej uzgadniania protokołu TLS.

Secure DTLS obsługuje przychodzące żądania renegocjacji z hostów zdalnych. **Nie obsługuje** wznawiania sesji. Dokładniejsze Omówienie tych funkcji można znaleźć w rozdziale 3 podręcznika użytkownika bezpiecznego protokołu TLS NetX.

### <a name="protocol-layering"></a>Warstwy protokołu

Protokół TLS (i w związku z tym DTLS również) mieści się w stosie sieci między warstwą transportu (np. TCP lub UDP) i warstwą aplikacji. Protokoły TLS są czasami uważane za protokół warstwy transportu (w związku z czym zabezpieczenia *warstwy transportowej* ), ale ponieważ działa jako aplikacja w odniesieniu do bazowych protokołów sieciowych, czasami pogrupowane w warstwę aplikacji.

Protokół TLS wymaga protokołu warstwy transportowej, który obsługuje dostarczanie w kolejności i bezstratne, takie jak TCP. Ze względu na to wymaganie protokół TLS nie może działać na podstawie protokołu UDP, ponieważ protokół UDP nie gwarantuje dostarczania datagramów. *DTLS* jest zmodyfikowaną wersją protokołu TLS, która jest używana dla aplikacji, które wymagają zabezpieczeń TLS za pośrednictwem protokołu datagramu, takiego jak UDP.

![Diagram warstw protokołu TLS.](media/image6.png)

**Rysunek 4 — warstwy protokołów TCP/IP, UDP i TLS/DTLS**

## <a name="network-communications-security-and-encryption"></a>Bezpieczeństwo i szyfrowanie komunikacji sieciowej

Zabezpieczanie komunikacji za pośrednictwem sieci publicznych oraz Internet jest ważnym tematem i tematem ogromnej liczby książek, artykułów i rozwiązań. Temat jest bogglingly złożony, ale może być zredukowany do prostego pomysłu: wysłanie informacji za pośrednictwem sieci, tak aby tylko przewidziany obiekt docelowy mógł uzyskać dostęp do tych informacji lub je zmienić. Ten podział na trzy ważne koncepcje: utajnienie, integralność i uwierzytelnianie. Protokół TLS/DTLS zapewnia rozwiązania dla wszystkich trzech.

Szyfrowanie jest używane na różne sposoby zapewniania tajemnicy, integralności i uwierzytelniania w ramach protokołów TLS i DTLS. Szyfrowanie musi być dostarczone do protokołu TLS lub DTLS podczas tworzenia sesji lub wystąpienia serwera, ponieważ protokół TLS zapewnia elastyczną platformę do korzystania z szyfrowania, a nie samego szyfrowania. NetX Secure DTLS zapewnia niezbędne procedury szyfrowania dla większości aplikacji, dzięki czemu nie trzeba mieć potrzeby znajdowania odpowiedniego szyfrowania.

Bardziej szczegółowy opis tych tematów można znaleźć w rozdziale 3 podręcznika użytkownika bezpiecznego protokołu TLS NetX.

## <a name="tls-and-dtls-extensions"></a>Rozszerzenia TLS i DTLS

Protokoły TLS (i w związku z tym DTLS) udostępniają wiele rozszerzeń zapewniających dodatkowe funkcje dla określonych aplikacji. Te rozszerzenia są zwykle wysyłane jako część komunikatów komunikacie ClientHello lub ServerHello, co oznacza, że host zdalny chce użyć rozszerzenia lub podać dodatkowe szczegóły do użycia podczas ustanawiania bezpiecznej sesji protokołu TLS.

NetX Secure DTLS obsługuje wszystkie rozszerzenia Znalezione w NetX Secure TLS, a pełny opis tych rozszerzeń można znaleźć w podręczniku użytkownika NetX Secure TLS, rozdział 3.

## <a name="authentication-methods"></a>Metody uwierzytelniania

Protokoły TLS i DTLS zapewniają strukturę służącą do ustanawiania bezpiecznego połączenia między dwoma urządzeniami za pośrednictwem niezabezpieczonej sieci, ale część problemu świadczy tożsamość urządzenia na drugim końcu tego połączenia. Bez mechanizmu uwierzytelniania tożsamości hostów zdalnych, jest to prosta operacja dla osoby atakującej, która będzie stanowić zaufane urządzenie.

Początkowo może się wydawać, że korzystanie z adresów IP, sprzętowych adresów MAC lub systemu DNS zapewni stosunkowo wysoki poziom zaufania do identyfikowania hostów w sieci, ale z uwzględnieniem rodzaju technologii TCP/IP i prostoty, z jakimi adresami mogą być sfałszowane i wpisy DNS są uszkodzone (np

Istnieją różne mechanizmy, które mogą zapewnić tę dodatkową warstwę uwierzytelniania dla protokołu TLS, ale najbardziej typowym *certyfikatem cyfrowym.* Inne mechanizmy obejmują klucze wstępne (PSK) i schematy haseł.

### <a name="digital-cerificates"></a>Digital instalowane

Certyfikaty cyfrowe są najczęściej spotykaną metodą uwierzytelniania hosta zdalnego w protokole TLS. Zasadniczo certyfikat cyfrowy to dokument z określonym formatowaniem, który zawiera informacje o tożsamości dla urządzenia w sieci komputerowej.

Protokół TLS zwykle korzysta z formatu o nazwie X. 509, który jest standardem opracowanym przez międzynarodowy związek telekomunikacyjny, ale inne formaty certyfikatów mogą być używane, Jeśli hosty TLS mogą wyrazić zgodę na używany format. X. 509 definiuje określony format certyfikatów i różnych kodowań, których można użyć do utworzenia dokumentu cyfrowego. Większość certyfikatów X. 509 używanych z protokołem TLS jest zakodowana przy użyciu wariantu numeru ASN 1, innego standardu telekomunikacyjnego. W ASN. 1 istnieje różne kodowanie cyfrowe, ale najpopularniejsze kodowanie certyfikatów TLS jest standardem Distinguished Encoding Rules (DER). DER to uproszczony podzbiór podstawowych reguł kodowania ASN. 1, które zostały zaprojektowane jako niejednoznaczne, co ułatwia analizowanie. W sieci, certyfikaty TLS są zwykle zakodowane w formacie binarnym DER i jest to format, który NetX bezpiecznego dla certyfikatów X. 509.

Certyfikaty binarne w formacie DER są używane w rzeczywistym protokole TLS, ale mogą być generowane i przechowywane w wielu różnych kodowaniach, z rozszerzeniami plików, takimi jak PEM, CRT i. p12. Różne warianty są używane przez różne aplikacje od różnych producentów, ale ogólnie wszystkie mogą być konwertowane na algorytm DER przy użyciu szeroko dostępnych narzędzi.

Najbardziej typowymi alternatywami kodowania certyfikatów jest PEM. Format PEM (z Privacy-Enhanced mail) jest zakodowaną w oparciu o wersję 64 kodowaniem algorytmu DER, która jest często używana, ponieważ kodowanie skutkuje tekstem drukowalnym, który można łatwo wysyłać przy użyciu poczty e-mail lub protokołów opartych na sieci Web.

Generowanie certyfikatu dla bezpiecznej aplikacji NetX jest zwykle poza zakresem tego podręcznika, ale narzędzie wiersza polecenia OpenSSL ([www.OpenSSL.org](http://www.openssl.org)) jest szeroko dostępne i może być konwertowane między większością formatów.

W zależności od aplikacji można generować własne certyfikaty, otrzymywać certyfikaty od producenta lub organizacji rządowej lub zakupić certyfikaty od komercyjnego urzędu certyfikacji.

Aby użyć certyfikatu cyfrowego w bezpiecznej aplikacji NetX, należy najpierw przekonwertować certyfikat na format binarny DER, a opcjonalnie przekonwertować skojarzony klucz prywatny ("wykładnik prywatny" dla RSA, na przykład) na format binarny, zazwyczaj w formacie PKCS # 1, który jest szyfrowany kluczem RSA. Po zakończeniu konwersji załadujesz certyfikat i klucz prywatny na urządzeniu. Możliwe opcje obejmują używanie systemu plików opartego na technologii Flash lub generowanie macierzy C na podstawie danych (za pomocą narzędzia takiego jak "XXD" w systemie Linux) i kompilowanie certyfikatu i klucza w aplikacji jako danych stałych.

Po załadowaniu certyfikatu na urządzenie można użyć interfejsu API DTLS w celu skojarzenia certyfikatu z sesją DTLS lub serwerem.

Aby uzyskać szczegółowe informacje i przykłady użycia certyfikatów X. 509 z NetX Secure DTLS, zobacz sekcję "Importowanie certyfikatów X. 509 do usługi NetX Secure" w podręczniku użytkownika NetX Secure TLS.

Aby uzyskać więcej informacji, zapoznaj się z następującymi usługami DTLS Services w dokumentacji interfejsu API:

- nx_secure_x509_certificate_initialize,
- nx_secure_dtls_session_local_certificate_add,
- nx_secure_dtls_server_local_certificate_add,
- nx_secure_dtls_session_local_certificate_remove,
- nx_secure_dtls_server_local_certificate_remove,
- nx_secure_dtls_session_trusted_certificate_add,
- nx_secure_dtls_server_trusted_certificate_add,
- nx_secure_dtls_session_trusted_certificate_remove
- nx_secure_dtls_server_trusted_certificate_remove

### <a name="tls-client-certificate-specifics"></a>Specyficzne dla certyfikatu klienta TLS

DTLS implementacje klientów zazwyczaj nie wymagają ładowania certyfikatu lokalnego na urządzeniu. Certyfikat lokalny to certyfikat, który identyfikuje urządzenie lokalne. W związku z tym certyfikat lokalny zawiera informacje o tożsamości dla urządzenia, na którym załadowana jest aplikacja TLS/DTLS. Wyjątkiem jest to, kiedy uwierzytelnianie certyfikatu klienta jest włączone, ale jest to mniej typowe.

Klient DTLS wymaga załadowania co najmniej jednego zaufanego certyfikatu (jeśli jest to wymagane) i miejsca na przydzielenie certyfikatu zdalnego. Zaufany certyfikat to certyfikat, który stanowi podstawę do zaufania i uwierzytelniania urządzenia zdalnego, bezpośrednio lub za pomocą infrastruktury kluczy publicznych (PKI). Katalog główny łańcucha zaufania jest zwykle nazywany urzędem certyfikacji lub certyfikatem urzędu certyfikacji. Certyfikat zdalny odwołuje się do certyfikatu wysyłanego przez hosta zdalnego podczas uzgadniania TLS. Zapewnia tożsamość dla tego hosta zdalnego i jest uwierzytelniany przez porównanie go z zaufanym certyfikatem na urządzeniu lokalnym.

Aby uzyskać więcej informacji na temat dodawania zaufanych certyfikatów i przydzielania miejsca dla certyfikatów zdalnych, zobacz Dokumentacja interfejsu API protokołu TLS dla następujących usług: nx_secure_dtls_session_create, nx_secure_dtls_session_trusted_certificate_add.

### <a name="tlsdtls-server-certificate-specifics"></a>Specyficzne dla certyfikatu serwera TLS/DTLS

Implementacje serwera DTLS zazwyczaj nie wymagają "zaufanych" certyfikatów do załadowania na urządzenie lub certyfikaty zdalne do przydzielenia. Wyjątek do tej sytuacji, gdy jest włączone uwierzytelnianie certyfikatu klienta.

Serwer TLS wymaga załadowania certyfikatu "Local" (lub "Identity"), aby serwer mógł udostępnić go klientowi zdalnemu podczas uzgadniania protokołu TLS w celu uwierzytelnienia serwera na komputerze klienckim.

Aby uzyskać więcej informacji na temat ładowania certyfikatów lokalnych do użycia z aplikacjami serwera NetX TLS, zobacz Dokumentacja interfejsu API dla następujących usług: nx_secure_dtls_server_local_certificate_add, nx_secure_dtls_server_local_certificate_remove.


### <a name="pre-shared-keys-psk"></a>Klucze wstępne (PSK)

Alternatywny mechanizm zapewnienia uwierzytelniania tożsamości w protokole TLS jest pojęciem kluczy wstępnych (PSK). Użycie ciphersuite PSK eliminuje konieczność wykonywania operacji szyfrowania klucza publicznego intensywnie korzystających z procesora, Boon dla urządzeń osadzonych z ograniczeniami zasobów. PSK zastępuje certyfikat w uzgadnianiu TLS/DTLS i jest używany zamiast szyfrowanego wstępnego klucza tajnego do generowania kluczy sesji TLS/DTLS.

Ciphersuites PSK jest ograniczony w tym sensie, że wspólny klucz tajny musi być obecny na obu urządzeniach przed ustanowieniem sesji TLS/DTLS. Oznacza to, że urządzenia muszą zostać załadowane za pomocą tego klucza tajnego, przy użyciu niebezpiecznych środków innych niż połączenie protokołu TLS z certyfikatem PSK — PSKs może zostać zaktualizowany za pośrednictwem połączenia z kluczem PSK protokołu TLS, ale urządzenie musi być uruchamiane z kluczem PSK, który jest ładowany przez inny mechanizm. Na przykład urządzenie czujnika i jego urządzenie bramy mogą zostać załadowane przy użyciu PSKs w fabryce przed wysyłką lub do załadowania klucza PSK przy użyciu standardowego połączenia TLS (z certyfikatem).

Ciphersuites PSK to kilka form, które opisano w dokumencie RFC 4279. W pierwszej kolejności są używane klucze RSA lub Diffie-Hellman, które są używane w taki sam sposób, jak klucze publiczne przesyłane w certyfikacie w standardowym uzgadnianiu protokołu TLS. Drugi formularz, który jest bardziej używany w środowisku z ograniczeniami zasobów, korzysta z klucza PSK, który jest używany do bezpośredniej generacji kluczy sesji (na przykład do użycia przez algorytm AES), unikając korzystania z kosztownych operacji RSA lub Diffie-Hellman.

NetX Secure obsługuje drugą formę klucza PSK ciphersuites, umożliwiając aplikacjom usuwanie wszystkich kodów kryptograficznych i użycie pamięci klucza publicznego. Sam klucz PSK nie jest kluczem AES, ale może być traktowany jak hasło, z którego są generowane rzeczywiste klucze. Istnieje kilka ograniczeń dotyczących tego, co może być wartością klucza PSK, ale dłuższe wartości zapewniają większe bezpieczeństwo (takie same jak w przypadku haseł).

Aby korzystać z klucza PSK w bezpiecznej aplikacji NetX, należy najpierw zdefiniować globalne makro **NX_SECURE_ENABLE_PSK_CIPHERSUITES**. Zwykle odbywa się to za pomocą ustawień kompilatora, ale definicja może być również umieszczona w pliku nagłówkowym nx_secure_tls. h. Po zdefiniowaniu makra obsługa klucza PSK ciphersuite zostanie skompilowana do aplikacji NetX Secure DTLS.

W przypadku włączenia obsługi PSK, można użyć interfejsu API DTLS, aby skonfigurować PSKs dla swojej aplikacji. Każdy PSK będzie wymagał wartości PSK (rzeczywisty klucz tajny) — Zapewnij bezpieczną wartość), wartość "Identity" służącą do identyfikowania określonego klucza PSK oraz "wskazówkę tożsamości", która jest używana przez serwer TLS do wybierania określonej wartości klucza PSK.

Sam PSK może być dowolną wartością binarną, ponieważ nigdy nie jest wysyłana za pośrednictwem połączenia sieciowego. Wartość PSK może być dowolną wartością o długości do 64 bajtów.

Tożsamość i Wskazówka muszą być drukowalne ciągi znaków sformatowane przy użyciu kodowania UTF-8. Wartości Identity i Hint mogą mieć długość do 128 bajtów.

Tożsamość i PSK tworzą unikatową parę, która jest ładowana na każde urządzenie w sieci, które musi komunikować się ze sobą.

"Wskazówka" jest używana głównie do definiowania profilów aplikacji w celu grupowania PSKs przez funkcję lub usługę. Te wartości muszą być uzgadniane z wyprzedzeniem i są zależne od aplikacji. Przykładowo aplikacja serwera wiersza polecenia OpenSSL (z włączonym PSK) używa domyślnego ciągu "Client_identity", który musi być dostarczony przez klienta TLS w celu kontynuowania uzgadniania TLS.

Aby uzyskać więcej informacji na temat PSKs, zobacz Dokumentacja bezpiecznego interfejsu API NetX dla następujących usług: nx_secure_dtls_psk_add, nx_secure_dtls_server_psk_add.

## <a name="importing-x509-certificates-into-netx-secure"></a>Importowanie certyfikatów X. 509 do NetX Secure

Certyfikaty cyfrowe są wymagane dla większości połączeń TLS w Internecie. Certyfikaty zapewniają metodę uwierzytelniania wcześniej nieznanych hostów za pośrednictwem Internetu przy użyciu zaufanych wystawców, *zwykle nazywanych urzędami certyfikacji lub* urzędami certyfikacji. Aby połączyć NetX bezpieczne urządzenie z usługą w chmurze komercyjnej (taką jak Amazon Web Services), należy zaimportować certyfikaty do aplikacji, ładując je na urządzenie.

Wraz z certyfikatami czasami potrzebny jest również *klucz prywatny* skojarzony z certyfikatem. W niektórych aplikacjach (takich jak klient protokołu TLS, gdy uwierzytelnianie certyfikatu klienta nie jest używane) certyfikat będzie wystarczający, ale jeśli certyfikat jest używany do identyfikowania urządzenia, potrzebny będzie klucz prywatny. Klucze prywatne są zwykle generowane podczas tworzenia certyfikatu i są przechowywane w osobnym pliku, często szyfrowane przy użyciu hasła.

Szczegółowy opis importowania certyfikatów do bezpiecznych aplikacji NetX można znaleźć w rozdziale 3 w podręczniku użytkownika NetX Secure TLS.

## <a name="client-certificate-authentication-in-netx-secure-tls"></a>Uwierzytelnianie certyfikatu klienta w protokole Secure TLS NetX

W przypadku korzystania z uwierzytelniania certyfikatu X. 509 protokół TLS/DTLS wymaga, aby wystąpienie serwera DTLS dostarczać certyfikat do identyfikacji, ale domyślnie wystąpienie klienta DTLS nie musi podawać certyfikatu do uwierzytelnienia przy użyciu innej formy uwierzytelniania (np. kombinacji nazwy użytkownika/hasła). Jest to zgodne z najbardziej typowym wykorzystaniem protokołu TLS w Internecie dla witryn sieci Web. Na przykład witryna handlu detalicznego w trybie online musi udowodnić potencjalnemu klientowi korzystanie z przeglądarki sieci Web, że serwer jest wiarygodny, ale użytkownik użyje nazwy logowania/hasła w celu uzyskania dostępu do określonego konta.

Jednak domyślny przypadek nie zawsze jest pożądany, więc protokół TLS/DTLS opcjonalnie zezwala na wystąpienie serwera DTLS o zażądanie certyfikatu od klienta zdalnego. Po włączeniu tej funkcji serwer DTLS wyśle do klienta DTLS komunikat CertificateRequest podczas uzgadniania. Klient musi odpowiedzieć własnym certyfikatem, a komunikat CertificateVerify zawierający token kryptograficzny wskazujący, że klient jest właścicielem zgodnego klucza prywatnego skojarzonego z tym certyfikatem. Jeśli weryfikacja nie powiedzie się lub certyfikat nie jest połączony z zaufanym certyfikatem na serwerze, uzgadnianie TLS nie powiedzie się.

Istnieją dwa oddzielne przypadki uwierzytelniania certyfikatu klienta w protokole TLS — w poniższych sekcjach omówiono oba przypadki.

### <a name="client-certificate-authentication-for-dtls-clients"></a>Uwierzytelnianie certyfikatu klienta dla klientów DTLS

Klient DTLS może próbować nawiązać połączenie z serwerem, który żąda certyfikatu do uwierzytelnienia klienta. W takim przypadku klient musi dostarczyć certyfikat do serwera i upewnić się, że jest właścicielem zgodnego klucza prywatnego lub serwer zakończy uzgadnianie DTLS.

W NetX Secure DTLS nie ma specjalnej konfiguracji do obsługi tej funkcji, ale aplikacja będzie musiała podać lokalny certyfikat identyfikacyjny dla wystąpienia klienta TLS przy użyciu usługi *nx_secure_tls_session_local_certificate_add* . Jeśli aplikacja nie udostępnia żadnego certyfikatu, ale serwer zdalny używa uwierzytelniania certyfikatu klienta i żąda certyfikatu, uzgadnianie DTLS zakończy się niepowodzeniem. Aby można było wykonać uzgadnianie DTLS, certyfikat dostarczony do sesji DTLS z *nx_secure_dtls_session_local_certificate_add* musi być rozpoznawany przez serwer zdalny.

### <a name="client-certificate-authentication-for-tls-servers"></a>Uwierzytelnianie certyfikatu klienta dla serwerów TLS

Przypadek serwera DTLS dla uwierzytelniania certyfikatu klienta jest nieco bardziej skomplikowany niż przypadek klienta DTLS ze względu na opcjonalną funkcję. W takim przypadku serwer TLS musi jawnie zażądać certyfikatu ze zdalnego klienta TLS, a następnie przetworzyć komunikat CertificateVerify, aby sprawdzić, czy Klient zdalny jest właścicielem pasującego klucza prywatnego, a następnie serwer musi sprawdzić, czy certyfikat dostarczony przez klienta może być śledzony do certyfikatu w lokalnym magazynie zaufanych certyfikatów.

W przypadku wystąpień serwera Secure TLS NetX uwierzytelnianie certyfikatu klienta jest kontrolowane przez *nx_secure_dtls_server_x509_client_verify_configure* i *nx_secure_dtls_server_x509_client_verify_disable* usług.

Aby włączyć uwierzytelnianie certyfikatu klienta, aplikacja musi wywoływać *nx_secure_dtls_server_x509_client_verify_configure* z wystąpieniem sesji serwera DTLS przed wywołaniem *nx_secure_dtls_server_start*. Weryfikacja wymaga przydzielenia miejsca na przychodzące certyfikaty klienta podane jako parametr do *nx_secure_dtls_server_x509_client_verify_configure.* Należy pamiętać, że bufor musi być wystarczająco duży, aby pomieścić maksymalny rozmiar łańcucha certyfikatów dostarczony przez klienta *pomnożonego przez liczbę sesji serwera DTLS*. Każda sesja serwera wymaga miejsca, które zostanie przydzielony z pojedynczego dostarczonego buforu. Upewnij się, że bufor jest wystarczająco duży lub wystąpi błąd, jeśli podany łańcuch certyfikatów klienta jest zbyt duży.

Po włączeniu uwierzytelniania certyfikatu klienta serwer DTLS żąda certyfikatu z klienta zdalnego DTLS podczas uzgadniania DTLS. W programie NetX Secure DTLS Server certyfikat klienta jest sprawdzany pod kątem magazynu zaufanych certyfikatów utworzonych przy użyciu *nx_secure_dtls_server_trusted_certificate_add* przez następujący łańcuch wystawcy X. 509. Klient zdalny musi dostarczyć łańcuch, który łączy jego certyfikat tożsamości z certyfikatem w zaufanym magazynie lub uzgadnianie DTLS zakończy się niepowodzeniem. Ponadto jeśli przetwarzanie komunikatu CertificateVerify nie powiedzie się, uzgadnianie DTLS również zakończy się niepowodzeniem.

Metody podpisu używane dla metody CertificateVerify są ustalone dla protokołów TLS w wersji 1,0 i TLS w wersji 1,1 i są określone przez serwer TLS w wersji TLS 1,2, na podstawie którego jest oparty NetX Secure DTLS. W przypadku DTLS 1,2 metody podpisywania są ogólnie zgodne z odpowiednimi metodami podanymi w tabeli metod kryptograficznych, ale zazwyczaj RSA z algorytmem SHA-256 (patrz sekcja "Kryptografia w NetX Secure TLS"), aby uzyskać więcej informacji na temat inicjowania protokołu TLS przy użyciu metod kryptograficznych).

## <a name="cryptography-in-netx-secure-tls"></a>Kryptografia w protokole Secure TLS NetX

TLS definiuje protokół, w którym Kryptografia może być używana do zabezpieczania komunikacji sieciowej. W związku z tym pozostawi rzeczywiste kryptografie do użycia w postaci otwartej dla użytkowników protokołu TLS. Specyfikacja wymaga tylko jednego ciphersuite do zaimplementowania — w przypadku protokołu TLS 1,2, że ciphersuite jest TLS_RSA_WITH_AES_128_CBC_SHA, wskazując użycie RSA dla operacji klucza publicznego, AES w trybie CBC z 128-bitowymi kluczami dla szyfrowania sesji i algorytmem SHA-1 dla skrótów uwierzytelniania komunikatów.

Jest zgodny z protokołem TLS 1,2, NetX Secure domyślnie włącza obowiązkowy TLS_RSA_WITH_AES_128_CBC_SHA ciphersuite, ale biorąc pod uwagę liczbę możliwych implementacji dla każdej z metod kryptograficznych ze względu na możliwości sprzętowe i inne zagadnienia, NetX Secure zapewnia ogólny interfejs API kryptografii, który umożliwia użytkownikowi określenie metod kryptograficznych, które mają być używane z protokołem TLS.

> [!NOTE]
> Mechanizm ogólnego interfejsu API kryptografii umożliwia również użytkownikom zaimplementowanie własnych ciphersuites, ale jest to zalecane dla zaawansowanych użytkowników, którzy znają ciphersuites TLS i rozszerzenia. Skontaktuj się z przedstawicielem programu Express Logic, Jeśli interesuje Cię obsługę własnych ciphersuites.

Zapoznaj się ze szczegółowymi informacjami na temat sposobu konfigurowania metod kryptograficznych dla usługi DTLS, w rozdziale 3 podręcznika użytkownika NetX Secure TLS. Ten sam proces dotyczy protokołów TLS i DTLS.
