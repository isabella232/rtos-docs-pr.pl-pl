---
title: Rozdział 1 — wprowadzenie do Azure RTOS NetX Duo SNTP
description: Protokół AZURE RTOS NetX Simple Network Time Protocol (SNTP) jest protokołem przeznaczonym do synchronizowania zegarów przez Internet.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a284871d8da9b8d6d220e962de5d27483dafab201b68d64d5c794c1edab50153
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798830"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-sntp"></a>Rozdział 1 — wprowadzenie do Azure RTOS NetX Duo SNTP 

Protokół AZURE RTOS NetX Simple Network Time Protocol (SNTP) jest protokołem przeznaczonym do synchronizowania zegarów przez Internet. SNTP w wersji 4 to uproszczony protokół oparty na protokole NTP (Network Time Protocol). Korzysta z usług UDP (User Datagram Protocol) do wykonywania aktualizacji czasu w prostym, bez stanowym protokole. Chociaż nie tak złożone jak NTP, SNTP jest wysoce niezawodne i dokładne. W większości współczesnych miejsc Internetu protokół SNTP zapewnia dokładność od 1 do 50 milisekund, w zależności od charakterystyk źródła synchronizacji i ścieżek sieciowych. Protokół SNTP oferuje wiele opcji, które zapewniają niezawodność odbierania aktualizacji czasu. Możliwość przełączenia się na serwery alternatywne, zastosowanie algorytmów sondowania i automatycznego odnajdywania serwerów czasu to tylko kilka sposobów obsługi zmiennej internetowego środowiska usługi czasowej przez klienta SNTP. To, czego brakuje mu precyzji, to prostota i łatwość implementacji. Protokół SNTP jest przeznaczony głównie do zapewnienia kompleksowych mechanizmów dostępu do usług czasu i częstotliwości (np. serwera NTP).

## <a name="netx-duo-sntp-client-requirements"></a>Wymagania dotyczące klienta NetX Duo SNTP

Klient NetX Duo SNTP wymaga, aby wystąpienie adresu IP zostało już utworzone. Ponadto protokół UDP musi być włączony w tym samym  wystąpieniu adresu IP i powinien mieć dostęp do dobrze znanego portu 123 w celu wysyłania danych czasu do serwera SNTP, chociaż będą również działać alternatywne porty. Klienci emisji powinni powiązać port UDP, na który wysyła serwer emisji, zazwyczaj 123. Aplikacja klienta NetX Duo SNTP musi mieć co najmniej jeden adres IP serwera SNTP.

## <a name="netx-duo-sntp-client-limitations"></a>Ograniczenia klienta NetX Duo SNTP 

Precyzja w reprezentacji czasu lokalnego w aktualizacjach czasu NTP obsługiwanych przez interfejs API klienta SNTP jest ograniczona do rozdzielczości milisekund.

Klient SNTP przechowuje w dowolnym momencie tylko jeden adres serwera SNTP. Jeśli wydaje się, że ten serwer nie jest już prawidłowy, aplikacja musi zatrzymać zadanie klienta SNTP i ponownie zainicjować je przy użyciu innego adresu serwera SNTP przy użyciu komunikacji SNTP emisji lub emisji pojedynczej.

Klient SNTP nie obsługuje multiemisji.

Klient NetX Duo SNTP nie obsługuje mechanizmów uwierzytelniania w celu weryfikowania odebranych danych pakietów.

## <a name="netx-duo-sntp-client-operation"></a>NetX Duo SNTP Client Operation

W dokumencie RFC 4330 zaleca się, aby klienci SNTP działali tylko w najwyższej warstwie sieci lokalnej i najlepiej w konfiguracjach, w których synchronizacja nie jest zależna od klienta NTP ani SNTP. Poziom warstwy odzwierciedla położenie hosta w hierarchii czasu NTP, gdzie warstwy 1 jest najwyższy poziom (serwer czasu głównego) i 15 jest najniższy dozwolony poziom (np. klienta). Domyślna warstwa minimalna klienta SNTP to 2.

Klient NetX Duo SNTP może działać w jednym z dwóch podstawowych trybów, emisji pojedynczej lub emisji, aby uzyskać czas przez Internet. W trybie emisji pojedynczej klient sonduje swój serwer SNTP w regularnych odstępach czasu i czeka na otrzymanie odpowiedzi z tego serwera. Po otrzymaniu klient sprawdza, czy odpowiedź zawiera prawidłową aktualizację czasu, stosując zestaw "testów sanity" zalecanych przez dokument RFC 4330. Klient następnie stosuje różnicę czasu, jeśli jest, z zegara serwera do jego zegara lokalnego. W trybie emisji klient jedynie nasłuchuje emisji aktualizacji czasu i utrzymuje zegar lokalny po zastosowaniu podobnego zestawu kontroli sanity w celu zweryfikowania danych czasu aktualizacji. Kontrole sanity zostały szczegółowo opisane w sekcji **SNTP Sanity Checks** poniżej.

Przed uruchomieniem klienta w obu trybach musi on ustanowić parametry operacyjne. Odbywa się to przez wywołanie nx_sntp_client_initialize_unicast *lub* *nx_sntp_client_initialize_broadcast* odpowiednio dla trybów emisji pojedynczej lub emisji. Służą one do ustawienia limitów czasu dla maksymalnego czasu bez ważnej aktualizacji, limitu kolejnych odebranych nieprawidłowych aktualizacji, interwału sondowania dla trybu emisji pojedynczej, trybu operacji, np. emisji pojedynczej a emisji i serwera SNTP.

W przypadku przekroczenia maksymalnego czasu lub przekroczenia maksymalnej liczby odebranych nieprawidłowych aktualizacji klient SNTP będzie nadal działać, ale ustawia bieżący stan serwera SNTP na nieprawidłowy. Aplikacja może sondować klienta SNTP przy użyciu *usługi nx_sntp_client_receiving_updates,* aby sprawdzić, czy serwer SNTP nadal wysyła prawidłowe aktualizacje. W innym przypadku należy zatrzymać wątek klienta SNTP przy użyciu usługi *nx_sntp_client_stop* i wywołać jedną z dwóch usług, aby ustawić inny adres serwera SNTP. Aby ponownie uruchomić klienta SNTP, aplikacja wywołuje *nx_sntp_client_run_broadcast* lub *nx_sntp_client_run_unicast*. Należy pamiętać, że aplikacja może zmienić tryb operacyjny klienta SNTP w wywołaniu inicjowania, aby w razie potrzeby przełączyć się na emisję pojedynczą lub emisję.

### <a name="local-clock-operation"></a>Operacja zegara lokalnego

Czas SNTP na podstawie liczby sekund na zegar NTP głównego lub liczbę sekund, które upłynęły w pierwszej epoce NTP, np. od 1 stycznia **1900 00:00:00** do **1 stycznia 1999 00:00:00.** Istotność 01-01-1999 miała miejsce, gdy miała miejsce ostatnia sekunda przestępna. Ta wartość jest zdefiniowana w następujący sposób:

\#definiowanie NTP_SECONDS_AT_01011999 0xBA368E80

Przed rozpoczęciem korzystania z klienta SNTP aplikacja może opcjonalnie zainicjować czas lokalny klienta SNTP, który będzie dla klienta używać jako czasu odniesienia. W tym celu musi używać usługi *nx_sntp_client_set_local_time* service. Zajmuje to czas w formacie NTP, sekundy i ułamek, gdzie ułamek jest milisekund w NTP skróconego czasu. W idealnym przypadku aplikacja może uzyskać czas SNTP z niezależnego źródła. W kliencie NetX Duo SNTP nie ma interfejsu API służącego do konwertowania roku, miesiąca, daty i czasu na czas NTP. Opis formatu czasu NTP, zobacz *RFC4330 "Simple Network Time Protocol (SNTP) wersja 4 dla IPv4, IPv6 i OSI".*

Jeśli podstawowy czas lokalny nie zostanie podany podczas uruchamiania klienta SNTP, klient SNTP zaakceptuje aktualizacje SNTP bez porównania z czasem lokalnym przy pierwszej aktualizacji. Następnie zastosuje wartości aktualizacji maksymalnego i minimalnego czasu, aby określić, czy zmodyfikuje czas lokalny.

Aby uzyskać czas lokalny klienta SNTP, aplikacja może użyć *nx_sntp_client_get_local_time_extended* usługi.

### <a name="sntp-sanity-checks"></a>SNTP Sanity Checks 

Klient sprawdza pakiet przychodzący pod następującymi kryteriami:

  - Źródłowy adres IP musi być zgodne z bieżącym adresem IP serwera.

  - Port źródłowy nadawcy musi być zgodne z bieżącym portem źródłowym serwera.

  - Długość pakietu musi być minimalną długością do przechowywania komunikatu czasu SNTP.

Następnie czas wyodrębnienia danych z buforu pakietów, do którego klient stosuje zestaw określonych "testów sanity":

  - Wskaźnik przestępny ustawiony na 3 wskazuje, że serwer nie jest zsynchronizowany. Klient powinien spróbować znaleźć alternatywny serwer.

  - Pole warstwy ustawione na wartość zero jest nazywane pakietem z of Death (KOD). Procedura obsługi kodów KOD klienta SMTP w tej sytuacji to wywołanie zwrotne zdefiniowane przez użytkownika. Mały przykładowy plik demonstracyjny zawiera prostą obsługę kodów KOD w tej sytuacji. Pole Identyfikator odwołania opcjonalnie zawiera kod wskazujący przyczynę odpowiedzi kodów KOD. W dowolnym momencie program obsługi kodów musi wskazać, jak obsługiwać odbieranie zgonów z serwera SNTP. Zazwyczaj konieczne jest ponowne zainicjowanie klienta SNTP z innym serwerem SNTP.

  - Wersja SNTP serwera, warstwa i tryb działania muszą być dopasowane do usługi klienta.

  - Jeśli klient jest skonfigurowany z maksymalnym rozproszeniem zegara serwera, klient sprawdza rozproszenie zegara serwera tylko przy pierwszej otrzymanej aktualizacji, a jeśli przekroczy wartość maksymalną klienta, klient odrzuci serwer.

  - Pola sygnatury czasowej serwera muszą również przejść określone testy. W przypadku serwera emisji pojedynczej wszystkie pola czasu muszą być wypełnione i nie mogą mieć wartości NULL. Sygnatura czasowa pochodzenia musi być równa sygnaturze czasowej przesyłania w żądaniu komunikatu o czasie SNTP klienta. Chroni to klienta przed złośliwymi intruzami i nieautoryzowanym zachowaniem serwera. Serwer emisji musi wypełnić tylko sygnaturę czasową przesyłania. Ponieważ nie otrzymuje on niczego od klienta, nie ma pól Receive ani Origination do wypełnienia.

    Sprawdzanie nieudanej kontroli sanity powoduje aktualizację czasu jako nieprawidłową aktualizację czasu. Usługa sprawdzania sanity klienta SNTP śledzi liczbę kolejnych nieprawidłowych aktualizacji czasu odebranych z tego samego serwera.

Gdy zadanie wątków klienta SNTP sprawdza poprawność pakietu SNTP do zastosowania do lokalnego czasu klienta SNTP, zwiększa liczbę klienta SNTP. Zwraca również stan błędu do wywołującego, ale to wszystko jest przetwarzanie wewnętrzne, więc nie jest natychmiast widoczne dla `nx_sntp_client_invalid_time_updates.` aplikacji. Aby wykryć aktualizacje czasu, które zakończyły się niepowodzeniem, należy odpytować wartość klienta SNTP po `nx_sntp_client_invalid_time_updates` otrzymaniu aktualizacji czasu serwera SNTP.

Jeśli aktualizacja czasu serwera przejdzie testy sanity, klient spróbuje przetworzyć dane czasu do czasu lokalnego. Jeśli klient jest skonfigurowany do obliczania rundy, np. czas od wysłania żądania aktualizacji do czasu, kiedy zostanie odebrany, jest obliczany czas rundy. Ta wartość jest połówkowana, a następnie dodawana do czasu serwera.

Następnie, jeśli jest to pierwsza aktualizacja odebrana z bieżącego serwera SNTP, klient SNTP określa, czy należy zignorować różnicę między czasem lokalnym serwera i klienta. Następnie wszystkie aktualizacje z serwera SNTP są oceniane pod względem różnicy czasu lokalnego klienta.

Różnica między czasem klienta i serwera jest porównywana z `NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT` . Jeśli przekroczy tę wartość, dane są generowane. Jeśli różnica jest mniejsza niż `NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT` różnica, jest uznawana za za małą, aby wymagać korekty.

Przekazanie wszystkich tych testów, aktualizacja czasu jest następnie stosowana do klienta SNTP z pewnymi korektami opóźnień w wewnętrznym przetwarzaniu klienta SNTP.

### <a name="sntp-asynchronous-unicast-requests"></a>Żądania asynchronicznego emisji pojedynczej SNTP 

Klient SNTP umożliwia aplikacji hosta asynchroniczne wysyłanie żądania emisji pojedynczej dla bieżącego czasu z serwera NTP.

```C
UINT _nx_sntp_client_request_unicast_time(
NX_SNTP_CLIENT *client_ptr, 
UINT wait_option)
```

Opcja oczekiwania to czas wygaśnięcia oczekiwania na odpowiedź.

Jeśli serwer NTP odpowiada, pakiet podlega tym samym przetwarzania i kontroli sanity, jak opisano w poprzedniej sekcji przed aktualizacją czasu lokalnego klienta SNTP.

Jeśli wywołanie zwróci pomyślne ukończenie,  aplikacja może wywołać nx_sntp_client_utility_display_date_time lub *nx_sntp_client_get_local_time_extended* dla zaktualizowanego czasu lokalnego.

Te żądania emisji pojedynczej nie zakłócają normalnego harmonogramu klienta SNTP wysyłania następnego żądania emisji pojedynczej lub w trybie emisji, kiedy należy oczekiwać następnej emisji NTP.

### <a name="periodic-local-time-updates"></a>Okresowe aktualizacje czasu lokalnego

Maksymalne dostosowanie czasu lokalnego jest ustawiane w NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT (w milisekundach). Interwał aktualizacji sondowania dla operacji klienta SNTP emisji pojedynczej jest ustawiany w NX_SNTP_CLIENT_UNICAST_POLL_INTERVAL (w sekundach). Jeśli interwał sondowania jest większy niż maksymalna korekta, kolejne aktualizacje serwera po pierwszej aktualizacji serwera zostaną odrzucone. Aby temu zapobiec, klient SNTP będzie okresowo aktualizować czas lokalny zdefiniowany jako NX_SNTP_UPDATE_TIMEOUT_INTERVAL. 

Jeśli istnieje różnica czasu między czasem na pokładzie RTC i czasem serwera (na którym należy ustawić czas lokalny klienta SNTP), należy z synchistrować rtc z czasem klienta SNTP (nie pokazaliśmy tego w tym Podręczniku użytkownika).

Ponieważ aktualizacje serwera SNTP nie powinny występować częściej niż raz na godzinę, sondowania klienta SNTP w celu aktualizacji serwera lub stanu serwera nie jest przydatne. Jednak klient SNTP powinien zaktualizować swój zegar lokalny wystarczająco często, aby nie spadnie więcej niż maksymalny czas parametru NX_SNTP_CLIENT_MAX_TIME_LAPSE.

Alternatywnie maksymalną liczbę NX_SNTP_CLIENT_MAX_TIME_LAPSE można ustawić na wartość większą niż aktualizacja sondowania emisji pojedynczej (lub przewidywane interwały emisji). Ta ostatnia eliminuje potrzebę niezależnego zegara czasu rzeczywistego. Jednak celem protokołu SNTP jest uniknięcie całkowitej zależności od aktualizacji lokalnego czasu RTC lub czasu sieci. Ponadto aktualizacje serwera SNTP mają zapobiegać dryfowi w lokalnym zegarze czasowym.

## <a name="multiple-network-interfaces"></a>Wiele interfejsów sieciowych

Klienta NetX Duo SNTP można skonfigurować do uruchamiania w sieciach pomocniczych, o ile te sieci są zarejestrowane w wystąpieniu adresu IP. Aby uzyskać więcej informacji na temat rejestrowania sieci pomocniczych, zobacz NetX Duo lub NetX User Guide (Podręcznik użytkownika aplikacji NetX Duo lub NetX).

W *wywołaniu nx_sntp_client_create* ustaw trzecie dane wejściowe, iface_index, na indeks sieci, aby klient SNTP odbierał aktualizacje czasu. Interfejs podstawowy jest zawsze w indeksie 0. Klient NetX Duo SNTP nie może obsługiwać aktualizacji czasu jednocześnie na wielu interfejsach sieciowych.

## <a name="sntp-and-ntp-rfcs"></a>RFC SNTP i NTP

Klient NetX Duo SNTP jest zgodny ze standardem RFC4330 "Simple Network Time Protocol (SNTP) w wersji 4 dla protokołów IPv4, IPv6 i OSI" i powiązanymi RFC.