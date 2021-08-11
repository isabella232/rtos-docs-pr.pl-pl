---
title: Rozdział 1 — Wprowadzenie do Azure RTOS NetX
description: Ten rozdział zawiera wprowadzenie do Azure RTOS NetX oraz opis jego aplikacji i korzyści.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 207aaec18f020e8cc3534a9ef55ed338df487fd95b22b5021f691ea63ba62b8b
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782866"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx"></a>Rozdział 1 — Wprowadzenie do Azure RTOS NetX

Azure RTOS NetX to implementacja standardów TCP/IP o wysokiej wydajności w czasie rzeczywistym przeznaczona wyłącznie dla osadzonych aplikacji opartych na technologii ThreadX. Ten rozdział zawiera wprowadzenie do środowiska NetX oraz opis jego aplikacji i korzyści.

## <a name="netx-unique-features"></a>NetX Unique Features

W przeciwieństwie do innych implementacji TCP/IP, netx został zaprojektowany tak, aby był wszechstronny — łatwo skalować z małych aplikacji opartych na mikrokontrolerze do tych, które korzystają z zaawansowanych procesorów RISC i DSP. Jest to w dużym przeciwieństwie do domeny publicznej lub innych implementacji komercyjnych pierwotnie przeznaczonych dla środowisk stacji roboczych, ale następnie z osadzonymi projektami.

### <a name="piconettrade-architecture"></a>Architektura &trade; Piconet

Bazą najwyższej skalowalności i wydajności netx jest *Piconet*, architektura oprogramowania specjalnie zaprojektowana dla systemów osadzonych. Architektura Piconet maksymalizuje skalowalność, implementując usługi NetX jako bibliotekę języka C. W ten sposób tylko te usługi rzeczywiście używane przez aplikację są wyprowadzane do obrazu końcowego środowiska uruchomieniowego. W związku z tym rzeczywisty rozmiar NetX jest całkowicie określany przez aplikację. W przypadku większości aplikacji wymagania dotyczące rozmiaru obrazu NetX wahają się w zakresie od 5 KB do 30 KB.

NetX osiąga doskonałą wydajność sieci przez nakładanie warstw wewnętrznych wywołań funkcji składników tylko wtedy, gdy jest to absolutnie konieczne. Ponadto większość przetwarzania NetX jest wykonywana bezpośrednio w wierszu, co pozwala na niesłychanie korzystne działanie oprogramowania sieciowego stacji roboczej, które było często używane w projektach osadzonych w przeszłości.</th>

### <a name="zero-copy-implementation"></a>Implementacja bez kopiowania

NetX zapewnia opartą na pakietach *implementację* protokołu TCP/IP bez kopiowania. Zerowy kopiowanie oznacza, że dane w buforze pakietów aplikacji nigdy nie są kopiowane wewnątrz netx. Znacznie zwiększa to wydajność i pozwala zmniejszyć liczbę cennych cykli procesora w aplikacji, co jest niezwykle ważne w aplikacjach osadzonych.

### <a name="udp-fast-pathtrade-technology"></a>Technologia szybkiej ścieżki UDP &trade;

Dzięki *technologii fast path protokołu UDP* technologia NetX zapewnia najszybsze możliwe przetwarzanie UDP. Po stronie wysyłającej przetwarzanie UDP — w tym opcjonalną sumy kontrolnej UDP — jest całkowicie zawarte w nx_udp_socket_send ***usługi.*** Żadne dodatkowe wywołania funkcji nie są dokonywane, dopóki pakiet nie będzie gotowy do wysłania za pośrednictwem wewnętrznej procedury wysyłania adresów IP NetX. Ta procedura jest również płaska (tj. zagnieżdżanie wywołań funkcji jest minimalne), więc pakiet jest szybko wysyłany do sterownika sieciowego aplikacji. Po otrzymaniu pakietu UDP przetwarzanie odbierania pakietów NetX umieszcza pakiet bezpośrednio w kolejce odbierania odpowiedniego gniazda UDP lub przekazuje go do pierwszego wątku wstrzymanego w oczekiwaniu na pakiet odbierania z kolejki odbierania gniazda UDP. Nie są wymagane żadne dodatkowe przełączniki kontekstu ThreadX.

### <a name="ansi-c-source-code"></a>Kod źródłowy ANSI C

NetX jest napisany całkowicie w języku ANSI C i jest natychmiast przenośny do praktycznie dowolnej architektury procesora, która obsługuje kompilator ANSI C i threadX.

### <a name="not-a-black-box"></a>Nie jest czarną skrzynką

Większość dystrybucji NetX zawiera pełny kod źródłowy języka C. Eliminuje to problemy "czarnej skrzynki", które występują w przypadku wielu komercyjnych stosów sieciowych. Korzystając z netX, deweloperzy aplikacji mogą zobaczyć dokładnie, co robi stos sieciowy — nie ma żadnych odjęć!
  
Kod źródłowy umożliwia również modyfikacje specyficzne dla aplikacji. Chociaż nie jest to zalecane, na pewno korzystne jest, aby mieć możliwość modyfikowania stosu sieciowego, jeśli jest to wymagane.  

Te funkcje są szczególnie wygodne dla deweloperów, którzy są przywykli do pracy ze stosami sieci domeny lokalnej lub publicznej. Oczekują oni kodu źródłowego i możliwości jego modyfikowania. NetX to ostateczne oprogramowanie sieciowe dla takich deweloperów.

### <a name="bsd-compatible-socket-api"></a>interfejs API BSD-Compatible Socket

W przypadku starszych aplikacji NetX udostępnia interfejs gniazd zgodny z BSD, który wykonuje wywołania interfejsu API NetX o wysokiej wydajności poniżej. Ułatwia to migrowanie istniejącego kodu aplikacji sieciowej do systemu NetX.

## <a name="rfcs-supported-by-netx"></a>RFC obsługiwane przez NetX

Obsługa NetX RFC opisujących podstawowe protokoły sieciowe obejmuje między innymi następujące protokoły sieciowe. Środowisko NetX jest zgodna ze wszystkimi ogólnymi zaleceniami i podstawowymi wymaganiami w ramach ograniczeń systemu operacyjnego w czasie rzeczywistym z małym zużyciem pamięci i wydajnym wykonywaniem.

| RFC      | Opis                                            |
|----------|--------------------------------------------------------|
| RFC 1112 | Rozszerzenia hosta dla multiemisji IP (IGMPv1)           |
| RFC 1122 | Wymagania dotyczące hostów internetowych — warstwy komunikacyjne |
| RFC 2236 | Protokół zarządzania grupą internetową, wersja 2          |
| RFC 768  | Protokół UDP (User Datagram Protocol)                           |
| RFC 791  | Protokół internetowy (IP)                                 |
| RFC 792  | Protokół ICMP (Internet Control Message Protocol)               |
| RFC 793  | Transmission Control Protocol (TCP)                    |
| RFC 826  | Protokół ARP (Ethernet Address Resolution Protocol)             |
| RFC 903  | Protokół RARP (Reverse Address Resolution Protocol)             |
|          |                                                        |

## <a name="embedded-network-applications"></a>Osadzone aplikacje sieciowe

Osadzone aplikacje sieciowe to aplikacje, które wymagają dostępu do sieci i są wykonywane na mikroprocesorach ukrytych wewnątrz produktów, takich jak telefony komórkowe, sprzęt komunikacyjny, aparaty samochodowy, drukarki laserowe, urządzenia medyczne itd. Takie aplikacje prawie zawsze mają pewne ograniczenia dotyczące pamięci i wydajności. Innym rozróżnieniem aplikacji sieciowych osadzonych jest to, że ich oprogramowanie i sprzęt mają specjalne przeznaczenie.

### <a name="real-time-network-software"></a>Oprogramowanie sieciowe w czasie rzeczywistym  

Zasadniczo oprogramowanie sieciowe, które musi wykonywać przetwarzanie w dokładnie   krótkim czasie, jest nazywane oprogramowaniem sieciowym w czasie rzeczywistym, a gdy na aplikacje sieciowe nakładane są ograniczenia czasowe, są one klasyfikowane jako aplikacje w czasie rzeczywistym. Osadzone aplikacje sieciowe prawie zawsze są dostępne w czasie rzeczywistym ze względu na ich naturalną interakcję ze światem zewnętrznym.

## <a name="netx-benefits"></a>Korzyści netx

Głównymi zaletami korzystania z netx w przypadku aplikacji osadzonych są szybkie połączenia z Internetem i bardzo małe wymagania dotyczące pamięci. NetX jest również całkowicie zintegrowany z wysokowydajnym, wielozadaniowym systemem operacyjnym ThreadX w czasie rzeczywistym.

### <a name="improved-responsiveness"></a>Ulepszona szybkość reagowania  

Stos protokołu NetX o wysokiej wydajności umożliwia aplikacjom sieci osadzonej szybsze reagowanie niż kiedykolwiek wcześniej. Jest to szczególnie ważne w przypadku aplikacji osadzonych, które mają znaczną ilość ruchu sieciowego lub rygorystyczne wymagania dotyczące przetwarzania pojedynczego pakietu.

### <a name="software-maintenance"></a>Konserwacja oprogramowania

Korzystanie z oprogramowania NetX umożliwia deweloperom łatwe partycjonowanie aspektów sieciowych osadzonej aplikacji. Partycjonowanie sprawia, że cały proces tworzenia oprogramowania jest prosty i znacząco usprawnia przyszłą konserwację oprogramowania.

### <a name="increased-throughput"></a>Zwiększona przepływność

NetX zapewnia dostępną sieć o najwyższej wydajności, co jest osiągane przez minimalne obciążenie związane z przetwarzaniem pakietów. Umożliwia to również zwiększenie przepływności.

### <a name="processor-isolation"></a>Izolacja procesora

NetX zapewnia niezawodny, niezależny od procesora interfejs między aplikacją a bazowym procesorem i sprzętem sieciowym. Dzięki temu deweloperzy mogą skoncentrować się na aspektach sieciowych aplikacji, zamiast poświęcać dodatkowy czas na radzenie sobie ze sprzętem, które bezpośrednio wpływają na sieć.

### <a name="ease-of-use"></a>Łatwość użycia

NetX został zaprojektowany z myślą o deweloperze aplikacji. Architektura NetX i interfejs wywołania usługi są łatwe do zrozumienia. W związku z tym deweloperzy oprogramowania NetX mogą szybko korzystać z jej zaawansowanych funkcji.

### <a name="improve-time-to-market"></a>Poprawianie czasu na rynek

Zaawansowane funkcje oprogramowania NetX przyspieszają proces tworzenia oprogramowania. NetX stanowi abstrakcję większości problemów ze sprzętem procesora i sieci, co usuwa te problemy z większości obszarów specyficznych dla sieci aplikacji. W połączeniu z łatwością użycia i zaawansowanym zestawem funkcji pozwala to przyspieszyć rynek.

### <a name="protecting-the-software-investment"></a>Ochrona inwestycji w oprogramowanie

NetX jest napisany wyłącznie w języku ANSI C i jest w pełni zintegrowany z systemem operacyjnym ThreadX w czasie rzeczywistym. Oznacza to, że aplikacje NetX są natychmiast przenośne na wszystkie procesory obsługiwane przez ThreadX. Co więcej, zupełnie nowa architektura procesora może być obsługiwana przez ThreadX w ciągu kilku tygodni. W związku z tym użycie narzędzia NetX zapewnia ścieżkę migracji aplikacji i chroni pierwotną inwestycję deweloperską.
