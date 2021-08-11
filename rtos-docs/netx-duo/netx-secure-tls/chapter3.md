---
title: Rozdział 3 — Opis funkcjonalny Azure RTOS NetX Secure
description: Ten rozdział zawiera opis funkcjonalny bezpiecznego TLS netx.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 711195e60771ebd467c69df49ef7665f32e13a17c21ca839404e829449cf1401
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797981"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-secure"></a>Rozdział 3 — Opis funkcjonalny Azure RTOS NetX Secure

## <a name="execution-overview"></a>Omówienie wykonywania

Ten rozdział zawiera opis funkcjonalny Azure RTOS NetX Secure TLS. Istnieją dwa podstawowe typy wykonywania programu w aplikacji NetX Secure TLS: inicjowanie i wywołania interfejsu aplikacji. 

*NetX Secure zakłada istnienie ThreadX i NetX/NetXDuo. W przypadku threadX wymaga wykonania wątku, zawieszenia, okresowych czasomierzy i obiektów wzajemnego wykluczania. Z NetX/NetXDuo wymaga infrastruktury sieci TCP/IP i sterowników.*

## <a name="transport-layer-security-tls-and-secure-sockets-layer-ssl"></a>Transport Layer Security (TLS) i Secure Sockets Layer (SSL)

Składnik protokołu sieci bezpiecznego NetX Secure to implementacja protokołu Transport Layer Security (TLS) zgodnie z opisem w RFC 2246 (wersja 1.0), 4346 (wersja 1.1), 5246 (wersja 1.2) i 8446 (wersja 1.3). Dostępne są również procedury pomocy technicznej dla podstawowego zestawu X.509 (RFC 5280).

NetX Secure TLS obsługuje zabezpieczenia TLS w wersjach 1.2 i 1.3. Implementacje są dostępne dla przestarzałych już TLS 1.0 i TLS 1.1, ale muszą być jawnie zainicjowane i nie są zalecane do użycia w nowych produktach.

*Secure Sockets Layer* (SSL) była oryginalną nazwą protokołu TLS, zanim stała się standardem w dokumencie RFC 2246, a "SSL" jest często używana jako nazwa ogólna protokołów TLS. Ostatnia wersja protokołu SSL to 3.0, a protokół TLS 1.0 jest czasami nazywany protokołem SSL w wersji 3.1. Wszystkie wersje oficjalnego protokołu "SSL" są uznawane za przestarzałe i niezabezpieczone, a obecnie netX Secure nie zapewnia implementacji protokołu SSL.

Protokół TLS określa  protokół do generowania kluczy sesji, które są tworzone podczas uściślania protokołu *TLS* między klientem a serwerem TLS, a te klucze są używane do szyfrowania danych wysyłanych przez aplikację podczas sesji protokołu *TLS.*

Dane protokołu TLS są podzielone na *rekordy,* które są w koncepcji równoważne pakietowi TCP. Każdy rekord TLS ma nagłówek, a zaszyfrowane rekordy TLS mają również stopkę (skrót sumy kontrolnej). Rekordy uściśleń TLS mają dodatkowy nagłówek hermetyzowany w większym rekordzie TLS. Rekord TLS jest hermetyzowany przez protokół sieciowy warstwy transportu w taki sam sposób, jak pakiet TCP jest hermetyzowany przez pakiet IP.

### <a name="tls-13"></a>TLS 1.3

W sierpniu 2018 r. została sfinalizowana specyfikacja TLS 1.3. Nowa wersja protokołu to dość znacząca aktualizacja, która zmienia niektóre podstawowe aspekty podstawowych zabezpieczeń i wydajności protokołu TLS. Jednak te zmiany są w dużym stopniu niewidoczne dla typowego użytkownika TLS, ponieważ dotyczą głównie maszyny stanu uściślniania TLS i generowania klucza sesji. Dodano również kilka opcjonalnych funkcji i rozszerzeń. Poniżej przedstawiono podsumowanie zmian i ich wpływu na funkcjonalność TLS.

- Maszyna stanu uściślinia została zoptymalizowana przez usunięcie całej wymiany komunikatów przez serwer.
- Zaktualizowano generowanie klucza w celu użycia standardowej procedury o nazwie HKDF (funkcja pochodna klucza HMAC) i powiązywano klucze sesji ze wszystkimi komunikatami uściślniania (zamiast kilku wybranych parametrów).
- Wszystkie szyfry TLS 1.2 i starsze są przestarzałe i są niezgodne z TLS 1.3. Podobnie wszystkie szyfry TLS 1.3 nie mogą być używane w poprzednich wersjach.
- Wszystkie szyfry TLS 1.3 zapewniają doskonałe utajnienie przekazywania (PFS) przy użyciu kluczy efemeralnych<sup>6</sup> 
- TLS 1.3 usuwa "kod uwierzytelniania komunikatów" (MAC) z każdego rekordu na rzecz używania szyfrów AEAD<sup>7</sup>
- Dodano niektóre dodatkowe funkcje opcjonalne, w tym 0-RTT (zero round trip time), które umożliwiają wysyłanych danych aplikacji podczas procesu handshake. 0-RTT jest wyłącznie opcjonalne i nie jest obecnie obsługiwane w Azure RTOS TLS.

TLS 1.3 nie ma istotnego wpływu na aplikacje użytkowników. Interfejs API pozostaje dokładnie taki sam między wersjami, a szyfry są oznaczane, aby można było użyć jednej tabeli szyfrów.

Aby można było używać TLS 1.3, NX_SECURE_TLS_ENABLE_TLS_1_3 musi być globalnie zdefiniowana. TLS 1.3 jest domyślnie wyłączony w Azure RTOS TLS.

6. Klucze "efemeryjne" to asymetryczne pary kluczy, które są generowane podczas ugody TLS i używane do wymiany wpisów tajnych tylko dla tej sesji. Pary kluczy są odrzucane po użyciu — uniemożliwia to osobie atakującej uzyskanie dostępu do zaszyfrowanych danych w zarejestrowanej sesji TLS, nawet jeśli klucz prywatny certyfikatu zostanie naruszony w dowolnym momencie w przyszłości — dlatego jest to "doskonałe tajemnice przekazywania".

7. Uwierzytelnione szyfrowanie za pomocą skojarzonych danych — tryb szyfrowania, taki jak AES, który łączy szyfrowanie i sprawdzanie integralności w ramach jednej operacji, eliminując konieczność oddzielnego skrótu danych na potrzeby sprawdzania integralności.

### <a name="tls-record-header"></a>Nagłówek rekordu TLS

Każdy prawidłowy rekord TLS musi mieć nagłówek TLS, jak pokazano w sekcji Błąd! Nie znaleziono źródła odwołania.

![Diagram nagłówka rekordu TLS.](media/image2.png)

Rysunek 1. Nagłówek rekordu TLS

Pola nagłówka rekordu TLS są zdefiniowane w następujący sposób:

| Pole nagłówka TLS | Przeznaczenie     |
| ---------------- | ------------- |
| **8-bitowy typ komunikatu** | To pole zawiera typ wysyłanego rekordu TLS. Prawidłowe typy są następujące:<br />- ChangeCipherSpec<sup>8</sup>: 0x14<br />- Alert: 0x15<br />- Uściślij: 0x16<br />— Dane aplikacji: 0x17 |
| **Wersja protokołu 16-bitowego** | To pole zawiera wersję protokołu TLS. Prawidłowe wartości są następujące:<br />- SSL 3.0: 0x0300<br />- TLS 1.0: 0x0301<br />- TLS 1.1: 0x0302<br />- TLS 1.2: 0x0303<br />- **TLS 1.3 <sup>9:</sup>** **0x0303** |
| **Długość 16-bitowa** | To pole zawiera długość danych hermetyzowanych w rekordzie TLS. |

8. W przypadku usługi TLS 1.3 komunikat ChangeCipherSpec nie jest już używany, chociaż nadal może być wysyłany ze względu na zgodność, w którym to przypadku komunikat jest ignorowany.

9. Protokół TLS 1.3 będzie technicznie miał wartość 0x0304, jeśli ten schemat był kontynuowany, ale protokół został zmieniony na rzeczywistą wersję protokołu w rozszerzeniu, więc wszystkie rekordy TLS 1.3 używają protokołu 0x0303 w polach wersji protokołu w celu zapewnienia zgodności z poprzednimi wersjami.

### <a name="tls-handshake-record-header"></a>Nagłówek rekordu uściślniania TLS

Każdy prawidłowy rekord uściślniania TLS musi mieć nagłówek handshake TLS, jak pokazano na rysunku 2.

![Diagram nagłówka rekordu uściślniania TLS.](media/image3.png)

Rysunek 2. Nagłówek rekordu uściślniania TLS

Pola nagłówka rekordu uściślniania TLS są zdefiniowane w następujący sposób:

| Pole nagłówka TLS | Przeznaczenie |
| ---------------- |----------------------- |
| **8-bitowy typ komunikatu** | To pole zawiera typ wysyłanego rekordu TLS. Prawidłowe typy są następujące:<br />- ChangeCipherSpec<sup>10</sup>: 0x14<br />- Alert: 0x15<br />- Uściślij: 0x16<br />— Dane aplikacji: 0x17 |
| **Wersja protokołu 16-bitowego** | To pole zawiera wersję protokołu TLS. Prawidłowe wartości są następujące:<br />- SSL 3.0: 0x0300<br />- TLS 1.0: 0x0301<br />- TLS 1.1: 0x0302<br />- TLS 1.2: 0x0303<br />- **TLS 1.3 <sup>11:</sup>** **0x0303** |
| **Długość 16-bitowa**    | To pole zawiera długość danych hermetyzowanych w rekordzie TLS. |
| **8-bitowy typ ugody** | To pole zawiera typ komunikatu praktycznego. Prawidłowe wartości są następujące (*komunikaty pogrubione **zostały** dodane w TLS 1.3):<br />- HelloRequest: 0x00<br />- ClientHello: 0x01<br />- ServerHello: 0x02<br />- **HelloVerifyRequest:** **0x03**<br />- **NewSessionTicket:** **0x04**<br />- **EndOfEarlyData**: **0x05**<br />- **EncryptedExtensions:** **0x08**<br />- Certyfikat: 0x0B<br />- ServerKeyExchange: 0x0C<br />- CertificateRequest: 0x0D<br />- ServerHelloDone: 0x0E<br />- CertificateVerify: 0x0F<br />- ClientKeyExchange: 0x10<br />— Zakończono: 0x14<br />- **KeyUpdate**: **0x18**<br />- **MessageHash:** **0xFE** |
| **Długość 24-bitowa**    | To pole zawiera długość danych komunikatu praktycznego. |

10. W przypadku usługi TLS 1.3 komunikat ChangeCipherSpec nie jest już używany, chociaż nadal może być wysyłany ze względu na zgodność, w którym to przypadku komunikat jest ignorowany.

11. Protokół TLS 1.3 będzie technicznie miał wartość 0x0304, jeśli ten schemat był kontynuowany, ale protokół został zmieniony na rzeczywistą wersję protokołu w rozszerzeniu, więc wszystkie rekordy TLS 1.3 używają protokołu 0x0303 w polach wersji protokołu w celu zapewnienia zgodności z poprzednimi wersjami.

### <a name="the-tls-handshake-and-tls-session"></a>Sesja TLS Handshake i TLS

Typowy uściślnianie TLS (wersje 1.0–1.2) przedstawiono na rysunku 3. A TLS handshake begins when the TLS Client sends a ClientHello message to a TLS server, indicating its desire to start a TLS session (Klient TLS wysyła do serwera TLS komunikat *ClientHello* wskazujący chęć uruchomienia sesji TLS). Komunikat zawiera informacje o szyfrowaniu, które klient chce użyć dla sesji, wraz z informacjami używanymi do generowania kluczy sesji w dalszej części procesu ugody. Dopóki klucze sesji nie zostaną wygenerowane, wszystkie komunikaty w uściślnie TLS nie będą szyfrowane. TLS 1.3 nieco zmienia ugodę — szczegóły przedstawiono w następnej sekcji.

Serwer TLS odpowiada na komunikat ClientHello komunikatem ServerHello wskazującym wybór opcji szyfrowania dostarczonych przez klienta. Po serverHello następuje komunikat Certyfikat, w którym serwer udostępnia certyfikat cyfrowy w celu uwierzytelnienia swojej tożsamości na kliencie. Na koniec serwer wysyła komunikat ServerHelloDone, aby wskazać, że nie ma więcej komunikatów do wysłania. Serwer może opcjonalnie wysyłać inne komunikaty następujące po ServerHello i w niektórych przypadkach może nie wysłać komunikat certyfikatu, dlatego potrzeba serverHelloDone komunikat.

Po otrzymaniu wszystkich komunikatów serwera klient ma wystarczająco dużo informacji, aby wygenerować klucze sesji. W tym celu TLS tworzy udostępniony bit danych losowych o nazwie *Pre-Master Secret*, który ma stały rozmiar i jest używany jako iniekt do generowania wszystkich kluczy potrzebnych po włączeniu szyfrowania. Klucz tajny wstępny jest szyfrowany przy użyciu algorytmu klucza publicznego (np. RSA) określonego w komunikatach Hello (zobacz poniżej, aby uzyskać informacje na temat algorytmów kluczy publicznych) i klucza publicznego dostarczonego przez serwer w certyfikacie. Opcjonalna funkcja TLS o nazwie Klucze wstępne (PSK, Pre-Shared Keys) umożliwia stosowanie szyfrów, które nie używają certyfikatu, ale zamiast tego używają wartości tajnej współdzielonych między hostami (zazwyczaj za pośrednictwem transferu fizycznego lub innej zabezpieczonej metody). Wspólny klucz tajny jest używany do generowania wstępnego głównego tajnego zamiast używania zaszyfrowanego komunikatu do wysyłania wstępnego tajnego. Zobacz sekcję klucze wstępne poniżej.

Zaszyfrowany klucz tajny wstępny jest wysyłany do serwera w komunikacie ClientKeyExchange. Serwer po otrzymaniu komunikatu ClientKeyExchange odszyfrowuje klucz tajny przedwłaszowy przy użyciu klucza prywatnego i kontynuuje generowanie kluczy sesji równolegle z klientem protokołu TLS.

Po wygenerowaniu kluczy sesji wszystkie dalsze komunikaty mogą być szyfrowane przy użyciu algorytmu klucza prywatnego (np. AES) wybranego w komunikatach Hello. Klient i serwer wysyła ostatni niezaszyfrowany komunikat o nazwie ChangeCipherSpec, aby wskazać, że wszystkie dalsze komunikaty będą szyfrowane.

Pierwszy zaszyfrowany komunikat wysyłany przez klienta i serwer jest również ostatnim komunikatem uściślniania TLS o nazwie Finished (Zakończono). Ten komunikat zawiera skrót wszystkich odebranych i wysłanych komunikatów z ugodą. Ten skrót służy do sprawdzania, czy żaden z komunikatów w uściśliniu nie został naruszony ani uszkodzony (co wskazuje na możliwe naruszenie zabezpieczeń).

Po odebraniu komunikatów Finished (Zakończono) i zweryfikowaniu skrótów uściśleń rozpoczyna się sesja TLS, a aplikacja rozpoczyna wysyłanie i odbieranie danych. Wszystkie dane wysyłane po obu stronach podczas sesji TLS są najpierw szyfrowane przy użyciu algorytmu wyznaczania wartości skrótu wybranego w komunikatach Hello (w celu zapewnienia integralności komunikatów) i szyfrowane przy użyciu wybranego algorytmu klucza prywatnego z wygenerowanym kluczem sesji.

Sesję TLS można zakończyć pomyślnie tylko wtedy, gdy klient lub serwer wybierze tę opcję. Obcinana sesja jest uznawana za naruszenie zabezpieczeń (ponieważ osoba atakująca może próbować zapobiec odbierania wszystkich wysyłanych danych), więc gdy którakolwiek ze stron chce zakończyć sesję, wysyłane jest specjalne powiadomienie, nazywane alertem CloseNotify. Zarówno klient, jak i serwer muszą wysłać i przetworzyć alert CloseNotify w celu pomyślnego zamknięcia sesji.

![Diagram typowego uściślniania TLS.](media/image4.png)

Rysunek 3. Typowe uściślnienie TLS

### <a name="tls-13-handshake"></a>TLS 1.3 Handshake

Protokół TLS 1.3 to dość duża modernizacja protokołu TLS. Ogromna większość zmian w uściśliwce w celu zwiększenia bezpieczeństwa i wydajności. Typowy uściślnianie TLS 1.3 przedstawiono na rysunku 4. Główną różnicę można zobaczyć w liczbie wymian między serwerem a klientem.

W wersji TLS 1.2 i starszych serwer wyśle dwa loty<sup>12</sup> komunikatów — najpierw serverHello, a następnie komunikat ChangeCipherSpec przed wysłaniem zaszyfrowanego komunikatu Finished (Zakończono), który kończy ugodę. W przypadku usługi TLS 1.3 serwer wysyła wszystko podczas pierwszego lotu — ServerHello, rozszerzenia, certyfikat i zakończone. Komunikat ChangeCipherSpec został wyeliminowany, a serwer generuje klucze sesji i rozpoczyna szyfrowanie komunikatów uściślających bezpośrednio po serwerzeHello.

Nowe rozwiązanie oznacza, że większa część procesu ugody TLS jest chroniona przez szyfrowanie, ograniczając ilość danych w postaci zwykłego tekstu, do których osoba atakująca może uzyskać dostęp. Ponadto usunięcie drugiego lotu serwera (który był tylko elementem ChangeCipherSpec, po którym następuje komunikat Finished) oznacza, że klient TLS nie musi już czekać na rozpoczęcie przesyłania danych aplikacji — gdy tylko klient wyśle własny komunikat Zakończono, sesja została uruchomiona.

12. Lot to po prostu kolekcja komunikatów TLS wysyłanych jednocześnie w grupie.

![Diagram uściślniania TLS 1.3.](media/image5.png)

Rysunek 4. TLS 1.3 Handshake

> [!NOTE]
> *W tLS 1.3 wprowadzono również pojęcia "Wczesne dane" i 0-RTT (zero round trip time), co oznacza, że niektóre dane aplikacji mogą być wysyłane w pierwszym locie komunikatów. Ta opcjonalna funkcja została dodana głównie jako optymalizacja pod kątem czasu odpowiedzi przeglądarki internetowej (np. w celu wysyłania wczesnych nagłówków HTTP w celu rozpoczęcia renderowania strony). Od Azure RTOS 6.0 ta funkcja NIE jest obsługiwana.*

### <a name="initialization"></a>Inicjalizacja

Stos TCP/IP NetX lub NetXDuo musi zostać zainicjowany przed użyciem protokołu NetX Secure TLS. Zapoznaj się z podręcznikiem użytkownika netx lub NetXDuo, aby uzyskać informacje na temat prawidłowego inicjowania stosu TCP/IP.

Po zainicjowania stosu TCP/IP NetX można włączyć protokół TLS. Wewnętrznie cały ruch sieciowy I przetwarzanie TLS jest obsługiwany przez stos NetX/NetXDuo bez interwencji użytkownika. Jednak tLS ma pewne określone wymagania, które muszą być obsługiwane oddzielnie od podstawowego stosu sieciowego. Te parametry są przypisywane do bloku sterowania TLS o nazwie ***NX_SECURE_TLS_SESSION** _ przy użyciu usługi _ *_nx_secure_tls_session_create_**.

TLS ma dwa tryby: Serwer i Klient, z których każdy może być włączony w aplikacji (ale tylko jeden tryb na gniazdo NetX) i każdy z nich ma własne specyficzne wymagania, szczegółowo opisane poniżej.

W obu trybach protokół NetX Secure TLS wymaga utworzenia i skonfigurowania gniazda TCP (***NX_TCP_SOCKET** _) do komunikacji TCP z hostem zdalnym. Gniazdo TCP jest przypisywane do wystąpienia sesji protokołu TLS za pomocą usługi _ *_nx_secure_tls_session_start_** opisanej poniżej.

### <a name="initialization--tls-server"></a>Inicjowanie — serwer TLS

Oprócz gniazda TCP tryb NetX Secure TLS Server wymaga certyfikatu *cyfrowego,* który jest dokumentem używanym do identyfikowania serwera TLS z łączącym się klientem protokołu TLS, oraz certyfikatów odpowiadających mu klucza prywatnego *,* zazwyczaj dla algorytmu szyfrowania RSA. Standard X.509 International Telecommunications Union określa format certyfikatu używany przez TLS i istnieje wiele narzędzi do tworzenia certyfikatów cyfrowych X.509.

W przypadku netX Secure TLS certyfikat X.509 musi być zakodowany binarnie przy użyciu formatu Distinguished Encoding Rules (DER) ASN.1. DER to standardowy format binarny TLS over-the-wire dla certyfikatów.

Klucz prywatny skojarzony z dostarczonym certyfikatem musi być w formacie DER-Encoded PKCS#1. Klucz prywatny jest używany tylko na urządzeniu i nigdy nie będzie przesyłany za pośrednictwem sieci. Dbaj o bezpieczeństwo kluczy prywatnych, ponieważ zapewniają one bezpieczeństwo komunikacji TLS.

Aby zainicjować certyfikat serwera TLS, aplikacja musi dostarczyć wskaźnik do buforu zawierającego certyfikat X.509 zakodowany w formacie DER i opcjonalne dane klucza prywatnego PKCS#1 RSA zakodowane w formacie DER przy użyciu usługi ***nx_secure_x509_certificate_intialize** _, która wypełnia strukturę _ *NX_SECURE_X509_CERT** odpowiednimi danymi certyfikatu do użycia przez TLS.

Po zainicjowania certyfikatu serwera należy go dodać do bloku sterowania TLS przy użyciu ***nx_secure_tls_local_certificate_add*** usługi.

Po dodaniu certyfikatu serwera do bloku sterowania TLS można użyć gniazda do nawiązania bezpiecznego połączenia z serwerem TLS.

### <a name="initialization--tls-client"></a>Inicjowanie — klient TLS

Tryb klienta NetX Secure TLS wymaga zaufanego magazynu certyfikatów *,* który jest kolekcją certyfikatów cyfrowych zakodowanych w formacie X.509 z zaufanych urzędów certyfikacji. Protokół TLS zakłada, że te certyfikaty są "zaufane" i służą jako podstawa uwierzytelniania certyfikatów dostarczonych przez jednostki serwera TLS do klienta NetX Secure TLS.

Certyfikat zaufanego urzędu  certyfikacji może być z podpisem własnym lub podpisany przez inny urząd certyfikacji. W takim przypadku ten certyfikat jest nazywany pośrednim urzędu *certyfikacji* (ICA). W typowej aplikacji protokołu TLS serwer udostępnia certyfikaty ICA wraz z certyfikatem serwera, ale jedynym wymaganiem pomyślnego uwierzytelniania jest możliwość śledzenia łańcucha wystawców (certyfikatów używanych do podpisywania innych certyfikatów) z certyfikatu serwera z powrotem do certyfikatu zaufanego urzędu certyfikacji w magazynie zaufanych certyfikatów. Ten łańcuch jest nazywany *łańcuchem zaufania lub* *łańcuchem certyfikatów.*

Aby zainicjować zaufany urząd certyfikacji lub certyfikat ICA, aplikacja musi dostarczyć wskaźnik do buforu zawierającego certyfikat X.509 zakodowany w formacie DER przy użyciu usługi ***nx_secure_x509_certificate_intialize** _, która wypełnia strukturę _ *NX_SECURE_X509_CERT** odpowiednimi danymi certyfikatów do użycia przez TLS.

Zaufane certyfikaty, które zostały zainicjowane, są następnie dodawane do bloku sterowania TLS przy użyciu ***nx_secure_tls_trusted_certificate_add*** usługi. Nie można dodać certyfikatu spowoduje, że sesja klienta TLS nie powiedzie się, ponieważ protokół TLS nie będzie w stanie uwierzytelnić zdalnych hostów serwera TLS.

Klient TLS musi również mieć miejsce na przydzielenie przychodzącego certyfikatu serwera (przy założeniu, że tryb klucza wstępnego nie jest używany). Od programu NetX Secure TLS 5.12 aplikacja nie musi już przydzielać miejsca dla certyfikatu zdalnego. Jednak starsza opcja przydzielania miejsca dla certyfikatu serwera jest nadal dostępna, a certyfikaty przydzielone przez użytkownika będą używane przed optymalizacją wewnętrznego buforu certyfikatów <sup>13</sup> — aby uzyskać więcej informacji, zobacz ***nx_secure_tls_remote_certificate_allocate*** Service.

Po utworzeniu zaufanego magazynu certyfikatów i przydzieleniu miejsca dla certyfikatu serwera można użyć gniazda do nawiązania bezpiecznego połączenia klienta TLS.

13. Optymalizacja wykorzystuje "bufor pakietów" dostarczony przez aplikację użytkownika do sesji protokołu *TLS* przy użyciu programu nx_secure_tls_session_packet_buffer_set w celu przydzielenia struktur analizy X.509 zamiast używania struktur dostarczonych przez użytkownika używanych we wcześniejszych wersjach protokołu NetX Secure TLS. Istnieje mało prawdopodobna możliwość napotkania łańcucha certyfikatów przekraczającego rozmiar bufora pakietów. W takim  przypadku można zwiększyć rozmiar buforu pakietu lub użyć nx_secure_tls _remote_certificate_allocate do przydzielenia więcej miejsca dla łańcucha certyfikatów.

### <a name="application-interface-calls"></a>Wywołania interfejsu aplikacji

Aplikacje NetX Secure TLS zazwyczaj będą uruchamiać wywołania funkcji z wątków aplikacji uruchomionych w ramach threadX RTOS. Niektóre inicjowanie, szczególnie w przypadku podstawowych protokołów komunikacji sieciowej (np. TCP i IP), może być wywoływane z ***tx_application_define*.** Zobacz Podręcznik użytkownika NetX/NetXDuo, aby uzyskać więcej informacji na temat inicjowania komunikacji sieciowej.

TLS intensywnie wykorzystuje procedury szyfrowania, które są operacjami intensywnie obciążający procesor. Ogólnie rzecz biorąc, te operacje będą wykonywane w kontekście wywoływania wątku.

### <a name="tls-session-start"></a>Uruchamianie sesji TLS

Do działania protokołu TLS jest wymagany podstawowy protokół sieciowy warstwy transportu. Zazwyczaj używanym protokołem jest TCP. Aby ustanowić sesję protokołu NetX Secure TLS, należy ustanowić połączenie TCP przy użyciu interfejsu API TCP NetX/NetXDuo. Należy **NX_TCP_SOCKET** i nawiązyć połączenie przy użyciu usług nx_tcp_server_socket_listen _ i _ nx_tcp_server_socket_accept _ (dla serwera ***TLS)* lub usługi __nx_tcp_client_socket_connect_** (dla klienta TLS).

Po nawiązaniu połączenia TCP gniazdo TCP jest następnie przekazywane do ***nx_secure_tls_session_start*** usługi.

### <a name="tls-packet-allocation"></a>Alokacja pakietów protokołu TLS

Protokół NetX Secure TLS używa tej samej struktury pakietów co protokół TCP NetX/NetXDuo (***NX_PACKET** _), z tą różnicą, że zamiast wywoływania usługi _*_nx_packet_allocate_*_ należy wywołać usługę *__nx_secure_tls_packet_allocate_**, aby można było prawidłowo przydzielić miejsce dla nagłówka protokołu TLS.

### <a name="tls-session-send"></a>Wysyłanie sesji TLS

Po zakończeniu sesji TLS aplikacja może wysyłać dane przy użyciu usługi ***nx_secure_tls_session_send** _service. Usługa wysyłania jest identyczna w użyciu z usługą _*_nx_tcp_socket_send,_*_ biorąc strukturę danych usługi NX_PACKET zawierającą wysyłane dane, tylko te dane będą szyfrowane przez stos SECURE TLS nx przed wysłaniem, _*_a_*_ pakiet musi zostać przydzielony przy użyciu _*_nx_secure_tls_packet_allocate_**.

### <a name="tls-session-receive"></a>Odbieranie sesji TLS

Po rozpoczęciu sesji TLS aplikacja może rozpocząć odbieranie danych przy użyciu usługi ***nx_secure_tls_session_receive** _. Podobnie jak w przypadku wysyłania sesji protokołu TLS, ta usługa jest identyczna w użyciu z _*_nx_tcp_socket_receive_**, z tą różnicą, że dane przychodzące są odszyfrowywane i weryfikowane przez stos protokołu TLS przed zwróceniem w strukturze pakietów.

### <a name="tls-session-close"></a>Zamykanie sesji TLS

Po zakończeniu sesji TLS zarówno klient TLS, jak i serwer muszą wysłać alert CloseNotify do drugiej strony, aby zamknąć sesję. Obie strony muszą odebrać i przetworzyć alert, aby zapewnić pomyślne zamknięcie sesji.

Jeśli host zdalny wyśle alert CloseNotify, wszystkie wywołania do usługi ***nx_secure_tls_session_receive** _ przetworzyć alert, wysłać odpowiedni alert z powrotem do hosta zdalnego i zwrócić wartość __*_ NX_SECURE_TLS_SESSION_CLOSED **. Po zamknięciu sesji wszystkie kolejne próby wysłania lub odbierania danych z tej sesji TLS nie powiodą się.

Jeśli aplikacja chce zamknąć sesję TLS, należy nx_secure_tls_session_end **_** service. Usługa wyśle alert CloseNotify i przetnie odpowiedź CloseNotify. Jeśli odpowiedź nie zostanie odebrana, zostanie zwrócona wartość błędu *__NX_SECURE_TLS_SESSION_CLOSE_FAIL_**, wskazująca, że sesja TLS nie została w sposób czysty zamknięty, co jest możliwym naruszeniem zabezpieczeń.

### <a name="tls-alerts"></a>Alerty TLS

Protokół TLS został zaprojektowany w celu zapewnienia maksymalnego bezpieczeństwa, dlatego każde błędne zachowanie protokołu jest uznawane za potencjalne naruszenie zabezpieczeń. Z tego powodu wszelkie błędy przetwarzania komunikatów lub szyfrowania/odszyfrowywania są uznawane za błędy krytyczne, które natychmiast przerywają ugodę lub sesję.

Chociaż obsługa błędów w aplikacji lokalnej jest stosunkowo prosta, host zdalny musi wiedzieć, że wystąpił błąd, aby prawidłowo obsłużyć tę sytuację i zapobiec kolejnym możliwym naruszeniom zabezpieczeń. Z tego powodu usługa TLS wyśle do hosta zdalnego *komunikat o alertach* po każdym błędzie.

Alerty są traktowane w taki sam sposób jak inne komunikaty TLS i są szyfrowane podczas sesji, aby uniemożliwić osobie atakującej zbieranie informacji z typu dostarczonego alertu. Podczas tego procesu wysyłane alerty mają ograniczony zakres, aby ograniczyć ilość informacji, które mogą zostać uzyskane przez potencjalnego atakującego.

Alert CloseNotify używany do zamknięcia sesji TLS jest jedynym alertem nie krytycznym. Chociaż jest uznawany za alert i wysyłany jako komunikat alertu, element CloseNotify różni się od innych alertów tym, że nie wskazuje, że wystąpił błąd.

Wartość alertu i "poziom" (poziomy to "ostrzeżenie" i "krytyczne" — większość alertów TLS jest "krytycznych") są zdefiniowane w RFC TLS i wskazują typ błędu, który wystąpił. Większość alertów TLS innych niż CloseNotify może być traktowana jako wskazanie potencjalnego problemu z zabezpieczeniami i spowoduje przerwanie sesji lub uścisku TLS. Jeśli dowolne wywołanie interfejsu API TLS zwraca wartość **NX_SECURE_TLS_ALERT_RECEIVED** (0x114), usługa interfejsu API **_nx_secure_tls_session_alert_value_get_** (nowość w programie NetX Secure TLS w wersji 5.12) może służyć do pobierania wartości i poziomu alertu TLS, aby aplikacja używana do podejmowania decyzji dotyczących odpowiedzi na problemy z zabezpieczeniami. W większości przypadków każdy alert otrzymany z hosta zdalnego innego niż CloseNotify powinien być traktowany jako błąd krytyczny, chociaż istnieją pewne fragmenty — zobacz RFC protokołu TLS, aby uzyskać więcej informacji.

### <a name="tls-session-renegotiation"></a>Renegocjacja sesji TLS

TLS obsługuje pojęcie "ponownego negocjowania", które jest po prostu renegocją parametrów sesji TLS w kontekście istniejącej sesji TLS. W praktyce oznacza to, że nowe komunikaty z ugodą są szyfrowane i uwierzytelniane przy użyciu istniejącej sesji. Renegocja jest używana, gdy host TLS chce wygenerować nowe parametry sesji (np. wygenerować nowe klucze sesji TLS) bez konieczności ukończenia istniejącej sesji. Na przykład ponowne negocjowanie może być pożądane, gdy zasady zabezpieczeń aplikacji określają, że klucze sesji są używane tylko przez ograniczony czas, ale sesja TLS pozostaje aktywna po tym czasie.

Jednym z problemów z ponowną negocjacją sesji jest to, że powoduje, że dostęp TLS jest narażony na określony atak typu Man-in-the-Middle, w którym osoba atakująca może przekonać serwer do zainicjowania ponownej negocjacji z nowymi parametrami, co pozwala osobie atakującej przejąć sesję TLS. Aby rozwiązać ten problem, wprowadzono rozszerzenie oznaczania bezpiecznego ponownego negocjowania (zobacz sekcję **Błąd! Nie znaleziono źródła odwołania.** ).

Zabezpieczenia NetX TLS w pełni obsługują ponowne negocjowanie sesji i rozszerzenie oznaczania bezpiecznego ponownego negocjowania.

Podczas odbierania danych z hosta zdalnego renegocjacje (i rozszerzenie) są obsługiwane automatycznie bez interakcji z aplikacją. Jeśli wymagane jest powiadomienie o ponownych negocjacjach sesji, wywołanie zwrotne renegocjowania może zostać dostarczone z nx_secure_tls_session_renegotiate_callback_set *usługą.* Wywołanie zwrotne będzie wywoływane za każdym razem, gdy host zdalny zażąda ponownej negocjacji, dzięki czemu aplikacja może podjąć odpowiednie działania.

Aby zainicjować ponowne negocjowanie z aktywnej sesji TLS, po prostu *wywołaj* usługę nx_secure_tls_session_renegotiate w żądanej sesji TLS.

### <a name="tls-session-resumption"></a>Wznowienie sesji TLS

Wznowienie sesji TLS nie powinno być mylone z renegocją sesji, pomimo pewnych podobieństw. Jeśli *ponowna* negocjacja sesji obejmuje rozpoczęcie nowego ugody  w ramach istniejącej sesji TLS, wznowienie sesji jest wyłącznie opcjonalną funkcją, która polega na ponownym uruchomieniu zamkniętej sesji TLS bez przeprowadzania pełnego ugody TLS. Aby to osiągnąć, implementacja TLS może buforować parametry sesji i klucze, kojarząc je z identyfikatorem *sesji,* unikatowym identyfikatorem dostarczonym podczas pierwotnego ugody. Po podaniem identyfikatora sesji serwerowi TLS klient wskazuje, że poprzednia sesja TLS między hostami istniała i zakończyła się jakiś czas w przeszłości, a klient nadal posiada stan, aby ponownie ustanowić sesję z ograniczoną uściślą. Ponieważ klucze sesji są teoretycznie nadal tajne i znane tylko przez dwóch komunikując się hostów, serwer może uruchomić nową sesję TLS i pominąć większość normalnego ugody.

Wznowienie sesji może być przydatne w celu uniknięcia potencjalnie kosztownych operacji klucza publicznego używanych do udostępniania głównego klucza tajnego generowania kluczy i weryfikowania podpisów certyfikatów, ale wymaga również, aby parametry sesji, klucze i stan kryptograficzny był utrzymywany w pamięci dla wszystkich możliwych sesji (co najmniej w przypadku konfigurowalnego okna czasowego).

Bieżąca wersja bezpiecznego zabezpieczenia TLS NetX nie obsługuje wznawiania sesji — identyfikator sesji jest po prostu ignorowany przez serwery TLS, a klienci TLS zawsze podają identyfikator sesji o wartości NULL, który monituje serwer o przeprowadzenie pełnego ugody. Brak wznowienia sesji nie powinien powodować żadnych problemów dotyczących współdziałania, ponieważ jest to funkcja całkowicie opcjonalna, a wszystkie implementacje TLS muszą domyślnie zostać zakończone, jeśli identyfikator sesji ma wartość NULL lub jest nierozpoznany.

### <a name="protocol-layering"></a>Warstwy protokołów

Protokół TLS pasuje do stosu sieciowego między warstwą transportu (np. TCP) a warstwą aplikacji. Protokół TLS jest czasami traktowany jako protokół warstwy transportu (stąd *Transport Layer* Security), ale ponieważ działa jako aplikacja w odniesieniu do podstawowych protokołów sieciowych (takich jak TCP), jest czasami grupowany w warstwie aplikacji.

Protokół TLS wymaga protokołu warstwy transportu, który obsługuje dostarczanie w porządek i bezstratne, takie jak TCP. Ze względu na to wymaganie nie można uruchomić protokołu TLS na podstawie protokołu UDP, ponieważ protokołu UDP nie gwarantuje dostarczenia datagramów. Oddzielny protokół o nazwie *DTLS,* który jest zmodyfikowaną wersją protokołu TLS, jest używany dla aplikacji, które wymagają zabezpieczeń protokołu TLS za pośrednictwem protokołu datagramu, takiego jak UDP. NetX Secure obsługuje usługi DTLS, ale dokumentacja dotycząca usługi DTLS jest oddzielona od tego dokumentu.

![Diagram warstw protokołu TCP/IP i TLS.](media/image6.png)

Rysunek 5. Warstwy protokołu TCP/IP i TLS

## <a name="network-communications-security"></a>Zabezpieczenia komunikacji sieciowej

Zabezpieczanie komunikacji za pośrednictwem sieci publicznych i Internetu jest niezwykle ważnym tematem i tematem ogromnej liczby książek, artykułów i rozwiązań. Temat jest bardzo złożony, ale można go ograniczyć do prostego pomysłu: wysyłania informacji za pośrednictwem sieci, aby tylko zamierzony element docelowy miał dostęp do tych informacji lub je zmieniał. Dzieli się to na trzy ważne pojęcia: uwierzytelnianie, uwierzytelnianie i uwierzytelnianie. Protokół TLS zapewnia rozwiązania dla wszystkich trzech.

### <a name="secrecy"></a>Tajemnicy

Podczas wysyłania danych za pośrednictwem sieci często ważne jest, aby nie można było uzyskać tych danych przez złośliwą jednostkę. Jeśli dane są wysyłane za pośrednictwem połączenia TCP/IP, każda osoba mająca dostęp do sieci będzie mogła odczytać te dane przy użyciu łatwo dostępnych narzędzi sieciowych. Aby zapobiec uzyskaniu tych danych, muszą one być zakodowane w taki sposób, aby nie można było ich odczytać z wyjątkiem zamierzonego obiektu docelowego — jest to *sekwowanie.* W przypadku szyfrowania TLS algorytmy szyfrowania, takie jak RSA i AES, zapewniają tajemnicę.

### <a name="integrity"></a>Integralność

Czasami sekwowanie nie wystarcza do ochrony przed przechowaniami danych za pośrednictwem sieci. W niektórych przypadkach złośliwy podmiot może zmienić zawartość pakietu TCP bez konieczności wiedzieć, co zawiera ten pakiet. Zaszyfrowane dane mogą być zmieniane, co powoduje nieprawidłowe odszyfrowywanie lub zmianę parametrów komunikatu, co prowadzi do dowolnego wyniku, który osoba atakująca może być zainteresowana osiągnięciem. W sieci nie możemy uniemożliwić osobie atakującej zmiany danych podczas przesyłania, ale możemy zapewnić mechanizm, aby wiedzieć, czy dane zostały zmienione. Gdy dane są zmieniane podczas przesyłania, będą znane i można je odrzucić. Ta koncepcja to *integralność*. W przypadku szyfrowania TLS integralność jest zapewniana przez klasę procedur kryptograficznych znanych jako *funkcje skrótu*. Niektóre przykłady funkcji wyznaczania wartości skrótu to MD5 i SHA-1.

### <a name="authentication"></a>Authentication

Trzecia ważna koncepcja zabezpieczeń komunikacji sieciowej polega na tym, że dane powinny być przekazywane tylko do zamierzonego celu. Osoba atakująca może próbować stanowić legalną jednostkę do odbierania danych przeznaczonych dla innego hosta. Nawet jeśli dane są wysyłane przy użyciu mechanizmów tajemnicy i integralności, osoba atakująca może nadal osiągnąć pożądany wynik (naruszenie bezpieczeństwa komunikacji) za pomocą tego oszustwa. Aby temu zapobiec, wymagany jest mechanizm do potwierdzenia tożsamości hosta zdalnego przed wysłaniem poufnych danych. Proces potwierdzania tożsamości hosta zdalnego to *uwierzytelnianie.* W przypadku protokołu TLS uwierzytelnianie jest zapewniane przy  użyciu certyfikatów cyfrowych, funkcji skrótów i mechanizmu nazywanego podpisami cyfrowymi, który wykorzystuje właściwość szyfrowania kluczem publicznym (opisana poniżej). Ograniczoną, ale przydatną formę uwierzytelniania można również udostępnić przy użyciu *klucza* wstępnego (PSK).

## <a name="tls-encryption"></a>Szyfrowanie TLS

Protokół TLS jest platformą zapewniającą bezpieczną komunikację sieciową przez Internet przy użyciu szyfrowania. Szyfrowanie jest ogólnie definiowane jako proces kodowania danych w taki sposób, że uzyskanie oryginalnych danych (lub informacji o tych danych) jest niezwykle trudne bez *klucza*. W systemach komputerowych szyfrowanie opiera się na złożonej matematyce, takiej jak skończone  pola, i może być klasyfikowane na dwa typy:  klucz prywatny (lub szyfrowanie symetryczne) i klucz publiczny (lub szyfrowanie *asymetryczne).* Przykłady szyfrowania klucza prywatnego to AES (Advanced Encryption Standard) i RC4 (Rivest Cipher 4). Przykłady szyfrowania kluczem publicznym to RSA (Rivest, Shamir, Adleson) i Diffie-Hellman szyfry.

Protokół TLS korzysta zarówno z procedur szyfrowania klucza prywatnego, jak i klucza publicznego w celu zapewnienia równowagi między wydajnością, zabezpieczeniami i elastycznością.

### <a name="private-key-encryption"></a>Private-Key szyfrowania

Szyfrowanie kluczem prywatnym jest w użyciu od tysięcy lat. Szyfry podstawień podstawowych (gdzie litera lub słowo jest zastępowane inną niepowiązaną literą lub słowem) to najwcześniejsze znane przykłady szyfrowania, ale wraz z pojawieniem się wieku informacji szyfrowanie klucza prywatnego znacznie się poprawiło.

Szyfr klucza prywatnego używa "klucza", który jest po prostu wartością (w ogólnym przypadku może to być słowo, fraza lub liczba), która jest używana do kodowania niektórych danych, tak aby tylko jednostka, która miała dostęp do tego klucza, mogła zdekodować dane w zrozumiały sposób. Klucz jest używany zarówno do szyfrowania, jak i odszyfrowywania danych, dlatego inna nazwa to *szyfrowanie symetryczne*.

Szyfry klucza prywatnego są zwykle szybkie i dość proste do zaimplementowania, nawet jeśli związane z matematyką są niezwykle złożone. Z tego powodu szyfrowanie TLS używa szyfrów klucza prywatnego do zbiorczej bezpiecznej komunikacji.

Jednak szyfrowanie klucza prywatnego ma problem podczas próby zastosowania go do ogólnej komunikacji sieciowej komputera: klucz musi być współużytkować obie maszyny próbujące się komunikować. W ogólnym przypadku niepraktyczne i często niemożliwe jest bezpieczne komunikowanie klucza prywatnego między dwiema maszynami w Internecie, ponieważ można założyć, że ruch sieciowy może być uzyskiwany przez dowolną liczbę jednostek w różnych przeskoków, które dane pobierają podczas przekierowywania przez Internet. Jeśli klucz zostanie uzyskany przez złośliwą jednostkę, wszystkie dane zaszyfrowane przy użyciu tego klucza będą zagrożone. Ponieważ większość maszyn w Internecie ma tylko połączenie sieciowe, a nie inny bezpieczny kanał komunikacji, wysyłanie kluczy za pośrednictwem sieci jest równoznaczne z wysyłaniem danych niezaszyfrowanych — nie zapewnia zabezpieczeń.

Z tego powodu szyfrowanie klucza prywatnego nie jest wystarczające do zaimplementowania protokołu zabezpieczeń komunikacji sieciowej ogólnego przeznaczenia. Jest to miejsce, w którym może pomóc szyfrowanie klucza publicznego.

NetX Secure TLS obsługuje szyfrowanie kluczem prywatnym AES.

### <a name="public-key-encryption"></a>Public-Key szyfrowania

W przeciwieństwie do szyfrowania klucza prywatnego szyfrowanie klucza publicznego jest dość nową koncepcją, opracowaną w latach 70. Korzystając z koncepcji znanej w matematyce jako "funkcje pułapki-drzwi", odkryliśmy, że istnieje sposób udostępniania klucza za pośrednictwem sieci bez naruszania bezpieczeństwa zaszyfrowanych danych.

Sposób działania szyfrowania klucza publicznego jest taki, że klucz (w opisanym powyżej sensie  szyfrowania klucza prywatnego) jest podzielony na dwie części: klucz prywatny i klucz *publiczny,* z którego szyfrowanie klucza publicznego pobiera jego nazwę. Koncepcja jest taka, że jeden z tych kluczy (zazwyczaj klucz publiczny) jest używany do szyfrowania, a drugi do odszyfrowywania. Ta asymetria kluczy jest przyczyną innej nazwy szyfrowania klucza publicznego: szyfrowanie *asymetryczne*.

Matematyka na temat szyfrowania kluczem publicznym jest dość złożona, ale chodzi o to, że klucz publiczny może być używany tylko do szyfrowania i uzyskanie tego klucza nie zezwala na uzyskiwanie zaszyfrowanych danych.  Klucz prywatny jest z kolei jedynym sposobem odszyfrowywania danych zaszyfrowanych przy użyciu klucza publicznego. W związku z tym dzięki zachowaniu klucza prywatnego każdy, kto chce bezpiecznie komunikować się z właścicielem tego klucza prywatnego, musi zaszyfrować swoje dane tylko przy użyciu odpowiedniego klucza publicznego, mając wiedzę, że tylko osoba mająca ten klucz prywatny może uzyskać bezpieczne dane.

NetX Secure TLS obsługuje szyfrowanie kluczem publicznym RSA.

> [!IMPORTANT] 
> *RSA jest operacją intensywnie obciążaną procesorem, jeśli jest używana implementacja oprogramowania RSA. Większe rozmiary kluczy zwiększają moc przetwarzania wymaganą przez współczynnik kwadratowy — 4 razy wolniejszy w przypadku 2-dziesiątego zwiększenia rozmiaru klucza.*

### <a name="public-key-authentication"></a>Public-Key uwierzytelniania

Interesującym efektem ubocznym koncepcji szyfrowania kluczem publicznym jest to, że może służyć do zapewnienia uwierzytelniania, a także szyfrowania, wykonując operację odwrotnie: szyfrowanie przy użyciu klucza prywatnego i odszyfrowywanie przy użyciu klucza *publicznego.*  Rzeczywisty mechanizm ten zależy od używanego algorytmu klucza publicznego, ale koncepcja jest taka sama.

Aby uwierzytelnić się przy użyciu uwierzytelniania za pomocą klucza publicznego, właściciel klucza prywatnego szyfruje niektóre dane (zazwyczaj kryptograficzne skróty danych do uwierzytelnienia) przy użyciu tego klucza prywatnego. Następnie ktoś, kto chce uwierzytelnić, że dane pochodzi od właściciela klucza prywatnego, używa skojarzonego klucza publicznego do odszyfrowania danych — jeśli odszyfrowanie powiedzie się i przy założeniu, że użytkownik zaufał ważności tego klucza publicznego, użytkownik może mieć pewność, że dane pochodziły od właściciela klucza prywatnego.

W przypadku protokołu TLS uwierzytelnianie za pomocą klucza publicznego służy do weryfikowania ważności certyfikatu cyfrowego dostarczonego przez serwer TLS (i opcjonalnie klienta TLS) przy użyciu kluczy publicznych z magazynu zaufanych certyfikatów. Certyfikat jest sprawdzany względem klucza publicznego w magazynie, a dane w certyfikacie są używane do sprawdzania tożsamości serwera.

NetX Secure TLS obsługuje uwierzytelnianie RSA.

### <a name="cryptographic-hashing"></a>Kryptograficzne skróty

Szyfrowanie nie jest jedyną operacją kryptograficznymi używaną w technologii TLS. Aby zapewnić integralność komunikatów podczas sesji TLS, potrzebna jest sumy kontrolnej, aby upewnić się, że zawartość komunikatu nie została naruszona. Jednak prosta suma kontrolna (używana w protokole TCP) jest niewystarczająca do zagwarantowania akceptowalnego poziomu integralności, ponieważ może zostać łatwo odwrócona przez znajomą atakującą. Mechanizm używany przez usługę TLS do zapewnienia integralności komunikatów jest nazywany *skrótem kryptograficznym*.

Szyfrowanie to kodowanie 1:1, czyli całe oryginalne dane można uzyskać z zaszyfrowanych danych. Skrót mapuje jednak dowolną ilość danych na stałą wartość rozmiaru, podobnie jak sumę kontrolną. W przeciwieństwie do prostej sumy kontrolnej skrót został zaprojektowany specjalnie w celu zmniejszenia kolizji, gdzie różne dane wejściowe spowodują te same dane wyjściowe. W prostej sumy kontrolnej, jeśli bit jest przerzucony z 1 do 0 i inny bit z 0 do 1, sumy kontrolnej jest taka sama. W przypadku skrótu kryptograficznego dane wyjściowe będą się znacznie różnić, co utrudnia osobie atakującej zmianę skrótu danych i wykonanie operacji wyznaczania wartości skrótu dla zmienionych danych nadal będzie skutkować taką samą wartością (i w ten sposób fałszywie zweryfikować integralność tych danych).

TLS używa wielu różnych algorytmów wyznaczania wartości skrótu, aby zapewnić integralność komunikatów, zarówno komunikatów aplikacji, jak i komunikatów sterujących TLS. Należą do nich MD5, SHA-1 i SHA-256.

Funkcja NetX Secure TLS obsługuje skróty MD5, SHA-1 i SHA-256.

## <a name="tls-extensions"></a>Rozszerzenia TLS

TLS udostępnia wiele rozszerzeń, które zapewniają dodatkowe funkcje dla niektórych aplikacji. Te rozszerzenia są zwykle wysyłane jako część komunikatów ClientHello lub ServerHello, wskazując hostowi zdalneowi chęć użycia rozszerzenia lub podając dodatkowe szczegóły do użycia podczas ustanawiania bezpiecznej sesji TLS.

Ogólnie rzecz biorąc, rozszerzenia zapewniają opcjonalne parametry do obsługi TLS na początku procedury praktycznej, która będzie kierować działaniami. Niektóre rozszerzenia wymagają danych wejściowych aplikacji lub podejmowania decyzji, podczas gdy inne są obsługiwane automatycznie.

W poniższej tabeli opisano rozszerzenia TLS, które są obecnie obsługiwane przez zabezpieczenia TLS netx:

| **Nazwa rozszerzenia**              | **Opis**              |
| ------------------------------- |----------------------------- |
| Wskaźnik bezpiecznej ponownej negocjacji | To rozszerzenie ogranicza lukę w zabezpieczeniach ataku typu Man-in-the-Middle, która może wystąpić podczas ponownego negocjowania.|
| Oznaczanie nazwy serwera          | To rozszerzenie umożliwia klientowi TLS dostarczenie określonej nazwy DNS serwerowi TLS, umożliwiając serwerowi wybranie poprawnych poświadczeń (przy założeniu, że serwer ma wiele certyfikatów tożsamości i punktów wejścia sieciowego). |
| Algorytmy podpisu            | To rozszerzenie umożliwia klientowi TLS podanie listy akceptowalnych algorytmów podpisu i skrótu dla serwera TLS. |

Omówienie obsługiwanych rozszerzeń TLS

### <a name="secure-renegotiation-indication"></a>Wskaźnik bezpiecznej ponownej negocjacji

TLS obsługuje sposób przeprowadzania uściślicia w ramach istniejącej sesji TLS, a tym samym użycie ustanowionej sesji w celu zaszyfrowania komunikatów uściślniania. Ten proces umożliwia ponowne ustanowione klucze sesji kryptograficznych bez kończenia sesji TLS (zobacz sekcję "Renegocjacja sesji TLS").

Niestety, po tym, jak przez pewien czas TLS używało renegocjowania, okazało się, że istnieje luka w zabezpieczeniach umożliwiająca atak typu Man-in-the-Middle, który wykorzystuje funkcję renegocjowania. Aby zamknąć tę lukę w zabezpieczeniach, wprowadzono rozszerzenie Oznaczanie bezpiecznej renegocjacji. Zasadniczo rozszerzenie Secure Renegotiation używa skrótu komunikatu Zakończono z ustanowionego połączenia, aby sprawdzić, czy oryginalne hosty uczestniczą w renegocjacji — zasadniczo skrót jest używany jako token weryfikacyjny przy założeniu, że osoba atakująca nie będzie mogła podszyć się pod skrót (co wymagałoby dostępu do kluczy sesji).

NetX Secure TLS obsługuje renegocjacje automatycznie i domyślnie używa rozszerzenia Secure Renegotiation. Nie jest wymagana żadna interakcja aplikacji.

### <a name="server-name-indication"></a>Oznaczanie nazwy serwera

Podczas ugody TLS klient TLS oczekuje, że serwer zdalny udostępni certyfikat tożsamości, aby klient może uwierzytelnić serwer. Mogą jednak wystąpić przypadki, w których serwer będzie zapewniać wiele różnych usług z różnymi "wirtualnymi" serwerami, z których każda ma unikatowe tożsamości. W przypadku pojedynczego serwera z wieloma tożsamościami klient TLS może podać określoną nazwę DNS, która będzie przez serwer używane do wybierania odpowiednich poświadczeń — mechanizmem do dostarczania tej nazwy jest rozszerzenie Oznaczanie nazwy serwera (SNI).

W przypadku aplikacji używającej rozszerzenia SNI wymagana jest interakcja. W przypadku klientów TLS aplikacja musi podać nazwę DNS, która ma zostać wysłana do serwera zdalnego. W przypadku serwerów TLS aplikacja musi odczytać nazwę DNS z rozszerzenia i wybrać odpowiedni certyfikat do wysłania z powrotem do klienta.

Poniższe sekcje zawierają więcej szczegółów na temat korzystania z rozszerzenia SNI w netx Secure TLS.

### <a name="sni-extension--tls-client"></a>Rozszerzenie SNI — klient TLS

Klient NetX Secure TLS, który chce korzystać z rozszerzenia SNI, musi podać nazwę DNS dla TLS, która zostanie dostarczona podczas procesu praktycznego. Ta nazwa musi zostać zainicjowana i dostarczona przed rozpoczęciem sesji TLS, ponieważ rozszerzenie jest wysyłane w komunikacie ClientHello, który rozpoczyna proces uściślania.

Poniższy fragment kodu ilustruje użycie rozszerzenia . Najpierw obiekt NX_SECURE_X509_DNS_NAME jest inicjowany z żądaną nazwą serwera. Następnie przed rozpoczęciem sesji TLS nazwa jest dostarczana do usługi TLS przy użyciu interfejsu API rozszerzenia SNI. Po skonfigurowaniu nazwy nie jest wymagana żadna dalsza akcja. Zobacz dokumentacja interfejsu API w rozdziale 4  
  
Opis bezpiecznych usług NetX, aby uzyskać więcej informacji na temat poszczególnych funkcji.

```C
/* The dns_name variable will contain our desired server name. */
UINT status;
NX_SECURE_X509_DNS_NAME dns_name;

/* Initialize the server DNS name. */
status = nx_secure_x509_dns_name_initialize(&dns_name, "www.example.com", 
                                            strlen("www.example.com"));


/* Initialize SNI extension in previously-initialized TLS Session. */
status = nx_secure_tls_session_sni_extension_set(&client_tls_session, &dns_name);

/* Now start the TLS session, starting with establishing the TCP connection – if 
   TLS is started before initializing the SNI extension, the extension will not be 
   sent in the ClientHello message! */
status = nx_tcp_client_socket_connect(&client_socket, IP_ADDRESS(1, 2, 3, 4), 443, 
                                      5 * NX_IP_PERIODIC_RATE);

status = nx_secure_tls_session_start(&client_tls_session, &client_socket, 
                                     NX_WAIT_FOREVER);
```
### <a name="sni-extension--tls-server"></a>Rozszerzenie SNI — serwer TLS

Po stronie serwera TLS rozszerzenie SNI może zostać przetworzone przez aplikację w celu wybrania odpowiednich poświadczeń (np. certyfikatu) do podania klientowi zdalnemu podczas procesu praktycznego. W tym celu aplikacja musi podać wywołanie zwrotne sesji wywoływane po otrzymaniu komunikatu ClientHello.

Przykładowy kod interfejsu API nx_secure_tls_session_server_callback_set (zobacz stronę 122) ilustruje analizowanie przychodzącego rozszerzenia SNI przy użyciu wywołania zwrotnego serwera. Zasadniczo serwer TLS odbiera element ClientHello i wywołuje wywołanie zwrotne. Następnie aplikacja używa interfejsu API usługi *nx_secure_tls_session_sni_extension_parse* do analizowania danych rozszerzenia dostarczonych do wywołania zwrotnego w celu znalezienia rozszerzenia SNI i zwrócenia podanej nazwy DNS (należy pamiętać, że rozszerzenie obsługuje tylko jedną nazwę DNS). Po pozyskanych nazwach aplikacja używa jej do znalezienia i wysłania odpowiedniego certyfikatu tożsamości serwera (i łańcucha wystawców, jeśli ma to zastosowanie).

### <a name="signature-algorithms-extension"></a>Rozszerzenie algorytmów podpisu

To rozszerzenie jest specyficzne dla wersji TLS 1.2 i umożliwia klientowi TLS podanie listy akceptowalnych par sygnatur i algorytmów wyznaczania wartości skrótu, które mogą być używane podczas generowania i weryfikowania podpisów cyfrowych. Lista jest generowana automatycznie przez program NetX Secure TLS dla klientów TLS przy użyciu tabeli szyfrowania dostarczonej do *usługi nx_secure_tls_session_create*. Nie jest wymagana żadna interakcja aplikacji.

## <a name="authentication-methods"></a>Metody uwierzytelniania

TLS zapewnia platformę do ustanawiania bezpiecznego połączenia między dwoma urządzeniami za pośrednictwem niezabezpieczonych sieci, ale częścią problemu jest znajomość tożsamości urządzenia na drugim końcu tego połączenia. Bez mechanizmu uwierzytelniania tożsamości hostów zdalnych atakujący może chcieć pozować jako zaufane urządzenie.

Początkowo może się wydawać, że użycie adresów IP, sprzętowych adresów MAC lub systemu DNS zapewni stosunkowo wysoki poziom ufności do identyfikowania hostów w sieci, ale ze względu na charakter technologii TCP/IP oraz łatwość fałszowania adresów i uszkodzenia wpisów DNS (np. za pomocą zatrucia pamięci podręcznej DNS) staje się jasne, że protokół TLS wymaga dodatkowej warstwy ochrony przed fałszywymi tożsamościami.

Istnieją różne mechanizmy, które mogą zapewnić tę dodatkową warstwę uwierzytelniania dla protokołu TLS, ale najczęściej jest to *certyfikat cyfrowy.* Inne mechanizmy to klucze wstępne (PSK) i schematy haseł.

### <a name="digital-cerificates"></a>Cyfrowe ceryfikaty

Certyfikaty cyfrowe to najczęstsza metoda uwierzytelniania hosta zdalnego w technologii TLS. Zasadniczo certyfikat cyfrowy to dokument z określonym formatowaniem, który dostarcza informacje o tożsamości dla urządzenia w sieci komputerowej.

Standard TLS zwykle używa formatu O nazwie X.509, standardu opracowanego przez Międzynarodowy Związek Telekomunikacyjny, chociaż można użyć innych formatów certyfikatów, jeśli hosty TLS mogą wyrazić zgodę na używany format. X.509 definiuje określony format certyfikatów i różnych kodowań, których można użyć do tworzenia dokumentu cyfrowego. Większość certyfikatów X.509 używanych z TLS jest kodowana przy użyciu wariantu ASN.1, innego standardu telekomunikacyjnego. W ramach usługi ASN.1 istnieją różne kodowania cyfrowe, ale najpopularniejszym kodowaniem certyfikatów TLS jest standard Distinguished Encoding Rules (DER). DER to uproszczony podzbiór podstawowych reguł kodowania ASN.1 (BER), który został zaprojektowany tak, aby był jednoznaczny, co ułatwia analizowanie. Za pośrednictwem połączenia certyfikaty TLS są zwykle kodowane w binarnym formacie DER i jest to format, który NetX Secure oczekuje dla certyfikatów X.509.

Chociaż certyfikaty binarne w formacie DER są używane w rzeczywistym protokole TLS, mogą być generowane i przechowywane w wielu różnych kodowaniach z rozszerzeniami plików, takimi jak PEM, CRT i P12. Różne warianty są używane przez różne aplikacje różnych producentów, ale ogólnie wszystkie można przekonwertować na der przy użyciu powszechnie dostępnych narzędzi.

Najczęstszym z alternatywnych kodowań certyfikatów jest PEM. Format PEM (z usługi Privacy-Enhanced Mail) to zakodowana w formacie Base-64 wersja kodowania DER, która jest często używana, ponieważ kodowanie powoduje drukowanie tekstu, który można łatwo wysłać przy użyciu poczty e-mail lub protokołów internetowych.

Generowanie certyfikatu dla aplikacji NetX Secure zwykle znajduje się poza zakresem tego podręcznika, ale narzędzie wiersza polecenia OpenSSL[(www.openssl.org)](http://www.openssl.org)jest powszechnie dostępne i można go konwertować między większość formatów.

W zależności od aplikacji można wygenerować własne certyfikaty, zostać dostarczone przez producenta lub organizację rządową albo zakupić certyfikaty od komercyjnego urzędu certyfikacji.

Aby użyć certyfikatu cyfrowego w aplikacji NetX Secure, należy najpierw przekonwertować certyfikat na binarny format DER i opcjonalnie przekonwertować skojarzony klucz prywatny (na przykład "wykładnik prywatny" dla RSA) na format binarny, zazwyczaj klucz RSA w formacie PKCS#1 lub klucz ECC zakodowany w formacie DER. Po zakończeniu konwersji do urządzenia należy załadowanie certyfikatu i klucza prywatnego. Możliwe opcje obejmują użycie systemu plików opartego na technologii flash lub wygenerowanie tablicy C na podstawie danych (przy użyciu narzędzia takiego jak "xxd" z systemu Linux) i skompilowanie certyfikatu i klucza w aplikacji jako danych stałych.

Po załadowaniu certyfikatu na urządzenie można użyć interfejsu API TLS do skojarzenia certyfikatu z sesją TLS.

Aby uzyskać szczegółowe informacje i przykłady dotyczące używania certyfikatów X.509 z bezpiecznymi zabezpieczeniami TLS netx, zobacz sekcję "Importowanie certyfikatów X.509 do usługi NetX Secure".

Aby uzyskać więcej informacji, zapoznaj się z następującymi usługami TLS w interfejsie API:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_local_certificate_remove
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_trusted_certificate_add
- nx_secure_trusted_certificate_remove

### <a name="tls-client-certificate-specifics"></a>Specyfika certyfikatu klienta TLS

Implementacje klienta TLS zwykle nie wymagają załadowania na urządzenie "lokalnego" certyfikatu<sup>14.</sup> Wyjątkiem jest to, gdy jest włączone uwierzytelnianie certyfikatu klienta, ale jest to znacznie rzadziej spotykane.

Klient TLS wymaga załadowania co najmniej jednego "zaufanego" certyfikatu<sup>15</sup> (w razie potrzeby może zostać załadowany więcej certyfikatów) oraz miejsca na przydzielenie "zdalnego" certyfikatu<sup>16.</sup>

Aby uzyskać więcej informacji na temat dodawania zaufanych certyfikatów i przydzielania miejsca dla certyfikatów zdalnych, zobacz dokumentacja interfejsu API TLS dla następujących usług: nx_secure_tls_remote_certificate_allocate, nx_secure_tls_trusted_certificate_add.

14. Certyfikat "lokalny" to certyfikat, który identyfikuje urządzenie lokalne, czyli udostępnia informacje o tożsamości dla urządzenia, na którym jest ładowana aplikacja TLS.

15. Certyfikat "zaufany" to certyfikat, który stanowi podstawę zaufania i uwierzytelniania urządzenia zdalnego, bezpośrednio lub za pośrednictwem infrastruktury kluczy publicznych (PKI). Katalog główny łańcucha zaufania jest zwykle nazywany "urzędem certyfikacji" lub certyfikatem urzędu certyfikacji.

16. Certyfikat "zdalny" odnosi się do certyfikatu wysyłanego przez hosta zdalnego podczas procesu ugody TLS. Zapewnia tożsamość dla tego hosta zdalnego i jest uwierzytelniany przez porównanie go z certyfikatem "zaufanym" na urządzeniu lokalnym.

### <a name="tls-server-certificate-specifics"></a>Specyfika certyfikatu serwera TLS

Implementacje serwera TLS zazwyczaj nie wymagają załadowania "zaufanych" certyfikatów na urządzenie lub certyfikatów zdalnych do przydzielenia. Wyjątkiem jest to, gdy jest włączone uwierzytelnianie certyfikatu klienta (jest to rzadziej spotykane).

Serwer TLS wymaga załadowania "lokalnego" certyfikatu, aby serwer może udostępnić go klientowi zdalnej podczas procesu ugody TLS w celu uwierzytelnienia serwera na kliencie.

Aby uzyskać więcej informacji na temat ładowania certyfikatów lokalnych do użycia z aplikacjami serwera NetX TLS, zobacz dokumentacja interfejsu API dla następujących usług: 
- nx_secure_tls_local_certificate_add, 
- nx_secure_tls_local_certificate_remove.

### <a name="pre-shared-keys-psk"></a>Klucze wstępne (PSK)

Alternatywnym mechanizmem zapewniania uwierzytelniania identyfikacji w protokołach TLS jest określenie kluczy wstępnych (PSK). Użycie szyfru PSK nie wymaga stosowania operacji szyfrowania klucza publicznego intensywnie korzystających z procesora, które są boonem dla urządzeń osadzonych z ograniczeniami zasobów. Klucz wstępny zastępuje certyfikat w uściśliwce TLS i jest używany w miejsce zaszyfrowanego klucza tajnego wstępnego na czas generowania klucza sesji TLS.

Szyfry PSK są ograniczone w tym sensie, że wspólny klucz tajny musi być obecny na obu urządzeniach przed rozpoczęciem sesji TLS. Oznacza to, że urządzenia muszą zostać załadowane z tym kluczem tajnym przy użyciu pewnych bezpiecznych środków innych niż połączenie TLS PSK — klucz psk może być aktualizowany za pośrednictwem połączenia TLS PSK, ale urządzenie musi koniecznie rozpoczynać się od kluczu PSK, który jest ładowany za pośrednictwem innego mechanizmu. Na przykład urządzenie czujnika i jego urządzenie bramy można załadować z zestawami PSK w fabryce przed wysyłką lub użyć standardowego połączenia TLS (z certyfikatem) do załadowania zestawu PSK.

Szyfry PSK mają kilka formularzy opisanych w dokumencie RFC 4279. Pierwszy z nich używa RSA lub Diffie-Hellman, które są używane w taki sam sposób jak klucze publiczne przesyłane w certyfikacie w standardowych ugodach TLS. Druga forma, która jest bardziej używana w środowisku z ograniczonymi zasobami, używa klucza psk, który jest używany do bezpośredniego generowania kluczy sesji (na przykład do użycia przez usługę AES), unikając używania kosztownych operacji RSA lub Diffie-Hellman.

NetX Secure obsługuje drugą formę szyfrów PSK, umożliwiając aplikacjom usunięcie całego kodu kryptografii klucza publicznego i użycia pamięci. Klucz psk nie jest kluczem AES, ale można go traktować jako bardziej przypominać hasło, z którego są generowane rzeczywiste klucze. Istnieje kilka ograniczeń dotyczących wartości psk, chociaż dłuższe wartości zapewniają większe bezpieczeństwo (tak samo jak w przypadku haseł).

Aby używać funkcji PSK z aplikacją NetX Secure, należy najpierw zdefiniować globalne makro NX_SECURE_ENABLE_PSK_CIPHERSUITES **.** Zwykle odbywa się to za pośrednictwem ustawień kompilatora, ale definicję można również umieścić w nx_secure_tls.h. Po zdefiniowanym makrze obsługa szyfrowania PSK zostanie skompilowana w aplikacji NetX Secure TLS.

Po włączeniu obsługi zestawu PSK można następnie skonfigurować zestawy PSK dla aplikacji przy użyciu interfejsu API TLS. Każdy klucz psk będzie wymagał wartości klucza psk (rzeczywistego klucza tajnego — ta wartość jest bezpieczna), wartości "tożsamości" używanej do identyfikowania określonego klucza psk oraz "wskazówki dotyczącej tożsamości", która jest używana przez serwer TLS do wybrania określonej wartości klucza psk.

Sam kod PSK może być dowolną wartością binarną, ponieważ nigdy nie jest wysyłany za pośrednictwem połączenia sieciowego. Może to być dowolna wartość o długości do 64 bajtów.

Tożsamość i wskazówka muszą być drukowalnymi ciągami znaków sformatowanym przy użyciu formatu UTF-8. Wartości tożsamości i wskazówek mogą mieć dowolną długość do 128 bajtów.

Tożsamość i kluczy psk tworzą unikatową parę, która jest ładowana na każde urządzenie w sieci, które muszą komunikować się ze sobą.

"Wskazówka" jest używana głównie do definiowania profilów określonych aplikacji w celu grupowania psk według funkcji lub usługi. Te wartości należy uzgodnić z wyprzedzeniem i są zależne od aplikacji. Na przykład aplikacja serwera wiersza polecenia OpenSSL (z włączonym zestawem PSK) używa domyślnego ciągu "Client_identity", który musi zostać dostarczony przez klienta TLS, aby można było kontynuować uściślanie TLS.

Aby uzyskać więcej informacji na temat psk, zobacz NetX Secure API reference for the following services: nx_secure_tls_client_psk_set, nx_secure_tls_psk_add(

## <a name="importing-x509-certificates-into-netx-secure"></a>Importowanie certyfikatów X.509 do usługi NetX Secure

Certyfikaty cyfrowe są wymagane w przypadku większości połączeń TLS w Internecie. Certyfikaty zapewniają metodę uwierzytelniania wcześniej nieznanych hostów za pośrednictwem Internetu  przy użyciu zaufanych pośredników, zwykle nazywanych urzędami certyfikacji lub urzędami certyfikacji. Aby połączyć urządzenie NetX Secure z komercyjną usługą w chmurze (taką jak Amazon Web Services), należy zaimportować certyfikaty do aplikacji przez załadowanie ich na urządzenie.

Oprócz certyfikatów czasami potrzebny jest również klucz *prywatny* skojarzony z certyfikatem. W niektórych aplikacjach (takich jak klient TLS, gdy uwierzytelnianie certyfikatu klienta nie jest używane) sam certyfikat będzie wystarczający, ale jeśli certyfikat jest używany do identyfikowania urządzenia, potrzebny będzie klucz prywatny. Klucze prywatne są zwykle generowane podczas tworzenia certyfikatu i są przechowywane w oddzielnym pliku, często zaszyfrowanym przy użyciu hasła.

### <a name="certificate-types"></a>Typy certyfikatów

Certyfikaty cyfrowe są zwykle używane do identyfikowania jednostek w sieci, ale w zależności od ich aplikacji będą mieć nieco inne właściwości.

### <a name="local-certificates"></a>Certyfikaty lokalne

Na potrzeby tej dokumentacji będziemy nazywać "certyfikatami lokalnymi" jako certyfikaty, które zapewniają tożsamość dla naszego urządzenia lokalnego (inną możliwą nazwą może być "certyfikat urządzenia"). Te certyfikaty zostaną dostarczone do hosta zdalnego, gdy host zdalny chce uwierzytelnić urządzenie lokalne.

### <a name="remote-certificates"></a>Certyfikaty zdalne

W tej dokumentacji "certyfikaty zdalne" odnoszą się do certyfikatów dostarczonych przez hosta zdalnego podczas procesu ugody TLS, jeśli ma to zastosowanie. Należy przydzielić miejsce dla tych certyfikatów. W przypadku, gdy rozwiązanie NetX Secure nie będzie w stanie ich przesłonić i ukończyć procesu uściślniania TLS.

### <a name="signing-certificates"></a>Podpisywanie certyfikatów

"Certyfikat podpisywania" służy do cyfrowego podpisywania innych certyfikatów lub danych na potrzeby uwierzytelniania. Te certyfikaty mogą być certyfikatami pośredniczącymi lub głównymi w ramach infrastruktury kluczy publicznych (PKI) i zazwyczaj nie są używane do identyfikowania poszczególnych urządzeń lub hostów.

### <a name="root-ca-certificates"></a>Certyfikaty głównego urzędu certyfikacji

"Certyfikaty głównego urzędu certyfikacji" to certyfikaty podpisywania, które stanowią podstawę usługi PKI i mają podpis własny, a nie przez inny certyfikat podpisywania. Co najmniej jeden certyfikat głównego urzędu certyfikacji jest zwykle wymagany, aby klient TLS weryfikował serwery zdalne.

### <a name="certificate-formats"></a>Formaty certyfikatów

Certyfikaty cyfrowe to po prostu pliki zawierające dane ustrukturyzowane zakodowane przy użyciu składni ASN.1. Istnieją jednak różne formaty, w których mogą być przechowywane certyfikaty. Ważne jest, aby przed załadowaniem certyfikatu do aplikacji NetX Secure mieć odpowiedni format.

Najczęściej spotykane formaty certyfikatów to DER i PEM. DER *(dla Distinguished Encoding Rules*, format ASN.1) to format binarny używany przez TLS podczas przeprowadzania początkowego handshake. PEM (od *Privacy Enhanced Mail*) to zakodowana w formacie BASE-64 wersja formatu DER, która jest odpowiednia do wysyłania wiadomości e-mail lub wysyłania za pośrednictwem protokołu HTTP w Internecie. Różni dostawcy używają różnych rozszerzeń nazw plików dla certyfikatów, takich jak "pem" lub "crt" dla certyfikatów PEM, i ".der" dla certyfikatów DER. Jeśli masz certyfikat i nie jest jasne, jaki format jest używany, otwarcie pliku w edytorze tekstów umożliwi określenie typu, ponieważ pliki DER są kodowane binarnie, a pliki PEM są zwykłym tekstem ASCII, który zaczyna się od nagłówka "-----BEGIN CERTIFICATE-----".

Program NetX Secure wymaga, aby certyfikat był w binarnym formacie DER, dlatego przed zaimportowanym certyfikatem należy przekonwertować go na format DER. Można to zrobić za pomocą łatwo dostępnych narzędzi, takich jak OpenSSL.

Jeśli potrzebujesz klucza prywatnego dla aplikacji, plik klucza zostanie zakodowany przy użyciu PEM lub DER w określonym formacie (PKCS#1 dla RSA, RFC 5915 for ECC). Plik klucza prywatnego należy przekonwertować na der przed zaimportowane.

Następujące polecenia OpenSSL są podane jako przykład konwertowania certyfikatów i plików kluczy RSA do formatu DER wymaganego przez netX Secure (ECC jest podobny — zapoznaj się z dokumentacją OpenSSL).

```C
openssl x509 -inform PEM -in <certificate> -outform DER -out cert.der
openssl x509 -inform PEM -in <root CA cert> -outform DER -out CA_cert.der
openssl rsa -inform PEM -in <private key> -outform DER -out private.key
```
### <a name="private-keys-and-certificates"></a>Klucze prywatne i certyfikaty

W przypadku certyfikatów, które identyfikują urządzenie, wraz z certyfikatem należy załadować skojarzony klucz prywatny. Klucz prywatny (który może być używany przez jeden z algorytmów kluczy publicznych, takich jak RSA, Diffie-Hellman lub Elliptic-Curve Kryptografia) jest używany przez serwer TLS do odszyfrowywania przychodzącego materiału klucza ("klucza wstępnego") od klienta TLS, a tym samym uwierzytelniania się dla klienta. W przypadku klienta TLS, jeśli zostanie podany certyfikat tożsamości (certyfikat ze skojarzonym kluczem prywatnym) i serwer zażąda certyfikatu klienta, klucz prywatny jest używany do uwierzytelniania klienta — w przypadku RSA klient szyfruje token przy użyciu klucza prywatnego, który serwer następnie odszyfrowuje przy użyciu klucza publicznego klienta.  w certyfikacie klienta (uwierzytelnianie Diffie'ego-Hellmana i ECC odbywa się w podobny sposób, ale szczegóły są nieco inne).

W środowisku NetX Secure usługa *nx_secure_x509_certificate_initialize* służy do inicjowania certyfikatu X.509 (zobacz sekcję "Ładowanie certyfikatów na urządzeniu", aby uzyskać więcej informacji) i opcjonalnie kojarzenie klucza prywatnego z tym certyfikatem.

Jeśli zostanie podany klucz prywatny, certyfikat zostanie oznaczony jako certyfikat "tożsamości" używany do identyfikowania urządzenia. Klucz jest przekazywany jako ciągły binarny obiekt blob i długość ze skojarzonym typem klucza. Typ klucza zależy od typu klucza (np. RSA, ECC itp.) i formatu (np. PKCS#1 DER). Jeśli klucz nie zostanie podany, wartość NX_SECURE_X509_KEY_TYPE_NONE (wartość 0x0) może zostać przekazana, aby wskazać, że żaden klucz nie jest dostarczany (długość 0 i wskaźnik NX_NULL dla parametru danych osiągnie ten sam efekt).

W poniższej tabeli przedstawiono typy kluczy znane z netx secure i skojarzony identyfikator typu, który ma zostać przekazany do *nx_secure_x509_certificate_initialize*. Dodatkowe typy kluczy będą dodawane w przypadku dodania większej liczby algorytmów szyfrowania do usługi NetX Secure.

| Identyfikator                              | Algorytm | Format   | Encoding | Wartość |
| --------------------------------------- | --------- | -------- | -------- | ----- |
| NX_SECURE_X509_KEY_TYPE_NONE            | Brak      | NIE DOTYCZY      | NIE DOTYCZY      | 0x0   |
| NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER   | RSA       | PKCS#1   | Der      | 0x1   |
| NX_SECURE_X509_KEY_TYPE_EC_DER          | Ecdsa     | RFC 5915 | Der      | 0x2   |

### <a name="user-defined-private-key-types"></a>Typy kluczy prywatnych zdefiniowanych przez użytkownika

Wartości identyfikatorów typu klucza dla usługi *nx_secure_x509_certificate_initialize* określają akcje podejmowane po posłudze klucza prywatnego. W przypadku znanych typów wartości znajdują się w zakresie od 0x0000 0000 do 0x0000 FFFF (dolne 16 bitów 32-bitowej liczby całkowitej bez znaku). W przypadku platform z niestandardowymi typami kluczy<sup>17</sup> (tak jak w przypadku niektórych sprzętowych aparatów szyfrowania) jako typ klucza może zostać przekazany zdefiniowany przez użytkownika typ klucza z zakresu 0x0000 1000-0xFFFF FFFF (16 bitów z najlepszymi wartościami niezerowymi). Jeśli ustawiono dowolny z 16 najważniejszych bitów typu klucza, dane klucza prywatnego są przekazywane bezpośrednio do odpowiedniej procedury kryptograficznej (np. RSA) podanej w tabeli szyfrowania TLS. Typy kluczy zdefiniowane przez użytkownika nie są analizowane ani przetwarzane w inny sposób przed ich przekazem do procedury kryptograficznych. Ponadto typ klucza zdefiniowanego przez użytkownika zostanie również przekazany do procedury kryptograficznej, dzięki czemu na tym poziomie będzie można obsłużyć dowolne odpowiednie przetwarzanie.

Należy pamiętać, że typy kluczy zdefiniowane przez użytkownika są zwykle używane dla określonych platform sprzętowych, które wykorzystują niestandardowe (potencjalnie zaszyfrowane) dane klucza. Ogólnie oznacza to, że kluczowe dane są generowane lub kodowane przy użyciu mechanizmu specyficznego dla tego dostawcy sprzętu (lub w przypadku standardu, takiego jak PKCS#11, określony standard). Aby uzyskać więcej informacji, zapoznaj się z dokumentacją platformy sprzętowej.

17. Typy kluczy zdefiniowane przez użytkownika wymagają odpowiedniej niestandardowej procedury kryptograficznej do obsługi niestandardowego formatu klucza. Procedura kryptograficzna musi mieć pasujący algorytm (np. RSA) i być przekazywana do TLS w tabeli ciphersuite. 

### <a name="loading-certificates-onto-your-device"></a>Ładowanie certyfikatów na urządzenie

Każda metoda ładowania pliku na urządzenie będzie wystarczająca do zaimportowania certyfikatów.

Najprostszą metodą ładowania certyfikatu jest przekonwertowanie danych binarnych zakodowanych w formacie DER na tablicę języka C i skompilowanie ich do aplikacji jako stałej. Można to łatwo zrobić za pomocą narzędzi, takich jak "xxd" w systemie Linux (z opcją "-i").

Alternatywnie możesz załadować certyfikat do systemu plików flash lub innych opcji magazynu, o ile możesz przekazać wskaźnik do danych certyfikatu do bezpiecznego interfejsu API NetX.

### <a name="certificate-files-needed-for-netx-secure"></a>Pliki certyfikatów wymagane dla usługi NetX Secure

Pliki certyfikatów, które należy zaimportować, zależą od aplikacji. Ogólnie rzecz biorąc, serwery TLS wymagają certyfikatu w celu zidentyfikowania  urządzenia, a klienci TLS wymagają co najmniej jednego zaufanego certyfikatu do uwierzytelniania serwerów zdalnych. W poniższej tabeli przedstawiono certyfikaty wymagane dla niektórych różnych aplikacji TLS.

| **Funkcje/opcje TLS**                     | **Wymagane certyfikaty/klucze (minimum)**              |
| ------------------------------------------------- | --------------------------------------------------- |
| Klient TLS                                        | Certyfikat głównego urzędu certyfikacji                                 |
| Serwer TLS                                        | Certyfikat lokalny, klucz prywatny dla tego certyfikatu |
| Serwer TLS z uwierzytelnianiem certyfikatu klienta | Certyfikat lokalny, klucz prywatny, główny urząd certyfikacji             |
| Klient TLS z uwierzytelnianiem certyfikatu klienta | Certyfikat lokalny, klucz prywatny, główny urząd certyfikacji             |
| Klient lub serwer TLS tylko z kluczami wstępnymi    | Brak (używany jest certyfikat PSK zamiast certyfikatów)             |

Odpowiednie usługi do ładowania certyfikatów są następujące:

| **Nazwa interfejsu API**                                   | **Cel**                                            |
| ---------------------------------------------- |------------------------------------------------------- |
| nx_secure_x509_certificate_initialize      | Musi być wywoływana, aby wszystkie certyfikaty wypełniały strukturę NX_SECURE_X509_CERT danymi certyfikatu i kluczem prywatnym. |
| nx_secure_tls_local_certificate_add       | Dodaj certyfikat lokalny do sesji TLS, aby zidentyfikować urządzenie.                                                                |
| nx_secure_tls_local_certificate_remove    | Usuń certyfikat lokalny z sesji TLS.                                                                                   |
| nx_secure_tls_remote_certificate_allocate | Przydzielanie miejsca dla certyfikatu zdalnego (nazywanego niezainicjowany NX_SECURE_X509_CERT).                                   |
| nx_secure_tls_trusted_certificate_add     | Dodaj certyfikat do sesji TLS jako zaufany certyfikat do uwierzytelniania hostów zdalnych.                                     |
| nx_secure_tls_trusted_certificate_remove  | Usuń zaufany certyfikat z sesji TLS.                                                                                 |

### <a name="working-with-aws-iot-certificates"></a>Praca z certyfikatami IoT usług AWS

W interfejsie Amazon Web Services IoT wybierz pozycję "Zabezpieczenia" z menu paska bocznego, a następnie wybierz pozycję "Certyfikaty". Utwórz nowy certyfikat i postępuj zgodnie z instrukcjami, aby pobrać nowy certyfikat urządzenia.

Po pobraniu certyfikatów należy przekonwertować je na format DER przy użyciu programu OpenSSL lub podobnego narzędzia.

UWAGA: Usługi AWS również udostępnią plik klucza publicznego. Klucz publiczny jest zawarty w certyfikacie urządzenia lokalnego, więc nie trzeba go importować do aplikacji.

Oto przykładowe polecenia służące do konwertowania certyfikatu urządzenia lokalnego i jego klucza prywatnego na format DER do użycia z platformą NetX Secure:

```C
openssl x509 -inform PEM -in <certificate> -outform DER -out cert.der
openssl x509 -inform PEM -in <root CA cert> -outform DER -out CA_cert.der
openssl rsa -inform PEM -in <private key> -outform DER -out private.key
```
Przekonwertowane pliki można zaimportować do aplikacji, zgodnie z powyższymi instrukcjami.

## <a name="x509-certificate-validation-in-netx-secure"></a>Weryfikacja certyfikatu X.509 w programie NetX Secure 

W przypadku korzystania z certyfikatów TLS z certyfikatami X.509 w celu identyfikacji i weryfikacji hosta ważne jest zrozumienie, jak te certyfikaty są faktycznie weryfikowane. Mimo że specyfikacja TLS nie zawiera szczegółowych instrukcji dotyczących weryfikowania certyfikatu, odnosi się do specyfikacji X.509 (RFC 5280). Ogólnie oczekuje się, że usługa TLS wykona co najmniej podstawową weryfikację certyfikatów przychodzących (certyfikatów dostarczonych przez hosta zdalnego podczas procesu uściślniania TLS), a zabezpieczenia NetX Secure TLS nie różnią się.

### <a name="basic-x509-validation"></a>Podstawowa walidacja X.509

W przypadku dowolnego certyfikatu przychodzącego technologia NetX Secure TLS wykona podstawową weryfikację ścieżki X.509. Proces ten obejmuje sprawdzenie podpisu cyfrowego każdego certyfikatu względem certyfikatu wystawcy, który może zostać dostarczony przez hosta zdalnego lub umieszczony w magazynie zaufanych certyfikatów (zobacz sekcję "Importowanie certyfikatów X.509 do rozwiązania NetX Secure", aby uzyskać więcej informacji na temat importowania zaufanych certyfikatów). Proces weryfikacji jest powtarzany cyklicznie w certyfikatach wystawców do momentu, gdy zostanie osiągnięty zaufany certyfikat lub łańcuch zakończy się (z certyfikatem z podpisem własnym lub brakującym certyfikatem wystawcy). Jeśli zostanie osiągnięty zaufany certyfikat, certyfikat zostanie zweryfikowany, w przeciwnym razie zostanie odrzucony. Ponadto na każdym etapie procesu weryfikacji data wygaśnięcia każdego certyfikatu jest sprawdzana względem czasu podanego przez funkcję znacznika czasu aplikacji (aby uzyskać więcej informacji, zobacz "nx_secure_tls_session_time_function_set" usługi).

Specyfikacja X.509 udostępnia również algorytm obsługi "zasad", czyli identyfikatory obecne w rozszerzeniu X.509, które można sprawdzić podczas sprawdzania poprawności ścieżki. Obecnie netX Secure traktuje certyfikaty X.509 tak, jakby zdefiniowano opcję "anyPolicy", czyli wszystkie zasady są dopuszczalne i opcjonalne sprawdzanie zasad nie jest wykonywane. Implementacja NetX Secure X.509 może zostać rozszerzona o tę funkcję w przyszłej wersji. Na razie rozszerzenie zasad można uzyskać z certyfikatu przy użyciu interfejsu API *nx_secure_x509_extension_find* API.

Po zakończeniu weryfikacji ścieżki podstawowej TLS wywoła wywołanie zwrotne weryfikacji certyfikatu dostarczone przez aplikację przy użyciu interfejsu API *nx_secure_tls_session_certificate_callback_set* API. Jeśli nie zostanie podane wywołanie zwrotne, certyfikat jest uznawany za zaufany po pomyślnej weryfikacji ścieżki. Jeśli zostanie podane wywołanie zwrotne, wywołanie zwrotne wykona dodatkową weryfikację certyfikatu wymaganą przez aplikację. Wartość zwracana przez wywołanie zwrotne służy do określenia, czy kontynuować ugodę TLS, czy przerwać ugodę z powodu błędu walidacji.

Wywołanie zwrotne jest wywoływane ze wskaźnikiem do odpowiedniej sesji TLS i NX_SECURE_X509_CERT do certyfikatu, który ma zostać zweryfikowany. Między sesją TLS a certyfikatem aplikacja ma wszystkie dane, których potrzebuje od usługi TLS w celu przeprowadzenia dodatkowych kontroli weryfikacyjnych.

Aby ułatwić dodatkową weryfikację, usługa NetX Secure udostępnia procedury X.509 dla niektórych typowych operacji weryfikacji, w tym weryfikacji DNS i sprawdzania listy odwołania certyfikatów. Wszystkie te procedury są odpowiednie do użycia w ramach wywołania zwrotnego weryfikacji certyfikatu, ale mogą być również używane do sprawdzania off-line certyfikatów X.509.

W poniższej tabeli przedstawiono podsumowanie dostępnych funkcji pomocnika dla przetwarzania certyfikatów X.509. Bardziej szczegółowe wyjaśnienia dotyczące operacji można znaleźć w poniższych sekcjach oraz w sekcji Dokumentacja interfejsu API w rozdziale 4.  
  
Opis bezpiecznych usług NetX zawiera dodatkowe szczegóły dotyczące określonych procedur.

| **Nazwa interfejsu API**                             | **Opis**                               |
| ---------------------------------------- | -------------------------------------- |
| nx_secure_x509_common_name_dns_check               | Sprawdź nazwę pospolitą podmiotu X.509 i nazwę SubjectAltName względem oczekiwanej nazwy DNS |
| nx_secure_x509_crl_revocation_check                 | Sprawdzanie odwołania certyfikatu na liście odwołania certyfikatów X.509 (CRL)       |
| nx_secure_x509_extended_key_usage_extension_parse | Analizowanie i znajdowanie określonego rozszerzonego OID użycia klucza w certyfikacie                   |
| nx_secure_x509_key_usage_extension_parse           | Analizowanie i zwracanie pola bitowego użycia klucza w certyfikacie                            |
| nx_secure_x509_extension_find                        | Znajdź i zwróć nieprzetworzone dane ASN.1 zakodowane w formacie DER dla określonego rozszerzenia.            |

Funkcje pomocnika X.509 do użycia w wywołaniu zwrotym weryfikacji certyfikatu

### <a name="x509-extensions"></a>Rozszerzenia X.509

Specyfikacja X.509 opisuje szereg "rozszerzeń", których można użyć do dostarczania dodatkowych informacji, które mogą być używane podczas weryfikacji certyfikatów. W większości przypadków te rozszerzenia są opcjonalne i nie są wymagane do bezpiecznej weryfikacji certyfikatu cyfrowego względem zaufanego certyfikatu głównego. Jednak program NetX Secure obsługuje niektóre podstawowe rozszerzenia. Obsługa dodatkowych rozszerzeń może zostać dodana w przyszłych wersjach.

Obecnie obsługiwane rozszerzenia są wymienione w poniższej tabeli:

| Nazwa rozszerzenia           | Opis                                                                   | Odpowiedni interfejs API                                             |
| ------------------------ | ----------------------------------------------------------------------------- | -------------------------------------------------------- |
| Użycie klucza                | Zapewnia dopuszczalne zastosowania klucza publicznego certyfikatu w bitfield         | nx_secure_x509_key_usage_extension_parse           |
| Rozszerzone użycie klucza       | Zapewnia dodatkowe dopuszczalne zastosowania klucza publicznego certyfikatu przy użyciu identyfikatorów ID | nx_secure_x509_extended_key_usage_extension_parse |
| Alternatywna nazwa podmiotu | Udostępnia alternatywne nazwy DNS, które są również reprezentowane przez certyfikat   | nx_secure_x509_common_name_dns_check               |

### <a name="unsupported-x509-extensions"></a>Nieobsługiwane rozszerzenia X.509

Implemacja X.509 netX Secure zapewnia usługę do wyodrębniania nieobsługiwanych rozszerzeń, a *także:* nx_secure_x509_extension_find . Ten interfejs API jest przeznaczony dla zaawansowanych użytkowników, ponieważ wymaga znajomości kodowania ASN.1 w formacie DER w celu analizowania zwracanych danych. Była używana wewnętrznie do wyodrębniania obsługiwanych rozszerzeń, ale jest dostarczana dla wygody podczas opracowywania dostosowanej obsługi rozszerzeń X.509.

Aby użyć nx_secure_x509_extension_find, przekazywany jest NX_SECURE_X509_EXTENSION wraz z certyfikatem i identyfikatorem rozszerzenia, który jest całkowitą reprezentacją ciągu identyfikatora OID o zmiennej długości dla znanego typu rozszerzenia. Pełna lista obsługiwanych identyfikatorów JID dla rozszerzeń X.509 znajduje się w wykazie interfejsów API dla nx_secure_x509_extension_find na stronie 178.

Struktura NX_SECURE_X509_EXTENSION jest zdefiniowana w następujący sposób:

```C
typedef struct NX_SECURE_X509_EXTENSION_STRUCT
{
    /* Identifier (maps to OID) for this extension. */
    USHORT nx_secure_x509_extension_id;

    /* Critical flag - boolean value. */
    USHORT nx_secure_x509_extension_critical;

    /* Pointer to DER-encoded extension data. */
    const UCHAR *nx_secure_x509_extension_data;
    ULONG        nx_secure_x509_extension_data_length;
} NX_SECURE_X509_EXTENSION;
```
Po pomyślnym powrocie usługi struktura zostanie wypełniona odpowiednimi danymi z certyfikatu. Pole nx_secure_x509_extension_id jest zwykle używane do celów wewnętrznych, ale zostanie wypełnione odpowiednią reprezentacją liczb całkowitych OID. Pole nx_secure_x509_extension_critical uwidacznia wartość flagi rozszerzenia krytycznego X.509 (wartość logiczna). Pola nx_secure_x509_extension_data i nx_secure_x509_extension_data_length zawierają wskaźnik odpowiednio do danych ASN.1 zakodowanych w formacie DER oraz długość tych danych.

Rzeczywista analizowanie danych rozszerzenia ASN.1 wykracza poza zakres tego dokumentu, ale jeśli masz dostęp do źródła NetX Secure TLS, możesz zobaczyć, jak analizy są wykonywane wszędzie tam, gdzie nx_secure_x509_extension_find jest wywoływana dla obsługiwanych rozszerzeń.

### <a name="x509-dns-validation"></a>Weryfikacja dns X.509

Wspólna operacja weryfikacji certyfikatu w ramach TLS polega na sprawdzeniu nazwy domeny Top-Level (TLD) hosta zdalnego względem certyfikatu X.509 dostarczonego przez tego hosta podczas procesu ugody TLS. Ta operacja pomaga upewnić się, że certyfikat rzeczywiście odpowiada serwerowi hosta, który go podał, przy założeniu, że odnośnik DNS może być zaufany. W zabezpieczeniach NetX TLS ta funkcja jest zapewniana przez usługę **nx_secure_x509_common_name_dns_check**, która przyjmuje certyfikat i ciąg zawierający część TLD adresu URL używanego do uzyskiwania dostępu do hosta. TLD jest porównywany z polem Nazwa pospolita certyfikatu i jeśli jest on NX_SUCCESS zwracany. Jeśli nazwa pospolita nie jest dopasowana, procedura sprawdzi również istnienie rozszerzenia certyfikatu X.509 *subjectAltName.* Jeśli subjectAltName jest obecny, wszystkie wpisy DNSName w rozszerzeniu są również sprawdzane względem podanego TLD. Ponownie, jeśli jakiekolwiek dopasowanie, NX_SUCCESS zwracane. Jeśli dopasowanie nie zostanie znalezione, zwracany jest błąd odpowiedni do powrotu z wywołania zwrotnego weryfikacji certyfikatu.

### <a name="x509-key-usage-and-extended-key-usage-extensions"></a>X.509 Użycie klucza i rozszerzone rozszerzenia użycia klucza

Rozszerzenia X.509 Key Usage (Użycie klucza X.509) i Extended Key Usage (Rozszerzone użycie klucza) zawierają informacje na temat sposobu używania klucza publicznego certyfikatu podczas uwierzytelniania tego certyfikatu. Użycie klucza jest dostarczane przez wystawcę certyfikatu, gdy certyfikat jest podpisany i wystawiony. Użycie klucza może być używane przez hosta TLS do sprawdzania, czy certyfikat jest autoryzowany do uwierzytelniania zdalnego hosta TLS i wykonywania innych operacji.

Rozszerzenie Użycie klucza składa się z prostego pola bitowego, w którym każdy bit reprezentuje określone użycie klucza. Pełna lista tych wartości znajduje się w odwołaniu do interfejsu API dla *nx_secure_x509_key_usage_extension_parse* na stronie 183. Bardziej szczegółowy opis bitów użycia klucza i ich znaczenia można znaleźć w dokumencie RFC 5280 w sekcji 4.2.1.3.

Rozszerzenie Rozszerzone użycie klucza, takie jak rozszerzenie Użycie klucza, udostępnia dopuszczalne informacje o użyciu klucza. Jednak w celu obsługi dowolnego użycia rozszerzenie Rozszerzone użycie klucza wykorzystuje identyfikatory ID zamiast pola bitowego. Podczas analizowania rozszerzenia rozszerzonego użycia klucza w programie NetX Secure X.509 aplikacja dostarcza liczbę całkowitą reprezentującą OID — usługa *nx_secure_x509_extended_key_usage_extension_parse* zwróci wtedy, czy ten OID jest obecny. Pełna lista obsługiwanych identyfikatorów ID dla rozszerzonego użycia klucza znajduje się w wykazie interfejsów API dla nx_secure_x509_extended_key_usage_extension_parse *na* stronie 175. Bardziej szczegółowy opis identyfikatorów ID i ich znaczenia można znaleźć w dokumencie RFC 5280 w sekcji 4.2.1.12.

### <a name="x509-crl-revocation-status-checking"></a>Sprawdzanie stanu odwołania listy CRL X.509

X.509 zapewnia mechanizm  o nazwie lista odwołania certyfikatów (CRL), który umożliwia urząd podpisywania certyfikatów cyfrowych odwołać ważność certyfikatów, które został podpisany. Każda aplikacja, która musi zweryfikować certyfikaty z urzędu podpisywania, może uzyskać listy CRL i porównać wszystkie certyfikaty podpisane przez ten urząd (wystawcę) z listą CRL, aby sprawdzić, czy ich stan został odwołany z jakiegoś powodu (na przykład z naruszonego klucza prywatnego). W ten sposób aplikacja może uniknąć używania potencjalnie niebezpiecznych certyfikatów, które przechodzą inne testy weryfikacji certyfikatu.

Uzyskiwanie listy CRL jest wykonywane przez aplikację przez pobranie listy zakodowanej w formacie DER ze wstępnie zdefiniowanego serwera lub w inny sposób. Rzeczywista konfiguracja różni się w zależności od wystawcy i wystawcy, więc netX Secure nie zapewnia mechanizmu uzyskiwania list CRL, ale zapewnia procedurę sprawdzania certyfikatu względem listy CRL, nx_secure_x509_crl_revocation_check **.**

Interfejs API pobiera do sprawdzenia adres CRL zakodowany w formacie DER, magazyn certyfikatów (taki jak ten w sesji TLS) oraz certyfikat do sprawdzenia. Procedura najpierw weryfikuje samą listę CRL względem zaufanego magazynu (część magazynu certyfikatów dostarczonego przez aplikację). Jest to ważne, aby chronić przed fałszywymi listami CRL używanymi do ataków typu "odmowa usługi" i ustalić, że listy CRL pochodzi faktycznie od odpowiedniego wystawcy. Po weryfikacji listy CRL jest sprawdzany wystawca — jeśli wystawca listy CRL nie pasuje do wystawcy certyfikatu, to nie jest prawidłowa dla tego certyfikatu i zwracany jest błąd. To aplikacja decyduje, czy w tym momencie można kontynuować uściślnienie TLS. Jeśli wystawcy są zgodne, a następnie listy CRL jest wyszukiwany numer seryjny weryfikowanego certyfikatu. Jeśli numer seryjny znajduje się na liście, zwracany jest błąd wskazujący, że certyfikat został odwołany. Jeśli dopasowanie nie zostanie znalezione, NX_SUCCESS zostanie zwrócona.

## <a name="client-certificate-authentication-in-netx-secure-tls"></a>Uwierzytelnianie certyfikatu klienta w zabezpieczonych zabezpieczeniach TLS netx

W przypadku korzystania z uwierzytelniania certyfikatu X.509 protokół TLS wymaga, aby wystąpienie serwera TLS dostarczało certyfikat do identyfikacji, ale domyślnie wystąpienie klienta TLS nie musi dostarczać certyfikatu na potrzeby uwierzytelniania przy użyciu innej formy uwierzytelniania (np. kombinacji nazwy użytkownika/hasła). Jest to najbardziej typowe użycie TLS w Internecie dla witryn internetowych. Na przykład witryna sklepu detalicznego online musi udowodnić potencjalnego klientowi za pomocą przeglądarki internetowej, że serwer jest legalny, ale użytkownik użyje nazwy logowania/hasła, aby uzyskać dostęp do określonego konta.

Jednak przypadek domyślny nie zawsze jest pożądany, więc usługa TLS opcjonalnie umożliwia wystąpieniu serwera TLS zażądanie certyfikatu od klienta zdalnego. Po włączeniu tej funkcji serwer TLS wyśle komunikat CertificateRequest do klienta TLS podczas procesu praktycznego. Klient musi odpowiedzieć własnym certyfikatem i komunikatem CertificateVerify zawierającym token kryptograficzny potwierdzający, że klient jest właścicielem pasującego klucza prywatnego skojarzonego z tym certyfikatem. Jeśli weryfikacja nie powiedzie się lub certyfikat nie jest połączony z zaufanym certyfikatem na serwerze, uściślinie TLS zakończy się niepowodzeniem.

Istnieją dwa oddzielne przypadki uwierzytelniania certyfikatu klienta w ULI — w poniższych sekcjach omykamy oba przypadki.

### <a name="client-certificate-authentication-for-tls-clients"></a>Uwierzytelnianie certyfikatu klienta dla klientów protokołu TLS

Klient protokołu TLS może próbować nawiązaniu połączenia z serwerem, który żąda certyfikatu w celu uwierzytelnienia klienta. W takim przypadku klient musi udostępnić certyfikat serwerowi i sprawdzić, czy jest właścicielem zgodnego klucza prywatnego. W takim przypadku serwer zakończy uzgadnianie TLS.

W zabezpieczeniach NetX TLS nie ma specjalnej konfiguracji do obsługi tej funkcji, ale aplikacja musi udostępnić lokalny certyfikat identyfikacji dla wystąpienia klienta TLS przy użyciu usługi *nx_secure_tls_local_certificate_add* service. Jeśli aplikacja nie dostarcza żadnego certyfikatu, ale serwer zdalny korzysta z uwierzytelniania certyfikatu klienta i żąda certyfikatu, uściślić TLS nie powiedzie się. Certyfikat dostarczony do sesji TLS z *nx_secure_tls_local_certificate_add* musi zostać rozpoznany przez serwer zdalny, aby można było ukończyć ugodę TLS.

### <a name="client-certificate-authentication-for-tls-servers"></a>Uwierzytelnianie certyfikatu klienta dla serwerów TLS

Przypadek serwera TLS dla uwierzytelniania certyfikatu klienta jest nieco bardziej złożony niż przypadek klienta TLS, ponieważ funkcja jest opcjonalna. W takim przypadku serwer TLS musi zażądać certyfikatu od zdalnego klienta TLS, następnie przetworzyć komunikat CertificateVerify, aby sprawdzić, czy klient zdalny jest właścicielem pasującego klucza prywatnego, a następnie serwer musi sprawdzić, czy certyfikat dostarczony przez klienta może być śledzony do certyfikatu w lokalnym zaufanym magazynie certyfikatów.

W wystąpieniach serwera NetX Secure TLS uwierzytelnianie certyfikatu klienta jest kontrolowane przez <br>
klient *<span class="underline"> _</span> bezpiecznej sesji <span class="underline">_</span>TLS <span class="underline"> _</span> <span class="underline">_</span>nx <span class="underline"> _</span> zweryfikuj <span class="underline">_</span>włącz i*<br>
*Nx secure tls session client <span class="underline"> _</span> verify disable <span class="underline">_</span>services .NX <span class="underline"> _</span> Secure <span class="underline">_</span>TLS <span class="underline"> _</span> session <span class="underline">_</span>client verify disable* services (Weryfikacja wyłączenia usług).

Aby włączyć uwierzytelnianie certyfikatu klienta, aplikacja musi wywołać metodę<br>
*Nx <span class="underline"> _</span> <span class="underline">_ secure</span>tls <span class="underline"> _</span> session <span class="underline">_</span>client <span class="underline"> _</span> verify <span class="underline">_</span>enable* with the TLS Server session instance before calling *nx_secure_tls_session_start*. Należy pamiętać, że wywołanie tej usługi w sesji TLS używanej dla połączeń klienta TLS nie będzie mieć żadnego efektu.

Po włączeniu uwierzytelniania certyfikatu klienta serwer TLS zażąda certyfikatu od zdalnego klienta protokołu TLS podczas uwierzytelniania TLS. Na serwerze NetX Secure TLS certyfikat klienta jest sprawdzany w magazynie zaufanych certyfikatów utworzonych za pomocą dodawania zaufanego certyfikatu *nx <span class="underline"> _</span> secure_tls <span class="underline">_</span><span class="underline"> _</span> <span class="underline">_</span>* zgodnie z łańcuchem wystawców X.509. Klient zdalny musi udostępnić łańcuch, który łączy swój certyfikat tożsamości z certyfikatem w zaufanym magazynie. W przypadku, gdy uściśnięcie TLS nie powiedzie się. Ponadto jeśli przetwarzanie komunikatów CertificateVerify zakończy się niepowodzeniem, uściślanie TLS również zakończy się niepowodzeniem.

Metody podpisu używane dla metody CertificateVerify są stałe dla TLS w wersji 1.0 i TLS w wersji 1.1 i są określone przez serwer TLS w wersji 1.2. W przypadku standardu TLS 1.2 obsługiwane metody podpisu zazwyczaj są zgodne z odpowiednimi metodami dostarczonymi w tabeli metod kryptograficznych, ale zwykle algorytmem SHA-256 RSA (zobacz sekcję "Kryptografia w zabezpieczonych zabezpieczeniach TLS NetX", aby uzyskać więcej informacji na temat inicjowania szyfrowania TLS przy użyciu metod kryptograficznych).

## <a name="cryptography-in-netx-secure-tls"></a>Kryptografia w zabezpieczonych zabezpieczeniach TLS netx

Protokół TLS definiuje protokół, w którym kryptografia może służyć do zabezpieczania komunikacji sieciowej. W związku z tym pozostawia rzeczywistą kryptografię do dość szerokiego wykorzystania dla użytkowników TLS. Specyfikacja wymaga tylko zaimplementowania jednego szyfru — w przypadku protokołu TLS 1.2 ten klucz szyfrowania jest TLS_RSA_WITH_AES_128_CBC_SHA, co wskazuje na użycie algorytmu RSA do operacji na kluczach publicznych, szyfrowanie AES w trybie CBC z 128-bitowym kluczem szyfrowania sesji i algorytm SHA-1 dla skrótów uwierzytelniania wiadomości.

Ponieważ zabezpieczenia NetX Secure są zgodne z TLS 1.2, domyślnie umożliwiają stosowanie obowiązkowego szyfrowania TLS_RSA_WITH_AES_128_CBC_SHA, ale biorąc pod uwagę liczbę możliwych implementacji dla każdej z metod kryptograficznych ze względu na możliwości sprzętowe i inne zagadnienia, usługa NetX Secure udostępnia ogólny interfejs API kryptograficzny, który umożliwia użytkownikowi określenie metod kryptograficznych do użycia z szyfrowaniem TLS.

UWAGA: Ogólny mechanizm kryptograficznego interfejsu API umożliwia również użytkownikom implementowanie własnych szyfrów, ale jest to zalecane w przypadku zaawansowanych użytkowników, którzy znają mechanizmy szyfrowania I rozszerzenia TLS. Jeśli chcesz wspierać własne szyfry, skontaktuj się z przedstawicielem firmy Express Logic.

### <a name="cryptographic-methods"></a>Metody kryptograficzne

NetX Secure TLS implementuje DES, 3DES, AES, MD5, HMAC-MD5, SHA-1, HMAC-SHA1, SHA-256, HMAC-SHA256, RSA i ECC (wybrane krzywe) w oprogramowaniu ze sterownikami sprzętowymi dla niektórych platform sprzętowych. Aplikacja może korzystać z procedur kryptograficznych dostarczanych z aplikacją NetX Secure lub korzystać z procedur niestandardowych dostarczonych przez użytkownika końcowego lub osoby trzecie.

Ten *NX_CRYPTO_METHOD* jest blokiem sterującym przeznaczonym dla aplikacji do opisywania konkretnej implementacji algorytmu kryptograficznego, który ma być używany z bezpiecznym tlsem NetX. Dzięki NX_CRYPTO_METHOD *aplikacja* może łatwo zintegrować własne implementacje kryptograficzne z usługą NetX Secure. Struktura *NX_CRYPTO_METHOD* jest zadeklarowana jako:

```C
typedef struct NX_CRYPTO_METHOD_STRUCT
{
    /* Symbolic name of the algorithm. */
    USHORT nx_crypto_algorithm;

    /* Size of the key, in bits. */
    USHORT nx_crypto_key_size_in_bits;

    /* Size of the IV block, in bits, used for encryption. */
    USHORT nx_crypto_IV_size_in_bits;

    /* Size of the ICV block, in bits, used for authentication. */
    USHORT nx_crypto_ICV_size_in_bits;

    /* Size of the crypto block, in bytes. */
    ULONG nx_crypto_block_size_in_bytes;

    /* Size of the metadata area. */
    ULONG nx_crypto_metadata_size;

    /* nx_crypto_init function initializes the crypto method with the
        "secret key" or other state  information. The initialization 
        routine should return a handle to the caller.  This handle is 
        used in subsequent crypto operations to identify the session.  
        */

    UINT (*nx_crypto_init) (NX_CRYPTO_METHOD     *method,
                            UCHAR               *key, 
                            NX_CRYPTO_KEY_SIZE   key_size_in_bits,
                            VOID               **handler,
                            VOID                *crypto_metadata,
                            VOID                 crypto_metadata_size);

    /* NetX Secure calls the nx_crypto_cleanup routine when a TLS
       session is to be deleted (or updated).  Resources allocated 
       during the crypto operation should be released in this routine.  
       */
    UINT (*nx_crypto_cleanup) (VOID *handler);

    /* nx_crypto_operation is the actual crypto or hash operation. Note 
       that both input and output buffers are prepared by the caller. 
       For encryption or decryption operations, the crypto operation 
       routine uses the output buffer for encrypted or decrypted data. 
       For authentication operations, the authentication routine shall 
       use the output buffer for the digest. */
    UINT (*nx_crypto_operation)(UINT  op, 
                  VOID              *handler, 
                  NX_CRYPTO_METHOD  *method,
                  UCHAR             *key,
                  NX_CRYPTO_KEY_SIZE key_size_in_bits,
                  UCHAR             *input,
                  ULONG              input_length_in_byte,
                  UCHAR             *iv_ptr,
                  UCHAR             *output,
                  ULONG              output_length_in_byte,
                  VOID              *crypto_metadata,
                  VOID               crypto_metadata_size,
                  NX_PACKET*         packet_ptr,
                  VOID (*nx_crypto_hw_process_callback(NX_PACKET 
                                                       *packet_ptr, 
                                                        UINT status);
} NX_CRYPTO_METHOD;
```

Poniżej znajduje się opis każdego elementu w *NX_CRYPTO_METHOD* struktury:

- nx_crypto_algorithm: to pole identyfikuje algorytm opisany w  metodzie zmiennej Niektóre prawidłowe wartości bezpiecznego szyfrowania TLS netX są następujące (konkretne wartości można znaleźć w nx_crypto_const.h):
    
  - NX_CRYPTO_NONE    
  - NX_CRYPTO_ENCRYPTION_NULL    
  - NX_CRYPTO_ENCRYPTION_AES_CBC    
  - NX_CRYPTO_AUTHENTICATION_NONE    
  - TLS_HASH_SHA_1    
  - TLS_HASH_SHA_256    
  - TLS_HASH_MD5    
  - TLS_CIPHER_RSA    
  - TLS_CIPHER_NULL

- nx_crypto_key_size_in_bits: to pole określa rozmiar klucza tajnego używanego przez metodę .

- nx_crypto_IV_size_in_bits: to pole określa rozmiar wektora inicjalizacji (IV). Należy pamiętać, że w większości przypadków blok IV jest używany tylko dla algorytmów szyfrowania/odszyfrowywania. Algorytmy uwierzytelniania i weryfikacji rzadko używają tego pola.

- nx_crypto_ICV_size_in_bits: to pole określa rozmiar bloku Wartości sprawdzania integralności (ICV). UWAGA: Ten blok jest dla użycia protokołu IPsec i nie jest nieużywany w protokołu TLS. Aby uzyskać więcej informacji, zobacz NetX Duo IPsec.

- nx_crypto_block_size_in_bytes: to pole określa rozmiar bloku algorytmu kryptograficznego szyfrów blokowych w bajtach. W większości przypadków jest to używane przez procedury szyfrowania i rzadko przez procedury uwierzytelniania.

- nx_crypto_metadata_area_size: to pole określa rozmiar obszaru metadanych wymaganego przez tę metodę. Każda implementacja może wymagać określonej pamięci do przechowywania informacji o stanie lub do przechowywania danych pośrednich (takich jak materiał przekształceń kluczy) lub do użycia jako obszar podstawowy. Ilość miejsca wymaganego przez implementację jest określona w tym polu. Aplikacja zapewnia miejsce w pamięci podczas tworzenia sesji TLS. Za zarządzanie tym obszarem metadanych odpowiada funkcja kryptograficzna.

- nx_crypto_init: jest to funkcja inicjowania algorytmu kryptograficznego. W przypadku implementacji, która nie wymaga procedury inicjowania, dla tego pola można ustawić wartość NX_NULL. Typowym zastosowaniem funkcji inicjowania jest zainicjowanie wewnętrznej struktury danych dla algorytmu. Funkcja NetX Secure TLS będzie obsługiwać inicjowanie procedury kryptograficznych przez wywołanie tej funkcji wewnętrznie.

Prototyp funkcji inicjowania to:

```C
UINT crypto_init_function(NX_CRYPTO_METHOD *method, 
                          UCHAR *key, 
                          UINT  key_size_in_bits, 
                          VOID  **handle, 
                          VOID  *crypto_metadata_area, 
                          ULONG crypto_metadata_area_size);
```

  - metoda jest wskaźnikiem do bloku sterowania metody kryptograficznych.

  - klucz to ciąg klucza tajnego do przetwarzania pakietów danych.

  - key_size_in_bits definiuje rozmiar klucza tajnego, w bitach.

  - handle to element zdefiniowany w implementacji, który identyfikuje określoną sesję kryptograficznych. Wartość jest generowana przez procedurę inicjowania i jest przekazywana z powrotem do wywołującego. Kolejne operacje kryptograficzne lub procedury oczyszczania używają tego dojścia do identyfikowania sesji.

  - crypto_metadata jest wskaźnikiem do obszaru metadanych wymaganego przez implementację tego algorytmu. W przypadku algorytmów, które nie wymagają obszaru metadanych, to pole jest ustawione na wartość NX_NULL a procedura inicjowania nie może uzyskać dostępu do obszaru metadanych.

  - crypto_metadata_size określa rozmiar obszaru metadanych. W przypadku sA utworzonych bez obszaru metadanych to pole jest ustawione na zero, a procedura inicjowania nie może uzyskać dostępu do obszaru metadanych.

  - Ta procedura powinna *zwracać NX_SUCCESS,* jeśli proces inicjowania zostanie pomyślnie zainicjowany. Wywołujący traktuje każdą inną wartość zwracaną jako błąd.

- nx_crypto_cleanup: jest to procedura oczyszczania zdefiniowana dla implementacji algorytmu kryptograficznego. Jest on wywoływany po usunięciu lub ponownym uruchomieniu sesji TLS.

Prototyp funkcji oczyszczania to:

```C
UINT crypto_cleanup_function(VOID *handle);
```
- Funkcja handle jest przekazywana do funkcji cleanup przez wywołujący. Dojście jest zainicjowane przez procedurę inicjowania kryptograficznego i używane do identyfikowania stanu algorytmu kryptograficznego.

- Ta procedura powinna *zwracać NX_SUCCESS,* jeśli proces oczyszczania powiedzie się. Wywołujący traktuje każdą inną wartość zwracaną jako błąd.

- nx_crypto_operation: jest to procedura, która wykonuje rzeczywiste usługi szyfrowania, odszyfrowywania i uwierzytelniania. Prototyp funkcji procedury operacji jest:

```C
UINT crypto_operation_function(UINT   op,
          VOID  *handle,  
          NX_CRYPTO_METHOD* method,
          UCHAR *key,
          UCHAR  key_size_in_bits,
          UCHAR* input,
          ULONG  input_length_in_byte,
          UCHAR* iv_ptr,
          UCHAR* output,
          ULONG  output_length_in_byte,
          VOID *crypto_metadata,
          ULONG crypto_metadata_size,
          NX_PACKET *packet_ptr,
          VOID (*nx_crypto_hw_process_callback)(NX_PACKET 
                          *packet_ptr, UINT status));
```

- Operacja wskazuje typ operacji, który ta procedura ma wykonać. Prawidłowe wartości to:
    
    - NX_CRYPTO_ENCRYPT
    - NX_CRYPTO_DECRYPT
    - NX_CRYPTO_AUTHENTICATE
    - NX_CRYPTO_VERIFY

- Funkcja handle jest przekazywana do funkcji operation przez wywołujący. Jest on generowany przez procedurę inicjowania kryptografii.
- metoda wskazuje blok kontroli metody kryptograficznych
- Klucz wskazuje klucz tajny używany dla tej operacji
- key_size_in_bits to rozmiar klucza tajnego w bitach
- Input jest wskaźnikiem do początku komunikatu, który ma być obsługiwany.
- input_length_in_byte jest przekazywany przez wywołujący, aby wskazać rozmiar komunikatu, który ma być obsługiwany.
- iv_ptr jest konfigurowany przez element wywołujący, aby wskazać początek bloku IV. Należy pamiętać, że pamięć dla bloku IV jest dostarczana przez obiekt wywołujący. W przypadku szyfrowania funkcja operacji powinna zapisywać informacje o iv w tym bloku pamięci; w przypadku odszyfrowywania funkcja operacji powinna pobrać informacje o iv z tego bloku pamięci. Algorytmy operacji uwierzytelniania i weryfikacji zwykle nie używają wektora inicjowania.
- Element wywołujący skonfiguruje dane wyjściowe, aby wskazać bufor wyjściowy. Należy pamiętać, że pamięć buforu wyjściowego jest dostarczana przez obiekt wywołujący. W przypadku szyfrowania funkcja operation powinna zapisywać tekst szyfrowania w buforze wyjściowym; w przypadku odszyfrowywania operacja powinna zapisywać zaszyfrowany tekst (tekst wyczyszowany) do buforu wyjściowego; w przypadku uwierzytelniania wartość skrótu musi być zapisywana w buforze wyjściowym. W przypadku weryfikacji bufor wyjściowy jest używany do przechowywania informacji o skrótach.
- output_length_in_byte wskazuje rozmiar buforu wyjściowego
- crypto_metadata wskazuje obszar metadanych, który ma być używany przez tę operację kryptograficznych. Obszar metadanych kryptograficznych jest zwykle zainicjowany przez crypto_init_function.
- crypto_metadata_size wskazuje rozmiar obszaru metadanych.
- Ta procedura powinna *zwracać NX_SUCCESS,* jeśli proces operacji się powiedzie. Wywołujący traktuje każdą inną wartość zwracaną jako błąd.
- packet_ptr: pakiet zawierający przetwarzane dane. UWAGA: ten parametr jest nieużywany przez TLS i powinien być ustawiony na wartość NX_NULL.
- nx_crypto_hw_process_callback: funkcja wywołania zwrotnego dostarczana przez metodę szyfrowania. Jest to używane, jeśli funkcja kryptograficzna jest dostarczana przez sprzęt i wymaga procedury wywołania zwrotnego.

NetX Secure TLS zapewnia następujące metody szyfrowania:

- *AES*  
- *Rsa*  
- *Null*

NetX Secure TLS zapewnia następujące metody uwierzytelniania:

- *HMAC-MD5*  
- *HMAC-SHA1*  
- *HMAC-SHA256*

W poniższych przykładach pokazano, jak skonfigurować strukturę *NX_CRYPTO_METHOD* do używania metod szyfrowania i uwierzytelniania dostarczanych przez program NetX Duo IPsec.

***Aes:***

```C
/* AES-CBC 128. */
NX_CRYPTO_METHOD crypto_method_aes_cbc_128 = 
{
    /* AES crypto algorithm                             */
    NX_CRYPTO_ENCRYPTION_AES_CBC,                       

    /* Key size in bits. For AES-128 this value is 128  */
    NX_CRYPTO_AES_128_KEY_LEN_IN_BITS,              
   
    /* IV size in bits.  For AES-128 this value is 128  */
    NX_CRYPTO_AES_IV_LEN_IN_BITS,

    /* ICV size in bits, not used.                      */
    0,                                              

    /* Block size in bytes.  For AES this value is 16   */
    (NX_CRYPTO_AES_BLOCK_SIZE_IN_BITS >> 3),        

    /* Metadata size in bytes, for AES this value is 262*/
    sizeof(NX_CRYPTO_AES),              

    /* AES-CBC initialization routine.                  */
    _nx_secure_crypto_method_aes_init,               

    /* AES-CBC cleanup routine, not used.               */
    NX_NULL,                                        

    /* AES-CBC operation                                */
    _nx_secure_crypto_method_aes_operation           
};

/* RSA. */
NX_CRYPTO_METHOD crypto_method_rsa = 
{
    /* RSA crypto algorithm                             */
    TLS_CIPHER_RSA,                       

    /* Key size. RSA key sizes vary, so set to 0.         */
    0,              
   
    /* IV size in bits.  RSA does not use an IV.         */
    0,

    /* ICV size in bits, not used.                      */
    0,                                              

    /* Block size in bytes.  RSA does not have a block size. */
    0,        

    /* Metadata size in bytes, for RSA use the control block. */
    sizeof(NX_CRYPTO_RSA),              

    /* RSA initialization routine.                  */
    _nx_secure_crypto_method_rsa_init,               

    /* Cleanup routine, not used.                    */
    NX_NULL,                                        

    /* RSA operation                                */
    _nx_secure_crypto_method_rsa_operation           

};
```
***Null***

```C
/* NULL encryption method. */
NX_CRYPTO_METHOD crypto_method_null = 
{
    NX_CRYPTO_ENCRYPTION_NULL,/* Name of the crypto algorithm  */
    0,                        /* Key size in bits, not used    */
    0,                        /* IV size in bits, not used     */
    0,                        /* ICV size in bits, not used    */
    4,                        /* Block size in bytes           */
    0,                        /* Metadata size in bytes        */
    NX_NULL,                  /* Initialization routine,unused */
    NX_NULL,                  /* Cleanup routine, not used     */
    _nx_secure_crypto_method_null_operation  /* NULL operation  
*/
}; 
```
***HMAC-SHA1***
```C
NX_CRYPTO_METHOD crypto_method_hmac_sha1 = 
{
    /* HMAC SHA1 algorithm                               */
    TLS_HASH_SHA1,            


    /* Key size in bits. For HMAC-SHA1 this value is 160 */ 
    NX_CRYPTO_HMAC_SHA1_KEY_LEN_IN_BITS,              

    /* IV size in bits, not used                         */
    0,                                            

    /* Transmitted ICV size in bits. Unused.             */
    0, 

    /* Block size in bytes, not used                     */
    0,                                            

    /* Metadata size in bytes                            */
    sizeof(NX_SHA1_HMAC),                                            

    /* Initialization routine, not used                  */
    NX_NULL,                                      

    /* Cleanup routine, not used                         */
    NX_NULL,                                          

    /* HMAC SHA1 operation                               */
    _nx_secure_crypto_method_hmac_sha1_operation   
};
```
***Brak***

Specjalna metoda **NX_CRYPTO_NONE** służy do sygnalizowania modułowi IPsec, że szyfrowanie lub usługa uwierzytelniania nie jest wymagana. Jest ona skonfigurowana w następujący sposób:

```C
/* NX_CRYPTO_NONE means encryption or authentication
   method is not needed.  */
NX_CRYPTO_METHOD crypto_method_none = 
{
    NX_CRYPTO_NONE,       /* Name of the crypto algorithm */
    0,                    /* Key size in bits, not used   */
    0,                    /* IV size in bits, not used    */
    0,                    /* ICV size in bits, not used   */
    0,                    /* Block size in bytes          */
    0,                    /* Metadata size in bytes       */
    NX_NULL,              /* Initialization routine, not used */
    NX_NULL,              /* Cleanup routine, not used    */
    NX_NULL               /* NULL operation               */
};                                               
```
### <a name="initializing-tls-with-cryptographic-methods"></a>Inicjowanie szyfrowania TLS za pomocą metod kryptograficznych

Po utworzeniu procedur kryptograficznych zgodnych z podpisami metod kryptograficznych opisanymi w poprzedniej sekcji należy przekazać je do szyfrowania TLS podczas inicjowania bloku NX_SECURE_TLS_SESSION kryptograficznego. Odbywa się to w usłudze TLS nx_secure_tls_session_create:

```C
UINT  nx_secure_tls_session_create(
              NX_SECURE_TLS_SESSION*     session_ptr,
              const NX_SECURE_TLS_CRYPTO*    tls_cipher_table,
              VOID*                encryption_metadata_area,
              ULONG                 encryption_metadata_size
);
```
- session_pointer jest wskaźnikiem do NX_SECURE_TLS_SESSION sterowania.
- tls_cipher_table jest wskaźnikiem do NX_SECURE_TLS_CRYPTO sterowania, opisanego poniżej.
- encryption_metadata_area wskazuje miejsce używane przez procedury kryptograficzne w tls.
- encryption_metadata_size to rozmiar obszaru metadanych w bajtach.

### <a name="elliptic-curve-cryptography-ecc-in-netx-secure-tls"></a>Kryptografia krzywej eliptycznej (ECC) w zabezpieczonych zabezpieczeniach NetX TLS

Kryptografia krzywej eliptycznej (ECC) udostępnia schemat kryptografii klucza publicznego, który może być używany zamiast RSA. EcC jest zwykle szybszy i używa mniejszych kluczy niż RSA, więc może być cenną opcją dla osadzonego szyfrowania TLS. W wersjach X-Ware starszych niż Azure RTOS 6.0 ecc zostało dostarczone jako dodatek, co wymagało zainstalowania kodu źródłowego ECC w projekcie. Azure RTOS 6.0 zintegrowane ECC z główną bazą kodu, więc instalacja plików ECC nie jest już konieczna. Jednak ecc nadal wymaga tego samego inicjowania co poprzednie wersje.

### <a name="supported-ecc-curves"></a>Obsługiwane krzywe ECC

NetX Secure implementuje części krzywych zgodnie z <http://www.secg.org/sec2-v2.pdf> . Krzywe pochyłowe są obsługiwane<sup>18:</sup>

  - secp256r1 
  - secp384r1 
  - secp521r1 

Jeśli są używane inne krzywe ECC, procedura *nx_secure_tls_session_start()* zwróci błąd NX_SECURE_TLS_NO_SUPPORTED_CIPHERS wskazujący, że były używane nieobsługiwane krzywe.

Należy pamiętać, że łańcuch certyfikatów TLS może być również szyfrowany za pomocą algorytmów ECC. Mimo że krzywe dostarczane przez klienta TLS są obsługiwane, istnieje możliwość, że krzywa ECC używana w łańcuchu certyfikatów nie jest obsługiwana. W takim przypadku *nx_secure_tls_session_start* zwraca NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER.

Przykład domyślnej tabeli szyfrowania ECC znajduje się w nx_crypto_generic_ciphersuites.c. Zobacz sekcję "TLS Cryptographic Cipher Table" (Kryptograficzna tabela szyfrowania TLS), aby uzyskać więcej informacji na temat tabel szyfrów.

18. Należy pamiętać, że implementacje dla krzywych secp192r1 i secp224r1 są również dostępne dla starszych aplikacji. Jednak te krzywe są teraz uznawane za słabe i NIE POWINNY być używane do tworzenia nowych aplikacji.

### <a name="crypto-methods-for-ecc"></a>Metody kryptograficzne dla ECC

Metody kryptograficzne dla grup krzywej eliptycznej:

- NX_CRYPTO_METHOD crypto_method_ec_secp192<sup>15;</sup>  
- NX_CRYPTO_METHOD crypto_method_ec_secp224<sup>15;</sup>  
- NX_CRYPTO_METHOD crypto_method_ec_secp256;  
- NX_CRYPTO_METHOD crypto_method_ec_secp384;  
- NX_CRYPTO_METHOD crypto_method_ec_secp521;

Metody kryptograficzne dla krzywych ECC są zdefiniowane w nx_crypto_generic_ciphersuites.c.

Metoda kryptograficzna dla ECDHE:

- NX_CRYPTO_METHOD crypto_method_ecdhe;

Metoda kryptograficzna ecdsa:

- NX_CRYPTO_METHOD crypto_method_ecdsa;

Metody kryptograficzne ECDSA i ECDHE są zdefiniowane w nx_crypto_generic_ciphersuites.c.

W połączeniu z innymi metodami kryptograficznymi, takimi jak RSA, SHA i AES, mogą być używane jako bloki konstrukcyjne dla tabeli odnośników szyfru.

### <a name="enabling-ecc-support-for-tls"></a>Włączanie obsługi ECC dla TLS

EcC jest domyślnie włączona dla TLS. Aby wyłączyć obsługę ECC, należy zdefiniować NX_SECURE_DISABLE_ECC_CIPHERSUITE symboli.

Aby zmiany weszły w życie, należy ponownie skompilować bezpieczną bibliotekę NetX i wszystkie aplikacje, które korzystają z tej biblioteki.

W kodzie aplikacji interfejs API n *x_secure_tls_ecc_initialize()* musi zostać wywołany po utworzeniu sesji TLS. Ten interfejs API powiadamia sesję TLS o typie krzywych, które mają być używane do operacji wymiany kluczy TLS i weryfikacji certyfikatów. W fazie uściślniania TLS, jeśli algorytm ECC jest wybrany, parametry związane z krzywą ECC klienta i serwera wymiany, aby zdecydować, której krzywej użyć.

Poniższy segment kodu ilustruje sposób korzystania z interfejsu API. Należy pamiętać, że *argumenty (nx_crypto_ecc_supported_groups, nx_crypto_ecc_supported_groups_size i nx_crypto_ecc_curves)* są zdefiniowane w *nx_crypto_generic_ciphersuites.c.* W związku z tym te symbole mogą być używane bezpośrednio.

```C
status = nx_secure_tls_ecc_initialize(&tls_session,     
                    nx_crypto_ecc_supported_groups,      
                    nx_crypto_ecc_supported_groups_size,     
                    nx_crypto_ecc_curves);
```
Przykładowa konfiguracja w pliku nx_crypto_generic_ciphersuites.c zawiera tabelę odnośników szyfru ECC, która jest używana po włączeniu ecc. Aby użyć ecc, po prostu nx_crypto_tls_ciphers_ecc jako parametr tabeli ciphersuite podczas tworzenia sesji TLS z nx_secure_tls_session_create. Przykładowa tabela zawiera zarówno szyfry ECC, jak i inne niż ECC.

### <a name="tls-cryptographic-cipher-table"></a>Kryptograficzna tabela szyfrowania TLS

Struktura NX_SECURE_TLS_CRYPTO jest zdefiniowana jako:

```C
typedef struct NX_SECURE_METHODS_STRUCT
{
    /* Table that maps ciphersuites to crypto methods. */
    NX_SECURE_TLS_CIPHERSUITE_INFO* nx_secure_tls_ciphersuite_lookup_table;
    USHORT nx_secure_tls_ciphersuite_lookup_table_size;

    /* Table that maps X.509 cipher identifiers to crypto methods. */
    NX_SECURE_X509_CRYPTO *nx_secure_tls_x509_cipher_table;
    USHORT nx_secure_tls_x509_cipher_table_size;

    /* Specific routines needed for specific TLS versions. */
#if (NX_SECURE_TLS_TLS_1_0_ENABLED || NX_SECURE_TLS_TLS_1_1_ENABLED)
    NX_CRYPTO_METHOD *nx_secure_tls_handshake_hash_md5_method;
    NX_CRYPTO_METHOD *nx_secure_tls_handshake_hash_sha1_method;
    NX_CRYPTO_METHOD *nx_secure_tls_prf_1_method;
#endif

#if (NX_SECURE_TLS_TLS_1_2_ENABLED)
    NX_CRYPTO_METHOD *nx_secure_tls_handshake_hash_sha256_method;
    NX_CRYPTO_METHOD *nx_secure_tls_prf_sha256_method;
#endif

#if (NX_SECURE_TLS_TLS_1_3_ENABLED)
    const NX_CRYPTO_METHOD *nx_secure_tls_hkdf_method;
    const NX_CRYPTO_METHOD *nx_secure_tls_hmac_method;
    const NX_CRYPTO_METHOD *nx_secure_tls_ecdhe_method;
#endif

} NX_SECURE_TLS_CRYPTO;
```
Tabela jest tworzona przez wypełnienie wpisów dla tej struktury w stałej statycznej znajdującej się w projekcie NetX Secure TLS, zwykle z procedurami kryptograficznymi i modułami.

Na przykład biblioteka kryptograficzna tylko do oprogramowania ("ogólna") dostarczana z oprogramowaniem NetX Secure zawiera następującą definicję tabeli (w przypadku obsługi szyfrów innych niż ECC<sup>19):</sup>

```C
/* Define the cipher table object we can pass into TLS. */
const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers =
{
    /* TLS Ciphersuite lookup table and size. */
    _nx_crypto_ciphersuite_lookup_table,
    sizeof(_nx_crypto_ciphersuite_lookup_table) / 
    sizeof(NX_SECURE_TLS_CIPHERSUITE_INFO),

    /* X.509 certificate cipher table and size. */
    _nx_crypto_x509_cipher_lookup_table,
    sizeof(_nx_crypto_x509_cipher_lookup_table) / sizeof(NX_SECURE_X509_CRYPTO),

    /* TLS version-specific methods. */
#if (NX_SECURE_TLS_TLS_1_0_ENABLED || NX_SECURE_TLS_TLS_1_1_ENABLED)
    &crypto_method_md5,
    &crypto_method_sha1,
    &crypto_method_tls_prf_1,
#endif

#if (NX_SECURE_TLS_TLS_1_2_ENABLED)
    &crypto_method_sha256,
    &crypto_method_tls_prf_sha_256
#endif

#if (NX_SECURE_TLS_TLS_1_3_ENABLED)
    &crypto_method_hkdf,
    &crypto_method_hmac,
    &crypto_method_ecdhe,
#endif
};
```
W strukturze pierwszym wpisem jest tabela szyfrowania TLS. Struktura NX_SECURE_TLS_CIPHERSUITE_INFO mapuje procedury kryptograficzne (w formie wskaźników NX_CRYPTO_METHOD) na określone szyfry zgodnie ze specyfikacjami TLS. Druga wartość to liczba wpisów w tabeli wskazywanych przez pierwsze pole.

Następne pole wskazuje tabelę procedur używanych przez platformę X.509 podczas przetwarzania certyfikatów cyfrowych, a struktura NX_SECURE_X509_CRYPTO jest podobna do NX_SECURE_TLS_CIPHERSUITE_INFO. Następujące pole to liczba wpisów w tabeli.

Poniżej tabeli odnośników znajduje się szereg procedur wymaganych dla określonych wersji TLS. Na przykład w wersjach wcześniejszych niż TLS 1.2 procedury generowania kluczy i wyznaczania skrótu uściślania zostały naprawione w celu użycia kombinacji algorytmu SHA-1 i MD5 — metody dla tych procedur są wywoływane w szczególności w strukturze szyfrowania, ponieważ nie są powiązane z określonymi szyframi. W wersji 1.2 TLS procedury generowania kluczy i wyznaczania wartości skrótu są wybierane przez szyfr, ale w przypadku szyfrów, które nie określają procedur do użycia, używana jest metoda wyznaczania wartości skrótu SHA-256, a struktura szyfrowania wywołuje tę procedurę specjalnie.

TLS 1.3 wymaga kilku dodatkowych szyfrów specyficznych dla różnych operacji.

19. Pamiętaj, że obsługa TLS 1.3 wymaga ecc — użyj nx_crypto_tls_ciphers_ecc, jeśli jest włączony.

### <a name="tls-ciphersuite-lookup-table"></a>Tabela odnośników szyfrowania TLS

Aby wypełnić tabelę szyfrowania dla szyfrowania TLS, należy również utworzyć tabelę odnośników szyfru, która mapuje procedury kryptograficzne na określone identyfikatory szyfrów. Identyfikatory są wartościami zarejestrowanymi przez IANA, które są uniwersalne. Aby uzyskać więcej informacji, zobacz RFC TLS. Procedury reprezentują 5 oddzielnych metod używanych w każdym szyfru (niektóre szyfry mogą nie używać wszystkich 5): szyfr publiczny, uwierzytelnianie za pomocą klucza publicznego, szyfrowanie sesji, procedura wyznaczania wartości skrótu sesji i funkcja Pseudo-Random TLS (PRF). W poniższej tabeli wyjaśniono każdą z 5 metod:

| **Kategoria procedury**      | **Opis**                                                                                       | **Przykładowe algorytmy**                                            |
| ------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| Szyfr publiczny             | Służy do wymiany kluczy podczas uściśniania TLS                                                        | RSA, Diffie-Hellman, ECC                                          |
| Uwierzytelnianie za pomocą klucza publicznego | Służy do uwierzytelniania lub podpisywania danych podczas uściśniania TLS                                            | RSA, DSS                                                          |
| Szyfrowanie sesji            | Algorytm klucza symetrycznego używany do szyfrowania danych aplikacji podczas sesji TLS                       | AES, RC4                                                          |
| Skrót sesji              | Służy do zachowania integralności komunikatów podczas sesji TLS (zapewnia, że dane nie uległy zmianie) | SHA-1, SHA-256                                                    |
| TLS PRF                   | Służy do generowania materiału klucza i skrótu uściśnia w uściśle TLS                          | Plik PRF jest oparty na procedurach wyznaczania wartości skrótu — SHA-1 + MD5, SHA-256, SHA-512 |

Struktura NX_SECURE_TLS_CIPHERSUITE_INFO jest zdefiniowana w następujący sposób:

```C
typedef struct NX_SECURE_TLS_CIPHERSUITE_INFO_struct
{
    /* The IANA value of the ciphersuite as defined by the TLS spec.*/
    USHORT nx_secure_tls_ciphersuite;

    /* The Public Key operation in this suite - RSA or DH. */
    NX_CRYPTO_METHOD *nx_secure_tls_public_cipher;

    /* The Public Authentication method used for signing data. */
    NX_CRYPTO_METHOD *nx_secure_tls_public_auth;

    /* The session cipher being used - AES, RC4, etc. */
    NX_CRYPTO_METHOD *nx_secure_tls_session_cipher;

    /* The size of the initialization vectors for the session cipher (bytes).*/
    USHORT nx_secure_tls_iv_size;

    /* The key size for the session cipher (bytes). */
    UCHAR nx_secure_tls_session_key_size;

    /* The hash being used - MD5, SHA-1, SHA-256, etc. */
    NX_CRYPTO_METHOD *nx_secure_tls_hash;

    /* The size of the hash being used. SHA-1 is 20 bytes, MD5 is 16 bytes.*/
    USHORT nx_secure_tls_hash_size;

    /* The TLS PRF being used – this is only for TLSv1.2. */
    NX_CRYPTO_METHOD *nx_secure_tls_prf;

} NX_SECURE_TLS_CIPHERSUITE_INFO;
```
Pole nx_secure_tls_ciphersuite zawiera wartość szyfru IANA, a wskaźniki NX_CRYPTO_METHOD reprezentują 5 metod używanych przez ten szyfr. Wartości skalarne (nx_secure_tls_iv_size, nx_secure_tls_key_size i nx_secure_tls_hash_size) są informacyjne i zawierają informacje, które mogą być NX_CRYPTO_METHOD wpisów.

Na przykład przyjrzymy się domyślnej wartości szyfrowania TLS, TLS_RSA_WITH_AES_128_CBC_SHA, która określa użycie algorytmu RSA, AES-CBC z kluczami 128-bitowym i algorytmu SHA-1 do wyznaczania wartości skrótu sesji. Dla tego szyfru nie określono żadnego szyfrowania TLS PRF, dlatego w trybie TLSv1.2 będzie on używać domyślnego pliku PRF SHA-256. Należy pamiętać, że wszystkie szyfry używają algorytmu SHA-1+MD5 PRF w tls 1.0 i 1.1, niezależnie od pliku PRF określonego w tabeli.

Wpis w tabeli NX_SECURE_TLS_CIPHERSUITE_INFO w ogólnej bibliotece kryptograficznej jest zdefiniowany w następujący sposób:

```C
{ 
  TLS_RSA_WITH_AES_128_CBC_SHA,     /* Ciphersuite identifier */
  &crypto_method_rsa,               /* Public-key cipher (NX_CRYPTO_METHOD)*/
  &crypto_method_rsa,               /* Authentication method(NX_CRYPTO_METHOD)*/
  &crypto_method_aes_cbc_128,       /* Session cipher method(NX_CRYPTO_METHOD)*/
  16,                               /* Session cipher IV size in bytes */
  16,                               /* Session cipher key size in bytes */
  &crypto_method_hmac_sha1,         /* Session hash routine(NX_CRYPTO_METHOD) */
  20,                               /* Session hash output size in bytes */
  &crypto_method_tls_prf_sha_256    /* TLSv1.2 PRF */
},
```

Należy pamiętać, że w przypadku szyfrowania sesji rozmiar klucza jest określany przez klucz szyfrowania, ale w przypadku metod klucza publicznego rozmiar klucza nie jest znany, dopóki nie zostanie w toku uściślanie TLS, ponieważ klucze publiczne są zawarte w certyfikatach cyfrowych wymienianych podczas uściślania.

### <a name="x509-cipher-lookup-table"></a>Tabela odnośników szyfrowania X.509

Podobnie jak NX_SECURE_TLS_CIPHERSUITE_INFO tabela, struktura NX_SECURE_X509_CRYPTO mapuje procedury kryptograficzne na znane wartości. W przypadku X.509 identyfikatory są w rzeczywistości identyfikatorami ID zdefiniowanymi przez X.509 i zarejestrowanymi w treściach standardów ISO i ITU. Identyfikatory ID to wielo bajtowe wartości o zmiennej długości, zaprojektowane w celu unikatowego identyfikowania różnych informacji w różnych standardach telekomunikacyjnych, w tym procedur kryptograficznych używanych w certyfikatach cyfrowych. Ze względu na fakt, że identyfikatory OID są zmienną długością, zabezpieczenia NetX TLS mapują oficjalne wartości OID na stałe o stałej długości, które są używane wewnętrznie (zobacz nx_secure_x509.h). Te stałe są używane w strukturze NX_SECURE_X509_CRYPTO, która jest zdefiniowana w następujący sposób:

```C
/* Structure to hold X.509 cryptographic routine information. */
typedef struct NX_SECURE_X509_CRYPTO_struct
{
    /* Internal NetX Secure identifier for certificate "ciphersuite" which consists
       of a hash and a public key operation. These can be mapped to OIDs in X.509.
        */
    USHORT nx_secure_x509_crypto_identifier;

    /* Public-Key Cryptographic method used by certificates. */
    NX_CRYPTO_METHOD *nx_secure_x509_public_cipher_method;

    /* Hash method used by certificates. */
    NX_CRYPTO_METHOD *nx_secure_x509_hash_method;
} NX_SECURE_X509_CRYPTO;
```

Pierwsze pole, *nx_secure_x509_crypto_identifier*, to wewnętrzna reprezentacja OID używana przez netX Secure.

Drugie i trzecie pola wskazują na NX_CRYPTO_METHOD, które reprezentują metody kryptograficzne identyfikowane przez OID, operację klucza publicznego sparowanego z procedurą wyznaczania wartości skrótu. Należy pamiętać, że każdy certyfikat cyfrowy może mieć więcej niż jeden identyfikator OID dla procedur kryptograficznych.

Tabela metod dla X.509 jest konstruowana w taki sam sposób jak tabela odnośników ciphersuite. Na przykład przyjrzymy się OID, aby uzyskać RSA_SHA1. Rzeczywisty OID dla RSA_SHA1 jest następujący:

```C
{iso(1) member-body(2) us(840) rsadsi(113549) pkcs(1) pkcs-1(1) sha1-with-rsa-
signature(5)}
```
Identyfikator OID jest reprezentowany w składni ASN.1 i ma wartość liczbową 1.2.840.113549.1.1.5. Ta wartość jest następnie kodowana w formacie binarnym, tworząc następujące bajty:

```C
UCHAR RSA_SHA1_OID = { 0x2A, 0x86, 0x48, 0x86, 0xF7, 0x0D, 0x01, 0x01, 0x05 };
```
Rzeczywista konwersja z asn.1 na format binarny wykracza poza zakres tego dokumentu. Wyszukaj kodowanie ASN.1 dla identyfikatorów ID, aby uzyskać więcej informacji. Binarną reprezentację identyfikatorów ID obsługiwanych przez zabezpieczenia NetX można znaleźć w *pliku nx_secure_x509.c.*

Po mapowaniu rzeczywistego OID na wewnętrznie rozpoznaną stałą możemy utworzyć wpis dla wartości RSA_SHA1 w NX_SECURE_X509_CRYPTO tabeli:

```C
{ 
    NX_SECURE_TLS_X509_TYPE_RSA_SHA_1,    /* Internal OID constant. */
    &crypto_method_rsa,                   /* RSA method (NX_CRYPTO_METHOD). */ 
    &crypto_method_sha1                   /* SHA-1 method (NX_CRYPTO_METHOD). */
}, 
```
### <a name="default-tls-routines"></a>Domyślne procedury TLS

Jak wspomniano powyżej, TLS wymaga pewnych domyślnych procedur generowania kluczy i weryfikacji komunikatów podczas procedury praktycznej. Podstawową procedurą jest funkcja Pseudo-Random TLS lub PRF. Funkcja PRF jest oparta na procedurach wyznaczania wartości skrótu i może służyć do generowania dowolnej ilości pseudolosowych danych<sup>20</sup> na potrzeby generowania kluczy lub w innych celach.

Oprócz funkcji PRF każda wersja usługi TLS korzysta z domyślnych procedur wyznaczania wartości skrótu, które również muszą zostać dostarczone. W przypadku wersji 1.0 i 1.1 TLS te procedury wyznaczania wartości skrótu to MD5 i SHA-1. TLS w wersji 1.2 wymaga tylko sha-256.

W strukturze NX_SECURE_TLS_CRYPTO istnieją wskaźniki NX_CRYPTO_METHOD MD5, SHA-1, SHA-256, TLS w wersji 1.0/1.1 PRF i domyślny TLS 1.2 PRF.

Obsługa TLS 1.3 dodaje pola dla funkcji HKDF (generowanie kluczy), HMAC (dla określonych operacji wyznaczania wartości skrótu używanych podczas wyznaczania wartości skrótu) i ECDHE (wymagane dla funkcji TLS 1.3).

W bibliotece kryptografii oprogramowania ogólnego są dostępne wersje oprogramowania TLS PRF. W przypadku TLS 1.0/1.1 ta funkcja jest nazywana *nx_crypto_tls_prf_1*. W przypadku TLS 1.2 funkcja jest nazywana *nx_secure_tls_prf_sha256*. Sufiks "1" reprezentuje starszą wartość TLS 1.0 PRF, a sufiks "sha256" odnosi się do faktu, że domyślny czas ściągnowania TLS 1.2 jest oparty na sha-256. Gdy jest potrzebna obsługa innych procedur PRF, sufiks dla tych procedur będzie odzwierciedlał używaną metodę skrótu. Ponieważ procedury PRF są oparte na metodach wyznaczania wartości skrótu, podstawowe procedury wyznaczania wartości skrótu mogą być niezależnie przyspieszane sprzętowo na różnych platformach docelowych.

Oprócz szyfrowania TLS i tabel odnośników X.509 można wypełnić domyślne procedury prf i skrótu wypełnione w strukturze NX_SECURE_TLS_CRYPTO i użyć ich do zainicjowania sesji TLS.

20. "Pseudolosowe" odnosi się do faktu, że PRF jest deterministyczny, co oznacza, że zawsze będzie tworzyć te same dane wyjściowe, biorąc pod uwagę te same dane wejściowe, ale losowe, ponieważ dane wyjściowe nie są przewidywalne. TLS używa tej właściwości prf do generowania kluczy sesji na podstawie różnych danych publicznych w połączeniu z głównym kluczem tajnym wymienianym podczas ugody przy użyciu szyfrowania klucza publicznego, takiego jak RSA.

### <a name="cryptographic-metadata"></a>Metadane kryptograficzne

Zanim będziemy w stanie zainicjować sesję TLS z tabelą NX_SECURE_TLS_CRYPTO, musimy przydzielić miejsce buforu dla metadanych procedury kryptograficznych. Metadane są używane do przechowywania całego stanu skojarzonego z określonej procedury reprezentowanej przez jej blok sterujący. Pole *nx_crypto_metadata_area_size* każdego NX_CRYPTO_METHOD musi być ustawione na rozmiar struktury sterującej skojarzonej z tą procedurą. Inicjalizacja TLS nie będzie prawidłowo uwzględniać wymaganego miejsca, co może powodować problemy z przepełnieniem buforu.

Przed rozpoczęciem sesji TLS należy przydzielić bufor metadanych. Bufor jest automatycznie dzielony przez nx_secure_tls_session_create a miejsce jest zarezerwowane dla każdej procedury, która jest dostarczana w tabeli metod kryptograficznych. Należy pamiętać, że ponieważ tylko jeden szyfr jest aktywny w danej chwili w sesji TLS, liczba obsługiwanych mechanizmów szyfrowania nie ma wpływu na potrzebną przestrzeń metadanych — miejsce jest zarezerwowane dla każdej z 5 procedur szyfrowania przy użyciu maksymalnego rozmiaru bloku kontrolnego dla tej kategorii w tabeli wyszukiwania szyfrów.

Aby ułatwić obliczanie rozmiaru buforu metadanych, usługa *nx_secure_metadata_size_calculate* wykonuje te same obliczenia co nx_secure_tls_session_create, ale po prostu zwraca całkowity wymagany rozmiar buforu metadanych w bajtach.

### <a name="initializing-the-tls-session"></a>Inicjowanie sesji TLS

Po utworzeniu NX_CRYPTO_METHOD i NX_SECURE_TLS_CRYPTO i zarezerwowaniu obszaru metadanych możemy zainicjować sesję TLS w następujący sposób (wartości z powyższych przykładów):

```C
/* Pointer to the platform-specific cipher table. */
extern nx_crypto_tls_ciphers;

/* Cryptographic routine metadata buffer. Size is determined by calling 
nx_secure_tls_metadata_size_calculate with the nx_crypto_tls_ciphers table referenced 
above. */
UCHAR crypto_metadata[4500];

/* Initialize our TLS session using our cipher table and metadata area. Note that we can 
use sizeof for the metadata array because the size parameter expects the size in bytes.*/

nx_secure_tls_session_create(
    &tls_session,            /* Pointer to TLS session.      */
    &nx_crypto_tls_ciphers,  /* Pointer to cipher table.     */
    crypto_metadata,         /* Cryptography metadata buffer.*/
    sizeof(crypto_metadata), /* Size of metadata buffer.     */
);
```
