---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX FTP
description: Protokół transferu plików (FTP) to protokół przeznaczony do transferów plików. FTP wykorzystuje niezawodne usługi Transmission Control Protocol (TCP) do wykonywania funkcji transferu plików.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 86e132daf96f9039631234f10c8e239b61ad5126
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822638"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-ftp"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO NetX FTP

Protokół transferu plików (FTP) to protokół przeznaczony do transferów plików. FTP wykorzystuje niezawodne usługi Transmission Control Protocol (TCP) do wykonywania funkcji transferu plików. Z tego powodu usługa FTP jest wysoce niezawodnym protokołem transferu plików. Serwer FTP jest również wysoce wydajny. Bieżący transfer plików FTP odbywa się na dedykowanym połączeniu FTP.

## <a name="ftp-requirements"></a>Wymagania dotyczące FTP

Aby zapewnić prawidłowe działanie, pakiet FTP usługi Azure RTO NetX wymaga, aby wystąpienie adresu IP NetX zostało już utworzone. Ponadto należy włączyć protokół TCP dla tego samego wystąpienia IP. Część klienta FTP pakietu FTP NetX nie ma żadnych dalszych wymagań.

Część serwera FTP w pakiecie FTP NetX ma kilka dodatkowych wymagań. Najpierw wymaga pełnego dostępu do *dobrze znanego portu* TCP, aby obsłużyć wszystkie żądania poleceń FTP klienta i *dobrze znany port 20* do obsługi wszystkich transferów danych FTP klienta. Serwer FTP jest również przeznaczony do użycia z osadzonym systemem plików FileX. Jeśli FileX nie jest dostępna, użytkownik może przenieść fragmenty FileX używane w ich własnym środowisku. Zostało to omówione w kolejnych sekcjach tego przewodnika.

## <a name="ftp-constraints"></a>Ograniczenia FTP

Standard FTP ma wiele opcji dotyczących reprezentacji danych plików. Podobnie jak w przypadku implementacji systemu UNIX, NetX FTP przyjmuje następujące ograniczenia dotyczące formatu pliku:

- Typ pliku: dane **binarne**
- Format pliku: **tylko do drukowania**
- Struktura pliku: **tylko Struktura pliku**
- Tryb transmisji: **tylko tryb strumienia**

## <a name="ftp-file-names"></a>Nazwy plików FTP

Nazwy plików FTP powinny mieć format docelowego systemu plików (zazwyczaj FileX). Powinny to być ciągi ASCII zakończonych znakiem NULL, z pełnymi informacjami o ścieżce, jeśli jest to konieczne. Nie ma określonego limitu rozmiaru nazw plików FTP w implementacji FTP NetX. Jednak rozmiar ładunku puli pakietów powinien być w stanie obsłużyć maksymalną ścieżkę i/lub nazwę pliku.

## <a name="ftp-client-commands"></a>Polecenia klienta FTP

FTP ma prosty mechanizm otwierania połączeń i wykonywania operacji plików i katalogów. Istnieje zasadniczo zestaw standardowych poleceń FTP, które są wydawane przez klienta po pomyślnym nawiązaniu połączenia z *dobrze znanym portem TCP 21*. Poniżej przedstawiono niektóre z podstawowych poleceń FTP:

### <a name="ftp-command-and-meaning"></a>FTP polecenie i znaczenie

- **Ścieżka CWD**: *Zmień katalog roboczy*
- **& Filename**: *Usuń określoną nazwę pliku*
- **Lista katalogów**: *Pobieranie listy katalogów*
- **Katalog MKD**: *Utwórz nowy katalog*
- **Katalog NLST**: *Pobieranie listy katalogów*
- **Aktualizujący nie działa**: *Brak operacji, zwraca sukces*
- **Przekaż hasło**: *Podaj hasło do logowania*
- **PASV**: *Zażądaj trybu transferu pasywnego*
- **Ścieżka PWD**: *odbiór bieżącej ścieżki katalogu*
- **Kończenie**: *Przerywanie połączenia klienta*
- **Nazwa pliku RETR**: *Odczytaj określony plik*
- **Katalog RMD**: *usuwanie określonego katalogu*
- **RNFR oldfilename**: *Określ plik do zmiany nazwy*
- **RNTO NewFileName**: *Zmień nazwę pliku na podaną nazwę pliku*
- **Stor filename**: *Napisz określony plik*
- **Typ I**: *Wybierz obraz pliku binarnego*
- **Nazwa_użytkownika użytkownika**: *Podaj nazwę użytkownika na potrzeby logowania*
- Port **IP_address, port**: *Podaj adres IP i port danych klienta*

Te polecenia ASCII są używane wewnętrznie przez oprogramowanie klienckie NetX FTP do wykonywania operacji FTP z serwerem FTP.

## <a name="ftp-server-responses"></a>Odpowiedzi serwera FTP

Serwer FTP używa *dobrze znanego portu TCP 21* do żądania poleceń klienta. Gdy serwer FTP przetworzy polecenie klienta, zwraca 3-cyfrową odpowiedź liczbową w kodzie ASCII, a po niej opcjonalny ciąg ASCII. Odpowiedź numeryczna jest używana przez oprogramowanie klienckie FTP do określenia, czy operacja zakończyła się powodzeniem, czy niepowodzeniem. Poniżej wymieniono różne odpowiedzi serwera FTP do poleceń klienta:

### <a name="first-numeric-field-and-meaning"></a>Pierwsze pole liczbowe i znaczenie

- **1XX**: *pozytywny stan wstępny — inna odpowiedź*.
- **2xx**: *stan ukończenia pozytywnej*.
- **3xx**: *dodatniy stan wstępny — należy wysłać inne polecenie*.
- **4xx**: *tymczasowy warunek błędu*.
- **5xx**: *warunek błędu.*

### <a name="second-numeric-field-and-meaning"></a>Drugie pole liczbowe i znaczenie

- **x0x**: błąd składniowy w poleceniu.
- **x1x**: komunikat informacyjny.
- **X2X**: powiązane z połączeniem.
- **x3x**: powiązane uwierzytelnianie.
- **x4x**: nieokreślony.
- **x5x**: powiązane z systemem plików.

Na przykład żądanie klienta dotyczące rozłączenia połączenia FTP z poleceniem QUIT zazwyczaj reaguje na kod "221" z serwera — w przypadku pomyślnego rozłączenia.

## <a name="ftp-passive-transfer-mode"></a>Tryb pasywnego transferu FTP

Domyślnie klient FTP NetX używa aktywnego trybu transportu do wymiany danych za pośrednictwem gniazda danych z serwerem FTP. Problem z tym rozmieszczeniem polega na tym, że klient FTP musi otworzyć gniazdo serwera TCP, z którym serwer FTP ma nawiązać połączenie. Oznacza to potencjalne zagrożenie bezpieczeństwa i może być blokowany przez zaporę klienta. Tryb transferu pasywnego różni się od aktywnego trybu transportu, ponieważ serwer FTP tworzy gniazdo serwera TCP na potrzeby połączenia danych. Eliminuje to zagrożenie bezpieczeństwa (dla klienta FTP).

Aby włączyć pasywny transfer danych, aplikacja wywołuje *nx_ftp_client_passive_mode_set* na wcześniej utworzonym kliencie FTP z drugim argumentem ustawionym na NX_TRUE. Następnie wszystkie kolejne usługi NetX FTP Client do przesyłania danych (NLST, RETR, STOR) są wypróbowywane w trybie transportu pasywnego.

Klient FTP najpierw wysyła polecenie PASV (bez argumentów). Jeśli serwer FTP obsługuje to żądanie, zwróci odpowiedź 227 "OK". Następnie klient wysyła żądanie, np. RETR. Jeśli serwer odmówi trybu transferu pasywnego, usługa klienta FTP NetX zwraca stan błędu.

Aby wyłączyć tryb transportu pasywnego i wrócić do trybu aktywnego transportu, aplikacja wywołuje *nx_ftp_client_passive_mode_set* z drugim argumentem ustawionym na NX_FALSE.

## <a name="ftp-communication"></a>Komunikacja FTP

Serwer FTP używa *dobrze znanego portu TCP 21* w polu żądania klientów. Klienci FTP mogą korzystać z dowolnego dostępnego portu TCP. Ogólna sekwencja zdarzeń FTP jest następująca:

### <a name="ftp-read-file-requests"></a>Żądania odczytu plików FTP

1. Problemy z klientem połączenie TCP z serwerem 21.
1. Serwer wysyła odpowiedź "220", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "użytkownik" z "username".
1. Serwer wysyła odpowiedź "331", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "PASS" z hasłem "Password" (hasło).
1. Serwer wysyła odpowiedź "230", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "TYPE I" na potrzeby transferu binarnego.
1. Serwer wysyła odpowiedź "200", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "PORT" z adresem IP i portem.
1. Serwer wysyła odpowiedź "200", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "RETR" z nazwą pliku do odczytu.
1. Serwer tworzy gniazdo danych i łączy się z portem danych klienta określonym w poleceniu "PORT".
1. Serwer wysyła odpowiedź "125" do odczytu pliku sygnału.
1. Serwer wysyła zawartość pliku za pomocą połączenia danych. Ten proces jest kontynuowany do momentu całkowitego przetransferowania pliku.
1. Po zakończeniu serwer rozłącza połączenie danych.
1. Serwer wysyła odpowiedź "250", aby odczytywanie pliku sygnału zakończyło się pomyślnie.
1. Klienci wysyłają "QUIT", aby zakończyć połączenie FTP.
1. Serwer wysyła odpowiedź "221", aby sygnał rozłączył się pomyślnie.
1. Serwer rozłącza połączenie FTP.

Jak wspomniano wcześniej, jedyną różnicą między usługą FTP uruchomioną za pośrednictwem protokołu IPv4 i IPv6 jest polecenie PORT jest zastępowane poleceniem EPRT dla protokołu IPv6

Jeśli klient FTP wykonuje żądanie odczytu w trybie transferu pasywnego, sekwencja poleceń jest następująca (**pogrubione** wiersze wskazują inny krok z aktywnego trybu transferu):

1. Problemy z klientem połączenie TCP z serwerem 21.
1. Serwer wysyła odpowiedź "220", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "użytkownik" z "username".
1. Serwer wysyła odpowiedź "331", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "PASS" z hasłem "Password" (hasło).
1. Serwer wysyła odpowiedź "230", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "TYPE I" na potrzeby transferu binarnego.
1. Serwer wysyła odpowiedź "200", aby sygnał zakończył się pomyślnie.
1. **Klient wysyła komunikat "PASV".**
1. **Serwer wysyła odpowiedź "227" oraz adres IP i port, z którymi klient może się połączyć, aby sygnalizować powodzenie.**
1. Klient wysyła komunikat "RETR" z nazwą pliku do odczytu.
1. **Serwer tworzy gniazdo serwera danych i nasłuchuje dla żądania połączenia klienta w tym gnieździe przy użyciu portu określonego w odpowiedzi "227".**
1. **Serwer wysyła odpowiedź "150" w gnieździe sterowania do odczytania pliku sygnału.**
1. Serwer wysyła zawartość pliku za pomocą połączenia danych. Ten proces jest kontynuowany do momentu całkowitego przetransferowania pliku.
1. Po zakończeniu serwer rozłącza połączenie danych.
1. **Serwer wysyła odpowiedź "226" w gnieździe sterowania, aby plik sygnału został pomyślnie odczytany.**
1. Klient wysyła "QUIT", aby zakończyć połączenie FTP.
1. Serwer wysyła odpowiedź "221", aby sygnał rozłączył się pomyślnie.
1. Serwer rozłącza połączenie FTP.

### <a name="ftp-write-requests"></a>Żądania zapisu FTP

1. Problemy z klientem połączenie TCP z serwerem 21.
1. Serwer wysyła odpowiedź "220", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "użytkownik" z "username".
1. Serwer wysyła odpowiedź "331", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "PASS" z hasłem "Password" (hasło).
1. Serwer wysyła odpowiedź "230", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "TYPE I" na potrzeby transferu binarnego.
1. Serwer wysyła odpowiedź "200", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "PORT" z adresem IP i portem.
1. Serwer wysyła odpowiedź "200", aby sygnał zakończył się pomyślnie.
1. Klient wysyła komunikat "STOR" z nazwą pliku do zapisu.
1. Serwer tworzy gniazdo danych i łączy się z portem danych klienta określonym w poleceniu "PORT".
1. Serwer wysyła odpowiedź "125" do zapisu pliku sygnału zostało uruchomione.
1. Klient wysyła zawartość pliku za pomocą połączenia danych. Ten proces jest kontynuowany do momentu całkowitego przetransferowania pliku.
1. Po zakończeniu klient rozłącza połączenie danych.
1. Serwer wysyła odpowiedź "250", aby zapis pliku sygnału zakończył się pomyślnie.
1. Klienci wysyłają "QUIT", aby zakończyć połączenie FTP.
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
1. **Klient wysyła komunikat "PASV".**
1. **Serwer wysyła odpowiedź "227" oraz adres IP i port, z którymi klient może się połączyć, aby sygnalizować powodzenie.**
1. Klient wysyła komunikat "STOR" z nazwą pliku do zapisu.
1. **Serwer tworzy gniazdo serwera danych i nasłuchuje dla żądania połączenia klienta w tym gnieździe przy użyciu portu określonego w odpowiedzi "227".**
1. **Serwer wysyła odpowiedź "150" w gnieździe sterowania, aby został uruchomiony zapis pliku sygnału.**
1. Klient wysyła zawartość pliku za pomocą połączenia danych. Ten proces jest kontynuowany do momentu całkowitego przetransferowania pliku.
1. Po zakończeniu klient rozłącza połączenie danych.
1. **Serwer wysyła odpowiedź "226" w gnieździe sterowania, aby sygnał zapisu pliku zakończył się pomyślnie.**
1. Klient wysyła "QUIT", aby zakończyć połączenie FTP.
1. Serwer wysyła odpowiedź "221", aby sygnał rozłączył się pomyślnie.
1. Serwer rozłącza połączenie FTP.

## <a name="ftp-authentication"></a>Uwierzytelnianie FTP

Za każdym razem, gdy ma miejsce połączenie FTP, klient musi podać *nazwę użytkownika* i *hasło*. Niektóre witryny FTP zezwalają na to, co jest nazywane *anonimową FTP*, co umożliwia dostęp do usługi FTP bez określonej nazwy użytkownika i hasła. Dla tego typu połączenia należy podać wartość "Anonymous" dla nazwy użytkownika, a hasło powinno być kompletnym adresem e-mail.

Użytkownik jest odpowiedzialny za dostarczanie NetX FTP z procedurami uwierzytelniania logowania i wylogowywania. Są one dostarczane podczas funkcji ***nx_ftp_server_create** _ i wywoływanej z przetwarzania hasła. Jeśli funkcja _login * zwróci NX_SUCCESS, połączenie zostanie uwierzytelnione i operacje FTP są dozwolone. W przeciwnym razie, jeśli funkcja *logowania* zwróci coś innego niż NX_SUCCESS, próba połączenia zostanie odrzucona.

## <a name="ftp-multi-thread-support"></a>Obsługa wielowątkowości FTP

Usługi klienta FTP NetX można wywołać z wielu wątków jednocześnie. Jednak żądania odczytu lub zapisu dla danego wystąpienia klienta FTP powinny być wykonywane w kolejności z tego samego wątku.

## <a name="ftp-rfcs"></a>Specyfikacje RFC protokołu FTP

NetX FTP jest zgodna z RFC959 i pokrewnymi specyfikacjami RFC.