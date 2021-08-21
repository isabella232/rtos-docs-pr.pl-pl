---
title: Rozdział 3 — Uruchamianie testu przesyłania UDP
description: Ten rozdział zawiera instrukcje dotyczące uruchamiania przykładu Iperf.
author: v-condav
ms.author: v-condav
ms.date: 08/16/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2a68ba3ddb71adc424002c815fd023f50b552997
ms.sourcegitcommit: 4842f4cfe9e31b3ac59059f43e598eb70faebc8f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2021
ms.locfileid: "122609961"
---
# <a name="chapter-3-running-the-demonstration"></a>Rozdział 3 Uruchamianie pokazu

Zakładając, że przeglądarka hosta wyświetla stronę internetową NetX Duo Iperf Demonstration, jak pokazano wcześniej, i aplikacja Jperf jest uruchomiona na hoście, w tym rozdziale opisano sposób wykonywania każdego testu Iperf.

## <a name="running-the-udp-transmit-test"></a>Uruchamianie testu przesyłania UDP

Test przesyłania UDP określa wydajność transmisji netx duo UDP do hosta. W tym teście element docelowy NetX Duo jest klientem, a host Jperf jest serwerem. Najpierw wybierz pozycję **Serwer i** **UDP** w idee Jperf. Następnie wybierz pozycję **Uruchom IPerf!** w celu zainicjowania serwera Iperf, jak pokazano poniżej.

![Uruchamianie testu transmisji UDP.](media/picture3.jpg)

Teraz na stronie internetowej NetX Duo Iperf Demonstration (Pokazowa aplikacja NetX Duo) wybierz przycisk **Start UDP Transmit Test (Uruchom** test przesyłania UDP), aby zainicjować test. Teraz należy obserwować statystyki wydajności w środowiskach IDE Jperf i zaktualizowanej stronie internetowej NetX Duo, jak pokazano poniżej.

![Statystyki testu transmisji UDP.](media/picture4.jpg)

Aby ukończyć test, wybierz **link tutaj** na stronie internetowej NetX Duo Iperf Demonstration. Teraz należy obserwować wyniki wydajności testu. W tym przykładzie wydajność transmisji UDP na celu NetX Duo do hosta Iperf wynosi 94 Mb/s w celu NetX Duo, jak pokazano poniżej.

![Wyniki testu transmisji UDP.](media/picture5.jpg)

## <a name="running-the-udp-receive-test"></a>Uruchamianie testu odbierania UDP

Test odbierania UDP określa wydajność odbioru protokołu NetX Duo UDP w celu NetX Duo. W tym teście element docelowy NetX Duo jest serwerem, a host Jperf jest klientem. Najpierw wybierz pozycję **Klient i** **UDP** w idee Jperf. Następnie wybierz pozycję **Uruchom test odbierania UDP** na stronie internetowej pokazu netX Duo Iperf, jak pokazano na poniższej ilustracji.

![Uruchomienie testu odbioru protokołu UDP.](media/picture6.jpg)

Teraz wybierz **pozycję Uruchom IPerf!** ze środowiska IDE Jperf i obserwuj statystyki w ide Jperf, jak pokazano poniżej.

![Odbieranie statystyk testów przez protokołu UDP.](media/picture7.jpg)

Aby ukończyć test, wybierz link **tutaj** na stronie internetowej pokazu NetX Duo Iperf. Teraz należy obserwować wyniki wydajności testu. W tym przykładzie wydajność odbioru UDP w celu NetX Duo wynosi 95 Mb/s, jak pokazano poniżej.

![Odbieranie wyników testów protokołu UDP](media/picture8.jpg)

## <a name="running-the-tcp-transmit-test"></a>Uruchamianie testu transmisji TCP

Test transmisji TCP określa wydajność transmisji TCP NetX Duo do hosta. W tym teście element docelowy NetX Duo jest klientem, a host Jperf jest serwerem. Najpierw wybierz pozycję **Serwer i** **protokół TCP** w idee Jperf. Następnie wybierz pozycję **Uruchom IPerf!** w celu zainicjowania serwera Iperf, jak pokazano poniżej.

![Uruchomienie testu przesyłania TCP.](media/picture9.jpg)

Teraz na stronie internetowej NetX Duo Iperf Demonstration (Pokazowa aplikacja NetX Duo) wybierz przycisk Start TCP Transmit Test (Uruchom test transmisji **tcp),** aby zainicjować test. Teraz należy obserwować statystyki wydajności w środowiskach IDE Jperf i zaktualizowanej stronie internetowej programu NetX Duo Iperf Demonstration, jak pokazano poniżej.

![Statystyki testu przesyłania tcp.](media/picture10.jpg)

Aby ukończyć test, wybierz link ***tutaj*** na stronie internetowej pokazu NetX Duo Iperf. Teraz należy obserwować wyniki wydajności testu. W tym przykładzie wydajność transmisji TCP w celu NetX Duo wynosi 91 Mb/s, jak pokazano poniżej.

![Tcp przesyła wyniki testu.](media/picture11.jpg)

## <a name="running-the-tcp-receive-test"></a>Uruchamianie testu odbierania protokołu TCP

Test odbierania TCP określa wydajność odbioru tcp NetX Duo w celu NetX Duo. W tym teście element docelowy NetX Duo jest serwerem, a host Jperf jest klientem. Najpierw wybierz pozycję **Klient i** **protokół TCP** w idee Jperf. Następnie wybierz pozycję **Uruchom test odbierania protokołu TCP** na stronie internetowej NetX Duo, jak pokazano.

![Uruchamianie testu odbierania protokołu TCP](media/picture12.jpg)

Teraz wybierz **pozycję Uruchom IPerf!** ze środowiska IDE Jperf i obserwuj statystyki w ide Jperf, jak pokazano poniżej.

![Protokół TCP odbiera statystyki testów.](media/picture13.jpg)

Aby ukończyć test, wybierz link ***tutaj*** na stronie internetowej pokazu NetX Duo Iperf. Teraz należy obserwować wyniki wydajności testu. W tym przykładzie wydajność odbioru PROTOKOŁU TCP dla obiektu docelowego NetX Duo wynosi 71 Mb/s, jak pokazano poniżej.

![Protokół TCP odbiera wyniki testu.](media/picture14.jpg)
