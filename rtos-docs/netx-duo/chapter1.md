---
title: Rozdział 1 — Wprowadzenie do Azure RTOS NetX Duo
description: Ten rozdział zawiera wprowadzenie do Azure RTOS NetX Duo oraz opis jego aplikacji i korzyści.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c9b5e0ea82319bd369318cca753cf1db222ca29b0b4db3da150642ca007f1191
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116789869"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo"></a>Rozdział 1 — Wprowadzenie do Azure RTOS NetX Duo

Azure RTOS NetX Duo to implementacja w czasie rzeczywistym o wysokiej wydajności standardów TCP/IP przeznaczona wyłącznie dla aplikacji osadzonych Azure RTOS opartych na ThreadX. Ten rozdział zawiera wprowadzenie do aplikacji NetX Duo oraz opis jej aplikacji i korzyści. 

## <a name="netx-duo-unique-features"></a>NetX Duo Unique Features

W przeciwieństwie do innych implementacji TCP/IP netX Duo zaprojektowano tak, aby był wszechstronny — łatwe skalowanie od małych aplikacji opartych na mikrokontrolerach do tych, które korzystają z zaawansowanych procesorów RISC i DSP. Jest to w dużym przeciwieństwie do domeny publicznej lub innych implementacji komercyjnych pierwotnie przeznaczonych dla środowisk stacji roboczych, ale następnie przechowane w osadzonych projektach.

### <a name="piconettrade-architecture"></a>Piconet &trade; Architecture (Architektura Piconet)

Bazą najwyższej skalowalności i wydajności netX Duo jest <em>Piconet</em>, architektura oprogramowania zaprojektowana specjalnie dla systemów osadzonych. Architektura Piconet maksymalizuje skalowalność, implementując usługi NetX Duo jako bibliotekę języka C. W ten sposób tylko te usługi używane przez aplikację są przeniesiene do obrazu końcowego środowiska uruchomieniowego. W związku z tym rzeczywisty rozmiar netx duo jest określany przez aplikację. W przypadku większości aplikacji wymagania dotyczące obrazów instrukcji aplikacji NetX Duo mają rozmiar od 5 KB do 30 KB. Po włączeniu protokołów IPv6 i ICMPv6 konfiguracji adresów IPv6 i protokołów odnajdywania sąsiadów netX Duo ma rozmiar od 30 kb do 45 kb.

NetX Duo osiąga najwyższą wydajność sieci, nakładając warstwy na wewnętrzne wywołania funkcji składników tylko wtedy, gdy jest to konieczne. Ponadto większość przetwarzania NetX Duo jest wykonywana bezpośrednio w wierszu, co w przeszłości osiągło niesłychanące korzyści z wydajności niż oprogramowanie sieciowe stacji roboczych używane w osadzonych projektach.

### <a name="zero-copy-implementation"></a>Implementacja bez kopiowania

NetX Duo zapewnia opartą na pakietach implementację protokołu TCP/IP bez kopiowania. Zerowy kopiowanie oznacza, że dane w buforze pakietów aplikacji nigdy nie są kopiowane wewnątrz netx duo. Znacznie zwiększa to wydajność i pozwala na wolnej aplikacji cenne cykle procesora, co jest ważne w aplikacjach osadzonych.

### <a name="udp-fast-pathtrade-technology"></a>Technologia szybkiej ścieżki UDP &trade;

Dzięki <em>technologii UDP Fast Path</em>netX Duo zapewnia najszybsze możliwe przetwarzanie UDP. Po stronie wysyłającej przetwarzanie UDP — w tym opcjonalną podsumę kontrolną UDP — jest zawarte w <em>**nx_udp_socket_send**</em> usługi. Żadne dodatkowe wywołania funkcji nie są dokonywane, dopóki pakiet nie jest gotowy do wysłania za pośrednictwem wewnętrznej procedury wysyłania adresów IP NetX Duo. Ta procedura jest również płaska (oznacza to, że zagnieżdżanie wywołań funkcji jest minimalne), więc pakiet jest szybko wysyłany do sterownika sieciowego aplikacji. Po otrzymaniu pakietu UDP przetwarzanie odbierania pakietów NetX Duo umieszcza pakiet bezpośrednio w kolejce odbierania odpowiedniego gniazda UDP lub przekazuje go do pierwszego wątku wstrzymanego w oczekiwaniu na pakiet odbierania z kolejki odbierania gniazda UDP. Nie są wymagane żadne dodatkowe przełączniki kontekstu ThreadX.

### <a name="ansi-c-source-cod"></a>ANSI C Source Cod

NetX Duo jest napisany całkowicie w języku ANSI C i jest od razu przenośny do praktycznie dowolnej architektury procesora, która ma kompilator ANSI C i obsługę ThreadX. 

### <a name="not-a-black-box"></a>Nie jest czarną skrzynką

Większość dystrybucji netX Duo zawiera kompletny kod źródłowy języka C. Eliminuje to problemy "czarnej skrzynki", które występują w przypadku wielu komercyjnych stosów sieciowych. Korzystając z netx duo, deweloperzy aplikacji mogą zobaczyć dokładnie, co robi stos sieciowy — nie ma żadnych wytłoków!

Kod źródłowy umożliwia również modyfikacje specyficzne dla aplikacji. Chociaż nie jest to zalecane, korzystne jest, aby mieć możliwość modyfikowania stosu sieciowego, jeśli jest to wymagane.

Te funkcje są szczególnie wygodne dla deweloperów, którzy są przywykli do pracy ze stosami sieci domeny lokalnej lub publicznej. Oczekują oni kodu źródłowego i możliwości jego modyfikowania. NetX Duo to ostateczne oprogramowanie sieciowe dla takich deweloperów.

### <a name="bsd-compatible-socket-api"></a>interfejs API BSD-Compatible Socket

W przypadku starszych aplikacji NetX Duo udostępnia również interfejs gniazd zgodny z BSD, który wykonuje wywołania interfejsu API NetX Duo o wysokiej wydajności poniżej. Ułatwia to migrowanie istniejącego kodu aplikacji sieciowej do netx duo.

## <a name="rfcs-supported-by-netx-duo"></a>RFC obsługiwane przez NetX Duo

Obsługa interfejsów RFC w netX Duo opisujących podstawowe protokoły sieciowe obejmuje między innymi następujące protokoły sieciowe. NetX Duo jest zgodny ze wszystkimi ogólnymi zaleceniami i podstawowymi wymaganiami w ramach ograniczeń systemu operacyjnego w czasie rzeczywistym, z małym zużyciem pamięci i wydajnym wykonywaniem.

| **RFC**  | **Opis**                                        |
| -------- | ------------------------------------------------------ |
|RFC 1112 | Rozszerzenia hosta dla multiemisji IP (IGMPv1)           |
|RFC 1122 | Wymagania dotyczące hostów internetowych — warstwy komunikacyjne |
|RFC 2236 | Protokół zarządzania grupą internetową, wersja 2          |
|RFC 768  | Protokół UDP (User Datagram Protocol)                           |
|RFC 791  | Protokół internetowy (IP)                                 |
|RFC 792  | Protokół ICMP (Internet Control Message Protocol)               |
|RFC 793  | Transmission Control Protocol (TCP)                    |
|RFC 826  | Protokół ARP (Ethernet Address Resolution Protocol) |
|RFC 903  | Protokół RARP (Reverse Address Resolution Protocol) |
|RFC 5681 | Kontrola przeciążenia protokołu TCP                     |

Poniżej przedstawiono RFC związane z IPv6 obsługiwane przez NetX Duo.

|**RFC** |**Opis**|
-------- | ------------------------------------------ |
|RFC 1981 |Odnajdywanie mtu ścieżki dla protokołu internetowego w wersji 6 (IPv6)|
|RFC 2460 | Specyfikacja protokołu internetowego w wersji 6 (IPv6)|
|RFC 2464 |Transmisja pakietów IPv6 za pośrednictwem sieci Ethernet|
|RFC 4291 |Architektura adresowania protokołu IPv6 (Internet Protocol v6)|
|RFC 4443 |Protokół ICMPv6 (Internet Control Message Protocol) dla specyfikacji protokołu internetowego w wersji 6 (IPv6)|
|RFC 4861 |Odnajdywanie sąsiadów dla adresu IP w wersji 6|
|RFC 4862 |Automatyczna konfiguracja bez stanowego adresu IPv6|

## <a name="embedded-network-applications"></a>Osadzone aplikacje sieciowe

Osadzone aplikacje sieciowe to aplikacje, które wymagają dostępu do sieci i są wykonywane na mikroprocesorach ukrytych wewnątrz produktów, takich jak telefony komórkowe, sprzęt komunikacyjny, aparaty samochodowy, drukarki laserowe, urządzenia medyczne itd. Takie aplikacje prawie zawsze mają pewne ograniczenia dotyczące pamięci i wydajności. Innym rozróżnieniem aplikacji sieciowych osadzonych jest to, że ich oprogramowanie i sprzęt mają specjalne przeznaczenie.

Oprogramowanie sieciowe, które musi wykonać przetwarzanie w   dokładnym czasie, jest nazywane oprogramowaniem sieciowym w czasie rzeczywistym, a w przypadku narzucania ograniczeń czasu na aplikacje sieciowe są one klasyfikowane jako aplikacje w czasie rzeczywistym. Osadzone aplikacje sieciowe prawie zawsze są w czasie rzeczywistym ze względu na ich naturalną interakcję ze światem zewnętrznym.

## <a name="netx-duo-benefits"></a>Korzyści z netx duo

Głównymi zaletami korzystania z netX Duo w aplikacjach osadzonych są szybkie połączenia z Internetem i małe wymagania dotyczące pamięci. NetX Duo jest również zintegrowany z wysokowydajnym, wielozadaniowym systemem operacyjnym ThreadX w czasie rzeczywistym.

### <a name="improved-responsiveness"></a>Udoskonalony czas odpowiedzi

Stos protokołu NetX Duo o wysokiej wydajności umożliwia aplikacjom sieci osadzonej szybsze reagowanie niż kiedykolwiek wcześniej. Jest to szczególnie ważne w przypadku aplikacji osadzonych, które mają znaczną ilość ruchu sieciowego lub rygorystyczne wymagania dotyczące przetwarzania pojedynczego pakietu.

### <a name="software-maintenance"></a>Konserwacja oprogramowania

Korzystanie z netX Duo umożliwia deweloperom łatwe partycjonowanie aspektów sieciowych osadzonej aplikacji. Dzięki takiemu partycjonowania cały proces tworzenia oprogramowania jest łatwy i znacząco usprawnia przyszłą konserwację oprogramowania.

### <a name="increased-throughput"></a>Zwiększona przepływność

NetX Duo zapewnia dostępną sieć o najwyższej wydajności, która jest osiągana przez minimalne obciążenie związane z przetwarzaniem pakietów. Umożliwia to również zwiększenie przepływności.

### <a name="processor-isolation"></a>Izolacja procesora

NetX Duo zapewnia niezawodny, niezależny od procesora interfejs między aplikacją a bazowym procesorem i sprzętem sieciowym. Dzięki temu deweloperzy mogą skoncentrować się na aspektach sieciowych aplikacji, zamiast poświęcać dodatkowy czas na radzenie sobie ze sprzętem, które bezpośrednio wpływają na sieć.

### <a name="ease-of-use"></a>Łatwość użycia

Aplikacja NetX Duo została zaprojektowana z myślą o deweloperach aplikacji. Architektura NetX Duo i interfejs wywołania usługi są łatwe do zrozumienia. W związku z tym deweloperzy netX Duo mogą szybko korzystać ze swoich zaawansowanych funkcji.

### <a name="improve-time-to-market"></a>Poprawianie czasu na rynek

Zaawansowane funkcje narzędzia NetX Duo przyspieszają proces tworzenia oprogramowania. NetX Duo stanowi abstrakcję większości problemów ze sprzętem procesora i sieci, co usuwa te problemy z większości obszarów specyficznych dla sieci aplikacji. W połączeniu z łatwością użycia i zaawansowanym zestawem funkcji pozwala to przyspieszyć rynek.

### <a name="protecting-the-software-investment"></a>Ochrona inwestycji w oprogramowanie

NetX Duo jest napisany wyłącznie w języku ANSI C i jest w pełni zintegrowany z systemem operacyjnym ThreadX w czasie rzeczywistym. Oznacza to, że aplikacje NetX Duo są natychmiast przenośne na wszystkie procesory obsługiwane przez ThreadX. Co więcej, nowa architektura procesora może być obsługiwana za pomocą threadX w ciągu kilku tygodni. W związku z tym użycie narzędzia NetX Duo zapewnia ścieżkę migracji aplikacji i chroni oryginalną inwestycję deweloperską.

## <a name="ipv6-ready-logo-certification"></a>Certyfikacja gotowego logo IPv6

Certyfikat NetX Duo "IPv6 Ready" został uzyskany za pośrednictwem pakietu "IPv6 Core Protocol (Phase 2) Self Test" dostępnego w organizacji gotowej do użycia w protokole IPv6. Zapoznaj się z następującymi witrynami IPv6-Ready projektu, aby uzyskać więcej informacji na temat platformy testowej i przypadków testowych:[**https://www.ipv6ready.org/**](https://www.ipv6ready.org/)

Pakiet testów self-test protokołu IPv6 Core Protocol (Faza 2) sprawdza, czy stos IPv6 spełnia wymagania określone w następujących RFC z obszernym testowaniem:  
Sekcja 1: RFC 2460  
Sekcja 2: RFC 4861  
Sekcja 3: RFC 4862  
Sekcja 4: RFC 1981  
Sekcja 5: RFC 4443  

## <a name="ixanvl-test"></a>IxANVL Test

NetX Duo jest testowany z IxANVL firmy IOWANO. IxANVL to branżowy standard zautomatyzowanej weryfikacji sieci i protokołu. Więcej informacji na temat IxANVL można znaleźć na stronie: [**https://www.ixiacom.com/products/ixanvl**](https://www.ipv6ready.org/)

W szczególności następujące moduły NetX Duo są testowane z programem IxANVL:

|**Moduł** | **Standardowa** |
| --------- | ------------ |
|Adres IP | RFC791 </br> RFC1122 </br> RFC894|
|ICMP | RFC792 </br> RFC1122 </br> RFC1812|
|UDP | RFC768 </br> RFC1122|
|TCP-Core| RFC793 </br> RFC1122 </br> RFC2460|
|TCP-Advanced| RFC1981</br>RFC2001</br>RFC2385</br>RFC2463</br>RFC813</br>RFC896|
|TCP-Performance| RFC793</br>RFC1323</br>RFC2018|

## <a name="safety-certifications"></a>Certyfikaty bezpieczeństwa

### <a name="tv-certification"></a>Certyfikacja TÜV  

Zgodnie z normami IEC61508 i IEC-62304 system NetX Duo został certyfikowany przez firmę SGS-TÜV Saar do użytku w systemach o krytycznym znaczeniu dla bezpieczeństwa. Certyfikat potwierdza, że netx duo może być używany do opracowywania oprogramowania związanego z bezpieczeństwem na najwyższym poziomie integralności bezpieczeństwa systemów Międzynarodowa Komisja Elektrotechniczna (IEC) 61508 i IEC 62304 w ramach "Bezpieczeństwa funkcjonalnego systemów elektronicznych, elektronicznych i programowalnych systemów związanych z bezpieczeństwem elektronicznym". SGS-TÜV Saar, utworzone za pośrednictwem wspólnej osady niemieckich firm SGSGroup i TÜV Saarland, stała się wiodącą akredytowaną, niezależną firmą do testowania, inspekcji, weryfikowania i certyfikowania osadzonego oprogramowania dla systemów powiązanych z bezpieczeństwem na całym świecie. Standard bezpieczeństwa przemysłowego IEC 61508 i wszystkie standardy, które z niego pochodzą, w tym IEC 62304, są używane w celu zapewnienia bezpieczeństwa funkcjonalnego urządzeń elektronicznych, elektronicznych i programowalnych urządzeń medycznych związanych z bezpieczeństwem, systemów sterowania procesami, maszyn przemysłowych i systemów sterowania węzłem. 

Firma SGS-TÜV Saar ma certyfikat NetX Duo do stosowania w krytycznych dla bezpieczeństwa systemach samochodowych zgodnie ze standardem ISO 26262. Ponadto NetX Duo ma certyfikat ASIL D (Safety Integrity Level) dla branży samochodów, który reprezentuje najwyższy poziom certyfikacji ISO 26262. 

Ponadto firma SGS-TÜV Saar ma certyfikat NetX Duo, który ma być używany w aplikacjach do ochrony przed krytycznym bezpieczeństwem, zgodnie ze standardem EN 50128, aż do programu SW-SIL 4.

![Diagram logo certyfikacji Saar SGS-TÜV.](./media/user-guide/sgs-tuv-saar-logo.png)

IEC 61508 do SIL 4  
IEC 62304 do bezpieczeństwa SW Klasa C ISO 26262 ASIL D EN 50128 SW-SIL 4

> [!IMPORTANT]
> *Skontaktuj się z firmą Microsoft, aby uzyskać więcej informacji na temat wersji aplikacji NetX Duo certyfikowanych przez firmę TÜV lub dostępności raportów testowych, certyfikatów i powiązanej dokumentacji.*

### <a name="ul-certification"></a>Certyfikacja UL

Firma NetX Duo ma certyfikat zgodności z przepisami UL 60730-1, CsA E60730-1, H, IEC 60730-1, H, UL 60335-1; IEC 60335-1; standardy bezpieczeństwa oprogramowania w programowalnych elementach. Wraz z IEC/UL 60730-1 który ma wymagania dotyczące "kontrolek korzystających z oprogramowania" w załączniku H, standard IEC 60335-1 opisuje wymagania dotyczące "programowalnych obwodów elektronicznych" w załączniku R. IEC 60730, załącznik H i IEC 60335-1 Dokument R dotyczy bezpieczeństwa sprzętu i oprogramowania MCU używanego w urządzeniach, takich jak maszyny nagie, nagie, lodówki, chłodziarki i pąki.

![Diagram logo certyfikacji UL.](./media/user-guide/c-ru-us-logo.png)

*UL/IEC 60730, UL/IEC 60335, UL 1998*

> [!IMPORTANT]  
> *Skontaktuj się z firmą Microsoft, aby uzyskać więcej informacji na temat wersji oprogramowania NetX Duo, które zostały certyfikowane przez firmę UL, lub w celu dostępności raportów testowych, certyfikatów i skojarzonej dokumentacji.*