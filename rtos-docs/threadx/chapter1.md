---
title: Rozdział 1 — Wprowadzenie do Azure RTOS ThreadX
description: Ten rozdział zawiera wprowadzenie do Azure RTOS ThreadX oraz opis jego aplikacji i korzyści.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 536b2d59bf9f2cf15d320b91277f0efc7bf96097329f690b0849b2145c5a3abc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802065"
---
# <a name="chapter-1---introduction-to-azure-rtos-threadx"></a>Rozdział 1 — Wprowadzenie do Azure RTOS ThreadX

Azure RTOS ThreadX jest jądrem w czasie rzeczywistym o wysokiej wydajności zaprojektowanym specjalnie dla aplikacji osadzonych. Ten rozdział zawiera wprowadzenie do produktu oraz opis jego aplikacji i korzyści.

## <a name="threadx-unique-features"></a>Unikatowe funkcje ThreadX

W przeciwieństwie do innych jąder czasu rzeczywistego threadX został zaprojektowany tak, aby był uniwersalny — łatwo skalować między małymi aplikacjami opartymi na mikrokontrolerach za pośrednictwem tych, które korzystają z zaawansowanych procesorów CISC, RISC i DSP.

ThreadX jest skalowalny w oparciu o jego podstawową architekturę. Ponieważ usługi ThreadX są implementowane jako biblioteka języka C, tylko te usługi faktycznie używane przez aplikację są wprowadzane do obrazu w czasie uruchamiania. W związku z tym rzeczywisty rozmiar ThreadX jest całkowicie określany przez aplikację. W przypadku większości aplikacji obraz instrukcji ThreadX ma rozmiar od 2 KB do 15 KB.

### <a name="picokerneltrade-architecture"></a>*picokernel Architecture (Architektura picokernel) &trade;*

Zamiast nakładać na siebie funkcje jądra, takie jak tradycyjne architektury *mikrokernel,* usługi ThreadX są podłączane bezpośrednio do jej rdzeni. Skutkuje to najszybszą możliwą wydajnością przełączania kontekstu i wywołania usługi. Nazywamy ten projekt niewarstwowy *architekturą picokernel.*

### <a name="ansi-c-source-code"></a>Kod źródłowy ANSI C

ThreadX jest napisany głównie w języku ANSI C. Aby dostosować jądro do podstawowego procesora docelowego, potrzebna jest niewielka ilość języka zestawu. Ten projekt umożliwia przenoszenie threadX do nowej rodziny procesorów w bardzo krótkim czasie — zwykle w ciągu tygodni!

### <a name="advanced-technology"></a>Zaawansowana technologia

Poniżej przedstawiono najważniejsze funkcje zaawansowanej technologii ThreadX.
- Prosta *architektura picokernel*
- Automatyczne skalowanie (małe zużycie)
- Przetwarzanie deterministyczne
- Szybka wydajność w czasie rzeczywistym
- Planowanie wywłaszcze i kooperatywne
- Elastyczna obsługa priorytetów wątków
- Dynamiczne tworzenie obiektów systemowych
- Nieograniczona liczba obiektów systemowych
- Zoptymalizowana obsługa przerwań
- Próg wywłaszczenia&trade;
- Dziedziczenie priorytetów
- Łańcuch zdarzeń&trade;
- Szybkie czasomierze oprogramowania
- Zarządzanie pamięcią w czasie rzeczywistym
- Monitorowanie wydajności w czasie wykonywania
- Analiza stosu w czasie rzeczywistym
- Wbudowane śledzenie systemu
- Obsługa ogromnych procesorów
- Ogromna obsługa narzędzi dewelopera
- Całkowicie neutralna endian

### <a name="not-a-black-box"></a>Nie jest czarną skrzynką

Większość dystrybucji ThreadX obejmuje pełny kod źródłowy C, a także język zestawu specyficzny dla procesora. Eliminuje to problemy "czarnej skrzynki", które występują w przypadku wielu jąder komercyjnych. Dzięki threadX deweloperzy aplikacji mogą zobaczyć dokładnie, co robi jądro — nie ma żadnych odmów!

Kod źródłowy umożliwia również modyfikacje specyficzne dla aplikacji. Chociaż nie jest to zalecane, na pewno korzystne jest, aby mieć możliwość modyfikowania jądra, jeśli jest to absolutnie wymagane.

Te funkcje są szczególnie wygodne dla deweloperów, którzy są przywykli do pracy z własnymi *jądrami.* Oczekują oni kodu źródłowego i możliwości modyfikowania jądra. ThreadX jest ostatecznym jądrem dla takich deweloperów.

### <a name="the-rtos-standard"></a>The RTOS Standard

Ze względu na ich niezawodność, wysoką wydajność, architekturę *rozwiązania Picokernel,* zaawansowaną technologię i zademonstrowany przenośność, threadX jest obecnie wdrażany na ponad dwóch miliardach urządzeń. Dzięki temu ThreadX jest standardem RTOS dla aplikacji głęboko osadzonych.

## <a name="safety-certifications"></a>Certyfikaty bezpieczeństwa

### <a name="tv-certification"></a>Certyfikacja TÜV

ThreadX ma certyfikat SGS-TÜV Saar do użycia w systemach o krytycznym znaczeniu dla bezpieczeństwa, zgodnie z normami IEC61508 i IEC-62304. Certyfikat potwierdza, że ThreadX może być używany do opracowywania oprogramowania związanego z bezpieczeństwem dla najwyższych poziomów integralności bezpieczeństwa systemów Międzynarodowa Komisja Elektrotechniczna (IEC) 61508 i IEC 62304 dla "bezpieczeństwa funkcjonalnego systemów elektronicznych, elektronicznych i programowalnych systemów związanych z bezpieczeństwem". SGS-TÜV Saar, utworzone za pośrednictwem wspólnej osady niemieckich firm SGSGroup i TÜV Saarland, stała się wiodącą akredytowaną, niezależną firmą do testowania, inspekcji, weryfikowania i certyfikowania osadzonego oprogramowania dla systemów powiązanych z bezpieczeństwem na całym świecie. Standard bezpieczeństwa przemysłowego IEC 61508 i wszystkie standardy, które z niego pochodzą, w tym IEC 62304, są używane w celu zapewnienia bezpieczeństwa funkcjonalnego urządzeń elektronicznych, elektronicznych i programowalnych urządzeń medycznych związanych z bezpieczeństwem, systemów sterowania procesami, maszyn przemysłowych i systemów sterowania węzłem.

SGS-TÜV Saar ma certyfikat ThreadX, który może być używany w krytycznych dla bezpieczeństwa systemach samochodowych zgodnie ze standardem ISO 26262. Ponadto ThreadX ma certyfikat ASIL D (Safety Integrity Level) dla samochodów, który reprezentuje najwyższy poziom certyfikacji ISO 26262.

Ponadto firma SGS-TÜV Saar ma certyfikat ThreadX, który może być używany w aplikacjach do kluczowych dla bezpieczeństwa, zgodnie ze standardem EN 50128 i zgodnie ze standardem SW-SIL 4.

![Certyfikacja TÜV](./media/overview-threadx/partener-logo-sgs-tuv-saar-2.png)

* IEC 61508 do SIL 4

* IEC 62304 do bezpieczeństwa SW, klasa C

* ISO 26262 ASIL D

* EN 50128 SW-SIL 4

> [!NOTE]
> *Skontaktuj się z nami, aby uzyskać więcej informacji o wersjach threadX, które zostały certyfikowane przez TÜV, lub o dostępności raportów testowych, certyfikatów i skojarzonej dokumentacji.*

### <a name="misra-c-compliant"></a>Zgodne ze standardem MISRA C

MISRA C to zestaw wytycznych programowania dla systemów krytycznych korzystających z języka programowania C. Oryginalne wytyczne MISRA C były przeznaczone głównie dla aplikacji samochodowych. Jednak język MISRA C jest teraz powszechnie uznawany za stosowany do wszystkich aplikacji o krytycznym znaczeniu dla bezpieczeństwa. ThreadX jest zgodny ze wszystkimi "wymaganymi" i "obowiązkowymi" regułami MISRA-C:2004 i MISRA C:2012. ThreadX jest również zgodny ze wszystkimi poza trzema regułami "porad". Zapoznaj się z ***ThreadX_MISRA_Compliance.pdf,*** aby uzyskać więcej szczegółów.

### <a name="ul-certification"></a>Certyfikacja UL

ThreadX ma certyfikat zgodności z ul 60730-1,H, CSA E60730-1, h, IEC 60730-1, h, ul 60335-1, część R, IEC 60335-1 i standardy bezpieczeństwa UL 1998 dla oprogramowania w programowalnych elementach. Wraz z IEC/UL 60730-1 który ma wymagania dotyczące "kontrolek korzystających z oprogramowania" w załączniku H, standard IEC 60335-1 opisuje wymagania dotyczące "programowalnych obwodów elektronicznych" w załączniku R. IEC 60730, załącznik H i IEC 60335-1 Dokument R dotyczy bezpieczeństwa sprzętu i oprogramowania MCU używanego w urządzeniach, takich jak maszyny nagie, nagie, lodówki, chłodziarki i pąki.

![Certyfikacja UL](./media/overview-threadx/partener-logo-c-ru-us-2.png)

*UL/IEC 60730, UL/IEC 60335, UL 1998*

> [!NOTE]
> *Skontaktuj się z firmą Microsoft, aby uzyskać więcej informacji o wersjach threadX, które zostały certyfikowane przez TÜV, lub o dostępności raportów testowych, certyfikatów i skojarzonej dokumentacji.*

### <a name="certification-pack"></a>Pakiet certyfikacji

Pakiet certyfikacji ThreadX jest w 100% kompletnym, gotowego do zastosowania, specyficznym dla branży pakietem autonomicznym, który zapewnia wszystkie dowód ThreadX potrzebne do certyfikowania lub pomyślnego przesyłania produktu opartego na threadX na najwyższy poziom niezawodności i krytyczności wymagany dla systemów informatycznych, medycznych i przemysłowych o krytycznym znaczeniu dla &trade; bezpieczeństwa. Obsługiwane certyfikaty to DO-178B, ED-12B, DO-278, TEŻ510(k), IEC62304, IEC-60601, ISO-14971, UL-1998, IEC-61508, CENELEC EN50128, BS50128 i 49CFR236. Aby uzyskać więcej informacji na temat pakietu certyfikacji, skontaktuj się z firmą Microsoft.

## <a name="embedded-applications"></a>Aplikacje osadzone

Aplikacje osadzone są wykonywane na mikroprocesorach w produktach, takich jak urządzenia do komunikacji bezprzewodowej, aparaty samochodowy, drukarki laserowe, urządzenia medyczne itp. Innym rozróżnieniem aplikacji osadzonych jest to, że ich oprogramowanie i sprzęt mają specjalne przeznaczenie.

### <a name="real-time-software"></a>Oprogramowanie w czasie rzeczywistym

Gdy na oprogramowanie aplikacji nakładane są ograniczenia czasowe, jest ono nazywane oprogramowaniem *w czasie* rzeczywistym. Aplikacje osadzone prawie zawsze są w czasie rzeczywistym ze względu na ich naturalną interakcję ze zdarzeniami zewnętrznymi.

### <a name="multitasking"></a>Wielozadaniowość

Jak wspomniano wcześniej, aplikacje osadzone mają specjalne przeznaczenie. Aby zrealizować ten cel, oprogramowanie musi wykonywać różne *zadania.* Zadanie to częściowo niezależna część aplikacji, która wykonuje określone obowiązki. Jest również tak, że niektóre zadania są ważniejsze niż inne. Jedną z głównych trudności w aplikacji osadzonej jest alokacja procesora między różnymi zadaniami aplikacji. Ta alokacja przetwarzania między konkurującymi zadaniami jest głównym celem threadX.

### <a name="tasks-vs-threads"></a>Zadania a wątki

Inne rozróżnienie dotyczące zadań polega na tym, że termin *zadanie* jest używany na różne sposoby. Czasami oznacza to oddzielnie ładowalny program. W innych przypadkach może odwoływać się do wewnętrznego segmentu programu. W związku z tym w nowoczesnych systemach operacyjnych istnieją dwa terminy, które w mniejszym lub mniejszym stopniu zastępują użycie zadania: *proces* i *wątek*. Proces *jest* całkowicie niezależnym programem, który ma własną przestrzeń adresową, *podczas* gdy wątek jest częściowo niezależnym segmentem programu, który jest wykonywany w ramach procesu. Wątki współdzielą tę samą przestrzeń adresową procesu. Obciążenie związane z zarządzaniem wątkami jest minimalne.

Większość aplikacji osadzonych nie może pozwolić sobie na obciążenie (zarówno pamięć, jak i wydajność) związane z w pełni zorientowanym na proces systemem operacyjnym. Ponadto mniejsze mikroprocesory nie mają architektury sprzętowej do obsługi prawdziwego systemu operacyjnego zorientowanego na proces. Z tego powodu ThreadX implementuje model wątków, który jest bardzo wydajny i praktyczny w przypadku większości aplikacji osadzonych w czasie rzeczywistym.

Aby uniknąć nieporozumień, ThreadX nie używa terminu *zadanie*. Zamiast tego jest używany bardziej opisowy i bardziej *opisowy wątek* nazwy.

## <a name="threadx-benefits"></a>Korzyści związane z ThreadX

Korzystanie z ThreadX zapewnia wiele korzyści dla aplikacji osadzonych. Oczywiście główną korzyścią jest przydzielanie czasu przetwarzania osadzonych wątków aplikacji.

### <a name="improved-responsiveness"></a>Ulepszone reagowanie

Przed jądrami czasu rzeczywistego, takich jak ThreadX, większość osadzonych aplikacji przydzielała czas przetwarzania przy użyciu prostej pętli sterowania, zazwyczaj z poziomu funkcji *głównej języka* C. To podejście jest nadal stosowane w bardzo małych lub prostych aplikacjach. Jednak w dużych lub złożonych aplikacjach nie jest to praktyczne, ponieważ czas odpowiedzi na dowolne zdarzenie jest funkcją najgorszego czasu przetwarzania jednego przebiegu przez pętlę sterowania. 

Co gorsza, charakterystyka chronometrażu aplikacji zmienia się za każdym razem, gdy w pętli sterowania zostaną wprowadzone modyfikacje. Sprawia to, że aplikacja jest z założenia niestabilna i trudna w konserwacji oraz ulepszana.

ThreadX zapewnia szybkie i deterministyczne czasy odpowiedzi na ważne zdarzenia zewnętrzne. ThreadX realizuje to za pomocą swojego wywłaszczaczego algorytmu planowania opartego na priorytetach, który umożliwia wątkowi o wyższym priorytecie wywłaszczanie wykonywania wątku o niższym priorytecie. W związku z tym czas odpowiedzi w najgorszym przypadku zbliża się do czasu wymaganego do przełączenia kontekstu. Jest to nie tylko deterministyczne, ale również niezwykle szybkie.

### <a name="software-maintenance"></a>Konserwacja oprogramowania

Jądro ThreadX umożliwia deweloperom aplikacji skoncentrowanie się na określonych wymaganiach swoich wątków aplikacji bez konieczności martwienia się o zmianę czasu innych obszarów aplikacji. Ta funkcja znacznie ułatwia również naprawę lub ulepszanie aplikacji, która korzysta z ThreadX.

### <a name="increased-throughput"></a>Zwiększona przepływność

Możliwe rozwiązanie problemu czasu odpowiedzi pętli sterowania polega na dodaniu większej liczby sondowania. Poprawia to czas odpowiedzi, ale nadal nie gwarantuje stałego czasu odpowiedzi w najgorszym przypadku i nie robi nic, aby poprawić przyszłe modyfikacje aplikacji. Ponadto procesor wykonuje teraz jeszcze bardziej niepotrzebne przetwarzanie ze względu na dodatkowe sondowanie. Wszystkie te niepotrzebne przetwarzanie zmniejsza ogólną przepływność systemu.

Interesujące jest to, że wielu deweloperów zakłada, że środowiska wielowątkowe, takie jak ThreadX, zwiększają narzut i mają negatywny wpływ na łączną przepływność systemu. Jednak w niektórych przypadkach wielowątkowanie faktycznie zmniejsza obciążenie, eliminując całe nadmiarowe sondowanie, które występuje w środowiskach pętli sterowania. Obciążenie związane z jądrami wielowątkowych jest zwykle funkcją czasu wymaganą do przełączania kontekstu. Jeśli czas przełączania kontekstu jest krótszy niż proces sondowania, threadX zapewnia rozwiązanie z potencjalnym mniejszym obciążeniem i większą przepływnością. Dzięki temu ThreadX jest oczywistym wyborem dla aplikacji, które mają dowolny stopień złożoności lub rozmiaru.

### <a name="processor-isolation"></a>Izolacja procesora

ThreadX zapewnia niezawodny interfejs niezależny od procesora między aplikacją a bazowym procesorem. Dzięki temu deweloperzy mogą skoncentrować się na aplikacji, zamiast poświęcać znaczną ilość czasu na uczenie się szczegółów sprzętu.

### <a name="dividing-the-application"></a>Dzielenie aplikacji

W aplikacjach opartych na pętli sterowania każdy deweloper musi mieć pełną wiedzę na temat zachowania i wymagań całej aplikacji w czasie działania. Jest to spowodowane rozproszeniem logiki alokacji procesora w całej aplikacji. Wraz ze wzrostem rozmiaru lub złożoności aplikacji wszyscy deweloperzy nie będą w stanie zapamiętać dokładnych wymagań dotyczących przetwarzania całej aplikacji.

ThreadX pozwala każdemu deweloperowi nie martwić się o alokację procesora i pozwala mu skoncentrować się na konkretnym elementie osadzonej aplikacji. Ponadto ThreadX wymusza podzieloną aplikację na jasno zdefiniowane wątki. Sam ten podział aplikacji na wątki sprawia, że opracowywanie jest znacznie prostsze.

### <a name="ease-of-use"></a>Łatwość obsługi

ThreadX został zaprojektowany z myślą o deweloperze aplikacji. Architektura ThreadX i interfejs wywołania usługi zostały zaprojektowane tak, aby można je było łatwo zrozumieć. Dzięki temu deweloperzy ThreadX mogą szybko korzystać z jej zaawansowanych funkcji.

### <a name="improve-time-to-market"></a>Poprawianie czasu przedsieć na rynek

Wszystkie zalety technologii ThreadX przyspieszają proces tworzenia oprogramowania. ThreadX zajmuje się większość problemów z procesorem i najbardziej powszechnymi certyfikatami bezpieczeństwa, co pozwala usunąć ten nakład pracy z harmonogramu projektowania. Wszystko to powoduje szybsze wyekserowania!

### <a name="protecting-the-software-investment"></a>Ochrona inwestycji w oprogramowanie

Ze względu na swoją architekturę ThreadX jest łatwo przenoszony do nowych procesorów i/lub środowisk narzędzi deweloperskich. W połączeniu z tym, że ThreadX odizoluje aplikacje od szczegółów bazowych procesorów, sprawia, że aplikacje ThreadX są wysoce przenośne. W związku z tym ścieżka migracji aplikacji jest gwarantowana, a pierwotna inwestycja w tworzenie aplikacji jest chroniona.
