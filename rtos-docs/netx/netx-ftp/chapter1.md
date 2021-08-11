---
title: Rozdział 1 — Wprowadzenie do Azure RTOS NetX FTP
description: Protokół protokół transferu plików (FTP) to protokół przeznaczony do transferów plików. Ftp wykorzystuje niezawodne usługi Transmission Control Protocol (TCP) do wykonywania funkcji transferu plików.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 35a7487720578ce8da578c490d96aa3c444ee818167b1bbd10833556e34b3dce
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799476"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-ftp"></a>Rozdział 1 — Wprowadzenie do Azure RTOS NetX FTP

Protokół protokół transferu plików (FTP) to protokół przeznaczony do transferów plików. Ftp wykorzystuje niezawodne usługi Transmission Control Protocol (TCP) do wykonywania funkcji transferu plików. W związku z tym FTP jest protokołem transferu plików o wysokiej niezawodności. Ftp jest również o wysokiej wydajności. Rzeczywisty transfer plików FTP jest wykonywany na dedykowanym połączeniu FTP.

## <a name="ftp-requirements"></a>Wymagania dotyczące protokołu FTP

Aby można było prawidłowo działać, Azure RTOS FTP NetX wymaga, aby wystąpienie adresu IP NetX zostało już utworzone. Ponadto protokół TCP musi być włączony w tym samym wystąpieniu adresu IP. Część klienta FTP pakietu FTP NetX nie ma dodatkowych wymagań.

Część serwera FTP w pakiecie FTP NetX ma kilka dodatkowych wymagań. Po pierwsze wymaga pełnego dostępu do dobrze znanego portu *TCP 21* do obsługi wszystkich żądań poleceń ftp klienta oraz dobrze znanego portu *20* do obsługi wszystkich transferów danych FTP klienta. Serwer FTP jest również przeznaczony do użytku z osadzonym systemem plików FileX. Jeśli plik FileX nie jest dostępny, użytkownik może portować części pliku FileX używane do własnego środowiska. Omówiono to w kolejnych sekcjach tego przewodnika.

## <a name="ftp-constraints"></a>Ograniczenia FTP

Standard FTP ma wiele opcji dotyczących reprezentacji danych plików. Podobnie jak w przypadku implementacji systemu Unix, protokół FTP NetX zakłada następujące ograniczenia formatu pliku:

- Typ pliku: **Binarny**
- Format pliku: **tylko bez odcisku**
- Struktura pliku: **Tylko struktura plików**
- Tryb transmisji: **tylko tryb strumienia**

## <a name="ftp-file-names"></a>Nazwy plików FTP

Nazwy plików FTP powinny być w formacie docelowego systemu plików (zazwyczaj FileX). Powinny to być ciągi ASCII zakończone wartością NULL z pełnymi informacjami o ścieżce, jeśli jest to konieczne. Nie ma określonego limitu rozmiaru nazw plików FTP w implementacji protokołu FTP NetX. Jednak rozmiar ładunku puli pakietów powinien być w stanie obsłużyć maksymalną ścieżkę i/lub nazwę pliku.

## <a name="ftp-client-commands"></a>Polecenia klienta FTP

Ftp ma prosty mechanizm otwierania połączeń i wykonywania operacji na plikach i katalogach. Zasadniczo istnieje zestaw standardowych poleceń FTP, które są wydawane przez klienta po pomyślnym nawiązaniu połączenia na dobrze znanym porcie TCP *21.* Poniżej przedstawiono niektóre z podstawowych poleceń FTP:

### <a name="ftp-command-and-meaning"></a>Ftp , polecenie i znaczenie

- **Ścieżka CWD:** *zmiana katalogu roboczego*
- **Nazwa pliku DELE:** *Usuń określoną nazwę pliku*
- **KATALOG LIST:** *Pobierz listę katalogów*
- **Katalog MKD:** Make new directory (Katalog MKD): *Make new directory (Udostępnij nowy katalog)*
- **Katalog NLST:** *Pobierz listę katalogów*
- **NOOP:** *Brak operacji, zwraca powodzenie*
- **PASS password** *:Podaj hasło do logowania*
- **PASV:** *żądanie pasywnego trybu transferu*
- **Ścieżka pwD:** *ścieżka bieżącego katalogu odbioru*
- **ZAMKNIJ:** *Zakończ połączenie klienta*
- Retr filename : Read specified file **(Nazwa pliku RETR:** *odczyt określonego pliku)*
- **Katalog RMD:** *Usuń określony katalog*
- **RNFR oldfilename:** *Określ plik do zmiany nazwy*
- **RNTO newfilename:** *Zmień nazwę pliku na podaną nazwę pliku*
- **STOR filename:** *Zapisz określony plik*
- **TYP I:** *Wybieranie obrazu pliku binarnego*
- **Nazwa użytkownika:** *podaj nazwę użytkownika do logowania*
- **PORT ip_address,port:** *Podaj adres IP i port danych klienta*

Te polecenia ASCII są używane wewnętrznie przez oprogramowanie klienckie NetX FTP do wykonywania operacji FTP na serwerze FTP.

## <a name="ftp-server-responses"></a>Odpowiedzi serwera FTP

Serwer FTP używa dobrze znanego portu *TCP 21* do pola Żądania poleceń klienta. Gdy serwer FTP przetwarza polecenie Client, zwraca 3-cyfrową odpowiedź liczbową w ascii, po której następuje opcjonalny ciąg ASCII. Odpowiedź liczbowa jest używana przez oprogramowanie klienckie FTP do określenia, czy operacja zakończyła się powodzeniem, czy niepowodzeniem. Poniżej wymieniono różne odpowiedzi serwera FTP na polecenia klienta:

### <a name="first-numeric-field-and-meaning"></a>Pierwsze pole liczbowe i znaczenie

- **1xx:** *Dodatni stan wstępny — nadchodzą kolejna odpowiedź.*
- **2xx:** *Dodatni stan ukończenia.*
- **3xx:** *Dodatni stan wstępny — należy wysłać inne polecenie*.
- **4xx:** Tymczasowy *warunek błędu*.
- **5xx:** *Warunek błędu.*

### <a name="second-numeric-field-and-meaning"></a>Drugie pole liczbowe i znaczenie

- **x0x:** błąd składni w poleceniu.
- **x1x:** komunikat informacyjny.
- **x2x:** związane z połączeniem.
- **x3x:** związane z uwierzytelnianiem.
- **x4x:** nieokreślony.
- **x5x:** związane z systemem plików.

Na przykład żądanie klienta dotyczące odłączenia połączenia FTP z poleceniem QUIT zwykle będzie odpowiadać kodem "221" z serwera — jeśli rozłączenie zakończy się pomyślnie.

## <a name="ftp-passive-transfer-mode"></a>Pasywny tryb transferu FTP

Domyślnie klient FTP NetX używa trybu aktywnego transportu do wymiany danych za pośrednictwem gniazda danych z serwerem FTP. Problem z tym rozmieszczeniem polega na tym, że klient FTP musi otworzyć gniazdo serwera TCP, z którym ma nawiązać połączenie serwer FTP. Reprezentuje to możliwe zagrożenie bezpieczeństwa i może zostać zablokowane przez zaporę klienta. Pasywny tryb transferu różni się od trybu transportu aktywnego przez utworzenie gniazda serwera TCP przez serwer FTP w połączeniu danych. Eliminuje to zagrożenie bezpieczeństwa (w przypadku klienta FTP).

Aby włączyć pasywny transfer danych, aplikacja wywołuje *nx_ftp_client_passive_mode_set* wcześniej utworzonego klienta FTP z drugim argumentem ustawionym na NX_TRUE. Następnie wszystkie kolejne usługi klienta FTP NetX w celu transferu danych (NLST, RETR, STOR) będą próbowane w trybie pasywnego transportu.

Klient FTP najpierw wysyła polecenie PASV (bez argumentów). Jeśli serwer FTP obsługuje to żądanie, zwróci odpowiedź 227 "OK". Następnie klient wysyła żądanie, np. RETR. Jeśli serwer odmawia pasywnego trybu transferu, usługa klienta FTP NetX zwraca stan błędu.

Aby wyłączyć pasywny tryb transportu i powrócić do trybu aktywnego transportu, aplikacja wywołuje nx_ftp_client_passive_mode_set *z* drugim argumentem ustawionym na NX_FALSE.

## <a name="ftp-communication"></a>Komunikacja FTP

Serwer FTP używa dobrze znanego portu *TCP 21* do pola Żądania klienta. Klienci FTP mogą używać dowolnego dostępnego portu TCP. Ogólna sekwencja zdarzeń FTP jest następująca:

### <a name="ftp-read-file-requests"></a>Żądania odczytu pliku FTP

1. Problemy z klientem: połączenie TCP z portem 21 serwera.
1. Serwer wysyła odpowiedź "220" w celu sygnalizowania powodzenia.
1. Klient wysyła komunikat "USER" z "username".
1. Serwer wysyła odpowiedź "331", aby zasygnalizować powodzenie.
1. Klient wysyła komunikat "PASS" z hasłem.
1. Serwer wysyła odpowiedź "230", aby zasygnalizować powodzenie.
1. Klient wysyła komunikat "TYP I" dla transferu binarnego.
1. Serwer wysyła odpowiedź "200" w celu sygnalizowania powodzenia.
1. Klient wysyła komunikat "PORT" z adresem IP i portem.
1. Serwer wysyła odpowiedź "200" w celu sygnalizowania powodzenia.
1. Klient wysyła komunikat "RETR" z nazwą pliku do odczytu.
1. Serwer tworzy gniazdo danych i nawiązuje połączenie przy użyciu portu danych klienta określonego w poleceniu "PORT".
1. Serwer wysyła odpowiedź "125" na sygnał odczytany plik został uruchomiony.
1. Serwer wysyła zawartość pliku za pośrednictwem połączenia danych. Ten proces jest kontynuowany do momentu całkowitego transferu pliku.
1. Po zakończeniu serwer rozłącza połączenie danych.
1. Serwer wysyła odpowiedź "250" na komunikat o pomyślnym odczycie pliku.
1. Klienci wysyłają komunikat "QUIT" w celu zakończenia połączenia FTP.
1. Serwer wysyła odpowiedź "221", aby sygnał rozłączenia został pomyślnie rozłączny.
1. Serwer rozłącza połączenie FTP.

Jak wspomniano wcześniej, jedyną różnicą między FTP uruchomione za pośrednictwem protokołu IPv4 i IPv6 jest port polecenie jest zastępowany EPRT polecenia dla protokołu IPv6

Jeśli klient FTP wysyła żądanie odczytu w trybie pasywnego transferu, sekwencja poleceń jest następująca (pogrubione wiersze wskazują inny krok niż aktywny tryb transferu):

1. Problemy z klientem: połączenie TCP z portem 21 serwera.
1. Serwer wysyła odpowiedź "220", aby zasygnalizować powodzenie.
1. Klient wysyła komunikat "USER" z "username".
1. Serwer wysyła odpowiedź "331", aby zasygnalizować powodzenie.
1. Klient wysyła komunikat "PASS" z hasłem.
1. Serwer wysyła odpowiedź "230" w celu sygnalizowania powodzenia.
1. Klient wysyła komunikat "TYP I" dla transferu binarnego.
1. Serwer wysyła odpowiedź "200" w celu sygnalizowania powodzenia.
1. **Klient wysyła komunikat "PASV".**
1. **Serwer wysyła odpowiedź "227" oraz adres IP i port, z którym klient może się połączyć, aby zasygnalizować powodzenie.**
1. Klient wysyła komunikat "RETR" z nazwą pliku do odczytu.
1. **Serwer tworzy gniazdo serwera danych i nasłuchuje żądania połączenia klienta na tym gnieździe przy użyciu portu określonego w odpowiedzi "227".**
1. **Serwer wysyła odpowiedź "150" na gniazdo sterowania, aby zasygnalizować, że rozpoczęto odczytywanie pliku.**
1. Serwer wysyła zawartość pliku za pośrednictwem połączenia danych. Ten proces jest kontynuowany do momentu całkowitego transferu pliku.
1. Po zakończeniu serwer rozłącza połączenie danych.
1. **Serwer wysyła odpowiedź "226" na gnieździe sterującym, aby sygnał odczytu pliku został pomyślnie odczytany.**
1. Klient wysyła komunikat "QUIT" w celu zakończenia połączenia FTP.
1. Serwer wysyła odpowiedź "221", aby sygnał rozłączenia został pomyślnie rozłączny.
1. Serwer rozłącza połączenie FTP.

### <a name="ftp-write-requests"></a>Żądania zapisu FTP

1. Problemy z klientem: połączenie TCP z portem 21 serwera.
1. Serwer wysyła odpowiedź "220", aby zasygnalizować powodzenie.
1. Klient wysyła komunikat "USER" z "username".
1. Serwer wysyła odpowiedź "331", aby zasygnalizować powodzenie.
1. Klient wysyła komunikat "PASS" z hasłem.
1. Serwer wysyła odpowiedź "230" w celu sygnalizowania powodzenia.
1. Klient wysyła komunikat "TYP I" dla transferu binarnego.
1. Serwer wysyła odpowiedź "200" w celu sygnalizowania powodzenia.
1. Klient wysyła komunikat "PORT" z adresem IP i portem.
1. Serwer wysyła odpowiedź "200" w celu sygnalizowania powodzenia.
1. Klient wysyła komunikat "STOR" z nazwą pliku do zapisu.
1. Serwer tworzy gniazdo danych i nawiązuje połączenie przy użyciu portu danych klienta określonego w poleceniu "PORT".
1. Serwer wysyła odpowiedź "125" na sygnał zapisu pliku została uruchomiona.
1. Klient wysyła zawartość pliku za pośrednictwem połączenia danych. Ten proces jest kontynuowany do momentu całkowitego transferu pliku.
1. Po zakończeniu klient rozłącza połączenie danych.
1. Serwer wysyła odpowiedź "250" na komunikat o pomyślnym zapisie pliku.
1. Klienci wysyłają komunikat "QUIT" w celu zakończenia połączenia FTP.
1. Serwer wysyła odpowiedź "221", aby sygnał rozłączenia został pomyślnie rozłączny.
1. Serwer rozłącza połączenie FTP.

Jeśli klient FTP wysyła żądanie zapisu w trybie pasywnego transferu, sekwencja poleceń jest następująca (pogrubione wiersze wskazują inny krok w trybie aktywnego transferu):

1. Problemy z klientem: połączenie TCP z portem 21 serwera.
1. Serwer wysyła odpowiedź "220", aby zasygnalizować powodzenie.
1. Klient wysyła komunikat "USER" z "username".
1. Serwer wysyła odpowiedź "331", aby zasygnalizować powodzenie.
1. Klient wysyła komunikat "PASS" z hasłem.
1. Serwer wysyła odpowiedź "230" w celu sygnalizowania powodzenia.
1. Klient wysyła komunikat "TYP I" dla transferu binarnego.
1. Serwer wysyła odpowiedź "200" w celu sygnalizowania powodzenia.
1. **Klient wysyła komunikat "PASV".**
1. **Serwer wysyła odpowiedź "227" oraz adres IP i port, z którym klient może się połączyć, aby zasygnalizować powodzenie.**
1. Klient wysyła komunikat "STOR" z nazwą pliku do zapisu.
1. **Serwer tworzy gniazdo serwera danych i nasłuchuje żądania połączenia klienta na tym gnieździe przy użyciu portu określonego w odpowiedzi "227".**
1. **Serwer wysyła odpowiedź "150" na gniazdo sterowania, aby zasygnalizować, że rozpoczęto zapis pliku.**
1. Klient wysyła zawartość pliku za pośrednictwem połączenia danych. Ten proces jest kontynuowany do momentu całkowitego transferu pliku.
1. Po zakończeniu klient rozłącza połączenie danych.
1. **Serwer wysyła odpowiedź "226" na gnieździe sterującym, aby zasygnalizować powodzenie zapisu pliku.**
1. Klient wysyła komunikat "QUIT" w celu zakończenia połączenia FTP.
1. Serwer wysyła odpowiedź "221", aby sygnał rozłączenia został pomyślnie rozłączny.
1. Serwer rozłącza połączenie FTP.

## <a name="ftp-authentication"></a>Uwierzytelnianie FTP

Przy każdym nawiązaniu połączenia FTP klient musi podać serwerowi nazwę *użytkownika i* *hasło*. Niektóre witryny FTP zezwalają na dostęp do protokołu *FTP* anonimowego bez określonej nazwy użytkownika i hasła. W przypadku tego typu połączenia jako nazwę użytkownika należy podać "anonimowe", a hasło powinno być kompletnym adresem e-mail.

Użytkownik jest odpowiedzialny za dostarczenie protokołu FTP NetX z procedurami uwierzytelniania logowania i wylogowania. Są one dostarczane podczas funkcji ***nx_ftp_server_create** _ i wywoływane z przetwarzania haseł. Jeśli funkcja _login* zwróci NX_SUCCESS, połączenie zostanie uwierzytelnione i operacje FTP będą dozwolone. W przeciwnym razie, *jeśli funkcja logowania* zwróci wartość inną NX_SUCCESS, próba połączenia zostanie odrzucona.

## <a name="ftp-multi-thread-support"></a>Obsługa wielu wątków FTP

Usługi klienta FTP NetX mogą być wywoływane z wielu wątków jednocześnie. Jednak żądania odczytu lub zapisu dla określonego wystąpienia klienta FTP powinny być wykonywane kolejno z tego samego wątku.

## <a name="ftp-rfcs"></a>RFC FTP

Protokół FTP NetX jest zgodny ze specyfikacją RFC959 i powiązanymi RFC.