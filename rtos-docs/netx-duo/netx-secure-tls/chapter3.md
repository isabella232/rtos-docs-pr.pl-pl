---
title: Rozdział 3 — Opis funkcjonalny usługi Azure RTO NetX Secure
description: Ten rozdział zawiera opis funkcjonalny protokołu Secure TLS NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c28ad0255f99986a4ddfe5faefad81e70840e5e0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821589"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-secure"></a>Rozdział 3 — Opis funkcjonalny usługi Azure RTO NetX Secure

## <a name="execution-overview"></a>Przegląd wykonywania

Ten rozdział zawiera opis funkcjonalny usługi Azure RTO NetX Secure TLS. Istnieją dwa podstawowe typy wykonywania programu w aplikacji NetX Secure TLS: inicjalizacja i wywołania interfejsu aplikacji. 

*Zabezpieczenia NetX zakładają istnienie ThreadX i NetX/NetXDuo. Z ThreadX wymaga wykonania wątku, zawieszenia, okresowe czasomierze i wzajemnych wykluczeń. Z NetX/NetXDuo wymaga sieci TCP/IP i sterowników.*

## <a name="transport-layer-security-tls-and-secure-sockets-layer-ssl"></a>Transport Layer Security (TLS) i Secure Sockets Layer (SSL)

Składnik Secure Network Protocol NetX Secure to Transport Layer Security implementacja protokołu TLS, zgodnie z opisem w RFC 2246 (wersja 1,0), 4346 (wersja 1,1), 5246 (wersja 1,2) i 8446 (wersja 1,3). Uwzględniono również procedury obsługi dla podstawowego X. 509 (RFC 5280).

NetX Secure TLS obsługuje protokół TLS w wersji 1,2 i 1,3. Implementacje są dostępne dla obecnie przestarzałych protokołów TLS 1,0 i TLS 1,1, ale muszą być jawnie zainicjowane i nie są zalecane do użycia w nowych produktach.

*Secure Sockets Layer* (SSL) była oryginalną nazwą protokołu TLS, zanim stała się standardem RFC 2246 i "SSL" jest często używana jako nazwa ogólna dla protokołów TLS. Ostatnia wersja protokołu SSL to 3,0, a protokół TLS 1,0 jest czasami określany jako wersja SSL 3,1. Wszystkie wersje oficjalnego protokołu "SSL" są uznawane za przestarzałe i niezabezpieczone, a obecnie NetX Secure nie zapewnia implementacji protokołu SSL.

TLS określa protokół do generowania *kluczy sesji* , które są tworzone podczas *uzgadniania* protokołu TLS między klientem i serwerem TLS, a te klucze są używane do szyfrowania danych wysyłanych przez aplikację podczas sesji TLS *.*

Dane protokołu TLS są podzielone na *rekordy* , które są równoważne koncepcji dla pakietu TCP. Każdy rekord TLS ma nagłówek, a zaszyfrowane rekordy TLS również mają stopkę (skrót sumy kontrolnej). Rekordy uzgadniania protokołu TLS mają dodatkowy nagłówek hermetyzowany w większym rekordzie TLS. Rekord TLS jest hermetyzowany przez protokół sieciowy warstwy transportu w taki sam sposób, w jaki pakiet protokołu TCP jest hermetyzowany przez pakiet IP.

### <a name="tls-13"></a>TLS 1,3

W sierpniu 2018 Specyfikacja TLS 1,3 została sfinalizowana. Nowa wersja protokołu to dość znacząca aktualizacja, która zmienia podstawowe aspekty zabezpieczeń i wydajności protokołu TLS. Jednak te zmiany są znacznie niewidoczne dla typowego użytkownika protokołu TLS, ponieważ dotyczą przede wszystkim do komputera stanu uzgadniania TLS i generowania klucza sesji. Dodano również kilka opcjonalnych funkcji i rozszerzeń. Poniżej znajduje się podsumowanie zmian i ich wpływu na funkcjonalność protokołu TLS.

- Komputer stanu uzgadniania został zoptymalizowany przez usunięcie całej wymiany komunikatów przez serwer.
- Generowanie klucza zostało zaktualizowane w celu użycia znormalizowanej procedury o nazwie HKDF (funkcja wyprowadzania klucza opartego na procesorze HMAC) i łączy klucze sesji ze wszystkimi komunikatami uzgadniania (zamiast kilku parametrów wyboru).
- Wszystkie protokoły TLS 1,2 i wcześniejsze ciphersuites są przestarzałe i nie są zgodne z protokołem TLS 1,3. Podobnie wszystkie ciphersuites TLS 1,3 są bezużyteczne z poprzednimi wersjami.
- Wszystkie protokoły TLS 1,3 ciphersuites zapewniają doskonałe utajnienie przekazywania (PFS) przy użyciu kluczy tymczasowych<sup>6</sup> 
- Protokół TLS 1,3 usuwa "kod uwierzytelniania wiadomości" (MAC) w każdym rekordzie na korzyść przy użyciu szyfrów AEAD<sup>7</sup>
- Dodano kilka dodatkowych funkcji opcjonalnych, w tym 0-RTT (czas błądzenia zero), co pozwala na wysyłanie danych aplikacji podczas uzgadniania. 0 — RTT jest czysto opcjonalny i nie jest obecnie obsługiwany w usłudze Azure RTO TLS.

Protokół TLS 1,3 nie ma znacząco wpływu na aplikacje użytkownika. Interfejs API pozostaje dokładnie taki sam między wersjami, a ciphersuites są oznaczane, aby można było użyć pojedynczej tabeli ciphersuite.

Aby można było korzystać z protokołu TLS 1,3, makro NX_SECURE_TLS_ENABLE_TLS_1_3 musi być zdefiniowane globalnie. Protokół TLS 1,3 jest domyślnie wyłączony w usłudze Azure RTO TLS.

6. Klucze "tymczasowych" to asymetryczne pary kluczy, które są generowane podczas uzgadniania protokołu TLS i używane do wymiany kluczy tajnych tylko dla tej sesji. Para kluczy jest odrzucana po użyciu — uniemożliwia to osobie atakującej dostęp do zaszyfrowanych danych w rejestrowanej sesji TLS, nawet jeśli w przyszłości zostanie naruszony klucz prywatny certyfikatu, a tym samym "doskonałe utajnienie przekazywania dalej".

7. Uwierzytelnione szyfrowanie za pomocą skojarzonych danych — tryb szyfrowania, taki jak AES, który łączy szyfrowanie i sprawdzanie integralności w ramach jednej operacji, eliminując konieczność oddzielnego skrótu danych do sprawdzania integralności.

### <a name="tls-record-header"></a>Nagłówek rekordu TLS

Każdy prawidłowy rekord TLS musi mieć nagłówek TLS, jak pokazano w błędzie. Nie znaleziono źródła odwołania.

![Diagram nagłówka rekordu TLS.](media/image2.png)

Rysunek 1 — nagłówek rekordu TLS

Pola nagłówka rekordu TLS są zdefiniowane w następujący sposób:

| Pole nagłówka TLS | Przeznaczenie     |
| ---------------- | ------------- |
| **8-bitowy typ komunikatu** | To pole zawiera typ wysyłanego rekordu TLS. Prawidłowe typy są następujące:<br />-ChangeCipherSpec<sup>8</sup>: 0x14<br />-Alert: 0x15<br />-Uzgadnianie: 0x16<br />-Dane aplikacji: 0x17 |
| **16-bitowa wersja protokołu** | To pole zawiera wersję protokołu TLS. Prawidłowe wartości są następujące:<br />-SSL 3,0:0x0300<br />-TLS 1,0:0x0301<br />-TLS 1,1:0x0302<br />-TLS 1,2:0x0303<br />- **TLS 1,3 <sup>9</sup>**: **0x0303** |
| **16-bitowa Długość** | To pole zawiera długość danych hermetyzowanych w rekordzie TLS. |

8. W protokole TLS 1,3 komunikat ChangeCipherSpec nie jest już używany, mimo że może być przesłany ze względu na zgodność, w takim przypadku komunikat jest ignorowany.

9. Protokół TLS 1,3 ma technicznie wartość 0x0304, jeśli ten schemat był kontynuowany, ale został zmieniony w taki sposób, aby miał rzeczywistą wersję protokołu w rozszerzeniu, więc wszystkie rekordy protokołu TLS 1,3 używają 0x0303 w polach wersji protokołu w celu zapewnienia zgodności z poprzednimi wersjami.

### <a name="tls-handshake-record-header"></a>Nagłówek rekordu uzgadniania protokołu TLS

Każdy prawidłowy rekord uzgadniania TLS musi mieć nagłówek uzgadniania TLS, jak pokazano na rysunku 2.

![Diagram nagłówka rekordu uzgadniania protokołu TLS.](media/image3.png)

Rysunek 2 — nagłówek rekordu uzgadniania TLS

Pola nagłówka rekordu uzgadniania protokołu TLS są zdefiniowane w następujący sposób:

| Pole nagłówka TLS | Przeznaczenie |
| ---------------- |----------------------- |
| **8-bitowy typ komunikatu** | To pole zawiera typ wysyłanego rekordu TLS. Prawidłowe typy są następujące:<br />-ChangeCipherSpec<sup>10</sup>: 0x14<br />-Alert: 0x15<br />-Uzgadnianie: 0x16<br />-Dane aplikacji: 0x17 |
| **16-bitowa wersja protokołu** | To pole zawiera wersję protokołu TLS. Prawidłowe wartości są następujące:<br />-SSL 3,0:0x0300<br />-TLS 1,0:0x0301<br />-TLS 1,1:0x0302<br />-TLS 1,2:0x0303<br />- **TLS 1,3 <sup>11</sup>**: **0x0303** |
| **16-bitowa Długość**    | To pole zawiera długość danych hermetyzowanych w rekordzie TLS. |
| **Typ uzgadniania 8-bitowego** | To pole zawiera typ komunikatu uzgadniania. Prawidłowe wartości są następujące (* **pogrubienie** komunikatów zostało dodane w protokole TLS 1,3):<br />-HelloRequest: 0x00<br />-Komunikacie ClientHello: 0x01<br />-ServerHello: 0x02<br />- **HelloVerifyRequest**: **0x03**<br />- **NewSessionTicket**: **0x04**<br />- **EndOfEarlyData**: **0x05**<br />- **EncryptedExtensions**: **0x08**<br />-Certificate: 0x0B<br />- ServerKeyExchange: 0x0C<br />-CertificateRequest: 0x0D<br />- ServerHelloDone: 0x0E<br />- CertificateVerify: 0x0F<br />-ClientKeyExchange: 0x10<br />-Zakończono: 0x14<br />- **Aktualizacja**: **0x18**<br />- **MessageHash**: **0xFE** |
| **Długość 24-bitowa**    | To pole zawiera długość danych komunikatu uzgadniania. |

10. W protokole TLS 1,3 komunikat ChangeCipherSpec nie jest już używany, mimo że może być przesłany ze względu na zgodność, w takim przypadku komunikat jest ignorowany.

11. Protokół TLS 1,3 ma technicznie wartość 0x0304, jeśli ten schemat był kontynuowany, ale został zmieniony w taki sposób, aby miał rzeczywistą wersję protokołu w rozszerzeniu, więc wszystkie rekordy protokołu TLS 1,3 używają 0x0303 w polach wersji protokołu w celu zapewnienia zgodności z poprzednimi wersjami.

### <a name="the-tls-handshake-and-tls-session"></a>Uzgadnianie TLS i sesja TLS

Typowy uzgadnianie TLS (wersje 1.0-1.2) przedstawiono na rysunku 3. Uzgadnianie TLS rozpoczyna się, gdy klient protokołu TLS wyśle komunikat *komunikacie ClientHello* do serwera TLS, wskazujący na to, że wolisz uruchomić sesję protokołu TLS. Komunikat zawiera informacje o szyfrowaniu, którego klient ma używać dla sesji, wraz z informacjami użytymi do wygenerowania kluczy sesji w dalszej części uzgadniania. Do momentu wygenerowania kluczy sesji wszystkie komunikaty uzgadniania TLS nie są szyfrowane. TLS 1,3 zmienia się nieco uzgadnianie — szczegóły są przedstawione w następnej sekcji.

Serwer TLS reaguje na komunikacie ClientHello z komunikatem ServerHello, wskazując na wybór opcji szyfrowania dostarczonych przez klienta. ServerHello następuje komunikat certyfikatu, w którym serwer udostępnia certyfikat cyfrowy do uwierzytelniania tożsamości klienta. Na koniec serwer wysyła komunikat ServerHelloDone, aby wskazać, że nie ma więcej komunikatów do wysłania. Serwer może opcjonalnie wysyłać inne komunikaty po ServerHello, a w niektórych przypadkach może nie wysłać komunikatu certyfikatu, w związku z czym jest konieczna wiadomość ServerHelloDone.

Gdy klient otrzyma wszystkie komunikaty serwera, ma wystarczającą ilość informacji do wygenerowania kluczy sesji. TLS robi to przez utworzenie udostępnionego bitu danych losowych nazywanych *wstępnie głównym kluczem tajnym*, który jest stałym rozmiarem i jest używany jako inicjator do generowania wszystkich kluczy wymaganych po włączeniu szyfrowania. Wstępnie główny klucz tajny jest szyfrowany przy użyciu algorytmu klucza publicznego (np. RSA) określonego w komunikatach Hello (zobacz poniżej, aby uzyskać informacje o algorytmach klucza publicznego) i klucz publiczny dostarczony przez serwer w jego certyfikacie. Opcjonalna funkcja TLS o nazwie klucze wstępne (PSK) umożliwia ciphersuites, które nie korzystają z certyfikatu, ale zamiast tego używają wartości tajnej współużytkowanej przez hosty (zwykle za pomocą fizycznego transferu lub innej zabezpieczonej metody). Wspólny klucz tajny służy do generowania wstępnego klucza tajnego, a nie przy użyciu zaszyfrowanej wiadomości w celu wysłania wstępnie głównego klucza tajnego. Zapoznaj się z sekcją dotyczącą wstępnie udostępnionych kluczy poniżej.

Zaszyfrowany wstępnie główny klucz tajny jest wysyłany do serwera w komunikacie ClientKeyExchange. Serwer, po odebraniu komunikatu ClientKeyExchange, odszyfrowuje wstępnie główny klucz tajny przy użyciu jego klucza prywatnego i kontynuuje generowanie kluczy sesji równolegle z klientem TLS.

Po wygenerowaniu kluczy sesji wszystkie dalsze komunikaty mogą być szyfrowane przy użyciu algorytmu klucza prywatnego (np. AES) wybranego w komunikatach Hello. Jeden końcowy komunikat niezaszyfrowany o nazwie ChangeCipherSpec jest wysyłany przez klienta i serwer, aby wskazać, że wszystkie dalsze komunikaty będą szyfrowane.

Pierwszy szyfrowany komunikat Wysłany przez klienta i serwer jest również końcowym komunikatem uzgadniania protokołu TLS o nazwie zakończony. Ten komunikat zawiera skrót wszystkich odebranych i wysłanych komunikatów uzgadniania. Ten skrót służy do sprawdzania, czy żaden z komunikatów w uzgadnianiu nie został naruszony ani uszkodzony (ze wskazaniem potencjalnego naruszenia zabezpieczeń).

Po odebraniu ukończonych komunikatów i sprawdzeniu wartości skrótu uzgadniania rozpocznie się sesja TLS, a aplikacja zaczyna wysyłać i odbierać dane. Wszystkie dane wysyłane po obu stronach podczas sesji TLS są najpierw tworzone przy użyciu algorytmu wyznaczania wartości skrótu wybranego w komunikatach powitalnych (w celu zapewnienia integralności komunikatów) i szyfrowany przy użyciu wybranego algorytmu klucza prywatnego z wygenerowanymi kluczami sesji.

Na koniec sesja TLS może zostać zakończona pomyślnie tylko wtedy, gdy klient lub serwer wybierze tę opcję. Obcięta sesja jest uznawana za naruszenie zabezpieczeń (ponieważ osoba atakująca może próbować uniemożliwić odbieranie wszystkich danych), więc zostanie wysłane specjalne powiadomienie, gdy jedna strona chce zakończyć sesję, nazywaną alertem CloseNotify. Zarówno klient, jak i serwer muszą wysyłać i przetwarzać alert CloseNotify o pomyślnym zamknięciu sesji.

![Diagram typowego uzgadniania protokołu TLS.](media/image4.png)

Rysunek 3 — typowe uzgadnianie protokołu TLS

### <a name="tls-13-handshake"></a>Uzgadnianie protokołu TLS 1,3

TLS 1,3 to dość ważna remonty protokołu TLS. Zdecydowana większość zmian została wprowadzona w celu zwiększenia bezpieczeństwa i wydajności. Typowy uzgadnianie TLS 1,3 przedstawiono na rysunku 4. Podstawową różnicę można zobaczyć w liczbie wymian między serwerem a klientem.

W protokole TLS 1,2 i starszych, serwer wyśle dwa loty<sup>12</sup> komunikatów — najpierw ServerHello, a następnie komunikat ChangeCipherSpec przed wysłaniem zaszyfrowanego komunikatu zakończonego, który kończy uzgadnianie. W protokole TLS 1,3 serwer wysyła wszystkie w pierwszym locie — ServerHello, rozszerzenia, certyfikat i gotowe. Komunikat ChangeCipherSpec został wyeliminowany, a serwer generuje swoje klucze sesji i uruchamia szyfrowane komunikaty uzgadniania bezpośrednio po ServerHello.

Nowe rozwiązanie oznacza, że większa część uzgadniania TLS jest chroniona przez szyfrowanie, ograniczając ilość danych w postaci zwykłego tekstu, do których atakujący może uzyskać dostęp. Ponadto usunięcie drugiego lotu serwera (który był tylko ChangeCipherSpec po zakończeniu) oznacza, że klient protokołu TLS nie musi już czekać na rozpoczęcie przesyłania danych aplikacji — gdy tylko klient wyśle własny gotowy komunikat, sesja zostanie uruchomiona.

12. Samolotem jest po prostu kolekcja komunikatów TLS wysyłanych jednocześnie w grupie.

![Diagram uzgadniania TLS 1,3.](media/image5.png)

Rysunek 4 — uzgadnianie protokołu TLS 1,3

> [!NOTE]
> *Protokół TLS 1,3 wprowadza również pojęcie "wczesne dane" i 0-RTT (czas błądzenia zero), co oznacza, że niektóre dane aplikacji mogą być wysyłane podczas pierwszego lotu komunikatów. Ta opcjonalna funkcja została dodana głównie jako Optymalizacja czasu odpowiedzi w przeglądarce sieci Web (np. w celu wysłania wczesnych nagłówków HTTP w celu rozpoczęcia renderowania strony). Począwszy od platformy Azure RTO 6,0, ta funkcja nie jest obsługiwana.*

### <a name="initialization"></a>Inicjalizacja

Stos TCP/IP NetX lub NetXDuo musi być zainicjowany przed użyciem NetX Secure TLS. Zapoznaj się z podręcznikiem użytkownika NetX lub NetXDuo, aby uzyskać informacje na temat poprawnego inicjowania stosu TCP/IP.

Po zainicjowaniu stosu TCP/IP NetX można włączyć protokół TLS. Wewnętrznie cały ruch sieciowy i przetwarzanie protokołu TLS jest obsługiwany przez stos NetX/NetXDuo, bez konieczności interwencji użytkownika. Jednak protokół TLS ma określone wymagania, które muszą być obsługiwane niezależnie od bazowego stosu sieciowego. Te parametry są przypisywane do bloku kontroli protokołu TLS o nazwie ***NX_SECURE_TLS_SESSION** _ przy użyciu usługi _ *_nx_secure_tls_session_create_**.

Protokół TLS ma dwa tryby: serwer i klienta, z których każdy może być włączony w aplikacji (ale tylko jeden tryb na gniazdo NetX), a każdy z nich ma własne określone wymagania, szczegółowo poniżej.

W obu trybach NetX Secure TLS wymaga utworzenia gniazda TCP (***NX_TCP_SOCKET** _) i skonfigurowania go na potrzeby komunikacji TCP z hostem zdalnym. Gniazdo TCP jest przypisane do wystąpienia sesji TLS z usługą _ *_nx_secure_tls_session_start_**, szczegółowo poniżej.

### <a name="initialization--tls-server"></a>Inicjowanie — Serwer TLS

Oprócz gniazda TCP NetX tryb bezpiecznego serwera TLS wymaga *certyfikatu cyfrowego*, który jest dokumentem używanym do identyfikowania serwera TLS na potrzeby połączenia z klientem TLS, i certyfikatami odpowiadającymi *kluczem prywatnym*, zazwyczaj dla algorytmu szyfrowania RSA. Międzynarodowy związek telekomunikacyjny X. 509 standard określa format certyfikatu używany przez protokół TLS i istnieje wiele narzędzi do tworzenia certyfikatów cyfrowych X. 509.

W przypadku protokołu Secure TLS NetX certyfikat X. 509 musi być zakodowany binarnie przy użyciu formatu Distinguished Encoding Rules (DER) z numerem ASN. 1. Algorytm DER to standardowy format binarny protokołu TLS dla certyfikatów.

Klucz prywatny skojarzony z podanym certyfikatem musi mieć format PKCS # 1 DER-Encoded. Klucz prywatny jest używany tylko na urządzeniu i nigdy nie będzie przesyłany przez sieć. Utrzymuj bezpieczeństwo kluczy prywatnych, ponieważ zapewniają one zabezpieczenia komunikacji TLS.

Aby można było zainicjować certyfikat serwera TLS, aplikacja musi udostępnić wskaźnik do buforu zawierającego certyfikat X. 509 szyfrowany algorytmem DER oraz opcjonalne dane klucza prywatnego PKCS # 1 RSA, używając usługi ***nx_secure_x509_certificate_intialize** _, która wypełnia strukturę _ *NX_SECURE_X509_CERT** z odpowiednimi danymi certyfikatu do użycia przez protokół TLS.

Po zainicjowaniu certyfikatu serwera należy go dodać do bloku kontroli protokołu TLS przy użyciu usługi ***nx_secure_tls_local_certificate_add*** .

Po dodaniu certyfikatu serwera do bloku kontroli protokołu TLS gniazdo może być używane do nawiązywania bezpiecznego połączenia z serwerem protokołu TLS.

### <a name="initialization--tls-client"></a>Inicjowanie — klient TLS

Bezpieczny tryb klienta protokołu TLS NetX wymaga *magazynu zaufanych certyfikatów*, który jest kolekcją certyfikatów cyfrowych X. 509 szyfrowanych z zaufanych urzędów certyfikacji (CA). Te certyfikaty są zakładane przez protokół TLS jako "zaufany" i stanowią podstawę do uwierzytelniania certyfikatów dostarczonych przez jednostki serwera TLS do NetX bezpiecznego klienta protokołu TLS.

Certyfikat zaufanego urzędu certyfikacji może być *podpisany z podpisem własnym* lub podpisany przez inny urząd certyfikacji, w którym to przypadku certyfikat jest nazywany *POśrednim urzędem certyfikacji* (ICA). W typowej aplikacji TLS serwer udostępnia certyfikaty usługi ICA wraz z certyfikatem serwera, ale Jedynym wymaganiem do pomyślnego uwierzytelnienia jest to, że łańcuch wystawców (certyfikaty służące do podpisywania innych certyfikatów) może być śledzony z certyfikatu serwera z powrotem do certyfikatu zaufanego urzędu certyfikacji w zaufanym magazynie certyfikatów. Ten łańcuch jest znany jako  *łańcuch zaufania* lub *łańcuch certyfikatów*.

Aby zainicjować zaufany urząd certyfikacji lub certyfikat usługi ICA, aplikacja musi udostępnić wskaźnik do buforu zawierającego certyfikat X. 509 szyfrowany algorytmem DER przy użyciu usługi ***nx_secure_x509_certificate_intialize** _, która wypełnia strukturę _ *NX_SECURE_X509_CERT** z odpowiednimi danymi certyfikatu do użycia przez protokół TLS.

Zaufane certyfikaty, które zostały zainicjowane, są następnie dodawane do bloku kontroli protokołu TLS przy użyciu usługi ***nx_secure_tls_trusted_certificate_add*** . Niepowodzenie dodania certyfikatu spowoduje niepowodzenie sesji klienta TLS, ponieważ nie będzie można uwierzytelnić protokołów protokołu TLS na potrzeby uwierzytelniania zdalnych hostów serwera TLS.

Klient TLS potrzebuje również miejsca na przydzielenie certyfikatu serwera przychodzącego (przy założeniu, że nie jest używany tryb klucza wstępnego). Od NetX Secure TLS 5,12 nie jest już konieczne, aby aplikacja mogła przydzielić miejsce dla certyfikatu zdalnego. Jednak Starsza opcja przydzielenia miejsca dla certyfikatu serwera jest nadal dostępna, a certyfikaty przypisane przez użytkownika będą używane przed wewnętrzną optymalizacją bufora certyfikatów <sup>13</sup> — zobacz usługę ***nx_secure_tls_remote_certificate_allocate*** , aby uzyskać więcej informacji.

Po utworzeniu magazynu zaufanych certyfikatów i przydzieleniu miejsca na certyfikat serwera, gniazdo może być używane do nawiązywania bezpiecznego połączenia z klientem TLS.

13. Optymalizacja wykorzystuje "bufor pakietów" dostarczony przez aplikację użytkownika w sesji protokołu TLS przy użyciu *nx_secure_tls_session_packet_buffer_set* do przydzielenia struktur analizy X. 509 zamiast używania struktur dostarczonych przez użytkownika, które są używane we wcześniejszych wersjach NetX Secure TLS. Jest mało prawdopodobne, że napotkanie łańcucha certyfikatów przekracza rozmiar buforu pakietów, co oznacza, że można zwiększyć rozmiar buforu pakietów lub *nx_secure_tls _remote_certificate_allocate* może zostać użyty do przydzielenia większej ilości miejsca dla łańcucha certyfikatów.

### <a name="application-interface-calls"></a>Wywołania interfejsu aplikacji

NetX Secure TLS aplikacje zwykle powodują wywołania funkcji z wątków aplikacji uruchomionych w ramach ThreadX RTO. Niektóre inicjalizacje, szczególnie w przypadku źródłowych protokołów komunikacji sieciowej (np. TCP i IP), mogą być wywoływane z programu ***tx_application_define *.** Więcej informacji na temat inicjowania komunikacji sieciowej można znaleźć w podręczniku użytkownika NetX/NetXDuo.

Protokół TLS znacznie wykorzystuje procedury szyfrowania, które są operacjami intensywnie wykorzystującymi procesor. Zwykle te operacje będą wykonywane w kontekście wywołania wątku.

### <a name="tls-session-start"></a>Rozpoczęcie sesji TLS

Aby można było działać, protokół TLS wymaga podstawowego protokołu sieciowego warstwy transportowej. Zazwyczaj używany jest protokół TCP. Aby można było ustanowić NetX bezpieczną sesję TLS, należy ustanowić połączenie TCP za pomocą interfejsu API NetX/NetXDuo TCP. Należy utworzyć **NX_TCP_SOCKET** i nawiązać połączenie za pomocą **_nx_tcp_server_socket_listen_*_ i _*_nx_tcp_server_socket_accept_*_ usług (dla serwera TLS) lub _* usługi _nx_tcp_client_socket_connect_** (dla klienta TLS).

Po nawiązaniu połączenia TCP gniazdo TCP jest następnie przesyłane do usługi ***nx_secure_tls_session_start*** .

### <a name="tls-packet-allocation"></a>Alokacja pakietów TLS

NetX Secure TLS używa tej samej struktury pakietów co NetX/NetXDuo TCP (***NX_PACKET** _), z wyjątkiem tego, że zamiast wywoływania usługi _*_nx_packet_allocate_*_ , należy wywołać usługę _ *_nx_secure_tls_packet_allocate_**, aby miejsce na nagłówek TLS mogło być prawidłowo przydzieloną.

### <a name="tls-session-send"></a>Wysyłanie sesji protokołu TLS

Po rozpoczęciu sesji TLS aplikacja może wysyłać dane przy użyciu usługi ***nx_secure_tls_session_send** _. Usługa Send jest taka sama jak w przypadku usługi _*_nx_tcp_socket_send_*_ , pobierając _*_NX_PACKETą_*_ strukturę danych zawierającą wysyłane dane, tylko te dane zostaną zaszyfrowane przez stos bezpiecznego protokołu TLS przed wysłaniem, a pakiet musi zostać alokowany przy użyciu _ *_nx_secure_tls_packet_allocate_* *.

### <a name="tls-session-receive"></a>Odbieranie sesji TLS

Po rozpoczęciu sesji TLS aplikacja może zacząć odbierać dane przy użyciu usługi ***nx_secure_tls_session_receive** _. Podobnie jak w przypadku wysyłania sesji TLS, ta usługa jest identyczna z użyciem do _ *_nx_tcp_socket_receive_* *, z tą różnicą, że dane przychodzące są odszyfrowywane i weryfikowane przez stos TLS przed zwróceniem w strukturze pakietów.

### <a name="tls-session-close"></a>Zamykanie sesji TLS

Po zakończeniu sesji TLS zarówno klient protokołu TLS, jak i serwer muszą wysłać Alert CloseNotify po drugiej stronie w celu zamknięcia sesji. Obie strony muszą odebrać i przetworzyć alert, aby upewnić się, że pomyślnie zamknięto sesję.

Jeśli host zdalny wyśle alert CloseNotify, wszystkie wywołania usługi ***nx_secure_tls_session_receive** _ przetworzy alert, wyśle odpowiedni alert z powrotem do hosta zdalnego i zwróci wartość _ *_NX_SECURE_TLS_SESSION_CLOSED_* *. Po zamknięciu sesji wszelkie dalsze próby wysłania lub odebrania danych z tą sesją TLS zakończą się niepowodzeniem.

Jeśli aplikacja chce zamknąć sesję TLS, należy wywołać usługę ***nx_secure_tls_session_end** _. Usługa wyśle alert CloseNotify i przetworzy CloseNotify odpowiedzi. Jeśli odpowiedź nie zostanie odebrana, zostanie zwrócona wartość błędu _ *_NX_SECURE_TLS_SESSION_CLOSE_FAIL_**, co oznacza, że sesja TLS nie została czysto ZAMKNIĘTA, możliwe naruszenie zabezpieczeń.

### <a name="tls-alerts"></a>Alerty protokołu TLS

Protokół TLS został zaprojektowany w celu zapewnienia maksymalnego poziomu zabezpieczeń, dlatego każde zachowanie errant w protokole jest uznawane za potencjalne naruszenie zabezpieczeń. Z tego powodu wszelkie błędy związane z przetwarzaniem komunikatów lub szyfrowaniem/odszyfrowywaniem są uznawane za błędy krytyczne, które natychmiast przerywają uzgadnianie lub sesję.

Podczas obsługi błędów w aplikacji lokalnej jest stosunkowo prosta, a host zdalny musi wiedzieć, że wystąpił błąd w celu prawidłowego obsłużenia tej sytuacji i zapobiegania wszelkim możliwym naruszeniom zabezpieczeń. Z tego powodu protokół TLS wyśle komunikat o *alercie* do hosta zdalnego w przypadku jakiegokolwiek błędu.

Alerty są traktowane w taki sam sposób jak inne komunikaty TLS i szyfrowane podczas sesji, aby zapobiec zbieraniu informacji przez osobę atakującą z typu dostarczonego alertu. W trakcie uzgadniania wysyłane alerty są ograniczone do zakresu, aby ograniczyć ilość informacji, które mogą zostać uzyskane przez potencjalną osobę atakującą.

Alert CloseNotify używany do zamykania sesji TLS jest jedynym alertem niekrytycznym. Mimo że jest on traktowany jako alert i wysyłany jako komunikat alertu, CloseNotify jest w przeciwieństwie do innych alertów, w tym nie wskazuje, że wystąpił błąd.

Wartość alertu i "poziom" (poziomy to "ostrzeżenie" i "krytyczny" — większość alertów protokołu TLS jest "krytyczna") zdefiniowanych w specyfikacjach RFC protokołu TLS i wskazuje typ błędu, który wystąpił. Większość alertów protokołu TLS innych niż CloseNotify może być traktowana jako wskazanie potencjalnego problemu z zabezpieczeniami i spowoduje przerwanie sesji TLS lub uzgadnianie. Jeśli dowolne wywołanie API protokołu TLS zwróci wartość **NX_SECURE_TLS_ALERT_RECEIVED** (0x114), usługa interfejsu API **_nx_secure_tls_session_alert_value_get_** (Nowość w NetX SECURE TLS w wersji 5,12) może zostać użyta do pobrania wartości alertu TLS i poziomu dla aplikacji do użycia w przypadku wszelkich decyzji dotyczących odpowiedzi na problemy z zabezpieczeniami. W większości przypadków każdy alert otrzymany z hosta zdalnego innego niż CloseNotify powinien być traktowany jako błąd krytyczny, chociaż istnieje kilka excptions — Aby uzyskać więcej informacji, zobacz specyfikacje RFC protokołu TLS.

### <a name="tls-session-renegotiation"></a>Ponowne negocjowanie sesji TLS

Protokół TLS obsługuje pojęcie "renegocjacji", która jest po prostu ponowną negocjacją parametrów sesji TLS w kontekście istniejącej sesji TLS. To oznacza, że nowe komunikaty uzgadniania są szyfrowane i uwierzytelniane przy użyciu istniejącej sesji. Ponowna negocjacja jest używana, gdy host TLS chce generować nowe parametry sesji (np. generować nowe klucze sesji TLS) bez konieczności kończenia istniejącej sesji. Na przykład ponowne negocjowanie może być pożądane, gdy zasady zabezpieczeń aplikacji określają, że klucze sesji są używane tylko przez ograniczony czas, ale sesja TLS pozostaje aktywna poza tym czasem.

Jednym problemem związanym z ponowną negocjacją sesji jest to, że protokół TLS jest narażony na określony atak typu man-in-the-Middle, w którym osoba atakująca może przekonać serwer do zainicjowania renegocjacji z nowymi parametrami, dzięki czemu osoba atakująca będzie mogła przejąć daną sesję TLS. Aby uniknąć tego problemu, wprowadzono rozszerzenie "oznaczenie bezpiecznego ponownego negocjowania" (Zobacz błąd sekcji). **Nie znaleziono źródła odwołania.** sekcja).

Protokół Secure TLS NetX całkowicie obsługuje ponowną negocjację sesji oraz rozszerzenie zabezpieczeń dotyczące bezpiecznego ponownego negocjowania.

Podczas otrzymywania danych z hosta zdalnego renegotations (i rozszerzenie) są obsługiwane automatycznie bez interakcji z aplikacją. Jeśli pożądane jest powiadomienie dotyczące ponownych negocjacji sesji, do usługi *nx_secure_tls_session_renegotiate_callback_set* może zostać dostarczone wywołanie zwrotne renegocjacji. Wywołanie zwrotne zostanie wywołane po każdym ponownym negocjowaniu żądania przez hosta zdalnego, co umożliwi aplikacji wykonanie akcji w razie potrzeby.

Aby zainicjować ponowną negocjację z aktywnej sesji protokołu TLS, po prostu Wywołaj usługę *nx_secure_tls_session_renegotiate* na ŻĄDANEJ sesji TLS.

### <a name="tls-session-resumption"></a>Wznawianie sesji protokołu TLS

Wznowienie sesji protokołu TLS nie powinno być pomylone z ponowną negocjacją sesji pomimo pewnych podobieństw. Gdy ponowne *negocjowanie* sesji obejmuje rozpoczęcie nowego uzgadniania w istniejącej sesji protokołu TLS, *wznowienie* sesji jest funkcją opcjonalną, która polega na ponownym uruchomieniu zamkniętej sesji TLS bez wykonywania pełnej uzgadniania protokołu TLS. Aby to osiągnąć, implementacja protokołu TLS może buforować parametry sesji i klucze, kojarząc je z *identyfikatorem sesji,* unikatowym identyfikatorem dostarczonym w pierwotnym uzgadnianiu. Dostarczając identyfikator sesji do serwera TLS, klient wskazuje, że poprzednia sesja protokołu TLS między hostami istniała i zakończyła się trochę czasu w przeszłości, i że klient nadal ma stan, aby ponownie ustanowić sesję z ograniczoną uzgadnianiem. Ponieważ klucze sesji są teoretycznie nadal tajne i są znane tylko przez dwóch komunikujących hosta, serwer może uruchomić nową sesję protokołu TLS i pominąć większość normalnej uzgadniania.

Wznawianie sesji może być przydatne, aby uniknąć potencjalnych operacji klucza publicznego używanych do udostępniania głównego klucza tajnego generacji kluczy i weryfikowania sygnatur certyfikatów, ale wymaga również, aby parametry sesji, klucze i stan crypotgraphic były utrzymywane w pamięci dla wszystkich możliwych sesji (co najmniej dla konfigurowalnego przedziału czasu).

Bieżąca wersja NetX Secure TLS nie obsługuje wznawiania sesji — identyfikator sesji jest po prostu ignorowany przez serwery TLS i klienci TLS zawsze muszą podawać identyfikator sesji o wartości NULL, który powoduje, że serwer ma wykonać pełną uzgadnianie. Brak wznowienia sesji nie powinien powodować problemów między procesami, ponieważ jest to całkowicie opcjonalna funkcja, a wszystkie implementacje protokołu TLS muszą domyślnie mieć wartość Ukończ uzgadnianie, jeśli identyfikator sesji jest równy NULL lub nie został rozpoznany.

### <a name="protocol-layering"></a>Warstwy protokołu

Protokół TLS pasuje do stosu sieciowego między warstwą transportu (np. TCP) i warstwą aplikacji. Protokół TLS jest czasami traktowany jako oparty na protokole transportowym (transport *Layer* Security), ale ponieważ działa jako aplikacja w odniesieniu do podstawowych protokołów sieciowych (takich jak TCP), ale czasami jest zgrupowana na warstwę aplikacji.

Protokół TLS wymaga protokołu warstwy transportowej, który obsługuje dostarczanie w kolejności i bezstratne, takie jak TCP. Ze względu na to wymaganie protokół TLS nie może działać na podstawie protokołu UDP, ponieważ protokół UDP nie gwarantuje dostarczania datagramów. Oddzielny protokół o nazwie *DTLS,* który jest zmodyfikowaną wersją protokołu TLS, jest używany w przypadku aplikacji wymagających zabezpieczeń TLS za pośrednictwem protokołu datagramu, takiego jak UDP. NetX Secure obsługuje DTLS, ale Dokumentacja dla DTLS jest oddzielona od tego dokumentu.

![Diagram warstw protokołu TCP/IP i TLS.](media/image6.png)

Rysunek 5 — warstwy protokołów TCP/IP i TLS

## <a name="network-communications-security"></a>Zabezpieczenia komunikacji sieciowej

Zabezpieczanie komunikacji za pośrednictwem sieci publicznych oraz Internet jest ważnym tematem i tematem ogromnej liczby książek, artykułów i rozwiązań. Temat jest bogglingly złożony, ale może być zredukowany do prostego pomysłu: wysłanie informacji za pośrednictwem sieci, tak aby tylko przewidziany obiekt docelowy mógł uzyskać dostęp do tych informacji lub je zmienić. Ten podział na trzy ważne koncepcje: utajnienie, integralność i uwierzytelnianie. Protokół TLS zawiera rozwiązania dla wszystkich trzech.

### <a name="secrecy"></a>Są

Podczas wysyłania danych przez sieć często ważne jest, aby dane nie były uzyskiwane przez złośliwą jednostkę. Jeśli dane są wysyłane za pośrednictwem połączenia TCP/IP, każda osoba mająca dostęp do sieci będzie mogła odczytywać te dane przy użyciu łatwo dostępnych narzędzi sieciowych. Aby zapobiec uzyskiwaniu tych danych, należy je zakodować, aby nie można było ich odczytać z wyjątkiem zamierzonego celu — jest to *utajnienie.* W protokole TLS algorytmy szyfrowania, takie jak RSA i AES, zapewniają tajemnicę.

### <a name="integrity"></a>Integralność

Czasami utajnienie ochrony danych odbywa się za pośrednictwem sieci, co jest niewystarczające. W niektórych przypadkach może być możliwe, aby złośliwa jednostka mogła zmienić zawartość pakietu TCP bez konieczności znajomości tego, co zawiera pakiet. Zaszyfrowane dane można zmienić, renderowanie nieprawidłowego lub zmiany parametrów komunikatu prowadzącego do dowolnych wyników, które osoba atakująca może chcieć osiągnąć. W sieci firma Microsoft nie może zapobiec zmianie danych podczas przesyłania przez osobę atakującą, ale możemy udostępnić mechanizm, aby dowiedzieć się, czy dane zostały zmienione. Gdy dane są zmieniane podczas przesyłania, będą znane i można odrzucić dane. Jest to koncepcja *spójna*. W protokole TLS integralność jest zapewniana przez klasę procedur kryptograficznych znanych jako *funkcje skrótu*. Niektóre przykłady funkcji mieszania to MD5 i SHA-1.

### <a name="authentication"></a>Authentication

Trzecia ważna koncepcja zabezpieczeń komunikacji sieciowej polega na tym, że dane powinny być przekazywane tylko do zamierzonego celu. Osoba atakująca może próbować stworzyć jako uprawniony podmiot do odbierania danych przeznaczonych dla innego hosta. Nawet jeśli dane są wysyłane z mechanizmami zachowania poufności i integralności, osoba atakująca może nadal mieć możliwość osiągnięcia żądanego wyniku (bezpieczeństwo komunikacji) przez ten proces. Aby tego uniknąć, mechanizm jest wymagany do potwierdzenia tożsamości hosta zdalnego przed wysłaniem poufnych danych. Proces potwierdzania tożsamości hosta zdalnego jest *uwierzytelniany.* W protokole TLS uwierzytelnianie jest zapewniane przy użyciu certyfikatów cyfrowych, funkcji skrótu i mechanizmu zwanego *podpisami cyfrowymi* , które korzystają z właściwości szyfrowania klucza publicznego (opisanych poniżej). Za pomocą *klucza wstępnego* (PSK) można również uzyskać ograniczoną, ale przydatną formę uwierzytelniania.

## <a name="tls-encryption"></a>Szyfrowanie TLS

Protokół TLS jest strukturą zapewniającą bezpieczną komunikację sieciową za pośrednictwem Internetu wykorzystującego szyfrowanie. Szyfrowanie jest ogólnie zdefiniowane jako proces kodowania danych w taki sposób, że uzyskanie oryginalnych danych (lub informacji o tych danych) jest bardziej trudne, bez *klucza*. W systemach komputerowych szyfrowanie jest oparte na złożonych matematykach, takich jak ograniczone pola i można je klasyfikować do dwóch typów: *klucza prywatnego* (lub *szyfrowania symetrycznego*) i *klucza publicznego* (lub *szyfrowania asymetrycznego*). Przykładami szyfrowania klucza prywatnego są AES (Advanced Encryption Standard) i RC4 (Rivest cipher 4). Przykładami szyfrowania klucza publicznego są RSA (Rivest, Shamir, Adleson) i Diffie-Hellman szyfrów.

Protokół TLS wykorzystuje zarówno procedury szyfrowania klucza prywatnego, jak i klucza publicznego, aby zapewnić balans wydajności, zabezpieczenia i elastyczność.

### <a name="private-key-encryption"></a>Szyfrowanie Private-Key

Szyfrowanie klucza prywatnego jest używane przez tysiące lat. Podstawowe szyfrowanie podstawiania (gdzie litera lub wyraz jest zastępowana przez inną niepokrewną literę lub słowo) to najstarsze znane przykłady szyfrowania, ale z pojawieniu szyfrowanie klucza prywatnego w wieku informacji znacznie Ulepszono.

Szyfr klucza prywatnego używa "klucza", który jest po prostu wartością (która może być słowem, frazą lub cyfrą w ogólnym przypadku), która jest używana do dodanego sposobu kodowania niektórych danych, tak aby tylko jednostka, która miała dostęp do tego klucza, mogła zdekodować dane w zrozumiały sposób. Klucz służy do szyfrowania i odszyfrowywania danych, a tym samym *szyfrowania symetrycznego*.

Szyfry klucza prywatnego są generalnie szybkie i stosunkowo proste do zaimplementowania, nawet jeśli te matematyczne przekroczenia są bardziej skomplikowane. Z tego powodu protokół TLS używa szyfrów kluczy prywatnych do masowej bezpiecznej komunikacji.

Jednak szyfrowanie klucza prywatnego ma problem podczas próby zastosowania go do ogólnej komunikacji sieciowej komputera: klucz musi być współużytkowany między obiema komputerami próbującymi komunikować się. Ogólnie rzecz biorąc, niepraktyczne i często nie można prawidłowo komunikować klucza prywatnego między dwoma komputerami w Internecie, ponieważ może być zakładany, że ruch sieciowy może być uzyskiwany przez dowolną liczbę jednostek w różnych przeskokach, które są wykonywane podczas routingu przez Internet. Jeśli klucz jest uzyskiwany przez złośliwą jednostkę, wszystkie dane zaszyfrowane za pomocą tego klucza zostaną naruszone. Ponieważ większość maszyn w Internecie ma tylko połączenie sieciowe, a nie inny bezpieczny kanał na potrzeby komunikacji, wysyłanie kluczy przez sieć jest tantamount do wysyłania nieszyfrowanych danych — nie zapewnia żadnych zabezpieczeń.

Z tego powodu szyfrowanie klucza prywatnego nie jest wystarczające do wdrożenia protokołu zabezpieczeń komunikacji sieciowej ogólnego przeznaczenia. Jest to miejsce, w którym może pomóc szyfrowanie klucza publicznego.

NetX Secure TLS obsługuje szyfrowanie klucza prywatnego AES.

### <a name="public-key-encryption"></a>Szyfrowanie Public-Key

W przeciwieństwie do szyfrowania klucza prywatnego szyfrowanie klucza publicznego to dość nowe pojęcie, które zostało opracowane w 1970 r. W przypadku użycia koncepcji zwanej "funkcjami" podlewek "i" pułapki ", stwierdzono, że istnieje sposób udostępniania klucza przez sieć bez naruszania zabezpieczeń zaszyfrowanych danych.

Sposób działania szyfrowania klucza publicznego polega na tym, że klucz (w powyższym sensie szyfrowania kluczem prywatnym) jest podzielony na dwie części, *klucz prywatny* i *klucz publiczny*, z którego jest pobierana nazwa klucza publicznego. Koncepcja polega na tym, że jeden z tych kluczy (zazwyczaj klucz publiczny) jest używany do szyfrowania, podczas gdy drugi jest używany do odszyfrowywania. Ta wartość asymetrii kluczy jest przyczyną drugiej nazwy szyfrowania klucza publicznego: *szyfrowania asymetrycznego*.

Matematyka za szyfrowaniem klucza publicznego jest dość złożona, ale pomysłem jest, że klucz publiczny może być używany *tylko* do szyfrowania i uzyskanie tego klucza nie zezwala na uzyskiwanie zaszyfrowanych danych. Z kolei klucz prywatny jest jedynym sposobem odszyfrowania danych zaszyfrowanych przy użyciu klucza publicznego. W ten sposób przez utrzymywanie tajnego klucza prywatnego każda osoba, która chce bezpiecznie komunikować się z właścicielem tego klucza prywatnego, musi tylko szyfrować dane przy użyciu odpowiedniego klucza publicznego z wiedzą, że tylko ktoś w posiadaniu tego klucza prywatnego może uzyskać bezpieczne dane.

NetX Secure TLS obsługuje szyfrowanie klucza publicznego RSA.

> [!IMPORTANT] 
> *Klucz RSA to bardzo duże użycie procesora, jeśli jest używana implementacja RSA oprogramowania. Większe rozmiary kluczy zwiększają moc obliczeniową wymaganą przez współczynnik kwadratowy — w przypadku dwukrotnego wzrostu rozmiaru klucza.*

### <a name="public-key-authentication"></a>Uwierzytelnianie Public-Key

Interesujący efekt działania koncepcji szyfrowania klucza publicznego polega na tym, że można go użyć do zapewnienia uwierzytelniania oraz szyfrowania przez wykonanie operacji w odwrotnej postaci: szyfrowanie przy użyciu klucza *prywatnego* i odszyfrowywanie przy użyciu klucza *publicznego* . Rzeczywisty mechanizm wykonywania tej czynności zależy od używanego algorytmu klucza publicznego, ale koncepcja jest taka sama.

W celu uwierzytelnienia przy użyciu uwierzytelniania za pomocą klucza publicznego właściciel klucza prywatnego szyfruje niektóre dane (zazwyczaj skrót kryptograficzny danych do uwierzytelnienia) przy użyciu tego klucza prywatnego. Następnie ktoś chcący uwierzytelniać dane pochodzące od właściciela klucza prywatnego za pomocą skojarzonego klucza publicznego do odszyfrowania danych — w przypadku pomyślnego odszyfrowania i zaakceptowania przez użytkownika wiarygodności tego klucza publicznego użytkownik może mieć pewność, że dane pochodzą od właściciela klucza prywatnego.

W protokole TLS uwierzytelnianie klucza publicznego służy do sprawdzania poprawności certyfikatu cyfrowego dostarczonego przez serwer TLS (oraz opcjonalnie klienta protokołu TLS) przy użyciu kluczy publicznych z zaufanego magazynu certyfikatów. Certyfikat jest sprawdzany pod kątem klucza publicznego w magazynie, a dane w certyfikacie są używane do sprawdzenia tożsamości serwera.

NetX Secure TLS obsługuje uwierzytelnianie RSA.

### <a name="cryptographic-hashing"></a>Mieszanie kryptograficzne

Szyfrowanie nie jest jedyną operacją kryptograficzną używaną w protokole TLS. Aby zapewnić integralność komunikatów podczas sesji TLS, należy uzyskać sumę kontrolną, aby upewnić się, że zawartość komunikatu nie została naruszona. Jednak prostą sumę kontrolną (używaną w protokole TCP) nie wystarczą do zagwarantowania akceptowalnego poziomu integralności, ponieważ może on być łatwo przeczytany przez osobę atakującą. Mechanizm używany przez protokół TLS w celu zapewnienia integralności komunikatów jest znany jako *skrót kryptograficzny*.

Szyfrowanie jest kodowaniem 1:1 — to oznacza, że wszystkie oryginalne dane można uzyskać z zaszyfrowanych danych. Jednak skrót mapuje dowolną ilość danych do wartości o ustalonym rozmiarze, podobnie jak suma kontrolna. W przeciwieństwie do prostej sumy kontrolnej, skrót jest specjalnie zaprojektowany w celu ograniczenia *kolizji*, gdzie różne dane wejściowe są w tym samym wyniku. W przypadku prostej sumy kontrolnej, jeśli bit zostanie przerzucony z 1 do 0 i inny bit od 0 do 1, suma kontrolna jest taka sama. W przypadku użycia skrótu kryptograficznego dane wyjściowe różnią się znacznie, co utrudnia osobie atakującej zmianę danych skrótów i wykonywanie operacji skrótu dla zmienionych danych nadal będzie miało taką samą wartość (i w związku z tym fałszywe sprawdzanie integralności tych danych).

Protokół TLS używa wielu różnych algorytmów wyznaczania wartości skrótu w celu zapewnienia integralności komunikatów, komunikatów aplikacji i komunikatów kontroli protokołu TLS. Należą do nich MD5, SHA-1 i SHA-256.

NetX Secure TLS obsługuje funkcję mieszania MD5, SHA-1 i SHA-256.

## <a name="tls-extensions"></a>Rozszerzenia protokołu TLS

Protokół TLS udostępnia wiele rozszerzeń zapewniających dodatkowe funkcje dla niektórych aplikacji. Te rozszerzenia są zwykle wysyłane jako część komunikatów komunikacie ClientHello lub ServerHello, co oznacza, że host zdalny chce użyć rozszerzenia lub podać dodatkowe szczegóły do użycia podczas ustanawiania bezpiecznej sesji protokołu TLS.

Ogólnie rzecz biorąc, rozszerzenia udostępniają opcjonalne parametry do protokołu TLS na początku uzgadniania, które kierują operacje dokonywania. Niektóre rozszerzenia wymagają wprowadzenia do aplikacji lub podejmowania decyzji, podczas gdy inne są obsługiwane automatycznie.

W poniższej tabeli opisano rozszerzenia protokołu TLS aktualnie obsługiwane przez NetX Secure TLS:

| **Nazwa rozszerzenia**              | **Opis**              |
| ------------------------------- |----------------------------- |
| Wskazanie bezpiecznego ponownego negocjowania | To rozszerzenie ogranicza ataki typu man-in-the-Middle, które mogą wystąpić podczas uzgadniania renegocjacji.|
| Oznaczanie nazwy serwera          | To rozszerzenie umożliwia klientowi protokołu TLS dostarczenie określonej nazwy DNS serwerowi TLS, co umożliwia serwerowi wybranie poprawnych poświadczeń (zakłada, że serwer ma wiele certyfikatów tożsamości i punktu wejścia sieci). |
| Algorytmy sygnatur            | To rozszerzenie umożliwia klientowi protokołu TLS udostępnienie listy akceptowalnych algorytmów sygnatur i wyznaczania wartości skrótu na serwerze TLS. |

Omówienie obsługiwanych rozszerzeń protokołu TLS

### <a name="secure-renegotiation-indication"></a>Wskazanie bezpiecznego ponownego negocjowania

Protokół TLS obsługuje uzgadnianie w ramach istniejącej sesji TLS przy użyciu ustanowionej sesji do szyfrowania komunikatów uzgadniania. Ten proces umożliwia ponowne ustanowienie kluczy sesji kryptograficznej bez kończenia sesji TLS (patrz sekcja "renegocjowanie sesji TLS").

Niestety, gdy protokół TLS był używany do ponownej negocjacji przez jakiś czas, okazało się, że wystąpił Luka w zabezpieczeniach ataku typu man-in-the-Middle, który korzystał z funkcji renegocjacji. Aby zamknąć luki w zabezpieczeniach, wprowadzono rozszerzenie "oznaczenie bezpiecznego ponownego negocjowania". W związku z tym rozszerzenie Secure renegocjacji używa skrótu gotowego komunikatu z ustalonego połączenia, aby sprawdzić, czy oryginalne hosty uczestniczą w uzgadnianiu renegocjacji — w związku z tym skrót jest używany jako token weryfikacyjny w założeniu, że osoba atakująca nie będzie w stanie sfałszować skrótu (co wymagałoby dostępu do kluczy sesji).

NetX Secure TLS obsługuje automatyczne ponowne negocjowanie i domyślnie używa rozszerzenia Secure renegocjacji. Interakcja aplikacji nie jest wymagana.

### <a name="server-name-indication"></a>Oznaczanie nazwy serwera

Podczas uzgadniania protokołu TLS klient protokołu TLS oczekuje serwera zdalnego, aby zapewnić certyfikat tożsamości, aby klient mógł uwierzytelnić serwer. Mogą jednak wystąpić sytuacje, w których serwer dostarczy wiele różnych usług z różnymi serwerami wirtualnymi z każdym unikatowymi tożsamościami. W przypadku pojedynczego serwera z wieloma tożsamościami klient protokołu TLS może podać określoną nazwę DNS, która będzie używana przez serwer do wybrania odpowiednich poświadczeń — mechanizm dostarczania tej nazwy jest rozszerzeniem Oznaczanie nazwy serwera (SNI).

W przypadku aplikacji używającej rozszerzenia SNI wymagane jest pewne interakcje. W przypadku klientów TLS aplikacja musi podać nazwę DNS do wysłania do serwera zdalnego. W przypadku serwerów TLS aplikacja musi odczytać nazwę DNS z rozszerzenia i wybrać odpowiedni certyfikat, aby wysłać z powrotem do klienta.

W poniższych sekcjach zawarto więcej szczegółowych informacji na temat używania rozszerzenia SNI w NetX Secure TLS.

### <a name="sni-extension--tls-client"></a>Rozszerzenie SNI — klient TLS

Klient usługi NetX Secure TLS chcący użyć rozszerzenia SNI musi podać nazwę DNS, która ma zostać dostarczona podczas uzgadniania. Ta nazwa musi zostać zainicjowana i dostarczona przed rozpoczęciem sesji TLS od momentu wysłania rozszerzenia w komunikacie komunikacie ClientHello, który uruchamia proces uzgadniania.

Poniższy fragment kodu ilustruje użycie rozszerzenia. Najpierw obiekt NX_SECURE_X509_DNS_NAME jest inicjowany z żądaną nazwą serwera. Następnie, przed rozpoczęciem sesji TLS, nazwa jest dostarczana do protokołu TLS przy użyciu interfejsu API rozszerzenia SNI. Po ustawieniu nazwy nie są wymagane żadne dalsze akcje. Zobacz informacje o interfejsie API w rozdziale 4  
  
Opis usług NetX Secure Services, aby uzyskać więcej informacji na temat poszczególnych funkcji.

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

Po stronie serwera TLS rozszerzenie SNI może być przetwarzane przez aplikację w celu wybrania odpowiednich poświadczeń (np. certyfikatów) do dostarczenia klientom zdalnym podczas uzgadniania. W tym celu aplikacja musi dostarczyć wywołanie zwrotne sesji, które jest wywoływane po odebraniu komunikatu komunikacie ClientHello.

Przykładowy kod dla interfejsu API nx_secure_tls_session_server_callback_set (patrz strona 122) ilustruje analizowanie przychodzącego rozszerzenia SNI przy użyciu wywołania zwrotnego serwera. Zasadniczo serwer TLS odbiera komunikacie ClientHello i wywołuje wywołanie zwrotne. Następnie aplikacja używa interfejsu API *nx_secure_tls_session_sni_extension_parse* , aby przeanalizować dane rozszerzenia dostarczone do wywołania zwrotnego, aby znaleźć rozszerzenie SNI i zwrócić podaną nazwę DNS (należy zauważyć, że rozszerzenie obsługuje tylko pojedynczą nazwę DNS). Po uzyskaniu nazwy aplikacja używa jej do znajdowania i wysyłania odpowiedniego certyfikatu tożsamości serwera (i łańcucha wystawcy, jeśli ma zastosowanie).

### <a name="signature-algorithms-extension"></a>Rozszerzenie algorytmów sygnatur

To rozszerzenie jest specyficzne dla protokołu TLS 1,2 i umożliwia klientowi protokołu TLS udostępnienie listy akceptowalnych par algorytmów sygnatur i wyznaczania wartości skrótu, które są akceptowane do użycia podczas generowania i weryfikowania podpisów cyfrowych. Lista jest generowana automatycznie przez NetX bezpiecznego protokołu TLS dla klientów TLS przy użyciu tabeli szyfru dostarczonej do *nx_secure_tls_session_create*. Interakcja aplikacji nie jest wymagana.

## <a name="authentication-methods"></a>Metody uwierzytelniania

Protokół TLS oferuje strukturę służącą do ustanawiania bezpiecznego połączenia między dwoma urządzeniami za pośrednictwem niezabezpieczonej sieci, ale część problemu ma na celu zapoznania się z tożsamością urządzenia na drugim końcu tego połączenia. Bez mechanizmu uwierzytelniania tożsamości hostów zdalnych, jest to prosta operacja dla osoby atakującej, która będzie stanowić zaufane urządzenie.

Początkowo może się wydawać, że korzystanie z adresów IP, sprzętowych adresów MAC lub systemu DNS zapewni stosunkowo wysoki poziom zaufania do identyfikowania hostów w sieci, ale z uwzględnieniem rodzaju technologii TCP/IP i prostoty, z jakimi adresami mogą być sfałszowane i wpisy DNS są uszkodzone (np

Istnieją różne mechanizmy, które mogą zapewnić tę dodatkową warstwę uwierzytelniania dla protokołu TLS, ale najbardziej typowym *certyfikatem cyfrowym.* Inne mechanizmy obejmują klucze wstępne (PSK) i schematy haseł.

### <a name="digital-cerificates"></a>Digital instalowane

Certyfikaty cyfrowe są najczęściej spotykaną metodą uwierzytelniania hosta zdalnego w protokole TLS. Zasadniczo certyfikat cyfrowy to dokument z określonym formatowaniem, który zawiera informacje o tożsamości dla urządzenia w sieci komputerowej.

Protokół TLS zwykle korzysta z formatu o nazwie X. 509, który jest standardem opracowanym przez międzynarodowy związek telekomunikacyjny, ale inne formaty certyfikatów mogą być używane, Jeśli hosty TLS mogą wyrazić zgodę na używany format. X. 509 definiuje określony format certyfikatów i różnych kodowań, których można użyć do utworzenia dokumentu cyfrowego. Większość certyfikatów X. 509 używanych z protokołem TLS jest zakodowana przy użyciu wariantu numeru ASN 1, innego standardu telekomunikacyjnego. W ASN. 1 istnieje różne kodowanie cyfrowe, ale najpopularniejsze kodowanie certyfikatów TLS jest standardem Distinguished Encoding Rules (DER). DER to uproszczony podzbiór podstawowych reguł kodowania ASN. 1, które zostały zaprojektowane jako niejednoznaczne, co ułatwia analizowanie. W sieci, certyfikaty TLS są zwykle zakodowane w formacie binarnym DER i jest to format, który NetX bezpiecznego dla certyfikatów X. 509.

Certyfikaty binarne w formacie DER są używane w rzeczywistym protokole TLS, ale mogą być generowane i przechowywane w wielu różnych kodowaniach, z rozszerzeniami plików, takimi jak PEM, CRT i. p12. Różne warianty są używane przez różne aplikacje od różnych producentów, ale ogólnie wszystkie mogą być konwertowane na algorytm DER przy użyciu szeroko dostępnych narzędzi.

Najbardziej typowymi alternatywami kodowania certyfikatów jest PEM. Format PEM (z Privacy-Enhanced mail) jest zakodowaną w oparciu o wersję 64 kodowaniem algorytmu DER, która jest często używana, ponieważ kodowanie skutkuje tekstem drukowalnym, który można łatwo wysyłać przy użyciu poczty e-mail lub protokołów opartych na sieci Web.

Generowanie certyfikatu dla bezpiecznej aplikacji NetX jest zwykle poza zakresem tego podręcznika, ale narzędzie wiersza polecenia OpenSSL ([www.OpenSSL.org](http://www.openssl.org)) jest szeroko dostępne i może być konwertowane między większością formatów.

W zależności od aplikacji można generować własne certyfikaty, otrzymywać certyfikaty od producenta lub organizacji rządowej lub zakupić certyfikaty od komercyjnego urzędu certyfikacji.

Aby użyć certyfikatu cyfrowego w bezpiecznej aplikacji NetX, musisz najpierw przekonwertować certyfikat na format binarny DER, a opcjonalnie przekonwertować skojarzony klucz prywatny ("wykładnik prywatny" dla RSA, na przykład) na format binarny, zazwyczaj w formacie PKCS # 1 — sformatowany klucz RSA lub klucz ECC szyfrowany algorytmem DER. Po zakończeniu konwersji załadujesz certyfikat i klucz prywatny na urządzeniu. Możliwe opcje obejmują używanie systemu plików opartego na technologii Flash lub generowanie macierzy C na podstawie danych (za pomocą narzędzia takiego jak "XXD" w systemie Linux) i kompilowanie certyfikatu i klucza w aplikacji jako danych stałych.

Po załadowaniu certyfikatu na urządzenie można użyć interfejsu API protokołu TLS do skojarzenia certyfikatu z sesją TLS.

Aby uzyskać szczegółowe informacje i przykłady użycia certyfikatów X. 509 z protokołem Secure TLS NetX, zobacz sekcję "Importowanie certyfikatów X. 509 do usługi NetX Secure".

Aby uzyskać więcej informacji, zapoznaj się z następującymi usługami TLS w dokumentacji interfejsu API:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_local_certificate_remove
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_trusted_certificate_add
- nx_secure_trusted_certificate_remove

### <a name="tls-client-certificate-specifics"></a>Specyficzne dla certyfikatu klienta TLS

Implementacje klientów TLS zwykle nie wymagają od "lokalnego" certyfikatu<sup>14</sup> do załadowania na urządzenie. Wyjątkiem jest to, kiedy uwierzytelnianie certyfikatu klienta jest włączone, ale jest to znacznie mniej typowe.

Klient TLS wymaga załadowania co najmniej jednego "zaufanego" certyfikatu<sup>15</sup> (w razie potrzeby może być załadowany) i miejsca na "zdalny" certyfikat<sup>16</sup> do przydzielenia.

Aby uzyskać więcej informacji na temat dodawania zaufanych certyfikatów i przydzielania miejsca dla certyfikatów zdalnych, zobacz Dokumentacja interfejsu API protokołu TLS dla następujących usług: nx_secure_tls_remote_certificate_allocate, nx_secure_tls_trusted_certificate_add.

14. "Lokalny" certyfikat jest certyfikatem, który identyfikuje urządzenie lokalne — czyli zawiera informacje o tożsamości dla urządzenia, na którym załadowana jest aplikacja TLS.

15. "Zaufany" certyfikat to certyfikat, który stanowi podstawę do zaufania i uwierzytelniania urządzenia zdalnego, bezpośrednio lub za pomocą infrastruktury kluczy publicznych (PKI). Katalog główny łańcucha zaufania jest zwykle nazywany "urzędem certyfikacji" lub certyfikatem urzędu certyfikacji.

16. Certyfikat "zdalny" odnosi się do certyfikatu wysyłanego przez hosta zdalnego podczas uzgadniania TLS. Zapewnia tożsamość dla tego hosta zdalnego i jest uwierzytelniany przez porównanie go z certyfikatem "zaufany" na urządzeniu lokalnym.

### <a name="tls-server-certificate-specifics"></a>Specyficzne dla certyfikatu serwera TLS

Implementacje serwera TLS zwykle nie wymagają od "zaufanych" certyfikatów do załadowania na urządzenie lub certyfikaty zdalne do przydzielenia. Wyjątkiem od tego, kiedy jest włączone uwierzytelnianie certyfikatu klienta (jest to mniej typowe).

Serwer TLS wymaga załadowania certyfikatu "Local", aby serwer mógł udostępnić go klientowi zdalnemu podczas uzgadniania protokołu TLS w celu uwierzytelnienia serwera na komputerze klienckim.

Aby uzyskać więcej informacji na temat ładowania certyfikatów lokalnych do użycia z aplikacjami serwera NetX TLS, zobacz Dokumentacja interfejsu API dla następujących usług: 
- nx_secure_tls_local_certificate_add, 
- nx_secure_tls_local_certificate_remove.

### <a name="pre-shared-keys-psk"></a>Klucze wstępne (PSK)

Alternatywny mechanizm zapewnienia uwierzytelniania tożsamości w protokole TLS jest pojęciem kluczy wstępnych (PSK). Użycie ciphersuite PSK eliminuje konieczność wykonywania operacji szyfrowania klucza publicznego intensywnie korzystających z procesora, Boon dla urządzeń osadzonych z ograniczeniami zasobów. Klucz PSK zastępuje certyfikat w uzgadnianiu protokołu TLS i jest używany zamiast szyfrowanego wstępnego tajnego wpisu do generowania klucza sesji TLS.

Ciphersuites klucza PSK są ograniczone w tym sensie, że wspólny klucz tajny musi być obecny na obu urządzeniach przed ustanowieniem sesji TLS. Oznacza to, że urządzenia muszą zostać załadowane za pomocą tego klucza tajnego, przy użyciu niebezpiecznych środków innych niż połączenie protokołu TLS z certyfikatem PSK — PSKs może zostać zaktualizowany za pośrednictwem połączenia z kluczem PSK protokołu TLS, ale urządzenie musi być uruchamiane z kluczem PSK, który jest ładowany przez inny mechanizm. Na przykład urządzenie czujnika i jego urządzenie bramy mogą zostać załadowane przy użyciu PSKs w fabryce przed wysyłką lub do załadowania klucza PSK przy użyciu standardowego połączenia TLS (z certyfikatem).

Ciphersuites PSK to kilka form, które opisano w dokumencie RFC 4279. W pierwszej kolejności są używane klucze RSA lub Diffie-Hellman, które są używane w taki sam sposób, jak klucze publiczne przesyłane w certyfikacie w standardowym uzgadnianiu protokołu TLS. Drugi formularz, który jest bardziej używany w środowisku z ograniczeniami zasobów, korzysta z klucza PSK, który jest używany do bezpośredniej generacji kluczy sesji (na przykład do użycia przez algorytm AES), unikając korzystania z kosztownych operacji RSA lub Diffie-Hellman.

NetX Secure obsługuje drugą formę klucza PSK ciphersuites, umożliwiając aplikacjom usuwanie wszystkich kodów kryptograficznych i użycie pamięci klucza publicznego. Sam klucz PSK nie jest kluczem AES, ale może być traktowany jak hasło, z którego są generowane rzeczywiste klucze. Istnieje kilka ograniczeń dotyczących tego, co może być wartością klucza PSK, ale dłuższe wartości zapewniają większe bezpieczeństwo (takie same jak w przypadku haseł).

Aby korzystać z klucza PSK w bezpiecznej aplikacji NetX, należy najpierw zdefiniować globalne makro **NX_SECURE_ENABLE_PSK_CIPHERSUITES**. Zwykle odbywa się to za pomocą ustawień kompilatora, ale definicja może być również umieszczona w pliku nagłówkowym nx_secure_tls. h. Po zdefiniowaniu makra obsługa klucza PSK ciphersuite zostanie skompilowana do aplikacji NetX Secure TLS.

W przypadku włączenia obsługi PSK, można użyć interfejsu API TLS do skonfigurowania PSKs dla aplikacji. Każdy PSK będzie wymagał wartości PSK (rzeczywisty klucz tajny) — Zapewnij bezpieczną wartość), wartość "Identity" służącą do identyfikowania określonego klucza PSK oraz "wskazówkę tożsamości", która jest używana przez serwer TLS do wybierania określonej wartości klucza PSK.

Sam PSK może być dowolną wartością binarną, ponieważ nigdy nie jest wysyłana za pośrednictwem połączenia sieciowego. Wartość PSK może być dowolną wartością o długości do 64 bajtów.

Tożsamość i Wskazówka muszą być drukowalne ciągi znaków sformatowane przy użyciu kodowania UTF-8. Wartości Identity i Hint mogą mieć długość do 128 bajtów.

Tożsamość i PSK tworzą unikatową parę, która jest ładowana na każde urządzenie w sieci, które musi komunikować się ze sobą.

"Wskazówka" jest używana głównie do definiowania profilów aplikacji w celu grupowania PSKs przez funkcję lub usługę. Te wartości muszą być uzgadniane z wyprzedzeniem i są zależne od aplikacji. Przykładowo aplikacja serwera wiersza polecenia OpenSSL (z włączonym PSK) używa domyślnego ciągu "Client_identity", który musi być dostarczony przez klienta TLS w celu kontynuowania uzgadniania TLS.

Aby uzyskać więcej informacji na temat PSKs, zobacz Dokumentacja bezpiecznego interfejsu API NetX dla następujących usług: nx_secure_tls_client_psk_set, nx_secure_tls_psk_add.

## <a name="importing-x509-certificates-into-netx-secure"></a>Importowanie certyfikatów X. 509 do NetX Secure

Certyfikaty cyfrowe są wymagane dla większości połączeń TLS w Internecie. Certyfikaty zapewniają metodę uwierzytelniania wcześniej nieznanych hostów za pośrednictwem Internetu przy użyciu zaufanych wystawców, *zwykle nazywanych urzędami certyfikacji lub* urzędami certyfikacji. Aby połączyć NetX bezpieczne urządzenie z usługą w chmurze komercyjnej (taką jak Amazon Web Services), należy zaimportować certyfikaty do aplikacji, ładując je na urządzenie.

Wraz z certyfikatami czasami potrzebny jest również *klucz prywatny* skojarzony z certyfikatem. W niektórych aplikacjach (takich jak klient protokołu TLS, gdy uwierzytelnianie certyfikatu klienta nie jest używane) certyfikat będzie wystarczający, ale jeśli certyfikat jest używany do identyfikowania urządzenia, potrzebny będzie klucz prywatny. Klucze prywatne są zwykle generowane podczas tworzenia certyfikatu i są przechowywane w osobnym pliku, często szyfrowane przy użyciu hasła.

### <a name="certificate-types"></a>Typy certyfikatów

Certyfikaty cyfrowe są zwykle używane do identyfikowania jednostek w sieci, ale w zależności od tego, jak ich aplikacja będzie miała nieco inne właściwości.

### <a name="local-certificates"></a>Certyfikaty lokalne

Na potrzeby tej dokumentacji będziemy odwoływać się do "certyfikatów lokalnych" jako tych certyfikatów, które zapewniają tożsamość dla urządzenia lokalnego (może to być "certyfikat urządzenia"). Te certyfikaty będą udostępniane hostowi zdalnemu, gdy host zdalny żąda uwierzytelnienia urządzenia lokalnego.

### <a name="remote-certificates"></a>Certyfikaty zdalne

W tej dokumentacji "certyfikaty zdalne" odwołują się do tych certyfikatów dostarczonych przez hosta zdalnego w trakcie uzgadniania TLS, gdy ma to zastosowanie. Miejsce dla tych certyfikatów musi być przydzielone lub NetX Secure nie będzie mogła przeanalizować ich ani ukończyć uzgadniania protokołu TLS.

### <a name="signing-certificates"></a>Certyfikaty podpisywania

"Certyfikat podpisywania" służy do cyfrowego podpisywania innych certyfikatów lub danych na potrzeby uwierzytelniania. Te certyfikaty mogą być certyfikatami pośrednimi lub głównymi w infrastrukturze kluczy publicznych (PKI) i zwykle nie są używane do identyfikowania poszczególnych urządzeń lub hostów.

### <a name="root-ca-certificates"></a>Certyfikaty głównego urzędu certyfikacji

"Certyfikaty głównego urzędu certyfikacji" to certyfikaty podpisywania, które stanowią podstawę infrastruktury PKI i są z podpisem własnym, a nie podpisywane przez inny certyfikat podpisywania. Co najmniej jeden certyfikat głównego urzędu certyfikacji jest zwykle wymagany dla klienta protokołu TLS do weryfikowania serwerów zdalnych.

### <a name="certificate-formats"></a>Formaty certyfikatów

Certyfikaty cyfrowe są po prostu plikami zawierającymi dane strukturalne kodowane przy użyciu składni ASN. 1. Istnieją jednak różne formaty, w których mogą być przechowywane certyfikaty i ważne jest, aby przed załadowaniem certyfikatu do NetX bezpiecznej aplikacji.

Najpopularniejsze formaty dla certyfikatów to DER i PEM. Algorytm DER (na *Distinguished Encoding Rules* format ASN. 1) jest formatem binarnym używanym przez protokół TLS podczas wykonywania wstępnego uzgadniania. PEM (from *privacy Enhanced mail*) to podstawowa 64 wersja formatu der, która jest odpowiednia do obsługi poczty e-mail lub wysyłania za pośrednictwem protokołu HTTP w sieci Web. Różni dostawcy używają różnych rozszerzeń nazw plików dla certyfikatów, takich jak "PEM" lub ". CRT" dla certyfikatów PEM i "der" dla certyfikatów DER. Jeśli masz certyfikat i nie wyczyścisz używanego formatu, otwarcie pliku w edytorze tekstów umożliwi określenie typu, ponieważ pliki DER są zakodowane jako binarne, a pliki PEM są zwykłym tekstem ASCII, który zaczyna się od nagłówka "-----BEGIN CERTIFICATE-----".

NetX Secure wymaga, aby certyfikat był w formacie binarnym DER, dlatego przed zaimportowaniem należy przekonwertować certyfikat na format DER. Można to zrobić za pomocą łatwo dostępnych narzędzi, takich jak OpenSSL.

Jeśli potrzebujesz klucza prywatnego dla aplikacji, plik klucza zostanie zakodowany przy użyciu PEM lub DER w określonym formacie (PKCS # 1 dla RSA, RFC 5915 dla ECC). Plik klucza prywatnego należy przekonwertować na algorytm DER przed zaimportowaniem.

Następujące polecenia OpenSSL są podawane jako przykład do konwertowania certyfikatów i plików kluczy RSA do formatu DER wymagane przez NetX Secure (ECC jest podobne — zapoznaj się z dokumentacją OpenSSL).

```C
openssl x509 -inform PEM -in <certificate> -outform DER -out cert.der
openssl x509 -inform PEM -in <root CA cert> -outform DER -out CA_cert.der
openssl rsa -inform PEM -in <private key> -outform DER -out private.key
```
### <a name="private-keys-and-certificates"></a>Klucze prywatne i certyfikaty

W przypadku certyfikatów, które identyfikują urządzenie, skojarzony klucz prywatny musi być załadowany wraz z certyfikatem. Klucz prywatny (może dotyczyć jednego z algorytmów klucza publicznego, takiego jak RSA, Diffie-Hellmana lub kryptografii Elliptic-Curve) jest używany przez serwer TLS do odszyfrowywania przychodzącego materiału klucza ("wstępnego klucza tajnego") z klienta TLS, a tym samym uwierzytelniania samego klienta. W przypadku klienta TLS jest dostarczany certyfikat tożsamości (certyfikat ze skojarzonym kluczem prywatnym), a serwer żąda certyfikatu klienta. klucz prywatny jest używany do uwierzytelniania klienta programu — w przypadku korzystania z klucza prywatnego klient szyfruje token przy użyciu klucz prywatny, który następnie jest odszyfrowywany przez serwer przy użyciu klucz publiczny klienta, który jest dostępny w certyfikacie klienta (w podobny sposób, ale szczegóły są inne).

W NetX Secure usługa *nx_secure_x509_certificate_initialize* jest używana do inicjowania certyfikatu X. 509 (zobacz sekcję "Ładowanie certyfikatów na urządzenie", aby uzyskać więcej informacji), i opcjonalnie Skojarz klucz prywatny z tym certyfikatem.

W przypadku podania klucza prywatnego certyfikat jest oznaczany jako certyfikat "tożsamość" używany do identyfikowania urządzenia. Klucz jest przesyłany jako ciągły binarny obiekt BLOB i Długość z typem skojarzonego klucza. Typ klucza zależy od typu klucza (np. RSA, ECC itp.) i formatu (np. PKCS # 1 DER). Jeśli nie podano klucza, wartość NX_SECURE_X509_KEY_TYPE_NONE (wartość 0x0) może być przekazywana w celu wskazania, że żaden klucz nie jest dostarczany (długość 0 i wskaźnik NX_NULL dla parametru danych osiągnie ten sam efekt).

W poniższej tabeli przedstawiono typy kluczy znane NetX Secure i skojarzony identyfikator typu, który ma zostać przekazana do *nx_secure_x509_certificate_initialize*. Dodatkowe typy kluczy zostaną dodane, ponieważ dodatkowe algorytmy szyfrowania zostaną dodane do NetX Secure.

| Identyfikator                              | Algorytm | Format   | Encoding | Wartość |
| --------------------------------------- | --------- | -------- | -------- | ----- |
| NX_SECURE_X509_KEY_TYPE_NONE            | Brak      | NIE DOTYCZY      | NIE DOTYCZY      | 0x0   |
| NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER   | RSA       | PKCS # 1   | ALGORYTM      | 0x1   |
| NX_SECURE_X509_KEY_TYPE_EC_DER          | ECDSA     | RFC 5915 | ALGORYTM      | 0x2   |

### <a name="user-defined-private-key-types"></a>Typy kluczy prywatnych zdefiniowane przez użytkownika

Wartości identyfikatorów typu klucza dla usługi *nx_secure_x509_certificate_initialize* określają działania podejmowane w momencie dostarczania klucza prywatnego. W przypadku znanych typów wartości znajdują się w zakresie 0x0000 0000 – 0x0000 FFFF (ostatnie 16 bitów z 32-bitową liczbą całkowitą bez znaku). W przypadku platform z niestandardowymi typami kluczy<sup>17</sup> (jak w przypadku niektórych sprzętowych aparatów szyfrowania), typ klucza zdefiniowanego przez użytkownika w zakresie 0x0000 1000 — FFFF (z 16 bitami niezerowymi) może być przekazanie jako typ klucza. W przypadku ustawienia dowolnego z 16 najważniejszych bitów typu klucza dane klucza prywatnego są przekazywane bezpośrednio do odpowiedniej procedury kryptograficznej (np. RSA) podanej w tabeli ciphersuite TLS. Typy kluczy zdefiniowane przez użytkownika nie są analizowane lub w inny sposób przetwarzane przed przekazaniem do procedury kryptograficznej. Ponadto typ klucza zdefiniowanego przez użytkownika również zostanie przesłany do procedury kryptograficznej, aby można było obsługiwać każde odpowiednie przetwarzanie na tym poziomie.

Należy pamiętać, że typy kluczy zdefiniowane przez użytkownika są zwykle używane dla konkretnych platform sprzętowych, które wykorzystują niestandardowe (prawdopodobnie zaszyfrowane) dane klucza. Zazwyczaj oznacza to, że dane klucza są generowane lub kodowane przy użyciu mechanizmu specyficznego dla tego dostawcy sprzętu (lub w przypadku standardu PKCS # 11, określonego standardu). Aby uzyskać więcej informacji, zapoznaj się z dokumentacją platformy sprzętowej.

17. Typy kluczy zdefiniowane przez użytkownika wymagają odpowiedniej niestandardowej procedury kryptograficznej do obsługi niestandardowego formatu klucza. Procedura kryptograficzna musi mieć zgodny algorytm (np. RSA) i być przekazywane do protokołu TLS w tabeli ciphersuite. 

### <a name="loading-certificates-onto-your-device"></a>Ładowanie certyfikatów na urządzenie

Każda metoda ładowania pliku na urządzenie będzie wystarczająca do zaimportowania certyfikatów.

Najprostszą metodą ładowania certyfikatu jest konwertowanie binarnych danych szyfrowanych algorytmem DER na tablicę C i kompilowanie ich do aplikacji jako stałej. Można to łatwo zrobić z narzędziami takimi jak "XXD" w systemie Linux (z opcją "-i").

Alternatywnie można załadować certyfikat do systemu plików Flash lub innych opcji magazynu, o ile można przekazać wskaźnik do danych certyfikatu do bezpiecznego interfejsu API NetX.

### <a name="certificate-files-needed-for-netx-secure"></a>Pliki certyfikatów, które są zbędne do NetX Secure

Pliki certyfikatów, które będą potrzebne do zaimportowania, zależą od aplikacji. Ogólnie rzecz biorąc, serwery TLS wymagają certyfikatu w celu zidentyfikowania urządzenia, a klienci TLS wymagają co najmniej jednego *zaufania zaufanego* do uwierzytelniania serwerów zdalnych. W poniższej tabeli przedstawiono certyfikaty, które są zbędne dla niektórych różnych aplikacji TLS.

| **Funkcje/opcje protokołu TLS**                     | **Wymagany certyfikat/klucze (minimum)**              |
| ------------------------------------------------- | --------------------------------------------------- |
| Klient TLS                                        | Certyfikat głównego urzędu certyfikacji                                 |
| Serwer TLS                                        | Certyfikat lokalny, klucz prywatny dla tego certyfikatu |
| Serwer TLS z uwierzytelnianiem certyfikatu klienta | Certyfikat lokalny, klucz prywatny, główny urząd certyfikacji             |
| Klient TLS z uwierzytelnianiem za pomocą certyfikatu klienta | Certyfikat lokalny, klucz prywatny, główny urząd certyfikacji             |
| Klient lub serwer TLS tylko z kluczami wstępnymi    | Brak (użycie PSK zamiast certyfikatów)             |

Odpowiednie usługi do ładowania certyfikatów są następujące:

| **Nazwa interfejsu API**                                   | **Cel**                                            |
| ---------------------------------------------- |------------------------------------------------------- |
| nx_secure_x509_certificate_initialize      | Musi być wywołana dla wszystkich certyfikatów, aby wypełnić strukturę NX_SECURE_X509_CERT danymi certyfikatu i kluczem prywatnym. |
| nx_secure_tls_local_certificate_add       | Dodaj certyfikat lokalny do sesji TLS w celu zidentyfikowania urządzenia.                                                                |
| nx_secure_tls_local_certificate_remove    | Usuń certyfikat lokalny z sesji TLS.                                                                                   |
| nx_secure_tls_remote_certificate_allocate | Przydziel miejsce dla certyfikatu zdalnego (wywoływane z niezainicjowanym NX_SECURE_X509_CERT).                                   |
| nx_secure_tls_trusted_certificate_add     | Dodaj certyfikat do sesji TLS jako zaufany certyfikat do uwierzytelniania hostów zdalnych.                                     |
| nx_secure_tls_trusted_certificate_remove  | Usuń zaufany certyfikat z sesji TLS.                                                                                 |

### <a name="working-with-aws-iot-certificates"></a>Praca z certyfikatami IoT AWS

W interfejsie Amazon Web Services IoT wybierz pozycję "zabezpieczenia" z menu paska bocznego i wybierz pozycję "certyfikaty". Utwórz nowy certyfikat i postępuj zgodnie z instrukcjami, aby pobrać nowy certyfikat urządzenia.

Po pobraniu certyfikatów konieczne będzie ich przekonwertowanie do formatu DER przy użyciu OpenSSL lub podobnego narzędzia.

Uwaga: AWS również udostępni plik klucza publicznego. Klucz publiczny jest zawarty w certyfikacie urządzenia lokalnego, dlatego nie musi zostać zaimportowany do aplikacji.

Poniżej przedstawiono przykładowe polecenia służące do konwertowania certyfikatu urządzenia lokalnego i jego klucza prywatnego na format DER do użycia z NetX Secure:

```C
openssl x509 -inform PEM -in <certificate> -outform DER -out cert.der
openssl x509 -inform PEM -in <root CA cert> -outform DER -out CA_cert.der
openssl rsa -inform PEM -in <private key> -outform DER -out private.key
```
Skonwertowane pliki można zaimportować do aplikacji zgodnie z powyższymi instrukcjami.

## <a name="x509-certificate-validation-in-netx-secure"></a>Walidacja certyfikatu X. 509 w usłudze NetX Secure 

W przypadku korzystania z protokołu TLS z certyfikatami X. 509 do identyfikacji i weryfikacji hosta ważne jest, aby zrozumieć, jak te certyfikaty są rzeczywiście weryfikowane. Chociaż Specyfikacja TLS nie zawiera szczegółowych instrukcji dotyczących weryfikacji certyfikatu, odnosi się do specyfikacji X. 509 (RFC 5280). Ogólnie rzecz biorąc, oczekuje się, że protokół TLS będzie przeprowadzać co najmniej podstawowe sprawdzanie poprawności certyfikatów przychodzących (te certyfikaty dostarczone przez hosta zdalnego podczas uzgadniania protokołu TLS), a protokół Secure TLS NetX nie jest inny.

### <a name="basic-x509-validation"></a>Podstawowa Walidacja X. 509

W przypadku dowolnego certyfikatu przychodzącego protokół NetX Secure TLS będzie wykonywał podstawowe sprawdzanie poprawności ścieżki X. 509. Proces polega na sprawdzeniu podpisu cyfrowego każdego certyfikatu dla certyfikatu wystawcy, który może być dostarczony przez hosta zdalnego lub znajdować się w zaufanym magazynie certyfikatów (zobacz sekcję "Importowanie certyfikatów X. 509 do usługi NetX Secure"), aby uzyskać więcej informacji na temat importowania zaufanych certyfikatów). Proces sprawdzania poprawności jest cyklicznie powtarzany w certyfikatach wystawcy, dopóki nie zostanie osiągnięty zaufany certyfikat lub że łańcuch zostanie zakończony (z certyfikatem z podpisem własnym lub z brakującym certyfikatem wystawcy). Jeśli zostanie osiągnięty zaufany certyfikat, certyfikat zostanie zweryfikowany, w przeciwnym razie zostanie odrzucony. Ponadto na każdym etapie procesu weryfikacji Data wygaśnięcia każdego certyfikatu jest sprawdzana względem czasu podanego przez funkcję sygnatury czasowej aplikacji (Aby uzyskać więcej informacji, zobacz "nx_secure_tls_session_time_function_set".

Specyfikacja X. 509 zawiera również algorytm obsługujący "zasady", czyli identyfikatory, które znajdują się w rozszerzeniu X. 509, które można sprawdzić podczas weryfikacji ścieżki. NetX zabezpiecza obecnie traktuje certyfikaty X. 509, ponieważ w przypadku zdefiniowania opcji "anyPolicy" — to oznacza, że wszystkie zasady są akceptowane, a opcjonalne sprawdzanie zasad nie jest wykonywane. Implementację NetX Secure X. 509 można rozszerzyć za pomocą tej funkcji w przyszłej wersji. Na razie rozszerzenie zasad może zostać uzyskane z certyfikatu przy użyciu interfejsu API *nx_secure_x509_extension_find* .

Po zakończeniu walidacji ścieżki podstawowej protokół TLS wywoła wywołanie zwrotne weryfikacji certyfikatu dostarczone przez aplikację przy użyciu interfejsu API *nx_secure_tls_session_certificate_callback_set* . Jeśli nie podano wywołania zwrotnego, certyfikat jest uznawany za zaufany po pomyślnej weryfikacji ścieżki. Jeśli zostanie podane wywołanie zwrotne, wywołanie zwrotne będzie przeprowadzać wszelkie dodatkowe walidacje certyfikatu wymagane przez aplikację. Wartość zwracana z wywołania zwrotnego jest używana do określenia, czy kontynuować uzgadnianie TLS czy też przerwać uzgadnianie z powodu błędu walidacji.

Wywołanie zwrotne jest wywoływane ze wskaźnikiem do odpowiedniej sesji TLS i NX_SECURE_X509_CERTm wskaźnikiem do certyfikatu do zweryfikowania. Między sesją TLS i certyfikatem aplikacja ma wszystkie dane wymagane od protokołu TLS w celu przeprowadzenia dodatkowych testów weryfikacyjnych.

Aby pomóc w dodatkowej weryfikacji, NetX Secure udostępnia procedury X. 509 dla niektórych typowych operacji sprawdzania poprawności, w tym sprawdzanie poprawności DNS i sprawdzanie listy odwołania certyfikatów. Wszystkie te procedury są odpowiednie do użycia w ramach wywołania zwrotnego weryfikacji certyfikatu, ale mogą być również używane do przeprowadzania wyłączania certyfikatów X. 509.

Poniższa tabela zawiera podsumowanie dostępnych funkcji pomocnika dla przetwarzania certyfikatów X. 509. Bardziej szczegółowe wyjaśnienia dotyczące operacji można znaleźć w poniższych sekcjach i dokumentacji interfejsu API w rozdziale 4  
  
Opis usług NetX Secure Services zawiera dodatkowe szczegóły dotyczące konkretnych procedur.

| **Nazwa interfejsu API**                             | **Opis**                               |
| ---------------------------------------- | -------------------------------------- |
| nx_secure_x509_common_name_dns_check               | Sprawdź nazwę pospolitą podmiotu X. 509 i SubjectAltName w odniesieniu do oczekiwanej nazwy DNS |
| nx_secure_x509_crl_revocation_check                 | Wyszukaj odwołany certyfikat na liście odwołania certyfikatów X. 509 (CRL)       |
| nx_secure_x509_extended_key_usage_extension_parse | Analizowanie i znajdowanie określonego identyfikatora OID rozszerzonego użycia klucza w certyfikacie                   |
| nx_secure_x509_key_usage_extension_parse           | Analizowanie i zwracanie pole bitowe użycia klucza w certyfikacie                            |
| nx_secure_x509_extension_find                        | Znajdź i zwróć nieprzetworzone dane ASN. 1 zakodowane algorytmem DER dla określonego rozszerzenia.            |

Funkcje pomocnika X. 509 do użycia w wywołaniu zwrotnym weryfikacji certyfikatu

### <a name="x509-extensions"></a>Rozszerzenia X. 509

Specyfikacja X. 509 zawiera wiele "rozszerzeń", które mogą być używane do dostarczania dodatkowych informacji, które mogą być wykorzystane w weryfikacji certyfikatów. W większości przypadków te rozszerzenia są opcjonalne i nie są wymagane do bezpiecznej weryfikacji certyfikatu cyfrowego względem zaufanego certyfikatu głównego. Jednak usługa NetX Secure obsługuje niektóre podstawowe rozszerzenia. Obsługę dodatkowych rozszerzeń można dodać w przyszłych wydaniach.

Obecnie obsługiwane rozszerzenia są wymienione w poniższej tabeli:

| Nazwa rozszerzenia           | Opis                                                                   | Odpowiedni interfejs API                                             |
| ------------------------ | ----------------------------------------------------------------------------- | -------------------------------------------------------- |
| Użycie klucza                | Zapewnia akceptowalne użycie klucza publicznego certyfikatu w pole bitowe         | nx_secure_x509_key_usage_extension_parse           |
| Rozszerzone użycie klucza       | Zapewnia dodatkowe akceptowalne zastosowania klucza publicznego certyfikatu przy użyciu identyfikatorów OID | nx_secure_x509_extended_key_usage_extension_parse |
| Alternatywna nazwa podmiotu | Udostępnia alternatywne nazwy DNS, które są również reprezentowane przez certyfikat   | nx_secure_x509_common_name_dns_check               |

### <a name="unsupported-x509-extensions"></a>Nieobsługiwane rozszerzenia X. 509

NetX Secure X. 509 implementacji zapewnia usługę do wyodrębnienia nieobsługiwanych rozszerzeń, jak również: *nx_secure_x509_extension_find*. Ten interfejs API jest przeznaczony dla zaawansowanych użytkowników, ponieważ wymaga informacji o ASN. 1 w celu przeanalizowania zwracanych danych. Jest ona używana wewnętrznie w celu wyodrębnienia obsługiwanych rozszerzeń, ale jest dostarczana dla wygody podczas opracowywania dostosowanej obsługi rozszerzeń X. 509.

Aby można było użyć nx_secure_x509_extension_find, zostanie przemieszczony NX_SECURE_X509_EXTENSION, wraz z certyfikatem i IDENTYFIKATORem rozszerzenia, który jest liczbą całkowitą ciągu identyfikatora OID o zmiennej długości dla znanego typu rozszerzenia. Pełna lista obsługiwanych identyfikatorów OID dla rozszerzeń X. 509 znajduje się w dokumentacji interfejsu API dla nx_secure_x509_extension_find na stronie 178.

Struktura NX_SECURE_X509_EXTENSION jest definiowana w następujący sposób:

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
Gdy usługa zwróci się pomyślnie, struktura zostanie wypełniona odpowiednimi danymi z certyfikatu. Pole nx_secure_x509_extension_id jest zwykle używane do celów wewnętrznych, ale zostanie wypełnione odpowiednią reprezentacją liczby całkowitej dla identyfikatora OID. Pole nx_secure_x509_extension_critical uwidacznia wartość flagi rozszerzenia krytycznego X. 509 (Boolean). Pola nx_secure_x509_extension_data i nx_secure_x509_extension_data_length zawierają wskaźnik do danych ASN w formacie DER. 1 dla rozszerzenia i długość tych danych.

Rzeczywista analiza numeru ASN. 1 dane wykracza poza zakres tego dokumentu, ale jeśli masz dostęp do źródła bezpiecznego protokołu TLS NetX, możesz sprawdzić, w jaki sposób analizowanie odbywa się wszędzie tam, gdzie nx_secure_x509_extension_find jest wywoływana dla obsługiwanych rozszerzeń.

### <a name="x509-dns-validation"></a>Weryfikacja systemu DNS X. 509

Typowa operacja weryfikacji certyfikatu w protokole TLS polega na sprawdzeniu, czy nazwa domeny jest Top-Level (TLD) hosta zdalnego względem certyfikatu X. 509 dostarczonego przez ten host podczas uzgadniania protokołu TLS. Ta operacja pomaga upewnić się, że certyfikat jest rzeczywiście zgodny z serwerem hosta, który go dostarczył, przy założeniu, że wyszukiwanie DNS może być zaufane. W NetX Secure TLS ta funkcja jest zapewniana przez **nx_secure_x509_common_name_dns_check** usługi, która pobiera certyfikat i ciąg zawierający część TLD adresu URL służącego do uzyskiwania dostępu do hosta. Wartość TLD jest porównywana z polem nazwa pospolita certyfikatu i jeśli jest zgodna, NX_SUCCESS jest zwracana. Jeśli nazwa pospolita nie jest zgodna, procedura będzie również sprawdzać istnienie rozszerzenia certyfikatu X. 509 *SubjectAltName*. Jeśli subjectAltName jest obecny, wszystkie wpisy DNSName w rozszerzeniu są również sprawdzane względem podanej TLD. Ponownie, jeśli dowolny z nich jest zgodny, NX_SUCCESS jest zwracana. Jeśli nie zostanie znalezione dopasowanie, zwracany jest błąd odpowiedni do powrotu z wywołania zwrotnego walidacji certyfikatu.

### <a name="x509-key-usage-and-extended-key-usage-extensions"></a>Użycie klucza X. 509 i rozszerzenia rozszerzonego użycia klucza

Rozszerzenia użycie klucza X. 509 i rozszerzone użycie klucza zawierają informacje dotyczące sposobu użycia klucza publicznego certyfikatu podczas uwierzytelniania tego certyfikatu. Użycie klucza jest dostarczane przez wystawcę certyfikatu, gdy certyfikat jest podpisany i wystawiony. Użycie klucza może być używane przez hosta TLS do sprawdzenia, czy certyfikat jest autoryzowany do uwierzytelniania zdalnego hosta TLS i wykonywania innych operacji.

Rozszerzenie użycie klucza składa się z prostego pole bitowe, gdzie każdy z bitów reprezentuje określone użycie klucza. Pełna lista tych wartości znajduje się w dokumentacji interfejsu API dla *nx_secure_x509_key_usage_extension_parse* na stronie 183. Aby zapoznać się z bardziej szczegółowym opisem bitów użycia klucza i ich znaczenia, zapoznaj się ze standardem RFC 5280, w sekcji 4.2.1.3.

Rozszerzenie rozszerzonego użycia klucza, takie jak rozszerzenie użycie klucza, zapewnia akceptowalne informacje o użyciu klucza. Jednak w celu zapewnienia obsługi dowolnego użycia rozszerzenie rozszerzonego użycia klucza wykorzystuje identyfikatory OID zamiast pole bitowe. Podczas analizowania rozszerzonego użycia klucza w NetX Secure X. 509, liczba całkowita reprezentująca identyfikator OID jest dostarczana przez aplikację — usługa *nx_secure_x509_extended_key_usage_extension_parse* następnie zwróci czy ten identyfikator OID jest obecny. Pełna lista obsługiwanych identyfikatorów OID dla rozszerzonego użycia klucza znajduje się w dokumentacji interfejsu API dla *nx_secure_x509_extended_key_usage_extension_parse* na stronie 175. Aby zapoznać się z bardziej szczegółowym opisem identyfikatorów OID i ich znaczenia, zapoznaj się ze standardem RFC 5280, w sekcji 4.2.1.12.

### <a name="x509-crl-revocation-status-checking"></a>Sprawdzanie stanu odwołania do listy CRL X. 509

X. 509 udostępnia mechanizm nazywany *listą odwołania certyfikatów* (CRL), która umożliwia urzędowi podpisywania certyfikatu cyfrowego odwoływanie ważności certyfikatów, które zostały podpisane. Wszystkie aplikacje, które wymagają zweryfikowania certyfikatów z urzędu podpisywania, mogą uzyskać listę CRL i porównać wszystkie certyfikaty podpisane przez urząd certyfikacji z listą CRL, aby sprawdzić, czy ich stan został odwołany z jakiegoś powodu (na przykład złamany klucz prywatny). W ten sposób aplikacja może uniknąć używania potencjalnie niebezpiecznych certyfikatów, które przekazują inne sprawdzenia poprawności certyfikatu.

Uzyskiwanie listy CRL odbywa się przez aplikację przez pobranie listy kodowanej algorytmem DER ze wstępnie zdefiniowanego serwera lub w inny sposób. Rzeczywista konfiguracja jest różna od wystawcy do wystawcy, aby usługa NetX Secure nie zapewniała mechanizmu uzyskiwania listy CRL, ale udostępnia procedurę sprawdzania certyfikatu w odniesieniu do listy CRL, **nx_secure_x509_crl_revocation_check**.

Interfejs API przyjmuje listę CRL zakodowaną algorytmem DER, magazyn certyfikatów (na przykład ten, który znajduje się w sesji TLS) do sprawdzenia i certyfikat do sprawdzenia. Procedura najpierw sprawdza poprawność samej listy CRL względem zaufanego magazynu (część magazynu certyfikatów dostarczanego przez aplikację). Jest to ważne, aby chronić przed nieuczciwymi listami CRL używanymi w przypadku ataków typu "odmowa usługi" oraz stwierdzać, że lista CRL jest rzeczywiście od właściwego wystawcy. Po sprawdzeniu poprawności listy CRL wystawcy zostanie sprawdzony — Jeśli wystawca listy CRL nie pasuje do wystawcy certyfikatu, wówczas lista CRL nie jest prawidłowa dla tego certyfikatu i zwracany jest błąd. Do aplikacji można określić, czy uzgadnianie TLS może być kontynuowane w tym momencie. Jeśli wystawcy są zgodne, lista CRL szuka numeru seryjnego zweryfikowanego certyfikatu. Jeśli numer seryjny znajduje się na liście, zwracany jest błąd wskazujący, że certyfikat został odwołany. Jeśli nie zostanie znalezione dopasowanie, zostanie zwrócona NX_SUCCESS.

## <a name="client-certificate-authentication-in-netx-secure-tls"></a>Uwierzytelnianie certyfikatu klienta w protokole Secure TLS NetX

W przypadku korzystania z uwierzytelniania certyfikatu X. 509 protokół TLS wymaga, aby wystąpienie serwera TLS zapewniało certyfikat do identyfikacji, ale domyślnie wystąpienie klienta TLS nie musi podawać certyfikatu do uwierzytelnienia przy użyciu innej formy uwierzytelniania (np. kombinacji nazwy użytkownika/hasła). Jest to zgodne z najbardziej typowym wykorzystaniem protokołu TLS w Internecie dla witryn sieci Web. Na przykład witryna handlu detalicznego w trybie online musi udowodnić potencjalnemu klientowi korzystanie z przeglądarki sieci Web, że serwer jest wiarygodny, ale użytkownik użyje nazwy logowania/hasła w celu uzyskania dostępu do określonego konta.

Jednak domyślna wielkość liter nie zawsze jest pożądana, więc protokół TLS zezwala na to, aby wystąpienie serwera TLS zażądało certyfikatu z klienta zdalnego. Po włączeniu tej funkcji serwer TLS wyśle do klienta protokołu TLS komunikat CertificateRequest podczas uzgadniania. Klient musi odpowiedzieć własnym certyfikatem, a komunikat CertificateVerify zawierający token kryptograficzny wskazujący, że klient jest właścicielem zgodnego klucza prywatnego skojarzonego z tym certyfikatem. Jeśli weryfikacja nie powiedzie się lub certyfikat nie jest połączony z zaufanym certyfikatem na serwerze, uzgadnianie TLS nie powiedzie się.

Istnieją dwa oddzielne przypadki uwierzytelniania certyfikatu klienta w protokole TLS — w poniższych sekcjach omówiono oba przypadki.

### <a name="client-certificate-authentication-for-tls-clients"></a>Uwierzytelnianie certyfikatu klienta dla klientów TLS

Klient protokołu TLS może próbować nawiązać połączenie z serwerem, który żąda certyfikatu do uwierzytelnienia klienta. W takim przypadku klient musi dostarczyć certyfikat do serwera i upewnić się, że jest właścicielem zgodnego klucza prywatnego lub serwer zakończy uzgadnianie TLS.

W NetX Secure TLS nie ma specjalnej konfiguracji do obsługi tej funkcji, ale aplikacja będzie musiała podać lokalny certyfikat identyfikacyjny dla wystąpienia klienta TLS przy użyciu usługi *nx_secure_tls_local_certificate_add* . Jeśli aplikacja nie udostępnia żadnego certyfikatu, ale serwer zdalny używa uwierzytelniania certyfikatu klienta i żąda certyfikatu, uzgadnianie protokołu TLS zakończy się niepowodzeniem. Aby można było wykonać uzgadnianie TLS, certyfikat podany w sesji protokołu TLS z *nx_secure_tls_local_certificate_add* musi być rozpoznawany przez serwer zdalny.

### <a name="client-certificate-authentication-for-tls-servers"></a>Uwierzytelnianie certyfikatu klienta dla serwerów TLS

Przypadek serwera TLS dla uwierzytelniania certyfikatu klienta jest nieco bardziej skomplikowany niż przypadek klienta TLS ze względu na opcjonalną funkcję. W takim przypadku serwer TLS musi jawnie zażądać certyfikatu ze zdalnego klienta TLS, a następnie przetworzyć komunikat CertificateVerify, aby sprawdzić, czy Klient zdalny jest właścicielem pasującego klucza prywatnego, a następnie serwer musi sprawdzić, czy certyfikat dostarczony przez klienta może być śledzony do certyfikatu w lokalnym magazynie zaufanych certyfikatów.

W przypadku wystąpień serwera Secure TLS NetX uwierzytelnianie certyfikatu klienta jest kontrolowane przez <br>
*Klient <span class="underline"> _</span> Secure <span class="underline">_</span>TLS <span class="underline"> _</span> sesji <span class="underline">_</span>NX <span class="underline"> _</span> Weryfikuj <span class="underline">_</span>* i<br>
*<span class="underline"> _</span> bezpieczny <span class="underline">_</span>klient <span class="underline"> _</span> sesji <span class="underline">_</span>protokołu TLS w usłudze NX <span class="underline"> _</span> Sprawdź, czy <span class="underline">_</span>są wyłączone* usługi.

Aby włączyć uwierzytelnianie certyfikatu klienta, aplikacja musi wywoływać<br>
*Klient <span class="underline"> _</span> bezpiecznej <span class="underline">_</span><span class="underline"> _</span> sesji <span class="underline">_</span>TLS przed wywołaniem nx_secure_tls_session_start <span class="underline"> _</span> Sprawdź, czy <span class="underline">_</span>włączono* go przy użyciu wystąpienia sesji serwera TLS. Należy zauważyć, że wywołanie tej usługi w sesji protokołu TLS, która jest używana na potrzeby połączeń klientów TLS, nie będzie miało żadnego efektu.

Po włączeniu uwierzytelniania przy użyciu certyfikatu klienta serwer TLS zażąda certyfikatu od klienta zdalnego protokołu TLS podczas uzgadniania protokołu TLS. W przypadku serwera NetX Secure TLS certyfikat klienta jest sprawdzany pod względem magazynu zaufanych certyfikatów utworzonych przy użyciu *nx <span class="underline"> _</span> <span class="underline">_ secure_tls</span>zaufany <span class="underline"> _</span> <span class="underline">_ certyfikat</span>Dodaj* następujący po łańcuchu wystawcy X. 509. Klient zdalny musi dostarczyć łańcuch, który łączy jego certyfikat tożsamości z certyfikatem w zaufanym magazynie lub uzgadnianie protokołu TLS zakończy się niepowodzeniem. Ponadto jeśli przetwarzanie komunikatu CertificateVerify nie powiedzie się, uzgadnianie TLS również zakończy się niepowodzeniem.

Metody podpisu używane dla metody CertificateVerify są ustalone dla protokołów TLS w wersji 1,0 i TLS w wersji 1,1 i są określone przez serwer TLS w wersji TLS 1,2. W przypadku protokołu TLS 1,2 metody podpisywania są ogólnie zgodne z odpowiednimi metodami podanymi w tabeli metod kryptograficznych, ale zazwyczaj RSA z algorytmem SHA-256 (zobacz sekcję "Kryptografia w NetX Secure TLS", aby uzyskać więcej informacji na temat inicjowania protokołu TLS z metodami kryptograficznymi).

## <a name="cryptography-in-netx-secure-tls"></a>Kryptografia w protokole Secure TLS NetX

TLS definiuje protokół, w którym Kryptografia może być używana do zabezpieczania komunikacji sieciowej. W związku z tym pozostawi rzeczywiste kryptografie do użycia w postaci otwartej dla użytkowników protokołu TLS. Specyfikacja wymaga tylko jednego ciphersuite do zaimplementowania — w przypadku protokołu TLS 1,2, że ciphersuite jest TLS_RSA_WITH_AES_128_CBC_SHA, wskazując użycie RSA dla operacji klucza publicznego, AES w trybie CBC z 128-bitowymi kluczami dla szyfrowania sesji i algorytmem SHA-1 dla skrótów uwierzytelniania komunikatów.

Jest zgodny z protokołem TLS 1,2, NetX Secure domyślnie włącza obowiązkowy TLS_RSA_WITH_AES_128_CBC_SHA ciphersuite, ale biorąc pod uwagę liczbę możliwych implementacji dla każdej z metod kryptograficznych ze względu na możliwości sprzętowe i inne zagadnienia, NetX Secure zapewnia ogólny interfejs API kryptografii, który umożliwia użytkownikowi określenie metod kryptograficznych, które mają być używane z protokołem TLS.

Uwaga: mechanizm ogólnego interfejsu API kryptografii umożliwia również użytkownikom implementację własnych ciphersuites, ale jest to zalecane dla zaawansowanych użytkowników, którzy znają ciphersuites i rozszerzenia TLS. Skontaktuj się z przedstawicielem programu Express Logic, Jeśli interesuje Cię obsługę własnych ciphersuites.

### <a name="cryptographic-methods"></a>Metody kryptograficzne

NetX Secure TLS implementuje algorytm DES, 3DES, AES, MD5, HMAC-MD5, SHA-1, HMAC-SHA1, SHA-256, HMAC-SHA256, RSA i ECC (wybrane krzywe) w oprogramowaniu ze sterownikami sprzętowymi dla określonych platform sprzętowych. Aplikacja może korzystać z procedur kryptograficznych dostarczanych z usługą NetX Secure lub używać procedur niestandardowych dostarczonych przez użytkownika końcowego lub inne osoby trzecie.

*NX_CRYPTO_METHOD* to blok sterowania zaprojektowany dla aplikacji do opisywania konkretnej implementacji algorytmu kryptograficznego, który ma być używany z NetX Secure TLS. Dzięki *NX_CRYPTO_METHOD* aplikacja może łatwo zintegrować swoją implementację kryptograficzną z bezpiecznym NetX. Struktura *NX_CRYPTO_METHOD* jest zadeklarowana jako:

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

Poniżej znajduje się opis każdego elementu w strukturze *NX_CRYPTO_METHOD* :

- nx_crypto_algorithm: to pole identyfikuje algorytm opisany w zmiennej *metody* pewne prawidłowe wartości dla NetX Secure TLS są następujące (zobacz nx_crypto_const. h dla określonych wartości):
    
  - NX_CRYPTO_NONE    
  - NX_CRYPTO_ENCRYPTION_NULL    
  - NX_CRYPTO_ENCRYPTION_AES_CBC    
  - NX_CRYPTO_AUTHENTICATION_NONE    
  - TLS_HASH_SHA_1    
  - TLS_HASH_SHA_256    
  - TLS_HASH_MD5    
  - TLS_CIPHER_RSA    
  - TLS_CIPHER_NULL

- nx_crypto_key_size_in_bits: to pole określa rozmiar klucza tajnego używanego przez metodę.

- nx_crypto_IV_size_in_bits: to pole określa rozmiar wektora inicjalizacji (IV). Należy zauważyć, że w większości przypadków blok IV jest używany tylko na potrzeby algorytmów szyfrowania i odszyfrowywania. Algorytmy uwierzytelniania i weryfikacji rzadko używają tego pola.

- nx_crypto_ICV_size_in_bits: to pole określa rozmiar bloku wartości sprawdzania integralności (ICV). Uwaga: ten blok służy do użycia protokołu IPsec i nie jest używany w protokole TLS. Aby uzyskać więcej informacji, zobacz NetX Duo IPsec.

- nx_crypto_block_size_in_bytes: to pole określa rozmiar bloku algorytmu kryptograficznego dla szyfrów opartych na blokach, w bajtach. W większości przypadków jest to używane przez procedury szyfrowania i rzadko przez procedury uwierzytelniania.

- nx_crypto_metadata_area_size: to pole określa rozmiar obszaru metadanych wymaganego przez tę metodę. Każda implementacja może wymagać pewnej ilości pamięci do przechowywania informacji o stanie lub przechowywania danych pośrednich (na przykład materiału transformacji Key) lub do użycia jako szkicownik. Ilość miejsca wymaganego przez implementację jest określona w tym polu. Aplikacja zapewnia miejsce w pamięci podczas tworzenia sesji TLS. Funkcja kryptograficzna jest odpowiedzialna za zarządzanie tym obszarem metadanych.

- nx_crypto_init: jest to funkcja inicjująca dla algorytmu kryptograficznego. Dla implementacji, która nie wymaga procedury inicjowania, to pole może mieć wartość NX_NULL. Typowym zastosowaniem funkcji inicjowania jest zainicjowanie wewnętrznej struktury danych dla algorytmu. NetX Secure TLS będzie obsługiwać inicjalizację procedury kryptograficznej przez wywołanie tej funkcji wewnętrznie.

Prototyp dla funkcji inicjującej to:

```C
UINT crypto_init_function(NX_CRYPTO_METHOD *method, 
                          UCHAR *key, 
                          UINT  key_size_in_bits, 
                          VOID  **handle, 
                          VOID  *crypto_metadata_area, 
                          ULONG crypto_metadata_area_size);
```

  - Metoda jest wskaźnikiem do bloku kontroli metody kryptograficznej.

  - klucz jest ciągiem klucza tajnego do przetwarzania pakietów danych.

  - key_size_in_bits definiuje rozmiar klucza tajnego w bitach.

  - dojście to element zdefiniowany przez implementację, który identyfikuje konkretną sesję kryptograficzną. Wartość jest generowana przez procedurę inicjowania i zostaje przeniesiona z powrotem do obiektu wywołującego. Kolejna operacja kryptograficzna lub procedura czyszczenia używają tego uchwytu do identyfikowania sesji.

  - crypto_metadata jest wskaźnikiem do obszaru metadanych wymaganego przez implementację tego algorytmu. Dla algorytmów, które nie potrzebują obszaru metadanych, to pole jest ustawione na NX_NULL a procedura inicjacji nie może uzyskać dostępu do obszaru metadanych.

  - crypto_metadata_size określa rozmiar obszaru metadanych. Dla sygnatury dostępu współdzielonego utworzonego bez obszaru metadanych to pole ma ustawioną wartość zero, a procedura inicjacji nie może uzyskać dostępu do obszaru metadanych.

  - Ta procedura zwraca *NX_SUCCESS* , jeśli proces inicjowania zakończył się pomyślnie. Obiekt wywołujący traktuje dowolną inną wartość zwracaną jako błąd.

- nx_crypto_cleanup: to jest procedura oczyszczania zdefiniowana dla implementacji algorytmu kryptograficznego. Jest wywoływana po usunięciu lub ponownym uruchomieniu sesji TLS.

Prototyp funkcji czyszczącej to:

```C
UINT crypto_cleanup_function(VOID *handle);
```
- Dojście jest przesyłane do funkcji oczyszczania przez wywołującego. Dojście jest inicjowane przez procedurę inicjalizacji kryptograficznej i używane do identyfikowania stanu algorytmu kryptograficznego.

- Ta procedura zwraca *NX_SUCCESS* , jeśli proces oczyszczania zakończy się pomyślnie. Obiekt wywołujący traktuje dowolną inną wartość zwracaną jako błąd.

- nx_crypto_operation: to jest procedura, która wykonuje rzeczywiste szyfrowanie, odszyfrowywanie i usługi uwierzytelniania. Prototyp funkcji procedury operacji to:

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

- op wskazuje typ operacji, która powinna zostać przeprowadzona. Prawidłowe wartości to:
    
    - NX_CRYPTO_ENCRYPT
    - NX_CRYPTO_DECRYPT
    - NX_CRYPTO_AUTHENTICATE
    - NX_CRYPTO_VERIFY

- dojście zostało przesłane do funkcji operacji przez obiekt wywołujący. Jest on generowany przez procedurę inicjalizacji kryptograficznej.
- Metoda wskazuje blok kontroli metody kryptograficznej
- klucz do klucza tajnego używanego dla tej operacji
- key_size_in_bits to rozmiar klucza tajnego w bitach
- wejście to wskaźnik do początku komunikatu, na którym ma być prowadzone zarządzanie.
- input_length_in_byte jest przenoszona przez obiekt wywołujący, aby wskazać rozmiar wiadomości, na której ma być prowadzony proces.
- iv_ptr jest konfiguracją przez obiekt wywołujący do wskazywania początku bloku IV. Należy pamiętać, że pamięć dla bloku IV jest udostępniana przez obiekt wywołujący. W przypadku szyfrowania, funkcja operacji powinna zapisać informacje o IV w tym bloku pamięci; w przypadku odszyfrowywania funkcja operacji powinna pobrać informacje o IV z tego bloku pamięci. Algorytmy dla operacji uwierzytelniania i weryfikacji zwykle nie używają wektora inicjalizacji.
- dane wyjściowe są skonfigurowane przez obiekt wywołujący, aby wskazywały bufor wyjściowy. Należy pamiętać, że pamięć dla buforu wyjściowego jest udostępniana przez obiekt wywołujący. W przypadku szyfrowania funkcja operacji powinna zapisać tekst szyfru do bufora wyjściowego; w przypadku odszyfrowywania operacja powinna napisać odszyfrowany tekst (zwykły tekst) do buforu wyjściowego; w celu uwierzytelnienia wartość skrótu jest zapisywana w buforze wyjściowym. W celu weryfikacji bufor wyjściowy służy do przechowywania informacji o skrócie.
- output_length_in_byte wskazuje rozmiar buforu wyjściowego
- crypto_metadata wskazuje obszar metadanych, który ma być używany przez tę operację kryptograficzną. Obszar metadanych kryptograficznych jest zazwyczaj inicjowany przez crypto_init_function.
- crypto_metadata_size wskazuje rozmiar obszaru metadanych.
- Ta procedura zwraca *NX_SUCCESS* , jeśli proces operacji zakończy się pomyślnie. Obiekt wywołujący traktuje dowolną inną wartość zwracaną jako błąd.
- packet_ptr: pakiet zawierający dane, które są przetwarzane. Uwaga: ten parametr jest nieużywany przez protokół TLS i powinien mieć ustawioną wartość NX_NULL.
- nx_crypto_hw_process_callback: funkcja wywołania zwrotnego podana przez metodę szyfrowania. Jest używana, jeśli funkcja kryptograficzna jest dostarczana przez sprzęt i wymaga procedury wywołania zwrotnego.

NetX Secure TLS zapewnia następujące metody szyfrowania:

- *AES*  
- *RSA*  
- *NULL*

NetX Secure TLS zapewnia następujące metody uwierzytelniania:

- *HMAC-MD5*  
- *HMAC-SHA1*  
- *HMAC-SHA256*

W poniższych przykładach pokazano, jak skonfigurować strukturę *NX_CRYPTO_METHOD* tak, aby korzystała z metod szyfrowania i uwierzytelniania dostarczonych przez NetX Duo IPSec.

***AES***

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
***NULL***

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
***DAWAJ***

Specjalna metoda **NX_CRYPTO_NONE** jest używana do sygnalizowania modułu IPSec, że szyfrowanie lub usługa uwierzytelniania nie jest wymagana. Jest on konfigurowany w następujący sposób:

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
### <a name="initializing-tls-with-cryptographic-methods"></a>Inicjowanie protokołu TLS z metodami kryptograficznymi

Po utworzeniu procedur kryptograficznych zgodnych z sygnaturami metod kryptograficznych opisanymi w poprzedniej sekcji należy przekazać je do protokołu TLS po zainicjowaniu bloku sterowania NX_SECURE_TLS_SESSION. Odbywa się to w nx_secure_tls_session_create usługi TLS:

```C
UINT  nx_secure_tls_session_create(
              NX_SECURE_TLS_SESSION*     session_ptr,
              const NX_SECURE_TLS_CRYPTO*    tls_cipher_table,
              VOID*                encryption_metadata_area,
              ULONG                 encryption_metadata_size
);
```
- session_pointer jest wskaźnikiem do bloku sterowania NX_SECURE_TLS_SESSION.
- tls_cipher_table jest wskaźnikiem do bloku sterowania NX_SECURE_TLS_CRYPTO, opisanego poniżej.
- encryption_metadata_area punkty do przestrzeni używanej przez procedury kryptograficzne w protokole TLS.
- encryption_metadata_size to rozmiar obszaru metadanych w bajtach.

### <a name="elliptic-curve-cryptography-ecc-in-netx-secure-tls"></a>Kryptografia krzywej eliptycznej (ECC) w NetX Secure TLS

Kryptografia krzywej eliptycznej (ECC) zapewnia schemat kryptografii klucza publicznego, który może być używany zamiast RSA. Funkcja ECC jest zwykle szybsza i używa mniejszych kluczy niż RSA, więc może być cenną opcją dla osadzonego protokołu TLS. W wersjach standardu X dla urządzeń z systemem Azure RTO 6,0, ECC został wysłany jako dodatek wymagający instalacji kodu źródłowego ECC do projektu. Usługa Azure RTO 6,0 Zintegrowana ECC z bazą kodu linii głównej w celu zainstalowania plików ECC nie jest już potrzebna. Jednak ECC nadal wymaga takiego samego inicjalizacji jak w poprzednich wersjach.

### <a name="supported-ecc-curves"></a>Obsługiwane krzywe ECC

NetX bezpiecznie implementuje części krzywych zgodnie z <http://www.secg.org/sec2-v2.pdf> . Thefollowing krzywe są obsługiwane<sup>18</sup>:

  - secp256r1 
  - secp384r1 
  - secp521r1 

Jeśli używane są inne krzywe ECC, procedura *nx_secure_tls_session_start ()* zwróci błąd NX_SECURE_TLS_NO_SUPPORTED_CIPHERS wskazujący, że użyto nieobsługiwanych krzywych.

Należy pamiętać, że łańcuch certyfikatów TLS może być zaszyfrowany również algorytmem ECC. Chociaż krzywe dostarczone przez klienta TLS są obsługiwane, istnieje możliwość, że krzywa ECC używana w łańcuchu certyfikatów nie jest obsługiwana. W takim przypadku procedura *nx_secure_tls_session_start* zwraca NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER.

Domyślny przykład tabeli ciphersuite dla ECC jest dostępny w nx_crypto_generic_ciphersuites. c. Więcej informacji o tabelach ciphersuite można znaleźć w sekcji "tabela szyfrowania kryptograficznego protokołu TLS".

18. Należy zauważyć, że implementacje dla krzywych secp192r1 i secp224r1are są również udostępniane dla starszych aplikacji. Jednak te krzywe są teraz uważane za słabe i nie powinny być używane do tworzenia nowych aplikacji.

### <a name="crypto-methods-for-ecc"></a>Metody kryptograficzne dla ECC

Metody kryptograficzne dla grup krzywej eliptyczna:

- NX_CRYPTO_METHOD crypto_method_ec_secp192<sup>15</sup>;  
- NX_CRYPTO_METHOD crypto_method_ec_secp224<sup>15</sup>;  
- NX_CRYPTO_METHOD crypto_method_ec_secp256;  
- NX_CRYPTO_METHOD crypto_method_ec_secp384;  
- NX_CRYPTO_METHOD crypto_method_ec_secp521;

Metody kryptograficzne dla krzywych ECC są zdefiniowane w nx_crypto_generic_ciphersuites. c.

Metoda kryptograficzna dla ECDHE:

- NX_CRYPTO_METHOD crypto_method_ecdhe;

Metoda kryptograficzna dla ECDSA:

- NX_CRYPTO_METHOD crypto_method_ecdsa;

Metody kryptograficzne ECDSA i ECDHE są zdefiniowane w nx_crypto_generic_ciphersuites. c.

W połączeniu z innymi metodami kryptograficznymi, takimi jak RSA, SHA i AES, można używać ich jako bloków konstrukcyjnych dla tabeli odnośników ciphersuite.

### <a name="enabling-ecc-support-for-tls"></a>Włączanie obsługi protokołu TLS

Funkcja ECC jest domyślnie włączona w przypadku protokołu TLS. Aby wyłączyć obsługę ECC, należy zdefiniować symbol NX_SECURE_DISABLE_ECC_CIPHERSUITE.

Aby zmiana zaczęła obowiązywać, należy ponownie skompilować bezpieczną bibliotekę NetX i wszystkie aplikacje używające tej biblioteki.

W kodzie aplikacji interfejs API n *x_secure_tls_ecc_initialize ()* musi zostać wywołany po utworzeniu sesji TLS. Ten interfejs API powiadamia sesję protokołu TLS o typie krzywych, które mają być używane na potrzeby operacji wymiany kluczy TLS i weryfikacji certyfikatu. W fazie uzgadniania protokołu TLS, jeśli wybrano algorytm ECC dla klienta i serwera, parametry powiązane z krzywą ECC, aby określić, która krzywa ma być używana.

Poniższy segment kodu ilustruje sposób korzystania z interfejsu API. Należy zauważyć, że argumenty (*nx_crypto_ecc_supported_groups, nx_crypto_ecc_supported_groups_size i nx_crypto_ecc_curves)* są zdefiniowane w *nx_crypto_generic_ciphersuites. c*. W związku z tym te symbole mogą być używane bezpośrednio.

```C
status = nx_secure_tls_ecc_initialize(&tls_session,     
                    nx_crypto_ecc_supported_groups,      
                    nx_crypto_ecc_supported_groups_size,     
                    nx_crypto_ecc_curves);
```
Przykładowa konfiguracja w nx_crypto_generic_ciphersuites. c zawiera tabelę odnośników ciphersuite ECC, która jest używana, gdy włączono funkcję ECC. Aby używać ECC, po prostu Przekaż nx_crypto_tls_ciphers_ecc jako parametr tabeli ciphersuite podczas tworzenia sesji protokołu TLS z nx_secure_tls_session_create. Przykładowa tabela zawiera dane ECC i ciphersuites bez ECC.

### <a name="tls-cryptographic-cipher-table"></a>Tabela szyfrowania kryptograficznego TLS

Struktura NX_SECURE_TLS_CRYPTO jest definiowana jako:

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
Tabela jest tworzona przez wypełnienie wpisów dla tej struktury w stałej statycznej znajdującej się w projekcie NetX Secure TLS, zazwyczaj znajdującym się w procedurach i modułach kryptograficznych.

Przykładowo Biblioteka kryptograficzna ("generyczna") oparta na oprogramowaniu NetX Secure zawiera następującą definicję tabeli (w przypadku usługi non-ECC ciphersuite support<sup>19</sup>):

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
W strukturze pierwszy wpis jest tabelą ciphersuite TLS. Struktura NX_SECURE_TLS_CIPHERSUITE_INFO mapuje procedury kryptograficzne (w formie wskaźników NX_CRYPTO_METHOD) do określonych ciphersuites zgodnie z definicją w specyfikacji TLS. Druga wartość to liczba wpisów w tabeli wskazywanych przez pierwsze pole.

Następne pole wskazuje tabelę procedur używanych przez X. 509 podczas przetwarzania certyfikatów cyfrowych i struktura NX_SECURE_X509_CRYPTO jest podobna w formularzu, aby NX_SECURE_TLS_CIPHERSUITE_INFO. Następujące pole jest liczbą wpisów w tabeli.

W poniższej tabeli odnośników przedstawiono różne procedury dla określonych wersji protokołu TLS. Na przykład przed protokołem TLS w wersji 1,2 procedury generowania kluczy i wyznaczania wartości skrótu zostały naprawione w celu użycia kombinacji algorytmu SHA-1 i MD5 — metody dla tych procedur są wywoływane w odniesieniu do struktury szyfru, ponieważ nie są one powiązane z konkretną ciphersuites. W przypadku protokołu TLS w wersji 1,2 są wybierane procedury generowania kluczy i wyznaczania wartości skrótu przez ciphersuite, ale dla ciphersuites, które nie określają procedur do użycia, używana jest metoda mieszania SHA-256, a struktura szyfru wywołuje tę procedurę w specjalny sposób.

Protokół TLS 1,3 wymaga kilku dodatkowych szyfrów dla różnych operacji.

19. Należy pamiętać, że obsługa protokołu TLS 1,3 wymaga ECC — Użyj nx_crypto_tls_ciphers_ecc, jeśli włączona jest funkcja TLS 1,3.

### <a name="tls-ciphersuite-lookup-table"></a>Tabela wyszukiwania Ciphersuite TLS

Aby wypełnić tabelę szyfrowania dla protokołu TLS, należy również utworzyć tabelę odnośników ciphersuite, która mapuje procedury kryptograficzne na określone identyfikatory ciphersuite. Identyfikatory są wartościami zarejestrowanymi przez organizację IANA, które są uniwersalne. Aby uzyskać więcej informacji, zobacz specyfikacje RFC protokołu TLS. Procedury przedstawiają 5 oddzielnych metod używanych w każdym ciphersuite (niektóre ciphersuites mogą nie używać wszystkich 5): szyfrowanie publiczne, uwierzytelnianie klucza publicznego, szyfrowanie sesji, procedura skrótu sesji i funkcja TLS Pseudo-Random funkcji (PRF). W poniższej tabeli opisano każdą z 5 metod:

| **Kategoria rutynowa**      | **Opis**                                                                                       | **Przykładowe algorytmy**                                            |
| ------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| Szyfrowanie publiczne             | Używane do wymiany kluczy podczas uzgadniania protokołu TLS                                                        | RSA, Diffie-Hellmana, ECC                                          |
| Uwierzytelnianie klucza publicznego | Służy do uwierzytelniania lub podpisywania danych podczas uzgadniania protokołu TLS                                            | RSA, DSS                                                          |
| Szyfr sesji            | Algorytm klucza symetrycznego służący do szyfrowania danych aplikacji podczas sesji TLS                       | AES, RC4                                                          |
| Skrót sesji              | Służy do zachowania integralności komunikatów w trakcie sesji TLS (gwarantuje, że dane nie uległy zmianie) | SHA-1, SHA-256                                                    |
| PRF TLS                   | Używane do generowania materiału klucza i w skrócie uzgadniania w uzgadnianiu protokołu TLS                          | PRF jest oparty na procedurach skrótu — SHA-1 + MD5, SHA-256, SHA-512 |

Struktura NX_SECURE_TLS_CIPHERSUITE_INFO jest definiowana w następujący sposób:

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
Pole nx_secure_tls_ciphersuite zawiera wartość ciphersuite organizacji IANA, a wskaźniki NX_CRYPTO_METHOD przedstawiają 5 metod używanych przez ten ciphersuite. Wartości skalarne (nx_secure_tls_iv_size, nx_secure_tls_key_size i nx_secure_tls_hash_size) są informacyjne, dostarczając informacje, które mogą nie być dostępne w wpisach NX_CRYPTO_METHOD.

Na przykład będziemy szukać domyślnego ciphersuite dla protokołu TLS TLS_RSA_WITH_AES_128_CBC_SHA, który określa użycie RSA, AES-CBC z kluczami 128-bitowymi i algorytm SHA-1 na potrzeby tworzenia skrótów sesji. Nie określono PRF TLS dla tego ciphersuite, więc w trybie TLSv 1.2 zostanie użyty domyślny PRF SHA-256. Należy pamiętać, że wszystkie ciphersuites używają algorytmu SHA-1 + MD5 PRF w protokole TLS 1,0 i 1,1, niezależnie od PRF określonych w tabeli.

Wpis w tabeli NX_SECURE_TLS_CIPHERSUITE_INFO w ogólnej bibliotece kryptograficznej jest definiowany w następujący sposób:

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

Należy pamiętać, że w przypadku szyfrowania sesji rozmiar klucza jest określany przez ciphersuite, ale w przypadku metod klucza publicznego rozmiar klucza nie jest znany, dopóki uzgadnianie protokołu TLS nie będzie możliwe, ponieważ klucze publiczne są zawarte w certyfikatach cyfrowych wymienianych podczas uzgadniania.

### <a name="x509-cipher-lookup-table"></a>Tabela odnośników szyfrowania X. 509

Podobnie jak w przypadku tabeli NX_SECURE_TLS_CIPHERSUITE_INFO, struktura NX_SECURE_X509_CRYPTO mapuje procedury kryptograficzne na znane wartości. W przypadku X. 509 identyfikatory są faktycznie identyfikatorami OID zdefiniowanymi przez X. 509 i zarejestrowane w instytucjach normalizacyjnych ISO i ITU. Identyfikatory OID są wartościami wielobajtowymi o zmiennej długości zaprojektowanych do unikatowego identyfikowania różnych informacji w różnych standardach telekomunikacyjnych, w tym procedur kryptograficznych używanych w certyfikatach cyfrowych. Ze względu na fakt, że identyfikatory OID mają zmienną długość, NetX Secure TLS mapuje oficjalne wartości identyfikatorów OID na stałe o stałej długości, które są używane wewnętrznie (patrz nx_secure_x509. h). Te stałe są używane w strukturze NX_SECURE_X509_CRYPTO, która jest zdefiniowana w następujący sposób:

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

Pierwsze pole, *nx_secure_x509_crypto_identifier*, to Wewnętrzna reprezentacja identyfikatorów OID używana przez NetX Secure.

Drugie i trzecie pola wskazują na NX_CRYPTO_METHOD obiektów, które reprezentują metody kryptograficzne identyfikowane przez OID, operacja klucza publicznego sparowana z procedurą skrótu. Należy pamiętać, że każdy certyfikat cyfrowy może mieć więcej niż jeden identyfikator OID dla procedur kryptograficznych.

Tabela metod dla X. 509 jest zbudowana w taki sam sposób jak w przypadku tabeli odnośników ciphersuite. Na przykład poszukamy identyfikatora OID dla RSA_SHA1. Rzeczywisty identyfikator OID dla RSA_SHA1 jest następujący:

```C
{iso(1) member-body(2) us(840) rsadsi(113549) pkcs(1) pkcs-1(1) sha1-with-rsa-
signature(5)}
```
Identyfikator OID jest reprezentowany w składni ASN. 1 i ma wartość liczbową 1.2.840.113549.1.1.5. Ta wartość jest następnie zakodowana w formacie binarnym, tworząc następujące bajty:

```C
UCHAR RSA_SHA1_OID = { 0x2A, 0x86, 0x48, 0x86, 0xF7, 0x0D, 0x01, 0x01, 0x05 };
```
Rzeczywista konwersja z ASN. 1 do formatu binarnego wykracza poza zakres tego dokumentu. Aby uzyskać więcej informacji, Wyszukaj numer ASN. 1 dla identyfikatorów OID. Reprezentację binarną identyfikatorów OID obsługiwanych przez NetX można znaleźć w pliku *nx_secure_x509. c*.

Gdy mamy mapowanie rzeczywistego identyfikatora OID na stałą rozpoznawaną wewnętrznie, możemy utworzyć wpis dla RSA_SHA1 w tabeli NX_SECURE_X509_CRYPTO:

```C
{ 
    NX_SECURE_TLS_X509_TYPE_RSA_SHA_1,    /* Internal OID constant. */
    &crypto_method_rsa,                   /* RSA method (NX_CRYPTO_METHOD). */ 
    &crypto_method_sha1                   /* SHA-1 method (NX_CRYPTO_METHOD). */
}, 
```
### <a name="default-tls-routines"></a>Domyślne procedury protokołu TLS

Jak wspomniano powyżej, protokół TLS wymaga pewnych domyślnych procedur do generowania kluczy i weryfikacji komunikatów podczas uzgadniania. Podstawową procedurą jest funkcja Pseudo-Random TLS lub PRF. PRF opiera się na procedurach skrótu i może służyć do generowania dowolnej ilości danych pseudo-losowych<sup>20</sup> dla generacji kluczy lub innych celów.

Oprócz PRF każda wersja protokołu TLS wykorzystuje domyślne procedury skrótu, które również muszą być dostarczone. W przypadku protokołu TLS w wersji 1,0 i 1,1 te procedury mieszania są MD5 i SHA-1. Protokół TLS w wersji 1,2 wymaga tylko algorytmu SHA-256.

W strukturze NX_SECURE_TLS_CRYPTO istnieją NX_CRYPTO_METHOD wskaźniki dla algorytmu MD5, SHA-1, SHA-256, protokołu TLS w wersji 1.0/1.1 PRF oraz domyślnego protokołu TLS 1,2 PRF.

Obsługa protokołu TLS 1,3 dodaje pola do HKDF (generowanie klucza), HMAC (dla określonych operacji tworzenia skrótów używanych podczas uzgadniania) i ECDHE (wymagane dla funkcji TLS 1,3).

Udostępnione w ogólnej bibliotece kryptografii oprogramowania są wersjami oprogramowania PRF TLS. W przypadku protokołu TLS 1.0/1.1 Ta funkcja jest wywoływana *nx_crypto_tls_prf_1*. W przypadku protokołu TLS 1,2 funkcja jest wywoływana *nx_secure_tls_prf_sha256*. Sufiks "1" reprezentuje starszą wersję protokołu TLS 1,0 PRF, a sufiks "SHA256" odnosi się do faktu, że wartość domyślna PRF protokołu TLS 1,2 jest oparta na algorytmie SHA-256. Gdy wymagana jest obsługa innych procedur PRF, sufiks tych procedur będzie odzwierciedlał użytą metodę mieszania. Ponieważ procedury PRF opierają się na metodach mieszania, bazowe procedury skrótu mogą być przyspieszane sprzętowo niezależnie od różnych platform docelowych.

Oprócz tabel odnośników TLS ciphersuite i X. 509 z domyślnymi procedurami PRF i skrótami wypełnionymi w strukturze NX_SECURE_TLS_CRYPTO można wypełnić i użyć do zainicjowania sesji TLS.

20. "Pseudo-Random" oznacza fakt, że PRF jest deterministyczna, co oznacza, że zawsze produkuje te same dane wyjściowe, które mają te same dane wejściowe, ale losowo w przypadku, gdy dane wyjściowe nie są przewidywalne. Protokół TLS wykorzystuje tę właściwość PRF, aby generować klucze sesji z różnych danych publicznych połączonych z głównym kluczem tajnym, które są wymieniane podczas uzgadniania przy użyciu szyfrowania klucza publicznego, takiego jak RSA.

### <a name="cryptographic-metadata"></a>Metadane kryptograficzne

Aby można było zainicjować sesję protokołu TLS z tabelą NX_SECURE_TLS_CRYPTO, musimy przydzielić miejsce w buforze dla metadanych procedury kryptograficznej. Metadane są używane do przechowywania wszystkich stanów skojarzonych z określoną procedurą, reprezentowane przez blok sterowania. W polu *nx_crypto_metadata_area_size* każdego NX_CRYPTO_METHOD musi być ustawiony rozmiar struktury kontroli skojarzonej z tą procedurą lub zainicjowanie protokołu TLS nie powiedzie się prawidłowo w przypadku potrzebnego miejsca, co może powodować problemy z przepełnieniem buforu.

Przed utworzeniem sesji TLS bufor metadanych musi być przydzielony. Bufor jest automatycznie dzielony przez nx_secure_tls_session_create i miejsce jest zarezerwowane dla każdej procedury, która jest dostępna w tabeli metod kryptograficznych. Należy pamiętać, że ponieważ tylko jeden ciphersuite jest aktywny w sesji TLS, liczba obsługiwanych ciphersuites nie ma wpływu na wymaganą przestrzeń metadanych — przestrzeń jest zarezerwowana dla każdej z 5 procedur ciphersuite przy użyciu maksymalnego rozmiaru bloku kontroli dla tej kategorii w tabeli odnośników ciphersuite.

Aby ułatwić Obliczanie rozmiaru buforu metadanych, usługa *nx_secure_metadata_size_calculate* wykonuje te same obliczenia co nx_secure_tls_session_create, ale po prostu zwraca łączny wymagany rozmiar buforu metadanych w bajtach.

### <a name="initializing-the-tls-session"></a>Inicjowanie sesji TLS

Po utworzeniu obiektów NX_CRYPTO_METHOD i NX_SECURE_TLS_CRYPTO i zastrzeżonym obszarze metadanych można zainicjować sesję protokołu TLS w następujący sposób (wartości pobrane z powyższych przykładów):

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
