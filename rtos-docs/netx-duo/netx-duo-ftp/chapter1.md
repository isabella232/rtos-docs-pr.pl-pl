---
title: Rozdział 1 — Wprowadzenie do usługi Azure RTOS NetX Duo FTP
description: Protokół protokół transferu plików (FTP) to protokół przeznaczony do transferów plików.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a36357ce486d5ba8a68b23c829de6c4b821dfb3cc62f47b0958ff32deaa2f7a7
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791299"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-ftp"></a>Rozdział 1 — Wprowadzenie do usługi Azure RTOS NetX Duo FTP

Protokół protokół transferu plików (FTP) to protokół przeznaczony do transferów plików. Protokół FTP korzysta z Transmission Control Protocol (TCP) do wykonywania funkcji transferu plików. W związku z tym FTP to wysoce niezawodny protokół transferu plików. Ftp jest również o wysokiej wydajności. Rzeczywisty transfer plików FTP jest wykonywany na dedykowanym połączeniu FTP. Protokół FTP NetX Duo jest przeznaczony zarówno dla sieci IPv4, jak i IPv6. Protokół IPv6 nie zmienia bezpośrednio protokołu FTP, chociaż niektóre zmiany w oryginalnym interfejsie API FTP NetX są niezbędne do dostosowania protokołu IPv6 i zostaną opisane w tym dokumencie.

## <a name="ftp-requirements"></a>Wymagania dotyczące protokołu FTP

Aby pakiet FTP NetX działał prawidłowo, wymagany jest program NetX Duo. Aplikacja hosta musi utworzyć wystąpienie adresu IP do uruchamiania usług NetX i okresowych zadań. W przypadku uruchamiania aplikacji hosta FTP za pośrednictwem sieci IPv6 należy włączyć protokoły IPv6 i ICMPv6 w zadaniu adresu IP. Protokół TCP musi być również włączony dla sieci IPv6 lub IPv4. Aplikacja hosta IPv6 musi ustawić swój linklokalny i globalny adres IPv6 przy użyciu interfejsu API IPv6 i/lub protokołu DHCPv6. Pokazowy program w sekcji "Mały przykładowy system" w **rozdziale 2** pokazuje, jak to zrobić.

Serwer FTP i klient są również zaprojektowane do pracy z osadzonym systemem plików FileX. Jeśli plik FileX jest niedostępny, deweloper hosta może zaimplementować lub zastąpić własny system plików zgodnie z wytycznymi sugerowanymi w pliku filex_stub.h przez zdefiniowanie każdej z usług wymienionych w tym pliku. Omówiono to w kolejnych sekcjach tego przewodnika.

Część klienta FTP pakietu FTP NetX nie ma dodatkowych wymagań.

Część FTP Server pakietu FTP NetX ma kilka dodatkowych wymagań. Po pierwsze, wymaga pełnego dostępu do dobrze znanego portu *21* protokołu TCP do obsługi wszystkich żądań poleceń ftp klienta i dobrze znanego portu *20* do obsługi wszystkich transferów danych KLIENTA FTP.

## <a name="ftp-constraints"></a>Ograniczenia FTP

Standard FTP ma wiele opcji dotyczących reprezentacji danych plików. NetX FTP nie implementuje opcji przełącznika, np. ls –al. Serwer FTP NetX oczekuje odbierania żądań i ich argumentów w jednym pakiecie, a nie kolejnych pakietach.

Podobnie jak system UNIX implementacji, protokół NETX FTP zakłada następujące ograniczenia formatu pliku:

- Typ pliku: **Binarny**
- Format pliku: **tylko bez odcisku palca**
- Struktura pliku: **Tylko struktura pliku**

## <a name="ftp-file-names"></a>Nazwy plików FTP

Nazwy plików FTP powinny być w formacie docelowego systemu plików (zazwyczaj FileX). Powinny to być ciągi ASCII zakończone wartością NULL z pełnymi informacjami o ścieżce, jeśli jest to konieczne. Nie ma określonego limitu rozmiaru nazw plików FTP w implementacji protokołu FTP NetX. Jednak rozmiar ładunku puli pakietów powinien być w stanie obsłużyć maksymalną ścieżkę i/lub nazwę pliku.

## <a name="ftp-client-commands"></a>Polecenia klienta FTP

Protokół FTP ma prosty mechanizm otwierania połączeń i wykonywania operacji na plikach i katalogach. Zasadniczo istnieje zestaw standardowych poleceń FTP, które są wydawane przez klienta po pomyślnym nawiązaniu połączenia na dobrze znanym porcie TCP *21.* Poniżej przedstawiono niektóre z podstawowych poleceń FTP. Należy pamiętać, że jedyną różnicą w przypadku, gdy protokół FTP działa za pośrednictwem protokołu IPv6, jest to, że polecenie PORT jest zastępowane poleceniem EPRT:

- Zmiana katalogu *roboczego* ścieżki CWD
- Nazwa pliku DELE *Usuń określoną nazwę pliku*
- EpRT ip_address, port *Podaj adres IPv6 i port danych klienta*
- Tryb pasywnego transferu żądania EPSV *dla protokołu IPv6*
- KATALOG LIST *Pobierz listę katalogów*
- Katalog MKD *Make new directory (Katalog MKD: make new directory)*
- Katalog NLST *Pobierz listę katalogów*
- NOOP *No operation, returns success (Brak operacji noop, zwraca powodzenie)*
- PASS password *(PRZEKAŻ hasło) Podaj hasło do logowania*
- Tryb pasywnego transferu żądania PASV *dla protokołu IPv4*
- PORT ip_address,port *Podaj adres IP i Port danych klienta*
- Ścieżka PWD *Odbiór bieżącej ścieżki katalogu*
- ZAKOŃCZ *przerywanie połączenia klienta*
- Nazwa pliku RETR *Odczytaj określony plik*
- Katalog RMD *Usuń określony katalog*
- RNFR oldfilename *Określ plik do zmiany nazwy*
- RNTO newfilename *Zmień nazwę pliku na podaną nazwę pliku*
- Nazwa pliku STOR *Zapisuj określony plik*
- TYP I *Wybieranie obrazu pliku binarnego*
- Nazwa użytkownika *Podaj nazwę użytkownika do logowania*

Te polecenia ASCII są używane wewnętrznie przez oprogramowanie klienckie NetX FTP do wykonywania operacji FTP na serwerze FTP.

## <a name="ftp-server-responses"></a>Odpowiedzi serwera FTP

Gdy serwer FTP przetwarza żądanie klienta, zwraca 3-cyfrową zakodowaną odpowiedź w ascii, po której następuje opcjonalny tekst ASCII. Odpowiedź liczbowa jest używana przez oprogramowanie klienckie FTP do określenia, czy operacja zakończyła się powodzeniem, czy niepowodzeniem. Na poniższej liście przedstawiono różne odpowiedzi serwera FTP na żądania klientów:

**Znaczenie pierwszego pola liczbowego**

- 1xx *Dodatni stan wstępny — nadchodzą kolejne odpowiedzi*.
- Stan ukończenia *dodatniego* 2xx .
- 3xx *Dodatni stan wstępny — należy wysłać inne polecenie*.
- 4xx *Warunek błędu tymczasowego*.
- 5xx *Warunek błędu.*

**Znaczenie drugiego pola liczbowego**

- Błąd składni x0x *w poleceniu*.
- X1x *Komunikat informacyjny*.
- x2x *Connection related*.
- Związane z *uwierzytelnianiem* x3x .
- x4x *Nieokreślony*.
- Związane z *systemem* plików x5x .

Na przykład żądanie klienta dotyczące odłączenia połączenia FTP za pomocą polecenia QUIT zwykle będzie odpowiadać kodem "221" z serwera — jeśli rozłączenie zakończy się pomyślnie.

## <a name="ftp-passive-transfer-mode"></a>Tryb pasywnego transferu FTP

Domyślnie klient FTP NetX Duo używa trybu aktywnego transportu do wymiany danych za pośrednictwem gniazda danych z serwerem FTP. Problem z tym rozmieszczeniem polega na tym, że klient FTP musi otworzyć gniazdo serwera TCP, z którym serwer FTP ma nawiązać połączenie. Reprezentuje to możliwe zagrożenie bezpieczeństwa i może zostać zablokowane przez zaporę klienta. Tryb transferu pasywnego różni się od trybu transportu aktywnego przez utworzenie przez serwer FTP gniazda serwera TCP na połączeniu danych. Eliminuje to zagrożenie bezpieczeństwa (w przypadku klienta FTP).

Aby włączyć pasywny transfer danych, aplikacja wywołuje nx_ftp_client_passive_mode_set *wcześniej* utworzonego klienta FTP z drugim argumentem ustawionym na NX_TRUE. Następnie wszystkie kolejne usługi klienta FTP NetX Duo w celu przesyłania danych (NLST, RETR, STOR) będą podejmować próby w trybie pasywnego transportu.

Klient FTP najpierw wysyła pasywne polecenie (bez argumentów), polecenie PASV dla polecenia IPv4 lub EPSV dla protokołu IPv6. Jeśli serwer FTP obsługuje to żądanie, zwróci odpowiedź 227 "OK" dla aplikacji PASV i odpowiedź 229 "OK" dla programu EPSV. Następnie klient wysyła żądanie, np. RETR. Jeśli serwer odmówi pasywnego trybu transferu, usługa klienta FTP NetX Duo zwraca stan błędu.

Aby wyłączyć pasywny tryb transportu i powrócić do trybu aktywnego transportu, aplikacja *wywołuje* nx_ftp_client_passive_mode_set z drugim argumentem ustawionym na NX_FALSE.

## <a name="ftp-communication"></a>Komunikacja FTP

Serwer FTP używa dobrze znanego portu *TCP 21* do pola Żądania klienta. Klienci FTP mogą używać dowolnego dostępnego portu TCP. Ogólna sekwencja zdarzeń FTP jest następująca:

**Żądania odczytu pliku FTP:**

1. Problemy z łącznością TCP klienta z portem 21 serwera.
1. Serwer wysyła odpowiedź "220", aby zasygnalizować powodzenie.
1. Klient wysyła komunikat "USER" z "username".
1. Serwer wysyła odpowiedź "331", aby zasygnalizować powodzenie.
1. Klient wysyła komunikat "PASS" z hasłem.
1. Serwer wysyła odpowiedź "230" w celu sygnalizowania powodzenia.
1. Klient wysyła komunikat "TYP I" dla transferu binarnego.
1. Serwer wysyła odpowiedź "200" w celu sygnalizowania powodzenia.
1. *Aplikacje IPv4:* klient wysyła komunikat "PORT" z adresem IP i portem.<br />*Aplikacje protokołu IPv6:* klient wysyła komunikat "EPRT" z adresem IP i portem.
1. Serwer wysyła odpowiedź "200" w celu sygnalizowania powodzenia.
1. Klient wysyła komunikat "RETR" z nazwą pliku do odczytu.
1. Serwer tworzy gniazdo danych i nawiązuje połączenie z portem danych klienta określonym w poleceniu "PORT".
1. Serwer wysyła odpowiedź "125" na sygnał odczytany plik został uruchomiony.
1. Serwer wysyła zawartość pliku za pośrednictwem połączenia danych. Ten proces jest kontynuowany do momentu całkowitego transferu pliku.
1. Po zakończeniu serwer rozłącza połączenie danych.
1. Serwer wysyła odpowiedź "250" na komunikat o pomyślnym odczycie pliku.
1. Klient wysyła komunikat "QUIT" w celu zakończenia połączenia FTP.
1. Serwer wysyła odpowiedź "221", aby sygnał rozłączenia został pomyślnie rozłączny.
1. Serwer rozłącza połączenie FTP.

Jak wspomniano wcześniej, jedyna różnica między protokołem FTP uruchomionym za pośrednictwem protokołu IPv4 i

Protokół IPv6 to polecenie PORT jest zastępowane poleceniem EPRT dla protokołu IPv6

Jeśli klient FTP wysyła żądanie odczytu w trybie pasywnego transferu, sekwencja poleceń jest następująca (pogrubione wiersze wskazują inny krok niż aktywny tryb transferu):

1. Problemy z klientem: połączenie TCP z portem 21 serwera.
1. Serwer wysyła odpowiedź "220" w celu sygnalizowania powodzenia.
1. Klient wysyła komunikat "USER" z "username".
1. Serwer wysyła odpowiedź "331", aby zasygnalizować powodzenie.
1. Klient wysyła komunikat "PASS" z hasłem.
1. Serwer wysyła odpowiedź "230" w celu sygnalizowania powodzenia.
1. Klient wysyła komunikat "TYP I" dla transferu binarnego.
1. Serwer wysyła odpowiedź "200" w celu sygnalizowania powodzenia.
1. ***Aplikacje IPv4:* Klient wysyła komunikat "PASV".**<br />**_Aplikacje protokołu IPv6:_ Klient wysyła komunikat "EPSV".**
1. ***Aplikacje IPv4:* Serwer wysyła odpowiedź "227" oraz adres IP i port, z którym klient może się połączyć, aby zasygnalizować powodzenie.**<br />**_Aplikacje protokołu IPv6:_ Serwer wysyła odpowiedź "229" oraz adres IP i port, z którym klient może się połączyć, aby zasygnalizować powodzenie.**
1. Klient wysyła komunikat "RETR" z nazwą pliku do odczytu.
1. **Serwer tworzy gniazdo serwera danych i nasłuchuje żądania Połączenia klienta na tym gnieździe przy użyciu portu określonego w odpowiedzi w kroku 10.**
1. **Serwer wysyła odpowiedź "150" na gniazdo sterowania, aby zasygnalizować, że rozpoczęto odczytywanie pliku.**
1. Serwer wysyła zawartość pliku za pośrednictwem połączenia danych. Ten proces jest kontynuowany do momentu całkowitego transferu pliku.
1. Po zakończeniu serwer rozłącza połączenie danych.
1. **Serwer wysyła odpowiedź "226" na gnieździe sterującym, aby sygnał odczytu pliku został pomyślnie odczytany.**
1. Klient wysyła komunikat "QUIT" w celu zakończenia połączenia FTP.
1. Serwer wysyła odpowiedź "221", aby sygnał rozłączenia został pomyślnie rozłączny.
1. Serwer rozłącza połączenie FTP.

**Żądania zapisu FTP:**

1. Problemy z klientem: połączenie TCP z portem 21 serwera.
1. Serwer wysyła odpowiedź "220" w celu sygnalizowania powodzenia.
1. Klient wysyła komunikat "USER" z "username".
1. Serwer wysyła odpowiedź "331", aby zasygnalizować powodzenie.
1. Klient wysyła komunikat "PASS" z hasłem.
1. Serwer wysyła odpowiedź "230" w celu sygnalizowania powodzenia.
1. Klient wysyła komunikat "TYP I" dla transferu binarnego.
1. Serwer wysyła odpowiedź "200" w celu sygnalizowania powodzenia.
1. *Aplikacje IPv4:* klient wysyła komunikat "PORT" z adresem IP i portem.<br />*Aplikacje protokołu IPv6:* klient wysyła komunikat "EPRT" z adresem IP i portem.
1. Serwer wysyła odpowiedź "200" w celu sygnalizowania powodzenia.
1. Klient wysyła komunikat "STOR" z nazwą pliku do zapisu.
1. Serwer tworzy gniazdo danych i nawiązuje połączenie przy użyciu portu danych klienta określonego w poprzednim poleceniu "EPRT" lub "PORT".
1. Serwer wysyła odpowiedź "125" na sygnał zapisu pliku została uruchomiona.
1. Klient wysyła zawartość pliku za pośrednictwem połączenia danych. Ten proces jest kontynuowany do momentu całkowitego transferu pliku.
1. Po zakończeniu klient rozłącza połączenie danych.
1. Serwer wysyła odpowiedź "250" na komunikat o pomyślnym zapisie pliku.
1. Klient wysyła komunikat "QUIT" w celu zakończenia połączenia FTP.
1. Serwer wysyła odpowiedź "221", aby sygnał rozłączenia został pomyślnie rozłączny.
1. Serwer rozłącza połączenie FTP.

Jeśli klient FTP wysyła żądanie zapisu w trybie pasywnego transferu, sekwencja poleceń jest następująca (pogrubione wiersze wskazują inny krok niż aktywny tryb transferu):

1. Problemy z klientem: połączenie TCP z portem 21 serwera.
1. Serwer wysyła odpowiedź "220" w celu sygnalizowania powodzenia.
1. Klient wysyła komunikat "USER" z "username".
1. Serwer wysyła odpowiedź "331", aby zasygnalizować powodzenie.
1. Klient wysyła komunikat "PASS" z hasłem.
1. Serwer wysyła odpowiedź "230" w celu sygnalizowania powodzenia.
1. Klient wysyła komunikat "TYP I" dla transferu binarnego.
1. Serwer wysyła odpowiedź "200" w celu sygnalizowania powodzenia.
1. ***Aplikacje IPv4:* Klient wysyła komunikat "PASV".**<br />**_Aplikacje protokołu IPv6:_ Klient wysyła komunikat "EPSV".**
1. ***Aplikacje IPv4:* Serwer wysyła odpowiedź "227" oraz adres IP i port, z którym klient może się połączyć, aby zasygnalizować powodzenie.**<br />**_Aplikacje protokołu IPv6:_ Serwer wysyła odpowiedź "229" oraz adres IP i port, z którym klient może się połączyć, aby zasygnalizować powodzenie.**
1. Klient wysyła komunikat "STOR" z nazwą pliku do zapisu.
1. **Serwer tworzy gniazdo serwera danych i nasłuchuje żądania Połączenia klienta na tym gnieździe przy użyciu portu określonego w odpowiedzi w kroku 10.**
1. **Serwer wysyła odpowiedź "150" na gniazdo sterowania, aby zasygnalizować, że rozpoczęto zapis pliku.**
1. Klient wysyła zawartość pliku za pośrednictwem połączenia danych. Ten proces jest kontynuowany do momentu całkowitego transferu pliku.
1. Po zakończeniu klient rozłącza połączenie danych.
1. **Serwer wysyła odpowiedź "226" na gnieździe sterującym, aby zasygnalizować powodzenie zapisu pliku.**
1. Klient wysyła komunikat "QUIT" w celu zakończenia połączenia FTP.
1. Serwer wysyła odpowiedź "221", aby sygnał rozłączenia został pomyślnie rozłączny.
1. Serwer rozłącza połączenie FTP.

## <a name="ftp-authentication"></a>Uwierzytelnianie FTP

Przy każdym nawiązaniu połączenia FTP klient musi podać serwerowi nazwę *użytkownika i* *hasło*. Niektóre witryny FTP zezwalają na dostęp do protokołu *FTP* anonimowego bez określonej nazwy użytkownika i hasła. W przypadku tego typu połączenia jako nazwę użytkownika należy podać "anonimowe", a hasło powinno być kompletnym adresem e-mail.

Użytkownik jest odpowiedzialny za dostarczenie protokołu FTP NetX z procedurami uwierzytelniania logowania i wylogowania. Są one dostarczane podczas ***nxd_ftp_server_create** _ i _*_nx_ftp_server_create_*_ usług i wywoływane z przetwarzania haseł. Różnica między nimi polega na tym, _*_że wskaźniki nxd_ftp_server_create_*_ do logowania i uwierzytelniania logout oczekują, że typ adresu NetX Duo będzie _*_NXD_ADDRESS_*_. Ten typ danych przechowuje formaty adresów IPv4 i IPv6, dzięki czemu ta funkcja jest usługą "duet" obsługą sieci IPv4 i IPv6. Funkcja _ *_nx_ftp_server_create_** wejściowych wskaźników do funkcji uwierzytelniania logowania i wylogowywu oczekuje typu adresu IP ULONG. Ta funkcja jest ograniczona do sieci IPv4. Zachęcamy deweloperów do korzystania z usługi "duo" zawsze, gdy jest to możliwe.

Jeśli funkcja *logowania* zwróci NX_SUCCESS, połączenie zostanie uwierzytelnione i operacje FTP będą dozwolone. W przeciwnym razie, *jeśli funkcja logowania* zwróci wartość inną NX_SUCCESS, próba połączenia zostanie odrzucona.

## <a name="ftp-multi-thread-support"></a>Obsługa wielu wątków FTP

Usługi klienta FTP NetX mogą być wywoływane z wielu wątków jednocześnie. Jednak żądania odczytu lub zapisu dla określonego wystąpienia klienta FTP powinny być wykonywane kolejno z tego samego wątku.

## <a name="ftp-rfcs"></a>RFC FTP

Protokół FTP NetX Duo jest zgodny ze specyfikacjami RFC 959, RFC 2428 i powiązanymi RFC.
