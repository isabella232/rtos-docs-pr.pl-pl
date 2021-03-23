---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo FTP
description: Protokół transferu plików (FTP) to protokół przeznaczony do transferów plików.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1d56b20b1c7d719d1b7d9c8c5b2fe234d5577da3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821889"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-ftp"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo FTP

Protokół transferu plików (FTP) to protokół przeznaczony do transferów plików. FTP wykorzystuje niezawodne usługi Transmission Control Protocol (TCP) do wykonywania funkcji transferu plików. Z tego powodu usługa FTP jest wysoce niezawodnym protokołem transferu plików. Serwer FTP jest również wysoce wydajny. Bieżący transfer plików FTP odbywa się na dedykowanym połączeniu FTP. Usługa FTP NetX Duo obsługuje zarówno sieci IPv4, jak i IPv6. Protokół IPv6 nie zmienia bezpośrednio protokołu FTP, mimo że niektóre zmiany w oryginalnym interfejsie API FTP NetX są niezbędne do uwzględnienia protokołu IPv6 i zostaną opisane w tym dokumencie.

## <a name="ftp-requirements"></a>Wymagania dotyczące FTP

Aby zapewnić prawidłowe działanie, pakiet FTP NetX wymaga NetX Duo. Aplikacja hosta musi utworzyć wystąpienie IP dla uruchomionych usług NetX i zadań okresowych. Jeśli uruchomiona jest aplikacja hosta FTP za pośrednictwem sieci IPv6, IPv6 i ICMPv6 musi być włączona w zadaniu adresu IP. Dla sieci IPv6 lub IPv4 musi być także włączony protokół TCP. Aplikacja hosta IPv6 musi ustawić swój LINKLOCAL i globalny adres IPv6 przy użyciu interfejsu API IPv6 i/lub protokołu DHCPv6. Program demonstracyjny w sekcji "mały przykładowy system" w **rozdziale 2** demonstruje, jak to zrobić.

Serwer FTP i klient są również zaprojektowane do pracy z osadzonym systemem plików FileX. Jeśli FileX nie jest dostępna, deweloper hosta może zaimplementować lub zastąpić własny system plików zgodnie z zaleceniami sugerowanymi w filex_stub. h przez zdefiniowanie każdej usługi wymienionej w tym pliku. Zostało to omówione w kolejnych sekcjach tego przewodnika.

Część klienta FTP pakietu FTP NetX nie ma żadnych dalszych wymagań.

Część serwera FTP w pakiecie FTP NetX ma kilka dodatkowych wymagań. Najpierw wymaga pełnego dostępu do *dobrze znanego portu* TCP, aby obsłużyć wszystkie żądania poleceń FTP klienta i *dobrze znany port 20* do obsługi wszystkich transferów danych FTP klienta.

## <a name="ftp-constraints"></a>Ograniczenia FTP

Standard FTP ma wiele opcji dotyczących reprezentacji danych plików. NetX FTP nie implementuje opcji przełącznika, np. ls – Al. NetX serwer FTP oczekuje, że żądania i ich argumenty są odbierane w pojedynczym pakiecie, a nie w kolejnych pakietach.

Podobnie jak w przypadku implementacji systemu UNIX, NetX FTP przyjmuje następujące ograniczenia dotyczące formatu pliku:

- Typ pliku: dane **binarne**
- Format pliku: **tylko do drukowania**
- Struktura pliku: **tylko Struktura pliku**

## <a name="ftp-file-names"></a>Nazwy plików FTP

Nazwy plików FTP powinny mieć format docelowego systemu plików (zazwyczaj FileX). Powinny to być ciągi ASCII zakończonych znakiem NULL, z pełnymi informacjami o ścieżce, jeśli jest to konieczne. Nie ma określonego limitu rozmiaru nazw plików FTP w implementacji FTP NetX. Jednak rozmiar ładunku puli pakietów powinien być w stanie obsłużyć maksymalną ścieżkę i/lub nazwę pliku.

## <a name="ftp-client-commands"></a>Polecenia klienta FTP

FTP ma prosty mechanizm otwierania połączeń i wykonywania operacji plików i katalogów. Istnieje zasadniczo zestaw standardowych poleceń FTP, które są wydawane przez klienta po pomyślnym nawiązaniu połączenia z *dobrze znanym portem TCP 21*. Poniżej przedstawiono niektóre z podstawowych poleceń FTP. Należy zauważyć, że jedyną różnicą, gdy usługa FTP działa za pośrednictwem protokołu IPv6, to polecenie PORT jest zastępowane poleceniem EPRT:

- CWD ścieżka *zmiany katalogu roboczego*
- & nazwa *pliku*
- EPRT ip_address, port *udostępnia adres IPv6 i port danych klienta*
- EPSV *Zażądaj trybu transferu pasywnego dla protokołu IPv6*
- Wyświetlanie listy katalogów *Pobierz katalog*
- Katalog MKD *Utwórz nowy katalog*
- Katalog NLST — *Pobieranie listy katalogów*
- AKTUALIZUJĄCY nie działa *Brak operacji, zwraca sukces*
- Hasło przekazywania hasła *dla logowania*
- PASV *Zażądaj trybu transferu pasywnego dla protokołu IPv4*
- Ip_address portów, port *udostępnia adres IP i port danych klienta*
- Ścieżka do *pobrania ścieżki bieżącego katalogu*
- Zakończ *Kończenie połączenia klienta*
- RETR filename *Odczytaj określony plik*
- Katalog RMD *Usuń określony katalog*
- RNFR oldfilename *Określ plik do zmiany nazwy*
- RNTO NewFileName *Zmień nazwę pliku na podaną nazwę pliku*
- STOR filename *Zapisz określony plik*
- *Wybierz opcję obraz pliku binarnego*
- Nazwa_użytkownika użytkownika *Podaj nazwę użytkownika na potrzeby logowania*

Te polecenia ASCII są używane wewnętrznie przez oprogramowanie klienckie NetX FTP do wykonywania operacji FTP z serwerem FTP.

## <a name="ftp-server-responses"></a>Odpowiedzi serwera FTP

Gdy serwer FTP przetwarza żądanie klienta, zwraca 3-cyfrową odpowiedź zakodowaną w kodzie ASCII, po którym następuje opcjonalny tekst ASCII. Odpowiedź numeryczna jest używana przez oprogramowanie klienckie FTP do określenia, czy operacja zakończyła się powodzeniem, czy niepowodzeniem. Na poniższej liście przedstawiono różne odpowiedzi serwera FTP na żądania klientów:

**Pierwsze znaczenie pola liczbowego**

- 1XX *pozytywnego stanu wstępnego — inna odpowiedź*.
- 2xx *pozytywnego stanu ukończenia*.
- 3xx *pozytywnego stanu wstępnego — należy wysłać inne polecenie*.
- 4xx *tymczasowy warunek błędu*.
- 5xx *warunek błędu.*

**Drugie znaczenie pola liczbowego**

- x0x *błąd składniowy w poleceniu*.
- x1x *komunikat informacyjny*.
- *powiązane z usługą* X2X.
- *powiązane z uwierzytelnianiem* x3x.
- *nieokreślony* x4x.
- *powiązany system plików* x5x.

Na przykład żądanie klienta dotyczące rozłączenia połączenia FTP z poleceniem QUIT zazwyczaj reaguje na kod "221" z serwera — w przypadku pomyślnego rozłączenia.

## <a name="ftp-passive-transfer-mode"></a>Tryb pasywnego transferu FTP

Domyślnie klient FTP NetX Duo używa aktywnego trybu transportu do wymiany danych za pośrednictwem gniazda danych z serwerem FTP. Problem z tym rozmieszczeniem polega na tym, że klient FTP musi otworzyć gniazdo serwera TCP, z którym serwer FTP ma nawiązać połączenie. Oznacza to potencjalne zagrożenie bezpieczeństwa i może być blokowany przez zaporę klienta. Tryb transferu pasywnego różni się od aktywnego trybu transportu, ponieważ serwer FTP tworzy gniazdo serwera TCP na potrzeby połączenia danych. Eliminuje to zagrożenie bezpieczeństwa (dla klienta FTP).

Aby włączyć pasywny transfer danych, aplikacja wywołuje *nx_ftp_client_passive_mode_set* na wcześniej utworzonym kliencie FTP z drugim argumentem ustawionym na NX_TRUE. Następnie wszystkie kolejne usługi klienta FTP NetX Duo do przesyłania danych (NLST, RETR, STOR) są podejmowane w trybie transportu pasywnego.

Klient FTP najpierw wysyła polecenie pasywne (bez argumentów), PASV polecenie dla protokołu IPv4 lub EPSV dla protokołu IPv6. Jeśli serwer FTP obsługuje to żądanie, zwróci odpowiedź 227 "OK" dla PASV i 229 "OK" odpowiedzi na EPSV. Następnie klient wysyła żądanie, np. RETR. Jeśli serwer odmówi trybu transferu pasywnego, usługa klienta FTP NetX Duo zwróci stan błędu.

Aby wyłączyć tryb transportu pasywnego i wrócić do trybu aktywnego transportu, aplikacja wywołuje *nx_ftp_client_passive_mode_set* z drugim argumentem ustawionym na NX_FALSE.

## <a name="ftp-communication"></a>Komunikacja FTP

Serwer FTP używa *dobrze znanego portu TCP 21* w polu żądania klientów. Klienci FTP mogą korzystać z dowolnego dostępnego portu TCP. Ogólna sekwencja zdarzeń FTP jest następująca:

**Żądania odczytu pliku FTP**:

1. Problemy z klientem połączenie TCP z serwerem 21.
1. Serwer wysyła odpowiedź "220", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "użytkownik" z "username".
1. Serwer wysyła odpowiedź "331", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "PASS" z hasłem "Password" (hasło).
1. Serwer wysyła odpowiedź "230", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "TYPE I" na potrzeby transferu binarnego.
1. Serwer wysyła odpowiedź "200", aby sygnał zakończył się pomyślnie.
1. *Aplikacje IPv4*: klient wysyła komunikat "Port" z adresem IP i portem.<br />*Aplikacje IPv6*: klient wysyła komunikat "EPRT" z adresem IP i portem.
1. Serwer wysyła odpowiedź "200", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "RETR" z nazwą pliku do odczytu.
1. Serwer tworzy gniazdo danych i łączy się z portem danych klienta określonym w poleceniu "PORT".
1. Serwer wysyła odpowiedź "125" do odczytu pliku sygnału.
1. Serwer wysyła zawartość pliku za pomocą połączenia danych. Ten proces jest kontynuowany do momentu całkowitego przetransferowania pliku.
1. Po zakończeniu serwer rozłącza połączenie danych.
1. Serwer wysyła odpowiedź "250", aby odczytywanie pliku sygnału zakończyło się pomyślnie.
1. Klient wysyła "QUIT", aby zakończyć połączenie FTP.
1. Serwer wysyła odpowiedź "221", aby sygnał rozłączył się pomyślnie.
1. Serwer rozłącza połączenie FTP.

Jak wspomniano wcześniej, jedyną różnicą między usługą FTP działającą za pośrednictwem protokołu IPv4 i

IPv6 to polecenie PORT jest zastępowane poleceniem EPRT dla protokołu IPv6

Jeśli klient FTP wykonuje żądanie odczytu w trybie transferu pasywnego, sekwencja poleceń jest następująca (**pogrubione** wiersze wskazują inny krok z aktywnego trybu transferu):

1. Problemy z klientem połączenie TCP z serwerem 21.
1. Serwer wysyła odpowiedź "220", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "użytkownik" z "username".
1. Serwer wysyła odpowiedź "331", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "PASS" z hasłem "Password" (hasło).
1. Serwer wysyła odpowiedź "230", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "TYPE I" na potrzeby transferu binarnego.
1. Serwer wysyła odpowiedź "200", aby sygnał zakończył się pomyślnie.
1. ***Aplikacje IPv4:* Klient wysyła komunikat "PASV".**<br />**_Aplikacje IPv6:_ Klient wysyła komunikat "EPSV".**
1. ***Aplikacje IPv4:* Serwer wysyła odpowiedź "227" oraz adres IP i port, z którymi klient może się połączyć, aby sygnalizować powodzenie.**<br />**_Aplikacje IPv6:_ Serwer wysyła odpowiedź "229" oraz adres IP i port, z którymi klient może się połączyć, aby sygnalizować powodzenie.**
1. Klient wysyła komunikat "RETR" z nazwą pliku do odczytu.
1. **Serwer tworzy gniazdo serwera danych i nasłuchuje dla żądania połączenia klienta w tym gnieździe przy użyciu portu określonego w odpowiedzi w kroku 10.**
1. **Serwer wysyła odpowiedź "150" w gnieździe sterowania do odczytania pliku sygnału.**
1. Serwer wysyła zawartość pliku za pomocą połączenia danych. Ten proces jest kontynuowany do momentu całkowitego przetransferowania pliku.
1. Po zakończeniu serwer rozłącza połączenie danych.
1. **Serwer wysyła odpowiedź "226" w gnieździe sterowania, aby plik sygnału został pomyślnie odczytany.**
1. Klient wysyła "QUIT", aby zakończyć połączenie FTP.
1. Serwer wysyła odpowiedź "221", aby sygnał rozłączył się pomyślnie.
1. Serwer rozłącza połączenie FTP.

**Żądania zapisu FTP**:

1. Problemy z klientem połączenie TCP z serwerem 21.
1. Serwer wysyła odpowiedź "220", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "użytkownik" z "username".
1. Serwer wysyła odpowiedź "331", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "PASS" z hasłem "Password" (hasło).
1. Serwer wysyła odpowiedź "230", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "TYPE I" na potrzeby transferu binarnego.
1. Serwer wysyła odpowiedź "200", aby sygnał zakończył się pomyślnie.
1. *Aplikacje IPv4*: klient wysyła komunikat "Port" z adresem IP i portem.<br />*Aplikacje IPv6*: klient wysyła komunikat "EPRT" z adresem IP i portem.
1. Serwer wysyła odpowiedź "200", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "STOR" z nazwą pliku do zapisu.
1. Serwer tworzy gniazdo danych i łączy się z portem danych klienta określonym w poprzednim poleceniu "EPRT" lub "PORT".
1. Serwer wysyła odpowiedź "125" do zapisu pliku sygnału zostało uruchomione.
1. Klient wysyła zawartość pliku za pomocą połączenia danych. Ten proces jest kontynuowany do momentu całkowitego przetransferowania pliku.
1. Po zakończeniu klient rozłącza połączenie danych.
1. Serwer wysyła odpowiedź "250", aby zapis pliku sygnału zakończył się pomyślnie.
1. Klient wysyła "QUIT", aby zakończyć połączenie FTP.
1. Serwer wysyła odpowiedź "221", aby sygnał rozłączył się pomyślnie.
1. Serwer rozłącza połączenie FTP.

Jeśli klient FTP wykonuje żądanie zapisu w trybie transferu pasywnego, sekwencja poleceń jest następująca (**pogrubione** wiersze wskazują inny krok z aktywnego trybu transferu):

1. Problemy z klientem połączenie TCP z serwerem 21.
1. Serwer wysyła odpowiedź "220", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "użytkownik" z "username".
1. Serwer wysyła odpowiedź "331", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "PASS" z hasłem "Password" (hasło).
1. Serwer wysyła odpowiedź "230", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "TYPE I" na potrzeby transferu binarnego.
1. Serwer wysyła odpowiedź "200", aby sygnał zakończył się pomyślnie.
1. ***Aplikacje IPv4:* Klient wysyła komunikat "PASV".**<br />**_Aplikacje IPv6:_ Klient wysyła komunikat "EPSV".**
1. ***Aplikacje IPv4:* Serwer wysyła odpowiedź "227" oraz adres IP i port, z którymi klient może się połączyć, aby sygnalizować powodzenie.**<br />**_Aplikacje IPv6:_ Serwer wysyła odpowiedź "229" oraz adres IP i port, z którymi klient może się połączyć, aby sygnalizować powodzenie.**
1. Klient wysyła komunikat "STOR" z nazwą pliku do zapisu.
1. **Serwer tworzy gniazdo serwera danych i nasłuchuje dla żądania połączenia klienta w tym gnieździe przy użyciu portu określonego w odpowiedzi w kroku 10.**
1. **Serwer wysyła odpowiedź "150" w gnieździe sterowania, aby został uruchomiony zapis pliku sygnału.**
1. Klient wysyła zawartość pliku za pomocą połączenia danych. Ten proces jest kontynuowany do momentu całkowitego przetransferowania pliku.
1. Po zakończeniu klient rozłącza połączenie danych.
1. **Serwer wysyła odpowiedź "226" w gnieździe sterowania, aby sygnał zapisu pliku zakończył się pomyślnie.**
1. Klient wysyła "QUIT", aby zakończyć połączenie FTP.
1. Serwer wysyła odpowiedź "221", aby sygnał rozłączył się pomyślnie.
1. Serwer rozłącza połączenie FTP.

## <a name="ftp-authentication"></a>Uwierzytelnianie FTP

Za każdym razem, gdy ma miejsce połączenie FTP, klient musi podać *nazwę użytkownika* i *hasło*. Niektóre witryny FTP zezwalają na to, co jest nazywane *anonimową FTP*, co umożliwia dostęp do usługi FTP bez określonej nazwy użytkownika i hasła. Dla tego typu połączenia należy podać wartość "Anonymous" dla nazwy użytkownika, a hasło powinno być kompletnym adresem e-mail.

Użytkownik jest odpowiedzialny za dostarczanie NetX FTP z procedurami uwierzytelniania logowania i wylogowywania. Są one dostarczane w ramach usług ***nxd_ftp_server_create** _ i _*_nx_ftp_server_create_*_ i wywoływane z przetwarzania haseł. Różnica między nimi polega na tym, że wskaźniki funkcji wejścia _*_nxd_ftp_server_create_*_ są używane do logowania i wylogowywania funkcji uwierzytelniania, oczekiwano typu adresu NetX Duo _*_NXD_ADDRESS_*_. Ten typ danych zawiera formaty adresów IPv4 lub IPv6, dzięki czemu ta funkcja jest usługą "Duo" obsługującą zarówno sieci IPv4, jak i IPv6. Funkcja input programu _ *_nx_ftp_server_create_**, która umożliwia zalogowanie i wylogowanie się, oczekuje ULONG typu adresu IP. Ta funkcja jest ograniczona do sieci IPv4. Deweloperzy są zachęcani do korzystania z usługi "Duo" wszędzie tam, gdzie to możliwe.

Jeśli funkcja *logowania* zwróci NX_SUCCESS, połączenie zostanie uwierzytelnione i operacje FTP są dozwolone. W przeciwnym razie, jeśli funkcja *logowania* zwróci coś innego niż NX_SUCCESS, próba połączenia zostanie odrzucona.

## <a name="ftp-multi-thread-support"></a>Obsługa wielowątkowości FTP

Usługi klienta FTP NetX można wywołać z wielu wątków jednocześnie. Jednak żądania odczytu lub zapisu dla danego wystąpienia klienta FTP powinny być wykonywane w kolejności z tego samego wątku.

## <a name="ftp-rfcs"></a>Specyfikacje RFC protokołu FTP

Usługa FTP NetX Duo jest zgodna ze standardami RFC 959, RFC 2428 i pokrewnymi specyfikacjami RFC.
