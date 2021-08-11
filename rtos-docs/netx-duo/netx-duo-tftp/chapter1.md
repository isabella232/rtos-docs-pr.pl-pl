---
title: Rozdział 1 — Wprowadzenie do Azure RTOS NetX Duo TFTP
description: Protokół Trivial File Transfer Protocol (TFTP) to lekki protokół przeznaczony do transferów plików.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4854f96d8f230d7c1f21700ac731d6430854a950009d3ed51fbf90d37885f255
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791979"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-tftp"></a>Rozdział 1 — Wprowadzenie do Azure RTOS NetX Duo TFTP 

Protokół Trivial File Transfer Protocol (TFTP) to lekki protokół przeznaczony do transferów plików. W przeciwieństwie do bardziej niezawodnych protokołów TFTP nie wykonuje rozbudowanych testów błędów i może również mieć ograniczoną wydajność, ponieważ jest to protokół typu stop-and-wait. Po wysłaniu pakietu danych TFTP nadawca czeka na zwrócenie przez odbiorcę ACK. Chociaż jest to proste, ogranicza ogólną przepływność TFTP. Pakiet TFTP umożliwia hostom korzystanie z protokołu TFTP za pośrednictwem sieci IP.

## <a name="tftp-requirements"></a>Wymagania TFTP

Aby zapewnić prawidłowe działanie, część klientów TFTP pakietu NetX Duo TFTP wymaga, aby wystąpienie adresu IP zostało już utworzone. Ponadto protokół UDP musi być włączony w tym samym wystąpieniu adresu IP. Część client pakietu NetX Duo TFTP nie ma dodatkowych wymagań.

Część serwera TFTP pakietu NetX Duo TFTP ma kilka dodatkowych wymagań. Po pierwsze wymaga pełnego dostępu do dobrze znanego portu *UDP 69* do obsługi wszystkich żądań TFTP klienta. Serwer TFTP jest również przeznaczony do użytku z osadzonym systemem plików FileX. Jeśli plik FileX nie jest dostępny, użytkownik może portować części pliku FileX używane do własnego środowiska. Omówiono to w kolejnych sekcjach tego przewodnika.

## <a name="tftp-file-names"></a>Nazwy plików TFTP 

Nazwy plików TFTP powinny być w formacie docelowego systemu plików. Powinny to być ciągi ASCII zakończone wartością NULL z pełnymi informacjami o ścieżce, jeśli jest to konieczne. Nie ma określonego limitu rozmiaru nazw plików TFTP w implementacji NetX Duo TFTP.

## <a name="tftp-messages"></a>Komunikaty TFTP

TfTP ma bardzo prosty mechanizm otwierania, odczytywania, zapisywania i zamykania plików. Poniżej nagłówka UDP znajduje się od 2 do 4 bajtów nagłówka TFTP. Definicja otwartych komunikatów TFTP ma następujący format:

**oooof... f0OCTET0**

Gdzie:

- **oooo,** 2-bajtowe pole opcode  
0x0001 -> Otwórz do odczytu  
0x0002 -> Otwórz do zapisu

- **f... f** n-bajtowe pole Nazwa pliku

- 0 1-bajtowy znak zakończenia o wartości NULL

- **OKTET** ASCII "OCTET", aby określić transfer binarny

- 0 1-bajtowy znak zakończenia o wartości NULL

Definicja komunikatów o błędach, ACK i zapisu TFTP jest nieco inna i jest zdefiniowana w następujący sposób:

**oooobbbbd... D**

Gdzie:

- **oooo,** 2-bajtowe pole opcode  
0x0003 -> Data  
0x0004 -> ACK do ostatniego odczytu  
0x0005 -> błąd  

- **bbbb** 2-bajtowe pole Numer bloku (1-n)

- **d... d** n-bajtowe pole danych


- 0x0001 (odczyt) Nazwa pliku 0 OCTET 0

- 0x0002 (zapis) Nazwa pliku 0 OCTET 0

## <a name="tftp-communication"></a>Komunikacja TFTP

Serwery TFTP wykorzystują dobrze znany port UDP 69 do nasłuchiwać żądań klientów. Gniazda klienta TFTP mogą być wiązane z dowolnym dostępnym portem UDP. Ładunek pakietu danych zawierający plik do przekazania lub pobrania jest wysyłany w 512-bajtowych fragmentach do ostatniego pakietu zawierającego < 512 bajtów. W związku z tym pakiet zawierający mniej niż 512 bajtów sygnalizuje koniec pliku. Ogólna sekwencja zdarzeń jest następująca:

Żądania odczytu pliku TFTP:

1.  Klient wysyła żądanie "Otwórz do odczytu" z nazwą pliku i czeka na odpowiedź z serwera.

2.  Serwer wysyła pierwszych 512 bajtów pliku lub mniej, jeśli rozmiar pliku jest mniejszy niż 512 bajtów.

3.  Klient odbiera dane, wysyła ACK i czeka na następny pakiet z serwera dla plików zawierających więcej niż 512 bajtów.

4.  Sekwencja kończy się, gdy klient odbiera pakiet zawierający mniej niż 512 bajtów.

Żądania zapisu TFTP:

1.  Klient wysyła żądanie "Otwórz do zapisu" z nazwą pliku i czeka na ACK z blokiem o numerze 0 z serwera.

2.  Gdy serwer jest gotowy do zapisu pliku, wysyła ACK z blokiem o numerze zero.

3.  Klient wysyła pierwsze 512 bajtów pliku (lub mniej dla plików mniejszej niż 512 bajtów) do serwera i czeka z powrotem na ACK.

4.  Serwer wysyła ACK po zapisane bajty.

5.  Sekwencja kończy się, gdy klient zakończy pisanie pakietu zawierającego mniej niż 512 bajtów.
 

## <a name="tftp-server-session-timer"></a>Czasomierz sesji serwera TFTP

Serwer TFTP ma ograniczoną liczbę miejsc żądań klienta. Jeśli sesja klienta wydaje się być porzucona, to miejsce nie może być dostępne do ponownego użycia. Jeśli jednak NX_TFTP_SERVER_RETRANSMIT_ENABLE jest włączona, serwer TFTP NetX Duo tworzy czasomierz sesji, który monitoruje limit czasu dla każdej sesji klienta. Po upłynie limit czasu sesji zostaje ona zakończona i wszystkie otwarte pliki są zamykane. W związku z tym "miejsce" staje się dostępne dla innego żądania klienta TFTP.

Aby ustawić limit czasu, dostosuj opcję konfiguracji, NX_TFTP_SERVER_RETRANSMIT_TIMEOUT która domyślnie ma wartość 200 takt czasomierza. Interwał między tym, między którymi są sprawdzane limity czasu sesji, jest ustawiany przez NX_TFTP_SERVER_TIMEOUT_PERIOD, która domyślnie wynosi 20 takt czasomierzy.

Gdy klient TFTP przekazać (zapisane) pliki na nośnik TFTP FileX, nośnik musi zostać opróżniony, aby dane można było zapisywać z dysku RAM serwera TFTP na nośniku podstawowym (pamięć dysku klienta TFTP). Można to zrobić przy użyciu usługi fx_media_flush, jeśli aplikacja nie chce zamknąć serwera TFTP.

Jednak po zamknięciu serwera TFTP aplikacja powinna, jeśli nie ma dalszego wykorzystania nośnika FileX, zamknąć nośnik przy użyciu fx_media_close usługi. Spowoduje to opróżnienie danych pliku z powrotem na dysk klienta TFTP, zamknięcie otwartych plików i zaktualizowanie informacji katalogu na nośniku.

Zademonstruje to sekcja "Mały przykład" w tym rozdziale.

Trzecią opcją aktualizacji nośnika FileX jest skompilowanie biblioteki FileX przy użyciu FX_FAULT_TOLERANT lub opcji FX_FAULT_TOLERANT_DATA zamiast jawnego używania usług FileX. Jeśli jest zdefiniowana, plik FileX automatycznie przekazuje żądania zapisu do sterownika nośnika. Te opcje mogą ograniczać wydajność, ale zapewniają większą ochronę przed utraconą lub utraconą klasterem plików. Aby uzyskać więcej informacji na ten temat i ogólnie o plikach FileX, zobacz Express Logic FileX User Guide (Przewodnik użytkownika aplikacji Express Logic FileX).

## <a name="tftp-multi-thread-support"></a>Obsługa wielu wątków TFTP

Usługi klienta NetX Duo TFTP mogą być wywoływane z wielu wątków jednocześnie. Jednak żądania odczytu lub zapisu dla określonego wystąpienia klienta TFTP powinny być wykonywane kolejno z tego samego wątku.

## <a name="tftp-rfcs"></a>RFC TFTP

NetX Duo TFTP jest zgodny ze specyfikacją RFC1350 i powiązanymi RFC.

