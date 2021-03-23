---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo SNTP
description: Usługa Azure RTO NetX Simple Network Time Protocol (SNTP) to protokół służący do synchronizowania zegarów przez Internet.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b3e1170197c6c4981060459104da80e354fac5db
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821655"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-sntp"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo SNTP 

Usługa Azure RTO NetX Simple Network Time Protocol (SNTP) to protokół służący do synchronizowania zegarów przez Internet. SNTP w wersji 4 to uproszczony protokół oparty na protokole NTP (Network Time Protocol). Korzysta ona z usług UDP (User Datagram Protocol) do wykonywania aktualizacji czasowych w prostym, bezstanowym protokole. Chociaż nie jest to skomplikowane jako NTP, SNTP jest wysoce niezawodny i dokładny. W większości miejsc Internetu dzisiaj protokół SNTP zapewnia dokładności 1-50 milisekund, w zależności od właściwości źródła synchronizacji i ścieżki sieci. Protokół SNTP ma wiele opcji zapewniających niezawodność aktualizacji czasu do odebrania. Możliwość przełączania do alternatywnych serwerów, stosowania algorytmów sondowania i automatycznego odnajdywania serwera, to tylko kilka z metod obsługi przez klienta SNTP zmiennej internetowego środowiska usługi czasowej. To, czego nie ma w tym sensie, stanowi prostotę i łatwość implementacji. Protokół SNTP jest przeznaczony głównie do zapewniania kompleksowych mechanizmów uzyskiwania dostępu do Narodowego czasu i rozpowszechniania (np. serwera NTP) usług.

## <a name="netx-duo-sntp-client-requirements"></a>Wymagania dotyczące klienta SNTP NetX Duo

Klient SNTP NetX Duo wymaga, aby wystąpienie adresu IP zostało już utworzone. Ponadto protokół UDP musi być włączony w tym samym wystąpieniu IP i powinien mieć dostęp do *dobrze znanego* portu 123 na potrzeby wysyłania danych czasu do serwera SNTP, chociaż alternatywne porty również będą działać. Klienci emisji powinni powiązać z portem UDP, na którym jest wysyłany serwer emisji, zwykle 123. Aplikacja kliencka NetX Duo SNTP musi mieć jeden lub więcej adresów IP protokołu SNTP.

## <a name="netx-duo-sntp-client-limitations"></a>Ograniczenia klienta SNTP NetX Duo 

Precyzja w czasie lokalnym reprezentacji w czasie NTP aktualizacje obsługiwane przez interfejs API klienta protokołu SNTP jest ograniczone do liczby milisekund.

Klient SNTP przechowuje tylko jeden adres serwera SNTP w dowolnym momencie. Jeśli ten serwer prawdopodobnie nie jest już prawidłowy, aplikacja musi zatrzymać zadanie klienta SNTP i zainicjować je ponownie z innym adresem serwera SNTP przy użyciu emisji lub protokołu SNTP emisji pojedynczej.

Klient SNTP nie obsługuje manycast.

Klient SNTP NetX Duo nie obsługuje mechanizmów uwierzytelniania na potrzeby weryfikowania odebranych danych pakietu.

## <a name="netx-duo-sntp-client-operation"></a>Operacja klienta SNTP NetX Duo

W dokumencie RFC 4330 zaleca się, aby klienci protokołu SNTP mogli działać tylko w najwyższej warstwie sieci lokalnej i najlepiej w konfiguracjach, w których żaden klient NTP lub SNTP nie jest zależny od nich do synchronizacji. Poziom warstwy odzwierciedla pozycję hosta w hierarchii czasu NTP, w której warstwa 1 to najwyższy poziom (główny serwer czasu), a 15 to najniższy dozwolony poziom (np. Klient). Domyślna minimalna warstwa klienta SNTP to 2.

Klient SNTP NetX Duo może działać w jednym z dwóch podstawowych trybów, emisji pojedynczej lub emisji, aby uzyskać czas za pośrednictwem Internetu. W trybie emisji pojedynczej klient sonduje swój serwer SNTP w regularnych odstępach czasu i czeka na odebranie odpowiedzi z tego serwera. Po odebraniu klient sprawdza, czy odpowiedź zawiera prawidłową aktualizację czasu, stosując zestaw "Sanity checks" zalecanego w dokumencie RFC 4330. Następnie klient stosuje różnicę czasu, jeśli istnieje, z zegarem serwera do zegara lokalnego. W trybie emisji klient tylko nasłuchuje emisji aktualizacji czasu i utrzymuje zegar lokalny po zastosowaniu podobnego zestawu Sanity checks w celu zweryfikowania danych dotyczących czasu aktualizacji. Sanity checks są szczegółowo opisane w poniższej sekcji **checks w usłudze SNTP Sanity** .

Przed uruchomieniem klienta w obu trybach należy określić jego parametry operacyjne. Jest to realizowane przez wywołanie odpowiednio *nx_sntp_client_initialize_unicast* lub *nx_sntp_client_initialize_broadcast* dla trybów emisji pojedynczej lub emisji. Służą one do ustawiania przedziałów czasowych dla maksymalnego czasu, który upłynął, bez prawidłowej aktualizacji, odebrano limit kolejnych nieprawidłowych aktualizacji, interwału sondowania trybu emisji pojedynczej, trybu operacji, np. emisji pojedynczej i emisji oraz serwera SNTP.

W przypadku przekroczenia maksymalnego czasu wygaśnięcia lub maksymalnej liczby odebranych nieprawidłowych aktualizacji klient SNTP będzie kontynuował pracę, ale ustawia bieżący stan serwera SNTP na nieprawidłowy. Aplikacja może sondować klienta SNTP przy użyciu usługi *nx_sntp_client_receiving_updates* , aby sprawdzić, czy serwer SNTP nadal wysyła prawidłowe aktualizacje. W przeciwnym razie należy zatrzymać wątek klienta SNTP przy użyciu usługi *nx_sntp_client_stop* i wywołać jedną z dwóch inicjowanych usług, aby ustawić inny adres serwera SNTP. Aby ponownie uruchomić klienta SNTP, aplikacja wywołuje *nx_sntp_client_run_broadcast* lub *nx_sntp_client_run_unicast*. Należy pamiętać, że aplikacja może zmienić tryb operacyjny klienta SNTP w wywołaniu inicjowania, aby przełączyć się na emisję pojedynczą lub emisję zgodnie z potrzebami.

### <a name="local-clock-operation"></a>Operacja zegara lokalnego

Czas SNTP na podstawie liczby sekund w ciągu głównego zegara NTP lub liczby sekund, które upłynęły od pierwszej epoki NTP, np. od 1 stycznia **1900 00:00:00 do** 1 stycznia **1999 00:00:00**. Istotność 01-01-1999 była ostatnią przestępnością sekundy. Ta wartość jest definiowana w następujący sposób:

\#Zdefiniuj NTP_SECONDS_AT_01011999 0xBA368E80

Przed uruchomieniem klienta SNTP aplikacja może opcjonalnie zainicjować czas lokalny klienta SNTP, który będzie używany przez klienta jako czas podstawowy. W tym celu należy użyć usługi *nx_sntp_client_set_local_time* . Trwa to czas w formacie NTP, sekundy i ułamek, gdzie ułamek jest milisekundą w czasie trwania NTP. Najlepiej, aby aplikacja mogła uzyskać czas SNTP z niezależnego źródła. Nie istnieje interfejs API służący do konwertowania roku, miesiąca, daty i czasu na czas NTP w kliencie NetX Duo SNTP. Opis formatu czasu NTP można znaleźć w *RFC4330 "Simple Network Time Protocol (SNTP) w wersji 4 dla protokołów IPv4, IPv6 i osi".*

Jeśli podczas uruchamiania klienta SNTP nie podano podstawowego czasu lokalnego, klient SNTP zaakceptuje aktualizacje SNTP bez porównywania ich z lokalnym czasem przy pierwszej aktualizacji. Następnie użyje wartości maksymalnego i minimalnego czasu aktualizacji, aby określić, czy będzie on modyfikowany jako czas lokalny.

Aby uzyskać czas lokalny klienta SNTP, aplikacja może używać usługi *nx_sntp_client_get_local_time_extended* .

### <a name="sntp-sanity-checks"></a>Kontrole Sanity SNTP 

Klient analizuje pakiet przychodzący dla następujących kryteriów:

  - Źródłowy adres IP musi być zgodny z bieżącym adresem IP serwera.

  - Port źródłowy nadawcy musi być zgodny z bieżącym portem źródłowym serwera.

  - Długość pakietu musi być minimalna długość, aby można było przechowywać komunikat czasu SNTP.

Następnie dane czasu są wyodrębniane z bufora pakietów, do którego Klient zastosuje zestaw konkretnych Sanity checks:

  - Wskaźnik przestępny ustawiony na 3 wskazuje, że serwer nie jest zsynchronizowany. Klient powinien próbować znaleźć alternatywny serwer.

  - Pole warstwy o wartości zero jest znane jako odnosi pakiet zgonu (KOD). Program obsługi kodu klienta SMTP w tej sytuacji jest wywołaniem zwrotnym zdefiniowanym przez użytkownika. Mały przykładowy plik demonstracyjny zawiera prostą procedurę obsługi kodu dla tej sytuacji. Pole Identyfikator odwołania opcjonalnie zawiera kod wskazujący powód odpowiedzi na KOD. W dowolnym tempie procedura obsługi kodu musi wskazywać, jak obsługiwać odbiór śmierci z serwera SNTP. Zazwyczaj należy ponownie zainicjować klienta SNTP przy użyciu innego serwera SNTP.

  - Wersja, warstwa i tryb operacji SNTP serwera muszą być dopasowane do usługi klienta.

  - Jeśli klient został skonfigurowany z maksymalną ilością rozproszenia zegara serwera, klient sprawdza rozproszenie zegara serwera przy pierwszej aktualizacji, która została odebrana, a jeśli przekroczy maksimum klienta, klient odrzuca serwer.

  - Pola sygnatury czasowej serwera muszą również przekazywać określone sprawdzenia. W przypadku serwera emisji pojedynczej wszystkie pola czasu muszą być wypełnione i nie mogą mieć wartości NULL. Sygnatura czasowa punktu początkowego musi być równa sygnatury czasowej transmisji w żądaniu komunikatu czasu SNTP klienta. Zapewnia to ochronę klienta przed złośliwymi intruzami i zachowaniem nieautoryzowanego serwera. Serwer emisji musi wypełniać tylko sygnaturę czasową transmisji. Ponieważ nie odbiera niczego od klienta, nie ma pól odbioru lub pochodzenia do wypełnienia.

    Niepowodzenie Sanity Check a Time Update jako nieprawidłową aktualizację czasu. Usługa sprawdzania Sanity klienta SNTP śledzi liczbę kolejnych nieprawidłowych aktualizacji czasu odebranych z tego samego serwera.

Gdy zadanie wątku klienta SNTP sprawdza poprawność pakietu SNTP do zastosowania do lokalnego czasu klienta SNTP, zwiększa liczbę klientów SNTP, która `nx_sntp_client_invalid_time_updates.` zwraca również stan błędu do obiektu wywołującego, ale jest to wszystkie wewnętrzne przetwarzanie, dlatego nie jest natychmiast widoczne dla aplikacji. Sposób wykrywania aktualizacji czasu niepowodzenia polega na wysłaniu zapytania o wartość klienta SNTP `nx_sntp_client_invalid_time_updates` po odebraniu aktualizacji czasu serwera SNTP.

Jeśli aktualizacja czasu serwera przeszedł testy Sanity, klient próbuje przetworzyć dane czasu do czasu lokalnego. Jeśli klient jest skonfigurowany do obliczeń rundy, np. czas wysłania żądania aktualizacji do momentu odebrania, zostanie obliczony czas błądzenia. Ta wartość jest mniejsza, a następnie dodawana do czasu serwera.

Następnie, jeśli jest to pierwsza aktualizacja odebrana od bieżącego serwera SNTP, klient SNTP określa, czy powinien on ignorować różnicę między serwerem a lokalnym czasem klienta. Następnie wszystkie aktualizacje z serwera SNTP są oceniane pod kątem różnic przy użyciu czasu lokalnego klienta.

Różnica między czasem klienta i serwera jest porównywana z `NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT` . W przypadku przekroczenia tej wartości dane są generowane. Różnica jest mniejsza niż `NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT` mała, aby wymagać korekty.

Przekazując wszystkie te sprawdzenia, aktualizacja czasu jest następnie stosowana do klienta SNTP z pewnymi poprawkami dla opóźnień w wewnętrznym przetwarzaniu klienta SNTP.

### <a name="sntp-asynchronous-unicast-requests"></a>Asynchroniczne żądania emisji pojedynczej SNTP 

Klient SNTP umożliwia aplikacji hosta asynchroniczne wysyłanie żądania emisji pojedynczej do bieżącego czasu z serwera NTP.

```C
UINT _nx_sntp_client_request_unicast_time(
NX_SNTP_CLIENT *client_ptr, 
UINT wait_option)
```

Opcja oczekiwania jest wygaśnięciem oczekiwania na odpowiedź.

Jeśli serwer NTP reaguje, pakiet podlega tym samym przetwarzaniem i Sanity sprawdzenia zgodnie z opisem w poprzedniej sekcji przed aktualizacją czasu lokalnego klienta SNTP.

Jeśli wywołanie zwróci pomyślne zakończenie, aplikacja może wywołać *nx_sntp_client_utility_display_date_time* lub *nx_sntp_client_get_local_time_extended* dla zaktualizowanego czasu lokalnego.

Te żądania emisji pojedynczej nie zakłócają normalnego harmonogramu klienta protokołu SNTP do wysyłania kolejnego żądania emisji pojedynczej lub w trybie emisji, kiedy oczekiwać następnej emisji NTP.

### <a name="periodic-local-time-updates"></a>Okresowe aktualizacje czasu lokalnego

Maksymalna korekta czasu lokalnego jest ustawiana w opcji NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT (w milisekundach). Interwał aktualizacji sondowania dla operacji klienta SNTP emisji pojedynczej jest ustawiany w opcji NX_SNTP_CLIENT_UNICAST_POLL_INTERVAL (w sekundach). Jeśli wartość interwału sondowania jest większa niż wartość ustawienia maksymalnego, kolejne aktualizacje serwera po pierwszej aktualizacji serwera zostaną odrzucone. Aby tego uniknąć, klient SNTP aktualizuje czas lokalny, który jest definiowany jako NX_SNTP_UPDATE_TIMEOUT_INTERVAL. 

W przypadku różnic w czasie między rejestracją RTC a czasem serwera (w którym czas lokalny klienta SNTP powinien być ustawiony na), czas RTC powinien zostać zsynchronizowany z czasem klienta SNTP (nie jest to zademonstrowane w tym przewodniku użytkownika).

Ponieważ aktualizacje serwera SNTP nie powinny występować częściej niż raz na godzinę, nie jest przydatne sondowanie klienta SNTP pod kątem aktualizacji serwera lub stanu serwera częściej niż to możliwe. Jednak klient SNTP powinien zaktualizować swój zegar lokalny wystarczająco często, aby nie był większy niż maksymalny parametr dostosowania czasu NX_SNTP_CLIENT_MAX_TIME_LAPSE.

Alternatywnie można ustawić maksymalny NX_SNTP_CLIENT_MAX_TIME_LAPSE korekty na wartość większą niż aktualizacja sondowania emisji pojedynczej (lub przewidywane interwały emisji). Ten ostatni eliminuje potrzebę niezależnego zegara w czasie rzeczywistym. Jednak zamiarem protokołu SNTP jest uniknięcie całkowitej zależności od lokalnych aktualizacji RTC lub czasu w sieci. Ponadto aktualizacje serwera SNTP są przeznaczone do zapobiegania dryfowi w lokalnym zegarze czasu.

## <a name="multiple-network-interfaces"></a>Wiele interfejsów sieciowych

Klienta SNTP NetX Duo można skonfigurować do uruchamiania w sieciach pomocniczych, o ile te sieci są zarejestrowane w wystąpieniu IP. Więcej informacji na temat rejestrowania sieci dodatkowych można znaleźć w podręczniku użytkownika NetX Duo lub NetX.

W wywołaniu *nx_sntp_client_create* Ustaw trzecią wartość wejściową, iface_index na indeks sieci dla klienta SNTP, na który mają zostać odebrane aktualizacje. Interfejs podstawowy ma zawsze indeks 0. Klient SNTP NetX Duo nie może obsługiwać aktualizacji czasu jednocześnie w wielu interfejsach sieciowych.

## <a name="sntp-and-ntp-rfcs"></a>Specyfikacje RFC protokołu SNTP i NTP

Klient SNTP NetX Duo jest zgodny z RFC4330em "Simple Network Time Protocol (SNTP) w wersji 4 dla protokołów IPv4, IPv6 i OSI" oraz pokrewnych specyfikacji RFC.