---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo
description: Ten rozdział zawiera wprowadzenie do usługi Azure RTO NetX Duo oraz opis jej aplikacji i korzyści.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 91dfd0e62cb565f677faa7d52fe22abc1f0e19a1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822128"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo

Usługa Azure RTO NetX Duo jest implementacją standardów TCP/IP o wysokiej wydajności w czasie rzeczywistym, które są przeznaczone wyłącznie dla osadzonych aplikacji opartych na platformie Azure RTO ThreadX. Ten rozdział zawiera wprowadzenie do NetX Duo oraz opis jego aplikacji i korzyści. 

## <a name="netx-duo-unique-features"></a>Unikatowe funkcje NetX Duo

W przeciwieństwie do innych implementacji protokołu TCP/IP, NetX Duo została zaprojektowana jako uniwersalna — łatwe skalowanie z małych aplikacji opartych na kontrolerach do tych, które używają zaawansowanych procesorów RISC i DSP. Jest to bardzo zróżnicowane dla domeny publicznej lub innych implementacji komercyjnych pierwotnie przeznaczonych dla środowisk stacji roboczych, ale a następnie zostały podzielone na osadzone projekty.

### <a name="piconettrade-architecture"></a>&trade;Architektura Piconet

Podstawową skalowalnością i wydajnością NetX Duo jest <em>Piconet</em>, architektury oprogramowania specjalnie zaprojektowanej dla systemów osadzonych. Architektura Piconet maksymalizuje skalowalność przez implementację usług NetX Duo jako biblioteki języka C. W ten sposób tylko te usługi, które są używane przez aplikację, są umieszczane w końcowym obrazie środowiska uruchomieniowego. W związku z tym rzeczywisty rozmiar NetX Duo jest określany przez aplikację. W przypadku większości aplikacji wymagania dotyczące obrazów w programie NetX Duo mają zakres od 5 kilobajtów do 30 kilobajtów. W przypadku protokołu IPv6 i ICMPv6 włączonego dla konfiguracji adresów IPv6 i protokołów Neighbor Discovery zakresy NetX Duo mają rozmiar od 30 KB do 45 kilobajtów.

Program NetX Duo zapewnia wyższą wydajność sieci przez równoległe wywołania funkcji składników wewnętrznych tylko wtedy, gdy jest to konieczne. Ponadto wiele NetX Duo jest wykonywane bezpośrednio w trybie online, co spowodowało znakomite wykorzystanie wydajności przez oprogramowanie sieciowe stacji roboczej używane w osadzonych projektach w przeszłości.

### <a name="zero-copy-implementation"></a>Implementacja kopiowania zerowego

NetX Duo zapewnia implementację protokołu TCP/IP bazującą na pakietach. Kopia zerowa oznacza, że dane w buforze pakietów aplikacji nigdy nie są kopiowane w NetX Duo. Znacznie poprawia to wydajność i zwalnia cenne cykle procesora dla aplikacji, co jest ważne w aplikacjach osadzonych.

### <a name="udp-fast-pathtrade-technology"></a>Technologia szybkiego ścieżki UDP &trade;

Dzięki <em>technologii UDP Fast Path</em>NetX Duo zapewnia najszybszy możliwy do przetworzenia UDP. Po stronie wysyłającej, przetwarzanie UDP — łącznie z opcjonalną sumą kontrolną UDP — jest zawarty w ramach usługi <em>**nx_udp_socket_send**</em> . Żadne dodatkowe wywołania funkcji nie są wykonywane, dopóki pakiet nie zostanie gotowy do wysłania za pośrednictwem procedury wysyłania protokołu IP wewnętrznej NetX Duo. Ta procedura jest również płaska (to oznacza, że funkcja zagnieżdżania wywołań funkcji jest minimalna), dzięki czemu pakiet jest szybko wysyłany do sterownika sieci aplikacji. Po odebraniu pakietu UDP proces odbierania pakietów NetX Duo umieszcza pakiet bezpośrednio w odpowiedniej kolejce odbieranych gniazd UDP lub przekazuje go do pierwszego wątku, oczekując na odebranie pakietu z kolejki odbierania w gnieździe UDP. Nie są wymagane żadne dodatkowe przełączniki kontekstu ThreadX.

### <a name="ansi-c-source-cod"></a>Źródło danych dorsza ANSI C

NetX Duo jest zapisywana całkowicie w standardzie ANSI C i jest natychmiast przenośny do praktycznie dowolnej architektury procesora, która ma kompilator ANSI C i obsługę ThreadX. 

### <a name="not-a-black-box"></a>To nie jest czarne pole

Większość dystrybucji NetX Duo obejmuje pełny kod źródłowy języka C. Eliminuje to problemy "z czarnym pudełkem" występujące w wielu stosach sieci komercyjnych. Korzystając z NetX Duo, deweloperzy aplikacji mogą zobaczyć dokładnie, co robi stos sieciowy — nie ma Mysteries!

Kod źródłowy umożliwia również modyfikacje specyficzne dla aplikacji. Chociaż nie jest to zalecane, korzystne jest, aby mieć możliwość modyfikowania stosu sieciowego, jeśli jest to wymagane.

Te funkcje są szczególnie wygodne dla deweloperów przyzwyczajonych do pracy z stosami sieci w domu lub w domenie publicznej. Powinny one mieć kod źródłowy i możliwość jego modyfikacji. NetX Duo to ostateczne oprogramowanie sieciowe dla takich deweloperów.

### <a name="bsd-compatible-socket-api"></a>Interfejs API usługi BSD-Compatible Socket

W przypadku starszych aplikacji NetX Duo zapewnia również interfejs gniazda zgodny z systemem BSD, który umożliwia nawiązywanie połączeń z interfejsem API o wysokiej wydajności NetX Duo poniżej. Ułatwia to Migrowanie istniejącego kodu aplikacji sieciowej do NetX Duo.

## <a name="rfcs-supported-by-netx-duo"></a>Specyfikacje RFC obsługiwane przez NetX Duo

NetX Duo obsługuje specyfikacje RFC opisujące podstawowe protokoły sieciowe, ale nie są ograniczone do następujących protokołów sieciowych. NetX Duo stosuje się do wszystkich ogólnych zaleceń i podstawowych wymagań w ramach ograniczeń systemu operacyjnego w czasie rzeczywistym z małą ilością pamięci i wydajnym wykonaniem.

| **RFC**  | **Opis**                                        |
| -------- | ------------------------------------------------------ |
|RFC 1112 | Rozszerzenia hosta do multiemisji IP (IGMPv1)           |
|RFC 1122 | Wymagania dotyczące hostów internetowych — warstwy komunikacji |
|RFC 2236 | Protokół zarządzania grupami internetowymi, wersja 2          |
|RFC 768  | User Datagram Protocol (UDP)                           |
|RFC 791  | Protokół internetowy (IP)                                 |
|RFC 792  | Protokół ICMP (Internet Control Message Protocol)               |
|RFC 793  | Transmission Control Protocol (TCP)                    |
|RFC 826  | Protokół ARP (Ethernet Address Resolution Protocol) |
|RFC 903  | Protokół odwrotnego rozpoznawania adresów (RARP) |
|RFC 5681 | Kontrola przeciążenia TCP                     |

Poniżej przedstawiono specyfikacje RFC powiązane z protokołem IPv6 obsługiwane przez program NetX Duo.

|**RFC** |**Opis**|
-------- | ------------------------------------------ |
|RFC 1981 |Odnajdowanie MTU ścieżki dla protokołu internetowego w wersji 6 (IPv6)|
|RFC 2460 | Specyfikacja protokołu internetowego w wersji 6 (IPv6)|
|RFC 2464 |Przesyłanie pakietów IPv6 za pośrednictwem sieci Ethernet|
|RFC 4291 |Architektura adresów protokołu internetowego w wersji 6 (IPv6)|
|RFC 4443 |Protokół komunikatów sterowania Internetem (ICMPv6) dla specyfikacji protokołu internetowego w wersji 6 (IPv6)|
|RFC 4861 |Odnajdywanie sąsiadów dla protokołu IP w wersji 6|
|RFC 4862 |Konfiguracja automatycznej bezstanowych adresów IPv6|

## <a name="embedded-network-applications"></a>Osadzone aplikacje sieciowe

Osadzone aplikacje sieciowe to aplikacje, które wymagają dostępu do sieci i działają w mikroprocesorach ukrytych w produktach, takich jak telefony komórkowe, sprzęt komunikacyjny, silniki motoryzacyjne, drukarki laserowe, urządzenia medyczne itd. Takie aplikacje prawie zawsze mają pewne ograniczenia dotyczące pamięci i wydajności. Innym rozróżnianie osadzonych aplikacji sieciowych polega na tym, że ich oprogramowanie i sprzęt mają dedykowany cel.

Oprogramowanie sieciowe, które musi wykonać przetwarzanie w określonym czasie, jest nazywane oprogramowaniem *sieci* w czasie *rzeczywistym* , a w przypadku wystąpienia ograniczeń czasowych w aplikacjach sieciowych są one klasyfikowane jako aplikacje w czasie rzeczywistym. Aplikacje sieci osadzone są prawie zawsze w czasie rzeczywistym ze względu na ich nieodłączną współpracę z zewnętrznym światem.

## <a name="netx-duo-benefits"></a>Zalety rozwiązania NetX Duo

Główną zaletą korzystania z NetX Duo dla aplikacji osadzonych są szybkie połączenia z Internetem i wymagania dotyczące małych ilości pamięci. Program NetX Duo jest również zintegrowany z wysoką wydajnością i ThreadX systemem operacyjnym w czasie rzeczywistym.

### <a name="improved-responsiveness"></a>Zwiększona czas odpowiedzi

Stos protokołu o wysokiej wydajności NetX Duo umożliwia aplikacjom osadzonym w sieci szybsze reagowanie niż kiedykolwiek wcześniej. Jest to szczególnie ważne w przypadku aplikacji osadzonych, które mają znaczną ilość ruchu sieciowego lub rygorystyczne wymagania dotyczące przetwarzania w pojedynczym pakiecie.

### <a name="software-maintenance"></a>Konserwacja oprogramowania

Korzystanie z programu NetX Duo pozwala deweloperom łatwo podzielić na siebie aspekty sieci aplikacji osadzonej. Takie partycjonowanie sprawia, że cały proces tworzenia oprogramowania jest łatwy i znacząco ulepsza konserwację w przyszłości.

### <a name="increased-throughput"></a>Zwiększona przepływność

NetX Duo zapewnia dostęp do najwyższej wydajności sieci, która jest osiągana w minimalnym obciążeniu przetwarzania pakietów. Zapewnia to również zwiększoną przepływność.

### <a name="processor-isolation"></a>Izolacja procesora

NetX Duo zapewnia niezawodny, niezależny od procesora interfejs między aplikacją a podstawowym procesorem i sprzętem sieciowym. Pozwala to deweloperom skoncentrować się na aspektach sieci aplikacji, a nie poświęcać dodatkowego czasu na problemy ze sprzętem bezpośrednio wpływające na sieć.

### <a name="ease-of-use"></a>Łatwość użycia

NetX Duo został zaprojektowany z myślą o deweloperu aplikacji. Architektura NetX Duo i interfejs wywołania usługi są łatwe do zrozumienia. W efekcie deweloperzy rozwiązań NetX Duo mogą szybko korzystać z zaawansowanych funkcji.

### <a name="improve-time-to-market"></a>Popraw czas wprowadzenia na rynek

Zaawansowane funkcje NetX Duo przyspieszają proces tworzenia oprogramowania. NetX Duo stanowi streszczenie większości problemów sprzętowych procesora i sieci, usuwając te problemy z większości obszarów specyficznych dla sieci aplikacji. W związku z tym łatwość użycia i zaawansowanego zestawu funkcji powstaje szybszy czas wprowadzenia na rynek.

### <a name="protecting-the-software-investment"></a>Ochrona inwestycji w oprogramowanie

NetX Duo jest zapisywana wyłącznie w standardzie ANSI C i jest w pełni zintegrowana z systemem operacyjnym ThreadX w czasie rzeczywistym. Oznacza to, że aplikacje NetX Duo są natychmiast przenośne do wszystkich obsługiwanych procesorów ThreadX. Jeszcze lepszym rozwiązaniem może być obsługa nowej architektury procesora z ThreadX w ciągu kilku tygodni. W efekcie korzystanie z programu NetX Duo gwarantuje ścieżkę migracji aplikacji i chroni pierwotne inwestycje rozwojowe.

## <a name="ipv6-ready-logo-certification"></a>Certyfikacja logo gotowego do protokołu IPv6

Certyfikat "IPv6 Read" NetX Duo został uzyskany za pośrednictwem "samotestowego protokołu IPv6 Core (faza 2)" dostępnego w organizacji z przygotowaną obsługą protokołu IPv6. Aby uzyskać więcej informacji na temat platformy testów i przypadków testowych, zobacz następujące IPv6-Ready witryny sieci Web projektu.[**https://www.ipv6ready.org/**](https://www.ipv6ready.org/)

Pakiet fazy 2 jądra Core protokołu samotestów sprawdza, czy stos IPv6 spełnia wymagania opisane w poniższych dokumentach RFC z rozbudowanym testowaniem:  
Sekcja 1: RFC 2460  
Sekcja 2: RFC 4861  
Sekcja 3: RFC 4862  
Sekcja 4: RFC 1981  
Sekcja 5: RFC 4443  

## <a name="ixanvl-test"></a>Test IxANVL

NetX Duo jest testowany z IxANVL z IXIA. IxANVL to standardowy branża do zautomatyzowanego sprawdzania poprawności sieci i protokołu. Więcej informacji na temat IxANVL można znaleźć pod adresem: [**https://www.ixiacom.com/products/ixanvl**](https://www.ipv6ready.org/)

W szczególności następujące moduły NetX Duo są testowane z IxANVL:

|**Moduł** | **Standardowa** |
| --------- | ------------ |
|Adres IP | RFC791 </br> RFC1122 </br> RFC894|
|ICMP | RFC792 </br> RFC1122 </br> RFC1812|
|UDP | RFC768 </br> RFC1122|
|TCP-Core| RFC793 </br> RFC1122 </br> RFC2460|
|TCP-Advanced| RFC1981</br>RFC2001</br>RFC2385</br>RFC2463</br>RFC813</br>RFC896|
|TCP-Performance| RFC793</br>RFC1323</br>RFC2018|

## <a name="safety-certifications"></a>Certyfikaty bezpieczeństwa

### <a name="tv-certification"></a>Certyfikat TÜV  

NetX Duo został certyfikowany przez moimi-TÜV Saar do użytku w systemach krytycznych dla bezpieczeństwa, zgodnie z IEC61508 i IEC-62304. Certyfikat potwierdza, że NetX Duo może być używany w opracowaniu oprogramowania związanego z bezpieczeństwem w celu uzyskania najwyższych poziomów integralności bezpieczeństwa Międzynarodowa Komisja Elektrotechniczna (IEC) 61508 i IEC 62304 dla "bezpieczeństwa funkcjonalnego, elektronicznego i programowalnego elektronicznego systemów związanych z bezpieczeństwem". MOIMI-TÜV Saar, utworzone za pomocą wspólnego przedsiębiorstwa z Niemiec SGSGroup i TÜV Saarland, stał się wiodącą, niezależną firmą do testowania, inspekcji, sprawdzania i certyfikowania oprogramowania osadzonego dla systemów związanych z bezpieczeństwem na całym świecie. Standard bezpieczeństwa przemysłowego IEC 61508 i wszystkie standardy, które są od niego pochodzące, w tym IEC 62304, są używane do zapewnienia bezpieczeństwa funkcjonalnego, elektronicznego i programowalnego elektronicznego sprzętu medycznego, systemów kontroli procesów, maszyn przemysłowych i systemów kontroli szynowej. 

MOIMI-TÜV Saar ma certyfikowane NetX Duo, które mają być używane w systemach samochodowych o krytycznym znaczeniu dla bezpieczeństwa, zgodnie ze standardem ISO 26262. Ponadto NetX Duo są certyfikowane na poziomie integralności infrastruktury bezpieczeństwa motoryzacyjnego (ASIL), który reprezentuje najwyższy poziom certyfikacji ISO 26262. 

Ponadto moimi-TÜV Saar ma certyfikowane NetX Duo, które mają być używane w kluczowych dla bezpieczeństwa aplikacjach związanych z bezpieczeństwem, ze standardem 50128 do SW-SIL 4.

![Diagram logo certyfikatu moimi-TÜV Saar.](./media/user-guide/sgs-tuv-saar-logo.png)

IEC 61508 do SIL 4  
IEC 62304 do klasy bezpieczeństwa oprogramowania SW ISO 26262 ASIL D EN 50128 SW-SIL 4

> [!IMPORTANT]
> *Skontaktuj się z firmą Microsoft, aby uzyskać więcej informacji na temat wersji NetX Duo z certyfikatem TÜV lub dostępności raportów testowych, certyfikatów i powiązanej dokumentacji.*

### <a name="ul-certification"></a>Certyfikat UL

NetX Duo został certyfikowany przez UL w celu zapewnienia zgodności z metodą UL 60730-1 w załączniku h, CSA E60730-1 załącznik H, IEC 60730-1 w załączniku H, UL 60335-1 załączniku R, IEC 60335-1 w załączniku R i standardami bezpieczeństwa UL 1998 dla oprogramowania w składnikach programowalnych. Wraz z IEC/UL 60730-1, które mają wymagania dotyczące "kontrolek wykorzystujących oprogramowanie" w załączniku H, standard IEC 60335-1 opisuje wymagania dotyczące "programowalnych obwodów elektronicznych" w załączniku R. IEC 60730 załącznik H i IEC 60335-1 Załącznik R dotyczy bezpieczeństwa sprzętu i oprogramowania używanego w urządzeniach, takich jak pralki, zmywarki, Dryers, chłodziarks, zamrażarki i Piece.

![Diagram logo certyfikacji UL.](./media/user-guide/c-ru-us-logo.png)

*UL/IEC 60730, UL/IEC 60335, UL 1998*

> [!IMPORTANT]  
> *Skontaktuj się z firmą Microsoft, aby uzyskać więcej informacji na temat wersji programu NetX Duo zakwalifikowanych przez UL lub na potrzeby dostępności raportów testowych, certyfikatów i powiązanej dokumentacji.*