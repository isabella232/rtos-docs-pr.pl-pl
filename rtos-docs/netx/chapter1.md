---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX
description: Ten rozdział zawiera wprowadzenie do usługi Azure RTO NetX oraz opis jej aplikacji i korzyści.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 48be6a7ecddc53b36b3cc1a9ecfb50a11e285881
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822795"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO NetX

Usługa Azure RTO NetX to implementacja standardów TCP/IP w czasie rzeczywistym, które są przeznaczone wyłącznie dla wbudowanych aplikacji opartych na ThreadX. Ten rozdział zawiera wprowadzenie do NetX oraz opis jego aplikacji i korzyści.

## <a name="netx-unique-features"></a>NetX unikatowe funkcje

W przeciwieństwie do innych implementacji protokołu TCP/IP, NetX został zaprojektowany jako uniwersalny — można łatwo skalować od małych aplikacji opartych na mikrokontrolerach do tych, które używają zaawansowanych procesorów RISC i DSP. Jest to bardzo zróżnicowane dla domeny publicznej lub innych implementacji komercyjnych pierwotnie przeznaczonych dla środowisk stacji roboczych, ale a następnie zostały podzielone na osadzone projekty.

### <a name="piconettrade-architecture"></a>&trade;Architektura Piconet

Podstawową skalowalnością i wydajnością NetX jest *Piconet*, architektury oprogramowania specjalnie zaprojektowanej dla systemów osadzonych. Architektura Piconet maksymalizuje skalowalność, implementując usługi NetX jako bibliotekę języka C. W ten sposób tylko usługi faktycznie używane przez aplikację są umieszczane w końcowym obrazie środowiska uruchomieniowego. W związku z tym rzeczywisty rozmiar NetX jest całkowicie określony przez aplikację. W przypadku większości aplikacji wymagania dotyczące rozmiaru obrazu NetX zakresów od 5 kilobajtów do 30 kilobajtów.

NetX zapewnia wyższą wydajność sieci przez równoległe wywołania funkcji składników wewnętrznych tylko wtedy, gdy jest to absolutnie konieczne. Ponadto wiele NetX przetwarzania jest wykonywane bezpośrednio w trybie online, co spowodowało znakomite wykorzystanie wydajności przez oprogramowanie sieciowe stacji roboczej, które często było używane w osadzonych projektach w przeszłości.</th>

### <a name="zero-copy-implementation"></a>Implementacja kopiowania zerowego

NetX *zapewnia implementację* protokołu TCP/IP bazującą na pakietach. Kopia zerowa oznacza, że dane w buforze pakietów aplikacji nigdy nie są kopiowane wewnątrz NetX. Znacznie poprawia to wydajność i zwalnia cenne cykle procesora dla aplikacji, co jest niezwykle ważne w aplikacjach osadzonych.

### <a name="udp-fast-pathtrade-technology"></a>Technologia szybkiego ścieżki UDP &trade;

Dzięki *technologii UDP Fast Path* NetX zapewnia najszybszy możliwy do przetworzenia UDP. Po stronie wysyłającej przetwarzanie UDP — w tym opcjonalną sumę kontrolną UDP — jest całkowicie zawarte w usłudze ***nx_udp_socket_send*** . Nie są wykonywane żadne dodatkowe wywołania funkcji, dopóki pakiet nie zostanie gotowy do wysłania przez wewnętrzną procedurę wysyłania protokołu IP NetX. Ta procedura jest również płaska (tj. jego zagnieżdżenie wywołań funkcji jest minimalne), dzięki czemu pakiet jest szybko wysyłany do sterownika sieci aplikacji. Po odebraniu pakietu UDP przetwarzanie odbierania pakietów NetX umieszcza pakiet bezpośrednio w odpowiedniej kolejce odbioru gniazda UDP lub przekazuje go do pierwszego wątku, oczekując na odebranie pakietu z kolejki odbierania w gnieździe UDP. Nie są wymagane żadne dodatkowe przełączniki kontekstu ThreadX.

### <a name="ansi-c-source-code"></a>Kod źródłowy ANSI C

NetX jest zapisywana całkowicie w standardzie ANSI C i jest natychmiast przenośny do praktycznie dowolnej architektury procesora, która ma kompilator ANSI C i obsługę ThreadX.

### <a name="not-a-black-box"></a>To nie jest czarne pole

Większość dystrybucji NetX obejmuje pełny kod źródłowy języka C. Eliminuje to problemy "z czarnym pudełkem" występujące w wielu stosach sieci komercyjnych. Korzystając z NetX, deweloperzy aplikacji mogą zobaczyć dokładnie, co robi stos sieciowy — nie ma Mysteries!
  
Kod źródłowy umożliwia również modyfikacje specyficzne dla aplikacji. Chociaż nie jest to zalecane, korzystne jest, aby mieć możliwość modyfikowania stosu sieciowego, jeśli jest to wymagane.  

Te funkcje są szczególnie wygodne dla deweloperów przyzwyczajonych do pracy z stosami sieci w domu lub w domenie publicznej. Powinny one mieć kod źródłowy i możliwość jego modyfikacji. NetX to ostateczne oprogramowanie sieciowe dla takich deweloperów.

### <a name="bsd-compatible-socket-api"></a>Interfejs API usługi BSD-Compatible Socket

W przypadku starszych aplikacji NetX udostępnia interfejs Socket zgodny z systemem BSD, który umożliwia nawiązywanie połączeń z interfejsem API NetX o wysokiej wydajności poniżej. Ułatwia to Migrowanie istniejącego kodu aplikacji sieciowej do NetX.

## <a name="rfcs-supported-by-netx"></a>Specyfikacje RFC obsługiwane przez NetX

Obsługa NetX w specyfikacjach RFC opisujących podstawowe protokoły sieciowe obejmuje, ale nie jest ograniczona do następujących protokołów sieciowych. NetX przestrzega wszystkich ogólnych zaleceń i podstawowych wymagań w ramach ograniczeń systemu operacyjnego w czasie rzeczywistym z małą ilością pamięci i wydajnym wykonywaniem.

| RFC      | Opis                                            |
|----------|--------------------------------------------------------|
| RFC 1112 | Rozszerzenia hosta do multiemisji IP (IGMPv1)           |
| RFC 1122 | Wymagania dotyczące hostów internetowych — warstwy komunikacji |
| RFC 2236 | Protokół zarządzania grupami internetowymi, wersja 2          |
| RFC 768  | User Datagram Protocol (UDP)                           |
| RFC 791  | Protokół internetowy (IP)                                 |
| RFC 792  | Protokół ICMP (Internet Control Message Protocol)               |
| RFC 793  | Transmission Control Protocol (TCP)                    |
| RFC 826  | Protokół ARP (Ethernet Address Resolution Protocol)             |
| RFC 903  | Protokół odwrotnego rozpoznawania adresów (RARP)             |
|          |                                                        |

## <a name="embedded-network-applications"></a>Osadzone aplikacje sieciowe

Osadzone aplikacje sieciowe to aplikacje, które wymagają dostępu do sieci i działają w mikroprocesorach ukrytych w produktach, takich jak telefony komórkowe, sprzęt komunikacyjny, silniki motoryzacyjne, drukarki laserowe, urządzenia medyczne itd. Takie aplikacje prawie zawsze mają pewne ograniczenia dotyczące pamięci i wydajności. Innym rozróżnianie osadzonych aplikacji sieciowych polega na tym, że ich oprogramowanie i sprzęt mają dedykowany cel.

### <a name="real-time-network-software"></a>Oprogramowanie sieciowe w czasie rzeczywistym  

Zasadniczo oprogramowanie sieciowe, które musi wykonać przetwarzanie w określonym czasie, jest nazywane oprogramowaniem *sieci* w czasie *rzeczywistym* , a w przypadku zastosowania ograniczeń czasowych w aplikacjach sieciowych są one klasyfikowane jako aplikacje w czasie rzeczywistym. Osadzone aplikacje sieciowe są prawie zawsze w czasie rzeczywistym ze względu na ich nieodłączną współpracę z zewnętrznym światem.

## <a name="netx-benefits"></a>Korzyści z NetX

Podstawową zaletą korzystania z NetX dla aplikacji osadzonych są szybkie połączenia z Internetem i bardzo małe wymagania dotyczące pamięci. NetX jest również całkowicie zintegrowany z wysoce wydajnym systemem operacyjnym ThreadX w czasie rzeczywistym.

### <a name="improved-responsiveness"></a>Zwiększona czas odpowiedzi  

Stos protokołu NetX o wysokiej wydajności umożliwia aplikacjom osadzonym w sieci szybsze reagowanie niż kiedykolwiek wcześniej. Jest to szczególnie ważne w przypadku aplikacji osadzonych, które mają znaczną ilość ruchu sieciowego lub rygorystyczne wymagania dotyczące przetwarzania w pojedynczym pakiecie.

### <a name="software-maintenance"></a>Konserwacja oprogramowania

Korzystanie z programu NetX umożliwia deweloperom łatwe partycjonowanie aspektów sieci aplikacji osadzonej. Takie partycjonowanie sprawia, że cały proces tworzenia oprogramowania jest łatwy i znacząco ulepsza konserwację w przyszłości.

### <a name="increased-throughput"></a>Zwiększona przepływność

NetX zapewnia dostęp do najwyższej wydajności sieci, która jest osiągana w minimalnym obciążeniu przetwarzania pakietów. Zapewnia to również zwiększoną przepływność.

### <a name="processor-isolation"></a>Izolacja procesora

NetX zapewnia niezawodny, niezależny od procesora interfejs między aplikacją a podstawowym procesorem i sprzętem sieciowym. Pozwala to deweloperom skoncentrować się na aspektach sieci aplikacji, a nie poświęcać dodatkowego czasu na problemy ze sprzętem bezpośrednio wpływające na sieć.

### <a name="ease-of-use"></a>Łatwość użycia

NetX jest zaprojektowana z myślą o deweloperu aplikacji. Interfejs NetX i architektura wywołania usługi są łatwe do zrozumienia. W związku z tym NetX deweloperzy mogą szybko korzystać z zaawansowanych funkcji.

### <a name="improve-time-to-market"></a>Popraw czas wprowadzenia na rynek

Zaawansowane funkcje NetX przyspieszają proces tworzenia oprogramowania. NetX abstrakcje większości problemów sprzętowych procesora i sieci, usuwając te zagadnienia z większości obszarów specyficznych dla sieci aplikacji. W związku z tym łatwość użycia i zaawansowanego zestawu funkcji powoduje skrócenie czasu wprowadzenia na rynek.

### <a name="protecting-the-software-investment"></a>Ochrona inwestycji w oprogramowanie

NetX jest zapisywana wyłącznie w standardzie ANSI C i jest w pełni zintegrowana z systemem operacyjnym ThreadX w czasie rzeczywistym. Oznacza to, że aplikacje NetX są natychmiast przenośne do wszystkich obsługiwanych procesorów ThreadX. Lepiej w dalszym ciągu można obsługiwać zupełnie nową architekturę procesora z ThreadX w ciągu kilku tygodni. W związku z tym użycie NetX gwarantuje, że ścieżka migracji aplikacji i chroni pierwotne inwestycje rozwojowe.
