---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo PTP Client
description: Ten rozdział zawiera wprowadzenie do klienta PTP usługi Azure RTO NetX Duo.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5beec64bd6d74e3bed06be15255d6bd4a940ba64
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821709"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-ptp-client"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo PTP Client

Program Azure RTO NetX Duo jest implementacją klienta w wersji 2, IEEE 1588-2008. Służy do synchronizowania zegarów między MCUs w sieci lokalnej przez wzajemne komunikowanie się za pośrednictwem protokołu IPv4 lub IPv6 pakietów multiemisji.

## <a name="netx-duo-ptp-client-setup"></a>Instalator klienta PTP NetX Duo

Aby zapewnić prawidłowe działanie, pakiet klienta protokołu PTP wymaga, aby wystąpienie NetX Duo zostało już utworzone.

Domyślnie klient protokołu PTP sprzęga grupę multiemisji IPv4. Aby można było uruchomić klienta protokołu PTP w sieci IPv6, `NX_ENABLE_IPV6_MULTICAST` należy go zdefiniować podczas kompilowania biblioteki NetX Duo.

Podczas tworzenia klienta programu PTP aplikacja musi zapewnić funkcję wywołania zwrotnego, aby obsługiwać sygnatury czasowe pakietów przychodzących i wychodzących. Aby osiągnąć wysoką rozdzielczość, zalecamy stosowanie aplikacji do generowania sygnatur czasowych przy użyciu czasomierza o wysokiej rozdzielczości. Do uruchomienia protokołu PTP w symulatorze zostanie udostępniona implementacja oparta na oprogramowaniu `nx_ptp_client_soft_clock_callback` .

Klient PTP wymaga puli pakietów do przesyłania komunikatów PTP. Rozmiar ładunku puli pakietów nie może być mniejszy niż `NX_UDP_PACKET + NX_PTP_CLIENT_PACKET_DATA_SIZE` , czyli 108 bajtów dla IPv4, i 128 bajtów, jeśli jest włączony protokół IPv6.

Po utworzeniu klienta programu PTP aplikacja może uruchomić klienta programu PTP. Synchronizacja jest wykonywana w wątku pomocnika PTP. Można określić funkcję wywołania zwrotnego zdarzenia. Zostanie wywołana w przypadku wystąpienia jednego z następujących zdarzeń.
* Wybrano wzorzec; 
* Czas jest kalibrowany.
* Główny limit czasu.

## <a name="netx-duo-ptp-client-messages"></a>Komunikaty klienta PTP NetX Duo

Klient PTP NetX Duo implementuje tylko mechanizm opóźnienia żądania-odpowiedź. Klient protokołu PTP otwiera dwa porty UDP. *319* dla komunikatu o **zdarzeniu** i *320* dla komunikatu **ogólnego** . Dla tego mechanizmu istnieje pięć typów komunikatów.

* **Ogłoszenie**. Jest to komunikat o zdarzeniu. Służy do wyboru zegara głównego.
* **Synchronizuj**. Jest to komunikat o zdarzeniu. Służy do wysyłania znacznika czasu pochodzenia i obliczania opóźnienia ścieżki od wzorca do klienta.
* **Follow_Up**. Jest to komunikat ogólny. Jest on opcjonalny i używany do korygowania sygnatury czasowej źródła w powiązanym komunikacie synchronizacji. Jest on wysyłany tylko wtedy, gdy ustawiono flagę dwóch etapów synchronizacji.
* **Delay_Req**. Jest to komunikat o zdarzeniu. Jest wysyłany z klienta programu PTP w celu obliczenia opóźnienia ścieżki od klienta do serwera głównego przy odebraniu Delay_Resp.
* **Delay_Resp**. Jest to komunikat o zdarzeniu. Jest on wysyłany z serwera głównego do klienta w celu obliczenia opóźnienia ścieżki od klienta do serwera głównego.

*Uwaga "nie zaimplementowano algorytmu" najlepszy wzorzec zegara ". Tylko pierwszy zegar główny jest akceptowany, gdy klient programu PTP jest w stanie nasłuchiwania.*

## <a name="netx-duo-ptp-client-clock-callback"></a>Wywołanie zwrotne zegara klienta PTP NetX Duo
Aby synchronizować zegar z serwera głównego, klient PTP potrzebuje zegara lokalnego. Funkcja wywołania zwrotnego zegara jest przenoszona do klienta PTP podczas tworzenia. Poniżej określono format procedury wywołania zwrotnego zegara.
```C
UINT ptp_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```
Parametry wejściowe są zdefiniowane w następujący sposób:
* *client_ptr* punkty do klienta PTP.
* *operacja* określa operację wywołania zwrotnego, prawidłowe wartości są zdefiniowane, jak pokazano na poniższej liście.
  * **NX_PTP_CLIENT_CLOCK_INIT** Zainicjuj zegar.
  * **NX_PTP_CLIENT_CLOCK_SET** Ustaw bieżącą sygnaturę czasową określoną przez `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_GET** Zwróć bieżącą sygnaturę czasową do `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Wyodrębnij sygnaturę czasową z `packet_ptr` do `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_ADJUST** Dostosuj bieżącą sygnaturę czasową mniejszą niż *1* sekunda.
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Oznacz, `packet_ptr` które są wymagane do powiadomienia klienta PTP o sygnaturze czasowej podczas przesyłania.
  * **NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Aktualizuj czasomierz elastyczny. Może być ignorowany przez zegar sprzętu.
* *time_ptr* punkty do sygnatury czasowej.
* *packet_ptr* punkty do pakietu.
* *callback_data* punkty na nieprzezroczyste dane wywołania zwrotnego.

NX_PTP_TIME typ danych jest zdefiniowany w następujący sposób.
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

## <a name="netx-duo-ptp-client-event-callback"></a>Wywołanie zwrotne zdarzenia klienta PTP NetX Duo
Funkcję wywołania zwrotnego zdarzenia można skonfigurować w celu powiadomienia aplikacji o stanie klienta programu PTP. Format procedury wywołania zwrotnego zdarzenia jest definiowany jak pokazano poniżej.
```C
UINT event_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT event, 
    VOID *event_data, 
    VOID *callback_data);
```
Parametry wejściowe to.
* *client_ptr* punkty do klienta PTP.
* *zdarzenie* określa zdarzenie wywołania zwrotnego, prawidłowe wartości są zdefiniowane jako:
  * **NX_PTP_CLIENT_EVENT_MASTER** Wybrano zegar główny.
  * **NX_PTP_CLIENT_EVENT_SYNC** Klient PTP jest skalibrowany.
  * **NX_PTP_CLIENT_EVENT_TIMEOUT** Zegar główny to limit czasu.
* *event_data* określa dane związane ze zdarzeniem. Gdy zdarzenie jest **NX_PTP_CLIENT_EVENT_MASTER**, event_data wskazuje na `NX_PTP_CLIENT_MASTER` wystąpienie. Gdy zdarzenie jest **NX_PTP_CLIENT_EVENT_SYNC**, dane zdarzenia wskazują na `NX_PTP_CLIENT_SYNC` wystąpienie.

## <a name="netx-duo-ptp-client-communication"></a>Komunikacja klienta PTP w NetX Duo
Jak wspomniano wcześniej, klient PTP NetX Duo obsługuje tylko mechanizm opóźnienia żądania. Ten mechanizm mierzy Średnie opóźnienie ścieżki między klientem a zegarem głównym, jak pokazano poniżej:
1. Klient otrzymuje komunikat *ogłoszenia* od wzorca i wybiera go jako najlepszy serwer główny.
1. Klient odbiera komunikat *synchronizacji* z serwera głównego. Sygnatura czasowa *T1* jest sygnaturą czasową źródła w tej wiadomości. Sygnatura czasowa *T2* jest odczytywana z zegara lokalnego po odebraniu tego komunikatu.
1. Klient odbiera komunikat *Follow_Up* od serwera głównego. Ten komunikat jest opcjonalny i prawidłowy tylko wtedy, gdy ustawiono dwa kroki flagi *synchronizacji* . Następnie sygnatura czasowa *T1* jest aktualizowana do sygnatury czasowej źródła w tej wiadomości.
1. Klient wysyła komunikat *Delay_Req* do serwera głównego. Sygnatura czasowa *T3* jest odczytywana z zegara lokalnego podczas przesyłania komunikatu.
1. Klient odbiera komunikat *Delay_Resp* od serwera głównego. Sygnatura czasowa *T4* jest sygnaturą czasową odbioru w tej wiadomości.

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
> ***CorrectionField*** jest ignorowany podczas calculation._