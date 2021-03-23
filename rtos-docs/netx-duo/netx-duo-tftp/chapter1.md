---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo TFTP
description: Trivial File Transfer Protocol (TFTP) jest lekkim protokołem przeznaczonym do transferów plików.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4431b23e143d05214090547e7f179a6f5def8217
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821613"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-tftp"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo TFTP 

Trivial File Transfer Protocol (TFTP) jest lekkim protokołem przeznaczonym do transferów plików. W przeciwieństwie do bardziej niezawodnych protokołów, TFTP nie wykonuje dokładnego sprawdzania błędów i może również mieć ograniczoną wydajność, ponieważ jest to protokół zatrzymania i oczekiwania. Po wysłaniu pakietu danych TFTP nadawca czeka na zwrócenie potwierdzenia przez adresata. Chociaż jest to proste, ograniczenie ogólnej przepływności protokołu TFTP jest ograniczone. Pakiet TFTP umożliwia hostom używanie protokołu TFTP w sieciach IP.

## <a name="tftp-requirements"></a>Wymagania dotyczące protokołu TFTP

Aby zapewnić prawidłowe działanie, część klientów TFTP pakietu TFTP NetX Duo wymaga, aby wystąpienie protokołu IP zostało już utworzone. Ponadto należy włączyć protokół UDP dla tego samego wystąpienia IP. Część kliencka pakietu TFTP NetX Duo nie ma żadnych dalszych wymagań.

Część serwera TFTP pakietu TFTP NetX Duo ma kilka dodatkowych wymagań. Najpierw wymaga pełnego dostępu do *dobrze znanego portu* protokołu UDP 69 do obsługi wszystkich żądań TFTP klienta. Serwer TFTP jest również przeznaczony do użycia z osadzonym systemem plików FileX. Jeśli FileX nie jest dostępna, użytkownik może przenieść fragmenty FileX używane w ich własnym środowisku. Zostało to omówione w kolejnych sekcjach tego przewodnika.

## <a name="tftp-file-names"></a>Nazwy plików TFTP 

Nazwy plików TFTP powinny mieć format docelowego systemu plików. Powinny to być ciągi ASCII zakończonych znakiem NULL, z pełnymi informacjami o ścieżce, jeśli jest to konieczne. Nie ma określonego limitu rozmiaru nazw plików TFTP w implementacji TFTP NetX Duo.

## <a name="tftp-messages"></a>Komunikaty TFTP

Protokół TFTP ma bardzo prosty mechanizm otwierania, odczytywania, zapisywania i zamykania plików. W nagłówku UDP znajduje się zasadniczo 2-4 bajtów nagłówka TFTP. Definicja otwartych komunikatów protokołu TFTP ma następujący format:

**oooof... f0OCTET0**

Gdzie:

- **Oooo** 2-bajtowe pole opcode  
0x0001 > Otwórz do odczytu  
0x0002 > Otwórz do zapisu

- **f... n-** bajtowe pole filename

- 0 1-bajtowy znak zakończenia o wartości NULL

- **Oktet** ASCII "OCTET", aby określić transfer binarny

- 0 1-bajtowy znak zakończenia o wartości NULL

Definicje komunikatów Write, ACK i Error protokołu TFTP są nieco inne i są zdefiniowane w następujący sposób:

**oooobbbbd... Wykres**

Gdzie:

- **Oooo** 2-bajtowe pole opcode  
0x0003 — pakiet danych >  
0x0004-> ACK dla ostatniego odczytu  
0x0005 — warunek błędu >  

- pole **bbbb** 2-bajtowego numeru bloku (1-n)

- **d... d** n-bajtowe pole danych


- 0x0001 (odczyt) nazwa pliku 0, OKTET 0

- 0x0002 (Write) — nazwa pliku 0 OKTET 0

## <a name="tftp-communication"></a>Komunikacja TFTP

Serwery TFTP używają dobrze znanego portu UDP 69 do nasłuchiwania żądań klientów. Gniazda klienta TFTP mogą być powiązane z dowolnym dostępnym portem UDP. Ładunek pakietu danych zawierający plik do przekazania lub pobrania jest wysyłany w 512ych fragmentach bajtów do momentu ostatniego pakietu zawierającego < 512 bajtów. W związku z tym pakiet zawierający mniej niż 512 bajtów sygnalizuje koniec pliku. Ogólna sekwencja zdarzeń jest następująca:

Żądania odczytu pliku TFTP:

1.  Klient wystawia żądanie "Otwórz do odczytu" z nazwą pliku i czeka na odpowiedź z serwera.

2.  Serwer wysyła pierwsze 512 bajtów pliku lub mniej, jeśli rozmiar pliku jest mniejszy niż 512 bajtów.

3.  Klient odbiera dane, wysyła potwierdzenie i czeka na następny pakiet z serwera dla plików zawierających więcej niż 512 bajtów.

4.  Sekwencja zostaje zakończona, gdy klient otrzymuje pakiet zawierający mniej niż 512 bajtów.

Żądania zapisu TFTP:

1.  Klient wystawia żądanie "Otwórz do zapisu" z nazwą pliku i oczekuje na potwierdzenie z numerem bloku 0 z serwera.

2.  Gdy serwer jest gotowy do zapisania pliku, wysyła potwierdzenie z numerem bloku równym zero.

3.  Klient wysyła pierwsze 512 bajtów pliku (lub mniej dla plików mniejszych niż 512 bajtów) do serwera i czeka na potwierdzenie zwrotne.

4.  Serwer wysyła potwierdzenie po zapisaniu bajtów.

5.  Sekwencja kończy się, gdy klient ukończy pisanie pakietu zawierającego mniej niż 512 bajtów.
 

## <a name="tftp-server-session-timer"></a>Czasomierz sesji serwera TFTP

Serwer TFTP ma ograniczoną liczbę miejsc żądania klienta. Jeśli sesja klienta zostanie porzucona, gniazdo nie może być dostępne do ponownego użycia. Jeśli jednak opcja NX_TFTP_SERVER_RETRANSMIT_ENABLE jest włączona, serwer TFTP NetX Duo utworzy czasomierz sesji monitorujący limit czasu dla każdej sesji klienta. Po upływie limitu czasu sesji zostaje zakończony i wszystkie otwarte pliki są zamknięte. W ten sposób "miejsce" staną się dostępne dla innego żądania klienta TFTP.

Aby ustawić limit czasu, Dostosuj opcję konfiguracji NX_TFTP_SERVER_RETRANSMIT_TIMEOUT która domyślnie ma 200 Takty czasomierza. Interwał, między jakim są sprawdzane limity czasu sesji, jest ustawiany przez NX_TFTP_SERVER_TIMEOUT_PERIOD, co domyślnie wynosi 20 taktów czasomierza.

Gdy klient TFTP przekazał (wypisano) pliki na nośniku TFTP FileX, nośnik musi zostać opróżniony, aby dane mogły być zapisywane z dysku RAM serwera TFTP do nośnika bazowego (pamięć dysku klienta TFTP). Można to zrobić za pomocą usługi fx_media_flush, jeśli aplikacja nie chce zamykać serwera TFTP.

Jednak po zamknięciu serwera TFTP aplikacja powinna, jeśli nie będzie więcej korzystać z nośnika FileX, a następnie zamknąć nośnik przy użyciu usługi fx_media_close. Spowoduje to opróżnienie danych pliku z powrotem do dysku klienta TFTP, zamknięcie otwartych plików i zaktualizowanie informacji o katalogu na nośniku.

W sekcji "mały przykład" w tym rozdziale pokazano, jak to zrobić.

Trzecią opcją aktualizacji nośnika FileX jest skompilowanie biblioteki FileX z FX_FAULT_TOLERANT lub opcjami FX_FAULT_TOLERANT_DATA zamiast jawnie korzystać z usług FileX Services. Jeśli jest zdefiniowany, FileX automatycznie przekazuje żądania zapisu do sterownika multimediów. Te opcje mogą ograniczać wydajność, ale zapewniają lepszą ochronę przed utraconymi danymi plików lub utraconymi klastrami. Więcej informacji na ten temat i FileX ogólnie można znaleźć w podręczniku użytkownika Express Logic FileX.

## <a name="tftp-multi-thread-support"></a>Obsługa wielowątkowości TFTP

Usługi klienta TFTP NetX Duo można wywołać z wielu wątków jednocześnie. Jednak żądania odczytu lub zapisu dla określonego wystąpienia klienta TFTP powinny być wykonywane w kolejności z tego samego wątku.

## <a name="tftp-rfcs"></a>Specyfikacje RFC protokołu TFTP

NetX Duo TFTP jest zgodny z RFC1350 i pokrewnymi specyfikacjami RFC.

