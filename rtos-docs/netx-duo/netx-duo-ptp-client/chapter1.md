---
title: Rozdział 1 — Wprowadzenie do Azure RTOS NetX Duo PTP Client
description: Ten rozdział zawiera wprowadzenie do klienta Azure RTOS NetX Duo PTP.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cf7210529121c8e49ff3cabbb7c673288b803f24760096396f32f33d4a9fb7e6
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798048"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-ptp-client"></a>Rozdział 1 — Wprowadzenie do Azure RTOS NetX Duo PTP Client

Zestaw Azure RTOS NetX Duo PTP implementuje część klienta protokołu Precision Time Protocol (PTP) w wersji 2, IEEE 1588-2008. Służy do synchronizowania zegarów między mikro mikroujem w sieci lokalnej, komunikując się ze sobą za pośrednictwem pakietów multiemisji IPv4 lub IPv6.

## <a name="netx-duo-ptp-client-setup"></a>NetX Duo PTP Client Setup

Aby pakiet klienta PTP działał prawidłowo, wymaga, aby wystąpienie adresu IP NetX Duo zostało już utworzone.

Domyślnie klient PTP dołącza do grupy multiemisji IPv4. Aby można było uruchomić klienta PTP w sieci IPv6, należy zdefiniować podczas `NX_ENABLE_IPV6_MULTICAST` tworzenia biblioteki NetX Duo.

Podczas tworzenia klienta PTP aplikacja musi zapewnić funkcję wywołania zwrotnego do obsługi sygnatur czasowych pakietów przychodzących i wychodzących. Aby uzyskać wysoką rozdzielczość, zalecamy aplikacjom generowanie znaczników czasu przy użyciu czasomierza o wysokiej rozdzielczości. Aby uruchomić pakiet PTP w symulatorze, zostanie zapewniona implementacja `nx_ptp_client_soft_clock_callback` programowa.

Klient PTP wymaga puli pakietów do przesyłania komunikatów PTP. Rozmiar ładunku puli pakietów nie może być mniejszy niż , czyli `NX_UDP_PACKET + NX_PTP_CLIENT_PACKET_DATA_SIZE` 108 bajtów dla protokołu IPv4 i 128 bajtów, jeśli protokół IPv6 jest włączony.

Po utworzeniu klienta PTP aplikacja może uruchomić klienta PTP. Synchronizacja jest wykonywana w wątku pomocnika PTP. Można określić funkcję wywołania zwrotnego zdarzenia. Zostanie on wywołany, gdy nastąpi dowolne z następujących zdarzeń.
* Wybrano wzorzec; 
* Czas jest skalibrowany.
* Ujmuje się w to wzorzec.

## <a name="netx-duo-ptp-client-messages"></a>Komunikaty klienta NETX Duo PTP

Klient NetX Duo PTP implementuje tylko mechanizm żądania i odpowiedzi na żądanie opóźnienia. Klient PTP otwiera dwa porty UDP. *319 dla* **komunikatu o zdarzeniu** i *320* dla **komunikatu ogólnego.** Dla tego mechanizmu istnieje pięć typów komunikatów.

* **Ogłaszaj .** Jest to komunikat zdarzenia. Służy do wyboru zegara głównego.
* **Zsynchronizuj**. Jest to komunikat zdarzenia. Służy do wysyłania znacznika czasu źródła i obliczania opóźnienia ścieżki z wzorca do klienta.
* **Follow_Up**. Jest to ogólny komunikat. Jest ona opcjonalna i służy do poprawiania znacznika czasu źródła w powiązanym komunikacie synchronizacji. Jest on wysyłany tylko wtedy, gdy bit dwuetapowy w flagi synchronizacji jest ustawiony.
* **Delay_Req**. Jest to komunikat zdarzenia. Jest on wysyłany z klienta PTP w celu obliczenia opóźnienia ścieżki z klienta do głównego po otrzymaniu Delay_Resp.
* **Delay_Resp**. Jest to komunikat zdarzenia. Jest on wysyłany z wzorca do klienta w celu obliczenia opóźnienia ścieżki z klienta do klienta głównego.

*Należy pamiętać, że algorytm "najlepszy zegar główny" nie jest zaimplementowany. Tylko pierwszy zegar główny jest akceptowany, gdy klient PTP jest w stanie nasłuchiwania.*

## <a name="netx-duo-ptp-client-clock-callback"></a>Wywołanie zwrotne zegara klienta NetX Duo PTP
Aby zsynchronizować zegar z głównego klienta PTP wymaga zegara lokalnego. Funkcja wywołania zwrotnego zegara jest przekazywana do klienta PTP podczas tworzenia. Format procedury wywołania zwrotnego zegara jest zdefiniowany poniżej.
```C
UINT ptp_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```
Parametry wejściowe są zdefiniowane w następujący sposób:
* *client_ptr* wskazuje klienta PTP.
* *Operacja* określa operację wywołania zwrotnego, prawidłowe wartości są zdefiniowane, jak pokazano na poniższej liście.
  * **NX_PTP_CLIENT_CLOCK_INIT** Zaimicjuj zegar.
  * **NX_PTP_CLIENT_CLOCK_SET** Ustaw bieżący znacznik czasu określony przez `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_GET** Zwróć bieżący znacznik czasu do `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Wyodrębnij znacznik czasu z `packet_ptr` do `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_ADJUST** Dostosuj bieżący znacznik czasu krótszy niż *1* sekundę.
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Oznacz znacznik , który wymaga powiadomienia klienta PTP o `packet_ptr` znaczniku czasu, gdy jest przesyłany.
  * **NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Aktualizowanie czasomierza programowego. Można ją zignorować za pomocą zegara sprzętowego.
* *time_ptr* wskazuje znacznik czasu.
* *packet_ptr* wskazuje pakiet.
* *callback_data* punkty na nieprzezroczyste dane wywołania zwrotnego.

Typ NX_PTP_TIME danych jest zdefiniowany w następujący sposób.
```C
typedef struct NX_PTP_TIME_STRUCT
{
    /* The MSB of the number of seconds */
    LONG  second_high;

    /* The LSB of the number of seconds */
    ULONG second_low;

    /* The number of nanoseconds */
    LONG  nanosecond;
} NX_PTP_TIME;
```

## <a name="netx-duo-ptp-client-event-callback"></a>Wywołanie zwrotne zdarzeń klienta PTP NetX Duo
Funkcję wywołania zwrotnego zdarzeń można skonfigurować w celu powiadamiania aplikacji o stanie klienta PTP. Format procedury wywołania zwrotnego zdarzeń jest zdefiniowany, jak pokazano poniżej.
```C
UINT event_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT event, 
    VOID *event_data, 
    VOID *callback_data);
```
Parametry wejściowe to.
* *client_ptr* wskazuje klienta PTP.
* *zdarzenie* określa zdarzenie wywołania zwrotnego, prawidłowe wartości są zdefiniowane jako:
  * **NX_PTP_CLIENT_EVENT_MASTER** Zegar główny jest zaznaczony.
  * **NX_PTP_CLIENT_EVENT_SYNC** Klient PTP jest skalibrowany.
  * **NX_PTP_CLIENT_EVENT_TIMEOUT** Zegar główny ma limit czasu.
* *event_data* określa dane związane ze zdarzeniem. Gdy zdarzenie jest **NX_PTP_CLIENT_EVENT_MASTER**, event_data wskazuje `NX_PTP_CLIENT_MASTER` wystąpienie. Gdy zdarzenie jest **NX_PTP_CLIENT_EVENT_SYNC**, dane zdarzenia wskazuje `NX_PTP_CLIENT_SYNC` wystąpienie.

## <a name="netx-duo-ptp-client-communication"></a>NetX Duo PTP Client Communication
Jak wspomniano wcześniej, klient NetX Duo PTP obsługuje tylko mechanizm opóźnienia żądań i odpowiedzi. Ten mechanizm mierzy średnie opóźnienie ścieżki między klientem a zegarem głównym, jak podano poniżej:
1. Klient odbiera komunikat *z ogłoszeniem* z wzorca i wybiera go jako najlepszy wzorzec.
1. Klient odbiera komunikat *synchronizacji* z głównego. Znacznik czasu *t1 jest* sygnaturą czasową źródła w tym komunikacie. Znacznik czasu *t2* jest odczytywany z zegara lokalnego po otrzymaniu tego komunikatu.
1. Klient odbiera *Follow_Up* z wzorca. Ten komunikat jest opcjonalny i prawidłowy tylko wtedy, gdy ustawiono dwa kroki *flagi* synchronizacji. Następnie znacznik czasu *t1* jest aktualizowany do znacznika czasu źródła w tym komunikacie.
1. Klient wysyła *Delay_Req* do wzorca. Znacznik czasu *t3* jest odczytywany z zegara lokalnego, gdy komunikat jest przesyłany.
1. Klient odbiera *Delay_Resp* z głównego. Znacznik czasu *t4* jest sygnaturą czasową odbierania w tym komunikacie.

Średnie opóźnienie ścieżki jest obliczane, jak pokazano poniżej.
```C
<meanPathDelay>=[(t2-t1)+(t4-t3)]/2
```
Przesunięcie od wzorca jest obliczane, jak pokazano poniżej.
```C
<offsetFromMaster>=client_clock-master_clock
                  =(t2-t1)-<meanPathDelay>
```

> [!NOTE]
> *Wartość ***correctionField** _ jest ignorowana podczas calculation._